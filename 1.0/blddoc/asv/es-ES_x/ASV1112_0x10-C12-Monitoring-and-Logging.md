# C12 Monitoreo, Registro y Detección de Anomalías

## Objetivo de control

Esta sección proporciona los requisitos para ofrecer visibilidad en tiempo real y forense de lo que el modelo y otros componentes de IA ven, hacen y devuelven, de modo que las amenazas puedan ser detectadas, priorizadas y de las que se pueda aprender.

## C12.1 Registro de Solicitudes y Respuestas

|   #    | Descripción                                                                                                                                                                                                                                                                   | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.1.1 | Verifique que todas las solicitudes del usuario y las respuestas del modelo se registren con metadatos apropiados (p. ej., marca de tiempo, ID de usuario, ID de sesión, versión del modelo).                                                                                 |   1   | D/V |
| 12.1.2 | Verifique que los registros se almacenen en repositorios seguros y con control de acceso, con políticas de retención adecuadas y procedimientos de respaldo.                                                                                                                  |   1   | D/V |
| 12.1.3 | Verifique que los sistemas de almacenamiento de registros implementen cifrado en reposo y en tránsito para proteger la información sensible contenida en los registros.                                                                                                       |   1   | D/V |
| 12.1.4 | Verifique que los datos sensibles en las indicaciones y en las salidas se enmascaren o se redacten automáticamente antes del registro, con reglas de enmascaramiento configurables para PII (información de identificación personal), credenciales e información propietaria. |   1   | D/V |
| 12.1.5 | Verifique que las decisiones de política y las acciones de filtrado de seguridad se registren con suficiente detalle para permitir la auditoría y la depuración de los sistemas de moderación de contenido.                                                                   |   2   | D/V |
| 12.1.6 | Verifique que la integridad de los registros esté protegida, por ejemplo, mediante firmas criptográficas o almacenamiento de solo escritura.                                                                                                                                  |   2   | D/V |

---

## C12.2 Detección de abuso y alertas

|   #    | Descripción                                                                                                                                                                                                                   | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.2.1 | Verifique que el sistema detecte y alerte sobre patrones conocidos de jailbreak, intentos de inyección de indicaciones y entradas adversarias utilizando detección basada en firmas.                                          |   1   | D/V |
| 12.2.2 | Verifique que el sistema se integre con las plataformas existentes de Security Information and Event Management (SIEM) utilizando formatos de registro y protocolos estándar.                                                 |   1   | D/V |
| 12.2.3 | Verifique que los eventos de seguridad enriquecidos incluyan contexto específico de IA, como identificadores de modelo, puntuaciones de confianza y decisiones del filtro de seguridad.                                       |   2   | D/V |
| 12.2.4 | Verifique que la detección de anomalías conductuales identifique patrones de conversación inusuales, intentos de reintento excesivos o comportamientos de sondeo sistemáticos.                                                |   2   | D/V |
| 12.2.5 | Verifique que los mecanismos de alerta en tiempo-real notifiquen a los equipos de seguridad cuando se detecten posibles violaciones de políticas o intentos de ataque.                                                        |   2   | D/V |
| 12.2.6 | Verifique que se hayan incluido reglas personalizadas para detectar patrones de amenaza específicos de IA, incluyendo intentos coordinados de jailbreak, campañas de inyección de prompts y ataques de extracción de modelos. |   2   | D/V |
| 12.2.7 | Verifique que los flujos de trabajo automatizados de respuesta a incidentes puedan aislar modelos comprometidos, bloquear usuarios malintencionados y escalar eventos de seguridad críticos.                                  |   3   | D/V |

---

## C12.3 Detección de deriva del modelo

|   #    | Descripción                                                                                                                                                                                                         | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.3.1 | Verificar que el sistema realiza un seguimiento de métricas de rendimiento básicas, como precisión, puntuaciones de confianza, latencia y tasas de error, a lo largo de las versiones del modelo y de los períodos. |   1   | D/V |
| 12.3.2 | Verifique que las alertas automatizadas se activen cuando las métricas de rendimiento superen los umbrales de degradación predefinidos o se desvíen significativamente de las líneas base.                          |   2   | D/V |
| 12.3.3 | Verifique que los monitores de detección de alucinaciones identifiquen y señalen casos en los que las salidas del modelo contengan información factualmente incorrecta, inconsistente o fabricada.                  |   2   | D/V |

---

## C12.4 Telemetría de Rendimiento y Comportamiento

|   #    | Descripción                                                                                                                                                                                | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 12.4.1 | Verifique que las métricas operativas, entre ellas la latencia de las solicitudes, el consumo de tokens, el uso de memoria y el rendimiento, se recolecten y supervisen de forma continua. |   1   | D/V |
| 12.4.2 | Verifique que las tasas de éxito y de fallo se registren con la categorización de tipos de errores y sus causas raíz.                                                                      |   1   | D/V |
| 12.4.3 | Verifique que la supervisión del uso de recursos incluya el uso de GPU/CPU, consumo de memoria y requisitos de almacenamiento, con alertas cuando se superen los umbrales.                 |   2   | D/V |

