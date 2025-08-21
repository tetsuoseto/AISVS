# C13 Menschliche Aufsicht, Verantwortlichkeit und Governance

## Kontrollziel

Dieses Kapitel stellt Anforderungen für die Aufrechterhaltung menschlicher Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen bereit und gewährleistet Erklärbarkeit, Transparenz und ethische Fürsorge während des gesamten KI-Lebenszyklus.

---

## C13.1 Kill-Switch- und Überschreibmechanismen

Stellen Sie Abschalt- oder Rollback-Pfade bereit, wenn ein unsicheres Verhalten des KI-Systems beobachtet wird.

|   #    | Beschreibung                                                                                                                      | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.1.1 | Verifizieren Sie, dass ein manueller Not-Aus-Mechanismus vorhanden ist, um die AI-Modell-Inferenz und Ausgaben sofort zu stoppen. |   1   |  D/V  |
| 13.1.2 | Stellen Sie sicher, dass die Übersteuerungskontrollen nur für autorisiertes Personal zugänglich sind.                             |   1   |   D   |
| 13.1.3 | Überprüfen Sie, ob Rollback-Verfahren zu vorherigen Modellversionen oder sicheren Betriebsmodi zurückkehren können.               |   3   |  D/V  |
| 13.1.4 | Stellen Sie sicher, dass die Override-Mechanismen regelmäßig getestet werden.                                                     |   3   |   V   |

---

## C13.2 Mensch-im-Loop-Entscheidungsüberprüfungspunkte

Menschliche Genehmigungen erforderlich, wenn Einsätze vordefinierte Risikoschwellen überschreiten.

|   #    | Beschreibung                                                                                                                                                                                  | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.2.1 | Stellen Sie sicher, dass KI-Entscheidungen mit hohem Risiko vor der Ausführung eine ausdrückliche menschliche Genehmigung erfordern.                                                          |   1   |  D/V  |
| 13.2.2 | Stellen Sie sicher, dass Risikoschwellen klar definiert sind und automatisch menschliche Prüfabläufe auslösen.                                                                                |   1   |   D   |
| 13.2.3 | Stellen Sie sicher, dass zeitkritische Entscheidungen über Ausweichverfahren verfügen, wenn eine menschliche Genehmigung innerhalb der erforderlichen Zeitrahmen nicht eingeholt werden kann. |   2   |   D   |
| 13.2.4 | Überprüfen Sie, ob Eskalationsverfahren klare Autoritätsebenen für verschiedene Entscheidungstypen oder Risikokategorien definieren, falls zutreffend.                                        |   3   |  D/V  |

---

## C13.3 Verantwortlichkeitskette & Prüfbarkeit

Protokollieren Sie Bedieneraktionen und Modellentscheidungen.

|   #    | Beschreibung                                                                                                                                                                    | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.3.1 | Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und menschliche Eingriffe mit Zeitstempeln, Benutzeridentitäten und Entscheidungsbegründungen protokolliert werden. |   1   |  D/V  |
| 13.3.2 | Stellen Sie sicher, dass Prüfprotokolle nicht manipuliert werden können und Integritätsprüfmechanismen enthalten.                                                               |   2   |   D   |

---

## C13.4 Erklärbare KI-Techniken

Oberflächenmerkmal-Wichtigkeit, Gegenfaktische und lokale Erklärungen.

|   #    | Beschreibung                                                                                                                                                                                    | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.4.1 | Stellen Sie sicher, dass KI-Systeme grundlegende Erklärungen für ihre Entscheidungen in einem für Menschen lesbaren Format liefern.                                                             |   1   |  D/V  |
| 13.4.2 | Stellen Sie sicher, dass die Qualität der Erklärungen durch menschliche Evaluationsstudien und Metriken validiert wird.                                                                         |   2   |   V   |
| 13.4.3 | Stellen Sie sicher, dass für kritische Entscheidungen Merkmalswichtigkeitswerte oder Attributionsmethoden (SHAP, LIME usw.) verfügbar sind.                                                     |   3   |  D/V  |
| 13.4.4 | Überprüfen Sie, dass kontrafaktische Erklärungen zeigen, wie Eingaben modifiziert werden könnten, um Ergebnisse zu verändern, sofern dies für den Anwendungsfall und die Domäne zutreffend ist. |   3   |   V   |

---

## C13.5 Modellkarten & Verwendungshinweise

Pflegen Sie Model Cards für den vorgesehenen Gebrauch, Leistungskennzahlen und ethische Überlegungen.

|   #    | Beschreibung                                                                                                                                                                                                           | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.5.1 | Stellen Sie sicher, dass Modelldokumentationen die vorgesehenen Anwendungsfälle, Einschränkungen und bekannten Ausfallmodi beschreiben.                                                                                |   1   |   D   |
| 13.5.2 | Stellen Sie sicher, dass Leistungskennzahlen für verschiedene anwendbare Anwendungsfälle offengelegt werden.                                                                                                           |   1   |  D/V  |
| 13.5.3 | Stellen Sie sicher, dass ethische Überlegungen, Bias-Bewertungen, Fairness-Evaluierungen, Merkmale der Trainingsdaten und bekannte Einschränkungen der Trainingsdaten dokumentiert und regelmäßig aktualisiert werden. |   2   |   D   |
| 13.5.4 | Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und während des gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.                                                                   |   2   |  D/V  |

---

## C13.6 Unsicherheitsquantifizierung

Verbreiten Sie Konfidenzwerte oder Entropie-Messungen in Antworten.

|   #    | Beschreibung                                                                                                                     | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.6.1 | Überprüfen Sie, ob KI-Systeme Vertrauenswerte oder Unsicherheitsmaße zusammen mit ihren Ausgaben bereitstellen.                  |   1   |   D   |
| 13.6.2 | Überprüfen Sie, ob Unsicherheitsschwellen eine zusätzliche menschliche Überprüfung oder alternative Entscheidungswege auslösen.  |   2   |  D/V  |
| 13.6.3 | Überprüfen Sie, ob Unsicherheitsquantifizierungsmethoden kalibriert und anhand von Grundwahrscheinlichkeitsdaten validiert sind. |   2   |   V   |
| 13.6.4 | Stellen Sie sicher, dass die Unsicherheitsfortpflanzung durch mehrstufige KI-Workflows erhalten bleibt.                          |   3   |  D/V  |

---

## C13.7 Nutzerorientierte Transparenzberichte

Geben Sie regelmäßige Offenlegungen zu Vorfällen, Drift und Datennutzung.

|   #    | Beschreibung                                                                                                                                                        | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.7.1 | Stellen Sie sicher, dass die Richtlinien zur Datennutzung und die Praktiken zur Verwaltung der Einwilligung der Nutzer klar an die Stakeholder kommuniziert werden. |   1   |  D/V  |
| 13.7.2 | Überprüfen Sie, dass KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in den Berichten enthalten sind.                                              |   2   |  D/V  |
| 13.7.3 | Stellen Sie sicher, dass regelmäßig veröffentlichte Transparenzberichte AI-Zwischenfälle und betriebliche Metriken in angemessenem Umfang offenlegen.               |   2   |  D/V  |

### Referenzen

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

