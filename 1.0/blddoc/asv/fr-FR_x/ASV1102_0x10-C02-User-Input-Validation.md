# C2 Validation des entrées utilisateur

## Objectif de contrôle

Une validation robuste des entrées utilisateur constitue une défense de première ligne contre certaines des attaques les plus dommageables sur les systèmes d'IA. Les attaques d'injection de prompts peuvent contourner les instructions du système, divulguer des données sensibles ou orienter le modèle vers un comportement qui n'est pas autorisé. À moins que des filtres dédiés et des hiérarchies d'instructions soient en place, les recherches montrent que des jailbreaks « multi-shot » qui exploitent des fenêtres de contexte très longues seront efficaces. De plus, des attaques de perturbation adversarielle subtiles — telles que des échanges d'homoglyphes ou leetspeak — peuvent silencieusement modifier les décisions d'un modèle.

---

## C2.1 Défense contre l'injection de prompt

L'injection de prompt est l'un des principaux risques pour les systèmes d'IA. Les défenses contre cette tactique utilisent une combinaison de filtres de motifs statiques, de classificateurs dynamiques et de l'application de la hiérarchie des instructions.

|   #   | description                                                                                                                                                                                                                                                         | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.1.1 | Vérifiez que les entrées des utilisateurs sont filtrées par rapport à une bibliothèque mise à jour en continu de motifs d'injection de prompts connus (mots-clés de jailbreak, "ignorer le précédent", chaînes de jeu de rôle, attaques HTML/URL indirectes).       |   1    | D/V  |
| 2.1.2 | Vérifiez que le système fait respecter une hiérarchie des instructions selon laquelle les messages système ou développeur prévalent sur les instructions de l'utilisateur, même après l'extension de la fenêtre de contexte.                                        |   1    | D/V  |
| 2.1.3 | Vérifiez que les tests d'évaluation adversariaux (par exemple, les prompts de l'équipe rouge "many-shot") sont exécutés avant chaque version d'un modèle ou d'un gabarit de prompt, avec des seuils de réussite et des bloqueurs automatiques pour les régressions. |   2    | D/V  |
| 2.1.4 | Vérifiez que les requêtes provenant de contenus tiers (pages Web, PDFs, e-mails) sont nettoyées dans un contexte d’analyse isolé avant d’être concaténées dans la requête principale.                                                                               |   2    |  D   |
| 2.1.5 | Vérifiez que toutes les mises à jour des règles de filtrage des prompts, les versions des modèles de classificateur et les modifications de la liste de blocage sont sous contrôle de versions et vérifiables.                                                      |   3    | D/V  |

---

## C2.2 Résistance aux exemples adversaires

Les modèles de Traitement Automatique du Langage Naturel (TALN) restent vulnérables à des perturbations subtiles au niveau des caractères ou des mots, que les humains manquent souvent mais que les modèles ont tendance à mal classer.

|   #   | description                                                                                                                                                                                                                                          | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.2.1 | Vérifiez que les étapes de normalisation d'entrée de base (Unicode NFC, correspondance d'homoglyphes, élimination des espaces) s'exécutent avant la tokenisation.                                                                                    |   1    |  D   |
| 2.2.2 | Vérifiez que la détection d'anomalies statistiques signale les entrées présentant une distance d'édition anormalement élevée par rapport aux normes de la langue, un nombre excessif de jetons répétés ou des distances d'embeddings anormales.      |   2    | D/V  |
| 2.2.3 | Vérifier que le pipeline d'inférence prend en charge des variantes de modèle adversarial-training–hardened optionnelles ou des couches de défense (par exemple, randomisation, distillation défensive) pour les points de terminaison à haut risque. |   2    |  D   |
| 2.2.4 | Vérifiez que les entrées susceptibles d'être adverses sont mises en quarantaine et consignées avec les charges utiles complètes (après la redaction des données à caractère personnel).                                                              |   2    |  V   |
| 2.2.5 | Vérifiez que les métriques de robustesse (taux de réussite des suites d’attaques connues) sont suivies au fil du temps et que les régressions déclenchent un blocage de mise en production.                                                          |   3    | D/V  |

---

## C2.3 Validation du schéma, du type et de la longueur

Des attaques d’IA présentant des entrées malformées ou surdimensionnées peuvent provoquer des erreurs d’analyse, un débordement du prompt entre les champs et un épuisement des ressources. L’application stricte du schéma est également une condition préalable lors de l’exécution d’appels d’outils déterministes.

