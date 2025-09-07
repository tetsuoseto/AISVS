# 10 Robustesse adversariale et défense de la vie privée

## Objectif de contrôle

Assurer que les modèles d'IA restent fiables, respectueux de la vie privée et résistants aux abus face aux attaques d'évasion, d'inférence, d'extraction ou d'empoisonnement.

---

## 10.1 Alignement et sécurité du modèle

Se prémunir contre les résultats nuisibles ou contraires à la politique.

|   #    | Description                                                                                                                                                                  | Niveau | Rôle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.1.1 | Vérifiez qu'une suite de tests d'alignement (incitations de red-team, sondes de jailbreak, contenu interdit) est versionnée et exécutée à chaque nouvelle version du modèle. |   1    | D/V  |
| 10.1.2 | Vérifiez que les garde-fous de refus et de complétion sécurisée sont appliqués.                                                                                              |   1    |  D   |
| 10.1.3 | Vérifiez qu'un évaluateur automatisé mesure le taux de contenu nuisible et signale les régressions dépassant un seuil défini.                                                |   2    | D/V  |
| 10.1.4 | Vérifiez que la formation contre les jailbreaks est documentée et reproductible.                                                                                             |   2    |  D   |
| 10.1.5 | Vérifiez que les preuves formelles de conformité aux politiques ou la surveillance certifiée couvrent les domaines critiques.                                                |   3    |  V   |

---

## 10.2 Renforcement contre les exemples adversariaux

Augmenter la résilience face aux entrées manipulées. L'entraînement adversarial robuste et l'évaluation par benchmark sont les meilleures pratiques actuelles.

|   #    | Description                                                                                                                                         | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.2.1 | Vérifiez que les répertoires de projets incluent des configurations d'entraînement adversarial avec des graines reproductibles.                     |   1    |  D   |
| 10.2.2 | Vérifiez que la détection des exemples adversariaux génère des alertes de blocage dans les pipelines de production.                                 |   2    | D/V  |
| 10.2.4 | Vérifiez que les preuves de robustesse certifiée ou les certificats de limites par intervalles couvrent au moins les classes critiques principales. |   3    |  V   |
| 10.2.5 | Vérifiez que les tests de régression utilisent des attaques adaptatives pour confirmer qu'il n'y a pas de perte mesurable de robustesse.            |   3    |  V   |

---

## 10.3 Atténuation de l'inférence d'appartenance

Limiter la capacité à déterminer si un enregistrement faisait partie des données d’entraînement. La confidentialité différentielle et le masquage du score de confiance restent les défenses connues les plus efficaces.

|   #    | Description                                                                                                                               | Niveau | Rôle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.3.1 | Vérifiez que la régularisation de l'entropie par requête ou la mise à l'échelle de la température réduit les prédictions trop confiantes. |   1    |  D   |
| 10.3.2 | Vérifiez que l'entraînement utilise une optimisation différentiellement privée bornée par ε pour les ensembles de données sensibles.      |   2    |  D   |
| 10.3.3 | Vérifiez que les simulations d'attaque (modèle fantôme ou boîte noire) affichent une AUC d'attaque ≤ 0,60 sur les données mises de côté.  |   2    |  V   |

---

## 10.4 Résistance à l'inversion de modèle

Empêcher la reconstruction des attributs privés. Des enquêtes récentes soulignent la troncature des sorties et les garanties de DP comme défenses pratiques.

|   #    | Description                                                                                                                                                  | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 10.4.1 | Vérifiez que les attributs sensibles ne sont jamais directement affichés ; si nécessaire, utilisez des catégories ou des transformations unidirectionnelles. |   1    |  D   |
| 10.4.2 | Vérifiez que les limites de taux de requête limitent les requêtes adaptatives répétées provenant du même principal.                                          |   1    | D/V  |
| 10.4.3 | Vérifiez que le modèle est entraîné avec un bruit préservant la vie privée.                                                                                  |   2    |  D   |

---

## 10.5 Défense contre l'extraction de modèle

Détecter et dissuader la copie non autorisée. Le tatouage numérique et l'analyse des motifs de requêtes sont recommandés.

|   #    | Description                                                                                                                                             | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.5.1 | Vérifiez que les passerelles d'inférence appliquent des limites de fréquence globales et par clé API adaptées au seuil de mémorisation du modèle.       |   1    |  D   |
| 10.5.2 | Vérifiez que les statistiques de query-entropy et input-plurality alimentent un détecteur d'extraction automatisée.                                     |   2    | D/V  |
| 10.5.3 | Vérifiez que les filigranes fragiles ou probabilistes peuvent être prouvés avec p < 0,01 en ≤ 1 000 requêtes contre un clone suspect.                   |   2    |  V   |
| 10.5.4 | Vérifiez que les clés de filigrane et les ensembles de déclencheurs sont stockés dans un module de sécurité matérielle et sont renouvelés chaque année. |   3    |  D   |
| 10.5.5 | Vérifiez que les événements d'alerte d'extraction incluent les requêtes incriminées et sont intégrés aux feuilles de route de réponse aux incidents.    |   3    |  V   |

