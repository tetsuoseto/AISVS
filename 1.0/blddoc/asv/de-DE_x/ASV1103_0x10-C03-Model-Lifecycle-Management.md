# C3 Modell-Lebenszyklusverwaltung & Änderungssteuerung

## Kontrollziel

KI-Systeme müssen Änderungssteuerungsprozesse implementieren, die verhindern, dass unautorisierte oder unsichere Modelländerungen in die Produktion gelangen. Diese Kontrolle gewährleistet die Integrität des Modells über den gesamten Lebenszyklus hinweg – von der Entwicklung über die Bereitstellung bis zur Außerdienststellung – und ermöglicht eine schnelle Reaktion auf Zwischenfälle sowie die Nachvollziehbarkeit aller Änderungen.

Kernziel der Sicherheit: Nur autorisierte, validierte Modelle gelangen durch kontrollierte Prozesse, die Integrität, Rückverfolgbarkeit und Wiederherstellbarkeit gewährleisten, in die Produktion.

---

## C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit überprüfter Integrität gelangen in Produktionsumgebungen.

|   #   | Beschreibung                                                                                                                                                                                                                                  | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.1.1 | Stellen Sie sicher, dass alle Modellartefakte (Gewichte, Konfigurationen, Tokenizer) vor der Bereitstellung kryptografisch von autorisierten Stellen signiert sind.                                                                           |   1   |  D/V  |
| 3.1.2 | Stellen Sie sicher, dass die Modellintegrität zur Bereitstellungszeit validiert wird und Signaturprüfungsfehler das Laden des Modells verhindern.                                                                                             |   1   |  D/V  |
| 3.1.3 | Überprüfen Sie, ob die Herkunftsaufzeichnungen des Modells die Identität der autorisierenden Entität, Prüfsummen der Trainingsdaten, Validierungstestergebnisse mit Bestehen/Nichtbestehen-Status und einen Erstellungszeitstempel enthalten. |   2   |  D/V  |
| 3.1.4 | Stellen Sie sicher, dass alle Modellartefakte eine semantische Versionsnummerierung (MAJOR.MINOR.PATCH) verwenden, mit dokumentierten Kriterien, die angeben, wann jede Versionskomponente erhöht wird.                                       |   2   |  D/V  |
| 3.1.5 | Überprüfen Sie, ob die Abhängigkeitsverfolgung ein Echtzeit-Inventar führt, das eine schnelle Identifizierung aller Verbrauchersysteme ermöglicht.                                                                                            |   2   |   V   |

---

## C3.2 Modellvalidierung & Test

Modelle müssen vor der Bereitstellung definierte Sicherheits- und Schutzvalidierungen bestehen.

|   #   | Beschreibung                                                                                                                                                                                                                                                             | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.2.1 | Stellen Sie sicher, dass Modelle automatisierten Sicherheitstests unterzogen werden, die Eingabevalidierung, Ausgabe-Sanitierung und Sicherheitsevaluierungen mit vorab vereinbarten organisatorischen Bestehens-/Nichtbestehensgrenzen vor der Bereitstellung umfassen. |   1   |  D/V  |
| 3.2.2 | Verifizieren Sie, dass Validierungsfehler nach expliziter Überschreibungsfreigabe durch vordefinierte autorisierte Personen mit dokumentierten geschäftlichen Begründungen automatisch die Modellbereitstellung blockieren.                                              |   1   |  D/V  |
| 3.2.3 | Überprüfen Sie, dass Testergebnisse kryptografisch signiert und unveränderlich mit dem spezifischen Modellversions-Hash, der validiert wird, verknüpft sind.                                                                                                             |   2   |   V   |
| 3.2.4 | Stellen Sie sicher, dass Notfalleinsätze eine dokumentierte Sicherheitsrisikobewertung und die Genehmigung durch eine vorab festgelegte Sicherheitsinstanz innerhalb vorab vereinbarter Zeitrahmen erfordern.                                                            |   2   |  D/V  |

---

## C3.3 Kontrollierte Bereitstellung & Rücknahme

