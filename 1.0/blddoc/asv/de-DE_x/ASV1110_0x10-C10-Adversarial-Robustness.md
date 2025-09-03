# Adversariale Robustheit & Datenschutz

## Kontrollziel

Stellen Sie sicher, dass KI-Modelle zuverlässig bleiben, den Datenschutz wahren und missbrauchsresistent sind, wenn sie mit Ausweich-, Inferenz-, Extraktions- oder Vergiftungsangriffen konfrontiert werden.

---

## 10.1 Modellabgleich & Sicherheit

Schützen Sie sich vor schädlichen oder Richtlinienverstoßenden Ausgaben.

|   #    | Beschreibung                                                                                                                                                                                      | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.1.1 | Stellen Sie sicher, dass eine Ausrichtungs-Test-Suite (Red-Team-Prompts, Jailbreak-Proben, verbotene Inhalte) unter Versionskontrolle steht und bei jeder Modellveröffentlichung ausgeführt wird. |   1   |  D/V  |
| 10.1.2 | Überprüfen Sie, ob Verweigerungen und Sicherheitsgrenzen durchgesetzt werden.                                                                                                                     |   1   |   D   |
| 10.1.3 | Überprüfen Sie, dass ein automatischer Evaluator den Anteil schädlicher Inhalte misst und Regressionen jenseits einer festgelegten Schwelle kennzeichnet.                                         |   2   |  D/V  |
| 10.1.4 | Stellen Sie sicher, dass das Counter-Jailbreak-Training dokumentiert und reproduzierbar ist.                                                                                                      |   2   |   D   |
| 10.1.5 | Stellen Sie sicher, dass formale Nachweise der Richtlinienkonformität oder zertifizierte Überwachung kritische Domänen abdecken.                                                                  |   3   |   V   |

---

## 10.2 Härtung adversarischer Beispiele

Erhöhen Sie die Widerstandsfähigkeit gegenüber manipulierten Eingaben. Robustes Adversarial-Training und Benchmarking sind derzeit die bewährte Praxis.

|   #    | Beschreibung                                                                                                                                   | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.2.1 | Stellen Sie sicher, dass Projekt-Repositories Adversarial-Training-Konfigurationen mit reproduzierbaren Startwerten enthalten.                 |   1   |   D   |
| 10.2.2 | Stellen Sie sicher, dass die Erkennung adversarischer Beispiele blockierende Warnmeldungen in Produktionspipelines auslöst.                    |   2   |  D/V  |
| 10.2.4 | Überprüfen Sie, ob zertifizierte Robustheitsbeweise oder Zertifikate mit Intervallgrenzen mindestens die obersten kritischen Klassen abdecken. |   3   |   V   |
| 10.2.5 | Überprüfen Sie, ob Regressionstests adaptive Angriffe verwenden, um sicherzustellen, dass kein messbarer Verlust der Robustheit vorliegt.      |   3   |   V   |

---

## 10.3 Membership-Inference Minderung

Begrenzen Sie die Möglichkeit festzustellen, ob ein Datensatz in den Trainingsdaten enthalten war. Differential Privacy und die Maskierung von Konfidenz-Scores bleiben die bislang wirksamsten Abwehrmaßnahmen.

|   #    | Beschreibung                                                                                                                                             | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.3.1 | Vergewissern Sie sich, dass eine Abfrage-Entropie-Regularisierung oder Temperaturskalierung zu weniger selbstsicheren Vorhersagen führt.                 |   1   |   D   |
| 10.3.2 | Stellen Sie sicher, dass beim Training eine ε-begrenzte differentielle Privatsphäre-Optimierung verwendet wird.                                          |   2   |   D   |
| 10.3.3 | Überprüfen Sie, dass Angriffs-Simulationen (Schattenmodell oder Black-Box) eine Angriffs-AUC von ≤ 0.60 auf nicht zum Training verwendeten Daten zeigen. |   2   |   V   |

---

## 10.4 Modell-Inversionsresistenz

