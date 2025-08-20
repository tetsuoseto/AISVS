# Comportamiento del Modelo C7, Control de Salida y Aseguramiento de la Seguridad

## Objetivo de Control

Las salidas del modelo deben ser estructuradas, fiables, seguras, explicables y monitoreadas continuamente en producción. Hacerlo reduce alucinaciones, fugas de privacidad, contenido dañino y acciones fuera de control, mientras aumenta la confianza del usuario y el cumplimiento normativo.

---

## C7.1 Aplicación del formato de salida

Los esquemas estrictos, la decodificación restringida y la validación posterior detienen el contenido malformado o malicioso antes de que se propague.

|   #   | Descripción                                                                                                                                                                                                                       | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.1.1 | Verifique que los esquemas de respuesta (p. ej., JSON Schema) se proporcionen en el mensaje del sistema y que cada salida se valide automáticamente; las salidas que no cumplan con el esquema desencadenan reparación o rechazo. |   1   | D/V |
| 7.1.2 | Verifique que la decodificación restringida (tokens de detención, expresiones regulares, máximo de tokens) esté habilitada para prevenir desbordamientos o canales laterales de inyección de indicaciones.                        |   1   | D/V |
| 7.1.3 | Verifique que los componentes posteriores traten las salidas como no confiables y las validen contra esquemas o deserializadores seguros contra inyección.                                                                        |   2   | D/V |
| 7.1.4 | Verifique que los eventos de salida incorrecta estén registrados, limitados por tasa y visibles en el monitoreo.                                                                                                                  |   3   |  V  |

---

## C7.2 Detección y Mitigación de Alucinaciones

La estimación de la incertidumbre y las estrategias de respaldo limitan las respuestas fabricadas.

|   #   | Descripción                                                                                                                                                                                                     | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.2.1 | Verifique que las probabilidades logarítmicas a nivel de token, la auto-consistencia de conjunto, o los detectores de alucinaciones afinados asignen una puntuación de confianza a cada respuesta.              |   1   | D/V |
| 7.2.2 | Verifique que las respuestas por debajo de un umbral de confianza configurable activen flujos de trabajo de respaldo (por ejemplo, generación aumentada por recuperación, modelo secundario o revisión humana). |   1   | D/V |
| 7.2.3 | Verifique que los incidentes de alucinación estén etiquetados con metadatos de causa raíz y sean enviados a las tuberías de post-mortem y ajuste fino.                                                          |   2   | D/V |
| 7.2.4 | Verifique que los umbrales y detectores se recalibren después de actualizaciones importantes del modelo o de la base de conocimiento.                                                                           |   3   | D/V |
| 7.2.5 | Verifique que las visualizaciones del panel de control rastreen las tasas de alucinación.                                                                                                                       |   3   |  V  |

---

## C7.3 Filtrado de Seguridad y Privacidad de Salida

Los filtros de políticas y la cobertura del equipo rojo protegen a los usuarios y datos confidenciales.

|   #   | Descripción                                                                                                                                                                          | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 7.3.1 | Verifique que los clasificadores previos y posteriores a la generación bloqueen contenido de odio, acoso, autolesiones, extremista y sexualmente explícito alineado con la política. |   1   | D/V |
| 7.3.2 | Verifique que la detección y redacción automática de PII/PCI se ejecuten en cada respuesta; las violaciones generan un incidente de privacidad.                                      |   1   | D/V |
| 7.3.3 | Verificar que las etiquetas de confidencialidad (por ejemplo, secretos comerciales) se propaguen a través de modalidades para evitar fugas en texto, imágenes o código.              |   2   |  D  |
| 7.3.4 | Verifique que los intentos de eludir el filtro o las clasificaciones de alto riesgo requieran una aprobación secundaria o la reautenticación del usuario.                            |   3   | D/V |
| 7.3.5 | Verifique que los umbrales de filtrado reflejen las jurisdicciones legales y el contexto de edad/rol del usuario.                                                                    |   3   | D/V |

---

## C7.4 Limitación de Salida y Acción

Los límites de velocidad y las puertas de aprobación previenen el abuso y la autonomía excesiva.

