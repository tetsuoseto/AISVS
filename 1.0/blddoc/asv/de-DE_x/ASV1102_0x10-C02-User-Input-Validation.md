# C2 Validierung von Benutzereingaben

## Kontrollziel

Robuste Validierung von Benutzereingaben ist eine erste Verteidigungslinie gegen einige der schädlichsten Angriffe auf KI-Systeme. Prompt-Injektionsangriffe können Systemanweisungen außer Kraft setzen, sensible Daten offenlegen oder das Modell auf ein Verhalten lenken, das nicht erlaubt ist. Sofern dedizierte Filter und Instruktionshierarchien vorhanden sind, zeigt die Forschung, dass „Multi-Shot“-Jailbreaks, die sehr langen Kontextfenster ausnutzen, wirksam sein werden. Auch subtile adversariale Perturbationsangriffe – wie Homoglyphen-Tausch oder Leetspeak – können unauffällig die Entscheidungen eines Modells verändern.

---

## C2.1 Verteidigung gegen Prompt-Injektion

Prompt-Injektion ist eines der größten Risiken für KI-Systeme. Abwehrmaßnahmen gegen diese Taktik setzen eine Kombination aus statischen Musterfiltern, dynamischen Klassifikatoren und der Durchsetzung der Anweisungs-Hierarchie ein.

|   #   | Beschreibung                                                                                                                                                                                                                                                                              | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.1.1 | Vergewissern Sie sich, dass Benutzereingaben gegen eine kontinuierlich aktualisierte Bibliothek bekannter Prompt-Injektionsmuster gefiltert werden (Jailbreak-Schlüsselwörter, "ignore previous", Rollenspiel-Ketten, indirekte HTML/URL-Angriffe).                                       |   1   |  D/V  |
| 2.1.2 | Überprüfen Sie, ob das System eine Anweisungshierarchie durchsetzt, in der System- oder Entwicklermeldungen Benutzeranweisungen überschreiben, auch nach der Erweiterung des Kontextfensters.                                                                                             |   1   |  D/V  |
| 2.1.3 | Stellen Sie sicher, dass adversarische Evaluierungstests (z. B. Red-Team „many-shot“-Prompts) vor jeder Veröffentlichung eines Modells oder eines Prompt-Templates durchgeführt werden, mit Schwellenwerten der Erfolgsrate und automatischen Blockern zur Verhinderung von Regressionen. |   2   |  D/V  |
| 2.1.4 | Stellen Sie sicher, dass Prompts, die aus Inhalten Dritter stammen (Webseiten, PDFs, E-Mails), in einem isolierten Parsing-Kontext bereinigt werden, bevor sie in den Hauptprompt zusammengeführt werden.                                                                                 |   2   |   D   |
| 2.1.5 | Stellen Sie sicher, dass alle Aktualisierungen der Prompt-Filter-Regeln, alle Versionen von Klassifikator-Modellen und alle Änderungen der Blockliste versionskontrolliert und auditierbar sind.                                                                                          |   3   |  D/V  |

---

## C2.2 Widerstand gegen adversarische Beispiele

Modelle der Verarbeitung natürlicher Sprache (NLP) sind nach wie vor anfällig für subtile Zeichen- oder Wortebenen-Perturbationen, die Menschen oft übersehen, während die Modelle dazu neigen, sie falsch zu klassifizieren.

|   #   | Beschreibung                                                                                                                                                                                                                | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.2.1 | Überprüfen Sie, dass grundlegende Schritte zur Eingabennormalisierung (Unicode NFC, Homoglyphenabbildung, Leerzeichenbereinigung) vor der Tokenisierung ausgeführt werden.                                                  |   1   |   D   |
| 2.2.2 | Vergewissern Sie sich, dass die statistische Anomalieerkennung Eingaben mit einem ungewöhnlich hohen Editierabstand zu Sprachnormen, übermäßig vielen wiederholten Tokens oder abnormalen Embedding-Distanzen kennzeichnet. |   2   |  D/V  |
| 2.2.3 | Überprüfen Sie, ob die Inferenz-Pipeline optionale adversarial-training–gehärtete Modellvarianten oder Verteidigungsschichten unterstützt (z. B. Randomisierung, defensive Distillation) für Hochrisiko-Endpunkte.          |   2   |   D   |
| 2.2.4 | Stellen Sie sicher, dass verdächtige adversarische Eingaben isoliert werden und mit vollständigen Payloads protokolliert werden (nach PII-Redaktion).                                                                       |   2   |   V   |
| 2.2.5 | Stellen Sie sicher, dass Robustheitsmetriken (Erfolgsquote bekannter Angriffs-Suiten) über die Zeit verfolgt werden und Regressionen einen Release-Blocker auslösen.                                                        |   3   |  D/V  |

