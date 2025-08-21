# C3 Modell-Lebenszyklusverwaltung & Änderungssteuerung

## Steuerungsziel

KI-Systeme müssen Änderungssteuerungsprozesse implementieren, die verhindern, dass unautorisierte oder unsichere Modelländerungen in die Produktion gelangen. Diese Kontrolle gewährleistet die Modellintegrität während des gesamten Lebenszyklus – von der Entwicklung über die Bereitstellung bis hin zur Stilllegung – und ermöglicht eine schnelle Reaktion auf Vorfälle sowie die Aufrechterhaltung der Verantwortlichkeit für alle Änderungen.

Kernziel der Sicherheit: Nur autorisierte, validierte Modelle gelangen durch den Einsatz kontrollierter Prozesse, die Integrität, Rückverfolgbarkeit und Wiederherstellbarkeit gewährleisten, in die Produktion.

---

## C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit verifizierter Integrität gelangen in Produktionsumgebungen.

|   #   | Beschreibung                                                                                                                                                                                                                         | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.1.1 | Stellen Sie sicher, dass alle Modellartefakte (Gewichte, Konfigurationen, Tokenizer) vor der Implementierung kryptografisch von autorisierten Stellen signiert sind.                                                                 |   1   |  D/V  |
| 3.1.2 | Stellen Sie sicher, dass die Integrität des Modells zum Zeitpunkt der Bereitstellung überprüft wird und dass Signaturprüfungsfehler das Laden des Modells verhindern.                                                                |   1   |  D/V  |
| 3.1.3 | Überprüfen Sie, ob die Modellherkunftsaufzeichnungen die Identität der genehmigenden Stelle, Prüfsummen der Trainingsdaten, Validierungstestergebnisse mit Bestehen/Nichtbestehen-Status und einen Erstellungszeitstempel enthalten. |   2   |  D/V  |
| 3.1.4 | Stellen Sie sicher, dass alle Modell-Artefakte semantische Versionsnummern (MAJOR.MINOR.PATCH) verwenden, mit dokumentierten Kriterien, die angeben, wann jede Versionskomponente erhöht wird.                                       |   2   |  D/V  |
| 3.1.5 | Überprüfen Sie, ob die Abhängigkeitsverfolgung ein Echtzeit-Inventar führt, das eine schnelle Identifizierung aller verbrauchenden Systeme ermöglicht.                                                                               |   2   |   V   |

---

## C3.2 Modellvalidierung & Testen

Modelle müssen vor der Bereitstellung definierte Sicherheits- und Schutzvalidierungen bestehen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.2.1 | Stellen Sie sicher, dass Modelle automatisierten Sicherheitstests unterzogen werden, die Eingabevalidierung, Ausgabe-Sanitierung und Sicherheitsbewertungen mit zuvor vereinbarten organisatorischen Bestehens-/Nichtbestehensgrenzen vor der Bereitstellung umfassen.      |   1   |  D/V  |
| 3.2.2 | Stellen Sie sicher, dass Validierungsfehler die Bereitstellung des Modells automatisch blockieren, es sei denn, es liegt eine ausdrückliche Genehmigung zum Überschreiben von zuvor festgelegtem autorisiertem Personal mit dokumentierten geschäftlichen Begründungen vor. |   1   |  D/V  |
| 3.2.3 | Überprüfen Sie, ob die Testergebnisse kryptografisch signiert und unveränderlich mit dem zu validierenden Hash der spezifischen Modellversion verknüpft sind.                                                                                                               |   2   |   V   |
| 3.2.4 | Stellen Sie sicher, dass Notfalleinsätze eine dokumentierte Sicherheitsrisikobewertung und die Genehmigung durch eine vorgesehene Sicherheitsinstanz innerhalb vorher vereinbarter Zeitrahmen erfordern.                                                                    |   2   |  D/V  |

---

## C3.3 Kontrollierte Bereitstellung & Rückrollen

