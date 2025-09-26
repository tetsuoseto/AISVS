# Annexe A : Glossaire

>Ce glossaire complet fournit des définitions des termes clés en IA, ML et sécurité utilisés tout au long de l'AISVS afin d'assurer la clarté et une compréhension commune.

* Exemple d’attaque antagoniste : une entrée délibérément conçue pour amener un modèle d’IA à faire une erreur, souvent en ajoutant des perturbations subtiles imperceptibles pour les humains.
  ​
* Robustesse adversaire – La robustesse adversaire en IA fait référence à la capacité d'un modèle à maintenir sa performance et à résister à être trompé ou manipulé par des entrées malveillantes intentionnellement conçues pour provoquer des erreurs.
  ​
* Agent – Les agents IA sont des systèmes logiciels qui utilisent l'IA pour poursuivre des objectifs et accomplir des tâches au nom des utilisateurs. Ils démontrent des capacités de raisonnement, de planification et de mémoire, et possèdent un certain niveau d'autonomie pour prendre des décisions, apprendre et s'adapter.
  ​
* IA agentive : systèmes d’IA capables de fonctionner avec un certain degré d’autonomie pour atteindre des objectifs, prenant souvent des décisions et exécutant des actions sans intervention humaine directe.
  ​
* Contrôle d'accès basé sur les attributs (ABAC) : un paradigme de contrôle d'accès où les décisions d'autorisation sont basées sur les attributs de l'utilisateur, de la ressource, de l'action et de l'environnement, évalués au moment de la requête.
  ​
* Attaque par porte dérobée : un type d'attaque par empoisonnement de données où le modèle est entraîné à répondre d'une manière spécifique à certains déclencheurs tout en se comportant normalement autrement.
  ​
* Biais : erreurs systématiques dans les résultats des modèles d'IA qui peuvent entraîner des résultats injustes ou discriminatoires pour certains groupes ou dans des contextes spécifiques.
  ​
* Exploitation des biais : une technique d'attaque qui tire parti des biais connus dans les modèles d'IA pour manipuler les résultats ou les sorties.
  ​
* Cedar : langage de politique et moteur d'Amazon pour des autorisations granulaires utilisées dans la mise en œuvre de l'ABAC pour les systèmes d'IA.
  ​
* Chaîne de pensée : une technique pour améliorer le raisonnement dans les modèles de langage en générant des étapes intermédiaires de raisonnement avant de produire une réponse finale.
  ​
* Disjoncteurs : Mécanismes qui arrêtent automatiquement les opérations du système d’IA lorsque des seuils de risque spécifiques sont dépassés.
  ​
* Service d'inférence confidentiel : un service d'inférence qui exécute des modèles d'IA à l'intérieur d'un environnement d'exécution sécurisé (TEE) ou d'un mécanisme équivalent de calcul confidentiel, garantissant que les poids du modèle et les données d'inférence restent chiffrés, scellés et protégés contre tout accès ou altération non autorisés.
  ​
* Charge de travail confidentielle : une charge de travail d’IA (par exemple, entraînement, inférence, prétraitement) exécutée à l’intérieur d’un environnement d’exécution sécurisé (TEE) avec isolation matérielle, chiffrement de la mémoire et attestation à distance pour protéger le code, les données et les modèles contre l’accès par l’hôte ou les co-occupants.
  ​
* Fuite de données : exposition non intentionnelle d'informations sensibles à travers les résultats ou le comportement d'un modèle d'IA.
  ​
* Empoisonnement des données : la corruption délibérée des données d'entraînement pour compromettre l'intégrité du modèle, souvent dans le but d'installer des portes dérobées ou de dégrader les performances.
  ​
* Confidentialité différentielle – La confidentialité différentielle est un cadre mathématiquement rigoureux pour la diffusion d'informations statistiques sur des ensembles de données tout en protégeant la vie privée des individus concernés. Elle permet à un détenteur de données de partager des tendances agrégées du groupe tout en limitant les informations divulguées sur des individus spécifiques.
  ​
* Embeddings : Représentations vectorielles denses des données (texte, images, etc.) qui capturent le sens sémantique dans un espace de haute dimension.
  ​
* Explicabilité – L’explicabilité en IA est la capacité d’un système d’IA à fournir des raisons compréhensibles par les humains pour ses décisions et prédictions, offrant ainsi des aperçus sur son fonctionnement interne.
  ​
* IA explicable (XAI) : Systèmes d'IA conçus pour fournir des explications compréhensibles par l'humain concernant leurs décisions et comportements grâce à diverses techniques et cadres.
  ​
* Apprentissage Fédéré : une approche d'apprentissage automatique où les modèles sont entraînés sur plusieurs dispositifs décentralisés détenant des échantillons de données locales, sans échanger les données elles-mêmes.
  ​
* Formulation : La recette ou méthode utilisée pour produire un artefact ou un ensemble de données, tels que les hyperparamètres, la configuration d'entraînement, les étapes de prétraitement ou les scripts de compilation.
  ​
* Garde-fous : Contraintes mises en place pour empêcher les systèmes d'IA de produire des résultats nuisibles, biaisés ou autrement indésirables.
  ​
* Hallucination – Une hallucination d’IA fait référence à un phénomène où un modèle d’IA génère des informations incorrectes ou trompeuses qui ne sont pas basées sur ses données d’entraînement ou sur la réalité factuelle.
  ​
* Humain dans la boucle (HITL) : Systèmes conçus pour nécessiter une supervision, une vérification ou une intervention humaine aux points de décision cruciaux.
  ​
