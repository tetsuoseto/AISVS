# 9 Orchestration autonome et sécurité de l'action agentique

## Objectif de contrôle

Assurez-vous que les systèmes d’IA autonomes ou multi-agents ne puissent exécuter que des actions explicitement prévues, authentifiées, auditables, et respectant des seuils définis de coût et de risque. Cela protège contre des menaces telles que la compromission de système autonome, le mauvais usage d’outils, la détection de boucle agent, le détournement de communication, l’usurpation d’identité, la manipulation d’essaim, et la manipulation d’intention.

---

## 9.1 Budgets de planification des tâches d'agent et de récursion

Limiter les plans récursifs et imposer des points de contrôle humains pour les actions privilégiées.

|   #   | Description                                                                                                                                                                                                         | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.1.1 | Vérifiez que la profondeur maximale de récursion, la largeur, le temps écoulé, les jetons et le coût monétaire par exécution d'agent sont configurés de manière centralisée et sous contrôle de version.            |   1    | D/V  |
| 9.1.2 | Vérifiez que les actions privilégiées ou irréversibles (par exemple, les validations de code, les transferts financiers) nécessitent une approbation humaine explicite via un canal auditable avant leur exécution. |   1    | D/V  |
| 9.1.3 | Vérifiez que les moniteurs de ressources en temps réel déclenchent une interruption du disjoncteur lorsque tout seuil de budget est dépassé, arrêtant ainsi toute extension supplémentaire des tâches.              |   2    |  D   |
| 9.1.4 | Vérifiez que les événements de disjoncteur sont enregistrés avec l'ID de l'agent, la condition de déclenchement et l'état du plan capturé pour un examen médico-légal.                                              |   2    | D/V  |
| 9.1.5 | Vérifiez que les tests de sécurité couvrent les scénarios d'épuisement de budget et de plan incontrôlé, en confirmant un arrêt sécurisé sans perte de données.                                                      |   3    |  V   |
| 9.1.6 | Vérifiez que les politiques budgétaires sont exprimées en tant que politique sous forme de code et appliquées dans le CI/CD pour bloquer la dérive de configuration.                                                |   3    |  D   |

---

## 9.2 Bac à sable des plugins d'outils

Isoler les interactions des outils pour prévenir tout accès non autorisé au système ou toute exécution de code.

|   #   | Description                                                                                                                                                                                                                              | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.2.1 | Vérifiez que chaque outil/plugin s'exécute à l'intérieur d'un système d'exploitation, d'un conteneur ou d'un bac à sable de niveau WASM avec des politiques de système de fichiers, de réseau et d'appels système à privilèges minimaux. |   1    | D/V  |
| 9.2.2 | Vérifiez que les quotas de ressources du bac à sable (CPU, mémoire, disque, sortie réseau) et les délais d'exécution sont appliqués et enregistrés.                                                                                      |   1    | D/V  |
| 9.2.3 | Vérifiez que les fichiers binaires ou descripteurs des outils sont signés numériquement ; les signatures sont validées avant le chargement.                                                                                              |   2    | D/V  |
| 9.2.4 | Vérifiez que les flux de télémétrie du bac à sable sont envoyés à un SIEM ; les anomalies (par exemple, les tentatives de connexions sortantes) déclenchent des alertes.                                                                 |   2    |  V   |
| 9.2.5 | Vérifiez que les plugins à haut risque font l'objet d'une revue de sécurité et de tests de pénétration avant leur déploiement en production.                                                                                             |   3    |  V   |
| 9.2.6 | Vérifiez que les tentatives d’évasion du bac à sable sont automatiquement bloquées et que le plugin fautif est mis en quarantaine en attendant l’enquête.                                                                                |   3    | D/V  |

---

## 9.3 Boucle autonome et limitation des coûts

Détecter et arrêter la récursion incontrôlée d’agent à agent et les explosions de coûts.

|   #   | Description                                                                                                                                                          | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.3.1 | Vérifiez que les appels inter-agents incluent une limite de saut ou un TTL que le runtime décrémente et applique.                                                    |   1    | D/V  |
| 9.3.2 | Vérifiez que les agents conservent un ID unique de graphe d’invocation pour détecter l’auto-invocation ou les schémas cycliques.                                     |   2    |  D   |
| 9.3.3 | Vérifiez que les compteurs cumulés d’unités de calcul et de dépenses sont suivis par chaîne de requêtes ; le dépassement de la limite entraîne l’arrêt de la chaîne. |   2    | D/V  |
| 9.3.4 | Vérifiez qu'une analyse formelle ou une vérification par modèle démontre l'absence de récursion non bornée dans les protocoles d'agent.                              |   3    |  V   |
| 9.3.5 | Vérifiez que les événements d'interruption de boucle génèrent des alertes et alimentent les indicateurs d'amélioration continue.                                     |   3    |  D   |

