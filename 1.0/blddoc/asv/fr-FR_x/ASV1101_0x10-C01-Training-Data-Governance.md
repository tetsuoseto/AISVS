# C1 Gouvernance des données d'entraînement et gestion des biais

## Objectif de contrôle

Les données d'entraînement doivent être sourcées, gérées et maintenues de manière à préserver leur provenance, leur sécurité, leur qualité et leur équité. Cela permet de respecter les obligations légales et de réduire les risques de biais, d'empoisonnement ou de violations de la vie privée qui apparaissent pendant l'entraînement et qui pourraient affecter l'ensemble du cycle de vie de l'IA.

---

## C1.1 Provenance des données d'entraînement

Maintenir un inventaire vérifiable de l’ensemble des jeux de données, n’accepter que des sources fiables et enregistrer chaque changement pour assurer l’auditabilité.

|   #   | description                                                                                                                                                                                                                       | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 1.1.1 | Vérifiez qu'un inventaire à jour de chaque source de données d'entraînement (origine, responsable/gestionnaire, licence, méthode de collecte, contraintes d'utilisation prévues et historique du traitement) est maintenu à jour. |   1    | D/V  |
| 1.1.2 | Vérifiez que les processus de traitement des données d'entraînement excluent les caractéristiques, attributs ou champs inutiles (par exemple, métadonnées inutilisées, PII sensibles, données de test divulguées).                |   1    | D/V  |
| 1.1.3 | Vérifiez que tous les changements apportés au jeu de données sont soumis à un flux d'approbation enregistré.                                                                                                                      |   2    | D/V  |
| 1.1.4 | Vérifiez que les ensembles de données ou leurs sous-ensembles portent un filigrane ou une empreinte numérique, lorsque cela est faisable.                                                                                         |   3    | D/V  |

---

## C1.2 Sécurité et intégrité des données d'entraînement

Restreindre l'accès aux données d'entraînement, les chiffrer au repos et en transit, et vérifier leur intégrité pour prévenir l'altération, le vol ou l'empoisonnement des données.

|   #   | description                                                                                                                                                                                                              | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 1.2.1 | Vérifiez que les contrôles d'accès protègent le stockage des données d'entraînement et les pipelines.                                                                                                                    |   1    | D/V  |
| 1.2.2 | Vérifiez que tout accès aux données d'entraînement est enregistré, y compris l'utilisateur, l'heure et l'action.                                                                                                         |   2    | D/V  |
| 1.2.3 | Vérifiez que les ensembles de données d’entraînement sont chiffrés en transit et au repos, en utilisant des algorithmes cryptographiques conformes aux normes de l’industrie et des pratiques de gestion des clés.       |   2    | D/V  |
| 1.2.4 | Vérifiez que des hachages cryptographiques ou des signatures numériques sont utilisés pour garantir l'intégrité des données lors du stockage et du transfert des données d'entraînement.                                 |   2    | D/V  |
| 1.2.5 | Vérifiez que les techniques de détection automatisées sont mises en œuvre pour prévenir les modifications non autorisées ou la corruption des données d'entraînement.                                                    |   2    | D/V  |
| 1.2.6 | Vérifiez que les données d'entraînement obsolètes sont purgées de manière sécurisée ou anonymisées.                                                                                                                      |   2    | D/V  |
| 1.2.7 | Vérifier que toutes les versions des jeux de données d'entraînement sont identifiables de manière unique, stockées de manière immuable et vérifiables afin de permettre le retour en arrière et l'analyse médico-légale. |   3    | D/V  |

---

## C1.3 Qualité, intégrité et sécurité de l'étiquetage des données d'entraînement

Protéger les étiquettes et exiger une revue technique pour les données critiques.

|   #   | description                                                                                                                                                                                                                                 | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 1.3.1 | Vérifier que des hachages cryptographiques ou des signatures numériques sont appliqués aux artefacts d'étiquetage afin d'en assurer l'intégrité et l'authenticité.                                                                          |   2    | D/V  |
| 1.3.2 | Vérifiez que les interfaces d’étiquetage et les plateformes imposent des contrôles d’accès robustes, conservent des journaux d’audit inviolables de toutes les activités d’étiquetage et protègent contre les modifications non autorisées. |   2    | D/V  |
| 1.3.3 | Vérifiez que les informations sensibles contenues dans les étiquettes sont masquées, anonymisées ou chiffrées au niveau des champs de données, au repos et en transit.                                                                      |   3    | D/V  |

---

## C1.4 Qualité des données d'entraînement et assurance de la sécurité

Combinez la validation automatisée, les vérifications manuelles ponctuelles et les actions correctives consignées pour garantir la fiabilité de l'ensemble de données.

|   #   | description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 1.4.1 | Vérifiez que les tests automatisés détectent les erreurs de format et les valeurs nulles à chaque ingestion ou transformation de données significative.                                                                                                                                                                                                                                                                                                                                                                              |   1    |  D   |
| 1.4.2 | Vérifiez que les pipelines d'entraînement et de fine-tuning des LLM intègrent la détection d'empoisonnement et la validation de l'intégrité des données (par exemple, des méthodes statistiques, la détection d'outliers et l'analyse des embeddings) afin d'identifier les attaques d'empoisonnement potentielles (par exemple basculement d'étiquettes, insertion de déclencheurs de porte dérobée, commandes de changement de rôle, attaques d'instances influentes) ou des corruptions involontaires des données d'entraînement. |   2    | D/V  |
| 1.4.3 | Vérifiez que des défenses appropriées, telles que l'entraînement adversarial (utilisant des exemples adverses générés), l'augmentation des données avec des entrées perturbées ou des techniques d'optimisation robustes, sont mises en œuvre et ajustées pour les modèles pertinents en fonction de l'évaluation des risques.                                                                                                                                                                                                       |   3    | D/V  |
| 1.4.4 | Vérifiez que les étiquettes générées automatiquement (par exemple, via des modèles de langage de grande taille (LLMs) ou par supervision faible) sont soumises à des seuils de confiance et à des vérifications de cohérence afin de détecter des étiquettes hallucinées, trompeuses ou à faible niveau de confiance.                                                                                                                                                                                                                |   2    | D/V  |
| 1.4.5 | Vérifiez que les tests automatisés détectent les déséquilibres des étiquettes à chaque ingestion ou transformation de données significative.                                                                                                                                                                                                                                                                                                                                                                                         |   3    |  D   |

---

## C1.5 Lignée des données et traçabilité

Suivre l'intégralité du parcours de chaque point de données, de la source à l'entrée du modèle, pour l'auditabilité et la réponse aux incidents.

|   #   | description                                                                                                                                                                                                                                                                                      | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 1.5.1 | Vérifiez que la lignée de chaque point de données, y compris toutes les transformations, augmentations et fusions, est enregistrée et peut être reconstruite.                                                                                                                                    |   2    | D/V  |
| 1.5.2 | Vérifiez que les enregistrements de traçabilité sont immuables, stockés de manière sécurisée et accessibles pour les audits.                                                                                                                                                                     |   2    | D/V  |
| 1.5.3 | Vérifier que la traçabilité des données couvre les données synthétiques générées via des techniques de préservation de la vie privée ou génératives et que toutes les données synthétiques soient clairement étiquetées et distinguables des données réelles tout au long du flux de traitement. |   2    | D/V  |

---

## Références

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

