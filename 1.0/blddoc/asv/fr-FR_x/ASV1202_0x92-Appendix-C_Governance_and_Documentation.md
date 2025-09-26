# Annexe C : Gouvernance et documentation de la sécurité de l'IA (réorganisé)

## Objectif

Cette annexe fournit les exigences fondamentales pour établir des structures organisationnelles, des politiques, de la documentation et des processus afin de gouverner la sécurité de l'IA tout au long du cycle de vie du système.

---

## AC.1 Adoption du cadre de gestion des risques liés à l'IA

|   #    | Description                                                                                                                           | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.1.1 | Vérifiez qu'une méthodologie d'évaluation des risques spécifique à l'IA est documentée et mise en œuvre.                              |   1    | D/V  |
| AC.1.2 | Vérifiez que des évaluations des risques sont effectuées aux points clés du cycle de vie de l'IA et avant des changements importants. |   2    |  D   |
| AC.1.3 | Vérifiez que le cadre de gestion des risques est conforme aux normes établies (par exemple, NIST AI RMF).                             |   3    | D/V  |

---

## AC.2 Politique et procédures de sécurité de l'IA

|   #    | Description                                                                                                                                        | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.2.1 | Vérifiez que des politiques de sécurité de l'IA documentées existent.                                                                              |   1    | D/V  |
| AC.2.2 | Vérifiez que les politiques sont examinées et mises à jour au moins une fois par an et après des changements significatifs du paysage des menaces. |   2    |  D   |
| AC.2.3 | Vérifiez que les politiques couvrent toutes les catégories AISVS et les exigences réglementaires applicables.                                      |   3    | D/V  |

---

## AC.3 Rôles et responsabilités pour la sécurité de l'IA

|   #    | Description                                                                                                           | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.3.1 | Vérifiez que les rôles et responsabilités en matière de sécurité de l'IA sont documentés.                             |   1    | D/V  |
| AC.3.2 | Vérifiez que les personnes responsables possèdent une expertise en sécurité appropriée.                               |   2    |  D   |
| AC.3.3 | Vérifiez qu'un comité d'éthique de l'IA ou un conseil de gouvernance est établi pour les systèmes d'IA à haut risque. |   3    | D/V  |

---

## AC.4 Application des lignes directrices pour une IA éthique

|   #    | Description                                                                                    | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.4.1 | Vérifiez que des directives éthiques pour le développement et le déploiement de l'IA existent. |   1    | D/V  |
| AC.4.2 | Vérifiez que des mécanismes sont en place pour détecter et signaler les violations éthiques.   |   2    |  D   |
| AC.4.3 | Vérifiez que des revues éthiques régulières des systèmes d'IA déployés sont effectuées.        |   3    | D/V  |

---

## AC.5 Surveillance de la conformité réglementaire en matière d'IA

|   #    | Description                                                                                                       | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.5.1 | Vérifiez que des processus existent pour identifier les réglementations applicables à l'IA.                       |   1    | D/V  |
| AC.5.2 | Vérifiez que la conformité à toutes les exigences réglementaires est évaluée.                                     |   2    |  D   |
| AC.5.3 | Vérifiez que les changements réglementaires déclenchent des revues et des mises à jour rapides des systèmes d’IA. |   3    | D/V  |

---

## AC.6 Gouvernance, Documentation et Processus des Données d’Entraînement

### AC.6.1 Approvisionnement en données et diligence raisonnable

