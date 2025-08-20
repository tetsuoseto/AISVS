# C13 Menschliche Aufsicht, Verantwortlichkeit & Governance

## Kontrollziel

Dieses Kapitel legt Anforderungen für die Aufrechterhaltung menschlicher Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen fest und gewährleistet Erklärbarkeit, Transparenz sowie ethische Verwaltung während des gesamten KI-Lebenszyklus.

---

## C13.1 Not-Aus- und Übersteuerungsmechanismen

Stellen Sie Abschalt- oder Rücksetzpfade bereit, wenn unsicheres Verhalten des KI-Systems beobachtet wird.

|   #    | Beschreibung                                                                                                                            | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.1.1 | Stellen Sie sicher, dass ein manueller Not-Aus-Mechanismus vorhanden ist, um die Inferenz und Ausgabe des KI-Modells sofort zu stoppen. |   1   |  D/V  |
| 13.1.2 | Stellen Sie sicher, dass Übersteuerungskontrollen nur für autorisiertes Personal zugänglich sind.                                       |   1   |   D   |
| 13.1.3 | Überprüfen Sie, ob Rücksetzverfahren auf frühere Modellversionen oder den sicheren Betriebsmodus zurücksetzen können.                   |   3   |  D/V  |
| 13.1.4 | Stellen Sie sicher, dass Überschreibemechanismen regelmäßig getestet werden.                                                            |   3   |   V   |

---

## C13.2 Mensch-in-der-Schleife Entscheidungs-Checkpoint

Erfordern Sie menschliche Genehmigungen, wenn die Einsätze vordefinierte Risikoschwellen überschreiten.

|   #    | Beschreibung                                                                                                                                                                                | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.2.1 | Vergewissern Sie sich, dass risikoreiche KI-Entscheidungen vor der Ausführung eine ausdrückliche menschliche Genehmigung erfordern.                                                         |   1   |  D/V  |
| 13.2.2 | Stellen Sie sicher, dass Risikoschwellenwerte klar definiert sind und automatisch menschliche Prüfprozesse auslösen.                                                                        |   1   |   D   |
| 13.2.3 | Stellen Sie sicher, dass zeitkritische Entscheidungen über Ausweichverfahren verfügen, falls eine menschliche Genehmigung nicht innerhalb der erforderlichen Fristen eingeholt werden kann. |   2   |   D   |
| 13.2.4 | Überprüfen Sie, ob Eskalationsverfahren klare Autoritätsebenen für verschiedene Entscheidungstypen oder Risikokategorien definieren, falls zutreffend.                                      |   3   |  D/V  |

---

## C13.3 Kette der Verantwortlichkeit & Prüfbarkeit

Protokollieren Sie Operatoraktionen und Modellentscheidungen.

|   #    | Beschreibung                                                                                                                                                                    | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.3.1 | Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und menschliche Eingriffe mit Zeitstempeln, Benutzeridentitäten und Entscheidungsbegründungen protokolliert werden. |   1   |  D/V  |
| 13.3.2 | Stellen Sie sicher, dass Audit-Protokolle nicht manipuliert werden können und Integritätsprüfmechanismen enthalten.                                                             |   2   |   D   |

---

## C13.4 Erklärbare KI-Techniken

Oberflächenmerkmal-Wichtigkeit, Gegenfaktische und lokale Erklärungen.

|   #    | Beschreibung                                                                                                                                                                        | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.4.1 | Stellen Sie sicher, dass KI-Systeme grundlegende Erklärungen für ihre Entscheidungen in einem für Menschen lesbaren Format bereitstellen.                                           |   1   |  D/V  |
| 13.4.2 | Stellen Sie sicher, dass die Qualität der Erklärungen durch menschliche Evaluationsstudien und Metriken validiert wird.                                                             |   2   |   V   |
| 13.4.3 | Überprüfen Sie, ob Feature-Importance-Werte oder Attributionsmethoden (SHAP, LIME usw.) für kritische Entscheidungen verfügbar sind.                                                |   3   |  D/V  |
| 13.4.4 | Überprüfen Sie, ob kontrafaktische Erklärungen zeigen, wie Eingaben modifiziert werden könnten, um Ergebnisse zu ändern, falls dies auf den Anwendungsfall und die Domäne zutrifft. |   3   |   V   |

---

## C13.5 Modellkarten & Nutzungsangaben

Pflegen Sie Modelldokumentationen für den vorgesehenen Gebrauch, Leistungskennzahlen und ethische Überlegungen.

|   #    | Beschreibung                                                                                                                                                                                                                | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.5.1 | Überprüfen Sie, ob Modellkarten die vorgesehenen Anwendungsfälle, Einschränkungen und bekannten Ausfallmodi dokumentieren.                                                                                                  |   1   |   D   |
| 13.5.2 | Stellen Sie sicher, dass Leistungskennzahlen für verschiedene anwendbare Anwendungsfälle offengelegt werden.                                                                                                                |   1   |  D/V  |
| 13.5.3 | Stellen Sie sicher, dass ethische Überlegungen, Bias-Bewertungen, Fairness-Evaluierungen, Eigenschaften der Trainingsdaten und bekannte Einschränkungen der Trainingsdaten dokumentiert und regelmäßig aktualisiert werden. |   2   |   D   |
| 13.5.4 | Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und im gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.                                                                                 |   2   |  D/V  |

---

## C13.6 Unsicherheitsquantifizierung

Verbreiten Sie Konfidenzwahrscheinlichkeiten oder Entropie-Messungen in den Antworten.

|   #    | Beschreibung                                                                                                                      | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.6.1 | Überprüfen Sie, ob KI-Systeme mit ihren Ausgaben Vertrauenswerte oder Unsicherheitsmaße bereitstellen.                            |   1   |   D   |
| 13.6.2 | Überprüfen Sie, ob Unsicherheitsschwellen zusätzliche menschliche Überprüfungen oder alternative Entscheidungswege auslösen.      |   2   |  D/V  |
| 13.6.3 | Überprüfen Sie, ob Methoden zur Unsicherheitsquantifizierung kalibriert sind und anhand von tatsächlichen Daten validiert wurden. |   2   |   V   |
| 13.6.4 | Stellen Sie sicher, dass die Unsicherheitsfortpflanzung durch mehrstufige KI-Workflows erhalten bleibt.                           |   3   |  D/V  |

---

## C13.7 Benutzerorientierte Transparenzberichte

Stellen Sie regelmäßige Offenlegungen zu Vorfällen, Drift und Datennutzung bereit.

|   #    | Beschreibung                                                                                                                                                    | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.7.1 | Stellen Sie sicher, dass die Richtlinien zur Datennutzung und die Praktiken des Nutzerzustimmungsmanagements klar an die Interessengruppen kommuniziert werden. |   1   |  D/V  |
| 13.7.2 | Stellen Sie sicher, dass KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in den Berichten enthalten sind.                                      |   2   |  D/V  |
| 13.7.3 | Stellen Sie sicher, dass regelmäßig veröffentlichte Transparenzberichte KI-Vorfälle und Betriebsmessgrößen in angemessenem Detailgrad offenlegen.               |   2   |  D/V  |

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

