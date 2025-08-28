## Frontispiece

### About the Standard

The Artificial Intelligence Security Verification Standard (AISVS) is a community-driven catalog of security requirements that data scientists, MLOps engineers, software architects, developers, testers, security professionals, tool vendors, regulators, and consumers can use to design, build, test, and verify trustworthy AI-enabled systems and applications. It provides a common language for specifying security controls across the AI lifecycle—from data collection and model development to deployment and ongoing monitoring—enabling organizations to measure and enhance the resilience, privacy, and safety of their AI solutions.

### Copyright and License

Version 0.1 (First Public Draft - Work In Progress), 2025  

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

AISVS is a brand-new standard specifically designed to address the unique security challenges of artificial intelligence systems. While it draws inspiration from broader security best practices, every requirement in AISVS has been developed from the ground up to reflect the AI threat landscape and to help organizations build safer, more resilient AI solutions.

## Preface

Welcome to version 1.0 of the Artificial Intelligence Security Verification Standard (AISVS)!

### Introduction

Established in 2025 through a collaborative community effort, AISVS defines the security requirements to consider when designing, developing, deploying, and operating modern AI models, pipelines, and AI-enabled services.

AISVS v1.0 represents the combined efforts of its project leads, working group, and broader community contributors to create a practical, testable baseline for securing AI systems.

Our goal with this release is to make AISVS easy to adopt while remaining sharply focused on its defined scope and addressing the rapidly evolving risk landscape unique to AI.

### Key Objectives for AISVS Version 1.0

Version 1.0 will be developed following several guiding principles.

#### Well-Defined Scope

Each requirement must align with AISVS’s name and mission:

Artificial Intelligence – Controls function at the AI/ML layer (data, model, pipeline, or inference) and are the responsibility of AI practitioners.
Security – Requirements directly address identified security, privacy, or safety risks.
Verification – Language is written so that conformance can be objectively validated.
Standard – Sections follow a consistent structure and terminology to create a coherent reference.
​
---

By following AISVS, organizations can systematically evaluate and enhance the security posture of their AI solutions, promoting a culture of secure AI engineering.

## Using the AISVS

The Artificial Intelligence Security Verification Standard (AISVS) defines security requirements for modern AI applications and services, focusing on the aspects under the control of application developers.

The AISVS is designed for anyone involved in developing or assessing the security of AI applications, including developers, architects, security engineers, and auditors. This chapter introduces the structure and usage of the AISVS, covering its verification levels and intended use cases.

### Artificial Intelligence Security Verification Levels

The AISVS defines three ascending levels of security verification. Each level increases in depth and complexity, allowing organizations to tailor their security posture according to the risk level of their AI systems.

Organizations may start at Level 1 and gradually advance to higher levels as their security maturity and exposure to threats increase.

#### Definition of the Levels

Each requirement in AISVS v1.0 is assigned to one of the following levels:

 Level 1 requirements

Level 1 includes the most critical and foundational security requirements. These focus on preventing common attacks that do not depend on other preconditions or vulnerabilities. Most Level 1 controls are either straightforward to implement or essential enough to warrant the effort.

 Level 2 requirements

Level 2 addresses more advanced or less common attacks, as well as layered defenses against widespread threats. These requirements may involve more complex logic or target specific prerequisites of attacks.

 Level 3 requirements

Level 3 includes controls that are generally more difficult to implement or applicable in specific situations. These often represent defense-in-depth strategies or mitigations against niche, targeted, or highly complex attacks.

#### Role (D/V)

Each AISVS requirement is labeled according to the primary audience:

D – Developer-focused requirements
V – Requirements focused on the verifier/auditor
D/V – Relevant to both developers and verifiers

## C1 Training Data Governance & Bias Management

### Control Objective

Training data must be sourced, handled, and maintained in a manner that preserves provenance, security, quality, and fairness. Doing so fulfills legal obligations and reduces the risks of bias, poisoning, or privacy breaches during training that could affect the entire AI lifecycle.

---

### C1.1 Training Data Provenance

Maintain a verifiable inventory of all datasets, accept only trusted sources, and log every change for audit purposes.

 #1.1.1    Level: 1    Role: D/V
 Ensure that an up-to-date inventory of every training data source—including origin, steward/owner, license, collection method, intended use constraints, and processing history—is maintained.
 #1.1.2    Level: 1    Role: D/V
 Ensure that training data processes exclude unnecessary features, attributes, or fields (e.g., unused metadata, sensitive PII, leaked test data).
 #1.1.3    Level: 2    Role: D/V
 Ensure that all dataset changes undergo a logged approval workflow.
 #1.1.4    Level: 3    Role: D/V
 Verify that datasets or subsets are watermarked or fingerprinted whenever feasible.

---

### C1.2 Training Data Security and Integrity

Restrict access to training data, encrypt it both at rest and during transit, and verify its integrity to prevent tampering, theft, or data poisoning.

 #1.2.1    Level: 1    Role: D/V
 Verify that access controls safeguard training data storage and pipelines.
 #1.2.2    Level: 2    Role: D/V
 Ensure that all access to training data is logged, including the user, time, and action.
 #1.2.3    Level: 2    Role: D/V
 Verify that training datasets are encrypted both in transit and at rest, using industry-standard cryptographic algorithms and key management practices.
 #1.2.4    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are used to ensure data integrity during the storage and transfer of training data.
 #1.2.5    Level: 2    Role: D/V
 Verify that automated detection techniques are applied to prevent unauthorized modifications or corruption of training data.
 #1.2.6    Level: 2    Role: D/V
 Ensure that outdated training data is securely deleted or anonymized.
 #1.2.7    Level: 3    Role: D/V
 Ensure that all training dataset versions are uniquely identified, stored immutably, and are auditable to support rollback and forensic analysis.

---

### C1.3 Quality, Integrity, and Security of Training Data Labeling

Protect labels and require technical review for critical data.

 #1.3.1    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are applied to label artifacts to ensure their integrity and authenticity.
 #1.3.2    Level: 2    Role: D/V
 Ensure that labeling interfaces and platforms enforce robust access controls, maintain tamper-evident audit logs of all labeling activities, and safeguard against unauthorized modifications.
 #1.3.3    Level: 3    Role: D/V
 Verify that sensitive information in labels is redacted, anonymized, or encrypted at the data field level both at rest and in transit.

---

### C1.4 Training Data Quality and Security Assurance

Combine automated validation, manual spot checks, and logged remediation to ensure dataset reliability.

 #1.4.1    Level: 1    Role: D
 Verify that automated tests catch format errors and nulls on every ingestion or significant data transformation.
 #1.4.2    Level: 2    Role: D/V
 Verify that LLM training and fine-tuning pipelines implement poisoning detection and data integrity validation (e.g., statistical methods, outlier detection, embedding analysis) to identify potential poisoning attacks (e.g., label flipping, backdoor trigger insertion, role-switching commands, influential instance attacks) or unintentional data corruption in the training data.
 #1.4.3    Level: 3    Role: D/V
 Verify that suitable defenses, such as adversarial training (using generated adversarial examples), data augmentation with perturbed inputs, or robust optimization techniques, are implemented and properly tuned for relevant models based on risk assessment.
 #1.4.4    Level: 2    Role: D/V
 Ensure that automatically generated labels (e.g., through LLMs or weak supervision) are subjected to confidence thresholds and consistency checks to identify hallucinated, misleading, or low-confidence labels.
 #1.4.5    Level: 3    Role: D
 Verify that automated tests detect label skews during every data ingestion or major data transformation.

---

### C1.5 Data Lineage and Traceability

Track the entire journey of each data point from its source to the model input for auditability and incident response.

 #1.5.1    Level: 2    Role: D/V
 Verify that the lineage of each data point, including all transformations, augmentations, and merges, is documented and can be reconstructed.
 #1.5.2    Level: 2    Role: D/V
 Verify that lineage records are immutable, securely stored, and accessible for audits.
 #1.5.3    Level: 2    Role: D/V
 Ensure that lineage tracking includes synthetic data generated through privacy-preserving or generative methods, and that all synthetic data is clearly labeled and distinguishable from real data throughout the entire pipeline.

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

Robust validation of user input is a first line of defense against some of the most damaging attacks on AI systems. Prompt injection attacks can override system instructions, leak sensitive data, or steer the model toward prohibited behavior. Unless dedicated filters and instruction hierarchies are in place, research shows that "multi-shot" jailbreaks exploiting very long context windows will be effective. Additionally, subtle adversarial perturbation attacks—such as homoglyph swaps or leetspeak—can silently alter a model's decisions.

---

### C2.1 Prompt Injection Defense

Prompt injection is one of the top risks for AI systems. Defenses against this tactic use a combination of static pattern filters, dynamic classifiers, and instruction hierarchy enforcement.

 #2.1.1    Level: 1    Role: D/V
 Verify that user inputs are screened against a continuously updated library of known prompt injection patterns, including jailbreak keywords, "ignore previous," role-play chains, and indirect HTML/URL attacks.
 #2.1.2    Level: 1    Role: D/V
 Verify that the system enforces an instruction hierarchy where system or developer messages override user instructions, even after the context window expands.
 #2.1.3    Level: 2    Role: D/V
 Ensure that adversarial evaluation tests (e.g., Red Team "many-shot" prompts) are conducted before every model or prompt-template release, with defined success-rate thresholds and automated blockers to prevent regressions.
 #2.1.4    Level: 2    Role: D
 Ensure that prompts sourced from third-party content (web pages, PDFs, emails) are sanitized within an isolated parsing environment before being concatenated into the main prompt.
 #2.1.5    Level: 3    Role: D/V
 Ensure that all updates to prompt-filter rules, classifier model versions, and block-list changes are version-controlled and auditable.

---

### C2.2 Resistance to Adversarial Examples

Natural Language Processing (NLP) models remain vulnerable to subtle character- or word-level perturbations that humans often overlook but cause models to misclassify.

 #2.2.1    Level: 1    Role: D
 Ensure that basic input normalization steps (Unicode NFC, homoglyph mapping, whitespace trimming) are performed before tokenization.
 #2.2.2    Level: 2    Role: D/V
 Verify that statistical anomaly detection identifies inputs with unusually high edit distances from language norms, excessive repeated tokens, or abnormal embedding distances.
 #2.2.3    Level: 2    Role: D
 Verify that the inference pipeline supports optional adversarial-training-hardened model variants or defense layers (e.g., randomization, defensive distillation) for high-risk endpoints.
 #2.2.4    Level: 2    Role: V
 Ensure that suspected adversarial inputs are quarantined and logged with full payloads (after redacting PII).
 #2.2.5    Level: 3    Role: D/V
 Ensure that robustness metrics (success rates of known attack suites) are monitored over time and that regressions trigger a release blocker.

---

### C2.3 Schema, Type, and Length Validation

AI attacks involving malformed or oversized inputs can lead to parsing errors, prompt spillage across fields, and resource exhaustion. Strict schema enforcement is also essential when executing deterministic tool calls.

 #2.3.1    Level: 1    Role: D
 Ensure that every API or function call endpoint specifies an explicit input schema (such as JSON Schema, Protobuf, or a multimodal equivalent) and that inputs are validated before assembling the prompt.
 #2.3.2    Level: 1    Role: D/V
 Ensure that inputs exceeding the maximum token or byte limits are rejected with a clear error message and are never silently truncated.
 #2.3.3    Level: 2    Role: D/V
 Ensure that type checks (such as numeric ranges, enum values, and MIME types for images/audio) are enforced on the server side, not just in client code.
 #2.3.4    Level: 2    Role: D
 Ensure that semantic validators (e.g., JSON Schema) operate in constant time to prevent algorithmic DoS attacks.
 #2.3.5    Level: 3    Role: V
 Ensure that validation failures are logged with redacted payload snippets and clear error codes to support security triage.

---

### C2.4 Content and Policy Screening

Developers should be able to detect syntactically valid prompts that request disallowed content (such as illicit instructions, hate speech, or copyrighted text) and prevent them from spreading.

 #2.4.1    Level: 1    Role: D
 Verify that a content classifier (zero-shot or fine-tuned) scores every input for violence, self-harm, hate speech, sexual content, and illegal requests, with configurable thresholds.
 #2.4.2    Level: 1    Role: D/V
 Ensure that inputs violating policies receive standardized refusals or safe completions to prevent propagation to downstream LLM calls.
 #2.4.3    Level: 2    Role: D
 Verify that the screening model or rule set is retrained or updated at least quarterly, incorporating newly observed jailbreak or policy bypass patterns.
 #2.4.4    Level: 2    Role: D
 Ensure that screening complies with user-specific policies (age, regional legal constraints) through attribute-based rules evaluated at the time of the request.
 #2.4.5    Level: 3    Role: V
 Verify that screening logs include classifier confidence scores and policy category tags for SOC correlation and future red team replay.

---

### C2.5 Input Rate Limiting and Abuse Prevention

Developers should prevent abuse, resource exhaustion, and automated attacks on AI systems by limiting input rates and detecting unusual usage patterns.

 #2.5.1    Level: 1    Role: D/V
 Verify that rate limits per user, per IP, and per API key are enforced for all input endpoints.
 #2.5.2    Level: 2    Role: D/V
 Ensure that burst and sustained rate limits are properly configured to prevent DoS and brute force attacks.
 #2.5.3    Level: 2    Role: D/V
 Verify that abnormal usage patterns (e.g., rapid-fire requests, input flooding) trigger automated blocks or escalations.
 #2.5.4    Level: 3    Role: V
 Verify that abuse prevention logs are retained and reviewed for emerging attack patterns.

---

### C2.6 Multi-Modal Input Validation

 AI systems should incorporate robust validation for non-text inputs (such as images, audio, and files) to prevent injection attacks, evasion tactics, or resource abuse.

 #2.6.1    Level: 1    Role: D
 Verify that all non-text inputs (images, audio, files) are validated for type, size, and format before processing.
 #2.6.2    Level: 2    Role: D/V
 Verify that files are scanned for malware and steganographic payloads before ingestion.
 #2.6.3    Level: 2    Role: D/V
 Verify that image and audio inputs are checked for adversarial perturbations or known attack patterns.
 #2.6.4    Level: 3    Role: V
 Verify that multi-modal input validation failures are logged and trigger alerts for investigation.

---

### C2.7 Input Provenance & Attribution

AI systems should support auditing, abuse tracking, and compliance by monitoring and tagging the sources of all user inputs.

 #2.7.1    Level: 1    Role: D/V
 Verify that all user inputs are tagged with metadata (user ID, session, source, timestamp, IP address) upon ingestion.
 #2.7.2    Level: 2    Role: D/V
 Ensure that provenance metadata is retained and can be audited for all processed inputs.
 #2.7.3    Level: 2    Role: D/V
 Ensure that anomalous or untrusted input sources are flagged and subjected to enhanced scrutiny or blocking.

---

### C2.8 Real-Time Adaptive Threat Detection

