# C13 Human Oversight, Accountability, and Governance

## Control Objective

This chapter outlines requirements for maintaining human oversight and clear accountability chains in AI systems, ensuring explainability, transparency, and ethical stewardship throughout the AI lifecycle.

---

## C13.1 Kill Switch & Override Mechanisms

Provide shutdown or rollback options when unsafe behavior of the AI system is observed.

|   #    | Description                                                                                                | Level | Role |
| :----: | ---------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 13.1.1 | Verify that a manual kill-switch mechanism is in place to immediately stop AI model inference and outputs. |   1   | D/V  |
| 13.1.2 | Verify that override controls are accessible only to authorized personnel.                                 |   1   |  D   |
| 13.1.3 | Verify that rollback procedures can restore previous model versions or safe-mode operations.               |   3   | D/V  |
| 13.1.4 | Ensure that override mechanisms are tested regularly.                                                      |   3   |  V   |

---

## C13.2 Human-in-the-Loop Decision Checkpoints

Require human approval when stakes exceed predefined risk thresholds.

|   #    | Description                                                                                                                                                  | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 13.2.1 | Ensure that high-risk AI decisions receive explicit human approval prior to execution.                                                                       |   1   | D/V  |
| 13.2.2 | Ensure that risk thresholds are clearly defined and automatically initiate human review workflows.                                                           |   1   |  D   |
| 13.2.3 | Verify that time-sensitive decisions have fallback procedures in place for situations when human approval cannot be obtained within the required timeframes. |   2   |  D   |
| 13.2.4 | Verify that escalation procedures clearly define authority levels for different decision types or risk categories, if applicable.                            |   3   | D/V  |

---

## C13.3 Chain of Responsibility & Auditability

Record operator actions and model decisions.

|   #    | Description                                                                                                                                     | Level | Role |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 13.3.1 | Ensure that all AI system decisions and human interventions are recorded with timestamps, user identities, and the rationale for each decision. |   1   | D/V  |
| 13.3.2 | Ensure that audit logs are tamper-proof and include mechanisms for verifying their integrity.                                                   |   2   |  D   |

---

## C13.4 Explainable AI Techniques

Surface feature importance, counterfactuals, and local explanations.

|   #    | Description                                                                                                                                   | Level | Role |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 13.4.1 | Verify that AI systems provide basic explanations for their decisions in a human-readable format.                                             |   1   | D/V  |
| 13.4.2 | Verify that the quality of explanations is validated through human evaluation studies and metrics.                                            |   2   |  V   |
| 13.4.3 | Verify that feature importance scores or attribution methods (SHAP, LIME, etc.) are available for critical decisions.                         |   3   | D/V  |
| 13.4.4 | Verify that counterfactual explanations demonstrate how inputs could be altered to change outcomes, if applicable to the use case and domain. |   3   |  V   |

---

## C13.5 Model Cards and Usage Disclosures

Maintain model cards detailing intended use, performance metrics, and ethical considerations.

|   #    | Description                                                                                                                                                                          | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 13.5.1 | Ensure that model cards document the intended use cases, limitations, and known failure modes.                                                                                       |   1   |  D   |
| 13.5.2 | Verify that performance metrics for various relevant use cases are disclosed.                                                                                                        |   1   | D/V  |
| 13.5.3 | Verify that ethical considerations, bias assessments, fairness evaluations, training data characteristics, and known training data limitations are documented and updated regularly. |   2   |  D   |
| 13.5.4 | Ensure that model cards are version-controlled and maintained throughout the model lifecycle with change tracking.                                                                   |   2   | D/V  |

---

## C13.6 Uncertainty Quantification

Propagate confidence scores or entropy measures within responses.

|   #    | Description                                                                                          | Level | Role |
| :----: | ---------------------------------------------------------------------------------------------------- | :---: | :--: |
| 13.6.1 | Verify that AI systems provide confidence scores or uncertainty measures with their outputs.         |   1   |  D   |
| 13.6.2 | Verify that uncertainty thresholds prompt additional human review or alternative decision pathways.  |   2   | D/V  |
| 13.6.3 | Verify that uncertainty quantification methods are calibrated and validated using ground truth data. |   2   |  V   |
| 13.6.4 | Verify that uncertainty propagation is preserved throughout multi-step AI workflows.                 |   3   | D/V  |

---

## C13.7 User-Facing Transparency Reports

Provide periodic disclosures about incidents, drift, and data usage.

|   #    | Description                                                                                                              | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 13.7.1 | Ensure that data usage policies and user consent management practices are clearly communicated to stakeholders.          |   1   | D/V  |
| 13.7.2 | Ensure that AI impact assessments are conducted and that the results are included in the reporting.                      |   2   | D/V  |
| 13.7.3 | Ensure that regularly published transparency reports disclose AI incidents and operational metrics in sufficient detail. |   2   | D/V  |

### References

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

