# C12 Überwachung, Protokollierung & Anomalieerkennung

## Steuerungsziel

Dieser Abschnitt enthält Anforderungen für die Bereitstellung von Echtzeit- und forensischer Transparenz darüber, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, bewertet und daraus gelernt werden kann.

## C12.1 Anforderungs- und Antwortprotokollierung

|   #    | Beschreibung                                                                                                                                                                                                                                                            | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.1.1 | Stellen Sie sicher, dass alle Benutzereingaben und Modellantworten mit geeigneten Metadaten (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion) protokolliert werden.                                                                                          |   1   |  D/V  |
| 12.1.2 | Stellen Sie sicher, dass Protokolle in sicheren, zugangskontrollierten Repositories mit geeigneten Aufbewahrungsrichtlinien und Sicherungsverfahren gespeichert werden.                                                                                                 |   1   |  D/V  |
| 12.1.3 | Stellen Sie sicher, dass Log-Speichersysteme Verschlüsselung im Ruhezustand und während der Übertragung implementieren, um sensible Informationen, die in Logs enthalten sind, zu schützen.                                                                             |   1   |  D/V  |
| 12.1.4 | Stellen Sie sicher, dass sensible Daten in Eingabeaufforderungen und Ausgaben automatisch vor der Protokollierung geschwärzt oder maskiert werden, mit konfigurierbaren Schwärzungsregeln für personenbezogene Daten (PII), Zugangsdaten und proprietäre Informationen. |   1   |  D/V  |
| 12.1.5 | Stellen Sie sicher, dass Richtlinienentscheidungen und Sicherheitsfilteraktionen mit ausreichenden Details protokolliert werden, um die Überprüfung und Fehlerbehebung von Inhaltsmoderationssystemen zu ermöglichen.                                                   |   2   |  D/V  |
| 12.1.6 | Stellen Sie sicher, dass die Integrität der Protokolle z. B. durch kryptografische Signaturen oder schreibgeschützten Speicher geschützt ist.                                                                                                                           |   2   |  D/V  |

---

## C12.2 Missbrauchserkennung und Alarmierung

|   #    | Beschreibung                                                                                                                                                                                                                | Ebene | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.2.1 | Überprüfen Sie, ob das System bekannte Jailbreak-Muster, Versuche zur Prompt-Injektion und adversariale Eingaben mithilfe einer signaturbasierten Erkennung erkennt und meldet.                                             |   1   |  D/V  |
| 12.2.2 | Stellen Sie sicher, dass das System mit bestehenden Security Information and Event Management (SIEM)-Plattformen unter Verwendung standardisierter Protokollformate und -protokolle integriert ist.                         |   1   |  D/V  |
| 12.2.3 | Stellen Sie sicher, dass angereicherte Sicherheitsereignisse KI-spezifische Kontextinformationen enthalten, wie Modellkennungen, Vertrauenswerte und Entscheidungen von Sicherheitsfiltern.                                 |   2   |  D/V  |
| 12.2.4 | Überprüfen Sie, ob die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematische Abtastverhalten erkennt.                                                              |   2   |  D/V  |
| 12.2.5 | Stellen Sie sicher, dass Echtzeit-Benachrichtigungsmechanismen Sicherheitsteams informieren, wenn potenzielle Richtlinienverstöße oder Angriffsversuche erkannt werden.                                                     |   2   |  D/V  |
| 12.2.6 | Verifizieren Sie, dass benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster zu erkennen, einschließlich koordinierter Jailbreak-Versuche, Prompt-Injektionskampagnen und Modellextraktionsangriffe. |   2   |  D/V  |
| 12.2.7 | Überprüfen Sie, ob automatisierte Abläufe zur Vorfallsreaktion kompromittierte Modelle isolieren, bösartige Benutzer blockieren und kritische Sicherheitsereignisse eskalieren können.                                      |   3   |  D/V  |

---

## C12.3 Modell-Drift-Erkennung

|   #    | Beschreibung                                                                                                                                                                                                | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.3.1 | Überprüfen Sie, ob das System grundlegende Leistungskennzahlen wie Genauigkeit, Vertrauenswerte, Latenz und Fehlerraten über Modellversionen und Zeiträume hinweg verfolgt.                                 |   1   |  D/V  |
| 12.3.2 | Überprüfen Sie, ob die automatisierte Alarmierung ausgelöst wird, wenn Leistungskennzahlen vordefinierte Verschlechterungsschwellen überschreiten oder signifikant von den Baselines abweichen.             |   2   |  D/V  |
| 12.3.3 | Stellen Sie sicher, dass die Überwachungen zur Halluzinationserkennung Instanzen identifizieren und markieren, wenn Modell-Ausgaben faktisch falsche, inkonsistente oder erfundene Informationen enthalten. |   2   |  D/V  |

---

## C12.4 Leistungs- und Verhaltens-Telemetrie

