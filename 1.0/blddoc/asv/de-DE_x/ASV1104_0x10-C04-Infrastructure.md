# C4 Infrastruktur, Konfiguration und Bereitstellungssicherheit

## Kontrollziel

KI-Infrastruktur muss gegen Privilegieneskalation, Manipulation der Lieferkette und laterale Bewegungen durch sichere Konfiguration, Laufzeitisolierung, vertrauenswürdige Bereitstellungspipelines und umfassende Überwachung gehärtet werden. Nur autorisierte, validierte Infrastrukturkomponenten und Konfigurationen gelangen durch kontrollierte Prozesse in die Produktion, die Sicherheit, Integrität und Auditierbarkeit gewährleisten.

Kernziel der Sicherheit: Nur kryptografisch signierte, auf Schwachstellen geprüfte Infrastrukturkomponenten gelangen durch automatisierte Validierungspipelines in die Produktion, die Sicherheitsrichtlinien durchsetzen und unveränderliche Audit-Trails aufrechterhalten.

---

## C4.1 Laufzeitumgebungs-Isolation

Verhindern Sie Container-Ausbrüche und Privilegien-Eskalationen durch Kernel-Ebene-Isolationsprimitiven und Mandatory Access Controls.

|   #   | Beschreibung                                                                                                                                                                                                                                      | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.1.1 | Überprüfen Sie, dass alle KI-Container alle Linux-Fähigkeiten außer CAP_SETUID, CAP_SETGID und ausdrücklich in den Sicherheitsbaselines dokumentierte erforderliche Fähigkeiten ablegen.                                                          |   1   |  D/V  |
| 4.1.2 | Stellen Sie sicher, dass Seccomp-Profile alle Systemaufrufe blockieren, außer denjenigen in vorab genehmigten Freigabelisten; bei Verstößen wird der Container beendet und Sicherheitswarnungen ausgelöst.                                        |   1   |  D/V  |
| 4.1.3 | Vergewissern Sie sich, dass KI-Arbeitslasten mit schreibgeschützten Root-Dateisystemen, tmpfs für temporäre Daten und benannten Volumes für persistente Daten ausgeführt werden, wobei noexec-Mount-Optionen durchgesetzt werden.                 |   2   |  D/V  |
| 4.1.4 | Stellen Sie sicher, dass die eBPF-basierte Laufzeitüberwachung (Falco, Tetragon oder Äquivalent) Versuche der Privilegienerhöhung erkennt und automatisch die betroffenen Prozesse innerhalb der organisatorischen Reaktionszeitvorgaben beendet. |   2   |  D/V  |
| 4.1.5 | Stellen Sie sicher, dass hochrisikoreiche KI-Workloads in hardwareisolierten Umgebungen (Intel TXT, AMD SVM oder dedizierte Bare-Metal-Knoten) mit Attestierungsprüfung ausgeführt werden.                                                        |   3   |  D/V  |

---

## C4.2 Sichere Build- und Deployment-Pipelines

Gewährleisten Sie kryptografische Integrität und Lieferkettensicherheit durch reproduzierbare Builds und signierte Artefakte.

|   #   | Beschreibung                                                                                                                                                                                                                                            | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.2.1 | Stellen Sie sicher, dass Infrastruktur als Code bei jedem Commit mit Tools (tfsec, Checkov oder Terrascan) gescannt wird und Merge-Vorgänge mit CRITICAL- oder HIGH-Schweregradbefunden blockiert werden.                                               |   1   |  D/V  |
| 4.2.2 | Überprüfen Sie, dass Container-Builds reproduzierbar sind und über Builds hinweg identische SHA256 Hashes aufweisen, und erzeugen Sie SLSA Level 3 Provenanceattestationen, die mit Sigstore signiert sind.                                             |   1   |  D/V  |
| 4.2.3 | Verifizieren Sie, dass Container-Images CycloneDX- oder SPDX-SBOMs enthalten und mit Cosign signiert sind, bevor der Push in die Registry erfolgt, und dass unsignierte Images bei der Bereitstellung abgelehnt werden.                                 |   2   |  D/V  |
| 4.2.4 | Stellen Sie sicher, dass CI/CD-Pipelines OIDC-Tokens von HashiCorp Vault, AWS IAM-Rollen oder Azure Managed Identity verwenden, deren Gültigkeitsdauer die in den organisatorischen Sicherheitsrichtlinien festgelegten Grenzwerte nicht überschreitet. |   2   |  D/V  |
| 4.2.5 | Stellen Sie sicher, dass Cosign-Signaturen und SLSA-Provenance während des Bereitstellungsprozesses vor der Ausführung des Containers validiert werden, und dass Verifizierungsfehler dazu führen, dass die Bereitstellung fehlschlägt.                 |   2   |  D/V  |
| 4.2.6 | Stellen Sie sicher, dass Build-Umgebungen in flüchtigen Containern oder VMs laufen, die keinen persistenten Speicher haben und vom Produktions-VPC-Netzwerk isoliert sind.                                                                              |   2   |  D/V  |

