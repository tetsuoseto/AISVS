# C6 Supply Chain Security for Models, Frameworks & Data

## Control Objective

AI supply‑chain attacks exploit third‑party models, frameworks, or datasets to embed backdoors, bias, or exploitable code. These controls provide end‑to‑end provenance, vulnerability management, and monitoring to protect the entire model lifecycle.

---

## C6.1 Pretrained Model Vetting & Provenance

Assess and authenticate third‑party model origins, licenses, and hidden behaviors before any fine‑tuning or deployment.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **6.1.1** | **Verify that** every third‑party model artifact includes a signed provenance record identifying source repository and commit hash. | 1 | D/V |
| **6.1.2** | **Verify that** models are scanned for malicious layers or Trojan triggers using automated tools before import. | 1 | D/V |
| **6.1.3** | **Verify that** transfer‑learning fine‑tunes pass adversarial evaluation to detect hidden behaviors. | 2 | D |
| **6.1.4** | **Verify that** model licenses, export‑control tags, and data‑origin statements are recorded in a ML‑BOM entry. | 2 | V |
| **6.1.5** | **Verify that** high‑risk models (publicly uploaded weights, unverified creators) remain quarantined until human review and sign‑off. | 3 | D/V |

---

## C6.2 Framework & Library Scanning

Continuously scan ML frameworks and libraries for CVEs and malicious code to keep the runtime stack secure.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **6.2.1** | **Verify that** CI pipelines run dependency scanners on AI frameworks and critical libraries. | 1 | D/V |
| **6.2.2** | **Verify that** critical vulnerabilities (CVSS ≥ 7.0) block promotion to production images. | 1 | D/V |
| **6.2.3** | **Verify that** static code analysis runs on forked or vendored ML libraries. | 2 | D |
| **6.2.4** | **Verify that** framework upgrade proposals include a security impact assessment referencing public CVE feeds. | 2 | V |
| **6.2.5** | **Verify that** runtime sensors alert on unexpected dynamic library loads that deviate from the signed SBOM. | 3 | V |

---

## C6.3 Dependency Pinning & Verification

Pin every dependency to immutable digests and reproduce builds to guarantee identical, tamper‑free artifacts.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **6.3.1** | **Verify that** all package managers enforce version pinning via lockfiles. | 1 | D/V |
| **6.3.2** | **Verify that** immutable digests are used instead of mutable tags in container references. | 1 | D/V |
| **6.3.3** | **Verify that** reproducible‑build checks compare hashes across CI runs to ensure identical outputs. | 2 | D |
| **6.3.4** | **Verify that** build attestations are stored for 18 months for audit traceability. | 2 | V |
| **6.3.5** | **Verify that** expired dependencies trigger automated PRs to update or fork pinned versions. | 3 | D |

---

## C6.4 Trusted Source Enforcement

Allow artifact downloads only from cryptographically verified, organization‑approved sources and block everything else.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **6.4.1** | **Verify that** model weights, datasets, and containers are downloaded only from approved domains or internal registries. | 1 | D/V |
| **6.4.2** | **Verify that** Sigstore/Cosign signatures validate publisher identity before artifacts are cached locally. | 1 | D/V |
| **6.4.3** | **Verify that** egress proxies block unauthenticated artifact downloads to enforce trusted‑source policy. | 2 | D |
| **6.4.4** | **Verify that** repository allow‑lists are reviewed quarterly with evidence of business justification for each entry. | 2 | V |
| **6.4.5** | **Verify that** policy violations trigger quarantining of artifacts and rollback of dependent pipeline runs. | 3 | V |

---

## C6.5 Third‑Party Dataset Risk Assessment

Evaluate external datasets for poisoning, bias, and legal compliance, and monitor them throughout their lifecycle.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **6.5.1** | **Verify that** external datasets undergo poisoning risk scoring (e.g., data fingerprinting, outlier detection). | 1 | D/V |
| **6.5.2** | **Verify that** bias metrics (demographic parity, equal opportunity) are calculated before dataset approval. | 1 | D |
| **6.5.3** | **Verify that** provenance and license terms for datasets are captured in ML‑BOM entries. | 2 | V |
| **6.5.4** | **Verify that** periodic monitoring detects drift or corruption in hosted datasets. | 2 | V |
| **6.5.5** | **Verify that** disallowed content (copyright, PII) is removed via automated scrubbing prior to training. | 3 | D |

---

## C6.6 Supply Chain Attack Monitoring

Detect supply‑chain threats early through CVE feeds, audit‑log analytics, and red‑team simulations.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **6.6.1** | **Verify that** CI/CD audit logs stream to SIEM detections for anomalous package pulls or tampered build steps. | 1 | V |
| **6.6.2** | **Verify that** incident response playbooks include rollback procedures for compromised models or libraries. | 2 | D ||
| **6.6.3** | **Verify that** threat‑intel enrichment tags ML‑specific indicators (e.g., model‑poisoning IoCs) in alert triage. | 3 | V |

---

## C6.7 ML‑BOM for Model Artifacts

Generate and sign detailed ML‑specific SBOMs (ML‑BOMs) so downstream consumers can verify component integrity at deploy time.

| # | Description | Level | Role |
|:--------:|---------------------------------------------------------------------------------------------------------------------|:---:|:---:|
| **6.7.1** | **Verify that** every model artifact publishes a ML‑BOM that lists datasets, weights, hyperparameters, and licenses. | 1 | D/V |
| **6.7.2** | **Verify that** ML‑BOM generation and Cosign signing are automated in CI and required for merge. | 1 | D/V |
| **6.7.3** | **Verify that** ML‑BOM completeness checks fail the build if any component metadata (hash, license) is missing. | 2 | D |
| **6.7.4** | **Verify that** downstream consumers can query ML-BOMs via API to validate imported models at deploy time. | 2 | V |
| **6.7.5** | **Verify that** ML‑BOMs are version‑controlled and diffed to detect unauthorized modifications. | 3 | V |

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
