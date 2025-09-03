# C13 menschliche Aufsicht, Rechenschaftspflicht und Governance

## Kontrollziel

Dieses Kapitel definiert Anforderungen zur Aufrechterhaltung menschlicher Aufsicht und klarer Verantwortlichkeitsketten in KI-Systemen, um Erklärbarkeit, Transparenz und ethische Verantwortungsführung über den gesamten Lebenszyklus der KI sicherzustellen.

---

## C13.1 Kill-Switch & Override-Mechanismen

Stellen Sie Abschalt- oder Rollback-Pfade bereit, wenn unsicheres Verhalten des KI-Systems beobachtet wird.

|   #    | Beschreibung                                                                                                                            | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.1.1 | Überprüfen Sie, ob ein manueller Kill-Switch-Mechanismus vorhanden ist, der die Inferenz des KI-Modells und die Ausgaben sofort stoppt. |   1   |  D/V  |
| 13.1.2 | Vergewissern Sie sich, dass die Override-Steuerungen nur für autorisiertes Personal zugänglich sind.                                    |   1   |   D   |
| 13.1.3 | Überprüfen Sie, ob Rollback-Verfahren auf frühere Modellversionen zurückgesetzt werden können oder im sicheren Modus funktionieren.     |   3   |  D/V  |
| 13.1.4 | Stellen Sie sicher, dass Override-Mechanismen regelmäßig getestet werden.                                                               |   3   |   V   |

---

## C13.2 Mensch-in-der-Schleife-Entscheidungspunkte

Menschliche Genehmigungen sind erforderlich, wenn die Einsätze vordefinierten Risikoschwellen überschreiten.

|   #    | Beschreibung                                                                                                                                                                 | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.2.1 | Stellen Sie sicher, dass hochriskante KI-Entscheidungen eine ausdrückliche menschliche Freigabe vor der Ausführung erfordern.                                                |   1   |  D/V  |
| 13.2.2 | Stellen Sie sicher, dass Risikoschwellen klar definiert sind und automatisch menschliche Prüfungs-Workflows auslösen.                                                        |   1   |   D   |
| 13.2.3 | Überprüfen Sie, ob zeitkritische Entscheidungen Fallback-Verfahren haben, wenn menschliche Genehmigungen innerhalb der erforderlichen Fristen nicht eingeholt werden können. |   2   |   D   |
| 13.2.4 | Überprüfen Sie, ob Eskalationsverfahren klare Autoritätsebenen für verschiedene Entscheidungsarten oder Risikokategorien definieren, falls zutreffend.                       |   3   |  D/V  |

---

## C13.3 Verantwortungskette und Auditierbarkeit

Protokollieren Sie Bedieneraktionen und Modellentscheidungen.

|   #    | Beschreibung                                                                                                                                                                                | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.3.1 | Stellen Sie sicher, dass alle Entscheidungen des KI-Systems und alle menschlichen Eingriffe mit Zeitstempeln, Benutzeridentitäten und Begründungen der Entscheidungen protokolliert werden. |   1   |  D/V  |
| 13.3.2 | Stellen Sie sicher, dass Audit-Protokolle nicht manipuliert werden können, und dass Integritätsprüfmechanismen vorhanden sind.                                                              |   2   |   D   |

---

## C13.4 Erklärbare KI-Techniken

Wichtigkeit von Oberflächenmerkmalen, gegenfaktische Beispiele und lokale Erklärungen.

|   #    | Beschreibung                                                                                                                                                                            | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.4.1 | Überprüfen Sie, dass KI-Systeme grundlegende Erklärungen zu ihren Entscheidungen in einem menschenlesbaren Format liefern.                                                              |   1   |  D/V  |
| 13.4.2 | Stellen Sie sicher, dass die Erklärungsqualität durch menschliche Evaluationsstudien und Metriken validiert wird.                                                                       |   2   |   V   |
| 13.4.3 | Überprüfen Sie, ob Merkmalsbedeutungswerte oder Attributionsmethoden (SHAP, LIME usw.) für kritische Entscheidungen verfügbar sind.                                                     |   3   |  D/V  |
| 13.4.4 | Überprüfen Sie, ob kontrafaktische Erklärungen zeigen, wie Eingaben geändert werden könnten, um Ergebnisse zu beeinflussen, sofern dies auf den Anwendungsfall und die Domäne zutrifft. |   3   |   V   |

---

## C13.5 Modellkarten und Nutzungs-Offenlegungen

Pflegen Sie Modellkarten für die beabsichtigte Verwendung, Leistungskennzahlen und ethische Überlegungen.

|   #    | Beschreibung                                                                                                                                                                                                                   | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 13.5.1 | Stellen Sie sicher, dass Modellkarten beabsichtigte Anwendungsfälle, Einschränkungen und bekannte Fehlermodi dokumentieren.                                                                                                    |   1   |   D   |
| 13.5.2 | Überprüfen Sie, ob Leistungskennzahlen über verschiedene anwendbare Anwendungsfälle offengelegt werden.                                                                                                                        |   1   |  D/V  |
| 13.5.3 | Stellen Sie sicher, dass ethische Überlegungen, Verzerrungsbewertungen, Fairnessbewertungen, Eigenschaften der Trainingsdaten und bekannte Einschränkungen der Trainingsdaten dokumentiert und regelmäßig aktualisiert werden. |   2   |   D   |
| 13.5.4 | Stellen Sie sicher, dass Modellkarten versionskontrolliert sind und während des gesamten Modelllebenszyklus mit Änderungsverfolgung gepflegt werden.                                                                           |   2   |  D/V  |

---

## C13.6 Quantifizierung der Unsicherheit

Geben Sie in Antworten Konfidenzwerte oder Entropiemessungen an.

|   #    | Beschreibung                                                                                                                                | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.6.1 | Stellen Sie sicher, dass KI-Systeme Konfidenzwerte oder Unsicherheitsmaße mit ihren Ausgaben liefern.                                       |   1   |   D   |
| 13.6.2 | Stellen Sie sicher, dass Unsicherheits-Schwellenwerte eine zusätzliche menschliche Überprüfung oder alternative Entscheidungswege auslösen. |   2   |  D/V  |
| 13.6.3 | Stellen Sie sicher, dass Methoden der Unsicherheitsquantifizierung gegenüber Ground-Truth-Daten kalibriert und validiert werden.            |   2   |   V   |
| 13.6.4 | Überprüfen Sie, ob die Unsicherheitsausbreitung in mehrstufigen KI-Arbeitsabläufen erhalten bleibt.                                         |   3   |  D/V  |

---

## C13.7 Benutzerorientierte Transparenzberichte

Regelmäßige Offenlegungen zu Vorfällen, Drift und Datennutzung bereitstellen.

|   #    | Beschreibung                                                                                                                                        | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 13.7.1 | Überprüfen Sie, ob Datenverwendungsrichtlinien und Praktiken zur Verwaltung von Benutzereinwilligungen den Stakeholdern deutlich mitgeteilt werden. |   1   |  D/V  |
| 13.7.2 | Überprüfen Sie, dass KI-Auswirkungsbewertungen durchgeführt werden und die Ergebnisse in den Bericht aufgenommen werden.                            |   2   |  D/V  |
| 13.7.3 | Überprüfen Sie, ob regelmäßig veröffentlichte Transparenzberichte KI-Vorfälle und Betriebskennzahlen in angemessener Detailtiefe offenlegen.        |   2   |  D/V  |

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

