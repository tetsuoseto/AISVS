# C2 Validación de la entrada del usuario

## Objetivo de control

Una validación robusta de la entrada del usuario es una defensa de primera línea contra algunos de los ataques más dañinos en los sistemas de IA. Los ataques de inyección de prompts pueden anular las instrucciones del sistema, filtrar datos sensibles o orientar el modelo hacia un comportamiento que no está permitido. A menos que existan filtros dedicados y jerarquías de instrucciones, la investigación muestra que los "multi-shot" jailbreaks que explotan ventanas de contexto muy largas serán eficaces. Además, ataques sutiles de perturbación adversaria, como intercambios de homógrafos o leetspeak—-pueden cambiar silenciosamente las decisiones de un modelo.

---

## C2.1 Defensa contra la inyección de prompts

La inyección de prompts es uno de los principales riesgos para los sistemas de IA. Las defensas contra esta táctica emplean una combinación de filtros de patrones estáticos, clasificadores dinámicos y el cumplimiento de la jerarquía de instrucciones.

|   #   | Descripción                                                                                                                                                                                                                                                   | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.1.1 | Verifique que las entradas de usuario sean filtradas contra una biblioteca continuamente actualizada de patrones conocidos de inyección de prompt (palabras clave de jailbreak, "ignore previous", cadenas de juego de roles, ataques HTML/URL indirectos).   |   1   | D/V |
| 2.1.2 | Verifique que el sistema aplique una jerarquía de instrucciones en la que los mensajes del sistema o del desarrollador tengan prioridad sobre las instrucciones del usuario, incluso después de la expansión de la ventana de contexto.                       |   1   | D/V |
| 2.1.3 | Verifique que las pruebas de evaluación adversarias (p. ej., indicaciones del Red Team "many-shot") se ejecuten antes de cada lanzamiento de modelo o plantilla de indicaciones, con umbrales de tasa de éxito y bloqueadores automatizados para regresiones. |   2   | D/V |
| 2.1.4 | Verifique que las indicaciones originadas en contenido de terceros (páginas web, PDFs y correos electrónicos) sean sanitizadas en un contexto de análisis aislado antes de ser concatenadas al prompt principal.                                              |   2   |  D  |
| 2.1.5 | Verifique que todas las actualizaciones de las reglas de filtrado de indicaciones, las versiones de modelos de clasificadores y los cambios en las listas de bloqueo estén versionados y sean auditables.                                                     |   3   | D/V |

---

## C2.2 Resistencia a Ejemplos Adversariales

Los modelos de Procesamiento del Lenguaje Natural (PLN) siguen siendo vulnerables a perturbaciones sutiles a nivel de caracteres o de palabras que los humanos suelen pasar por alto, pero los modelos tienden a malclasificar.

|   #   | Descripción                                                                                                                                                                                                                        | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.2.1 | Verifique que los pasos básicos de normalización de entrada (Unicode NFC, mapeo de homógrafos, recorte de espacios en blanco) se ejecuten antes de la tokenización.                                                                |   1   |  D  |
| 2.2.2 | Verifique que la detección de anomalías estadísticas marque entradas con una distancia de edición inusualmente alta respecto a las normas del idioma, tokens repetidos en excesso o distancias de incrustación anómalas.           |   2   | D/V |
| 2.2.3 | Verifique que la canalización de inferencia admita variantes de modelo endurecidas por entrenamiento adversarial opcionales o capas defensivas (p. ej., aleatorización, destilación defensiva) para puntos finales de alto riesgo. |   2   |  D  |
| 2.2.4 | Verificar que las entradas adversarias sospechosas estén en cuarentena y se registren con las cargas útiles completas (después de la anonimización de PII).                                                                        |   2   |  V  |
| 2.2.5 | Verifique que las métricas de robustez (tasa de éxito de conjuntos de ataques conocidos) se rastreen a lo largo del tiempo y que las regresiones activen un bloqueo de lanzamiento.                                                |   3   | D/V |

---

## C2.3 Validación de Esquema, Tipo y Longitud

Los ataques de IA que presentan entradas mal formateadas o de gran tamaño pueden provocar errores de análisis, desbordamiento del prompt entre campos y agotamiento de recursos.  El cumplimiento estricto de un esquema también es un requisito previo al realizar llamadas deterministas a herramientas.

