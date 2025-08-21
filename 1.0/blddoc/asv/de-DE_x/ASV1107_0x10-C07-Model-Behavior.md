# C7 Modellverhalten, Ausgabekontrolle & Sicherheitsgarantie

## Steuerungsziel

Modelloutputs müssen strukturiert, zuverlässig, sicher, erklärbar und im Produktionsbetrieb kontinuierlich überwacht werden. Dadurch werden Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und unkontrollierte Aktionen reduziert, während das Vertrauen der Nutzer und die Einhaltung gesetzlicher Vorschriften erhöht werden.

---

## C7.1 Ausgabeformatdurchsetzung

Strikte Schemata, eingeschränkte Dekodierung und nachgelagerte Validierung verhindern, dass fehlerhafte oder bösartige Inhalte sich ausbreiten.

|   #   | Beschreibung                                                                                                                                                                                                    | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.1.1 | Stellen Sie sicher, dass Antwortschemas (z. B. JSON Schema) im Systemprompt bereitgestellt werden und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben lösen eine Reparatur oder Ablehnung aus. |   1   |  D/V  |
| 7.1.2 | Stellen Sie sicher, dass die eingeschränkte Dekodierung (Stoppzeichen, Regex, Max-Tokens) aktiviert ist, um Überläufe oder Prompt-Injection-Seitenkanäle zu verhindern.                                         |   1   |  D/V  |
| 7.1.3 | Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese gegen Schemata oder injektionssichere Deserialisierer validieren.                                    |   2   |  D/V  |
| 7.1.4 | Überprüfen Sie, dass fehlerhafte Ausgabereignisse protokolliert, mit einer Ratenbegrenzung versehen und im Monitoring angezeigt werden.                                                                         |   3   |   V   |

---

## C7.2 Halluzinationserkennung und -minderung

Unsicherheitsabschätzung und Ausweichstrategien begrenzen erfundene Antworten.

|   #   | Beschreibung                                                                                                                                                                                         | Ebene | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.2.1 | Überprüfen Sie, ob tokenbasierte Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jedem Antwort eine Vertrauensbewertung zuweisen.                  |   1   |  D/V  |
| 7.2.2 | Überprüfen Sie, ob Antworten unterhalb einer konfigurierbaren Vertrauensschwelle Fallback-Workflows auslösen (z. B. retrieval-augmented generation, sekundäres Modell oder menschliche Überprüfung). |   1   |  D/V  |
| 7.2.3 | Stellen Sie sicher, dass Vorfälle von Halluzinationen mit Root-Cause-Metadaten gekennzeichnet und an Post-Mortem- und Feinabstimmungs-Pipelines weitergeleitet werden.                               |   2   |  D/V  |
| 7.2.4 | Stellen Sie sicher, dass Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbank-Updates neu kalibriert werden.                                                                    |   3   |  D/V  |
| 7.2.5 | Überprüfen Sie, ob die Dashboard-Visualisierungen die Halluzinationsraten verfolgen.                                                                                                                 |   3   |   V   |

---

## C7.3 Ausgabe-Sicherheits- und Datenschutzfilterung

Richtlinienfilter und Red-Team-Abdeckung schützen Benutzer und vertrauliche Daten.

|   #   | Beschreibung                                                                                                                                                                                 | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.3.1 | Überprüfen Sie, dass Pre- und Post-Generation-Klassifikatoren Hass, Belästigung, Selbstverletzung, extremistische und sexuell explizite Inhalte, die der Richtlinie entsprechen, blockieren. |   1   |  D/V  |
| 7.3.2 | Überprüfen Sie, dass die Erkennung von PII/PCI und die automatische Schwärzung bei jeder Antwort ausgeführt werden; Verstöße lösen einen Datenschutzvorfall aus.                             |   1   |  D/V  |
| 7.3.3 | Stellen Sie sicher, dass Vertraulichkeitstags (z. B. Geschäftsgeheimnisse) über Modalitäten hinweg übertragen werden, um ein Auslaufen in Text, Bildern oder Code zu verhindern.             |   2   |   D   |
| 7.3.4 | Stellen Sie sicher, dass Versuche zur Umgehung des Filters oder Hochrisikoklassifizierungen eine sekundäre Genehmigung oder eine erneute Benutzerauthentifizierung erfordern.                |   3   |  D/V  |
| 7.3.5 | Überprüfen Sie, ob die Filtergrenzwerte die gesetzlichen Zuständigkeiten sowie den Kontext von Benutzeralter und -rolle widerspiegeln.                                                       |   3   |  D/V  |

---

## C7.4 Ausgabe- und Aktionsbegrenzung

Ratenbegrenzungen und Genehmigungsschranken verhindern Missbrauch und übermäßige Autonomie.

