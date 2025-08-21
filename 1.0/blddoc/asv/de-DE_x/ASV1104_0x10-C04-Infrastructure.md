# C4 Infrastruktur, Konfiguration und Bereitstellungssicherheit

## Steuerungsziel

Die KI-Infrastruktur muss durch sichere Konfiguration, Laufzeitisolation, vertrauenswürdige Bereitstellungspipelines und umfassende Überwachung gegen Privilegieneskalation, Manipulation der Lieferkette und laterale Bewegungen gehärtet werden. Nur autorisierte, validierte Infrastrukturkomponenten und -konfigurationen gelangen durch kontrollierte Prozesse, die Sicherheit, Integrität und Prüfbarkeit gewährleisten, in die Produktion.

Kernziel der Sicherheit: Nur kryptografisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen durch automatisierte Validierungspipelines, die Sicherheitsrichtlinien durchsetzen und unveränderliche Audit-Trails aufrechterhalten, in die Produktion.

---

## C4.1 Laufzeitumgebungs-Isolierung

Verhindern Sie Container-Ausbrüche und Privilegienerweiterungen durch Kernel-Ebenen-Isolationsprimitive und obligatorische Zugriffskontrollen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                 | Ebene | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.1.1 | Stellen Sie sicher, dass alle KI-Container ALLE Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und ausdrücklich in den Sicherheitsgrundlagen dokumentierten erforderlichen Fähigkeiten entfernen.                                                                            |   1   |  D/V  |
| 4.1.2 | Überprüfen Sie, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denen in vordefinierten Zulassungslisten, wobei Verstöße zur Beendigung des Containers und zur Generierung von Sicherheitswarnungen führen.                                                        |   1   |  D/V  |
| 4.1.3 | Stellen Sie sicher, dass KI-Arbeitslasten mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei noexec-Mount-Optionen durchgesetzt sind.                                                 |   2   |  D/V  |
| 4.1.4 | Verifizieren Sie, dass die auf eBPF basierende Laufzeitüberwachung (Falco, Tetragon oder ein gleichwertiges System) Versuche zur Privilegienerweiterung erkennt und die verantwortlichen Prozesse automatisch innerhalb der organisatorischen Reaktionszeitvorgaben beendet. |   2   |  D/V  |
| 4.1.5 | Stellen Sie sicher, dass hochriskante KI-Arbeitslasten in hardware-isolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestationsüberprüfung ausgeführt werden.                                                                               |   3   |  D/V  |

---

## C4.2 Sichere Build- und Deployment-Pipelines

Gewährleisten Sie kryptografische Integrität und Sicherheit der Lieferkette durch reproduzierbare Builds und signierte Artefakte.

|   #   | Beschreibung                                                                                                                                                                                                                           | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.2.1 | Stellen Sie sicher, dass Infrastructure-as-Code bei jedem Commit mit Tools (tfsec, Checkov oder Terrascan) gescannt wird und das Zusammenführen bei CRITICAL- oder HIGH-Severity-Funden blockiert wird.                                |   1   |  D/V  |
| 4.2.2 | Stellen Sie sicher, dass Container-Builds mit identischen SHA256-Hashwerten über mehrere Builds hinweg reproduzierbar sind, und erstellen Sie SLSA Level 3 Herkunftszertifikate, die mit Sigstore signiert sind.                       |   1   |  D/V  |
| 4.2.3 | Überprüfen Sie, dass Container-Images CycloneDX- oder SPDX-SBOMs eingebettet haben und vor dem Push in das Registry mit Cosign signiert sind, wobei unsignierte Images bei der Bereitstellung abgelehnt werden.                        |   2   |  D/V  |
| 4.2.4 | Stellen Sie sicher, dass CI/CD-Pipelines OIDC-Token von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity verwenden, deren Laufzeiten die Grenzen der organisatorischen Sicherheitsrichtlinien nicht überschreiten.          |   2   |  D/V  |
| 4.2.5 | Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Provenance während des Bereitstellungsprozesses vor der Ausführung des Containers validiert werden und dass Verifizierungsfehler dazu führen, dass die Bereitstellung fehlschlägt. |   2   |  D/V  |
| 4.2.6 | Stellen Sie sicher, dass Build-Umgebungen in ephemeren Containern oder VMs ohne persistenten Speicher und mit Netzwerkisolierung von Produktions-VPCs ausgeführt werden.                                                               |   2   |  D/V  |