---

## 9.4 Protection contre les utilisations inadéquates au niveau du protocole

Canaux de communication sécurisés entre les agents et les systèmes externes pour prévenir la prise de contrôle ou la manipulation.

|   #   | Description                                                                                                                                                      | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.4.1 | Vérifiez que tous les messages agent-à-outil et agent-à-agent sont authentifiés (par exemple, TLS mutuel ou JWT) et chiffrés de bout en bout.                    |   1    | D/V  |
| 9.4.2 | Vérifiez que les schémas sont strictement validés ; les champs inconnus ou les messages mal formés sont rejetés.                                                 |   1    |  D   |
| 9.4.3 | Vérifiez que les contrôles d'intégrité (MAC ou signatures numériques) couvrent l'intégralité de la charge utile du message, y compris les paramètres de l'outil. |   2    | D/V  |
| 9.4.4 | Vérifiez que la protection contre la relecture (nonces ou fenêtres de timestamp) est appliquée au niveau du protocole.                                           |   2    |  D   |
| 9.4.5 | Vérifiez que les implémentations des protocoles subissent un fuzzing et une analyse statique pour détecter les failles d’injection ou de désérialisation.        |   3    |  V   |

---

## 9.5 Identité de l'agent et preuve de falsification

Assurez-vous que les actions sont attribuables et que les modifications sont détectables.

|   #   | Description                                                                                                                                | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 9.5.1 | Vérifiez que chaque instance d'agent possède une identité cryptographique unique (paire de clés ou crédential matériel racine).            |   1    | D/V  |
| 9.5.2 | Vérifiez que toutes les actions des agents sont signées et horodatées ; les journaux incluent la signature pour la non-répudiation.        |   2    | D/V  |
| 9.5.3 | Vérifiez que les journaux à preuve de falsification sont stockés dans un support en mode ajout uniquement ou en mode écriture unique.      |   2    |  V   |
| 9.5.4 | Vérifiez que les clés d'identité tournent selon un calendrier défini et en cas d'indicateurs de compromission.                             |   3    |  D   |
| 9.5.5 | Vérifiez que les tentatives d'usurpation d'identité ou de conflit de clé déclenchent une mise en quarantaine immédiate de l'agent affecté. |   3    | D/V  |

---

## 9.6 Réduction des risques par essaim multi-agent

Atténuer les risques liés au comportement collectif grâce à l'isolation et à la modélisation formelle de la sécurité.

|   #   | Description                                                                                                                                                   | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.6.1 | Vérifiez que les agents opérant dans différents domaines de sécurité s'exécutent dans des environnements d'exécution isolés ou des segments réseau séparés.   |   1    | D/V  |
| 9.6.2 | Vérifiez que les comportements en essaim sont modélisés et formellement vérifiés pour la vivacité et la sécurité avant le déploiement.                        |   3    |  V   |
| 9.6.3 | Vérifiez que les moniteurs d'exécution détectent les motifs émergents dangereux (par exemple, oscillations, interblocages) et initient une action corrective. |   3    |  D   |

---

## 9.7 Authentification / Autorisation des utilisateurs et des outils

Implémentez des contrôles d'accès robustes pour chaque action déclenchée par un agent.

|   #   | Description                                                                                                                                                                     | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.7.1 | Vérifiez que les agents s'authentifient en tant que principaux de première classe auprès des systèmes en aval, sans jamais réutiliser les identifiants des utilisateurs finaux. |   1    | D/V  |
| 9.7.2 | Vérifiez que les politiques d'autorisation granulaires restreignent les outils qu'un agent peut invoquer ainsi que les paramètres qu'il peut fournir.                           |   2    |  D   |
| 9.7.3 | Vérifiez que les contrôles de privilèges sont réévalués à chaque appel (autorisation continue), et pas seulement au début de la session.                                        |   2    |  V   |
| 9.7.4 | Vérifiez que les privilèges délégués expirent automatiquement et nécessitent un nouveau consentement après un délai d'attente ou un changement de portée.                       |   3    |  D   |