---

## C4.3 Netzwerksicherheit und Zugriffskontrolle

Implementieren Sie Zero-Trust-Netzwerk mit Standard-Verweigerungsrichtlinien und verschlüsselter Kommunikation.

|   #   | Beschreibung                                                                                                                                                                                                                            | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.3.1 | Überprüfen Sie, ob Kubernetes-Netzwerkrichtlinien oder eine äquivalente Implementierung standardmäßig eingehenden und ausgehenden Verkehr verweigern und explizite Zulassungsregeln für erforderliche Ports (443, 8080 usw.) enthalten. |   1   |  D/V  |
| 4.3.2 | Überprüfen Sie, ob SSH (Port 22), RDP (Port 3389) und Cloud-Metadaten-Endpunkte (169.254.169.254) blockiert sind oder eine zertifikatbasierte Authentifizierung erfordern.                                                              |   1   |  D/V  |
| 4.3.3 | Verifizieren Sie, dass ausgehender Verkehr durch HTTP/HTTPS-Proxys (Squid, Istio oder Cloud NAT-Gateways) mit Domänen-Whitelists gefiltert wird und blockierte Anfragen protokolliert werden.                                           |   2   |  D/V  |
| 4.3.4 | Stellen Sie sicher, dass die Inter-Service-Kommunikation mutual TLS verwendet, Zertifikate gemäß den organisatorischen Richtlinien rotiert werden und die Zertifikatvalidierung durchgesetzt wird (keine Skip-Verify-Flags).            |   2   |  D/V  |
| 4.3.5 | Überprüfen Sie, dass die KI-Infrastruktur in dedizierten VPCs/VNets läuft, keinen direkten Internetzugang hat und ausschließlich über NAT-Gateways oder Bastion-Hosts kommuniziert.                                                     |   2   |  D/V  |

---

## C4.4 Geheimnisse & Kryptografische Schlüsselverwaltung

Schützen Sie Anmeldeinformationen durch hardwaregestützte Speicherung und automatische Rotation mit Zero-Trust-Zugriff.

|   #   | Beschreibung                                                                                                                                                                                                                  | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.4.1 | Vergewissern Sie sich, dass Geheimnisse in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault oder Google Secret Manager gespeichert sind und dort im Ruhezustand durch AES-256-Verschlüsselung geschützt sind.            |   1   |  D/V  |
| 4.4.2 | Stellen Sie sicher, dass kryptografische Schlüssel in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) mit Schlüsselrotation gemäß der organisatorischen kryptografischen Richtlinie generiert werden.             |   1   |  D/V  |
| 4.4.3 | Vergewissern Sie sich, dass die Geheimnisrotation automatisiert erfolgt, dass die Bereitstellung ohne Ausfallzeit erfolgt und dass die Rotation sofort durch Personalwechsel oder Sicherheitsvorfälle ausgelöst wird.         |   2   |  D/V  |
| 4.4.4 | Verifizieren Sie, dass Container-Images mit Tools (GitLeaks, TruffleHog oder detect-secrets) gescannt werden, die Builds blockieren, die API-Schlüssel, Passwörter oder Zertifikate enthalten.                                |   2   |  D/V  |
| 4.4.5 | Stellen Sie sicher, dass der Zugriff auf Produktionsgeheimnisse eine MFA mit Hardware-Token (YubiKey, FIDO2) erfordert und durch unveränderliche Auditprotokolle mit Benutzeridentitäten und Zeitstempeln aufgezeichnet wird. |   2   |  D/V  |
| 4.4.6 | Überprüfen Sie, dass Secrets über Kubernetes-Secrets, gemountete Volumes oder Init-Containeren injiziert werden, und stellen Sie sicher, dass Secrets niemals in Umgebungsvariablen oder Images eingebettet werden.           |   2   |  D/V  |

---

## C4.5 KI-Arbeitslast-Sandboxing & Validierung

Isolieren Sie unvertrauenswürdige KI-Modelle in sicheren Sandbox-Umgebungen mit umfassender Verhaltensanalyse.

