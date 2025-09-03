## Frontispiece

### About the Standard

The Artificial Intelligence Security Verification Standard (AISVS) is a community-driven catalog of security requirements that data scientists, MLOps engineers, software architects, developers, testers, security professionals, tool vendors, regulators, and consumers can use to design, build, test, and verify trustworthy AI-enabled systems and applications. It provides a common language for specifying security controls across the AI lifecycle—from data collection and model development to deployment and ongoing monitoring—enabling organizations to measure and improve the resilience, privacy, and safety of their AI solutions.

### Copyright and License

Version 0.1 (First Public Draft - Work In Progress), 2025  

![license](images/license.png)
Copyright © 2025 The AISVS Project.  

Released under theCreative Commons Attribution‑ShareAlike 4.0 International License.
If you reuse or distribute this work, you must clearly communicate its license terms to others.

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

AISVS is a brand‑new standard designed specifically to address the unique security challenges of artificial‑intelligence systems. While it draws inspiration from broader security best practices, every AISVS requirement has been developed from the ground up to reflect the AI threat landscape and to help organizations build safer, more resilient AI solutions.

## Preface

Welcome to the Artificial Intelligence Security Verification Standard (AISVS) version 1.0!

### Introduction

Established in 2025 through a collaborative community effort, AISVS defines the security requirements to be considered when designing, developing, deploying, and operating modern AI models, pipelines, and AI‑enabled services.

AISVS v1.0 represents the combined effort of its project leads, the working group, and the wider community of contributors to produce a pragmatic, testable baseline for securing AI systems.

Our goal with this release is to make AISVS straightforward to adopt while staying laser‑focused on its defined scope and addressing the rapidly evolving risk landscape unique to AI.

### Key Objectives for AISVS Version 1.0

Version 1.0 will be created based on several guiding principles.

#### Well‑Defined Scope

Each requirement must align with AISVS's name and mission:

Artificial intelligence – controls operate at the AI/ML layer (data, model, pipeline, or inference) and are the responsibility of AI practitioners.
Security – requirements directly mitigate identified security, privacy, or safety risks.
Verification – Language is written so that conformance can be objectively validated.
Standards – Sections follow a consistent structure and terminology to form a coherent reference.
​
---

By following AISVS, organizations can systematically assess and strengthen the security posture of their AI solutions, fostering a culture of secure AI engineering.

## Using AISVS.

The Artificial Intelligence Security Verification Standard (AISVS) defines security requirements for modern AI applications and services, focusing on aspects that are within the control of application developers.

The AISVS is intended for anyone developing or evaluating the security of AI applications, including developers, architects, security engineers, and auditors. This chapter explains the structure and use of the AISVS, including its verification levels and intended use cases.

### Artificial Intelligence Security Verification Levels

The AISVS defines three progressively higher levels of security verification.

Organizations may start at Level 1 and progressively adopt higher levels as their security maturity and threat exposure increase.

#### Definitions of the Levels

Each requirement in AISVS v1.0 is assigned to one of the following levels:

 Level 1 requirements

Level 1 includes the most critical and foundational security requirements. These focus on preventing common attacks that do not rely on other preconditions or vulnerabilities. Most Level 1 controls are straightforward to implement or are essential enough to justify the effort.

 Level 2 requirements

Level 2 addresses more advanced or less common attacks, as well as layered defenses against widespread threats. These requirements may involve more complex logic or target specific prerequisites for attacks.

 Level 3 requirements.

Level 3 includes controls that are typically harder to implement or have situational applicability. These controls often represent defense-in-depth mechanisms or mitigations against niche, targeted, or highly complex attacks.

#### Role (D/V)

Each AISVS requirement is marked according to its primary audience:

D – Developer-Focused Requirements
V – Verifier/auditor-focused requirements
D/V – Relevant to both developers and verifiers

## C1 Training Data Governance and Bias Management

### Control Objective

Training data must be sourced, handled, and maintained in a way that preserves provenance, security, quality, and fairness. Doing so fulfills legal duties and reduces the risks of bias, poisoning, or privacy breaches that arise during training, which could affect the entire AI lifecycle.

---

### C1.1 Training Data Provenance

Maintain a verifiable inventory of all datasets, accept only trusted sources, and log every change for auditability.

 #1.1.1    Level: 1    Role: D/V
 Verify that an up-to-date inventory of every training-data source (origin, steward/owner, license, collection method, intended use constraints, and processing history) is maintained.
 #1.1.2    Level: 1    Role: D/V
 Verify that training data processing excludes unnecessary features, attributes, or fields (e.g., unused metadata, sensitive PII, leaked test data).
 #1.1.3    Level: 2    Role: D/V
 Verify that all dataset changes are subject to a logged approval workflow.
 #1.1.4    Level: 3    Role: D/V
 Verify that datasets or subsets are watermarked or fingerprinted where feasible.

---

### C1.2 Training Data Security and Integrity

Restrict access to training data, encrypt it at rest and in transit, and validate its integrity to prevent tampering, theft, or data poisoning.

 #1.2.1    Level: 1    Role: D/V
 Verify that access controls protect training data storage and pipelines.
 #1.2.2    Level: 2    Role: D/V
 Verify that all access to training data is logged, including the user, the timestamp, and the action.
 #1.2.3    Level: 2    Role: D/V
 Verify that training datasets are encrypted in transit and at rest, using industry-standard cryptographic algorithms and robust key-management practices.
 #1.2.4    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are used to ensure data integrity during the storage and transfer of training data.
 #1.2.5    Level: 2    Role: D/V
 Verify that automated detection techniques are applied to guard against unauthorized modifications or corruption of training data.
 #1.2.6    Level: 2    Role: D/V
 Verify that obsolete training data have been securely purged or anonymized.
 #1.2.7    Level: 3    Role: D/V
 Verify that all training dataset versions are uniquely identified, stored immutably, and auditable to support rollback and forensic analysis.

---

### C1.3 Training Data Labeling Quality, Integrity, and Security

Protect labels and require a technical review for critical data.

 #1.3.1    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are applied to label artifacts to ensure their integrity and authenticity.
 #1.3.2    Level: 2    Role: D/V
 Verify that labeling interfaces and platforms enforce strong access controls, maintain tamper-evident audit logs of all labeling activities, and protect against unauthorized modifications.
 #1.3.3    Level: 3    Role: D/V
 Verify that sensitive information in labels is redacted, anonymized, or encrypted at the data field level, both at rest and in transit.

---

### C1.4 Training Data Quality and Security Assurance

Combine automated validation, manual spot-checks, and logged remediation to ensure dataset reliability.

 #1.4.1    Level: 1    Role: D
 Verify that automated tests catch formatting errors and null values at every ingestion or significant data transformation.
 #1.4.2    Level: 2    Role: D/V
 Verify that LLM training and fine-tuning pipelines implement poisoning detection and data integrity validation (for example, statistical methods, outlier detection, and embedding analysis) to identify potential poisoning attacks (such as label flipping, backdoor trigger insertion, role-switching commands, and influential instance attacks) or unintentional data corruption in training data.
 #1.4.3    Level: 3    Role: D/V
 Verify that appropriate defenses, such as adversarial training (using generated adversarial examples), data augmentation with perturbed inputs, or robust optimization techniques, are implemented and tuned for the relevant models based on risk assessment.
 #1.4.4    Level: 2    Role: D/V
 Verify that automatically generated labels (for example, generated by LLMs or through weak supervision) are subjected to confidence thresholds and consistency checks to detect hallucinated, misleading, or low-confidence labels.
 #1.4.5    Level: 3    Role: D
 Verify that automated tests catch label skew during every ingest or significant data transformation.

---

### C1.5 Data Lineage and Traceability

Track the full journey of each data point from its source to its model input to support auditability and incident response.

 #1.5.1    Level: 2    Role: D/V
 Verify that the lineage of each data point, including all transformations, augmentations, and merges, is recorded and can be reconstructed.
 #1.5.2    Level: 2    Role: D/V
 Verify that lineage records are immutable, securely stored, and accessible for audits.
 #1.5.3    Level: 2    Role: D/V
 Verify that lineage tracking covers synthetic data generated through privacy-preserving or generative techniques, and that all synthetic data is clearly labeled and distinguishable from real data throughout the pipeline.

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

Robust validation of user input is a first line of defense against some of the most damaging attacks on AI systems. Prompt injection attacks can override system instructions, leak sensitive data, or steer the model toward behavior that is not allowed. Unless dedicated filters and instruction hierarchies are in place, research shows that "multi-shot" jailbreaks that exploit very long context windows will be effective. Additionally, subtle adversarial perturbation attacks--such as homoglyph swaps or leetspeak—-can silently change a model's decisions.

---

### C2.1 Prompt Injection Defense

Prompt injection is one of the top risks for AI systems. Defenses against this tactic employ a combination of static pattern filters, dynamic classifiers, and instruction hierarchy enforcement.

 #2.1.1    Level: 1    Role: D/V
 Verify that user inputs are screened against a continuously updated library of known prompt injection patterns (jailbreak keywords, "ignore previous", role-play chains, indirect HTML/URL attacks).
 #2.1.2    Level: 1    Role: D/V
 Verify that the system enforces an instruction hierarchy in which system or developer messages override user instructions, even after the context window has expanded.
 #2.1.3    Level: 2    Role: D/V
 Verify that adversarial evaluation tests (e.g., the Red Team "many-shot" prompts) are run before every model or prompt-template release, with success-rate thresholds and automated blockers to prevent regressions.
 #2.1.4    Level: 2    Role: D
 Verify that prompts originating from third-party content (web pages, PDFs, emails) are sanitized in an isolated parsing context before they are concatenated into the main prompt.
 #2.1.5    Level: 3    Role: D/V
 Verify that all prompt-filter rule updates, classifier model versions, and block-list changes are version-controlled and auditable.

---

### C2.2 Adversarial-Example Resistance

Natural Language Processing (NLP) models remain vulnerable to subtle character- or word-level perturbations that humans often miss, but models tend to misclassify them.

 #2.2.1    Level: 1    Role: D
 Verify that basic input normalization steps (Unicode NFC, homoglyph mapping, whitespace trimming) run before tokenization.
 #2.2.2    Level: 2    Role: D/V
 Verify that statistical anomaly detection flags inputs that have an unusually high edit distance from language norms, excessive repetition of tokens, or abnormal embedding distances.
 #2.2.3    Level: 2    Role: D
 Verify that the inference pipeline supports optional adversarial-training–hardened model variants or defense layers (e.g., randomization, defensive distillation) for high-risk endpoints.
 #2.2.4    Level: 2    Role: V
 Verify that suspected adversarial inputs are quarantined and logged with full payloads (after PII redaction).
 #2.2.5    Level: 3    Role: D/V
 Verify that robustness metrics (the success rate of known attack suites) are tracked over time, and that regressions trigger a release blocker.

---

### C2.3 Schema, Type, and Length Validation

AI attacks that feature malformed or oversized inputs can cause parsing errors, prompt spillage across fields, and exhaust resources.  Strict schema enforcement is also a prerequisite when performing deterministic tool calls.

 #2.3.1    Level: 1    Role: D
 Verify that every API or function call endpoint defines an explicit input schema (JSON Schema, Protobuf, or a multimodal equivalent) and that inputs are validated before prompt assembly.
 #2.3.2    Level: 1    Role: D/V
 Verify that inputs exceeding the maximum token or byte limits are rejected with a safe error and are never silently truncated.
 #2.3.3    Level: 2    Role: D/V
 Verify that type checks (e.g., numeric ranges, enum values, and MIME types for images and audio) are enforced server-side, not only in client code.
 #2.3.4    Level: 2    Role: D
 Verify that semantic validators, such as JSON Schema, run in constant time to prevent algorithmic DoS.
 #2.3.5    Level: 3    Role: V
 Ensure that validation failures are logged with redacted payload snippets and unambiguous error codes to aid security triage.

---

### C2.4 Content & Policy Screening

Developers should be able to detect syntactically valid prompts that request disallowed content, such as illicit instructions, hate speech, or copyrighted text, and then prevent them from propagating.

 #2.4.1    Level: 1    Role: D
 Verify that a content classifier (zero-shot or fine-tuned) scores every input for violence, self-harm, hate, sexual content, and illegal requests, with configurable thresholds.
 #2.4.2    Level: 1    Role: D/V
 Verify that inputs that violate policies receive standardized refusals or safe completions so they do not propagate to downstream LLM calls.
 #2.4.3    Level: 2    Role: D
 Verify that the screening model or rule set is retrained or updated at least quarterly, incorporating newly observed jailbreak or policy bypass patterns.
 #2.4.4    Level: 2    Role: D
 Verify that screening complies with user-specific policies (age and regional legal constraints) via attribute-based rules resolved at request time.
 #2.4.5    Level: 3    Role: V
 Verify that screening logs include classifier confidence scores and policy category tags for SOC correlation and future red-team replay.

---

### C2.5 Input Rate Limiting and Abuse Prevention

Developers should prevent abuse, resource exhaustion, and automated attacks on AI systems by limiting input rates and detecting anomalous usage patterns.

 #2.5.1    Level: 1    Role: D/V
 Verify that rate limits per user, per IP address, and per API key are enforced for all input endpoints.
 #2.5.2    Level: 2    Role: D/V
 Verify that burst and sustained rate limits are tuned to prevent DoS and brute-force attacks.
 #2.5.3    Level: 2    Role: D/V
 Verify that anomalous usage patterns (e.g., rapid-fire requests and input flooding) trigger automated blocks or escalations.
 #2.5.4    Level: 3    Role: V
 Verify that abuse-prevention logs are retained and reviewed for emerging attack patterns.

---

### C2.6 Multi-Modal Input Validation

AI systems should implement robust validation for non-textual inputs (images, audio, and files) to prevent injection, evasion, or resource abuse.

 #2.6.1    Level: 1    Role: D
 Verify that all non-text inputs (images, audio, and files) are validated for type, size, and format before processing.
 #2.6.2    Level: 2    Role: D/V
 Verify that files are scanned for malware and steganographic payloads prior to ingestion.
 #2.6.3    Level: 2    Role: D/V
 Verify that image or audio inputs are checked for adversarial perturbations or known attack patterns.
 #2.6.4    Level: 3    Role: V
 Verify that multi-modal input validation failures are logged and that alerts are triggered for investigation.

---

### C2.7 Input Provenance and Attribution

AI systems should support auditing, abuse tracking, and compliance by monitoring and tagging the origins of all user inputs.

 #2.7.1    Level: 1    Role: D/V
 Verify that all user inputs are tagged with metadata (user ID, session, source, timestamp, IP address) during ingestion.
 #2.7.2    Level: 2    Role: D/V
 Verify that provenance metadata is retained and auditable for all processed inputs.
 #2.7.3    Level: 2    Role: D/V
 Verify that anomalous or untrusted input sources are flagged and subjected to enhanced scrutiny or blocked.

---

### C2.8 Real-Time Adaptive Threat Detection

Developers should employ advanced threat-detection systems for AI that adapt to evolving attack patterns and provide real-time protection through compiled pattern matching.

 #2.8.1    Level: 1    Role: D/V
 Verify that threat detection patterns are compiled into optimized regex engines for high-performance real-time filtering with minimal latency impact.
 #2.8.2    Level: 1    Role: D/V
 Verify that threat-detection systems maintain separate pattern libraries for different threat categories (prompt injection, harmful content, sensitive data, and system commands).
 #2.8.3    Level: 2    Role: D/V
 Verify that adaptive threat detection uses machine learning models that adjust threat sensitivity based on attack frequency and success rates.
 #2.8.4    Level: 2    Role: D/V
 Verify that real-time threat intelligence feeds automatically update pattern libraries with new attack signatures and IOCs (Indicators of Compromise).
 #2.8.5    Level: 3    Role: D/V
 Verify that threat detection false positive rates are continuously monitored and that pattern specificity is automatically tuned to minimize interference with legitimate use cases.
 #2.8.6    Level: 3    Role: D/V
 Verify that contextual threat analysis takes input source, user behavior patterns, and session history into account to improve detection accuracy.
 #2.8.7    Level: 3    Role: D/V
 Verify that threat detection performance metrics (detection rate, processing latency, and resource utilization) are monitored and optimized in real-time.

---

### C2.9 Multi-Modal Security Validation Pipeline

