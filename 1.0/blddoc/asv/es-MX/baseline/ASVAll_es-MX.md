## Frontispicio

### Acerca del Estándar

El Estándar de Verificación de Seguridad de Inteligencia Artificial (AISVS) es un catálogo impulsado por la comunidad de requisitos de seguridad que científicos de datos, ingenieros de MLOps, arquitectos de software, desarrolladores, evaluadores, profesionales de seguridad, proveedores de herramientas, reguladores y consumidores pueden usar para diseñar, construir, probar y verificar sistemas y aplicaciones confiables habilitados con IA. Proporciona un lenguaje común para especificar controles de seguridad a lo largo del ciclo de vida de la IA, desde la recopilación de datos y desarrollo de modelos hasta la implementación y el monitoreo continuo, de modo que las organizaciones puedan medir y mejorar la resiliencia, privacidad y seguridad de sus soluciones de IA.

### Derechos de Autor y Licencia

Versión 0.1 (Primer Borrador Público - Trabajo En Progreso), 2025  

![license](images/license.png)
Derechos de autor © 2025 El Proyecto AISVS.  

Publicado bajo laCreative Commons Attribution‑ShareAlike 4.0 International License.
Para cualquier reutilización o distribución, debe comunicar claramente los términos de la licencia de este trabajo a otros.

### Líderes de Proyecto

Jim Manico
Aras “Russ” Memisyazici

### Contribuyentes y Revisores

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS es un estándar totalmente nuevo creado específicamente para abordar los desafíos únicos de seguridad de los sistemas de inteligencia artificial. Aunque se inspira en las mejores prácticas de seguridad más amplias, cada requisito en AISVS ha sido desarrollado desde cero para reflejar el panorama de amenazas de la IA y ayudar a las organizaciones a construir soluciones de IA más seguras y resistentes.

## Prefacio

¡Bienvenido al Estándar de Verificación de Seguridad de Inteligencia Artificial (AISVS) versión 1.0!

### Introducción

Establecida en 2025 mediante un esfuerzo comunitario colaborativo, AISVS define los requisitos de seguridad a considerar al diseñar, desarrollar, desplegar y operar modelos modernos de IA, canales y servicios habilitados con IA.

AISVS v1.0 representa el trabajo conjunto de sus líderes de proyecto, grupo de trabajo y contribuyentes de la comunidad en general para producir una base pragmática y comprobable para asegurar los sistemas de IA.

Nuestro objetivo con esta versión es hacer que AISVS sea fácil de adoptar, manteniendo un enfoque preciso en su alcance definido y abordando el panorama de riesgos en rápida evolución, único en la inteligencia artificial.

### Objetivos clave para AISVS Versión 1.0

La versión 1.0 se creará con varios principios rectores.

#### Alcance Bien Definido

Cada requisito debe alinearse con el nombre y la misión de AISVS:

Inteligencia Artificial – Los controles operan en la capa de IA/ML (datos, modelo, pipeline o inferencia) y son responsabilidad de los profesionales de IA.
Seguridad – Los requisitos mitigan directamente los riesgos identificados de seguridad, privacidad o seguridad.
Verificación: el lenguaje está escrito para que la conformidad pueda ser validada objetivamente.
Estándar: las secciones siguen una estructura y terminología consistentes para formar una referencia coherente.
​
---

Al seguir AISVS, las organizaciones pueden evaluar y fortalecer sistemáticamente la postura de seguridad de sus soluciones de IA, fomentando una cultura de ingeniería de IA segura.

## Usando el AISVS

El Estándar de Verificación de Seguridad de la Inteligencia Artificial (AISVS) define los requisitos de seguridad para aplicaciones y servicios de IA modernos, enfocándose en aspectos bajo el control de los desarrolladores de aplicaciones.

El AISVS está destinado a cualquier persona que desarrolle o evalúe la seguridad de aplicaciones de IA, incluidos desarrolladores, arquitectos, ingenieros de seguridad y auditores. Este capítulo presenta la estructura y el uso del AISVS, incluidos sus niveles de verificación y casos de uso previstos.

### Niveles de Verificación de Seguridad en Inteligencia Artificial

El AISVS define tres niveles ascendentes de verificación de seguridad. Cada nivel añade profundidad y complejidad, permitiendo a las organizaciones adaptar su postura de seguridad al nivel de riesgo de sus sistemas de IA.

Las organizaciones pueden comenzar en el Nivel 1 y adoptar progresivamente niveles superiores a medida que la madurez de la seguridad y la exposición a amenazas aumentan.

#### Definición de los Niveles

Cada requisito en AISVS v1.0 se asigna a uno de los siguientes niveles:

 Requisitos de Nivel 1

El Nivel 1 incluye los requisitos de seguridad más críticos y fundamentales. Estos se centran en prevenir ataques comunes que no dependen de otras condiciones previas o vulnerabilidades. La mayoría de los controles del Nivel 1 son sencillos de implementar o lo suficientemente esenciales como para justificar el esfuerzo.

 Requisitos de nivel 2

El Nivel 2 aborda ataques más avanzados o menos comunes, así como defensas en capas contra amenazas generalizadas. Estos requisitos pueden involucrar una lógica más compleja o dirigirse a prerrequisitos específicos de ataques.

 Requisitos de Nivel 3

El Nivel 3 incluye controles que normalmente son más difíciles de implementar o de aplicabilidad situacional. Estos suelen representar mecanismos de defensa en profundidad o mitigaciones contra ataques específicos, dirigidos o de alta complejidad.

#### Rol (D/V)

Cada requisito de AISVS está marcado según el público principal:

D – Requisitos enfocados en el desarrollador
V – Requisitos enfocados en el verificador/auditor
D/V – Relevante para desarrolladores y verificadores

## Gobernanza de Datos de Entrenamiento C1 y Gestión de Sesgos

### Objetivo de Control

Los datos de entrenamiento deben ser obtenidos, manejados y mantenidos de manera que se preserve la procedencia, seguridad, calidad y equidad. Hacerlo cumple con las obligaciones legales y reduce los riesgos de sesgo, envenenamiento o violaciones de privacidad que puedan surgir durante el entrenamiento y que podrían afectar todo el ciclo de vida de la IA.

---

### C1.1 Procedencia de los Datos de Entrenamiento

Mantenga un inventario verificable de todos los conjuntos de datos, acepte solo fuentes confiables y registre cada cambio para garantizar la auditabilidad.

 #1.1.1    Nivel: 1    Rol: D/V
 Verifique que se mantenga un inventario actualizado de cada fuente de datos de entrenamiento (origen, responsable/propietario, licencia, método de recopilación, restricciones de uso previstas y historial de procesamiento).
 #1.1.2    Nivel: 1    Rol: D/V
 Verifique que los procesos de datos de entrenamiento excluyan características, atributos o campos innecesarios (por ejemplo, metadatos no utilizados, PII sensible, datos de prueba filtrados).
 #1.1.3    Nivel: 2    Rol: D/V
 Verifique que todos los cambios en el conjunto de datos estén sujetos a un flujo de trabajo de aprobación registrado.
 #1.1.4    Nivel: 3    Rol: D/V
 Verifique que los conjuntos de datos o subconjuntos estén marcados con una marca de agua o con huella digital cuando sea posible.

---

### C1.2 Seguridad e Integridad de los Datos de Entrenamiento

Restringir el acceso a los datos de entrenamiento, cifrarlos en reposo y en tránsito, y validar su integridad para prevenir manipulaciones, robos o envenenamiento de datos.

 #1.2.1    Nivel: 1    Rol: D/V
 Verifique que los controles de acceso protejan el almacenamiento de datos de entrenamiento y las canalizaciones.
 #1.2.2    Nivel: 2    Rol: D/V
 Verifique que todo acceso a los datos de entrenamiento esté registrado, incluyendo usuario, hora y acción.
 #1.2.3    Nivel: 2    Rol: D/V
 Verifique que los conjuntos de datos de entrenamiento estén cifrados en tránsito y en reposo, utilizando algoritmos criptográficos estándar de la industria y prácticas de gestión de claves.
 #1.2.4    Nivel: 2    Rol: D/V
 Verifique que se utilicen hashes criptográficos o firmas digitales para garantizar la integridad de los datos durante el almacenamiento y la transferencia de datos de entrenamiento.
 #1.2.5    Nivel: 2    Rol: D/V
 Verifique que se apliquen técnicas automatizadas de detección para proteger contra modificaciones no autorizadas o corrupción de los datos de entrenamiento.
 #1.2.6    Nivel: 2    Rol: D/V
 Verifique que los datos de entrenamiento obsoletos se eliminen de manera segura o se anonimicen.
 #1.2.7    Nivel: 3    Rol: D/V
 Verifique que todas las versiones del conjunto de datos de entrenamiento estén identificadas de manera única, almacenadas de forma inmutable y sean auditables para apoyar la reversión y el análisis forense.

---

### C1.3 Calidad, integridad y seguridad del etiquetado de datos de entrenamiento

Proteja las etiquetas y requiera una revisión técnica para los datos críticos.

 #1.3.1    Nivel: 2    Rol: D/V
 Verifique que se apliquen hashes criptográficos o firmas digitales a los artefactos de etiquetado para garantizar su integridad y autenticidad.
 #1.3.2    Nivel: 2    Rol: D/V
 Verifique que las interfaces y plataformas de etiquetado apliquen controles de acceso fuertes, mantengan registros de auditoría a prueba de manipulaciones de todas las actividades de etiquetado y protejan contra modificaciones no autorizadas.
 #1.3.3    Nivel: 3    Rol: D/V
 Verifique que la información sensible en las etiquetas esté redactada, anonimizada o encriptada a nivel de campo de datos en reposo y en tránsito.

---

### C1.4 Calidad del Datos de Entrenamiento y Garantía de Seguridad

Combine la validación automatizada, las verificaciones manuales aleatorias y la remediación registrada para garantizar la fiabilidad del conjunto de datos.

 #1.4.1    Nivel: 1    Rol: D
 Verifique que las pruebas automatizadas detecten errores de formato y valores nulos en cada ingestión o transformación significativa de datos.
 #1.4.2    Nivel: 2    Rol: D/V
 Verifique que las canalizaciones de entrenamiento y ajuste fino de LLM implementen la detección de envenenamiento y la validación de la integridad de los datos (por ejemplo, métodos estadísticos, detección de valores atípicos, análisis de incrustaciones) para identificar posibles ataques de envenenamiento (por ejemplo, cambio de etiquetas, inserción de disparadores de puerta trasera, comandos de cambio de rol, ataques de instancias influyentes) o la corrupción no intencional de los datos de entrenamiento.
 #1.4.3    Nivel: 3    Rol: D/V
 Verifique que se implementen y ajusten defensas apropiadas, como el entrenamiento adversarial (usando ejemplos adversariales generados), la aumento de datos con entradas perturbadas o técnicas de optimización robusta, para los modelos relevantes según la evaluación de riesgos.
 #1.4.4    Nivel: 2    Rol: D/V
 Verifique que las etiquetas generadas automáticamente (por ejemplo, mediante LLMs o supervisión débil) estén sujetas a umbrales de confianza y verificaciones de consistencia para detectar etiquetas alucinadas, engañosas o de baja confianza.
 #1.4.5    Nivel: 3    Rol: D
 Verifique que las pruebas automatizadas detecten desviaciones en las etiquetas en cada ingestión o transformación significativa de datos.

---

### C1.5 Linaje y trazabilidad de datos

Rastree el recorrido completo de cada punto de datos desde la fuente hasta la entrada del modelo para auditoría y respuesta a incidentes.

 #1.5.1    Nivel: 2    Rol: D/V
 Verifique que el linaje de cada punto de datos, incluidas todas las transformaciones, aumentos y fusiones, esté registrado y pueda reconstruirse.
 #1.5.2    Nivel: 2    Rol: D/V
 Verifique que los registros de linaje sean inmutables, estén almacenados de forma segura y sean accesibles para auditorías.
 #1.5.3    Nivel: 2    Rol: D/V
 Verifique que el seguimiento de la procedencia cubra los datos sintéticos generados mediante técnicas de preservación de la privacidad o generativas, y que todos los datos sintéticos estén claramente etiquetados y sean distinguibles de los datos reales a lo largo de toda la canalización.

---

### Referencias

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
MITRE ATLAS: Adversary Tactics for AI
Survey of ML Bias Mitigation Techniques – MDPI
Data Provenance & Lineage Best Practices – Nightfall AI
Data Labeling Quality Standards – LabelYourData
Training Data Poisoning Guide – Lakera.ai
CISA Advisory: Securing Data for AI Systems
ISO/IEC 23053: AI Management Systems Framework
IBM: What is AI Governance?
Google AI Principles
GDPR & AI Training Data – DataProtectionReport
Supply-Chain Security for AI Data – AppSOC
OpenAI Privacy Center – Data Deletion Controls
Adversarial ML Dataset – Kaggle

## Validación de entrada del usuario C2

### Objetivo de Control

La validación robusta de la entrada del usuario es una defensa de primera línea contra algunos de los ataques más dañinos en los sistemas de IA. Los ataques de inyección de indicaciones pueden anular las instrucciones del sistema, filtrar datos sensibles o dirigir el modelo hacia comportamientos no permitidos. A menos que estén en su lugar filtros dedicados y jerarquías de instrucciones, la investigación demuestra que las "evasiones multi-disparo" que explotan ventanas de contexto muy largas serán efectivas. Además, ataques sutiles de perturbación adversarial—como los intercambios de homoglifos o leetspeak—pueden cambiar silenciosamente las decisiones de un modelo.

---

### C2.1 Defensa contra la Inyección de Prompts

La inyección de indicaciones es uno de los principales riesgos para los sistemas de IA. Las defensas contra esta táctica emplean una combinación de filtros de patrones estáticos, clasificadores dinámicos y aplicación de jerarquía de instrucciones.

 #2.1.1    Nivel: 1    Rol: D/V
 Verifique que las entradas de los usuarios se filtren contra una biblioteca actualizada continuamente de patrones conocidos de inyección de indicaciones (palabras clave de jailbreak, "ignorar lo anterior", cadenas de juego de roles, ataques indirectos de HTML/URL).
 #2.1.2    Nivel: 1    Rol: D/V
 Verifique que el sistema aplica una jerarquía de instrucciones en la que los mensajes del sistema o del desarrollador prevalecen sobre las instrucciones del usuario, incluso después de la expansión de la ventana de contexto.
 #2.1.3    Nivel: 2    Rol: D/V
 Verifique que las pruebas de evaluación adversarial (por ejemplo, indicaciones "many-shot" del Red Team) se realicen antes de cada lanzamiento de modelo o plantilla de indicación, con umbrales de tasa de éxito y bloqueadores automáticos para regresiones.
 #2.1.4    Nivel: 2    Rol: D
 Verifique que los prompts provenientes de contenido de terceros (páginas web, PDFs, correos electrónicos) sean depurados en un contexto de análisis aislado antes de ser concatenados en el prompt principal.
 #2.1.5    Nivel: 3    Rol: D/V
 Verifique que todas las actualizaciones de reglas de filtro de indicaciones, las versiones de los modelos clasificadores y los cambios en la lista de bloqueo estén controlados por versiones y sean auditables.

---

### C2.2 Resistencia a Ejemplos Adversariales

Los modelos de Procesamiento del Lenguaje Natural (PLN) todavía son vulnerables a perturbaciones sutiles a nivel de caracteres o palabras que los humanos suelen pasar por alto pero que los modelos tienden a clasificar incorrectamente.

 #2.2.1    Nivel: 1    Rol: D
 Verifique que los pasos básicos de normalización de entrada (Unicode NFC, mapeo de homógrafos, recorte de espacios en blanco) se ejecuten antes de la tokenización.
 #2.2.2    Nivel: 2    Rol: D/V
 Verifique que la detección estadística de anomalías señale entradas con una distancia de edición inusualmente alta con respecto a las normas del lenguaje, tokens repetidos en exceso o distancias anómalas en los embeddings.
 #2.2.3    Nivel: 2    Rol: D
 Verifique que la canalización de inferencia soporte variantes de modelos endurecidos opcionales por entrenamiento adversarial o capas de defensa (p. ej., aleatorización, destilación defensiva) para puntos finales de alto riesgo.
 #2.2.4    Nivel: 2    Rol: V
 Verifique que las entradas adversarias sospechosas estén en cuarentena, registradas con cargas completas (después de la redacción de PII).
 #2.2.5    Nivel: 3    Rol: D/V
 Verifique que las métricas de robustez (tasa de éxito de conjuntos de ataques conocidos) se rastreen a lo largo del tiempo y que las regresiones activen un bloqueo de lanzamiento.

---

### C2.3 Validación de Esquema, Tipo y Longitud

Los ataques de IA que presentan entradas malformadas o sobredimensionadas pueden causar errores de análisis, desbordamiento de indicaciones entre campos y agotamiento de recursos. La aplicación estricta del esquema también es un requisito previo al realizar llamadas a herramientas deterministas.

 #2.3.1    Nivel: 1    Rol: D
 Verifique que cada punto final de llamada a API o función defina un esquema de entrada explícito (JSON Schema, Protobuf o equivalente multimodal) y que las entradas se validen antes del ensamblaje del prompt.
 #2.3.2    Nivel: 1    Rol: D/V
 Verifique que las entradas que superan el límite máximo de tokens o bytes sean rechazadas con un error seguro y nunca se trunquen silenciosamente.
 #2.3.3    Nivel: 2    Rol: D/V
 Verifique que las comprobaciones de tipo (por ejemplo, rangos numéricos, valores enum, tipos MIME para imágenes/audio) se apliquen del lado del servidor, no solo en el código del cliente.
 #2.3.4    Nivel: 2    Rol: D
 Verificar que los validadores semánticos (por ejemplo, JSON Schema) se ejecuten en tiempo constante para prevenir ataques DoS algorítmicos.
 #2.3.5    Nivel: 3    Rol: V
 Verifique que los fallos de validación se registren con fragmentos de carga útil redactados y códigos de error inequívocos para facilitar la clasificación de seguridad.

---

### C2.4 Revisión de Contenido y Políticas

Los desarrolladores deberían poder detectar indicaciones sintácticamente válidas que soliciten contenido no permitido (como instrucciones ilícitas, discurso de odio y texto con derechos de autor) y luego evitar que se propaguen.

 #2.4.1    Nivel: 1    Rol: D
 Verifique que un clasificador de contenido (sin entrenamiento previo o ajustado) evalúe cada entrada para violencia, autolesiones, odio, contenido sexual y solicitudes ilegales, con umbrales configurables.
 #2.4.2    Nivel: 1    Rol: D/V
 Verifique que las entradas que violen las políticas reciban rechazos estandarizados o cumplimientos seguros para que no se propaguen a llamadas posteriores de modelos de lenguaje grandes (LLM).
 #2.4.3    Nivel: 2    Rol: D
 Verifique que el modelo de filtrado o el conjunto de reglas se reentrene/actualice al menos trimestralmente, incorporando los patrones recién observados de jailbreak o evasión de políticas.
 #2.4.4    Nivel: 2    Rol: D
 Verifique que el filtrado respete las políticas específicas del usuario (edad, restricciones legales regionales) mediante reglas basadas en atributos resueltas en el momento de la solicitud.
 #2.4.5    Nivel: 3    Rol: V
 Verifique que los registros de filtrado incluyan puntajes de confianza del clasificador y etiquetas de categoría de política para la correlación SOC y la reproducción futura de red team.

---

### C2.5 Limitación de la Tasa de Entrada y Prevención de Abuso

Los desarrolladores deben prevenir el abuso, el agotamiento de recursos y los ataques automatizados contra los sistemas de IA limitando las tasas de entrada y detectando patrones de uso anómalos.

 #2.5.1    Nivel: 1    Rol: D/V
 Verifique que los límites de velocidad por usuario, por IP y por clave API se apliquen para todos los puntos finales de entrada.
 #2.5.2    Nivel: 2    Rol: D/V
 Verifique que los límites de velocidad de ráfaga y sostenidos estén ajustados para prevenir ataques DoS y de fuerza bruta.
 #2.5.3    Nivel: 2    Rol: D/V
 Verifique que los patrones de uso anómalos (por ejemplo, solicitudes rápidas, inundación de entradas) desencadenen bloqueos o escaladas automáticas.
 #2.5.4    Nivel: 3    Rol: V
 Verifique que los registros de prevención de abusos se conserven y revisen para detectar patrones de ataque emergentes.

---

### C2.6 Validación de Entrada Multimodal

Los sistemas de IA deben incluir una validación robusta para entradas no textuales (imágenes, audio, archivos) para prevenir inyecciones, evasiones o abusos de recursos.

 #2.6.1    Nivel: 1    Rol: D
 Verifique que todas las entradas no textuales (imágenes, audio, archivos) sean validadas por tipo, tamaño y formato antes de su procesamiento.
 #2.6.2    Nivel: 2    Rol: D/V
 Verifique que los archivos se escaneen en busca de malware y cargas útiles esteganográficas antes de su ingestión.
 #2.6.3    Nivel: 2    Rol: D/V
 Verifique que las entradas de imagen/audio sean revisadas para detectar perturbaciones adversariales o patrones de ataque conocidos.
 #2.6.4    Nivel: 3    Rol: V
 Verifique que las fallas de validación de entrada multimodal se registren y generen alertas para su investigación.

---

### C2.7 Procedencia y Atribución de la Entrada

Los sistemas de IA deben apoyar la auditoría, el seguimiento de abusos y el cumplimiento mediante la supervisión y el etiquetado de los orígenes de todas las entradas de usuario.

 #2.7.1    Nivel: 1    Rol: D/V
 Verifique que todas las entradas de usuario estén etiquetadas con metadatos (ID de usuario, sesión, origen, marca temporal, dirección IP) al momento de la ingestión.
 #2.7.2    Nivel: 2    Rol: D/V
 Verifique que los metadatos de procedencia se conserven y sean auditables para todas las entradas procesadas.
 #2.7.3    Nivel: 2    Rol: D/V
 Verifique que las fuentes de entrada anómalas o no confiables sean señaladas y estén sujetas a un escrutinio o bloqueo mejorado.

---

### C2.8 Detección Adaptativa de Amenazas en Tiempo Real

