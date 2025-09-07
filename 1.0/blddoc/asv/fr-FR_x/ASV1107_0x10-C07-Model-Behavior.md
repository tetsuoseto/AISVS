# Comportement du modèle C7, contrôle de la sortie et assurance de la sécurité

## Objectif de contrôle

Les sorties des modèles doivent être structurées, fiables, sécurisées, explicables et continuellement surveillées en production. Cela permet de réduire les hallucinations, les fuites de données personnelles, les contenus nuisibles et les actions incontrôlées, tout en augmentant la confiance des utilisateurs et la conformité réglementaire.

---

## C7.1 Application de la Norme de Format de Sortie

Les schémas stricts, le décodage contraint et la validation descendante empêchent le contenu malformé ou malveillant de se propager.

|   #   | Description                                                                                                                                                                                                               | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.1.1 | Vérifiez que les schémas de réponse (par exemple, le schéma JSON) sont fournis dans l'invite système et que chaque sortie est automatiquement validée ; les sorties non conformes déclenchent une réparation ou un rejet. |   1    | D/V  |
| 7.1.2 | Vérifiez que le décodage contraint (tokens d'arrêt, expressions régulières, nombre maximal de tokens) est activé pour empêcher tout débordement ou canal secondaire d'injection dans le prompt.                           |   1    | D/V  |
| 7.1.3 | Vérifiez que les composants en aval considèrent les sorties comme non fiables et les valident selon des schémas ou des déserialiseurs sûrs contre les injections.                                                         |   2    | D/V  |
| 7.1.4 | Vérifiez que les événements de sortie incorrecte sont enregistrés, soumis à une limitation de débit et remontés au système de surveillance.                                                                               |   3    |  V   |

---

## C7.2 Détection et atténuation des hallucinations

L'estimation de l'incertitude et les stratégies de secours limitent les réponses fabriquées.

|   #   | Description                                                                                                                                                                                              | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.2.1 | Vérifiez que les log-probabilités au niveau des jetons, la self-consistency en ensemble, ou les détecteurs d'hallucinations affinés attribuent un score de confiance à chaque réponse.                   |   1    | D/V  |
| 7.2.2 | Vérifiez que les réponses en dessous d'un seuil de confiance configurable déclenchent des workflows de secours (par exemple, génération augmentée par récupération, modèle secondaire ou revue humaine). |   1    | D/V  |
| 7.2.3 | Vérifiez que les incidents d’hallucination sont étiquetés avec des métadonnées de cause racine et alimentés dans les pipelines de post-mortem et de fine-tuning.                                         |   2    | D/V  |
| 7.2.4 | Vérifiez que les seuils et les détecteurs sont recalibrés après des mises à jour majeures du modèle ou de la base de connaissances.                                                                      |   3    | D/V  |
| 7.2.5 | Vérifiez que les visualisations du tableau de bord suivent les taux d'hallucination.                                                                                                                     |   3    |  V   |

---

## C7.3 Filtrage de sécurité et de confidentialité des sorties

Les filtres de politique et la couverture en équipe rouge protègent les utilisateurs et les données confidentielles.

|   #   | Description                                                                                                                                                                                                                                             | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.3.1 | Vérifiez que les classificateurs pré- et post-génération bloquent les contenus haineux, les harcèlements, les automutilations, les contenus extrémistes et sexuellement explicites conformes à la politique.                                            |   1    | D/V  |
| 7.3.2 | Vérifiez que la détection des données personnelles identifiables (PII) et des informations de carte de paiement (PCI) ainsi que la rédaction automatique sont effectuées sur chaque réponse ; les violations entraînent un incident de confidentialité. |   1    | D/V  |
| 7.3.3 | Vérifiez que les étiquettes de confidentialité (par exemple, secrets commerciaux) se propagent à travers les modalités afin d’éviter toute fuite dans le texte, les images ou le code.                                                                  |   2    |  D   |
| 7.3.4 | Vérifiez que les tentatives de contournement du filtre ou les classifications à haut risque nécessitent une approbation secondaire ou une ré-authentification de l'utilisateur.                                                                         |   3    | D/V  |
| 7.3.5 | Vérifiez que les seuils de filtrage reflètent les juridictions légales ainsi que le contexte d'âge/rôle de l'utilisateur.                                                                                                                               |   3    | D/V  |

---

## C7.4 Limitation des sorties et des actions

Les limites de débit et les barrières d'approbation empêchent les abus et une autonomie excessive.

|   #   | Description                                                                                                                                                                                              | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.4.1 | Vérifiez que les quotas par utilisateur et par clé API limitent les requêtes, les jetons et les coûts avec un retour en arrière exponentiel en cas d'erreurs 429.                                        |   1    |  D   |
| 7.4.2 | Vérifiez que les actions privilégiées (écriture de fichiers, exécution de code, appels réseau) nécessitent une approbation basée sur une politique ou une intervention humaine.                          |   1    | D/V  |
| 7.4.3 | Vérifiez que les contrôles de cohérence intermodale garantissent que les images, le code et le texte générés pour la même demande ne peuvent pas être utilisés pour faire passer du contenu malveillant. |   2    | D/V  |
| 7.4.4 | Vérifiez que la profondeur de délégation des agents, les limites de récursion et les listes d'outils autorisés sont explicitement configurées.                                                           |   2    |  D   |
| 7.4.5 | Vérifiez que la violation des limites génère des événements de sécurité structurés pour l’ingestion par SIEM.                                                                                            |   3    |  V   |

---

## C7.5 Explicabilité de la sortie

Les signaux transparents améliorent la confiance des utilisateurs et le débogage interne.

|   #   | Description                                                                                                                                                                 | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.5.1 | Vérifiez que les scores de confiance destinés à l'utilisateur ou les résumés succincts des raisonnements sont présentés lorsque l'évaluation des risques le juge approprié. |   2    | D/V  |
| 7.5.2 | Vérifiez que les explications générées évitent de révéler des invites système sensibles ou des données propriétaires.                                                       |   2    | D/V  |
| 7.5.3 | Vérifiez que le système capture les log-probabilités au niveau des tokens ou les cartes d'attention et les stocke pour une inspection autorisée.                            |   3    |  D   |
| 7.5.4 | Vérifiez que les artefacts d'explicabilité sont contrôlés par version en même temps que les versions du modèle pour garantir leur auditabilité.                             |   3    |  V   |

---

## C7.6 Intégration de la Surveillance

L'observabilité en temps réel boucle la boucle entre le développement et la production.

|   #   | Description                                                                                                                                                                                                            | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.6.1 | Vérifiez que les métriques (violations de schéma, taux d'hallucination, toxicité, fuites d'Informations Identifiables Personnellement (PII), latence, coût) sont transmises à une plateforme centrale de surveillance. |   1    |  D   |
| 7.6.2 | Vérifiez que des seuils d'alerte sont définis pour chaque indicateur de sécurité, avec des voies d'escalade pour l'astreinte.                                                                                          |   1    |  V   |
| 7.6.3 | Vérifiez que les tableaux de bord corrèlent les anomalies de sortie avec le modèle/version, le drapeau de fonctionnalité et les modifications des données en amont.                                                    |   2    |  V   |
| 7.6.4 | Vérifiez que les données de surveillance sont réintégrées dans le processus de réentraînement, d'ajustement fin ou de mise à jour des règles au sein d'un flux de travail MLOps documenté.                             |   2    | D/V  |
| 7.6.5 | Vérifiez que les pipelines de surveillance sont soumis à des tests de pénétration et contrôlés en termes d'accès afin d'éviter la fuite de journaux sensibles.                                                         |   3    |  V   |

---

## 7.7 Mesures de protection des médias génératifs

Veiller à ce que les systèmes d'IA ne génèrent pas de contenu média illégal, nuisible ou non autorisé en appliquant des contraintes politiques, une validation des sorties et une traçabilité.

|   #   | Description                                                                                                                                                                                                                                         | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.7.1 | Vérifiez que les invites système et les instructions utilisateur interdisent explicitement la génération de médias deepfake illégaux, nuisibles ou non consensuels (par exemple, image, vidéo, audio).                                              |   1    | D/V  |
| 7.7.2 | Vérifiez que les invites sont filtrées pour empêcher les tentatives de génération d'usurpations d'identité, de deepfakes à caractère sexuel explicite ou de médias représentant des personnes réelles sans consentement.                            |   2    | D/V  |
| 7.7.3 | Vérifiez que le système utilise le hachage perceptuel, la détection de filigrane ou l'empreinte digitale pour empêcher la reproduction non autorisée de médias protégés par des droits d'auteur.                                                    |   2    |  V   |
| 7.7.4 | Vérifiez que tous les médias générés sont signés cryptographiquement, marqués par filigrane, ou intégrés avec des métadonnées de provenance résistantes à la falsification pour assurer une traçabilité en aval.                                    |   3    | D/V  |
| 7.7.5 | Vérifiez que les tentatives de contournement (par exemple, l’obfuscation des instructions, l’argot, les formulations adverses) sont détectées, enregistrées et limitées en fréquence ; les abus répétés sont signalés aux systèmes de surveillance. |   3    |  V   |

## Références

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