|    #     | Description                                                                                                                                                                                                                                                                                                                                                                                        | Niveau | Rôle |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.6.1.1 | Vérifiez que seuls les ensembles de données validés pour leur qualité, leur représentativité, leur approvisionnement éthique et leur conformité aux licences sont autorisés, réduisant ainsi les risques d'empoisonnement, de biais intégrés et de violation de la propriété intellectuelle.                                                                                                       |   1    | D/V  |
| AC.6.1.2 | Vérifiez que les fournisseurs de données tiers, y compris les prestataires de modèles pré-entraînés et de jeux de données externes, font l'objet d'une diligence raisonnable en matière de sécurité, de confidentialité, d'approvisionnement éthique et de qualité des données avant que leurs données ou modèles ne soient intégrés.                                                              |   2    | D/V  |
| AC.6.1.3 | Vérifier que les transferts externes utilisent TLS/authentification et des contrôles d'intégrité.                                                                                                                                                                                                                                                                                                  |   1    |  D   |
| AC.6.1.4 | Vérifiez que les sources de données à haut risque (par exemple, les ensembles de données open-source à provenance inconnue, les fournisseurs non vérifiés) font l'objet d'un examen renforcé, tel qu'une analyse en environnement isolé (sandbox), des contrôles approfondis de qualité/biais et une détection ciblée des empoisonnements, avant leur utilisation dans des applications sensibles. |   2    | D/V  |
| AC.6.1.5 | Vérifiez que les modèles pré-entraînés obtenus auprès de tiers sont évalués pour les biais intégrés, les portes dérobées potentielles, l'intégrité de leur architecture et la provenance de leurs données d'entraînement originales avant l'affinage ou le déploiement.                                                                                                                            |   3    | D/V  |

### AC.6.2 Gestion des Biais et de l’Équité

|    #     | Description                                                                                                                                                                                                                                                                                                                                                                                            | Niveau | Rôle |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| AC.6.2.1 | Vérifiez que les ensembles de données sont analysés pour détecter un déséquilibre de représentation et des biais potentiels concernant des attributs légalement protégés (par exemple, la race, le genre, l’âge) ainsi que d’autres caractéristiques éthiquement sensibles pertinentes pour le domaine d’application du modèle (par exemple, le statut socio-économique, la localisation).             |   1    | D/V  |
| AC.6.2.2 | Vérifier que les biais identifiés sont atténués via des stratégies documentées telles que le rééquilibrage, l'augmentation ciblée des données, les ajustements algorithmiques (par exemple, les techniques de pré-traitement, traitement en cours, post-traitement) ou le re-pondération, et que l'impact de cette atténuation sur l'équité ainsi que sur la performance globale du modèle est évalué. |   2    | D/V  |
| AC.6.2.3 | Vérifiez que les métriques d'équité post-formation sont évaluées et documentées.                                                                                                                                                                                                                                                                                                                       |   2    | D/V  |
| AC.6.2.4 | Vérifiez qu'une politique de gestion des biais tout au long du cycle de vie attribue des propriétaires et une cadence de révision.                                                                                                                                                                                                                                                                     |   3    | D/V  |

### AC.6.3 Gouvernance de l'étiquetage et de l'annotation