Los desarrolladores deben emplear sistemas avanzados de detección de amenazas para IA que se adapten a nuevos patrones de ataque y proporcionen protección en tiempo real mediante la coincidencia de patrones compilados.

 #2.8.1    Nivel: 1    Rol: D/V
 Verifique que los patrones de detección de amenazas estén compilados en motores de expresiones regulares optimizados para un filtrado en tiempo real de alto rendimiento con un impacto mínimo en la latencia.
 #2.8.2    Nivel: 1    Rol: D/V
 Verifique que los sistemas de detección de amenazas mantengan bibliotecas de patrones separadas para diferentes categorías de amenazas (inyección de comandos, contenido dañino, datos sensibles, comandos del sistema).
 #2.8.3    Nivel: 2    Rol: D/V
 Verifique que la detección adaptativa de amenazas incorpore modelos de aprendizaje automático que actualicen la sensibilidad a las amenazas en función de la frecuencia de ataques y las tasas de éxito.
 #2.8.4    Nivel: 2    Rol: D/V
 Verifique que las fuentes de inteligencia de amenazas en tiempo real actualicen automáticamente las bibliotecas de patrones con nuevas firmas de ataque e IOCs (Indicadores de Compromiso).
 #2.8.5    Nivel: 3    Rol: D/V
 Verifique que las tasas de falsos positivos en la detección de amenazas se supervisen continuamente y que la especificidad del patrón se ajuste automáticamente para minimizar la interferencia en los casos de uso legítimos.
 #2.8.6    Nivel: 3    Rol: D/V
 Verifique que el análisis contextual de amenazas considere la fuente de entrada, los patrones de comportamiento del usuario y el historial de la sesión para mejorar la precisión de la detección.
 #2.8.7    Nivel: 3    Rol: D/V
 Verifique que las métricas de rendimiento de detección de amenazas (tasa de detección, latencia de procesamiento, utilización de recursos) se monitoreen y optimicen en tiempo real.

---

### C2.9 Pipeline de Validación de Seguridad Multi-Modal

Los desarrolladores deben proporcionar validación de seguridad para texto, imagen, audio y otras modalidades de entrada de IA con tipos específicos de detección de amenazas y aislamiento de recursos.

 #2.9.1    Nivel: 1    Rol: D/V
 Verifique que cada modalidad de entrada tenga validadores de seguridad dedicados con patrones de amenazas documentados (texto: inyección de comandos, imágenes: esteganografía, audio: ataques de espectrograma) y umbrales de detección.
 #2.9.2    Nivel: 2    Rol: D/V
 Verifique que las entradas multimodales se procesen en entornos aislados con límites de recursos definidos (memoria, CPU, tiempo de procesamiento) específicos para cada tipo de modalidad y documentados en las políticas de seguridad.
 #2.9.3    Nivel: 2    Rol: D/V
 Verifique que la detección de ataques cruzados modales identifique ataques coordinados que abarcan múltiples tipos de entradas (por ejemplo, cargas útiles esteganográficas en imágenes combinadas con inyección de indicaciones en texto) mediante reglas de correlación y generación de alertas.
 #2.9.4    Nivel: 3    Rol: D/V
 Verifique que las fallas de validación multimodal desencadenen un registro detallado que incluya todas las modalidades de entrada, resultados de la validación, puntajes de amenaza y análisis de correlación con formatos de registro estructurados para la integración con SIEM.
 #2.9.5    Nivel: 3    Rol: D/V
 Verificar que los clasificadores de contenido específicos de modalidad se actualicen según los cronogramas documentados (mínimo trimestralmente) con nuevos patrones de amenazas, ejemplos adversarios y que los puntos de referencia de rendimiento se mantengan por encima de los umbrales básicos.

---

### Referencias

LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security
Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
$PDF$ OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
Easily enforcing valid JSON schema following – API
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## Gestión del Ciclo de Vida del Modelo C3 y Control de Cambios

### Objetivo de Control

Los sistemas de IA deben implementar procesos de control de cambios que eviten que modificaciones no autorizadas o inseguras del modelo lleguen a producción. Este control garantiza la integridad del modelo a lo largo de todo su ciclo de vida, desde el desarrollo hasta el despliegue y la desactivación, lo que permite una respuesta rápida ante incidentes y mantiene la responsabilidad por todos los cambios.

Objetivo de Seguridad Principal: Solo los modelos autorizados y validados llegan a producción mediante la aplicación de procesos controlados que mantienen la integridad, trazabilidad y recuperabilidad.

---

### C3.1 Autorización e Integridad del Modelo

Solo los modelos autorizados con integridad verificada llegan a los entornos de producción.

 #3.1.1    Nivel: 1    Rol: D/V
 Verifique que todos los artefactos del modelo (pesos, configuraciones, tokenizadores) estén firmados criptográficamente por entidades autorizadas antes del despliegue.
 #3.1.2    Nivel: 1    Rol: D/V
 Verifique que la integridad del modelo se valide en el momento del despliegue y que las fallas en la verificación de la firma impidan la carga del modelo.
 #3.1.3    Nivel: 2    Rol: D/V
 Verifique que los registros de procedencia del modelo incluyan la identidad de la entidad autorizante, sumas de comprobación de los datos de entrenamiento, resultados de pruebas de validación con estado de aprobado/fallado y una marca de tiempo de creación.
 #3.1.4    Nivel: 2    Rol: D/V
 Verifique que todos los artefactos del modelo utilicen versionado semántico (MAYOR.MENOR.PARCHE) con criterios documentados que especifiquen cuándo se incrementa cada componente de la versión.
 #3.1.5    Nivel: 2    Rol: V
 Verifique que el seguimiento de dependencias mantenga un inventario en tiempo real que permita la identificación rápida de todos los sistemas consumidores.

---

### C3.2 Validación y Pruebas del Modelo

Los modelos deben pasar las validaciones definidas de seguridad y seguridad antes del despliegue.

 #3.2.1    Nivel: 1    Rol: D/V
 Verifique que los modelos se sometan a pruebas de seguridad automatizadas que incluyan validación de entradas, saneamiento de salidas y evaluaciones de seguridad con umbrales de aprobación/reprobación organizacionales preacordados antes del despliegue.
 #3.2.2    Nivel: 1    Rol: D/V
 Verifique que las fallas de validación bloqueen automáticamente el despliegue del modelo después de la aprobación explícita de anulación por parte del personal autorizado predesignado con justificaciones comerciales documentadas.
 #3.2.3    Nivel: 2    Rol: V
 Verifique que los resultados de las pruebas estén firmados criptográficamente y vinculados de forma inmutable al hash de la versión específica del modelo que se está validando.
 #3.2.4    Nivel: 2    Rol: D/V
 Verifique que los despliegues de emergencia requieran una evaluación de riesgos de seguridad documentada y la aprobación de una autoridad de seguridad predesignada dentro de los plazos previamente acordados.

---

### C3.3 Despliegue Controlado y Reversión

Las implementaciones de modelos deben ser controladas, monitoreadas y reversibles.

 #3.3.1    Nivel: 1    Rol: D
 Verifique que las implementaciones en producción utilicen mecanismos de despliegue gradual (despliegues canarios, despliegues azul-verde) con activadores automáticos de reversión basados en tasas de error, umbrales de latencia o criterios de alerta de seguridad preacordados.
 #3.3.2    Nivel: 1    Rol: D/V
 Verifique que las capacidades de reversión restauren el estado completo del modelo (pesos, configuraciones, dependencias) de manera atómica dentro de las ventanas de tiempo organizacionales predefinidas.
 #3.3.3    Nivel: 2    Rol: D/V
 Verifique que los procesos de implementación validen las firmas criptográficas y calculen sumas de verificación de integridad antes de la activación del modelo, y que la implementación falle ante cualquier discrepancia.
 #3.3.4    Nivel: 2    Rol: D/V
 Verifique que las capacidades de apagado de emergencia del modelo puedan deshabilitar los puntos finales del modelo dentro de los tiempos de respuesta predefinidos mediante interruptores automáticos de circuito o interruptores de apagado manuales.
 #3.3.5    Nivel: 2    Rol: V
 Verifique que los artefactos de reversión (versiones anteriores del modelo, configuraciones, dependencias) se conserven según las políticas organizacionales con almacenamiento inmutable para la respuesta a incidentes.

---

### C3.4 Cambio de Responsabilidad y Auditoría

Todos los cambios en el ciclo de vida del modelo deben ser rastreables y auditables.

 #3.4.1    Nivel: 1    Rol: V
 Verifique que todos los cambios en el modelo (implementación, configuración, retiro) generen registros de auditoría inmutables que incluyan una marca de tiempo, una identidad de actor autenticada, un tipo de cambio y los estados antes/después.
 #3.4.2    Nivel: 2    Rol: D/V
 Verifique que el acceso al registro de auditoría requiera la autorización adecuada y que todos los intentos de acceso se registren con la identidad del usuario y una marca de tiempo.
 #3.4.3    Nivel: 2    Rol: D/V
 Verifique que las plantillas de indicaciones y los mensajes del sistema estén controlados por versiones en repositorios git con revisión de código obligatoria y aprobación de revisores designados antes de la implementación.
 #3.4.4    Nivel: 2    Rol: V
 Verifique que los registros de auditoría incluyan detalles suficientes (hashes de modelos, capturas de configuración, versiones de dependencias) para permitir la reconstrucción completa del estado del modelo para cualquier marca de tiempo dentro del período de retención.

---

### C3.5 Prácticas de Desarrollo Seguro

Los procesos de desarrollo y entrenamiento del modelo deben seguir prácticas seguras para prevenir compromisos.

 #3.5.1    Nivel: 1    Rol: D
 Verifique que los entornos de desarrollo, prueba y producción del modelo estén separados física o lógicamente. No deben compartir infraestructura, deben tener controles de acceso distintos y almacenes de datos aislados.
 #3.5.2    Nivel: 1    Rol: D
 Verifique que el entrenamiento y la afinación del modelo se realicen en entornos aislados con acceso de red controlado.
 #3.5.3    Nivel: 1    Rol: D/V
 Verifique que las fuentes de datos de entrenamiento sean validadas mediante controles de integridad y autenticadas a través de fuentes confiables con una cadena de custodia documentada antes de su uso en el desarrollo del modelo.
 #3.5.4    Nivel: 2    Rol: D
 Verifique que los artefactos de desarrollo del modelo (hiperparámetros, scripts de entrenamiento, archivos de configuración) estén almacenados en control de versiones y requieran aprobación mediante revisión por pares antes de usarse en el entrenamiento.

---

### C3.6 Retiro y Desmantelamiento del Modelo

Los modelos deben ser retirados de manera segura cuando ya no son necesarios o cuando se identifican problemas de seguridad.

 #3.6.1    Nivel: 1    Rol: D
 Verifique que los procesos de retiro de modelos escaneen automáticamente los grafos de dependencias, identifiquen todos los sistemas consumidores y proporcionen períodos de aviso previo acordados antes de la desactivación.
 #3.6.2    Nivel: 1    Rol: D/V
 Verifique que los artefactos de modelos retirados sean eliminados de forma segura utilizando borrado criptográfico o sobrescritura múltiple conforme a las políticas documentadas de retención de datos, con certificados de destrucción verificados.
 #3.6.3    Nivel: 2    Rol: V
 Verifique que los eventos de retiro del modelo se registren con marca de tiempo e identidad del actor, y que las firmas del modelo sean revocadas para prevenir su reutilización.
 #3.6.4    Nivel: 2    Rol: D/V
 Verifique que la retirada de modelos de emergencia pueda deshabilitar el acceso al modelo dentro de los plazos preestablecidos de respuesta a emergencias mediante interruptores automáticos en caso de que se descubran vulnerabilidades críticas de seguridad.

---

### Referencias

MLOps Principles
Securing AI/ML Ops – Cisco.com
Audit logs security: cryptographically signed tamper-proof logs
Machine Learning Model Versioning: Top Tools & Best Practices
AI Hygiene Starts with Models and Data Loaders – SEI Blog
How to handle versioning and rollback of a deployed ML model?
Reinforcement fine-tuning – OpenAI API
Auditing Machine Learning models: Governance, Data Security and …
Adversarial Training to Improve Model Robustness
What is AI adversarial robustness? – IBM Research
Exploring Data Provenance: Ensuring Data Integrity and Authenticity
MITRE ATLAS
AWS Prescriptive Guidance – Best practices for retiring applications …

## Seguridad de Infraestructura, Configuración y Despliegue C4

### Objetivo de Control

La infraestructura de IA debe ser reforzada contra la escalada de privilegios, la manipulación de la cadena de suministro y el movimiento lateral mediante configuración segura, aislamiento en tiempo de ejecución, canales de despliegue confiables y monitoreo integral. Solo los componentes y configuraciones de infraestructura autorizados y validados llegan a producción a través de procesos controlados que mantienen la seguridad, integridad y capacidad de auditoría.

Objetivo principal de seguridad: Solo los componentes de infraestructura firmados criptográficamente y escaneados en busca de vulnerabilidades llegan a producción a través de canalizaciones de validación automatizadas que aplican políticas de seguridad y mantienen registros de auditoría inmutables.

---

### C4.1 Aislamiento del Entorno de Ejecución

Prevenir escapes de contenedores y la escalada de privilegios mediante primitivas de aislamiento a nivel de kernel y controles de acceso obligatorios.

 #4.1.1    Nivel: 1    Rol: D/V
 Verifique que todos los contenedores de IA descarten TODAS las capacidades de Linux excepto CAP_SETUID, CAP_SETGID y las capacidades explícitamente requeridas documentadas en las líneas base de seguridad.
 #4.1.2    Nivel: 1    Rol: D/V
 Verifique que los perfiles seccomp bloqueen todas las llamadas al sistema excepto aquellas en las listas de autorización preaprobadas, con violaciones que terminan el contenedor y generan alertas de seguridad.
 #4.1.3    Nivel: 2    Rol: D/V
 Verifique que las cargas de trabajo de IA se ejecuten con sistemas de archivos raíz de solo lectura, tmpfs para datos temporales y volúmenes con nombre para datos persistentes, aplicando opciones de montaje noexec.
 #4.1.4    Nivel: 2    Rol: D/V
 Verifique que la monitorización en tiempo real basada en eBPF (Falco, Tetragon o equivalente) detecte intentos de escalada de privilegios y elimine automáticamente los procesos infractores dentro de los requisitos de tiempo de respuesta organizacional.
 #4.1.5    Nivel: 3    Rol: D/V
 Verifique que las cargas de trabajo de IA de alto riesgo se ejecuten en entornos aislados por hardware (Intel TXT, AMD SVM o nodos dedicados bare-metal) con verificación de atestación.

---

### C4.2 Canalizaciones Seguras de Construcción y Despliegue

Asegure la integridad criptográfica y la seguridad de la cadena de suministro mediante compilaciones reproducibles y artefactos firmados.

 #4.2.1    Nivel: 1    Rol: D/V
 Verifique que la infraestructura como código se escanee con herramientas (tfsec, Checkov o Terrascan) en cada commit, bloqueando las fusiones con hallazgos de severidad CRÍTICA o ALTA.
 #4.2.2    Nivel: 1    Rol: D/V
 Verifique que las compilaciones de contenedores sean reproducibles con hashes SHA256 idénticos en diferentes compilaciones y genere atestaciones de procedencia SLSA Nivel 3 firmadas con Sigstore.
 #4.2.3    Nivel: 2    Rol: D/V
 Verifique que las imágenes de contenedor integren SBOMs CycloneDX o SPDX y estén firmadas con Cosign antes de la subida al registro, rechazando las imágenes no firmadas en el despliegue.
 #4.2.4    Nivel: 2    Rol: D/V
 Verifique que las canalizaciones CI/CD utilicen tokens OIDC de HashiCorp Vault, Roles IAM de AWS o Identidad Administrada de Azure con tiempos de vida que no excedan los límites establecidos por la política de seguridad organizacional.
 #4.2.5    Nivel: 2    Rol: D/V
 Verifique que las firmas Cosign y la procedencia SLSA se validen durante el proceso de implementación antes de la ejecución del contenedor y que los errores de verificación provoquen que la implementación falle.
 #4.2.6    Nivel: 2    Rol: D/V
 Verifique que los entornos de construcción se ejecuten en contenedores efímeros o máquinas virtuales sin almacenamiento persistente y con aislamiento de red respecto a las VPC de producción.

---

### C4.3 Seguridad de la Red y Control de Acceso

Implemente redes de confianza cero con políticas de denegación predeterminada y comunicaciones cifradas.

 #4.3.1    Nivel: 1    Rol: D/V
 Verifique que las NetworkPolicies de Kubernetes o cualquier equivalente implementen una política predeterminada de denegación para ingress/egress con reglas explícitas de permiso para los puertos requeridos (443, 8080, etc.).
 #4.3.2    Nivel: 1    Rol: D/V
 Verifique que SSH (puerto 22), RDP (puerto 3389) y los endpoints de metadatos en la nube (169.254.169.254) estén bloqueados o requieran autenticación basada en certificados.
 #4.3.3    Nivel: 2    Rol: D/V
 Verifique que el tráfico de salida esté filtrado a través de proxies HTTP/HTTPS (Squid, Istio o puertas de enlace NAT en la nube) con listas de dominios permitidos y que las solicitudes bloqueadas sean registradas.
 #4.3.4    Nivel: 2    Rol: D/V
 Verifique que la comunicación entre servicios utilice TLS mutuo con certificados rotados según la política organizacional y que se aplique la validación de certificados (sin utilizar banderas de omisión de verificación).
 #4.3.5    Nivel: 2    Rol: D/V
 Verifique que la infraestructura de IA funcione en VPCs/VNets dedicadas sin acceso directo a internet y que se comunique únicamente a través de gateways NAT o hosts bastión.

---

### C4.4 Gestión de secretos y claves criptográficas

Proteja las credenciales mediante almacenamiento respaldado por hardware y rotación automatizada con acceso de confianza cero.

 #4.4.1    Nivel: 1    Rol: D/V
 Verifique que los secretos estén almacenados en HashiCorp Vault, AWS Secrets Manager, Azure Key Vault o Google Secret Manager con cifrado en reposo utilizando AES-256.
 #4.4.2    Nivel: 1    Rol: D/V
 Verificar que las claves criptográficas se generen en HSMs de nivel 2 FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) con rotación de claves según la política criptográfica organizacional.
 #4.4.3    Nivel: 2    Rol: D/V
 Verifique que la rotación de secretos esté automatizada con despliegue sin tiempo de inactividad y rotación inmediata activada por cambios de personal o incidentes de seguridad.
 #4.4.4    Nivel: 2    Rol: D/V
 Verifique que las imágenes de contenedores sean escaneadas con herramientas (GitLeaks, TruffleHog o detect-secrets) bloqueando las compilaciones que contengan claves API, contraseñas o certificados.
 #4.4.5    Nivel: 2    Rol: D/V
 Verifique que el acceso secreto a producción requiera MFA con tokens de hardware (YubiKey, FIDO2) y que se registre mediante registros de auditoría inmutables con identidades de usuario y marcas de tiempo.
 #4.4.6    Nivel: 2    Rol: D/V
 Verifique que los secretos se inyecten mediante secretos de Kubernetes, volúmenes montados o contenedores de inicialización y asegúrese de que los secretos nunca se incrusten en variables de entorno o imágenes.

---

### C4.5 Sandboxing y Validación de Carga de Trabajo de IA

Aísle los modelos de IA no confiables en entornos seguros con un análisis de comportamiento integral.

 #4.5.1    Nivel: 1    Rol: D/V
 Verifique que los modelos externos de IA se ejecuten en gVisor, microVMs (como Firecracker, CrossVM) o contenedores Docker con las opciones --security-opt=no-new-privileges y --read-only.
 #4.5.2    Nivel: 1    Rol: D/V
 Verifique que los entornos de prueba no tengan conectividad de red (--network=none) o solo acceso a localhost, con todas las solicitudes externas bloqueadas por reglas de iptables.
 #4.5.3    Nivel: 2    Rol: D/V
 Verifique que la validación del modelo de IA incluya pruebas automáticas de red team con cobertura de prueba definida organizacionalmente y análisis de comportamiento para la detección de puertas traseras.
 #4.5.4    Nivel: 2    Rol: D/V
 Verifique que antes de que un modelo de IA sea promovido a producción, sus resultados en sandbox estén firmados criptográficamente por personal de seguridad autorizado y almacenados en registros de auditoría inmutables.
 #4.5.5    Nivel: 2    Rol: D/V
 Verifique que los entornos sandbox se destruyan y se vuelvan a crear a partir de imágenes maestras entre las evaluaciones, con una limpieza completa del sistema de archivos y la memoria.

---

### C4.6 Monitoreo de Seguridad de Infraestructura

Escanee y supervise continuamente la infraestructura con remediación automatizada y alertas en tiempo real.

 #4.6.1    Nivel: 1    Rol: D/V
 Verifique que las imágenes de contenedores se escaneen según los horarios organizacionales, con vulnerabilidades CRÍTICAS que bloqueen el despliegue basándose en los umbrales de riesgo organizacionales.
 #4.6.2    Nivel: 1    Rol: D/V
 Verifique que la infraestructura cumpla con los CIS Benchmarks o los controles NIST 800-53 con umbrales de cumplimiento definidos por la organización y remediación automatizada para las verificaciones que no pasen.
 #4.6.3    Nivel: 2    Rol: D/V
 Verifique que las vulnerabilidades de alta gravedad estén parcheadas de acuerdo con los cronogramas de gestión de riesgos organizacionales, con procedimientos de emergencia para CVEs que se están explotando activamente.
 #4.6.4    Nivel: 2    Rol: V
 Verifique que las alertas de seguridad se integren con las plataformas SIEM (Splunk, Elastic o Sentinel) utilizando los formatos CEF o STIX/TAXII con enriquecimiento automatizado.
 #4.6.5    Nivel: 3    Rol: V
 Verifique que las métricas de la infraestructura se exporten a los sistemas de monitoreo (Prometheus, DataDog) con paneles de SLA y reportes ejecutivos.
 #4.6.6    Nivel: 2    Rol: D/V
 Verifique que la deriva de configuración se detecte utilizando herramientas (Chef InSpec, AWS Config) según los requisitos de monitoreo organizacional con reversión automática para cambios no autorizados.

