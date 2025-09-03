# 9 autonome Orchestrierung und agentische Handlungssicherheit

## Kontrollziel

Stellen Sie sicher, dass autonome oder Multiagenten-KI-Systeme nur solche Handlungen ausführen können, die ausdrücklich beabsichtigt, authentifiziert und auditierbar sind und innerhalb begrenzter Kosten- und Risikogrenzen bleiben. Dies schützt vor Bedrohungen wie Autonomous-System Compromise, Tool Misuse, Agent Loop Detection, Communication Hijacking, Identity Spoofing, Swarm Manipulation und Intent Manipulation.

---

## 9.1 Agenten-Aufgabenplanung und Rekursionbudgets

Drosseln Sie rekursive Pläne und erzwingen Sie menschliche Kontrollpunkte für privilegierte Aktionen.

|   #   | Beschreibung                                                                                                                                                                                                 | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.1.1 | Überprüfen Sie, ob die maximale Rekursionstiefe, Breite, reale Zeit, Tokenanzahl und monetäre Kosten pro Agentenausführung zentral konfiguriert und versionskontrolliert sind.                               |   1   |  D/V  |
| 9.1.2 | Stellen Sie sicher, dass privilegierte oder irreversible Aktionen (z. B. Code-Commits, Finanztransfers) eine explizite menschliche Freigabe über einen auditierbaren Kanal vor der Ausführung erfordern.     |   1   |  D/V  |
| 9.1.3 | Stellen Sie sicher, dass Echtzeit-Ressourcenüberwachung eine Circuit-Breaker-Unterbrechung auslöst, wenn irgendeine Budgetgrenze überschritten wird, wodurch eine weitere Aufgabenerweiterung gestoppt wird. |   2   |   D   |
| 9.1.4 | Stellen Sie sicher, dass Circuit-Breaker-Ereignisse mit der Agenten-ID, der auslösenden Bedingung und dem erfassten Planzustand protokolliert werden, um eine forensische Auswertung zu ermöglichen.         |   2   |  D/V  |
| 9.1.5 | Stellen Sie sicher, dass Sicherheitstests Budgeterschöpfungs- und aus dem Ruder laufende Plan-Szenarien abdecken und ein sicheres Anhalten ohne Datenverlust bestätigen.                                     |   3   |   V   |
| 9.1.6 | Vergewissern Sie sich, dass Budgetrichtlinien als Policy-as-Code ausgedrückt werden und in CI/CD durchgesetzt werden, um Konfigurationsabweichungen zu verhindern.                                           |   3   |   D   |

---

## 9.2 Tool-Plugin-Sandboxing

Isolieren Sie Tool-Interaktionen, um unbefugten Systemzugriff oder Codeausführung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                 | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.2.1 | Überprüfen Sie, dass jedes Tool/Plugin innerhalb einer OS-, Container- oder WASM-Ebene Sandbox ausgeführt wird und Minimalberechtigungen für Dateisystem, Netzwerk und Systemaufrufe gelten. |   1   |  D/V  |
| 9.2.2 | Stellen Sie sicher, dass Sandbox-Ressourcenquoten (CPU, Speicher, Festplatte, ausgehender Netzwerkverkehr) durchgesetzt und protokolliert werden.                                            |   1   |  D/V  |
| 9.2.3 | Stellen Sie sicher, dass Tool-Binärdateien oder Deskriptoren digital signiert sind; Signaturen werden vor dem Laden validiert.                                                               |   2   |  D/V  |
| 9.2.4 | Überprüfen Sie, dass Sandbox-Telemetrie an ein SIEM gestreamt wird; Anomalien (z. B. ausgehende Verbindungen) lösen Alarme aus.                                                              |   2   |   V   |
| 9.2.5 | Stellen Sie sicher, dass Hochrisiko-Plugins einer Sicherheitsüberprüfung und Penetrationstests unterzogen werden, bevor sie in die Produktion bereitgestellt werden.                         |   3   |   V   |
| 9.2.6 | Stellen Sie sicher, dass Sandbox-Ausbruchsversuche automatisch blockiert werden und das betreffende Plugin bis zur Untersuchung in Quarantäne gestellt wird.                                 |   3   |  D/V  |

---

## 9.3 Autonome Schleife und Kostenbegrenzung

