# 9 Orquestación Autónoma y Seguridad de Acción Agencial

## Objetivo de Control

Asegurar que los sistemas de IA autónomos o multiagente solo puedan ejecutar acciones que sean explícitamente intencionadas, autenticadas, auditables y dentro de umbrales limitados de costo y riesgo. Esto protege contra amenazas como Compromiso del Sistema Autónomo, Uso Indebido de Herramientas, Detección de Bucle de Agentes, Secuestro de Comunicación, Suplantación de Identidad, Manipulación de Enjambres y Manipulación de Intenciones.

---

## 9.1 Presupuestos de planificación de tareas del agente y recursión

Limitar los planes recursivos y forzar puntos de control humanos para acciones privilegiadas.

|   #   | Descripción                                                                                                                                                                                                             | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.1.1 | Verifique que la profundidad máxima de recursión, el ancho, el tiempo de reloj de pared, los tokens y el costo monetario por ejecución de agente estén configurados de manera centralizada y controlados por versiones. |   1   | D/V |
| 9.1.2 | Verifique que las acciones privilegiadas o irreversibles (por ejemplo, commits de código, transferencias financieras) requieran aprobación humana explícita a través de un canal auditable antes de su ejecución.       |   1   | D/V |
| 9.1.3 | Verifique que los monitores de recursos en tiempo real activen la interrupción del disyuntor cuando se supere cualquier umbral de presupuesto, deteniendo la expansión adicional de tareas.                             |   2   |  D  |
| 9.1.4 | Verifique que los eventos del disyuntor se registren con el ID del agente, la condición que lo activó y el estado del plan capturado para su revisión forense.                                                          |   2   | D/V |
| 9.1.5 | Verifique que las pruebas de seguridad cubran los escenarios de agotamiento del presupuesto y planes descontrolados, confirmando la detención segura sin pérdida de datos.                                              |   3   |  V  |
| 9.1.6 | Verifique que las políticas presupuestarias estén expresadas como política-como-código y se apliquen en CI/CD para bloquear la deriva de configuración.                                                                 |   3   |  D  |

---

## 9.2 Aislamiento de Complementos de Herramientas

Aislar las interacciones de la herramienta para prevenir el acceso no autorizado al sistema o la ejecución de código.

|   #   | Descripción                                                                                                                                                                                              | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.2.1 | Verifique que cada herramienta/plugin se ejecute dentro de un sistema operativo, contenedor o sandbox a nivel WASM con políticas de sistema de archivos, red y llamadas al sistema de mínimo privilegio. |   1   | D/V |
| 9.2.2 | Verifique que las cuotas de recursos del sandbox (CPU, memoria, disco, salida de red) y los tiempos de espera de ejecución se apliquen y registren.                                                      |   1   | D/V |
| 9.2.3 | Verificar que los binarios o descriptores de las herramientas estén firmados digitalmente; las firmas se validan antes de la carga.                                                                      |   2   | D/V |
| 9.2.4 | Verifique que la telemetría del sandbox se transmita a un SIEM; las anomalías (por ejemplo, intentos de conexiones salientes) generen alertas.                                                           |   2   |  V  |
| 9.2.5 | Verifique que los plugins de alto riesgo se sometan a una revisión de seguridad y pruebas de penetración antes de su despliegue en producción.                                                           |   3   |  V  |
| 9.2.6 | Verifique que los intentos de escape del sandbox sean bloqueados automáticamente y que el plugin infractor sea puesto en cuarentena mientras se realiza la investigación.                                |   3   | D/V |

---

## 9.3 Bucle Autónomo y Limitación de Costos

Detectar y detener la recursión incontrolada de agente a agente y las explosiones de costos.

|   #   | Descripción                                                                                                                                       | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.3.1 | Verifique que las llamadas entre agentes incluyan un límite de saltos o TTL que el tiempo de ejecución decremente y haga cumplir.                 |   1   | D/V |
| 9.3.2 | Verifique que los agentes mantengan un ID de grafo de invocación único para detectar auto-invocación o patrones cíclicos.                         |   2   |  D  |
| 9.3.3 | Verifique que los contadores acumulativos de unidades de cómputo y gasto se rastreen por cadena de solicitud; superar el límite aborta la cadena. |   2   | D/V |
| 9.3.4 | Verifique que el análisis formal o la verificación de modelos demuestren la ausencia de recursión no acotada en los protocolos de agentes.        |   3   |  V  |
| 9.3.5 | Verifique que los eventos de abortar el bucle generen alertas y alimenten métricas de mejora continua.                                            |   3   |  D  |