Developers should use advanced AI threat detection systems that adapt to new attack patterns and offer real-time protection through compiled pattern matching.

 #2.8.1    Level: 1    Role: D/V
 Verify that threat detection patterns are compiled into optimized regex engines to ensure high-performance real-time filtering with minimal latency impact.
 #2.8.2    Level: 1    Role: D/V
 Verify that threat detection systems maintain separate pattern libraries for different threat categories such as prompt injection, harmful content, sensitive data, and system commands.
 #2.8.3    Level: 2    Role: D/V
 Verify that adaptive threat detection includes machine learning models that adjust threat sensitivity based on attack frequency and success rates.
 #2.8.4    Level: 2    Role: D/V
 Verify that real-time threat intelligence feeds automatically update pattern libraries with new attack signatures and Indicators of Compromise (IOCs).
 #2.8.5    Level: 3    Role: D/V
 Ensure that threat detection false positive rates are continuously monitored and that pattern specificity is automatically adjusted to minimize interference with legitimate use cases.
 #2.8.6    Level: 3    Role: D/V
 Verify that contextual threat analysis takes into account the input source, user behavior patterns, and session history to enhance detection accuracy.
 #2.8.7    Level: 3    Role: D/V
 Ensure that threat detection performance metrics (detection rate, processing latency, resource utilization) are continuously monitored and optimized in real time.

---

### C2.9 Multi-Modal Security Validation Pipeline

Developers should ensure security validation for text, image, audio, and other AI input modalities by implementing specific types of threat detection and resource isolation.

 #2.9.1    Level: 1    Role: D/V
 Verify that each input modality has dedicated security validators with documented threat patterns (text: prompt injection, images: steganography, audio: spectrogram attacks) and specified detection thresholds.
 #2.9.2    Level: 2    Role: D/V
 Verify that multi-modal inputs are processed within isolated sandboxes that have defined resource limits (memory, CPU, processing time) specific to each modality type, as documented in security policies.
 #2.9.3    Level: 2    Role: D/V
 Ensure that cross-modal attack detection identifies coordinated attacks across multiple input types (e.g., steganographic payloads in images combined with prompt injection in text) using correlation rules and alert generation.
 #2.9.4    Level: 3    Role: D/V
 Verify that multi-modal validation failures trigger detailed logging, including all input modalities, validation results, threat scores, and correlation analysis, using structured log formats for SIEM integration.
 #2.9.5    Level: 3    Role: D/V
 Verify that modality-specific content classifiers are updated according to documented schedules (at least quarterly) with new threat patterns, adversarial examples, and performance benchmarks maintained above baseline thresholds.

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

AI systems must implement change control processes that prevent unauthorized or unsafe model modifications from reaching production. This control ensures model integrity throughout the entire lifecycle—from development through deployment to decommissioning—enabling rapid incident response and maintaining accountability for all changes.

Core Security Goal: Ensure that only authorized and validated models reach production by using controlled processes that maintain integrity, traceability, and recoverability.

---

### C3.1 Model Authorization and Integrity

Only authorized models with verified integrity are deployed to production environments.

 #3.1.1    Level: 1    Role: D/V
 Verify that all model artifacts (weights, configurations, tokenizers) are cryptographically signed by authorized entities before deployment.
 #3.1.2    Level: 1    Role: D/V
 Ensure that model integrity is validated during deployment and that signature verification failures prevent the model from loading.
 #3.1.3    Level: 2    Role: D/V
 Verify that model provenance records include the identity of the authorizing entity, training data checksums, validation test results with pass/fail status, and a creation timestamp.
 #3.1.4    Level: 2    Role: D/V
 Ensure that all model artifacts follow semantic versioning (MAJOR.MINOR.PATCH) with clearly documented criteria detailing when each version component should be incremented.
 #3.1.5    Level: 2    Role: V
 Verify that dependency tracking maintains an up-to-date inventory that allows for the rapid identification of all consuming systems.

---

### C3.2 Model Validation & Testing

Models must pass defined security and safety validations before deployment.

 #3.2.1    Level: 1    Role: D/V
 Ensure that models undergo automated security testing, including input validation, output sanitization, and safety evaluations, with pre-agreed organizational pass/fail criteria before deployment.
 #3.2.2    Level: 1    Role: D/V
 Verify that validation failures automatically block model deployment unless there is explicit override approval from pre-designated authorized personnel with documented business justifications.
 #3.2.3    Level: 2    Role: V
 Verify that test results are cryptographically signed and immutably linked to the specific model version hash being validated.
 #3.2.4    Level: 2    Role: D/V
 Verify that emergency deployments require a documented security risk assessment and approval from a pre-designated security authority within pre-agreed timeframes.

---

### C3.3 Controlled Deployment and Rollback

Model deployments must be controlled, monitored, and reversible.

 #3.3.1    Level: 1    Role: D
 Verify that production deployments use gradual rollout mechanisms (such as canary deployments and blue-green deployments) with automated rollback triggers based on predetermined error rates, latency thresholds, or security alert criteria.
 #3.3.2    Level: 1    Role: D/V
 Verify that rollback capabilities restore the complete model state—including weights, configurations, and dependencies—atomically within predefined organizational time windows.
 #3.3.3    Level: 2    Role: D/V
 Ensure that deployment processes validate cryptographic signatures and compute integrity checksums before model activation, and that deployment fails if any mismatch is detected.
 #3.3.4    Level: 2    Role: D/V
 Verify that emergency model shutdown capabilities can disable model endpoints within predefined response times through automated circuit breakers or manual kill switches.
 #3.3.5    Level: 2    Role: V
 Ensure that rollback artifacts (previous model versions, configurations, dependencies) are retained in accordance with organizational policies using immutable storage for incident response.

---

### C3.4 Change Accountability and Audit

All changes in the model lifecycle must be traceable and auditable.

 #3.4.1    Level: 1    Role: V
 Ensure that all model changes (deployment, configuration, retirement) produce immutable audit records containing a timestamp, an authenticated actor identity, a change type, and the states before and after the change.
 #3.4.2    Level: 2    Role: D/V
 Verify that access to the audit log requires proper authorization and that all access attempts are recorded with the user's identity and a timestamp.
 #3.4.3    Level: 2    Role: D/V
 Ensure that prompt templates and system messages are version-controlled in git repositories, requiring mandatory code review and approval from designated reviewers before deployment.
 #3.4.4    Level: 2    Role: V
 Verify that audit records contain sufficient detail (model hashes, configuration snapshots, dependency versions) to allow complete reconstruction of the model state at any timestamp within the retention period.

---

### C3.5 Secure Development Practices

Model development and training processes must adhere to secure practices to prevent compromise.

 #3.5.1    Level: 1    Role: D
 Verify that the model development, testing, and production environments are physically or logically separated. They should have no shared infrastructure, distinct access controls, and isolated data storage.
 #3.5.2    Level: 1    Role: D
 Ensure that model training and fine-tuning take place in isolated environments with restricted network access.
 #3.5.3    Level: 1    Role: D/V
 Verify that training data sources are validated through integrity checks and authenticated by trusted sources with a documented chain of custody before being used in model development.
 #3.5.4    Level: 2    Role: D
 Verify that model development artifacts (such as hyperparameters, training scripts, and configuration files) are stored in version control and require peer review approval before being used in training.

---

### C3.6 Model Retirement & Decommissioning

Models must be securely retired when they are no longer needed or when security issues are detected.

 #3.6.1    Level: 1    Role: D
 Verify that model retirement processes automatically scan dependency graphs, identify all dependent systems, and provide pre-agreed advance notice periods before decommissioning.
 #3.6.2    Level: 1    Role: D/V
 Verify that retired model artifacts are securely erased using cryptographic erasure or multi-pass overwriting in accordance with documented data retention policies, accompanied by verified destruction certificates.
 #3.6.3    Level: 2    Role: V
 Verify that model retirement events are logged with a timestamp and actor identity, and that model signatures are revoked to prevent reuse.
 #3.6.4    Level: 2    Role: D/V
 Verify that emergency model retirement can disable model access within pre-established emergency response timeframes using automated kill switches if critical security vulnerabilities are discovered.

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

AI infrastructure must be strengthened against privilege escalation, supply chain tampering, and lateral movement by implementing secure configurations, runtime isolation, trusted deployment pipelines, and comprehensive monitoring. Only authorized and validated infrastructure components and configurations should reach production through controlled processes that ensure security, integrity, and auditability.

Core Security Goal: Only cryptographically signed, vulnerability-scanned infrastructure components are deployed to production through automated validation pipelines that enforce security policies and maintain immutable audit trails.

---

### C4.1 Runtime Environment Isolation

Prevent container escapes and privilege escalation by using kernel-level isolation primitives and mandatory access controls.

 #4.1.1    Level: 1    Role: D/V
 Verify that all AI containers drop all Linux capabilities except for CAP_SETUID, CAP_SETGID, and any explicitly required capabilities documented in the security baselines.
 #4.1.2    Level: 1    Role: D/V
 Verify that seccomp profiles block all syscalls except those in the pre-approved allowlists, with violations terminating the container and generating security alerts.
 #4.1.3    Level: 2    Role: D/V
 Verify that AI workloads run with read-only root filesystems, tmpfs for temporary data, and named volumes for persistent data with noexec mount options enforced.
 #4.1.4    Level: 2    Role: D/V
 Verify that eBPF-based runtime monitoring (such as Falco, Tetragon, or an equivalent tool) detects privilege escalation attempts and automatically terminates offending processes within the organization's response time requirements.
 #4.1.5    Level: 3    Role: D/V
 Ensure that high-risk AI workloads run in hardware-isolated environments (Intel TXT, AMD SVM, or dedicated bare-metal nodes) with attestation verification.

---

### C4.2 Secure Build and Deployment Pipelines

Ensure cryptographic integrity and supply chain security by using reproducible builds and signed artifacts.

 #4.2.1    Level: 1    Role: D/V
 Ensure that infrastructure-as-code is scanned with tools (tfsec, Checkov, or Terrascan) on every commit, blocking merges that have CRITICAL or HIGH severity findings.
 #4.2.2    Level: 1    Role: D/V
 Ensure that container builds are reproducible with identical SHA256 hashes across builds and generate SLSA Level 3 provenance attestations signed with Sigstore.
 #4.2.3    Level: 2    Role: D/V
 Ensure that container images include embedded CycloneDX or SPDX SBOMs and are signed with Cosign before being pushed to the registry, with unsigned images rejected during deployment.
 #4.2.4    Level: 2    Role: D/V
 Verify that CI/CD pipelines use OIDC tokens from HashiCorp Vault, AWS IAM Roles, or Azure Managed Identity with lifetimes that do not exceed organizational security policy limits.
 #4.2.5    Level: 2    Role: D/V
 Verify that Cosign signatures and SLSA provenance are validated during the deployment process prior to container execution, and ensure that verification errors cause the deployment to fail.
 #4.2.6    Level: 2    Role: D/V
 Ensure that build environments run in ephemeral containers or VMs with no persistent storage and have network isolation from production VPCs.

---

### C4.3 Network Security and Access Control

Implement zero-trust networking using default-deny policies and encrypted communications.

 #4.3.1    Level: 1    Role: D/V
 Ensure that Kubernetes NetworkPolicies or any equivalent mechanism enforces default-deny ingress and egress rules, with explicit allow rules for the required ports (443, 8080, etc.).
 #4.3.2    Level: 1    Role: D/V
 Verify that SSH (port 22), RDP (port 3389), and cloud metadata endpoints (169.254.169.254) are either blocked or require certificate-based authentication.
 #4.3.3    Level: 2    Role: D/V
 Ensure that egress traffic is filtered through HTTP/HTTPS proxies (such as Squid, Istio, or cloud NAT gateways) using domain allowlists, and that blocked requests are logged.
 #4.3.4    Level: 2    Role: D/V
 Ensure that inter-service communication utilizes mutual TLS with certificates rotated in accordance with organizational policy and that certificate validation is strictly enforced (no skip-verify flags).
 #4.3.5    Level: 2    Role: D/V
 Ensure that AI infrastructure operates within dedicated VPCs/VNets without direct internet access and communicates exclusively through NAT gateways or bastion hosts.

---

### C4.4 Secrets & Cryptographic Key Management

Protect credentials using hardware-backed storage and automated rotation with zero-trust access.

 #4.4.1    Level: 1    Role: D/V
 Verify that secrets are stored in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault, or Google Secret Manager with AES-256 encryption at rest.
 #4.4.2    Level: 1    Role: D/V
 Verify that cryptographic keys are generated in FIPS 140-2 Level 2 HSMs (such as AWS CloudHSM and Azure Dedicated HSM) with key rotation performed according to the organization's cryptographic policy.
 #4.4.3    Level: 2    Role: D/V
 Ensure that secret rotation is fully automated with zero-downtime deployment and immediate rotation triggered by personnel changes or security incidents.
 #4.4.4    Level: 2    Role: D/V
 Ensure that container images are scanned using tools such as GitLeaks, TruffleHog, or detect-secrets, and block builds that contain API keys, passwords, or certificates.
 #4.4.5    Level: 2    Role: D/V
 Verify that production secret access requires MFA using hardware tokens (YubiKey, FIDO2) and is recorded in immutable audit logs with user identities and timestamps.
 #4.4.6    Level: 2    Role: D/V
 Verify that secrets are injected through Kubernetes secrets, mounted volumes, or init containers, and ensure that secrets are never embedded in environment variables or images.

---

### C4.5 AI Workload Sandboxing and Validation

Isolate untrusted AI models within secure sandboxes using comprehensive behavioral analysis.

 #4.5.1    Level: 1    Role: D/V
 Verify that external AI models run in gVisor, microVMs (such as Firecracker, CrossVM), or Docker containers using the --security-opt=no-new-privileges and --read-only flags.
 #4.5.2    Level: 1    Role: D/V
 Verify that sandbox environments have no network connectivity (--network=none) or only allow localhost access, with all external requests blocked by iptables rules.
 #4.5.3    Level: 2    Role: D/V
 Ensure that AI model validation includes automated red-team testing with organizationally defined test coverage and behavioral analysis for detecting backdoors.
 #4.5.4    Level: 2    Role: D/V
 Verify that, before an AI model is promoted to production, its sandbox results are cryptographically signed by authorized security personnel and stored in immutable audit logs.
 #4.5.5    Level: 2    Role: D/V
 Ensure that sandbox environments are destroyed and recreated from golden images between evaluations, with complete cleanup of the filesystem and memory.

---

### C4.6 Infrastructure Security Monitoring

Continuously scan and monitor infrastructure with automated remediation and real-time alerts.

 #4.6.1    Level: 1    Role: D/V
 Verify that container images are scanned according to organizational schedules, with CRITICAL vulnerabilities blocking deployment based on organizational risk thresholds.
 #4.6.2    Level: 1    Role: D/V
 Verify that infrastructure complies with CIS Benchmarks or NIST 800-53 controls according to organizationally defined compliance thresholds, with automated remediation for failed checks.
 #4.6.3    Level: 2    Role: D/V
 Verify that HIGH-severity vulnerabilities are patched according to organizational risk management timelines, with emergency procedures in place for actively exploited CVEs.
 #4.6.4    Level: 2    Role: V
 Verify that security alerts integrate with SIEM platforms (Splunk, Elastic, or Sentinel) using CEF or STIX/TAXII formats with automated enrichment.
 #4.6.5    Level: 3    Role: V
 Verify that infrastructure metrics are exported to monitoring systems (Prometheus, DataDog) with SLA dashboards and executive reports.
 #4.6.6    Level: 2    Role: D/V
 Verify that configuration drift is detected using tools (Chef InSpec, AWS Config) according to organizational monitoring requirements, with automatic rollback for unauthorized changes.

---

