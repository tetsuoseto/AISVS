## Frontispice

### À propos de la norme

La Norme de vérification de la sécurité de l'intelligence artificielle (AISVS) est un catalogue piloté par la communauté d'exigences de sécurité que les scientifiques des données, les ingénieurs MLOps, les architectes logiciels, les développeurs, les testeurs, les professionnels de la sécurité, les fournisseurs d'outils, les régulateurs et les consommateurs peuvent utiliser pour concevoir, construire, tester et vérifier des systèmes et applications dotés d'une IA fiable. Elle fournit un langage commun pour spécifier les contrôles de sécurité tout au long du cycle de vie de l'IA—from la collecte des données et du développement des modèles à la mise en production et à la surveillance continue—from afin que les organisations puissent mesurer et améliorer la résilience, la vie privée et la sécurité de leurs solutions d'IA.

### Droits d'auteur et licence

Version 0.1 (Première ébauche publique - Travail en cours), 2025  

![license](images/license.png)
Droits d’auteur © 2025 The AISVS Project.  

Publié sous laCreative Commons Attribution‑ShareAlike 4.0 International License.
Pour toute réutilisation ou distribution, vous devez communiquer clairement les termes de la licence de cette œuvre aux autres.

### Responsables de projet

Jim Manico
Aras “Russ” Memisyazici

### Contributeurs et réviseurs

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS est une norme entièrement nouvelle conçue spécifiquement pour relever les défis de sécurité uniques des systèmes d'intelligence artificielle. Bien qu'elle s'inspire des meilleures pratiques de sécurité plus générales, chaque exigence d'AISVS a été développée de zéro pour refléter le paysage des menaces propres à l'IA et aider les organisations à construire des solutions d'IA plus sûres et plus résilientes.

## Préface

Bienvenue à la norme de vérification de la sécurité de l'intelligence artificielle (AISVS) version 1.0!

### Introduction

Établi en 2025 grâce à un effort communautaire collaboratif, AISVS définit les exigences de sécurité à prendre en compte lors de la conception, du développement, du déploiement et de l'exploitation des modèles d'IA modernes, des pipelines et des services basés sur l'IA.

AISVS v1.0 représente le travail combiné de ses responsables de projet, du groupe de travail et des contributeurs de la communauté au sens large, afin de produire une base pragmatique et testable pour sécuriser les systèmes d'IA.

Notre objectif avec cette version est de rendre AISVS facile à adopter tout en restant laser‑focused sur son périmètre défini et en répondant au paysage des risques en évolution rapide propre à l'IA.

### Objectifs clés pour AISVS version 1.0

La version 1.0 sera créée avec plusieurs principes directeurs.

#### Portée bien définie

Chaque exigence doit être alignée sur le nom et la mission d'AISVS:

Intelligence artificielle – les contrôles opèrent au niveau de la couche IA/ML (données, modèle, pipeline ou inférence) et relèvent de la responsabilité des professionnels de l’IA.
Sécurité – les exigences atténuent directement les risques identifiés de sécurité, de confidentialité ou de sûreté.
Vérification – Le langage est rédigé de façon à ce que la conformité puisse être validée de manière objective.
Norme – Les sections suivent une structure et une terminologie cohérentes pour former une référence cohérente.
​
---

En suivant AISVS, les organisations peuvent évaluer et renforcer systématiquement la posture de sécurité de leurs solutions d'IA, favorisant une culture d'ingénierie de l'IA sécurisée.

## En utilisant l'AISVS

La norme de vérification de la sécurité de l'intelligence artificielle (AISVS) définit les exigences de sécurité pour les applications et services d'IA modernes, en mettant l'accent sur les aspects qui relèvent du contrôle des développeurs d'applications.

L'AISVS est destiné à toute personne développant ou évaluant la sécurité des applications d'IA, notamment les développeurs, les architectes, les ingénieurs de sécurité et les auditeurs. Ce chapitre présente la structure et l'utilisation de l'AISVS, y compris ses niveaux de vérification et les cas d'utilisation prévus.

### Niveaux de vérification de la sécurité de l'IA

L'AISVS définit trois niveaux croissants de vérification de la sécurité. Chaque niveau ajoute de la profondeur et de la complexité, permettant aux organisations d'adapter leur posture de sécurité au niveau de risque de leurs systèmes d’IA.

Les organisations peuvent commencer au niveau 1 et adopter progressivement des niveaux supérieurs à mesure que la maturité en matière de sécurité et l'exposition aux menaces augmentent.

#### Définition des niveaux

Chaque exigence dans AISVS v1.0 est assignée à l'un des niveaux suivants:

 Exigences de niveau 1

Le niveau 1 comprend les exigences de sécurité les plus critiques et fondamentales. Celles-ci se concentrent sur la prévention des attaques courantes qui ne dépendent pas d'autres préconditions ou vulnérabilités. La plupart des contrôles du niveau 1 sont soit simples à mettre en œuvre, soit suffisamment essentiels pour justifier l'effort.

 Exigences du niveau 2

Le niveau 2 aborde des attaques plus avancées ou moins courantes, ainsi que des défenses en couches contre les menaces généralisées. Ces exigences peuvent impliquer une logique plus complexe ou viser des prérequis d'attaque spécifiques.

 Exigences du niveau 3

Le niveau 3 comprend des contrôles qui sont généralement plus difficiles à mettre en œuvre ou dont l'applicabilité est situationnelle. Ils représentent souvent des mécanismes de défense-en-profondeur ou des mesures d'atténuation contre des attaques de niche, ciblées ou à haute complexité.

#### Rôle (D/V)

Chaque exigence AISVS est marquée selon le public cible principal :

D – exigences axées sur les développeurs
V – Exigences axées sur le vérificateur/auditeur
D/V – Pertinent à la fois pour les développeurs et les vérificateurs

## C1 Gouvernance des données d'entraînement et gestion des biais

### Objectif de contrôle

Les données d'entraînement doivent être sourcées, gérées et maintenues de manière à préserver leur provenance, leur sécurité, leur qualité et leur équité. Cela permet de respecter les obligations légales et de réduire les risques de biais, d'empoisonnement ou de violations de la vie privée qui apparaissent pendant l'entraînement et qui pourraient affecter l'ensemble du cycle de vie de l'IA.

---

### C1.1 Provenance des données d'entraînement

Maintenir un inventaire vérifiable de l’ensemble des jeux de données, n’accepter que des sources fiables et enregistrer chaque changement pour assurer l’auditabilité.

 #1.1.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'un inventaire à jour de chaque source de données d'entraînement (origine, responsable/gestionnaire, licence, méthode de collecte, contraintes d'utilisation prévues et historique du traitement) est maintenu à jour.
 #1.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les processus de traitement des données d'entraînement excluent les caractéristiques, attributs ou champs inutiles (par exemple, métadonnées inutilisées, PII sensibles, données de test divulguées).
 #1.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que tous les changements apportés au jeu de données sont soumis à un flux d'approbation enregistré.
 #1.1.4    Niveau: 3    Rôle: D/V
 Vérifiez que les ensembles de données ou leurs sous-ensembles portent un filigrane ou une empreinte numérique, lorsque cela est faisable.

---

### C1.2 Sécurité et intégrité des données d'entraînement

Restreindre l'accès aux données d'entraînement, les chiffrer au repos et en transit, et vérifier leur intégrité pour prévenir l'altération, le vol ou l'empoisonnement des données.

 #1.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les contrôles d'accès protègent le stockage des données d'entraînement et les pipelines.
 #1.2.2    Niveau: 2    Rôle: D/V
 Vérifiez que tout accès aux données d'entraînement est enregistré, y compris l'utilisateur, l'heure et l'action.
 #1.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les ensembles de données d’entraînement sont chiffrés en transit et au repos, en utilisant des algorithmes cryptographiques conformes aux normes de l’industrie et des pratiques de gestion des clés.
 #1.2.4    Niveau: 2    Rôle: D/V
 Vérifiez que des hachages cryptographiques ou des signatures numériques sont utilisés pour garantir l'intégrité des données lors du stockage et du transfert des données d'entraînement.
 #1.2.5    Niveau: 2    Rôle: D/V
 Vérifiez que les techniques de détection automatisées sont mises en œuvre pour prévenir les modifications non autorisées ou la corruption des données d'entraînement.
 #1.2.6    Niveau: 2    Rôle: D/V
 Vérifiez que les données d'entraînement obsolètes sont purgées de manière sécurisée ou anonymisées.
 #1.2.7    Niveau: 3    Rôle: D/V
 Vérifier que toutes les versions des jeux de données d'entraînement sont identifiables de manière unique, stockées de manière immuable et vérifiables afin de permettre le retour en arrière et l'analyse médico-légale.

---

### C1.3 Qualité, intégrité et sécurité de l'étiquetage des données d'entraînement

Protéger les étiquettes et exiger une revue technique pour les données critiques.

 #1.3.1    Niveau: 2    Rôle: D/V
 Vérifier que des hachages cryptographiques ou des signatures numériques sont appliqués aux artefacts d'étiquetage afin d'en assurer l'intégrité et l'authenticité.
 #1.3.2    Niveau: 2    Rôle: D/V
 Vérifiez que les interfaces d’étiquetage et les plateformes imposent des contrôles d’accès robustes, conservent des journaux d’audit inviolables de toutes les activités d’étiquetage et protègent contre les modifications non autorisées.
 #1.3.3    Niveau: 3    Rôle: D/V
 Vérifiez que les informations sensibles contenues dans les étiquettes sont masquées, anonymisées ou chiffrées au niveau des champs de données, au repos et en transit.

---

### C1.4 Qualité des données d'entraînement et assurance de la sécurité

Combinez la validation automatisée, les vérifications manuelles ponctuelles et les actions correctives consignées pour garantir la fiabilité de l'ensemble de données.

 #1.4.1    Niveau: 1    Rôle: D
 Vérifiez que les tests automatisés détectent les erreurs de format et les valeurs nulles à chaque ingestion ou transformation de données significative.
 #1.4.2    Niveau: 2    Rôle: D/V
 Vérifiez que les pipelines d'entraînement et de fine-tuning des LLM intègrent la détection d'empoisonnement et la validation de l'intégrité des données (par exemple, des méthodes statistiques, la détection d'outliers et l'analyse des embeddings) afin d'identifier les attaques d'empoisonnement potentielles (par exemple basculement d'étiquettes, insertion de déclencheurs de porte dérobée, commandes de changement de rôle, attaques d'instances influentes) ou des corruptions involontaires des données d'entraînement.
 #1.4.3    Niveau: 3    Rôle: D/V
 Vérifiez que des défenses appropriées, telles que l'entraînement adversarial (utilisant des exemples adverses générés), l'augmentation des données avec des entrées perturbées ou des techniques d'optimisation robustes, sont mises en œuvre et ajustées pour les modèles pertinents en fonction de l'évaluation des risques.
 #1.4.4    Niveau: 2    Rôle: D/V
 Vérifiez que les étiquettes générées automatiquement (par exemple, via des modèles de langage de grande taille (LLMs) ou par supervision faible) sont soumises à des seuils de confiance et à des vérifications de cohérence afin de détecter des étiquettes hallucinées, trompeuses ou à faible niveau de confiance.
 #1.4.5    Niveau: 3    Rôle: D
 Vérifiez que les tests automatisés détectent les déséquilibres des étiquettes à chaque ingestion ou transformation de données significative.

---

### C1.5 Lignée des données et traçabilité

Suivre l'intégralité du parcours de chaque point de données, de la source à l'entrée du modèle, pour l'auditabilité et la réponse aux incidents.

 #1.5.1    Niveau: 2    Rôle: D/V
 Vérifiez que la lignée de chaque point de données, y compris toutes les transformations, augmentations et fusions, est enregistrée et peut être reconstruite.
 #1.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les enregistrements de traçabilité sont immuables, stockés de manière sécurisée et accessibles pour les audits.
 #1.5.3    Niveau: 2    Rôle: D/V
 Vérifier que la traçabilité des données couvre les données synthétiques générées via des techniques de préservation de la vie privée ou génératives et que toutes les données synthétiques soient clairement étiquetées et distinguables des données réelles tout au long du flux de traitement.

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

## C2 Validation des entrées utilisateur

### Objectif de contrôle

Une validation robuste des entrées utilisateur constitue une défense de première ligne contre certaines des attaques les plus dommageables sur les systèmes d'IA. Les attaques d'injection de prompts peuvent contourner les instructions du système, divulguer des données sensibles ou orienter le modèle vers un comportement qui n'est pas autorisé. À moins que des filtres dédiés et des hiérarchies d'instructions soient en place, les recherches montrent que des jailbreaks « multi-shot » qui exploitent des fenêtres de contexte très longues seront efficaces. De plus, des attaques de perturbation adversarielle subtiles — telles que des échanges d'homoglyphes ou leetspeak — peuvent silencieusement modifier les décisions d'un modèle.

---

### C2.1 Défense contre l'injection de prompt

L'injection de prompt est l'un des principaux risques pour les systèmes d'IA. Les défenses contre cette tactique utilisent une combinaison de filtres de motifs statiques, de classificateurs dynamiques et de l'application de la hiérarchie des instructions.

 #2.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que les entrées des utilisateurs sont filtrées par rapport à une bibliothèque mise à jour en continu de motifs d'injection de prompts connus (mots-clés de jailbreak, "ignorer le précédent", chaînes de jeu de rôle, attaques HTML/URL indirectes).
 #2.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que le système fait respecter une hiérarchie des instructions selon laquelle les messages système ou développeur prévalent sur les instructions de l'utilisateur, même après l'extension de la fenêtre de contexte.
 #2.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que les tests d'évaluation adversariaux (par exemple, les prompts de l'équipe rouge "many-shot") sont exécutés avant chaque version d'un modèle ou d'un gabarit de prompt, avec des seuils de réussite et des bloqueurs automatiques pour les régressions.
 #2.1.4    Niveau: 2    Rôle: D
 Vérifiez que les requêtes provenant de contenus tiers (pages Web, PDFs, e-mails) sont nettoyées dans un contexte d’analyse isolé avant d’être concaténées dans la requête principale.
 #2.1.5    Niveau: 3    Rôle: D/V
 Vérifiez que toutes les mises à jour des règles de filtrage des prompts, les versions des modèles de classificateur et les modifications de la liste de blocage sont sous contrôle de versions et vérifiables.

---

### C2.2 Résistance aux exemples adversaires

Les modèles de Traitement Automatique du Langage Naturel (TALN) restent vulnérables à des perturbations subtiles au niveau des caractères ou des mots, que les humains manquent souvent mais que les modèles ont tendance à mal classer.

 #2.2.1    Niveau: 1    Rôle: D
 Vérifiez que les étapes de normalisation d'entrée de base (Unicode NFC, correspondance d'homoglyphes, élimination des espaces) s'exécutent avant la tokenisation.
 #2.2.2    Niveau: 2    Rôle: D/V
 Vérifiez que la détection d'anomalies statistiques signale les entrées présentant une distance d'édition anormalement élevée par rapport aux normes de la langue, un nombre excessif de jetons répétés ou des distances d'embeddings anormales.
 #2.2.3    Niveau: 2    Rôle: D
 Vérifier que le pipeline d'inférence prend en charge des variantes de modèle adversarial-training–hardened optionnelles ou des couches de défense (par exemple, randomisation, distillation défensive) pour les points de terminaison à haut risque.
 #2.2.4    Niveau: 2    Rôle: V
 Vérifiez que les entrées susceptibles d'être adverses sont mises en quarantaine et consignées avec les charges utiles complètes (après la redaction des données à caractère personnel).
 #2.2.5    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques de robustesse (taux de réussite des suites d’attaques connues) sont suivies au fil du temps et que les régressions déclenchent un blocage de mise en production.

---

### C2.3 Validation du schéma, du type et de la longueur

Des attaques d’IA présentant des entrées malformées ou surdimensionnées peuvent provoquer des erreurs d’analyse, un débordement du prompt entre les champs et un épuisement des ressources. L’application stricte du schéma est également une condition préalable lors de l’exécution d’appels d’outils déterministes.

 #2.3.1    Niveau: 1    Rôle: D
 Vérifiez que chaque point de terminaison API ou appel de fonction définit un schéma d'entrée explicite (schéma JSON, Protobuf ou équivalent multimodal) et que les entrées sont validées avant l'assemblage du prompt.
 #2.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que les entrées dépassant les limites maximales de jetons ou d'octets sont rejetées avec une erreur sûre et ne sont jamais tronquées silencieusement.
 #2.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les vérifications de type (par exemple, les plages numériques, les valeurs d'énumération, les types MIME pour les images et les fichiers audio) sont appliquées côté serveur, et pas seulement dans le code côté client.
 #2.3.4    Niveau: 2    Rôle: D
 Vérifiez que les validateurs sémantiques (par exemple JSON Schema) s'exécutent en temps constant afin d'éviter le déni de service algorithmique.
 #2.3.5    Niveau: 3    Rôle: V
 Vérifiez que les échecs de validation sont enregistrés avec des extraits de charge utile masqués et des codes d'erreur non ambigus pour faciliter le triage de sécurité.

---

### C2.4 Vérification du contenu et des politiques

