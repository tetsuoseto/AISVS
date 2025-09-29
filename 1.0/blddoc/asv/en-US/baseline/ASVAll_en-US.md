## Frontispiece

### About the Standard

The Artificial Intelligence Security Verification Standard (AISVS) is a community-driven catalog of security requirements that data scientists, MLOps engineers, software architects, developers, testers, security professionals, tool vendors, regulators, and consumers can use to design, build, test, and verify trustworthy AI-enabled systems and applications. It provides a common language for specifying security controls throughout the AI lifecycle—from data collection and model development to deployment and ongoing monitoring—allowing organizations to measure and improve the resilience, privacy, and safety of their AI solutions.

### Copyright and License

Version 0.1 (First Public Draft - Work in Progress), 2025  

![license](images/license.png)
Copyright © 2025 The AISVS Project.  

Released under theCreative Commons Attribution‑ShareAlike 4.0 International License.
For any reuse or distribution, you must clearly communicate the license terms of this work to others.

### Project Leads

Jim Manico
Aras "Russ" Memisyazici

### Contributors and Reviewers

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS is a brand-new standard created specifically to address the unique security challenges of artificial intelligence systems. While it draws inspiration from broader security best practices, every requirement in AISVS has been developed from the ground up to reflect the AI threat landscape and help organizations build safer, more resilient AI solutions.

## Preface

Welcome to version 1.0 of the Artificial Intelligence Security Verification Standard (AISVS)!

### Introduction

Established in 2025 through a collaborative community effort, AISVS defines the security requirements to consider when designing, developing, deploying, and operating modern AI models, pipelines, and AI-enabled services.

AISVS v1.0 represents the collaborative effort of its project leads, working group, and broader community contributors to create a practical, testable baseline for securing AI systems.

Our goal with this release is to make AISVS easy to adopt while remaining sharply focused on its defined scope and addressing the rapidly evolving risk landscape unique to AI.

### Key Objectives for AISVS Version 1.0

Version 1.0 will be developed based on several guiding principles.

#### Well-Defined Scope

Each requirement must align with AISVS's name and mission:

Artificial Intelligence – Controls operate at the AI/ML layer (data, model, pipeline, or inference) and are the responsibility of AI practitioners.
Security – Requirements directly address identified security, privacy, or safety risks.
Verification – The language is written to allow objective validation of conformance.
Standard – Sections follow a consistent structure and terminology to create a coherent reference.
​
---

By following AISVS, organizations can systematically assess and enhance the security posture of their AI solutions, promoting a culture of secure AI engineering.

## Using the AISVS

The Artificial Intelligence Security Verification Standard (AISVS) defines security requirements for modern AI applications and services, focusing on elements within the control of application developers.

The AISVS is designed for anyone involved in developing or assessing the security of AI applications, including developers, architects, security engineers, and auditors. This chapter introduces the structure and usage of the AISVS, covering its verification levels and intended use cases.

### Artificial Intelligence Security Verification Levels

The AISVS defines three ascending levels of security verification. Each level adds depth and complexity, allowing organizations to tailor their security posture to the risk level of their AI systems.

Organizations may start at Level 1 and progressively move to higher levels as their security maturity and threat exposure increase.

#### Definition of the Levels

Each requirement in AISVS v1.0 is assigned to one of the following levels:

 Level 1 requirements

Level 1 includes the most critical and foundational security requirements. These focus on preventing common attacks that do not depend on other preconditions or vulnerabilities. Most Level 1 controls are either straightforward to implement or essential enough to warrant the effort.

 Level 2 requirements

Level 2 addresses more advanced or less common attacks, as well as layered defenses against widespread threats. These requirements may involve more complex logic or target specific attack prerequisites.

 Level 3 requirements

Level 3 includes controls that are generally more difficult to implement or applicable only in certain situations. These often serve as defense-in-depth measures or protections against specialized, targeted, or highly complex attacks.

#### Role (D/V)

Each AISVS requirement is designated according to the primary audience:

D – Developer-focused requirements
V – Requirements Focused on Verifiers/Auditors
D/V – Relevant to both developers and verifiers

## C1 Training Data Governance & Bias Management

### Control Objective

Training data must be sourced, handled, and maintained in a way that preserves provenance, security, quality, and fairness. Doing so fulfills legal obligations and reduces the risks of bias, poisoning, or privacy breaches that can arise during training and affect the entire AI lifecycle.

---

### C1.1 Training Data Provenance

Maintain a verifiable inventory of all datasets, accept only trusted sources, and log every change for auditing purposes.

 #1.1.1    Level: 1    Role: D/V
 Ensure that an up-to-date inventory is maintained for every training data source, including origin, steward/owner, license, collection method, intended use constraints, and processing history.
 #1.1.2    Level: 1    Role: D/V
 Ensure that training data processes exclude unnecessary features, attributes, or fields (e.g., unused metadata, sensitive PII, leaked test data).
 #1.1.3    Level: 2    Role: D/V
 Verify that all dataset changes undergo a logged approval workflow.
 #1.1.4    Level: 3    Role: D/V
 Verify that datasets or subsets are watermarked or fingerprinted where feasible.

---

### C1.2 Training Data Security and Integrity

Restrict access to training data, encrypt it both at rest and in transit, and verify its integrity to prevent tampering, theft, or data poisoning.

 #1.2.1    Level: 1    Role: D/V
 Verify that access controls safeguard training data storage and pipelines.
 #1.2.2    Level: 2    Role: D/V
 Ensure that all access to training data is logged, including the user, time, and action.
 #1.2.3    Level: 2    Role: D/V
 Ensure that training datasets are encrypted both in transit and at rest, employing industry-standard cryptographic algorithms and key management practices.
 #1.2.4    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are used to ensure data integrity during the storage and transfer of training data.
 #1.2.5    Level: 2    Role: D/V
 Verify that automated detection techniques are implemented to protect against unauthorized modifications or corruption of training data.
 #1.2.6    Level: 2    Role: D/V
 Verify that outdated training data is securely purged or anonymized.
 #1.2.7    Level: 3    Role: D/V
 Ensure that all versions of the training dataset are uniquely identified, stored in an immutable manner, and auditable to enable rollback and forensic analysis.

---

### C1.3 Training Data Labeling Quality, Integrity, and Security

Protect labels and require technical review for critical data.

 #1.3.1    Level: 2    Role: D/V
 Verify that cryptographic hashes or digital signatures are applied to label artifacts to ensure their integrity and authenticity.
 #1.3.2    Level: 2    Role: D/V
 Verify that labeling interfaces and platforms enforce robust access controls, maintain tamper-evident audit logs of all labeling activities, and protect against unauthorized modifications.
 #1.3.3    Level: 3    Role: D/V
 Verify that sensitive information in labels is redacted, anonymized, or encrypted at the data field level both at rest and in transit.

---

### C1.4 Training Data Quality and Security Assurance

Combine automated validation, manual spot checks, and logged remediation to ensure dataset reliability.

 #1.4.1    Level: 1    Role: D
 Verify that automated tests detect format errors and nulls in every ingest or significant data transformation.
 #1.4.2    Level: 2    Role: D/V
 Verify that LLM training and fine-tuning pipelines incorporate poisoning detection and data integrity validation (e.g., statistical methods, outlier detection, embedding analysis) to identify potential poisoning attacks (e.g., label flipping, backdoor trigger insertion, role-switching commands, influential instance attacks) or unintentional data corruption in the training data.
 #1.4.3    Level: 2    Role: D/V
 Ensure that automatically generated labels (e.g., from LLMs or weak supervision) undergo confidence thresholding and consistency checks to identify hallucinated, misleading, or low-confidence labels.
 #1.4.4    Level: 3    Role: D/V
 Verify that appropriate defenses, such as adversarial training (using generated adversarial examples), data augmentation with perturbed inputs, or robust optimization techniques, are implemented and properly tuned for relevant models based on the risk assessment.
 #1.4.5    Level: 3    Role: D
 Ensure that automated tests detect label skews during every data ingestion or major data transformation.

---

### C1.5 Data Lineage and Traceability

Track the entire journey of each data point from the source to the model input for auditability and incident response.

 #1.5.1    Level: 2    Role: D/V
 Ensure that the lineage of each data point, including all transformations, augmentations, and merges, is documented and can be fully reconstructed.
 #1.5.2    Level: 2    Role: D/V
 Ensure that lineage records are immutable, securely stored, and accessible for audits.
 #1.5.3    Level: 2    Role: D/V
 Ensure that lineage tracking includes synthetic data generated through privacy-preserving or generative techniques, and that all synthetic data is clearly labeled and distinguishable from real data throughout the entire pipeline.

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

Robust validation of user input is a primary defense against some of the most harmful attacks on AI systems. Prompt injection attacks can override system instructions, expose sensitive data, or direct the model toward prohibited behaviors. Without dedicated filters and other validation measures, research shows that jailbreaks exploiting context windows will continue to be effective.

---

### C2.1 Prompt Injection Defense

Prompt injection is one of the top risks for AI systems. Defenses against this tactic use a combination of pattern filters, data classifiers, and instruction hierarchy enforcement.

 #2.1.1    Level: 1    Role: D/V
 Verify that user inputs are screened against a continuously updated library of known prompt injection patterns, including jailbreak keywords, "ignore previous," and role-play chains.
 #2.1.2    Level: 1    Role: D/V
 Verify that the system enforces an instruction hierarchy where system messages override user instructions, even after processing the user instructions.
 #2.1.4    Level: 2    Role: D
 Ensure that prompts coming from third-party content (web pages, PDFs, emails) are sanitized separately before being combined into the main prompt.

---

### C2.2 Resistance to Adversarial Examples

Natural Language Processing (NLP) models remain vulnerable to subtle character- or word-level perturbations that humans often overlook but cause models to misclassify.

 #2.2.1    Level: 1    Role: D
 Ensure that basic input normalization steps—Unicode NFC, homoglyph mapping, and whitespace trimming—are performed before tokenization.
 #2.2.2    Level: 2    Role: D/V
 Verify that statistical anomaly detection flags inputs with unusually high edit distances from language norms or abnormal embedding distances.
 #2.2.3    Level: 2    Role: D
 Verify that the inference pipeline supports adversarial training–hardened model variants or defense layers (e.g., randomization, defensive distillation, alignment checks) for high-risk endpoints.
 #2.2.4    Level: 2    Role: V
 Ensure that suspected adversarial inputs are quarantined and logged with their full payloads.
 #2.2.5    Level: 2    Role: D/V
 Ensure that encoding and representation smuggling in both inputs and outputs (e.g., invisible Unicode/control characters, homoglyph swaps, or mixed-direction text) are detected and mitigated. Approved mitigation methods include canonicalization, strict schema validation, policy-based rejection, or explicit marking.

---

### C2.3 Schema, Type, and Length Validation

AI attacks involving malformed or oversized inputs can lead to parsing errors, prompt spillage across fields, and resource exhaustion. Strict schema enforcement is also essential when performing deterministic tool calls.

 #2.3.1    Level: 1    Role: D
 Ensure that every API or function call endpoint defines an explicit input schema (JSON Schema, Protobuf, or multimodal equivalent) and that inputs are validated before assembling the prompt.
 #2.3.2    Level: 1    Role: D/V
 Verify that inputs exceeding the maximum token or byte limits are rejected with a safe error message and are never silently truncated.
 #2.3.3    Level: 2    Role: D/V
 Verify that type checks (e.g., numeric ranges, enum values, MIME types for images/audio) are enforced on the server side.
 #2.3.4    Level: 2    Role: D
 Ensure that semantic validators (e.g., JSON Schema) execute in constant time to prevent algorithmic DoS attacks.
 #2.3.5    Level: 3    Role: V
 Verify that validation failures are logged with redacted payload snippets and clear error codes to support security triage.

---

### C2.4 Content and Policy Screening

Developers should be able to detect syntactically valid prompts that request disallowed content (such as illicit instructions, hate speech, and/or copyrighted text) and then prevent them from spreading.

 #2.4.1    Level: 1    Role: D
 Ensure that a content classifier (zero-shot or fine-tuned) evaluates every input for violence, self-harm, hate, sexual content, and illegal requests, with configurable thresholds.
 #2.4.2    Level: 1    Role: D/V
 Ensure that inputs violating policies receive standardized refusals or safe completions to prevent them from propagating to downstream LLM calls.
 #2.4.3    Level: 2    Role: D
 Ensure that screening complies with user-specific policies (such as age and regional legal restrictions) through attribute-based rules evaluated at the time of the request.
 #2.4.4    Level: 3    Role: V
 Verify that screening logs include classifier confidence scores and policy category tags for SOC correlation and future red team replay.

---

### C2.5 Input Rate Limiting and Abuse Prevention

Developers should prevent abuse, resource exhaustion, and automated attacks on AI systems by limiting input rates and detecting anomalous usage patterns.

 #2.5.1    Level: 1    Role: D/V
 Verify that rate limits per user, per IP, and per API key are enforced for all input endpoints.
 #2.5.2    Level: 2    Role: D/V
 Verify that burst and sustained rate limits are properly configured to prevent DoS and brute force attacks.
 #2.5.3    Level: 2    Role: D/V
 Verify that abnormal usage patterns (e.g., rapid-fire requests, input flooding) trigger automated blocks or escalations.
 #2.5.4    Level: 3    Role: V
 Verify that abuse prevention logs are retained and reviewed for emerging attack patterns.

---

### C2.6 Multi-Modal Input Validation

AI systems should incorporate robust validation for non-text inputs (images, audio, files) to prevent injection, evasion, or resource abuse.

 #2.6.1    Level: 1    Role: D
 Verify that all non-text inputs (images, audio, files) are validated for type, size, and format before processing.
 #2.6.2    Level: 2    Role: D/V
 Ensure that files are scanned for malware and steganographic payloads before ingestion.
 #2.6.3    Level: 2    Role: D/V
 Ensure that image and audio inputs are verified for adversarial perturbations or recognized attack patterns.
 #2.6.4    Level: 3    Role: V
 Ensure that multi-modal input validation failures are logged and generate alerts for investigation.
 #2.6.5    Level: 2    Role: D/V
 Verify that cross-modal attack detection can identify coordinated attacks across multiple input types (e.g., steganographic payloads in images combined with prompt injection in text) using correlation rules and alert generation.
 #2.6.6    Level: 3    Role: D/V
 Verify that multi-modal validation failures trigger detailed logging, including all input modalities, validation results, and threat scores.
---

### C2.7 Real-Time Adaptive Threat Detection

Developers should use advanced threat detection systems for AI that adapt to new attack patterns and offer real-time protection through compiled pattern matching.

 #2.7.1    Level: 1    Role: D/V
 Ensure that pattern matching (e.g., compiled regex) executes on all inputs with minimal latency impact.
 #2.8.3    Level: 2    Role: D/V
 Verify that adaptive detection models adjust their sensitivity based on recent attack activity and are updated with new patterns in real-time.
 #2.8.4    Level: 3    Role: D/V
 Verify that detection accuracy improves through contextual analysis of user history, source, and session behavior.
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

## C3 Model Lifecycle Management and Change Control

### Control Objective

