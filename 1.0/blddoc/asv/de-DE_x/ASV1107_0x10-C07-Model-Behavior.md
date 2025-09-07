# C7 Modellverhalten, Ausgabe Steuerung & Sicherheitsgarantie

## Kontrollziel

Modelausgaben müssen strukturiert, zuverlässig, sicher, erklärbar und kontinuierlich in der Produktion überwacht werden. Dadurch werden Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und unkontrollierte Aktionen reduziert, während das Vertrauen der Nutzer und die Einhaltung von Vorschriften erhöht werden.

---

## C7.1 Durchsetzung des Ausgabeformats

Strenge Schemata, eingeschränkte Decodierung und nachgelagerte Validierung verhindern, dass fehlerhafte oder bösartige Inhalte sich ausbreiten.

|   #   | Beschreibung                                                                                                                                                                                               | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.1.1 | Stellen Sie sicher, dass Antwortschemata (z. B. JSON-Schema) im System-Prompt angegeben sind und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben lösen eine Reparatur oder Ablehnung aus. |   1    |  D/V  |
| 7.1.2 | Stellen Sie sicher, dass das eingeschränkte Decodieren (Stoppzeichen, Regex, Maximalanzahl an Tokens) aktiviert ist, um Overflow- oder Prompt-Injection-Seitenkanäle zu verhindern.                        |   1    |  D/V  |
| 7.1.3 | Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese gegen Schemata oder injektionssichere Deserialisierer validieren.                               |   2    |  D/V  |
| 7.1.4 | Überprüfen Sie, dass falsche Ausgabeereignisse protokolliert, mit einer Ratenbegrenzung versehen und im Monitoring sichtbar gemacht werden.                                                                |   3    |   V   |

---

## C7.2 Halluzinationserkennung und -minderung

Unsicherheitsabschätzung und Fallback-Strategien begrenzen erfundene Antworten.

|   #   | Beschreibung                                                                                                                                                                                                | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.2.1 | Verifizieren Sie, dass Token-Level-Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jedem Antwort eine Konfidenzbewertung zuweisen.                        |   1    |  D/V  |
| 7.2.2 | Verifizieren Sie, dass Antworten unterhalb eines konfigurierbaren Vertrauensschwellenwerts Rückfall-Workflows auslösen (z. B. retrieval-augmented Generation, sekundäres Modell oder manuelle Überprüfung). |   1    |  D/V  |
| 7.2.3 | Stellen Sie sicher, dass Halluzinationsvorfälle mit Root-Cause-Metadaten gekennzeichnet und an Post-Mortem- und Feinabstimmungspipelines weitergeleitet werden.                                             |   2    |  D/V  |
| 7.2.4 | Stellen Sie sicher, dass Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbank-Updates neu kalibriert werden.                                                                           |   3    |  D/V  |
| 7.2.5 | Überprüfen Sie, ob die Dashboard-Visualisierungen die Halluzinationsraten verfolgen.                                                                                                                        |   3    |   V   |

---

## C7.3 Ausgabe-Sicherheits- und Datenschutzfilterung

Richtlinienfilter und Red-Team-Abdeckung schützen Benutzer und vertrauliche Daten.

|   #   | Beschreibung                                                                                                                                                                                    | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.3.1 | Verifizieren Sie, dass Vor- und Nachgenerierungs-Klassifikatoren Hass, Belästigung, Selbstverletzung, extremistische und sexuell explizite Inhalte, die der Richtlinie entsprechen, blockieren. |   1    |  D/V  |
| 7.3.2 | Stellen Sie sicher, dass die Erkennung von PII/PCI und die automatische Schwärzung bei jeder Antwort durchgeführt werden; Verstöße führen zu einem Datenschutzvorfall.                          |   1    |  D/V  |
| 7.3.3 | Überprüfen Sie, ob Vertraulichkeitsetiketten (z. B. Geschäftsgeheimnisse) modalitätsübergreifend weitergegeben werden, um ein Leck in Text, Bildern oder Code zu verhindern.                    |   2    |   D   |
| 7.3.4 | Überprüfen Sie, ob Versuche zum Umgehen von Filtern oder Klassifizierungen mit hohem Risiko eine sekundäre Genehmigung oder eine erneute Benutzer-Authentifizierung erfordern.                  |   3    |  D/V  |
| 7.3.5 | Überprüfen Sie, ob die Filtergrenzwerte die gesetzlichen Zuständigkeiten sowie den Benutzeralter-/Rollen-Kontext widerspiegeln.                                                                 |   3    |  D/V  |

---

## C7.4 Ausgabe- und Handlungseinschränkung

Ratenbegrenzungen und Genehmigungsschranken verhindern Missbrauch und übermäßige Autonomie.

