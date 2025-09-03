# Annexe A: Glossaire

>This glossaire exhaustif fournit les définitions des principaux termes d'IA, d'apprentissage automatique et de sécurité utilisés dans tout l'AISVS pour assurer la clarté et une compréhension commune.

* Exemple adversarial : Une entrée délibérément conçue pour amener un modèle d'IA à commettre une erreur, souvent en ajoutant des perturbations subtiles imperceptibles pour les humains.
  ​
* Robustesse adversarielle – La robustesse adversarielle en IA fait référence à la capacité d'un modèle à maintenir ses performances et à résister à être trompé ou manipulé par des entrées intentionnellement conçues et malveillantes destinées à provoquer des erreurs.
  ​
* Agent – Les agents d'IA sont des systèmes logiciels qui utilisent l'IA pour poursuivre des objectifs et accomplir des tâches au nom des utilisateurs. Ils font preuve de raisonnement, de planification et de mémoire, et disposent d'un niveau d'autonomie pour prendre des décisions, apprendre et s'adapter.
  ​
* IA agentive : des systèmes d'IA capables d'opérer avec un certain degré d'autonomie pour atteindre des objectifs, prenant souvent des décisions et effectuant des actions sans intervention humaine directe.
  ​
* Contrôle d'accès basé sur les attributs (ABAC) : Un paradigme de contrôle d'accès dans lequel les décisions d'autorisation sont basées sur les attributs de l'utilisateur, de la ressource, de l'action et de l'environnement, évalués au moment de la requête.
  ​
* Attaque par porte dérobée : un type d'attaque par empoisonnement des données dans laquelle le modèle est entraîné à répondre d'une manière spécifique à certains déclencheurs tout en se comportant normalement dans les autres cas.
  ​
* Biais : erreurs systématiques dans les sorties des modèles d'IA qui peuvent entraîner des résultats injustes ou discriminatoires pour certains groupes ou dans des contextes spécifiques.
  ​
* Exploitation des biais : une technique d’attaque qui exploite les biais connus dans les modèles d’IA pour manipuler les sorties ou les résultats.
  ​
* Cedar: le langage de politique et le moteur d'Amazon pour les autorisations granulaires utilisées dans la mise en œuvre de l'ABAC pour les systèmes d'IA.
  ​
* Chaîne de raisonnement : une technique visant à améliorer le raisonnement des modèles de langage en générant des étapes de raisonnement intermédiaires avant de produire une réponse finale.
  ​
* Disjoncteurs : des mécanismes qui arrêtent automatiquement les opérations des systèmes d'IA lorsque des seuils de risque spécifiques sont dépassés.
  ​
* Fuite de données : exposition involontaire d'informations sensibles par les sorties ou le comportement du modèle d'IA.
  ​
* Empoisonnement des données : la corruption délibérée des données d'entraînement visant à compromettre l'intégrité du modèle, souvent pour installer des portes dérobées ou dégrader les performances.
  ​
* Confidentialité différentielle – La confidentialité différentielle est un cadre mathématiquement rigoureux pour publier des informations statistiques sur des ensembles de données tout en protégeant la vie privée des personnes concernées. Elle permet à un détenteur de données de partager des tendances agrégées du groupe tout en limitant les informations qui pourraient être divulguées au sujet de personnes spécifiques.
  ​
* Embeddings: Représentations vectorielles denses de données (texte, images, etc.) qui capturent la signification sémantique dans un espace de haute dimension.
  ​
* Explicabilité – L'explicabilité dans l'IA est la capacité d'un système d'IA à fournir des raisons compréhensibles par l'être humain pour ses décisions et ses prédictions, offrant des aperçus sur son fonctionnement interne.
  ​
* IA explicable (XAI): des systèmes d'IA conçus pour fournir des explications compréhensibles par l'homme de leurs décisions et de leurs comportements à travers diverses techniques et cadres.
  ​
* Apprentissage fédéré : une approche d'apprentissage automatique où les modèles sont entraînés sur plusieurs dispositifs décentralisés détenant des échantillons locaux de données, sans échanger les données elles-mêmes.
  ​
* Garde-fous : Contraintes mises en œuvre pour empêcher les systèmes d'IA de produire des sorties nocives, biaisées ou autrement indésirables.
  ​
* Hallucination – Une hallucination d'IA désigne un phénomène par lequel un modèle d'IA génère des informations incorrectes ou trompeuses qui ne sont pas basées sur ses données d'entraînement ou sur la réalité factuelle.
  ​
* Human-in-the-Loop (HITL) : des systèmes conçus pour exiger une supervision humaine, une vérification ou une intervention aux points de décision cruciaux.
  ​