|     #     | Description                                                                                                                                                                                                                                                                                           | Niveau | Rôle |
| :-------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.6.3.1  | Vérifiez que la qualité de l'étiquetage/annotation est assurée par des contrôles croisés des examinateurs ou un consensus.                                                                                                                                                                            |   2    | D/V  |
| AC.6.3.2  | Vérifiez que des fiches de données sont maintenues pour les ensembles de données d'entraînement significatifs, détaillant les caractéristiques, motivations, composition, processus de collecte, prétraitement, licences et utilisations recommandées/déconseillées.                                  |   2    | D/V  |
| AC.6.3.3  | Vérifiez que les fiches de données documentent les risques de biais, les déséquilibres démographiques et les considérations éthiques pertinentes pour le jeu de données.                                                                                                                              |   2    | D/V  |
| AC.6.3.4  | Vérifiez que les fiches de données sont versionnées parallèlement aux ensembles de données et mises à jour chaque fois que l'ensemble de données est modifié.                                                                                                                                         |   2    | D/V  |
| AC.6.3.5  | Vérifiez que les fiches de données sont examinées et approuvées à la fois par des parties prenantes techniques et non techniques (par exemple, conformité, éthique, experts du domaine).                                                                                                              |   2    | D/V  |
| AC.6.3.6  | Vérifiez que la qualité de l'étiquetage/annotation est garantie grâce à des directives claires, des vérifications croisées par des examinateurs, des mécanismes de consensus (par exemple, la surveillance de l'accord entre les annotateurs) et des processus définis pour résoudre les divergences. |   2    | D/V  |
| AC.6.3.7  | Vérifiez que les étiquettes critiques pour la sécurité, la sûreté ou l'équité (par exemple, l'identification de contenu toxique, des résultats médicaux critiques) font l'objet d'une révision indépendante doublée obligatoire ou d'une vérification rigoureuse équivalente.                         |   3    | D/V  |
| AC.6.3.8  | Vérifiez que les guides d'étiquetage et les instructions sont complets, soumis à un contrôle de version et examinés par les pairs.                                                                                                                                                                    |   2    | D/V  |
| AC.6.3.9  | Vérifiez que les schémas de données pour les étiquettes sont clairement définis et soumis à un contrôle de version.                                                                                                                                                                                   |   2    | D/V  |
| AC.6.3.10 | Vérifiez que les flux de travail de labellisation externalisés ou crowdsourcés incluent des mesures techniques/procédurales pour garantir la confidentialité des données, leur intégrité, la qualité des étiquettes, et prévenir les fuites de données.                                               |   2    | D/V  |
| AC.6.3.11 | Vérifiez que tout le personnel impliqué dans l'annotation des données a été soumis à une vérification des antécédents et formé à la sécurité et à la confidentialité des données.                                                                                                                     |   2    | D/V  |
| AC.6.3.12 | Vérifiez que tout le personnel d'annotation signe des accords de confidentialité et de non-divulgation.                                                                                                                                                                                               |   2    | D/V  |
| AC.6.3.13 | Vérifiez que les plateformes d'annotation appliquent des contrôles d'accès et surveillent les menaces internes.                                                                                                                                                                                       |   2    | D/V  |

### AC.6.4 Portails de qualité des jeux de données et quarantaine

|    #     | Description                                                                                                                                                                                                                                                                                                                                               | Niveau | Rôle |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.6.4.1 | Vérifiez que les ensembles de données défaillants sont mis en quarantaine avec des pistes d'audit.                                                                                                                                                                                                                                                        |   2    | D/V  |
| AC.6.4.2 | Vérifiez que les passerelles de qualité bloquent les ensembles de données de qualité inférieure, sauf si des exceptions sont approuvées.                                                                                                                                                                                                                  |   2    | D/V  |
| AC.6.4.3 | Vérifiez que les contrôles ponctuels manuels effectués par des experts du domaine couvrent un échantillon statistiquement significatif (par exemple, ≥1 % ou 1 000 échantillons, selon la valeur la plus élevée, ou tel que déterminé par l’évaluation des risques) afin d’identifier les problèmes de qualité subtils non détectés par l’automatisation. |   2    |  V   |

### AC.6.5 Détection de menaces/empoisonnement et dérive

|    #     | Description                                                                                                                   | Niveau | Rôle |
| :------: | ----------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.6.5.1 | Vérifiez que les échantillons signalés déclenchent un examen manuel avant l'entraînement.                                     |   2    | D/V  |
| AC.6.5.2 | Vérifiez que les résultats alimentent le dossier de sécurité du modèle et informent le renseignement continu sur les menaces. |   2    |  V   |
| AC.6.5.3 | Vérifiez que la logique de détection est mise à jour avec les nouvelles informations sur les menaces.                         |   3    | D/V  |
| AC.6.5.4 | Vérifiez que les pipelines d'apprentissage en ligne surveillent la dérive de distribution.                                    |   3    | D/V  |

### AC.6.6 Suppression, Consentement, Droits, Conservation et Conformité

