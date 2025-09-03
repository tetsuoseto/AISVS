# C12 Überwachung, Protokollierung & Anomalieerkennung

## Kontrollziel

Dieser Abschnitt legt Anforderungen fest, um Echtzeit- und forensische Nachvollziehbarkeit dessen bereitzustellen, was das Modell und andere KI-Komponenten sehen, tun und zurückgeben, damit Bedrohungen erkannt, priorisiert und daraus gelernt werden können.

## C12.1 Protokollierung von Anfragen und Antworten

|   #    | Beschreibung                                                                                                                                                                                                            | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.1.1 | Stellen Sie sicher, dass alle Benutzereingaben und Modellantworten mit geeigneten Metadaten protokolliert werden (z. B. Zeitstempel, Benutzer-ID, Sitzungs-ID, Modellversion).                                          |   1   |  D/V  |
| 12.1.2 | Überprüfen Sie, dass Protokolle in sicheren, zugriffskontrollierten Repositories mit geeigneten Aufbewahrungsrichtlinien und Backup-Verfahren gespeichert werden.                                                       |   1   |  D/V  |
| 12.1.3 | Überprüfen Sie, ob Log-Speichersysteme eine Verschlüsselung im Ruhezustand und während der Übertragung implementieren, um sensible Informationen in Logdateien zu schützen.                                             |   1   |  D/V  |
| 12.1.4 | Stellen Sie sicher, dass sensible Daten in Prompts und Ausgaben vor dem Logging automatisch geschwärzt oder maskiert werden, mit konfigurierbaren Redaktionsregeln für PII, Zugangsdaten und proprietäre Informationen. |   1   |  D/V  |
| 12.1.5 | Stellen Sie sicher, dass Richtlinienentscheidungen und Sicherheitsfiltermaßnahmen mit ausreichenden Details protokolliert werden, um Audits und das Debuggen von Content-Moderationssystemen zu ermöglichen.            |   2   |  D/V  |
| 12.1.6 | Stellen Sie sicher, dass die Integrität der Logdateien durch z. B. kryptografische Signaturen oder Schreib-Only-Speicher geschützt ist.                                                                                 |   2   |  D/V  |

---

## C12.2 Missbrauchserkennung und Alarmierung

|   #    | Beschreibung                                                                                                                                                                                                                  | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.2.1 | Vergewissern Sie sich, dass das System bekannte Jailbreak-Muster, Prompt-Injektionsversuche und adversariale Eingaben erkennt und Warnungen ausgibt, die durch signaturbasierte Erkennung erfolgen.                           |   1   |  D/V  |
| 12.2.2 | Stellen Sie sicher, dass das System in vorhandene Sicherheitsinformations- und Ereignismanagement-(SIEM)-Plattformen integriert wird, die Standard-Logformate und Protokolle verwenden.                                       |   1   |  D/V  |
| 12.2.3 | Stellen Sie sicher, dass angereicherte Sicherheitsereignisse KI-spezifischen Kontext enthalten, wie Modellkennungen, Konfidenzwerte und Entscheidungen des Sicherheitsfilters.                                                |   2   |  D/V  |
| 12.2.4 | Überprüfen Sie, ob die Verhaltensanomalieerkennung ungewöhnliche Gesprächsmuster, übermäßige Wiederholungsversuche oder systematisches Erkundungsverhalten erkennt.                                                           |   2   |  D/V  |
| 12.2.5 | Vergewissern Sie sich, dass Echtzeit-Alarmierungssysteme Sicherheitsteams benachrichtigen, wenn potenzielle Richtlinienverstöße oder Angriffsversuche erkannt werden.                                                         |   2   |  D/V  |
| 12.2.6 | Stellen Sie sicher, dass benutzerdefinierte Regeln enthalten sind, um KI-spezifische Bedrohungsmuster zu erkennen, einschließlich koordinierter Jailbreak-Versuche, Prompt-Injection-Kampagnen und Modellextraktionsangriffe. |   2   |  D/V  |
| 12.2.7 | Überprüfen Sie, ob automatisierte Vorfallreaktionsabläufe kompromittierte Modelle isolieren, böswillige Benutzer blockieren und kritische Sicherheitsvorfälle eskalieren können.                                              |   3   |  D/V  |

---

## C12.3 Modell-Drift-Erkennung

|   #    | Beschreibung                                                                                                                                                                                                           | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.3.1 | Stellen Sie sicher, dass das System grundlegende Leistungskennzahlen wie Genauigkeit, Konfidenzwerte, Latenz und Fehlerraten über Modellversionen und Zeiträume hinweg verfolgt.                                       |   1   |  D/V  |
| 12.3.2 | Überprüfen Sie, ob die automatisierte Alarmierung ausgelöst wird, wenn Leistungskennzahlen vordefinierte Schwellenwerte für Leistungsverschlechterung überschreiten oder signifikant von den Referenzwerten abweichen. |   2   |  D/V  |
| 12.3.3 | Überprüfen Sie, ob Halluzinationserkennungsmodule Fälle identifizieren und kennzeichnen, in denen Modellausgaben sachlich inkorrekte, inkonsistente oder fabrizierte Informationen enthalten.                          |   2   |  D/V  |

---

## C12.4 Leistung & Verhalten Telemetrie

|   #    | Beschreibung                                                                                                                                                                                           | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 12.4.1 | Stellen Sie sicher, dass betriebliche Kennzahlen, einschließlich der Anfragelatenz, des Tokenverbrauchs, des Speicherverbrauchs und des Durchsatzes, kontinuierlich erhoben und überwacht werden.      |   1   |  D/V  |
| 12.4.2 | Stellen Sie sicher, dass Erfolgs- und Fehlerraten erfasst werden, zusammen mit der Kategorisierung von Fehlerarten und deren Ursachen.                                                                 |   1   |  D/V  |
| 12.4.3 | Vergewissern Sie sich, dass die Überwachung der Ressourcennutzung GPU/CPU-Auslastung, Speicherverbrauch und Speicherbedarf umfasst und bei Überschreitungen von Schwellenwerten Alarmierungen auslöst. |   2   |  D/V  |

