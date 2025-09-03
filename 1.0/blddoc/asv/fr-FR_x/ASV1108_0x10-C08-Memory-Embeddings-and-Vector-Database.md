# C8 Memory, Représentations vectorielles et sécurité des bases de données vectorielles

## Objectif de contrôle

Les embeddings et les stockages vectoriels agissent comme la mémoire active des systèmes d'IA contemporains, acceptant en continu les données fournies par les utilisateurs et les réintégrant dans les contextes des modèles via la génération augmentée par récupération (RAG). Si elle est laissée sans gouvernance, cette mémoire peut divulguer des informations personnelles identifiables (PII), violer le consentement ou être utilisée pour reconstituer le texte d'origine. L'objectif de cette famille de contrôles est de durcir les pipelines de mémoire et les bases de données vectorielles afin que l'accès respecte le principe du moindre privilège, que les embeddings préservent la vie privée, que les vecteurs stockés expirent ou puissent être révoqués à la demande, et que la mémoire par utilisateur ne contamine jamais les invites ou les réponses générées d'un autre utilisateur.

---

## C8.1 Contrôles d'accès sur la mémoire et les indices RAG

Appliquer des contrôles d'accès granulaires sur chaque collection de vecteurs.

|   #   | description                                                                                                                                                                                                               | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 8.1.1 | Vérifiez que les règles de contrôle d'accès au niveau des lignes et des espaces de noms restreignent les opérations d'insertion, de suppression et de requête par locataire, par collection ou par étiquette de document. |   1    | D/V  |
| 8.1.2 | Vérifiez que les clés d'API ou les jetons JWT contiennent des revendications à portée limitée (par exemple, identifiants de collection, verbes d'action) et qu'ils soient renouvelés au moins une fois par trimestre.     |   1    | D/V  |
| 8.1.3 | Vérifiez que les tentatives d'escalade de privilèges (par exemple des requêtes de similarité entre espaces de noms) sont détectées et journalisées dans un SIEM dans les 5 minutes.                                       |   2    | D/V  |
| 8.1.4 | Vérifiez que les journaux d'audit de la base de données vectorielle enregistrent l'identifiant du sujet, l'opération, l'ID de vecteur/espace de noms, le seuil de similarité et le nombre de résultats.                   |   2    | D/V  |
| 8.1.5 | Vérifiez que les décisions d'accès sont testées pour détecter des failles de contournement à chaque mise à niveau des moteurs ou lorsque les règles de partitionnement d'index changent.                                  |   3    |  V   |

---

## C8.2 Nettoyage et validation des embeddings

Effectuer un pré-filtrage du texte pour les informations personnellement identifiables (PII), les masquer ou les pseudonymiser avant la vectorisation, et, éventuellement, post-traiter les représentations vectorielles pour éliminer les signaux résiduels.

|   #   | description                                                                                                                                                                                                                                                           | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 8.2.1 | Vérifiez que les PII et les données réglementées sont détectées par des classificateurs automatisés et masquées, tokenisées ou supprimées avant l'embedding.                                                                                                          |   1    | D/V  |
| 8.2.2 | Vérifiez que les pipelines d'embeddings rejettent ou mettent en quarantaine les entrées contenant du code exécutable ou des artefacts non UTF-8 susceptibles de contaminer l'index.                                                                                   |   1    |  D   |
| 8.2.3 | Vérifiez que l’assainissement par confidentialité différentielle locale ou métrique est appliqué aux embeddings de phrases dont la distance par rapport à tout jeton d’informations personnellement identifiables (PII) connu est inférieure à un seuil configurable. |   2    | D/V  |
| 8.2.4 | Vérifiez que l’efficacité de la sanitisation (par exemple, le rappel de la rédaction des PII, dérive sémantique) est validée au moins semestriellement sur des corpus de référence.                                                                                   |   2    |  V   |
| 8.2.5 | Vérifiez que les configurations de sanitisation sont versionnées et que les modifications font l'objet d'une revue par les pairs.                                                                                                                                     |   3    | D/V  |

---

## C8.3 Expiration de la mémoire, Révocation et Suppression

Le RGPD et des lois similaires exigent une suppression en temps utile ; les stockages vectoriels doivent donc prendre en charge les TTLs, les suppressions définitives et le tombstoning afin que les vecteurs révoqués ne puissent pas être récupérés ni réindexés.

|   #   | description                                                                                                                                                                                                         | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 8.3.1 | Vérifiez que tous les vecteurs et tous les enregistrements de métadonnées portent un TTL ou une étiquette de rétention explicite, et que ces éléments sont pris en charge par les tâches de nettoyage automatisées. |   1    | D/V  |
| 8.3.2 | Vérifiez que les demandes de suppression initiées par l'utilisateur purgent les vecteurs, les métadonnées, les copies en cache et les indices dérivés dans un délai de 30 jours.                                    |   1    | D/V  |
| 8.3.3 | Vérifiez que les suppressions logiques sont suivies d'un déchiquetage cryptographique des blocs de stockage si le matériel le prend en charge, ou par la destruction des clés du Key Vault.                         |   2    |  D   |
| 8.3.4 | Vérifiez que les vecteurs expirés sont exclus des résultats de la recherche du plus proche voisin en < 500 ms après l'expiration.                                                                                   |   3    | D/V  |