|     #     | Description                                                                                                                                                                                                                                                                                                                                                         | Niveau | Rôle |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.6.6.1  | Vérifiez que les flux de travail de suppression des données d'entraînement effacent les données primaires et dérivées et évaluent l'impact sur le modèle, et que l'impact sur les modèles concernés est évalué et, si nécessaire, corrigé (par exemple, par un réentraînement ou un recalibrage).                                                                   |   1    | D/V  |
| AC.6.6.2  | Vérifiez que des mécanismes sont en place pour suivre et respecter la portée et le statut du consentement de l'utilisateur (et des retraits) concernant les données utilisées pour l'entraînement, et que le consentement est validé avant que les données ne soient intégrées dans de nouveaux processus d'entraînement ou des mises à jour importantes du modèle. |   2    |  D   |
| AC.6.6.3  | Vérifiez que les flux de travail sont testés annuellement et consignés.                                                                                                                                                                                                                                                                                             |   2    |  V   |
| AC.6.6.4  | Vérifiez que des périodes de rétention explicites sont définies pour tous les ensembles de données d'entraînement.                                                                                                                                                                                                                                                  |   1    | D/V  |
| AC.6.6.5  | Vérifiez que les ensembles de données sont automatiquement expirés, supprimés ou examinés pour suppression à la fin de leur cycle de vie.                                                                                                                                                                                                                           |   2    | D/V  |
| AC.6.6.6  | Vérifiez que les actions de conservation et de suppression sont enregistrées et vérifiables.                                                                                                                                                                                                                                                                        |   2    | D/V  |
| AC.6.6.7  | Vérifiez que les exigences relatives à la résidence des données et au transfert transfrontalier sont identifiées et appliquées pour tous les ensembles de données.                                                                                                                                                                                                  |   2    | D/V  |
| AC.6.6.8  | Vérifiez que les réglementations spécifiques à chaque secteur (par exemple, la santé, la finance) sont identifiées et prises en compte dans la gestion des données.                                                                                                                                                                                                 |   2    | D/V  |
| AC.6.6.9  | Vérifiez que la conformité avec les lois sur la vie privée pertinentes (par exemple, GDPR, CCPA) est documentée et examinée régulièrement.                                                                                                                                                                                                                          |   2    | D/V  |
| AC.6.6.10 | Vérifiez que des mécanismes existent pour répondre aux demandes des personnes concernées concernant l'accès, la rectification, la restriction ou l'opposition.                                                                                                                                                                                                      |   2    | D/V  |
| AC.6.6.11 | Vérifiez que les demandes sont enregistrées, suivies et satisfaites dans les délais légaux impartis.                                                                                                                                                                                                                                                                |   2    | D/V  |
| AC.6.6.12 | Vérifiez que les processus relatifs aux droits des personnes concernées sont testés et révisés régulièrement pour en assurer l'efficacité.                                                                                                                                                                                                                          |   2    | D/V  |

### AC.6.7 Gestion des versions et des changements

|    #     | Description                                                                                                                                                                          | Niveau | Rôle |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| AC.6.7.1 | Vérifiez qu'une analyse d'impact est réalisée avant de mettre à jour ou de remplacer une version de jeu de données, en couvrant la performance du modèle, l'équité et la conformité. |   2    | D/V  |
| AC.6.7.2 | Vérifiez que les résultats de l'analyse d'impact sont documentés et examinés par les parties prenantes concernées.                                                                   |   2    | D/V  |
| AC.6.7.3 | Vérifiez que des plans de retour en arrière existent au cas où les nouvelles versions introduiraient des risques inacceptables ou des régressions.                                   |   2    | D/V  |

### AC.6.8 Gouvernance des données synthétiques

|    #     | Description                                                                                                                                                                                                            | Niveau | Rôle |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.6.8.1 | Vérifiez que le processus de génération, les paramètres et l'utilisation prévue des données synthétiques sont documentés.                                                                                              |   2    | D/V  |
| AC.6.8.2 | Vérifiez que les données synthétiques ont fait l'objet d'une évaluation des risques concernant les biais, les fuites de confidentialité et les problèmes de représentation avant leur utilisation dans l'entraînement. |   2    | D/V  |

### AC.6.9 Surveillance des accès

