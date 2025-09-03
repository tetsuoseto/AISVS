# Infrastructure C4, Configuration et Déploiement Sécurité

## Objectif de contrôle

L'infrastructure d'IA doit être durcie contre l'élévation de privilèges, l'altération de la chaîne d'approvisionnement et le mouvement latéral par une configuration sécurisée, une isolation d'exécution, des pipelines de déploiement fiables et une surveillance complète. Seuls les composants et configurations d'infrastructure autorisés et validés atteignent la production par des processus contrôlés qui maintiennent la sécurité, l'intégrité et l'auditabilité.

Objectif de sécurité principal : Seuls les composants d'infrastructure signés cryptographiquement et scannés pour les vulnérabilités atteignent la production via des pipelines de validation automatisés qui appliquent des politiques de sécurité et maintiennent des traces d'audit immuables.

---

## C4.1 Isolement de l'environnement d'exécution

Prévenir les évasions de conteneurs et l’élévation de privilèges grâce aux primitives d’isolement au niveau du noyau et aux contrôles d’accès obligatoires.

|   #   | description                                                                                                                                                                                                                                       | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.1.1 | Vérifiez que tous les conteneurs d'IA suppriment toutes les capacités Linux, à l'exception de CAP_SETUID, CAP_SETGID et des capacités explicitement requises documentées dans les référentiels de sécurité.                                       |   1    | D/V  |
| 4.1.2 | Vérifiez que les profils seccomp bloquent tous les appels système, à l'exception de ceux figurant sur des listes d'autorisation préapprouvées, et que les violations entraînent l'arrêt du conteneur et génèrent des alertes de sécurité.         |   1    | D/V  |
| 4.1.3 | Vérifiez que les charges de travail d'IA s'exécutent avec des systèmes de fichiers racine en lecture seule, tmpfs pour les données temporaires et des volumes nommés pour les données persistantes, avec les options de montage noexec imposées.  |   2    | D/V  |
| 4.1.4 | Vérifiez que la surveillance d’exécution basée sur eBPF (Falco, Tetragon ou équivalent) détecte les tentatives d’élévation de privilèges et tue automatiquement les processus malveillants dans les délais de réponse imposés par l’organisation. |   2    | D/V  |
| 4.1.5 | Vérifiez que les charges de travail d’IA à haut risque s’exécutent dans des environnements isolés au niveau matériel (Intel TXT, AMD SVM, ou nœuds bare-metal dédiés) avec vérification d'attestation.                                            |   3    | D/V  |

---

## C4.2 Pipelines de construction et de déploiement sécurisés

Assurer l'intégrité cryptographique et la sécurité de la chaîne d'approvisionnement grâce à des builds reproductibles et à des artefacts signés.

|   #   | description                                                                                                                                                                                                                                          | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.2.1 | Vérifiez que l'infrastructure-as-code est analysée par des outils (tfsec, Checkov ou Terrascan) à chaque commit, et bloquez les fusions en cas de résultats de gravité critique ou élevée.                                                           |   1    | D/V  |
| 4.2.2 | Vérifiez que les builds de conteneurs sont reproductibles avec des hachages SHA256 identiques d'un build à l'autre et générez des attestations de provenance SLSA Niveau 3 signées avec Sigstore.                                                    |   1    | D/V  |
| 4.2.3 | Vérifiez que les images de conteneurs intègrent des SBOM CycloneDX ou SPDX et sont signées avec Cosign avant le push vers le registre, les images non signées étant rejetées au déploiement.                                                         |   2    | D/V  |
| 4.2.4 | Vérifiez que les pipelines CI/CD utilisent des jetons OIDC provenant de HashiCorp Vault, des rôles AWS IAM ou de l'identité gérée Azure, avec des durées de validité qui ne dépassent pas les limites de la politique de sécurité de l'organisation. |   2    | D/V  |
| 4.2.5 | Vérifiez que les signatures Cosign et la provenance SLSA soient validées au cours du processus de déploiement avant l'exécution du conteneur et que les erreurs de vérification entraînent l'échec du déploiement.                                   |   2    | D/V  |
| 4.2.6 | Vérifiez que les environnements de build fonctionnent dans des conteneurs éphémères ou des machines virtuelles (VMs) sans stockage persistant et avec une isolation réseau par rapport aux VPC de production.                                        |   2    | D/V  |

