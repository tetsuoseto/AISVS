# C6 Lieferkettensicherheit für Modelle, Frameworks & Daten

## Steuerungsziel

KI-Lieferkettenangriffe nutzen Drittanbieter-Modelle, Frameworks oder Datensätze aus, um Hintertüren, Verzerrungen oder ausnutzbaren Code einzufügen. Diese Kontrollen bieten eine durchgängige Herkunftsnachverfolgung, Schwachstellenmanagement und Überwachung, um den gesamten Modelllebenszyklus zu schützen.

---

## C6.1 Überprüfung und Herkunft vortrainierter Modelle

Bewerten und authentifizieren Sie Herkunft, Lizenzen und verborgene Verhaltensweisen von Modellen Dritter, bevor Sie eine Feinabstimmung oder Bereitstellung durchführen.

|   #   | Beschreibung                                                                                                                                                                     | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.1.1 | Stellen Sie sicher, dass jedes Drittanbieter-Modellartefakt eine signierte Herkunftsaufzeichnung enthält, die das Quell-Repository und den Commit-Hash identifiziert.            |   1   |  D/V  |
| 6.1.2 | Überprüfen Sie, ob Modelle vor dem Import mithilfe automatisierter Werkzeuge auf bösartige Schichten oder Trojaner-Auslöser gescannt werden.                                     |   1   |  D/V  |
| 6.1.3 | Überprüfen Sie, ob das Transfer-Learning-Feinabstimmung einer adversarialen Evaluation standhält, um verborgene Verhaltensweisen zu erkennen.                                    |   2   |   D   |
| 6.1.4 | Stellen Sie sicher, dass Modelllizenzen, Exportkontrollkennzeichnungen und Angaben zur Datenherkunft in einem ML-BOM-Eintrag erfasst sind.                                       |   2   |   V   |
| 6.1.5 | Stellen Sie sicher, dass Hochrisikomodelle (öffentlich hochgeladene Gewichte, nicht verifizierte Ersteller) bis zur menschlichen Überprüfung und Freigabe in Quarantäne bleiben. |   3   |  D/V  |

---

## C6.2 Framework- und Bibliotheksscanning

Scannen Sie kontinuierlich ML-Frameworks und Bibliotheken nach CVEs und bösartigem Code, um den Laufzeit-Stack sicher zu halten.

|   #   | Beschreibung                                                                                                                                            | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.2.1 | Stellen Sie sicher, dass CI-Pipelines Abhängigkeits-Scanner auf AI-Frameworks und kritische Bibliotheken ausführen.                                     |   1   |  D/V  |
| 6.2.2 | Überprüfen Sie, dass kritische Schwachstellen (CVSS ≥ 7.0) die Freigabe von Produktionsabbildern verhindern.                                            |   1   |  D/V  |
| 6.2.3 | Überprüfen Sie, ob die statische Codeanalyse bei geforkten oder eingebundenen ML-Bibliotheken ausgeführt wird.                                          |   2   |   D   |
| 6.2.4 | Stellen Sie sicher, dass Framework-Upgrade-Vorschläge eine Bewertung der Sicherheitsauswirkungen enthalten, die sich auf öffentliche CVE-Feeds bezieht. |   2   |   V   |
| 6.2.5 | Stellen Sie sicher, dass Laufzeitsensoren bei unerwarteten dynamischen Bibliotheksladungen, die von der signierten SBOM abweichen, Alarm schlagen.      |   3   |   V   |

---

## C6.3 Abhängigkeitsverankerung und -verifizierung

Fixieren Sie jede Abhängigkeit auf unveränderliche Digests und reproduzieren Sie Builds, um identische, manipulationssichere Artefakte zu garantieren.

|   #   | Beschreibung                                                                                                                                | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.3.1 | Überprüfen Sie, ob alle Paketmanager Versionssperrung durch Lockfiles erzwingen.                                                            |   1   |  D/V  |
| 6.3.2 | Stellen Sie sicher, dass unveränderliche Digests anstelle von veränderlichen Tags in Containerreferenzen verwendet werden.                  |   1   |  D/V  |
| 6.3.3 | Überprüfen Sie, dass Reproduzierbarkeitsprüfungen Hashes über CI-Durchläufe hinweg vergleichen, um identische Ausgaben sicherzustellen.     |   2   |   D   |
| 6.3.4 | Überprüfen Sie, ob Build-Bestätigungen für 18 Monate zur Prüfspuraufzeichnung gespeichert werden.                                           |   2   |   V   |
| 6.3.5 | Überprüfen Sie, ob abgelaufene Abhängigkeiten automatisierte Pull Requests auslösen, um gepinnte Versionen zu aktualisieren oder zu forken. |   3   |   D   |

---

## C6.4 Durchsetzung vertrauenswürdiger Quellen

Erlauben Sie den Download von Artefakten nur von kryptografisch verifizierten, von der Organisation genehmigten Quellen und blockieren Sie alles andere.