|    #     | Description                                                                                                                                                                             | Niveau | Rôle |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.6.9.1 | Vérifiez que les journaux d'accès sont régulièrement examinés pour détecter des motifs inhabituels, tels que des exportations importantes ou des accès depuis de nouveaux emplacements. |   2    | D/V  |
| AC.6.9.2 | Vérifiez que des alertes sont générées pour les événements d'accès suspects et qu'elles sont examinées rapidement.                                                                      |   2    | D/V  |

### AC.6.10 Gouvernance de l'entraînement adversarial

|     #     | Description                                                                                                                                                                                                                          | Niveau | Rôle |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| AC.6.10.1 | Vérifiez que si l'entraînement adversarial est utilisé, la génération, la gestion et la version des ensembles de données adversariales sont documentées et contrôlées.                                                               |   2    | D/V  |
| AC.6.10.2 | Vérifier que l'impact de l'entraînement à la robustesse adversariale sur les performances du modèle (contre des entrées à la fois propres et adversariales) ainsi que sur les métriques d'équité est évalué, documenté et surveillé. |   3    | D/V  |
| AC.6.10.3 | Vérifiez que les stratégies d'entraînement adversarial et de robustesse sont périodiquement révisées et mises à jour pour contrer les techniques d'attaque adversariales en évolution.                                               |   3    | D/V  |

---

## AC.7 Gouvernance et documentation du cycle de vie du modèle

|   #    | Description                                                                                                                                                                                                         | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.7.1 | Vérifiez que tous les artefacts du modèle utilisent le versionnage sémantique (MAJOR.MINOR.PATCH) avec des critères documentés précisant quand chaque composant de version est incrémenté.                          |   2    | D/V  |
| AC.7.2 | Vérifiez que les déploiements d'urgence nécessitent une évaluation documentée des risques de sécurité et une approbation de la part d'une autorité de sécurité pré-désignée dans des délais préalablement convenus. |   2    | D/V  |
| AC.7.3 | Vérifiez que les artefacts de restauration (versions précédentes du modèle, configurations, dépendances) sont conservés conformément aux politiques organisationnelles.                                             |   2    |  V   |
| AC.7.4 | Vérifiez que l'accès au journal d'audit nécessite une autorisation appropriée et que toutes les tentatives d'accès sont enregistrées avec l'identité de l'utilisateur et un horodatage.                             |   2    | D/V  |
| AC.7.5 | Vérifiez que les artefacts des modèles retirés sont conservés conformément aux politiques de conservation des données.                                                                                              |   1    | D/V  |

---

## Gouvernance de la sécurité des invites, des entrées et des sorties AC.8

### AC.8.1 Défense contre l'injection de requêtes

|    #     | Description                                                                                                                                                                                                                                                        | Niveau | Rôle |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| AC.8.1.1 | Vérifiez que les tests d’évaluation adversariale (par exemple, les invites Red Team « many-shot ») sont effectués avant chaque publication de modèle ou de modèle d’invite, avec des seuils de taux de réussite et des bloqueurs automatisés pour les régressions. |   2    | D/V  |
| AC.8.1.2 | Vérifiez que toutes les mises à jour des règles de filtrage des invites, les versions des modèles classificateurs et les modifications des listes de blocage sont contrôlées par version et vérifiables.                                                           |   3    | D/V  |

### AC.8.2 Résistance aux exemples contradictoires

|    #     | Description                                                                                                                                                                                | Niveau | Rôle |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| AC.8.2.1 | Vérifiez que les métriques de robustesse (taux de réussite des suites d'attaques connues) sont suivies au fil du temps via l'automatisation et que les régressions déclenchent une alerte. |   3    | D/V  |

### AC.8.3 Filtrage du contenu et des politiques

|    #     | Description                                                                                                                                                                                                | Niveau | Rôle |
| :------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.8.3.1 | Vérifiez que le modèle de filtrage ou l'ensemble de règles est réentraîné/mis à jour au moins trimestriellement, en intégrant les nouveaux schémas de jailbreak ou de contournement de politique observés. |   2    |  D   |

