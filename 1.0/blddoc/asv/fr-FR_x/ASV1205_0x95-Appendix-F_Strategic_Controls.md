# Annexe B : Contrôles stratégiques

## C4.15 Sécurité des infrastructures résistantes au quantique

Préparez l'infrastructure d'IA face aux menaces de l'informatique quantique grâce à la cryptographie post-quantique et aux protocoles résistants au quantique.

|   #    | Description                                                                                                                                                                                                                | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.15.1 | Vérifiez que l'infrastructure d'IA met en œuvre des algorithmes cryptographiques post-quantiques approuvés par le NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) pour l'échange de clés et les signatures numériques. |   3    | D/V  |
| 4.15.2 | Vérifiez que les systèmes de distribution de clés quantiques (QKD) sont mis en œuvre pour les communications IA à haute sécurité avec des protocoles de gestion de clés résistants au quantique.                           |   3    | D/V  |
| 4.15.3 | Vérifiez que les cadres d'agilité cryptographique permettent une migration rapide vers de nouveaux algorithmes post-quantiques avec une rotation automatisée des certificats et des clés.                                  |   3    | D/V  |
| 4.15.4 | Vérifiez que la modélisation des menaces quantiques évalue la vulnérabilité de l'infrastructure IA aux attaques quantiques avec des calendriers de migration documentés et des évaluations des risques.                    |   3    |  V   |
| 4.15.5 | Vérifiez que les systèmes cryptographiques hybrides classique-quantique offrent une défense en profondeur pendant la période de transition quantique avec une surveillance des performances.                               |   3    | D/V  |

---

## C4.17 Infrastructure à connaissance zéro

Implémentez des systèmes de preuve à divulgation nulle de connaissance pour la vérification et l’authentification de l’IA préservant la confidentialité, sans révéler d’informations sensibles.

|   #    | Description                                                                                                                                                                                                              | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 4.17.1 | Vérifiez que les preuves à divulgation nulle de connaissance (ZK-SNARKs, ZK-STARKs) valident l’intégrité du modèle IA et la provenance de l’entraînement sans exposer les poids du modèle ni les données d’entraînement. |   3    | D/V  |
| 4.17.2 | Vérifiez que les systèmes d'authentification basés sur ZK permettent une vérification de l'utilisateur préservant la confidentialité pour les services d'IA sans révéler d'informations liées à l'identité.              |   3    | D/V  |
| 4.17.3 | Vérifiez que les protocoles d'intersection d'ensembles privés (PSI) permettent une correspondance sécurisée des données pour l'IA fédérée sans exposer les ensembles de données individuels.                             |   3    | D/V  |
| 4.17.4 | Vérifiez que les systèmes d'apprentissage automatique à connaissance zéro (ZKML) permettent des inférences d'IA vérifiables avec une preuve cryptographique de calcul correct.                                           |   3    | D/V  |
| 4.17.5 | Vérifiez que les ZK-rollups offrent un traitement des transactions IA évolutif et respectueux de la vie privée, avec une vérification par lots et une réduction de la charge computationnelle.                           |   3    | D/V  |

---

## C4.18 Prévention des attaques par canal auxiliaire

Protégez l'infrastructure IA contre les attaques par canal auxiliaire basées sur le timing, la puissance, l'électromagnétisme et le cache qui pourraient divulguer des informations sensibles.

|   #    | Description                                                                                                                                                                                     | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.18.1 | Vérifiez que le temps d'inférence de l'IA est normalisé en utilisant des algorithmes à temps constant et un bourrage afin de prévenir les attaques d'extraction de modèle basées sur le temps.  |   3    | D/V  |
| 4.18.2 | Vérifiez que la protection contre l'analyse de puissance comprend l'injection de bruit, le filtrage de la ligne d'alimentation et les schémas d'exécution aléatoires pour le matériel d'IA.     |   3    | D/V  |
| 4.18.3 | Vérifiez que l'atténuation des canaux auxiliaires basés sur le cache utilise le partitionnement du cache, la randomisation et les instructions de vidage pour empêcher la fuite d'informations. |   3    | D/V  |
| 4.18.4 | Vérifiez que la protection contre les émissions électromagnétiques comprend un blindage, un filtrage des signaux et un traitement aléatoire pour prévenir les attaques de type TEMPEST.         |   3    | D/V  |
| 4.18.5 | Vérifiez que les défenses contre les canaux latéraux microarchitecturaux incluent des contrôles d’exécution spéculative et l’obscurcissement des modèles d’accès mémoire.                       |   3    | D/V  |

