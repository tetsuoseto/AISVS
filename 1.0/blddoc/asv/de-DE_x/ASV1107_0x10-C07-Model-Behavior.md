# C7 Modellverhalten, Ausgabesteuerung und Sicherheitsabsicherung

## Kontrollziel

Modellausgaben müssen strukturiert, zuverlässig, sicher, erklärbar und in der Produktion kontinuierlich überwacht werden. Dadurch verringern sich Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und außer Kontrolle geratene Handlungen, während das Vertrauen der Nutzer steigt und die Einhaltung gesetzlicher Vorschriften verbessert wird.

---

## C7.1 Durchsetzung des Ausgabeformats

Strikte Schemata, eingeschränkte Dekodierung und nachgelagerte Validierung stoppen fehlerhaften oder schädlichen Inhalt, bevor er sich verbreitet.

|   #   | Beschreibung                                                                                                                                                                                                           | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.1.1 | Stellen Sie sicher, dass Antwort-Schemata (z. B. JSON-Schema) im Systemprompt bereitgestellt werden und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben führen zu einer Nachbesserung oder Ablehnung. |   1   |  D/V  |
| 7.1.2 | Überprüfen Sie, ob eingeschränkte Decodierung (Stop-Tokens, Regex, Max-Tokens) aktiviert ist, um Überlauf oder Prompt-Injection-Seitenkanäle zu verhindern.                                                            |   1   |  D/V  |
| 7.1.3 | Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese gegen Schemata oder injektionssichere Deserialisierer validieren.                                           |   2   |  D/V  |
| 7.1.4 | Stellen Sie sicher, dass unzulässige Ausgabeereignisse protokolliert werden, einer Ratenbegrenzung unterliegen und dem Monitoring gemeldet werden.                                                                     |   3   |   V   |

---

## C7.2 Halluzinationserkennung und Minderung

Unsicherheitsabschätzung und Fallback-Strategien dämpfen halluzinierte Antworten.

|   #   | Beschreibung                                                                                                                                                                                  | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.2.1 | Überprüfen Sie, ob Token-Level-Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jeder Antwort einen Konfidenzwert zuweisen.                  |   1   |  D/V  |
| 7.2.2 | Überprüfen Sie, ob Antworten unter einer konfigurierbaren Konfidenzschwelle Fallback-Workflows auslösen (z. B. abfragegestützte Generierung, sekundäres Modell oder menschliche Überprüfung). |   1   |  D/V  |
| 7.2.3 | Überprüfen Sie, dass Halluzinationsvorfälle mit Grundursachen-Metadaten gekennzeichnet sind und in Post-Mortem- und Feinabstimmungs-Pipelines eingespeist werden.                             |   2   |  D/V  |
| 7.2.4 | Stellen Sie sicher, dass Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbankaktualisierungen neu kalibriert werden.                                                     |   3   |  D/V  |
| 7.2.5 | Stellen Sie sicher, dass Dashboard-Visualisierungen die Halluzinationsraten verfolgen.                                                                                                        |   3   |   V   |

---

## C7.3 Ausgabe-Sicherheit und Datenschutz-Filterung

Richtlinienfilter und Red-Team-Abdeckung schützen Nutzer und vertrauliche Daten.

|   #   | Beschreibung                                                                                                                                                                                                  | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.3.1 | Vergewissern Sie sich, dass Vor- und Nachgenerierungs-Klassifikatoren Inhalte, die Hass, Belästigung, Selbstverletzung, Extremismus und sexuell explizite Inhalte betreffen, gemäß der Richtlinie blockieren. |   1   |  D/V  |
| 7.3.2 | Überprüfen Sie, ob PII/PCI-Erkennung und automatische Unkenntlichmachung bei jeder Antwort ausgeführt werden; Verstöße lösen einen Datenschutzvorfall aus.                                                    |   1   |  D/V  |
| 7.3.3 | Überprüfen Sie, ob Vertraulichkeitskennzeichnungen (z. B. Geschäftsgeheimnisse) über Modalitäten hinweg weitergegeben werden, um Datenlecks in Texten, Bildern oder Code zu verhindern.                       |   2   |   D   |
| 7.3.4 | Stellen Sie sicher, dass Versuche der Filterumgehung oder Klassifizierungen mit hohem Risiko eine sekundäre Freigabe oder eine erneute Authentifizierung des Benutzers erfordern.                             |   3   |  D/V  |
| 7.3.5 | Stellen Sie sicher, dass Filter-Schwellenwerte die geltenden Rechtsordnungen sowie den Alters- bzw. Rollen-Kontext des Nutzers berücksichtigen.                                                               |   3   |  D/V  |

---

## C7.4 Ausgabe- und Aktionsbeschränkung

Ratenbegrenzungen und Freigabestufen verhindern Missbrauch und übermäßige Autonomie.

