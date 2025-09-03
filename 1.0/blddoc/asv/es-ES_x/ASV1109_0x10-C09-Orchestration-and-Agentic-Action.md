# 9 Seguridad de la Orquestación Autónoma y de la Acción Agencial

## Objetivo de control

Asegúrese de que los sistemas de IA autónomos o multiagentes solo puedan ejecutar acciones que estén explícitamente previstas, autenticadas y que puedan ser auditadas dentro de umbrales acotados de costo y riesgo. Esto protege contra amenazas tales como compromiso del sistema autónomo, uso indebido de herramientas, detección de bucles de agentes, secuestro de las comunicaciones, suplantación de identidad, manipulación de enjambres y manipulación de la intención.

---

## 9.1 Agente Planificación de Tareas y Presupuestos de Recursión

Ralentizar planes recursivos y forzar puntos de control humanos para acciones privilegiadas.

|   #   | Descripción                                                                                                                                                                                                        | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 9.1.1 | Verifique que la profundidad máxima de recursión, la amplitud, el tiempo de reloj real, los tokens y el costo monetario por la ejecución de un agente estén configurados centralmente y bajo control de versiones. |   1   | D/V |
| 9.1.2 | Verifique que las acciones privilegiadas o irreversibles (p. ej., commits de código, transferencias financieras) requieran aprobación humana explícita a través de un canal auditable antes de la ejecución.       |   1   | D/V |
| 9.1.3 | Verifique que los monitores de recursos en tiempo real disparen la interrupción del disyuntor cuando se supere cualquier umbral presupuestario, deteniendo la expansión adicional de tareas.                       |   2   |  D  |
| 9.1.4 | Verifique que los eventos de disyuntor se registren con la identificación del agente, la condición desencadenante y el estado del plan capturado para revisión forense.                                            |   2   | D/V |
| 9.1.5 | Asegúrese de que las pruebas de seguridad cubran los escenarios de agotamiento presupuestario y de plan descontrolado, y confirme una parada segura sin pérdida de datos.                                          |   3   |  V  |
| 9.1.6 | Verifique que las políticas de presupuesto estén expresadas como política como código y se apliquen en CI/CD para bloquear la deriva de configuración.                                                             |   3   |  D  |

---

## 9.2 Aislamiento de plugins de herramientas

Aislar las interacciones con las herramientas para evitar el acceso no autorizado al sistema o la ejecución de código.

|   #   | Descripción                                                                                                                                                                                                                                 | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.2.1 | Verifique que cada herramienta o complemento se ejecute dentro de un sandbox a nivel del sistema operativo, de un contenedor o de WASM, con políticas de privilegios mínimos para el sistema de archivos, la red y las llamadas al sistema. |   1   | D/V |
| 9.2.2 | Verifique que los límites de recursos del sandbox (CPU, memoria, disco, tráfico de salida de red) y los tiempos de espera de ejecución se apliquen y se registren.                                                                          |   1   | D/V |
| 9.2.3 | Verifique que los binarios de la herramienta o los descriptores estén firmados digitalmente; las firmas se validan antes de cargarlos.                                                                                                      |   2   | D/V |
| 9.2.4 | Verifique que la telemetría del sandbox se envíe a un SIEM; las anomalías (p. ej., intentos de conexiones salientes) generan alertas.                                                                                                       |   2   |  V  |
| 9.2.5 | Verificar que los plugins de alto riesgo pasen revisión de seguridad y pruebas de penetración antes del despliegue en producción.                                                                                                           |   3   |  V  |
| 9.2.6 | Verifique que los intentos de escape del sandbox se bloqueen automáticamente y que el complemento infractor esté en cuarentena mientras se realiza la investigación.                                                                        |   3   | D/V |

---

## 9.3 Bucle Autónomo y Limitación de Costos

Detectar y detener la recursión descontrolada de agente-a-agente y las explosiones de costo.