### C4.7 AI Infrastructure Resource Management

Prevent resource exhaustion attacks and ensure fair resource allocation by implementing quotas and monitoring.

 #4.7.1    Level: 1    Role: D/V
 Verify that GPU/TPU utilization is monitored, with alerts triggered at organizationally defined thresholds, and that automatic scaling or load balancing is activated based on capacity management policies.
 #4.7.2    Level: 1    Role: D/V
 Verify that AI workload metrics (inference latency, throughput, error rates) are collected in accordance with organizational monitoring requirements and are correlated with infrastructure utilization.
 #4.7.3    Level: 2    Role: D/V
 Verify that Kubernetes ResourceQuotas or equivalent mechanisms limit individual workloads according to organizational resource allocation policies, with hard limits enforced.
 #4.7.4    Level: 2    Role: V
 Verify that cost monitoring tracks spending per workload or tenant, with alerts triggered based on organizational budget thresholds and automated controls to prevent budget overruns.
 #4.7.5    Level: 3    Role: V
 Verify that capacity planning utilizes historical data with forecasting periods defined by the organization and includes automated resource provisioning based on demand patterns.
 #4.7.6    Level: 2    Role: D/V
 Verify that resource exhaustion triggers circuit breakers in accordance with organizational response requirements, including rate limiting based on capacity policies and workload isolation.

---

### C4.8 Environment Separation & Promotion Controls

Enforce strict environment boundaries using automated promotion gates and security validation.

 #4.8.1    Level: 1    Role: D/V
 Ensure that the development, testing, and production environments operate in separate VPCs/VNets without any shared IAM roles, security groups, or network connectivity.
 #4.8.2    Level: 1    Role: D/V
 Ensure that environment promotion requires approval from authorized personnel defined by the organization, using cryptographic signatures and immutable audit trails.
 #4.8.3    Level: 2    Role: D/V
 Verify that production environments block SSH access, disable debug endpoints, and require change requests with organizational advance notice requirements, except in emergencies.
 #4.8.4    Level: 2    Role: D/V
 Ensure that infrastructure-as-code changes undergo peer review along with automated testing and security scanning before merging into the main branch.
 #4.8.5    Level: 2    Role: D/V
 Verify that non-production data is anonymized in accordance with organizational privacy requirements, using synthetic data generation or complete data masking with verified removal of PII.
 #4.8.6    Level: 2    Role: D/V
 Ensure that promotion gates include automated security tests (SAST, DAST, container scanning) with zero CRITICAL findings required for approval.

---

### C4.9 Infrastructure Backup and Recovery

Ensure infrastructure resilience by implementing automated backups, verified recovery procedures, and disaster recovery capabilities.

 #4.9.1    Level: 1    Role: D/V
 Verify that infrastructure configurations are backed up according to organizational backup schedules, using the 3-2-1 backup strategy, and stored in geographically separate regions.
 #4.9.2    Level: 2    Role: D/V
 Ensure that backup systems operate on isolated networks with separate credentials and air-gapped storage to protect against ransomware.
 #4.9.3    Level: 2    Role: V
 Verify that recovery procedures are tested and validated through automated testing according to organizational schedules, ensuring RTO and RPO targets meet organizational requirements.
 #4.9.4    Level: 3    Role: V
 Verify that disaster recovery plans include AI-specific runbooks detailing model weight restoration, GPU cluster rebuilding, and service dependency mapping.

---

### C4.10 Infrastructure Compliance and Governance

Ensure regulatory compliance through continuous assessment, documentation, and automated controls.

 #4.10.1    Level: 2    Role: D/V
 Ensure that infrastructure compliance is evaluated according to organizational schedules against SOC 2, ISO 27001, or FedRAMP controls, utilizing automated evidence collection.
 #4.10.2    Level: 2    Role: V
 Ensure that infrastructure documentation includes network diagrams, data flow maps, and threat models updated according to organizational change management requirements.
 #4.10.3    Level: 3    Role: D/V
 Ensure that infrastructure changes undergo automated compliance impact assessments with regulatory approval workflows for high-risk modifications.

---

### C4.11 AI Hardware Security

Secure AI-specific hardware components, including GPUs, TPUs, and specialized AI accelerators.

 #4.11.1    Level: 2    Role: D/V
 Ensure that AI accelerator firmware (GPU BIOS, TPU firmware) is authenticated with cryptographic signatures and updated following the organization's patch management schedule.
 #4.11.2    Level: 2    Role: D/V
 Ensure that before workload execution, the AI accelerator's integrity is verified through hardware attestation using TPM 2.0, Intel TXT, or AMD SVM.
 #4.11.3    Level: 2    Role: D/V
 Verify that GPU memory is isolated between workloads using SR-IOV, MIG (Multi-Instance GPU), or equivalent hardware partitioning, with memory sanitization between jobs.
 #4.11.4    Level: 3    Role: V
 Verify that the AI hardware supply chain includes provenance verification through manufacturer certificates and validation of tamper-evident packaging.
 #4.11.5    Level: 3    Role: D/V
 Verify that hardware security modules (HSMs) protect AI model weights and cryptographic keys with FIPS 140-2 Level 3 or Common Criteria EAL4+ certification.

---

### C4.12 Edge and Distributed AI Infrastructure

Secure distributed AI deployments, including edge computing, federated learning, and multi-site architectures.

 #4.12.1    Level: 2    Role: D/V
 Ensure that edge AI devices authenticate to the central infrastructure using mutual TLS with device certificates rotated in accordance with the organization's certificate management policy.
 #4.12.2    Level: 2    Role: D/V
 Ensure that edge devices implement secure boot with verified signatures and rollback protection to prevent firmware downgrade attacks.
 #4.12.3    Level: 3    Role: D/V
 Verify that distributed AI coordination utilizes Byzantine fault-tolerant consensus algorithms incorporating participant validation and detection of malicious nodes.
 #4.12.4    Level: 3    Role: D/V
 Ensure that edge-to-cloud communication incorporates bandwidth throttling, data compression, and offline operation capabilities with secure local storage.

---

### C4.13 Multi-Cloud and Hybrid Infrastructure Security

Secure AI workloads across multiple cloud providers and hybrid cloud-on-premises deployments.

 #4.13.1    Level: 2    Role: D/V
 Ensure that multi-cloud AI deployments utilize cloud-agnostic identity federation (OIDC, SAML) with centralized policy management across providers.
 #4.13.2    Level: 2    Role: D/V
 Verify that cross-cloud data transfer utilizes end-to-end encryption with customer-managed keys and that data residency controls are enforced according to jurisdiction.
 #4.13.3    Level: 2    Role: D/V
 Verify that hybrid cloud AI workloads enforce consistent security policies across on-premises and cloud environments with unified monitoring and alerting.
 #4.13.4    Level: 3    Role: V
 Ensure that cloud vendor lock-in prevention includes portable infrastructure-as-code, standardized APIs, and data export capabilities with format conversion tools.
 #4.13.5    Level: 3    Role: V
 Verify that multi-cloud cost optimization includes security controls to prevent resource sprawl and unauthorized cross-cloud data transfer charges.

---

### C4.14 Infrastructure Automation & GitOps Security

Secure infrastructure automation pipelines and GitOps workflows for managing AI infrastructure.

 #4.14.1    Level: 2    Role: D/V
 Verify that GitOps repositories require signed commits using GPG keys and enforce branch protection rules that prevent direct pushes to the main branches.
 #4.14.2    Level: 2    Role: D/V
 Verify that infrastructure automation includes drift detection with automatic remediation and rollback capabilities triggered according to organizational response requirements for unauthorized changes.
 #4.14.3    Level: 2    Role: D/V
 Ensure that automated infrastructure provisioning includes security policy validation and blocks deployment of non-compliant configurations.
 #4.14.4    Level: 2    Role: D/V
 Verify that infrastructure automation secrets are managed using external secret operators (External Secrets Operator, Bank-Vaults) with automatic rotation.
 #4.14.5    Level: 3    Role: V
 Verify that the self-healing infrastructure includes security event correlation with automated incident response and stakeholder notification workflows.

---

### C4.15 Quantum-Resistant Infrastructure Security

Prepare AI infrastructure for quantum computing threats by implementing post-quantum cryptography and quantum-safe protocols.

 #4.15.1    Level: 3    Role: D/V
 Verify that the AI infrastructure implements NIST-approved post-quantum cryptographic algorithms (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) for key exchange and digital signatures.
 #4.15.2    Level: 3    Role: D/V
 Verify that quantum key distribution (QKD) systems are implemented for high-security AI communications using quantum-safe key management protocols.
 #4.15.3    Level: 3    Role: D/V
 Verify that cryptographic agility frameworks support rapid migration to new post-quantum algorithms through automated certificate and key rotation.
 #4.15.4    Level: 3    Role: V
 Verify that quantum threat modeling evaluates AI infrastructure vulnerabilities to quantum attacks, including documented migration timelines and risk assessments.
 #4.15.5    Level: 3    Role: D/V
 Verify that hybrid classical-quantum cryptographic systems offer defense-in-depth throughout the quantum transition period, including performance monitoring.

---

### C4.16 Confidential Computing & Secure Enclaves

Protect AI workloads and model weights using hardware-based trusted execution environments and confidential computing technologies.

 #4.16.1    Level: 3    Role: D/V
 Verify that sensitive AI models run within Intel SGX enclaves, AMD SEV-SNP, or ARM TrustZone environments, using encrypted memory and attestation verification.
 #4.16.2    Level: 3    Role: D/V
 Verify that confidential containers (such as Kata Containers and gVisor with confidential computing) isolate AI workloads using hardware-enforced memory encryption.
 #4.16.3    Level: 3    Role: D/V
 Ensure that remote attestation verifies enclave integrity with cryptographic proof of the execution environment's authenticity before loading AI models.
 #4.16.4    Level: 3    Role: D/V
 Verify that confidential AI inference services prevent model extraction by using encrypted computation with sealed model weights and protected execution.
 #4.16.5    Level: 3    Role: D/V
 Verify that the trusted execution environment orchestration manages the secure enclave lifecycle using remote attestation and encrypted communication channels.
 #4.16.6    Level: 3    Role: D/V
 Verify that secure multi-party computation (SMPC) enables collaborative AI training without revealing individual datasets or model parameters.

---

### C4.17 Zero-Knowledge Infrastructure

Develop zero-knowledge proof systems to enable privacy-preserving AI verification and authentication without disclosing sensitive information.

 #4.17.1    Level: 3    Role: D/V
 Verify that zero-knowledge proofs (ZK-SNARKs, ZK-STARKs) confirm AI model integrity and training provenance without revealing model weights or training data.
 #4.17.2    Level: 3    Role: D/V
 Verify that zero-knowledge (ZK)–based authentication systems enable privacy-preserving user verification for AI services without revealing identity-related information.
 #4.17.3    Level: 3    Role: D/V
 Verify that private set intersection (PSI) protocols enable secure data matching for federated AI without revealing individual datasets.
 #4.17.4    Level: 3    Role: D/V
 Verify that zero-knowledge machine learning (ZKML) systems enable verifiable AI inferences through cryptographic proof of correct computation.
 #4.17.5    Level: 3    Role: D/V
 Verify that ZK-rollups provide scalable, privacy-preserving AI transaction processing through batch verification and reduced computational overhead.

---

### C4.18 Prevention of Side-Channel Attacks

Protect AI infrastructure against timing, power, electromagnetic, and cache-based side-channel attacks that could expose sensitive information.

 #4.18.1    Level: 3    Role: D/V
 Verify that AI inference timing is normalized using constant-time algorithms and padding to prevent timing-based model extraction attacks.
 #4.18.2    Level: 3    Role: D/V
 Verify that power analysis protection includes noise injection, power line filtering, and randomized execution patterns for AI hardware.
 #4.18.3    Level: 3    Role: D/V
 Verify that cache-based side-channel mitigation utilizes cache partitioning, randomization, and flush instructions to prevent information leakage.
 #4.18.4    Level: 3    Role: D/V
 Verify that electromagnetic emanation protection includes shielding, signal filtering, and randomized processing to prevent TEMPEST-style attacks.
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
 Verify that hybrid analog-digital AI chips incorporate secure analog computation, protected weight storage, and authenticated analog-to-digital conversion.

---

### C4.20 Privacy-Preserving Computing Infrastructure

Implement infrastructure controls for privacy-preserving computation to protect sensitive data during AI processing and analysis.

 #4.20.1    Level: 3    Role: D/V
 Verify that the homomorphic encryption infrastructure supports encrypted computation on sensitive AI workloads with cryptographic integrity verification and performance monitoring.
 #4.20.2    Level: 3    Role: D/V
 Verify that private information retrieval systems allow database queries without exposing query patterns by using cryptographic protection for access patterns.
 #4.20.3    Level: 3    Role: D/V
 Ensure that secure multi-party computation protocols enable privacy-preserving AI inference without revealing individual inputs or intermediate computations.
 #4.20.4    Level: 3    Role: D/V
 Verify that privacy-preserving key management includes distributed key generation, threshold cryptography, and secure key rotation with hardware-backed protection.
 #4.20.5    Level: 3    Role: D/V
 Ensure that privacy-preserving compute performance is optimized through batching, caching, and hardware acceleration while maintaining cryptographic security guarantees.

---

### C4.15 Agent Framework: Cloud Integration Security and Hybrid Deployment

Security controls for cloud-integrated agent frameworks with hybrid on-premises/cloud architectures.

 #4.15.1    Level: 1    Role: D/V
 Ensure that cloud storage integration uses end-to-end encryption with agent-controlled key management.
 #4.15.2    Level: 2    Role: D/V
 Ensure that the security boundaries for hybrid deployments are clearly defined and that communication channels are encrypted.
 #4.15.3    Level: 2    Role: D/V
 Verify that cloud resource access incorporates zero-trust verification with continuous authentication.
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

Effective access control for AI systems requires robust identity management, context-aware authorization, and runtime enforcement based on zero-trust principles. These controls ensure that humans, services, and autonomous agents interact only with models, data, and computational resources within explicitly granted scopes, with continuous verification and auditing capabilities.

---

### C5.1 Identity Management & Authentication

Establish cryptographically-backed identities for all entities and require multi-factor authentication for privileged operations.

 #5.1.1    Level: 1    Role: D/V
 Ensure that all human users and service principals authenticate through a centralized enterprise identity provider (IdP) using OIDC/SAML protocols with unique identity-to-token mappings (no shared accounts or credentials).
 #5.1.2    Level: 1    Role: D/V
 Verify that high-risk operations (model deployment, weight export, training data access, production configuration changes) require multi-factor authentication or step-up authentication with session revalidation.
 #5.1.3    Level: 2    Role: D
 Verify that new principals undergo identity proofing aligned with NIST 800-63-3 IAL-2 or equivalent standards before gaining production system access.
 #5.1.4    Level: 2    Role: V
 Verify that access reviews are conducted quarterly, incorporating automated detection of dormant accounts, enforcement of credential rotation, and de-provisioning workflows.
 #5.1.5    Level: 3    Role: D/V
 Verify that federated AI agents authenticate using signed JWT assertions with a maximum lifetime of 24 hours and include cryptographic proof of origin.

---

### C5.2 Resource Authorization and Least Privilege