|   #    | Beschreibung                                                                                                                                                                                                    | Ebene | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.4.1 | Stellen Sie sicher, dass operative Metriken wie Anfragelatenz, Tokenverbrauch, Speichernutzung und Durchsatz kontinuierlich erfasst und überwacht werden.                                                       |   1   |  D/V  |
| 12.4.2 | Stellen Sie sicher, dass Erfolgs- und Fehlerquoten mit Kategorisierung der Fehlertypen und deren Ursachen nachverfolgt werden.                                                                                  |   1   |  D/V  |
| 12.4.3 | Stellen Sie sicher, dass die Überwachung der Ressourcenauslastung die Nutzung von GPU/CPU, den Speicherverbrauch und die Speicheranforderungen umfasst, mit Alarmierung bei Überschreitung von Schwellenwerten. |   2   |  D/V  |

---

## C12.5 Planung und Durchführung der Reaktion auf KI-Vorfälle

|   #    | Beschreibung                                                                                                                                                                                                    | Ebene | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Stellen Sie sicher, dass Vorfallreaktionspläne speziell AI-bezogene Sicherheitsereignisse wie Modellkompromittierung, Datenvergiftung und adversariale Angriffe berücksichtigen.                                |   1   |  D/V  |
| 12.5.2 | Stellen Sie sicher, dass Incident-Response-Teams Zugriff auf KI-spezifische forensische Werkzeuge und Fachkenntnisse haben, um das Modellverhalten und Angriffsvektoren zu untersuchen.                         |   2   |  D/V  |
| 12.5.3 | Stellen Sie sicher, dass die Analyse nach Vorfällen Überlegungen zur Modellerneuerung, Aktualisierungen der Sicherheitsfilter und die Integration gewonnener Erkenntnisse in die Sicherheitskontrollen umfasst. |   3   |  D/V  |

---

## C12.5 Erkennung von Leistungsabfällen bei KI

Überwachen und Erkennen von Leistungs- und Qualitätsverschlechterungen von KI-Modellen im Laufe der Zeit.

|   #    | Beschreibung                                                                                                                                                   | Ebene | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Überprüfen Sie, dass die Modellgenauigkeit, Präzision, Sensitivität und F1-Werte kontinuierlich überwacht und mit den Basisschwellenwerten verglichen werden.  |   1   |  D/V  |
| 12.5.2 | Überprüfen Sie, ob die Erkennung von Datenverschiebungen Änderungen in der Eingabeverteilung überwacht, die die Modellleistung beeinträchtigen könnten.        |   1   |  D/V  |
| 12.5.3 | Überprüfen Sie, ob die Konzeptdrifterkennung Veränderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.                           |   2   |  D/V  |
| 12.5.4 | Überprüfen Sie, ob Leistungsabfälle automatisierte Warnmeldungen auslösen und Workflows für das Nachtrainieren oder den Austausch des Modells starten.         |   2   |  D/V  |
| 12.5.5 | Überprüfen Sie, ob die Ursachenanalyse für Leistungsverluste Leistungseinbrüche mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert. |   3   |   V   |

---

## C12.6 DAG-Visualisierung & Workflow-Sicherheit

Schützen Sie Workflow-Visualisierungssysteme vor Informationslecks und Manipulationsangriffen.

|   #    | Beschreibung                                                                                                                                                                                                                | Ebene | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.6.1 | Überprüfen Sie, ob die Visualisierungsdaten des DAG bereinigt werden, um sensible Informationen vor der Speicherung oder Übertragung zu entfernen.                                                                          |   1   |  D/V  |
| 12.6.2 | Stellen Sie sicher, dass die Zugriffskontrollen der Workflow-Visualisierung gewährleisten, dass nur autorisierte Benutzer Entscheidungswege von Agenten und Nachverfolgungen der Entscheidungsbegründungen einsehen können. |   1   |  D/V  |
| 12.6.3 | Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermethoden geschützt ist.                                                                             |   2   |  D/V  |
| 12.6.4 | Überprüfen Sie, ob Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injektionsangriffe durch manipulierte Knoten- oder Kantendaten zu verhindern.                                                 |   2   |  D/V  |
| 12.6.5 | Stellen Sie sicher, dass Echtzeit-DAG-Aktualisierungen rate-begrenzt und validiert werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.                                                          |   3   |  D/V  |

---

## C12.7 Proaktive Überwachung von Sicherheitsverhalten

Erkennung und Prävention von Sicherheitsbedrohungen durch proaktive Verhaltensanalyse von Agenten.

|   #    | Beschreibung                                                                                                                                                | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.7.1 | Stellen Sie sicher, dass proaktive Agentenverhalten vor der Ausführung mit einer Risikobewertungsintegration sicherheitsgeprüft sind.                       |   1   |  D/V  |
| 12.7.2 | Überprüfen Sie, ob autonome Initiativauslöser die Bewertung des Sicherheitskontexts und die Analyse der Bedrohungslandschaft umfassen.                      |   2   |  D/V  |
| 12.7.3 | Stellen Sie sicher, dass proaktive Verhaltensmuster auf mögliche Sicherheitsimplikationen und unbeabsichtigte Folgen analysiert werden.                     |   2   |  D/V  |
| 12.7.4 | Stellen Sie sicher, dass sicherheitskritische proaktive Maßnahmen explizite Genehmigungsketten mit Prüfprotokollen erfordern.                               |   3   |  D/V  |
| 12.7.5 | Überprüfen Sie, ob die Verhaltensanomalieerkennung Abweichungen in den Mustern proaktiver Agenten erkennt, die auf eine Kompromittierung hinweisen könnten. |   3   |  D/V  |

---

## Literaturverzeichnis

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

