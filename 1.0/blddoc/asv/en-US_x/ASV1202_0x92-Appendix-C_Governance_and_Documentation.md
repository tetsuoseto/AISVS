# Appendix C: AI Security Governance and Documentation (Reorganized)

## Objective

This appendix outlines the fundamental requirements for establishing organizational structures, policies, documentation, and processes to manage AI security throughout the system lifecycle.

---

## AC.1 Adoption of AI Risk Management Framework

|   #    | Description                                                                                                           | Level | Role |
| :----: | --------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.1.1 | Verify that an AI-specific risk assessment methodology is documented and implemented.                                 |   1   | D/V  |
| AC.1.2 | Ensure that risk assessments are conducted at critical stages in the AI lifecycle and before any significant changes. |   2   |  D   |
| AC.1.3 | Verify that the risk management framework aligns with established standards (e.g., NIST AI RMF).                      |   3   | D/V  |

---

## AC.2 AI Security Policy & Procedures

|   #    | Description                                                                                                                | Level | Role |
| :----: | -------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.2.1 | Verify that documented AI security policies are in place.                                                                  |   1   | D/V  |
| AC.2.2 | Ensure that policies are reviewed and updated at least annually and following significant changes in the threat landscape. |   2   |  D   |
| AC.2.3 | Verify that policies cover all AISVS categories and comply with applicable regulatory requirements.                        |   3   | D/V  |

---

## AC.3 Roles & Responsibilities for AI Security

|   #    | Description                                                                                           | Level | Role |
| :----: | ----------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.3.1 | Verify that AI security roles and responsibilities are properly documented.                           |   1   | D/V  |
| AC.3.2 | Ensure that responsible individuals have the appropriate security expertise.                          |   2   |  D   |
| AC.3.3 | Verify that an AI ethics committee or governance board has been established for high-risk AI systems. |   3   | D/V  |

---

## AC.4 Enforcement of Ethical AI Guidelines

|   #    | Description                                                                     | Level | Role |
| :----: | ------------------------------------------------------------------------------- | :---: | :--: |
| AC.4.1 | Confirm that ethical guidelines for AI development and deployment are in place. |   1   | D/V  |
| AC.4.2 | Ensure that mechanisms are in place to detect and report ethical violations.    |   2   |  D   |
| AC.4.3 | Ensure that regular ethical reviews of deployed AI systems are conducted.       |   3   | D/V  |

---

## AC.5 AI Regulatory Compliance Monitoring

|   #    | Description                                                                     | Level | Role |
| :----: | ------------------------------------------------------------------------------- | :---: | :--: |
| AC.5.1 | Ensure processes are in place to identify applicable AI regulations.            |   1   | D/V  |
| AC.5.2 | Verify that compliance with all regulatory requirements has been assessed.      |   2   |  D   |
| AC.5.3 | Ensure that regulatory changes prompt timely reviews and updates to AI systems. |   3   | D/V  |

---

## AC.6 Training Data Governance, Documentation, and Process

### AC.6.1 Data Sourcing and Due Diligence

|    #     | Description                                                                                                                                                                                                                                                                           | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.6.1.1 | Ensure that only datasets verified for quality, representativeness, ethical sourcing, and license compliance are used, minimizing risks of poisoning, embedded bias, and intellectual property infringement.                                                                          |   1   | D/V  |
| AC.6.1.2 | Ensure that third-party data suppliers, including providers of pre-trained models and external datasets, undergo due diligence for security, privacy, ethical sourcing, and data quality before their data or models are integrated.                                                  |   2   | D/V  |
| AC.6.1.3 | Verify that external transfers utilize TLS/authentication and include integrity checks.                                                                                                                                                                                               |   1   |  D   |
| AC.6.1.4 | Ensure that high-risk data sources (e.g., open-source datasets with unknown origins, unvetted suppliers) undergo enhanced scrutiny before being used in sensitive applications, including sandboxed analysis, thorough quality and bias assessments, and focused poisoning detection. |   2   | D/V  |
| AC.6.1.5 | Verify that pre-trained models obtained from third parties are evaluated for embedded biases, potential backdoors, the integrity of their architecture, and the provenance of their original training data before fine-tuning or deployment.                                          |   3   | D/V  |

