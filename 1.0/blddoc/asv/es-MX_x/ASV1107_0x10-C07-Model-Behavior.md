# Comportamiento del Modelo C7, Control de Salida y Garantía de Seguridad

## Objetivo de Control

Los resultados del modelo deben ser estructurados, fiables, seguros, explicables y monitorizados continuamente en producción. Hacer esto reduce las alucinaciones, las filtraciones de privacidad, el contenido dañino y las acciones descontroladas, mientras aumenta la confianza del usuario y el cumplimiento normativo.

---

## C7.1 Aplicación estricta del formato de salida

Esquemas estrictos, decodificación restringida y validación posterior detienen el contenido malformado o malicioso antes de que se propague.

|   #   | Descripción                                                                                                                                                                                                                                | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 7.1.1 | Verifique que los esquemas de respuesta (por ejemplo, JSON Schema) se proporcionen en el mensaje del sistema y que cada salida se valide automáticamente; las salidas que no cumplan con el esquema desencadenan una reparación o rechazo. |   1   | D/V |
| 7.1.2 | Verifique que la decodificación limitada (tokens de parada, expresiones regulares, máximo de tokens) esté habilitada para prevenir desbordamientos o canales secundarios de inyección en el prompt.                                        |   1   | D/V |
| 7.1.3 | Verifique que los componentes descendentes traten las salidas como no confiables y las validen contra esquemas o deserializadores seguros contra inyecciones.                                                                              |   2   | D/V |
| 7.1.4 | Verifique que los eventos de salida incorrecta estén registrados, limitados en tasa y visibles para la monitorización.                                                                                                                     |   3   |  V  |

---

## C7.2 Detección y Mitigación de Alucinaciones

La estimación de la incertidumbre y las estrategias de respaldo limitan las respuestas fabricadas.

|   #   | Descripción                                                                                                                                                                                                     | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.2.1 | Verifique que las probabilidades logarítmicas a nivel de token, la auto-consistencia del conjunto o los detectores de alucinaciones ajustados asignen una puntuación de confianza a cada respuesta.             |   1   | D/V |
| 7.2.2 | Verifique que las respuestas por debajo de un umbral de confianza configurable activen flujos de trabajo de respaldo (por ejemplo, generación aumentada por recuperación, modelo secundario o revisión humana). |   1   | D/V |
| 7.2.3 | Verifique que los incidentes de alucinación estén etiquetados con metadatos de causa raíz y se envíen a los procesos de análisis post-mortem y afinamiento.                                                     |   2   | D/V |
| 7.2.4 | Verifique que los umbrales y detectores se recalibran después de actualizaciones importantes del modelo o de la base de conocimientos.                                                                          |   3   | D/V |
| 7.2.5 | Verifique que las visualizaciones del panel rastreen las tasas de alucinaciones.                                                                                                                                |   3   |  V  |

---

## C7.3 Filtrado de Seguridad y Privacidad de Salida

Los filtros de políticas y la cobertura del equipo rojo protegen a los usuarios y los datos confidenciales.

|   #   | Descripción                                                                                                                                                                          | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 7.3.1 | Verifique que los clasificadores previos y posteriores a la generación bloqueen contenido de odio, acoso, autolesiones, extremista y sexualmente explícito alineado con la política. |   1   | D/V |
| 7.3.2 | Verifique que la detección de PII/PCI y la redacción automática se ejecuten en cada respuesta; las violaciones generan un incidente de privacidad.                                   |   1   | D/V |
| 7.3.3 | Verifique que las etiquetas de confidencialidad (por ejemplo, secretos comerciales) se propaguen a través de modalidades para evitar fugas en texto, imágenes o código.              |   2   |  D  |
| 7.3.4 | Verifique que los intentos de eludir filtros o las clasificaciones de alto riesgo requieran una aprobación secundaria o la reautenticación del usuario.                              |   3   | D/V |
| 7.3.5 | Verifique que los umbrales de filtrado reflejen las jurisdicciones legales y el contexto de edad/rol del usuario.                                                                    |   3   | D/V |

---

## C7.4 Limitación de Salida y Acción

Los límites de tasa y las puertas de aprobación evitan el abuso y la autonomía excesiva.

