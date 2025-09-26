## Frontispiece

### About the Standard

The Artificial Intelligence Security Verification Standard (AISVS) is a community‑driven catalogue of security requirements that data scientists, MLOps engineers, software architects, developers, testers, security professionals, tool vendors, regulators, and consumers can use to design, build, test, and verify trustworthy AI‑enabled systems and applications. It provides a common language for specifying security controls across the AI lifecycle—from data collection and model development to deployment and ongoing monitoring—so that organizations can measure and improve the resilience, privacy, and safety of their AI solutions.

### Copyright and License

Version 0.1 (First Public Draft - Work In Progress), 2025  

![license](images/license.png)
Copyright © 2025 The AISVS Project.  

Released under the Creative Commons Attribution‑ShareAlike 4.0 International License.
For any reuse or distribution, you must clearly communicate the license terms of this work to others.

### Project Leads

Jim Manico
Aras “Russ” Memisyazici

### Contributors and Reviewers

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS is a brand‑new standard created specifically to address the unique security challenges of artificial‑intelligence systems. While it draws inspiration from broader security best practices, every requirement in AISVS has been developed from the ground up to reflect the AI threat landscape and to help organizations build safer, more resilient AI solutions.
## Preface

Welcome to the Artificial Intelligence Security Verification Standard (AISVS) version 1.0!

### Introduction

Established in 2025 through a collaborative community effort, AISVS defines the security requirements to consider when designing, developing, deploying, and operating modern AI models, pipelines, and AI‑enabled services.

AISVS v1.0 represents the combined work of its project leads, working group, and wider community contributors to produce a pragmatic, testable baseline for securing AI systems.

Our goal with this release is to make AISVS straightforward to adopt while staying laser‑focused on its defined scope and addressing the rapidly evolving risk landscape unique to AI.

### Key Objectives for AISVS Version 1.0

Version 1.0 will be created with several guiding principles.

#### Well‑Defined Scope

Each requirement must align with AISVS’s name and mission:

Artificial Intelligence – Controls operate at the AI/ML layer (data, model, pipeline, or inference) and are the responsibility of AI practitioners.
Security – Requirements directly mitigate identified security, privacy, or safety risks.
Verification – Language is written so conformance can be objectively validated.
Standard – Sections follow a consistent structure and terminology to form a coherent reference.

---

By following AISVS, organizations can systematically evaluate and strengthen the security posture of their AI solutions, fostering a culture of secure AI engineering.
## Using the AISVS

The Artificial Intelligence Security Verification Standard (AISVS) defines security requirements for modern AI applications and services, focusing on aspects within the control of application developers.

The AISVS is intended for anyone developing or evaluating the security of AI applications, including developers, architects, security engineers, and auditors. This chapter introduces the structure and use of the AISVS, including its verification levels and intended use cases.

### Artificial Intelligence Security Verification Levels

The AISVS defines three ascending levels of security verification. Each level adds depth and complexity, enabling organizations to tailor their security posture to the risk level of their AI systems.

Organizations may begin at Level 1 and progressively adopt higher levels as security maturity and threat exposure increase.

#### Definition of the Levels

Each requirement in AISVS v1.0 is assigned to one of the following levels:

 Level 1 requirements

Level 1 includes the most critical and foundational security requirements. These focus on preventing common attacks that do not rely on other preconditions or vulnerabilities. Most Level 1 controls are either straightforward to implement or essential enough to justify the effort.

 Level 2 requirements

Level 2 addresses more advanced or less common attacks, as well as layered defenses against widespread threats. These requirements may involve more complex logic or target specific attack prerequisites.

 Level 3 requirements

Level 3 includes controls that are typically harder to implement or situational in applicability. These often represent defense-in-depth mechanisms or mitigations against niche, targeted, or high-complexity attacks.

#### Role (D/V)

Each AISVS requirement is marked according to the primary audience:

D – Developer-focused requirements
V – Verifier/auditor-focused requirements
D/V – Relevant to both developers and verifiers
## C1 Training Data Governance & Bias Management

### Control Objective