---

## 9.4 Protección contra el uso indebido a nivel de protocolo

Canales de comunicación seguros entre agentes y sistemas externos para prevenir el secuestro o la manipulación.

|   #   | Descripción                                                                                                                                                      | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.4.1 | Verifique que todos los mensajes de agente a herramienta y de agente a agente estén autenticados (por ejemplo, TLS mutuo o JWT) y cifrados de extremo a extremo. |   1   | D/V |
| 9.4.2 | Verifique que los esquemas sean validados estrictamente; los campos desconocidos o los mensajes mal formados sean rechazados.                                    |   1   |  D  |
| 9.4.3 | Verifique que las comprobaciones de integridad (MAC o firmas digitales) cubran toda la carga útil del mensaje, incluidos los parámetros de la herramienta.       |   2   | D/V |
| 9.4.4 | Verifique que la protección contra repetición (nonces o ventanas de marca de tiempo) se aplique en la capa del protocolo.                                        |   2   |  D  |
| 9.4.5 | Verifique que las implementaciones del protocolo se sometan a fuzzing y análisis estático para detectar fallas de inyección o deserialización.                   |   3   |  V  |

---

## 9.5 Identidad del Agente y Evidencia de Manipulación

Asegurar que las acciones sean atribuibles y las modificaciones detectables.

|   #   | Descripción                                                                                                                                      | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 9.5.1 | Verifique que cada instancia de agente posea una identidad criptográfica única (par de claves o credencial basada en hardware).                  |   1   | D/V |
| 9.5.2 | Verifique que todas las acciones del agente estén firmadas y con marca de tiempo; los registros incluyen la firma para garantizar la no repudio. |   2   | D/V |
| 9.5.3 | Verifique que los registros a prueba de manipulaciones se almacenen en un medio de solo anexado o de escritura única.                            |   2   |  V  |
| 9.5.4 | Verifique que las claves de identidad roten según un calendario definido y en presencia de indicadores de compromiso.                            |   3   |  D  |
| 9.5.5 | Verifique que los intentos de suplantación o conflicto de claves desencadenen la cuarentena inmediata del agente afectado.                       |   3   | D/V |

---

## 9.6 Reducción de Riesgos en Enjambres Multi-Agente

Mitigue los riesgos del comportamiento colectivo mediante aislamiento y modelado formal de seguridad.

|   #   | Descripción                                                                                                                                                     | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.6.1 | Verifique que los agentes que operan en diferentes dominios de seguridad se ejecuten en entornos de ejecución aislados o en segmentos de red separados.         |   1   | D/V |
| 9.6.2 | Verifique que los comportamientos de enjambre estén modelados y formalmente verificados para vivacidad y seguridad antes de la implementación.                  |   3   |  V  |
| 9.6.3 | Verifique que los monitores en tiempo de ejecución detecten patrones emergentes inseguros (por ejemplo, oscilaciones, bloqueos) e inicien acciones correctivas. |   3   |  D  |

---

## 9.7 Autenticación / Autorización de Usuario y Herramienta

Implemente controles de acceso robustos para cada acción activada por el agente.

|   #   | Descripción                                                                                                                                                       | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.7.1 | Verifique que los agentes se autentiquen como principales de primera clase en los sistemas descendentes, sin reutilizar nunca las credenciales del usuario final. |   1   | D/V |
| 9.7.2 | Verifique que las políticas de autorización detalladas restrinjan qué herramientas puede invocar un agente y qué parámetros puede suministrar.                    |   2   |  D  |
| 9.7.3 | Verifique que las comprobaciones de privilegios se reevalúen en cada llamada (autorización continua), no sólo al inicio de la sesión.                             |   2   |  V  |
| 9.7.4 | Verifique que los privilegios delegados expiren automáticamente y requieran nuevo consentimiento después del tiempo de espera o cambio de alcance.                |   3   |  D  |

---

