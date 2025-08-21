# C3 Modell-Lebenszyklusmanagement & Änderungssteuerung

## Kontrollziel

KI-Systeme müssen Änderungssteuerungsprozesse implementieren, die verhindern, dass unautorisierte oder unsichere Modelländerungen in die Produktion gelangen. Diese Kontrolle gewährleistet die Modellintegrität über den gesamten Lebenszyklus hinweg – von der Entwicklung über die Bereitstellung bis zur Außerbetriebnahme – und ermöglicht eine schnelle Reaktion auf Vorfälle sowie die Aufrechterhaltung der Verantwortlichkeit für alle Änderungen.

Kernziel der Sicherheit: Nur autorisierte, validierte Modelle gelangen durch kontrollierte Prozesse, die Integrität, Rückverfolgbarkeit und Wiederherstellbarkeit gewährleisten, in die Produktion.

---

## C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit überprüfter Integrität gelangen in Produktionsumgebungen.

|   #   | Beschreibung                                                                                                                                                                                                                           | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.1.1 | Stellen Sie sicher, dass alle Modellartefakte (Gewichte, Konfigurationen, Tokenizer) vor der Bereitstellung kryptografisch von autorisierten Stellen signiert sind.                                                                    |   1   |  D/V  |
| 3.1.2 | Stellen Sie sicher, dass die Modellintegrität zur Bereitstellungszeit validiert wird und Signaturprüfungsfehler das Laden des Modells verhindern.                                                                                      |   1   |  D/V  |
| 3.1.3 | Verifizieren Sie, dass die Modellherkunftsdaten die Identität der autorisierenden Entität, Prüfsummen der Trainingsdaten, Validierungstest-Ergebnisse mit Bestehens-/Nichtbestehens-Status und einen Erstellungszeitstempel enthalten. |   2   |  D/V  |
| 3.1.4 | Verifizieren Sie, dass alle Modellartefakte semantische Versionsnummern (MAJOR.MINOR.PATCH) verwenden, mit dokumentierten Kriterien, die angeben, wann jede Versionskomponente erhöht wird.                                            |   2   |  D/V  |
| 3.1.5 | Überprüfen Sie, ob die Abhängigkeitsverfolgung ein Echtzeit-Inventar pflegt, das eine schnelle Identifizierung aller verbrauchenden Systeme ermöglicht.                                                                                |   2   |   V   |

---

## C3.2 Modellvalidierung & Testen

Modelle müssen definierte Sicherheits- und Schutzvalidierungen vor der Bereitstellung bestehen.

|   #   | Beschreibung                                                                                                                                                                                                                                                           | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.2.1 | Stellen Sie sicher, dass Modelle automatisierten Sicherheitstests unterzogen werden, die Eingabevalidierung, Ausgabe-Sanitierung und Sicherheitsbewertungen mit vorab festgelegten organisatorischen Bestehens-/Nichtbestehensgrenzen vor der Bereitstellung umfassen. |   1   |  D/V  |
| 3.2.2 | Verifizieren Sie, dass Validierungsfehler die Modellbereitstellung automatisch blockieren, nachdem eine ausdrückliche Ausnahmegenehmigung von vorab benannten autorisierten Personen mit dokumentierten geschäftlichen Begründungen vorliegt.                          |   1   |  D/V  |
| 3.2.3 | Stellen Sie sicher, dass Testergebnisse kryptografisch signiert und unveränderlich mit dem spezifischen Modellversions-Hash, der validiert wird, verknüpft sind.                                                                                                       |   2   |   V   |
| 3.2.4 | Stellen Sie sicher, dass Notfalleinsätze eine dokumentierte Sicherheitsrisikobewertung und die Genehmigung einer vorab benannten Sicherheitsbehörde innerhalb vorab vereinbarter Zeitrahmen erfordern.                                                                 |   2   |  D/V  |

---

## C3.3 Kontrollierte Bereitstellung & Rückrollung

