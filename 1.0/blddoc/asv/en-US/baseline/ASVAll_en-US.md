## Frontispiece

### About the Standard

The Artificial Intelligence Security Verification Standard (AISVS) is a community-driven catalog of security requirements that data scientists, MLOps engineers, software architects, developers, testers, security professionals, tool vendors, regulators, and consumers can use to design, build, test, and verify trustworthy AI-enabled systems and applications. It provides a common language for specifying security controls throughout the AI lifecycle—from data collection and model development to deployment and ongoing monitoring—enabling organizations to measure and enhance the resilience, privacy, and safety of their AI solutions.

### Copyright and License

Version 0.1 (First Public Draft – Work in Progress), 2025  

![license](images/license.png)
Copyright © 2025 The AISVS Project.  

Released under theCreative Commons Attribution‑ShareAlike 4.0 International License.
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

AISVS is a brand-new standard created specifically to address the unique security challenges of artificial intelligence systems. While it draws inspiration from broader security best practices, every requirement in AISVS has been developed from the ground up to reflect the AI threat landscape and help organizations build safer, more resilient AI solutions.

## Preface

Welcome to the Artificial Intelligence Security Verification Standard (AISVS) version 1.0!

### Introduction

Established in 2025 through a collaborative community effort, AISVS defines the security requirements to consider when designing, developing, deploying, and operating modern AI models, pipelines, and AI-enabled services.

AISVS v1.0 represents the collaborative effort of its project leads, working group, and broader community contributors to establish a practical, testable baseline for securing AI systems.

Our goal with this release is to make AISVS easy to adopt while maintaining a sharp focus on its defined scope and addressing the rapidly evolving risk landscape unique to AI.

### Key Objectives for AISVS Version 1.0

Version 1.0 will be developed following several guiding principles.

#### Clearly Defined Scope

Each requirement must align with AISVS's name and mission:

Artificial Intelligence – Controls function at the AI/ML layer (data, model, pipeline, or inference) and fall under the responsibility of AI practitioners.
Security – Requirements directly address identified security, privacy, or safety risks.
Verification – The language is written to ensure conformance can be objectively validated.
Standard – Sections follow a consistent structure and terminology to create a coherent reference.
​
---

By following AISVS, organizations can systematically assess and enhance the security posture of their AI solutions, promoting a culture of secure AI engineering.

## Using the AISVS

The Artificial Intelligence Security Verification Standard (AISVS) defines security requirements for modern AI applications and services, focusing on aspects that are within the control of application developers.

The AISVS is designed for anyone involved in developing or assessing the security of AI applications, including developers, architects, security engineers, and auditors. This chapter introduces the structure and usage of the AISVS, covering its verification levels and intended use cases.

### Artificial Intelligence Security Verification Levels

The AISVS defines three ascending levels of security verification. Each level adds greater depth and complexity, allowing organizations to tailor their security posture to the risk level of their AI systems.

Organizations may start at Level 1 and gradually advance to higher levels as their security maturity and threat exposure grow.

#### Definition of the Levels

Each requirement in AISVS v1.0 is assigned to one of the following levels:

 Level 1 requirements

Level 1 includes the most critical and foundational security requirements. These focus on preventing common attacks that do not rely on other preconditions or vulnerabilities. Most Level 1 controls are either straightforward to implement or essential enough to justify the effort.

 Level 2 requirements

Level 2 addresses more advanced or less common attacks, as well as layered defenses against widespread threats. These requirements may involve more complex logic or target specific attack prerequisites.

 Level 3 requirements

Level 3 includes controls that are generally more difficult to implement or are applicable only in specific situations. These often represent defense-in-depth mechanisms or mitigations against niche, targeted, or highly complex attacks.

#### Role (D/V)

Each AISVS requirement is labeled according to the primary audience:

D – Developer-focused requirements
V – Verifier/Auditor-Focused Requirements
D/V – Relevant to both developers and verifiers

## C1 Training Data Governance and Bias Management

### Control Objective

Training data must be sourced, handled, and maintained in a way that preserves provenance, security, quality, and fairness. Doing so fulfills legal obligations and reduces the risks of bias, poisoning, or privacy breaches that can occur during training and potentially affect the entire AI lifecycle.

---

### C1.1 Training Data Provenance

Maintain a verifiable inventory of all datasets, accept only trusted sources, and log every change for audit purposes.

 #1.1.1    Level: 1    Role: D/V
 Ensure that a current inventory of every training data source—including origin, steward/owner, license, collection method, intended use constraints, and processing history—is maintained.
 #1.1.2    Level: 1    Role: D/V
 Verify that training data processes exclude unnecessary features, attributes, or fields (e.g., unused metadata, sensitive personally identifiable information, leaked test data).
 #1.1.3    Level: 2    Role: D/V
 Ensure that all dataset changes undergo a logged approval workflow.
 #1.1.4    Level: 3    Role: D/V
 Verify that datasets or subsets are watermarked or fingerprinted when feasible.

---

### C1.2 Training Data Security & Integrity

Restrict access to training data, encrypt it both at rest and in transit, and verify its integrity to prevent tampering, theft, or data poisoning.

 #1.2.1    Level: 1    Role: D/V
 Ensure that access controls safeguard training data storage and pipelines.
 #1.2.2    Level: 2    Role: D/V
 Ensure that all access to training data is logged, including the user, time, and action.
 #1.2.3    Level: 2    Role: D/V
 Verify that training datasets are encrypted both in transit and at rest, utilizing industry-standard cryptographic algorithms and key management practices.
 #1.2.4    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are utilized to ensure data integrity during the storage and transfer of training data.
 #1.2.5    Level: 2    Role: D/V
 Verify that automated detection techniques are applied to guard against unauthorized modifications or corruption of training data.
 #1.2.6    Level: 2    Role: D/V
 Ensure that outdated training data is securely deleted or anonymized.
 #1.2.7    Level: 3    Role: D/V
 Ensure that all versions of the training dataset are uniquely identified, stored immutably, and auditable to support rollback and forensic analysis.

---

### C1.3 Training Data Labeling Quality, Integrity, and Security

Protect labels and require a technical review for critical data.

 #1.3.1    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are applied to label artifacts to ensure their integrity and authenticity.
 #1.3.2    Level: 2    Role: D/V
 Ensure that labeling interfaces and platforms enforce strong access controls, maintain tamper-evident audit logs for all labeling activities, and protect against unauthorized modifications.
 #1.3.3    Level: 3    Role: D/V
 Ensure that sensitive information in labels is redacted, anonymized, or encrypted at the data field level both at rest and in transit.

---

### C1.4 Training Data Quality and Security Assurance

Combine automated validation, manual spot checks, and logged remediation to guarantee dataset reliability.

 #1.4.1    Level: 1    Role: D
 Verify that automated tests catch format errors and nulls on every ingestion or significant data transformation.
 #1.4.2    Level: 2    Role: D/V
 Verify that LLM training and fine-tuning pipelines implement poisoning detection and data integrity validation (e.g., statistical methods, outlier detection, embedding analysis) to identify potential poisoning attacks (e.g., label flipping, backdoor trigger insertion, role-switching commands, influential instance attacks) or unintentional data corruption in the training data.
 #1.4.3    Level: 3    Role: D/V
 Ensure that appropriate defenses, such as adversarial training (using generated adversarial examples), data augmentation with perturbed inputs, or robust optimization techniques, are implemented and properly tuned for relevant models based on risk assessment.
 #1.4.4    Level: 2    Role: D/V
 Verify that automatically generated labels (e.g., through LLMs or weak supervision) undergo confidence thresholding and consistency checks to identify hallucinated, misleading, or low-confidence labels.
 #1.4.5    Level: 3    Role: D
 Ensure that automated tests detect label skews during every data ingestion or major data transformation.

---

### C1.5 Data Lineage and Traceability

Track the complete journey of each data point from its source to model input for auditability and incident response.

 #1.5.1    Level: 2    Role: D/V
 Verify that the lineage of each data point, including all transformations, augmentations, and merges, is documented and can be reconstructed.
 #1.5.2    Level: 2    Role: D/V
 Ensure that lineage records are immutable, securely stored, and accessible for audits.
 #1.5.3    Level: 2    Role: D/V
 Ensure that lineage tracking includes synthetic data generated through privacy-preserving or generative methods, and verify that all synthetic data is clearly labeled and distinguishable from real data throughout the entire pipeline.

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

Robust validation of user input is a primary defense against some of the most damaging attacks on AI systems. Prompt injection attacks can override system instructions, leak sensitive data, or steer the model toward prohibited behavior. Unless dedicated filters and instruction hierarchies are implemented, research shows that "multi-shot" jailbreaks exploiting very long context windows will be effective. Additionally, subtle adversarial perturbation attacks—such as homoglyph swaps or leetspeak—can silently alter a model's decisions.

---

### C2.1 Defense Against Prompt Injection

Prompt injection is one of the top risks for AI systems. Defenses against this tactic utilize a combination of static pattern filters, dynamic classifiers, and instruction hierarchy enforcement.

 #2.1.1    Level: 1    Role: D/V
 Ensure that user inputs are screened against a continuously updated library of known prompt injection patterns, including jailbreak keywords, "ignore previous" commands, role-play chains, and indirect HTML/URL attacks.
 #2.1.2    Level: 1    Role: D/V
 Verify that the system enforces an instruction hierarchy where system or developer messages override user instructions, even after expanding the context window.
 #2.1.3    Level: 2    Role: D/V
 Ensure that adversarial evaluation tests (such as Red Team "many-shot" prompts) are conducted before every model or prompt-template release, with established success-rate thresholds and automated blockers to prevent regressions.
 #2.1.4    Level: 2    Role: D
 Ensure that prompts coming from third-party sources (web pages, PDFs, emails) are sanitized within an isolated parsing environment before being combined into the main prompt.
 #2.1.5    Level: 3    Role: D/V
 Ensure that all updates to prompt-filter rules, classifier model versions, and block-list changes are version-controlled and can be audited.

---

### C2.2 Resistance to Adversarial Examples

Natural Language Processing (NLP) models remain vulnerable to subtle character or word-level perturbations that humans often overlook but cause models to misclassify.

 #2.2.1    Level: 1    Role: D
 Verify that basic input normalization steps (Unicode NFC, homoglyph mapping, whitespace trimming) are performed before tokenization.
 #2.2.2    Level: 2    Role: D/V
 Verify that statistical anomaly detection flags inputs with unusually high edit distances from language norms, excessive repeated tokens, or abnormal embedding distances.
 #2.2.3    Level: 2    Role: D
 Verify that the inference pipeline supports optional adversarial training–hardened model variants or defense layers (e.g., randomization, defensive distillation) for high-risk endpoints.
 #2.2.4    Level: 2    Role: V
 Ensure that suspected adversarial inputs are quarantined and logged with full payloads (after redacting any PII).
 #2.2.5    Level: 3    Role: D/V
 Ensure that robustness metrics (success rates of known attack suites) are monitored over time and that regressions trigger a release blocker.

---

### C2.3 Schema, Type, and Length Validation

AI attacks involving malformed or oversized inputs can lead to parsing errors, prompt spillage across fields, and resource exhaustion. Strict schema enforcement is also essential when performing deterministic tool calls.

 #2.3.1    Level: 1    Role: D
 Ensure that every API or function call endpoint defines a clear input schema (JSON Schema, Protobuf, or a multimodal equivalent) and that inputs are validated before assembling the prompt.
 #2.3.2    Level: 1    Role: D/V
 Ensure that inputs exceeding the maximum token or byte limits are rejected with a clear error message and are never silently truncated.
 #2.3.3    Level: 2    Role: D/V
 Ensure that type checks (such as numeric ranges, enum values, and MIME types for images/audio) are enforced on the server side, not just in client-side code.
 #2.3.4    Level: 2    Role: D
 Verify that semantic validators (e.g., JSON Schema) operate in constant time to prevent algorithmic DoS attacks.
 #2.3.5    Level: 3    Role: V
 Ensure that validation failures are logged with redacted payload snippets and clear, unambiguous error codes to support security triage.

---

### C2.4 Content and Policy Screening

Developers should be able to identify syntactically valid prompts that request disallowed content (such as illicit instructions, hate speech, and copyrighted text) and then prevent their propagation.

 #2.4.1    Level: 1    Role: D
 Ensure that a content classifier (zero-shot or fine-tuned) evaluates every input for violence, self-harm, hate, sexual content, and illegal requests, using configurable thresholds.
 #2.4.2    Level: 1    Role: D/V
 Ensure that inputs violating policies receive standardized refusals or safe completions to prevent propagation to downstream LLM calls.
 #2.4.3    Level: 2    Role: D
 Ensure that the screening model or rule set is retrained or updated at least quarterly, incorporating newly observed jailbreak or policy bypass patterns.
 #2.4.4    Level: 2    Role: D
 Verify that screening adheres to user-specific policies (age, regional legal constraints) through attribute-based rules resolved at the time of the request.
 #2.4.5    Level: 3    Role: V
 Verify that screening logs include classifier confidence scores and policy category tags for SOC correlation and future red team replay.

---

### C2.5 Input Rate Limiting and Abuse Prevention

Developers should prevent abuse, resource exhaustion, and automated attacks on AI systems by limiting input rates and detecting unusual usage patterns.

 #2.5.1    Level: 1    Role: D/V
 Verify that rate limits are enforced per user, per IP, and per API key for all input endpoints.
 #2.5.2    Level: 2    Role: D/V
 Ensure that both burst and sustained rate limits are configured properly to prevent DoS and brute force attacks.
 #2.5.3    Level: 2    Role: D/V
 Verify that unusual usage patterns (e.g., rapid-fire requests, input flooding) trigger automated blocks or escalations.
 #2.5.4    Level: 3    Role: V
 Verify that abuse prevention logs are retained and reviewed for emerging attack patterns.

---

### C2.6 Multi-Modal Input Validation

AI systems should have strong validation processes for non-text inputs (such as images, audio, and files) to prevent injection, evasion, or misuse of resources.

 #2.6.1    Level: 1    Role: D
 Ensure that all non-text inputs (images, audio, files) are validated for type, size, and format before processing.
 #2.6.2    Level: 2    Role: D/V
 Ensure that files are scanned for malware and steganographic payloads before ingestion.
 #2.6.3    Level: 2    Role: D/V
 Ensure that image and audio inputs are checked for adversarial perturbations or known attack patterns.
 #2.6.4    Level: 3    Role: V
 Verify that multi-modal input validation failures are logged and trigger alerts for investigation.

---

### C2.7 Input Provenance and Attribution

AI systems should support auditing, abuse tracking, and compliance by monitoring and tagging the sources of all user inputs.

 #2.7.1    Level: 1    Role: D/V
 Verify that all user inputs are tagged with metadata (user ID, session, source, timestamp, IP address) during ingestion.
 #2.7.2    Level: 2    Role: D/V
 Verify that provenance metadata is preserved and auditable for all processed inputs.
 #2.7.3    Level: 2    Role: D/V
 Ensure that anomalous or untrusted input sources are flagged and subjected to enhanced scrutiny or blocking.

---

### C2.8 Real-Time Adaptive Threat Detection

Developers should use advanced threat detection systems for AI that adapt to new attack patterns and provide real-time protection through compiled pattern matching.

 #2.8.1    Level: 1    Role: D/V
 Ensure that threat detection patterns are compiled into optimized regex engines for high-performance, real-time filtering with minimal latency impact.
 #2.8.2    Level: 1    Role: D/V
 Verify that threat detection systems maintain separate pattern libraries for different threat categories, including prompt injection, harmful content, sensitive data, and system commands.
 #2.8.3    Level: 2    Role: D/V
 Verify that adaptive threat detection utilizes machine learning models that adjust threat sensitivity according to attack frequency and success rates.
 #2.8.4    Level: 2    Role: D/V
 Verify that real-time threat intelligence feeds automatically update pattern libraries with new attack signatures and Indicators of Compromise (IOCs).
 #2.8.5    Level: 3    Role: D/V
 Verify that false positive rates in threat detection are continuously monitored and that pattern specificity is automatically adjusted to minimize interference with legitimate use cases.
 #2.8.6    Level: 3    Role: D/V
 Verify that contextual threat analysis takes into account the input source, user behavior patterns, and session history to enhance detection accuracy.
 #2.8.7    Level: 3    Role: D/V
 Ensure that threat detection performance metrics (detection rate, processing latency, resource utilization) are monitored and optimized in real time.