|   #   | Descripción                                                                                                                                                                                                                 | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.3.1 | Verifique que cada punto final de API o de llamada a función defina un esquema de entrada explícito (JSON Schema, Protobuf o su equivalente multimodal) y que las entradas estén validadas antes del ensamblaje del prompt. |   1   |  D  |
| 2.3.2 | Verifique que las entradas que excedan los límites máximos de tokens o bytes sean rechazadas con un error seguro y que nunca se trunquen silenciosamente.                                                                   |   1   | D/V |
| 2.3.3 | Verifique que las comprobaciones de tipo (p. ej., rangos numéricos, valores enum, tipos MIME para imágenes y audio) se apliquen en el servidor, y no solo en el código del cliente.                                         |   2   | D/V |
| 2.3.4 | Verifique que los validadores semánticos (p. ej., JSON Schema) se ejecuten en tiempo constante para evitar un DoS algorítmico.                                                                                              |   2   |  D  |
| 2.3.5 | Verifique que las fallas de validación se registren con fragmentos de la carga útil redactados y códigos de error inequívocos para facilitar la priorización de incidentes de seguridad.                                    |   3   |  V  |

---

## C2.4 Cribado de Contenido y Políticas

Los desarrolladores deben poder detectar indicaciones sintácticamente válidas que soliciten contenido prohibido (como instrucciones ilícitas, discurso de odio y texto protegido por derechos de autor) y luego evitar que se propaguen.

|   #   | Descripción                                                                                                                                                                                                          | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.4.1 | Verifique que un clasificador de contenido (zero-shot o fine-tuned) asigne puntuaciones a cada entrada en cuanto a violencia, autolesión, odio, contenido sexual y solicitudes ilegales, con umbrales configurables. |   1   |  D  |
| 2.4.2 | Verifique que las entradas que violen las políticas reciban rechazos estandarizados o respuestas seguras, para que no se propaguen a llamadas posteriores del LLM.                                                   |   1   | D/V |
| 2.4.3 | Verifique que el modelo de filtrado o el conjunto de reglas sea reentrenado/actualizado al menos cada trimestre, incorporando patrones de jailbreak o de elusión de políticas observados recientemente.              |   2   |  D  |
| 2.4.4 | Verificar que el filtrado respete las políticas específicas del usuario (edad, restricciones legales regionales) mediante reglas basadas en atributos resueltas en el momento de la solicitud.                       |   2   |  D  |
| 2.4.5 | Verifique que los registros de cribado incluyan puntuaciones de confianza del clasificador y etiquetas de categorías de políticas para la correlación con SOC y la repetición futura por el equipo rojo.             |   3   |  V  |

---

## C2.5 Limitación de la tasa de entrada y prevención de abusos

Los desarrolladores deben prevenir abusos, agotamiento de recursos y ataques automatizados contra sistemas de IA limitando las tasas de entrada y detectando patrones de uso anómalos.

|   #   | Descripción                                                                                                                                         | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.5.1 | Verifique que se apliquen límites de tasa por usuario, por IP y por clave API para todos los puntos de entrada.                                     |   1   | D/V |
| 2.5.2 | Verifique que los límites de tasa de ráfaga y de tasa sostenida estén ajustados para prevenir ataques de DoS y de fuerza bruta.                     |   2   | D/V |
| 2.5.3 | Verifique que los patrones de uso anómalos (por ejemplo, solicitudes en ráfaga, inundación de entradas) activen bloqueos automatizados o escaladas. |   2   | D/V |
| 2.5.4 | Verifique que los registros de prevención de abusos se mantengan y se revisen para detectar patrones de ataque emergentes.                          |   3   |  V  |

---

## C2.6 Validación de entradas multimodales

Los sistemas de IA deben incluir una validación robusta para entradas no textuales (imágenes, audio, archivos) para prevenir la inyección, la evasión o el abuso de recursos.

|   #   | Descripción                                                                                                                               | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.6.1 | Verifique que todas las entradas no textuales (imágenes, audio, archivos) sean validadas por tipo, tamaño y formato antes de procesarlas. |   1   |  D  |
| 2.6.2 | Verifique que los archivos sean escaneados en busca de malware y de cargas útiles esteganográficas antes de la ingestión.                 |   2   | D/V |
| 2.6.3 | Verifique que las entradas de imagen y de audio se revisen en busca de perturbaciones adversarias o patrones de ataque conocidos.         |   2   | D/V |
| 2.6.4 | Verifique que las fallas de validación de entradas multimodales se registren y que se activen alertas para la investigación.              |   3   |  V  |

---

## C2.7 Procedencia de la entrada y atribución

Los sistemas de IA deben apoyar la auditoría, el seguimiento de abusos y el cumplimiento mediante la supervisión y el etiquetado de los orígenes de todas las entradas de usuario.

