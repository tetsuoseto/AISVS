# C1 Schulung zu Daten-Governance und Bias-Management

## Kontrollziel

Trainingsdaten müssen so beschafft, gehandhabt und gepflegt werden, dass Herkunft, Sicherheit, Qualität und Fairness gewahrt bleiben. Dies erfüllt rechtliche Verpflichtungen und verringert das Risiko von Verzerrungen, Manipulationen oder Datenschutzverletzungen, die während des Trainings auftreten und den gesamten KI-Lebenszyklus beeinträchtigen könnten.

---

## C1.1 Herkunft der Trainingsdaten

Führen Sie ein überprüfbares Inventar aller Datensätze, akzeptieren Sie nur vertrauenswürdige Quellen und protokollieren Sie jede Änderung zur Nachvollziehbarkeit.

|   #   | Beschreibung                                                                                                                                                                                                    | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.1.1 | Stellen Sie sicher, dass ein aktuelles Inventar aller Trainingsdatenquellen (Ursprung, Verantwortlicher/Eigentümer, Lizenz, Erfassungsmethode, Nutzungseinschränkungen und Verarbeitungshistorie) geführt wird. |   1   |  D/V  |
| 1.1.2 | Überprüfen Sie, dass die Verarbeitung der Trainingsdaten unnötige Merkmale, Attribute oder Felder ausschließt (z. B. ungenutzte Metadaten, sensible personenbezogene Daten, durchgesickerte Testdaten).         |   1   |  D/V  |
| 1.1.3 | Stellen Sie sicher, dass alle Änderungen am Datensatz einem protokollierten Genehmigungsworkflow unterliegen.                                                                                                   |   2   |  D/V  |
| 1.1.4 | Stellen Sie sicher, dass Datensätze oder Teilmengen, wo möglich, mit Wasserzeichen oder Fingerabdrücken versehen sind.                                                                                          |   3   |  D/V  |

---

## C1.2 Sicherheit und Integrität der Trainingsdaten

Beschränken Sie den Zugriff auf Trainingsdaten, verschlüsseln Sie diese im Ruhezustand und während der Übertragung und überprüfen Sie deren Integrität, um Manipulation, Diebstahl oder Datenvergiftung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                    | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.2.1 | Überprüfen Sie, dass Zugriffskontrollen den Speicher und die Pipelines der Trainingsdaten schützen.                                                                                             |   1   |  D/V  |
| 1.2.2 | Stellen Sie sicher, dass sämtlicher Zugriff auf Trainingsdaten protokolliert wird, einschließlich Benutzer, Zeitpunkt und Aktion.                                                               |   2   |  D/V  |
| 1.2.3 | Stellen Sie sicher, dass Trainingsdatensätze während der Übertragung und im Ruhezustand mit branchenüblichen kryptografischen Algorithmen und Schlüsselverwaltungspraktiken verschlüsselt sind. |   2   |  D/V  |
| 1.2.4 | Stellen Sie sicher, dass kryptografische Hashes oder digitale Signaturen verwendet werden, um die Datenintegrität während der Speicherung und Übertragung von Trainingsdaten zu gewährleisten.  |   2   |  D/V  |
| 1.2.5 | Stellen Sie sicher, dass automatisierte Erkennungstechniken angewendet werden, um unautorisierte Änderungen oder die Beschädigung von Trainingsdaten zu verhindern.                             |   2   |  D/V  |
| 1.2.6 | Stellen Sie sicher, dass veraltete Trainingsdaten sicher gelöscht oder anonymisiert werden.                                                                                                     |   2   |  D/V  |
| 1.2.7 | Stellen Sie sicher, dass alle Trainingsdatensatzversionen eindeutig identifiziert, unveränderlich gespeichert und prüfbar sind, um Rollbacks und forensische Analysen zu unterstützen.          |   3   |  D/V  |

---

## C1.3 Qualität, Integrität und Sicherheit der Trainingsdatenkennzeichnung

Schützen Sie Labels und verlangen Sie eine technische Überprüfung für kritische Daten.