AI systems must implement change control processes that prevent unauthorized or unsafe model modifications from reaching production. This control ensures model integrity throughout the entire lifecycle—from development through deployment to decommissioning—which enables rapid incident response and maintains accountability for all changes.

Core Security Goal: Only authorized, validated models are deployed to production through controlled processes that ensure integrity, traceability, and recoverability.

---

### C3.1 Model Authorization & Integrity

Only authorized models with verified integrity reach production environments.

 #3.1.1    Level: 1    Role: D/V
 Verify that all model artifacts (weights, configurations, tokenizers) are cryptographically signed by authorized entities before deployment.
 #3.1.2    Level: 2    Role: V
 Verify that dependency tracking maintains a real-time inventory that enables identification of all consuming systems.
 #3.1.3    Level: 3    Role: D/V
 Verify that model provenance records include the identity of the authorizing entity, training data checksums, validation test results with pass/fail status, and a creation timestamp.

---

### C3.2 Model Validation and Testing

Models must pass established security and safety validations before deployment.

 #3.2.1    Level: 1    Role: D/V
 Ensure that models undergo automated security testing, including input validation, output sanitization, and safety evaluations, meeting pre-agreed organizational pass/fail thresholds before deployment.
 #3.2.2    Level: 1    Role: V
 Verify that all model changes (deployment, configuration, retirement) generate immutable audit records that include a timestamp, authenticated actor identity, change type, and before/after states.
 #3.2.3    Level: 2    Role: D/V
 Verify that validation failures automatically prevent model deployment, even after explicit override approval from pre-designated authorized personnel with documented business justifications.

---

### C3.3 Controlled Deployment & Rollback

Model deployments must be controlled, monitored, and reversible.

 #3.3.1    Level: 1    Role: D/V
 Ensure that deployment processes validate cryptographic signatures and compute integrity checksums before activating the model, and fail the deployment if any mismatch occurs.
 #3.3.2    Level: 1    Role: D
 Verify that production deployments implement gradual rollout mechanisms (canary deployments, blue-green deployments) with automated rollback triggers based on predefined error rates, latency thresholds, or security alert criteria.
 #3.3.3    Level: 2    Role: D/V
 Verify that rollback capabilities restore the complete model state—including weights, configurations, and dependencies—atomically.
 #3.3.4    Level: 3    Role: D/V
 Verify that emergency model shutdown capabilities can disable model endpoints within a predefined response time.

---

### C3.4 Secure Development Practices

Model development and training processes must adhere to secure practices to prevent compromise.

 #3.4.1    Level: 1    Role: D/V
 Ensure that model development, testing, and production environments are physically or logically separated, with no shared infrastructure, distinct access controls, and isolated data stores.
 #3.4.2    Level: 1    Role: D
 Ensure that model development artifacts (hyperparameters, training scripts, configuration files, prompt templates, etc.) are stored in version control and require peer review approval before being used in training.
 #3.4.3    Level: 2    Role: D/V
 Ensure that model training and fine-tuning take place in isolated environments with controlled network access.
 #3.4.4    Level: 2    Role: D
 Verify that training data sources are validated through integrity checks and authenticated via trusted sources with a documented chain of custody before being used in model development.

---

### C3.5 Model Retirement & Decommissioning

Models must be securely retired when they are no longer needed or when security issues are detected.

 #3.5.1    Level: 1    Role: D/V
 Verify that retired model artifacts are securely erased using secure cryptographic erasure.
 #3.5.2    Level: 2    Role: V
 Verify that model retirement events are logged with a timestamp and the identity of the actor, and that model signatures are revoked to prevent reuse.

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

AI infrastructure must be secured against privilege escalation, supply chain tampering, and lateral movement by using secure configurations, runtime isolation, trusted deployment pipelines, and comprehensive monitoring. Only validated and authorized infrastructure components should reach production through controlled processes that guarantee security, integrity, and auditability.

Core Security Goal: Only cryptographically signed, vulnerability-scanned infrastructure components can reach production through automated validation pipelines that enforce security policies and maintain immutable audit trails.

---

### C4.1 Runtime Environment Isolation

Prevent container escapes and privilege escalation by using OS-level isolation primitives.

 #4.1.1    Level: 1    Role: D/V
 Ensure that all AI workloads operate with the minimal necessary permissions on the operating system, for example, by removing unnecessary Linux capabilities in the case of a container.
 #4.1.2    Level: 1    Role: D/V
 Verify that workloads are protected by technologies that limit exploitation, such as sandboxing, seccomp profiles, AppArmor, SELinux, or similar solutions, and ensure the configuration is appropriate.
 #4.1.3    Level: 2    Role: D/V
 Ensure that workloads run with a read-only root filesystem and that any writable mounts are explicitly defined and secured with restrictive options (e.g., noexec, nosuid, nodev).
 #4.1.4    Level: 2    Role: D/V
 Verify that runtime monitoring detects privilege escalation and container escape behaviors and automatically terminates offending processes.
 #4.1.5    Level: 3    Role: D/V
 Ensure that high-risk AI workloads operate in hardware-isolated environments (e.g., TEEs, trusted hypervisors, or bare-metal nodes) only after successful remote attestation.

---

### C4.2 Secure Build and Deployment Pipelines

Ensure cryptographic integrity and supply chain security by using reproducible builds and signed artifacts.


 4.2.14.2.2    1: 2    D/V: D/V
 Verify that builds generate a software bill of materials (SBOM) and are signed before being approved for deployment.
 4.2.14.2.3    1: 2    D/V: D/V
 Ensure that build artifact signatures (e.g., container images) and provenance metadata are verified at deployment, and reject any artifacts that are not verified.

---

### C4.3 Network Security and Access Control

Implement zero-trust networking using default-deny policies and encrypted communications.

 #4.3.1    Level: 1    Role: D/V
 Verify that network policies enforce default-deny for ingress and egress, allowing only the necessary services explicitly.
 #4.3.2    Level: 1    Role: D/V
 Verify that administrative access protocols (e.g., SSH, RDP) and access to cloud metadata services are restricted and require strong authentication.
 #4.3.3    Level: 2    Role: D/V
 Verify that outbound traffic is restricted to approved destinations and that all requests are logged.
 #4.3.4    Level: 2    Role: D/V
 Ensure that inter-service communication utilizes mutual TLS with certificate validation and undergoes regular automated rotation.
 #4.3.5    Level: 2    Role: D/V
 Ensure that AI workloads and environments (dev, test, prod) operate within isolated network segments (VPCs/VNets) without direct internet access and without shared IAM roles, security groups, or cross-environment connectivity.

### C4.4 Secrets and Cryptographic Key Management

Protect secrets and cryptographic keys with secure storage, automated rotation, and robust access controls.

 #4.4.1    Level: 1    Role: D/V
 Ensure that secrets are stored in a dedicated secrets management system that uses encryption at rest and is isolated from application workloads.
 #4.4.2    Level: 1    Role: D/V
 Ensure that cryptographic keys are generated and stored in hardware-backed modules (e.g., HSMs, cloud KMS).
 #4.4.3    Level: 2    Role: D/V
 Verify that the rotation of secrets is automated.
 #4.4.4    Level: TRANS ERR    Role: 
 Ensure that access to production secrets requires strong authentication.
 #4.4.5    Level: 2    Role: D/V
 Ensure that secrets are deployed to applications at runtime using a secrets management solution. Secrets should never be embedded in source code, configuration files, build artifacts, container images, or environment variables.

---

### C4.5 AI Workload Sandboxing and Validation

Isolate untrusted AI models within secure sandboxes and safeguard sensitive AI workloads using trusted execution environments (TEEs) and confidential computing technologies.

 #4.5.1    Level: 1    Role: D/V
 Verify that external or untrusted AI models run in isolated sandboxes.
 #4.5.2    Level: 1    Role: D/V
 Ensure that sandboxed workloads have no outbound network connectivity by default, with any necessary access explicitly specified.
 #4.5.3    Level: 2    Role: D/V
 Verify that workload attestation is performed before loading the model or workload, ensuring cryptographic proof of a trusted execution environment.
 #4.5.4    Level: 3    Role: D/V
 Ensure that confidential workloads run within a trusted execution environment (TEE) that offers hardware-enforced isolation, memory encryption, and integrity protection.
 #4.5.5    Level: 3    Role: D/V
 Ensure that confidential inference services prevent model extraction by using encrypted computation with sealed model weights and secure execution.
 #4.5.6    Level: 3    Role: D/V
 Verify that the orchestration of trusted execution environments includes lifecycle management, remote attestation, and encrypted communication channels.
 #4.5.7    Level: 3    Role: D/V
 Verify that secure multi-party computation (SMPC) enables collaborative AI training without revealing individual datasets or model parameters.

---

### C4.6 AI Infrastructure Resource Management, Backup, and Recovery

Prevent resource exhaustion attacks and ensure fair resource allocation using quotas and monitoring. Maintain infrastructure resilience with secure backups, tested recovery procedures, and disaster recovery capabilities.

 #4.6.1    Level: 2    Role: D/V
 Verify that the workload's resource consumption is appropriately limited using Kubernetes ResourceQuotas or similar methods to mitigate Denial of Service attacks.
 #4.6.2    Level: 2    Role: D/V
 Verify that resource exhaustion triggers automated protections (e.g., rate limiting or workload isolation) once defined CPU, memory, or request thresholds are exceeded.
 #4.6.3    Level: 2    Role: D/V
 Verify that backup systems operate within isolated networks using separate credentials, and ensure the storage system either functions in an air-gapped network or employs WORM (write-once-read-many) protection to prevent unauthorized modifications.

---

### C4.7 AI Hardware Security

Secure AI-specific hardware components, including GPUs, TPUs, and specialized AI accelerators.

 #4.7.1    Level: 2    Role: D/V
 Verify that before workload execution, the AI accelerator's integrity is validated using hardware-based attestation mechanisms (e.g., TPM, DRTM, or equivalent).
 #4.7.2    Level: 2    Role: D/V
 Verify that accelerator (GPU) memory is isolated between workloads using partitioning mechanisms, with memory sanitization performed between jobs.
 #4.7.3    Level: 3    Role: D/V
 Ensure that hardware security modules (HSMs) protect AI model weights and cryptographic keys with certification to FIPS 140-3 Level 3 or Common Criteria EAL4+.

---

### C4.8 Edge and Distributed AI Security

Secure distributed AI deployments, including edge computing, federated learning, and multi-site architectures.

 #4.8.1    Level: 2    Role: D/V
 Verify that edge AI devices authenticate to central infrastructure using mutual TLS.
 #4.8.2    Level: 2    Role: D/V
 Verify that edge devices implement secure boot using verified signatures and include rollback protection to prevent firmware downgrade attacks.
 #4.8.3    Level: 3    Role: D/V
 Verify that distributed AI coordination employs Byzantine fault-tolerant consensus mechanisms incorporating participant validation and malicious node detection.
 #4.8.4    Level: 3    Role: D/V
 Verify that edge-to-cloud communication supports bandwidth throttling, data compression, and secure offline operation with encrypted local storage.

---

### References

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework

## C5 Access Control & Identity for AI Components and Users

### Control Objective

Effective access control for AI systems requires robust identity management, context-aware authorization, and runtime enforcement based on zero-trust principles. These controls ensure that humans, services, and autonomous agents interact only with models, data, and computational resources within explicitly granted scopes, with continuous verification and auditing capabilities.

---

### C5.1 Identity Management & Authentication

Establish cryptographically-backed identities for all entities, using multi-factor authentication for privileged operations.

 #5.1.1    Level: 1    Role: D/V
 Ensure that all human users and service principals authenticate through a centralized enterprise identity provider (IdP) using OIDC/SAML protocols with unique identity-to-token mappings (no shared accounts or credentials).
 #5.1.2    Level: 1    Role: D/V
 Ensure that high-risk operations (model deployment, weight export, training data access, production configuration changes) require multi-factor authentication or step-up authentication with session re-validation.
 #5.1.3    Level: 2    Role: D
 Ensure that new principals undergo identity proofing aligned with NIST 800-63-3 IAL-2 or equivalent standards before gaining access to the production system.
 #5.1.4    Level: 2    Role: V
 Verify that access reviews are conducted quarterly with automated detection of dormant accounts, enforcement of credential rotation, and de-provisioning workflows.
 #5.1.5    Level: 3    Role: D/V
 Verify that federated AI agents authenticate using signed JWT assertions with a maximum lifetime of 24 hours, which include cryptographic proof of origin.

---

### C5.2 Resource Authorization & Least Privilege

Implement fine-grained access controls for all AI resources using explicit permission models and audit trails.

 #5.2.1    Level: 1    Role: D/V
 Verify that every AI resource (datasets, models, endpoints, vector collections, embedding indices, compute instances) enforces role-based access controls with explicit allow lists and default-deny policies.
 #5.2.2    Level: 1    Role: D/V
 Ensure that least-privilege principles are enforced by default for service accounts, starting with read-only permissions and requiring documented business justification for write access.
 #5.2.3    Level: 1    Role: V
 Ensure that all access control modifications are associated with approved change requests and are immutably logged with timestamps, actor identities, resource identifiers, and permission changes.
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
 Verify that policies evaluate dynamic attributes at runtime, including user clearance level, resource sensitivity classification, request context, tenant isolation, and temporal constraints.
 #5.3.3    Level: 2    Role: D
 Ensure that policy definitions are version-controlled, peer-reviewed, and validated through automated testing in CI/CD pipelines before deploying to production.
 #5.3.4    Level: 2    Role: V
 Verify that policy evaluation results include structured decision rationales and are transmitted to SIEM systems for correlation analysis and compliance reporting.
 #5.3.5    Level: 3    Role: D/V
 Verify that policy cache time-to-live (TTL) values do not exceed 5 minutes for high-sensitivity resources and 1 hour for standard resources that have cache invalidation capabilities.

---

### C5.4 Query-Time Security Enforcement

Implement database-layer security controls using mandatory filtering and row-level security policies.

 #5.4.1    Level: 1    Role: D/V
 Verify that all vector database and SQL queries include mandatory security filters (tenant ID, sensitivity labels, user scope) enforced at the database engine level, rather than in the application code.
 #5.4.2    Level: 1    Role: D/V
 Verify that row-level security (RLS) policies and field-level masking are enabled with policy inheritance for all vector databases, search indexes, and training datasets.
 #5.4.3    Level: 2    Role: D
 Verify that failed authorization evaluations prevent "confused deputy attacks" by immediately aborting queries and returning explicit authorization error codes instead of returning empty result sets.
 #5.4.4    Level: 2    Role: V
 Ensure that policy evaluation latency is continuously monitored with automated alerts for timeout conditions that could allow authorization bypass.
 #5.4.5    Level: 3    Role: D/V
 Ensure that query retry mechanisms re-evaluate authorization policies to accommodate dynamic permission changes during active user sessions.

---

### C5.5 Output Filtering and Data Loss Prevention

