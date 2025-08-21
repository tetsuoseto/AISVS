# 9 Autonome Orchestrierung & Agentisches Handeln Sicherheit

## Steuerungsziel

Stellen Sie sicher, dass autonome oder Multi-Agenten-KI-Systeme nur Aktionen ausführen können, die ausdrücklich beabsichtigt, authentifiziert, prüfbar und innerhalb begrenzter Kosten- und Risikoschwellen liegen. Dies schützt vor Bedrohungen wie Kompromittierung autonomer Systeme, Missbrauch von Werkzeugen, Erkennung von Agentenschleifen, Übernahme der Kommunikation, Identitätsfälschung, Schwarmmanipulation und Manipulation der Absicht.

---

## 9.1 Agent Aufgabenplanung & Rekursionsbudgets

Drosseln Sie rekursive Pläne und erzwingen Sie menschliche Überprüfungen für privilegierte Aktionen.

|   #   | Beschreibung                                                                                                                                                                                                          | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.1.1 | Stellen Sie sicher, dass maximale Rekursionstiefe, Breite, Echtzeit, Tokens und monetäre Kosten pro Agentenausführung zentral konfiguriert und versionskontrolliert sind.                                             |   1   |  D/V  |
| 9.1.2 | Stellen Sie sicher, dass privilegierte oder irreversible Aktionen (z. B. Code-Commits, finanzielle Überweisungen) vor der Ausführung eine ausdrückliche menschliche Genehmigung über einen prüfbaren Kanal erfordern. |   1   |  D/V  |
| 9.1.3 | Überprüfen Sie, ob Echtzeit-Ressourcenmonitore eine Unterbrechung durch einen Circuit-Breaker auslösen, wenn eine Budgetschwelle überschritten wird, und dadurch eine weitere Aufgabenerweiterung stoppen.            |   2   |   D   |
| 9.1.4 | Überprüfen Sie, dass Circuit-Breaker-Ereignisse mit Agenten-ID, auslösender Bedingung und erfasstem Planstatus für die forensische Überprüfung protokolliert werden.                                                  |   2   |  D/V  |
| 9.1.5 | Stellen Sie sicher, dass Sicherheitstests Budgeterschöpfungs- und Ausreißer-Plan-Szenarien abdecken und einen sicheren Abbruch ohne Datenverlust bestätigen.                                                          |   3   |   V   |
| 9.1.6 | Stellen Sie sicher, dass Budgetrichtlinien als Policy-as-Code ausgedrückt und in CI/CD durchgesetzt werden, um Konfigurationsabweichungen zu verhindern.                                                              |   3   |   D   |

---

## 9.2 Werkzeug-Plugin-Sandboxing

Isolieren Sie Werkzeuginteraktionen, um unbefugten Systemzugriff oder Codeausführung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.2.1 | Stellen Sie sicher, dass jedes Tool/Plugin innerhalb eines Betriebssystems, Containers oder eines WASM-Level-Sandbox mit minimalen Berechtigungen für Dateisystem-, Netzwerk- und Systemaufruf-Richtlinien ausgeführt wird. |   1   |  D/V  |
| 9.2.2 | Überprüfen Sie, ob Sandbox-Ressourcenkontingente (CPU, Speicher, Festplatte, Netzwerk-Ausgang) und Ausführungszeitüberschreitungen durchgesetzt und protokolliert werden.                                                   |   1   |  D/V  |
| 9.2.3 | Überprüfen Sie, ob Tool-Binärdateien oder Deskriptoren digital signiert sind; Signaturen werden vor dem Laden validiert.                                                                                                    |   2   |  D/V  |
| 9.2.4 | Überprüfen Sie, dass Sandboxtelemetrie an ein SIEM übertragen wird; Anomalien (z. B. versuchte ausgehende Verbindungen) lösen Warnmeldungen aus.                                                                            |   2   |   V   |
| 9.2.5 | Stellen Sie sicher, dass Hochrisiko-Plugins vor der Produktionsbereitstellung einer Sicherheitsüberprüfung und Penetrationstests unterzogen werden.                                                                         |   3   |   V   |
| 9.2.6 | Überprüfen Sie, ob Sandbox-Fluchtversuche automatisch blockiert werden und das betreffende Plugin bis zur Untersuchung unter Quarantäne gestellt wird.                                                                      |   3   |  D/V  |