---

### Gestión de Recursos de Infraestructura de IA C4.7

Prevenir ataques de agotamiento de recursos y garantizar la asignación justa de recursos mediante cuotas y monitoreo.

 #4.7.1    Nivel: 1    Rol: D/V
 Verifique que la utilización de GPU/TPU se monitoree con alertas que se activen en los umbrales definidos organizacionalmente y que se active el escalado automático o el balanceo de carga según las políticas de gestión de capacidad.
 #4.7.2    Nivel: 1    Rol: D/V
 Verifique que las métricas de carga de trabajo de IA (latencia de inferencia, rendimiento, tasas de error) se recopilen de acuerdo con los requisitos de monitoreo organizacional y se correlacionen con la utilización de la infraestructura.
 #4.7.3    Nivel: 2    Rol: D/V
 Verifique que los ResourceQuotas de Kubernetes o su equivalente limiten los trabajos individuales de acuerdo con las políticas organizacionales de asignación de recursos, con límites estrictos aplicados.
 #4.7.4    Nivel: 2    Rol: V
 Verifique que el monitoreo de costos rastree el gasto por carga de trabajo/inquilino con alertas basadas en los umbrales presupuestarios organizacionales y controles automatizados para sobrepasos del presupuesto.
 #4.7.5    Nivel: 3    Rol: V
 Verifique que la planificación de capacidad utilice datos históricos con periodos de pronóstico definidos por la organización y aprovisionamiento automatizado de recursos basado en patrones de demanda.
 #4.7.6    Nivel: 2    Rol: D/V
 Verifique que el agotamiento de recursos active los disyuntores según los requisitos de respuesta organizacional, incluyendo la limitación de la tasa basada en políticas de capacidad y el aislamiento de la carga de trabajo.

---

### C4.8 Separación de Entornos y Controles de Promoción

Aplicar límites estrictos al entorno con puertas de promoción automatizadas y validación de seguridad.

 #4.8.1    Nivel: 1    Rol: D/V
 Verifique que los entornos de desarrollo/prueba/producción se ejecuten en VPCs/VNets separadas sin roles IAM, grupos de seguridad o conectividad de red compartidos.
 #4.8.2    Nivel: 1    Rol: D/V
 Verifique que la promoción del entorno requiera la aprobación del personal autorizado definido organizacionalmente mediante firmas criptográficas y registros de auditoría inmutables.
 #4.8.3    Nivel: 2    Rol: D/V
 Verifique que los entornos de producción bloqueen el acceso SSH, deshabiliten los puntos finales de depuración y requieran solicitudes de cambio con requisitos de aviso previo organizacional, excepto en emergencias.
 #4.8.4    Nivel: 2    Rol: D/V
 Verifique que los cambios en infraestructura como código requieran revisión por pares junto con pruebas automatizadas y escaneo de seguridad antes de fusionarlos a la rama principal.
 #4.8.5    Nivel: 2    Rol: D/V
 Verifique que los datos no productivos estén anonimizados según los requisitos de privacidad organizacionales, generación de datos sintéticos o enmascaramiento completo de datos con eliminación de información de identificación personal (PII) verificada.
 #4.8.6    Nivel: 2    Rol: D/V
 Verifique que las puertas de promoción incluyan pruebas de seguridad automatizadas (SAST, DAST, escaneo de contenedores) con cero hallazgos CRÍTICOS requeridos para la aprobación.

---

### C4.9 Respaldo y Recuperación de Infraestructura

Garantice la resiliencia de la infraestructura mediante copias de seguridad automatizadas, procedimientos de recuperación probados y capacidades de recuperación ante desastres.

 #4.9.1    Nivel: 1    Rol: D/V
 Verifique que las configuraciones de infraestructura estén respaldadas según los cronogramas de respaldo organizacionales en regiones geográficamente separadas con la implementación de la estrategia de respaldo 3-2-1.
 #4.9.2    Nivel: 2    Rol: D/V
 Verifique que los sistemas de respaldo funcionen en redes aisladas con credenciales separadas y almacenamiento con aislamiento de red para la protección contra ransomware.
 #4.9.3    Nivel: 2    Rol: V
 Verifique que los procedimientos de recuperación se prueben y validen mediante pruebas automatizadas según los horarios organizacionales, con objetivos de RTO y RPO que cumplan con los requisitos de la organización.
 #4.9.4    Nivel: 3    Rol: V
 Verifique que la recuperación ante desastres incluya runbooks específicos de IA con restauración de pesos del modelo, reconstrucción de clústeres GPU y mapeo de dependencias de servicios.

---

### C4.10 Cumplimiento y Gobernanza de Infraestructura

Mantenga el cumplimiento normativo mediante la evaluación continua, la documentación y los controles automatizados.

 #4.10.1    Nivel: 2    Rol: D/V
 Verifique que el cumplimiento de la infraestructura se evalúe según los cronogramas organizacionales contra los controles SOC 2, ISO 27001 o FedRAMP con recolección automatizada de evidencia.
 #4.10.2    Nivel: 2    Rol: V
 Verifique que la documentación de la infraestructura incluya diagramas de red, mapas de flujo de datos y modelos de amenazas actualizados conforme a los requisitos de gestión de cambios organizacionales.
 #4.10.3    Nivel: 3    Rol: D/V
 Verifique que los cambios en la infraestructura se sometan a una evaluación automatizada del impacto de cumplimiento con flujos de trabajo de aprobación regulatoria para modificaciones de alto riesgo.

---

### C4.11 Seguridad de Hardware de IA

Componentes de hardware específicos para IA seguros, incluidos GPUs, TPUs y aceleradores especializados de IA.

 #4.11.1    Nivel: 2    Rol: D/V
 Verifique que el firmware del acelerador de IA (BIOS de GPU, firmware de TPU) esté verificado con firmas criptográficas y se actualice de acuerdo con los cronogramas de gestión de parches de la organización.
 #4.11.2    Nivel: 2    Rol: D/V
 Verifique que antes de la ejecución de la carga de trabajo, la integridad del acelerador de IA sea validada mediante atestación de hardware utilizando TPM 2.0, Intel TXT o AMD SVM.
 #4.11.3    Nivel: 2    Rol: D/V
 Verifique que la memoria GPU esté aislada entre cargas de trabajo utilizando SR-IOV, MIG (GPU de instancia múltiple) o particionamiento de hardware equivalente con saneamiento de memoria entre trabajos.
 #4.11.4    Nivel: 3    Rol: V
 Verifique que la cadena de suministro de hardware de IA incluya la verificación de procedencia con certificados del fabricante y la validación de embalajes a prueba de manipulaciones.
 #4.11.5    Nivel: 3    Rol: D/V
 Verifique que los módulos de seguridad de hardware (HSM) protejan los pesos del modelo de IA y las claves criptográficas con la certificación FIPS 140-2 Nivel 3 o Common Criteria EAL4+.

---

### C4.12 Infraestructura de IA en el Borde y Distribuida

Despliegues de IA distribuidos seguros que incluyen computación en el borde, aprendizaje federado y arquitecturas multipunto.

 #4.12.1    Nivel: 2    Rol: D/V
 Verifique que los dispositivos de edge AI se autentiquen con la infraestructura central utilizando TLS mutuo con certificados de dispositivo rotados según la política organizacional de gestión de certificados.
 #4.12.2    Nivel: 2    Rol: D/V
 Verifique que los dispositivos edge implementen arranque seguro con firmas verificadas y protección contra reversión para prevenir ataques de degradación de firmware.
 #4.12.3    Nivel: 3    Rol: D/V
 Verifique que la coordinación de IA distribuida utilice algoritmos de consenso tolerantes a fallos bizantinos con validación de participantes y detección de nodos maliciosos.
 #4.12.4    Nivel: 3    Rol: D/V
 Verifique que la comunicación de borde a nube incluya limitación de ancho de banda, compresión de datos y capacidades de operación sin conexión con almacenamiento local seguro.

---

### C4.13 Seguridad de Infraestructura Multi-Nube e Híbrida

Asegure las cargas de trabajo de IA en múltiples proveedores de nube y en implementaciones híbridas de nube y locales.

 #4.13.1    Nivel: 2    Rol: D/V
 Verifique que las implementaciones de IA multi-nube utilicen federación de identidad agnóstica a la nube (OIDC, SAML) con gestión centralizada de políticas entre proveedores.
 #4.13.2    Nivel: 2    Rol: D/V
 Verifique que la transferencia de datos entre nubes utilice cifrado de extremo a extremo con claves gestionadas por el cliente y que se apliquen controles de residencia de datos según la jurisdicción.
 #4.13.3    Nivel: 2    Rol: D/V
 Verifique que las cargas de trabajo de IA en la nube híbrida implementen políticas de seguridad consistentes tanto en entornos locales como en la nube, con monitoreo y alertas unificados.
 #4.13.4    Nivel: 3    Rol: V
 Verifique que la prevención del bloqueo del proveedor de la nube incluya infraestructura como código portátil, APIs estandarizadas y capacidades de exportación de datos con herramientas de conversión de formatos.
 #4.13.5    Nivel: 3    Rol: V
 Verifique que la optimización de costos multi-nube incluya controles de seguridad que eviten la proliferación de recursos, así como cargos no autorizados por transferencia de datos entre nubes.

---

### C4.14 Automatización de Infraestructura y Seguridad GitOps

Automatización segura de infraestructuras y flujos de trabajo GitOps para la gestión de infraestructuras de IA.

 #4.14.1    Nivel: 2    Rol: D/V
 Verifique que los repositorios GitOps requieran commits firmados con claves GPG y reglas de protección de ramas que eviten los empujes directos a las ramas principales.
 #4.14.2    Nivel: 2    Rol: D/V
 Verifique que la automatización de la infraestructura incluya detección de desviaciones con capacidades automáticas de remediación y reversión activadas según los requisitos de respuesta organizacional para cambios no autorizados.
 #4.14.3    Nivel: 2    Rol: D/V
 Verifique que la provisión automatizada de infraestructura incluya la validación de políticas de seguridad con bloqueo de despliegue para configuraciones no conformes.
 #4.14.4    Nivel: 2    Rol: D/V
 Verifique que los secretos de automatización de infraestructura se gestionen a través de operadores de secretos externos (External Secrets Operator, Bank-Vaults) con rotación automática.
 #4.14.5    Nivel: 3    Rol: V
 Verifique que la infraestructura autocurativa incluya la correlación de eventos de seguridad con la respuesta automatizada a incidentes y los flujos de trabajo de notificación a las partes interesadas.

---

### C4.15 Seguridad de Infraestructura Resistente a la Computación Cuántica

Prepare la infraestructura de IA para amenazas de informática cuántica mediante criptografía post-cuántica y protocolos seguros frente a la computación cuántica.

 #4.15.1    Nivel: 3    Rol: D/V
 Verifique que la infraestructura de IA implemente algoritmos criptográficos post-cuánticos aprobados por NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para el intercambio de claves y firmas digitales.
 #4.15.2    Nivel: 3    Rol: D/V
 Verificar que los sistemas de distribución de claves cuánticas (QKD) se implementen para comunicaciones de IA de alta seguridad con protocolos de gestión de claves resistentes a la computación cuántica.
 #4.15.3    Nivel: 3    Rol: D/V
 Verifique que los marcos de agilidad criptográfica permitan una migración rápida a nuevos algoritmos post-cuánticos con rotación automatizada de certificados y claves.
 #4.15.4    Nivel: 3    Rol: V
 Verifique que el modelado de amenazas cuánticas evalúe la vulnerabilidad de la infraestructura de IA a ataques cuánticos con líneas de tiempo de migración documentadas y evaluaciones de riesgo.
 #4.15.5    Nivel: 3    Rol: D/V
 Verifique que los sistemas criptográficos híbridos clásico-cuánticos proporcionen una defensa en profundidad durante el período de transición cuántica con monitoreo de rendimiento.

---

### C4.16 Computación Confidencial y Enclaves Seguros

Proteja las cargas de trabajo de IA y los pesos del modelo utilizando entornos de ejecución confiables basados en hardware y tecnologías de computación confidencial.

 #4.16.1    Nivel: 3    Rol: D/V
 Verifique que los modelos de IA sensibles se ejecuten dentro de enclaves Intel SGX, AMD SEV-SNP o ARM TrustZone con memoria cifrada y verificación de atestación.
 #4.16.2    Nivel: 3    Rol: D/V
 Verifique que los contenedores confidenciales (Kata Containers, gVisor con computación confidencial) aíslan las cargas de trabajo de IA con cifrado de memoria aplicado por hardware.
 #4.16.3    Nivel: 3    Rol: D/V
 Verifique que la atestación remota valide la integridad del enclave antes de cargar los modelos de IA con una prueba criptográfica de la autenticidad del entorno de ejecución.
 #4.16.4    Nivel: 3    Rol: D/V
 Verifique que los servicios confidenciales de inferencia de IA eviten la extracción del modelo mediante computación encriptada con pesos del modelo sellados y ejecución protegida.
 #4.16.5    Nivel: 3    Rol: D/V
 Verifique que la orquestación del entorno de ejecución confiable gestione el ciclo de vida del enclave seguro con atestación remota y canales de comunicación cifrados.
 #4.16.6    Nivel: 3    Rol: D/V
 Verifique que el cómputo multipartito seguro (SMPC) permite el entrenamiento colaborativo de IA sin exponer conjuntos de datos individuales ni parámetros del modelo.

---

### C4.17 Infraestructura de Conocimiento Cero

Implementar sistemas de prueba de conocimiento cero para la verificación y autenticación de IA que preserven la privacidad sin revelar información sensible.

 #4.17.1    Nivel: 3    Rol: D/V
 Verifique que las pruebas de conocimiento cero (ZK-SNARKs, ZK-STARKs) validan la integridad del modelo de IA y la procedencia del entrenamiento sin exponer los pesos del modelo ni los datos de entrenamiento.
 #4.17.2    Nivel: 3    Rol: D/V
 Verifique que los sistemas de autenticación basados en ZK permiten la verificación de usuarios preservando la privacidad para servicios de IA sin revelar información relacionada con la identidad.
 #4.17.3    Nivel: 3    Rol: D/V
 Verifique que los protocolos de intersección privada de conjuntos (PSI) permiten una coincidencia segura de datos para la IA federada sin exponer conjuntos de datos individuales.
 #4.17.4    Nivel: 3    Rol: D/V
 Verifique que los sistemas de aprendizaje automático de conocimiento cero (ZKML) permiten inferencias de IA verificables con prueba criptográfica de cálculo correcto.
 #4.17.5    Nivel: 3    Rol: D/V
 Verifique que los ZK-rollups proporcionan un procesamiento de transacciones de IA escalable y que preserva la privacidad, con verificación por lotes y reducción de la carga computacional.

---

### C4.18 Prevención de ataques por canal lateral

Proteja la infraestructura de IA contra ataques de canal lateral basados en tiempo, energía, electromagnéticos y caché que podrían filtrar información sensible.

 #4.18.1    Nivel: 3    Rol: D/V
 Verifique que el tiempo de inferencia de IA esté normalizado utilizando algoritmos de tiempo constante y relleno para prevenir ataques de extracción de modelos basados en el tiempo.
 #4.18.2    Nivel: 3    Rol: D/V
 Verifique que la protección contra el análisis de potencia incluya inyección de ruido, filtrado de la línea de alimentación y patrones de ejecución aleatorios para el hardware de IA.
 #4.18.3    Nivel: 3    Rol: D/V
 Verifique que la mitigación de canales secundarios basada en caché utilice particionamiento de caché, aleatorización e instrucciones de limpieza para prevenir la filtración de información.
 #4.18.4    Nivel: 3    Rol: D/V
 Verifique que la protección contra emanaciones electromagnéticas incluya blindaje, filtrado de señales y procesamiento aleatorio para prevenir ataques al estilo TEMPEST.
 #4.18.5    Nivel: 3    Rol: D/V
 Verifique que las defensas contra canales laterales microarquitectónicos incluyan controles de ejecución especulativa y ofuscación de patrones de acceso a memoria.

---

### C4.19 Seguridad en Hardware Neuromórfico y de IA Especializada

Asegurar arquitecturas de hardware de IA emergentes, incluyendo chips neuromórficos, FPGAs, ASICs personalizados y sistemas de computación óptica.

 #4.19.1    Nivel: 3    Rol: D/V
 Verifique que la seguridad del chip neuromórfico incluya el cifrado del patrón de picos, la protección del peso sináptico y la validación basada en hardware de la regla de aprendizaje.
 #4.19.2    Nivel: 3    Rol: D/V
 Verifique que los aceleradores de IA basados en FPGA implementen cifrado de bitstream, mecanismos anti-manipulación y carga de configuración segura con actualizaciones autenticadas.
 #4.19.3    Nivel: 3    Rol: D/V
 Verifique que la seguridad personalizada del ASIC incluya procesadores de seguridad en chip, raíz de confianza de hardware y almacenamiento seguro de claves con detección de manipulación.
 #4.19.4    Nivel: 3    Rol: D/V
 Verifique que los sistemas de computación óptica implementen cifrado óptico seguro ante tecnologías cuánticas, conmutación fotónica segura y procesamiento de señales ópticas protegido.
 #4.19.5    Nivel: 3    Rol: D/V
 Verifique que los chips de IA híbridos analógicos-digitales incluyan computación analógica segura, almacenamiento protegido de pesos y conversión analógica a digital autenticada.

---

### C4.20 Infraestructura de Cómputo Preservadora de la Privacidad

Implementar controles de infraestructura para el cálculo que preserva la privacidad y proteger los datos sensibles durante el procesamiento y análisis de IA.

 #4.20.1    Nivel: 3    Rol: D/V
 Verifique que la infraestructura de cifrado homomórfico permita el cálculo cifrado en cargas de trabajo de IA sensibles con verificación criptográfica de integridad y monitoreo de desempeño.
 #4.20.2    Nivel: 3    Rol: D/V
 Verifique que los sistemas de recuperación de información privada permitan consultas a la base de datos sin revelar patrones de consulta con protección criptográfica de los patrones de acceso.
 #4.20.3    Nivel: 3    Rol: D/V
 Verifique que los protocolos de computación multipartita segura permiten la inferencia de IA preservando la privacidad sin exponer las entradas individuales ni los cálculos intermedios.
 #4.20.4    Nivel: 3    Rol: D/V
 Verifique que la gestión de claves que preserva la privacidad incluya generación distribuida de claves, criptografía umbral y rotación segura de claves con protección respaldada por hardware.
 #4.20.5    Nivel: 3    Rol: D/V
 Verifique que el rendimiento del cómputo preservador de la privacidad esté optimizado mediante agrupamiento, almacenamiento en caché y aceleración de hardware, mientras se mantienen las garantías de seguridad criptográfica.

---

### C4.15 Seguridad de Integración en la Nube del Marco de Agentes y Despliegue Híbrido

Controles de seguridad para marcos de agentes integrados en la nube con arquitecturas híbridas on-premises/nube.

 #4.15.1    Nivel: 1    Rol: D/V
 Verifique que la integración del almacenamiento en la nube utilice cifrado de extremo a extremo con gestión de claves controlada por el agente.
 #4.15.2    Nivel: 2    Rol: D/V
 Verifique que los límites de seguridad del despliegue híbrido estén claramente definidos con canales de comunicación encriptados.
 #4.15.3    Nivel: 2    Rol: D/V
 Verifique que el acceso a los recursos en la nube incluya verificación de confianza cero con autenticación continua.
 #4.15.4    Nivel: 3    Rol: D/V
 Verifique que los requisitos de residencia de datos se cumplan mediante la atestación criptográfica de las ubicaciones de almacenamiento.
 #4.15.5    Nivel: 3    Rol: D/V
 Verifique que las evaluaciones de seguridad del proveedor de la nube incluyan la modelización de amenazas específicas para agentes y la evaluación de riesgos.

---

### Referencias

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
NIST SP 800-190: Application Container Security Guide
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
NIST SP 800-53: Security Controls for Federal Information Systems
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework
CIS Kubernetes Benchmark
FIPS 140-2 Security Requirements
NIST SP 800-207: Zero Trust Architecture
IEEE 2857: Privacy Engineering for AI Systems
NIST SP 800-161: Cybersecurity Supply Chain Risk Management
NIST Post-Quantum Cryptography Standards
Intel SGX Developer Guide
AMD SEV-SNP White Paper
ARM TrustZone Technology
ZK-SNARKs: A Gentle Introduction
NIST SP 800-57: Cryptographic Key Management
Side-Channel Attack Countermeasures
Neuromorphic Computing Security Challenges
FPGA Security: Fundamentals, Evaluation, and Countermeasures
Microsoft SEAL: Homomorphic Encryption Library
HElib: Homomorphic Encryption Library
PALISADE Lattice Cryptography Library
Differential Privacy: A Survey of Results
Secure Aggregation for Federated Learning
Private Information Retrieval: Concepts and Constructions

## Control de acceso e identidad C5 para componentes y usuarios de IA

### Objetivo de Control

El control de acceso efectivo para sistemas de IA requiere una gestión de identidad robusta, autorización consciente del contexto y aplicación en tiempo de ejecución siguiendo los principios de confianza cero. Estos controles garantizan que humanos, servicios y agentes autónomos solo interactúen con modelos, datos y recursos computacionales dentro de los ámbitos explícitamente concedidos, con capacidades continuas de verificación y auditoría.

---

### C5.1 Gestión de Identidad y Autenticación

Establezca identidades respaldadas criptográficamente para todas las entidades con autenticación multifactor para operaciones privilegiadas.

 #5.1.1    Nivel: 1    Rol: D/V
 Verifique que todos los usuarios humanos y los principales de servicio se autentiquen a través de un proveedor de identidad empresarial centralizado (IdP) utilizando protocolos OIDC/SAML con asignaciones únicas de identidad a token (sin cuentas ni credenciales compartidas).
 #5.1.2    Nivel: 1    Rol: D/V
 Verifique que las operaciones de alto riesgo (despliegue de modelos, exportación de pesos, acceso a datos de entrenamiento, cambios en la configuración de producción) requieran autenticación multifactor o autenticación escalonada con revalidación de sesión.
 #5.1.3    Nivel: 2    Rol: D
 Verifique que los nuevos responsables pasen por un proceso de verificación de identidad alineado con NIST 800-63-3 IAL-2 o estándares equivalentes antes de recibir acceso al sistema de producción.
 #5.1.4    Nivel: 2    Rol: V
 Verifique que las revisiones de acceso se realicen trimestralmente con detección automatizada de cuentas inactivas, aplicación de rotación de credenciales y flujos de trabajo de desprovisión.
 #5.1.5    Nivel: 3    Rol: D/V
 Verifique que los agentes de IA federada se autentiquen mediante aserciones JWT firmadas que tengan una vida máxima de 24 horas e incluyan prueba criptográfica de origen.

