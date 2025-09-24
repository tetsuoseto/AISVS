# C2 User Input Validation

## Control Objective

Robust validation of user input is a first-line defense against some of the most damaging attacks on AI systems. Prompt injection attacks can override system instructions, leak sensitive data, or steer the model toward behavior that is not allowed. Unless dedicated filters and other validation is in place, research shows that jailbreaks that exploit context windows will continue to be effective.

---

## C2.1 Prompt Injection Defense

Prompt injection is one of the top risks for AI systems. Defenses against this tactic employ a combination of pattern filters, data classifiers and instruction hierarchy enforcement.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **2.1.1** | **Verify that** user inputs are screened against a continuously updated library of known prompt injection patterns. These include jailbreak keywords, "ignore previous" and role-play chains. | 1 |  D/V |
| **2.1.2** | **Verify that** the system enforces an instruction hierarchy in which system messages override user instructions, even after processing user instructions. | 1 |  D/V |
| **2.1.4** | **Verify that** prompts originating from third-party content (web pages, PDFs, emails) are sanitized in isolation before being concatenated into the main prompt. | 2 | D |

---

## C2.2 Adversarial-Example Resistance

Natural Language Processing (NLP) models are still vulnerable to subtle character or word-level perturbations that humans often miss but models tend to misclassify.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **2.2.1** | **Verify that** basic input normalization steps (Unicode NFC, homoglyph mapping, whitespace trimming) run before tokenization. | 1 | D |
| **2.2.2** | **Verify that** statistical anomaly detection flags inputs with unusually high edit distance to language norms or abnormal embedding distances. | 2 |  D/V |
| **2.2.3** | **Verify that** the inference pipeline supports adversarial-training–hardened model variants or defense layers (e.g., randomization, defensive distillation, alignment checks) for high-risk endpoints. | 2 | D |
| **2.2.4** | **Verify that** suspected adversarial inputs are quarantined, and logged with full payloads.  | 2 | V |
| **2.2.5** | **Verify that** that encoding and representation smuggling in both inputs and outputs (e.g., invisible Unicode/control characters, homoglyph swaps, or mixed-direction text) are detected and mitigated. Approved mitigations include canonicalization, strict schema validation, policy-based rejection, or explicit marking. | 2 | D/V |

---

## C2.3 Schema, Type & Length Validation

AI attacks featuring malformed or oversized inputs can cause parsing errors, prompt spillage across fields, and resource exhaustion.  Strict schema enforcement is also a prerequisite when performing deterministic tool calls.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **2.3.1** | **Verify that** every API or function call endpoint defines an explicit input schema (JSON Schema, Protobuf or multimodal equivalent) and that inputs are validated before prompt assembly. | 1 | D |
| **2.3.2** | **Verify that** inputs exceeding maximum token or byte limits are rejected with a safe error and never silently truncated. | 1 |  D/V |
| **2.3.3** | **Verify that** type checks (e.g., numeric ranges, enum values, MIME types for images/audio) are enforced server-side. | 2 |  D/V |
| **2.3.4** | **Verify that** semantic validators (e.g., JSON Schema) run in constant time to prevent algorithmic DoS. | 2 | D |
| **2.3.5** | **Verify that** validation failures are logged with redacted payload snippets and unambiguous error codes to aid security triage. | 3 | V |

---

## C2.4 Content & Policy Screening

Developers should be able to detect syntactically valid prompts that request disallowed content (such as illicit instructions, hate speech, and/or copyrighted text) then prevent them from propagating.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **2.4.1** | **Verify that** a content classifier (zero shot or fine tuned) scores every input for violence, self-harm, hate, sexual content and illegal requests, with configurable thresholds. | 1 | D |
| **2.4.2** | **Verify that** inputs which violate policies will receive standardized refusals or safe completions so they will not propagate to downstream LLM calls. | 1 |  D/V |
| **2.4.3** | **Verify that** screening respects user-specific policies (age, regional legal constraints) via attribute-based rules resolved at request time.  | 2 | D |
| **2.4.4** | **Verify that** screening logs include classifier confidence scores and policy category tags for SOC correlation and future red-team replay. | 3 | V |

---

## C2.5 Input Rate Limiting & Abuse Prevention

Developers should prevent abuse, resource exhaustion, and automated attacks against AI systems by limiting input rates and detecting anomalous usage patterns.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **2.5.1** | **Verify that** per-user, per-IP, and per-API-key rate limits are enforced for all input endpoints. | 1 | D/V |
| **2.5.2** | **Verify that** burst and sustained rate limits are tuned to prevent DoS and brute force attacks. | 2 | D/V |
| **2.5.3** | **Verify that** anomalous usage patterns (e.g., rapid-fire requests, input flooding) trigger automated blocks or escalations. | 2 | D/V |
| **2.5.4** | **Verify that** abuse prevention logs are retained and reviewed for emerging attack patterns. | 3 | V |

---

## C2.6 Multi-Modal Input Validation

AI systems should include robust validation for non-textual inputs (images, audio, files) to prevent injection, evasion, or resource abuse.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **2.6.1** | **Verify that** all non-text inputs (images, audio, files) are validated for type, size, and format before processing. | 1 | D |
| **2.6.2** | **Verify that** files are scanned for malware and steganographic payloads before ingestion. | 2 | D/V |
| **2.6.3** | **Verify that** image/audio inputs are checked for adversarial perturbations or known attack patterns. | 2 | D/V |
| **2.6.4** | **Verify that** multi-modal input validation failures are logged and trigger alerts for investigation. | 3 | V |
| **2.6.5** | **Verify that** cross-modal attack detection identifies coordinated attacks spanning multiple input types (e.g., steganographic payloads in images combined with prompt injection in text) with correlation rules and alert generation. | 2 | D/V |
| **2.6.6** | **Verify that** multi-modal validation failures trigger detailed logging including all input modalities, validation results and threat scores. | 3 | D/V |
---

## C2.7 Real-Time Adaptive Threat Detection

Developers should employ advanced threat detection systems for AI that adapt to new attack patterns and provide real-time protection with compiled pattern matching.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **2.7.1** | **Verify that** pattern matching (e.g., compiled regex) runs on all inputs with minimal latency impact. | 1 | D/V |
| **2.8.3** | **Verify that** adaptive detection models adjust sensitivity based on recent attack activity and are updated with new patterns in real time. | 2 | D/V |
| **2.8.4** | **Verify that** detection accuracy is improved via contextual analysis of user history, source, and session behavior. | 3 | D/V |
| **2.8.5** | **Verify that** detection performance metrics (detection rate, false positive rate, processing latency) are continuously monitored and optimized. | 3 | D/V |

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
