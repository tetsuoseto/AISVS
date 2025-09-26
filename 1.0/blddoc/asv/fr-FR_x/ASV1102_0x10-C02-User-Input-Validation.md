# Validation des entrées utilisateur C2

## Objectif de contrôle

La validation robuste des entrées utilisateur est une ligne de défense primordiale contre certaines des attaques les plus dommageables sur les systèmes d'IA. Les attaques par injection de prompt peuvent ignorer les instructions du système, divulguer des données sensibles ou orienter le modèle vers un comportement non autorisé. À moins que des filtres dédiés et d'autres validations soient en place, les recherches montrent que les jailbreaks exploitant les fenêtres de contexte continueront d'être efficaces.

---

## C2.1 Défense contre l'injection de prompt

L'injection de prompt est l'un des principaux risques pour les systèmes d'IA. Les défenses contre cette tactique utilisent une combinaison de filtres de motifs, de classificateurs de données et de l'application hiérarchique des instructions.

|   #   | Description                                                                                                                                                                                                                                                                                | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 2.1.1 | Vérifiez que les entrées utilisateur sont contrôlées par rapport à une bibliothèque continuellement mise à jour de modèles connus d'injection de requêtes. Cela inclut les mots-clés de jailbreak, les instructions de type « ignorer le précédent » et les enchaînements de jeux de rôle. |   1    | D/V  |
| 2.1.2 | Vérifiez que le système applique une hiérarchie des instructions dans laquelle les messages système l'emportent sur les instructions utilisateur, même après le traitement des instructions utilisateur.                                                                                   |   1    | D/V  |
| 2.1.4 | Vérifiez que les invites provenant de contenus tiers (pages web, PDF, e-mails) sont nettoyées isolément avant d’être concaténées dans l’invite principale.                                                                                                                                 |   2    |  D   |

---

## C2.2 Résistance aux exemples adverses

Les modèles de traitement du langage naturel (NLP) restent vulnérables aux perturbations subtiles au niveau des caractères ou des mots que les humains manquent souvent mais que les modèles ont tendance à mal classifier.