Les développeurs devraient être capables de détecter des invites syntaxiquement valides qui demandent un contenu interdit (tels que des instructions illicites, des discours de haine et des textes protégés par le droit d'auteur), puis empêcher leur propagation.

 #2.4.1    Niveau: 1    Rôle: D
 Vérifiez qu'un classificateur de contenu (zero-shot ou fine-tuned) évalue chaque entrée pour la violence, l'automutilation, la haine, le contenu sexuel et les demandes illégales, avec des seuils configurables.
 #2.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les entrées qui violent les politiques reçoivent des refus standardisés ou des sorties sûres afin qu'elles ne se propagent pas vers les appels LLM en aval.
 #2.4.3    Niveau: 2    Rôle: D
 Vérifiez que le modèle de filtrage ou l’ensemble de règles est réentraîné/mis à jour au moins tous les trimestres, en intégrant les motifs de jailbreak ou de contournement des politiques nouvellement observés.
 #2.4.4    Niveau: 2    Rôle: D
 Vérifiez que le filtrage respecte les politiques propres à l'utilisateur (âge, contraintes légales régionales) via des règles basées sur les attributs déterminées au moment de la demande.
 #2.4.5    Niveau: 3    Rôle: V
 Vérifier que les journaux de filtrage comprennent les scores de confiance du classificateur et les étiquettes de catégorie de politique, pour la corrélation avec le SOC et le rejouement futur par l'équipe rouge.

---

### C2.5 Limitation du débit d'entrée et prévention des abus

Les développeurs devraient prévenir les abus, l'épuisement des ressources et les attaques automatisées contre les systèmes d'IA en limitant les débits d'entrée et en détectant les schémas d'utilisation anormaux.

 #2.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les limites de taux par utilisateur, par adresse IP et par clé API sont appliquées à tous les points d'entrée.
 #2.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les limites de débit en rafale et de débit soutenu sont réglées pour prévenir les attaques par déni de service (DoS) et par force brute.
 #2.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que les comportements d'utilisation anormaux (par exemple des requêtes en rafale, une inondation d'entrées) déclenchent des blocages automatisés ou des mesures d'escalade.
 #2.5.4    Niveau: 3    Rôle: V
 Vérifier que les journaux de prévention des abus sont conservés et examinés pour détecter les motifs d'attaque émergents.

---

### C2.6 Validation d’entrée Multi-Modal

Les systèmes d'IA doivent inclure une validation robuste des entrées non textuelles (images, audio, fichiers) afin de prévenir l'injection, l'évasion ou l'abus de ressources.

 #2.6.1    Niveau: 1    Rôle: D
 Vérifiez que toutes les entrées non textuelles (images, audio et fichiers) sont validées par le type, la taille et le format avant le traitement.
 #2.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que les fichiers sont scannés à la recherche de logiciels malveillants et de charges utiles steganographiques avant l’ingestion.
 #2.6.3    Niveau: 2    Rôle: D/V
 Vérifiez que les entrées d'image et d'audio sont vérifiées pour des perturbations adversariales ou des motifs d'attaque connus.
 #2.6.4    Niveau: 3    Rôle: V
 Vérifiez que les échecs de validation des entrées multimodales sont consignés et déclenchent des alertes pour enquête.

---

### C2.7 Provenance des entrées et attribution

Les systèmes d'IA devraient permettre l'audit, le suivi des abus et la conformité en surveillant et en étiquetant les origines de toutes les entrées des utilisateurs.

 #2.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que toutes les entrées des utilisateurs sont associées à des métadonnées (ID utilisateur, session, source, horodatage, adresse IP) lors de l’ingestion.
 #2.7.2    Niveau: 2    Rôle: D/V
 Vérifier que les métadonnées de provenance sont conservées et auditées pour toutes les entrées traitées.
 #2.7.3    Niveau: 2    Rôle: D/V
 Vérifiez que les sources d’entrée anormales ou non fiables sont signalées et soumises à une surveillance renforcée ou à un blocage.

---

### C2.8 Détection des menaces adaptatives en temps réel

Les développeurs devraient utiliser des systèmes avancés de détection des menaces pour l'IA qui s'adaptent à de nouveaux motifs d'attaque et offrent une protection en temps réel grâce à une correspondance de motifs compilée.

 #2.8.1    Niveau: 1    Rôle: D/V
 Vérifiez que les motifs de détection des menaces sont compilés dans des moteurs d'expressions régulières optimisés pour un filtrage en temps réel à haute performance avec un impact de latence minimal.
 #2.8.2    Niveau: 1    Rôle: D/V
 Vérifiez que les systèmes de détection des menaces maintiennent des bibliothèques de motifs distinctes pour différentes catégories de menaces (injection de prompt, contenu nuisible, données sensibles, commandes système).
 #2.8.3    Niveau: 2    Rôle: D/V
 Vérifiez que la détection adaptative des menaces intègre des modèles d'apprentissage automatique qui ajustent la sensibilité aux menaces en fonction de la fréquence des attaques et des taux de réussite.
 #2.8.4    Niveau: 2    Rôle: D/V
 Vérifiez que les flux d'intelligence sur les menaces en temps réel mettent automatiquement à jour les bibliothèques de signatures avec les nouvelles signatures d'attaque et les IOCs (Indicateurs de compromission).
 #2.8.5    Niveau: 3    Rôle: D/V
 Vérifier que les taux de faux positifs de la détection des menaces sont surveillés en continu et que la spécificité des motifs est ajustée automatiquement afin de minimiser les interférences avec les cas d'utilisation légitimes.
 #2.8.6    Niveau: 3    Rôle: D/V
 Vérifiez que l’analyse contextuelle des menaces prend en compte la source d’entrée, les modèles de comportement des utilisateurs et l’historique des sessions afin d’améliorer la précision de la détection.
 #2.8.7    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques de performance de la détection des menaces (taux de détection, latence de traitement, utilisation des ressources) sont surveillées et optimisées en temps réel.

---

### C2.9 Multi-Modal pipeline de validation de sécurité

Les développeurs devraient fournir une validation de sécurité pour le texte, les images, l'audio et d'autres modalités d'entrée de l'IA, avec des types spécifiques de détection des menaces et d'isolation des ressources.

 #2.9.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque modalité d'entrée dispose de validateurs de sécurité dédiés avec des motifs de menace documentés (texte : injection de prompt, images : stéganographie, audio : attaques par spectrogrammes) et des seuils de détection.
 #2.9.2    Niveau: 2    Rôle: D/V
 Vérifier que les entrées multimodales sont traitées dans des environnements isolés (bac à sable) avec des limites de ressources définies (mémoire, CPU, temps de traitement) spécifiques à chaque type de modalité et documentées dans les politiques de sécurité.
 #2.9.3    Niveau: 2    Rôle: D/V
 Vérifiez que la détection d’attaques inter-modales identifie des attaques coordonnées couvrant plusieurs types d’entrée (par exemple, des charges steganographiques dans les images combinées à une injection de prompt dans le texte) avec des règles de corrélation et la génération d’alertes.
 #2.9.4    Niveau: 3    Rôle: D/V
 Vérifiez que les défaillances de validation multimodale déclenchent une journalisation détaillée incluant toutes les modalités d'entrée, les résultats de la validation, les scores de menace et l'analyse de corrélation avec des formats de journalisation structurés pour l'intégration SIEM.
 #2.9.5    Niveau: 3    Rôle: D/V
 Vérifiez que les classificateurs de contenu spécifiques à chaque modalité sont mis à jour selon des plannings documentés (au moins trimestriels) avec de nouveaux motifs de menace, des exemples adversariaux et des benchmarks de performance maintenus au-dessus des seuils de référence.

---

### Références

LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security
Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
$PDF$ OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
Easily enforcing valid JSON schema following – API
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## C3 Gestion du cycle de vie des modèles et contrôle des changements

### Objectif de contrôle

Les systèmes d'IA doivent mettre en œuvre des processus de contrôle des modifications qui empêchent des modifications non autorisées ou dangereuses du modèle d'atteindre la production. Ce contrôle garantit l'intégrité du modèle tout au long du cycle de vie--du développement au déploiement jusqu'à la mise hors service--ce qui permet une réponse rapide aux incidents et assure la traçabilité et la responsabilité de l'ensemble des changements.

Objectif de sécurité principal: Seuls les modèles autorisés et validés atteignent la production en utilisant des processus contrôlés qui maintiennent l'intégrité, la traçabilité et la récupérabilité.

---

### C3.1 Autorisation et Intégrité du Modèle

Seuls les modèles autorisés dont l'intégrité est vérifiée atteignent les environnements de production.

 #3.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les artefacts du modèle (poids, configurations, tokeniseurs) sont signés cryptographiquement par des entités autorisées avant le déploiement.
 #3.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que l'intégrité du modèle est validée au moment du déploiement et que les échecs de la vérification de signature empêchent le chargement du modèle.
 #3.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que les enregistrements de provenance du modèle incluent l'identité de l'entité autorisante, les sommes de contrôle des données d'entraînement, les résultats des tests de validation avec le statut réussite/échec et un horodatage de création.
 #3.1.4    Niveau: 2    Rôle: D/V
 Vérifiez que tous les artefacts du modèle utilisent le versionnage sémantique (MAJOR.MINOR.PATCH) avec des critères documentés précisant quand chaque composant de la version s'incrémente.
 #3.1.5    Niveau: 2    Rôle: V
 Vérifiez que le traçage des dépendances maintient un inventaire en temps réel qui permet une identification rapide de tous les systèmes consommateurs.

---

### C3.2 Validation et tests du modèle

Les modèles doivent passer les validations de sécurité et de sûreté définies avant le déploiement.

 #3.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les modèles subissent des tests de sécurité automatisés comprenant la validation des entrées, la sanitisation des sorties et des évaluations de sécurité avec des seuils de réussite/échec organisationnels préalablement convenus avant le déploiement.
 #3.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que les échecs de validation bloquent automatiquement le déploiement du modèle après l'approbation explicite d'une dérogation par le personnel autorisé pré-désigné, avec des justifications commerciales documentées.
 #3.2.3    Niveau: 2    Rôle: V
 Vérifiez que les résultats de test sont signés cryptographiquement et liés de manière immuable au hash de la version du modèle spécifique en cours de validation.
 #3.2.4    Niveau: 2    Rôle: D/V
 Vérifiez que les déploiements d'urgence nécessitent une évaluation des risques de sécurité documentée et l'approbation d'une autorité de sécurité prédésignée, dans des délais préalablement convenus.

---

### C3.3 Déploiement contrôlé et retour arrière

Les déploiements de modèles doivent être contrôlés, surveillés et réversibles.

 #3.3.1    Niveau: 1    Rôle: D
 Vérifiez que les déploiements en production mettent en œuvre des mécanismes de déploiement progressif (déploiements canari, déploiements bleu-vert) avec des déclencheurs de retour arrière automatisés basés sur des taux d'erreur convenus à l'avance, des seuils de latence ou des critères d'alerte de sécurité.
 #3.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que les capacités de rollback restaurent l'état complet du modèle (poids, configurations, dépendances) de manière atomique dans des fenêtres temporelles organisationnelles pré-définies.
 #3.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les processus de déploiement valident les signatures cryptographiques et calculent les sommes de contrôle d’intégrité avant l’activation du modèle, et que le déploiement échoue en cas de discordance.
 #3.3.4    Niveau: 2    Rôle: D/V
 Vérifier que les capacités d'arrêt d'urgence du modèle peuvent désactiver les points de terminaison du modèle dans des délais de réponse pré-définis, soit via des disjoncteurs automatiques, soit via des interrupteurs d'arrêt manuels.
 #3.3.5    Niveau: 2    Rôle: V
 Vérifiez que les artefacts de rollback (versions précédentes du modèle, configurations, dépendances) sont conservés conformément aux politiques organisationnelles avec un stockage immuable pour la réponse aux incidents.

---

### C3.4 Traçabilité des changements et audit

Tous les changements du cycle de vie du modèle doivent être traçables et audités.

 #3.4.1    Niveau: 1    Rôle: V
 Vérifiez que toutes les modifications du modèle (déploiement, configuration, retrait) génèrent des enregistrements d'audit immuables comprenant un horodatage, l'identité d'un acteur authentifié, un type de modification et les états avant/après.
 #3.4.2    Niveau: 2    Rôle: D/V
 Vérifiez que l'accès au journal d'audit nécessite une autorisation appropriée et que toutes les tentatives d'accès sont enregistrées avec l'identité de l'utilisateur et un horodatage.
 #3.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que les modèles d'invite et les messages système sont sous contrôle de version dans des dépôts Git, avec une revue de code obligatoire et une approbation par des réviseurs désignés avant le déploiement.
 #3.4.4    Niveau: 2    Rôle: V
 Vérifiez que les enregistrements d'audit contiennent des détails suffisants (empreintes du modèle, instantanés de configuration, versions des dépendances) pour permettre une reconstruction complète de l'état du modèle pour tout horodatage dans la période de rétention.

---

### C3.5 Bonnes pratiques de développement sécurisé

Les processus de développement et d'entraînement des modèles doivent suivre des pratiques sécurisées afin d'éviter toute compromission.

 #3.5.1    Niveau: 1    Rôle: D
 Vérifiez que les environnements de développement, de test et de production du modèle sont séparés physiquement ou logiquement. Ils ne disposent pas d'infrastructure partagée, de contrôles d'accès distincts et de stockages de données isolés.
 #3.5.2    Niveau: 1    Rôle: D
 Vérifiez que l'entraînement et l'ajustement fin du modèle se déroulent dans des environnements isolés avec un accès réseau contrôlé.
 #3.5.3    Niveau: 1    Rôle: D/V
 Vérifiez que les sources de données d'entraînement sont validées par des contrôles d'intégrité et authentifiées via des sources de confiance avec une traçabilité documentée de la chaîne de custodie avant leur utilisation dans le développement du modèle.
 #3.5.4    Niveau: 2    Rôle: D
 Vérifiez que les artefacts de développement du modèle (hyperparamètres, scripts d'entraînement, fichiers de configuration) sont stockés dans le contrôle de version et nécessitent une revue par les pairs avant d'être utilisés pour l'entraînement.

---

### C3.6 Mise hors service du modèle et décommissionnement

Les modèles doivent être retirés de manière sécurisée lorsqu'ils ne sont plus nécessaires ou lorsque des problèmes de sécurité sont identifiés.

 #3.6.1    Niveau: 1    Rôle: D
 Vérifiez que les processus de retrait des modèles analysent automatiquement les graphes de dépendances, identifient tous les systèmes consommateurs et fournissent des périodes de préavis convenues à l'avance avant la mise hors service.
 #3.6.2    Niveau: 1    Rôle: D/V
 Vérifiez que les artefacts des modèles retirés sont effacés en toute sécurité à l'aide d'un effacement cryptographique ou d'un écrasement à plusieurs passes, conformément aux politiques de rétention des données documentées, avec des certificats de destruction vérifiés.
 #3.6.3    Niveau: 2    Rôle: V
 Vérifiez que les événements de retrait du modèle sont enregistrés avec horodatage et identité de l'acteur, et que les signatures du modèle sont révoquées pour empêcher toute réutilisation.
 #3.6.4    Niveau: 2    Rôle: D/V
 Vérifier que la mise hors service d'urgence du modèle peut désactiver l'accès au modèle dans les délais de réponse d'urgence préétablis via des interrupteurs d'arrêt automatisés si des vulnérabilités de sécurité critiques sont découvertes.

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

## Infrastructure C4, Configuration et Déploiement Sécurité

### Objectif de contrôle

L'infrastructure d'IA doit être durcie contre l'élévation de privilèges, l'altération de la chaîne d'approvisionnement et le mouvement latéral par une configuration sécurisée, une isolation d'exécution, des pipelines de déploiement fiables et une surveillance complète. Seuls les composants et configurations d'infrastructure autorisés et validés atteignent la production par des processus contrôlés qui maintiennent la sécurité, l'intégrité et l'auditabilité.

Objectif de sécurité principal : Seuls les composants d'infrastructure signés cryptographiquement et scannés pour les vulnérabilités atteignent la production via des pipelines de validation automatisés qui appliquent des politiques de sécurité et maintiennent des traces d'audit immuables.

---

### C4.1 Isolement de l'environnement d'exécution

Prévenir les évasions de conteneurs et l’élévation de privilèges grâce aux primitives d’isolement au niveau du noyau et aux contrôles d’accès obligatoires.

 #4.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les conteneurs d'IA suppriment toutes les capacités Linux, à l'exception de CAP_SETUID, CAP_SETGID et des capacités explicitement requises documentées dans les référentiels de sécurité.
 #4.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les profils seccomp bloquent tous les appels système, à l'exception de ceux figurant sur des listes d'autorisation préapprouvées, et que les violations entraînent l'arrêt du conteneur et génèrent des alertes de sécurité.
 #4.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que les charges de travail d'IA s'exécutent avec des systèmes de fichiers racine en lecture seule, tmpfs pour les données temporaires et des volumes nommés pour les données persistantes, avec les options de montage noexec imposées.
 #4.1.4    Niveau: 2    Rôle: D/V
 Vérifiez que la surveillance d’exécution basée sur eBPF (Falco, Tetragon ou équivalent) détecte les tentatives d’élévation de privilèges et tue automatiquement les processus malveillants dans les délais de réponse imposés par l’organisation.
 #4.1.5    Niveau: 3    Rôle: D/V
 Vérifiez que les charges de travail d’IA à haut risque s’exécutent dans des environnements isolés au niveau matériel (Intel TXT, AMD SVM, ou nœuds bare-metal dédiés) avec vérification d'attestation.

---

### C4.2 Pipelines de construction et de déploiement sécurisés

Assurer l'intégrité cryptographique et la sécurité de la chaîne d'approvisionnement grâce à des builds reproductibles et à des artefacts signés.

 #4.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que l'infrastructure-as-code est analysée par des outils (tfsec, Checkov ou Terrascan) à chaque commit, et bloquez les fusions en cas de résultats de gravité critique ou élevée.
 #4.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que les builds de conteneurs sont reproductibles avec des hachages SHA256 identiques d'un build à l'autre et générez des attestations de provenance SLSA Niveau 3 signées avec Sigstore.
 #4.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les images de conteneurs intègrent des SBOM CycloneDX ou SPDX et sont signées avec Cosign avant le push vers le registre, les images non signées étant rejetées au déploiement.
 #4.2.4    Niveau: 2    Rôle: D/V
 Vérifiez que les pipelines CI/CD utilisent des jetons OIDC provenant de HashiCorp Vault, des rôles AWS IAM ou de l'identité gérée Azure, avec des durées de validité qui ne dépassent pas les limites de la politique de sécurité de l'organisation.
 #4.2.5    Niveau: 2    Rôle: D/V
 Vérifiez que les signatures Cosign et la provenance SLSA soient validées au cours du processus de déploiement avant l'exécution du conteneur et que les erreurs de vérification entraînent l'échec du déploiement.
 #4.2.6    Niveau: 2    Rôle: D/V
 Vérifiez que les environnements de build fonctionnent dans des conteneurs éphémères ou des machines virtuelles (VMs) sans stockage persistant et avec une isolation réseau par rapport aux VPC de production.

---

### C4.3 Sécurité du réseau et contrôle d'accès

Implémenter le réseau zéro-confiance avec des politiques de refus par défaut et des communications chiffrées.

 #4.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les politiques réseau de Kubernetes, ou tout équivalent, mettent en œuvre un refus par défaut du trafic entrant et sortant avec des règles explicites d'autorisation pour les ports requis (443, 8080, etc.).
 #4.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que SSH (port 22), RDP (port 3389) et les points de terminaison des métadonnées du cloud (169.254.169.254) sont bloqués ou nécessitent une authentification basée sur des certificats.
 #4.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que le trafic sortant est filtré via des proxies HTTP/HTTPS (Squid, Istio ou passerelles NAT cloud) avec des listes blanches de domaines et que les requêtes bloquées sont enregistrées.
 #4.3.4    Niveau: 2    Rôle: D/V
 Vérifiez que la communication entre services utilise le TLS mutuel avec des certificats renouvelés conformément à la politique organisationnelle et que la validation des certificats est appliquée (aucun drapeau skip-verify).
 #4.3.5    Niveau: 2    Rôle: D/V
 Vérifiez que l'infrastructure d'IA fonctionne dans des VPCs/VNets dédiés, sans accès direct à Internet, et ne communique que via des passerelles NAT ou des hôtes bastion.

---

### C4.4 Secrets et gestion des clés cryptographiques

Protéger les identifiants grâce à un stockage protégé par le matériel et à une rotation automatique avec un accès Zero Trust.

 #4.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que les secrets sont stockés dans HashiCorp Vault, AWS Secrets Manager, Azure Key Vault ou Google Secret Manager avec chiffrement au repos utilisant AES-256.
 #4.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les clés cryptographiques sont générées dans des HSM conformes à FIPS 140-2 Niveau 2 (AWS CloudHSM, Azure Dedicated HSM) avec rotation des clés conformément à la politique cryptographique de l'organisation.
 #4.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que la rotation des secrets est automatisée avec un déploiement sans interruption et une rotation immédiate déclenchée par des changements de personnel ou des incidents de sécurité.
 #4.4.4    Niveau: 2    Rôle: D/V
 Vérifiez que les images de conteneur sont analysées à l'aide d'outils (GitLeaks, TruffleHog ou detect-secrets) qui bloquent les builds contenant des clés d'API, des mots de passe ou des certificats.
 #4.4.5    Niveau: 2    Rôle: D/V
 Vérifiez que l'accès aux secrets de production nécessite une authentification à facteurs multiples (MFA) avec des jetons matériels (YubiKey, FIDO2) et est consigné dans des journaux d'audit immuables comprenant les identités des utilisateurs et les horodatages.
 #4.4.6    Niveau: 2    Rôle: D/V
 Vérifiez que les secrets sont injectés via les secrets Kubernetes, des volumes montés ou des conteneurs d'initialisation, et assurez‑vous que les secrets ne sont jamais intégrés dans les variables d’environnement ou les images.

---

### C4.5 Sandboxing des charges de travail d'IA et validation

Isolez les modèles d'IA non fiables dans des sandboxes sécurisés avec une analyse comportementale approfondie.

 #4.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les modèles d'IA externes s'exécutent dans gVisor, des microVMs (tels que Firecracker, CrossVM) ou des conteneurs Docker, avec les options --security-opt=no-new-privileges et --read-only.
 #4.5.2    Niveau: 1    Rôle: D/V
 Vérifiez que les environnements sandbox n'ont aucune connectivité réseau (--network=none) ou qu'ils n'ont qu'un accès à localhost, toutes les requêtes externes étant bloquées par des règles iptables.
 #4.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que la validation des modèles d'IA inclut des tests automatisés de type red team avec une couverture des tests définie par l'organisation et une analyse comportementale pour la détection de portes dérobées.
 #4.5.4    Niveau: 2    Rôle: D/V
 Vérifiez que, avant la promotion d'un modèle d'IA en production, les résultats du bac à sable de ce modèle sont signés cryptographiquement par du personnel de sécurité autorisé et stockés dans des journaux d'audit immuables.
 #4.5.5    Niveau: 2    Rôle: D/V
 Vérifiez que les environnements sandbox sont détruits et recréés à partir d'images dorées entre les évaluations, avec un nettoyage complet du système de fichiers et de la mémoire.

---

### C4.6 Surveillance de la sécurité des infrastructures

Scanner et surveiller l'infrastructure en continu avec une remédiation automatisée et des alertes en temps réel.

 #4.6.1    Niveau: 1    Rôle: D/V
 Vérifier que les images de conteneur sont scannées selon les calendriers organisationnels, les vulnérabilités critiques bloquant le déploiement en fonction des seuils de risque organisationnels.
 #4.6.2    Niveau: 1    Rôle: D/V
 Vérifier que l'infrastructure satisfait les benchmarks CIS ou les contrôles NIST SP 800-53, avec des seuils de conformité définis au niveau organisationnel et une remédiation automatisée pour les vérifications échouées.
 #4.6.3    Niveau: 2    Rôle: D/V
 Vérifiez que les vulnérabilités à gravité élevée sont corrigées conformément aux calendriers de gestion des risques de l'organisation, avec des procédures d’urgence pour les CVE activement exploitées.
 #4.6.4    Niveau: 2    Rôle: V
 Vérifiez que les alertes de sécurité s'intègrent aux plateformes SIEM (Splunk, Elastic ou Sentinel) en utilisant les formats CEF ou STIX/TAXII, avec un enrichissement automatisé.
 #4.6.5    Niveau: 3    Rôle: V
 Vérifiez que les métriques d'infrastructure sont exportées vers les systèmes de surveillance (Prometheus, DataDog) avec des tableaux de bord SLA et des rapports destinés à la direction.
 #4.6.6    Niveau: 2    Rôle: D/V
 Vérifiez que la dérive de configuration est détectée à l'aide d'outils (Chef InSpec, AWS Config) conformément aux exigences de surveillance de l'organisation, avec une restauration automatique en cas de modifications non autorisées.

---

### C4.7 Gestion des ressources d'infrastructure d'IA

Prévenir les attaques d'épuisement des ressources et assurer une allocation équitable des ressources grâce à des quotas et à une surveillance.

 #4.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que l'utilisation du GPU/TPU est surveillée avec des alertes déclenchées à des seuils définis par l'organisation et que les mécanismes de mise à l'échelle automatique ou d'équilibrage de charge soient activés conformément aux politiques de gestion de la capacité.
 #4.7.2    Niveau: 1    Rôle: D/V
 Vérifiez que les métriques de charge de travail d'IA (latence d'inférence, débit, taux d'erreur) sont collectées conformément aux exigences de surveillance de l'organisation et corrélées à l'utilisation de l'infrastructure.
 #4.7.3    Niveau: 2    Rôle: D/V
 Vérifiez que les quotas de ressources Kubernetes (ResourceQuotas) ou équivalents limitent les charges de travail individuelles conformément aux politiques internes d'allocation des ressources, avec des limites strictes imposées.
 #4.7.4    Niveau: 2    Rôle: V
 Vérifiez que la surveillance des coûts suit les dépenses par charge de travail/locataire, avec des alertes basées sur les seuils budgétaires organisationnels et des contrôles automatisés en cas de dépassements budgétaires.
 #4.7.5    Niveau: 3    Rôle: V
 Vérifiez que la planification de la capacité utilise des données historiques avec des périodes de prévision définies par l'organisation et un approvisionnement automatique des ressources basé sur les schémas de la demande.
 #4.7.6    Niveau: 2    Rôle: D/V
 Vérifiez que l'épuisement des ressources déclenche les disjoncteurs conformément aux exigences de réponse organisationnelles, y compris la limitation du débit basée sur les politiques de capacité et l'isolement des charges de travail.

---

### C4.8 Séparation des environnements et contrôles de promotion

Imposer des limites d'environnement strictes avec des portes de promotion automatisées et une validation de sécurité.

 #4.8.1    Niveau: 1    Rôle: D/V
 Vérifier que les environnements de développement, de test et de production fonctionnent dans des VPCs/VNets séparés, sans rôles IAM partagés, groupes de sécurité ni connectivité réseau.
 #4.8.2    Niveau: 1    Rôle: D/V
 Vérifiez que la promotion d'un environnement nécessite l'approbation du personnel autorisé défini au niveau organisationnel, avec des signatures cryptographiques et des journaux d'audit immuables.
 #4.8.3    Niveau: 2    Rôle: D/V
 Vérifiez que les environnements de production bloquent l'accès SSH, désactivent les points de terminaison de débogage et exigent des demandes de changement assorties de préavis organisationnels, sauf en cas d'urgence.
 #4.8.4    Niveau: 2    Rôle: D/V
 Vérifiez que les modifications d'infrastructure-as-code nécessitent une revue par les pairs avec des tests automatisés et une analyse de sécurité avant la fusion dans la branche principale.
 #4.8.5    Niveau: 2    Rôle: D/V
 Vérifiez que les données hors production sont anonymisées conformément aux exigences de confidentialité organisationnelles, à la génération de données synthétiques ou à un masquage complet des données avec suppression des PII.
 #4.8.6    Niveau: 2    Rôle: D/V
 Vérifier que les portes de promotion incluent des tests de sécurité automatisés (SAST, DAST, analyse des images de conteneurs) avec aucune découverte critique requise pour l'approbation.

---

### C4.9 Infrastructure Sauvegarde et Restauration

Assurer la résilience de l'infrastructure grâce à des sauvegardes automatisées, des procédures de récupération testées et des capacités de reprise après sinistre.

 #4.9.1    Niveau: 1    Rôle: D/V
 Vérifiez que les configurations d'infrastructure sont sauvegardées conformément aux plannings de sauvegarde de l'organisation dans des régions géographiquement séparées, selon la stratégie de sauvegarde 3-2-1.
 #4.9.2    Niveau: 2    Rôle: D/V
 Vérifiez que les systèmes de sauvegarde fonctionnent dans des réseaux isolés, avec des identifiants séparés et un stockage déconnecté du réseau pour la protection contre les ransomwares.
 #4.9.3    Niveau: 2    Rôle: V
 Vérifier que les procédures de récupération sont testées et validées par des tests automatisés, conformément aux calendriers organisationnels, avec des objectifs RTO et RPO qui répondent aux exigences organisationnelles.
 #4.9.4    Niveau: 3    Rôle: V
 Vérifiez que la reprise après sinistre inclut des runbooks spécifiques à l’IA avec la restauration des poids du modèle, la reconstruction du cluster GPU et la cartographie des dépendances des services.

---

### C4.10 Conformité et gouvernance des infrastructures

Maintenir la conformité réglementaire grâce à une évaluation continue, à la documentation et à des contrôles automatisés.

 #4.10.1    Niveau: 2    Rôle: D/V
 Vérifier que la conformité de l'infrastructure est évaluée selon les plannings organisationnels et les contrôles SOC 2, ISO 27001 ou FedRAMP, avec une collecte automatisée des preuves.
 #4.10.2    Niveau: 2    Rôle: V
 Vérifiez que la documentation d'infrastructure comprend des diagrammes réseau, des cartes de flux de données et des modèles de menace et qu'ils sont mis à jour conformément aux exigences de la gestion du changement organisationnel.
 #4.10.3    Niveau: 3    Rôle: D/V
 Vérifiez que les modifications d'infrastructure font l'objet d'une évaluation d'impact sur la conformité automatisée avec des flux de travail d'approbation réglementaire pour les modifications à haut risque.

---

### C4.11 Sécurité du matériel d'IA

Sécuriser les composants matériels spécifiques à l’IA, y compris les GPU, les TPU et les accélérateurs IA spécialisés.

 #4.11.1    Niveau: 2    Rôle: D/V
 Vérifiez que le micrologiciel de l'accélérateur IA (BIOS GPU, micrologiciel TPU) est vérifié par des signatures cryptographiques et mis à jour conformément aux calendriers de gestion des correctifs au sein de l'organisation.
 #4.11.2    Niveau: 2    Rôle: D/V
 Vérifiez que, avant l'exécution de la charge de travail, l'intégrité de l'accélérateur d'IA est validée par une attestation matérielle utilisant TPM 2.0, Intel TXT ou AMD SVM.
 #4.11.3    Niveau: 2    Rôle: D/V
 Vérifiez que la mémoire GPU est isolée entre les charges de travail en utilisant SR-IOV, MIG (Multi-Instance GPU) ou une partition matérielle équivalente, avec sanitisation de la mémoire entre les charges de travail.
 #4.11.4    Niveau: 3    Rôle: V
 Vérifiez que la chaîne d'approvisionnement du matériel d'IA inclut la vérification de la provenance avec des certificats du fabricant et la validation des emballages inviolables.
 #4.11.5    Niveau: 3    Rôle: D/V
 Vérifiez que les modules de sécurité matériels (HSM) protègent les poids des modèles d’IA et les clés cryptographiques avec une certification FIPS 140-2 Niveau 3 ou Common Criteria EAL4+.

---

### C4.12 Infrastructure d'IA en périphérie et distribuée

Déploiements sécurisés d'IA distribuée, y compris l'informatique en périphérie, l'apprentissage fédéré et les architectures multi-sites.

 #4.12.1    Niveau: 2    Rôle: D/V
 Vérifiez que les dispositifs d'IA en périphérie s'authentifient auprès de l'infrastructure centrale en utilisant TLS mutuel, avec des certificats d'appareil renouvelés conformément à la politique de gestion des certificats de l'organisation.
 #4.12.2    Niveau: 2    Rôle: D/V
 Vérifiez que les dispositifs en périphérie mettent en œuvre un démarrage sécurisé avec des signatures vérifiées et une protection contre le rétrogradage du firmware.
 #4.12.3    Niveau: 3    Rôle: D/V
 Vérifiez que la coordination distribuée de l’IA utilise des algorithmes de consensus tolérants aux fautes byzantines avec validation des participants et détection des nœuds malveillants.
 #4.12.4    Niveau: 3    Rôle: D/V
 Vérifiez que la communication edge-to-cloud comprend la limitation de la bande passante, la compression des données et des capacités de fonctionnement hors ligne avec un stockage local sécurisé.

---

### C4.13 Sécurité des infrastructures multi-cloud et hybrides

Sécuriser les charges de travail d'IA à travers plusieurs fournisseurs de cloud et des déploiements hybrides cloud et sur site.

 #4.13.1    Niveau: 2    Rôle: D/V
 Vérifiez que les déploiements multi-cloud d'IA utilisent une fédération d'identité indépendante du cloud (OIDC, SAML) avec une gestion centralisée des politiques entre les fournisseurs.
 #4.13.2    Niveau: 2    Rôle: D/V
 Vérifier que le transfert de données entre clouds utilise le chiffrement de bout en bout avec des clés gérées par le client et des contrôles de localisation des données appliqués par juridiction.
 #4.13.3    Niveau: 2    Rôle: D/V
 Vérifiez que les charges de travail d’IA dans un cloud hybride mettent en œuvre des politiques de sécurité cohérentes entre les environnements sur site et dans le cloud, avec une surveillance et des alertes unifiées.
 #4.13.4    Niveau: 3    Rôle: V
 Vérifiez que la prévention du verrouillage du fournisseur de cloud inclut l'infrastructure-as-code portable, des API standardisées et des capacités d'exportation de données avec des outils de conversion de formats.
 #4.13.5    Niveau: 3    Rôle: V
 Vérifiez que l'optimisation des coûts multi-cloud inclut des contrôles de sécurité empêchant l'étalement des ressources ainsi que les frais de transfert de données inter-cloud non autorisés.

---

### C4.14 Automatisation de l'infrastructure et sécurité GitOps

Sécuriser les pipelines d'automatisation de l'infrastructure et les workflows GitOps pour la gestion de l'infrastructure d'IA.

 #4.14.1    Niveau: 2    Rôle: D/V
 Vérifiez que les dépôts GitOps exigent des commits signés avec des clés GPG et des règles de protection de branche empêchant les pushes directs vers les branches principales.
 #4.14.2    Niveau: 2    Rôle: D/V
 Vérifiez que l'automatisation de l'infrastructure inclut la détection de dérive avec une remédiation automatique et des capacités de rollback déclenchées conformément aux exigences de réponse organisationnelles en cas de modifications non autorisées.
 #4.14.3    Niveau: 2    Rôle: D/V
 Vérifiez que le provisionnement automatisé de l'infrastructure inclut la validation des politiques de sécurité avec blocage du déploiement pour les configurations non conformes.
 #4.14.4    Niveau: 2    Rôle: D/V
 Vérifiez que les secrets d'automatisation de l'infrastructure sont gérés par des opérateurs de secrets externes (External Secrets Operator, Bank-Vaults) avec rotation automatique.
 #4.14.5    Niveau: 3    Rôle: V
 Vérifiez que l'infrastructure auto-guérissante intègre la corrélation des événements de sécurité avec une réponse automatisée aux incidents et des flux de notification destinés aux parties prenantes.

---

### C4.15 Sécurité des infrastructures résistantes à l'informatique quantique

Préparez l'infrastructure d'IA pour faire face aux menaces de l'informatique quantique grâce à la cryptographie post-quantique et à des protocoles résistants à l'informatique quantique.

 #4.15.1    Niveau: 3    Rôle: D/V
 Vérifiez que l'infrastructure d'IA implémente les algorithmes cryptographiques post-quantiques approuvés par le NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) pour l'échange de clés et les signatures numériques.
 #4.15.2    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes de distribution de clés quantiques (QKD) sont mis en œuvre pour des communications d'IA à haute sécurité avec des protocoles de gestion des clés résistants à l'informatique quantique.
 #4.15.3    Niveau: 3    Rôle: D/V
 Vérifiez que les cadres d’agilité cryptographique permettent une migration rapide vers de nouveaux algorithmes post-quantiques avec rotation automatisée des certificats et des clés.
 #4.15.4    Niveau: 3    Rôle: V
 Vérifiez que la modélisation des menaces quantiques évalue la vulnérabilité des infrastructures d'IA face aux attaques quantiques, avec des calendriers de migration documentés et des évaluations des risques.
 #4.15.5    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes cryptographiques hybrides classiques-quantique assurent une défense en profondeur pendant la période de transition quantique avec une surveillance des performances.

---

### C4.16 Informatique confidentielle et enclaves sécurisées

Protéger les charges de travail d'IA et les poids des modèles en utilisant des environnements d'exécution de confiance basés sur le matériel et des technologies d'informatique confidentielle.

 #4.16.1    Niveau: 3    Rôle: D/V
 Vérifiez que les modèles d'IA sensibles s'exécutent dans les enclaves Intel SGX, AMD SEV-SNP ou ARM TrustZone, avec mémoire chiffrée et vérification d'attestation.
 #4.16.2    Niveau: 3    Rôle: D/V
 Vérifiez que les conteneurs confidentiels (Kata Containers, gVisor avec informatique confidentielle) isolent les charges de travail d’IA grâce à un chiffrement mémoire pris en charge par le matériel.
 #4.16.3    Niveau: 3    Rôle: D/V
 Vérifiez que l'attestation à distance valide l'intégrité de l'enclave avant de charger des modèles d'IA avec une preuve cryptographique de l'authenticité d'un environnement d'exécution.
 #4.16.4    Niveau: 3    Rôle: D/V
 Vérifiez que les services d'inférence d'IA confidentiels empêchent l'extraction de modèles par calcul chiffré, avec des poids du modèle scellés et une exécution protégée.
 #4.16.5    Niveau: 3    Rôle: D/V
 Vérifiez que l'orchestration de l'environnement d'exécution fiable gère le cycle de vie des enclaves sécurisées avec l'attestation à distance et des canaux de communication chiffrés.
 #4.16.6    Niveau: 3    Rôle: D/V
 Vérifiez que le calcul multipartite sécurisé (SMPC) permet un entraînement collaboratif en IA sans exposer les ensembles de données individuels ou les paramètres du modèle.

---

### C4.17 Infrastructure à connaissance nulle

Mettre en œuvre des systèmes de preuves à connaissance nulle pour la vérification et l'authentification de l'IA respectant la vie privée, sans révéler d'informations sensibles.

 #4.17.1    Niveau: 3    Rôle: D/V
 Vérifier que les preuves à connaissance nulle (ZK-SNARKs, ZK-STARKs) vérifient l'intégrité du modèle d'IA et la provenance de l'entraînement sans exposer les poids du modèle ni les données d'entraînement.
 #4.17.2    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes d'authentification basés sur des preuves à connaissance nulle permettent une vérification des utilisateurs préservant la vie privée pour les services d'IA, sans révéler d'informations relatives à l'identité.
 #4.17.3    Niveau: 3    Rôle: D/V
 Vérifiez que les protocoles d'intersection d’ensembles privés (PSI) permettent une mise en correspondance sécurisée des données pour l'IA fédérée sans exposer les jeux de données individuels.
 #4.17.4    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes d'apprentissage automatique à connaissance nulle (ZKML) permettent des inférences d'IA vérifiables avec une preuve cryptographique du calcul correct.
 #4.17.5    Niveau: 3    Rôle: D/V
 Vérifiez que les ZK-rollups offrent un traitement des transactions d'IA évolutif et préservant la confidentialité, avec une vérification par lots et une surcharge de calcul réduite.

---

### C4.18 Prévention des attaques par canaux latéraux

Protéger l'infrastructure d'IA des attaques par canaux auxiliaires de temporisation, de puissance, électromagnétiques et basées sur le cache qui pourraient divulguer des informations sensibles.

 #4.18.1    Niveau: 3    Rôle: D/V
 Vérifiez que le temps d'inférence de l'IA est normalisé à l'aide d'algorithmes à temps constant et de rembourrage afin d'empêcher les attaques d'extraction de modèle basées sur le temps.
 #4.18.2    Niveau: 3    Rôle: D/V
 Vérifiez que la protection contre l'analyse de puissance inclut l'injection de bruit, le filtrage des lignes d'alimentation et des schémas d'exécution aléatoires pour le matériel d'IA.
 #4.18.3    Niveau: 3    Rôle: D/V
 Vérifiez que l’atténuation des canaux latéraux basés sur le cache utilise le partitionnement du cache, la randomisation et les instructions de purge du cache pour empêcher les fuites d’informations.
 #4.18.4    Niveau: 3    Rôle: D/V
 Vérifiez que la protection contre les émissions électromagnétiques comprend le blindage, le filtrage des signaux et le traitement aléatoire afin de prévenir les attaques de type TEMPEST.
 #4.18.5    Niveau: 3    Rôle: D/V
 Vérifiez que les défenses contre les canaux latéraux microarchitecturaux incluent des contrôles de l'exécution spéculative et l'obfuscation des motifs d'accès mémoire.

---

### C4.19 Neuromorphique et sécurité du matériel IA spécialisé

Sécuriser les architectures matérielles émergentes pour l’IA, y compris les puces neuromorphiques, les FPGAs, les ASICs personnalisés et les systèmes de calcul optique.

 #4.19.1    Niveau: 3    Rôle: D/V
 Vérifiez que la sécurité des puces neuromorphes inclut le chiffrement des motifs d'impulsions, la protection des poids synaptiques et la validation des règles d'apprentissage basées sur le matériel.
 #4.19.2    Niveau: 3    Rôle: D/V
 Vérifiez que les accélérateurs IA basés sur FPGA mettent en œuvre le chiffrement du bitstream, les mécanismes anti-sabotage et le chargement sécurisé de la configuration avec des mises à jour authentifiées.
 #4.19.3    Niveau: 3    Rôle: D/V
 Vérifiez que la sécurité des ASIC personnalisés inclut des processeurs de sécurité sur puce, une racine de confiance matérielle et un stockage sûr des clés avec détection de manipulation.
 #4.19.4    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes de calcul optique mettent en œuvre un chiffrement optique résistant aux ordinateurs quantiques, une commutation photonique sécurisée et un traitement du signal optique protégé.
 #4.19.5    Niveau: 3    Rôle: D/V
 Vérifiez que les puces d'IA hybrides analogiques et numériques incluent un calcul analogique sécurisé, un stockage protégé des poids et une conversion analogique-numérique authentifiée.

---

### C4.20 Infrastructure de calcul préservant la vie privée

Implémenter des contrôles d'infrastructure pour des calculs préservant la confidentialité afin de protéger les données sensibles pendant le traitement et l'analyse par l'IA.

 #4.20.1    Niveau: 3    Rôle: D/V
 Vérifiez que l'infrastructure de chiffrement homomorphe permet des calculs chiffrés sur des charges de travail sensibles liées à l'IA, avec vérification de l'intégrité cryptographique et surveillance des performances.
 #4.20.2    Niveau: 3    Rôle: D/V
 Vérifiez que les systèmes de récupération d'informations privées permettent des requêtes sur des bases de données sans révéler les motifs de requête, grâce à une protection cryptographique des motifs d'accès.
 #4.20.3    Niveau: 3    Rôle: D/V
 Vérifiez que les protocoles de calcul multipartite sécurisé permettent une inférence d’IA respectueuse de la vie privée sans exposer les entrées individuelles ni les calculs intermédiaires.
 #4.20.4    Niveau: 3    Rôle: D/V
 Vérifiez que la gestion des clés respectueuse de la vie privée inclut la génération de clés distribuée, la cryptographie à seuil et la rotation sécurisée des clés avec une protection matérielle.
 #4.20.5    Niveau: 3    Rôle: D/V
 Vérifiez que les performances du calcul à confidentialité préservée sont optimisées grâce au traitement par lots, à la mise en cache et à l'accélération matérielle tout en maintenant les garanties de sécurité cryptographique.

---

### C4.15 Agent Framework Cloud Integration Sécurité et Déploiement Hybride

Contrôles de sécurité pour les frameworks d'agents intégrés au cloud avec des architectures hybrides sur site et dans le cloud.

 #4.15.1    Niveau: 1    Rôle: D/V
 Vérifiez que l'intégration du stockage dans le cloud utilise un chiffrement de bout en bout avec une gestion des clés contrôlée par l'agent.
 #4.15.2    Niveau: 2    Rôle: D/V
 Vérifiez que les frontières de sécurité du déploiement hybride sont clairement définies avec des canaux de communication chiffrés.
 #4.15.3    Niveau: 2    Rôle: D/V
 Vérifiez que l'accès aux ressources cloud inclut une vérification zéro-trust avec une authentification continue.
 #4.15.4    Niveau: 3    Rôle: D/V
 Vérifiez que les exigences de résidence des données sont appliquées par une attestation cryptographique des emplacements de stockage.
 #4.15.5    Niveau: 3    Rôle: D/V
 Vérifiez que les évaluations de sécurité du fournisseur cloud incluent une modélisation des menaces axée sur l’agent et une évaluation des risques.

---

### Références

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
NIST SP 800-190: Application Container Security Guide
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
NIST SP 800-53: Security Controls for Federal Information Systems
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework
CIS Kubernetes Benchmark
FIPS 140-2 Security Requirements
NIST SP 800-207: Zero Trust Architecture
IEEE 2857: Privacy Engineering for AI Systems
NIST SP 800-161: Cybersecurity Supply Chain Risk Management
NIST Post-Quantum Cryptography Standards
Intel SGX Developer Guide
AMD SEV-SNP White Paper
ARM TrustZone Technology
ZK-SNARKs: A Gentle Introduction
NIST SP 800-57: Cryptographic Key Management
Side-Channel Attack Countermeasures
Neuromorphic Computing Security Challenges
FPGA Security: Fundamentals, Evaluation, and Countermeasures
Microsoft SEAL: Homomorphic Encryption Library
HElib: Homomorphic Encryption Library
PALISADE Lattice Cryptography Library
Differential Privacy: A Survey of Results
Secure Aggregation for Federated Learning
Private Information Retrieval: Concepts and Constructions

## C5 Contrôle d’accès et identité pour les composants et les utilisateurs d’IA

### Objectif de contrôle

Un contrôle d'accès efficace pour les systèmes d’IA nécessite une gestion robuste des identités, une autorisation adaptée au contexte et une mise en œuvre à l’exécution conforme aux principes du zéro-trust. Ces contrôles garantissent que les humains, les services et les agents autonomes n'interagissent qu'avec les modèles, les données et les ressources informatiques dans des périmètres explicitement autorisés, avec une vérification continue et des capacités d'audit.

---

### C5.1 Gestion des identités et de l’authentification

Établir des identités fondées sur la cryptographie pour toutes les entités, avec une authentification multifactorielle pour les opérations privilégiées.

 #5.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les utilisateurs humains et les principaux de service s'authentifient via un fournisseur d'identité d'entreprise centralisé (IdP) utilisant les protocoles OIDC/SAML, avec des correspondances identifiant-jeton uniques (aucun compte ni identifiants partagés).
 #5.1.2    Niveau: 1    Rôle: D/V
 Vérifier que les opérations haut-risque (déploiement de modèles, exportation de poids, accès aux données d'entraînement, modifications de la configuration de production) nécessitent une authentification multifactorielle ou une authentification renforcée avec ré-validation de session.
 #5.1.3    Niveau: 2    Rôle: D
 Vérifiez que les nouveaux utilisateurs subissent une vérification d'identité conforme à NIST 800-63-3 IAL-2 ou à des normes équivalentes, avant d'obtenir l'accès au système de production.
 #5.1.4    Niveau: 2    Rôle: V
 Vérifiez que les revues d’accès sont effectuées trimestriellement avec une détection automatisée des comptes dormants, l’application de la rotation des identifiants et des flux de désprovisionnement.
 #5.1.5    Niveau: 3    Rôle: D/V
 Vérifier que les agents d'IA fédérés s'authentifient par des assertions JWT signées qui ont une durée de validité maximale de 24 heures et qui incluent une preuve cryptographique d'origine.

---

### C5.2 Autorisation des ressources et le principe du moindre privilège

Mettez en place des contrôles d'accès granulaire pour toutes les ressources d'IA, avec des modèles d'autorisation explicites et des pistes d'audit.

 #5.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque ressource d'IA (ensembles de données, modèles, points de terminaison, collections vectorielles, indices d'incorporation, instances de calcul) applique des contrôles d'accès basés sur les rôles avec des listes blanches explicites et des politiques de refus par défaut.
 #5.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que les principes du moindre privilège sont appliqués par défaut, les comptes de service débutant avec des droits en lecture seule, et qu'une justification commerciale documentée est requise pour l'accès en écriture.
 #5.2.3    Niveau: 1    Rôle: V
 Vérifiez que toutes les modifications du contrôle d'accès sont liées à des demandes de modification approuvées et enregistrées de manière immuable avec des horodatages, identités des acteurs, identifiants des ressources et variations des droits d'accès.
 #5.2.4    Niveau: 2    Rôle: D
 Les étiquettes de classification des données (PII, PHI, sous contrôle d'exportation, propriétaire) se propagent automatiquement vers les ressources dérivées (embeddings, caches de prompts, sorties du modèle) avec une application cohérente de la politique.
 #5.2.5    Niveau: 2    Rôle: D/V
 Vérifiez que les tentatives d'accès non autorisées et les événements d'élévation de privilèges déclenchent des alertes en temps réel avec des métadonnées contextuelles vers les systèmes SIEM dans les 5 minutes.

---

### C5.3 Évaluation dynamique de la politique

Déployer des moteurs ABAC (contrôle d'accès basé sur les attributs) pour des décisions d'autorisation sensibles au contexte avec des capacités d'audit.

 #5.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les décisions d'autorisation sont externalisées vers un moteur de politiques dédié (OPA, Cedar ou équivalent) accessible via des API authentifiées avec une protection d'intégrité cryptographique.
 #5.3.2    Niveau: 1    Rôle: D/V
 Vérifier que les politiques évaluent des attributs dynamiques à l'exécution, y compris le niveau d'habilitation de l'utilisateur, la classification de la sensibilité des ressources, le contexte de la requête, l'isolation entre locataires et les contraintes temporelles.
 #5.3.3    Niveau: 2    Rôle: D
 Vérifiez que les définitions de politiques sont sous contrôle de version, évaluées par des pairs et validées par des tests automatisés dans les pipelines CI/CD avant le déploiement en production.
 #5.3.4    Niveau: 2    Rôle: V
 Vérifier que les résultats d'évaluation des politiques incluent des justifications de décision structurées et qu'ils sont transmis aux systèmes SIEM pour l'analyse de corrélation et les rapports de conformité.
 #5.3.5    Niveau: 3    Rôle: D/V
 Vérifiez que les valeurs TTL du cache des politiques ne dépassent pas 5 minutes pour les ressources à haute sensibilité et 1 heure pour les ressources standard dotées de capacités d'invalidation du cache.

---

### C5.4 Sécurité à l'exécution des requêtes

Mettre en œuvre des contrôles de sécurité au niveau de la base de données avec filtrage obligatoire et des politiques de sécurité au niveau des lignes.

 #5.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que toutes les requêtes vers les bases de données vectorielles et SQL incluent des filtres de sécurité obligatoires (ID du locataire, étiquettes de sensibilité, périmètre utilisateur) imposés au niveau du moteur de la base de données, et non dans le code de l'application.
 #5.4.2    Niveau: 1    Rôle: D/V
 Vérifier que les politiques de sécurité au niveau des lignes (RLS) et le masquage au niveau des champs sont activés avec l'héritage des politiques pour toutes les bases de données vectorielles, les indices de recherche et les ensembles de données d'entraînement.
 #5.4.3    Niveau: 2    Rôle: D
 Vérifiez que les échecs des évaluations d'autorisation empêcheront les « confused deputy attacks » en abortant immédiatement les requêtes et en renvoyant des codes d'erreur d'autorisation explicites plutôt que de renvoyer des ensembles de résultats vides.
 #5.4.4    Niveau: 2    Rôle: V
 Vérifiez que la latence d’évaluation des politiques est surveillée en continu avec des alertes automatisées pour les conditions de délai d’expiration qui pourraient permettre un contournement de l’autorisation.
 #5.4.5    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes de réessai des requêtes réévaluent les politiques d'autorisation afin de prendre en compte les modifications dynamiques des autorisations au sein des sessions utilisateur actives.

---

### C5.5 Filtrage de sortie et prévention de la perte de données

Déployer des contrôles de post-traitement pour prévenir l'exposition non autorisée des données dans le contenu généré par l'IA.

 #5.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les mécanismes de filtrage post-inférence analysent et masquent les PII (informations personnellement identifiables) non autorisées, les informations classifiées et les données propriétaires avant de livrer le contenu aux demandeurs.
 #5.5.2    Niveau: 1    Rôle: D/V
 Vérifiez que les citations, les références et les attributions de sources dans les sorties du modèle sont validées en fonction des droits d'accès de l'appelant et sont supprimées en cas d'accès non autorisé détecté.
 #5.5.3    Niveau: 2    Rôle: D
 Vérifiez que les restrictions de format de sortie (PDFs dépourvus de métadonnées, images dépourvues de métadonnées, types de fichiers approuvés) sont appliquées en fonction des niveaux d'autorisation des utilisateurs et des classifications des données.
 #5.5.4    Niveau: 2    Rôle: V
 Vérifiez que les algorithmes de rédaction sont déterministes, versionnés et conservent des journaux d’audit pour soutenir les enquêtes de conformité et l’analyse médico-légale.
 #5.5.5    Niveau: 3    Rôle: V
 Vérifiez que les événements de redaction à haut risque génèrent des journaux adaptatifs qui incluent des hachages cryptographiques du contenu d'origine pour la récupération médico-légale sans exposition des données.

---

### C5.6 Isolement multi-locataires

Assurer l'isolation cryptographique et logique entre les locataires dans une infrastructure d'IA partagée.

 #5.6.1    Niveau: 1    Rôle: D/V
 Vérifier que les espaces mémoire, les stockages d'embeddings, les entrées de cache et les fichiers temporaires sont isolés par espace de noms pour chaque locataire, avec une purge sécurisée lors de la suppression du locataire ou de la terminaison de la session.
 #5.6.2    Niveau: 1    Rôle: D/V
 Vérifiez que chaque requête API comprend un identifiant de locataire authentifié qui est validé cryptographiquement par rapport au contexte de session et aux droits d'accès de l'utilisateur.
 #5.6.3    Niveau: 2    Rôle: D
 Vérifiez que les politiques réseau mettent en œuvre des règles de refus par défaut pour la communication inter-locataires au sein des maillages de services et des plateformes d'orchestration de conteneurs.
 #5.6.4    Niveau: 3    Rôle: D
 Vérifiez que les clés de chiffrement sont uniques par locataire avec prise en charge des clés gérées par le client (CMK) et l'isolation cryptographique entre les stockages de données des locataires.

---

### C5.7 Autorisation d'agent autonome

Contrôler les permissions des agents d'IA et des systèmes autonomes grâce à des jetons de capacité à portée limitée et à une autorisation continue.

 #5.7.1    Niveau: 1    Rôle: D/V
 Assurez-vous que les agents autonomes reçoivent des jetons de capacité à portée limitée qui énumèrent explicitement les actions autorisées, les ressources accessibles, les limites temporelles et les contraintes opérationnelles.
 #5.7.2    Niveau: 1    Rôle: D/V
 Vérifiez que les capacités à haut risque (accès au système de fichiers, exécution de code, appels d'API externes, transactions financières) sont désactivées par défaut et nécessitent des autorisations explicites pour leur activation avec des justifications commerciales.
 #5.7.3    Niveau: 2    Rôle: D
 Vérifiez que les jetons de capacité sont liés aux sessions utilisateur, qu'ils disposent d'une protection d'intégrité cryptographique et assurez-vous qu'ils ne peuvent pas être conservés ni réutilisés dans des scénarios hors ligne.
 #5.7.4    Niveau: 2    Rôle: V
 Vérifiez que les actions initiées par l'agent font l'objet d'une autorisation secondaire via le moteur de politiques ABAC, avec une évaluation complète du contexte et une journalisation d'audit.
 #5.7.5    Niveau: 3    Rôle: V
 Vérifiez que les conditions d'erreur des agents et la gestion des exceptions incluent des informations sur la portée des capacités afin de soutenir l'analyse des incidents et l'enquête médico-légale.

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
#### Sécurité IA-spécifique

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Sécurité de la chaîne d'approvisionnement pour les modèles, frameworks et données

### Objectif de contrôle

Les attaques de la chaîne d'approvisionnement en IA exploitent des modèles, cadres ou ensembles de données fournis par des tiers pour intégrer des portes dérobées, des biais ou du code exploitable. Ces contrôles offrent une traçabilité de bout en bout, la gestion des vulnérabilités et la surveillance pour protéger l'ensemble du cycle de vie du modèle.

---

### C6.1 Évaluation et provenance des modèles pré-entraînés

Évaluer et authentifier les origines des modèles tiers, leurs licences et les comportements cachés avant tout affinage ou déploiement.

 #6.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque artefact de modèle tiers‑partie comprend un enregistrement de provenance signé qui identifie le dépôt source et le hash du commit.
 #6.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les modèles sont scannés à l’aide d’outils automatisés pour détecter des couches malveillantes ou des déclencheurs de cheval de Troie avant l’importation.
 #6.1.3    Niveau: 2    Rôle: D
 Vérifiez que les réglages fins par transfert d'apprentissage passent l'évaluation adversariale pour détecter les comportements cachés.
 #6.1.4    Niveau: 2    Rôle: V
 Vérifiez que les licences des modèles, les étiquettes d'export‑contrôle et les déclarations d'origine des données sont enregistrées dans une entrée ML‑BOM.
 #6.1.5    Niveau: 3    Rôle: D/V
 Vérifiez que les modèles à haut risque (poids téléversés publiquement, créateurs non vérifiés) restent en quarantaine jusqu'à l'examen et l'approbation par un être humain.

---

### C6.2 Analyse des frameworks et des bibliothèques

Analysez en continu les frameworks et bibliothèques d'apprentissage automatique pour les CVEs et le code malveillant afin de garantir la sécurité de la pile d'exécution.

 #6.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les pipelines CI exécutent des analyseurs de dépendances sur les frameworks d'IA et les bibliothèques critiques.
 #6.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que les vulnérabilités critiques (CVSS ≥ 7.0) empêchent la promotion vers les images de production.
 #6.2.3    Niveau: 2    Rôle: D
 Vérifiez que l’analyse statique du code s’exécute sur des bibliothèques ML forkées ou vendues en interne.
 #6.2.4    Niveau: 2    Rôle: V
 Vérifiez que les propositions de mise à niveau du cadre incluent une évaluation de l'impact sur la sécurité faisant référence aux flux CVE publics.
 #6.2.5    Niveau: 3    Rôle: V
 Vérifiez que les capteurs d'exécution déclenchent des alertes lorsque des chargements dynamiques de bibliothèques inattendus s'écartent de la SBOM signée.

---

### C6.3 Verrouillage des dépendances et vérification

Fixer chaque dépendance à des empreintes immuables et reproduire les builds afin de garantir des artefacts identiques et inviolables.

 #6.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les gestionnaires de paquets imposent le verrouillage des versions via les fichiers de verrouillage.
 #6.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que les digests immuables sont utilisés plutôt que des tags mutables dans les références de conteneurs.
 #6.3.3    Niveau: 2    Rôle: D
 Vérifiez que les contrôles de reproducible‑build comparent les hachages entre les exécutions CI afin de garantir des sorties identiques.
 #6.3.4    Niveau: 2    Rôle: V
 Vérifiez que les attestations de build sont conservées pendant 18 mois pour assurer la traçabilité lors des audits.
 #6.3.5    Niveau: 3    Rôle: D
 Vérifiez que les dépendances expirées déclenchent des PR automatisées pour mettre à jour ou forker des versions épinglées.

---

### C6.4 Application des sources de confiance

Autoriser les téléchargements d'artefacts uniquement à partir de sources vérifiées cryptographiquement et approuvées par l'organisation, et bloquer tout le reste.

 #6.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que les poids du modèle, les ensembles de données et les conteneurs sont téléchargés uniquement depuis des domaines approuvés ou des registres internes.
 #6.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les signatures Sigstore/Cosign valident l'identité de l'éditeur avant que les artefacts ne soient mis en cache localement.
 #6.4.3    Niveau: 2    Rôle: D
 Vérifiez que les proxys de sortie bloquent les téléchargements d’artefacts non authentifiés afin de faire respecter la politique des sources fiables.
 #6.4.4    Niveau: 2    Rôle: V
 Vérifiez que les listes blanches du dépôt sont examinées trimestriellement avec des preuves de justification métier pour chaque entrée.
 #6.4.5    Niveau: 3    Rôle: V
 Vérifiez que les violations de la politique déclenchent la mise en quarantaine des artefacts et le retour en arrière des exécutions de pipeline dépendantes.

---

### C6.5 Évaluation des risques des jeux de données tiers

Évaluer les ensembles de données externes pour l’empoisonnement des données, les biais et la conformité juridique, et les surveiller tout au long de leur cycle de vie.

 #6.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les ensembles de données externes subissent une évaluation du risque d'empoisonnement (par exemple, empreinte numérique des données, détection des valeurs aberrantes).
 #6.5.2    Niveau: 1    Rôle: D
 Vérifiez que les métriques de biais (parité démographique, égalité des chances) sont calculées avant l'approbation du jeu de données.
 #6.5.3    Niveau: 2    Rôle: V
 Vérifiez que la provenance et les termes de licence des ensembles de données sont capturés dans les entrées ML‑BOM.
 #6.5.4    Niveau: 2    Rôle: V
 Vérifiez que la surveillance périodique détecte la dérive ou la corruption des ensembles de données hébergés.
 #6.5.5    Niveau: 3    Rôle: D
 Vérifiez que le contenu interdit (droits d’auteur, informations personnelles identifiables) est supprimé par un nettoyage automatisé avant l’entraînement.

---

### C6.6 Surveillance des attaques de la chaîne d'approvisionnement

Détecter les menaces de la chaîne d'approvisionnement tôt grâce aux flux CVE, à l'analyse des journaux d'audit et aux simulations de l'équipe rouge.

 #6.6.1    Niveau: 1    Rôle: V
 Vérifiez que les journaux d’audit CI/CD sont acheminés vers les détections SIEM pour les téléchargements de paquets anormaux ou les étapes de build altérées.
 #6.6.2    Niveau: 2    Rôle: D
 Vérifiez que les playbooks de réponse aux incidents incluent des procédures de rollback pour des modèles ou des bibliothèques qui ont été compromis.
 #6.6.3    Niveau: 3    Rôle: V
 Vérifiez que l'enrichissement par renseignement sur les menaces marque les indicateurs ML‑spécifiques (par exemple, IoCs d'empoisonnement de modèles) dans le triage des alertes.

---

### C6.7 ML‑BOM pour les artefacts du modèle

Générer et signer des SBOM détaillés spécifiques à l'apprentissage automatique (ML‑BOMs) afin que les consommateurs en aval puissent vérifier l'intégrité des composants au moment du déploiement.

 #6.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque artefact de modèle publie un ML‑BOM qui répertorie les ensembles de données, les poids, les hyperparamètres et les licences.
 #6.7.2    Niveau: 1    Rôle: D/V
 Vérifiez que la génération ML‑BOM et la signature Cosign sont automatisées dans l’intégration continue et obligatoires pour la fusion.
 #6.7.3    Niveau: 2    Rôle: D
 Vérifiez que les vérifications de complétude ML‑BOM font échouer la compilation si des métadonnées de composants (hash, licence) sont manquantes.
 #6.7.4    Niveau: 2    Rôle: V
 Vérifiez que les consommateurs en aval peuvent interroger les ML-BOMs via l'API pour valider les modèles importés au moment du déploiement.
 #6.7.5    Niveau: 3    Rôle: V
 Vérifiez que les ML‑BOMs font l'objet d'un contrôle de version et d'un diff afin de détecter les modifications non autorisées.

---

### Références

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
AI & Transparency: Protect ML Models – ReversingLabs
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## C7 Comportement du modèle, Contrôle de sortie et Assurance de sécurité

### Objectif de contrôle

Les sorties du modèle doivent être structurées, fiables, sûres, explicables et surveillées en continu en production. Ce faisant, cela réduit les hallucinations, les fuites de données personnelles, le contenu nuisible et les actions hors de contrôle, tout en renforçant la confiance des utilisateurs et la conformité réglementaire.

---

### C7.1 Application du format de sortie

Des schémas stricts, un décodage contraint et une validation en aval empêchent le contenu malformé ou malveillant de se propager.

 #7.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que les schémas de réponse (par exemple, le schéma JSON) sont fournis dans l'invite système et que chaque sortie est automatiquement vérifiée; les sorties non conformes déclenchent réparation ou rejet.
 #7.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que le décodage sous contraintes (jetons d'arrêt, expressions régulières, max-tokens) est activé pour prévenir le débordement ou les canaux d'injection de prompt.
 #7.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que les composants en aval traitent les sorties comme non fiables et les valident selon des schémas ou des désérialiseurs sûrs contre les injections.
 #7.1.4    Niveau: 3    Rôle: V
 Vérifiez que les événements de sortie inappropriés sont enregistrés, limités en débit et remontés vers le système de surveillance.

---

### C7.2 Détection et atténuation des hallucinations

L'estimation de l'incertitude et les stratégies de repli permettent de limiter les réponses fabriquées.

 #7.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les log-probabilités au niveau des jetons, la cohérence d'ensemble ou les détecteurs d'hallucination finement ajustés attribuent un score de confiance à chaque réponse.
 #7.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que les réponses en dessous d'un seuil de confiance configurable déclenchent des flux de travail de secours (par exemple, génération augmentée par récupération, modèle secondaire ou révision humaine).
 #7.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les incidents d'hallucination sont étiquetés avec des métadonnées de cause racine et acheminés vers les pipelines de post-mortem et de finetuning.
 #7.2.4    Niveau: 3    Rôle: D/V
 Vérifiez que les seuils et les détecteurs sont recalibrés après les mises à jour majeures du modèle ou de la base de connaissances.
 #7.2.5    Niveau: 3    Rôle: V
 Vérifiez que les visualisations du tableau de bord suivent les taux d'hallucination.

---

### C7.3 Filtrage de la sécurité et de la confidentialité des sorties

Les filtres de politique et la couverture par l'équipe rouge protègent les utilisateurs et les données confidentielles.

 #7.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les classificateurs pré-génération et post-génération bloquent le contenu haineux, le harcèlement, l'automutilation, le contenu extrémiste et le contenu sexuellement explicite, conformément à la politique.
 #7.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que la détection PII/PCI et la rédaction automatique s'exécutent sur chaque réponse; les violations provoquent un incident de confidentialité.
 #7.3.3    Niveau: 2    Rôle: D
 Vérifiez que les étiquettes de confidentialité se propagent à travers les modalités afin d'éviter les fuites dans le texte, les images ou le code.
 #7.3.4    Niveau: 3    Rôle: D/V
 Vérifiez que les tentatives de contournement du filtre ou les classifications à haut risque nécessitent une approbation secondaire ou une réauthentification de l'utilisateur.
 #7.3.5    Niveau: 3    Rôle: D/V
 Vérifiez que les seuils de filtrage reflètent les juridictions légales et le contexte d'âge et de rôle de l'utilisateur.

---

### C7.4 Sortie et limitation des actions

Les limites de débit et les portes d'approbation empêchent les abus et l'autonomie excessive.

 #7.4.1    Niveau: 1    Rôle: D
 Vérifiez que les quotas par utilisateur et par clé API limitent les requêtes, les jetons et le coût avec une temporisation exponentielle en cas d'erreurs 429.
 #7.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les actions privilégiées (écritures de fichiers, exécution de code, appels réseau) nécessitent une approbation basée sur une politique ou une intervention humaine dans la boucle.
 #7.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que les contrôles de cohérence intermodaux garantissent que les images, le code et le texte générés pour la même requête ne puissent pas être utilisés pour faire passer du contenu malveillant.
 #7.4.4    Niveau: 2    Rôle: D
 Vérifiez que la profondeur de délégation de l'agent, les limites de récursion et les listes d'outils autorisés soient explicitement configurés.
 #7.4.5    Niveau: 3    Rôle: V
 Vérifiez que la violation des limites émet des événements de sécurité structurés pour l'ingestion dans le SIEM.

---

### C7.5 Explicabilité des sorties

Des signaux transparents améliorent la confiance des utilisateurs et facilitent le débogage interne.

 #7.5.1    Niveau: 2    Rôle: D/V
 Vérifiez que les scores de confiance affichés à l'utilisateur ou les résumés de raisonnement succincts sont affichés lorsque l'évaluation des risques est jugée appropriée.
 #7.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les explications générées ne révèlent pas d'invites système sensibles ou des données propriétaires.
 #7.5.3    Niveau: 3    Rôle: D
 Vérifiez que le système capture les log-probabilités au niveau des jetons ou les cartes d'attention et les stocke pour un examen autorisé.
 #7.5.4    Niveau: 3    Rôle: V
 Vérifiez que les artefacts d'explicabilité sont versionnés parallèlement aux versions des modèles pour l'auditabilité.

---

### C7.6 Intégration de la surveillance

L'observabilité en temps réel ferme la boucle entre le développement et la production.

 #7.6.1    Niveau: 1    Rôle: D
 Vérifiez que les métriques (violations de schéma, taux d'hallucination, toxicité, fuites d'informations personnellement identifiables (PII), latence, coût) sont transmises à une plateforme centrale de surveillance.
 #7.6.2    Niveau: 1    Rôle: V
 Vérifier que les seuils d’alerte sont définis pour chaque métrique de sécurité, avec des procédures d’escalade lors de l’astreinte.
 #7.6.3    Niveau: 2    Rôle: V
 Vérifiez que les tableaux de bord corrèlent les anomalies de sortie avec le modèle/version, le flag de fonctionnalité et les changements de données en amont.
 #7.6.4    Niveau: 2    Rôle: D/V
 Vérifiez que les données de surveillance reviennent dans le réentraînement, le réglage fin ou la mise à jour des règles dans le cadre d’un flux de travail MLOps documenté.
 #7.6.5    Niveau: 3    Rôle: V
 Vérifiez que les pipelines de surveillance sont soumis à des tests de pénétration et à un contrôle d'accès afin d'éviter la fuite des journaux sensibles.

---

### 7.7 Garde-fous des médias génératifs

Veiller à ce que les systèmes d'IA ne génèrent pas de contenu multimédia illégal, nuisible ou non autorisé en appliquant des contraintes de politique, en procédant à la validation des sorties et en assurant la traçabilité.

 #7.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les invites du système et les instructions de l'utilisateur interdisent explicitement la génération de médias deepfake illégaux, nuisibles ou non consensuels (par exemple, image, vidéo, audio).
 #7.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que les requêtes sont filtrées pour prévenir les tentatives d'usurpation d'identité, de deepfakes sexuellement explicites ou de contenus montrant des personnes réelles sans leur consentement.
 #7.7.3    Niveau: 2    Rôle: V
 Vérifiez que le système utilise le hachage perceptuel, la détection de filigranes ou l’empreinte numérique pour prévenir la reproduction non autorisée de contenus protégés par le droit d’auteur.
 #7.7.4    Niveau: 3    Rôle: D/V
 Vérifiez que tous les médias générés sont signés cryptographiquement, marqués d'un filigrane, ou intégrés avec des métadonnées de provenance résistantes à la falsification, afin d'assurer la traçabilité en aval.
 #7.7.5    Niveau: 3    Rôle: V
 Vérifier que les tentatives de contournement (par exemple l'obfuscation des requêtes, l'argot, les formulations adversariales) sont détectées, consignées et soumises à une limitation de débit ; les abus répétés sont remontés aux systèmes de surveillance.

### Références

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Improper Output Handling – OWASP LLM05:2025
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
LLM Red-Teaming Guide
Sensitive Information Disclosure in LLMs
LangChain – Chat Model Rate Limiting
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## C8 Memory, Représentations vectorielles et sécurité des bases de données vectorielles

### Objectif de contrôle

Les embeddings et les stockages vectoriels agissent comme la mémoire active des systèmes d'IA contemporains, acceptant en continu les données fournies par les utilisateurs et les réintégrant dans les contextes des modèles via la génération augmentée par récupération (RAG). Si elle est laissée sans gouvernance, cette mémoire peut divulguer des informations personnelles identifiables (PII), violer le consentement ou être utilisée pour reconstituer le texte d'origine. L'objectif de cette famille de contrôles est de durcir les pipelines de mémoire et les bases de données vectorielles afin que l'accès respecte le principe du moindre privilège, que les embeddings préservent la vie privée, que les vecteurs stockés expirent ou puissent être révoqués à la demande, et que la mémoire par utilisateur ne contamine jamais les invites ou les réponses générées d'un autre utilisateur.

---

### C8.1 Contrôles d'accès sur la mémoire et les indices RAG

Appliquer des contrôles d'accès granulaires sur chaque collection de vecteurs.

 #8.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que les règles de contrôle d'accès au niveau des lignes et des espaces de noms restreignent les opérations d'insertion, de suppression et de requête par locataire, par collection ou par étiquette de document.
 #8.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les clés d'API ou les jetons JWT contiennent des revendications à portée limitée (par exemple, identifiants de collection, verbes d'action) et qu'ils soient renouvelés au moins une fois par trimestre.
 #8.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que les tentatives d'escalade de privilèges (par exemple des requêtes de similarité entre espaces de noms) sont détectées et journalisées dans un SIEM dans les 5 minutes.
 #8.1.4    Niveau: 2    Rôle: D/V
 Vérifiez que les journaux d'audit de la base de données vectorielle enregistrent l'identifiant du sujet, l'opération, l'ID de vecteur/espace de noms, le seuil de similarité et le nombre de résultats.
 #8.1.5    Niveau: 3    Rôle: V
 Vérifiez que les décisions d'accès sont testées pour détecter des failles de contournement à chaque mise à niveau des moteurs ou lorsque les règles de partitionnement d'index changent.

---

### C8.2 Nettoyage et validation des embeddings

Effectuer un pré-filtrage du texte pour les informations personnellement identifiables (PII), les masquer ou les pseudonymiser avant la vectorisation, et, éventuellement, post-traiter les représentations vectorielles pour éliminer les signaux résiduels.

 #8.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les PII et les données réglementées sont détectées par des classificateurs automatisés et masquées, tokenisées ou supprimées avant l'embedding.
 #8.2.2    Niveau: 1    Rôle: D
 Vérifiez que les pipelines d'embeddings rejettent ou mettent en quarantaine les entrées contenant du code exécutable ou des artefacts non UTF-8 susceptibles de contaminer l'index.
 #8.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que l’assainissement par confidentialité différentielle locale ou métrique est appliqué aux embeddings de phrases dont la distance par rapport à tout jeton d’informations personnellement identifiables (PII) connu est inférieure à un seuil configurable.
 #8.2.4    Niveau: 2    Rôle: V
 Vérifiez que l’efficacité de la sanitisation (par exemple, le rappel de la rédaction des PII, dérive sémantique) est validée au moins semestriellement sur des corpus de référence.
 #8.2.5    Niveau: 3    Rôle: D/V
 Vérifiez que les configurations de sanitisation sont versionnées et que les modifications font l'objet d'une revue par les pairs.

---

### C8.3 Expiration de la mémoire, Révocation et Suppression

Le RGPD et des lois similaires exigent une suppression en temps utile ; les stockages vectoriels doivent donc prendre en charge les TTLs, les suppressions définitives et le tombstoning afin que les vecteurs révoqués ne puissent pas être récupérés ni réindexés.

 #8.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les vecteurs et tous les enregistrements de métadonnées portent un TTL ou une étiquette de rétention explicite, et que ces éléments sont pris en charge par les tâches de nettoyage automatisées.
 #8.3.2    Niveau: 1    Rôle: D/V
 Vérifiez que les demandes de suppression initiées par l'utilisateur purgent les vecteurs, les métadonnées, les copies en cache et les indices dérivés dans un délai de 30 jours.
 #8.3.3    Niveau: 2    Rôle: D
 Vérifiez que les suppressions logiques sont suivies d'un déchiquetage cryptographique des blocs de stockage si le matériel le prend en charge, ou par la destruction des clés du Key Vault.
 #8.3.4    Niveau: 3    Rôle: D/V
 Vérifiez que les vecteurs expirés sont exclus des résultats de la recherche du plus proche voisin en < 500 ms après l'expiration.

---

### C8.4 Prévenir l'inversion des embeddings et la fuite

Des défenses récentes—superposition de bruit, réseaux de projection, perturbation des neurones de confidentialité et chiffrement au niveau de la couche applicative—peuvent faire chuter les taux d'inversion au niveau des jetons en dessous de 5%.

 #8.4.1    Niveau: 1    Rôle: V
 Vérifier qu’un modèle de menace formel couvrant les attaques d’inversion, d’appartenance et d’inférence d’attributs existe et est révisé annuellement.
 #8.4.2    Niveau: 2    Rôle: D/V
 Vérifiez que le chiffrement au niveau de l'application ou le chiffrement recherchable protège les vecteurs contre les lectures directes par les administrateurs d'infrastructure ou le personnel cloud.
 #8.4.3    Niveau: 3    Rôle: V
 Vérifiez que les paramètres de défense (ε pour la confidentialité différentielle, bruit σ, rang de projection k) équilibrent la confidentialité des jetons ≥ 99 % et l'utilité ≤ 3 % de perte de précision.
 #8.4.4    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques de résilience à l’inversion font partie des portes de déploiement pour les mises à jour des modèles, avec des budgets de régression définis.

---

### C8.5 Contrôle de la portée pour la mémoire spécifique à l'utilisateur

La fuite entre locataires demeure l’un des principaux risques liés à la RAG : des requêtes de similarité mal filtrées peuvent révéler les documents privés d’un autre client.

 #8.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque requête de récupération est filtrée a posteriori par l'ID du locataire/utilisateur avant d'être transmise à l'invite du modèle de langage.
 #8.5.2    Niveau: 1    Rôle: D
 Vérifiez que les noms de collection ou les identifiants avec espace de noms soient salés par utilisateur ou par locataire afin que les vecteurs ne puissent pas entrer en collision entre les portées.
 #8.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que les résultats de similarité supérieurs à un seuil de distance configurable mais en dehors du champ d'application de l'appelant sont ignorés et déclenchent des alertes de sécurité.
 #8.5.4    Niveau: 2    Rôle: V
 Vérifiez que les tests de stress multi-locataires simulent des requêtes adverses visant à récupérer des documents hors périmètre et démontrent l'absence de fuite.
 #8.5.5    Niveau: 3    Rôle: D/V
 Vérifiez que les clés de chiffrement sont séparées par locataire, assurant l'isolement cryptographique même si le stockage physique est partagé.

---

### C8.6 Sécurité avancée du système de mémoire

Contrôles de sécurité pour des architectures de mémoire sophistiquées, y compris la mémoire épisodique, la mémoire sémantique et la mémoire de travail, avec des exigences d'isolation et de validation spécifiques.

 #8.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que les différents types de mémoire (mémoire épisodique, mémoire sémantique, mémoire de travail) disposent de contextes de sécurité isolés avec des contrôles d'accès basés sur les rôles, des clés de chiffrement distinctes et des schémas d'accès documentés pour chaque type de mémoire.
 #8.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que les processus de consolidation de la mémoire intègrent une validation de sécurité afin de prévenir l'injection de mémoires malveillantes par la sanitisation du contenu, la vérification de la source et les vérifications d'intégrité avant le stockage.
 #8.6.3    Niveau: 2    Rôle: D/V
 Vérifiez que les requêtes de récupération en mémoire sont validées et assainies afin d'empêcher l'extraction d'informations non autorisées par l'analyse des motifs de requête, l'application des contrôles d'accès et le filtrage des résultats.
 #8.6.4    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes d'effacement de la mémoire effacent les informations sensibles de manière sécurisée, avec des garanties d'effacement cryptographique, en utilisant la suppression de clés, l'écrasement sur plusieurs passes ou la suppression sécurisée basée sur le matériel avec des certificats de vérification.
 #8.6.5    Niveau: 3    Rôle: D/V
 Vérifier que l’intégrité du système mémoire est surveillée en continu pour détecter des modifications ou corruptions non autorisées grâce à des sommes de contrôle, des journaux d’audit et des alertes automatisées lorsque le contenu mémoire change en dehors des opérations normales.

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

## 9 Orchestration autonome et sécurité des actions agentiques

### Objectif de contrôle

Assurez-vous que les systèmes d'IA autonomes ou multi-agent ne puissent exécuter que des actions qui sont explicitement prévues, authentifiées, auditées et dans des limites de coût et de risque. Cela protège contre des menaces telles que la compromission de systèmes autonomes, l'utilisation abusive d'outils, la détection de boucle d'agent, le détournement des communications, l'usurpation d'identité, la manipulation d'essaims et la manipulation des intentions.

---

### 9.1 Agent Planification-des-tâches & Budgets de récursivité

Ralentir les plans récursifs et imposer des points de contrôle humains pour les actions privilégiées.

 #9.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que la profondeur maximale de récursion, la largeur d'exploration, le temps réel (wall-clock time), les jetons et le coût monétaire par exécution d'un agent sont centralement configurés et sous contrôle de version.
 #9.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les actions privilégiées ou irréversibles (par exemple, des commits de code, des transferts financiers) nécessitent une approbation humaine explicite via un canal auditable avant l'exécution.
 #9.1.3    Niveau: 2    Rôle: D
 Vérifiez que les moniteurs de ressources en temps réel déclenchent l'interruption du circuit-breaker lorsque n'importe quel seuil budgétaire est dépassé, ce qui met fin à l'expansion ultérieure des tâches.
 #9.1.4    Niveau: 2    Rôle: D/V
 Vérifier que les événements de disjoncteur sont enregistrés avec l'identifiant de l'agent, la condition de déclenchement et l'état du plan capturé pour examen médico-légal.
 #9.1.5    Niveau: 3    Rôle: V
 Vérifiez que les tests de sécurité couvrent les scénarios budget-exhaustion et runaway-plan, en confirmant un arrêt sûr sans perte de données.
 #9.1.6    Niveau: 3    Rôle: D
 Vérifiez que les politiques budgétaires sont exprimées sous forme de policy-as-code et appliquées dans CI/CD pour empêcher la dérive de configuration.

---

### 9.2 Mise en bac à sable des outils et des plug-ins

Isoler les interactions avec les outils afin de prévenir tout accès non autorisé au système ou l'exécution de code.

 #9.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque outil/plug-in s'exécute dans un bac à sable au niveau OS, conteneur ou WASM, avec des politiques de moindre privilège pour le système de fichiers, le réseau et les appels système.
 #9.2.2    Niveau: 1    Rôle: D/V
 Vérifier que les quotas de ressources du bac à sable (CPU, mémoire, disque, sortie réseau) et les timeouts d’exécution sont appliqués et consignés.
 #9.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les fichiers binaires d’outils ou les descripteurs sont signés numériquement ; les signatures sont vérifiées avant le chargement.
 #9.2.4    Niveau: 2    Rôle: V
 Vérifiez que la télémétrie du bac à sable est acheminée vers un SIEM ; les anomalies (par exemple des tentatives de connexions sortantes) déclenchent des alertes.
 #9.2.5    Niveau: 3    Rôle: V
 Vérifiez que les plugins à haut risque subissent une revue de sécurité et des tests de pénétration avant le déploiement en production.
 #9.2.6    Niveau: 3    Rôle: D/V
 Vérifiez que les tentatives d'évasion du bac à sable sont automatiquement bloquées et que le plugin fautif est mis en quarantaine en attendant l'enquête.

---

### 9.3 Boucle autonome et bornage des coûts

Détecter et arrêter la récursion non maîtrisée entre agents et les explosions de coûts.

 #9.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les appels inter-agent incluent une limite de sauts ou un TTL que l’environnement d’exécution décrémente et fasse respecter.
 #9.3.2    Niveau: 2    Rôle: D
 Vérifiez que les agents maintiennent un identifiant unique du graphe d'invocation afin de repérer l'auto-invocation ou les motifs cycliques.
 #9.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les compteurs cumulatifs d'unités de calcul et de consommation sont suivis pour chaque chaîne de requêtes ; en cas de dépassement de la limite, la chaîne est interrompue.
 #9.3.4    Niveau: 3    Rôle: V
 Vérifiez que l'analyse formelle ou la vérification de modèles démontre l'absence de récursion non bornée dans les protocoles des agents.
 #9.3.5    Niveau: 3    Rôle: D
 Vérifiez que les événements d'arrêt de boucle génèrent des alertes et alimentent des métriques d'amélioration continue.

---

### 9.4 Protection contre les abus au niveau du protocole

Des canaux de communication sécurisés entre les agents et les systèmes externes afin de prévenir le piratage ou la manipulation.

 #9.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que tous les messages entre l'agent et l'outil, ainsi que ceux entre les agents, sont authentifiés (par exemple TLS mutuel ou JWT) et chiffrés de bout en bout.
 #9.4.2    Niveau: 1    Rôle: D
 Vérifiez que les schémas sont strictement validés; les champs inconnus ou les messages malformés sont rejetés.
 #9.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que les contrôles d'intégrité (MAC ou signatures numériques) couvrent l'intégralité de la charge utile du message, y compris les paramètres de l'outil.
 #9.4.4    Niveau: 2    Rôle: D
 Vérifiez que la protection anti-rejeu (nonces ou fenêtres d'horodatage) est appliquée au niveau de la couche protocole.
 #9.4.5    Niveau: 3    Rôle: V
 Vérifiez que les implémentations de protocoles subissent des tests de fuzzing et une analyse statique pour des failles d'injection ou de désérialisation.

---

### 9.5 Identité de l'agent et preuve d'altération

Veillez à ce que les actions soient attribuables et que les modifications soient détectables.

 #9.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que chaque instance d’agent possède une identité cryptographique unique (paire de clés ou crédentiel enraciné dans le matériel).
 #9.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que toutes les actions des agents sont signées et horodatées; les journaux contiennent la signature pour assurer la non-répudiation.
 #9.5.3    Niveau: 2    Rôle: V
 Vérifiez que les journaux à preuve d'altération sont stockés sur un support en mode append-only ou write-once.
 #9.5.4    Niveau: 3    Rôle: D
 Vérifiez que les clés d'identité se renouvellent selon un calendrier défini et en présence d'indicateurs de compromission.
 #9.5.5    Niveau: 3    Rôle: D/V
 Vérifiez que les tentatives d'usurpation ou de conflit de clés déclenchent une mise en quarantaine immédiate de l'agent affecté.

---

### 9.6 Réduction du risque des essaims multi-agents

Atténuer les risques liés au comportement collectif par l'isolation et la modélisation formelle de la sécurité.

 #9.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que les agents opérant dans différents domaines de sécurité s'exécutent dans des environnements d'exécution isolés ou dans des segments réseau isolés.
 #9.6.2    Niveau: 3    Rôle: V
 Vérifiez que les comportements d’essaims sont modélisés et vérifiés formellement pour la vivacité et la sécurité avant le déploiement.
 #9.6.3    Niveau: 3    Rôle: D
 Vérifiez que les moniteurs d'exécution détectent les comportements dangereux émergents (par exemple des oscillations, des blocages) et déclenchent une action corrective.

---

### 9.7 Authentification des utilisateurs et des outils / Autorisation

Implémenter des contrôles d'accès robustes pour chaque action déclenchée par l'agent.

 #9.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les agents s’authentifient en tant que principaux de premier ordre auprès des systèmes en aval, sans jamais réutiliser les identifiants des utilisateurs finaux.
 #9.7.2    Niveau: 2    Rôle: D
 Vérifiez que les politiques d'autorisation à granularité fine restreignent les outils qu'un agent peut invoquer et les paramètres qu'il peut fournir.
 #9.7.3    Niveau: 2    Rôle: V
 Vérifier que les contrôles d'autorisation sont réévalués à chaque appel (autorisation continue), et non seulement au démarrage de la session.
 #9.7.4    Niveau: 3    Rôle: D
 Vérifiez que les privilèges délégués expirent automatiquement et nécessitent un nouveau consentement après un délai d'expiration ou un changement de portée.

---

### 9.8 Agent-à-Agent Sécurité des communications

Chiffrez et protégez l'intégrité de tous les messages échangés entre les agents afin de contrer l'écoute clandestine et l'altération.

 #9.8.1    Niveau: 1    Rôle: D/V
 Vérifiez que l’authentification mutuelle et le chiffrement à secret parfait (par exemple TLS 1.3) sont obligatoires pour les canaux d’agents.
 #9.8.2    Niveau: 1    Rôle: D
 Vérifiez que l'intégrité du message et son origine sont vérifiées avant le traitement ; en cas d'échec, des alertes sont déclenchées et le message est rejeté.
 #9.8.3    Niveau: 2    Rôle: D/V
 Vérifiez que les métadonnées de communication (horodatages, numéros de séquence) sont enregistrées pour faciliter la reconstitution médico-légale.
 #9.8.4    Niveau: 3    Rôle: V
 Vérifiez que la vérification formelle ou la vérification par modèle confirme que les machines à états de protocole ne peuvent pas être conduites vers des états non sûrs.

---

### 9.9 Vérification de l'intention et application des contraintes

Vérifiez que les actions de l'agent s'alignent sur l'intention déclarée par l'utilisateur et sur les contraintes du système.

 #9.9.1    Niveau: 1    Rôle: D
 Vérifiez que les solveurs de contraintes pré-exécution vérifient les actions proposées par rapport à des règles de sécurité et de politique codées en dur.
 #9.9.2    Niveau: 2    Rôle: D/V
 Vérifiez que les actions à fort impact (financières, destructrices et sensibles à la vie privée) nécessitent une confirmation d'intention explicite de la part de l'utilisateur qui les initie.
 #9.9.3    Niveau: 2    Rôle: V
 Vérifiez que les vérifications des post-conditions valident que les actions réalisées ont produit les effets escomptés sans effets secondaires ; les écarts déclenchent un retour en arrière.
 #9.9.4    Niveau: 3    Rôle: V
 Vérifiez que les méthodes formelles (par exemple, la vérification de modèles et la démonstration de théorèmes) ou les tests basés sur les propriétés démontrent que les plans des agents satisfont toutes les contraintes déclarées.
 #9.9.5    Niveau: 3    Rôle: D
 Vérifiez que les incidents d'intent-mismatch ou de constraint-violation alimentent les cycles d'amélioration continue et le partage de renseignements sur les menaces.

---

### 9.10 Raisonnement des agents, Stratégie et Sécurité

Sélection et exécution sécurisées de différentes stratégies de raisonnement, y compris ReAct, Chain-of-Thought et Tree-of-Thoughts.

 #9.10.1    Niveau: 1    Rôle: D/V
 Vérifier que la sélection de la stratégie de raisonnement utilise des critères déterministes (complexité de l’entrée, type de tâche, contexte de sécurité) et que des entrées identiques produisent des sélections de stratégie identiques dans le même contexte de sécurité.
 #9.10.2    Niveau: 1    Rôle: D/V
 Vérifiez que chaque stratégie de raisonnement (ReAct, Chain-of-Thought, Tree-of-Thoughts) dispose d'une validation des entrées dédiée, d'une sanitisation des sorties et de limites de temps d'exécution propres à son approche cognitive.
 #9.10.3    Niveau: 2    Rôle: D/V
 Vérifiez que les transitions entre les stratégies de raisonnement sont enregistrées avec le contexte complet, y compris les caractéristiques d'entrée, les valeurs des critères de sélection et les métadonnées d'exécution pour la reconstruction de la trace d'audit.
 #9.10.4    Niveau: 2    Rôle: D/V
 Vérifiez que le raisonnement par arbre des pensées inclut des mécanismes d'élagage des branches qui interrompent l'exploration lorsque des violations des politiques, des limites de ressources ou des frontières de sécurité sont détectées.
 #9.10.5    Niveau: 2    Rôle: D/V
 Vérifiez que les cycles ReAct (Reason-Act-Observe) intègrent des points de contrôle de validation à chaque phase : vérification des étapes de raisonnement, autorisation d'action et assainissement des observations avant de poursuivre.
 #9.10.6    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques de performance de la stratégie de raisonnement (temps d'exécution, utilisation des ressources, qualité de la sortie) sont surveillées par des alertes automatiques lorsque les métriques s'écartent au-delà des seuils configurés.
 #9.10.7    Niveau: 3    Rôle: D/V
 Vérifiez que les approches de raisonnement hybrides qui combinent plusieurs stratégies respectent la validation des entrées et les contraintes de sortie de toutes les stratégies constitutives sans contourner aucun contrôle de sécurité.
 #9.10.8    Niveau: 3    Rôle: D/V
 Vérifiez que les tests de sécurité des stratégies de raisonnement incluent le fuzzing avec des entrées malformées, des requêtes adversariales conçues pour forcer le basculement de la stratégie, et des tests des conditions aux limites pour chaque approche cognitive.

---

### 9.11 Gestion du cycle de vie et de la sécurité de l'agent

Initialisation sécurisée de l'agent, transitions d'état et terminaison avec des journaux d'audit cryptographiques et des procédures de récupération définies.

 #9.11.1    Niveau: 1    Rôle: D/V
 Vérifiez que l'initialisation de l'agent inclut l'établissement d'une identité cryptographique avec des identifiants basés sur le matériel et des journaux d'audit de démarrage immuables contenant l'ID de l'agent, l'horodatage, le hachage de la configuration et les paramètres d'initialisation.
 #9.11.2    Niveau: 2    Rôle: D/V
 Vérifiez que les transitions d'état des agents sont signées cryptographiquement, horodatées et enregistrées avec un contexte complet incluant les événements déclencheurs, le hachage de l'état précédent, le hachage du nouvel état, et les validations de sécurité effectuées.
 #9.11.3    Niveau: 2    Rôle: D/V
 Vérifiez que les procédures d'arrêt de l'agent incluent un effacement sécurisé de la mémoire utilisant l'effacement cryptographique ou l'écriture sur plusieurs passes, la révocation des informations d'identification avec notification à l'autorité de certification, et la génération de certificats de terminaison à preuve d'altération.
 #9.11.4    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes de récupération des agents valident l'intégrité de l'état à l'aide de sommes de contrôle cryptographiques (SHA-256 au minimum) et basculent vers des états connus et valides lorsque la corruption est détectée, avec des alertes automatisées et des exigences d'approbation manuelle.
 #9.11.5    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes de persistance des agents chiffrent les données d'état sensibles avec des clés AES-256 par agent et mettent en œuvre une rotation sécurisée des clés selon des calendriers configurables (maximum 90 jours) avec un déploiement sans temps d'arrêt.

---

### 9.12 Cadre de sécurité de l’intégration des outils

Contrôles de sécurité pour le chargement dynamique d'outils, l'exécution et la validation des résultats, avec des processus d'évaluation des risques et d'approbation définis.

 #9.12.1    Niveau: 1    Rôle: D/V
 Vérifiez que les descripteurs d'outils incluent des métadonnées de sécurité précisant les privilèges requis (lecture/écriture/exécution), les niveaux de risque (faible/moyen/élevé), les limites de ressources (CPU, mémoire, réseau), et les exigences de validation documentées dans les manifestes d'outils.
 #9.12.2    Niveau: 1    Rôle: D/V
 Vérifiez que les résultats d'exécution des outils sont validés par rapport aux schémas attendus (Schéma JSON, Schéma XML) et aux politiques de sécurité (sanitisation de la sortie, classification des données) avant l'intégration avec des limites de délai d'attente et des procédures de gestion des erreurs.
 #9.12.3    Niveau: 2    Rôle: D/V
 Vérifiez que les journaux d'interaction des outils incluent un contexte de sécurité détaillé, y compris l'utilisation des privilèges, les schémas d'accès aux données, le temps d'exécution, la consommation des ressources et les codes de retour, avec une journalisation structurée pour l’intégration dans un SIEM.
 #9.12.4    Niveau: 2    Rôle: D/V
 Vérifiez que les mécanismes de chargement dynamique des outils valident les signatures numériques en utilisant une infrastructure PKI et mettez en œuvre des protocoles de chargement sécurisés avec une isolation sandbox et une vérification des permissions avant l’exécution.
 #9.12.5    Niveau: 3    Rôle: D/V
 Vérifiez que les évaluations de sécurité des outils sont déclenchées automatiquement pour les nouvelles versions, avec des portes d'approbation obligatoires comprenant l'analyse statique, les tests dynamiques et la revue par l'équipe de sécurité, avec des critères d'approbation documentés et des exigences de SLA.

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

## 10 Robustesse adversarielle et défense de la vie privée

### Objectif de contrôle

Veiller à ce que les modèles d'IA restent fiables, respectueux de la vie privée et résistants à l'abus lorsqu'ils sont confrontés à des attaques d'évasion, d'inférence, d'extraction ou d'empoisonnement.

---

### 10.1 Alignement et sécurité du modèle

Évitez les sorties nuisibles ou qui enfreignent les politiques.

 #10.1.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'une suite de tests d'alignement (prompts red-team, sondes de jailbreak, contenu interdit) est versionnée et exécutée à chaque version du modèle.
 #10.1.2    Niveau: 1    Rôle: D
 Vérifiez que les garde-fous relatifs au refus et à la complétion sûre sont appliqués.
 #10.1.3    Niveau: 2    Rôle: D/V
 Vérifiez que l’évaluateur automatisé mesure le taux de contenu nocif et signale les régressions au-delà d’un seuil défini.
 #10.1.4    Niveau: 2    Rôle: D
 Vérifiez que la formation anti-jailbreak est documentée et reproductible.
 #10.1.5    Niveau: 3    Rôle: V
 Vérifiez que les preuves formelles de conformité des politiques ou une surveillance certifiée couvrent des domaines critiques.

---

### 10.2 Renforcement des exemples adverses

Renforcer la résilience face aux entrées manipulées. Un entraînement adversarial robuste et une évaluation par benchmarks constituent les meilleures pratiques actuelles.

 #10.2.1    Niveau: 1    Rôle: D
 Vérifiez que les dépôts de projets incluent des configurations d'entraînement adversarial avec des graines reproductibles.
 #10.2.2    Niveau: 2    Rôle: D/V
 Vérifiez que la détection d'exemples adversariaux déclenche des alertes bloquantes dans les pipelines de production.
 #10.2.4    Niveau: 3    Rôle: V
 Vérifiez que les preuves de robustesse certifiée ou les certificats à bornes d'intervalle couvrent au moins les classes les plus critiques.
 #10.2.5    Niveau: 3    Rôle: V
 Vérifiez que les tests de régression utilisent des attaques adaptatives pour confirmer l’absence de perte de robustesse mesurable.

---

### 10.3 Atténuation de l'inférence d'appartenance

Limiter la capacité à déterminer si un enregistrement faisait partie des données d'entraînement. La confidentialité différentielle et le masquage du score de confiance restent les défenses les plus efficaces à ce jour.

 #10.3.1    Niveau: 1    Rôle: D
 Vérifiez que la régularisation de l'entropie par requête ou la mise à l'échelle par température réduisent les prédictions trop confiantes.
 #10.3.2    Niveau: 2    Rôle: D
 Vérifiez que l’entraînement utilise une optimisation différentiellement privée bornée par ε pour des ensembles de données sensibles.
 #10.3.3    Niveau: 2    Rôle: V
 Vérifiez que les simulations d'attaque (shadow-model ou black-box) affichent l'AUC d'attaque ≤ 0.60 sur des données hors-échantillon.

---

### 10.4 Modèle-Inversion Résistance

Empêcher la reconstruction d'attributs privés. Des enquêtes récentes mettent en avant la troncation des sorties et les garanties de confidentialité différentielle comme des défenses pratiques.

 #10.4.1    Niveau: 1    Rôle: D
 Vérifiez que les attributs sensibles ne sont jamais directement affichés; là où c'est nécessaire, utilisez des seaux ou des transformations à sens unique.
 #10.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les limites de débit des requêtes ralentissent les requêtes adaptatives répétées provenant du même principal.
 #10.4.3    Niveau: 2    Rôle: D
 Vérifiez que le modèle est entraîné avec du bruit préservant la vie privée.

---

### 10.5 Défense contre Model-Extraction

Détecter et dissuader le clonage non autorisé. Le filigrage et l’analyse des motifs de requête sont recommandés.

 #10.5.1    Niveau: 1    Rôle: D
 Vérifiez que les passerelles d’inférence appliquent des limites de débit globales et par clé API, réglées en fonction du seuil de mémorisation du modèle.
 #10.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les statistiques de query-entropy et d'input-plurality alimentent un détecteur d'extraction automatisé.
 #10.5.3    Niveau: 2    Rôle: V
 Vérifiez que les filigranes fragiles ou probabilistes peuvent être démontrés avec p < 0.01 en ≤ 1 000 requêtes contre un clone suspecté.
 #10.5.4    Niveau: 3    Rôle: D
 Vérifiez que les clés de filigrane et les ensembles déclencheurs sont stockés dans un module matériel de sécurité et renouvelés chaque année.
 #10.5.5    Niveau: 3    Rôle: V
 Vérifiez que les événements d'alerte d'extraction incluent les requêtes malveillantes et qu'ils sont intégrés aux playbooks de réponse aux incidents.

---

### 10.6 Détection des données empoisonnées au moment de l'inférence

Identifier et neutraliser les entrées présentant une porte dérobée ou empoisonnées.

 #10.6.1    Niveau: 1    Rôle: D
 Vérifier que les entrées passent par un détecteur d’anomalies (par exemple STRIP, score de cohérence) avant l’inférence du modèle.
 #10.6.2    Niveau: 1    Rôle: V
 Vérifiez que les seuils du détecteur sont ajustés sur des ensembles de validation propres et empoisonnés afin d'obtenir moins de 5 % de faux positifs.
 #10.6.3    Niveau: 2    Rôle: D
 Vérifiez que les entrées signalées comme empoisonnées déclenchent le blocage doux et les workflows de révision humaine.
 #10.6.4    Niveau: 2    Rôle: V
 Vérifiez que les détecteurs sont soumis à des tests de résistance avec des attaques par porte dérobée adaptatives et sans déclencheur.
 #10.6.5    Niveau: 3    Rôle: D
 Vérifiez que les métriques d'efficacité de la détection sont enregistrées et réévaluées périodiquement avec des renseignements sur les menaces à jour.

---

### 10.7 Adaptation dynamique de la politique de sécurité

Mises à jour de la politique de sécurité en temps réel basées sur l'intelligence des menaces et l'analyse comportementale.

 #10.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les politiques de sécurité peuvent être mises à jour dynamiquement sans redémarrage de l’agent, tout en maintenant l’intégrité des versions des politiques.
 #10.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que les mises à jour des politiques sont signées cryptographiquement par du personnel de sécurité autorisé et validées avant leur application.
 #10.7.3    Niveau: 2    Rôle: D/V
 Vérifiez que les modifications dynamiques des politiques sont enregistrées avec des traces d'audit complètes, y compris la justification, les chaînes d'approbation et les procédures de rollback.
 #10.7.4    Niveau: 3    Rôle: D/V
 Vérifiez que les mécanismes de sécurité adaptatifs ajustent la sensibilité de la détection des menaces en fonction du contexte de risque et des comportements.
 #10.7.5    Niveau: 3    Rôle: D/V
 Vérifiez que les décisions d'adaptation des politiques sont explicables et incluez des traces probantes pour l'examen par l'équipe de sécurité.

---

### 10.8 Analyse de sécurité basée sur la réflexion

Validation de sécurité par l'auto-réflexion de l'agent et l'analyse métacognitive.

 #10.8.1    Niveau: 1    Rôle: D/V
 Vérifiez que les mécanismes de réflexion des agents incluent une auto-évaluation axée sur la sécurité des décisions et des actions.
 #10.8.2    Niveau: 2    Rôle: D/V
 Vérifiez que les sorties de réflexion sont validées afin d'empêcher la manipulation des mécanismes d'auto-évaluation par des entrées adverses.
 #10.8.3    Niveau: 2    Rôle: D/V
 Vérifiez que l’analyse de sécurité métacognitive identifie les biais potentiels, les manipulations ou les compromissions dans les processus de raisonnement de l’agent.
 #10.8.4    Niveau: 3    Rôle: D/V
 Vérifiez que les avertissements de sécurité basés sur la réflexion déclenchent une surveillance renforcée et des workflows d'intervention humaine potentiels.
 #10.8.5    Niveau: 3    Rôle: D/V
 Vérifiez que l'apprentissage continu à partir des réflexions sur la sécurité améliore la détection des menaces sans dégrader les fonctionnalités légitimes.

---

### 10.9 Évolution et sécurité de l'auto-amélioration

Mesures de sécurité pour les systèmes d'agents capables d'auto-modification et d'évolution.

 #10.9.1    Niveau: 1    Rôle: D/V
 Vérifiez que les capacités d'auto-modification sont restreintes aux zones sûres désignées, avec des bornes de vérification formelle.
 #10.9.2    Niveau: 2    Rôle: D/V
 Vérifiez que les propositions d’évolution font l’objet d’une évaluation de l’impact sur la sécurité avant leur mise en œuvre.
 #10.9.3    Niveau: 2    Rôle: D/V
 Vérifiez que les mécanismes d'auto-amélioration incluent des capacités de retour en arrière avec vérification d'intégrité.
 #10.9.4    Niveau: 3    Rôle: D/V
 Vérifiez que la sécurité de l'apprentissage par méta-apprentissage empêche la manipulation adversarielle des algorithmes d'amélioration.
 #10.9.5    Niveau: 3    Rôle: D/V
 Vérifier que l'auto-amélioration récursive est bornée par des contraintes de sécurité formelles, avec des preuves mathématiques de convergence.

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

Maintenir des garanties de confidentialité rigoureuses tout au long du cycle de vie de l'IA—collecte, entraînement, inférence et réponse aux incidents—afin que les données personnelles ne soient traitées qu'avec un consentement éclairé, une portée minimale nécessaire, un effacement vérifiable et des garanties de confidentialité formelles.

---

### 11.1 Anonymisation et minimisation des données

 #11.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que les identifiants directs et quasi-identifiants sont supprimés et hachés.
 #11.1.2    Niveau: 2    Rôle: D/V
 Vérifiez que les audits automatisés mesurent la k-anonymité et l-diversité et alertent lorsque les seuils tombent en dessous de la politique.
 #11.1.3    Niveau: 2    Rôle: V
 Vérifiez que les rapports d'importance des caractéristiques du modèle démontrent qu'il n'y a pas de fuite d'identifiants au-delà de ε = 0.01 d'information mutuelle.
 #11.1.4    Niveau: 3    Rôle: V
 Vérifiez que des preuves formelles ou une certification des données synthétiques montrent un risque de réidentification ≤ 0.05, même lors d’attaques de jonction.

---

### 11.2 Droit à l'oubli et mise en œuvre de la suppression

 #11.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les demandes de suppression de données à caractère personnel se propagent vers les ensembles de données brutes, les points de contrôle, les représentations vectorielles, les journaux et les sauvegardes dans le cadre des accords de niveau de service dont la durée est inférieure à 30 jours.
 #11.2.2    Niveau: 2    Rôle: D
 Vérifiez que les routines "machine-unlearning" réentraînent physiquement ou approximent la suppression en utilisant des algorithmes de désapprentissage certifiés.
 #11.2.3    Niveau: 2    Rôle: V
 Vérifiez que l'évaluation du modèle fantôme prouve que les enregistrements oubliés influencent moins de 1% des sorties après le désapprentissage.
 #11.2.4    Niveau: 3    Rôle: V
 Vérifiez que les événements de suppression sont consignés de manière immuable et auditable pour les régulateurs.

---

### 11.3 Garanties de confidentialité-différentielle

 #11.3.1    Niveau: 2    Rôle: D/V
 Vérifiez que les tableaux de bord de comptabilité de la perte de confidentialité alertent lorsque ε cumulatif dépasse les seuils de la politique.
 #11.3.2    Niveau: 2    Rôle: V
 Vérifiez que les audits de confidentialité en boîte noire estiment ε̂ dans une marge de 10% par rapport à la valeur déclarée.
 #11.3.3    Niveau: 3    Rôle: V
 Vérifiez que les preuves formelles couvrent tous les ajustements fins après l'entraînement et les représentations vectorielles.

---

### 11.4 Limitation des objectifs et protection contre la dérive du périmètre

 #11.4.1    Niveau: 1    Rôle: D
 Vérifiez que chaque jeu de données et chaque point de contrôle du modèle portent une étiquette de finalité lisible par machine, alignée sur le consentement initial.
 #11.4.2    Niveau: 1    Rôle: D/V
 Vérifiez que les moniteurs d'exécution détectent les requêtes incompatibles avec l'objectif déclaré et déclenchent un refus doux.
 #11.4.3    Niveau: 3    Rôle: D
 Vérifiez que les mécanismes de contrôle basés sur des politiques en tant que code bloquent le redéploiement des modèles vers de nouveaux domaines sans évaluation DPIA.
 #11.4.4    Niveau: 3    Rôle: V
 Vérifiez que les preuves de traçabilité formelles démontrent que chaque cycle de vie des données personnelles demeure dans la portée consentie.

---

### 11.5 Gestion du consentement et traçage sur base légale

 #11.5.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'une plateforme de gestion des consentements (CMP) enregistre le statut d'opt-in, la finalité et la durée de conservation par sujet de données.
 #11.5.2    Niveau: 2    Rôle: D
 Vérifiez que les API exposent des jetons de consentement; les modèles doivent valider la portée du jeton avant l’inférence.
 #11.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que le consentement refusé ou retiré entraîne l’arrêt des pipelines de traitement dans les 24 heures.

---

### 11.6 Apprentissage fédéré avec des contrôles de confidentialité

 #11.6.1    Niveau: 1    Rôle: D
 Vérifiez que les mises à jour côté client utilisent l’ajout de bruit de confidentialité différentielle locale avant l’agrégation.
 #11.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que les métriques d’entraînement respectent la confidentialité différentielle et ne révèlent jamais la perte d’un seul client.
 #11.6.3    Niveau: 2    Rôle: V
 Vérifiez que l'agrégation résistante à l'empoisonnement (par exemple Krum/Trimmed-Mean) est activée.
 #11.6.4    Niveau: 3    Rôle: V
 Vérifiez que les preuves formelles démontrent le budget ε global avec une perte d’utilité de moins de 5.

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

## C12 Surveillance, journalisation et détection d’anomalies

### Objectif de contrôle

Cette section fournit les exigences pour offrir une visibilité en temps réel et forensique sur ce que le modèle et les autres composants d'IA voient, font et renvoient, afin que les menaces puissent être détectées, triées et que l’on puisse en tirer des enseignements.

### C12.1 Journalisation des requêtes et des réponses

 #12.1.1    Niveau: 1    Rôle: D/V
 Vérifiez que toutes les requêtes des utilisateurs et les réponses du modèle sont enregistrées avec des métadonnées appropriées (par exemple horodatage, identifiant utilisateur, identifiant de session, version du modèle).
 #12.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que les journaux sont stockés dans des dépôts sécurisés et à accès contrôlé, avec des politiques de rétention appropriées et des procédures de sauvegarde.
 #12.1.3    Niveau: 1    Rôle: D/V
 Vérifiez que les systèmes de stockage des journaux mettent en œuvre le chiffrement au repos et en transit afin de protéger les informations sensibles contenues dans les journaux.
 #12.1.4    Niveau: 1    Rôle: D/V
 Vérifiez que les données sensibles dans les invites et les sorties sont automatiquement caviardées ou masquées avant l'enregistrement dans les journaux, avec des règles de caviardage configurables pour les PII (informations personnellement identifiables), les identifiants et les informations propriétaires.
 #12.1.5    Niveau: 2    Rôle: D/V
 Vérifiez que les décisions de politique et les actions de filtrage de sécurité sont consignées avec un niveau de détail suffisant pour permettre l’audit et le débogage des systèmes de modération de contenu.
 #12.1.6    Niveau: 2    Rôle: D/V
 Vérifiez que l'intégrité des journaux est protégée, par exemple, par des signatures cryptographiques ou par un stockage en écriture seule.

---

### C12.2 Détection et alerte des abus

 #12.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que le système détecte et déclenche des alertes sur des modèles de jailbreak connus, des tentatives d'injection d'instructions et des entrées adversariales en utilisant une détection basée sur des signatures.
 #12.2.2    Niveau: 1    Rôle: D/V
 Vérifiez que le système s'intègre aux plateformes SIEM existantes en utilisant des formats de journalisation standard et des protocoles standard.
 #12.2.3    Niveau: 2    Rôle: D/V
 Vérifiez que les événements de sécurité enrichis incluent un contexte spécifique à l’IA, tel que les identifiants du modèle, les scores de confiance et les décisions du filtre de sécurité.
 #12.2.4    Niveau: 2    Rôle: D/V
 Vérifiez que la détection d’anomalies comportementales identifie des motifs de conversation inhabituels, des tentatives de réessai excessives ou des comportements d’exploration systématiques.
 #12.2.5    Niveau: 2    Rôle: D/V
 Vérifiez que les mécanismes d'alerte en temps réel notifient les équipes de sécurité lorsque des violations potentielles de la politique ou des tentatives d'attaque sont détectées.
 #12.2.6    Niveau: 2    Rôle: D/V
 Vérifiez que des règles personnalisées sont incluses pour détecter des schémas de menace spécifiques à l'IA, y compris les tentatives de jailbreak coordonnées, les campagnes d'injection de prompts et les attaques d'extraction de modèles.
 #12.2.7    Niveau: 3    Rôle: D/V
 Vérifiez que des workflows automatisés de réponse aux incidents peuvent isoler les modèles compromis, bloquer les utilisateurs malveillants et faire remonter les événements de sécurité critiques.

---

### C12.3 Détection de dérive du modèle

 #12.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que le système suit les mesures de performance de base telles que la précision, les scores de confiance, la latence et les taux d'erreur, à travers les versions du modèle et les périodes.
 #12.3.2    Niveau: 2    Rôle: D/V
 Vérifier que les alertes automatisées se déclenchent lorsque les métriques de performance dépassent des seuils de dégradation prédéfinis ou dévient de manière significative des lignes de base.
 #12.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les moniteurs de détection d’hallucinations identifient et signalent les cas où les sorties du modèle contiennent des informations factuellement incorrectes, incohérentes ou fabriquées.

---

### C12.4 Télémétrie de performance et de comportement

 #12.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que les métriques opérationnelles, notamment la latence des requêtes, la consommation de jetons, l'utilisation de la mémoire et le débit, sont collectées et surveillées en continu.
 #12.4.2    Niveau: 1    Rôle: D/V
 Vérifier que les taux de réussite et d'échec sont suivis avec une catégorisation des types d'erreurs et de leurs causes profondes.
 #12.4.3    Niveau: 2    Rôle: D/V
 Vérifier que la surveillance de l'utilisation des ressources inclut l'utilisation du GPU/CPU, la consommation de mémoire et les exigences de stockage, avec des alertes en cas de franchissement des seuils.

---

### C12.5 Planification et exécution de la réponse aux incidents d’IA

 #12.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les plans de réponse aux incidents prennent spécifiquement en compte les événements de sécurité liés à l'IA, y compris la compromission du modèle, l'empoisonnement des données et les attaques adversariales.
 #12.5.2    Niveau: 2    Rôle: D/V
 Vérifiez que les équipes d'intervention en cas d'incident disposent d'outils forensiques spécifiques à l'IA et d'une expertise pour enquêter sur le comportement des modèles et les vecteurs d'attaque.
 #12.5.3    Niveau: 3    Rôle: D/V
 Vérifiez que l'analyse post-incident inclut les considérations de réentraînement du modèle, les mises à jour des filtres de sécurité et l'intégration des leçons tirées dans les contrôles de sécurité.

---

### C12.5 Détection de la dégradation des performances de l'IA

Surveiller et détecter la dégradation des performances et de la qualité des modèles d'IA au fil du temps.

 #12.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que l'exactitude du modèle, la précision, le rappel et les scores F1 sont surveillés en continu et comparés aux seuils de référence.
 #12.5.2    Niveau: 1    Rôle: D/V
 Vérifiez que la détection de dérive des données surveille les changements de distribution des entrées qui pourraient affecter les performances du modèle.
 #12.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que la détection du concept drift identifie les changements dans la relation entre les entrées et les sorties attendues.
 #12.5.4    Niveau: 2    Rôle: D/V
 Vérifiez que la dégradation des performances déclenche des alertes automatisées et initie des flux de travail de réentraînement ou de remplacement du modèle.
 #12.5.5    Niveau: 3    Rôle: V
 Vérifiez que l'analyse des causes profondes de la dégradation corrèle les baisses de performance avec les modifications des données, les problèmes d'infrastructure ou les facteurs externes.

---

### C12.6 Visualisation du DAG et sécurité des flux de travail

Protégez les systèmes de visualisation des flux de travail contre les fuites d'informations et les attaques de manipulation.

 #12.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que les données de visualisation du graphe dirigé acyclique (GDA) sont nettoyées pour supprimer les informations sensibles avant le stockage ou la transmission.
 #12.6.2    Niveau: 1    Rôle: D/V
 Vérifiez que les contrôles d'accès à la visualisation du flux de travail garantissent que seuls les utilisateurs autorisés peuvent voir les chemins de décision des agents et les traces de raisonnement.
 #12.6.3    Niveau: 2    Rôle: D/V
 Vérifiez que l'intégrité des données DAG est protégée par des signatures cryptographiques et des mécanismes de stockage à preuve de manipulation.
 #12.6.4    Niveau: 2    Rôle: D/V
 Vérifiez que les systèmes de visualisation des flux de travail mettent en œuvre une validation des entrées afin de prévenir les attaques par injection via des données de nœud ou d'arête soigneusement conçues.
 #12.6.5    Niveau: 3    Rôle: D/V
 Vérifiez que les mises à jour en temps réel du DAG sont limitées en débit et validées afin de prévenir les attaques par déni de service sur les systèmes de visualisation.

---

### C12.7 Surveillance proactive du comportement de sécurité

Détection et prévention des menaces de sécurité par l'analyse proactive du comportement des agents.

 #12.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les comportements des agents proactifs sont validés sur le plan de la sécurité avant l'exécution, avec une intégration de l'évaluation des risques.
 #12.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que les déclencheurs d’initiative autonome incluent l’évaluation du contexte de sécurité et l’évaluation du paysage des menaces.
 #12.7.3    Niveau: 2    Rôle: D/V
 Vérifiez que les comportements proactifs sont analysés pour des implications de sécurité potentielles et des conséquences inattendues.
 #12.7.4    Niveau: 3    Rôle: D/V
 Vérifiez que les actions proactives critiques en matière de sécurité nécessitent des chaînes d'approbation explicites avec des journaux d'audit.
 #12.7.5    Niveau: 3    Rôle: D/V
 Vérifiez que la détection d’anomalies comportementales identifie les écarts dans les schémas des agents proactifs susceptibles d’indiquer une compromission.

---

### Références

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Supervision humaine, responsabilité et gouvernance

### Objectif de contrôle

Ce chapitre fournit les exigences relatives au maintien d'une supervision humaine et de chaînes de reddition de comptes claires dans les systèmes d'IA, garantissant l'explicabilité, la transparence et une gouvernance éthique tout au long du cycle de vie de l'IA.

---

### C13.1 Interrupteur d'arrêt d'urgence et mécanismes de contournement

Fournir des mécanismes d'arrêt ou de restauration lorsque des comportements dangereux du système d'IA sont observés.

 #13.1.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'un mécanisme d'arrêt manuel existe pour interrompre immédiatement l'inférence du modèle d'IA et ses sorties.
 #13.1.2    Niveau: 1    Rôle: D
 Vérifiez que les contrôles d'override ne soient accessibles qu'au personnel autorisé.
 #13.1.3    Niveau: 3    Rôle: D/V
 Vérifiez que les procédures de rollback permettent de revenir à des versions antérieures du modèle ou à des opérations en mode sans échec.
 #13.1.4    Niveau: 3    Rôle: V
 Vérifiez que les mécanismes de contournement sont testés régulièrement.

---

### C13.2 Points de contrôle de décision avec Human-in-the-Loop

Exiger des approbations humaines lorsque les enjeux dépassent des seuils de risque prédéfinis.

 #13.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les décisions d'IA à haut risque nécessitent une approbation explicite de la part d'un être humain avant leur exécution.
 #13.2.2    Niveau: 1    Rôle: D
 Vérifiez que les seuils de risque sont clairement définis et déclenchent automatiquement les flux de travail de révision humaine.
 #13.2.3    Niveau: 2    Rôle: D
 Vérifiez que les décisions sensibles au temps disposent de procédures de repli lorsque l'approbation humaine ne peut pas être obtenue dans les délais impartis.
 #13.2.4    Niveau: 3    Rôle: D/V
 Vérifiez que les procédures d'escalade définissent des niveaux d'autorité clairs pour différents types de décisions ou catégories de risques, le cas échéant.

---

### C13.3 Chaîne de responsabilité et auditabilité

Consigner les actions de l’opérateur et les décisions du modèle.

 #13.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que toutes les décisions du système d'IA et les interventions humaines sont consignées avec des horodatages, des identités des utilisateurs et la justification des décisions.
 #13.3.2    Niveau: 2    Rôle: D
 Vérifiez que les journaux d'audit ne puissent pas être altérés et incluez des mécanismes de vérification de l'intégrité.

---

### C13.4 Techniques d'IA explicables

Importance des caractéristiques de surface, contre-factuels et explications locales.

 #13.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que les systèmes d'IA fournissent des explications de base sur leurs décisions dans un format lisible par l'homme.
 #13.4.2    Niveau: 2    Rôle: V
 Vérifiez que la qualité des explications est validée par des études d'évaluation humaine et par des métriques.
 #13.4.3    Niveau: 3    Rôle: D/V
 Vérifiez que les scores d'importance des caractéristiques ou les méthodes d'attribution (SHAP, LIME, etc.) sont disponibles pour les décisions critiques.
 #13.4.4    Niveau: 3    Rôle: V
 Vérifiez que les explications contrefactuelles montrent comment les entrées pourraient être modifiées pour changer les résultats, si cela est applicable au cas d'utilisation et au domaine.

---

### C13.5 Cartes de modèle et divulgations d'utilisation

Maintenez les cartes de modèle pour l'utilisation prévue, les métriques de performance et les considérations éthiques.

 #13.5.1    Niveau: 1    Rôle: D
 Vérifiez que les fiches de modèle documentent les cas d'utilisation prévus, les limites et les modes de défaillance connus.
 #13.5.2    Niveau: 1    Rôle: D/V
 Vérifiez que les métriques de performance pour les différents cas d'utilisation applicables sont divulguées.
 #13.5.3    Niveau: 2    Rôle: D
 Vérifiez que les considérations éthiques, les évaluations des biais, les évaluations d'équité, les caractéristiques des données d'entraînement et les limites connues des données d'entraînement sont documentées et mises à jour régulièrement.
 #13.5.4    Niveau: 2    Rôle: D/V
 Vérifiez que les fiches de modèle sont sous contrôle de version et maintenues tout au long du cycle de vie du modèle, avec le suivi des modifications.

---

### C13.6 Quantification de l'incertitude

Propager les scores de confiance ou les mesures d'entropie dans les réponses.

 #13.6.1    Niveau: 1    Rôle: D
 Vérifiez que les systèmes d'IA fournissent des scores de confiance ou des mesures d'incertitude avec leurs sorties.
 #13.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que les seuils d'incertitude déclenchent une révision humaine supplémentaire ou des voies de décision alternatives.
 #13.6.3    Niveau: 2    Rôle: V
 Vérifiez que les méthodes de quantification de l'incertitude sont calibrées et validées par rapport aux données de vérité au sol.
 #13.6.4    Niveau: 3    Rôle: D/V
 Vérifier que la propagation de l'incertitude est maintenue tout au long des flux de travail d'IA en plusieurs étapes.

---

### C13.7 Rapports de transparence destinés à l'utilisateur

Fournir des divulgations périodiques concernant les incidents, la dérive et l’utilisation des données.

 #13.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les politiques d'utilisation des données et les pratiques de gestion du consentement des utilisateurs sont clairement communiquées aux parties prenantes.
 #13.7.2    Niveau: 2    Rôle: D/V
 Vérifiez que les évaluations d'impact de l'IA sont réalisées et que les résultats sont inclus dans le rapport.
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
GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Annexe A: Glossaire

This glossaire exhaustif fournit les définitions des principaux termes d'IA, d'apprentissage automatique et de sécurité utilisés dans tout l'AISVS pour assurer la clarté et une compréhension commune.

Exemple adversarial : Une entrée délibérément conçue pour amener un modèle d'IA à commettre une erreur, souvent en ajoutant des perturbations subtiles imperceptibles pour les humains.
​
Robustesse adversarielle – La robustesse adversarielle en IA fait référence à la capacité d'un modèle à maintenir ses performances et à résister à être trompé ou manipulé par des entrées intentionnellement conçues et malveillantes destinées à provoquer des erreurs.
​
Agent – Les agents d'IA sont des systèmes logiciels qui utilisent l'IA pour poursuivre des objectifs et accomplir des tâches au nom des utilisateurs. Ils font preuve de raisonnement, de planification et de mémoire, et disposent d'un niveau d'autonomie pour prendre des décisions, apprendre et s'adapter.
​
IA agentive : des systèmes d'IA capables d'opérer avec un certain degré d'autonomie pour atteindre des objectifs, prenant souvent des décisions et effectuant des actions sans intervention humaine directe.
​
Contrôle d'accès basé sur les attributs (ABAC) : Un paradigme de contrôle d'accès dans lequel les décisions d'autorisation sont basées sur les attributs de l'utilisateur, de la ressource, de l'action et de l'environnement, évalués au moment de la requête.
​
Attaque par porte dérobée : un type d'attaque par empoisonnement des données dans laquelle le modèle est entraîné à répondre d'une manière spécifique à certains déclencheurs tout en se comportant normalement dans les autres cas.
​
Biais : erreurs systématiques dans les sorties des modèles d'IA qui peuvent entraîner des résultats injustes ou discriminatoires pour certains groupes ou dans des contextes spécifiques.
​
Exploitation des biais : une technique d’attaque qui exploite les biais connus dans les modèles d’IA pour manipuler les sorties ou les résultats.
​
Cedar: le langage de politique et le moteur d'Amazon pour les autorisations granulaires utilisées dans la mise en œuvre de l'ABAC pour les systèmes d'IA.
​
Chaîne de raisonnement : une technique visant à améliorer le raisonnement des modèles de langage en générant des étapes de raisonnement intermédiaires avant de produire une réponse finale.
​
Disjoncteurs : des mécanismes qui arrêtent automatiquement les opérations des systèmes d'IA lorsque des seuils de risque spécifiques sont dépassés.
​
Fuite de données : exposition involontaire d'informations sensibles par les sorties ou le comportement du modèle d'IA.
​
Empoisonnement des données : la corruption délibérée des données d'entraînement visant à compromettre l'intégrité du modèle, souvent pour installer des portes dérobées ou dégrader les performances.
​
Confidentialité différentielle – La confidentialité différentielle est un cadre mathématiquement rigoureux pour publier des informations statistiques sur des ensembles de données tout en protégeant la vie privée des personnes concernées. Elle permet à un détenteur de données de partager des tendances agrégées du groupe tout en limitant les informations qui pourraient être divulguées au sujet de personnes spécifiques.
​
Embeddings: Représentations vectorielles denses de données (texte, images, etc.) qui capturent la signification sémantique dans un espace de haute dimension.
​
Explicabilité – L'explicabilité dans l'IA est la capacité d'un système d'IA à fournir des raisons compréhensibles par l'être humain pour ses décisions et ses prédictions, offrant des aperçus sur son fonctionnement interne.
​
IA explicable (XAI): des systèmes d'IA conçus pour fournir des explications compréhensibles par l'homme de leurs décisions et de leurs comportements à travers diverses techniques et cadres.
​
Apprentissage fédéré : une approche d'apprentissage automatique où les modèles sont entraînés sur plusieurs dispositifs décentralisés détenant des échantillons locaux de données, sans échanger les données elles-mêmes.
​
Garde-fous : Contraintes mises en œuvre pour empêcher les systèmes d'IA de produire des sorties nocives, biaisées ou autrement indésirables.
​
Hallucination – Une hallucination d'IA désigne un phénomène par lequel un modèle d'IA génère des informations incorrectes ou trompeuses qui ne sont pas basées sur ses données d'entraînement ou sur la réalité factuelle.
​
Human-in-the-Loop (HITL) : des systèmes conçus pour exiger une supervision humaine, une vérification ou une intervention aux points de décision cruciaux.
​
Infrastructure as Code (IaC) : gestion et provisionnement de l'infrastructure par le code, plutôt que par des processus manuels, permettant l’analyse de sécurité et des déploiements cohérents.
​
Jailbreak: Techniques utilisées pour contourner les garde-fous de sécurité dans les systèmes d’IA, en particulier dans les grands modèles de langage, afin de produire un contenu interdit.
​
Le principe du moindre privilège : le principe de sécurité consistant à n'accorder que les droits d'accès minimaux nécessaires aux utilisateurs et aux processus.
​
LIME (Local Interpretable Model-agnostic Explanations): Une technique pour expliquer les prédictions de tout classificateur d'apprentissage automatique en l'approximation locale avec un modèle interprétable.
​
Attaque d'inférence d'appartenance : une attaque visant à déterminer si un échantillon de données spécifique a été utilisé pour entraîner un modèle d'apprentissage automatique.
​
MITRE ATLAS: Paysage des menaces adverses pour les systèmes d'intelligence artificielle; une base de connaissances sur les tactiques et techniques adverses contre les systèmes d'IA.
​
Fiche du modèle – Une fiche du modèle est un document qui fournit des informations standardisées sur les performances d'un modèle d'IA, ses limites, ses usages prévus et les considérations éthiques afin de promouvoir la transparence et le développement responsable de l'IA.
​
Extraction de modèle : une attaque au cours de laquelle un adversaire interroge à répétition un modèle cible afin de créer une copie fonctionnellement similaire sans autorisation.
​
Inversion de modèle: une attaque qui tente de reconstruire les données d'entraînement en analysant les sorties du modèle.
​
Gestion du cycle de vie des modèles – La gestion du cycle de vie des modèles d’IA est le processus de supervision de toutes les étapes de l’existence d’un modèle d’IA, y compris sa conception, son développement, son déploiement, sa surveillance, sa maintenance et sa retraite éventuelle, afin de garantir qu’il demeure efficace et aligné sur les objectifs.
​
Empoisonnement du modèle : introduction de vulnérabilités ou de portes dérobées directement dans un modèle pendant le processus d'entraînement.
​
Vol de modèle : Extraction d'une copie ou d'une approximation d'un modèle propriétaire par des requêtes répétées.
​
Système multi-agent: Un système composé de multiples agents d'IA interagissants, chacun ayant des capacités et des objectifs potentiellement différents.
​
OPA (Open Policy Agent): un moteur de politiques open-source qui permet une application unifiée des politiques à travers la pile.
​
Apprentissage automatique préservant la vie privée (PPML) : Techniques et méthodes pour former et déployer des modèles ML tout en protégeant la vie privée des données d'entraînement.
​
Injection de prompt : une attaque dans laquelle des instructions malveillantes sont intégrées dans des entrées afin de contourner le comportement prévu du modèle.
​
RAG (Retrieval-Augmented Generation): Une technique qui améliore les grands modèles de langage en récupérant des informations pertinentes à partir de sources de connaissances externes avant de générer une réponse.
​
Red-Teaming: La pratique consistant à tester activement des systèmes d'IA en simulant des attaques adversariales afin d'identifier les vulnérabilités.
​
SBOM (Liste des composants logiciels) : Un enregistrement formel contenant les détails et les relations de chaîne d'approvisionnement de divers composants utilisés dans la construction de logiciels ou de modèles d'IA.
​
SHAP (SHapley Additive exPlanations) : une approche basée sur la théorie des jeux pour expliquer la sortie de tout modèle d'apprentissage automatique en calculant la contribution de chaque caractéristique à la prédiction.
​
Attaque de la chaîne d'approvisionnement : compromettre un système en ciblant des éléments moins sécurisés de sa chaîne d'approvisionnement, tels que des bibliothèques tierces, des ensembles de données ou des modèles pré-entraînés.
​
Apprentissage par transfert : une technique où un modèle développé pour une tâche est réutilisé comme point de départ pour un modèle sur une seconde tâche.
​
Base de données vectorielle : une base de données spécialisée conçue pour stocker des vecteurs de haute dimension (embeddings) et effectuer des recherches de similarité efficaces.
​
Analyse de vulnérabilités : outils automatisés qui identifient des vulnérabilités de sécurité connues dans les composants logiciels, y compris les frameworks d’IA et les dépendances.
​
Filigrage numérique : techniques pour insérer des marqueurs imperceptibles dans le contenu généré par l’IA afin de retracer son origine ou de détecter une génération par IA.
​
Vulnérabilité zero-day : une vulnérabilité auparavant inconnue que les attaquants peuvent exploiter avant que les développeurs ne créent et déploient un correctif.

## Annexe B : Références

### TODO

## Annexe C : Gouvernance et documentation de la sécurité de l'IA

### Objectif

Cette annexe présente les exigences fondamentales pour établir des structures organisationnelles, des politiques et des processus afin de régir la sécurité de l'IA tout au long du cycle de vie du système.

---

### AC.1 Adoption du cadre de gestion des risques de l'IA

Fournir un cadre formel pour identifier, évaluer et atténuer les risques spécifiques à l’IA tout au long du cycle de vie du système.

 #AC.1.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'une méthodologie d'évaluation des risques spécifique à l'IA est documentée et mise en œuvre.
 #AC.1.2    Niveau: 2    Rôle: D
 Vérifiez que des évaluations des risques sont effectuées à des points clés du cycle de vie de l'IA et avant des changements importants.
 #AC.1.3    Niveau: 3    Rôle: D/V
 Vérifiez que le cadre de gestion des risques est aligné sur les normes établies (par exemple le NIST AI RMF).

---

### AC.2 Politique et procédures de sécurité de l'IA

Établir et faire respecter les normes organisationnelles relatives au développement, au déploiement et à l'exploitation sécurisés de l'IA.

 #AC.2.1    Niveau: 1    Rôle: D/V
 Vérifiez que les politiques de sécurité de l’IA documentées existent.
 #AC.2.2    Niveau: 2    Rôle: D
 Vérifiez que les politiques sont révisées et mises à jour au moins une fois par an et après des changements significatifs du paysage des menaces.
 #AC.2.3    Niveau: 3    Rôle: D/V
 Vérifiez que les politiques couvrent toutes les catégories AISVS et les exigences réglementaires applicables.

---

### AC.3 Rôles et responsabilités en matière de sécurité de l'IA

Établir une responsabilité claire en matière de sécurité de l'IA au sein de l'organisation.

 #AC.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les rôles et les responsabilités en matière de sécurité de l'IA sont documentés.
 #AC.3.2    Niveau: 2    Rôle: D
 Vérifiez que les personnes responsables possèdent l'expertise en sécurité appropriée.
 #AC.3.3    Niveau: 3    Rôle: D/V
 Vérifiez qu'un comité d'éthique de l'IA ou un conseil de gouvernance est établi pour les systèmes d'IA à haut‑risque.

---

### AC.4 Mise en œuvre des directives éthiques de l'IA

Assurez-vous que les systèmes d'IA fonctionnent selon des principes éthiques établis.

 #AC.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que des directives éthiques pour le développement et le déploiement de l’IA existent.
 #AC.4.2    Niveau: 2    Rôle: D
 Vérifiez que des mécanismes sont en place pour détecter et signaler les violations éthiques.
 #AC.4.3    Niveau: 3    Rôle: D/V
 Vérifiez que des évaluations éthiques régulières des systèmes d’IA déployés soient effectuées.

---

### AC.5 Surveillance de la conformité réglementaire de l'IA

Maintenir une veille sur les réglementations relatives à l’IA en constante évolution et assurer leur conformité.

 #AC.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que des processus existent pour identifier les réglementations applicables à l'IA.
 #AC.5.2    Niveau: 2    Rôle: D
 Vérifiez que la conformité à toutes les exigences réglementaires est évaluée.
 #AC.5.3    Niveau: 3    Rôle: D/V
 Vérifiez que les modifications réglementaires déclenchent des revues et des mises à jour en temps utile des systèmes d'IA.

### AC.6 Gouvernance des données d’entraînement, documentation et processus

 #1.1.2    Niveau: 1    Rôle: D/V
 Vérifiez que seuls les ensembles de données vérifiés quant à leur qualité, leur représentativité, leur provenance éthique et leur conformité à la licence soient autorisés, ce qui réduit les risques d'empoisonnement des données, de biais intégré et de violation des droits de propriété intellectuelle.
 #1.1.5    Niveau: 2    Rôle: D/V
 Vérifiez que la qualité de l'étiquetage/annotation est assurée par des vérifications croisées réalisées par des réviseurs ou par consensus.
 #1.1.6    Niveau: 2    Rôle: D/V
 Vérifiez que les fiches techniques des jeux de données (ou datasheets pour jeux de données) sont tenues à jour pour les ensembles d'entraînement importants, en détaillant leurs caractéristiques, leurs motivations, leur composition, les processus de collecte, le prétraitement et les usages recommandés/déconseillés.
 #1.3.2    Niveau: 2    Rôle: D/V
 Vérifier que les biais identifiés sont atténués grâce à des stratégies documentées telles que le rééquilibrage, l’augmentation ciblée des données, des ajustements algorithmiques (par exemple, des techniques de pré-traitement, de traitement pendant l’apprentissage et de post-traitement), ou la pondération, et que l’impact de l’atténuation sur l’équité ainsi que sur les performances globales du modèle est évalué.
 #1.3.3    Niveau: 2    Rôle: D/V
 Vérifiez que les métriques d'équité post-entraînement sont évaluées et documentées.
 #1.3.4    Niveau: 3    Rôle: D/V
 Vérifiez qu'une politique de gestion du cycle de vie des biais désigne des propriétaires et une cadence de révision.
 #1.4.1    Niveau: 2    Rôle: D/V
 Assurez-vous que la qualité de l’étiquetage/annotation est assurée grâce à des directives claires, des vérifications croisées par les réviseurs, des mécanismes de consensus (par exemple, le suivi de l’accord inter-annotateurs) et à des processus définis pour résoudre les écarts.
 #1.4.4    Niveau: 3    Rôle: D/V
 Vérifiez que les étiquettes critiques pour la sécurité, la sûreté ou l'équité (par exemple l'identification de contenu toxique, des constats médicaux critiques) font l'objet d'une revue indépendante double obligatoire ou d'une vérification robuste équivalente.
 #1.4.6    Niveau: 2    Rôle: D/V
 Vérifiez que les guides et les instructions d'étiquetage sont complets, sous contrôle de version et évalués par des pairs.
 #1.4.6    Niveau: 2    Rôle: D/V
 Vérifiez que les schémas de données des étiquettes sont clairement définis et versionnés.
 #1.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les ensembles de données font l'objet d'un profilage pour repérer les déséquilibres de représentation et les biais potentiels sur les attributs légalement protégés (par exemple, race, sexe, âge) et d'autres caractéristiques éthiquement sensibles pertinentes au domaine d'application du modèle (par exemple, statut socio-économique, localisation).
 #1.5.3    Niveau: 2    Rôle: V
 Vérifiez que les contrôles ponctuels manuels effectués par des experts du domaine couvrent un échantillon statistiquement significatif (par exemple ≥1% ou 1,000 échantillons, selon ce qui est le plus élevé, ou tel que déterminé par l’évaluation des risques) afin d’identifier des problèmes de qualité subtils non détectés par l’automatisation.
 #1.8.4    Niveau: 2    Rôle: D/V
 Vérifier que les flux de travail d'étiquetage externalisés ou crowdsourcés incluent des mesures techniques et procédurales de sauvegarde pour garantir la confidentialité et l'intégrité des données, la qualité des étiquettes et prévenir les fuites de données.
 #1.5.4    Niveau: 2    Rôle: D/V
 Vérifiez que les étapes de remédiation sont ajoutées aux enregistrements de provenance.
 #1.6.2    Niveau: 2    Rôle: D/V
 Vérifiez que les échantillons signalés déclenchent une révision manuelle avant l'entraînement.
 #1.6.3    Niveau: 2    Rôle: V
 Vérifiez que les résultats alimentent le dossier de sécurité du modèle et le renseignement sur les menaces en cours.
 #1.6.4    Niveau: 3    Rôle: D/V
 Vérifiez que la logique de détection est actualisée avec de nouveaux renseignements sur les menaces.
 #1.6.5    Niveau: 3    Rôle: D/V
 Vérifiez que les pipelines d'apprentissage en ligne surveillent la dérive de la distribution.
 #1.7.1    Niveau: 1    Rôle: D/V
 Vérifiez que les flux de travail de suppression des données d'entraînement purgent les données primaires et dérivées et évaluent l'impact sur le modèle, et que l'impact sur les modèles concernés est évalué et, si nécessaire, pris en charge (par exemple, par un réentraînement ou une récalibration).
 #1.7.2    Niveau: 2    Rôle: D
 Vérifiez que des mécanismes sont en place pour suivre et respecter l'étendue et le statut du consentement des utilisateurs (ainsi que les retraits) pour les données utilisées lors de l'entraînement, et que le consentement est validé avant que les données ne soient intégrées dans de nouveaux processus d'entraînement ou des mises à jour importantes du modèle.
 #1.7.3    Niveau: 2    Rôle: V
 Vérifiez que les flux de travail sont testés annuellement et consignés.
 #1.8.1    Niveau: 2    Rôle: D/V
 Vérifiez que les fournisseurs de données tiers, y compris les fournisseurs de modèles pré-entraînés et d’ensembles de données externes, subissent une diligence raisonnable en matière de sécurité, de confidentialité, d'approvisionnement éthique et de qualité des données avant que leurs données ou leurs modèles ne soient intégrés.
 #1.8.2    Niveau: 1    Rôle: D
 Vérifiez que les transferts externes utilisent TLS/auth et des contrôles d’intégrité.
 #1.8.3    Niveau: 2    Rôle: D/V
 Vérifiez que les sources de données à haut risque (par exemple, des ensembles de données open source dont la provenance est inconnue, des fournisseurs non vérifiés) font l'objet d'un contrôle renforcé, tel qu'une analyse sandboxée, des vérifications approfondies de la qualité et des biais, et une détection ciblée d'empoisonnement, avant leur utilisation dans des applications sensibles.
 #1.8.4    Niveau: 3    Rôle: D/V
 Vérifiez que Vérifiez que les modèles pré-entraînés obtenus auprès de tiers sont évalués pour des biais intégrés, des portes dérobées potentielles, l'intégrité de leur architecture et la provenance de leurs données d'entraînement d'origine avant le réglage fin ou le déploiement.
 #1.5.3    Niveau: 2    Rôle: D/V
 Vérifiez que, si un entraînement adversarial est utilisé, la génération, la gestion et le versionnage des ensembles de données adversariaux sont documentés et contrôlés.
 #1.5.3    Niveau: 3    Rôle: D/V
 Vérifiez que l'impact de l'entraînement à la robustesse adversarielle sur les performances du modèle (à la fois sur des entrées propres et adversariales) et sur les métriques d'équité est évalué, documenté et surveillé.
 #1.5.4    Niveau: 3    Rôle: D/V
 Vérifier que les stratégies d'entraînement adversarial et de robustesse sont périodiquement revues et mises à jour afin de contrer l'évolution des techniques d'attaque adverses.
 #1.4.2    Niveau: 2    Rôle: D/V
 Vérifiez que les ensembles de données échoués sont mis en quarantaine avec des traces d'audit.
 #1.4.3    Niveau: 2    Rôle: D/V
 Vérifiez que les contrôles de qualité bloquent les ensembles de données de qualité inférieure, à moins que des exceptions soient approuvées.
 #1.11.2    Niveau: 2    Rôle: D/V
 Vérifiez que le processus de génération, les paramètres et l’utilisation prévue des données synthétiques sont documentés.
 #1.11.3    Niveau: 2    Rôle: D/V
 Vérifiez que les données synthétiques font l'objet d'une évaluation des risques concernant les biais, les fuites de confidentialité et les problèmes de représentation, avant leur utilisation dans l'entraînement.
 #1.12.3    Niveau: 2    Rôle: D/V
 Vérifiez que des alertes sont générées pour les événements d'accès suspects et qu'elles font l'objet d'une enquête rapide.
 #1.13.1    Niveau: 1    Rôle: D/V
 Vérifiez que des périodes de rétention explicites sont définies pour tous les jeux de données d'entraînement.
 #1.13.2    Niveau: 2    Rôle: D/V
 Vérifiez que les jeux de données expirent automatiquement, sont supprimés ou font l'objet d'un examen en vue de leur suppression à la fin de leur cycle de vie.
 #1.13.3    Niveau: 2    Rôle: D/V
 Assurez-vous que les actions de rétention et de suppression sont consignées et auditées.
 #1.14.1    Niveau: 2    Rôle: D/V
 Vérifiez que les exigences de localisation des données et de transferts transfrontaliers sont identifiées et appliquées pour tous les ensembles de données.
 #1.14.2    Niveau: 2    Rôle: D/V
 Vérifiez que les réglementations propres à chaque secteur (par exemple, le secteur de la santé et le secteur financier) sont identifiées et prises en compte dans le traitement des données.
 #1.14.3    Niveau: 2    Rôle: D/V
 Vérifier que la conformité aux lois pertinentes en matière de protection de la vie privée (par exemple RGPD, CCPA) est documentée et révisée régulièrement.
 #1.16.1    Niveau: 2    Rôle: D/V
 Vérifiez que des mécanismes existent pour répondre aux demandes des personnes concernées relatives à l'accès, à la rectification, à la restriction ou à l'opposition.
 #1.16.2    Niveau: 2    Rôle: D/V
 Vérifiez que les demandes sont enregistrées, suivies et traitées dans les délais imposés par la loi.
 #1.16.3    Niveau: 2    Rôle: D/V
 Vérifiez que les processus relatifs aux droits des personnes concernées sont régulièrement testés et examinés afin d'en évaluer l'efficacité.
 #1.17.1    Niveau: 2    Rôle: D/V
 Vérifiez qu'une analyse d'impact est réalisée avant la mise à jour ou le remplacement d'une version du jeu de données, couvrant les performances du modèle, l'équité et la conformité.
 #1.17.2    Niveau: 2    Rôle: D/V
 Vérifiez que les résultats de l’analyse d’impact sont documentés et examinés par les parties prenantes pertinentes.
 #1.17.3    Niveau: 2    Rôle: D/V
 Vérifiez que des plans de rollback existent au cas où les nouvelles versions introduiraient des risques inacceptables ou des régressions.
 #1.18.1    Niveau: 2    Rôle: D/V
 Vérifiez que tout le personnel impliqué dans l’annotation des données a subi une vérification des antécédents et est formé à la sécurité des données et à la protection de la vie privée.
 #1.18.2    Niveau: 2    Rôle: D/V
 Vérifiez que tout le personnel d'annotation signe des accords de confidentialité et de non-divulgation.
 #1.18.3    Niveau: 2    Rôle: D/V
 Vérifiez que les plateformes d’annotation appliquent des contrôles d’accès et surveillent les menaces internes.

#### Références

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Annexe D: Gouvernance et vérification du codage sécurisé assisté par l'IA

### Objectif

Ce chapitre définit les contrôles organisationnels de référence pour l'utilisation sûre et efficace des outils de codage assistés par l'IA pendant le développement logiciel, assurant la sécurité et la traçabilité tout au long du SDLC.

---

### AD.1 Flux de travail de codage‑sécurisé assisté par l'IA

Intégrer les outils d’IA dans le cycle de vie sécurisé du développement logiciel de l’organisation (SSDLC) sans affaiblir les garde-fous de sécurité existants.

 #AD.1.1    Niveau: 1    Rôle: D/V
 Assurez-vous qu'un flux de travail documenté décrit quand et comment les outils d'IA peuvent générer, refactoriser ou examiner le code.
 #AD.1.2    Niveau: 2    Rôle: D
 Vérifiez que le flux de travail correspond à chaque phase du SSDLC (conception, mise en œuvre, revue de code, tests, déploiement).
 #AD.1.3    Niveau: 3    Rôle: D/V
 Vérifiez que les métriques (par exemple, densité de vulnérabilités, temps moyen de détection) sont collectées sur le code généré par l’IA et comparées à des références uniquement humaines.

---

### AD.2 Qualification des outils d'IA et modélisation des menaces

Assurez-vous que les outils de codage basés sur l’IA soient évalués en termes de capacités de sécurité, de risques et d’impact sur la chaîne d’approvisionnement avant leur adoption.

 #AD.2.1    Niveau: 1    Rôle: D/V
 Vérifiez qu'un modèle de menace pour chaque outil d'IA identifie l'utilisation abusive, l'inversion de modèle, les fuites de données et les risques liés à la chaîne de dépendances.
 #AD.2.2    Niveau: 2    Rôle: D
 Vérifiez que les évaluations des outils incluent l’analyse statique/dynamique de tous les composants locaux et l’évaluation des points de terminaison SaaS (TLS, authentification/autorisation, journalisation).
 #AD.2.3    Niveau: 3    Rôle: D/V
 Vérifiez que les évaluations suivent un cadre reconnu et qu'elles sont ré‑effectuées après des changements de version majeurs.

---

### AD.3 Gestion sécurisée du prompt et du contexte

Prévenir la fuite de secrets, de code propriétaire et de données personnelles lors de l'élaboration de prompts ou de contextes pour des modèles d’IA.

 #AD.3.1    Niveau: 1    Rôle: D/V
 Vérifiez que les directives écrites interdisent l'envoi de secrets, d'identifiants ou de données classifiées dans les invites.
 #AD.3.2    Niveau: 2    Rôle: D
 Vérifiez que les contrôles techniques (rédaction côté client, filtres de contexte approuvés) suppriment automatiquement les artefacts sensibles.
 #AD.3.3    Niveau: 3    Rôle: D/V
 Vérifiez que les invites et les réponses sont tokenisées, chiffrées en transit et au repos, et que les périodes de conservation respectent la politique de data‑classification.

---

### AD.4 Validation du code généré par l'IA

Détecter et remédier aux vulnérabilités introduites par la sortie générée par l'IA avant que le code ne soit fusionné ou déployé.

 #AD.4.1    Niveau: 1    Rôle: D/V
 Vérifiez que le code généré par l’IA est toujours soumis à une revue de code par des humains.
 #AD.4.2    Niveau: 2    Rôle: D
 Vérifiez que les analyseurs automatisés (SAST/IAST/DAST) s'exécutent sur chaque pull request contenant du code généré par l'IA et bloquent les fusions en cas de constats critiques.
 #AD.4.3    Niveau: 3    Rôle: D/V
 Vérifiez que le fuzzing différentiel ou les tests basés sur les propriétés prouvent les comportements critiques en matière de sécurité (par exemple, validation des entrées, logique d'autorisation).

---

### AD.5 Explicabilité et traçabilité des suggestions de code

Fournir aux auditeurs et aux développeurs un aperçu des raisons pour lesquelles une suggestion a été faite et de son évolution.

 #AD.5.1    Niveau: 1    Rôle: D/V
 Vérifiez que les paires prompt/réponse sont enregistrées avec des identifiants de commit.
 #AD.5.2    Niveau: 2    Rôle: D
 Vérifiez que les développeurs peuvent faire apparaître des citations du modèle (extraits d'entraînement, documentation) qui étayent une suggestion.
 #AD.5.3    Niveau: 3    Rôle: D/V
 Vérifiez que les rapports d’explicabilité sont stockés avec les artefacts de conception et référencés dans les revues de sécurité, conformément aux principes de traçabilité ISO/IEC 42001.

---

### AD.6 Rétroaction continue & réglage fin du modèle

Améliorer les performances de sécurité du modèle au fil du temps tout en évitant la dérive négative.

 #AD.6.1    Niveau: 1    Rôle: D/V
 Vérifiez que les développeurs peuvent signaler des suggestions peu sûres ou non‑conformes, et que les drapeaux sont suivis.
 #AD.6.2    Niveau: 2    Rôle: D
 Vérifiez que les retours agrégés informent un affinage‑périodique ou une génération‑augmentée par récupération avec des corpus de codage sécurisé vérifiés (par exemple, OWASP Cheat Sheets).
 #AD.6.3    Niveau: 3    Rôle: D/V
 Vérifier qu'un cadre d’évaluation en boucle fermée exécute des tests de régression après chaque réglage‑fin ; les métriques de sécurité doivent atteindre ou dépasser les références antérieures avant le déploiement.

---

#### Références

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Annexe E : Exemples d'outils et de cadres

### Objectif

Ce chapitre présente des exemples d’outils et de cadres qui peuvent soutenir la mise en œuvre ou l’accomplissement d’une exigence AISVS donnée. Ces éléments ne doivent pas être considérés comme des recommandations ou des soutiens de la part de l’équipe AISVS ou du Projet OWASP GenAI Security.

---

### AE.1 Gouvernance des données d'entraînement et gestion des biais

Outils utilisés pour l'analyse de données, la gouvernance et la gestion des biais.

 #AE.1.1    Section: 1.1
 Outils d'inventaire des données : des outils de gestion d'inventaire des données tels que...
 #AE.1.2    Section: 1.2
 Chiffrement-en-transit Utilisez TLS pour les applications basées sur HTTPS, avec des outils tels que OpenSSL et Python`ssl` bibliothèque.

---

### AE.2 Validation des saisies utilisateur

Outillage pour gérer et valider les entrées utilisateur.

 #AE.2.1    Section: 2.1
 Outils de défense contre l'injection d'invite : utilisez des outils de garde-fous tels que NeMo de NVIDIA ou Guardrails AI.

---

