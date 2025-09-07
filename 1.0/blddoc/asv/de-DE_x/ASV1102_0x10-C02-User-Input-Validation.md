# C2 Benutzereingabevalidierung

## Kontrollziel

Robuste Validierung von Benutzereingaben ist eine erste Verteidigungslinie gegen einige der schädlichsten Angriffe auf KI-Systeme. Prompt-Injection-Angriffe können Systemanweisungen überschreiben, sensible Daten preisgeben oder das Modell zu unerlaubtem Verhalten lenken. Wenn keine speziellen Filter und Anweisungshierarchien vorhanden sind, zeigen Untersuchungen, dass „Multi-Shot“-Jailbreaks, die sehr lange Kontextfenster ausnutzen, effektiv sein werden. Ebenso können subtile adversarial perturbation attacks – wie Homoglyphentausch oder Leetspeak – die Entscheidungen eines Modells unbemerkt verändern.

---

## C2.1 Abwehr von Prompt-Injektionen

Prompt-Injektion ist eines der größten Risiken für KI-Systeme. Verteidigungsmechanismen gegen diese Taktik verwenden eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und der Durchsetzung von Befehlen in hierarchischer Reihenfolge.

|   #   | Beschreibung                                                                                                                                                                                                                                                    | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.1.1 | Überprüfen Sie, ob Benutzereingaben anhand einer kontinuierlich aktualisierten Bibliothek bekannter Prompt-Injektion-Muster (Jailbreak-Schlüsselwörter, „ignore previous“, Rollenspielketten, indirekte HTML/URL-Angriffe) gefiltert werden.                    |   1    |  D/V  |
| 2.1.2 | Überprüfen Sie, dass das System eine Anweisungs-Hierarchie durchsetzt, bei der System- oder Entwicklernachrichten Benutzeranweisungen überschreiben, selbst nach Erweiterung des Kontextfensters.                                                               |   1    |  D/V  |
| 2.1.3 | Stellen Sie sicher, dass adversariale Evaluierungstests (z. B. Red Team "many-shot" Prompts) vor jeder Veröffentlichung eines Modells oder Prompt-Templates durchgeführt werden, mit Erfolgsraten-Schwellenwerten und automatischen Blockaden bei Regressionen. |   2    |  D/V  |
| 2.1.4 | Stellen Sie sicher, dass Eingabeaufforderungen, die aus Inhalten Dritter (Webseiten, PDFs, E-Mails) stammen, in einem isolierten Parsing-Kontext bereinigt werden, bevor sie in die Hauptaufforderung eingefügt werden.                                         |   2    |   D   |
| 2.1.5 | Stellen Sie sicher, dass alle Aktualisierungen der Prompt-Filterregeln, Versionen der Klassifizierungsmodelle und Änderungen der Sperrlisten versionskontrolliert und prüfbar sind.                                                                             |   3    |  D/V  |

---

## C2.2 Widerstandsfähigkeit gegen adversariale Beispiele

Modelle der natürlichen Sprachverarbeitung (Natural Language Processing, NLP) sind weiterhin anfällig für subtile Zeichen- oder Wort-Ebene-Störungen, die Menschen häufig übersehen, die Modelle jedoch oft falsch klassifizieren.

|   #   | Beschreibung                                                                                                                                                                                                       | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 2.2.1 | Überprüfen Sie, dass grundlegende Eingabe-Normalisierungsschritte (Unicode NFC, Homoglyph-Mapping, Entfernen von Leerzeichen) vor der Tokenisierung durchgeführt werden.                                           |   1    |   D   |
| 2.2.2 | Überprüfen Sie, ob die statistische Anomalieerkennung Eingaben mit ungewöhnlich hoher Editierdistanz zu Sprachnormen, übermäßiger Wiederholung von Tokens oder abnormalen Einbettungsdistanzen kennzeichnet.       |   2    |  D/V  |
| 2.2.3 | Überprüfen Sie, ob die Inferenz-Pipeline optionale adversarial-trainingsgehärtete Modellvarianten oder Verteidigungsschichten (z. B. Randomisierung, defensive Destillation) für Hochrisiko-Endpunkte unterstützt. |   2    |   D   |
| 2.2.4 | Stellen Sie sicher, dass vermutete adversariale Eingaben isoliert, mit vollständigen Nutzdaten (nach PII-Redaktion) protokolliert werden.                                                                          |   2    |   V   |
| 2.2.5 | Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsrate bekannter Angriffssuiten) im Zeitverlauf verfolgt werden und Regressionen einen Release-Blocker auslösen.                                                |   3    |  D/V  |

---

## C2.3 Schema-, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler, Überschreitungen von Aufforderungen über Felder hinweg und Ressourcenerschöpfung verursachen. Eine strikte Durchsetzung des Schemas ist zudem Voraussetzung für die Ausführung deterministischer Werkzeugaufrufe.

