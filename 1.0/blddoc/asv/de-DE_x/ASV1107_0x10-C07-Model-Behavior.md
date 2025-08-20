# C7 Modellverhalten, Ausgabe­kontrolle & Sicherheits­garantie

## Kontrollziel

Modelausgaben müssen strukturiert, zuverlässig, sicher, erklärbar und kontinuierlich in der Produktion überwacht werden. Dies reduziert Halluzinationen, Datenschutzverletzungen, schädliche Inhalte und außer Kontrolle geratene Aktionen, während es das Vertrauen der Nutzer und die Einhaltung von Vorschriften erhöht.

---

## C7.1 Durchsetzung des Ausgabeformats

Strikte Schemata, eingeschränkte Decodierung und nachgelagerte Validierung stoppen fehlerhafte oder bösartige Inhalte, bevor sie sich ausbreiten.

|   #   | Beschreibung                                                                                                                                                                                                      | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.1.1 | Stellen Sie sicher, dass Antwortschemas (z. B. JSON Schema) im System-Prompt bereitgestellt werden und jede Ausgabe automatisch validiert wird; nicht konforme Ausgaben führen zu einer Reparatur oder Ablehnung. |   1   |  D/V  |
| 7.1.2 | Stellen Sie sicher, dass die eingeschränkte Dekodierung (Stopptoken, Regex, Max-Tokens) aktiviert ist, um Überläufe oder Prompt-Injection-Seitenkanäle zu verhindern.                                             |   1   |  D/V  |
| 7.1.3 | Stellen Sie sicher, dass nachgelagerte Komponenten Ausgaben als nicht vertrauenswürdig behandeln und diese gegen Schemata oder injektionssichere Deserialisierer validieren.                                      |   2   |  D/V  |
| 7.1.4 | Überprüfen Sie, dass Ereignisse mit fehlerhaften Ausgaben protokolliert, mit Begrenzung der Rate versehen und in der Überwachung angezeigt werden.                                                                |   3   |   V   |

---

## C7.2 Halluzinationserkennung und -minderung

Die Abschätzung der Unsicherheit und Fallback-Strategien begrenzen erfundene Antworten.

|   #   | Beschreibung                                                                                                                                                                                               | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.2.1 | Verifizieren Sie, dass token-spezifische Log-Wahrscheinlichkeiten, Ensemble-Selbstkonsistenz oder feinabgestimmte Halluzinationsdetektoren jedem Antwort eine Vertrauensbewertung zuweisen.                |   1   |  D/V  |
| 7.2.2 | Stellen Sie sicher, dass Antworten unterhalb einer konfigurierbaren Vertrauensschwelle Rückfall-Workflows auslösen (z. B. retrieval-augmented generation, sekundäres Modell oder menschliche Überprüfung). |   1   |  D/V  |
| 7.2.3 | Stellen Sie sicher, dass Halluzinationsvorfälle mit Root-Cause-Metadaten gekennzeichnet und an Post-Mortem- und Feinabstimmungs-Pipelines weitergeleitet werden.                                           |   2   |  D/V  |
| 7.2.4 | Stellen Sie sicher, dass Schwellenwerte und Detektoren nach größeren Modell- oder Wissensdatenbank-Updates neu kalibriert werden.                                                                          |   3   |  D/V  |
| 7.2.5 | Überprüfen Sie, ob die Dashboard-Visualisierungen die Halluzinationsraten verfolgen.                                                                                                                       |   3   |   V   |

---

## C7.3 Ausgabe-Sicherheits- und Datenschutzfilterung

Richtlinienfilter und Red-Team-Abdeckung schützen Benutzer und vertrauliche Daten.

|   #   | Beschreibung                                                                                                                                                                                   | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.3.1 | Stellen Sie sicher, dass vor- und nachgelagerte Klassifikatoren Hass, Belästigung, Selbstverletzung, extremistische und sexuell explizite Inhalte, die der Richtlinie entsprechen, blockieren. |   1   |  D/V  |
| 7.3.2 | Stellen Sie sicher, dass die Erkennung von PII/PCI und die automatische Schwärzung bei jeder Antwort ausgeführt werden; Verstöße führen zu einem Datenschutzvorfall.                           |   1   |  D/V  |
| 7.3.3 | Überprüfen Sie, ob Vertraulichkeitstags (z. B. Geschäftsgeheimnisse) über Modalitäten hinweg propagiert werden, um eine Weitergabe in Text, Bildern oder Code zu verhindern.                   |   2   |   D   |
| 7.3.4 | Stellen Sie sicher, dass Umgehungsversuche von Filtern oder Hochrisikoklassifizierungen eine sekundäre Freigabe oder eine erneute Benutzerauthentifizierung erfordern.                         |   3   |  D/V  |
| 7.3.5 | Überprüfen Sie, ob die Filtergrenzwerte die gesetzlichen Zuständigkeitsbereiche sowie den Benutzeralter-/Rollen-Kontext widerspiegeln.                                                         |   3   |  D/V  |

---

## C7.4 Ausgabe- und Aktionsbegrenzung

Ratenbegrenzungen und Genehmigungsschleusen verhindern Missbrauch und übermäßige Autonomie.