---

## 9.3 Autonome Schleife & Kostenbegrenzung

Erkennen und stoppen Sie unkontrollierte rekursive Agent-zu-Agent-Aufrufe und Kostenexplosionen.

|   #   | Beschreibung                                                                                                                                                   | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.3.1 | Stellen Sie sicher, dass Inter-Agent-Aufrufe eine Hop-Grenze oder TTL enthalten, die zur Laufzeit dekrementiert und durchgesetzt wird.                         |   1   |  D/V  |
| 9.3.2 | Stellen Sie sicher, dass Agenten eine eindeutige Aufrufgraph-ID beibehalten, um Selbstaufrufe oder zyklische Muster zu erkennen.                               |   2   |   D   |
| 9.3.3 | Verifizieren Sie, dass kumulative Recheneinheiten- und Ausgabenzähler pro Anforderungskette verfolgt werden; das Überschreiten des Limits bricht die Kette ab. |   2   |  D/V  |
| 9.3.4 | Stellen Sie sicher, dass die formale Analyse oder Model Checking das Fehlen von unbeschränkter Rekursion in Agentenprotokollen nachweist.                      |   3   |   V   |
| 9.3.5 | Überprüfen Sie, ob Schleifen-Abbruchereignisse Alarme erzeugen und kontinuierliche Verbesserungsmetriken speisen.                                              |   3   |   D   |

---

## 9.4 Protokollebene-Missbrauchsschutz

Sichere Kommunikationskanäle zwischen Agenten und externen Systemen, um Übernahmen oder Manipulationen zu verhindern.

|   #   | Beschreibung                                                                                                                                                                              | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.4.1 | Verifizieren Sie, dass alle Nachrichten von Agent zu Werkzeug und von Agent zu Agent authentifiziert sind (z. B. mittels gegenseitigem TLS oder JWT) und Ende-zu-Ende verschlüsselt sind. |   1   |  D/V  |
| 9.4.2 | Stellen Sie sicher, dass Schemata streng validiert werden; unbekannte Felder oder fehlerhaft formatierte Nachrichten werden abgelehnt.                                                    |   1   |   D   |
| 9.4.3 | Stellen Sie sicher, dass Integritätsprüfungen (MACs oder digitale Signaturen) die gesamte Nachrichten-Nutzlast einschließlich der Werkzeugparameter abdecken.                             |   2   |  D/V  |
| 9.4.4 | Stellen Sie sicher, dass der Replay-Schutz (Nonces oder Zeitstempelfenster) auf der Protokollebene durchgesetzt wird.                                                                     |   2   |   D   |
| 9.4.5 | Überprüfen Sie, dass Protokollimplementierungen Fuzzing und statische Analyse auf Injektions- oder Deserialisierungsfehler durchlaufen.                                                   |   3   |   V   |

---

## 9.5 Agenten-Identität & Manipulationssicherheit

Stellen Sie sicher, dass Aktionen zuordenbar und Änderungen erkennbar sind.

|   #   | Beschreibung                                                                                                                                                 | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.5.1 | Stellen Sie sicher, dass jede Agenteninstanz eine eindeutige kryptografische Identität (Schlüsselpaar oder hardwarebasierte Anmeldeinformationen) besitzt.   |   1   |  D/V  |
| 9.5.2 | Stellen Sie sicher, dass alle Agentenaktionen signiert und mit einem Zeitstempel versehen sind; Protokolle enthalten die Signatur zur Nicht-Abstreitbarkeit. |   2   |  D/V  |
| 9.5.3 | Stellen Sie sicher, dass manipulationssichere Protokolle in einem nur-anfügbaren oder einmal beschreibbaren Medium gespeichert werden.                       |   2   |   V   |
| 9.5.4 | Überprüfen Sie, ob Identitätsschlüssel gemäß einem definierten Zeitplan und bei Kompromittierungsindikatoren rotieren.                                       |   3   |   D   |
| 9.5.5 | Überprüfen Sie, dass Spoofing- oder Schlüsselkonfliktversuche eine sofortige Quarantäne des betroffenen Agenten auslösen.                                    |   3   |  D/V  |

---

## 9.6 Risikominderung bei Multi-Agenten-Schwärmen