|   #   | Description                                                                                                                                                                                                                                                                                                                                                                                       | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.2.1 | Vérifiez que les étapes de normalisation de base des entrées (NFC Unicode, mappage des homoglyphes, suppression des espaces superflus) sont effectuées avant la tokenisation.                                                                                                                                                                                                                     |   1    |  D   |
| 2.2.2 | Vérifiez que la détection d'anomalies statistiques signale les entrées avec une distance d'édition exceptionnellement élevée par rapport aux normes linguistiques ou des distances d'incorporation anormales.                                                                                                                                                                                     |   2    | D/V  |
| 2.2.3 | Vérifiez que le pipeline d'inférence prend en charge les variantes de modèles renforcés par entraînement adversarial ou les couches de défense (par exemple, la randomisation, la distillation défensive, les contrôles d'alignement) pour les points de terminaison à haut risque.                                                                                                               |   2    |  D   |
| 2.2.4 | Vérifiez que les entrées adverses suspectées sont mises en quarantaine et enregistrées avec leurs charges utiles complètes.                                                                                                                                                                                                                                                                       |   2    |  V   |
| 2.2.5 | Vérifiez que le détournement de codage et de représentation dans les entrées et sorties (par exemple, les caractères Unicode/invisibles de contrôle, les substitutions d'homoglyphes ou le texte à direction mixte) est détecté et atténué. Les atténuations approuvées incluent la canonicalisation, la validation stricte du schéma, le rejet basé sur des politiques ou le marquage explicite. |   2    | D/V  |

---

## C2.3 Validation du schéma, du type et de la longueur

Les attaques d'IA impliquant des entrées malformées ou surdimensionnées peuvent provoquer des erreurs d'analyse, des débordements d'invite entre les champs et une surcharge des ressources. L'application stricte des schémas est également une condition préalable lors de l'exécution d'appels d'outils déterministes.

|   #   | Description                                                                                                                                                                                                                  | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.3.1 | Vérifiez que chaque point de terminaison d'appel d'API ou de fonction définit un schéma d'entrée explicite (JSON Schema, Protobuf ou équivalent multimodal) et que les entrées sont validées avant l'assemblage de l'invite. |   1    |  D   |
| 2.3.2 | Vérifiez que les entrées dépassant les limites maximales de jetons ou d'octets sont rejetées avec une erreur sûre et jamais tronquées silencieusement.                                                                       |   1    | D/V  |
| 2.3.3 | Vérifiez que les vérifications de type (par exemple, les plages numériques, les valeurs d’énumération, les types MIME pour les images/audio) sont appliquées côté serveur.                                                   |   2    | D/V  |
| 2.3.4 | Vérifiez que les validateurs sémantiques (par exemple, JSON Schema) s'exécutent en temps constant afin de prévenir les attaques par déni de service algorithmique (DoS).                                                     |   2    |  D   |
| 2.3.5 | Vérifiez que les échecs de validation sont enregistrés avec des extraits de charge utile masqués et des codes d'erreur non ambigus pour faciliter le triage de la sécurité.                                                  |   3    |  V   |

---

## C2.4 Filtrage du Contenu et des Politiques

Les développeurs devraient être en mesure de détecter les invites syntaxiquement valides qui demandent un contenu interdit (tel que des instructions illicites, des discours haineux et/ou du texte soumis à des droits d'auteur), puis de les empêcher de se propager.

|   #   | Description                                                                                                                                                                                                   | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.4.1 | Vérifiez qu'un classificateur de contenu (zero shot ou affiné) évalue chaque entrée pour la violence, l'automutilation, la haine, le contenu sexuel et les demandes illégales, avec des seuils configurables. |   1    |  D   |
| 2.4.2 | Vérifiez que les entrées qui violent les politiques recevront des refus standardisés ou des complétions sûres afin qu'elles ne soient pas propagées aux appels de LLM en aval.                                |   1    | D/V  |
| 2.4.3 | Vérifiez que le filtrage respecte les politiques spécifiques à l'utilisateur (âge, contraintes légales régionales) via des règles basées sur les attributs résolues au moment de la requête.                  |   2    |  D   |
| 2.4.4 | Vérifiez que les journaux de sélection incluent les scores de confiance du classificateur et les étiquettes de catégorie de politique pour la corrélation SOC et la relecture future de l’équipe rouge.       |   3    |  V   |

---

## C2.5 Limitation du débit d'entrée et prévention des abus

Les développeurs doivent prévenir les abus, l'épuisement des ressources et les attaques automatisées contre les systèmes d'IA en limitant les taux d'entrée et en détectant les schémas d'utilisation anormaux.

|   #   | Description                                                                                                                                                      | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.5.1 | Vérifiez que les limites de débit par utilisateur, par adresse IP et par clé API sont appliquées pour tous les points de terminaison d'entrée.                   |   1    | D/V  |
| 2.5.2 | Vérifiez que les limites de débit en rafale et soutenues sont ajustées pour prévenir les attaques par déni de service (DoS) et les attaques par force brute.     |   2    | D/V  |
| 2.5.3 | Vérifiez que les schémas d'utilisation anormaux (par exemple, les requêtes en rafale, le flood d'entrée) déclenchent des blocages ou des escalades automatiques. |   2    | D/V  |
| 2.5.4 | Vérifier que les journaux de prévention des abus sont conservés et examinés pour détecter les schémas d'attaque émergents.                                       |   3    |  V   |

---

## C2.6 Validation d'entrée multimodale

Les systèmes d'IA doivent inclure une validation robuste pour les entrées non textuelles (images, audio, fichiers) afin de prévenir les injections, les contournements ou les abus de ressources.

|   #   | Description                                                                                                                                                                                                                                                                                                     | Niveau | Rôle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.6.1 | Vérifiez que toutes les entrées non textuelles (images, audio, fichiers) sont validées pour leur type, taille et format avant traitement.                                                                                                                                                                       |   1    |  D   |
| 2.6.2 | Vérifiez que les fichiers sont analysés pour détecter les logiciels malveillants et les charges utiles stéganographiques avant l'ingestion.                                                                                                                                                                     |   2    | D/V  |
| 2.6.3 | Vérifiez que les entrées image/audio sont contrôlées pour détecter les perturbations adversariales ou les schémas d'attaque connus.                                                                                                                                                                             |   2    | D/V  |
| 2.6.4 | Vérifiez que les échecs de validation des entrées multi-modales sont enregistrés et déclenchent des alertes pour enquête.                                                                                                                                                                                       |   3    |  V   |
| 2.6.5 | Vérifiez que la détection des attaques cross-modales identifie les attaques coordonnées couvrant plusieurs types d’entrée (par exemple, des charges utiles stéganographiques dans des images combinées à une injection de prompt dans du texte) grâce à des règles de corrélation et à la génération d’alertes. |   2    | D/V  |
| 2.6.6 | Vérifiez que les échecs de validation multimodale déclenchent une journalisation détaillée incluant toutes les modalités d'entrée, les résultats de validation et les scores de menace.                                                                                                                         |   3    | D/V  |
---

## C2.7 Détection adaptative des menaces en temps réel

Les développeurs devraient utiliser des systèmes avancés de détection des menaces pour l'IA qui s'adaptent aux nouveaux modèles d'attaque et offrent une protection en temps réel grâce à la correspondance de modèles compilés.

|   #   | Description                                                                                                                                                                        | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.7.1 | Vérifiez que la correspondance de motifs (par exemple, expressions régulières compilées) s'exécute sur toutes les entrées avec un impact minimal sur la latence.                   |   1    | D/V  |
| 2.8.3 | Vérifiez que les modèles de détection adaptatifs ajustent la sensibilité en fonction de l'activité récente des attaques et sont mis à jour avec de nouveaux schémas en temps réel. |   2    | D/V  |
| 2.8.4 | Vérifiez que la précision de détection est améliorée par une analyse contextuelle de l'historique utilisateur, de la source et du comportement de session.                         |   3    | D/V  |
| 2.8.5 | Vérifiez que les métriques de performance de détection (taux de détection, taux de fausses alertes, latence de traitement) sont continuellement surveillées et optimisées.         |   3    | D/V  |

---

## Références

* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