|   #   | Beschreibung                                                                                                                                                                                                                              | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.5.1 | Stellen Sie sicher, dass externe KI-Modelle in gVisor, MicroVMs (wie Firecracker, CrossVM) oder Docker-Containern mit --security-opt=no-new-privileges und --read-only ausgeführt werden.                                                 |   1   |  D/V  |
| 4.5.2 | Überprüfen Sie, dass Sandbox-Umgebungen keine Netzwerkverbindung haben (--network=none) oder nur Zugriff auf localhost ermöglichen, wobei alle externen Anfragen durch iptables-Regeln blockiert werden.                                  |   1   |  D/V  |
| 4.5.3 | Stellen Sie sicher, dass die Validierung von KI-Modellen automatisierte Red-Team-Tests mit organisationsweit festgelegter Testabdeckung und Verhaltensanalyse zur Backdoor-Erkennung umfasst.                                             |   2   |  D/V  |
| 4.5.4 | Stellen Sie sicher, dass ein KI-Modell erst dann in die Produktion überführt wird, wenn seine Sandbox-Ergebnisse kryptografisch von autorisiertem Sicherheitspersonal signiert und in unveränderlichen Auditprotokollen gespeichert sind. |   2   |  D/V  |
| 4.5.5 | Stellen Sie sicher, dass Sandbox-Umgebungen zwischen Evaluierungen vollständig gelöscht und aus Golden-Images neu erstellt werden, wobei das Dateisystem und der Arbeitsspeicher vollständig bereinigt werden.                            |   2   |  D/V  |

---

## C4.6 Infrastruktur-Sicherheitsüberwachung

Infrastruktur kontinuierlich scannen und überwachen, mit automatisierter Behebung und Echtzeit-Alarmierung.

|   #   | Beschreibung                                                                                                                                                                                                             | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.6.1 | Überprüfen Sie, dass Container-Images gemäß den organisatorischen Zeitplänen auf kritische Schwachstellen gescannt werden, die die Bereitstellung basierend auf organisatorischen Risikogrenzen blockieren.              |   1   |  D/V  |
| 4.6.2 | Überprüfen Sie, dass die Infrastruktur die CIS-Benchmarks oder NIST SP 800-53-Kontrollen erfüllt, mit organisatorisch definierten Compliance-Schwellenwerten und automatisierter Behebung für fehlgeschlagene Prüfungen. |   1   |  D/V  |
| 4.6.3 | Überprüfen Sie, dass Schwachstellen mit hohem Schweregrad gemäß den Zeitplänen des organisatorischen Risikomanagements behoben werden, mit Notfallmaßnahmen für aktiv ausgenutzte CVEs.                                  |   2   |  D/V  |
| 4.6.4 | Überprüfen Sie, dass Sicherheitswarnungen in SIEM-Plattformen (Splunk, Elastic oder Sentinel) unter Verwendung von CEF- oder STIX/TAXII-Formaten mit automatischer Anreicherung integriert werden.                       |   2   |   V   |
| 4.6.5 | Verifizieren Sie, dass Infrastrukturmetriken an Überwachungssysteme (Prometheus, DataDog) mit SLA-Dashboards und Berichten für das Management exportiert werden.                                                         |   3   |   V   |
| 4.6.6 | Überprüfen Sie, dass Konfigurationsabweichungen mithilfe von Tools (Chef InSpec, AWS Config) gemäß den organisatorischen Überwachungsanforderungen erkannt werden, mit automatischem Rollback bei unbefugten Änderungen. |   2   |  D/V  |

---

## C4.7 KI-Infrastruktur-Ressourcenmanagement

Verhindern Sie Ressourcenerschöpfungsangriffe und gewährleisten Sie eine faire Ressourcenzuteilung durch Quoten und Überwachung.

|   #   | Beschreibung                                                                                                                                                                                                                                           | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.7.1 | Stellen Sie sicher, dass die GPU-/TPU-Auslastung überwacht wird, Warnmeldungen bei organisatorisch festgelegten Schwellenwerten ausgelöst werden und automatische Skalierung oder Lastenausgleich gemäß Kapazitätsmanagementrichtlinien aktiviert ist. |   1   |  D/V  |
| 4.7.2 | Stellen Sie sicher, dass KI-Arbeitslastkennzahlen (Inferenzlatenz, Durchsatz, Fehlerraten) gemäß den organisatorischen Monitoring-Anforderungen erfasst werden und mit der Auslastung der Infrastruktur korreliert sind.                               |   1   |  D/V  |
| 4.7.3 | Überprüfen Sie, ob Kubernetes ResourceQuotas oder äquivalente Mechanismen einzelne Arbeitslasten gemäß organisatorischen Ressourcenallokationsrichtlinien mit harten Grenzwerten durchgesetzt werden.                                                  |   2   |  D/V  |
| 4.7.4 | Überprüfen Sie, dass die Kostenüberwachung die Ausgaben pro Arbeitslast/Mandant verfolgt, Warnungen basierend auf organisatorischen Budgetgrenzen bereitstellt und automatisierte Kontrollen bei Budgetüberschreitungen ermöglicht.                    |   2   |   V   |
| 4.7.5 | Stellen Sie sicher, dass die Kapazitätsplanung historische Daten verwendet, mit organisatorisch festgelegten Prognosezeiträumen und automatisierter Ressourcenbereitstellung basierend auf Nachfragemustern.                                           |   3   |   V   |
| 4.7.6 | Überprüfen Sie, dass Ressourcenerschöpfung Circuit-Breaker gemäß den organisatorischen Reaktionsanforderungen auslöst, einschließlich Ratenbegrenzung basierend auf Kapazitätsrichtlinien und Arbeitslastisolierung.                                   |   2   |  D/V  |