---

### C5.2 Autorización de Recursos y Mínimo Privilegio

Implemente controles de acceso granulares para todos los recursos de IA con modelos de permiso explícitos y registros de auditoría.

 #5.2.1    Nivel: 1    Rol: D/V
 Verifique que cada recurso de IA (conjuntos de datos, modelos, puntos finales, colecciones vectoriales, índices de incrustación, instancias de cómputo) aplique controles de acceso basados en roles con listas de permitidos explícitas y políticas de denegación predeterminadas.
 #5.2.2    Nivel: 1    Rol: D/V
 Verifique que los principios de menor privilegio se apliquen de forma predeterminada con las cuentas de servicio, comenzando con permisos de solo lectura y que se requiera una justificación comercial documentada para el acceso de escritura.
 #5.2.3    Nivel: 1    Rol: V
 Verifique que todas las modificaciones de control de acceso estén vinculadas a solicitudes de cambio aprobadas y se registren de manera inmutable con marcas de tiempo, identidades de actores, identificadores de recursos y deltas de permisos.
 #5.2.4    Nivel: 2    Rol: D
 Verifique que las etiquetas de clasificación de datos (PII, PHI, controladas para exportación, propietarias) se propaguen automáticamente a los recursos derivados (embeddings, cachés de prompts, salidas del modelo) con una aplicación coherente de la política.
 #5.2.5    Nivel: 2    Rol: D/V
 Verifique que los intentos de acceso no autorizados y los eventos de escalamiento de privilegios generen alertas en tiempo real con metadatos contextuales hacia los sistemas SIEM dentro de 5 minutos.

---

### C5.3 Evaluación Dinámica de Políticas

Implemente motores de control de acceso basado en atributos (ABAC) para decisiones de autorización con conciencia contextual y capacidades de auditoría.

 #5.3.1    Nivel: 1    Rol: D/V
 Verifique que las decisiones de autorización estén externalizadas a un motor de políticas dedicado (OPA, Cedar o equivalente) accesible mediante APIs autenticadas con protección criptográfica de integridad.
 #5.3.2    Nivel: 1    Rol: D/V
 Verifique que las políticas evalúen atributos dinámicos en tiempo de ejecución, incluyendo el nivel de autorización del usuario, la clasificación de sensibilidad del recurso, el contexto de la solicitud, el aislamiento del inquilino y las restricciones temporales.
 #5.3.3    Nivel: 2    Rol: D
 Verifique que las definiciones de políticas estén controladas por versiones, revisadas por pares y validadas mediante pruebas automatizadas en las canalizaciones CI/CD antes del despliegue en producción.
 #5.3.4    Nivel: 2    Rol: V
 Verifique que los resultados de la evaluación de políticas incluyan razonamientos estructurados de decisión y se transmitan a los sistemas SIEM para análisis de correlación e informes de cumplimiento.
 #5.3.5    Nivel: 3    Rol: D/V
 Verifique que los valores de tiempo de vida (TTL) de la caché de políticas no excedan 5 minutos para recursos de alta sensibilidad y 1 hora para recursos estándar con capacidades de invalidación de caché.

---

### C5.4 Aplicación de Seguridad en Tiempo de Consulta

Implemente controles de seguridad a nivel de base de datos con filtrado obligatorio y políticas de seguridad a nivel de fila.

 #5.4.1    Nivel: 1    Rol: D/V
 Verifique que todas las consultas de bases de datos vectoriales y SQL incluyan filtros de seguridad obligatorios (ID de inquilino, etiquetas de sensibilidad, alcance del usuario) aplicados a nivel del motor de base de datos, no en el código de la aplicación.
 #5.4.2    Nivel: 1    Rol: D/V
 Verifique que las políticas de seguridad a nivel de fila (RLS) y el enmascaramiento a nivel de campo estén habilitados con herencia de políticas para todas las bases de datos vectoriales, índices de búsqueda y conjuntos de datos de entrenamiento.
 #5.4.3    Nivel: 2    Rol: D
 Verifique que las evaluaciones de autorización fallidas evitarán los "ataques de representante confundido" abortando inmediatamente las consultas y devolviendo códigos de error de autorización explícitos en lugar de devolver conjuntos de resultados vacíos.
 #5.4.4    Nivel: 2    Rol: V
 Verifique que la latencia en la evaluación de políticas se supervise de manera continua con alertas automatizadas para condiciones de tiempo de espera que podrían permitir la evasión de autorización.
 #5.4.5    Nivel: 3    Rol: D/V
 Verifique que los mecanismos de reintento de consultas vuelvan a evaluar las políticas de autorización para tener en cuenta los cambios dinámicos de permisos dentro de las sesiones activas de usuario.

---

### Filtrado de Salida C5.5 y Prevención de Pérdida de Datos

Implementar controles de postprocesamiento para prevenir la exposición no autorizada de datos en contenido generado por IA.

 #5.5.1    Nivel: 1    Rol: D/V
 Verifique que los mecanismos de filtrado posterior a la inferencia escaneen y redacten la información de identificación personal (PII) no autorizada, la información clasificada y los datos propietarios antes de entregar el contenido a los solicitantes.
 #5.5.2    Nivel: 1    Rol: D/V
 Verifique que las citas, referencias y atribuciones de fuente en las salidas del modelo sean validadas según los derechos del solicitante y se eliminen si se detecta acceso no autorizado.
 #5.5.3    Nivel: 2    Rol: D
 Verifique que se apliquen las restricciones de formato de salida (PDFs sanitizados, imágenes sin metadatos, tipos de archivo aprobados) según los niveles de permiso del usuario y las clasificaciones de datos.
 #5.5.4    Nivel: 2    Rol: V
 Verifique que los algoritmos de redacción sean deterministas, controlados por versiones y mantengan registros de auditoría para respaldar las investigaciones de cumplimiento y el análisis forense.
 #5.5.5    Nivel: 3    Rol: V
 Verifique que los eventos de redacción de alto riesgo generen registros adaptativos que incluyan hashes criptográficos del contenido original para su recuperación forense sin exponer datos.

---

### C5.6 Aislamiento Multiinquilino

Garantizar el aislamiento criptográfico y lógico entre inquilinos en la infraestructura de IA compartida.

 #5.6.1    Nivel: 1    Rol: D/V
 Verifique que los espacios de memoria, almacenes de incrustaciones, entradas de caché y archivos temporales estén segregados por espacio de nombres para cada inquilino con purga segura al eliminar el inquilino o al finalizar la sesión.
 #5.6.2    Nivel: 1    Rol: D/V
 Verifique que cada solicitud de API incluya un identificador de inquilino autenticado que sea validado criptográficamente contra el contexto de la sesión y los derechos del usuario.
 #5.6.3    Nivel: 2    Rol: D
 Verifique que las políticas de red implementen reglas de denegación predeterminada para la comunicación entre inquilinos dentro de mallas de servicio y plataformas de orquestación de contenedores.
 #5.6.4    Nivel: 3    Rol: D
 Verifique que las claves de cifrado sean únicas por inquilino con soporte de clave administrada por el cliente (CMK) y aislamiento criptográfico entre los almacenes de datos de los inquilinos.

---

### C5.7 Autorización de Agentes Autónomos

Controlar los permisos para agentes de IA y sistemas autónomos mediante tokens de capacidad delimitados y autorización continua.

 #5.7.1    Nivel: 1    Rol: D/V
 Verifique que los agentes autónomos reciban tokens de capacidad con alcance que enumeren explícitamente las acciones permitidas, los recursos accesibles, los límites de tiempo y las restricciones operativas.
 #5.7.2    Nivel: 1    Rol: D/V
 Verifique que las capacidades de alto riesgo (acceso al sistema de archivos, ejecución de código, llamadas a API externas, transacciones financieras) estén deshabilitadas por defecto y requieran autorizaciones explícitas para su activación con justificaciones comerciales.
 #5.7.3    Nivel: 2    Rol: D
 Verifique que los tokens de capacidad estén vinculados a las sesiones de usuario, incluyan protección de integridad criptográfica y aseguren que no puedan ser almacenados ni reutilizados en escenarios sin conexión.
 #5.7.4    Nivel: 2    Rol: V
 Verifique que las acciones iniciadas por el agente pasen por una autorización secundaria mediante el motor de políticas ABAC con evaluación de contexto completo y registro de auditoría.
 #5.7.5    Nivel: 3    Rol: V
 Verificar que las condiciones de error del agente y el manejo de excepciones incluyan información sobre el alcance de la capacidad para apoyar el análisis de incidentes y la investigación forense.

---

### Referencias

#### Estándares y Marcos de Trabajo

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Guías de Implementación

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### Seguridad específica de IA

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Seguridad de la cadena de suministro para modelos, frameworks y datos

### Objetivo de Control

Los ataques a la cadena de suministro de IA explotan modelos, marcos o conjuntos de datos de terceros para insertar puertas traseras, sesgos o código explotable. Estos controles proporcionan trazabilidad de extremo a extremo, gestión de vulnerabilidades y monitoreo para proteger todo el ciclo de vida del modelo.

---

### C6.1 Evaluación y Procedencia de Modelos Preentrenados

Evalúe y autentique los orígenes, licencias y comportamientos ocultos de modelos de terceros antes de cualquier ajuste fino o despliegue.

 #6.1.1    Nivel: 1    Rol: D/V
 Verifique que cada artefacto de modelo de terceros incluya un registro de procedencia firmado que identifique el repositorio de origen y el hash de commit.
 #6.1.2    Nivel: 1    Rol: D/V
 Verifique que los modelos sean escaneados en busca de capas maliciosas o gatillos Troyanos utilizando herramientas automatizadas antes de la importación.
 #6.1.3    Nivel: 2    Rol: D
 Verifique que el ajuste fino mediante transferencia de aprendizaje supere la evaluación adversarial para detectar comportamientos ocultos.
 #6.1.4    Nivel: 2    Rol: V
 Verifique que las licencias del modelo, las etiquetas de control de exportación y las declaraciones de origen de datos estén registradas en una entrada de ML-BOM.
 #6.1.5    Nivel: 3    Rol: D/V
 Verificar que los modelos de alto riesgo (pesos subidos públicamente, creadores no verificados) permanezcan en cuarentena hasta la revisión y aprobación humana.

---

### C6.2 Escaneo de Frameworks y Bibliotecas

Escanee continuamente los frameworks y bibliotecas de ML en busca de CVE y código malicioso para mantener segura la pila de ejecución.

 #6.2.1    Nivel: 1    Rol: D/V
 Verifique que las pipelines de CI ejecuten escáneres de dependencias en los frameworks de IA y las bibliotecas críticas.
 #6.2.2    Nivel: 1    Rol: D/V
 Verifique que las vulnerabilidades críticas (CVSS ≥ 7.0) bloqueen la promoción a imágenes de producción.
 #6.2.3    Nivel: 2    Rol: D
 Verifique que el análisis estático de código se ejecute en las bibliotecas de ML bifurcadas o incluidas.
 #6.2.4    Nivel: 2    Rol: V
 Verifique que las propuestas de actualización del framework incluyan una evaluación del impacto en la seguridad que haga referencia a fuentes públicas de CVE.
 #6.2.5    Nivel: 3    Rol: V
 Verifique que los sensores en tiempo de ejecución alerten sobre cargas inesperadas de bibliotecas dinámicas que se desvíen del SBOM firmado.

---

### C6.3 Fijación y Verificación de Dependencias

Fije cada dependencia a digests inmutables y reproduzca las compilaciones para garantizar artefactos idénticos y libres de manipulaciones.

 #6.3.1    Nivel: 1    Rol: D/V
 Verifique que todos los gestores de paquetes apliquen el fijado de versiones mediante archivos de bloqueo.
 #6.3.2    Nivel: 1    Rol: D/V
 Verifique que se utilicen resúmenes inmutables en lugar de etiquetas mutables en las referencias de contenedores.
 #6.3.3    Nivel: 2    Rol: D
 Verifique que las comprobaciones de compilación reproducible comparen hashes entre ejecuciones de CI para garantizar resultados idénticos.
 #6.3.4    Nivel: 2    Rol: V
 Verifique que las atestaciones de compilación se almacenen durante 18 meses para la trazabilidad de auditoría.
 #6.3.5    Nivel: 3    Rol: D
 Verifique que las dependencias caducadas desencadenen solicitudes de extracción automatizadas para actualizar o bifurcar versiones fijadas.

---

### C6.4 Aplicación de Fuente Confiable

Permitir descargas de artefactos solo desde fuentes aprobadas por la organización y verificadas criptográficamente, y bloquear todo lo demás.

 #6.4.1    Nivel: 1    Rol: D/V
 Verifique que los pesos del modelo, los conjuntos de datos y los contenedores se descarguen únicamente de dominios aprobados o registros internos.
 #6.4.2    Nivel: 1    Rol: D/V
 Verifique que las firmas de Sigstore/Cosign validen la identidad del editor antes de que los artefactos se almacenen en caché localmente.
 #6.4.3    Nivel: 2    Rol: D
 Verifique que los proxies de salida bloqueen las descargas de artefactos no autenticadas para hacer cumplir la política de fuente confiable.
 #6.4.4    Nivel: 2    Rol: V
 Verifique que las listas de permitidos del repositorio se revisen trimestralmente con evidencia de justificación comercial para cada entrada.
 #6.4.5    Nivel: 3    Rol: V
 Verifique que las violaciones de políticas desencadenen el aislamiento de artefactos y la reversión de las ejecuciones de canalizaciones dependientes.

---

### C6.5 Evaluación de Riesgos de Conjuntos de Datos de Terceros

Evaluar conjuntos de datos externos para detectar envenenamiento, sesgo y cumplimiento legal, y monitorearlos a lo largo de su ciclo de vida.

 #6.5.1    Nivel: 1    Rol: D/V
 Verifique que los conjuntos de datos externos sean sometidos a una puntuación de riesgo de envenenamiento (por ejemplo, huella digital de datos, detección de valores atípicos).
 #6.5.2    Nivel: 1    Rol: D
 Verifique que las métricas de sesgo (paridad demográfica, igualdad de oportunidad) se calculen antes de la aprobación del conjunto de datos.
 #6.5.3    Nivel: 2    Rol: V
 Verifique que el origen y los términos de licencia de los conjuntos de datos estén registrados en las entradas de ML‑BOM.
 #6.5.4    Nivel: 2    Rol: V
 Verifique que la monitorización periódica detecte deriva o corrupción en los conjuntos de datos alojados.
 #6.5.5    Nivel: 3    Rol: D
 Verifique que el contenido no permitido (derechos de autor, información personal identificable) se elimine mediante un proceso automatizado de limpieza antes del entrenamiento.

---

### C6.6 Monitoreo de Ataques a la Cadena de Suministro

Detecte las amenazas en la cadena de suministro de manera temprana mediante fuentes CVE, análisis de registros de auditoría y simulaciones de equipos rojos.

 #6.6.1    Nivel: 1    Rol: V
 Verifique que los registros de auditoría de CI/CD se transmitan a las detecciones SIEM para identificar extracciones anómalas de paquetes o pasos de compilación manipulados.
 #6.6.2    Nivel: 2    Rol: D
 Verifique que los libros de jugadas de respuesta a incidentes incluyan procedimientos de reversión para modelos o bibliotecas comprometidos.
 #6.6.3    Nivel: 3    Rol: V
 Verifique que el enriquecimiento de threat-intel etiquete indicadores específicos de ML (por ejemplo, IoCs de envenenamiento de modelos) en el triaje de alertas.

---

### C6.7 ML‑BOM para Artefactos del Modelo

Genere y firme SBOMs detallados específicos para ML (ML-BOMs) para que los consumidores posteriores puedan verificar la integridad del componente en el momento del despliegue.

 #6.7.1    Nivel: 1    Rol: D/V
 Verifique que cada artefacto del modelo publique un ML-BOM que liste conjuntos de datos, pesos, hiperparámetros y licencias.
 #6.7.2    Nivel: 1    Rol: D/V
 Verifique que la generación de ML‑BOM y la firma con Cosign estén automatizadas en CI y sean obligatorias para la fusión.
 #6.7.3    Nivel: 2    Rol: D
 Verifique que las comprobaciones de integridad de ML-BOM fracasen en la compilación si falta cualquier metadato del componente (hash, licencia).
 #6.7.4    Nivel: 2    Rol: V
 Verifique que los consumidores posteriores puedan consultar ML-BOMs a través de la API para validar los modelos importados en el momento del despliegue.
 #6.7.5    Nivel: 3    Rol: V
 Verifique que los ML‑BOMs estén controlados por versiones y comparados para detectar modificaciones no autorizadas.

---

### Referencias

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
AI & Transparency: Protect ML Models – ReversingLabs
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## Comportamiento del Modelo C7, Control de Salida y Aseguramiento de la Seguridad

### Objetivo de Control

Las salidas del modelo deben ser estructuradas, fiables, seguras, explicables y monitoreadas continuamente en producción. Hacerlo reduce alucinaciones, fugas de privacidad, contenido dañino y acciones fuera de control, mientras aumenta la confianza del usuario y el cumplimiento normativo.

---

### C7.1 Aplicación del formato de salida

Los esquemas estrictos, la decodificación restringida y la validación posterior detienen el contenido malformado o malicioso antes de que se propague.

 #7.1.1    Nivel: 1    Rol: D/V
 Verifique que los esquemas de respuesta (p. ej., JSON Schema) se proporcionen en el mensaje del sistema y que cada salida se valide automáticamente; las salidas que no cumplan con el esquema desencadenan reparación o rechazo.
 #7.1.2    Nivel: 1    Rol: D/V
 Verifique que la decodificación restringida (tokens de detención, expresiones regulares, máximo de tokens) esté habilitada para prevenir desbordamientos o canales laterales de inyección de indicaciones.
 #7.1.3    Nivel: 2    Rol: D/V
 Verifique que los componentes posteriores traten las salidas como no confiables y las validen contra esquemas o deserializadores seguros contra inyección.
 #7.1.4    Nivel: 3    Rol: V
 Verifique que los eventos de salida incorrecta estén registrados, limitados por tasa y visibles en el monitoreo.

---

### C7.2 Detección y Mitigación de Alucinaciones

La estimación de la incertidumbre y las estrategias de respaldo limitan las respuestas fabricadas.

 #7.2.1    Nivel: 1    Rol: D/V
 Verifique que las probabilidades logarítmicas a nivel de token, la auto-consistencia de conjunto, o los detectores de alucinaciones afinados asignen una puntuación de confianza a cada respuesta.
 #7.2.2    Nivel: 1    Rol: D/V
 Verifique que las respuestas por debajo de un umbral de confianza configurable activen flujos de trabajo de respaldo (por ejemplo, generación aumentada por recuperación, modelo secundario o revisión humana).
 #7.2.3    Nivel: 2    Rol: D/V
 Verifique que los incidentes de alucinación estén etiquetados con metadatos de causa raíz y sean enviados a las tuberías de post-mortem y ajuste fino.
 #7.2.4    Nivel: 3    Rol: D/V
 Verifique que los umbrales y detectores se recalibren después de actualizaciones importantes del modelo o de la base de conocimiento.
 #7.2.5    Nivel: 3    Rol: V
 Verifique que las visualizaciones del panel de control rastreen las tasas de alucinación.

---

### C7.3 Filtrado de Seguridad y Privacidad de Salida

Los filtros de políticas y la cobertura del equipo rojo protegen a los usuarios y datos confidenciales.

 #7.3.1    Nivel: 1    Rol: D/V
 Verifique que los clasificadores previos y posteriores a la generación bloqueen contenido de odio, acoso, autolesiones, extremista y sexualmente explícito alineado con la política.
 #7.3.2    Nivel: 1    Rol: D/V
 Verifique que la detección y redacción automática de PII/PCI se ejecuten en cada respuesta; las violaciones generan un incidente de privacidad.
 #7.3.3    Nivel: 2    Rol: D
 Verificar que las etiquetas de confidencialidad (por ejemplo, secretos comerciales) se propaguen a través de modalidades para evitar fugas en texto, imágenes o código.
 #7.3.4    Nivel: 3    Rol: D/V
 Verifique que los intentos de eludir el filtro o las clasificaciones de alto riesgo requieran una aprobación secundaria o la reautenticación del usuario.
 #7.3.5    Nivel: 3    Rol: D/V
 Verifique que los umbrales de filtrado reflejen las jurisdicciones legales y el contexto de edad/rol del usuario.

---

### C7.4 Limitación de Salida y Acción

Los límites de velocidad y las puertas de aprobación previenen el abuso y la autonomía excesiva.

 #7.4.1    Nivel: 1    Rol: D
 Verifique que las cuotas por usuario y por clave API limiten las solicitudes, los tokens y el costo con retroceso exponencial en errores 429.
 #7.4.2    Nivel: 1    Rol: D/V
 Verifique que las acciones privilegiadas (escritura de archivos, ejecución de código, llamadas de red) requieran aprobación basada en políticas o intervención humana.
 #7.4.3    Nivel: 2    Rol: D/V
 Verifique que las comprobaciones de consistencia cross-modal aseguren que las imágenes, el código y el texto generados para la misma solicitud no puedan usarse para introducir contenido malicioso.
 #7.4.4    Nivel: 2    Rol: D
 Verifique que la profundidad de delegación de agentes, los límites de recursión y las listas de herramientas permitidas estén configurados explícitamente.
 #7.4.5    Nivel: 3    Rol: V
 Verifique que la violación de los límites emita eventos de seguridad estructurados para la ingestión en SIEM.

---

### C7.5 Explicabilidad de la salida