### AC.6.2 Bias and Fairness Management

|    #     | Description                                                                                                                                                                                                                                                                                                                           | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.6.2.1 | Verify that datasets are analyzed for representational imbalance and potential biases across legally protected attributes (e.g., race, gender, age) and other ethically sensitive characteristics relevant to the model's application domain (e.g., socio-economic status, location).                                                 |   1   | D/V  |
| AC.6.2.2 | Verify that identified biases are mitigated through documented strategies such as re-balancing, targeted data augmentation, algorithmic adjustments (e.g., pre-processing, in-processing, post-processing techniques), or re-weighting, and that the impact of mitigation on both fairness and overall model performance is assessed. |   2   | D/V  |
| AC.6.2.3 | Verify that post-training fairness metrics have been evaluated and documented.                                                                                                                                                                                                                                                        |   2   | D/V  |
| AC.6.2.4 | Verify that a lifecycle bias management policy designates owners and establishes a review schedule.                                                                                                                                                                                                                                   |   3   | D/V  |

### AC.6.3 Labeling and Annotation Governance

|     #     | Description                                                                                                                                                                                                             | Level | Role |
| :-------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.6.3.1  | Verify that labeling/annotation quality is ensured through reviewer cross-checks or consensus.                                                                                                                          |   2   | D/V  |
| AC.6.3.2  | Ensure that data cards are maintained for significant training datasets, detailing characteristics, motivations, composition, collection processes, preprocessing, licenses, and recommended or discouraged uses.       |   2   | D/V  |
| AC.6.3.3  | Ensure that data cards document bias risks, demographic skews, and ethical considerations relevant to the dataset.                                                                                                      |   2   | D/V  |
| AC.6.3.4  | Ensure that data cards are versioned along with datasets and updated whenever the dataset is modified.                                                                                                                  |   2   | D/V  |
| AC.6.3.5  | Ensure that data cards are reviewed and approved by both technical and non-technical stakeholders (e.g., compliance, ethics, domain experts).                                                                           |   2   | D/V  |
| AC.6.3.6  | Ensure labeling and annotation quality through clear guidelines, cross-checks by reviewers, consensus mechanisms (such as monitoring inter-annotator agreement), and established processes for resolving discrepancies. |   2   | D/V  |
| AC.6.3.7  | Ensure that labels critical to safety, security, or fairness (e.g., identifying toxic content or critical medical findings) undergo mandatory independent dual review or an equally robust verification process.        |   3   | D/V  |
| AC.6.3.8  | Ensure that labeling guides and instructions are comprehensive, version-controlled, and peer-reviewed.                                                                                                                  |   2   | D/V  |
| AC.6.3.9  | Ensure that data schemas for labels are clearly defined and version-controlled.                                                                                                                                         |   2   | D/V  |
| AC.6.3.10 | Verify that outsourced or crowdsourced labeling workflows incorporate technical and procedural safeguards to ensure data confidentiality, data integrity, label quality, and to prevent data leakage.                   |   2   | D/V  |
| AC.6.3.11 | Verify that all personnel involved in data annotation have undergone background checks and are trained in data security and privacy.                                                                                    |   2   | D/V  |
| AC.6.3.12 | Ensure that all annotation personnel sign confidentiality and non-disclosure agreements.                                                                                                                                |   2   | D/V  |
| AC.6.3.13 | Ensure that annotation platforms implement access controls and monitor for insider threats.                                                                                                                             |   2   | D/V  |

### AC.6.4 Dataset Quality Gates & Quarantine

|    #     | Description                                                                                                                                                                                                                                                    | Level | Role |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.6.4.1 | Verify that failed datasets are quarantined with audit trails.                                                                                                                                                                                                 |   2   | D/V  |
| AC.6.4.2 | Verify that quality gates block subpar datasets unless exceptions have been approved.                                                                                                                                                                          |   2   | D/V  |
| AC.6.4.3 | Verify that manual spot-checks conducted by domain experts cover a statistically significant sample size (e.g., ≥1% or 1,000 samples, whichever is greater, or as determined by risk assessment) to detect subtle quality issues not identified by automation. |   2   |  V   |