---

### C2.9 Multi-Modal Security Validation Pipeline

Developers should implement security validation for text, image, audio, and other AI input modalities, incorporating specific methods for threat detection and resource isolation.

 #2.9.1    Level: 1    Role: D/V
 Verify that each input modality has dedicated security validators with documented threat patterns (text: prompt injection, images: steganography, audio: spectrogram attacks) and defined detection thresholds.
 #2.9.2    Level: 2    Role: D/V
 Verify that multi-modal inputs are processed in isolated sandboxes with defined resource limits (memory, CPU, processing time) specific to each modality type and documented in security policies.
 #2.9.3    Level: 2    Role: D/V
 Verify that cross-modal attack detection effectively identifies coordinated attacks involving multiple input types (e.g., steganographic payloads embedded in images combined with prompt injections in text) through correlation rules and alert generation.
 #2.9.4    Level: 3    Role: D/V
 Ensure that multi-modal validation failures trigger detailed logging that includes all input modalities, validation results, threat scores, and correlation analysis, using structured log formats for SIEM integration.
 #2.9.5    Level: 3    Role: D/V
 Ensure that modality-specific content classifiers are updated according to documented schedules (at least quarterly) with new threat patterns, adversarial examples, and performance benchmarks maintained above baseline thresholds.

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

## C3 Model Lifecycle Management & Change Control

### Control Objective

AI systems must implement change control processes that prevent unauthorized or unsafe model modifications from reaching production. This control ensures model integrity throughout the entire lifecycle—from development through deployment to decommissioning—enabling rapid incident response and maintaining accountability for all changes.

Core Security Goal: Ensure that only authorized, validated models reach production by using controlled processes that maintain integrity, traceability, and recoverability.

---

### C3.1 Model Authorization and Integrity

Only authorized models with verified integrity are deployed in production environments.

 #3.1.1    Level: 1    Role: D/V
 Ensure that all model artifacts (weights, configurations, tokenizers) are cryptographically signed by authorized entities before deployment.
 #3.1.2    Level: 1    Role: D/V
 Ensure that model integrity is validated at deployment and that signature verification failures prevent the model from loading.
 #3.1.3    Level: 2    Role: D/V
 Verify that model provenance records contain the authorizing entity's identity, training data checksums, validation test results with pass/fail status, and a creation timestamp.
 #3.1.4    Level: 2    Role: D/V
 Ensure that all model artifacts use semantic versioning (MAJOR.MINOR.PATCH) with clearly documented criteria outlining when each version component should be incremented.
 #3.1.5    Level: 2    Role: V
 Ensure that dependency tracking maintains a real-time inventory that allows for the rapid identification of all systems consuming the dependencies.

---

### C3.2 Model Validation & Testing

Models must pass defined security and safety validations before deployment.

 #3.2.1    Level: 1    Role: D/V
 Ensure that models undergo automated security testing that includes input validation, output sanitization, and safety evaluations, adhering to pre-agreed organizational pass/fail thresholds before deployment.
 #3.2.2    Level: 1    Role: D/V
 Ensure that validation failures automatically prevent model deployment unless explicitly overridden by pre-designated authorized personnel with documented business justifications.
 #3.2.3    Level: 2    Role: V
 Verify that test results are cryptographically signed and immutably linked to the specific model version hash being validated.
 #3.2.4    Level: 2    Role: D/V
 Verify that emergency deployments require a documented security risk assessment and approval from a pre-designated security authority within pre-agreed timeframes.

---

### C3.3 Controlled Deployment & Rollback

Model deployments must be controlled, monitored, and reversible.

 #3.3.1    Level: 1    Role: D
 Ensure that production deployments use gradual rollout methods, such as canary deployments or blue-green deployments, with automated rollback triggers based on predetermined error rates, latency limits, or security alert conditions.
 #3.3.2    Level: 1    Role: D/V
 Verify that rollback capabilities restore the entire model state (weights, configurations, dependencies) atomically within predefined organizational time windows.
 #3.3.3    Level: 2    Role: D/V
 Ensure that deployment processes validate cryptographic signatures and compute integrity checksums before model activation, and halt deployment if any mismatch is detected.
 #3.3.4    Level: 2    Role: D/V
 Verify that emergency model shutdown capabilities can disable model endpoints within predefined response times using automated circuit breakers or manual kill switches.
 #3.3.5    Level: 2    Role: V
 Verify that rollback artifacts (previous model versions, configurations, dependencies) are retained according to organizational policies using immutable storage for incident response.

---

### C3.4 Change Accountability and Audit

All changes throughout the model lifecycle must be traceable and auditable.

 #3.4.1    Level: 1    Role: V
 Verify that all model changes (deployment, configuration, retirement) generate immutable audit records that include a timestamp, an authenticated actor identity, a change type, and before/after states.
 #3.4.2    Level: 2    Role: D/V
 Ensure that access to the audit log requires proper authorization and that all access attempts are recorded with the user’s identity and a timestamp.
 #3.4.3    Level: 2    Role: D/V
 Ensure that prompt templates and system messages are version-controlled in git repositories, with mandatory code reviews and approvals from designated reviewers before deployment.
 #3.4.4    Level: 2    Role: V
 Verify that audit records contain sufficient detail (model hashes, configuration snapshots, dependency versions) to allow complete reconstruction of the model state for any timestamp within the retention period.

---

### C3.5 Secure Development Practices

Model development and training processes must follow secure practices to prevent any compromise.

 #3.5.1    Level: 1    Role: D
 Ensure that model development, testing, and production environments are physically or logically separated. They should have no shared infrastructure, distinct access controls, and isolated data stores.
 #3.5.2    Level: 1    Role: D
 Ensure that model training and fine-tuning take place in isolated environments with restricted network access.
 #3.5.3    Level: 1    Role: D/V
 Ensure that training data sources are validated through integrity checks and authenticated by trusted sources with a documented chain of custody before being used in model development.
 #3.5.4    Level: 2    Role: D
 Ensure that model development artifacts (hyperparameters, training scripts, configuration files) are stored in version control and require peer review approval before being used for training.

---

### C3.6 Model Retirement and Decommissioning

Models must be securely retired when they are no longer needed or when security issues are identified.

 #3.6.1    Level: 1    Role: D
 Verify that model retirement processes automatically scan dependency graphs, identify all dependent systems, and provide pre-agreed advance notice periods before decommissioning.
 #3.6.2    Level: 1    Role: D/V
 Ensure that retired model artifacts are securely erased through cryptographic erasure or multi-pass overwriting in accordance with documented data retention policies, accompanied by verified destruction certificates.
 #3.6.3    Level: 2    Role: V
 Ensure that model retirement events are logged with a timestamp and the identity of the actor, and that model signatures are revoked to prevent reuse.
 #3.6.4    Level: 2    Role: D/V
 Verify that emergency model retirement can disable model access within predetermined emergency response timeframes using automated kill switches if critical security vulnerabilities are identified.

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

AI infrastructure must be fortified against privilege escalation, supply chain tampering, and lateral movement through secure configuration, runtime isolation, trusted deployment pipelines, and comprehensive monitoring. Only authorized, validated infrastructure components and configurations are deployed to production through controlled processes that ensure security, integrity, and auditability.

Core Security Goal: Only cryptographically signed, vulnerability-scanned infrastructure components should reach production through automated validation pipelines that enforce security policies and maintain immutable audit trails.

---

### C4.1 Runtime Environment Isolation

Prevent container escapes and privilege escalation using kernel-level isolation primitives and mandatory access controls.

 #4.1.1    Level: 1    Role: D/V
 Verify that all AI containers drop ALL Linux capabilities except CAP_SETUID, CAP_SETGID, and any explicitly required capabilities documented in the security baselines.
 #4.1.2    Level: 1    Role: D/V
 Ensure that seccomp profiles block all system calls except those on pre-approved allowlists, with any violations terminating the container and triggering security alerts.
 #4.1.3    Level: 2    Role: D/V
 Verify that AI workloads operate with read-only root filesystems, use tmpfs for temporary data, and utilize named volumes for persistent data that enforce noexec mount options.
 #4.1.4    Level: 2    Role: D/V
 Verify that eBPF-based runtime monitoring (Falco, Tetragon, or equivalent) detects privilege escalation attempts and automatically terminates offending processes within the organization's response time requirements.
 #4.1.5    Level: 3    Role: D/V
 Ensure that high-risk AI workloads run in hardware-isolated environments (Intel TXT, AMD SVM, or dedicated bare-metal nodes) with attestation verification.

---

### C4.2 Secure Build and Deployment Pipelines

Ensure cryptographic integrity and supply chain security by using reproducible builds and signed artifacts.

 #4.2.1    Level: 1    Role: D/V
 Ensure that infrastructure-as-code is scanned with tools (tfsec, Checkov, or Terrascan) on every commit, blocking merges when CRITICAL or HIGH severity issues are found.
 #4.2.2    Level: 1    Role: D/V
 Ensure container builds are reproducible by producing identical SHA256 hashes across builds and generate SLSA Level 3 provenance attestations signed with Sigstore.
 #4.2.3    Level: 2    Role: D/V
 Ensure that container images include embedded CycloneDX or SPDX SBOMs and are signed with Cosign before pushing to the registry, rejecting unsigned images during deployment.
 #4.2.4    Level: 2    Role: D/V
 Verify that CI/CD pipelines use OIDC tokens from HashiCorp Vault, AWS IAM Roles, or Azure Managed Identity with lifetimes that do not exceed organizational security policy limits.
 #4.2.5    Level: 2    Role: D/V
 Ensure that Cosign signatures and SLSA provenance are validated during the deployment process before container execution, and that any verification errors cause the deployment to fail.
 #4.2.6    Level: 2    Role: D/V
 Ensure that build environments operate in ephemeral containers or virtual machines without persistent storage and maintain network isolation from production VPCs.

---

### C4.3 Network Security & Access Control

Implement zero-trust networking by using default-deny policies and encrypted communications.

 #4.3.1    Level: 1    Role: D/V
 Verify that Kubernetes NetworkPolicies or any equivalent enforce a default-deny policy for ingress and egress, with explicit allow rules for required ports (443, 8080, etc.).
 #4.3.2    Level: 1    Role: D/V
 Verify that SSH (port 22), RDP (port 3389), and cloud metadata endpoints (169.254.169.254) are blocked or require certificate-based authentication.
 #4.3.3    Level: 2    Role: D/V
 Verify that egress traffic is filtered through HTTP/HTTPS proxies (such as Squid, Istio, or cloud NAT gateways) with domain allowlists and that blocked requests are logged.
 #4.3.4    Level: 2    Role: D/V
 Ensure that inter-service communication uses mutual TLS with certificates rotated according to organizational policy and that certificate validation is enforced (no skip-verify flags).
 #4.3.5    Level: 2    Role: D/V
 Ensure that AI infrastructure operates within dedicated VPCs/VNets without direct internet access and communicates exclusively through NAT gateways or bastion hosts.

---

### C4.4 Secrets and Cryptographic Key Management

Protect credentials using hardware-backed storage and automated rotation with zero-trust access.

 #4.4.1    Level: 1    Role: D/V
 Verify that secrets are stored in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault, or Google Secret Manager, with encryption at rest using AES-256.
 #4.4.2    Level: 1    Role: D/V
 Verify that cryptographic keys are generated in FIPS 140-2 Level 2 HSMs (AWS CloudHSM, Azure Dedicated HSM) and that key rotation is performed according to the organizational cryptographic policy.
 #4.4.3    Level: 2    Role: D/V
 Verify that secret rotation is automated with zero-downtime deployment and immediate rotation triggered by personnel changes or security incidents.
 #4.4.4    Level: 2    Role: D/V
 Ensure that container images are scanned using tools such as GitLeaks, TruffleHog, or detect-secrets to block builds that contain API keys, passwords, or certificates.
 #4.4.5    Level: 2    Role: D/V
 Verify that access to production secrets requires multi-factor authentication (MFA) using hardware tokens (YubiKey, FIDO2) and that all access is recorded in immutable audit logs containing user identities and timestamps.
 #4.4.6    Level: 2    Role: D/V
 Verify that secrets are injected through Kubernetes secrets, mounted volumes, or init containers, and ensure that secrets are never embedded in environment variables or images.

---

### C4.5 AI Workload Sandboxing & Validation

Isolate untrusted AI models in secure sandboxes with thorough behavioral analysis.

 #4.5.1    Level: 1    Role: D/V
 Verify that external AI models run in gVisor, microVMs (such as Firecracker, CrossVM), or Docker containers using the --security-opt=no-new-privileges and --read-only flags.
 #4.5.2    Level: 1    Role: D/V
 Verify that sandbox environments have no network connectivity (--network=none) or only localhost access, with all external requests blocked by iptables rules.
 #4.5.3    Level: 2    Role: D/V
 Ensure that AI model validation includes automated red-team testing with organization-defined test coverage and behavioral analysis for backdoor detection.
 #4.5.4    Level: 2    Role: D/V
 Ensure that before an AI model is deployed to production, its sandbox results are cryptographically signed by authorized security personnel and stored in immutable audit logs.
 #4.5.5    Level: 2    Role: D/V
 Ensure that sandbox environments are destroyed and recreated from golden images between evaluations, with complete filesystem and memory cleanup.

---

### C4.6 Infrastructure Security Monitoring

Continuously scan and monitor infrastructure with automated remediation and real-time alerts.

 #4.6.1    Level: 1    Role: D/V
 Verify that container images are scanned according to organizational schedules, with CRITICAL vulnerabilities blocking deployment based on organizational risk thresholds.
 #4.6.2    Level: 1    Role: D/V
 Ensure that the infrastructure complies with CIS Benchmarks or NIST 800-53 controls according to organizationally defined compliance thresholds, and implement automated remediation for any failed checks.
 #4.6.3    Level: 2    Role: D/V
 Verify that HIGH severity vulnerabilities are patched according to organizational risk management timelines, with emergency procedures in place for actively exploited CVEs.
 #4.6.4    Level: 2    Role: V
 Verify that security alerts integrate with SIEM platforms (Splunk, Elastic, or Sentinel) using CEF or STIX/TAXII formats with automated enrichment.
 #4.6.5    Level: 3    Role: V
 Verify that infrastructure metrics are exported to monitoring systems (Prometheus, DataDog) with SLA dashboards and executive reports.
 #4.6.6    Level: 2    Role: D/V
 Verify that configuration drift is detected using tools (Chef InSpec, AWS Config) in accordance with organizational monitoring requirements, with automatic rollback for unauthorized changes.

---

### C4.7 AI Infrastructure Resource Management

Prevent resource exhaustion attacks and ensure fair resource allocation through quotas and monitoring.

 #4.7.1    Level: 1    Role: D/V
 Verify that GPU/TPU utilization is monitored, with alerts triggered at organizationally defined thresholds, and that automatic scaling or load balancing is activated based on capacity management policies.
 #4.7.2    Level: 1    Role: D/V
 Ensure that AI workload metrics (inference latency, throughput, error rates) are collected in accordance with organizational monitoring requirements and correlated with infrastructure utilization.
 #4.7.3    Level: 2    Role: D/V
 Verify that Kubernetes ResourceQuotas or equivalent mechanisms limit individual workloads according to organizational resource allocation policies, with hard limits enforced.
 #4.7.4    Level: 2    Role: V
 Verify that cost monitoring tracks spending per workload or tenant, includes alerts based on organizational budget thresholds, and has automated controls to prevent budget overruns.
 #4.7.5    Level: 3    Role: V
 Verify that capacity planning utilizes historical data with forecasting periods defined by the organization and includes automated resource provisioning based on demand patterns.
 #4.7.6    Level: 2    Role: D/V
 Verify that resource exhaustion triggers circuit breakers according to organizational response requirements, including rate limiting based on capacity policies and workload isolation.