---

## C4.8 Trennung der Umgebungen und Freigabekontrollen

Durchsetzung strenger Umgebungsgrenzen mit automatisierten Freigabe-Toren und Sicherheitsvalidierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                          | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.8.1 | Stellen Sie sicher, dass Entwicklungs-, Test- und Produktionsumgebungen in separaten VPCs/VNets laufen und keine gemeinsamen IAM-Rollen, Sicherheitsgruppen oder Netzwerkverbindungen bestehen.                                                                       |   1   |  D/V  |
| 4.8.2 | Stellen Sie sicher, dass die Umgebungsfreigabe eine Genehmigung durch organisatorisch definierte befugte Personen mit kryptografischen Signaturen und unveränderlichen Audit-Trails erfordert.                                                                        |   1   |  D/V  |
| 4.8.3 | Stellen Sie sicher, dass Produktionsumgebungen SSH-Zugriff blockieren, Debug-Endpunkte deaktivieren und Änderungsanträge mit organisatorischen Vorankündigungsfristen verlangen, außer bei Notfällen.                                                                 |   2   |  D/V  |
| 4.8.4 | Stellen Sie sicher, dass Änderungen an Infrastructure-as-Code (IaC) eine Peer-Review mit automatisierten Tests und Sicherheitsprüfungen erfordern, bevor sie in den Hauptzweig zusammengeführt werden.                                                                |   2   |  D/V  |
| 4.8.5 | Überprüfen Sie, dass Nichtproduktionsdaten gemäß den organisatorischen Datenschutzanforderungen anonymisiert sind, dass die Erzeugung synthetischer Daten erfolgt bzw. dass eine vollständige Datenmaskierung mit Entfernung personenbezogener Daten verifiziert ist. |   2   |  D/V  |
| 4.8.6 | Stellen Sie sicher, dass Freigabetore automatisierte Sicherheitsprüfungen (SAST, DAST, Container-Scanning) enthalten, bei denen für die Freigabe keine kritischen Befunde erforderlich sind.                                                                          |   2   |  D/V  |

---

## C4.9 Infrastruktur-Backup und Wiederherstellung

Gewährleisten Sie die Infrastrukturresilienz durch automatisierte Backups, getestete Wiederherstellungsverfahren und Fähigkeiten zur Notfallwiederherstellung.

|   #   | Beschreibung                                                                                                                                                                                                                       | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.9.1 | Verifizieren Sie, dass Infrastrukturkonfigurationen gemäß den Backup-Zeitplänen der Organisation gesichert werden, um räumlich getrennte Regionen mit der Implementierung der 3-2-1-Backup-Strategie zu erreichen.                 |   1   |  D/V  |
| 4.9.2 | Vergewissern Sie sich, dass Backup-Systeme in isolierten Netzwerken mit separaten Anmeldeinformationen betrieben werden und über luftgetrennte Speicher verfügen, zum Schutz vor Ransomware.                                       |   2   |  D/V  |
| 4.9.3 | Vergewissern Sie sich, dass Wiederherstellungsverfahren durch automatisierte Tests gemäß den organisatorischen Zeitplänen getestet und validiert werden, wobei RTO- und RPO-Ziele den organisatorischen Anforderungen entsprechen. |   2   |   V   |
| 4.9.4 | Stellen Sie sicher, dass die Katastrophenwiederherstellung KI-spezifische Runbooks mit der Wiederherstellung der Modellgewichte, dem Neuaufbau des GPU-Clusters und der Kartierung der Dienstabhängigkeiten umfasst.               |   3   |   V   |

---

## C4.10 Infrastruktur-Compliance und Governance

Sicherstellung der Einhaltung regulatorischer Vorgaben durch kontinuierliche Bewertung, Dokumentation und automatisierte Kontrollen.

|   #    | Beschreibung                                                                                                                                                                                                        | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.10.1 | Stellen Sie sicher, dass die Compliance der Infrastruktur gemäß den organisatorischen Zeitplänen gegen SOC 2, ISO 27001 oder FedRAMP-Kontrollen bewertet wird, mit automatisierter Beweiserhebung.                  |   2   |  D/V  |
| 4.10.2 | Überprüfen Sie, ob die Infrastrukturdokumentation Netzwerkdiagramme, Datenflussdiagramme und Bedrohungsmodelle enthält, die gemäß den Anforderungen des organisatorischen Änderungsmanagements aktualisiert wurden. |   2   |   V   |
| 4.10.3 | Überprüfen Sie, dass Infrastrukturänderungen einer automatisierten Compliance-Folgenabschätzung unterzogen werden, zusammen mit regulatorischen Freigabeprozessen für risikoreiche Änderungen.                      |   3   |  D/V  |

