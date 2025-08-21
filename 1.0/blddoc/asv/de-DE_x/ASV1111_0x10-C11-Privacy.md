# 11 Datenschutz & Verwaltung persönlicher Daten

## Kontrollziel

Gewährleisten Sie strenge Datenschutzgarantien über den gesamten KI-Lebenszyklus hinweg—Erfassung, Training, Inferenz und Vorfallreaktion—sodass personenbezogene Daten nur mit eindeutiger Zustimmung, minimalem erforderlichen Umfang, nachweisbarer Löschung und formellen Datenschutzgarantien verarbeitet werden.

---

## 11.1 Anonymisierung & Datenminimierung

|   #    | Beschreibung                                                                                                                                                                          | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.1.1 | Überprüfen Sie, dass direkte und Quasi-Identifikatoren entfernt oder gehasht werden.                                                                                                  |   1   |  D/V  |
| 11.1.2 | Überprüfen Sie, dass automatisierte Prüfungen k-Anonymität/l-Diversität messen und benachrichtigen, wenn die Schwellenwerte unter die Richtlinie fallen.                              |   2   |  D/V  |
| 11.1.3 | Überprüfen Sie, dass die Berichte zur Merkmalwichtigkeit des Modells keine Kennungsweitergabe über ε = 0,01 wechselseitige Information hinaus nachweisen.                             |   2   |   V   |
| 11.1.4 | Stellen Sie sicher, dass formale Beweise oder Zertifizierungen mit synthetischen Daten zeigen, dass das Risiko der Re-Identifikation selbst bei Verknüpfungsangriffen ≤ 0,05 beträgt. |   3   |   V   |

---

## 11.2 Recht auf Vergessenwerden & Durchsetzung der Löschung

|   #    | Beschreibung                                                                                                                                                                                                                         | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 11.2.1 | Überprüfen Sie, dass Anfragen zur Löschung von Datenbetroffenen auf Rohdatensätze, Checkpoints, Einbettungen, Protokolle und Sicherungskopien innerhalb von Service-Level-Vereinbarungen von weniger als 30 Tagen übertragen werden. |   1   |  D/V  |
| 11.2.2 | Überprüfen Sie, dass „Machine-Unlearning“-Routinen physisch eine Neu-Trainierung durchführen oder eine Annäherung der Entfernung mithilfe zertifizierter Unlearning-Algorithmen vornehmen.                                           |   2   |   D   |
| 11.2.3 | Überprüfen Sie, dass die Evaluierung des Schattenmodells nachweist, dass vergessene Datensätze weniger als 1 % der Ausgaben nach dem Unlearning beeinflussen.                                                                        |   2   |   V   |
| 11.2.4 | Stellen Sie sicher, dass Löschvorgänge unveränderlich protokolliert und für Aufsichtsbehörden prüfbar sind.                                                                                                                          |   3   |   V   |

---

## 11.3 Differenzielle Datenschutzmaßnahmen

|   #    | Beschreibung                                                                                                                         | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 11.3.1 | Überprüfen Sie, ob Datenschutz-Verlustabrechnungs-Dashboards alarmieren, wenn der kumulative ε die Richtliniengrenzen überschreitet. |   2   |  D/V  |
| 11.3.2 | Überprüfen Sie, ob Black-Box-Datenschutzprüfungen ε̂ innerhalb von 10 % des angegebenen Werts schätzen.                              |   2   |   V   |
| 11.3.3 | Stellen Sie sicher, dass formale Beweise alle Feinabstimmungen nach dem Training und Einbettungen abdecken.                          |   3   |   V   |

---

## 11.4 Zweckbindung & Schutz vor Scope Creep

|   #    | Beschreibung                                                                                                                                                                | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.4.1 | Überprüfen Sie, dass jeder Datensatz und jeder Modell-Checkpoint mit einem maschinenlesbaren Zweck-Tag versehen ist, das mit der ursprünglichen Einwilligung übereinstimmt. |   1   |   D   |
| 11.4.2 | Stellen Sie sicher, dass Laufzeitüberwachungen Anfragen erkennen, die mit dem angegebenen Zweck unvereinbar sind, und eine weiche Ablehnung auslösen.                       |   1   |  D/V  |
| 11.4.3 | Verifizieren Sie, dass Richtlinien-als-Code-Gates die erneute Bereitstellung von Modellen in neuen Domänen ohne DPIA-Überprüfung blockieren.                                |   3   |   D   |
| 11.4.4 | Stellen Sie sicher, dass formale Rückverfolgbarkeitsnachweise zeigen, dass sich jeder Lebenszyklus personenbezogener Daten im einwilligungsgemäßen Umfang bewegt.           |   3   |   V   |

---

## 11.5 Einwilligungsmanagement & rechtmäßige Grundlagenverfolgung

|   #    | Beschreibung                                                                                                                                         | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.5.1 | Überprüfen Sie, ob eine Consent-Management-Plattform (CMP) den Opt-in-Status, den Zweck und die Aufbewahrungsdauer pro betroffener Person speichert. |   1   |  D/V  |
| 11.5.2 | Stellen Sie sicher, dass APIs Einwilligungstoken bereitstellen; Modelle müssen den Token-Bereich vor der Inferenz validieren.                        |   2   |   D   |
| 11.5.3 | Stellen Sie sicher, dass verweigerte oder widerrufene Einwilligungen die Verarbeitungsprozesse innerhalb von 24 Stunden stoppen.                     |   2   |  D/V  |

---

## 11.6 Föderiertes Lernen mit Datenschutzkontrollen

|   #    | Beschreibung                                                                                                                 | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.6.1 | Überprüfen Sie, ob Client-Updates vor der Aggregation eine lokale Differentielle-Privatsphäre-Rauschunterdrückung verwenden. |   1   |   D   |
| 11.6.2 | Überprüfen Sie, dass Trainingsmetriken differenziell privat sind und niemals den Verlust eines einzelnen Clients offenlegen. |   2   |  D/V  |
| 11.6.3 | Verifizieren Sie, dass eine gegen Datenvergiftung resistente Aggregation (z. B. Krum/Trimmed-Mean) aktiviert ist.            |   2   |   V   |
| 11.6.4 | Verifizieren Sie, dass formale Beweise das gesamte ε-Budget mit einem Nutzungsverlust von weniger als 5 nachweisen.          |   3   |   V   |

---

### Referenzen

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

