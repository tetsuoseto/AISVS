# 10 Gegnerschaftliche Robustheit & Datenschutzverteidigung

## Kontrollziel

Stellen Sie sicher, dass KI-Modelle auch bei Umgehungs-, Rückschluss-, Extraktions- oder Vergiftungsangriffen zuverlässig, datenschutzwahrend und missbrauchsresistent bleiben.

---

## 10.1 Modellabstimmung & Sicherheit

Schützen Sie vor schädlichen oder gegen Richtlinien verstoßenden Ausgaben.

|   #    | Beschreibung                                                                                                                                                                           | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.1.1 | Stellen Sie sicher, dass ein Alignment-Testset (Red-Team-Eingabeaufforderungen, Jailbreak-Prüfungen, nicht erlaubte Inhalte) versioniert und bei jeder Modellfreigabe ausgeführt wird. |   1   |  D/V  |
| 10.1.2 | Überprüfen Sie, ob Verweigerungs- und sichere Abschluss-Schutzmaßnahmen durchgesetzt werden.                                                                                           |   1   |   D   |
| 10.1.3 | Überprüfen Sie, ob ein automatisierter Evaluator die Rate schädlicher Inhalte misst und Rückschritte über eine festgelegte Schwelle hinaus markiert.                                   |   2   |  D/V  |
| 10.1.4 | Stellen Sie sicher, dass das Training zur Gegen-Jailbreak-Maßnahme dokumentiert und reproduzierbar ist.                                                                                |   2   |   D   |
| 10.1.5 | Überprüfen Sie, ob formale Nachweise der Einhaltung von Richtlinien oder zertifizierte Überwachungen kritische Bereiche abdecken.                                                      |   3   |   V   |

---

## 10.2 Härtung gegen adversarielle Beispiele

Erhöhen Sie die Resilienz gegenüber manipulierten Eingaben. Robustes adversariales Training und Benchmark-Bewertung sind die derzeit besten Praktiken.

|   #    | Beschreibung                                                                                                                                     | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 10.2.1 | Überprüfen Sie, ob Projekt-Repositorien adversariale Trainingskonfigurationen mit reproduzierbaren Seeds enthalten.                              |   1   |   D   |
| 10.2.2 | Überprüfen Sie, ob die Erkennung adversarialer Beispiele in Produktionspipelines Blockierungswarnungen auslöst.                                  |   2   |  D/V  |
| 10.2.4 | Verifizieren Sie, dass zertifizierte Robustheitsnachweise oder Intervallgrenzzertifikate mindestens die wichtigsten kritischen Klassen abdecken. |   3   |   V   |
| 10.2.5 | Überprüfen Sie, dass Regressionstests adaptive Angriffe verwenden, um keinen messbaren Verlust an Robustheit zu bestätigen.                      |   3   |   V   |

---

## 10.3 Maßnahmen zur Minderung von Mitgliedschafts-Inferenz

Begrenzen Sie die Möglichkeit zu entscheiden, ob ein Datensatz im Trainingsmaterial enthalten war. Differentielle Privatsphäre und das Maskieren von Vertrauensscores bleiben die effektivsten bekannten Schutzmaßnahmen.

|   #    | Beschreibung                                                                                                                        | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.3.1 | Überprüfen Sie, ob die Entropieregulierung pro Abfrage oder die Temperaturskalierung übermäßig selbstsichere Vorhersagen reduziert. |   1   |   D   |
| 10.3.2 | Stellen Sie sicher, dass das Training eine ε-beschränkte differentielle Datenschutz-Optimierung für sensible Datensätze verwendet.  |   2   |   D   |
| 10.3.3 | Überprüfen Sie, dass Angriffssimulationen (Shadow-Modell oder Blackbox) einen Angriff-AUC ≤ 0,60 auf zurückgehaltenen Daten zeigen. |   2   |   V   |

---

## 10.4 Modell-Inversionsresistenz

Verhindern Sie die Rekonstruktion privater Attribute. Aktuelle Umfragen heben die Ausgabekürzung und DP-Garantien als praktische Schutzmaßnahmen hervor.

|   #    | Beschreibung                                                                                                                                             | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.4.1 | Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; falls erforderlich, verwenden Sie Kategorien oder Einweg-Transformationen. |   1   |   D   |
| 10.4.2 | Überprüfen Sie, ob die Abfrage-Ratenbegrenzungen wiederholte adaptive Abfragen vom selben Principal drosseln.                                            |   1   |  D/V  |
| 10.4.3 | Überprüfen Sie, ob das Modell mit datenschutzwahrendem Rauschen trainiert wurde.                                                                         |   2   |   D   |

---

## 10.5 Modell-Extraktionsabwehr

Erkennen und Verhindern unautorisierter Klonungen. Wasserzeichen und Abfrage-Musteranalyse werden empfohlen.

|   #    | Beschreibung                                                                                                                                                                | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.5.1 | Überprüfen Sie, dass Inferenz-Gateways globale und pro-API-Schlüssel festgelegte Ratenbegrenzungen durchsetzen, die an die Memorierungsschwelle des Modells angepasst sind. |   1   |   D   |
| 10.5.2 | Überprüfen Sie, dass die Statistik der Abfrage-Entropie und der Eingabe-Mehrzahl eine automatisierte Extraktionsdetektion speisen.                                          |   2   |  D/V  |
| 10.5.3 | Überprüfen Sie, dass fragile oder probabilistische Wasserzeichen mit p < 0,01 in ≤ 1 000 Abfragen gegen einen verdächtigen Klon nachgewiesen werden können.                 |   2   |   V   |
| 10.5.4 | Stellen Sie sicher, dass Wasserzeichen-Schlüssel und Auslöse-Sets in einem Hardware-Sicherheitsmodul gespeichert und jährlich rotiert werden.                               |   3   |   D   |
| 10.5.5 | Überprüfen Sie, ob Extraction-Alert-Ereignisse die beanstandeten Abfragen enthalten und in Incident-Response-Playbooks integriert sind.                                     |   3   |   V   |