---

## C4.11 KI-Hardware-Sicherheit

Sichere KI-spezifische Hardwarekomponenten, einschließlich GPUs, TPUs und spezialisierter KI-Beschleuniger.

|   #    | Beschreibung                                                                                                                                                                                                                              | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.11.1 | Stellen Sie sicher, dass die Firmware von KI-Beschleunigern (GPU-BIOS, TPU-Firmware) mit kryptografischen Signaturen verifiziert wird und gemäß den Zeitplänen des Patch-Managements der Organisation aktualisiert wird.                  |   2   |  D/V  |
| 4.11.2 | Stellen Sie sicher, dass vor der Ausführung der Arbeitslast die Integrität des KI-Beschleunigers durch Hardware-Attestation mittels TPM 2.0, Intel TXT oder AMD SVM validiert wird.                                                       |   2   |  D/V  |
| 4.11.3 | Stellen Sie sicher, dass der GPU-Speicher zwischen Arbeitslasten isoliert ist, indem Sie SR-IOV, MIG (Multi-Instance GPU) oder eine gleichwertige hardwarebasierte Partitionierung mit Speichersanitisierung zwischen den Jobs verwenden. |   2   |  D/V  |
| 4.11.4 | Überprüfen Sie, dass die KI-Hardware-Lieferkette eine Provenienzverifikation mit Herstellerzertifikaten sowie eine Validierung manipulationssicherer Verpackungen umfasst.                                                                |   3   |   V   |
| 4.11.5 | Stellen Sie sicher, dass Hardware-Sicherheitsmodule (HSMs) KI-Modellgewichte und kryptografische Schlüssel mit FIPS-140-2 Stufe 3 bzw. Common Criteria EAL4+ Zertifizierung geschützt sind.                                               |   3   |  D/V  |

---

## C4.12 Edge- und verteilte KI-Infrastruktur

Sichere verteilte KI-Bereitstellungen, einschließlich Edge-Computing, föderiertes Lernen und Architekturen mit mehreren Standorten.

|   #    | Beschreibung                                                                                                                                                                                                                               | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.12.1 | Überprüfen Sie, dass Edge-KI-Geräte sich gegenüber der zentralen Infrastruktur durch gegenseitige TLS-Authentifizierung authentifizieren, wobei Gerätezertifikate gemäß der Organisationspolitik zum Zertifikatsmanagement rotiert werden. |   2   |  D/V  |
| 4.12.2 | Überprüfen Sie, ob Edge-Geräte Secure Boot mit verifizierten Signaturen implementieren und einen Rollback-Schutz bieten, der Firmware-Downgrade-Angriffe verhindert.                                                                       |   2   |  D/V  |
| 4.12.3 | Überprüfen Sie, ob die verteilte KI-Koordination byzantinische Fehlertoleranz-Konsensalgorithmen mit Teilnehmervalidierung und Erkennung böswilliger Knoten verwendet.                                                                     |   3   |  D/V  |
| 4.12.4 | Stellen Sie sicher, dass die Edge-to-Cloud-Kommunikation Bandbreiten-Drosselung, Datenkompression und Offline-Betriebsfunktionen mit sicherem lokalem Speicher umfasst.                                                                    |   3   |  D/V  |

---

## C4.13 Sicherheit von Multi-Cloud- und Hybrid-Infrastrukturen

Sichere KI-Workloads über mehrere Cloud-Anbieter hinweg und hybride Cloud- und On-Premises-Bereitstellungen.

|   #    | Beschreibung                                                                                                                                                                                                                            | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.13.1 | Stellen Sie sicher, dass Multi-Cloud-KI-Bereitstellungen eine cloud-agnostische Identitätsföderation (OIDC, SAML) mit zentralisiertem Richtlinienmanagement über Anbieter hinweg verwenden.                                             |   2   |  D/V  |
| 4.13.2 | Vergewissern Sie sich, dass bei der cloud-übergreifenden Datenübertragung eine Ende-zu-Ende-Verschlüsselung mit vom Kunden verwalteten Schlüsseln verwendet wird und dass Datenresidenzkontrollen je Rechtsordnung durchgesetzt werden. |   2   |  D/V  |
| 4.13.3 | Überprüfen Sie, ob hybride Cloud-KI-Workloads konsistente Sicherheitsrichtlinien über On-Premises- und Cloud-Umgebungen hinweg implementieren, mit einheitlicher Überwachung und Alarmierung.                                           |   2   |  D/V  |
| 4.13.4 | Stellen Sie sicher, dass Maßnahmen zur Verhinderung von Cloud-Anbieter-Lock-in portables Infrastructure-as-Code, standardisierte APIs und Datenexportfunktionen mit Formatkonvertierungstools umfassen.                                 |   3   |   V   |
| 4.13.5 | Stellen Sie sicher, dass die Kostenoptimierung in Multi-Cloud-Umgebungen Sicherheitskontrollen umfasst, die eine Ressourcenverbreitung verhindern, sowie unautorisierte Datenübertragungskosten zwischen Clouds verhindern.             |   3   |   V   |

