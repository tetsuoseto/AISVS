# C12 Surveillance, journalisation et détection d’anomalies

## Objectif de contrôle

Cette section fournit les exigences pour offrir une visibilité en temps réel et forensique sur ce que le modèle et les autres composants d'IA voient, font et renvoient, afin que les menaces puissent être détectées, triées et que l’on puisse en tirer des enseignements.

## C12.1 Journalisation des requêtes et des réponses

|   #    | description                                                                                                                                                                                                                                                                                                         | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.1.1 | Vérifiez que toutes les requêtes des utilisateurs et les réponses du modèle sont enregistrées avec des métadonnées appropriées (par exemple horodatage, identifiant utilisateur, identifiant de session, version du modèle).                                                                                        |   1    | D/V  |
| 12.1.2 | Vérifiez que les journaux sont stockés dans des dépôts sécurisés et à accès contrôlé, avec des politiques de rétention appropriées et des procédures de sauvegarde.                                                                                                                                                 |   1    | D/V  |
| 12.1.3 | Vérifiez que les systèmes de stockage des journaux mettent en œuvre le chiffrement au repos et en transit afin de protéger les informations sensibles contenues dans les journaux.                                                                                                                                  |   1    | D/V  |
| 12.1.4 | Vérifiez que les données sensibles dans les invites et les sorties sont automatiquement caviardées ou masquées avant l'enregistrement dans les journaux, avec des règles de caviardage configurables pour les PII (informations personnellement identifiables), les identifiants et les informations propriétaires. |   1    | D/V  |
| 12.1.5 | Vérifiez que les décisions de politique et les actions de filtrage de sécurité sont consignées avec un niveau de détail suffisant pour permettre l’audit et le débogage des systèmes de modération de contenu.                                                                                                      |   2    | D/V  |
| 12.1.6 | Vérifiez que l'intégrité des journaux est protégée, par exemple, par des signatures cryptographiques ou par un stockage en écriture seule.                                                                                                                                                                          |   2    | D/V  |

---

## C12.2 Détection et alerte des abus

|   #    | description                                                                                                                                                                                                                                   | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.2.1 | Vérifiez que le système détecte et déclenche des alertes sur des modèles de jailbreak connus, des tentatives d'injection d'instructions et des entrées adversariales en utilisant une détection basée sur des signatures.                     |   1    | D/V  |
| 12.2.2 | Vérifiez que le système s'intègre aux plateformes SIEM existantes en utilisant des formats de journalisation standard et des protocoles standard.                                                                                             |   1    | D/V  |
| 12.2.3 | Vérifiez que les événements de sécurité enrichis incluent un contexte spécifique à l’IA, tel que les identifiants du modèle, les scores de confiance et les décisions du filtre de sécurité.                                                  |   2    | D/V  |
| 12.2.4 | Vérifiez que la détection d’anomalies comportementales identifie des motifs de conversation inhabituels, des tentatives de réessai excessives ou des comportements d’exploration systématiques.                                               |   2    | D/V  |
| 12.2.5 | Vérifiez que les mécanismes d'alerte en temps réel notifient les équipes de sécurité lorsque des violations potentielles de la politique ou des tentatives d'attaque sont détectées.                                                          |   2    | D/V  |
| 12.2.6 | Vérifiez que des règles personnalisées sont incluses pour détecter des schémas de menace spécifiques à l'IA, y compris les tentatives de jailbreak coordonnées, les campagnes d'injection de prompts et les attaques d'extraction de modèles. |   2    | D/V  |
| 12.2.7 | Vérifiez que des workflows automatisés de réponse aux incidents peuvent isoler les modèles compromis, bloquer les utilisateurs malveillants et faire remonter les événements de sécurité critiques.                                           |   3    | D/V  |

---

## C12.3 Détection de dérive du modèle

|   #    | description                                                                                                                                                                                            | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 12.3.1 | Vérifiez que le système suit les mesures de performance de base telles que la précision, les scores de confiance, la latence et les taux d'erreur, à travers les versions du modèle et les périodes.   |   1    | D/V  |
| 12.3.2 | Vérifier que les alertes automatisées se déclenchent lorsque les métriques de performance dépassent des seuils de dégradation prédéfinis ou dévient de manière significative des lignes de base.       |   2    | D/V  |
| 12.3.3 | Vérifiez que les moniteurs de détection d’hallucinations identifient et signalent les cas où les sorties du modèle contiennent des informations factuellement incorrectes, incohérentes ou fabriquées. |   2    | D/V  |

---

## C12.4 Télémétrie de performance et de comportement