|   #   | description                                                                                                                                                                                                                           | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.3.1 | Vérifiez que chaque point de terminaison API ou appel de fonction définit un schéma d'entrée explicite (schéma JSON, Protobuf ou équivalent multimodal) et que les entrées sont validées avant l'assemblage du prompt.                |   1    |  D   |
| 2.3.2 | Vérifiez que les entrées dépassant les limites maximales de jetons ou d'octets sont rejetées avec une erreur sûre et ne sont jamais tronquées silencieusement.                                                                        |   1    | D/V  |
| 2.3.3 | Vérifiez que les vérifications de type (par exemple, les plages numériques, les valeurs d'énumération, les types MIME pour les images et les fichiers audio) sont appliquées côté serveur, et pas seulement dans le code côté client. |   2    | D/V  |
| 2.3.4 | Vérifiez que les validateurs sémantiques (par exemple JSON Schema) s'exécutent en temps constant afin d'éviter le déni de service algorithmique.                                                                                      |   2    |  D   |
| 2.3.5 | Vérifiez que les échecs de validation sont enregistrés avec des extraits de charge utile masqués et des codes d'erreur non ambigus pour faciliter le triage de sécurité.                                                              |   3    |  V   |

---

## C2.4 Vérification du contenu et des politiques

Les développeurs devraient être capables de détecter des invites syntaxiquement valides qui demandent un contenu interdit (tels que des instructions illicites, des discours de haine et des textes protégés par le droit d'auteur), puis empêcher leur propagation.

|   #   | description                                                                                                                                                                                                         | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.4.1 | Vérifiez qu'un classificateur de contenu (zero-shot ou fine-tuned) évalue chaque entrée pour la violence, l'automutilation, la haine, le contenu sexuel et les demandes illégales, avec des seuils configurables.   |   1    |  D   |
| 2.4.2 | Vérifiez que les entrées qui violent les politiques reçoivent des refus standardisés ou des sorties sûres afin qu'elles ne se propagent pas vers les appels LLM en aval.                                            |   1    | D/V  |
| 2.4.3 | Vérifiez que le modèle de filtrage ou l’ensemble de règles est réentraîné/mis à jour au moins tous les trimestres, en intégrant les motifs de jailbreak ou de contournement des politiques nouvellement observés.   |   2    |  D   |
| 2.4.4 | Vérifiez que le filtrage respecte les politiques propres à l'utilisateur (âge, contraintes légales régionales) via des règles basées sur les attributs déterminées au moment de la demande.                         |   2    |  D   |
| 2.4.5 | Vérifier que les journaux de filtrage comprennent les scores de confiance du classificateur et les étiquettes de catégorie de politique, pour la corrélation avec le SOC et le rejouement futur par l'équipe rouge. |   3    |  V   |

---

## C2.5 Limitation du débit d'entrée et prévention des abus

Les développeurs devraient prévenir les abus, l'épuisement des ressources et les attaques automatisées contre les systèmes d'IA en limitant les débits d'entrée et en détectant les schémas d'utilisation anormaux.

|   #   | description                                                                                                                                                                          | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 2.5.1 | Vérifiez que les limites de taux par utilisateur, par adresse IP et par clé API sont appliquées à tous les points d'entrée.                                                          |   1    | D/V  |
| 2.5.2 | Vérifiez que les limites de débit en rafale et de débit soutenu sont réglées pour prévenir les attaques par déni de service (DoS) et par force brute.                                |   2    | D/V  |
| 2.5.3 | Vérifiez que les comportements d'utilisation anormaux (par exemple des requêtes en rafale, une inondation d'entrées) déclenchent des blocages automatisés ou des mesures d'escalade. |   2    | D/V  |
| 2.5.4 | Vérifier que les journaux de prévention des abus sont conservés et examinés pour détecter les motifs d'attaque émergents.                                                            |   3    |  V   |

---

## C2.6 Validation d’entrée Multi-Modal

Les systèmes d'IA doivent inclure une validation robuste des entrées non textuelles (images, audio, fichiers) afin de prévenir l'injection, l'évasion ou l'abus de ressources.

|   #   | description                                                                                                                                       | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.6.1 | Vérifiez que toutes les entrées non textuelles (images, audio et fichiers) sont validées par le type, la taille et le format avant le traitement. |   1    |  D   |
| 2.6.2 | Vérifiez que les fichiers sont scannés à la recherche de logiciels malveillants et de charges utiles steganographiques avant l’ingestion.         |   2    | D/V  |
| 2.6.3 | Vérifiez que les entrées d'image et d'audio sont vérifiées pour des perturbations adversariales ou des motifs d'attaque connus.                   |   2    | D/V  |
| 2.6.4 | Vérifiez que les échecs de validation des entrées multimodales sont consignés et déclenchent des alertes pour enquête.                            |   3    |  V   |

---

## C2.7 Provenance des entrées et attribution

Les systèmes d'IA devraient permettre l'audit, le suivi des abus et la conformité en surveillant et en étiquetant les origines de toutes les entrées des utilisateurs.

|   #   | description                                                                                                                                                      | Niveau | Rôle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.7.1 | Vérifiez que toutes les entrées des utilisateurs sont associées à des métadonnées (ID utilisateur, session, source, horodatage, adresse IP) lors de l’ingestion. |   1    | D/V  |
| 2.7.2 | Vérifier que les métadonnées de provenance sont conservées et auditées pour toutes les entrées traitées.                                                         |   2    | D/V  |
| 2.7.3 | Vérifiez que les sources d’entrée anormales ou non fiables sont signalées et soumises à une surveillance renforcée ou à un blocage.                              |   2    | D/V  |

---

## C2.8 Détection des menaces adaptatives en temps réel

Les développeurs devraient utiliser des systèmes avancés de détection des menaces pour l'IA qui s'adaptent à de nouveaux motifs d'attaque et offrent une protection en temps réel grâce à une correspondance de motifs compilée.

|   #   | description                                                                                                                                                                                                                          | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :--: |
| 2.8.1 | Vérifiez que les motifs de détection des menaces sont compilés dans des moteurs d'expressions régulières optimisés pour un filtrage en temps réel à haute performance avec un impact de latence minimal.                             |   1    | D/V  |
| 2.8.2 | Vérifiez que les systèmes de détection des menaces maintiennent des bibliothèques de motifs distinctes pour différentes catégories de menaces (injection de prompt, contenu nuisible, données sensibles, commandes système).         |   1    | D/V  |
| 2.8.3 | Vérifiez que la détection adaptative des menaces intègre des modèles d'apprentissage automatique qui ajustent la sensibilité aux menaces en fonction de la fréquence des attaques et des taux de réussite.                           |   2    | D/V  |
| 2.8.4 | Vérifiez que les flux d'intelligence sur les menaces en temps réel mettent automatiquement à jour les bibliothèques de signatures avec les nouvelles signatures d'attaque et les IOCs (Indicateurs de compromission).                |   2    | D/V  |
| 2.8.5 | Vérifier que les taux de faux positifs de la détection des menaces sont surveillés en continu et que la spécificité des motifs est ajustée automatiquement afin de minimiser les interférences avec les cas d'utilisation légitimes. |   3    | D/V  |
| 2.8.6 | Vérifiez que l’analyse contextuelle des menaces prend en compte la source d’entrée, les modèles de comportement des utilisateurs et l’historique des sessions afin d’améliorer la précision de la détection.                         |   3    | D/V  |
| 2.8.7 | Vérifiez que les métriques de performance de la détection des menaces (taux de détection, latence de traitement, utilisation des ressources) sont surveillées et optimisées en temps réel.                                           |   3    | D/V  |

---

## C2.9 Multi-Modal pipeline de validation de sécurité

Les développeurs devraient fournir une validation de sécurité pour le texte, les images, l'audio et d'autres modalités d'entrée de l'IA, avec des types spécifiques de détection des menaces et d'isolation des ressources.

|   #   | description                                                                                                                                                                                                                                                                                       | Niveau | Rôle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :--: |
| 2.9.1 | Vérifiez que chaque modalité d'entrée dispose de validateurs de sécurité dédiés avec des motifs de menace documentés (texte : injection de prompt, images : stéganographie, audio : attaques par spectrogrammes) et des seuils de détection.                                                      |   1    | D/V  |
| 2.9.2 | Vérifier que les entrées multimodales sont traitées dans des environnements isolés (bac à sable) avec des limites de ressources définies (mémoire, CPU, temps de traitement) spécifiques à chaque type de modalité et documentées dans les politiques de sécurité.                                |   2    | D/V  |
| 2.9.3 | Vérifiez que la détection d’attaques inter-modales identifie des attaques coordonnées couvrant plusieurs types d’entrée (par exemple, des charges steganographiques dans les images combinées à une injection de prompt dans le texte) avec des règles de corrélation et la génération d’alertes. |   2    | D/V  |
| 2.9.4 | Vérifiez que les défaillances de validation multimodale déclenchent une journalisation détaillée incluant toutes les modalités d'entrée, les résultats de la validation, les scores de menace et l'analyse de corrélation avec des formats de journalisation structurés pour l'intégration SIEM.  |   3    | D/V  |
| 2.9.5 | Vérifiez que les classificateurs de contenu spécifiques à chaque modalité sont mis à jour selon des plannings documentés (au moins trimestriels) avec de nouveaux motifs de menace, des exemples adversariaux et des benchmarks de performance maintenus au-dessus des seuils de référence.       |   3    | D/V  |

---

## Références

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