---

## 10.6 Détection des données empoisonnées en temps d'inférence

Identifier et neutraliser les entrées avec portes dérobées ou empoisonnées.

|   #    | Description                                                                                                                                             | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.6.1 | Vérifiez que les entrées passent par un détecteur d'anomalies (par exemple, STRIP, notation de cohérence) avant l'inférence du modèle.                  |   1    |  D   |
| 10.6.2 | Vérifiez que les seuils du détecteur sont ajustés sur des ensembles de validation propres/empoisonnés pour atteindre moins de 5 % de faux positifs.     |   1    |  V   |
| 10.6.3 | Vérifiez que les entrées signalées comme empoisonnées déclenchent le blocage souple et les flux de travail de révision humaine.                         |   2    |  D   |
| 10.6.4 | Vérifiez que les détecteurs sont soumis à un test de résistance avec des attaques d’arrière-plan adaptatives sans déclencheur.                          |   2    |  V   |
| 10.6.5 | Vérifiez que les métriques d'efficacité de détection sont enregistrées et réévaluées périodiquement avec des renseignements sur les menaces actualisés. |   3    |  D   |

---

## 10.7 Adaptation Dynamique de la Politique de Sécurité

Mises à jour en temps réel des politiques de sécurité basées sur le renseignement sur les menaces et l'analyse comportementale.

|   #    | Description                                                                                                                                                                                                  | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 10.7.1 | Vérifiez que les politiques de sécurité peuvent être mises à jour dynamiquement sans redémarrage de l'agent tout en maintenant l'intégrité de la version de la politique.                                    |   1    | D/V  |
| 10.7.2 | Vérifiez que les mises à jour de la politique sont signées cryptographiquement par le personnel de sécurité autorisé et validées avant leur application.                                                     |   2    | D/V  |
| 10.7.3 | Vérifiez que les modifications dynamiques de la politique sont enregistrées avec des pistes d'audit complètes, y compris la justification, les chaînes d'approbation et les procédures de retour en arrière. |   2    | D/V  |
| 10.7.4 | Vérifiez que les mécanismes de sécurité adaptatifs ajustent la sensibilité de détection des menaces en fonction du contexte de risque et des schémas comportementaux.                                        |   3    | D/V  |
| 10.7.5 | Vérifiez que les décisions d’adaptation de la politique sont explicables et incluent des traces de preuves pour la revue par l’équipe de sécurité.                                                           |   3    | D/V  |

---

## 10.8 Analyse de sécurité basée sur la réflexion

Validation de la sécurité par auto-réflexion de l'agent et analyse métacognitive.

|   #    | Description                                                                                                                                                         | Niveau | Rôle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.8.1 | Vérifiez que les mécanismes de réflexion de l'agent incluent une auto-évaluation axée sur la sécurité des décisions et des actions.                                 |   1    | D/V  |
| 10.8.2 | Vérifiez que les sorties de réflexion sont validées afin d'empêcher la manipulation des mécanismes d'auto-évaluation par des entrées adverses.                      |   2    | D/V  |
| 10.8.3 | Vérifiez que l'analyse de sécurité métacognitive identifie les biais potentiels, la manipulation ou la compromission dans les processus de raisonnement de l'agent. |   2    | D/V  |
| 10.8.4 | Vérifiez que les avertissements de sécurité basés sur la réflexion déclenchent une surveillance renforcée et des workflows d'intervention humaine potentielle.      |   3    | D/V  |
| 10.8.5 | Vérifiez que l'apprentissage continu à partir des réflexions sur la sécurité améliore la détection des menaces sans dégrader la fonctionnalité légitime.            |   3    | D/V  |

---

## 10.9 Sécurité de l'évolution et de l'auto-amélioration

Contrôles de sécurité pour les systèmes d'agents capables d'auto-modification et d'évolution.

|   #    | Description                                                                                                                                         | Niveau | Rôle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 10.9.1 | Vérifiez que les capacités d'auto-modification sont limitées aux zones sûres désignées avec des limites de vérification formelle.                   |   1    | D/V  |
| 10.9.2 | Vérifiez que les propositions d'évolution font l'objet d'une évaluation de l'impact sur la sécurité avant leur mise en œuvre.                       |   2    | D/V  |
| 10.9.3 | Vérifiez que les mécanismes d'auto-amélioration incluent des capacités de retour arrière avec vérification de l'intégrité.                          |   2    | D/V  |
| 10.9.4 | Vérifiez que la sécurité de la méta-apprentissage empêche la manipulation malveillante des algorithmes d'amélioration.                              |   3    | D/V  |
| 10.9.5 | Vérifiez que l'amélioration autonome récursive est limitée par des contraintes formelles de sécurité avec des preuves mathématiques de convergence. |   3    | D/V  |

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

