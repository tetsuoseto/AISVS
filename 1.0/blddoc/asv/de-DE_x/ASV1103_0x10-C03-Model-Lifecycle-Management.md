# C3 Modell-Lebenszyklusverwaltung & Änderungssteuerung

## Kontrollziel

KI-Systeme müssen Änderungssteuerungsprozesse implementieren, die verhindern, dass unautorisierte oder unsichere Modelländerungen in die Produktion gelangen. Diese Kontrolle gewährleistet die Modellintegrität über den gesamten Lebenszyklus hinweg – von der Entwicklung über die Bereitstellung bis zur Außerbetriebnahme – was eine schnelle Reaktion auf Vorfälle ermöglicht und die Verantwortlichkeit für alle Änderungen sicherstellt.

Wichtigstes Sicherheitsziel: Nur autorisierte, validierte Modelle gelangen durch kontrollierte Prozesse, die Integrität, Rückverfolgbarkeit und Wiederherstellbarkeit gewährleisten, in die Produktion.

---

## C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit verifizierter Integrität erreichen Produktionsumgebungen.

|   #   | Beschreibung                                                                                                                                                                                                                                          | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.1.1 | Überprüfen Sie, ob alle Modellartefakte (Gewichte, Konfigurationen, Tokenizer) vor der Bereitstellung kryptographisch von autorisierten Stellen signiert sind.                                                                                        |   1    |  D/V  |
| 3.1.2 | Stellen Sie sicher, dass die Modellintegrität zur Bereitstellungszeit validiert wird und Signaturprüfungsfehler das Laden des Modells verhindern.                                                                                                     |   1    |  D/V  |
| 3.1.3 | Überprüfen Sie, ob die Herkunftsaufzeichnungen des Modells die Identität der autorisierenden Instanz, Prüfsummen der Trainingsdaten, Ergebnisse der Validierungstests mit Bestehen/Nichtbestehen-Status sowie einen Erstellungszeitstempel enthalten. |   2    |  D/V  |
| 3.1.4 | Stellen Sie sicher, dass alle Modellartefakte semantische Versionierung (MAJOR.MINOR.PATCH) verwenden, mit dokumentierten Kriterien, die angeben, wann jede Versionskomponente erhöht wird.                                                           |   2    |  D/V  |
| 3.1.5 | Überprüfen Sie, dass die Abhängigkeitsverfolgung ein Echtzeit-Inventar führt, das eine schnelle Identifizierung aller konsumierenden Systeme ermöglicht.                                                                                              |   2    |   V   |

---

## C3.2 Modellvalidierung & Testen

Modelle müssen vor der Bereitstellung definierte Sicherheits- und Schutzvalidierungen bestehen.

|   #   | Beschreibung                                                                                                                                                                                                                                                              | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.2.1 | Stellen Sie sicher, dass Modelle automatisierten Sicherheitstests unterzogen werden, die Eingabevalidierung, Ausgabereinigung und Sicherheitsevaluierungen mit vorab vereinbarten organisatorischen Bestehens-/Nichtbestehensgrenzwerten vor der Bereitstellung umfassen. |   1    |  D/V  |
| 3.2.2 | Stellen Sie sicher, dass Validierungsfehler nach ausdrücklicher Genehmigung durch vorab bestimmte autorisierte Personen mit dokumentierten geschäftlichen Begründungen automatisch die Bereitstellung des Modells blockieren.                                             |   1    |  D/V  |
| 3.2.3 | Überprüfen Sie, dass die Testergebnisse kryptografisch signiert und unveränderlich mit dem spezifischen Modellversions-Hash verknüpft sind, der validiert wird.                                                                                                           |   2    |   V   |
| 3.2.4 | Stellen Sie sicher, dass Notfalleinsätze eine dokumentierte Sicherheitsrisikobewertung und die Genehmigung einer vorab festgelegten Sicherheitsinstanz innerhalb vorab vereinbarter Zeitrahmen erfordern.                                                                 |   2    |  D/V  |

---

## C3.3 Kontrollierte Bereitstellung & Rücksetzung