---

### C4.8 Environment Separation and Promotion Controls

Enforce strict environment boundaries using automated promotion gates and security validation.

 #4.8.1    Level: 1    Role: D/V
 Verify that the development, testing, and production environments operate in separate VPCs/VNets without shared IAM roles, security groups, or network connections.
 #4.8.2    Level: 1    Role: D/V
 Verify that environment promotion requires approval from organizationally defined authorized personnel, using cryptographic signatures and immutable audit trails.
 #4.8.3    Level: 2    Role: D/V
 Ensure that production environments block SSH access, disable debug endpoints, and require change requests with organizational advance notice, except in emergencies.
 #4.8.4    Level: 2    Role: D/V
 Ensure that infrastructure-as-code changes require peer review, automated testing, and security scanning before merging into the main branch.
 #4.8.5    Level: 2    Role: D/V
 Verify that non-production data is anonymized in accordance with organizational privacy requirements, using synthetic data generation or complete data masking with verified PII removal.
 #4.8.6    Level: 2    Role: D/V
 Ensure that promotion gates incorporate automated security tests (SAST, DAST, container scanning) and require zero CRITICAL findings for approval.

---

### C4.9 Infrastructure Backup and Recovery

Ensure infrastructure resilience through automated backups, tested recovery procedures, and disaster recovery capabilities.

 #4.9.1    Level: 1    Role: D/V
 Verify that infrastructure configurations are backed up according to the organizational backup schedules to geographically separate regions, implementing the 3-2-1 backup strategy.
 #4.9.2    Level: 2    Role: D/V
 Ensure that backup systems operate within isolated networks using separate credentials and air-gapped storage to protect against ransomware.
 #4.9.3    Level: 2    Role: V
 Verify that recovery procedures are tested and validated through automated testing according to organizational schedules, ensuring RTO and RPO targets meet organizational requirements.
 #4.9.4    Level: 3    Role: V
 Ensure that disaster recovery plans include AI-specific runbooks covering model weight restoration, GPU cluster reconstruction, and service dependency mapping.

---

### C4.10 Infrastructure Compliance & Governance

Ensure regulatory compliance through continuous assessment, documentation, and automated controls.

 #4.10.1    Level: 2    Role: D/V
 Ensure that infrastructure compliance is evaluated according to organizational schedules based on SOC 2, ISO 27001, or FedRAMP controls, with automated evidence collection.
 #4.10.2    Level: 2    Role: V
 Verify that the infrastructure documentation includes network diagrams, data flow maps, and threat models updated in accordance with organizational change management requirements.
 #4.10.3    Level: 3    Role: D/V
 Ensure that infrastructure changes undergo automated compliance impact assessments with regulatory approval workflows for high-risk modifications.

---

### C4.11 AI Hardware Security

Secure AI-specific hardware components, including GPUs, TPUs, and specialized AI accelerators.

 #4.11.1    Level: 2    Role: D/V
 Ensure that AI accelerator firmware (GPU BIOS, TPU firmware) is verified using cryptographic signatures and updated in accordance with organizational patch management schedules.
 #4.11.2    Level: 2    Role: D/V
 Ensure that before workload execution, the AI accelerator's integrity is validated through hardware attestation using TPM 2.0, Intel TXT, or AMD SVM.
 #4.11.3    Level: 2    Role: D/V
 Verify that GPU memory is isolated between workloads using SR-IOV, MIG (Multi-Instance GPU), or equivalent hardware partitioning, with memory sanitization between jobs.
 #4.11.4    Level: 3    Role: V
 Ensure that the AI hardware supply chain includes provenance verification through manufacturer certificates and validation of tamper-evident packaging.
 #4.11.5    Level: 3    Role: D/V
 Ensure that hardware security modules (HSMs) protect AI model weights and cryptographic keys with FIPS 140-2 Level 3 or Common Criteria EAL4+ certification.

---

### C4.12 Edge and Distributed AI Infrastructure

Secure distributed AI deployments, including edge computing, federated learning, and multi-site architectures.

 #4.12.1    Level: 2    Role: D/V
 Ensure that edge AI devices authenticate to the central infrastructure using mutual TLS with device certificates rotated in accordance with the organizational certificate management policy.
 #4.12.2    Level: 2    Role: D/V
 Ensure that edge devices implement secure boot with verified signatures and rollback protection to prevent firmware downgrade attacks.
 #4.12.3    Level: 3    Role: D/V
 Verify that distributed AI coordination employs Byzantine fault-tolerant consensus algorithms with participant validation and malicious node detection.
 #4.12.4    Level: 3    Role: D/V
 Verify that edge-to-cloud communication includes bandwidth throttling, data compression, and offline operation capabilities with secure local storage.

---

### C4.13 Multi-Cloud and Hybrid Infrastructure Security

Secure AI workloads across multiple cloud providers and hybrid cloud and on-premises deployments.

 #4.13.1    Level: 2    Role: D/V
 Verify that multi-cloud AI deployments utilize cloud-agnostic identity federation (OIDC, SAML) with centralized policy management across providers.
 #4.13.2    Level: 2    Role: D/V
 Ensure that cross-cloud data transfer employs end-to-end encryption using customer-managed keys and that data residency controls are enforced according to jurisdiction.
 #4.13.3    Level: 2    Role: D/V
 Ensure that hybrid cloud AI workloads apply consistent security policies across both on-premises and cloud environments with unified monitoring and alerting.
 #4.13.4    Level: 3    Role: V
 Verify that cloud vendor lock-in prevention includes portable infrastructure-as-code, standardized APIs, and data export capabilities with format conversion tools.
 #4.13.5    Level: 3    Role: V
 Verify that multi-cloud cost optimization includes security controls that prevent resource sprawl as well as unauthorized cross-cloud data transfer charges.

---

### C4.14 Infrastructure Automation & GitOps Security

Secure infrastructure automation pipelines and GitOps workflows for managing AI infrastructure.

 #4.14.1    Level: 2    Role: D/V
 Verify that GitOps repositories require signed commits using GPG keys and enforce branch protection rules that prevent direct pushes to the main branches.
 #4.14.2    Level: 2    Role: D/V
 Ensure that infrastructure automation includes drift detection with automatic remediation and rollback capabilities triggered according to organizational response requirements for unauthorized changes.
 #4.14.3    Level: 2    Role: D/V
 Ensure that automated infrastructure provisioning includes security policy validation that blocks deployment for non-compliant configurations.
 #4.14.4    Level: 2    Role: D/V
 Verify that infrastructure automation secrets are managed through external secret operators (External Secrets Operator, Bank-Vaults) with automatic rotation.
 #4.14.5    Level: 3    Role: V
 Verify that the self-healing infrastructure includes security event correlation, automated incident response, and stakeholder notification workflows.

---

### C4.15 Quantum-Resistant Infrastructure Security

Prepare AI infrastructure for quantum computing threats by implementing post-quantum cryptography and quantum-safe protocols.

 #4.15.1    Level: 3    Role: D/V
 Verify that the AI infrastructure implements NIST-approved post-quantum cryptographic algorithms (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) for key exchange and digital signatures.
 #4.15.2    Level: 3    Role: D/V
 Ensure that quantum key distribution (QKD) systems are implemented for high-security AI communications using quantum-safe key management protocols.
 #4.15.3    Level: 3    Role: D/V
 Verify that cryptographic agility frameworks enable rapid migration to new post-quantum algorithms through automated certificate and key rotation.
 #4.15.4    Level: 3    Role: V
 Verify that quantum threat modeling evaluates AI infrastructure vulnerabilities to quantum attacks, including documented migration timelines and risk assessments.
 #4.15.5    Level: 3    Role: D/V
 Verify that hybrid classical-quantum cryptographic systems offer defense-in-depth throughout the quantum transition period by incorporating performance monitoring.

---

### C4.16 Confidential Computing & Secure Enclaves

Protect AI workloads and model weights using hardware-based trusted execution environments and confidential computing technologies.

 #4.16.1    Level: 3    Role: D/V
 Verify that sensitive AI models run within Intel SGX enclaves, AMD SEV-SNP, or ARM TrustZone environments with encrypted memory and attestation verification.
 #4.16.2    Level: 3    Role: D/V
 Verify that confidential containers (Kata Containers, gVisor with confidential computing) isolate AI workloads using hardware-enforced memory encryption.
 #4.16.3    Level: 3    Role: D/V
 Verify that remote attestation confirms enclave integrity before loading AI models by providing cryptographic proof of the execution environment’s authenticity.
 #4.16.4    Level: 3    Role: D/V
 Ensure that confidential AI inference services prevent model extraction by using encrypted computation with sealed model weights and protected execution.
 #4.16.5    Level: 3    Role: D/V
 Verify that the trusted execution environment orchestration manages the secure enclave lifecycle using remote attestation and encrypted communication channels.
 #4.16.6    Level: 3    Role: D/V
 Verify that secure multi-party computation (SMPC) enables collaborative AI training without revealing individual datasets or model parameters.

---

### C4.17 Zero-Knowledge Infrastructure

Develop zero-knowledge proof systems for privacy-preserving AI verification and authentication that do not disclose sensitive information.

 #4.17.1    Level: 3    Role: D/V
 Verify that zero-knowledge proofs (ZK-SNARKs, ZK-STARKs) confirm AI model integrity and training provenance without revealing model weights or training data.
 #4.17.2    Level: 3    Role: D/V
 Confirm that zero-knowledge (ZK) based authentication systems allow privacy-preserving user verification for AI services without disclosing identity-related information.
 #4.17.3    Level: 3    Role: D/V
 Confirm that private set intersection (PSI) protocols allow secure data matching in federated AI without revealing individual datasets.
 #4.17.4    Level: 3    Role: D/V
 Verify that zero-knowledge machine learning (ZKML) systems enable verifiable AI inferences through cryptographic proofs of correct computation.
 #4.17.5    Level: 3    Role: D/V
 Verify that ZK-rollups offer scalable, privacy-preserving AI transaction processing through batch verification and reduced computational overhead.

---

### C4.18 Side-Channel Attack Prevention

Protect AI infrastructure from timing, power, electromagnetic, and cache-based side-channel attacks that could expose sensitive information.

 #4.18.1    Level: 3    Role: D/V
 Verify that AI inference timing is normalized using constant-time algorithms and padding to prevent timing-based model extraction attacks.
 #4.18.2    Level: 3    Role: D/V
 Verify that power analysis protection includes noise injection, power line filtering, and randomized execution patterns for AI hardware.
 #4.18.3    Level: 3    Role: D/V
 Verify that cache-based side-channel mitigation employs cache partitioning, randomization, and flush instructions to prevent information leakage.
 #4.18.4    Level: 3    Role: D/V
 Verify that electromagnetic emission protection includes shielding, signal filtering, and randomized processing to prevent TEMPEST-style attacks.
 #4.18.5    Level: 3    Role: D/V
 Verify that microarchitectural side-channel defenses include controls for speculative execution and obfuscation of memory access patterns.

---

### C4.19 Neuromorphic and Specialized AI Hardware Security

Secure emerging AI hardware architectures, including neuromorphic chips, FPGAs, custom ASICs, and optical computing systems.

 #4.19.1    Level: 3    Role: D/V
 Verify that neuromorphic chip security includes spike pattern encryption, synaptic weight protection, and hardware-based learning rule validation.
 #4.19.2    Level: 3    Role: D/V
 Verify that FPGA-based AI accelerators implement bitstream encryption, anti-tamper mechanisms, and secure configuration loading with authenticated updates.
 #4.19.3    Level: 3    Role: D/V
 Verify that custom ASIC security features include on-chip security processors, a hardware root of trust, and secure key storage with tamper detection.
 #4.19.4    Level: 3    Role: D/V
 Verify that optical computing systems implement quantum-safe optical encryption, secure photonic switching, and protected optical signal processing.
 #4.19.5    Level: 3    Role: D/V
 Verify that hybrid analog-digital AI chips include secure analog computation, protected weight storage, and authenticated analog-to-digital conversion.

---

### C4.20 Privacy-Preserving Computing Infrastructure

Implement infrastructure controls for privacy-preserving computation to safeguard sensitive data during AI processing and analysis.

 #4.20.1    Level: 3    Role: D/V
 Verify that the homomorphic encryption infrastructure enables encrypted computation on sensitive AI workloads, ensuring cryptographic integrity verification and performance monitoring.
 #4.20.2    Level: 3    Role: D/V
 Verify that private information retrieval systems allow database queries without exposing query patterns by using cryptographic protection for access patterns.
 #4.20.3    Level: 3    Role: D/V
 Verify that secure multi-party computation protocols enable privacy-preserving AI inference without revealing individual inputs or intermediate computations.
 #4.20.4    Level: 3    Role: D/V
 Ensure that privacy-preserving key management includes distributed key generation, threshold cryptography, and secure key rotation with hardware-backed protection.
 #4.20.5    Level: 3    Role: D/V
 Ensure that privacy-preserving compute performance is optimized through batching, caching, and hardware acceleration while maintaining cryptographic security guarantees.

---

### C4.15 Agent Framework Cloud Integration Security & Hybrid Deployment

Security controls for cloud-integrated agent frameworks with hybrid on-premises/cloud architectures.

 #4.15.1    Level: 1    Role: D/V
 Verify that cloud storage integration employs end-to-end encryption with agent-controlled key management.
 #4.15.2    Level: 2    Role: D/V
 Ensure that the security boundaries of the hybrid deployment are clearly defined and that communication channels are encrypted.
 #4.15.3    Level: 2    Role: D/V
 Ensure that access to cloud resources incorporates zero-trust verification with continuous authentication.
 #4.15.4    Level: 3    Role: D/V
 Verify that data residency requirements are enforced through cryptographic attestation of storage locations.
 #4.15.5    Level: 3    Role: D/V
 Verify that cloud provider security assessments include threat modeling and risk evaluation specific to agents.

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

## C5 Access Control and Identity for AI Components and Users

### Control Objective

Effective access control for AI systems requires robust identity management, context-aware authorization, and runtime enforcement following zero-trust principles. These controls ensure that humans, services, and autonomous agents interact only with models, data, and computational resources within explicitly granted scopes, with continuous verification and audit capabilities.

---

### C5.1 Identity Management & Authentication

Establish cryptographically backed identities for all entities with multi-factor authentication for privileged operations.

 #5.1.1    Level: 1    Role: D/V
 Ensure that all human users and service principals authenticate through a centralized enterprise identity provider (IdP) using OIDC/SAML protocols with unique identity-to-token mappings (no shared accounts or credentials).
 #5.1.2    Level: 1    Role: D/V
 Verify that high-risk operations (model deployment, weight export, training data access, production configuration changes) require multi-factor authentication or step-up authentication with session revalidation.
 #5.1.3    Level: 2    Role: D
 Ensure that new principals undergo identity proofing aligned with NIST 800-63-3 IAL-2 or equivalent standards before gaining access to the production system.
 #5.1.4    Level: 2    Role: V
 Verify that access reviews are conducted quarterly with automated detection of inactive accounts, enforcement of credential rotation, and de-provisioning workflows.
 #5.1.5    Level: 3    Role: D/V
 Ensure that federated AI agents authenticate using signed JWT assertions with a maximum lifespan of 24 hours, which include cryptographic proof of origin.

---

### C5.2 Resource Authorization & Least Privilege