|   #   | Beschreibung                                                                                                                                                                                                   | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.4.1 | Überprüfen Sie, dass die Kontingente pro Benutzer und pro API-Schlüssel Anfragen, Tokens und Kosten mit exponentiellem Backoff bei 429-Fehlern begrenzen.                                                      |   1    |   D   |
| 7.4.2 | Stellen Sie sicher, dass privilegierte Aktionen (Dateischreibvorgänge, Codeausführung, Netzwerkanrufe) eine richtlinienbasierte Genehmigung oder eine menschliche Genehmigung erfordern.                       |   1    |  D/V  |
| 7.4.3 | Überprüfen Sie, ob cross-modale Konsistenzprüfungen sicherstellen, dass Bilder, Code und Text, die für dieselbe Anfrage generiert wurden, nicht verwendet werden können, um schädliche Inhalte einzuschleusen. |   2    |  D/V  |
| 7.4.4 | Stellen Sie sicher, dass die Agentendelegationstiefe, Rekursionsgrenzen und erlaubte Werkzeuglisten explizit konfiguriert sind.                                                                                |   2    |   D   |
| 7.4.5 | Überprüfen Sie, dass die Überschreitung von Grenzwerten strukturierte Sicherheitsereignisse für die SIEM-Erfassung auslöst.                                                                                    |   3    |   V   |

---

## C7.5 Ausgabeerklärbarkeit

Transparente Signale verbessern das Vertrauen der Benutzer und die interne Fehlerbehebung.

|   #   | Beschreibung                                                                                                                                                            | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.5.1 | Stellen Sie sicher, dass benutzerseitige Vertrauenswerte oder kurze Begründungszusammenfassungen angezeigt werden, wenn die Risikoabschätzung dies für angemessen hält. |   2    |  D/V  |
| 7.5.2 | Überprüfen Sie, dass erzeugte Erklärungen keine sensiblen Systemaufforderungen oder proprietären Daten preisgeben.                                                      |   2    |  D/V  |
| 7.5.3 | Überprüfen Sie, ob das System Token-Ebenen-Log-Wahrscheinlichkeiten oder Aufmerksamkeitskarten erfasst und für autorisierte Prüfungen speichert.                        |   3    |   D   |
| 7.5.4 | Stellen Sie sicher, dass Erklärbarkeitsartefakte zusammen mit Modellversionen versionskontrolliert werden, um Prüfbarkeit zu gewährleisten.                             |   3    |   V   |

---

## C7.6 Überwachungsintegration

Echtzeit-Observabilität schließt den Kreis zwischen Entwicklung und Produktion.

|   #   | Beschreibung                                                                                                                                                           | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.6.1 | Überprüfen Sie, dass Metriken (Schemaverletzungen, Halluzinationsrate, Toxizität, PII-Lecks, Latenz, Kosten) an eine zentrale Überwachungsplattform übertragen werden. |   1    |   D   |
| 7.6.2 | Stellen Sie sicher, dass für jede Sicherheitsmetrik Warnschwellen definiert sind, einschließlich Eskalationspfaden für Bereitschaftspersonal.                          |   1    |   V   |
| 7.6.3 | Überprüfen Sie, ob Dashboards Ausgabefehler mit Modell/Version, Feature-Flag und Änderungen der vorgelagerten Daten korrelieren.                                       |   2    |   V   |
| 7.6.4 | Überprüfen Sie, dass Überwachungsdaten in einem dokumentierten MLOps-Workflow in das Retraining, Fine-Tuning oder die Regelaktualisierung zurückfließen.               |   2    |  D/V  |
| 7.6.5 | Stellen Sie sicher, dass Überwachungspipelines auf Penetration getestet sind und zugangskontrolliert werden, um das Lecken sensibler Protokolle zu vermeiden.          |   3    |   V   |

---

## 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder unautorisierten Medieninhalte erzeugen, indem Sie Richtlinienbeschränkungen, Ausgabekontrollen und Rückverfolgbarkeit durchsetzen.

|   #   | Beschreibung                                                                                                                                                                                                                                   | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 7.7.1 | Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erstellung illegaler, schädlicher oder nicht einvernehmlicher Deepfake-Medien (z. B. Bild, Video, Audio) untersagen.                                    |   1    |  D/V  |
| 7.7.2 | Überprüfen Sie, ob Aufforderungen darauf gefiltert werden, Versuche zur Erzeugung von Nachahmungen, sexuell expliziten Deepfakes oder Medien, die reale Personen ohne deren Zustimmung darstellen, zu erkennen.                                |   2    |  D/V  |
| 7.7.3 | Überprüfen Sie, ob das System Wahrnehmungshashing, Wasserzeichenerkennung oder Fingerprinting verwendet, um die unautorisierte Vervielfältigung von urheberrechtlich geschütztem Medium zu verhindern.                                         |   2    |   V   |
| 7.7.4 | Stellen Sie sicher, dass alle generierten Medien kryptografisch signiert, mit einem Wasserzeichen versehen oder mit manipulationssicheren Herkunftsmetadaten eingebettet sind, um eine nachgelagerte Rückverfolgbarkeit zu gewährleisten.      |   3    |  D/V  |
| 7.7.5 | Stellen Sie sicher, dass Umgehungsversuche (z. B. Prompt-Verschleierung, Slang, adversative Formulierungen) erkannt, protokolliert und durch eine Ratenbegrenzung eingeschränkt werden; wiederholter Missbrauch wird zur Überwachung gemeldet. |   3    |   V   |

## Referenzen

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