* Infrastructure as Code (IaC) : gestion et provisionnement de l'infrastructure via du code plutôt que par des processus manuels, permettant l'analyse de sécurité et des déploiements cohérents.
  ​
* Jailbreak : Techniques utilisées pour contourner les dispositifs de sécurité dans les systèmes d’IA, en particulier dans les grands modèles de langage, afin de produire du contenu interdit.
  ​
* Moindre privilège : Le principe de sécurité consistant à accorder uniquement les droits d'accès minimaux nécessaires aux utilisateurs et aux processus.
  ​
* LIME (Explications Locales Modèle-agnostique Interprétables) : une technique pour expliquer les prédictions de n'importe quel classificateur d'apprentissage automatique en l'approximation localement avec un modèle interprétable.
  ​
* Attaque par inférence d'appartenance : une attaque visant à déterminer si un point de données spécifique a été utilisé pour entraîner un modèle d'apprentissage automatique.
  ​
* MITRE ATLAS : Paysage des menaces adverses pour les systèmes d'intelligence artificielle ; une base de connaissances des tactiques et techniques adverses contre les systèmes d'IA.
  ​
* Fiche de modèle – Une fiche de modèle est un document qui fournit des informations standardisées sur les performances, les limites, les usages prévus et les considérations éthiques d'un modèle d'IA afin de promouvoir la transparence et le développement responsable de l'IA.
  ​
* Extraction de modèle : une attaque où un adversaire interroge de manière répétée un modèle cible afin de créer une copie fonctionnellement similaire sans autorisation.
  ​
* Inversion de modèle : une attaque qui tente de reconstruire les données d'entraînement en analysant les sorties du modèle.
  ​
* Gestion du cycle de vie du modèle – La gestion du cycle de vie des modèles d’IA est le processus de supervision de toutes les phases de l’existence d’un modèle d’IA, y compris sa conception, son développement, son déploiement, sa surveillance, sa maintenance et son retrait éventuel, afin de garantir qu’il reste efficace et en accord avec les objectifs.
  ​
* Empoisonnement de modèle : introduction de vulnérabilités ou de portes dérobées directement dans un modèle pendant le processus d'entraînement.
  ​
* Vol de modèle : Extraire une copie ou une approximation d'un modèle propriétaire par des requêtes répétées.
  ​
* Système multi-agent : un système composé de plusieurs agents d'IA interagissant, chacun pouvant avoir des capacités et des objectifs différents.
  ​
* OPA (Open Policy Agent) : un moteur de politique open-source qui permet une application unifiée des politiques dans toute la pile.
  ​
* Origine : La généalogie et la chaîne de conservation d'un artefact ou d'un ensemble de données, incluant son origine, les manipulateurs, le chemin de transfert, et les preuves d'intégrité (par exemple, sommes de contrôle, signatures).
  ​
* Apprentissage automatique respectueux de la vie privée (PPML) : Techniques et méthodes pour entraîner et déployer des modèles d’AA tout en protégeant la confidentialité des données d’entraînement.
  ​
* Injection de prompt : une attaque où des instructions malveillantes sont intégrées dans les entrées pour contourner le comportement prévu d'un modèle.
  ​
* RAG (Génération augmentée par récupération) : une technique qui améliore les grands modèles de langage en récupérant des informations pertinentes à partir de sources de connaissances externes avant de générer une réponse.
  ​
* Red-Teaming : La pratique de tester activement les systèmes d'IA en simulant des attaques adverses afin d'identifier les vulnérabilités.
  ​
* Provenance SLSA : Métadonnées définies par le cadre SLSA qui enregistrent où, quand et comment un artefact a été produit (par exemple, dépôt source, hachage de commit, système de construction et paramètres).
  ​
* SBOM (Liste des composants logiciels) : Un enregistrement formel contenant les détails et les relations de la chaîne d'approvisionnement des différents composants utilisés dans la création de logiciels ou de modèles d'IA.
  ​
* SHAP (Explications Additives de Shapley) : Une approche basée sur la théorie des jeux pour expliquer la sortie de n'importe quel modèle d'apprentissage automatique en calculant la contribution de chaque caractéristique à la prédiction.
  ​
* Authentification forte : Authentification qui résiste au vol d’identifiants et à la rejeu en exigeant au moins deux facteurs (connaissance, possession, inhérence) et des mécanismes résistants au phishing tels que FIDO2/WebAuthn, l’authentification de service basée sur un certificat, ou les jetons à courte durée de vie.
  ​
* Attaque sur la chaîne d'approvisionnement : compromettre un système en ciblant les éléments moins sécurisés de sa chaîne d'approvisionnement, tels que les bibliothèques tierces, les ensembles de données ou les modèles pré-entraînés.
  ​
* Apprentissage par transfert : une technique où un modèle développé pour une tâche est réutilisé comme point de départ pour un modèle sur une deuxième tâche.
  ​
* Base de données vectorielle : une base de données spécialisée conçue pour stocker des vecteurs de haute dimension (embeddings) et effectuer des recherches efficaces de similarité.
  ​
* Analyse des vulnérabilités : Outils automatisés qui identifient les vulnérabilités de sécurité connues dans les composants logiciels, y compris les frameworks d'IA et leurs dépendances.
  ​
* Filigrane : Techniques pour intégrer des marqueurs imperceptibles dans le contenu généré par l'IA afin de suivre son origine ou de détecter une génération par IA.
  ​
* Vulnérabilité Zero-Day : une vulnérabilité jusqu’alors inconnue que les attaquants peuvent exploiter avant que les développeurs ne créent et déploient un correctif.

