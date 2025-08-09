# C6 Supply Chain Security for Models, Frameworks, and Data

## Control Objective

AI supply-chain attacks exploit third-party models, frameworks, or datasets to embed backdoors, biases, or exploitable code. These controls provide end-to-end provenance, vulnerability management, and monitoring to protect the entire model lifecycle.

---

## C6.1 Pretrained Model Vetting and Provenance

Assess and verify the origins, licenses, and hidden behaviors of third-party models before any fine-tuning or deployment.

|   #   | Description                                                                                                                                                          | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.1.1 | Verify that every third-party model artifact includes a signed provenance record identifying the source repository and commit hash.                                  |   1   | D/V  |
| 6.1.2 | Verify that models are scanned for malicious layers or Trojan triggers using automated tools before importing.                                                       |   1   | D/V  |
| 6.1.3 | Verify that transfer learning fine-tuning passes adversarial evaluation to detect hidden behaviors.                                                                  |   2   |  D   |
| 6.1.4 | Verify that model licenses, export-control tags, and data-origin statements are documented in an ML-BOM entry.                                                       |   2   |  V   |
| 6.1.5 | Ensure that high-risk models (those with publicly uploaded weights and unverified creators) remain quarantined until they undergo human review and receive approval. |   3   | D/V  |

---

## C6.2 Framework & Library Scanning

Continuously scan machine learning frameworks and libraries for CVEs and malicious code to maintain the security of the runtime stack.

|   #   | Description                                                                                                        | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 6.2.1 | Ensure that CI pipelines execute dependency scanners on AI frameworks and critical libraries.                      |   1   | D/V  |
| 6.2.2 | Ensure that critical vulnerabilities (CVSS ≥ 7.0) prevent promotion to production images.                          |   1   | D/V  |
| 6.2.3 | Verify that static code analysis runs on forked or vendored ML libraries.                                          |   2   |  D   |
| 6.2.4 | Verify that framework upgrade proposals include a security impact assessment referencing public CVE feeds.         |   2   |  V   |
| 6.2.5 | Ensure that runtime sensors trigger alerts for unexpected dynamic library loads that deviate from the signed SBOM. |   3   |  V   |

---

## C6.3 Dependency Pinning & Verification

Pin every dependency to immutable digests and reproduce builds to guarantee identical, tamper-free artifacts.

|   #   | Description                                                                                         | Level | Role |
| :---: | --------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.3.1 | Verify that all package managers enforce version pinning through lockfiles.                         |   1   | D/V  |
| 6.3.2 | Ensure that immutable digests are used instead of mutable tags in container references.             |   1   | D/V  |
| 6.3.3 | Verify that reproducible-build checks compare hashes across CI runs to ensure identical outputs.    |   2   |  D   |
| 6.3.4 | Verify that build attestations are retained for 18 months to ensure audit traceability.             |   2   |  V   |
| 6.3.5 | Ensure that expired dependencies trigger automated pull requests to update or fork pinned versions. |   3   |  D   |

---

## C6.4 Trusted Source Enforcement

Allow artifact downloads only from cryptographically verified, organization-approved sources, and block everything else.

|   #   | Description                                                                                                                  | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.4.1 | Verify that model weights, datasets, and containers are downloaded exclusively from approved domains or internal registries. |   1   | D/V  |
| 6.4.2 | Ensure that Sigstore/Cosign signatures validate the publisher's identity before artifacts are cached locally.                |   1   | D/V  |
| 6.4.3 | Verify that egress proxies block unauthenticated artifact downloads to enforce the trusted-source policy.                    |   2   |  D   |
| 6.4.4 | Verify that repository allow-lists are reviewed quarterly with documented business justification for each entry.             |   2   |  V   |
| 6.4.5 | Verify that policy violations trigger quarantining of artifacts and rollback of dependent pipeline runs.                     |   3   |  V   |

---

## C6.5 Third-Party Dataset Risk Assessment

Evaluate external datasets for poisoning, bias, and legal compliance, and continuously monitor them throughout their lifecycle.

|   #   | Description                                                                                                                      | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.5.1 | Ensure that external datasets are subjected to poisoning risk assessment methods (e.g., data fingerprinting, outlier detection). |   1   | D/V  |
| 6.5.2 | Ensure that bias metrics (demographic parity, equal opportunity) are calculated before approving the dataset.                    |   1   |  D   |
| 6.5.3 | Verify that the provenance and licensing terms for datasets are recorded in ML-BOM entries.                                      |   2   |  V   |
| 6.5.4 | Ensure that periodic monitoring identifies drift or corruption in hosted datasets.                                               |   2   |  V   |
| 6.5.5 | Ensure that disallowed content (copyright, PII) is removed through automated scrubbing before training.                          |   3   |  D   |

---

## C6.6 Supply Chain Attack Monitoring

Detect supply-chain threats early using CVE feeds, audit log analytics, and red team simulations.

|   #   | Description                                                                                                                     | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.6.1 | Ensure that CI/CD audit logs are streamed to the SIEM for detecting anomalous package pulls or tampered build steps.            |   1   |  V   |
| 6.6.2 | Verify that incident response playbooks include rollback procedures for compromised models or libraries.                        |   2   |  D   |
| 6.6.3 | Verify that threat-intel enrichment tags machine learning-specific indicators (e.g., model-poisoning IoCs) during alert triage. |   3   |  V   |

---

## C6.7 ML-BOM for Model Artifacts

Generate and sign detailed ML-specific SBOMs (ML-BOMs) so that downstream consumers can verify component integrity at deployment time.

|   #   | Description                                                                                                                    | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 6.7.1 | Verify that each model artifact publishes an ML-BOM listing datasets, weights, hyperparameters, and licenses.                  |   1   | D/V  |
| 6.7.2 | Verify that ML‑BOM generation and Cosign signing are automated in the CI process and are required for merging.                 |   1   | D/V  |
| 6.7.3 | Verify that ML-BOM completeness checks cause the build to fail if any component metadata (such as hash or license) is missing. |   2   |  D   |
| 6.7.4 | Verify that downstream consumers can query ML-BOMs through the API to validate imported models at deployment time.             |   2   |  V   |
| 6.7.5 | Ensure that ML-BOMs are version-controlled and compared using diffs to detect unauthorized changes.                            |   3   |  V   |

---

## References

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