Erkennen und stoppen Sie unkontrollierte Agent-zu-Agenten-Rekursion und Kostenexplosionen.

|   #   | Beschreibung                                                                                                                                                       | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.3.1 | Überprüfen Sie, ob Aufrufe zwischen Agenten ein Hop-Limit oder TTL enthalten, das von der Laufzeitumgebung dekrementiert und durchgesetzt wird.                    |   1   |  D/V  |
| 9.3.2 | Vergewissern Sie sich, dass Agenten eine eindeutige Aufruf-Graph-ID beibehalten, um Selbstaufrufe oder zyklische Muster zu erkennen.                               |   2   |   D   |
| 9.3.3 | Stellen Sie sicher, dass kumulative Compute-Einheit- und Kosten-Zähler pro Anfragekette verfolgt werden; bei Überschreitung des Limits wird die Kette abgebrochen. |   2   |  D/V  |
| 9.3.4 | Stellen Sie sicher, dass formale Analysen oder die Modellprüfung das Fehlen unbeschränkter Rekursion in Agentenprotokollen nachweist.                              |   3   |   V   |
| 9.3.5 | Überprüfen Sie, ob Schleifenabbruch-Ereignisse Alarme erzeugen und Metriken zur kontinuierlichen Verbesserung liefern.                                             |   3   |   D   |

---

## 9.4 Protokoll-Ebene Missbrauchsschutz

Sichere Kommunikationskanäle zwischen Agenten und externen Systemen, um Sitzungsübernahme oder Manipulation zu verhindern.

|   #   | Beschreibung                                                                                                                                                        | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.4.1 | Stellen Sie sicher, dass alle Agent-zu-Tool- und Agent-zu-Agent-Nachrichten authentifiziert und Ende-zu-Ende-verschlüsselt sind (z. B. gegenseitiges TLS oder JWT). |   1   |  D/V  |
| 9.4.2 | Stellen Sie sicher, dass Schemata streng validiert werden; unbekannte Felder oder fehlerhafte Nachrichten werden abgelehnt.                                         |   1   |   D   |
| 9.4.3 | Stellen Sie sicher, dass Integritätsprüfungen (MACs oder digitale Signaturen) die gesamte Nutzlast der Nachricht abdecken, einschließlich der Tool-Parameter.       |   2   |  D/V  |
| 9.4.4 | Stellen Sie sicher, dass der Replay-Schutz (Nonces oder Zeitstempel-Fenster) auf Protokollebene durchgesetzt wird.                                                  |   2   |   D   |
| 9.4.5 | Stellen Sie sicher, dass Protokollimplementierungen Fuzzing und statische Analysen durchlaufen, um Injektions- oder Deserialisierungsfehler zu erkennen.            |   3   |   V   |

---

## 9.5 Agentenidentität & Manipulationsnachweis

Sicherstellen, dass Handlungen zuordenbar und Änderungen nachverfolgbar sind.

|   #   | Beschreibung                                                                                                                                                | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.5.1 | Verifizieren Sie, dass jede Agenteninstanz eine eindeutige kryptografische Identität besitzt (Schlüsselpaar oder hardwareverwurzelte Anmeldeinformationen). |   1   |  D/V  |
| 9.5.2 | Stellen Sie sicher, dass alle Agentenaktionen signiert und mit Zeitstempel versehen sind; Protokolle enthalten die Signatur zur Nichtabstreitbarkeit.       |   2   |  D/V  |
| 9.5.3 | Überprüfen Sie, ob manipulationssichere Protokolle in einem append-only oder write-once Medium gespeichert werden.                                          |   2   |   V   |
| 9.5.4 | Stellen Sie sicher, dass Identitätsschlüssel gemäß einem definierten Zeitplan sowie bei Anzeichen einer Kompromittierung rotiert werden.                    |   3   |   D   |
| 9.5.5 | Überprüfen Sie, ob Spoofing oder Schlüssel-Konfliktversuche eine sofortige Quarantäne des betroffenen Agenten auslösen.                                     |   3   |  D/V  |

---

## 9.6 Mehr-Agent Schwarm Risikoreduzierung

Kollektive Verhaltensrisiken durch Isolation und formale Sicherheitsmodellierung mindern.

