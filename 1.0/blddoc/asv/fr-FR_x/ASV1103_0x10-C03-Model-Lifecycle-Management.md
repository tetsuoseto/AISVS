# Gestion du cycle de vie du modèle C3 et contrôle des modifications

## Objectif de contrôle

Les systèmes d'IA doivent mettre en œuvre des processus de contrôle des modifications qui empêchent les modifications non autorisées ou dangereuses du modèle d'atteindre la production. Ce contrôle garantit l'intégrité du modèle tout au long de son cycle de vie--du développement jusqu'au déploiement et à la mise hors service--ce qui permet une réponse rapide aux incidents et maintient la responsabilité de tous les changements.

Objectif de sécurité fondamentale : Seuls les modèles autorisés et validés atteignent la production en utilisant des processus contrôlés qui garantissent l'intégrité, la traçabilité et la capacité de récupération.

---

## C3.1 Autorisation et Intégrité du Modèle

Seuls les modèles autorisés avec une intégrité vérifiée atteignent les environnements de production.

|   #   | Description                                                                                                                                                                                                                                                  | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 3.1.1 | Vérifiez que tous les artefacts du modèle (poids, configurations, tokenizeurs) sont signés cryptographiquement par des entités autorisées avant le déploiement.                                                                                              |   1    | D/V  |
| 3.1.2 | Vérifiez que le suivi des dépendances maintient un inventaire en temps réel permettant l’identification de tous les systèmes consommateurs.                                                                                                                  |   2    |  V   |
| 3.1.3 | Vérifiez que les enregistrements de provenance du modèle incluent l'identité d'une entité autorisante, les sommes de contrôle des données d'entraînement, les résultats des tests de validation avec le statut réussite/échec, et un horodatage de création. |   3    | D/V  |

---

## C3.2 Validation et test du modèle

Les modèles doivent passer les validations de sécurité et de sûreté définies avant le déploiement.

|   #   | Description                                                                                                                                                                                                                                                            | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 3.2.1 | Vérifiez que les modèles subissent des tests de sécurité automatisés incluant la validation des entrées, la désinfection des sorties, et des évaluations de sécurité avec des seuils d’acceptation/rejet organisationnels préalablement convenus avant le déploiement. |   1    | D/V  |
| 3.2.2 | Vérifiez que toutes les modifications du modèle (déploiement, configuration, retrait) génèrent des enregistrements d'audit immuables incluant un horodatage, une identité d'acteur authentifiée, un type de modification, ainsi que les états avant/après.             |   1    |  V   |
| 3.2.3 | Vérifiez que les échecs de validation bloquent automatiquement le déploiement du modèle après une approbation explicite de dérogation provenant de personnel autorisé pré-désigné avec des justifications commerciales documentées.                                    |   2    | D/V  |

---

## C3.3 Déploiement Contrôlé & Repli

Les déploiements de modèles doivent être contrôlés, surveillés et réversibles.

|   #   | Description                                                                                                                                                                                                                                                                                                                  | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 3.3.1 | Vérifiez que les processus de déploiement valident les signatures cryptographiques et calculent les sommes de contrôle d'intégrité avant l'activation du modèle, en interrompant le déploiement en cas de divergence.                                                                                                        |   1    | D/V  |
| 3.3.2 | Vérifiez que les déploiements en production mettent en œuvre des mécanismes de déploiement progressif (déploiements canaris, déploiements blue-green) avec des déclencheurs de retour en arrière automatisés basés sur des taux d'erreur, des seuils de latence ou des critères d'alerte de sécurité préalablement convenus. |   1    |  D   |
| 3.3.3 | Vérifiez que les capacités de restauration annulent de manière atomique l’état complet du modèle (poids, configurations, dépendances).                                                                                                                                                                                       |   2    | D/V  |
| 3.3.4 | Vérifiez que les capacités d'arrêt d'urgence du modèle peuvent désactiver les points de terminaison du modèle dans un délai de réponse prédéfini.                                                                                                                                                                            |   3    | D/V  |

---

## C3.4 Pratiques de Développement Sécurisé

Les processus de développement et d'entraînement des modèles doivent suivre des pratiques sécurisées pour prévenir toute compromission.

|   #   | Description                                                                                                                                                                                                                                                                                                 | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 3.4.1 | Vérifiez que les environnements de développement, de test et de production du modèle sont séparés physiquement ou logiquement. Ils ne partagent aucune infrastructure, disposent de contrôles d'accès distincts et de bases de données isolées.                                                             |   1    | D/V  |
| 3.4.2 | Vérifiez que les artefacts de développement du modèle (hyperparamètres, scripts d'entraînement, fichiers de configuration, modèles de requêtes, etc.) sont stockés dans un système de gestion de versions et nécessitent une approbation par revue par les pairs avant d'être utilisés pour l'entraînement. |   1    |  D   |
| 3.4.3 | Vérifiez que la formation du modèle et l'ajustement fin se déroulent dans des environnements isolés avec un accès réseau contrôlé.                                                                                                                                                                          |   2    | D/V  |
| 3.4.4 | Vérifiez que les sources de données d'entraînement sont validées par des contrôles d'intégrité et authentifiées via des sources fiables avec une chaîne de custody documentée avant leur utilisation dans le développement du modèle.                                                                       |   2    |  D   |

---

## Retrait et mise hors service du modèle C3.5

Les modèles doivent être retirés de manière sécurisée lorsqu'ils ne sont plus nécessaires ou lorsqu'on identifie des problèmes de sécurité.

|   #   | Description                                                                                                                                                                                | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 3.5.1 | Vérifiez que les artefacts du modèle retiré sont effacés de manière sécurisée en utilisant une suppression cryptographique sécurisée.                                                      |   1    | D/V  |
| 3.5.2 | Vérifiez que les événements de retrait de modèle sont consignés avec horodatage et identité de l'acteur, et que les signatures du modèle sont révoquées pour empêcher toute réutilisation. |   2    |  V   |

---

## Références

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