Implement fine-grained access controls for all AI resources using explicit permission models and maintain audit trails.

 #5.2.1    Level: 1    Role: D/V
 Verify that every AI resource (datasets, models, endpoints, vector collections, embedding indices, compute instances) enforces role-based access controls with explicit allow lists and default-deny policies.
 #5.2.2    Level: 1    Role: D/V
 Ensure that least-privilege principles are enforced by default for service accounts, starting with read-only permissions and requiring documented business justification for write access.
 #5.2.3    Level: 1    Role: V
 Verify that all access control modifications are linked to approved change requests and are immutably logged with timestamps, actor identities, resource identifiers, and permission changes.
 #5.2.4    Level: 2    Role: D
 Verify that data classification labels (PII, PHI, export-controlled, proprietary) automatically propagate to derived resources (embeddings, prompt caches, model outputs) with consistent policy enforcement.
 #5.2.5    Level: 2    Role: D/V
 Verify that unauthorized access attempts and privilege escalation events trigger real-time alerts with contextual metadata to SIEM systems within 5 minutes.

---

### C5.3 Dynamic Policy Evaluation

Deploy attribute-based access control (ABAC) engines to enable context-aware authorization decisions with auditing capabilities.

 #5.3.1    Level: 1    Role: D/V
 Verify that authorization decisions are externalized to a dedicated policy engine (such as OPA, Cedar, or an equivalent) accessible through authenticated APIs with cryptographic integrity protection.
 #5.3.2    Level: 1    Role: D/V
 Ensure that policies evaluate dynamic attributes at runtime, including user clearance level, resource sensitivity classification, request context, tenant isolation, and temporal constraints.
 #5.3.3    Level: 2    Role: D
 Ensure that policy definitions are version-controlled, peer-reviewed, and validated through automated testing within CI/CD pipelines before deploying to production.
 #5.3.4    Level: 2    Role: V
 Verify that policy evaluation results include structured decision rationales and are transmitted to SIEM systems for correlation analysis and compliance reporting.
 #5.3.5    Level: 3    Role: D/V
 Verify that policy cache time-to-live (TTL) values do not exceed 5 minutes for high-sensitivity resources and 1 hour for standard resources with cache invalidation capabilities.

---

### C5.4 Query-Time Security Enforcement

Implement database-layer security controls using mandatory filtering and row-level security policies.

 #5.4.1    Level: 1    Role: D/V
 Verify that all vector database and SQL queries include mandatory security filters (tenant ID, sensitivity labels, user scope) enforced at the database engine level, not in the application code.
 #5.4.2    Level: 1    Role: D/V
 Verify that row-level security (RLS) policies and field-level masking are enabled with policy inheritance for all vector databases, search indices, and training datasets.
 #5.4.3    Level: 2    Role: D
 Ensure that failed authorization checks prevent "confused deputy attacks" by immediately aborting queries and returning explicit authorization error codes instead of returning empty result sets.
 #5.4.4    Level: 2    Role: V
 Ensure that policy evaluation latency is continuously monitored with automated alerts for timeout conditions that could allow authorization bypass.
 #5.4.5    Level: 3    Role: D/V
 Ensure that query retry mechanisms re-evaluate authorization policies to accommodate dynamic permission changes during active user sessions.

---

### C5.5 Output Filtering & Data Loss Prevention

Implement post-processing controls to prevent unauthorized exposure of data in AI-generated content.

 #5.5.1    Level: 1    Role: D/V
 Ensure that post-inference filtering mechanisms scan for and redact unauthorized PII, classified information, and proprietary data before delivering content to requestors.
 #5.5.2    Level: 1    Role: D/V
 Verify that citations, references, and source attributions in model outputs are validated against user entitlements and removed if unauthorized access is detected.
 #5.5.3    Level: 2    Role: D
 Ensure that output format restrictions (such as sanitized PDFs, metadata-stripped images, and approved file types) are enforced according to user permission levels and data classification.
 #5.5.4    Level: 2    Role: V
 Ensure that redaction algorithms are deterministic, version-controlled, and maintain audit logs to support compliance investigations and forensic analysis.
 #5.5.5    Level: 3    Role: V
 Verify that high-risk redaction events generate adaptive logs containing cryptographic hashes of the original content for forensic retrieval without exposing the data.

---

### C5.6 Multi-Tenant Isolation

Ensure cryptographic and logical isolation between tenants in shared AI infrastructure.

 #5.6.1    Level: 1    Role: D/V
 Verify that memory spaces, embedding stores, cache entries, and temporary files are segregated by namespace for each tenant, with secure purging upon tenant deletion or session termination.
 #5.6.2    Level: 1    Role: D/V
 Verify that every API request includes an authenticated tenant identifier that is cryptographically validated against the session context and user entitlements.
 #5.6.3    Level: 2    Role: D
 Ensure that network policies enforce default-deny rules for cross-tenant communication within service meshes and container orchestration platforms.
 #5.6.4    Level: 3    Role: D
 Verify that encryption keys are unique for each tenant, support customer-managed keys (CMK), and ensure cryptographic isolation between tenant data stores.

---

### C5.7 Authorization for Autonomous Agents

Manage permissions for AI agents and autonomous systems using scoped capability tokens and continuous authorization.

 #5.7.1    Level: 1    Role: D/V
 Ensure that autonomous agents receive scoped capability tokens that clearly specify allowed actions, accessible resources, time limits, and operational constraints.
 #5.7.2    Level: 1    Role: D/V
 Verify that high-risk capabilities (file system access, code execution, external API calls, financial transactions) are disabled by default and require explicit authorization for activation with business justifications.
 #5.7.3    Level: 2    Role: D
 Verify that capability tokens are linked to user sessions, include cryptographic integrity protection, and ensure they cannot be stored or reused in offline scenarios.
 #5.7.4    Level: 2    Role: V
 Verify that agent-initiated actions undergo secondary authorization via the ABAC policy engine, including full context evaluation and audit logging.
 #5.7.5    Level: 3    Role: V
 Verify that agent error conditions and exception handling include capability scope information to support incident analysis and forensic investigation.

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

AI supply-chain attacks exploit third-party models, frameworks, or datasets to embed backdoors, biases, or exploitable code. These controls provide end-to-end provenance, vulnerability management, and monitoring to protect the entire model lifecycle.

---

### C6.1 Pretrained Model Vetting and Provenance

Evaluate and verify third-party model origins, licenses, and hidden behaviors before any fine-tuning or deployment.

 #6.1.1    Level: 1    Role: D/V
 Verify that every third-party model artifact includes a signed provenance record identifying the source repository and commit hash.
 #6.1.2    Level: 1    Role: D/V
 Ensure that models are scanned for malicious layers or Trojan triggers using automated tools before importing.
 #6.1.3    Level: 2    Role: D
 Verify that transfer-learning fine-tuning passes adversarial evaluation to detect hidden behaviors.
 #6.1.4    Level: 2    Role: V
 Verify that model licenses, export-control tags, and data-origin statements are recorded in an ML-BOM entry.
 #6.1.5    Level: 3    Role: D/V
 Ensure that high-risk models (publicly uploaded weights, unverified creators) remain quarantined until they undergo human review and receive sign-off.

---

### C6.2 Framework and Library Scanning

Continuously scan machine learning frameworks and libraries for CVEs and malicious code to maintain the security of the runtime stack.

 #6.2.1    Level: 1    Role: D/V
 Verify that CI pipelines execute dependency scanners on AI frameworks and critical libraries.
 #6.2.2    Level: 1    Role: D/V
 Ensure that critical vulnerabilities (CVSS score ≥ 7.0) prevent promotion to production images.
 #6.2.3    Level: 2    Role: D
 Ensure that static code analysis is performed on forked or vendored machine learning libraries.
 #6.2.4    Level: 2    Role: V
 Ensure that framework upgrade proposals include a security impact assessment that references public CVE feeds.
 #6.2.5    Level: 3    Role: V
 Verify that runtime sensors generate alerts for unexpected dynamic library loads that deviate from the signed SBOM.

---

### C6.3 Dependency Pinning & Verification

Pin every dependency to immutable digests and reproduce builds to guarantee identical, tamper-proof artifacts.

 #6.3.1    Level: 1    Role: D/V
 Verify that all package managers enforce version pinning through lockfiles.
 #6.3.2    Level: 1    Role: D/V
 Ensure that immutable digests are used instead of mutable tags in container references.
 #6.3.3    Level: 2    Role: D
 Verify that reproducible-build checks compare hashes across CI runs to ensure identical outputs.
 #6.3.4    Level: 2    Role: V
 Confirm that build attestations are retained for 18 months to ensure audit traceability.
 #6.3.5    Level: 3    Role: D
 Verify that expired dependencies trigger automated pull requests to update or fork pinned versions.

---

### C6.4 Trusted Source Enforcement

Allow artifact downloads only from cryptographically verified, organization-approved sources and block everything else.

 #6.4.1    Level: 1    Role: D/V
 Verify that model weights, datasets, and containers are downloaded only from approved domains or internal registries.
 #6.4.2    Level: 1    Role: D/V
 Verify that Sigstore/Cosign signatures authenticate the publisher's identity before caching artifacts locally.
 #6.4.3    Level: 2    Role: D
 Verify that egress proxies block unauthenticated artifact downloads to enforce the trusted-source policy.
 #6.4.4    Level: 2    Role: V
 Verify that repository allow-lists are reviewed quarterly, with evidence of a business justification for each entry.
 #6.4.5    Level: 3    Role: V
 Verify that policy violations trigger the quarantining of artifacts and the rollback of dependent pipeline runs.

---

### C6.5 Third-Party Dataset Risk Assessment

Evaluate external datasets for poisoning, bias, and legal compliance, and continuously monitor them throughout their lifecycle.

 #6.5.1    Level: 1    Role: D/V
 Ensure that external datasets are evaluated for poisoning risks, such as through data fingerprinting and outlier detection.
 #6.5.2    Level: 1    Role: D
 Ensure that bias metrics (demographic parity, equal opportunity) are calculated before approving the dataset.
 #6.5.3    Level: 2    Role: V
 Verify that provenance and license terms for datasets are recorded in ML-BOM entries.
 #6.5.4    Level: 2    Role: V
 Verify that regular monitoring detects drift or corruption in hosted datasets.
 #6.5.5    Level: 3    Role: D
 Ensure that disallowed content (copyrighted material, personally identifiable information) is removed through automated scrubbing before training.

---

### C6.6 Supply Chain Attack Monitoring

Detect supply chain threats early through CVE feeds, audit log analytics, and red team simulations.

 #6.6.1    Level: 1    Role: V
 Verify that CI/CD audit logs are streamed to SIEM detections to identify anomalous package pulls or tampered build steps.
 #6.6.2    Level: 2    Role: D
 Ensure that incident response playbooks include rollback procedures for compromised models or libraries.
 #6.6.3    Level: 3    Role: V
 Verify that threat-intel enrichment tags machine learning–specific indicators (e.g., model-poisoning IoCs) during alert triage.

---

### C6.7 ML-BOM for Model Artifacts

Generate and sign detailed ML-specific SBOMs (ML-BOMs) so downstream consumers can verify component integrity at deployment time.

 #6.7.1    Level: 1    Role: D/V
 Verify that each model artifact publishes an ML-BOM that lists datasets, weights, hyperparameters, and licenses.
 #6.7.2    Level: 1    Role: D/V
 Verify that ML-BOM generation and Cosign signing are automated in the CI process and mandatory for merging.
 #6.7.3    Level: 2    Role: D
 Verify that ML-BOM completeness checks cause the build to fail if any component metadata (hash, license) is missing.
 #6.7.4    Level: 2    Role: V
 Verify that downstream consumers can query ML-BOMs through the API to validate imported models at deployment time.
 #6.7.5    Level: 3    Role: V
 Ensure that ML-BOMs are version-controlled and compared using diffs to detect unauthorized changes.

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

## C7 Model Behavior, Output Control, and Safety Assurance

### Control Objective

Model outputs must be structured, reliable, safe, explainable, and continuously monitored in production. This approach reduces hallucinations, privacy leaks, harmful content, and runaway actions, while increasing user trust and regulatory compliance.

---

### C7.1 Output Format Enforcement

Strict schemas, constrained decoding, and downstream validation prevent malformed or malicious content from propagating.

 #7.1.1    Level: 1    Role: D/V
 Ensure that response schemas (e.g., JSON Schema) are provided in the system prompt and that every output is automatically validated; outputs that do not conform trigger repair or rejection.
 #7.1.2    Level: 1    Role: D/V
 Ensure that constrained decoding (stop tokens, regex, max tokens) is enabled to prevent overflow or prompt-injection side channels.
 #7.1.3    Level: 2    Role: D/V
 Ensure that downstream components treat outputs as untrusted and validate them against schemas or injection-safe deserializers.
 #7.1.4    Level: 3    Role: V
 Verify that improper output events are logged, rate-limited, and displayed in monitoring.

---

### C7.2 Hallucination Detection and Mitigation

Estimating uncertainty and implementing fallback strategies help prevent fabricated answers.

 #7.2.1    Level: 1    Role: D/V
 Verify that token-level log-probabilities, ensemble self-consistency, or fine-tuned hallucination detectors assign a confidence score to each answer.
 #7.2.2    Level: 1    Role: D/V
 Ensure that responses falling below a configurable confidence threshold activate fallback workflows (e.g., retrieval-augmented generation, secondary models, or human review).
 #7.2.3    Level: 2    Role: D/V
 Ensure that hallucination incidents are tagged with root-cause metadata and fed into post-mortem and fine-tuning pipelines.
 #7.2.4    Level: 3    Role: D/V
 Verify that thresholds and detectors are recalibrated after major model or knowledge base updates.
 #7.2.5    Level: 3    Role: V
 Verify that dashboard visualizations track hallucination rates.

---

### C7.3 Output Safety and Privacy Filtering

Policy filters and red-team coverage safeguard users and confidential data.

 #7.3.1    Level: 1    Role: D/V
 Verify that pre- and post-generation classifiers block hate, harassment, self-harm, extremist, and sexually explicit content in alignment with policy.
 #7.3.2    Level: 1    Role: D/V
 Ensure that PII/PCI detection and automatic redaction occur on every response; any violations trigger a privacy incident report.
 #7.3.3    Level: 2    Role: D
 Verify that confidentiality tags (e.g., trade secrets) propagate across modalities to prevent leakage in text, images, or code.
 #7.3.4    Level: 3    Role: D/V
 Ensure that filter bypass attempts or high-risk classifications require secondary approval or user re-authentication.
 #7.3.5    Level: 3    Role: D/V
 Ensure that filtering thresholds correspond to applicable legal jurisdictions and the user's age or role context.

---

### C7.4 Output and Action Limiting

Rate limits and approval gates prevent abuse and excessive autonomy.

 #7.4.1    Level: 1    Role: D
 Verify that per-user and per-API-key quotas limit requests, tokens, and costs with exponential backoff on 429 errors.
 #7.4.2    Level: 1    Role: D/V
 Ensure that privileged actions (file writes, code execution, network calls) require approval based on policy or involve human intervention.
 #7.4.3    Level: 2    Role: D/V
 Verify that cross-modal consistency checks ensure images, code, and text generated for the same request cannot be used to conceal malicious content.
 #7.4.4    Level: 2    Role: D
 Ensure that agent delegation depth, recursion limits, and allowed tool lists are explicitly configured.
 #7.4.5    Level: 3    Role: V
 Verify that exceeding limits generates structured security events for SIEM ingestion.

---

### C7.5 Output Explainability

Transparent signals enhance user trust and facilitate internal debugging.

 #7.5.1    Level: 2    Role: D/V
 Ensure that user-facing confidence scores or brief reasoning summaries are provided when the risk assessment deems it appropriate.
 #7.5.2    Level: 2    Role: D/V
 Ensure that generated explanations do not disclose sensitive system prompts or proprietary information.
 #7.5.3    Level: 3    Role: D
 Verify that the system captures token-level log probabilities or attention maps and stores them for authorized inspection.
 #7.5.4    Level: 3    Role: V
 Ensure that explainability artifacts are version-controlled alongside model releases to maintain auditability.

