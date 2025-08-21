# C4 Infrastruktur, Konfiguration & Bereitstellungssicherheit

## Kontrollziel

Die KI-Infrastruktur muss gegen Privilegieneskalation, Manipulation der Lieferkette und laterale Bewegungen durch sichere Konfiguration, Laufzeitisolierung, vertrauenswürdige Bereitstellungspipelines und umfassendes Monitoring gehärtet werden. Nur autorisierte, validierte Infrastrukturkomponenten und Konfigurationen gelangen über kontrollierte Prozesse, die Sicherheit, Integrität und Prüfbarkeit gewährleisten, in die Produktion.

Kernziel der Sicherheit: Nur kryptographisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen über automatisierte Validierungspipelines, die Sicherheitsrichtlinien durchsetzen und unveränderliche Prüfpfade aufrechterhalten, in die Produktion.

---

## C4.1 Laufzeitumgebungsisolation

Verhindern Sie Container-Ausbrüche und Privilegieneskalationen durch kernelbasierte Isolationsprimitive und zwingende Zugriffskontrollen.

|   #   | Beschreibung                                                                                                                                                                                                                                     | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.1.1 | Überprüfen Sie, dass alle KI-Container ALLE Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und ausdrücklich in den Sicherheitsgrundlagen dokumentierten, erforderlichen Fähigkeiten deaktivieren.                                                |   1   |  D/V  |
| 4.1.2 | Überprüfen Sie, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denen in vorab genehmigten Allowlisten, wobei Verstöße zur Beendigung des Containers und zur Generierung von Sicherheitswarnungen führen.                              |   1   |  D/V  |
| 4.1.3 | Stellen Sie sicher, dass KI-Arbeitslasten mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei noexec-Mount-Optionen durchgesetzt sind.                     |   2   |  D/V  |
| 4.1.4 | Überprüfen Sie, ob die eBPF-basierte Laufzeitüberwachung (Falco, Tetragon oder ein Äquivalent) Versuche zur Rechteerweiterung erkennt und automatisch die verursachenden Prozesse innerhalb der organisatorischen Reaktionszeitvorgaben beendet. |   2   |  D/V  |
| 4.1.5 | Stellen Sie sicher, dass KI-Arbeitslasten mit hohem Risiko in hardwareisolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestationsüberprüfung ausgeführt werden.                                                |   3   |  D/V  |

---

## C4.2 Sichere Build- und Deployment-Pipelines

Sichern Sie die kryptografische Integrität und die Sicherheit der Lieferkette durch reproduzierbare Builds und signierte Artefakte.

|   #   | Beschreibung                                                                                                                                                                                                                     | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.2.1 | Stellen Sie sicher, dass Infrastructure-as-Code bei jedem Commit mit Tools wie tfsec, Checkov oder Terrascan gescannt wird und Merge-Vorgänge bei CRITICAL- oder HIGH-Schweregrad-Funden blockiert werden.                       |   1   |  D/V  |
| 4.2.2 | Überprüfen Sie, dass Container-Builds mit identischen SHA256-Hashes über mehrere Builds hinweg reproduzierbar sind, und erzeugen Sie SLSA Level 3 Provenance-Attestierungen, die mit Sigstore signiert sind.                     |   1   |  D/V  |
| 4.2.3 | Verifizieren Sie, dass Container-Images CycloneDX- oder SPDX-SBOMs einbetten und mit Cosign signiert sind, bevor sie in das Registry hochgeladen werden, wobei unsignierte Images bei der Bereitstellung abgelehnt werden.       |   2   |  D/V  |
| 4.2.4 | Überprüfen Sie, ob CI/CD-Pipelines OIDC-Tokens von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity mit Lebensdauern verwenden, die die Grenzwerte der organisatorischen Sicherheitsrichtlinien nicht überschreiten.  |   2   |  D/V  |
| 4.2.5 | Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Provenienz während des Bereitstellungsprozesses vor der Containerausführung validiert werden und dass Verifizierungsfehler dazu führen, dass die Bereitstellung fehlschlägt. |   2   |  D/V  |
| 4.2.6 | Überprüfen Sie, dass Build-Umgebungen in flüchtigen Containern oder VMs ohne persistenten Speicher und mit Netzwerkisolation von Produktions-VPCs ausgeführt werden.                                                             |   2   |  D/V  |

---

