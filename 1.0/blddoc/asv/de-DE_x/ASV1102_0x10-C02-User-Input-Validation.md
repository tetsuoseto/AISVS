# C2 Benutzereingabevalidierung

## Kontrollziel

Robuste Validierung von Benutzereingaben ist die erste Verteidigungslinie gegen einige der schädlichsten Angriffe auf KI-Systeme. Prompt-Injection-Angriffe können Systemanweisungen überschreiben, sensible Daten preisgeben oder das Modell zu unerlaubtem Verhalten lenken. Ohne dedizierte Filter und Anweisungshierarchien zeigen Untersuchungen, dass „Multi-Shot“-Jailbreaks, die sehr lange Kontextfenster ausnutzen, wirksam sein werden. Auch subtile adversariale Störangriffe – wie Homoglyphen-Tauschaktionen oder Leetspeak – können die Entscheidungen eines Modells unbemerkt verändern.

---

## C2.1 Schutz vor Prompt-Injektion

Prompt Injection ist eines der größten Risiken für KI-Systeme. Abwehrmaßnahmen gegen diese Taktik verwenden eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und Durchsetzung der Befehlshierarchie.

|   #   | Beschreibung                                                                                                                                                                                                                                                     | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.1.1 | Überprüfen Sie, ob Benutzereingaben gegen eine kontinuierlich aktualisierte Bibliothek bekannter Prompt-Injektion-Muster (Jailbreak-Schlüsselwörter, "ignore previous", Rollenspielketten, indirekte HTML/URL-Angriffe) überprüft werden.                        |   1   |  D/V  |
| 2.1.2 | Überprüfen Sie, ob das System eine Befehls-Hierarchie durchsetzt, bei der System- oder Entwicklernachrichten Benutzeranweisungen überschreiben, selbst nach Erweiterung des Kontextfensters.                                                                     |   1   |  D/V  |
| 2.1.3 | Stellen Sie sicher, dass adversariale Evaluierungstests (z. B. Red Team "Many-Shot"-Prompts) vor jeder Veröffentlichung eines Modells oder Prompt-Templates durchgeführt werden, mit Erfolgsraten-Schwellenwerten und automatisierten Blockern für Regressionen. |   2   |  D/V  |
| 2.1.4 | Verifizieren Sie, dass Eingabeaufforderungen, die aus Inhalten Dritter (Webseiten, PDFs, E-Mails) stammen, in einem isolierten Parsing-Kontext bereinigt werden, bevor sie zum Hauptprompt hinzugefügt werden.                                                   |   2   |   D   |
| 2.1.5 | Verifizieren Sie, dass alle Aktualisierungen der Prompt-Filterregeln, Versionen der Klassifikationsmodelle und Änderungen der Sperrlisten versionskontrolliert und prüfbar sind.                                                                                 |   3   |  D/V  |

---

## C2.2 Widerstandsfähigkeit gegen Adversarial-Beispiele

Modelle der natürlichen Sprachverarbeitung (NLP) sind nach wie vor anfällig für subtile Zeichen- oder Wortebenenstörungen, die Menschen oft übersehen, die von Modellen jedoch häufig falsch klassifiziert werden.

|   #   | Beschreibung                                                                                                                                                                                                       | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 2.2.1 | Stellen Sie sicher, dass grundlegende Schritte der Eingabenormalisierung (Unicode NFC, Homoglyphenabbildung, Abschneiden von Leerzeichen) vor der Tokenisierung ausgeführt werden.                                 |   1   |   D   |
| 2.2.2 | Überprüfen Sie, ob die statistische Anomalieerkennung Eingaben mit ungewöhnlich hoher Editierdistanz zu Sprachnormen, übermäßigen Wiederholungen von Token oder abnormen Einbettungsdistanzen kennzeichnet.        |   2   |  D/V  |
| 2.2.3 | Überprüfen Sie, ob die Inferenzpipeline optionale, adversarial-trainingsgehärtete Modellvarianten oder Verteidigungsschichten (z. B. Randomisierung, defensive Destillation) für Hochrisiko-Endpunkte unterstützt. |   2   |   D   |
| 2.2.4 | Stellen Sie sicher, dass vermutete feindliche Eingaben isoliert, mit vollständigen Payloads (nach der PII-Redaktion) protokolliert werden.                                                                         |   2   |   V   |
| 2.2.5 | Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsrate bekannter Angriffssuites) im Zeitverlauf verfolgt werden und Regressionen eine Freigabesperre auslösen.                                                  |   3   |  D/V  |

---

## C2.3 Schema-, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler, Prompt-Überläufe zwischen Feldern und Ressourcenerschöpfung verursachen. Eine strikte Schemaüberprüfung ist zudem Voraussetzung für die Durchführung deterministischer Tool-Aufrufe.