---

## C2.3 Schema, Typ- und Längenvalidierung

KI-Angriffe mit fehlerhaften oder übergroßen Eingaben können Parsing-Fehler verursachen, Prompt-Spillage über Felder hinweg auslösen und Ressourcenerschöpfung verursachen.  Strikte Schema-Durchsetzung ist ebenfalls eine Voraussetzung, wenn deterministische Tool-Aufrufe durchgeführt werden.

|   #   | Beschreibung                                                                                                                                                                                                                           | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.3.1 | Stellen Sie sicher, dass jeder API- oder Funktionsaufruf-Endpunkt ein explizites Eingabenschema definiert (JSON-Schema, Protobuf oder multimodale Entsprechung) und dass die Eingaben vor der Erstellung des Prompts validiert werden. |   1   |   D   |
| 2.3.2 | Stellen Sie sicher, dass Eingaben, die die maximalen Token- oder Bytegrenzen überschreiten, mit einer sicheren Fehlermeldung abgewiesen werden und niemals stillschweigend abgeschnitten werden.                                       |   1   |  D/V  |
| 2.3.3 | Stellen Sie sicher, dass Typprüfungen (z. B. numerische Bereiche, Enum-Werte, MIME-Typen für Bilder und Audio) serverseitig durchgesetzt werden und nicht nur im Client-Code.                                                          |   2   |  D/V  |
| 2.3.4 | Stellen Sie sicher, dass semantische Validatoren (z. B. JSON Schema) in konstanter Zeit ausgeführt werden, um einen algorithmischen DoS-Angriff zu verhindern.                                                                         |   2   |   D   |
| 2.3.5 | Stellen Sie sicher, dass Validierungsfehler mit geschwärzten Nutzlastausschnitten und eindeutigen Fehlercodes protokolliert werden, um die Sicherheits-Triage zu unterstützen.                                                         |   3   |   V   |

---

## C2.4 Inhalt und Richtlinienprüfung

Entwickler sollten in der Lage sein, syntaktisch gültige Aufforderungen zu erkennen, die verbotenen Inhalte anfordern (wie illegale Anleitungen, Hassrede und urheberrechtlich geschützte Texte) und sie dann daran zu hindern, sich zu verbreiten.

|   #   | Beschreibung                                                                                                                                                                                                                   | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 2.4.1 | Stellen Sie sicher, dass ein Inhaltsklassifikator (Zero-Shot oder feinabgestimmt) jeden Input auf Gewalt, Selbstverletzung, Hassrede, sexuelle Inhalte und illegale Anfragen bewertet, mit konfigurierbaren Schwellenwerten.   |   1   |   D   |
| 2.4.2 | Stellen Sie sicher, dass Eingaben, die gegen Richtlinien verstoßen, standardisierte Ablehnungen oder sichere Vervollständigungen erhalten, damit sie nicht an nachgelagerte LLM-Aufrufe weitergegeben werden.                  |   1   |  D/V  |
| 2.4.3 | Vergewissern Sie sich, dass das Screening-Modell oder der Regelsatz mindestens quartalsweise neu trainiert oder aktualisiert wird und dabei neu beobachtete Jailbreak- oder Richtlinien-Umgehungsmuster berücksichtigt werden. |   2   |   D   |
| 2.4.4 | Stellen Sie sicher, dass das Screening benutzerspezifische Richtlinien (Alter, regionale Rechtsvorschriften) durch attributbasierte Regeln einhält, die zum Zeitpunkt der Anforderung aufgelöst werden.                        |   2   |   D   |
| 2.4.5 | Verifizieren Sie, dass Screening-Protokolle Konfidenzwerte des Klassifikators und Richtlinienkategorietags enthalten, die für SOC-Korrelation und zukünftige Red-Team-Wiederholungen verwendet werden.                         |   3   |   V   |

