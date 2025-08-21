# 9 Autonome Orchestrierung & Agentische Handlungssicherheit

## Kontrollziel

Stellen Sie sicher, dass autonome oder Multi-Agenten-KI-Systeme nur Aktionen ausführen können, die ausdrücklich beabsichtigt, authentifiziert, prüfbar und innerhalb festgelegter Kosten- und Risikoschwellen liegen. Dies schützt vor Bedrohungen wie Kompromittierung autonomer Systeme, Missbrauch von Werkzeugen, Agentenschleifen-Erkennung, Kommunikationsübernahme, Identitätsfälschung, Schwarmmanipulation und Absichtsmanipulation.

---

## 9.1 Aufgabenplanung von Agenten und Rekursionsbudgets

Drosseln Sie rekursive Pläne und erzwingen Sie menschliche Kontrollpunkte für privilegierte Aktionen.

|   #   | Beschreibung                                                                                                                                                                                                             | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.1.1 | Stellen Sie sicher, dass maximale Rekursionstiefe, Breite, Echtzeitdauer, Tokens und monetäre Kosten pro Agentenausführung zentral konfiguriert und versioniert sind.                                                    |   1   |  D/V  |
| 9.1.2 | Vergewissern Sie sich, dass privilegierte oder unumkehrbare Aktionen (z. B. Code-Commits, finanzielle Überweisungen) vor der Ausführung eine ausdrückliche menschliche Genehmigung über einen prüfbaren Kanal erfordern. |   1   |  D/V  |
| 9.1.3 | Überprüfen Sie, ob Echtzeit-Ressourcenmonitoren eine Circuit-Breaker-Unterbrechung auslösen, wenn eine Budgetgrenze überschritten wird, und dadurch die weitere Aufgabenerweiterung stoppen.                             |   2   |   D   |
| 9.1.4 | Stellen Sie sicher, dass Circuit-Breaker-Ereignisse mit Agenten-ID, auslösendem Zustand und erfasstem Planstatus zur forensischen Überprüfung protokolliert werden.                                                      |   2   |  D/V  |
| 9.1.5 | Verifizieren Sie, dass Sicherheitstests Szenarien der Budgeterschöpfung und des Ausbruchs von Plänen abdecken und einen sicheren Stopp ohne Datenverlust bestätigen.                                                     |   3   |   V   |
| 9.1.6 | Stellen Sie sicher, dass Budgetrichtlinien als Policy-as-Code formuliert und in CI/CD durchgesetzt werden, um Konfigurationsabweichungen zu verhindern.                                                                  |   3   |   D   |

---

## 9.2 Tool-Plugin-Sandboxing

Isoliere Werkzeuginteraktionen, um unbefugten Systemzugriff oder Codeausführung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.2.1 | Stellen Sie sicher, dass jedes Tool/Plugin innerhalb eines Betriebssystems, Containers oder einer WASM-Ebene-Sandbox mit minimalen Berechtigungen für Dateisystem-, Netzwerk- und Systemaufruf-Richtlinien ausgeführt wird. |   1   |  D/V  |
| 9.2.2 | Stellen Sie sicher, dass Sandbox-Ressourcenkontingente (CPU, Speicher, Festplatte, Netzwerkausgang) und Ausführungszeitlimits durchgesetzt und protokolliert werden.                                                        |   1   |  D/V  |
| 9.2.3 | Stellen Sie sicher, dass Werkzeug-Binärdateien oder Beschreibungen digital signiert sind; die Signaturen werden vor dem Laden überprüft.                                                                                    |   2   |  D/V  |
| 9.2.4 | Überprüfen Sie, ob die Sandbox-Telemetrie an ein SIEM übertragen wird; Anomalien (z. B. versuchte ausgehende Verbindungen) lösen Alarme aus.                                                                                |   2   |   V   |
| 9.2.5 | Stellen Sie sicher, dass Plugins mit hohem Risiko vor dem produktiven Einsatz einer Sicherheitsüberprüfung und Penetrationstests unterzogen werden.                                                                         |   3   |   V   |
| 9.2.6 | Überprüfen Sie, ob Sandbox-Ausbruchsversuche automatisch blockiert werden und das betreffende Plugin bis zur Untersuchung unter Quarantäne gestellt wird.                                                                   |   3   |  D/V  |

