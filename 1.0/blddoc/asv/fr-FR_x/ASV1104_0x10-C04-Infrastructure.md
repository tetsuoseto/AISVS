# Infrastructure C4, sécurité de la configuration et du déploiement

## Objectif de contrôle

L'infrastructure d'IA doit être renforcée contre l'escalade de privilèges, la falsification de la chaîne d'approvisionnement et les mouvements latéraux grâce à une configuration sécurisée, une isolation à l'exécution, des pipelines de déploiement fiables et une surveillance complète. Seuls les composants d'infrastructure validés et autorisés atteignent la production via des processus contrôlés garantissant la sécurité, l'intégrité et la traçabilité.

Objectif principal de sécurité : seuls les composants d'infrastructure signés cryptographiquement et analysés pour les vulnérabilités atteignent la production via des pipelines de validation automatisés qui appliquent les politiques de sécurité et maintiennent des pistes d'audit immuables.

---

## C4.1 Isolation de l'environnement d'exécution

Empêcher les échappées de conteneurs et l'escalade de privilèges grâce aux primitives d'isolation au niveau du système d'exploitation.

|   #   | Description                                                                                                                                                                                                                                           | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.1.1 | Vérifiez que toutes les charges de travail d'IA s'exécutent avec les permissions minimales nécessaires sur le système d'exploitation, par exemple en supprimant les capacités Linux inutiles dans le cas d'un conteneur.                              |   1    | D/V  |
| 4.1.2 | Vérifiez que les charges de travail sont protégées par des technologies limitant l'exploitation telles que le sandboxing, les profils seccomp, AppArmor, SELinux ou similaires, et que la configuration est appropriée.                               |   1    | D/V  |
| 4.1.3 | Vérifiez que les charges de travail s'exécutent avec un système de fichiers racine en lecture seule, et que tous les montages en écriture sont explicitement définis et renforcés avec des options restrictives (par exemple, noexec, nosuid, nodev). |   2    | D/V  |
| 4.1.4 | Vérifiez que la surveillance en temps réel détecte les comportements d'élévation de privilèges et d'évasion de conteneurs, puis termine automatiquement les processus fautifs.                                                                        |   2    | D/V  |
| 4.1.5 | Vérifiez que les charges de travail d'IA à haut risque fonctionnent dans des environnements isolés matériellement (par exemple, TEEs, hyperviseurs de confiance ou nœuds bare-metal) uniquement après une attestation distante réussie.               |   3    | D/V  |

---

## C4.2 Chaînes de build et de déploiement sécurisées

Assurez l'intégrité cryptographique et la sécurité de la chaîne d'approvisionnement grâce à des builds reproductibles et des artefacts signés.

|  #  | Description | Niveau | Rôle |
| :-: | ----------- | :----: | :--: |

| 4.2.1 | Vérifier que les builds sont reproductibles et produisent des métadonnées de provenance signées, selon ce qui est approprié pour les artefacts de build, afin qu'elles puissent être vérifiées de manière indépendante. | 1 | D/V |
| 4.2.2 | Vérifier que les builds produisent une liste des composants logiciels (SBOM) et sont signés avant d'être acceptés pour le déploiement. | 2 | D/V |
| 4.2.3 | Vérifier que les signatures des artefacts de build (par exemple, les images de conteneurs) et les métadonnées de provenance sont validées lors du déploiement, et que les artefacts non vérifiés sont rejetés. | 2 | D/V |

---

## C4.3 Sécurité du réseau et contrôle d'accès

Mettre en œuvre un réseau à confiance zéro avec des politiques de refus par défaut et des communications chiffrées.

|   #   | Description                                                                                                                                                                                                                                                  | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 4.3.1 | Vérifiez que les politiques réseau appliquent un refus par défaut pour l’entrée et la sortie, avec uniquement les services requis explicitement autorisés.                                                                                                   |   1    | D/V  |
| 4.3.2 | Vérifiez que les protocoles d'accès administratif (par ex., SSH, RDP) et l'accès aux services de métadonnées cloud sont restreints et exigent une authentification forte.                                                                                    |   1    | D/V  |
| 4.3.3 | Vérifiez que le trafic sortant est limité aux destinations approuvées et que toutes les requêtes sont enregistrées.                                                                                                                                          |   2    | D/V  |
| 4.3.4 | Vérifiez que la communication inter-services utilise TLS mutuel avec validation des certificats et une rotation automatisée régulière.                                                                                                                       |   2    | D/V  |
| 4.3.5 | Vérifiez que les charges de travail et les environnements d’IA (dev, test, prod) fonctionnent dans des segments réseau isolés (VPC/VNets) sans accès direct à Internet et sans rôles IAM, groupes de sécurité ou connectivité inter-environnements partagés. |   2    | D/V  |

## C4.4 Gestion des Secrets et des Clés Cryptographiques

Protégez les secrets et les clés cryptographiques grâce à un stockage sécurisé, une rotation automatisée et des contrôles d'accès renforcés.

|   #   | Description                                                                                                                                                                                                                                                                                                 | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.4.1 | Vérifiez que les secrets sont stockés dans un système dédié de gestion des secrets avec chiffrement au repos et isolés des charges de travail des applications.                                                                                                                                             |   1    | D/V  |
| 4.4.2 | Vérifiez que les clés cryptographiques sont générées et stockées dans des modules matériels sécurisés (par exemple, HSM, KMS cloud).                                                                                                                                                                        |   1    | D/V  |
| 4.4.3 | Vérifiez que la rotation des secrets est automatisée.                                                                                                                                                                                                                                                       |   2    | D/V  |
| 4.4.4 | Vérifiez que l'accès aux secrets de production nécessite une authentification forte.                                                                                                                                                                                                                        |        |      |
| 4.4.5 | Vérifiez que les secrets sont déployés aux applications au moment de l'exécution via une solution de gestion des secrets. Les secrets ne doivent jamais être intégrés dans le code source, les fichiers de configuration, les artefacts de build, les images de conteneur ou les variables d'environnement. |   2    | D/V  |