---

## C4.14 Infrastrukturautomatisierung & GitOps-Sicherheit

Sichern Sie Infrastruktur-Automatisierungspipelines und GitOps-Workflows für das KI-Infrastrukturmanagement.

|   #    | Beschreibung                                                                                                                                                                                                                                    | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.14.1 | Stellen Sie sicher, dass GitOps-Repositories signierte Commits mit GPG-Schlüsseln erfordern und Branch-Schutzregeln vorsehen, die das direkte Pushen auf Hauptzweige verhindern.                                                                |   2   |  D/V  |
| 4.14.2 | Stellen Sie sicher, dass die Infrastrukturautomatisierung eine Drift-Erkennung mit automatisierter Behebung und Rollback-Funktionen umfasst, die gemäß den organisatorischen Reaktionsanforderungen bei unbefugten Änderungen ausgelöst werden. |   2   |  D/V  |
| 4.14.3 | Stellen Sie sicher, dass die automatisierte Infrastruktur-Bereitstellung eine Validierung der Sicherheitsrichtlinien umfasst, die bei nicht konformen Konfigurationen die Bereitstellung blockiert.                                             |   2   |  D/V  |
| 4.14.4 | Stellen Sie sicher, dass Geheimnisse der Infrastrukturautomatisierung durch externe Secrets-Operatoren (External Secrets Operator, Bank-Vaults) mit automatischer Rotation verwaltet werden.                                                    |   2   |  D/V  |
| 4.14.5 | Stellen Sie sicher, dass die selbstheilende Infrastruktur die Sicherheitsereigniskorrelation mit automatisierter Vorfallreaktion und Benachrichtigungsabläufen für Stakeholder umfasst.                                                         |   3   |   V   |

---

## C4.15 Quantenresistente Infrastruktur-Sicherheit

Bereiten Sie eine KI-Infrastruktur auf Bedrohungen durch Quantencomputing vor, indem Sie Post-Quanten-Kryptografie und quantenresistente Protokolle einsetzen.

|   #    | Beschreibung                                                                                                                                                                                                         | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Stellen Sie sicher, dass die KI-Infrastruktur NIST-anerkannte postquantenkryptografische Algorithmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) für Schlüsselaustausch und digitale Signaturen implementiert.    |   3   |  D/V  |
| 4.15.2 | Überprüfen Sie, dass QKD-Systeme für die hochsichere KI-Kommunikation mit quantensicheren Schlüsselverwaltungsprotokollen implementiert sind.                                                                        |   3   |  D/V  |
| 4.15.3 | Überprüfen Sie, ob Rahmenwerke kryptografischer Agilität eine schnelle Migration zu neuen Post-Quanten-Algorithmen mit automatisierter Zertifikats- und Schlüsselrotation ermöglichen.                               |   3   |  D/V  |
| 4.15.4 | Stellen Sie sicher, dass die Quantenbedrohungsmodellierung die Verwundbarkeit der KI-Infrastruktur gegenüber Quantenangriffen bewertet und dass dokumentierte Migrationszeitpläne sowie Risikobewertungen vorliegen. |   3   |   V   |
| 4.15.5 | Verifizieren Sie, dass hybride klassische-quantische kryptografische Systeme während der Quantenübergangsphase eine Verteidigung in der Tiefe bieten und Leistungsüberwachung implementieren.                        |   3   |  D/V  |

---

## C4.16 Vertrauliches Computing & Sichere Enklaven

Schützen Sie KI-Workloads und Modellgewichte durch hardwarebasierte vertrauenswürdige Ausführungsumgebungen und Technologien des vertraulichen Computings.

