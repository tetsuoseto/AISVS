# Validación de entrada del usuario C2

## Objetivo de Control

La validación robusta de la entrada del usuario es una defensa de primera línea contra algunos de los ataques más dañinos en los sistemas de IA. Los ataques de inyección de indicaciones pueden anular las instrucciones del sistema, filtrar datos sensibles o dirigir el modelo hacia comportamientos no permitidos. A menos que estén en su lugar filtros dedicados y jerarquías de instrucciones, la investigación demuestra que las "evasiones multi-disparo" que explotan ventanas de contexto muy largas serán efectivas. Además, ataques sutiles de perturbación adversarial—como los intercambios de homoglifos o leetspeak—pueden cambiar silenciosamente las decisiones de un modelo.

---

## C2.1 Defensa contra la Inyección de Prompts

La inyección de indicaciones es uno de los principales riesgos para los sistemas de IA. Las defensas contra esta táctica emplean una combinación de filtros de patrones estáticos, clasificadores dinámicos y aplicación de jerarquía de instrucciones.

|   #   | Descripción                                                                                                                                                                                                                                                               | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.1.1 | Verifique que las entradas de los usuarios se filtren contra una biblioteca actualizada continuamente de patrones conocidos de inyección de indicaciones (palabras clave de jailbreak, "ignorar lo anterior", cadenas de juego de roles, ataques indirectos de HTML/URL). |   1   | D/V |
| 2.1.2 | Verifique que el sistema aplica una jerarquía de instrucciones en la que los mensajes del sistema o del desarrollador prevalecen sobre las instrucciones del usuario, incluso después de la expansión de la ventana de contexto.                                          |   1   | D/V |
| 2.1.3 | Verifique que las pruebas de evaluación adversarial (por ejemplo, indicaciones "many-shot" del Red Team) se realicen antes de cada lanzamiento de modelo o plantilla de indicación, con umbrales de tasa de éxito y bloqueadores automáticos para regresiones.            |   2   | D/V |
| 2.1.4 | Verifique que los prompts provenientes de contenido de terceros (páginas web, PDFs, correos electrónicos) sean depurados en un contexto de análisis aislado antes de ser concatenados en el prompt principal.                                                             |   2   |  D  |
| 2.1.5 | Verifique que todas las actualizaciones de reglas de filtro de indicaciones, las versiones de los modelos clasificadores y los cambios en la lista de bloqueo estén controlados por versiones y sean auditables.                                                          |   3   | D/V |

---

## C2.2 Resistencia a Ejemplos Adversariales

Los modelos de Procesamiento del Lenguaje Natural (PLN) todavía son vulnerables a perturbaciones sutiles a nivel de caracteres o palabras que los humanos suelen pasar por alto pero que los modelos tienden a clasificar incorrectamente.

|   #   | Descripción                                                                                                                                                                                                                          | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 2.2.1 | Verifique que los pasos básicos de normalización de entrada (Unicode NFC, mapeo de homógrafos, recorte de espacios en blanco) se ejecuten antes de la tokenización.                                                                  |   1   |  D  |
| 2.2.2 | Verifique que la detección estadística de anomalías señale entradas con una distancia de edición inusualmente alta con respecto a las normas del lenguaje, tokens repetidos en exceso o distancias anómalas en los embeddings.       |   2   | D/V |
| 2.2.3 | Verifique que la canalización de inferencia soporte variantes de modelos endurecidos opcionales por entrenamiento adversarial o capas de defensa (p. ej., aleatorización, destilación defensiva) para puntos finales de alto riesgo. |   2   |  D  |
| 2.2.4 | Verifique que las entradas adversarias sospechosas estén en cuarentena, registradas con cargas completas (después de la redacción de PII).                                                                                           |   2   |  V  |
| 2.2.5 | Verifique que las métricas de robustez (tasa de éxito de conjuntos de ataques conocidos) se rastreen a lo largo del tiempo y que las regresiones activen un bloqueo de lanzamiento.                                                  |   3   | D/V |

---

## C2.3 Validación de Esquema, Tipo y Longitud

Los ataques de IA que presentan entradas malformadas o sobredimensionadas pueden causar errores de análisis, desbordamiento de indicaciones entre campos y agotamiento de recursos. La aplicación estricta del esquema también es un requisito previo al realizar llamadas a herramientas deterministas.

