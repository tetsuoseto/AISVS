# C5 Access Control and Identity for AI Components and Users

## Control Objective

Effective access control for AI systems requires robust identity management, context-aware authorization, and runtime enforcement following zero-trust principles. These controls ensure that humans, services, and autonomous agents interact only with models, data, and computational resources within explicitly granted scopes, with continuous verification and audit capabilities.

---

## C5.1 Identity Management & Authentication

Establish cryptographically backed identities for all entities with multi-factor authentication for privileged operations.

|   #   | Description                                                                                                                                                                                                                    | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :--: |
| 5.1.1 | Ensure that all human users and service principals authenticate through a centralized enterprise identity provider (IdP) using OIDC/SAML protocols with unique identity-to-token mappings (no shared accounts or credentials). |   1   | D/V  |
| 5.1.2 | Verify that high-risk operations (model deployment, weight export, training data access, production configuration changes) require multi-factor authentication or step-up authentication with session revalidation.            |   1   | D/V  |
| 5.1.3 | Ensure that new principals undergo identity proofing aligned with NIST 800-63-3 IAL-2 or equivalent standards before gaining access to the production system.                                                                  |   2   |  D   |
| 5.1.4 | Verify that access reviews are conducted quarterly with automated detection of inactive accounts, enforcement of credential rotation, and de-provisioning workflows.                                                           |   2   |  V   |
| 5.1.5 | Ensure that federated AI agents authenticate using signed JWT assertions with a maximum lifespan of 24 hours, which include cryptographic proof of origin.                                                                     |   3   | D/V  |

---

## C5.2 Resource Authorization & Least Privilege

Implement fine-grained access controls for all AI resources using explicit permission models and maintain audit trails.

|   #   | Description                                                                                                                                                                                                    | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 5.2.1 | Verify that every AI resource (datasets, models, endpoints, vector collections, embedding indices, compute instances) enforces role-based access controls with explicit allow lists and default-deny policies. |   1   | D/V  |
| 5.2.2 | Ensure that least-privilege principles are enforced by default for service accounts, starting with read-only permissions and requiring documented business justification for write access.                     |   1   | D/V  |
| 5.2.3 | Verify that all access control modifications are linked to approved change requests and are immutably logged with timestamps, actor identities, resource identifiers, and permission changes.                  |   1   |  V   |
| 5.2.4 | Verify that data classification labels (PII, PHI, export-controlled, proprietary) automatically propagate to derived resources (embeddings, prompt caches, model outputs) with consistent policy enforcement.  |   2   |  D   |
| 5.2.5 | Verify that unauthorized access attempts and privilege escalation events trigger real-time alerts with contextual metadata to SIEM systems within 5 minutes.                                                   |   2   | D/V  |

---

## C5.3 Dynamic Policy Evaluation

Deploy attribute-based access control (ABAC) engines to enable context-aware authorization decisions with auditing capabilities.

|   #   | Description                                                                                                                                                                                             | Level | Role |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 5.3.1 | Verify that authorization decisions are externalized to a dedicated policy engine (such as OPA, Cedar, or an equivalent) accessible through authenticated APIs with cryptographic integrity protection. |   1   | D/V  |
| 5.3.2 | Ensure that policies evaluate dynamic attributes at runtime, including user clearance level, resource sensitivity classification, request context, tenant isolation, and temporal constraints.          |   1   | D/V  |
| 5.3.3 | Ensure that policy definitions are version-controlled, peer-reviewed, and validated through automated testing within CI/CD pipelines before deploying to production.                                    |   2   |  D   |
| 5.3.4 | Verify that policy evaluation results include structured decision rationales and are transmitted to SIEM systems for correlation analysis and compliance reporting.                                     |   2   |  V   |
| 5.3.5 | Verify that policy cache time-to-live (TTL) values do not exceed 5 minutes for high-sensitivity resources and 1 hour for standard resources with cache invalidation capabilities.                       |   3   | D/V  |

---

## C5.4 Query-Time Security Enforcement

Implement database-layer security controls using mandatory filtering and row-level security policies.

