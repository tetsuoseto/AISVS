# C1 Trainingsdatenverwaltung & Bias-Management

## Kontrollziel

Trainingsdaten müssen so beschafft, verarbeitet und gepflegt werden, dass Herkunft, Sicherheit, Qualität und Fairness gewährleistet sind. Dies erfüllt rechtliche Pflichten und verringert das Risiko von Verzerrungen, Manipulationen oder Datenschutzverletzungen, die während des Trainings auftreten und den gesamten KI-Lebenszyklus beeinträchtigen könnten.

---

## C1.1 Herkunft der Trainingsdaten

Führen Sie ein überprüfbares Inventar aller Datensätze, akzeptieren Sie nur vertrauenswürdige Quellen und protokollieren Sie jede Änderung zur Nachvollziehbarkeit.

|   #   | Beschreibung                                                                                                                                                                                                    | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.1.1 | Stellen Sie sicher, dass ein aktuelles Inventar jeder Trainingsdatenquelle (Herkunft, Verantwortlicher/Eigentümer, Lizenz, Erhebungsmethode, Verwendungsbeschränkungen und Verarbeitungshistorie) geführt wird. |   1   |  D/V  |
| 1.1.2 | Stellen Sie sicher, dass die Trainingsdatenprozesse unnötige Merkmale, Attribute oder Felder ausschließen (z. B. ungenutzte Metadaten, sensible personenbezogene Daten, durchgesickerte Testdaten).             |   1   |  D/V  |
| 1.1.3 | Stellen Sie sicher, dass alle Änderungen am Datensatz einem protokollierten Genehmigungsworkflow unterliegen.                                                                                                   |   2   |  D/V  |
| 1.1.4 | Überprüfen Sie, ob Datensätze oder Datensatzuntergruppen dort, wo es möglich ist, mit Wasserzeichen oder Fingerabdrücken versehen sind.                                                                         |   3   |  D/V  |

---

## C1.2 Sicherheit und Integrität der Trainingsdaten

Beschränken Sie den Zugriff auf Trainingsdaten, verschlüsseln Sie diese im Ruhezustand und während der Übertragung und prüfen Sie ihre Integrität, um Manipulation, Diebstahl oder Datenvergiftung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                         | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.2.1 | Stellen Sie sicher, dass Zugriffskontrollen die Speicherung und Pipelines der Trainingsdaten schützen.                                                                                               |   1   |  D/V  |
| 1.2.2 | Stellen Sie sicher, dass jeder Zugriff auf Trainingsdaten protokolliert wird, einschließlich Benutzer, Zeit und Aktion.                                                                              |   2   |  D/V  |
| 1.2.3 | Stellen Sie sicher, dass Trainingsdatensätze während der Übertragung und im Ruhezustand mit branchenüblichen kryptografischen Algorithmen und Schlüsselverwaltungsmethoden verschlüsselt sind.       |   2   |  D/V  |
| 1.2.4 | Überprüfen Sie, ob kryptografische Hashes oder digitale Signaturen verwendet werden, um die Datenintegrität während der Speicherung und Übertragung von Trainingsdaten sicherzustellen.              |   2   |  D/V  |
| 1.2.5 | Stellen Sie sicher, dass automatisierte Erkennungstechniken angewendet werden, um unbefugte Änderungen oder Beschädigungen der Trainingsdaten zu verhindern.                                         |   2   |  D/V  |
| 1.2.6 | Verifizieren Sie, dass veraltete Trainingsdaten sicher gelöscht oder anonymisiert werden.                                                                                                            |   2   |  D/V  |
| 1.2.7 | Stellen Sie sicher, dass alle Versionen des Trainingsdatensatzes eindeutig identifiziert, unveränderlich gespeichert und prüfbar sind, um eine Rücksetzung und forensische Analysen zu unterstützen. |   3   |  D/V  |

---

## C1.3 Qualität, Integrität und Sicherheit der Trainingsdatenkennzeichnung

Schützen Sie Labels und verlangen Sie eine technische Überprüfung für kritische Daten.