---

## C4.3 Sécurité du réseau et contrôle d'accès

Implémenter le réseau zéro-confiance avec des politiques de refus par défaut et des communications chiffrées.

|   #   | description                                                                                                                                                                                                                      | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.3.1 | Vérifiez que les politiques réseau de Kubernetes, ou tout équivalent, mettent en œuvre un refus par défaut du trafic entrant et sortant avec des règles explicites d'autorisation pour les ports requis (443, 8080, etc.).       |   1    | D/V  |
| 4.3.2 | Vérifiez que SSH (port 22), RDP (port 3389) et les points de terminaison des métadonnées du cloud (169.254.169.254) sont bloqués ou nécessitent une authentification basée sur des certificats.                                  |   1    | D/V  |
| 4.3.3 | Vérifiez que le trafic sortant est filtré via des proxies HTTP/HTTPS (Squid, Istio ou passerelles NAT cloud) avec des listes blanches de domaines et que les requêtes bloquées sont enregistrées.                                |   2    | D/V  |
| 4.3.4 | Vérifiez que la communication entre services utilise le TLS mutuel avec des certificats renouvelés conformément à la politique organisationnelle et que la validation des certificats est appliquée (aucun drapeau skip-verify). |   2    | D/V  |
| 4.3.5 | Vérifiez que l'infrastructure d'IA fonctionne dans des VPCs/VNets dédiés, sans accès direct à Internet, et ne communique que via des passerelles NAT ou des hôtes bastion.                                                       |   2    | D/V  |

---

## C4.4 Secrets et gestion des clés cryptographiques

Protéger les identifiants grâce à un stockage protégé par le matériel et à une rotation automatique avec un accès Zero Trust.

|   #   | description                                                                                                                                                                                                                                                           | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.4.1 | Vérifiez que les secrets sont stockés dans HashiCorp Vault, AWS Secrets Manager, Azure Key Vault ou Google Secret Manager avec chiffrement au repos utilisant AES-256.                                                                                                |   1    | D/V  |
| 4.4.2 | Vérifiez que les clés cryptographiques sont générées dans des HSM conformes à FIPS 140-2 Niveau 2 (AWS CloudHSM, Azure Dedicated HSM) avec rotation des clés conformément à la politique cryptographique de l'organisation.                                           |   1    | D/V  |
| 4.4.3 | Vérifiez que la rotation des secrets est automatisée avec un déploiement sans interruption et une rotation immédiate déclenchée par des changements de personnel ou des incidents de sécurité.                                                                        |   2    | D/V  |
| 4.4.4 | Vérifiez que les images de conteneur sont analysées à l'aide d'outils (GitLeaks, TruffleHog ou detect-secrets) qui bloquent les builds contenant des clés d'API, des mots de passe ou des certificats.                                                                |   2    | D/V  |
| 4.4.5 | Vérifiez que l'accès aux secrets de production nécessite une authentification à facteurs multiples (MFA) avec des jetons matériels (YubiKey, FIDO2) et est consigné dans des journaux d'audit immuables comprenant les identités des utilisateurs et les horodatages. |   2    | D/V  |
| 4.4.6 | Vérifiez que les secrets sont injectés via les secrets Kubernetes, des volumes montés ou des conteneurs d'initialisation, et assurez‑vous que les secrets ne sont jamais intégrés dans les variables d’environnement ou les images.                                   |   2    | D/V  |

---

## C4.5 Sandboxing des charges de travail d'IA et validation

Isolez les modèles d'IA non fiables dans des sandboxes sécurisés avec une analyse comportementale approfondie.

|   #   | description                                                                                                                                                                                                                      | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.5.1 | Vérifiez que les modèles d'IA externes s'exécutent dans gVisor, des microVMs (tels que Firecracker, CrossVM) ou des conteneurs Docker, avec les options --security-opt=no-new-privileges et --read-only.                         |   1    | D/V  |
| 4.5.2 | Vérifiez que les environnements sandbox n'ont aucune connectivité réseau (--network=none) ou qu'ils n'ont qu'un accès à localhost, toutes les requêtes externes étant bloquées par des règles iptables.                          |   1    | D/V  |
| 4.5.3 | Vérifiez que la validation des modèles d'IA inclut des tests automatisés de type red team avec une couverture des tests définie par l'organisation et une analyse comportementale pour la détection de portes dérobées.          |   2    | D/V  |
| 4.5.4 | Vérifiez que, avant la promotion d'un modèle d'IA en production, les résultats du bac à sable de ce modèle sont signés cryptographiquement par du personnel de sécurité autorisé et stockés dans des journaux d'audit immuables. |   2    | D/V  |
| 4.5.5 | Vérifiez que les environnements sandbox sont détruits et recréés à partir d'images dorées entre les évaluations, avec un nettoyage complet du système de fichiers et de la mémoire.                                              |   2    | D/V  |

