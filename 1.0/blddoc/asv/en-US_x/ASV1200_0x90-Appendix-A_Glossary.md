# Appendix A: Glossary

This comprehensive glossary provides definitions of key AI, ML, and security terms used throughout the AISVS to ensure clarity and a common understanding.

* Adversarial Example: An input intentionally designed to cause an AI model to make an error, often by adding subtle perturbations that are imperceptible to humans.
  ​
* Adversarial Robustness – In AI, adversarial robustness refers to a model's ability to maintain its performance and resist being deceived or manipulated by intentionally crafted malicious inputs designed to cause errors.
  ​
* Agent – AI agents are software systems that use AI to pursue goals and complete tasks on behalf of users. They demonstrate reasoning, planning, and memory and possess a level of autonomy to make decisions, learn, and adapt.
  ​
* Agentic AI: AI systems capable of operating with a certain level of autonomy to achieve goals, often making decisions and taking actions without direct human intervention.
  ​
* Attribute-Based Access Control (ABAC): An access control model in which authorization decisions are made based on attributes of the user, resource, action, and environment, evaluated at the time of the request.
  ​
* Backdoor Attack: A type of data poisoning attack in which the model is trained to respond in a specific way to certain triggers while behaving normally in other situations.
  ​
* Bias: Systematic errors in AI model outputs that can result in unfair or discriminatory outcomes for certain groups or specific contexts.
  ​
* Bias Exploitation: An attack technique that leverages known biases in AI models to manipulate outputs or results.
  ​
* Cedar: Amazon's policy language and engine for fine-grained permissions used in implementing Attribute-Based Access Control (ABAC) for AI systems.
  ​
* Chain of Thought: A technique for enhancing reasoning in language models by generating intermediate reasoning steps before producing the final answer.
  ​
* Circuit Breakers: Mechanisms that automatically stop AI system operations when specific risk thresholds are exceeded.
  ​
* Confidential Inference Service: An inference service that operates AI models within a trusted execution environment (TEE) or an equivalent confidential computing mechanism, ensuring that model weights and inference data remain encrypted, sealed, and protected from unauthorized access or tampering.
  ​
* Confidential Workload: An AI workload (such as training, inference, or preprocessing) executed inside a trusted execution environment (TEE) with hardware-enforced isolation, memory encryption, and remote attestation to protect code, data, and models from access by the host or co-tenants.
  ​
* Data Leakage: The unintended exposure of sensitive information through AI model outputs or behavior.
  ​
* Data Poisoning: The intentional corruption of training data to compromise model integrity, often to introduce backdoors or degrade performance.
  ​
* Differential Privacy – Differential privacy is a mathematically rigorous framework for releasing statistical information about datasets while protecting the privacy of individual data subjects. It allows a data holder to share aggregate patterns of the group while limiting the information leaked about specific individuals.
  ​
* Embeddings: Dense vector representations of data (such as text, images, etc.) that capture semantic meaning within a high-dimensional space.
  ​
* Explainability – Explainability in AI refers to an AI system's ability to provide human-understandable explanations for its decisions and predictions, offering insights into how it operates internally.
  ​
* Explainable AI (XAI): AI systems designed to offer human-understandable explanations for their decisions and behaviors using various techniques and frameworks.
  ​
* Federated Learning: A machine learning approach in which models are trained across multiple decentralized devices holding local data samples, without exchanging the data itself.
  ​
* Formulation: The recipe or method used to create an artifact or dataset, such as hyperparameters, training configuration, preprocessing steps, or build scripts.
  ​
* Guardrails: Constraints implemented to prevent AI systems from generating harmful, biased, or otherwise undesirable outputs.
  ​
* Hallucination – An AI hallucination refers to a phenomenon where an AI model generates incorrect or misleading information that is not based on its training data or factual reality.
  ​
* Human-in-the-Loop (HITL): Systems designed to require human oversight, verification, or intervention at critical decision points.
  ​
