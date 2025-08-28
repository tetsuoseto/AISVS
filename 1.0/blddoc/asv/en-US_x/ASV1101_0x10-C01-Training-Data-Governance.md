# C1 Training Data Governance & Bias Management

## Control Objective

Training data must be sourced, handled, and maintained in a manner that preserves provenance, security, quality, and fairness. Doing so fulfills legal obligations and reduces the risks of bias, poisoning, or privacy breaches during training that could affect the entire AI lifecycle.

---

## C1.1 Training Data Provenance

Maintain a verifiable inventory of all datasets, accept only trusted sources, and log every change for audit purposes.

|   #   | Description                                                                                                                                                                                    | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 1.1.1 | Ensure that an up-to-date inventory of every training data source—including origin, steward/owner, license, collection method, intended use constraints, and processing history—is maintained. |   1   | D/V  |
| 1.1.2 | Ensure that training data processes exclude unnecessary features, attributes, or fields (e.g., unused metadata, sensitive PII, leaked test data).                                              |   1   | D/V  |
| 1.1.3 | Ensure that all dataset changes undergo a logged approval workflow.                                                                                                                            |   2   | D/V  |
| 1.1.4 | Verify that datasets or subsets are watermarked or fingerprinted whenever feasible.                                                                                                            |   3   | D/V  |

---

## C1.2 Training Data Security and Integrity

Restrict access to training data, encrypt it both at rest and during transit, and verify its integrity to prevent tampering, theft, or data poisoning.

|   #   | Description                                                                                                                                             | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 1.2.1 | Verify that access controls safeguard training data storage and pipelines.                                                                              |   1   | D/V  |
| 1.2.2 | Ensure that all access to training data is logged, including the user, time, and action.                                                                |   2   | D/V  |
| 1.2.3 | Verify that training datasets are encrypted both in transit and at rest, using industry-standard cryptographic algorithms and key management practices. |   2   | D/V  |
| 1.2.4 | Verify that cryptographic hashes or digital signatures are used to ensure data integrity during the storage and transfer of training data.              |   2   | D/V  |
| 1.2.5 | Verify that automated detection techniques are applied to prevent unauthorized modifications or corruption of training data.                            |   2   | D/V  |
| 1.2.6 | Ensure that outdated training data is securely deleted or anonymized.                                                                                   |   2   | D/V  |
| 1.2.7 | Ensure that all training dataset versions are uniquely identified, stored immutably, and are auditable to support rollback and forensic analysis.       |   3   | D/V  |

---

## C1.3 Quality, Integrity, and Security of Training Data Labeling

Protect labels and require technical review for critical data.

|   #   | Description                                                                                                                                                                                    | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 1.3.1 | Verify that cryptographic hashes or digital signatures are applied to label artifacts to ensure their integrity and authenticity.                                                              |   2   | D/V  |
| 1.3.2 | Ensure that labeling interfaces and platforms enforce robust access controls, maintain tamper-evident audit logs of all labeling activities, and safeguard against unauthorized modifications. |   2   | D/V  |
| 1.3.3 | Verify that sensitive information in labels is redacted, anonymized, or encrypted at the data field level both at rest and in transit.                                                         |   3   | D/V  |

---

## C1.4 Training Data Quality and Security Assurance

Combine automated validation, manual spot checks, and logged remediation to ensure dataset reliability.

|   #   | Description                                                                                                                                                                                                                                                                                                                                                                                | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 1.4.1 | Verify that automated tests catch format errors and nulls on every ingestion or significant data transformation.                                                                                                                                                                                                                                                                           |   1   |  D   |
| 1.4.2 | Verify that LLM training and fine-tuning pipelines implement poisoning detection and data integrity validation (e.g., statistical methods, outlier detection, embedding analysis) to identify potential poisoning attacks (e.g., label flipping, backdoor trigger insertion, role-switching commands, influential instance attacks) or unintentional data corruption in the training data. |   2   | D/V  |
| 1.4.3 | Verify that suitable defenses, such as adversarial training (using generated adversarial examples), data augmentation with perturbed inputs, or robust optimization techniques, are implemented and properly tuned for relevant models based on risk assessment.                                                                                                                           |   3   | D/V  |
| 1.4.4 | Ensure that automatically generated labels (e.g., through LLMs or weak supervision) are subjected to confidence thresholds and consistency checks to identify hallucinated, misleading, or low-confidence labels.                                                                                                                                                                          |   2   | D/V  |
| 1.4.5 | Verify that automated tests detect label skews during every data ingestion or major data transformation.                                                                                                                                                                                                                                                                                   |   3   |  D   |

---

## C1.5 Data Lineage and Traceability

Track the entire journey of each data point from its source to the model input for auditability and incident response.

|   #   | Description                                                                                                                                                                                                                        | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 1.5.1 | Verify that the lineage of each data point, including all transformations, augmentations, and merges, is documented and can be reconstructed.                                                                                      |   2   | D/V  |
| 1.5.2 | Verify that lineage records are immutable, securely stored, and accessible for audits.                                                                                                                                             |   2   | D/V  |
| 1.5.3 | Ensure that lineage tracking includes synthetic data generated through privacy-preserving or generative methods, and that all synthetic data is clearly labeled and distinguishable from real data throughout the entire pipeline. |   2   | D/V  |

---

## References

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

