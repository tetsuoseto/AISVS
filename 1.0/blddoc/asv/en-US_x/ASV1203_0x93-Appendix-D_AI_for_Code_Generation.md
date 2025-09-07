# Appendix D: AI-Assisted Secure Coding Governance and Verification

## Objective

This chapter establishes baseline organizational controls for the safe and effective use of AI-assisted coding tools during software development, ensuring security and traceability throughout the SDLC.

---

## AD.1 AI-Assisted Secure-Coding Workflow

Integrate AI tools into the organization's secure software development lifecycle (SSDLC) without compromising existing security controls.

|   #    | Description                                                                                                                                     | Level | Role |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.1.1 | Ensure that a documented workflow specifies when and how AI tools can generate, refactor, or review code.                                       |   1   | D/V  |
| AD.1.2 | Verify that the workflow corresponds to each SSDLC phase (design, implementation, code review, testing, deployment).                            |   2   |  D   |
| AD.1.3 | Verify that metrics (e.g., vulnerability density, mean time to detect) are collected on AI-generated code and compared to human-only baselines. |   3   | D/V  |

---

## AD.2 AI Tool Qualification & Threat Modeling

Ensure AI coding tools are evaluated for security capabilities, risks, and supply-chain impact before adoption.

|   #    | Description                                                                                                                                                                                 | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.2.1 | Ensure that the threat model for each AI tool identifies risks related to misuse, model inversion, data leakage, and dependency-chain vulnerabilities.                                      |   1   | D/V  |
| AD.2.2 | Verify that tool evaluations include static and dynamic analysis of any local components as well as assessment of SaaS endpoints, including TLS, authentication/authorization, and logging. |   2   |  D   |
| AD.2.3 | Verify that evaluations adhere to a recognized framework and are re-performed after major version changes.                                                                                  |   3   | D/V  |

---

## AD.3 Secure Prompt & Context Management

Prevent the leakage of secrets, proprietary code, and personal data when creating prompts or contexts for AI models.

|   #    | Description                                                                                                                                                    | Level | Role |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.3.1 | Ensure that written guidelines explicitly prohibit including secrets, credentials, or classified information in prompts.                                       |   1   | D/V  |
| AD.3.2 | Verify that technical controls (client-side redaction, approved context filters) automatically remove sensitive artifacts.                                     |   2   |  D   |
| AD.3.3 | Verify that prompts and responses are tokenized, encrypted both in transit and at rest, and that retention periods comply with the data classification policy. |   3   | D/V  |

---

## AD.4 Validation of AI-Generated Code

Identify and fix vulnerabilities introduced by AI-generated output before the code is merged or deployed.

|   #    | Description                                                                                                                                              | Level | Role |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.4.1 | Ensure that AI-generated code always undergoes human code review.                                                                                        |   1   | D/V  |
| AD.4.2 | Ensure that automated scanners (SAST/IAST/DAST) run on every pull request containing AI-generated code and block merges if critical issues are detected. |   2   |  D   |
| AD.4.3 | Verify that differential fuzz testing or property-based tests demonstrate security-critical behaviors (e.g., input validation, authorization logic).     |   3   | D/V  |

---

## AD.5 Explainability and Traceability of Code Suggestions

Provide auditors and developers with insight into why a suggestion was made and how it developed.

|   #    | Description                                                                                                                                                   | Level | Role |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.5.1 | Verify that prompt/response pairs are logged with commit IDs.                                                                                                 |   1   | D/V  |
| AD.5.2 | Verify that developers can display model citations (training snippets, documentation) supporting a suggestion.                                                |   2   |  D   |
| AD.5.3 | Ensure that explainability reports are stored alongside design artifacts and referenced in security reviews, meeting ISO/IEC 42001 traceability requirements. |   3   | D/V  |

---

## AD.6 Continuous Feedback and Model Fine-Tuning

Enhance model security performance over time while preventing negative drift.

|   #    | Description                                                                                                                                                            | Level | Role |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| AD.6.1 | Verify that developers can mark insecure or non-compliant suggestions and that these flags are recorded.                                                               |   1   | D/V  |
| AD.6.2 | Ensure that aggregated feedback guides periodic fine-tuning or retrieval-augmented generation using vetted secure-coding corpora (e.g., OWASP Cheat Sheets).           |   2   |  D   |
| AD.6.3 | Verify that a closed-loop evaluation harness runs regression tests after every fine-tuning; security metrics must meet or exceed previous baselines before deployment. |   3   | D/V  |

---

### References

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

