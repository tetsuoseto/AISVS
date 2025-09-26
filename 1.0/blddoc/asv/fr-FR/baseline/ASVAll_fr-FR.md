## Frontispice

### À propos de la norme

La norme de vérification de la sécurité de l’intelligence artificielle (AISVS) est un catalogue communautaire des exigences de sécurité que les data scientists, ingénieurs MLOps, architectes logiciels, développeurs, testeurs, professionnels de la sécurité, fournisseurs d’outils, régulateurs et consommateurs peuvent utiliser pour concevoir, construire, tester et vérifier des systèmes et applications d’IA fiables. Elle fournit un langage commun pour spécifier les contrôles de sécurité tout au long du cycle de vie de l’IA — depuis la collecte des données et le développement des modèles jusqu’au déploiement et à la surveillance continue — afin que les organisations puissent mesurer et améliorer la résilience, la confidentialité et la sécurité de leurs solutions d’IA.

### Droits d'auteur et licence

Version 0.1 (Premier brouillon public - Travail en cours), 2025  

![license](images/license.png)
Droits d'auteur © 2025 Le projet AISVS.  

Publié sous laCreative Commons Attribution‑ShareAlike 4.0 International License.
Pour toute réutilisation ou distribution, vous devez clairement communiquer les conditions de licence de ce travail aux autres.

### Chefs de projet

Jim Manico
Aras “Russ” Memisyazici

### Contributeurs et réviseurs

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS est une toute nouvelle norme créée spécifiquement pour répondre aux défis uniques de sécurité des systèmes d’intelligence artificielle. Bien qu’elle s’inspire des meilleures pratiques de sécurité plus générales, chaque exigence de l’AISVS a été développée de zéro pour refléter le paysage des menaces liées à l’IA et aider les organisations à construire des solutions d’IA plus sûres et plus résilientes.

## Préface

Bienvenue dans la norme de vérification de la sécurité de l'intelligence artificielle (AISVS) version 1.0 !

### Introduction

Établi en 2025 grâce à un effort communautaire collaboratif, AISVS définit les exigences de sécurité à prendre en compte lors de la conception, du développement, du déploiement et de l'exploitation des modèles d'IA modernes, des pipelines et des services activés par l'IA.

AISVS v1.0 représente le travail combiné de ses responsables de projet, de son groupe de travail et de ses contributeurs de la communauté élargie pour produire une base pragmatique et testable pour la sécurisation des systèmes d'IA.

Notre objectif avec cette version est de rendre l'adoption de l'AISVS simple tout en restant strictement concentré sur son périmètre défini et en répondant au paysage des risques en rapide évolution propre à l'IA.

### Objectifs clés pour AISVS Version 1.0

La version 1.0 sera créée avec plusieurs principes directeurs.

#### Portée bien définie

Chaque exigence doit être alignée avec le nom et la mission d’AISVS :

Intelligence artificielle – Les contrôles fonctionnent au niveau de la couche IA/ML (données, modèle, pipeline ou inférence) et sont sous la responsabilité des praticiens de l'IA.
Sécurité – Les exigences atténuent directement les risques identifiés en matière de sécurité, de confidentialité ou de sûreté.
Vérification – Le langage est rédigé de manière à ce que la conformité puisse être validée objectivement.
Norme – Les sections suivent une structure et une terminologie cohérentes pour former une référence homogène.
​
---

En suivant AISVS, les organisations peuvent évaluer systématiquement et renforcer la posture de sécurité de leurs solutions d’IA, favorisant ainsi une culture d’ingénierie de l’IA sécurisée.

## Utilisation de l'AISVS

La norme de vérification de la sécurité de l'intelligence artificielle (AISVS) définit les exigences de sécurité pour les applications et services d'IA modernes, en se concentrant sur les aspects sous le contrôle des développeurs d'applications.

L'AISVS est destiné à toute personne développant ou évaluant la sécurité des applications d'IA, y compris les développeurs, architectes, ingénieurs en sécurité et auditeurs. Ce chapitre présente la structure et l'utilisation de l'AISVS, y compris ses niveaux de vérification et ses cas d'utilisation prévus.

### Niveaux de vérification de la sécurité de l'intelligence artificielle

L'AISVS définit trois niveaux ascendantes de vérification de la sécurité. Chaque niveau ajoute de la profondeur et de la complexité, permettant aux organisations d'adapter leur posture de sécurité au niveau de risque de leurs systèmes d'IA.

Les organisations peuvent commencer au Niveau 1 et adopter progressivement des niveaux supérieurs à mesure que la maturité en matière de sécurité et l'exposition aux menaces augmentent.

#### Définition des niveaux

Chaque exigence dans AISVS v1.0 est attribuée à l'un des niveaux suivants :

 Exigences de niveau 1

Le niveau 1 comprend les exigences de sécurité les plus critiques et fondamentales. Celles-ci se concentrent sur la prévention des attaques courantes qui ne reposent pas sur d'autres conditions préalables ou vulnérabilités. La plupart des contrôles de niveau 1 sont soit simples à mettre en œuvre, soit suffisamment essentiels pour justifier l'effort.

 Exigences de niveau 2

Le niveau 2 traite des attaques plus avancées ou moins fréquentes, ainsi que des défenses à plusieurs niveaux contre des menaces répandues. Ces exigences peuvent impliquer une logique plus complexe ou cibler des conditions préalables spécifiques aux attaques.

 Exigences de niveau 3

Le niveau 3 inclut des contrôles qui sont généralement plus difficiles à mettre en œuvre ou dont l'applicabilité est situationnelle. Ceux-ci représentent souvent des mécanismes de défense en profondeur ou des mesures d'atténuation contre des attaques de niche, ciblées ou de haute complexité.

#### Rôle (D/V)

Chaque exigence AISVS est marquée en fonction du public principal :

D – Exigences axées sur les développeurs
V – Exigences axées sur le vérificateur/auditeur
D/V – Pertinent à la fois pour les développeurs et les vérificateurs

## Gouvernance des données de formation C1 et gestion des biais

### Objectif de contrôle

Les données d'entraînement doivent être obtenues, manipulées et maintenues de manière à préserver la provenance, la sécurité, la qualité et l'équité. Cela permet de respecter les obligations légales et de réduire les risques de biais, d'empoisonnement ou de violations de la vie privée qui pourraient survenir lors de la formation et affecter l'ensemble du cycle de vie de l'IA.

---

### C1.1 Provenance des données d'entraînement

Maintenez un inventaire vérifiable de tous les ensembles de données, n'acceptez que des sources fiables et consignez chaque modification pour garantir l'auditabilité.

 #1.1.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'un inventaire à jour de chaque source de données d'entraînement (origine, gestionnaire/propriétaire, licence, méthode de collecte, contraintes d'utilisation prévues et historique de traitement) est maintenu.
 #1.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les processus de préparation des données d’entraînement excluent les caractéristiques, attributs ou champs inutiles (par exemple, les métadonnées non utilisées, les informations personnelles sensibles, les données de test divulguées).
 #1.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que toutes les modifications du jeu de données sont soumises à un processus d'approbation consigné.
 #1.1.4    Niveau: 3    Rôle: D/V
 Vérifiez que les ensembles de données ou les sous-ensembles sont marqués par un filigrane ou empreint d'empreintes digitales lorsque cela est possible.

---

### C1.2 Sécurité et intégrité des données d'entraînement

Restreindre l'accès aux données d'entraînement, les chiffrer au repos et en transit, et valider leur intégrité pour prévenir toute falsification, vol ou empoisonnement des données.

 #1.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les contrôles d'accès protègent le stockage des données d'entraînement et les pipelines.
 #1.2.2    Niveau: 2    Rôle: D/V
 Vérifiez que tous les accès aux données d'entraînement sont enregistrés, y compris l'utilisateur, l'heure et l'action.
 #1.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les ensembles de données d'entraînement sont chiffrés lors de leur transfert et au repos, en utilisant des algorithmes cryptographiques et des pratiques de gestion des clés conformes aux normes de l'industrie.
 #1.2.4    Niveau: 2    Rôle: D/V
 Vérifiez que des hachages cryptographiques ou des signatures numériques sont utilisés pour garantir l'intégrité des données lors du stockage et du transfert des données d'entraînement.
 #1.2.5    Niveau: 2    Rôle: D/V
 Vérifiez que des techniques de détection automatisées sont appliquées pour protéger contre les modifications non autorisées ou la corruption des données d'entraînement.
 #1.2.6    Niveau: 2    Rôle: D/V
 Vérifiez que les données d'entraînement obsolètes sont supprimées en toute sécurité ou anonymisées.
 #1.2.7    Niveau: 3    Rôle: D/V
 Vérifiez que toutes les versions des ensembles de données d'entraînement sont identifiées de manière unique, stockées de façon immuable et auditables afin de permettre la restauration et l'analyse médico-légale.

---

### C1.3 Qualité, intégrité et sécurité de l'étiquetage des données d'entraînement

Protéger les étiquettes et exiger une révision technique pour les données critiques.

 #1.3.1    Niveau: 2    Rôle: D/V
 Vérifiez que les hachages cryptographiques ou les signatures numériques sont appliqués aux artefacts d'étiquette afin d'assurer leur intégrité et leur authenticité.
 #1.3.2    Niveau: 2    Rôle: D/V
 Vérifiez que les interfaces et plateformes d'étiquetage appliquent des contrôles d'accès stricts, maintiennent des journaux d'audit infalsifiables de toutes les activités d'étiquetage et protègent contre les modifications non autorisées.
 #1.3.3    Niveau: 3    Rôle: D/V
 Vérifiez que les informations sensibles dans les étiquettes sont supprimées, anonymisées ou cryptées au niveau du champ de données, au repos et en transit.

---

### C1.4 Qualité des données d'entraînement et garantie de sécurité