|   #   | Descripción                                                                                                                                                | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.3.1 | Verifique que las llamadas entre agentes incluyan un límite de saltos o TTL y que el tiempo de ejecución decremente y haga cumplir ese límite.             |   1   | D/V |
| 9.3.2 | Verifique que los agentes mantengan un identificador único del grafo de invocación para detectar autoinvocación o patrones cíclicos.                       |   2   |  D  |
| 9.3.3 | Verifique que los contadores acumulativos de unidades de cómputo y gasto se rastrean por cadena de solicitudes; al exceder el límite, se aborta la cadena. |   2   | D/V |
| 9.3.4 | Verifique que el análisis formal o la verificación de modelos demuestre la ausencia de recursión no acotada en los protocolos de agentes.                  |   3   |  V  |
| 9.3.5 | Verifique que los eventos de interrupción de bucle generen alertas y alimenten métricas de mejora continua.                                                |   3   |  D  |

---

## 9.4 Protección contra el uso indebido a nivel de protocolo

Canales de comunicación seguros entre agentes y sistemas externos para prevenir el secuestro o la manipulación.

|   #   | Descripción                                                                                                                                                 | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.4.1 | Verifique que todos los mensajes de agente a herramienta y de agente a agente estén autenticados (p. ej., TLS mutuo o JWT) y cifrados de extremo a extremo. |   1   | D/V |
| 9.4.2 | Verifique que los esquemas se validen de forma estricta; los campos desconocidos o los mensajes malformados sean rechazados.                                |   1   |  D  |
| 9.4.3 | Verifique que las comprobaciones de integridad (MACs o firmas digitales) cubran toda la carga útil del mensaje, incluidos los parámetros de la herramienta. |   2   | D/V |
| 9.4.4 | Verifique que la protección contra ataques de repetición (nonces o ventanas de marca de tiempo) se aplique a nivel de la capa de protocolo.                 |   2   |  D  |
| 9.4.5 | Verifique que las implementaciones de protocolo se sometan a fuzzing y análisis estático para detectar fallas de inyección o deserialización.               |   3   |  V  |

---

## 9.5 Identidad del Agente y Evidencia de Manipulación

Asegúrese de que las acciones sean atribuibles y las modificaciones sean detectables.

|   #   | Descripción                                                                                                                                        | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.5.1 | Verifique que cada instancia de agente posea una identidad criptográfica única (par de claves o credencial basada en hardware).                    |   1   | D/V |
| 9.5.2 | Verifique que todas las acciones de los agentes estén firmadas y con marca de tiempo; los registros incluyan la firma para la no repudiación.      |   2   | D/V |
| 9.5.3 | Verifique que los registros a prueba de manipulaciones se almacenen en un medio de solo escritura (append-only) o de escritura única (write-once). |   2   |  V  |
| 9.5.4 | Verificar que las claves de identidad roten de acuerdo con un calendario definido y ante indicadores de compromiso.                                |   3   |  D  |
| 9.5.5 | Verifique que los intentos de suplantación o conflicto de claves desencadenen la cuarentena inmediata del agente afectado.                         |   3   | D/V |

---

## 9.6 Reducción de riesgos del enjambre multi-agente

Mitigar los peligros de comportamiento-colectivo mediante el aislamiento y el modelado formal de la seguridad.

|   #   | Descripción                                                                                                                                                       | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.6.1 | Verifique que los agentes que operan en diferentes dominios de seguridad se ejecuten en sandboxes de tiempo de ejecución aislados o en segmentos de red.          |   1   | D/V |
| 9.6.2 | Verifique que los comportamientos de enjambre estén modelados y verificados formalmente para la vivacidad y la seguridad antes del despliegue.                    |   3   |  V  |
| 9.6.3 | Verifique que los monitores en tiempo de ejecución detecten patrones inseguros emergentes (p. ej., oscilaciones e interbloqueos) e inicien una acción correctiva. |   3   |  D  |

---

## 9.7 Autenticación de Usuario y Herramienta / Autorización

Implementa controles de acceso robustos para cada acción desencadenada por el agente.

|   #   | Descripción                                                                                                                                                        | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 9.7.1 | Verifique que los agentes se autentiquen como principales de primera clase ante sistemas aguas abajo, sin volver a usar credenciales del usuario final.            |   1   | D/V |
| 9.7.2 | Verifique que las políticas de autorización granular limiten qué herramientas puede invocar un agente y qué parámetros puede suministrar.                          |   2   |  D  |
| 9.7.3 | Verifique que las verificaciones de privilegios se vuelvan a evaluar en cada llamada (autorización continua), no solo al inicio de la sesión.                      |   2   |  V  |
| 9.7.4 | Verifique que los privilegios delegados expiren automáticamente y requieran volver a obtener el consentimiento tras un tiempo de espera o un cambio en el alcance. |   3   |  D  |

