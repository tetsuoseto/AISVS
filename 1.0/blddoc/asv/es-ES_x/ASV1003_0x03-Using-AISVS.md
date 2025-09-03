# Usando AISVS

El Estándar de Verificación de Seguridad de la Inteligencia Artificial (AISVS) define los requisitos de seguridad para las aplicaciones y servicios modernos de IA, enfocándose en aspectos que están bajo el control de los desarrolladores de aplicaciones.

El AISVS está destinado a cualquiera que desarrolle o evalúe la seguridad de las aplicaciones de IA, incluyendo desarrolladores, arquitectos, ingenieros de seguridad y auditores. Este capítulo introduce la estructura y el uso del AISVS, incluyendo sus niveles de verificación y los casos de uso previstos.

## Niveles de Verificación de Seguridad de la Inteligencia Artificial

El AISVS define tres niveles progresivos de verificación de seguridad. Cada nivel añade profundidad y complejidad, permitiendo a las organizaciones adaptar su postura de seguridad al nivel de riesgo de sus sistemas de IA.

Las organizaciones pueden comenzar en el Nivel 1 y adoptar progresivamente niveles más altos a medida que aumenta la madurez de la seguridad y la exposición a amenazas.

### Definición de los niveles

Cada requisito en AISVS v1.0 se asigna a uno de los siguientes niveles:

#### Requisitos de Nivel 1

El Nivel 1 incluye los requisitos de seguridad más críticos y fundamentales. Estos controles se enfocan en prevenir ataques comunes que no dependen de otras condiciones previas o vulnerabilidades. La mayoría de los controles de Nivel 1 son fáciles de implementar o lo suficientemente esenciales como para justificar el esfuerzo.

#### Requisitos de Nivel 2

Nivel 2 aborda ataques más avanzados o menos comunes, así como defensas en capas contra amenazas generalizadas. Estos requisitos pueden implicar una lógica más compleja o apuntar a prerrequisitos de ataque específicos.

#### Requisitos de Nivel 3

El Nivel 3 incluye controles que, por lo general, son más difíciles de implementar o cuya aplicabilidad es situacional. Estos suelen representar mecanismos de defensa en profundidad o mitigaciones frente a ataques de nicho, dirigidos o de alta complejidad.

### Rol (D/V)

Cada requisito AISVS está marcado de acuerdo con el público principal:

* D – Requisitos centrados en el desarrollador
* V – Requisitos centrados en verificadores/auditores
* D/V – Relevante tanto para desarrolladores como para verificadores