---

### C7.6 Monitoring Integration

Real-time observability closes the gap between development and production.

 #7.6.1    Level: 1    Role: D
 Verify that metrics (schema violations, hallucination rate, toxicity, PII leaks, latency, cost) are streamed to a central monitoring platform.
 #7.6.2    Level: 1    Role: V
 Verify that alert thresholds are established for each safety metric, with on-call escalation paths defined.
 #7.6.3    Level: 2    Role: V
 Verify that dashboards correlate output anomalies with the model/version, feature flag, and upstream data changes.
 #7.6.4    Level: 2    Role: D/V
 Verify that monitoring data is fed back into retraining, fine-tuning, or rule updates within a documented MLOps workflow.
 #7.6.5    Level: 3    Role: V
 Ensure that monitoring pipelines are penetration-tested and access-controlled to prevent leakage of sensitive logs.

---

### 7.7 Safeguards for Generative Media

Ensure that AI systems do not produce illegal, harmful, or unauthorized media content by enforcing policy constraints, validating outputs, and maintaining traceability.

 #7.7.1    Level: 1    Role: D/V
 Ensure that system prompts and user instructions explicitly forbid generating illegal, harmful, or non-consensual deepfake media (such as images, videos, or audio).
 #7.7.2    Level: 2    Role: D/V
 Ensure that prompts are screened to prevent attempts to generate impersonations, sexually explicit deepfakes, or media depicting real individuals without their consent.
 #7.7.3    Level: 2    Role: V
 Verify that the system uses perceptual hashing, watermark detection, or fingerprinting to prevent unauthorized reproduction of copyrighted media.
 #7.7.4    Level: 3    Role: D/V
 Verify that all generated media is cryptographically signed, watermarked, or embedded with tamper-resistant provenance metadata to ensure downstream traceability.
 #7.7.5    Level: 3    Role: V
 Verify that bypass attempts (e.g., prompt obfuscation, slang, adversarial phrasing) are detected, logged, and rate-limited, and that repeated abuse is reported to monitoring systems.

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

## C8 Memory, Embeddings, and Vector Database Security

### Control Objective

Embeddings and vector stores serve as the "live memory" of modern AI systems, continuously receiving user-supplied data and feeding it back into model contexts through Retrieval-Augmented Generation (RAG). If not properly governed, this memory can leak Personally Identifiable Information (PII), violate consent, or be exploited to reconstruct the original text. The goal of this control family is to strengthen memory pipelines and vector databases by ensuring least-privilege access, preserving privacy in embeddings, enabling stored vectors to expire or be revoked on demand, and preventing per-user memory from contaminating another user's prompts or completions.

---

### C8.1 Access Controls on Memory & RAG Indices

Enforce detailed access controls on every vector collection.

 #8.1.1    Level: 1    Role: D/V
 Verify that row- and namespace-level access control rules restrict insert, delete, and query operations according to tenant, collection, or document tag.
 #8.1.2    Level: 1    Role: D/V
 Ensure that API keys or JWTs include scoped claims (such as collection IDs and action verbs) and are rotated at least every quarter.
 #8.1.3    Level: 2    Role: D/V
 Ensure that privilege-escalation attempts (e.g., cross-namespace similarity queries) are detected and logged to a SIEM within 5 minutes.
 #8.1.4    Level: 2    Role: D/V
 Verify that the vector database audit logs include the subject identifier, operation, vector ID/namespace, similarity threshold, and result count.
 #8.1.5    Level: 3    Role: V
 Verify that access decisions are tested for bypass vulnerabilities whenever engines are upgraded or index-sharding rules are modified.

---

### C8.2 Embedding Sanitization and Validation

Pre-screen text for PII, redact or pseudonymize before vectorization, and optionally post-process embeddings to remove residual signals.

 #8.2.1    Level: 1    Role: D/V
 Ensure that PII and regulated data are detected by automated classifiers and are masked, tokenized, or removed before embedding.
 #8.2.2    Level: 1    Role: D
 Verify that embedding pipelines reject or quarantine inputs containing executable code or non-UTF-8 artifacts that could compromise the index.
 #8.2.3    Level: 2    Role: D/V
 Verify that local or metric differential privacy sanitization is applied to sentence embeddings when their distance to any known PII token falls below a configurable threshold.
 #8.2.4    Level: 2    Role: V
 Verify that the effectiveness of sanitization (e.g., recall of PII redaction, semantic drift) is validated at least semiannually against benchmark corpora.
 #8.2.5    Level: 3    Role: D/V
 Ensure that sanitization configurations are version-controlled and that any changes undergo peer review.

---

### C8.3 Memory Expiry, Revocation, and Deletion

GDPR's "right to be forgotten" and similar laws require prompt erasure; therefore, vector stores must support TTLs, hard deletes, and tombstoning to ensure that revoked vectors cannot be recovered or re-indexed.

 #8.3.1    Level: 1    Role: D/V
 Ensure that every vector and metadata record has a TTL or an explicit retention label that is respected by automated cleanup processes.
 #8.3.2    Level: 1    Role: D/V
 Verify that user-initiated deletion requests remove vectors, metadata, cached copies, and derivative indices within 30 days.
 #8.3.3    Level: 2    Role: D
 Verify that logical deletions are followed by cryptographic shredding of storage blocks if supported by hardware, or by destruction of the key-vault keys.
 #8.3.4    Level: 3    Role: D/V
 Verify that expired vectors are excluded from nearest-neighbor search results within 500 ms after expiration.

---

### C8.4 Prevent Embedding Inversion and Leakage

Recent defenses—noise superposition, projection networks, privacy-neuron perturbation, and application-layer encryption—can reduce token-level inversion rates to below 5%.

 #8.4.1    Level: 1    Role: V
 Ensure that a formal threat model addressing inversion, membership, and attribute-inference attacks exists and is reviewed annually.
 #8.4.2    Level: 2    Role: D/V
 Ensure that application-layer encryption or searchable encryption protects vectors from direct access by infrastructure administrators or cloud personnel.
 #8.4.3    Level: 3    Role: V
 Verify that defense parameters (ε for DP, noise σ, projection rank k) maintain privacy at ≥ 99% token protection and utility with ≤ 3% accuracy loss.
 #8.4.4    Level: 3    Role: D/V
 Ensure that inversion-resilience metrics are included as part of the release gates for model updates, with clearly defined regression budgets.

---

### C8.5 Scope Enforcement for User-Specific Memory

Cross-tenant leakage remains a top RAG risk: improperly filtered similarity queries can expose another customer's private documents.

 #8.5.1    Level: 1    Role: D/V
 Verify that every retrieval query is post-filtered by tenant/user ID before it is passed to the LLM prompt.
 #8.5.2    Level: 1    Role: D
 Ensure that collection names or namespaced IDs are uniquely salted per user or tenant to prevent vector collisions across different scopes.
 #8.5.3    Level: 2    Role: D/V
 Verify that similarity results exceeding a configurable distance threshold but falling outside the caller's scope are discarded and trigger security alerts.
 #8.5.4    Level: 2    Role: V
 Verify that multi-tenant stress tests simulate adversarial queries that attempt to retrieve out-of-scope documents and demonstrate zero leakage.
 #8.5.5    Level: 3    Role: D/V
 Ensure that encryption keys are segregated per tenant, providing cryptographic isolation even when physical storage is shared.

---

### C8.6 Advanced Memory System Security

Security controls for advanced memory architectures, including episodic, semantic, and working memory, with specific isolation and validation requirements.

 #8.6.1    Level: 1    Role: D/V
 Verify that the different memory types (episodic, semantic, working) have isolated security contexts with role-based access controls, separate encryption keys, and documented access patterns for each memory type.
 #8.6.2    Level: 2    Role: D/V
 Ensure that memory consolidation processes include security validation to prevent the injection of malicious memories by implementing content sanitization, source verification, and integrity checks before storage.
 #8.6.3    Level: 2    Role: D/V
 Verify that memory retrieval queries are validated and sanitized to prevent the extraction of unauthorized information through query pattern analysis, access control enforcement, and result filtering.
 #8.6.4    Level: 3    Role: D/V
 Ensure that memory forgetting mechanisms securely erase sensitive information by providing cryptographic erasure guarantees through methods such as key deletion, multi-pass overwriting, or hardware-based secure deletion accompanied by verification certificates.
 #8.6.5    Level: 3    Role: D/V
 Verify that the memory system integrity is continuously monitored for unauthorized modifications or corruption using checksums, audit logs, and automated alerts when memory content changes outside of normal operations.

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

## 9 Autonomous Orchestration & Agentic Action Security

### Control Objective

Ensure that autonomous or multi-agent AI systems can only perform actions that are explicitly intended, authenticated, auditable, and within defined cost and risk limits. This safeguards against threats such as Autonomous System Compromise, Tool Misuse, Agent Loop Detection, Communication Hijacking, Identity Spoofing, Swarm Manipulation, and Intent Manipulation.

---

### 9.1 Agent Task Planning & Recursion Budgets

Throttle recursive plans and enforce human checkpoints for privileged actions.

 #9.1.1    Level: 1    Role: D/V
 Verify that the maximum recursion depth, breadth, wall-clock time, tokens, and monetary cost per agent execution are centrally configured and version-controlled.
 #9.1.2    Level: 1    Role: D/V
 Verify that privileged or irreversible actions (e.g., code commits, financial transfers) require explicit human approval through an auditable channel before execution.
 #9.1.3    Level: 2    Role: D
 Verify that real-time resource monitors trigger the circuit breaker interruption when any budget threshold is exceeded, stopping further task expansion.
 #9.1.4    Level: 2    Role: D/V
 Ensure that circuit-breaker events are logged with the agent ID, triggering condition, and the captured plan state for forensic review.
 #9.1.5    Level: 3    Role: V
 Verify that security tests cover budget exhaustion and runaway plan scenarios, ensuring safe halting without data loss.
 #9.1.6    Level: 3    Role: D
 Ensure that budget policies are defined as policy-as-code and enforced within the CI/CD pipeline to prevent configuration drift.

---

### 9.2 Tool Plugin Sandboxing

Isolate tool interactions to prevent unauthorized access to the system or execution of code.

 #9.2.1    Level: 1    Role: D/V
 Ensure that every tool or plugin runs inside an OS, container, or WASM-level sandbox with least-privilege policies for the file system, network, and system calls.
 #9.2.2    Level: 1    Role: D/V
 Verify that sandbox resource quotas (CPU, memory, disk, network egress) and execution timeouts are enforced and logged.
 #9.2.3    Level: 2    Role: D/V
 Verify that tool binaries or descriptors are digitally signed, and validate signatures before loading.
 #9.2.4    Level: 2    Role: V
 Verify that sandbox telemetry streams to a SIEM; anomalies (e.g., attempted outbound connections) trigger alerts.
 #9.2.5    Level: 3    Role: V
 Ensure that high-risk plugins undergo security reviews and penetration testing before being deployed to production.
 #9.2.6    Level: 3    Role: D/V
 Verify that sandbox escape attempts are automatically blocked and that the offending plugin is quarantined pending investigation.

---

### 9.3 Autonomous Loop and Cost Bounding

Detect and prevent uncontrolled agent-to-agent recursion and cost overruns.

 #9.3.1    Level: 1    Role: D/V
 Verify that inter-agent calls include a hop limit or TTL that the runtime decrements and enforces.
 #9.3.2    Level: 2    Role: D
 Ensure that agents maintain a unique invocation-graph ID to detect self-invocation or cyclical patterns.
 #9.3.3    Level: 2    Role: D/V
 Verify that cumulative compute-unit and spend counters are tracked for each request chain; exceeding the limit aborts the chain.
 #9.3.4    Level: 3    Role: V
 Confirm that formal analysis or model checking verifies the absence of unbounded recursion in agent protocols.
 #9.3.5    Level: 3    Role: D
 Verify that loop-abort events generate alerts and provide continuous improvement metrics.

---

### 9.4 Protocol-Level Misuse Protection

Secure communication channels between agents and external systems to prevent hijacking or manipulation.

 #9.4.1    Level: 1    Role: D/V
 Ensure that all messages between agents and tools, as well as between agents themselves, are authenticated (e.g., using mutual TLS or JWT) and secured with end-to-end encryption.
 #9.4.2    Level: 1    Role: D
 Verify that schemas are strictly validated; reject unknown fields or malformed messages.
 #9.4.3    Level: 2    Role: D/V
 Verify that integrity checks (MACs or digital signatures) cover the entire message payload, including tool parameters.
 #9.4.4    Level: 2    Role: D
 Verify that replay protection (nonces or timestamp windows) is enforced at the protocol layer.
 #9.4.5    Level: 3    Role: V
 Verify that protocol implementations undergo both fuzz testing and static analysis to detect injection or deserialization vulnerabilities.

---

### 9.5 Agent Identity and Tamper Evidence

Ensure actions can be attributed and modifications can be detected.

 #9.5.1    Level: 1    Role: D/V
 Ensure that each agent instance has a unique cryptographic identity (key pair or hardware-rooted credential).
 #9.5.2    Level: 2    Role: D/V
 Verify that all agent actions are signed and timestamped; logs contain the signature to ensure non-repudiation.
 #9.5.3    Level: 2    Role: V
 Verify that tamper-evident logs are stored in an append-only or write-once medium.
 #9.5.4    Level: 3    Role: D
 Ensure that identity keys rotate according to a defined schedule and upon detection of compromise indicators.
 #9.5.5    Level: 3    Role: D/V
 Verify that spoofing or key conflict attempts trigger the immediate quarantine of the affected agent.

---

### 9.6 Multi-Agent Swarm Risk Reduction

Mitigate collective behavior hazards through isolation and formal safety modeling.

 #9.6.1    Level: 1    Role: D/V
 Ensure that agents operating in different security domains run in isolated runtime sandboxes or network segments.
 #9.6.2    Level: 3    Role: V
 Ensure that swarm behaviors are modeled and formally verified for both liveness and safety prior to deployment.
 #9.6.3    Level: 3    Role: D
 Verify that runtime monitors detect emerging unsafe patterns (e.g., oscillations, deadlocks) and initiate corrective actions.

---

### 9.7 User and Tool Authentication / Authorization

Implement robust access controls for every agent-triggered action.

 #9.7.1    Level: 1    Role: D/V
 Ensure that agents authenticate as first-class principals to downstream systems, never reusing end-user credentials.
 #9.7.2    Level: 2    Role: D
 Verify that fine-grained authorization policies limit which tools an agent can invoke and which parameters it can provide.
 #9.7.3    Level: 2    Role: V
 Ensure that privilege checks are re-evaluated on every call (continuous authorization), not just at the start of the session.
 #9.7.4    Level: 3    Role: D
 Verify that delegated privileges automatically expire and require re-consent after a timeout or a change in scope.

---

### 9.8 Security of Agent-to-Agent Communication

Encrypt and provide integrity protection for all inter-agent messages to prevent eavesdropping and tampering.

 #9.8.1    Level: 1    Role: D/V
 Verify that mutual authentication and perfect forward secrecy encryption (e.g., TLS 1.3) are mandatory for agent channels.
 #9.8.2    Level: 1    Role: D
 Verify that message integrity and origin are validated before processing; failures trigger alerts and cause the message to be dropped.
 #9.8.3    Level: 2    Role: D/V
 Ensure that communication metadata (timestamps, sequence numbers) is logged to support forensic reconstruction.
 #9.8.4    Level: 3    Role: V
 Verify that formal verification or model checking confirms that protocol state machines cannot be driven into unsafe states.

---

### 9.9 Intent Verification and Constraint Enforcement