---

## 9.8 Seguridad de la Comunicación entre Agentes

Cifrar y proteger la integridad de todos los mensajes entre agentes para contrarrestar la interceptación y la manipulación.

|   #   | Descripción                                                                                                                                                | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.8.1 | Verifique que la autenticación mutua y el cifrado con secreto perfecto hacia adelante (p. ej. TLS 1.3) sean obligatorios para los canales del agente.      |   1   | D/V |
| 9.8.2 | Verifique que la integridad del mensaje y su origen se validen antes de procesarlo; si falla, se generan alertas y se descarta el mensaje.                 |   1   |  D  |
| 9.8.3 | Verifique que los metadatos de la comunicación (sellos de tiempo, números de secuencia) se registren para facilitar la reconstrucción forense.             |   2   | D/V |
| 9.8.4 | Verifique que la verificación formal o la comprobación de modelos confirme que las máquinas de estados del protocolo no pueden llegar a estados inseguros. |   3   |  V  |

---

## 9.9 Verificación de intenciones y aplicación de restricciones

Verifique que las acciones del agente se alineen con la intención declarada por el usuario y con las restricciones del sistema.

|   #   | Descripción                                                                                                                                                                                                          | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.9.1 | Verifique que los solucionadores de restricciones previas a la ejecución verifiquen las acciones propuestas frente a las reglas de seguridad y a las políticas codificadas en el código.                             |   1   |  D  |
| 9.9.2 | Verifique que las acciones de alto impacto (financieras, destructivas, sensibles a la privacidad) requieren confirmación explícita de la intención por parte del usuario que inicia.                                 |   2   | D/V |
| 9.9.3 | Asegúrese de que las comprobaciones de post-condición verifiquen que las acciones completadas alcanzaron los efectos previstos sin efectos secundarios; las discrepancias desencadenan la reversión.                 |   2   |  V  |
| 9.9.4 | Verifique que los métodos formales (p. ej., verificación de modelos, demostración de teoremas) o las pruebas basadas en propiedades demuestren que los planes del agente cumplen todas las restricciones declaradas. |   3   |  V  |
| 9.9.5 | Verifique que los incidentes de desajuste-de-intención o violación-de-restricciones alimenten ciclos-de-mejora-continua y intercambio-de-inteligencia-de-amenazas.                                                   |   3   |  D  |

---

## 9.10 Agente Razonamiento Estrategia Seguridad

Selección y ejecución seguras de diferentes estrategias de razonamiento, incluyendo ReAct, Chain-of-Thought y Tree-of-Thoughts.

|   #    | Descripción                                                                                                                                                                                                                                                                    | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 9.10.1 | Verifique que la selección de la estrategia de razonamiento utilice criterios determinísticos (complejidad de la entrada, tipo de tarea, contexto de seguridad) y que entradas idénticas produzcan selecciones de estrategia idénticas dentro del mismo contexto de seguridad. |   1   | D/V |
| 9.10.2 | Verifique que cada estrategia de razonamiento (ReAct, Cadena de pensamiento, Árbol de pensamientos) tenga validación de entrada dedicada, sanitización de salida y límites de tiempo de ejecución específicos a su enfoque cognitivo.                                          |   1   | D/V |
| 9.10.3 | Verifique que las transiciones de la estrategia de razonamiento se registren con el contexto completo, incluyendo las características de entrada, los valores de los criterios de selección y los metadatos de ejecución para la reconstrucción del rastro de auditoría.       |   2   | D/V |
| 9.10.4 | Verifique que el razonamiento Tree-of-Thoughts incluya mecanismos de poda de ramas que terminen la exploración cuando se detecten violaciones de políticas, límites de recursos o límites de seguridad.                                                                        |   2   | D/V |
| 9.10.5 | Verifique que los ciclos de ReAct (Reason-Act-Observe) incluyan puntos de control de validación en cada fase: verificación de pasos de razonamiento, autorización de acciones y sanitización de observaciones antes de proceder.                                               |   2   | D/V |
| 9.10.6 | Verifique que las métricas de rendimiento de la estrategia de razonamiento (tiempo de ejecución, uso de recursos, calidad de la salida) sean monitoreadas con alertas automatizadas cuando las métricas se desvíen más allá de los umbrales configurados.                      |   3   | D/V |
| 9.10.7 | Verifique que los enfoques de razonamiento híbrido que combinan múltiples estrategias mantengan la validación de entradas y las restricciones de salida de todas las estrategias constituyentes, sin eludir ningún control de seguridad.                                       |   3   | D/V |
| 9.10.8 | Verifique que las pruebas de seguridad de la estrategia de razonamiento incluyan fuzzing con entradas malformadas, indicaciones adversarias diseñadas para forzar el cambio de estrategia y pruebas de condiciones límite para cada enfoque cognitivo.                         |   3   | D/V |

