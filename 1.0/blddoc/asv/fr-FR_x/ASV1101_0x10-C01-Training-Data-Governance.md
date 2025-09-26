# Gouvernance des données de formation C1 et gestion des biais

## Objectif de contrôle

Les données d'entraînement doivent être obtenues, manipulées et maintenues de manière à préserver la provenance, la sécurité, la qualité et l'équité. Cela permet de respecter les obligations légales et de réduire les risques de biais, d'empoisonnement ou de violations de la vie privée qui pourraient survenir lors de la formation et affecter l'ensemble du cycle de vie de l'IA.

---

## C1.1 Provenance des données d'entraînement

Maintenez un inventaire vérifiable de tous les ensembles de données, n'acceptez que des sources fiables et consignez chaque modification pour garantir l'auditabilité.

|   #   | Description                                                                                                                                                                                                                                             | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 1.1.1 | Vérifiez qu'un inventaire à jour de chaque source de données d'entraînement (origine, gestionnaire/propriétaire, licence, méthode de collecte, contraintes d'utilisation prévues et historique de traitement) est maintenu.                             |   1    | D/V  |
| 1.1.2 | Vérifiez que les processus de préparation des données d’entraînement excluent les caractéristiques, attributs ou champs inutiles (par exemple, les métadonnées non utilisées, les informations personnelles sensibles, les données de test divulguées). |   1    | D/V  |
| 1.1.3 | Vérifiez que toutes les modifications du jeu de données sont soumises à un processus d'approbation consigné.                                                                                                                                            |   2    | D/V  |
| 1.1.4 | Vérifiez que les ensembles de données ou les sous-ensembles sont marqués par un filigrane ou empreint d'empreintes digitales lorsque cela est possible.                                                                                                 |   3    | D/V  |

---

## C1.2 Sécurité et intégrité des données d'entraînement

Restreindre l'accès aux données d'entraînement, les chiffrer au repos et en transit, et valider leur intégrité pour prévenir toute falsification, vol ou empoisonnement des données.

|   #   | Description                                                                                                                                                                                                                    | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 1.2.1 | Vérifiez que les contrôles d'accès protègent le stockage des données d'entraînement et les pipelines.                                                                                                                          |   1    | D/V  |
| 1.2.2 | Vérifiez que tous les accès aux données d'entraînement sont enregistrés, y compris l'utilisateur, l'heure et l'action.                                                                                                         |   2    | D/V  |
| 1.2.3 | Vérifiez que les ensembles de données d'entraînement sont chiffrés lors de leur transfert et au repos, en utilisant des algorithmes cryptographiques et des pratiques de gestion des clés conformes aux normes de l'industrie. |   2    | D/V  |
| 1.2.4 | Vérifiez que des hachages cryptographiques ou des signatures numériques sont utilisés pour garantir l'intégrité des données lors du stockage et du transfert des données d'entraînement.                                       |   2    | D/V  |
| 1.2.5 | Vérifiez que des techniques de détection automatisées sont appliquées pour protéger contre les modifications non autorisées ou la corruption des données d'entraînement.                                                       |   2    | D/V  |
| 1.2.6 | Vérifiez que les données d'entraînement obsolètes sont supprimées en toute sécurité ou anonymisées.                                                                                                                            |   2    | D/V  |
| 1.2.7 | Vérifiez que toutes les versions des ensembles de données d'entraînement sont identifiées de manière unique, stockées de façon immuable et auditables afin de permettre la restauration et l'analyse médico-légale.            |   3    | D/V  |

---

## C1.3 Qualité, intégrité et sécurité de l'étiquetage des données d'entraînement

Protéger les étiquettes et exiger une révision technique pour les données critiques.

|   #   | Description                                                                                                                                                                                                                                   | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 1.3.1 | Vérifiez que les hachages cryptographiques ou les signatures numériques sont appliqués aux artefacts d'étiquette afin d'assurer leur intégrité et leur authenticité.                                                                          |   2    | D/V  |
| 1.3.2 | Vérifiez que les interfaces et plateformes d'étiquetage appliquent des contrôles d'accès stricts, maintiennent des journaux d'audit infalsifiables de toutes les activités d'étiquetage et protègent contre les modifications non autorisées. |   2    | D/V  |
| 1.3.3 | Vérifiez que les informations sensibles dans les étiquettes sont supprimées, anonymisées ou cryptées au niveau du champ de données, au repos et en transit.                                                                                   |   3    | D/V  |

---

## C1.4 Qualité des données d'entraînement et garantie de sécurité

Combinez la validation automatisée, les contrôles manuels ponctuels et la correction enregistrée pour garantir la fiabilité des ensembles de données.

|   #   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 1.4.1 | Vérifiez que les tests automatisés détectent les erreurs de format et les valeurs nulles à chaque ingestion ou transformation de données importante.                                                                                                                                                                                                                                                                                                                                                                                   |   1    |  D   |
| 1.4.2 | Vérifiez que les pipelines de formation et de fine-tuning des LLM mettent en œuvre la détection d’empoisonnement et la validation de l’intégrité des données (par exemple, méthodes statistiques, détection des valeurs aberrantes, analyse d'empreintes) afin d’identifier les attaques potentielles d’empoisonnement (par exemple, inversion d’étiquettes, insertion de déclencheurs de porte dérobée, commandes de changement de rôle, attaques par instances influentes) ou la corruption accidentelle des données d’entraînement. |   2    | D/V  |
| 1.4.3 | Vérifiez que les étiquettes générées automatiquement (par exemple, via des LLM ou une supervision faible) sont soumises à des seuils de confiance et à des contrôles de cohérence pour détecter les étiquettes hallucinées, trompeuses ou à faible confiance.                                                                                                                                                                                                                                                                          |   2    | D/V  |
| 1.4.4 | Vérifiez que des défenses appropriées, telles que l'entraînement adversarial (en utilisant des exemples adversariaux générés), l'augmentation de données avec des entrées perturbées, ou des techniques d'optimisation robuste, sont mises en œuvre et ajustées pour les modèles concernés en fonction de l'évaluation des risques.                                                                                                                                                                                                    |   3    | D/V  |
| 1.4.5 | Vérifiez que les tests automatisés détectent les décalages d'étiquettes à chaque ingestion ou transformation de données significative.                                                                                                                                                                                                                                                                                                                                                                                                 |   3    |  D   |

---

## C1.5 Traçabilité et origine des données

Suivez le parcours complet de chaque point de données depuis la source jusqu'à l'entrée du modèle pour assurer la traçabilité et la réponse aux incidents.

|   #   | Description                                                                                                                                                                                                                                                                     | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 1.5.1 | Vérifiez que la lignée de chaque point de données, y compris toutes les transformations, augmentations et fusions, est enregistrée et peut être reconstruite.                                                                                                                   |   2    | D/V  |
| 1.5.2 | Vérifiez que les enregistrements de lignée sont immuables, stockés de manière sécurisée et accessibles pour les audits.                                                                                                                                                         |   2    | D/V  |
| 1.5.3 | Vérifiez que le suivi de la lignée couvre les données synthétiques générées via des techniques de préservation de la vie privée ou génératives et que toutes les données synthétiques sont clairement étiquetées et distinguables des données réelles tout au long du pipeline. |   2    | D/V  |

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

