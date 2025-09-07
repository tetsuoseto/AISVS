# 9 Autonome Orchestrierung & agentische Handlungssicherheit

## Kontrollziel

Stellen Sie sicher, dass autonome oder Multi-Agenten-KI-Systeme nur Aktionen ausführen können, die ausdrücklich beabsichtigt, authentifiziert, prüfbar und innerhalb begrenzter Kosten- und Risiko-Schwellenwerte liegen. Dies schützt vor Bedrohungen wie Kompromittierung autonomer Systeme, Werkzeugmissbrauch, Agentenschleifenerkennung, Kommunikationsentführung, Identitätsfälschung, Schwarmmanipulation und Absichtsmanipulation.

---

## 9.1 Agent-Aufgabenplanung und Rekursionsbudgets

Drosseln Sie rekursive Pläne und erzwingen Sie menschliche Kontrollpunkte für privilegierte Aktionen.

|   #   | Beschreibung                                                                                                                                                                                                | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.1.1 | Überprüfen Sie, ob maximale Rekursionstiefe, Breite, Echtzeit, Token und monetäre Kosten pro Agenten-Ausführung zentral konfiguriert und versionskontrolliert sind.                                         |   1    |  D/V  |
| 9.1.2 | Stellen Sie sicher, dass privilegierte oder irreversible Aktionen (z. B. Code-Commits, Finanztransfers) vor der Ausführung eine ausdrückliche menschliche Genehmigung über einen prüfbaren Kanal erfordern. |   1    |  D/V  |
| 9.1.3 | Überprüfen Sie, ob Echtzeit-Ressourcenmonitore eine Circuit-Breaker-Unterbrechung auslösen, wenn eine Budgetschwelle überschritten wird, und dadurch eine weitere Aufgabenerweiterung stoppen.              |   2    |   D   |
| 9.1.4 | Überprüfen Sie, dass Circuit-Breaker-Ereignisse mit Agenten-ID, Auslösebedingung und erfasstem Planzustand für die forensische Überprüfung protokolliert werden.                                            |   2    |  D/V  |
| 9.1.5 | Überprüfen Sie, dass Sicherheitstests Szenarien mit Budgeterschöpfung und ausufernden Plänen abdecken und ein sicheres Anhalten ohne Datenverlust bestätigen.                                               |   3    |   V   |
| 9.1.6 | Stellen Sie sicher, dass Budgetrichtlinien als Policy-as-Code ausgedrückt und in CI/CD durchgesetzt werden, um Konfigurationsabweichungen zu verhindern.                                                    |   3    |   D   |

---

## 9.2 Tool-Plugin-Sandboxing

Isoliere Werkzeuginteraktionen, um unbefugten Systemzugriff oder Codeausführung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                       | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 9.2.1 | Stellen Sie sicher, dass jedes Werkzeug/Plugin in einem Betriebssystem-, Container- oder WASM-Level-Sandbox mit minimalen Berechtigungen für Dateisystem-, Netzwerk- und Systemaufruf-Richtlinien ausgeführt wird. |   1    |  D/V  |
| 9.2.2 | Überprüfen Sie, ob Sandbox-Ressourcenkontingente (CPU, Arbeitsspeicher, Festplatte, Netzwerkausgang) und Ausführungs-Timeouts durchgesetzt und protokolliert werden.                                               |   1    |  D/V  |
| 9.2.3 | Überprüfen Sie, ob Tool-Binärdateien oder Descriptoren digital signiert sind; Signaturen werden vor dem Laden validiert.                                                                                           |   2    |  D/V  |
| 9.2.4 | Verifizieren Sie, dass die Sandbox-Telemetrie in ein SIEM gestreamt wird; Anomalien (z. B. versuchte ausgehende Verbindungen) lösen Alarme aus.                                                                    |   2    |   V   |
| 9.2.5 | Stellen Sie sicher, dass risikoreiche Plugins vor der Produktivsetzung einer Sicherheitsüberprüfung und einem Penetrationstest unterzogen werden.                                                                  |   3    |   V   |
| 9.2.6 | Überprüfen Sie, ob Versuche, die Sandbox zu umgehen, automatisch blockiert werden und das betreffende Plugin bis zur Untersuchung in Quarantäne gestellt wird.                                                     |   3    |  D/V  |