Combinez la validation automatisée, les contrôles manuels ponctuels et la correction enregistrée pour garantir la fiabilité des ensembles de données.

 #1.4.1    Niveau: 1    Rôle: D
 Vérifiez que les tests automatisés détectent les erreurs de format et les valeurs nulles à chaque ingestion ou transformation de données importante.
 #1.4.2    Niveau: 2    Rôle: D/V
 Vérifiez que les pipelines de formation et de fine-tuning des LLM mettent en œuvre la détection d’empoisonnement et la validation de l’intégrité des données (par exemple, méthodes statistiques, détection des valeurs aberrantes, analyse d'empreintes) afin d’identifier les attaques potentielles d’empoisonnement (par exemple, inversion d’étiquettes, insertion de déclencheurs de porte dérobée, commandes de changement de rôle, attaques par instances influentes) ou la corruption accidentelle des données d’entraînement.
 #1.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que les étiquettes générées automatiquement (par exemple, via des LLM ou une supervision faible) sont soumises à des seuils de confiance et à des contrôles de cohérence pour détecter les étiquettes hallucinées, trompeuses ou à faible confiance.
 #1.4.4    Niveau: 3    Rôle: D/V
 Vérifiez que des défenses appropriées, telles que l'entraînement adversarial (en utilisant des exemples adversariaux générés), l'augmentation de données avec des entrées perturbées, ou des techniques d'optimisation robuste, sont mises en œuvre et ajustées pour les modèles concernés en fonction de l'évaluation des risques.
 #1.4.5    Niveau: 3    Rôle: D
 Vérifiez que les tests automatisés détectent les décalages d'étiquettes à chaque ingestion ou transformation de données significative.

---

### C1.5 Traçabilité et origine des données

Suivez le parcours complet de chaque point de données depuis la source jusqu'à l'entrée du modèle pour assurer la traçabilité et la réponse aux incidents.

 #1.5.1    Niveau: 2    Rôle: D/V
 Vérifiez que la lignée de chaque point de données, y compris toutes les transformations, augmentations et fusions, est enregistrée et peut être reconstruite.
 #1.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les enregistrements de lignée sont immuables, stockés de manière sécurisée et accessibles pour les audits.
 #1.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que le suivi de la lignée couvre les données synthétiques générées via des techniques de préservation de la vie privée ou génératives et que toutes les données synthétiques sont clairement étiquetées et distinguables des données réelles tout au long du pipeline.

---

### Références

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
MITRE ATLAS: Adversary Tactics for AI
Survey of ML Bias Mitigation Techniques – MDPI
Data Provenance & Lineage Best Practices – Nightfall AI
Data Labeling Quality Standards – LabelYourData
Training Data Poisoning Guide – Lakera.ai
CISA Advisory: Securing Data for AI Systems
ISO/IEC 23053: AI Management Systems Framework
IBM: What is AI Governance?
Google AI Principles
GDPR & AI Training Data – DataProtectionReport
Supply-Chain Security for AI Data – AppSOC
OpenAI Privacy Center – Data Deletion Controls
Adversarial ML Dataset – Kaggle

## Validation des entrées utilisateur C2

### Objectif de contrôle

La validation robuste des entrées utilisateur est une ligne de défense primordiale contre certaines des attaques les plus dommageables sur les systèmes d'IA. Les attaques par injection de prompt peuvent ignorer les instructions du système, divulguer des données sensibles ou orienter le modèle vers un comportement non autorisé. À moins que des filtres dédiés et d'autres validations soient en place, les recherches montrent que les jailbreaks exploitant les fenêtres de contexte continueront d'être efficaces.

---

### C2.1 Défense contre l'injection de prompt

L'injection de prompt est l'un des principaux risques pour les systèmes d'IA. Les défenses contre cette tactique utilisent une combinaison de filtres de motifs, de classificateurs de données et de l'application hiérarchique des instructions.

 #2.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que les entrées utilisateur sont contrôlées par rapport à une bibliothèque continuellement mise à jour de modèles connus d'injection de requêtes. Cela inclut les mots-clés de jailbreak, les instructions de type « ignorer le précédent » et les enchaînements de jeux de rôle.
 #2.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que le système applique une hiérarchie des instructions dans laquelle les messages système l'emportent sur les instructions utilisateur, même après le traitement des instructions utilisateur.
 #2.1.4    Niveau: 2    Rôle: D
 Vérifiez que les invites provenant de contenus tiers (pages web, PDF, e-mails) sont nettoyées isolément avant d’être concaténées dans l’invite principale.

---

### C2.2 Résistance aux exemples adverses

Les modèles de traitement du langage naturel (NLP) restent vulnérables aux perturbations subtiles au niveau des caractères ou des mots que les humains manquent souvent mais que les modèles ont tendance à mal classifier.

 #2.2.1    Niveau: 1    Rôle: D
 Vérifiez que les étapes de normalisation de base des entrées (NFC Unicode, mappage des homoglyphes, suppression des espaces superflus) sont effectuées avant la tokenisation.
 #2.2.2    Niveau: 2    Rôle: D/V
 Vérifiez que la détection d'anomalies statistiques signale les entrées avec une distance d'édition exceptionnellement élevée par rapport aux normes linguistiques ou des distances d'incorporation anormales.
 #2.2.3    Niveau: 2    Rôle: D
 Vérifiez que le pipeline d'inférence prend en charge les variantes de modèles renforcés par entraînement adversarial ou les couches de défense (par exemple, la randomisation, la distillation défensive, les contrôles d'alignement) pour les points de terminaison à haut risque.
 #2.2.4    Niveau: 2    Rôle: V
 Vérifiez que les entrées adverses suspectées sont mises en quarantaine et enregistrées avec leurs charges utiles complètes.
 #2.2.5    Niveau: 2    Rôle: D/V
 Vérifiez que le détournement de codage et de représentation dans les entrées et sorties (par exemple, les caractères Unicode/invisibles de contrôle, les substitutions d'homoglyphes ou le texte à direction mixte) est détecté et atténué. Les atténuations approuvées incluent la canonicalisation, la validation stricte du schéma, le rejet basé sur des politiques ou le marquage explicite.

---

### C2.3 Validation du schéma, du type et de la longueur

Les attaques d'IA impliquant des entrées malformées ou surdimensionnées peuvent provoquer des erreurs d'analyse, des débordements d'invite entre les champs et une surcharge des ressources. L'application stricte des schémas est également une condition préalable lors de l'exécution d'appels d'outils déterministes.

 #2.3.1    Niveau: 1    Rôle: D
 Vérifiez que chaque point de terminaison d'appel d'API ou de fonction définit un schéma d'entrée explicite (JSON Schema, Protobuf ou équivalent multimodal) et que les entrées sont validées avant l'assemblage de l'invite.
 #2.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que les entrées dépassant les limites maximales de jetons ou d'octets sont rejetées avec une erreur sûre et jamais tronquées silencieusement.
 #2.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les vérifications de type (par exemple, les plages numériques, les valeurs d’énumération, les types MIME pour les images/audio) sont appliquées côté serveur.
 #2.3.4    Niveau: 2    Rôle: D
 Vérifiez que les validateurs sémantiques (par exemple, JSON Schema) s'exécutent en temps constant afin de prévenir les attaques par déni de service algorithmique (DoS).
 #2.3.5    Niveau: 3    Rôle: V
 Vérifiez que les échecs de validation sont enregistrés avec des extraits de charge utile masqués et des codes d'erreur non ambigus pour faciliter le triage de la sécurité.

---

### C2.4 Filtrage du Contenu et des Politiques

Les développeurs devraient être en mesure de détecter les invites syntaxiquement valides qui demandent un contenu interdit (tel que des instructions illicites, des discours haineux et/ou du texte soumis à des droits d'auteur), puis de les empêcher de se propager.

 #2.4.1    Niveau: 1    Rôle: D
 Vérifiez qu'un classificateur de contenu (zero shot ou affiné) évalue chaque entrée pour la violence, l'automutilation, la haine, le contenu sexuel et les demandes illégales, avec des seuils configurables.
 #2.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les entrées qui violent les politiques recevront des refus standardisés ou des complétions sûres afin qu'elles ne soient pas propagées aux appels de LLM en aval.
 #2.4.3    Niveau: 2    Rôle: D
 Vérifiez que le filtrage respecte les politiques spécifiques à l'utilisateur (âge, contraintes légales régionales) via des règles basées sur les attributs résolues au moment de la requête.
 #2.4.4    Niveau: 3    Rôle: V
 Vérifiez que les journaux de sélection incluent les scores de confiance du classificateur et les étiquettes de catégorie de politique pour la corrélation SOC et la relecture future de l’équipe rouge.

---

### C2.5 Limitation du débit d'entrée et prévention des abus

Les développeurs doivent prévenir les abus, l'épuisement des ressources et les attaques automatisées contre les systèmes d'IA en limitant les taux d'entrée et en détectant les schémas d'utilisation anormaux.

 #2.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les limites de débit par utilisateur, par adresse IP et par clé API sont appliquées pour tous les points de terminaison d'entrée.
 #2.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les limites de débit en rafale et soutenues sont ajustées pour prévenir les attaques par déni de service (DoS) et les attaques par force brute.
 #2.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que les schémas d'utilisation anormaux (par exemple, les requêtes en rafale, le flood d'entrée) déclenchent des blocages ou des escalades automatiques.
 #2.5.4    Niveau: 3    Rôle: V
 Vérifier que les journaux de prévention des abus sont conservés et examinés pour détecter les schémas d'attaque émergents.

---

### C2.6 Validation d'entrée multimodale

Les systèmes d'IA doivent inclure une validation robuste pour les entrées non textuelles (images, audio, fichiers) afin de prévenir les injections, les contournements ou les abus de ressources.

 #2.6.1    Niveau: 1    Rôle: D
 Vérifiez que toutes les entrées non textuelles (images, audio, fichiers) sont validées pour leur type, taille et format avant traitement.
 #2.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que les fichiers sont analysés pour détecter les logiciels malveillants et les charges utiles stéganographiques avant l'ingestion.
 #2.6.3    Niveau: 2    Rôle: D/V
 Vérifiez que les entrées image/audio sont contrôlées pour détecter les perturbations adversariales ou les schémas d'attaque connus.
 #2.6.4    Niveau: 3    Rôle: V
 Vérifiez que les échecs de validation des entrées multi-modales sont enregistrés et déclenchent des alertes pour enquête.
 #2.6.5    Niveau: 2    Rôle: D/V
 Vérifiez que la détection des attaques cross-modales identifie les attaques coordonnées couvrant plusieurs types d’entrée (par exemple, des charges utiles stéganographiques dans des images combinées à une injection de prompt dans du texte) grâce à des règles de corrélation et à la génération d’alertes.
 #2.6.6    Niveau: 3    Rôle: D/V
 Vérifiez que les échecs de validation multimodale déclenchent une journalisation détaillée incluant toutes les modalités d'entrée, les résultats de validation et les scores de menace.
---

### C2.7 Détection adaptative des menaces en temps réel

Les développeurs devraient utiliser des systèmes avancés de détection des menaces pour l'IA qui s'adaptent aux nouveaux modèles d'attaque et offrent une protection en temps réel grâce à la correspondance de modèles compilés.

 #2.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que la correspondance de motifs (par exemple, expressions régulières compilées) s'exécute sur toutes les entrées avec un impact minimal sur la latence.
 #2.8.3    Niveau: 2    Rôle: D/V
 Vérifiez que les modèles de détection adaptatifs ajustent la sensibilité en fonction de l'activité récente des attaques et sont mis à jour avec de nouveaux schémas en temps réel.
 #2.8.4    Niveau: 3    Rôle: D/V
 Vérifiez que la précision de détection est améliorée par une analyse contextuelle de l'historique utilisateur, de la source et du comportement de session.
 #2.8.5    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques de performance de détection (taux de détection, taux de fausses alertes, latence de traitement) sont continuellement surveillées et optimisées.

---

### Références

Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## Gestion du cycle de vie du modèle C3 et contrôle des modifications

### Objectif de contrôle

Les systèmes d'IA doivent mettre en œuvre des processus de contrôle des modifications qui empêchent les modifications non autorisées ou dangereuses du modèle d'atteindre la production. Ce contrôle garantit l'intégrité du modèle tout au long de son cycle de vie--du développement jusqu'au déploiement et à la mise hors service--ce qui permet une réponse rapide aux incidents et maintient la responsabilité de tous les changements.

Objectif de sécurité fondamentale : Seuls les modèles autorisés et validés atteignent la production en utilisant des processus contrôlés qui garantissent l'intégrité, la traçabilité et la capacité de récupération.

---

### C3.1 Autorisation et Intégrité du Modèle

Seuls les modèles autorisés avec une intégrité vérifiée atteignent les environnements de production.

 #3.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les artefacts du modèle (poids, configurations, tokenizeurs) sont signés cryptographiquement par des entités autorisées avant le déploiement.
 #3.1.2    Niveau: 2    Rôle: V
 Vérifiez que le suivi des dépendances maintient un inventaire en temps réel permettant l’identification de tous les systèmes consommateurs.
 #3.1.3    Niveau: 3    Rôle: D/V
 Vérifiez que les enregistrements de provenance du modèle incluent l'identité d'une entité autorisante, les sommes de contrôle des données d'entraînement, les résultats des tests de validation avec le statut réussite/échec, et un horodatage de création.

---

### C3.2 Validation et test du modèle

Les modèles doivent passer les validations de sécurité et de sûreté définies avant le déploiement.

 #3.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les modèles subissent des tests de sécurité automatisés incluant la validation des entrées, la désinfection des sorties, et des évaluations de sécurité avec des seuils d’acceptation/rejet organisationnels préalablement convenus avant le déploiement.
 #3.2.2    Niveau: 1    Rôle: V
 Vérifiez que toutes les modifications du modèle (déploiement, configuration, retrait) génèrent des enregistrements d'audit immuables incluant un horodatage, une identité d'acteur authentifiée, un type de modification, ainsi que les états avant/après.
 #3.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les échecs de validation bloquent automatiquement le déploiement du modèle après une approbation explicite de dérogation provenant de personnel autorisé pré-désigné avec des justifications commerciales documentées.

---

### C3.3 Déploiement Contrôlé & Repli

Les déploiements de modèles doivent être contrôlés, surveillés et réversibles.

 #3.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les processus de déploiement valident les signatures cryptographiques et calculent les sommes de contrôle d'intégrité avant l'activation du modèle, en interrompant le déploiement en cas de divergence.
 #3.3.2    Niveau: 1    Rôle: D
 Vérifiez que les déploiements en production mettent en œuvre des mécanismes de déploiement progressif (déploiements canaris, déploiements blue-green) avec des déclencheurs de retour en arrière automatisés basés sur des taux d'erreur, des seuils de latence ou des critères d'alerte de sécurité préalablement convenus.
 #3.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les capacités de restauration annulent de manière atomique l’état complet du modèle (poids, configurations, dépendances).
 #3.3.4    Niveau: 3    Rôle: D/V
 Vérifiez que les capacités d'arrêt d'urgence du modèle peuvent désactiver les points de terminaison du modèle dans un délai de réponse prédéfini.

---

### C3.4 Pratiques de Développement Sécurisé

Les processus de développement et d'entraînement des modèles doivent suivre des pratiques sécurisées pour prévenir toute compromission.

 #3.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que les environnements de développement, de test et de production du modèle sont séparés physiquement ou logiquement. Ils ne partagent aucune infrastructure, disposent de contrôles d'accès distincts et de bases de données isolées.
 #3.4.2    Niveau: 1    Rôle: D
 Vérifiez que les artefacts de développement du modèle (hyperparamètres, scripts d'entraînement, fichiers de configuration, modèles de requêtes, etc.) sont stockés dans un système de gestion de versions et nécessitent une approbation par revue par les pairs avant d'être utilisés pour l'entraînement.
 #3.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que la formation du modèle et l'ajustement fin se déroulent dans des environnements isolés avec un accès réseau contrôlé.
 #3.4.4    Niveau: 2    Rôle: D
 Vérifiez que les sources de données d'entraînement sont validées par des contrôles d'intégrité et authentifiées via des sources fiables avec une chaîne de custody documentée avant leur utilisation dans le développement du modèle.

---

### Retrait et mise hors service du modèle C3.5

Les modèles doivent être retirés de manière sécurisée lorsqu'ils ne sont plus nécessaires ou lorsqu'on identifie des problèmes de sécurité.

 #3.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les artefacts du modèle retiré sont effacés de manière sécurisée en utilisant une suppression cryptographique sécurisée.
 #3.5.2    Niveau: 2    Rôle: V
 Vérifiez que les événements de retrait de modèle sont consignés avec horodatage et identité de l'acteur, et que les signatures du modèle sont révoquées pour empêcher toute réutilisation.

---

### Références

MLOps Principles
Securing AI/ML Ops – Cisco.com
Audit logs security: cryptographically signed tamper-proof logs
Machine Learning Model Versioning: Top Tools & Best Practices
AI Hygiene Starts with Models and Data Loaders – SEI Blog
How to handle versioning and rollback of a deployed ML model?
Reinforcement fine-tuning – OpenAI API
Auditing Machine Learning models: Governance, Data Security and …
Adversarial Training to Improve Model Robustness
What is AI adversarial robustness? – IBM Research
Exploring Data Provenance: Ensuring Data Integrity and Authenticity
MITRE ATLAS
AWS Prescriptive Guidance – Best practices for retiring applications …

## Infrastructure C4, sécurité de la configuration et du déploiement

### Objectif de contrôle

L'infrastructure d'IA doit être renforcée contre l'escalade de privilèges, la falsification de la chaîne d'approvisionnement et les mouvements latéraux grâce à une configuration sécurisée, une isolation à l'exécution, des pipelines de déploiement fiables et une surveillance complète. Seuls les composants d'infrastructure validés et autorisés atteignent la production via des processus contrôlés garantissant la sécurité, l'intégrité et la traçabilité.

Objectif principal de sécurité : seuls les composants d'infrastructure signés cryptographiquement et analysés pour les vulnérabilités atteignent la production via des pipelines de validation automatisés qui appliquent les politiques de sécurité et maintiennent des pistes d'audit immuables.

---

### C4.1 Isolation de l'environnement d'exécution

Empêcher les échappées de conteneurs et l'escalade de privilèges grâce aux primitives d'isolation au niveau du système d'exploitation.

 #4.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que toutes les charges de travail d'IA s'exécutent avec les permissions minimales nécessaires sur le système d'exploitation, par exemple en supprimant les capacités Linux inutiles dans le cas d'un conteneur.
 #4.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les charges de travail sont protégées par des technologies limitant l'exploitation telles que le sandboxing, les profils seccomp, AppArmor, SELinux ou similaires, et que la configuration est appropriée.
 #4.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que les charges de travail s'exécutent avec un système de fichiers racine en lecture seule, et que tous les montages en écriture sont explicitement définis et renforcés avec des options restrictives (par exemple, noexec, nosuid, nodev).
 #4.1.4    Niveau: 2    Rôle: D/V
 Vérifiez que la surveillance en temps réel détecte les comportements d'élévation de privilèges et d'évasion de conteneurs, puis termine automatiquement les processus fautifs.
 #4.1.5    Niveau: 3    Rôle: D/V
 Vérifiez que les charges de travail d'IA à haut risque fonctionnent dans des environnements isolés matériellement (par exemple, TEEs, hyperviseurs de confiance ou nœuds bare-metal) uniquement après une attestation distante réussie.

---

### C4.2 Chaînes de build et de déploiement sécurisées

Assurez l'intégrité cryptographique et la sécurité de la chaîne d'approvisionnement grâce à des builds reproductibles et des artefacts signés.


 4.2.14.2.2    1: 2    D/V: D/V
 Vérifier que les builds produisent une liste des composants logiciels (SBOM) et sont signés avant d'être acceptés pour le déploiement.
 4.2.14.2.3    1: 2    D/V: D/V
 Vérifier que les signatures des artefacts de build (par exemple, les images de conteneurs) et les métadonnées de provenance sont validées lors du déploiement, et que les artefacts non vérifiés sont rejetés.

---

### C4.3 Sécurité du réseau et contrôle d'accès

Mettre en œuvre un réseau à confiance zéro avec des politiques de refus par défaut et des communications chiffrées.

 #4.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les politiques réseau appliquent un refus par défaut pour l’entrée et la sortie, avec uniquement les services requis explicitement autorisés.
 #4.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que les protocoles d'accès administratif (par ex., SSH, RDP) et l'accès aux services de métadonnées cloud sont restreints et exigent une authentification forte.
 #4.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que le trafic sortant est limité aux destinations approuvées et que toutes les requêtes sont enregistrées.
 #4.3.4    Niveau: 2    Rôle: D/V
 Vérifiez que la communication inter-services utilise TLS mutuel avec validation des certificats et une rotation automatisée régulière.
 #4.3.5    Niveau: 2    Rôle: D/V
 Vérifiez que les charges de travail et les environnements d’IA (dev, test, prod) fonctionnent dans des segments réseau isolés (VPC/VNets) sans accès direct à Internet et sans rôles IAM, groupes de sécurité ou connectivité inter-environnements partagés.

### C4.4 Gestion des Secrets et des Clés Cryptographiques

Protégez les secrets et les clés cryptographiques grâce à un stockage sécurisé, une rotation automatisée et des contrôles d'accès renforcés.

 #4.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que les secrets sont stockés dans un système dédié de gestion des secrets avec chiffrement au repos et isolés des charges de travail des applications.
 #4.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les clés cryptographiques sont générées et stockées dans des modules matériels sécurisés (par exemple, HSM, KMS cloud).
 #4.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que la rotation des secrets est automatisée.
 #4.4.4    Niveau: TRANS ERR    Rôle: 
 Vérifiez que l'accès aux secrets de production nécessite une authentification forte.
 #4.4.5    Niveau: 2    Rôle: D/V
 Vérifiez que les secrets sont déployés aux applications au moment de l'exécution via une solution de gestion des secrets. Les secrets ne doivent jamais être intégrés dans le code source, les fichiers de configuration, les artefacts de build, les images de conteneur ou les variables d'environnement.

---

### C4.5 Sandbox et Validation des Charges de Travail IA

Isolez les modèles d'IA non fiables dans des environnements sécurisés isolés et protégez les charges de travail sensibles en IA en utilisant des environnements d'exécution de confiance (TEE) et des technologies de calcul confidentiel.

 #4.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les modèles d'IA externes ou non fiables s'exécutent dans des environnements isolés (sandboxes).
 #4.5.2    Niveau: 1    Rôle: D/V
 Vérifiez que les charges de travail en environnement isolé n'ont pas de connectivité réseau sortante par défaut, tout accès nécessaire devant être défini explicitement.
 #4.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que l'attestation de la charge de travail est effectuée avant le chargement du modèle ou de la charge de travail, garantissant une preuve cryptographique d'un environnement d'exécution de confiance.
 #4.5.4    Niveau: 3    Rôle: D/V
 Vérifiez que les charges de travail confidentielles s'exécutent au sein d'un environnement d'exécution sécurisé (TEE) qui fournit une isolation renforcée par le matériel, un chiffrement de la mémoire et une protection de l'intégrité.
 #4.5.5    Niveau: 3    Rôle: D/V
 Vérifiez que les services d'inférence confidentiels empêchent l'extraction du modèle grâce à un calcul chiffré avec des poids de modèle scellés et une exécution protégée.
 #4.5.6    Niveau: 3    Rôle: D/V
 Vérifiez que l'orchestration des environnements d'exécution sécurisés inclut la gestion du cycle de vie, l'attestation à distance et les canaux de communication chiffrés.
 #4.5.7    Niveau: 3    Rôle: D/V
 Vérifiez que le calcul multipartite sécurisé (SMPC) permet un entraînement collaboratif de l’IA sans exposer les ensembles de données individuels ni les paramètres du modèle.

---

### C4.6 Gestion des ressources de l'infrastructure IA, sauvegarde et récupération

Prévenir les attaques par épuisement de ressources et assurer une allocation équitable des ressources grâce à des quotas et une surveillance. Maintenir la résilience de l'infrastructure grâce à des sauvegardes sécurisées, des procédures de récupération testées et des capacités de reprise après sinistre.

 #4.6.1    Niveau: 2    Rôle: D/V
 Vérifiez que la consommation des ressources de la charge de travail est limitée de manière appropriée, par exemple avec des ResourceQuotas Kubernetes ou des mécanismes similaires, pour atténuer les attaques par déni de service.
 #4.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que l'épuisement des ressources déclenche des protections automatisées (par exemple, la limitation de débit ou l'isolation de la charge de travail) une fois que les seuils définis de CPU, de mémoire ou de requêtes sont dépassés.
 #4.6.3    Niveau: 2    Rôle: D/V
 Vérifier que les systèmes de sauvegarde fonctionnent dans des réseaux isolés avec des identifiants séparés, et que le système de stockage est soit exploité dans un réseau isolé physiquement (air-gapped), soit qu’il implémente une protection WORM (write-once-read-many) contre toute modification non autorisée.

---

### C4.7 Sécurité matérielle de l'IA

Sécurisez les composants matériels spécifiques à l'IA, y compris les GPU, les TPU et les accélérateurs IA spécialisés.

 #4.7.1    Niveau: 2    Rôle: D/V
 Vérifiez qu'avant l'exécution de la charge de travail, l'intégrité de l'accélérateur d'IA est validée à l'aide de mécanismes d'attestation basés sur le matériel (par exemple, TPM, DRTM ou équivalent).
 #4.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que la mémoire de l'accélérateur (GPU) est isolée entre les charges de travail via des mécanismes de partitionnement avec une sanitation de la mémoire entre les tâches.
 #4.7.3    Niveau: 3    Rôle: D/V
 Vérifiez que les modules de sécurité matérielle (HSM) protègent les poids des modèles d'IA et les clés cryptographiques avec une certification conforme à FIPS 140-3 Niveau 3 ou Common Criteria EAL4+.

---

### C4.8 Sécurité de l'IA en périphérie et distribuée

Déploiements AI distribués sécurisés incluant l'informatique en périphérie, l'apprentissage fédéré et les architectures multi-sites.

 #4.8.1    Niveau: 2    Rôle: D/V
 Vérifiez que les dispositifs AI en périphérie s'authentifient auprès de l'infrastructure centrale en utilisant le TLS mutuel.
 #4.8.2    Niveau: 2    Rôle: D/V
 Vérifiez que les dispositifs périphériques mettent en œuvre un démarrage sécurisé avec des signatures vérifiées et une protection contre la régression afin d'éviter les attaques de rétrogradation du firmware.
 #4.8.3    Niveau: 3    Rôle: D/V
 Vérifiez que la coordination de l’IA distribuée utilise des mécanismes de consensus tolérants aux fautes byzantines avec validation des participants et détection des nœuds malveillants.
 #4.8.4    Niveau: 3    Rôle: D/V
 Vérifiez que la communication de la périphérie au cloud prend en charge la limitation de bande passante, la compression des données et le fonctionnement hors ligne sécurisé avec un stockage local chiffré.

---

### Références

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework

## C5 Contrôle d'accès et identité pour les composants et utilisateurs d'IA

### Objectif de contrôle

Un contrôle d'accès efficace pour les systèmes d'IA nécessite une gestion robuste des identités, une autorisation contextuelle et une application en temps réel suivant les principes du zéro-trust. Ces contrôles garantissent que les humains, les services et les agents autonomes n'interagissent avec les modèles, les données et les ressources informatiques que dans les périmètres explicitement accordés, avec des capacités continues de vérification et d'audit.

---

### C5.1 Gestion des identités et authentification

Établir des identités cryptographiquement sécurisées pour toutes les entités avec une authentification multi-facteurs pour les opérations privilégiées.

 #5.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les utilisateurs humains et les principaux de service s'authentifient via un fournisseur d'identité d'entreprise centralisé (IdP) utilisant les protocoles OIDC/SAML avec des correspondances uniques identité-vers-token (pas de comptes ou d'identifiants partagés).
 #5.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les opérations à haut risque (déploiement du modèle, exportation des poids, accès aux données d'entraînement, modifications de la configuration en production) nécessitent une authentification multi-facteurs ou une authentification renforcée avec une revalidation de session.
 #5.1.3    Niveau: 2    Rôle: D
 Vérifiez que les nouveaux principaux subissent une vérification d'identité conforme à la norme NIST 800-63-3 IAL-2 ou à des normes équivalentes avant d'accéder au système de production.
 #5.1.4    Niveau: 2    Rôle: V
 Vérifiez que les revues d'accès sont effectuées trimestriellement avec une détection automatisée des comptes dormants, l'application de la rotation des identifiants et des workflows de suppression des accès.
 #5.1.5    Niveau: 3    Rôle: D/V
 Vérifiez que les agents d’IA fédérés s’authentifient via des assertions JWT signées qui ont une durée de vie maximale de 24 heures et incluent une preuve cryptographique d’origine.

---

### C5.2 Autorisation des ressources et principe du moindre privilège

Mettez en œuvre des contrôles d'accès granulaires pour toutes les ressources d'IA avec des modèles d'autorisation explicites et des pistes d'audit.

 #5.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque ressource d'IA (ensembles de données, modèles, points de terminaison, collections vectorielles, indices d'incorporation, instances de calcul) applique des contrôles d'accès basés sur les rôles avec des listes d'autorisation explicites et des politiques de refus par défaut.
 #5.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que les principes du moindre privilège sont appliqués par défaut avec les comptes de service commençant par des permissions en lecture seule et qu'une justification commerciale documentée est requise pour l'accès en écriture.
 #5.2.3    Niveau: 1    Rôle: V
 Vérifiez que toutes les modifications du contrôle d'accès sont liées à des demandes de changement approuvées et enregistrées de manière immuable avec des horodatages, les identités des acteurs, les identifiants des ressources et les deltas de permissions.
 #5.2.4    Niveau: 2    Rôle: D
 Vérifiez que les étiquettes de classification des données (PII, PHI, contrôlées à l'exportation, propriétaires) se propagent automatiquement aux ressources dérivées (embeddings, caches d'invite, sorties de modèle) avec une application cohérente des politiques.
 #5.2.5    Niveau: 2    Rôle: D/V
 Vérifiez que les tentatives d'accès non autorisées et les événements d'élévation de privilèges déclenchent des alertes en temps réel avec des métadonnées contextuelles vers les systèmes SIEM dans un délai de 5 minutes.

---

### C5.3 Évaluation Dynamique de la Politique

Déployez des moteurs de contrôle d'accès basé sur les attributs (ABAC) pour des décisions d'autorisation contextuelles avec des capacités d'audit.

 #5.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les décisions d'autorisation sont externalisées vers un moteur de politique dédié (OPA, Cedar ou équivalent) accessible via des API authentifiées avec une protection cryptographique de l'intégrité.
 #5.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que les politiques évaluent les attributs dynamiques au moment de l'exécution, y compris le niveau de habilitation de l'utilisateur, la classification de la sensibilité des ressources, le contexte de la requête, l'isolation du locataire et les contraintes temporelles.
 #5.3.3    Niveau: 2    Rôle: D
 Vérifiez que les définitions de stratégie sont contrôlées en version, examinées par des pairs et validées par des tests automatisés dans les pipelines CI/CD avant le déploiement en production.
 #5.3.4    Niveau: 2    Rôle: V
 Vérifiez que les résultats de l’évaluation des politiques incluent des justifications décisionnelles structurées et sont transmis aux systèmes SIEM pour l’analyse de corrélation et la génération de rapports de conformité.
 #5.3.5    Niveau: 3    Rôle: D/V
 Vérifiez que les valeurs de time-to-live (TTL) du cache de politique ne dépassent pas 5 minutes pour les ressources à haute sensibilité et 1 heure pour les ressources standards disposant de capacités d'invalidation de cache.

---

### C5.4 Application de la sécurité au moment de la requête

Mettre en œuvre des contrôles de sécurité au niveau de la base de données avec filtrage obligatoire et politiques de sécurité au niveau des lignes.

 #5.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que toutes les requêtes des bases de données vectorielles et SQL incluent des filtres de sécurité obligatoires (ID du locataire, étiquettes de sensibilité, périmètre utilisateur) appliqués au niveau du moteur de base de données, et non dans le code de l'application.
 #5.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les politiques de sécurité au niveau des lignes (RLS) et le masquage au niveau des champs sont activés avec l'héritage des politiques pour toutes les bases de données vectorielles, indices de recherche et ensembles de données d'entraînement.
 #5.4.3    Niveau: 2    Rôle: D
 Vérifiez que les évaluations d'autorisation échouées empêcheront les « attaques du substitut confus » en interrompant immédiatement les requêtes et en renvoyant des codes d'erreur d'autorisation explicites plutôt qu'en renvoyant des ensembles de résultats vides.
 #5.4.4    Niveau: 2    Rôle: V
 Vérifiez que la latence d'évaluation des politiques est continuellement surveillée avec des alertes automatisées pour les conditions de dépassement de délai pouvant permettre un contournement de l'autorisation.
 #5.4.5    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes de nouvelle tentative de requête réévaluent les politiques d'autorisation afin de prendre en compte les modifications dynamiques des permissions au sein des sessions utilisateur actives.

---

### Filtrage de sortie C5.5 et prévention des pertes de données

Déployez des contrôles de post-traitement pour prévenir l’exposition non autorisée de données dans le contenu généré par l’IA.

 #5.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les mécanismes de filtrage post-inférence analysent et révisent les informations personnelles identifiables non autorisées, les informations classifiées et les données propriétaires avant de fournir le contenu aux demandeurs.
 #5.5.2    Niveau: 1    Rôle: D/V
 Vérifiez que les citations, références et attributions de sources dans les résultats du modèle sont validées par rapport aux droits d'accès de l'appelant et supprimées en cas de détection d'un accès non autorisé.
 #5.5.3    Niveau: 2    Rôle: D
 Vérifiez que les restrictions de format de sortie (PDFs sécurisés, images sans métadonnées, types de fichiers approuvés) sont appliquées en fonction des niveaux d'autorisation des utilisateurs et des classifications des données.
 #5.5.4    Niveau: 2    Rôle: V
 Vérifiez que les algorithmes de rédaction sont déterministes, contrôlés par version, et conservent des journaux d'audit pour soutenir les enquêtes de conformité et l'analyse médico-légale.
 #5.5.5    Niveau: 3    Rôle: V
 Vérifiez que les événements de rédaction à haut risque génèrent des journaux adaptatifs incluant des hachages cryptographiques du contenu original pour une récupération judiciaire sans exposition des données.

---

### C5.6 Isolation multi-locataire

Garantir l'isolation cryptographique et logique entre les locataires dans une infrastructure d'IA partagée.

 #5.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que les espaces mémoire, les magasins d'intégration, les entrées de cache et les fichiers temporaires sont séparés par espace de noms pour chaque locataire, avec une suppression sécurisée lors de la suppression du locataire ou de la fin de la session.
 #5.6.2    Niveau: 1    Rôle: D/V
 Vérifiez que chaque requête API inclut un identifiant de locataire authentifié qui est validé cryptographiquement par rapport au contexte de session et aux droits de l'utilisateur.
 #5.6.3    Niveau: 2    Rôle: D
 Vérifiez que les politiques réseau appliquent des règles de refus par défaut pour la communication inter-locataires au sein des maillages de services et des plateformes d'orchestration de conteneurs.
 #5.6.4    Niveau: 3    Rôle: D
 Vérifiez que les clés de chiffrement sont uniques par locataire avec la prise en charge des clés gérées par le client (CMK) et un isolement cryptographique entre les magasins de données des locataires.

---

### C5.7 Autorisation des agents autonomes

Contrôlez les permissions pour les agents d'IA et les systèmes autonomes grâce à des jetons de capacité à périmètre défini et à une autorisation continue.

 #5.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les agents autonomes reçoivent des jetons de capacité délimités qui énumèrent explicitement les actions autorisées, les ressources accessibles, les limites temporelles et les contraintes opérationnelles.
 #5.7.2    Niveau: 1    Rôle: D/V
 Vérifiez que les capacités à haut risque (accès au système de fichiers, exécution de code, appels API externes, transactions financières) sont désactivées par défaut et nécessitent des autorisations explicites pour leur activation avec des justifications commerciales.
 #5.7.3    Niveau: 2    Rôle: D
 Vérifiez que les jetons de capacité sont liés aux sessions utilisateur, incluent une protection cryptographique de l'intégrité et garantissent qu'ils ne peuvent pas être conservés ou réutilisés dans des scénarios hors ligne.
 #5.7.4    Niveau: 2    Rôle: V
 Vérifiez que les actions initiées par l'agent font l'objet d'une autorisation secondaire via le moteur de politique ABAC avec une évaluation complète du contexte et une journalisation d'audit.
 #5.7.5    Niveau: 3    Rôle: V
 Vérifiez que les conditions d'erreur de l'agent et la gestion des exceptions incluent des informations sur le périmètre des capacités pour soutenir l'analyse des incidents et l'enquête médico-légale.

---

### Références

#### Normes et Cadres

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Guides de mise en œuvre

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### Sécurité spécifique à l'IA

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## Sécurité de la chaîne d'approvisionnement C6 pour les modèles, frameworks et données

### Objectif de contrôle

Les attaques sur la chaîne d'approvisionnement en IA exploitent des modèles, des frameworks ou des ensembles de données tiers pour y intégrer des portes dérobées, des biais ou du code exploitable. Ces contrôles offrent une traçabilité de bout en bout, une gestion des vulnérabilités et une surveillance pour protéger l'ensemble du cycle de vie du modèle.

---

### C6.1 Vérification et Provenance des Modèles Pré-entraînés

Évaluer et authentifier les origines, les licences et les comportements cachés des modèles tiers avant toute phase de fine-tuning ou de déploiement.

 #6.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque artefact de modèle tiers inclut un enregistrement de provenance signé identifiant le dépôt source et le hash du commit.
 #6.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les modèles sont analysés pour détecter des couches malveillantes ou des déclencheurs de cheval de Troie à l'aide d'outils automatisés avant l'importation.
 #6.1.3    Niveau: 2    Rôle: D
 Vérifiez que la fine-tuning par transfert d’apprentissage passe l’évaluation adversaire pour détecter les comportements cachés.
 #6.1.4    Niveau: 2    Rôle: V
 Vérifiez que les licences des modèles, les étiquettes de contrôle à l'exportation et les déclarations d'origine des données sont enregistrées dans une entrée ML-BOM.
 #6.1.5    Niveau: 3    Rôle: D/V
 Vérifiez que les modèles à haut risque (poids téléchargés publiquement, créateurs non vérifiés) restent mis en quarantaine jusqu'à ce qu'une revue humaine et une validation soient effectuées.

---

### C6.2 Analyse des cadres et des bibliothèques

Analyser en continu les frameworks et bibliothèques de ML à la recherche de CVE et de code malveillant afin de maintenir la sécurité de la pile d’exécution.

 #6.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les pipelines CI exécutent des analyseurs de dépendances sur les frameworks d'IA et les bibliothèques critiques.
 #6.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que les vulnérabilités critiques (CVSS ≥ 7.0) bloquent la promotion vers les images de production.
 #6.2.3    Niveau: 2    Rôle: D
 Vérifiez que l'analyse statique du code s'exécute sur les bibliothèques ML forkées ou fournies.
 #6.2.4    Niveau: 2    Rôle: V
 Vérifiez que les propositions de mise à niveau du framework incluent une évaluation de l'impact sur la sécurité faisant référence aux flux CVE publics.
 #6.2.5    Niveau: 3    Rôle: V
 Vérifiez que les capteurs d'exécution alertent sur les chargements dynamiques de bibliothèques inattendus qui dévient du SBOM signé.

---

### C6.3 Verrouillage et Vérification des Dépendances

Épingler chaque dépendance à des digests immuables et reproduire les builds pour garantir des artefacts identiques et inviolables.

 #6.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les gestionnaires de paquets imposent le verrouillage des versions via des fichiers de verrouillage.
 #6.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que des condensats immuables sont utilisés au lieu de balises mutables dans les références de conteneurs.
 #6.3.3    Niveau: 2    Rôle: D
 Vérifiez que les contrôles de build reproductible comparent les hachages entre les exécutions CI afin de garantir des résultats identiques.
 #6.3.4    Niveau: 2    Rôle: V
 Vérifiez que les attestations de construction sont conservées pendant 18 mois pour la traçabilité des audits.
 #6.3.5    Niveau: 3    Rôle: D
 Vérifiez que les dépendances expirées déclenchent des PR automatisées pour mettre à jour ou forker les versions épinglées.

---

### C6.4 Application de la Source Fiable

Autoriser les téléchargements d’artefacts uniquement à partir de sources approuvées par l’organisation et vérifiées cryptographiquement, et bloquer tout le reste.

 #6.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que les poids du modèle, les ensembles de données et les conteneurs sont téléchargés uniquement à partir de domaines approuvés ou de registres internes.
 #6.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les signatures Sigstore/Cosign valident l'identité de l'éditeur avant que les artefacts ne soient mis en cache localement.
 #6.4.3    Niveau: 2    Rôle: D
 Vérifiez que les proxys de sortie bloquent les téléchargements d'artefacts non authentifiés afin de faire respecter la politique de source fiable.
 #6.4.4    Niveau: 2    Rôle: V
 Vérifier que les listes blanches du référentiel sont examinées trimestriellement avec une preuve de justification commerciale pour chaque entrée.
 #6.4.5    Niveau: 3    Rôle: V
 Vérifiez que les violations de politique déclenchent la mise en quarantaine des artefacts et le retour en arrière des exécutions de pipeline dépendantes.

---

### C6.5 Évaluation des risques des ensembles de données tiers

Évaluer les ensembles de données externes pour le empoisonnement, les biais et la conformité légale, et les surveiller tout au long de leur cycle de vie.

 #6.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les ensembles de données externes font l’objet d’une évaluation du risque d’empoisonnement (par exemple, empreinte de données, détection des valeurs aberrantes).
 #6.5.2    Niveau: 1    Rôle: D
 Vérifiez que les métriques de biais (parité démographique, égalité des chances) sont calculées avant l'approbation du jeu de données.
 #6.5.3    Niveau: 2    Rôle: V
 Vérifiez que la provenance et les conditions de licence des jeux de données sont enregistrées dans les entrées ML-BOM.
 #6.5.4    Niveau: 2    Rôle: V
 Vérifiez que la surveillance périodique détecte les dérives ou la corruption dans les ensembles de données hébergés.
 #6.5.5    Niveau: 3    Rôle: D
 Vérifiez que le contenu interdit (droits d'auteur, informations personnelles identifiables) est supprimé automatiquement via un nettoyage automatisé avant l'entraînement.

---

### C6.6 Surveillance des attaques sur la chaîne d'approvisionnement

Détectez tôt les menaces de la chaîne d'approvisionnement grâce aux flux CVE, à l'analyse des journaux d'audit et aux simulations d'équipes rouges.

 #6.6.1    Niveau: 1    Rôle: V
 Vérifiez que les journaux d'audit CI/CD sont transmis au SIEM pour la détection d'extractions de paquets anomalies ou d'étapes de construction altérées.
 #6.6.2    Niveau: 2    Rôle: D
 Vérifiez que les guides d'intervention en cas d'incident incluent des procédures de restauration pour les modèles ou bibliothèques compromis.
 #6.6.3    Niveau: 3    Rôle: V
 Vérifiez que l'enrichissement des renseignements sur les menaces étiquette les indicateurs spécifiques au ML (par exemple, les IoC de l'empoisonnement de modèle) dans le triage des alertes.

---

### C6.7 ML‑BOM pour les artefacts de modèle

Générez et signez des SBOMs spécifiques au ML détaillés (ML‑BOMs) afin que les utilisateurs en aval puissent vérifier l'intégrité des composants lors du déploiement.

 #6.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque artefact de modèle publie un ML-BOM répertoriant les ensembles de données, les poids, les hyperparamètres et les licences.
 #6.7.2    Niveau: 1    Rôle: D/V
 Vérifiez que la génération de ML‑BOM et la signature Cosign sont automatisées dans l'intégration continue (CI) et requises pour la fusion.
 #6.7.3    Niveau: 2    Rôle: D
 Vérifiez que les contrôles de complétude ML-BOM échouent la construction si des métadonnées de composants (hachage, licence) sont manquantes.
 #6.7.4    Niveau: 2    Rôle: V
 Vérifiez que les utilisateurs en aval peuvent interroger les ML-BOM via l'API pour valider les modèles importés lors du déploiement.
 #6.7.5    Niveau: 3    Rôle: V
 Vérifiez que les ML‑BOM sont contrôlés par version et comparés pour détecter les modifications non autorisées.

---

### Références

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## Comportement du modèle C7, contrôle de la sortie et assurance de sécurité

### Objectif de contrôle

Les sorties des modèles doivent être structurées, fiables, sûres, explicables et continuellement surveillées en production. Cela permet de réduire les hallucinations, les fuites de données privées, les contenus nuisibles et les actions incontrôlées, tout en augmentant la confiance des utilisateurs et la conformité réglementaire.

---

### C7.1 Application des règles du format de sortie

Les schémas stricts, le décodage contraint et la validation en aval empêchent le contenu malformé ou malveillant de se propager.

 #7.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que les schémas de réponse (par exemple, JSON Schema) sont fournis dans l'invite système et que chaque sortie est automatiquement validée ; les sorties non conformes déclenchent une réparation ou un rejet.
 #7.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que le décodage contraint (tokens d'arrêt, regex, max-tokens) est activé pour éviter les débordements ou les canaux secondaires d'injection de prompt.
 #7.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que les composants en aval considèrent les sorties comme non fiables et les valident selon des schémas ou des désérialiseurs sécurisés contre les injections.
 #7.1.4    Niveau: 3    Rôle: V
 Vérifiez que les événements de sortie incorrecte sont enregistrés, soumis à un contrôle de débit et affichés dans la surveillance.

---

### C7.2 Détection et atténuation des hallucinations

L'estimation de l'incertitude et les stratégies de repli limitent les réponses fabriquées.

 #7.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les log-probabilités au niveau des tokens, la self-consistance ensembliste ou les détecteurs d'hallucination affinés attribuent un score de confiance à chaque réponse.
 #7.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que les réponses en dessous d’un seuil de confiance configurable déclenchent des flux de travail de repli (par exemple, génération augmentée par récupération, modèle secondaire ou révision humaine).
 #7.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les incidents d'hallucination sont étiquetés avec des métadonnées de cause profonde et envoyés aux pipelines d'analyse post-mortem et de réglage fin.
 #7.2.4    Niveau: 3    Rôle: D/V
 Vérifiez que les seuils et les détecteurs sont recalibrés après des mises à jour majeures du modèle ou de la base de connaissances.
 #7.2.5    Niveau: 3    Rôle: V
 Vérifiez que les visualisations du tableau de bord suivent les taux d'hallucination.

---

### C7.3 Filtrage de la sécurité et de la confidentialité des sorties

Les filtres de politique et la couverture de l'équipe rouge protègent les utilisateurs et les données confidentielles.

 #7.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les classificateurs pré et post-génération bloquent les contenus haineux, harcelants, d’automutilation, extrémistes et sexuellement explicites conformément à la politique.
 #7.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que la détection de PII/PCI et la rédaction automatique s’exécutent sur chaque réponse ; les violations entraînent un incident de confidentialité.
 #7.3.3    Niveau: 2    Rôle: D
 Vérifiez que les étiquettes de confidentialité (par exemple, secrets commerciaux) se propagent à travers les modalités afin d'empêcher toute fuite dans le texte, les images ou le code.
 #7.3.4    Niveau: 3    Rôle: D/V
 Vérifiez que les tentatives de contournement du filtre ou les classifications à haut risque nécessitent une approbation secondaire ou une réauthentification de l'utilisateur.
 #7.3.5    Niveau: 3    Rôle: D/V
 Vérifiez que les seuils de filtrage reflètent les juridictions légales ainsi que le contexte d'âge/rôle de l'utilisateur.

---

### C7.4 Limitation de la sortie et des actions

Les limites de fréquence et les portes d'approbation empêchent les abus et l'autonomie excessive.

 #7.4.1    Niveau: 1    Rôle: D
 Vérifiez que les quotas par utilisateur et par clé API limitent les requêtes, les jetons et le coût avec un retour en arrière exponentiel en cas d'erreurs 429.
 #7.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les actions privilégiées (écriture de fichiers, exécution de code, appels réseau) nécessitent une approbation basée sur une politique ou une intervention humaine.
 #7.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que les contrôles de cohérence cross-modaux garantissent que les images, le code et le texte générés pour la même demande ne peuvent pas être utilisés pour dissimuler du contenu malveillant.
 #7.4.4    Niveau: 2    Rôle: D
 Vérifiez que la profondeur de délégation des agents, les limites de récursion et les listes d'outils autorisés sont configurées explicitement.
 #7.4.5    Niveau: 3    Rôle: V
 Vérifiez que la violation des limites génère des événements de sécurité structurés pour l'ingestion SIEM.

---

### C7.5 Explicabilité de la sortie

Les signaux transparents améliorent la confiance des utilisateurs et le débogage interne.

 #7.5.1    Niveau: 2    Rôle: D/V
 Vérifiez que les scores de confiance destinés à l'utilisateur ou les résumés brefs de raisonnement sont exposés lorsque l'évaluation des risques le juge approprié.
 #7.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les explications générées évitent de révéler des invites système sensibles ou des données propriétaires.
 #7.5.3    Niveau: 3    Rôle: D
 Vérifiez que le système capture les log-probabilités au niveau des tokens ou les cartes d’attention et les stocke pour une inspection autorisée.
 #7.5.4    Niveau: 3    Rôle: V
 Vérifiez que les artefacts d'explicabilité sont contrôlés en version parallèlement aux versions du modèle pour garantir leur auditabilité.

---

### C7.6 Intégration de la surveillance

L'observabilité en temps réel ferme la boucle entre le développement et la production.

 #7.6.1    Niveau: 1    Rôle: D
 Vérifiez que les métriques (violations du schéma, taux d'hallucination, toxicité, fuites d'IPI, latence, coût) sont transmises à une plateforme centrale de surveillance.
 #7.6.2    Niveau: 1    Rôle: V
 Vérifiez que des seuils d'alerte sont définis pour chaque métrique de sécurité, avec des voies d'escalade en astreinte.
 #7.6.3    Niveau: 2    Rôle: V
 Vérifiez que les tableaux de bord corrèlent les anomalies de sortie avec le modèle/version, le drapeau de fonctionnalité et les modifications des données en amont.
 #7.6.4    Niveau: 2    Rôle: D/V
 Vérifiez que les données de surveillance sont réinjectées dans le processus de réentraînement, d’ajustement fin ou de mise à jour des règles dans un flux de travail MLOps documenté.
 #7.6.5    Niveau: 3    Rôle: V
 Vérifiez que les pipelines de surveillance sont soumis à des tests de pénétration et contrôlés par accès afin d'éviter la fuite de journaux sensibles.

---

### 7.7 Mesures de protection des médias génératifs

Assurez-vous que les systèmes d'IA ne génèrent pas de contenu médiatique illégal, nuisible ou non autorisé en appliquant des contraintes politiques, une validation des sorties et une traçabilité.

 #7.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les invites système et les instructions utilisateur interdisent explicitement la génération de médias deepfake illégaux, nuisibles ou non consensuels (par exemple, image, vidéo, audio).
 #7.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que les invites sont filtrées pour détecter les tentatives de génération d'usurpations d'identité, de deepfakes à caractère sexuel explicite ou de médias représentant de véritables individus sans consentement.
 #7.7.3    Niveau: 2    Rôle: V
 Vérifiez que le système utilise le hachage perceptuel, la détection de filigrane ou l’empreinte digitale pour empêcher la reproduction non autorisée de médias protégés par des droits d’auteur.
 #7.7.4    Niveau: 3    Rôle: D/V
 Vérifiez que tous les médias générés sont signés cryptographiquement, filigranés ou intégrés avec des métadonnées de provenance résistantes à la falsification pour une traçabilité en aval.
 #7.7.5    Niveau: 3    Rôle: V
 Vérifiez que les tentatives de contournement (par exemple, l’obscurcissement des invites, l’argot, les formulations adversariales) sont détectées, enregistrées et soumises à une limitation de débit ; les abus répétés sont signalés aux systèmes de surveillance.

### Références

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
Sensitive Information Disclosure in LLMs
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## Sécurité de la mémoire C8, des embeddings et des bases de données vectorielles

### Objectif de contrôle

Les embeddings et les bases de données vectorielles agissent comme la « mémoire vivante » des systèmes d'IA contemporains, acceptant en continu les données fournies par les utilisateurs et les réintégrant dans les contextes des modèles via la génération augmentée par récupération (RAG). Si cette mémoire n'est pas contrôlée, elle peut divulguer des informations personnelles identifiables (PII), violer le consentement ou être inversée pour reconstruire le texte original. L'objectif de cette famille de contrôles est de renforcer les pipelines de mémoire et les bases de données vectorielles afin que l'accès soit à moindre privilège, que les embeddings préservent la confidentialité, que les vecteurs stockés expirent ou puissent être révoqués à la demande, et que la mémoire par utilisateur ne contamine jamais les invites ou les complétions d'un autre utilisateur.

---

### C8.1 Contrôles d'accès sur la mémoire et les indices RAG

Appliquez des contrôles d'accès granulaires sur chaque collection de vecteurs.

 #8.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que les règles de contrôle d'accès au niveau des lignes/namespaces restreignent les opérations d'insertion, de suppression et de requête par locataire, collection ou étiquette de document.
 #8.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les clés API ou les JWT contiennent des revendications limitées (par exemple, des identifiants de collection, des verbes d'action) et qu'ils sont renouvelés au moins chaque trimestre.
 #8.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que les tentatives d'escalade de privilèges (par exemple, les requêtes de similarité entre espaces de noms) sont détectées et enregistrées dans un SIEM dans un délai de 5 minutes.
 #8.1.4    Niveau: 2    Rôle: D/V
 Vérifiez que la base de données vectorielle consigne dans les journaux l'identifiant du sujet, l'opération, l'ID/espace de noms du vecteur, le seuil de similarité et le nombre de résultats.
 #8.1.5    Niveau: 3    Rôle: V
 Vérifiez que les décisions d'accès sont testées pour détecter les failles de contournement chaque fois que les moteurs sont mis à jour ou que les règles de partitionnement d'index changent.

---

### C8.2 Assainissement et validation des intégrations

Pré-filtrer le texte pour les informations personnelles identifiables (IPI), les masquer ou les pseudonymiser avant la vectorisation, et éventuellement post-traiter les embeddings pour éliminer les signaux résiduels.

 #8.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les données PII et réglementées sont détectées via des classificateurs automatisés et masquées, tokenisées ou supprimées avant l'intégration.
 #8.2.2    Niveau: 1    Rôle: D
 Vérifiez que les pipelines d’intégration rejettent ou mettent en quarantaine les entrées contenant du code exécutable ou des artefacts non UTF-8 susceptibles d’empoisonner l’index.
 #8.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que la désanonymisation locale ou métrique à confidentialité différentielle est appliquée aux embeddings de phrases dont la distance par rapport à tout jeton PII connu est inférieure à un seuil configurable.
 #8.2.4    Niveau: 2    Rôle: V
 Vérifiez que l'efficacité de la désinfection (par exemple, le rappel de la suppression des informations personnelles identifiables, la dérive sémantique) est validée au moins semestriellement à l'aide de corpus de référence.
 #8.2.5    Niveau: 3    Rôle: D/V
 Vérifiez que les configurations de désinfection sont contrôlées par version et que les modifications font l'objet d'une revue par les pairs.

---

### C8.3 Expiration, Révocation et Suppression de la Mémoire

Le RGPD « droit à l’oubli » et les lois similaires exigent une suppression rapide ; les magasins de vecteurs doivent donc prendre en charge les TTL, les suppressions définitives et le marquage des entrées comme obsolètes afin que les vecteurs révoqués ne puissent pas être récupérés ni réindexés.

 #8.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque vecteur et enregistrement de métadonnées porte un TTL ou une étiquette de rétention explicite respectée par les tâches de nettoyage automatisées.
 #8.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que les demandes de suppression initiées par l'utilisateur suppriment les vecteurs, les métadonnées, les copies en cache et les indices dérivés dans un délai de 30 jours.
 #8.3.3    Niveau: 2    Rôle: D
 Vérifiez que les suppressions logiques sont suivies d'un effacement cryptographique des blocs de stockage si le matériel le prend en charge, ou par la destruction de la clé du coffre-fort.
 #8.3.4    Niveau: 3    Rôle: D/V
 Vérifiez que les vecteurs expirés sont exclus des résultats de la recherche du plus proche voisin en moins de 500 ms après leur expiration.

---

### C8.4 Prévenir l'inversion et la fuite d'intégration

Les défenses récentes—superposition de bruit, réseaux de projection, perturbation des neurones de confidentialité, et chiffrement au niveau de la couche applicative—peuvent réduire les taux d'inversion au niveau des jetons à moins de 5 %.

 #8.4.1    Niveau: 1    Rôle: V
 Vérifier qu’un modèle de menace formel couvrant les attaques d'inversion, d'appartenance et d'inférence d'attribut existe et qu'il est révisé annuellement.
 #8.4.2    Niveau: 2    Rôle: D/V
 Vérifiez que le chiffrement au niveau de la couche applicative ou le chiffrement recherché protège les vecteurs contre les lectures directes par les administrateurs de l'infrastructure ou le personnel du cloud.
 #8.4.3    Niveau: 3    Rôle: V
 Vérifiez que les paramètres de défense (ε pour DP, bruit σ, rang de projection k) équilibrent la confidentialité ≥ 99 % de protection des jetons et l'utilité ≤ 3 % de perte de précision.
 #8.4.4    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques de résilience à l'inversion font partie des critères de validation pour les mises à jour de modèle, avec des budgets de régression définis.

---

### C8.5 Application de la portée pour la mémoire spécifique à l'utilisateur

La fuite entre locataires reste un risque majeur de RAG : des requêtes de similarité mal filtrées peuvent révéler les documents privés d’un autre client.

 #8.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque requête de récupération est post-filtrée par l'ID du locataire/utilisateur avant d'être transmise à l'invite LLM.
 #8.5.2    Niveau: 1    Rôle: D
 Vérifiez que les noms de collections ou les identifiants avec espaces de noms sont salés par utilisateur ou locataire afin que les vecteurs ne puissent pas entrer en collision entre les domaines.
 #8.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que les résultats de similarité supérieurs à un seuil de distance configurable mais en dehors du périmètre de l'appelant sont rejetés et déclenchent des alertes de sécurité.
 #8.5.4    Niveau: 2    Rôle: V
 Vérifiez que les tests de charge multi-locataires simulent des requêtes adversariales tentant de récupérer des documents hors de leur périmètre et démontrent une absence totale de fuite.
 #8.5.5    Niveau: 3    Rôle: D/V
 Vérifiez que les clés de chiffrement sont segregées par locataire, garantissant une isolation cryptographique même si le stockage physique est partagé.

---

### C8.6 Sécurité Avancée du Système de Mémoire

Contrôles de sécurité pour des architectures mémoire sophistiquées incluant la mémoire épisodique, sémantique et de travail avec des exigences spécifiques d’isolation et de validation.

 #8.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que les différents types de mémoire (épisodique, sémantique, de travail) disposent de contextes de sécurité isolés avec des contrôles d'accès basés sur les rôles, des clés de chiffrement distinctes, et des schémas d'accès documentés pour chaque type de mémoire.
 #8.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que les processus de consolidation de la mémoire incluent une validation de sécurité pour empêcher l'injection de souvenirs malveillants via la désinfection du contenu, la vérification de la source et les contrôles d'intégrité avant le stockage.
 #8.6.3    Niveau: 2    Rôle: D/V
 Vérifiez que les requêtes de récupération de mémoire sont validées et nettoyées afin de prévenir l'extraction d'informations non autorisées via l'analyse des modèles de requête, l'application du contrôle d'accès et le filtrage des résultats.
 #8.6.4    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes d'oubli de la mémoire suppriment de manière sécurisée les informations sensibles avec des garanties d'effacement cryptographique en utilisant la suppression de clés, l'écrasement multiple ou la suppression sécurisée matérielle avec des certificats de vérification.
 #8.6.5    Niveau: 3    Rôle: D/V
 Vérifiez que l'intégrité du système de mémoire est continuellement surveillée pour détecter toute modification ou corruption non autorisée à l'aide de sommes de contrôle, de journaux d'audit et d'alertes automatisées lorsque le contenu de la mémoire change en dehors des opérations normales.

---

### Références

Vector database security: Pinecone – IronCore Labs
Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera
Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances
Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv
DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview
Art. 17 GDPR – Right to Erasure
Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai
PII Identification and Removal – NVIDIA NeMo Docs
De-identifying Sensitive Data – Google Cloud DLP
Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails
Think Your RAG Is Secure? Think Again – Medium
Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn
Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog

## 9 Orchestration autonome et sécurité de l'action agentique

### Objectif de contrôle

Assurez-vous que les systèmes d’IA autonomes ou multi-agents ne puissent exécuter que des actions explicitement prévues, authentifiées, auditables, et respectant des seuils définis de coût et de risque. Cela protège contre des menaces telles que la compromission de système autonome, le mauvais usage d’outils, la détection de boucle agent, le détournement de communication, l’usurpation d’identité, la manipulation d’essaim, et la manipulation d’intention.

---

### 9.1 Budgets de planification des tâches d'agent et de récursion

Limiter les plans récursifs et imposer des points de contrôle humains pour les actions privilégiées.

 #9.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que la profondeur maximale de récursion, la largeur, le temps écoulé, les jetons et le coût monétaire par exécution d'agent sont configurés de manière centralisée et sous contrôle de version.
 #9.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les actions privilégiées ou irréversibles (par exemple, les validations de code, les transferts financiers) nécessitent une approbation humaine explicite via un canal auditable avant leur exécution.
 #9.1.3    Niveau: 2    Rôle: D
 Vérifiez que les moniteurs de ressources en temps réel déclenchent une interruption du disjoncteur lorsque tout seuil de budget est dépassé, arrêtant ainsi toute extension supplémentaire des tâches.
 #9.1.4    Niveau: 2    Rôle: D/V
 Vérifiez que les événements de disjoncteur sont enregistrés avec l'ID de l'agent, la condition de déclenchement et l'état du plan capturé pour un examen médico-légal.
 #9.1.5    Niveau: 3    Rôle: V
 Vérifiez que les tests de sécurité couvrent les scénarios d'épuisement de budget et de plan incontrôlé, en confirmant un arrêt sécurisé sans perte de données.
 #9.1.6    Niveau: 3    Rôle: D
 Vérifiez que les politiques budgétaires sont exprimées en tant que politique sous forme de code et appliquées dans le CI/CD pour bloquer la dérive de configuration.

---

### 9.2 Bac à sable des plugins d'outils

Isoler les interactions des outils pour prévenir tout accès non autorisé au système ou toute exécution de code.

 #9.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque outil/plugin s'exécute à l'intérieur d'un système d'exploitation, d'un conteneur ou d'un bac à sable de niveau WASM avec des politiques de système de fichiers, de réseau et d'appels système à privilèges minimaux.
 #9.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que les quotas de ressources du bac à sable (CPU, mémoire, disque, sortie réseau) et les délais d'exécution sont appliqués et enregistrés.
 #9.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les fichiers binaires ou descripteurs des outils sont signés numériquement ; les signatures sont validées avant le chargement.
 #9.2.4    Niveau: 2    Rôle: V
 Vérifiez que les flux de télémétrie du bac à sable sont envoyés à un SIEM ; les anomalies (par exemple, les tentatives de connexions sortantes) déclenchent des alertes.
 #9.2.5    Niveau: 3    Rôle: V
 Vérifiez que les plugins à haut risque font l'objet d'une revue de sécurité et de tests de pénétration avant leur déploiement en production.
 #9.2.6    Niveau: 3    Rôle: D/V
 Vérifiez que les tentatives d’évasion du bac à sable sont automatiquement bloquées et que le plugin fautif est mis en quarantaine en attendant l’enquête.

---

### 9.3 Boucle autonome et limitation des coûts

Détecter et arrêter la récursion incontrôlée d’agent à agent et les explosions de coûts.

 #9.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les appels inter-agents incluent une limite de saut ou un TTL que le runtime décrémente et applique.
 #9.3.2    Niveau: 2    Rôle: D
 Vérifiez que les agents conservent un ID unique de graphe d’invocation pour détecter l’auto-invocation ou les schémas cycliques.
 #9.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les compteurs cumulés d’unités de calcul et de dépenses sont suivis par chaîne de requêtes ; le dépassement de la limite entraîne l’arrêt de la chaîne.
 #9.3.4    Niveau: 3    Rôle: V
 Vérifiez qu'une analyse formelle ou une vérification par modèle démontre l'absence de récursion non bornée dans les protocoles d'agent.
 #9.3.5    Niveau: 3    Rôle: D
 Vérifiez que les événements d'interruption de boucle génèrent des alertes et alimentent les indicateurs d'amélioration continue.

---

### 9.4 Protection contre les utilisations inadéquates au niveau du protocole

Canaux de communication sécurisés entre les agents et les systèmes externes pour prévenir la prise de contrôle ou la manipulation.

 #9.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les messages agent-à-outil et agent-à-agent sont authentifiés (par exemple, TLS mutuel ou JWT) et chiffrés de bout en bout.
 #9.4.2    Niveau: 1    Rôle: D
 Vérifiez que les schémas sont strictement validés ; les champs inconnus ou les messages mal formés sont rejetés.
 #9.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que les contrôles d'intégrité (MAC ou signatures numériques) couvrent l'intégralité de la charge utile du message, y compris les paramètres de l'outil.
 #9.4.4    Niveau: 2    Rôle: D
 Vérifiez que la protection contre la relecture (nonces ou fenêtres de timestamp) est appliquée au niveau du protocole.
 #9.4.5    Niveau: 3    Rôle: V
 Vérifiez que les implémentations des protocoles subissent un fuzzing et une analyse statique pour détecter les failles d’injection ou de désérialisation.

---

### 9.5 Identité de l'agent et preuve de falsification

Assurez-vous que les actions sont attribuables et que les modifications sont détectables.

 #9.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque instance d'agent possède une identité cryptographique unique (paire de clés ou crédential matériel racine).
 #9.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que toutes les actions des agents sont signées et horodatées ; les journaux incluent la signature pour la non-répudiation.
 #9.5.3    Niveau: 2    Rôle: V
 Vérifiez que les journaux à preuve de falsification sont stockés dans un support en mode ajout uniquement ou en mode écriture unique.
 #9.5.4    Niveau: 3    Rôle: D
 Vérifiez que les clés d'identité tournent selon un calendrier défini et en cas d'indicateurs de compromission.
 #9.5.5    Niveau: 3    Rôle: D/V
 Vérifiez que les tentatives d'usurpation d'identité ou de conflit de clé déclenchent une mise en quarantaine immédiate de l'agent affecté.

---

### 9.6 Réduction des risques par essaim multi-agent

Atténuer les risques liés au comportement collectif grâce à l'isolation et à la modélisation formelle de la sécurité.

 #9.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que les agents opérant dans différents domaines de sécurité s'exécutent dans des environnements d'exécution isolés ou des segments réseau séparés.
 #9.6.2    Niveau: 3    Rôle: V
 Vérifiez que les comportements en essaim sont modélisés et formellement vérifiés pour la vivacité et la sécurité avant le déploiement.
 #9.6.3    Niveau: 3    Rôle: D
 Vérifiez que les moniteurs d'exécution détectent les motifs émergents dangereux (par exemple, oscillations, interblocages) et initient une action corrective.

---

### 9.7 Authentification / Autorisation des utilisateurs et des outils

Implémentez des contrôles d'accès robustes pour chaque action déclenchée par un agent.

 #9.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les agents s'authentifient en tant que principaux de première classe auprès des systèmes en aval, sans jamais réutiliser les identifiants des utilisateurs finaux.
 #9.7.2    Niveau: 2    Rôle: D
 Vérifiez que les politiques d'autorisation granulaires restreignent les outils qu'un agent peut invoquer ainsi que les paramètres qu'il peut fournir.
 #9.7.3    Niveau: 2    Rôle: V
 Vérifiez que les contrôles de privilèges sont réévalués à chaque appel (autorisation continue), et pas seulement au début de la session.
 #9.7.4    Niveau: 3    Rôle: D
 Vérifiez que les privilèges délégués expirent automatiquement et nécessitent un nouveau consentement après un délai d'attente ou un changement de portée.

---

### 9.8 Sécurité de la communication agent à agent

Chiffrer et protéger l'intégrité de tous les messages inter-agents pour empêcher l'écoute clandestine et la falsification.

 #9.8.1    Niveau: 1    Rôle: D/V
 Vérifiez que l'authentification mutuelle et le chiffrement à secret parfait avancé (par exemple TLS 1.3) sont obligatoires pour les canaux des agents.
 #9.8.2    Niveau: 1    Rôle: D
 Vérifiez que l'intégrité et l'origine du message sont validées avant le traitement ; les échecs déclenchent des alertes et le rejet du message.
 #9.8.3    Niveau: 2    Rôle: D/V
 Vérifiez que les métadonnées de communication (horodatages, numéros de séquence) sont enregistrées pour soutenir la reconstruction judiciaire.
 #9.8.4    Niveau: 3    Rôle: V
 Vérifiez que la vérification formelle ou la model checking confirme que les machines à états du protocole ne peuvent pas être conduites à des états non sûrs.

---

### 9.9 Vérification de l'intention et application des contraintes

Valider que les actions de l'agent sont conformes à l'intention exprimée par l'utilisateur et aux contraintes du système.

 #9.9.1    Niveau: 1    Rôle: D
 Vérifiez que les solveurs de contraintes pré-exécution vérifient les actions proposées par rapport aux règles de sécurité et de politique codées en dur.
 #9.9.2    Niveau: 2    Rôle: D/V
 Vérifiez que les actions à fort impact (financières, destructrices, sensibles à la vie privée) nécessitent une confirmation explicite d'intention de la part de l'utilisateur initiateur.
 #9.9.3    Niveau: 2    Rôle: V
 Vérifiez que les contrôles de post-condition valident que les actions terminées ont atteint les effets prévus sans effets secondaires ; les écarts déclenchent une restauration.
 #9.9.4    Niveau: 3    Rôle: V
 Vérifiez que les méthodes formelles (par exemple, la vérification de modèle, la démonstration de théorèmes) ou les tests basés sur les propriétés démontrent que les plans des agents respectent toutes les contraintes déclarées.
 #9.9.5    Niveau: 3    Rôle: D
 Vérifiez que les incidents de non-correspondance d'intention ou de violation de contrainte alimentent les cycles d'amélioration continue et le partage du renseignement sur les menaces.

---

### 9.10 Sécurité de la stratégie de raisonnement de l'agent

Sélection et exécution sécurisées de différentes stratégies de raisonnement, y compris les approches ReAct, Chain-of-Thought et Tree-of-Thoughts.

 #9.10.1    Niveau: 1    Rôle: D/V
 Vérifiez que la sélection de la stratégie de raisonnement utilise des critères déterministes (complexité de l'entrée, type de tâche, contexte de sécurité) et que des entrées identiques produisent des sélections de stratégie identiques dans un même contexte de sécurité.
 #9.10.2    Niveau: 1    Rôle: D/V
 Vérifiez que chaque stratégie de raisonnement (ReAct, chaîne de pensée, arbre de pensées) dispose d'une validation d'entrée dédiée, d'une assainissement des sorties et de limites de temps d'exécution spécifiques à son approche cognitive.
 #9.10.3    Niveau: 2    Rôle: D/V
 Vérifiez que les transitions de stratégie de raisonnement sont enregistrées avec un contexte complet incluant les caractéristiques de l'entrée, les valeurs des critères de sélection et les métadonnées d'exécution pour la reconstitution de la piste d'audit.
 #9.10.4    Niveau: 2    Rôle: D/V
 Vérifiez que le raisonnement Tree-of-Thoughts inclut des mécanismes d'élagage des branches qui arrêtent l'exploration lorsqu'une violation de politique, une limite de ressources ou une frontière de sécurité est détectée.
 #9.10.5    Niveau: 2    Rôle: D/V
 Vérifiez que les cycles ReAct (Reason-Act-Observe) incluent des points de contrôle de validation à chaque phase : vérification des étapes de raisonnement, autorisation des actions, et assainissement des observations avant de continuer.
 #9.10.6    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques de performance de la stratégie de raisonnement (temps d'exécution, utilisation des ressources, qualité de sortie) sont surveillées avec des alertes automatisées lorsque les métriques s'écartent des seuils configurés.
 #9.10.7    Niveau: 3    Rôle: D/V
 Vérifiez que les approches de raisonnement hybride combinant plusieurs stratégies maintiennent la validation des entrées et les contraintes de sortie de toutes les stratégies constitutives sans contourner aucun contrôle de sécurité.
 #9.10.8    Niveau: 3    Rôle: D/V
 Vérifiez que les tests de sécurité des stratégies de raisonnement incluent le fuzzing avec des entrées malformées, des invites adverses conçues pour forcer le changement de stratégie, et des tests des conditions limites pour chaque approche cognitive.

---

### 9.11 Gestion de l'État du Cycle de Vie de l'Agent et Sécurité

Initialisation sécurisée des agents, transitions d’état et terminaison avec des pistes d’audit cryptographiques et des procédures de récupération définies.

 #9.11.1    Niveau: 1    Rôle: D/V
 Vérifiez que l'initialisation de l'agent inclut l'établissement d'une identité cryptographique avec des informations d'identification sécurisées par le matériel et des journaux d'audit de démarrage immuables contenant l'ID de l'agent, l'horodatage, le hachage de configuration et les paramètres d'initialisation.
 #9.11.2    Niveau: 2    Rôle: D/V
 Vérifiez que les transitions d’état de l’agent sont signées cryptographiquement, horodatées, et enregistrées avec un contexte complet incluant les événements déclencheurs, le hachage de l’état précédent, le hachage du nouvel état, ainsi que les validations de sécurité effectuées.
 #9.11.3    Niveau: 2    Rôle: D/V
 Vérifiez que les procédures d'arrêt de l'agent incluent l'effacement sécurisé de la mémoire à l'aide d'une suppression cryptographique ou d'une réécriture multiple, la révocation des identifiants avec notification à l'autorité de certification, et la génération de certificats de terminaison inviolables.
 #9.11.4    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes de récupération des agents valident l’intégrité de l’état à l’aide de sommes de contrôle cryptographiques (SHA-256 minimum) et reviennent à des états connus comme fiables en cas de détection de corruption, avec des alertes automatisées et des exigences d’approbation manuelle.
 #9.11.5    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes de persistance des agents chiffrent les données d'état sensibles avec des clés AES-256 spécifiques à chaque agent et mettent en œuvre une rotation sécurisée des clés selon des calendriers configurables (maximum 90 jours) avec un déploiement sans interruption.

---

### 9.12 Cadre de sécurité pour l'intégration des outils

Contrôles de sécurité pour le chargement dynamique des outils, leur exécution et la validation des résultats avec des processus définis d'évaluation des risques et d'approbation.

 #9.12.1    Niveau: 1    Rôle: D/V
 Vérifiez que les descripteurs d’outils incluent des métadonnées de sécurité spécifiant les privilèges requis (lecture/écriture/exécution), les niveaux de risque (faible/moyen/élevé), les limites de ressources (CPU, mémoire, réseau) et les exigences de validation documentées dans les manifestes d’outils.
 #9.12.2    Niveau: 1    Rôle: D/V
 Vérifiez que les résultats d'exécution des outils sont validés par rapport aux schémas attendus (JSON Schema, XML Schema) et aux politiques de sécurité (assainissement des sorties, classification des données) avant intégration, avec des limites de délai d'attente et des procédures de gestion des erreurs.
 #9.12.3    Niveau: 2    Rôle: D/V
 Vérifiez que les journaux d'interaction des outils incluent un contexte de sécurité détaillé, comprenant l'utilisation des privilèges, les schémas d'accès aux données, le temps d'exécution, la consommation des ressources et les codes de retour, avec une journalisation structurée pour l'intégration SIEM.
 #9.12.4    Niveau: 2    Rôle: D/V
 Vérifiez que les mécanismes de chargement dynamique des outils valident les signatures numériques en utilisant l'infrastructure PKI et mettent en œuvre des protocoles de chargement sécurisés avec une isolation en sandbox et une vérification des permissions avant l'exécution.
 #9.12.5    Niveau: 3    Rôle: D/V
 Vérifiez que les évaluations de sécurité des outils sont automatiquement déclenchées pour les nouvelles versions avec des étapes d'approbation obligatoires incluant l'analyse statique, les tests dynamiques et la revue par l'équipe de sécurité, avec des critères d'approbation documentés et des exigences de SLA.

---

#### Références

MITRE ATLAS tactics ML09
Circuit-breaker research for AI agents — Zou et al., 2024
Trend Micro analysis of sandbox escapes in AI agents — Park, 2025
Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025
Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025
Rapid7 fundamentals on spoofing attack prevention — 2024
Imperial College verification of swarm systems — Lomuscio et al.
NIST AI Risk Management Framework 1.0, 2023
WIRED security briefing on encryption best practices, 2024
OWASP Top 10 for LLM Applications, 2025
Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS
[How Is LLM Reasoning Distracted by Irrelevant Context?
An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
Large Language Model Sentinel: LLM Agent for Adversarial Purification
Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents

## 10 Robustesse Adversariale et Défense de la Confidentialité

### Objectif de contrôle

Assurez-vous que les modèles d'IA restent fiables, respectueux de la vie privée et résistants aux abus lorsqu'ils sont confrontés à des attaques d'évasion, d'inférence, d'extraction ou d'empoisonnement.

---

### 10.1 Alignement et sécurité du modèle

Se prémunir contre les résultats nuisibles ou contraires aux politiques.

 #10.1.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'une suite de tests d'alignement (prompts de red-team, sondes de jailbreak, contenu interdit) est gérée en contrôle de version et exécutée à chaque version du modèle.
 #10.1.2    Niveau: 1    Rôle: D
 Vérifiez que les garde-fous de refus et de complétion sécurisée sont appliqués.
 #10.1.3    Niveau: 2    Rôle: D/V
 Vérifiez qu'un évaluateur automatisé mesure le taux de contenu nuisible et signale les régressions au-delà d'un seuil défini.
 #10.1.4    Niveau: 2    Rôle: D
 Vérifiez que la formation anti-jailbreak est documentée et reproductible.
 #10.1.5    Niveau: 3    Rôle: V
 Vérifiez que les preuves formelles de conformité aux politiques ou la surveillance certifiée couvrent les domaines critiques.

---

### 10.2 Renforcement contre les exemples adverses

Augmenter la résilience face aux entrées manipulées. L'entraînement adversarial robuste et le scoring de référence sont les meilleures pratiques actuelles.

 #10.2.1    Niveau: 1    Rôle: D
 Vérifiez que les dépôts du projet incluent des configurations d'entraînement adversarial avec des graines reproductibles.
 #10.2.2    Niveau: 2    Rôle: D/V
 Vérifiez que la détection des exemples adverses génère des alertes de blocage dans les pipelines de production.
 #10.2.4    Niveau: 3    Rôle: V
 Vérifiez que les preuves de robustesse certifiée ou les certificats de borne d'intervalle couvrent au moins les principales classes critiques.
 #10.2.5    Niveau: 3    Rôle: V
 Vérifiez que les tests de régression utilisent des attaques adaptatives pour confirmer l'absence de perte de robustesse mesurable.

---

### 10.3 Atténuation de l'inférence d'appartenance

Limiter la capacité à décider si un enregistrement faisait partie des données d'entraînement. La confidentialité différentielle et le masquage des scores de confiance demeurent les défenses connues les plus efficaces.

 #10.3.1    Niveau: 1    Rôle: D
 Vérifiez que la régularisation de l'entropie par requête ou la mise à l’échelle de la température réduit les prédictions trop confiantes.
 #10.3.2    Niveau: 2    Rôle: D
 Vérifiez que la formation utilise une optimisation différentiellement privée avec une borne ε pour les ensembles de données sensibles.
 #10.3.3    Niveau: 2    Rôle: V
 Vérifiez que les simulations d'attaque (modèle fantôme ou boîte noire) affichent une AUC d'attaque ≤ 0,60 sur les données non utilisées pour l'entraînement.

---

### 10.4 Résistance à l'inversion de modèle

Empêcher la reconstruction des attributs privés. Les enquêtes récentes soulignent la troncature des sorties et les garanties de DP comme des défenses pratiques.

 #10.4.1    Niveau: 1    Rôle: D
 Vérifiez que les attributs sensibles ne sont jamais directement affichés ; si nécessaire, utilisez des catégories ou des transformations unidirectionnelles.
 #10.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les limites de taux de requête régulent les requêtes adaptatives répétées provenant du même principal.
 #10.4.3    Niveau: 2    Rôle: D
 Vérifiez que le modèle est entraîné avec un bruit préservant la confidentialité.

---

### 10.5 Défense contre l'extraction de modèle

Détecter et dissuader la duplication non autorisée. Le filigrane et l'analyse des motifs de requête sont recommandés.

 #10.5.1    Niveau: 1    Rôle: D
 Vérifiez que les passerelles d'inférence appliquent des limites de taux globales et par clé API ajustées au seuil de mémorisation du modèle.
 #10.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les statistiques d'entropie de requête et de pluralité d'entrée alimentent un détecteur d'extraction automatisé.
 #10.5.3    Niveau: 2    Rôle: V
 Vérifiez que les filigranes fragiles ou probabilistes peuvent être prouvés avec p < 0,01 en ≤ 1 000 requêtes contre un clone suspecté.
 #10.5.4    Niveau: 3    Rôle: D
 Vérifiez que les clés de tatouage numérique et les ensembles de déclenchement sont stockés dans un module de sécurité matériel et sont renouvelés chaque année.
 #10.5.5    Niveau: 3    Rôle: V
 Vérifiez que les événements d'alerte d'extraction incluent les requêtes incriminées et sont intégrés aux playbooks de réponse aux incidents.

---

### 10.6 Détection de données empoisonnées en temps d'inférence

Identifier et neutraliser les entrées avec porte dérobée ou empoisonnées.

 #10.6.1    Niveau: 1    Rôle: D
 Vérifiez que les entrées passent par un détecteur d’anomalies (par exemple, STRIP, scoring de cohérence) avant l’inférence du modèle.
 #10.6.2    Niveau: 1    Rôle: V
 Vérifiez que les seuils du détecteur sont ajustés sur des ensembles de validation propres/empoisonnés afin d'atteindre moins de 5 % de faux positifs.
 #10.6.3    Niveau: 2    Rôle: D
 Vérifiez que les entrées signalées comme empoisonnées déclenchent le blocage doux et les processus de révision humaine.
 #10.6.4    Niveau: 2    Rôle: V
 Vérifiez que les détecteurs sont soumis à un stress-test avec des attaques de porte dérobée adaptatives et sans déclencheur.
 #10.6.5    Niveau: 3    Rôle: D
 Vérifiez que les métriques d'efficacité de détection sont enregistrées et réévaluées périodiquement avec des renseignements sur les menaces actualisés.

---

### 10.7 Adaptation dynamique de la politique de sécurité

Mises à jour en temps réel des politiques de sécurité basées sur le renseignement sur les menaces et l'analyse comportementale.

 #10.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les politiques de sécurité peuvent être mises à jour de manière dynamique sans redémarrage de l'agent tout en maintenant l'intégrité de la version de la politique.
 #10.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que les mises à jour des politiques sont signées cryptographiquement par le personnel de sécurité autorisé et validées avant leur application.
 #10.7.3    Niveau: 2    Rôle: D/V
 Vérifiez que les modifications dynamiques des politiques sont enregistrées avec des pistes d'audit complètes, comprenant la justification, les chaînes d'approbation et les procédures de restauration.
 #10.7.4    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes de sécurité adaptatifs ajustent la sensibilité de la détection des menaces en fonction du contexte de risque et des modèles comportementaux.
 #10.7.5    Niveau: 3    Rôle: D/V
 Vérifiez que les décisions d'adaptation de la politique sont explicables et incluent des pistes de preuves pour la revue par l'équipe de sécurité.

---

### 10.8 Analyse de sécurité basée sur la réflexion

Validation de la sécurité par auto-réflexion de l'agent et analyse métacognitive.

 #10.8.1    Niveau: 1    Rôle: D/V
 Vérifiez que les mécanismes de réflexion des agents incluent une auto-évaluation axée sur la sécurité des décisions et des actions.
 #10.8.2    Niveau: 2    Rôle: D/V
 Vérifiez que les sorties de réflexion sont validées afin d'éviter la manipulation des mécanismes d'auto-évaluation par des entrées adverses.
 #10.8.3    Niveau: 2    Rôle: D/V
 Vérifiez que l'analyse de sécurité métacognitive identifie les biais potentiels, la manipulation ou la compromission dans les processus de raisonnement des agents.
 #10.8.4    Niveau: 3    Rôle: D/V
 Vérifiez que les alertes de sécurité basées sur la réflexion déclenchent une surveillance renforcée et des flux de travail potentiels d'intervention humaine.
 #10.8.5    Niveau: 3    Rôle: D/V
 Vérifiez que l'apprentissage continu à partir des réflexions sur la sécurité améliore la détection des menaces sans dégrader la fonctionnalité légitime.

---

### 10.9 Sécurité de l'évolution et de l'auto-amélioration

Contrôles de sécurité pour les systèmes agents capables d’auto-modification et d’évolution.

 #10.9.1    Niveau: 1    Rôle: D/V
 Vérifiez que les capacités d'auto-modification sont limitées aux zones sûres désignées avec des frontières de vérification formelle.
 #10.9.2    Niveau: 2    Rôle: D/V
 Vérifiez que les propositions d'évolution font l'objet d'une évaluation de l'impact sur la sécurité avant leur mise en œuvre.
 #10.9.3    Niveau: 2    Rôle: D/V
 Vérifiez que les mécanismes d'amélioration autonome incluent des capacités de retour en arrière avec vérification d'intégrité.
 #10.9.4    Niveau: 3    Rôle: D/V
 Vérifiez que la sécurité de la méta-apprentissage empêche la manipulation adversaire des algorithmes d'amélioration.
 #10.9.5    Niveau: 3    Rôle: D/V
 Vérifiez que l'amélioration récursive autonome est limitée par des contraintes formelles de sécurité avec des preuves mathématiques de convergence.

---

#### Références

MITRE ATLAS adversary tactics for ML
NIST AI Risk Management Framework 1.0, 2023
OWASP Top 10 for LLM Applications, 2025
Adversarial Training: A Survey — Zhao et al., 2024
RobustBench adversarial-robustness benchmark
Membership-Inference & Model-Inversion Risk Survey, 2025
PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023
Model-Inversion Attacks & Defenses Survey — AI Review, 2025
Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024
Fragile Model Watermarking Survey — 2025
Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025
BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024

## 11 Protection de la vie privée et gestion des données personnelles

### Objectif de contrôle

Maintenir des garanties strictes en matière de confidentialité tout au long du cycle de vie de l'IA—collecte, entraînement, inférence et réponse aux incidents—afin que les données personnelles ne soient traitées qu'avec un consentement clair, une portée minimale nécessaire, une suppression vérifiable et des garanties formelles de confidentialité.

---

### 11.1 Anonymisation et minimisation des données

 #11.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que les identifiants directs et quasi-identifiants sont supprimés ou hachés.
 #11.1.2    Niveau: 2    Rôle: D/V
 Vérifiez que les audits automatisés mesurent la k-anonymat/l-diversité et alertent lorsque les seuils descendent en dessous de la politique.
 #11.1.3    Niveau: 2    Rôle: V
 Vérifiez que les rapports d'importance des caractéristiques du modèle prouvent qu'il n'y a pas de fuite d'identifiant au-delà de ε = 0,01 d'information mutuelle.
 #11.1.4    Niveau: 3    Rôle: V
 Vérifiez que les preuves formelles ou la certification par données synthétiques démontrent un risque de ré-identification ≤ 0,05 même en cas d’attaques par rapprochement.

---

### 11.2 Droit à l’oubli et application de la suppression

 #11.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les demandes de suppression des données personnelles se propagent aux ensembles de données bruts, aux points de contrôle, aux embeddings, aux journaux et aux sauvegardes dans le cadre des accords de niveau de service de moins de 30 jours.
 #11.2.2    Niveau: 2    Rôle: D
 Vérifiez que les routines de « machine-unlearning » ré-entraînent physiquement ou approximativement suppriment les données en utilisant des algorithmes de désapprentissage certifiés.
 #11.2.3    Niveau: 2    Rôle: V
 Vérifiez que l’évaluation par modèle d’ombre prouve que les enregistrements oubliés influencent moins de 1 % des résultats après l’oubli.
 #11.2.4    Niveau: 3    Rôle: V
 Vérifiez que les événements de suppression sont consignés de manière immuable et auditable pour les régulateurs.

---

### 11.3 Mesures de protection de la confidentialité différentielle

 #11.3.1    Niveau: 2    Rôle: D/V
 Vérifiez que les tableaux de bord de comptabilisation de la perte de confidentialité alertent lorsque le cumulatif ε dépasse les seuils de la politique.
 #11.3.2    Niveau: 2    Rôle: V
 Vérifiez que les audits de confidentialité en boîte noire estiment ε̂ à moins de 10 % de la valeur déclarée.
 #11.3.3    Niveau: 3    Rôle: V
 Vérifiez que les preuves formelles couvrent toutes les fines optimisations et les embeddings post-entraînement.

---

### 11.4 Limitation de l'objectif et protection contre le débordement de périmètre

 #11.4.1    Niveau: 1    Rôle: D
 Vérifiez que chaque ensemble de données et point de contrôle de modèle porte une étiquette de but lisible par machine conforme au consentement initial.
 #11.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les moniteurs d'exécution détectent les requêtes incompatibles avec l'objectif déclaré et déclenchent un refus soft.
 #11.4.3    Niveau: 3    Rôle: D
 Vérifiez que les contrôles de politique sous forme de code bloquent le redéploiement des modèles vers de nouveaux domaines sans examen DPIA.
 #11.4.4    Niveau: 3    Rôle: V
 Vérifiez que les preuves formelles de traçabilité démontrent que chaque cycle de vie des données personnelles reste dans le périmètre consenti.

---

### 11.5 Gestion du consentement et suivi basé sur une base légale

 #11.5.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'une plateforme de gestion du consentement (CMP) enregistre le statut d'opt-in, la finalité et la période de conservation par sujet de données.
 #11.5.2    Niveau: 2    Rôle: D
 Vérifiez que les API exposent les jetons de consentement ; les modèles doivent valider la portée du jeton avant l'inférence.
 #11.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que le consentement refusé ou retiré interrompt les chaînes de traitement dans un délai de 24 heures.

---

### 11.6 Apprentissage Fédéré avec Contrôles de Confidentialité

 #11.6.1    Niveau: 1    Rôle: D
 Vérifiez que les mises à jour des clients utilisent l’ajout de bruit de confidentialité différentielle locale avant l’agrégation.
 #11.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que les métriques d'entraînement sont privées différentielles et ne révèlent jamais la perte d'un seul client.
 #11.6.3    Niveau: 2    Rôle: V
 Vérifiez que l'agrégation résistante au empoisonnement (par exemple, Krum/Moyenne Trimmée) est activée.
 #11.6.4    Niveau: 3    Rôle: V
 Vérifiez que les preuves formelles démontrent un budget global ε avec une perte d'utilité inférieure à 5.

---

#### Références

GDPR & AI Compliance Best Practices
EU Parliament Study on GDPR & AI, 2020
ISO 31700-1:2023 — Privacy by Design for Consumer Products
NIST Privacy Framework 1.1 (2025 Draft)
Machine Unlearning: Right-to-Be-Forgotten Techniques
A Survey of Machine Unlearning, 2024
Auditing DP-SGD — ArXiv 2024
DP-SGD Explained — PyTorch Blog
Purpose-Limitation for AI — IJLIT 2025
Data-Protection Considerations for AI — URM Consulting
Top Consent-Management Platforms, 2025
Secure Aggregation in DP Federated Learning — ArXiv 2024

## C12 Surveillance, journalisation et détection des anomalies

### Objectif de contrôle

Cette section fournit les exigences pour offrir une visibilité en temps réel et médico-légale sur ce que le modèle et les autres composants d’IA voient, font et retournent, afin que les menaces puissent être détectées, triées et dont on puisse tirer des enseignements.

### C12.1 Journalisation des requêtes et des réponses

 #12.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que toutes les invites utilisateur et les réponses du modèle sont enregistrées avec des métadonnées appropriées (par exemple, horodatage, ID utilisateur, ID de session, version du modèle).
 #12.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les journaux sont stockés dans des dépôts sécurisés, avec un contrôle d’accès approprié, des politiques de rétention adéquates et des procédures de sauvegarde.
 #12.1.3    Niveau: 1    Rôle: D/V
 Vérifiez que les systèmes de stockage des journaux mettent en œuvre le chiffrement au repos et en transit pour protéger les informations sensibles contenues dans les journaux.
 #12.1.4    Niveau: 1    Rôle: D/V
 Vérifiez que les données sensibles dans les invites et les résultats sont automatiquement supprimées ou masquées avant la journalisation, avec des règles de suppression configurables pour les informations personnelles identifiables (PII), les identifiants et les informations propriétaires.
 #12.1.5    Niveau: 2    Rôle: D/V
 Vérifiez que les décisions de politique et les actions de filtrage de sécurité sont enregistrées avec suffisamment de détails pour permettre l'audit et le débogage des systèmes de modération de contenu.
 #12.1.6    Niveau: 2    Rôle: D/V
 Vérifiez que l'intégrité des journaux est protégée par exemple par des signatures cryptographiques ou un stockage en écriture seule.

---

### C12.2 Détection des abus et alertes

 #12.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que le système détecte et alerte sur les schémas de jailbreak connus, les tentatives d'injection de prompt et les entrées adversariales en utilisant une détection basée sur des signatures.
 #12.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que le système s'intègre aux plateformes existantes de Gestion des Informations et des Événements de Sécurité (SIEM) en utilisant des formats de journalisation et des protocoles standard.
 #12.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les événements de sécurité enrichis incluent un contexte spécifique à l’IA tel que les identifiants de modèle, les scores de confiance et les décisions des filtres de sécurité.
 #12.2.4    Niveau: 2    Rôle: D/V
 Vérifiez que la détection des anomalies comportementales identifie les schémas de conversation inhabituels, les tentatives de réessai excessives ou les comportements de sondage systématiques.
 #12.2.5    Niveau: 2    Rôle: D/V
 Vérifiez que les mécanismes d'alerte en temps réel notifient les équipes de sécurité lorsque des violations potentielles de la politique ou des tentatives d'attaque sont détectées.
 #12.2.6    Niveau: 2    Rôle: D/V
 Vérifiez que des règles personnalisées sont incluses pour détecter les modèles de menaces spécifiques à l'IA, y compris les tentatives coordonnées de jailbreak, les campagnes d'injection de prompts et les attaques d'extraction de modèles.
 #12.2.7    Niveau: 3    Rôle: D/V
 Vérifiez que les flux de travail automatisés de réponse aux incidents peuvent isoler les modèles compromis, bloquer les utilisateurs malveillants et escalader les événements de sécurité critiques.

---

### C12.3 Détection de la dérive du modèle

 #12.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que le système suit les métriques de performance de base telles que la précision, les scores de confiance, la latence et les taux d'erreur à travers les versions du modèle et les périodes temporelles.
 #12.3.2    Niveau: 2    Rôle: D/V
 Vérifiez que les alertes automatisées se déclenchent lorsque les indicateurs de performance dépassent les seuils de dégradation prédéfinis ou s’écartent significativement des références.
 #12.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les systèmes de détection d'hallucinations identifient et signalent les cas où les sorties du modèle contiennent des informations factuellement incorrectes, incohérentes ou fabriquées.

---

### C12.4 Télémétrie de performance et de comportement

 #12.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que les métriques opérationnelles, y compris la latence des requêtes, la consommation de jetons, l'utilisation de la mémoire et le débit, sont collectées et surveillées en continu.
 #12.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les taux de réussite et d'échec sont suivis avec une catégorisation des types d'erreurs et de leurs causes profondes.
 #12.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que la surveillance de l'utilisation des ressources inclut l'utilisation du GPU/CPU, la consommation de mémoire et les besoins en stockage, avec des alertes en cas de dépassement des seuils.

---

### C12.5 Planification et exécution de la réponse aux incidents d’IA

 #12.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les plans d'intervention en cas d'incident traitent spécifiquement les événements de sécurité liés à l'IA, y compris la compromission des modèles, l'empoisonnement des données et les attaques adverses.
 #12.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les équipes d'intervention en cas d'incident disposent d'outils médico-légaux spécifiques à l'IA et de l'expertise nécessaire pour enquêter sur le comportement des modèles et les vecteurs d'attaque.
 #12.5.3    Niveau: 3    Rôle: D/V
 Vérifiez que l'analyse post-incident inclut des considérations de reformation du modèle, des mises à jour des filtres de sécurité et l'intégration des leçons apprises dans les contrôles de sécurité.

---

### C12.6 Détection de la dégradation des performances de l'IA

Surveiller et détecter la dégradation des performances et de la qualité du modèle d'IA au fil du temps.

 #12.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que la précision, la justesse, le rappel et les scores F1 du modèle sont continuellement surveillés et comparés aux seuils de référence.
 #12.6.2    Niveau: 1    Rôle: D/V
 Vérifiez que la détection de dérive des données surveille les changements dans la distribution des entrées pouvant affecter les performances du modèle.
 #12.6.3    Niveau: 2    Rôle: D/V
 Vérifiez que la détection de dérive de concept identifie les changements dans la relation entre les entrées et les sorties attendues.
 #12.6.4    Niveau: 2    Rôle: D/V
 Vérifiez que la dégradation des performances déclenche des alertes automatisées et initie des flux de travail de réentraînement ou de remplacement du modèle.
 #12.6.5    Niveau: 3    Rôle: V
 Vérifiez que l'analyse des causes profondes de la dégradation corrèle les baisses de performance avec les changements de données, les problèmes d'infrastructure ou les facteurs externes.

---

### C12.7 Visualisation du DAG et sécurité du flux de travail

Protéger les systèmes de visualisation des flux de travail contre les fuites d'informations et les attaques de manipulation.

 #12.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les données de visualisation du DAG sont nettoyées pour supprimer les informations sensibles avant le stockage ou la transmission.
 #12.7.2    Niveau: 1    Rôle: D/V
 Vérifiez que les contrôles d’accès à la visualisation du flux de travail garantissent que seuls les utilisateurs autorisés peuvent voir les chemins de décision des agents et les traces de raisonnement.
 #12.7.3    Niveau: 2    Rôle: D/V
 Vérifiez que l'intégrité des données DAG est protégée par des signatures cryptographiques et des mécanismes de stockage inviolables.
 #12.7.4    Niveau: 2    Rôle: D/V
 Vérifiez que les systèmes de visualisation de flux de travail mettent en œuvre une validation des entrées pour prévenir les attaques par injection via des données de nœuds ou d’arêtes fabriquées.
 #12.7.5    Niveau: 3    Rôle: D/V
 Vérifiez que les mises à jour en temps réel des DAG sont limitées en débit et validées afin de prévenir les attaques par déni de service sur les systèmes de visualisation.

---

### C12.8 Surveillance proactive du comportement en matière de sécurité

Détection et prévention des menaces de sécurité grâce à une analyse proactive du comportement des agents.

 #12.8.1    Niveau: 1    Rôle: D/V
 Vérifiez que les comportements proactifs des agents sont validés en matière de sécurité avant leur exécution, avec une intégration de l’évaluation des risques.
 #12.8.2    Niveau: 2    Rôle: D/V
 Vérifiez que les déclencheurs d'initiative autonome incluent l'évaluation du contexte de sécurité et l'évaluation du paysage des menaces.
 #12.8.3    Niveau: 2    Rôle: D/V
 Vérifiez que les modèles de comportement proactif sont analysés pour leurs implications potentielles en matière de sécurité et leurs conséquences inattendues.
 #12.8.4    Niveau: 3    Rôle: D/V
 Vérifiez que les actions proactives critiques pour la sécurité nécessitent des chaînes d'approbation explicites avec des pistes d'audit.
 #12.8.5    Niveau: 3    Rôle: D/V
 Vérifiez que la détection d'anomalies comportementales identifie les déviations dans les schémas des agents proactifs pouvant indiquer une compromission.

---

### Références

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6

## C13 Supervision Humaine, Responsabilité et Gouvernance

### Objectif de contrôle

Ce chapitre fournit des exigences pour maintenir une supervision humaine et des chaînes de responsabilité claires dans les systèmes d'IA, garantissant l'explicabilité, la transparence et une gestion éthique tout au long du cycle de vie de l'IA.

---

### C13.1 Mécanismes de coupure d'urgence et d'override

Fournir des chemins d'arrêt ou de retour en arrière lorsque l'on observe un comportement dangereux du système d'IA.

 #13.1.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'un mécanisme d'arrêt manuel existe pour interrompre immédiatement l'inférence et les sorties du modèle d'IA.
 #13.1.2    Niveau: 1    Rôle: D
 Vérifiez que les contrôles de remplacement sont accessibles uniquement au personnel autorisé.
 #13.1.3    Niveau: 3    Rôle: D/V
 Vérifiez que les procédures de retour arrière peuvent revenir aux versions précédentes du modèle ou aux opérations en mode sécurisé.
 #13.1.4    Niveau: 3    Rôle: V
 Vérifiez que les mécanismes de remplacement sont testés régulièrement.

---

### C13.2 Points de contrôle décisionnels avec intervention humaine

Exiger des approbations humaines lorsque les enjeux dépassent les seuils de risque prédéfinis.

 #13.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les décisions d'IA à haut risque nécessitent une approbation humaine explicite avant leur exécution.
 #13.2.2    Niveau: 1    Rôle: D
 Vérifiez que les seuils de risque sont clairement définis et déclenchent automatiquement les flux de travail de révision humaine.
 #13.2.3    Niveau: 2    Rôle: D
 Vérifiez que les décisions sensibles au facteur temps disposent de procédures de secours lorsque l'approbation humaine ne peut être obtenue dans les délais requis.
 #13.2.4    Niveau: 3    Rôle: D/V
 Vérifiez que les procédures d'escalade définissent des niveaux d'autorité clairs pour les différents types de décisions ou catégories de risques, le cas échéant.

---

### C13.3 Chaîne de Responsabilité et Auditabilité

Enregistrer les actions de l’opérateur et les décisions du modèle.

 #13.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que toutes les décisions du système d'IA et les interventions humaines sont enregistrées avec des horodatages, les identités des utilisateurs et la justification des décisions.
 #13.3.2    Niveau: 2    Rôle: D
 Vérifiez que les journaux d'audit ne peuvent pas être falsifiés et qu'ils comprennent des mécanismes de vérification d'intégrité.

---

### C13.4 Techniques d’IA explicable

Importance des caractéristiques de surface, contre-factuels et explications locales.

 #13.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que les systèmes d'IA fournissent des explications de base pour leurs décisions dans un format lisible par l'homme.
 #13.4.2    Niveau: 2    Rôle: V
 Vérifiez que la qualité de l'explication est validée par des études d'évaluation humaine et des métriques.
 #13.4.3    Niveau: 3    Rôle: D/V
 Vérifiez que les scores d’importance des caractéristiques ou les méthodes d’attribution (SHAP, LIME, etc.) sont disponibles pour les décisions critiques.
 #13.4.4    Niveau: 3    Rôle: V
 Vérifiez que les explications contrefactuelles montrent comment les entrées pourraient être modifiées pour changer les résultats, si cela est applicable au cas d'utilisation et au domaine.

---

### Cartes de Modèle C13.5 et Divulgations d'Utilisation

Maintenir les fiches de modèle pour l'utilisation prévue, les métriques de performance et les considérations éthiques.

 #13.5.1    Niveau: 1    Rôle: D
 Vérifiez que les fiches de modèle documentent les cas d'utilisation prévus, les limitations et les modes de défaillance connus.
 #13.5.2    Niveau: 1    Rôle: D/V
 Vérifiez que les métriques de performance pour les différents cas d'utilisation applicables sont divulguées.
 #13.5.3    Niveau: 2    Rôle: D
 Vérifiez que les considérations éthiques, les évaluations des biais, les évaluations de l'équité, les caractéristiques des données d'entraînement et les limites connues des données d'entraînement sont documentées et mises à jour régulièrement.
 #13.5.4    Niveau: 2    Rôle: D/V
 Vérifiez que les fiches de modèles sont contrôlées en version et maintenues tout au long du cycle de vie du modèle avec un suivi des modifications.

---

### C13.6 Quantification de l'incertitude

Propager les scores de confiance ou les mesures d'entropie dans les réponses.

 #13.6.1    Niveau: 1    Rôle: D
 Vérifiez que les systèmes d'IA fournissent des scores de confiance ou des mesures d'incertitude avec leurs résultats.
 #13.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que les seuils d'incertitude déclenchent une revue humaine supplémentaire ou des voies de décision alternatives.
 #13.6.3    Niveau: 2    Rôle: V
 Vérifiez que les méthodes de quantification de l'incertitude sont calibrées et validées par rapport aux données de référence.
 #13.6.4    Niveau: 3    Rôle: D/V
 Vérifiez que la propagation de l'incertitude est maintenue tout au long des flux de travail d'IA à plusieurs étapes.

---

### C13.7 Rapports de transparence destinés aux utilisateurs

Fournir des divulgations périodiques sur les incidents, la dérive et l'utilisation des données.

 #13.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les politiques d'utilisation des données et les pratiques de gestion du consentement des utilisateurs sont clairement communiquées aux parties prenantes.
 #13.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que des évaluations d'impact de l'IA sont réalisées et que les résultats sont inclus dans les rapports.
 #13.7.3    Niveau: 2    Rôle: D/V
 Vérifiez que les rapports de transparence publiés régulièrement divulguent les incidents liés à l'IA et les métriques opérationnelles avec un niveau de détail raisonnable.

#### Références

EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
ISO/IEC 42001:2023 — AI Management Systems Requirements
NIST AI Risk Management Framework 1.0
NIST SP 800-53 Revision 5 — Security and Privacy Controls
A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)
Model Cards for Model Reporting (Mitchell et al., 2018)
Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)
ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods
IEEE 7001-2021 — Transparency of Autonomous Systems
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Annexe A : Glossaire

Ce glossaire complet fournit des définitions des termes clés en IA, ML et sécurité utilisés tout au long de l'AISVS afin d'assurer la clarté et une compréhension commune.

Exemple d’attaque antagoniste : une entrée délibérément conçue pour amener un modèle d’IA à faire une erreur, souvent en ajoutant des perturbations subtiles imperceptibles pour les humains.
​
Robustesse adversaire – La robustesse adversaire en IA fait référence à la capacité d'un modèle à maintenir sa performance et à résister à être trompé ou manipulé par des entrées malveillantes intentionnellement conçues pour provoquer des erreurs.
​
Agent – Les agents IA sont des systèmes logiciels qui utilisent l'IA pour poursuivre des objectifs et accomplir des tâches au nom des utilisateurs. Ils démontrent des capacités de raisonnement, de planification et de mémoire, et possèdent un certain niveau d'autonomie pour prendre des décisions, apprendre et s'adapter.
​
IA agentive : systèmes d’IA capables de fonctionner avec un certain degré d’autonomie pour atteindre des objectifs, prenant souvent des décisions et exécutant des actions sans intervention humaine directe.
​
Contrôle d'accès basé sur les attributs (ABAC) : un paradigme de contrôle d'accès où les décisions d'autorisation sont basées sur les attributs de l'utilisateur, de la ressource, de l'action et de l'environnement, évalués au moment de la requête.
​
Attaque par porte dérobée : un type d'attaque par empoisonnement de données où le modèle est entraîné à répondre d'une manière spécifique à certains déclencheurs tout en se comportant normalement autrement.
​
Biais : erreurs systématiques dans les résultats des modèles d'IA qui peuvent entraîner des résultats injustes ou discriminatoires pour certains groupes ou dans des contextes spécifiques.
​
Exploitation des biais : une technique d'attaque qui tire parti des biais connus dans les modèles d'IA pour manipuler les résultats ou les sorties.
​
Cedar : langage de politique et moteur d'Amazon pour des autorisations granulaires utilisées dans la mise en œuvre de l'ABAC pour les systèmes d'IA.
​
Chaîne de pensée : une technique pour améliorer le raisonnement dans les modèles de langage en générant des étapes intermédiaires de raisonnement avant de produire une réponse finale.
​
Disjoncteurs : Mécanismes qui arrêtent automatiquement les opérations du système d’IA lorsque des seuils de risque spécifiques sont dépassés.
​
Service d'inférence confidentiel : un service d'inférence qui exécute des modèles d'IA à l'intérieur d'un environnement d'exécution sécurisé (TEE) ou d'un mécanisme équivalent de calcul confidentiel, garantissant que les poids du modèle et les données d'inférence restent chiffrés, scellés et protégés contre tout accès ou altération non autorisés.
​
Charge de travail confidentielle : une charge de travail d’IA (par exemple, entraînement, inférence, prétraitement) exécutée à l’intérieur d’un environnement d’exécution sécurisé (TEE) avec isolation matérielle, chiffrement de la mémoire et attestation à distance pour protéger le code, les données et les modèles contre l’accès par l’hôte ou les co-occupants.
​
Fuite de données : exposition non intentionnelle d'informations sensibles à travers les résultats ou le comportement d'un modèle d'IA.
​
Empoisonnement des données : la corruption délibérée des données d'entraînement pour compromettre l'intégrité du modèle, souvent dans le but d'installer des portes dérobées ou de dégrader les performances.
​
Confidentialité différentielle – La confidentialité différentielle est un cadre mathématiquement rigoureux pour la diffusion d'informations statistiques sur des ensembles de données tout en protégeant la vie privée des individus concernés. Elle permet à un détenteur de données de partager des tendances agrégées du groupe tout en limitant les informations divulguées sur des individus spécifiques.
​
Embeddings : Représentations vectorielles denses des données (texte, images, etc.) qui capturent le sens sémantique dans un espace de haute dimension.
​
Explicabilité – L’explicabilité en IA est la capacité d’un système d’IA à fournir des raisons compréhensibles par les humains pour ses décisions et prédictions, offrant ainsi des aperçus sur son fonctionnement interne.
​
IA explicable (XAI) : Systèmes d'IA conçus pour fournir des explications compréhensibles par l'humain concernant leurs décisions et comportements grâce à diverses techniques et cadres.
​
Apprentissage Fédéré : une approche d'apprentissage automatique où les modèles sont entraînés sur plusieurs dispositifs décentralisés détenant des échantillons de données locales, sans échanger les données elles-mêmes.
​
Formulation : La recette ou méthode utilisée pour produire un artefact ou un ensemble de données, tels que les hyperparamètres, la configuration d'entraînement, les étapes de prétraitement ou les scripts de compilation.
​
Garde-fous : Contraintes mises en place pour empêcher les systèmes d'IA de produire des résultats nuisibles, biaisés ou autrement indésirables.
​
Hallucination – Une hallucination d’IA fait référence à un phénomène où un modèle d’IA génère des informations incorrectes ou trompeuses qui ne sont pas basées sur ses données d’entraînement ou sur la réalité factuelle.
​
Humain dans la boucle (HITL) : Systèmes conçus pour nécessiter une supervision, une vérification ou une intervention humaine aux points de décision cruciaux.
​
Infrastructure as Code (IaC) : gestion et provisionnement de l'infrastructure via du code plutôt que par des processus manuels, permettant l'analyse de sécurité et des déploiements cohérents.
​
Jailbreak : Techniques utilisées pour contourner les dispositifs de sécurité dans les systèmes d’IA, en particulier dans les grands modèles de langage, afin de produire du contenu interdit.
​
Moindre privilège : Le principe de sécurité consistant à accorder uniquement les droits d'accès minimaux nécessaires aux utilisateurs et aux processus.
​
LIME (Explications Locales Modèle-agnostique Interprétables) : une technique pour expliquer les prédictions de n'importe quel classificateur d'apprentissage automatique en l'approximation localement avec un modèle interprétable.
​
Attaque par inférence d'appartenance : une attaque visant à déterminer si un point de données spécifique a été utilisé pour entraîner un modèle d'apprentissage automatique.
​
MITRE ATLAS : Paysage des menaces adverses pour les systèmes d'intelligence artificielle ; une base de connaissances des tactiques et techniques adverses contre les systèmes d'IA.
​
Fiche de modèle – Une fiche de modèle est un document qui fournit des informations standardisées sur les performances, les limites, les usages prévus et les considérations éthiques d'un modèle d'IA afin de promouvoir la transparence et le développement responsable de l'IA.
​
Extraction de modèle : une attaque où un adversaire interroge de manière répétée un modèle cible afin de créer une copie fonctionnellement similaire sans autorisation.
​
Inversion de modèle : une attaque qui tente de reconstruire les données d'entraînement en analysant les sorties du modèle.
​
Gestion du cycle de vie du modèle – La gestion du cycle de vie des modèles d’IA est le processus de supervision de toutes les phases de l’existence d’un modèle d’IA, y compris sa conception, son développement, son déploiement, sa surveillance, sa maintenance et son retrait éventuel, afin de garantir qu’il reste efficace et en accord avec les objectifs.
​
Empoisonnement de modèle : introduction de vulnérabilités ou de portes dérobées directement dans un modèle pendant le processus d'entraînement.
​
Vol de modèle : Extraire une copie ou une approximation d'un modèle propriétaire par des requêtes répétées.
​
Système multi-agent : un système composé de plusieurs agents d'IA interagissant, chacun pouvant avoir des capacités et des objectifs différents.
​
OPA (Open Policy Agent) : un moteur de politique open-source qui permet une application unifiée des politiques dans toute la pile.
​
Origine : La généalogie et la chaîne de conservation d'un artefact ou d'un ensemble de données, incluant son origine, les manipulateurs, le chemin de transfert, et les preuves d'intégrité (par exemple, sommes de contrôle, signatures).
​
Apprentissage automatique respectueux de la vie privée (PPML) : Techniques et méthodes pour entraîner et déployer des modèles d’AA tout en protégeant la confidentialité des données d’entraînement.
​
Injection de prompt : une attaque où des instructions malveillantes sont intégrées dans les entrées pour contourner le comportement prévu d'un modèle.
​
RAG (Génération augmentée par récupération) : une technique qui améliore les grands modèles de langage en récupérant des informations pertinentes à partir de sources de connaissances externes avant de générer une réponse.
​
Red-Teaming : La pratique de tester activement les systèmes d'IA en simulant des attaques adverses afin d'identifier les vulnérabilités.
​
Provenance SLSA : Métadonnées définies par le cadre SLSA qui enregistrent où, quand et comment un artefact a été produit (par exemple, dépôt source, hachage de commit, système de construction et paramètres).
​
SBOM (Liste des composants logiciels) : Un enregistrement formel contenant les détails et les relations de la chaîne d'approvisionnement des différents composants utilisés dans la création de logiciels ou de modèles d'IA.
​
SHAP (Explications Additives de Shapley) : Une approche basée sur la théorie des jeux pour expliquer la sortie de n'importe quel modèle d'apprentissage automatique en calculant la contribution de chaque caractéristique à la prédiction.
​
Authentification forte : Authentification qui résiste au vol d’identifiants et à la rejeu en exigeant au moins deux facteurs (connaissance, possession, inhérence) et des mécanismes résistants au phishing tels que FIDO2/WebAuthn, l’authentification de service basée sur un certificat, ou les jetons à courte durée de vie.
​
Attaque sur la chaîne d'approvisionnement : compromettre un système en ciblant les éléments moins sécurisés de sa chaîne d'approvisionnement, tels que les bibliothèques tierces, les ensembles de données ou les modèles pré-entraînés.
​
Apprentissage par transfert : une technique où un modèle développé pour une tâche est réutilisé comme point de départ pour un modèle sur une deuxième tâche.
​
Base de données vectorielle : une base de données spécialisée conçue pour stocker des vecteurs de haute dimension (embeddings) et effectuer des recherches efficaces de similarité.
​
Analyse des vulnérabilités : Outils automatisés qui identifient les vulnérabilités de sécurité connues dans les composants logiciels, y compris les frameworks d'IA et leurs dépendances.
​
Filigrane : Techniques pour intégrer des marqueurs imperceptibles dans le contenu généré par l'IA afin de suivre son origine ou de détecter une génération par IA.
​
Vulnérabilité Zero-Day : une vulnérabilité jusqu’alors inconnue que les attaquants peuvent exploiter avant que les développeurs ne créent et déploient un correctif.

## Annexe B : Références

### TODO

## Annexe C : Gouvernance et documentation de la sécurité de l'IA (réorganisé)

### Objectif

Cette annexe fournit les exigences fondamentales pour établir des structures organisationnelles, des politiques, de la documentation et des processus afin de gouverner la sécurité de l'IA tout au long du cycle de vie du système.

---

### AC.1 Adoption du cadre de gestion des risques liés à l'IA

 #AC.1.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'une méthodologie d'évaluation des risques spécifique à l'IA est documentée et mise en œuvre.
 #AC.1.2    Niveau: 2    Rôle: D
 Vérifiez que des évaluations des risques sont effectuées aux points clés du cycle de vie de l'IA et avant des changements importants.
 #AC.1.3    Niveau: 3    Rôle: D/V
 Vérifiez que le cadre de gestion des risques est conforme aux normes établies (par exemple, NIST AI RMF).

---

### AC.2 Politique et procédures de sécurité de l'IA

 #AC.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que des politiques de sécurité de l'IA documentées existent.
 #AC.2.2    Niveau: 2    Rôle: D
 Vérifiez que les politiques sont examinées et mises à jour au moins une fois par an et après des changements significatifs du paysage des menaces.
 #AC.2.3    Niveau: 3    Rôle: D/V
 Vérifiez que les politiques couvrent toutes les catégories AISVS et les exigences réglementaires applicables.

---

### AC.3 Rôles et responsabilités pour la sécurité de l'IA

 #AC.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les rôles et responsabilités en matière de sécurité de l'IA sont documentés.
 #AC.3.2    Niveau: 2    Rôle: D
 Vérifiez que les personnes responsables possèdent une expertise en sécurité appropriée.
 #AC.3.3    Niveau: 3    Rôle: D/V
 Vérifiez qu'un comité d'éthique de l'IA ou un conseil de gouvernance est établi pour les systèmes d'IA à haut risque.

---

### AC.4 Application des lignes directrices pour une IA éthique

 #AC.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que des directives éthiques pour le développement et le déploiement de l'IA existent.
 #AC.4.2    Niveau: 2    Rôle: D
 Vérifiez que des mécanismes sont en place pour détecter et signaler les violations éthiques.
 #AC.4.3    Niveau: 3    Rôle: D/V
 Vérifiez que des revues éthiques régulières des systèmes d'IA déployés sont effectuées.

---

### AC.5 Surveillance de la conformité réglementaire en matière d'IA

 #AC.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que des processus existent pour identifier les réglementations applicables à l'IA.
 #AC.5.2    Niveau: 2    Rôle: D
 Vérifiez que la conformité à toutes les exigences réglementaires est évaluée.
 #AC.5.3    Niveau: 3    Rôle: D/V
 Vérifiez que les changements réglementaires déclenchent des revues et des mises à jour rapides des systèmes d’IA.

---

### AC.6 Gouvernance, Documentation et Processus des Données d’Entraînement

#### AC.6.1 Approvisionnement en données et diligence raisonnable

 #AC.6.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que seuls les ensembles de données validés pour leur qualité, leur représentativité, leur approvisionnement éthique et leur conformité aux licences sont autorisés, réduisant ainsi les risques d'empoisonnement, de biais intégrés et de violation de la propriété intellectuelle.
 #AC.6.1.2    Niveau: 2    Rôle: D/V
 Vérifiez que les fournisseurs de données tiers, y compris les prestataires de modèles pré-entraînés et de jeux de données externes, font l'objet d'une diligence raisonnable en matière de sécurité, de confidentialité, d'approvisionnement éthique et de qualité des données avant que leurs données ou modèles ne soient intégrés.
 #AC.6.1.3    Niveau: 1    Rôle: D
 Vérifier que les transferts externes utilisent TLS/authentification et des contrôles d'intégrité.
 #AC.6.1.4    Niveau: 2    Rôle: D/V
 Vérifiez que les sources de données à haut risque (par exemple, les ensembles de données open-source à provenance inconnue, les fournisseurs non vérifiés) font l'objet d'un examen renforcé, tel qu'une analyse en environnement isolé (sandbox), des contrôles approfondis de qualité/biais et une détection ciblée des empoisonnements, avant leur utilisation dans des applications sensibles.
 #AC.6.1.5    Niveau: 3    Rôle: D/V
 Vérifiez que les modèles pré-entraînés obtenus auprès de tiers sont évalués pour les biais intégrés, les portes dérobées potentielles, l'intégrité de leur architecture et la provenance de leurs données d'entraînement originales avant l'affinage ou le déploiement.

#### AC.6.2 Gestion des Biais et de l’Équité

 #AC.6.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les ensembles de données sont analysés pour détecter un déséquilibre de représentation et des biais potentiels concernant des attributs légalement protégés (par exemple, la race, le genre, l’âge) ainsi que d’autres caractéristiques éthiquement sensibles pertinentes pour le domaine d’application du modèle (par exemple, le statut socio-économique, la localisation).
 #AC.6.2.2    Niveau: 2    Rôle: D/V
 Vérifier que les biais identifiés sont atténués via des stratégies documentées telles que le rééquilibrage, l'augmentation ciblée des données, les ajustements algorithmiques (par exemple, les techniques de pré-traitement, traitement en cours, post-traitement) ou le re-pondération, et que l'impact de cette atténuation sur l'équité ainsi que sur la performance globale du modèle est évalué.
 #AC.6.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les métriques d'équité post-formation sont évaluées et documentées.
 #AC.6.2.4    Niveau: 3    Rôle: D/V
 Vérifiez qu'une politique de gestion des biais tout au long du cycle de vie attribue des propriétaires et une cadence de révision.

#### AC.6.3 Gouvernance de l'étiquetage et de l'annotation

 #AC.6.3.1    Niveau: 2    Rôle: D/V
 Vérifiez que la qualité de l'étiquetage/annotation est assurée par des contrôles croisés des examinateurs ou un consensus.
 #AC.6.3.2    Niveau: 2    Rôle: D/V
 Vérifiez que des fiches de données sont maintenues pour les ensembles de données d'entraînement significatifs, détaillant les caractéristiques, motivations, composition, processus de collecte, prétraitement, licences et utilisations recommandées/déconseillées.
 #AC.6.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les fiches de données documentent les risques de biais, les déséquilibres démographiques et les considérations éthiques pertinentes pour le jeu de données.
 #AC.6.3.4    Niveau: 2    Rôle: D/V
 Vérifiez que les fiches de données sont versionnées parallèlement aux ensembles de données et mises à jour chaque fois que l'ensemble de données est modifié.
 #AC.6.3.5    Niveau: 2    Rôle: D/V
 Vérifiez que les fiches de données sont examinées et approuvées à la fois par des parties prenantes techniques et non techniques (par exemple, conformité, éthique, experts du domaine).
 #AC.6.3.6    Niveau: 2    Rôle: D/V
 Vérifiez que la qualité de l'étiquetage/annotation est garantie grâce à des directives claires, des vérifications croisées par des examinateurs, des mécanismes de consensus (par exemple, la surveillance de l'accord entre les annotateurs) et des processus définis pour résoudre les divergences.
 #AC.6.3.7    Niveau: 3    Rôle: D/V
 Vérifiez que les étiquettes critiques pour la sécurité, la sûreté ou l'équité (par exemple, l'identification de contenu toxique, des résultats médicaux critiques) font l'objet d'une révision indépendante doublée obligatoire ou d'une vérification rigoureuse équivalente.
 #AC.6.3.8    Niveau: 2    Rôle: D/V
 Vérifiez que les guides d'étiquetage et les instructions sont complets, soumis à un contrôle de version et examinés par les pairs.
 #AC.6.3.9    Niveau: 2    Rôle: D/V
 Vérifiez que les schémas de données pour les étiquettes sont clairement définis et soumis à un contrôle de version.
 #AC.6.3.10    Niveau: 2    Rôle: D/V
 Vérifiez que les flux de travail de labellisation externalisés ou crowdsourcés incluent des mesures techniques/procédurales pour garantir la confidentialité des données, leur intégrité, la qualité des étiquettes, et prévenir les fuites de données.
 #AC.6.3.11    Niveau: 2    Rôle: D/V
 Vérifiez que tout le personnel impliqué dans l'annotation des données a été soumis à une vérification des antécédents et formé à la sécurité et à la confidentialité des données.
 #AC.6.3.12    Niveau: 2    Rôle: D/V
 Vérifiez que tout le personnel d'annotation signe des accords de confidentialité et de non-divulgation.
 #AC.6.3.13    Niveau: 2    Rôle: D/V
 Vérifiez que les plateformes d'annotation appliquent des contrôles d'accès et surveillent les menaces internes.

#### AC.6.4 Portails de qualité des jeux de données et quarantaine

 #AC.6.4.1    Niveau: 2    Rôle: D/V
 Vérifiez que les ensembles de données défaillants sont mis en quarantaine avec des pistes d'audit.
 #AC.6.4.2    Niveau: 2    Rôle: D/V
 Vérifiez que les passerelles de qualité bloquent les ensembles de données de qualité inférieure, sauf si des exceptions sont approuvées.
 #AC.6.4.3    Niveau: 2    Rôle: V
 Vérifiez que les contrôles ponctuels manuels effectués par des experts du domaine couvrent un échantillon statistiquement significatif (par exemple, ≥1 % ou 1 000 échantillons, selon la valeur la plus élevée, ou tel que déterminé par l’évaluation des risques) afin d’identifier les problèmes de qualité subtils non détectés par l’automatisation.

#### AC.6.5 Détection de menaces/empoisonnement et dérive

 #AC.6.5.1    Niveau: 2    Rôle: D/V
 Vérifiez que les échantillons signalés déclenchent un examen manuel avant l'entraînement.
 #AC.6.5.2    Niveau: 2    Rôle: V
 Vérifiez que les résultats alimentent le dossier de sécurité du modèle et informent le renseignement continu sur les menaces.
 #AC.6.5.3    Niveau: 3    Rôle: D/V
 Vérifiez que la logique de détection est mise à jour avec les nouvelles informations sur les menaces.
 #AC.6.5.4    Niveau: 3    Rôle: D/V
 Vérifiez que les pipelines d'apprentissage en ligne surveillent la dérive de distribution.

#### AC.6.6 Suppression, Consentement, Droits, Conservation et Conformité

 #AC.6.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que les flux de travail de suppression des données d'entraînement effacent les données primaires et dérivées et évaluent l'impact sur le modèle, et que l'impact sur les modèles concernés est évalué et, si nécessaire, corrigé (par exemple, par un réentraînement ou un recalibrage).
 #AC.6.6.2    Niveau: 2    Rôle: D
 Vérifiez que des mécanismes sont en place pour suivre et respecter la portée et le statut du consentement de l'utilisateur (et des retraits) concernant les données utilisées pour l'entraînement, et que le consentement est validé avant que les données ne soient intégrées dans de nouveaux processus d'entraînement ou des mises à jour importantes du modèle.
 #AC.6.6.3    Niveau: 2    Rôle: V
 Vérifiez que les flux de travail sont testés annuellement et consignés.
 #AC.6.6.4    Niveau: 1    Rôle: D/V
 Vérifiez que des périodes de rétention explicites sont définies pour tous les ensembles de données d'entraînement.
 #AC.6.6.5    Niveau: 2    Rôle: D/V
 Vérifiez que les ensembles de données sont automatiquement expirés, supprimés ou examinés pour suppression à la fin de leur cycle de vie.
 #AC.6.6.6    Niveau: 2    Rôle: D/V
 Vérifiez que les actions de conservation et de suppression sont enregistrées et vérifiables.
 #AC.6.6.7    Niveau: 2    Rôle: D/V
 Vérifiez que les exigences relatives à la résidence des données et au transfert transfrontalier sont identifiées et appliquées pour tous les ensembles de données.
 #AC.6.6.8    Niveau: 2    Rôle: D/V
 Vérifiez que les réglementations spécifiques à chaque secteur (par exemple, la santé, la finance) sont identifiées et prises en compte dans la gestion des données.
 #AC.6.6.9    Niveau: 2    Rôle: D/V
 Vérifiez que la conformité avec les lois sur la vie privée pertinentes (par exemple, GDPR, CCPA) est documentée et examinée régulièrement.
 #AC.6.6.10    Niveau: 2    Rôle: D/V
 Vérifiez que des mécanismes existent pour répondre aux demandes des personnes concernées concernant l'accès, la rectification, la restriction ou l'opposition.
 #AC.6.6.11    Niveau: 2    Rôle: D/V
 Vérifiez que les demandes sont enregistrées, suivies et satisfaites dans les délais légaux impartis.
 #AC.6.6.12    Niveau: 2    Rôle: D/V
 Vérifiez que les processus relatifs aux droits des personnes concernées sont testés et révisés régulièrement pour en assurer l'efficacité.

#### AC.6.7 Gestion des versions et des changements

 #AC.6.7.1    Niveau: 2    Rôle: D/V
 Vérifiez qu'une analyse d'impact est réalisée avant de mettre à jour ou de remplacer une version de jeu de données, en couvrant la performance du modèle, l'équité et la conformité.
 #AC.6.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que les résultats de l'analyse d'impact sont documentés et examinés par les parties prenantes concernées.
 #AC.6.7.3    Niveau: 2    Rôle: D/V
 Vérifiez que des plans de retour en arrière existent au cas où les nouvelles versions introduiraient des risques inacceptables ou des régressions.

#### AC.6.8 Gouvernance des données synthétiques

 #AC.6.8.1    Niveau: 2    Rôle: D/V
 Vérifiez que le processus de génération, les paramètres et l'utilisation prévue des données synthétiques sont documentés.
 #AC.6.8.2    Niveau: 2    Rôle: D/V
 Vérifiez que les données synthétiques ont fait l'objet d'une évaluation des risques concernant les biais, les fuites de confidentialité et les problèmes de représentation avant leur utilisation dans l'entraînement.

#### AC.6.9 Surveillance des accès

 #AC.6.9.1    Niveau: 2    Rôle: D/V
 Vérifiez que les journaux d'accès sont régulièrement examinés pour détecter des motifs inhabituels, tels que des exportations importantes ou des accès depuis de nouveaux emplacements.
 #AC.6.9.2    Niveau: 2    Rôle: D/V
 Vérifiez que des alertes sont générées pour les événements d'accès suspects et qu'elles sont examinées rapidement.

#### AC.6.10 Gouvernance de l'entraînement adversarial

 #AC.6.10.1    Niveau: 2    Rôle: D/V
 Vérifiez que si l'entraînement adversarial est utilisé, la génération, la gestion et la version des ensembles de données adversariales sont documentées et contrôlées.
 #AC.6.10.2    Niveau: 3    Rôle: D/V
 Vérifier que l'impact de l'entraînement à la robustesse adversariale sur les performances du modèle (contre des entrées à la fois propres et adversariales) ainsi que sur les métriques d'équité est évalué, documenté et surveillé.
 #AC.6.10.3    Niveau: 3    Rôle: D/V
 Vérifiez que les stratégies d'entraînement adversarial et de robustesse sont périodiquement révisées et mises à jour pour contrer les techniques d'attaque adversariales en évolution.

---

### AC.7 Gouvernance et documentation du cycle de vie du modèle

 #AC.7.1    Niveau: 2    Rôle: D/V
 Vérifiez que tous les artefacts du modèle utilisent le versionnage sémantique (MAJOR.MINOR.PATCH) avec des critères documentés précisant quand chaque composant de version est incrémenté.
 #AC.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que les déploiements d'urgence nécessitent une évaluation documentée des risques de sécurité et une approbation de la part d'une autorité de sécurité pré-désignée dans des délais préalablement convenus.
 #AC.7.3    Niveau: 2    Rôle: V
 Vérifiez que les artefacts de restauration (versions précédentes du modèle, configurations, dépendances) sont conservés conformément aux politiques organisationnelles.
 #AC.7.4    Niveau: 2    Rôle: D/V
 Vérifiez que l'accès au journal d'audit nécessite une autorisation appropriée et que toutes les tentatives d'accès sont enregistrées avec l'identité de l'utilisateur et un horodatage.
 #AC.7.5    Niveau: 1    Rôle: D/V
 Vérifiez que les artefacts des modèles retirés sont conservés conformément aux politiques de conservation des données.

---

### Gouvernance de la sécurité des invites, des entrées et des sorties AC.8

#### AC.8.1 Défense contre l'injection de requêtes

 #AC.8.1.1    Niveau: 2    Rôle: D/V
 Vérifiez que les tests d’évaluation adversariale (par exemple, les invites Red Team « many-shot ») sont effectués avant chaque publication de modèle ou de modèle d’invite, avec des seuils de taux de réussite et des bloqueurs automatisés pour les régressions.
 #AC.8.1.2    Niveau: 3    Rôle: D/V
 Vérifiez que toutes les mises à jour des règles de filtrage des invites, les versions des modèles classificateurs et les modifications des listes de blocage sont contrôlées par version et vérifiables.

#### AC.8.2 Résistance aux exemples contradictoires

 #AC.8.2.1    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques de robustesse (taux de réussite des suites d'attaques connues) sont suivies au fil du temps via l'automatisation et que les régressions déclenchent une alerte.

#### AC.8.3 Filtrage du contenu et des politiques

 #AC.8.3.1    Niveau: 2    Rôle: D
 Vérifiez que le modèle de filtrage ou l'ensemble de règles est réentraîné/mis à jour au moins trimestriellement, en intégrant les nouveaux schémas de jailbreak ou de contournement de politique observés.

#### AC.8.4 Limitation du taux d'entrée et prévention des abus

 #AC.8.4.1    Niveau: 3    Rôle: V
 Vérifiez que les journaux de prévention des abus sont conservés et examinés pour détecter les nouveaux schémas d'attaque.

#### AC.8.5 Provenance et attribution des entrées

 #AC.8.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que toutes les entrées utilisateur sont étiquetées avec des métadonnées (ID utilisateur, session, source, horodatage, adresse IP) lors de l'ingestion.
 #AC.8.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les métadonnées de provenance sont conservées et vérifiables pour toutes les entrées traitées.
 #AC.8.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que les sources d’entrée anormales ou non fiables sont signalées et soumises à un contrôle accru ou à un blocage.

---

### AC.9 Validation multimodale, MLOps et gouvernance de l'infrastructure

#### AC.9.1 Pipeline de validation de la sécurité multimodale

 #AC.9.1.1    Niveau: 3    Rôle: D/V
 Vérifiez que les classificateurs de contenu spécifiques à chaque modalité sont mis à jour selon les calendriers documentés (au minimum trimestriellement) avec de nouveaux schémas de menaces, des exemples adverses, et que les performances sont maintenues au-dessus des seuils de référence.

#### AC.9.2 Sécurité CI/CD et de la Compilation

 #AC.9.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que l'infrastructure en tant que code est analysée à chaque commit, et que les fusions sont bloquées en cas de détections critiques ou de haute gravité.
 #AC.9.2.2    Niveau: 2    Rôle: D/V
 Vérifiez que les pipelines CI/CD utilisent des identités à courte durée de vie et à champ d'application limité pour accéder aux secrets et à l'infrastructure.
 #AC.9.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les environnements de développement sont isolés des réseaux et des données de production.

#### AC.9.3 Sécurité des conteneurs et des images

 #AC.9.3.1    Niveau: 2    Rôle: D/V
 Vérifiez que les images de conteneurs sont analysées pour bloquer les secrets codés en dur (par exemple, les clés API, les identifiants, les certificats).
 #AC.9.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que les images des conteneurs sont analysées conformément aux calendriers organisationnels, avec les vulnérabilités CRITIQUES bloquant le déploiement en fonction des seuils de risque organisationnels.

#### AC.9.4 Surveillance, Alertes et SIEM

 #AC.9.4.1    Niveau: 2    Rôle: V
 Vérifiez que les alertes de sécurité s'intègrent aux plateformes SIEM (Splunk, Elastic ou Sentinel) en utilisant les formats CEF ou STIX/TAXII avec un enrichissement automatisé.

#### AC.9.5 Gestion des vulnérabilités

 #AC.9.5.1    Niveau: 2    Rôle: D/V
 Vérifiez que les vulnérabilités de gravité ÉLEVÉE sont corrigées conformément aux délais de gestion des risques organisationnels avec des procédures d'urgence pour les CVE activement exploitées.

#### AC.9.6 Contrôle de la Configuration et des Dérives

 #AC.9.6.1    Niveau: 2    Rôle: D/V
 Vérifiez que la dérive de configuration est détectée à l'aide d'outils (Chef InSpec, AWS Config) conformément aux exigences de surveillance organisationnelles avec un retour automatique en cas de modifications non autorisées.

#### AC.9.7 Durcissement de l'Environnement de Production

 #AC.9.7.1    Niveau: 2    Rôle: D/V
 Vérifiez que les environnements de production bloquent l'accès SSH, désactivent les points de terminaison de débogage et exigent des demandes de modification avec des exigences de préavis organisationnel, sauf en cas d'urgence.

#### AC.9.8 Portes de Promotion de Version

 #AC.9.8.1    Niveau: 2    Rôle: D/V
 Vérifiez que les points de contrôle de promotion incluent des tests de sécurité automatisés (SAST, DAST, analyse des conteneurs) avec zéro résultat CRITIQUE requis pour l'approbation.

#### AC.9.9 Surveillance de la charge de travail, de la capacité et des coûts

 #AC.9.9.1    Niveau: 1    Rôle: D/V
 Vérifiez que l'utilisation du GPU/TPU est surveillée avec des alertes déclenchées aux seuils définis par l'organisation et que la mise à l'échelle automatique ou la répartition de la charge est activée en fonction des politiques de gestion de la capacité.
 #AC.9.9.2    Niveau: 1    Rôle: D/V
 Vérifiez que les métriques de charge de travail de l'IA (latence d'inférence, débit, taux d'erreur) sont collectées conformément aux exigences de surveillance organisationnelle et corrélées avec l'utilisation de l'infrastructure.
 #AC.9.9.3    Niveau: 2    Rôle: V
 Vérifiez que la surveillance des coûts suit les dépenses par charge de travail/locataire avec des alertes basées sur les seuils budgétaires organisationnels et des contrôles automatisés pour les dépassements de budget.
 #AC.9.9.4    Niveau: 3    Rôle: V
 Vérifiez que la planification de capacité utilise des données historiques avec des périodes de prévision définies par l'organisation et un approvisionnement automatisé des ressources basé sur les modèles de demande.

#### AC.9.10 Approbations et pistes d’audit

 #AC.9.10.1    Niveau: 1    Rôle: D/V
 Vérifiez que la promotion de l’environnement nécessite l’approbation du personnel autorisé défini organisationnellement, avec des signatures cryptographiques et des pistes d’audit immuables.

#### AC.9.11 Gouvernance IaC

 #AC.9.11.1    Niveau: 2    Rôle: D/V
 Vérifiez que les modifications de l'infrastructure en tant que code nécessitent une relecture par les pairs avec des tests automatisés et une analyse de sécurité avant la fusion dans la branche principale.

#### AC.9.12 Gestion des données en environnement non productif

 #AC.9.12.1    Niveau: 2    Rôle: D/V
 Vérifiez que les données non destinées à la production sont anonymisées conformément aux exigences de confidentialité organisationnelles, à la génération de données synthétiques ou à un masquage complet des données avec suppression des informations personnelles identifiables (PII) vérifiée.

#### AC.9.13 Sauvegarde et récupération après sinistre

 #AC.9.13.1    Niveau: 1    Rôle: D/V
 Vérifiez que les configurations d'infrastructure sont sauvegardées conformément aux calendriers de sauvegarde organisationnels vers des régions géographiquement séparées avec la mise en œuvre de la stratégie de sauvegarde 3-2-1.
 #AC.9.13.2    Niveau: 2    Rôle: V
 Vérifiez que les procédures de récupération sont testées et validées par des tests automatisés conformément aux calendriers organisationnels, avec des objectifs de RTO et RPO répondant aux exigences de l'organisation.
 #AC.9.13.3    Niveau: 3    Rôle: V
 Vérifiez que la reprise après sinistre inclut des runbooks spécifiques à l'IA avec la restauration des poids du modèle, la reconstruction du cluster GPU et la cartographie des dépendances des services.

#### AC.9.14 Conformité et Documentation

 #AC.9.14.1    Niveau: 2    Rôle: D/V
 Vérifiez que la conformité de l'infrastructure est évaluée selon les calendriers organisationnels en fonction des contrôles SOC 2, ISO 27001 ou FedRAMP avec une collecte automatisée des preuves.
 #AC.9.14.2    Niveau: 2    Rôle: V
 Vérifiez que la documentation de l'infrastructure comprend des diagrammes réseau, des cartes de flux de données et des modèles de menace mis à jour conformément aux exigences de gestion des changements organisationnels.
 #AC.9.14.3    Niveau: 3    Rôle: D/V
 Vérifiez que les changements d'infrastructure font l'objet d'une évaluation automatisée de l'impact sur la conformité avec des flux de travail d'approbation réglementaire pour les modifications à haut risque.

#### AC.9.15 Matériel et chaîne d'approvisionnement

 #AC.9.15.1    Niveau: 2    Rôle: D/V
 Vérifiez que le microprogramme de l'accélérateur AI (BIOS GPU, microprogramme TPU) est vérifié avec des signatures cryptographiques et mis à jour conformément aux délais de gestion des correctifs de l'organisation.
 #AC.9.15.2    Niveau: 3    Rôle: V
 Vérifiez que la chaîne d'approvisionnement du matériel IA inclut une vérification de la provenance avec des certificats du fabricant et une validation de l'emballage inviolable.

#### AC.9.16 Stratégie Cloud et Portabilité

 #AC.9.16.1    Niveau: 3    Rôle: V
 Vérifiez que la prévention du verrouillage fournisseur cloud inclut une infrastructure en tant que code portable, des API standardisées, et des capacités d'exportation de données avec des outils de conversion de format.
 #AC.9.16.2    Niveau: 3    Rôle: V
 Vérifiez que l’optimisation des coûts multi-cloud inclut des contrôles de sécurité empêchant la prolifération des ressources ainsi que les frais de transfert de données inter-cloud non autorisés.

#### AC.9.17 GitOps et Auto-réparation

 #AC.9.17.1    Niveau: 2    Rôle: D/V
 Vérifiez que les dépôts GitOps exigent des commits signés avec des clés GPG et des règles de protection des branches empêchant les pushes directs vers les branches principales.
 #AC.9.17.2    Niveau: 3    Rôle: V
 Vérifiez que l'infrastructure auto-réparatrice inclut la corrélation des événements de sécurité avec une réponse automatisée aux incidents et des flux de travail de notification aux parties prenantes.

#### AC.9.18 Zero-Trust, Agents, Provisionnement et Attestation de Résidence

 #AC.9.18.1    Niveau: 2    Rôle: D/V
 Vérifiez que l'accès aux ressources cloud inclut une vérification zero-trust avec une authentification continue.
 #AC.9.18.2    Niveau: 2    Rôle: D/V
 Vérifiez que la provision automatisée de l'infrastructure inclut la validation des politiques de sécurité avec un blocage du déploiement pour les configurations non conformes.
 #AC.9.18.3    Niveau: 2    Rôle: D/V
 Vérifiez que l'approvisionnement automatisé de l'infrastructure valide les politiques de sécurité pendant le CI/CD, avec les configurations non conformes bloquées lors du déploiement.
 #AC.9.18.4    Niveau: 3    Rôle: D/V
 Vérifiez que les exigences de résidence des données sont respectées par une attestation cryptographique des emplacements de stockage.
 #AC.9.18.5    Niveau: 3    Rôle: D/V
 Vérifiez que les évaluations de sécurité du fournisseur cloud incluent une modélisation des menaces spécifique à l'agent et une évaluation des risques.

## Annexe D : Gouvernance et vérification du codage sécurisé assisté par IA

### Objectif

Ce chapitre définit les contrôles organisationnels de base pour l'utilisation sûre et efficace des outils de codage assistés par IA lors du développement logiciel, garantissant la sécurité et la traçabilité tout au long du cycle de vie du développement logiciel (SDLC).

---

### AD.1 Flux de travail de codage sécurisé assisté par IA

Intégrer les outils d’IA dans le cycle de vie du développement sécurisé des logiciels (SSDLC) de l’organisation sans affaiblir les barrières de sécurité existantes.

 #AD.1.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'un flux de travail documenté décrit quand et comment les outils d'IA peuvent générer, refactoriser ou examiner du code.
 #AD.1.2    Niveau: 2    Rôle: D
 Vérifiez que le flux de travail correspond à chaque phase du SSDLC (conception, mise en œuvre, revue de code, tests, déploiement).
 #AD.1.3    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques (par exemple, la densité de vulnérabilité, le temps moyen de détection) sont collectées sur le code produit par l'IA et comparées aux référentiels humains uniquement.

---

### AD.2 Qualification des outils d'IA et modélisation des menaces

Veillez à ce que les outils de codage IA soient évalués en termes de capacités de sécurité, de risques et d'impact sur la chaîne d'approvisionnement avant leur adoption.

 #AD.2.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'un modèle de menace pour chaque outil d'IA identifie les risques d'utilisation abusive, d'inversion de modèle, de fuite de données et de chaîne de dépendances.
 #AD.2.2    Niveau: 2    Rôle: D
 Vérifiez que les évaluations des outils incluent une analyse statique/dynamique de tous les composants locaux ainsi qu’une évaluation des points de terminaison SaaS (TLS, authentification/autorisation, journalisation).
 #AD.2.3    Niveau: 3    Rôle: D/V
 Vérifiez que les évaluations suivent un cadre reconnu et sont refaites après des changements majeurs de version.

---

### AD.3 Gestion sécurisée des invites et du contexte

Prévenir la fuite de secrets, de code propriétaire et de données personnelles lors de la construction de prompts ou de contextes pour les modèles d'IA.

 #AD.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les directives écrites interdisent l'envoi de secrets, d'identifiants ou de données classifiées dans les prompts.
 #AD.3.2    Niveau: 2    Rôle: D
 Vérifiez que les contrôles techniques (rédaction côté client, filtres de contexte approuvés) suppriment automatiquement les éléments sensibles.
 #AD.3.3    Niveau: 3    Rôle: D/V
 Vérifiez que les invites et les réponses sont tokenisées, chiffrées en transit et au repos, et que les périodes de rétention sont conformes à la politique de classification des données.

---

### AD.4 Validation du code généré par l'IA

Détecter et corriger les vulnérabilités introduites par la sortie de l'IA avant que le code ne soit fusionné ou déployé.

 #AD.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que le code généré par l'IA soit toujours soumis à une revue de code humaine.
 #AD.4.2    Niveau: 2    Rôle: D
 Vérifiez que les scanners automatisés (SAST/IAST/DAST) sont exécutés sur chaque demande de fusion contenant du code généré par l'IA et empêchent les fusions en cas de détections critiques.
 #AD.4.3    Niveau: 3    Rôle: D/V
 Vérifiez que les tests de fuzzing différentiel ou les tests basés sur les propriétés prouvent les comportements critiques pour la sécurité (par exemple, la validation des entrées, la logique d'autorisation).

---

### AD.5 Explicabilité et Traçabilité des Suggestions de Code

Fournir aux auditeurs et aux développeurs des informations sur les raisons pour lesquelles une suggestion a été faite et comment elle a évolué.

 #AD.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les paires invite/réponse sont enregistrées avec les identifiants de commit.
 #AD.5.2    Niveau: 2    Rôle: D
 Vérifiez que les développeurs peuvent afficher les citations du modèle (extraits d'entraînement, documentation) soutenant une suggestion.
 #AD.5.3    Niveau: 3    Rôle: D/V
 Vérifiez que les rapports d'explicabilité sont stockés avec les artefacts de conception et référencés dans les revues de sécurité, satisfaisant ainsi les principes de traçabilité de l'ISO/IEC 42001.

---

### AD.6 Retour Continu et Affinage du Modèle

Améliorer les performances de sécurité du modèle au fil du temps tout en empêchant la dérive négative.

 #AD.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que les développeurs peuvent signaler les suggestions non sécurisées ou non conformes, et que ces signalements sont suivis.
 #AD.6.2    Niveau: 2    Rôle: D
 Vérifiez que les retours agrégés alimentent le réglage périodique ou la génération augmentée par récupération avec des corpus de codage sécurisé vérifiés (par exemple, les Cheat Sheets d’OWASP).
 #AD.6.3    Niveau: 3    Rôle: D/V
 Vérifiez qu'un dispositif d'évaluation en boucle fermée exécute des tests de régression après chaque ajustement fin ; les métriques de sécurité doivent atteindre ou dépasser les niveaux de référence précédents avant le déploiement.

---

#### Références

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Annexe E : Exemples d'outils et de frameworks

### Objectif

Ce chapitre fournit des exemples d’outils et de cadres qui peuvent soutenir la mise en œuvre ou la satisfaction d’une exigence AISVS donnée. Ceux-ci ne doivent pas être considérés comme des recommandations ou des approbations de la part de l’équipe AISVS ou du projet OWASP GenAI Security.

---

### AE.1 Gouvernance des données d'entraînement et gestion des biais

Outils utilisés pour l'analyse des données, la gouvernance et la gestion des biais.

 #AE.1.1    Section: 1.1
 Outils d'inventaire des données : Outils de gestion d'inventaire des données tels que...
 #AE.1.2    Section: 1.2
 Chiffrement en transit Utilisez TLS pour les applications basées sur HTTPS, avec des outils comme openSSL et python's`ssl`bibliothèque.

---

### AE.2 Validation des entrées utilisateur

Outils pour gérer et valider les entrées utilisateur.

 #AE.2.1    Section: 2.1
 Outils de défense contre l'injection de prompt : utilisez des outils de garde-fous tels que NeMo de NVIDIA ou Guardrails AI.

---

## Annexe B : Contrôles stratégiques

### C4.15 Sécurité des infrastructures résistantes au quantique

Préparez l'infrastructure d'IA face aux menaces de l'informatique quantique grâce à la cryptographie post-quantique et aux protocoles résistants au quantique.

 #4.15.1    Niveau: 3    Rôle: D/V
 Vérifiez que l'infrastructure d'IA met en œuvre des algorithmes cryptographiques post-quantiques approuvés par le NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) pour l'échange de clés et les signatures numériques.
 #4.15.2    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes de distribution de clés quantiques (QKD) sont mis en œuvre pour les communications IA à haute sécurité avec des protocoles de gestion de clés résistants au quantique.
 #4.15.3    Niveau: 3    Rôle: D/V
 Vérifiez que les cadres d'agilité cryptographique permettent une migration rapide vers de nouveaux algorithmes post-quantiques avec une rotation automatisée des certificats et des clés.
 #4.15.4    Niveau: 3    Rôle: V
 Vérifiez que la modélisation des menaces quantiques évalue la vulnérabilité de l'infrastructure IA aux attaques quantiques avec des calendriers de migration documentés et des évaluations des risques.
 #4.15.5    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes cryptographiques hybrides classique-quantique offrent une défense en profondeur pendant la période de transition quantique avec une surveillance des performances.

---

### C4.17 Infrastructure à connaissance zéro

Implémentez des systèmes de preuve à divulgation nulle de connaissance pour la vérification et l’authentification de l’IA préservant la confidentialité, sans révéler d’informations sensibles.

 #4.17.1    Niveau: 3    Rôle: D/V
 Vérifiez que les preuves à divulgation nulle de connaissance (ZK-SNARKs, ZK-STARKs) valident l’intégrité du modèle IA et la provenance de l’entraînement sans exposer les poids du modèle ni les données d’entraînement.
 #4.17.2    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes d'authentification basés sur ZK permettent une vérification de l'utilisateur préservant la confidentialité pour les services d'IA sans révéler d'informations liées à l'identité.
 #4.17.3    Niveau: 3    Rôle: D/V
 Vérifiez que les protocoles d'intersection d'ensembles privés (PSI) permettent une correspondance sécurisée des données pour l'IA fédérée sans exposer les ensembles de données individuels.
 #4.17.4    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes d'apprentissage automatique à connaissance zéro (ZKML) permettent des inférences d'IA vérifiables avec une preuve cryptographique de calcul correct.
 #4.17.5    Niveau: 3    Rôle: D/V
 Vérifiez que les ZK-rollups offrent un traitement des transactions IA évolutif et respectueux de la vie privée, avec une vérification par lots et une réduction de la charge computationnelle.

---

### C4.18 Prévention des attaques par canal auxiliaire

Protégez l'infrastructure IA contre les attaques par canal auxiliaire basées sur le timing, la puissance, l'électromagnétisme et le cache qui pourraient divulguer des informations sensibles.

 #4.18.1    Niveau: 3    Rôle: D/V
 Vérifiez que le temps d'inférence de l'IA est normalisé en utilisant des algorithmes à temps constant et un bourrage afin de prévenir les attaques d'extraction de modèle basées sur le temps.
 #4.18.2    Niveau: 3    Rôle: D/V
 Vérifiez que la protection contre l'analyse de puissance comprend l'injection de bruit, le filtrage de la ligne d'alimentation et les schémas d'exécution aléatoires pour le matériel d'IA.
 #4.18.3    Niveau: 3    Rôle: D/V
 Vérifiez que l'atténuation des canaux auxiliaires basés sur le cache utilise le partitionnement du cache, la randomisation et les instructions de vidage pour empêcher la fuite d'informations.
 #4.18.4    Niveau: 3    Rôle: D/V
 Vérifiez que la protection contre les émissions électromagnétiques comprend un blindage, un filtrage des signaux et un traitement aléatoire pour prévenir les attaques de type TEMPEST.
 #4.18.5    Niveau: 3    Rôle: D/V
 Vérifiez que les défenses contre les canaux latéraux microarchitecturaux incluent des contrôles d’exécution spéculative et l’obscurcissement des modèles d’accès mémoire.

---

### C4.19 Sécurité du matériel IA neuromorphique et spécialisé

Sécuriser les architectures matérielles émergentes de l'IA, y compris les puces neuromorphiques, les FPGA, les ASIC personnalisés et les systèmes informatiques optiques.

 #4.19.1    Niveau: 3    Rôle: D/V
 Vérifiez que la sécurité des puces neuromorphiques inclut le cryptage des motifs de pics, la protection des poids synaptiques et la validation des règles d’apprentissage basées sur le matériel.
 #4.19.2    Niveau: 3    Rôle: D/V
 Vérifiez que les accélérateurs d'IA basés sur FPGA mettent en œuvre le chiffrement des bitstreams, des mécanismes anti-contrefaçon et le chargement sécurisé de la configuration avec des mises à jour authentifiées.
 #4.19.3    Niveau: 3    Rôle: D/V
 Vérifiez que la sécurité ASIC personnalisée inclut des processeurs de sécurité intégrés, une racine de confiance matérielle et un stockage sécurisé des clés avec détection d'altération.
 #4.19.4    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes de calcul optique mettent en œuvre un chiffrement optique quantique-sûr, un commutateur photonique sécurisé et un traitement du signal optique protégé.
 #4.19.5    Niveau: 3    Rôle: D/V
 Vérifiez que les puces d’IA hybrides analogiques-numériques incluent un calcul analogique sécurisé, un stockage protégé des poids, et une conversion analogique-numérique authentifiée.

---

### C4.20 Infrastructure de calcul préservant la confidentialité

Mettre en œuvre des contrôles d'infrastructure pour le calcul respectueux de la vie privée afin de protéger les données sensibles lors du traitement et de l'analyse par l'IA.

 #4.20.1    Niveau: 3    Rôle: D/V
 Vérifiez que l'infrastructure de chiffrement homomorphe permet le calcul chiffré sur des charges de travail IA sensibles avec une vérification d'intégrité cryptographique et une surveillance des performances.
 #4.20.2    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes de récupération d'informations privées permettent des requêtes de base de données sans révéler les schémas de requête grâce à la protection cryptographique des schémas d'accès.
 #4.20.3    Niveau: 3    Rôle: D/V
 Vérifiez que les protocoles de calcul multipartite sécurisé permettent une inférence IA préservant la confidentialité sans exposer les entrées individuelles ni les calculs intermédiaires.
 #4.20.4    Niveau: 3    Rôle: D/V
 Vérifiez que la gestion des clés préservant la confidentialité comprend la génération distribuée de clés, la cryptographie à seuil, et la rotation sécurisée des clés avec une protection matérielle garantie.
 #4.20.5    Niveau: 3    Rôle: D/V
 Vérifiez que les performances de calcul préservant la confidentialité sont optimisées grâce au traitement par lots, à la mise en cache et à l'accélération matérielle tout en maintenant les garanties de sécurité cryptographique.

 4.9.14.9.2    1: 2    D/V: D/V
 Vérifier que les déploiements multi-cloud utilisent des normes d’identité fédérée (par exemple, OIDC, SAML) avec une application centralisée des politiques à travers les fournisseurs.
 4.9.14.9.3    1: 2    D/V: D/V
 Vérifier que les transferts de données inter-cloud et hybrides utilisent un chiffrement de bout en bout avec des clés gérées par le client et qu'ils respectent les exigences de résidence des données selon la juridiction.
 4.9.14.9.1    1: 1    D/V: D/V
 Vérifiez que l’intégration du stockage cloud utilise un chiffrement de bout en bout avec une gestion des clés contrôlée par l’agent.
 4.9.14.9.2    1: 2    D/V: D/V
 Vérifier que les frontières de sécurité du déploiement hybride sont clairement définies avec des canaux de communication chiffrés.