---

## C12.5 KI-Vorfallreaktionsplanung und Ausführung

|   #    | Beschreibung                                                                                                                                                                                                             | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 12.5.1 | Stellen Sie sicher, dass Vorfallreaktionspläne speziell KI-bezogene Sicherheitsereignisse berücksichtigen, einschließlich Modellkompromittierung, Datenvergiftung und adversariale Angriffe.                             |   1   |  D/V  |
| 12.5.2 | Vergewissern Sie sich, dass Sicherheitsvorfall-Teams Zugriff auf KI-spezifische forensische Werkzeuge und Fachwissen haben, um das Modellverhalten und Angriffsvektoren zu untersuchen.                                  |   2   |  D/V  |
| 12.5.3 | Stellen Sie sicher, dass die Nachvorfallanalyse Überlegungen zum erneuten Training des Modells, Aktualisierungen der Sicherheitsfilter und die Integration der gewonnenen Erkenntnisse in Sicherheitskontrollen umfasst. |   3   |  D/V  |

---

## C12.5 KI-Leistungsabfall-Erkennung

Überwachen und Erkennen von Verschlechterungen der Leistung und Qualität eines KI-Modells im Laufe der Zeit.

|   #    | Beschreibung                                                                                                                                                              | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.5.1 | Vergewissern Sie sich, dass die Genauigkeit des Modells, Präzision, Sensitivität und F1-Werte kontinuierlich überwacht und mit Referenzschwellenwerten verglichen werden. |   1   |  D/V  |
| 12.5.2 | Stellen Sie sicher, dass die Datenverschiebungserkennung Änderungen der Eingabeverteilung überwacht, die die Modellleistung beeinträchtigen können.                       |   1   |  D/V  |
| 12.5.3 | Überprüfen Sie, ob die Detektion von Konzeptdrift Veränderungen in der Beziehung zwischen Eingaben und erwarteten Ausgaben identifiziert.                                 |   2   |  D/V  |
| 12.5.4 | Stellen Sie sicher, dass Leistungsabfall automatische Warnmeldungen auslöst und Arbeitsabläufe für das erneute Trainieren des Modells oder dessen Austausch einleitet.    |   2   |  D/V  |
| 12.5.5 | Überprüfen Sie, ob die Ursachenanalyse der Degradation Leistungsabfälle mit Datenänderungen, Infrastrukturproblemen oder externen Faktoren korreliert.                    |   3   |   V   |

---

## C12.6 DAG-Visualisierung und Workflow-Sicherheit

Schützen Sie Workflow-Visualisierungssysteme vor Informationslecks und Manipulationsangriffen.

|   #    | Beschreibung                                                                                                                                                                                               | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.6.1 | Vergewissern Sie sich, dass DAG-Visualisierungsdaten bereinigt werden, um sensible Informationen vor der Speicherung oder Übertragung zu entfernen.                                                        |   1   |  D/V  |
| 12.6.2 | Vergewissern Sie sich, dass die Zugriffssteuerungen für die Workflow-Visualisierung sicherstellen, dass nur autorisierte Benutzer die Entscheidungswege des Agenten und Begründungsspuren einsehen können. |   1   |  D/V  |
| 12.6.3 | Stellen Sie sicher, dass die Integrität der DAG-Daten durch kryptografische Signaturen und manipulationssichere Speichermechanismen geschützt ist.                                                         |   2   |  D/V  |
| 12.6.4 | Stellen Sie sicher, dass Workflow-Visualisierungssysteme eine Eingabevalidierung implementieren, um Injektionsangriffe durch gezielt gestaltete Knoten- oder Kanten-Daten zu verhindern.                   |   2   |  D/V  |
| 12.6.5 | Verifizieren Sie, dass Echtzeit-DAG-Updates einer Ratenbegrenzung unterliegen und validiert werden, um Denial-of-Service-Angriffe auf Visualisierungssysteme zu verhindern.                                |   3   |  D/V  |

---

## C12.7 Proaktive Sicherheitsverhaltensüberwachung

Erkennung und Verhinderung von Sicherheitsbedrohungen durch proaktive Verhaltensanalyse von Agenten.

|   #    | Beschreibung                                                                                                                                                      | Level | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 12.7.1 | Stellen Sie sicher, dass proaktive Agentenverhaltensweisen vor der Ausführung sicherheitsvalidiert sind und dass eine Risikobewertung integriert ist.             |   1   |  D/V  |
| 12.7.2 | Überprüfen Sie, ob die Auslöser autonomer Initiativen eine Bewertung des Sicherheitskontexts und eine Bewertung der Bedrohungslage umfassen.                      |   2   |  D/V  |
| 12.7.3 | Stellen Sie sicher, dass proaktive Verhaltensmuster auf potenzielle sicherheitsrelevante Implikationen und unbeabsichtigte Folgen analysiert werden.              |   2   |  D/V  |
| 12.7.4 | Überprüfen Sie, ob sicherheitskritische proaktive Maßnahmen explizite Freigabeketten mit Audit-Trails erfordern.                                                  |   3   |  D/V  |
| 12.7.5 | Überprüfen Sie, ob die Verhaltensanomalieerkennung Abweichungen in den Mustern proaktiver Agenten identifiziert, die auf eine Kompromittierung hindeuten könnten. |   3   |  D/V  |

---

## Referenzen

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

