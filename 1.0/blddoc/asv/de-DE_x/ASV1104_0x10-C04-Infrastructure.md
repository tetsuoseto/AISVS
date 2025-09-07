# C4-Infrastruktur, Konfigurations- und Bereitstellungssicherheit

## Kontrollziel

Die KI-Infrastruktur muss gegen Privilegienerweiterung, Manipulation der Lieferkette und laterale Bewegung durch sichere Konfiguration, Laufzeitisolierung, vertrauenswürdige Bereitstellungspipelines und umfassende Überwachung gehärtet werden. Nur autorisierte, validierte Infrastrukturbestandteile und Konfigurationen gelangen über kontrollierte Prozesse in die Produktion, die Sicherheit, Integrität und Prüfbarkeit gewährleisten.

Kern-Sicherheitsziel: Nur kryptografisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen durch automatisierte Validierungspipelines, die Sicherheitsrichtlinien durchsetzen und unveränderliche Prüfpfade aufrechterhalten, in die Produktion.

---

## C4.1 Laufzeitumgebungsisolation

Verhindern Sie Container-Ausbrüche und Privilegieneskalationen durch kernelbasierte Isolationsprimitiven und obligatorische Zugriffskontrollen.

|   #   | Beschreibung                                                                                                                                                                                                                                                     | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.1.1 | Stellen Sie sicher, dass alle KI-Container ALLE Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und den ausdrücklich in den Sicherheitsgrundlagen dokumentierten erforderlichen Fähigkeiten entfernen.                                                            |   1    |  D/V  |
| 4.1.2 | Überprüfen Sie, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denen in vorab genehmigten Allow-Lists, wobei Verstöße den Container beenden und Sicherheitswarnungen erzeugen.                                                                        |   1    |  D/V  |
| 4.1.3 | Überprüfen Sie, dass KI-Arbeitslasten mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei die noexec-Mount-Optionen durchgesetzt werden.                                   |   2    |  D/V  |
| 4.1.4 | Überprüfen Sie, dass die auf eBPF basierende Laufzeitüberwachung (Falco, Tetragon oder gleichwertig) Versuche zur Privilegienerweiterung erkennt und die verursachenden Prozesse automatisch innerhalb der organisatorischen Reaktionszeitanforderungen beendet. |   2    |  D/V  |
| 4.1.5 | Verifizieren Sie, dass KI-Arbeitslasten mit hohem Risiko in hardware-isolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestierungsprüfung ausgeführt werden.                                                                    |   3    |  D/V  |

---

## C4.2 Sichere Build- und Deployment-Pipelines

Sichern Sie die kryptografische Integrität und die Sicherheit der Lieferkette durch reproduzierbare Builds und signierte Artefakte.

|   #   | Beschreibung                                                                                                                                                                                                                   | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 4.2.1 | Stellen Sie sicher, dass Infrastructure-as-Code bei jedem Commit mit Tools (tfsec, Checkov oder Terrascan) gescannt wird und dass Merges bei FINDUNGEN mit CRITICAL oder HIGH Schweregrad blockiert werden.                    |   1    |  D/V  |
| 4.2.2 | Überprüfen Sie, dass Container-Builds reproduzierbar sind mit identischen SHA256-Hashes über Builds hinweg, und erstellen Sie SLSA Level 3 Herkunftsbescheinigungen, die mit Sigstore signiert sind.                           |   1    |  D/V  |
| 4.2.3 | Stellen Sie sicher, dass Container-Images CycloneDX- oder SPDX-SBOMs einbetten und vor dem Push ins Registry mit Cosign signiert sind, wobei unsignierte Images bei der Bereitstellung abgelehnt werden.                       |   2    |  D/V  |
| 4.2.4 | Überprüfen Sie, dass CI/CD-Pipelines OIDC-Token von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity verwenden, deren Lebensdauer die Grenzen der organisatorischen Sicherheitsrichtlinien nicht überschreitet.     |   2    |  D/V  |
| 4.2.5 | Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Herkunft während des Bereitstellungsprozesses vor der Containerausführung überprüft werden und dass Verifizierungsfehler dazu führen, dass die Bereitstellung fehlschlägt. |   2    |  D/V  |
| 4.2.6 | Überprüfen Sie, dass Build-Umgebungen in temporären Containern oder VMs ohne persistenten Speicher ausgeführt werden und eine Netzwerkisolierung von produktiven VPCs besteht.                                                 |   2    |  D/V  |

---

## C4.3 Netzwerksicherheit & Zugangskontrolle

Implementieren Sie eine Zero-Trust-Netzwerkarchitektur mit Standard-Deny-Richtlinien und verschlüsselter Kommunikation.

