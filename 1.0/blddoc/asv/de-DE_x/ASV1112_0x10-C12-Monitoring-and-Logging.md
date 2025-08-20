# C12 Überwachung, Protokollierung und Anomalieerkennung

## Kontrollziel

Dieser Abschnitt enthält Anforderungen für die Bereitstellung von Echtzeit- und forensischer Sichtbarkeit darüber, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, bewertet und daraus gelernt werden kann.

## C12.1 Anforderungs- und Antwortprotokollierung

|   #    | Beschreibung                                                                                                                                                                                                                                                                                        | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.1.1 | Stellen Sie sicher, dass alle Benutzeranfragen und Modellantworten mit den entsprechenden Metadaten (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion) protokolliert werden.                                                                                                              |   1   |  D/V  |
| 12.1.2 | Stellen Sie sicher, dass Protokolle in sicheren, zugangskontrollierten Repositories mit geeigneten Aufbewahrungsrichtlinien und Sicherungsverfahren gespeichert werden.                                                                                                                             |   1   |  D/V  |
| 12.1.3 | Überprüfen Sie, ob Log-Speichersysteme Verschlüsselung im Ruhezustand und während der Übertragung implementieren, um sensible Informationen in den Protokollen zu schützen.                                                                                                                         |   1   |  D/V  |
| 12.1.4 | Stellen Sie sicher, dass sensible Daten in Eingabeaufforderungen und Ausgaben vor dem Protokollieren automatisch unkenntlich gemacht oder maskiert werden, mit konfigurierbaren Regeln zur Unkenntlichmachung für personenbezogene Daten (PII), Anmeldeinformationen und proprietäre Informationen. |   1   |  D/V  |
| 12.1.5 | Verifizieren Sie, dass Richtlinienentscheidungen und Maßnahmen zur Sicherheitsfilterung mit ausreichenden Details protokolliert werden, um die Überprüfung und Fehlerbehebung von Inhaltsmoderationssystemen zu ermöglichen.                                                                        |   2   |  D/V  |
| 12.1.6 | Stellen Sie sicher, dass die Protokollintegrität durch z. B. kryptografische Signaturen oder schreibgeschützten Speicher geschützt ist.                                                                                                                                                             |   2   |  D/V  |

---

## C12.2 Missbrauchserkennung und Alarmierung

|   #    | Beschreibung                                                                                                                                                                                                           | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.2.1 | Überprüfen Sie, ob das System bekannte Jailbreak-Muster, Prompt-Injektionsversuche und adversariale Eingaben mithilfe von signaturbasierter Erkennung erkennt und meldet.                                              |   1   |  D/V  |
| 12.2.2 | Überprüfen Sie, ob das System sich mit bestehenden Security Information and Event Management (SIEM)-Plattformen unter Verwendung standardisierter Protokollformate und -protokolle integriert.                         |   1   |  D/V  |
| 12.2.3 | Verifizieren Sie, dass angereicherte Sicherheitsereignisse KI-spezifische Kontexte wie Modellkennungen, Konfidenzwerte und Entscheidungen des Sicherheitsfilters enthalten.                                            |   2   |  D/V  |
| 12.2.4 | Stellen Sie sicher, dass die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematische Abtastverhalten identifiziert.                                             |   2   |  D/V  |
| 12.2.5 | Überprüfen Sie, ob Echtzeit-Benachrichtigungsmechanismen die Sicherheitsteams informieren, wenn potenzielle Richtlinienverletzungen oder Angriffsversuche erkannt werden.                                              |   2   |  D/V  |
| 12.2.6 | Überprüfen Sie, ob benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster einschließlich koordinierter Jailbreak-Versuche, Prompt-Injektionskampagnen und Modellextraktionsangriffe zu erkennen. |   2   |  D/V  |
| 12.2.7 | Überprüfen Sie, dass automatisierte Abläufe zur Vorfallreaktion kompromittierte Modelle isolieren, bösartige Benutzer blockieren und kritische Sicherheitsereignisse eskalieren können.                                |   3   |  D/V  |

---

## C12.3 Modellabweichungserkennung

|   #    | Beschreibung                                                                                                                                                                                         | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.3.1 | Überprüfen Sie, ob das System grundlegende Leistungskennzahlen wie Genauigkeit, Vertrauenswerte, Latenz und Fehlerraten über Modellversionen und Zeiträume hinweg verfolgt.                          |   1   |  D/V  |
| 12.3.2 | Überprüfen Sie, ob automatisierte Benachrichtigungen ausgelöst werden, wenn Leistungskennzahlen vordefinierte Verschlechterungsschwellen überschreiten oder erheblich von den Basiswerten abweichen. |   2   |  D/V  |
| 12.3.3 | Überprüfen Sie, ob die Halluzinationserkennungsmonitore Instanzen identifizieren und kennzeichnen, bei denen Modelloutputs faktisch falsche, inkonsistente oder erfundene Informationen enthalten.   |   2   |  D/V  |

---

## C12.4 Leistungs- und Verhaltens-Telemetrie