Mildern Sie Gefahren durch kollektives Verhalten durch Isolation und formale Sicherheitsmodellierung.

|   #   | Beschreibung                                                                                                                                                        | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.6.1 | Stellen Sie sicher, dass Agenten, die in unterschiedlichen Sicherheitsdomänen operieren, in isolierten Laufzeit-Sandboxes oder Netzwerksegmenten ausgeführt werden. |   1   |  D/V  |
| 9.6.2 | Stellen Sie sicher, dass Schwarmverhalten modelliert und formal auf Lebendigkeit und Sicherheit vor der Bereitstellung verifiziert werden.                          |   3   |   V   |
| 9.6.3 | Überprüfen Sie, ob Laufzeit-Monitore emergente unsichere Muster (z. B. Oszillationen, Deadlocks) erkennen und korrigierende Maßnahmen einleiten.                    |   3   |   D   |

---

## 9.7 Benutzer- und Tool-Authentifizierung / Autorisierung

Implementieren Sie robuste Zugriffskontrollen für jede durch Agenten ausgelöste Aktion.

|   #   | Beschreibung                                                                                                                                                                      | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.7.1 | Stellen Sie sicher, dass Agenten sich als erstklassige Prinzipale gegenüber nachgelagerten Systemen authentifizieren und niemals Endbenutzeranmeldeinformationen wiederverwenden. |   1   |  D/V  |
| 9.7.2 | Verifizieren Sie, dass fein abgestimmte Autorisierungsrichtlinien einschränken, welche Werkzeuge ein Agent aufrufen darf und welche Parameter er dabei übermitteln darf.          |   2   |   D   |
| 9.7.3 | Stellen Sie sicher, dass Berechtigungsprüfungen bei jedem Aufruf erneut bewertet werden (kontinuierliche Autorisierung) und nicht nur zu Beginn der Sitzung.                      |   2   |   V   |
| 9.7.4 | Überprüfen Sie, dass delegierte Berechtigungen automatisch ablaufen und nach Ablauf der Zeitspanne oder bei Änderung des Umfangs eine erneute Zustimmung erforderlich ist.        |   3   |   D   |

---

## 9.8 Sicherheit der Agent-zu-Agent-Kommunikation

Verschlüsseln und Integritätsschutz für alle Nachrichten zwischen Agenten, um Abhören und Manipulationen zu verhindern.

|   #   | Beschreibung                                                                                                                                                            | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.8.1 | Stellen Sie sicher, dass gegenseitige Authentifizierung und perfekte Vorwärtsgeheimnis-Verschlüsselung (z. B. TLS 1.3) für Agentenkanäle obligatorisch sind.            |   1   |  D/V  |
| 9.8.2 | Stellen Sie sicher, dass die Nachrichtenintegrität und der Ursprung vor der Verarbeitung validiert werden; Fehler führen zu Warnungen und die Nachricht wird verworfen. |   1   |   D   |
| 9.8.3 | Stellen Sie sicher, dass Kommunikationsmetadaten (Zeitstempel, Sequenznummern) protokolliert werden, um eine forensische Rekonstruktion zu unterstützen.                |   2   |  D/V  |
| 9.8.4 | Stellen Sie sicher, dass die formale Verifikation oder Model-Checking bestätigt, dass Protokoll-Zustandsautomaten nicht in unsichere Zustände gebracht werden können.   |   3   |   V   |

---

## 9.9 Intent-Überprüfung & Durchsetzung von Beschränkungen

Überprüfen Sie, ob die Aktionen des Agenten mit der angegebenen Absicht des Benutzers und den Systembeschränkungen übereinstimmen.