---

## C4.6 Surveillance de la sécurité des infrastructures

Scanner et surveiller l'infrastructure en continu avec une remédiation automatisée et des alertes en temps réel.

|   #   | description                                                                                                                                                                                                                              | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.6.1 | Vérifier que les images de conteneur sont scannées selon les calendriers organisationnels, les vulnérabilités critiques bloquant le déploiement en fonction des seuils de risque organisationnels.                                       |   1    | D/V  |
| 4.6.2 | Vérifier que l'infrastructure satisfait les benchmarks CIS ou les contrôles NIST SP 800-53, avec des seuils de conformité définis au niveau organisationnel et une remédiation automatisée pour les vérifications échouées.              |   1    | D/V  |
| 4.6.3 | Vérifiez que les vulnérabilités à gravité élevée sont corrigées conformément aux calendriers de gestion des risques de l'organisation, avec des procédures d’urgence pour les CVE activement exploitées.                                 |   2    | D/V  |
| 4.6.4 | Vérifiez que les alertes de sécurité s'intègrent aux plateformes SIEM (Splunk, Elastic ou Sentinel) en utilisant les formats CEF ou STIX/TAXII, avec un enrichissement automatisé.                                                       |   2    |  V   |
| 4.6.5 | Vérifiez que les métriques d'infrastructure sont exportées vers les systèmes de surveillance (Prometheus, DataDog) avec des tableaux de bord SLA et des rapports destinés à la direction.                                                |   3    |  V   |
| 4.6.6 | Vérifiez que la dérive de configuration est détectée à l'aide d'outils (Chef InSpec, AWS Config) conformément aux exigences de surveillance de l'organisation, avec une restauration automatique en cas de modifications non autorisées. |   2    | D/V  |

---

## C4.7 Gestion des ressources d'infrastructure d'IA

Prévenir les attaques d'épuisement des ressources et assurer une allocation équitable des ressources grâce à des quotas et à une surveillance.

|   #   | description                                                                                                                                                                                                                                                                      | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.7.1 | Vérifiez que l'utilisation du GPU/TPU est surveillée avec des alertes déclenchées à des seuils définis par l'organisation et que les mécanismes de mise à l'échelle automatique ou d'équilibrage de charge soient activés conformément aux politiques de gestion de la capacité. |   1    | D/V  |
| 4.7.2 | Vérifiez que les métriques de charge de travail d'IA (latence d'inférence, débit, taux d'erreur) sont collectées conformément aux exigences de surveillance de l'organisation et corrélées à l'utilisation de l'infrastructure.                                                  |   1    | D/V  |
| 4.7.3 | Vérifiez que les quotas de ressources Kubernetes (ResourceQuotas) ou équivalents limitent les charges de travail individuelles conformément aux politiques internes d'allocation des ressources, avec des limites strictes imposées.                                             |   2    | D/V  |
| 4.7.4 | Vérifiez que la surveillance des coûts suit les dépenses par charge de travail/locataire, avec des alertes basées sur les seuils budgétaires organisationnels et des contrôles automatisés en cas de dépassements budgétaires.                                                   |   2    |  V   |
| 4.7.5 | Vérifiez que la planification de la capacité utilise des données historiques avec des périodes de prévision définies par l'organisation et un approvisionnement automatique des ressources basé sur les schémas de la demande.                                                   |   3    |  V   |
| 4.7.6 | Vérifiez que l'épuisement des ressources déclenche les disjoncteurs conformément aux exigences de réponse organisationnelles, y compris la limitation du débit basée sur les politiques de capacité et l'isolement des charges de travail.                                       |   2    | D/V  |

---

## C4.8 Séparation des environnements et contrôles de promotion

Imposer des limites d'environnement strictes avec des portes de promotion automatisées et une validation de sécurité.