|   #   | Beschreibung                                                                                                                                                   | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.6.1 | Stellen Sie sicher, dass Agenten, die in verschiedenen Sicherheitsdomänen arbeiten, in isolierten Laufzeit-Sandboxen oder Netzwerksegmenten ausgeführt werden. |   1   |  D/V  |
| 9.6.2 | Stellen Sie sicher, dass das Schwarmverhalten modelliert und formell verifiziert wird, um Lebensfähigkeit und Sicherheit vor dem Einsatz zu gewährleisten.     |   3   |   V   |
| 9.6.3 | Überprüfen Sie, dass Laufzeit-Monitore aufkommende unsichere Muster erkennen (z. B. Oszillationen, Deadlocks) und entsprechende Gegenmaßnahmen einleiten.      |   3   |   D   |

---

## 9.7 Benutzer- und Tool-Authentifizierung / Autorisierung

Implementieren Sie robuste Zugriffskontrollen für jede vom Agenten ausgelöste Aktion.

|   #   | Beschreibung                                                                                                                                                                      | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.7.1 | Stellen Sie sicher, dass Agenten sich gegenüber nachgelagerten Systemen als First-Class-Principals authentifizieren und niemals Endbenutzer-Anmeldeinformationen wiederverwenden. |   1   |  D/V  |
| 9.7.2 | Überprüfen Sie, dass feingranulare Autorisierungsrichtlinien einschränken, welche Werkzeuge ein Agent aufrufen darf und welche Parameter er angeben darf.                         |   2   |   D   |
| 9.7.3 | Vergewissern Sie sich, dass Berechtigungsprüfungen bei jedem Aufruf erneut bewertet werden (kontinuierliche Autorisierung) und nicht nur beim Start der Sitzung.                  |   2   |   V   |
| 9.7.4 | Überprüfen Sie, ob delegierte Berechtigungen automatisch ablaufen und nach Ablauf der Frist oder bei Änderungen des Umfangs eine erneute Zustimmung erforderlich ist.             |   3   |   D   |

---

## 9.8 Sicherheit der Agent-zu-Agent-Kommunikation

Alle Inter-Agenten-Nachrichten verschlüsseln und deren Integrität sicherstellen, um Abhören und Manipulation zu verhindern.

|   #   | Beschreibung                                                                                                                                                                     | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.8.1 | Stellen Sie sicher, dass gegenseitige Authentifizierung und Verschlüsselung mit Perfect Forward Secrecy (PFS) (z. B. TLS 1.3) für Agentkanäle verpflichtend sind.                |   1   |  D/V  |
| 9.8.2 | Verifizieren Sie, dass die Nachrichtenintegrität und der Ursprung vor der Verarbeitung validiert werden; Bei Fehlern werden Warnmeldungen ausgelöst und die Nachricht verworfen. |   1   |   D   |
| 9.8.3 | Überprüfen Sie, dass Kommunikationsmetadaten (Zeitstempel, Sequenznummern) protokolliert werden, um eine forensische Rekonstruktion zu unterstützen.                             |   2   |  D/V  |
| 9.8.4 | Verifizieren Sie, dass die formale Verifikation oder die Modellprüfung bestätigt, dass Protokoll-Zustandsmaschinen nicht in unsichere Zustände geführt werden können.            |   3   |   V   |

---

## 9.9 Absicht-Verifikation & Durchsetzung von Beschränkungen

Überprüfen Sie, ob die Handlungen des Agenten mit der vom Benutzer geäußerten Absicht und den Systembeschränkungen übereinstimmen.

