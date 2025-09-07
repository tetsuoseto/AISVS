# 10 Adversarielle Robustheit & Datenschutzabwehr

## Kontrollziel

Stellen Sie sicher, dass KI-Modelle zuverlässig, datenschutzwahrend und missbrauchssicher bleiben, wenn sie auf Umgehungs-, Inferenz-, Extraktions- oder Vergiftungsangriffe treffen.

---

## 10.1 Modell-Ausrichtung & Sicherheit

Sichern Sie sich gegen schädliche oder gegen Richtlinien verstoßende Ausgaben ab.

|   #    | Beschreibung                                                                                                                                                                                      | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.1.1 | Stellen Sie sicher, dass eine Ausrichtungstest-Suite (Red-Team-Eingabeaufforderungen, Jailbreak-Prüfungen, nicht erlaubte Inhalte) versioniert wird und bei jeder Modellfreigabe ausgeführt wird. |   1    |  D/V  |
| 10.1.2 | Überprüfen Sie, dass Ablehnungs- und sichere Abschluss-Schutzmaßnahmen durchgesetzt werden.                                                                                                       |   1    |   D   |
| 10.1.3 | Überprüfen Sie, dass ein automatischer Evaluator die Rate schädlicher Inhalte misst und Rückschritte über einen festgelegten Schwellenwert hinaus kennzeichnet.                                   |   2    |  D/V  |
| 10.1.4 | Stellen Sie sicher, dass das Training zur Gegenmaßnahme gegen Jailbreaks dokumentiert und reproduzierbar ist.                                                                                     |   2    |   D   |
| 10.1.5 | Stellen Sie sicher, dass formale Nachweise der Richtlinienkonformität oder zertifizierte Überwachungen kritische Bereiche abdecken.                                                               |   3    |   V   |

---

## 10.2 Härten gegen adversariale Beispiele

Erhöhen Sie die Widerstandsfähigkeit gegen manipulierte Eingaben. Robustes adversariales Training und Benchmark-Bewertung sind derzeit der beste Ansatz.

|   #    | Beschreibung                                                                                                                                  | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.2.1 | Überprüfen Sie, ob die Projekt-Repositorys Konfigurationen für adversariales Training mit reproduzierbaren Seeds enthalten.                   |   1    |   D   |
| 10.2.2 | Überprüfen Sie, ob die Erkennung von adversarialen Beispielen in Produktionspipelines Blockierungswarnungen auslöst.                          |   2    |  D/V  |
| 10.2.4 | Überprüfen Sie, ob zertifizierte Robustheitsnachweise oder Intervall-Grenzzertifikate mindestens die wichtigsten kritischen Klassen abdecken. |   3    |   V   |
| 10.2.5 | Überprüfen Sie, dass Regressionstests adaptive Angriffe verwenden, um einen nicht messbaren Robustheitsverlust zu bestätigen.                 |   3    |   V   |

---

## 10.3 Mitgliedschaftsinferenz-Minderung

Begrenzen Sie die Möglichkeit zu entscheiden, ob ein Datensatz im Trainingsdatensatz enthalten war. Differentielle Privatsphäre und Maskierung des Vertrauensscores bleiben die effektivsten bekannten Schutzmaßnahmen.

|   #    | Beschreibung                                                                                                                                      | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.3.1 | Überprüfen Sie, ob eine pro-Abfrage-Entropie-Regularisierung oder Temperaturskalierung übermäßig zuversichtliche Vorhersagen reduziert.           |   1    |   D   |
| 10.3.2 | Überprüfen Sie, ob das Training eine ε-begrenzte differentielle Datenschutzoptimierung für sensible Datensätze verwendet.                         |   2    |   D   |
| 10.3.3 | Überprüfen Sie, dass Angriffssimulationen (Shadow-Model- oder Black-Box-Methoden) eine Angriff-AUC von ≤ 0,60 bei nicht verwendeten Daten zeigen. |   2    |   V   |

---

## 10.4 Widerstand gegen Modellinversion

Verhindern Sie die Rekonstruktion privater Attribute. Aktuelle Umfragen betonen die Ausgabekürzung und DP-Garantien als praktische Schutzmaßnahmen.

|   #    | Beschreibung                                                                                                                                | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.4.1 | Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; verwenden Sie bei Bedarf Buckets oder Einwegtransformationen. |   1    |   D   |
| 10.4.2 | Überprüfen Sie, ob Abfrage-Ratenbegrenzungen wiederholte adaptive Abfragen von derselben Instanz drosseln.                                  |   1    |  D/V  |
| 10.4.3 | Überprüfen Sie, dass das Modell mit datenschutzförderndem Rauschen trainiert wurde.                                                         |   2    |   D   |

---

## 10.5 Verteidigung gegen Modell-Extraktion

Erkennen und Verhindern unbefugter Klonierung. Wasserzeichen und Analyse von Abfragemustern werden empfohlen.

|   #    | Beschreibung                                                                                                                                                                       | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.5.1 | Überprüfen Sie, dass Inferenz-Gateways globale und pro-API-Schlüssel festgelegte Ratenbegrenzungen durchsetzen, die auf den Memorierungsschwellenwert des Modells abgestimmt sind. |   1    |   D   |
| 10.5.2 | Überprüfen Sie, ob die Statistiken zur Abfrage-Entropie und Eingabe-Pluralität einen automatisierten Extraktionsdetektor speisen.                                                  |   2    |  D/V  |
| 10.5.3 | Überprüfen Sie, dass zerbrechliche oder probabilistische Wasserzeichen mit p < 0,01 in ≤ 1 000 Anfragen gegen einen verdächtigen Klon nachgewiesen werden können.                  |   2    |   V   |
| 10.5.4 | Überprüfen Sie, dass Wasserzeichen-Schlüssel und Auslöse-Sets in einem Hardware-Sicherheitsmodul gespeichert und jährlich ausgetauscht werden.                                     |   3    |   D   |
| 10.5.5 | Überprüfen Sie, ob Extraktionswarnereignisse die beanstandeten Abfragen enthalten und in Incident-Response-Playbooks integriert sind.                                              |   3    |   V   |