|   #   | Descripción                                                                                                                                                                                                      | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.3.1 | Verifique que cada punto final de llamada a API o función defina un esquema de entrada explícito (JSON Schema, Protobuf o equivalente multimodal) y que las entradas se validen antes del ensamblaje del prompt. |   1   |  D  |
| 2.3.2 | Verifique que las entradas que superan el límite máximo de tokens o bytes sean rechazadas con un error seguro y nunca se trunquen silenciosamente.                                                               |   1   | D/V |
| 2.3.3 | Verifique que las comprobaciones de tipo (por ejemplo, rangos numéricos, valores enum, tipos MIME para imágenes/audio) se apliquen del lado del servidor, no solo en el código del cliente.                      |   2   | D/V |
| 2.3.4 | Verificar que los validadores semánticos (por ejemplo, JSON Schema) se ejecuten en tiempo constante para prevenir ataques DoS algorítmicos.                                                                      |   2   |  D  |
| 2.3.5 | Verifique que los fallos de validación se registren con fragmentos de carga útil redactados y códigos de error inequívocos para facilitar la clasificación de seguridad.                                         |   3   |  V  |

---

## C2.4 Revisión de Contenido y Políticas

Los desarrolladores deberían poder detectar indicaciones sintácticamente válidas que soliciten contenido no permitido (como instrucciones ilícitas, discurso de odio y texto con derechos de autor) y luego evitar que se propaguen.

|   #   | Descripción                                                                                                                                                                                                   | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.4.1 | Verifique que un clasificador de contenido (sin entrenamiento previo o ajustado) evalúe cada entrada para violencia, autolesiones, odio, contenido sexual y solicitudes ilegales, con umbrales configurables. |   1   |  D  |
| 2.4.2 | Verifique que las entradas que violen las políticas reciban rechazos estandarizados o cumplimientos seguros para que no se propaguen a llamadas posteriores de modelos de lenguaje grandes (LLM).             |   1   | D/V |
| 2.4.3 | Verifique que el modelo de filtrado o el conjunto de reglas se reentrene/actualice al menos trimestralmente, incorporando los patrones recién observados de jailbreak o evasión de políticas.                 |   2   |  D  |
| 2.4.4 | Verifique que el filtrado respete las políticas específicas del usuario (edad, restricciones legales regionales) mediante reglas basadas en atributos resueltas en el momento de la solicitud.                |   2   |  D  |
| 2.4.5 | Verifique que los registros de filtrado incluyan puntajes de confianza del clasificador y etiquetas de categoría de política para la correlación SOC y la reproducción futura de red team.                    |   3   |  V  |

---

## C2.5 Limitación de la Tasa de Entrada y Prevención de Abuso

Los desarrolladores deben prevenir el abuso, el agotamiento de recursos y los ataques automatizados contra los sistemas de IA limitando las tasas de entrada y detectando patrones de uso anómalos.

|   #   | Descripción                                                                                                                                          | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.5.1 | Verifique que los límites de velocidad por usuario, por IP y por clave API se apliquen para todos los puntos finales de entrada.                     |   1   | D/V |
| 2.5.2 | Verifique que los límites de velocidad de ráfaga y sostenidos estén ajustados para prevenir ataques DoS y de fuerza bruta.                           |   2   | D/V |
| 2.5.3 | Verifique que los patrones de uso anómalos (por ejemplo, solicitudes rápidas, inundación de entradas) desencadenen bloqueos o escaladas automáticas. |   2   | D/V |
| 2.5.4 | Verifique que los registros de prevención de abusos se conserven y revisen para detectar patrones de ataque emergentes.                              |   3   |  V  |

---

## C2.6 Validación de Entrada Multimodal

Los sistemas de IA deben incluir una validación robusta para entradas no textuales (imágenes, audio, archivos) para prevenir inyecciones, evasiones o abusos de recursos.

|   #   | Descripción                                                                                                                                    | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.6.1 | Verifique que todas las entradas no textuales (imágenes, audio, archivos) sean validadas por tipo, tamaño y formato antes de su procesamiento. |   1   |  D  |
| 2.6.2 | Verifique que los archivos se escaneen en busca de malware y cargas útiles esteganográficas antes de su ingestión.                             |   2   | D/V |
| 2.6.3 | Verifique que las entradas de imagen/audio sean revisadas para detectar perturbaciones adversariales o patrones de ataque conocidos.           |   2   | D/V |
| 2.6.4 | Verifique que las fallas de validación de entrada multimodal se registren y generen alertas para su investigación.                             |   3   |  V  |

---

## C2.7 Procedencia y Atribución de la Entrada