---

## 9.3 Autonome Schleife & Kostenbegrenzung

Erkennen und stoppen Sie unkontrollierte Agent-zu-Agent-Rekursionen und Kostenexplosionen.

|   #   | Beschreibung                                                                                                                                                      | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.3.1 | Überprüfen Sie, ob Inter-Agent-Aufrufe eine Hop-Grenze oder TTL enthalten, die zur Laufzeit dekrementiert und durchgesetzt wird.                                  |   1   |  D/V  |
| 9.3.2 | Stellen Sie sicher, dass Agenten eine eindeutige Invocation-Graph-ID beibehalten, um Selbstaufrufe oder zyklische Muster zu erkennen.                             |   2   |   D   |
| 9.3.3 | Überprüfen Sie, dass kumulative Compute-Unit- und Ausgabenzähler pro Anforderungskette verfolgt werden; das Überschreiten des Limits führt zum Abbruch der Kette. |   2   |  D/V  |
| 9.3.4 | Überprüfen Sie, dass die formale Analyse oder das Model Checking das Fehlen von unbeschränkter Rekursion in Agentenprotokollen nachweist.                         |   3   |   V   |
| 9.3.5 | Überprüfen Sie, ob Schleifen-Abbruchereignisse Warnungen generieren und kontinuierliche Verbesserungskennzahlen speisen.                                          |   3   |   D   |

---

## 9.4 Schutz vor Protokollebene-Missbrauch

Sichere Kommunikationskanäle zwischen Agenten und externen Systemen, um Entführung oder Manipulation zu verhindern.

|   #   | Beschreibung                                                                                                                                                           | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.4.1 | Verifizieren Sie, dass alle Nachrichten von Agent zu Tool und von Agent zu Agent authentifiziert sind (z. B. Mutual TLS oder JWT) und Ende-zu-Ende verschlüsselt sind. |   1   |  D/V  |
| 9.4.2 | Stellen Sie sicher, dass Schemata strikt validiert werden; unbekannte Felder oder fehlerhafte Nachrichten werden abgelehnt.                                            |   1   |   D   |
| 9.4.3 | Stellen Sie sicher, dass Integritätsprüfungen (MACs oder digitale Signaturen) den gesamten Nachrichteninhalt einschließlich der Werkzeugparameter abdecken.            |   2   |  D/V  |
| 9.4.4 | Stellen Sie sicher, dass der Wiedergabeschutz (Nonces oder Zeitstempelfenster) auf der Protokollebene durchgesetzt wird.                                               |   2   |   D   |
| 9.4.5 | Stellen Sie sicher, dass Protokollimplementierungen einem Fuzzing und einer statischen Analyse auf Injektions- oder Deserialisierungsfehler unterzogen werden.         |   3   |   V   |

---

## 9.5 Agentenidentität & Manipulationsnachweis

Stellen Sie sicher, dass Aktionen zurückverfolgbar sind und Änderungen erkennbar bleiben.

|   #   | Beschreibung                                                                                                                                         | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.5.1 | Überprüfen Sie, ob jede Agenteninstanz eine eindeutige kryptografische Identität besitzt (Schlüsselpaar oder hardwarebasierte Anmeldeinformationen). |   1   |  D/V  |
| 9.5.2 | Überprüfen Sie, dass alle Agentenaktionen signiert und mit Zeitstempel versehen sind; Protokolle enthalten die Signatur zur Nichtabstreitbarkeit.    |   2   |  D/V  |
| 9.5.3 | Stellen Sie sicher, dass manipulationssichere Protokolle in einem nur-anhängbaren oder einmal beschreibbaren Medium gespeichert werden.              |   2   |   V   |
| 9.5.4 | Überprüfen Sie, dass Identitätsschlüssel gemäß einem definierten Zeitplan und bei Anzeichen einer Kompromittierung rotieren.                         |   3   |   D   |
| 9.5.5 | Überprüfen Sie, dass Spoofing- oder Schlüsselkonfliktversuche eine sofortige Quarantäne des betroffenen Agents auslösen.                             |   3   |  D/V  |

---

## 9.6 Multi-Agent Schwarm-Risikoreduzierung