* Infrastructure as Code (IaC) : gestion et provisionnement de l'infrastructure par le code, plutôt que par des processus manuels, permettant l’analyse de sécurité et des déploiements cohérents.
  ​
* Jailbreak: Techniques utilisées pour contourner les garde-fous de sécurité dans les systèmes d’IA, en particulier dans les grands modèles de langage, afin de produire un contenu interdit.
  ​
* Le principe du moindre privilège : le principe de sécurité consistant à n'accorder que les droits d'accès minimaux nécessaires aux utilisateurs et aux processus.
  ​
* LIME (Local Interpretable Model-agnostic Explanations): Une technique pour expliquer les prédictions de tout classificateur d'apprentissage automatique en l'approximation locale avec un modèle interprétable.
  ​
* Attaque d'inférence d'appartenance : une attaque visant à déterminer si un échantillon de données spécifique a été utilisé pour entraîner un modèle d'apprentissage automatique.
  ​
* MITRE ATLAS: Paysage des menaces adverses pour les systèmes d'intelligence artificielle; une base de connaissances sur les tactiques et techniques adverses contre les systèmes d'IA.
  ​
* Fiche du modèle – Une fiche du modèle est un document qui fournit des informations standardisées sur les performances d'un modèle d'IA, ses limites, ses usages prévus et les considérations éthiques afin de promouvoir la transparence et le développement responsable de l'IA.
  ​
* Extraction de modèle : une attaque au cours de laquelle un adversaire interroge à répétition un modèle cible afin de créer une copie fonctionnellement similaire sans autorisation.
  ​
* Inversion de modèle: une attaque qui tente de reconstruire les données d'entraînement en analysant les sorties du modèle.
  ​
* Gestion du cycle de vie des modèles – La gestion du cycle de vie des modèles d’IA est le processus de supervision de toutes les étapes de l’existence d’un modèle d’IA, y compris sa conception, son développement, son déploiement, sa surveillance, sa maintenance et sa retraite éventuelle, afin de garantir qu’il demeure efficace et aligné sur les objectifs.
  ​
* Empoisonnement du modèle : introduction de vulnérabilités ou de portes dérobées directement dans un modèle pendant le processus d'entraînement.
  ​
* Vol de modèle : Extraction d'une copie ou d'une approximation d'un modèle propriétaire par des requêtes répétées.
  ​
* Système multi-agent: Un système composé de multiples agents d'IA interagissants, chacun ayant des capacités et des objectifs potentiellement différents.
  ​
* OPA (Open Policy Agent): un moteur de politiques open-source qui permet une application unifiée des politiques à travers la pile.
  ​
* Apprentissage automatique préservant la vie privée (PPML) : Techniques et méthodes pour former et déployer des modèles ML tout en protégeant la vie privée des données d'entraînement.
  ​
* Injection de prompt : une attaque dans laquelle des instructions malveillantes sont intégrées dans des entrées afin de contourner le comportement prévu du modèle.
  ​
* RAG (Retrieval-Augmented Generation): Une technique qui améliore les grands modèles de langage en récupérant des informations pertinentes à partir de sources de connaissances externes avant de générer une réponse.
  ​
* Red-Teaming: La pratique consistant à tester activement des systèmes d'IA en simulant des attaques adversariales afin d'identifier les vulnérabilités.
  ​
* SBOM (Liste des composants logiciels) : Un enregistrement formel contenant les détails et les relations de chaîne d'approvisionnement de divers composants utilisés dans la construction de logiciels ou de modèles d'IA.
  ​
* SHAP (SHapley Additive exPlanations) : une approche basée sur la théorie des jeux pour expliquer la sortie de tout modèle d'apprentissage automatique en calculant la contribution de chaque caractéristique à la prédiction.
  ​
* Attaque de la chaîne d'approvisionnement : compromettre un système en ciblant des éléments moins sécurisés de sa chaîne d'approvisionnement, tels que des bibliothèques tierces, des ensembles de données ou des modèles pré-entraînés.
  ​
* Apprentissage par transfert : une technique où un modèle développé pour une tâche est réutilisé comme point de départ pour un modèle sur une seconde tâche.
  ​
* Base de données vectorielle : une base de données spécialisée conçue pour stocker des vecteurs de haute dimension (embeddings) et effectuer des recherches de similarité efficaces.
  ​
* Analyse de vulnérabilités : outils automatisés qui identifient des vulnérabilités de sécurité connues dans les composants logiciels, y compris les frameworks d’IA et les dépendances.
  ​
* Filigrage numérique : techniques pour insérer des marqueurs imperceptibles dans le contenu généré par l’IA afin de retracer son origine ou de détecter une génération par IA.
  ​
* Vulnérabilité zero-day : une vulnérabilité auparavant inconnue que les attaquants peuvent exploiter avant que les développeurs ne créent et déploient un correctif.