Los sistemas de IA deben apoyar la auditoría, el seguimiento de abusos y el cumplimiento mediante la supervisión y el etiquetado de los orígenes de todas las entradas de usuario.

|   #   | Descripción                                                                                                                                                           | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.7.1 | Verifique que todas las entradas de usuario estén etiquetadas con metadatos (ID de usuario, sesión, origen, marca temporal, dirección IP) al momento de la ingestión. |   1   | D/V |
| 2.7.2 | Verifique que los metadatos de procedencia se conserven y sean auditables para todas las entradas procesadas.                                                         |   2   | D/V |
| 2.7.3 | Verifique que las fuentes de entrada anómalas o no confiables sean señaladas y estén sujetas a un escrutinio o bloqueo mejorado.                                      |   2   | D/V |

---

## C2.8 Detección Adaptativa de Amenazas en Tiempo Real

Los desarrolladores deben emplear sistemas avanzados de detección de amenazas para IA que se adapten a nuevos patrones de ataque y proporcionen protección en tiempo real mediante la coincidencia de patrones compilados.

|   #   | Descripción                                                                                                                                                                                                                    | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 2.8.1 | Verifique que los patrones de detección de amenazas estén compilados en motores de expresiones regulares optimizados para un filtrado en tiempo real de alto rendimiento con un impacto mínimo en la latencia.                 |   1   | D/V |
| 2.8.2 | Verifique que los sistemas de detección de amenazas mantengan bibliotecas de patrones separadas para diferentes categorías de amenazas (inyección de comandos, contenido dañino, datos sensibles, comandos del sistema).       |   1   | D/V |
| 2.8.3 | Verifique que la detección adaptativa de amenazas incorpore modelos de aprendizaje automático que actualicen la sensibilidad a las amenazas en función de la frecuencia de ataques y las tasas de éxito.                       |   2   | D/V |
| 2.8.4 | Verifique que las fuentes de inteligencia de amenazas en tiempo real actualicen automáticamente las bibliotecas de patrones con nuevas firmas de ataque e IOCs (Indicadores de Compromiso).                                    |   2   | D/V |
| 2.8.5 | Verifique que las tasas de falsos positivos en la detección de amenazas se supervisen continuamente y que la especificidad del patrón se ajuste automáticamente para minimizar la interferencia en los casos de uso legítimos. |   3   | D/V |
| 2.8.6 | Verifique que el análisis contextual de amenazas considere la fuente de entrada, los patrones de comportamiento del usuario y el historial de la sesión para mejorar la precisión de la detección.                             |   3   | D/V |
| 2.8.7 | Verifique que las métricas de rendimiento de detección de amenazas (tasa de detección, latencia de procesamiento, utilización de recursos) se monitoreen y optimicen en tiempo real.                                           |   3   | D/V |

---

## C2.9 Pipeline de Validación de Seguridad Multi-Modal

Los desarrolladores deben proporcionar validación de seguridad para texto, imagen, audio y otras modalidades de entrada de IA con tipos específicos de detección de amenazas y aislamiento de recursos.

|   #   | Descripción                                                                                                                                                                                                                                                                                           | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.9.1 | Verifique que cada modalidad de entrada tenga validadores de seguridad dedicados con patrones de amenazas documentados (texto: inyección de comandos, imágenes: esteganografía, audio: ataques de espectrograma) y umbrales de detección.                                                             |   1   | D/V |
| 2.9.2 | Verifique que las entradas multimodales se procesen en entornos aislados con límites de recursos definidos (memoria, CPU, tiempo de procesamiento) específicos para cada tipo de modalidad y documentados en las políticas de seguridad.                                                              |   2   | D/V |
| 2.9.3 | Verifique que la detección de ataques cruzados modales identifique ataques coordinados que abarcan múltiples tipos de entradas (por ejemplo, cargas útiles esteganográficas en imágenes combinadas con inyección de indicaciones en texto) mediante reglas de correlación y generación de alertas.    |   2   | D/V |
| 2.9.4 | Verifique que las fallas de validación multimodal desencadenen un registro detallado que incluya todas las modalidades de entrada, resultados de la validación, puntajes de amenaza y análisis de correlación con formatos de registro estructurados para la integración con SIEM.                    |   3   | D/V |
| 2.9.5 | Verificar que los clasificadores de contenido específicos de modalidad se actualicen según los cronogramas documentados (mínimo trimestralmente) con nuevos patrones de amenazas, ejemplos adversarios y que los puntos de referencia de rendimiento se mantengan por encima de los umbrales básicos. |   3   | D/V |

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