Implement post-processing controls to prevent unauthorized data exposure in AI-generated content.

 #5.5.1    Level: 1    Role: D/V
 Ensure that post-inference filtering mechanisms scan for and redact unauthorized PII, classified information, and proprietary data before delivering content to requesters.
 #5.5.2    Level: 1    Role: D/V
 Verify that citations, references, and source attributions in model outputs are validated against caller entitlements and removed if unauthorized access is detected.
 #5.5.3    Level: 2    Role: D
 Ensure that output format restrictions (such as sanitized PDFs, metadata-stripped images, and approved file types) are enforced according to user permission levels and data classifications.
 #5.5.4    Level: 2    Role: V
 Ensure that redaction algorithms are deterministic, version-controlled, and maintain audit logs to support compliance investigations and forensic analysis.
 #5.5.5    Level: 3    Role: V
 Verify that high-risk redaction events generate adaptive logs containing cryptographic hashes of the original content for forensic retrieval without exposing the data.

---

### C5.6 Multi-Tenant Isolation

Ensure cryptographic and logical isolation between tenants in shared AI infrastructure.

 #5.6.1    Level: 1    Role: D/V
 Ensure that memory spaces, embedding stores, cache entries, and temporary files are segregated by namespace per tenant, with secure purging upon tenant deletion or session termination.
 #5.6.2    Level: 1    Role: D/V
 Ensure that every API request includes an authenticated tenant identifier that is cryptographically validated against the session context and user entitlements.
 #5.6.3    Level: 2    Role: D
 Verify that network policies enforce default-deny rules for cross-tenant communication within service meshes and container orchestration platforms.
 #5.6.4    Level: 3    Role: D
 Verify that encryption keys are unique for each tenant, support customer-managed keys (CMK), and ensure cryptographic isolation between tenant data stores.

---

### C5.7 Autonomous Agent Authorization

Manage permissions for AI agents and autonomous systems using scoped capability tokens and continuous authorization.

 #5.7.1    Level: 1    Role: D/V
 Ensure that autonomous agents receive scoped capability tokens that explicitly specify permitted actions, accessible resources, time limits, and operational constraints.
 #5.7.2    Level: 1    Role: D/V
 Verify that high-risk capabilities (file system access, code execution, external API calls, financial transactions) are disabled by default and require explicit authorization for activation, supported by business justifications.
 #5.7.3    Level: 2    Role: D
 Verify that capability tokens are tied to user sessions, include cryptographic integrity protection, and are prevented from being stored or reused in offline scenarios.
 #5.7.4    Level: 2    Role: V
 Ensure that agent-initiated actions undergo secondary authorization via the ABAC policy engine, including full context evaluation and audit logging.
 #5.7.5    Level: 3    Role: V
 Ensure that agent error conditions and exception handling include capability scope information to facilitate incident analysis and forensic investigation.

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

Evaluate and verify the origins, licenses, and hidden behaviors of third-party models before any fine-tuning or deployment.

 #6.1.1    Level: 1    Role: D/V
 Verify that each third-party model artifact includes a signed provenance record identifying the source repository and commit hash.
 #6.1.2    Level: 1    Role: D/V
 Ensure that models are scanned for malicious layers or Trojan triggers using automated tools prior to import.
 #6.1.3    Level: 2    Role: D
 Verify that transfer learning fine-tunes pass adversarial evaluation to detect hidden behaviors.
 #6.1.4    Level: 2    Role: V
 Verify that model licenses, export-control tags, and data-origin statements are recorded in an ML-BOM entry.
 #6.1.5    Level: 3    Role: D/V
 Ensure that high-risk models (those with publicly uploaded weights or created by unverified sources) stay quarantined until they undergo human review and receive approval.

---

### C6.2 Framework & Library Scanning

Continuously monitor ML frameworks and libraries for CVEs and malicious code to maintain runtime stack security.

 #6.2.1    Level: 1    Role: D/V
 Verify that CI pipelines execute dependency scanners on AI frameworks and critical libraries.
 #6.2.2    Level: 1    Role: D/V
 Verify that critical vulnerabilities (CVSS ≥ 7.0) prevent promotion to production images.
 #6.2.3    Level: 2    Role: D
 Ensure that static code analysis is performed on forked or vendored machine learning libraries.
 #6.2.4    Level: 2    Role: V
 Ensure that framework upgrade proposals include a security impact assessment referencing public CVE feeds.
 #6.2.5    Level: 3    Role: V
 Verify that runtime sensors alert on unexpected dynamic library loads that deviate from the signed Software Bill of Materials (SBOM).

---

### C6.3 Dependency Pinning & Verification

Pin every dependency to immutable digests and reproduce builds to guarantee identical, tamper-free artifacts.

 #6.3.1    Level: 1    Role: D/V
 Verify that all package managers enforce version pinning through lockfiles.
 #6.3.2    Level: 1    Role: D/V
 Ensure that immutable digests are used rather than mutable tags in container references.
 #6.3.3    Level: 2    Role: D
 Verify that reproducible-build checks compare hashes across CI runs to ensure identical outputs.
 #6.3.4    Level: 2    Role: V
 Confirm that build attestations are retained for 18 months to ensure audit traceability.
 #6.3.5    Level: 3    Role: D
 Verify that expired dependencies trigger automated pull requests to update or fork pinned versions.

---

### C6.4 Trusted Source Enforcement

Allow artifact downloads only from cryptographically verified, organization-approved sources, and block all other sources.

 #6.4.1    Level: 1    Role: D/V
 Ensure that model weights, datasets, and containers are downloaded exclusively from approved domains or internal registries.
 #6.4.2    Level: 1    Role: D/V
 Confirm that Sigstore/Cosign signatures authenticate the publisher's identity before caching artifacts locally.
 #6.4.3    Level: 2    Role: D
 Verify that egress proxies block unauthenticated artifact downloads to enforce the trusted-source policy.
 #6.4.4    Level: 2    Role: V
 Verify that repository allow-lists are reviewed quarterly, with evidence of a business justification for each entry.
 #6.4.5    Level: 3    Role: V
 Ensure that policy violations trigger the quarantining of artifacts and the rollback of dependent pipeline runs.

---

### C6.5 Third-Party Dataset Risk Assessment

Evaluate external datasets for poisoning, bias, and legal compliance, and continuously monitor them throughout their lifecycle.

 #6.5.1    Level: 1    Role: D/V
 Verify that external datasets undergo poisoning risk assessment (e.g., data fingerprinting, outlier detection).
 #6.5.2    Level: 1    Role: D
 Ensure that bias metrics (demographic parity, equal opportunity) are calculated prior to dataset approval.
 #6.5.3    Level: 2    Role: V
 Verify that the provenance and license terms for datasets are recorded in ML-BOM entries.
 #6.5.4    Level: 2    Role: V
 Verify that periodic monitoring detects drift or corruption in hosted datasets.
 #6.5.5    Level: 3    Role: D
 Ensure that disallowed content (such as copyright-protected material and personally identifiable information) is removed through automated scrubbing before training.

---

### C6.6 Supply Chain Attack Monitoring

Detect supply-chain threats early through CVE feeds, audit log analytics, and red team simulations.

 #6.6.1    Level: 1    Role: V
 Verify that CI/CD audit logs are streamed to the SIEM for detection of anomalous package pulls or tampered build steps.
 #6.6.2    Level: 2    Role: D
 Verify that incident response playbooks include rollback procedures for compromised models or libraries.
 #6.6.3    Level: 3    Role: V
 Verify that threat-intel enrichment tags machine learning–specific indicators (e.g., model-poisoning IoCs) during alert triage.

---

### C6.7 ML-BOM for Model Artifacts

Generate and sign detailed machine learning-specific SBOMs (ML-BOMs) so downstream users can verify component integrity during deployment.

 #6.7.1    Level: 1    Role: D/V
 Verify that every model artifact publishes an ML-BOM listing datasets, weights, hyperparameters, and licenses.
 #6.7.2    Level: 1    Role: D/V
 Verify that ML-BOM generation and Cosign signing are automated in CI and required for merging.
 #6.7.3    Level: 2    Role: D
 Verify that ML-BOM completeness checks cause the build to fail if any component metadata (hash, license) is missing.
 #6.7.4    Level: 2    Role: V
 Verify that downstream consumers can query ML-BOMs through the API to validate imported models during deployment.
 #6.7.5    Level: 3    Role: V
 Ensure that ML-BOMs are version-controlled and compared using diffs to identify unauthorized changes.

---

### References

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## C7 Model Behavior, Output Control, and Safety Assurance

### Control Objective

Model outputs must be structured, reliable, safe, explainable, and continuously monitored in production. This approach reduces hallucinations, privacy leaks, harmful content, and uncontrolled actions, while increasing user trust and regulatory compliance.

---

### C7.1 Output Format Enforcement

Strict schemas, constrained decoding, and downstream validation prevent malformed or malicious content from spreading.

 #7.1.1    Level: 1    Role: D/V
 Ensure that response schemas (such as JSON Schema) are included in the system prompt and that every output is automatically validated; any outputs that do not conform should trigger repair or rejection.
 #7.1.2    Level: 1    Role: D/V
 Verify that constrained decoding (stop tokens, regex, max tokens) is enabled to prevent overflow or prompt-injection side channels.
 #7.1.3    Level: 2    Role: D/V
 Ensure that downstream components treat outputs as untrusted and validate them using schemas or injection-safe deserializers.
 #7.1.4    Level: 3    Role: V
 Verify that improper output events are logged, rate-limited, and reported to monitoring.

---

### C7.2 Hallucination Detection and Mitigation

Estimating uncertainty and implementing fallback strategies help prevent fabricated answers.

 #7.2.1    Level: 1    Role: D/V
 Verify that token-level log-probabilities, ensemble self-consistency, or fine-tuned hallucination detectors assign a confidence score to each answer.
 #7.2.2    Level: 1    Role: D/V
 Ensure that responses below a configurable confidence threshold activate fallback workflows (e.g., retrieval-augmented generation, secondary model, or human review).
 #7.2.3    Level: 2    Role: D/V
 Verify that hallucination incidents are tagged with root-cause metadata and fed into post-mortem and fine-tuning pipelines.
 #7.2.4    Level: 3    Role: D/V
 Verify that thresholds and detectors are recalibrated after major model or knowledge-base updates.
 #7.2.5    Level: 3    Role: V
 Verify that dashboard visualizations track hallucination rates.

---

### C7.3 Output Safety and Privacy Filtering

Policy filters and red team coverage safeguard users and confidential data.

 #7.3.1    Level: 1    Role: D/V
 Verify that pre- and post-generation classifiers block hate, harassment, self-harm, extremist, and sexually explicit content in accordance with policy.
 #7.3.2    Level: 1    Role: D/V
 Verify that PII/PCI detection and automatic redaction are performed on every response; any violations trigger a privacy incident.
 #7.3.3    Level: 2    Role: D
 Verify that confidentiality tags (e.g., trade secrets) propagate across modalities to prevent leakage in text, images, or code.
 #7.3.4    Level: 3    Role: D/V
 Verify that attempts to bypass filters or classifications marked as high-risk require secondary approval or user re-authentication.
 #7.3.5    Level: 3    Role: D/V
 Verify that filtering thresholds correspond to legal jurisdictions and the user's age and role context.

---

### C7.4 Output and Action Limiting

Rate limits and approval gates prevent abuse and excessive autonomy.

 #7.4.1    Level: 1    Role: D
 Verify that per-user and per-API-key quotas limit requests, tokens, and costs with exponential back-off on 429 errors.
 #7.4.2    Level: 1    Role: D/V
 Ensure that privileged actions (file writes, code execution, network calls) require policy-based approval or human involvement.
 #7.4.3    Level: 2    Role: D/V
 Confirm that cross-modal consistency checks guarantee images, code, and text produced for the same request cannot be exploited to conceal malicious content.
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
 Ensure that explainability artifacts are version-controlled together with model releases for auditability.

---

### C7.6 Monitoring Integration

Real-time observability closes the feedback loop between development and production.

 #7.6.1    Level: 1    Role: D
 Verify that metrics (schema violations, hallucination rate, toxicity, PII leaks, latency, cost) are streamed to a central monitoring platform.
 #7.6.2    Level: 1    Role: V
 Verify that alert thresholds are established for each safety metric, including on-call escalation protocols.
 #7.6.3    Level: 2    Role: V
 Verify that dashboards correlate output anomalies with the model/version, feature flag, and upstream data changes.
 #7.6.4    Level: 2    Role: D/V
 Ensure that monitoring data is fed back into retraining, fine-tuning, or rule updates within a documented MLOps workflow.
 #7.6.5    Level: 3    Role: V
 Ensure that monitoring pipelines are penetration tested and access controlled to prevent the leakage of sensitive logs.

---

### 7.7 Generative Media Safeguards

Ensure that AI systems do not produce illegal, harmful, or unauthorized media content by enforcing policy constraints, validating outputs, and maintaining traceability.

 #7.7.1    Level: 1    Role: D/V
 Ensure that system prompts and user instructions clearly prohibit generating illegal, harmful, or non-consensual deepfake media (e.g., images, videos, audio).
 #7.7.2    Level: 2    Role: D/V
 Verify that prompts are filtered to prevent attempts to generate impersonations, sexually explicit deepfakes, or media depicting real individuals without consent.
 #7.7.3    Level: 2    Role: V
 Verify that the system uses perceptual hashing, watermark detection, or fingerprinting to prevent unauthorized reproduction of copyrighted media.
 #7.7.4    Level: 3    Role: D/V
 Ensure that all generated media is cryptographically signed, watermarked, or embedded with tamper-resistant provenance metadata for downstream traceability.
 #7.7.5    Level: 3    Role: V
 Verify that bypass attempts (e.g., prompt obfuscation, slang, adversarial phrasing) are detected, logged, and rate-limited; repeated abuse is reported to monitoring systems.

### References

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
Sensitive Information Disclosure in LLMs
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## C8 Memory, Embeddings, and Vector Database Security

### Control Objective

Embeddings and vector stores serve as the "live memory" of modern AI systems, continuously receiving user-supplied data and integrating it back into model contexts through Retrieval-Augmented Generation (RAG). If left unmanaged, this memory can leak PII, violate consent, or be reverse-engineered to reconstruct the original text. The goal of this control family is to strengthen memory pipelines and vector databases so that access is limited to least privilege, embeddings preserve privacy, stored vectors expire or can be revoked on demand, and per-user memory never contaminates another user's prompts or completions.

---

### C8.1 Access Controls on Memory & RAG Indices

Apply precise access controls to each vector collection.

 #8.1.1    Level: 1    Role: D/V
 Verify that row- and namespace-level access control rules restrict insert, delete, and query operations for each tenant, collection, or document tag.
 #8.1.2    Level: 1    Role: D/V
 Ensure that API keys or JWTs include scoped claims (such as collection IDs and action verbs) and are rotated at least every quarter.
 #8.1.3    Level: 2    Role: D/V
 Verify that privilege escalation attempts (e.g., cross-namespace similarity queries) are detected and logged to a SIEM within 5 minutes.
 #8.1.4    Level: 2    Role: D/V
 Verify that the vector database audit logs include the subject identifier, operation, vector ID/namespace, similarity threshold, and result count.
 #8.1.5    Level: 3    Role: V
 Verify that access decisions are tested for bypass vulnerabilities whenever engines are upgraded or index-sharding rules are changed.

---

