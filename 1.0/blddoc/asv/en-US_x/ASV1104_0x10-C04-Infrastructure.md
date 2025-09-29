# C4 Infrastructure, Configuration, and Deployment Security

## Control Objective

AI infrastructure must be secured against privilege escalation, supply chain tampering, and lateral movement by using secure configurations, runtime isolation, trusted deployment pipelines, and comprehensive monitoring. Only validated and authorized infrastructure components should reach production through controlled processes that guarantee security, integrity, and auditability.

Core Security Goal: Only cryptographically signed, vulnerability-scanned infrastructure components can reach production through automated validation pipelines that enforce security policies and maintain immutable audit trails.

---

## C4.1 Runtime Environment Isolation

Prevent container escapes and privilege escalation by using OS-level isolation primitives.

|   #   | Description                                                                                                                                                                                              | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 4.1.1 | Ensure that all AI workloads operate with the minimal necessary permissions on the operating system, for example, by removing unnecessary Linux capabilities in the case of a container.                 |   1   | D/V  |
| 4.1.2 | Verify that workloads are protected by technologies that limit exploitation, such as sandboxing, seccomp profiles, AppArmor, SELinux, or similar solutions, and ensure the configuration is appropriate. |   1   | D/V  |
| 4.1.3 | Ensure that workloads run with a read-only root filesystem and that any writable mounts are explicitly defined and secured with restrictive options (e.g., noexec, nosuid, nodev).                       |   2   | D/V  |
| 4.1.4 | Verify that runtime monitoring detects privilege escalation and container escape behaviors and automatically terminates offending processes.                                                             |   2   | D/V  |
| 4.1.5 | Ensure that high-risk AI workloads operate in hardware-isolated environments (e.g., TEEs, trusted hypervisors, or bare-metal nodes) only after successful remote attestation.                            |   3   | D/V  |

---

## C4.2 Secure Build and Deployment Pipelines

Ensure cryptographic integrity and supply chain security by using reproducible builds and signed artifacts.

|  #  | Description | Level | Role |
| :-: | ----------- | :---: | :--: |

| 4.2.1 | Verify that builds are reproducible and produce signed provenance metadata, as appropriate for the build artifacts, that can be independently verified. | 1 | D/V |
| 4.2.2 | Verify that builds generate a software bill of materials (SBOM) and are signed before being approved for deployment. | 2 | D/V |
| 4.2.3 | Ensure that build artifact signatures (e.g., container images) and provenance metadata are verified at deployment, and reject any artifacts that are not verified. | 2 | D/V |

---

## C4.3 Network Security and Access Control

Implement zero-trust networking using default-deny policies and encrypted communications.

|   #   | Description                                                                                                                                                                                                                        | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 4.3.1 | Verify that network policies enforce default-deny for ingress and egress, allowing only the necessary services explicitly.                                                                                                         |   1   | D/V  |
| 4.3.2 | Verify that administrative access protocols (e.g., SSH, RDP) and access to cloud metadata services are restricted and require strong authentication.                                                                               |   1   | D/V  |
| 4.3.3 | Verify that outbound traffic is restricted to approved destinations and that all requests are logged.                                                                                                                              |   2   | D/V  |
| 4.3.4 | Ensure that inter-service communication utilizes mutual TLS with certificate validation and undergoes regular automated rotation.                                                                                                  |   2   | D/V  |
| 4.3.5 | Ensure that AI workloads and environments (dev, test, prod) operate within isolated network segments (VPCs/VNets) without direct internet access and without shared IAM roles, security groups, or cross-environment connectivity. |   2   | D/V  |

## C4.4 Secrets and Cryptographic Key Management

Protect secrets and cryptographic keys with secure storage, automated rotation, and robust access controls.

|   #   | Description                                                                                                                                                                                                                         | Level | Role |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 4.4.1 | Ensure that secrets are stored in a dedicated secrets management system that uses encryption at rest and is isolated from application workloads.                                                                                    |   1   | D/V  |
| 4.4.2 | Ensure that cryptographic keys are generated and stored in hardware-backed modules (e.g., HSMs, cloud KMS).                                                                                                                         |   1   | D/V  |
| 4.4.3 | Verify that the rotation of secrets is automated.                                                                                                                                                                                   |   2   | D/V  |
| 4.4.4 | Ensure that access to production secrets requires strong authentication.                                                                                                                                                            |       |      |
| 4.4.5 | Ensure that secrets are deployed to applications at runtime using a secrets management solution. Secrets should never be embedded in source code, configuration files, build artifacts, container images, or environment variables. |   2   | D/V  |