---

## C4.19 Sécurité du matériel IA neuromorphique et spécialisé

Sécuriser les architectures matérielles émergentes de l'IA, y compris les puces neuromorphiques, les FPGA, les ASIC personnalisés et les systèmes informatiques optiques.

|   #    | Description                                                                                                                                                                                                           | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.19.1 | Vérifiez que la sécurité des puces neuromorphiques inclut le cryptage des motifs de pics, la protection des poids synaptiques et la validation des règles d’apprentissage basées sur le matériel.                     |   3    | D/V  |
| 4.19.2 | Vérifiez que les accélérateurs d'IA basés sur FPGA mettent en œuvre le chiffrement des bitstreams, des mécanismes anti-contrefaçon et le chargement sécurisé de la configuration avec des mises à jour authentifiées. |   3    | D/V  |
| 4.19.3 | Vérifiez que la sécurité ASIC personnalisée inclut des processeurs de sécurité intégrés, une racine de confiance matérielle et un stockage sécurisé des clés avec détection d'altération.                             |   3    | D/V  |
| 4.19.4 | Vérifiez que les systèmes de calcul optique mettent en œuvre un chiffrement optique quantique-sûr, un commutateur photonique sécurisé et un traitement du signal optique protégé.                                     |   3    | D/V  |
| 4.19.5 | Vérifiez que les puces d’IA hybrides analogiques-numériques incluent un calcul analogique sécurisé, un stockage protégé des poids, et une conversion analogique-numérique authentifiée.                               |   3    | D/V  |

---

## C4.20 Infrastructure de calcul préservant la confidentialité

Mettre en œuvre des contrôles d'infrastructure pour le calcul respectueux de la vie privée afin de protéger les données sensibles lors du traitement et de l'analyse par l'IA.

|   #    | Description                                                                                                                                                                                                                         | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.20.1 | Vérifiez que l'infrastructure de chiffrement homomorphe permet le calcul chiffré sur des charges de travail IA sensibles avec une vérification d'intégrité cryptographique et une surveillance des performances.                    |   3    | D/V  |
| 4.20.2 | Vérifiez que les systèmes de récupération d'informations privées permettent des requêtes de base de données sans révéler les schémas de requête grâce à la protection cryptographique des schémas d'accès.                          |   3    | D/V  |
| 4.20.3 | Vérifiez que les protocoles de calcul multipartite sécurisé permettent une inférence IA préservant la confidentialité sans exposer les entrées individuelles ni les calculs intermédiaires.                                         |   3    | D/V  |
| 4.20.4 | Vérifiez que la gestion des clés préservant la confidentialité comprend la génération distribuée de clés, la cryptographie à seuil, et la rotation sécurisée des clés avec une protection matérielle garantie.                      |   3    | D/V  |
| 4.20.5 | Vérifiez que les performances de calcul préservant la confidentialité sont optimisées grâce au traitement par lots, à la mise en cache et à l'accélération matérielle tout en maintenant les garanties de sécurité cryptographique. |   3    | D/V  |

| 4.9.1 | Vérifier que tous les environnements cloud sont intégrés dans des systèmes d'identité centralisés afin d'assurer une authentification cohérente. | 1 | D/V |
| 4.9.2 | Vérifier que les déploiements multi-cloud utilisent des normes d’identité fédérée (par exemple, OIDC, SAML) avec une application centralisée des politiques à travers les fournisseurs. | 2 | D/V |
| 4.9.3 | Vérifier que les transferts de données inter-cloud et hybrides utilisent un chiffrement de bout en bout avec des clés gérées par le client et qu'ils respectent les exigences de résidence des données selon la juridiction. | 2 | D/V |
| 4.9.1 | Vérifiez que l’intégration du stockage cloud utilise un chiffrement de bout en bout avec une gestion des clés contrôlée par l’agent. | 1 | D/V |
| 4.9.2 | Vérifier que les frontières de sécurité du déploiement hybride sont clairement définies avec des canaux de communication chiffrés. | 2 | D/V |

