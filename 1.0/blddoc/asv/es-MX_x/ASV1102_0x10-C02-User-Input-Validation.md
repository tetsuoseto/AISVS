# Validación de Entrada de Usuario C2

## Objetivo de Control

La validación robusta de la entrada del usuario es una defensa de primera línea contra algunos de los ataques más dañinos a los sistemas de IA. Los ataques de inyección de instrucciones pueden anular las instrucciones del sistema, filtrar datos sensibles o dirigir el modelo hacia un comportamiento no permitido. A menos que existan filtros dedicados y jerarquías de instrucciones, la investigación muestra que los "multi-shot" jailbreaks que explotan ventanas de contexto muy largas serán efectivos. Además, ataques sutiles de perturbación adversaria —como intercambios de homógrafos o leetspeak— pueden cambiar silenciosamente las decisiones de un modelo.

---

## C2.1 Defensa contra la Inyección de Prompts

La inyección de prompt es uno de los principales riesgos para los sistemas de IA. Las defensas contra esta táctica emplean una combinación de filtros de patrones estáticos, clasificadores dinámicos y aplicación de la jerarquía de instrucciones.

|   #   | Descripción                                                                                                                                                                                                                                                           | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.1.1 | Verificar que las entradas del usuario sean filtradas contra una biblioteca actualizada continuamente de patrones conocidos de inyección de prompts (palabras clave de jailbreak, "ignorar lo anterior", cadenas de juegos de roles, ataques indirectos de HTML/URL). |   1   | D/V |
| 2.1.2 | Verifique que el sistema aplique una jerarquía de instrucciones en la que los mensajes del sistema o del desarrollador prevalezcan sobre las instrucciones del usuario, incluso después de la expansión de la ventana de contexto.                                    |   1   | D/V |
| 2.1.3 | Verifique que las pruebas de evaluación adversarial (por ejemplo, los "prompts" de Red Team de "many-shot") se realicen antes de cada lanzamiento de modelo o plantilla de prompt, con umbrales de tasa de éxito y bloqueadores automáticos para regresiones.         |   2   | D/V |
| 2.1.4 | Verifique que las indicaciones que provienen de contenido de terceros (páginas web, PDF, correos electrónicos) sean depuradas en un contexto de análisis aislado antes de ser concatenadas en la indicación principal.                                                |   2   |  D  |
| 2.1.5 | Verifique que todas las actualizaciones de las reglas de filtro de indicaciones, las versiones de los modelos clasificadores y los cambios en las listas de bloqueo estén controlados por versiones y sean auditables.                                                |   3   | D/V |

---

## C2.2 Resistencia a Ejemplos Adversarios

Los modelos de Procesamiento de Lenguaje Natural (NLP) siguen siendo vulnerables a perturbaciones sutiles a nivel de caracteres o palabras que los humanos a menudo pasan por alto, pero que los modelos tienden a clasificar incorrectamente.

|   #   | Descripción                                                                                                                                                                                                                                               | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.2.1 | Verifique que los pasos básicos de normalización de entrada (Unicode NFC, mapeo de homoglifos, recorte de espacios en blanco) se ejecuten antes de la tokenización.                                                                                       |   1   |  D  |
| 2.2.2 | Verifique que la detección de anomalías estadísticas identifique entradas con una distancia de edición inusualmente alta respecto a las normas del lenguaje, tokens repetidos en exceso o distancias anormales en las incrustaciones.                     |   2   | D/V |
| 2.2.3 | Verifique que la canalización de inferencia sea compatible con variantes opcionales de modelos endurecidos mediante entrenamiento adversarial o capas de defensa (por ejemplo, aleatorización, destilación defensiva) para puntos finales de alto riesgo. |   2   |  D  |
| 2.2.4 | Verifique que las entradas adversarias sospechosas estén en cuarentena, registradas con cargas completas (después de la redacción de la información de identificación personal).                                                                          |   2   |  V  |
| 2.2.5 | Verifique que las métricas de robustez (tasa de éxito de conjuntos de ataques conocidos) se registren a lo largo del tiempo y que las regresiones activen un bloqueo de lanzamiento.                                                                      |   3   | D/V |

---

## C2.3 Validación de Esquema, Tipo y Longitud

Los ataques de IA que presentan entradas malformadas o sobredimensionadas pueden causar errores de análisis, derrame de indicaciones entre campos y agotamiento de recursos. La aplicación estricta de esquemas también es un requisito previo al realizar llamadas a herramientas deterministas.