## C4.3 Netzwerksicherheit & Zugriffskontrolle

Implementieren Sie Zero-Trust-Netzwerke mit Standard-Verweigerungsrichtlinien und verschlüsselter Kommunikation.

|   #   | Beschreibung                                                                                                                                                                                                                      | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.3.1 | Überprüfen Sie, ob Kubernetes NetworkPolicies oder eine gleichwertige Lösung ein Standard-Deny für Ingress/Egress mit expliziten Zulassungsregeln für erforderliche Ports (443, 8080 usw.) implementiert.                         |   1   |  D/V  |
| 4.3.2 | Überprüfen Sie, ob SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatbasierte Authentifizierung erfordern.                                                        |   1   |  D/V  |
| 4.3.3 | Stellen Sie sicher, dass ausgehender Datenverkehr über HTTP/HTTPS-Proxys (Squid, Istio oder Cloud-NAT-Gateways) mit Domain-Whitelists gefiltert wird und blockierte Anfragen protokolliert werden.                                |   2   |  D/V  |
| 4.3.4 | Stellen Sie sicher, dass die Kommunikation zwischen Diensten Mutual TLS verwendet, wobei Zertifikate gemäß der Organisationsrichtlinie rotiert werden und die Zertifikatsvalidierung durchgesetzt wird (keine Skip-Verify-Flags). |   2   |  D/V  |
| 4.3.5 | Stellen Sie sicher, dass die KI-Infrastruktur in dedizierten VPCs/VNets ohne direkten Internetzugang betrieben wird und ausschließlich über NAT-Gateways oder Bastion Hosts kommuniziert.                                         |   2   |  D/V  |

---

## C4.4 Geheimnisse & Verwaltung kryptografischer Schlüssel

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatisierte Rotation mit Zero-Trust-Zugriff.