Developers should implement security validation for text, image, audio, and other AI input modalities, using specific threat-detection techniques and resource isolation.

 #2.9.1    Level: 1    Role: D/V
 Verify that each input modality has dedicated security validators with documented threat patterns (text: prompt injection; images: steganography; audio: spectrogram attacks) and defined detection thresholds.
 #2.9.2    Level: 2    Role: D/V
 Verify that multi-modal inputs are processed in isolated sandboxes with defined resource limits (memory, CPU, and processing time) that are specific to each modality type and documented in security policies.
 #2.9.3    Level: 2    Role: D/V
 Verify that cross-modal attack detection identifies coordinated attacks spanning multiple input types (e.g., steganographic payloads in images combined with prompt injection in text) using correlation rules and alert generation.
 #2.9.4    Level: 3    Role: D/V
 Verify that multi-modal validation failures trigger detailed logging, including all input modalities, validation results, threat scores, and correlation analysis, using structured log formats suitable for SIEM integration.
 #2.9.5    Level: 3    Role: D/V
 Verify that modality-specific content classifiers are updated according to documented schedules (minimum quarterly) with new threat patterns, adversarial examples, and performance benchmarks maintained above baseline thresholds.

---

### References

LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security
Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
$PDF$ OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
Easily enforcing valid JSON schema following – API
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## C3 Model Lifecycle Management and Change Control

### Control Objective

AI systems must implement change-control processes that prevent unauthorized or unsafe model modifications from reaching production. These controls ensure model integrity throughout the entire lifecycle--from development through deployment to decommissioning--enabling rapid incident response and maintaining accountability for all changes.

Core Security Goal: Ensure that only authorized, validated models reach production by employing controlled processes that maintain integrity, traceability, and recoverability.

---

### C3.1 Model Authorization and Integrity

Only authorized models with verified integrity reach production environments.

 #3.1.1    Level: 1    Role: D/V
 Verify that all model artifacts (weights, configurations, and tokenizers) are cryptographically signed by authorized entities prior to deployment.
 #3.1.2    Level: 1    Role: D/V
 Ensure that model integrity is validated at deployment time, and that signature verification failures prevent the model from loading.
 #3.1.3    Level: 2    Role: D/V
 Verify that model provenance records include the identity of the authorizing entity, the training data checksums, the validation test results with a pass/fail status, and a creation timestamp.
 #3.1.4    Level: 2    Role: D/V
 Verify that all model artifacts use semantic versioning (MAJOR.MINOR.PATCH), with documented criteria describing when each version component increments.
 #3.1.5    Level: 2    Role: V
 Verify that dependency tracking maintains a real-time inventory, enabling rapid identification of all consuming systems.

---

### C3.2 Model Validation and Testing

Models must pass defined security and safety validations prior to deployment.

 #3.2.1    Level: 1    Role: D/V
 Verify that models undergo automated security testing, including input validation, output sanitization, and safety evaluations, with pre-agreed organizational pass/fail thresholds before deployment.
 #3.2.2    Level: 1    Role: D/V
 Verify that validation failures automatically block model deployment after explicit override approval from pre-designated authorized personnel, with documented business justifications.
 #3.2.3    Level: 2    Role: V
 Verify that test results are cryptographically signed and immutably linked to the specific model version hash being validated.
 #3.2.4    Level: 2    Role: D/V
 Verify that emergency deployments require a documented security risk assessment and approval from a pre-designated security authority within pre-agreed timeframes.

---

### C3.3 Controlled Deployment and Rollback

Model deployments must be controlled, monitored, and reversible.

 #3.3.1    Level: 1    Role: D
 Verify that production deployments implement gradual rollout mechanisms (canary deployments and blue-green deployments) with automated rollback triggers based on agreed-upon error rates, latency thresholds, or security alert criteria.
 #3.3.2    Level: 1    Role: D/V
 Verify that rollback capabilities restore the complete model state (weights, configurations, and dependencies) atomically within pre-defined organizational time windows.
 #3.3.3    Level: 2    Role: D/V
 Verify that deployment processes validate cryptographic signatures and compute integrity checksums before model activation, and fail deployment if any mismatch is detected.
 #3.3.4    Level: 2    Role: D/V
 Verify that emergency model shutdown capabilities can disable model endpoints within predefined response times via automated circuit breakers or manual kill switches.
 #3.3.5    Level: 2    Role: V
 Verify that rollback artifacts (previous model versions, configurations, and dependencies) are retained in accordance with organizational policies, with immutable storage for incident response.

---

### C3.4 Change Accountability and Audit

All changes to the model lifecycle must be traceable and auditable.

 #3.4.1    Level: 1    Role: V
 Verify that all model changes (deployment, configuration, and retirement) generate immutable audit records that include a timestamp, an authenticated actor identity, a change type, and the before/after states.
 #3.4.2    Level: 2    Role: D/V
 Verify that access to audit logs requires appropriate authorization and that all access attempts are logged with the user’s identity and a timestamp.
 #3.4.3    Level: 2    Role: D/V
 Verify that prompt templates and system messages are version-controlled in Git repositories, with mandatory code review and approval from designated reviewers before deployment.
 #3.4.4    Level: 2    Role: V
 Verify that audit records contain sufficient detail, including model hashes, configuration snapshots, and dependency versions, to enable the complete reconstruction of the model state for any timestamp within the retention period.

---

### C3.5 Secure Development Practices

Model development and training processes must adhere to secure practices to prevent compromise.

 #3.5.1    Level: 1    Role: D
 Verify that the model development, testing, and production environments are physically or logically separated. They do not share infrastructure, and they have distinct access controls and isolated data stores.
 #3.5.2    Level: 1    Role: D
 Verify that model training and fine-tuning occur in isolated environments with controlled network access.
 #3.5.3    Level: 1    Role: D/V
 Verify that training data sources are validated for integrity and authenticated through trusted sources with a documented chain of custody before they are used in model development.
 #3.5.4    Level: 2    Role: D
 Verify that model development artifacts (hyperparameters, training scripts, configuration files) are stored in version control and require peer review approval before they are used in training.

---

### C3.6 Model Retirement and Decommissioning

Models must be securely retired when they are no longer needed or when security issues are identified.

 #3.6.1    Level: 1    Role: D
 Verify that model retirement processes automatically scan dependency graphs, identify all consuming systems, and provide pre-agreed advance notice periods prior to decommissioning.
 #3.6.2    Level: 1    Role: D/V
 Verify that retired model artifacts are securely wiped using cryptographic erasure or multi-pass overwriting in accordance with documented data retention policies, with destruction certificates that have been verified.
 #3.6.3    Level: 2    Role: V
 Verify that model retirement events are logged with a timestamp and the actor's identity, and that model signatures are revoked to prevent reuse.
 #3.6.4    Level: 2    Role: D/V
 Verify that emergency model retirement can disable model access within pre-established emergency response timeframes through automated kill switches if critical security vulnerabilities are discovered.

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

## C4 Infrastructure, Configuration, and Deployment Security

### Control Objective

AI infrastructure must be hardened against privilege escalation, supply chain tampering, and lateral movement through secure configuration, runtime isolation, trusted deployment pipelines, and comprehensive monitoring. Only authorized and validated infrastructure components and configurations reach production through controlled processes that maintain security, integrity, and auditability.

Core Security Goal: Only cryptographically signed, vulnerability-scanned infrastructure components reach production through automated validation pipelines that enforce security policies and maintain immutable audit trails.

---

### C4.1 Runtime Environment Isolation

Prevent container escapes and privilege escalation through kernel-level isolation primitives and mandatory access controls.

 #4.1.1    Level: 1    Role: D/V
 Verify that all AI containers drop all Linux capabilities, except CAP_SETUID, CAP_SETGID, and the explicitly required capabilities documented in security baselines.
 #4.1.2    Level: 1    Role: D/V
 Verify that seccomp profiles block all syscalls except those in pre-approved allowlists, and that any violations terminate the container and generate security alerts.
 #4.1.3    Level: 2    Role: D/V
 Verify that AI workloads run with read-only root filesystems, tmpfs for temporary data, and named volumes for persistent data, with noexec mount options enforced.
 #4.1.4    Level: 2    Role: D/V
 Verify that eBPF-based runtime monitoring (Falco, Tetragon, or an equivalent solution) detects privilege escalation attempts and automatically terminates offending processes within the organization's response time requirements.
 #4.1.5    Level: 3    Role: D/V
 Verify that high-risk AI workloads execute in hardware-isolated environments (Intel TXT, AMD SVM, or dedicated bare-metal nodes) with attestation.

---

### C4.2 Secure Build & Deployment Pipelines

Ensure cryptographic integrity and supply chain security through reproducible builds and signed artifacts.

 #4.2.1    Level: 1    Role: D/V
 Verify that infrastructure-as-code is scanned on every commit using tools such as tfsec, Checkov, or Terrascan, and block merges that report CRITICAL or HIGH severity findings.
 #4.2.2    Level: 1    Role: D/V
 Verify that container builds are reproducible with identical SHA256 hashes across builds and generate SLSA Level 3 provenance attestations signed with Sigstore.
 #4.2.3    Level: 2    Role: D/V
 Verify that container images embed CycloneDX or SPDX SBOMs and are signed with Cosign before pushing to the registry, and that unsigned images are rejected at deployment.
 #4.2.4    Level: 2    Role: D/V
 Verify that CI/CD pipelines use OIDC tokens issued by HashiCorp Vault, AWS IAM Roles, or Azure Managed Identity, with lifetimes that do not exceed organizational security policy limits.
 #4.2.5    Level: 2    Role: D/V
 Verify that Cosign signatures and SLSA provenance are validated during the deployment process before container execution, and that verification errors cause the deployment to fail.
 #4.2.6    Level: 2    Role: D/V
 Verify that build environments run in ephemeral containers or virtual machines with no persistent storage and are network-isolated from production VPCs.

---

### C4.3 Network Security and Access Control

Implement zero-trust networking with default-deny policies and encrypted communications.

 #4.3.1    Level: 1    Role: D/V
 Verify that Kubernetes NetworkPolicies, or any equivalent mechanism, implement default-deny ingress and egress with explicit allow rules for the required ports (443, 8080, etc.).
 #4.3.2    Level: 1    Role: D/V
 Verify that SSH (port 22), RDP (port 3389), and the cloud metadata endpoint (169.254.169.254) are blocked or require certificate-based authentication.
 #4.3.3    Level: 2    Role: D/V
 Verify that egress traffic is filtered through HTTP/HTTPS proxies (Squid, Istio, or cloud NAT gateways), using domain allowlists, and that blocked requests are logged.
 #4.3.4    Level: 2    Role: D/V
 Verify that inter-service communication uses mutual TLS, with certificates rotated in accordance with organizational policy and certificate validation enforced (no skip-verify flags).
 #4.3.5    Level: 2    Role: D/V
 Verify that AI infrastructure runs in dedicated VPCs/VNets with no direct Internet access and communicates only through NAT gateways or bastion hosts.

---

### C4.4 Secrets and Cryptographic Key Management

Protect credentials with hardware-backed storage and automated rotation using zero-trust access.

 #4.4.1    Level: 1    Role: D/V
 Verify that secrets are stored in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault, or Google Secret Manager with encryption at rest using AES-256.
 #4.4.2    Level: 1    Role: D/V
 Verify that cryptographic keys are generated within FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) with key rotation in accordance with the organization's cryptographic policy.
 #4.4.3    Level: 2    Role: D/V
 Verify that secret rotation is automated with zero-downtime deployment, and that rotation is triggered immediately by personnel changes or security incidents.
 #4.4.4    Level: 2    Role: D/V
 Verify that container images are scanned using tools such as GitLeaks, TruffleHog, or detect-secrets, and that builds containing API keys, passwords, or certificates are blocked.
 #4.4.5    Level: 2    Role: D/V
 Verify that production secret access requires MFA with hardware tokens (YubiKey, FIDO2) and that immutable audit logs record user identities and timestamps.
 #4.4.6    Level: 2    Role: D/V
 Verify that secrets are injected via Kubernetes secrets, mounted volumes, or init containers, and ensure that secrets are never embedded in environment variables or images.

---

### C4.5 AI Workload Sandboxing and Validation

Isolate untrusted AI models in secure sandboxes and conduct comprehensive behavioral analysis.

 #4.5.1    Level: 1    Role: D/V
 Verify that external AI models run inside gVisor, microVMs (such as Firecracker or CrossVM), or Docker containers started with the flags --security-opt=no-new-privileges and --read-only.
 #4.5.2    Level: 1    Role: D/V
 Verify that sandbox environments have no network connectivity (--network=none) or only localhost access, with all external requests blocked by iptables rules.
 #4.5.3    Level: 2    Role: D/V
 Verify that AI model validation includes automated red-team testing with organization-defined test coverage and behavioral analysis for backdoor detection.
 #4.5.4    Level: 2    Role: D/V
 Verify that, before an AI model is promoted to production, its sandbox results are cryptographically signed by authorized security personnel and stored in immutable audit logs.
 #4.5.5    Level: 2    Role: D/V
 Verify that sandbox environments are destroyed and recreated from golden images between evaluations, with complete filesystem and memory cleanup.

---

### C4.6 Infrastructure Security Monitoring

Continuously scan and monitor infrastructure with automated remediation and real-time alerting.

 #4.6.1    Level: 1    Role: D/V
 Verify that container images are scanned according to organizational schedules, with CRITICAL vulnerabilities blocking deployment based on organizational risk thresholds.
 #4.6.2    Level: 1    Role: D/V
 Verify that the infrastructure complies with CIS Benchmarks or NIST 800-53 controls, using organizationally defined compliance thresholds and automated remediation for failed checks.
 #4.6.3    Level: 2    Role: D/V
 Verify that high-severity vulnerabilities are patched in accordance with organizational risk-management timelines, and that emergency procedures are in place for actively exploited CVEs.
 #4.6.4    Level: 2    Role: V
 Verify that security alerts integrate with SIEM platforms (Splunk, Elastic, or Sentinel) using CEF or STIX/TAXII formats with automated enrichment.
 #4.6.5    Level: 3    Role: V
 Verify that infrastructure metrics are exported to monitoring systems (Prometheus, Datadog) with SLA dashboards and executive-level reporting.
 #4.6.6    Level: 2    Role: D/V
 Verify that configuration drift is detected using tools (Chef InSpec, AWS Config) in accordance with organizational monitoring requirements, with automatic rollback for unauthorized changes.

---

### C4.7 AI Infrastructure Resource Management

Prevent resource exhaustion attacks and ensure fair resource allocation through quotas and monitoring.

 #4.7.1    Level: 1    Role: D/V
 Verify that GPU/TPU utilization is monitored with alerts triggered at organization-defined thresholds, and that automatic scaling or load balancing is activated based on capacity-management policies.
 #4.7.2    Level: 1    Role: D/V
 Verify that AI workload metrics (inference latency, throughput, and error rates) are collected in accordance with organizational monitoring requirements and correlated with infrastructure utilization.
 #4.7.3    Level: 2    Role: D/V
 Verify that Kubernetes ResourceQuotas, or an equivalent mechanism, limit individual workloads according to organizational resource-allocation policies, with hard limits enforced.
 #4.7.4    Level: 2    Role: V
 Verify that cost monitoring tracks spending per workload or per tenant, with alerts based on organizational budget thresholds and automated controls to prevent budget overruns.
 #4.7.5    Level: 3    Role: V
 Verify that capacity planning relies on historical data, uses organizationally defined forecasting periods, and automatically provisions resources based on demand patterns.
 #4.7.6    Level: 2    Role: D/V
 Verify that resource exhaustion triggers circuit breakers in accordance with organizational response requirements, including rate limiting based on capacity policies and workload isolation.

---

### C4.8 Environment Separation and Promotion Controls

Enforce strict environment boundaries with automated promotion gates and security validation.

 #4.8.1    Level: 1    Role: D/V
 Verify that the dev, test, and prod environments run in separate VPCs/VNets, with no shared IAM roles, security groups, or network connectivity.
 #4.8.2    Level: 1    Role: D/V
 Verify that environment promotion requires approval by organization-defined authorized personnel, with cryptographic signatures and immutable audit trails.
 #4.8.3    Level: 2    Role: D/V
 Verify that production environments block SSH access, disable debug endpoints, and require change requests that follow organizational advance notice requirements, except in emergencies.
 #4.8.4    Level: 2    Role: D/V
 Verify that infrastructure-as-code changes require peer review, automated testing, and security scanning before merging into the main branch.
 #4.8.5    Level: 2    Role: D/V
 Verify that non-production data is anonymized in accordance with organizational privacy requirements, or through synthetic data generation, or through complete data masking with PII removal verification.
 #4.8.6    Level: 2    Role: D/V
 Verify that promotion gates include automated security tests (SAST, DAST, and container scanning) and require zero critical findings for approval.

