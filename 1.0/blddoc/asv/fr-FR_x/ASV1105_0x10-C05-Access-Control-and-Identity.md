# C5 Contrôle d’accès et identité pour les composants et les utilisateurs d’IA

## Objectif de contrôle

Un contrôle d'accès efficace pour les systèmes d’IA nécessite une gestion robuste des identités, une autorisation adaptée au contexte et une mise en œuvre à l’exécution conforme aux principes du zéro-trust. Ces contrôles garantissent que les humains, les services et les agents autonomes n'interagissent qu'avec les modèles, les données et les ressources informatiques dans des périmètres explicitement autorisés, avec une vérification continue et des capacités d'audit.

---

## C5.1 Gestion des identités et de l’authentification

Établir des identités fondées sur la cryptographie pour toutes les entités, avec une authentification multifactorielle pour les opérations privilégiées.

|   #   | description                                                                                                                                                                                                                                                                                  | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.1.1 | Vérifiez que tous les utilisateurs humains et les principaux de service s'authentifient via un fournisseur d'identité d'entreprise centralisé (IdP) utilisant les protocoles OIDC/SAML, avec des correspondances identifiant-jeton uniques (aucun compte ni identifiants partagés).          |   1    | D/V  |
| 5.1.2 | Vérifier que les opérations haut-risque (déploiement de modèles, exportation de poids, accès aux données d'entraînement, modifications de la configuration de production) nécessitent une authentification multifactorielle ou une authentification renforcée avec ré-validation de session. |   1    | D/V  |
| 5.1.3 | Vérifiez que les nouveaux utilisateurs subissent une vérification d'identité conforme à NIST 800-63-3 IAL-2 ou à des normes équivalentes, avant d'obtenir l'accès au système de production.                                                                                                  |   2    |  D   |
| 5.1.4 | Vérifiez que les revues d’accès sont effectuées trimestriellement avec une détection automatisée des comptes dormants, l’application de la rotation des identifiants et des flux de désprovisionnement.                                                                                      |   2    |  V   |
| 5.1.5 | Vérifier que les agents d'IA fédérés s'authentifient par des assertions JWT signées qui ont une durée de validité maximale de 24 heures et qui incluent une preuve cryptographique d'origine.                                                                                                |   3    | D/V  |

---

## C5.2 Autorisation des ressources et le principe du moindre privilège

Mettez en place des contrôles d'accès granulaire pour toutes les ressources d'IA, avec des modèles d'autorisation explicites et des pistes d'audit.

|   #   | description                                                                                                                                                                                                                                                                                     | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.2.1 | Vérifiez que chaque ressource d'IA (ensembles de données, modèles, points de terminaison, collections vectorielles, indices d'incorporation, instances de calcul) applique des contrôles d'accès basés sur les rôles avec des listes blanches explicites et des politiques de refus par défaut. |   1    | D/V  |
| 5.2.2 | Vérifiez que les principes du moindre privilège sont appliqués par défaut, les comptes de service débutant avec des droits en lecture seule, et qu'une justification commerciale documentée est requise pour l'accès en écriture.                                                               |   1    | D/V  |
| 5.2.3 | Vérifiez que toutes les modifications du contrôle d'accès sont liées à des demandes de modification approuvées et enregistrées de manière immuable avec des horodatages, identités des acteurs, identifiants des ressources et variations des droits d'accès.                                   |   1    |  V   |
| 5.2.4 | Les étiquettes de classification des données (PII, PHI, sous contrôle d'exportation, propriétaire) se propagent automatiquement vers les ressources dérivées (embeddings, caches de prompts, sorties du modèle) avec une application cohérente de la politique.                                 |   2    |  D   |
| 5.2.5 | Vérifiez que les tentatives d'accès non autorisées et les événements d'élévation de privilèges déclenchent des alertes en temps réel avec des métadonnées contextuelles vers les systèmes SIEM dans les 5 minutes.                                                                              |   2    | D/V  |

---

## C5.3 Évaluation dynamique de la politique

Déployer des moteurs ABAC (contrôle d'accès basé sur les attributs) pour des décisions d'autorisation sensibles au contexte avec des capacités d'audit.

|   #   | description                                                                                                                                                                                                                                                                   | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.3.1 | Vérifiez que les décisions d'autorisation sont externalisées vers un moteur de politiques dédié (OPA, Cedar ou équivalent) accessible via des API authentifiées avec une protection d'intégrité cryptographique.                                                              |   1    | D/V  |
| 5.3.2 | Vérifier que les politiques évaluent des attributs dynamiques à l'exécution, y compris le niveau d'habilitation de l'utilisateur, la classification de la sensibilité des ressources, le contexte de la requête, l'isolation entre locataires et les contraintes temporelles. |   1    | D/V  |
| 5.3.3 | Vérifiez que les définitions de politiques sont sous contrôle de version, évaluées par des pairs et validées par des tests automatisés dans les pipelines CI/CD avant le déploiement en production.                                                                           |   2    |  D   |
| 5.3.4 | Vérifier que les résultats d'évaluation des politiques incluent des justifications de décision structurées et qu'ils sont transmis aux systèmes SIEM pour l'analyse de corrélation et les rapports de conformité.                                                             |   2    |  V   |
| 5.3.5 | Vérifiez que les valeurs TTL du cache des politiques ne dépassent pas 5 minutes pour les ressources à haute sensibilité et 1 heure pour les ressources standard dotées de capacités d'invalidation du cache.                                                                  |   3    | D/V  |

---

## C5.4 Sécurité à l'exécution des requêtes

Mettre en œuvre des contrôles de sécurité au niveau de la base de données avec filtrage obligatoire et des politiques de sécurité au niveau des lignes.

|   #   | description                                                                                                                                                                                                                                                                               | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.4.1 | Vérifiez que toutes les requêtes vers les bases de données vectorielles et SQL incluent des filtres de sécurité obligatoires (ID du locataire, étiquettes de sensibilité, périmètre utilisateur) imposés au niveau du moteur de la base de données, et non dans le code de l'application. |   1    | D/V  |
| 5.4.2 | Vérifier que les politiques de sécurité au niveau des lignes (RLS) et le masquage au niveau des champs sont activés avec l'héritage des politiques pour toutes les bases de données vectorielles, les indices de recherche et les ensembles de données d'entraînement.                    |   1    | D/V  |
| 5.4.3 | Vérifiez que les échecs des évaluations d'autorisation empêcheront les « confused deputy attacks » en abortant immédiatement les requêtes et en renvoyant des codes d'erreur d'autorisation explicites plutôt que de renvoyer des ensembles de résultats vides.                           |   2    |  D   |
| 5.4.4 | Vérifiez que la latence d’évaluation des politiques est surveillée en continu avec des alertes automatisées pour les conditions de délai d’expiration qui pourraient permettre un contournement de l’autorisation.                                                                        |   2    |  V   |
| 5.4.5 | Vérifiez que les mécanismes de réessai des requêtes réévaluent les politiques d'autorisation afin de prendre en compte les modifications dynamiques des autorisations au sein des sessions utilisateur actives.                                                                           |   3    | D/V  |

---

## C5.5 Filtrage de sortie et prévention de la perte de données

Déployer des contrôles de post-traitement pour prévenir l'exposition non autorisée des données dans le contenu généré par l'IA.

|   #   | description                                                                                                                                                                                                                                                  | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 5.5.1 | Vérifiez que les mécanismes de filtrage post-inférence analysent et masquent les PII (informations personnellement identifiables) non autorisées, les informations classifiées et les données propriétaires avant de livrer le contenu aux demandeurs.       |   1    | D/V  |
| 5.5.2 | Vérifiez que les citations, les références et les attributions de sources dans les sorties du modèle sont validées en fonction des droits d'accès de l'appelant et sont supprimées en cas d'accès non autorisé détecté.                                      |   1    | D/V  |
| 5.5.3 | Vérifiez que les restrictions de format de sortie (PDFs dépourvus de métadonnées, images dépourvues de métadonnées, types de fichiers approuvés) sont appliquées en fonction des niveaux d'autorisation des utilisateurs et des classifications des données. |   2    |  D   |
| 5.5.4 | Vérifiez que les algorithmes de rédaction sont déterministes, versionnés et conservent des journaux d’audit pour soutenir les enquêtes de conformité et l’analyse médico-légale.                                                                             |   2    |  V   |
| 5.5.5 | Vérifiez que les événements de redaction à haut risque génèrent des journaux adaptatifs qui incluent des hachages cryptographiques du contenu d'origine pour la récupération médico-légale sans exposition des données.                                      |   3    |  V   |

---

## C5.6 Isolement multi-locataires

Assurer l'isolation cryptographique et logique entre les locataires dans une infrastructure d'IA partagée.

|   #   | description                                                                                                                                                                                                                                                           | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.6.1 | Vérifier que les espaces mémoire, les stockages d'embeddings, les entrées de cache et les fichiers temporaires sont isolés par espace de noms pour chaque locataire, avec une purge sécurisée lors de la suppression du locataire ou de la terminaison de la session. |   1    | D/V  |
| 5.6.2 | Vérifiez que chaque requête API comprend un identifiant de locataire authentifié qui est validé cryptographiquement par rapport au contexte de session et aux droits d'accès de l'utilisateur.                                                                        |   1    | D/V  |
| 5.6.3 | Vérifiez que les politiques réseau mettent en œuvre des règles de refus par défaut pour la communication inter-locataires au sein des maillages de services et des plateformes d'orchestration de conteneurs.                                                         |   2    |  D   |
| 5.6.4 | Vérifiez que les clés de chiffrement sont uniques par locataire avec prise en charge des clés gérées par le client (CMK) et l'isolation cryptographique entre les stockages de données des locataires.                                                                |   3    |  D   |

---

## C5.7 Autorisation d'agent autonome

Contrôler les permissions des agents d'IA et des systèmes autonomes grâce à des jetons de capacité à portée limitée et à une autorisation continue.

|   #   | description                                                                                                                                                                                                                                                                    | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 5.7.1 | Assurez-vous que les agents autonomes reçoivent des jetons de capacité à portée limitée qui énumèrent explicitement les actions autorisées, les ressources accessibles, les limites temporelles et les contraintes opérationnelles.                                            |   1    | D/V  |
| 5.7.2 | Vérifiez que les capacités à haut risque (accès au système de fichiers, exécution de code, appels d'API externes, transactions financières) sont désactivées par défaut et nécessitent des autorisations explicites pour leur activation avec des justifications commerciales. |   1    | D/V  |
| 5.7.3 | Vérifiez que les jetons de capacité sont liés aux sessions utilisateur, qu'ils disposent d'une protection d'intégrité cryptographique et assurez-vous qu'ils ne peuvent pas être conservés ni réutilisés dans des scénarios hors ligne.                                        |   2    |  D   |
| 5.7.4 | Vérifiez que les actions initiées par l'agent font l'objet d'une autorisation secondaire via le moteur de politiques ABAC, avec une évaluation complète du contexte et une journalisation d'audit.                                                                             |   2    |  V   |
| 5.7.5 | Vérifiez que les conditions d'erreur des agents et la gestion des exceptions incluent des informations sur la portée des capacités afin de soutenir l'analyse des incidents et l'enquête médico-légale.                                                                        |   3    |  V   |

---

## Références

### Normes et Cadres

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Guides de mise en œuvre

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Sécurité IA-spécifique

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