|   #   | description                                                                                                                                                                                                                        | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.8.1 | Vérifier que les environnements de développement, de test et de production fonctionnent dans des VPCs/VNets séparés, sans rôles IAM partagés, groupes de sécurité ni connectivité réseau.                                          |   1    | D/V  |
| 4.8.2 | Vérifiez que la promotion d'un environnement nécessite l'approbation du personnel autorisé défini au niveau organisationnel, avec des signatures cryptographiques et des journaux d'audit immuables.                               |   1    | D/V  |
| 4.8.3 | Vérifiez que les environnements de production bloquent l'accès SSH, désactivent les points de terminaison de débogage et exigent des demandes de changement assorties de préavis organisationnels, sauf en cas d'urgence.          |   2    | D/V  |
| 4.8.4 | Vérifiez que les modifications d'infrastructure-as-code nécessitent une revue par les pairs avec des tests automatisés et une analyse de sécurité avant la fusion dans la branche principale.                                      |   2    | D/V  |
| 4.8.5 | Vérifiez que les données hors production sont anonymisées conformément aux exigences de confidentialité organisationnelles, à la génération de données synthétiques ou à un masquage complet des données avec suppression des PII. |   2    | D/V  |
| 4.8.6 | Vérifier que les portes de promotion incluent des tests de sécurité automatisés (SAST, DAST, analyse des images de conteneurs) avec aucune découverte critique requise pour l'approbation.                                         |   2    | D/V  |

---

## C4.9 Infrastructure Sauvegarde et Restauration

Assurer la résilience de l'infrastructure grâce à des sauvegardes automatisées, des procédures de récupération testées et des capacités de reprise après sinistre.

|   #   | description                                                                                                                                                                                                                  | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.9.1 | Vérifiez que les configurations d'infrastructure sont sauvegardées conformément aux plannings de sauvegarde de l'organisation dans des régions géographiquement séparées, selon la stratégie de sauvegarde 3-2-1.            |   1    | D/V  |
| 4.9.2 | Vérifiez que les systèmes de sauvegarde fonctionnent dans des réseaux isolés, avec des identifiants séparés et un stockage déconnecté du réseau pour la protection contre les ransomwares.                                   |   2    | D/V  |
| 4.9.3 | Vérifier que les procédures de récupération sont testées et validées par des tests automatisés, conformément aux calendriers organisationnels, avec des objectifs RTO et RPO qui répondent aux exigences organisationnelles. |   2    |  V   |
| 4.9.4 | Vérifiez que la reprise après sinistre inclut des runbooks spécifiques à l’IA avec la restauration des poids du modèle, la reconstruction du cluster GPU et la cartographie des dépendances des services.                    |   3    |  V   |

---

## C4.10 Conformité et gouvernance des infrastructures

Maintenir la conformité réglementaire grâce à une évaluation continue, à la documentation et à des contrôles automatisés.

|   #    | description                                                                                                                                                                                                                             | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.10.1 | Vérifier que la conformité de l'infrastructure est évaluée selon les plannings organisationnels et les contrôles SOC 2, ISO 27001 ou FedRAMP, avec une collecte automatisée des preuves.                                                |   2    | D/V  |
| 4.10.2 | Vérifiez que la documentation d'infrastructure comprend des diagrammes réseau, des cartes de flux de données et des modèles de menace et qu'ils sont mis à jour conformément aux exigences de la gestion du changement organisationnel. |   2    |  V   |
| 4.10.3 | Vérifiez que les modifications d'infrastructure font l'objet d'une évaluation d'impact sur la conformité automatisée avec des flux de travail d'approbation réglementaire pour les modifications à haut risque.                         |   3    | D/V  |

---

## C4.11 Sécurité du matériel d'IA

Sécuriser les composants matériels spécifiques à l’IA, y compris les GPU, les TPU et les accélérateurs IA spécialisés.

