# C7 Comportamiento del modelo, control de salida y garantía de seguridad

## Objetivo de control

Los resultados del modelo deben estar estructurados, ser confiables, seguros, explicables y estar monitoreados de forma continua en producción. Hacerlo reduce las alucinaciones, filtraciones de privacidad, contenido dañino y acciones descontroladas, al tiempo que aumenta la confianza de los usuarios y el cumplimiento regulatorio.

---

## C7.1 Cumplimiento del Formato de Salida

Esquemas estrictos, decodificación restringida y validación posterior evitan que el contenido malformado o malintencionado se propague.

|   #   | Descripción                                                                                                                                                                                                           | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.1.1 | Verifique que los esquemas de respuesta (p. ej., JSON Schema) sean proporcionados en el prompt del sistema y que cada salida se valide automáticamente; las salidas que no cumplan desencadenan reparación o rechazo. |   1   | D/V |
| 7.1.2 | Verifique que la decodificación restringida (tokens de detención, expresión regular, max-tokens) esté habilitada para prevenir desbordamientos o canales laterales de inyección de indicaciones.                      |   1   | D/V |
| 7.1.3 | Verifique que los componentes aguas abajo traten las salidas como no confiables y las validen contra esquemas o deserializadores seguros contra inyección.                                                            |   2   | D/V |
| 7.1.4 | Verifique que los eventos de salida inapropiada estén registrados, tengan limitación de tasa y se expongan al sistema de monitorización.                                                                              |   3   |  V  |

---

## C7.2 Detección y Mitigación de Alucinaciones

La estimación de la incertidumbre y las estrategias de respaldo limitan las respuestas fabricadas.

|   #   | Descripción                                                                                                                                                                                                | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.2.1 | Verifique que las probabilidades logarítmicas por token, la consistencia del ensamble o los detectores de alucinaciones ajustados asignen una puntuación de confianza a cada respuesta.                    |   1   | D/V |
| 7.2.2 | Verifique que las respuestas por debajo de un umbral de confianza configurable activen flujos de trabajo de respaldo (p. ej., generación aumentada por recuperación, modelo secundario o revisión humana). |   1   | D/V |
| 7.2.3 | Verifique que los incidentes de alucinación estén etiquetados con metadatos de causa raíz y se envíen a los flujos de procesamiento de post-mortem y de ajuste fino.                                       |   2   | D/V |
| 7.2.4 | Verifique que los umbrales y los detectores se recalibren después de actualizaciones importantes del modelo o de la base de conocimientos.                                                                 |   3   | D/V |
| 7.2.5 | Verifique que las visualizaciones del tablero monitoreen las tasas de alucinación.                                                                                                                         |   3   |  V  |

---

## C7.3 Filtrado de Seguridad de la Salida y Privacidad

Los filtros de políticas y la cobertura del equipo rojo protegen a los usuarios y a los datos confidenciales.

|   #   | Descripción                                                                                                                                                                                 | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.3.1 | Verifique que los clasificadores pre-generación y post-generación bloqueen contenido de odio, acoso, autolesiones, extremismo y contenido sexualmente explícito de acuerdo con la política. |   1   | D/V |
| 7.3.2 | Verifique que la detección de PII/PCI y la redacción automática se ejecuten en cada respuesta; las violaciones generan un incidente de privacidad.                                          |   1   | D/V |
| 7.3.3 | Verifique que las etiquetas de confidencialidad (por ejemplo, secretos comerciales) se propaguen entre modalidades para evitar filtraciones en texto, imágenes o código.                    |   2   |  D  |
| 7.3.4 | Verifique que los intentos de eludir los filtros o las clasificaciones de alto riesgo exijan aprobación secundaria o reautenticación del usuario.                                           |   3   | D/V |
| 7.3.5 | Verifique que los umbrales de filtrado reflejen las jurisdicciones legales y el contexto de edad y rol del usuario.                                                                         |   3   | D/V |

---

## C7.4 Limitación de salida y acción

Los límites de tasa y las puertas de aprobación previenen abusos y una autonomía excesiva.

