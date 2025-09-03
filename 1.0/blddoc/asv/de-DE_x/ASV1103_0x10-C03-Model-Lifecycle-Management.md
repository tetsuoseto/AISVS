# C3 Modell-Lebenszyklus-Verwaltung & Änderungssteuerung

## Kontrollziel

KI-Systeme müssen Änderungskontrollprozesse implementieren, die unbefugte oder unsichere Modelländerungen daran hindern, die Produktion zu erreichen. Diese Kontrolle gewährleistet die Integrität des Modells über den gesamten Lebenszyklus--von der Entwicklung über den Einsatz bis zur Außerbetriebnahme--was eine schnelle Reaktion auf Vorfälle ermöglicht und die Verantwortlichkeit für alle Änderungen sicherstellt.

Kernziel der Sicherheit: Nur autorisierte, validierte Modelle gelangen durch den Einsatz kontrollierter Prozesse in die Produktion, wodurch Integrität, Nachvollziehbarkeit und Wiederherstellbarkeit gewährleistet werden.

---

## C3.1 Modellautorisierung & Integrität

Nur autorisierte Modelle mit verifizierter Integrität gelangen in Produktionsumgebungen.

|   #   | Beschreibung                                                                                                                                                                                                                                                   | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.1.1 | Verifizieren Sie, dass alle Modellartefakte (Gewichte, Konfigurationen, Tokenizers) vor der Bereitstellung kryptografisch von autorisierten Parteien signiert sind.                                                                                            |   1   |  D/V  |
| 3.1.2 | Stellen Sie sicher, dass die Integrität des Modells zum Zeitpunkt der Bereitstellung validiert wird, und dass Fehler bei der Signaturprüfung das Laden des Modells verhindern.                                                                                 |   1   |  D/V  |
| 3.1.3 | Stellen Sie sicher, dass die Modellprovenienzaufzeichnungen die Identität einer autorisierenden Entität, Prüfsummen der Trainingsdaten, Validierungstestergebnisse mit dem Status Bestanden bzw. Nicht bestanden sowie einen Erstellungszeitstempel enthalten. |   2   |  D/V  |
| 3.1.4 | Stellen Sie sicher, dass alle Modellartefakte semantische Versionsnummern verwenden (MAJOR.MINOR.PATCH) und dass dokumentierte Kriterien vorliegen, die festlegen, wann jede Versionsebene erhöht wird.                                                        |   2   |  D/V  |
| 3.1.5 | Überprüfen Sie, ob die Abhängigkeitsverfolgung ein Echtzeit-Inventar aufrechterhält, das eine schnelle Identifizierung aller verbrauchenden Systeme ermöglicht.                                                                                                |   2   |   V   |

---

## C3.2 Modellvalidierung und Tests

Modelle müssen vor der Bereitstellung definierte Sicherheits- und Zuverlässigkeitsprüfungen bestehen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                    | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.2.1 | Vergewissern Sie sich, dass Modelle automatisierte Sicherheitsprüfungen durchlaufen, die Eingabevalidierung, Ausgabensanitisierung und Sicherheitsbewertungen umfassen, mit vorab vereinbarten organisatorischen Bestehen/Nichtbestehen-Schwellenwerten vor der Bereitstellung. |   1   |  D/V  |
| 3.2.2 | Stellen Sie sicher, dass Validierungsfehler die Bereitstellung des Modells automatisch blockieren, nachdem eine ausdrückliche Ausnahmengenehmigung durch vordefiniertes befugtes Personal mit dokumentierten geschäftlichen Begründungen erteilt wurde.                         |   1   |  D/V  |
| 3.2.3 | Verifizieren Sie, dass Testergebnisse kryptografisch signiert sind und unveränderlich mit dem spezifischen Modellversions-Hash verknüpft sind, der validiert wird.                                                                                                              |   2   |   V   |
| 3.2.4 | Verifizieren Sie, dass Notfallbereitstellungen eine dokumentierte Sicherheitsrisikobewertung sowie die Genehmigung durch eine vorher festgelegte Sicherheitsbehörde innerhalb der vorab vereinbarten Fristen erfordern.                                                         |   2   |  D/V  |

---

## Kontrollierte Bereitstellung und Rollback

Modellbereitstellungen müssen kontrolliert, überwacht und umkehrbar sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                         | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.3.1 | Stellen Sie sicher, dass Produktionsbereitstellungen schrittweise Rollout-Mechanismen (Canary-Deployments, Blue-Green-Deployments) mit automatischen Rollback-Auslösern implementieren, basierend auf vorab vereinbarten Fehlerraten, Latenzschwellen oder Sicherheitswarnkriterien. |   1   |   D   |
| 3.3.2 | Überprüfen Sie, dass Rollback-Funktionen den vollständigen Modellzustand (Gewichte, Konfigurationen, Abhängigkeiten) atomar innerhalb vordefinierter organisatorischer Zeitfenster wiederherstellen.                                                                                 |   1   |  D/V  |
| 3.3.3 | Stellen Sie sicher, dass Bereitstellungsprozesse kryptografische Signaturen validieren und Integritätsprüfsummen berechnen, bevor das Modell aktiviert wird, und dass die Bereitstellung bei jeder Abweichung fehlschlägt.                                                           |   2   |  D/V  |
| 3.3.4 | Überprüfen Sie, ob Notabschaltfunktionen des Modells die Endpunkte innerhalb vordefinierter Reaktionszeiten deaktivieren können – entweder durch automatisierte Circuit-Breaker oder durch manuelle Kill-Schalter.                                                                   |   2   |  D/V  |
| 3.3.5 | Überprüfen Sie, ob Rollback-Artefakte (frühere Modellversionen, Konfigurationen, Abhängigkeiten) gemäß den organisatorischen Richtlinien mit unveränderlichem Speicher für die Vorfallreaktion aufbewahrt werden.                                                                    |   2   |   V   |