Implement fine-grained access controls for all AI resources using explicit permission models and audit trails.

 #5.2.1    Level: 1    Role: D/V
 Ensure that every AI resource (datasets, models, endpoints, vector collections, embedding indices, compute instances) enforces role-based access controls using explicit allow lists and default-deny policies.
 #5.2.2    Level: 1    Role: D/V
 Ensure that least-privilege principles are enforced by default for service accounts, starting with read-only permissions, and require documented business justification for any write access.
 #5.2.3    Level: 1    Role: V
 Verify that all access control modifications are associated with approved change requests and are immutably logged with timestamps, actor identities, resource identifiers, and permission changes.
 #5.2.4    Level: 2    Role: D
 Verify that data classification labels (PII, PHI, export-controlled, proprietary) automatically propagate to derived resources (embeddings, prompt caches, model outputs) with consistent policy enforcement.
 #5.2.5    Level: 2    Role: D/V
 Verify that unauthorized access attempts and privilege escalation events trigger real-time alerts with contextual metadata to SIEM systems within 5 minutes.

---

### C5.3 Dynamic Policy Evaluation

Deploy attribute-based access control (ABAC) engines for context-aware authorization decisions with auditing capabilities.

 #5.3.1    Level: 1    Role: D/V
 Verify that authorization decisions are externalized to a dedicated policy engine (such as OPA, Cedar, or an equivalent) accessible through authenticated APIs with cryptographic integrity protection.
 #5.3.2    Level: 1    Role: D/V
 Verify that policies evaluate dynamic attributes at runtime, including user clearance level, resource sensitivity classification, request context, tenant isolation, and temporal constraints.
 #5.3.3    Level: 2    Role: D
 Ensure that policy definitions are version-controlled, peer-reviewed, and validated through automated testing within CI/CD pipelines before being deployed to production.
 #5.3.4    Level: 2    Role: V
 Verify that policy evaluation results include structured decision rationales and are transmitted to SIEM systems for correlation analysis and compliance reporting.
 #5.3.5    Level: 3    Role: D/V
 Verify that the policy cache time-to-live (TTL) values do not exceed 5 minutes for high-sensitivity resources and 1 hour for standard resources with cache invalidation capabilities.

---

### C5.4 Security Enforcement at Query Time

Implement database-layer security controls using mandatory filtering and row-level security policies.

 #5.4.1    Level: 1    Role: D/V
 Verify that all vector database and SQL queries include mandatory security filters (tenant ID, sensitivity labels, user scope) enforced at the database engine level, rather than in the application code.
 #5.4.2    Level: 1    Role: D/V
 Verify that row-level security (RLS) policies and field-level masking are enabled with policy inheritance for all vector databases, search indexes, and training datasets.
 #5.4.3    Level: 2    Role: D
 Ensure that failed authorization checks prevent "confused deputy attacks" by immediately aborting queries and returning explicit authorization error codes instead of returning empty result sets.
 #5.4.4    Level: 2    Role: V
 Ensure that policy evaluation latency is continuously monitored with automated alerts for timeout conditions that could allow authorization bypass.
 #5.4.5    Level: 3    Role: D/V
 Ensure that query retry mechanisms re-evaluate authorization policies to reflect dynamic permission changes during active user sessions.

---

### C5.5 Output Filtering & Data Loss Prevention

Implement post-processing controls to prevent unauthorized exposure of data in AI-generated content.

 #5.5.1    Level: 1    Role: D/V
 Verify that post-inference filtering mechanisms scan for and redact unauthorized PII, classified information, and proprietary data before delivering content to requesters.
 #5.5.2    Level: 1    Role: D/V
 Ensure that citations, references, and source attributions in model outputs are verified against caller entitlements and removed if unauthorized access is detected.
 #5.5.3    Level: 2    Role: D
 Ensure that output format restrictions (sanitized PDFs, metadata-stripped images, approved file types) are enforced according to user permission levels and data classifications.
 #5.5.4    Level: 2    Role: V
 Ensure that redaction algorithms are deterministic, version-controlled, and maintain audit logs to support compliance investigations and forensic analysis.
 #5.5.5    Level: 3    Role: V
 Verify that high-risk redaction events generate adaptive logs containing cryptographic hashes of the original content for forensic retrieval without exposing the data.

---

### C5.6 Multi-Tenant Isolation

Ensure cryptographic and logical isolation between tenants within shared AI infrastructure.

 #5.6.1    Level: 1    Role: D/V
 Verify that memory spaces, embedding stores, cache entries, and temporary files are segregated by namespace for each tenant, with secure purging upon tenant deletion or session termination.
 #5.6.2    Level: 1    Role: D/V
 Ensure that every API request includes an authenticated tenant identifier that is cryptographically validated against the session context and user entitlements.
 #5.6.3    Level: 2    Role: D
 Verify that network policies enforce default-deny rules for cross-tenant communication within service meshes and container orchestration platforms.
 #5.6.4    Level: 3    Role: D
 Ensure that encryption keys are unique for each tenant with customer-managed key (CMK) support and maintain cryptographic isolation between tenant data stores.

---

### C5.7 Autonomous Agent Authorization

Manage permissions for AI agents and autonomous systems using scoped capability tokens and continuous authorization.

 #5.7.1    Level: 1    Role: D/V
 Ensure that autonomous agents receive scoped capability tokens that explicitly specify permitted actions, accessible resources, time limits, and operational constraints.
 #5.7.2    Level: 1    Role: D/V
 Verify that high-risk capabilities (file system access, code execution, external API calls, financial transactions) are disabled by default and require explicit authorization for activation, along with business justifications.
 #5.7.3    Level: 2    Role: D
 Verify that capability tokens are tied to user sessions, include cryptographic integrity protection, and ensure they cannot be stored or reused in offline scenarios.
 #5.7.4    Level: 2    Role: V
 Ensure that agent-initiated actions are subject to secondary authorization by the ABAC policy engine, including comprehensive context evaluation and audit logging.
 #5.7.5    Level: 3    Role: V
 Verify that agent error conditions and exception handling include capability scope information to support incident analysis and forensic investigations.

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

AI supply-chain attacks exploit third-party models, frameworks, or datasets to embed backdoors, bias, or exploitable code. These controls offer end-to-end provenance, vulnerability management, and monitoring to protect the entire model lifecycle.

---

### C6.1 Vetting and Provenance of Pretrained Models

Evaluate and verify third-party model origins, licenses, and concealed behaviors before any fine-tuning or deployment.

 #6.1.1    Level: 1    Role: D/V
 Verify that every third-party model artifact includes a signed provenance record identifying the source repository and commit hash.
 #6.1.2    Level: 1    Role: D/V
 Verify that models are scanned for malicious layers or Trojan triggers using automated tools before importing.
 #6.1.3    Level: 2    Role: D
 Verify that transfer learning fine-tunes successfully pass adversarial evaluation to detect hidden behaviors.
 #6.1.4    Level: 2    Role: V
 Verify that model licenses, export-control tags, and data-origin statements are recorded in an ML-BOM entry.
 #6.1.5    Level: 3    Role: D/V
 Ensure that high-risk models (those with publicly uploaded weights or created by unverified individuals) remain quarantined until they undergo human review and receive approval.

---

### C6.2 Framework and Library Scanning

Continuously scan ML frameworks and libraries for CVEs and malicious code to maintain a secure runtime stack.

 #6.2.1    Level: 1    Role: D/V
 Verify that CI pipelines run dependency scanners on AI frameworks and critical libraries.
 #6.2.2    Level: 1    Role: D/V
 Verify that critical vulnerabilities (CVSS ≥ 7.0) prevent promotion to production images.
 #6.2.3    Level: 2    Role: D
 Ensure that static code analysis is performed on forked or vendored machine learning libraries.
 #6.2.4    Level: 2    Role: V
 Ensure that framework upgrade proposals include a security impact assessment that references public CVE feeds.
 #6.2.5    Level: 3    Role: V
 Verify that runtime sensors trigger alerts for unexpected dynamic library loads that deviate from the signed SBOM.

---

### C6.3 Dependency Pinning & Verification

Pin every dependency to immutable digests and reproduce builds to ensure identical, tamper-free artifacts.

 #6.3.1    Level: 1    Role: D/V
 Verify that all package managers enforce version pinning through lockfiles.
 #6.3.2    Level: 1    Role: D/V
 Ensure that immutable digests are used instead of mutable tags in container references.
 #6.3.3    Level: 2    Role: D
 Verify that reproducible build checks compare hashes across CI runs to ensure identical outputs.
 #6.3.4    Level: 2    Role: V
 Verify that build attestations are stored for 18 months to ensure audit traceability.
 #6.3.5    Level: 3    Role: D
 Verify that expired dependencies trigger automated pull requests to update or fork pinned versions.

---

### C6.4 Trusted Source Enforcement

Allow artifact downloads only from cryptographically verified, organization-approved sources, and block all others.

 #6.4.1    Level: 1    Role: D/V
 Verify that model weights, datasets, and containers are downloaded only from approved domains or internal registries.
 #6.4.2    Level: 1    Role: D/V
 Verify that Sigstore/Cosign signatures authenticate the publisher's identity before storing artifacts locally in the cache.
 #6.4.3    Level: 2    Role: D
 Verify that egress proxies block unauthenticated artifact downloads to enforce the trusted-source policy.
 #6.4.4    Level: 2    Role: V
 Verify that repository allow-lists are reviewed quarterly, with evidence of business justification for each entry.
 #6.4.5    Level: 3    Role: V
 Verify that policy violations trigger quarantining of artifacts and rolling back of dependent pipeline runs.

---

### C6.5 Third-Party Dataset Risk Assessment

Evaluate external datasets for poisoning, bias, and legal compliance, and continuously monitor them throughout their lifecycle.

 #6.5.1    Level: 1    Role: D/V
 Verify that external datasets are subjected to poisoning risk assessment (e.g., data fingerprinting, outlier detection).
 #6.5.2    Level: 1    Role: D
 Ensure that bias metrics (demographic parity, equal opportunity) are calculated prior to dataset approval.
 #6.5.3    Level: 2    Role: V
 Verify that provenance and license terms for datasets are recorded in ML-BOM entries.
 #6.5.4    Level: 2    Role: V
 Ensure that periodic monitoring identifies drift or corruption in hosted datasets.
 #6.5.5    Level: 3    Role: D
 Ensure that disallowed content (copyrighted material, PII) is removed through automated scrubbing before training.

---

### C6.6 Supply Chain Attack Monitoring

Detect supply-chain threats early using CVE feeds, audit log analytics, and red team simulations.

 #6.6.1    Level: 1    Role: V
 Verify that CI/CD audit logs are streamed to SIEM for detecting anomalous package pulls or tampered build steps.
 #6.6.2    Level: 2    Role: D
 Verify that incident response playbooks include rollback procedures for compromised models or libraries.
 #6.6.3    Level: 3    Role: V
 Verify that threat-intel enrichment tags machine learning-specific indicators (e.g., model-poisoning IoCs) during alert triage.

---

### C6.7 ML‑BOM for Model Artifacts

Generate and sign detailed ML-specific SBOMs (ML-BOMs) so that downstream consumers can verify component integrity at deployment time.

 #6.7.1    Level: 1    Role: D/V
 Verify that every model artifact publishes an ML-BOM listing datasets, weights, hyperparameters, and licenses.
 #6.7.2    Level: 1    Role: D/V
 Verify that ML-BOM generation and Cosign signing are automated in the CI process and are required for merging.
 #6.7.3    Level: 2    Role: D
 Verify that ML-BOM completeness checks cause the build to fail if any component metadata (hash, license) is missing.
 #6.7.4    Level: 2    Role: V
 Verify that downstream consumers can query ML-BOMs through the API to validate imported models at deployment time.
 #6.7.5    Level: 3    Role: V
 Verify that ML-BOMs are version-controlled and diffed to detect unauthorized modifications.

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

## C7 Model Behavior, Output Control & Safety Assurance

### Control Objective

Model outputs must be structured, reliable, safe, explainable, and continuously monitored in production. This approach reduces hallucinations, privacy leaks, harmful content, and unintended actions, while increasing user trust and ensuring regulatory compliance.

---

### C7.1 Output Format Enforcement

Strict schemas, constrained decoding, and downstream validation prevent malformed or malicious content from propagating.

 #7.1.1    Level: 1    Role: D/V
 Ensure that response schemas (e.g., JSON Schema) are included in the system prompt and that every output is automatically validated; outputs that do not conform should trigger repair or rejection.
 #7.1.2    Level: 1    Role: D/V
 Ensure that constrained decoding (stop tokens, regex, max tokens) is enabled to prevent overflow or prompt injection side channels.
 #7.1.3    Level: 2    Role: D/V
 Ensure that downstream components treat outputs as untrusted and validate them against schemas or injection-safe deserializers.
 #7.1.4    Level: 3    Role: V
 Verify that events with improper output are logged, rate-limited, and surfaced to monitoring.

---

### C7.2 Hallucination Detection and Mitigation

Estimating uncertainty and employing fallback strategies help reduce fabricated answers.

 #7.2.1    Level: 1    Role: D/V
 Verify that token-level log-probabilities, ensemble self-consistency, or fine-tuned hallucination detectors assign a confidence score to each answer.
 #7.2.2    Level: 1    Role: D/V
 Ensure that responses falling below a configurable confidence threshold activate fallback workflows, such as retrieval-augmented generation, a secondary model, or human review.
 #7.2.3    Level: 2    Role: D/V
 Ensure that hallucination incidents are tagged with root-cause metadata and fed into post-mortem analysis and fine-tuning pipelines.
 #7.2.4    Level: 3    Role: D/V
 Ensure that thresholds and detectors are recalibrated after significant model or knowledge-base updates.
 #7.2.5    Level: 3    Role: V
 Verify that dashboard visualizations track hallucination rates.

---

### C7.3 Output Safety and Privacy Filtering

Policy filters and red-team coverage safeguard users and confidential data.

 #7.3.1    Level: 1    Role: D/V
 Verify that both pre- and post-generation classifiers block hate speech, harassment, self-harm, extremist content, and sexually explicit material in accordance with policy.
 #7.3.2    Level: 1    Role: D/V
 Ensure that PII/PCI detection and automatic redaction are performed on every response; any violations trigger a privacy incident.
 #7.3.3    Level: 2    Role: D
 Verify that confidentiality tags (e.g., trade secrets) carry over across modalities to prevent leaks in text, images, or code.
 #7.3.4    Level: 3    Role: D/V
 Verify that filter bypass attempts or high-risk classifications require secondary approval or user re-authentication.
 #7.3.5    Level: 3    Role: D/V
 Verify that filtering thresholds correspond to legal jurisdictions and the user's age and role context.

---

### C7.4 Output and Action Limiting

Rate limits and approval gates prevent abuse and excessive autonomy.

 #7.4.1    Level: 1    Role: D
 Verify that per-user and per-API-key quotas limit requests, tokens, and costs, implementing exponential back-off on 429 errors.
 #7.4.2    Level: 1    Role: D/V
 Verify that privileged actions (file writes, code execution, network calls) require policy-based approval or human-in-the-loop intervention.
 #7.4.3    Level: 2    Role: D/V
 Verify that cross-modal consistency checks ensure that images, code, and text generated for the same request cannot be used to smuggle malicious content.
 #7.4.4    Level: 2    Role: D
 Verify that agent delegation depth, recursion limits, and allowed tool lists are explicitly configured.
 #7.4.5    Level: 3    Role: V
 Verify that limit violations generate structured security events for SIEM ingestion.