---

## 10.6 Erkennung von vergifteten Daten zur Inferenzzeit

Erkennen und Neutralisieren von mit Hintertüren versehenen oder vergifteten Eingaben.

|   #    | Beschreibung                                                                                                                                                                      | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.6.1 | Stellen Sie sicher, dass Eingaben vor der Modellausführung durch einen Anomalie-Detektor (z. B. STRIP, Konsistenzbewertung) laufen.                                               |   1    |   D   |
| 10.6.2 | Überprüfen Sie, dass die Schwellenwerte des Detektors auf sauberen/vergifteten Validierungsdatensätzen so eingestellt sind, dass weniger als 5 % Falsch-Positive erreicht werden. |   1    |   V   |
| 10.6.3 | Überprüfen Sie, dass als vergiftet gekennzeichnete Eingaben eine Soft-Sperrung und einen Workflow zur menschlichen Überprüfung auslösen.                                          |   2    |   D   |
| 10.6.4 | Stellen Sie sicher, dass Detektoren mit adaptiven, triggerlosen Backdoor-Angriffen einem Stresstest unterzogen werden.                                                            |   2    |   V   |
| 10.6.5 | Stellen Sie sicher, dass Erkennungsleistungsmetriken protokolliert und regelmäßig mit aktuellen Bedrohungsinformationen neu bewertet werden.                                      |   3    |   D   |

---

## 10.7 Dynamische Anpassung der Sicherheitsrichtlinie

Echtzeit-Aktualisierungen der Sicherheitspolitik basierend auf Bedrohungsinformationen und Verhaltensanalyse.

|   #    | Beschreibung                                                                                                                                                                          | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.7.1 | Überprüfen Sie, dass Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne den Agenten neu zu starten, und dabei die Integrität der Richtlinienversion beibehalten wird.  |   1    |  D/V  |
| 10.7.2 | Überprüfen Sie, ob Richtlinienaktualisierungen kryptografisch von autorisiertem Sicherheitspersonal signiert und vor der Anwendung validiert werden.                                  |   2    |  D/V  |
| 10.7.3 | Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Prüfpfaden protokolliert werden, einschließlich Begründung, Genehmigungsketten und Rücksetzungsverfahren. |   2    |  D/V  |
| 10.7.4 | Überprüfen Sie, dass adaptive Sicherheitsmechanismen die Empfindlichkeit der Bedrohungserkennung basierend auf dem Risikokontext und Verhaltensmustern anpassen.                      |   3    |  D/V  |
| 10.7.5 | Stellen Sie sicher, dass Entscheidungen zur Richtlinienanpassung erklärbar sind und Nachweise für die Überprüfung durch das Sicherheitsteam enthalten.                                |   3    |  D/V  |

---

## 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch Agenten-Selbstreflexion und metakognitive Analyse.

|   #    | Beschreibung                                                                                                                                                          | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.8.1 | Überprüfen Sie, ob Reflexionsmechanismen von Agenten eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen enthalten.                         |   1    |  D/V  |
| 10.8.2 | Stellen Sie sicher, dass Reflexionsausgaben validiert werden, um eine Manipulation der Selbstbewertungsmechanismen durch feindliche Eingaben zu verhindern.           |   2    |  D/V  |
| 10.8.3 | Überprüfen Sie, ob die meta-kognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulationen oder Beeinträchtigungen in den Denkprozessen von Agenten erkennt.   |   2    |  D/V  |
| 10.8.4 | Überprüfen Sie, ob sicherheitsrelevante Warnungen basierend auf Reflection eine erweitere Überwachung und potenzielle Workflows für menschliches Eingreifen auslösen. |   3    |  D/V  |
| 10.8.5 | Überprüfen Sie, dass kontinuierliches Lernen aus Sicherheitserkenntnissen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu beeinträchtigen.    |   3    |  D/V  |

---

## 10.9 Sicherheit bei Evolution und Selbstverbesserung

Sicherheitskontrollen für Agentensysteme, die zur Selbstmodifikation und Evolution fähig sind.

|   #    | Beschreibung                                                                                                                                              | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 10.9.1 | Überprüfen Sie, dass Selbstmodifikationsfähigkeiten auf ausgewiesene sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.                  |   1    |  D/V  |
| 10.9.2 | Stellen Sie sicher, dass Evolutionvorschläge vor der Implementierung einer Sicherheitsauswirkungsbewertung unterzogen werden.                             |   2    |  D/V  |
| 10.9.3 | Stellen Sie sicher, dass Selbstverbesserungsmechanismen Rückrollfunktionen mit Integritätsprüfung enthalten.                                              |   2    |  D/V  |
| 10.9.4 | Verifizieren Sie, dass Meta-Learning-Sicherheit die feindliche Manipulation von Verbesserungsalgorithmen verhindert.                                      |   3    |  D/V  |
| 10.9.5 | Verifizieren Sie, dass rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mit mathematischen Beweisen für die Konvergenz. |   3    |  D/V  |

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