Modelbereitstellungen müssen kontrolliert, überwacht und reversibel sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                        | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.3.1 | Stellen Sie sicher, dass Produktionseinsätze schrittweise Rollout-Mechanismen (Canary-Deployments, Blue-Green-Deployments) mit automatischen Rollback-Auslösern basierend auf vorher vereinbarten Fehlerraten, Latenzschwellenwerten oder Sicherheitsalarmkriterien implementieren. |   1   |   D   |
| 3.3.2 | Stellen Sie sicher, dass Rückrollfunktionen den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vordefinierter organisatorischer Zeitfenster wiederherstellen.                                                                             |   1   |  D/V  |
| 3.3.3 | Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen berechnen, bevor das Modell aktiviert wird, und die Bereitstellung bei jeglicher Abweichung fehlschlägt.                                                           |   2   |  D/V  |
| 3.3.4 | Überprüfen Sie, ob die Notabschaltfunktionen für Modelle Modellendpunkte innerhalb vordefinierter Reaktionszeiten über automatisierte Stromkreise oder manuelle Abschaltvorrichtungen deaktivieren können.                                                                          |   2   |  D/V  |
| 3.3.5 | Stellen Sie sicher, dass Rollback-Artefakte (vorherige Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderlichem Speicher für die Vorfallreaktion aufbewahrt werden.                                                           |   2   |   V   |

---

## C3.4 Änderung der Verantwortlichkeit & Prüfung

Alle Änderungen am Modelllebenszyklus müssen nachvollziehbar und prüfbar sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.4.1 | Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Außerdienststellung) unveränderliche Prüfprotokolle erzeugen, die einen Zeitstempel, eine authentifizierte Akteur-Identität, einen Änderungstyp sowie Vorher-/Nachher-Zustände enthalten.    |   1   |   V   |
| 3.4.2 | Überprüfen Sie, dass der Zugriff auf das Auditprotokoll eine geeignete Autorisierung erfordert und alle Zugriffsversuche mit Benutzeridentität und Zeitstempel protokolliert werden.                                                                                        |   2   |  D/V  |
| 3.4.3 | Stellen Sie sicher, dass Aufforderungsvorlagen und Systemmeldungen in Git-Repositories versionskontrolliert sind und vor der Bereitstellung eine obligatorische Codeüberprüfung und Genehmigung durch festgelegte Prüfer erfolgt.                                           |   2   |  D/V  |
| 3.4.4 | Stellen Sie sicher, dass Prüfprotokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Snapshots, Abhängigkeitsversionen), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitstempel innerhalb des Aufbewahrungszeitraums zu ermöglichen. |   2   |   V   |

---

## C3.5 Sichere Entwicklungsmethoden

Modellentwicklungs- und Trainingsprozesse müssen sicheren Praktiken folgen, um eine Kompromittierung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                                  | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.5.1 | Stellen Sie sicher, dass die Umgebungen für Modellentwicklung, -test und -produktion physisch oder logisch getrennt sind. Sie verfügen über keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher.  |   1   |   D   |
| 3.5.2 | Stellen Sie sicher, dass das Modelltraining und die Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang erfolgen.                                                                                                       |   1   |   D   |
| 3.5.3 | Stellen Sie sicher, dass Trainingsdatenquellen durch Integritätsprüfungen validiert und vor der Verwendung in der Modellentwicklung über vertrauenswürdige Quellen mit dokumentierter Nachweiskette authentifiziert werden.                   |   1   |  D/V  |
| 3.5.4 | Stellen Sie sicher, dass Entwicklungsartefakte des Modells (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionskontrolle gespeichert sind und vor der Verwendung im Training eine Peer-Review-Freigabe erforderlich ist. |   2   |   D   |

---

## C3.6 Modell-Pensionierung & Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme festgestellt werden.

|   #   | Beschreibung                                                                                                                                                                                                                                        | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.6.1 | Überprüfen Sie, dass die Model-Rentierungsprozesse automatisch Abhängigkeitsgraphen scannen, alle konsumierenden Systeme identifizieren und vor der Stilllegung vorab vereinbarte Vorankündigungsfristen einhalten.                                 |   1   |   D   |
| 3.6.2 | Überprüfen Sie, dass archivierte Modellartefakte gemäß den dokumentierten Datenaufbewahrungsrichtlinien sicher durch kryptographische Löschung oder mehrfaches Überschreiben gelöscht werden, wobei verifizierte Vernichtungszertifikate vorliegen. |   1   |  D/V  |
| 3.6.3 | Überprüfen Sie, dass Ereignisse zur Stilllegung von Modellen mit Zeitstempel und Akteur-Identität protokolliert werden und Modell-Signaturen widerrufen werden, um eine Wiederverwendung zu verhindern.                                             |   2   |   V   |
| 3.6.4 | Überprüfen Sie, ob die Notfall-Modelldeaktivierung den Modellzugriff innerhalb vorab festgelegter Notfallreaktionszeiträume durch automatisierte Abschaltmechanismen deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.          |   2   |  D/V  |

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