---

## C3.4 Änderungsverantwortlichkeit & Audit

Alle Änderungen am Lebenszyklus des Modells müssen nachvollziehbar und auditierbar sein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                     | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 3.4.1 | Stellen Sie sicher, dass alle Modelländerungen (Bereitstellung, Konfiguration, Stilllegung) unveränderliche Auditprotokolle erzeugen, die einen Zeitstempel, eine authentifizierte Identität des Akteurs, eine Änderungsart und Vorher- und Nachherzustände enthalten.                           |   1   |   V   |
| 3.4.2 | Überprüfen Sie, dass der Zugriff auf das Audit-Log eine angemessene Autorisierung erfordert und alle Zugriffsversuche mit Benutzeridentität und einem Zeitstempel protokolliert werden.                                                                                                          |   2   |  D/V  |
| 3.4.3 | Vergewissern Sie sich, dass Prompt-Vorlagen und Systemmeldungen in Git-Repositories versioniert sind, mit obligatorischer Code-Review und Freigabe durch festgelegte Prüfer vor dem Deployment.                                                                                                  |   2   |  D/V  |
| 3.4.4 | Stellen Sie sicher, dass Auditprotokolle ausreichende Details enthalten (Modell-Hashes, Konfigurations-Schnappschüsse und Versionsangaben der Abhängigkeiten), um eine vollständige Rekonstruktion des Modellzustands für jeden Zeitstempel innerhalb des Aufbewahrungszeitraums zu ermöglichen. |   2   |   V   |

---

## C3.5 Sichere Softwareentwicklungspraktiken

Die Modellentwicklung und die Trainingsprozesse müssen sicheren Praktiken folgen, um eine Kompromittierung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                        | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.5.1 | Überprüfen Sie, ob Modellentwicklungs-, Test- und Produktionsumgebungen physisch oder logisch voneinander getrennt sind. Sie haben keine gemeinsame Infrastruktur, unterschiedliche Zugriffskontrollen und isolierte Datenspeicher. |   1   |   D   |
| 3.5.2 | Stellen Sie sicher, dass das Modelltraining und die Feinabstimmung in isolierten Umgebungen mit kontrolliertem Netzwerkzugang erfolgen.                                                                                             |   1   |   D   |
| 3.5.3 | Stellen Sie sicher, dass Trainingsdatenquellen vor der Verwendung in der Modellentwicklung durch Integritätsprüfungen validiert und über vertrauenswürdige Quellen authentifiziert werden, mit einer dokumentierten Herkunftskette. |   1   |  D/V  |
| 3.5.4 | Stellen Sie sicher, dass Artefakte der Modellentwicklung (Hyperparameter, Trainingsskripte, Konfigurationsdateien) in der Versionskontrolle gespeichert werden und vor dem Training eine Peer-Review-Genehmigung erforderlich ist.  |   2   |   D   |

---

## C3.6 Modellstilllegung und Außerbetriebnahme

Modelle müssen sicher außer Betrieb genommen werden, wenn sie nicht mehr benötigt werden oder wenn Sicherheitsprobleme identifiziert werden.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                 | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 3.6.1 | Stellen Sie sicher, dass die Modellstilllegungsprozesse automatisch Abhängigkeitsgraphen scannen, alle darauf zugreifenden Systeme identifizieren und vorab vereinbarte Vorankündigungsfristen vor der Stilllegung bereitstellen.                                                            |   1   |   D   |
| 3.6.2 | Stellen Sie sicher, dass ausrangierte Modellartefakte gemäß dokumentierter Richtlinien zur Datenaufbewahrung sicher gelöscht werden, entweder durch kryptografische Vernichtung oder durch Überschreibung mit mehreren Durchgängen, und dass verifizierte Vernichtungszertifikate vorliegen. |   1   |  D/V  |
| 3.6.3 | Überprüfen Sie, dass Modellstilllegungsereignisse mit Zeitstempel und Identität des Akteurs protokolliert werden, und dass Modellsignaturen widerrufen werden, um eine Wiederverwendung zu verhindern.                                                                                       |   2   |   V   |
| 3.6.4 | Stellen Sie sicher, dass die Notfall-Modellabschaltung den Zugriff auf das Modell innerhalb der vorab festgelegten Notfall-Reaktionszeiträume durch automatisierte Kill-Schalter deaktivieren kann, falls kritische Sicherheitslücken entdeckt werden.                                       |   2   |  D/V  |

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

