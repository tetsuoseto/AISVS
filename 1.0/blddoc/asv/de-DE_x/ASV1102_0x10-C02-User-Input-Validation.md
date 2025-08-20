# C2 Benutzereingabevalidierung

## Kontrollziel

Robuste Validierung von Benutzereingaben ist eine erste Verteidigungslinie gegen einige der schädlichsten Angriffe auf KI-Systeme. Prompt-Injection-Angriffe können Systemanweisungen außer Kraft setzen, sensible Daten offenlegen oder das Modell zu unerlaubtem Verhalten lenken. Sofern keine dedizierten Filter und Anweisungshierarchien vorhanden sind, zeigt die Forschung, dass „Multi-Shot“-Jailbreaks, die sehr lange Kontextfenster ausnutzen, wirksam sein werden. Ebenso können subtile adversariale Störangriffe – wie Homoglyph-Vertauschungen oder Leetspeak – die Entscheidungen eines Modells unbemerkt verändern.

---

## C2.1 Prompt-Injection-Abwehr

Prompt-Injektion ist eines der größten Risiken für KI-Systeme. Abwehrmaßnahmen gegen diese Taktik verwenden eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und der Durchsetzung einer Instruktionshierarchie.

|   #   | Beschreibung                                                                                                                                                                                                                                                       | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 2.1.1 | Überprüfen Sie, dass Benutzereingaben anhand einer kontinuierlich aktualisierten Bibliothek bekannter Prompt-Injektionsmuster (Jailbreak-Stichwörter, „ignore previous“, Rollenspielketten, indirekte HTML/URL-Angriffe) gefiltert werden.                         |   1   |  D/V  |
| 2.1.2 | Verifizieren Sie, dass das System eine Anweisungs-Hierarchie durchsetzt, bei der System- oder Entwicklernachrichten Benutzeranweisungen übersteuern, auch nach Erweiterung des Kontextfensters.                                                                    |   1   |  D/V  |
| 2.1.3 | Stellen Sie sicher, dass adversariale Bewertungstests (z. B. Red Team „Many-Shot“-Prompts) vor jeder Veröffentlichung eines Modells oder einer Prompt-Vorlage durchgeführt werden, mit Erfolgsraten-Schwellenwerten und automatisierten Blockern für Regressionen. |   2   |  D/V  |
| 2.1.4 | Stellen Sie sicher, dass Eingabeaufforderungen, die aus Inhalten Dritter stammen (Webseiten, PDFs, E-Mails), in einem isolierten Parsing-Kontext bereinigt werden, bevor sie in die Haupt-Eingabeaufforderung zusammengeführt werden.                              |   2   |   D   |
| 2.1.5 | Stellen Sie sicher, dass alle Aktualisierungen der Prompt-Filterregeln, Versionen der Klassifizierer-Modelle und Änderungen der Sperrlisten versionskontrolliert und prüfbar sind.                                                                                 |   3   |  D/V  |

---

## C2.2 Widerstandsfähigkeit gegen adversariale Beispiele

Modelle der natürlichen Sprachverarbeitung (Natural Language Processing, NLP) sind weiterhin anfällig für subtile Störungen auf Zeichen- oder Wortebene, die Menschen oft übersehen, die Modelle jedoch typischerweise falsch klassifizieren.

|   #   | Beschreibung                                                                                                                                                                                                        | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.2.1 | Stellen Sie sicher, dass grundlegende Eingabenormalisierungsschritte (Unicode NFC, Homoglyphen-Zuordnung, Entfernen von Leerzeichen) vor der Tokenisierung ausgeführt werden.                                       |   1   |   D   |
| 2.2.2 | Überprüfen Sie, ob die statistische Anomalieerkennung Eingaben mit ungewöhnlich hoher Editierdistanz zu Sprachnormen, übermäßiger Wiederholung von Token oder abnormalen Einbettungsabständen markiert.             |   2   |  D/V  |
| 2.2.3 | Überprüfen Sie, ob die Inferenz-Pipeline optionale gegnerische Trainings-härtete Modellvarianten oder Verteidigungsschichten (z. B. Randomisierung, defensive Destillation) für hochriskante Endpunkte unterstützt. |   2   |   D   |
| 2.2.4 | Stellen Sie sicher, dass verdächtige adversariale Eingaben isoliert, mit vollständigen Nutzdaten protokolliert (nach PII-Redaktion) werden.                                                                         |   2   |   V   |
| 2.2.5 | Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsrate bekannter Angriffssuites) im Zeitverlauf verfolgt werden und Regressionen einen Veröffentlichungsblocker auslösen.                                        |   3   |  D/V  |

---

## C2.3 Schema-, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler, Überlaufen von Eingaben über Felder hinweg und Ressourcenerschöpfung verursachen. Eine strikte Schemaüberprüfung ist zudem eine Voraussetzung für die Durchführung deterministischer Werkzeugaufrufe.