## 9.8 Seguridad en la Comunicación entre Agentes

Cifrar y proteger la integridad de todos los mensajes entre agentes para impedir la interceptación y la manipulación.

|   #   | Descripción                                                                                                                                                       | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.8.1 | Verifique que la autenticación mutua y el cifrado con secreto hacia adelante perfecto (por ejemplo, TLS 1.3) sean obligatorios para los canales de agente.        |   1   | D/V |
| 9.8.2 | Verifique que la integridad y el origen del mensaje se validen antes de procesarlo; los fallos generan alertas y descartan el mensaje.                            |   1   |  D  |
| 9.8.3 | Verifique que los metadatos de comunicación (marcas de tiempo, números de secuencia) se registren para respaldar la reconstrucción forense.                       |   2   | D/V |
| 9.8.4 | Verifique que la verificación formal o la comprobación de modelos confirmen que las máquinas de estados del protocolo no pueden ser llevadas a estados inseguros. |   3   |  V  |

---

## 9.9 Verificación de Intención y Aplicación de Restricciones

Validar que las acciones del agente se alineen con la intención declarada por el usuario y las restricciones del sistema.

|   #   | Descripción                                                                                                                                                                                                                   | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.9.1 | Verifique que los solucionadores de restricciones previas a la ejecución revisen las acciones propuestas contra las reglas de seguridad y políticas codificadas rígidamente.                                                  |   1   |  D  |
| 9.9.2 | Verifique que las acciones de alto impacto (financieras, destructivas, sensibles a la privacidad) requieran una confirmación explícita de intención por parte del usuario que las inicia.                                     |   2   | D/V |
| 9.9.3 | Verifique que las comprobaciones de post-condición validen que las acciones completadas lograron los efectos previstos sin efectos secundarios; las discrepancias activan la reversión.                                       |   2   |  V  |
| 9.9.4 | Verifique que los métodos formales (por ejemplo, verificación de modelos, demostración de teoremas) o las pruebas basadas en propiedades demuestren que los planes del agente cumplen con todas las restricciones declaradas. |   3   |  V  |
| 9.9.5 | Verifique que los incidentes de incompatibilidad de intención o violación de restricciones alimenten los ciclos de mejora continua y el intercambio de inteligencia sobre amenazas.                                           |   3   |  D  |

---

## 9.10 Seguridad de la Estrategia de Razonamiento del Agente

Selección y ejecución segura de diferentes estrategias de razonamiento, incluyendo los enfoques ReAct, Chain-of-Thought y Tree-of-Thoughts.

|   #    | Descripción                                                                                                                                                                                                                                                              | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 9.10.1 | Verifique que la selección de la estrategia de razonamiento use criterios deterministas (complejidad de la entrada, tipo de tarea, contexto de seguridad) y que entradas idénticas produzcan selecciones de estrategia idénticas dentro del mismo contexto de seguridad. |   1   | D/V |
| 9.10.2 | Verifique que cada estrategia de razonamiento (ReAct, Cadena de Pensamientos, Árbol de Pensamientos) tenga validación de entrada dedicada, saneamiento de salida y límites de tiempo de ejecución específicos para su enfoque cognitivo.                                 |   1   | D/V |
| 9.10.3 | Verifique que las transiciones de la estrategia de razonamiento se registren con contexto completo, incluyendo las características de entrada, los valores de los criterios de selección y los metadatos de ejecución para la reconstrucción del historial de auditoría. |   2   | D/V |
| 9.10.4 | Verifique que el razonamiento de Árbol de Pensamientos incluya mecanismos de poda de ramas que terminen la exploración cuando se detecten violaciones de políticas, límites de recursos o límites de seguridad.                                                          |   2   | D/V |
| 9.10.5 | Verifique que los ciclos ReAct (Razonar-Actuar-Observar) incluyan puntos de control de validación en cada fase: verificación del paso de razonamiento, autorización de la acción y sanitización de la observación antes de proceder.                                     |   2   | D/V |
| 9.10.6 | Verifique que los métricas de rendimiento de la estrategia de razonamiento (tiempo de ejecución, uso de recursos, calidad del resultado) se monitoreen con alertas automatizadas cuando las métricas se desvíen más allá de los umbrales configurados.                   |   3   | D/V |
| 9.10.7 | Verifique que los enfoques de razonamiento híbrido que combinan múltiples estrategias mantengan la validación de entrada y las restricciones de salida de todas las estrategias constituyentes sin eludir ningún control de seguridad.                                   |   3   | D/V |
| 9.10.8 | Verifique que la prueba de seguridad de la estrategia de razonamiento incluya fuzzing con entradas malformadas, solicitudes adversarias diseñadas para forzar el cambio de estrategia y pruebas de condiciones límite para cada enfoque cognitivo.                       |   3   | D/V |