|   #    | Beschreibung                                                                                                                                                                                                | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.4.1 | Stellen Sie sicher, dass betriebliche Metriken wie Anfragelatenz, Token-Verbrauch, Speichernutzung und Durchsatz kontinuierlich erfasst und überwacht werden.                                               |   1   |  D/V  |
| 12.4.2 | Stellen Sie sicher, dass Erfolgs- und Fehlerquoten mit Kategorisierung der Fehlertypen und ihrer Ursachen verfolgt werden.                                                                                  |   1   |  D/V  |
| 12.4.3 | Stellen Sie sicher, dass die Überwachung der Ressourcenauslastung die GPU-/CPU-Nutzung, den Speicherverbrauch und die Speicheranforderungen umfasst und bei Überschreiten von Schwellwerten Alarme auslöst. |   2   |  D/V  |

---

## C12.5 Planung und Durchführung der KI-Zwischenfallreaktion

|   #    | Beschreibung                                                                                                                                                                                                                 | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Stellen Sie sicher, dass die Reaktionspläne für Sicherheitsvorfälle speziell AI-bezogene Sicherheitsereignisse wie Modellkompromittierung, Datenvergiftung und adversariale Angriffe abdecken.                               |   1   |  D/V  |
| 12.5.2 | Stellen Sie sicher, dass Incident-Response-Teams Zugang zu KI-spezifischen forensischen Werkzeugen und Fachwissen haben, um Modellverhalten und Angriffsvektoren zu untersuchen.                                             |   2   |  D/V  |
| 12.5.3 | Stellen Sie sicher, dass die Analyse nach Zwischenfällen Überlegungen zur Modellneutrainierung, Aktualisierungen der Sicherheitsfilter und die Integration der gewonnenen Erkenntnisse in die Sicherheitskontrollen umfasst. |   3   |  D/V  |

---

## C12.5 KI-Leistungsverschlechterungs-Erkennung

Überwachen und Erkennen von Leistungs- und Qualitätsverschlechterungen bei KI-Modellen im Zeitverlauf.

|   #    | Beschreibung                                                                                                                                                   | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Stellen Sie sicher, dass Modellgenauigkeit, Präzision, Recall und F1-Werte kontinuierlich überwacht und mit den Basislinien-Schwellenwerten verglichen werden. |   1   |  D/V  |
| 12.5.2 | Überprüfen Sie, dass die Erkennung von Datenverschiebungen Änderungen in der Eingabeverteilung überwacht, die die Modellleistung beeinflussen könnten.         |   1   |  D/V  |
| 12.5.3 | Überprüfen Sie, ob die Konzeptdrift-Erkennung Änderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.                             |   2   |  D/V  |
| 12.5.4 | Verifizieren Sie, dass Leistungsabfälle automatisierte Alarme auslösen und Workflows für das erneute Training oder den Austausch von Modellen einleiten.       |   2   |  D/V  |
| 12.5.5 | Überprüfen Sie, ob die Ursachenanalyse für Leistungsabfälle Leistungseinbußen mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert.   |   3   |   V   |

---

## C12.6 DAG-Visualisierung & Workflow-Sicherheit

Schützen Sie Workflow-Visualisierungssysteme vor Informationslecks und Manipulationsangriffen.

|   #    | Beschreibung                                                                                                                                                                                     | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 12.6.1 | Stellen Sie sicher, dass die DAG-Visualisierungsdaten bereinigt werden, um sensible Informationen vor der Speicherung oder Übertragung zu entfernen.                                             |   1   |  D/V  |
| 12.6.2 | Stellen Sie sicher, dass die Zugriffssteuerungen bei der Workflow-Visualisierung gewährleisten, dass nur autorisierte Benutzer Agenten-Entscheidungspfade und Begründungsspuren einsehen können. |   1   |  D/V  |
| 12.6.3 | Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermechanismen geschützt ist.                                               |   2   |  D/V  |
| 12.6.4 | Verifizieren Sie, dass Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injektionsangriffe durch manipulierte Knoten- oder Kantendaten zu verhindern.                  |   2   |  D/V  |
| 12.6.5 | Stellen Sie sicher, dass Echtzeit-DAG-Aktualisierungen eine Drosselung unterliegen und validiert werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.                 |   3   |  D/V  |

---

## C12.7 Proaktive Überwachung sicherheitsrelevanten Verhaltens

Erkennung und Verhinderung von Sicherheitsbedrohungen durch proaktive Analyse des Agentenverhaltens.

|   #    | Beschreibung                                                                                                                                                       | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 12.7.1 | Stellen Sie sicher, dass proaktive Agentenverhalten vor der Ausführung sicherheitsvalidiert sind, einschließlich der Integration einer Risikoanalyse.              |   1   |  D/V  |
| 12.7.2 | Stellen Sie sicher, dass autonome Initiativ-Auslöser die Bewertung des Sicherheitskontexts und die Beurteilung der Bedrohungslage umfassen.                        |   2   |  D/V  |
| 12.7.3 | Überprüfen Sie, ob proaktive Verhaltensmuster auf potenzielle Sicherheitsimplikationen und unbeabsichtigte Folgen analysiert werden.                               |   2   |  D/V  |
| 12.7.4 | Stellen Sie sicher, dass sicherheitskritische proaktive Maßnahmen explizite Genehmigungsketten mit Prüfprotokollen erfordern.                                      |   3   |  D/V  |
| 12.7.5 | Überprüfen Sie, dass die Verhaltensanomalie-Erkennung Abweichungen in den proaktiven Agentenmuster identifiziert, die auf eine Kompromittierung hinweisen könnten. |   3   |  D/V  |

---

## Referenzen

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