Training data must be sourced, handled, and maintained in a way that preserves provenance, security, quality, and fairness. Doing so fulfils legal duties and reduces risks of bias, poisoning, or privacy breaches that show up during training that could effect the entire AI lifecycle.

---

### C1.1 Training Data Provenance

Maintain a verifiable inventory of all datasets, accept only trusted sources, and log every change for auditability.

 #1.1.1    Level: 1    Role: D/V
 Verify that an up-to-date inventory of every training-data source (origin, steward/owner, licence, collection method, intended use constraints, and processing history) is maintained.
 #1.1.2    Level: 1    Role: D/V
 Verify that training data processes exclude unnecessary features, attributes, or fields (e.g., unused metadata, sensitive PII, leaked test data).
 #1.1.3    Level: 2    Role: D/V
 Verify that all dataset changes are subject to a logged approval workflow.
 #1.1.4    Level: 3    Role: D/V
 Verify that datasets or subsets are watermarked or fingerprinted where feasible.

---

### C1.2 Training Data Security & Integrity

Restrict access to training data, encrypt it at rest and in transit, and validate its integrity to prevent tampering, theft, or data poisoning.

 #1.2.1    Level: 1    Role: D/V
 Verify that access controls protect training data storage and pipelines.
 #1.2.2    Level: 2    Role: D/V
 Verify that all access to training data is logged, including user, time, and action.
 #1.2.3    Level: 2    Role: D/V
 Verify that training datasets are encrypted in transit and at rest, using industry-standard cryptographic algorithms and key management practices.
 #1.2.4    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are used to ensure data integrity during training data storage and transfer.
 #1.2.5    Level: 2    Role: D/V
 Verify that that automated detection techniques are applied to guard against unauthorized modifications or corruption of training data.
 #1.2.6    Level: 2    Role: D/V
 Verify that obsolete training data is securely purged or anonymized.
 #1.2.7    Level: 3    Role: D/V
 Verify that all training dataset versions are uniquely identified, stored immutably, and auditable to support rollback and forensic analysis.

---

### C1.3 Training Data Labeling Quality, Integrity, and Security

Protect labels and require technical review for critical data.

 #1.3.1    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are applied to label artifacts to ensure their integrity and authenticity.
 #1.3.2    Level: 2    Role: D/V
 Verify that labeling interfaces and platforms enforce strong access controls, maintain tamper-evident audit logs of all labeling activities, and protect against unauthorized modifications.
 #1.3.3    Level: 3    Role: D/V
 Verify that sensitive information in labels is redacted, anonymized, or encrypted at the data field level at rest and in transit.

---

### C1.4 Training Data Quality and Security Assurance

Combine automated validation, manual spot-checks, and logged remediation to guarantee dataset reliability.

 #1.4.1    Level: 1    Role: D
 Verify that automated tests catch format errors amd nulls on every ingest or significant data transformation.
 #1.4.2    Level: 2    Role: D/V
 Verify that LLM training and fine-tuning pipelines implement poisoning detection & data integrity validation (e.g., statistical methods, outlier detection, embedding analysis) to identify potential poisoning attacks (e.g., label flipping, backdoor trigger insertion, role-switching commands, influential instance attacks) or unintentional data corruption in training data.
 #1.4.3    Level: 2    Role: D/V
 Verify that automatically generated labels (e.g., via LLMs or weak supervision) are subject to confidence thresholds and consistency checks to detect hallucinated, misleading, or low-confidence labels.
 #1.4.4    Level: 3    Role: D/V
 Verify that appropriate defenses, such as adversarial training (using generated adversarial examples), data augmentation with perturbed inputs, or robust optimization techniques, are implemented and tuned for relevant models based on risk assessment.
 #1.4.5    Level: 3    Role: D
 Verify that automated tests catch label skews on every ingest or significant data transformation.

---

### C1.5 Data Lineage and Traceability

