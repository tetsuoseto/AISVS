# C12 Surveillance, journalisation et détection d'anomalies

## Objectif de contrôle

Cette section fournit les exigences pour assurer une visibilité en temps réel et médico-légale sur ce que le modèle et les autres composants d'IA voient, font et renvoient, afin que les menaces puissent être détectées, triées et analysées.

## C12.1 Journalisation des requêtes et des réponses

|   #    | Description                                                                                                                                                                                                                                                                                    | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.1.1 | Vérifiez que toutes les invites des utilisateurs et les réponses du modèle sont enregistrées avec les métadonnées appropriées (par exemple, horodatage, ID utilisateur, ID de session, version du modèle).                                                                                     |   1    | D/V  |
| 12.1.2 | Vérifiez que les journaux sont stockés dans des référentiels sécurisés et contrôlés par accès, avec des politiques de conservation appropriées et des procédures de sauvegarde.                                                                                                                |   1    | D/V  |
| 12.1.3 | Vérifiez que les systèmes de stockage des journaux mettent en œuvre le chiffrement au repos et en transit pour protéger les informations sensibles contenues dans les journaux.                                                                                                                |   1    | D/V  |
| 12.1.4 | Vérifiez que les données sensibles dans les invites et les résultats sont automatiquement redigées ou masquées avant la journalisation, avec des règles de redaction configurables pour les informations personnelles identifiables (PII), les identifiants et les informations propriétaires. |   1    | D/V  |
| 12.1.5 | Vérifiez que les décisions de politique et les actions de filtrage de sécurité sont enregistrées avec suffisamment de détails pour permettre l'audit et le débogage des systèmes de modération de contenu.                                                                                     |   2    | D/V  |
| 12.1.6 | Vérifiez que l'intégrité des journaux est protégée, par exemple, par des signatures cryptographiques ou un stockage en écriture seule.                                                                                                                                                         |   2    | D/V  |

---

## C12.2 Détection des Abus et Alertes

|   #    | Description                                                                                                                                                                                                                                  | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.2.1 | Vérifiez que le système détecte et alerte sur les schémas de jailbreak connus, les tentatives d'injection de prompt et les entrées adverses en utilisant une détection basée sur des signatures.                                             |   1    | D/V  |
| 12.2.2 | Vérifiez que le système s'intègre avec les plateformes existantes de Gestion des Informations et des Événements de Sécurité (SIEM) en utilisant des formats et protocoles de journalisation standard.                                        |   1    | D/V  |
| 12.2.3 | Vérifiez que les événements de sécurité enrichis incluent un contexte spécifique à l'IA, tel que les identifiants de modèle, les scores de confiance et les décisions du filtre de sécurité.                                                 |   2    | D/V  |
| 12.2.4 | Vérifiez que la détection des anomalies comportementales identifie les schémas de conversation inhabituels, les tentatives de reprise excessives ou les comportements de sondage systématique.                                               |   2    | D/V  |
| 12.2.5 | Vérifiez que les mécanismes d'alerte en temps réel notifient les équipes de sécurité lorsqu'une violation potentielle de la politique ou une tentative d'attaque est détectée.                                                               |   2    | D/V  |
| 12.2.6 | Vérifiez que des règles personnalisées sont incluses pour détecter les modèles de menaces spécifiques à l'IA, notamment les tentatives coordonnées de jailbreak, les campagnes d'injection de prompt et les attaques d'extraction de modèle. |   2    | D/V  |
| 12.2.7 | Vérifiez que les workflows automatisés de réponse aux incidents peuvent isoler les modèles compromis, bloquer les utilisateurs malveillants et escalader les événements de sécurité critiques.                                               |   3    | D/V  |

---

## C12.3 Détection de la dérive du modèle

|   #    | Description                                                                                                                                                                                                    | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.3.1 | Vérifiez que le système suit les métriques de performance de base telles que la précision, les scores de confiance, la latence et les taux d'erreur à travers les versions du modèle et les périodes de temps. |   1    | D/V  |
| 12.3.2 | Vérifiez que les alertes automatisées se déclenchent lorsque les métriques de performance dépassent les seuils de dégradation prédéfinis ou s'écartent significativement des références.                       |   2    | D/V  |
| 12.3.3 | Vérifiez que les moniteurs de détection d'hallucinations identifient et signalent les cas où les sorties du modèle contiennent des informations factuellement incorrectes, incohérentes ou fabriquées.         |   2    | D/V  |

---

## C12.4 Télémétrie des performances et du comportement