|   #   | Beschreibung                                                                                                                                                                                                                          | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.3.1 | Überprüfen Sie, ob kryptografische Hashes oder digitale Signaturen auf Label-Artefakte angewendet werden, um deren Integrität und Authentizität sicherzustellen.                                                                      |   2   |  D/V  |
| 1.3.2 | Stellen Sie sicher, dass Beschriftungsschnittstellen und -plattformen starke Zugriffskontrollen durchsetzen, manipulationssichere Audit-Protokolle aller Beschriftungsaktivitäten führen und Schutz vor unbefugten Änderungen bieten. |   2   |  D/V  |
| 1.3.3 | Überprüfen Sie, ob sensible Informationen in Labels auf Feldebene sowohl im Ruhezustand als auch während der Übertragung geschwärzt, anonymisiert oder verschlüsselt sind.                                                            |   3   |  D/V  |

---

## C1.4 Qualität der Trainingsdaten und Sicherheitsgarantie

Kombinieren Sie automatisierte Validierung, manuelle Stichprobenprüfungen und protokollierte Behebungen, um die Zuverlässigkeit des Datensatzes zu gewährleisten.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 1.4.1 | Stellen Sie sicher, dass automatisierte Tests Formatfehler und Nullwerte bei jeder Datenaufnahme oder bedeutenden Datenumwandlung erfassen.                                                                                                                                                                                                                                                                                                                              |   1   |   D   |
| 1.4.2 | Stellen Sie sicher, dass LLM-Trainings- und Feinabstimmungs-Pipelines eine Erkennung von Datenvergiftungen und eine Validierung der Datenintegrität implementieren (z. B. statistische Methoden, Ausreißererkennung, Einbettungsanalyse), um potenzielle Vergiftungsangriffe (z. B. Label-Flipping, Einfügen von Backdoor-Auslösern, Rollenwechselbefehle, einflussreiche Instanzangriffe) oder unbeabsichtigte Datenkorruption in den Trainingsdaten zu identifizieren. |   2   |  D/V  |
| 1.4.3 | Stellen Sie sicher, dass geeignete Schutzmaßnahmen wie adversariales Training (unter Verwendung erzeugter adversarialer Beispiele), Datenaugmentation mit gestörten Eingaben oder robuste Optimierungstechniken implementiert und basierend auf der Risikobewertung für relevante Modelle abgestimmt sind.                                                                                                                                                               |   3   |  D/V  |
| 1.4.4 | Stellen Sie sicher, dass automatisch generierte Labels (z. B. durch LLMs oder schwache Überwachung) Konfidenzschwellen und Konsistenzprüfungen unterliegen, um halluzinierte, irreführende oder Labels mit geringer Konfidenz zu erkennen.                                                                                                                                                                                                                               |   2   |  D/V  |
| 1.4.5 | Verifizieren Sie, dass automatisierte Tests bei jeder Datenaufnahme oder jeder signifikanten Datenumwandlung Label-Skews erkennen.                                                                                                                                                                                                                                                                                                                                       |   3   |   D   |

---

## C1.5 Datenherkunft und Nachverfolgbarkeit

Verfolgen Sie den vollständigen Weg jedes einzelnen Datenpunkts vom Ursprung bis zur Modelleingabe für Nachvollziehbarkeit und Vorfallreaktion.

|   #   | Beschreibung                                                                                                                                                                                                                                                                             | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.5.1 | Stellen Sie sicher, dass der Ursprung jedes Datenpunkts, einschließlich aller Transformationen, Erweiterungen und Zusammenführungen, dokumentiert ist und rekonstruiert werden kann.                                                                                                     |   2   |  D/V  |
| 1.5.2 | Stellen Sie sicher, dass Herkunftsdaten unveränderlich, sicher gespeichert und für Prüfungen zugänglich sind.                                                                                                                                                                            |   2   |  D/V  |
| 1.5.3 | Stellen Sie sicher, dass die Nachverfolgung der Herkunft synthetischer Daten, die mittels datenschutzschützender oder generativer Techniken erzeugt wurden, abdeckt, und dass alle synthetischen Daten im gesamten Prozess klar gekennzeichnet und von realen Daten unterscheidbar sind. |   2   |  D/V  |

---

## Referenzen

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