---

## C4.3 Netzwerksicherheit & Zugriffskontrolle

Implementieren Sie Zero-Trust-Netzwerke mit Standard-Ablehnungsrichtlinien und verschlüsselter Kommunikation.

|   #   | Beschreibung                                                                                                                                                                                                                          | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.3.1 | Stellen Sie sicher, dass Kubernetes NetworkPolicies oder ein Äquivalent eine Standardverweigerung für Ingress/Egress mit expliziten Erlaubnisregeln für die erforderlichen Ports (443, 8080, etc.) implementieren.                    |   1   |  D/V  |
| 4.3.2 | Stellen Sie sicher, dass SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatbasierte Authentifizierung erfordern.                                                      |   1   |  D/V  |
| 4.3.3 | Stellen Sie sicher, dass ausgehender Datenverkehr über HTTP/HTTPS-Proxys (Squid, Istio oder Cloud-NAT-Gateways) mit Domain-Positivlisten gefiltert wird und blockierte Anfragen protokolliert werden.                                 |   2   |  D/V  |
| 4.3.4 | Stellen Sie sicher, dass die Kommunikation zwischen Diensten Mutual TLS verwendet, wobei die Zertifikate gemäß der Organisationsrichtlinie rotiert werden und die Zertifikatsvalidierung durchgesetzt wird (keine Skip-Verify-Flags). |   2   |  D/V  |
| 4.3.5 | Stellen Sie sicher, dass die KI-Infrastruktur in dedizierten VPCs/VNets ohne direkten Internetzugang betrieben wird und ausschließlich über NAT-Gateways oder Bastion-Hosts kommuniziert.                                             |   2   |  D/V  |

---

## C4.4 Geheimnisse & Verwaltung kryptographischer Schlüssel

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatische Rotation mit Zero-Trust-Zugriff.

