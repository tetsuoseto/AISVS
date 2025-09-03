# 9 Orchestration autonome et sécurité des actions agentiques

## Objectif de contrôle

Assurez-vous que les systèmes d'IA autonomes ou multi-agent ne puissent exécuter que des actions qui sont explicitement prévues, authentifiées, auditées et dans des limites de coût et de risque. Cela protège contre des menaces telles que la compromission de systèmes autonomes, l'utilisation abusive d'outils, la détection de boucle d'agent, le détournement des communications, l'usurpation d'identité, la manipulation d'essaims et la manipulation des intentions.

---

## 9.1 Agent Planification-des-tâches & Budgets de récursivité

Ralentir les plans récursifs et imposer des points de contrôle humains pour les actions privilégiées.

|   #   | description                                                                                                                                                                                                                     | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.1.1 | Vérifiez que la profondeur maximale de récursion, la largeur d'exploration, le temps réel (wall-clock time), les jetons et le coût monétaire par exécution d'un agent sont centralement configurés et sous contrôle de version. |   1    | D/V  |
| 9.1.2 | Vérifiez que les actions privilégiées ou irréversibles (par exemple, des commits de code, des transferts financiers) nécessitent une approbation humaine explicite via un canal auditable avant l'exécution.                    |   1    | D/V  |
| 9.1.3 | Vérifiez que les moniteurs de ressources en temps réel déclenchent l'interruption du circuit-breaker lorsque n'importe quel seuil budgétaire est dépassé, ce qui met fin à l'expansion ultérieure des tâches.                   |   2    |  D   |
| 9.1.4 | Vérifier que les événements de disjoncteur sont enregistrés avec l'identifiant de l'agent, la condition de déclenchement et l'état du plan capturé pour examen médico-légal.                                                    |   2    | D/V  |
| 9.1.5 | Vérifiez que les tests de sécurité couvrent les scénarios budget-exhaustion et runaway-plan, en confirmant un arrêt sûr sans perte de données.                                                                                  |   3    |  V   |
| 9.1.6 | Vérifiez que les politiques budgétaires sont exprimées sous forme de policy-as-code et appliquées dans CI/CD pour empêcher la dérive de configuration.                                                                          |   3    |  D   |

---

## 9.2 Mise en bac à sable des outils et des plug-ins

Isoler les interactions avec les outils afin de prévenir tout accès non autorisé au système ou l'exécution de code.

|   #   | description                                                                                                                                                                                             | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.2.1 | Vérifiez que chaque outil/plug-in s'exécute dans un bac à sable au niveau OS, conteneur ou WASM, avec des politiques de moindre privilège pour le système de fichiers, le réseau et les appels système. |   1    | D/V  |
| 9.2.2 | Vérifier que les quotas de ressources du bac à sable (CPU, mémoire, disque, sortie réseau) et les timeouts d’exécution sont appliqués et consignés.                                                     |   1    | D/V  |
| 9.2.3 | Vérifiez que les fichiers binaires d’outils ou les descripteurs sont signés numériquement ; les signatures sont vérifiées avant le chargement.                                                          |   2    | D/V  |
| 9.2.4 | Vérifiez que la télémétrie du bac à sable est acheminée vers un SIEM ; les anomalies (par exemple des tentatives de connexions sortantes) déclenchent des alertes.                                      |   2    |  V   |
| 9.2.5 | Vérifiez que les plugins à haut risque subissent une revue de sécurité et des tests de pénétration avant le déploiement en production.                                                                  |   3    |  V   |
| 9.2.6 | Vérifiez que les tentatives d'évasion du bac à sable sont automatiquement bloquées et que le plugin fautif est mis en quarantaine en attendant l'enquête.                                               |   3    | D/V  |

---

## 9.3 Boucle autonome et bornage des coûts

Détecter et arrêter la récursion non maîtrisée entre agents et les explosions de coûts.

|   #   | description                                                                                                                                                                             | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.3.1 | Vérifiez que les appels inter-agent incluent une limite de sauts ou un TTL que l’environnement d’exécution décrémente et fasse respecter.                                               |   1    | D/V  |
| 9.3.2 | Vérifiez que les agents maintiennent un identifiant unique du graphe d'invocation afin de repérer l'auto-invocation ou les motifs cycliques.                                            |   2    |  D   |
| 9.3.3 | Vérifiez que les compteurs cumulatifs d'unités de calcul et de consommation sont suivis pour chaque chaîne de requêtes ; en cas de dépassement de la limite, la chaîne est interrompue. |   2    | D/V  |
| 9.3.4 | Vérifiez que l'analyse formelle ou la vérification de modèles démontre l'absence de récursion non bornée dans les protocoles des agents.                                                |   3    |  V   |
| 9.3.5 | Vérifiez que les événements d'arrêt de boucle génèrent des alertes et alimentent des métriques d'amélioration continue.                                                                 |   3    |  D   |

