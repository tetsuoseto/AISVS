# C2 User Input Validation

## Control Objective

Robust validation of user input is a first line of defense against some of the most damaging attacks on AI systems. Prompt injection attacks can override system instructions, leak sensitive data, or steer the model toward unauthorized behavior. Unless dedicated filters and instruction hierarchies are in place, research shows that "multi-shot" jailbreaks exploiting very long context windows will be effective. Additionally, subtle adversarial perturbation attacks—such as homoglyph swaps or leetspeak—can silently alter a model’s decisions.

---

## C2.1 Defense Against Prompt Injection

Prompt injection is one of the top risks for AI systems. Defenses against this tactic use a combination of static pattern filters, dynamic classifiers, and instruction hierarchy enforcement.

|   #   | Description                                                                                                                                                                                                                      | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.1.1 | Ensure that user inputs are screened against a continuously updated library of known prompt injection patterns, including jailbreak keywords, "ignore previous" commands, role-play chains, and indirect HTML/URL attacks.       |   1   | D/V  |
| 2.1.2 | Verify that the system enforces an instruction hierarchy where system or developer messages take precedence over user instructions, even after expanding the context window.                                                     |   1   | D/V  |
| 2.1.3 | Ensure that adversarial evaluation tests (e.g., Red Team "many-shot" prompts) are conducted before each model or prompt-template release, with predefined success-rate thresholds and automated blockers to prevent regressions. |   2   | D/V  |
| 2.1.4 | Ensure that prompts derived from third-party content (such as web pages, PDFs, and emails) are sanitized within an isolated parsing context before being concatenated into the main prompt.                                      |   2   |  D   |
| 2.1.5 | Ensure that all updates to prompt-filter rules, classifier model versions, and block-list changes are version-controlled and auditable.                                                                                          |   3   | D/V  |

---

## C2.2 Resistance to Adversarial Examples

Natural Language Processing (NLP) models remain vulnerable to subtle character- or word-level perturbations that humans often overlook but models frequently misclassify.

|   #   | Description                                                                                                                                                                                | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 2.2.1 | Ensure that basic input normalization steps (Unicode NFC, homoglyph mapping, whitespace trimming) are performed before tokenization.                                                       |   1   |  D   |
| 2.2.2 | Verify that statistical anomaly detection identifies inputs with unusually high edit distances from language norms, excessive repeated tokens, or abnormal embedding distances.            |   2   | D/V  |
| 2.2.3 | Verify that the inference pipeline supports optional adversarial training–hardened model variants or defense layers (e.g., randomization, defensive distillation) for high-risk endpoints. |   2   |  D   |
| 2.2.4 | Verify that suspected adversarial inputs are quarantined and logged with full payloads (after redacting PII).                                                                              |   2   |  V   |
| 2.2.5 | Ensure that robustness metrics (success rate of known attack suites) are monitored over time, and that regressions trigger a release blocker.                                              |   3   | D/V  |

---

## C2.3 Schema, Type, and Length Validation

AI attacks involving malformed or oversized inputs can lead to parsing errors, prompt spillage across fields, and resource exhaustion. Strict schema enforcement is also essential when performing deterministic tool calls.

|   #   | Description                                                                                                                                                                                      | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 2.3.1 | Ensure that every API or function call endpoint defines an explicit input schema (JSON Schema, Protobuf, or a multimodal equivalent) and that inputs are validated before assembling the prompt. |   1   |  D   |
| 2.3.2 | Verify that inputs exceeding the maximum token or byte limits are rejected with a safe error and are never silently truncated.                                                                   |   1   | D/V  |
| 2.3.3 | Verify that type checks (e.g., numeric ranges, enum values, MIME types for images/audio) are enforced on the server side, not just in the client code.                                           |   2   | D/V  |
| 2.3.4 | Verify that semantic validators (e.g., JSON Schema) operate in constant time to prevent algorithmic DoS attacks.                                                                                 |   2   |  D   |
| 2.3.5 | Ensure that validation failures are logged with redacted payload snippets and clear error codes to support security triage.                                                                      |   3   |  V   |

---

## C2.4 Content and Policy Screening

Developers should be able to detect syntactically valid prompts that request disallowed content (such as illicit instructions, hate speech, and copyrighted material) and then prevent them from spreading.

|   #   | Description                                                                                                                                                                                         | Level | Role |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.4.1 | Ensure that a content classifier (whether zero-shot or fine-tuned) evaluates every input for violence, self-harm, hate speech, sexual content, and illegal requests, using configurable thresholds. |   1   |  D   |
| 2.4.2 | Ensure that inputs violating policies receive standardized refusals or safe completions to prevent propagation to downstream LLM calls.                                                             |   1   | D/V  |
| 2.4.3 | Ensure that the screening model or rule set is retrained or updated at least quarterly, incorporating newly detected jailbreak or policy bypass patterns.                                           |   2   |  D   |
| 2.4.4 | Ensure that screening complies with user-specific policies (such as age and regional legal restrictions) by using attribute-based rules that are resolved at the time of the request.               |   2   |  D   |
| 2.4.5 | Verify that screening logs include classifier confidence scores and policy category tags for SOC correlation and future red-team replay.                                                            |   3   |  V   |