|   #   | Beschreibung                                                                                                                                                                                                                                        | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.3.1 | Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabe-Schema (JSON Schema, Protobuf oder multimodales Äquivalent) definiert und dass Eingaben vor der Zusammenstellung der Eingabeaufforderung validiert werden. |   1   |   D   |
| 2.3.2 | Überprüfen Sie, dass Eingaben, die die maximalen Token- oder Byte-Grenzen überschreiten, mit einer sicheren Fehlermeldung abgelehnt werden und niemals stillschweigend abgeschnitten werden.                                                        |   1   |  D/V  |
| 2.3.3 | Stellen Sie sicher, dass Typüberprüfungen (z. B. numerische Bereiche, Enum-Werte, MIME-Typen für Bilder/Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.                                                                       |   2   |  D/V  |
| 2.3.4 | Stellen Sie sicher, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um algorithmische DoS-Angriffe zu verhindern.                                                                                            |   2   |   D   |
| 2.3.5 | Stellen Sie sicher, dass Validierungsfehler mit redigierten Nutzlastausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheitsanalyse zu unterstützen.                                                                       |   3   |   V   |

---

## C2.4 Inhalts- und Richtlinienprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Eingabeaufforderungen zu erkennen, die unerlaubte Inhalte anfordern (wie zum Beispiel illegale Anweisungen, Hassrede und urheberrechtlich geschützten Text) und deren Verbreitung zu verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                          | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.4.1 | Stellen Sie sicher, dass ein Inhaltsklassifikator (Zero-Shot oder feinabgestimmt) jede Eingabe hinsichtlich Gewalt, Selbstverletzung, Hass, sexuellen Inhalten und illegalen Anfragen bewertet, mit konfigurierbaren Schwellenwerten. |   1   |   D   |
| 2.4.2 | Stellen Sie sicher, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Abschlüsse erhalten, damit sie nicht an nachgelagerte LLM-Aufrufe weitergeleitet werden.                                 |   1   |  D/V  |
| 2.4.3 | Stellen Sie sicher, dass das Screening-Modell oder die Regelmenge mindestens vierteljährlich neu trainiert/aktualisiert wird, wobei neu beobachtete Jailbreak- oder Richtlinienumgehungsmuster einbezogen werden.                     |   2   |   D   |
| 2.4.4 | Überprüfen Sie, dass das Screening benutzerspezifische Richtlinien (Alter, regionale gesetzliche Beschränkungen) durch attributbasierte Regeln, die zur Anforderungszeit aufgelöst werden, einhält.                                   |   2   |   D   |
| 2.4.5 | Verifizieren Sie, dass Screening-Protokolle Klassifikator-Vertrauenswerte und Richtlinienkategorie-Tags für SOC-Korrelation und zukünftige Red-Team-Wiedergaben enthalten.                                                            |   3   |   V   |

---

## C2.5 Eingabebeschränkung der Datenrate und Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenerschöpfung und automatisierte Angriffe auf KI-Systeme verhindern, indem sie Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

|   #   | Beschreibung                                                                                                                           | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.5.1 | Überprüfen Sie, ob pro Benutzer, pro IP und pro API-Schlüssel Ratenbegrenzungen für alle Eingabeendpunkte durchgesetzt werden.         |   1   |  D/V  |
| 2.5.2 | Überprüfen Sie, ob die Burst- und Dauer-Drosselungsgrenzen so eingestellt sind, dass DoS- und Brute-Force-Angriffe verhindert werden.  |   2   |  D/V  |
| 2.5.3 | Überprüfen Sie, ob anomale Nutzungsmuster (z. B. Rapid-Fire-Anfragen, Input-Fluten) automatisierte Sperren oder Eskalationen auslösen. |   2   |  D/V  |
| 2.5.4 | Stellen Sie sicher, dass Protokolle zur Missbrauchsprävention aufbewahrt und auf neue Angriffsmuster überprüft werden.                 |   3   |   V   |

---

## C2.6 Multi-modale Eingabevalidierung

KI-Systeme sollten eine robuste Validierung für nicht-textuelle Eingaben (Bilder, Audio, Dateien) enthalten, um Injektionen, Umgehungen oder Ressourcenmissbrauch zu verhindern.

|   #   | Beschreibung                                                                                                                                   | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.6.1 | Vergewissern Sie sich, dass alle Nicht-Text-Eingaben (Bilder, Audio, Dateien) vor der Verarbeitung auf Typ, Größe und Format überprüft werden. |   1   |   D   |
| 2.6.2 | Stellen Sie sicher, dass Dateien vor der Verarbeitung auf Malware und steganografische Nutzlasten gescannt werden.                             |   2   |  D/V  |
| 2.6.3 | Verifizieren Sie, dass Bild- und Audioeingaben auf adversariale Störungen oder bekannte Angriffsmuster überprüft werden.                       |   2   |  D/V  |
| 2.6.4 | Überprüfen Sie, ob Fehler bei der Validierung multimodaler Eingaben protokolliert werden und Alarme zur Untersuchung auslösen.                 |   3   |   V   |

---

## C2.7 Eingabeherkunft & Attribution

KI-Systeme sollten Prüfungen, Missbrauchsverfolgung und Compliance unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

|   #   | Beschreibung                                                                                                                                                | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.7.1 | Stellen Sie sicher, dass alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) versehen sind.       |   1   |  D/V  |
| 2.7.2 | Stellen Sie sicher, dass Herkunftsmetadaten für alle verarbeiteten Eingaben erhalten bleiben und prüfbar sind.                                              |   2   |  D/V  |
| 2.7.3 | Stellen Sie sicher, dass anomale oder nicht vertrauenswürdige Eingabequellen markiert und einer verstärkten Überprüfung oder Blockierung unterzogen werden. |   2   |  D/V  |

---

## C2.8 Echtzeit-Adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsmuster anpassen und durch kompiliertes Musterabgleich Echtzeitschutz bieten.

|   #   | Beschreibung                                                                                                                                                                                                                | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.8.1 | Stellen Sie sicher, dass Bedrohungserkennungsmuster in optimierte Regex-Engines kompiliert werden, um eine leistungsstarke Echtzeitfilterung mit minimaler Latenzauswirkung zu gewährleisten.                               |   1   |  D/V  |
| 2.8.2 | Stellen Sie sicher, dass Bedrohungserkennungssysteme separate Musterdatenbanken für verschiedene Bedrohungskategorien (Prompt-Injektion, schädliche Inhalte, sensible Daten, Systembefehle) führen.                         |   1   |  D/V  |
| 2.8.3 | Verifizieren Sie, dass die adaptive Bedrohungserkennung Machine-Learning-Modelle einbezieht, die die Bedrohungsempfindlichkeit basierend auf der Angriffsfrequenz und den Erfolgsraten aktualisieren.                       |   2   |  D/V  |
| 2.8.4 | Überprüfen Sie, ob Echtzeit-Bedrohungsinformationsquellen die Musterdatenbanken automatisch mit neuen Angriffssignaturen und IOCs (Indicators of Compromise) aktualisieren.                                                 |   2   |  D/V  |
| 2.8.5 | Stellen Sie sicher, dass die Fehlalarmraten bei der Bedrohungserkennung kontinuierlich überwacht werden und die Musterspezifität automatisch angepasst wird, um Interferenzen bei legitimen Anwendungsfällen zu minimieren. |   3   |  D/V  |
| 2.8.6 | Verifizieren Sie, dass die kontextuelle Bedrohungsanalyse die Eingabequelle, das Benutzerverhalten und die Sitzungsverlauf berücksichtigt, um die Erkennungsgenauigkeit zu verbessern.                                      |   3   |  D/V  |
| 2.8.7 | Stellen Sie sicher, dass Leistungskennzahlen zur Bedrohungserkennung (Erkennungsrate, Verarbeitungsverzögerung, Ressourcenauslastung) in Echtzeit überwacht und optimiert werden.                                           |   3   |  D/V  |

---

## C2.9 Multi-modale Sicherheitsvalidierungs-Pipeline

Entwickler sollten Sicherheitsvalidierungen für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten mit spezifischen Arten der Bedrohungserkennung und Ressourcenisolierung bereitstellen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                 | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.9.1 | Stellen Sie sicher, dass jede Eingabemodalität über dedizierte Sicherheitsvalidatoren mit dokumentierten Bedrohungsmustern (Text: Prompt-Injektion, Bilder: Steganographie, Audio: Spektrogramm-Angriffe) und Erkennungsschwellen verfügt.                                                   |   1   |  D/V  |
| 2.9.2 | Stellen Sie sicher, dass multimodale Eingaben in isolierten Sandboxes mit definierten Ressourcenbegrenzungen (Speicher, CPU, Verarbeitungszeit) verarbeitet werden, die spezifisch für jeden Modalitätstyp sind und in den Sicherheitsrichtlinien dokumentiert sind.                         |   2   |  D/V  |
| 2.9.3 | Verifizieren Sie, dass die Erkennung von cross-modal Angriffen koordinierte Angriffe über mehrere Eingabetypen hinweg identifiziert (z. B. steganografische Nutzlasten in Bildern kombiniert mit Prompt-Injektionen im Text) durch Korrelationsregeln und die Generierung von Warnmeldungen. |   2   |  D/V  |
| 2.9.4 | Stellen Sie sicher, dass bei multi-modalem Validierungsfehlern eine detaillierte Protokollierung ausgelöst wird, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungswerte und Korrelationsanalysen mit strukturierten Protokollformaten für die SIEM-Integration umfasst.        |   3   |  D/V  |
| 2.9.5 | Stellen Sie sicher, dass modalitätsspezifische Inhaltsklassifikatoren gemäß den dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, gegnerischen Beispielen und Leistungsbenchmarks, die über den Basisschwellenwerten liegen, aktualisiert werden.          |   3   |  D/V  |

---

## Referenzen

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