|   #   | Beschreibung                                                                                                                                                                                                       | Level | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 7.4.1 | Überprüfen Sie, ob die Pro-Benutzer- und Pro-API-Schlüssel-Quoten Anfragen, Tokens und Kosten mit exponentiellem Back-off bei 429-Fehlern begrenzen.                                                               |   1   |   D   |
| 7.4.2 | Stellen Sie sicher, dass privilegierte Aktionen (Dateischreibvorgänge, Codeausführung, Netzwerkaufrufe) eine richtlinienbasierte Genehmigung oder eine menschliche Überprüfung erfordern.                          |   1   |  D/V  |
| 7.4.3 | Stellen Sie sicher, dass Cross-Modal-Konsistenzprüfungen gewährleisten, dass Bilder, Code und Text, die für dieselbe Anfrage generiert werden, nicht verwendet werden können, um bösartigen Inhalt einzuschleusen. |   2   |  D/V  |
| 7.4.4 | Stellen Sie sicher, dass die Tiefe der Agenten-Delegation, Rekursionsgrenzen und zulässige Werkzeuglisten explizit konfiguriert sind.                                                                              |   2   |   D   |
| 7.4.5 | Überprüfen Sie, ob die Überschreitung von Grenzen strukturierte Sicherheitsereignisse für die SIEM-Einbindung auslöst.                                                                                             |   3   |   V   |

---

## C7.5 Ausgabeerklärbarkeit

Transparente Signale verbessern das Vertrauen der Benutzer und die interne Fehlersuche.

|   #   | Beschreibung                                                                                                                                                                  | Level | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.5.1 | Stellen Sie sicher, dass benutzerorientierte Vertrauenswerte oder kurze Begründungszusammenfassungen angezeigt werden, wenn die Risikobewertung dies als angemessen erachtet. |   2   |  D/V  |
| 7.5.2 | Stellen Sie sicher, dass generierte Erklärungen keine sensiblen Systemaufforderungen oder proprietären Daten offenlegen.                                                      |   2   |  D/V  |
| 7.5.3 | Verifizieren Sie, dass das System Token-Ebene Log-Wahrscheinlichkeiten oder Aufmerksamkeitskarten erfasst und diese zur autorisierten Prüfung speichert.                      |   3   |   D   |
| 7.5.4 | Stellen Sie sicher, dass Erklärbarkeitsartefakte zusammen mit Modellversionen versioniert werden, um die Nachvollziehbarkeit zu gewährleisten.                                |   3   |   V   |

---

## C7.6 Überwachungsintegration

Echtzeit-Observabilität schließt den Kreislauf zwischen Entwicklung und Produktion.

|   #   | Beschreibung                                                                                                                                                           | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.6.1 | Überprüfen Sie, dass Metriken (Schemaverletzungen, Halluzinationsrate, Toxizität, PII-Lecks, Latenz, Kosten) an eine zentrale Überwachungsplattform übertragen werden. |   1   |   D   |
| 7.6.2 | Stellen Sie sicher, dass für jede Sicherheitsmetrik Alarmgrenzwerte definiert sind, einschließlich Eskalationspfaden für den Bereitschaftsdienst.                      |   1   |   V   |
| 7.6.3 | Überprüfen Sie, dass Dashboards Ausgabefehler mit Modell/Version, Feature-Flag und Änderungen an den vorgelagerten Daten korrelieren.                                  |   2   |   V   |
| 7.6.4 | Verifizieren Sie, dass Überwachungsdaten in einem dokumentierten MLOps-Workflow in das Retraining, Fine-Tuning oder Regel-Updates zurückfließen.                       |   2   |  D/V  |
| 7.6.5 | Stellen Sie sicher, dass Überwachungspipelines einem Penetrationstest unterzogen und zugriffskontrolliert sind, um das Austreten sensibler Protokolle zu vermeiden.    |   3   |   V   |

---

## 7.7 Schutzmaßnahmen für generative Medien

Stellen Sie sicher, dass KI-Systeme keine illegalen, schädlichen oder nicht autorisierten Medieninhalte erzeugen, indem Sie Richtlinienbeschränkungen, Ausgabevalidierung und Rückverfolgbarkeit durchsetzen.

|   #   | Beschreibung                                                                                                                                                                                                                                   | Level | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 7.7.1 | Stellen Sie sicher, dass Systemaufforderungen und Benutzeranweisungen ausdrücklich die Erstellung illegaler, schädlicher oder nicht einvernehmlicher Deepfake-Medien (z. B. Bild, Video, Audio) untersagen.                                    |   1   |  D/V  |
| 7.7.2 | Stellen Sie sicher, dass Eingabeaufforderungen auf Versuche überprüft werden, Nachahmungen, sexuell explizite Deepfakes oder Medien, die reale Personen ohne Zustimmung darstellen, zu erzeugen.                                               |   2   |  D/V  |
| 7.7.3 | Überprüfen Sie, ob das System Wahrnehmungshashing, Wasserzeichenerkennung oder Fingerprinting verwendet, um die unbefugte Vervielfältigung von urheberrechtlich geschütztem Medienmaterial zu verhindern.                                      |   2   |   V   |
| 7.7.4 | Stellen Sie sicher, dass alle generierten Medien kryptografisch signiert, mit einem Wasserzeichen versehen oder mit manipulationssicheren Herkunftsmetadaten eingebettet sind, um die Nachverfolgbarkeit im weiteren Verlauf zu gewährleisten. |   3   |  D/V  |
| 7.7.5 | Stellen Sie sicher, dass Umgehungsversuche (z. B. Prompt-Verschleierung, Slang, adversative Formulierungen) erkannt, protokolliert und in der Rate begrenzt werden; wiederholter Missbrauch wird den Überwachungssystemen gemeldet.            |   3   |   V   |

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

