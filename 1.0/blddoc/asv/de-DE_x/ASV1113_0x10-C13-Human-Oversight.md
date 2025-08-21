# C13 Menschliche Aufsicht, Verantwortlichkeit & Governance

## Steuerungsziel

Dieses Kapitel enthält Anforderungen zur Aufrechterhaltung der menschlichen Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen, um Erklärbarkeit, Transparenz und ethische Steuerung über den gesamten Lebenszyklus der KI sicherzustellen.

---

## C13.1 Notschalter- und Übersteuerungsmechanismen

Stellen Sie Abschalt- oder Rücksetzwege bereit, wenn ein unsicheres Verhalten des KI-Systems festgestellt wird.

|   #    | Beschreibung                                                                                                                     | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.1.1 | Überprüfen Sie, ob ein manueller Not-Aus-Mechanismus vorhanden ist, um die KI-Modell-Inferenz und die Ausgabe sofort zu stoppen. |   1   |  D/V  |
| 13.1.2 | Stellen Sie sicher, dass die Überschreibungssteuerungen nur für autorisiertes Personal zugänglich sind.                          |   1   |   D   |
| 13.1.3 | Überprüfen Sie, ob Rollback-Verfahren auf vorherige Modellversionen oder sicheren Betriebsmodi zurückgesetzt werden können.      |   3   |  D/V  |
| 13.1.4 | Stellen Sie sicher, dass Überschreibemechanismen regelmäßig getestet werden.                                                     |   3   |   V   |

---

## C13.2 Mensch-in-der-Schleife Entscheidungs-Kontrollpunkte

Menschliche Genehmigungen erforderlich, wenn Einsätze vordefinierte Risikoschwellen überschreiten.

|   #    | Beschreibung                                                                                                                                                              | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.2.1 | Stellen Sie sicher, dass KI-Entscheidungen mit hohem Risiko vor der Ausführung eine ausdrückliche menschliche Genehmigung erfordern.                                      |   1   |  D/V  |
| 13.2.2 | Stellen Sie sicher, dass Risiko-Schwellenwerte klar definiert sind und automatisch menschliche Überprüfungsabläufe auslösen.                                              |   1   |   D   |
| 13.2.3 | Überprüfen Sie, ob zeitkritische Entscheidungen Rückfallverfahren haben, wenn innerhalb der erforderlichen Zeiträume keine menschliche Genehmigung eingeholt werden kann. |   2   |   D   |
| 13.2.4 | Stellen Sie sicher, dass Eskalationsverfahren klare Autoritätsstufen für verschiedene Entscheidungstypen oder Risikokategorien definieren, falls zutreffend.              |   3   |  D/V  |

---

## C13.3 Kette der Verantwortlichkeit & Prüfpfadfähigkeit

Protokollieren Sie Operatoraktionen und Modellentscheidungen.

|   #    | Beschreibung                                                                                                                                                                     | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.3.1 | Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und menschlichen Eingriffe mit Zeitstempeln, Benutzeridentitäten und Entscheidungsbegründungen protokolliert werden. |   1   |  D/V  |
| 13.3.2 | Stellen Sie sicher, dass Auditprotokolle nicht manipuliert werden können und Integritätsprüfmechanismen enthalten.                                                               |   2   |   D   |

---

## C13.4 Erklärbare KI-Techniken

Oberflächen-Feature-Wichtigkeit, Gegenfaktische und lokale Erklärungen.

|   #    | Beschreibung                                                                                                                                                                               | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 13.4.1 | Stellen Sie sicher, dass KI-Systeme grundlegende Erklärungen für ihre Entscheidungen in einem für Menschen lesbaren Format bereitstellen.                                                  |   1   |  D/V  |
| 13.4.2 | Stellen Sie sicher, dass die Qualität der Erklärung durch menschliche Evaluationsstudien und Metriken validiert wird.                                                                      |   2   |   V   |
| 13.4.3 | Verifizieren Sie, dass Merkmalswichtungswerte oder Attributionsmethoden (SHAP, LIME usw.) für kritische Entscheidungen verfügbar sind.                                                     |   3   |  D/V  |
| 13.4.4 | Überprüfen Sie, ob kontrafaktische Erklärungen zeigen, wie Eingaben modifiziert werden könnten, um Ergebnisse zu ändern, sofern dies für den Anwendungsfall und die Domäne zutreffend ist. |   3   |   V   |

---

## C13.5 Modellkarten & Nutzungshinweise

Führen Sie Modellkarten für den beabsichtigten Einsatz, Leistungskennzahlen und ethische Überlegungen.

|   #    | Beschreibung                                                                                                                                                                                                           | Ebene | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.5.1 | Stellen Sie sicher, dass Modellkarten die beabsichtigten Anwendungsfälle, Einschränkungen und bekannten Ausfallmodi dokumentieren.                                                                                     |   1   |   D   |
| 13.5.2 | Stellen Sie sicher, dass Leistungskennzahlen für verschiedene anwendbare Anwendungsfälle offengelegt werden.                                                                                                           |   1   |  D/V  |
| 13.5.3 | Stellen Sie sicher, dass ethische Überlegungen, Bias-Bewertungen, Fairness-Evaluierungen, Merkmale der Trainingsdaten und bekannte Einschränkungen der Trainingsdaten dokumentiert und regelmäßig aktualisiert werden. |   2   |   D   |
| 13.5.4 | Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und während des gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.                                                                   |   2   |  D/V  |

---

## C13.6 Unsicherheitsquantifizierung

Verbreiten Sie Vertrauenswerte oder Entropiemaße in den Antworten.

|   #    | Beschreibung                                                                                                                     | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.6.1 | Stellen Sie sicher, dass KI-Systeme mit ihren Ausgaben Vertrauenswerte oder Unsicherheitsmaße bereitstellen.                     |   1   |   D   |
| 13.6.2 | Überprüfen Sie, ob Unsicherheitsschwellen zusätzliche menschliche Überprüfungen oder alternative Entscheidungswege auslösen.     |   2   |  D/V  |
| 13.6.3 | Verifizieren Sie, dass Methoden zur Quantifizierung von Unsicherheiten kalibriert und anhand von Referenzdaten validiert werden. |   2   |   V   |
| 13.6.4 | Stellen Sie sicher, dass die Unsicherheitsfortpflanzung in mehrstufigen KI-Workflows erhalten bleibt.                            |   3   |  D/V  |

---

## C13.7 Transparenzberichte für Endnutzer

Stellen Sie regelmäßige Offenlegungen zu Vorfällen, Drift und Datennutzung bereit.

|   #    | Beschreibung                                                                                                                                        | Ebene | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.7.1 | Stellen Sie sicher, dass Datenschutzrichtlinien und Praktiken zum Management der Benutzerzustimmung den Interessengruppen klar kommuniziert werden. |   1   |  D/V  |
| 13.7.2 | Überprüfen Sie, ob KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in den Berichten enthalten sind.                                |   2   |  D/V  |
| 13.7.3 | Überprüfen Sie, ob regelmäßig veröffentlichte Transparenzberichte KI-Vorfälle und Betriebskennzahlen in angemessenem Detail offenlegen.             |   2   |  D/V  |

### Literaturverzeichnis

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

