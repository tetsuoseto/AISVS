# C12 Monitoreo, Registro y Detección de Anomalías

## Objetivo de Control

Esta sección proporciona los requisitos para ofrecer visibilidad en tiempo real y forense de lo que el modelo y otros componentes de IA ven, hacen y devuelven, de modo que las amenazas puedan ser detectadas, clasificadas y aprendidas.

## C12.1 Registro de Solicitudes y Respuestas

|   #    | Descripción                                                                                                                                                                                                                                                      | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.1.1 | Verificar que todas las indicaciones del usuario y las respuestas del modelo se registren con los metadatos apropiados (por ejemplo, marca de tiempo, ID de usuario, ID de sesión, versión del modelo).                                                          |   1   | D/V |
| 12.1.2 | Verifique que los registros se almacenen en repositorios seguros y controlados por acceso, con políticas de retención adecuadas y procedimientos de respaldo.                                                                                                    |   1   | D/V |
| 12.1.3 | Verifique que los sistemas de almacenamiento de registros implementen cifrado en reposo y en tránsito para proteger la información sensible contenida en los registros.                                                                                          |   1   | D/V |
| 12.1.4 | Verifique que los datos sensibles en las indicaciones y salidas se redacten o enmascaren automáticamente antes de registrarlos, con reglas de redacción configurables para información de identificación personal (PII), credenciales e información propietaria. |   1   | D/V |
| 12.1.5 | Verifique que las decisiones de política y las acciones de filtrado de seguridad se registren con suficiente detalle para permitir la auditoría y depuración de los sistemas de moderación de contenido.                                                         |   2   | D/V |
| 12.1.6 | Verifique que la integridad del registro esté protegida mediante, por ejemplo, firmas criptográficas o almacenamiento de solo escritura.                                                                                                                         |   2   | D/V |

---

## C12.2 Detección y Alerta de Abusos

|   #    | Descripción                                                                                                                                                                                                                  | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.2.1 | Verifique que el sistema detecte y alerte sobre patrones conocidos de jailbreak, intentos de inyección de prompts e inputs adversariales utilizando detección basada en firmas.                                              |   1   | D/V |
| 12.2.2 | Verifique que el sistema se integre con las plataformas existentes de Gestión de Información y Eventos de Seguridad (SIEM) utilizando formatos y protocolos estándar de registro.                                            |   1   | D/V |
| 12.2.3 | Verifique que los eventos de seguridad enriquecidos incluyan contexto específico de IA, como identificadores de modelos, puntuaciones de confianza y decisiones de filtros de seguridad.                                     |   2   | D/V |
| 12.2.4 | Verifique que la detección de anomalías conductuales identifique patrones inusuales de conversación, intentos excesivos de reintento o comportamientos de sondeo sistemáticos.                                               |   2   | D/V |
| 12.2.5 | Verifique que los mecanismos de alerta en tiempo real notifiquen a los equipos de seguridad cuando se detecten posibles violaciones de políticas o intentos de ataque.                                                       |   2   | D/V |
| 12.2.6 | Verifique que se incluyan reglas personalizadas para detectar patrones de amenazas específicos de IA, incluidos intentos coordinados de jailbreak, campañas de inyección de indicaciones y ataques de extracción de modelos. |   2   | D/V |
| 12.2.7 | Verifique que los flujos de trabajo automatizados de respuesta a incidentes puedan aislar modelos comprometidos, bloquear usuarios maliciosos y escalar eventos críticos de seguridad.                                       |   3   | D/V |

---

## C12.3 Detección de deriva del modelo

|   #    | Descripción                                                                                                                                                                                            | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 12.3.1 | Verifique que el sistema rastree métricas básicas de rendimiento como precisión, puntuaciones de confianza, latencia y tasas de error a lo largo de las versiones del modelo y los períodos de tiempo. |   1   | D/V |
| 12.3.2 | Verifique que las alertas automatizadas se activen cuando las métricas de rendimiento superen los umbrales de degradación predefinidos o se desvíen significativamente de las líneas base.             |   2   | D/V |
| 12.3.3 | Verifique que los monitores de detección de alucinaciones identifiquen y marquen los casos en que las salidas del modelo contengan información factualmente incorrecta, inconsistente o fabricada.     |   2   | D/V |

---

## C12.4 Telemetría de Rendimiento y Comportamiento

|   #    | Descripción                                                                                                                                                                                                  | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 12.4.1 | Verifique que las métricas operativas, incluyendo la latencia de solicitudes, el consumo de tokens, el uso de memoria y el rendimiento, se recopilen y monitoreen continuamente.                             |   1   | D/V |
| 12.4.2 | Verifique que las tasas de éxito y fracaso se registren con la categorización de los tipos de error y sus causas raíz.                                                                                       |   1   | D/V |
| 12.4.3 | Verifique que la monitorización de la utilización de recursos incluya el uso de GPU/CPU, el consumo de memoria y los requisitos de almacenamiento, con alertas en caso de superar los umbrales establecidos. |   2   | D/V |