Modellbereitstellungen müssen kontrolliert, überwacht und umkehrbar sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                               | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.3.1 | Stellen Sie sicher, dass Produktionsbereitstellungen schrittweise Rollout-Mechanismen (Canary-Deployments, Blue-Green-Deployments) mit automatischen Rollback-Auslösern basierend auf vorab vereinbarten Fehlerquoten, Latenzschwellenwerten oder Sicherheitswarnkriterien implementieren. |   1   |   D   |
| 3.3.2 | Stellen Sie sicher, dass die Rollback-Fähigkeiten den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vordefinierter organisatorischer Zeitfenster wiederherstellen.                                                                              |   1   |  D/V  |
| 3.3.3 | Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen vor der Modellaktivierung berechnen, wobei die Bereitstellung bei jeglicher Abweichung fehlschlägt.                                                                       |   2   |  D/V  |
| 3.3.4 | Überprüfen Sie, dass Notfall-Modelabschaltfunktionen Modellendpunkte innerhalb vorgegebener Reaktionszeiten über automatisierte Stromkreisunterbrecher oder manuelle Not-Aus-Schalter deaktivieren können.                                                                                 |   2   |  D/V  |
| 3.3.5 | Stellen Sie sicher, dass Rücksetz-Artefakte (vorherige Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderbarem Speicher für die Vorfallreaktion aufbewahrt werden.                                                                   |   2   |   V   |

---

## C3.4 Änderung Verantwortlichkeit & Prüfung

Alle Änderungen im Lebenszyklus des Modells müssen nachvollziehbar und prüfbar sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.4.1 | Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Außerbetriebnahme) unveränderliche Audit-Protokolle erzeugen, die einen Zeitstempel, eine authentifizierte Akteursidentität, einen ÄnderungsTyp sowie Vorher-/Nachher-Zustände enthalten.    |   1   |   V   |
| 3.4.2 | Stellen Sie sicher, dass für den Zugriff auf das Audit-Protokoll eine geeignete Autorisierung erforderlich ist und dass alle Zugriffsversuche mit Benutzeridentität und Zeitstempel protokolliert werden.                                                                   |   2   |  D/V  |
| 3.4.3 | Stellen Sie sicher, dass Prompt-Vorlagen und Systemnachrichten versionskontrolliert in Git-Repositories sind, mit verpflichtender Codeüberprüfung und Genehmigung durch festgelegte Prüfer vor der Bereitstellung.                                                          |   2   |  D/V  |
| 3.4.4 | Überprüfen Sie, ob die Prüfungsprotokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Snapshots, Abhängigkeitsversionen), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitpunkt innerhalb des Aufbewahrungszeitraums zu ermöglichen. |   2   |   V   |

---

## C3.5 Sichere Entwicklungspraktiken

Modellentwicklungs- und Trainingsprozesse müssen sichere Praktiken befolgen, um Kompromittierungen zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                                                         | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.5.1 | Stellen Sie sicher, dass die Entwicklungs-, Test- und Produktionsumgebungen des Modells physisch oder logisch getrennt sind. Sie verfügen über keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher.                      |   1   |   D   |
| 3.5.2 | Überprüfen Sie, dass das Modelltraining und die Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang stattfinden.                                                                                                                               |   1   |   D   |
| 3.5.3 | Stellen Sie sicher, dass Trainingsdatenquellen durch Integritätsprüfungen validiert und über vertrauenswürdige Quellen mit dokumentierter Nachweiskette vor der Verwendung in der Modellentwicklung authentifiziert werden.                                          |   1   |  D/V  |
| 3.5.4 | Stellen Sie sicher, dass Artefakte der Modellentwicklung (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionsverwaltung gespeichert werden und eine Genehmigung durch die Peer-Review erforderlich ist, bevor sie im Training verwendet werden. |   2   |   D   |

---

## C3.6 Modellstilllegung & Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme erkannt werden.

|   #   | Beschreibung                                                                                                                                                                                                                                       | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.6.1 | Stellen Sie sicher, dass Modellstilllegungsprozesse automatisch Abhängigkeitsgraphen scannen, alle verbrauchenden Systeme identifizieren und vor der Außerbetriebnahme vorab vereinbarte Vorankündigungsfristen einhalten.                         |   1   |   D   |
| 3.6.2 | Verifizieren Sie, dass ausgemusterte Modell-Artefakte gemäß dokumentierten Datenaufbewahrungsrichtlinien sicher durch kryptografische Löschung oder mehrfaches Überschreiben gelöscht werden, wobei zertifizierte Vernichtungsnachweise vorliegen. |   1   |  D/V  |
| 3.6.3 | Überprüfen Sie, ob Modell-Ruhestandsereignisse mit Zeitstempel und Identität des Akteurs protokolliert werden und Modell-Signaturen widerrufen werden, um eine Wiederverwendung zu verhindern.                                                     |   2   |   V   |
| 3.6.4 | Überprüfen Sie, ob die Notfallabschaltung von Modellen den Modellzugriff innerhalb vorab festgelegter Notfallreaktionszeiten durch automatisierte Abschaltmechanismen deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.        |   2   |  D/V  |

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