---

## 9.8 Sécurité de la communication agent à agent

Chiffrer et protéger l'intégrité de tous les messages inter-agents pour empêcher l'écoute clandestine et la falsification.

|   #   | Description                                                                                                                                                   | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.8.1 | Vérifiez que l'authentification mutuelle et le chiffrement à secret parfait avancé (par exemple TLS 1.3) sont obligatoires pour les canaux des agents.        |   1    | D/V  |
| 9.8.2 | Vérifiez que l'intégrité et l'origine du message sont validées avant le traitement ; les échecs déclenchent des alertes et le rejet du message.               |   1    |  D   |
| 9.8.3 | Vérifiez que les métadonnées de communication (horodatages, numéros de séquence) sont enregistrées pour soutenir la reconstruction judiciaire.                |   2    | D/V  |
| 9.8.4 | Vérifiez que la vérification formelle ou la model checking confirme que les machines à états du protocole ne peuvent pas être conduites à des états non sûrs. |   3    |  V   |

---

## 9.9 Vérification de l'intention et application des contraintes

Valider que les actions de l'agent sont conformes à l'intention exprimée par l'utilisateur et aux contraintes du système.

|   #   | Description                                                                                                                                                                                                                        | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.9.1 | Vérifiez que les solveurs de contraintes pré-exécution vérifient les actions proposées par rapport aux règles de sécurité et de politique codées en dur.                                                                           |   1    |  D   |
| 9.9.2 | Vérifiez que les actions à fort impact (financières, destructrices, sensibles à la vie privée) nécessitent une confirmation explicite d'intention de la part de l'utilisateur initiateur.                                          |   2    | D/V  |
| 9.9.3 | Vérifiez que les contrôles de post-condition valident que les actions terminées ont atteint les effets prévus sans effets secondaires ; les écarts déclenchent une restauration.                                                   |   2    |  V   |
| 9.9.4 | Vérifiez que les méthodes formelles (par exemple, la vérification de modèle, la démonstration de théorèmes) ou les tests basés sur les propriétés démontrent que les plans des agents respectent toutes les contraintes déclarées. |   3    |  V   |
| 9.9.5 | Vérifiez que les incidents de non-correspondance d'intention ou de violation de contrainte alimentent les cycles d'amélioration continue et le partage du renseignement sur les menaces.                                           |   3    |  D   |

---

## 9.10 Sécurité de la stratégie de raisonnement de l'agent

Sélection et exécution sécurisées de différentes stratégies de raisonnement, y compris les approches ReAct, Chain-of-Thought et Tree-of-Thoughts.

