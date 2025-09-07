# Sécurité de la chaîne d'approvisionnement C6 pour les modèles, les frameworks et les données

## Objectif de contrôle

Les attaques sur la chaîne d'approvisionnement de l'IA exploitent des modèles, des frameworks ou des ensembles de données tiers pour intégrer des portes dérobées, des biais ou du code exploitable. Ces contrôles offrent une traçabilité complète, une gestion des vulnérabilités et une surveillance afin de protéger l'ensemble du cycle de vie du modèle.

---

## C6.1 Vérification et provenance des modèles préentraînés

Évaluer et authentifier les origines des modèles tiers, les licences, et les comportements cachés avant tout ajustement ou déploiement.

|   #   | Description                                                                                                                                                                | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.1.1 | Vérifiez que chaque artefact de modèle tiers inclut un enregistrement de provenance signé identifiant le dépôt source et le hachage du commit.                             |   1    | D/V  |
| 6.1.2 | Vérifiez que les modèles sont analysés à la recherche de couches malveillantes ou de déclencheurs de cheval de Troie à l'aide d'outils automatisés avant leur importation. |   1    | D/V  |
| 6.1.3 | Vérifiez que l’apprentissage par transfert affine avec ajustement passe l’évaluation adversariale pour détecter les comportements cachés.                                  |   2    |  D   |
| 6.1.4 | Vérifiez que les licences des modèles, les étiquettes de contrôle des exportations et les déclarations d'origine des données sont enregistrées dans une entrée ML-BOM.     |   2    |  V   |
| 6.1.5 | Vérifiez que les modèles à haut risque (poids téléchargés publiquement, créateurs non vérifiés) restent en quarantaine jusqu'à la revue et l'approbation humaine.          |   3    | D/V  |

---

## C6.2 Analyse des Frameworks et Bibliothèques

Analyser en continu les frameworks et bibliothèques de ML pour les CVE et le code malveillant afin de maintenir la sécurité de la pile d'exécution.

|   #   | Description                                                                                                                                             | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.2.1 | Vérifiez que les pipelines CI exécutent des analyseurs de dépendances sur les frameworks d'IA et les bibliothèques critiques.                           |   1    | D/V  |
| 6.2.2 | Vérifiez que les vulnérabilités critiques (CVSS ≥ 7,0) empêchent la promotion vers les images de production.                                            |   1    | D/V  |
| 6.2.3 | Vérifiez que l'analyse statique du code s'exécute sur les bibliothèques ML forkées ou vendues.                                                          |   2    |  D   |
| 6.2.4 | Vérifiez que les propositions de mise à niveau du framework incluent une évaluation de l'impact sur la sécurité faisant référence aux flux CVE publics. |   2    |  V   |
| 6.2.5 | Vérifiez que les capteurs en temps réel alertent sur les chargements inattendus de bibliothèques dynamiques qui dévient du SBOM signé.                  |   3    |  V   |

---

## C6.3 Verrouillage des dépendances et vérification

Verrouillez chaque dépendance sur des digests immuables et reproduisez les builds pour garantir des artefacts identiques et intègres.

|   #   | Description                                                                                                                                      | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 6.3.1 | Vérifiez que tous les gestionnaires de paquets appliquent le verrouillage de version via des fichiers de verrouillage.                           |   1    | D/V  |
| 6.3.2 | Vérifiez que des empreintes immuables sont utilisées au lieu de tags mutables dans les références aux conteneurs.                                |   1    | D/V  |
| 6.3.3 | Vérifiez que les contrôles de construction reproductible comparent les hachages entre les exécutions CI afin de garantir des sorties identiques. |   2    |  D   |
| 6.3.4 | Vérifiez que les attestations de compilation sont conservées pendant 18 mois pour la traçabilité des audits.                                     |   2    |  V   |
| 6.3.5 | Vérifiez que les dépendances expirées déclenchent des PR automatisées pour mettre à jour ou forker les versions épinglées.                       |   3    |  D   |

---

## C6.4 Application stricte des sources de confiance

Autoriser les téléchargements d'artefacts uniquement à partir de sources cryptographiquement vérifiées et approuvées par l'organisation, et bloquer tout le reste.