|   #   | Descripción                                                                                                                                                                                          | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.4.1 | Verifique que las cuotas por usuario y por clave API limiten las solicitudes, los tokens y el costo con retroceso exponencial en errores 429.                                                        |   1   |  D  |
| 7.4.2 | Verifique que las acciones privilegiadas (escritura de archivos, ejecución de código, llamadas de red) requieran aprobación basada en políticas o intervención humana.                               |   1   | D/V |
| 7.4.3 | Verifique que las comprobaciones de consistencia cross-modal aseguren que las imágenes, el código y el texto generados para la misma solicitud no puedan usarse para introducir contenido malicioso. |   2   | D/V |
| 7.4.4 | Verifique que la profundidad de delegación de agentes, los límites de recursión y las listas de herramientas permitidas estén configurados explícitamente.                                           |   2   |  D  |
| 7.4.5 | Verifique que la violación de los límites emita eventos de seguridad estructurados para la ingestión en SIEM.                                                                                        |   3   |  V  |

---

## C7.5 Explicabilidad de la salida

Las señales transparentes mejoran la confianza del usuario y la depuración interna.

|   #   | Descripción                                                                                                                                                                 | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.5.1 | Verifique que se muestren las puntuaciones de confianza visibles para el usuario o resúmenes breves de razonamiento cuando la evaluación de riesgos lo considere apropiado. |   2   | D/V |
| 7.5.2 | Verifique que las explicaciones generadas eviten revelar indicaciones del sistema sensibles o datos propietarios.                                                           |   2   | D/V |
| 7.5.3 | Verifique que el sistema capture las probabilidades logarítmicas a nivel de token o los mapas de atención y los almacene para su inspección autorizada.                     |   3   |  D  |
| 7.5.4 | Verifique que los artefactos de explicabilidad estén controlados por versiones junto con las versiones del modelo para garantizar la auditabilidad.                         |   3   |  V  |

---

## C7.6 Integración de Monitoreo

La observabilidad en tiempo real cierra el ciclo entre el desarrollo y la producción.

|   #   | Descripción                                                                                                                                                                                                     | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.6.1 | Verifique que las métricas (violaciones de esquema, tasa de alucinaciones, toxicidad, filtraciones de información personal identificable, latencia, costo) se transmitan a una plataforma central de monitoreo. |   1   |  D  |
| 7.6.2 | Verifique que se definan umbrales de alerta para cada métrica de seguridad, con rutas de escalamiento para el personal de guardia.                                                                              |   1   |  V  |
| 7.6.3 | Verifique que los paneles correlacionen las anomalías de salida con el modelo/versión, la bandera de función y los cambios en los datos ascendentes.                                                            |   2   |  V  |
| 7.6.4 | Verifique que los datos de monitoreo se retroalimenten en el reentrenamiento, ajuste fino o actualizaciones de reglas dentro de un flujo de trabajo de MLOps documentado.                                       |   2   | D/V |
| 7.6.5 | Verifique que las canalizaciones de monitoreo estén sometidas a pruebas de penetración y control de acceso para evitar la filtración de registros sensibles.                                                    |   3   |  V  |

---

## 7.7 Salvaguardias para Medios Generativos

Asegurar que los sistemas de IA no generen contenido mediático ilegal, dañino o no autorizado mediante la aplicación de restricciones de políticas, validación de salida y trazabilidad.

|   #   | Descripción                                                                                                                                                                                                                           | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.7.1 | Verifique que las indicaciones del sistema y las instrucciones al usuario prohíban explícitamente la generación de medios deepfake ilegales, dañinos o no consentidos (por ejemplo, imagen, video, audio).                            |   1   | D/V |
| 7.7.2 | Verifique que las indicaciones sean filtradas para evitar intentos de generar suplantaciones, deepfakes sexualmente explícitos o medios que representen a individuos reales sin su consentimiento.                                    |   2   | D/V |
| 7.7.3 | Verifique que el sistema utilice hash perceptual, detección de marca de agua o huellas digitales para evitar la reproducción no autorizada de medios con derechos de autor.                                                           |   2   |  V  |
| 7.7.4 | Verifique que todos los medios generados estén firmados criptográficamente, marcados con una marca de agua o incorporados con metadatos de procedencia resistentes a manipulaciones para la trazabilidad posterior.                   |   3   | D/V |
| 7.7.5 | Verifique que los intentos de evasión (por ejemplo, ofuscación de indicaciones, jerga, formulaciones adversariales) sean detectados, registrados y limitados en frecuencia; el abuso repetido se informe a los sistemas de monitoreo. |   3   |  V  |

## Referencias

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