---

## C2.5 Eingabe-Ratenbegrenzung und Missbrauchsprävention

Entwickler sollten Missbrauch, Ressourcenerschöpfung und automatisierte Angriffe gegen KI-Systeme verhindern, indem sie die Eingaberaten begrenzen und anomale Nutzungsmuster erkennen.

|   #   | Beschreibung                                                                                                                                               | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.5.1 | Überprüfen Sie, dass pro Benutzer, pro IP und pro API-Schlüssel die Ratenbegrenzungen für alle Eingabe-Endpunkte durchgesetzt werden.                      |   1   |  D/V  |
| 2.5.2 | Überprüfen Sie, ob Burst- und Dauer-Ratenbegrenzungen so abgestimmt sind, dass DoS- und Brute-Force-Angriffe verhindert werden.                            |   2   |  D/V  |
| 2.5.3 | Überprüfen Sie, ob anomale Nutzungsmuster (z. B. Anfragen in schneller Folge, Eingabeüberflutung) automatisierte Blockierungen oder Eskalationen auslösen. |   2   |  D/V  |
| 2.5.4 | Stellen Sie sicher, dass Protokolle zur Missbrauchsprävention aufbewahrt und aufkommende Angriffsformen geprüft werden.                                    |   3   |   V   |

---

## C2.6 Multi-Modal Eingabevalidierung

KI-Systeme sollten eine robuste Validierung von nicht-textuellen Eingaben (Bilder, Audio, Dateien) vorsehen, um Injektion, Umgehung oder Ressourcenmissbrauch zu verhindern.

|   #   | Beschreibung                                                                                                                                       | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.6.1 | Stellen Sie sicher, dass alle Nicht-Text-Eingaben (Bilder, Audiodateien, Dateien) vor der Verarbeitung auf Typ, Größe und Format validiert werden. |   1   |   D   |
| 2.6.2 | Stellen Sie sicher, dass Dateien vor dem Import auf Malware und steganografische Nutzlasten gescannt werden.                                       |   2   |  D/V  |
| 2.6.3 | Überprüfen Sie, dass Bild- und Audioeingaben auf adversariale Perturbationen oder bekannte Angriffsmuster geprüft werden.                          |   2   |  D/V  |
| 2.6.4 | Stellen Sie sicher, dass multimodale Eingabevalidierungsfehler protokolliert werden und Alarme zur Untersuchung auslösen.                          |   3   |   V   |

---

## C2.7 Eingabenherkunft und Attribution

KI-Systeme sollten Auditing, Missbrauchsverfolgung und Compliance unterstützen, indem sie die Herkunft aller Benutzereingaben überwachen und kennzeichnen.

|   #   | Beschreibung                                                                                                                                            | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.7.1 | Überprüfen Sie, ob alle Benutzereingaben bei der Erfassung mit Metadaten (Benutzer-ID, Sitzung, Quelle, Zeitstempel, IP-Adresse) versehen sind.         |   1   |  D/V  |
| 2.7.2 | Überprüfen Sie, ob die Provenienzmetadaten für alle verarbeiteten Eingaben beibehalten und nachprüfbar sind.                                            |   2   |  D/V  |
| 2.7.3 | Stellen Sie sicher, dass anomale oder nicht vertrauenswürdige Eingabequellen markiert und einer verstärkten Prüfung oder Blockierung unterzogen werden. |   2   |  D/V  |

---

## C2.8 Echtzeit-adaptive Bedrohungserkennung

Entwickler sollten fortschrittliche Bedrohungserkennungssysteme für KI einsetzen, die sich an neue Angriffsartenmuster anpassen und Echtzeitschutz mit kompiliertem Musterabgleich bieten.

