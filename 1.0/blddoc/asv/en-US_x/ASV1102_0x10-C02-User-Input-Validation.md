# C2 User Input Validation

## Control Objective

Robust validation of user input is a first line of defense against some of the most damaging attacks on AI systems. Prompt injection attacks can override system instructions, leak sensitive data, or steer the model toward behavior that is not allowed. Unless dedicated filters and instruction hierarchies are in place, research shows that "multi-shot" jailbreaks that exploit very long context windows will be effective. Additionally, subtle adversarial perturbation attacks--such as homoglyph swaps or leetspeak—-can silently change a model's decisions.

---

## C2.1 Prompt Injection Defense

Prompt injection is one of the top risks for AI systems. Defenses against this tactic employ a combination of static pattern filters, dynamic classifiers, and instruction hierarchy enforcement.

|   #   | Description                                                                                                                                                                                                          | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.1.1 | Verify that user inputs are screened against a continuously updated library of known prompt injection patterns (jailbreak keywords, "ignore previous", role-play chains, indirect HTML/URL attacks).                 |   1   | D/V  |
| 2.1.2 | Verify that the system enforces an instruction hierarchy in which system or developer messages override user instructions, even after the context window has expanded.                                               |   1   | D/V  |
| 2.1.3 | Verify that adversarial evaluation tests (e.g., the Red Team "many-shot" prompts) are run before every model or prompt-template release, with success-rate thresholds and automated blockers to prevent regressions. |   2   | D/V  |
| 2.1.4 | Verify that prompts originating from third-party content (web pages, PDFs, emails) are sanitized in an isolated parsing context before they are concatenated into the main prompt.                                   |   2   |  D   |
| 2.1.5 | Verify that all prompt-filter rule updates, classifier model versions, and block-list changes are version-controlled and auditable.                                                                                  |   3   | D/V  |

---

## C2.2 Adversarial-Example Resistance

Natural Language Processing (NLP) models remain vulnerable to subtle character- or word-level perturbations that humans often miss, but models tend to misclassify them.

|   #   | Description                                                                                                                                                                                | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 2.2.1 | Verify that basic input normalization steps (Unicode NFC, homoglyph mapping, whitespace trimming) run before tokenization.                                                                 |   1   |  D   |
| 2.2.2 | Verify that statistical anomaly detection flags inputs that have an unusually high edit distance from language norms, excessive repetition of tokens, or abnormal embedding distances.     |   2   | D/V  |
| 2.2.3 | Verify that the inference pipeline supports optional adversarial-training–hardened model variants or defense layers (e.g., randomization, defensive distillation) for high-risk endpoints. |   2   |  D   |
| 2.2.4 | Verify that suspected adversarial inputs are quarantined and logged with full payloads (after PII redaction).                                                                              |   2   |  V   |
| 2.2.5 | Verify that robustness metrics (the success rate of known attack suites) are tracked over time, and that regressions trigger a release blocker.                                            |   3   | D/V  |

---

## C2.3 Schema, Type, and Length Validation

AI attacks that feature malformed or oversized inputs can cause parsing errors, prompt spillage across fields, and exhaust resources.  Strict schema enforcement is also a prerequisite when performing deterministic tool calls.

|   #   | Description                                                                                                                                                                                | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 2.3.1 | Verify that every API or function call endpoint defines an explicit input schema (JSON Schema, Protobuf, or a multimodal equivalent) and that inputs are validated before prompt assembly. |   1   |  D   |
| 2.3.2 | Verify that inputs exceeding the maximum token or byte limits are rejected with a safe error and are never silently truncated.                                                             |   1   | D/V  |
| 2.3.3 | Verify that type checks (e.g., numeric ranges, enum values, and MIME types for images and audio) are enforced server-side, not only in client code.                                        |   2   | D/V  |
| 2.3.4 | Verify that semantic validators, such as JSON Schema, run in constant time to prevent algorithmic DoS.                                                                                     |   2   |  D   |
| 2.3.5 | Ensure that validation failures are logged with redacted payload snippets and unambiguous error codes to aid security triage.                                                              |   3   |  V   |

---

## C2.4 Content & Policy Screening

Developers should be able to detect syntactically valid prompts that request disallowed content, such as illicit instructions, hate speech, or copyrighted text, and then prevent them from propagating.

|   #   | Description                                                                                                                                                                      | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.4.1 | Verify that a content classifier (zero-shot or fine-tuned) scores every input for violence, self-harm, hate, sexual content, and illegal requests, with configurable thresholds. |   1   |  D   |
| 2.4.2 | Verify that inputs that violate policies receive standardized refusals or safe completions so they do not propagate to downstream LLM calls.                                     |   1   | D/V  |
| 2.4.3 | Verify that the screening model or rule set is retrained or updated at least quarterly, incorporating newly observed jailbreak or policy bypass patterns.                        |   2   |  D   |
| 2.4.4 | Verify that screening complies with user-specific policies (age and regional legal constraints) via attribute-based rules resolved at request time.                              |   2   |  D   |
| 2.4.5 | Verify that screening logs include classifier confidence scores and policy category tags for SOC correlation and future red-team replay.                                         |   3   |  V   |