### AC.8.4 Limitation du taux d'entrée et prévention des abus

|    #     | Description                                                                                                               | Niveau | Rôle |
| :------: | ------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.8.4.1 | Vérifiez que les journaux de prévention des abus sont conservés et examinés pour détecter les nouveaux schémas d'attaque. |   3    |  V   |

### AC.8.5 Provenance et attribution des entrées

|    #     | Description                                                                                                                                                     | Niveau | Rôle |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.8.5.1 | Vérifiez que toutes les entrées utilisateur sont étiquetées avec des métadonnées (ID utilisateur, session, source, horodatage, adresse IP) lors de l'ingestion. |   1    | D/V  |
| AC.8.5.2 | Vérifiez que les métadonnées de provenance sont conservées et vérifiables pour toutes les entrées traitées.                                                     |   2    | D/V  |
| AC.8.5.3 | Vérifiez que les sources d’entrée anormales ou non fiables sont signalées et soumises à un contrôle accru ou à un blocage.                                      |   2    | D/V  |

---

## AC.9 Validation multimodale, MLOps et gouvernance de l'infrastructure

### AC.9.1 Pipeline de validation de la sécurité multimodale

|    #     | Description                                                                                                                                                                                                                                                                                      | Niveau | Rôle |
| :------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| AC.9.1.1 | Vérifiez que les classificateurs de contenu spécifiques à chaque modalité sont mis à jour selon les calendriers documentés (au minimum trimestriellement) avec de nouveaux schémas de menaces, des exemples adverses, et que les performances sont maintenues au-dessus des seuils de référence. |   3    | D/V  |

### AC.9.2 Sécurité CI/CD et de la Compilation

|    #     | Description                                                                                                                                                       | Niveau | Rôle |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.2.1 | Vérifiez que l'infrastructure en tant que code est analysée à chaque commit, et que les fusions sont bloquées en cas de détections critiques ou de haute gravité. |   1    | D/V  |
| AC.9.2.2 | Vérifiez que les pipelines CI/CD utilisent des identités à courte durée de vie et à champ d'application limité pour accéder aux secrets et à l'infrastructure.    |   2    | D/V  |
| AC.9.2.3 | Vérifiez que les environnements de développement sont isolés des réseaux et des données de production.                                                            |   2    | D/V  |

### AC.9.3 Sécurité des conteneurs et des images

|    #     | Description                                                                                                                                                                                                       | Niveau | Rôle |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.3.1 | Vérifiez que les images de conteneurs sont analysées pour bloquer les secrets codés en dur (par exemple, les clés API, les identifiants, les certificats).                                                        |   2    | D/V  |
| AC.9.3.2 | Vérifiez que les images des conteneurs sont analysées conformément aux calendriers organisationnels, avec les vulnérabilités CRITIQUES bloquant le déploiement en fonction des seuils de risque organisationnels. |   1    | D/V  |

### AC.9.4 Surveillance, Alertes et SIEM

|    #     | Description                                                                                                                                                                       | Niveau | Rôle |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.4.1 | Vérifiez que les alertes de sécurité s'intègrent aux plateformes SIEM (Splunk, Elastic ou Sentinel) en utilisant les formats CEF ou STIX/TAXII avec un enrichissement automatisé. |   2    |  V   |

### AC.9.5 Gestion des vulnérabilités

|    #     | Description                                                                                                                                                                                        | Niveau | Rôle |
| :------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.5.1 | Vérifiez que les vulnérabilités de gravité ÉLEVÉE sont corrigées conformément aux délais de gestion des risques organisationnels avec des procédures d'urgence pour les CVE activement exploitées. |   2    | D/V  |

### AC.9.6 Contrôle de la Configuration et des Dérives

|    #     | Description                                                                                                                                                                                                                       | Niveau | Rôle |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.6.1 | Vérifiez que la dérive de configuration est détectée à l'aide d'outils (Chef InSpec, AWS Config) conformément aux exigences de surveillance organisationnelles avec un retour automatique en cas de modifications non autorisées. |   2    | D/V  |