### AC.6.5 Threat/Poisoning Detection and Drift

|    #     | Description                                                                                             | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.6.5.1 | Verify that flagged samples prompt manual review before training.                                       |   2   | D/V  |
| AC.6.5.2 | Verify that the results feed into the model's security dossier and support ongoing threat intelligence. |   2   |  V   |
| AC.6.5.3 | Verify that the detection logic is updated with the latest threat intelligence.                         |   3   | D/V  |
| AC.6.5.4 | Verify that online learning pipelines monitor distribution drift.                                       |   3   | D/V  |

### AC.6.6 Deletion, Consent, Rights, Retention & Compliance

|     #     | Description                                                                                                                                                                                                                                                 | Level | Role |
| :-------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.6.6.1  | Verify that training data deletion workflows remove both primary and derived data and evaluate the impact on the models. Ensure that any effects on the affected models are assessed and, if needed, addressed (e.g., through retraining or recalibration). |   1   | D/V  |
| AC.6.6.2  | Ensure mechanisms are established to track and honor the scope and status of user consent (including withdrawals) for data used in training, and that consent is confirmed before incorporating data into new training processes or major model updates.    |   2   |  D   |
| AC.6.6.3  | Ensure that workflows are tested annually and properly documented.                                                                                                                                                                                          |   2   |  V   |
| AC.6.6.4  | Ensure that explicit retention periods are established for all training datasets.                                                                                                                                                                           |   1   | D/V  |
| AC.6.6.5  | Confirm that datasets are automatically expired, deleted, or reviewed for deletion at the end of their lifecycle.                                                                                                                                           |   2   | D/V  |
| AC.6.6.6  | Ensure that retention and deletion actions are logged and can be audited.                                                                                                                                                                                   |   2   | D/V  |
| AC.6.6.7  | Verify that data residency and cross-border transfer requirements are identified and enforced for all datasets.                                                                                                                                             |   2   | D/V  |
| AC.6.6.8  | Ensure that sector-specific regulations (e.g., healthcare, finance) are identified and addressed in data handling.                                                                                                                                          |   2   | D/V  |
| AC.6.6.9  | Ensure that compliance with applicable privacy laws (e.g., GDPR, CCPA) is documented and reviewed regularly.                                                                                                                                                |   2   | D/V  |
| AC.6.6.10 | Ensure that mechanisms are in place to respond to data subject requests for access, correction, restriction, or objection.                                                                                                                                  |   2   | D/V  |
| AC.6.6.11 | Ensure that requests are logged, tracked, and completed within legally mandated timeframes.                                                                                                                                                                 |   2   | D/V  |
| AC.6.6.12 | Ensure that data subject rights processes are regularly tested and reviewed for effectiveness.                                                                                                                                                              |   2   | D/V  |

### AC.6.7 Versioning and Change Management

|    #     | Description                                                                                                                                         | Level | Role |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.6.7.1 | Ensure that an impact analysis is conducted before updating or replacing a dataset version, addressing model performance, fairness, and compliance. |   2   | D/V  |
| AC.6.7.2 | Verify that the results of the impact analysis are documented and reviewed by the relevant stakeholders.                                            |   2   | D/V  |
| AC.6.7.3 | Verify that rollback plans are in place in case new versions introduce unacceptable risks or regressions.                                           |   2   | D/V  |

### AC.6.8 Synthetic Data Governance

|    #     | Description                                                                                                                                  | Level | Role |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.6.8.1 | Ensure that the generation process, parameters, and intended use of synthetic data are properly documented.                                  |   2   | D/V  |
| AC.6.8.2 | Ensure that synthetic data undergoes a risk assessment for bias, privacy leakage, and representational issues before being used in training. |   2   | D/V  |

### AC.6.9 Access Monitoring

