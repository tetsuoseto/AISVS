# C6 Supply Chain Security for Models, Frameworks, and Data

## Control Objective

AI supply-chain attacks exploit third-party models, frameworks, or datasets to embed backdoors, biases, or exploitable code. These controls provide end-to-end provenance, vulnerability management, and monitoring to protect the entire model lifecycle.

---

## C6.1 Pretrained Model Vetting and Provenance

Evaluate and verify the origins, licenses, and hidden behaviors of third-party models before any fine-tuning or deployment.

|   #   | Description                                                                                                                                                                 | Level | Role |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.1.1 | Verify that each third-party model artifact includes a signed provenance record identifying the source repository and commit hash.                                          |   1   | D/V  |
| 6.1.2 | Ensure that models are scanned for malicious layers or Trojan triggers using automated tools prior to import.                                                               |   1   | D/V  |
| 6.1.3 | Verify that transfer learning fine-tunes pass adversarial evaluation to detect hidden behaviors.                                                                            |   2   |  D   |
| 6.1.4 | Verify that model licenses, export-control tags, and data-origin statements are recorded in an ML-BOM entry.                                                                |   2   |  V   |
| 6.1.5 | Ensure that high-risk models (those with publicly uploaded weights or created by unverified sources) stay quarantined until they undergo human review and receive approval. |   3   | D/V  |

---

## C6.2 Framework & Library Scanning

Continuously monitor ML frameworks and libraries for CVEs and malicious code to maintain runtime stack security.

|   #   | Description                                                                                                                           | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.2.1 | Verify that CI pipelines execute dependency scanners on AI frameworks and critical libraries.                                         |   1   | D/V  |
| 6.2.2 | Verify that critical vulnerabilities (CVSS ≥ 7.0) prevent promotion to production images.                                             |   1   | D/V  |
| 6.2.3 | Ensure that static code analysis is performed on forked or vendored machine learning libraries.                                       |   2   |  D   |
| 6.2.4 | Ensure that framework upgrade proposals include a security impact assessment referencing public CVE feeds.                            |   2   |  V   |
| 6.2.5 | Verify that runtime sensors alert on unexpected dynamic library loads that deviate from the signed Software Bill of Materials (SBOM). |   3   |  V   |

---

## C6.3 Dependency Pinning & Verification

Pin every dependency to immutable digests and reproduce builds to guarantee identical, tamper-free artifacts.

|   #   | Description                                                                                         | Level | Role |
| :---: | --------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.3.1 | Verify that all package managers enforce version pinning through lockfiles.                         |   1   | D/V  |
| 6.3.2 | Ensure that immutable digests are used rather than mutable tags in container references.            |   1   | D/V  |
| 6.3.3 | Verify that reproducible-build checks compare hashes across CI runs to ensure identical outputs.    |   2   |  D   |
| 6.3.4 | Confirm that build attestations are retained for 18 months to ensure audit traceability.            |   2   |  V   |
| 6.3.5 | Verify that expired dependencies trigger automated pull requests to update or fork pinned versions. |   3   |  D   |

---

## C6.4 Trusted Source Enforcement

Allow artifact downloads only from cryptographically verified, organization-approved sources, and block all other sources.

|   #   | Description                                                                                                                  | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.4.1 | Ensure that model weights, datasets, and containers are downloaded exclusively from approved domains or internal registries. |   1   | D/V  |
| 6.4.2 | Confirm that Sigstore/Cosign signatures authenticate the publisher's identity before caching artifacts locally.              |   1   | D/V  |
| 6.4.3 | Verify that egress proxies block unauthenticated artifact downloads to enforce the trusted-source policy.                    |   2   |  D   |
| 6.4.4 | Verify that repository allow-lists are reviewed quarterly, with evidence of a business justification for each entry.         |   2   |  V   |
| 6.4.5 | Ensure that policy violations trigger the quarantining of artifacts and the rollback of dependent pipeline runs.             |   3   |  V   |

---

## C6.5 Third-Party Dataset Risk Assessment

Evaluate external datasets for poisoning, bias, and legal compliance, and continuously monitor them throughout their lifecycle.

|   #   | Description                                                                                                                                                           | Level | Role |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.5.1 | Verify that external datasets undergo poisoning risk assessment (e.g., data fingerprinting, outlier detection).                                                       |   1   | D/V  |
| 6.5.2 | Ensure that bias metrics (demographic parity, equal opportunity) are calculated prior to dataset approval.                                                            |   1   |  D   |
| 6.5.3 | Verify that the provenance and license terms for datasets are recorded in ML-BOM entries.                                                                             |   2   |  V   |
| 6.5.4 | Verify that periodic monitoring detects drift or corruption in hosted datasets.                                                                                       |   2   |  V   |
| 6.5.5 | Ensure that disallowed content (such as copyright-protected material and personally identifiable information) is removed through automated scrubbing before training. |   3   |  D   |

---

## C6.6 Supply Chain Attack Monitoring

Detect supply-chain threats early through CVE feeds, audit log analytics, and red team simulations.

|   #   | Description                                                                                                                     | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.6.1 | Verify that CI/CD audit logs are streamed to the SIEM for detection of anomalous package pulls or tampered build steps.         |   1   |  V   |
| 6.6.2 | Verify that incident response playbooks include rollback procedures for compromised models or libraries.                        |   2   |  D   |
| 6.6.3 | Verify that threat-intel enrichment tags machine learning–specific indicators (e.g., model-poisoning IoCs) during alert triage. |   3   |  V   |

---

## C6.7 ML-BOM for Model Artifacts

Generate and sign detailed machine learning-specific SBOMs (ML-BOMs) so downstream users can verify component integrity during deployment.

|   #   | Description                                                                                                          | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 6.7.1 | Verify that every model artifact publishes an ML-BOM listing datasets, weights, hyperparameters, and licenses.       |   1   | D/V  |
| 6.7.2 | Verify that ML-BOM generation and Cosign signing are automated in CI and required for merging.                       |   1   | D/V  |
| 6.7.3 | Verify that ML-BOM completeness checks cause the build to fail if any component metadata (hash, license) is missing. |   2   |  D   |
| 6.7.4 | Verify that downstream consumers can query ML-BOMs through the API to validate imported models during deployment.    |   2   |  V   |
| 6.7.5 | Ensure that ML-BOMs are version-controlled and compared using diffs to identify unauthorized changes.                |   3   |  V   |

---

## References

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