|   #    | description                                                                                                                                                                                                                      | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.11.1 | Vérifiez que le micrologiciel de l'accélérateur IA (BIOS GPU, micrologiciel TPU) est vérifié par des signatures cryptographiques et mis à jour conformément aux calendriers de gestion des correctifs au sein de l'organisation. |   2    | D/V  |
| 4.11.2 | Vérifiez que, avant l'exécution de la charge de travail, l'intégrité de l'accélérateur d'IA est validée par une attestation matérielle utilisant TPM 2.0, Intel TXT ou AMD SVM.                                                  |   2    | D/V  |
| 4.11.3 | Vérifiez que la mémoire GPU est isolée entre les charges de travail en utilisant SR-IOV, MIG (Multi-Instance GPU) ou une partition matérielle équivalente, avec sanitisation de la mémoire entre les charges de travail.         |   2    | D/V  |
| 4.11.4 | Vérifiez que la chaîne d'approvisionnement du matériel d'IA inclut la vérification de la provenance avec des certificats du fabricant et la validation des emballages inviolables.                                               |   3    |  V   |
| 4.11.5 | Vérifiez que les modules de sécurité matériels (HSM) protègent les poids des modèles d’IA et les clés cryptographiques avec une certification FIPS 140-2 Niveau 3 ou Common Criteria EAL4+.                                      |   3    | D/V  |

---

## C4.12 Infrastructure d'IA en périphérie et distribuée

Déploiements sécurisés d'IA distribuée, y compris l'informatique en périphérie, l'apprentissage fédéré et les architectures multi-sites.

|   #    | description                                                                                                                                                                                                                                       | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.12.1 | Vérifiez que les dispositifs d'IA en périphérie s'authentifient auprès de l'infrastructure centrale en utilisant TLS mutuel, avec des certificats d'appareil renouvelés conformément à la politique de gestion des certificats de l'organisation. |   2    | D/V  |
| 4.12.2 | Vérifiez que les dispositifs en périphérie mettent en œuvre un démarrage sécurisé avec des signatures vérifiées et une protection contre le rétrogradage du firmware.                                                                             |   2    | D/V  |
| 4.12.3 | Vérifiez que la coordination distribuée de l’IA utilise des algorithmes de consensus tolérants aux fautes byzantines avec validation des participants et détection des nœuds malveillants.                                                        |   3    | D/V  |
| 4.12.4 | Vérifiez que la communication edge-to-cloud comprend la limitation de la bande passante, la compression des données et des capacités de fonctionnement hors ligne avec un stockage local sécurisé.                                                |   3    | D/V  |

---

## C4.13 Sécurité des infrastructures multi-cloud et hybrides

Sécuriser les charges de travail d'IA à travers plusieurs fournisseurs de cloud et des déploiements hybrides cloud et sur site.

|   #    | description                                                                                                                                                                                                              | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 4.13.1 | Vérifiez que les déploiements multi-cloud d'IA utilisent une fédération d'identité indépendante du cloud (OIDC, SAML) avec une gestion centralisée des politiques entre les fournisseurs.                                |   2    | D/V  |
| 4.13.2 | Vérifier que le transfert de données entre clouds utilise le chiffrement de bout en bout avec des clés gérées par le client et des contrôles de localisation des données appliqués par juridiction.                      |   2    | D/V  |
| 4.13.3 | Vérifiez que les charges de travail d’IA dans un cloud hybride mettent en œuvre des politiques de sécurité cohérentes entre les environnements sur site et dans le cloud, avec une surveillance et des alertes unifiées. |   2    | D/V  |
| 4.13.4 | Vérifiez que la prévention du verrouillage du fournisseur de cloud inclut l'infrastructure-as-code portable, des API standardisées et des capacités d'exportation de données avec des outils de conversion de formats.   |   3    |  V   |
| 4.13.5 | Vérifiez que l'optimisation des coûts multi-cloud inclut des contrôles de sécurité empêchant l'étalement des ressources ainsi que les frais de transfert de données inter-cloud non autorisés.                           |   3    |  V   |

---

## C4.14 Automatisation de l'infrastructure et sécurité GitOps

Sécuriser les pipelines d'automatisation de l'infrastructure et les workflows GitOps pour la gestion de l'infrastructure d'IA.

