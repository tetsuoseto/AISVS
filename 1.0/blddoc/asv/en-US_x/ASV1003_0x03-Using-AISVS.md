# Using AISVS.

The Artificial Intelligence Security Verification Standard (AISVS) defines security requirements for modern AI applications and services, focusing on aspects that are within the control of application developers.

The AISVS is intended for anyone developing or evaluating the security of AI applications, including developers, architects, security engineers, and auditors. This chapter explains the structure and use of the AISVS, including its verification levels and intended use cases.

## Artificial Intelligence Security Verification Levels

The AISVS defines three progressively higher levels of security verification.

Organizations may start at Level 1 and progressively adopt higher levels as their security maturity and threat exposure increase.

### Definitions of the Levels

Each requirement in AISVS v1.0 is assigned to one of the following levels:

#### Level 1 requirements

Level 1 includes the most critical and foundational security requirements. These focus on preventing common attacks that do not rely on other preconditions or vulnerabilities. Most Level 1 controls are straightforward to implement or are essential enough to justify the effort.

#### Level 2 requirements

Level 2 addresses more advanced or less common attacks, as well as layered defenses against widespread threats. These requirements may involve more complex logic or target specific prerequisites for attacks.

#### Level 3 requirements.

Level 3 includes controls that are typically harder to implement or have situational applicability. These controls often represent defense-in-depth mechanisms or mitigations against niche, targeted, or highly complex attacks.

### Role (D/V)

Each AISVS requirement is marked according to its primary audience:

* D – Developer-Focused Requirements
* V – Verifier/auditor-focused requirements
* D/V – Relevant to both developers and verifiers