|   #   | Beschreibung                                                                                                                                                                                                                            | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.3.1 | Überprüfen Sie, dass kryptografische Hashes oder digitale Signaturen auf Etikettenartefakte angewendet werden, um deren Integrität und Authentizität zu gewährleisten.                                                                  |   2   |  D/V  |
| 1.3.2 | Stellen Sie sicher, dass die Kennzeichnungsoberflächen und -plattformen starke Zugriffskontrollen durchsetzen, manipulationssichere Prüfprotokolle aller Kennzeichnungsaktivitäten führen und Schutz gegen unbefugte Änderungen bieten. |   2   |  D/V  |
| 1.3.3 | Stellen Sie sicher, dass sensible Informationen in Labels auf Feldebene sowohl im Ruhezustand als auch während der Übertragung geschwärzt, anonymisiert oder verschlüsselt sind.                                                        |   3   |  D/V  |

---

## C1.4 Qualität der Trainingsdaten und Sicherheitsgarantie

Kombinieren Sie automatisierte Validierung, manuelle Stichprobenprüfungen und protokollierte Behebung, um die Zuverlässigkeit des Datensatzes zu gewährleisten.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                  | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.4.1 | Stellen Sie sicher, dass automatisierte Tests Formatfehler und Nullwerte bei jedem Ingest oder jeder signifikanten Datenumwandlung erfassen.                                                                                                                                                                                                                                                                                                                  |   1   |   D   |
| 1.4.2 | Stellen Sie sicher, dass LLM-Trainings- und Feinabstimmungs-Pipelines eine Erkennung von Vergiftungen und eine Validierung der Datenintegrität implementieren (z. B. statistische Methoden, Ausreißererkennung, Embedding-Analyse), um potenzielle Vergiftungsangriffe (z. B. Label-Flipping, Backdoor-Trigger-Einfügung, Rollenwechselbefehle, einflussreiche Instanzangriffe) oder unbeabsichtigte Datenkorruption im Trainingsdatensatz zu identifizieren. |   2   |  D/V  |
| 1.4.3 | Stellen Sie sicher, dass geeignete Abwehrmaßnahmen wie adversariales Training (unter Verwendung generierter adversarischer Beispiele), Datenaugmentation mit gestörten Eingaben oder robuste Optimierungstechniken implementiert und für relevante Modelle basierend auf der Risikobewertung abgestimmt sind.                                                                                                                                                 |   3   |  D/V  |
| 1.4.4 | Stellen Sie sicher, dass automatisch generierte Labels (z. B. über LLMs oder schwache Aufsicht) Confidenz-Schwellenwerten und Konsistenzprüfungen unterliegen, um halluzinierte, irreführende oder Labels mit geringer Zuverlässigkeit zu erkennen.                                                                                                                                                                                                           |   2   |  D/V  |
| 1.4.5 | Stellen Sie sicher, dass automatisierte Tests bei jeder Datenaufnahme oder bedeutenden Datenumwandlung Label-Verschiebungen erkennen.                                                                                                                                                                                                                                                                                                                         |   3   |   D   |

---

## C1.5 Datenherkunft und Rückverfolgbarkeit

Verfolgen Sie die gesamte Reise jedes Datenpunkts von der Quelle bis zur Modelleingabe für Prüfbarkeit und Vorfallreaktion.

|   #   | Beschreibung                                                                                                                                                                                                                                                                            | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.5.1 | Stellen Sie sicher, dass die Herkunft jedes Datenpunkts, einschließlich aller Transformationen, Erweiterungen und Zusammenführungen, aufgezeichnet wird und rekonstruiert werden kann.                                                                                                  |   2   |  D/V  |
| 1.5.2 | Stellen Sie sicher, dass Abstammungsdaten unveränderlich, sicher gespeichert und für Prüfungen zugänglich sind.                                                                                                                                                                         |   2   |  D/V  |
| 1.5.3 | Stellen Sie sicher, dass die Nachverfolgung der Herkunft synthetischer Daten, die durch datenschutzwahrende oder generative Techniken erzeugt wurden, abgedeckt ist und dass alle synthetischen Daten im gesamten Prozess klar gekennzeichnet und von echten Daten unterscheidbar sind. |   2   |  D/V  |

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

