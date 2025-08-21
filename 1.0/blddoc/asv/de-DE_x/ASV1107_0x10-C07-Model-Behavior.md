# C7 Modellverhalten, Ausgabeüberwachung & Sicherheitsgarantie

## Kontrollziel

Modellausgaben müssen strukturiert, zuverlässig, sicher, erklärbar und in der Produktion kontinuierlich überwacht werden. Dies verringert Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und unkontrollierte Aktionen, während es das Vertrauen der Benutzer und die Einhaltung gesetzlicher Vorschriften erhöht.

---

## C7.1 Durchsetzung des Ausgabeformats

Strikte Schemata, eingeschränkte Decodierung und nachgelagerte Validierung verhindern, dass fehlerhafte oder bösartige Inhalte verbreitet werden.

|   #   | Beschreibung                                                                                                                                                                                                 | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 7.1.1 | Überprüfen Sie, dass Antwortschemata (z. B. JSON-Schema) im Systemprompt bereitgestellt werden und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben lösen eine Reparatur oder Ablehnung aus. |   1   |  D/V  |
| 7.1.2 | Vergewissern Sie sich, dass die eingeschränkte Decodierung (Stopp-Token, Regex, Max-Token) aktiviert ist, um Überläufe oder Prompt-Injektions-Nebenkanäle zu verhindern.                                     |   1   |  D/V  |
| 7.1.3 | Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese anhand von Schemata oder gegen Injektionen gesicherten Deserialisierern validieren.               |   2   |  D/V  |
| 7.1.4 | Stellen Sie sicher, dass Ereignisse mit fehlerhaften Ausgaben protokolliert, rate-begrenzt und der Überwachung zugänglich gemacht werden.                                                                    |   3   |   V   |

---

## C7.2 Halluzinations­erkennung und -minderung

Unsicherheitsabschätzung und Fallback-Strategien begrenzen erfundene Antworten.

|   #   | Beschreibung                                                                                                                                                                                               | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.2.1 | Verifizieren Sie, dass Token-Ebenen-Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jedem Antwort eine Vertrauensbewertung zuweisen.                     |   1   |  D/V  |
| 7.2.2 | Überprüfen Sie, ob Antworten unterhalb eines konfigurierbaren Vertrauensschwellenwerts Rückfall-Workflows auslösen (z. B. retrieval-augmented Generation, sekundäres Modell oder menschliche Überprüfung). |   1   |  D/V  |
| 7.2.3 | Stellen Sie sicher, dass Halluzinationsvorfälle mit Ursachen-Metadaten gekennzeichnet und an Post-Mortem- und Fine-Tuning-Pipelines weitergeleitet werden.                                                 |   2   |  D/V  |
| 7.2.4 | Überprüfen Sie, ob Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbank-Aktualisierungen neu kalibriert werden.                                                                       |   3   |  D/V  |
| 7.2.5 | Überprüfen Sie, ob die Dashboard-Visualisierungen die Halluzinationsraten erfassen.                                                                                                                        |   3   |   V   |

---

## C7.3 Ausgabe-Sicherheits- und Datenschutzfilterung

Richtlinienfilter und Red-Team-Abdeckung schützen Benutzer und vertrauliche Daten.

|   #   | Beschreibung                                                                                                                                                                               | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 7.3.1 | Überprüfen Sie, ob Pre- und Post-Generation-Klassifikatoren Hass, Belästigung, Selbstverletzung, extremistische und sexuell explizite Inhalte, die der Richtlinie entsprechen, blockieren. |   1   |  D/V  |
| 7.3.2 | Überprüfen Sie, dass die Erkennung von PII/PCI und die automatische Schwärzung in jeder Antwort ausgeführt werden; Verstöße führen zu einem Datenschutzvorfall.                            |   1   |  D/V  |
| 7.3.3 | Überprüfen Sie, ob Vertraulichkeitskennzeichnungen (z. B. Geschäftsgeheimnisse) über Modalitäten hinweg übertragen werden, um ein Leck in Texten, Bildern oder Code zu verhindern.         |   2   |   D   |
| 7.3.4 | Überprüfen Sie, ob Versuche zur Umgehung von Filtern oder Klassifizierungen mit hohem Risiko eine sekundäre Genehmigung oder eine erneute Benutzer-Authentifizierung erfordern.            |   3   |  D/V  |
| 7.3.5 | Überprüfen Sie, ob die Filtergrenzwerte die gesetzlichen Zuständigkeiten sowie den Benutzeralter- und Rollen-Kontext berücksichtigen.                                                      |   3   |  D/V  |

---

## C7.4 Ausgabe- und Aktionsbegrenzung

Ratenbegrenzungen und Genehmigungskontrollen verhindern Missbrauch und übermäßige Autonomie.