|   #   | Beschreibung                                                                                                                                                                                                                                             | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.3.1 | Überprüfen Sie, ob Kubernetes NetworkPolicies oder eine äquivalente Lösung standardmäßig den Ingress/Egress blockiert und explizite Zulassungsregeln für erforderliche Ports (443, 8080 usw.) implementiert.                                             |   1    |  D/V  |
| 4.3.2 | Überprüfen Sie, ob SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatbasierte Authentifizierung erfordern.                                                                               |   1    |  D/V  |
| 4.3.3 | Stellen Sie sicher, dass ausgehender Datenverkehr über HTTP/HTTPS-Proxys (Squid, Istio oder Cloud-NAT-Gateways) mit Domain-Zulassungslisten gefiltert wird und blockierte Anfragen protokolliert werden.                                                 |   2    |  D/V  |
| 4.3.4 | Stellen Sie sicher, dass die Kommunikation zwischen den Diensten Mutual TLS verwendet, die Zertifikate gemäß der organisatorischen Richtlinie regelmäßig ausgetauscht werden und die Zertifikatsvalidierung durchgesetzt wird (keine skip-verify-Flags). |   2    |  D/V  |
| 4.3.5 | Stellen Sie sicher, dass die KI-Infrastruktur in dedizierten VPCs/VNets ohne direkten Internetzugang betrieben wird und nur über NAT-Gateways oder Bastion Hosts kommuniziert.                                                                           |   2    |  D/V  |

---

## C4.4 Geheimnis- und kryptografisches Schlüsselmanagement

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatisierte Rotation mit Zero-Trust-Zugriff.