|   #   | Beschreibung                                                                                                                                                                                                              | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.8.1 | Überprüfen Sie, dass Bedrohungserkennungsmuster in optimierte Regex-Engines kompiliert werden, um eine hochleistungsfähige Echtzeit-Filterung mit minimaler Latenzbelastung zu ermöglichen.                               |   1   |  D/V  |
| 2.8.2 | Überprüfen Sie, ob Bedrohungserkennungssysteme getrennte Musterbibliotheken für verschiedene Bedrohungskategorien pflegen (Prompt-Injektion, schädliche Inhalte, sensible Daten, Systembefehle).                          |   1   |  D/V  |
| 2.8.3 | Vergewissern Sie sich, dass die adaptive Bedrohungserkennung Machine-Learning-Modelle integriert, die die Bedrohungssensitivität basierend auf Angriffsfrequenz und Erfolgsraten aktualisieren.                           |   2   |  D/V  |
| 2.8.4 | Stellen Sie sicher, dass Echtzeit-Bedrohungsintelligenz-Feeds Musterbibliotheken automatisch mit neuen Angriffssignaturen und IOCs (Indikatoren für Kompromittierung) aktualisieren.                                      |   2   |  D/V  |
| 2.8.5 | Verifizieren Sie, dass die Fehlalarmraten bei der Bedrohungserkennung kontinuierlich überwacht werden und die Musterspezifität automatisch angepasst wird, um Beeinträchtigungen legitimer Anwendungsfälle zu minimieren. |   3   |  D/V  |
| 2.8.6 | Stellen Sie sicher, dass kontextbezogene Bedrohungsanalyse die Eingabequelle, Verhaltensmuster des Benutzers und die Sitzungshistorie berücksichtigt, um die Erkennungsgenauigkeit zu verbessern.                         |   3   |  D/V  |
| 2.8.7 | Überprüfen Sie, dass Leistungskennzahlen der Bedrohungserkennung (Erkennungsrate, Verarbeitungslatenz, Ressourcenauslastung) in Echtzeit überwacht und optimiert werden.                                                  |   3   |  D/V  |

---

## C2.9 Multimodale Sicherheitsvalidierungspipeline

Entwickler sollten Sicherheitsvalidierung für Text-, Bild-, Audio- und andere KI-Eingabemodalitäten bereitstellen, einschließlich spezifischer Arten der Bedrohungserkennung und Ressourcenisolierung.

|   #   | Beschreibung                                                                                                                                                                                                                                                                              | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 2.9.1 | Vergewissere dich, dass jede Eingabemodalität über dedizierte Sicherheitsvalidatoren verfügt, die dokumentierte Bedrohungsmuster (Text: Prompt-Injektion, Bilder: Steganografie, Audio: Spektrogramm-Angriffe) sowie Erkennungsschwellen aufweisen.                                       |   1   |  D/V  |
| 2.9.2 | Stellen Sie sicher, dass multimodale Eingaben in isolierten Sandboxen mit festgelegten Ressourcenlimits (Speicher, CPU, Verarbeitungszeit) verarbeitet werden, die jeweils für jeden Modalitätstyp spezifisch festgelegt sind und in Sicherheitsrichtlinien dokumentiert sind.            |   2   |  D/V  |
| 2.9.3 | Überprüfen Sie, dass die Cross-Modal-Angriffserkennung koordinierte Angriffe erkennt, die sich über mehrere Eingabetypen hinweg erstrecken (z. B. steganografische Payloads in Bildern, kombiniert mit Prompt-Injektion im Text) und Korrelationsregeln sowie Alarmgenerierung verwendet. |   2   |  D/V  |
| 2.9.4 | Stellen Sie sicher, dass multimodale Validierungsfehler eine detaillierte Protokollierung auslösen, die alle Eingabemodalitäten, Validierungsergebnisse, Bedrohungsscores und Korrelationsanalysen mit strukturierten Protokollformaten für die SIEM-Integration umfasst.                 |   3   |  D/V  |
| 2.9.5 | Verifizieren Sie, dass modalitätsspezifische Inhaltsklassifizierer gemäß den dokumentierten Zeitplänen (mindestens vierteljährlich) mit neuen Bedrohungsmustern, adversarialen Beispielen und Leistungsbenchmarks aktualisiert werden, die über den Basisgrenzwerten liegen.              |   3   |  D/V  |

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