|    #     | Description                                                                                                                   | Level | Role |
| :------: | ----------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.6.9.1 | Ensure that access logs are regularly reviewed for unusual patterns, such as large data exports or access from new locations. |   2   | D/V  |
| AC.6.9.2 | Ensure that alerts are generated for suspicious access events and investigated promptly.                                      |   2   | D/V  |

### AC.6.10 Governance of Adversarial Training

|     #     | Description                                                                                                                                                                                      | Level | Role |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| AC.6.10.1 | Verify that when adversarial training is used, the generation, management, and versioning of adversarial datasets are properly documented and controlled.                                        |   2   | D/V  |
| AC.6.10.2 | Ensure that the effect of adversarial robustness training on model performance (for both clean and adversarial inputs) and fairness metrics is assessed, documented, and continuously monitored. |   3   | D/V  |
| AC.6.10.3 | Ensure that strategies for adversarial training and robustness are regularly reviewed and updated to address evolving adversarial attack techniques.                                             |   3   | D/V  |

---

## AC.7 Model Lifecycle Governance and Documentation

|   #    | Description                                                                                                                                                         | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.7.1 | Verify that all model artifacts use semantic versioning (MAJOR.MINOR.PATCH) with clearly documented criteria for when each version component should be incremented. |   2   | D/V  |
| AC.7.2 | Verify that emergency deployments require a documented security risk assessment and approval from a pre-designated security authority within pre-agreed timeframes. |   2   | D/V  |
| AC.7.3 | Verify that rollback artifacts (previous model versions, configurations, dependencies) are retained in accordance with organizational policies.                     |   2   |  V   |
| AC.7.4 | Ensure that access to the audit log requires proper authorization and that all access attempts are recorded with the user's identity and a timestamp.               |   2   | D/V  |
| AC.7.5 | Confirm that retired model artifacts are maintained in accordance with data retention policies.                                                                     |   1   | D/V  |

---

## AC.8 Prompt, Input, and Output Safety Governance

### AC.8.1 Prompt Injection Defense

|    #     | Description                                                                                                                                                                                                                    | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| AC.8.1.1 | Ensure that adversarial evaluation tests (e.g., Red Team "many-shot" prompts) are conducted before every model or prompt-template release, with defined success-rate thresholds and automated blockers to prevent regressions. |   2   | D/V  |
| AC.8.1.2 | Verify that all prompt-filter rule updates, classifier model versions, and block-list changes are version-controlled and auditable.                                                                                            |   3   | D/V  |

### AC.8.2 Resistance to Adversarial Examples

|    #     | Description                                                                                                                                                  | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| AC.8.2.1 | Ensure that robustness metrics (success rates of known attack suites) are monitored over time through automation, and that any regressions trigger an alert. |   3   | D/V  |

### AC.8.3 Content & Policy Screening

|    #     | Description                                                                                                                                               | Level | Role |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.8.3.1 | Verify that the screening model or rule set is retrained or updated at least quarterly, incorporating newly observed jailbreak or policy bypass patterns. |   2   |  D   |

### AC.8.4 Input Rate Limiting and Abuse Prevention

|    #     | Description                                                                               | Level | Role |
| :------: | ----------------------------------------------------------------------------------------- | :---: | :--: |
| AC.8.4.1 | Verify that abuse prevention logs are retained and reviewed for emerging attack patterns. |   3   |  V   |

### AC.8.5 Input Provenance and Attribution

|    #     | Description                                                                                                            | Level | Role |
| :------: | ---------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.8.5.1 | Ensure that all user inputs are tagged with metadata (user ID, session, source, timestamp, IP address) upon ingestion. |   1   | D/V  |
| AC.8.5.2 | Ensure that provenance metadata is preserved and can be audited for all processed inputs.                              |   2   | D/V  |
| AC.8.5.3 | Ensure that anomalous or untrusted input sources are flagged and subjected to enhanced scrutiny or blocking.           |   2   | D/V  |

---

## AC.9 Multimodal Validation, MLOps, and Infrastructure Governance

