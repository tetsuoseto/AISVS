# C6 Lieferkettensicherheit für Modelle, Frameworks und Daten

## Kontrollziel

KI-Lieferkettenangriffe nutzen Drittanbieter-Modelle, -Frameworks oder -Datensätze aus, um Hintertüren, Verzerrungen oder ausnutzbaren Code einzuschleusen. Diese Kontrollen bieten eine durchgängige Herkunftsnachverfolgung, Schwachstellenmanagement und Überwachung, um den gesamten Modellentwicklungszyklus zu schützen.

---

## C6.1 Überprüfung und Herkunft vortrainierter Modelle

Bewerten und authentifizieren Sie die Herkunft, Lizenzen und verborgenen Verhaltensweisen von Modellen Dritter, bevor Sie Feinabstimmungen vornehmen oder diese bereitstellen.

|   #   | Beschreibung                                                                                                                                                                     | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.1.1 | Stellen Sie sicher, dass jedes Drittanbieter-Modellartefakt einen signierten Herkunftsnachweis enthält, der das Quell-Repository und den Commit-Hash identifiziert.              |   1   |  D/V  |
| 6.1.2 | Stellen Sie sicher, dass Modelle vor dem Import mit automatisierten Werkzeugen auf bösartige Schichten oder Trojanische Auslöser gescannt werden.                                |   1   |  D/V  |
| 6.1.3 | Überprüfen Sie, ob Transferlernen-Feinabstimmungen eine adversariale Bewertung bestehen, um verborgene Verhaltensweisen zu erkennen.                                             |   2   |   D   |
| 6.1.4 | Stellen Sie sicher, dass Modelllizenzen, Exportkontrollkennzeichnungen und Angaben zur Datenherkunft in einem ML-BOM-Eintrag aufgezeichnet sind.                                 |   2   |   V   |
| 6.1.5 | Stellen Sie sicher, dass Hochrisikomodelle (öffentlich hochgeladene Gewichte, nicht verifizierte Ersteller) bis zur menschlichen Überprüfung und Freigabe in Quarantäne bleiben. |   3   |  D/V  |

---

## C6.2 Framework- und Bibliotheksscanning

Scannen Sie kontinuierlich ML-Frameworks und -Bibliotheken auf CVEs und bösartigen Code, um den Laufzeit-Stack sicher zu halten.

|   #   | Beschreibung                                                                                                                                      | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.2.1 | Überprüfen Sie, dass CI-Pipelines Dependency-Scanner auf KI-Frameworks und kritische Bibliotheken ausführen.                                      |   1   |  D/V  |
| 6.2.2 | Überprüfen Sie, dass kritische Schwachstellen (CVSS ≥ 7,0) die Freigabe für Produktions-Images blockieren.                                        |   1   |  D/V  |
| 6.2.3 | Überprüfen Sie, ob die statische Codeanalyse bei geforkten oder eingebundenen ML-Bibliotheken ausgeführt wird.                                    |   2   |   D   |
| 6.2.4 | Stellen Sie sicher, dass Framework-Upgrade-Vorschläge eine Sicherheitsauswirkungsbewertung enthalten, die sich auf öffentliche CVE-Feeds bezieht. |   2   |   V   |
| 6.2.5 | Überprüfen Sie, ob Laufzeitsensoren bei unerwarteten dynamischen Bibliotheksläufen alarmieren, die von der signierten SBOM abweichen.             |   3   |   V   |

---

## C6.3 Abhängigkeits-Pinning und -Verifizierung

Fixieren Sie jede Abhängigkeit auf unveränderliche Digests und reproduzieren Sie Builds, um identische, manipulationsfreie Artefakte zu garantieren.

|   #   | Beschreibung                                                                                                                                   | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.3.1 | Überprüfen Sie, ob alle Paketmanager die Versionssperrung über Lockfiles erzwingen.                                                            |   1   |  D/V  |
| 6.3.2 | Überprüfen Sie, dass unveränderliche Digests anstelle von veränderlichen Tags in Container-Referenzen verwendet werden.                        |   1   |  D/V  |
| 6.3.3 | Überprüfen Sie, dass reproduzierbare Build-Checks Hashes über CI-Durchläufe hinweg vergleichen, um identische Ausgaben sicherzustellen.        |   2   |   D   |
| 6.3.4 | Überprüfen Sie, dass Build-Atteste für 18 Monate zur Audit-Rückverfolgbarkeit gespeichert werden.                                              |   2   |   V   |
| 6.3.5 | Überprüfen Sie, ob abgelaufene Abhängigkeiten automatisierte Pull Requests auslösen, um angeheftete Versionen zu aktualisieren oder zu forken. |   3   |   D   |

---

## C6.4 Durchsetzung vertrauenswürdiger Quellen

Erlauben Sie den Download von Artefakten nur von kryptographisch verifizierten, von der Organisation genehmigten Quellen und blockieren Sie alle anderen.

