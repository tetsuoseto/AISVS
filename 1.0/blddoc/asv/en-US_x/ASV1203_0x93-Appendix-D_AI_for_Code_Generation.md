# Appendix D: AI-Assisted Secure Coding Governance and Verification

## Objective

This chapter defines baseline organizational controls for the safe and effective use of AI-assisted coding tools during software development, ensuring security and traceability throughout the SDLC.

---

## AD.1 AI-Assisted Secure-Coding Workflow

Integrate AI tools into the organization’s secure software development lifecycle (SSDLC) without compromising existing security controls.

|   #    | Description                                                                                                                                    | Level | Role |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.1.1 | Ensure that the documented workflow specifies when and how AI tools can generate, refactor, or review code.                                    |   1   | D/V  |
| AD.1.2 | Verify that the workflow corresponds to each SSDLC phase (design, implementation, code review, testing, deployment).                           |   2   |  D   |
| AD.1.3 | Verify that metrics (e.g., vulnerability density, mean time to detect) are collected on AI-produced code and compared to human-only baselines. |   3   | D/V  |

---

## AD.2 AI Tool Qualification & Threat Modeling

Ensure AI coding tools are evaluated for security capabilities, risks, and supply-chain impact before adoption.

|   #    | Description                                                                                                                                                                     | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.2.1 | Ensure that a threat model for each AI tool identifies risks related to misuse, model inversion, data leakage, and dependency chains.                                           |   1   | D/V  |
| AD.2.2 | Ensure that tool evaluations include static and dynamic analysis of any local components, as well as assessment of SaaS endpoints (TLS, authentication/authorization, logging). |   2   |  D   |
| AD.2.3 | Verify that evaluations follow a recognized framework and are conducted again after major version changes.                                                                      |   3   | D/V  |

---

## AD.3 Secure Prompt and Context Management

Prevent leakage of secrets, proprietary code, and personal data when creating prompts or contexts for AI models.

|   #    | Description                                                                                                                                                              | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| AD.3.1 | Ensure that written guidelines explicitly prohibit sending secrets, credentials, or classified information in prompts.                                                   |   1   | D/V  |
| AD.3.2 | Verify that technical controls (client-side redaction, approved context filters) automatically remove sensitive artifacts.                                               |   2   |  D   |
| AD.3.3 | Verify that prompts and responses are tokenized and encrypted both in transit and at rest, and ensure that retention periods comply with the data classification policy. |   3   | D/V  |

---

## AD.4 Validation of AI-Generated Code

Identify and fix vulnerabilities introduced by AI-generated code before merging or deployment.

|   #    | Description                                                                                                                                             | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.4.1 | Ensure that AI-generated code is always subject to human code review.                                                                                   |   1   | D/V  |
| AD.4.2 | Ensure that automated scanners (SAST/IAST/DAST) run on every pull request containing AI-generated code and block merges when critical issues are found. |   2   |  D   |
| AD.4.3 | Verify that differential fuzz testing or property-based tests confirm security-critical behaviors (e.g., input validation, authorization logic).        |   3   | D/V  |

---

## AD.5 Explainability & Traceability of Code Suggestions

Give auditors and developers an understanding of why a suggestion was made and how it developed.

|   #    | Description                                                                                                                                            | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| AD.5.1 | Verify that prompt/response pairs are logged with commit IDs.                                                                                          |   1   | D/V  |
| AD.5.2 | Verify that developers can display model citations (training excerpts, documentation) supporting a suggestion.                                         |   2   |  D   |
| AD.5.3 | Verify that explainability reports are stored with design artifacts and referenced in security reviews, meeting ISO/IEC 42001 traceability principles. |   3   | D/V  |

---

## AD.6 Continuous Feedback & Model Fine-Tuning

Enhance model security performance over time while avoiding negative drift.

|   #    | Description                                                                                                                                                         | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.6.1 | Verify that developers can flag insecure or non-compliant suggestions and that these flags are tracked.                                                             |   1   | D/V  |
| AD.6.2 | Verify that aggregated feedback informs periodic fine-tuning or retrieval-augmented generation using vetted secure-coding corpora (e.g., OWASP Cheat Sheets).       |   2   |  D   |
| AD.6.3 | Verify that a closed-loop evaluation harness runs regression tests after each fine-tune; security metrics must meet or exceed previous baselines before deployment. |   3   | D/V  |

---

### References

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

