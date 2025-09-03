# C3 Gestion du cycle de vie des modèles et contrôle des changements

## Objectif de contrôle

Les systèmes d'IA doivent mettre en œuvre des processus de contrôle des modifications qui empêchent des modifications non autorisées ou dangereuses du modèle d'atteindre la production. Ce contrôle garantit l'intégrité du modèle tout au long du cycle de vie--du développement au déploiement jusqu'à la mise hors service--ce qui permet une réponse rapide aux incidents et assure la traçabilité et la responsabilité de l'ensemble des changements.

Objectif de sécurité principal: Seuls les modèles autorisés et validés atteignent la production en utilisant des processus contrôlés qui maintiennent l'intégrité, la traçabilité et la récupérabilité.

---

## C3.1 Autorisation et Intégrité du Modèle

Seuls les modèles autorisés dont l'intégrité est vérifiée atteignent les environnements de production.

|   #   | description                                                                                                                                                                                                                                                | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 3.1.1 | Vérifiez que tous les artefacts du modèle (poids, configurations, tokeniseurs) sont signés cryptographiquement par des entités autorisées avant le déploiement.                                                                                            |   1    | D/V  |
| 3.1.2 | Vérifiez que l'intégrité du modèle est validée au moment du déploiement et que les échecs de la vérification de signature empêchent le chargement du modèle.                                                                                               |   1    | D/V  |
| 3.1.3 | Vérifiez que les enregistrements de provenance du modèle incluent l'identité de l'entité autorisante, les sommes de contrôle des données d'entraînement, les résultats des tests de validation avec le statut réussite/échec et un horodatage de création. |   2    | D/V  |
| 3.1.4 | Vérifiez que tous les artefacts du modèle utilisent le versionnage sémantique (MAJOR.MINOR.PATCH) avec des critères documentés précisant quand chaque composant de la version s'incrémente.                                                                |   2    | D/V  |
| 3.1.5 | Vérifiez que le traçage des dépendances maintient un inventaire en temps réel qui permet une identification rapide de tous les systèmes consommateurs.                                                                                                     |   2    |  V   |

---

## C3.2 Validation et tests du modèle

Les modèles doivent passer les validations de sécurité et de sûreté définies avant le déploiement.

|   #   | description                                                                                                                                                                                                                                                           | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 3.2.1 | Vérifiez que les modèles subissent des tests de sécurité automatisés comprenant la validation des entrées, la sanitisation des sorties et des évaluations de sécurité avec des seuils de réussite/échec organisationnels préalablement convenus avant le déploiement. |   1    | D/V  |
| 3.2.2 | Vérifiez que les échecs de validation bloquent automatiquement le déploiement du modèle après l'approbation explicite d'une dérogation par le personnel autorisé pré-désigné, avec des justifications commerciales documentées.                                       |   1    | D/V  |
| 3.2.3 | Vérifiez que les résultats de test sont signés cryptographiquement et liés de manière immuable au hash de la version du modèle spécifique en cours de validation.                                                                                                     |   2    |  V   |
| 3.2.4 | Vérifiez que les déploiements d'urgence nécessitent une évaluation des risques de sécurité documentée et l'approbation d'une autorité de sécurité prédésignée, dans des délais préalablement convenus.                                                                |   2    | D/V  |

---

## C3.3 Déploiement contrôlé et retour arrière

Les déploiements de modèles doivent être contrôlés, surveillés et réversibles.

|   #   | description                                                                                                                                                                                                                                                                                                          | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 3.3.1 | Vérifiez que les déploiements en production mettent en œuvre des mécanismes de déploiement progressif (déploiements canari, déploiements bleu-vert) avec des déclencheurs de retour arrière automatisés basés sur des taux d'erreur convenus à l'avance, des seuils de latence ou des critères d'alerte de sécurité. |   1    |  D   |
| 3.3.2 | Vérifiez que les capacités de rollback restaurent l'état complet du modèle (poids, configurations, dépendances) de manière atomique dans des fenêtres temporelles organisationnelles pré-définies.                                                                                                                   |   1    | D/V  |
| 3.3.3 | Vérifiez que les processus de déploiement valident les signatures cryptographiques et calculent les sommes de contrôle d’intégrité avant l’activation du modèle, et que le déploiement échoue en cas de discordance.                                                                                                 |   2    | D/V  |
| 3.3.4 | Vérifier que les capacités d'arrêt d'urgence du modèle peuvent désactiver les points de terminaison du modèle dans des délais de réponse pré-définis, soit via des disjoncteurs automatiques, soit via des interrupteurs d'arrêt manuels.                                                                            |   2    | D/V  |
| 3.3.5 | Vérifiez que les artefacts de rollback (versions précédentes du modèle, configurations, dépendances) sont conservés conformément aux politiques organisationnelles avec un stockage immuable pour la réponse aux incidents.                                                                                          |   2    |  V   |