Mildern Sie kollektives Verhaltensrisiken durch Isolation und formale Sicherheitsmodellierung.

|   #   | Beschreibung                                                                                                                                               | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.6.1 | Überprüfen Sie, dass Agenten, die in verschiedenen Sicherheitsdomänen arbeiten, in isolierten Laufzeit-Sandboxen oder Netzwerksegmenten ausgeführt werden. |   1   |  D/V  |
| 9.6.2 | Stellen Sie sicher, dass Schwarmverhalten modelliert und formell auf Lebendigkeit und Sicherheit vor der Bereitstellung überprüft werden.                  |   3   |   V   |
| 9.6.3 | Überprüfen Sie, ob Laufzeit-Monitore aufkommende unsichere Muster (z. B. Oszillationen, Deadlocks) erkennen und Korrekturmaßnahmen einleiten.              |   3   |   D   |

---

## 9.7 Benutzer- und Werkzeugauthentifizierung / Autorisierung

Implementieren Sie robuste Zugriffskontrollen für jede agenteninitiierte Aktion.

|   #   | Beschreibung                                                                                                                                                                | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.7.1 | Stellen Sie sicher, dass Agenten sich als erstklassige Prinzipale bei nachgelagerten Systemen authentifizieren und niemals Endbenutzeranmeldeinformationen wiederverwenden. |   1   |  D/V  |
| 9.7.2 | Überprüfen Sie, dass feinkörnige Autorisierungsrichtlinien einschränken, welche Tools ein Agent aufrufen darf und welche Parameter er angeben darf.                         |   2   |   D   |
| 9.7.3 | Überprüfen Sie, dass die Berechtigungsprüfungen bei jedem Aufruf erneut bewertet werden (kontinuierliche Autorisierung) und nicht nur zu Beginn der Sitzung.                |   2   |   V   |
| 9.7.4 | Stellen Sie sicher, dass delegierte Privilegien automatisch ablaufen und nach Ablauf der Frist oder einer Änderung des Umfangs eine erneute Zustimmung erforderlich ist.    |   3   |   D   |

---

## 9.8 Sicherheit der Agent-zu-Agent-Kommunikation

Verschlüsseln und integritätssichern Sie alle Nachrichten zwischen Agenten, um Abhören und Manipulation zu verhindern.

|   #   | Beschreibung                                                                                                                                                                         | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.8.1 | Stellen Sie sicher, dass gegenseitige Authentifizierung und perfekte Vorwärtsgeheimnis-Verschlüsselung (z. B. TLS 1.3) für Agentenkanäle obligatorisch sind.                         |   1   |  D/V  |
| 9.8.2 | Überprüfen Sie, dass die Nachrichtenintegrität und der Ursprung validiert werden, bevor die Verarbeitung erfolgt; Fehler lösen Warnungen aus und führen zum Verwerfen der Nachricht. |   1   |   D   |
| 9.8.3 | Stellen Sie sicher, dass Kommunikationsmetadaten (Zeitstempel, Sequenznummern) protokolliert werden, um eine forensische Rekonstruktion zu unterstützen.                             |   2   |  D/V  |
| 9.8.4 | Stellen Sie sicher, dass die formale Verifikation oder Modellüberprüfung bestätigt, dass Protokoll-Zustandsautomaten nicht in unsichere Zustände geführt werden können.              |   3   |   V   |

---

## 9.9 Absichtsüberprüfung und Durchsetzung von Einschränkungen

Überprüfen Sie, ob die Aktionen des Agenten mit der angegebenen Absicht des Benutzers und den Systembeschränkungen übereinstimmen.

