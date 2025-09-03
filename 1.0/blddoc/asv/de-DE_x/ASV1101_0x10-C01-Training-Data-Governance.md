# C1 Trainingsdaten-Governance und Bias-Management

## Kontrollziel

Trainingsdaten müssen beschafft, verarbeitet und gepflegt werden, um Provenienz, Sicherheit, Qualität und Fairness zu bewahren. Dadurch werden gesetzliche Pflichten erfüllt und das Risiko von Voreingenommenheit, Datenvergiftung oder Datenschutzverletzungen reduziert, die während des Trainings auftreten und den gesamten KI-Lebenszyklus beeinflussen könnten.

---

## C1.1 Provenienz der Trainingsdaten

Führen Sie ein verifizierbares Inventar aller Datensätze, akzeptieren Sie ausschließlich vertrauenswürdige Quellen und protokollieren Sie jede Änderung zur Auditierbarkeit.

|   #   | Beschreibung                                                                                                                                                                                              | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.1.1 | Stellen Sie sicher, dass ein aktuelles Inventar jeder Trainingsdatenquelle (Ursprung, Verwalter/Eigentümer, Lizenz, Sammlungsmethode, Verwendungsbeschränkungen und Verarbeitungshistorie) gepflegt wird. |   1   |  D/V  |
| 1.1.2 | Stellen Sie sicher, dass die Verarbeitung von Trainingsdaten unnötige Merkmale, Attribute oder Felder ausschließt (z. B. ungenutzte Metadaten, sensible PII, geleakte Testdaten).                         |   1   |  D/V  |
| 1.1.3 | Stellen Sie sicher, dass alle Datensatzänderungen einem protokollierten Genehmigungs-Workflow unterliegen.                                                                                                |   2   |  D/V  |
| 1.1.4 | Stellen Sie sicher, dass Datensätze oder Teilmengen, soweit möglich, mit Wasserzeichen versehen oder durch Fingerprinting gekennzeichnet werden.                                                          |   3   |  D/V  |

---

## C1.2 Sicherheit und Integrität der Trainingsdaten

Beschränken Sie den Zugriff auf Trainingsdaten, verschlüsseln Sie sie im Ruhezustand und bei der Übertragung und validieren Sie deren Integrität, um Manipulationen, Diebstahl oder Datenvergiftung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                          | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.2.1 | Überprüfen Sie, ob Zugriffskontrollen die Speicherung von Trainingsdaten und Datenpipelines schützen.                                                                                                                 |   1   |  D/V  |
| 1.2.2 | Stellen Sie sicher, dass alle Zugriffe auf Trainingsdaten protokolliert werden, einschließlich Benutzer, Zeit und Aktion.                                                                                             |   2   |  D/V  |
| 1.2.3 | Überprüfen Sie, dass Trainingsdatensätze sowohl bei der Übertragung als auch im Ruhezustand verschlüsselt sind, unter Verwendung branchenüblicher kryptografischer Algorithmen und Praktiken der Schlüsselverwaltung. |   2   |  D/V  |
| 1.2.4 | Stellen Sie sicher, dass kryptografische Hashwerte oder digitale Signaturen verwendet werden, um die Integrität der Trainingsdaten während der Speicherung und Übertragung sicherzustellen.                           |   2   |  D/V  |
| 1.2.5 | Vergewissern Sie sich, dass automatisierte Erkennungstechniken angewendet werden, um unautorisierte Änderungen oder Beschädigungen der Trainingsdaten zu verhindern.                                                  |   2   |  D/V  |
| 1.2.6 | Stellen Sie sicher, dass veraltete Trainingsdaten sicher gelöscht oder anonymisiert werden.                                                                                                                           |   2   |  D/V  |
| 1.2.7 | Stellen Sie sicher, dass alle Versionen von Trainingsdatensätzen eindeutig identifiziert, unveränderlich gespeichert und nachprüfbar sind, um Rollback und forensische Analysen zu unterstützen.                      |   3   |  D/V  |

---

## C1.3 Qualität, Integrität und Sicherheit der Beschriftung von Trainingsdaten

Schützen Sie Labels und verlangen Sie eine technische Prüfung für kritische Daten.

