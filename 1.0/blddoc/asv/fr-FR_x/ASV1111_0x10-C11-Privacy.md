# 11 Protection de la vie privée et gestion des données personnelles

## Objectif de contrôle

Maintenir des garanties strictes de confidentialité tout au long du cycle de vie de l’IA — collecte, entraînement, inférence et réponse aux incidents — afin que les données personnelles ne soient traitées qu’avec un consentement clair, une portée minimale nécessaire, une suppression vérifiable et des garanties formelles de confidentialité.

---

## 11.1 Anonymisation et minimisation des données

|   #    | Description                                                                                                                                                                    | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 11.1.1 | Vérifiez que les identifiants directs et quasi-identifiants sont supprimés, hachés.                                                                                            |   1    | D/V  |
| 11.1.2 | Vérifiez que les audits automatisés mesurent la k-anonymat/l-diversité et alertent lorsque les seuils descendent en dessous de la politique.                                   |   2    | D/V  |
| 11.1.3 | Vérifiez que les rapports d'importance des caractéristiques du modèle prouvent qu'il n'y a pas de fuite d'identifiant au-delà de ε = 0,01 d'information mutuelle.              |   2    |  V   |
| 11.1.4 | Vérifiez que les preuves formelles ou la certification par données synthétiques montrent que le risque de ré-identification est ≤ 0,05 même en cas d'attaques par recoupement. |   3    |  V   |

---

## 11.2 Droit à l’oubli et application de la suppression

|   #    | Description                                                                                                                                                                                                                         | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.2.1 | Vérifiez que les demandes de suppression des données subjectives se propagent aux ensembles de données brutes, points de contrôle, embeddings, journaux et sauvegardes dans des accords de niveau de service inférieurs à 30 jours. |   1    | D/V  |
| 11.2.2 | Vérifiez que les routines de « machine-unlearning » réentraînent physiquement ou approximativement la suppression en utilisant des algorithmes d’effacement certifiés.                                                              |   2    |  D   |
| 11.2.3 | Vérifiez que l'évaluation par modèle-ombre prouve que les enregistrements oubliés influencent moins de 1 % des résultats après l'effacement.                                                                                        |   2    |  V   |
| 11.2.4 | Vérifiez que les événements de suppression sont enregistrés de manière immuable et auditables pour les régulateurs.                                                                                                                 |   3    |  V   |

---

## 11.3 Mesures de protection de la confidentialité différentielle

|   #    | Description                                                                                                                                         | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.3.1 | Vérifiez que les tableaux de bord de comptabilisation des pertes de confidentialité alertent lorsque le cumul ε dépasse les seuils de la politique. |   2    | D/V  |
| 11.3.2 | Vérifiez que les audits de confidentialité en boîte noire estiment ε̂ avec une précision de 10 % par rapport à la valeur déclarée.                  |   2    |  V   |
| 11.3.3 | Vérifiez que les preuves formelles couvrent tous les ajustements fins et incorporations post-formation.                                             |   3    |  V   |

---

## 11.4 Limitation de l'objectif et protection contre l'expansion non contrôlée du périmètre

|   #    | Description                                                                                                                                                | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.4.1 | Vérifiez que chaque ensemble de données et point de contrôle de modèle comporte une étiquette de but lisible par machine conforme au consentement initial. |   1    |  D   |
| 11.4.2 | Vérifiez que les moniteurs d'exécution détectent les requêtes incompatibles avec l'objectif déclaré et déclenchent un refus soft.                          |   1    | D/V  |
| 11.4.3 | Vérifiez que les contrôles de la politique en tant que code empêchent le redéploiement des modèles vers de nouveaux domaines sans examen DPIA.             |   3    |  D   |
| 11.4.4 | Vérifiez que les preuves formelles de traçabilité démontrent que chaque cycle de vie des données personnelles reste dans le cadre consenti.                |   3    |  V   |

---

## 11.5 Gestion du consentement et suivi basé sur une base légale

|   #    | Description                                                                                                                                                            | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.5.1 | Vérifiez qu'une plateforme de gestion du consentement (CMP) enregistre le statut d'acceptation, l'objectif et la période de conservation pour chaque sujet de données. |   1    | D/V  |
| 11.5.2 | Vérifiez que les API exposent les jetons de consentement ; les modèles doivent valider la portée du jeton avant l'inférence.                                           |   2    |  D   |
| 11.5.3 | Vérifiez que le consentement refusé ou retiré arrête les pipelines de traitement dans un délai de 24 heures.                                                           |   2    | D/V  |

---

## 11.6 Apprentissage Fédéré avec Contrôles de Confidentialité

|   #    | Description                                                                                                                  | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.6.1 | Vérifiez que les mises à jour client utilisent l'ajout de bruit de confidentialité différentielle locale avant l'agrégation. |   1    |  D   |
| 11.6.2 | Vérifiez que les métriques d'entraînement sont privées différentielles et ne révèlent jamais la perte d'un seul client.      |   2    | D/V  |
| 11.6.3 | Vérifiez que l'agrégation résistante au empoisonnement (par exemple, Krum/Moyenne Élaguée) est activée.                      |   2    |  V   |
| 11.6.4 | Vérifiez que les preuves formelles démontrent un budget global ε avec une perte d'utilité inférieure à 5.                    |   3    |  V   |

---

### Références

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

