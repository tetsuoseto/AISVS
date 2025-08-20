# C4-Infrastruktur, Konfigurations- und Bereitstellungssicherheit

## Kontrollziel

Die KI-Infrastruktur muss gegen Privilegienerweiterung, Manipulation der Lieferkette und laterale Bewegungen durch sichere Konfiguration, Laufzeitisolation, vertrauenswürdige Bereitstellungspipelines und umfassende Überwachung gehärtet werden. Nur autorisierte, validierte Infrastrukturkomponenten und -konfigurationen gelangen über kontrollierte Prozesse, die Sicherheit, Integrität und Prüfbarkeit gewährleisten, in die Produktion.

Kernziel der Sicherheit: Nur kryptografisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen durch automatisierte Validierungspipelines, die Sicherheitsrichtlinien durchsetzen und unveränderliche Prüfprotokolle führen, in die Produktion.

---

## C4.1 Laufzeitumgebungsisolierung

Verhindern Sie das Entkommen aus Containern und die Eskalation von Berechtigungen durch kernelbasierte Isolationsprimitiven und obligatorische Zugriffskontrollen.

|   #   | Beschreibung                                                                                                                                                                                                                                               | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.1.1 | Stellen Sie sicher, dass alle KI-Container ALLE Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und ausdrücklich in den Sicherheitsgrundlagen dokumentierten erforderlichen Fähigkeiten deaktivieren.                                                       |   1   |  D/V  |
| 4.1.2 | Überprüfen Sie, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denen in vordefinierten Erlaubnislisten, wobei Verstöße zum Beenden des Containers und zur Generierung von Sicherheitswarnungen führen.                                          |   1   |  D/V  |
| 4.1.3 | Verifizieren Sie, dass KI-Workloads mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei noexec-Mount-Optionen durchgesetzt sind.                                     |   2   |  D/V  |
| 4.1.4 | Verifizieren Sie, dass eine auf eBPF basierende Laufzeitüberwachung (Falco, Tetragon oder Äquivalentes) Versuche zur Privilegienerweiterung erkennt und störende Prozesse automatisch innerhalb der organisatorischen Reaktionszeit-Anforderungen beendet. |   2   |  D/V  |
| 4.1.5 | Verifizieren Sie, dass KI-Workloads mit hohem Risiko in hardware-isolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestierungsüberprüfung ausgeführt werden.                                                              |   3   |  D/V  |

---

## C4.2 Sichere Build- und Deployment-Pipelines

Sichern Sie die kryptografische Integrität und die Sicherheit der Lieferkette durch reproduzierbare Builds und signierte Artefakte.

|   #   | Beschreibung                                                                                                                                                                                                              | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.2.1 | Stellen Sie sicher, dass Infrastructure-as-Code bei jedem Commit mit Tools wie tfsec, Checkov oder Terrascan gescannt wird und dass Merges bei CRITICAL- oder HIGH-Schweregrad-Funden blockiert werden.                   |   1   |  D/V  |
| 4.2.2 | Stellen Sie sicher, dass Container-Builds reproduzierbar sind und bei Wiederholungen identische SHA256-Hashes erzeugen, und erstellen Sie SLSA Level 3 Herkunftsbestätigungen, die mit Sigstore signiert sind.            |   1   |  D/V  |
| 4.2.3 | Verifizieren Sie, dass Container-Images CycloneDX- oder SPDX-SBOMs einbetten und vor dem Push in das Registry mit Cosign signiert sind, wobei unsignierte Images bei der Bereitstellung abgelehnt werden.                 |   2   |  D/V  |
| 4.2.4 | Überprüfen Sie, dass CI/CD-Pipelines OIDC-Token von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity verwenden, deren Laufzeiten die Grenzen der organisatorischen Sicherheitsrichtlinien nicht überschreiten. |   2   |  D/V  |
| 4.2.5 | Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Provenance während des Bereitstellungsprozesses vor der Containerausführung überprüft werden und dass Verifizierungsfehler zum Scheitern der Bereitstellung führen.   |   2   |  D/V  |
| 4.2.6 | Stellen Sie sicher, dass Build-Umgebungen in flüchtigen Containern oder VMs ohne persistenten Speicher und mit Netzwerktrennung von Produktions-VPCs ausgeführt werden.                                                   |   2   |  D/V  |

---