### AC.9.7 Durcissement de l'Environnement de Production

|    #     | Description                                                                                                                                                                                                                         | Niveau | Rôle |
| :------: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.7.1 | Vérifiez que les environnements de production bloquent l'accès SSH, désactivent les points de terminaison de débogage et exigent des demandes de modification avec des exigences de préavis organisationnel, sauf en cas d'urgence. |   2    | D/V  |

### AC.9.8 Portes de Promotion de Version

|    #     | Description                                                                                                                                                                             | Niveau | Rôle |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.8.1 | Vérifiez que les points de contrôle de promotion incluent des tests de sécurité automatisés (SAST, DAST, analyse des conteneurs) avec zéro résultat CRITIQUE requis pour l'approbation. |   2    | D/V  |

### AC.9.9 Surveillance de la charge de travail, de la capacité et des coûts

|    #     | Description                                                                                                                                                                                                                                                     | Niveau | Rôle |
| :------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.9.1 | Vérifiez que l'utilisation du GPU/TPU est surveillée avec des alertes déclenchées aux seuils définis par l'organisation et que la mise à l'échelle automatique ou la répartition de la charge est activée en fonction des politiques de gestion de la capacité. |   1    | D/V  |
| AC.9.9.2 | Vérifiez que les métriques de charge de travail de l'IA (latence d'inférence, débit, taux d'erreur) sont collectées conformément aux exigences de surveillance organisationnelle et corrélées avec l'utilisation de l'infrastructure.                           |   1    | D/V  |
| AC.9.9.3 | Vérifiez que la surveillance des coûts suit les dépenses par charge de travail/locataire avec des alertes basées sur les seuils budgétaires organisationnels et des contrôles automatisés pour les dépassements de budget.                                      |   2    |  V   |
| AC.9.9.4 | Vérifiez que la planification de capacité utilise des données historiques avec des périodes de prévision définies par l'organisation et un approvisionnement automatisé des ressources basé sur les modèles de demande.                                         |   3    |  V   |

### AC.9.10 Approbations et pistes d’audit

|     #     | Description                                                                                                                                                                                    | Niveau | Rôle |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.10.1 | Vérifiez que la promotion de l’environnement nécessite l’approbation du personnel autorisé défini organisationnellement, avec des signatures cryptographiques et des pistes d’audit immuables. |   1    | D/V  |

### AC.9.11 Gouvernance IaC

|     #     | Description                                                                                                                                                                                                   | Niveau | Rôle |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.11.1 | Vérifiez que les modifications de l'infrastructure en tant que code nécessitent une relecture par les pairs avec des tests automatisés et une analyse de sécurité avant la fusion dans la branche principale. |   2    | D/V  |

### AC.9.12 Gestion des données en environnement non productif

|     #     | Description                                                                                                                                                                                                                                                                                         | Niveau | Rôle |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.12.1 | Vérifiez que les données non destinées à la production sont anonymisées conformément aux exigences de confidentialité organisationnelles, à la génération de données synthétiques ou à un masquage complet des données avec suppression des informations personnelles identifiables (PII) vérifiée. |   2    | D/V  |

### AC.9.13 Sauvegarde et récupération après sinistre

|     #     | Description                                                                                                                                                                                                                          | Niveau | Rôle |
| :-------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| AC.9.13.1 | Vérifiez que les configurations d'infrastructure sont sauvegardées conformément aux calendriers de sauvegarde organisationnels vers des régions géographiquement séparées avec la mise en œuvre de la stratégie de sauvegarde 3-2-1. |   1    | D/V  |
| AC.9.13.2 | Vérifiez que les procédures de récupération sont testées et validées par des tests automatisés conformément aux calendriers organisationnels, avec des objectifs de RTO et RPO répondant aux exigences de l'organisation.            |   2    |  V   |
| AC.9.13.3 | Vérifiez que la reprise après sinistre inclut des runbooks spécifiques à l'IA avec la restauration des poids du modèle, la reconstruction du cluster GPU et la cartographie des dépendances des services.                            |   3    |  V   |