---

### C4.9 Infrastructure Backup & Recovery

Ensure infrastructure resilience through automated backups, tested recovery procedures, and disaster recovery capabilities.

 #4.9.1    Level: 1    Role: D/V
 Verify that infrastructure configurations are backed up according to organizational backup schedules across geographically separated regions using a 3-2-1 backup strategy.
 #4.9.2    Level: 2    Role: D/V
 Verify that backup systems operate in isolated networks with separate credentials and air-gapped storage to protect against ransomware.
 #4.9.3    Level: 2    Role: V
 Verify that recovery procedures are tested and validated through automated testing in accordance with organizational schedules, with RTO and RPO targets that meet organizational requirements.
 #4.9.4    Level: 3    Role: V
 Verify that disaster recovery plans include AI-specific runbooks with model weight restoration, GPU cluster rebuilding, and service dependency mapping.

---

### C4.10 Infrastructure Compliance & Governance

Maintain regulatory compliance through continuous assessment, documentation, and automated controls.

 #4.10.1    Level: 2    Role: D/V
 Verify that infrastructure compliance is assessed in accordance with organizational schedules against SOC 2, ISO 27001, or FedRAMP controls, with automated evidence collection.
 #4.10.2    Level: 2    Role: V
 Verify that infrastructure documentation includes network diagrams, data flow maps, and threat models updated in accordance with organizational change management requirements.
 #4.10.3    Level: 3    Role: D/V
 Verify that infrastructure changes undergo an automated compliance impact assessment within regulatory approval workflows for high-risk modifications.

---

### C4.11 AI Hardware Security

Secure AI-specific hardware components, including GPUs, TPUs, and specialized AI accelerators.

 #4.11.1    Level: 2    Role: D/V
 Verify that AI accelerator firmware (GPU BIOS, TPU firmware) is signed with cryptographic signatures and updated according to organizational patch management timelines.
 #4.11.2    Level: 2    Role: D/V
 Verify that before workload execution, the AI accelerator's integrity is validated by hardware attestation using TPM 2.0, Intel TXT, or AMD SVM.
 #4.11.3    Level: 2    Role: D/V
 Verify that GPU memory is isolated among workloads using SR-IOV, MIG (Multi-Instance GPU), or equivalent hardware partitioning, with memory sanitization between jobs.
 #4.11.4    Level: 3    Role: V
 Verify that the AI hardware supply chain includes provenance verification with manufacturer certificates and tamper-evident packaging validation.
 #4.11.5    Level: 3    Role: D/V
 Verify that hardware security modules (HSMs) protect AI model weights and cryptographic keys with FIPS 140-2 Level 3 certification or Common Criteria EAL4+ certification.

---

### C4.12 Edge and Distributed AI Infrastructure

Secure distributed AI deployments, including edge computing, federated learning, and multi-site architectures.

 #4.12.1    Level: 2    Role: D/V
 Verify that edge AI devices authenticate to central infrastructure using mutual TLS, with device certificates rotated in accordance with the organization’s certificate management policy.
 #4.12.2    Level: 2    Role: D/V
 Verify that edge devices implement secure boot with verified signatures and rollback protection that prevents firmware downgrade attacks.
 #4.12.3    Level: 3    Role: D/V
 Verify that distributed AI coordination uses Byzantine fault-tolerant consensus algorithms, with participant validation and detection of malicious nodes.
 #4.12.4    Level: 3    Role: D/V
 Verify that edge-to-cloud communication supports bandwidth throttling, data compression, and offline operation capabilities with secure local storage.

---

### C4.13 Multi-Cloud & Hybrid Infrastructure Security

Secure AI workloads across multiple cloud providers and hybrid cloud-on-premises deployments.

 #4.13.1    Level: 2    Role: D/V
 Verify that multi-cloud AI deployments use cloud-agnostic identity federation (OIDC, SAML) with centralized policy management across cloud providers.
 #4.13.2    Level: 2    Role: D/V
 Verify that cross-cloud data transfers use end-to-end encryption with customer-managed keys and data residency controls enforced per jurisdiction.
 #4.13.3    Level: 2    Role: D/V
 Verify that hybrid-cloud AI workloads implement consistent security policies across on-premises and cloud environments with unified monitoring and alerting.
 #4.13.4    Level: 3    Role: V
 Verify that cloud vendor lock-in prevention includes portable infrastructure-as-code, standardized APIs, and data export capabilities with format conversion tools.
 #4.13.5    Level: 3    Role: V
 Verify that multi-cloud cost optimization includes security controls to prevent resource sprawl and unauthorized cross-cloud data transfer charges.

---

### C4.14 Infrastructure Automation and GitOps Security

Secure infrastructure automation pipelines and GitOps workflows for AI infrastructure management.

 #4.14.1    Level: 2    Role: D/V
 Verify that GitOps repositories require commits signed with GPG keys and implement branch protection rules that prevent direct pushes to the main branches.
 #4.14.2    Level: 2    Role: D/V
 Verify that infrastructure automation includes drift detection with automatic remediation and rollback capabilities, triggered in accordance with the organization's response requirements for unauthorized changes.
 #4.14.3    Level: 2    Role: D/V
 Verify that automated infrastructure provisioning includes security policy validation and blocks deployment for non-compliant configurations.
 #4.14.4    Level: 2    Role: D/V
 Verify that infrastructure automation secrets are managed by external secret operators (External Secrets Operator, Bank-Vaults) with automatic rotation.
 #4.14.5    Level: 3    Role: V
 Verify that self-healing infrastructure includes security event correlation with automated incident response and stakeholder notification workflows.

---

### C4.15 Quantum-Resistant Infrastructure Security

Prepare AI infrastructure to mitigate quantum computing threats by implementing post-quantum cryptography and quantum-safe protocols.

 #4.15.1    Level: 3    Role: D/V
 Verify that AI infrastructure implements NIST-approved post-quantum cryptographic algorithms (CRYSTALS-Kyber, CRYSTALS-Dilithium, and SPHINCS+) for key exchange and digital signatures.
 #4.15.2    Level: 3    Role: D/V
 Verify that quantum key distribution (QKD) systems are implemented for high-security AI communications using quantum-safe key management protocols.
 #4.15.3    Level: 3    Role: D/V
 Verify that cryptographic agility frameworks enable rapid migration to new post-quantum algorithms, with automated certificate and key rotation.
 #4.15.4    Level: 3    Role: V
 Verify that quantum threat modeling assesses AI infrastructure vulnerability to quantum attacks with documented migration timelines and risk assessments.
 #4.15.5    Level: 3    Role: D/V
 Verify that hybrid classical-quantum cryptographic systems provide defense-in-depth during the quantum transition period, with performance monitoring.

---

### C4.16 Confidential Computing and Secure Enclaves

Protect AI workloads and model weights with hardware-based trusted execution environments and confidential computing technologies.

 #4.16.1    Level: 3    Role: D/V
 Verify that sensitive AI models execute within Intel SGX enclaves, AMD SEV-SNP, or ARM TrustZone, with encrypted memory and attestation verification.
 #4.16.2    Level: 3    Role: D/V
 Verify that confidential containers (Kata Containers, gVisor with confidential computing) isolate AI workloads using hardware-enforced memory encryption.
 #4.16.3    Level: 3    Role: D/V
 Verify that remote attestation validates enclave integrity before loading AI models, using cryptographic proof of the execution environment's authenticity.
 #4.16.4    Level: 3    Role: D/V
 Verify that confidential AI inference services prevent model extraction through encrypted computation, with sealed model weights and protected execution.
 #4.16.5    Level: 3    Role: D/V
 Verify that trusted execution environment orchestration manages the lifecycle of secure enclaves with remote attestation and encrypted communication channels.
 #4.16.6    Level: 3    Role: D/V
 Verify that secure multi-party computation (SMPC) enables collaborative AI training without exposing individual datasets or model parameters.

---

### C4.17 Zero-Knowledge Infrastructure

Implement zero-knowledge proof systems to enable privacy-preserving AI verification and authentication without disclosing sensitive information.

 #4.17.1    Level: 3    Role: D/V
 Verify that zero-knowledge proofs (ZK-SNARKs, ZK-STARKs) can validate AI model integrity and training provenance without exposing model weights or training data.
 #4.17.2    Level: 3    Role: D/V
 Verify that ZK-based authentication systems enable privacy-preserving user verification for AI services without revealing identity-related information.
 #4.17.3    Level: 3    Role: D/V
 Verify that private set intersection (PSI) protocols enable secure data matching for federated AI without exposing any individual datasets.
 #4.17.4    Level: 3    Role: D/V
 Verify that zero-knowledge machine-learning (ZKML) systems enable verifiable AI inferences with a cryptographic proof of correct computation.
 #4.17.5    Level: 3    Role: D/V
 Verify that ZK-rollups provide scalable, privacy-preserving AI transaction processing with batch verification and reduced computational overhead.

---

### C4.18 Side-Channel Attack Prevention

Protect AI infrastructure against timing, power, electromagnetic, and cache-based side-channel attacks that could leak sensitive information.

 #4.18.1    Level: 3    Role: D/V
 Verify that AI inference timing is normalized using constant-time algorithms and padding to prevent timing-based model-extraction attacks.
 #4.18.2    Level: 3    Role: D/V
 Verify that power analysis protection includes noise injection, power line filtering, and randomized execution patterns for AI hardware.
 #4.18.3    Level: 3    Role: D/V
 Verify that cache-based side-channel mitigation uses cache partitioning, randomization, and flush instructions to prevent information leakage.
 #4.18.4    Level: 3    Role: D/V
 Verify that electromagnetic emanation protection includes shielding, signal filtering, and randomized processing to prevent TEMPEST-style attacks.
 #4.18.5    Level: 3    Role: D/V
 Verify that microarchitectural side-channel defenses include speculative-execution controls and memory access pattern obfuscation.

---

### C4.19 Neuromorphic and Specialized AI Hardware Security

Secure emerging AI hardware architectures, including neuromorphic chips, FPGAs, custom ASICs, and optical computing systems.

 #4.19.1    Level: 3    Role: D/V
 Verify that neuromorphic chip security includes spike-pattern encryption, synaptic-weight protection, and hardware-based learning-rule validation.
 #4.19.2    Level: 3    Role: D/V
 Verify that FPGA-based AI accelerators implement bitstream encryption, anti-tamper mechanisms, and secure configuration loading with authenticated updates.
 #4.19.3    Level: 3    Role: D/V
 Verify that the security features of custom ASICs include on-chip security processors, a hardware root of trust, and secure key storage with tamper detection.
 #4.19.4    Level: 3    Role: D/V
 Verify that optical computing systems implement quantum-safe optical encryption, secure photonic switching, and protected optical signal processing.
 #4.19.5    Level: 3    Role: D/V
 Verify that hybrid analog-digital AI chips include secure analog computation, protected weight storage, and authenticated analog-to-digital conversion.

---

### C4.20 Privacy-Preserving Compute Infrastructure

Implement infrastructure controls for privacy-preserving computation to protect sensitive data during AI processing and analysis.

 #4.20.1    Level: 3    Role: D/V
 Verify that the homomorphic encryption infrastructure enables encrypted computation on sensitive AI workloads, with cryptographic integrity verification and performance monitoring.
 #4.20.2    Level: 3    Role: D/V
 Verify that Private Information Retrieval (PIR) systems enable database queries without revealing query patterns, using cryptographic protection of access patterns.
 #4.20.3    Level: 3    Role: D/V
 Verify that secure multi-party computation protocols enable privacy-preserving AI inference without exposing individual inputs or intermediate computations.
 #4.20.4    Level: 3    Role: D/V
 Verify that privacy-preserving key management includes distributed key generation, threshold cryptography, and secure key rotation with hardware-backed protection.
 #4.20.5    Level: 3    Role: D/V
 Verify that privacy-preserving compute performance is optimized through batching, caching, and hardware acceleration while maintaining cryptographic security guarantees.

---

### C4.15 Agent Framework Cloud Integration Security & Hybrid Deployment

Security controls for cloud-integrated agent frameworks in hybrid on-premises and cloud architectures.

 #4.15.1    Level: 1    Role: D/V
 Verify that the cloud storage integration uses end-to-end encryption with agent-controlled key management.
 #4.15.2    Level: 2    Role: D/V
 Verify that the security boundaries for hybrid deployments are clearly defined and that communication channels are encrypted.
 #4.15.3    Level: 2    Role: D/V
 Verify that access to cloud resources uses zero-trust verification with continuous authentication.
 #4.15.4    Level: 3    Role: D/V
 Verify that data residency requirements are enforced through cryptographic attestation of storage locations.
 #4.15.5    Level: 3    Role: D/V
 Verify that cloud provider security assessments include agent-specific threat modeling and risk evaluation.

---

### References

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
NIST SP 800-190: Application Container Security Guide
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
NIST SP 800-53: Security Controls for Federal Information Systems
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework
CIS Kubernetes Benchmark
FIPS 140-2 Security Requirements
NIST SP 800-207: Zero Trust Architecture
IEEE 2857: Privacy Engineering for AI Systems
NIST SP 800-161: Cybersecurity Supply Chain Risk Management
NIST Post-Quantum Cryptography Standards
Intel SGX Developer Guide
AMD SEV-SNP White Paper
ARM TrustZone Technology
ZK-SNARKs: A Gentle Introduction
NIST SP 800-57: Cryptographic Key Management
Side-Channel Attack Countermeasures
Neuromorphic Computing Security Challenges
FPGA Security: Fundamentals, Evaluation, and Countermeasures
Microsoft SEAL: Homomorphic Encryption Library
HElib: Homomorphic Encryption Library
PALISADE Lattice Cryptography Library
Differential Privacy: A Survey of Results
Secure Aggregation for Federated Learning
Private Information Retrieval: Concepts and Constructions

## C5: Access Control and Identity for AI Components and Users

### Control Objective

Effective access control for AI systems requires robust identity management, context-aware authorization, and runtime enforcement aligned with zero-trust principles. These controls ensure that humans, services, and autonomous agents interact only with models, data, and computational resources within explicitly granted scopes, with continuous verification and auditing capabilities.

---

### C5.1 Identity Management and Authentication

Establish cryptographically-backed identities for all entities, with multi-factor authentication for privileged operations.

 #5.1.1    Level: 1    Role: D/V
 Verify that all human users and service principals authenticate through a centralized enterprise identity provider (IdP) using OIDC/SAML protocols, with unique identity-to-token mappings (no shared accounts or credentials).
 #5.1.2    Level: 1    Role: D/V
 Verify that high-risk operations, such as model deployment, weight export, access to training data, and production configuration changes, require multi-factor authentication or step-up authentication with session re-validation.
 #5.1.3    Level: 2    Role: D
 Verify that new principals undergo identity-proofing aligned with NIST SP 800-63-3 IAL-2 or equivalent standards before receiving access to production systems.
 #5.1.4    Level: 2    Role: V
 Verify that access reviews are conducted quarterly, with automated detection of dormant accounts, credential rotation enforcement, and de-provisioning workflows.
 #5.1.5    Level: 3    Role: D/V
 Verify that federated AI agents authenticate using signed JWT assertions that have a maximum lifetime of 24 hours and include cryptographic proof of origin.

---

### C5.2 Resource Authorization and Least Privilege

Implement fine-grained access controls for all AI resources, with explicit permission models and audit trails.

 #5.2.1    Level: 1    Role: D/V
 Verify that every AI resource (datasets, models, endpoints, vector collections, embedding indices, compute instances) enforces role-based access controls with explicit allow-lists and default-deny policies.
 #5.2.2    Level: 1    Role: D/V
 Verify that least-privilege principles are enforced by default: service accounts start with read-only permissions, and a documented business justification is required for write access.
 #5.2.3    Level: 1    Role: V
 Verify that all access control modifications are linked to approved change requests and are immutably logged with timestamps, actor identities, resource identifiers, and permission deltas.
 #5.2.4    Level: 2    Role: D
 Verify that data classification labels (PII, PHI, export-controlled, and proprietary) automatically propagate to derived resources (embeddings, prompt caches, model outputs) with consistent policy enforcement.
 #5.2.5    Level: 2    Role: D/V
 Verify that unauthorized access attempts and privilege escalation events trigger real-time alerts with contextual metadata to SIEM systems within 5 minutes.

