# 11 Datenschutz und Verwaltung persönlicher Daten

## Steuerungsziel

Gewährleisten Sie strenge Datenschutzgarantien im gesamten KI-Lebenszyklus—Erhebung, Training, Inferenz und Vorfallreaktion—sodass personenbezogene Daten nur mit eindeutiger Einwilligung, auf das notwendige Minimum beschränkt, nachweislich gelöscht und mit formalen Datenschutzgarantien verarbeitet werden.

---

## 11.1 Anonymisierung & Datenminimierung

|   #    | Beschreibung                                                                                                                                                    | Ebene | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.1.1 | Überprüfen Sie, dass direkte und Quasi-Identifikatoren entfernt oder gehasht werden.                                                                            |   1   |  D/V  |
| 11.1.2 | Überprüfen Sie, dass automatisierte Prüfungen k-Anonymität/l-Diversität messen und Alarm schlagen, wenn die Schwellenwerte unter die Richtlinie fallen.         |   2   |  D/V  |
| 11.1.3 | Verifizieren Sie, dass Modell-Feature-Importance-Berichte keine Identifikator-Lecks über ε = 0,01 gegenseitige Information hinaus nachweisen.                   |   2   |   V   |
| 11.1.4 | Überprüfen Sie, dass formale Beweise oder Zertifizierungen für synthetische Daten ein Re-Identifikationsrisiko von ≤ 0,05 zeigen, selbst bei Linkage-Angriffen. |   3   |   V   |

---

## 11.2 Recht auf Vergessenwerden und Durchsetzung der Löschung

|   #    | Beschreibung                                                                                                                                                                                                                        | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.2.1 | Überprüfen Sie, dass Löschanfragen von Betroffenen in Bezug auf Daten auf rohe Datensätze, Checkpoints, Einbettungen, Protokolle und Backups innerhalb von Service-Level-Vereinbarungen von weniger als 30 Tagen übertragen werden. |   1   |  D/V  |
| 11.2.2 | Verifizieren Sie, dass "Machine-Unlearning"-Routinen physisch neu trainieren oder eine angenäherte Entfernung durch zertifizierte Unlearning-Algorithmen durchführen.                                                               |   2   |   D   |
| 11.2.3 | Verifizieren Sie, dass die Auswertung des Schattenmodells beweist, dass vergessene Datensätze weniger als 1 % der Ausgaben nach dem Unlearning beeinflussen.                                                                        |   2   |   V   |
| 11.2.4 | Verifizieren Sie, dass Löschvorgänge unveränderlich protokolliert und für Aufsichtsbehörden prüfbar sind.                                                                                                                           |   3   |   V   |

---

## 11.3 Differential-Privacy-Schutzmaßnahmen

|   #    | Beschreibung                                                                                                                              | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.3.1 | Überprüfen Sie, ob Datenschutz-Verlust-Abrechnungs-Dashboards Alarm schlagen, wenn der kumulative ε die Richtliniengrenzen überschreitet. |   2   |  D/V  |
| 11.3.2 | Verifizieren Sie, dass Black-Box-Datenschutzprüfungen ε̂ innerhalb von 10 % des angegebenen Werts schätzen.                               |   2   |   V   |
| 11.3.3 | Stellen Sie sicher, dass formale Beweise alle Feinabstimmungen und Einbettungen nach dem Training abdecken.                               |   3   |   V   |

---

## 11.4 Zweckbindung & Schutz vor Umfangserweiterung

|   #    | Beschreibung                                                                                                                                                         | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.4.1 | Stellen Sie sicher, dass jeder Datensatz und jeder Modell-Checkpoint einen maschinenlesbaren Zweck-Tag trägt, der mit der ursprünglichen Einwilligung übereinstimmt. |   1   |   D   |
| 11.4.2 | Überprüfen Sie, ob Laufzeitüberwachungen Abfragen erkennen, die mit dem deklarierten Zweck nicht übereinstimmen, und eine sanfte Ablehnung auslösen.                 |   1   |  D/V  |
| 11.4.3 | Überprüfen Sie, dass Policy-as-Code-Gates die erneute Bereitstellung von Modellen in neuen Domänen ohne DPIA-Überprüfung blockieren.                                 |   3   |   D   |
| 11.4.4 | Stellen Sie sicher, dass formelle Rückverfolgbarkeitsnachweise zeigen, dass jeder Lebenszyklus personenbezogener Daten im genehmigten Umfang verbleibt.              |   3   |   V   |

---

## 11.5 Einwilligungsmanagement & rechtmäßige Basisverfolgung

|   #    | Beschreibung                                                                                                                                           | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 11.5.1 | Überprüfen Sie, ob eine Consent-Management-Plattform (CMP) den Opt-in-Status, den Zweck und die Aufbewahrungsdauer pro betroffener Person aufzeichnet. |   1   |  D/V  |
| 11.5.2 | Überprüfen Sie, ob APIs Zustimmungstoken bereitstellen; Modelle müssen den Geltungsbereich des Tokens vor der Inferenz validieren.                     |   2   |   D   |
| 11.5.3 | Stellen Sie sicher, dass verweigerte oder widerrufene Einwilligungen die Verarbeitungspipelines innerhalb von 24 Stunden stoppen.                      |   2   |  D/V  |

---

## 11.6 Föderiertes Lernen mit Datenschutzkontrollen

|   #    | Beschreibung                                                                                                                 | Ebene | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.6.1 | Stellen Sie sicher, dass Client-Updates vor der Aggregation eine lokale Differential-Privacy-Rauschaddition verwenden.       |   1   |   D   |
| 11.6.2 | Überprüfen Sie, dass Trainingsmetriken differenziell privat sind und niemals den Verlust eines einzelnen Clients offenlegen. |   2   |  D/V  |
| 11.6.3 | Vergewissern Sie sich, dass eine gegen Vergiftung resistente Aggregation (z. B. Krum/Trimmed-Mean) aktiviert ist.            |   2   |   V   |
| 11.6.4 | Überprüfen Sie, dass formale Beweise das gesamte ε-Budget mit weniger als 5 Nutzungsverlust nachweisen.                      |   3   |   V   |

---

### Literaturverzeichnis

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

