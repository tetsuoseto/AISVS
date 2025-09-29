# C2 User Input Validation

## Control Objective

Robust validation of user input is a primary defense against some of the most harmful attacks on AI systems. Prompt injection attacks can override system instructions, expose sensitive data, or direct the model toward prohibited behaviors. Without dedicated filters and other validation measures, research shows that jailbreaks exploiting context windows will continue to be effective.

---

## C2.1 Prompt Injection Defense

Prompt injection is one of the top risks for AI systems. Defenses against this tactic use a combination of pattern filters, data classifiers, and instruction hierarchy enforcement.

|   #   | Description                                                                                                                                                                            | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.1.1 | Verify that user inputs are screened against a continuously updated library of known prompt injection patterns, including jailbreak keywords, "ignore previous," and role-play chains. |   1   | D/V  |
| 2.1.2 | Verify that the system enforces an instruction hierarchy where system messages override user instructions, even after processing the user instructions.                                |   1   | D/V  |
| 2.1.4 | Ensure that prompts coming from third-party content (web pages, PDFs, emails) are sanitized separately before being combined into the main prompt.                                     |   2   |  D   |

---

## C2.2 Resistance to Adversarial Examples

Natural Language Processing (NLP) models remain vulnerable to subtle character- or word-level perturbations that humans often overlook but cause models to misclassify.

|   #   | Description                                                                                                                                                                                                                                                                                                                  | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.2.1 | Ensure that basic input normalization steps—Unicode NFC, homoglyph mapping, and whitespace trimming—are performed before tokenization.                                                                                                                                                                                       |   1   |  D   |
| 2.2.2 | Verify that statistical anomaly detection flags inputs with unusually high edit distances from language norms or abnormal embedding distances.                                                                                                                                                                               |   2   | D/V  |
| 2.2.3 | Verify that the inference pipeline supports adversarial training–hardened model variants or defense layers (e.g., randomization, defensive distillation, alignment checks) for high-risk endpoints.                                                                                                                          |   2   |  D   |
| 2.2.4 | Ensure that suspected adversarial inputs are quarantined and logged with their full payloads.                                                                                                                                                                                                                                |   2   |  V   |
| 2.2.5 | Ensure that encoding and representation smuggling in both inputs and outputs (e.g., invisible Unicode/control characters, homoglyph swaps, or mixed-direction text) are detected and mitigated. Approved mitigation methods include canonicalization, strict schema validation, policy-based rejection, or explicit marking. |   2   | D/V  |

---

## C2.3 Schema, Type, and Length Validation

AI attacks involving malformed or oversized inputs can lead to parsing errors, prompt spillage across fields, and resource exhaustion. Strict schema enforcement is also essential when performing deterministic tool calls.

|   #   | Description                                                                                                                                                                                    | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.3.1 | Ensure that every API or function call endpoint defines an explicit input schema (JSON Schema, Protobuf, or multimodal equivalent) and that inputs are validated before assembling the prompt. |   1   |  D   |
| 2.3.2 | Verify that inputs exceeding the maximum token or byte limits are rejected with a safe error message and are never silently truncated.                                                         |   1   | D/V  |
| 2.3.3 | Verify that type checks (e.g., numeric ranges, enum values, MIME types for images/audio) are enforced on the server side.                                                                      |   2   | D/V  |
| 2.3.4 | Ensure that semantic validators (e.g., JSON Schema) execute in constant time to prevent algorithmic DoS attacks.                                                                               |   2   |  D   |
| 2.3.5 | Verify that validation failures are logged with redacted payload snippets and clear error codes to support security triage.                                                                    |   3   |  V   |

---

## C2.4 Content and Policy Screening

Developers should be able to detect syntactically valid prompts that request disallowed content (such as illicit instructions, hate speech, and/or copyrighted text) and then prevent them from spreading.

|   #   | Description                                                                                                                                                                         | Level | Role |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.4.1 | Ensure that a content classifier (zero-shot or fine-tuned) evaluates every input for violence, self-harm, hate, sexual content, and illegal requests, with configurable thresholds. |   1   |  D   |
| 2.4.2 | Ensure that inputs violating policies receive standardized refusals or safe completions to prevent them from propagating to downstream LLM calls.                                   |   1   | D/V  |
| 2.4.3 | Ensure that screening complies with user-specific policies (such as age and regional legal restrictions) through attribute-based rules evaluated at the time of the request.        |   2   |  D   |
| 2.4.4 | Verify that screening logs include classifier confidence scores and policy category tags for SOC correlation and future red team replay.                                            |   3   |  V   |

---

## C2.5 Input Rate Limiting and Abuse Prevention

Developers should prevent abuse, resource exhaustion, and automated attacks on AI systems by limiting input rates and detecting anomalous usage patterns.

|   #   | Description                                                                                                              | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 2.5.1 | Verify that rate limits per user, per IP, and per API key are enforced for all input endpoints.                          |   1   | D/V  |
| 2.5.2 | Verify that burst and sustained rate limits are properly configured to prevent DoS and brute force attacks.              |   2   | D/V  |
| 2.5.3 | Verify that abnormal usage patterns (e.g., rapid-fire requests, input flooding) trigger automated blocks or escalations. |   2   | D/V  |
| 2.5.4 | Verify that abuse prevention logs are retained and reviewed for emerging attack patterns.                                |   3   |  V   |

---

## C2.6 Multi-Modal Input Validation

AI systems should incorporate robust validation for non-text inputs (images, audio, files) to prevent injection, evasion, or resource abuse.

|   #   | Description                                                                                                                                                                                                                          | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 2.6.1 | Verify that all non-text inputs (images, audio, files) are validated for type, size, and format before processing.                                                                                                                   |   1   |  D   |
| 2.6.2 | Ensure that files are scanned for malware and steganographic payloads before ingestion.                                                                                                                                              |   2   | D/V  |
| 2.6.3 | Ensure that image and audio inputs are verified for adversarial perturbations or recognized attack patterns.                                                                                                                         |   2   | D/V  |
| 2.6.4 | Ensure that multi-modal input validation failures are logged and generate alerts for investigation.                                                                                                                                  |   3   |  V   |
| 2.6.5 | Verify that cross-modal attack detection can identify coordinated attacks across multiple input types (e.g., steganographic payloads in images combined with prompt injection in text) using correlation rules and alert generation. |   2   | D/V  |
| 2.6.6 | Verify that multi-modal validation failures trigger detailed logging, including all input modalities, validation results, and threat scores.                                                                                         |   3   | D/V  |
---

## C2.7 Real-Time Adaptive Threat Detection

Developers should use advanced threat detection systems for AI that adapt to new attack patterns and offer real-time protection through compiled pattern matching.

|   #   | Description                                                                                                                                    | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 2.7.1 | Ensure that pattern matching (e.g., compiled regex) executes on all inputs with minimal latency impact.                                        |   1   | D/V  |
| 2.8.3 | Verify that adaptive detection models adjust their sensitivity based on recent attack activity and are updated with new patterns in real-time. |   2   | D/V  |
| 2.8.4 | Verify that detection accuracy improves through contextual analysis of user history, source, and session behavior.                             |   3   | D/V  |
| 2.8.5 | Verify that detection performance metrics (detection rate, false positive rate, processing latency) are continuously monitored and optimized.  |   3   | D/V  |

---

## References

* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