---

## C12.5 Planificación y Ejecución de Respuesta a Incidentes de IA

|   #    | Descripción                                                                                                                                                                                                                        | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.5.1 | Verifique que los planes de respuesta a incidentes aborden específicamente eventos de seguridad relacionados con la IA, incluyendo compromiso del modelo, envenenamiento de datos y ataques adversariales.                         |   1   | D/V |
| 12.5.2 | Verifique que los equipos de respuesta a incidentes tengan acceso a herramientas forenses específicas de IA y experiencia para investigar el comportamiento del modelo y los vectores de ataque.                                   |   2   | D/V |
| 12.5.3 | Verifique que el análisis posterior al incidente incluya consideraciones sobre el reentrenamiento del modelo, actualizaciones de los filtros de seguridad e integración de las lecciones aprendidas en los controles de seguridad. |   3   | D/V |

---

## C12.5 Detección de Degradación del Rendimiento de la IA

Monitorear y detectar la degradación en el rendimiento y la calidad del modelo de IA a lo largo del tiempo.

|   #    | Descripción                                                                                                                                                                     | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.5.1 | Verifique que la precisión, exactitud, recall y las puntuaciones F1 del modelo se monitoreen continuamente y se comparen con los umbrales base.                                 |   1   | D/V |
| 12.5.2 | Verifique que la detección de derivación de datos monitoree los cambios en la distribución de entrada que puedan afectar el rendimiento del modelo.                             |   1   | D/V |
| 12.5.3 | Verifique que la detección de deriva conceptual identifique cambios en la relación entre las entradas y las salidas esperadas.                                                  |   2   | D/V |
| 12.5.4 | Verifique que la degradación del rendimiento desencadene alertas automáticas e inicie los flujos de trabajo de reentrenamiento o reemplazo del modelo.                          |   2   | D/V |
| 12.5.5 | Verifique que el análisis de la causa raíz de la degradación correlacione las caídas de rendimiento con cambios en los datos, problemas de infraestructura o factores externos. |   3   |  V  |

---

## C12.6 Visualización de DAG y Seguridad del Flujo de Trabajo

Proteger los sistemas de visualización de flujos de trabajo contra fugas de información y ataques de manipulación.

|   #    | Descripción                                                                                                                                                                                        | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.6.1 | Verifique que los datos de visualización del DAG estén saneados para eliminar información sensible antes del almacenamiento o la transmisión.                                                      |   1   | D/V |
| 12.6.2 | Verificar que los controles de acceso a la visualización del flujo de trabajo aseguren que solo los usuarios autorizados puedan ver las rutas de decisión del agente y las trazas de razonamiento. |   1   | D/V |
| 12.6.3 | Verifique que la integridad de los datos del DAG esté protegida mediante firmas criptográficas y mecanismos de almacenamiento a prueba de manipulaciones.                                          |   2   | D/V |
| 12.6.4 | Verifique que los sistemas de visualización de flujos de trabajo implementen la validación de entradas para prevenir ataques de inyección a través de datos manipulados de nodos o conexiones.     |   2   | D/V |
| 12.6.5 | Verifique que las actualizaciones en tiempo real del DAG estén limitadas en tasa y validadas para prevenir ataques de denegación de servicio en los sistemas de visualización.                     |   3   | D/V |

---

## C12.7 Monitoreo Proactivo del Comportamiento de Seguridad

Detección y prevención de amenazas de seguridad mediante el análisis proactivo del comportamiento de agentes.

|   #    | Descripción                                                                                                                                                   | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.7.1 | Verifique que los comportamientos proactivos del agente estén validados en términos de seguridad antes de la ejecución, integrando una evaluación de riesgos. |   1   | D/V |
| 12.7.2 | Verifique que los disparadores de iniciativa autónoma incluyan la evaluación del contexto de seguridad y la evaluación del panorama de amenazas.              |   2   | D/V |
| 12.7.3 | Verifique que los patrones de comportamiento proactivo sean analizados para posibles implicaciones de seguridad y consecuencias no deseadas.                  |   2   | D/V |
| 12.7.4 | Verifique que las acciones proactivas críticas para la seguridad requieran cadenas de aprobación explícitas con registros de auditoría.                       |   3   | D/V |
| 12.7.5 | Verifique que la detección de anomalías de comportamiento identifique desviaciones en los patrones del agente proactivo que puedan indicar un compromiso.     |   3   | D/V |

---

## Referencias

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

