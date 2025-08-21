# C1 Schulungsdaten-Governance & Bias-Management

## Steuerungsziel

Trainingsdaten müssen so beschafft, verarbeitet und gepflegt werden, dass Herkunft, Sicherheit, Qualität und Fairness erhalten bleiben. Dies erfüllt gesetzliche Verpflichtungen und verringert Risiken von Verzerrungen, Manipulationen oder Datenschutzverletzungen, die während des Trainings auftreten und den gesamten KI-Lebenszyklus beeinflussen könnten.

---

## C1.1 Herkunft der Trainingsdaten

Führen Sie ein überprüfbares Inventar aller Datensätze, akzeptieren Sie nur vertrauenswürdige Quellen und protokollieren Sie jede Änderung zur Nachvollziehbarkeit.

|   #   | Beschreibung                                                                                                                                                                                              | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.1.1 | Stellen Sie sicher, dass ein aktuelles Inventar jeder Trainingsdatenquelle (Herkunft, Verwalter/Eigentümer, Lizenz, Erfassungsmethode, Nutzungsbeschränkungen und Verarbeitungshistorie) geführt wird.    |   1   |  D/V  |
| 1.1.2 | Stellen Sie sicher, dass die Trainingsdatenprozesse unnötige Merkmale, Attribute oder Felder ausschließen (z. B. nicht verwendete Metadaten, sensible personenbezogene Daten, durchgesickerte Testdaten). |   1   |  D/V  |
| 1.1.3 | Stellen Sie sicher, dass alle Änderungen an Datensätzen einem protokollierten Genehmigungsworkflow unterliegen.                                                                                           |   2   |  D/V  |
| 1.1.4 | Stellen Sie sicher, dass Datensätze oder Teilmengen, sofern möglich, mit Wasserzeichen versehen oder mit Fingerabdrücken gekennzeichnet sind.                                                             |   3   |  D/V  |

---

## C1.2 Sicherheit und Integrität der Trainingsdaten

Beschränken Sie den Zugriff auf Trainingsdaten, verschlüsseln Sie diese im Ruhezustand und während der Übertragung und validieren Sie deren Integrität, um Manipulation, Diebstahl oder Datenvergiftung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                      | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.2.1 | Überprüfen Sie, dass Zugriffskontrollen den Speicher für Trainingsdaten und die Pipelines schützen.                                                                                                               |   1   |  D/V  |
| 1.2.2 | Stellen Sie sicher, dass jeder Zugriff auf Trainingsdaten protokolliert wird, einschließlich Benutzer, Zeitpunkt und Aktion.                                                                                      |   2   |  D/V  |
| 1.2.3 | Stellen Sie sicher, dass Trainingsdatensätze während der Übertragung und im Ruhezustand verschlüsselt sind, unter Verwendung von branchenüblichen kryptografischen Algorithmen und Schlüsselverwaltungspraktiken. |   2   |  D/V  |
| 1.2.4 | Überprüfen Sie, dass kryptographische Hashes oder digitale Signaturen verwendet werden, um die Datenintegrität während der Speicherung und Übertragung von Trainingsdaten sicherzustellen.                        |   2   |  D/V  |
| 1.2.5 | Überprüfen Sie, dass automatisierte Erkennungstechniken angewendet werden, um unbefugte Änderungen oder Beschädigungen der Trainingsdaten zu verhindern.                                                          |   2   |  D/V  |
| 1.2.6 | Stellen Sie sicher, dass veraltete Trainingsdaten sicher gelöscht oder anonymisiert werden.                                                                                                                       |   2   |  D/V  |
| 1.2.7 | Stellen Sie sicher, dass alle Versionen des Trainingsdatensatzes eindeutig identifiziert, unveränderlich gespeichert und auditierbar sind, um Rücksetzungen und forensische Analysen zu unterstützen.             |   3   |  D/V  |

---

## C1.3 Qualität, Integrität und Sicherheit der Trainingsdaten-Kennzeichnung

Schützen Sie Labels und verlangen Sie eine technische Überprüfung für kritische Daten.

