# 10 Robustesse adversarielle et défense de la vie privée

## Objectif de contrôle

Veiller à ce que les modèles d'IA restent fiables, respectueux de la vie privée et résistants à l'abus lorsqu'ils sont confrontés à des attaques d'évasion, d'inférence, d'extraction ou d'empoisonnement.

---

## 10.1 Alignement et sécurité du modèle

Évitez les sorties nuisibles ou qui enfreignent les politiques.

|   #    | description                                                                                                                                                  | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 10.1.1 | Vérifiez qu'une suite de tests d'alignement (prompts red-team, sondes de jailbreak, contenu interdit) est versionnée et exécutée à chaque version du modèle. |   1    | D/V  |
| 10.1.2 | Vérifiez que les garde-fous relatifs au refus et à la complétion sûre sont appliqués.                                                                        |   1    |  D   |
| 10.1.3 | Vérifiez que l’évaluateur automatisé mesure le taux de contenu nocif et signale les régressions au-delà d’un seuil défini.                                   |   2    | D/V  |
| 10.1.4 | Vérifiez que la formation anti-jailbreak est documentée et reproductible.                                                                                    |   2    |  D   |
| 10.1.5 | Vérifiez que les preuves formelles de conformité des politiques ou une surveillance certifiée couvrent des domaines critiques.                               |   3    |  V   |

---

## 10.2 Renforcement des exemples adverses

Renforcer la résilience face aux entrées manipulées. Un entraînement adversarial robuste et une évaluation par benchmarks constituent les meilleures pratiques actuelles.

|   #    | description                                                                                                                                 | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.2.1 | Vérifiez que les dépôts de projets incluent des configurations d'entraînement adversarial avec des graines reproductibles.                  |   1    |  D   |
| 10.2.2 | Vérifiez que la détection d'exemples adversariaux déclenche des alertes bloquantes dans les pipelines de production.                        |   2    | D/V  |
| 10.2.4 | Vérifiez que les preuves de robustesse certifiée ou les certificats à bornes d'intervalle couvrent au moins les classes les plus critiques. |   3    |  V   |
| 10.2.5 | Vérifiez que les tests de régression utilisent des attaques adaptatives pour confirmer l’absence de perte de robustesse mesurable.          |   3    |  V   |

---

## 10.3 Atténuation de l'inférence d'appartenance

Limiter la capacité à déterminer si un enregistrement faisait partie des données d'entraînement. La confidentialité différentielle et le masquage du score de confiance restent les défenses les plus efficaces à ce jour.

|   #    | description                                                                                                                                | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 10.3.1 | Vérifiez que la régularisation de l'entropie par requête ou la mise à l'échelle par température réduisent les prédictions trop confiantes. |   1    |  D   |
| 10.3.2 | Vérifiez que l’entraînement utilise une optimisation différentiellement privée bornée par ε pour des ensembles de données sensibles.       |   2    |  D   |
| 10.3.3 | Vérifiez que les simulations d'attaque (shadow-model ou black-box) affichent l'AUC d'attaque ≤ 0.60 sur des données hors-échantillon.      |   2    |  V   |

---

## 10.4 Modèle-Inversion Résistance

Empêcher la reconstruction d'attributs privés. Des enquêtes récentes mettent en avant la troncation des sorties et les garanties de confidentialité différentielle comme des défenses pratiques.

|   #    | description                                                                                                                                                | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.4.1 | Vérifiez que les attributs sensibles ne sont jamais directement affichés; là où c'est nécessaire, utilisez des seaux ou des transformations à sens unique. |   1    |  D   |
| 10.4.2 | Vérifiez que les limites de débit des requêtes ralentissent les requêtes adaptatives répétées provenant du même principal.                                 |   1    | D/V  |
| 10.4.3 | Vérifiez que le modèle est entraîné avec du bruit préservant la vie privée.                                                                                |   2    |  D   |

---

## 10.5 Défense contre Model-Extraction

Détecter et dissuader le clonage non autorisé. Le filigrage et l’analyse des motifs de requête sont recommandés.

|   #    | description                                                                                                                                               | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.5.1 | Vérifiez que les passerelles d’inférence appliquent des limites de débit globales et par clé API, réglées en fonction du seuil de mémorisation du modèle. |   1    |  D   |
| 10.5.2 | Vérifiez que les statistiques de query-entropy et d'input-plurality alimentent un détecteur d'extraction automatisé.                                      |   2    | D/V  |
| 10.5.3 | Vérifiez que les filigranes fragiles ou probabilistes peuvent être démontrés avec p < 0.01 en ≤ 1 000 requêtes contre un clone suspecté.                  |   2    |  V   |
| 10.5.4 | Vérifiez que les clés de filigrane et les ensembles déclencheurs sont stockés dans un module matériel de sécurité et renouvelés chaque année.             |   3    |  D   |
| 10.5.5 | Vérifiez que les événements d'alerte d'extraction incluent les requêtes malveillantes et qu'ils sont intégrés aux playbooks de réponse aux incidents.     |   3    |  V   |

