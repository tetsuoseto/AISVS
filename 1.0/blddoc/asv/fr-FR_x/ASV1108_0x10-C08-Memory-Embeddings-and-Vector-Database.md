# Sécurité de la mémoire C8, des embeddings et des bases de données vectorielles

## Objectif de contrôle

Les embeddings et les magasins de vecteurs agissent comme la « mémoire vive » des systèmes d’IA contemporains, acceptant en continu les données fournies par les utilisateurs et les réinjectant dans les contextes des modèles via la génération augmentée par récupération (RAG). Si cette mémoire n’est pas régulée, elle peut divulguer des informations personnelles identifiables (PII), violer le consentement ou être inversée pour reconstituer le texte original. L’objectif de cette famille de contrôles est de renforcer les pipelines de mémoire et les bases de données vectorielles afin que l’accès soit basé sur le principe du moindre privilège, que les embeddings préservent la confidentialité, que les vecteurs stockés expirent ou puissent être révoqués à la demande, et que la mémoire par utilisateur ne contamine jamais les invites ou complétions d’un autre utilisateur.

---

## C8.1 Contrôles d'accès sur la mémoire et les indices RAG

Appliquez des contrôles d'accès granulaires sur chaque collection de vecteurs.

|   #   | Description                                                                                                                                                                                           | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 8.1.1 | Vérifiez que les règles de contrôle d'accès au niveau des lignes/espace de noms limitent les opérations d'insertion, de suppression et de requête par locataire, collection ou étiquette de document. |   1    | D/V  |
| 8.1.2 | Vérifiez que les clés API ou les JWT portent des revendications limitées (par exemple, des identifiants de collection, des verbes d’action) et qu’ils sont renouvelés au moins tous les trimestres.   |   1    | D/V  |
| 8.1.3 | Vérifiez que les tentatives d'escalade de privilèges (par exemple, les requêtes de similarité entre namespaces) sont détectées et enregistrées dans un SIEM sous 5 minutes.                           |   2    | D/V  |
| 8.1.4 | Vérifiez que la base de données vectorielle enregistre dans les audits l'identifiant du sujet, l'opération, l'ID/namespace du vecteur, le seuil de similarité et le nombre de résultats.              |   2    | D/V  |
| 8.1.5 | Vérifiez que les décisions d'accès sont testées pour détecter les failles de contournement chaque fois que les moteurs sont mis à jour ou que les règles de fragmentation d'index changent.           |   3    |  V   |

---

## C8.2 Assainissement et validation des embeddings

Pré-filtrer le texte pour les informations personnelles identifiables (IPI), les anonymiser ou les pseudonymiser avant la vectorisation, et éventuellement post-traiter les embeddings pour éliminer les signaux résiduels.

|   #   | Description                                                                                                                                                                                                                   | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 8.2.1 | Vérifiez que les données PII et réglementées sont détectées via des classificateurs automatisés et masquées, tokenisées ou supprimées avant l'incorporation.                                                                  |   1    | D/V  |
| 8.2.2 | Vérifiez que les pipelines d'intégration rejettent ou mettent en quarantaine les entrées contenant du code exécutable ou des artefacts non UTF-8 pouvant compromettre l'index.                                                |   1    |  D   |
| 8.2.3 | Vérifiez que la sanitisation par confidentialité différentielle locale ou métrique est appliquée aux embeddings de phrases dont la distance à tout jeton PII connu est inférieure à un seuil configurable.                    |   2    | D/V  |
| 8.2.4 | Vérifiez que l'efficacité de la désinfection (par exemple, le rappel de la rédaction des informations personnelles identifiables, la dérive sémantique) est validée au moins semestriellement contre des corpus de référence. |   2    |  V   |
| 8.2.5 | Vérifiez que les configurations de désinfection sont contrôlées par version et que les modifications font l'objet d'une revue par les pairs.                                                                                  |   3    | D/V  |

---

## C8.3 Expiration, Révocation et Suppression de la Mémoire

Le RGPD « droit à l'oubli » et des lois similaires exigent une suppression rapide ; les magasins de vecteurs doivent donc prendre en charge les TTL, les suppressions définitives et le tomb-stoning afin que les vecteurs révoqués ne puissent pas être récupérés ou réindexés.

|   #   | Description                                                                                                                                                                                | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 8.3.1 | Vérifiez que chaque vecteur et chaque enregistrement de métadonnées possède un TTL ou une étiquette de rétention explicite respectée par les tâches de nettoyage automatisées.             |   1    | D/V  |
| 8.3.2 | Vérifiez que les demandes de suppression initiées par l'utilisateur suppriment les vecteurs, les métadonnées, les copies en cache et les indices dérivés dans un délai de 30 jours.        |   1    | D/V  |
| 8.3.3 | Vérifiez que les suppressions logiques sont suivies par un effacement cryptographique des blocs de stockage si le matériel le supporte, ou par la destruction de la clé du coffre de clés. |   2    |  D   |
| 8.3.4 | Vérifiez que les vecteurs expirés sont exclus des résultats de la recherche de plus proches voisins en moins de 500 ms après leur expiration.                                              |   3    | D/V  |