|   #   | Beschreibung                                                                                                                                                                                                                    | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.4.1 | Überprüfen Sie, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager mit Verschlüsselung im Ruhezustand unter Verwendung von AES-256 gespeichert werden.                        |   1   |  D/V  |
| 4.4.2 | Stellen Sie sicher, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) erzeugt werden und eine Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie erfolgt.    |   1   |  D/V  |
| 4.4.3 | Überprüfen Sie, dass die Rotation von Geheimnissen automatisiert ist mit einem Zero-Downtime-Deployment und einer sofortigen Rotation, die durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.                       |   2   |  D/V  |
| 4.4.4 | Stellen Sie sicher, dass Container-Images mit Werkzeugen (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds blockieren, die API-Schlüssel, Passwörter oder Zertifikate enthalten.                           |   2   |  D/V  |
| 4.4.5 | Überprüfen Sie, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Audit-Protokolle mit Benutzeridentitäten und Zeitstempeln dokumentiert wird.       |   2   |  D/V  |
| 4.4.6 | Stellen Sie sicher, dass Geheimnisse über Kubernetes-Geheimnisse, eingehängte Volumes oder Init-Container injiziert werden, und gewährleisten Sie, dass Geheimnisse niemals in Umgebungsvariablen oder Images eingebettet sind. |   2   |  D/V  |

---

## C4.5 KI-Arbeitslast-Sandboxing und Validierung

Isoliere nicht vertrauenswürdige KI-Modelle in sicheren Sandboxes mit umfassender Verhaltensanalyse.

|   #   | Beschreibung                                                                                                                                                                                                                   | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.5.1 | Stellen Sie sicher, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit den Flags --security-opt=no-new-privileges und --read-only ausgeführt werden.                            |   1   |  D/V  |
| 4.5.2 | Überprüfen Sie, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost mit allen externen Anfragen, die durch iptables-Regeln blockiert werden.                                |   1   |  D/V  |
| 4.5.3 | Stellen Sie sicher, dass die Validierung des KI-Modells automatisierte Red-Team-Tests mit organisatorisch definiertem Testumfang und Verhaltensanalyse zur Rückdohrerkennung umfasst.                                          |   2   |  D/V  |
| 4.5.4 | Stellen Sie sicher, dass vor der Freigabe eines KI-Modells für die Produktion die Sandbox-Ergebnisse kryptografisch von autorisiertem Sicherheitspersonal signiert und in unveränderlichen Prüfprotokollen gespeichert werden. |   2   |  D/V  |
| 4.5.5 | Stellen Sie sicher, dass Sandbox-Umgebungen zwischen den Bewertungen zerstört und aus Golden Images neu erstellt werden, wobei eine vollständige Bereinigung des Dateisystems und des Speichers erfolgt.                       |   2   |  D/V  |

---

## C4.6 Überwachung der Infrastruktursicherheit

Infrastruktur kontinuierlich mit automatischer Behebung und Echtzeit-Benachrichtigungen scannen und überwachen.

|   #   | Beschreibung                                                                                                                                                                                                                                          | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.6.1 | Stellen Sie sicher, dass Container-Images gemäß den organisatorischen Zeitplänen gescannt werden, wobei CRITICAL-Schwachstellen die Bereitstellung basierend auf den organisatorischen Risikoschwellen blockieren.                                    |   1   |  D/V  |
| 4.6.2 | Überprüfen Sie, ob die Infrastruktur die CIS-Benchmarks oder NIST 800-53-Kontrollen mit organisatorisch definierten Compliance-Schwellenwerten erfüllt und automatisierte Behebungen für fehlerhafte Prüfungen durchführt.                            |   1   |  D/V  |
| 4.6.3 | Überprüfen Sie, dass HIGH-Schweregrad-Schwachstellen gemäß den Zeitplänen des organisatorischen Risikomanagements gepatcht werden, mit Notfallverfahren für aktiv ausgenutzte CVEs.                                                                   |   2   |  D/V  |
| 4.6.4 | Überprüfen Sie, ob Sicherheitswarnungen mithilfe der Formate CEF oder STIX/TAXII mit automatischer Anreicherung in SIEM-Plattformen (Splunk, Elastic oder Sentinel) integriert werden.                                                                |   2   |   V   |
| 4.6.5 | Überprüfen Sie, dass Infrastrukturskennzahlen an Überwachungssysteme (Prometheus, DataDog) mit SLA-Dashboards und Managementberichten exportiert werden.                                                                                              |   3   |   V   |
| 4.6.6 | Überprüfen Sie, dass Konfigurationsabweichungen gemäß den organisatorischen Überwachungsanforderungen mithilfe von Tools (Chef InSpec, AWS Config) erkannt werden, und führen Sie bei unautorisierten Änderungen eine automatische Rücksetzung durch. |   2   |  D/V  |

---

## C4.7 KI-Infrastruktur-Ressourcenmanagement

Verhindern Sie Ressourcenerschöpfungsangriffe und gewährleisten Sie eine faire Ressourcenverteilung durch Kontingente und Überwachung.

|   #   | Beschreibung                                                                                                                                                                                                                                             | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.7.1 | Stellen Sie sicher, dass die GPU/TPU-Auslastung überwacht wird, wobei bei organisatorisch festgelegten Schwellenwerten Alarme ausgelöst und basierend auf Kapazitätsmanagementrichtlinien automatische Skalierung oder Lastenausgleich aktiviert werden. |   1   |  D/V  |
| 4.7.2 | Überprüfen Sie, ob KI-Arbeitslastmetriken (Inference-Latenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Monitoring-Anforderungen erfasst und mit der Auslastung der Infrastruktur korreliert werden.                                            |   1   |  D/V  |
| 4.7.3 | Stellen Sie sicher, dass Kubernetes ResourceQuotas oder entsprechende Mechanismen einzelne Workloads gemäß den Ressourcenallokationsrichtlinien der Organisation mit durchgesetzten harten Grenzwerten begrenzen.                                        |   2   |  D/V  |
| 4.7.4 | Überprüfen Sie, dass die Kostenüberwachung die Ausgaben pro Arbeitslast/Mandant mit Alarmen basierend auf den organisatorischen Budgetgrenzen und automatisierten Kontrollen bei Budgetüberschreitungen verfolgt.                                        |   2   |   V   |
| 4.7.5 | Stellen Sie sicher, dass die Kapazitätsplanung historische Daten mit organisatorisch definierten Prognosezeiträumen verwendet und eine automatisierte Ressourcenbereitstellung basierend auf Nachfrageverläufen erfolgt.                                 |   3   |   V   |
| 4.7.6 | Überprüfen Sie, ob Ressourcenerschöpfung die Circuit Breaker gemäß den organisatorischen Reaktionsanforderungen auslöst, einschließlich der Drosselung der Rate basierend auf Kapazitätsrichtlinien und der Arbeitslastisolierung.                       |   2   |  D/V  |

---

## C4.8 Trennung der Umgebungen und Steuerung der Promotion

Durchsetzung strenger Umweltgrenzen mit automatisierten Fördertoren und Sicherheitsvalidierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                             | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.8.1 | Verifizieren Sie, dass Entwicklungs-, Test- und Produktionsumgebungen in separaten VPCs/VNets laufen, ohne gemeinsame IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen.                                                                                          |   1   |  D/V  |
| 4.8.2 | Verifizieren Sie, dass die Umgebungspromotion die Genehmigung durch organisatorisch definierte autorisierte Personen mit kryptografischen Signaturen und unveränderlichen Prüfpfaden erfordert.                                                                          |   1   |  D/V  |
| 4.8.3 | Überprüfen Sie, dass Produktionsumgebungen den SSH-Zugriff blockieren, Debug-Endpunkte deaktivieren und Änderungsanfragen mit organisatorischen Vorankündigungsanforderungen außer in Notfällen erfordern.                                                               |   2   |  D/V  |
| 4.8.4 | Stellen Sie sicher, dass Änderungen an der Infrastruktur als Code vor dem Zusammenführen in den Hauptzweig Peer-Review, automatisierte Tests und Sicherheitsscans erfordern.                                                                                             |   2   |  D/V  |
| 4.8.5 | Verifizieren Sie, dass Nicht-Produktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert werden, die Generierung synthetischer Daten erfolgt oder eine vollständige Datenmaskierung mit Entfernung personenbezogener Daten (PII) überprüft wurde. |   2   |  D/V  |
| 4.8.6 | Stellen Sie sicher, dass die Freigabetore automatisierte Sicherheitstests (SAST, DAST, Container-Scans) enthalten, wobei für die Genehmigung keine CRITICAL-Befunde zulässig sind.                                                                                       |   2   |  D/V  |

---

## C4.9 Infrastruktur-Backup & Wiederherstellung

Sichern Sie die Infrastrukturresilienz durch automatisierte Backups, getestete Wiederherstellungsverfahren und Fähigkeiten zur Katastrophenwiederherstellung.

|   #   | Beschreibung                                                                                                                                                                                                                     | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.9.1 | Überprüfen Sie, dass Infrastrukturkonfigurationen gemäß den organisatorischen Backup-Zeitplänen in geografisch getrennte Regionen gesichert werden, unter Anwendung der 3-2-1-Backup-Strategie.                                  |   1   |  D/V  |
| 4.9.2 | Stellen Sie sicher, dass Backup-Systeme in isolierten Netzwerken mit separaten Anmeldedaten und air-gapped Speicher zur Ransomware-Abwehr betrieben werden.                                                                      |   2   |  D/V  |
| 4.9.3 | Verifizieren Sie, dass Wiederherstellungsverfahren gemäß den organisatorischen Zeitplänen mit automatisierten Tests getestet und validiert werden, wobei die RTO- und RPO-Ziele den organisatorischen Anforderungen entsprechen. |   2   |   V   |
| 4.9.4 | Stellen Sie sicher, dass die Notfallwiederherstellung AI-spezifische Runbooks mit Modellgewichtswiederherstellung, GPU-Cluster-Neuaufbau und Dienstabhängigkeitskartierung umfasst.                                              |   3   |   V   |

---

## C4.10 Infrastruktur-Compliance & Governance

Gewährleisten Sie die Einhaltung von Vorschriften durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollen.

|   #    | Beschreibung                                                                                                                                                                                                         | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.10.1 | Stellen Sie sicher, dass die Einhaltung der Infrastruktur gemäß den organisatorischen Zeitplänen gegen SOC 2-, ISO 27001- oder FedRAMP-Kontrollen mit automatisierter Beweissammlung bewertet wird.                  |   2   |  D/V  |
| 4.10.2 | Verifizieren Sie, dass die Infrastrukturdokumentation Netzwerkdiagramme, Datenflusskarten und Bedrohungsmodelle enthält, die gemäß den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden. |   2   |   V   |
| 4.10.3 | Stellen Sie sicher, dass Infrastrukturänderungen einer automatisierten Compliance-Auswirkungsbewertung unterzogen werden, einschließlich regulatorischer Genehmigungsabläufe für risikoreiche Änderungen.            |   3   |  D/V  |

---

## C4.11 KI-Hardware-Sicherheit

Sichern Sie KI-spezifische Hardwarekomponenten einschließlich GPUs, TPUs und spezialisierter KI-Beschleuniger.

|   #    | Beschreibung                                                                                                                                                                                                               | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.11.1 | Stellen Sie sicher, dass die Firmware des KI-Beschleunigers (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen verifiziert wird und gemäß den Zeitplänen des organisatorischen Patch-Managements aktualisiert wird.  |   2   |  D/V  |
| 4.11.2 | Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestierung mittels TPM 2.0, Intel TXT oder AMD SVM überprüft wird.                                       |   2   |  D/V  |
| 4.11.3 | Überprüfen Sie, ob der GPU-Speicher zwischen Workloads mithilfe von SR-IOV, MIG (Multi-Instance GPU) oder einer gleichwertigen hardwarebasierten Partitionierung mit Speichersanierung zwischen den Aufgaben isoliert ist. |   2   |  D/V  |
| 4.11.4 | Stellen Sie sicher, dass die Lieferkette der KI-Hardware eine Herkunftsüberprüfung mit Herstellungszertifikaten und eine Validierung manipulationssicherer Verpackungen umfasst.                                           |   3   |   V   |
| 4.11.5 | Stellen Sie sicher, dass Hardware-Sicherheitsmodule (HSMs) die KI-Modellgewichte und kryptografischen Schlüssel mit einer FIPS 140-2 Level 3- oder Common Criteria EAL4+-Zertifizierung schützen.                          |   3   |  D/V  |

---

## C4.12 Edge- und verteilte KI-Infrastruktur

Sichere verteilte KI-Bereitstellungen einschließlich Edge-Computing, föderiertem Lernen und Multi-Site-Architekturen.

|   #    | Beschreibung                                                                                                                                                                                                                                    | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.12.1 | Stellen Sie sicher, dass Edge-AI-Geräte sich gegenüber der zentralen Infrastruktur mittels mutual TLS mit Gerätezertifikaten authentifizieren, die gemäß der organisatorischen Zertifikatsverwaltungsrichtlinie regelmäßig ausgetauscht werden. |   2   |  D/V  |
| 4.12.2 | Überprüfen Sie, dass Edge-Geräte Secure Boot mit verifizierten Signaturen und einer Rückrollschutzfunktion implementieren, um Firmware-Downgrade-Angriffe zu verhindern.                                                                        |   2   |  D/V  |
| 4.12.3 | Stellen Sie sicher, dass die verteilte KI-Koordination byzantinisch fehlertolerante Konsensalgorithmen mit Teilnehmervalidierung und Erkennung bösartiger Knoten verwendet.                                                                     |   3   |  D/V  |
| 4.12.4 | Stellen Sie sicher, dass die Kommunikation von Edge zu Cloud Bandbreiten-Drosselung, Datenkompression und Offline-Betriebsfähigkeit mit sicherer lokaler Speicherung umfasst.                                                                   |   3   |  D/V  |

---

## C4.13 Sicherheit von Multi-Cloud- und Hybrid-Infrastrukturen

Sichern Sie KI-Workloads über mehrere Cloud-Anbieter und hybride Cloud-On-Premises-Bereitstellungen hinweg.

|   #    | Beschreibung                                                                                                                                                                                                                                                 | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.13.1 | Stellen Sie sicher, dass Multi-Cloud-KI-Bereitstellungen cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralem Richtlinienmanagement über die Anbieter hinweg verwenden.                                                                         |   2   |  D/V  |
| 4.13.2 | Überprüfen Sie, dass der datenaustausch zwischen verschiedenen Cloud-Anbietern eine Ende-zu-Ende-Verschlüsselung mit kundenseitig verwalteten Schlüsseln verwendet und dass Datenresidenzkontrollen gemäß den jeweiligen Rechtsgebieten durchgesetzt werden. |   2   |  D/V  |
| 4.13.3 | Überprüfen Sie, ob hybride Cloud-KI-Workloads konsistente Sicherheitsrichtlinien sowohl in lokalen als auch in Cloud-Umgebungen mit einheitlichem Monitoring und Alerting implementieren.                                                                    |   2   |  D/V  |
| 4.13.4 | Überprüfen Sie, ob die Verhinderung von Cloud-Anbieterbindung portierbare Infrastructure-as-Code, standardisierte APIs und Datenexportmöglichkeiten mit Formatkonvertierungstools umfasst.                                                                   |   3   |   V   |
| 4.13.5 | Stellen Sie sicher, dass die Multi-Cloud-Kostenoptimierung Sicherheitskontrollen umfasst, die sowohl die Ausbreitung von Ressourcen verhindern als auch unautorisierte Gebühren für Datenübertragungen zwischen Clouds unterbinden.                          |   3   |   V   |

---

## C4.14 Infrastrukturautomatisierung & GitOps-Sicherheit

Sichere Automatisierungspipelines für Infrastruktur und GitOps-Workflows für das Management von KI-Infrastrukturen.

|   #    | Beschreibung                                                                                                                                                                                                                                          | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.14.1 | Überprüfen Sie, dass GitOps-Repositories signierte Commits mit GPG-Schlüsseln verlangen und Branch-Schutzregeln vorhanden sind, die direkte Pushes auf Haupt-Branches verhindern.                                                                     |   2   |  D/V  |
| 4.14.2 | Stellen Sie sicher, dass die Infrastrukturautomatisierung eine Drift-Erkennung mit automatischer Behebung und Rollback-Funktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen für nicht autorisierte Änderungen ausgelöst werden. |   2   |  D/V  |
| 4.14.3 | Stellen Sie sicher, dass die automatisierte Infrastruktur-Bereitstellung eine Validierung der Sicherheitspolitik umfasst und die Bereitstellung bei nicht konformen Konfigurationen blockiert wird.                                                   |   2   |  D/V  |
| 4.14.4 | Stellen Sie sicher, dass Infrastruktur-Automatisierungsgeheimnisse durch externe Geheimnis-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.                                                           |   2   |  D/V  |
| 4.14.5 | Stellen Sie sicher, dass die selbstheilende Infrastruktur eine Sicherheitsereigniskorrelation mit automatisierter Vorfallreaktion und Benachrichtigungsabläufen für Interessengruppen umfasst.                                                        |   3   |   V   |

---

## C4.15 Quantenresistente Infrastruktursicherheit

Bereiten Sie die KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor, indem Sie postquantengerechte Kryptographie und quantensichere Protokolle einsetzen.

|   #    | Beschreibung                                                                                                                                                                                                               | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Stellen Sie sicher, dass die KI-Infrastruktur NIST-zugelassene postquantische kryptografische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für den Schlüsselaustausch und digitale Signaturen implementiert. |   3   |  D/V  |
| 4.15.2 | Überprüfen Sie, dass Quantenschlüsselverteilungssysteme (QKD) für hochsichere KI-Kommunikationen mit quantensicheren Schlüsselverwaltungsprotokollen implementiert sind.                                                   |   3   |  D/V  |
| 4.15.3 | Überprüfen Sie, dass kryptografische Agilitätsrahmen eine schnelle Migration zu neuen postquantumalgorithmen mit automatischer Zertifikats- und Schlüsseldrehung ermöglichen.                                              |   3   |  D/V  |
| 4.15.4 | Überprüfen Sie, ob die Quantendrohungsmodellierung die Verwundbarkeit der KI-Infrastruktur gegenüber Quantenangriffen bewertet, einschließlich dokumentierter Migrationszeitpläne und Risikobewertungen.                   |   3   |   V   |
| 4.15.5 | Stellen Sie sicher, dass hybride klassische-quantum kryptografische Systeme während der Quantenübergangsphase mit Leistungsüberwachung eine Defense-in-Depth bieten.                                                       |   3   |  D/V  |

---

## C4.16 Vertrauliches Computing & Sichere Enklaven

Schützen Sie KI-Arbeitslasten und Modellgewichte mithilfe hardwarebasierter vertrauenswürdiger Ausführungsumgebungen und Technologien für vertrauliches Computing.

|   #    | Beschreibung                                                                                                                                                                                | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.16.1 | Stellen Sie sicher, dass sensible KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsüberprüfung ausgeführt werden.  |   3   |  D/V  |
| 4.16.2 | Überprüfen Sie, ob vertrauliche Container (Kata Containers, gVisor mit Confidential Computing) KI-Arbeitslasten mit hardwaregestützter Speicher­verschlüsselung isolieren.                  |   3   |  D/V  |
| 4.16.3 | Überprüfen Sie, dass die Remote-Attestierung die Integrität der Enklave validiert, bevor KI-Modelle mit kryptografischem Nachweis der Echtheit einer Ausführungsumgebung geladen werden.    |   3   |  D/V  |
| 4.16.4 | Verifizieren Sie, dass vertrauliche KI-Inferenzdienste die Modellauslesung durch verschlüsselte Berechnungen mit versiegelten Modellgewichten und geschützter Ausführung verhindern.        |   3   |  D/V  |
| 4.16.5 | Verifizieren Sie, dass die Orchestrierung der Trusted Execution Environment den Lebenszyklus sicherer Enklaven mit Remote-Attestierung und verschlüsselten Kommunikationskanälen verwaltet. |   3   |  D/V  |
| 4.16.6 | Überprüfen Sie, dass Secure Multi-Party Computation (SMPC) kollaboratives AI-Training ermöglicht, ohne individuelle Datensätze oder Modellparameter offenzulegen.                           |   3   |  D/V  |

---

## C4.17 Zero-Knowledge Infrastruktur

Implementieren Sie Zero-Knowledge-Beweissysteme für datenschutzfreundliche KI-Verifikation und Authentifizierung, ohne sensible Informationen preiszugeben.

|   #    | Beschreibung                                                                                                                                                                                         | Ebene | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.17.1 | Überprüfen Sie, dass Zero-Knowledge-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität von KI-Modellen und die Herkunft des Trainings bestätigen, ohne Modellgewichte oder Trainingsdaten offenzulegen.   |   3   |  D/V  |
| 4.17.2 | Stellen Sie sicher, dass auf ZK basierende Authentifizierungssysteme eine datenschutzfreundliche Benutzerüberprüfung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen preiszugeben. |   3   |  D/V  |
| 4.17.3 | Überprüfen Sie, dass Private Set Intersection (PSI)-Protokolle eine sichere Datenabstimmung für föderierte KI ermöglichen, ohne einzelne Datensätze offenzulegen.                                    |   3   |  D/V  |
| 4.17.4 | Verifizieren Sie, dass Zero-Knowledge-Maschinelles Lernen (ZKML)-Systeme überprüfbare KI-Schlussfolgerungen mit kryptographischem Nachweis der korrekten Berechnung ermöglichen.                     |   3   |  D/V  |
| 4.17.5 | Überprüfen Sie, dass ZK-Rollups skalierbare, datenschutzwahrende KI-Transaktionsverarbeitung mit Stapelverifikation und reduziertem Rechenaufwand bieten.                                            |   3   |  D/V  |

---

## C4.18 Verhinderung von Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor Timing-, Leistungs-, elektromagnetischen und cache-basierten Side-Channel-Angriffen, die sensible Informationen preisgeben könnten.

|   #    | Beschreibung                                                                                                                                                                           | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.18.1 | Stellen Sie sicher, dass die AI-Inferenzzeiten mithilfe von Konstantzeit-Algorithmen und Padding normalisiert werden, um timingbasierte Modell-Extraktionsangriffe zu verhindern.      |   3   |  D/V  |
| 4.18.2 | Überprüfen Sie, ob der Schutz vor Leistungsanalyse Rauschinjektion, Filterung der Stromversorgung und zufällige Ausführungsmuster für KI-Hardware umfasst.                             |   3   |  D/V  |
| 4.18.3 | Überprüfen Sie, ob die cache-basierte Seitenkanalabwehr Cache-Partitionierung, Randomisierung und Flush-Anweisungen verwendet, um Informationslecks zu verhindern.                     |   3   |  D/V  |
| 4.18.4 | Stellen Sie sicher, dass der Schutz vor elektromagnetischer Abstrahlung Abschirmung, Signalfilterung und randomisierte Verarbeitung umfasst, um TEMPEST-artige Angriffe zu verhindern. |   3   |  D/V  |
| 4.18.5 | Überprüfen Sie, ob mikroraumarchitektonische Seitenkanalabwehrmaßnahmen spekulative Ausführungskontrollen und die Verschleierung von Speicherzugriffsmustern umfassen.                 |   3   |  D/V  |

---

## C4.19 Neuromorphe und spezialisierte KI-Hardware-Sicherheit

Sichern Sie neuartige KI-Hardwarearchitekturen, einschließlich neuromorpher Chips, FPGAs, maßgeschneiderter ASICs und optischer Rechensysteme.

|   #    | Beschreibung                                                                                                                                                                                     | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.19.1 | Überprüfen Sie, dass die Sicherheit neuromorpher Chips die Verschlüsselung von Spike-Mustern, den Schutz von synaptischen Gewichten und die hardwarebasierte Validierung von Lernregeln umfasst. |   3   |  D/V  |
| 4.19.2 | Stellen Sie sicher, dass FPGA-basierte KI-Beschleuniger Bitstream-Verschlüsselung, Anti-Manipulationsmechanismen und sicheres Konfigurationsladen mit authentifizierten Updates implementieren.  |   3   |  D/V  |
| 4.19.3 | Überprüfen Sie, dass die benutzerdefinierte ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, eine Hardware-Root of Trust und einen sicheren Schlüsselspeicher mit Manipulationsdetektion umfasst. |   3   |  D/V  |
| 4.19.4 | Überprüfen Sie, ob optische Rechensysteme quantensichere optische Verschlüsselung, sichere photonische Schaltung und geschützte optische Signalverarbeitung implementieren.                      |   3   |  D/V  |
| 4.19.5 | Überprüfen Sie, ob hybride analog-digital KI-Chips sichere analoge Berechnungen, geschützte Gewichtsspeicherung und authentifizierte Analog-Digital-Wandlung enthalten.                          |   3   |  D/V  |

---

## C4.20 Datenschutzwahrende Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzfreundliche Berechnungen, um sensible Daten während der KI-Verarbeitung und -Analyse zu schützen.

|   #    | Beschreibung                                                                                                                                                                                                                    | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.20.1 | Stellen Sie sicher, dass die homomorphe Verschlüsselungsinfrastruktur verschlüsselte Berechnungen bei sensiblen KI-Arbeitslasten mit kryptografischer Integritätsprüfung und Leistungsüberwachung ermöglicht.                   |   3   |  D/V  |
| 4.20.2 | Verifizieren Sie, dass Systeme zur privaten Informationsabfrage Datenbankabfragen ermöglichen, ohne Abfragemuster offenzulegen, und dabei kryptographischen Schutz der Zugriffsmuster gewährleisten.                            |   3   |  D/V  |
| 4.20.3 | Überprüfen Sie, dass sichere Mehrparteienrechnung-Protokolle eine datenschutzfreundliche KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenberechnungen offenzulegen.                                                |   3   |  D/V  |
| 4.20.4 | Stellen Sie sicher, dass die datenschutzschonende Schlüsselverwaltung verteilte Schlüsselerzeugung, Schwellenwertkryptografie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.                              |   3   |  D/V  |
| 4.20.5 | Stellen Sie sicher, dass die Leistung von datenschutzwahrendem Rechnen durch Batch-Verarbeitung, Caching und Hardwarebeschleunigung optimiert wird, während die kryptografischen Sicherheitsgarantien aufrechterhalten bleiben. |   3   |  D/V  |

---

## C4.15 Agent Framework Cloud-Integrationssicherheit & hybride Bereitstellung

Sicherheitskontrollen für cloud-integrierte Agentenframeworks mit hybriden On-Premises/Cloud-Architekturen.

|   #    | Beschreibung                                                                                                                                              | Ebene | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Stellen Sie sicher, dass die Integration von Cloud-Speicher End-to-End-Verschlüsselung mit agentengesteuerter Schlüsselverwaltung verwendet.              |   1   |  D/V  |
| 4.15.2 | Stellen Sie sicher, dass die Sicherheitsgrenzen der hybriden Bereitstellung klar definiert sind und verschlüsselte Kommunikationskanäle verwendet werden. |   2   |  D/V  |
| 4.15.3 | Überprüfen Sie, dass der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung beinhaltet.                    |   2   |  D/V  |
| 4.15.4 | Überprüfen Sie, ob die Anforderungen an den Datenstandort durch kryptografische Bestätigung der Speicherorte eingehalten werden.                          |   3   |  D/V  |
| 4.15.5 | Überprüfen Sie, ob Sicherheitsbewertungen des Cloud-Anbieters agentenspezifisches Bedrohungsmodellieren und Risikoanalyse enthalten.                      |   3   |  D/V  |

---

## Literaturverzeichnis

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