Verify that agent actions correspond with the user's expressed intent and system constraints.

 #9.9.1    Level: 1    Role: D
 Ensure that pre-execution constraint solvers validate proposed actions against hard-coded safety and policy rules.
 #9.9.2    Level: 2    Role: D/V
 Ensure that high-impact actions (financial, destructive, privacy-sensitive) require explicit confirmation of intent from the initiating user.
 #9.9.3    Level: 2    Role: V
 Verify that post-condition checks ensure completed actions achieve their intended effects without side effects; any discrepancies trigger a rollback.
 #9.9.4    Level: 3    Role: V
 Verify that formal methods (e.g., model checking, theorem proving) or property-based tests demonstrate that agent plans satisfy all specified constraints.
 #9.9.5    Level: 3    Role: D
 Ensure that incidents of intent mismatch or constraint violation contribute to continuous improvement cycles and the sharing of threat intelligence.

---

### 9.10 Agent Reasoning Strategy Security

Secure selection and execution of various reasoning strategies, including ReAct, Chain-of-Thought, and Tree-of-Thoughts approaches.

 #9.10.1    Level: 1    Role: D/V
 Verify that the selection of reasoning strategies uses deterministic criteria (input complexity, task type, security context) and that identical inputs produce identical strategy selections within the same security context.
 #9.10.2    Level: 1    Role: D/V
 Verify that each reasoning strategy (ReAct, Chain-of-Thought, Tree-of-Thoughts) includes dedicated input validation, output sanitization, and execution time limits tailored to its specific cognitive approach.
 #9.10.3    Level: 2    Role: D/V
 Verify that reasoning strategy transitions are logged with complete context, including input characteristics, selection criteria values, and execution metadata, to enable audit trail reconstruction.
 #9.10.4    Level: 2    Role: D/V
 Verify that Tree-of-Thoughts reasoning includes branch pruning mechanisms that terminate exploration when policy violations, resource limits, or safety boundaries are detected.
 #9.10.5    Level: 2    Role: D/V
 Verify that ReAct (Reason-Act-Observe) cycles include validation checkpoints at each phase: reasoning step verification, action authorization, and observation sanitization before proceeding.
 #9.10.6    Level: 3    Role: D/V
 Ensure that reasoning strategy performance metrics (execution time, resource usage, output quality) are monitored with automated alerts triggered when metrics exceed configured thresholds.
 #9.10.7    Level: 3    Role: D/V
 Ensure that hybrid reasoning approaches combining multiple strategies uphold input validation and output constraints of all individual strategies, without bypassing any security controls.
 #9.10.8    Level: 3    Role: D/V
 Ensure that reasoning strategy security testing includes fuzzing with malformed inputs, adversarial prompts designed to trigger strategy switching, and boundary condition testing for each cognitive approach.

---

### 9.11 Agent Lifecycle State Management and Security

Secure agent initialization, state transitions, and termination with cryptographic audit trails and clearly defined recovery procedures.

 #9.11.1    Level: 1    Role: D/V
 Verify that agent initialization includes establishing a cryptographic identity with hardware-backed credentials and immutable startup audit logs containing the agent ID, timestamp, configuration hash, and initialization parameters.
 #9.11.2    Level: 2    Role: D/V
 Verify that agent state transitions are cryptographically signed, timestamped, and logged with complete context, including triggering events, previous state hash, new state hash, and performed security validations.
 #9.11.3    Level: 2    Role: D/V
 Ensure that agent shutdown procedures include secure memory wiping through cryptographic erasure or multi-pass overwriting, credential revocation with notification to the certificate authority, and the generation of tamper-evident termination certificates.
 #9.11.4    Level: 3    Role: D/V
 Verify that agent recovery mechanisms validate state integrity using cryptographic checksums (minimum SHA-256) and rollback to known good states when corruption is detected, with automated alerts and manual approval requirements.
 #9.11.5    Level: 3    Role: D/V
 Ensure that agent persistence mechanisms encrypt sensitive state data using per-agent AES-256 keys and implement secure key rotation on configurable schedules (up to a maximum of 90 days) with zero-downtime deployment.

---

### 9.12 Tool Integration Security Framework

Security controls for dynamic tool loading, execution, and result validation with clearly defined risk assessment and approval procedures.

 #9.12.1    Level: 1    Role: D/V
 Verify that tool descriptors include security metadata specifying required privileges (read/write/execute), risk levels (low/medium/high), resource limits (CPU, memory, network), and validation requirements documented in tool manifests.
 #9.12.2    Level: 1    Role: D/V
 Verify that tool execution results are validated against the expected schemas (JSON Schema, XML Schema) and security policies (output sanitization, data classification) before integration, with timeout limits and error handling procedures in place.
 #9.12.3    Level: 2    Role: D/V
 Ensure that tool interaction logs contain detailed security context, including privilege usage, data access patterns, execution time, resource consumption, and return codes, with structured logging for SIEM integration.
 #9.12.4    Level: 2    Role: D/V
 Verify that dynamic tool loading mechanisms validate digital signatures using Public Key Infrastructure (PKI) and implement secure loading protocols with sandbox isolation and permission verification prior to execution.
 #9.12.5    Level: 3    Role: D/V
 Verify that tool security assessments are automatically triggered for new versions with mandatory approval gates, including static analysis, dynamic testing, and security team review, with documented approval criteria and SLA requirements.

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

## 10 Adversarial Robustness & Privacy Defense

### Control Objective

Ensure that AI models remain reliable, protect privacy, and resist abuse when confronted with evasion, inference, extraction, or poisoning attacks.

---

### 10.1 Model Alignment and Safety

Protect against harmful or policy-violating outputs.

 #10.1.1    Level: 1    Role: D/V
 Ensure that an alignment test suite (including red-team prompts, jailbreak probes, and disallowed content) is version-controlled and executed with every model release.
 #10.1.2    Level: 1    Role: D
 Verify that refusal and safe-completion guardrails are enforced.
 #10.1.3    Level: 2    Role: D/V
 Verify that an automated evaluator measures the harmful content rate and flags regressions that exceed a set threshold.
 #10.1.4    Level: 2    Role: D
 Verify that counter-jailbreak training is thoroughly documented and can be reliably reproduced.
 #10.1.5    Level: 3    Role: V
 Ensure that formal policy compliance proofs or certified monitoring cover critical domains.

---

### 10.2 Adversarial Example Hardening

Enhance resilience to manipulated inputs. Robust adversarial training and benchmark scoring remain the best current practices.

 #10.2.1    Level: 1    Role: D
 Verify that project repositories contain adversarial training configurations with reproducible seeds.
 #10.2.2    Level: 2    Role: D/V
 Confirm that adversarial example detection triggers blocking alerts in production pipelines.
 #10.2.4    Level: 3    Role: V
 Verify that certified robustness proofs or interval-bound certificates cover at least the most critical top classes.
 #10.2.5    Level: 3    Role: V
 Verify that regression tests employ adaptive attacks to confirm there is no measurable loss of robustness.

---

### 10.3 Membership Inference Mitigation

Limit the ability to determine whether a record was included in the training data. Differential privacy and confidence score masking remain the most effective known defenses.

 #10.3.1    Level: 1    Role: D
 Verify that per-query entropy regularization or temperature scaling reduces overconfident predictions.
 #10.3.2    Level: 2    Role: D
 Verify that the training process uses ε-bounded differentially private optimization for sensitive datasets.
 #10.3.3    Level: 2    Role: V
 Verify that attack simulations (shadow-model or black-box) demonstrate an attack AUC of ≤ 0.60 on held-out data.

---

### 10.4 Resistance to Model Inversion

Prevent reconstruction of private attributes. Recent surveys highlight output truncation and differential privacy guarantees as effective defenses.

 #10.4.1    Level: 1    Role: D
 Ensure that sensitive attributes are never directly outputted; when necessary, use buckets or one-way transformations.
 #10.4.2    Level: 1    Role: D/V
 Verify that query rate limits throttle repeated adaptive queries from the same principal.
 #10.4.3    Level: 2    Role: D
 Verify that the model is trained using privacy-preserving noise.

---

### 10.5 Model Extraction Defense

Detect and prevent unauthorized cloning. Watermarking and query pattern analysis are recommended.

 #10.5.1    Level: 1    Role: D
 Ensure that inference gateways enforce both global and per-API-key rate limits, calibrated to the model's memorization threshold.
 #10.5.2    Level: 2    Role: D/V
 Verify that query-entropy and input-plurality statistics are used to feed an automated extraction detector.
 #10.5.3    Level: 2    Role: V
 Verify that fragile or probabilistic watermarks can be proven with p < 0.01 in ≤ 1,000 queries against a suspected clone.
 #10.5.4    Level: 3    Role: D
 Verify that watermark keys and trigger sets are stored in a hardware security module and rotated annually.
 #10.5.5    Level: 3    Role: V
 Verify that extraction-alert events include the offending queries and are integrated with incident response playbooks.

---

### 10.6 Detection of Poisoned Data During Inference Time

Identify and neutralize backdoored or poisoned inputs.

 #10.6.1    Level: 1    Role: D
 Verify that inputs pass through an anomaly detector (e.g., STRIP, consistency scoring) before model inference.
 #10.6.2    Level: 1    Role: V
 Verify that detector thresholds are tuned on clean and poisoned validation sets to achieve less than 5% false positives.
 #10.6.3    Level: 2    Role: D
 Verify that inputs identified as poisoned trigger soft-blocking and human review workflows.
 #10.6.4    Level: 2    Role: V
 Verify that detectors are stress-tested using adaptive, triggerless backdoor attacks.
 #10.6.5    Level: 3    Role: D
 Ensure that detection efficacy metrics are logged and periodically re-evaluated using updated threat intelligence.

---

### 10.7 Dynamic Security Policy Adaptation

Real-time security policy updates based on threat intelligence and behavioral analysis.

 #10.7.1    Level: 1    Role: D/V
 Verify that security policies can be updated dynamically without restarting the agent while maintaining the integrity of the policy version.
 #10.7.2    Level: 2    Role: D/V
 Ensure that policy updates are cryptographically signed by authorized security personnel and validated before being applied.
 #10.7.3    Level: 2    Role: D/V
 Verify that dynamic policy changes are logged with complete audit trails, including justification, approval chains, and rollback procedures.
 #10.7.4    Level: 3    Role: D/V
 Verify that adaptive security mechanisms adjust threat detection sensitivity according to risk context and behavioral patterns.
 #10.7.5    Level: 3    Role: D/V
 Ensure that policy adaptation decisions are explainable and include evidence trails for review by the security team.

---

### 10.8 Reflection-Based Security Analysis

Security validation through agent self-reflection and metacognitive analysis.

 #10.8.1    Level: 1    Role: D/V
 Ensure that agent reflection mechanisms incorporate security-focused self-assessment of decisions and actions.
 #10.8.2    Level: 2    Role: D/V
 Verify that reflection outputs are validated to prevent adversarial inputs from manipulating self-assessment mechanisms.
 #10.8.3    Level: 2    Role: D/V
 Verify that meta-cognitive security analysis detects potential biases, manipulation, or compromises in agent reasoning processes.
 #10.8.4    Level: 3    Role: D/V
 Verify that reflection-based security warnings activate enhanced monitoring and possible human intervention workflows.
 #10.8.5    Level: 3    Role: D/V
 Verify that continuous learning from security reflections enhances threat detection without compromising legitimate functionality.

---

### 10.9 Evolution and Self-Improvement Security

Security controls for agent systems that are capable of self-modification and evolution.

 #10.9.1    Level: 1    Role: D/V
 Ensure that self-modification capabilities are limited to designated safe areas with formal verification boundaries.
 #10.9.2    Level: 2    Role: D/V
 Ensure that evolution proposals undergo a security impact assessment before implementation.
 #10.9.3    Level: 2    Role: D/V
 Verify that self-improvement mechanisms include rollback capabilities with integrity verification.
 #10.9.4    Level: 3    Role: D/V
 Ensure that meta-learning security effectively prevents adversarial manipulation of improvement algorithms.
 #10.9.5    Level: 3    Role: D/V
 Verify that recursive self-improvement is constrained by formal safety parameters with mathematical proofs demonstrating convergence.

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

Ensure strict privacy protections throughout the entire AI lifecycle—collection, training, inference, and incident response—so that personal data is processed only with explicit consent, limited to the minimum necessary scope, with verifiable erasure, and formal privacy guarantees.

---

### 11.1 Anonymization & Data Minimization

 #11.1.1    Level: 1    Role: D/V
 Verify that direct and quasi-identifiers are removed or hashed.
 #11.1.2    Level: 2    Role: D/V
 Verify that automated audits measure k-anonymity and l-diversity, and send alerts when thresholds fall below the policy limits.
 #11.1.3    Level: 2    Role: V
 Verify that the model's feature importance reports demonstrate no identifier leakage beyond ε = 0.01 mutual information.
 #11.1.4    Level: 3    Role: V
 Verify that formal proofs or synthetic-data certification demonstrate a re-identification risk of ≤ 0.05, even under linkage attacks.

---

### 11.2 Right to Be Forgotten & Deletion Enforcement

 #11.2.1    Level: 1    Role: D/V
 Ensure that data-subject deletion requests are propagated to raw datasets, checkpoints, embeddings, logs, and backups within service level agreements of less than 30 days.
 #11.2.2    Level: 2    Role: D
 Confirm that "machine unlearning" procedures physically retrain or approximate removal through certified unlearning algorithms.
 #11.2.3    Level: 2    Role: V
 Verify that shadow-model evaluation demonstrates that forgotten records influence less than 1% of outputs after unlearning.
 #11.2.4    Level: 3    Role: V
 Ensure that deletion events are immutably logged and can be audited for regulatory compliance.

---

### 11.3 Differential Privacy Safeguards

 #11.3.1    Level: 2    Role: D/V
 Verify that privacy-loss accounting dashboards trigger alerts when cumulative ε exceeds policy thresholds.
 #11.3.2    Level: 2    Role: V
 Verify that black-box privacy audits estimate ε̂ within 10% of the declared value.
 #11.3.3    Level: 3    Role: V
 Verify that formal proofs encompass all post-training fine-tuning and embeddings.

---

### 11.4 Purpose Limitation & Scope Creep Protection

 #11.4.1    Level: 1    Role: D
 Ensure that every dataset and model checkpoint includes a machine-readable purpose tag that aligns with the original consent.
 #11.4.2    Level: 1    Role: D/V
 Verify that runtime monitors detect queries inconsistent with the declared purpose and trigger a soft refusal.
 #11.4.3    Level: 3    Role: D
 Verify that policy-as-code gates prevent redeployment of models to new domains without a DPIA review.
 #11.4.4    Level: 3    Role: V
 Verify that formal traceability proofs demonstrate that every personal data lifecycle stays within the consented scope.

---

### 11.5 Consent Management & Lawful Basis Tracking

 #11.5.1    Level: 1    Role: D/V
 Verify that a Consent Management Platform (CMP) records the opt-in status, purpose, and retention period for each data subject.
 #11.5.2    Level: 2    Role: D
 Verify that APIs expose consent tokens; models must validate the token scope before inference.
 #11.5.3    Level: 2    Role: D/V
 Verify that denied or withdrawn consent stops processing pipelines within 24 hours.

---

### 11.6 Federated Learning with Privacy Controls

 #11.6.1    Level: 1    Role: D
 Ensure that client updates use local differential privacy noise addition prior to aggregation.
 #11.6.2    Level: 2    Role: D/V
 Ensure that training metrics maintain differential privacy and never disclose the loss of any individual client.
 #11.6.3    Level: 2    Role: V
 Ensure that poisoning-resistant aggregation (such as Krum or Trimmed-Mean) is enabled.
 #11.6.4    Level: 3    Role: V
 Verify that formal proofs demonstrate an overall ε budget with less than 5 utility loss.

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

This section outlines the requirements for delivering real-time and forensic visibility into what the model and other AI components observe, perform, and return, enabling threats to be detected, triaged, and analyzed for learning.