|   #   | Beschreibung                                                                                                                                                                                                                         | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 1.3.1 | Überprüfen Sie, dass kryptografische Hashwerte oder digitale Signaturen auf Label-Artefakte angewendet werden, um deren Integrität und Authentizität sicherzustellen.                                                                |   2   |  D/V  |
| 1.3.2 | Überprüfen Sie, ob Beschriftungsschnittstellen und Beschriftungsplattformen strenge Zugriffskontrollen durchsetzen, manipulationssichere Audit-Protokolle aller Beschriftungsvorgänge führen und vor unbefugten Änderungen schützen. |   2   |  D/V  |
| 1.3.3 | Stellen Sie sicher, dass sensible Informationen in Labels auf Feldebene sowohl im Ruhezustand als auch bei der Übertragung geschwärzt, anonymisiert oder verschlüsselt werden.                                                       |   3   |  D/V  |

---

## C1.4 Qualität der Trainingsdaten und Sicherheitsgarantien

Kombinieren Sie automatisierte Validierung, manuelle Spot-Checks und protokollierte Behebungsmaßnahmen, um die Zuverlässigkeit des Datensatzes sicherzustellen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 1.4.1 | Stellen Sie sicher, dass automatisierte Tests bei jeder Datenaufnahme oder wesentlichen Datenumwandlung Formatfehler und Nullwerte erkennen.                                                                                                                                                                                                                                                                                                                              |   1   |   D   |
| 1.4.2 | Vergewissern Sie sich, dass die LLM-Trainings- und Feinabstimmungs-Pipelines eine Erkennung von Datenvergiftung und Validierung der Datenintegrität implementieren (z. B. statistische Methoden, Ausreißererkennung, Embedding-Analyse), um potenzielle Vergiftungsangriffe (z. B. Label-Flipping, Einfügung von Backdoor-Auslösern, Rollenwechsel-Befehle, einflussreiche Instanzangriffe) oder unbeabsichtigte Datenkorruption in den Trainingsdaten zu identifizieren. |   2   |  D/V  |
| 1.4.3 | Überprüfen Sie, dass geeignete Abwehrmaßnahmen implementiert und basierend auf der Risikobewertung auf relevante Modelle abgestimmt sind, z. B. Adversarial Training (unter Verwendung generierter adversarischer Beispiele), Datenaugmentation mit gestörten Eingaben oder robuste Optimierungstechniken.                                                                                                                                                                |   3   |  D/V  |
| 1.4.4 | Stellen Sie sicher, dass automatisch generierte Labels (z. B. mittels LLMs oder schwacher Überwachung) Konfidenzschwellen und Konsistenzprüfungen unterliegen, um halluzinierte, irreführende oder Labels mit niedriger Konfidenz zu erkennen.                                                                                                                                                                                                                            |   2   |  D/V  |
| 1.4.5 | Stellen Sie sicher, dass automatisierte Tests Label-Verzerrungen bei jeder Datenaufnahme oder jeder signifikanten Datenumwandlung erkennen.                                                                                                                                                                                                                                                                                                                               |   3   |   D   |

---

## C1.5 Datenherkunft und Rückverfolgbarkeit

Verfolgen Sie den vollständigen Weg jedes Datenpunkts vom Ursprung zur Modell-Eingabe, um Nachvollziehbarkeit und Vorfallreaktion zu ermöglichen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                           | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 1.5.1 | Überprüfen Sie, ob die Herkunft jedes Datenpunkts, einschließlich aller Transformationen, Datenaugmentationen und Zusammenführungen, aufgezeichnet wird und rekonstruiert werden kann.                                                                                                                 |   2   |  D/V  |
| 1.5.2 | Überprüfen Sie, dass die Datenherkunftsaufzeichnungen unveränderlich, sicher gespeichert und für Audits zugänglich sind.                                                                                                                                                                               |   2   |  D/V  |
| 1.5.3 | Stellen Sie sicher, dass die Datenherkunftsnachverfolgung auch synthetische Daten abdeckt, die mittels datenschutzfreundlicher oder generativer Techniken erzeugt werden, und dass alle synthetischen Daten in der gesamten Pipeline deutlich gekennzeichnet und von echten Daten unterscheidbar sind. |   2   |  D/V  |

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