### AC.9.14 Conformité et Documentation

|     #     | Description                                                                                                                                                                                                                 | Niveau | Rôle |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.14.1 | Vérifiez que la conformité de l'infrastructure est évaluée selon les calendriers organisationnels en fonction des contrôles SOC 2, ISO 27001 ou FedRAMP avec une collecte automatisée des preuves.                          |   2    | D/V  |
| AC.9.14.2 | Vérifiez que la documentation de l'infrastructure comprend des diagrammes réseau, des cartes de flux de données et des modèles de menace mis à jour conformément aux exigences de gestion des changements organisationnels. |   2    |  V   |
| AC.9.14.3 | Vérifiez que les changements d'infrastructure font l'objet d'une évaluation automatisée de l'impact sur la conformité avec des flux de travail d'approbation réglementaire pour les modifications à haut risque.            |   3    | D/V  |

### AC.9.15 Matériel et chaîne d'approvisionnement

|     #     | Description                                                                                                                                                                                                            | Niveau | Rôle |
| :-------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.15.1 | Vérifiez que le microprogramme de l'accélérateur AI (BIOS GPU, microprogramme TPU) est vérifié avec des signatures cryptographiques et mis à jour conformément aux délais de gestion des correctifs de l'organisation. |   2    | D/V  |
| AC.9.15.2 | Vérifiez que la chaîne d'approvisionnement du matériel IA inclut une vérification de la provenance avec des certificats du fabricant et une validation de l'emballage inviolable.                                      |   3    |  V   |

### AC.9.16 Stratégie Cloud et Portabilité

|     #     | Description                                                                                                                                                                                                                 | Niveau | Rôle |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.16.1 | Vérifiez que la prévention du verrouillage fournisseur cloud inclut une infrastructure en tant que code portable, des API standardisées, et des capacités d'exportation de données avec des outils de conversion de format. |   3    |  V   |
| AC.9.16.2 | Vérifiez que l’optimisation des coûts multi-cloud inclut des contrôles de sécurité empêchant la prolifération des ressources ainsi que les frais de transfert de données inter-cloud non autorisés.                         |   3    |  V   |

### AC.9.17 GitOps et Auto-réparation

|     #     | Description                                                                                                                                                                                              | Niveau | Rôle |
| :-------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.17.1 | Vérifiez que les dépôts GitOps exigent des commits signés avec des clés GPG et des règles de protection des branches empêchant les pushes directs vers les branches principales.                         |   2    | D/V  |
| AC.9.17.2 | Vérifiez que l'infrastructure auto-réparatrice inclut la corrélation des événements de sécurité avec une réponse automatisée aux incidents et des flux de travail de notification aux parties prenantes. |   3    |  V   |

### AC.9.18 Zero-Trust, Agents, Provisionnement et Attestation de Résidence

|     #     | Description                                                                                                                                                                             | Niveau | Rôle |
| :-------: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AC.9.18.1 | Vérifiez que l'accès aux ressources cloud inclut une vérification zero-trust avec une authentification continue.                                                                        |   2    | D/V  |
| AC.9.18.2 | Vérifiez que la provision automatisée de l'infrastructure inclut la validation des politiques de sécurité avec un blocage du déploiement pour les configurations non conformes.         |   2    | D/V  |
| AC.9.18.3 | Vérifiez que l'approvisionnement automatisé de l'infrastructure valide les politiques de sécurité pendant le CI/CD, avec les configurations non conformes bloquées lors du déploiement. |   2    | D/V  |
| AC.9.18.4 | Vérifiez que les exigences de résidence des données sont respectées par une attestation cryptographique des emplacements de stockage.                                                   |   3    | D/V  |
| AC.9.18.5 | Vérifiez que les évaluations de sécurité du fournisseur cloud incluent une modélisation des menaces spécifique à l'agent et une évaluation des risques.                                 |   3    | D/V  |