### AC.9.1 Multimodal Security Validation Pipeline

|    #     | Description                                                                                                                                                                                                                           | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.1.1 | Verify that modality-specific content classifiers are updated according to documented schedules (at least quarterly) with new threat patterns, adversarial examples, and performance benchmarks maintained above baseline thresholds. |   3   | D/V  |

### AC.9.2 CI/CD and Build Security

|    #     | Description                                                                                                                                 | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.2.1 | Ensure that infrastructure-as-code is scanned with every commit, and that merges are blocked if critical or high-severity issues are found. |   1   | D/V  |
| AC.9.2.2 | Ensure that CI/CD pipelines use short-lived, scoped identities to access secrets and infrastructure.                                        |   2   | D/V  |
| AC.9.2.3 | Verify that build environments are isolated from production networks and data.                                                              |   2   | D/V  |

### AC.9.3 Container and Image Security

|    #     | Description                                                                                                                                                                | Level | Role |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.3.1 | Verify that container images are scanned to block hardcoded secrets (e.g., API keys, credentials, certificates).                                                           |   2   | D/V  |
| AC.9.3.2 | Verify that container images are scanned according to organizational schedules, with CRITICAL vulnerabilities blocking deployment based on organizational risk thresholds. |   1   | D/V  |

### AC.9.4 Monitoring, Alerting & SIEM

|    #     | Description                                                                                                                                         | Level | Role |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.4.1 | Verify that security alerts integrate with SIEM platforms (Splunk, Elastic, or Sentinel) using CEF or STIX/TAXII formats with automated enrichment. |   2   |  V   |

### AC.9.5 Vulnerability Management

|    #     | Description                                                                                                                                                                  | Level | Role |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.5.1 | Ensure that HIGH severity vulnerabilities are patched according to organizational risk management timelines, with emergency procedures in place for actively exploited CVEs. |   2   | D/V  |

### AC.9.6 Configuration and Drift Control

|    #     | Description                                                                                                                                                                              | Level | Role |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.6.1 | Verify that configuration drift is detected using tools (Chef InSpec, AWS Config) according to organizational monitoring requirements, with automatic rollback for unauthorized changes. |   2   | D/V  |

### AC.9.7 Production Environment Hardening

|    #     | Description                                                                                                                                                                                | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| AC.9.7.1 | Verify that production environments block SSH access, disable debug endpoints, and require change requests that include organizational advance notice requirements, except in emergencies. |   2   | D/V  |

### AC.9.8 Release Promotion Gates

|    #     | Description                                                                                                                                      | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| AC.9.8.1 | Verify that promotion gates include automated security tests (SAST, DAST, container scanning) with zero CRITICAL findings required for approval. |   2   | D/V  |

### AC.9.9 Workload, Capacity, and Cost Monitoring

|    #     | Description                                                                                                                                                                                                  | Level | Role |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| AC.9.9.1 | Ensure that GPU/TPU utilization is monitored, with alerts triggered at organization-defined thresholds, and that automatic scaling or load balancing is activated according to capacity management policies. |   1   | D/V  |
| AC.9.9.2 | Verify that AI workload metrics (inference latency, throughput, error rates) are collected in accordance with organizational monitoring requirements and correlated with infrastructure utilization.         |   1   | D/V  |
| AC.9.9.3 | Verify that cost monitoring tracks spending by workload or tenant, includes alerts based on organizational budget thresholds, and implements automated controls for budget overruns.                         |   2   |  V   |
| AC.9.9.4 | Verify that capacity planning utilizes historical data with forecasting periods defined by the organization and includes automated resource provisioning based on demand patterns.                           |   3   |  V   |

### AC.9.10 Approvals & Audit Trails

|     #     | Description                                                                                                                                                                           | Level | Role |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.10.1 | Verify that environment promotion requires approval from organizationally designated authorized personnel, utilizing cryptographic signatures and maintaining immutable audit trails. |   1   | D/V  |

### AC.9.11 IaC Governance

