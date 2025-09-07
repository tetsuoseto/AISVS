# Usando el AISVS

El Estándar de Verificación de Seguridad de la Inteligencia Artificial (AISVS) define los requisitos de seguridad para aplicaciones y servicios de IA modernos, enfocándose en aspectos bajo el control de los desarrolladores de aplicaciones.

El AISVS está destinado a cualquier persona que desarrolle o evalúe la seguridad de aplicaciones de IA, incluidos desarrolladores, arquitectos, ingenieros de seguridad y auditores. Este capítulo presenta la estructura y el uso del AISVS, incluidos sus niveles de verificación y casos de uso previstos.

## Niveles de Verificación de Seguridad en Inteligencia Artificial

El AISVS define tres niveles ascendentes de verificación de seguridad. Cada nivel añade profundidad y complejidad, lo que permite a las organizaciones adaptar su postura de seguridad al nivel de riesgo de sus sistemas de IA.

Las organizaciones pueden comenzar en el Nivel 1 y adoptar progresivamente niveles más altos a medida que aumentan la madurez de la seguridad y la exposición a amenazas.

### Definición de los Niveles

Cada requisito en AISVS v1.0 se asigna a uno de los siguientes niveles:

#### Requisitos de Nivel 1

El Nivel 1 incluye los requisitos de seguridad más críticos y fundamentales. Estos se centran en prevenir ataques comunes que no dependen de otras condiciones previas o vulnerabilidades. La mayoría de los controles del Nivel 1 son fáciles de implementar o lo suficientemente esenciales como para justificar el esfuerzo.

#### Requisitos de Nivel 2

El Nivel 2 aborda ataques más avanzados o menos comunes, así como defensas en capas contra amenazas generalizadas. Estos requisitos pueden implicar una lógica más compleja o dirigirse a prerrequisitos específicos de ataques.

#### Requisitos de nivel 3

El Nivel 3 incluye controles que normalmente son más difíciles de implementar o que se aplican en situaciones específicas. Estos a menudo representan mecanismos de defensa en profundidad o mitigaciones contra ataques especializados, dirigidos o de alta complejidad.

### Rol (D/V)

Cada requisito de AISVS está marcado según el público principal:

* D – Requisitos enfocados en el desarrollador
* V – Requisitos centrados en el verificador/auditor
* D/V – Relevante tanto para desarrolladores como para verificadores