|   #    | Description                                                                                                                                                                                             | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.4.1 | Vérifiez que les métriques opérationnelles, y compris la latence des requêtes, la consommation de jetons, l'utilisation de la mémoire et le débit, sont continuellement collectées et surveillées.      |   1    | D/V  |
| 12.4.2 | Vérifiez que les taux de réussite et d'échec sont suivis avec une catégorisation des types d'erreurs et de leurs causes profondes.                                                                      |   1    | D/V  |
| 12.4.3 | Vérifiez que la surveillance de l'utilisation des ressources inclut l'utilisation du GPU/CPU, la consommation de mémoire et les besoins en stockage, avec des alertes en cas de dépassement des seuils. |   2    | D/V  |

---

## C12.5 Planification et Exécution de la Réponse aux Incidents d'IA

|   #    | Description                                                                                                                                                                                                            | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.5.1 | Vérifiez que les plans d'intervention en cas d'incident abordent spécifiquement les événements de sécurité liés à l'IA, y compris la compromission des modèles, l'empoisonnement des données et les attaques adverses. |   1    | D/V  |
| 12.5.2 | Vérifiez que les équipes de réponse aux incidents ont accès à des outils et compétences médico-légaux spécifiques à l'IA pour enquêter sur le comportement des modèles et les vecteurs d'attaque.                      |   2    | D/V  |
| 12.5.3 | Vérifiez que l'analyse post-incident inclut les considérations de reformation du modèle, les mises à jour des filtres de sécurité, ainsi que l'intégration des enseignements tirés dans les contrôles de sécurité.     |   3    | D/V  |

---

## C12.5 Détection de la dégradation des performances de l'IA

Surveiller et détecter la dégradation des performances et de la qualité des modèles d'IA au fil du temps.

|   #    | Description                                                                                                                                                                                | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 12.5.1 | Vérifiez que la précision du modèle, la précision, le rappel et les scores F1 sont continuellement surveillés et comparés aux seuils de référence.                                         |   1    | D/V  |
| 12.5.2 | Vérifiez que la détection de dérive des données surveille les changements de distribution des entrées pouvant affecter les performances du modèle.                                         |   1    | D/V  |
| 12.5.3 | Vérifiez que la détection de dérive conceptuelle identifie les changements dans la relation entre les entrées et les sorties attendues.                                                    |   2    | D/V  |
| 12.5.4 | Vérifiez que la dégradation des performances déclenche des alertes automatisées et initie les flux de travail de réentraînement ou de remplacement du modèle.                              |   2    | D/V  |
| 12.5.5 | Vérifiez que l'analyse des causes profondes de la dégradation corrèle les baisses de performance avec les changements de données, les problèmes d'infrastructure ou les facteurs externes. |   3    |  V   |

---

## C12.6 Visualisation de DAG et sécurité des flux de travail

Protéger les systèmes de visualisation des flux de travail contre les fuites d’informations et les attaques de manipulation.

|   #    | Description                                                                                                                                                                                                   | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.6.1 | Vérifiez que les données de visualisation du DAG sont assainies pour supprimer les informations sensibles avant le stockage ou la transmission.                                                               |   1    | D/V  |
| 12.6.2 | Vérifiez que les contrôles d'accès à la visualisation des workflows garantissent que seuls les utilisateurs autorisés peuvent consulter les chemins de décision des agents et les traces de raisonnement.     |   1    | D/V  |
| 12.6.3 | Vérifiez que l'intégrité des données DAG est protégée par des signatures cryptographiques et des mécanismes de stockage infalsifiable.                                                                        |   2    | D/V  |
| 12.6.4 | Vérifiez que les systèmes de visualisation de flux de travail mettent en œuvre une validation des entrées pour empêcher les attaques par injection via des données de nœuds ou d'arêtes spécialement conçues. |   2    | D/V  |
| 12.6.5 | Vérifiez que les mises à jour en temps réel du DAG sont limitées en débit et validées afin de prévenir les attaques par déni de service sur les systèmes de visualisation.                                    |   3    | D/V  |

---

## C12.7 Surveillance proactive du comportement en matière de sécurité

Détection et prévention des menaces de sécurité par l'analyse proactive du comportement des agents.

|   #    | Description                                                                                                                                                           | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 12.7.1 | Vérifiez que les comportements proactifs des agents sont validés en matière de sécurité avant leur exécution, avec intégration d'une évaluation des risques.          |   1    | D/V  |
| 12.7.2 | Vérifiez que les déclencheurs de l'initiative autonome incluent l'évaluation du contexte de sécurité et l'analyse du paysage des menaces.                             |   2    | D/V  |
| 12.7.3 | Vérifiez que les schémas de comportement proactifs sont analysés en tenant compte des implications potentielles en matière de sécurité et des conséquences imprévues. |   2    | D/V  |
| 12.7.4 | Vérifiez que les actions proactives critiques pour la sécurité nécessitent des chaînes d'approbation explicites avec des pistes d'audit.                              |   3    | D/V  |
| 12.7.5 | Vérifiez que la détection des anomalies comportementales identifie les déviations dans les modèles d'agents proactifs pouvant indiquer une compromission.             |   3    | D/V  |

---

## Références

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