|   #   | Beschreibung                                                                                                                                                                                           | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.9.1 | Stellen Sie sicher, dass Vor-Ausführungs-Constraint-Solver die vorgeschlagenen Aktionen gegen fest codierte Sicherheits- und Richtlinienregeln prüfen.                                                 |   1   |   D   |
| 9.9.2 | Stellen Sie sicher, dass Aktionen mit hohem Einfluss (finanzielle, destruktive, datenschutzrelevante) eine explizite Bestätigung der Absicht durch den initiierenden Benutzer erfordern.               |   2   |  D/V  |
| 9.9.3 | Vergewissern Sie sich, dass Nachbedingungsprüfungen bestätigen, dass die abgeschlossenen Aktionen die beabsichtigten Wirkungen ohne Nebeneffekte erzielt haben; Abweichungen lösen einen Rollback aus. |   2   |   V   |
| 9.9.4 | Verifizieren Sie, dass formale Methoden (z. B. Modellprüfung, Theorembeweis) oder eigenschaftsbasierte Tests nachweisen, dass die Pläne des Agenten alle deklarierten Anforderungen erfüllen.          |   3   |   V   |
| 9.9.5 | Überprüfen Sie, dass Vorfälle von Absichtsdiskrepanz oder Verstößen gegen Beschränkungen kontinuierliche Verbesserungszyklen und den Austausch von Bedrohungsinformationen antreiben.                  |   3   |   D   |

---

## 9.10 Agent Schlussfolgerungsstrategie Sicherheit

Sichere Auswahl und Durchführung verschiedener Denkstrategien, einschließlich ReAct, Chain-of-Thought und Tree-of-Thoughts-Ansätze.

|   #    | Beschreibung                                                                                                                                                                                                                                                 | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.10.1 | Stellen Sie sicher, dass die Auswahl der Schlussfolgerungsstrategie deterministische Kriterien verwendet (Eingabekomplexität, Aufgabentyp, Sicherheitskontext) und identische Eingaben im gleichen Sicherheitskontext zu identischen Strategiewahlen führen. |   1   |  D/V  |
| 9.10.2 | Überprüfen Sie, dass jede Denkstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) über dedizierte Eingabevalidierung, Ausgabebereinigung und Ausführungszeitbeschränkungen verfügt, die spezifisch auf ihren kognitiven Ansatz zugeschnitten sind.         |   1   |  D/V  |
| 9.10.3 | Stellen Sie sicher, dass Wechsel der Begründungsstrategie mit vollständigem Kontext protokolliert wird, einschließlich Eingabecharakteristika, Werte der Auswahlkriterien und Ausführungsmetadaten zur Rekonstruktion der Audit-Spur.                        |   2   |  D/V  |
| 9.10.4 | Überprüfen Sie, ob der Tree-of-Thoughts-Ansatz Mechanismen zur Zweig-Ausdünkung enthält, die die Erkundung beenden, wenn Richtlinienverstöße, Ressourcenbeschränkungen oder Sicherheitsgrenzen erkannt werden.                                               |   2   |  D/V  |
| 9.10.5 | Vergewissern Sie sich, dass ReAct (Reason-Act-Observe) Zyklen Validierungspunkte in jeder Phase enthalten: Überprüfung der Schlussfolgerungsschritte, Autorisierung der Aktion und Bereinigung der Beobachtungen, bevor fortgefahren wird.                   |   2   |  D/V  |
| 9.10.6 | Stellen Sie sicher, dass die Leistungskennzahlen der Schlussfolgerungsstrategie (Ausführungszeit, Ressourcenverbrauch, Ausgabequalität) durch automatisierte Warnungen überwacht werden, wenn die Metriken von den konfigurierten Schwellenwerten abweichen. |   3   |  D/V  |
| 9.10.7 | Überprüfen Sie, dass hybride Schlussfolgerungsansätze, die mehrere Strategien kombinieren, die Eingabevalidierung und die Ausgabebeschränkungen aller einzelnen Strategien beibehalten, ohne Sicherheitskontrollen zu umgehen.                               |   3   |  D/V  |
| 9.10.8 | Stellen Sie sicher, dass die Sicherheitstests der Denkstrategien Fuzzing mit fehlerhaften Eingaben, adversariale Prompts, die darauf abzielen, einen Strategiewechsel zu erzwingen, sowie Grenzwerte-Tests für jeden kognitiven Ansatz umfassen.             |   3   |  D/V  |

---

## 9.11 Agentenlebenszyklus Zustandsverwaltung und Sicherheit

Sichere Initialisierung des Agenten, Zustandsübergänge und Beendigung mit kryptografischen Audit-Trails und definierten Wiederherstellungsverfahren.