|   #   | Beschreibung                                                                                                                                           | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 6.4.1 | Stellen Sie sicher, dass Modellgewichte, Datensätze und Container nur von genehmigten Domains oder internen Registrierungen heruntergeladen werden.    |   1   |  D/V  |
| 6.4.2 | Stellen Sie sicher, dass Sigstore/Cosign-Signaturen die Identität des Herausgebers überprüfen, bevor Artefakte lokal zwischengespeichert werden.       |   1   |  D/V  |
| 6.4.3 | Überprüfen Sie, ob Egress-Proxys nicht authentifizierte Artefakt-Downloads blockieren, um die Richtlinie für vertrauenswürdige Quellen durchzusetzen.  |   2   |   D   |
| 6.4.4 | Verifizieren Sie, dass Repository-Allow-Lists vierteljährlich überprüft werden, mit Nachweisen für die geschäftliche Rechtfertigung für jeden Eintrag. |   2   |   V   |
| 6.4.5 | Überprüfen Sie, ob Richtlinienverstöße zur Quarantäne von Artefakten und zum Zurücksetzen abhängiger Pipeline-Läufe führen.                            |   3   |   V   |

---

## C6.5 Bewertung von Risiken bei Datensätzen Dritter

Bewerten Sie externe Datensätze auf Vergiftung, Verzerrung und rechtliche Konformität und überwachen Sie diese während ihres gesamten Lebenszyklus.

|   #   | Beschreibung                                                                                                                                             | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.5.1 | Stellen Sie sicher, dass externe Datensätze einer Bewertung des Vergiftungsrisikos unterzogen werden (z. B. Daten-Fingerprinting, Ausreißererkennung).   |   1   |  D/V  |
| 6.5.2 | Verifizieren Sie, dass Bias-Metriken (demografische Parität, Chancengleichheit) vor der Genehmigung des Datensatzes berechnet werden.                    |   1   |   D   |
| 6.5.3 | Verifizieren Sie, dass Herkunft und Lizenzbedingungen für Datensätze in ML-BOM-Einträgen erfasst werden.                                                 |   2   |   V   |
| 6.5.4 | Stellen Sie sicher, dass die regelmäßige Überwachung Verschiebungen oder Beschädigungen in gehosteten Datensätzen erkennt.                               |   2   |   V   |
| 6.5.5 | Stellen Sie sicher, dass nicht erlaubte Inhalte (Urheberrecht, personenbezogene Daten) vor dem Training durch automatisiertes Entfernen entfernt werden. |   3   |   D   |

---

## C6.6 Überwachung von Lieferkettenangriffen

Erkennen Sie Bedrohungen in der Lieferkette frühzeitig durch CVE-Feeds, Audit-Protokoll-Analysen und Red-Team-Simulationen.

|   #   | Beschreibung                                                                                                                                                 | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 6.6.1 | Überprüfen Sie, dass CI/CD-Auditprotokolle an SIEM-Erkennungen für anomale Paketabrufe oder manipulierte Build-Schritte übertragen werden.                   |   1   |   V   |
| 6.6.2 | Überprüfen Sie, ob die Incident-Response-Playbooks Rollback-Verfahren für kompromittierte Modelle oder Bibliotheken enthalten.                               |   2   |   D   |
| 6.6.3 | Verifizieren Sie, dass die Bedrohungs-Intelligence-Anreicherung ML-spezifische Indikatoren (z. B. model-poisoning IoCs) bei der Alarmbewertung kennzeichnet. |   3   |   V   |

---

## C6.7 ML‑BOM für Modellartefakte

Erstellen und signieren Sie detaillierte, auf maschinelles Lernen spezialisierte SBOMs (ML‑BOMs), damit nachgelagerte Verbraucher die Integrität der Komponenten zur Bereitstellungszeit überprüfen können.

|   #   | Beschreibung                                                                                                                                                   | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.7.1 | Stellen Sie sicher, dass jedes Modellartefakt eine ML-BOM veröffentlicht, die Datensätze, Gewichte, Hyperparameter und Lizenzen auflistet.                     |   1   |  D/V  |
| 6.7.2 | Verifizieren Sie, dass die ML‑BOM-Erstellung und die Cosign-Signierung in der CI automatisiert sind und für das Zusammenführen erforderlich sind.              |   1   |  D/V  |
| 6.7.3 | Überprüfen Sie, dass die Vollständigkeitsprüfungen von ML‑BOM den Build fehlschlagen lassen, wenn Metadaten eines beliebigen Components (Hash, Lizenz) fehlen. |   2   |   D   |
| 6.7.4 | Überprüfen Sie, ob nachgelagerte Verbraucher ML-BOMs über die API abfragen können, um importierte Modelle zum Bereitstellungszeitpunkt zu validieren.          |   2   |   V   |
| 6.7.5 | Stellen Sie sicher, dass ML‑BOMs versioniert und verglichen werden, um unautorisierte Änderungen zu erkennen.                                                  |   3   |   V   |

---

## Referenzen

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