## C4.3 Netzwerksicherheit & Zugriffskontrolle

Implementieren Sie Zero-Trust-Netzwerke mit standardmäßigen Verweigerungsrichtlinien und verschlüsselter Kommunikation.

|   #   | Beschreibung                                                                                                                                                                                                             | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.3.1 | Verifizieren Sie, dass Kubernetes NetworkPolicies oder ein Äquivalent ein standardmäßiges Verweigern von Ingress/Egress mit expliziten Erlaubnisregeln für erforderliche Ports (443, 8080, etc.) implementieren.         |   1   |  D/V  |
| 4.3.2 | Stellen Sie sicher, dass SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatsbasierte Authentifizierung erfordern.                                        |   1   |  D/V  |
| 4.3.3 | Stellen Sie sicher, dass ausgehender Datenverkehr über HTTP/HTTPS-Proxys (Squid, Istio oder Cloud-NAT-Gateways) mit Domain-Erlaubnislisten gefiltert wird und blockierte Anfragen protokolliert werden.                  |   2   |  D/V  |
| 4.3.4 | Überprüfen Sie, dass die Kommunikation zwischen Diensten Mutual TLS verwendet, wobei Zertifikate gemäß der Organisationsrichtlinie rotiert und die Zertifikatsvalidierung durchgesetzt wird (keine skip-verify-Flaggen). |   2   |  D/V  |
| 4.3.5 | Stellen Sie sicher, dass die KI-Infrastruktur in dedizierten VPCs/VNets ohne direkten Internetzugang betrieben wird und nur über NAT-Gateways oder Bastion-Hosts kommuniziert.                                           |   2   |  D/V  |

---

## C4.4 Geheimnisse & Verwaltung kryptografischer Schlüssel

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatisierte Rotation mit Zero-Trust-Zugriff.