|   #    | Beschreibung                                                                                                                                                                                 | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.16.1 | Stellen Sie sicher, dass empfindliche KI-Modelle innerhalb von Intel SGX-Enklaven, AMD SEV-SNP oder ARM TrustZone mit verschlüsseltem Speicher und Attestierungsprüfung ausgeführt werden.   |   3   |  D/V  |
| 4.16.2 | Stellen Sie sicher, dass vertrauliche Container (Kata Containers, gVisor mit vertraulichem Computing) KI-Arbeitslasten mit hardwaregestützter Speicherverschlüsselung isolieren.             |   3   |  D/V  |
| 4.16.3 | Stellen Sie sicher, dass Remote-Attestation die Integrität der Enklave überprüft, bevor KI-Modelle mit kryptografischem Nachweis der Authentizität einer Ausführungsumgebung geladen werden. |   3   |  D/V  |
| 4.16.4 | Überprüfen Sie, ob vertrauliche KI-Inferenzdienste eine Modellextraktion durch verschlüsselte Berechnungen mit versiegelten Modellgewichten und geschützter Ausführung verhindern.           |   3   |  D/V  |
| 4.16.5 | Überprüfen Sie, ob die Orchestrierung der Trusted Execution Environment (TEE) den Lebenszyklus sicherer Enklaven mit Remote-Attestation und verschlüsselten Kommunikationskanälen verwaltet. |   3   |  D/V  |
| 4.16.6 | Verifizieren Sie, dass sichere Mehrparteienberechnung (SMPC) kooperatives KI-Training ermöglicht, ohne einzelne Datensätze oder Modellparameter offenzulegen.                                |   3   |  D/V  |

---

## C4.17 Infrastruktur für Nullwissen

Implementieren Sie Null-Wissens-Beweissysteme für datenschutzfreundliche KI-Verifikation und Authentifizierung, ohne sensible Informationen offenzulegen.

|   #    | Beschreibung                                                                                                                                                                                     | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.17.1 | Verifizieren Sie, dass Null-Wissens-Beweise (ZK-SNARKs, ZK-STARKs) die Integrität des KI-Modells und die Provenienz des Trainings belegen, ohne Modellgewichte oder Trainingsdaten offenzulegen. |   3   |  D/V  |
| 4.17.2 | Überprüfen Sie, ob ZK-basierte Authentifizierungssysteme eine datenschutzfreundliche Benutzerauthentifizierung für KI-Dienste ermöglichen, ohne identitätsbezogene Informationen offenzulegen.   |   3   |  D/V  |
| 4.17.3 | Überprüfen Sie, ob Private Set Intersection (PSI)-Protokolle einen sicheren Datenabgleich für föderierte KI ermöglichen, ohne einzelne Datensätze offenzulegen.                                  |   3   |  D/V  |
| 4.17.4 | Bestätigen Sie, dass Null-Wissens-Maschinelles Lernen (ZKML)-Systeme verifizierbare KI-Inferenzen mit kryptografischem Beweis der korrekten Berechnung ermöglichen.                              |   3   |  D/V  |
| 4.17.5 | Verifizieren Sie, dass ZK-rollups skalierbare datenschutzfreundliche KI-Transaktionsverarbeitung mit Batch-Verifikation und reduziertem Rechenaufwand bieten.                                    |   3   |  D/V  |

---

## C4.18 Verhinderung von Seitenkanalangriffen

Schützen Sie die KI-Infrastruktur vor Timing-, Leistungs-, elektromagnetischen und Cache-basierten Seitenkanalangriffen, die sensible Informationen preisgeben könnten.

|   #    | Beschreibung                                                                                                                                                                        | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.18.1 | Überprüfen Sie, dass die Inferenzzeit der KI durch Algorithmen mit konstanter Laufzeit und Padding normalisiert wird, um Timing-basierte Modellextraktionsangriffe zu verhindern.   |   3   |  D/V  |
| 4.18.2 | Überprüfen Sie, dass der Schutz gegen Stromverbrauchsanalyse Rauschinjektion, Netzspannungsfilterung und randomisierte Ausführungsabläufe für KI-Hardware umfasst.                  |   3   |  D/V  |
| 4.18.3 | Überprüfen Sie, ob Cache-basierte Gegenmaßnahmen gegen Seitenkanäle Cache-Partitionierung, Randomisierung und Flush-Instruktionen verwenden, um Informationsleckagen zu verhindern. |   3   |  D/V  |
| 4.18.4 | Überprüfen Sie, ob der Schutz vor elektromagnetischer Abstrahlung Abschirmung, Signalfilterung und randomisierte Verarbeitung umfasst, um TEMPEST-ähnliche Angriffe zu verhindern.  |   3   |  D/V  |
| 4.18.5 | Überprüfen Sie, ob mikroarchitektonische Seitenkanal-Schutzmaßnahmen spekulative Ausführungskontrollen und Obfuskation von Speicherzugriffs-Mustern umfassen.                       |   3   |  D/V  |

---

## C4.19 Neuromorphische & spezialisierte KI-Hardware-Sicherheit