---

### C5.3 Dynamic Policy Evaluation

Deploy attribute-based access control (ABAC) engines to support context-aware authorization decisions with auditing capabilities.

 #5.3.1    Level: 1    Role: D/V
 Verify that authorization decisions are externalized to a dedicated policy engine (such as OPA, Cedar, or an equivalent) accessible via authenticated APIs with cryptographic integrity protection.
 #5.3.2    Level: 1    Role: D/V
 Verify that policies evaluate dynamic attributes at runtime, including user clearance level, resource sensitivity classification, request context, tenant isolation, and temporal constraints.
 #5.3.3    Level: 2    Role: D
 Verify that policy definitions are version-controlled, peer-reviewed, and validated through automated testing in CI/CD pipelines before deployment to production.
 #5.3.4    Level: 2    Role: V
 Verify that policy evaluation results include structured decision rationales and are transmitted to SIEM systems for correlation analysis and compliance reporting.
 #5.3.5    Level: 3    Role: D/V
 Verify that policy cache TTL values do not exceed 5 minutes for high-sensitivity resources and 1 hour for standard resources with cache invalidation capabilities.

---

### C5.4 Query-Time Security Enforcement

Implement database-layer security controls, including mandatory filtering and row-level security policies.

 #5.4.1    Level: 1    Role: D/V
 Verify that all vector database and SQL queries include mandatory security filters (tenant ID, sensitivity labels, and user scope) that are enforced at the database engine level, rather than in the application code.
 #5.4.2    Level: 1    Role: D/V
 Verify that row-level security (RLS) policies and field-level masking are enabled with policy inheritance for all vector databases, search indexes, and training datasets.
 #5.4.3    Level: 2    Role: D
 Verify that failed authorization evaluations will prevent the confused deputy attack by immediately aborting queries and returning explicit authorization error codes instead of returning empty result sets.
 #5.4.4    Level: 2    Role: V
 Verify that policy evaluation latency is continuously monitored, with automated alerts for timeout conditions that could enable an authorization bypass.
 #5.4.5    Level: 3    Role: D/V
 Verify that query retry mechanisms re-evaluate authorization policies to account for dynamic permission changes within active user sessions.

---

### C5.5 Output Filtering and Data Loss Prevention

Deploy post-processing controls to prevent unauthorized data exposure in AI-generated content.

 #5.5.1    Level: 1    Role: D/V
 Verify that post-inference filtering mechanisms scan for and redact unauthorized PII, classified information, and proprietary data before delivering content to requesters.
 #5.5.2    Level: 1    Role: D/V
 Verify that citations, references, and source attributions in model outputs are validated against the caller's entitlements and removed if unauthorized access is detected.
 #5.5.3    Level: 2    Role: D
 Verify that output format restrictions (sanitized PDFs, metadata-stripped images, and approved file types) are enforced based on user permission levels and data classifications.
 #5.5.4    Level: 2    Role: V
 Verify that redaction algorithms are deterministic, version-controlled, and that they maintain audit logs to support compliance investigations and forensic analysis.
 #5.5.5    Level: 3    Role: V
 Verify that high-risk redaction events generate adaptive logs that include cryptographic hashes of the original content for forensic retrieval without exposing data.

---

### C5.6 Multi-Tenant Isolation

Ensure cryptographic and logical isolation among tenants in shared AI infrastructure.

 #5.6.1    Level: 1    Role: D/V
 Verify that memory spaces, embedding stores, cache entries, and temporary files are namespace-segregated per tenant, with secure purging upon tenant deletion or session termination.
 #5.6.2    Level: 1    Role: D/V
 Verify that every API request includes an authenticated tenant identifier that is cryptographically validated against the session context and the user's entitlements.
 #5.6.3    Level: 2    Role: D
 Verify that network policies implement default-deny rules for cross-tenant communication within service meshes and container orchestration platforms.
 #5.6.4    Level: 3    Role: D
 Verify that encryption keys are unique per tenant with customer-managed key (CMK) support and that tenant data stores are cryptographically isolated.

---

### C5.7 Autonomous Agent Authorization

Control permissions for AI agents and autonomous systems using scoped capability tokens and continuous authorization.

 #5.7.1    Level: 1    Role: D/V
 Verify that autonomous agents receive scoped capability tokens that explicitly enumerate the permitted actions, accessible resources, time boundaries, and operational constraints.
 #5.7.2    Level: 1    Role: D/V
 Verify that high-risk capabilities (file system access, code execution, external API calls, and financial transactions) are disabled by default and require explicit authorization for activation, with business justifications.
 #5.7.3    Level: 2    Role: D
 Verify that capability tokens are bound to user sessions, provide cryptographic integrity protection, and ensure that they cannot be persisted or reused offline.
 #5.7.4    Level: 2    Role: V
 Verify that agent-initiated actions undergo secondary authorization through the ABAC policy engine, with full-context evaluation and audit logging.
 #5.7.5    Level: 3    Role: V
 Verify that agent error conditions and exception handling include capability-scope information to support incident analysis and forensic investigations.

---

### References

#### Standards & Frameworks

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Implementation Guides

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### AI-Specific Security

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Supply Chain Security for Models, Frameworks, and Data

### Control Objective

AI supply‑chain attacks exploit third‑party models, frameworks, or datasets to embed backdoors, bias, or exploitable code. These controls provide end‑to‑end provenance, vulnerability management, and monitoring to protect the entire model lifecycle.

---

### C6.1 Pre-trained Model Vetting and Provenance

Assess and authenticate the origins, licenses, and hidden behaviors of third‑party models before any fine‑tuning or deployment.

 #6.1.1    Level: 1    Role: D/V
 Verify that every third-party model artifact includes a signed provenance record identifying its source repository and commit hash.
 #6.1.2    Level: 1    Role: D/V
 Verify that models are scanned for malicious layers or Trojan triggers using automated tools before importing.
 #6.1.3    Level: 2    Role: D
 Verify that transfer-learning fine-tuning passes adversarial evaluation to detect hidden behaviors.
 #6.1.4    Level: 2    Role: V
 Verify that model licenses, export‑control tags, and data‑origin statements are recorded in an ML‑BOM entry.
 #6.1.5    Level: 3    Role: D/V
 Verify that high‑risk models (publicly uploaded weights and unverified creators) remain quarantined until human review and sign‑off.

---

### C6.2 Framework and Library Scanning

Continuously monitor ML frameworks and libraries for CVEs and malicious code to keep the runtime stack secure.

 #6.2.1    Level: 1    Role: D/V
 Verify that CI pipelines run dependency scanners for AI frameworks and critical libraries.
 #6.2.2    Level: 1    Role: D/V
 Verify that critical vulnerabilities (CVSS ≥ 7.0) block promotion to production images.
 #6.2.3    Level: 2    Role: D
 Verify that static code analysis runs on forked or vendored ML libraries.
 #6.2.4    Level: 2    Role: V
 Verify that framework upgrade proposals include a security impact assessment that references public CVE feeds.
 #6.2.5    Level: 3    Role: V
 Verify that runtime sensors generate alerts for unexpected dynamic library loads that deviate from the signed SBOM.

---

### C6.3 Dependency Pinning & Verification

Pin every dependency to immutable digests and reproduce builds to guarantee identical, tamper‑free artifacts.

 #6.3.1    Level: 1    Role: D/V
 Verify that all package managers enforce version pinning through lockfiles.
 #6.3.2    Level: 1    Role: D/V
 Verify that immutable digests are used instead of mutable tags in container references.
 #6.3.3    Level: 2    Role: D
 Verify that reproducible-build checks compare hashes across CI runs to ensure identical outputs.
 #6.3.4    Level: 2    Role: V
 Verify that build attestations are stored for 18 months to ensure audit traceability.
 #6.3.5    Level: 3    Role: D
 Verify that expired dependencies trigger automated pull requests to update or fork pinned versions.

---

### C6.4 Trusted Source Enforcement

Allow artifact downloads only from cryptographically verified, organization‑approved sources and block everything else.

 #6.4.1    Level: 1    Role: D/V
 Verify that model weights, datasets, and containers are downloaded only from approved domains or internal registries.
 #6.4.2    Level: 1    Role: D/V
 Verify that Sigstore/Cosign signatures validate the publisher's identity before artifacts are cached locally.
 #6.4.3    Level: 2    Role: D
 Verify that egress proxies block unauthenticated artifact downloads to enforce a trusted-source policy.
 #6.4.4    Level: 2    Role: V
 Verify that repository allow‑lists are reviewed quarterly, with evidence of a business justification for each entry.
 #6.4.5    Level: 3    Role: V
 Verify that policy violations trigger quarantine of artifacts and rollback of dependent pipeline runs.

---

### C6.5 Third‑Party Dataset Risk Assessment

Evaluate external datasets for data poisoning, bias, and legal compliance, and monitor them throughout their lifecycle.

 #6.5.1    Level: 1    Role: D/V
 Verify that external datasets undergo poisoning-risk scoring (e.g., data fingerprinting and outlier detection).
 #6.5.2    Level: 1    Role: D
 Verify that bias metrics (demographic parity and equal opportunity) are calculated before dataset approval.
 #6.5.3    Level: 2    Role: V
 Verify that the provenance and license terms for datasets are captured in ML‑BOM entries.
 #6.5.4    Level: 2    Role: V
 Verify that periodic monitoring detects drift or corruption in hosted datasets.
 #6.5.5    Level: 3    Role: D
 Verify that prohibited content (copyrighted material and PII) is removed by automated scrubbing prior to training.

---

### C6.6 Supply Chain Attack Monitoring

Detect supply‑chain threats early through CVE feeds, audit‑log analytics, and red‑team simulations.

 #6.6.1    Level: 1    Role: V
 Verify that CI/CD audit logs stream into SIEM for detections of anomalous package pulls or tampered build steps.
 #6.6.2    Level: 2    Role: D
 Verify that incident response playbooks include rollback procedures for compromised models or libraries.
 #6.6.3    Level: 3    Role: V
 Verify that threat‑intel enrichment tags ML‑specific indicators (e.g., model‑poisoning IoCs) are present in alert triage.

---

### C6.7 ML‑BOM for Model Artifacts

Generate and sign detailed ML‑specific SBOMs (ML‑BOMs) so downstream consumers can verify component integrity at deployment time.

 #6.7.1    Level: 1    Role: D/V
 Verify that every model artifact publishes an ML‑BOM that lists datasets, weights, hyperparameters, and licenses.
 #6.7.2    Level: 1    Role: D/V
 Verify that ML‑BOM generation and Cosign signing are automated in CI and required for merges.
 #6.7.3    Level: 2    Role: D
 Verify that ML‑BOM completeness checks cause the build to fail when any component metadata (hash, license) is missing.
 #6.7.4    Level: 2    Role: V
 Verify that downstream consumers can query ML-BOMs via API to validate imported models at deployment time.
 #6.7.5    Level: 3    Role: V
 Verify that ML‑BOMs are version‑controlled and diffed to detect unauthorized modifications.

---

### References

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
AI & Transparency: Protect ML Models – ReversingLabs
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## C7 model behavior, output control, and safety assurance

### Control Objective

Model outputs must be structured, reliable, safe, explainable, and continuously monitored in production. This approach reduces hallucinations, privacy leaks, harmful content, and runaway actions, while increasing user trust and regulatory compliance.

---

### C7.1 Output Format Enforcement

Strict schemas, constrained decoding, and downstream validation prevent malformed or malicious content from propagating.

 #7.1.1    Level: 1    Role: D/V
 Verify that response schemas (for example, JSON Schema) are included in the system prompt and that every output is automatically validated; non-conforming outputs should be repaired or rejected.
 #7.1.2    Level: 1    Role: D/V
 Verify that constrained decoding (stop tokens, regex, and max-tokens) is enabled to prevent overflow or prompt-injection side-channels.
 #7.1.3    Level: 2    Role: D/V
 Verify that downstream components treat outputs as untrusted and validate them against schemas or injection-safe de-serializers.
 #7.1.4    Level: 3    Role: V
 Verify that improper-output events are logged, rate-limited, and surfaced to monitoring.

---

### C7.2 Hallucination Detection & Mitigation

Uncertainty estimation and fallback strategies help curb fabricated answers.

 #7.2.1    Level: 1    Role: D/V
 Verify that token-level log-probabilities, ensemble self-consistency, or fine-tuned hallucination detectors assign a confidence score to each answer.
 #7.2.2    Level: 1    Role: D/V
 Verify that responses below a configurable confidence threshold trigger fallback workflows, such as retrieval-augmented generation, a secondary model, or human review.
 #7.2.3    Level: 2    Role: D/V
 Verify that hallucination incidents are tagged with root-cause metadata and fed into post-mortem and fine-tuning pipelines.
 #7.2.4    Level: 3    Role: D/V
 Verify that thresholds and detectors are re-calibrated after major model or knowledge-base updates.
 #7.2.5    Level: 3    Role: V
 Verify that the dashboard visualizations track hallucination rates.

---

### C7.3 Output Safety & Privacy Filtering

Policy filters and red-team coverage protect users and confidential data.

 #7.3.1    Level: 1    Role: D/V
 Verify that pre- and post-generation classifiers block hate, harassment, self-harm, extremist content, and sexually explicit material in alignment with policy.
 #7.3.2    Level: 1    Role: D/V
 Verify that PII/PCI detection and automatic redaction run on every response; any violations trigger a privacy incident.
 #7.3.3    Level: 2    Role: D
 Verify that confidentiality tags (for example, trade secrets) propagate across modalities to prevent information leakage in text, images, or code.
 #7.3.4    Level: 3    Role: D/V
 Verify that attempts to bypass filters or high-risk classifications require secondary approval or user re-authentication.
 #7.3.5    Level: 3    Role: D/V
 Verify that the filtering thresholds reflect the applicable legal jurisdictions and the user’s age/role context.

---

### C7.4 Output & Action Limiting

Rate-limits and approval gates prevent abuse and excessive autonomy.

 #7.4.1    Level: 1    Role: D
 Verify that per-user and per-API-key quotas limit requests, tokens, and cost, and use exponential back-off for 429 errors.
 #7.4.2    Level: 1    Role: D/V
 Verify that privileged actions, such as file writes, code execution, and network calls, require policy-based approval or human-in-the-loop.
 #7.4.3    Level: 2    Role: D/V
 Verify that cross-modal consistency checks ensure that images, code, and text generated for the same request cannot be used to smuggle malicious content.
 #7.4.4    Level: 2    Role: D
 Verify that the agent delegation depth, the recursion limits, and the allowed tool lists are explicitly configured.
 #7.4.5    Level: 3    Role: V
 Verify that violations of limits emit structured security events for SIEM ingestion.

---

### C7.5 Output Explainability

Transparent signals improve user trust and facilitate internal debugging.

 #7.5.1    Level: 2    Role: D/V
 Verify that user-facing confidence scores or brief reasoning summaries are exposed when risk assessment deems appropriate.
 #7.5.2    Level: 2    Role: D/V
 Verify that generated explanations do not reveal sensitive system prompts or proprietary data.
 #7.5.3    Level: 3    Role: D
 Verify that the system captures token-level log-probabilities or attention maps and stores them for authorized inspection.
 #7.5.4    Level: 3    Role: V
 Verify that explainability artifacts are version-controlled alongside model releases for auditability.

---

### C7.6 Monitoring Integration

Real-time observability closes the loop between development and production.

 #7.6.1    Level: 1    Role: D
 Verify that metrics (schema violations, hallucination rate, toxicity, PII leaks, latency, and cost) stream to a central monitoring platform.
 #7.6.2    Level: 1    Role: V
 Verify that alert thresholds are defined for each safety metric and that on-call escalation paths are in place.
 #7.6.3    Level: 2    Role: V
 Verify that dashboards correlate output anomalies with the model version, the feature flag, and upstream data changes.
 #7.6.4    Level: 2    Role: D/V
 Verify that monitoring data feeds back into retraining, fine-tuning, or rule updates within a documented MLOps workflow.
 #7.6.5    Level: 3    Role: V
 Verify that monitoring pipelines are penetration-tested and access-controlled to prevent leakage of sensitive logs.