|   #    | description                                                                                                                                                                                                                                                | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.14.1 | Vérifiez que les dépôts GitOps exigent des commits signés avec des clés GPG et des règles de protection de branche empêchant les pushes directs vers les branches principales.                                                                             |   2    | D/V  |
| 4.14.2 | Vérifiez que l'automatisation de l'infrastructure inclut la détection de dérive avec une remédiation automatique et des capacités de rollback déclenchées conformément aux exigences de réponse organisationnelles en cas de modifications non autorisées. |   2    | D/V  |
| 4.14.3 | Vérifiez que le provisionnement automatisé de l'infrastructure inclut la validation des politiques de sécurité avec blocage du déploiement pour les configurations non conformes.                                                                          |   2    | D/V  |
| 4.14.4 | Vérifiez que les secrets d'automatisation de l'infrastructure sont gérés par des opérateurs de secrets externes (External Secrets Operator, Bank-Vaults) avec rotation automatique.                                                                        |   2    | D/V  |
| 4.14.5 | Vérifiez que l'infrastructure auto-guérissante intègre la corrélation des événements de sécurité avec une réponse automatisée aux incidents et des flux de notification destinés aux parties prenantes.                                                    |   3    |  V   |

---

## C4.15 Sécurité des infrastructures résistantes à l'informatique quantique

Préparez l'infrastructure d'IA pour faire face aux menaces de l'informatique quantique grâce à la cryptographie post-quantique et à des protocoles résistants à l'informatique quantique.

|   #    | description                                                                                                                                                                                                              | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 4.15.1 | Vérifiez que l'infrastructure d'IA implémente les algorithmes cryptographiques post-quantiques approuvés par le NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) pour l'échange de clés et les signatures numériques. |   3    | D/V  |
| 4.15.2 | Vérifiez que les systèmes de distribution de clés quantiques (QKD) sont mis en œuvre pour des communications d'IA à haute sécurité avec des protocoles de gestion des clés résistants à l'informatique quantique.        |   3    | D/V  |
| 4.15.3 | Vérifiez que les cadres d’agilité cryptographique permettent une migration rapide vers de nouveaux algorithmes post-quantiques avec rotation automatisée des certificats et des clés.                                    |   3    | D/V  |
| 4.15.4 | Vérifiez que la modélisation des menaces quantiques évalue la vulnérabilité des infrastructures d'IA face aux attaques quantiques, avec des calendriers de migration documentés et des évaluations des risques.          |   3    |  V   |
| 4.15.5 | Vérifiez que les systèmes cryptographiques hybrides classiques-quantique assurent une défense en profondeur pendant la période de transition quantique avec une surveillance des performances.                           |   3    | D/V  |

---

## C4.16 Informatique confidentielle et enclaves sécurisées

Protéger les charges de travail d'IA et les poids des modèles en utilisant des environnements d'exécution de confiance basés sur le matériel et des technologies d'informatique confidentielle.

|   #    | description                                                                                                                                                                                             | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.16.1 | Vérifiez que les modèles d'IA sensibles s'exécutent dans les enclaves Intel SGX, AMD SEV-SNP ou ARM TrustZone, avec mémoire chiffrée et vérification d'attestation.                                     |   3    | D/V  |
| 4.16.2 | Vérifiez que les conteneurs confidentiels (Kata Containers, gVisor avec informatique confidentielle) isolent les charges de travail d’IA grâce à un chiffrement mémoire pris en charge par le matériel. |   3    | D/V  |
| 4.16.3 | Vérifiez que l'attestation à distance valide l'intégrité de l'enclave avant de charger des modèles d'IA avec une preuve cryptographique de l'authenticité d'un environnement d'exécution.               |   3    | D/V  |
| 4.16.4 | Vérifiez que les services d'inférence d'IA confidentiels empêchent l'extraction de modèles par calcul chiffré, avec des poids du modèle scellés et une exécution protégée.                              |   3    | D/V  |
| 4.16.5 | Vérifiez que l'orchestration de l'environnement d'exécution fiable gère le cycle de vie des enclaves sécurisées avec l'attestation à distance et des canaux de communication chiffrés.                  |   3    | D/V  |
| 4.16.6 | Vérifiez que le calcul multipartite sécurisé (SMPC) permet un entraînement collaboratif en IA sans exposer les ensembles de données individuels ou les paramètres du modèle.                            |   3    | D/V  |

---

## C4.17 Infrastructure à connaissance nulle

Mettre en œuvre des systèmes de preuves à connaissance nulle pour la vérification et l'authentification de l'IA respectant la vie privée, sans révéler d'informations sensibles.