---

## 9.11 Gestión del estado del ciclo de vida del agente y seguridad

Inicialización segura del agente, transiciones de estado y terminación con trazas de auditoría criptográficas y procedimientos de recuperación definidos.

|   #    | Descripción                                                                                                                                                                                                                                                                                                                | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.11.1 | Verifique que la inicialización del agente incluya el establecimiento de identidad criptográfica con credenciales respaldadas por hardware y registros de auditoría de inicio inmutables que contengan el ID del agente, la marca de tiempo, el hash de configuración y los parámetros de inicialización.                  |   1   | D/V |
| 9.11.2 | Verifique que las transiciones de estado del agente estén firmadas criptográficamente, tengan marca de tiempo y se registren con un contexto completo que incluya los eventos desencadenantes, el hash del estado anterior, el hash del nuevo estado y las validaciones de seguridad realizadas.                           |   2   | D/V |
| 9.11.3 | Verifique que los procedimientos de apagado del agente incluyan el borrado seguro de la memoria mediante borrado criptográfico o sobreescritura en varias pasadas, la revocación de credenciales con notificación a la autoridad de certificación y la generación de certificados de terminación a prueba de manipulación. |   2   | D/V |
| 9.11.4 | Verifique que los mecanismos de recuperación de agentes validen la integridad del estado utilizando sumas de verificación criptográficas (SHA-256 como mínimo) y reviertan a estados previamente verificados como válidos cuando se detecte corrupción, con alertas automatizadas y requisitos de aprobación manual.       |   3   | D/V |
| 9.11.5 | Verifique que los mecanismos de persistencia de los agentes cifren los datos de estado sensibles con claves AES-256 por agente y que implementen una rotación de claves segura en intervalos configurables (máximo 90 días) con despliegue sin tiempo de inactividad.                                                      |   3   | D/V |

---

## 9.12 Marco de Seguridad de la Integración de Herramientas

Controles de seguridad para la carga dinámica de herramientas, la ejecución y la validación de resultados, con procesos de evaluación de riesgos y aprobación definidos.

|   #    | Descripción                                                                                                                                                                                                                                                                                                    | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.12.1 | Verifique que los descriptores de herramientas incluyan metadatos de seguridad que especifiquen privilegios requeridos (lectura/escritura/ejecución), niveles de riesgo (bajo/medio/alto), límites de recursos (CPU, memoria, red) y requisitos de validación documentados en los manifiestos de herramientas. |   1   | D/V |
| 9.12.2 | Verifique que los resultados de la ejecución de la herramienta se validen frente a los esquemas esperados (Esquema JSON, Esquema XML) y a las políticas de seguridad (sanitización de la salida, clasificación de datos) antes de la integración con límites de tiempo y procedimientos de manejo de errores.  |   1   | D/V |
| 9.12.3 | Verifique que los registros de interacción de herramientas incluyan un contexto de seguridad detallado, incluyendo el uso de privilegios, patrones de acceso a datos, tiempo de ejecución, consumo de recursos y códigos de retorno, con registro estructurado para la integración con SIEM.                   |   2   | D/V |
| 9.12.4 | Verificar que los mecanismos de carga dinámica de herramientas validen firmas digitales utilizando una infraestructura PKI e implementar protocolos de carga seguros con aislamiento de sandbox y verificación de permisos antes de la ejecución.                                                              |   2   | D/V |
| 9.12.5 | Verifique que las evaluaciones de seguridad de la herramienta se activen automáticamente para nuevas versiones con puertas de aprobación obligatorias, que incluyen análisis estático, pruebas dinámicas y revisión del equipo de seguridad, con criterios de aprobación documentados y requisitos de SLA.     |   3   | D/V |

---

### Referencias

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