---

## 9.11 Gestión del Estado del Ciclo de Vida del Agente y Seguridad

Inicialización segura del agente, transiciones de estado y terminación con registros de auditoría criptográficos y procedimientos de recuperación definidos.

|   #    | Descripción                                                                                                                                                                                                                                                                                                          | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.11.1 | Verifique que la inicialización del agente incluya el establecimiento de identidad criptográfica con credenciales respaldadas por hardware y registros de auditoría de inicio inmutables que contengan el ID del agente, la marca de tiempo, el hash de configuración y los parámetros de inicialización.            |   1   | D/V |
| 9.11.2 | Verifique que las transiciones de estado del agente estén firmadas criptográficamente, con sello de tiempo y registradas con contexto completo, incluyendo los eventos desencadenantes, el hash del estado anterior, el hash del nuevo estado y las validaciones de seguridad realizadas.                            |   2   | D/V |
| 9.11.3 | Verifique que los procedimientos de apagado del agente incluyan el borrado seguro de la memoria mediante borrado criptográfico o sobreescritura múltiple, la revocación de credenciales con notificación a la autoridad certificadora, y la generación de certificados de terminación con evidencia de manipulación. |   2   | D/V |
| 9.11.4 | Verifique que los mecanismos de recuperación del agente validen la integridad del estado utilizando sumas de verificación criptográficas (mínimo SHA-256) y que retrocedan a estados conocidos como buenos cuando se detecte corrupción, con alertas automatizadas y requisitos de aprobación manual.                |   3   | D/V |
| 9.11.5 | Verifique que los mecanismos de persistencia del agente cifren los datos de estado sensibles con claves AES-256 por agente y que implementen rotación segura de claves según horarios configurables (máximo 90 días) con despliegue sin tiempo de inactividad.                                                       |   3   | D/V |

---

## 9.12 Marco de Seguridad para la Integración de Herramientas

Controles de seguridad para la carga dinámica de herramientas, ejecución y validación de resultados con procesos definidos de evaluación de riesgos y aprobación.

|   #    | Descripción                                                                                                                                                                                                                                                                                                                | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 9.12.1 | Verifique que los descriptores de las herramientas incluyan metadatos de seguridad que especifiquen los privilegios requeridos (lectura/escritura/ejecución), niveles de riesgo (bajo/medio/alto), límites de recursos (CPU, memoria, red) y requisitos de validación documentados en los manifiestos de las herramientas. |   1   | D/V |
| 9.12.2 | Verifique que los resultados de la ejecución de la herramienta se validen contra los esquemas esperados (JSON Schema, XML Schema) y las políticas de seguridad (saneamiento de salida, clasificación de datos) antes de la integración, con límites de tiempo y procedimientos de manejo de errores.                       |   1   | D/V |
| 9.12.3 | Verifique que los registros de interacción de la herramienta incluyan un contexto de seguridad detallado que incluya el uso de privilegios, patrones de acceso a datos, tiempo de ejecución, consumo de recursos y códigos de retorno con registro estructurado para la integración con SIEM.                              |   2   | D/V |
| 9.12.4 | Verifique que los mecanismos de carga dinámica de herramientas validen las firmas digitales utilizando la infraestructura PKI e implementen protocolos de carga segura con aislamiento en sandbox y verificación de permisos antes de la ejecución.                                                                        |   2   | D/V |
| 9.12.5 | Verifique que las evaluaciones de seguridad de la herramienta se activen automáticamente para las nuevas versiones con puertas de aprobación obligatorias que incluyan análisis estático, pruebas dinámicas y revisión del equipo de seguridad con criterios de aprobación documentados y requisitos de SLA.               |   3   | D/V |

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