|   #   | Beschreibung                                                                                                                                                                                     | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 9.9.1 | Überprüfen Sie, dass vor der Ausführung Constraint-Solver vorgeschlagene Aktionen anhand von fest programmierten Sicherheits- und Richtlinienregeln prüfen.                                      |   1   |   D   |
| 9.9.2 | Stellen Sie sicher, dass Maßnahmen mit hoher Auswirkung (finanziell, destruktiv, datenschutzsensibel) eine ausdrückliche Intentionbestätigung des initiierenden Benutzers erfordern.             |   2   |  D/V  |
| 9.9.3 | Überprüfen Sie, dass Nachbedingungsprüfungen bestätigen, dass abgeschlossene Aktionen die beabsichtigten Effekte ohne Nebenwirkungen erreicht haben; Abweichungen lösen eine Rückrollaktion aus. |   2   |   V   |
| 9.9.4 | Stellen Sie sicher, dass formale Methoden (z. B. Modellprüfung, Theorembeweis) oder eigenschaftsbasierte Tests nachweisen, dass Agentenpläne alle deklarierten Einschränkungen erfüllen.         |   3   |   V   |
| 9.9.5 | Stellen Sie sicher, dass Vorfälle mit Absichtsabweichungen oder Verstoß gegen Auflagen kontinuierliche Verbesserungszyklen und den Austausch von Bedrohungsinformationen fördern.                |   3   |   D   |

---

## 9.10 Sicherheitsstrategie für die Agentenlogik

Sichere Auswahl und Ausführung verschiedener Denkstrategien, einschließlich ReAct-, Chain-of-Thought- und Tree-of-Thoughts-Ansätzen.

|   #    | Beschreibung                                                                                                                                                                                                                                                              | Level | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.10.1 | Überprüfen Sie, dass die Auswahl der Reasoning-Strategie deterministische Kriterien verwendet (Eingabekomplexität, Aufgabentyp, Sicherheitskontext) und dass identische Eingaben innerhalb desselben Sicherheitskontexts identische Strategiewahlen ergeben.              |   1   |  D/V  |
| 9.10.2 | Stellen Sie sicher, dass jede Denkstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) eine dedizierte Eingabevalidierung, Ausgabe-Säuberung und spezifische Ausführungszeitbegrenzungen entsprechend ihrem kognitiven Ansatz besitzt.                                   |   1   |  D/V  |
| 9.10.3 | Stellen Sie sicher, dass Übergänge der Argumentationsstrategie mit vollständigem Kontext protokolliert werden, einschließlich Eingabeeigenschaften, Auswahlkriterienwerten und Ausführungsmetadaten zur Nachverfolgung des Prüfpfads.                                     |   2   |  D/V  |
| 9.10.4 | Stellen Sie sicher, dass die Tree-of-Thoughts-Argumentation Verzweigungsbeschneidungsmechanismen beinhaltet, die die Exploration beenden, wenn Richtlinienverstöße, Ressourcenbeschränkungen oder Sicherheitsgrenzen erkannt werden.                                      |   2   |  D/V  |
| 9.10.5 | Stellen Sie sicher, dass ReAct (Reason-Act-Observe)-Zyklen Validierungskontrollpunkte in jeder Phase beinhalten: Verifikation des Denkprozesses, Autorisierung der Handlung und Bereinigung der Beobachtung vor dem Fortfahren.                                           |   2   |  D/V  |
| 9.10.6 | Stellen Sie sicher, dass die Leistungskennzahlen der Argumentationsstrategie (Ausführungszeit, Ressourcenverbrauch, Ausgabequalität) überwacht werden und automatisierte Warnungen ausgelöst werden, wenn die Kennzahlen die konfigurierten Schwellenwerte überschreiten. |   3   |  D/V  |
| 9.10.7 | Stellen Sie sicher, dass hybride Reasoning-Ansätze, die mehrere Strategien kombinieren, die Eingabevalidierung und Ausgabegrenzen aller beteiligten Strategien einhalten, ohne dabei Sicherheitskontrollen zu umgehen.                                                    |   3   |  D/V  |
| 9.10.8 | Stellen Sie sicher, dass die Sicherheitstests der Reasoning-Strategie Fuzzing mit fehlerhaften Eingaben, adversariale Eingabeaufforderungen, die darauf ausgelegt sind, einen Strategiewechsel zu erzwingen, sowie Grenzwerttests für jeden kognitiven Ansatz umfassen.   |   3   |  D/V  |

---

## 9.11 Agent-Lebenszyklus Zustandsverwaltung & Sicherheit

Sichere Agenteninitalisierung, Zustandsübergänge und Beendigung mit kryptografischen Prüfpfaden und definierten Wiederherstellungsverfahren.