|   #   | Description                                                                                                                                                                                        | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 5.4.1 | Verify that all vector database and SQL queries include mandatory security filters (tenant ID, sensitivity labels, user scope) enforced at the database engine level, not in the application code. |   1   | D/V  |
| 5.4.2 | Verify that row-level security (RLS) policies and field-level masking are enabled with policy inheritance for all vector databases, search indices, and training datasets.                         |   1   | D/V  |
| 5.4.3 | Ensure that failed authorization checks prevent "confused deputy attacks" by immediately aborting queries and returning explicit authorization error codes instead of returning empty result sets. |   2   |  D   |
| 5.4.4 | Ensure that policy evaluation latency is continuously monitored with automated alerts for timeout conditions that could allow authorization bypass.                                                |   2   |  V   |
| 5.4.5 | Ensure that query retry mechanisms re-evaluate authorization policies to accommodate dynamic permission changes during active user sessions.                                                       |   3   | D/V  |

---

## C5.5 Output Filtering & Data Loss Prevention

Implement post-processing controls to prevent unauthorized exposure of data in AI-generated content.

|   #   | Description                                                                                                                                                                                  | Level | Role |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 5.5.1 | Ensure that post-inference filtering mechanisms scan for and redact unauthorized PII, classified information, and proprietary data before delivering content to requestors.                  |   1   | D/V  |
| 5.5.2 | Verify that citations, references, and source attributions in model outputs are validated against user entitlements and removed if unauthorized access is detected.                          |   1   | D/V  |
| 5.5.3 | Ensure that output format restrictions (such as sanitized PDFs, metadata-stripped images, and approved file types) are enforced according to user permission levels and data classification. |   2   |  D   |
| 5.5.4 | Ensure that redaction algorithms are deterministic, version-controlled, and maintain audit logs to support compliance investigations and forensic analysis.                                  |   2   |  V   |
| 5.5.5 | Verify that high-risk redaction events generate adaptive logs containing cryptographic hashes of the original content for forensic retrieval without exposing the data.                      |   3   |  V   |

---

## C5.6 Multi-Tenant Isolation

Ensure cryptographic and logical isolation between tenants in shared AI infrastructure.

|   #   | Description                                                                                                                                                                                   | Level | Role |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 5.6.1 | Verify that memory spaces, embedding stores, cache entries, and temporary files are segregated by namespace for each tenant, with secure purging upon tenant deletion or session termination. |   1   | D/V  |
| 5.6.2 | Verify that every API request includes an authenticated tenant identifier that is cryptographically validated against the session context and user entitlements.                              |   1   | D/V  |
| 5.6.3 | Ensure that network policies enforce default-deny rules for cross-tenant communication within service meshes and container orchestration platforms.                                           |   2   |  D   |
| 5.6.4 | Verify that encryption keys are unique for each tenant, support customer-managed keys (CMK), and ensure cryptographic isolation between tenant data stores.                                   |   3   |  D   |

---

## C5.7 Authorization for Autonomous Agents

Manage permissions for AI agents and autonomous systems using scoped capability tokens and continuous authorization.

|   #   | Description                                                                                                                                                                                                                 | Level | Role |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :--: |
| 5.7.1 | Ensure that autonomous agents receive scoped capability tokens that clearly specify allowed actions, accessible resources, time limits, and operational constraints.                                                        |   1   | D/V  |
| 5.7.2 | Verify that high-risk capabilities (file system access, code execution, external API calls, financial transactions) are disabled by default and require explicit authorization for activation with business justifications. |   1   | D/V  |
| 5.7.3 | Verify that capability tokens are linked to user sessions, include cryptographic integrity protection, and ensure they cannot be stored or reused in offline scenarios.                                                     |   2   |  D   |
| 5.7.4 | Verify that agent-initiated actions undergo secondary authorization via the ABAC policy engine, including full context evaluation and audit logging.                                                                        |   2   |  V   |
| 5.7.5 | Verify that agent error conditions and exception handling include capability scope information to support incident analysis and forensic investigation.                                                                     |   3   |  V   |

---

## References

### Standards & Frameworks

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Implementation Guides

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### AI-Specific Security

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