---

### 7.7 Generative Media Safeguards

Ensure that AI systems do not generate illegal, harmful, or unauthorized media content by enforcing policy constraints, validating outputs, and ensuring traceability.

 #7.7.1    Level: 1    Role: D/V
 Verify that system prompts and user instructions explicitly prohibit the creation of illegal, harmful, or non-consensual deepfake media (e.g., images, videos, or audio).
 #7.7.2    Level: 2    Role: D/V
 Verify that prompts are filtered to prevent attempts to generate impersonations, sexually explicit deepfakes, or media depicting real individuals without consent.
 #7.7.3    Level: 2    Role: V
 Verify that the system uses perceptual hashing, watermark detection, or fingerprinting to prevent unauthorized reproduction of copyrighted media.
 #7.7.4    Level: 3    Role: D/V
 Verify that all generated media are cryptographically signed, watermarked, or embedded with tamper-resistant provenance metadata for downstream traceability.
 #7.7.5    Level: 3    Role: V
 Verify that bypass attempts (for example, prompt obfuscation, slang, and adversarial phrasing) are detected, logged, and rate-limited, and that repeated abuse is surfaced to monitoring systems.

### References

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Improper Output Handling – OWASP LLM05:2025
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
LLM Red-Teaming Guide
Sensitive Information Disclosure in LLMs
LangChain – Chat Model Rate Limiting
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## C8 Memory, Embeddings & Vector Database Security

### Control Objective

Embeddings and vector stores act as the "live memory" of contemporary AI systems, continuously accepting user-supplied data and surfacing it back into model contexts via Retrieval-Augmented Generation (RAG).

If left ungoverned, this memory can leak PII, violate consent, or be inverted to reconstruct the original text.

The objective of this control family is to harden memory pipelines and vector databases so that access is least-privilege, embeddings are privacy-preserving, stored vectors expire or can be revoked on demand, and per-user memory never contaminates another user's prompts or completions.

---

### C8.1 Access Controls for Memory and RAG Indices

Enforce fine-grained access controls on every vector collection.

 #8.1.1    Level: 1    Role: D/V
 Verify that row-level and namespace-level access control rules restrict insert, delete, and query operations per tenant, collection, or document tag.
 #8.1.2    Level: 1    Role: D/V
 Verify that API keys or JWTs carry scoped claims (for example, collection IDs and action verbs) and that they are rotated at least quarterly.
 #8.1.3    Level: 2    Role: D/V
 Verify that privilege-escalation attempts (for example, cross-namespace similarity queries) are detected and logged by a SIEM within 5 minutes.
 #8.1.4    Level: 2    Role: D/V
 Verify that the vector DB audit logs include the subject-identifier, operation, vector ID/namespace, similarity threshold, and result count.
 #8.1.5    Level: 3    Role: V
 Verify that access decisions are tested for bypass flaws whenever engines are upgraded or index-sharding rules change.

---

### C8.2 Embedding Sanitization & Validation

Pre-screen text for PII, redact or pseudonymize before vectorization, and optionally post-process embeddings to strip residual signals.

 #8.2.1    Level: 1    Role: D/V
 Verify that PII and regulated data are detected by automated classifiers and masked, tokenized, or dropped before embedding.
 #8.2.2    Level: 1    Role: D
 Verify that embedding pipelines reject or quarantine inputs that contain executable code or non-UTF-8 artifacts that could poison the index.
 #8.2.3    Level: 2    Role: D/V
 Verify that local or metric differential-privacy sanitization is applied to sentence embeddings whose distance from any known PII token falls below a configurable threshold.
 #8.2.4    Level: 2    Role: V
 Verify that sanitization efficacy (e.g., recall of PII redaction and semantic drift) is validated at least semi-annually against benchmark corpora.
 #8.2.5    Level: 3    Role: D/V
 Verify that sanitization configurations are version-controlled and that any changes undergo peer review.

---

### C8.3 Memory Expiration, Revocation, and Deletion

GDPR's 'right to be forgotten' and similar data protection laws require timely erasure, so vector stores must support TTLs, hard deletes, and tomb-stoning to prevent revoked vectors from being recovered or re-indexed.

 #8.3.1    Level: 1    Role: D/V
 Verify that every vector and metadata record carries a TTL or explicit retention label honored by automated cleanup jobs.
 #8.3.2    Level: 1    Role: D/V
 Verify that user-initiated deletion requests purge vectors, metadata, cache copies, and derivative indices within 30 days.
 #8.3.3    Level: 2    Role: D
 Verify that logical deletions are followed by cryptographic shredding of storage blocks if hardware supports it, or by key-vault key destruction.
 #8.3.4    Level: 3    Role: D/V
 Verify that expired vectors are excluded from nearest-neighbor search results within 500 ms of expiration.

---

### C8.4 Prevent Embedding Inversion and Leakage

Recent defenses—noise superposition, projection networks, privacy-neuron perturbation, and application-layer encryption—can cut token-level inversion rates below 5%.

 #8.4.1    Level: 1    Role: V
 Verify that a formal threat model covering inversion, membership, and attribute-inference attacks exists and is reviewed annually.
 #8.4.2    Level: 2    Role: D/V
 Verify that application-layer encryption or searchable encryption shields vectors from direct reads by infrastructure administrators or cloud staff.
 #8.4.3    Level: 3    Role: V
 Verify that the defense parameters (ε for DP, noise σ, and projection rank k) balance privacy (≥ 99 % token protection) and utility (≤ 3 % accuracy loss).
 #8.4.4    Level: 3    Role: D/V
 Verify that inversion-resilience metrics are part of release gates for model updates, with regression budgets defined.

---

### C8.5 Scope Enforcement for User-Specific Memory

Cross-tenant leakage remains a top RAG risk: improperly filtered similarity queries can surface another customer's private documents.

 #8.5.1    Level: 1    Role: D/V
 Verify that every retrieval query is post-filtered by tenant or user ID before being passed to the LLM prompt.
 #8.5.2    Level: 1    Role: D
 Verify that collection names or namespaced IDs are salted per user or per tenant to prevent vector collisions across scopes.
 #8.5.3    Level: 2    Role: D/V
 Verify that similarity results that exceed a configurable distance threshold and lie outside the caller's scope are discarded and trigger security alerts.
 #8.5.4    Level: 2    Role: V
 Verify that multi-tenant stress tests simulate adversarial queries aimed at retrieving out-of-scope documents and demonstrate no leakage.
 #8.5.5    Level: 3    Role: D/V
 Verify that encryption keys are segregated by tenant, ensuring cryptographic isolation even when physical storage is shared.

---

### C8.6 Advanced Memory System Security

Security controls for sophisticated memory architectures, including episodic, semantic, and working memory, with specific isolation and validation requirements.

 #8.6.1    Level: 1    Role: D/V
 Verify that each memory type (episodic, semantic, and working) has isolated security contexts with role-based access controls, separate encryption keys, and documented access patterns.
 #8.6.2    Level: 2    Role: D/V
 Verify that memory consolidation processes include security validation to prevent the injection of malicious memories through content sanitization, source verification, and integrity checks prior to storage.
 #8.6.3    Level: 2    Role: D/V
 Verify that memory retrieval queries are validated and sanitized to prevent unauthorized information extraction through query pattern analysis, access control enforcement, and result filtering.
 #8.6.4    Level: 3    Role: D/V
 Verify that memory-erasure mechanisms securely delete sensitive information with cryptographic erasure guarantees, using key deletion, multi-pass overwriting, or hardware-based secure deletion with verification certificates.
 #8.6.5    Level: 3    Role: D/V
 Verify that memory system integrity is continuously monitored for unauthorized modifications or corruption through checksums, audit logs, and automated alerts whenever memory contents change outside normal operations.

---

### References

Vector database security: Pinecone – IronCore Labs
Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera
Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances
Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv
DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview
Art. 17 GDPR – Right to Erasure
Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai
PII Identification and Removal – NVIDIA NeMo Docs
De-identifying Sensitive Data – Google Cloud DLP
Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails
Think Your RAG Is Secure? Think Again – Medium
Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn
Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog

## 9 Autonomous Orchestration and Agentic Action Security

### Control Objective

Ensure that autonomous or multi-agent AI systems can only execute actions that are explicitly intended, authenticated, auditable, and within bounded cost and risk thresholds. This protects against threats such as Autonomous-System Compromise, Tool Misuse, Agent Loop Detection, Communication Hijacking, Identity Spoofing, Swarm Manipulation, and Intent Manipulation.

---

### 9.1 Agent Task-Planning & Recursion Budgets

Throttle recursive plans and require human checkpoints for privileged actions.

 #9.1.1    Level: 1    Role: D/V
 Verify that the maximum recursion depth, breadth, wall-clock time, tokens, and monetary cost per agent execution are centrally configured and version-controlled.
 #9.1.2    Level: 1    Role: D/V
 Verify that privileged or irreversible actions (e.g., code commits, financial transfers) require explicit human approval via an auditable channel before execution.
 #9.1.3    Level: 2    Role: D
 Verify that real-time resource monitors trigger circuit-breaker interruptions whenever any budget threshold is exceeded, thereby halting further task expansion.
 #9.1.4    Level: 2    Role: D/V
 Verify that circuit-breaker events are logged with an agent ID, a triggering condition, and the captured plan state for forensic review.
 #9.1.5    Level: 3    Role: V
 Verify that security tests cover budget-exhaustion and runaway-plan scenarios, and confirm safe halting without data loss.
 #9.1.6    Level: 3    Role: D
 Verify that budget policies are expressed as policy-as-code and enforced in CI/CD to prevent configuration drift.

---

### 9.2 Tool Plugin Sandboxing

Isolate tool interactions to prevent unauthorized access to the system or code execution.

 #9.2.1    Level: 1    Role: D/V
 Verify that every tool or plugin runs inside an OS, container, or WASM-level sandbox with least-privilege file-system, network, and system-call policies.
 #9.2.2    Level: 1    Role: D/V
 Verify that sandbox resource quotas (CPU, memory, disk, network egress) and execution timeouts are enforced and logged.
 #9.2.3    Level: 2    Role: D/V
 Verify that tool binaries or descriptors are digitally signed and that signatures are validated before loading.
 #9.2.4    Level: 2    Role: V
 Verify that sandbox telemetry is streamed to a SIEM, and that anomalies (e.g., attempted outbound connections) raise alerts.
 #9.2.5    Level: 3    Role: V
 Ensure that high-risk plugins undergo security review and penetration testing before deployment to production.
 #9.2.6    Level: 3    Role: D/V
 Verify that sandbox escape attempts are automatically blocked and that the offending plugin is quarantined pending investigation.

---

### 9.3 Autonomous Loop and Cost Bounding

Detect and stop uncontrolled agent-to-agent recursion and the resulting cost explosions.

 #9.3.1    Level: 1    Role: D/V
 Verify that inter-agent calls include a hop-limit or TTL that the runtime decrements and enforces.
 #9.3.2    Level: 2    Role: D
 Verify that agents maintain a unique invocation-graph ID to detect self-invocation or cyclical patterns.
 #9.3.3    Level: 2    Role: D/V
 Verify that the cumulative compute-unit and spend counters are tracked per request chain; breaching the limit aborts the chain.
 #9.3.4    Level: 3    Role: V
 Verify that formal analysis or model checking demonstrates the absence of unbounded recursion in agent protocols.
 #9.3.5    Level: 3    Role: D
 Verify that loop-abort events generate alerts and feed continuous-improvement metrics.

---

### 9.4 Protocol-Level Misuse Protection

Secure the communication channels between agents and external systems to prevent hijacking or manipulation.

 #9.4.1    Level: 1    Role: D/V
 Verify that all agent-to-tool and agent-to-agent messages are authenticated (for example, using mutual TLS or JWT) and end-to-end encrypted.
 #9.4.2    Level: 1    Role: D
 Verify that schemas are strictly validated, and that unknown fields or malformed messages are rejected.
 #9.4.3    Level: 2    Role: D/V
 Verify that integrity checks (MACs or digital signatures) cover the entire message payload, including tool parameters.
 #9.4.4    Level: 2    Role: D
 Verify that replay protection (nonces or timestamp windows) is enforced at the protocol layer.
 #9.4.5    Level: 3    Role: V
 Verify that protocol implementations undergo fuzzing and static analysis to detect injection or deserialization flaws.

---

### 9.5 Agent Identity and Tamper Evidence

Ensure actions are attributable and modifications are detectable.

 #9.5.1    Level: 1    Role: D/V
 Verify that each agent instance has a unique cryptographic identity (key-pair or hardware-rooted credential).
 #9.5.2    Level: 2    Role: D/V
 Verify that all agent actions are signed and timestamped, and that logs include signatures for non-repudiation.
 #9.5.3    Level: 2    Role: V
 Verify that tamper-evident logs are stored on an append-only or write-once medium.
 #9.5.4    Level: 3    Role: D
 Verify that identity keys rotate on a defined schedule and in response to indicators of compromise.
 #9.5.5    Level: 3    Role: D/V
 Verify that spoofing or key-conflict attempts trigger an immediate quarantine of the affected agent.

---

### 9.6 Multi-Agent Swarm Risk Reduction

Mitigate hazards arising from collective behavior through isolation and formal safety modeling.

 #9.6.1    Level: 1    Role: D/V
 Verify that agents operating in different security domains execute within isolated runtime sandboxes or network segments.
 #9.6.2    Level: 3    Role: V
 Verify that swarm behaviors are modeled and formally verified for liveness and safety prior to deployment.
 #9.6.3    Level: 3    Role: D
 Verify that runtime monitors detect emerging unsafe patterns, such as oscillations or deadlocks, and trigger corrective action.

---

### 9.7 User and Tool Authentication / Authorization

Implement robust access controls for every agent-triggered action.

 #9.7.1    Level: 1    Role: D/V
 Verify that agents authenticate to downstream systems as first-class principals, and never reuse end-user credentials.
 #9.7.2    Level: 2    Role: D
 Verify that fine-grained authorization policies restrict the tools an agent may invoke and the parameters it may supply.
 #9.7.3    Level: 2    Role: V
 Verify that privilege checks are re-evaluated on every call (continuous authorization), and not only at session start.
 #9.7.4    Level: 3    Role: D
 Verify that delegated privileges expire automatically and require re-consent after a timeout or a change in scope.

---

### 9.8 Agent-to-Agent Communication Security

Encrypt all inter-agent messages and ensure their integrity to thwart eavesdropping and tampering.

 #9.8.1    Level: 1    Role: D/V
 Verify that mutual authentication and perfect forward secrecy (e.g., TLS 1.3) are mandatory for agent channels.
 #9.8.2    Level: 1    Role: D
 Ensure that the message's integrity and origin are validated before processing; if validation fails, raise alerts and drop the message.
 #9.8.3    Level: 2    Role: D/V
 Verify that communication metadata (timestamps and sequence numbers) are logged to support forensic reconstruction.
 #9.8.4    Level: 3    Role: V
 Verify that formal verification or model checking demonstrates that protocol state machines cannot be driven into unsafe states.

---

### 9.9 Intent Verification and Constraint Enforcement

Validate that the agent's actions align with the user's stated intent and system constraints.

 #9.9.1    Level: 1    Role: D
 Verify that pre-execution constraint solvers validate proposed actions against hard-coded safety and policy rules.
 #9.9.2    Level: 2    Role: D/V
 Verify that high-impact actions (financial, destructive, privacy-sensitive) require explicit confirmation of intent from the initiating user.
 #9.9.3    Level: 2    Role: V
 Verify that post-condition checks confirm that completed actions achieved their intended effects without side effects; any discrepancies trigger a rollback.
 #9.9.4    Level: 3    Role: V
 Verify that formal methods (for example, model checking and theorem proving) or property-based tests demonstrate that agent plans satisfy all declared constraints.
 #9.9.5    Level: 3    Role: D
 Verify that incidents of intent-mismatch or constraint-violation feed continuous-improvement cycles and threat-intel sharing.

---

### 9.10 Agent Reasoning Strategy Security

