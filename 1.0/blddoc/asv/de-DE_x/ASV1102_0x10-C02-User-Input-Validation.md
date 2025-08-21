# C2 Benutzer-Eingabevalidierung

## Steuerungsziel

Robuste Validierung von Benutzereingaben ist eine Erstlinientaktik zum Schutz vor einigen der schädlichsten Angriffe auf KI-Systeme. Prompt-Injection-Angriffe können Systemanweisungen überschreiben, sensible Daten offenlegen oder das Modell zu unerlaubtem Verhalten lenken. Ohne spezielle Filter und hierarchische Anweisungen zeigen Forschungen, dass „Multi-Shot“-Jailbreaks, die sehr lange Kontextfenster ausnutzen, effektiv sein werden. Ebenso können subtile adversariale Störangriffe – wie Homoglyph-Tausch oder Leetspeak – die Entscheidungen eines Modells unauffällig verändern.

---

## C2.1 Abwehr von Prompt-Injektionen

Prompt Injection ist eines der größten Risiken für KI-Systeme. Abwehrmaßnahmen gegen diese Taktik setzen eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und Durchsetzung der Anweisungshierarchie ein.

|   #   | Beschreibung                                                                                                                                                                                                                                      | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.1.1 | Überprüfen Sie, ob Benutzereingaben gegen eine kontinuierlich aktualisierte Bibliothek bekannter Prompt-Injektionsmuster (Jailbreak-Stichwörter, "ignore previous", Rollenspielketten, indirekte HTML/URL-Angriffe) gefiltert werden.             |   1   |  D/V  |
| 2.1.2 | Stellen Sie sicher, dass das System eine Anweisungs-Hierarchie durchsetzt, bei der System- oder Entwicklernachrichten Benutzeranweisungen überstimmen, selbst nach Erweiterung des Kontextfensters.                                               |   1   |  D/V  |
| 2.1.3 | Stellen Sie sicher, dass adversarielle Evaluationstests (z. B. Red Team "many-shot"-Prompts) vor jeder Modell- oder Prompt-Template-Freigabe durchgeführt werden, mit Erfolgsraten-Schwellenwerten und automatisierten Blockern für Rückschritte. |   2   |  D/V  |
| 2.1.4 | Überprüfen Sie, ob Eingabeaufforderungen, die aus Inhalten Dritter (Webseiten, PDFs, E-Mails) stammen, in einem isolierten Analysekontext bereinigt werden, bevor sie in die Hauptaufforderung eingefügt werden.                                  |   2   |   D   |
| 2.1.5 | Stellen Sie sicher, dass alle Aktualisierungen der Prompt-Filter-Regeln, Versionen der Klassifizierungsmodelle und Änderungen an der Blockliste versionskontrolliert und prüfbar sind.                                                            |   3   |  D/V  |

---

## C2.2 Widerstandsfähigkeit gegen adversariale Beispiele

Modelle der natürlichen Sprachverarbeitung (NLP) sind weiterhin anfällig für subtile Störungen auf Zeichen- oder Wortebene, die Menschen häufig übersehen, aber von den Modellen oft falsch klassifiziert werden.

|   #   | Beschreibung                                                                                                                                                                                                                    | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.2.1 | Stellen Sie sicher, dass grundlegende Eingabenormalisierungsschritte (Unicode NFC, Homoglyph-Mapping, Entfernen von Leerzeichen) vor der Tokenisierung ausgeführt werden.                                                       |   1   |   D   |
| 2.2.2 | Stellen Sie sicher, dass die statistische Anomalieerkennung Eingaben mit ungewöhnlich hoher Editierdistanz zu Sprachnormen, übermäßigen wiederholten Token oder abnormen Einbettungsdistanzen kennzeichnet.                     |   2   |  D/V  |
| 2.2.3 | Verifizieren Sie, dass die Inferenz-Pipeline optionale, durch adversariales Training gehärtete Modellvarianten oder Verteidigungsschichten (z. B. Randomisierung, defensive Distillation) für Hochrisiko-Endpunkte unterstützt. |   2   |   D   |
| 2.2.4 | Verifizieren Sie, dass vermutete adversariale Eingaben isoliert, mit vollständigen Nutzdaten (nach PII-Redaktion) protokolliert werden.                                                                                         |   2   |   V   |
| 2.2.5 | Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsrate bekannter Angriffssuites) im Zeitverlauf verfolgt werden und Regressionen einen Release-Blocker auslösen.                                                             |   3   |  D/V  |

---

## C2.3 Schema-, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler, Überlaufen von Eingaben über Felder hinweg und Ressourcenerschöpfung verursachen. Strikte Schemaüberprüfung ist ebenfalls eine Voraussetzung für die Durchführung deterministischer Werkzeugaufrufe.

