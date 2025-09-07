# C6 Lieferkettensicherheit für Modelle, Frameworks und Daten

## Kontrollziel

KI-Lieferkettenangriffe nutzen Drittanbieter-Modelle, Frameworks oder Datensätze aus, um Hintertüren, Verzerrungen oder ausnutzbaren Code einzubetten. Diese Kontrollen bieten durchgehende Herkunftsnachweise, Schwachstellenmanagement und Überwachung zum Schutz des gesamten Modelllebenszyklus.

---

## C6.1 Überprüfung und Herkunft vortrainierter Modelle

Bewerten und authentifizieren Sie Herkunft, Lizenzen und versteckte Verhaltensweisen von Modellen Dritter, bevor Sie eine Feinabstimmung oder Bereitstellung vornehmen.

|   #   | Beschreibung                                                                                                                                                                                         | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.1.1 | Überprüfen Sie, dass jedes Drittanbieter-Modell-Artefakt eine signierte Herkunftsaufzeichnung enthält, die das Quellrepository und den Commit-Hash identifiziert.                                    |   1    |  D/V  |
| 6.1.2 | Stellen Sie sicher, dass Modelle vor dem Import mit automatisierten Werkzeugen auf bösartige Schichten oder Trojaner-Auslöser gescannt werden.                                                       |   1    |  D/V  |
| 6.1.3 | Stellen Sie sicher, dass Transfer-Learning-Feinabstimmungen die adversariale Bewertung bestehen, um versteckte Verhaltensweisen zu erkennen.                                                         |   2    |   D   |
| 6.1.4 | Stellen Sie sicher, dass Modelllizenzen, Exportkontrollmarkierungen und Datenherkunftserklärungen in einem ML-BOM-Eintrag erfasst werden.                                                            |   2    |   V   |
| 6.1.5 | Stellen Sie sicher, dass Modelle mit hohem Risiko (öffentlich hochgeladene Gewichte, nicht verifizierte Ersteller) bis zur menschlichen Überprüfung und Freigabe weiterhin unter Quarantäne bleiben. |   3    |  D/V  |

---

## C6.2 Framework- und Bibliotheksscanning

Scannen Sie kontinuierlich ML-Frameworks und Bibliotheken nach CVEs und schädlichem Code, um den Laufzeit-Stack sicher zu halten.

|   #   | Beschreibung                                                                                                                                     | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 6.2.1 | Überprüfen Sie, dass CI-Pipelines Abhängigkeits-Scanner für KI-Frameworks und kritische Bibliotheken ausführen.                                  |   1    |  D/V  |
| 6.2.2 | Überprüfen Sie, ob kritische Schwachstellen (CVSS ≥ 7,0) die Freigabe von Produktionsabbildern verhindern.                                       |   1    |  D/V  |
| 6.2.3 | Überprüfen Sie, ob die statische Codeanalyse bei geforkten oder eingebetteten ML-Bibliotheken ausgeführt wird.                                   |   2    |   D   |
| 6.2.4 | Überprüfen Sie, ob Vorschläge für Framework-Upgrades eine Sicherheitsauswirkungsbewertung enthalten, die sich auf öffentliche CVE-Feeds bezieht. |   2    |   V   |
| 6.2.5 | Überprüfen Sie, dass Laufzeitsensoren bei unerwarteten dynamischen Bibliotheksladungen, die von der signierten SBOM abweichen, Alarm schlagen.   |   3    |   V   |

---

## C6.3 Abhängigkeiten Festlegen und Verifizieren

Fixieren Sie jede Abhängigkeit auf unveränderliche Digests und reproduzieren Sie Builds, um identische, manipulationsfreie Artefakte zu garantieren.

|   #   | Beschreibung                                                                                                                                      | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.3.1 | Überprüfen Sie, ob alle Paketmanager Versionsfixierung über Lockfiles durchsetzen.                                                                |   1    |  D/V  |
| 6.3.2 | Überprüfen Sie, dass unveränderliche Digests anstelle von veränderlichen Tags in Containerreferenzen verwendet werden.                            |   1    |  D/V  |
| 6.3.3 | Überprüfen Sie, dass die Reproducible-Build-Prüfungen Hashes über CI-Durchläufe hinweg vergleichen, um identische Ergebnisse sicherzustellen.     |   2    |   D   |
| 6.3.4 | Überprüfen Sie, dass Build-Bescheinigungen für 18 Monate zur Audit-Nachverfolgbarkeit gespeichert werden.                                         |   2    |   V   |
| 6.3.5 | Überprüfen Sie, ob abgelaufene Abhängigkeiten automatisierte Pull Requests auslösen, um aktualisierte oder geforkte feste Versionen zu erstellen. |   3    |   D   |

---

## C6.4 Durchsetzung vertrauenswürdiger Quellen

Erlaube den Download von Artefakten nur von kryptografisch verifizierten, von der Organisation genehmigten Quellen und blockiere alles andere.