|   #    | Description                                                                                                                                                                                                                                                                   | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.10.1 | Vérifiez que la sélection de la stratégie de raisonnement utilise des critères déterministes (complexité de l'entrée, type de tâche, contexte de sécurité) et que des entrées identiques produisent des sélections de stratégie identiques dans un même contexte de sécurité. |   1    | D/V  |
| 9.10.2 | Vérifiez que chaque stratégie de raisonnement (ReAct, chaîne de pensée, arbre de pensées) dispose d'une validation d'entrée dédiée, d'une assainissement des sorties et de limites de temps d'exécution spécifiques à son approche cognitive.                                 |   1    | D/V  |
| 9.10.3 | Vérifiez que les transitions de stratégie de raisonnement sont enregistrées avec un contexte complet incluant les caractéristiques de l'entrée, les valeurs des critères de sélection et les métadonnées d'exécution pour la reconstitution de la piste d'audit.              |   2    | D/V  |
| 9.10.4 | Vérifiez que le raisonnement Tree-of-Thoughts inclut des mécanismes d'élagage des branches qui arrêtent l'exploration lorsqu'une violation de politique, une limite de ressources ou une frontière de sécurité est détectée.                                                  |   2    | D/V  |
| 9.10.5 | Vérifiez que les cycles ReAct (Reason-Act-Observe) incluent des points de contrôle de validation à chaque phase : vérification des étapes de raisonnement, autorisation des actions, et assainissement des observations avant de continuer.                                   |   2    | D/V  |
| 9.10.6 | Vérifiez que les métriques de performance de la stratégie de raisonnement (temps d'exécution, utilisation des ressources, qualité de sortie) sont surveillées avec des alertes automatisées lorsque les métriques s'écartent des seuils configurés.                           |   3    | D/V  |
| 9.10.7 | Vérifiez que les approches de raisonnement hybride combinant plusieurs stratégies maintiennent la validation des entrées et les contraintes de sortie de toutes les stratégies constitutives sans contourner aucun contrôle de sécurité.                                      |   3    | D/V  |
| 9.10.8 | Vérifiez que les tests de sécurité des stratégies de raisonnement incluent le fuzzing avec des entrées malformées, des invites adverses conçues pour forcer le changement de stratégie, et des tests des conditions limites pour chaque approche cognitive.                   |   3    | D/V  |

---

## 9.11 Gestion de l'État du Cycle de Vie de l'Agent et Sécurité

Initialisation sécurisée des agents, transitions d’état et terminaison avec des pistes d’audit cryptographiques et des procédures de récupération définies.

|   #    | Description                                                                                                                                                                                                                                                                                                              | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 9.11.1 | Vérifiez que l'initialisation de l'agent inclut l'établissement d'une identité cryptographique avec des informations d'identification sécurisées par le matériel et des journaux d'audit de démarrage immuables contenant l'ID de l'agent, l'horodatage, le hachage de configuration et les paramètres d'initialisation. |   1    | D/V  |
| 9.11.2 | Vérifiez que les transitions d’état de l’agent sont signées cryptographiquement, horodatées, et enregistrées avec un contexte complet incluant les événements déclencheurs, le hachage de l’état précédent, le hachage du nouvel état, ainsi que les validations de sécurité effectuées.                                 |   2    | D/V  |
| 9.11.3 | Vérifiez que les procédures d'arrêt de l'agent incluent l'effacement sécurisé de la mémoire à l'aide d'une suppression cryptographique ou d'une réécriture multiple, la révocation des identifiants avec notification à l'autorité de certification, et la génération de certificats de terminaison inviolables.         |   2    | D/V  |
| 9.11.4 | Vérifiez que les mécanismes de récupération des agents valident l’intégrité de l’état à l’aide de sommes de contrôle cryptographiques (SHA-256 minimum) et reviennent à des états connus comme fiables en cas de détection de corruption, avec des alertes automatisées et des exigences d’approbation manuelle.         |   3    | D/V  |
| 9.11.5 | Vérifiez que les mécanismes de persistance des agents chiffrent les données d'état sensibles avec des clés AES-256 spécifiques à chaque agent et mettent en œuvre une rotation sécurisée des clés selon des calendriers configurables (maximum 90 jours) avec un déploiement sans interruption.                          |   3    | D/V  |

---

## 9.12 Cadre de sécurité pour l'intégration des outils

Contrôles de sécurité pour le chargement dynamique des outils, leur exécution et la validation des résultats avec des processus définis d'évaluation des risques et d'approbation.

|   #    | Description                                                                                                                                                                                                                                                                                                             | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.12.1 | Vérifiez que les descripteurs d’outils incluent des métadonnées de sécurité spécifiant les privilèges requis (lecture/écriture/exécution), les niveaux de risque (faible/moyen/élevé), les limites de ressources (CPU, mémoire, réseau) et les exigences de validation documentées dans les manifestes d’outils.        |   1    | D/V  |
| 9.12.2 | Vérifiez que les résultats d'exécution des outils sont validés par rapport aux schémas attendus (JSON Schema, XML Schema) et aux politiques de sécurité (assainissement des sorties, classification des données) avant intégration, avec des limites de délai d'attente et des procédures de gestion des erreurs.       |   1    | D/V  |
| 9.12.3 | Vérifiez que les journaux d'interaction des outils incluent un contexte de sécurité détaillé, comprenant l'utilisation des privilèges, les schémas d'accès aux données, le temps d'exécution, la consommation des ressources et les codes de retour, avec une journalisation structurée pour l'intégration SIEM.        |   2    | D/V  |
| 9.12.4 | Vérifiez que les mécanismes de chargement dynamique des outils valident les signatures numériques en utilisant l'infrastructure PKI et mettent en œuvre des protocoles de chargement sécurisés avec une isolation en sandbox et une vérification des permissions avant l'exécution.                                     |   2    | D/V  |
| 9.12.5 | Vérifiez que les évaluations de sécurité des outils sont automatiquement déclenchées pour les nouvelles versions avec des étapes d'approbation obligatoires incluant l'analyse statique, les tests dynamiques et la revue par l'équipe de sécurité, avec des critères d'approbation documentés et des exigences de SLA. |   3    | D/V  |

---

### Références

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