* Infrastructure as Code (IaC): Managing and provisioning infrastructure through code rather than manual processes, enabling security scanning and ensuring consistent deployments.
  ​
* Jailbreak: Techniques used to bypass safety guardrails in AI systems, especially in large language models, to generate prohibited content.
  ​
* Least Privilege: The security principle of granting users and processes only the minimum necessary access rights.
  ​
* LIME (Local Interpretable Model-agnostic Explanations): A technique for explaining the predictions of any machine learning classifier by locally approximating it with an interpretable model.
  ​
* Membership Inference Attack: An attack that aims to determine whether a specific data point was used to train a machine learning model.
  ​
* MITRE ATLAS: Adversarial Threat Landscape for Artificial Intelligence Systems; a knowledge base of adversarial tactics and techniques targeting AI systems.
  ​
* Model Card – A model card is a document that provides standardized information about an AI model’s performance, limitations, intended uses, and ethical considerations to promote transparency and responsible AI development.
  ​
* Model Extraction: An attack in which an adversary repeatedly queries a target model to create an unauthorized functionally similar copy.
  ​
* Model Inversion: An attack that tries to reconstruct training data by analyzing the outputs of a model.
  ​
* Model Lifecycle Management – AI Model Lifecycle Management is the process of overseeing all stages of an AI model’s existence, including its design, development, deployment, monitoring, maintenance, and eventual retirement, to ensure it remains effective and aligned with objectives.
  ​
* Model Poisoning: Introducing vulnerabilities or backdoors directly into a model during the training process.
  ​
* Model Stealing/Theft: Obtaining a copy or approximation of a proprietary model through repeated queries.
  ​
* Multi-agent System: A system comprised of multiple interacting AI agents, each potentially having different capabilities and goals.
  ​
* OPA (Open Policy Agent): An open-source policy engine that enables unified policy enforcement across the entire stack.
  ​
* Provenance: The pedigree and chain of custody of an artifact or dataset, including its origin, handlers, transfer path, and evidence of integrity (e.g., checksums, signatures).
  ​
* Privacy-Preserving Machine Learning (PPML): Techniques and methods for training and deploying ML models while safeguarding the privacy of the training data.
  ​
* Prompt Injection: An attack in which malicious instructions are embedded in inputs to override a model's intended behavior.
  ​
* RAG (Retrieval-Augmented Generation): A technique that improves large language models by retrieving relevant information from external knowledge sources before generating a response.
  ​
* Red-Teaming: The practice of actively testing AI systems by simulating adversarial attacks to identify vulnerabilities.
  ​
* SLSA Provenance: Metadata defined by the SLSA framework that records where, when, and how an artifact was produced (e.g., source repository, commit hash, build system, and parameters).
  ​
* SBOM (Software Bill of Materials): A formal record that contains the details and supply chain relationships of various components used in building software or AI models.
  ​
* SHAP (SHapley Additive exPlanations): A game-theoretic approach to explain the output of any machine learning model by calculating the contribution of each feature to the prediction.
  ​
* Strong Authentication: Authentication that resists credential theft and replay attacks by requiring at least two factors (knowledge, possession, inherence) and phishing-resistant mechanisms such as FIDO2/WebAuthn, certificate-based service authentication, or short-lived tokens.
  ​
* Supply Chain Attack: Compromising a system by targeting weaker elements in its supply chain, such as third-party libraries, datasets, or pre-trained models.
  ​
* Transfer Learning: A technique where a model developed for one task is reused as the starting point for a model on a second task.
  ​
* Vector Database: A specialized database designed to store high-dimensional vectors (embeddings) and efficiently perform similarity searches.
  ​
* Vulnerability Scanning: Automated tools that detect known security vulnerabilities in software components, including AI frameworks and dependencies.
  ​
* Watermarking: Techniques for embedding imperceptible markers in AI-generated content to trace its origin or identify AI generation.
  ​
* Zero-Day Vulnerability: A previously unknown flaw that attackers can exploit before developers create and release a patch.