### C12.1 Request and Response Logging

 #12.1.1    Level: 1    Role: D/V
 Verify that all user prompts and model responses are logged with appropriate metadata (e.g., timestamp, user ID, session ID, model version).
 #12.1.2    Level: 1    Role: D/V
 Verify that logs are stored in secure, access-controlled repositories with appropriate retention policies and backup procedures.
 #12.1.3    Level: 1    Role: D/V
 Verify that log storage systems implement encryption both at rest and in transit to protect sensitive information contained in logs.
 #12.1.4    Level: 1    Role: D/V
 Ensure that sensitive data in prompts and outputs is automatically redacted or masked before logging, with configurable redaction rules for PII, credentials, and proprietary information.
 #12.1.5    Level: 2    Role: D/V
 Verify that policy decisions and safety filtering actions are logged with enough detail to allow auditing and debugging of content moderation systems.
 #12.1.6    Level: 2    Role: D/V
 Ensure log integrity is protected through methods such as cryptographic signatures or write-only storage.

---

### C12.2 Abuse Detection and Alerting

 #12.2.1    Level: 1    Role: D/V
 Verify that the system detects and alerts on known jailbreak patterns, prompt injection attempts, and adversarial inputs using signature-based detection methods.
 #12.2.2    Level: 1    Role: D/V
 Verify that the system integrates with existing Security Information and Event Management (SIEM) platforms using standard log formats and protocols.
 #12.2.3    Level: 2    Role: D/V
 Verify that enriched security events include AI-specific context such as model identifiers, confidence scores, and safety filter decisions.
 #12.2.4    Level: 2    Role: D/V
 Verify that behavioral anomaly detection identifies unusual conversation patterns, excessive retry attempts, or systematic probing behavior.
 #12.2.5    Level: 2    Role: D/V
 Ensure that real-time alerting mechanisms notify security teams when potential policy violations or attack attempts are detected.
 #12.2.6    Level: 2    Role: D/V
 Verify that custom rules are implemented to detect AI-specific threat patterns, including coordinated jailbreak attempts, prompt injection campaigns, and model extraction attacks.
 #12.2.7    Level: 3    Role: D/V
 Verify that automated incident response workflows can isolate compromised models, block malicious users, and escalate critical security events.

---

### C12.3 Model Drift Detection

 #12.3.1    Level: 1    Role: D/V
 Ensure that the system tracks basic performance metrics such as accuracy, confidence scores, latency, and error rates across different model versions and time periods.
 #12.3.2    Level: 2    Role: D/V
 Verify that automated alerting triggers when performance metrics exceed predefined degradation thresholds or significantly deviate from baselines.
 #12.3.3    Level: 2    Role: D/V
 Verify that hallucination detection monitors identify and flag instances where model outputs contain factually incorrect, inconsistent, or fabricated information.

---

### C12.4 Performance & Behavior Telemetry

 #12.4.1    Level: 1    Role: D/V
 Ensure that operational metrics, including request latency, token consumption, memory usage, and throughput, are continuously collected and monitored.
 #12.4.2    Level: 1    Role: D/V
 Verify that success and failure rates are tracked, with error types and their root causes categorized.
 #12.4.3    Level: 2    Role: D/V
 Verify that resource utilization monitoring includes GPU/CPU usage, memory consumption, and storage requirements, with alerts for threshold breaches.

---

### C12.5 AI Incident Response Planning & Execution

 #12.5.1    Level: 1    Role: D/V
 Verify that incident response plans specifically address AI-related security events, including model compromise, data poisoning, and adversarial attacks.
 #12.5.2    Level: 2    Role: D/V
 Ensure that incident response teams have access to AI-specific forensic tools and expertise to investigate model behavior and attack vectors.
 #12.5.3    Level: 3    Role: D/V
 Verify that post-incident analysis includes considerations for model retraining, updates to safety filters, and integration of lessons learned into security controls.

---

### C12.5 AI Performance Degradation Detection

Monitor and detect deterioration in AI model performance and quality over time.

 #12.5.1    Level: 1    Role: D/V
 Ensure that model accuracy, precision, recall, and F1 scores are continuously monitored and compared against baseline thresholds.
 #12.5.2    Level: 1    Role: D/V
 Verify that data drift detection monitors changes in input distribution that could affect model performance.
 #12.5.3    Level: 2    Role: D/V
 Confirm that concept drift detection recognizes changes in the relationship between inputs and expected outputs.
 #12.5.4    Level: 2    Role: D/V
 Verify that performance degradation triggers automated alerts and initiates workflows for model retraining or replacement.
 #12.5.5    Level: 3    Role: V
 Verify that degradation root cause analysis links performance drops to data changes, infrastructure problems, or external factors.

---

### C12.6 DAG Visualization & Workflow Security

Protect workflow visualization systems from information leakage and manipulation attacks.

 #12.6.1    Level: 1    Role: D/V
 Ensure that DAG visualization data is sanitized to remove sensitive information before storage or transmission.
 #12.6.2    Level: 1    Role: D/V
 Verify that workflow visualization access controls ensure that only authorized users can view agent decision paths and reasoning traces.
 #12.6.3    Level: 2    Role: D/V
 Ensure that the DAG data integrity is protected by cryptographic signatures and tamper-evident storage mechanisms.
 #12.6.4    Level: 2    Role: D/V
 Ensure that workflow visualization systems perform input validation to prevent injection attacks via maliciously crafted node or edge data.
 #12.6.5    Level: 3    Role: D/V
 Ensure that real-time DAG updates are rate-limited and validated to prevent denial-of-service attacks on visualization systems.

---

### C12.7 Proactive Security Behavior Monitoring

Detection and prevention of security threats through proactive analysis of agent behavior.

 #12.7.1    Level: 1    Role: D/V
 Ensure that proactive agent behaviors are security-validated prior to execution through integration with risk assessment.
 #12.7.2    Level: 2    Role: D/V
 Ensure that autonomous initiative triggers include evaluation of the security context and assessment of the threat landscape.
 #12.7.3    Level: 2    Role: D/V
 Ensure that proactive behavior patterns are analyzed for potential security risks and unintended consequences.
 #12.7.4    Level: 3    Role: D/V
 Ensure that security-critical proactive actions require explicit approval chains accompanied by audit trails.
 #12.7.5    Level: 3    Role: D/V
 Verify that behavioral anomaly detection identifies deviations in proactive agent patterns that may indicate a compromise.

---

### References

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Human Oversight, Accountability, & Governance

### Control Objective

This chapter outlines requirements for maintaining human oversight and clear accountability chains in AI systems, ensuring explainability, transparency, and ethical stewardship throughout the AI lifecycle.

---

### C13.1 Kill Switch & Override Mechanisms

Provide shutdown or rollback procedures when unsafe behavior of the AI system is detected.

 #13.1.1    Level: 1    Role: D/V
 Verify that a manual kill-switch mechanism is in place to immediately stop AI model inference and outputs.
 #13.1.2    Level: 1    Role: D
 Verify that override controls are accessible only to authorized personnel.
 #13.1.3    Level: 3    Role: D/V
 Confirm that rollback procedures can restore previous model versions or safe-mode operations.
 #13.1.4    Level: 3    Role: V
 Ensure that override mechanisms are tested regularly.

---

### C13.2 Human-in-the-Loop Decision Checkpoints

Require human approval when stakes exceed predefined risk thresholds.

 #13.2.1    Level: 1    Role: D/V
 Ensure that high-risk AI decisions receive explicit human approval before execution.
 #13.2.2    Level: 1    Role: D
 Ensure that risk thresholds are clearly defined and automatically trigger human review workflows.
 #13.2.3    Level: 2    Role: D
 Ensure that time-sensitive decisions have fallback procedures in place if human approval cannot be obtained within the required timeframes.
 #13.2.4    Level: 3    Role: D/V
 Verify that escalation procedures clearly define authority levels for various decision types or risk categories, if applicable.

---

### C13.3 Chain of Responsibility & Auditability

Record operator actions and model decisions.

 #13.3.1    Level: 1    Role: D/V
 Ensure that all AI system decisions and human interventions are recorded with timestamps, user identities, and the rationale behind the decisions.
 #13.3.2    Level: 2    Role: D
 Ensure that audit logs are tamper-proof and incorporate integrity verification mechanisms.

---

### C13.4 Explainable AI Techniques

Surface feature importance, counterfactuals, and local explanations.

 #13.4.1    Level: 1    Role: D/V
 Ensure that AI systems provide basic explanations for their decisions in a human-readable format.
 #13.4.2    Level: 2    Role: V
 Ensure that the quality of explanations is validated through human evaluation studies and appropriate metrics.
 #13.4.3    Level: 3    Role: D/V
 Verify that feature importance scores or attribution methods (such as SHAP, LIME, etc.) are available for critical decisions.
 #13.4.4    Level: 3    Role: V
 Ensure that counterfactual explanations demonstrate how inputs could be altered to change outcomes, if relevant to the use case and domain.

---

### C13.5 Model Cards & Usage Disclosures

Maintain model cards for intended use, performance metrics, and ethical considerations.

 #13.5.1    Level: 1    Role: D
 Confirm that model cards document intended use cases, limitations, and known failure modes.
 #13.5.2    Level: 1    Role: D/V
 Ensure that performance metrics for all relevant use cases are clearly disclosed.
 #13.5.3    Level: 2    Role: D
 Ensure that ethical considerations, bias assessments, fairness evaluations, training data characteristics, and known limitations of the training data are documented and updated regularly.
 #13.5.4    Level: 2    Role: D/V
 Ensure that model cards are version-controlled and maintained throughout the model lifecycle with change tracking.

---

### C13.6 Uncertainty Quantification

Propagate confidence scores or entropy measures in the responses.

 #13.6.1    Level: 1    Role: D
 Verify that AI systems provide confidence scores or uncertainty measures with their outputs.
 #13.6.2    Level: 2    Role: D/V
 Ensure that uncertainty thresholds activate additional human review or alternative decision pathways.
 #13.6.3    Level: 2    Role: V
 Verify that uncertainty quantification methods are properly calibrated and validated against ground truth data.
 #13.6.4    Level: 3    Role: D/V
 Verify that uncertainty propagation is preserved throughout multi-step AI workflows.

---

### C13.7 User-Facing Transparency Reports

Provide regular disclosures on incidents, drift, and data usage.

 #13.7.1    Level: 1    Role: D/V
 Ensure that data usage policies and user consent management practices are clearly communicated to stakeholders.
 #13.7.2    Level: 2    Role: D/V
 Ensure that AI impact assessments are conducted and that the results are included in the reporting.
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

This comprehensive glossary provides definitions of key AI, ML, and security terms used throughout the AISVS to ensure clarity and a common understanding.

Adversarial Example: An input intentionally designed to cause an AI model to make an error, often by adding subtle perturbations that are imperceptible to humans.
​
Adversarial Robustness – In AI, adversarial robustness refers to a model's ability to maintain its performance and resist being deceived or manipulated by intentionally crafted malicious inputs designed to cause errors.
​
Agent – AI agents are software systems that use artificial intelligence to pursue goals and complete tasks on behalf of users. They demonstrate reasoning, planning, and memory and possess a level of autonomy to make decisions, learn, and adapt.
​
Agentic AI: AI systems capable of operating with a certain level of autonomy to achieve goals, often making decisions and taking actions without direct human intervention.
​
Attribute-Based Access Control (ABAC): An access control model where authorization decisions are made based on the attributes of the user, resource, action, and environment, evaluated at the time of the query.
​
Backdoor Attack: A type of data poisoning attack in which the model is trained to respond in a specific way to certain triggers while otherwise behaving normally.
​
Bias: Systematic errors in AI model outputs that may result in unfair or discriminatory outcomes for certain groups or in specific contexts.
​
Bias Exploitation: An attack technique that leverages known biases in AI models to manipulate outputs or outcomes.
​
Cedar: Amazon's policy language and engine for fine-grained permissions used to implement ABAC in AI systems.
​
Chain of Thought: A technique for enhancing reasoning in language models by generating intermediate reasoning steps before providing a final answer.
​
Circuit Breakers: Mechanisms that automatically stop AI system operations when specific risk thresholds are exceeded.
​
Data Leakage: The unintended exposure of sensitive information through AI model outputs or behavior.
​
Data Poisoning: The intentional corruption of training data to compromise model integrity, often to install backdoors or degrade performance.
​
Differential Privacy – Differential privacy is a mathematically rigorous framework for releasing statistical information about datasets while protecting the privacy of individual data subjects. It enables a data holder to share aggregate group patterns while limiting the information leaked about specific individuals.
​
Embeddings: Dense vector representations of data (such as text, images, etc.) that capture semantic meaning within a high-dimensional space.
​
Explainability in AI refers to an AI system’s ability to provide reasons for its decisions and predictions that humans can understand, offering insights into how the system operates internally.
​
Explainable AI (XAI): AI systems designed to offer human-understandable explanations for their decisions and behaviors using various techniques and frameworks.
​
Federated Learning: A machine learning method where models are trained across multiple decentralized devices that hold local data samples, without sharing the data itself.
​
Guardrails: Constraints implemented to prevent AI systems from generating harmful, biased, or otherwise undesirable outputs.
​
Hallucination – An AI hallucination refers to a phenomenon in which an AI model produces incorrect or misleading information that is not based on its training data or factual reality.
​
Human-in-the-Loop (HITL): Systems designed to require human oversight, verification, or intervention at critical decision points.
​
Infrastructure as Code (IaC): Managing and provisioning infrastructure through code rather than manual processes, enabling security scanning and consistent deployments.
​
Jailbreak: Techniques used to bypass safety measures in AI systems, especially in large language models, to generate prohibited content.
​
Least Privilege: The security principle of granting users and processes only the minimum necessary access rights.
​
LIME (Local Interpretable Model-agnostic Explanations): A technique to explain the predictions of any machine learning classifier by locally approximating it with an interpretable model.
​
Membership Inference Attack: An attack that seeks to determine whether a particular data point was included in the training of a machine learning model.
​
MITRE ATLAS: Adversarial Threat Landscape for Artificial Intelligence Systems; a knowledge base of adversarial tactics and techniques targeting AI systems.
​
Model Card – A model card is a document that provides standardized information about an AI model's performance, limitations, intended uses, and ethical considerations to promote transparency and responsible AI development.
​
Model Extraction: An attack in which an adversary repeatedly queries a target model to create an unauthorized, functionally similar copy.
​
Model Inversion: An attack that tries to reconstruct training data by analyzing the outputs of a model.
​
Model Lifecycle Management – AI Model Lifecycle Management is the process of overseeing all phases of an AI model's existence, including its design, development, deployment, monitoring, maintenance, and eventual retirement, to ensure it remains effective and aligned with its objectives.
​
Model Poisoning: Introducing vulnerabilities or backdoors directly into a model during the training process.
​
Model Stealing/Theft: Obtaining a copy or approximation of a proprietary model by making repeated queries.
​
Multi-agent System: A system composed of multiple interacting AI agents, each potentially having different capabilities and goals.
​
OPA (Open Policy Agent): An open-source policy engine that enables unified policy enforcement across the stack.
​
Privacy-Preserving Machine Learning (PPML): Techniques and methods for training and deploying ML models while protecting the privacy of the training data.
​
Prompt Injection: An attack in which harmful instructions are embedded in inputs to override a model's intended behavior.
​
RAG (Retrieval-Augmented Generation): A technique that improves large language models by retrieving relevant information from external knowledge sources prior to generating a response.
​
Red-Teaming: The practice of actively testing AI systems by simulating adversarial attacks to identify vulnerabilities.
​
SBOM (Software Bill of Materials): A formal record that includes the details and supply chain relationships of the various components used in developing software or AI models.
​
SHAP (SHapley Additive exPlanations): A game-theoretic approach to explain the output of any machine learning model by calculating the contribution of each feature to the prediction.
​
Supply Chain Attack: Compromising a system by targeting less secure elements in its supply chain, such as third-party libraries, datasets, or pre-trained models.
​
Transfer Learning: A technique in which a model developed for one task is reused as the foundation for a model on a second task.
​
Vector Database: A specialized database designed to store high-dimensional vectors (embeddings) and perform efficient similarity searches.
​
Vulnerability Scanning: Automated tools that detect known security vulnerabilities in software components, including AI frameworks and dependencies.
​
Watermarking: Techniques for embedding imperceptible markers in AI-generated content to trace its origin or detect AI generation.
​
Zero-Day Vulnerability: A previously unknown vulnerability that attackers can exploit before developers create and release a patch.