---

## C4.5 Sandbox et Validation des Charges de Travail IA

Isolez les modèles d'IA non fiables dans des environnements sécurisés isolés et protégez les charges de travail sensibles en IA en utilisant des environnements d'exécution de confiance (TEE) et des technologies de calcul confidentiel.

|   #   | Description                                                                                                                                                                                                                               | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.5.1 | Vérifiez que les modèles d'IA externes ou non fiables s'exécutent dans des environnements isolés (sandboxes).                                                                                                                             |   1    | D/V  |
| 4.5.2 | Vérifiez que les charges de travail en environnement isolé n'ont pas de connectivité réseau sortante par défaut, tout accès nécessaire devant être défini explicitement.                                                                  |   1    | D/V  |
| 4.5.3 | Vérifiez que l'attestation de la charge de travail est effectuée avant le chargement du modèle ou de la charge de travail, garantissant une preuve cryptographique d'un environnement d'exécution de confiance.                           |   2    | D/V  |
| 4.5.4 | Vérifiez que les charges de travail confidentielles s'exécutent au sein d'un environnement d'exécution sécurisé (TEE) qui fournit une isolation renforcée par le matériel, un chiffrement de la mémoire et une protection de l'intégrité. |   3    | D/V  |
| 4.5.5 | Vérifiez que les services d'inférence confidentiels empêchent l'extraction du modèle grâce à un calcul chiffré avec des poids de modèle scellés et une exécution protégée.                                                                |   3    | D/V  |
| 4.5.6 | Vérifiez que l'orchestration des environnements d'exécution sécurisés inclut la gestion du cycle de vie, l'attestation à distance et les canaux de communication chiffrés.                                                                |   3    | D/V  |
| 4.5.7 | Vérifiez que le calcul multipartite sécurisé (SMPC) permet un entraînement collaboratif de l’IA sans exposer les ensembles de données individuels ni les paramètres du modèle.                                                            |   3    | D/V  |

---

## C4.6 Gestion des ressources de l'infrastructure IA, sauvegarde et récupération

Prévenir les attaques par épuisement de ressources et assurer une allocation équitable des ressources grâce à des quotas et une surveillance. Maintenir la résilience de l'infrastructure grâce à des sauvegardes sécurisées, des procédures de récupération testées et des capacités de reprise après sinistre.

|   #   | Description                                                                                                                                                                                                                                                                                                           | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.6.1 | Vérifiez que la consommation des ressources de la charge de travail est limitée de manière appropriée, par exemple avec des ResourceQuotas Kubernetes ou des mécanismes similaires, pour atténuer les attaques par déni de service.                                                                                   |   2    | D/V  |
| 4.6.2 | Vérifiez que l'épuisement des ressources déclenche des protections automatisées (par exemple, la limitation de débit ou l'isolation de la charge de travail) une fois que les seuils définis de CPU, de mémoire ou de requêtes sont dépassés.                                                                         |   2    | D/V  |
| 4.6.3 | Vérifier que les systèmes de sauvegarde fonctionnent dans des réseaux isolés avec des identifiants séparés, et que le système de stockage est soit exploité dans un réseau isolé physiquement (air-gapped), soit qu’il implémente une protection WORM (write-once-read-many) contre toute modification non autorisée. |   2    | D/V  |

---

## C4.7 Sécurité matérielle de l'IA

Sécurisez les composants matériels spécifiques à l'IA, y compris les GPU, les TPU et les accélérateurs IA spécialisés.

|   #   | Description                                                                                                                                                                                              | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.7.1 | Vérifiez qu'avant l'exécution de la charge de travail, l'intégrité de l'accélérateur d'IA est validée à l'aide de mécanismes d'attestation basés sur le matériel (par exemple, TPM, DRTM ou équivalent). |   2    | D/V  |
| 4.7.2 | Vérifiez que la mémoire de l'accélérateur (GPU) est isolée entre les charges de travail via des mécanismes de partitionnement avec une sanitation de la mémoire entre les tâches.                        |   2    | D/V  |
| 4.7.3 | Vérifiez que les modules de sécurité matérielle (HSM) protègent les poids des modèles d'IA et les clés cryptographiques avec une certification conforme à FIPS 140-3 Niveau 3 ou Common Criteria EAL4+.  |   3    | D/V  |

---

## C4.8 Sécurité de l'IA en périphérie et distribuée

Déploiements AI distribués sécurisés incluant l'informatique en périphérie, l'apprentissage fédéré et les architectures multi-sites.

|   #   | Description                                                                                                                                                                                                      | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 4.8.1 | Vérifiez que les dispositifs AI en périphérie s'authentifient auprès de l'infrastructure centrale en utilisant le TLS mutuel.                                                                                    |   2    | D/V  |
| 4.8.2 | Vérifiez que les dispositifs périphériques mettent en œuvre un démarrage sécurisé avec des signatures vérifiées et une protection contre la régression afin d'éviter les attaques de rétrogradation du firmware. |   2    | D/V  |
| 4.8.3 | Vérifiez que la coordination de l’IA distribuée utilise des mécanismes de consensus tolérants aux fautes byzantines avec validation des participants et détection des nœuds malveillants.                        |   3    | D/V  |
| 4.8.4 | Vérifiez que la communication de la périphérie au cloud prend en charge la limitation de bande passante, la compression des données et le fonctionnement hors ligne sécurisé avec un stockage local chiffré.     |   3    | D/V  |

---

## Références

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)