|   #   | Beschreibung                                                                                                                                                                                  | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.9.1 | Stellen Sie sicher, dass Pre-Execution Constraint Solver vorgeschlagene Aktionen anhand von fest codierten Sicherheits- und Richtlinienregeln überprüfen.                                     |   1   |   D   |
| 9.9.2 | Stellen Sie sicher, dass Maßnahmen mit hoher Auswirkung (finanziell, zerstörerisch, datenschutzsensitiv) eine ausdrückliche Intentbestätigung des initiierenden Benutzers erfordern.          |   2   |  D/V  |
| 9.9.3 | Überprüfen Sie, dass Postconditionsprüfungen validieren, dass abgeschlossene Aktionen die beabsichtigten Effekte ohne Nebenwirkungen erreicht haben; Abweichungen lösen eine Rücksetzung aus. |   2   |   V   |
| 9.9.4 | Verifizieren Sie, dass formale Methoden (z. B. Modellüberprüfung, Theorembeweis) oder eigenschaftsbasierte Tests demonstrieren, dass Agentenpläne alle angegebenen Einschränkungen erfüllen.  |   3   |   V   |
| 9.9.5 | Stellen Sie sicher, dass Vorfälle von Intent-Mismatch oder Constraint-Verletzungen kontinuierliche Verbesserungszyklen und den Austausch von Bedrohungsinformationen fördern.                 |   3   |   D   |

---

## 9.10 Sicherheit der Agenten-Reasoning-Strategie

Sichere Auswahl und Ausführung verschiedener Denkstrategien, einschließlich ReAct, Chain-of-Thought und Tree-of-Thoughts Ansätzen.

|   #    | Beschreibung                                                                                                                                                                                                                                                            | Ebene | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.10.1 | Überprüfen Sie, dass die Auswahl der Argumentationsstrategie deterministische Kriterien verwendet (Eingabekomplexität, Aufgabentyp, Sicherheitskontext) und dass identische Eingaben innerhalb desselben Sicherheitskontexts zu identischen Strategiewahlen führen.     |   1   |  D/V  |
| 9.10.2 | Überprüfen Sie, dass jede Denkstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) eine dedizierte Eingabevalidierung, Ausgabe-Säuberung und spezifische Ausführungszeitbegrenzungen entsprechend ihrem kognitiven Ansatz aufweist.                                    |   1   |  D/V  |
| 9.10.3 | Überprüfen Sie, ob Übergänge der Denkstrategie mit vollständigem Kontext protokolliert werden, einschließlich Eingabemerkmalen, Werten der Auswahlkriterien und Ausführungsmetadaten zur Rekonstruktion der Prüfspur.                                                   |   2   |  D/V  |
| 9.10.4 | Stellen Sie sicher, dass das Tree-of-Thoughts-Reasoning Verzweigungsstornierungsmechanismen umfasst, die die Exploration beenden, wenn Richtlinienverletzungen, Ressourcenbeschränkungen oder Sicherheitsgrenzen erkannt werden.                                        |   2   |  D/V  |
| 9.10.5 | Überprüfen Sie, dass ReAct (Reason-Act-Observe)-Zyklen Validierungskontrollpunkte in jeder Phase enthalten: Verifizierung des Denkschritts, Autorisierung der Aktion und Bereinigung der Beobachtung vor dem Fortfahren.                                                |   2   |  D/V  |
| 9.10.6 | Überprüfen Sie, dass Leistungskennzahlen der Schlussfolgerungsstrategie (Ausführungszeit, Ressourcennutzung, Ausgabequalität) überwacht werden und automatisierte Alarme ausgelöst werden, wenn die Kennzahlen über die konfigurierten Schwellenwerte hinaus abweichen. |   3   |  D/V  |
| 9.10.7 | Stellen Sie sicher, dass hybride Reasoning-Ansätze, die mehrere Strategien kombinieren, die Eingabevalidierung und Ausgabegrenzen aller beteiligten Strategien einhalten, ohne dabei Sicherheitskontrollen zu umgehen.                                                  |   3   |  D/V  |
| 9.10.8 | Stellen Sie sicher, dass die Sicherheitstests der Denkstrategie Fuzzing mit fehlerhaften Eingaben, adversarielle Eingabeaufforderungen, die zum Erzwingen eines Strategiewechsels entworfen wurden, sowie Grenzwerttests für jeden kognitiven Ansatz umfassen.          |   3   |  D/V  |

---

## 9.11 Agent-Lebenszykluszustandsverwaltung & Sicherheit

Sichere Agenteninitalisierung, Zustandsübergänge und Beendigung mit kryptografischen Audit-Trails und definierten Wiederherstellungsverfahren.