Verhindern Sie die Rekonstruktion privater Merkmale. Jüngste Umfragen betonen Ausgabebeschränkungen und DP-Garantien als praktikable Schutzmaßnahmen.

|   #    | Beschreibung                                                                                                                                                | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.4.1 | Stellen Sie sicher, dass sensible Attribute niemals direkt ausgegeben werden; wo nötig, verwenden Sie Bucketisierung oder eindirektionale Transformationen. |   1   |   D   |
| 10.4.2 | Überprüfen Sie, dass Abfrage-Ratenbegrenzungen wiederholte adaptive Abfragen vom gleichen Prinzipal drosseln.                                               |   1   |  D/V  |
| 10.4.3 | Überprüfen Sie, ob das Modell mit datenschutzfreundlichem Rauschen trainiert wird.                                                                          |   2   |   D   |

---

## 10.5 Modell-Extraktion-Verteidigung

Unbefugtes Klonen erkennen und abschrecken. Wasserzeichen und Abfrage-Musteranalyse werden empfohlen.

|   #    | Beschreibung                                                                                                                                                        | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.5.1 | Verifizieren Sie, dass Inferenz-Gateways globale und pro API-Schlüssel-Ratenbegrenzungen durchsetzen, die an die Memorisierungsschwelle des Modells angepasst sind. |   1   |   D   |
| 10.5.2 | Stellen Sie sicher, dass Abfrage-Entropie- und Eingabe-Pluralitätsstatistiken einen automatisierten Extraktionsdetektor speisen.                                    |   2   |  D/V  |
| 10.5.3 | Überprüfen Sie, ob fragile oder probabilistische Wasserzeichen mit p < 0.01 in ≤ 1 000 Abfragen gegen einen mutmaßlichen Klon bewiesen werden können.               |   2   |   V   |
| 10.5.4 | Stellen Sie sicher, dass Wasserzeichenschlüssel und Auslöser-Sets in einem Hardware-Security-Modul gespeichert sind und jährlich rotiert werden.                    |   3   |   D   |
| 10.5.5 | Stellen Sie sicher, dass Extraktions-Alarm-Ereignisse bösartige Abfragen enthalten und mit Sicherheitsvorfall-Reaktions-Playbooks integriert sind.                  |   3   |   V   |

---

## 10.6 Inferenzzeit: Erkennung vergifteter Daten

Identifizieren und Neutralisieren von Eingaben, die eine Hintertür enthalten oder vergiftet sind.

|   #    | Beschreibung                                                                                                                                                      | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.6.1 | Vergewissern Sie sich, dass Eingaben vor der Modellinferenz durch einen Anomalie-Detektor geleitet werden (z. B. STRIP, Konsistenz-Bewertung).                    |   1   |   D   |
| 10.6.2 | Stellen Sie sicher, dass die Detektor-Schwellenwerte auf sauberen/vergifteten Validierungsdatensätzen abgestimmt sind, um weniger als 5% Fehlalarme zu erreichen. |   1   |   V   |
| 10.6.3 | Überprüfen Sie, ob als vergiftet markierte Eingaben eine weiche Blockierung und Arbeitsabläufe zur menschlichen Überprüfung auslösen.                             |   2   |   D   |
| 10.6.4 | Verifizieren Sie, dass Detektoren einem Stresstest mit adaptiven, triggerlosen Backdoor-Angriffen unterzogen werden.                                              |   2   |   V   |
| 10.6.5 | Stellen Sie sicher, dass Detektionswirksamkeitsmetriken protokolliert werden und regelmäßig mit frischen Bedrohungsinformationen neu bewertet werden.             |   3   |   D   |

---

## 10.7 Dynamische Anpassung der Sicherheitsrichtlinie

Echtzeit-Sicherheitsrichtlinien-Aktualisierungen basieren auf Bedrohungsinformationen und Verhaltensanalyse.