|   #   | Descripción                                                                                                                                                                                                   | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.3.1 | Verifique que cada endpoint de llamada a API o función defina un esquema de entrada explícito (JSON Schema, Protobuf o equivalente multimodal) y que las entradas se validen antes del ensamblaje del prompt. |   1   |  D  |
| 2.3.2 | Verifique que las entradas que superan los límites máximos de tokens o bytes sean rechazadas con un error seguro y nunca se trunquen silenciosamente.                                                         |   1   | D/V |
| 2.3.3 | Verifique que las comprobaciones de tipo (por ejemplo, rangos numéricos, valores enumerados, tipos MIME para imágenes/audio) se apliquen en el servidor, no solo en el código del cliente.                    |   2   | D/V |
| 2.3.4 | Verifique que los validadores semánticos (por ejemplo, JSON Schema) se ejecuten en tiempo constante para prevenir ataques de denegación de servicio algorítmica (DoS).                                        |   2   |  D  |
| 2.3.5 | Verifique que los fallos de validación se registren con fragmentos de carga útil redactedos y códigos de error inequívocos para ayudar en la clasificación de seguridad.                                      |   3   |  V  |

---

## C2.4 Revisión de Contenido y Políticas

Los desarrolladores deberían poder detectar indicaciones sintácticamente válidas que soliciten contenido no permitido (como instrucciones ilícitas, discursos de odio y texto protegido por derechos de autor) y luego evitar que se propaguen.

|   #   | Descripción                                                                                                                                                                                                            | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.4.1 | Verifique que un clasificador de contenido (de cero disparos o ajustado finamente) evalúe cada entrada en cuanto a violencia, autolesiones, odio, contenido sexual y solicitudes ilegales, con umbrales configurables. |   1   |  D  |
| 2.4.2 | Verifique que las entradas que violen las políticas reciban rechazos estandarizados o completaciones seguras para que no se propaguen a llamadas posteriores de LLM.                                                   |   1   | D/V |
| 2.4.3 | Verifique que el modelo de filtrado o el conjunto de reglas se reentrene/actualice al menos trimestralmente, incorporando nuevos patrones de jailbreak o evasión de políticas observados.                              |   2   |  D  |
| 2.4.4 | Verifique que el filtrado respete las políticas específicas del usuario (edad, restricciones legales regionales) mediante reglas basadas en atributos que se resuelven en el momento de la solicitud.                  |   2   |  D  |
| 2.4.5 | Verifique que los registros de selección incluyan puntajes de confianza del clasificador y etiquetas de categoría de política para la correlación SOC y la reproducción futura del red-team.                           |   3   |  V  |

---

## C2.5 Limitación de Tasa de Entrada y Prevención de Abuso

Los desarrolladores deben prevenir el abuso, el agotamiento de recursos y los ataques automatizados contra los sistemas de IA limitando las tasas de entrada y detectando patrones de uso anómalos.

|   #   | Descripción                                                                                                                                                           | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.5.1 | Verifique que los límites de tasa por usuario, por IP y por clave API se apliquen en todos los puntos finales de entrada.                                             |   1   | D/V |
| 2.5.2 | Verifique que los límites de tasa de ráfaga y sostenida estén ajustados para prevenir ataques DoS y de fuerza bruta.                                                  |   2   | D/V |
| 2.5.3 | Verifique que los patrones de uso anómalos (por ejemplo, solicitudes rápidas en sucesión, saturación de entradas) desencadenen bloqueos automatizados o escalaciones. |   2   | D/V |
| 2.5.4 | Verifique que los registros de prevención de abusos se conserven y se revisen para detectar patrones de ataque emergentes.                                            |   3   |  V  |

---

## C2.6 Validación de Entrada Multi-Modal

Los sistemas de IA deben incluir una validación robusta para entradas no textuales (imágenes, audio, archivos) para prevenir inyecciones, evasiones o abuso de recursos.

|   #   | Descripción                                                                                                                                    | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.6.1 | Verifique que todas las entradas no textuales (imágenes, audio, archivos) sean validadas por tipo, tamaño y formato antes de su procesamiento. |   1   |  D  |
| 2.6.2 | Verifique que los archivos se escaneen en busca de malware y cargas útiles esteganográficas antes de la ingestión.                             |   2   | D/V |
| 2.6.3 | Verifique que las entradas de imagen/audio sean revisadas para detectar perturbaciones adversarias o patrones de ataque conocidos.             |   2   | D/V |
| 2.6.4 | Verifique que las fallas en la validación de entradas multimodales se registren y generen alertas para su investigación.                       |   3   |  V  |

---

## C2.7 Procedencia de la Entrada y Atribución