|   #    | Beschreibung                                                                                                                                                                                                                                                                                                                                   | Ebene | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.11.1 | Stellen Sie sicher, dass die Agenteninitalisierung die Einrichtung einer kryptografischen Identität mit hardwaregestützten Anmeldeinformationen sowie unveränderliche Startprüfprotokolle enthält, die Agenten-ID, Zeitstempel, Konfigurations-Hash und Initialisierungsparameter umfassen.                                                    |   1   |  D/V  |
| 9.11.2 | Stellen Sie sicher, dass Agentenzustandsübergänge kryptografisch signiert, mit einem Zeitstempel versehen und mit vollständigem Kontext protokolliert werden, einschließlich auslösender Ereignisse, Hash des vorherigen Zustands, Hash des neuen Zustands und durchgeführter Sicherheitsprüfungen.                                            |   2   |  D/V  |
| 9.11.3 | Überprüfen Sie, dass die Agenten-Abschaltverfahren eine sichere Speicherlöschung mittels kryptographischer Löschung oder mehrfacher Überschreibung, die Zurückziehung von Berechtigungen mit Benachrichtigung der Zertifizierungsstelle sowie die Erstellung von manipulationssicheren Beendigungszertifikaten umfassen.                       |   2   |  D/V  |
| 9.11.4 | Überprüfen Sie, ob Agent-Wiederherstellungsmechanismen die Integrität des Zustands mithilfe kryptografischer Prüfsummen (mindestens SHA-256) validieren und bei erkannter Beschädigung automatisch auf bekannte fehlerfreie Zustände zurücksetzen, wobei automatisierte Warnmeldungen und manuelle Genehmigungsanforderungen verwendet werden. |   3   |  D/V  |
| 9.11.5 | Stellen Sie sicher, dass die Persistenzmechanismen der Agenten sensible Zustandsdaten mit pro-Agent AES-256-Schlüsseln verschlüsseln und eine sichere Schlüsselrotation nach konfigurierbaren Zeitplänen (maximal 90 Tage) mit Null-Ausfallzeit-Bereitstellung implementieren.                                                                 |   3   |  D/V  |

---

## 9.12 Sicherheitsrahmen für Werkzeugintegration

Sicherheitskontrollen für das dynamische Laden von Tools, deren Ausführung und Ergebnisvalidierung mit definierten Risikobewertungen und Genehmigungsverfahren.

|   #    | Beschreibung                                                                                                                                                                                                                                                                                                                    | Ebene | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.12.1 | Überprüfen Sie, ob Tool-Beschreibungen Sicherheitsmetadaten enthalten, die erforderliche Berechtigungen (Lesen/Schreiben/Ausführen), Risikostufen (niedrig/mittel/hoch), Ressourcengrenzen (CPU, Speicher, Netzwerk) und Validierungsanforderungen, die in den Tool-Manifests dokumentiert sind, angeben.                       |   1   |  D/V  |
| 9.12.2 | Stellen Sie sicher, dass die Ausführungsergebnisse von Tools vor der Integration anhand der erwarteten Schemas (JSON-Schema, XML-Schema) und der Sicherheitsrichtlinien (Ausgabe-Sanitierung, Datenklassifizierung) validiert werden, und implementieren Sie dabei Zeitlimitbeschränkungen sowie Fehlerbehandlungsverfahren.    |   1   |  D/V  |
| 9.12.3 | Stellen Sie sicher, dass Tool-Interaktionsprotokolle einen detaillierten Sicherheitskontext enthalten, einschließlich der Verwendung von Berechtigungen, Datenzugriffsmustern, Ausführungszeit, Ressourcenverbrauch und Rückgabecodes mit strukturierter Protokollierung für die SIEM-Integration.                              |   2   |  D/V  |
| 9.12.4 | Stellen Sie sicher, dass dynamische Werkzeuglade-Mechanismen digitale Signaturen unter Verwendung der PKI-Infrastruktur validieren und sichere Ladeprotokolle mit Sandbox-Isolierung sowie Berechtigungsverifizierung vor der Ausführung implementieren.                                                                        |   2   |  D/V  |
| 9.12.5 | Stellen Sie sicher, dass Sicherheitsbewertungen von Tools für neue Versionen automatisch ausgelöst werden, mit obligatorischen Genehmigungsschritten einschließlich statischer Analyse, dynamischer Tests und Überprüfung durch das Sicherheitsteam, einschließlich dokumentierter Genehmigungskriterien und SLA-Anforderungen. |   3   |  D/V  |

---

### Literaturverzeichnis

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