---

## 10.6 Erkennung von zur Inferenzzeit vergifteten Daten

Identifizieren und Neutralisieren von mit Hintertüren verseuchten oder vergifteten Eingaben.

|   #    | Beschreibung                                                                                                                                                                          | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.6.1 | Stellen Sie sicher, dass Eingaben vor der Modellausführung durch einen Anomalieerkenner (z. B. STRIP, Konsistenzbewertung) geprüft werden.                                            |   1   |   D   |
| 10.6.2 | Stellen Sie sicher, dass die Schwellenwerte des Detektors an sauberen/verseuchten Validierungsdatensätzen angepasst sind, um weniger als 5 % falsch positive Ergebnisse zu erreichen. |   1   |   V   |
| 10.6.3 | Überprüfen Sie, ob als vergiftet gekennzeichnete Eingaben eine Soft-Blockierung und menschliche Prüfungsabläufe auslösen.                                                             |   2   |   D   |
| 10.6.4 | Verifizieren Sie, dass Detektoren mit adaptiven, triggerlosen Hintertür-Angriffen auf Stress getestet werden.                                                                         |   2   |   V   |
| 10.6.5 | Überprüfen Sie, ob Wirksamkeitsmetriken der Erkennung protokolliert und regelmäßig mit aktuellen Bedrohungsinformationen neu bewertet werden.                                         |   3   |   D   |

---

## 10.7 Dynamische Anpassung der Sicherheitsrichtlinie

Echtzeit-Sicherheitsrichtlinienaktualisierungen basierend auf Bedrohungsinformationen und Verhaltensanalysen.

|   #    | Beschreibung                                                                                                                                                                          | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.7.1 | Überprüfen Sie, dass Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne den Agenten neu zu starten, und dabei die Integrität der Richtlinienversion gewahrt bleibt.    |   1   |  D/V  |
| 10.7.2 | Überprüfen Sie, dass Richtlinienaktualisierungen kryptographisch von autorisiertem Sicherheitspersonal signiert und vor der Anwendung validiert werden.                               |   2   |  D/V  |
| 10.7.3 | Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Prüfpfaden protokolliert werden, einschließlich Begründung, Genehmigungsketten und Rücksetzungsverfahren. |   2   |  D/V  |
| 10.7.4 | Überprüfen Sie, ob adaptive Sicherheitsmechanismen die Sensitivität der Bedrohungserkennung basierend auf dem Risikokontext und Verhaltensmustern anpassen.                           |   3   |  D/V  |
| 10.7.5 | Stellen Sie sicher, dass Entscheidungen zur Richtlinienanpassung erklärbar sind und Beweispfade für die Überprüfung durch das Sicherheitsteam enthalten.                              |   3   |  D/V  |

---

## 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch Agenten-Selbstreflexion und metakognitive Analyse.

|   #    | Beschreibung                                                                                                                                                         | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.8.1 | Verifizieren Sie, dass Agenten-Reflexionsmechanismen eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen beinhalten.                       |   1   |  D/V  |
| 10.8.2 | Stellen Sie sicher, dass Reflexionsausgaben validiert werden, um die Manipulation von Selbstbewertungsmechanismen durch feindliche Eingaben zu verhindern.           |   2   |  D/V  |
| 10.8.3 | Überprüfen Sie, ob die metakognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulationen oder Beeinträchtigungen in den Denkprozessen von Agenten erkennt.   |   2   |  D/V  |
| 10.8.4 | Überprüfen Sie, ob sicherheitsbezogene Warnungen auf Reflection-Basis eine erweiterte Überwachung und potenzielle Workflows für menschliche Eingriffe auslösen.      |   3   |  D/V  |
| 10.8.5 | Stellen Sie sicher, dass kontinuierliches Lernen aus Sicherheitsreflexionen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu beeinträchtigen. |   3   |  D/V  |

---

## 10.9 Evolution & Selbstverbesserung Sicherheit

Sicherheitskontrollen für Agentensysteme, die zur Selbstmodifikation und Evolution fähig sind.

|   #    | Beschreibung                                                                                                                                                 | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 10.9.1 | Überprüfen Sie, dass Selbstmodifikationsfähigkeiten auf ausgewiesene sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.                     |   1   |  D/V  |
| 10.9.2 | Stellen Sie sicher, dass Entwicklungsvorschläge vor der Umsetzung einer Sicherheitsauswirkungsbewertung unterzogen werden.                                   |   2   |  D/V  |
| 10.9.3 | Überprüfen Sie, dass Selbstverbesserungsmechanismen Rückrollfunktionen mit Integritätsüberprüfung enthalten.                                                 |   2   |  D/V  |
| 10.9.4 | Überprüfen Sie, ob die Meta-Learning-Sicherheit manipulativem Eingreifen in Verbesserungsalgorithmen entgegenwirkt.                                          |   3   |  D/V  |
| 10.9.5 | Verifizieren Sie, dass rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mittels mathematischer Beweise für die Konvergenz. |   3   |  D/V  |

---

### Referenzen

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