---

## C12.5 Planificación y Ejecución de la Respuesta a Incidentes de IA

|   #    | Descripción                                                                                                                                                                                                                 | Nivel | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.5.1 | Verifique que los planes de respuesta ante incidentes aborden específicamente los eventos de seguridad relacionados con IA, incluidos el compromiso del modelo, el envenenamiento de datos y los ataques adversariales.     |   1   | D/V |
| 12.5.2 | Asegúrese de que los equipos de respuesta a incidentes tengan acceso a herramientas forenses específicas de IA y a la experiencia necesaria para investigar el comportamiento de los modelos y los vectores de ataque.      |   2   | D/V |
| 12.5.3 | Verifique que el análisis posterior al incidente incluya consideraciones de reentrenamiento del modelo, actualizaciones de filtros de seguridad y la integración de las lecciones aprendidas en los controles de seguridad. |   3   | D/V |

---

## C12.5 Detección de la degradación del rendimiento de la IA

Monitorear y detectar la degradación del rendimiento y de la calidad de los modelos de IA a lo largo del tiempo.

|   #    | Descripción                                                                                                                                                                     | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.5.1 | Verifique que la exactitud del modelo, la precisión, la sensibilidad y las puntuaciones F1 se supervisen continuamente y se comparen con umbrales de referencia.                |   1   | D/V |
| 12.5.2 | Verifique que la detección de deriva de datos monitoree los cambios en la distribución de entrada que puedan afectar el rendimiento del modelo.                                 |   1   | D/V |
| 12.5.3 | Verifique que la detección de deriva de concepto identifique cambios en la relación entre las entradas y las salidas esperadas.                                                 |   2   | D/V |
| 12.5.4 | Asegúrese de que la degradación del rendimiento active alertas automáticas e inicie flujos de trabajo de reentrenamiento o reemplazo del modelo.                                |   2   | D/V |
| 12.5.5 | Verifique que el análisis de la causa raíz de la degradación correlacione las caídas de rendimiento con cambios en los datos, problemas de infraestructura o factores externos. |   3   |  V  |

---

## C12.6 Visualización de DAG y Seguridad del Flujo de Trabajo

Proteja los sistemas de visualización de flujos de trabajo contra la filtración de información y ataques de manipulación.

|   #    | Descripción                                                                                                                                                                                         | Nivel | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.6.1 | Verifique que los datos de visualización de DAG estén sanitizados para eliminar información sensible antes del almacenamiento o la transmisión.                                                     |   1   | D/V |
| 12.6.2 | Verifique que los controles de acceso de la visualización de flujos de trabajo aseguren que solo los usuarios autorizados puedan ver las rutas de decisión del agente y las trazas de razonamiento. |   1   | D/V |
| 12.6.3 | Verifique que la integridad de los datos del DAG esté protegida mediante firmas criptográficas y mecanismos de almacenamiento a prueba de manipulación.                                             |   2   | D/V |
| 12.6.4 | Asegúrese de que los sistemas de visualización de flujos de trabajo implementen la validación de entradas para prevenir ataques de inyección a través de datos de nodos o aristas diseñados.        |   2   | D/V |
| 12.6.5 | Verifique que las actualizaciones en tiempo real del DAG estén limitadas por tasa y validadas para prevenir ataques de denegación de servicio en sistemas de visualización.                         |   3   | D/V |

---

## C12.7 Monitoreo proactivo del comportamiento de seguridad

Detección y prevención de amenazas de seguridad mediante el análisis proactivo del comportamiento de los agentes.

|   #    | Descripción                                                                                                                                                                | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 12.7.1 | Verifique que los comportamientos de los agentes proactivos estén validados en términos de seguridad antes de la ejecución con la integración de la evaluación de riesgos. |   1   | D/V |
| 12.7.2 | Verifique que los disparadores de iniciativas autónomas incluyan la evaluación del contexto de seguridad y la evaluación del panorama de amenazas.                         |   2   | D/V |
| 12.7.3 | Verifique que los patrones de comportamiento proactivo se analicen en busca de posibles implicaciones de seguridad y consecuencias no deseadas.                            |   2   | D/V |
| 12.7.4 | Verifique que las acciones proactivas críticas para la seguridad requieran cadenas de aprobación explícitas con registros de auditoría.                                    |   3   | D/V |
| 12.7.5 | Verifique que la detección de anomalías conductuales identifique desviaciones en los patrones de agentes proactivos que podrían indicar compromiso.                        |   3   | D/V |

---

## Referencias

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