### C8.2 Embedding Sanitization and Validation

Pre-screen text for PII, redact or pseudonymize before vectorization, and optionally post-process embeddings to remove residual signals.

 #8.2.1    Level: 1    Role: D/V
 Verify that PII and regulated data are detected using automated classifiers and are masked, tokenized, or removed before embedding.
 #8.2.2    Level: 1    Role: D
 Verify that embedding pipelines reject or quarantine inputs containing executable code or non-UTF-8 artifacts that could compromise the index.
 #8.2.3    Level: 2    Role: D/V
 Verify that local or metric differential privacy sanitization is applied to sentence embeddings with a distance to any known PII token below a configurable threshold.
 #8.2.4    Level: 2    Role: V
 Ensure that sanitization effectiveness (such as recall of PII redaction and semantic drift) is validated at least semi-annually using benchmark corpora.
 #8.2.5    Level: 3    Role: D/V
 Verify that sanitization configurations are version-controlled and that changes undergo peer review.

---

### C8.3 Memory Expiry, Revocation, and Deletion

GDPR's "right to be forgotten" and similar laws require timely erasure; therefore, vector stores must support TTLs, hard deletes, and tombstoning to ensure that revoked vectors cannot be recovered or re-indexed.

 #8.3.1    Level: 1    Role: D/V
 Verify that every vector and metadata record includes a TTL or an explicit retention label that is enforced by automated cleanup jobs.
 #8.3.2    Level: 1    Role: D/V
 Ensure that user-initiated deletion requests remove vectors, metadata, cache copies, and derivative indices within 30 days.
 #8.3.3    Level: 2    Role: D
 Verify that logical deletes are followed by cryptographic shredding of storage blocks if the hardware supports it, or by key vault key destruction.
 #8.3.4    Level: 3    Role: D/V
 Ensure that expired vectors are excluded from nearest-neighbor search results within 500 ms after expiration.

---

### C8.4 Prevent Embedding Inversion and Leakage

Recent defenses—noise superposition, projection networks, privacy-neuron perturbation, and application-layer encryption—can reduce token-level inversion rates to below 5%.

 #8.4.1    Level: 1    Role: V
 Ensure that a formal threat model addressing inversion, membership, and attribute-inference attacks is established and reviewed annually.
 #8.4.2    Level: 2    Role: D/V
 Ensure that application-layer encryption or searchable encryption protects vectors from direct access by infrastructure administrators or cloud personnel.
 #8.4.3    Level: 3    Role: V
 Verify that defense parameters (ε for DP, noise σ, projection rank k) balance privacy with at least 99% token protection and utility with no more than 3% accuracy loss.
 #8.4.4    Level: 3    Role: D/V
 Ensure that inversion-resilience metrics are included as part of the release gates for model updates, with clearly defined regression budgets.

---

### C8.5 Scope Enforcement for User-Specific Memory

Cross-tenant leakage remains a major RAG risk: improperly filtered similarity queries can expose another customer's private documents.

 #8.5.1    Level: 1    Role: D/V
 Verify that every retrieval query is post-filtered by the tenant/user ID before being passed to the LLM prompt.
 #8.5.2    Level: 1    Role: D
 Confirm that collection names or namespaced IDs are salted per user or tenant to prevent vector collisions across different scopes.
 #8.5.3    Level: 2    Role: D/V
 Verify that similarity results exceeding a configurable distance threshold but outside the caller's scope are discarded and trigger security alerts.
 #8.5.4    Level: 2    Role: V
 Verify that multi-tenant stress tests simulate adversarial queries attempting to retrieve out-of-scope documents and demonstrate zero data leakage.
 #8.5.5    Level: 3    Role: D/V
 Verify that encryption keys are segregated for each tenant, ensuring cryptographic isolation even when physical storage is shared.

---

### C8.6 Advanced Memory System Security

Security controls for advanced memory architectures, including episodic, semantic, and working memory, with specific isolation and validation requirements.

 #8.6.1    Level: 1    Role: D/V
 Ensure that different memory types (episodic, semantic, working) have isolated security contexts with role-based access controls, distinct encryption keys, and documented access patterns for each memory type.
 #8.6.2    Level: 2    Role: D/V
 Ensure that memory consolidation processes include security validation to prevent the injection of malicious memories by implementing content sanitization, source verification, and integrity checks before storage.
 #8.6.3    Level: 2    Role: D/V
 Ensure that memory retrieval queries are validated and sanitized to prevent unauthorized information extraction through query pattern analysis, access control enforcement, and result filtering.
 #8.6.4    Level: 3    Role: D/V
 Ensure that memory forgetting mechanisms securely erase sensitive information by providing cryptographic erasure guarantees through key deletion, multi-pass overwriting, or hardware-based secure deletion accompanied by verification certificates.
 #8.6.5    Level: 3    Role: D/V
 Ensure that memory system integrity is continuously monitored for unauthorized modifications or corruption using checksums, audit logs, and automated alerts whenever memory content changes outside of normal operations.

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

Ensure that autonomous or multi-agent AI systems execute only actions that are explicitly intended, authenticated, auditable, and within defined cost and risk limits. This safeguards against threats such as Autonomous-System Compromise, Tool Misuse, Agent Loop Detection, Communication Hijacking, Identity Spoofing, Swarm Manipulation, and Intent Manipulation.

---

### 9.1 Agent Task Planning & Recursion Budgets

Limit recursive plans and require human checkpoints for privileged actions.

 #9.1.1    Level: 1    Role: D/V
 Confirm that the maximum recursion depth, breadth, wall-clock time, tokens, and monetary cost per agent execution are centrally configured and version-controlled.
 #9.1.2    Level: 1    Role: D/V
 Ensure that privileged or irreversible actions (e.g., code commits, financial transfers) require explicit human approval through an auditable channel before execution.
 #9.1.3    Level: 2    Role: D
 Verify that real-time resource monitors trigger a circuit-breaker interruption whenever any budget threshold is exceeded, stopping further task expansion.
 #9.1.4    Level: 2    Role: D/V
 Verify that circuit breaker events are logged with the agent ID, triggering condition, and captured plan state for forensic review.
 #9.1.5    Level: 3    Role: V
 Verify that security tests cover budget exhaustion and runaway plan scenarios, confirming safe halting without data loss.
 #9.1.6    Level: 3    Role: D
 Ensure that budget policies are defined as policy-as-code and enforced within CI/CD pipelines to prevent configuration drift.

---

### 9.2 Tool Plugin Sandboxing

Isolate tool interactions to prevent unauthorized access to the system or code execution.

 #9.2.1    Level: 1    Role: D/V
 Ensure that every tool or plugin runs inside an OS, container, or WASM-level sandbox with strict least-privilege policies for the file system, network, and system calls.
 #9.2.2    Level: 1    Role: D/V
 Verify that sandbox resource quotas (CPU, memory, disk, network egress) and execution timeouts are enforced and logged.
 #9.2.3    Level: 2    Role: D/V
 Verify that tool binaries or descriptors are digitally signed; validate signatures before loading.
 #9.2.4    Level: 2    Role: V
 Verify that sandbox telemetry streams to a SIEM and that anomalies (e.g., attempted outbound connections) trigger alerts.
 #9.2.5    Level: 3    Role: V
 Ensure that high-risk plugins undergo security reviews and penetration testing before being deployed in production.
 #9.2.6    Level: 3    Role: D/V
 Verify that sandbox escape attempts are automatically blocked and the offending plugin is quarantined pending investigation.

---

### 9.3 Autonomous Loop & Cost Bounding

Detect and prevent uncontrolled agent-to-agent recursion and cost escalations.

 #9.3.1    Level: 1    Role: D/V
 Verify that inter-agent calls include a hop limit or TTL that the runtime decrements and enforces.
 #9.3.2    Level: 2    Role: D
 Ensure that agents maintain a unique invocation-graph ID to detect self-invocation or cyclical patterns.
 #9.3.3    Level: 2    Role: D/V
 Verify that cumulative compute-unit and spending counters are tracked per request chain; exceeding the limit aborts the chain.
 #9.3.4    Level: 3    Role: V
 Verify that formal analysis or model checking demonstrates the absence of unbounded recursion in agent protocols.
 #9.3.5    Level: 3    Role: D
 Verify that loop-abort events generate alerts and contribute to continuous improvement metrics.

---

### 9.4 Protocol-Level Misuse Protection

Secure communication channels between agents and external systems to prevent hijacking or manipulation.

 #9.4.1    Level: 1    Role: D/V
 Ensure that all agent-to-tool and agent-to-agent communications are authenticated (e.g., mutual TLS or JWT) and encrypted end-to-end.
 #9.4.2    Level: 1    Role: D
 Ensure that schemas are strictly validated; unknown fields or malformed messages must be rejected.
 #9.4.3    Level: 2    Role: D/V
 Confirm that integrity checks (MACs or digital signatures) cover the entire message payload, including tool parameters.
 #9.4.4    Level: 2    Role: D
 Verify that replay protection (nonces or timestamp windows) is enforced at the protocol layer.
 #9.4.5    Level: 3    Role: V
 Ensure that protocol implementations are subjected to fuzz testing and static analysis to detect injection or deserialization vulnerabilities.

---

### 9.5 Agent Identity and Tamper Evidence

Ensure actions are traceable and modifications are detectable.

 #9.5.1    Level: 1    Role: D/V
 Ensure that each agent instance has a unique cryptographic identity, such as a key pair or hardware-rooted credential.
 #9.5.2    Level: 2    Role: D/V
 Verify that all agent actions are signed and timestamped; logs include the signature to ensure non-repudiation.
 #9.5.3    Level: 2    Role: V
 Ensure that tamper-evident logs are stored in an append-only or write-once medium.
 #9.5.4    Level: 3    Role: D
 Verify that identity keys rotate according to a defined schedule and in response to compromise indicators.
 #9.5.5    Level: 3    Role: D/V
 Verify that spoofing or key-conflict attempts immediately trigger the quarantine of the affected agent.

---

### 9.6 Multi-Agent Swarm Risk Reduction

Reduce collective behavior hazards through isolation and formal safety modeling.

 #9.6.1    Level: 1    Role: D/V
 Ensure that agents functioning in different security domains run in isolated runtime sandboxes or separate network segments.
 #9.6.2    Level: 3    Role: V
 Ensure that swarm behaviors are modeled and formally verified for both liveness and safety before deployment.
 #9.6.3    Level: 3    Role: D
 Verify that runtime monitors detect emerging unsafe patterns (e.g., oscillations, deadlocks) and initiate corrective actions.

---

### 9.7 User and Tool Authentication / Authorization

Implement robust access controls for every action triggered by agents.

 #9.7.1    Level: 1    Role: D/V
 Ensure that agents authenticate as primary principals to downstream systems, without ever reusing end-user credentials.
 #9.7.2    Level: 2    Role: D
 Ensure that fine-grained authorization policies restrict which tools an agent can invoke and which parameters it can supply.
 #9.7.3    Level: 2    Role: V
 Ensure that privilege checks are re-evaluated on every call (continuous authorization), not just at the start of the session.
 #9.7.4    Level: 3    Role: D
 Ensure that delegated privileges automatically expire and require re-consent after a timeout or a change in scope.

---

### 9.8 Security of Agent-to-Agent Communication

Encrypt and protect the integrity of all inter-agent messages to prevent eavesdropping and tampering.

 #9.8.1    Level: 1    Role: D/V
 Verify that mutual authentication and perfect forward secrecy encryption (e.g., TLS 1.3) are mandatory for agent channels.
 #9.8.2    Level: 1    Role: D
 Ensure that message integrity and origin are verified before processing; any failures trigger alerts and cause the message to be discarded.
 #9.8.3    Level: 2    Role: D/V
 Confirm that communication metadata (timestamps, sequence numbers) is logged to enable forensic reconstruction.
 #9.8.4    Level: 3    Role: V
 Verify that formal verification or model checking confirms that protocol state machines cannot be driven into unsafe states.

---

### 9.9 Intent Verification and Constraint Enforcement

Verify that agent actions correspond with the user's expressed intent and the system's limitations.

 #9.9.1    Level: 1    Role: D
 Ensure that pre-execution constraint solvers verify proposed actions against hard-coded safety and policy rules.
 #9.9.2    Level: 2    Role: D/V
 Ensure that high-impact actions (financial, destructive, privacy-sensitive) require explicit intent confirmation from the initiating user.
 #9.9.3    Level: 2    Role: V
 Verify that post-condition checks confirm completed actions achieved the intended effects without side effects; any discrepancies trigger a rollback.
 #9.9.4    Level: 3    Role: V
 Ensure that formal methods (e.g., model checking, theorem proving) or property-based tests verify that agent plans meet all specified constraints.
 #9.9.5    Level: 3    Role: D
 Ensure that incidents involving intent mismatches or constraint violations contribute to continuous improvement cycles and threat intelligence sharing.

---

### 9.10 Security of Agent Reasoning Strategies

Secure selection and execution of various reasoning strategies, including ReAct, Chain-of-Thought, and Tree-of-Thoughts approaches.

 #9.10.1    Level: 1    Role: D/V
 Verify that the reasoning strategy selection uses deterministic criteria (input complexity, task type, security context) and that identical inputs produce identical strategy selections within the same security context.
 #9.10.2    Level: 1    Role: D/V
 Verify that each reasoning strategy (ReAct, Chain-of-Thought, Tree-of-Thoughts) has dedicated input validation, output sanitization, and execution time limits specific to its cognitive approach.
 #9.10.3    Level: 2    Role: D/V
 Ensure that reasoning strategy transitions are logged with full context, including input characteristics, selection criteria values, and execution metadata, to enable audit trail reconstruction.
 #9.10.4    Level: 2    Role: D/V
 Verify that Tree-of-Thoughts reasoning incorporates branch pruning mechanisms that halt exploration when policy violations, resource limits, or safety boundaries are identified.
 #9.10.5    Level: 2    Role: D/V
 Verify that ReAct (Reason-Act-Observe) cycles include validation checkpoints at each phase: reasoning step verification, action authorization, and observation sanitization before proceeding.
 #9.10.6    Level: 3    Role: D/V
 Ensure that performance metrics for the reasoning strategy (execution time, resource usage, output quality) are monitored with automated alerts triggered when metrics exceed configured thresholds.
 #9.10.7    Level: 3    Role: D/V
 Ensure that hybrid reasoning approaches combining multiple strategies uphold input validation and output constraints of each constituent strategy without circumventing any security controls.
 #9.10.8    Level: 3    Role: D/V
 Verify that the reasoning strategy security testing includes fuzzing with malformed inputs, adversarial prompts designed to trigger strategy switching, and boundary condition testing for each cognitive approach.

---

### 9.11 Agent Lifecycle State Management and Security