Los sistemas de IA deben soportar auditorías, seguimiento de abusos y cumplimiento mediante la monitorización y etiquetado de los orígenes de todas las entradas de los usuarios.

|   #   | Descripción                                                                                                                                                            | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.7.1 | Verifique que todas las entradas de usuario estén etiquetadas con metadatos (ID de usuario, sesión, origen, marca de tiempo, dirección IP) al momento de la ingestión. |   1   | D/V |
| 2.7.2 | Verifique que los metadatos de procedencia se conserven y sean auditable para todas las entradas procesadas.                                                           |   2   | D/V |
| 2.7.3 | Verifique que las fuentes de entrada anómalas o no confiables sean señaladas y estén sujetas a un escrutinio reforzado o bloqueo.                                      |   2   | D/V |

---

## C2.8 Detección Adaptativa de Amenazas en Tiempo Real

Los desarrolladores deben emplear sistemas avanzados de detección de amenazas para IA que se adapten a nuevos patrones de ataque y proporcionen protección en tiempo real con coincidencia de patrones compilados.

|   #   | Descripción                                                                                                                                                                                                                          | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 2.8.1 | Verifique que los patrones de detección de amenazas estén compilados en motores regex optimizados para un filtrado en tiempo real de alto rendimiento con un impacto mínimo en la latencia.                                          |   1   | D/V |
| 2.8.2 | Verifique que los sistemas de detección de amenazas mantengan bibliotecas de patrones separadas para diferentes categorías de amenazas (inyección de instrucciones, contenido dañino, datos sensibles, comandos del sistema).        |   1   | D/V |
| 2.8.3 | Verifique que la detección de amenazas adaptativa incorpore modelos de aprendizaje automático que actualicen la sensibilidad a las amenazas según la frecuencia y las tasas de éxito de los ataques.                                 |   2   | D/V |
| 2.8.4 | Verifique que los flujos de inteligencia de amenazas en tiempo real actualicen automáticamente las bibliotecas de patrones con nuevas firmas de ataque e IOC (Indicadores de Compromiso).                                            |   2   | D/V |
| 2.8.5 | Verifique que las tasas de falsos positivos en la detección de amenazas se monitoricen continuamente y que la especificidad de los patrones se ajuste automáticamente para minimizar la interferencia en los casos de uso legítimos. |   3   | D/V |
| 2.8.6 | Verifique que el análisis de amenazas contextual considere la fuente de entrada, los patrones de comportamiento del usuario y el historial de la sesión para mejorar la precisión de la detección.                                   |   3   | D/V |
| 2.8.7 | Verifique que las métricas de rendimiento de detección de amenazas (tasa de detección, latencia de procesamiento, utilización de recursos) se supervisen y optimicen en tiempo real.                                                 |   3   | D/V |

---

## C2.9 Canalización de Validación de Seguridad Multi-Modal

Los desarrolladores deben proporcionar validación de seguridad para texto, imagen, audio y otras modalidades de entrada de IA con tipos específicos de detección de amenazas y aislamiento de recursos.

|   #   | Descripción                                                                                                                                                                                                                                                                                         | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 2.9.1 | Verifique que cada modalidad de entrada tenga validadores de seguridad dedicados con patrones de amenazas documentados (texto: inyección de instrucciones, imágenes: esteganografía, audio: ataques de espectrograma) y umbrales de detección.                                                      |   1   | D/V |
| 2.9.2 | Verifique que las entradas multimodales se procesen en entornos aislados con límites de recursos definidos (memoria, CPU, tiempo de procesamiento) específicos para cada tipo de modalidad y documentados en las políticas de seguridad.                                                            |   2   | D/V |
| 2.9.3 | Verifique que la detección de ataques cruzados modales identifique ataques coordinados que abarquen múltiples tipos de entrada (por ejemplo, cargas útiles esteganográficas en imágenes combinadas con inyección de instrucciones en texto) mediante reglas de correlación y generación de alertas. |   2   | D/V |
| 2.9.4 | Verifique que las fallas de validación multimodal disparen un registro detallado que incluya todas las modalidades de entrada, resultados de validación, puntuaciones de amenazas y análisis de correlación con formatos de registro estructurados para la integración SIEM.                        |   3   | D/V |
| 2.9.5 | Verifique que los clasificadores de contenido específicos de la modalidad se actualicen según los cronogramas documentados (mínimo trimestralmente) con nuevos patrones de amenaza, ejemplos adversarios y puntos de referencia de rendimiento mantenidos por encima de los umbrales básicos.       |   3   | D/V |

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