Las señales transparentes mejoran la confianza del usuario y la depuración interna.

 #7.5.1    Nivel: 2    Rol: D/V
 Verifique que se muestren las puntuaciones de confianza visibles para el usuario o resúmenes breves de razonamiento cuando la evaluación de riesgos lo considere apropiado.
 #7.5.2    Nivel: 2    Rol: D/V
 Verifique que las explicaciones generadas eviten revelar indicaciones del sistema sensibles o datos propietarios.
 #7.5.3    Nivel: 3    Rol: D
 Verifique que el sistema capture las probabilidades logarítmicas a nivel de token o los mapas de atención y los almacene para su inspección autorizada.
 #7.5.4    Nivel: 3    Rol: V
 Verifique que los artefactos de explicabilidad estén controlados por versiones junto con las versiones del modelo para garantizar la auditabilidad.

---

### C7.6 Integración de Monitoreo

La observabilidad en tiempo real cierra el ciclo entre el desarrollo y la producción.

 #7.6.1    Nivel: 1    Rol: D
 Verifique que las métricas (violaciones de esquema, tasa de alucinaciones, toxicidad, filtraciones de información personal identificable, latencia, costo) se transmitan a una plataforma central de monitoreo.
 #7.6.2    Nivel: 1    Rol: V
 Verifique que se definan umbrales de alerta para cada métrica de seguridad, con rutas de escalamiento para el personal de guardia.
 #7.6.3    Nivel: 2    Rol: V
 Verifique que los paneles correlacionen las anomalías de salida con el modelo/versión, la bandera de función y los cambios en los datos ascendentes.
 #7.6.4    Nivel: 2    Rol: D/V
 Verifique que los datos de monitoreo se retroalimenten en el reentrenamiento, ajuste fino o actualizaciones de reglas dentro de un flujo de trabajo de MLOps documentado.
 #7.6.5    Nivel: 3    Rol: V
 Verifique que las canalizaciones de monitoreo estén sometidas a pruebas de penetración y control de acceso para evitar la filtración de registros sensibles.

---

### 7.7 Salvaguardias para Medios Generativos

Asegurar que los sistemas de IA no generen contenido mediático ilegal, dañino o no autorizado mediante la aplicación de restricciones de políticas, validación de salida y trazabilidad.

 #7.7.1    Nivel: 1    Rol: D/V
 Verifique que las indicaciones del sistema y las instrucciones al usuario prohíban explícitamente la generación de medios deepfake ilegales, dañinos o no consentidos (por ejemplo, imagen, video, audio).
 #7.7.2    Nivel: 2    Rol: D/V
 Verifique que las indicaciones sean filtradas para evitar intentos de generar suplantaciones, deepfakes sexualmente explícitos o medios que representen a individuos reales sin su consentimiento.
 #7.7.3    Nivel: 2    Rol: V
 Verifique que el sistema utilice hash perceptual, detección de marca de agua o huellas digitales para evitar la reproducción no autorizada de medios con derechos de autor.
 #7.7.4    Nivel: 3    Rol: D/V
 Verifique que todos los medios generados estén firmados criptográficamente, marcados con una marca de agua o incorporados con metadatos de procedencia resistentes a manipulaciones para la trazabilidad posterior.
 #7.7.5    Nivel: 3    Rol: V
 Verifique que los intentos de evasión (por ejemplo, ofuscación de indicaciones, jerga, formulaciones adversariales) sean detectados, registrados y limitados en frecuencia; el abuso repetido se informe a los sistemas de monitoreo.

### Referencias

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Improper Output Handling – OWASP LLM05:2025
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
LLM Red-Teaming Guide
Sensitive Information Disclosure in LLMs
LangChain – Chat Model Rate Limiting
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## Seguridad de Memoria C8, Embeddings y Bases de Datos Vectoriales

### Objetivo de Control

Las incrustaciones y los almacenes vectoriales actúan como la "memoria activa" de los sistemas de IA contemporáneos, aceptando continuamente datos proporcionados por el usuario y mostrándolos nuevamente en los contextos del modelo a través de la Generación Aumentada por Recuperación (RAG, por sus siglas en inglés). Si no se gobierna adecuadamente, esta memoria puede filtrar información personal identificable (PII), violar el consentimiento o ser invertida para reconstruir el texto original. El objetivo de esta familia de controles es fortalecer las canalizaciones de memoria y las bases de datos vectoriales para que el acceso sea de mínimo privilegio, las incrustaciones preserven la privacidad, los vectores almacenados expiren o puedan ser revocados bajo demanda, y que la memoria por usuario nunca contamine las indicaciones o respuestas de otro usuario.

---

### C8.1 Controles de Acceso en Memoria e Índices RAG

Aplicar controles de acceso detallados en cada colección vectorial.

 #8.1.1    Nivel: 1    Rol: D/V
 Verifique que las reglas de control de acceso a nivel de fila/espacio de nombres restrinjan las operaciones de inserción, eliminación y consulta por inquilino, colección o etiqueta de documento.
 #8.1.2    Nivel: 1    Rol: D/V
 Verifique que las claves API o los JWT contengan reclamaciones con ámbito específico (por ejemplo, ID de colecciones, verbos de acción) y se roten al menos trimestralmente.
 #8.1.3    Nivel: 2    Rol: D/V
 Verifique que los intentos de escalamiento de privilegios (por ejemplo, consultas de similitud entre espacios de nombres) sean detectados y registrados en un SIEM dentro de los 5 minutos.
 #8.1.4    Nivel: 2    Rol: D/V
 Verifique que la base de datos vectorial registre en los auditorías el identificador del sujeto, la operación, el ID/espacio de nombres del vector, el umbral de similitud y el recuento de resultados.
 #8.1.5    Nivel: 3    Rol: V
 Verifique que las decisiones de acceso se prueben en busca de fallas de omisión siempre que se actualicen los motores o cambien las reglas de partición de índices.

---

### C8.2 Saneamiento y Validación de Embebidos

Preseleccionar texto para información de identificación personal (PII), redactar o seudonimizar antes de la vectorización, y opcionalmente posprocesar los embeddings para eliminar señales residuales.

 #8.2.1    Nivel: 1    Rol: D/V
 Verifique que los datos PII y regulados sean detectados mediante clasificadores automatizados y enmascarados, tokenizados o eliminados antes del embedding.
 #8.2.2    Nivel: 1    Rol: D
 Verifique que las canalizaciones de incrustación rechacen o pongan en cuarentena las entradas que contengan código ejecutable o artefactos no UTF-8 que puedan contaminar el índice.
 #8.2.3    Nivel: 2    Rol: D/V
 Verificar que se aplique sanitización de privacidad diferencial local o métrica a las incrustaciones de oraciones cuya distancia a cualquier token PII conocido caiga por debajo de un umbral configurable.
 #8.2.4    Nivel: 2    Rol: V
 Verifique que la eficacia de la sanitización (por ejemplo, el recall de la redacción de PII, la deriva semántica) se valide al menos de forma semestral contra corpus de referencia.
 #8.2.5    Nivel: 3    Rol: D/V
 Verifique que las configuraciones de saneamiento estén controladas por versiones y que los cambios sean revisados por pares.

---

### C8.3 Expiración, Revocación y Eliminación de Memoria

El GDPR "derecho al olvido" y leyes similares requieren la eliminación oportuna; por lo tanto, los almacenes de vectores deben soportar TTLs, eliminaciones definitivas y tomb-stoning para que los vectores revocados no puedan ser recuperados ni reindexados.

 #8.3.1    Nivel: 1    Rol: D/V
 Verifique que cada vector y registro de metadatos tenga un TTL o una etiqueta de retención explícita respetada por los trabajos de limpieza automatizados.
 #8.3.2    Nivel: 1    Rol: D/V
 Verifique que las solicitudes de eliminación iniciadas por el usuario eliminen los vectores, metadatos, copias de caché e índices derivados dentro de los 30 días.
 #8.3.3    Nivel: 2    Rol: D
 Verifique que las eliminaciones lógicas sean seguidas por el borrado criptográfico de los bloques de almacenamiento si el hardware lo soporta, o por la destrucción de la clave del almacén de claves.
 #8.3.4    Nivel: 3    Rol: D/V
 Verifique que los vectores expirados estén excluidos de los resultados de la búsqueda de vecinos más cercanos en menos de 500 ms después de la expiración.

---

### C8.4 Prevenir la inversión y fuga de incrustaciones

Las defensas recientes—superposición de ruido, redes de proyección, perturbación de neuronas de privacidad y cifrado a nivel de capa de aplicación—pueden reducir las tasas de inversión a nivel de token por debajo del 5%.

 #8.4.1    Nivel: 1    Rol: V
 Verifique que exista un modelo de amenaza formal que cubra ataques de inversión, membresía e inferencia de atributos y que se revise anualmente.
 #8.4.2    Nivel: 2    Rol: D/V
 Verifique que el cifrado a nivel de aplicación o el cifrado consultable protejan los vectores contra lecturas directas por parte de los administradores de infraestructura o el personal de la nube.
 #8.4.3    Nivel: 3    Rol: V
 Verifique que los parámetros de defensa (ε para DP, ruido σ, rango de proyección k) equilibren la privacidad ≥ 99 % de protección de tokens y la utilidad ≤ 3 % de pérdida de precisión.
 #8.4.4    Nivel: 3    Rol: D/V
 Verifique que las métricas de resistencia a la inversión formen parte de los criterios de liberación para las actualizaciones del modelo, con presupuestos de regresión definidos.

---

### C8.5 Aplicación del Ámbito para la Memoria Específica del Usuario

La filtración entre inquilinos sigue siendo un riesgo principal de RAG: las consultas de similitud mal filtradas pueden exponer documentos privados de otro cliente.

 #8.5.1    Nivel: 1    Rol: D/V
 Verifique que cada consulta de recuperación sea filtrada posteriormente por el ID del inquilino/usuario antes de ser pasada al prompt del LLM.
 #8.5.2    Nivel: 1    Rol: D
 Verifique que los nombres de las colecciones o los IDs con espacio de nombres estén salados por usuario o inquilino para que los vectores no puedan colisionar entre ámbitos.
 #8.5.3    Nivel: 2    Rol: D/V
 Verifique que los resultados de similitud por encima de un umbral de distancia configurable pero fuera del alcance del llamador sean descartados y generen alertas de seguridad.
 #8.5.4    Nivel: 2    Rol: V
 Verifique que las pruebas de estrés multiinquilino simulen consultas adversariales que intentan recuperar documentos fuera del alcance y demuestren ausencia total de filtración.
 #8.5.5    Nivel: 3    Rol: D/V
 Verifique que las claves de cifrado estén segregadas por inquilino, asegurando el aislamiento criptográfico incluso si el almacenamiento físico es compartido.

---

### C8.6 Seguridad avanzada del sistema de memoria

Controles de seguridad para arquitecturas de memoria sofisticadas que incluyen memoria episódica, semántica y de trabajo con requisitos específicos de aislamiento y validación.

 #8.6.1    Nivel: 1    Rol: D/V
 Verifique que los diferentes tipos de memoria (episódica, semántica, de trabajo) tengan contextos de seguridad aislados con controles de acceso basados en roles, claves de cifrado separadas y patrones de acceso documentados para cada tipo de memoria.
 #8.6.2    Nivel: 2    Rol: D/V
 Verifique que los procesos de consolidación de memoria incluyan validación de seguridad para prevenir la inyección de memorias maliciosas mediante la sanitización de contenido, la verificación de la fuente y las comprobaciones de integridad antes del almacenamiento.
 #8.6.3    Nivel: 2    Rol: D/V
 Verifique que las consultas de recuperación de memoria sean validadas y limpiadas para prevenir la extracción de información no autorizada mediante el análisis de patrones de consulta, la aplicación de control de acceso y el filtrado de resultados.
 #8.6.4    Nivel: 3    Rol: D/V
 Verifique que los mecanismos de olvido de memoria eliminen de forma segura la información sensible con garantías de borrado criptográfico mediante la eliminación de clave, sobreescritura múltiple o eliminación segura basada en hardware con certificados de verificación.
 #8.6.5    Nivel: 3    Rol: D/V
 Verifique que la integridad del sistema de memoria sea monitoreada continuamente para detectar modificaciones o corrupciones no autorizadas mediante sumas de verificación, registros de auditoría y alertas automatizadas cuando el contenido de la memoria cambie fuera de las operaciones normales.

---

### Referencias

Vector database security: Pinecone – IronCore Labs
Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera
Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances
Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv
DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview
Art. 17 GDPR – Right to Erasure
Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai
PII Identification and Removal – NVIDIA NeMo Docs
De-identifying Sensitive Data – Google Cloud DLP
Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails
Think Your RAG Is Secure? Think Again – Medium
Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn
Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog

## 9 Orquestación Autónoma y Seguridad de Acción Agente

### Objetivo de Control

Asegurar que los sistemas de IA autónomos o multiagente solo puedan ejecutar acciones que sean explícitamente intencionadas, autenticadas, auditables y dentro de los umbrales de costo y riesgo delimitados. Esto protege contra amenazas como el compromiso del sistema autónomo, el uso indebido de herramientas, la detección de bucles de agentes, el secuestro de comunicaciones, la suplantación de identidad, la manipulación de enjambres y la manipulación de intenciones.

---

### 9.1 Presupuestos de Planificación de Tareas de Agentes y Recursión

Regule los planes recursivos y obligue a puntos de control humanos para acciones privilegiadas.

 #9.1.1    Nivel: 1    Rol: D/V
 Verifique que la profundidad máxima de recursión, amplitud, tiempo de reloj de pared, tokens y costo monetario por ejecución de agente estén configurados de manera centralizada y controlados por versiones.
 #9.1.2    Nivel: 1    Rol: D/V
 Verifique que las acciones privilegiadas o irreversibles (por ejemplo, compromisos de código, transferencias financieras) requieran aprobación humana explícita a través de un canal auditable antes de su ejecución.
 #9.1.3    Nivel: 2    Rol: D
 Verifique que los monitores de recursos en tiempo real activan la interrupción del disyuntor cuando se supera cualquier umbral de presupuesto, deteniendo la expansión adicional de tareas.
 #9.1.4    Nivel: 2    Rol: D/V
 Verifique que los eventos del interruptor automático se registren con la ID del agente, la condición que lo activó y el estado del plan capturado para su revisión forense.
 #9.1.5    Nivel: 3    Rol: V
 Verifique que las pruebas de seguridad cubran escenarios de agotamiento del presupuesto y planes descontrolados, confirmando una detención segura sin pérdida de datos.
 #9.1.6    Nivel: 3    Rol: D
 Verifique que las políticas presupuestarias estén expresadas como política-como-código y se apliquen en CI/CD para bloquear la desviación de configuración.

---

### 9.2 Aislamiento de Complementos de Herramientas

Aísle las interacciones de la herramienta para prevenir el acceso no autorizado al sistema o la ejecución de código.

 #9.2.1    Nivel: 1    Rol: D/V
 Verifique que cada herramienta/plugin se ejecute dentro de un sistema operativo, contenedor o sandbox a nivel WASM con políticas de sistema de archivos, red y llamadas al sistema de menor privilegio.
 #9.2.2    Nivel: 1    Rol: D/V
 Verifique que las cuotas de recursos del sandbox (CPU, memoria, disco, salida de red) y los tiempos de espera de ejecución se apliquen y registren.
 #9.2.3    Nivel: 2    Rol: D/V
 Verifique que los binarios o descriptores de la herramienta estén firmados digitalmente; las firmas se validan antes de la carga.
 #9.2.4    Nivel: 2    Rol: V
 Verifique que la telemetría del sandbox se envíe a un SIEM; las anomalías (por ejemplo, intentos de conexiones salientes) generan alertas.
 #9.2.5    Nivel: 3    Rol: V
 Verifique que los plugins de alto riesgo sean sometidos a una revisión de seguridad y pruebas de penetración antes del despliegue en producción.
 #9.2.6    Nivel: 3    Rol: D/V
 Verifique que los intentos de escape del sandbox se bloqueen automáticamente y que el complemento infractor sea puesto en cuarentena hasta que se realice una investigación.

---

### 9.3 Bucle Autónomo y Limitación de Costos

Detectar y detener la recursión incontrolada entre agentes y las explosiones de costos.

 #9.3.1    Nivel: 1    Rol: D/V
 Verifique que las llamadas entre agentes incluyan un límite de saltos o TTL que el tiempo de ejecución decrementa y hace cumplir.
 #9.3.2    Nivel: 2    Rol: D
 Verifique que los agentes mantengan un ID único de grafo de invocación para detectar auto-invocaciones o patrones cíclicos.
 #9.3.3    Nivel: 2    Rol: D/V
 Verifique que los contadores acumulativos de unidades de cómputo y gasto se registren por cadena de solicitud; exceder el límite aborta la cadena.
 #9.3.4    Nivel: 3    Rol: V
 Verifique que el análisis formal o la verificación mediante modelos demuestren la ausencia de recursión ilimitada en los protocolos de agentes.
 #9.3.5    Nivel: 3    Rol: D
 Verificar que los eventos de abortar bucle generen alertas y alimenten métricas de mejora continua.

---

### 9.4 Protección contra el Mal Uso a Nivel de Protocolo

Canales de comunicación seguros entre agentes y sistemas externos para prevenir secuestros o manipulaciones.

 #9.4.1    Nivel: 1    Rol: D/V
 Verifique que todos los mensajes de agente a herramienta y de agente a agente estén autenticados (por ejemplo, TLS mutuo o JWT) y cifrados de extremo a extremo.
 #9.4.2    Nivel: 1    Rol: D
 Verifique que los esquemas sean validados estrictamente; los campos desconocidos o los mensajes mal formados sean rechazados.
 #9.4.3    Nivel: 2    Rol: D/V
 Verifique que las comprobaciones de integridad (MAC o firmas digitales) cubran todo el contenido del mensaje, incluidos los parámetros de la herramienta.
 #9.4.4    Nivel: 2    Rol: D
 Verifique que la protección contra reproducciones (nonces o ventanas de marcas de tiempo) se aplique en la capa del protocolo.
 #9.4.5    Nivel: 3    Rol: V
 Verifique que las implementaciones del protocolo se sometan a fuzzing y análisis estático para detectar fallas de inyección o deserialización.

---

### 9.5 Identidad del Agente y Evidencia de Manipulación

Asegurar que las acciones sean atribuibles y que las modificaciones sean detectables.

 #9.5.1    Nivel: 1    Rol: D/V
 Verifique que cada instancia de agente posea una identidad criptográfica única (par de claves o credencial basada en hardware).
 #9.5.2    Nivel: 2    Rol: D/V
 Verifique que todas las acciones del agente estén firmadas y con sello de tiempo; los registros incluyan la firma para evitar la repudiación.
 #9.5.3    Nivel: 2    Rol: V
 Verifique que los registros a prueba de manipulaciones se almacenen en un medio de solo adición o de escritura única.
 #9.5.4    Nivel: 3    Rol: D
 Verifique que las claves de identidad roten según un cronograma definido y en presencia de indicadores de compromiso.
 #9.5.5    Nivel: 3    Rol: D/V
 Verifique que los intentos de suplantación o conflicto de claves desencadenen la cuarentena inmediata del agente afectado.

---

### 9.6 Reducción de Riesgos en Enjambres Multi-Agente

Mitigue los riesgos del comportamiento colectivo mediante aislamiento y modelado formal de seguridad.

 #9.6.1    Nivel: 1    Rol: D/V
 Verifique que los agentes que operan en diferentes dominios de seguridad se ejecuten en sandboxes de tiempo de ejecución aislados o en segmentos de red.
 #9.6.2    Nivel: 3    Rol: V
 Verifique que los comportamientos en enjambre estén modelados y verificados formalmente para vivacidad y seguridad antes del despliegue.
 #9.6.3    Nivel: 3    Rol: D
 Verifique que los monitores en tiempo de ejecución detecten patrones emergentes inseguros (por ejemplo, oscilaciones, bloqueos) e inicien acciones correctivas.

---

### 9.7 Autenticación / Autorización de Usuario y Herramienta

Implemente controles de acceso robustos para cada acción desencadenada por un agente.

 #9.7.1    Nivel: 1    Rol: D/V
 Verifique que los agentes se autentiquen como principales de primera clase ante los sistemas descendentes, sin reutilizar nunca las credenciales del usuario final.
 #9.7.2    Nivel: 2    Rol: D
 Verifique que las políticas de autorización detalladas restrinjan qué herramientas puede invocar un agente y qué parámetros puede suministrar.
 #9.7.3    Nivel: 2    Rol: V
 Verifique que las comprobaciones de privilegios se reevaluén en cada llamada (autorización continua), no solo al inicio de la sesión.
 #9.7.4    Nivel: 3    Rol: D
 Verifique que los privilegios delegados expiren automáticamente y requieran nuevo consentimiento después del tiempo de espera o cambio de alcance.

---

### 9.8 Seguridad en la Comunicación de Agente a Agente

Cifre y proteja la integridad de todos los mensajes entre agentes para evitar la intercepción y la manipulación.

 #9.8.1    Nivel: 1    Rol: D/V
 Verifique que la autenticación mutua y el cifrado con secreto perfecto hacia adelante (por ejemplo, TLS 1.3) sean obligatorios para los canales de agentes.
 #9.8.2    Nivel: 1    Rol: D
 Verifique que la integridad y el origen del mensaje se validen antes de procesarlo; las fallas generan alertas y descartan el mensaje.
 #9.8.3    Nivel: 2    Rol: D/V
 Verifique que los metadatos de comunicación (marcas de tiempo, números de secuencia) se registren para apoyar la reconstrucción forense.
 #9.8.4    Nivel: 3    Rol: V
 Verifique que la verificación formal o la comprobación de modelos confirme que las máquinas de estado del protocolo no pueden conducir a estados inseguros.

---

### 9.9 Verificación de Intención y Aplicación de Restricciones