---

## C4.5 AI Workload Sandboxing and Validation

Isolate untrusted AI models within secure sandboxes and safeguard sensitive AI workloads using trusted execution environments (TEEs) and confidential computing technologies.

|   #   | Description                                                                                                                                                               | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 4.5.1 | Verify that external or untrusted AI models run in isolated sandboxes.                                                                                                    |   1   | D/V  |
| 4.5.2 | Ensure that sandboxed workloads have no outbound network connectivity by default, with any necessary access explicitly specified.                                         |   1   | D/V  |
| 4.5.3 | Verify that workload attestation is performed before loading the model or workload, ensuring cryptographic proof of a trusted execution environment.                      |   2   | D/V  |
| 4.5.4 | Ensure that confidential workloads run within a trusted execution environment (TEE) that offers hardware-enforced isolation, memory encryption, and integrity protection. |   3   | D/V  |
| 4.5.5 | Ensure that confidential inference services prevent model extraction by using encrypted computation with sealed model weights and secure execution.                       |   3   | D/V  |
| 4.5.6 | Verify that the orchestration of trusted execution environments includes lifecycle management, remote attestation, and encrypted communication channels.                  |   3   | D/V  |
| 4.5.7 | Verify that secure multi-party computation (SMPC) enables collaborative AI training without revealing individual datasets or model parameters.                            |   3   | D/V  |

---

## C4.6 AI Infrastructure Resource Management, Backup, and Recovery

Prevent resource exhaustion attacks and ensure fair resource allocation using quotas and monitoring. Maintain infrastructure resilience with secure backups, tested recovery procedures, and disaster recovery capabilities.

|   #   | Description                                                                                                                                                                                                                                              | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 4.6.1 | Verify that the workload's resource consumption is appropriately limited using Kubernetes ResourceQuotas or similar methods to mitigate Denial of Service attacks.                                                                                       |   2   | D/V  |
| 4.6.2 | Verify that resource exhaustion triggers automated protections (e.g., rate limiting or workload isolation) once defined CPU, memory, or request thresholds are exceeded.                                                                                 |   2   | D/V  |
| 4.6.3 | Verify that backup systems operate within isolated networks using separate credentials, and ensure the storage system either functions in an air-gapped network or employs WORM (write-once-read-many) protection to prevent unauthorized modifications. |   2   | D/V  |

---

## C4.7 AI Hardware Security

Secure AI-specific hardware components, including GPUs, TPUs, and specialized AI accelerators.

|   #   | Description                                                                                                                                                      | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 4.7.1 | Verify that before workload execution, the AI accelerator's integrity is validated using hardware-based attestation mechanisms (e.g., TPM, DRTM, or equivalent). |   2   | D/V  |
| 4.7.2 | Verify that accelerator (GPU) memory is isolated between workloads using partitioning mechanisms, with memory sanitization performed between jobs.               |   2   | D/V  |
| 4.7.3 | Ensure that hardware security modules (HSMs) protect AI model weights and cryptographic keys with certification to FIPS 140-3 Level 3 or Common Criteria EAL4+.  |   3   | D/V  |

---

## C4.8 Edge and Distributed AI Security

Secure distributed AI deployments, including edge computing, federated learning, and multi-site architectures.

|   #   | Description                                                                                                                                                      | Level | Role |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 4.8.1 | Verify that edge AI devices authenticate to central infrastructure using mutual TLS.                                                                             |   2   | D/V  |
| 4.8.2 | Verify that edge devices implement secure boot using verified signatures and include rollback protection to prevent firmware downgrade attacks.                  |   2   | D/V  |
| 4.8.3 | Verify that distributed AI coordination employs Byzantine fault-tolerant consensus mechanisms incorporating participant validation and malicious node detection. |   3   | D/V  |
| 4.8.4 | Verify that edge-to-cloud communication supports bandwidth throttling, data compression, and secure offline operation with encrypted local storage.              |   3   | D/V  |

---

## References

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)

