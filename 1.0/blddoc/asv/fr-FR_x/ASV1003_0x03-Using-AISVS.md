# En utilisant l'AISVS

La norme de vérification de la sécurité de l'intelligence artificielle (AISVS) définit les exigences de sécurité pour les applications et services d'IA modernes, en mettant l'accent sur les aspects qui relèvent du contrôle des développeurs d'applications.

L'AISVS est destiné à toute personne développant ou évaluant la sécurité des applications d'IA, notamment les développeurs, les architectes, les ingénieurs de sécurité et les auditeurs. Ce chapitre présente la structure et l'utilisation de l'AISVS, y compris ses niveaux de vérification et les cas d'utilisation prévus.

## Niveaux de vérification de la sécurité de l'IA

L'AISVS définit trois niveaux croissants de vérification de la sécurité. Chaque niveau ajoute de la profondeur et de la complexité, permettant aux organisations d'adapter leur posture de sécurité au niveau de risque de leurs systèmes d’IA.

Les organisations peuvent commencer au niveau 1 et adopter progressivement des niveaux supérieurs à mesure que la maturité en matière de sécurité et l'exposition aux menaces augmentent.

### Définition des niveaux

Chaque exigence dans AISVS v1.0 est assignée à l'un des niveaux suivants:

#### Exigences de niveau 1

Le niveau 1 comprend les exigences de sécurité les plus critiques et fondamentales. Celles-ci se concentrent sur la prévention des attaques courantes qui ne dépendent pas d'autres préconditions ou vulnérabilités. La plupart des contrôles du niveau 1 sont soit simples à mettre en œuvre, soit suffisamment essentiels pour justifier l'effort.

#### Exigences du niveau 2

Le niveau 2 aborde des attaques plus avancées ou moins courantes, ainsi que des défenses en couches contre les menaces généralisées. Ces exigences peuvent impliquer une logique plus complexe ou viser des prérequis d'attaque spécifiques.

#### Exigences du niveau 3

Le niveau 3 comprend des contrôles qui sont généralement plus difficiles à mettre en œuvre ou dont l'applicabilité est situationnelle. Ils représentent souvent des mécanismes de défense-en-profondeur ou des mesures d'atténuation contre des attaques de niche, ciblées ou à haute complexité.

### Rôle (D/V)

Chaque exigence AISVS est marquée selon le public cible principal :

* D – exigences axées sur les développeurs
* V – Exigences axées sur le vérificateur/auditeur
* D/V – Pertinent à la fois pour les développeurs et les vérificateurs