|   #    | description                                                                                                                                                                                                  | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 12.4.1 | Vérifiez que les métriques opérationnelles, notamment la latence des requêtes, la consommation de jetons, l'utilisation de la mémoire et le débit, sont collectées et surveillées en continu.                |   1    | D/V  |
| 12.4.2 | Vérifier que les taux de réussite et d'échec sont suivis avec une catégorisation des types d'erreurs et de leurs causes profondes.                                                                           |   1    | D/V  |
| 12.4.3 | Vérifier que la surveillance de l'utilisation des ressources inclut l'utilisation du GPU/CPU, la consommation de mémoire et les exigences de stockage, avec des alertes en cas de franchissement des seuils. |   2    | D/V  |

---

## C12.5 Planification et exécution de la réponse aux incidents d’IA

|   #    | description                                                                                                                                                                                                                 | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.5.1 | Vérifiez que les plans de réponse aux incidents prennent spécifiquement en compte les événements de sécurité liés à l'IA, y compris la compromission du modèle, l'empoisonnement des données et les attaques adversariales. |   1    | D/V  |
| 12.5.2 | Vérifiez que les équipes d'intervention en cas d'incident disposent d'outils forensiques spécifiques à l'IA et d'une expertise pour enquêter sur le comportement des modèles et les vecteurs d'attaque.                     |   2    | D/V  |
| 12.5.3 | Vérifiez que l'analyse post-incident inclut les considérations de réentraînement du modèle, les mises à jour des filtres de sécurité et l'intégration des leçons tirées dans les contrôles de sécurité.                     |   3    | D/V  |

---

## C12.5 Détection de la dégradation des performances de l'IA

Surveiller et détecter la dégradation des performances et de la qualité des modèles d'IA au fil du temps.

|   #    | description                                                                                                                                                                                   | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.5.1 | Vérifiez que l'exactitude du modèle, la précision, le rappel et les scores F1 sont surveillés en continu et comparés aux seuils de référence.                                                 |   1    | D/V  |
| 12.5.2 | Vérifiez que la détection de dérive des données surveille les changements de distribution des entrées qui pourraient affecter les performances du modèle.                                     |   1    | D/V  |
| 12.5.3 | Vérifiez que la détection du concept drift identifie les changements dans la relation entre les entrées et les sorties attendues.                                                             |   2    | D/V  |
| 12.5.4 | Vérifiez que la dégradation des performances déclenche des alertes automatisées et initie des flux de travail de réentraînement ou de remplacement du modèle.                                 |   2    | D/V  |
| 12.5.5 | Vérifiez que l'analyse des causes profondes de la dégradation corrèle les baisses de performance avec les modifications des données, les problèmes d'infrastructure ou les facteurs externes. |   3    |  V   |

---

## C12.6 Visualisation du DAG et sécurité des flux de travail

Protégez les systèmes de visualisation des flux de travail contre les fuites d'informations et les attaques de manipulation.

|   #    | description                                                                                                                                                                                                      | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.6.1 | Vérifiez que les données de visualisation du graphe dirigé acyclique (GDA) sont nettoyées pour supprimer les informations sensibles avant le stockage ou la transmission.                                        |   1    | D/V  |
| 12.6.2 | Vérifiez que les contrôles d'accès à la visualisation du flux de travail garantissent que seuls les utilisateurs autorisés peuvent voir les chemins de décision des agents et les traces de raisonnement.        |   1    | D/V  |
| 12.6.3 | Vérifiez que l'intégrité des données DAG est protégée par des signatures cryptographiques et des mécanismes de stockage à preuve de manipulation.                                                                |   2    | D/V  |
| 12.6.4 | Vérifiez que les systèmes de visualisation des flux de travail mettent en œuvre une validation des entrées afin de prévenir les attaques par injection via des données de nœud ou d'arête soigneusement conçues. |   2    | D/V  |
| 12.6.5 | Vérifiez que les mises à jour en temps réel du DAG sont limitées en débit et validées afin de prévenir les attaques par déni de service sur les systèmes de visualisation.                                       |   3    | D/V  |

---

## C12.7 Surveillance proactive du comportement de sécurité

Détection et prévention des menaces de sécurité par l'analyse proactive du comportement des agents.

|   #    | description                                                                                                                                                      | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.7.1 | Vérifiez que les comportements des agents proactifs sont validés sur le plan de la sécurité avant l'exécution, avec une intégration de l'évaluation des risques. |   1    | D/V  |
| 12.7.2 | Vérifiez que les déclencheurs d’initiative autonome incluent l’évaluation du contexte de sécurité et l’évaluation du paysage des menaces.                        |   2    | D/V  |
| 12.7.3 | Vérifiez que les comportements proactifs sont analysés pour des implications de sécurité potentielles et des conséquences inattendues.                           |   2    | D/V  |
| 12.7.4 | Vérifiez que les actions proactives critiques en matière de sécurité nécessitent des chaînes d'approbation explicites avec des journaux d'audit.                 |   3    | D/V  |
| 12.7.5 | Vérifiez que la détection d’anomalies comportementales identifie les écarts dans les schémas des agents proactifs susceptibles d’indiquer une compromission.     |   3    | D/V  |

---

## Références

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