Securely select and execute various reasoning strategies, including ReAct, Chain-of-Thought, and Tree-of-Thoughts approaches.

 #9.10.1    Level: 1    Role: D/V
 Verify that reasoning strategy selection uses deterministic criteria (input complexity, task type, security context), and that identical inputs produce identical strategy selections within the same security context.
 #9.10.2    Level: 1    Role: D/V
 Verify that each reasoning strategy (ReAct, Chain-of-Thought, Tree-of-Thoughts) has dedicated input validation, output sanitization, and execution time limits specific to its cognitive approach.
 #9.10.3    Level: 2    Role: D/V
 Verify that reasoning strategy transitions are logged with complete context, including input characteristics, selection criteria values, and execution metadata for audit trail reconstruction.
 #9.10.4    Level: 2    Role: D/V
 Verify that Tree-of-Thoughts reasoning includes branch pruning mechanisms that terminate exploration when policy violations, resource limits, or safety boundaries are detected.
 #9.10.5    Level: 2    Role: D/V
 Verify that ReAct (Reason-Act-Observe) cycles include validation checkpoints at each phase: reasoning-step verification, action authorization, and observation sanitization before proceeding.
 #9.10.6    Level: 3    Role: D/V
 Verify that reasoning strategy performance metrics (execution time, resource usage, and output quality) are monitored with automated alerts when metrics deviate from configured thresholds.
 #9.10.7    Level: 3    Role: D/V
 Verify that hybrid reasoning approaches, which combine multiple strategies, maintain the input validation and the output constraints of all constituent strategies, without bypassing any security controls.
 #9.10.8    Level: 3    Role: D/V
 Verify that security testing of reasoning strategies includes fuzzing with malformed inputs, adversarial prompts designed to force strategy switching, and boundary condition testing for each cognitive approach.

---

### 9.11 Agent Lifecycle State Management and Security

Secure agent initialization, state transitions, and termination, with cryptographic audit trails and defined recovery procedures.

 #9.11.1    Level: 1    Role: D/V
 Verify that agent initialization includes cryptographic identity establishment with hardware-backed credentials and immutable startup audit logs containing agent ID, timestamp, configuration hash, and initialization parameters.
 #9.11.2    Level: 2    Role: D/V
 Ensure that agent state transitions are cryptographically signed, timestamped, and logged with complete context, including the triggering events, the previous state hash, the new state hash, and the security validations performed.
 #9.11.3    Level: 2    Role: D/V
 Verify that agent shutdown procedures include secure memory wiping via cryptographic erasure or multi-pass overwriting, credential revocation with notification to the certificate authority, and the generation of tamper-evident termination certificates.
 #9.11.4    Level: 3    Role: D/V
 Verify that agent recovery mechanisms validate state integrity using cryptographic checksums (minimum SHA-256) and roll back to known-good states when corruption is detected, with automated alerts and manual approval requirements.
 #9.11.5    Level: 3    Role: D/V
 Verify that agent persistence mechanisms encrypt sensitive state data using per-agent AES-256 keys and implement secure key rotation on configurable schedules (maximum 90 days) with zero-downtime deployment.

---

### 9.12 Tool Integration Security Framework

Security controls for dynamic tool loading, execution, and result validation, with defined risk assessment and approval processes.

 #9.12.1    Level: 1    Role: D/V
 Verify that tool descriptors include security metadata that specifies the required privileges (read, write, and execute), risk levels (low, medium, high), resource limits (CPU, memory, network), and validation requirements documented in the tool manifests.
 #9.12.2    Level: 1    Role: D/V
 Verify that tool execution results are validated against the expected schemas (JSON Schema, XML Schema) and security policies (output sanitization, data classification) before integration, with timeout limits and error handling procedures.
 #9.12.3    Level: 2    Role: D/V
 Verify that tool interaction logs include detailed security context, including privilege usage, data access patterns, execution time, resource consumption, and return codes, with structured logging for SIEM integration.
 #9.12.4    Level: 2    Role: D/V
 Verify that dynamic tool loading mechanisms validate digital signatures using PKI infrastructure and implement secure loading protocols with sandbox isolation and permission verification prior to execution.
 #9.12.5    Level: 3    Role: D/V
 Verify that tool security assessments are automatically triggered for new versions, with mandatory approval gates including static analysis, dynamic testing, and security team review, along with documented approval criteria and SLA requirements.

---

#### References

MITRE ATLAS tactics ML09
Circuit-breaker research for AI agents — Zou et al., 2024
Trend Micro analysis of sandbox escapes in AI agents — Park, 2025
Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025
Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025
Rapid7 fundamentals on spoofing attack prevention — 2024
Imperial College verification of swarm systems — Lomuscio et al.
NIST AI Risk Management Framework 1.0, 2023
WIRED security briefing on encryption best practices, 2024
OWASP Top 10 for LLM Applications, 2025
Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS
[How Is LLM Reasoning Distracted by Irrelevant Context?
An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
Large Language Model Sentinel: LLM Agent for Adversarial Purification
Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents

## 10 Adversarial Robustness and Privacy Defense

### Control Objective

Ensure that AI models remain reliable, privacy-preserving, and abuse-resistant when faced with evasion, inference, extraction, or poisoning attacks.

---

### 10.1 Model Alignment and Safety

Guard against harmful or policy-breaking outputs.

 #10.1.1    Level: 1    Role: D/V
 Verify that an alignment test-suite (red-team prompts, jailbreak probes, and disallowed content) is version-controlled and run on every model release.
 #10.1.2    Level: 1    Role: D
 Verify that the refusal and safe-completion guard-rails are enforced.
 #10.1.3    Level: 2    Role: D/V
 Verify that an automated evaluator measures the rate of harmful content and flags regressions that exceed a set threshold.
 #10.1.4    Level: 2    Role: D
 Verify that counter-jailbreak training is thoroughly documented and reproducible.
 #10.1.5    Level: 3    Role: V
 Verify that formal policy-compliance proofs or certified monitoring cover the critical domains.

---

### 10.2 Adversarial-Example Hardening

Increase resilience to manipulated inputs. Robust adversarial training and benchmark scoring are the current best practices.

 #10.2.1    Level: 1    Role: D
 Verify that project repositories include adversarial training configurations with reproducible seeds.
 #10.2.2    Level: 2    Role: D/V
 Verify that adversarial-example detection raises blocking alerts in production pipelines.
 #10.2.4    Level: 3    Role: V
 Verify that certified‐robustness proofs or interval-bound certificates cover at least the top critical classes.
 #10.2.5    Level: 3    Role: V
 Verify that regression tests use adaptive attacks to confirm that there is no measurable loss of robustness.

---

### 10.3 Membership-Inference Mitigation

Limit the ability to determine whether a record was part of the training data. Differential privacy and confidence-score masking remain the most effective known defenses.

 #10.3.1    Level: 1    Role: D
 Verify that per-query entropy regularization or temperature-scaling reduces overconfident predictions.
 #10.3.2    Level: 2    Role: D
 Verify that training employs ε-bounded differentially-private optimization for sensitive datasets.
 #10.3.3    Level: 2    Role: V
 Verify that attack simulations (shadow-model or black-box) yield an attack AUC of ≤ 0.60 on held-out data.

---

### 10.4 Model-Inversion Resistance

Prevent reconstruction of private attributes. Recent surveys emphasize output truncation and differential privacy guarantees as practical defenses.

 #10.4.1    Level: 1    Role: D
 Verify that sensitive attributes are never output directly; where necessary, use buckets or one-way transformations.
 #10.4.2    Level: 1    Role: D/V
 Verify that query-rate limits throttle repeated adaptive queries from the same principal.
 #10.4.3    Level: 2    Role: D
 Verify that the model has been trained with privacy-preserving noise.

---

### 10.5 Model-Extraction Defense

Detect and deter unauthorized cloning. Watermarking and query-pattern analysis are recommended.

 #10.5.1    Level: 1    Role: D
 Verify that inference gateways enforce global and per-API-key rate limits, tuned to the model’s memorization threshold.
 #10.5.2    Level: 2    Role: D/V
 Verify that the query-entropy and input-plurality statistics feed an automated extraction detector.
 #10.5.3    Level: 2    Role: V
 Verify that fragile or probabilistic watermarks can be proven with p < 0.01 in ≤ 1 000 queries against a suspected clone.
 #10.5.4    Level: 3    Role: D
 Verify that watermark keys and trigger sets are stored in a hardware-security-module and rotated annually.
 #10.5.5    Level: 3    Role: V
 Verify that extraction-alert events include offending queries and are integrated with incident-response playbooks.

---

### 10.6 Inference-Time Poisoned-Data Detection

Identify and neutralize backdoored or poisoned inputs.

 #10.6.1    Level: 1    Role: D
 Verify that inputs pass through an anomaly detector (e.g., STRIP, consistency-scoring) before model inference.
 #10.6.2    Level: 1    Role: V
 Verify that detector thresholds are tuned on clean and poisoned validation sets to achieve less than 5% false positives.
 #10.6.3    Level: 2    Role: D
 Verify that inputs flagged as poisoned trigger soft-blocking and human review workflows.
 #10.6.4    Level: 2    Role: V
 Verify that detectors are stress-tested against adaptive, triggerless backdoor attacks.
 #10.6.5    Level: 3    Role: D
 Verify that detection efficacy metrics are logged and periodically re-evaluated with up-to-date threat intelligence.

---

### 10.7 Dynamic Security Policy Adaptation

Real-time security policy updates based on threat intelligence and behavioral analysis.

 #10.7.1    Level: 1    Role: D/V
 Verify that security policies can be updated dynamically without restarting the agent, while maintaining the integrity of policy versions.
 #10.7.2    Level: 2    Role: D/V
 Verify that policy updates are cryptographically signed by authorized security personnel and validated before they are applied.
 #10.7.3    Level: 2    Role: D/V
 Verify that dynamic policy changes are logged with complete audit trails, including justification, approval chains, and rollback procedures.
 #10.7.4    Level: 3    Role: D/V
 Verify that adaptive security mechanisms adjust threat detection sensitivity based on risk context and behavioral patterns.
 #10.7.5    Level: 3    Role: D/V
 Verify that policy adaptation decisions are explainable and provide evidence trails for review by the security team.

---

### 10.8 Reflection-Based Security Analysis

Security validation through agent self-reflection and meta-cognitive analysis.

 #10.8.1    Level: 1    Role: D/V
 Verify that agent reflection mechanisms include a security-focused self-assessment of decisions and actions.
 #10.8.2    Level: 2    Role: D/V
 Verify that reflection outputs are validated to prevent adversarial inputs from manipulating self-assessment mechanisms.
 #10.8.3    Level: 2    Role: D/V
 Verify that a meta-cognitive security analysis identifies potential bias, manipulation, or compromise in an agent's reasoning processes.
 #10.8.4    Level: 3    Role: D/V
 Verify that reflection-based security warnings trigger enhanced monitoring and workflows for potential human intervention.
 #10.8.5    Level: 3    Role: D/V
 Verify that continuous learning from security reflections improves threat detection without degrading legitimate functionality.

---

### 10.9 Evolution and Self-Improvement Security

Security controls for agent systems capable of self-modification and evolution.

 #10.9.1    Level: 1    Role: D/V
 Verify that self-modification capabilities are restricted to designated safe areas and bounded by formal verification boundaries.
 #10.9.2    Level: 2    Role: D/V
 Verify that evolution proposals undergo a security impact assessment before implementation.
 #10.9.3    Level: 2    Role: D/V
 Verify that self-improvement mechanisms include rollback capabilities with integrity verification.
 #10.9.4    Level: 3    Role: D/V
 Verify that the security of meta-learning prevents adversarial manipulation of improvement algorithms.
 #10.9.5    Level: 3    Role: D/V
 Verify that recursive self-improvement is bounded by formal safety constraints, with mathematical proofs of convergence.

---

#### References

MITRE ATLAS adversary tactics for ML
NIST AI Risk Management Framework 1.0, 2023
OWASP Top 10 for LLM Applications, 2025
Adversarial Training: A Survey — Zhao et al., 2024
RobustBench adversarial-robustness benchmark
Membership-Inference & Model-Inversion Risk Survey, 2025
PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023
Model-Inversion Attacks & Defenses Survey — AI Review, 2025
Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024
Fragile Model Watermarking Survey — 2025
Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025
BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024

## 11 Privacy Protection & Personal Data Management

### Control Objective

Maintain rigorous privacy assurances across the entire AI lifecycle—collection, training, inference, and incident response—so that personal data are processed only with clear consent, the minimum necessary scope, provable erasure, and formal privacy guarantees.

---

### 11.1 Anonymization and Data Minimization

 #11.1.1    Level: 1    Role: D/V
 Verify that direct and quasi-identifiers are removed and hashed.
 #11.1.2    Level: 2    Role: D/V
 Verify that automated audits measure k-anonymity and l-diversity, and alert when thresholds fall below policy.
 #11.1.3    Level: 2    Role: V
 Verify that model feature-importance reports demonstrate that no identifier leakage occurs beyond ε = 0.01 mutual information.
 #11.1.4    Level: 3    Role: V
 Verify that formal proofs or synthetic-data certifications show that the re-identification risk is ≤ 0.05, even under linkage attacks.

---

### 11.2 Right-to-be-Forgotten and Deletion Enforcement

 #11.2.1    Level: 1    Role: D/V
 Verify that data-subject deletion requests propagate to raw datasets, checkpoints, embeddings, logs, and backups within service level agreements of less than 30 days.
 #11.2.2    Level: 2    Role: D
 Verify that "machine-unlearning" routines physically re-train or approximate removal using certified unlearning algorithms.
 #11.2.3    Level: 2    Role: V
 Verify that the shadow-model evaluation demonstrates that forgotten records influence fewer than 1% of outputs after unlearning.
 #11.2.4    Level: 3    Role: V
 Verify that deletion events are immutably logged and auditable by regulators.

---

### 11.3 Differential-Privacy Safeguards

 #11.3.1    Level: 2    Role: D/V
 Verify that privacy-loss accounting dashboards alert when the cumulative ε exceeds policy thresholds.
 #11.3.2    Level: 2    Role: V
 Verify that black-box privacy audits estimate ε̂ within 10% of the declared value.
 #11.3.3    Level: 3    Role: V
 Verify that formal proofs cover all post-training fine-tuning and embeddings.

---

### 11.4 Purpose-Limitation and Scope-Creep Protection

 #11.4.1    Level: 1    Role: D
 Verify that every dataset and model checkpoint carries a machine-readable purpose tag aligned with the original consent.
 #11.4.2    Level: 1    Role: D/V
 Verify that runtime monitors detect queries that are inconsistent with the declared purpose and trigger a soft refusal.
 #11.4.3    Level: 3    Role: D
 Verify that policy-as-code gates prevent the redeployment of models to new domains without a DPIA review.
 #11.4.4    Level: 3    Role: V
 Verify that formal traceability proofs demonstrate that every personal data lifecycle remains within the consented scope.

---

### 11.5 Consent Management and Lawful-Basis Tracking

 #11.5.1    Level: 1    Role: D/V
 Verify that a Consent-Management Platform (CMP) records the opt-in status, purpose, and retention period per data-subject.
 #11.5.2    Level: 2    Role: D
 Verify that APIs expose consent tokens, and that models validate the token scope before inference.
 #11.5.3    Level: 2    Role: D/V
 Verify that denied or withdrawn consent halts processing pipelines within 24 hours.

---

### 11.6 Federated Learning with Privacy Controls

 #11.6.1    Level: 1    Role: D
 Verify that client updates apply locally added differential privacy noise before aggregation.
 #11.6.2    Level: 2    Role: D/V
 Verify that training metrics are differentially private and never reveal any single client's loss.
 #11.6.3    Level: 2    Role: V
 Verify that poisoning-resistant aggregation (e.g., Krum/Trimmed-Mean) is enabled.
 #11.6.4    Level: 3    Role: V
 Verify that formal proofs demonstrate an overall ε budget with less than 5 units of utility loss.

---

#### References

GDPR & AI Compliance Best Practices
EU Parliament Study on GDPR & AI, 2020
ISO 31700-1:2023 — Privacy by Design for Consumer Products
NIST Privacy Framework 1.1 (2025 Draft)
Machine Unlearning: Right-to-Be-Forgotten Techniques
A Survey of Machine Unlearning, 2024
Auditing DP-SGD — ArXiv 2024
DP-SGD Explained — PyTorch Blog
Purpose-Limitation for AI — IJLIT 2025
Data-Protection Considerations for AI — URM Consulting
Top Consent-Management Platforms, 2025
Secure Aggregation in DP Federated Learning — ArXiv 2024

## C12 Monitoring, Logging, and Anomaly Detection

### Control Objective

This section outlines the requirements for delivering real-time and forensic visibility into what the model and other AI components see, do, and return, so threats can be detected, triaged, and learned from.

### C12.1 Request and Response Logging

 #12.1.1    Level: 1    Role: D/V
 Verify that all user prompts and model responses are logged with appropriate metadata, such as timestamp, user ID, session ID, and model version.
 #12.1.2    Level: 1    Role: D/V
 Verify that logs are stored in secure, access-controlled repositories that enforce appropriate retention policies and backup procedures.
 #12.1.3    Level: 1    Role: D/V
 Verify that log storage systems implement encryption at rest and in transit to protect sensitive information contained in logs.
 #12.1.4    Level: 1    Role: D/V
 Verify that sensitive data in prompts and outputs is automatically redacted or masked before logging, with configurable redaction rules for PII, credentials, and proprietary information.
 #12.1.5    Level: 2    Role: D/V
 Verify that policy decisions and safety-filtering actions are logged with sufficient detail to enable auditing and debugging of content moderation systems.
 #12.1.6    Level: 2    Role: D/V
 Verify that log integrity is protected, for example, by cryptographic signatures or by write-only storage.

---

### C12.2 Abuse Detection and Alerting

 #12.2.1    Level: 1    Role: D/V
 Verify that the system detects and alerts for known jailbreak patterns, prompt-injection attempts, and adversarial inputs using signature-based detection.
 #12.2.2    Level: 1    Role: D/V
 Verify that the system integrates with existing Security Information and Event Management (SIEM) platforms using standard log formats and protocols.
 #12.2.3    Level: 2    Role: D/V
 Verify that enriched security events include AI-specific context, such as model identifiers, confidence scores, and safety filter decisions.
 #12.2.4    Level: 2    Role: D/V
 Verify that behavioral anomaly detection identifies unusual conversational patterns, excessive retry attempts, or systematic probing behaviors.
 #12.2.5    Level: 2    Role: D/V
 Verify that real-time alerting mechanisms notify the security teams whenever potential policy violations or attack attempts are detected.
 #12.2.6    Level: 2    Role: D/V
 Verify that custom rules are in place to detect AI-specific threat patterns, including coordinated jailbreak attempts, prompt injection campaigns, and model extraction attacks.
 #12.2.7    Level: 3    Role: D/V
 Verify that automated incident response workflows can isolate compromised models, block malicious users, and escalate critical security events.

---

### C12.3 Model Drift Detection

 #12.3.1    Level: 1    Role: D/V
 Verify that the system tracks basic performance metrics, such as accuracy, confidence scores, latency, and error rates, across model versions and over time.
 #12.3.2    Level: 2    Role: D/V
 Verify that automated alerts are triggered when performance metrics exceed predefined degradation thresholds or deviate significantly from baselines.
 #12.3.3    Level: 2    Role: D/V
 Verify that hallucination-detection monitors identify and flag instances where model outputs are factually incorrect, inconsistent, or fabricated.

---

### C12.4 Performance and Behavior Telemetry

 #12.4.1    Level: 1    Role: D/V
 Verify that operational metrics, including request latency, token consumption, memory usage, and throughput, are continuously collected and monitored.
 #12.4.2    Level: 1    Role: D/V
 Verify that success and failure rates are tracked, with categorization of error types and their root causes.
 #12.4.3    Level: 2    Role: D/V
 Verify that resource utilization monitoring includes GPU and CPU usage, memory consumption, and storage requirements, with alerting on threshold breaches.

---

### C12.5 AI Incident-Response Planning and Execution

 #12.5.1    Level: 1    Role: D/V
 Verify that incident response plans specifically address AI-related security events, including model compromise, data poisoning, and adversarial attacks.
 #12.5.2    Level: 2    Role: D/V
 Verify that incident response teams have access to AI-specific forensic tools and expertise to investigate model behavior and attack vectors.
 #12.5.3    Level: 3    Role: D/V
 Verify that post-incident analysis includes model retraining considerations, updates to safety filters, and integration of lessons learned into security controls.

---

### C12.5 AI Performance Degradation Detection

Monitor and detect degradation in AI model performance and quality over time.

 #12.5.1    Level: 1    Role: D/V
 Ensure that model accuracy, precision, recall, and F1 scores are continuously monitored and compared against baseline thresholds.
 #12.5.2    Level: 1    Role: D/V
 Verify that data-drift detection monitors changes in the input distribution that may affect model performance.
 #12.5.3    Level: 2    Role: D/V
 Verify that concept drift detection identifies changes in the relationship between inputs and their expected outputs.
 #12.5.4    Level: 2    Role: D/V
 Verify that performance degradation triggers automated alerts and initiates model retraining or replacement workflows.
 #12.5.5    Level: 3    Role: V
 Verify that degradation root-cause analysis correlates performance drops with data changes, infrastructure issues, or external factors.

---

### C12.6 DAG Visualization and Workflow Security

Protect workflow-visualization systems from information leakage and manipulation attacks.

 #12.6.1    Level: 1    Role: D/V
 Verify that DAG visualization data is sanitized to remove sensitive information before storage or transmission.
 #12.6.2    Level: 1    Role: D/V
 Verify that access controls for workflow visualization ensure that only authorized users can view agent decision paths and reasoning traces.
 #12.6.3    Level: 2    Role: D/V
 Verify that the integrity of DAG data is protected by cryptographic signatures and tamper-evident storage mechanisms.
 #12.6.4    Level: 2    Role: D/V
 Verify that workflow-visualization systems implement input validation to prevent injection attacks through crafted node or edge data.
 #12.6.5    Level: 3    Role: D/V
 Verify that real-time DAG updates are rate-limited and validated to prevent denial-of-service attacks on visualization systems.

---

### C12.7 Proactive Security Behavior Monitoring

Detection and prevention of security threats through proactive analysis of agent behavior.

 #12.7.1    Level: 1    Role: D/V
 Verify that proactive agent behaviors are security-validated before execution, with an integrated risk assessment.
 #12.7.2    Level: 2    Role: D/V
 Verify that autonomous initiative triggers include security context evaluation and threat landscape assessment.
 #12.7.3    Level: 2    Role: D/V
 Ensure that proactive behavior patterns are analyzed for potential security implications and unintended consequences.
 #12.7.4    Level: 3    Role: D/V
 Verify that security-critical proactive actions require explicit approval chains with audit trails.
 #12.7.5    Level: 3    Role: D/V
 Verify that behavioral anomaly detection identifies deviations in proactive agent patterns that could indicate a compromise.

---

### References

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13: Human Oversight, Accountability and Governance

### Control Objective

This chapter sets forth requirements for maintaining human oversight and clear accountability chains within AI systems, ensuring explainability, transparency, and ethical stewardship throughout the AI lifecycle.

---

### C13.1 Kill-Switch and Override Mechanisms

Provide shutdown or rollback paths when unsafe behavior by the AI system is observed.

 #13.1.1    Level: 1    Role: D/V
 Verify that a manual kill-switch mechanism exists to immediately halt AI model inference and its outputs.
 #13.1.2    Level: 1    Role: D
 Verify that override controls are accessible only to authorized personnel.
 #13.1.3    Level: 3    Role: D/V
 Verify that rollback procedures can revert to earlier model versions or operate in safe mode.
 #13.1.4    Level: 3    Role: V
 Verify that the override mechanisms are tested regularly.

---

### C13.2 Human-in-the-Loop Decision Checkpoints

Require human approvals when the stakes exceed predefined risk thresholds.

 #13.2.1    Level: 1    Role: D/V
 Verify that high-risk AI decisions require explicit human approval before execution.
 #13.2.2    Level: 1    Role: D
 Verify that risk thresholds are clearly defined and that they automatically trigger human review workflows.
 #13.2.3    Level: 2    Role: D
 Verify that time-sensitive decisions have fallback procedures when human approval cannot be obtained within the required timeframes.
 #13.2.4    Level: 3    Role: D/V
 Verify that escalation procedures define clear authority levels for different types of decisions or risk categories, where applicable.

---

### C13.3 Chain of Responsibility and Auditability

Log the operator actions and model decisions.

 #13.3.1    Level: 1    Role: D/V
 Verify that all AI system decisions and human interventions are logged with timestamps, user identities, and the rationale for each decision.
 #13.3.2    Level: 2    Role: D
 Verify that audit logs cannot be tampered with, and include integrity verification mechanisms.

---

### C13.4 Explainable-AI Techniques

Surface feature importance, counterfactuals, and local explanations.

 #13.4.1    Level: 1    Role: D/V
 Verify that AI systems provide basic explanations for their decisions in a human-readable format.
 #13.4.2    Level: 2    Role: V
 Verify that the quality of explanations is validated through human evaluation studies and metrics.
 #13.4.3    Level: 3    Role: D/V
 Verify that feature importance scores or attribution methods (SHAP, LIME, etc.) are available for critical decisions.
 #13.4.4    Level: 3    Role: V
 Verify that counterfactual explanations demonstrate how inputs could be modified to change outcomes, where applicable to the use case and domain.

---

### C13.5 Model Cards & Usage Disclosures

Maintain model cards for intended use, performance metrics, and ethical considerations.

 #13.5.1    Level: 1    Role: D
 Verify that model cards document intended use cases, limitations, and known failure modes.
 #13.5.2    Level: 1    Role: D/V
 Verify that performance metrics for the various applicable use cases are disclosed.
 #13.5.3    Level: 2    Role: D
 Ensure that ethical considerations, bias assessments, fairness evaluations, training data characteristics, and known training data limitations are documented and regularly updated.
 #13.5.4    Level: 2    Role: D/V
 Verify that model cards are version-controlled and maintained throughout the model lifecycle, with change tracking.

---

### C13.6 Uncertainty Quantification

Propagate confidence scores or entropy measures in responses.

 #13.6.1    Level: 1    Role: D
 Verify that AI systems provide confidence scores or uncertainty measures alongside their outputs.
 #13.6.2    Level: 2    Role: D/V
 Verify that uncertainty thresholds trigger additional human review or alternative decision pathways.
 #13.6.3    Level: 2    Role: V
 Verify that uncertainty quantification methods are calibrated and validated against ground truth data.
 #13.6.4    Level: 3    Role: D/V
 Verify that uncertainty propagation is maintained throughout multi-step AI workflows.

---

### C13.7 User-Facing Transparency Reports

Provide periodic disclosures regarding incidents, drift, and data usage.

 #13.7.1    Level: 1    Role: D/V
 Verify that data usage policies and user consent management practices are clearly communicated to stakeholders.
 #13.7.2    Level: 2    Role: D/V
 Verify that AI impact assessments are conducted and that the results are included in the report.
 #13.7.3    Level: 2    Role: D/V
 Verify that regularly published transparency reports disclose AI incidents and operational metrics in reasonable detail.

#### References

EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
ISO/IEC 42001:2023 — AI Management Systems Requirements
NIST AI Risk Management Framework 1.0
NIST SP 800-53 Revision 5 — Security and Privacy Controls
A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)
Model Cards for Model Reporting (Mitchell et al., 2018)
Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)
ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods
IEEE 7001-2021 — Transparency of Autonomous Systems
GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Appendix A: Glossary