Validar que las acciones del agente se alineen con la intención declarada del usuario y las restricciones del sistema.

 #9.9.1    Nivel: 1    Rol: D
 Verifique que los solucionadores de restricciones previas a la ejecución comprueben las acciones propuestas contra las reglas de seguridad y políticas codificadas.
 #9.9.2    Nivel: 2    Rol: D/V
 Verifique que las acciones de alto impacto (financieras, destructivas, sensibles a la privacidad) requieran una confirmación explícita de la intención por parte del usuario que las inicia.
 #9.9.3    Nivel: 2    Rol: V
 Verifique que las comprobaciones de postcondición validen que las acciones completadas lograron los efectos previstos sin efectos secundarios; las discrepancias activan la reversión.
 #9.9.4    Nivel: 3    Rol: V
 Verifique que los métodos formales (por ejemplo, verificación de modelos, demostración de teoremas) o las pruebas basadas en propiedades demuestren que los planes de los agentes cumplen con todas las restricciones declaradas.
 #9.9.5    Nivel: 3    Rol: D
 Verifique que los incidentes de desajuste de intención o violación de restricciones alimenten los ciclos de mejora continua y el intercambio de inteligencia sobre amenazas.

---

### 9.10 Seguridad de la Estrategia de Razonamiento del Agente

Selección y ejecución segura de diferentes estrategias de razonamiento, incluyendo los enfoques ReAct, Cadena-de-Pensamiento, y Árbol-de-Pensamientos.

 #9.10.1    Nivel: 1    Rol: D/V
 Verifique que la selección de la estrategia de razonamiento utilice criterios deterministas (complejidad de entrada, tipo de tarea, contexto de seguridad) y que entradas idénticas produzcan selecciones de estrategia idénticas dentro del mismo contexto de seguridad.
 #9.10.2    Nivel: 1    Rol: D/V
 Verifique que cada estrategia de razonamiento (ReAct, Cadena de Pensamiento, Árbol de Pensamientos) tenga validación de entrada dedicada, saneamiento de salida y límites de tiempo de ejecución específicos para su enfoque cognitivo.
 #9.10.3    Nivel: 2    Rol: D/V
 Verifique que las transiciones de la estrategia de razonamiento se registren con contexto completo, incluyendo las características de entrada, los valores de los criterios de selección y los metadatos de ejecución para la reconstrucción de la pista de auditoría.
 #9.10.4    Nivel: 2    Rol: D/V
 Verifique que el razonamiento de Árbol de Pensamientos incluya mecanismos de poda de ramas que terminen la exploración cuando se detecten violaciones de políticas, límites de recursos o fronteras de seguridad.
 #9.10.5    Nivel: 2    Rol: D/V
 Verifique que los ciclos ReAct (Razonar-Actuar-Observar) incluyan puntos de control de validación en cada fase: verificación del paso de razonamiento, autorización de la acción y saneamiento de la observación antes de proceder.
 #9.10.6    Nivel: 3    Rol: D/V
 Verifique que las métricas de rendimiento de la estrategia de razonamiento (tiempo de ejecución, uso de recursos, calidad de salida) se supervisen con alertas automáticas cuando las métricas se desvíen más allá de los umbrales configurados.
 #9.10.7    Nivel: 3    Rol: D/V
 Verifique que los enfoques de razonamiento híbridos que combinan múltiples estrategias mantengan la validación de entrada y las restricciones de salida de todas las estrategias constituyentes sin evadir ningún control de seguridad.
 #9.10.8    Nivel: 3    Rol: D/V
 Verifique que la prueba de seguridad de la estrategia de razonamiento incluya fuzzing con entradas malformadas, indicaciones adversariales diseñadas para forzar el cambio de estrategia y pruebas de condiciones límite para cada enfoque cognitivo.

---

### 9.11 Gestión del Estado del Ciclo de Vida del Agente y Seguridad

Inicialización segura del agente, transiciones de estado y terminación con registros criptográficos de auditoría y procedimientos de recuperación definidos.

 #9.11.1    Nivel: 1    Rol: D/V
 Verifique que la inicialización del agente incluya el establecimiento de identidad criptográfica con credenciales respaldadas por hardware y registros de auditoría de arranque inmutables que contengan ID del agente, marca de tiempo, hash de configuración y parámetros de inicialización.
 #9.11.2    Nivel: 2    Rol: D/V
 Verifique que las transiciones de estado del agente estén firmadas criptográficamente, con sello de tiempo y registradas con contexto completo que incluya eventos desencadenantes, hash del estado anterior, hash del nuevo estado y validaciones de seguridad realizadas.
 #9.11.3    Nivel: 2    Rol: D/V
 Verifique que los procedimientos de apagado del agente incluyan el borrado seguro de memoria mediante eliminación criptográfica o sobrescritura múltiple, la revocación de credenciales con notificación a la autoridad certificadora, y la generación de certificados de terminación a prueba de manipulaciones.
 #9.11.4    Nivel: 3    Rol: D/V
 Verificar que los mecanismos de recuperación del agente validen la integridad del estado utilizando sumas de verificación criptográficas (mínimo SHA-256) y retrocedan a estados conocidos como buenos cuando se detecte corrupción, con alertas automatizadas y requisitos de aprobación manual.
 #9.11.5    Nivel: 3    Rol: D/V
 Verifique que los mecanismos de persistencia del agente cifren los datos de estado sensibles con claves AES-256 por agente e implementen una rotación segura de claves en horarios configurables (máximo 90 días) con despliegue sin tiempo de inactividad.

---

### 9.12 Marco de Seguridad para la Integración de Herramientas

Controles de seguridad para la carga dinámica de herramientas, ejecución y validación de resultados con procesos definidos de evaluación de riesgos y aprobación.

 #9.12.1    Nivel: 1    Rol: D/V
 Verifique que los descriptores de herramientas incluyan metadatos de seguridad que especifiquen los privilegios requeridos (lectura/escritura/ejecución), niveles de riesgo (bajo/medio/alto), límites de recursos (CPU, memoria, red) y los requisitos de validación documentados en los manifiestos de las herramientas.
 #9.12.2    Nivel: 1    Rol: D/V
 Verifique que los resultados de la ejecución de herramientas se validen contra esquemas esperados (JSON Schema, XML Schema) y políticas de seguridad (saneamiento de salida, clasificación de datos) antes de la integración, con límites de tiempo y procedimientos de manejo de errores.
 #9.12.3    Nivel: 2    Rol: D/V
 Verifique que los registros de interacción de la herramienta incluyan un contexto de seguridad detallado que abarque el uso de privilegios, patrones de acceso a datos, tiempo de ejecución, consumo de recursos y códigos de retorno, con un registro estructurado para la integración con SIEM.
 #9.12.4    Nivel: 2    Rol: D/V
 Verifique que los mecanismos de carga dinámica de herramientas validen las firmas digitales utilizando la infraestructura PKI e implementen protocolos de carga seguros con aislamiento en sandbox y verificación de permisos antes de la ejecución.
 #9.12.5    Nivel: 3    Rol: D/V
 Verifique que las evaluaciones de seguridad de las herramientas se activen automáticamente para nuevas versiones con puertas de aprobación obligatorias que incluyan análisis estático, pruebas dinámicas y revisión por parte del equipo de seguridad, con criterios de aprobación documentados y requisitos de SLA.

---

#### Referencias

