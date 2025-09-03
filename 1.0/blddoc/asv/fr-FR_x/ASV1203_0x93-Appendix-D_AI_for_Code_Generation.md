# Annexe D: Gouvernance et vérification du codage sécurisé assisté par l'IA

## Objectif

Ce chapitre définit les contrôles organisationnels de référence pour l'utilisation sûre et efficace des outils de codage assistés par l'IA pendant le développement logiciel, assurant la sécurité et la traçabilité tout au long du SDLC.

---

## AD.1 Flux de travail de codage‑sécurisé assisté par l'IA

Intégrer les outils d’IA dans le cycle de vie sécurisé du développement logiciel de l’organisation (SSDLC) sans affaiblir les garde-fous de sécurité existants.

|   #    | description                                                                                                                                                                                  | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.1.1 | Assurez-vous qu'un flux de travail documenté décrit quand et comment les outils d'IA peuvent générer, refactoriser ou examiner le code.                                                      |   1    | D/V  |
| AD.1.2 | Vérifiez que le flux de travail correspond à chaque phase du SSDLC (conception, mise en œuvre, revue de code, tests, déploiement).                                                           |   2    |  D   |
| AD.1.3 | Vérifiez que les métriques (par exemple, densité de vulnérabilités, temps moyen de détection) sont collectées sur le code généré par l’IA et comparées à des références uniquement humaines. |   3    | D/V  |

---

## AD.2 Qualification des outils d'IA et modélisation des menaces

Assurez-vous que les outils de codage basés sur l’IA soient évalués en termes de capacités de sécurité, de risques et d’impact sur la chaîne d’approvisionnement avant leur adoption.

|   #    | description                                                                                                                                                                                                      | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.2.1 | Vérifiez qu'un modèle de menace pour chaque outil d'IA identifie l'utilisation abusive, l'inversion de modèle, les fuites de données et les risques liés à la chaîne de dépendances.                             |   1    | D/V  |
| AD.2.2 | Vérifiez que les évaluations des outils incluent l’analyse statique/dynamique de tous les composants locaux et l’évaluation des points de terminaison SaaS (TLS, authentification/autorisation, journalisation). |   2    |  D   |
| AD.2.3 | Vérifiez que les évaluations suivent un cadre reconnu et qu'elles sont ré‑effectuées après des changements de version majeurs.                                                                                   |   3    | D/V  |

---

## AD.3 Gestion sécurisée du prompt et du contexte

Prévenir la fuite de secrets, de code propriétaire et de données personnelles lors de l'élaboration de prompts ou de contextes pour des modèles d’IA.

|   #    | description                                                                                                                                                                     | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.3.1 | Vérifiez que les directives écrites interdisent l'envoi de secrets, d'identifiants ou de données classifiées dans les invites.                                                  |   1    | D/V  |
| AD.3.2 | Vérifiez que les contrôles techniques (rédaction côté client, filtres de contexte approuvés) suppriment automatiquement les artefacts sensibles.                                |   2    |  D   |
| AD.3.3 | Vérifiez que les invites et les réponses sont tokenisées, chiffrées en transit et au repos, et que les périodes de conservation respectent la politique de data‑classification. |   3    | D/V  |

---

## AD.4 Validation du code généré par l'IA

Détecter et remédier aux vulnérabilités introduites par la sortie générée par l'IA avant que le code ne soit fusionné ou déployé.

|   #    | description                                                                                                                                                                                           | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.4.1 | Vérifiez que le code généré par l’IA est toujours soumis à une revue de code par des humains.                                                                                                         |   1    | D/V  |
| AD.4.2 | Vérifiez que les analyseurs automatisés (SAST/IAST/DAST) s'exécutent sur chaque pull request contenant du code généré par l'IA et bloquent les fusions en cas de constats critiques.                  |   2    |  D   |
| AD.4.3 | Vérifiez que le fuzzing différentiel ou les tests basés sur les propriétés prouvent les comportements critiques en matière de sécurité (par exemple, validation des entrées, logique d'autorisation). |   3    | D/V  |

---

## AD.5 Explicabilité et traçabilité des suggestions de code

Fournir aux auditeurs et aux développeurs un aperçu des raisons pour lesquelles une suggestion a été faite et de son évolution.

|   #    | description                                                                                                                                                                                 | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.5.1 | Vérifiez que les paires prompt/réponse sont enregistrées avec des identifiants de commit.                                                                                                   |   1    | D/V  |
| AD.5.2 | Vérifiez que les développeurs peuvent faire apparaître des citations du modèle (extraits d'entraînement, documentation) qui étayent une suggestion.                                         |   2    |  D   |
| AD.5.3 | Vérifiez que les rapports d’explicabilité sont stockés avec les artefacts de conception et référencés dans les revues de sécurité, conformément aux principes de traçabilité ISO/IEC 42001. |   3    | D/V  |

---

## AD.6 Rétroaction continue & réglage fin du modèle

Améliorer les performances de sécurité du modèle au fil du temps tout en évitant la dérive négative.

|   #    | description                                                                                                                                                                                                            | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| AD.6.1 | Vérifiez que les développeurs peuvent signaler des suggestions peu sûres ou non‑conformes, et que les drapeaux sont suivis.                                                                                            |   1    | D/V  |
| AD.6.2 | Vérifiez que les retours agrégés informent un affinage‑périodique ou une génération‑augmentée par récupération avec des corpus de codage sécurisé vérifiés (par exemple, OWASP Cheat Sheets).                          |   2    |  D   |
| AD.6.3 | Vérifier qu'un cadre d’évaluation en boucle fermée exécute des tests de régression après chaque réglage‑fin ; les métriques de sécurité doivent atteindre ou dépasser les références antérieures avant le déploiement. |   3    | D/V  |

---

### Références

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

