# C12 Überwachung, Protokollierung und Anomalieerkennung

## Kontrollziel

Dieser Abschnitt enthält Anforderungen für die Bereitstellung von Echtzeit- und forensischer Sichtbarkeit darüber, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, eingestuft und analysiert werden können.

## C12.1 Anforderungs- und Antwortprotokollierung

|   #    | Beschreibung                                                                                                                                                                                                                                                            | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.1.1 | Stellen Sie sicher, dass alle Benutzereingaben und Modellantworten mit den entsprechenden Metadaten protokolliert werden (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion).                                                                                  |   1    |  D/V  |
| 12.1.2 | Stellen Sie sicher, dass Protokolle in sicheren, zugangskontrollierten Repositorien mit geeigneten Aufbewahrungsrichtlinien und Backup-Verfahren gespeichert werden.                                                                                                    |   1    |  D/V  |
| 12.1.3 | Überprüfen Sie, ob Log-Speichersysteme eine Verschlüsselung im Ruhezustand und während der Übertragung implementieren, um vertrauliche Informationen in den Logs zu schützen.                                                                                           |   1    |  D/V  |
| 12.1.4 | Stellen Sie sicher, dass sensible Daten in Eingabeaufforderungen und Ausgaben automatisch vor der Protokollierung geschwärzt oder maskiert werden, mit konfigurierbaren Schwärzungsregeln für personenbezogene Daten (PII), Zugangsdaten und proprietäre Informationen. |   1    |  D/V  |
| 12.1.5 | Stellen Sie sicher, dass Richtlinienentscheidungen und Sicherheitsfiltermaßnahmen mit ausreichenden Details protokolliert werden, um die Überprüfung und Fehlerbehebung von Content-Moderationssystemen zu ermöglichen.                                                 |   2    |  D/V  |
| 12.1.6 | Stellen Sie sicher, dass die Integrität der Protokolle z. B. durch kryptografische Signaturen oder schreibgeschützten Speicher geschützt ist.                                                                                                                           |   2    |  D/V  |

---

## C12.2 Missbrauchserkennung und Alarmierung

|   #    | Beschreibung                                                                                                                                                                                                                 | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.2.1 | Überprüfen Sie, ob das System bekannte Jailbreak-Muster, Versuche der Prompt-Injektion und adversariale Eingaben mithilfe einer signaturbasierten Erkennung erkennt und meldet.                                              |   1    |  D/V  |
| 12.2.2 | Überprüfen Sie, ob das System mit vorhandenen Security Information and Event Management (SIEM)-Plattformen unter Verwendung standardisierter Protokollformate und -protokolle integriert ist.                                |   1    |  D/V  |
| 12.2.3 | Überprüfen Sie, dass angereicherte Sicherheitsereignisse KI-spezifischen Kontext wie Modell-Identifikatoren, Vertrauenswerte und Entscheidungen von Sicherheitsfiltern enthalten.                                            |   2    |  D/V  |
| 12.2.4 | Überprüfen Sie, ob die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematische Abfrageverhalten identifiziert.                                                        |   2    |  D/V  |
| 12.2.5 | Überprüfen Sie, ob Echtzeit-Benachrichtigungsmechanismen die Sicherheitsteams informieren, wenn potenzielle Richtlinienverstöße oder Angriffsversuche erkannt werden.                                                        |   2    |  D/V  |
| 12.2.6 | Verifizieren Sie, dass benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster zu erkennen, einschließlich koordinierter Jailbreak-Versuche, Prompt-Injektionskampagnen und Modell-Extraktionsangriffe. |   2    |  D/V  |
| 12.2.7 | Überprüfen Sie, dass automatisierte Incident-Response-Workflows kompromittierte Modelle isolieren, bösartige Benutzer blockieren und kritische Sicherheitsereignisse eskalieren können.                                      |   3    |  D/V  |

---

## C12.3 Modellverschiebungserkennung

|   #    | Beschreibung                                                                                                                                                                                  | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.3.1 | Überprüfen Sie, ob das System grundlegende Leistungskennzahlen wie Genauigkeit, Vertrauenswerte, Latenzzeiten und Fehlerquoten über Modellversionen und Zeiträume hinweg verfolgt.            |   1    |  D/V  |
| 12.3.2 | Überprüfen Sie, ob die automatisierte Alarmierung ausgelöst wird, wenn Leistungskennzahlen vordefinierte Verschlechterungsschwellen überschreiten oder erheblich von den Baselines abweichen. |   2    |  D/V  |
| 12.3.3 | Überprüfen Sie, ob die Halluzinationsdetektionsmonitore Instanzen erkennen und kennzeichnen, wenn Modell-Ausgaben faktisch inkorrekte, inkonsistente oder erfundene Informationen enthalten.  |   2    |  D/V  |

---

## C12.4 Leistungs- und Verhaltens-Telemetrie

|   #    | Beschreibung                                                                                                                                                                                                          | Niveau | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.4.1 | Stellen Sie sicher, dass Betriebsmetriken wie Anforderungsverzögerung, Token-Verbrauch, Speicherverbrauch und Durchsatz kontinuierlich erfasst und überwacht werden.                                                  |   1    |  D/V  |
| 12.4.2 | Verifizieren Sie, dass Erfolgs- und Fehlerraten mit Kategorisierung der Fehlertypen und deren Ursachen nachverfolgt werden.                                                                                           |   1    |  D/V  |
| 12.4.3 | Überprüfen Sie, ob die Überwachung der Ressourcennutzung die GPU-/CPU-Auslastung, den Speicherverbrauch und die Speicheranforderungen umfasst und ob bei Überschreitung von Schwellenwerten eine Alarmierung erfolgt. |   2    |  D/V  |