---

### C7.5 Output Explainability

Transparent signals enhance user trust and facilitate internal debugging.

 #7.5.1    Level: 2    Role: D/V
 Ensure that user-facing confidence scores or brief reasoning summaries are displayed when the risk assessment deems it appropriate.
 #7.5.2    Level: 2    Role: D/V
 Ensure that generated explanations do not reveal sensitive system prompts or proprietary information.
 #7.5.3    Level: 3    Role: D
 Verify that the system captures token-level log probabilities or attention maps and stores them for authorized inspection.
 #7.5.4    Level: 3    Role: V
 Ensure that explainability artifacts are version-controlled alongside model releases for auditability.

---

### C7.6 Monitoring Integration

Real-time observability closes the loop between development and production.

 #7.6.1    Level: 1    Role: D
 Verify that metrics (schema violations, hallucination rate, toxicity, PII leaks, latency, cost) are streamed to a central monitoring platform.
 #7.6.2    Level: 1    Role: V
 Ensure that alert thresholds are defined for each safety metric, with on-call escalation paths established.
 #7.6.3    Level: 2    Role: V
 Verify that dashboards correlate output anomalies with the model/version, feature flags, and upstream data changes.
 #7.6.4    Level: 2    Role: D/V
 Ensure that monitoring data is fed back into retraining, fine-tuning, or rule updates within a documented MLOps workflow.
 #7.6.5    Level: 3    Role: V
 Ensure that monitoring pipelines undergo penetration testing and have access controls in place to prevent the leakage of sensitive logs.

---

### 7.7 Generative Media Safeguards

Ensure that AI systems do not generate illegal, harmful, or unauthorized media content by enforcing policy constraints, validating outputs, and maintaining traceability.

 #7.7.1    Level: 1    Role: D/V
 Verify that system prompts and user instructions explicitly prohibit generating illegal, harmful, or non-consensual deepfake media (e.g., images, videos, audio).
 #7.7.2    Level: 2    Role: D/V
 Ensure that prompts are filtered to prevent attempts to generate impersonations, sexually explicit deepfakes, or media depicting real individuals without their consent.
 #7.7.3    Level: 2    Role: V
 Verify that the system uses perceptual hashing, watermark detection, or fingerprinting to prevent unauthorized reproduction of copyrighted media.
 #7.7.4    Level: 3    Role: D/V
 Ensure that all generated media is cryptographically signed, watermarked, or embedded with tamper-resistant provenance metadata to enable downstream traceability.
 #7.7.5    Level: 3    Role: V
 Ensure that bypass attempts (e.g., prompt obfuscation, slang, adversarial phrasing) are detected, logged, and rate-limited; repeated abuse is reported to monitoring systems.

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

Embeddings and vector stores serve as the "live memory" of modern AI systems, continuously receiving user-provided data and reintegrating it into model contexts through Retrieval-Augmented Generation (RAG). If left unmanaged, this memory can leak personally identifiable information (PII), violate consent, or be reverse-engineered to reconstruct the original text. The goal of this control family is to strengthen memory pipelines and vector databases so that access follows the principle of least privilege, embeddings maintain privacy, stored vectors have expiration or can be revoked on demand, and individual user memory never contaminates another user's prompts or completions.

---

### C8.1 Access Controls on Memory and RAG Indices

Enforce fine-grained access controls on each vector collection.

 #8.1.1    Level: 1    Role: D/V
 Verify that row-level and namespace-level access control rules restrict insert, delete, and query operations for each tenant, collection, or document tag.
 #8.1.2    Level: 1    Role: D/V
 Ensure that API keys or JWTs include scoped claims (e.g., collection IDs, action verbs) and are rotated at least quarterly.
 #8.1.3    Level: 2    Role: D/V
 Verify that attempts at privilege escalation (e.g., cross-namespace similarity queries) are detected and logged in a SIEM within 5 minutes.
 #8.1.4    Level: 2    Role: D/V
 Verify that the vector database audit logs include the subject identifier, operation, vector ID/namespace, similarity threshold, and result count.
 #8.1.5    Level: 3    Role: V
 Ensure that access decisions are tested for bypass vulnerabilities whenever engines are upgraded or index-sharding rules are modified.

---

### C8.2 Embedding Sanitization and Validation

Pre-screen text for PII, redact or pseudonymize it before vectorization, and optionally post-process embeddings to remove any residual signals.

 #8.2.1    Level: 1    Role: D/V
 Verify that PII and regulated data are detected by automated classifiers and then masked, tokenized, or dropped before embedding.
 #8.2.2    Level: 1    Role: D
 Verify that embedding pipelines reject or quarantine inputs containing executable code or non-UTF-8 artifacts that could compromise the index.
 #8.2.3    Level: 2    Role: D/V
 Verify that local or metric differential privacy sanitization is applied to sentence embeddings whose distance to any known PII token falls below a configurable threshold.
 #8.2.4    Level: 2    Role: V
 Verify that the effectiveness of sanitization (e.g., recall of PII redaction, semantic drift) is validated at least semiannually against benchmark corpora.
 #8.2.5    Level: 3    Role: D/V
 Ensure that sanitization configurations are version-controlled and that any changes undergo peer review.

---

### C8.3 Memory Expiry, Revocation, and Deletion

The GDPR "right to be forgotten" and similar regulations require prompt deletion; therefore, vector stores must support TTLs, hard deletes, and tombstoning to ensure that revoked vectors cannot be recovered or re-indexed.

 #8.3.1    Level: 1    Role: D/V
 Ensure that every vector and metadata record includes a TTL or an explicit retention label that is respected by automated cleanup jobs.
 #8.3.2    Level: 1    Role: D/V
 Verify that user-initiated deletion requests remove vectors, metadata, cache copies, and derivative indices within 30 days.
 #8.3.3    Level: 2    Role: D
 Verify that logical deletions are followed by cryptographic shredding of storage blocks if the hardware supports it, or by key-vault key destruction.
 #8.3.4    Level: 3    Role: D/V
 Verify that expired vectors are excluded from nearest neighbor search results within 500 ms after expiration.

---

### C8.4 Prevent Embedding Inversion and Leakage

Recent defenses—noise superposition, projection networks, privacy-neuron perturbation, and application-layer encryption—can reduce token-level inversion rates to below 5%.

 #8.4.1    Level: 1    Role: V
 Ensure that a formal threat model addressing inversion, membership, and attribute-inference attacks is in place and reviewed annually.
 #8.4.2    Level: 2    Role: D/V
 Verify that application-layer encryption or searchable encryption protects vectors from direct access by infrastructure administrators or cloud personnel.
 #8.4.3    Level: 3    Role: V
 Verify that defense parameters (ε for DP, noise σ, projection rank k) maintain privacy at ≥ 99% token protection and utility at ≤ 3% accuracy loss.
 #8.4.4    Level: 3    Role: D/V
 Verify that inversion-resilience metrics are included in the release gates for model updates, with regression budgets clearly defined.

---

### C8.5 Scope Enforcement for User-Specific Memory

Cross-tenant leakage remains a major RAG risk: improperly filtered similarity queries can reveal another customer's private documents.

 #8.5.1    Level: 1    Role: D/V
 Verify that every retrieval query is post-filtered by tenant/user ID before being sent to the LLM prompt.
 #8.5.2    Level: 1    Role: D
 Verify that collection names or namespaced IDs are salted for each user or tenant to prevent vector collisions across scopes.
 #8.5.3    Level: 2    Role: D/V
 Verify that similarity results exceeding a configurable distance threshold but falling outside the caller’s scope are discarded and trigger security alerts.
 #8.5.4    Level: 2    Role: V
 Verify that multi-tenant stress tests simulate adversarial queries attempting to retrieve out-of-scope documents and demonstrate zero leakage.
 #8.5.5    Level: 3    Role: D/V
 Verify that encryption keys are segregated per tenant, ensuring cryptographic isolation even when physical storage is shared.

---

### C8.6 Advanced Memory System Security

Security controls for advanced memory architectures, including episodic, semantic, and working memory, with specific isolation and validation requirements.

 #8.6.1    Level: 1    Role: D/V
 Verify that different memory types (episodic, semantic, working) have isolated security contexts with role-based access controls, separate encryption keys, and documented access patterns for each memory type.
 #8.6.2    Level: 2    Role: D/V
 Ensure that memory consolidation processes include security validation to prevent the injection of malicious memories by implementing content sanitization, source verification, and integrity checks before storage.
 #8.6.3    Level: 2    Role: D/V
 Verify that memory retrieval queries are validated and sanitized to prevent the extraction of unauthorized information through query pattern analysis, access control enforcement, and result filtering.
 #8.6.4    Level: 3    Role: D/V
 Ensure that memory forgetting mechanisms securely delete sensitive information by providing cryptographic erasure guarantees through key deletion, multi-pass overwriting, or hardware-based secure deletion accompanied by verification certificates.
 #8.6.5    Level: 3    Role: D/V
 Verify that the memory system's integrity is continuously monitored for unauthorized modifications or corruption using checksums, audit logs, and automated alerts triggered when memory content changes outside of normal operations.

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

Ensure that autonomous or multi-agent AI systems can only perform actions that are explicitly intended, authenticated, auditable, and within defined cost and risk limits. This safeguards against threats such as autonomous system compromise, tool misuse, agent loop detection, communication hijacking, identity spoofing, swarm manipulation, and intent manipulation.

---

### 9.1 Agent Task Planning & Recursion Budgets

Limit recursive plans and require human verification for privileged actions.

 #9.1.1    Level: 1    Role: D/V
 Ensure that the maximum recursion depth, breadth, wall-clock time, tokens, and monetary cost per agent execution are configured centrally and managed through version control.
 #9.1.2    Level: 1    Role: D/V
 Ensure that privileged or irreversible actions (e.g., code commits, financial transfers) require explicit human approval through an auditable channel before execution.
 #9.1.3    Level: 2    Role: D
 Verify that real-time resource monitors trigger a circuit-breaker interruption when any budget threshold is exceeded, halting further task expansion.
 #9.1.4    Level: 2    Role: D/V
 Verify that circuit breaker events are logged with the agent ID, triggering condition, and captured plan state for forensic review.
 #9.1.5    Level: 3    Role: V
 Verify that security tests cover budget exhaustion and runaway plan scenarios, ensuring safe halting without data loss.
 #9.1.6    Level: 3    Role: D
 Ensure that budget policies are defined as policy-as-code and enforced within CI/CD pipelines to prevent configuration drift.

---

### 9.2 Tool Plugin Sandboxing

Isolate tool interactions to prevent unauthorized system access or code execution.

 #9.2.1    Level: 1    Role: D/V
 Ensure that every tool/plugin runs within an OS, container, or WASM-level sandbox using least-privilege policies for the file system, network, and system calls.
 #9.2.2    Level: 1    Role: D/V
 Verify that sandbox resource quotas (CPU, memory, disk, network egress) and execution timeouts are enforced and properly logged.
 #9.2.3    Level: 2    Role: D/V
 Verify that tool binaries or descriptors are digitally signed; signatures must be validated before loading.
 #9.2.4    Level: 2    Role: V
 Verify that sandbox telemetry streams to a SIEM; anomalies (e.g., attempted outbound connections) trigger alerts.
 #9.2.5    Level: 3    Role: V
 Ensure that high-risk plugins undergo security reviews and penetration testing before being deployed to production.
 #9.2.6    Level: 3    Role: D/V
 Ensure that sandbox escape attempts are automatically blocked and that the offending plugin is quarantined pending investigation.

---

### 9.3 Autonomous Loop and Cost Bounding

Detect and prevent uncontrolled agent-to-agent recursion and cost explosions.

 #9.3.1    Level: 1    Role: D/V
 Verify that inter-agent calls have a hop limit or TTL that the runtime decrements and enforces.
 #9.3.2    Level: 2    Role: D
 Verify that agents maintain a unique invocation-graph ID to detect self-invocation or cyclical patterns.
 #9.3.3    Level: 2    Role: D/V
 Verify that cumulative compute-unit and spending counters are tracked per request chain; exceeding the limit aborts the chain.
 #9.3.4    Level: 3    Role: V
 Verify that formal analysis or model checking demonstrates the absence of unbounded recursion in agent protocols.
 #9.3.5    Level: 3    Role: D
 Verify that loop-abort events trigger alerts and provide metrics for continuous improvement.

---

### 9.4 Protocol-Level Misuse Protection

Secure communication channels between agents and external systems to prevent hijacking or manipulation.

 #9.4.1    Level: 1    Role: D/V
 Ensure that all agent-to-tool and agent-to-agent messages are authenticated (e.g., mutual TLS or JWT) and encrypted end-to-end.
 #9.4.2    Level: 1    Role: D
 Ensure that schemas are strictly validated; unknown fields or malformed messages must be rejected.
 #9.4.3    Level: 2    Role: D/V
 Verify that integrity checks (MACs or digital signatures) cover the entire message payload, including tool parameters.
 #9.4.4    Level: 2    Role: D
 Verify that replay protection (using nonces or timestamp windows) is enforced at the protocol layer.
 #9.4.5    Level: 3    Role: V
 Ensure that protocol implementations undergo fuzz testing and static analysis to detect injection or deserialization vulnerabilities.

---

### 9.5 Agent Identity & Tamper Evidence

Ensure that actions are attributable and that modifications are detectable.

 #9.5.1    Level: 1    Role: D/V
 Verify that each agent instance has a unique cryptographic identity (key pair or hardware-rooted credential).
 #9.5.2    Level: 2    Role: D/V
 Ensure that all agent actions are signed and timestamped; logs must include the signature to prevent repudiation.
 #9.5.3    Level: 2    Role: V
 Verify that tamper-evident logs are stored in an append-only or write-once medium.
 #9.5.4    Level: 3    Role: D
 Verify that identity keys rotate according to a defined schedule and upon indicators of compromise.
 #9.5.5    Level: 3    Role: D/V
 Verify that spoofing or key-conflict attempts immediately trigger quarantine of the affected agent.

---

### 9.6 Multi-Agent Swarm Risk Mitigation

Mitigate collective behavior hazards through isolation and formal safety modeling.

 #9.6.1    Level: 1    Role: D/V
 Ensure that agents operating in different security domains run in isolated runtime sandboxes or separate network segments.
 #9.6.2    Level: 3    Role: V
 Verify that swarm behaviors are modeled and formally verified for both liveness and safety before deployment.
 #9.6.3    Level: 3    Role: D
 Verify that runtime monitors detect emerging unsafe patterns (e.g., oscillations, deadlocks) and initiate corrective actions.

---

### 9.7 User and Tool Authentication / Authorization

Implement robust access controls for every action triggered by an agent.

 #9.7.1    Level: 1    Role: D/V
 Ensure that agents authenticate as first-class principals to downstream systems without ever reusing end-user credentials.
 #9.7.2    Level: 2    Role: D
 Ensure that fine-grained authorization policies limit which tools an agent can invoke and which parameters it can provide.
 #9.7.3    Level: 2    Role: V
 Ensure that privilege checks are re-evaluated on every call (continuous authorization), not just at session start.
 #9.7.4    Level: 3    Role: D
 Ensure that delegated privileges automatically expire and require re-consent after a timeout or a change in scope.