Schützen Sie aufkommende KI-Hardware-Architekturen, einschließlich neuromorpher Chips, FPGAs, kundenspezifischer ASICs und optischer Rechensysteme.

|   #    | Beschreibung                                                                                                                                                                                     | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 4.19.1 | Überprüfen Sie, ob die Sicherheit neuromorpher Chips die Verschlüsselung von Spikemustern, den Schutz synaptischer Gewichte und die hardwarebasierte Validierung von Lernregeln umfasst.         |   3   |  D/V  |
| 4.19.2 | Stellen Sie sicher, dass FPGA-basierte KI-Beschleuniger Bitstream-Verschlüsselung, Anti-Tamper-Mechanismen und sicheres Laden von Konfigurationen mit authentifizierten Updates implementieren.  |   3   |  D/V  |
| 4.19.3 | Stellen Sie sicher, dass die kundenspezifische ASIC-Sicherheit On-Chip-Sicherheitsprozessoren, Hardware-Wurzel des Vertrauens und sicheren Schlüsselspeicher mit Manipulationsdetektion umfasst. |   3   |  D/V  |
| 4.19.4 | Überprüfen Sie, ob optische Rechensysteme quantensichere optische Verschlüsselung, sichere photonische Schaltung und geschützte optische Signalverarbeitung implementieren.                      |   3   |  D/V  |
| 4.19.5 | Stellen Sie sicher, dass hybride Analog-Digital-Chips für KI sichere analoge Berechnungen, geschützten Gewichtsspeicher und authentifizierte Analog-zu-Digital-Wandlung enthalten.               |   3   |  D/V  |

---

## C4.20 Datenschutzfreundliche Recheninfrastruktur

Implementieren Sie Infrastrukturkontrollen für datenschutzkonforme Berechnungen, um sensible Daten während der KI-Verarbeitung und KI-Analyse zu schützen.

|   #    | Beschreibung                                                                                                                                                                                                                    | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.20.1 | Stellen Sie sicher, dass die Infrastruktur für homomorphe Verschlüsselung verschlüsselte Berechnungen auf sensiblen KI-Arbeitslasten ermöglicht und kryptografische Integritätsprüfung sowie Leistungsüberwachung bietet.       |   3   |  D/V  |
| 4.20.2 | Überprüfen Sie, ob Private Information Retrieval-Systeme Datenbankabfragen ermöglichen, ohne Abfragemuster offenzulegen, indem sie die Zugriffsmuster kryptografisch schützen.                                                  |   3   |  D/V  |
| 4.20.3 | Überprüfen Sie, ob sichere Mehrparteienberechnungsverfahren eine datenschutzfreundliche KI-Inferenz ermöglichen, ohne einzelne Eingaben oder Zwischenberechnungen offenzulegen.                                                 |   3   |  D/V  |
| 4.20.4 | Stellen Sie sicher, dass datenschutzfreundliche Schlüsselverwaltung verteilte Schlüsselgenerierung, Schwellenkryptographie und sichere Schlüsselrotation mit hardwaregestütztem Schutz umfasst.                                 |   3   |  D/V  |
| 4.20.5 | Stellen Sie sicher, dass die Rechenleistung bei datenschutzfreundlichen Berechnungen durch Batch-Verarbeitung, Caching und Hardwarebeschleunigung optimiert wird, während kryptografische Sicherheitsgarantien gewahrt bleiben. |   3   |  D/V  |

---

## C4.15 Agent Framework Cloud-Integration-Sicherheit und hybride Bereitstellung

Sicherheitskontrollen für Cloud-integrierte Agenten-Frameworks mit hybriden On-Premises-/Cloud-Architekturen.

|   #    | Beschreibung                                                                                                                                                   | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 4.15.1 | Überprüfen Sie, ob die Cloud-Speicherintegration eine Ende-zu-Ende-Verschlüsselung mit agentengesteuerter Schlüsselverwaltung verwendet.                       |   1   |  D/V  |
| 4.15.2 | Stellen Sie sicher, dass die Sicherheitsgrenzen der hybriden Bereitstellung klar definiert sind und dass verschlüsselte Kommunikationskanäle verwendet werden. |   2   |  D/V  |
| 4.15.3 | Stellen Sie sicher, dass der Zugriff auf Cloud-Ressourcen eine Zero-Trust-Verifizierung mit kontinuierlicher Authentifizierung umfasst.                        |   2   |  D/V  |
| 4.15.4 | Überprüfen Sie, ob die Anforderungen an die Datenresidenz durch kryptografische Attestierung der Speicherorte durchgesetzt werden.                             |   3   |  D/V  |
| 4.15.5 | Überprüfen Sie, ob die Sicherheitsbewertungen von Cloud-Anbietern eine agentenspezifische Bedrohungsmodellierung und Risikobewertung umfassen.                 |   3   |  D/V  |

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