---

## C2.5 Input Rate Limiting and Abuse Prevention

Developers should prevent abuse, resource exhaustion, and automated attacks on AI systems by limiting input rates and detecting anomalous usage patterns.

|   #   | Description                                                                                                                  | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.5.1 | Verify that rate limits per user, per IP address, and per API key are enforced for all input endpoints.                      |   1   | D/V  |
| 2.5.2 | Verify that burst and sustained rate limits are tuned to prevent DoS and brute-force attacks.                                |   2   | D/V  |
| 2.5.3 | Verify that anomalous usage patterns (e.g., rapid-fire requests and input flooding) trigger automated blocks or escalations. |   2   | D/V  |
| 2.5.4 | Verify that abuse-prevention logs are retained and reviewed for emerging attack patterns.                                    |   3   |  V   |

---

## C2.6 Multi-Modal Input Validation

AI systems should implement robust validation for non-textual inputs (images, audio, and files) to prevent injection, evasion, or resource abuse.

|   #   | Description                                                                                                            | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.6.1 | Verify that all non-text inputs (images, audio, and files) are validated for type, size, and format before processing. |   1   |  D   |
| 2.6.2 | Verify that files are scanned for malware and steganographic payloads prior to ingestion.                              |   2   | D/V  |
| 2.6.3 | Verify that image or audio inputs are checked for adversarial perturbations or known attack patterns.                  |   2   | D/V  |
| 2.6.4 | Verify that multi-modal input validation failures are logged and that alerts are triggered for investigation.          |   3   |  V   |

---

## C2.7 Input Provenance and Attribution

AI systems should support auditing, abuse tracking, and compliance by monitoring and tagging the origins of all user inputs.

|   #   | Description                                                                                                              | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 2.7.1 | Verify that all user inputs are tagged with metadata (user ID, session, source, timestamp, IP address) during ingestion. |   1   | D/V  |
| 2.7.2 | Verify that provenance metadata is retained and auditable for all processed inputs.                                      |   2   | D/V  |
| 2.7.3 | Verify that anomalous or untrusted input sources are flagged and subjected to enhanced scrutiny or blocked.              |   2   | D/V  |

---

## C2.8 Real-Time Adaptive Threat Detection

Developers should employ advanced threat-detection systems for AI that adapt to evolving attack patterns and provide real-time protection through compiled pattern matching.

|   #   | Description                                                                                                                                                                          | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 2.8.1 | Verify that threat detection patterns are compiled into optimized regex engines for high-performance real-time filtering with minimal latency impact.                                |   1   | D/V  |
| 2.8.2 | Verify that threat-detection systems maintain separate pattern libraries for different threat categories (prompt injection, harmful content, sensitive data, and system commands).   |   1   | D/V  |
| 2.8.3 | Verify that adaptive threat detection uses machine learning models that adjust threat sensitivity based on attack frequency and success rates.                                       |   2   | D/V  |
| 2.8.4 | Verify that real-time threat intelligence feeds automatically update pattern libraries with new attack signatures and IOCs (Indicators of Compromise).                               |   2   | D/V  |
| 2.8.5 | Verify that threat detection false positive rates are continuously monitored and that pattern specificity is automatically tuned to minimize interference with legitimate use cases. |   3   | D/V  |
| 2.8.6 | Verify that contextual threat analysis takes input source, user behavior patterns, and session history into account to improve detection accuracy.                                   |   3   | D/V  |
| 2.8.7 | Verify that threat detection performance metrics (detection rate, processing latency, and resource utilization) are monitored and optimized in real-time.                            |   3   | D/V  |

---

## C2.9 Multi-Modal Security Validation Pipeline

Developers should implement security validation for text, image, audio, and other AI input modalities, using specific threat-detection techniques and resource isolation.

|   #   | Description                                                                                                                                                                                                                          | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 2.9.1 | Verify that each input modality has dedicated security validators with documented threat patterns (text: prompt injection; images: steganography; audio: spectrogram attacks) and defined detection thresholds.                      |   1   | D/V  |
| 2.9.2 | Verify that multi-modal inputs are processed in isolated sandboxes with defined resource limits (memory, CPU, and processing time) that are specific to each modality type and documented in security policies.                      |   2   | D/V  |
| 2.9.3 | Verify that cross-modal attack detection identifies coordinated attacks spanning multiple input types (e.g., steganographic payloads in images combined with prompt injection in text) using correlation rules and alert generation. |   2   | D/V  |
| 2.9.4 | Verify that multi-modal validation failures trigger detailed logging, including all input modalities, validation results, threat scores, and correlation analysis, using structured log formats suitable for SIEM integration.       |   3   | D/V  |
| 2.9.5 | Verify that modality-specific content classifiers are updated according to documented schedules (minimum quarterly) with new threat patterns, adversarial examples, and performance benchmarks maintained above baseline thresholds. |   3   | D/V  |

---

## References

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