This comprehensive glossary provides definitions of key AI, ML, and security terms used throughout the AISVS to ensure clarity and common understanding.

Adversarial example: An input deliberately crafted to cause an AI model to make a mistake, often by introducing subtle perturbations that are imperceptible to humans.
​
Adversarial Robustness – In AI, adversarial robustness refers to a model's ability to maintain its performance and resist being fooled or manipulated by intentionally crafted, malicious inputs designed to cause errors.
​
Agent – AI agents are software systems that use AI to pursue goals and complete tasks on behalf of users. They exhibit reasoning, planning, and memory, and they possess a degree of autonomy to make decisions, learn, and adapt.
​
Agentic AI: AI systems that operate with some autonomy to achieve goals, often making decisions and taking actions without direct human intervention.
​
Attribute-Based Access Control (ABAC): an access-control paradigm in which authorization decisions are based on the attributes of the user, the resource, the action, and the environment, evaluated at query time.
​
Backdoor attack: a type of data-poisoning attack in which the model is trained to respond in a specific way to certain triggers, while behaving normally otherwise.
​
Bias: Systematic errors in AI model outputs that can lead to unfair or discriminatory outcomes for certain groups or in specific contexts.
​
Bias exploitation: An attack technique that exploits known biases in AI models to manipulate outputs or outcomes.
​
Cedar is Amazon's policy language and engine for fine-grained permissions used to implement ABAC for AI systems.
​
Chain of Thought: a technique for improving reasoning in language models by generating intermediate reasoning steps before producing a final answer.
​
Circuit Breakers: Mechanisms that automatically halt AI system operations when specific risk thresholds are exceeded.
​
Data leakage: Unintended exposure of sensitive information through AI model outputs or behaviors.
​
Data poisoning is the deliberate corruption of training data intended to compromise a model's integrity, often to install backdoors or degrade performance.
​
Differential privacy is a mathematically rigorous framework for releasing statistical information about datasets while protecting the privacy of individual data subjects. It enables data holders to share aggregate patterns of the group while limiting information leaked about specific individuals.
​
Embeddings: dense vector representations of data (text, images, etc.) that capture semantic meaning in a high-dimensional space.
​
Explainability in AI is the ability of an AI system to provide human-understandable reasons for its decisions and predictions, offering insights into its internal workings.
​
Explainable AI (XAI): AI systems designed to provide human-understandable explanations for their decisions and behaviors through various techniques and frameworks.
​
Federated learning is a machine learning approach in which models are trained across multiple decentralized devices that hold local data samples, without exchanging the data itself.
​
Guardrails: Constraints designed to prevent AI systems from producing outputs that are harmful, biased, or otherwise undesirable.
​
Hallucination – An AI hallucination refers to a phenomenon in which an AI model generates information that is incorrect or misleading and that is not based on its training data or factual reality.
​
Human-in-the-Loop (HITL): Systems that require human oversight, verification, or intervention at crucial decision points.
​
Infrastructure as Code (IaC): The practice of managing and provisioning infrastructure through code rather than manual processes, enabling security scanning and consistent deployments.
​
Jailbreak: Techniques for circumventing safety guardrails in AI systems, especially in large language models, to produce prohibited content.
​
Least Privilege: The security principle of granting only the minimum necessary access rights to users and processes.
​
LIME (Local Interpretable Model-agnostic Explanations) is a technique for explaining the predictions of any machine learning classifier by approximating it locally with an interpretable model.
​
Membership Inference Attack: A type of attack that aims to determine whether a specific data point was used to train a machine learning model.
​
MITRE ATLAS: Adversarial Threat Landscape for Artificial-Intelligence Systems, a knowledge base of adversarial tactics and techniques against AI systems.
​
Model Card – A model card is a document that provides standardized information about an AI model's performance, limitations, intended uses, and ethical considerations to promote transparency and responsible AI development.
​
Model extraction: An attack in which an adversary repeatedly queries a target model to create a functionally similar copy without authorization.
​
Model inversion: an attack that attempts to reconstruct training data by analyzing the model's outputs.
​
Model lifecycle management – AI model lifecycle management is the process of overseeing all stages of an AI model's existence, including its design, development, deployment, monitoring, maintenance, and eventual retirement, to ensure it remains effective and aligned with objectives.
​
Model Poisoning: Introducing vulnerabilities or backdoors directly into a model during training.
​
Model stealing/theft: Extracting a copy or an approximation of a proprietary model by repeatedly querying it.
​
A multi-agent system is a system composed of multiple interacting AI agents, each with potentially different capabilities and goals.
​
OPA (Open Policy Agent): an open-source policy engine that enables unified policy enforcement across the stack.
​
Privacy-Preserving Machine Learning (PPML): Techniques and methods for training and deploying ML models while protecting the privacy of the training data.
​
Prompt injection: An attack in which malicious instructions are embedded in inputs to override a model's intended behavior.
​
RAG (Retrieval-Augmented Generation) is a technique that enhances large language models by retrieving relevant information from external knowledge sources before generating a response.
​
Red-Teaming: the practice of actively testing AI systems by simulating adversarial attacks to identify vulnerabilities.
​
SBOM (Software Bill of Materials): A formal record detailing the components and their supply chain relationships used to build software or AI models.
​
SHAP (SHapley Additive exPlanations): A game-theoretic approach for explaining the output of any machine learning model by computing each feature's contribution to the prediction.
​
Supply-chain attack: compromising a system by targeting less-secure elements in its supply chain, such as third-party libraries, datasets, or pre-trained models.
​
Transfer learning: A technique in which a model developed for one task is reused as the starting point for a model intended for a second task.
​
Vector Database: A specialized database designed to store high-dimensional vectors (embeddings) and to perform efficient similarity searches.
​
Vulnerability scanning: Automated tools that identify known security vulnerabilities in software components, including AI frameworks and their dependencies.
​
Watermarking: Techniques for embedding imperceptible markers in AI-generated content to track its origin or detect AI generation.
​
Zero-day vulnerability: a previously unknown vulnerability that attackers can exploit before developers create and deploy a patch.