---

## C8.4 Prévenir l'inversion des embeddings et la fuite

Des défenses récentes—superposition de bruit, réseaux de projection, perturbation des neurones de confidentialité et chiffrement au niveau de la couche applicative—peuvent faire chuter les taux d'inversion au niveau des jetons en dessous de 5%.

|   #   | description                                                                                                                                                                                                 | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 8.4.1 | Vérifier qu’un modèle de menace formel couvrant les attaques d’inversion, d’appartenance et d’inférence d’attributs existe et est révisé annuellement.                                                      |   1    |  V   |
| 8.4.2 | Vérifiez que le chiffrement au niveau de l'application ou le chiffrement recherchable protège les vecteurs contre les lectures directes par les administrateurs d'infrastructure ou le personnel cloud.     |   2    | D/V  |
| 8.4.3 | Vérifiez que les paramètres de défense (ε pour la confidentialité différentielle, bruit σ, rang de projection k) équilibrent la confidentialité des jetons ≥ 99 % et l'utilité ≤ 3 % de perte de précision. |   3    |  V   |
| 8.4.4 | Vérifiez que les métriques de résilience à l’inversion font partie des portes de déploiement pour les mises à jour des modèles, avec des budgets de régression définis.                                     |   3    | D/V  |

---

## C8.5 Contrôle de la portée pour la mémoire spécifique à l'utilisateur

La fuite entre locataires demeure l’un des principaux risques liés à la RAG : des requêtes de similarité mal filtrées peuvent révéler les documents privés d’un autre client.

|   #   | description                                                                                                                                                                                            | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 8.5.1 | Vérifiez que chaque requête de récupération est filtrée a posteriori par l'ID du locataire/utilisateur avant d'être transmise à l'invite du modèle de langage.                                         |   1    | D/V  |
| 8.5.2 | Vérifiez que les noms de collection ou les identifiants avec espace de noms soient salés par utilisateur ou par locataire afin que les vecteurs ne puissent pas entrer en collision entre les portées. |   1    |  D   |
| 8.5.3 | Vérifiez que les résultats de similarité supérieurs à un seuil de distance configurable mais en dehors du champ d'application de l'appelant sont ignorés et déclenchent des alertes de sécurité.       |   2    | D/V  |
| 8.5.4 | Vérifiez que les tests de stress multi-locataires simulent des requêtes adverses visant à récupérer des documents hors périmètre et démontrent l'absence de fuite.                                     |   2    |  V   |
| 8.5.5 | Vérifiez que les clés de chiffrement sont séparées par locataire, assurant l'isolement cryptographique même si le stockage physique est partagé.                                                       |   3    | D/V  |

---

## C8.6 Sécurité avancée du système de mémoire

Contrôles de sécurité pour des architectures de mémoire sophistiquées, y compris la mémoire épisodique, la mémoire sémantique et la mémoire de travail, avec des exigences d'isolation et de validation spécifiques.

|   #   | description                                                                                                                                                                                                                                                                                                                      | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 8.6.1 | Vérifiez que les différents types de mémoire (mémoire épisodique, mémoire sémantique, mémoire de travail) disposent de contextes de sécurité isolés avec des contrôles d'accès basés sur les rôles, des clés de chiffrement distinctes et des schémas d'accès documentés pour chaque type de mémoire.                            |   1    | D/V  |
| 8.6.2 | Vérifiez que les processus de consolidation de la mémoire intègrent une validation de sécurité afin de prévenir l'injection de mémoires malveillantes par la sanitisation du contenu, la vérification de la source et les vérifications d'intégrité avant le stockage.                                                           |   2    | D/V  |
| 8.6.3 | Vérifiez que les requêtes de récupération en mémoire sont validées et assainies afin d'empêcher l'extraction d'informations non autorisées par l'analyse des motifs de requête, l'application des contrôles d'accès et le filtrage des résultats.                                                                                |   2    | D/V  |
| 8.6.4 | Vérifiez que les mécanismes d'effacement de la mémoire effacent les informations sensibles de manière sécurisée, avec des garanties d'effacement cryptographique, en utilisant la suppression de clés, l'écrasement sur plusieurs passes ou la suppression sécurisée basée sur le matériel avec des certificats de vérification. |   3    | D/V  |
| 8.6.5 | Vérifier que l’intégrité du système mémoire est surveillée en continu pour détecter des modifications ou corruptions non autorisées grâce à des sommes de contrôle, des journaux d’audit et des alertes automatisées lorsque le contenu mémoire change en dehors des opérations normales.                                        |   3    | D/V  |

---

## Références

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