|   #    | description                                                                                                                                                                                                                               | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.17.1 | Vérifier que les preuves à connaissance nulle (ZK-SNARKs, ZK-STARKs) vérifient l'intégrité du modèle d'IA et la provenance de l'entraînement sans exposer les poids du modèle ni les données d'entraînement.                              |   3    | D/V  |
| 4.17.2 | Vérifiez que les systèmes d'authentification basés sur des preuves à connaissance nulle permettent une vérification des utilisateurs préservant la vie privée pour les services d'IA, sans révéler d'informations relatives à l'identité. |   3    | D/V  |
| 4.17.3 | Vérifiez que les protocoles d'intersection d’ensembles privés (PSI) permettent une mise en correspondance sécurisée des données pour l'IA fédérée sans exposer les jeux de données individuels.                                           |   3    | D/V  |
| 4.17.4 | Vérifiez que les systèmes d'apprentissage automatique à connaissance nulle (ZKML) permettent des inférences d'IA vérifiables avec une preuve cryptographique du calcul correct.                                                           |   3    | D/V  |
| 4.17.5 | Vérifiez que les ZK-rollups offrent un traitement des transactions d'IA évolutif et préservant la confidentialité, avec une vérification par lots et une surcharge de calcul réduite.                                                     |   3    | D/V  |

---

## C4.18 Prévention des attaques par canaux latéraux

Protéger l'infrastructure d'IA des attaques par canaux auxiliaires de temporisation, de puissance, électromagnétiques et basées sur le cache qui pourraient divulguer des informations sensibles.

|   #    | description                                                                                                                                                                                            | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 4.18.1 | Vérifiez que le temps d'inférence de l'IA est normalisé à l'aide d'algorithmes à temps constant et de rembourrage afin d'empêcher les attaques d'extraction de modèle basées sur le temps.             |   3    | D/V  |
| 4.18.2 | Vérifiez que la protection contre l'analyse de puissance inclut l'injection de bruit, le filtrage des lignes d'alimentation et des schémas d'exécution aléatoires pour le matériel d'IA.               |   3    | D/V  |
| 4.18.3 | Vérifiez que l’atténuation des canaux latéraux basés sur le cache utilise le partitionnement du cache, la randomisation et les instructions de purge du cache pour empêcher les fuites d’informations. |   3    | D/V  |
| 4.18.4 | Vérifiez que la protection contre les émissions électromagnétiques comprend le blindage, le filtrage des signaux et le traitement aléatoire afin de prévenir les attaques de type TEMPEST.             |   3    | D/V  |
| 4.18.5 | Vérifiez que les défenses contre les canaux latéraux microarchitecturaux incluent des contrôles de l'exécution spéculative et l'obfuscation des motifs d'accès mémoire.                                |   3    | D/V  |

---

## C4.19 Neuromorphique et sécurité du matériel IA spécialisé

Sécuriser les architectures matérielles émergentes pour l’IA, y compris les puces neuromorphiques, les FPGAs, les ASICs personnalisés et les systèmes de calcul optique.

|   #    | description                                                                                                                                                                                                    | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.19.1 | Vérifiez que la sécurité des puces neuromorphes inclut le chiffrement des motifs d'impulsions, la protection des poids synaptiques et la validation des règles d'apprentissage basées sur le matériel.         |   3    | D/V  |
| 4.19.2 | Vérifiez que les accélérateurs IA basés sur FPGA mettent en œuvre le chiffrement du bitstream, les mécanismes anti-sabotage et le chargement sécurisé de la configuration avec des mises à jour authentifiées. |   3    | D/V  |
| 4.19.3 | Vérifiez que la sécurité des ASIC personnalisés inclut des processeurs de sécurité sur puce, une racine de confiance matérielle et un stockage sûr des clés avec détection de manipulation.                    |   3    | D/V  |
| 4.19.4 | Vérifiez que les systèmes de calcul optique mettent en œuvre un chiffrement optique résistant aux ordinateurs quantiques, une commutation photonique sécurisée et un traitement du signal optique protégé.     |   3    | D/V  |
| 4.19.5 | Vérifiez que les puces d'IA hybrides analogiques et numériques incluent un calcul analogique sécurisé, un stockage protégé des poids et une conversion analogique-numérique authentifiée.                      |   3    | D/V  |

---

## C4.20 Infrastructure de calcul préservant la vie privée

Implémenter des contrôles d'infrastructure pour des calculs préservant la confidentialité afin de protéger les données sensibles pendant le traitement et l'analyse par l'IA.