|   #   | Descripción                                                                                                                                                                                                    | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.4.1 | Verifique que las cuotas por usuario y por clave API limiten las solicitudes, los tokens y el costo con retroceso exponencial ante errores 429.                                                                |   1   |  D  |
| 7.4.2 | Verifique que las acciones privilegiadas (escrituras de archivos, ejecución de código, llamadas de red) requieren aprobación basada en políticas o humano-en-el-bucle.                                         |   1   | D/V |
| 7.4.3 | Verifique que las comprobaciones de consistencia entre modalidades aseguren que las imágenes, el código y el texto generados para la misma solicitud no puedan utilizarse para introducir contenido malicioso. |   2   | D/V |
| 7.4.4 | Verifique que la profundidad de delegación de agentes, los límites de recursión y las listas de herramientas permitidas estén configurados explícitamente.                                                     |   2   |  D  |
| 7.4.5 | Verifique que la violación de los límites emita eventos de seguridad estructurados para la ingestión en SIEM.                                                                                                  |   3   |  V  |

---

## C7.5 Explicabilidad de la salida

Las señales transparentes mejoran la confianza del usuario y la depuración interna.

|   #   | Descripción                                                                                                                                                             | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.5.1 | Verifique que las puntuaciones de confianza visibles para el usuario o resúmenes breves de razonamiento se muestren cuando la evaluación de riesgos lo estime adecuado. |   2   | D/V |
| 7.5.2 | Verifique que las explicaciones generadas eviten revelar indicaciones del sistema sensibles o datos propietarios.                                                       |   2   | D/V |
| 7.5.3 | Verifique que el sistema capture probabilidades logarítmicas por token o mapas de atención y almacene estos datos para inspección autorizada.                           |   3   |  D  |
| 7.5.4 | Verifique que los artefactos de explicabilidad estén bajo control de versiones junto con los lanzamientos de modelos para garantizar la auditabilidad.                  |   3   |  V  |

---

## C7.6 Integración de monitoreo

La observabilidad en tiempo-real cierra el ciclo entre desarrollo y producción.

|   #   | Descripción                                                                                                                                                                    | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 7.6.1 | Verifique que las métricas (violaciones de esquema, tasa de alucinación, toxicidad, filtraciones de PII, latencia, costo) se transmitan a una plataforma de monitoreo central. |   1   |  D  |
| 7.6.2 | Verifique que se definan umbrales de alerta para cada métrica de seguridad, con rutas de escalamiento en guardia.                                                              |   1   |  V  |
| 7.6.3 | Verifique que los paneles de control correlacionen las anomalías de salida con el modelo / versión, la bandera de características y los cambios en los datos de origen.        |   2   |  V  |
| 7.6.4 | Verifique que los datos de monitoreo retroalimenten el reentrenamiento, el ajuste fino o las actualizaciones de reglas dentro de un flujo de trabajo de MLOps documentado.     |   2   | D/V |
| 7.6.5 | Verifique que los pipelines de monitoreo cuenten con pruebas de penetración y con control de acceso para evitar la filtración de registros sensibles.                          |   3   |  V  |

---

## 7.7 Salvaguardas de Medios Generativos

Asegúrese de que los sistemas de IA no generen contenido multimedia ilegal, dañino o no autorizado mediante la aplicación de restricciones políticas, la validación de resultados y la trazabilidad.

|   #   | Descripción                                                                                                                                                                                                          | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 7.7.1 | Verifique que las indicaciones del sistema y las instrucciones del usuario prohíban explícitamente la generación de medios deepfake ilegales, dañinos o no consensuados (p. ej., imágenes, videos, audios).          |   1   | D/V |
| 7.7.2 | Verifique que las indicaciones estén filtradas para evitar intentos de generar suplantaciones de identidad, deepfakes sexualmente explícitos o medios que representen a personas reales sin su consentimiento.       |   2   | D/V |
| 7.7.3 | Verifique que el sistema utilice hashing perceptual, detección de marcas de agua o fingerprinting de contenido para prevenir la reproducción no autorizada de medios protegidos por derechos de autor.               |   2   |  V  |
| 7.7.4 | Verifique que todos los medios generados estén firmados criptográficamente, cuenten con marca de agua o estén incrustados con metadatos de procedencia a prueba de manipulación para la trazabilidad aguas abajo.    |   3   | D/V |
| 7.7.5 | Verifique que los intentos de eludir (p. ej., ofuscación de indicaciones, jerga, redacción adversarial) sean detectados, registrados y limitados por tasa; el abuso repetido se reporte a los sistemas de monitoreo. |   3   |  V  |

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