|   #    | Beschreibung                                                                                                                                                                                                                                                                                                                       | Level | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.11.1 | Stellen Sie sicher, dass die Agenteninitialisierung die Einrichtung einer kryptografischen Identität mit hardwaregestützten Anmeldeinformationen und unveränderlichen Start-Auditprotokollen umfasst, die die Agenten-ID, den Zeitstempel, den Konfigurations-Hash und die Initialisierungsparameter enthalten.                    |   1   |  D/V  |
| 9.11.2 | Stellen Sie sicher, dass Zustandsübergänge des Agenten kryptografisch signiert, mit Zeitstempel versehen und mit vollständigem Kontext protokolliert werden, einschließlich auslösender Ereignisse, Hash des vorherigen Zustands, Hash des neuen Zustands und durchgeführter Sicherheitsüberprüfungen.                             |   2   |  D/V  |
| 9.11.3 | Stellen Sie sicher, dass die Agenten-Abschaltverfahren eine sichere Speicherlöschung mittels kryptografischer Vernichtung oder mehrfacher Überschreibung, die Widerrufung von Anmeldeinformationen mit Benachrichtigung der Zertifizierungsstelle sowie die Erstellung von manipulationssicheren Beendigungszertifikaten umfassen. |   2   |  D/V  |
| 9.11.4 | Stellen Sie sicher, dass Agent-Wiederherstellungsmechanismen die Integrität des Zustands mithilfe kryptografischer Prüfsummen (mindestens SHA-256) validieren und bei erkannter Beschädigung auf bekannte intakte Zustände zurücksetzen, wobei automatisierte Warnungen und manuelle Genehmigungsanforderungen erforderlich sind.  |   3   |  D/V  |
| 9.11.5 | Überprüfen Sie, ob Agenten-Persistenzmechanismen sensible Zustandsdaten mit pro-Agent AES-256-Schlüsseln verschlüsseln und eine sichere Schlüsselrotation nach konfigurierbaren Zeitplänen (maximal 90 Tage) mit unterbrechungsfreier Bereitstellung implementieren.                                                               |   3   |  D/V  |

---

## 9.12 Sicherheitsrahmen für Werkzeugintegration

Sicherheitskontrollen für das dynamische Laden von Tools, deren Ausführung und Ergebnisvalidierung mit definierten Risikoabschätzungs- und Genehmigungsverfahren.

|   #    | Beschreibung                                                                                                                                                                                                                                                                                                          | Level | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 9.12.1 | Stellen Sie sicher, dass Tool-Beschreibungen Sicherheits-Metadaten enthalten, die erforderliche Berechtigungen (Lesen/Schreiben/Ausführen), Risikostufen (niedrig/mittel/hoch), Ressourcenbeschränkungen (CPU, Speicher, Netzwerk) und Validierungsanforderungen dokumentiert in Tool-Manifests angeben.              |   1   |  D/V  |
| 9.12.2 | Stellen Sie sicher, dass die Ergebnisse der Toolausführung vor der Integration anhand der erwarteten Schemata (JSON-Schema, XML-Schema) und Sicherheitsrichtlinien (Ausgabereinigung, Datenklassifizierung) validiert werden, unter Einhaltung von Zeitlimits und Fehlerbehandlungsverfahren.                         |   1   |  D/V  |
| 9.12.3 | Stellen Sie sicher, dass die Interaktionsprotokolle des Werkzeugs einen detaillierten Sicherheitskontext enthalten, einschließlich der Verwendung von Berechtigungen, Datenzugriffsmustern, Ausführungszeit, Ressourcennutzung und Rückgabecodes, mit strukturierter Protokollierung für die SIEM-Integration.        |   2   |  D/V  |
| 9.12.4 | Überprüfen Sie, ob dynamische Werkzeuglade-Mechanismen digitale Signaturen unter Verwendung der PKI-Infrastruktur validieren und sichere Ladeprotokolle mit Sandbox-Isolierung und Berechtigungsverifizierung vor der Ausführung implementieren.                                                                      |   2   |  D/V  |
| 9.12.5 | Stellen Sie sicher, dass Sicherheitsbewertungen von Tools automatisch für neue Versionen ausgelöst werden, mit obligatorischen Genehmigungsschritten, einschließlich statischer Analyse, dynamischer Tests und Überprüfung durch das Sicherheitsteam, mit dokumentierten Genehmigungskriterien und SLA-Anforderungen. |   3   |  D/V  |

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

