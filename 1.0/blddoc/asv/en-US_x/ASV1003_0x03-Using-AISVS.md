# Using the AISVS

The Artificial Intelligence Security Verification Standard (AISVS) defines security requirements for modern AI applications and services, focusing on aspects that are within the control of application developers.

The AISVS is designed for anyone involved in developing or assessing the security of AI applications, including developers, architects, security engineers, and auditors. This chapter introduces the structure and usage of the AISVS, covering its verification levels and intended use cases.

## Artificial Intelligence Security Verification Levels

The AISVS defines three ascending levels of security verification. Each level adds greater depth and complexity, allowing organizations to tailor their security posture to the risk level of their AI systems.

Organizations may start at Level 1 and gradually advance to higher levels as their security maturity and threat exposure grow.

### Definition of the Levels

Each requirement in AISVS v1.0 is assigned to one of the following levels:

#### Level 1 requirements

Level 1 includes the most critical and foundational security requirements. These focus on preventing common attacks that do not rely on other preconditions or vulnerabilities. Most Level 1 controls are either straightforward to implement or essential enough to justify the effort.

#### Level 2 requirements

Level 2 addresses more advanced or less common attacks, as well as layered defenses against widespread threats. These requirements may involve more complex logic or target specific attack prerequisites.

#### Level 3 requirements

Level 3 includes controls that are generally more difficult to implement or are applicable only in specific situations. These often represent defense-in-depth mechanisms or mitigations against niche, targeted, or highly complex attacks.

### Role (D/V)

Each AISVS requirement is labeled according to the primary audience:

* D – Developer-focused requirements
* V – Verifier/Auditor-Focused Requirements
* D/V – Relevant to both developers and verifiers