Modellbereitstellungen müssen kontrolliert, überwacht und reversibel sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.3.1 | Stellen Sie sicher, dass Produktionsbereitstellungen schrittweise Rollout-Mechanismen (Canary-Deployments, Blue-Green-Deployments) mit automatisierten Rollback-Auslösern implementieren, die auf vorab vereinbarten Fehlerquoten, Latenzschwellen oder Sicherheitsalarmkriterien basieren. |   1    |   D   |
| 3.3.2 | Überprüfen Sie, dass die Rollback-Fähigkeiten den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vorgegebener organisatorischer Zeitfenster wiederherstellen.                                                                                     |   1    |  D/V  |
| 3.3.3 | Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen berechnen, bevor das Modell aktiviert wird, und dass die Bereitstellung bei jeglicher Abweichung fehlschlägt.                                                              |   2    |  D/V  |
| 3.3.4 | Überprüfen Sie, ob die Notfall-Abschaltfunktionen des Modells Modellendpunkte innerhalb vorgegebener Reaktionszeiten über automatisierte Stromkreise oder manuelle Abschaltvorrichtungen deaktivieren können.                                                                               |   2    |  D/V  |
| 3.3.5 | Stellen Sie sicher, dass Rollback-Artefakte (vorherige Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderbarem Speicher für die Vorfallreaktion aufbewahrt werden.                                                                    |   2    |   V   |

---

## C3.4 Änderung der Verantwortlichkeit & Prüfung

Alle Änderungen im Modelllebenszyklus müssen nachvollziehbar und prüfbar sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.4.1 | Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Stilllegung) unveränderliche Prüfaufzeichnungen erzeugen, die einen Zeitstempel, eine authentifizierte Akteursidentität, einen Änderungstyp sowie Vorher-/Nachher-Zustände enthalten.        |   1    |   V   |
| 3.4.2 | Überprüfen Sie, ob der Zugriff auf das Audit-Protokoll eine angemessene Autorisierung erfordert und ob alle Zugriffsversuche mit Benutzeridentität und Zeitstempel protokolliert werden.                                                                                    |   2    |  D/V  |
| 3.4.3 | Stellen Sie sicher, dass Prompt-Vorlagen und Systemnachrichten in Git-Repositories versioniert sind und vor der Bereitstellung eine obligatorische Code-Überprüfung sowie die Genehmigung durch festgelegte Prüfer erfolgen.                                                |   2    |  D/V  |
| 3.4.4 | Überprüfen Sie, ob die Audit-Protokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Snapshots, Abhängigkeitsversionen), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitstempel innerhalb des Aufbewahrungszeitraums zu ermöglichen. |   2    |   V   |

---

## C3.5 Sichere Entwicklungspraktiken

Modelentwicklungs- und Trainingsprozesse müssen sicheren Verfahren folgen, um eine Kompromittierung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                                                | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.5.1 | Verifizieren Sie, dass die Entwicklungs-, Test- und Produktionsumgebungen für Modelle physisch oder logisch getrennt sind. Sie dürfen keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher besitzen.             |   1    |   D   |
| 3.5.2 | Stellen Sie sicher, dass Modelltraining und Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang stattfinden.                                                                                                                          |   1    |   D   |
| 3.5.3 | Stellen Sie sicher, dass Trainingsdatenquellen durch Integritätsprüfungen validiert und vor der Verwendung in der Modellentwicklung über vertrauenswürdige Quellen mit dokumentierter Nachverfolgbarkeit authentifiziert werden.                            |   1    |  D/V  |
| 3.5.4 | Stellen Sie sicher, dass Entwicklungsartefakte des Modells (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionsverwaltung gespeichert sind und vor der Verwendung im Training eine Genehmigung durch Kollegenprüfung erforderlich ist. |   2    |   D   |

---

## C3.6 Modellrücknahme und Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme festgestellt werden.

|   #   | Beschreibung                                                                                                                                                                                                                                       | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 3.6.1 | Überprüfen Sie, dass Modell-Ruhestandsprozesse automatisch Abhängigkeitsgraphen scannen, alle verbrauchenden Systeme identifizieren und vor der Stilllegung vorab vereinbarte Vorankündigungsfristen einhalten.                                    |   1    |   D   |
| 3.6.2 | Überprüfen Sie, dass ausgemusterte Modellartefakte gemäß dokumentierten Datenaufbewahrungsrichtlinien sicher durch kryptografische Löschung oder mehrfaches Überschreiben gelöscht werden, und verwenden Sie verifizierte Vernichtungszertifikate. |   1    |  D/V  |
| 3.6.3 | Stellen Sie sicher, dass Modellstilllegungsereignisse mit Zeitstempel und Identität des Akteurs protokolliert werden und Modellsignaturen widerrufen werden, um eine Wiederverwendung zu verhindern.                                               |   2    |   V   |
| 3.6.4 | Überprüfen Sie, ob die Notfallabschaltung von Modellen den Modellzugriff innerhalb vorab festgelegter Notfallreaktionszeiten durch automatisierte Abschaltvorrichtungen deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.      |   2    |  D/V  |

---

## Referenzen

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

