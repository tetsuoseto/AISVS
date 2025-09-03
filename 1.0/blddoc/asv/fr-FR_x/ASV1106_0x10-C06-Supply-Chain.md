# C6 Sécurité de la chaîne d'approvisionnement pour les modèles, frameworks et données

## Objectif de contrôle

Les attaques de la chaîne d'approvisionnement en IA exploitent des modèles, cadres ou ensembles de données fournis par des tiers pour intégrer des portes dérobées, des biais ou du code exploitable. Ces contrôles offrent une traçabilité de bout en bout, la gestion des vulnérabilités et la surveillance pour protéger l'ensemble du cycle de vie du modèle.

---

## C6.1 Évaluation et provenance des modèles pré-entraînés

Évaluer et authentifier les origines des modèles tiers, leurs licences et les comportements cachés avant tout affinage ou déploiement.

|   #   | description                                                                                                                                                                 | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.1.1 | Vérifiez que chaque artefact de modèle tiers‑partie comprend un enregistrement de provenance signé qui identifie le dépôt source et le hash du commit.                      |   1    | D/V  |
| 6.1.2 | Vérifiez que les modèles sont scannés à l’aide d’outils automatisés pour détecter des couches malveillantes ou des déclencheurs de cheval de Troie avant l’importation.     |   1    | D/V  |
| 6.1.3 | Vérifiez que les réglages fins par transfert d'apprentissage passent l'évaluation adversariale pour détecter les comportements cachés.                                      |   2    |  D   |
| 6.1.4 | Vérifiez que les licences des modèles, les étiquettes d'export‑contrôle et les déclarations d'origine des données sont enregistrées dans une entrée ML‑BOM.                 |   2    |  V   |
| 6.1.5 | Vérifiez que les modèles à haut risque (poids téléversés publiquement, créateurs non vérifiés) restent en quarantaine jusqu'à l'examen et l'approbation par un être humain. |   3    | D/V  |

---

## C6.2 Analyse des frameworks et des bibliothèques

Analysez en continu les frameworks et bibliothèques d'apprentissage automatique pour les CVEs et le code malveillant afin de garantir la sécurité de la pile d'exécution.

|   #   | description                                                                                                                                                | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.2.1 | Vérifiez que les pipelines CI exécutent des analyseurs de dépendances sur les frameworks d'IA et les bibliothèques critiques.                              |   1    | D/V  |
| 6.2.2 | Vérifiez que les vulnérabilités critiques (CVSS ≥ 7.0) empêchent la promotion vers les images de production.                                               |   1    | D/V  |
| 6.2.3 | Vérifiez que l’analyse statique du code s’exécute sur des bibliothèques ML forkées ou vendues en interne.                                                  |   2    |  D   |
| 6.2.4 | Vérifiez que les propositions de mise à niveau du cadre incluent une évaluation de l'impact sur la sécurité faisant référence aux flux CVE publics.        |   2    |  V   |
| 6.2.5 | Vérifiez que les capteurs d'exécution déclenchent des alertes lorsque des chargements dynamiques de bibliothèques inattendus s'écartent de la SBOM signée. |   3    |  V   |

---

## C6.3 Verrouillage des dépendances et vérification

Fixer chaque dépendance à des empreintes immuables et reproduire les builds afin de garantir des artefacts identiques et inviolables.

|   #   | description                                                                                                                              | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.3.1 | Vérifiez que tous les gestionnaires de paquets imposent le verrouillage des versions via les fichiers de verrouillage.                   |   1    | D/V  |
| 6.3.2 | Vérifiez que les digests immuables sont utilisés plutôt que des tags mutables dans les références de conteneurs.                         |   1    | D/V  |
| 6.3.3 | Vérifiez que les contrôles de reproducible‑build comparent les hachages entre les exécutions CI afin de garantir des sorties identiques. |   2    |  D   |
| 6.3.4 | Vérifiez que les attestations de build sont conservées pendant 18 mois pour assurer la traçabilité lors des audits.                      |   2    |  V   |
| 6.3.5 | Vérifiez que les dépendances expirées déclenchent des PR automatisées pour mettre à jour ou forker des versions épinglées.               |   3    |  D   |

---

## C6.4 Application des sources de confiance

Autoriser les téléchargements d'artefacts uniquement à partir de sources vérifiées cryptographiquement et approuvées par l'organisation, et bloquer tout le reste.