|   #   | Beschreibung                                                                                                                                                                                                      | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.4.1 | Überprüfen Sie, dass Kontingente pro Benutzer und pro API-Schlüssel die Anfragen, Tokens und Kosten mit exponentiellem Back-off bei 429-Fehlern begrenzen.                                                        |   1   |   D   |
| 7.4.2 | Stellen Sie sicher, dass privilegierte Aktionen (Dateischreibvorgänge, Codeausführung, Netzwerkaufrufe) eine richtlinienbasierte Genehmigung oder eine menschliche Überprüfung erfordern.                         |   1   |  D/V  |
| 7.4.3 | Stellen Sie sicher, dass Cross-Modal-Konsistenzprüfungen gewährleisten, dass Bilder, Code und Text, die für dieselbe Anfrage generiert werden, nicht verwendet werden können, um bösartige Inhalte zu schmuggeln. |   2   |  D/V  |
| 7.4.4 | Stellen Sie sicher, dass die Tiefe der Agentendelegation, Rekursionsgrenzen und erlaubte Tool-Listen explizit konfiguriert sind.                                                                                  |   2   |   D   |
| 7.4.5 | Überprüfen Sie, dass die Überschreitung von Grenzwerten strukturierte Sicherheitsereignisse für die SIEM-Aufnahme auslöst.                                                                                        |   3   |   V   |

---

## C7.5 Ausgabeerklärbarkeit

Transparente Signale verbessern das Vertrauen der Benutzer und die interne Fehlersuche.

|   #   | Beschreibung                                                                                                                                                              | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.5.1 | Stellen Sie sicher, dass benutzerorientierte Vertrauenswerte oder kurze Begründungszusammenfassungen angezeigt werden, wenn die Risikobewertung dies für angemessen hält. |   2   |  D/V  |
| 7.5.2 | Stellen Sie sicher, dass generierte Erklärungen keine sensiblen Systemanweisungen oder proprietären Daten offenbaren.                                                     |   2   |  D/V  |
| 7.5.3 | Überprüfen Sie, ob das System Token-Ebene Log-Wahrscheinlichkeiten oder Aufmerksamkeitskarten erfasst und sie für autorisierte Inspektionen speichert.                    |   3   |   D   |
| 7.5.4 | Stellen Sie sicher, dass Erklärbarkeits-Artefakte zusammen mit Modellversionen versioniert werden, um die Prüfbarkeit zu gewährleisten.                                   |   3   |   V   |

---

## C7.6 Überwachungsintegration

Echtzeit-Beobachtbarkeit schließt den Kreislauf zwischen Entwicklung und Produktion.

|   #   | Beschreibung                                                                                                                                                                     | Level | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.6.1 | Stellen Sie sicher, dass Metriken (Schemaverstöße, Halluzinationsrate, Toxizität, PII-Lecks, Latenz, Kosten) an eine zentrale Überwachungsplattform übertragen werden.           |   1   |   D   |
| 7.6.2 | Stellen Sie sicher, dass für jede Sicherheitsmetrik Alarmgrenzwerte definiert sind, einschließlich der Eskalationswege für Bereitschaftsdienste.                                 |   1   |   V   |
| 7.6.3 | Überprüfen Sie, ob Dashboards Ausgabestörungen mit Modell/Version, Feature-Flag und Änderungen der vorgelagerten Daten korrelieren.                                              |   2   |   V   |
| 7.6.4 | Überprüfen Sie, ob Überwachungsdaten in einem dokumentierten MLOps-Workflow in das Retraining, Fine-Tuning oder Regel-Updates zurückfließen.                                     |   2   |  D/V  |
| 7.6.5 | Stellen Sie sicher, dass Überwachungspipelines Penetrationstests unterzogen werden und Zugangskontrollen implementiert sind, um das Austreten sensibler Protokolle zu vermeiden. |   3   |   V   |

---

## 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder unautorisierten Medieninhalte erzeugen, indem Sie Richtlinienbeschränkungen, Ausgabeverifizierung und Rückverfolgbarkeit durchsetzen.

|   #   | Beschreibung                                                                                                                                                                                                                                    | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.7.1 | Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erstellung von illegalen, schädlichen oder nicht einvernehmlichen Deepfake-Medien (z. B. Bild, Video, Audio) verbieten.                                  |   1   |  D/V  |
| 7.7.2 | Vergewissern Sie sich, dass Eingabeaufforderungen auf Versuche gefiltert werden, Nachahmungen, sexuell explizite Deepfakes oder Medien, die reale Personen ohne deren Zustimmung darstellen, zu generieren.                                     |   2   |  D/V  |
| 7.7.3 | Überprüfen Sie, ob das System Wahrnehmungshashing, Wasserzeichenerkennung oder Fingerprinting verwendet, um die unbefugte Vervielfältigung von urheberrechtlich geschütztem Material zu verhindern.                                             |   2   |   V   |
| 7.7.4 | Stellen Sie sicher, dass alle generierten Medien kryptografisch signiert, mit einem Wasserzeichen versehen oder mit manipulationssicheren Herkunfts-Metadaten eingebettet sind, um die Nachverfolgbarkeit im weiteren Verlauf zu gewährleisten. |   3   |  D/V  |
| 7.7.5 | Stellen Sie sicher, dass Umgehungsversuche (z. B. Aufforderungsverschleierung, Slang, adversative Formulierungen) erkannt, protokolliert und in der Rate begrenzt werden; wiederholter Missbrauch wird an Überwachungssysteme gemeldet.         |   3   |   V   |

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