|   #   | Beschreibung                                                                                                                                                                                                                                   | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.3.1 | Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabeschema (JSON Schema, Protobuf oder ein multimodales Äquivalent) definiert und dass die Eingaben vor der Zusammenstellung des Prompts validiert werden. |   1    |   D   |
| 2.3.2 | Stellen Sie sicher, dass Eingaben, die die maximalen Token- oder Byte-Grenzen überschreiten, mit einer sicheren Fehlermeldung abgelehnt werden und niemals stillschweigend abgeschnitten werden.                                               |   1    |  D/V  |
| 2.3.3 | Stellen Sie sicher, dass Typprüfungen (z. B. numerische Bereiche, Enum-Werte, MIME-Typen für Bilder/Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.                                                                      |   2    |  D/V  |
| 2.3.4 | Überprüfen Sie, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um algorithmische DoS-Angriffe zu verhindern.                                                                                           |   2    |   D   |
| 2.3.5 | Überprüfen Sie, dass Validierungsfehler mit geschwärzten Nutzdaten-Ausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheitstriage zu unterstützen.                                                                    |   3    |   V   |

---

## C2.4 Inhalts- und Richtlinienüberprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Aufforderungen zu erkennen, die unerlaubte Inhalte anfordern (wie illegale Anweisungen, Hassrede und urheberrechtlich geschützten Text), und dann verhindern, dass diese weiterverbreitet werden.

|   #   | Beschreibung                                                                                                                                                                                                                    | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.4.1 | Überprüfen Sie, ob ein Inhaltsklassifikator (Zero-Shot oder feinabgestimmt) jede Eingabe hinsichtlich Gewalt, Selbstschädigung, Hass, sexuellen Inhalten und illegalen Anfragen bewertet, mit konfigurierbaren Schwellenwerten. |   1    |   D   |
| 2.4.2 | Überprüfen Sie, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Abschlüsse erhalten, damit sie nicht an nachgelagerte LLM-Aufrufe weitergeleitet werden.                               |   1    |  D/V  |
| 2.4.3 | Stellen Sie sicher, dass das Screening-Modell oder Regelwerk mindestens vierteljährlich neu trainiert/aktualisiert wird und dabei neu beobachtete Jailbreak- oder Richtlinienumgehungsmuster berücksichtigt.                    |   2    |   D   |
| 2.4.4 | Stellen Sie sicher, dass die Prüfung benutzerspezifische Richtlinien (Alter, regionale gesetzliche Einschränkungen) durch attributbasierte Regeln respektiert, die zur Anforderungszeit aufgelöst werden.                       |   2    |   D   |
| 2.4.5 | Stellen Sie sicher, dass Screening-Protokolle Klassifikator-Vertrauenswerte und Richtlinienkategorietags für SOC-Korrelation und zukünftige Red-Team-Wiedergaben enthalten.                                                     |   3    |   V   |

---

## C2.5 Eingangsratengrenzung & Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenerschöpfung und automatisierte Angriffe auf KI-Systeme verhindern, indem sie Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

|   #   | Beschreibung                                                                                                                                 | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.5.1 | Überprüfen Sie, ob für alle Eingabeendpunkte benutzerbezogene, IP-bezogene und API-Schlüssel-bezogene Ratenbegrenzungen durchgesetzt werden. |   1    |  D/V  |
| 2.5.2 | Stellen Sie sicher, dass die Burst- und Dauer-Drosselungsraten so eingestellt sind, dass DoS- und Brute-Force-Angriffe verhindert werden.    |   2    |  D/V  |
| 2.5.3 | Überprüfen Sie, ob anomale Nutzungsmuster (z. B. Schnellfeueranfragen, Eingabeflut) automatisierte Sperren oder Eskalationen auslösen.       |   2    |  D/V  |
| 2.5.4 | Stellen Sie sicher, dass Protokolle zur Missbrauchsprävention aufbewahrt und auf aufkommende Angriffsmuster überprüft werden.                |   3    |   V   |

---

## C2.6 Multimodale Eingabevalidierung

KI-Systeme sollten eine robuste Validierung für nicht-textuelle Eingaben (Bilder, Audio, Dateien) enthalten, um Injektionen, Umgehungen oder Ressourcenmissbrauch zu verhindern.

|   #   | Beschreibung                                                                                                                                | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.6.1 | Stellen Sie sicher, dass alle Nicht-Text-Eingaben (Bilder, Audio, Dateien) vor der Verarbeitung auf Typ, Größe und Format überprüft werden. |   1    |   D   |
| 2.6.2 | Stellen Sie sicher, dass Dateien vor der Verarbeitung auf Malware und steganografische Nutzlasten gescannt werden.                          |   2    |  D/V  |
| 2.6.3 | Stellen Sie sicher, dass Bild-/Audioeingaben auf adversarielle Störungen oder bekannte Angriffsmuster überprüft werden.                     |   2    |  D/V  |
| 2.6.4 | Verifizieren Sie, dass Fehler bei der Validierung multimodaler Eingaben protokolliert werden und Alarme zur Untersuchung auslösen.          |   3    |   V   |

---

## C2.7 Eingabeherkunft & Attribution

KI-Systeme sollten die Prüfung, Verfolgung von Missbrauch und Compliance unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

|   #   | Beschreibung                                                                                                                                           | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 2.7.1 | Stellen Sie sicher, dass alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) versehen sind.  |   1    |  D/V  |
| 2.7.2 | Stellen Sie sicher, dass Herkunftsmetadaten für alle verarbeiteten Eingaben erhalten bleiben und überprüfbar sind.                                     |   2    |  D/V  |
| 2.7.3 | Stellen Sie sicher, dass anomale oder nicht vertrauenswürdige Eingabequellen erkannt und einer verstärkten Prüfung oder Blockierung unterzogen werden. |   2    |  D/V  |

---

## C2.8 Echtzeit-Adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsvektoren anpassen und Echtzeitschutz durch kompiliertes Musterabgleichen bieten.

|   #   | Beschreibung                                                                                                                                                                                                             | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 2.8.1 | Überprüfen Sie, ob Bedrohungserkennungsmuster in optimierte reguläre Ausdrucks-Engines kompiliert werden, um eine hochleistungsfähige Echtzeitfilterung mit minimaler Latenzauswirkung zu gewährleisten.                 |   1    |  D/V  |
| 2.8.2 | Stellen Sie sicher, dass Bedrohungserkennungssysteme separate Musterdatenbanken für verschiedene Bedrohungskategorien (Prompt-Injektion, schädliche Inhalte, sensible Daten, Systembefehle) führen.                      |   1    |  D/V  |
| 2.8.3 | Verifizieren Sie, dass die adaptive Bedrohungserkennung maschinelle Lernmodelle integriert, die die Bedrohungssensitivität basierend auf der Angriffsfrequenz und den Erfolgsraten aktualisieren.                        |   2    |  D/V  |
| 2.8.4 | Überprüfen Sie, ob Echtzeit-Bedrohungsdatenfeeds Musterbibliotheken automatisch mit neuen Angriffssignaturen und IOCs (Indikatoren für Kompromittierung) aktualisieren.                                                  |   2    |  D/V  |
| 2.8.5 | Stellen Sie sicher, dass die Fehlalarmrate bei der Bedrohungserkennung kontinuierlich überwacht wird und die Musterspezifität automatisch angepasst wird, um Beeinträchtigungen legitimer Anwendungsfälle zu minimieren. |   3    |  D/V  |
| 2.8.6 | Stellen Sie sicher, dass die kontextbezogene Bedrohungsanalyse die Eingabequelle, das Verhaltensmuster des Benutzers und die Sitzungsverlauf berücksichtigt, um die Erkennungsgenauigkeit zu verbessern.                 |   3    |  D/V  |
| 2.8.7 | Stellen Sie sicher, dass Leistungskennzahlen der Bedrohungserkennung (Erkennungsrate, Verarbeitungsverzögerung, Ressourcennutzung) in Echtzeit überwacht und optimiert werden.                                           |   3    |  D/V  |

---

## C2.9 Multi-Modale Sicherheitsvalidierungspipeline

Entwickler sollten Sicherheitsüberprüfungen für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten mit spezifischen Arten der Bedrohungserkennung und Ressourcentrennung bereitstellen.

|   #   | Beschreibung                                                                                                                                                                                                                                                                                 | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 2.9.1 | Stellen Sie sicher, dass jede Eingabemodalität über dedizierte Sicherheitsvalidatoren mit dokumentierten Bedrohungsmustern (Text: Prompt-Injektion, Bilder: Steganographie, Audio: Spektrogrammangriffe) und Erkennungsschwellen verfügt.                                                    |   1    |  D/V  |
| 2.9.2 | Stellen Sie sicher, dass multimodale Eingaben in isolierten Sandboxes mit definierten Ressourcenbegrenzungen (Speicher, CPU, Verarbeitungszeit) verarbeitet werden, die für jeden Modalitätstyp spezifisch sind und in den Sicherheitsrichtlinien dokumentiert werden.                       |   2    |  D/V  |
| 2.9.3 | Überprüfen Sie, ob die Erkennung von cross-modal Angriffen koordinierte Angriffe identifiziert, die sich über mehrere Eingabetypen erstrecken (z. B. steganografische Nutzlasten in Bildern kombiniert mit Prompt-Injektionen im Text) mithilfe von Korrelationsregeln und Alarmgenerierung. |   2    |  D/V  |
| 2.9.4 | Verifizieren Sie, dass mehrdimensionale Validierungsfehler detaillierte Protokollierungen auslösen, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungswerte und Korrelationsanalysen mit strukturierten Protokollformaten für die SIEM-Integration umfassen.                    |   3    |  D/V  |
| 2.9.5 | Stellen Sie sicher, dass modalitätsspezifische Inhaltsklassifikatoren gemäß dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, adversarialen Beispielen und Leistungsbenchmarks, die über den Basisschwellenwerten liegen, aktualisiert werden.             |   3    |  D/V  |

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