---

### 9.8 Security of Agent-to-Agent Communication

Encrypt and protect the integrity of all inter-agent messages to prevent eavesdropping and tampering.

 #9.8.1    Level: 1    Role: D/V
 Ensure that mutual authentication and perfect forward secrecy encryption (e.g., TLS 1.3) are mandatory for agent channels.
 #9.8.2    Level: 1    Role: D
 Ensure that message integrity and origin are verified before processing; any failures trigger alerts and result in the message being discarded.
 #9.8.3    Level: 2    Role: D/V
 Verify that communication metadata (timestamps, sequence numbers) is logged to support forensic reconstruction.
 #9.8.4    Level: 3    Role: V
 Verify that formal verification or model checking confirms that protocol state machines cannot be driven into unsafe states.

---

### 9.9 Intent Verification and Constraint Enforcement

Verify that the agent's actions align with the user's stated intent and system constraints.

 #9.9.1    Level: 1    Role: D
 Ensure that pre-execution constraint solvers verify proposed actions against hard-coded safety and policy rules.
 #9.9.2    Level: 2    Role: D/V
 Ensure that high-impact actions (financial, destructive, privacy-sensitive) require explicit intent confirmation from the initiating user.
 #9.9.3    Level: 2    Role: V
 Verify that post-condition checks confirm completed actions achieved their intended effects without side effects; any discrepancies trigger a rollback.
 #9.9.4    Level: 3    Role: V
 Verify that formal methods (e.g., model checking, theorem proving) or property-based testing demonstrate that agent plans satisfy all declared constraints.
 #9.9.5    Level: 3    Role: D
 Verify that incidents involving intent mismatch or constraint violations contribute to continuous improvement cycles and threat intelligence sharing.

---

### 9.10 Security of Agent Reasoning Strategies

Secure selection and execution of various reasoning strategies, including ReAct, Chain-of-Thought, and Tree-of-Thoughts approaches.

 #9.10.1    Level: 1    Role: D/V
 Verify that the reasoning strategy selection uses deterministic criteria (such as input complexity, task type, and security context) and that identical inputs produce identical strategy selections within the same security context.
 #9.10.2    Level: 1    Role: D/V
 Verify that each reasoning strategy (ReAct, Chain-of-Thought, Tree-of-Thoughts) has dedicated input validation, output sanitization, and execution time limits tailored to its specific cognitive approach.
 #9.10.3    Level: 2    Role: D/V
 Ensure that reasoning strategy transitions are logged with complete context, including input characteristics, selection criteria values, and execution metadata, to support audit trail reconstruction.
 #9.10.4    Level: 2    Role: D/V
 Verify that Tree-of-Thoughts reasoning incorporates branch pruning mechanisms that halt exploration when policy violations, resource constraints, or safety boundaries are identified.
 #9.10.5    Level: 2    Role: D/V
 Verify that ReAct (Reason-Act-Observe) cycles include validation checkpoints at each phase: reasoning step verification, action authorization, and observation sanitization before proceeding.
 #9.10.6    Level: 3    Role: D/V
 Ensure that the performance metrics of the reasoning strategy (execution time, resource usage, output quality) are monitored with automated alerts triggered when metrics exceed configured thresholds.
 #9.10.7    Level: 3    Role: D/V
 Ensure that hybrid reasoning approaches, which combine multiple strategies, maintain input validation and output constraints for all constituent strategies without bypassing any security controls.
 #9.10.8    Level: 3    Role: D/V
 Verify that the reasoning strategy security testing includes fuzzing with malformed inputs, adversarial prompts designed to trigger strategy switching, and boundary condition testing for each cognitive approach.

---

### 9.11 Agent Lifecycle State Management and Security

Secure agent initialization, state transitions, and termination with cryptographic audit trails and defined recovery procedures.

 #9.11.1    Level: 1    Role: D/V
 Verify that agent initialization includes establishing a cryptographic identity with hardware-backed credentials and immutable startup audit logs containing the agent ID, timestamp, configuration hash, and initialization parameters.
 #9.11.2    Level: 2    Role: D/V
 Verify that agent state transitions are cryptographically signed, timestamped, and logged with complete context, including triggering events, previous state hash, new state hash, and security validations performed.
 #9.11.3    Level: 2    Role: D/V
 Verify that agent shutdown procedures include secure memory wiping through cryptographic erasure or multi-pass overwriting, credential revocation with notification to the certificate authority, and the generation of tamper-evident termination certificates.
 #9.11.4    Level: 3    Role: D/V
 Verify that agent recovery mechanisms validate state integrity using cryptographic checksums (minimum SHA-256) and roll back to known-good states when corruption is detected, with automated alerts and manual approval requirements.
 #9.11.5    Level: 3    Role: D/V
 Ensure that agent persistence mechanisms encrypt sensitive state data using per-agent AES-256 keys and implement secure key rotation on configurable schedules (maximum 90 days) with zero-downtime deployment.

---

### 9.12 Tool Integration Security Framework

Security controls for dynamic tool loading, execution, and result validation with established risk assessment and approval processes.

 #9.12.1    Level: 1    Role: D/V
 Verify that tool descriptors include security metadata specifying required privileges (read/write/execute), risk levels (low/medium/high), resource limits (CPU, memory, network), and validation requirements as documented in tool manifests.
 #9.12.2    Level: 1    Role: D/V
 Verify that tool execution results are validated against expected schemas (JSON Schema, XML Schema) and security policies (output sanitization, data classification) before integration, ensuring timeout limits and error handling procedures are in place.
 #9.12.3    Level: 2    Role: D/V
 Verify that tool interaction logs contain detailed security context, including privilege usage, data access patterns, execution time, resource consumption, and return codes, with structured logging for SIEM integration.
 #9.12.4    Level: 2    Role: D/V
 Ensure that dynamic tool loading mechanisms validate digital signatures through PKI infrastructure and implement secure loading protocols, including sandbox isolation and permission verification, prior to execution.
 #9.12.5    Level: 3    Role: D/V
 Verify that tool security assessments are automatically triggered for new versions, with mandatory approval gates including static analysis, dynamic testing, and security team review, all supported by documented approval criteria and SLA requirements.

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

Ensure that AI models remain reliable, privacy-preserving, and resistant to abuse when confronted with evasion, inference, extraction, or poisoning attacks.

---

### 10.1 Model Alignment & Safety

Protect against harmful or policy-violating outputs.

 #10.1.1    Level: 1    Role: D/V
 Verify that an alignment test suite (red-team prompts, jailbreak probes, disallowed content) is version-controlled and executed with every model release.
 #10.1.2    Level: 1    Role: D
 Verify that refusal and safe-completion guardrails are enforced.
 #10.1.3    Level: 2    Role: D/V
 Verify that an automated evaluator measures the harmful content rate and flags regressions that exceed a set threshold.
 #10.1.4    Level: 2    Role: D
 Ensure that counter-jailbreak training is properly documented and can be consistently reproduced.
 #10.1.5    Level: 3    Role: V
 Ensure that formal proofs of policy compliance or certified monitoring address critical domains.

---

### 10.2 Adversarial Example Hardening

Enhance resilience to manipulated inputs. Robust adversarial training and benchmark scoring are the current best practices.

 #10.2.1    Level: 1    Role: D
 Ensure that project repositories contain adversarial training configurations with reproducible seeds.
 #10.2.2    Level: 2    Role: D/V
 Verify that adversarial example detection triggers blocking alerts in production pipelines.
 #10.2.4    Level: 3    Role: V
 Verify that certified robustness proofs or interval-bound certificates cover at least the most critical classes.
 #10.2.5    Level: 3    Role: V
 Verify that regression tests utilize adaptive attacks to ensure there is no measurable loss of robustness.

---

### 10.3 Membership-Inference Mitigation

Limit the ability to determine whether a record was part of the training data. Differential privacy and confidence score masking remain the most effective known defenses.

 #10.3.1    Level: 1    Role: D
 Verify that per-query entropy regularization or temperature scaling reduces overconfident predictions.
 #10.3.2    Level: 2    Role: D
 Verify that training uses ε-bounded differentially private optimization for sensitive datasets.
 #10.3.3    Level: 2    Role: V
 Verify that attack simulations (shadow-model or black-box) demonstrate an attack AUC of ≤ 0.60 on held-out data.

---

### 10.4 Resistance to Model Inversion

Prevent the reconstruction of private attributes. Recent surveys highlight output truncation and differential privacy (DP) guarantees as effective practical defenses.

 #10.4.1    Level: 1    Role: D
 Verify that sensitive attributes are never directly outputted; when necessary, use buckets or one-way transformations.
 #10.4.2    Level: 1    Role: D/V
 Confirm that query rate limits effectively throttle repeated adaptive queries from the same principal.
 #10.4.3    Level: 2    Role: D
 Verify that the model is trained using privacy-preserving noise.

---

### 10.5 Defense Against Model Extraction

Detect and prevent unauthorized cloning. Watermarking and query pattern analysis are recommended.

 #10.5.1    Level: 1    Role: D
 Verify that inference gateways enforce both global and per-API-key rate limits adjusted to the model's memorization threshold.
 #10.5.2    Level: 2    Role: D/V
 Verify that query entropy and input plurality statistics feed an automated extraction detector.
 #10.5.3    Level: 2    Role: V
 Verify that fragile or probabilistic watermarks can be proven with p < 0.01 in 1,000 or fewer queries against a suspected clone.
 #10.5.4    Level: 3    Role: D
 Verify that watermark keys and trigger sets are stored in a hardware security module and rotated annually.
 #10.5.5    Level: 3    Role: V
 Verify that extraction-alert events include the offending queries and are integrated with incident response playbooks.

---

### 10.6 Detection of Poisoned Data at Inference Time

Identify and neutralize backdoored or poisoned inputs.

 #10.6.1    Level: 1    Role: D
 Verify that inputs pass through an anomaly detector (e.g., STRIP, consistency scoring) before model inference.
 #10.6.2    Level: 1    Role: V
 Verify that the detector thresholds are adjusted on clean and poisoned validation sets to achieve less than 5% false positives.
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
 Verify that policy updates are cryptographically signed by authorized security personnel and validated before being applied.
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
 Verify that agent reflection mechanisms include security-focused self-assessment of decisions and actions.
 #10.8.2    Level: 2    Role: D/V
 Ensure that reflection outputs are validated to prevent manipulation of self-assessment mechanisms by adversarial inputs.
 #10.8.3    Level: 2    Role: D/V
 Verify that meta-cognitive security analysis identifies potential biases, manipulation, or compromises in agent reasoning processes.
 #10.8.4    Level: 3    Role: D/V
 Verify that reflection-based security warnings activate enhanced monitoring and possible human intervention workflows.
 #10.8.5    Level: 3    Role: D/V
 Verify that continuous learning from security reflections enhances threat detection without compromising legitimate functionality.

---

### 10.9 Evolution and Self-Improvement Security

Security controls for agent systems capable of self-modification and evolution.

 #10.9.1    Level: 1    Role: D/V
 Verify that self-modification capabilities are limited to designated safe areas with formal verification boundaries.
 #10.9.2    Level: 2    Role: D/V
 Ensure that evolution proposals undergo a security impact assessment before implementation.
 #10.9.3    Level: 2    Role: D/V
 Ensure that self-improvement mechanisms incorporate rollback features with integrity verification.
 #10.9.4    Level: 3    Role: D/V
 Verify that meta-learning security prevents adversarial manipulation of improvement algorithms.
 #10.9.5    Level: 3    Role: D/V
 Ensure that recursive self-improvement is limited by formal safety constraints, supported by mathematical proofs of convergence.

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

Maintain strict privacy protections throughout the entire AI lifecycle—collection, training, inference, and incident response—ensuring that personal data is processed only with explicit consent, minimal necessary scope, verifiable erasure, and formal privacy assurances.

---

### 11.1 Anonymization and Data Minimization

 #11.1.1    Level: 1    Role: D/V
 Verify that direct and quasi-identifiers are removed or hashed.
 #11.1.2    Level: 2    Role: D/V
 Verify that automated audits measure k-anonymity and l-diversity, and alert when thresholds fall below policy levels.
 #11.1.3    Level: 2    Role: V
 Verify that the model's feature importance reports demonstrate no identifier leakage beyond ε = 0.01 mutual information.
 #11.1.4    Level: 3    Role: V
 Verify that formal proofs or synthetic data certification demonstrate a re-identification risk of ≤ 0.05, even under linkage attacks.

---

### 11.2 Right to Be Forgotten & Deletion Enforcement

 #11.2.1    Level: 1    Role: D/V
 Verify that data-subject deletion requests propagate to raw datasets, checkpoints, embeddings, logs, and backups within service level agreements of under 30 days.
 #11.2.2    Level: 2    Role: D
 Verify that "machine unlearning" routines physically retrain or approximate removal using certified unlearning algorithms.
 #11.2.3    Level: 2    Role: V
 Verify that the shadow-model evaluation demonstrates that forgotten records influence less than 1% of outputs after unlearning.
 #11.2.4    Level: 3    Role: V
 Verify that deletion events are immutably logged and can be audited by regulators.

---

### 11.3 Differential Privacy Safeguards

 #11.3.1    Level: 2    Role: D/V
 Verify that the privacy-loss accounting dashboards alert when the cumulative ε exceeds policy thresholds.
 #11.3.2    Level: 2    Role: V
 Verify that black-box privacy audits estimate ε̂ within 10% of the declared value.
 #11.3.3    Level: 3    Role: V
 Ensure that formal proofs encompass all post-training fine-tuning processes and embeddings.

---

### 11.4 Purpose Limitation & Scope Creep Protection

 #11.4.1    Level: 1    Role: D
 Ensure that every dataset and model checkpoint includes a machine-readable purpose tag that aligns with the original consent.
 #11.4.2    Level: 1    Role: D/V
 Verify that runtime monitors detect queries inconsistent with the declared purpose and trigger a soft refusal.
 #11.4.3    Level: 3    Role: D
 Verify that policy-as-code gates prevent redeployment of models to new domains without a DPIA review.
 #11.4.4    Level: 3    Role: V
 Ensure that formal traceability proofs demonstrate that every personal data lifecycle stays within the consented scope.

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
 Verify that client updates use local differential privacy noise addition before aggregation.
 #11.6.2    Level: 2    Role: D/V
 Ensure that training metrics are differentially private and never disclose the loss of any single client.
 #11.6.3    Level: 2    Role: V
 Ensure that poisoning-resistant aggregation methods (e.g., Krum or Trimmed-Mean) are enabled.
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

This section outlines the requirements for providing real-time and forensic visibility into what the model and other AI components observe, perform, and return, enabling threats to be detected, prioritized, and analyzed for learning.

### C12.1 Request and Response Logging

 #12.1.1    Level: 1    Role: D/V
 Ensure that all user prompts and model responses are logged with the appropriate metadata (e.g., timestamp, user ID, session ID, model version).
 #12.1.2    Level: 1    Role: D/V
 Verify that logs are stored in secure, access-controlled repositories with appropriate retention policies and backup procedures.
 #12.1.3    Level: 1    Role: D/V
 Verify that log storage systems implement encryption both at rest and in transit to protect sensitive information contained in the logs.
 #12.1.4    Level: 1    Role: D/V
 Ensure that sensitive data in prompts and outputs is automatically redacted or masked before logging, with configurable redaction rules for PII, credentials, and proprietary information.
 #12.1.5    Level: 2    Role: D/V
 Ensure that policy decisions and safety filtering actions are logged with enough detail to allow for auditing and debugging of content moderation systems.
 #12.1.6    Level: 2    Role: D/V
 Ensure that log integrity is protected through methods such as cryptographic signatures or write-only storage.