Track the full journey of each data point from source to model input for auditability and incident response.

 #1.5.1    Level: 2    Role: D/V
 Verify that the lineage of each data point, including all transformations, augmentations, and merges, is recorded and can be reconstructed.
 #1.5.2    Level: 2    Role: D/V
 Verify that lineage records are immutable, securely stored, and accessible for audits.
 #1.5.3    Level: 2    Role: D/V
 Verify that lineage tracking covers synthetic data generated via privacy-preserving or generative techniques and that all synthetic data is clearly labeled and distinguishable from real data throughout the pipeline.

---

### References

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
MITRE ATLAS: Adversary Tactics for AI
Survey of ML Bias Mitigation Techniques – MDPI
Data Provenance & Lineage Best Practices – Nightfall AI
Data Labeling Quality Standards – LabelYourData
Training Data Poisoning Guide – Lakera.ai
CISA Advisory: Securing Data for AI Systems
ISO/IEC 23053: AI Management Systems Framework
IBM: What is AI Governance?
Google AI Principles
GDPR & AI Training Data – DataProtectionReport
Supply-Chain Security for AI Data – AppSOC
OpenAI Privacy Center – Data Deletion Controls
Adversarial ML Dataset – Kaggle
## C2 User Input Validation

### Control Objective

Robust validation of user input is a first-line defense against some of the most damaging attacks on AI systems. Prompt injection attacks can override system instructions, leak sensitive data, or steer the model toward behavior that is not allowed. Unless dedicated filters and other validation is in place, research shows that jailbreaks that exploit context windows will continue to be effective.

---

### C2.1 Prompt Injection Defense

Prompt injection is one of the top risks for AI systems. Defenses against this tactic employ a combination of pattern filters, data classifiers and instruction hierarchy enforcement.

 #2.1.1    Level: 1    Role: D/V
 Verify that user inputs are screened against a continuously updated library of known prompt injection patterns. These include jailbreak keywords, "ignore previous" and role-play chains.
 #2.1.2    Level: 1    Role: D/V
 Verify that the system enforces an instruction hierarchy in which system messages override user instructions, even after processing user instructions.
 #2.1.4    Level: 2    Role: D
 Verify that prompts originating from third-party content (web pages, PDFs, emails) are sanitized in isolation before being concatenated into the main prompt.

---

### C2.2 Adversarial-Example Resistance

Natural Language Processing (NLP) models are still vulnerable to subtle character or word-level perturbations that humans often miss but models tend to misclassify.

 #2.2.1    Level: 1    Role: D
 Verify that basic input normalization steps (Unicode NFC, homoglyph mapping, whitespace trimming) run before tokenization.
 #2.2.2    Level: 2    Role: D/V
 Verify that statistical anomaly detection flags inputs with unusually high edit distance to language norms or abnormal embedding distances.
 #2.2.3    Level: 2    Role: D
 Verify that the inference pipeline supports adversarial-training–hardened model variants or defense layers (e.g., randomization, defensive distillation, alignment checks) for high-risk endpoints.
 #2.2.4    Level: 2    Role: V
 Verify that suspected adversarial inputs are quarantined, and logged with full payloads.
 #2.2.5    Level: 2    Role: D/V
 Verify that that encoding and representation smuggling in both inputs and outputs (e.g., invisible Unicode/control characters, homoglyph swaps, or mixed-direction text) are detected and mitigated. Approved mitigations include canonicalization, strict schema validation, policy-based rejection, or explicit marking.

---

### C2.3 Schema, Type & Length Validation

AI attacks featuring malformed or oversized inputs can cause parsing errors, prompt spillage across fields, and resource exhaustion.  Strict schema enforcement is also a prerequisite when performing deterministic tool calls.

 #2.3.1    Level: 1    Role: D
 Verify that every API or function call endpoint defines an explicit input schema (JSON Schema, Protobuf or multimodal equivalent) and that inputs are validated before prompt assembly.
 #2.3.2    Level: 1    Role: D/V
 Verify that inputs exceeding maximum token or byte limits are rejected with a safe error and never silently truncated.
 #2.3.3    Level: 2    Role: D/V
 Verify that type checks (e.g., numeric ranges, enum values, MIME types for images/audio) are enforced server-side.
 #2.3.4    Level: 2    Role: D
 Verify that semantic validators (e.g., JSON Schema) run in constant time to prevent algorithmic DoS.
 #2.3.5    Level: 3    Role: V
 Verify that validation failures are logged with redacted payload snippets and unambiguous error codes to aid security triage.

