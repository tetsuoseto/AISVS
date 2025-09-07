# 11 Datenschutz und Verwaltung personenbezogener Daten

## Kontrollziel

Gewährleisten Sie strenge Datenschutzgarantien über den gesamten KI-Lebenszyklus hinweg – Erfassung, Training, Inferenz und Vorfallsreaktion – damit personenbezogene Daten nur mit klarer Einwilligung, minimalem notwendigem Umfang, nachweisbarer Löschung und formellen Datenschutzgarantien verarbeitet werden.

---

## 11.1 Anonymisierung & Datenminimierung

|   #    | Beschreibung                                                                                                                                                        | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.1.1 | Überprüfen Sie, dass direkte und Quasi-Identifier entfernt oder gehasht werden.                                                                                     |   1    |  D/V  |
| 11.1.2 | Verifizieren Sie, dass automatisierte Prüfungen k-Anonymität/l-Diversität messen und Alarm schlagen, wenn Schwellenwerte unter die Richtlinie fallen.               |   2    |  D/V  |
| 11.1.3 | Überprüfen Sie, dass die Berichte zur Merkmalswichtigkeit des Modells keinen Identifikator-Leckage jenseits von ε = 0,01 wechselseitiger Information nachweisen.    |   2    |   V   |
| 11.1.4 | Verifizieren Sie, dass formale Beweise oder die Zertifizierung synthetischer Daten das Re-Identifikationsrisiko ≤ 0,05 selbst bei Verknüpfungsangriffen nachweisen. |   3    |   V   |

---

## 11.2 Recht auf Vergessenwerden und Durchsetzung der Löschung

|   #    | Beschreibung                                                                                                                                                                                                         | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.2.1 | Stellen Sie sicher, dass Löschanfragen von Datenpersonen auf Rohdatensätze, Checkpoints, Einbettungen, Protokolle und Backups innerhalb der Service-Level-Vereinbarungen von weniger als 30 Tagen übertragen werden. |   1    |  D/V  |
| 11.2.2 | Verifizieren Sie, dass „Machine-Unlearning“-Routinen physisch neu trainieren oder eine angenäherte Entfernung unter Verwendung zertifizierter Unlearning-Algorithmen durchführen.                                    |   2    |   D   |
| 11.2.3 | Überprüfen Sie, dass die Bewertung des Schattenmodells beweist, dass vergessene Datensätze nach dem Unlearning weniger als 1 % der Ausgaben beeinflussen.                                                            |   2    |   V   |
| 11.2.4 | Stellen Sie sicher, dass Löschvorgänge unveränderlich protokolliert und für Regulierungsbehörden prüfbar sind.                                                                                                       |   3    |   V   |

---

## 11.3 Differenzielle Datenschutzmaßnahmen

|   #    | Beschreibung                                                                                                                             | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.3.1 | Überprüfen Sie, ob Datenschutzverlust-Abrechnungs-Dashboards Alarm schlagen, wenn die kumulative ε die Richtliniengrenzen überschreitet. |   2    |  D/V  |
| 11.3.2 | Überprüfen Sie, ob Black-Box-Datenschutzprüfungen ε̂ auf innerhalb von 10 % des angegebenen Werts schätzen.                              |   2    |   V   |
| 11.3.3 | Stellen Sie sicher, dass formale Beweise alle Feinabstimmungen und Einbettungen nach dem Training abdecken.                              |   3    |   V   |

---

## 11.4 Zweckbeschränkung und Schutz vor Umfangserweiterung

|   #    | Beschreibung                                                                                                                                                       | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 11.4.1 | Stellen Sie sicher, dass jeder Datensatz und jeder Modell-Checkpoint einen maschinenlesbaren Zweck-Tag trägt, der mit der ursprünglichen Zustimmung übereinstimmt. |   1    |   D   |
| 11.4.2 | Überprüfen Sie, ob Laufzeitmonitore Abfragen erkennen, die mit dem angegebenen Zweck unvereinbar sind, und eine sanfte Ablehnung auslösen.                         |   1    |  D/V  |
| 11.4.3 | Überprüfen Sie, dass Policy-as-Code-Gates die erneute Bereitstellung von Modellen in neuen Domänen ohne DPIA-Überprüfung blockieren.                               |   3    |   D   |
| 11.4.4 | Überprüfen Sie, dass formale Rückverfolgbarkeitsnachweise zeigen, dass jeder Ablauf personenbezogener Daten innerhalb des genehmigten Rahmens bleibt.              |   3    |   V   |

---

## 11.5 Einwilligungsverwaltung & rechtmäßige Grundlage der Nachverfolgung

|   #    | Beschreibung                                                                                                                                                  | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 11.5.1 | Überprüfen Sie, ob eine Consent-Management-Plattform (CMP) den Opt-in-Status, den Verwendungszweck und die Aufbewahrungsdauer pro betroffener Person erfasst. |   1    |  D/V  |
| 11.5.2 | Überprüfen Sie, ob APIs Konsenttokene bereitstellen; Modelle müssen den Token-Bereich vor der Inferenz validieren.                                            |   2    |   D   |
| 11.5.3 | Überprüfen Sie, dass verweigerte oder widerrufene Einwilligungen die Verarbeitungspipelines innerhalb von 24 Stunden stoppen.                                 |   2    |  D/V  |

---

## 11.6 Föderiertes Lernen mit Datenschutzkontrollen

|   #    | Beschreibung                                                                                                                   | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 11.6.1 | Stellen Sie sicher, dass bei Client-Updates vor der Aggregation lokal differentielle Datenschutzrauschaddition verwendet wird. |   1    |   D   |
| 11.6.2 | Verifizieren Sie, dass Trainingsmetriken differenziell privat sind und niemals den Verlust einzelner Kunden offenlegen.        |   2    |  D/V  |
| 11.6.3 | Stellen Sie sicher, dass eine vergiftungsresistente Aggregation (z. B. Krum/Trimmed-Mean) aktiviert ist.                       |   2    |   V   |
| 11.6.4 | Überprüfen Sie, dass formale Beweise das gesamte ε-Budget mit einem Nutzungsverlust von weniger als 5 nachweisen.              |   3    |   V   |

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