MITRE ATLAS tactics ML09
Circuit-breaker research for AI agents — Zou et al., 2024
Trend Micro analysis of sandbox escapes in AI agents — Park, 2025
Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025
Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025
Rapid7 fundamentals on spoofing attack prevention — 2024
Imperial College verification of swarm systems — Lomuscio et al.
NIST AI Risk Management Framework 1.0, 2023
WIRED security briefing on encryption best practices, 2024
OWASP Top 10 for LLM Applications, 2025
Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS
[How Is LLM Reasoning Distracted by Irrelevant Context?
An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
Large Language Model Sentinel: LLM Agent for Adversarial Purification
Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents

## 10 Robustez adversarial y defensa de la privacidad

### Objetivo de Control

Asegurar que los modelos de IA sigan siendo confiables, que respeten la privacidad y que sean resistentes al abuso cuando enfrentan ataques de evasión, inferencia, extracción o envenenamiento.

---

### 10.1 Alineación y Seguridad del Modelo

Protéjase contra salidas dañinas o que violen las políticas.

 #10.1.1    Nivel: 1    Rol: D/V
 Verifique que un conjunto de pruebas de alineación (prompts de red-team, sondeos de jailbreak, contenido no permitido) esté controlado por versiones y se ejecute en cada lanzamiento de modelo.
 #10.1.2    Nivel: 1    Rol: D
 Verifique que se apliquen las medidas de seguridad de rechazo y finalización segura.
 #10.1.3    Nivel: 2    Rol: D/V
 Verifique que un evaluador automatizado mida la tasa de contenido dañino y marque regresiones que superen un umbral establecido.
 #10.1.4    Nivel: 2    Rol: D
 Verifique que el entrenamiento contra jailbreak esté documentado y sea reproducible.
 #10.1.5    Nivel: 3    Rol: V
 Verifique que las pruebas formales de cumplimiento de políticas o la supervisión certificada cubran dominios críticos.

---

### 10.2 Endurecimiento contra Ejemplos Adversariales

Aumentar la resiliencia frente a entradas manipuladas. El entrenamiento adversarial robusto y la puntuación de referencia son la mejor práctica actual.

 #10.2.1    Nivel: 1    Rol: D
 Verifique que los repositorios del proyecto incluyan configuraciones de entrenamiento adversarial con semillas reproducibles.
 #10.2.2    Nivel: 2    Rol: D/V
 Verifique que la detección de ejemplos adversariales genere alertas de bloqueo en las canalizaciones de producción.
 #10.2.4    Nivel: 3    Rol: V
 Verifique que las pruebas de robustez certificada o los certificados de límites de intervalo cubran al menos las principales clases críticas.
 #10.2.5    Nivel: 3    Rol: V
 Verifique que las pruebas de regresión utilicen ataques adaptativos para confirmar que no haya pérdida de robustez medible.

---

### 10.3 Mitigación de Inferencias de Membresía

Limitar la capacidad de decidir si un registro formó parte de los datos de entrenamiento. La privacidad diferencial y el enmascaramiento de la puntuación de confianza siguen siendo las defensas conocidas más efectivas.

 #10.3.1    Nivel: 1    Rol: D
 Verifique que la regularización de entropía por consulta o el escalado de temperatura reducen las predicciones sobreconfidentes.
 #10.3.2    Nivel: 2    Rol: D
 Verifique que el entrenamiento emplea optimización diferencialmente privada acotada por ε para conjuntos de datos sensibles.
 #10.3.3    Nivel: 2    Rol: V
 Verifique que las simulaciones de ataque (modelo sombra o caja negra) muestren un AUC de ataque ≤ 0.60 en datos reservados.

---

### 10.4 Resistencia a la inversión de modelos

Prevenir la reconstrucción de atributos privados. Encuestas recientes enfatizan la truncación de salida y las garantías de DP como defensas prácticas.

 #10.4.1    Nivel: 1    Rol: D
 Verifique que los atributos sensibles nunca se muestren directamente; cuando sea necesario, utilice categorías o transformaciones unidireccionales.
 #10.4.2    Nivel: 1    Rol: D/V
 Verifique que los límites de tasa de consulta regulen las consultas adaptativas repetidas del mismo principal.
 #10.4.3    Nivel: 2    Rol: D
 Verifique que el modelo esté entrenado con ruido que preserve la privacidad.

---

### 10.5 Defensa contra la extracción de modelos

Detectar y disuadir la clonación no autorizada. Se recomiendan el marcado con marca de agua y el análisis de patrones de consulta.

 #10.5.1    Nivel: 1    Rol: D
 Verifique que las pasarelas de inferencia apliquen límites de tasa globales y por clave API ajustados al umbral de memorización del modelo.
 #10.5.2    Nivel: 2    Rol: D/V
 Verifique que las estadísticas de query-entropy y input-plurality alimenten un detector de extracción automatizado.
 #10.5.3    Nivel: 2    Rol: V
 Verifique que las marcas de agua frágiles o probabilísticas puedan demostrarse con p < 0.01 en ≤ 1 000 consultas contra un clon sospechoso.
 #10.5.4    Nivel: 3    Rol: D
 Verifique que las claves de marca de agua y los conjuntos de activación se almacenen en un módulo de seguridad de hardware y se roten anualmente.
 #10.5.5    Nivel: 3    Rol: V
 Verifique que los eventos de alerta de extracción incluyan las consultas infractoras y estén integrados con los playbooks de respuesta a incidentes.

---

### 10.6 Detección de datos envenenados en tiempo de inferencia

Identificar y neutralizar entradas con puertas traseras o envenenadas.

 #10.6.1    Nivel: 1    Rol: D
 Verifique que las entradas pasen por un detector de anomalías (por ejemplo, STRIP, puntuación de consistencia) antes de la inferencia del modelo.
 #10.6.2    Nivel: 1    Rol: V
 Verifique que los umbrales del detector estén ajustados en conjuntos de validación limpios/envenenados para lograr menos del 5% de falsos positivos.
 #10.6.3    Nivel: 2    Rol: D
 Verifique que las entradas marcadas como envenenadas desencadenen bloqueos suaves y flujos de trabajo de revisión humana.
 #10.6.4    Nivel: 2    Rol: V
 Verifique que los detectores sean sometidos a pruebas de estrés con ataques de puerta trasera adaptativos y sin disparadores.
 #10.6.5    Nivel: 3    Rol: D
 Verifique que las métricas de eficacia de detección se registren y se reevalúen periódicamente con nueva inteligencia de amenazas.

---

### 10.7 Adaptación Dinámica de Políticas de Seguridad

Actualizaciones en tiempo real de políticas de seguridad basadas en inteligencia de amenazas y análisis comportamental.

 #10.7.1    Nivel: 1    Rol: D/V
 Verificar que las políticas de seguridad se puedan actualizar dinámicamente sin reiniciar el agente, manteniendo la integridad de la versión de la política.
 #10.7.2    Nivel: 2    Rol: D/V
 Verifique que las actualizaciones de políticas estén firmadas criptográficamente por personal de seguridad autorizado y validadas antes de su aplicación.
 #10.7.3    Nivel: 2    Rol: D/V
 Verifique que los cambios en la política dinámica se registren con auditorías completas, incluyendo justificaciones, cadenas de aprobación y procedimientos de reversión.
 #10.7.4    Nivel: 3    Rol: D/V
 Verifique que los mecanismos de seguridad adaptativa ajusten la sensibilidad de detección de amenazas en función del contexto de riesgo y los patrones de comportamiento.
 #10.7.5    Nivel: 3    Rol: D/V
 Verifique que las decisiones de adaptación de políticas sean explicables e incluyan registros de evidencia para la revisión del equipo de seguridad.

---

### 10.8 Análisis de Seguridad Basado en Reflexión

Validación de seguridad mediante la autorreflexión del agente y el análisis metacognitivo.

 #10.8.1    Nivel: 1    Rol: D/V
 Verifique que los mecanismos de reflexión del agente incluyan una autoevaluación centrada en la seguridad de las decisiones y acciones.
 #10.8.2    Nivel: 2    Rol: D/V
 Verifique que las salidas de reflexión estén validadas para prevenir la manipulación de los mecanismos de autoevaluación mediante entradas adversarias.
 #10.8.3    Nivel: 2    Rol: D/V
 Verifique que el análisis de seguridad meta-cognitivo identifique posibles sesgos, manipulaciones o compromisos en los procesos de razonamiento del agente.
 #10.8.4    Nivel: 3    Rol: D/V
 Verifique que las advertencias de seguridad basadas en reflexión activen la supervisión mejorada y los posibles flujos de trabajo de intervención humana.
 #10.8.5    Nivel: 3    Rol: D/V
 Verifique que el aprendizaje continuo a partir de reflexiones de seguridad mejora la detección de amenazas sin degradar la funcionalidad legítima.

---

### 10.9 Seguridad en Evolución y Auto-mejora

Controles de seguridad para sistemas agentes capaces de auto-modificación y evolución.

 #10.9.1    Nivel: 1    Rol: D/V
 Verifique que las capacidades de auto-modificación estén restringidas a áreas designadas seguras con límites formales de verificación.
 #10.9.2    Nivel: 2    Rol: D/V
 Verificar que las propuestas de evolución sean sometidas a una evaluación de impacto de seguridad antes de su implementación.
 #10.9.3    Nivel: 2    Rol: D/V
 Verifique que los mecanismos de auto-mejora incluyan capacidades de reversión con verificación de integridad.
 #10.9.4    Nivel: 3    Rol: D/V
 Verifique que la seguridad del meta-aprendizaje previene la manipulación adversaria de los algoritmos de mejora.
 #10.9.5    Nivel: 3    Rol: D/V
 Verifique que la auto-mejora recursiva esté limitada por restricciones formales de seguridad con pruebas matemáticas de convergencia.

---

#### Referencias

MITRE ATLAS adversary tactics for ML
NIST AI Risk Management Framework 1.0, 2023
OWASP Top 10 for LLM Applications, 2025
Adversarial Training: A Survey — Zhao et al., 2024
RobustBench adversarial-robustness benchmark
Membership-Inference & Model-Inversion Risk Survey, 2025
PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023
Model-Inversion Attacks & Defenses Survey — AI Review, 2025
Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024
Fragile Model Watermarking Survey — 2025
Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025
BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024

## 11 Protección de la privacidad y gestión de datos personales

### Objetivo de Control

Mantenga garantías rigurosas de privacidad a lo largo de todo el ciclo de vida de la IA: recopilación, entrenamiento, inferencia y respuesta a incidentes, de modo que los datos personales se procesen solo con consentimiento claro, el alcance mínimo necesario, eliminación demostrable y garantías formales de privacidad.

---

### 11.1 Anonimización y Minimización de Datos

 #11.1.1    Nivel: 1    Rol: D/V
 Verifique que los identificadores directos y cuasi-identificadores sean eliminados o encriptados mediante hash.
 #11.1.2    Nivel: 2    Rol: D/V
 Verifique que las auditorías automatizadas midan k-anonimato/l-diversidad y alerten cuando los umbrales caigan por debajo de la política.
 #11.1.3    Nivel: 2    Rol: V
 Verifique que los informes de importancia de características del modelo demuestren que no hay filtración de identificadores más allá de ε = 0.01 de información mutua.
 #11.1.4    Nivel: 3    Rol: V
 Verifique que las pruebas formales o la certificación con datos sintéticos demuestren un riesgo de reidentificación ≤ 0.05 incluso bajo ataques de vinculación.

---

### 11.2 Derecho al Olvido y Aplicación de la Eliminación

 #11.2.1    Nivel: 1    Rol: D/V
 Verifique que las solicitudes de eliminación de datos de sujetos se propaguen a los conjuntos de datos en bruto, puntos de control, incrustaciones, registros y copias de seguridad dentro de los acuerdos de nivel de servicio de menos de 30 días.
 #11.2.2    Nivel: 2    Rol: D
 Verifique que las rutinas de "desaprendizaje automático" reentrenen físicamente o aproximen la eliminación utilizando algoritmos de desaprendizaje certificados.
 #11.2.3    Nivel: 2    Rol: V
 Verifique que la evaluación del modelo sombra demuestre que los registros olvidados influyen en menos del 1% de las salidas después del desaprendizaje.
 #11.2.4    Nivel: 3    Rol: V
 Verifique que los eventos de eliminación se registren de manera inmutable y sean auditables para los reguladores.

---

### 11.3 Salvaguardas de Privacidad Diferencial

 #11.3.1    Nivel: 2    Rol: D/V
 Verifique que los paneles de control de contabilidad de pérdida de privacidad alerten cuando ε acumulativo supere los umbrales de la política.
 #11.3.2    Nivel: 2    Rol: V
 Verifique que las auditorías de privacidad de caja negra estimen ε̂ dentro del 10% del valor declarado.
 #11.3.3    Nivel: 3    Rol: V
 Verifique que las pruebas formales cubran todas las afinaciones finas y los embeddings posteriores al entrenamiento.

---

### 11.4 Limitación de Propósito y Protección contra la Expansión del Alcance

 #11.4.1    Nivel: 1    Rol: D
 Verifique que cada conjunto de datos y punto de control del modelo lleve una etiqueta de propósito legible por máquina alineada con el consentimiento original.
 #11.4.2    Nivel: 1    Rol: D/V
 Verifique que los monitores de tiempo de ejecución detecten consultas inconsistentes con el propósito declarado y activen una negativa suave.
 #11.4.3    Nivel: 3    Rol: D
 Verifique que las puertas de política-como-código bloqueen la redistribución de modelos a nuevos dominios sin la revisión de DPIA.
 #11.4.4    Nivel: 3    Rol: V
 Verifique que las pruebas formales de trazabilidad demuestren que todo el ciclo de vida de los datos personales permanece dentro del alcance consentido.

---

### 11.5 Gestión de Consentimiento y Seguimiento de Base Legal

 #11.5.1    Nivel: 1    Rol: D/V
 Verifique que una Plataforma de Gestión de Consentimiento (CMP) registre el estado de opt-in, el propósito y el período de retención por sujeto de datos.
 #11.5.2    Nivel: 2    Rol: D
 Verifique que las API expongan tokens de consentimiento; los modelos deben validar el alcance del token antes de la inferencia.
 #11.5.3    Nivel: 2    Rol: D/V
 Verifique que el consentimiento denegado o retirado detenga las canalizaciones de procesamiento dentro de las 24 horas.

---

### 11.6 Aprendizaje Federado con Controles de Privacidad

 #11.6.1    Nivel: 1    Rol: D
 Verifique que las actualizaciones del cliente empleen la adición de ruido de privacidad diferencial local antes de la agregación.
 #11.6.2    Nivel: 2    Rol: D/V
 Verifique que las métricas de entrenamiento sean privadas de forma diferencial y que nunca revelen la pérdida de un solo cliente.
 #11.6.3    Nivel: 2    Rol: V
 Verifique que la agregación resistente a envenenamientos (por ejemplo, Krum/Trimmed-Mean) esté habilitada.
 #11.6.4    Nivel: 3    Rol: V
 Verifique que las pruebas formales demuestren un presupuesto general de ε con una pérdida de utilidad menor a 5.

---

#### Referencias

GDPR & AI Compliance Best Practices
EU Parliament Study on GDPR & AI, 2020
ISO 31700-1:2023 — Privacy by Design for Consumer Products
NIST Privacy Framework 1.1 (2025 Draft)
Machine Unlearning: Right-to-Be-Forgotten Techniques
A Survey of Machine Unlearning, 2024
Auditing DP-SGD — ArXiv 2024
DP-SGD Explained — PyTorch Blog
Purpose-Limitation for AI — IJLIT 2025
Data-Protection Considerations for AI — URM Consulting
Top Consent-Management Platforms, 2025
Secure Aggregation in DP Federated Learning — ArXiv 2024

## C12 Monitoreo, Registro y Detección de Anomalías

### Objetivo de Control

Esta sección proporciona requisitos para ofrecer visibilidad en tiempo real y forense sobre lo que el modelo y otros componentes de IA ven, hacen y devuelven, para que las amenazas puedan ser detectadas, clasificadas y aprendidas.

### C12.1 Registro de Solicitudes y Respuestas

 #12.1.1    Nivel: 1    Rol: D/V
 Verifique que todas las solicitudes de los usuarios y las respuestas del modelo estén registradas con los metadatos apropiados (por ejemplo, marca de tiempo, ID de usuario, ID de sesión, versión del modelo).
 #12.1.2    Nivel: 1    Rol: D/V
 Verifique que los registros se almacenen en repositorios seguros, con control de acceso, y con políticas de retención y procedimientos de respaldo apropiados.
 #12.1.3    Nivel: 1    Rol: D/V
 Verifique que los sistemas de almacenamiento de registros implementen cifrado en reposo y en tránsito para proteger la información sensible contenida en los registros.
 #12.1.4    Nivel: 1    Rol: D/V
 Verifique que los datos sensibles en los avisos y las salidas se redacten o enmascaren automáticamente antes de registrarlos, con reglas de redacción configurables para información personal identificable (PII), credenciales e información propietaria.
 #12.1.5    Nivel: 2    Rol: D/V
 Verifique que las decisiones de política y las acciones de filtrado de seguridad se registren con suficiente detalle para permitir la auditoría y depuración de los sistemas de moderación de contenido.
 #12.1.6    Nivel: 2    Rol: D/V
 Verifique que la integridad del registro esté protegida mediante, por ejemplo, firmas criptográficas o almacenamiento de solo escritura.

---

### C12.2 Detección y Alerta de Abuso

 #12.2.1    Nivel: 1    Rol: D/V
 Verifique que el sistema detecte y alerte sobre patrones conocidos de jailbreak, intentos de inyección de indicaciones y entradas adversarias utilizando detección basada en firmas.
 #12.2.2    Nivel: 1    Rol: D/V
 Verifique que el sistema se integre con las plataformas existentes de Gestión de Información y Eventos de Seguridad (SIEM) utilizando formatos y protocolos estándar de registro.
 #12.2.3    Nivel: 2    Rol: D/V
 Verifique que los eventos de seguridad enriquecidos incluyan contexto específico de IA, como identificadores de modelos, puntuaciones de confianza y decisiones del filtro de seguridad.
 #12.2.4    Nivel: 2    Rol: D/V
 Verifique que la detección de anomalías conductuales identifique patrones inusuales de conversación, intentos excesivos de reintento o comportamientos sistemáticos de sondeo.
 #12.2.5    Nivel: 2    Rol: D/V
 Verifique que los mecanismos de alerta en tiempo real notifiquen a los equipos de seguridad cuando se detecten posibles violaciones de políticas o intentos de ataque.
 #12.2.6    Nivel: 2    Rol: D/V
 Verifique que se incluyan reglas personalizadas para detectar patrones de amenazas específicos de IA, incluyendo intentos coordinados de jailbreak, campañas de inyección de prompts y ataques de extracción de modelos.
 #12.2.7    Nivel: 3    Rol: D/V
 Verifique que los flujos de trabajo automatizados de respuesta a incidentes puedan aislar modelos comprometidos, bloquear usuarios maliciosos y escalar eventos de seguridad críticos.

---

### C12.3 Detección de deriva del modelo

 #12.3.1    Nivel: 1    Rol: D/V
 Verifique que el sistema registre métricas básicas de rendimiento como precisión, puntuaciones de confianza, latencia y tasas de error a lo largo de las versiones del modelo y los períodos de tiempo.
 #12.3.2    Nivel: 2    Rol: D/V
 Verifique que las alertas automatizadas se activen cuando los métricas de rendimiento excedan los umbrales de degradación predefinidos o se desvíen significativamente de las líneas base.
 #12.3.3    Nivel: 2    Rol: D/V
 Verifique que los monitores de detección de alucinaciones identifiquen y señalen los casos en que las salidas del modelo contienen información incorrecta, inconsistente o fabricada.

---

### C12.4 Telemetría de Rendimiento y Comportamiento

 #12.4.1    Nivel: 1    Rol: D/V
 Verifique que las métricas operativas, incluyendo la latencia de las solicitudes, el consumo de tokens, el uso de memoria y el rendimiento, se recopilen y supervisen continuamente.
 #12.4.2    Nivel: 1    Rol: D/V
 Verifique que las tasas de éxito y fracaso se registren con la categorización de los tipos de error y sus causas raíz.
 #12.4.3    Nivel: 2    Rol: D/V
 Verifique que el monitoreo de la utilización de recursos incluya el uso de GPU/CPU, consumo de memoria y requisitos de almacenamiento, con alertas en caso de superar los umbrales establecidos.

---

### C12.5 Planificación y Ejecución de la Respuesta a Incidentes de IA

 #12.5.1    Nivel: 1    Rol: D/V
 Verifique que los planes de respuesta a incidentes aborden específicamente eventos de seguridad relacionados con IA, incluyendo compromiso del modelo, envenenamiento de datos y ataques adversarios.
 #12.5.2    Nivel: 2    Rol: D/V
 Verifique que los equipos de respuesta a incidentes tengan acceso a herramientas forenses específicas de IA y experiencia para investigar el comportamiento del modelo y los vectores de ataque.
 #12.5.3    Nivel: 3    Rol: D/V
 Verifique que el análisis posterior al incidente incluya consideraciones para el reentrenamiento del modelo, actualizaciones de los filtros de seguridad e integración de las lecciones aprendidas en los controles de seguridad.

---

### C12.5 Detección de Degradación del Rendimiento de la IA

Monitorear y detectar la degradación en el rendimiento y la calidad del modelo de IA con el tiempo.

 #12.5.1    Nivel: 1    Rol: D/V
 Verifique que la precisión, exactitud, recuperación y las puntuaciones F1 del modelo se monitoreen continuamente y se comparen con los umbrales de referencia.
 #12.5.2    Nivel: 1    Rol: D/V
 Verifique que la detección de deriva de datos monitoree los cambios en la distribución de entrada que puedan afectar el rendimiento del modelo.
 #12.5.3    Nivel: 2    Rol: D/V
 Verifique que la detección de deriva conceptual identifica cambios en la relación entre las entradas y las salidas esperadas.
 #12.5.4    Nivel: 2    Rol: D/V
 Verifique que la degradación del rendimiento active alertas automáticas e inicie los flujos de trabajo de reentrenamiento o reemplazo del modelo.
 #12.5.5    Nivel: 3    Rol: V
 Verifique que el análisis de la causa raíz de la degradación correlacione las caídas de rendimiento con cambios en los datos, problemas de infraestructura o factores externos.

---

### C12.6 Visualización de DAG y Seguridad del Flujo de Trabajo

Proteja los sistemas de visualización de flujos de trabajo contra fugas de información y ataques de manipulación.

 #12.6.1    Nivel: 1    Rol: D/V
 Verifique que los datos de visualización del DAG estén desinfectados para eliminar información sensible antes de su almacenamiento o transmisión.
 #12.6.2    Nivel: 1    Rol: D/V
 Verifique que los controles de acceso a la visualización del flujo de trabajo aseguren que solo los usuarios autorizados puedan ver las rutas de decisión del agente y los rastros de razonamiento.
 #12.6.3    Nivel: 2    Rol: D/V
 Verifique que la integridad de los datos del DAG esté protegida mediante firmas criptográficas y mecanismos de almacenamiento a prueba de manipulaciones.
 #12.6.4    Nivel: 2    Rol: D/V
 Verifique que los sistemas de visualización de flujos de trabajo implementen validación de entrada para prevenir ataques de inyección a través de datos manipulados en nodos o aristas.
 #12.6.5    Nivel: 3    Rol: D/V
 Verifique que las actualizaciones en tiempo real del DAG estén limitadas en tasa y validadas para prevenir ataques de denegación de servicio en los sistemas de visualización.

---

### C12.7 Monitoreo Proactivo del Comportamiento de Seguridad

Detección y prevención de amenazas de seguridad mediante el análisis proactivo del comportamiento de agentes.

 #12.7.1    Nivel: 1    Rol: D/V
 Verifique que los comportamientos proactivos del agente estén validados en seguridad antes de su ejecución con la integración de evaluación de riesgos.
 #12.7.2    Nivel: 2    Rol: D/V
 Verifique que los disparadores de iniciativa autónoma incluyan la evaluación del contexto de seguridad y la evaluación del panorama de amenazas.
 #12.7.3    Nivel: 2    Rol: D/V
 Verifique que los patrones de comportamiento proactivo sean analizados para posibles implicaciones de seguridad y consecuencias no intencionadas.
 #12.7.4    Nivel: 3    Rol: D/V
 Verifique que las acciones proactivas críticas para la seguridad requieran cadenas de aprobación explícitas con registros de auditoría.
 #12.7.5    Nivel: 3    Rol: D/V
 Verifique que la detección de anomalías conductuales identifique desviaciones en los patrones de agentes proactivos que puedan indicar compromiso.

---

### Referencias

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Supervisión Humana, Responsabilidad y Gobernanza

### Objetivo de Control

Este capítulo proporciona requisitos para mantener la supervisión humana y cadenas claras de responsabilidad en los sistemas de IA, asegurando explicabilidad, transparencia y gestión ética a lo largo del ciclo de vida de la IA.

---

### C13.1 Mecanismos de Interruptor de Apagado y Anulación

Proporcionar rutas de apagado o reversión cuando se observe un comportamiento inseguro del sistema de IA.

 #13.1.1    Nivel: 1    Rol: D/V
 Verifique que exista un mecanismo manual de interruptor de apagado para detener inmediatamente la inferencia y los resultados del modelo de IA.
 #13.1.2    Nivel: 1    Rol: D
 Verifique que los controles de anulación sean accesibles solo para el personal autorizado.
 #13.1.3    Nivel: 3    Rol: D/V
 Verifique que los procedimientos de reversión puedan regresar a versiones anteriores del modelo o a operaciones en modo seguro.
 #13.1.4    Nivel: 3    Rol: V
 Verifique que los mecanismos de anulación se prueben regularmente.

---

### C13.2 Puntos de Control de Decisión con Intervención Humana

Requerir aprobaciones humanas cuando las apuestas superen los umbrales de riesgo predefinidos.

 #13.2.1    Nivel: 1    Rol: D/V
 Verifique que las decisiones de IA de alto riesgo requieran aprobación humana explícita antes de su ejecución.
 #13.2.2    Nivel: 1    Rol: D
 Verifique que los umbrales de riesgo estén claramente definidos y que disparen automáticamente los flujos de trabajo de revisión humana.
 #13.2.3    Nivel: 2    Rol: D
 Verifique que las decisiones sensibles al tiempo cuenten con procedimientos alternativos cuando no se pueda obtener la aprobación humana dentro de los plazos requeridos.
 #13.2.4    Nivel: 3    Rol: D/V
 Verifique que los procedimientos de escalamiento definan niveles claros de autoridad para diferentes tipos de decisiones o categorías de riesgo, si aplica.

---

### C13.3 Cadena de Responsabilidad y Auditabilidad

Registrar las acciones del operador y las decisiones del modelo.

 #13.3.1    Nivel: 1    Rol: D/V
 Verifique que todas las decisiones del sistema de IA y las intervenciones humanas estén registradas con marcas de tiempo, identidades de usuario y la justificación de la decisión.
 #13.3.2    Nivel: 2    Rol: D
 Verifique que los registros de auditoría no puedan ser manipulados e incluyan mecanismos de verificación de integridad.

---

### C13.4 Técnicas de IA Explicable

Importancia de características superficiales, contrafactuales y explicaciones locales.

 #13.4.1    Nivel: 1    Rol: D/V
 Verifique que los sistemas de IA proporcionen explicaciones básicas de sus decisiones en un formato legible para humanos.
 #13.4.2    Nivel: 2    Rol: V
 Verifique que la calidad de la explicación sea validada mediante estudios y métricas de evaluación humana.
 #13.4.3    Nivel: 3    Rol: D/V
 Verifique que las puntuaciones de importancia de características o métodos de atribución (SHAP, LIME, etc.) estén disponibles para decisiones críticas.
 #13.4.4    Nivel: 3    Rol: V
 Verifique que las explicaciones contrafactuales muestren cómo se podrían modificar las entradas para cambiar los resultados, si es aplicable al caso de uso y dominio.

---

### C13.5 Tarjetas de Modelo y Divulgaciones de Uso

Mantener las tarjetas de modelo para el uso previsto, las métricas de rendimiento y las consideraciones éticas.

 #13.5.1    Nivel: 1    Rol: D
 Verifique que las tarjetas de modelo documenten los casos de uso previstos, las limitaciones y los modos de fallo conocidos.
 #13.5.2    Nivel: 1    Rol: D/V
 Verifique que se divulguen las métricas de rendimiento en los diferentes casos de uso aplicables.
 #13.5.3    Nivel: 2    Rol: D
 Verifique que las consideraciones éticas, evaluaciones de sesgo, evaluaciones de equidad, características de los datos de entrenamiento y limitaciones conocidas de los datos de entrenamiento estén documentadas y actualizadas regularmente.
 #13.5.4    Nivel: 2    Rol: D/V
 Verifique que las tarjetas del modelo estén controladas por versiones y se mantengan a lo largo del ciclo de vida del modelo con seguimiento de cambios.

---

### C13.6 Cuantificación de la Incertidumbre

Propagar puntuaciones de confianza o medidas de entropía en las respuestas.

 #13.6.1    Nivel: 1    Rol: D
 Verifique que los sistemas de IA proporcionen puntajes de confianza o medidas de incertidumbre con sus resultados.
 #13.6.2    Nivel: 2    Rol: D/V
 Verifique que los umbrales de incertidumbre activen una revisión humana adicional o vías de decisión alternativas.
 #13.6.3    Nivel: 2    Rol: V
 Verifique que los métodos de cuantificación de incertidumbre estén calibrados y validados contra los datos de verdad fundamental.
 #13.6.4    Nivel: 3    Rol: D/V
 Verifique que la propagación de la incertidumbre se mantenga a través de flujos de trabajo de IA multinivel.

---

### C13.7 Informes de Transparencia para Usuarios

Proporcione divulgaciones periódicas sobre incidentes, desviaciones y uso de datos.

 #13.7.1    Nivel: 1    Rol: D/V
 Verifique que las políticas de uso de datos y las prácticas de gestión del consentimiento del usuario sean comunicadas claramente a las partes interesadas.
 #13.7.2    Nivel: 2    Rol: D/V
 Verificar que se realicen evaluaciones de impacto de la IA y que los resultados se incluyan en los informes.
 #13.7.3    Nivel: 2    Rol: D/V
 Verificar que los informes de transparencia publicados regularmente revelen incidentes de IA y métricas operativas con un detalle razonable.

#### Referencias

EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
ISO/IEC 42001:2023 — AI Management Systems Requirements
NIST AI Risk Management Framework 1.0
NIST SP 800-53 Revision 5 — Security and Privacy Controls
A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)
Model Cards for Model Reporting (Mitchell et al., 2018)
Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)
ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods
IEEE 7001-2021 — Transparency of Autonomous Systems
GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Apéndice A: Glosario

Este glosario completo ofrece definiciones de términos clave de IA, ML y seguridad utilizados en todo el AISVS para asegurar claridad y comprensión común.

Ejemplo adversarial: una entrada elaborada deliberadamente para hacer que un modelo de IA cometa un error, a menudo agregando perturbaciones sutiles imperceptibles para los humanos.
​
Robustez adversarial: la robustez adversarial en IA se refiere a la capacidad de un modelo para mantener su rendimiento y resistir ser engañado o manipulado por entradas maliciosamente diseñadas intencionalmente para causar errores.
​
Agente – Los agentes de IA son sistemas de software que utilizan IA para perseguir objetivos y completar tareas en nombre de los usuarios. Muestran razonamiento, planificación y memoria, y tienen un nivel de autonomía para tomar decisiones, aprender y adaptarse.
​
IA Agente: sistemas de IA que pueden operar con cierto grado de autonomía para alcanzar objetivos, a menudo tomando decisiones y realizando acciones sin intervención humana directa.
​
Control de Acceso Basado en Atributos (ABAC): Un paradigma de control de acceso donde las decisiones de autorización se basan en atributos del usuario, recurso, acción y entorno, evaluados en tiempo de consulta.
​
Ataque de puerta trasera: Un tipo de ataque de envenenamiento de datos donde el modelo se entrena para responder de una manera específica a ciertos disparadores mientras se comporta normalmente en otras circunstancias.
​
Sesgo: Errores sistemáticos en los resultados de los modelos de IA que pueden conducir a resultados injustos o discriminatorios para ciertos grupos o en contextos específicos.
​
Explotación de sesgos: una técnica de ataque que aprovecha los sesgos conocidos en los modelos de IA para manipular resultados o salidas.
​
Cedar: lenguaje y motor de políticas de Amazon para permisos detallados utilizados en la implementación de ABAC para sistemas de IA.
​
Cadena de pensamiento: Una técnica para mejorar el razonamiento en modelos de lenguaje mediante la generación de pasos intermedios de razonamiento antes de producir una respuesta final.
​
Interruptores automáticos: Mecanismos que detienen automáticamente las operaciones del sistema de IA cuando se superan umbrales específicos de riesgo.
​
Fuga de datos: Exposición no intencionada de información sensible a través de las salidas o el comportamiento del modelo de IA.
​
Envenenamiento de datos: La corrupción deliberada de los datos de entrenamiento para comprometer la integridad del modelo, a menudo para instalar puertas traseras o degradar el rendimiento.
​
Privacidad Diferencial – La privacidad diferencial es un marco matemáticamente riguroso para publicar información estadística sobre conjuntos de datos protegiendo la privacidad de los sujetos individuales. Permite que un poseedor de datos comparta patrones agregados del grupo mientras limita la información filtrada sobre individuos específicos.
​
Embeddings: Representaciones vectoriales densas de datos (texto, imágenes, etc.) que capturan el significado semántico en un espacio de alta dimensión.
​
Explicabilidad – La explicabilidad en IA es la capacidad de un sistema de IA para proporcionar razones comprensibles para los humanos sobre sus decisiones y predicciones, ofreciendo información sobre su funcionamiento interno.
​
Inteligencia Artificial Explicable (XAI): sistemas de IA diseñados para proporcionar explicaciones comprensibles para los humanos sobre sus decisiones y comportamientos mediante diversas técnicas y marcos.
​
Aprendizaje Federado: Un enfoque de aprendizaje automático donde los modelos se entrenan en múltiples dispositivos descentralizados que poseen muestras de datos locales, sin intercambiar los datos mismos.
​
Guardrails: Restricciones implementadas para evitar que los sistemas de IA produzcan resultados dañinos, sesgados o de otro modo indeseables.
​
Alucinación – Una alucinación de IA se refiere a un fenómeno donde un modelo de IA genera información incorrecta o engañosa que no se basa en sus datos de entrenamiento ni en la realidad factual.
​
Human-in-the-Loop (HITL): Sistemas diseñados para requerir supervisión, verificación o intervención humana en puntos cruciales de decisión.
​
Infraestructura como Código (IaC): Gestión y aprovisionamiento de infraestructura mediante código en lugar de procesos manuales, permitiendo escaneo de seguridad y despliegues consistentes.
​
Escape de la cárcel (Jailbreak): Técnicas utilizadas para eludir las medidas de seguridad en sistemas de IA, especialmente en grandes modelos de lenguaje, para producir contenido prohibido.
​
Privilegio Mínimo: El principio de seguridad de conceder solo los derechos de acceso mínimos necesarios para los usuarios y procesos.
​
LIME (Explicaciones Locales Interpretable y Agnósticas al Modelo): Una técnica para explicar las predicciones de cualquier clasificador de aprendizaje automático aproximándolo localmente con un modelo interpretable.
​
Ataque de Inferencia de Membresía: Un ataque que tiene como objetivo determinar si un punto de datos específico fue utilizado para entrenar un modelo de aprendizaje automático.
​
MITRE ATLAS: Panorama de Amenazas Adversarias para Sistemas de Inteligencia Artificial; una base de conocimiento de tácticas y técnicas adversarias contra sistemas de IA.
​
Tarjeta del modelo – Una tarjeta del modelo es un documento que proporciona información estandarizada sobre el rendimiento, limitaciones, usos previstos y consideraciones éticas de un modelo de IA para promover la transparencia y el desarrollo responsable de la IA.
​
Extracción de Modelo: Un ataque en el que un adversario consulta repetidamente un modelo objetivo para crear una copia funcionalmente similar sin autorización.
​
Inversión de modelo: Un ataque que intenta reconstruir datos de entrenamiento analizando las salidas del modelo.
​
Gestión del Ciclo de Vida del Modelo – La gestión del ciclo de vida del modelo de IA es el proceso de supervisar todas las etapas de la existencia de un modelo de IA, incluyendo su diseño, desarrollo, despliegue, monitoreo, mantenimiento y eventual retirada, para garantizar que permanezca efectivo y alineado con los objetivos.
​
Envenenamiento de modelos: Introducción de vulnerabilidades o puertas traseras directamente en un modelo durante el proceso de entrenamiento.
​
Robo/Robo de Modelo: Extracción de una copia o aproximación de un modelo propietario mediante consultas repetidas.
​
Sistema multiagente: un sistema compuesto por múltiples agentes de IA que interactúan entre sí, cada uno con capacidades y objetivos potencialmente diferentes.
​
OPA (Open Policy Agent): Un motor de políticas de código abierto que permite la aplicación unificada de políticas en toda la pila.
​
Aprendizaje Automático que Preserva la Privacidad (PPML): Técnicas y métodos para entrenar y desplegar modelos de ML mientras se protege la privacidad de los datos de entrenamiento.
​
Inyección de indicaciones: Un ataque donde se insertan instrucciones maliciosas en las entradas para anular el comportamiento previsto de un modelo.
​
RAG (Generación Aumentada con Recuperación): Una técnica que mejora los modelos de lenguaje grandes al recuperar información relevante de fuentes externas de conocimiento antes de generar una respuesta.
​
Red-Teaming: La práctica de probar activamente los sistemas de IA simulando ataques adversarios para identificar vulnerabilidades.
​
SBOM (Registro de materiales de software): Un registro formal que contiene los detalles y las relaciones de la cadena de suministro de varios componentes utilizados en la construcción de software o modelos de IA.
​
SHAP (Explicaciones Aditivas de Shapley): Un enfoque basado en la teoría de juegos para explicar el resultado de cualquier modelo de aprendizaje automático mediante el cálculo de la contribución de cada característica a la predicción.
​
Ataque a la cadena de suministro: comprometer un sistema al dirigirse a elementos menos seguros en su cadena de suministro, como bibliotecas de terceros, conjuntos de datos o modelos preentrenados.
​
Aprendizaje por transferencia: Una técnica en la que un modelo desarrollado para una tarea se reutiliza como punto de partida para un modelo en una segunda tarea.
​
Base de Datos Vectorial: Una base de datos especializada diseñada para almacenar vectores de alta dimensión (embeddings) y realizar búsquedas de similitud de manera eficiente.
​
Escaneo de Vulnerabilidades: Herramientas automatizadas que identifican vulnerabilidades de seguridad conocidas en componentes de software, incluidos marcos de IA y dependencias.
​
Marcas de agua: Técnicas para insertar marcadores imperceptibles en contenido generado por IA para rastrear su origen o detectar generación por IA.
​
Vulnerabilidad de Día Cero: Una vulnerabilidad previamente desconocida que los atacantes pueden explotar antes de que los desarrolladores creen y desplieguen un parche.