|   #   | Descripción                                                                                                                                                                                              | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.4.1 | Verifique que las cuotas por usuario y por clave API limiten las solicitudes, tokens y costos con retroceso exponencial en errores 429.                                                                  |   1   |  D  |
| 7.4.2 | Verifique que las acciones privilegiadas (escrituras en archivos, ejecución de código, llamadas a la red) requieran aprobación basada en políticas o intervención humana.                                |   1   | D/V |
| 7.4.3 | Verifique que las comprobaciones de consistencia cross-modal aseguren que las imágenes, el código y el texto generados para la misma solicitud no puedan ser usados para introducir contenido malicioso. |   2   | D/V |
| 7.4.4 | Verifique que la profundidad de delegación de agentes, los límites de recursión y las listas de herramientas permitidas estén configurados explícitamente.                                               |   2   |  D  |
| 7.4.5 | Verifique que la violación de límites emita eventos de seguridad estructurados para la ingestión en SIEM.                                                                                                |   3   |  V  |

---

## C7.5 Explicabilidad de la salida

Las señales transparentes mejoran la confianza del usuario y la depuración interna.

|   #   | Descripción                                                                                                                                                                | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.5.1 | Verifique que se expongan las puntuaciones de confianza visibles para el usuario o resúmenes breves de razonamiento cuando la evaluación de riesgo lo considere apropiado. |   2   | D/V |
| 7.5.2 | Verifique que las explicaciones generadas eviten revelar indicaciones del sistema sensibles o datos propietarios.                                                          |   2   | D/V |
| 7.5.3 | Verifique que el sistema capture las log-probabilidades a nivel de token o mapas de atención y las almacene para inspección autorizada.                                    |   3   |  D  |
| 7.5.4 | Verifique que los artefactos de explicabilidad estén controlados por versiones junto con las versiones del modelo para garantizar la auditabilidad.                        |   3   |  V  |

---

## C7.6 Integración de Monitoreo

La observabilidad en tiempo real cierra el ciclo entre el desarrollo y la producción.

|   #   | Descripción                                                                                                                                                                                           | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.6.1 | Verifique que las métricas (violaciones del esquema, tasa de alucinaciones, toxicidad, fugas de información personal identificable, latencia, costo) se envíen a una plataforma central de monitoreo. |   1   |  D  |
| 7.6.2 | Verifique que se definan los umbrales de alerta para cada métrica de seguridad, con rutas de escalamiento para el personal de guardia.                                                                |   1   |  V  |
| 7.6.3 | Verifique que los paneles correlacionen las anomalías de salida con el modelo/versión, la bandera de característica y los cambios en los datos ascendentes.                                           |   2   |  V  |
| 7.6.4 | Verifique que los datos de monitoreo retroalimenten el reentrenamiento, la afinación o la actualización de reglas dentro de un flujo de trabajo MLOps documentado.                                    |   2   | D/V |
| 7.6.5 | Verifique que las canalizaciones de monitoreo sean sometidas a pruebas de penetración y tengan control de acceso para evitar la filtración de registros sensibles.                                    |   3   |  V  |

---

## 7.7 Salvaguardas para Medios Generativos

Asegurar que los sistemas de IA no generen contenido multimedia ilegal, perjudicial o no autorizado mediante la aplicación de restricciones de políticas, validación de resultados y trazabilidad.

|   #   | Descripción                                                                                                                                                                                                                      | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.7.1 | Verifique que las indicaciones del sistema y las instrucciones para el usuario prohíban explícitamente la generación de medios deepfake ilegales, dañinos o no consensuados (por ejemplo, imagen, video, audio).                 |   1   | D/V |
| 7.7.2 | Verifique que las indicaciones sean filtradas para detectar intentos de generar suplantaciones, falsificaciones profundas sexuales explícitas o medios que representen a personas reales sin consentimiento.                     |   2   | D/V |
| 7.7.3 | Verifique que el sistema utilice hashing perceptual, detección de marcas de agua o huellas digitales para prevenir la reproducción no autorizada de medios protegidos por derechos de autor.                                     |   2   |  V  |
| 7.7.4 | Verifique que todos los medios generados estén firmados criptográficamente, con marcas de agua o integrados con metadatos de procedencia resistentes a la manipulación para la trazabilidad posterior.                           |   3   | D/V |
| 7.7.5 | Verifique que los intentos de elusión (por ejemplo, ofuscación de indicaciones, jerga, formulación adversaria) sean detectados, registrados y limitados en frecuencia; el abuso repetido se reporte a los sistemas de monitoreo. |   3   |  V  |

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

