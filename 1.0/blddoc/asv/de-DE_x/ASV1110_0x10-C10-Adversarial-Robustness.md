# 10 Gegnerische Robustheit & Datenschutzabwehr

## Kontrollziel

Stellen Sie sicher, dass KI-Modelle zuverlässig, datenschutzwahrend und missbrauchsresistent bleiben, wenn sie Evasions-, Inferenz-, Extraktions- oder Vergiftungsangriffen ausgesetzt sind.

---

## 10.1 Modellabstimmung & Sicherheit

Schützen Sie vor schädlichen oder richtlinienwidrigen Ausgaben.

|   #    | Beschreibung                                                                                                                                                          | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.1.1 | Überprüfen Sie, ob ein Alignment-Testset (Red-Team-Prompts, Jailbreak-Sonden, nicht erlaubte Inhalte) versioniert wird und bei jeder Modellfreigabe ausgeführt wird.  |   1   |  D/V  |
| 10.1.2 | Überprüfen Sie, ob Ablehnungs- und sichere Abschluss-Schutzvorrichtungen durchgesetzt werden.                                                                         |   1   |   D   |
| 10.1.3 | Verifizieren Sie, dass ein automatischer Evaluator die Rate schädlicher Inhalte misst und Rückschritte, die einen festgelegten Schwellenwert überschreiten, markiert. |   2   |  D/V  |
| 10.1.4 | Stellen Sie sicher, dass das Counter-Jailbreak-Training dokumentiert und reproduzierbar ist.                                                                          |   2   |   D   |
| 10.1.5 | Stellen Sie sicher, dass förmliche Nachweise der Richtlinienkonformität oder zertifizierte Überwachungen kritische Bereiche abdecken.                                 |   3   |   V   |

---

## 10.2 Härtung gegen adversariale Beispiele

Erhöhen Sie die Widerstandsfähigkeit gegenüber manipulierten Eingaben. Robustes adversariales Training und Benchmark-Bewertungen sind derzeit die beste Praxis.

|   #    | Beschreibung                                                                                                                                       | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.2.1 | Überprüfen Sie, ob Projekt-Repositorien Konfigurationen für adversariales Training mit reproduzierbaren Seeds enthalten.                           |   1   |   D   |
| 10.2.2 | Überprüfen Sie, ob die Erkennung von adversarialen Beispielen in Produktionspipelines Blockierungswarnungen auslöst.                               |   2   |  D/V  |
| 10.2.4 | Stellen Sie sicher, dass zertifizierte Robustheitsnachweise oder Intervall-Grenzzertifikate zumindest die wichtigsten kritischen Klassen abdecken. |   3   |   V   |
| 10.2.5 | Überprüfen Sie, dass Regressionstests adaptive Angriffe verwenden, um einen nicht messbaren Robustheitsverlust zu bestätigen.                      |   3   |   V   |

---

## 10.3 Minderung von Mitgliedschaftsinferenz

Begrenzen Sie die Fähigkeit, zu entscheiden, ob ein Datensatz im Trainingsmaterial enthalten war. Differentielle Privatsphäre und die Maskierung von Konfidenzwerten bleiben die wirksamsten bekannten Abwehrmaßnahmen.

|   #    | Beschreibung                                                                                                                                       | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.3.1 | Überprüfen Sie, ob die Entropieregulierung pro Abfrage oder Temperaturskalierung übermäßig zuversichtliche Vorhersagen reduziert.                  |   1   |   D   |
| 10.3.2 | Stellen Sie sicher, dass das Training für sensible Datensätze eine ε-begrenzte differentielle Datenschutzoptimierung verwendet.                    |   2   |   D   |
| 10.3.3 | Stellen Sie sicher, dass Angriffssimulationen (Shadow-Model- oder Black-Box-Methoden) eine Angriffs-AUC ≤ 0,60 auf nicht verwendeten Daten zeigen. |   2   |   V   |

---

## 10.4 Widerstand gegen Modellinversion

Verhindern Sie die Rekonstruktion privater Attribute. Aktuelle Umfragen heben Ausgabeabschneidung und DP-Garantien als praktische Abwehrmaßnahmen hervor.

|   #    | Beschreibung                                                                                                                                        | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.4.1 | Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; verwenden Sie, wo erforderlich, Cluster oder Einweg-Transformationen. |   1   |   D   |
| 10.4.2 | Überprüfen Sie, ob Abfrageratenbeschränkungen wiederholte adaptive Abfragen desselben Akteurs drosseln.                                             |   1   |  D/V  |
| 10.4.3 | Verifizieren Sie, dass das Modell mit datenschutzwahrendem Rauschen trainiert wurde.                                                                |   2   |   D   |

---

## 10.5 Verteidigung gegen Modell-Extraktion

Erkennen und verhindern Sie unautorisierte Klonungen. Wasserzeichen und Analyse von Abfragemustern werden empfohlen.

|   #    | Beschreibung                                                                                                                                                            | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.5.1 | Stellen Sie sicher, dass Inferenz-Gateways globale und pro-API-Schlüssel Ratenbegrenzungen durchsetzen, die auf die Merkfähigkeitsschwelle des Modells abgestimmt sind. |   1   |   D   |
| 10.5.2 | Überprüfen Sie, ob die Statistiken zur Abfrage-Entropie und Eingabe-Mehrzahl eine automatisierte Extraktionsdetektion unterstützen.                                     |   2   |  D/V  |
| 10.5.3 | Verifizieren Sie, dass fragile oder probabilistische Wasserzeichen mit p < 0,01 in ≤ 1 000 Abfragen gegen einen verdächtigten Klon nachgewiesen werden können.          |   2   |   V   |
| 10.5.4 | Stellen Sie sicher, dass Wasserzeichen-Schlüssel und Auslöser-Sets in einem Hardware-Sicherheitsmodul gespeichert und jährlich ausgetauscht werden.                     |   3   |   D   |
| 10.5.5 | Stellen Sie sicher, dass Extraktionswarn-Ereignisse die beanstandeten Abfragen enthalten und in Incident-Response-Playbooks integriert sind.                            |   3   |   V   |