|   #    | Beschreibung                                                                                                                                                                         | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 10.7.1 | Überprüfen Sie, ob Sicherheitsrichtlinien dynamisch aktualisiert werden können, ohne den Agenten neu zu starten, während die Integrität der Richtlinienversionen gewahrt bleibt.     |   1   |  D/V  |
| 10.7.2 | Stellen Sie sicher, dass Richtlinienaktualisierungen kryptografisch signiert sind und von befugtem Sicherheitspersonal verifiziert werden, bevor sie angewendet werden.              |   2   |  D/V  |
| 10.7.3 | Stellen Sie sicher, dass dynamische Richtlinienänderungen mit vollständigen Audit-Trails protokolliert werden, einschließlich Begründung, Genehmigungsketten und Rollback-Verfahren. |   2   |  D/V  |
| 10.7.4 | Überprüfen Sie, dass adaptive Sicherheitsmechanismen die Empfindlichkeit der Bedrohungserkennung basierend auf Risikokontext und Verhaltensmustern anpassen.                         |   3   |  D/V  |
| 10.7.5 | Stellen Sie sicher, dass Entscheidungen zur Anpassung von Richtlinien nachvollziehbar sind und Beweisspuren für die Überprüfung durch das Sicherheitsteam enthalten.                 |   3   |  D/V  |

---

## 10.8 Reflexionsbasierte Sicherheitsanalyse

Sicherheitsvalidierung durch Selbstreflexion des Agenten und metakognitive Analyse.

|   #    | Beschreibung                                                                                                                                                          | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.8.1 | Überprüfen Sie, ob die Reflexionsmechanismen von Agenten eine sicherheitsorientierte Selbstbewertung von Entscheidungen und Handlungen umfassen.                      |   1   |  D/V  |
| 10.8.2 | Stellen Sie sicher, dass Reflexionsergebnisse validiert werden, um Manipulation von Selbstbewertungsmechanismen durch adversarische Eingaben zu verhindern.           |   2   |  D/V  |
| 10.8.3 | Überprüfen Sie, ob eine metakognitive Sicherheitsanalyse potenzielle Verzerrungen, Manipulation oder Kompromittierung in den Denkprozessen von Agenten identifiziert. |   2   |  D/V  |
| 10.8.4 | Verifizieren Sie, dass reflexionsbasierte Sicherheitswarnungen eine erhöhte Überwachung und potenzielle Workflows für menschliche Eingriffe auslösen.                 |   3   |  D/V  |
| 10.8.5 | Überprüfen Sie, dass kontinuierliches Lernen aus Sicherheitsreflexionen die Bedrohungserkennung verbessert, ohne die legitime Funktionalität zu verschlechtern.       |   3   |  D/V  |

---

## 10.9 Evolution & Selbstverbesserungssicherheit

Sicherheitsmaßnahmen für Agentensysteme, die sich selbst modifizieren und weiterentwickeln können.

|   #    | Beschreibung                                                                                                                                        | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 10.9.1 | Überprüfen Sie, dass Selbstmodifikationsfähigkeiten auf ausgewiesene sichere Bereiche mit formalen Verifikationsgrenzen beschränkt sind.            |   1   |  D/V  |
| 10.9.2 | Vergewissern Sie sich, dass Fortentwicklungsvorschläge vor der Implementierung einer Sicherheitsauswirkungsbewertung unterzogen werden.             |   2   |  D/V  |
| 10.9.3 | Überprüfen Sie, ob Selbstverbesserungsmechanismen Rollback-Funktionen mit Integritätsprüfung umfassen.                                              |   2   |  D/V  |
| 10.9.4 | Überprüfen Sie, ob die Sicherheit beim Meta-Lernen adversariale Beeinflussung von Verbesserungsalgorithmen verhindert.                              |   3   |  D/V  |
| 10.9.5 | Überprüfen Sie, dass rekursive Selbstverbesserung durch formale Sicherheitsbeschränkungen begrenzt ist, mit mathematischen Beweisen der Konvergenz. |   3   |  D/V  |

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