|   #   | Descripción                                                                                                                                                     | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.7.1 | Verifique que todas las entradas de usuario estén etiquetadas con metadatos (ID de usuario, sesión, fuente, marca temporal, dirección IP) durante la ingestión. |   1   | D/V |
| 2.7.2 | Verifique que los metadatos de procedencia se conserven y sean auditables para todas las entradas procesadas.                                                   |   2   | D/V |
| 2.7.3 | Verifique que las fuentes de entrada anómalas o no confiables sean marcadas y estén sujetas a un escrutinio más riguroso o a un bloqueo.                        |   2   | D/V |

---

## C2.8 Detección adaptativa de amenazas en tiempo real

Los desarrolladores deberían emplear sistemas avanzados de detección de amenazas para IA que se adapten a nuevos patrones de ataque y proporcionen protección en tiempo real mediante coincidencia de patrones compilados.

|   #   | Descripción                                                                                                                                                                                                                      | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.8.1 | Verifique que los patrones de detección de amenazas se compilen en motores de expresiones regulares optimizados para un filtrado en tiempo real de alto rendimiento con un impacto de latencia mínimo.                           |   1   | D/V |
| 2.8.2 | Verifique que los sistemas de detección de amenazas mantengan bibliotecas de patrones separadas para diferentes categorías de amenazas (inyección de indicaciones, contenido dañino, datos sensibles, comandos del sistema).     |   1   | D/V |
| 2.8.3 | Verifique que la detección adaptativa de amenazas incorpore modelos de aprendizaje automático que actualicen la sensibilidad ante amenazas basándose en la frecuencia de ataques y las tasas de éxito.                           |   2   | D/V |
| 2.8.4 | Verifique que las fuentes de inteligencia de amenazas en tiempo real actualicen automáticamente las bibliotecas de patrones con nuevas firmas de ataque e IOCs (Indicadores de Compromiso).                                      |   2   | D/V |
| 2.8.5 | Verifique que las tasas de falsos positivos en la detección de amenazas se supervisen continuamente y que la especificidad de los patrones se ajuste automáticamente para minimizar la interferencia con casos de uso legítimos. |   3   | D/V |
| 2.8.6 | Verifique que el análisis contextual de amenazas considere la fuente de entrada, los patrones de comportamiento del usuario y el historial de la sesión para mejorar la precisión de la detección.                               |   3   | D/V |
| 2.8.7 | Verifique que las métricas de rendimiento de la detección de amenazas (tasa de detección, latencia de procesamiento, utilización de recursos) sean monitoreadas y optimizadas en tiempo real.                                    |   3   | D/V |

---

## C2.9 Pipeline de validación de seguridad Multi-Modal

Los desarrolladores deben proporcionar validación de seguridad para texto, imágenes, audio y otras modalidades de entrada de IA con tipos específicos de detección de amenazas y aislamiento de recursos.

|   #   | Descripción                                                                                                                                                                                                                                                                                                         | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.9.1 | Verifique que cada modalidad de entrada cuente con validadores de seguridad dedicados con patrones de amenazas documentados (texto: inyección de prompts, imágenes: esteganografía, audio: ataques de espectrograma) y umbrales de detección.                                                                       |   1   | D/V |
| 2.9.2 | Verifique que las entradas multimodales se procesen en entornos aislados con límites de recursos definidos (memoria, CPU, tiempo de procesamiento) específicos para cada tipo de modalidad y que estén documentados en las políticas de seguridad.                                                                  |   2   | D/V |
| 2.9.3 | Verifique que la detección de ataques multimodales identifique ataques coordinados que abarcan múltiples tipos de entrada (p. ej., cargas útiles esteganográficas en imágenes combinadas con inyección de indicaciones en texto) mediante reglas de correlación y generación de alertas.                            |   2   | D/V |
| 2.9.4 | Verifique que los fallos de validación multimodales activen un registro detallado que incluya todas las modalidades de entrada, los resultados de validación, los puntajes de amenaza y el análisis de correlación, con formatos de registro estructurados para la integración con SIEM.                            |   3   | D/V |
| 2.9.5 | Verifique que los clasificadores de contenido específicos de cada modalidad se actualicen de acuerdo con cronogramas documentados (como mínimo trimestral) con nuevos patrones de amenazas, ejemplos adversariales y puntos de referencia de rendimiento que se mantengan por encima de los umbrales de referencia. |   3   | D/V |

---

## Referencias

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

