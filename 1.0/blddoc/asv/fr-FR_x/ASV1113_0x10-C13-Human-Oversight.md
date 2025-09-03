# C13 Supervision humaine, responsabilité et gouvernance

## Objectif de contrôle

Ce chapitre fournit les exigences relatives au maintien d'une supervision humaine et de chaînes de reddition de comptes claires dans les systèmes d'IA, garantissant l'explicabilité, la transparence et une gouvernance éthique tout au long du cycle de vie de l'IA.

---

## C13.1 Interrupteur d'arrêt d'urgence et mécanismes de contournement

Fournir des mécanismes d'arrêt ou de restauration lorsque des comportements dangereux du système d'IA sont observés.

|   #    | description                                                                                                                                | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 13.1.1 | Vérifiez qu'un mécanisme d'arrêt manuel existe pour interrompre immédiatement l'inférence du modèle d'IA et ses sorties.                   |   1    | D/V  |
| 13.1.2 | Vérifiez que les contrôles d'override ne soient accessibles qu'au personnel autorisé.                                                      |   1    |  D   |
| 13.1.3 | Vérifiez que les procédures de rollback permettent de revenir à des versions antérieures du modèle ou à des opérations en mode sans échec. |   3    | D/V  |
| 13.1.4 | Vérifiez que les mécanismes de contournement sont testés régulièrement.                                                                    |   3    |  V   |

---

## C13.2 Points de contrôle de décision avec Human-in-the-Loop

Exiger des approbations humaines lorsque les enjeux dépassent des seuils de risque prédéfinis.

|   #    | description                                                                                                                                                     | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 13.2.1 | Vérifiez que les décisions d'IA à haut risque nécessitent une approbation explicite de la part d'un être humain avant leur exécution.                           |   1    | D/V  |
| 13.2.2 | Vérifiez que les seuils de risque sont clairement définis et déclenchent automatiquement les flux de travail de révision humaine.                               |   1    |  D   |
| 13.2.3 | Vérifiez que les décisions sensibles au temps disposent de procédures de repli lorsque l'approbation humaine ne peut pas être obtenue dans les délais impartis. |   2    |  D   |
| 13.2.4 | Vérifiez que les procédures d'escalade définissent des niveaux d'autorité clairs pour différents types de décisions ou catégories de risques, le cas échéant.   |   3    | D/V  |

---

## C13.3 Chaîne de responsabilité et auditabilité

Consigner les actions de l’opérateur et les décisions du modèle.

|   #    | description                                                                                                                                                                             | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 13.3.1 | Vérifiez que toutes les décisions du système d'IA et les interventions humaines sont consignées avec des horodatages, des identités des utilisateurs et la justification des décisions. |   1    | D/V  |
| 13.3.2 | Vérifiez que les journaux d'audit ne puissent pas être altérés et incluez des mécanismes de vérification de l'intégrité.                                                                |   2    |  D   |

---

## C13.4 Techniques d'IA explicables

Importance des caractéristiques de surface, contre-factuels et explications locales.

|   #    | description                                                                                                                                                                                  | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 13.4.1 | Vérifiez que les systèmes d'IA fournissent des explications de base sur leurs décisions dans un format lisible par l'homme.                                                                  |   1    | D/V  |
| 13.4.2 | Vérifiez que la qualité des explications est validée par des études d'évaluation humaine et par des métriques.                                                                               |   2    |  V   |
| 13.4.3 | Vérifiez que les scores d'importance des caractéristiques ou les méthodes d'attribution (SHAP, LIME, etc.) sont disponibles pour les décisions critiques.                                    |   3    | D/V  |
| 13.4.4 | Vérifiez que les explications contrefactuelles montrent comment les entrées pourraient être modifiées pour changer les résultats, si cela est applicable au cas d'utilisation et au domaine. |   3    |  V   |

---

## C13.5 Cartes de modèle et divulgations d'utilisation

Maintenez les cartes de modèle pour l'utilisation prévue, les métriques de performance et les considérations éthiques.

|   #    | description                                                                                                                                                                                                                                      | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 13.5.1 | Vérifiez que les fiches de modèle documentent les cas d'utilisation prévus, les limites et les modes de défaillance connus.                                                                                                                      |   1    |  D   |
| 13.5.2 | Vérifiez que les métriques de performance pour les différents cas d'utilisation applicables sont divulguées.                                                                                                                                     |   1    | D/V  |
| 13.5.3 | Vérifiez que les considérations éthiques, les évaluations des biais, les évaluations d'équité, les caractéristiques des données d'entraînement et les limites connues des données d'entraînement sont documentées et mises à jour régulièrement. |   2    |  D   |
| 13.5.4 | Vérifiez que les fiches de modèle sont sous contrôle de version et maintenues tout au long du cycle de vie du modèle, avec le suivi des modifications.                                                                                           |   2    | D/V  |

---

## C13.6 Quantification de l'incertitude

Propager les scores de confiance ou les mesures d'entropie dans les réponses.

|   #    | description                                                                                                                       | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 13.6.1 | Vérifiez que les systèmes d'IA fournissent des scores de confiance ou des mesures d'incertitude avec leurs sorties.               |   1    |  D   |
| 13.6.2 | Vérifiez que les seuils d'incertitude déclenchent une révision humaine supplémentaire ou des voies de décision alternatives.      |   2    | D/V  |
| 13.6.3 | Vérifiez que les méthodes de quantification de l'incertitude sont calibrées et validées par rapport aux données de vérité au sol. |   2    |  V   |
| 13.6.4 | Vérifier que la propagation de l'incertitude est maintenue tout au long des flux de travail d'IA en plusieurs étapes.             |   3    | D/V  |

---

## C13.7 Rapports de transparence destinés à l'utilisateur

Fournir des divulgations périodiques concernant les incidents, la dérive et l’utilisation des données.

|   #    | description                                                                                                                                                                 | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 13.7.1 | Vérifiez que les politiques d'utilisation des données et les pratiques de gestion du consentement des utilisateurs sont clairement communiquées aux parties prenantes.      |   1    | D/V  |
| 13.7.2 | Vérifiez que les évaluations d'impact de l'IA sont réalisées et que les résultats sont inclus dans le rapport.                                                              |   2    | D/V  |
| 13.7.3 | Vérifiez que les rapports de transparence publiés régulièrement divulguent les incidents liés à l'IA et les métriques opérationnelles avec un niveau de détail raisonnable. |   2    | D/V  |

### Références

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