---

## 10.6 Erkennung von vergifteten Daten zur Inferenzzeit

Identifizieren und Neutralisieren von hintertürartigen oder vergifteten Eingaben.

|   #    | Beschreibung                                                                                                                                                                              | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.6.1 | Überprüfen Sie, ob Eingaben einen Anomalie-Detektor (z. B. STRIP, Konsistenzbewertung) durchlaufen, bevor die Modellinferenz erfolgt.                                                     |   1   |   D   |
| 10.6.2 | Überprüfen Sie, ob die Schwellenwerte des Detektors auf sauberen/verseuchten Validierungsdatensätzen so eingestellt sind, dass weniger als 5 % falsch positive Ergebnisse erzielt werden. |   1   |   V   |
| 10.6.3 | Überprüfen Sie, ob Eingaben, die als vergiftet markiert sind, Soft-Blocking und menschliche Überprüfungsprozesse auslösen.                                                                |   2   |   D   |
| 10.6.4 | Stellen Sie sicher, dass Detektoren mit adaptiven, auslöserlosen Backdoor-Angriffen einem Stresstest unterzogen werden.                                                                   |   2   |   V   |
| 10.6.5 | Überprüfen Sie, ob die Wirksamkeitsmetriken der Erkennung protokolliert und regelmäßig mit aktuellen Bedrohungsinformationen neu bewertet werden.                                         |   3   |   D   |

---

## 10.7 Dynamische Anpassung der Sicherheitspolitik

Echtzeit-Aktualisierungen der Sicherheitspolitik basierend auf Bedrohungsinformationen und Verhaltensanalysen.

|   #    | Beschreibung                                                                                                                                                                                      | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.7.1 | Überprüfen Sie, dass Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne dass der Agent neu gestartet werden muss, und dabei die Integrität der Richtlinienversion erhalten bleibt. |   1   |  D/V  |
| 10.7.2 | Stellen Sie sicher, dass Richtlinienaktualisierungen kryptografisch von autorisiertem Sicherheitspersonal signiert und vor der Anwendung validiert werden.                                        |   2   |  D/V  |
| 10.7.3 | Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Prüfprotokollen erfasst werden, einschließlich Begründung, Genehmigungsketten und Rücksetzungsverfahren.              |   2   |  D/V  |
| 10.7.4 | Überprüfen Sie, ob adaptive Sicherheitsmechanismen die Empfindlichkeit der Bedrohungserkennung basierend auf dem Risikokontext und Verhaltensmustern anpassen.                                    |   3   |  D/V  |
| 10.7.5 | Stellen Sie sicher, dass Entscheidungen zur Richtlinienanpassung erklärbar sind und Beweispfade für die Überprüfung durch das Sicherheitsteam enthalten.                                          |   3   |  D/V  |

---

## 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch agenteninterne Selbstreflexion und metakognitive Analyse.

|   #    | Beschreibung                                                                                                                                                             | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 10.8.1 | Überprüfen Sie, dass Agenten-Reflexionsmechanismen eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen umfassen.                               |   1   |  D/V  |
| 10.8.2 | Überprüfen Sie, dass Reflexionsausgaben validiert werden, um die Manipulation von Selbstbewertungsmechanismen durch adversariale Eingaben zu verhindern.                 |   2   |  D/V  |
| 10.8.3 | Überprüfen Sie, ob die metakognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulationen oder Kompromittierungen in den Denkprozessen von Agenten identifiziert. |   2   |  D/V  |
| 10.8.4 | Überprüfen Sie, ob reflektionsbasierte Sicherheitswarnungen eine erweiterte Überwachung und potenzielle Arbeitsabläufe für menschliches Eingreifen auslösen.             |   3   |  D/V  |
| 10.8.5 | Überprüfen Sie, ob kontinuierliches Lernen aus Sicherheitsreflexionen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu beeinträchtigen.           |   3   |  D/V  |

---

## 10.9 Evolution & Selbstverbesserung Sicherheit

Sicherheitskontrollen für Agentensysteme, die zur Selbstmodifikation und Evolution fähig sind.

|   #    | Beschreibung                                                                                                                                              | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.9.1 | Stellen Sie sicher, dass Selbstmodifikationsfähigkeiten auf festgelegte sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.               |   1   |  D/V  |
| 10.9.2 | Stellen Sie sicher, dass Entwicklungsvorschläge vor der Umsetzung einer Sicherheitsfolgenabschätzung unterzogen werden.                                   |   2   |  D/V  |
| 10.9.3 | Stellen Sie sicher, dass Selbstverbesserungsmechanismen Rückrollfähigkeiten mit Integritätsprüfung umfassen.                                              |   2   |  D/V  |
| 10.9.4 | Überprüfen Sie, dass Meta-Learning-Sicherheit die feindliche Manipulation von Verbesserungsalgorithmen verhindert.                                        |   3   |  D/V  |
| 10.9.5 | Verifizieren Sie, dass die rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mit mathematischen Beweisen der Konvergenz. |   3   |  D/V  |

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