Modellbereitstellungen müssen kontrolliert, überwacht und umkehrbar sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                 | Ebene | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.3.1 | Stellen Sie sicher, dass Produktionseinsätze schrittweise Rollout-Mechanismen implementieren (Canary-Deployments, Blue-Green-Deployments) mit automatisierten Rückroll-Auslösern basierend auf vorab vereinbarten Fehlerquoten, Latenzgrenzen oder Sicherheitswarnkriterien. |   1   |   D   |
| 3.3.2 | Stellen Sie sicher, dass Rollback-Fähigkeiten den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vorgegebener organisatorischer Zeitfenster wiederherstellen.                                                                      |   1   |  D/V  |
| 3.3.3 | Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen vor der Modellaktivierung berechnen und die Bereitstellung bei jeglicher Abweichung fehlschlagen.                                                           |   2   |  D/V  |
| 3.3.4 | Überprüfen Sie, dass Notabschaltfunktionen für das Modell die Modellendpunkte innerhalb vorgegebener Reaktionszeiten über automatisierte Stromkreise oder manuelle Abschaltschalter deaktivieren können.                                                                     |   2   |  D/V  |
| 3.3.5 | Verifizieren Sie, dass Rollback-Artefakte (vorherige Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderbarem Speicher für die Vorfallreaktion aufbewahrt werden.                                                       |   2   |   V   |

---

## C3.4 Verantwortlichkeit für Änderungen & Audit

Alle Änderungen im Modelllebenszyklus müssen nachvollziehbar und überprüfbar sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                            | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.4.1 | Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Stilllegung) unveränderliche Prüfprotokolle erzeugen, die einen Zeitstempel, eine authentifizierte Akteursidentität, einen Änderungstyp sowie Vorher-/Nachher-Zustände enthalten.        |   1   |   V   |
| 3.4.2 | Überprüfen Sie, ob der Zugriff auf das Audit-Log eine entsprechende Autorisierung erfordert und alle Zugriffsversuche mit Benutzeridentität und Zeitstempel protokolliert werden.                                                                                       |   2   |  D/V  |
| 3.4.3 | Stellen Sie sicher, dass Prompt-Vorlagen und Systemnachrichten in Git-Repositories versionskontrolliert sind, wobei vor der Bereitstellung eine obligatorische Codeüberprüfung und Genehmigung durch festgelegte Prüfer erfolgt.                                        |   2   |  D/V  |
| 3.4.4 | Stellen Sie sicher, dass Prüfprotokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Snapshots, Abhängigkeitsversionen), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitstempel innerhalb der Aufbewahrungsfrist zu ermöglichen. |   2   |   V   |

---

## C3.5 Sichere Entwicklungspraktiken

Modellentwicklungs- und Trainingsprozesse müssen sichere Praktiken befolgen, um eine Kompromittierung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                                           | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.5.1 | Stellen Sie sicher, dass die Entwicklungs-, Test- und Produktionsumgebungen für Modelle physisch oder logisch getrennt sind. Sie verfügen über keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher.        |   1   |   D   |
| 3.5.2 | Verifizieren Sie, dass das Modelltraining und die Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang erfolgen.                                                                                                                  |   1   |   D   |
| 3.5.3 | Stellen Sie sicher, dass die Trainingsdatenquellen durch Integritätsprüfungen validiert und vor der Verwendung in der Modellentwicklung über vertrauenswürdige Quellen mit dokumentierter Nachverfolgbarkeit authentifiziert werden.                   |   1   |  D/V  |
| 3.5.4 | Stellen Sie sicher, dass Artefakte der Modellentwicklung (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionskontrolle gespeichert werden und vor der Verwendung im Training eine Genehmigung durch Peer Review erforderlich ist. |   2   |   D   |

---

## C3.6 Modellstilllegung & Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme festgestellt werden.

|   #   | Beschreibung                                                                                                                                                                                                                                                           | Ebene | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.6.1 | Stellen Sie sicher, dass Modell-Rückzugsprozesse automatisch Abhängigkeitsdiagramme scannen, alle konsumierenden Systeme identifizieren und vor der Außerdienststellung vorab vereinbarte Vorankündigungsfristen einhalten.                                            |   1   |   D   |
| 3.6.2 | Stellen Sie sicher, dass ausgemusterte Modellartefakte gemäß den dokumentierten Datenaufbewahrungsrichtlinien durch kryptografische Löschung oder mehrfaches Überschreiben sicher gelöscht werden, und bestätigen Sie dies mit verifizierten Vernichtungszertifikaten. |   1   |  D/V  |
| 3.6.3 | Stellen Sie sicher, dass Modell-Ruhestandsereignisse mit Zeitstempel und Akteursidentität protokolliert werden und Modell-Signaturen widerrufen werden, um eine Wiederverwendung zu verhindern.                                                                        |   2   |   V   |
| 3.6.4 | Überprüfen Sie, ob die Notfallmodellstilllegung den Zugriff auf das Modell innerhalb vorab festgelegter Notfallreaktionszeiträume durch automatisierte Abschaltmechanismen deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.                       |   2   |  D/V  |

---

## Literaturverzeichnis

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