Secure agent initialization, state transitions, and termination with cryptographic audit trails and clearly defined recovery procedures.

 #9.11.1    Level: 1    Role: D/V
 Verify that agent initialization includes cryptographic identity establishment using hardware-backed credentials and immutable startup audit logs containing the agent ID, timestamp, configuration hash, and initialization parameters.
 #9.11.2    Level: 2    Role: D/V
 Verify that agent state transitions are cryptographically signed, timestamped, and logged with complete context, including triggering events, previous state hash, new state hash, and security validations performed.
 #9.11.3    Level: 2    Role: D/V
 Verify that agent shutdown procedures include secure memory wiping through cryptographic erasure or multi-pass overwriting, credential revocation with notification to the certificate authority, and the generation of tamper-evident termination certificates.
 #9.11.4    Level: 3    Role: D/V
 Verify that agent recovery mechanisms validate state integrity using cryptographic checksums (minimum SHA-256) and rollback to known-good states when corruption is detected, incorporating automated alerts and requiring manual approval.
 #9.11.5    Level: 3    Role: D/V
 Verify that agent persistence mechanisms encrypt sensitive state data using per-agent AES-256 keys and implement secure key rotation on configurable schedules (up to a maximum of 90 days) with zero downtime deployment.

---

### 9.12 Tool Integration Security Framework

Security controls for dynamic tool loading, execution, and result validation with established risk assessment and approval procedures.

 #9.12.1    Level: 1    Role: D/V
 Verify that tool descriptors include security metadata specifying required privileges (read/write/execute), risk levels (low/medium/high), resource limits (CPU, memory, network), and validation requirements documented in tool manifests.
 #9.12.2    Level: 1    Role: D/V
 Verify that tool execution results are validated against expected schemas (JSON Schema, XML Schema) and security policies (output sanitization, data classification) before integration, including timeout limits and error handling procedures.
 #9.12.3    Level: 2    Role: D/V
 Verify that tool interaction logs include detailed security context such as privilege usage, data access patterns, execution time, resource consumption, and return codes, with structured logging for SIEM integration.
 #9.12.4    Level: 2    Role: D/V
 Ensure that dynamic tool loading mechanisms validate digital signatures through PKI infrastructure and implement secure loading protocols with sandbox isolation and permission verification before execution.
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

Ensure that AI models remain reliable, privacy-preserving, and resistant to abuse when facing evasion, inference, extraction, or poisoning attacks.

---

### 10.1 Model Alignment & Safety

Protect against harmful or policy-violating outputs.

 #10.1.1    Level: 1    Role: D/V
 Ensure that an alignment test suite (including red-team prompts, jailbreak probes, and disallowed content) is version-controlled and executed with every model release.
 #10.1.2    Level: 1    Role: D
 Verify that refusal and safe-completion guardrails are enforced.
 #10.1.3    Level: 2    Role: D/V
 Verify that an automated evaluator measures the harmful content rate and flags regressions that exceed a set threshold.
 #10.1.4    Level: 2    Role: D
 Verify that counter-jailbreak training is properly documented and can be reproduced.
 #10.1.5    Level: 3    Role: V
 Verify that formal policy-compliance proofs or certified monitoring cover all critical domains.

---

### 10.2 Adversarial Example Hardening

Enhance resilience against manipulated inputs. Robust adversarial training and benchmark scoring remain the current best practices.

 #10.2.1    Level: 1    Role: D
 Ensure that project repositories contain adversarial-training configurations with reproducible seeds.
 #10.2.2    Level: 2    Role: D/V
 Verify that the detection of adversarial examples triggers blocking alerts in production pipelines.
 #10.2.4    Level: 3    Role: V
 Verify that certified robustness proofs or interval-bound certificates cover at least the most critical classes.
 #10.2.5    Level: 3    Role: V
 Verify that regression tests employ adaptive attacks to ensure there is no measurable loss in robustness.

---

### 10.3 Membership-Inference Mitigation

Limit the ability to determine whether a record was included in the training data. Differential privacy and confidence score masking continue to be the most effective known defenses.

 #10.3.1    Level: 1    Role: D
 Verify that per-query entropy regularization or temperature scaling reduces overconfident predictions.
 #10.3.2    Level: 2    Role: D
 Verify that training uses ε-bounded differentially private optimization for sensitive datasets.
 #10.3.3    Level: 2    Role: V
 Verify that attack simulations (shadow-model or black-box) demonstrate an attack AUC of ≤ 0.60 on held-out data.

---

### 10.4 Model Inversion Resistance

Prevent the reconstruction of private attributes. Recent surveys highlight output truncation and differential privacy guarantees as effective defensive measures.

 #10.4.1    Level: 1    Role: D
 Ensure that sensitive attributes are never directly output; when necessary, use buckets or one-way transformations.
 #10.4.2    Level: 1    Role: D/V
 Verify that query rate limits throttle repeated adaptive queries from the same principal.
 #10.4.3    Level: 2    Role: D
 Verify that the model is trained using privacy-preserving noise.

---

### 10.5 Model Extraction Defense

Detect and prevent unauthorized cloning. Watermarking and query pattern analysis are recommended.

 #10.5.1    Level: 1    Role: D
 Verify that inference gateways enforce global and per-API-key rate limits adjusted to the model's memorization threshold.
 #10.5.2    Level: 2    Role: D/V
 Verify that query-entropy and input-plurality statistics are used to feed an automated extraction detector.
 #10.5.3    Level: 2    Role: V
 Verify that fragile or probabilistic watermarks can be proven with p < 0.01 in no more than 1,000 queries against a suspected clone.
 #10.5.4    Level: 3    Role: D
 Verify that watermark keys and trigger sets are stored in a hardware security module and rotated annually.
 #10.5.5    Level: 3    Role: V
 Verify that extraction-alert events include the offending queries and are integrated with incident response playbooks.

---

### 10.6 Detection of Poisoned Data at Inference Time

Detect and neutralize backdoored or poisoned inputs.

 #10.6.1    Level: 1    Role: D
 Ensure that inputs pass through an anomaly detector (e.g., STRIP, consistency scoring) before model inference.
 #10.6.2    Level: 1    Role: V
 Verify that detector thresholds are tuned on clean or poisoned validation sets to achieve less than 5% false positives.
 #10.6.3    Level: 2    Role: D
 Verify that inputs identified as poisoned trigger soft-blocking and initiate human review workflows.
 #10.6.4    Level: 2    Role: V
 Verify that detectors are stress-tested using adaptive, triggerless backdoor attacks.
 #10.6.5    Level: 3    Role: D
 Verify that detection efficacy metrics are logged and periodically re-evaluated using updated threat intelligence.

---

### 10.7 Dynamic Security Policy Adaptation

Real-time security policy updates based on threat intelligence and behavioral analysis.

 #10.7.1    Level: 1    Role: D/V
 Verify that security policies can be updated dynamically without restarting the agent while preserving the integrity of the policy version.
 #10.7.2    Level: 2    Role: D/V
 Ensure that policy updates are cryptographically signed by authorized security personnel and verified before implementation.
 #10.7.3    Level: 2    Role: D/V
 Ensure that dynamic policy changes are logged with complete audit trails, including justification, approval chains, and rollback procedures.
 #10.7.4    Level: 3    Role: D/V
 Verify that adaptive security mechanisms adjust threat detection sensitivity according to risk context and behavioral patterns.
 #10.7.5    Level: 3    Role: D/V
 Ensure that policy adaptation decisions are explainable and include evidence trails for security team review.

---

### 10.8 Reflection-Based Security Analysis

Security validation through agent self-reflection and meta-cognitive analysis.

 #10.8.1    Level: 1    Role: D/V
 Ensure that agent reflection mechanisms incorporate security-focused self-assessment of decisions and actions.
 #10.8.2    Level: 2    Role: D/V
 Ensure that reflection outputs are validated to prevent adversarial inputs from manipulating self-assessment mechanisms.
 #10.8.3    Level: 2    Role: D/V
 Verify that meta-cognitive security analysis identifies potential bias, manipulation, or compromise in the agent's reasoning processes.
 #10.8.4    Level: 3    Role: D/V
 Verify that reflection-based security warnings activate enhanced monitoring and possible human intervention workflows.
 #10.8.5    Level: 3    Role: D/V
 Verify that continuous learning from security reflections enhances threat detection without compromising legitimate functionality.

---

### 10.9 Evolution and Self-Improvement Security

Security controls for agent systems capable of self-modification and evolution.

 #10.9.1    Level: 1    Role: D/V
 Ensure that self-modification capabilities are limited to designated safe areas with formal verification boundaries.
 #10.9.2    Level: 2    Role: D/V
 Ensure that evolution proposals undergo a security impact assessment before implementation.
 #10.9.3    Level: 2    Role: D/V
 Ensure that self-improvement mechanisms include rollback capabilities accompanied by integrity verification.
 #10.9.4    Level: 3    Role: D/V
 Confirm that meta-learning security prevents adversarial manipulation of improvement algorithms.
 #10.9.5    Level: 3    Role: D/V
 Verify that recursive self-improvement is bounded by formal safety constraints using mathematical proofs of convergence.

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

Maintain strict privacy guarantees throughout the entire AI lifecycle—collection, training, inference, and incident response—ensuring that personal data is processed only with explicit consent, limited to the minimum necessary scope, verifiable erasure, and formal privacy assurances.

---

### 11.1 Anonymization and Data Minimization

 #11.1.1    Level: 1    Role: D/V
 Verify that direct and quasi-identifiers are removed or hashed.
 #11.1.2    Level: 2    Role: D/V
 Verify that automated audits measure k-anonymity and l-diversity and issue alerts when thresholds fall below policy.
 #11.1.3    Level: 2    Role: V
 Verify that model feature-importance reports demonstrate no identifier leakage beyond ε = 0.01 mutual information.
 #11.1.4    Level: 3    Role: V
 Verify that formal proofs or synthetic data certification demonstrate a re-identification risk of ≤ 0.05 even under linkage attacks.

---

### 11.2 Right to Be Forgotten and Deletion Enforcement

 #11.2.1    Level: 1    Role: D/V
 Verify that data-subject deletion requests are propagated to raw datasets, checkpoints, embeddings, logs, and backups within service level agreements of less than 30 days.
 #11.2.2    Level: 2    Role: D
 Verify that "machine unlearning" routines physically retrain or approximate removal using certified unlearning algorithms.
 #11.2.3    Level: 2    Role: V
 Verify that shadow-model evaluation demonstrates that forgotten records influence less than 1% of outputs after unlearning.
 #11.2.4    Level: 3    Role: V
 Ensure that deletion events are immutably logged and can be audited by regulators.

---

### 11.3 Differential Privacy Safeguards

 #11.3.1    Level: 2    Role: D/V
 Verify that privacy-loss accounting dashboards trigger alerts when the cumulative ε exceeds policy thresholds.
 #11.3.2    Level: 2    Role: V
 Verify that black-box privacy audits estimate ε̂ within 10% of the declared value.
 #11.3.3    Level: 3    Role: V
 Verify that formal proofs encompass all post-training fine-tunes and embeddings.

---

### 11.4 Purpose Limitation & Scope Creep Protection

 #11.4.1    Level: 1    Role: D
 Verify that each dataset and model checkpoint includes a machine-readable purpose tag aligned with the original consent.
 #11.4.2    Level: 1    Role: D/V
 Verify that runtime monitors detect queries inconsistent with the declared purpose and trigger a soft refusal.
 #11.4.3    Level: 3    Role: D
 Verify that policy-as-code gates prevent redeployment of models to new domains without a DPIA review.
 #11.4.4    Level: 3    Role: V
 Verify that formal traceability proofs demonstrate that every personal data lifecycle remains within the consented scope.

---

### 11.5 Consent Management & Lawful Basis Tracking

 #11.5.1    Level: 1    Role: D/V
 Verify that a Consent Management Platform (CMP) records the opt-in status, purpose, and retention period for each data subject.
 #11.5.2    Level: 2    Role: D
 Verify that APIs expose consent tokens; models must validate token scope before performing inference.
 #11.5.3    Level: 2    Role: D/V
 Verify that processing pipelines stop within 24 hours when consent is denied or withdrawn.

---

### 11.6 Federated Learning with Privacy Controls

 #11.6.1    Level: 1    Role: D
 Ensure that client updates include local differential privacy noise addition before aggregation.
 #11.6.2    Level: 2    Role: D/V
 Verify that training metrics are differentially private and do not reveal any individual client's loss.
 #11.6.3    Level: 2    Role: V
 Verify that poisoning-resistant aggregation methods (e.g., Krum or Trimmed-Mean) are enabled.
 #11.6.4    Level: 3    Role: V
 Verify that formal proofs demonstrate the overall ε budget with less than 5 utility loss.

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

This section outlines requirements for providing real-time and forensic visibility into what the model and other AI components observe, perform, and output, enabling threats to be detected, triaged, and analyzed for learning.

### C12.1 Request and Response Logging

 #12.1.1    Level: 1    Role: D/V
 Ensure that all user prompts and model responses are logged with the appropriate metadata (e.g., timestamp, user ID, session ID, model version).
 #12.1.2    Level: 1    Role: D/V
 Ensure that logs are stored in secure, access-controlled repositories with proper retention policies and backup procedures.
 #12.1.3    Level: 1    Role: D/V
 Ensure that log storage systems implement encryption both at rest and in transit to protect sensitive information contained in logs.
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
 Verify that enriched security events include AI-specific context, such as model identifiers, confidence scores, and safety filter decisions.
 #12.2.4    Level: 2    Role: D/V
 Verify that behavioral anomaly detection identifies unusual conversation patterns, excessive retry attempts, or systematic probing behaviors.
 #12.2.5    Level: 2    Role: D/V
 Verify that real-time alerting mechanisms notify security teams whenever potential policy violations or attack attempts are detected.
 #12.2.6    Level: 2    Role: D/V
 Verify that custom rules are included to detect AI-specific threat patterns, including coordinated jailbreak attempts, prompt injection campaigns, and model extraction attacks.
 #12.2.7    Level: 3    Role: D/V
 Verify that automated incident response workflows can isolate compromised models, block malicious users, and escalate critical security events.

---

### C12.3 Model Drift Detection

 #12.3.1    Level: 1    Role: D/V
 Verify that the system tracks basic performance metrics such as accuracy, confidence scores, latency, and error rates across different model versions and time periods.
 #12.3.2    Level: 2    Role: D/V
 Verify that automated alerts trigger when performance metrics exceed predefined degradation thresholds or deviate significantly from baselines.
 #12.3.3    Level: 2    Role: D/V
 Verify that hallucination detection monitors identify and flag instances where model outputs contain factually incorrect, inconsistent, or fabricated information.

---

### C12.4 Performance and Behavior Telemetry

 #12.4.1    Level: 1    Role: D/V
 Ensure that operational metrics such as request latency, token consumption, memory usage, and throughput are continuously collected and monitored.
 #12.4.2    Level: 1    Role: D/V
 Ensure that success and failure rates are tracked, including the categorization of error types and their root causes.
 #12.4.3    Level: 2    Role: D/V
 Verify that resource utilization monitoring includes GPU and CPU usage, memory consumption, and storage requirements, with alerts triggered when thresholds are breached.

---

### C12.5 AI Incident Response Planning and Execution

 #12.5.1    Level: 1    Role: D/V
 Verify that incident response plans specifically address AI-related security events, including model compromise, data poisoning, and adversarial attacks.
 #12.5.2    Level: 2    Role: D/V
 Ensure that incident response teams have access to AI-specific forensic tools and expertise to investigate model behavior and attack vectors.
 #12.5.3    Level: 3    Role: D/V
 Verify that the post-incident analysis includes considerations for model retraining, updates to safety filters, and the integration of lessons learned into security controls.