|   #   | Beschreibung                                                                                                                                                                                                                      | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.3.1 | Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabeschema (JSON Schema, Protobuf oder multimodales Äquivalent) definiert und dass Eingaben vor der Prompt-Zusammenstellung validiert werden. |   1   |   D   |
| 2.3.2 | Stellen Sie sicher, dass Eingaben, die die maximalen Token- oder Byte-Grenzen überschreiten, mit einem sicheren Fehler abgelehnt werden und niemals stillschweigend abgeschnitten werden.                                         |   1   |  D/V  |
| 2.3.3 | Stellen Sie sicher, dass Typüberprüfungen (z. B. numerische Bereiche, Enumerationswerte, MIME-Typen für Bilder/Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.                                              |   2   |  D/V  |
| 2.3.4 | Stellen Sie sicher, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um algorithmische DoS-Angriffe zu verhindern.                                                                          |   2   |   D   |
| 2.3.5 | Stellen Sie sicher, dass Validierungsfehler mit geschwärzten Nutzlastausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheitstriangulation zu unterstützen.                                              |   3   |   V   |

---

## C2.4 Inhalts- und Richtlinienprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Eingabeaufforderungen zu erkennen, die unzulässige Inhalte anfordern (wie illegale Anweisungen, Hassrede und urheberrechtlich geschützten Text), und diese daran hindern, weiterverbreitet zu werden.

|   #   | Beschreibung                                                                                                                                                                                                                        | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.4.1 | Stellen Sie sicher, dass ein Inhaltsklassifikator (Zero-Shot oder feinjustiert) jede Eingabe hinsichtlich Gewalt, Selbstverletzung, Hass, sexuellen Inhalten und illegalen Anfragen bewertet, mit konfigurierbaren Schwellenwerten. |   1   |   D   |
| 2.4.2 | Stellen Sie sicher, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Abschlüsse erhalten, sodass sie nicht an nachgelagerte LLM-Aufrufe weitergegeben werden.                               |   1   |  D/V  |
| 2.4.3 | Stellen Sie sicher, dass das Screening-Modell oder Regelwerk mindestens vierteljährlich neu trainiert/aktualisiert wird und dabei neu beobachtete Jailbreak- oder Richtlinienumgehungsmuster einbezieht.                            |   2   |   D   |
| 2.4.4 | Überprüfen Sie, dass das Screening benutzerspezifische Richtlinien (Alter, regionale gesetzliche Beschränkungen) durch attributbasierte Regeln einhält, die zur Anforderungszeit aufgelöst werden.                                  |   2   |   D   |
| 2.4.5 | Überprüfen Sie, ob die Screening-Protokolle Klassifikator-Vertrauenswerte und Richtlinienkategorie-Tags für SOC-Korrelation und zukünftige Red-Team-Wiederholungen enthalten.                                                       |   3   |   V   |

---

## C2.5 Eingangsratebegrenzung und Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenerschöpfung und automatisierte Angriffe auf KI-Systeme verhindern, indem sie die Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

|   #   | Beschreibung                                                                                                                                     | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 2.5.1 | Überprüfen Sie, ob die Grenzwerte für Anfragen pro Benutzer, pro IP und pro API-Schlüssel für alle Eingabe-Endpunkte durchgesetzt werden.        |   1   |  D/V  |
| 2.5.2 | Stellen Sie sicher, dass die Burst- und anhaltenden Ratenbegrenzungen so eingestellt sind, dass DoS- und Brute-Force-Angriffe verhindert werden. |   2   |  D/V  |
| 2.5.3 | Stellen Sie sicher, dass anomale Nutzungsmuster (z. B. Schnellfeueranfragen, Eingabeflutung) automatisierte Sperren oder Eskalationen auslösen.  |   2   |  D/V  |
| 2.5.4 | Überprüfen Sie, ob Protokolle zur Missbrauchsprävention aufbewahrt und auf aufkommende Angriffsmuster überprüft werden.                          |   3   |   V   |

---

## C2.6 Multi-modale Eingabevalidierung

KI-Systeme sollten eine robuste Validierung für nicht-textuelle Eingaben (Bilder, Audio, Dateien) enthalten, um Injektionen, Umgehungen oder Ressourcenmissbrauch zu verhindern.

|   #   | Beschreibung                                                                                                                                 | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.6.1 | Stellen Sie sicher, dass alle Nicht-Text-Eingaben (Bilder, Audio, Dateien) vor der Verarbeitung auf Typ, Größe und Format überprüft werden.  |   1   |   D   |
| 2.6.2 | Stellen Sie sicher, dass Dateien vor der Verarbeitung auf Malware und steganographische Nutzlasten gescannt werden.                          |   2   |  D/V  |
| 2.6.3 | Stellen Sie sicher, dass Bild-/Audioeingaben auf feindliche Störungen oder bekannte Angriffsmuster überprüft werden.                         |   2   |  D/V  |
| 2.6.4 | Stellen Sie sicher, dass fehlerhafte Eingaben bei multimodaler Validierung protokolliert werden und Warnmeldungen zur Untersuchung auslösen. |   3   |   V   |

---

## C2.7 Eingabeherkunft & Zuschreibung

KI-Systeme sollten die Prüfung, Nachverfolgung von Missbrauch und Einhaltung von Vorschriften unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

|   #   | Beschreibung                                                                                                                                                | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.7.1 | Stellen Sie sicher, dass alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) gekennzeichnet sind. |   1   |  D/V  |
| 2.7.2 | Stellen Sie sicher, dass Herkunftsmetadaten für alle verarbeiteten Eingaben beibehalten und prüfbar sind.                                                   |   2   |  D/V  |
| 2.7.3 | Überprüfen Sie, ob anomale oder nicht vertrauenswürdige Eingabequellen markiert und einer verstärkten Prüfung oder Sperrung unterzogen werden.              |   2   |  D/V  |

---

## C2.8 Echtzeit-Adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsverfahren anpassen und mit kompiliertem Musterabgleich Echtzeitschutz bieten.

|   #   | Beschreibung                                                                                                                                                                                                    | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.8.1 | Stellen Sie sicher, dass Bedrohungserkennungsmuster in optimierte Regex-Engines kompiliert werden, um eine leistungsstarke Echtzeitfilterung mit minimaler Latenzauswirkung zu gewährleisten.                   |   1   |  D/V  |
| 2.8.2 | Überprüfen Sie, dass Bedrohungserkennungssysteme separate Musterbibliotheken für verschiedene Bedrohungskategorien (Prompt-Injektion, schädliche Inhalte, vertrauliche Daten, Systembefehle) verwalten.         |   1   |  D/V  |
| 2.8.3 | Überprüfen Sie, ob die adaptive Bedrohungserkennung Machine-Learning-Modelle beinhaltet, die die Bedrohungsempfindlichkeit basierend auf der Angriffsfrequenz und den Erfolgsraten aktualisieren.               |   2   |  D/V  |
| 2.8.4 | Stellen Sie sicher, dass Echtzeit-Bedrohungsinformationsquellen die Musterbibliotheken automatisch mit neuen Angriffs-Signaturen und IOCs (Indikatoren für Kompromittierung) aktualisieren.                     |   2   |  D/V  |
| 2.8.5 | Stellen Sie sicher, dass die Fehlalarmrate bei der Bedrohungserkennung kontinuierlich überwacht wird und die Musterspezifität automatisch angepasst wird, um Störungen legitimer Anwendungsfälle zu minimieren. |   3   |  D/V  |
| 2.8.6 | Überprüfen Sie, ob die kontextbezogene Bedrohungsanalyse die Eingabequelle, das Benutzerverhaltensmuster und die Sitzungsverlauf berücksichtigt, um die Erkennungsgenauigkeit zu verbessern.                    |   3   |  D/V  |
| 2.8.7 | Stellen Sie sicher, dass die Leistungskennzahlen der Bedrohungserkennung (Erkennungsrate, Verarbeitungsverzögerung, Ressourcennutzung) in Echtzeit überwacht und optimiert werden.                              |   3   |  D/V  |

---

## C2.9 Multi-Modale Sicherheitsvalidierungspipeline

Entwickler sollten Sicherheitsvalidierungen für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten mit spezifischen Bedrohungserkennungstypen und Ressourcenisolation bereitstellen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                         | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 2.9.1 | Überprüfen Sie, dass jede Eingabemodalität dedizierte Sicherheit-Validatoren mit dokumentierten Bedrohungsmustern (Text: Prompt Injection, Bilder: Steganographie, Audio: Spektrogramm-Angriffe) und Erkennungsschwellenwerten besitzt.                                              |   1   |  D/V  |
| 2.9.2 | Stellen Sie sicher, dass multi-modale Eingaben in isolierten Sandboxes mit definierten Ressourcenbeschränkungen (Speicher, CPU, Verarbeitungszeit), die für jeden Modalitätstyp spezifisch sind, verarbeitet werden und in den Sicherheitsrichtlinien dokumentiert sind.             |   2   |  D/V  |
| 2.9.3 | Überprüfen Sie, ob die Erkennung von cross-modalen Angriffen koordinierte Angriffe über mehrere Eingabetypen hinweg identifiziert (z. B. steganografische Nutzlasten in Bildern kombiniert mit Prompt-Injektion im Text) durch Korrelationsregeln und Alarmgenerierung.              |   2   |  D/V  |
| 2.9.4 | Verifizieren Sie, dass Validierungsfehler bei Multi-Modalität eine detaillierte Protokollierung auslösen, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungsbewertungen und Korrelationsanalysen mit strukturierten Protokollformaten für die SIEM-Integration umfasst. |   3   |  D/V  |
| 2.9.5 | Überprüfen Sie, ob modalitätsspezifische Inhaltsklassifikatoren gemäß den dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, adversarialen Beispielen und Leistungsbenchmarks, die über den Mindestanforderungen liegen, aktualisiert werden.       |   3   |  D/V  |

---

## Literaturverzeichnis

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

