# C12 Überwachung, Protokollierung & Anomalieerkennung

## Kontrollziel

Dieser Abschnitt enthält Anforderungen für die Bereitstellung von Echtzeit- und forensischer Sichtbarkeit dessen, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, eingestuft und daraus gelernt werden kann.

## C12.1 Anforderungs- und Antwortprotokollierung

|   #    | Beschreibung                                                                                                                                                                                                                                                            | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.1.1 | Stellen Sie sicher, dass alle Benutzeranfragen und Modellantworten mit geeigneten Metadaten protokolliert werden (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion).                                                                                          |   1   |  D/V  |
| 12.1.2 | Stellen Sie sicher, dass Protokolle in sicheren, zugriffskontrollierten Repositorien mit angemessenen Aufbewahrungsrichtlinien und Backup-Verfahren gespeichert werden.                                                                                                 |   1   |  D/V  |
| 12.1.3 | Überprüfen Sie, ob Log-Speichersysteme Verschlüsselung sowohl im Ruhezustand als auch während der Übertragung implementieren, um sensible Informationen in den Logs zu schützen.                                                                                        |   1   |  D/V  |
| 12.1.4 | Stellen Sie sicher, dass sensible Daten in Eingabeaufforderungen und Ausgaben vor der Protokollierung automatisch geschwärzt oder maskiert werden, mit konfigurierbaren Schwärzungsregeln für personenbezogene Daten (PII), Zugangsdaten und proprietäre Informationen. |   1   |  D/V  |
| 12.1.5 | Stellen Sie sicher, dass Richtlinienentscheidungen und Maßnahmen zur Sicherheitssfilterung mit ausreichenden Details protokolliert werden, um die Prüfung und Fehlerbehebung von Inhaltenmoderationssystemen zu ermöglichen.                                            |   2   |  D/V  |
| 12.1.6 | Stellen Sie sicher, dass die Protokollintegrität beispielsweise durch kryptografische Signaturen oder schreibgeschützten Speicher geschützt ist.                                                                                                                        |   2   |  D/V  |

---

## C12.2 Missbrauchserkennung und Alarmierung

|   #    | Beschreibung                                                                                                                                                                                                             | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 12.2.1 | Überprüfen Sie, dass das System bekannte Jailbreak-Muster, Versuche der Prompt-Injektion und adversariale Eingaben mithilfe der signaturbasierten Erkennung erkennt und meldet.                                          |   1   |  D/V  |
| 12.2.2 | Stellen Sie sicher, dass das System mit bestehenden Security Information and Event Management (SIEM)-Plattformen unter Verwendung standardisierter Protokollformate und -protokolle integriert wird.                     |   1   |  D/V  |
| 12.2.3 | Stellen Sie sicher, dass angereicherte Sicherheitsereignisse KI-spezifische Kontexte wie Modellkennungen, Vertrauenswerte und Entscheidungen des Sicherheitsfilters enthalten.                                           |   2   |  D/V  |
| 12.2.4 | Überprüfen Sie, ob die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematische Erkundungsverhalten erkennt.                                                       |   2   |  D/V  |
| 12.2.5 | Überprüfen Sie, ob Echtzeit-Alarmmechanismen die Sicherheitsteams benachrichtigen, wenn potenzielle Richtlinienverstöße oder Angriffsversuche erkannt werden.                                                            |   2   |  D/V  |
| 12.2.6 | Überprüfen Sie, ob benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster zu erkennen, einschließlich koordinierter Jailbreak-Versuche, Prompt-Injektionskampagnen und Modell-Extraktionsangriffe. |   2   |  D/V  |
| 12.2.7 | Überprüfen Sie, ob automatisierte Abläufe zur Vorfallreaktion kompromittierte Modelle isolieren, bösartige Benutzer blockieren und kritische Sicherheitsereignisse eskalieren können.                                    |   3   |  D/V  |

---

## C12.3 Modellerkennungsverschiebung

|   #    | Beschreibung                                                                                                                                                                                             | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.3.1 | Stellen Sie sicher, dass das System grundlegende Leistungskennzahlen wie Genauigkeit, Vertrauenswerte, Latenz und Fehlerraten über Modellversionen und Zeiträume hinweg verfolgt.                        |   1   |  D/V  |
| 12.3.2 | Überprüfen Sie, dass automatisierte Warnmeldungen ausgelöst werden, wenn Leistungskennzahlen vordefinierte Schwellenwerte für Verschlechterungen überschreiten oder erheblich von Basiswerten abweichen. |   2   |  D/V  |
| 12.3.3 | Stellen Sie sicher, dass die Halluzinations-Erkennungsmonitore Fälle identifizieren und markieren, in denen die Modellausgaben faktisch falsche, inkonsistente oder erfundene Informationen enthalten.   |   2   |  D/V  |

---

## C12.4 Leistungs- und Verhaltens-Telemetrie