---

### C12.6 AI Performance Degradation Detection

Monitor and detect declines in AI model performance and quality over time.

 #12.6.1    Level: 1    Role: D/V
 Ensure that model accuracy, precision, recall, and F1 scores are continuously monitored and compared against baseline thresholds.
 #12.6.2    Level: 1    Role: D/V
 Verify that data drift detection monitors changes in input distribution that could affect model performance.
 #12.6.3    Level: 2    Role: D/V
 Verify that concept drift detection accurately identifies changes in the relationship between inputs and expected outputs.
 #12.6.4    Level: 2    Role: D/V
 Ensure that performance degradation triggers automated alerts and initiates workflows for model retraining or replacement.
 #12.6.5    Level: 3    Role: V
 Verify that degradation root cause analysis correlates performance declines with data changes, infrastructure problems, or external factors.

---

### C12.7 DAG Visualization & Workflow Security

Protect workflow visualization systems against information leakage and manipulation attacks.

 #12.7.1    Level: 1    Role: D/V
 Ensure that DAG visualization data is sanitized to remove sensitive information before storage or transmission.
 #12.7.2    Level: 1    Role: D/V
 Verify that workflow visualization access controls ensure that only authorized users can view agent decision paths and reasoning traces.
 #12.7.3    Level: 2    Role: D/V
 Ensure that DAG data integrity is protected using cryptographic signatures and tamper-evident storage mechanisms.
 #12.7.4    Level: 2    Role: D/V
 Verify that workflow visualization systems implement input validation to prevent injection attacks via crafted node or edge data.
 #12.7.5    Level: 3    Role: D/V
 Ensure that real-time DAG updates are rate-limited and validated to prevent denial-of-service attacks on visualization systems.

---

### C12.8 Proactive Security Behavior Monitoring

Detection and prevention of security threats through proactive analysis of agent behavior.

 #12.8.1    Level: 1    Role: D/V
 Ensure that proactive agent behaviors are security-validated before execution, incorporating risk assessment integration.
 #12.8.2    Level: 2    Role: D/V
 Verify that autonomous initiative triggers include evaluation of the security context and assessment of the threat landscape.
 #12.8.3    Level: 2    Role: D/V
 Ensure that proactive behavior patterns are analyzed for potential security implications and unintended consequences.
 #12.8.4    Level: 3    Role: D/V
 Ensure that security-critical proactive actions require explicit approval chains along with audit trails.
 #12.8.5    Level: 3    Role: D/V
 Verify that behavioral anomaly detection identifies deviations in proactive agent patterns that may indicate a compromise.

---

### References

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6

## C13 Human Oversight, Accountability, and Governance

### Control Objective

This chapter outlines requirements for maintaining human oversight and clear accountability chains in AI systems, ensuring explainability, transparency, and ethical stewardship throughout the AI lifecycle.

---

### C13.1 Kill-Switch and Override Mechanisms

Provide shutdown or rollback procedures when unsafe behavior of the AI system is detected.

 #13.1.1    Level: 1    Role: D/V
 Confirm that a manual kill-switch mechanism is in place to immediately stop AI model inference and outputs.
 #13.1.2    Level: 1    Role: D
 Verify that override controls are accessible only to authorized personnel.
 #13.1.3    Level: 3    Role: D/V
 Verify that rollback procedures can restore previous model versions or safe-mode operations.
 #13.1.4    Level: 3    Role: V
 Ensure that override mechanisms are tested regularly.

---

### C13.2 Human-in-the-Loop Decision Checkpoints

Require human approval when stakes exceed predefined risk thresholds.

 #13.2.1    Level: 1    Role: D/V
 Ensure that high-risk AI decisions receive explicit human approval before execution.
 #13.2.2    Level: 1    Role: D
 Ensure that risk thresholds are clearly defined and that they automatically trigger human review workflows.
 #13.2.3    Level: 2    Role: D
 Verify that time-sensitive decisions have fallback procedures in place when human approval cannot be obtained within the required timeframes.
 #13.2.4    Level: 3    Role: D/V
 Verify that escalation procedures clearly define authority levels for different decision types or risk categories, if applicable.

---

### C13.3 Chain of Responsibility & Auditability

Log operator actions and model decisions.

 #13.3.1    Level: 1    Role: D/V
 Ensure that all AI system decisions and human interventions are recorded with timestamps, user identities, and the rationale behind the decisions.
 #13.3.2    Level: 2    Role: D
 Ensure that audit logs cannot be tampered with and incorporate mechanisms for verifying their integrity.

---

### C13.4 Explainable AI Techniques

Surface feature importance, counterfactuals, and local explanations.

 #13.4.1    Level: 1    Role: D/V
 Verify that AI systems provide basic explanations for their decisions in a human-readable format.
 #13.4.2    Level: 2    Role: V
 Ensure that the quality of explanations is validated through human evaluation studies and metrics.
 #13.4.3    Level: 3    Role: D/V
 Verify that feature importance scores or attribution methods (such as SHAP, LIME, etc.) are available for critical decisions.
 #13.4.4    Level: 3    Role: V
 Confirm that counterfactual explanations demonstrate how inputs could be altered to change outcomes, if relevant to the use case and domain.

---

### C13.5 Model Cards and Usage Disclosures

Maintain model cards documenting intended use, performance metrics, and ethical considerations.

 #13.5.1    Level: 1    Role: D
 Ensure that model cards document intended use cases, limitations, and known failure modes.
 #13.5.2    Level: 1    Role: D/V
 Ensure that performance metrics for all relevant use cases are disclosed.
 #13.5.3    Level: 2    Role: D
 Ensure that ethical considerations, bias assessments, fairness evaluations, training data characteristics, and known training data limitations are documented and updated regularly.
 #13.5.4    Level: 2    Role: D/V
 Ensure that model cards are version-controlled and maintained throughout the model lifecycle with change tracking.

---

### C13.6 Uncertainty Quantification

Propagate confidence scores or entropy measures in the responses.

 #13.6.1    Level: 1    Role: D
 Verify that AI systems include confidence scores or uncertainty measures with their outputs.
 #13.6.2    Level: 2    Role: D/V
 Verify that uncertainty thresholds initiate additional human review or activate alternative decision pathways.
 #13.6.3    Level: 2    Role: V
 Ensure that uncertainty quantification methods are calibrated and validated against ground truth data.
 #13.6.4    Level: 3    Role: D/V
 Ensure that uncertainty propagation is preserved throughout multi-step AI workflows.

---

### C13.7 User-Facing Transparency Reports

Provide regular disclosures on incidents, drift, and data usage.

 #13.7.1    Level: 1    Role: D/V
 Ensure that data usage policies and user consent management practices are clearly communicated to stakeholders.
 #13.7.2    Level: 2    Role: D/V
 Verify that AI impact assessments are conducted and that the results are included in reporting.
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
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Appendix A: Glossary

This comprehensive glossary provides definitions of key AI, ML, and security terms used throughout the AISVS to ensure clarity and a common understanding.

Adversarial Example: An input intentionally designed to cause an AI model to make an error, often by adding subtle perturbations that are imperceptible to humans.
​
Adversarial Robustness – In AI, adversarial robustness refers to a model's ability to maintain its performance and resist being deceived or manipulated by intentionally crafted malicious inputs designed to cause errors.
​
Agent – AI agents are software systems that use AI to pursue goals and complete tasks on behalf of users. They demonstrate reasoning, planning, and memory and possess a level of autonomy to make decisions, learn, and adapt.
​
Agentic AI: AI systems capable of operating with a certain level of autonomy to achieve goals, often making decisions and taking actions without direct human intervention.
​
Attribute-Based Access Control (ABAC): An access control model in which authorization decisions are made based on attributes of the user, resource, action, and environment, evaluated at the time of the request.
​
Backdoor Attack: A type of data poisoning attack in which the model is trained to respond in a specific way to certain triggers while behaving normally in other situations.
​
Bias: Systematic errors in AI model outputs that can result in unfair or discriminatory outcomes for certain groups or specific contexts.
​
Bias Exploitation: An attack technique that leverages known biases in AI models to manipulate outputs or results.
​
Cedar: Amazon's policy language and engine for fine-grained permissions used in implementing Attribute-Based Access Control (ABAC) for AI systems.
​
Chain of Thought: A technique for enhancing reasoning in language models by generating intermediate reasoning steps before producing the final answer.
​
Circuit Breakers: Mechanisms that automatically stop AI system operations when specific risk thresholds are exceeded.
​
Confidential Inference Service: An inference service that operates AI models within a trusted execution environment (TEE) or an equivalent confidential computing mechanism, ensuring that model weights and inference data remain encrypted, sealed, and protected from unauthorized access or tampering.
​
Confidential Workload: An AI workload (such as training, inference, or preprocessing) executed inside a trusted execution environment (TEE) with hardware-enforced isolation, memory encryption, and remote attestation to protect code, data, and models from access by the host or co-tenants.
​
Data Leakage: The unintended exposure of sensitive information through AI model outputs or behavior.
​
Data Poisoning: The intentional corruption of training data to compromise model integrity, often to introduce backdoors or degrade performance.
​
Differential Privacy – Differential privacy is a mathematically rigorous framework for releasing statistical information about datasets while protecting the privacy of individual data subjects. It allows a data holder to share aggregate patterns of the group while limiting the information leaked about specific individuals.
​
Embeddings: Dense vector representations of data (such as text, images, etc.) that capture semantic meaning within a high-dimensional space.
​
Explainability – Explainability in AI refers to an AI system's ability to provide human-understandable explanations for its decisions and predictions, offering insights into how it operates internally.
​
Explainable AI (XAI): AI systems designed to offer human-understandable explanations for their decisions and behaviors using various techniques and frameworks.
​
Federated Learning: A machine learning approach in which models are trained across multiple decentralized devices holding local data samples, without exchanging the data itself.
​
Formulation: The recipe or method used to create an artifact or dataset, such as hyperparameters, training configuration, preprocessing steps, or build scripts.
​
Guardrails: Constraints implemented to prevent AI systems from generating harmful, biased, or otherwise undesirable outputs.
​
Hallucination – An AI hallucination refers to a phenomenon where an AI model generates incorrect or misleading information that is not based on its training data or factual reality.
​
Human-in-the-Loop (HITL): Systems designed to require human oversight, verification, or intervention at critical decision points.
​
Infrastructure as Code (IaC): Managing and provisioning infrastructure through code rather than manual processes, enabling security scanning and ensuring consistent deployments.
​
Jailbreak: Techniques used to bypass safety guardrails in AI systems, especially in large language models, to generate prohibited content.
​
Least Privilege: The security principle of granting users and processes only the minimum necessary access rights.
​
LIME (Local Interpretable Model-agnostic Explanations): A technique for explaining the predictions of any machine learning classifier by locally approximating it with an interpretable model.
​
Membership Inference Attack: An attack that aims to determine whether a specific data point was used to train a machine learning model.
​
MITRE ATLAS: Adversarial Threat Landscape for Artificial Intelligence Systems; a knowledge base of adversarial tactics and techniques targeting AI systems.
​
Model Card – A model card is a document that provides standardized information about an AI model’s performance, limitations, intended uses, and ethical considerations to promote transparency and responsible AI development.
​
Model Extraction: An attack in which an adversary repeatedly queries a target model to create an unauthorized functionally similar copy.
​
Model Inversion: An attack that tries to reconstruct training data by analyzing the outputs of a model.
​
Model Lifecycle Management – AI Model Lifecycle Management is the process of overseeing all stages of an AI model’s existence, including its design, development, deployment, monitoring, maintenance, and eventual retirement, to ensure it remains effective and aligned with objectives.
​
Model Poisoning: Introducing vulnerabilities or backdoors directly into a model during the training process.
​
Model Stealing/Theft: Obtaining a copy or approximation of a proprietary model through repeated queries.
​
Multi-agent System: A system comprised of multiple interacting AI agents, each potentially having different capabilities and goals.
​
OPA (Open Policy Agent): An open-source policy engine that enables unified policy enforcement across the entire stack.
​
Provenance: The pedigree and chain of custody of an artifact or dataset, including its origin, handlers, transfer path, and evidence of integrity (e.g., checksums, signatures).
​
Privacy-Preserving Machine Learning (PPML): Techniques and methods for training and deploying ML models while safeguarding the privacy of the training data.
​
Prompt Injection: An attack in which malicious instructions are embedded in inputs to override a model's intended behavior.
​
RAG (Retrieval-Augmented Generation): A technique that improves large language models by retrieving relevant information from external knowledge sources before generating a response.
​
Red-Teaming: The practice of actively testing AI systems by simulating adversarial attacks to identify vulnerabilities.
​
SLSA Provenance: Metadata defined by the SLSA framework that records where, when, and how an artifact was produced (e.g., source repository, commit hash, build system, and parameters).
​
SBOM (Software Bill of Materials): A formal record that contains the details and supply chain relationships of various components used in building software or AI models.
​
SHAP (SHapley Additive exPlanations): A game-theoretic approach to explain the output of any machine learning model by calculating the contribution of each feature to the prediction.
​
Strong Authentication: Authentication that resists credential theft and replay attacks by requiring at least two factors (knowledge, possession, inherence) and phishing-resistant mechanisms such as FIDO2/WebAuthn, certificate-based service authentication, or short-lived tokens.
​
Supply Chain Attack: Compromising a system by targeting weaker elements in its supply chain, such as third-party libraries, datasets, or pre-trained models.
​
Transfer Learning: A technique where a model developed for one task is reused as the starting point for a model on a second task.
​
Vector Database: A specialized database designed to store high-dimensional vectors (embeddings) and efficiently perform similarity searches.
​
Vulnerability Scanning: Automated tools that detect known security vulnerabilities in software components, including AI frameworks and dependencies.
​
Watermarking: Techniques for embedding imperceptible markers in AI-generated content to trace its origin or identify AI generation.
​
Zero-Day Vulnerability: A previously unknown flaw that attackers can exploit before developers create and release a patch.

## Appendix B: References

### TODO

## Appendix C: AI Security Governance and Documentation (Reorganized)

### Objective

This appendix outlines the fundamental requirements for establishing organizational structures, policies, documentation, and processes to manage AI security throughout the system lifecycle.

---

### AC.1 Adoption of AI Risk Management Framework

 #AC.1.1    Level: 1    Role: D/V
 Verify that an AI-specific risk assessment methodology is documented and implemented.
 #AC.1.2    Level: 2    Role: D
 Ensure that risk assessments are conducted at critical stages in the AI lifecycle and before any significant changes.
 #AC.1.3    Level: 3    Role: D/V
 Verify that the risk management framework aligns with established standards (e.g., NIST AI RMF).

---

### AC.2 AI Security Policy & Procedures

 #AC.2.1    Level: 1    Role: D/V
 Verify that documented AI security policies are in place.
 #AC.2.2    Level: 2    Role: D
 Ensure that policies are reviewed and updated at least annually and following significant changes in the threat landscape.
 #AC.2.3    Level: 3    Role: D/V
 Verify that policies cover all AISVS categories and comply with applicable regulatory requirements.