|   #   | Beschreibung                                                                                                                                                                                                   | Ebene | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.4.1 | Überprüfen Sie, dass benutzerbezogene und API-Schlüssel-bezogene Kontingente Anfragen, Token und Kosten mit exponentiellem Back-off bei 429-Fehlern begrenzen.                                                 |   1   |   D   |
| 7.4.2 | Überprüfen Sie, dass privilegierte Aktionen (Dateischreibvorgänge, Codeausführung, Netzwerkanrufe) eine richtlinienbasierte Genehmigung oder eine menschliche Beteiligung erfordern.                           |   1   |  D/V  |
| 7.4.3 | Überprüfen Sie, dass cross-modale Konsistenzprüfungen sicherstellen, dass Bilder, Code und Text, die für dieselbe Anfrage generiert wurden, nicht verwendet werden können, um bösartigen Inhalt zu schmuggeln. |   2   |  D/V  |
| 7.4.4 | Stellen Sie sicher, dass die Tiefe der Agentendelegation, Rekursionsgrenzen und erlaubte Werkzeuglisten explizit konfiguriert sind.                                                                            |   2   |   D   |
| 7.4.5 | Überprüfen Sie, dass die Verletzung von Grenzwerten strukturierte Sicherheitsereignisse für die SIEM-Erfassung aussendet.                                                                                      |   3   |   V   |

---

## C7.5 Ausgabeerklärbarkeit

Transparente Signale verbessern das Vertrauen der Nutzer und die interne Fehlersuche.

|   #   | Beschreibung                                                                                                                                                              | Ebene | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.5.1 | Verifizieren Sie, dass benutzerorientierte Vertrauenswerte oder kurze Begründungszusammenfassungen angezeigt werden, wenn die Risikoabschätzung dies für angemessen hält. |   2   |  D/V  |
| 7.5.2 | Vergewissern Sie sich, dass generierte Erklärungen keine sensiblen Systemanweisungen oder proprietären Daten preisgeben.                                                  |   2   |  D/V  |
| 7.5.3 | Überprüfen Sie, ob das System Token-Ebene Log-Wahrscheinlichkeiten oder Aufmerksamkeitskarten erfasst und diese für autorisierte Prüfungen speichert.                     |   3   |   D   |
| 7.5.4 | Stellen Sie sicher, dass Erklärungsartefakte zusammen mit Modellversionen versioniert werden, um die Nachprüfbarkeit zu gewährleisten.                                    |   3   |   V   |

---

## C7.6 Überwachungsintegration

Echtzeit-Observabilität schließt die Lücke zwischen Entwicklung und Produktion.

|   #   | Beschreibung                                                                                                                                                          | Ebene | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.6.1 | Überprüfen Sie, dass Metriken (Schemaverletzungen, Halluzinationsrate, Toxizität, PII-Lecks, Latenz, Kosten) an eine zentrale Überwachungsplattform gestreamt werden. |   1   |   D   |
| 7.6.2 | Stellen Sie sicher, dass für jede Sicherheitsmetrik Warnschwellen definiert sind, einschließlich Eskalationspfade für Bereitschaftsdienste.                           |   1   |   V   |
| 7.6.3 | Überprüfen Sie, ob Dashboards Ausgabefehler mit Modell/Version, Feature-Flag und Änderungen der vorgelagerten Daten korrelieren.                                      |   2   |   V   |
| 7.6.4 | Stellen Sie sicher, dass Überwachungsdaten in einem dokumentierten MLOps-Workflow in das Retraining, Fine-Tuning oder Regelaktualisierungen zurückfließen.            |   2   |  D/V  |
| 7.6.5 | Stellen Sie sicher, dass Überwachungspipelines einem Penetrationstest unterzogen und zugangskontrolliert sind, um das Auslaufen sensibler Protokolle zu vermeiden.    |   3   |   V   |

---

## 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder unautorisierten Medieninhalte erzeugen, indem Sie Richtlinienbeschränkungen, Ausgabevalidierung und Nachvollziehbarkeit durchsetzen.

|   #   | Beschreibung                                                                                                                                                                                                                        | Ebene | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.7.1 | Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erstellung von illegalen, schädlichen oder nicht einvernehmlichen Deepfake-Medien (z. B. Bild, Video, Audio) verbieten.                      |   1   |  D/V  |
| 7.7.2 | Stellen Sie sicher, dass Eingabeaufforderungen auf Versuche gefiltert werden, Nachahmungen zu erzeugen, sexuell explizite Deepfakes zu erstellen oder Medien darzustellen, die reale Personen ohne deren Zustimmung zeigen.         |   2   |  D/V  |
| 7.7.3 | Überprüfen Sie, ob das System Perceptual Hashing, Wasserzeichenerkennung oder Fingerprinting verwendet, um die unbefugte Vervielfältigung von urheberrechtlich geschütztem Material zu verhindern.                                  |   2   |   V   |
| 7.7.4 | Stellen Sie sicher, dass alle generierten Medien kryptografisch signiert, mit Wasserzeichen versehen oder mit manipulationssicheren Herkunftsmetadaten eingebettet sind, um eine nachgelagerte Rückverfolgbarkeit zu gewährleisten. |   3   |  D/V  |
| 7.7.5 | Stellen Sie sicher, dass Umgehungsversuche (z. B. Prompt-Verschleierung, Slang, adversariale Formulierungen) erkannt, protokolliert und in der Rate begrenzt werden; wiederholter Missbrauch wird an Überwachungssysteme gemeldet.  |   3   |   V   |

## Literaturverzeichnis

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