---

## C8.4 Prévenir l'inversion et la fuite d'incorporation

Les défenses récentes—superposition de bruit, réseaux de projection, perturbation des neurones de confidentialité, et chiffrement au niveau de l’application—peuvent réduire les taux d’inversion au niveau des tokens à moins de 5 %.

|   #   | Description                                                                                                                                                                                                          | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 8.4.1 | Vérifiez qu'un modèle de menace formel couvrant les attaques d'inversion, de membership et d'inférence d'attributs existe et est révisé annuellement.                                                                |   1    |  V   |
| 8.4.2 | Vérifiez que le chiffrement au niveau de la couche application ou le chiffrement consultable protège les vecteurs contre les lectures directes par les administrateurs de l'infrastructure ou le personnel du cloud. |   2    | D/V  |
| 8.4.3 | Vérifiez que les paramètres de défense (ε pour DP, bruit σ, rang de projection k) équilibrent la confidentialité ≥ 99 % de protection des tokens et l'utilité ≤ 3 % de perte de précision.                           |   3    |  V   |
| 8.4.4 | Vérifiez que les métriques de résilience à l'inversion font partie des critères de validation pour les mises à jour du modèle, avec des budgets de régression définis.                                               |   3    | D/V  |

---

## C8.5 Application de la portée pour la mémoire spécifique à l’utilisateur

La fuite entre locataires reste un risque majeur de RAG : des requêtes de similitude mal filtrées peuvent faire apparaître les documents privés d'un autre client.

|   #   | Description                                                                                                                                                                                      | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 8.5.1 | Vérifiez que chaque requête de récupération est filtrée ultérieurement par l’ID du locataire/utilisateur avant d’être envoyée à l’invite du LLM.                                                 |   1    | D/V  |
| 8.5.2 | Vérifiez que les noms de collections ou les ID avec espaces de noms sont salés par utilisateur ou locataire afin que les vecteurs ne puissent pas entrer en collision entre les espaces.         |   1    |  D   |
| 8.5.3 | Vérifiez que les résultats de similarité supérieurs à un seuil de distance configurable mais en dehors du périmètre de l'appelant sont rejetés et déclenchent des alertes de sécurité.           |   2    | D/V  |
| 8.5.4 | Vérifiez que les tests de charge multi-tenant simulent des requêtes adversariales tentant de récupérer des documents hors de leur champ d’application et démontrent une absence totale de fuite. |   2    |  V   |
| 8.5.5 | Vérifiez que les clés de chiffrement sont segreguées par locataire, garantissant une isolation cryptographique même si le stockage physique est partagé.                                         |   3    | D/V  |

---

## C8.6 Sécurité avancée des systèmes de mémoire

Contrôles de sécurité pour des architectures mémoire sophistiquées comprenant la mémoire épisodique, sémantique et de travail avec des exigences spécifiques d'isolation et de validation.

|   #   | Description                                                                                                                                                                                                                                                                                                      | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 8.6.1 | Vérifier que les différents types de mémoire (épisodique, sémantique, de travail) disposent de contextes de sécurité isolés avec des contrôles d’accès basés sur les rôles, des clés de chiffrement séparées et des schémas d’accès documentés pour chaque type de mémoire.                                      |   1    | D/V  |
| 8.6.2 | Vérifiez que les processus de consolidation de la mémoire incluent une validation de la sécurité pour prévenir l'injection de mémoires malveillantes via la sanitation du contenu, la vérification de la source et les contrôles d'intégrité avant le stockage.                                                  |   2    | D/V  |
| 8.6.3 | Vérifiez que les requêtes de récupération de mémoire sont validées et assainies pour empêcher l'extraction d'informations non autorisées par l'analyse des modèles de requêtes, l'application du contrôle d'accès et le filtrage des résultats.                                                                  |   2    | D/V  |
| 8.6.4 | Vérifiez que les mécanismes d'oubli de la mémoire suppriment de manière sécurisée les informations sensibles avec des garanties d'effacement cryptographique en utilisant la suppression de clés, la réécriture multiple ou la suppression sécurisée basée sur le matériel avec des certificats de vérification. |   3    | D/V  |
| 8.6.5 | Vérifiez que l'intégrité du système mémoire est continuellement surveillée pour détecter toute modification non autorisée ou corruption grâce à des sommes de contrôle, des journaux d'audit et des alertes automatisées en cas de changement du contenu mémoire en dehors des opérations normales.              |   3    | D/V  |

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