|   #    | description                                                                                                                                                                                                                       | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.20.1 | Vérifiez que l'infrastructure de chiffrement homomorphe permet des calculs chiffrés sur des charges de travail sensibles liées à l'IA, avec vérification de l'intégrité cryptographique et surveillance des performances.         |   3    | D/V  |
| 4.20.2 | Vérifiez que les systèmes de récupération d'informations privées permettent des requêtes sur des bases de données sans révéler les motifs de requête, grâce à une protection cryptographique des motifs d'accès.                  |   3    | D/V  |
| 4.20.3 | Vérifiez que les protocoles de calcul multipartite sécurisé permettent une inférence d’IA respectueuse de la vie privée sans exposer les entrées individuelles ni les calculs intermédiaires.                                     |   3    | D/V  |
| 4.20.4 | Vérifiez que la gestion des clés respectueuse de la vie privée inclut la génération de clés distribuée, la cryptographie à seuil et la rotation sécurisée des clés avec une protection matérielle.                                |   3    | D/V  |
| 4.20.5 | Vérifiez que les performances du calcul à confidentialité préservée sont optimisées grâce au traitement par lots, à la mise en cache et à l'accélération matérielle tout en maintenant les garanties de sécurité cryptographique. |   3    | D/V  |

---

## C4.15 Agent Framework Cloud Integration Sécurité et Déploiement Hybride

Contrôles de sécurité pour les frameworks d'agents intégrés au cloud avec des architectures hybrides sur site et dans le cloud.

|   #    | description                                                                                                                                         | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.15.1 | Vérifiez que l'intégration du stockage dans le cloud utilise un chiffrement de bout en bout avec une gestion des clés contrôlée par l'agent.        |   1    | D/V  |
| 4.15.2 | Vérifiez que les frontières de sécurité du déploiement hybride sont clairement définies avec des canaux de communication chiffrés.                  |   2    | D/V  |
| 4.15.3 | Vérifiez que l'accès aux ressources cloud inclut une vérification zéro-trust avec une authentification continue.                                    |   2    | D/V  |
| 4.15.4 | Vérifiez que les exigences de résidence des données sont appliquées par une attestation cryptographique des emplacements de stockage.               |   3    | D/V  |
| 4.15.5 | Vérifiez que les évaluations de sécurité du fournisseur cloud incluent une modélisation des menaces axée sur l’agent et une évaluation des risques. |   3    | D/V  |

---

## Références

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [NIST SP 800-190: Application Container Security Guide](https://csrc.nist.gov/publications/detail/sp/800-190/final)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST SP 800-53: Security Controls for Federal Information Systems](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
* [FIPS 140-2 Security Requirements](https://csrc.nist.gov/publications/detail/fips/140/2/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
* [IEEE 2857: Privacy Engineering for AI Systems](https://standards.ieee.org/ieee/2857/7273/)
* [NIST SP 800-161: Cybersecurity Supply Chain Risk Management](https://csrc.nist.gov/publications/detail/sp/800-161/rev-1/final)
* [NIST Post-Quantum Cryptography Standards](https://csrc.nist.gov/Projects/post-quantum-cryptography)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/tools/software-guard-extensions/overview.html)
* [AMD SEV-SNP White Paper](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf)
* [ARM TrustZone Technology](https://developer.arm.com/ip-products/security-ip/trustzone)
* [ZK-SNARKs: A Gentle Introduction](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)
* [NIST SP 800-57: Cryptographic Key Management](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-5/final)
* [Side-Channel Attack Countermeasures](https://link.springer.com/book/10.1007/978-3-319-75268-6)
* [Neuromorphic Computing Security Challenges](https://ieeexplore.ieee.org/document/9458103)
* [FPGA Security: Fundamentals, Evaluation, and Countermeasures](https://link.springer.com/book/10.1007/978-3-319-90385-9)
* [Microsoft SEAL: Homomorphic Encryption Library](https://github.com/Microsoft/SEAL)
* [HElib: Homomorphic Encryption Library](https://github.com/homenc/HElib)
* [PALISADE Lattice Cryptography Library](https://palisade-crypto.org/)
* [Differential Privacy: A Survey of Results](https://link.springer.com/chapter/10.1007/978-3-540-79228-4_1)
* [Secure Aggregation for Federated Learning](https://eprint.iacr.org/2017/281.pdf)
* [Private Information Retrieval: Concepts and Constructions](https://link.springer.com/book/10.1007/978-3-030-16234-8)

