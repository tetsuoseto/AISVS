# 11 Protection de la vie privée et gestion des données personnelles

## Objectif de contrôle

Maintenir des garanties de confidentialité rigoureuses tout au long du cycle de vie de l'IA—collecte, entraînement, inférence et réponse aux incidents—afin que les données personnelles ne soient traitées qu'avec un consentement éclairé, une portée minimale nécessaire, un effacement vérifiable et des garanties de confidentialité formelles.

---

## 11.1 Anonymisation et minimisation des données

|   #    | description                                                                                                                                                          | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.1.1 | Vérifiez que les identifiants directs et quasi-identifiants sont supprimés et hachés.                                                                                |   1    | D/V  |
| 11.1.2 | Vérifiez que les audits automatisés mesurent la k-anonymité et l-diversité et alertent lorsque les seuils tombent en dessous de la politique.                        |   2    | D/V  |
| 11.1.3 | Vérifiez que les rapports d'importance des caractéristiques du modèle démontrent qu'il n'y a pas de fuite d'identifiants au-delà de ε = 0.01 d'information mutuelle. |   2    |  V   |
| 11.1.4 | Vérifiez que des preuves formelles ou une certification des données synthétiques montrent un risque de réidentification ≤ 0.05, même lors d’attaques de jonction.    |   3    |  V   |

---

## 11.2 Droit à l'oubli et mise en œuvre de la suppression

|   #    | description                                                                                                                                                                                                                                                                                                    | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.2.1 | Vérifiez que les demandes de suppression de données à caractère personnel se propagent vers les ensembles de données brutes, les points de contrôle, les représentations vectorielles, les journaux et les sauvegardes dans le cadre des accords de niveau de service dont la durée est inférieure à 30 jours. |   1    | D/V  |
| 11.2.2 | Vérifiez que les routines "machine-unlearning" réentraînent physiquement ou approximent la suppression en utilisant des algorithmes de désapprentissage certifiés.                                                                                                                                             |   2    |  D   |
| 11.2.3 | Vérifiez que l'évaluation du modèle fantôme prouve que les enregistrements oubliés influencent moins de 1% des sorties après le désapprentissage.                                                                                                                                                              |   2    |  V   |
| 11.2.4 | Vérifiez que les événements de suppression sont consignés de manière immuable et auditable pour les régulateurs.                                                                                                                                                                                               |   3    |  V   |

---

## 11.3 Garanties de confidentialité-différentielle

|   #    | description                                                                                                                                       | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.3.1 | Vérifiez que les tableaux de bord de comptabilité de la perte de confidentialité alertent lorsque ε cumulatif dépasse les seuils de la politique. |   2    | D/V  |
| 11.3.2 | Vérifiez que les audits de confidentialité en boîte noire estiment ε̂ dans une marge de 10% par rapport à la valeur déclarée.                     |   2    |  V   |
| 11.3.3 | Vérifiez que les preuves formelles couvrent tous les ajustements fins après l'entraînement et les représentations vectorielles.                   |   3    |  V   |

---

## 11.4 Limitation des objectifs et protection contre la dérive du périmètre

|   #    | description                                                                                                                                                             | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.4.1 | Vérifiez que chaque jeu de données et chaque point de contrôle du modèle portent une étiquette de finalité lisible par machine, alignée sur le consentement initial.    |   1    |  D   |
| 11.4.2 | Vérifiez que les moniteurs d'exécution détectent les requêtes incompatibles avec l'objectif déclaré et déclenchent un refus doux.                                       |   1    | D/V  |
| 11.4.3 | Vérifiez que les mécanismes de contrôle basés sur des politiques en tant que code bloquent le redéploiement des modèles vers de nouveaux domaines sans évaluation DPIA. |   3    |  D   |
| 11.4.4 | Vérifiez que les preuves de traçabilité formelles démontrent que chaque cycle de vie des données personnelles demeure dans la portée consentie.                         |   3    |  V   |

---

## 11.5 Gestion du consentement et traçage sur base légale

|   #    | description                                                                                                                                                | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.5.1 | Vérifiez qu'une plateforme de gestion des consentements (CMP) enregistre le statut d'opt-in, la finalité et la durée de conservation par sujet de données. |   1    | D/V  |
| 11.5.2 | Vérifiez que les API exposent des jetons de consentement; les modèles doivent valider la portée du jeton avant l’inférence.                                |   2    |  D   |
| 11.5.3 | Vérifiez que le consentement refusé ou retiré entraîne l’arrêt des pipelines de traitement dans les 24 heures.                                             |   2    | D/V  |

---

## 11.6 Apprentissage fédéré avec des contrôles de confidentialité

|   #    | description                                                                                                                             | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 11.6.1 | Vérifiez que les mises à jour côté client utilisent l’ajout de bruit de confidentialité différentielle locale avant l’agrégation.       |   1    |  D   |
| 11.6.2 | Vérifiez que les métriques d’entraînement respectent la confidentialité différentielle et ne révèlent jamais la perte d’un seul client. |   2    | D/V  |
| 11.6.3 | Vérifiez que l'agrégation résistante à l'empoisonnement (par exemple Krum/Trimmed-Mean) est activée.                                    |   2    |  V   |
| 11.6.4 | Vérifiez que les preuves formelles démontrent le budget ε global avec une perte d’utilité de moins de 5.                                |   3    |  V   |

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