|   #    | Beschreibung                                                                                                                                                                                                    | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.4.1 | Stellen Sie sicher, dass Betriebsmetriken wie Anforderungsverzögerung, Token-Verbrauch, Speichernutzung und Durchsatz kontinuierlich erfasst und überwacht werden.                                              |   1   |  D/V  |
| 12.4.2 | Stellen Sie sicher, dass Erfolgs- und Fehlerraten mit Kategorisierung der Fehlertypen und deren Ursachen erfasst werden.                                                                                        |   1   |  D/V  |
| 12.4.3 | Überprüfen Sie, ob die Überwachung der Ressourcenauslastung die GPU-/CPU-Nutzung, den Speicherverbrauch und die Speicheranforderungen umfasst und bei Überschreiten von Schwellenwerten Alarmmeldungen ausgibt. |   2   |  D/V  |

---

## C12.5 Planung und Durchführung der Reaktion auf KI-Vorfälle

|   #    | Beschreibung                                                                                                                                                                                                           | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Überprüfen Sie, ob die Reaktionspläne für Vorfälle speziell AI-bezogene Sicherheitsereignisse wie Modellkompromittierung, Datenvergiftung und adversarielle Angriffe abdecken.                                         |   1   |  D/V  |
| 12.5.2 | Stellen Sie sicher, dass Incident-Response-Teams Zugriff auf KI-spezifische forensische Werkzeuge und Fachkenntnisse haben, um das Modellverhalten und Angriffsvektoren zu untersuchen.                                |   2   |  D/V  |
| 12.5.3 | Stellen Sie sicher, dass die Analyse nach dem Vorfall Überlegungen zur Modellneuschulung, Aktualisierungen der Sicherheitsfilter und die Integration der gewonnenen Erkenntnisse in die Sicherheitskontrollen umfasst. |   3   |  D/V  |

---

## C12.5 Erkennung von Leistungsabfällen bei KI

Überwachen und Erkennen von Verschlechterungen in der Leistungsfähigkeit und Qualität von KI-Modellen im Zeitverlauf.

|   #    | Beschreibung                                                                                                                                                               | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Stellen Sie sicher, dass Modellgenauigkeit, Präzision, Recall und F1-Werte kontinuierlich überwacht und mit den Basisschwellenwerten verglichen werden.                    |   1   |  D/V  |
| 12.5.2 | Verifizieren Sie, dass die Erkennung von Datenverschiebungen Änderungen der Eingabeverteilung überwacht, die die Modellleistung beeinträchtigen könnten.                   |   1   |  D/V  |
| 12.5.3 | Überprüfen Sie, ob die Erkennung von Konzeptveränderungen Änderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.                             |   2   |  D/V  |
| 12.5.4 | Überprüfen Sie, ob Leistungsabfälle automatisierte Warnungen auslösen und Workflows für die Modellneu- oder -ersetzung einleiten.                                          |   2   |  D/V  |
| 12.5.5 | Stellen Sie sicher, dass die Ursachenanalyse der Leistungsverschlechterung Leistungsabfälle mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert. |   3   |   V   |

---

## C12.6 DAG-Visualisierung & Workflow-Sicherheit

Schützen Sie Workflow-Visualisierungssysteme vor Informationslecks und Manipulationsangriffen.

|   #    | Beschreibung                                                                                                                                                                                          | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.6.1 | Stellen Sie sicher, dass die DAG-Visualisierungsdaten vor der Speicherung oder Übertragung bereinigt werden, um sensible Informationen zu entfernen.                                                  |   1   |  D/V  |
| 12.6.2 | Überprüfen Sie, ob die Zugriffssteuerungen für die Workflow-Visualisierung gewährleisten, dass nur autorisierte Benutzer die Entscheidungswege des Agenten und die Begründungsspuren einsehen können. |   1   |  D/V  |
| 12.6.3 | Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermechanismen geschützt ist.                                                    |   2   |  D/V  |
| 12.6.4 | Verifizieren Sie, dass Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injections-Angriffe durch manipulierte Knoten- oder Kantendaten zu verhindern.                      |   2   |  D/V  |
| 12.6.5 | Überprüfen Sie, ob Echtzeit-Updates des DAG einer Ratenbegrenzung unterliegen und validiert werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.                           |   3   |  D/V  |

---

## C12.7 Proaktives Verhalten zur Sicherheitsüberwachung

Erkennung und Verhinderung von Sicherheitsbedrohungen durch proaktive Analyse des Agentenverhaltens.

|   #    | Beschreibung                                                                                                                                                         | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.7.1 | Stellen Sie sicher, dass proaktive Agentenverhalten vor der Ausführung mit einer Risikoabschätzung validiert werden.                                                 |   1   |  D/V  |
| 12.7.2 | Überprüfen Sie, ob autonome Initiativauslöser die Bewertung des Sicherheitskontexts und die Analyse der Bedrohungslandschaft umfassen.                               |   2   |  D/V  |
| 12.7.3 | Überprüfen Sie, ob proaktive Verhaltensmuster auf potenzielle Sicherheitsimplikationen und unbeabsichtigte Konsequenzen analysiert werden.                           |   2   |  D/V  |
| 12.7.4 | Stellen Sie sicher, dass sicherheitskritische proaktive Maßnahmen explizite Genehmigungsketten mit Audit-Trails erfordern.                                           |   3   |  D/V  |
| 12.7.5 | Verifizieren Sie, dass die Verhaltensanomalieerkennung Abweichungen in den Mustern proaktiver Agenten identifiziert, die auf eine Kompromittierung hinweisen können. |   3   |  D/V  |

---

## Referenzen

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