|   #   | Beschreibung                                                                                                                                                                                                                | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.4.1 | Stellen Sie sicher, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager mit ruhender Verschlüsselung unter Verwendung von AES-256 gespeichert werden.                      |   1   |  D/V  |
| 4.4.2 | Überprüfen Sie, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) mit Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie erzeugt werden.                 |   1   |  D/V  |
| 4.4.3 | Überprüfen Sie, dass die Rotation von Geheimnissen automatisiert erfolgt, mit einer unterbrechungsfreien Bereitstellung und einer sofortigen Rotation, die durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.   |   2   |  D/V  |
| 4.4.4 | Stellen Sie sicher, dass Container-Images mit Tools (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds blockieren, die API-Schlüssel, Passwörter oder Zertifikate enthalten.                            |   2   |  D/V  |
| 4.4.5 | Überprüfen Sie, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Prüfprotokolle mit Benutzeridentitäten und Zeitstempeln dokumentiert wird.     |   2   |  D/V  |
| 4.4.6 | Stellen Sie sicher, dass Geheimnisse über Kubernetes-Secrets, gemountete Volumes oder Init-Container injiziert werden, und stellen Sie sicher, dass Geheimnisse niemals in Umgebungsvariablen oder Images eingebettet sind. |   2   |  D/V  |

---

## C4.5 KI-Arbeitslast-Sandboxing & Validierung

Isolieren Sie nicht vertrauenswürdige KI-Modelle in sicheren Sandboxes mit umfassender Verhaltensanalyse.

|   #   | Beschreibung                                                                                                                                                                                                                   | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.5.1 | Stellen Sie sicher, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit den Flags --security-opt=no-new-privileges und --read-only ausgeführt werden.                            |   1   |  D/V  |
| 4.5.2 | Stellen Sie sicher, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost mit allen externen Anfragen, die durch iptables-Regeln blockiert sind.                              |   1   |  D/V  |
| 4.5.3 | Stellen Sie sicher, dass die Validierung von KI-Modellen automatisierte Red-Team-Tests mit organisatorisch definiertem Testumfang und Verhaltensanalysen zur Erkennung von Hintertüren umfasst.                                |   2   |  D/V  |
| 4.5.4 | Stellen Sie sicher, dass vor der Freigabe eines KI-Modells für die Produktion die Sandbox-Ergebnisse von autorisiertem Sicherheitspersonal kryptografisch signiert und in unveränderlichen Prüfprotokollen gespeichert werden. |   2   |  D/V  |
| 4.5.5 | Stellen Sie sicher, dass Sandbox-Umgebungen zwischen den Bewertungen zerstört und aus Gold-Images neu erstellt werden, wobei eine vollständige Bereinigung des Dateisystems und des Arbeitsspeichers erfolgt.                  |   2   |  D/V  |

---

## C4.6 Infrastruktur-Sicherheitsüberwachung

Infrastruktur kontinuierlich scannen und überwachen mit automatisierter Behebung und Echtzeit-Benachrichtigung.

|   #   | Beschreibung                                                                                                                                                                                                                         | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.6.1 | Stellen Sie sicher, dass Container-Images gemäß den organisatorischen Zeitplänen gescannt werden, wobei KRITISCHE Schwachstellen die Bereitstellung basierend auf den organisatorischen Risikoschwellen blockieren.                  |   1   |  D/V  |
| 4.6.2 | Überprüfen Sie, ob die Infrastruktur die CIS-Benchmarks oder NIST 800-53-Kontrollen mit organisatorisch definierten Compliance-Schwellenwerten und automatischer Behebung bei fehlgeschlagenen Prüfungen erfüllt.                    |   1   |  D/V  |
| 4.6.3 | Überprüfen Sie, ob Schwachstellen mit HÖHERER Kritikalität gemäß den Zeitplänen des organisatorischen Risikomanagements gepatcht werden, einschließlich Notfallverfahren für aktiv ausgenutzte CVEs.                                 |   2   |  D/V  |
| 4.6.4 | Überprüfen Sie, dass Sicherheitswarnungen mit SIEM-Plattformen (Splunk, Elastic oder Sentinel) unter Verwendung der Formate CEF oder STIX/TAXII mit automatischer Anreicherung integriert werden.                                    |   2   |   V   |
| 4.6.5 | Überprüfen Sie, dass Infrastrukturmetriken mit SLA-Dashboards und Executive-Reporting an Überwachungssysteme (Prometheus, DataDog) exportiert werden.                                                                                |   3   |   V   |
| 4.6.6 | Überprüfen Sie, dass Konfigurationsabweichungen mithilfe von Tools (Chef InSpec, AWS Config) entsprechend den organisatorischen Überwachungsanforderungen erkannt werden, mit automatischem Rollback bei unautorisierten Änderungen. |   2   |  D/V  |

---

## C4.7 KI-Infrastruktur-Ressourcenmanagement

Verhindern Sie Angriffe durch Ressourcenerschöpfung und gewährleisten Sie eine faire Ressourcenzuteilung durch Quoten und Überwachung.

|   #   | Beschreibung                                                                                                                                                                                                                                              | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.7.1 | Überprüfen Sie, ob die GPU/TPU-Auslastung überwacht wird, wobei bei organisatorisch definierten Schwellenwerten Warnmeldungen ausgelöst und basierend auf Kapazitätsmanagement-Richtlinien automatische Skalierung oder Lastenausgleich aktiviert werden. |   1   |  D/V  |
| 4.7.2 | Überprüfen Sie, ob AI-Arbeitslastmetriken (Inference-Latenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Überwachungsanforderungen erfasst und mit der Infrastruktur-Auslastung korreliert werden.                                                |   1   |  D/V  |
| 4.7.3 | Überprüfen Sie, ob Kubernetes ResourceQuotas oder ein Äquivalent einzelne Workloads gemäß den organisatorischen Richtlinien zur Ressourcenzuteilung mit durchgesetzten harten Grenzwerten begrenzen.                                                      |   2   |  D/V  |
| 4.7.4 | Überprüfen Sie, ob die Kostenüberwachung die Ausgaben pro Arbeitslast/Mieter verfolgt, mit Warnmeldungen basierend auf den Budgetgrenzen der Organisation und automatisierten Kontrollen bei Budgetüberschreitungen.                                      |   2   |   V   |
| 4.7.5 | Stellen Sie sicher, dass die Kapazitätsplanung historische Daten mit organisatorisch definierten Prognosezeiträumen verwendet und eine automatisierte Ressourcenbereitstellung basierend auf Nachfragemustern erfolgt.                                    |   3   |   V   |
| 4.7.6 | Überprüfen Sie, dass Ressourcenerschöpfung entsprechend den organisatorischen Reaktionsanforderungen Circuit Breaker auslöst, einschließlich der Drosselung basierend auf Kapazitätsrichtlinien und Workload-Isolierung.                                  |   2   |  D/V  |

---

## C4.8 Umgebungstrennung & Promotion-Kontrollen

Durchsetzung strenger Umgebungsgrenzen mit automatisierten Beförderungstoren und Sicherheitsvalidierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                                       | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.8.1 | Stellen Sie sicher, dass Entwicklungs-, Test- und Produktionsumgebungen in separaten VPCs/VNets laufen, ohne gemeinsam genutzte IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen.                                                                                          |   1   |  D/V  |
| 4.8.2 | Stellen Sie sicher, dass die Beförderung der Umgebung die Genehmigung von organisatorisch definiertem autorisiertem Personal mit kryptografischen Signaturen und unveränderlichen Prüfpfaden erfordert.                                                                            |   1   |  D/V  |
| 4.8.3 | Stellen Sie sicher, dass Produktionsumgebungen den SSH-Zugang blockieren, Debug-Endpunkte deaktivieren und Änderungsanforderungen mit organisatorischen Vorankündigungsanforderungen außer in Notfällen verlangen.                                                                 |   2   |  D/V  |
| 4.8.4 | Stellen Sie sicher, dass Änderungen an Infrastructure-as-Code vor dem Merge in den Hauptzweig eine Peer-Review, automatisierte Tests und eine Sicherheitsüberprüfung durchlaufen.                                                                                                  |   2   |  D/V  |
| 4.8.5 | Überprüfen Sie, ob Nicht-Produktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert wurden, die Generierung synthetischer Daten erfolgt ist oder eine vollständige Datenmaskierung mit Entfernung personenbezogener Informationen (PII) verifiziert wurde. |   2   |  D/V  |
| 4.8.6 | Stellen Sie sicher, dass die Promotion-Gates automatisierte Sicherheitstests (SAST, DAST, Container-Scanning) enthalten, wobei für die Genehmigung keine CRITICAL-Funde zulässig sind.                                                                                             |   2   |  D/V  |

---

## C4.9 Infrastruktur-Backup & Wiederherstellung

Sichern Sie die Infrastrukturresilienz durch automatisierte Backups, getestete Wiederherstellungsverfahren und Katastrophenwiederherstellungsfunktionen.

|   #   | Beschreibung                                                                                                                                                                                                               | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.9.1 | Überprüfen Sie, ob die Infrastrukturkonfigurationen gemäß den organisatorischen Sicherungsplänen mit der 3-2-1-Backup-Strategie in geografisch getrennte Regionen gesichert werden.                                        |   1   |  D/V  |
| 4.9.2 | Stellen Sie sicher, dass Backup-Systeme in isolierten Netzwerken mit separaten Zugangsdaten und luftgetrenntem Speicher zum Schutz vor Ransomware betrieben werden.                                                        |   2   |  D/V  |
| 4.9.3 | Stellen Sie sicher, dass Wiederherstellungsverfahren gemäß den organisatorischen Zeitplänen mit automatisierten Tests geprüft und validiert werden, wobei RTO- und RPO-Ziele die organisatorischen Anforderungen erfüllen. |   2   |   V   |
| 4.9.4 | Stellen Sie sicher, dass die Notfallwiederherstellung AI-spezifische Runbooks mit der Wiederherstellung der Modellgewichte, dem Wiederaufbau von GPU-Clustern und der Abbildung von Dienstabhängigkeiten umfasst.          |   3   |   V   |

---

## C4.10 Infrastruktur-Compliance & Governance

Gewährleisten Sie die Einhaltung gesetzlicher Vorschriften durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollmechanismen.

|   #    | Beschreibung                                                                                                                                                                                                      | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.10.1 | Stellen Sie sicher, dass die Einhaltung der Infrastruktur gemäß den organisatorischen Zeitplänen anhand der SOC 2-, ISO 27001- oder FedRAMP-Kontrollen mit automatischer Evidenzsammlung bewertet wird.           |   2   |  D/V  |
| 4.10.2 | Überprüfen Sie, ob die Infrastruktur-Dokumentation Netzwerkdiagramme, Datenflusskarten und Bedrohungsmodelle enthält, die gemäß den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden. |   2   |   V   |
| 4.10.3 | Stellen Sie sicher, dass Infrastrukturänderungen einer automatisierten Compliance-Auswirkungsbewertung unterzogen werden, die bei risikoreichen Änderungen regulatorische Genehmigungsabläufe beinhaltet.         |   3   |  D/V  |

---

## C4.11 KI-Hardware-Sicherheit

Sichern Sie KI-spezifische Hardwarekomponenten einschließlich GPUs, TPUs und spezialisierter KI-Beschleuniger.

|   #    | Beschreibung                                                                                                                                                                                                                   | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.11.1 | Stellen Sie sicher, dass die Firmware des KI-Beschleunigers (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen überprüft wird und entsprechend den Zeitplänen des organisatorischen Patch-Managements aktualisiert wird. |   2   |  D/V  |
| 4.11.2 | Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestierung mit TPM 2.0, Intel TXT oder AMD SVM überprüft wird.                                               |   2   |  D/V  |
| 4.11.3 | Stellen Sie sicher, dass der GPU-Speicher zwischen den Workloads mithilfe von SR-IOV, MIG (Multi-Instance GPU) oder einer gleichwertigen Hardwarepartitionierung mit Speichersanitierung zwischen den Jobs isoliert ist.       |   2   |  D/V  |
| 4.11.4 | Stellen Sie sicher, dass die Lieferkette der KI-Hardware eine Herkunftsprüfung mit Herstellungszertifikaten und eine Validierung der manipulationssicheren Verpackung umfasst.                                                 |   3   |   V   |
| 4.11.5 | Stellen Sie sicher, dass Hardware-Sicherheitsmodule (HSMs) KI-Modellgewichte und kryptografische Schlüssel mit FIPS 140-2 Level 3 oder Common Criteria EAL4+-Zertifizierung schützen.                                          |   3   |  D/V  |

---

## C4.12 Edge- und verteilte KI-Infrastruktur

Sichere verteilte KI-Einsätze, einschließlich Edge-Computing, föderiertem Lernen und Multi-Site-Architekturen.

|   #    | Beschreibung                                                                                                                                                                                                                 | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.12.1 | Stellen Sie sicher, dass Edge-AI-Geräte sich gegenüber der zentralen Infrastruktur mittels mutual TLS mit Gerätezertifikaten authentifizieren, die gemäß der organisatorischen Zertifikatsverwaltungspolitik rotiert werden. |   2   |  D/V  |
| 4.12.2 | Stellen Sie sicher, dass Edge-Geräte Secure Boot mit verifizierten Signaturen und Rollback-Schutz implementieren, um Firmware-Downgrade-Angriffe zu verhindern.                                                              |   2   |  D/V  |
| 4.12.3 | Überprüfen Sie, ob die verteilte KI-Koordination byzantinisch fehlertolerante Konsensalgorithmen mit Teilnehmervalidierung und bösartiger Knotenerkennung verwendet.                                                         |   3   |  D/V  |
| 4.12.4 | Stellen Sie sicher, dass die Kommunikation zwischen Edge und Cloud Bandbreitenbegrenzung, Datenkompression und Offline-Betriebsfähigkeit mit sicherer lokaler Speicherung umfasst.                                           |   3   |  D/V  |

---

## C4.13 Multi-Cloud- und Hybrid-Infrastruktursicherheit

Sichern Sie KI-Arbeitslasten über mehrere Cloud-Anbieter hinweg sowie bei hybridem Cloud- und On-Premises-Betrieb.

|   #    | Beschreibung                                                                                                                                                                                                                                       | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.13.1 | Stellen Sie sicher, dass Multi-Cloud-AI-Bereitstellungen cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralem Richtlinienmanagement über Anbieter hinweg verwenden.                                                                   |   2   |  D/V  |
| 4.13.2 | Stellen Sie sicher, dass der Datentransfer zwischen verschiedenen Clouds eine Ende-zu-Ende-Verschlüsselung mit vom Kunden verwalteten Schlüsseln verwendet und die Datenresidenzkontrollen gemäß der jeweiligen Rechtsordnung durchgesetzt werden. |   2   |  D/V  |
| 4.13.3 | Stellen Sie sicher, dass hybride Cloud-KI-Workloads konsistente Sicherheitsrichtlinien sowohl in lokalen als auch in Cloud-Umgebungen mit einheitlicher Überwachung und Alarmierung implementieren.                                                |   2   |  D/V  |
| 4.13.4 | Überprüfen Sie, dass die Vermeidung von Cloud-Anbieterabhängigkeit portable Infrastructure-as-Code, standardisierte APIs und Datenexportfunktionen mit Formatkonvertierungstools umfasst.                                                          |   3   |   V   |
| 4.13.5 | Überprüfen Sie, ob die Multi-Cloud-Kostenoptimierung Sicherheitskontrollen beinhaltet, die sowohl die Ausbreitung von Ressourcen verhindern als auch unerlaubte gebührenpflichtige Datentransfers zwischen Clouds.                                 |   3   |   V   |

---

## C4.14 Infrastruktur-Automatisierung & GitOps-Sicherheit

Sichern Sie Automatisierungspipelines für Infrastruktur und GitOps-Workflows für das Management von KI-Infrastrukturen.

|   #    | Beschreibung                                                                                                                                                                                                                                         | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.14.1 | Stellen Sie sicher, dass GitOps-Repositorien signierte Commits mit GPG-Schlüsseln erfordern und Branch-Schutzregeln implementiert sind, die direkte Pushes auf Hauptzweige verhindern.                                                               |   2   |  D/V  |
| 4.14.2 | Stellen Sie sicher, dass die Infrastrukturautomatisierung eine Drift-Erkennung mit automatischer Behebung und Rückrollfunktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen für nicht autorisierte Änderungen ausgelöst werden. |   2   |  D/V  |
| 4.14.3 | Überprüfen Sie, ob die automatisierte Bereitstellung der Infrastruktur eine Validierung der Sicherheitsrichtlinien umfasst und die Bereitstellung bei nicht konformen Konfigurationen blockiert wird.                                                |   2   |  D/V  |
| 4.14.4 | Verifizieren Sie, dass Infrastruktur-Automatisierungsgeheimnisse durch externe Secret-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.                                                               |   2   |  D/V  |
| 4.14.5 | Überprüfen Sie, ob die selbstheilende Infrastruktur die Korrelation von Sicherheitsereignissen mit automatisierter Reaktionsauslösung auf Vorfälle und Benachrichtigungsabläufen für Beteiligte umfasst.                                             |   3   |   V   |

---

## C4.15 Quantenresistente Infrastruktursicherheit

Bereiten Sie die KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor, indem Sie postquantum-kryptographische Verfahren und quantensichere Protokolle einsetzen.

|   #    | Beschreibung                                                                                                                                                                                                              | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Überprüfen Sie, ob die KI-Infrastruktur NIST-zugelassene postquantensichere kryptografische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für den Schlüsselaustausch und digitale Signaturen implementiert.  |   3   |  D/V  |
| 4.15.2 | Verifizieren Sie, dass Quanten-Schlüsselverteilungssysteme (QKD) für hochsichere KI-Kommunikationen mit quantensicheren Schlüsselverwaltungprotokollen implementiert sind.                                                |   3   |  D/V  |
| 4.15.3 | Überprüfen Sie, ob kryptografische Agilitätsframeworks eine schnelle Migration zu neuen postquantensicheren Algorithmen mit automatischer Zertifikats- und Schlüsselrotation ermöglichen.                                 |   3   |  D/V  |
| 4.15.4 | Verifizieren Sie, dass die Bedrohungsmodellierung durch Quantenrechner die Verwundbarkeit der KI-Infrastruktur gegenüber Quantenangriffen bewertet und dokumentierte Migrationszeitpläne sowie Risikobewertungen enthält. |   3   |   V   |
| 4.15.5 | Verifizieren Sie, dass hybride klassische-quantum kryptografische Systeme während der Quantenübergangsphase mit Leistungsüberwachung eine Tiefenverteidigung bieten.                                                      |   3   |  D/V  |

---

## C4.16 Vertrauliches Rechnen & Sichere Enklaven

Schützen Sie KI-Arbeitslasten und Modellgewichte mithilfe hardwarebasierter vertrauenswürdiger Ausführungsumgebungen und vertraulicher Computertechnologien.

|   #    | Beschreibung                                                                                                                                                                                     | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.16.1 | Stellen Sie sicher, dass sensible KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsüberprüfung ausgeführt werden.       |   3   |  D/V  |
| 4.16.2 | Überprüfen Sie, ob vertrauliche Container (Kata Containers, gVisor mit Confidential Computing) KI-Arbeitslasten mittels hardwaregestützter Speicher-Verschlüsselung isolieren.                   |   3   |  D/V  |
| 4.16.3 | Stellen Sie sicher, dass die Remote-Attestation die Integrität der Enklave validiert, bevor KI-Modelle mit kryptografischem Nachweis der Authentizität einer Ausführungsumgebung geladen werden. |   3   |  D/V  |
| 4.16.4 | Überprüfen Sie, dass vertrauliche KI-Inferenzdienste die Modellauslesung durch verschlüsselte Berechnung mit versiegelten Modellgewichten und geschützter Ausführung verhindern.                 |   3   |  D/V  |
| 4.16.5 | Überprüfen Sie, ob die Orchestrierung der Trusted Execution Environment den Lebenszyklus des sicheren Enclaves mit Remote-Attestation und verschlüsselten Kommunikationskanälen verwaltet.       |   3   |  D/V  |
| 4.16.6 | Überprüfen Sie, dass sichere Mehrparteienberechnung (SMPC) kollaboratives KI-Training ermöglicht, ohne einzelne Datensätze oder Modellparameter offenzulegen.                                    |   3   |  D/V  |

---

## C4.17 Zero-Knowledge-Infrastruktur

Implementieren Sie Zero-Knowledge-Beweissysteme für datenschutzfreundliche AI-Verifikation und Authentifizierung, ohne sensible Informationen preiszugeben.

|   #    | Beschreibung                                                                                                                                                                                         | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.17.1 | Überprüfen Sie, dass Zero-Knowledge-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität von KI-Modellen und die Herkunft des Trainings verifizieren, ohne Modellgewichte oder Trainingsdaten offenzulegen. |   3   |  D/V  |
| 4.17.2 | Verifizieren Sie, dass ZK-basierte Authentifizierungssysteme eine datenschutzfreundliche Benutzerüberprüfung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen preiszugeben.         |   3   |  D/V  |
| 4.17.3 | Stellen Sie sicher, dass Private-Set-Intersection-(PSI)-Protokolle eine sichere Datenabgleichung für föderierte KI ermöglichen, ohne individuelle Datensätze offenzulegen.                           |   3   |  D/V  |
| 4.17.4 | Überprüfen Sie, dass Zero-Knowledge-Machine-Learning (ZKML)-Systeme verifizierbare KI-Schlüsse mit kryptografischem Nachweis der korrekten Berechnung ermöglichen.                                   |   3   |  D/V  |
| 4.17.5 | Stellen Sie sicher, dass ZK-Rollups eine skalierbare, datenschutzwahrende KI-Transaktionsverarbeitung mit Stapelverifizierung und reduziertem Rechenaufwand bieten.                                  |   3   |  D/V  |

---

## C4.18 Verhinderung von Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor Timing-, Leistungs-, elektromagnetischen und Cache-basierten Side-Channel-Angriffen, die sensible Informationen preisgeben könnten.

|   #    | Beschreibung                                                                                                                                                                                | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.18.1 | Verifizieren Sie, dass die AI-Inferenzzeit mit konstanten Zeitalgorithmen und Padding normalisiert wird, um Timing-basierte Modellextraktionsangriffe zu verhindern.                        |   3   |  D/V  |
| 4.18.2 | Stellen Sie sicher, dass der Schutz vor Leistungsanalyse Rauschinjektion, Stromleitungsfilterung und zufällig ausgeführte Muster für KI-Hardware umfasst.                                   |   3   |  D/V  |
| 4.18.3 | Überprüfen Sie, ob die Abschwächung von Seiteneffekten bei Cache-basierten Angriffen Cache-Partitionierung, Randomisierung und Flush-Befehle verwendet, um Informationslecks zu verhindern. |   3   |  D/V  |
| 4.18.4 | Stellen Sie sicher, dass der Schutz vor elektromagnetischen Abstrahlungen Abschirmung, Signalfilterung und zufällige Verarbeitung umfasst, um TEMPEST-ähnliche Angriffe zu verhindern.      |   3   |  D/V  |
| 4.18.5 | Überprüfen Sie, ob mikroarchitekturelle Seitenkanalabwehrmaßnahmen spekulative Ausführungssteuerungen und die Verschleierung von Speicherzugriffsmustern umfassen.                          |   3   |  D/V  |

---

## C4.19 Neuromorphe & Spezialisierte KI-Hardware-Sicherheit

Sichern Sie aufkommende KI-Hardwarearchitekturen, einschließlich neuromorpher Chips, FPGAs, kundenspezifischer ASICs und optischer Rechensysteme.

|   #    | Beschreibung                                                                                                                                                                                             | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.19.1 | Überprüfen Sie, dass die Sicherheit neuromorpher Chips Spike-Muster-Verschlüsselung, Schutz der synaptischen Gewichtung und hardwarebasierte Validierung der Lernregel umfasst.                          |   3   |  D/V  |
| 4.19.2 | Überprüfen Sie, ob FPGA-basierte KI-Beschleuniger Bitstromverschlüsselung, Schutzmechanismen gegen Manipulation und sichere Konfigurationsladeverfahren mit authentifizierten Updates implementieren.    |   3   |  D/V  |
| 4.19.3 | Verifizieren Sie, dass die benutzerdefinierte ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, eine hardwarebasierte Vertrauenswurzel und sichere Schlüsselverwaltung mit Manipulationserkennung umfasst. |   3   |  D/V  |
| 4.19.4 | Stellen Sie sicher, dass optische Rechensysteme quantensichere optische Verschlüsselung, sichere photonische Schalttechnik und geschützte optische Signalverarbeitung implementieren.                    |   3   |  D/V  |
| 4.19.5 | Überprüfen Sie, dass hybride analog-digitale KI-Chips sichere analoge Berechnungen, geschützte Gewichtsspeicherung und authentifizierte Analog-Digital-Umwandlung enthalten.                             |   3   |  D/V  |

---

## C4.20 Datenschutzwahrende Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzfreundliche Berechnungen, um sensible Daten während der KI-Verarbeitung und -Analyse zu schützen.

|   #    | Beschreibung                                                                                                                                                                                                                          | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.20.1 | Überprüfen Sie, dass die homomorphe Verschlüsselungsinfrastruktur verschlüsselte Berechnungen auf sensiblen KI-Arbeitslasten unter Gewährleistung der kryptographischen Integritätsprüfung und Leistungsüberwachung ermöglicht.       |   3   |  D/V  |
| 4.20.2 | Verifizieren Sie, dass Systeme für die private Informationsabfrage Datenbankanfragen ermöglichen, ohne Abfragemuster offenzulegen, durch kryptografischen Schutz der Zugriffsmuster.                                                  |   3   |  D/V  |
| 4.20.3 | Überprüfen Sie, dass sichere Mehrparteienberechnungsprotokolle eine datenschutzwahrende KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenergebnisse offenzulegen.                                                         |   3   |  D/V  |
| 4.20.4 | Stellen Sie sicher, dass die datenschutzfreundliche Schlüsselverwaltung verteilte Schlüsselerzeugung, Schwellenwert-Kryptografie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.                                 |   3   |  D/V  |
| 4.20.5 | Stellen Sie sicher, dass die Leistung der datenschutzfreundlichen Berechnung durch Batch-Verarbeitung, Caching und Hardwarebeschleunigung optimiert wird, während die kryptografischen Sicherheitsgarantien aufrechterhalten bleiben. |   3   |  D/V  |

---

## C4.15 Agent Framework Cloud-Integrationssicherheit & hybride Bereitstellung

Sicherheitskontrollen für cloud-integrierte Agentenframeworks mit hybriden On-Premises/Cloud-Architekturen.

|   #    | Beschreibung                                                                                                                                              | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Stellen Sie sicher, dass die Cloud-Speicherintegration End-to-End-Verschlüsselung mit agentengesteuertem Schlüsselmanagement verwendet.                   |   1   |  D/V  |
| 4.15.2 | Stellen Sie sicher, dass die Sicherheitsgrenzen der hybriden Bereitstellung klar definiert sind und verschlüsselte Kommunikationskanäle verwendet werden. |   2   |  D/V  |
| 4.15.3 | Überprüfen Sie, dass der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung umfasst.                       |   2   |  D/V  |
| 4.15.4 | Stellen Sie sicher, dass Anforderungen an den Datenaufenthalt durch kryptographische Bestätigung der Speicherorte durchgesetzt werden.                    |   3   |  D/V  |
| 4.15.5 | Überprüfen Sie, ob die Sicherheitsbewertungen des Cloud-Anbieters agentenspezifische Bedrohungsmodellierung und Risikobewertung umfassen.                 |   3   |  D/V  |

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