|   #   | description                                                                                                                                                       | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.4.1 | Vérifiez que les poids du modèle, les ensembles de données et les conteneurs sont téléchargés uniquement depuis des domaines approuvés ou des registres internes. |   1    | D/V  |
| 6.4.2 | Vérifiez que les signatures Sigstore/Cosign valident l'identité de l'éditeur avant que les artefacts ne soient mis en cache localement.                           |   1    | D/V  |
| 6.4.3 | Vérifiez que les proxys de sortie bloquent les téléchargements d’artefacts non authentifiés afin de faire respecter la politique des sources fiables.             |   2    |  D   |
| 6.4.4 | Vérifiez que les listes blanches du dépôt sont examinées trimestriellement avec des preuves de justification métier pour chaque entrée.                           |   2    |  V   |
| 6.4.5 | Vérifiez que les violations de la politique déclenchent la mise en quarantaine des artefacts et le retour en arrière des exécutions de pipeline dépendantes.      |   3    |  V   |

---

## C6.5 Évaluation des risques des jeux de données tiers

Évaluer les ensembles de données externes pour l’empoisonnement des données, les biais et la conformité juridique, et les surveiller tout au long de leur cycle de vie.

|   #   | description                                                                                                                                                                          | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 6.5.1 | Vérifiez que les ensembles de données externes subissent une évaluation du risque d'empoisonnement (par exemple, empreinte numérique des données, détection des valeurs aberrantes). |   1    | D/V  |
| 6.5.2 | Vérifiez que les métriques de biais (parité démographique, égalité des chances) sont calculées avant l'approbation du jeu de données.                                                |   1    |  D   |
| 6.5.3 | Vérifiez que la provenance et les termes de licence des ensembles de données sont capturés dans les entrées ML‑BOM.                                                                  |   2    |  V   |
| 6.5.4 | Vérifiez que la surveillance périodique détecte la dérive ou la corruption des ensembles de données hébergés.                                                                        |   2    |  V   |
| 6.5.5 | Vérifiez que le contenu interdit (droits d’auteur, informations personnelles identifiables) est supprimé par un nettoyage automatisé avant l’entraînement.                           |   3    |  D   |

---

## C6.6 Surveillance des attaques de la chaîne d'approvisionnement

Détecter les menaces de la chaîne d'approvisionnement tôt grâce aux flux CVE, à l'analyse des journaux d'audit et aux simulations de l'équipe rouge.

|   #   | description                                                                                                                                                                       | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.6.1 | Vérifiez que les journaux d’audit CI/CD sont acheminés vers les détections SIEM pour les téléchargements de paquets anormaux ou les étapes de build altérées.                     |   1    |  V   |
| 6.6.2 | Vérifiez que les playbooks de réponse aux incidents incluent des procédures de rollback pour des modèles ou des bibliothèques qui ont été compromis.                              |   2    |  D   |
| 6.6.3 | Vérifiez que l'enrichissement par renseignement sur les menaces marque les indicateurs ML‑spécifiques (par exemple, IoCs d'empoisonnement de modèles) dans le triage des alertes. |   3    |  V   |

---

## C6.7 ML‑BOM pour les artefacts du modèle

Générer et signer des SBOM détaillés spécifiques à l'apprentissage automatique (ML‑BOMs) afin que les consommateurs en aval puissent vérifier l'intégrité des composants au moment du déploiement.

|   #   | description                                                                                                                                       | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.7.1 | Vérifiez que chaque artefact de modèle publie un ML‑BOM qui répertorie les ensembles de données, les poids, les hyperparamètres et les licences.  |   1    | D/V  |
| 6.7.2 | Vérifiez que la génération ML‑BOM et la signature Cosign sont automatisées dans l’intégration continue et obligatoires pour la fusion.            |   1    | D/V  |
| 6.7.3 | Vérifiez que les vérifications de complétude ML‑BOM font échouer la compilation si des métadonnées de composants (hash, licence) sont manquantes. |   2    |  D   |
| 6.7.4 | Vérifiez que les consommateurs en aval peuvent interroger les ML-BOMs via l'API pour valider les modèles importés au moment du déploiement.       |   2    |  V   |
| 6.7.5 | Vérifiez que les ML‑BOMs font l'objet d'un contrôle de version et d'un diff afin de détecter les modifications non autorisées.                    |   3    |  V   |

---

## Références

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