|   #   | Beschreibung                                                                                                                                            | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.4.1 | Stellen Sie sicher, dass Modellgewichte, Datensätze und Container nur von genehmigten Domains oder internen Registern heruntergeladen werden.           |   1   |  D/V  |
| 6.4.2 | Stellen Sie sicher, dass Sigstore/Cosign-Signaturen die Identität des Herausgebers überprüfen, bevor Artefakte lokal zwischengespeichert werden.        |   1   |  D/V  |
| 6.4.3 | Überprüfen Sie, dass Egress-Proxys nicht authentifizierte Artefakt-Downloads blockieren, um die Richtlinie für vertrauenswürdige Quellen durchzusetzen. |   2   |   D   |
| 6.4.4 | Überprüfen Sie, ob die Repository-Zulassungslisten vierteljährlich mit Nachweisen der geschäftlichen Rechtfertigung für jeden Eintrag überprüft werden. |   2   |   V   |
| 6.4.5 | Überprüfen Sie, ob Richtlinienverstöße zur Isolierung von Artefakten und zum Rücksetzen abhängiger Pipeline-Ausführungen führen.                        |   3   |   V   |

---

## C6.5 Risikobewertung von Drittanbieter-Datensätzen

Bewerten Sie externe Datensätze auf Manipulation, Verzerrung und rechtliche Konformität und überwachen Sie diese während ihres gesamten Lebenszyklus.

|   #   | Beschreibung                                                                                                                                          | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.5.1 | Stellen Sie sicher, dass externe Datensätze einer Risikoanalyse auf Vergiftung unterzogen werden (z. B. Daten-Fingerprinting, Ausreißererkennung).    |   1   |  D/V  |
| 6.5.2 | Stellen Sie sicher, dass Bias-Metriken (demografische Parität, Chancengleichheit) vor der Genehmigung des Datensatzes berechnet werden.               |   1   |   D   |
| 6.5.3 | Überprüfen Sie, dass Herkunft und Lizenzbedingungen für Datensätze in ML‑BOM-Einträgen erfasst sind.                                                  |   2   |   V   |
| 6.5.4 | Stellen Sie sicher, dass die periodische Überwachung Drift oder Korruption in gehosteten Datensätzen erkennt.                                         |   2   |   V   |
| 6.5.5 | Stellen Sie sicher, dass unzulässige Inhalte (Urheberrecht, personenbezogene Daten) vor dem Training durch automatisiertes Scrubbing entfernt werden. |   3   |   D   |

---

## C6.6 Überwachung von Lieferkettenangriffen

Erkennen Sie Lieferkettenbedrohungen frühzeitig durch CVE-Feeds, Audit-Log-Analysen und Red-Team-Simulationen.

|   #   | Beschreibung                                                                                                                                      | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.6.1 | Überprüfen Sie, dass CI/CD-Auditprotokolle an SIEM-Erkennungen für anomale Paketabrufe oder manipulierte Build-Schritte übertragen werden.        |   1   |   V   |
| 6.6.2 | Stellen Sie sicher, dass Incident-Response-Playbooks Rücksetzverfahren für kompromittierte Modelle oder Bibliotheken enthalten.                   |   2   |   D   |
| 6.6.3 | Überprüfen Sie, ob die Bedrohungs‑Intel‑Anreicherung ML‑spezifische Indikatoren (z. B. Modellvergiftungs-IoCs) bei der Alarm‑Triage kennzeichnet. |   3   |   V   |

---

## C6.7 ML‑BOM für Modellartefakte

Erstellen und signieren Sie detaillierte, ML-spezifische SBOMs (ML-BOMs), damit nachgelagerte Nutzer die Integrität der Komponenten zum Zeitpunkt der Bereitstellung überprüfen können.

|   #   | Beschreibung                                                                                                                                          | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.7.1 | Stellen Sie sicher, dass jedes Modell-Artefakt eine ML‑BOM veröffentlicht, die Datensätze, Gewichte, Hyperparameter und Lizenzen auflistet.           |   1   |  D/V  |
| 6.7.2 | Stellen Sie sicher, dass die ML-BOM-Erstellung und die Cosign-Unterzeichnung im CI automatisiert sind und für den Merge erforderlich sind.            |   1   |  D/V  |
| 6.7.3 | Überprüfen Sie, dass die ML-BOM-Vollständigkeitsprüfungen den Build fehlschlagen lassen, wenn Metadaten einer Komponente (Hash, Lizenz) fehlen.       |   2   |   D   |
| 6.7.4 | Überprüfen Sie, ob nachgelagerte Verbraucher ML-BOMs über die API abfragen können, um importierte Modelle zum Bereitstellungszeitpunkt zu validieren. |   2   |   V   |
| 6.7.5 | Stellen Sie sicher, dass ML‑BOMs versioniert und verglichen werden, um unautorisierte Änderungen zu erkennen.                                         |   3   |   V   |

---

## Literaturverzeichnis

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

