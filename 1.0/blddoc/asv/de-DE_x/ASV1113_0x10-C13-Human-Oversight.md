# C13 Menschliche Aufsicht, Verantwortlichkeit und Governance

## Kontrollziel

Dieses Kapitel enthält Anforderungen zur Aufrechterhaltung menschlicher Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen und gewährleistet Erklärbarkeit, Transparenz und ethische Verantwortung während des gesamten KI-Lebenszyklus.

---

## C13.1 Not-Aus-Schalter & Übersteuerungsmechanismen

Stellen Sie bei Beobachtung eines unsicheren Verhaltens des KI-Systems Abschalt- oder Rückrollpfade bereit.

|   #    | Beschreibung                                                                                                                  | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.1.1 | Überprüfen Sie, ob ein manueller Not-Aus-Mechanismus vorhanden ist, um die KI-Modell-Inferenz und Ausgaben sofort zu stoppen. |   1    |  D/V  |
| 13.1.2 | Überprüfen Sie, dass Override-Kontrollen nur für autorisiertes Personal zugänglich sind.                                      |   1    |   D   |
| 13.1.3 | Stellen Sie sicher, dass Rücksetzverfahren auf vorherige Modellversionen oder den sicheren Betriebsmodus zurückkehren können. |   3    |  D/V  |
| 13.1.4 | Stellen Sie sicher, dass Übersteuerungsmechanismen regelmäßig getestet werden.                                                |   3    |   V   |

---

## C13.2 Mensch-in-der-Schleife Entscheidungs-Kontrollpunkte

Erfordern Sie menschliche Genehmigungen, wenn Einsätze vordefinierte Risikoschwellen überschreiten.

|   #    | Beschreibung                                                                                                                                                                          | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.2.1 | Stellen Sie sicher, dass KI-Entscheidungen mit hohem Risiko vor der Ausführung eine ausdrückliche menschliche Genehmigung erfordern.                                                  |   1    |  D/V  |
| 13.2.2 | Stellen Sie sicher, dass Risikoschwellenwerte klar definiert sind und automatisch menschliche Überprüfungsarbeitsabläufe auslösen.                                                    |   1    |   D   |
| 13.2.3 | Stellen Sie sicher, dass zeitkritische Entscheidungen Ausweichverfahren haben, wenn eine menschliche Genehmigung nicht innerhalb der erforderlichen Zeitrahmen eingeholt werden kann. |   2    |   D   |
| 13.2.4 | Stellen Sie sicher, dass Eskalationsverfahren klare Autoritätsebenen für verschiedene Entscheidungstypen oder Risikokategorien definieren, sofern zutreffend.                         |   3    |  D/V  |

---

## C13.3 Verantwortlichkeitskette & Prüfbarkeit

Protokollieren Sie Operatoraktionen und Modellentscheidungen.

|   #    | Beschreibung                                                                                                                                                                    | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.3.1 | Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und menschliche Eingriffe mit Zeitstempeln, Benutzeridentitäten und Entscheidungsbegründungen protokolliert werden. |   1    |  D/V  |
| 13.3.2 | Stellen Sie sicher, dass Prüfprotokolle nicht manipuliert werden können und Integritätsüberprüfungsmechanismen enthalten.                                                       |   2    |   D   |

---

## C13.4 Erklärbare KI-Techniken

Oberflächenmerkmalbedeutung, kontrafaktische Analysen und lokale Erklärungen.

|   #    | Beschreibung                                                                                                                                                                            | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.4.1 | Stellen Sie sicher, dass KI-Systeme grundlegende Erklärungen für ihre Entscheidungen in menschenlesbarem Format liefern.                                                                |   1    |  D/V  |
| 13.4.2 | Stellen Sie sicher, dass die Qualität der Erklärung durch menschliche Evaluationsstudien und Metriken validiert wird.                                                                   |   2    |   V   |
| 13.4.3 | Stellen Sie sicher, dass Wichtigkeitsscores für Merkmale oder Attributionsmethoden (SHAP, LIME usw.) für kritische Entscheidungen verfügbar sind.                                       |   3    |  D/V  |
| 13.4.4 | Überprüfen Sie, ob kontrafaktische Erklärungen aufzeigen, wie Eingaben modifiziert werden könnten, um Ergebnisse zu ändern, sofern dies für den Anwendungsfall und die Domäne zutrifft. |   3    |   V   |

---

## C13.5 Modellkarten & Nutzungsangaben

Pflegen Sie Modellkarten für den beabsichtigten Gebrauch, Leistungskennzahlen und ethische Überlegungen.

|   #    | Beschreibung                                                                                                                                                                                                     | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.5.1 | Überprüfen Sie, ob Modellkarten die vorgesehenen Anwendungsfälle, Einschränkungen und bekannte Ausfallmodi dokumentieren.                                                                                        |   1    |   D   |
| 13.5.2 | Stellen Sie sicher, dass Leistungskennzahlen für verschiedene anwendbare Anwendungsfälle offengelegt werden.                                                                                                     |   1    |  D/V  |
| 13.5.3 | Stellen Sie sicher, dass ethische Überlegungen, Bias-Bewertungen, Fairness-Evaluierungen, Merkmale der Trainingsdaten und bekannte Trainingsdatenbeschränkungen dokumentiert und regelmäßig aktualisiert werden. |   2    |   D   |
| 13.5.4 | Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und während des gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.                                                             |   2    |  D/V  |

---

## C13.6 Unsicherheitsquantifizierung

Verbreiten Sie Konfidenzwerte oder Entropiemessungen in den Antworten.

|   #    | Beschreibung                                                                                                                     | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.6.1 | Verifizieren Sie, dass KI-Systeme ihren Ausgaben Vertrauenswerte oder Unsicherheitsmaße bereitstellen.                           |   1    |   D   |
| 13.6.2 | Überprüfen Sie, ob Unsicherheitsschwellen zusätzliche menschliche Überprüfungen oder alternative Entscheidungswege auslösen.     |   2    |  D/V  |
| 13.6.3 | Überprüfen Sie, ob Methoden zur Unsicherheitsquantifizierung kalibriert sind und anhand von Ground-Truth-Daten validiert wurden. |   2    |   V   |
| 13.6.4 | Stellen Sie sicher, dass die Unsicherheitsfortpflanzung in mehrstufigen KI-Workflows beibehalten wird.                           |   3    |  D/V  |

---

## C13.7 Transparenzberichte für Benutzer

Stellen Sie regelmäßige Offenlegungen zu Vorfällen, Abweichungen und Datennutzung bereit.

|   #    | Beschreibung                                                                                                                                                | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 13.7.1 | Stellen Sie sicher, dass die Richtlinien zur Datennutzung und die Verfahren zum Management der Benutzerzustimmung den Beteiligten klar kommuniziert werden. |   1    |  D/V  |
| 13.7.2 | Stellen Sie sicher, dass KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in die Berichterstattung aufgenommen werden.                      |   2    |  D/V  |
| 13.7.3 | Überprüfen Sie, ob regelmäßig veröffentlichte Transparenzberichte KI-Vorfälle und Betriebskennzahlen in angemessenem Detailgrad offenlegen.                 |   2    |  D/V  |

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