---

## 9.3 Autonome Schleife & Kostenbegrenzung

Erkennen und Stoppen von unkontrollierter Agent-zu-Agent-Rekursion und Kostenexplosionen.

|   #   | Beschreibung                                                                                                                                              | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.3.1 | Überprüfen Sie, dass Inter-Agent-Aufrufe eine Hop-Grenze oder TTL enthalten, die zur Laufzeit dekrementiert und durchgesetzt wird.                        |   1    |  D/V  |
| 9.3.2 | Stellen Sie sicher, dass Agenten eine eindeutige Invocation-Graph-ID beibehalten, um Selbstaufrufe oder zyklische Muster zu erkennen.                     |   2    |   D   |
| 9.3.3 | Überprüfen Sie, dass kumulative Compute-Unit- und Ausgabenzähler pro Anforderungskette verfolgt werden; das Überschreiten des Limits bricht die Kette ab. |   2    |  D/V  |
| 9.3.4 | Überprüfen Sie, dass die formale Analyse oder Modellprüfung die Abwesenheit von unbeschränkter Rekursion in Agentenprotokollen nachweist.                 |   3    |   V   |
| 9.3.5 | Überprüfen Sie, ob Loop-Abbruch-Ereignisse Warnmeldungen erzeugen und kontinuierliche Verbesserungsmetriken speisen.                                      |   3    |   D   |

---

## 9.4 Protokollebene-Missbrauchsschutz

Sichere Kommunikationskanäle zwischen Agenten und externen Systemen, um Entführungen oder Manipulationen zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                   | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.4.1 | Stellen Sie sicher, dass alle Nachrichten zwischen Agent und Werkzeug sowie zwischen Agenten authentifiziert sind (z. B. durch gegenseitiges TLS oder JWT) und durchgängig verschlüsselt sind. |   1    |  D/V  |
| 9.4.2 | Stellen Sie sicher, dass Schemata strikt validiert werden; unbekannte Felder oder fehlerhaft formatierte Nachrichten werden abgelehnt.                                                         |   1    |   D   |
| 9.4.3 | Stellen Sie sicher, dass Integritätsprüfungen (MACs oder digitale Signaturen) die gesamte Nachrichtenlast einschließlich der Werkzeugparameter abdecken.                                       |   2    |  D/V  |
| 9.4.4 | Überprüfen Sie, ob der Replay-Schutz (Nonces oder Zeitstempelfenster) auf Protokollebene durchgesetzt wird.                                                                                    |   2    |   D   |
| 9.4.5 | Stellen Sie sicher, dass Protokollimplementierungen durch Fuzzing und statische Analyse auf Injektions- oder Deserialisierungsfehler überprüft werden.                                         |   3    |   V   |

---

## 9.5 Agent-Identität & Manipulationssicherheit

Stellen Sie sicher, dass Handlungen zuordenbar und Änderungen erkennbar sind.

|   #   | Beschreibung                                                                                                                                            | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.5.1 | Überprüfen Sie, dass jede Agenteninstanz eine eindeutige kryptografische Identität (Schlüsselpaar oder hardwaregebundene Anmeldeinformationen) besitzt. |   1    |  D/V  |
| 9.5.2 | Überprüfen Sie, dass alle Agentenaktionen signiert und mit einem Zeitstempel versehen sind; Protokolle enthalten die Signatur zur Nichtabstreitbarkeit. |   2    |  D/V  |
| 9.5.3 | Überprüfen Sie, ob manipulationssichere Protokolle in einem nur-anhängbaren oder einmal beschreibbaren Medium gespeichert werden.                       |   2    |   V   |
| 9.5.4 | Überprüfen Sie, ob Identitätsschlüssel nach einem definierten Zeitplan und bei Anzeichen eines Kompromisses wechseln.                                   |   3    |   D   |
| 9.5.5 | Verifizieren Sie, dass Spoofing- oder Schlüsselkonfliktversuche eine sofortige Quarantäne des betroffenen Agenten auslösen.                             |   3    |  D/V  |

---

## 9.6 Multi-Agent-Schwarm-Risiko-Reduzierung

Mildern Sie Gefahren des kollektiven Verhaltens durch Isolierung und formale Sicherheitsmodellierung.