---

### AC.3 Roles & Responsibilities for AI Security

 #AC.3.1    Level: 1    Role: D/V
 Verify that AI security roles and responsibilities are properly documented.
 #AC.3.2    Level: 2    Role: D
 Ensure that responsible individuals have the appropriate security expertise.
 #AC.3.3    Level: 3    Role: D/V
 Verify that an AI ethics committee or governance board has been established for high-risk AI systems.

---

### AC.4 Enforcement of Ethical AI Guidelines

 #AC.4.1    Level: 1    Role: D/V
 Confirm that ethical guidelines for AI development and deployment are in place.
 #AC.4.2    Level: 2    Role: D
 Ensure that mechanisms are in place to detect and report ethical violations.
 #AC.4.3    Level: 3    Role: D/V
 Ensure that regular ethical reviews of deployed AI systems are conducted.

---

### AC.5 AI Regulatory Compliance Monitoring

 #AC.5.1    Level: 1    Role: D/V
 Ensure processes are in place to identify applicable AI regulations.
 #AC.5.2    Level: 2    Role: D
 Verify that compliance with all regulatory requirements has been assessed.
 #AC.5.3    Level: 3    Role: D/V
 Ensure that regulatory changes prompt timely reviews and updates to AI systems.

---

### AC.6 Training Data Governance, Documentation, and Process

#### AC.6.1 Data Sourcing and Due Diligence

 #AC.6.1.1    Level: 1    Role: D/V
 Ensure that only datasets verified for quality, representativeness, ethical sourcing, and license compliance are used, minimizing risks of poisoning, embedded bias, and intellectual property infringement.
 #AC.6.1.2    Level: 2    Role: D/V
 Ensure that third-party data suppliers, including providers of pre-trained models and external datasets, undergo due diligence for security, privacy, ethical sourcing, and data quality before their data or models are integrated.
 #AC.6.1.3    Level: 1    Role: D
 Verify that external transfers utilize TLS/authentication and include integrity checks.
 #AC.6.1.4    Level: 2    Role: D/V
 Ensure that high-risk data sources (e.g., open-source datasets with unknown origins, unvetted suppliers) undergo enhanced scrutiny before being used in sensitive applications, including sandboxed analysis, thorough quality and bias assessments, and focused poisoning detection.
 #AC.6.1.5    Level: 3    Role: D/V
 Verify that pre-trained models obtained from third parties are evaluated for embedded biases, potential backdoors, the integrity of their architecture, and the provenance of their original training data before fine-tuning or deployment.

#### AC.6.2 Bias and Fairness Management

 #AC.6.2.1    Level: 1    Role: D/V
 Verify that datasets are analyzed for representational imbalance and potential biases across legally protected attributes (e.g., race, gender, age) and other ethically sensitive characteristics relevant to the model's application domain (e.g., socio-economic status, location).
 #AC.6.2.2    Level: 2    Role: D/V
 Verify that identified biases are mitigated through documented strategies such as re-balancing, targeted data augmentation, algorithmic adjustments (e.g., pre-processing, in-processing, post-processing techniques), or re-weighting, and that the impact of mitigation on both fairness and overall model performance is assessed.
 #AC.6.2.3    Level: 2    Role: D/V
 Verify that post-training fairness metrics have been evaluated and documented.
 #AC.6.2.4    Level: 3    Role: D/V
 Verify that a lifecycle bias management policy designates owners and establishes a review schedule.

#### AC.6.3 Labeling and Annotation Governance

 #AC.6.3.1    Level: 2    Role: D/V
 Verify that labeling/annotation quality is ensured through reviewer cross-checks or consensus.
 #AC.6.3.2    Level: 2    Role: D/V
 Ensure that data cards are maintained for significant training datasets, detailing characteristics, motivations, composition, collection processes, preprocessing, licenses, and recommended or discouraged uses.
 #AC.6.3.3    Level: 2    Role: D/V
 Ensure that data cards document bias risks, demographic skews, and ethical considerations relevant to the dataset.
 #AC.6.3.4    Level: 2    Role: D/V
 Ensure that data cards are versioned along with datasets and updated whenever the dataset is modified.
 #AC.6.3.5    Level: 2    Role: D/V
 Ensure that data cards are reviewed and approved by both technical and non-technical stakeholders (e.g., compliance, ethics, domain experts).
 #AC.6.3.6    Level: 2    Role: D/V
 Ensure labeling and annotation quality through clear guidelines, cross-checks by reviewers, consensus mechanisms (such as monitoring inter-annotator agreement), and established processes for resolving discrepancies.
 #AC.6.3.7    Level: 3    Role: D/V
 Ensure that labels critical to safety, security, or fairness (e.g., identifying toxic content or critical medical findings) undergo mandatory independent dual review or an equally robust verification process.
 #AC.6.3.8    Level: 2    Role: D/V
 Ensure that labeling guides and instructions are comprehensive, version-controlled, and peer-reviewed.
 #AC.6.3.9    Level: 2    Role: D/V
 Ensure that data schemas for labels are clearly defined and version-controlled.
 #AC.6.3.10    Level: 2    Role: D/V
 Verify that outsourced or crowdsourced labeling workflows incorporate technical and procedural safeguards to ensure data confidentiality, data integrity, label quality, and to prevent data leakage.
 #AC.6.3.11    Level: 2    Role: D/V
 Verify that all personnel involved in data annotation have undergone background checks and are trained in data security and privacy.
 #AC.6.3.12    Level: 2    Role: D/V
 Ensure that all annotation personnel sign confidentiality and non-disclosure agreements.
 #AC.6.3.13    Level: 2    Role: D/V
 Ensure that annotation platforms implement access controls and monitor for insider threats.

#### AC.6.4 Dataset Quality Gates & Quarantine

 #AC.6.4.1    Level: 2    Role: D/V
 Verify that failed datasets are quarantined with audit trails.
 #AC.6.4.2    Level: 2    Role: D/V
 Verify that quality gates block subpar datasets unless exceptions have been approved.
 #AC.6.4.3    Level: 2    Role: V
 Verify that manual spot-checks conducted by domain experts cover a statistically significant sample size (e.g., ≥1% or 1,000 samples, whichever is greater, or as determined by risk assessment) to detect subtle quality issues not identified by automation.

#### AC.6.5 Threat/Poisoning Detection and Drift

 #AC.6.5.1    Level: 2    Role: D/V
 Verify that flagged samples prompt manual review before training.
 #AC.6.5.2    Level: 2    Role: V
 Verify that the results feed into the model's security dossier and support ongoing threat intelligence.
 #AC.6.5.3    Level: 3    Role: D/V
 Verify that the detection logic is updated with the latest threat intelligence.
 #AC.6.5.4    Level: 3    Role: D/V
 Verify that online learning pipelines monitor distribution drift.

#### AC.6.6 Deletion, Consent, Rights, Retention & Compliance

 #AC.6.6.1    Level: 1    Role: D/V
 Verify that training data deletion workflows remove both primary and derived data and evaluate the impact on the models. Ensure that any effects on the affected models are assessed and, if needed, addressed (e.g., through retraining or recalibration).
 #AC.6.6.2    Level: 2    Role: D
 Ensure mechanisms are established to track and honor the scope and status of user consent (including withdrawals) for data used in training, and that consent is confirmed before incorporating data into new training processes or major model updates.
 #AC.6.6.3    Level: 2    Role: V
 Ensure that workflows are tested annually and properly documented.
 #AC.6.6.4    Level: 1    Role: D/V
 Ensure that explicit retention periods are established for all training datasets.
 #AC.6.6.5    Level: 2    Role: D/V
 Confirm that datasets are automatically expired, deleted, or reviewed for deletion at the end of their lifecycle.
 #AC.6.6.6    Level: 2    Role: D/V
 Ensure that retention and deletion actions are logged and can be audited.
 #AC.6.6.7    Level: 2    Role: D/V
 Verify that data residency and cross-border transfer requirements are identified and enforced for all datasets.
 #AC.6.6.8    Level: 2    Role: D/V
 Ensure that sector-specific regulations (e.g., healthcare, finance) are identified and addressed in data handling.
 #AC.6.6.9    Level: 2    Role: D/V
 Ensure that compliance with applicable privacy laws (e.g., GDPR, CCPA) is documented and reviewed regularly.
 #AC.6.6.10    Level: 2    Role: D/V
 Ensure that mechanisms are in place to respond to data subject requests for access, correction, restriction, or objection.
 #AC.6.6.11    Level: 2    Role: D/V
 Ensure that requests are logged, tracked, and completed within legally mandated timeframes.
 #AC.6.6.12    Level: 2    Role: D/V
 Ensure that data subject rights processes are regularly tested and reviewed for effectiveness.

#### AC.6.7 Versioning and Change Management

 #AC.6.7.1    Level: 2    Role: D/V
 Ensure that an impact analysis is conducted before updating or replacing a dataset version, addressing model performance, fairness, and compliance.
 #AC.6.7.2    Level: 2    Role: D/V
 Verify that the results of the impact analysis are documented and reviewed by the relevant stakeholders.
 #AC.6.7.3    Level: 2    Role: D/V
 Verify that rollback plans are in place in case new versions introduce unacceptable risks or regressions.

#### AC.6.8 Synthetic Data Governance

 #AC.6.8.1    Level: 2    Role: D/V
 Ensure that the generation process, parameters, and intended use of synthetic data are properly documented.
 #AC.6.8.2    Level: 2    Role: D/V
 Ensure that synthetic data undergoes a risk assessment for bias, privacy leakage, and representational issues before being used in training.

#### AC.6.9 Access Monitoring

 #AC.6.9.1    Level: 2    Role: D/V
 Ensure that access logs are regularly reviewed for unusual patterns, such as large data exports or access from new locations.
 #AC.6.9.2    Level: 2    Role: D/V
 Ensure that alerts are generated for suspicious access events and investigated promptly.

#### AC.6.10 Governance of Adversarial Training

 #AC.6.10.1    Level: 2    Role: D/V
 Verify that when adversarial training is used, the generation, management, and versioning of adversarial datasets are properly documented and controlled.
 #AC.6.10.2    Level: 3    Role: D/V
 Ensure that the effect of adversarial robustness training on model performance (for both clean and adversarial inputs) and fairness metrics is assessed, documented, and continuously monitored.
 #AC.6.10.3    Level: 3    Role: D/V
 Ensure that strategies for adversarial training and robustness are regularly reviewed and updated to address evolving adversarial attack techniques.

---

### AC.7 Model Lifecycle Governance and Documentation

 #AC.7.1    Level: 2    Role: D/V
 Verify that all model artifacts use semantic versioning (MAJOR.MINOR.PATCH) with clearly documented criteria for when each version component should be incremented.
 #AC.7.2    Level: 2    Role: D/V
 Verify that emergency deployments require a documented security risk assessment and approval from a pre-designated security authority within pre-agreed timeframes.
 #AC.7.3    Level: 2    Role: V
 Verify that rollback artifacts (previous model versions, configurations, dependencies) are retained in accordance with organizational policies.
 #AC.7.4    Level: 2    Role: D/V
 Ensure that access to the audit log requires proper authorization and that all access attempts are recorded with the user's identity and a timestamp.
 #AC.7.5    Level: 1    Role: D/V
 Confirm that retired model artifacts are maintained in accordance with data retention policies.

---

### AC.8 Prompt, Input, and Output Safety Governance

#### AC.8.1 Prompt Injection Defense

 #AC.8.1.1    Level: 2    Role: D/V
 Ensure that adversarial evaluation tests (e.g., Red Team "many-shot" prompts) are conducted before every model or prompt-template release, with defined success-rate thresholds and automated blockers to prevent regressions.
 #AC.8.1.2    Level: 3    Role: D/V
 Verify that all prompt-filter rule updates, classifier model versions, and block-list changes are version-controlled and auditable.

#### AC.8.2 Resistance to Adversarial Examples

 #AC.8.2.1    Level: 3    Role: D/V
 Ensure that robustness metrics (success rates of known attack suites) are monitored over time through automation, and that any regressions trigger an alert.

#### AC.8.3 Content & Policy Screening

 #AC.8.3.1    Level: 2    Role: D
 Verify that the screening model or rule set is retrained or updated at least quarterly, incorporating newly observed jailbreak or policy bypass patterns.

#### AC.8.4 Input Rate Limiting and Abuse Prevention

 #AC.8.4.1    Level: 3    Role: V
 Verify that abuse prevention logs are retained and reviewed for emerging attack patterns.

#### AC.8.5 Input Provenance and Attribution

 #AC.8.5.1    Level: 1    Role: D/V
 Ensure that all user inputs are tagged with metadata (user ID, session, source, timestamp, IP address) upon ingestion.
 #AC.8.5.2    Level: 2    Role: D/V
 Ensure that provenance metadata is preserved and can be audited for all processed inputs.
 #AC.8.5.3    Level: 2    Role: D/V
 Ensure that anomalous or untrusted input sources are flagged and subjected to enhanced scrutiny or blocking.

---

### AC.9 Multimodal Validation, MLOps, and Infrastructure Governance

#### AC.9.1 Multimodal Security Validation Pipeline

 #AC.9.1.1    Level: 3    Role: D/V
 Verify that modality-specific content classifiers are updated according to documented schedules (at least quarterly) with new threat patterns, adversarial examples, and performance benchmarks maintained above baseline thresholds.

#### AC.9.2 CI/CD and Build Security

 #AC.9.2.1    Level: 1    Role: D/V
 Ensure that infrastructure-as-code is scanned with every commit, and that merges are blocked if critical or high-severity issues are found.
 #AC.9.2.2    Level: 2    Role: D/V
 Ensure that CI/CD pipelines use short-lived, scoped identities to access secrets and infrastructure.
 #AC.9.2.3    Level: 2    Role: D/V
 Verify that build environments are isolated from production networks and data.

#### AC.9.3 Container and Image Security

 #AC.9.3.1    Level: 2    Role: D/V
 Verify that container images are scanned to block hardcoded secrets (e.g., API keys, credentials, certificates).
 #AC.9.3.2    Level: 1    Role: D/V
 Verify that container images are scanned according to organizational schedules, with CRITICAL vulnerabilities blocking deployment based on organizational risk thresholds.

#### AC.9.4 Monitoring, Alerting & SIEM

 #AC.9.4.1    Level: 2    Role: V
 Verify that security alerts integrate with SIEM platforms (Splunk, Elastic, or Sentinel) using CEF or STIX/TAXII formats with automated enrichment.

#### AC.9.5 Vulnerability Management

 #AC.9.5.1    Level: 2    Role: D/V
 Ensure that HIGH severity vulnerabilities are patched according to organizational risk management timelines, with emergency procedures in place for actively exploited CVEs.

#### AC.9.6 Configuration and Drift Control

 #AC.9.6.1    Level: 2    Role: D/V
 Verify that configuration drift is detected using tools (Chef InSpec, AWS Config) according to organizational monitoring requirements, with automatic rollback for unauthorized changes.