---

### C2.4 Content & Policy Screening

Developers should be able to detect syntactically valid prompts that request disallowed content (such as illicit instructions, hate speech, and/or copyrighted text) then prevent them from propagating.

 #2.4.1    Level: 1    Role: D
 Verify that a content classifier (zero shot or fine tuned) scores every input for violence, self-harm, hate, sexual content and illegal requests, with configurable thresholds.
 #2.4.2    Level: 1    Role: D/V
 Verify that inputs which violate policies will receive standardized refusals or safe completions so they will not propagate to downstream LLM calls.
 #2.4.3    Level: 2    Role: D
 Verify that screening respects user-specific policies (age, regional legal constraints) via attribute-based rules resolved at request time.
 #2.4.4    Level: 3    Role: V
 Verify that screening logs include classifier confidence scores and policy category tags for SOC correlation and future red-team replay.

---

### C2.5 Input Rate Limiting & Abuse Prevention

Developers should prevent abuse, resource exhaustion, and automated attacks against AI systems by limiting input rates and detecting anomalous usage patterns.

 #2.5.1    Level: 1    Role: D/V
 Verify that per-user, per-IP, and per-API-key rate limits are enforced for all input endpoints.
 #2.5.2    Level: 2    Role: D/V
 Verify that burst and sustained rate limits are tuned to prevent DoS and brute force attacks.
 #2.5.3    Level: 2    Role: D/V
 Verify that anomalous usage patterns (e.g., rapid-fire requests, input flooding) trigger automated blocks or escalations.
 #2.5.4    Level: 3    Role: V
 Verify that abuse prevention logs are retained and reviewed for emerging attack patterns.

---

### C2.6 Multi-Modal Input Validation

AI systems should include robust validation for non-textual inputs (images, audio, files) to prevent injection, evasion, or resource abuse.

 #2.6.1    Level: 1    Role: D
 Verify that all non-text inputs (images, audio, files) are validated for type, size, and format before processing.
 #2.6.2    Level: 2    Role: D/V
 Verify that files are scanned for malware and steganographic payloads before ingestion.
 #2.6.3    Level: 2    Role: D/V
 Verify that image/audio inputs are checked for adversarial perturbations or known attack patterns.
 #2.6.4    Level: 3    Role: V
 Verify that multi-modal input validation failures are logged and trigger alerts for investigation.
 #2.6.5    Level: 2    Role: D/V
 Verify that cross-modal attack detection identifies coordinated attacks spanning multiple input types (e.g., steganographic payloads in images combined with prompt injection in text) with correlation rules and alert generation.
 #2.6.6    Level: 3    Role: D/V
 Verify that multi-modal validation failures trigger detailed logging including all input modalities, validation results and threat scores.
---

### C2.7 Real-Time Adaptive Threat Detection

Developers should employ advanced threat detection systems for AI that adapt to new attack patterns and provide real-time protection with compiled pattern matching.

 #2.7.1    Level: 1    Role: D/V
 Verify that pattern matching (e.g., compiled regex) runs on all inputs with minimal latency impact.
 #2.8.3    Level: 2    Role: D/V
 Verify that adaptive detection models adjust sensitivity based on recent attack activity and are updated with new patterns in real time.
 #2.8.4    Level: 3    Role: D/V
 Verify that detection accuracy is improved via contextual analysis of user history, source, and session behavior.
 #2.8.5    Level: 3    Role: D/V
 Verify that detection performance metrics (detection rate, false positive rate, processing latency) are continuously monitored and optimized.

---

### References

Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection
## C3 Model Lifecycle Management & Change Control

### Control Objective

AI systems must implement change control processes that prevent unauthorized or unsafe model modifications from reaching production. This control ensures model integrity through the entire lifecycle--from development through deployment to decommissioning--which enables rapid incident response and maintains accountability for all changes.

