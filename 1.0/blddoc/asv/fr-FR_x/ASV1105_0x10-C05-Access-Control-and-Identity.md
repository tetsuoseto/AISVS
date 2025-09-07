# C5 Contrôle d'accès et identité pour les composants et utilisateurs d'IA

## Objectif de contrôle

Un contrôle d'accès efficace pour les systèmes d'IA nécessite une gestion robuste des identités, une autorisation contextuelle et une application en temps réel conformément aux principes du zero-trust. Ces contrôles garantissent que les humains, services et agents autonomes n'interagissent avec les modèles, les données et les ressources informatiques que dans des périmètres explicitement accordés, avec des capacités de vérification continue et d'audit.

---

## C5.1 Gestion des identités et authentification

Établir des identités sécurisées par cryptographie pour toutes les entités avec authentification multi-facteurs pour les opérations privilégiées.

|   #   | Description                                                                                                                                                                                                                                                                                          | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.1.1 | Vérifiez que tous les utilisateurs humains et principaux de service s’authentifient via un fournisseur d’identité d’entreprise centralisé (IdP) en utilisant les protocoles OIDC/SAML avec des correspondances uniques identité-vers-token (pas de comptes ou de données d’identification partagés). |   1    | D/V  |
| 5.1.2 | Vérifiez que les opérations à haut risque (déploiement de modèle, exportation de poids, accès aux données d'entraînement, modifications de la configuration de production) nécessitent une authentification multifacteur ou une authentification renforcée avec revalidation de session.             |   1    | D/V  |
| 5.1.3 | Vérifiez que les nouveaux responsables subissent une vérification d'identité conforme à la norme NIST 800-63-3 IAL-2 ou à des normes équivalentes avant d'obtenir l'accès au système de production.                                                                                                  |   2    |  D   |
| 5.1.4 | Vérifiez que les revues d'accès sont effectuées trimestriellement avec une détection automatisée des comptes inactifs, l'application de la rotation des identifiants, et des workflows de suppression des accès.                                                                                     |   2    |  V   |
| 5.1.5 | Vérifiez que les agents d'IA fédérés s'authentifient via des assertions JWT signées ayant une durée de vie maximale de 24 heures et incluant une preuve cryptographique d'origine.                                                                                                                   |   3    | D/V  |

---

## C5.2 Autorisation des ressources et moindre privilège

Mettez en œuvre des contrôles d'accès précis pour toutes les ressources d'IA avec des modèles de permission explicites et des pistes d'audit.

|   #   | Description                                                                                                                                                                                                                                                                                            | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 5.2.1 | Vérifiez que chaque ressource d'IA (ensembles de données, modèles, points de terminaison, collections vectorielles, indices d'incorporation, instances de calcul) applique des contrôles d'accès basés sur les rôles avec des listes d'autorisations explicites et des politiques par défaut de refus. |   1    | D/V  |
| 5.2.2 | Vérifiez que les principes du moindre privilège sont appliqués par défaut avec les comptes de service, en commençant par des permissions en lecture seule et en exigeant une justification commerciale documentée pour l'accès en écriture.                                                            |   1    | D/V  |
| 5.2.3 | Vérifiez que toutes les modifications du contrôle d'accès sont liées à des demandes de changement approuvées et consignées de manière immuable avec des horodatages, des identités d'acteurs, des identifiants de ressources et des deltas de permissions.                                             |   1    |  V   |
| 5.2.4 | Vérifiez que les étiquettes de classification des données (PII, PHI, contrôle à l'exportation, propriétaire) se propagent automatiquement aux ressources dérivées (embeddings, caches de prompts, sorties de modèles) avec une application cohérente de la politique.                                  |   2    |  D   |
| 5.2.5 | Vérifiez que les tentatives d'accès non autorisées et les événements d'escalade de privilèges déclenchent des alertes en temps réel avec des métadonnées contextuelles vers les systèmes SIEM dans un délai de 5 minutes.                                                                              |   2    | D/V  |

---

## C5.3 Évaluation Dynamique des Politiques

Déployez des moteurs de contrôle d'accès basé sur les attributs (ABAC) pour des décisions d'autorisation contextuelles avec des capacités d'audit.

|   #   | Description                                                                                                                                                                                                                                                                 | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.3.1 | Vérifiez que les décisions d'autorisation sont externalisées vers un moteur de politique dédié (OPA, Cedar ou équivalent) accessible via des API authentifiées avec une protection d'intégrité cryptographique.                                                             |   1    | D/V  |
| 5.3.2 | Vérifiez que les politiques évaluent les attributs dynamiques à l'exécution, y compris le niveau d'habilitation de l'utilisateur, la classification de la sensibilité des ressources, le contexte de la requête, l'isolation des locataires et les contraintes temporelles. |   1    | D/V  |
| 5.3.3 | Vérifiez que les définitions de politique sont contrôlées par version, évaluées par des pairs et validées par des tests automatisés dans les pipelines CI/CD avant le déploiement en production.                                                                            |   2    |  D   |
| 5.3.4 | Vérifiez que les résultats de l’évaluation des politiques incluent des justifications structurées des décisions et sont transmis aux systèmes SIEM pour l’analyse de corrélation et la génération de rapports de conformité.                                                |   2    |  V   |
| 5.3.5 | Vérifiez que les valeurs de durée de vie (TTL) du cache de politique ne dépassent pas 5 minutes pour les ressources à haute sensibilité et 1 heure pour les ressources standard avec des capacités d'invalidation du cache.                                                 |   3    | D/V  |

---

## C5.4 Application de la sécurité au moment de la requête

Mettre en œuvre des contrôles de sécurité au niveau de la base de données avec filtrage obligatoire et politiques de sécurité au niveau des lignes.

|   #   | Description                                                                                                                                                                                                                                                                | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.4.1 | Vérifiez que toutes les requêtes de base de données vectorielle et SQL incluent des filtres de sécurité obligatoires (ID du locataire, étiquettes de sensibilité, périmètre utilisateur) appliqués au niveau du moteur de base de données, et non dans le code applicatif. |   1    | D/V  |
| 5.4.2 | Vérifiez que les politiques de sécurité au niveau des lignes (RLS) et le masquage au niveau des champs sont activés avec l'héritage des politiques pour toutes les bases de données vectorielles, indices de recherche et ensembles de données d'entraînement.             |   1    | D/V  |
| 5.4.3 | Vérifiez que les évaluations d'autorisation échouées empêchent les « attaques du délégué confus » en interrompant immédiatement les requêtes et en renvoyant des codes d'erreur d'autorisation explicites plutôt que de retourner des ensembles de résultats vides.        |   2    |  D   |
| 5.4.4 | Vérifiez que la latence d'évaluation des politiques est surveillée en continu avec des alertes automatisées pour les conditions de dépassement de délai pouvant permettre un contournement de l'autorisation.                                                              |   2    |  V   |
| 5.4.5 | Vérifiez que les mécanismes de nouvelle tentative de requête réévaluent les politiques d'autorisation pour prendre en compte les modifications dynamiques des permissions au sein des sessions utilisateur actives.                                                        |   3    | D/V  |

---

## Filtrage de sortie C5.5 et prévention des pertes de données

Déployez des contrôles de post-traitement pour prévenir l'exposition non autorisée des données dans le contenu généré par l'IA.

|   #   | Description                                                                                                                                                                                                                                                | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.5.1 | Vérifiez que les mécanismes de filtrage post-inférence scannent et censurent les informations personnelles identifiables non autorisées, les informations classifiées et les données exclusives avant de livrer le contenu aux demandeurs.                 |   1    | D/V  |
| 5.5.2 | Vérifiez que les citations, références et attributions de sources dans les résultats du modèle sont validées en fonction des droits d'accès de l'appelant et supprimées en cas de détection d'accès non autorisé.                                          |   1    | D/V  |
| 5.5.3 | Vérifiez que les restrictions de format de sortie (PDFs nettoyés, images dont les métadonnées ont été supprimées, types de fichiers approuvés) sont appliquées en fonction des niveaux d'autorisation des utilisateurs et des classifications des données. |   2    |  D   |
| 5.5.4 | Vérifiez que les algorithmes de rédaction sont déterministes, contrôlés par version et maintiennent des journaux d'audit pour soutenir les enquêtes de conformité et l'analyse judiciaire.                                                                 |   2    |  V   |
| 5.5.5 | Vérifiez que les événements de rédaction à haut risque génèrent des journaux adaptatifs incluant des hachages cryptographiques du contenu original pour une récupération médico-légale sans exposition des données.                                        |   3    |  V   |

---

## C5.6 Isolation Multi-Locataire

Assurer l'isolation cryptographique et logique entre les locataires dans une infrastructure d'IA partagée.

|   #   | Description                                                                                                                                                                                                                                                      | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.6.1 | Vérifiez que les espaces mémoire, les magasins d'intégration, les entrées de cache et les fichiers temporaires sont segmentés par espace de noms pour chaque locataire, avec une purge sécurisée lors de la suppression du locataire ou de la fin de la session. |   1    | D/V  |
| 5.6.2 | Vérifiez que chaque requête API inclut un identifiant de locataire authentifié qui est validé cryptographiquement par rapport au contexte de session et aux droits de l'utilisateur.                                                                             |   1    | D/V  |
| 5.6.3 | Vérifiez que les politiques réseau appliquent des règles de refus par défaut pour la communication inter-locataires au sein des maillages de services et des plateformes d'orchestration de conteneurs.                                                          |   2    |  D   |
| 5.6.4 | Vérifiez que les clés de chiffrement sont uniques par locataire avec prise en charge des clés gérées par le client (CMK) et une isolation cryptographique entre les magasins de données des locataires.                                                          |   3    |  D   |

---

## C5.7 Autorisation de l'Agent Autonome

Contrôlez les permissions des agents IA et des systèmes autonomes via des jetons de capacité à portée limitée et une autorisation continue.

|   #   | Description                                                                                                                                                                                                                                                                  | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 5.7.1 | Vérifiez que les agents autonomes reçoivent des jetons de capacités limités qui énumèrent explicitement les actions autorisées, les ressources accessibles, les limites temporelles et les contraintes opérationnelles.                                                      |   1    | D/V  |
| 5.7.2 | Vérifiez que les capacités à haut risque (accès au système de fichiers, exécution de code, appels API externes, transactions financières) sont désactivées par défaut et nécessitent des autorisations explicites pour leur activation avec des justifications commerciales. |   1    | D/V  |
| 5.7.3 | Vérifiez que les jetons de capacité sont liés aux sessions utilisateur, incluent une protection cryptographique de l'intégrité, et assurez-vous qu'ils ne peuvent pas être conservés ou réutilisés dans des scénarios hors ligne.                                            |   2    |  D   |
| 5.7.4 | Vérifiez que les actions initiées par l'agent subissent une autorisation secondaire via le moteur de politique ABAC avec une évaluation complète du contexte et une journalisation des audits.                                                                               |   2    |  V   |
| 5.7.5 | Vérifiez que les conditions d’erreur de l’agent et la gestion des exceptions incluent des informations sur la portée des capacités pour soutenir l’analyse des incidents et l’enquête médico-légale.                                                                         |   3    |  V   |

---

## Références

### Normes et cadres

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Guides de mise en œuvre

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Sécurité spécifique à l'IA

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