|   #   | Beschreibung                                                                                                                                                  | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.4.1 | Stellen Sie sicher, dass Modellgewichte, Datensätze und Container nur von genehmigten Domains oder internen Registern heruntergeladen werden.                 |   1    |  D/V  |
| 6.4.2 | Stellen Sie sicher, dass Sigstore/Cosign-Signaturen die Identität des Herausgebers validieren, bevor Artefakte lokal zwischengespeichert werden.              |   1    |  D/V  |
| 6.4.3 | Überprüfen Sie, ob Auswärtsproxies nicht authentifizierte Artefakt-Downloads blockieren, um die Richtlinie vertrauenswürdiger Quellen durchzusetzen.          |   2    |   D   |
| 6.4.4 | Überprüfen Sie, ob die Repository-Whitelist vierteljährlich überprüft wird und für jeden Eintrag ein Nachweis über die geschäftliche Rechtfertigung vorliegt. |   2    |   V   |
| 6.4.5 | Überprüfen Sie, ob Richtlinienverstöße die Quarantäne von Artefakten und den Rollback abhängiger Pipeline-Ausführungen auslösen.                              |   3    |   V   |

---

## C6.5 Bewertung der Risiken bei Drittanbieter-Datensätzen

Bewerten Sie externe Datensätze auf Vergiftung, Verzerrung und rechtliche Konformität und überwachen Sie diese während ihres gesamten Lebenszyklus.

|   #   | Beschreibung                                                                                                                                              | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.5.1 | Stellen Sie sicher, dass externe Datensätze einer Bewertung des Poisoning-Risikos unterzogen werden (z. B. Daten-Fingerabdruck, Ausreißererkennung).      |   1    |  D/V  |
| 6.5.2 | Stellen Sie sicher, dass Bias-Metriken (demografische Parität, Chancengleichheit) vor der Genehmigung des Datensatzes berechnet werden.                   |   1    |   D   |
| 6.5.3 | Stellen Sie sicher, dass Herkunft und Lizenzbedingungen für Datensätze in ML-BOM-Einträgen erfasst werden.                                                |   2    |   V   |
| 6.5.4 | Überprüfen Sie, ob die regelmäßige Überwachung Verschiebungen oder Korruption in gehosteten Datensätzen erkennt.                                          |   2    |   V   |
| 6.5.5 | Stellen Sie sicher, dass nicht erlaubte Inhalte (Urheberrecht, personenbezogene Daten) vor dem Training durch automatisiertes Bereinigen entfernt werden. |   3    |   D   |

---

## C6.6 Überwachung von Lieferkettenangriffen

Erkennen Sie Lieferkettenbedrohungen frühzeitig durch CVE-Feeds, Audit-Log-Analysen und Red-Team-Simulationen.

|   #   | Beschreibung                                                                                                                                           | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 6.6.1 | Stellen Sie sicher, dass CI/CD-Auditprotokolle an SIEM-Systeme übertragen werden, um anomale Paketabrufe oder manipulierte Build-Schritte zu erkennen. |   1    |   V   |
| 6.6.2 | Überprüfen Sie, ob Vorfallsreaktions-Playbooks Rücksetzverfahren für kompromittierte Modelle oder Bibliotheken enthalten.                              |   2    |   D   |
| 6.6.3 | Überprüfen Sie, ob die Threat‑Intel‑Anreicherung ML‑spezifische Indikatoren (z. B. IoCs für Modellvergiftung) bei der Alarmbearbeitung kennzeichnet.   |   3    |   V   |

---

## C6.7 ML-BOM für Modellartefakte

Erstellen und signieren Sie detaillierte, ML-spezifische SBOMs (ML-BOMs), damit nachgelagerte Anwender die Integrität der Komponenten bei der Bereitstellung überprüfen können.

|   #   | Beschreibung                                                                                                                                       | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 6.7.1 | Stellen Sie sicher, dass jedes Modell-Artefakt eine ML‑BOM veröffentlicht, die Datensätze, Gewichte, Hyperparameter und Lizenzen auflistet.        |   1    |  D/V  |
| 6.7.2 | Stellen Sie sicher, dass die ML-BOM-Erstellung und die Cosign-Signierung im CI automatisiert sind und für das Zusammenführen erforderlich sind.    |   1    |  D/V  |
| 6.7.3 | Überprüfen Sie, dass die Vollständigkeitsprüfungen von ML-BOM den Build abbrechen, wenn Metadaten zu Komponenten (Hash, Lizenz) fehlen.            |   2    |   D   |
| 6.7.4 | Überprüfen Sie, dass nachgelagerte Verbraucher ML-BOMs über die API abfragen können, um importierte Modelle zur Bereitstellungszeit zu validieren. |   2    |   V   |
| 6.7.5 | Stellen Sie sicher, dass ML‑BOMs versioniert und verglichen werden, um unautorisierte Änderungen zu erkennen.                                      |   3    |   V   |

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

