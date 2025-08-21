# 10 Gegnerische Robustheit & Datenschutzverteidigung

## Steuerungsziel

Stellen Sie sicher, dass KI-Modelle zuverlässig, datenschutzwahrend und missbrauchsresistent bleiben, wenn sie Angriffen wie Umgehung, Rückschluss, Extraktion oder Vergiftung ausgesetzt sind.

---

## 10.1 Modellabstimmung und Sicherheit

Schützen Sie vor schädlichen oder gegen Richtlinien verstoßenden Ausgaben.

|   #    | Beschreibung                                                                                                                                                                                | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.1.1 | Stellen Sie sicher, dass ein Alignment-Test-Suite (Red-Team-Aufforderungen, Jailbreak-Tests, nicht erlaubte Inhalte) versionskontrolliert ist und bei jeder Modellfreigabe ausgeführt wird. |   1   |  D/V  |
| 10.1.2 | Überprüfen Sie, dass Verweigerungs- und Sicherheitsabschluss-Schutzvorrichtungen durchgesetzt werden.                                                                                       |   1   |   D   |
| 10.1.3 | Überprüfen Sie, ob ein automatisierter Evaluator die Rate schädlicher Inhalte misst und Rückschritte, die über einen festgelegten Schwellenwert hinausgehen, kennzeichnet.                  |   2   |  D/V  |
| 10.1.4 | Stellen Sie sicher, dass das Counter-Jailbreak-Training dokumentiert und reproduzierbar ist.                                                                                                |   2   |   D   |
| 10.1.5 | Stellen Sie sicher, dass formale Nachweise der Richtlinienkonformität oder zertifizierte Überwachung kritische Bereiche abdecken.                                                           |   3   |   V   |

---

## 10.2 Härtung gegen adversariale Beispiele

Erhöhen Sie die Widerstandsfähigkeit gegenüber manipulierten Eingaben. Robustes adversariales Training und Bewertung anhand von Benchmarks sind derzeit die besten Verfahren.

|   #    | Beschreibung                                                                                                                                      | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.2.1 | Überprüfen Sie, dass Projekt-Repositorys Konfigurationen für adversariales Training mit reproduzierbaren Seeds enthalten.                         |   1   |   D   |
| 10.2.2 | Überprüfen Sie, ob die Erkennung von adversarialen Beispielen in Produktionspipelines blockierende Warnungen auslöst.                             |   2   |  D/V  |
| 10.2.4 | Verifizieren Sie, dass zertifizierte Robustheitsnachweise oder Intervall-Grenzzertifikate mindestens die wichtigsten kritischen Klassen abdecken. |   3   |   V   |
| 10.2.5 | Überprüfen Sie, dass Regressionstests adaptive Angriffe verwenden, um einen nicht messbaren Verlust der Robustheit zu bestätigen.                 |   3   |   V   |

---

## 10.3 Maßnahmen zur Minderung von Mitgliedschaftsinferenz

Begrenzen Sie die Möglichkeit zu entscheiden, ob ein Datensatz im Trainingsdatensatz enthalten war. Differentielle Privatsphäre und das Maskieren von Konfidenz-Scores bleiben die effektivsten bekannten Schutzmaßnahmen.

|   #    | Beschreibung                                                                                                                             | Ebene | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.3.1 | Überprüfen Sie, ob eine Entropie-Regularisierung pro Abfrage oder Temperaturskalierung übermäßig selbstsichere Vorhersagen reduziert.    |   1   |   D   |
| 10.3.2 | Verifizieren Sie, dass das Training eine ε-begrenzte differentielle private Optimierung für sensible Datensätze verwendet.               |   2   |   D   |
| 10.3.3 | Stellen Sie sicher, dass Angriffssimulationen (Shadow-Modell oder Black-Box) einen Angriff-AUC ≤ 0,60 auf zurückgehaltenen Daten zeigen. |   2   |   V   |

---

## 10.4 Widerstand gegen Modell-Inversion

Verhindern Sie die Rekonstruktion privater Attribute. Aktuelle Umfragen betonen die Ausgabekürzung und DP-Garantien als praktische Schutzmaßnahmen.

|   #    | Beschreibung                                                                                                                                 | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.4.1 | Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; verwenden Sie bei Bedarf Buckets oder Einweg-Transformationen. |   1   |   D   |
| 10.4.2 | Stellen Sie sicher, dass Abfrage-Ratenbeschränkungen wiederholte adaptive Abfragen vom selben Prinzipal drosseln.                            |   1   |  D/V  |
| 10.4.3 | Verifizieren Sie, dass das Modell mit datenschutzwahrendem Rauschen trainiert wurde.                                                         |   2   |   D   |

---

## 10.5 Modell-Extraktionsabwehr

Erkennen und Verhindern unautorisierter Klone. Wasserzeichen und Analyse von Abfragemustern werden empfohlen.

|   #    | Beschreibung                                                                                                                                                                                       | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.5.1 | Stellen Sie sicher, dass Inferenz-Gateways globale und pro API-Schlüssel angepasste Grenzwerte für die Anfragerate durchsetzen, die auf den Memorierungsschwellenwert des Modells abgestimmt sind. |   1   |   D   |
| 10.5.2 | Überprüfen Sie, ob die Statistiken zur Abfrage-Entropie und zur Eingabe-Mehrzahligkeit einen automatischen Extraktionsdetektor speisen.                                                            |   2   |  D/V  |
| 10.5.3 | Überprüfen Sie, ob fragile oder probabilistische Wasserzeichen mit p < 0,01 in ≤ 1.000 Abfragen gegen einen verdächtigen Klon nachgewiesen werden können.                                          |   2   |   V   |
| 10.5.4 | Stellen Sie sicher, dass Wasserzeichen-Schlüssel und Auslöse-Sets in einem Hardware-Sicherheitsmodul gespeichert und jährlich ausgetauscht werden.                                                 |   3   |   D   |
| 10.5.5 | Überprüfen Sie, ob Extraction-Alert-Ereignisse die anstößigen Abfragen enthalten und in Incident-Response-Playbooks integriert sind.                                                               |   3   |   V   |