---

## C12.5 Planung und Durchführung der Reaktion auf KI-Vorfälle

|   #    | Beschreibung                                                                                                                                                                                                                 | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.5.1 | Stellen Sie sicher, dass die Vorfallreaktionspläne speziell auf KI-bezogene Sicherheitsereignisse eingehen, einschließlich Modellkompromittierung, Datenvergiftung und adversarialen Angriffen.                              |   1    |  D/V  |
| 12.5.2 | Stellen Sie sicher, dass Vorfallreaktionsteams Zugang zu KI-spezifischen forensischen Werkzeugen und Fachwissen haben, um das Modellverhalten und Angriffsvektoren zu untersuchen.                                           |   2    |  D/V  |
| 12.5.3 | Überprüfen Sie, dass die Analyse nach dem Vorfall Überlegungen zur Nachtrainierung des Modells, Aktualisierungen der Sicherheitsfilter und die Integration der gewonnenen Erkenntnisse in die Sicherheitskontrollen umfasst. |   3    |  D/V  |

---

## C12.5 Erkennung der Leistungsverschlechterung von KI

Überwachen und Erkennen von Verschlechterungen der Leistung und Qualität eines KI-Modells im Laufe der Zeit.

|   #    | Beschreibung                                                                                                                                                               | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.5.1 | Überprüfen Sie, dass die Modellgenauigkeit, Präzision, Recall und F1-Werte kontinuierlich überwacht und mit den Basisschwellenwerten verglichen werden.                    |   1    |  D/V  |
| 12.5.2 | Stellen Sie sicher, dass die Erkennung von Datenverschiebungen Änderungen der Eingabeverteilung überwacht, die die Modellleistung beeinträchtigen könnten.                 |   1    |  D/V  |
| 12.5.3 | Überprüfen Sie, ob die Konzeptverschiebungserkennung Änderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.                                  |   2    |  D/V  |
| 12.5.4 | Überprüfen Sie, dass Leistungsabfälle automatisierte Warnungen auslösen und Workflows für die Modellneuschulung oder -ersetzung starten.                                   |   2    |  D/V  |
| 12.5.5 | Verifizieren Sie, dass die Ursachenanalyse für Leistungsabfälle Leistungsverschlechterungen mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert. |   3    |   V   |

---

## C12.6 DAG-Visualisierung & Workflow-Sicherheit

Schützen Sie System zur Visualisierung von Arbeitsabläufen vor Informationslecks und Manipulationsangriffen.

|   #    | Beschreibung                                                                                                                                                                                                                     | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.6.1 | Stellen Sie sicher, dass die Visualisierungsdaten des DAG bereinigt werden, um sensible Informationen vor der Speicherung oder Übertragung zu entfernen.                                                                         |   1    |  D/V  |
| 12.6.2 | Überprüfen Sie, ob die Zugriffskontrollen für die Workflow-Visualisierung sicherstellen, dass nur autorisierte Benutzer die Entscheidungswege der Agenten und die Nachvollziehbarkeit der Entscheidungsprozesse einsehen können. |   1    |  D/V  |
| 12.6.3 | Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermethoden geschützt ist.                                                                                  |   2    |  D/V  |
| 12.6.4 | Überprüfen Sie, ob Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injektionsangriffe durch manipulierte Knoten- oder Kantendaten zu verhindern.                                                      |   2    |  D/V  |
| 12.6.5 | Stellen Sie sicher, dass Echtzeit-DAG-Aktualisierungen mengenbegrenzten und validierten werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.                                                          |   3    |  D/V  |

---

## C12.7 Proaktive Überwachung des Sicherheitsverhaltens

Erkennung und Verhinderung von Sicherheitsbedrohungen durch proaktive Analyse des Agentenverhaltens.

|   #    | Beschreibung                                                                                                                                                      | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.7.1 | Stellen Sie sicher, dass proaktive Agentenverhalten vor der Ausführung mit Integration der Risikobewertung sicherheitsvalidiert werden.                           |   1    |  D/V  |
| 12.7.2 | Überprüfen Sie, ob selbstständige Initiativen die Bewertung des Sicherheitskontexts und die Analyse der Bedrohungslandschaft umfassen.                            |   2    |  D/V  |
| 12.7.3 | Stellen Sie sicher, dass proaktive Verhaltensmuster auf potenzielle Sicherheitsimplikationen und unbeabsichtigte Folgen analysiert werden.                        |   2    |  D/V  |
| 12.7.4 | Stellen Sie sicher, dass sicherheitskritische proaktive Maßnahmen explizite Genehmigungsketten mit Prüfpfaden erfordern.                                          |   3    |  D/V  |
| 12.7.5 | Überprüfen Sie, ob die Verhaltensanomalieerkennung Abweichungen in den Mustern proaktiver Agenten identifiziert, die auf eine Kompromittierung hinweisen könnten. |   3    |  D/V  |

---

## Referenzen

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

