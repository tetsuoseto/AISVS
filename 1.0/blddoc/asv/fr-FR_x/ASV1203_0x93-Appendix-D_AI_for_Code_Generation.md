# Annexe D : Gouvernance et vérification du codage sécurisé assisté par IA

## Objectif

Ce chapitre définit les contrôles organisationnels de base pour l'utilisation sûre et efficace des outils de codage assistés par IA lors du développement logiciel, garantissant la sécurité et la traçabilité tout au long du cycle de vie du développement logiciel (SDLC).

---

## AD.1 Flux de travail de codage sécurisé assisté par IA

Intégrer les outils d’IA dans le cycle de vie du développement sécurisé des logiciels (SSDLC) de l’organisation sans affaiblir les barrières de sécurité existantes.

|   #    | Description                                                                                                                                                                                       | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.1.1 | Vérifiez qu'un flux de travail documenté décrit quand et comment les outils d'IA peuvent générer, refactoriser ou examiner du code.                                                               |   1    | D/V  |
| AD.1.2 | Vérifiez que le flux de travail correspond à chaque phase du SSDLC (conception, mise en œuvre, revue de code, tests, déploiement).                                                                |   2    |  D   |
| AD.1.3 | Vérifiez que les métriques (par exemple, la densité de vulnérabilité, le temps moyen de détection) sont collectées sur le code produit par l'IA et comparées aux référentiels humains uniquement. |   3    | D/V  |

---

## AD.2 Qualification des outils d'IA et modélisation des menaces

Veillez à ce que les outils de codage IA soient évalués en termes de capacités de sécurité, de risques et d'impact sur la chaîne d'approvisionnement avant leur adoption.

|   #    | Description                                                                                                                                                                                                                | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.2.1 | Vérifiez qu'un modèle de menace pour chaque outil d'IA identifie les risques d'utilisation abusive, d'inversion de modèle, de fuite de données et de chaîne de dépendances.                                                |   1    | D/V  |
| AD.2.2 | Vérifiez que les évaluations des outils incluent une analyse statique/dynamique de tous les composants locaux ainsi qu’une évaluation des points de terminaison SaaS (TLS, authentification/autorisation, journalisation). |   2    |  D   |
| AD.2.3 | Vérifiez que les évaluations suivent un cadre reconnu et sont refaites après des changements majeurs de version.                                                                                                           |   3    | D/V  |

---

## AD.3 Gestion sécurisée des invites et du contexte

Prévenir la fuite de secrets, de code propriétaire et de données personnelles lors de la construction de prompts ou de contextes pour les modèles d'IA.

|   #    | Description                                                                                                                                                                               | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.3.1 | Vérifiez que les directives écrites interdisent l'envoi de secrets, d'identifiants ou de données classifiées dans les prompts.                                                            |   1    | D/V  |
| AD.3.2 | Vérifiez que les contrôles techniques (rédaction côté client, filtres de contexte approuvés) suppriment automatiquement les éléments sensibles.                                           |   2    |  D   |
| AD.3.3 | Vérifiez que les invites et les réponses sont tokenisées, chiffrées en transit et au repos, et que les périodes de rétention sont conformes à la politique de classification des données. |   3    | D/V  |

---

## AD.4 Validation du code généré par l'IA

Détecter et corriger les vulnérabilités introduites par la sortie de l'IA avant que le code ne soit fusionné ou déployé.

|   #    | Description                                                                                                                                                                                                     | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.4.1 | Vérifiez que le code généré par l'IA soit toujours soumis à une revue de code humaine.                                                                                                                          |   1    | D/V  |
| AD.4.2 | Vérifiez que les scanners automatisés (SAST/IAST/DAST) sont exécutés sur chaque demande de fusion contenant du code généré par l'IA et empêchent les fusions en cas de détections critiques.                    |   2    |  D   |
| AD.4.3 | Vérifiez que les tests de fuzzing différentiel ou les tests basés sur les propriétés prouvent les comportements critiques pour la sécurité (par exemple, la validation des entrées, la logique d'autorisation). |   3    | D/V  |

---

## AD.5 Explicabilité et Traçabilité des Suggestions de Code

Fournir aux auditeurs et aux développeurs des informations sur les raisons pour lesquelles une suggestion a été faite et comment elle a évolué.

|   #    | Description                                                                                                                                                                                            | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| AD.5.1 | Vérifiez que les paires invite/réponse sont enregistrées avec les identifiants de commit.                                                                                                              |   1    | D/V  |
| AD.5.2 | Vérifiez que les développeurs peuvent afficher les citations du modèle (extraits d'entraînement, documentation) soutenant une suggestion.                                                              |   2    |  D   |
| AD.5.3 | Vérifiez que les rapports d'explicabilité sont stockés avec les artefacts de conception et référencés dans les revues de sécurité, satisfaisant ainsi les principes de traçabilité de l'ISO/IEC 42001. |   3    | D/V  |

---

## AD.6 Retour Continu et Affinage du Modèle

Améliorer les performances de sécurité du modèle au fil du temps tout en empêchant la dérive négative.

|   #    | Description                                                                                                                                                                                                                             | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.6.1 | Vérifiez que les développeurs peuvent signaler les suggestions non sécurisées ou non conformes, et que ces signalements sont suivis.                                                                                                    |   1    | D/V  |
| AD.6.2 | Vérifiez que les retours agrégés alimentent le réglage périodique ou la génération augmentée par récupération avec des corpus de codage sécurisé vérifiés (par exemple, les Cheat Sheets d’OWASP).                                      |   2    |  D   |
| AD.6.3 | Vérifiez qu'un dispositif d'évaluation en boucle fermée exécute des tests de régression après chaque ajustement fin ; les métriques de sécurité doivent atteindre ou dépasser les niveaux de référence précédents avant le déploiement. |   3    | D/V  |

---

### Références

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