---

## 9.4 Protection contre les abus au niveau du protocole

Des canaux de communication sécurisés entre les agents et les systèmes externes afin de prévenir le piratage ou la manipulation.

|   #   | description                                                                                                                                                              | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 9.4.1 | Vérifiez que tous les messages entre l'agent et l'outil, ainsi que ceux entre les agents, sont authentifiés (par exemple TLS mutuel ou JWT) et chiffrés de bout en bout. |   1    | D/V  |
| 9.4.2 | Vérifiez que les schémas sont strictement validés; les champs inconnus ou les messages malformés sont rejetés.                                                           |   1    |  D   |
| 9.4.3 | Vérifiez que les contrôles d'intégrité (MAC ou signatures numériques) couvrent l'intégralité de la charge utile du message, y compris les paramètres de l'outil.         |   2    | D/V  |
| 9.4.4 | Vérifiez que la protection anti-rejeu (nonces ou fenêtres d'horodatage) est appliquée au niveau de la couche protocole.                                                  |   2    |  D   |
| 9.4.5 | Vérifiez que les implémentations de protocoles subissent des tests de fuzzing et une analyse statique pour des failles d'injection ou de désérialisation.                |   3    |  V   |

---

## 9.5 Identité de l'agent et preuve d'altération

Veillez à ce que les actions soient attribuables et que les modifications soient détectables.

|   #   | description                                                                                                                                   | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.5.1 | Vérifiez que chaque instance d’agent possède une identité cryptographique unique (paire de clés ou crédentiel enraciné dans le matériel).     |   1    | D/V  |
| 9.5.2 | Vérifiez que toutes les actions des agents sont signées et horodatées; les journaux contiennent la signature pour assurer la non-répudiation. |   2    | D/V  |
| 9.5.3 | Vérifiez que les journaux à preuve d'altération sont stockés sur un support en mode append-only ou write-once.                                |   2    |  V   |
| 9.5.4 | Vérifiez que les clés d'identité se renouvellent selon un calendrier défini et en présence d'indicateurs de compromission.                    |   3    |  D   |
| 9.5.5 | Vérifiez que les tentatives d'usurpation ou de conflit de clés déclenchent une mise en quarantaine immédiate de l'agent affecté.              |   3    | D/V  |

---

## 9.6 Réduction du risque des essaims multi-agents

Atténuer les risques liés au comportement collectif par l'isolation et la modélisation formelle de la sécurité.

|   #   | description                                                                                                                                                               | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.6.1 | Vérifiez que les agents opérant dans différents domaines de sécurité s'exécutent dans des environnements d'exécution isolés ou dans des segments réseau isolés.           |   1    | D/V  |
| 9.6.2 | Vérifiez que les comportements d’essaims sont modélisés et vérifiés formellement pour la vivacité et la sécurité avant le déploiement.                                    |   3    |  V   |
| 9.6.3 | Vérifiez que les moniteurs d'exécution détectent les comportements dangereux émergents (par exemple des oscillations, des blocages) et déclenchent une action corrective. |   3    |  D   |

---

## 9.7 Authentification des utilisateurs et des outils / Autorisation

Implémenter des contrôles d'accès robustes pour chaque action déclenchée par l'agent.

|   #   | description                                                                                                                                                                   | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.7.1 | Vérifiez que les agents s’authentifient en tant que principaux de premier ordre auprès des systèmes en aval, sans jamais réutiliser les identifiants des utilisateurs finaux. |   1    | D/V  |
| 9.7.2 | Vérifiez que les politiques d'autorisation à granularité fine restreignent les outils qu'un agent peut invoquer et les paramètres qu'il peut fournir.                         |   2    |  D   |
| 9.7.3 | Vérifier que les contrôles d'autorisation sont réévalués à chaque appel (autorisation continue), et non seulement au démarrage de la session.                                 |   2    |  V   |
| 9.7.4 | Vérifiez que les privilèges délégués expirent automatiquement et nécessitent un nouveau consentement après un délai d'expiration ou un changement de portée.                  |   3    |  D   |

---

## 9.8 Agent-à-Agent Sécurité des communications

Chiffrez et protégez l'intégrité de tous les messages échangés entre les agents afin de contrer l'écoute clandestine et l'altération.

|   #   | description                                                                                                                                                               | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.8.1 | Vérifiez que l’authentification mutuelle et le chiffrement à secret parfait (par exemple TLS 1.3) sont obligatoires pour les canaux d’agents.                             |   1    | D/V  |
| 9.8.2 | Vérifiez que l'intégrité du message et son origine sont vérifiées avant le traitement ; en cas d'échec, des alertes sont déclenchées et le message est rejeté.            |   1    |  D   |
| 9.8.3 | Vérifiez que les métadonnées de communication (horodatages, numéros de séquence) sont enregistrées pour faciliter la reconstitution médico-légale.                        |   2    | D/V  |
| 9.8.4 | Vérifiez que la vérification formelle ou la vérification par modèle confirme que les machines à états de protocole ne peuvent pas être conduites vers des états non sûrs. |   3    |  V   |

---

## 9.9 Vérification de l'intention et application des contraintes

Vérifiez que les actions de l'agent s'alignent sur l'intention déclarée par l'utilisateur et sur les contraintes du système.

|   #   | description                                                                                                                                                                                                                          | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 9.9.1 | Vérifiez que les solveurs de contraintes pré-exécution vérifient les actions proposées par rapport à des règles de sécurité et de politique codées en dur.                                                                           |   1    |  D   |
| 9.9.2 | Vérifiez que les actions à fort impact (financières, destructrices et sensibles à la vie privée) nécessitent une confirmation d'intention explicite de la part de l'utilisateur qui les initie.                                      |   2    | D/V  |
| 9.9.3 | Vérifiez que les vérifications des post-conditions valident que les actions réalisées ont produit les effets escomptés sans effets secondaires ; les écarts déclenchent un retour en arrière.                                        |   2    |  V   |
| 9.9.4 | Vérifiez que les méthodes formelles (par exemple, la vérification de modèles et la démonstration de théorèmes) ou les tests basés sur les propriétés démontrent que les plans des agents satisfont toutes les contraintes déclarées. |   3    |  V   |
| 9.9.5 | Vérifiez que les incidents d'intent-mismatch ou de constraint-violation alimentent les cycles d'amélioration continue et le partage de renseignements sur les menaces.                                                               |   3    |  D   |

---

## 9.10 Raisonnement des agents, Stratégie et Sécurité

Sélection et exécution sécurisées de différentes stratégies de raisonnement, y compris ReAct, Chain-of-Thought et Tree-of-Thoughts.

|   #    | description                                                                                                                                                                                                                                                                   | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.10.1 | Vérifier que la sélection de la stratégie de raisonnement utilise des critères déterministes (complexité de l’entrée, type de tâche, contexte de sécurité) et que des entrées identiques produisent des sélections de stratégie identiques dans le même contexte de sécurité. |   1    | D/V  |
| 9.10.2 | Vérifiez que chaque stratégie de raisonnement (ReAct, Chain-of-Thought, Tree-of-Thoughts) dispose d'une validation des entrées dédiée, d'une sanitisation des sorties et de limites de temps d'exécution propres à son approche cognitive.                                    |   1    | D/V  |
| 9.10.3 | Vérifiez que les transitions entre les stratégies de raisonnement sont enregistrées avec le contexte complet, y compris les caractéristiques d'entrée, les valeurs des critères de sélection et les métadonnées d'exécution pour la reconstruction de la trace d'audit.       |   2    | D/V  |
| 9.10.4 | Vérifiez que le raisonnement par arbre des pensées inclut des mécanismes d'élagage des branches qui interrompent l'exploration lorsque des violations des politiques, des limites de ressources ou des frontières de sécurité sont détectées.                                 |   2    | D/V  |
| 9.10.5 | Vérifiez que les cycles ReAct (Reason-Act-Observe) intègrent des points de contrôle de validation à chaque phase : vérification des étapes de raisonnement, autorisation d'action et assainissement des observations avant de poursuivre.                                     |   2    | D/V  |
| 9.10.6 | Vérifiez que les métriques de performance de la stratégie de raisonnement (temps d'exécution, utilisation des ressources, qualité de la sortie) sont surveillées par des alertes automatiques lorsque les métriques s'écartent au-delà des seuils configurés.                 |   3    | D/V  |
| 9.10.7 | Vérifiez que les approches de raisonnement hybrides qui combinent plusieurs stratégies respectent la validation des entrées et les contraintes de sortie de toutes les stratégies constitutives sans contourner aucun contrôle de sécurité.                                   |   3    | D/V  |
| 9.10.8 | Vérifiez que les tests de sécurité des stratégies de raisonnement incluent le fuzzing avec des entrées malformées, des requêtes adversariales conçues pour forcer le basculement de la stratégie, et des tests des conditions aux limites pour chaque approche cognitive.     |   3    | D/V  |

---

## 9.11 Gestion du cycle de vie et de la sécurité de l'agent

Initialisation sécurisée de l'agent, transitions d'état et terminaison avec des journaux d'audit cryptographiques et des procédures de récupération définies.

|   #    | description                                                                                                                                                                                                                                                                                                                                    | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.11.1 | Vérifiez que l'initialisation de l'agent inclut l'établissement d'une identité cryptographique avec des identifiants basés sur le matériel et des journaux d'audit de démarrage immuables contenant l'ID de l'agent, l'horodatage, le hachage de la configuration et les paramètres d'initialisation.                                          |   1    | D/V  |
| 9.11.2 | Vérifiez que les transitions d'état des agents sont signées cryptographiquement, horodatées et enregistrées avec un contexte complet incluant les événements déclencheurs, le hachage de l'état précédent, le hachage du nouvel état, et les validations de sécurité effectuées.                                                               |   2    | D/V  |
| 9.11.3 | Vérifiez que les procédures d'arrêt de l'agent incluent un effacement sécurisé de la mémoire utilisant l'effacement cryptographique ou l'écriture sur plusieurs passes, la révocation des informations d'identification avec notification à l'autorité de certification, et la génération de certificats de terminaison à preuve d'altération. |   2    | D/V  |
| 9.11.4 | Vérifiez que les mécanismes de récupération des agents valident l'intégrité de l'état à l'aide de sommes de contrôle cryptographiques (SHA-256 au minimum) et basculent vers des états connus et valides lorsque la corruption est détectée, avec des alertes automatisées et des exigences d'approbation manuelle.                            |   3    | D/V  |
| 9.11.5 | Vérifiez que les mécanismes de persistance des agents chiffrent les données d'état sensibles avec des clés AES-256 par agent et mettent en œuvre une rotation sécurisée des clés selon des calendriers configurables (maximum 90 jours) avec un déploiement sans temps d'arrêt.                                                                |   3    | D/V  |

---

## 9.12 Cadre de sécurité de l’intégration des outils

Contrôles de sécurité pour le chargement dynamique d'outils, l'exécution et la validation des résultats, avec des processus d'évaluation des risques et d'approbation définis.

|   #    | description                                                                                                                                                                                                                                                                                                                | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 9.12.1 | Vérifiez que les descripteurs d'outils incluent des métadonnées de sécurité précisant les privilèges requis (lecture/écriture/exécution), les niveaux de risque (faible/moyen/élevé), les limites de ressources (CPU, mémoire, réseau), et les exigences de validation documentées dans les manifestes d'outils.           |   1    | D/V  |
| 9.12.2 | Vérifiez que les résultats d'exécution des outils sont validés par rapport aux schémas attendus (Schéma JSON, Schéma XML) et aux politiques de sécurité (sanitisation de la sortie, classification des données) avant l'intégration avec des limites de délai d'attente et des procédures de gestion des erreurs.          |   1    | D/V  |
| 9.12.3 | Vérifiez que les journaux d'interaction des outils incluent un contexte de sécurité détaillé, y compris l'utilisation des privilèges, les schémas d'accès aux données, le temps d'exécution, la consommation des ressources et les codes de retour, avec une journalisation structurée pour l’intégration dans un SIEM.    |   2    | D/V  |
| 9.12.4 | Vérifiez que les mécanismes de chargement dynamique des outils valident les signatures numériques en utilisant une infrastructure PKI et mettez en œuvre des protocoles de chargement sécurisés avec une isolation sandbox et une vérification des permissions avant l’exécution.                                          |   2    | D/V  |
| 9.12.5 | Vérifiez que les évaluations de sécurité des outils sont déclenchées automatiquement pour les nouvelles versions, avec des portes d'approbation obligatoires comprenant l'analyse statique, les tests dynamiques et la revue par l'équipe de sécurité, avec des critères d'approbation documentés et des exigences de SLA. |   3    | D/V  |

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