## Appendix B: References

### TODO

## Appendix C: AI Security Governance & Documentation

### Objective

This appendix outlines the fundamental requirements for setting up organizational structures, policies, and processes to manage AI security throughout the system lifecycle.

---

### AC.1 AI Risk Management Framework Adoption

Develop a formal framework to identify, assess, and mitigate AI-specific risks throughout the system lifecycle.

 #AC.1.1    Level: 1    Role: D/V
 Verify that an AI-specific risk assessment methodology is documented and implemented.
 #AC.1.2    Level: 2    Role: D
 Confirm that risk assessments are performed at critical stages in the AI lifecycle and before any major changes.
 #AC.1.3    Level: 3    Role: D/V
 Verify that the risk management framework aligns with established standards (e.g., NIST AI RMF).

---

### AC.2 AI Security Policy and Procedures

Establish and implement organizational standards for secure AI development, deployment, and operation.

 #AC.2.1    Level: 1    Role: D/V
 Verify that documented AI security policies are in place.
 #AC.2.2    Level: 2    Role: D
 Verify that policies are reviewed and updated at least annually and following significant changes in the threat landscape.
 #AC.2.3    Level: 3    Role: D/V
 Verify that policies address all AISVS categories and applicable regulatory requirements.

---

### AC.3 Roles & Responsibilities for AI Security

Establish clear accountability for AI security throughout the organization.

 #AC.3.1    Level: 1    Role: D/V
 Verify that the roles and responsibilities for AI security are properly documented.
 #AC.3.2    Level: 2    Role: D
 Verify that responsible individuals have the appropriate security expertise.
 #AC.3.3    Level: 3    Role: D/V
 Ensure that an AI ethics committee or governance board is established for high-risk AI systems.

---

### AC.4 Enforcement of Ethical AI Guidelines

Ensure AI systems operate in accordance with established ethical principles.

 #AC.4.1    Level: 1    Role: D/V
 Verify that ethical guidelines for AI development and deployment are in place.
 #AC.4.2    Level: 2    Role: D
 Ensure that mechanisms are in place to detect and report ethical violations.
 #AC.4.3    Level: 3    Role: D/V
 Ensure that regular ethical reviews of deployed AI systems are conducted.

---

### AC.5 AI Regulatory Compliance Monitoring

Stay informed about and comply with evolving AI regulations.

 #AC.5.1    Level: 1    Role: D/V
 Ensure that procedures are in place to identify applicable AI regulations.
 #AC.5.2    Level: 2    Role: D
 Verify that compliance with all regulatory requirements has been assessed.
 #AC.5.3    Level: 3    Role: D/V
 Ensure that regulatory changes prompt timely reviews and updates of AI systems.

### AC.6 Training Data Governance, Documentation, and Process

 #1.1.2    Level: 1    Role: D/V
 Ensure that only datasets that have been vetted for quality, representativeness, ethical sourcing, and license compliance are permitted, thereby reducing risks of poisoning, embedded bias, and intellectual property infringement.
 #1.1.5    Level: 2    Role: D/V
 Verify that labeling/annotation quality is ensured through reviewer cross-checks or consensus.
 #1.1.6    Level: 2    Role: D/V
 Verify that "data cards" or "datasheets for datasets" are maintained for significant training datasets, detailing their characteristics, motivations, composition, collection processes, preprocessing methods, and recommended or discouraged uses.
 #1.3.2    Level: 2    Role: D/V
 Verify that identified biases are mitigated through documented strategies such as rebalancing, targeted data augmentation, algorithmic adjustments (e.g., pre-processing, in-processing, post-processing techniques), or reweighting, and assess the impact of mitigation on both fairness and overall model performance.
 #1.3.3    Level: 2    Role: D/V
 Verify that post-training fairness metrics have been evaluated and documented.
 #1.3.4    Level: 3    Role: D/V
 Verify that a lifecycle bias management policy designates owners and establishes a review schedule.
 #1.4.1    Level: 2    Role: D/V
 Verify that labeling and annotation quality is ensured through clear guidelines, reviewer cross-checks, consensus mechanisms (e.g., monitoring inter-annotator agreement), and established processes for resolving discrepancies.
 #1.4.4    Level: 3    Role: D/V
 Ensure that labels critical to safety, security, or fairness (e.g., identifying toxic content, critical medical findings) undergo mandatory independent dual review or an equivalent rigorous verification process.
 #1.4.6    Level: 2    Role: D/V
 Ensure that labeling guides and instructions are comprehensive, version-controlled, and peer-reviewed.
 #1.4.6    Level: 2    Role: D/V
 Ensure that data schemas for labels are clearly defined and version-controlled.
 #1.3.1    Level: 1    Role: D/V
 Ensure that datasets are analyzed for representational imbalance and potential biases across legally protected attributes (e.g., race, gender, age) and other ethically sensitive characteristics relevant to the model's application domain (e.g., socio-economic status, location).
 #1.5.3    Level: 2    Role: V
 Confirm that manual spot-checks conducted by domain experts cover a statistically significant sample (e.g., ≥1% or 1,000 samples, whichever is greater, or as determined by risk assessment) to detect subtle quality issues not identified by automation.
 #1.8.4    Level: 2    Role: D/V
 Verify that outsourced or crowdsourced labeling workflows incorporate technical and procedural safeguards to ensure data confidentiality, integrity, label quality, and prevent data leakage.
 #1.5.4    Level: 2    Role: D/V
 Verify that the remediation steps are appended to the provenance records.
 #1.6.2    Level: 2    Role: D/V
 Verify that flagged samples initiate a manual review before training.
 #1.6.3    Level: 2    Role: V
 Ensure that the results update the model's security dossier and support continuous threat intelligence.
 #1.6.4    Level: 3    Role: D/V
 Verify that the detection logic has been refreshed with new threat intelligence.
 #1.6.5    Level: 3    Role: D/V
 Ensure that online learning pipelines monitor for distribution drift.
 #1.7.1    Level: 1    Role: D/V
 Verify that training data deletion workflows remove both primary and derived data, evaluate the impact on models, and ensure that any effects on affected models are assessed and, if necessary, addressed (e.g., through retraining or recalibration).
 #1.7.2    Level: 2    Role: D
 Ensure that mechanisms are in place to track and respect the scope and status of user consent (including withdrawals) for data used in training, and that consent is validated before incorporating data into new training processes or significant model updates.
 #1.7.3    Level: 2    Role: V
 Verify that workflows are tested annually and documented.
 #1.8.1    Level: 2    Role: D/V
 Verify that third-party data suppliers, including providers of pre-trained models and external datasets, undergo security, privacy, ethical sourcing, and data quality due diligence before integrating their data or models.
 #1.8.2    Level: 1    Role: D
 Verify that external transfers use TLS/authentication and integrity checks.
 #1.8.3    Level: 2    Role: D/V
 Ensure that high-risk data sources (e.g., open-source datasets with unknown provenance, unvetted suppliers) undergo enhanced scrutiny, including sandboxed analysis, thorough quality and bias checks, and targeted poisoning detection, before being used in sensitive applications.
 #1.8.4    Level: 3    Role: D/V
 Verify that pre-trained models obtained from third parties are evaluated for embedded biases, potential backdoors, the integrity of their architecture, and the provenance of their original training data before fine-tuning or deployment.
 #1.5.3    Level: 2    Role: D/V
 Verify that when adversarial training is used, the generation, management, and versioning of adversarial datasets are properly documented and controlled.
 #1.5.3    Level: 3    Role: D/V
 Ensure that the effects of adversarial robustness training on model performance—against both clean and adversarial inputs—as well as on fairness metrics, are evaluated, documented, and continuously monitored.
 #1.5.4    Level: 3    Role: D/V
 Ensure that strategies for adversarial training and robustness are regularly reviewed and updated to address evolving adversarial attack techniques.
 #1.4.2    Level: 2    Role: D/V
 Verify that failed datasets are quarantined with audit trails.
 #1.4.3    Level: 2    Role: D/V
 Ensure that quality gates block subpar datasets unless exceptions have been approved.
 #1.11.2    Level: 2    Role: D/V
 Verify that the generation process, parameters, and intended use of synthetic data are thoroughly documented.
 #1.11.3    Level: 2    Role: D/V
 Ensure that synthetic data undergoes a risk assessment for bias, privacy leakage, and representational issues before being used in training.
 #1.12.3    Level: 2    Role: D/V
 Verify that alerts are generated for suspicious access events and investigated promptly.
 #1.13.1    Level: 1    Role: D/V
 Ensure that explicit retention periods are defined for all training datasets.
 #1.13.2    Level: 2    Role: D/V
 Verify that datasets are automatically expired, deleted, or reviewed for deletion at the end of their lifecycle.
 #1.13.3    Level: 2    Role: D/V
 Ensure that retention and deletion actions are logged and can be audited.
 #1.14.1    Level: 2    Role: D/V
 Ensure that data residency and cross-border transfer requirements are identified and enforced for all datasets.
 #1.14.2    Level: 2    Role: D/V
 Ensure that sector-specific regulations (e.g., healthcare, finance) are identified and addressed in data handling.
 #1.14.3    Level: 2    Role: D/V
 Ensure that compliance with relevant privacy laws (e.g., GDPR, CCPA) is documented and reviewed regularly.
 #1.16.1    Level: 2    Role: D/V
 Verify that mechanisms are in place to respond to data subject requests for access, rectification, restriction, or objection.
 #1.16.2    Level: 2    Role: D/V
 Ensure that requests are logged, tracked, and completed within legally required timeframes.
 #1.16.3    Level: 2    Role: D/V
 Verify that data subject rights processes are regularly tested and reviewed for effectiveness.
 #1.17.1    Level: 2    Role: D/V
 Ensure that an impact analysis is conducted before updating or replacing a dataset version, addressing model performance, fairness, and compliance.
 #1.17.2    Level: 2    Role: D/V
 Ensure that the results of the impact analysis are documented and reviewed by the appropriate stakeholders.
 #1.17.3    Level: 2    Role: D/V
 Confirm that rollback plans are in place in case new versions introduce unacceptable risks or regressions.
 #1.18.1    Level: 2    Role: D/V
 Ensure that all personnel involved in data annotation have undergone background checks and are trained in data security and privacy.
 #1.18.2    Level: 2    Role: D/V
 Ensure that all annotation personnel sign confidentiality and non-disclosure agreements.
 #1.18.3    Level: 2    Role: D/V
 Verify that annotation platforms enforce access controls and monitor for insider threats.

#### References

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Appendix D: AI-Assisted Secure Coding Governance and Verification

### Objective

This chapter establishes baseline organizational controls for the safe and effective use of AI-assisted coding tools during software development, ensuring security and traceability throughout the SDLC.

---

### AD.1 AI-Assisted Secure-Coding Workflow

Integrate AI tools into the organization's secure software development lifecycle (SSDLC) without compromising existing security controls.

 #AD.1.1    Level: 1    Role: D/V
 Ensure that a documented workflow specifies when and how AI tools can generate, refactor, or review code.
 #AD.1.2    Level: 2    Role: D
 Verify that the workflow corresponds to each SSDLC phase (design, implementation, code review, testing, deployment).
 #AD.1.3    Level: 3    Role: D/V
 Verify that metrics (e.g., vulnerability density, mean time to detect) are collected on AI-generated code and compared to human-only baselines.

---

### AD.2 AI Tool Qualification & Threat Modeling

Ensure AI coding tools are evaluated for security capabilities, risks, and supply-chain impact before adoption.

 #AD.2.1    Level: 1    Role: D/V
 Ensure that the threat model for each AI tool identifies risks related to misuse, model inversion, data leakage, and dependency-chain vulnerabilities.
 #AD.2.2    Level: 2    Role: D
 Verify that tool evaluations include static and dynamic analysis of any local components as well as assessment of SaaS endpoints, including TLS, authentication/authorization, and logging.
 #AD.2.3    Level: 3    Role: D/V
 Verify that evaluations adhere to a recognized framework and are re-performed after major version changes.

---

### AD.3 Secure Prompt & Context Management

Prevent the leakage of secrets, proprietary code, and personal data when creating prompts or contexts for AI models.

 #AD.3.1    Level: 1    Role: D/V
 Ensure that written guidelines explicitly prohibit including secrets, credentials, or classified information in prompts.
 #AD.3.2    Level: 2    Role: D
 Verify that technical controls (client-side redaction, approved context filters) automatically remove sensitive artifacts.
 #AD.3.3    Level: 3    Role: D/V
 Verify that prompts and responses are tokenized, encrypted both in transit and at rest, and that retention periods comply with the data classification policy.

---

### AD.4 Validation of AI-Generated Code

Identify and fix vulnerabilities introduced by AI-generated output before the code is merged or deployed.

 #AD.4.1    Level: 1    Role: D/V
 Ensure that AI-generated code always undergoes human code review.
 #AD.4.2    Level: 2    Role: D
 Ensure that automated scanners (SAST/IAST/DAST) run on every pull request containing AI-generated code and block merges if critical issues are detected.
 #AD.4.3    Level: 3    Role: D/V
 Verify that differential fuzz testing or property-based tests demonstrate security-critical behaviors (e.g., input validation, authorization logic).

---

### AD.5 Explainability and Traceability of Code Suggestions

Provide auditors and developers with insight into why a suggestion was made and how it developed.

 #AD.5.1    Level: 1    Role: D/V
 Verify that prompt/response pairs are logged with commit IDs.
 #AD.5.2    Level: 2    Role: D
 Verify that developers can display model citations (training snippets, documentation) supporting a suggestion.
 #AD.5.3    Level: 3    Role: D/V
 Ensure that explainability reports are stored alongside design artifacts and referenced in security reviews, meeting ISO/IEC 42001 traceability requirements.

---

### AD.6 Continuous Feedback and Model Fine-Tuning

Enhance model security performance over time while preventing negative drift.

 #AD.6.1    Level: 1    Role: D/V
 Verify that developers can mark insecure or non-compliant suggestions and that these flags are recorded.
 #AD.6.2    Level: 2    Role: D
 Ensure that aggregated feedback guides periodic fine-tuning or retrieval-augmented generation using vetted secure-coding corpora (e.g., OWASP Cheat Sheets).
 #AD.6.3    Level: 3    Role: D/V
 Verify that a closed-loop evaluation harness runs regression tests after every fine-tuning; security metrics must meet or exceed previous baselines before deployment.

---

#### References

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Appendix E: Sample Tools and Frameworks

### Objective

This chapter provides examples of tools and frameworks that can assist in implementing or meeting a specific AISVS requirement. These examples should not be considered recommendations or endorsements by the AISVS team or the OWASP GenAI Security Project.

---

### AE.1 Training Data Governance and Bias Management

Tools used for data analytics, governance, and bias management.

 #AE.1.1    Section: 1.1
 Data Inventory Tooling: Tools for managing data inventory such as...
 #AE.1.2    Section: 1.2
 Encryption In Transit Use TLS for HTTPS-based applications, with tools like OpenSSL and Python's`ssl`library.

---

### AE.2 User Input Validation

Tooling to handle and validate user inputs.

 #AE.2.1    Section: 2.1
 Prompt Injection Defense Tooling: Use guardrail tools like NVIDIA's NeMo or Guardrails AI.

---

