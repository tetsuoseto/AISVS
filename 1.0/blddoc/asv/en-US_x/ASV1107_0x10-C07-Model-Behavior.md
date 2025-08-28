# C7 Model Behavior, Output Control & Safety Assurance

## Control Objective

Model outputs must be structured, reliable, safe, explainable, and continuously monitored in production. This approach reduces hallucinations, privacy leaks, harmful content, and unintended actions, while increasing user trust and ensuring regulatory compliance.

---

## C7.1 Output Format Enforcement

Strict schemas, constrained decoding, and downstream validation prevent malformed or malicious content from propagating.

|   #   | Description                                                                                                                                                                                          | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 7.1.1 | Ensure that response schemas (e.g., JSON Schema) are included in the system prompt and that every output is automatically validated; outputs that do not conform should trigger repair or rejection. |   1   | D/V  |
| 7.1.2 | Ensure that constrained decoding (stop tokens, regex, max tokens) is enabled to prevent overflow or prompt injection side channels.                                                                  |   1   | D/V  |
| 7.1.3 | Ensure that downstream components treat outputs as untrusted and validate them against schemas or injection-safe deserializers.                                                                      |   2   | D/V  |
| 7.1.4 | Verify that events with improper output are logged, rate-limited, and surfaced to monitoring.                                                                                                        |   3   |  V   |

---

## C7.2 Hallucination Detection and Mitigation

Estimating uncertainty and employing fallback strategies help reduce fabricated answers.

|   #   | Description                                                                                                                                                                      | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 7.2.1 | Verify that token-level log-probabilities, ensemble self-consistency, or fine-tuned hallucination detectors assign a confidence score to each answer.                            |   1   | D/V  |
| 7.2.2 | Ensure that responses falling below a configurable confidence threshold activate fallback workflows, such as retrieval-augmented generation, a secondary model, or human review. |   1   | D/V  |
| 7.2.3 | Ensure that hallucination incidents are tagged with root-cause metadata and fed into post-mortem analysis and fine-tuning pipelines.                                             |   2   | D/V  |
| 7.2.4 | Ensure that thresholds and detectors are recalibrated after significant model or knowledge-base updates.                                                                         |   3   | D/V  |
| 7.2.5 | Verify that dashboard visualizations track hallucination rates.                                                                                                                  |   3   |  V   |

---

## C7.3 Output Safety and Privacy Filtering

Policy filters and red-team coverage safeguard users and confidential data.

|   #   | Description                                                                                                                                                                  | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 7.3.1 | Verify that both pre- and post-generation classifiers block hate speech, harassment, self-harm, extremist content, and sexually explicit material in accordance with policy. |   1   | D/V  |
| 7.3.2 | Ensure that PII/PCI detection and automatic redaction are performed on every response; any violations trigger a privacy incident.                                            |   1   | D/V  |
| 7.3.3 | Verify that confidentiality tags (e.g., trade secrets) carry over across modalities to prevent leaks in text, images, or code.                                               |   2   |  D   |
| 7.3.4 | Verify that filter bypass attempts or high-risk classifications require secondary approval or user re-authentication.                                                        |   3   | D/V  |
| 7.3.5 | Verify that filtering thresholds correspond to legal jurisdictions and the user's age and role context.                                                                      |   3   | D/V  |

---

## C7.4 Output and Action Limiting

Rate limits and approval gates prevent abuse and excessive autonomy.

|   #   | Description                                                                                                                                               | Level | Role |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 7.4.1 | Verify that per-user and per-API-key quotas limit requests, tokens, and costs, implementing exponential back-off on 429 errors.                           |   1   |  D   |
| 7.4.2 | Verify that privileged actions (file writes, code execution, network calls) require policy-based approval or human-in-the-loop intervention.              |   1   | D/V  |
| 7.4.3 | Verify that cross-modal consistency checks ensure that images, code, and text generated for the same request cannot be used to smuggle malicious content. |   2   | D/V  |
| 7.4.4 | Verify that agent delegation depth, recursion limits, and allowed tool lists are explicitly configured.                                                   |   2   |  D   |
| 7.4.5 | Verify that limit violations generate structured security events for SIEM ingestion.                                                                      |   3   |  V   |

---

## C7.5 Output Explainability

Transparent signals enhance user trust and facilitate internal debugging.

|   #   | Description                                                                                                                         | Level | Role |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 7.5.1 | Ensure that user-facing confidence scores or brief reasoning summaries are displayed when the risk assessment deems it appropriate. |   2   | D/V  |
| 7.5.2 | Ensure that generated explanations do not reveal sensitive system prompts or proprietary information.                               |   2   | D/V  |
| 7.5.3 | Verify that the system captures token-level log probabilities or attention maps and stores them for authorized inspection.          |   3   |  D   |
| 7.5.4 | Ensure that explainability artifacts are version-controlled alongside model releases for auditability.                              |   3   |  V   |

---

## C7.6 Monitoring Integration

Real-time observability closes the loop between development and production.

|   #   | Description                                                                                                                                    | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 7.6.1 | Verify that metrics (schema violations, hallucination rate, toxicity, PII leaks, latency, cost) are streamed to a central monitoring platform. |   1   |  D   |
| 7.6.2 | Ensure that alert thresholds are defined for each safety metric, with on-call escalation paths established.                                    |   1   |  V   |
| 7.6.3 | Verify that dashboards correlate output anomalies with the model/version, feature flags, and upstream data changes.                            |   2   |  V   |
| 7.6.4 | Ensure that monitoring data is fed back into retraining, fine-tuning, or rule updates within a documented MLOps workflow.                      |   2   | D/V  |
| 7.6.5 | Ensure that monitoring pipelines undergo penetration testing and have access controls in place to prevent the leakage of sensitive logs.       |   3   |  V   |

---

## 7.7 Generative Media Safeguards

Ensure that AI systems do not generate illegal, harmful, or unauthorized media content by enforcing policy constraints, validating outputs, and maintaining traceability.

|   #   | Description                                                                                                                                                                   | Level | Role |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 7.7.1 | Verify that system prompts and user instructions explicitly prohibit generating illegal, harmful, or non-consensual deepfake media (e.g., images, videos, audio).             |   1   | D/V  |
| 7.7.2 | Ensure that prompts are filtered to prevent attempts to generate impersonations, sexually explicit deepfakes, or media depicting real individuals without their consent.      |   2   | D/V  |
| 7.7.3 | Verify that the system uses perceptual hashing, watermark detection, or fingerprinting to prevent unauthorized reproduction of copyrighted media.                             |   2   |  V   |
| 7.7.4 | Ensure that all generated media is cryptographically signed, watermarked, or embedded with tamper-resistant provenance metadata to enable downstream traceability.            |   3   | D/V  |
| 7.7.5 | Ensure that bypass attempts (e.g., prompt obfuscation, slang, adversarial phrasing) are detected, logged, and rate-limited; repeated abuse is reported to monitoring systems. |   3   |  V   |

## References

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