---

## C2.5 Input Rate Limiting and Abuse Prevention

Developers should prevent abuse, resource exhaustion, and automated attacks on AI systems by limiting input rates and detecting anomalous usage patterns.

|   #   | Description                                                                                                                        | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.5.1 | Verify that rate limits are enforced for each user, each IP address, and each API key across all input endpoints.                  |   1   | D/V  |
| 2.5.2 | Verify that burst and sustained rate limits are configured to prevent DoS and brute force attacks.                                 |   2   | D/V  |
| 2.5.3 | Confirm that abnormal usage patterns (e.g., rapid-fire requests, input flooding) activate automated blocks or trigger escalations. |   2   | D/V  |
| 2.5.4 | Ensure that abuse prevention logs are retained and reviewed to identify emerging attack patterns.                                  |   3   |  V   |

---

## C2.6 Multi-Modal Input Validation

AI systems should incorporate robust validation for non-textual inputs (images, audio, files) to prevent injection attacks, evasion, or resource exploitation.

|   #   | Description                                                                                                          | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.6.1 | Ensure that all non-text inputs (images, audio, files) are validated for type, size, and format prior to processing. |   1   |  D   |
| 2.6.2 | Verify that files are scanned for malware and steganographic payloads before ingestion.                              |   2   | D/V  |
| 2.6.3 | Verify that image and audio inputs are checked for adversarial perturbations or known attack patterns.               |   2   | D/V  |
| 2.6.4 | Ensure that multi-modal input validation failures are logged and trigger alerts for investigation.                   |   3   |  V   |

---

## C2.7 Input Provenance and Attribution

AI systems should support auditing, abuse tracking, and compliance by monitoring and tagging the sources of all user inputs.

|   #   | Description                                                                                                                      | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.7.1 | Ensure that all user inputs are tagged with metadata (user ID, session, source, timestamp, IP address) at the time of ingestion. |   1   | D/V  |
| 2.7.2 | Ensure that provenance metadata is retained and auditable for all processed inputs.                                              |   2   | D/V  |
| 2.7.3 | Ensure that anomalous or untrusted input sources are flagged and subjected to enhanced scrutiny or blocking.                     |   2   | D/V  |

---

## C2.8 Real-Time Adaptive Threat Detection

Developers should use advanced threat detection systems for AI that adapt to new attack patterns and offer real-time protection through compiled pattern matching.

|   #   | Description                                                                                                                                                                             | Level | Role |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.8.1 | Ensure that threat detection patterns are compiled into optimized regex engines for high-performance real-time filtering with minimal latency impact.                                   |   1   | D/V  |
| 2.8.2 | Verify that threat detection systems maintain separate pattern libraries for different threat categories (prompt injection, harmful content, sensitive data, system commands).          |   1   | D/V  |
| 2.8.3 | Verify that adaptive threat detection includes machine learning models that adjust threat sensitivity based on the frequency and success rates of attacks.                              |   2   | D/V  |
| 2.8.4 | Verify that real-time threat intelligence feeds automatically update pattern libraries with new attack signatures and IOCs (Indicators of Compromise).                                  |   2   | D/V  |
| 2.8.5 | Ensure that threat detection false positive rates are continuously monitored and that pattern specificity is automatically adjusted to minimize interference with legitimate use cases. |   3   | D/V  |
| 2.8.6 | Verify that contextual threat analysis takes into account the input source, user behavior patterns, and session history to enhance detection accuracy.                                  |   3   | D/V  |
| 2.8.7 | Verify that threat detection performance metrics (detection rate, processing latency, resource utilization) are continuously monitored and optimized in real time.                      |   3   | D/V  |

---

## C2.9 Multi-Modal Security Validation Pipeline

Developers should implement security validation for text, image, audio, and other AI input modalities by using specific types of threat detection and resource isolation.

|   #   | Description                                                                                                                                                                                                                           | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.9.1 | Verify that each input modality has dedicated security validators with documented threat patterns (text: prompt injection, images: steganography, audio: spectrogram attacks) and established detection thresholds.                   |   1   | D/V  |
| 2.9.2 | Verify that multi-modal inputs are processed in isolated sandboxes with defined resource limits (memory, CPU, processing time) specific to each modality type and documented in the security policies.                                |   2   | D/V  |
| 2.9.3 | Verify that cross-modal attack detection identifies coordinated attacks spanning multiple input types (e.g., steganographic payloads in images combined with prompt injection in text) using correlation rules and alert generation.  |   2   | D/V  |
| 2.9.4 | Verify that multi-modal validation failures trigger detailed logging, including all input modalities, validation results, threat scores, and correlation analysis, using structured log formats for SIEM integration.                 |   3   | D/V  |
| 2.9.5 | Verify that modality-specific content classifiers are updated according to documented schedules (at least quarterly) with new threat patterns, adversarial examples, and performance benchmarks maintained above baseline thresholds. |   3   | D/V  |

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