#### AC.9.7 Production Environment Hardening

 #AC.9.7.1    Level: 2    Role: D/V
 Verify that production environments block SSH access, disable debug endpoints, and require change requests that include organizational advance notice requirements, except in emergencies.

#### AC.9.8 Release Promotion Gates

 #AC.9.8.1    Level: 2    Role: D/V
 Verify that promotion gates include automated security tests (SAST, DAST, container scanning) with zero CRITICAL findings required for approval.

#### AC.9.9 Workload, Capacity, and Cost Monitoring

 #AC.9.9.1    Level: 1    Role: D/V
 Ensure that GPU/TPU utilization is monitored, with alerts triggered at organization-defined thresholds, and that automatic scaling or load balancing is activated according to capacity management policies.
 #AC.9.9.2    Level: 1    Role: D/V
 Verify that AI workload metrics (inference latency, throughput, error rates) are collected in accordance with organizational monitoring requirements and correlated with infrastructure utilization.
 #AC.9.9.3    Level: 2    Role: V
 Verify that cost monitoring tracks spending by workload or tenant, includes alerts based on organizational budget thresholds, and implements automated controls for budget overruns.
 #AC.9.9.4    Level: 3    Role: V
 Verify that capacity planning utilizes historical data with forecasting periods defined by the organization and includes automated resource provisioning based on demand patterns.

#### AC.9.10 Approvals & Audit Trails

 #AC.9.10.1    Level: 1    Role: D/V
 Verify that environment promotion requires approval from organizationally designated authorized personnel, utilizing cryptographic signatures and maintaining immutable audit trails.

#### AC.9.11 IaC Governance

 #AC.9.11.1    Level: 2    Role: D/V
 Ensure that infrastructure-as-code changes undergo peer review, automated testing, and security scanning before merging into the main branch.

#### AC.9.12 Data Handling in Non-Production Environments

 #AC.9.12.1    Level: 2    Role: D/V
 Verify that non-production data is anonymized in accordance with organizational privacy requirements, synthetic data generation standards, or complete data masking with verified PII removal.

#### AC.9.13 Backup and Disaster Recovery

 #AC.9.13.1    Level: 1    Role: D/V
 Verify that infrastructure configurations are backed up according to organizational backup schedules to geographically separate regions, implementing the 3-2-1 backup strategy.
 #AC.9.13.2    Level: 2    Role: V
 Verify that recovery procedures are tested and validated through automated testing according to organizational schedules, ensuring RTO and RPO targets meet organizational requirements.
 #AC.9.13.3    Level: 3    Role: V
 Verify that disaster recovery plans include AI-specific runbooks covering model weight restoration, GPU cluster rebuilding, and service dependency mapping.

#### AC.9.14 Compliance & Documentation

 #AC.9.14.1    Level: 2    Role: D/V
 Verify that infrastructure compliance is assessed according to organizational schedules against SOC 2, ISO 27001, or FedRAMP controls, using automated evidence collection.
 #AC.9.14.2    Level: 2    Role: V
 Verify that infrastructure documentation includes network diagrams, data flow maps, and threat models that are updated in accordance with organizational change management requirements.
 #AC.9.14.3    Level: 3    Role: D/V
 Ensure that infrastructure changes undergo automated compliance impact assessments with regulatory approval workflows for high-risk modifications.

#### AC.9.15 Hardware & Supply Chain

 #AC.9.15.1    Level: 2    Role: D/V
 Ensure that AI accelerator firmware (GPU BIOS, TPU firmware) is authenticated with cryptographic signatures and updated in accordance with organizational patch management schedules.
 #AC.9.15.2    Level: 3    Role: V
 Ensure that the AI hardware supply chain incorporates provenance verification using manufacturer certificates and validates tamper-evident packaging.

#### AC.9.16 Cloud Strategy & Portability

 #AC.9.16.1    Level: 3    Role: V
 Verify that cloud vendor lock-in prevention includes portable infrastructure-as-code, standardized APIs, and data export capabilities with format conversion tools.
 #AC.9.16.2    Level: 3    Role: V
 Verify that multi-cloud cost optimization includes security controls to prevent resource sprawl as well as unauthorized cross-cloud data transfer charges.

#### AC.9.17 GitOps & Self-Healing

 #AC.9.17.1    Level: 2    Role: D/V
 Verify that GitOps repositories require signed commits using GPG keys and enforce branch protection rules that prevent direct pushes to main branches.
 #AC.9.17.2    Level: 3    Role: V
 Verify that self-healing infrastructure includes security event correlation with automated incident response and workflows for stakeholder notification.

#### AC.9.18 Zero-Trust, Agents, Provisioning, and Residency Attestation

 #AC.9.18.1    Level: 2    Role: D/V
 Ensure that cloud resource access incorporates zero-trust verification with continuous authentication.
 #AC.9.18.2    Level: 2    Role: D/V
 Ensure that automated infrastructure provisioning includes security policy validation and blocks deployment for non-compliant configurations.
 #AC.9.18.3    Level: 2    Role: D/V
 Ensure that automated infrastructure provisioning validates security policies during CI/CD, blocking deployment of non-compliant configurations.
 #AC.9.18.4    Level: 3    Role: D/V
 Verify that data residency requirements are enforced through cryptographic attestation of storage locations.
 #AC.9.18.5    Level: 3    Role: D/V
 Ensure that cloud provider security assessments incorporate agent-specific threat modeling and risk analysis.

## Appendix D: AI-Assisted Secure Coding Governance and Verification

### Objective

This chapter defines baseline organizational controls for the safe and effective use of AI-assisted coding tools during software development, ensuring security and traceability throughout the SDLC.

---

### AD.1 AI-Assisted Secure-Coding Workflow

Integrate AI tools into the organization’s secure software development lifecycle (SSDLC) without compromising existing security controls.

 #AD.1.1    Level: 1    Role: D/V
 Ensure that the documented workflow specifies when and how AI tools can generate, refactor, or review code.
 #AD.1.2    Level: 2    Role: D
 Verify that the workflow corresponds to each SSDLC phase (design, implementation, code review, testing, deployment).
 #AD.1.3    Level: 3    Role: D/V
 Verify that metrics (e.g., vulnerability density, mean time to detect) are collected on AI-produced code and compared to human-only baselines.

---

### AD.2 AI Tool Qualification & Threat Modeling

Ensure AI coding tools are evaluated for security capabilities, risks, and supply-chain impact before adoption.

 #AD.2.1    Level: 1    Role: D/V
 Ensure that a threat model for each AI tool identifies risks related to misuse, model inversion, data leakage, and dependency chains.
 #AD.2.2    Level: 2    Role: D
 Ensure that tool evaluations include static and dynamic analysis of any local components, as well as assessment of SaaS endpoints (TLS, authentication/authorization, logging).
 #AD.2.3    Level: 3    Role: D/V
 Verify that evaluations follow a recognized framework and are conducted again after major version changes.

---

### AD.3 Secure Prompt and Context Management

Prevent leakage of secrets, proprietary code, and personal data when creating prompts or contexts for AI models.

 #AD.3.1    Level: 1    Role: D/V
 Ensure that written guidelines explicitly prohibit sending secrets, credentials, or classified information in prompts.
 #AD.3.2    Level: 2    Role: D
 Verify that technical controls (client-side redaction, approved context filters) automatically remove sensitive artifacts.
 #AD.3.3    Level: 3    Role: D/V
 Verify that prompts and responses are tokenized and encrypted both in transit and at rest, and ensure that retention periods comply with the data classification policy.

---

### AD.4 Validation of AI-Generated Code

Identify and fix vulnerabilities introduced by AI-generated code before merging or deployment.

 #AD.4.1    Level: 1    Role: D/V
 Ensure that AI-generated code is always subject to human code review.
 #AD.4.2    Level: 2    Role: D
 Ensure that automated scanners (SAST/IAST/DAST) run on every pull request containing AI-generated code and block merges when critical issues are found.
 #AD.4.3    Level: 3    Role: D/V
 Verify that differential fuzz testing or property-based tests confirm security-critical behaviors (e.g., input validation, authorization logic).

---

### AD.5 Explainability & Traceability of Code Suggestions

Give auditors and developers an understanding of why a suggestion was made and how it developed.

 #AD.5.1    Level: 1    Role: D/V
 Verify that prompt/response pairs are logged with commit IDs.
 #AD.5.2    Level: 2    Role: D
 Verify that developers can display model citations (training excerpts, documentation) supporting a suggestion.
 #AD.5.3    Level: 3    Role: D/V
 Verify that explainability reports are stored with design artifacts and referenced in security reviews, meeting ISO/IEC 42001 traceability principles.

---

### AD.6 Continuous Feedback & Model Fine-Tuning

Enhance model security performance over time while avoiding negative drift.

 #AD.6.1    Level: 1    Role: D/V
 Verify that developers can flag insecure or non-compliant suggestions and that these flags are tracked.
 #AD.6.2    Level: 2    Role: D
 Verify that aggregated feedback informs periodic fine-tuning or retrieval-augmented generation using vetted secure-coding corpora (e.g., OWASP Cheat Sheets).
 #AD.6.3    Level: 3    Role: D/V
 Verify that a closed-loop evaluation harness runs regression tests after each fine-tune; security metrics must meet or exceed previous baselines before deployment.

---

#### References

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Appendix E: Example Tools and Frameworks

### Objective

This chapter provides examples of tools and frameworks that can support the implementation or fulfillment of a given AISVS requirement. These should not be considered recommendations or endorsements by the AISVS team or the OWASP GenAI Security Project.

---

### AE.1 Training Data Governance and Bias Management

Tools used for data analytics, governance, and bias management.

 #AE.1.1    Section: 1.1
 Data Inventory Tooling: Data inventory management tools such as...
 #AE.1.2    Section: 1.2
 Encryption In Transit Use TLS for HTTPS-based applications, using tools like OpenSSL and Python's`ssl`library.

---

### AE.2 User Input Validation

Tools to handle and validate user inputs.

 #AE.2.1    Section: 2.1
 Prompt Injection Defense Tooling: Use guardrail tools like NVIDIA's NeMo or Guardrails AI.

---

## Appendix B: Strategic Controls

### C4.15 Quantum-Resistant Infrastructure Security

Prepare AI infrastructure for quantum computing threats by implementing post-quantum cryptography and quantum-safe protocols.

 #4.15.1    Level: 3    Role: D/V
 Verify that the AI infrastructure implements NIST-approved post-quantum cryptographic algorithms (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) for key exchange and digital signatures.
 #4.15.2    Level: 3    Role: D/V
 Ensure that quantum key distribution (QKD) systems are implemented for high-security AI communications using quantum-safe key management protocols.
 #4.15.3    Level: 3    Role: D/V
 Verify that cryptographic agility frameworks enable rapid migration to new post-quantum algorithms through automated certificate and key rotation.
 #4.15.4    Level: 3    Role: V
 Verify that quantum threat modeling evaluates AI infrastructure vulnerability to quantum attacks, including documented migration timelines and risk assessments.
 #4.15.5    Level: 3    Role: D/V
 Confirm that hybrid classical-quantum cryptographic systems offer defense-in-depth throughout the quantum transition period by implementing performance monitoring.

---

### C4.17 Zero-Knowledge Infrastructure

Develop zero-knowledge proof systems to enable privacy-preserving AI verification and authentication without exposing sensitive information.

 #4.17.1    Level: 3    Role: D/V
 Verify that zero-knowledge proofs (ZK-SNARKs, ZK-STARKs) validate AI model integrity and training provenance without revealing model weights or training data.
 #4.17.2    Level: 3    Role: D/V
 Confirm that ZK-based authentication systems provide privacy-preserving user verification for AI services without disclosing identity-related information.
 #4.17.3    Level: 3    Role: D/V
 Private set intersection (PSI) protocols enable secure data matching for federated AI by allowing multiple parties to identify common elements across their datasets without revealing any other information about their individual data. Through cryptographic techniques, PSI ensures that only the intersection of the datasets is disclosed, keeping the rest of the data private. This means that each participant's dataset remains confidential, preventing exposure of sensitive or proprietary information while still enabling collaborative analysis in federated AI environments.
 #4.17.4    Level: 3    Role: D/V
 Verify that zero-knowledge machine learning (ZKML) systems enable verifiable AI inferences through cryptographic proofs of correct computation.
 #4.17.5    Level: 3    Role: D/V
 Verify that ZK-rollups offer scalable, privacy-preserving AI transaction processing by enabling batch verification and reducing computational overhead.

---

### C4.18 Side-Channel Attack Prevention

Protect AI infrastructure from timing, power, electromagnetic, and cache-based side-channel attacks that may leak sensitive information.

 #4.18.1    Level: 3    Role: D/V
 Verify that AI inference timing is normalized using constant-time algorithms and padding to prevent timing-based model extraction attacks.
 #4.18.2    Level: 3    Role: D/V
 Verify that power analysis protection includes noise injection, power line filtering, and randomized execution patterns for AI hardware.
 #4.18.3    Level: 3    Role: D/V
 Verify that cache-based side-channel mitigation employs cache partitioning, randomization, and flush instructions to prevent information leakage.
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
 Verify that the custom ASIC security features include on-chip security processors, a hardware root of trust, and secure key storage with tamper detection.
 #4.19.4    Level: 3    Role: D/V
 Verify that optical computing systems implement quantum-safe optical encryption, secure photonic switching, and protected optical signal processing.
 #4.19.5    Level: 3    Role: D/V
 Verify that hybrid analog-digital AI chips incorporate secure analog computation, protected weight storage, and authenticated analog-to-digital conversion.

---

### C4.20 Privacy-Preserving Computing Infrastructure

Implement infrastructure controls for privacy-preserving computation to safeguard sensitive data during AI processing and analysis.

 #4.20.1    Level: 3    Role: D/V
 Verify that the homomorphic encryption infrastructure enables encrypted computation on sensitive AI workloads with cryptographic integrity verification and performance monitoring.
 #4.20.2    Level: 3    Role: D/V
 Verify that private information retrieval systems allow database queries without disclosing query patterns by using cryptographic protection of access patterns.
 #4.20.3    Level: 3    Role: D/V
 Verify that secure multi-party computation protocols enable privacy-preserving AI inference without revealing individual inputs or intermediate computations.
 #4.20.4    Level: 3    Role: D/V
 Verify that privacy-preserving key management includes distributed key generation, threshold cryptography, and secure key rotation with hardware-backed protection.
 #4.20.5    Level: 3    Role: D/V
 Verify that privacy-preserving compute performance is optimized through batching, caching, and hardware acceleration while maintaining cryptographic security guarantees.

 4.9.14.9.2    1: 2    D/V: D/V
 Verify that multi-cloud deployments use federated identity standards (e.g., OIDC, SAML) with centralized policy enforcement across providers.
 4.9.14.9.3    1: 2    D/V: D/V
 Verify that cross-cloud and hybrid data transfers use end-to-end encryption with customer-managed keys and enforce jurisdictional data residency requirements.
 4.9.14.9.1    1: 1    D/V: D/V
 Verify that cloud storage integration uses end-to-end encryption with agent-controlled key management.
 4.9.14.9.2    1: 2    D/V: D/V
 Verify that security boundaries in hybrid deployments are clearly defined with encrypted communication channels.