---

### C12.2 Abuse Detection and Alerting

 #12.2.1    Level: 1    Role: D/V
 Verify that the system detects and alerts on known jailbreak patterns, prompt injection attempts, and adversarial inputs using signature-based detection.
 #12.2.2    Level: 1    Role: D/V
 Verify that the system integrates with existing Security Information and Event Management (SIEM) platforms using standard log formats and protocols.
 #12.2.3    Level: 2    Role: D/V
 Verify that enriched security events include AI-specific context like model identifiers, confidence scores, and safety filter decisions.
 #12.2.4    Level: 2    Role: D/V
 Verify that behavioral anomaly detection identifies unusual conversation patterns, excessive retry attempts, or systematic probing behaviors.
 #12.2.5    Level: 2    Role: D/V
 Ensure that real-time alerting systems notify security teams promptly when potential policy violations or attack attempts are detected.
 #12.2.6    Level: 2    Role: D/V
 Verify that custom rules are included to detect AI-specific threat patterns, including coordinated jailbreak attempts, prompt injection campaigns, and model extraction attacks.
 #12.2.7    Level: 3    Role: D/V
 Ensure that automated incident response workflows can isolate compromised models, block malicious users, and escalate critical security events.

---

### C12.3 Model Drift Detection

 #12.3.1    Level: 1    Role: D/V
 Verify that the system tracks basic performance metrics, including accuracy, confidence scores, latency, and error rates, across different model versions and time periods.
 #12.3.2    Level: 2    Role: D/V
 Verify that automated alerts trigger when performance metrics exceed predefined degradation thresholds or significantly deviate from baselines.
 #12.3.3    Level: 2    Role: D/V
 Ensure that hallucination detection monitors recognize and flag instances where model outputs include factually incorrect, inconsistent, or fabricated information.

---

### C12.4 Performance and Behavior Telemetry

 #12.4.1    Level: 1    Role: D/V
 Ensure that operational metrics, including request latency, token consumption, memory usage, and throughput, are continuously collected and monitored.
 #12.4.2    Level: 1    Role: D/V
 Verify that success and failure rates are tracked, including categorization of error types and their root causes.
 #12.4.3    Level: 2    Role: D/V
 Verify that resource utilization monitoring includes GPU and CPU usage, memory consumption, and storage requirements, with alerts triggered when thresholds are breached.

---

### C12.5 AI Incident Response Planning and Execution

 #12.5.1    Level: 1    Role: D/V
 Ensure that incident response plans specifically address AI-related security events such as model compromise, data poisoning, and adversarial attacks.
 #12.5.2    Level: 2    Role: D/V
 Ensure that incident response teams have access to AI-specific forensic tools and expertise to investigate model behavior and attack vectors.
 #12.5.3    Level: 3    Role: D/V
 Verify that post-incident analysis includes considerations for model retraining, updates to safety filters, and the integration of lessons learned into security controls.

---

### C12.5 AI Performance Degradation Detection

Monitor and detect declines in AI model performance and quality over time.

 #12.5.1    Level: 1    Role: D/V
 Ensure that model accuracy, precision, recall, and F1 scores are continuously monitored and compared against baseline thresholds.
 #12.5.2    Level: 1    Role: D/V
 Ensure that data drift detection monitors changes in input distribution that could affect model performance.
 #12.5.3    Level: 2    Role: D/V
 Confirm that concept drift detection recognizes changes in the relationship between inputs and expected outputs.
 #12.5.4    Level: 2    Role: D/V
 Verify that performance degradation triggers automated alerts and initiates workflows for model retraining or replacement.
 #12.5.5    Level: 3    Role: V
 Verify that degradation root cause analysis correlates performance declines with data changes, infrastructure issues, or external factors.

---

### C12.6 DAG Visualization & Workflow Security

Protect workflow visualization systems from information leaks and manipulation attacks.

 #12.6.1    Level: 1    Role: D/V
 Ensure that DAG visualization data is sanitized to remove any sensitive information before it is stored or transmitted.
 #12.6.2    Level: 1    Role: D/V
 Verify that workflow visualization access controls ensure that only authorized users can view agent decision paths and reasoning traces.
 #12.6.3    Level: 2    Role: D/V
 Verify that DAG data integrity is protected through cryptographic signatures and tamper-evident storage mechanisms.
 #12.6.4    Level: 2    Role: D/V
 Verify that workflow visualization systems implement input validation to prevent injection attacks via crafted node or edge data.
 #12.6.5    Level: 3    Role: D/V
 Ensure that real-time DAG updates are rate-limited and validated to prevent denial-of-service attacks on visualization systems.

---

### C12.7 Proactive Security Behavior Monitoring

Detection and prevention of security threats through proactive analysis of agent behavior.

 #12.7.1    Level: 1    Role: D/V
 Ensure that proactive agent behaviors are security-validated before execution by integrating risk assessments.
 #12.7.2    Level: 2    Role: D/V
 Verify that autonomous initiative triggers include the evaluation of the security context and the assessment of the threat landscape.
 #12.7.3    Level: 2    Role: D/V
 Ensure that proactive behavior patterns are analyzed for potential security implications and unintended consequences.
 #12.7.4    Level: 3    Role: D/V
 Ensure that security-critical proactive actions require explicit approval chains with accompanying audit trails.
 #12.7.5    Level: 3    Role: D/V
 Verify that behavioral anomaly detection identifies deviations in proactive agent patterns that may indicate a compromise.

---

### References

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Human Oversight, Accountability, and Governance

### Control Objective

This chapter outlines the requirements for maintaining human oversight and clear accountability chains in AI systems, ensuring explainability, transparency, and ethical stewardship throughout the AI lifecycle.

---

### C13.1 Kill-Switch & Override Mechanisms

Provide shutdown or rollback procedures when unsafe behavior of the AI system is detected.

 #13.1.1    Level: 1    Role: D/V
 Confirm that a manual kill-switch mechanism is in place to instantly stop AI model inference and outputs.
 #13.1.2    Level: 1    Role: D
 Verify that override controls are accessible only to authorized personnel.
 #13.1.3    Level: 3    Role: D/V
 Ensure that rollback procedures can revert to previous model versions or safe-mode operations.
 #13.1.4    Level: 3    Role: V
 Ensure that override mechanisms are regularly tested.

---

### C13.2 Human-in-the-Loop Decision Checkpoints

Require human approval when stakes exceed predefined risk thresholds.

 #13.2.1    Level: 1    Role: D/V
 Ensure that high-risk AI decisions receive explicit human approval before being executed.
 #13.2.2    Level: 1    Role: D
 Ensure that risk thresholds are clearly defined and automatically initiate human review workflows.
 #13.2.3    Level: 2    Role: D
 Ensure that time-sensitive decisions have fallback procedures in place when human approval cannot be obtained within the required timeframes.
 #13.2.4    Level: 3    Role: D/V
 Verify that escalation procedures clearly define authority levels for different types of decisions or risk categories, if applicable.

---

### C13.3 Chain of Responsibility & Auditability

Log operator actions and model decisions.

 #13.3.1    Level: 1    Role: D/V
 Ensure that all AI system decisions and human interventions are logged with timestamps, user identities, and the rationale behind each decision.
 #13.3.2    Level: 2    Role: D
 Ensure that audit logs cannot be altered and incorporate integrity verification mechanisms.

---

### C13.4 Explainable AI Techniques

Surface feature importance, counterfactuals, and local explanations.

 #13.4.1    Level: 1    Role: D/V
 Ensure that AI systems provide basic explanations for their decisions in a human-readable format.
 #13.4.2    Level: 2    Role: V
 Verify that the quality of explanations is validated through human evaluation studies and metrics.
 #13.4.3    Level: 3    Role: D/V
 Verify that feature importance scores or attribution methods (such as SHAP, LIME, etc.) are available for critical decisions.
 #13.4.4    Level: 3    Role: V
 Verify that counterfactual explanations demonstrate how inputs could be modified to change outcomes, if applicable to the use case and domain.

---

### C13.5 Model Cards and Usage Disclosures

Maintain model cards to document intended use, performance metrics, and ethical considerations.

 #13.5.1    Level: 1    Role: D
 Ensure that model cards document the intended use cases, limitations, and known failure modes.
 #13.5.2    Level: 1    Role: D/V
 Verify that performance metrics for various relevant use cases are disclosed.
 #13.5.3    Level: 2    Role: D
 Ensure that ethical considerations, bias assessments, fairness evaluations, training data characteristics, and known training data limitations are documented and regularly updated.
 #13.5.4    Level: 2    Role: D/V
 Ensure that model cards are version-controlled and maintained throughout the model lifecycle with change tracking.

---

### C13.6 Uncertainty Quantification

Propagate confidence scores or entropy measures in the responses.

 #13.6.1    Level: 1    Role: D
 Verify that AI systems provide confidence scores or uncertainty measures with their outputs.
 #13.6.2    Level: 2    Role: D/V
 Ensure that uncertainty thresholds prompt additional human review or alternative decision pathways.
 #13.6.3    Level: 2    Role: V
 Verify that uncertainty quantification methods are calibrated and validated using ground truth data.
 #13.6.4    Level: 3    Role: D/V
 Ensure that uncertainty propagation is preserved throughout multi-step AI workflows.

---

### C13.7 User-Facing Transparency Reports

Provide periodic disclosures on incidents, drift, and data usage.

 #13.7.1    Level: 1    Role: D/V
 Ensure that data usage policies and user consent management practices are clearly communicated to stakeholders.
 #13.7.2    Level: 2    Role: D/V
 Verify that AI impact assessments are conducted and that the results are included in the reports.
 #13.7.3    Level: 2    Role: D/V
 Ensure that transparency reports published regularly disclose AI incidents and operational metrics with reasonable detail.

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

This comprehensive glossary offers definitions of key AI, ML, and security terms used throughout the AISVS to ensure clarity and a common understanding.

Adversarial Example: An input intentionally designed to cause an AI model to make an error, often by adding subtle perturbations that are imperceptible to humans.
​
Adversarial Robustness – In AI, adversarial robustness refers to a model's ability to maintain its performance and resist being tricked or manipulated by intentionally crafted malicious inputs designed to cause errors.
​
Agent – AI agents are software systems that utilize AI to achieve goals and complete tasks on behalf of users. They demonstrate reasoning, planning, and memory, and possess a degree of autonomy to make decisions, learn, and adapt.
​
Agentic AI: AI systems capable of operating with a certain degree of autonomy to achieve goals, often making decisions and taking actions without direct human intervention.
​
Attribute-Based Access Control (ABAC): An access control model where authorization decisions are based on the attributes of the user, resource, action, and environment, evaluated at the time of the request.
​
Backdoor Attack: A type of data poisoning attack in which the model is trained to respond in a specific way to certain triggers, while behaving normally otherwise.
​
Bias: Systematic errors in AI model outputs that can result in unfair or discriminatory outcomes for certain groups or specific contexts.
​
Bias Exploitation: An attack technique that leverages known biases in AI models to manipulate outputs or outcomes.
​
Cedar: Amazon's policy language and engine for fine-grained permissions used to implement ABAC in AI systems.
​
Chain of Thought: A technique to enhance reasoning in language models by generating intermediate reasoning steps before delivering a final answer.
​
Circuit Breakers: Mechanisms that automatically stop AI system operations when specific risk thresholds are exceeded.
​
Data Leakage: Unintended exposure of sensitive information through AI model outputs or behavior.
​
Data Poisoning: The intentional corruption of training data to compromise model integrity, often to install backdoors or degrade performance.
​
Differential Privacy – Differential privacy is a mathematically rigorous framework for releasing statistical information about datasets while protecting the privacy of individual data subjects. It allows a data holder to share aggregate group patterns while limiting the information leaked about specific individuals.
​
Embeddings: Dense vector representations of data (text, images, etc.) that capture semantic meaning in a high-dimensional space.
​
Explainability – In AI, explainability refers to the ability of an AI system to provide reasons for its decisions and predictions that are understandable to humans, offering insights into its internal processes.
​
Explainable AI (XAI): AI systems designed to offer human-understandable explanations for their decisions and behaviors using various techniques and frameworks.
​
Federated Learning: A machine learning approach in which models are trained across multiple decentralized devices that hold local data samples, without exchanging the data itself.
​
Guardrails: Constraints implemented to prevent AI systems from generating harmful, biased, or otherwise undesirable outputs.
​
Hallucination – An AI hallucination refers to a phenomenon in which an AI model produces incorrect or misleading information that is not grounded in its training data or factual reality.
​
Human-in-the-Loop (HITL): Systems designed to require human oversight, verification, or intervention at critical decision points.
​
Infrastructure as Code (IaC): Managing and provisioning infrastructure through code instead of manual processes, enabling security scanning and consistent deployments.
​
Jailbreak: Techniques used to bypass safety guardrails in AI systems, especially in large language models, in order to generate prohibited content.
​
Least Privilege: The security principle of granting users and processes only the minimum necessary access rights.
​
LIME (Local Interpretable Model-agnostic Explanations): A technique used to explain the predictions of any machine learning classifier by locally approximating it with an interpretable model.
​
Membership Inference Attack: An attack designed to determine whether a specific data point was included in the training data of a machine learning model.
​
MITRE ATLAS: Adversarial Threat Landscape for Artificial Intelligence Systems; a knowledge base of adversarial tactics and techniques targeting AI systems.
​
Model Card – A model card is a document that provides standardized information about an AI model’s performance, limitations, intended uses, and ethical considerations to promote transparency and responsible AI development.
​
Model Extraction: An attack in which an adversary repeatedly queries a target model to create an unauthorized, functionally similar copy.
​
Model Inversion: An attack that tries to reconstruct training data by analyzing the model’s outputs.
​
Model Lifecycle Management – AI Model Lifecycle Management involves supervising all phases of an AI model's existence, including its design, development, deployment, monitoring, maintenance, and eventual retirement, to ensure it stays effective and aligned with its objectives.
​
Model Poisoning: Introducing vulnerabilities or backdoors directly into a model during the training process.
​
Model Stealing/Theft: Obtaining a copy or an approximation of a proprietary model by making repeated queries.
​
Multi-agent System: A system composed of multiple interacting AI agents, each potentially possessing different capabilities and goals.
​
OPA (Open Policy Agent): An open-source policy engine that enables unified policy enforcement across the entire stack.
​
Privacy-Preserving Machine Learning (PPML): Techniques and methods for training and deploying ML models while safeguarding the privacy of the training data.
​
Prompt Injection: An attack in which malicious instructions are embedded in inputs to override a model's intended behavior.
​
RAG (Retrieval-Augmented Generation): A technique that improves large language models by retrieving relevant information from external knowledge sources before generating a response.
​
Red Teaming: The practice of actively testing AI systems by simulating adversarial attacks to identify vulnerabilities.
​
SBOM (Software Bill of Materials): A formal record that includes the details and supply chain relationships of various components used in building software or AI models.
​
SHAP (SHapley Additive exPlanations): A game-theoretic approach for explaining the output of any machine learning model by calculating the contribution of each feature to the prediction.
​
Supply Chain Attack: Compromising a system by targeting less secure components in its supply chain, such as third-party libraries, datasets, or pre-trained models.
​
Transfer Learning: A technique in which a model developed for one task is reused as the starting point for a model on a second task.
​
Vector Database: A specialized database designed to store high-dimensional vectors (embeddings) and perform efficient similarity searches.
​
Vulnerability Scanning: Automated tools that detect known security vulnerabilities in software components, including AI frameworks and dependencies.
​
Watermarking: Techniques for embedding imperceptible markers in AI-generated content to track its origin or detect AI generation.
​
Zero-Day Vulnerability: A previously unknown security flaw that attackers can exploit before developers create and release a patch.