---

## 10.6 Erkennung von vergifteten Daten zur Inferenzzeit

Erkennen und Neutralisieren von mit Hintertüren verseuchten oder vergifteten Eingaben.

|   #    | Beschreibung                                                                                                                                                                      | Ebene | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.6.1 | Verifizieren Sie, dass Eingaben vor der Modellausführung durch einen Anomalieerkenner (z. B. STRIP, Konsistenzbewertung) geprüft werden.                                          |   1   |   D   |
| 10.6.2 | Stellen Sie sicher, dass die Detektorschwellenwerte an sauberen/verseuchten Validierungssets so eingestellt sind, dass weniger als 5 % falsch positive Ergebnisse erzielt werden. |   1   |   V   |
| 10.6.3 | Überprüfen Sie, ob Eingaben, die als vergiftet markiert sind, Soft-Blocking und menschliche Überprüfungs-Workflows auslösen.                                                      |   2   |   D   |
| 10.6.4 | Stellen Sie sicher, dass Detektoren mit adaptiven, triggerlosen Backdoor-Angriffen einem Stresstest unterzogen werden.                                                            |   2   |   V   |
| 10.6.5 | Stellen Sie sicher, dass Metriken zur Erkennungseffizienz protokolliert und regelmäßig mit aktuellen Bedrohungsinformationen neu bewertet werden.                                 |   3   |   D   |

---

## 10.7 Dynamische Anpassung der Sicherheitsrichtlinie

Echtzeit-Aktualisierungen von Sicherheitsrichtlinien basierend auf Bedrohungsinformationen und Verhaltensanalysen.

|   #    | Beschreibung                                                                                                                                                                        | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.7.1 | Überprüfen Sie, dass Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne den Agenten neu zu starten, und dabei die Integrität der Richtlinienversion erhalten bleibt. |   1   |  D/V  |
| 10.7.2 | Stellen Sie sicher, dass Richtlinienaktualisierungen kryptografisch von autorisiertem Sicherheitspersonal signiert und vor der Anwendung validiert werden.                          |   2   |  D/V  |
| 10.7.3 | Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Prüfpfaden protokolliert werden, einschließlich Begründung, Genehmigungsketten und Rücksetzverfahren.   |   2   |  D/V  |
| 10.7.4 | Überprüfen Sie, ob adaptive Sicherheitsmechanismen die Empfindlichkeit der Bedrohungserkennung basierend auf Risikokontext und Verhaltensmustern anpassen.                          |   3   |  D/V  |
| 10.7.5 | Stellen Sie sicher, dass Entscheidungen zur Richtlinienanpassung erklärbar sind und Nachweispfade für die Überprüfung durch das Sicherheitsteam enthalten.                          |   3   |  D/V  |

---

## 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch Agenten-Selbstreflexion und metakognitive Analyse.

|   #    | Beschreibung                                                                                                                                                                   | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 10.8.1 | Stellen Sie sicher, dass Agenten-Reflexionsmechanismen eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen umfassen.                                 |   1   |  D/V  |
| 10.8.2 | Stellen Sie sicher, dass Reflektionsausgaben validiert werden, um die Manipulation von Selbstbewertungsmechanismen durch adversarielle Eingaben zu verhindern.                 |   2   |  D/V  |
| 10.8.3 | Stellen Sie sicher, dass die metakognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulationen oder Kompromittierungen in den Denkprozessen von Agenten identifiziert. |   2   |  D/V  |
| 10.8.4 | Überprüfen Sie, dass reflektionsbasierte Sicherheitswarnungen eine erweiterte Überwachung und potenzielle menschliche Interventionsprozesse auslösen.                          |   3   |  D/V  |
| 10.8.5 | Überprüfen Sie, dass kontinuierliches Lernen aus Sicherheitsreflexionen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu beeinträchtigen.               |   3   |  D/V  |

---

## 10.9 Evolution & Selbstverbesserungssicherheit

Sicherheitskontrollen für Agentensysteme, die zur Selbstmodifikation und Evolution fähig sind.

|   #    | Beschreibung                                                                                                                                            | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.9.1 | Stellen Sie sicher, dass Selbstmodifikationsfähigkeiten auf festgelegte sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.             |   1   |  D/V  |
| 10.9.2 | Stellen Sie sicher, dass Evolutionsvorschläge vor der Implementierung einer Sicherheitsauswirkungsbewertung unterzogen werden.                          |   2   |  D/V  |
| 10.9.3 | Überprüfen Sie, dass Selbstverbesserungsmechanismen Rücksetzfunktionen mit Integritätsprüfung enthalten.                                                |   2   |  D/V  |
| 10.9.4 | Überprüfen Sie, ob Meta-Learning-Sicherheit die feindliche Manipulation von Verbesserungsalgorithmen verhindert.                                        |   3   |  D/V  |
| 10.9.5 | Überprüfen Sie, dass rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mit mathematischen Beweisen für die Konvergenz. |   3   |  D/V  |

---

### Literaturverzeichnis

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