|     #     | Description                                                                                                                                   | Level | Role |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.11.1 | Ensure that infrastructure-as-code changes undergo peer review, automated testing, and security scanning before merging into the main branch. |   2   | D/V  |

### AC.9.12 Data Handling in Non-Production Environments

|     #     | Description                                                                                                                                                                                    | Level | Role |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.12.1 | Verify that non-production data is anonymized in accordance with organizational privacy requirements, synthetic data generation standards, or complete data masking with verified PII removal. |   2   | D/V  |

### AC.9.13 Backup and Disaster Recovery

|     #     | Description                                                                                                                                                                              | Level | Role |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.13.1 | Verify that infrastructure configurations are backed up according to organizational backup schedules to geographically separate regions, implementing the 3-2-1 backup strategy.         |   1   | D/V  |
| AC.9.13.2 | Verify that recovery procedures are tested and validated through automated testing according to organizational schedules, ensuring RTO and RPO targets meet organizational requirements. |   2   |  V   |
| AC.9.13.3 | Verify that disaster recovery plans include AI-specific runbooks covering model weight restoration, GPU cluster rebuilding, and service dependency mapping.                              |   3   |  V   |

### AC.9.14 Compliance & Documentation

|     #     | Description                                                                                                                                                                              | Level | Role |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.14.1 | Verify that infrastructure compliance is assessed according to organizational schedules against SOC 2, ISO 27001, or FedRAMP controls, using automated evidence collection.              |   2   | D/V  |
| AC.9.14.2 | Verify that infrastructure documentation includes network diagrams, data flow maps, and threat models that are updated in accordance with organizational change management requirements. |   2   |  V   |
| AC.9.14.3 | Ensure that infrastructure changes undergo automated compliance impact assessments with regulatory approval workflows for high-risk modifications.                                       |   3   | D/V  |

### AC.9.15 Hardware & Supply Chain

|     #     | Description                                                                                                                                                                           | Level | Role |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.15.1 | Ensure that AI accelerator firmware (GPU BIOS, TPU firmware) is authenticated with cryptographic signatures and updated in accordance with organizational patch management schedules. |   2   | D/V  |
| AC.9.15.2 | Ensure that the AI hardware supply chain incorporates provenance verification using manufacturer certificates and validates tamper-evident packaging.                                 |   3   |  V   |

### AC.9.16 Cloud Strategy & Portability

|     #     | Description                                                                                                                                                         | Level | Role |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.16.1 | Verify that cloud vendor lock-in prevention includes portable infrastructure-as-code, standardized APIs, and data export capabilities with format conversion tools. |   3   |  V   |
| AC.9.16.2 | Verify that multi-cloud cost optimization includes security controls to prevent resource sprawl as well as unauthorized cross-cloud data transfer charges.          |   3   |  V   |

### AC.9.17 GitOps & Self-Healing

|     #     | Description                                                                                                                                              | Level | Role |
| :-------: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AC.9.17.1 | Verify that GitOps repositories require signed commits using GPG keys and enforce branch protection rules that prevent direct pushes to main branches.   |   2   | D/V  |
| AC.9.17.2 | Verify that self-healing infrastructure includes security event correlation with automated incident response and workflows for stakeholder notification. |   3   |  V   |

### AC.9.18 Zero-Trust, Agents, Provisioning, and Residency Attestation

|     #     | Description                                                                                                                                      | Level | Role |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| AC.9.18.1 | Ensure that cloud resource access incorporates zero-trust verification with continuous authentication.                                           |   2   | D/V  |
| AC.9.18.2 | Ensure that automated infrastructure provisioning includes security policy validation and blocks deployment for non-compliant configurations.    |   2   | D/V  |
| AC.9.18.3 | Ensure that automated infrastructure provisioning validates security policies during CI/CD, blocking deployment of non-compliant configurations. |   2   | D/V  |
| AC.9.18.4 | Verify that data residency requirements are enforced through cryptographic attestation of storage locations.                                     |   3   | D/V  |
| AC.9.18.5 | Ensure that cloud provider security assessments incorporate agent-specific threat modeling and risk analysis.                                    |   3   | D/V  |