Core Security Goal: Only authorized, validated models reach production by employing controlled processes that maintain integrity, traceability, and recoverability.

---

### C3.1 Model Authorization & Integrity

Only authorized models with verified integrity reach production environments.

 #3.1.1    Level: 1    Role: D/V
 Verify that all model artifacts (weights, configurations, tokenizers) are cryptographically signed by authorized entities before deployment.
 #3.1.2    Level: 2    Role: V
 Verify that dependency tracking maintains a real-time inventory that enables identification of all consuming systems.
 #3.1.3    Level: 3    Role: D/V
 Verify that model provenance records include an authorizing entity's identity, training data checksums, validation test results with pass/fail status, and a creation timestamp.

---

### C3.2 Model Validation & Testing

Models must pass defined security and safety validations before deployment.

 #3.2.1    Level: 1    Role: D/V
 Verify that models undergo automated security testing that includes input validation, output sanitization, and safety evaluations with pre-agreed organizational pass/fail thresholds before deployment.
 #3.2.2    Level: 1    Role: V
 Verify that all model changes (deployment, configuration, retirement) generate immutable audit records including a timestamp, an authenticated actor identity, a change type, and before/after states.
 #3.2.3    Level: 2    Role: D/V
 Verify that validation failures automatically block model deployment after explicit override approval from pre-designated authorized personnel with documented business justifications.

---

### C3.3 Controlled Deployment & Rollback

Model deployments must be controlled, monitored, and reversible.

 #3.3.1    Level: 1    Role: D/V
 Verify that deployment processes validate cryptographic signatures and compute integrity checksums before model activation, failing deployment on any mismatch.
 #3.3.2    Level: 1    Role: D
 Verify that production deployments implement gradual rollout mechanisms (canary deployments, blue-green deployments) with automated rollback triggers based on pre-agreed error rates, latency thresholds, or security alert criteria.
 #3.3.3    Level: 2    Role: D/V
 Verify that rollback capabilities restore the complete model state (weights, configurations, dependencies) atomically.
 #3.3.4    Level: 3    Role: D/V
 Verify that emergency model shutdown capabilities can disable model endpoints within pre-defined response.

---

### C3.4 Secure Development Practices

Model development and training processes must follow secure practices to prevent compromise.

 #3.4.1    Level: 1    Role: D/V
 Verify that model development, testing, and production environments are physically or logically separated. They have no shared infrastructure, distinct access controls, and isolated data stores.
 #3.4.2    Level: 1    Role: D
 Verify that model development artifacts (hyperparameters, training scripts, configuration files, prompt templates etc) are stored in version control and require peer review approval before use in training.
 #3.4.3    Level: 2    Role: D/V
 Verify that model training and fine-tuning occur in isolated environments with controlled network access.
 #3.4.4    Level: 2    Role: D
 Verify that training data sources are validated through integrity checks and authenticated via trusted sources with documented chain of custody before use in model development.

---

### C3.5 Model Retirement & Decommissioning

Models must be securely retired when they are no longer needed or when security issues are identified.

 #3.5.1    Level: 1    Role: D/V
 Verify that retired model artifacts are securely wiped using secure cryptographic erasure.
 #3.5.2    Level: 2    Role: V
 Verify that model retirement events are logged with timestamp and actor identity, and model signatures are revoked to prevent reuse.

---

### References

MLOps Principles
Securing AI/ML Ops – Cisco.com
Audit logs security: cryptographically signed tamper-proof logs
Machine Learning Model Versioning: Top Tools & Best Practices
AI Hygiene Starts with Models and Data Loaders – SEI Blog
How to handle versioning and rollback of a deployed ML model?
Reinforcement fine-tuning – OpenAI API
Auditing Machine Learning models: Governance, Data Security and …
Adversarial Training to Improve Model Robustness
What is AI adversarial robustness? – IBM Research
Exploring Data Provenance: Ensuring Data Integrity and Authenticity
MITRE ATLAS
AWS Prescriptive Guidance – Best practices for retiring applications …