---

## C3.4 Traçabilité des changements et audit

Tous les changements du cycle de vie du modèle doivent être traçables et audités.

|   #   | description                                                                                                                                                                                                                                                                  | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 3.4.1 | Vérifiez que toutes les modifications du modèle (déploiement, configuration, retrait) génèrent des enregistrements d'audit immuables comprenant un horodatage, l'identité d'un acteur authentifié, un type de modification et les états avant/après.                         |   1    |  V   |
| 3.4.2 | Vérifiez que l'accès au journal d'audit nécessite une autorisation appropriée et que toutes les tentatives d'accès sont enregistrées avec l'identité de l'utilisateur et un horodatage.                                                                                      |   2    | D/V  |
| 3.4.3 | Vérifiez que les modèles d'invite et les messages système sont sous contrôle de version dans des dépôts Git, avec une revue de code obligatoire et une approbation par des réviseurs désignés avant le déploiement.                                                          |   2    | D/V  |
| 3.4.4 | Vérifiez que les enregistrements d'audit contiennent des détails suffisants (empreintes du modèle, instantanés de configuration, versions des dépendances) pour permettre une reconstruction complète de l'état du modèle pour tout horodatage dans la période de rétention. |   2    |  V   |

---

## C3.5 Bonnes pratiques de développement sécurisé

Les processus de développement et d'entraînement des modèles doivent suivre des pratiques sécurisées afin d'éviter toute compromission.

|   #   | description                                                                                                                                                                                                                                                   | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 3.5.1 | Vérifiez que les environnements de développement, de test et de production du modèle sont séparés physiquement ou logiquement. Ils ne disposent pas d'infrastructure partagée, de contrôles d'accès distincts et de stockages de données isolés.              |   1    |  D   |
| 3.5.2 | Vérifiez que l'entraînement et l'ajustement fin du modèle se déroulent dans des environnements isolés avec un accès réseau contrôlé.                                                                                                                          |   1    |  D   |
| 3.5.3 | Vérifiez que les sources de données d'entraînement sont validées par des contrôles d'intégrité et authentifiées via des sources de confiance avec une traçabilité documentée de la chaîne de custodie avant leur utilisation dans le développement du modèle. |   1    | D/V  |
| 3.5.4 | Vérifiez que les artefacts de développement du modèle (hyperparamètres, scripts d'entraînement, fichiers de configuration) sont stockés dans le contrôle de version et nécessitent une revue par les pairs avant d'être utilisés pour l'entraînement.         |   2    |  D   |

---

## C3.6 Mise hors service du modèle et décommissionnement

Les modèles doivent être retirés de manière sécurisée lorsqu'ils ne sont plus nécessaires ou lorsque des problèmes de sécurité sont identifiés.

|   #   | description                                                                                                                                                                                                                                                                   | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 3.6.1 | Vérifiez que les processus de retrait des modèles analysent automatiquement les graphes de dépendances, identifient tous les systèmes consommateurs et fournissent des périodes de préavis convenues à l'avance avant la mise hors service.                                   |   1    |  D   |
| 3.6.2 | Vérifiez que les artefacts des modèles retirés sont effacés en toute sécurité à l'aide d'un effacement cryptographique ou d'un écrasement à plusieurs passes, conformément aux politiques de rétention des données documentées, avec des certificats de destruction vérifiés. |   1    | D/V  |
| 3.6.3 | Vérifiez que les événements de retrait du modèle sont enregistrés avec horodatage et identité de l'acteur, et que les signatures du modèle sont révoquées pour empêcher toute réutilisation.                                                                                  |   2    |  V   |
| 3.6.4 | Vérifier que la mise hors service d'urgence du modèle peut désactiver l'accès au modèle dans les délais de réponse d'urgence préétablis via des interrupteurs d'arrêt automatisés si des vulnérabilités de sécurité critiques sont découvertes.                               |   2    | D/V  |

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