## Apéndice B: Referencias

### TODO

## Apéndice C: Gobernanza y Documentación de Seguridad en IA

### Objetivo

Este apéndice proporciona los requisitos fundamentales para establecer estructuras organizativas, políticas y procesos para gobernar la seguridad de la IA a lo largo del ciclo de vida del sistema.

---

### Adopción del Marco de Gestión de Riesgos de IA AC.1

Proporcionar un marco formal para identificar, evaluar y mitigar los riesgos específicos de la IA a lo largo del ciclo de vida del sistema.

 #AC.1.1    Nivel: 1    Rol: D/V
 Verifique que una metodología de evaluación de riesgos específica para IA esté documentada e implementada.
 #AC.1.2    Nivel: 2    Rol: D
 Verifique que se realicen evaluaciones de riesgos en puntos clave del ciclo de vida de la IA y antes de cambios significativos.
 #AC.1.3    Nivel: 3    Rol: D/V
 Verifique que el marco de gestión de riesgos esté alineado con los estándares establecidos (por ejemplo, NIST AI RMF).

---

### AC.2 Política y Procedimientos de Seguridad de IA

Definir y hacer cumplir los estándares organizacionales para el desarrollo, despliegue y operación segura de la IA.

 #AC.2.1    Nivel: 1    Rol: D/V
 Verificar que existan políticas de seguridad de IA documentadas.
 #AC.2.2    Nivel: 2    Rol: D
 Verifique que las políticas se revisen y actualicen al menos anualmente y después de cambios significativos en el panorama de amenazas.
 #AC.2.3    Nivel: 3    Rol: D/V
 Verifique que las políticas aborden todas las categorías de AISVS y los requisitos regulatorios aplicables.

---

### AC.3 Roles y Responsabilidades para la Seguridad de la IA

Establecer una responsabilidad clara para la seguridad de la IA en toda la organización.

 #AC.3.1    Nivel: 1    Rol: D/V
 Verifique que los roles y responsabilidades de seguridad de la IA estén documentados.
 #AC.3.2    Nivel: 2    Rol: D
 Verifique que las personas responsables posean la experiencia adecuada en seguridad.
 #AC.3.3    Nivel: 3    Rol: D/V
 Verificar que se haya establecido un comité de ética de IA o una junta de gobernanza para los sistemas de IA de alto riesgo.

---

### Aplicación de las Directrices Éticas para la IA

Asegurar que los sistemas de IA operen de acuerdo con los principios éticos establecidos.

 #AC.4.1    Nivel: 1    Rol: D/V
 Verifique que existan directrices éticas para el desarrollo y despliegue de IA.
 #AC.4.2    Nivel: 2    Rol: D
 Verifique que existan mecanismos para detectar y reportar violaciones éticas.
 #AC.4.3    Nivel: 3    Rol: D/V
 Verifique que se realicen revisiones éticas regulares de los sistemas de IA implementados.

---

### AC.5 Monitoreo de Cumplimiento Regulatorio de IA

Mantener la conciencia y el cumplimiento de las regulaciones de IA en evolución.

 #AC.5.1    Nivel: 1    Rol: D/V
 Verifique que existan procesos para identificar las regulaciones de IA aplicables.
 #AC.5.2    Nivel: 2    Rol: D
 Verifique que se evalúe el cumplimiento de todos los requisitos reglamentarios.
 #AC.5.3    Nivel: 3    Rol: D/V
 Verifique que los cambios regulatorios provoquen revisiones y actualizaciones oportunas de los sistemas de IA.

### AC.6 Gobernanza, Documentación y Proceso de los Datos de Entrenamiento

 #1.1.2    Nivel: 1    Rol: D/V
 Verifique que solo se permitan conjuntos de datos evaluados por calidad, representatividad, abastecimiento ético y cumplimiento de licencias, reduciendo los riesgos de envenenamiento, sesgo incorporado e infracción de propiedad intelectual.
 #1.1.5    Nivel: 2    Rol: D/V
 Verifique que la calidad del etiquetado/anotación esté garantizada mediante la verificación cruzada o el consenso de los revisores.
 #1.1.6    Nivel: 2    Rol: D/V
 Verifique que se mantengan "tarjetas de datos" o "hojas de datos para conjuntos de datos" para conjuntos de datos de entrenamiento significativos, detallando características, motivaciones, composición, procesos de recopilación, preprocesamiento y usos recomendados/desaconsejados.
 #1.3.2    Nivel: 2    Rol: D/V
 Verificar que los sesgos identificados se mitiguen mediante estrategias documentadas como el reequilibrio, la aumentación de datos dirigida, los ajustes algorítmicos (por ejemplo, técnicas de preprocesamiento, procesamiento y posprocesamiento) o el reponderamiento, y que se evalúe el impacto de la mitigación tanto en la equidad como en el rendimiento general del modelo.
 #1.3.3    Nivel: 2    Rol: D/V
 Verifique que las métricas de equidad posteriores al entrenamiento sean evaluadas y documentadas.
 #1.3.4    Nivel: 3    Rol: D/V
 Verifique que una política de gestión de sesgos a lo largo del ciclo de vida asigne propietarios y una cadencia de revisión.
 #1.4.1    Nivel: 2    Rol: D/V
 Verifique que la calidad del etiquetado/anotación se garantice mediante pautas claras, revisiones cruzadas por parte de los evaluadores, mecanismos de consenso (por ejemplo, monitoreo del acuerdo entre anotadores) y procesos definidos para resolver discrepancias.
 #1.4.4    Nivel: 3    Rol: D/V
 Verifique que las etiquetas críticas para la seguridad, la protección o la equidad (por ejemplo, la identificación de contenido tóxico, hallazgos médicos críticos) reciban una revisión dual independiente obligatoria o una verificación robusta equivalente.
 #1.4.6    Nivel: 2    Rol: D/V
 Verifique que las guías de etiquetado e instrucciones sean completas, controladas por versión y revisadas por pares.
 #1.4.6    Nivel: 2    Rol: D/V
 Verifique que los esquemas de datos para las etiquetas estén claramente definidos y controlados por versiones.
 #1.3.1    Nivel: 1    Rol: D/V
 Verifique que los conjuntos de datos estén analizados para detectar desequilibrios representacionales y sesgos potenciales en atributos legalmente protegidos (por ejemplo, raza, género, edad) y otras características éticamente sensibles relevantes para el dominio de aplicación del modelo (por ejemplo, estatus socioeconómico, ubicación).
 #1.5.3    Nivel: 2    Rol: V
 Verifique que las revisiones manuales puntuales por expertos en el dominio cubran una muestra estadísticamente significativa (por ejemplo, ≥1 % o 1,000 muestras, lo que sea mayor, o según lo determinado por la evaluación de riesgos) para identificar problemas sutiles de calidad que no sean detectados por la automatización.
 #1.8.4    Nivel: 2    Rol: D/V
 Verifique que los flujos de trabajo de etiquetado subcontratados o realizados por crowdsourcing incluyan salvaguardas técnicas/procedimentales para garantizar la confidencialidad e integridad de los datos, la calidad de las etiquetas y prevenir la fuga de datos.
 #1.5.4    Nivel: 2    Rol: D/V
 Verifique que los pasos de remediación se anexen a los registros de procedencia.
 #1.6.2    Nivel: 2    Rol: D/V
 Verifique que las muestras marcadas desencadenen una revisión manual antes del entrenamiento.
 #1.6.3    Nivel: 2    Rol: V
 Verifique que los resultados alimenten el dossier de seguridad del modelo e informen la inteligencia de amenazas en curso.
 #1.6.4    Nivel: 3    Rol: D/V
 Verifique que la lógica de detección se actualice con nueva inteligencia de amenazas.
 #1.6.5    Nivel: 3    Rol: D/V
 Verifique que las canalizaciones de aprendizaje en línea supervisen la deriva de distribución.
 #1.7.1    Nivel: 1    Rol: D/V
 Verificar que los flujos de trabajo de eliminación de datos de entrenamiento purguen datos primarios y derivados y evaluar el impacto en el modelo, y que se evalúe y, si es necesario, se aborde el impacto en los modelos afectados (por ejemplo, mediante reentrenamiento o recalibración).
 #1.7.2    Nivel: 2    Rol: D
 Verifique que existan mecanismos para rastrear y respetar el alcance y el estado del consentimiento del usuario (y las retiradas) para los datos utilizados en el entrenamiento, y que el consentimiento se valide antes de que los datos se incorporen en nuevos procesos de entrenamiento o actualizaciones significativas del modelo.
 #1.7.3    Nivel: 2    Rol: V
 Verifique que los flujos de trabajo se prueben anualmente y se registren.
 #1.8.1    Nivel: 2    Rol: D/V
 Verifique que los proveedores de datos externos, incluidos los proveedores de modelos preentrenados y conjuntos de datos externos, se sometan a una debida diligencia en seguridad, privacidad, obtención ética y calidad de datos antes de que sus datos o modelos se integren.
 #1.8.2    Nivel: 1    Rol: D
 Verifique que las transferencias externas utilicen TLS/autenticación y controles de integridad.
 #1.8.3    Nivel: 2    Rol: D/V
 Verifique que las fuentes de datos de alto riesgo (por ejemplo, conjuntos de datos de código abierto con procedencia desconocida, proveedores no verificados) reciban un escrutinio mejorado, como análisis en entornos aislados, verificaciones extensas de calidad/sesgo y detección dirigida de envenenamiento, antes de su uso en aplicaciones sensibles.
 #1.8.4    Nivel: 3    Rol: D/V
 Verifique que los modelos preentrenados obtenidos de terceros sean evaluados para detectar sesgos incorporados, puertas traseras potenciales, la integridad de su arquitectura y la procedencia de sus datos de entrenamiento originales antes de su ajuste fino o despliegue.
 #1.5.3    Nivel: 2    Rol: D/V
 Verifique que si se utiliza entrenamiento adversarial, la generación, gestión y versionado de conjuntos de datos adversariales estén documentados y controlados.
 #1.5.3    Nivel: 3    Rol: D/V
 Verifique que el impacto del entrenamiento de robustez adversarial en el rendimiento del modelo (tanto contra entradas limpias como adversariales) y en las métricas de equidad sea evaluado, documentado y monitoreado.
 #1.5.4    Nivel: 3    Rol: D/V
 Verificar que las estrategias para el entrenamiento adversarial y la robustez se revisen y actualicen periódicamente para contrarrestar las técnicas evolutivas de ataques adversarios.
 #1.4.2    Nivel: 2    Rol: D/V
 Verifique que los conjuntos de datos fallidos estén en cuarentena con registros de auditoría.
 #1.4.3    Nivel: 2    Rol: D/V
 Verifique que las puertas de calidad bloqueen conjuntos de datos de calidad inferior a menos que se aprueben excepciones.
 #1.11.2    Nivel: 2    Rol: D/V
 Verifique que el proceso de generación, los parámetros y el uso previsto de los datos sintéticos estén documentados.
 #1.11.3    Nivel: 2    Rol: D/V
 Verifique que los datos sintéticos sean evaluados en cuanto a riesgos de sesgo, filtración de privacidad y problemas de representación antes de usarlos en el entrenamiento.
 #1.12.3    Nivel: 2    Rol: D/V
 Verifique que se generen alertas para eventos de acceso sospechosos y que se investiguen de manera oportuna.
 #1.13.1    Nivel: 1    Rol: D/V
 Verifique que se definan períodos de retención explícitos para todos los conjuntos de datos de entrenamiento.
 #1.13.2    Nivel: 2    Rol: D/V
 Verifique que los conjuntos de datos se expiren, eliminen o revisen automáticamente para su eliminación al final de su ciclo de vida.
 #1.13.3    Nivel: 2    Rol: D/V
 Verifique que las acciones de retención y eliminación estén registradas y sean auditables.
 #1.14.1    Nivel: 2    Rol: D/V
 Verifique que los requisitos de residencia de datos y transferencia transfronteriza estén identificados y aplicados para todos los conjuntos de datos.
 #1.14.2    Nivel: 2    Rol: D/V
 Verificar que las regulaciones específicas del sector (por ejemplo, salud, finanzas) estén identificadas y abordadas en el manejo de datos.
 #1.14.3    Nivel: 2    Rol: D/V
 Verifique que el cumplimiento con las leyes de privacidad relevantes (por ejemplo, GDPR, CCPA) esté documentado y se revise regularmente.
 #1.16.1    Nivel: 2    Rol: D/V
 Verifique que existan mecanismos para responder a las solicitudes del sujeto de datos para acceso, rectificación, restricción u oposición.
 #1.16.2    Nivel: 2    Rol: D/V
 Verifique que las solicitudes se registren, rastreen y cumplan dentro de los plazos legalmente establecidos.
 #1.16.3    Nivel: 2    Rol: D/V
 Verifique que los procesos de derechos del sujeto de datos se prueben y revisen regularmente para garantizar su efectividad.
 #1.17.1    Nivel: 2    Rol: D/V
 Verifique que se realice un análisis de impacto antes de actualizar o reemplazar una versión de conjunto de datos, cubriendo el rendimiento del modelo, la equidad y el cumplimiento.
 #1.17.2    Nivel: 2    Rol: D/V
 Verifique que los resultados del análisis de impacto estén documentados y revisados por las partes interesadas relevantes.
 #1.17.3    Nivel: 2    Rol: D/V
 Verifique que existan planes de reversión en caso de que las nuevas versiones introduzcan riesgos inaceptables o regresiones.
 #1.18.1    Nivel: 2    Rol: D/V
 Verifique que todo el personal involucrado en la anotación de datos haya sido sometido a una verificación de antecedentes y esté capacitado en seguridad y privacidad de datos.
 #1.18.2    Nivel: 2    Rol: D/V
 Verifique que todo el personal de anotación firme acuerdos de confidencialidad y no divulgación.
 #1.18.3    Nivel: 2    Rol: D/V
 Verifique que las plataformas de anotación apliquen controles de acceso y supervisen las amenazas internas.

#### Referencias

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Apéndice D: Gobernanza y Verificación de Codificación Segura Asistida por IA

### Objetivo

Este capítulo define controles organizacionales básicos para el uso seguro y efectivo de herramientas de codificación asistidas por IA durante el desarrollo de software, asegurando la seguridad y trazabilidad a lo largo del SDLC.

---

### AD.1 Flujo de trabajo de codificación segura asistida por IA

Integrar herramientas de IA en el ciclo de vida de desarrollo de software seguro (SSDLC) de la organización sin debilitar las barreras de seguridad existentes.

 #AD.1.1    Nivel: 1    Rol: D/V
 Verifique que un flujo de trabajo documentado describa cuándo y cómo las herramientas de IA pueden generar, refactorizar o revisar código.
 #AD.1.2    Nivel: 2    Rol: D
 Verifique que el flujo de trabajo se corresponda con cada fase del SSDLC (diseño, implementación, revisión de código, pruebas, despliegue).
 #AD.1.3    Nivel: 3    Rol: D/V
 Verifique que las métricas (por ejemplo, densidad de vulnerabilidades, tiempo medio para detectar) se recopilen en el código producido por IA y se comparen con las bases de referencia solo humanas.

---

### AD.2 Calificación de Herramientas de IA y Modelado de Amenazas

Asegúrese de que las herramientas de codificación de IA sean evaluadas en cuanto a capacidades de seguridad, riesgos y impacto en la cadena de suministro antes de su adopción.

 #AD.2.1    Nivel: 1    Rol: D/V
 Verifique que un modelo de amenazas para cada herramienta de IA identifique el uso indebido, la inversión del modelo, la filtración de datos y los riesgos de la cadena de dependencias.
 #AD.2.2    Nivel: 2    Rol: D
 Verifique que las evaluaciones de las herramientas incluyan análisis estático/dinámico de cualquier componente local y evaluación de los puntos finales SaaS (TLS, autenticación/autorización, registro).
 #AD.2.3    Nivel: 3    Rol: D/V
 Verifique que las evaluaciones sigan un marco reconocido y se vuelvan a realizar después de cambios importantes de versión.

---

### AD.3 Gestión Segura de Indicaciones y Contexto

Evitar la filtración de secretos, código propietario y datos personales al construir indicaciones o contextos para modelos de IA.

 #AD.3.1    Nivel: 1    Rol: D/V
 Verifique que las directrices escritas prohíban enviar secretos, credenciales o datos clasificados en los prompts.
 #AD.3.2    Nivel: 2    Rol: D
 Verifique que los controles técnicos (redacción del lado del cliente, filtros de contexto aprobados) eliminen automáticamente los artefactos sensibles.
 #AD.3.3    Nivel: 3    Rol: D/V
 Verifique que los prompts y respuestas sean tokenizados, encriptados durante la transmisión y en reposo, y que los períodos de retención cumplan con la política de clasificación de datos.

---

### AD.4 Validación del Código Generado por IA

Detectar y remediar vulnerabilidades introducidas por la salida de IA antes de que el código sea fusionado o desplegado.

 #AD.4.1    Nivel: 1    Rol: D/V
 Verifique que el código generado por IA siempre sea sometido a revisión humana de código.
 #AD.4.2    Nivel: 2    Rol: D
 Verifique que los escáneres automatizados (SAST/IAST/DAST) se ejecuten en cada solicitud de extracción que contenga código generado por IA y bloqueen las fusiones en hallazgos críticos.
 #AD.4.3    Nivel: 3    Rol: D/V
 Verifique que las pruebas de fuzzing diferencial o las pruebas basadas en propiedades demuestren comportamientos críticos para la seguridad (por ejemplo, validación de entradas, lógica de autorización).

---

### AD.5 Explicabilidad y trazabilidad de las sugerencias de código

Proporcionar a los auditores y desarrolladores información sobre por qué se hizo una sugerencia y cómo evolucionó.

 #AD.5.1    Nivel: 1    Rol: D/V
 Verifique que los pares de entrada/respuesta se registren con IDs de commit.
 #AD.5.2    Nivel: 2    Rol: D
 Verifique que los desarrolladores puedan mostrar citas del modelo (fragmentos de entrenamiento, documentación) que respalden una sugerencia.
 #AD.5.3    Nivel: 3    Rol: D/V
 Verifique que los informes de explicabilidad se almacenen junto con los artefactos de diseño y se hagan referencia en las revisiones de seguridad, satisfaciendo los principios de trazabilidad de ISO/IEC 42001.

---

### AD.6 Retroalimentación Continua y Ajuste Fino del Modelo

Mejorar el rendimiento de la seguridad del modelo con el tiempo mientras se previene la deriva negativa.

 #AD.6.1    Nivel: 1    Rol: D/V
 Verifique que los desarrolladores puedan señalar sugerencias inseguras o no conformes, y que las marcas sean registradas.
 #AD.6.2    Nivel: 2    Rol: D
 Verifique que la retroalimentación agregada informe el ajuste fino periódico o la generación aumentada por recuperación con corpora de codificación segura verificadas (por ejemplo, las hojas de trucos de OWASP).
 #AD.6.3    Nivel: 3    Rol: D/V
 Verifique que un arnés de evaluación de bucle cerrado ejecute pruebas de regresión después de cada ajuste fino; las métricas de seguridad deben cumplir o superar las líneas base anteriores antes del despliegue.

---

#### Referencias

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Apéndice E: Ejemplos de Herramientas y Frameworks

### Objetivo

Este capítulo proporciona ejemplos de herramientas y marcos que pueden apoyar la implementación o cumplimiento de un requisito dado del AISVS. Estos no deben ser vistos como recomendaciones o avales por parte del equipo de AISVS o del Proyecto de Seguridad GenAI de OWASP.

---

### AE.1 Gobernanza de Datos de Entrenamiento y Gestión de Sesgos

Herramientas utilizadas para análisis de datos, gobernanza y gestión de sesgos.

 #AE.1.1    Sección: 1.1
 Herramientas de Inventario de Datos: Herramientas para la gestión de inventario de datos como...
 #AE.1.2    Sección: 1.2
 Cifrado en tránsito Utilice TLS para aplicaciones basadas en HTTPS, con herramientas como openSSL y python's`ssl` biblioteca.

---

### AE.2 Validación de Entrada del Usuario

Herramientas para manejar y validar las entradas de usuario.

 #AE.2.1    Sección: 2.1
 Herramientas de defensa contra inyección de indicaciones: Use herramientas de protección como NeMo de NVIDIA o Guardrails AI.

---