|   #   | Beschreibung                                                                                                                                                   | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.6.1 | Stellen Sie sicher, dass Agenten, die in verschiedenen Sicherheitsdomänen arbeiten, in isolierten Laufzeit-Sandboxen oder Netzwerksegmenten ausgeführt werden. |   1    |  D/V  |
| 9.6.2 | Stellen Sie sicher, dass Schwarmverhalten modelliert und formal auf Lebendigkeit und Sicherheit verifiziert werden, bevor sie eingesetzt werden.               |   3    |   V   |
| 9.6.3 | Verifizieren Sie, dass Laufzeit-Monitore emergente unsichere Muster (z. B. Oszillationen, Deadlocks) erkennen und korrigierende Maßnahmen einleiten.           |   3    |   D   |

---

## 9.7 Benutzer- und Werkzeugauthentifizierung / -autorisierung

Implementieren Sie robuste Zugriffskontrollen für jede agentengesteuerte Aktion.

|   #   | Beschreibung                                                                                                                                                                      | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.7.1 | Stellen Sie sicher, dass Agenten sich als erstklassige Prinzipale gegenüber nachgelagerten Systemen authentifizieren und Endbenutzeranmeldeinformationen niemals wiederverwenden. |   1    |  D/V  |
| 9.7.2 | Überprüfen Sie, dass fein granulare Autorisierungsrichtlinien einschränken, welche Werkzeuge ein Agent aufrufen darf und welche Parameter er dabei übergeben darf.                |   2    |   D   |
| 9.7.3 | Stellen Sie sicher, dass Berechtigungsprüfungen bei jedem Aufruf erneut durchgeführt werden (kontinuierliche Autorisierung) und nicht nur zu Beginn der Sitzung.                  |   2    |   V   |
| 9.7.4 | Überprüfen Sie, ob delegierte Berechtigungen automatisch ablaufen und nach Zeitüberschreitung oder Umfangsänderung eine erneute Zustimmung erfordern.                             |   3    |   D   |

---

## 9.8 Sicherheit der Agent-zu-Agent-Kommunikation

Verschlüsseln und mit Integritätsschutz versehen Sie alle Nachrichten zwischen Agenten, um Abhören und Manipulationen zu verhindern.

|   #   | Beschreibung                                                                                                                                                           | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.8.1 | Stellen Sie sicher, dass gegenseitige Authentifizierung und perfect-forward-secret-Verschlüsselung (z. B. TLS 1.3) für Agentenkanäle obligatorisch sind.               |   1    |  D/V  |
| 9.8.2 | Stellen Sie sicher, dass die Nachrichtenintegrität und der Ursprung vor der Verarbeitung validiert werden; Fehler führen zu Warnungen und zum Verwerfen der Nachricht. |   1    |   D   |
| 9.8.3 | Stellen Sie sicher, dass Kommunikationsmetadaten (Zeitstempel, Sequenznummern) protokolliert werden, um eine forensische Rekonstruktion zu unterstützen.               |   2    |  D/V  |
| 9.8.4 | Überprüfen Sie, ob die formale Verifikation oder Modellprüfung bestätigt, dass Protokoll-Zustandsmaschinen nicht in unsichere Zustände gebracht werden können.         |   3    |   V   |

---

## 9.9 Absichtüberprüfung & Durchsetzung von Beschränkungen

Überprüfen Sie, ob die Aktionen des Agenten mit der angegebenen Absicht des Benutzers und den Systembeschränkungen übereinstimmen.

|   #   | Beschreibung                                                                                                                                                                              | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.9.1 | Überprüfen Sie, dass Pre-Execution-Constraint-Solver vorgeschlagene Aktionen anhand von fest codierten Sicherheits- und Richtlinienregeln prüfen.                                         |   1    |   D   |
| 9.9.2 | Stellen Sie sicher, dass Aktionen mit hoher Auswirkung (finanziell, destruktiv, datenschutzsensitiv) eine ausdrückliche Bestätigung der Absicht vom ausführenden Benutzer erfordern.      |   2    |  D/V  |
| 9.9.3 | Überprüfen Sie, dass Nachbedingungsprüfungen validieren, dass abgeschlossene Aktionen die beabsichtigten Effekte ohne Nebeneffekte erreicht haben; Abweichungen lösen einen Rollback aus. |   2    |   V   |
| 9.9.4 | Verifizieren Sie, dass formale Methoden (z. B. Model Checking, Theorembeweise) oder eigenschaftsbasierte Tests nachweisen, dass Agentenpläne alle deklarierten Einschränkungen erfüllen.  |   3    |   V   |
| 9.9.5 | Stellen Sie sicher, dass Absichtsdiskrepanzen oder Verletzungen von Einschränkungen kontinuierliche Verbesserungszyklen und den Austausch von Bedrohungsinformationen fördern.            |   3    |   D   |

