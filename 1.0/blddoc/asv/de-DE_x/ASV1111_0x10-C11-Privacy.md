# 11 Datenschutz und Verwaltung personenbezogener Daten

## Kontrollziel

Gewährleisten Sie durchgängig strenge Datenschutzgarantien über den gesamten KI-Lebenszyklus hinweg—Datenerhebung, Training, Inferenz und Vorfallreaktion—damit personenbezogene Daten nur mit klarer Zustimmung, minimalem notwendigen Umfang, nachweisbarer Löschung und formalen Datenschutzgarantien verarbeitet werden.

---

## 11.1 Anonymisierung und Datenminimierung

|   #    | Beschreibung                                                                                                                                                           | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.1.1 | Überprüfen Sie, ob direkte und quasi-identifizierende Merkmale entfernt und gehasht werden.                                                                            |   1   |  D/V  |
| 11.1.2 | Verifizieren Sie, dass automatisierte Prüfungen k-Anonymität/l-Diversität messen und Warnungen auslösen, wenn Schwellenwerte unter der festgelegten Richtlinie liegen. |   2   |  D/V  |
| 11.1.3 | Verifizieren Sie, dass Berichte zur Merkmals-Wichtigkeit des Modells kein Identifikatorleck über ε = 0.01 Mutual Information nachweisen.                               |   2   |   V   |
| 11.1.4 | Stellen Sie sicher, dass formale Beweise oder Zertifizierungen synthetischer Daten das Re-Identifikationsrisiko ≤ 0.05 auch unter Verknüpfungsangriffen nachweisen.    |   3   |   V   |

---

## 11.2 Recht auf Vergessenwerden und Durchsetzung der Löschung

|   #    | Beschreibung                                                                                                                                                                                                                | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.2.1 | Überprüfen Sie, dass Anfragen zur Löschung von Daten-Subjekten an Rohdatensätze, Checkpoints, Embeddings, Protokolle und Backups innerhalb der Service-Level-Vereinbarungen von weniger als 30 Tagen weitergeleitet werden. |   1   |  D/V  |
| 11.2.2 | Verifizieren Sie, dass 'machine-unlearning'-Routinen physisch neu trainieren oder die Entfernung mithilfe zertifizierter Unlearning-Algorithmen annähern.                                                                   |   2   |   D   |
| 11.2.3 | Verifizieren Sie, dass die Evaluierung des Schattenmodells nachweist, dass vergessene Datensätze weniger als 1% der Ausgaben nach dem Unlernen beeinflussen.                                                                |   2   |   V   |
| 11.2.4 | Überprüfen Sie, dass Löschvorgänge unveränderlich protokolliert und für Aufsichtsbehörden auditierbar sind.                                                                                                                 |   3   |   V   |

---

## 11.3 Schutzmaßnahmen zur Differential-Privatsphäre

|   #    | Beschreibung                                                                                                                                         | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.3.1 | Überprüfen Sie, ob Dashboards zur Privacy-Verlust-Abrechnung Warnungen auslösen, wenn das kumulative ε die Richtlinien-Schwellenwerte überschreitet. |   2   |  D/V  |
| 11.3.2 | Verifizieren Sie, dass Black-Box-Datenschutzprüfungen ε̂ innerhalb von 10% des angegebenen Werts schätzen.                                           |   2   |   V   |
| 11.3.3 | Überprüfen Sie, ob formale Beweise alle Feinabstimmungen nach dem Training und Einbettungen abdecken.                                                |   3   |   V   |

---

## 11.4 Zweck-Limitierung & Scope-Creep-Schutz

|   #    | Beschreibung                                                                                                                                                       | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 11.4.1 | Verifizieren Sie, dass jeder Datensatz und jeder Modell-Checkpoint eine maschinenlesbare Zweckangabe trägt, die mit der ursprünglichen Einwilligung übereinstimmt. |   1   |   D   |
| 11.4.2 | Stellen Sie sicher, dass Laufzeitmonitore Abfragen erkennen, die nicht mit dem angegebenen Zweck übereinstimmen, und eine sanfte Ablehnung auslösen.               |   1   |  D/V  |
| 11.4.3 | Stellen Sie sicher, dass Policy-as-Code-Gates die erneute Bereitstellung von Modellen in neue Domänen ohne DPIA-Überprüfung blockieren.                            |   3   |   D   |
| 11.4.4 | Überprüfen Sie, ob formale Nachweise der Rückverfolgbarkeit zeigen, dass jeder Lebenszyklus personenbezogener Daten innerhalb des genehmigten Umfangs bleibt.      |   3   |   V   |

---

## 11.5 Einwilligungs-Management & Tracking gemäß Rechtsgrundlage

|   #    | Beschreibung                                                                                                                                             | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.5.1 | Stellen Sie sicher, dass eine Consent-Management-Plattform (CMP) den Opt-in-Status, den Zweck und die Aufbewahrungsdauer pro Datensubjekt protokolliert. |   1   |  D/V  |
| 11.5.2 | Stellen Sie sicher, dass APIs Einwilligungstoken bereitstellen; Modelle müssen den Gültigkeitsbereich des Tokens vor der Inferenz validieren.            |   2   |   D   |
| 11.5.3 | Stellen Sie sicher, dass verweigerte oder widerrufene Zustimmung Verarbeitungspipelines innerhalb von 24 Stunden gestoppt werden.                        |   2   |  D/V  |

---

## 11.6 Föderiertes Lernen mit Datenschutzkontrollen

|   #    | Beschreibung                                                                                                                           | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 11.6.1 | Überprüfen Sie, dass Client-Updates vor der Aggregation eine Rauschaddierung im Rahmen der lokalen Differentialprivatsphäre verwenden. |   1   |   D   |
| 11.6.2 | Stellen Sie sicher, dass die Trainingsmetriken differenziell privat sind und niemals den Verlust eines einzelnen Clients preisgeben.   |   2   |  D/V  |
| 11.6.3 | Vergewissern Sie sich, dass eine vergiftungsresistente Aggregation (z. B. Krum/getrimmter Mittelwert) aktiviert ist.                   |   2   |   V   |
| 11.6.4 | Verifizieren Sie, dass formale Beweise das gesamte ε-Budget nachweisen und dabei einen Nutzenverlust von weniger als 5 aufweisen.      |   3   |   V   |

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

