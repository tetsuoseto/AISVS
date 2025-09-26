# Comportement du modèle C7, contrôle de la sortie et assurance de sécurité

## Objectif de contrôle

Les sorties des modèles doivent être structurées, fiables, sûres, explicables et continuellement surveillées en production. Cela permet de réduire les hallucinations, les fuites de données privées, les contenus nuisibles et les actions incontrôlées, tout en augmentant la confiance des utilisateurs et la conformité réglementaire.

---

## C7.1 Application des règles du format de sortie

Les schémas stricts, le décodage contraint et la validation en aval empêchent le contenu malformé ou malveillant de se propager.

|   #   | Description                                                                                                                                                                                                            | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.1.1 | Vérifiez que les schémas de réponse (par exemple, JSON Schema) sont fournis dans l'invite système et que chaque sortie est automatiquement validée ; les sorties non conformes déclenchent une réparation ou un rejet. |   1    | D/V  |
| 7.1.2 | Vérifiez que le décodage contraint (tokens d'arrêt, regex, max-tokens) est activé pour éviter les débordements ou les canaux secondaires d'injection de prompt.                                                        |   1    | D/V  |
| 7.1.3 | Vérifiez que les composants en aval considèrent les sorties comme non fiables et les valident selon des schémas ou des désérialiseurs sécurisés contre les injections.                                                 |   2    | D/V  |
| 7.1.4 | Vérifiez que les événements de sortie incorrecte sont enregistrés, soumis à un contrôle de débit et affichés dans la surveillance.                                                                                     |   3    |  V   |

---

## C7.2 Détection et atténuation des hallucinations

L'estimation de l'incertitude et les stratégies de repli limitent les réponses fabriquées.

|   #   | Description                                                                                                                                                                                                     | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.2.1 | Vérifiez que les log-probabilités au niveau des tokens, la self-consistance ensembliste ou les détecteurs d'hallucination affinés attribuent un score de confiance à chaque réponse.                            |   1    | D/V  |
| 7.2.2 | Vérifiez que les réponses en dessous d’un seuil de confiance configurable déclenchent des flux de travail de repli (par exemple, génération augmentée par récupération, modèle secondaire ou révision humaine). |   1    | D/V  |
| 7.2.3 | Vérifiez que les incidents d'hallucination sont étiquetés avec des métadonnées de cause profonde et envoyés aux pipelines d'analyse post-mortem et de réglage fin.                                              |   2    | D/V  |
| 7.2.4 | Vérifiez que les seuils et les détecteurs sont recalibrés après des mises à jour majeures du modèle ou de la base de connaissances.                                                                             |   3    | D/V  |
| 7.2.5 | Vérifiez que les visualisations du tableau de bord suivent les taux d'hallucination.                                                                                                                            |   3    |  V   |

---

## C7.3 Filtrage de la sécurité et de la confidentialité des sorties

Les filtres de politique et la couverture de l'équipe rouge protègent les utilisateurs et les données confidentielles.

|   #   | Description                                                                                                                                                                              | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.3.1 | Vérifiez que les classificateurs pré et post-génération bloquent les contenus haineux, harcelants, d’automutilation, extrémistes et sexuellement explicites conformément à la politique. |   1    | D/V  |
| 7.3.2 | Vérifiez que la détection de PII/PCI et la rédaction automatique s’exécutent sur chaque réponse ; les violations entraînent un incident de confidentialité.                              |   1    | D/V  |
| 7.3.3 | Vérifiez que les étiquettes de confidentialité (par exemple, secrets commerciaux) se propagent à travers les modalités afin d'empêcher toute fuite dans le texte, les images ou le code. |   2    |  D   |
| 7.3.4 | Vérifiez que les tentatives de contournement du filtre ou les classifications à haut risque nécessitent une approbation secondaire ou une réauthentification de l'utilisateur.           |   3    | D/V  |
| 7.3.5 | Vérifiez que les seuils de filtrage reflètent les juridictions légales ainsi que le contexte d'âge/rôle de l'utilisateur.                                                                |   3    | D/V  |

---

## C7.4 Limitation de la sortie et des actions

Les limites de fréquence et les portes d'approbation empêchent les abus et l'autonomie excessive.

|   #   | Description                                                                                                                                                                                             | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.4.1 | Vérifiez que les quotas par utilisateur et par clé API limitent les requêtes, les jetons et le coût avec un retour en arrière exponentiel en cas d'erreurs 429.                                         |   1    |  D   |
| 7.4.2 | Vérifiez que les actions privilégiées (écriture de fichiers, exécution de code, appels réseau) nécessitent une approbation basée sur une politique ou une intervention humaine.                         |   1    | D/V  |
| 7.4.3 | Vérifiez que les contrôles de cohérence cross-modaux garantissent que les images, le code et le texte générés pour la même demande ne peuvent pas être utilisés pour dissimuler du contenu malveillant. |   2    | D/V  |
| 7.4.4 | Vérifiez que la profondeur de délégation des agents, les limites de récursion et les listes d'outils autorisés sont configurées explicitement.                                                          |   2    |  D   |
| 7.4.5 | Vérifiez que la violation des limites génère des événements de sécurité structurés pour l'ingestion SIEM.                                                                                               |   3    |  V   |

---

## C7.5 Explicabilité de la sortie

Les signaux transparents améliorent la confiance des utilisateurs et le débogage interne.

|   #   | Description                                                                                                                                                         | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.5.1 | Vérifiez que les scores de confiance destinés à l'utilisateur ou les résumés brefs de raisonnement sont exposés lorsque l'évaluation des risques le juge approprié. |   2    | D/V  |
| 7.5.2 | Vérifiez que les explications générées évitent de révéler des invites système sensibles ou des données propriétaires.                                               |   2    | D/V  |
| 7.5.3 | Vérifiez que le système capture les log-probabilités au niveau des tokens ou les cartes d’attention et les stocke pour une inspection autorisée.                    |   3    |  D   |
| 7.5.4 | Vérifiez que les artefacts d'explicabilité sont contrôlés en version parallèlement aux versions du modèle pour garantir leur auditabilité.                          |   3    |  V   |

---

## C7.6 Intégration de la surveillance

L'observabilité en temps réel ferme la boucle entre le développement et la production.

|   #   | Description                                                                                                                                                                           | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.6.1 | Vérifiez que les métriques (violations du schéma, taux d'hallucination, toxicité, fuites d'IPI, latence, coût) sont transmises à une plateforme centrale de surveillance.             |   1    |  D   |
| 7.6.2 | Vérifiez que des seuils d'alerte sont définis pour chaque métrique de sécurité, avec des voies d'escalade en astreinte.                                                               |   1    |  V   |
| 7.6.3 | Vérifiez que les tableaux de bord corrèlent les anomalies de sortie avec le modèle/version, le drapeau de fonctionnalité et les modifications des données en amont.                   |   2    |  V   |
| 7.6.4 | Vérifiez que les données de surveillance sont réinjectées dans le processus de réentraînement, d’ajustement fin ou de mise à jour des règles dans un flux de travail MLOps documenté. |   2    | D/V  |
| 7.6.5 | Vérifiez que les pipelines de surveillance sont soumis à des tests de pénétration et contrôlés par accès afin d'éviter la fuite de journaux sensibles.                                |   3    |  V   |

---

## 7.7 Mesures de protection des médias génératifs

Assurez-vous que les systèmes d'IA ne génèrent pas de contenu médiatique illégal, nuisible ou non autorisé en appliquant des contraintes politiques, une validation des sorties et une traçabilité.

|   #   | Description                                                                                                                                                                                                                                                          | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.7.1 | Vérifiez que les invites système et les instructions utilisateur interdisent explicitement la génération de médias deepfake illégaux, nuisibles ou non consensuels (par exemple, image, vidéo, audio).                                                               |   1    | D/V  |
| 7.7.2 | Vérifiez que les invites sont filtrées pour détecter les tentatives de génération d'usurpations d'identité, de deepfakes à caractère sexuel explicite ou de médias représentant de véritables individus sans consentement.                                           |   2    | D/V  |
| 7.7.3 | Vérifiez que le système utilise le hachage perceptuel, la détection de filigrane ou l’empreinte digitale pour empêcher la reproduction non autorisée de médias protégés par des droits d’auteur.                                                                     |   2    |  V   |
| 7.7.4 | Vérifiez que tous les médias générés sont signés cryptographiquement, filigranés ou intégrés avec des métadonnées de provenance résistantes à la falsification pour une traçabilité en aval.                                                                         |   3    | D/V  |
| 7.7.5 | Vérifiez que les tentatives de contournement (par exemple, l’obscurcissement des invites, l’argot, les formulations adversariales) sont détectées, enregistrées et soumises à une limitation de débit ; les abus répétés sont signalés aux systèmes de surveillance. |   3    |  V   |

## Références

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