---

## 10.6 Détection des données empoisonnées au moment de l'inférence

Identifier et neutraliser les entrées présentant une porte dérobée ou empoisonnées.

|   #    | description                                                                                                                                            | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 10.6.1 | Vérifier que les entrées passent par un détecteur d’anomalies (par exemple STRIP, score de cohérence) avant l’inférence du modèle.                     |   1    |  D   |
| 10.6.2 | Vérifiez que les seuils du détecteur sont ajustés sur des ensembles de validation propres et empoisonnés afin d'obtenir moins de 5 % de faux positifs. |   1    |  V   |
| 10.6.3 | Vérifiez que les entrées signalées comme empoisonnées déclenchent le blocage doux et les workflows de révision humaine.                                |   2    |  D   |
| 10.6.4 | Vérifiez que les détecteurs sont soumis à des tests de résistance avec des attaques par porte dérobée adaptatives et sans déclencheur.                 |   2    |  V   |
| 10.6.5 | Vérifiez que les métriques d'efficacité de la détection sont enregistrées et réévaluées périodiquement avec des renseignements sur les menaces à jour. |   3    |  D   |

---

## 10.7 Adaptation dynamique de la politique de sécurité

Mises à jour de la politique de sécurité en temps réel basées sur l'intelligence des menaces et l'analyse comportementale.

|   #    | description                                                                                                                                                                                        | Niveau | Rôle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.7.1 | Vérifiez que les politiques de sécurité peuvent être mises à jour dynamiquement sans redémarrage de l’agent, tout en maintenant l’intégrité des versions des politiques.                           |   1    | D/V  |
| 10.7.2 | Vérifiez que les mises à jour des politiques sont signées cryptographiquement par du personnel de sécurité autorisé et validées avant leur application.                                            |   2    | D/V  |
| 10.7.3 | Vérifiez que les modifications dynamiques des politiques sont enregistrées avec des traces d'audit complètes, y compris la justification, les chaînes d'approbation et les procédures de rollback. |   2    | D/V  |
| 10.7.4 | Vérifiez que les mécanismes de sécurité adaptatifs ajustent la sensibilité de la détection des menaces en fonction du contexte de risque et des comportements.                                     |   3    | D/V  |
| 10.7.5 | Vérifiez que les décisions d'adaptation des politiques sont explicables et incluez des traces probantes pour l'examen par l'équipe de sécurité.                                                    |   3    | D/V  |

---

## 10.8 Analyse de sécurité basée sur la réflexion

Validation de sécurité par l'auto-réflexion de l'agent et l'analyse métacognitive.

|   #    | description                                                                                                                                                             | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.8.1 | Vérifiez que les mécanismes de réflexion des agents incluent une auto-évaluation axée sur la sécurité des décisions et des actions.                                     |   1    | D/V  |
| 10.8.2 | Vérifiez que les sorties de réflexion sont validées afin d'empêcher la manipulation des mécanismes d'auto-évaluation par des entrées adverses.                          |   2    | D/V  |
| 10.8.3 | Vérifiez que l’analyse de sécurité métacognitive identifie les biais potentiels, les manipulations ou les compromissions dans les processus de raisonnement de l’agent. |   2    | D/V  |
| 10.8.4 | Vérifiez que les avertissements de sécurité basés sur la réflexion déclenchent une surveillance renforcée et des workflows d'intervention humaine potentiels.           |   3    | D/V  |
| 10.8.5 | Vérifiez que l'apprentissage continu à partir des réflexions sur la sécurité améliore la détection des menaces sans dégrader les fonctionnalités légitimes.             |   3    | D/V  |

---

## 10.9 Évolution et sécurité de l'auto-amélioration

Mesures de sécurité pour les systèmes d'agents capables d'auto-modification et d'évolution.

|   #    | description                                                                                                                                     | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.9.1 | Vérifiez que les capacités d'auto-modification sont restreintes aux zones sûres désignées, avec des bornes de vérification formelle.            |   1    | D/V  |
| 10.9.2 | Vérifiez que les propositions d’évolution font l’objet d’une évaluation de l’impact sur la sécurité avant leur mise en œuvre.                   |   2    | D/V  |
| 10.9.3 | Vérifiez que les mécanismes d'auto-amélioration incluent des capacités de retour en arrière avec vérification d'intégrité.                      |   2    | D/V  |
| 10.9.4 | Vérifiez que la sécurité de l'apprentissage par méta-apprentissage empêche la manipulation adversarielle des algorithmes d'amélioration.        |   3    | D/V  |
| 10.9.5 | Vérifier que l'auto-amélioration récursive est bornée par des contraintes de sécurité formelles, avec des preuves mathématiques de convergence. |   3    | D/V  |

---

### Références

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