|   #   | Beschreibung                                                                                                                                                                                                                | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.4.1 | Stellen Sie sicher, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager mit ruhender Verschlüsselung unter Verwendung von AES-256 gespeichert werden.                      |   1    |  D/V  |
| 4.4.2 | Überprüfen Sie, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) erzeugt werden und eine Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie erfolgt.    |   1    |  D/V  |
| 4.4.3 | Stellen Sie sicher, dass die Rotation von Geheimnissen automatisiert ist mit einer Zero-Downtime-Bereitstellung und einer sofortigen Rotation, die durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.           |   2    |  D/V  |
| 4.4.4 | Stellen Sie sicher, dass Container-Images mit Tools (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds blockieren, die API-Schlüssel, Passwörter oder Zertifikate enthalten.                            |   2    |  D/V  |
| 4.4.5 | Überprüfen Sie, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Prüfprotokolle mit Benutzeridentitäten und Zeitstempeln aufgezeichnet wird.    |   2    |  D/V  |
| 4.4.6 | Stellen Sie sicher, dass Geheimnisse über Kubernetes-Secrets, eingehängte Volumes oder Init-Container injiziert werden, und gewährleisten Sie, dass Geheimnisse niemals in Umgebungsvariablen oder Images eingebettet sind. |   2    |  D/V  |

---

## C4.5 AI Workload-Sandboxing und Validierung

Isolieren Sie nicht vertrauenswürdige KI-Modelle in sicheren Sandboxes mit umfassender Verhaltensanalyse.

|   #   | Beschreibung                                                                                                                                                                                                                       | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.5.1 | Stellen Sie sicher, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit den Flags --security-opt=no-new-privileges und --read-only ausgeführt werden.                                |   1    |  D/V  |
| 4.5.2 | Überprüfen Sie, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost mit allen externen Anfragen, die durch iptables-Regeln blockiert werden.                                    |   1    |  D/V  |
| 4.5.3 | Stellen Sie sicher, dass die Validierung des KI-Modells automatisierte Red-Team-Tests mit organisatorisch definiertem Testumfang und Verhaltensanalysen zur Backdoor-Erkennung umfasst.                                            |   2    |  D/V  |
| 4.5.4 | Stellen Sie sicher, dass vor der Freigabe eines KI-Modells für die Produktion die Ergebnisse der Sandbox kryptografisch von autorisiertem Sicherheitspersonal signiert und in unveränderlichen Prüfprotokollen gespeichert werden. |   2    |  D/V  |
| 4.5.5 | Stellen Sie sicher, dass Sandbox-Umgebungen zwischen den Bewertungen zerstört und aus goldenen Images mit vollständiger Bereinigung von Dateisystem und Arbeitsspeicher neu erstellt werden.                                       |   2    |  D/V  |

---

## C4.6 Überwachung der Infrastruktur-Sicherheit

Infrastruktur kontinuierlich mit automatisierter Behebung und Echtzeit-Benachrichtigung scannen und überwachen.

|   #   | Beschreibung                                                                                                                                                                                                                             | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.6.1 | Verifizieren Sie, dass Container-Images gemäß den organisatorischen Zeitplänen gescannt werden, wobei CRITISCHE Schwachstellen basierend auf den organisatorischen Risikoschwellen den Einsatz blockieren.                               |   1    |  D/V  |
| 4.6.2 | Verifizieren Sie, dass die Infrastruktur die CIS-Benchmarks oder NIST 800-53-Steuerungen mit organisatorisch definierten Compliance-Schwellenwerten erfüllt und automatisierte Behebungen für nicht bestandene Prüfungen vorhanden sind. |   1    |  D/V  |
| 4.6.3 | Überprüfen Sie, ob Schwachstellen mit hoher Schwere entsprechend den Zeitplänen des organisatorischen Risikomanagements gepatcht werden, einschließlich Notfallverfahren für aktiv ausgenutzte CVEs.                                     |   2    |  D/V  |
| 4.6.4 | Überprüfen Sie, ob Sicherheitswarnungen mit SIEM-Plattformen (Splunk, Elastic oder Sentinel) unter Verwendung von CEF- oder STIX/TAXII-Formaten mit automatischer Anreicherung integriert werden.                                        |   2    |   V   |
| 4.6.5 | Überprüfen Sie, dass Infrastrukturmetriken mit SLA-Dashboards und Managementberichten an Überwachungssysteme (Prometheus, DataDog) exportiert werden.                                                                                    |   3    |   V   |
| 4.6.6 | Überprüfen Sie, dass Konfigurationsabweichungen mithilfe von Tools (Chef InSpec, AWS Config) gemäß den organisatorischen Überwachungsanforderungen erkannt werden, mit automatischer Rücksetzung bei nicht autorisierten Änderungen.     |   2    |  D/V  |

---

## C4.7 KI-Infrastruktur Ressourcenmanagement

Verhindern Sie Ressourcenerschöpfungsangriffe und stellen Sie durch Quoten und Überwachung eine faire Ressourcenzuteilung sicher.

|   #   | Beschreibung                                                                                                                                                                                                                                             | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.7.1 | Überprüfen Sie, ob die GPU/TPU-Auslastung überwacht wird, wobei bei organisationsweit definierten Schwellenwerten Alarme ausgelöst werden und basierend auf Kapazitätsmanagementrichtlinien automatische Skalierung oder Lastenausgleich aktiviert wird. |   1    |  D/V  |
| 4.7.2 | Überprüfen Sie, ob die Kennzahlen der KI-Arbeitslasten (Inferenze-Latenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Überwachungsanforderungen erfasst und mit der Auslastung der Infrastruktur korreliert werden.                              |   1    |  D/V  |
| 4.7.3 | Überprüfen Sie, ob Kubernetes ResourceQuotas oder gleichwertige Mechanismen einzelne Workloads gemäß den organisatorischen Richtlinien zur Ressourcenverteilung mit durchgesetzten Hard-Limits begrenzen.                                                |   2    |  D/V  |
| 4.7.4 | Überprüfen Sie, dass die Kostenüberwachung die Ausgaben pro Arbeitslast/Mieter verfolgt, mit Warnmeldungen basierend auf den organisatorischen Budgetgrenzen und automatisierten Kontrollen zur Vermeidung von Budgetüberschreitungen.                   |   2    |   V   |
| 4.7.5 | Stellen Sie sicher, dass die Kapazitätsplanung historische Daten mit organisatorisch definierten Prognosezeiträumen verwendet und eine automatisierte Ressourcenbereitstellung basierend auf Nachfragemustern erfolgt.                                   |   3    |   V   |
| 4.7.6 | Überprüfen Sie, ob Ressourcenerschöpfung gemäß den organisatorischen Reaktionsanforderungen zu Auslösern von Circuit Breakern führt, einschließlich der Ratenbegrenzung basierend auf Kapazitätsrichtlinien und Arbeitslastisolierung.                   |   2    |  D/V  |

---

## C4.8 Trennung der Umgebungen und Steuerung der Promotion

Durchsetzung strenger Umgebungsgrenzen mit automatisierten Freigabeschranken und Sicherheitsvalidierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                             | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 4.8.1 | Überprüfen Sie, dass die Entwicklungs-, Test- und Produktionsumgebungen in getrennten VPCs/VNets ausgeführt werden, ohne gemeinsame IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen.                                                                            |   1    |  D/V  |
| 4.8.2 | Stellen Sie sicher, dass die Freigabe einer Umgebung die Genehmigung durch organisatorisch definierte autorisierte Personen mit kryptografischen Signaturen und unveränderbaren Prüfpfaden erfordert.                                                                    |   1    |  D/V  |
| 4.8.3 | Überprüfen Sie, ob Produktionsumgebungen den SSH-Zugang blockieren, Debug-Endpunkte deaktivieren und Änderungsanfragen mit organisatorischen Vorankündigungsanforderungen außer in Notfällen vorschreiben.                                                               |   2    |  D/V  |
| 4.8.4 | Stellen Sie sicher, dass Änderungen an Infrastructure-as-Code vor dem Zusammenführen in den Hauptzweig eine Peer-Review mit automatisierten Tests und Sicherheitsprüfungen erfordern.                                                                                    |   2    |  D/V  |
| 4.8.5 | Stellen Sie sicher, dass Nicht-Produktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert, synthetische Datengenerierung durchgeführt oder eine vollständige Datenmaskierung mit Entfernung von personenbezogenen Daten (PII) verifiziert wurde. |   2    |  D/V  |
| 4.8.6 | Stellen Sie sicher, dass die Beförderungspunkte automatisierte Sicherheitstests (SAST, DAST, Container-Scanning) enthalten, bei denen keine KRISELNDE Befunde zur Genehmigung erforderlich sind.                                                                         |   2    |  D/V  |

---

## C4.9 Infrastruktur-Backup & Wiederherstellung

Sichern Sie die Widerstandsfähigkeit der Infrastruktur durch automatisierte Backups, getestete Wiederherstellungsverfahren und Katastrophenwiederherstellungsfähigkeiten.

|   #   | Beschreibung                                                                                                                                                                                                                         | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 4.9.1 | Überprüfen Sie, ob Infrastrukturkonfigurationen gemäß den organisatorischen Sicherungsplänen mit der Implementierung der 3-2-1-Sicherungsstrategie in geografisch getrennte Regionen gesichert werden.                               |   1    |  D/V  |
| 4.9.2 | Überprüfen Sie, ob Backup-Systeme in isolierten Netzwerken mit separaten Anmeldeinformationen und air-gapped Speicherlösungen für den Schutz vor Ransomware betrieben werden.                                                        |   2    |  D/V  |
| 4.9.3 | Stellen Sie sicher, dass Wiederherstellungsverfahren gemäß den organisatorischen Zeitplänen mit RTO- und RPO-Zielen, die den organisatorischen Anforderungen entsprechen, durch automatisierte Tests überprüft und validiert werden. |   2    |   V   |
| 4.9.4 | Stellen Sie sicher, dass die Notfallwiederherstellung KI-spezifische Runbooks mit der Wiederherstellung von Modellgewichten, dem Wiederaufbau von GPU-Clustern und der Abbildung von Dienstabhängigkeiten umfasst.                   |   3    |   V   |

---

## C4.10 Infrastruktur-Compliance & Governance

Erhalten Sie die Einhaltung gesetzlicher Vorschriften durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollen.

|   #    | Beschreibung                                                                                                                                                                                                                       | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.10.1 | Stellen Sie sicher, dass die Einhaltung der Infrastruktur gemäß den organisatorischen Zeitplänen anhand der SOC 2-, ISO 27001- oder FedRAMP-Kontrollen bewertet wird, einschließlich der automatisierten Erfassung von Nachweisen. |   2    |  D/V  |
| 4.10.2 | Stellen Sie sicher, dass die Infrastruktur-Dokumentation Netzwerkdiagramme, Datenflusskarten und Bedrohungsmodelle enthält, die gemäß den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden.            |   2    |   V   |
| 4.10.3 | Stellen Sie sicher, dass Infrastrukturänderungen einer automatisierten Bewertung der Compliance-Auswirkungen unterzogen werden, einschließlich regulatorischer Genehmigungsprozesse für risikoreiche Änderungen.                   |   3    |  D/V  |

---

## C4.11 KI-Hardware-Sicherheit

Sichern Sie KI-spezifische Hardwarekomponenten, einschließlich GPUs, TPUs und spezialisierter KI-Beschleuniger.

|   #    | Beschreibung                                                                                                                                                                                                                     | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.11.1 | Stellen Sie sicher, dass die Firmware des KI-Beschleunigers (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen verifiziert wird und gemäß den Zeitplänen des organisatorischen Patch-Managements aktualisiert wird.        |   2    |  D/V  |
| 4.11.2 | Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestierung mit TPM 2.0, Intel TXT oder AMD SVM validiert wird.                                                 |   2    |  D/V  |
| 4.11.3 | Überprüfen Sie, dass der GPU-Speicher zwischen Arbeitslasten mittels SR-IOV, MIG (Multi-Instance GPU) oder einer entsprechenden Hardware-Partitionierung isoliert ist, wobei eine Speicherbereinigung zwischen den Jobs erfolgt. |   2    |  D/V  |
| 4.11.4 | Stellen Sie sicher, dass die Lieferkette für AI-Hardware eine Herkunftsüberprüfung mit Herstellerzertifikaten und eine Validierung von manipulationssicherer Verpackung beinhaltet.                                              |   3    |   V   |
| 4.11.5 | Überprüfen Sie, dass Hardware-Sicherheitsmodule (HSMs) AI-Modellgewichte und kryptografische Schlüssel mit einer FIPS 140-2 Level 3- oder Common Criteria EAL4+-Zertifizierung schützen.                                         |   3    |  D/V  |

---

## C4.12 Kanten- und verteilte KI-Infrastruktur

Sichere verteilte KI-Einsätze, einschließlich Edge Computing, föderiertem Lernen und Multi-Site-Architekturen.

|   #    | Beschreibung                                                                                                                                                                                                                   | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 4.12.1 | Stellen Sie sicher, dass Edge-AI-Geräte sich mit der zentralen Infrastruktur über mutual TLS authentifizieren und dass die Gerätezertifikate gemäß der organisatorischen Zertifikatsverwaltungsrichtlinie ausgetauscht werden. |   2    |  D/V  |
| 4.12.2 | Stellen Sie sicher, dass Edge-Geräte einen sicheren Start mit verifizierten Signaturen und einer Rollback-Schutzfunktion implementieren, um Firmware-Abwärtstransferangriffe zu verhindern.                                    |   2    |  D/V  |
| 4.12.3 | Stellen Sie sicher, dass die verteilte KI-Koordination byzantinisch fehlertolerante Konsensalgorithmen mit Teilnehmervalidierung und Erkennung bösartiger Knoten verwendet.                                                    |   3    |  D/V  |
| 4.12.4 | Stellen Sie sicher, dass die Kommunikation zwischen Edge und Cloud Bandbreitenbegrenzung, Datenkompression und Offline-Betriebsfähigkeiten mit sicherer lokaler Speicherung umfasst.                                           |   3    |  D/V  |

---

## C4.13 Multi-Cloud- und Hybrid-Infrastruktur-Sicherheit

Sichern Sie KI-Arbeitslasten über mehrere Cloud-Anbieter hinweg sowie bei hybriden Cloud-On-Premises-Bereitstellungen.

|   #    | Beschreibung                                                                                                                                                                                                                          | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.13.1 | Stellen Sie sicher, dass Multi-Cloud-KI-Bereitstellungen cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralem Richtlinienmanagement über die Anbieter hinweg verwenden.                                                  |   2    |  D/V  |
| 4.13.2 | Stellen Sie sicher, dass der Cloud-übergreifende Datentransfer Ende-zu-Ende-Verschlüsselung mit kundenseitig verwalteten Schlüsseln verwendet und Datenresidenzkontrollen gemäß der jeweiligen Gerichtsbarkeit durchgesetzt werden.   |   2    |  D/V  |
| 4.13.3 | Überprüfen Sie, dass hybride Cloud-AI-Workloads konsistente Sicherheitsrichtlinien sowohl in On-Premise- als auch in Cloud-Umgebungen mit einheitlichem Monitoring und Alarme implementieren.                                         |   2    |  D/V  |
| 4.13.4 | Stellen Sie sicher, dass die Vermeidung von Cloud-Anbieter-Bindung tragbare Infrastructure-as-Code, standardisierte APIs und Datenexportfunktionen mit Formatkonvertierungstools umfasst.                                             |   3    |   V   |
| 4.13.5 | Stellen Sie sicher, dass die Multi-Cloud-Kostenoptimierung Sicherheitskontrollen umfasst, die sowohl die Ausbreitung von Ressourcen verhindern als auch unautorisierte Kosten für datenübergreifende Cloud-Übertragungen unterbinden. |   3    |   V   |

---

## C4.14 Infrastruktur-Automatisierung & GitOps-Sicherheit

Sichern Sie Automatisierungspipelines für die Infrastruktur und GitOps-Workflows für das Management von KI-Infrastrukturen.

|   #    | Beschreibung                                                                                                                                                                                                                                 | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.14.1 | Überprüfen Sie, ob GitOps-Repositories signierte Commits mit GPG-Schlüsseln erfordern und Branch-Schutzregeln implementiert sind, die direkte Pushes zu Hauptzweigen verhindern.                                                             |   2    |  D/V  |
| 4.14.2 | Verifizieren Sie, dass die Infrastrukturautomatisierung Drift-Erkennung mit automatischen Behebungs- und Rollback-Funktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen für unautorisierte Änderungen ausgelöst werden. |   2    |  D/V  |
| 4.14.3 | Stellen Sie sicher, dass die automatisierte Bereitstellung der Infrastruktur eine Überprüfung der Sicherheitsrichtlinien beinhaltet und die Bereitstellung bei nicht konformen Konfigurationen blockiert.                                    |   2    |  D/V  |
| 4.14.4 | Stellen Sie sicher, dass Geheimnisse der Infrastrukturautomatisierung über externe Geheimnis-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.                                                |   2    |  D/V  |
| 4.14.5 | Überprüfen Sie, ob die selbstheilende Infrastruktur Sicherheitsereigniskorrelation mit automatisierter Vorfallreaktion und Benachrichtigungsabläufen für Beteiligte umfasst.                                                                 |   3    |   V   |

---

## C4.15 Quantenresistente Infrastruktursicherheit

Bereiten Sie die KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor, indem Sie postquantum Kryptographie und quantensichere Protokolle einsetzen.

|   #    | Beschreibung                                                                                                                                                                                                              | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.15.1 | Stellen Sie sicher, dass die KI-Infrastruktur NIST-zertifizierte postquantum-kryptografische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für den Schlüsselaustausch und digitale Signaturen implementiert. |   3    |  D/V  |
| 4.15.2 | Verifizieren Sie, dass Quanten-Schlüsselaustauschsysteme (QKD) für hochsichere KI-Kommunikationen mit quantensicheren Schlüsselverwaltungsprotokollen implementiert sind.                                                 |   3    |  D/V  |
| 4.15.3 | Stellen Sie sicher, dass kryptografische Agilitätsrahmen eine schnelle Migration zu neuen postquanten Algorithmus ermöglichen, einschließlich automatisierter Zertifikats- und Schlüsselrotation.                         |   3    |  D/V  |
| 4.15.4 | Stellen Sie sicher, dass die Quanten-Bedrohungsmodellierung die Anfälligkeit der KI-Infrastruktur für Quantenangriffe bewertet und dokumentierte Migrationszeitpläne sowie Risikoanalysen enthält.                        |   3    |   V   |
| 4.15.5 | Stellen Sie sicher, dass hybride klassische-quantum kryptografische Systeme während der Quantenübergangsphase einen Schutz-in-Tiefe bieten und eine Leistungsüberwachung durchführen.                                     |   3    |  D/V  |

---

## C4.16 Vertrauliches Rechnen & Sichere Enklaven

Schützen Sie AI-Arbeitslasten und Modellgewichte mithilfe von hardwarebasierten Trusted Execution Environments und Technologien für vertrauliches Computing.

|   #    | Beschreibung                                                                                                                                                                                | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.16.1 | Überprüfen Sie, dass sensible KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsüberprüfung ausgeführt werden.      |   3    |  D/V  |
| 4.16.2 | Überprüfen Sie, ob vertrauliche Container (Kata Containers, gVisor mit vertraulichem Computing) KI-Workloads mit hardwaregestützter Speicher­verschlüsselung isolieren.                     |   3    |  D/V  |
| 4.16.3 | Überprüfen Sie, dass die Remote-Attestierung die Integrität der Enklave validiert, bevor KI-Modelle mit kryptografischem Nachweis der Authentizität der Ausführungsumgebung geladen werden. |   3    |  D/V  |
| 4.16.4 | Verifizieren Sie, dass vertrauliche KI-Inferenzdienste die Modellextraktion durch verschlüsselte Berechnung mit versiegelten Modellgewichten und geschützter Ausführung verhindern.         |   3    |  D/V  |
| 4.16.5 | Verifizieren Sie, dass die Orchestrierung der Trusted Execution Environment den Lebenszyklus der sicheren Enklave mit Fernattestierung und verschlüsselten Kommunikationskanälen verwaltet. |   3    |  D/V  |
| 4.16.6 | Überprüfen Sie, dass sichere Mehrparteienberechnung (SMPC) gemeinsames KI-Training ermöglicht, ohne individuelle Datensätze oder Modellparameter offenzulegen.                              |   3    |  D/V  |

---

## C4.17 Zero-Knowledge-Infrastruktur

Implementieren Sie Zero-Knowledge-Beweissysteme zur datenschutzfreundlichen KI-Verifikation und -Authentifizierung, ohne sensible Informationen preiszugeben.

|   #    | Beschreibung                                                                                                                                                                                            | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.17.1 | Stellen Sie sicher, dass Zero-Knowledge-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität des KI-Modells und die Herkunft des Trainings verifizieren, ohne Modellgewichte oder Trainingsdaten offenzulegen. |   3    |  D/V  |
| 4.17.2 | Überprüfen Sie, dass ZK-basierte Authentifizierungssysteme eine datenschutzfreundliche Benutzerüberprüfung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen preiszugeben.              |   3    |  D/V  |
| 4.17.3 | Überprüfen Sie, dass Private Set Intersection (PSI)-Protokolle eine sichere Datenabstimmung für föderiertes KI ermöglichen, ohne einzelne Datensätze offenzulegen.                                      |   3    |  D/V  |
| 4.17.4 | Überprüfen Sie, dass Zero-Knowledge Machine Learning (ZKML)-Systeme überprüfbare KI-Schlussfolgerungen mit kryptografischem Nachweis der korrekten Berechnung ermöglichen.                              |   3    |  D/V  |
| 4.17.5 | Überprüfen Sie, dass ZK-Rollups skalierbare, datenschutzwahrende KI-Transaktionsverarbeitung mit Sammelverifizierung und reduziertem Rechenaufwand bieten.                                              |   3    |  D/V  |

---

## C4.18 Schutz vor Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor zeitlichen, leistungsbezogenen, elektromagnetischen und cache-basierten Seitenkanalangriffen, die sensible Informationen preisgeben könnten.

|   #    | Beschreibung                                                                                                                                                                             | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.18.1 | Stellen Sie sicher, dass die AI-Inferenzzeit durch Algorithmen mit konstanter Laufzeit und Padding normalisiert wird, um zeitbasierte Modellextraktionsangriffe zu verhindern.           |   3    |  D/V  |
| 4.18.2 | Überprüfen Sie, dass der Schutz vor Leistungsanalyse Rauschinjektion, Netzleitungsfilterung und randomisierte Ausführungsmuster für KI-Hardware umfasst.                                 |   3    |  D/V  |
| 4.18.3 | Überprüfen Sie, dass die Seiteneffektminderung basierend auf dem Cache Cache-Partitionierung, Zufallszuweisung und Flush-Befehle verwendet, um Informationslecks zu verhindern.          |   3    |  D/V  |
| 4.18.4 | Stellen Sie sicher, dass der Schutz vor elektromagnetischer Abstrahlung Abschirmung, Signalfilterung und randomisierte Verarbeitung umfasst, um TEMPEST-ähnliche Angriffe zu verhindern. |   3    |  D/V  |
| 4.18.5 | Überprüfen Sie, dass mikroarchitektonische Seitenkanalabwehrmechanismen spekulative Ausführungssteuerungen und die Verschleierung von Speicherzugriffsmustern beinhalten.                |   3    |  D/V  |

---

## C4.19 Neuromorphe & spezialisierte KI-Hardware-Sicherheit

Sichern Sie neu aufkommende KI-Hardwarearchitekturen, einschließlich neuromorpher Chips, FPGAs, kundenspezifischer ASICs und optischer Rechensysteme.

|   #    | Beschreibung                                                                                                                                                                                        | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.19.1 | Überprüfen Sie, dass die Sicherheit von neuromorphen Chips die Verschlüsselung von Spike-Mustern, den Schutz der synaptischen Gewichte und die hardwarebasierte Validierung der Lernregeln umfasst. |   3    |  D/V  |
| 4.19.2 | Überprüfen Sie, dass FPGA-basierte KI-Beschleuniger Bitstream-Verschlüsselung, Anti-Tamper-Mechanismen und sicheres Laden der Konfiguration mit authentifizierten Updates implementieren.           |   3    |  D/V  |
| 4.19.3 | Überprüfen Sie, ob die kundenspezifische ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, eine Hardware-Root of Trust und eine sichere Schlüsselspeicherung mit Manipulationserkennung umfasst.      |   3    |  D/V  |
| 4.19.4 | Überprüfen Sie, dass optische Computersysteme quantensichere optische Verschlüsselung, sichere photonische Schaltung und geschützte optische Signalverarbeitung implementieren.                     |   3    |  D/V  |
| 4.19.5 | Stellen Sie sicher, dass hybride analog-digitale KI-Chips sichere analoge Berechnungen, geschützte Gewichtsspeicherung und authentifizierte Analog-Digital-Wandlung umfassen.                       |   3    |  D/V  |

---

## C4.20 Datenschutzwahrende Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzfreundliche Berechnungen, um sensible Daten während der KI-Verarbeitung und -Analyse zu schützen.

|   #    | Beschreibung                                                                                                                                                                                                   | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.20.1 | Überprüfen Sie, dass die Infrastruktur für homomorphe Verschlüsselung verschlüsselte Berechnungen bei sensiblen KI-Arbeitslasten mit kryptographischer Integritätsprüfung und Leistungsüberwachung ermöglicht. |   3    |  D/V  |
| 4.20.2 | Überprüfen Sie, dass Systeme für private Informationsabfrage Datenbankabfragen ermöglichen, ohne Abfragemuster preiszugeben, und dabei den Zugriffsmustern kryptografischen Schutz bieten.                     |   3    |  D/V  |
| 4.20.3 | Überprüfen Sie, dass sichere Mehrparteienberechnungsprotokolle eine datenschutzfreundliche KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenberechnungen offenzulegen.                             |   3    |  D/V  |
| 4.20.4 | Überprüfen Sie, dass die datenschutzfreundliche Schlüsselverwaltung verteilte Schlüsselerzeugung, Schwellenwert-Kryptographie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.             |   3    |  D/V  |
| 4.20.5 | Überprüfen Sie, ob die Leistung des datenschutzwahrenden Rechnens durch Batch-Verarbeitung, Caching und Hardwarebeschleunigung optimiert ist, während kryptografische Sicherheitsgarantien erhalten bleiben.   |   3    |  D/V  |

---

## C4.15 Agent Framework Cloud-Integration Sicherheit & hybride Bereitstellung

Sicherheitskontrollen für cloud-integrierte Agentenframeworks mit hybriden On-Premises-/Cloud-Architekturen.

|   #    | Beschreibung                                                                                                                                              | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 4.15.1 | Überprüfen Sie, ob die Integration der Cloud-Speicherung eine Ende-zu-Ende-Verschlüsselung mit agentengesteuertem Schlüsselmanagement verwendet.          |   1    |  D/V  |
| 4.15.2 | Stellen Sie sicher, dass die Sicherheitsgrenzen der hybriden Bereitstellung klar definiert sind und verschlüsselte Kommunikationskanäle verwendet werden. |   2    |  D/V  |
| 4.15.3 | Überprüfen Sie, ob der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung beinhaltet.                      |   2    |  D/V  |
| 4.15.4 | Stellen Sie sicher, dass die Anforderungen an den Datenaufenthalt durch kryptografische Bestätigung der Speicherorte durchgesetzt werden.                 |   3    |  D/V  |
| 4.15.5 | Überprüfen Sie, dass Sicherheitsbewertungen von Cloud-Anbietern agentenspezifische Bedrohungsmodellierung und Risikoanalyse beinhalten.                   |   3    |  D/V  |

---

## Referenzen

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [NIST SP 800-190: Application Container Security Guide](https://csrc.nist.gov/publications/detail/sp/800-190/final)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST SP 800-53: Security Controls for Federal Information Systems](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
* [FIPS 140-2 Security Requirements](https://csrc.nist.gov/publications/detail/fips/140/2/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
* [IEEE 2857: Privacy Engineering for AI Systems](https://standards.ieee.org/ieee/2857/7273/)
* [NIST SP 800-161: Cybersecurity Supply Chain Risk Management](https://csrc.nist.gov/publications/detail/sp/800-161/rev-1/final)
* [NIST Post-Quantum Cryptography Standards](https://csrc.nist.gov/Projects/post-quantum-cryptography)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/tools/software-guard-extensions/overview.html)
* [AMD SEV-SNP White Paper](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf)
* [ARM TrustZone Technology](https://developer.arm.com/ip-products/security-ip/trustzone)
* [ZK-SNARKs: A Gentle Introduction](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)
* [NIST SP 800-57: Cryptographic Key Management](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-5/final)
* [Side-Channel Attack Countermeasures](https://link.springer.com/book/10.1007/978-3-319-75268-6)
* [Neuromorphic Computing Security Challenges](https://ieeexplore.ieee.org/document/9458103)
* [FPGA Security: Fundamentals, Evaluation, and Countermeasures](https://link.springer.com/book/10.1007/978-3-319-90385-9)
* [Microsoft SEAL: Homomorphic Encryption Library](https://github.com/Microsoft/SEAL)
* [HElib: Homomorphic Encryption Library](https://github.com/homenc/HElib)
* [PALISADE Lattice Cryptography Library](https://palisade-crypto.org/)
* [Differential Privacy: A Survey of Results](https://link.springer.com/chapter/10.1007/978-3-540-79228-4_1)
* [Secure Aggregation for Federated Learning](https://eprint.iacr.org/2017/281.pdf)
* [Private Information Retrieval: Concepts and Constructions](https://link.springer.com/book/10.1007/978-3-030-16234-8)