|   #   | Beschreibung                                                                                                                                                                                                                    | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.4.1 | Stellen Sie sicher, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager mit ruhender Verschlüsselung unter Verwendung von AES-256 gespeichert sind.                            |   1   |  D/V  |
| 4.4.2 | Stellen Sie sicher, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) generiert werden und eine Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie erfolgt.  |   1   |  D/V  |
| 4.4.3 | Stellen Sie sicher, dass die Rotation von Secrets automatisiert ist, mit einer Zero-Downtime-Bereitstellung und sofortiger Rotation, die durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.                         |   2   |  D/V  |
| 4.4.4 | Stellen Sie sicher, dass Container-Images mit Tools (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds mit API-Schlüsseln, Passwörtern oder Zertifikaten blockieren.                                        |   2   |  D/V  |
| 4.4.5 | Stellen Sie sicher, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Audit-Logs mit Benutzeridentitäten und Zeitstempeln protokolliert wird.        |   2   |  D/V  |
| 4.4.6 | Stellen Sie sicher, dass Geheimnisse über Kubernetes-Secrets, eingehängte Volumes oder Init-Container injiziert werden, und vergewissern Sie sich, dass Geheimnisse niemals in Umgebungsvariablen oder Images eingebettet sind. |   2   |  D/V  |

---

## C4.5 KI-Arbeitslast-Sandboxing & Validierung

Isolieren Sie nicht vertrauenswürdige KI-Modelle in sicheren Sandboxes mit umfassender Verhaltensanalyse.

|   #   | Beschreibung                                                                                                                                                                                                                   | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.5.1 | Überprüfen Sie, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit den Flags --security-opt=no-new-privileges und --read-only ausgeführt werden.                                |   1   |  D/V  |
| 4.5.2 | Stellen Sie sicher, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost mit allen externen Anfragen, die durch iptables-Regeln blockiert sind.                              |   1   |  D/V  |
| 4.5.3 | Stellen Sie sicher, dass die Validierung des KI-Modells automatisierte Red-Team-Tests mit organisatorisch definiertem Testumfang und Verhaltensanalyse zur Erkennung von Hintertüren umfasst.                                  |   2   |  D/V  |
| 4.5.4 | Stellen Sie sicher, dass vor der Freigabe eines KI-Modells für die Produktion die Sandbox-Ergebnisse kryptografisch von autorisiertem Sicherheitspersonal signiert und in unveränderlichen Prüfprotokollen gespeichert werden. |   2   |  D/V  |
| 4.5.5 | Stellen Sie sicher, dass Sandbox-Umgebungen zwischen den Bewertungen zerstört und aus Gold-Images mit vollständiger Bereinigung des Dateisystems und des Speichers neu erstellt werden.                                        |   2   |  D/V  |

---

## C4.6 Infrastruktur-Sicherheitsüberwachung

Die Infrastruktur kontinuierlich mit automatisierter Behebung und Echtzeit-Benachrichtigungen scannen und überwachen.

|   #   | Beschreibung                                                                                                                                                                                                                             | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.6.1 | Stellen Sie sicher, dass Container-Images gemäß den organisatorischen Zeitplänen gescannt werden, wobei CRITICAL-Schwachstellen die Bereitstellung basierend auf den organisatorischen Risikoschwellen blockieren.                       |   1   |  D/V  |
| 4.6.2 | Überprüfen Sie, ob die Infrastruktur die CIS-Benchmarks oder NIST 800-53-Kontrollen mit organisatorisch definierten Compliance-Schwellenwerten erfüllt und automatisierte Behebungen bei fehlgeschlagenen Prüfungen durchgeführt werden. |   1   |  D/V  |
| 4.6.3 | Überprüfen Sie, ob Sicherheitslücken mit hoher Kritikalität gemäß den zeitlichen Vorgaben des organisatorischen Risikomanagements gepatcht werden, einschließlich Notfallverfahren für aktiv ausgenutzte CVEs.                           |   2   |  D/V  |
| 4.6.4 | Stellen Sie sicher, dass Sicherheitswarnungen mit SIEM-Plattformen (Splunk, Elastic oder Sentinel) unter Verwendung der CEF- oder STIX/TAXII-Formate mit automatischer Anreicherung integriert sind.                                     |   2   |   V   |
| 4.6.5 | Überprüfen Sie, ob Infrastrukturmetriken an Überwachungssysteme (Prometheus, DataDog) mit SLA-Dashboards und Managementberichten exportiert werden.                                                                                      |   3   |   V   |
| 4.6.6 | Überprüfen Sie, dass Konfigurationsabweichungen gemäß den organisatorischen Überwachungsanforderungen mit Werkzeugen (Chef InSpec, AWS Config) erkannt werden und eine automatische Rücksetzung für unautorisierte Änderungen erfolgt.   |   2   |  D/V  |

---

## C4.7 KI-Infrastruktur Ressourcenmanagement

Verhindern Sie Ressourcenerschöpfungsangriffe und gewährleisten Sie eine faire Ressourcenzuteilung durch Quoten und Überwachung.

|   #   | Beschreibung                                                                                                                                                                                                                                            | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.7.1 | Verifizieren Sie, dass die GPU/TPU-Auslastung überwacht wird, wobei bei organisationsweit definierten Schwellenwerten Alarme ausgelöst und automatische Skalierung oder Lastenausgleich basierend auf Kapazitätsmanagementrichtlinien aktiviert werden. |   1   |  D/V  |
| 4.7.2 | Überprüfen Sie, ob KI-Arbeitslastmetriken (Inferenzlatenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Überwachungsanforderungen erfasst und mit der Infrastruktur-Auslastung korreliert werden.                                                |   1   |  D/V  |
| 4.7.3 | Überprüfen Sie, dass Kubernetes ResourceQuotas oder entsprechende Mechanismen einzelne Workloads gemäß den organisatorischen Ressourcenallokationsrichtlinien mit durchgesetzten harten Grenzwerten begrenzen.                                          |   2   |  D/V  |
| 4.7.4 | Überprüfen Sie, ob die Kostenüberwachung die Ausgaben pro Arbeitslast/Mandant erfasst, mit Warnmeldungen basierend auf den Budgetgrenzen der Organisation und automatisierten Kontrollen für Budgetüberschreitungen.                                    |   2   |   V   |
| 4.7.5 | Stellen Sie sicher, dass die Kapazitätsplanung historische Daten mit organisatorisch definierten Prognosezeiträumen verwendet und eine automatisierte Ressourcenbereitstellung basierend auf Nachfrage mustern erfolgt.                                 |   3   |   V   |
| 4.7.6 | Überprüfen Sie, ob Ressourcenerschöpfung gemäß den organisatorischen Reaktionsanforderungen Circuit Breaker auslöst, einschließlich der Ratenbegrenzung basierend auf Kapazitätsrichtlinien und Arbeitslastisolierung.                                  |   2   |  D/V  |

---

## C4.8 Umgebungstrennung & Förderkontrollen

Erzwingen Sie strenge Umgebungsgrenzen mit automatisierten Freigabe-Gates und Sicherheitsvalidierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                               | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.8.1 | Stellen Sie sicher, dass Entwicklungs-, Test- und Produktionsumgebungen in separaten VPCs/VNets betrieben werden, ohne gemeinsame IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen.                                                                                |   1   |  D/V  |
| 4.8.2 | Stellen Sie sicher, dass die Förderung von Umgebungen die Genehmigung von organisatorisch definiertem autorisiertem Personal erfordert, mit kryptografischen Signaturen und unveränderbaren Prüfpfaden.                                                                    |   1   |  D/V  |
| 4.8.3 | Überprüfen Sie, dass Produktionsumgebungen den SSH-Zugriff blockieren, Debug-Endpunkte deaktivieren und Änderungsanforderungen mit organisatorischen Vorankündigungsanforderungen außer bei Notfällen erforderlich sind.                                                   |   2   |  D/V  |
| 4.8.4 | Stellen Sie sicher, dass Änderungen an der Infrastruktur als Code eine Peer-Review mit automatisierten Tests und Sicherheitsüberprüfungen erfordern, bevor sie in den Main-Branch zusammengeführt werden.                                                                  |   2   |  D/V  |
| 4.8.5 | Überprüfen Sie, dass Nicht-Produktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert sind, synthetische Datengenerierung oder vollständige Datenmaskierung mit Entfernung von personenbezogenen Identifikationsmerkmalen (PII) verifiziert wurde. |   2   |  D/V  |
| 4.8.6 | Stellen Sie sicher, dass Beförderungstore automatisierte Sicherheitstests (SAST, DAST, Container-Scanning) enthalten, bei denen keine CRITICAL-Funde für die Genehmigung erforderlich sind.                                                                                |   2   |  D/V  |

---

## C4.9 Infrastruktur-Backup & Wiederherstellung

Sichern Sie die Infrastrukturresilienz durch automatisierte Backups, getestete Wiederherstellungsverfahren und Katastrophenwiederherstellungsfähigkeiten.

|   #   | Beschreibung                                                                                                                                                                                                                   | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.9.1 | Überprüfen Sie, ob Infrastrukturkonfigurationen gemäß den organisatorischen Sicherungsplänen in geografisch getrennte Regionen gesichert werden, unter Umsetzung der 3-2-1-Sicherungsstrategie.                                |   1   |  D/V  |
| 4.9.2 | Verifizieren Sie, dass Backup-Systeme in isolierten Netzwerken mit separaten Zugangsdaten und luftgetrenntem Speicher zum Schutz vor Ransomware betrieben werden.                                                              |   2   |  D/V  |
| 4.9.3 | Überprüfen Sie, dass Wiederherstellungsverfahren gemäß den organisatorischen Zeitplänen mit RTO- und RPO-Zielen, die den organisatorischen Anforderungen entsprechen, durch automatisierte Tests geprüft und validiert werden. |   2   |   V   |
| 4.9.4 | Stellen Sie sicher, dass die Notfallwiederherstellung AI-spezifische Runbooks mit Wiederherstellung der Modellgewichte, Wiederaufbau des GPU-Clusters und Abbildung der Serviceabhängigkeiten umfasst.                         |   3   |   V   |

---

## C4.10 Infrastruktur-Compliance & Governance

Erhalten Sie die Einhaltung von Vorschriften durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollen.

|   #    | Beschreibung                                                                                                                                                                                                                | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.10.1 | Stellen Sie sicher, dass die Einhaltung der Infrastruktur gemäß den organisatorischen Zeitplänen anhand von SOC 2-, ISO 27001- oder FedRAMP-Kontrollen mit automatisierter Erfassung von Nachweisen bewertet wird.          |   2   |  D/V  |
| 4.10.2 | Verifizieren Sie, dass die Infrastrukturdokumentation Netzwerkdiagramme, Datenflusskarten und Bedrohungsmodelle enthält, die entsprechend den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden. |   2   |   V   |
| 4.10.3 | Stellen Sie sicher, dass Infrastrukturänderungen einer automatisierten Compliance-Auswirkungsbewertung mit regulatorischen Genehmigungsabläufen für risikoreiche Änderungen unterzogen werden.                              |   3   |  D/V  |

---

## C4.11 KI-Hardware-Sicherheit

Sichern Sie AI-spezifische Hardwarekomponenten einschließlich GPUs, TPUs und spezialisierter AI-Beschleuniger.

|   #    | Beschreibung                                                                                                                                                                                                                             | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.11.1 | Stellen Sie sicher, dass die Firmware des KI-Beschleunigers (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen verifiziert wird und gemäß den zeitlichen Vorgaben des organisatorischen Patch-Managements aktualisiert wird.       |   2   |  D/V  |
| 4.11.2 | Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestierung mittels TPM 2.0, Intel TXT oder AMD SVM überprüft wird.                                                     |   2   |  D/V  |
| 4.11.3 | Überprüfen Sie, dass der GPU-Speicher zwischen den Workloads mithilfe von SR-IOV, MIG (Multi-Instance GPU) oder einer gleichwertigen Hardwarepartitionierung isoliert ist, wobei eine Speicherbereinigung zwischen den Aufgaben erfolgt. |   2   |  D/V  |
| 4.11.4 | Überprüfen Sie, ob die Lieferkette der KI-Hardware eine Herkunftsverifizierung mit Herstellerzertifikaten und eine Validierung der manipulationssicheren Verpackung umfasst.                                                             |   3   |   V   |
| 4.11.5 | Stellen Sie sicher, dass Hardware-Sicherheitsmodule (HSMs) die KI-Modellgewichte und kryptografischen Schlüssel mit FIPS 140-2 Level 3 oder Common Criteria EAL4+ Zertifizierung schützen.                                               |   3   |  D/V  |

---

## C4.12 Edge- und verteilte KI-Infrastruktur

Sichere verteilte KI-Bereitstellungen einschließlich Edge-Computing, föderiertem Lernen und Multi-Site-Architekturen.

|   #    | Beschreibung                                                                                                                                                                                                                                          | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.12.1 | Stellen Sie sicher, dass Edge-AI-Geräte sich gegenüber der zentralen Infrastruktur mithilfe von mutual TLS authentifizieren, wobei die Gerätezertifikate gemäß der organisatorischen Zertifikatsverwaltungsrichtlinie regelmäßig ausgetauscht werden. |   2   |  D/V  |
| 4.12.2 | Stellen Sie sicher, dass Edge-Geräte Secure Boot mit verifizierten Signaturen und Rollback-Schutz implementieren, um Firmware-Downgrade-Angriffe zu verhindern.                                                                                       |   2   |  D/V  |
| 4.12.3 | Überprüfen Sie, ob die verteilte KI-Koordination byzantinisch fehlertolerante Konsensalgorithmen mit Teilnehmervalidierung und Erkennung bösartiger Knoten verwendet.                                                                                 |   3   |  D/V  |
| 4.12.4 | Überprüfen Sie, dass die Kommunikation zwischen Edge und Cloud Bandbreitenbegrenzung, Datenkompression und Offline-Betriebsfunktionen mit sicherer lokaler Speicherung umfasst.                                                                       |   3   |  D/V  |

---

## C4.13 Mehrfach-Cloud- und hybride Infrastruktur-Sicherheit

Sichern Sie KI-Arbeitslasten über mehrere Cloud-Anbieter hinweg sowie bei hybriden Cloud- und On-Premises-Bereitstellungen.

|   #    | Beschreibung                                                                                                                                                                                                               | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.13.1 | Verifizieren Sie, dass Multi-Cloud-KI-Bereitstellungen cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralem Richtlinienmanagement über die Anbieter hinweg verwenden.                                         |   2   |  D/V  |
| 4.13.2 | Überprüfen Sie, dass der plattformübergreifende Datentransfer eine Ende-zu-Ende-Verschlüsselung mit vom Kunden verwalteten Schlüsseln verwendet und dass Datenresidenzkontrollen je nach Rechtsgebiet durchgesetzt werden. |   2   |  D/V  |
| 4.13.3 | Überprüfen Sie, dass hybride Cloud-KI-Workloads konsistente Sicherheitsrichtlinien sowohl in lokalen als auch in Cloud-Umgebungen mit einheitlicher Überwachung und Alarmierung implementieren.                            |   2   |  D/V  |
| 4.13.4 | Überprüfen Sie, dass die Verhinderung von Anbieterbindung in der Cloud tragbare Infrastruktur-als-Code, standardisierte APIs und Datenexportfunktionen mit Formatkonvertierungswerkzeugen umfasst.                         |   3   |   V   |
| 4.13.5 | Stellen Sie sicher, dass die Multi-Cloud-Kostenoptimierung Sicherheitskontrollen umfasst, die sowohl die Ausweitung von Ressourcen als auch unautorisierte Gebühren für Datenübertragungen zwischen Clouds verhindern.     |   3   |   V   |

---

## C4.14 Infrastruktur-Automatisierung & GitOps-Sicherheit

Sichern Sie Infrastrukturautomatisierungspipelines und GitOps-Workflows für das Management von KI-Infrastrukturen.

|   #    | Beschreibung                                                                                                                                                                                                                                           | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.14.1 | Überprüfen Sie, dass GitOps-Repositorys signierte Commits mit GPG-Schlüsseln erfordern und Branch-Schutzregeln vorhanden sind, die direkte Pushes zu den Haupt-Branches verhindern.                                                                    |   2   |  D/V  |
| 4.14.2 | Stellen Sie sicher, dass die Infrastrukturautomatisierung eine Drift-Erkennung mit automatischer Fehlerbehebung und Rückrollfunktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen für unautorisierte Änderungen ausgelöst werden. |   2   |  D/V  |
| 4.14.3 | Stellen Sie sicher, dass die automatisierte Infrastrukturbereitstellung eine Sicherheitsrichtlinienvalidierung beinhaltet, die bei nicht konformen Konfigurationen den Einsatz blockiert.                                                              |   2   |  D/V  |
| 4.14.4 | Überprüfen Sie, ob Geheimnisse der Infrastrukturautomatisierung durch externe Secret-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.                                                                  |   2   |  D/V  |
| 4.14.5 | Stellen Sie sicher, dass die selbstheilende Infrastruktur die Korrelation von Sicherheitsereignissen mit automatisierter Vorfallreaktion und Workflows zur Benachrichtigung der Stakeholder umfasst.                                                   |   3   |   V   |

---

## C4.15 Quantenresistente Infrastruktursicherheit

Bereiten Sie die KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor mittels postquantischer Kryptographie und quantensicherer Protokolle.

|   #    | Beschreibung                                                                                                                                                                                                   | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Überprüfen Sie, ob die KI-Infrastruktur NIST-zugelassene postquantum-kryptographische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für Schlüsselaustausch und digitale Signaturen implementiert. |   3   |  D/V  |
| 4.15.2 | Stellen Sie sicher, dass Quantenschlüsselverteilungssysteme (QKD) für hochsichere KI-Kommunikation mit quantensicheren Schlüsselverwaltungsprotokollen implementiert sind.                                     |   3   |  D/V  |
| 4.15.3 | Stellen Sie sicher, dass kryptografische Agilitätsframeworks eine schnelle Migration zu neuen postquantenalgorithmen mit automatischer Zertifikats- und Schlüsselrotation ermöglichen.                         |   3   |  D/V  |
| 4.15.4 | Überprüfen Sie, ob die Quanten-Bedrohungsmodellierung die Anfälligkeit der KI-Infrastruktur für Quantenangriffe bewertet, mit dokumentierten Migrationszeitplänen und Risikobewertungen.                       |   3   |   V   |
| 4.15.5 | Überprüfen Sie, dass hybride klassische-quantum kryptografische Systeme während der Quantenübergangsperiode mit Leistungsüberwachung eine Tiefenverteidigung bieten.                                           |   3   |  D/V  |

---

## C4.16 Vertrauliches Rechnen & Sichere Enklaven

Schützen Sie KI-Arbeitslasten und Modellgewichte mithilfe von hardwarebasierten vertrauenswürdigen Ausführungsumgebungen und Technologien für vertrauliches Rechnen.

|   #    | Beschreibung                                                                                                                                                                                   | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.16.1 | Überprüfen Sie, dass sensible KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsprüfung ausgeführt werden.             |   3   |  D/V  |
| 4.16.2 | Überprüfen Sie, ob vertrauliche Container (Kata Containers, gVisor mit Confidential Computing) KI-Arbeitslasten mit hardware-gestützter Speicher-Verschlüsselung isolieren.                    |   3   |  D/V  |
| 4.16.3 | Stellen Sie sicher, dass die Remote-Attestation die Integrität der Enklave überprüft, bevor KI-Modelle mit kryptografischem Nachweis der Authentizität der Ausführungsumgebung geladen werden. |   3   |  D/V  |
| 4.16.4 | Überprüfen Sie, dass vertrauliche KI-Inferenzdienste Modellextraktion durch verschlüsselte Berechnung mit versiegelten Modellgewichten und geschützter Ausführung verhindern.                  |   3   |  D/V  |
| 4.16.5 | Überprüfen Sie, dass die Orchestrierung der Trusted Execution Environment den Lebenszyklus der sicheren Enklave mit Fernattestierung und verschlüsselten Kommunikationskanälen verwaltet.      |   3   |  D/V  |
| 4.16.6 | Überprüfen Sie, dass Secure Multi-Party Computation (SMPC) kollaboratives KI-Training ermöglicht, ohne individuelle Datensätze oder Modellparameter offenzulegen.                              |   3   |  D/V  |

---

## C4.17 Zero-Knowledge-Infrastruktur

Implementieren Sie Zero-Knowledge-Beweissysteme für datenschutzfreundliche KI-Verifikation und Authentifizierung, ohne sensible Informationen preiszugeben.

|   #    | Beschreibung                                                                                                                                                                                       | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.17.1 | Überprüfen Sie, dass Zero-Knowledge-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität von KI-Modellen und die Herkunft des Trainings bestätigen, ohne Modellgewichte oder Trainingsdaten offenzulegen. |   3   |  D/V  |
| 4.17.2 | Überprüfen Sie, dass ZK-basierte Authentifizierungssysteme eine datenschutzfreundliche Benutzerüberprüfung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen preiszugeben.         |   3   |  D/V  |
| 4.17.3 | Überprüfen Sie, dass Private Set Intersection (PSI)-Protokolle eine sichere Datenabstimmung für föderiertes KI ermöglichen, ohne einzelne Datensätze offenzulegen.                                 |   3   |  D/V  |
| 4.17.4 | Überprüfen Sie, dass Zero-Knowledge-Maschinenlern (ZKML)-Systeme überprüfbare KI-Schlüsse mit kryptografischem Nachweis korrekter Berechnungen ermöglichen.                                        |   3   |  D/V  |
| 4.17.5 | Überprüfen Sie, dass ZK-Rollups skalierbare, datenschutzwahrende KI-Transaktionsverarbeitung mit Batch-Verifikation und reduziertem Rechenaufwand bieten.                                          |   3   |  D/V  |

---

## C4.18 Verhinderung von Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor Timing-, Energie-, elektromagnetischen und cache-basierten Side-Channel-Angriffen, die sensible Informationen preisgeben könnten.

|   #    | Beschreibung                                                                                                                                                                             | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.18.1 | Überprüfen Sie, ob die AI-Inferenzzeit mit Hilfe von Algorithmen konstanter Zeit und Padding normalisiert wird, um Timing-basierte Modell-Extraktionsangriffe zu verhindern.             |   3   |  D/V  |
| 4.18.2 | Überprüfen Sie, dass der Schutz vor Leistungsanalyse Rauschinjektion, Stromlinienfilterung und zufällige Ausführungsmuster für KI-Hardware umfasst.                                      |   3   |  D/V  |
| 4.18.3 | Überprüfen Sie, ob die auf dem Cache basierende Seitenkanal-Minderung Cache-Partitionierung, Randomisierung und Flush-Befehle verwendet, um Informationslecks zu verhindern.             |   3   |  D/V  |
| 4.18.4 | Stellen Sie sicher, dass der Schutz vor elektromagnetischer Abstrahlung Abschirmung, Signalfilterung und randomisierte Verarbeitung umfasst, um TEMPEST-ähnliche Angriffe zu verhindern. |   3   |  D/V  |
| 4.18.5 | Überprüfen Sie, ob mikroarchitekturelle Seitenkanalabwehrmaßnahmen spekulative Ausführungssteuerungen und Verschleierung von Speicherzugriffsmustern umfassen.                           |   3   |  D/V  |

---

## C4.19 Neuromorphe & Spezialisierte KI-Hardware-Sicherheit

Sichern Sie aufkommende KI-Hardwarearchitekturen, einschließlich neuromorpher Chips, FPGAs, kundenspezifischer ASICs und optischer Rechensysteme.

|   #    | Beschreibung                                                                                                                                                                                    | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.19.1 | Überprüfen Sie, ob die Sicherheit neuromorpher Chips Spike-Muster-Verschlüsselung, Schutz der synaptischen Gewichte und hardwarebasierte Validierung der Lernregel umfasst.                     |   3   |  D/V  |
| 4.19.2 | Überprüfen Sie, ob FPGA-basierte KI-Beschleuniger Bitstream-Verschlüsselung, Manipulationsschutzmechanismen und sicheres Konfigurationsladen mit authentifizierten Updates implementieren.      |   3   |  D/V  |
| 4.19.3 | Stellen Sie sicher, dass die kundenspezifische ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, eine Hardware-Root-of-Trust und sichere Schlüsselspeicherung mit Manipulationserkennung umfasst. |   3   |  D/V  |
| 4.19.4 | Verifizieren Sie, dass optische Rechensysteme quantensichere optische Verschlüsselung, sichere photonische Schaltung und geschützte optische Signalverarbeitung implementieren.                 |   3   |  D/V  |
| 4.19.5 | Überprüfen Sie, dass hybride analog-digitale KI-Chips sichere analoge Berechnungen, geschützte Gewichtsspeicherung und authentifizierte Analog-Digital-Wandlung enthalten.                      |   3   |  D/V  |

---

## C4.20 Datenschutzwahrende Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzbewahrende Berechnungen, um sensible Daten während der KI-Verarbeitung und -Analyse zu schützen.

|   #    | Beschreibung                                                                                                                                                                                                                             | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.20.1 | Überprüfen Sie, ob die homomorphe Verschlüsselungsinfrastruktur verschlüsselte Berechnungen bei sensiblen KI-Workloads mit kryptographischer Integritätsprüfung und Leistungsüberwachung ermöglicht.                                     |   3   |  D/V  |
| 4.20.2 | Verifizieren Sie, dass Private Information Retrieval (PIR)-Systeme Datenbankabfragen ermöglichen, ohne Abfragemuster offenzulegen, durch kryptographischen Schutz der Zugriffs Muster.                                                   |   3   |  D/V  |
| 4.20.3 | Überprüfen Sie, dass sichere Multi-Party-Computing-Protokolle eine datenschutzfreundliche KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenberechnungen offenzulegen.                                                        |   3   |  D/V  |
| 4.20.4 | Stellen Sie sicher, dass die datenschutzfreundliche Schlüsselverwaltung die verteilte Schlüsselerzeugung, Schwellenwert-Kryptographie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.                               |   3   |  D/V  |
| 4.20.5 | Stellen Sie sicher, dass die leistungsfähige Verarbeitung mit Datenschutz durch Batch-Verarbeitung, Zwischenspeicherung und Hardwarebeschleunigung optimiert wird, während die kryptografischen Sicherheitsgarantien beibehalten werden. |   3   |  D/V  |

---

## C4.15 Agent Framework Cloud-Integrationssicherheit & Hybride Bereitstellung

Sicherheitskontrollen für cloud-integrierte Agentenframeworks mit hybriden On-Premises-/Cloud-Architekturen.

|   #    | Beschreibung                                                                                                                                           | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.15.1 | Überprüfen Sie, ob die Cloud-Speicherintegration End-to-End-Verschlüsselung mit agentengesteuertem Schlüsselmanagement verwendet.                      |   1   |  D/V  |
| 4.15.2 | Stellen Sie sicher, dass die Sicherheitsgrenzen der Hybridbereitstellung klar definiert sind und verschlüsselte Kommunikationskanäle verwendet werden. |   2   |  D/V  |
| 4.15.3 | Überprüfen Sie, ob der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung umfasst.                      |   2   |  D/V  |
| 4.15.4 | Stellen Sie sicher, dass Anforderungen an den Datenaufenthaltsort durch kryptografische Bestätigung der Speicherorte durchgesetzt werden.              |   3   |  D/V  |
| 4.15.5 | Verifizieren Sie, dass Sicherheitsbewertungen von Cloud-Anbietern agentspezifische Bedrohungsmodellierung und Risikoanalysen umfassen.                 |   3   |  D/V  |

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