|   #   | Description                                                                                                                                                       | Niveau | Rôle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.4.1 | Vérifiez que les poids du modèle, les ensembles de données et les conteneurs sont téléchargés uniquement à partir de domaines approuvés ou de registres internes. |   1    | D/V  |
| 6.4.2 | Vérifiez que les signatures Sigstore/Cosign valident l'identité de l'éditeur avant que les artefacts ne soient mis en cache localement.                           |   1    | D/V  |
| 6.4.3 | Vérifiez que les proxys de sortie bloquent les téléchargements d’artefacts non authentifiés afin de faire respecter la politique de source de confiance.          |   2    |  D   |
| 6.4.4 | Vérifiez que les listes blanches des dépôts sont examinées trimestriellement avec une preuve de justification commerciale pour chaque entrée.                     |   2    |  V   |
| 6.4.5 | Vérifiez que les violations de politique entraînent la mise en quarantaine des artefacts et le retour en arrière des exécutions de pipeline dépendantes.          |   3    |  V   |

---

## C6.5 Évaluation des risques des ensembles de données tiers

Évaluer les ensembles de données externes pour le poisonnage, les biais, et la conformité légale, et les surveiller tout au long de leur cycle de vie.

|   #   | Description                                                                                                                                                                       | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.5.1 | Vérifiez que les jeux de données externes font l'objet d'une évaluation du risque de contamination (par exemple, empreinte des données, détection des valeurs aberrantes).        |   1    | D/V  |
| 6.5.2 | Vérifiez que les métriques de biais (parité démographique, égalité des chances) sont calculées avant l'approbation du jeu de données.                                             |   1    |  D   |
| 6.5.3 | Vérifiez que la provenance et les conditions de licence des ensembles de données sont enregistrées dans les entrées ML-BOM.                                                       |   2    |  V   |
| 6.5.4 | Vérifiez que la surveillance périodique détecte la dérive ou la corruption dans les ensembles de données hébergés.                                                                |   2    |  V   |
| 6.5.5 | Vérifiez que les contenus interdits (droits d'auteur, informations personnelles identifiables) sont supprimés automatiquement par un processus de nettoyage avant l'entraînement. |   3    |  D   |

---

## C6.6 Surveillance des attaques de la chaîne d'approvisionnement

Détectez précocement les menaces liées à la chaîne d'approvisionnement grâce aux flux CVE, à l'analyse des journaux d'audit et aux simulations d'équipe rouge.

|   #   | Description                                                                                                                                                    | Niveau | Rôle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.6.1 | Vérifiez que les journaux d'audit CI/CD sont transmis au SIEM pour la détection d'extractions de paquets anormales ou d'étapes de construction altérées.       |   1    |  V   |
| 6.6.2 | Vérifiez que les guides d'intervention en cas d'incident incluent des procédures de restauration pour les modèles ou bibliothèques compromis.                  |   2    |  D   |
| 6.6.3 | Vérifiez que l'enrichissement threat‑intel étiquette les indicateurs spécifiques au ML (par exemple, les IoC de corruption de modèle) lors du triage d'alerte. |   3    |  V   |

---

## C6.7 ML‑BOM pour les artefacts de modèle

Générez et signez des SBOMs détaillés spécifiques au ML (ML-BOMs) afin que les utilisateurs en aval puissent vérifier l'intégrité des composants au moment du déploiement.

|   #   | Description                                                                                                                                 | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 6.7.1 | Vérifiez que chaque artefact de modèle publie un ML-BOM qui liste les ensembles de données, les poids, les hyperparamètres et les licences. |   1    | D/V  |
| 6.7.2 | Vérifiez que la génération de ML‑BOM et la signature Cosign sont automatisées dans le CI et requises pour la fusion.                        |   1    | D/V  |
| 6.7.3 | Vérifiez que les contrôles de complétude ML‑BOM échouent la compilation si des métadonnées de composant (hachage, licence) sont manquantes. |   2    |  D   |
| 6.7.4 | Vérifiez que les consommateurs en aval peuvent interroger les ML-BOM via l'API pour valider les modèles importés au moment du déploiement.  |   2    |  V   |
| 6.7.5 | Vérifiez que les ML‑BOMs sont contrôlés en version et comparés pour détecter les modifications non autorisées.                              |   3    |  V   |

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

