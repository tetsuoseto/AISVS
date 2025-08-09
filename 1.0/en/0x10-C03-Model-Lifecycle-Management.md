# C3 Model Lifecycle Management and Change Control

## Control Objective

AI systems must implement change control processes that prevent unauthorized or unsafe model modifications from reaching production. This control ensures model integrity throughout the entire lifecycle—from development and deployment to decommissioning—enabling rapid incident response and maintaining accountability for all changes.

Core Security Goal: Ensure that only authorized and validated models reach production by using controlled processes that maintain integrity, traceability, and recoverability.

---

## C3.1 Model Authorization and Integrity

Only authorized models with verified integrity are deployed to production environments.

|   #   | Description                                                                                                                                                                            | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 3.1.1 | Verify that all model artifacts (weights, configurations, tokenizers) are cryptographically signed by authorized entities before deployment.                                           |   1   | D/V  |
| 3.1.2 | Ensure that model integrity is verified at deployment and that signature verification failures prevent the model from loading.                                                         |   1   | D/V  |
| 3.1.3 | Verify that model provenance records include the identity of the authorizing entity, training data checksums, validation test results with pass/fail status, and a creation timestamp. |   2   | D/V  |
| 3.1.4 | Ensure that all model artifacts follow semantic versioning (MAJOR.MINOR.PATCH) with clearly documented criteria defining when each version component should be incremented.            |   2   | D/V  |
| 3.1.5 | Ensure that dependency tracking maintains a real-time inventory that allows for the rapid identification of all consuming systems.                                                     |   2   |  V   |

---

## C3.2 Model Validation & Testing

Models must pass defined security and safety validations prior to deployment.

|   #   | Description                                                                                                                                                                                              | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 3.2.1 | Ensure that models undergo automated security testing that includes input validation, output sanitization, and safety evaluations with pre-agreed organizational pass/fail thresholds before deployment. |   1   | D/V  |
| 3.2.2 | Verify that validation failures automatically block model deployment unless explicitly overridden by pre-designated authorized personnel with documented business justifications.                        |   1   | D/V  |
| 3.2.3 | Verify that test results are cryptographically signed and immutably linked to the specific model version hash being validated.                                                                           |   2   |  V   |
| 3.2.4 | Verify that emergency deployments require a documented security risk assessment and approval from a pre-designated security authority within pre-agreed timeframes.                                      |   2   | D/V  |

---

## C3.3 Controlled Deployment and Rollback

Model deployments must be controlled, monitored, and reversible.

|   #   | Description                                                                                                                                                                                                                                 | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 3.3.1 | Verify that production deployments use gradual rollout mechanisms (such as canary deployments and blue-green deployments) with automated rollback triggers based on pre-agreed error rates, latency thresholds, or security alert criteria. |   1   |  D   |
| 3.3.2 | Verify that rollback capabilities restore the entire model state (weights, configurations, dependencies) atomically within predefined organizational time windows.                                                                          |   1   | D/V  |
| 3.3.3 | Ensure that deployment processes validate cryptographic signatures and compute integrity checksums before activating the model, failing the deployment if any mismatch is detected.                                                         |   2   | D/V  |
| 3.3.4 | Verify that emergency model shutdown capabilities can disable model endpoints within predefined response times using automated circuit breakers or manual kill switches.                                                                    |   2   | D/V  |
| 3.3.5 | Verify that rollback artifacts (previous model versions, configurations, dependencies) are retained in accordance with organizational policies using immutable storage for incident response.                                               |   2   |  V   |

---

## C3.4 Change Accountability and Audit

All changes in the model lifecycle must be traceable and auditable.

|   #   | Description                                                                                                                                                                                                          | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 3.4.1 | Verify that all model changes (deployment, configuration, retirement) generate immutable audit records that include a timestamp, an authenticated actor identity, a change type, and before/after states.            |   1   |  V   |
| 3.4.2 | Ensure that access to audit logs requires proper authorization and that all access attempts are recorded with the user’s identity and a timestamp.                                                                   |   2   | D/V  |
| 3.4.3 | Verify that prompt templates and system messages are version-controlled in Git repositories, with mandatory code review and approval from designated reviewers before deployment.                                    |   2   | D/V  |
| 3.4.4 | Verify that audit records contain sufficient details (model hashes, configuration snapshots, dependency versions) to allow complete reconstruction of the model state for any timestamp within the retention period. |   2   |  V   |

---

## C3.5 Secure Development Practices

Model development and training processes must adhere to secure practices to prevent compromise.

|   #   | Description                                                                                                                                                                                                    | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 3.5.1 | Ensure that the model development, testing, and production environments are physically or logically separated. They should have no shared infrastructure, distinct access controls, and isolated data storage. |   1   |  D   |
| 3.5.2 | Verify that model training and fine-tuning take place in isolated environments with controlled network access.                                                                                                 |   1   |  D   |
| 3.5.3 | Verify that training data sources are validated through integrity checks and authenticated by trusted sources with a documented chain of custody before being used in model development.                       |   1   | D/V  |
| 3.5.4 | Ensure that model development artifacts (such as hyperparameters, training scripts, and configuration files) are stored in version control and require peer review approval before being used for training.    |   2   |  D   |

---

## C3.6 Model Retirement & Decommissioning

Models must be securely retired when they are no longer needed or when security issues are identified.

|   #   | Description                                                                                                                                                                                                               | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 3.6.1 | Ensure that model retirement processes automatically scan dependency graphs, identify all dependent systems, and provide pre-agreed advance notice periods before decommissioning.                                        |   1   |  D   |
| 3.6.2 | Verify that retired model artifacts are securely erased using cryptographic erasure or multi-pass overwriting in accordance with documented data retention policies and accompanied by verified destruction certificates. |   1   | D/V  |
| 3.6.3 | Ensure that model retirement events are logged with timestamps and actor identities, and that model signatures are revoked to prevent reuse.                                                                              |   2   |  V   |
| 3.6.4 | Verify that emergency model retirement can disable model access within pre-established emergency response timeframes using automated kill switches if critical security vulnerabilities are discovered.                   |   2   | D/V  |

---

## References

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