|   #   | Beschreibung                                                                                                                                                                                                                       | Ebene | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.3.1 | Überprüfen Sie, ob kryptografische Hashes oder digitale Signaturen auf Label-Artefakte angewendet werden, um deren Integrität und Authentizität zu gewährleisten.                                                                  |   2   |  D/V  |
| 1.3.2 | Stellen Sie sicher, dass Kennzeichnungsoberflächen und -plattformen strenge Zugriffskontrollen durchsetzen, manipulationssichere Prüfprotokolle aller Kennzeichnungsaktivitäten führen und vor unbefugten Modifikationen schützen. |   2   |  D/V  |
| 1.3.3 | Überprüfen Sie, dass sensible Informationen in Bezeichnungen auf Feldebene sowohl im Ruhezustand als auch bei der Übertragung geschwärzt, anonymisiert oder verschlüsselt sind.                                                    |   3   |  D/V  |

---

## C1.4 Qualität und Sicherheit der Trainingsdaten gewährleisten

Kombinieren Sie automatisierte Validierung, manuelle Stichprobenprüfungen und protokollierte Behebung, um die Zuverlässigkeit des Datensatzes zu gewährleisten.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 1.4.1 | Überprüfen Sie, ob automatisierte Tests Formatfehler und Nullwerte bei jedem Import oder jeder bedeutenden Datenumwandlung erfassen.                                                                                                                                                                                                                                                                                                                         |   1   |   D   |
| 1.4.2 | Verifizieren Sie, dass LLM-Trainings- und Fine-Tuning-Pipelines eine Erkennung von Vergiftungen und eine Validierung der Datenintegrität implementieren (z. B. statistische Methoden, Ausreißererkennung, Einbettungsanalyse), um potenzielle Vergiftungsangriffe (z. B. Label-Flipping, Einfügen von Backdoor-Triggern, Rollenwechselbefehle, einflussreiche Instanzangriffe) oder unbeabsichtigte Datenkorruption in den Trainingsdaten zu identifizieren. |   2   |  D/V  |
| 1.4.3 | Stellen Sie sicher, dass geeignete Schutzmaßnahmen wie adversariales Training (unter Verwendung generierter adversarialer Beispiele), Datenaugmentation mit gestörten Eingaben oder robuste Optimierungstechniken implementiert und basierend auf der Risikobewertung für relevante Modelle abgestimmt sind.                                                                                                                                                 |   3   |  D/V  |
| 1.4.4 | Überprüfen Sie, dass automatisch generierte Labels (z. B. durch LLMs oder schwache Überwachung) Schwellenwerte für die Vertrauenswürdigkeit und Konsistenzprüfungen unterliegen, um halluzinierte, irreführende oder Labels mit geringer Vertrauenswürdigkeit zu erkennen.                                                                                                                                                                                   |   2   |  D/V  |
| 1.4.5 | Verifizieren Sie, dass automatisierte Tests bei jeder Datenaufnahme oder signifikanten Datenveränderung Label-Skews erfassen.                                                                                                                                                                                                                                                                                                                                |   3   |   D   |

---

## C1.5 Datenherkunft und Rückverfolgbarkeit

Verfolgen Sie die vollständige Reise jedes einzelnen Datenpunkts von der Quelle bis zur Modelleingabe für Nachvollziehbarkeit und Vorfallreaktion.

|   #   | Beschreibung                                                                                                                                                                                                                                                          | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.5.1 | Stellen Sie sicher, dass die Abstammung jedes einzelnen Datenpunkts, einschließlich aller Transformationen, Augmentierungen und Zusammenführungen, dokumentiert ist und rekonstruiert werden kann.                                                                    |   2   |  D/V  |
| 1.5.2 | Stellen Sie sicher, dass Stammdaten unveränderlich, sicher gespeichert und für Prüfungen zugänglich sind.                                                                                                                                                             |   2   |  D/V  |
| 1.5.3 | Stellen Sie sicher, dass die Rückverfolgbarkeit die über datenschutzfördernde oder generative Techniken erzeugten synthetischen Daten abdeckt und dass alle synthetischen Daten im gesamten Ablauf eindeutig gekennzeichnet und von realen Daten unterscheidbar sind. |   2   |  D/V  |

---

## Literaturverzeichnis

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