---

## 9.10 Sicherheitsstrategie für Agentenlogik

Sichere Auswahl und Ausführung verschiedener Schlussfolgerungsstrategien, einschließlich ReAct-, Chain-of-Thought- und Tree-of-Thoughts-Ansätzen.

|   #    | Beschreibung                                                                                                                                                                                                                                                             | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 9.10.1 | Überprüfen Sie, ob die Auswahl der Vorgehensweise zur Argumentation deterministische Kriterien verwendet (Eingabekomplexität, Aufgabentyp, Sicherheitskontext) und ob identische Eingaben innerhalb desselben Sicherheitskontexts zu identischen Strategiewahlen führen. |   1    |  D/V  |
| 9.10.2 | Stellen Sie sicher, dass jede Denkstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) über eine spezifische Eingabevalidierung, Ausgabereinigung und Ausführungszeitbegrenzung verfügt, die auf ihren jeweiligen kognitiven Ansatz abgestimmt ist.                     |   1    |  D/V  |
| 9.10.3 | Verifizieren Sie, dass Übergänge der Denkstrategie mit vollständigem Kontext protokolliert werden, einschließlich Eingabeeigenschaften, Auswahlkriterienwerten und Ausführungsmetadaten, um die Rekonstruktion der Prüfpfadnachverfolgung zu gewährleisten.              |   2    |  D/V  |
| 9.10.4 | Stellen Sie sicher, dass die Tree-of-Thoughts-Argumentation Mechanismen zum Beschneiden von Ästen enthält, die die Erkundung beenden, wenn Richtlinienverstöße, Ressourcengrenzen oder Sicherheitsgrenzen erkannt werden.                                                |   2    |  D/V  |
| 9.10.5 | Stellen Sie sicher, dass ReAct (Reason-Act-Observe)-Zyklen Validierungspunkte in jeder Phase enthalten: Überprüfung des Denkschritts, Autorisierung der Handlung und Bereinigung der Beobachtung, bevor fortgefahren wird.                                               |   2    |  D/V  |
| 9.10.6 | Stellen Sie sicher, dass die Leistungskennzahlen der Reasoning-Strategie (Ausführungszeit, Ressourcennutzung, Ausgabequalität) mit automatisierten Warnungen überwacht werden, wenn die Kennzahlen über die konfigurierten Schwellenwerte hinaus abweichen.              |   3    |  D/V  |
| 9.10.7 | Stellen Sie sicher, dass hybride Reasoning-Ansätze, die mehrere Strategien kombinieren, die Eingabevalidierung und Ausgabegrenzen aller beteiligten Strategien einhalten, ohne dabei Sicherheitskontrollen zu umgehen.                                                   |   3    |  D/V  |
| 9.10.8 | Überprüfen Sie, dass die Sicherheitstests der Denkstrategie Fuzzing mit fehlerhaften Eingaben, gegnerische Eingabeaufforderungen, die darauf abzielen, einen Strategiewechsel zu erzwingen, und Grenzwerttests für jeden kognitiven Ansatz umfassen.                     |   3    |  D/V  |

---

## 9.11 Agentlebenszyklus-Zustandsverwaltung & Sicherheit

Sichere Agenteninitalisierung, Zustandsübergänge und Beendigung mit kryptografischen Prüfpfaden und definierten Wiederherstellungsverfahren.