|   #   | Beschreibung                                                                                                                                                                                                                     | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.4.1 | Stellen Sie sicher, dass die Nutzungsquoten pro Benutzer und pro API-Schlüssel Anfragen, Tokens und Kosten begrenzen, mit exponentiellem Back-off bei 429-Fehlern.                                                               |   1   |   D   |
| 7.4.2 | Vergewissern Sie sich, dass privilegierte Aktionen (Datei-Schreibvorgänge, Code-Ausführung, Netzwerkaufrufe) eine policy-basierte Genehmigung oder Mensch-in-der-Schleife erfordern.                                             |   1   |  D/V  |
| 7.4.3 | Stellen Sie sicher, dass modalitätsübergreifende Konsistenzprüfungen sicherstellen, dass Bilder, Code und Text, die für dieselbe Anfrage generiert wurden, nicht dazu verwendet werden können, böswillige Inhalte zu schmuggeln. |   2   |  D/V  |
| 7.4.4 | Stellen Sie sicher, dass die Delegierungstiefe des Agenten, die Rekursionstiefen und die zulässigen Werkzeuglisten explizit konfiguriert sind.                                                                                   |   2   |   D   |
| 7.4.5 | Überprüfen Sie, ob Grenzwertverletzungen strukturierte Sicherheitsereignisse für die SIEM-Ingestion erzeugen.                                                                                                                    |   3   |   V   |

---

## C7.5 Ausgabenerklärbarkeit

Transparente Signale stärken das Vertrauen der Benutzer und erleichtern die interne Fehlersuche.

|   #   | Beschreibung                                                                                                                                                                      | Level | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.5.1 | Stellen Sie sicher, dass für den Benutzer sichtbare Konfidenzwerte oder kurze Begründungszusammenfassungen offengelegt werden, wenn die Risikobewertung dies für angemessen hält. |   2   |  D/V  |
| 7.5.2 | Vergewissern Sie sich, dass generierte Erklärungen keine sensiblen System-Prompts oder proprietären Daten offenlegen.                                                             |   2   |  D/V  |
| 7.5.3 | Stellen Sie sicher, dass das System Log-Wahrscheinlichkeiten pro Token oder Aufmerksamkeitskarten erfasst und diese speichert.                                                    |   3   |   D   |
| 7.5.4 | Stellen Sie sicher, dass Artefakte der Erklärbarkeit neben Modellveröffentlichungen unter Versionskontrolle stehen, um Auditierbarkeit zu gewährleisten.                          |   3   |   V   |

---

## C7.6 Monitoring-Integration

Echtzeit-Beobachtbarkeit schließt den Kreis zwischen Entwicklung und Produktion.

|   #   | Beschreibung                                                                                                                                                                          | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.6.1 | Stellen Sie sicher, dass Metriken (Schema-Verstöße, Halluzinationsrate, Toxizität, PII-Datenlecks, Latenz, Kosten) an eine zentrale Überwachungsplattform gestreamt werden.           |   1   |   D   |
| 7.6.2 | Stellen Sie sicher, dass Alarm-Schwellenwerte für jede Sicherheitsmetrik definiert sind, mit Eskalationspfaden im Bereitschaftsdienst.                                                |   1   |   V   |
| 7.6.3 | Verifizieren Sie, dass Dashboards Ausgabeanomalien mit Modell/Version, Feature-Flag und Änderungen der Quelldaten korrelieren.                                                        |   2   |   V   |
| 7.6.4 | Stellen Sie sicher, dass Überwachungsdaten in Retraining, Feinabstimmung oder Regelaktualisierungen innerhalb eines dokumentierten MLOps-Workflows zurückfließen.                     |   2   |  D/V  |
| 7.6.5 | Verifizieren Sie, dass die Überwachungs-Pipelines Penetrationstests unterzogen werden und Zugriffskontrollen implementiert sind, um das Austreten sensibler Protokolle zu verhindern. |   3   |   V   |

---

## 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder unautorisierten Medieninhalte erzeugen, indem Richtlinienbeschränkungen, Ausgabevalidierung und Nachverfolgbarkeit durchgesetzt werden.

|   #   | Beschreibung                                                                                                                                                                                                                                          | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.7.1 | Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erzeugung illegaler, schädlicher oder nicht einvernehmlicher Deepfake-Medien (z. B. Bilder, Videos, Audios) untersagen.                                        |   1   |  D/V  |
| 7.7.2 | Stellen Sie sicher, dass Eingabeaufforderungen dahingehend gefiltert werden, ob sie darauf abzielen, Imitationen zu erzeugen, sexuell explizite Deepfakes zu erstellen oder Medien zu produzieren, die reale Personen ohne deren Einwilligung zeigen. |   2   |  D/V  |
| 7.7.3 | Stellen Sie sicher, dass das System Perzeptuelles Hashing, Wasserzeichenerkennung oder Fingerabdruckverfahren verwendet, um eine unbefugte Reproduktion urheberrechtlich geschützter Medien zu verhindern.                                            |   2   |   V   |
| 7.7.4 | Vergewissern Sie sich, dass alle generierten Medien kryptografisch signiert, mit Wasserzeichen versehen oder mit manipulationssicheren Provenienz-Metadaten eingebettet sind, um eine nachgelagerte Nachverfolgbarkeit zu ermöglichen.                |   3   |  D/V  |
| 7.7.5 | Stellen Sie sicher, dass Umgehungsversuche (z. B. Prompt-Obfuskation, Slang, adversarische Formulierungen) erkannt, protokolliert und durch Ratenbegrenzung eingeschränkt werden; wiederholter Missbrauch wird an die Überwachungssysteme gemeldet.   |   3   |   V   |

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

