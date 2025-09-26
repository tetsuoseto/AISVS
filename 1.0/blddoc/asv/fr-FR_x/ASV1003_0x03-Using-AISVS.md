# Utilisation de l'AISVS

La norme de vérification de la sécurité de l'intelligence artificielle (AISVS) définit les exigences de sécurité pour les applications et services d'IA modernes, en se concentrant sur les aspects sous le contrôle des développeurs d'applications.

L'AISVS est destiné à toute personne développant ou évaluant la sécurité des applications d'IA, y compris les développeurs, architectes, ingénieurs en sécurité et auditeurs. Ce chapitre présente la structure et l'utilisation de l'AISVS, y compris ses niveaux de vérification et ses cas d'utilisation prévus.

## Niveaux de vérification de la sécurité de l'intelligence artificielle

L'AISVS définit trois niveaux ascendantes de vérification de la sécurité. Chaque niveau ajoute de la profondeur et de la complexité, permettant aux organisations d'adapter leur posture de sécurité au niveau de risque de leurs systèmes d'IA.

Les organisations peuvent commencer au Niveau 1 et adopter progressivement des niveaux supérieurs à mesure que la maturité en matière de sécurité et l'exposition aux menaces augmentent.

### Définition des niveaux

Chaque exigence dans AISVS v1.0 est attribuée à l'un des niveaux suivants :

#### Exigences de niveau 1

Le niveau 1 comprend les exigences de sécurité les plus critiques et fondamentales. Celles-ci se concentrent sur la prévention des attaques courantes qui ne reposent pas sur d'autres conditions préalables ou vulnérabilités. La plupart des contrôles de niveau 1 sont soit simples à mettre en œuvre, soit suffisamment essentiels pour justifier l'effort.

#### Exigences de niveau 2

Le niveau 2 traite des attaques plus avancées ou moins fréquentes, ainsi que des défenses à plusieurs niveaux contre des menaces répandues. Ces exigences peuvent impliquer une logique plus complexe ou cibler des conditions préalables spécifiques aux attaques.

#### Exigences de niveau 3

Le niveau 3 inclut des contrôles qui sont généralement plus difficiles à mettre en œuvre ou dont l'applicabilité est situationnelle. Ceux-ci représentent souvent des mécanismes de défense en profondeur ou des mesures d'atténuation contre des attaques de niche, ciblées ou de haute complexité.

### Rôle (D/V)

Chaque exigence AISVS est marquée en fonction du public principal :

* D – Exigences axées sur les développeurs
* V – Exigences axées sur le vérificateur/auditeur
* D/V – Pertinent à la fois pour les développeurs et les vérificateurs