|   #    | Beschreibung                                                                                                                                                                                                                                                                                                                                         | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.11.1 | Überprüfen Sie, dass die Initialisierung des Agenten eine kryptografische Identitätsfeststellung mit hardwaregestützten Berechtigungsnachweisen umfasst und unveränderliche Start-Auditprotokolle enthält, die Agenten-ID, Zeitstempel, Konfigurations-Hash und Initialisierungsparameter enthalten.                                                 |   1   |  D/V  |
| 9.11.2 | Stellen Sie sicher, dass Zustandsübergänge des Agenten kryptografisch signiert, mit Zeitstempel versehen und protokolliert werden, und dass der vollständige Kontext enthalten ist, einschließlich der auslösenden Ereignisse, des Hashes des vorherigen Zustands, des Hashes des neuen Zustands und der durchgeführten Sicherheitsprüfungen.        |   2   |  D/V  |
| 9.11.3 | Vergewissern Sie sich, dass die Abschaltverfahren des Agenten eine sichere Speicherlöschung umfassen (entweder kryptografische Löschung oder Mehrfachüberschreibung), den Widerruf von Anmeldeinformationen mit Benachrichtigung der Zertifizierungsstelle berücksichtigen und die Erstellung manipulationssicherer Beendigungszertifikate vorsehen. |   2   |  D/V  |
| 9.11.4 | Überprüfen Sie, dass die Wiederherstellungsmechanismen für Agenten die Integrität des Zustands mithilfe kryptografischer Prüfsummen (mindestens SHA-256) validieren und bei Feststellung von Beschädigungen auf bekannte gute Zustände zurücksetzen, mit automatisierten Warnmeldungen und Anforderungen an manuelle Genehmigungen.                  |   3   |  D/V  |
| 9.11.5 | Stellen Sie sicher, dass die Persistenzmechanismen der Agenten die sensiblen Zustandsdaten mit pro-Agent AES-256-Schlüsseln verschlüsseln und implementieren Sie eine sichere Schlüsselrotation nach konfigurierbaren Rotationsplänen (max. 90 Tage) mit Deployment ohne Ausfallzeit.                                                                |   3   |  D/V  |

---

## 9.12 Sicherheitsrahmen für Tool-Integration

Sicherheitskontrollen für das dynamische Laden von Tools, Ausführung und Ergebnisvalidierung mit definierten Risikobewertungs- und Freigabeprozessen.

|   #    | Beschreibung                                                                                                                                                                                                                                                                                                         | Level | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.12.1 | Stellen Sie sicher, dass Toolbeschreibungen Sicherheitsmetadaten enthalten, die die erforderlichen Berechtigungen (Lesen/Schreiben/Ausführen), Risikostufen (niedrig/mittel/hoch) und Ressourcenlimits (CPU, Speicher, Netzwerk) sowie Validierungsanforderungen, die in Tool-Manifeste dokumentiert sind, angeben.  |   1   |  D/V  |
| 9.12.2 | Stellen Sie sicher, dass die Ergebnisse der Toolausführung gegen die erwarteten Schemas (JSON Schema, XML Schema) und Sicherheitsrichtlinien (Ausgabensanitisierung, Datenklassifizierung) validiert werden, bevor die Integration mit Timeout-Limits und Fehlerbehandlungsverfahren erfolgt.                        |   1   |  D/V  |
| 9.12.3 | Stellen Sie sicher, dass Tool-Interaktionsprotokolle einen detaillierten Sicherheitskontext enthalten, einschließlich Privilegienverwendung, Muster des Datenzugriffs, Ausführungszeit, Ressourcenverbrauch und Rückgabewerten, mit strukturierter Protokollierung für die SIEM-Integration.                         |   2   |  D/V  |
| 9.12.4 | Verifizieren Sie, dass dynamische Tool-Lade-Mechanismen digitale Signaturen mithilfe der PKI-Infrastruktur validieren, und implementieren Sie sichere Ladeprotokolle mit Sandbox-Isolation und Berechtigungsprüfung vor der Ausführung.                                                                              |   2   |  D/V  |
| 9.12.5 | Stellen Sie sicher, dass Tool-Sicherheitsbewertungen für neue Versionen automatisch ausgelöst werden, die verpflichtenden Freigabestufen umfassen, darunter statische Analyse, dynamische Tests und eine Überprüfung durch das Sicherheitsteam, zusammen mit dokumentierten Freigabekriterien und SLA-Anforderungen. |   3   |  D/V  |

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