## Appendix B: References

### TODO

## Appendix C: AI Security Governance & Documentation

### Objective

This appendix outlines the fundamental requirements for creating organizational structures, policies, and processes to manage AI security throughout the system lifecycle.

---

### AC.1 AI Risk Management Framework Adoption

Provide a formal framework to identify, assess, and mitigate AI-specific risks throughout the system lifecycle.

 #AC.1.1    Level: 1    Role: D/V
 Verify that an AI-specific risk assessment methodology is documented and implemented.
 #AC.1.2    Level: 2    Role: D
 Ensure that risk assessments are conducted at critical stages in the AI lifecycle and before any significant changes.
 #AC.1.3    Level: 3    Role: D/V
 Verify that the risk management framework aligns with established standards (e.g., NIST AI RMF).

---

### AC.2 AI Security Policy and Procedures

Establish and enforce organizational standards for the secure development, deployment, and operation of AI.

 #AC.2.1    Level: 1    Role: D/V
 Verify that documented AI security policies are in place.
 #AC.2.2    Level: 2    Role: D
 Verify that policies are reviewed and updated at least once a year and following significant changes in the threat landscape.
 #AC.2.3    Level: 3    Role: D/V
 Verify that policies cover all AISVS categories and comply with applicable regulatory requirements.

---

### AC.3 Roles and Responsibilities for AI Security

Establish clear accountability for AI security throughout the organization.

 #AC.3.1    Level: 1    Role: D/V
 Verify that AI security roles and responsibilities are properly documented.
 #AC.3.2    Level: 2    Role: D
 Ensure that responsible individuals have the appropriate security expertise.
 #AC.3.3    Level: 3    Role: D/V
 Ensure that an AI ethics committee or governance board is established for high-risk AI systems.

---

### AC.4 Enforcement of Ethical AI Guidelines

Ensure AI systems operate according to established ethical principles.

 #AC.4.1    Level: 1    Role: D/V
 Confirm that ethical guidelines for AI development and deployment are in place.
 #AC.4.2    Level: 2    Role: D
 Ensure that mechanisms are in place to detect and report ethical violations.
 #AC.4.3    Level: 3    Role: D/V
 Ensure that regular ethical reviews of deployed AI systems are conducted.

---

### AC.5 AI Regulatory Compliance Monitoring

Stay informed about and comply with evolving AI regulations.

 #AC.5.1    Level: 1    Role: D/V
 Ensure that processes are in place to identify applicable AI regulations.
 #AC.5.2    Level: 2    Role: D
 Verify that compliance with all regulatory requirements has been assessed.
 #AC.5.3    Level: 3    Role: D/V
 Ensure that regulatory changes prompt timely reviews and updates of AI systems.

### AC.6 Training Data Governance, Documentation, and Process

 #1.1.2    Level: 1    Role: D/V
 Ensure that only datasets verified for quality, representativeness, ethical sourcing, and license compliance are used, minimizing risks of data poisoning, embedded bias, and intellectual property infringement.
 #1.1.5    Level: 2    Role: D/V
 Verify that labeling/annotation quality is ensured through reviewer cross-checks or consensus.
 #1.1.6    Level: 2    Role: D/V
 Ensure that "data cards" or "datasheets for datasets" are maintained for significant training datasets, providing details on characteristics, motivations, composition, collection processes, preprocessing, and recommended or discouraged uses.
 #1.3.2    Level: 2    Role: D/V
 Verify that the identified biases are mitigated using documented strategies such as re-balancing, targeted data augmentation, algorithmic adjustments (e.g., pre-processing, in-processing, post-processing techniques), or re-weighting, and ensure that the impact of mitigation on both fairness and overall model performance is assessed.
 #1.3.3    Level: 2    Role: D/V
 Ensure that post-training fairness metrics are evaluated and documented.
 #1.3.4    Level: 3    Role: D/V
 Verify that a lifecycle bias management policy designates owners and establishes a review cadence.
 #1.4.1    Level: 2    Role: D/V
 Ensure labeling and annotation quality through clear guidelines, reviewer cross-checks, consensus mechanisms (such as monitoring inter-annotator agreement), and established processes for resolving discrepancies.
 #1.4.4    Level: 3    Role: D/V
 Ensure that labels critical to safety, security, or fairness (e.g., identifying toxic content or critical medical findings) undergo mandatory independent dual review or an equivalent robust verification process.
 #1.4.6    Level: 2    Role: D/V
 Ensure that labeling guides and instructions are thorough, version-controlled, and peer-reviewed.
 #1.4.6    Level: 2    Role: D/V
 Ensure that data schemas for labels are clearly defined and version-controlled.
 #1.3.1    Level: 1    Role: D/V
 Verify that datasets are analyzed for representational imbalance and potential biases across legally protected attributes (e.g., race, gender, age) and other ethically sensitive characteristics relevant to the model’s application domain (e.g., socio-economic status, location).
 #1.5.3    Level: 2    Role: V
 Ensure that manual spot-checks conducted by domain experts cover a statistically significant sample size (e.g., ≥1% or 1,000 samples, whichever is greater, or as determined by a risk assessment) to detect subtle quality issues that automation might miss.
 #1.8.4    Level: 2    Role: D/V
 Verify that outsourced or crowdsourced labeling workflows incorporate technical and procedural safeguards to ensure data confidentiality, integrity, label quality, and to prevent data leakage.
 #1.5.4    Level: 2    Role: D/V
 Verify that remediation steps are appended to the provenance records.
 #1.6.2    Level: 2    Role: D/V
 Confirm that flagged samples initiate manual review before training.
 #1.6.3    Level: 2    Role: V
 Verify that the results feed into the model's security dossier and inform ongoing threat intelligence.
 #1.6.4    Level: 3    Role: D/V
 Verify that the detection logic is updated with new threat intelligence.
 #1.6.5    Level: 3    Role: D/V
 Ensure that online learning pipelines monitor for distribution drift.
 #1.7.1    Level: 1    Role: D/V
 Verify that training data deletion workflows remove both primary and derived data, assess the impact on the model, and, if necessary, address the impact on affected models (e.g., through retraining or recalibration).
 #1.7.2    Level: 2    Role: D
 Ensure that mechanisms are in place to track and honor the scope and status of user consent (including withdrawals) for data used in training, and verify that consent is validated before the data is incorporated into new training processes or major model updates.
 #1.7.3    Level: 2    Role: V
 Ensure that workflows are tested annually and properly logged.
 #1.8.1    Level: 2    Role: D/V
 Ensure that third-party data suppliers, including providers of pre-trained models and external datasets, undergo due diligence for security, privacy, ethical sourcing, and data quality before their data or models are integrated.
 #1.8.2    Level: 1    Role: D
 Verify that external transfers utilize TLS/authentication and integrity checks.
 #1.8.3    Level: 2    Role: D/V
 Ensure that high-risk data sources (e.g., open-source datasets with unknown provenance or unvetted suppliers) undergo enhanced scrutiny—such as sandboxed analysis, thorough quality and bias assessments, and targeted poisoning detection—before being used in sensitive applications.
 #1.8.4    Level: 3    Role: D/V
 Verify that pre-trained models obtained from third parties are evaluated for embedded biases, potential backdoors, the integrity of their architecture, and the provenance of their original training data before fine-tuning or deployment.
 #1.5.3    Level: 2    Role: D/V
 Verify that when adversarial training is used, the generation, management, and versioning of adversarial datasets are properly documented and controlled.
 #1.5.3    Level: 3    Role: D/V
 Ensure that the impact of adversarial robustness training on model performance (for both clean and adversarial inputs) and fairness metrics is evaluated, documented, and monitored.
 #1.5.4    Level: 3    Role: D/V
 Ensure that strategies for adversarial training and robustness are periodically reviewed and updated to address evolving adversarial attack techniques.
 #1.4.2    Level: 2    Role: D/V
 Verify that failed datasets are quarantined with audit trails.
 #1.4.3    Level: 2    Role: D/V
 Verify that quality gates block subpar datasets unless exceptions are approved.
 #1.11.2    Level: 2    Role: D/V
 Ensure that the generation process, parameters, and intended use of synthetic data are thoroughly documented.
 #1.11.3    Level: 2    Role: D/V
 Ensure that synthetic data undergoes a risk assessment for bias, privacy leakage, and representational issues before being used for training.
 #1.12.3    Level: 2    Role: D/V
 Verify that alerts are generated for suspicious access events and investigated promptly.
 #1.13.1    Level: 1    Role: D/V
 Verify that explicit retention periods are established for all training datasets.
 #1.13.2    Level: 2    Role: D/V
 Verify that datasets are automatically expired, deleted, or reviewed for deletion at the end of their lifecycle.
 #1.13.3    Level: 2    Role: D/V
 Ensure that retention and deletion actions are logged and can be audited.
 #1.14.1    Level: 2    Role: D/V
 Ensure that data residency and cross-border transfer requirements are identified and enforced for all datasets.
 #1.14.2    Level: 2    Role: D/V
 Verify that sector-specific regulations (e.g., healthcare, finance) are identified and properly addressed in data handling.
 #1.14.3    Level: 2    Role: D/V
 Ensure that compliance with applicable privacy laws (e.g., GDPR, CCPA) is documented and reviewed regularly.
 #1.16.1    Level: 2    Role: D/V
 Verify that mechanisms are in place to respond to data subject requests for access, rectification, restriction, or objection.
 #1.16.2    Level: 2    Role: D/V
 Verify that requests are logged, tracked, and fulfilled within legally mandated timeframes.
 #1.16.3    Level: 2    Role: D/V
 Verify that data subject rights processes are regularly tested and reviewed for effectiveness.
 #1.17.1    Level: 2    Role: D/V
 Ensure that an impact analysis is conducted before updating or replacing a dataset version, addressing model performance, fairness, and compliance.
 #1.17.2    Level: 2    Role: D/V
 Ensure that the results of the impact analysis are documented and reviewed by the appropriate stakeholders.
 #1.17.3    Level: 2    Role: D/V
 Verify that rollback plans are in place in case new versions introduce unacceptable risks or regressions.
 #1.18.1    Level: 2    Role: D/V
 Verify that all personnel involved in data annotation have undergone background checks and are trained in data security and privacy.
 #1.18.2    Level: 2    Role: D/V
 Ensure that all annotation personnel sign confidentiality and non-disclosure agreements.
 #1.18.3    Level: 2    Role: D/V
 Ensure that annotation platforms enforce access controls and monitor for insider threats.

#### References

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Appendix D: AI-Assisted Secure Coding Governance and Verification

### Objective

This chapter defines baseline organizational controls for the safe and effective use of AI-assisted coding tools during software development, ensuring security and traceability throughout the SDLC.

---

### AD.1 AI-Assisted Secure-Coding Workflow

Integrate AI tools into the organization’s secure software development lifecycle (SSDLC) without compromising existing security measures.

 #AD.1.1    Level: 1    Role: D/V
 Ensure that a documented workflow specifies when and how AI tools can generate, refactor, or review code.
 #AD.1.2    Level: 2    Role: D
 Verify that the workflow corresponds to each SSDLC phase (design, implementation, code review, testing, deployment).
 #AD.1.3    Level: 3    Role: D/V
 Verify that metrics (e.g., vulnerability density, mean time to detect) are collected on AI-generated code and compared to human-only baselines.

---

### AD.2 AI Tool Qualification & Threat Modeling

Ensure that AI coding tools are evaluated for security capabilities, risks, and supply-chain impact before adoption.

 #AD.2.1    Level: 1    Role: D/V
 Ensure that the threat model for each AI tool identifies risks related to misuse, model inversion, data leakage, and dependency chains.
 #AD.2.2    Level: 2    Role: D
 Ensure that tool evaluations include both static and dynamic analysis of any local components, as well as an assessment of SaaS endpoints covering TLS, authentication/authorization, and logging.
 #AD.2.3    Level: 3    Role: D/V
 Ensure that evaluations adhere to a recognized framework and are re-conducted after major version updates.

---

### AD.3 Secure Prompt and Context Management

Prevent the leakage of secrets, proprietary code, and personal data when creating prompts or contexts for AI models.

 #AD.3.1    Level: 1    Role: D/V
 Confirm that written guidelines prohibit including secrets, credentials, or classified data in prompts.
 #AD.3.2    Level: 2    Role: D
 Verify that technical controls (client-side redaction, approved context filters) automatically remove sensitive artifacts.
 #AD.3.3    Level: 3    Role: D/V
 Verify that prompts and responses are tokenized and encrypted both in transit and at rest, and ensure that retention periods comply with the data classification policy.

---

### AD.4 Validation of AI-Generated Code

Detect and fix vulnerabilities introduced by AI-generated output before the code is merged or deployed.

 #AD.4.1    Level: 1    Role: D/V
 Ensure that AI-generated code is always subject to human code review.
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
 Ensure that developers can display model citations (training snippets, documentation) that support a suggestion.
 #AD.5.3    Level: 3    Role: D/V
 Verify that explainability reports are stored with design artifacts and referenced in security reviews, meeting ISO/IEC 42001 traceability principles.

---

### AD.6 Continuous Feedback & Model Fine-Tuning

Enhance model security performance over time while preventing negative drift.

 #AD.6.1    Level: 1    Role: D/V
 Verify that developers can flag insecure or non-compliant suggestions and that these flags are tracked.
 #AD.6.2    Level: 2    Role: D
 Ensure that aggregated feedback guides periodic fine-tuning or retrieval-augmented generation using vetted secure coding corpora (e.g., OWASP Cheat Sheets).
 #AD.6.3    Level: 3    Role: D/V
 Verify that a closed-loop evaluation harness runs regression tests after each fine-tuning; security metrics must meet or exceed previous baselines before deployment.

---

#### References

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Appendix E: Sample Tools and Frameworks

### Objective

This chapter provides examples of tools and frameworks that can assist in implementing or fulfilling a specific AISVS requirement. These examples should not be considered recommendations or endorsements by the AISVS team or the OWASP GenAI Security Project.

---

### AE.1 Training Data Governance and Bias Management

Tools used for data analytics, governance, and bias management.

 #AE.1.1    Section: 1.1
 Data Inventory Tooling: Tools for managing data inventory such as...
 #AE.1.2    Section: 1.2
 Encryption In Transit: Use TLS for HTTPS-based applications, with tools like OpenSSL and Python's`ssl`library.

---

### AE.2 User Input Validation

Tooling to handle and validate user inputs.

 #AE.2.1    Section: 2.1
 Prompt Injection Defense Tooling: Use guardrail tools such as NVIDIA's NeMo or Guardrails AI.

---