|   #    | Beschreibung                                                                                                                                                                                                                                                                                                                   | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 9.11.1 | Stellen Sie sicher, dass die Agenteninitalisierung die Einrichtung einer kryptografischen Identität mit hardware-gesicherten Anmeldeinformationen und unveränderlichen Start-Protokollen umfasst, die Agenten-ID, Zeitstempel, Konfigurations-Hash und Initialisierungsparameter enthalten.                                    |   1    |  D/V  |
| 9.11.2 | Verifizieren Sie, dass Agentenzustandsübergänge kryptographisch signiert, mit Zeitstempel versehen und mit vollständigem Kontext protokolliert werden, einschließlich der auslösenden Ereignisse, des Hashs des vorherigen Zustands, des Hashs des neuen Zustands und der durchgeführten Sicherheitsüberprüfungen.             |   2    |  D/V  |
| 9.11.3 | Verifizieren Sie, dass die Agent-Abschaltverfahren eine sichere Speicherlöschung mittels kryptografischer Löschung oder mehrmaligem Überschreiben, die Widerrufung von Berechtigungsnachweisen mit Benachrichtigung der Zertifizierungsstelle sowie die Erstellung von manipulationssicheren Beendigungszertifikaten umfassen. |   2    |  D/V  |
| 9.11.4 | Stellen Sie sicher, dass Agenten-Wiederherstellungsmechanismen die Zustandsintegrität mithilfe kryptografischer Prüfsummen (mindestens SHA-256) validieren und bei erkannter Korruption auf bekannte gute Zustände zurücksetzen, wobei automatisierte Warnungen und manuelle Genehmigungsanforderungen verwendet werden.       |   3    |  D/V  |
| 9.11.5 | Überprüfen Sie, ob Agent-Persistenzmechanismen sensible Zustandsdaten mit individuellen AES-256-Schlüsseln pro Agent verschlüsseln und eine sichere Schlüsselrotation entsprechend konfigurierbaren Zeitplänen (maximal 90 Tage) mit unterbrechungsfreier Bereitstellung implementieren.                                       |   3    |  D/V  |

---

## 9.12 Sicherheitsrahmen für die Integration von Werkzeugen

Sicherheitskontrollen für das dynamische Laden von Werkzeugen, deren Ausführung und Ergebnisvalidierung mit definierten Risiko-Bewertungs- und Genehmigungsprozessen.

|   #    | Beschreibung                                                                                                                                                                                                                                                                                                         | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 9.12.1 | Stellen Sie sicher, dass Tool-Beschreibungen Sicherheitsmetadaten enthalten, die die erforderlichen Berechtigungen (Lesen/Schreiben/Ausführen), Risikostufen (niedrig/mittel/hoch), Ressourcenlimits (CPU, Speicher, Netzwerk) und Validierungsanforderungen, die in den Tool-Manifests dokumentiert sind, angeben.  |   1    |  D/V  |
| 9.12.2 | Stellen Sie sicher, dass die Ergebnisse der Werkzeugausführung gegen erwartete Schemata (JSON-Schema, XML-Schema) und Sicherheitsrichtlinien (Ausgabe-Sanitierung, Datenklassifizierung) validiert werden, bevor sie mit Zeitlimitvorgaben und Fehlerbehandlungsverfahren integriert werden.                         |   1    |  D/V  |
| 9.12.3 | Überprüfen Sie, dass Tool-Interaktionsprotokolle einen detaillierten Sicherheitskontext enthalten, einschließlich der Verwendung von Berechtigungen, Datenzugriffsmustern, Ausführungszeit, Ressourcenverbrauch und Rückgabecodes mit strukturiertem Logging für die SIEM-Integration.                               |   2    |  D/V  |
| 9.12.4 | Überprüfen Sie, ob dynamische Mechanismen zum Laden von Werkzeugen digitale Signaturen unter Verwendung der PKI-Infrastruktur validieren und sichere Ladeprotokolle mit Sandbox-Isolierung sowie Berechtigungsüberprüfung vor der Ausführung implementieren.                                                         |   2    |  D/V  |
| 9.12.5 | Stellen Sie sicher, dass Sicherheitsbewertungen von Tools automatisch für neue Versionen ausgelöst werden, mit verpflichtenden Genehmigungsschritten einschließlich statischer Analyse, dynamischer Tests und Überprüfung durch das Sicherheitsteam, mit dokumentierten Genehmigungskriterien und SLA-Anforderungen. |   3    |  D/V  |

---

### Referenzen

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