|   #   | Beschreibung                                                                                                                                                                                                                           | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.3.1 | Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabeschema (JSON Schema, Protobuf oder multimodales Äquivalent) definiert und dass Eingaben vor der Zusammenstellung des Prompts validiert werden. |   1   |   D   |
| 2.3.2 | Stellen Sie sicher, dass Eingaben, die die maximalen Token- oder Byte-Grenzen überschreiten, mit einem sicheren Fehler abgelehnt werden und niemals stillschweigend abgeschnitten werden.                                              |   1   |  D/V  |
| 2.3.3 | Stellen Sie sicher, dass Typüberprüfungen (z. B. numerische Bereiche, Enum-Werte, MIME-Typen für Bilder/Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.                                                          |   2   |  D/V  |
| 2.3.4 | Stellen Sie sicher, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um algorithmische DoS-Angriffe zu verhindern.                                                                               |   2   |   D   |
| 2.3.5 | Stellen Sie sicher, dass Validierungsfehler mit anonymisierten Nutzlast-Ausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheitsbewertung zu erleichtern.                                                     |   3   |   V   |

---

## C2.4 Inhalt- und Richtlinienüberprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Aufforderungen zu erkennen, die verbotene Inhalte anfordern (wie etwa illegale Anweisungen, Hassrede und urheberrechtlich geschützten Text), und deren Verbreitung verhindern.

|   #   | Beschreibung                                                                                                                                                                                                                           | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.4.1 | Stellen Sie sicher, dass ein Inhaltsklassifizierer (Zero-Shot oder feinabgestimmt) jede Eingabe hinsichtlich Gewalt, Selbstverletzung, Hass, sexuellen Inhalten und illegalen Anfragen bewertet, mit konfigurierbaren Schwellenwerten. |   1   |   D   |
| 2.4.2 | Stellen Sie sicher, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Abschlüsse erhalten, damit sie nicht an nachgelagerte LLM-Aufrufe weitergeleitet werden.                                  |   1   |  D/V  |
| 2.4.3 | Stellen Sie sicher, dass das Screening-Modell oder Regelwerk mindestens vierteljährlich neu trainiert/aktualisiert wird, wobei neu beobachtete Jailbreak- oder Umgehungsmuster von Richtlinien einbezogen werden.                      |   2   |   D   |
| 2.4.4 | Überprüfen Sie, ob das Screening benutzerspezifische Richtlinien (Alter, regionale gesetzliche Einschränkungen) mittels attributbasierter Regeln, die zur Anfragezeit aufgelöst werden, einhält.                                       |   2   |   D   |
| 2.4.5 | Stellen Sie sicher, dass Screening-Protokolle Klassifikator-Vertrauenswerte und Richtlinienkategorie-Tags für die SOC-Korrelation und zukünftige Red-Team-Wiederholungen enthalten.                                                    |   3   |   V   |

---

## C2.5 Eingangsratebegrenzung & Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenauslastung und automatisierte Angriffe auf KI-Systeme verhindern, indem sie Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

|   #   | Beschreibung                                                                                                                           | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.5.1 | Überprüfen Sie, ob für alle Eingabe-Endpunkte Benutzer-, IP- und API-Schlüssel-spezifische Ratenbegrenzungen durchgesetzt werden.      |   1   |  D/V  |
| 2.5.2 | Überprüfen Sie, ob die Burst- und Dauerbetragsgrenzen so eingestellt sind, dass DoS- und Brute-Force-Angriffe verhindert werden.       |   2   |  D/V  |
| 2.5.3 | Überprüfen Sie, ob anomale Nutzungsmuster (z. B. Schnellfeueranfragen, Eingabeflut) automatisierte Sperren oder Eskalationen auslösen. |   2   |  D/V  |
| 2.5.4 | Überprüfen Sie, ob Protokolle zur Missbrauchsverhinderung aufbewahrt und auf aufkommende Angriffsmuster überprüft werden.              |   3   |   V   |

---

## C2.6 Mehrmodale Eingabevalidierung

KI-Systeme sollten eine robuste Validierung für nicht-textuelle Eingaben (Bilder, Audio, Dateien) enthalten, um Injektion, Umgehung oder Ressourcenmissbrauch zu verhindern.

|   #   | Beschreibung                                                                                                                                | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.6.1 | Stellen Sie sicher, dass alle Nicht-Text-Eingaben (Bilder, Audio, Dateien) vor der Verarbeitung auf Typ, Größe und Format validiert werden. |   1   |   D   |
| 2.6.2 | Stellen Sie sicher, dass Dateien vor der Verarbeitung auf Malware und steganographische Nutzlasten gescannt werden.                         |   2   |  D/V  |
| 2.6.3 | Überprüfen Sie, ob Bild-/Audioeingaben auf adversarielle Störungen oder bekannte Angriffs-muster geprüft werden.                            |   2   |  D/V  |
| 2.6.4 | Stellen Sie sicher, dass Validierungsfehler bei multimodalen Eingaben protokolliert werden und Warnmeldungen zur Untersuchung auslösen.     |   3   |   V   |

---

## C2.7 Eingabeherkunft und Attribution

KI-Systeme sollten die Prüfung, die Verfolgung von Missbrauch und die Einhaltung von Vorschriften unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

|   #   | Beschreibung                                                                                                                                             | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.7.1 | Überprüfen Sie, ob alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) versehen sind.          |   1   |  D/V  |
| 2.7.2 | Stellen Sie sicher, dass Herkunftsmetadaten für alle verarbeiteten Eingaben erhalten bleiben und prüfbar sind.                                           |   2   |  D/V  |
| 2.7.3 | Stellen Sie sicher, dass anomale oder nicht vertrauenswürdige Eingabequellen markiert und einer verstärkten Überprüfung oder Sperrung unterzogen werden. |   2   |  D/V  |

---

## C2.8 Echtzeit-Adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsarten anpassen und durch kompilierte Mustererkennung Echtzeitschutz bieten.

|   #   | Beschreibung                                                                                                                                                                                               | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.8.1 | Stellen Sie sicher, dass Bedrohungserkennungsmuster in optimierte Regex-Engines kompiliert werden, um eine hochleistungsfähige Echtzeitfilterung mit minimaler Latenzauswirkung zu gewährleisten.          |   1   |  D/V  |
| 2.8.2 | Überprüfen Sie, ob Bedrohungserkennungssysteme separate Musterbibliotheken für verschiedene Bedrohungskategorien (Prompt-Injektion, schädliche Inhalte, sensible Daten, Systembefehle) unterhalten.        |   1   |  D/V  |
| 2.8.3 | Überprüfen Sie, ob die adaptive Bedrohungserkennung Machine-Learning-Modelle integriert, die die Bedrohungsempfindlichkeit basierend auf der Angriffsfrequenz und den Erfolgsraten aktualisieren.          |   2   |  D/V  |
| 2.8.4 | Überprüfen Sie, ob Echtzeit-Bedrohungsintelligenz-Feeds Musterbibliotheken automatisch mit neuen Angriffssignaturen und IOC (Indicators of Compromise) aktualisieren.                                      |   2   |  D/V  |
| 2.8.5 | Stellen Sie sicher, dass die Fehlalarme der Bedrohungserkennung kontinuierlich überwacht werden und die Musterspezifität automatisch angepasst wird, um Störungen legitimer Anwendungsfälle zu minimieren. |   3   |  D/V  |
| 2.8.6 | Überprüfen Sie, dass die kontextbezogene Bedrohungsanalyse die Eingabequelle, Benutzerverhaltensmuster und Sitzungsverlauf berücksichtigt, um die Genauigkeit der Erkennung zu verbessern.                 |   3   |  D/V  |
| 2.8.7 | Stellen Sie sicher, dass Leistungskennzahlen der Bedrohungserkennung (Erkennungsrate, Verarbeitungsverzögerung, Ressourcenauslastung) in Echtzeit überwacht und optimiert werden.                          |   3   |  D/V  |

---

## C2.9 Multi-modale Sicherheitsvalidierungspipeline

Entwickler sollten Sicherheitsvalidierungen für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten mit spezifischen Arten der Bedrohungserkennung und Ressourcenisolierung bereitstellen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                       | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.9.1 | Stellen Sie sicher, dass jede Eingabemodalität über dedizierte Sicherheitsvalidatoren mit dokumentierten Bedrohungsmustern (Text: Prompt-Injektion, Bilder: Steganographie, Audio: Spektrogramm-Angriffe) und Erkennungsschwellen verfügt.                                         |   1   |  D/V  |
| 2.9.2 | Stellen Sie sicher, dass multimodale Eingaben in isolierten Sandboxes mit definierten Ressourcenbegrenzungen (Speicher, CPU, Verarbeitungszeit), die für jeden Modultyp spezifisch sind, verarbeitet werden und in den Sicherheitsrichtlinien dokumentiert sind.                   |   2   |  D/V  |
| 2.9.3 | Überprüfen Sie, ob die Erkennung von Cross-Modal-Angriffen koordinierte Angriffe erfasst, die mehrere Eingabetypen umfassen (z. B. steganografische Nutzlasten in Bildern kombiniert mit Prompt-Injektion im Text) mithilfe von Korrelationsregeln und Alarmgenerierung.           |   2   |  D/V  |
| 2.9.4 | Verifizieren Sie, dass Multi-Modal-Validierungsfehler eine detaillierte Protokollierung auslösen, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungsscores und Korrelationsanalysen mit strukturierten Protokollformaten zur SIEM-Integration umfasst.                |   3   |  D/V  |
| 2.9.5 | Stellen Sie sicher, dass modalitiespezifische Inhaltsklassifikatoren gemäß den dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, adversarialen Beispielen und Leistungskennzahlen aktualisiert werden, die über den Basisschwellenwerten liegen. |   3   |  D/V  |

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