## Appendix B: References

### TODO

## Appendix C: AI Security Governance & Documentation

### Objective

This appendix outlines the foundational requirements for establishing organizational structures, policies, and processes to govern AI security throughout the system lifecycle.

---

### AC.1 AI Risk Management Framework Adoption

Provide a formal framework for identifying, assessing, and mitigating AI‑specific risks throughout the system lifecycle.

 #AC.1.1    Level: 1    Role: D/V
 Verify that an AI‑specific risk assessment methodology is documented and implemented.
 #AC.1.2    Level: 2    Role: D
 Verify that risk assessments are conducted at key points in the AI lifecycle and prior to significant changes.
 #AC.1.3    Level: 3    Role: D/V
 Verify that the risk management framework aligns with established standards, such as the NIST AI RMF.

---

### AC.2 AI Security Policy & Procedures

Define and enforce organizational standards for secure AI development, deployment, and operation.

 #AC.2.1    Level: 1    Role: D/V
 Verify that the documented AI security policies exist.
 #AC.2.2    Level: 2    Role: D
 Verify that policies are reviewed and updated at least annually and after significant threat‑landscape changes.
 #AC.2.3    Level: 3    Role: D/V
 Verify that policies address all AISVS categories and any applicable regulatory requirements.

---

### AC.3 Roles and Responsibilities for AI Security

Establish clear accountability for AI security across the organization.

 #AC.3.1    Level: 1    Role: D/V
 Verify that the roles and responsibilities for AI security are documented.
 #AC.3.2    Level: 2    Role: D
 Verify that responsible individuals possess the appropriate security expertise.
 #AC.3.3    Level: 3    Role: D/V
 Verify that an AI ethics committee or governance board has been established for high‑risk AI systems.

---

### AC.4: Ethical AI Guidelines Enforcement

Ensure that AI systems operate according to established ethical principles.

 #AC.4.1    Level: 1    Role: D/V
 Verify that ethical guidelines for AI development and deployment exist.
 #AC.4.2    Level: 2    Role: D
 Verify that there are mechanisms in place to detect and report ethical violations.
 #AC.4.3    Level: 3    Role: D/V
 Verify that regular ethical reviews of deployed AI systems are conducted.

---

### AC.5 AI Regulatory Compliance Monitoring

Maintain awareness of and compliance with evolving AI regulations.

 #AC.5.1    Level: 1    Role: D/V
 Verify that processes are in place to identify applicable AI regulations.
 #AC.5.2    Level: 2    Role: D
 Verify that compliance with all regulatory requirements is assessed.
 #AC.5.3    Level: 3    Role: D/V
 Ensure that regulatory changes trigger timely reviews and updates to AI systems.

### AC.6 Training Data Governance, Documentation, and Process

 #1.1.2    Level: 1    Role: D/V
 Verify that only datasets vetted for quality, representativeness, ethical sourcing, and license compliance are allowed, thereby reducing the risks of data poisoning, embedded bias, and intellectual property infringement.
 #1.1.5    Level: 2    Role: D/V
 Verify that labeling and annotation quality is ensured through reviewer cross-checks or consensus.
 #1.1.6    Level: 2    Role: D/V
 Verify that data cards or datasheets for datasets are maintained for significant training datasets, detailing their characteristics, motivations, composition, collection processes, preprocessing steps, and recommended or discouraged uses.
 #1.3.2    Level: 2    Role: D/V
 Verify that identified biases are mitigated through documented strategies such as re-balancing, targeted data augmentation, algorithmic adjustments (e.g., pre-processing, in-processing, post-processing techniques), or re-weighting, and that the impact of mitigation on both fairness and overall model performance is assessed.
 #1.3.3    Level: 2    Role: D/V
 Verify that post-training fairness metrics have been evaluated and documented.
 #1.3.4    Level: 3    Role: D/V
 Verify that a lifecycle bias-management policy assigns owners and a review cadence.
 #1.4.1    Level: 2    Role: D/V
 Verify that labeling/annotation quality is ensured through clear guidelines, reviewer cross-checks, consensus mechanisms (e.g., monitoring inter-annotator agreement), and defined processes for resolving discrepancies.
 #1.4.4    Level: 3    Role: D/V
 Verify that labels critical to safety, security, or fairness (e.g., identifying toxic content or critical medical findings) receive mandatory independent dual review or an equivalent robust verification.
 #1.4.6    Level: 2    Role: D/V
 Verify that labeling guides and instructions are comprehensive, version-controlled, and peer-reviewed.
 #1.4.6    Level: 2    Role: D/V
 Verify that the data schemas for labels are clearly defined and version-controlled.
 #1.3.1    Level: 1    Role: D/V
 Verify that datasets are profiled for representational imbalance and potential biases across legally protected attributes (e.g., race, gender, age) and other ethically sensitive characteristics relevant to the model's application domain (e.g., socio-economic status, location).
 #1.5.3    Level: 2    Role: V
 Verify that manual spot-checks by domain experts cover a statistically significant sample (e.g., ≥1% or 1,000 samples, whichever is greater, or as determined by risk assessment) to identify subtle quality issues that automation does not catch.
 #1.8.4    Level: 2    Role: D/V
 Verify that outsourced or crowdsourced labeling workflows incorporate technical and procedural safeguards to ensure data confidentiality, data integrity, and label quality, and to prevent data leakage.
 #1.5.4    Level: 2    Role: D/V
 Verify that remediation steps are appended to provenance records.
 #1.6.2    Level: 2    Role: D/V
 Verify that flagged samples trigger a manual review before training.
 #1.6.3    Level: 2    Role: V
 Verify that the results feed the model's security dossier and inform ongoing threat intelligence.
 #1.6.4    Level: 3    Role: D/V
 Verify that the detection logic is refreshed with new threat intelligence.
 #1.6.5    Level: 3    Role: D/V
 Verify that online-learning pipelines monitor distribution drift.
 #1.7.1    Level: 1    Role: D/V
 Verify that training data deletion workflows purge both primary and derived data and assess their impact on the models, and ensure that the impact on affected models is evaluated and, if necessary, addressed (e.g., through retraining or recalibration).
 #1.7.2    Level: 2    Role: D
 Verify that mechanisms exist to track and respect the scope and status of user consent (including withdrawals) for data used in training, and that consent is validated before data is incorporated into new training processes or significant model updates.
 #1.7.3    Level: 2    Role: V
 Verify that workflows are tested and logged annually.
 #1.8.1    Level: 2    Role: D/V
 Verify that third-party data suppliers, including providers of pre-trained models and external datasets, undergo security, privacy, ethical sourcing, and data quality due diligence before their data or models are integrated.
 #1.8.2    Level: 1    Role: D
 Verify that external transfers use TLS and authentication, along with integrity checks.
 #1.8.3    Level: 2    Role: D/V
 Verify that high-risk data sources (e.g., open-source datasets with unknown provenance or unvetted suppliers) receive enhanced scrutiny—such as sandboxed analysis, extensive quality and bias checks, and targeted poisoning detection—before being used in sensitive applications.
 #1.8.4    Level: 3    Role: D/V
 Verify that pre-trained models obtained from third parties are evaluated for embedded biases, potential backdoors, the integrity of their architecture, and the provenance of their original training data before they are fine-tuned or deployed.
 #1.5.3    Level: 2    Role: D/V
 Verify that, when adversarial training is used, the generation, management, and versioning of adversarial datasets are documented and controlled.
 #1.5.3    Level: 3    Role: D/V
 Verify that the impact of adversarial robustness training on model performance (for both clean and adversarial inputs) and on fairness metrics is evaluated, documented, and monitored.
 #1.5.4    Level: 3    Role: D/V
 Ensure that strategies for adversarial training and robustness are periodically reviewed and updated to counter evolving adversarial attack techniques.
 #1.4.2    Level: 2    Role: D/V
 Verify that failed datasets are quarantined and have audit trails.
 #1.4.3    Level: 2    Role: D/V
 Verify that quality gates block subpar datasets unless exceptions are approved.
 #1.11.2    Level: 2    Role: D/V
 Verify that the generation process, the parameters, and the intended use of synthetic data are documented.
 #1.11.3    Level: 2    Role: D/V
 Verify that synthetic data has been risk-assessed for bias, privacy leakage, and representational issues before use in training.
 #1.12.3    Level: 2    Role: D/V
 Verify that alerts are generated for suspicious access events and that they are investigated promptly.
 #1.13.1    Level: 1    Role: D/V
 Verify that explicit retention periods are defined for all training datasets.
 #1.13.2    Level: 2    Role: D/V
 Verify that datasets are automatically expired, deleted, or reviewed for deletion at the end of their lifecycle.
 #1.13.3    Level: 2    Role: D/V
 Verify that retention and deletion actions are logged and auditable.
 #1.14.1    Level: 2    Role: D/V
 Verify that data residency and cross-border transfer requirements are identified and enforced for all datasets.
 #1.14.2    Level: 2    Role: D/V
 Verify that sector-specific regulations, such as those for healthcare and finance, are identified and addressed in data handling.
 #1.14.3    Level: 2    Role: D/V
 Verify that compliance with relevant privacy laws (e.g., GDPR, CCPA) is documented and regularly reviewed.
 #1.16.1    Level: 2    Role: D/V
 Verify that mechanisms are in place to respond to data-subject requests for access, correction, restriction, or objection.
 #1.16.2    Level: 2    Role: D/V
 Verify that requests are logged, tracked, and fulfilled within legally mandated timeframes.
 #1.16.3    Level: 2    Role: D/V
 Verify that data subject rights processes are regularly tested and reviewed for effectiveness.
 #1.17.1    Level: 2    Role: D/V
 Verify that an impact analysis is conducted before updating or replacing a dataset version, and that it covers model performance, fairness, and compliance.
 #1.17.2    Level: 2    Role: D/V
 Verify that the results of the impact analysis are documented and reviewed by the relevant stakeholders.
 #1.17.3    Level: 2    Role: D/V
 Verify that rollback plans are in place in case new versions introduce unacceptable risks or regressions.
 #1.18.1    Level: 2    Role: D/V
 Verify that all personnel involved in data annotation have undergone background checks and are trained in data security and privacy.
 #1.18.2    Level: 2    Role: D/V
 Verify that all annotation personnel have signed confidentiality and non-disclosure agreements.
 #1.18.3    Level: 2    Role: D/V
 Verify that annotation platforms enforce access controls and monitor for insider threats.

#### References

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Appendix D: AI-Assisted Secure Coding Governance & Verification

### Objective

This chapter defines baseline organizational controls for the safe and effective use of AI-assisted coding tools in software development, ensuring security and traceability across the SDLC.

---

### AD.1 AI-Assisted Secure‑Coding Workflow

Integrate AI tooling into the organization’s secure‑software‑development lifecycle (SSDLC) without weakening existing security gates.

 #AD.1.1    Level: 1    Role: D/V
 Verify that the documented workflow specifies when and how AI tools may generate, refactor, or review code.
 #AD.1.2    Level: 2    Role: D
 Verify that the workflow maps to each SSDLC phase: design, implementation, code review, testing, and deployment.
 #AD.1.3    Level: 3    Role: D/V
 Verify that metrics (e.g., vulnerability density, mean‑time‑to‑detect) are collected from AI‑produced code and compared with human‑only baselines.

---

### AD.2 AI Tool Qualification and Threat Modeling

Ensure AI coding tools are evaluated for security capabilities, risks, and supply‑chain impact before adoption.

 #AD.2.1    Level: 1    Role: D/V
 Verify that a threat model for each AI tool identifies misuse, model‑inversion, data leakage, and dependency‑chain risks.
 #AD.2.2    Level: 2    Role: D
 Verify that tool evaluations include static and dynamic analysis of any local components, and assess SaaS endpoints (TLS, authentication/authorization, and logging).
 #AD.2.3    Level: 3    Role: D/V
 Verify that evaluations adhere to a recognized framework and are re‑performed after major version changes.

---

### AD.3 Secure Prompt and Context Management

Prevent the leakage of secrets, proprietary code, and personal data when constructing prompts or contexts for AI models.

 #AD.3.1    Level: 1    Role: D/V
 Verify that the written guidance prohibits sending secrets, credentials, or classified data in prompts.
 #AD.3.2    Level: 2    Role: D
 Verify that technical controls (client‑side redaction, approved context filters) automatically strip sensitive artifacts.
 #AD.3.3    Level: 3    Role: D/V
 Verify that prompts and responses are tokenized, encrypted in transit and at rest, and that retention periods comply with the data-classification policy.

---

### AD.4 Validation of AI‑Generated Code

Detect and remediate vulnerabilities introduced by AI-generated output before the code is merged or deployed.

 #AD.4.1    Level: 1    Role: D/V
 Verify that AI‑generated code is always subject to human code review.
 #AD.4.2    Level: 2    Role: D
 Verify that automated scanners (SAST/IAST/DAST) run on every pull request containing AI‑generated code and block merges when critical findings are detected.
 #AD.4.3    Level: 3    Role: D/V
 Verify that differential fuzz testing or property-based testing demonstrates security-critical behaviors (e.g., input validation and authorization logic).

---

### AD.5 Explainability and Traceability of Code Suggestions

Provide auditors and developers with insight into why a suggestion was made and how it evolved.

 #AD.5.1    Level: 1    Role: D/V
 Verify that prompt/response pairs are logged with commit IDs.
 #AD.5.2    Level: 2    Role: D
 Verify that developers can surface model citations (training snippets, documentation) that support a suggestion.
 #AD.5.3    Level: 3    Role: D/V
 Verify that explainability reports are stored with design artifacts and referenced in security reviews, in accordance with ISO/IEC 42001 traceability principles.

---

### AD.6 Continuous Feedback & Model Fine‑Tuning

Improve a model's security performance over time while preventing negative drift.

 #AD.6.1    Level: 1    Role: D/V
 Verify that developers can flag insecure or non‑compliant suggestions, and that those flags are tracked.
 #AD.6.2    Level: 2    Role: D
 Verify that aggregated feedback informs periodic fine‑tuning or retrieval‑augmented generation using vetted secure‑coding corpora (e.g., OWASP Cheat Sheets).
 #AD.6.3    Level: 3    Role: D/V
 Verify that a closed‑loop evaluation harness runs regression tests after each fine‑tune; security metrics must meet or exceed prior baselines before deployment.

---

#### References

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Appendix E: Examples of Tools and Frameworks

### Objective

This chapter provides examples of tooling and frameworks that can support the implementation or fulfillment of a given AISVS requirement. These should not be viewed as recommendations or endorsements by the AISVS team or the OWASP GenAI Security Project.

---

### AE.1 Training Data Governance and Bias Management

Tools used for data analytics, governance, and bias management.

 #AE.1.1    Section: 1.1
 Data Inventory Tooling: Examples of data inventory management tooling include...
 #AE.1.2    Section: 1.2
 Encryption-In-Transit: Use TLS for HTTPS-based applications, with tools like OpenSSL and Python's`ssl` Library.

---

### AE.2 User Input Validation

Tools to handle and validate user inputs.

 #AE.2.1    Section: 2.1
 Prompt-injection defense tooling: Use guardrail tooling such as NVIDIA's NeMo or Guardrails AI.

---

