# C7 Comportement du modèle, Contrôle de sortie et Assurance de sécurité

## Objectif de contrôle

Les sorties du modèle doivent être structurées, fiables, sûres, explicables et surveillées en continu en production. Ce faisant, cela réduit les hallucinations, les fuites de données personnelles, le contenu nuisible et les actions hors de contrôle, tout en renforçant la confiance des utilisateurs et la conformité réglementaire.

---

## C7.1 Application du format de sortie

Des schémas stricts, un décodage contraint et une validation en aval empêchent le contenu malformé ou malveillant de se propager.

|   #   | description                                                                                                                                                                                                        | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 7.1.1 | Vérifiez que les schémas de réponse (par exemple, le schéma JSON) sont fournis dans l'invite système et que chaque sortie est automatiquement vérifiée; les sorties non conformes déclenchent réparation ou rejet. |   1    | D/V  |
| 7.1.2 | Vérifiez que le décodage sous contraintes (jetons d'arrêt, expressions régulières, max-tokens) est activé pour prévenir le débordement ou les canaux d'injection de prompt.                                        |   1    | D/V  |
| 7.1.3 | Vérifiez que les composants en aval traitent les sorties comme non fiables et les valident selon des schémas ou des désérialiseurs sûrs contre les injections.                                                     |   2    | D/V  |
| 7.1.4 | Vérifiez que les événements de sortie inappropriés sont enregistrés, limités en débit et remontés vers le système de surveillance.                                                                                 |   3    |  V   |

---

## C7.2 Détection et atténuation des hallucinations

L'estimation de l'incertitude et les stratégies de repli permettent de limiter les réponses fabriquées.

|   #   | description                                                                                                                                                                                                       | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.2.1 | Vérifiez que les log-probabilités au niveau des jetons, la cohérence d'ensemble ou les détecteurs d'hallucination finement ajustés attribuent un score de confiance à chaque réponse.                             |   1    | D/V  |
| 7.2.2 | Vérifiez que les réponses en dessous d'un seuil de confiance configurable déclenchent des flux de travail de secours (par exemple, génération augmentée par récupération, modèle secondaire ou révision humaine). |   1    | D/V  |
| 7.2.3 | Vérifiez que les incidents d'hallucination sont étiquetés avec des métadonnées de cause racine et acheminés vers les pipelines de post-mortem et de finetuning.                                                   |   2    | D/V  |
| 7.2.4 | Vérifiez que les seuils et les détecteurs sont recalibrés après les mises à jour majeures du modèle ou de la base de connaissances.                                                                               |   3    | D/V  |
| 7.2.5 | Vérifiez que les visualisations du tableau de bord suivent les taux d'hallucination.                                                                                                                              |   3    |  V   |

---

## C7.3 Filtrage de la sécurité et de la confidentialité des sorties

Les filtres de politique et la couverture par l'équipe rouge protègent les utilisateurs et les données confidentielles.

|   #   | description                                                                                                                                                                                                                | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.3.1 | Vérifiez que les classificateurs pré-génération et post-génération bloquent le contenu haineux, le harcèlement, l'automutilation, le contenu extrémiste et le contenu sexuellement explicite, conformément à la politique. |   1    | D/V  |
| 7.3.2 | Vérifiez que la détection PII/PCI et la rédaction automatique s'exécutent sur chaque réponse; les violations provoquent un incident de confidentialité.                                                                    |   1    | D/V  |
| 7.3.3 | Vérifiez que les étiquettes de confidentialité se propagent à travers les modalités afin d'éviter les fuites dans le texte, les images ou le code.                                                                         |   2    |  D   |
| 7.3.4 | Vérifiez que les tentatives de contournement du filtre ou les classifications à haut risque nécessitent une approbation secondaire ou une réauthentification de l'utilisateur.                                             |   3    | D/V  |
| 7.3.5 | Vérifiez que les seuils de filtrage reflètent les juridictions légales et le contexte d'âge et de rôle de l'utilisateur.                                                                                                   |   3    | D/V  |

---

## C7.4 Sortie et limitation des actions

Les limites de débit et les portes d'approbation empêchent les abus et l'autonomie excessive.

|   #   | description                                                                                                                                                                                               | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.4.1 | Vérifiez que les quotas par utilisateur et par clé API limitent les requêtes, les jetons et le coût avec une temporisation exponentielle en cas d'erreurs 429.                                            |   1    |  D   |
| 7.4.2 | Vérifiez que les actions privilégiées (écritures de fichiers, exécution de code, appels réseau) nécessitent une approbation basée sur une politique ou une intervention humaine dans la boucle.           |   1    | D/V  |
| 7.4.3 | Vérifiez que les contrôles de cohérence intermodaux garantissent que les images, le code et le texte générés pour la même requête ne puissent pas être utilisés pour faire passer du contenu malveillant. |   2    | D/V  |
| 7.4.4 | Vérifiez que la profondeur de délégation de l'agent, les limites de récursion et les listes d'outils autorisés soient explicitement configurés.                                                           |   2    |  D   |
| 7.4.5 | Vérifiez que la violation des limites émet des événements de sécurité structurés pour l'ingestion dans le SIEM.                                                                                           |   3    |  V   |

---

## C7.5 Explicabilité des sorties

Des signaux transparents améliorent la confiance des utilisateurs et facilitent le débogage interne.

|   #   | description                                                                                                                                                                 | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.5.1 | Vérifiez que les scores de confiance affichés à l'utilisateur ou les résumés de raisonnement succincts sont affichés lorsque l'évaluation des risques est jugée appropriée. |   2    | D/V  |
| 7.5.2 | Vérifiez que les explications générées ne révèlent pas d'invites système sensibles ou des données propriétaires.                                                            |   2    | D/V  |
| 7.5.3 | Vérifiez que le système capture les log-probabilités au niveau des jetons ou les cartes d'attention et les stocke pour un examen autorisé.                                  |   3    |  D   |
| 7.5.4 | Vérifiez que les artefacts d'explicabilité sont versionnés parallèlement aux versions des modèles pour l'auditabilité.                                                      |   3    |  V   |

---

## C7.6 Intégration de la surveillance

L'observabilité en temps réel ferme la boucle entre le développement et la production.

|   #   | description                                                                                                                                                                                                            | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.6.1 | Vérifiez que les métriques (violations de schéma, taux d'hallucination, toxicité, fuites d'informations personnellement identifiables (PII), latence, coût) sont transmises à une plateforme centrale de surveillance. |   1    |  D   |
| 7.6.2 | Vérifier que les seuils d’alerte sont définis pour chaque métrique de sécurité, avec des procédures d’escalade lors de l’astreinte.                                                                                    |   1    |  V   |
| 7.6.3 | Vérifiez que les tableaux de bord corrèlent les anomalies de sortie avec le modèle/version, le flag de fonctionnalité et les changements de données en amont.                                                          |   2    |  V   |
| 7.6.4 | Vérifiez que les données de surveillance reviennent dans le réentraînement, le réglage fin ou la mise à jour des règles dans le cadre d’un flux de travail MLOps documenté.                                            |   2    | D/V  |
| 7.6.5 | Vérifiez que les pipelines de surveillance sont soumis à des tests de pénétration et à un contrôle d'accès afin d'éviter la fuite des journaux sensibles.                                                              |   3    |  V   |

---

## 7.7 Garde-fous des médias génératifs

Veiller à ce que les systèmes d'IA ne génèrent pas de contenu multimédia illégal, nuisible ou non autorisé en appliquant des contraintes de politique, en procédant à la validation des sorties et en assurant la traçabilité.

|   #   | description                                                                                                                                                                                                                                                    | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 7.7.1 | Vérifiez que les invites du système et les instructions de l'utilisateur interdisent explicitement la génération de médias deepfake illégaux, nuisibles ou non consensuels (par exemple, image, vidéo, audio).                                                 |   1    | D/V  |
| 7.7.2 | Vérifiez que les requêtes sont filtrées pour prévenir les tentatives d'usurpation d'identité, de deepfakes sexuellement explicites ou de contenus montrant des personnes réelles sans leur consentement.                                                       |   2    | D/V  |
| 7.7.3 | Vérifiez que le système utilise le hachage perceptuel, la détection de filigranes ou l’empreinte numérique pour prévenir la reproduction non autorisée de contenus protégés par le droit d’auteur.                                                             |   2    |  V   |
| 7.7.4 | Vérifiez que tous les médias générés sont signés cryptographiquement, marqués d'un filigrane, ou intégrés avec des métadonnées de provenance résistantes à la falsification, afin d'assurer la traçabilité en aval.                                            |   3    | D/V  |
| 7.7.5 | Vérifier que les tentatives de contournement (par exemple l'obfuscation des requêtes, l'argot, les formulations adversariales) sont détectées, consignées et soumises à une limitation de débit ; les abus répétés sont remontés aux systèmes de surveillance. |   3    |  V   |

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

