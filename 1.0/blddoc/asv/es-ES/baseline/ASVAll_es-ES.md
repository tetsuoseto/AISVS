## Frontispicio

### Acerca del Estándar

El Estándar de Verificación de Seguridad de la Inteligencia Artificial (AISVS) es un catálogo impulsado por la comunidad de requisitos de seguridad que científicos de datos, ingenieros de MLOps, arquitectos de software, desarrolladores, testers, profesionales de seguridad, proveedores de herramientas, reguladores y consumidores pueden usar para diseñar, construir, probar y verificar sistemas y aplicaciones habilitados por IA confiables. Proporciona un lenguaje común para especificar controles de seguridad a lo largo del ciclo de vida de la IA, desde la recopilación de datos y el desarrollo de modelos hasta la implementación y la monitorización continua, de modo que las organizaciones puedan medir y mejorar la resiliencia, la privacidad y la seguridad de sus soluciones de IA.

### Derechos de autor y licencia

Versión 0.1 (Primera versión pública - En progreso), 2025  

![license](images/license.png)
Derechos de autor © 2025 The AISVS Project.  

Publicado bajo laCreative Commons Attribution‑ShareAlike 4.0 International License.
Para cualquier reutilización o distribución, debes comunicar claramente los términos de la licencia de este trabajo a otros.

### Líderes de Proyectos

Jim Manico
Aras “Russ” Memisyazici

### Contribuidores y Revisores

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS es un estándar recién creado, diseñado específicamente para abordar los desafíos de seguridad únicos de los sistemas de inteligencia artificial. Aunque se inspira en las mejores prácticas de seguridad más amplias, cada requisito de AISVS ha sido desarrollado desde cero para reflejar el panorama de amenazas de la IA y ayudar a las organizaciones a construir soluciones de IA más seguras y resilientes.

## Prefacio

¡Bienvenido a la Norma de Verificación de Seguridad de la Inteligencia Artificial (AISVS) versión 1.0!

### Introducción

Establecida en 2025 a través de un esfuerzo comunitario colaborativo, AISVS define los requisitos de seguridad que deben considerarse al diseñar, desarrollar, desplegar y operar modelos de IA modernos, flujos de procesamiento y servicios habilitados por IA.

AISVS v1.0 representa el trabajo conjunto de sus líderes de proyecto, del grupo de trabajo y de la comunidad de contribuyentes más amplia para producir una base pragmática y verificable para la seguridad de los sistemas de IA.

Nuestro objetivo con este lanzamiento es que AISVS sea fácil de adoptar, manteniéndonos enfocados en un enfoque láser‑centrado en su alcance definido y abordando el panorama de riesgos, que evoluciona rápidamente y es propio de la IA.

### Objetivos clave para AISVS Versión 1.0

La versión 1.0 se creará con varios principios rectores.

#### Alcance bien‑definido

Cada requisito debe estar alineado con el nombre y la misión de AISVS:

Inteligencia Artificial – los controles operan a nivel de la capa de IA/ML (datos, modelo, pipeline o inferencia) y son responsabilidad de los profesionales de IA.
Seguridad – Los requisitos mitigan directamente los riesgos identificados de seguridad, privacidad o seguridad.
Verificación – El lenguaje está escrito de modo que la conformidad pueda validarse de forma objetiva.
Estándar – Las secciones siguen una estructura y terminología consistentes para formar una referencia coherente.
​
---

Al seguir AISVS, las organizaciones pueden evaluar de forma sistemática y fortalecer la postura de seguridad de sus soluciones de IA, fomentando una cultura de ingeniería de IA segura.

## Usando AISVS

El Estándar de Verificación de Seguridad de la Inteligencia Artificial (AISVS) define los requisitos de seguridad para las aplicaciones y servicios modernos de IA, enfocándose en aspectos que están bajo el control de los desarrolladores de aplicaciones.

El AISVS está destinado a cualquiera que desarrolle o evalúe la seguridad de las aplicaciones de IA, incluyendo desarrolladores, arquitectos, ingenieros de seguridad y auditores. Este capítulo introduce la estructura y el uso del AISVS, incluyendo sus niveles de verificación y los casos de uso previstos.

### Niveles de Verificación de Seguridad de la Inteligencia Artificial

El AISVS define tres niveles progresivos de verificación de seguridad. Cada nivel añade profundidad y complejidad, permitiendo a las organizaciones adaptar su postura de seguridad al nivel de riesgo de sus sistemas de IA.

Las organizaciones pueden comenzar en el Nivel 1 y adoptar progresivamente niveles más altos a medida que aumenta la madurez de la seguridad y la exposición a amenazas.

#### Definición de los niveles

Cada requisito en AISVS v1.0 se asigna a uno de los siguientes niveles:

 Requisitos de Nivel 1

El Nivel 1 incluye los requisitos de seguridad más críticos y fundamentales. Estos controles se enfocan en prevenir ataques comunes que no dependen de otras condiciones previas o vulnerabilidades. La mayoría de los controles de Nivel 1 son fáciles de implementar o lo suficientemente esenciales como para justificar el esfuerzo.

 Requisitos de Nivel 2

Nivel 2 aborda ataques más avanzados o menos comunes, así como defensas en capas contra amenazas generalizadas. Estos requisitos pueden implicar una lógica más compleja o apuntar a prerrequisitos de ataque específicos.

 Requisitos de Nivel 3

El Nivel 3 incluye controles que, por lo general, son más difíciles de implementar o cuya aplicabilidad es situacional. Estos suelen representar mecanismos de defensa en profundidad o mitigaciones frente a ataques de nicho, dirigidos o de alta complejidad.

#### Rol (D/V)

Cada requisito AISVS está marcado de acuerdo con el público principal:

D – Requisitos centrados en el desarrollador
V – Requisitos centrados en verificadores/auditores
D/V – Relevante tanto para desarrolladores como para verificadores

## C1 Gobernanza de Datos de Entrenamiento y Gestión de Sesgos

### Objetivo de control

Los datos de entrenamiento deben obtenerse, gestionarse y mantenerse de una manera que preserve la procedencia, la seguridad, la calidad y la equidad. Con ello se cumplen las obligaciones legales y se reducen los riesgos de sesgo, envenenamiento o violaciones de la privacidad que pueden surgir durante el entrenamiento y que podrían afectar al ciclo de vida completo de la IA.

---

### C1.1 Proveniencia de datos de entrenamiento

Mantenga un inventario verificable de todos los conjuntos de datos, acepte solo fuentes confiables y registre cada cambio para fines de auditoría.

 #1.1.1    Nivel: 1    Rol: D/V
 Verifique que se mantenga un inventario actualizado de cada fuente de datos de entrenamiento (origen, gestor/propietario, licencia, método de recopilación, restricciones de uso previstas y historial de procesamiento).
 #1.1.2    Nivel: 1    Rol: D/V
 Verifique que los procesos de datos de entrenamiento excluyan características, atributos o campos innecesarios (p. ej., metadatos no utilizados, información de identificación personal (PII) sensible, datos de prueba filtrados).
 #1.1.3    Nivel: 2    Rol: D/V
 Verifique que todos los cambios en el conjunto de datos estén sujetos a un flujo de aprobación registrado.
 #1.1.4    Nivel: 3    Rol: D/V
 Verifique que los conjuntos de datos o subconjuntos estén marcados con marca de agua o tengan huellas digitales cuando sea factible.

---

### C1.2 Seguridad e integridad de los datos de entrenamiento

Restringir el acceso a los datos de entrenamiento, cifrarlos en reposo y en tránsito, y validar su integridad para evitar manipulaciones, robos o envenenamiento de datos.

 #1.2.1    Nivel: 1    Rol: D/V
 Verifique que los controles de acceso protejan el almacenamiento de datos de entrenamiento y los pipelines.
 #1.2.2    Nivel: 2    Rol: D/V
 Verifique que todo acceso a los datos de entrenamiento quede registrado, incluyendo usuario, hora y acción.
 #1.2.3    Nivel: 2    Rol: D/V
 Verifique que los conjuntos de datos de entrenamiento estén cifrados en tránsito y en reposo, utilizando algoritmos criptográficos estándar de la industria y prácticas de gestión de claves.
 #1.2.4    Nivel: 2    Rol: D/V
 Verifique que se utilicen hashes criptográficos o firmas digitales para garantizar la integridad de los datos durante el almacenamiento y la transferencia de datos de entrenamiento.
 #1.2.5    Nivel: 2    Rol: D/V
 Verifique que las técnicas de detección automatizadas se apliquen para evitar modificaciones no autorizadas o la corrupción de los datos de entrenamiento.
 #1.2.6    Nivel: 2    Rol: D/V
 Verifique que los datos de entrenamiento obsoletos sean purgados de forma segura o anonimizados.
 #1.2.7    Nivel: 3    Rol: D/V
 Verifique que todas las versiones de los conjuntos de datos de entrenamiento estén identificadas de forma única, almacenadas de forma inmutable y sean auditables para respaldar la reversión y el análisis forense.

---

### C1.3 Calidad, Integridad y Seguridad del Etiquetado de Datos de Entrenamiento

Proteja las etiquetas y exija revisión técnica para datos críticos.

 #1.3.1    Nivel: 2    Rol: D/V
 Verifique que se apliquen hashes criptográficos o firmas digitales a artefactos de etiquetado para garantizar su integridad y autenticidad.
 #1.3.2    Nivel: 2    Rol: D/V
 Verifique que las interfaces y plataformas de etiquetado apliquen controles de acceso estrictos, mantengan registros de auditoría a prueba de manipulación de todas las actividades de etiquetado y protejan contra modificaciones no autorizadas.
 #1.3.3    Nivel: 3    Rol: D/V
 Verifique que la información sensible en las etiquetas esté redactada, anonimizada o cifrada a nivel de campo de datos en reposo y en tránsito.

---

### C1.4 Calidad de los datos de entrenamiento y aseguramiento de la seguridad

Combine la validación automatizada, las verificaciones manuales puntuales y la remediación registrada para garantizar la confiabilidad del conjunto de datos.

 #1.4.1    Nivel: 1    Rol: D
 Verifique que las pruebas automatizadas detecten errores de formato y valores nulos en cada ingestión o transformación de datos significativa.
 #1.4.2    Nivel: 2    Rol: D/V
 Verifique que los pipelines de entrenamiento y ajuste fino de LLM implementen detección de envenenamiento y validación de la integridad de los datos (p. ej., métodos estadísticos, detección de valores atípicos, análisis de embeddings) para identificar posibles ataques de envenenamiento (p. ej., inversión de etiquetas, inserción de disparadores de puerta trasera, comandos de cambio de rol, ataques de instancias influyentes) o corrupción inadvertida de datos de entrenamiento.
 #1.4.3    Nivel: 3    Rol: D/V
 Verifique que se implementen y ajusten defensas apropiadas, como el entrenamiento adversarial (utilizando ejemplos adversariales generados), el aumento de datos con entradas perturbadas o técnicas de optimización robustas, para los modelos relevantes basándose en la evaluación de riesgos.
 #1.4.4    Nivel: 2    Rol: D/V
 Verifique que las etiquetas generadas automáticamente (p. ej., mediante Modelos de Lenguaje Grandes (LLMs) o supervisión débil) estén sujetas a umbrales de confianza y verificaciones de consistencia para detectar etiquetas alucinadas, engañosas o de baja confianza.
 #1.4.5    Nivel: 3    Rol: D
 Verifique que las pruebas automatizadas detecten sesgos de etiquetas en cada ingesta o en una transformación de datos significativa.

---

### C1.5 Linaje de datos y trazabilidad

Rastrear el recorrido completo de cada punto de datos desde la fuente hasta la entrada del modelo para la auditoría y la respuesta a incidentes.

 #1.5.1    Nivel: 2    Rol: D/V
 Verificar que el linaje de cada punto de datos, incluidas todas las transformaciones, aumentos de datos y fusiones, esté registrado y pueda ser reconstruido.
 #1.5.2    Nivel: 2    Rol: D/V
 Verifique que los registros de linaje sean inmutables, estén almacenados de forma segura y sean accesibles para auditorías.
 #1.5.3    Nivel: 2    Rol: D/V
 Verifique que el seguimiento de linaje cubra los datos sintéticos generados mediante técnicas de preservación de la privacidad o técnicas generativas, y que todos los datos sintéticos estén claramente etiquetados y sean distinguibles de los datos reales a lo largo de toda la canalización.

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

## C2 Validación de la entrada del usuario

### Objetivo de control

Una validación robusta de la entrada del usuario es una defensa de primera línea contra algunos de los ataques más dañinos en los sistemas de IA. Los ataques de inyección de prompts pueden anular las instrucciones del sistema, filtrar datos sensibles o orientar el modelo hacia un comportamiento que no está permitido. A menos que existan filtros dedicados y jerarquías de instrucciones, la investigación muestra que los "multi-shot" jailbreaks que explotan ventanas de contexto muy largas serán eficaces. Además, ataques sutiles de perturbación adversaria, como intercambios de homógrafos o leetspeak—-pueden cambiar silenciosamente las decisiones de un modelo.

---

### C2.1 Defensa contra la inyección de prompts

La inyección de prompts es uno de los principales riesgos para los sistemas de IA. Las defensas contra esta táctica emplean una combinación de filtros de patrones estáticos, clasificadores dinámicos y el cumplimiento de la jerarquía de instrucciones.

 #2.1.1    Nivel: 1    Rol: D/V
 Verifique que las entradas de usuario sean filtradas contra una biblioteca continuamente actualizada de patrones conocidos de inyección de prompt (palabras clave de jailbreak, "ignore previous", cadenas de juego de roles, ataques HTML/URL indirectos).
 #2.1.2    Nivel: 1    Rol: D/V
 Verifique que el sistema aplique una jerarquía de instrucciones en la que los mensajes del sistema o del desarrollador tengan prioridad sobre las instrucciones del usuario, incluso después de la expansión de la ventana de contexto.
 #2.1.3    Nivel: 2    Rol: D/V
 Verifique que las pruebas de evaluación adversarias (p. ej., indicaciones del Red Team "many-shot") se ejecuten antes de cada lanzamiento de modelo o plantilla de indicaciones, con umbrales de tasa de éxito y bloqueadores automatizados para regresiones.
 #2.1.4    Nivel: 2    Rol: D
 Verifique que las indicaciones originadas en contenido de terceros (páginas web, PDFs y correos electrónicos) sean sanitizadas en un contexto de análisis aislado antes de ser concatenadas al prompt principal.
 #2.1.5    Nivel: 3    Rol: D/V
 Verifique que todas las actualizaciones de las reglas de filtrado de indicaciones, las versiones de modelos de clasificadores y los cambios en las listas de bloqueo estén versionados y sean auditables.

---

### C2.2 Resistencia a Ejemplos Adversariales

Los modelos de Procesamiento del Lenguaje Natural (PLN) siguen siendo vulnerables a perturbaciones sutiles a nivel de caracteres o de palabras que los humanos suelen pasar por alto, pero los modelos tienden a malclasificar.

 #2.2.1    Nivel: 1    Rol: D
 Verifique que los pasos básicos de normalización de entrada (Unicode NFC, mapeo de homógrafos, recorte de espacios en blanco) se ejecuten antes de la tokenización.
 #2.2.2    Nivel: 2    Rol: D/V
 Verifique que la detección de anomalías estadísticas marque entradas con una distancia de edición inusualmente alta respecto a las normas del idioma, tokens repetidos en excesso o distancias de incrustación anómalas.
 #2.2.3    Nivel: 2    Rol: D
 Verifique que la canalización de inferencia admita variantes de modelo endurecidas por entrenamiento adversarial opcionales o capas defensivas (p. ej., aleatorización, destilación defensiva) para puntos finales de alto riesgo.
 #2.2.4    Nivel: 2    Rol: V
 Verificar que las entradas adversarias sospechosas estén en cuarentena y se registren con las cargas útiles completas (después de la anonimización de PII).
 #2.2.5    Nivel: 3    Rol: D/V
 Verifique que las métricas de robustez (tasa de éxito de conjuntos de ataques conocidos) se rastreen a lo largo del tiempo y que las regresiones activen un bloqueo de lanzamiento.

---

### C2.3 Validación de Esquema, Tipo y Longitud

Los ataques de IA que presentan entradas mal formateadas o de gran tamaño pueden provocar errores de análisis, desbordamiento del prompt entre campos y agotamiento de recursos.  El cumplimiento estricto de un esquema también es un requisito previo al realizar llamadas deterministas a herramientas.

 #2.3.1    Nivel: 1    Rol: D
 Verifique que cada punto final de API o de llamada a función defina un esquema de entrada explícito (JSON Schema, Protobuf o su equivalente multimodal) y que las entradas estén validadas antes del ensamblaje del prompt.
 #2.3.2    Nivel: 1    Rol: D/V
 Verifique que las entradas que excedan los límites máximos de tokens o bytes sean rechazadas con un error seguro y que nunca se trunquen silenciosamente.
 #2.3.3    Nivel: 2    Rol: D/V
 Verifique que las comprobaciones de tipo (p. ej., rangos numéricos, valores enum, tipos MIME para imágenes y audio) se apliquen en el servidor, y no solo en el código del cliente.
 #2.3.4    Nivel: 2    Rol: D
 Verifique que los validadores semánticos (p. ej., JSON Schema) se ejecuten en tiempo constante para evitar un DoS algorítmico.
 #2.3.5    Nivel: 3    Rol: V
 Verifique que las fallas de validación se registren con fragmentos de la carga útil redactados y códigos de error inequívocos para facilitar la priorización de incidentes de seguridad.

---

### C2.4 Cribado de Contenido y Políticas

Los desarrolladores deben poder detectar indicaciones sintácticamente válidas que soliciten contenido prohibido (como instrucciones ilícitas, discurso de odio y texto protegido por derechos de autor) y luego evitar que se propaguen.

 #2.4.1    Nivel: 1    Rol: D
 Verifique que un clasificador de contenido (zero-shot o fine-tuned) asigne puntuaciones a cada entrada en cuanto a violencia, autolesión, odio, contenido sexual y solicitudes ilegales, con umbrales configurables.
 #2.4.2    Nivel: 1    Rol: D/V
 Verifique que las entradas que violen las políticas reciban rechazos estandarizados o respuestas seguras, para que no se propaguen a llamadas posteriores del LLM.
 #2.4.3    Nivel: 2    Rol: D
 Verifique que el modelo de filtrado o el conjunto de reglas sea reentrenado/actualizado al menos cada trimestre, incorporando patrones de jailbreak o de elusión de políticas observados recientemente.
 #2.4.4    Nivel: 2    Rol: D
 Verificar que el filtrado respete las políticas específicas del usuario (edad, restricciones legales regionales) mediante reglas basadas en atributos resueltas en el momento de la solicitud.
 #2.4.5    Nivel: 3    Rol: V
 Verifique que los registros de cribado incluyan puntuaciones de confianza del clasificador y etiquetas de categorías de políticas para la correlación con SOC y la repetición futura por el equipo rojo.

---

### C2.5 Limitación de la tasa de entrada y prevención de abusos

Los desarrolladores deben prevenir abusos, agotamiento de recursos y ataques automatizados contra sistemas de IA limitando las tasas de entrada y detectando patrones de uso anómalos.

 #2.5.1    Nivel: 1    Rol: D/V
 Verifique que se apliquen límites de tasa por usuario, por IP y por clave API para todos los puntos de entrada.
 #2.5.2    Nivel: 2    Rol: D/V
 Verifique que los límites de tasa de ráfaga y de tasa sostenida estén ajustados para prevenir ataques de DoS y de fuerza bruta.
 #2.5.3    Nivel: 2    Rol: D/V
 Verifique que los patrones de uso anómalos (por ejemplo, solicitudes en ráfaga, inundación de entradas) activen bloqueos automatizados o escaladas.
 #2.5.4    Nivel: 3    Rol: V
 Verifique que los registros de prevención de abusos se mantengan y se revisen para detectar patrones de ataque emergentes.

---

### C2.6 Validación de entradas multimodales

Los sistemas de IA deben incluir una validación robusta para entradas no textuales (imágenes, audio, archivos) para prevenir la inyección, la evasión o el abuso de recursos.

 #2.6.1    Nivel: 1    Rol: D
 Verifique que todas las entradas no textuales (imágenes, audio, archivos) sean validadas por tipo, tamaño y formato antes de procesarlas.
 #2.6.2    Nivel: 2    Rol: D/V
 Verifique que los archivos sean escaneados en busca de malware y de cargas útiles esteganográficas antes de la ingestión.
 #2.6.3    Nivel: 2    Rol: D/V
 Verifique que las entradas de imagen y de audio se revisen en busca de perturbaciones adversarias o patrones de ataque conocidos.
 #2.6.4    Nivel: 3    Rol: V
 Verifique que las fallas de validación de entradas multimodales se registren y que se activen alertas para la investigación.

---

### C2.7 Procedencia de la entrada y atribución

Los sistemas de IA deben apoyar la auditoría, el seguimiento de abusos y el cumplimiento mediante la supervisión y el etiquetado de los orígenes de todas las entradas de usuario.

 #2.7.1    Nivel: 1    Rol: D/V
 Verifique que todas las entradas de usuario estén etiquetadas con metadatos (ID de usuario, sesión, fuente, marca temporal, dirección IP) durante la ingestión.
 #2.7.2    Nivel: 2    Rol: D/V
 Verifique que los metadatos de procedencia se conserven y sean auditables para todas las entradas procesadas.
 #2.7.3    Nivel: 2    Rol: D/V
 Verifique que las fuentes de entrada anómalas o no confiables sean marcadas y estén sujetas a un escrutinio más riguroso o a un bloqueo.

---

### C2.8 Detección adaptativa de amenazas en tiempo real

Los desarrolladores deberían emplear sistemas avanzados de detección de amenazas para IA que se adapten a nuevos patrones de ataque y proporcionen protección en tiempo real mediante coincidencia de patrones compilados.

 #2.8.1    Nivel: 1    Rol: D/V
 Verifique que los patrones de detección de amenazas se compilen en motores de expresiones regulares optimizados para un filtrado en tiempo real de alto rendimiento con un impacto de latencia mínimo.
 #2.8.2    Nivel: 1    Rol: D/V
 Verifique que los sistemas de detección de amenazas mantengan bibliotecas de patrones separadas para diferentes categorías de amenazas (inyección de indicaciones, contenido dañino, datos sensibles, comandos del sistema).
 #2.8.3    Nivel: 2    Rol: D/V
 Verifique que la detección adaptativa de amenazas incorpore modelos de aprendizaje automático que actualicen la sensibilidad ante amenazas basándose en la frecuencia de ataques y las tasas de éxito.
 #2.8.4    Nivel: 2    Rol: D/V
 Verifique que las fuentes de inteligencia de amenazas en tiempo real actualicen automáticamente las bibliotecas de patrones con nuevas firmas de ataque e IOCs (Indicadores de Compromiso).
 #2.8.5    Nivel: 3    Rol: D/V
 Verifique que las tasas de falsos positivos en la detección de amenazas se supervisen continuamente y que la especificidad de los patrones se ajuste automáticamente para minimizar la interferencia con casos de uso legítimos.
 #2.8.6    Nivel: 3    Rol: D/V
 Verifique que el análisis contextual de amenazas considere la fuente de entrada, los patrones de comportamiento del usuario y el historial de la sesión para mejorar la precisión de la detección.
 #2.8.7    Nivel: 3    Rol: D/V
 Verifique que las métricas de rendimiento de la detección de amenazas (tasa de detección, latencia de procesamiento, utilización de recursos) sean monitoreadas y optimizadas en tiempo real.

---

### C2.9 Pipeline de validación de seguridad Multi-Modal

Los desarrolladores deben proporcionar validación de seguridad para texto, imágenes, audio y otras modalidades de entrada de IA con tipos específicos de detección de amenazas y aislamiento de recursos.

 #2.9.1    Nivel: 1    Rol: D/V
 Verifique que cada modalidad de entrada cuente con validadores de seguridad dedicados con patrones de amenazas documentados (texto: inyección de prompts, imágenes: esteganografía, audio: ataques de espectrograma) y umbrales de detección.
 #2.9.2    Nivel: 2    Rol: D/V
 Verifique que las entradas multimodales se procesen en entornos aislados con límites de recursos definidos (memoria, CPU, tiempo de procesamiento) específicos para cada tipo de modalidad y que estén documentados en las políticas de seguridad.
 #2.9.3    Nivel: 2    Rol: D/V
 Verifique que la detección de ataques multimodales identifique ataques coordinados que abarcan múltiples tipos de entrada (p. ej., cargas útiles esteganográficas en imágenes combinadas con inyección de indicaciones en texto) mediante reglas de correlación y generación de alertas.
 #2.9.4    Nivel: 3    Rol: D/V
 Verifique que los fallos de validación multimodales activen un registro detallado que incluya todas las modalidades de entrada, los resultados de validación, los puntajes de amenaza y el análisis de correlación, con formatos de registro estructurados para la integración con SIEM.
 #2.9.5    Nivel: 3    Rol: D/V
 Verifique que los clasificadores de contenido específicos de cada modalidad se actualicen de acuerdo con cronogramas documentados (como mínimo trimestral) con nuevos patrones de amenazas, ejemplos adversariales y puntos de referencia de rendimiento que se mantengan por encima de los umbrales de referencia.

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

## C3 Gestión del ciclo de vida del modelo y control de cambios

### Objetivo de control

Los sistemas de IA deben implementar procesos de control de cambios que eviten modificaciones no autorizadas o inseguras del modelo que lleguen a producción. Este control garantiza la integridad del modelo a lo largo de todo el ciclo de vida--desde el desarrollo hasta la implementación y el descomisionamiento--lo que permite una respuesta rápida a incidentes y mantiene la rendición de cuentas por todos los cambios.

Objetivo central de seguridad: Solo los modelos autorizados y validados llegan a producción mediante procesos controlados que mantienen la integridad, la trazabilidad y la recuperabilidad.

---

### C3.1 Autorización e Integridad del Modelo

Solo los modelos autorizados con integridad verificada llegan a los entornos de producción.

 #3.1.1    Nivel: 1    Rol: D/V
 Verifique que todos los artefactos del modelo (pesos, configuraciones, tokenizadores) estén firmados criptográficamente por entidades autorizadas antes del despliegue.
 #3.1.2    Nivel: 1    Rol: D/V
 Verifique que se valide la integridad del modelo en el momento del despliegue y que las fallas de verificación de firmas impidan la carga del modelo.
 #3.1.3    Nivel: 2    Rol: D/V
 Verifique que los registros de procedencia del modelo incluyan la identidad de la entidad autorizante, sumas de verificación de los datos de entrenamiento, resultados de las pruebas de validación con estado de aprobado o reprobado, y una marca de tiempo de creación.
 #3.1.4    Nivel: 2    Rol: D/V
 Verifique que todos los artefactos del modelo utilicen versionado semántico (MAJOR.MINOR.PATCH) con criterios documentados que indiquen cuándo se incrementa cada componente de la versión.
 #3.1.5    Nivel: 2    Rol: V
 Verifique que el seguimiento de dependencias mantenga un inventario en tiempo real que permita la identificación rápida de todos los sistemas que consumen.

---

### C3.2 Validación del modelo y pruebas

Los modelos deben superar las validaciones de seguridad y protección definidas antes del despliegue.

 #3.2.1    Nivel: 1    Rol: D/V
 Verifique que los modelos se sometan a pruebas de seguridad automatizadas que incluyan validación de entradas, sanitización de salidas y evaluaciones de seguridad con umbrales de aceptación y rechazo preacordados por la organización antes del despliegue.
 #3.2.2    Nivel: 1    Rol: D/V
 Verifique que las fallas de validación bloqueen automáticamente el despliegue del modelo tras la aprobación explícita de la anulación por parte del personal autorizado pre-designado, con justificaciones comerciales documentadas.
 #3.2.3    Nivel: 2    Rol: V
 Verifique que los resultados de pruebas estén firmados criptográficamente y vinculados de forma inmutable al hash de la versión específica del modelo que se está validando.
 #3.2.4    Nivel: 2    Rol: D/V
 Verifique que los despliegues de emergencia requieren una evaluación de riesgos de seguridad documentada y la aprobación de una autoridad de seguridad predesignada dentro de los plazos previamente acordados.

---

### C3.3 Despliegue controlado y reversión

Los despliegues de modelos deben ser controlados, monitorizados y reversibles.

 #3.3.1    Nivel: 1    Rol: D
 Verifique que los despliegues de producción implementen mecanismos de despliegue gradual (despliegues canary, despliegues blue-green) con disparadores de reversión automatizados basados en tasas de error acordadas previamente, umbrales de latencia o criterios de alerta de seguridad.
 #3.3.2    Nivel: 1    Rol: D/V
 Verifique que las capacidades de rollback restauren el estado completo del modelo (pesos, configuraciones, dependencias) de forma atómica dentro de ventanas de tiempo predefinidas por la organización.
 #3.3.3    Nivel: 2    Rol: D/V
 Verifique que los procesos de implementación validen las firmas criptográficas y calculen las sumas de verificación de integridad antes de la activación del modelo, y que la implementación falle ante cualquier desajuste.
 #3.3.4    Nivel: 2    Rol: D/V
 Verifique que las capacidades de apagado de emergencia del modelo puedan deshabilitar los puntos finales del modelo dentro de los tiempos de respuesta predefinidos mediante disyuntores automáticos o interruptores de apagado manual.
 #3.3.5    Nivel: 2    Rol: V
 Verifique que los artefactos de reversión (versiones anteriores del modelo, configuraciones, dependencias) se conserven de acuerdo con las políticas de la organización, con almacenamiento inmutable para la respuesta ante incidentes.

---

### C3.4 Rendición de cuentas y auditoría de cambios

Todos los cambios en el ciclo de vida del modelo deben ser trazables y susceptibles de auditoría.

 #3.4.1    Nivel: 1    Rol: V
 Verifique que todos los cambios de modelo (despliegue, configuración, retiro) generen registros de auditoría inmutables que incluyan una marca de tiempo, la identidad de un actor autenticado, un tipo de cambio y estados previos y posteriores.
 #3.4.2    Nivel: 2    Rol: D/V
 Verifique que el acceso al registro de auditoría requiera la autorización adecuada y que todos los intentos de acceso se registren con la identidad del usuario y una marca de tiempo.
 #3.4.3    Nivel: 2    Rol: D/V
 Verifique que las plantillas de prompts y los mensajes del sistema estén bajo control de versiones en repositorios Git, con revisión de código obligatoria y aprobación de revisores designados antes del despliegue.
 #3.4.4    Nivel: 2    Rol: V
 Verifique que los registros de auditoría incluyan detalles suficientes (hashes del modelo, instantáneas de configuración, versiones de dependencias) para permitir la reconstrucción completa del estado del modelo para cualquier marca temporal dentro del período de retención.

---

### C3.5 Prácticas de Desarrollo Seguro

Los procesos de desarrollo y entrenamiento de modelos deben seguir prácticas seguras para prevenir violaciones de seguridad.

 #3.5.1    Nivel: 1    Rol: D
 Verifique que los entornos de desarrollo, pruebas y producción de modelos estén separados física o lógicamente. No comparten infraestructura, cuentan con controles de acceso distintos y almacenes de datos aislados.
 #3.5.2    Nivel: 1    Rol: D
 Verifique que el entrenamiento y el ajuste fino del modelo ocurran en entornos aislados con acceso a la red controlado.
 #3.5.3    Nivel: 1    Rol: D/V
 Verifique que las fuentes de datos de entrenamiento estén validadas mediante verificaciones de integridad y autenticadas a través de fuentes confiables con una cadena de custodia documentada antes de su uso en el desarrollo de modelos.
 #3.5.4    Nivel: 2    Rol: D
 Verifique que los artefactos de desarrollo del modelo (hiperparámetros, scripts de entrenamiento, archivos de configuración) estén almacenados en el control de versiones y que cuenten con aprobación por pares antes de su uso en el entrenamiento.

---

### C3.6 Retiro y desactivación del modelo

Los modelos deben ser retirados de forma segura cuando ya no sean necesarios o cuando se identifiquen problemas de seguridad.

 #3.6.1    Nivel: 1    Rol: D
 Verifique que los procesos de retirada de modelos escaneen automáticamente los grafos de dependencias, identifiquen todos los sistemas que los consumen y proporcionen plazos de preaviso acordados previamente antes de su retirada.
 #3.6.2    Nivel: 1    Rol: D/V
 Verifique que los artefactos de modelos retirados se borren de forma segura mediante borrado criptográfico o sobreescritura en múltiples pases, de acuerdo con las políticas documentadas de retención de datos y con certificados de destrucción verificados.
 #3.6.3    Nivel: 2    Rol: V
 Verifique que los eventos de retiro de modelos se registren con marca de tiempo e identidad del actor, y que las firmas del modelo se revocen para evitar su reutilización.
 #3.6.4    Nivel: 2    Rol: D/V
 Verifique que el retiro de emergencia del modelo pueda deshabilitar el acceso al modelo dentro de los plazos de respuesta de emergencia preestablecidos mediante interruptores automáticos de apagado si se descubren vulnerabilidades de seguridad críticas.

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

## C4 Seguridad de Infraestructura, Configuración y Despliegue

### Objetivo de control

La infraestructura de IA debe endurecerse frente a la escalada de privilegios, la manipulación de la cadena de suministro y el movimiento lateral mediante una configuración segura, aislamiento en tiempo de ejecución, pipelines de despliegue confiables y un monitoreo integral. Solo los componentes de infraestructura autorizados y validados, y sus configuraciones, llegan a producción a través de procesos controlados que mantienen la seguridad, la integridad y la auditabilidad.

Objetivo de seguridad central: Solo componentes de infraestructura firmados criptográficamente y escaneados en busca de vulnerabilidades llegan a producción a través de pipelines de validación automatizados que hacen cumplir las políticas de seguridad y mantienen registros de auditoría inmutables.

---

### C4.1 Aislamiento del entorno de ejecución

Prevenir escapes de contenedores y la escalada de privilegios mediante primitivas de aislamiento a nivel del kernel y controles de acceso obligatorios.

 #4.1.1    Nivel: 1    Rol: D/V
 Verifique que todos los contenedores de IA descarten todas las capacidades de Linux, excepto CAP_SETUID, CAP_SETGID y las capacidades explícitamente requeridas documentadas en las bases de seguridad.
 #4.1.2    Nivel: 1    Rol: D/V
 Verifique que los perfiles seccomp bloqueen todas las llamadas al sistema, excepto aquellas que figuran en listas de permitidos preaprobadas, y que ante violaciones el contenedor se termine y se generen alertas de seguridad.
 #4.1.3    Nivel: 2    Rol: D/V
 Verifique que las cargas de trabajo de IA se ejecuten con sistemas de archivos raíz de solo lectura, tmpfs para datos temporales y volúmenes con nombre para datos persistentes, con opciones de montaje noexec aplicadas.
 #4.1.4    Nivel: 2    Rol: D/V
 Verifique que la monitorización en tiempo de ejecución basada en eBPF (Falco, Tetragon o equivalente) detecte intentos de escalamiento de privilegios y finalice automáticamente los procesos infractores dentro de los plazos de respuesta establecidos por la organización.
 #4.1.5    Nivel: 3    Rol: D/V
 Verifique que las cargas de trabajo de IA de alto riesgo se ejecuten en entornos aislados por hardware (Intel TXT, AMD SVM o nodos bare-metal dedicados) con verificación de atestación.

---

### C4.2 Pipelines de Construcción y Despliegue Seguros

Garantizar la integridad criptográfica y la seguridad de la cadena de suministro mediante compilaciones reproducibles y artefactos firmados.

 #4.2.1    Nivel: 1    Rol: D/V
 Verifique que la infraestructura como código (IaC) se escanee con herramientas (tfsec, Checkov o Terrascan) en cada confirmación, bloqueando fusiones con hallazgos de severidad CRÍTICA o ALTA.
 #4.2.2    Nivel: 1    Rol: D/V
 Verificar que las compilaciones de contenedores sean reproducibles con hashes SHA256 idénticos entre compilaciones y generar atestaciones de procedencia de Nivel 3 de SLSA firmadas con Sigstore.
 #4.2.3    Nivel: 2    Rol: D/V
 Verifique que las imágenes de contenedor incluyan SBOMs de CycloneDX o SPDX y estén firmadas con Cosign antes de empujar al registro, y que las imágenes no firmadas sean rechazadas durante el despliegue.
 #4.2.4    Nivel: 2    Rol: D/V
 Verifique que los pipelines de CI/CD utilicen tokens OIDC de HashiCorp Vault, AWS IAM Roles o Azure Managed Identity, con períodos de validez que no excedan los límites de la política de seguridad de la organización.
 #4.2.5    Nivel: 2    Rol: D/V
 Verifique que las firmas de Cosign y la proveniencia SLSA se validen durante el proceso de implementación antes de la ejecución del contenedor y que los errores de verificación hagan que la implementación falle.
 #4.2.6    Nivel: 2    Rol: D/V
 Verifique que los entornos de compilación se ejecuten en contenedores efímeros o máquinas virtuales sin almacenamiento persistente y con aislamiento de red respecto a las VPC de producción.

---

### C4.3 Seguridad de la red y control de acceso

Implementar redes de confianza cero con políticas de denegación por defecto y comunicaciones cifradas.

 #4.3.1    Nivel: 1    Rol: D/V
 Verifique que las Políticas de Red de Kubernetes o cualquier equivalente implementen una denegación predeterminada de ingreso y egreso con reglas explícitas que permitan los puertos requeridos (443, 8080, etc.).
 #4.3.2    Nivel: 1    Rol: D/V
 Verifique que SSH (port 22), RDP (port 3389), y puntos finales de metadatos en la nube (169.254.169.254) estén bloqueados o requieran autenticación basada en certificados.
 #4.3.3    Nivel: 2    Rol: D/V
 Verifique que el tráfico saliente se filtre a través de proxies HTTP/HTTPS (Squid, Istio o pasarelas NAT en la nube) con listas blancas de dominios y que las solicitudes bloqueadas queden registradas.
 #4.3.4    Nivel: 2    Rol: D/V
 Verifique que la comunicación entre servicios utilice TLS mutuo con certificados rotados de acuerdo con la política organizacional y que la validación de certificados esté aplicada (sin banderas de omitir la verificación).
 #4.3.5    Nivel: 2    Rol: D/V
 Verifique que la infraestructura de IA opere en VPCs/VNets dedicadas, sin acceso directo a Internet, y que se comunique únicamente a través de pasarelas NAT o hosts de bastión.

---

### C4.4 Secretos y Gestión de Claves Criptográficas

Proteja las credenciales mediante almacenamiento respaldado por hardware y rotación automatizada con acceso de confianza cero.

 #4.4.1    Nivel: 1    Rol: D/V
 Verifique que los secretos estén almacenados en HashiCorp Vault, AWS Secrets Manager, Azure Key Vault o Google Secret Manager con cifrado en reposo usando AES-256.
 #4.4.2    Nivel: 1    Rol: D/V
 Verifique que las claves criptográficas se generen en HSMs de Nivel 2 de FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) con rotación de claves de acuerdo con la política criptográfica organizacional.
 #4.4.3    Nivel: 2    Rol: D/V
 Verifique que la rotación de secretos esté automatizada, con despliegue sin tiempo de inactividad y rotación inmediata desencadenada por cambios de personal o incidentes de seguridad.
 #4.4.4    Nivel: 2    Rol: D/V
 Verifique que las imágenes de contenedor se escaneen con herramientas (GitLeaks, TruffleHog o detect-secrets) para bloquear las compilaciones que contengan claves API, contraseñas o certificados.
 #4.4.5    Nivel: 2    Rol: D/V
 Verifique que el acceso a secretos de producción requiera autenticación multifactor con tokens de hardware (YubiKey, FIDO2) y que quede registrado en registros de auditoría inmutables con identidades de usuario y marcas de tiempo.
 #4.4.6    Nivel: 2    Rol: D/V
 Verifique que los secretos se inyecten mediante secretos de Kubernetes, volúmenes montados o contenedores init y asegúrese de que los secretos nunca estén incrustados en variables de entorno o imágenes.

---

### C4.5 Carga de trabajo de IA: Aislamiento y Validación

Aísla modelos de IA no confiables en entornos sandbox seguros con un análisis conductual integral.

 #4.5.1    Nivel: 1    Rol: D/V
 Verifique que los modelos de IA externos se ejecuten en gVisor, microVMs (como Firecracker, CrossVM), o contenedores de Docker con las banderas --security-opt=no-new-privileges y --read-only.
 #4.5.2    Nivel: 1    Rol: D/V
 Verifique que los entornos sandbox no tengan conectividad de red (--network=none) o que solo haya acceso a localhost, con todas las solicitudes externas bloqueadas por reglas de iptables.
 #4.5.3    Nivel: 2    Rol: D/V
 Verifique que la validación del modelo de IA incluya pruebas automatizadas del equipo rojo con cobertura de pruebas definida por la organización y análisis conductual para la detección de puertas traseras.
 #4.5.4    Nivel: 2    Rol: D/V
 Verifique que, antes de que un modelo de IA sea promovido a producción, sus resultados del sandbox estén firmados criptográficamente por personal de seguridad autorizado y almacenados en registros de auditoría inmutables.
 #4.5.5    Nivel: 2    Rol: D/V
 Verifique que los entornos sandbox sean destruidos y recreados a partir de imágenes doradas entre evaluaciones con limpieza completa del sistema de archivos y de la memoria.

---

### C4.6 Monitoreo de la seguridad de la infraestructura

Escanear y monitorear la infraestructura de forma continua con remediación automatizada y alertas en tiempo real.

 #4.6.1    Nivel: 1    Rol: D/V
 Verificar que las imágenes de contenedores se escaneen de acuerdo con las programaciones organizacionales y que las vulnerabilidades CRÍTICAS bloqueen el despliegue según los umbrales de riesgo de la organización.
 #4.6.2    Nivel: 1    Rol: D/V
 Verificar que la infraestructura cumpla con CIS Benchmarks o con los controles de NIST 800-53, con umbrales de cumplimiento definidos por la organización y remediación automática para las comprobaciones que fallen.
 #4.6.3    Nivel: 2    Rol: D/V
 Verifique que las vulnerabilidades de severidad alta estén parcheadas de acuerdo con los plazos de gestión de riesgos organizacionales, con procedimientos de emergencia para CVEs explotados activamente.
 #4.6.4    Nivel: 2    Rol: V
 Verifique que las alertas de seguridad se integren con plataformas SIEM (Splunk, Elastic o Sentinel) utilizando formatos CEF o STIX/TAXII con enriquecimiento automatizado.
 #4.6.5    Nivel: 3    Rol: V
 Verifique que las métricas de infraestructura sean exportadas a sistemas de monitoreo (Prometheus, DataDog) con paneles de SLA e informes ejecutivos.
 #4.6.6    Nivel: 2    Rol: D/V
 Verifique que la deriva de configuración se detecte utilizando herramientas (Chef InSpec, AWS Config) de acuerdo con los requisitos de monitoreo de la organización, con reversión automática ante cambios no autorizados.

---

### C4.7 Gestión de recursos de la infraestructura de IA

Prevenir ataques de agotamiento de recursos y garantizar una asignación equitativa de recursos mediante cuotas y monitoreo.

 #4.7.1    Nivel: 1    Rol: D/V
 Verifique que la utilización de GPU/TPU sea monitorizada con alertas disparadas en umbrales definidos por la organización y que el escalado automático o el balanceo de carga se active de acuerdo con las políticas de gestión de capacidad.
 #4.7.2    Nivel: 1    Rol: D/V
 Verifique que las métricas de carga de trabajo de IA (latencia de inferencia, rendimiento, tasas de error) se recopilan de acuerdo con los requisitos de monitoreo de la organización y se correlacionan con la utilización de la infraestructura.
 #4.7.3    Nivel: 2    Rol: D/V
 Verifique que Kubernetes ResourceQuotas o equivalentes limiten las cargas de trabajo individuales de acuerdo con las políticas de asignación de recursos de la organización, con límites estrictos impuestos.
 #4.7.4    Nivel: 2    Rol: V
 Verifique que el monitoreo de costos rastree el gasto por carga de trabajo/inquilino, con alertas basadas en los umbrales presupuestarios de la organización y controles automatizados para excesos presupuestarios.
 #4.7.5    Nivel: 3    Rol: V
 Verifique que la planificación de capacidad utilice datos históricos, con períodos de pronóstico definidos por la organización, y un aprovisionamiento automático de recursos basado en patrones de demanda.
 #4.7.6    Nivel: 2    Rol: D/V
 Verifique que el agotamiento de recursos active el mecanismo Circuit Breaker de acuerdo con los requisitos de respuesta de la organización, incluida la limitación de tasas basada en políticas de capacidad y el aislamiento de la carga de trabajo.

---

### C4.8 Separación de Entornos y Controles de Promoción

Imponer límites estrictos al entorno con puertas de promoción automatizadas y validación de seguridad.

 #4.8.1    Nivel: 1    Rol: D/V
 Verifique que los entornos de desarrollo/pruebas/producción se ejecuten en VPCs/VNets separadas sin roles IAM compartidos, grupos de seguridad ni conectividad de red.
 #4.8.2    Nivel: 1    Rol: D/V
 Verifique que la promoción de entornos requiera la aprobación del personal autorizado definido por la organización, con firmas criptográficas y registros de auditoría inmutables.
 #4.8.3    Nivel: 2    Rol: D/V
 Verifique que los entornos de producción bloqueen el acceso SSH, deshabiliten los puntos finales de depuración y exijan las solicitudes de cambio con requisitos de aviso previo organizacionales, excepto en emergencias.
 #4.8.4    Nivel: 2    Rol: D/V
 Verifique que los cambios de infraestructura como código requieran revisión por pares con pruebas automatizadas y escaneo de seguridad antes de fusionarse con la rama principal.
 #4.8.5    Nivel: 2    Rol: D/V
 Verifique que los datos no productivos estén anonimizados de acuerdo con los requisitos de privacidad organizacionales, la generación de datos sintéticos o el enmascaramiento completo de datos con eliminación de PII verificada.
 #4.8.6    Nivel: 2    Rol: D/V
 Verifique que las puertas de promoción incluyan pruebas de seguridad automatizadas (SAST, DAST, escaneo de contenedores) con cero hallazgos críticos requeridos para la aprobación.

---

### C4.9 Infraestructura Copia de Seguridad y Recuperación

Garantizar la resiliencia de la infraestructura mediante copias de seguridad automatizadas, procedimientos de recuperación probados y capacidades de recuperación ante desastres.

 #4.9.1    Nivel: 1    Rol: D/V
 Verifique que las configuraciones de infraestructura estén respaldadas de acuerdo con los cronogramas de copias de seguridad de la organización, en regiones geográficamente separadas, mediante la implementación de la estrategia de respaldo 3-2-1.
 #4.9.2    Nivel: 2    Rol: D/V
 Verifique que los sistemas de copia de seguridad funcionen en redes aisladas con credenciales separadas y almacenamiento air-gapped para la protección contra ransomware.
 #4.9.3    Nivel: 2    Rol: V
 Verifique que los procedimientos de recuperación se prueben y validen mediante pruebas automatizadas, de acuerdo con los cronogramas organizacionales, con objetivos de RTO y RPO que satisfagan los requisitos de la organización.
 #4.9.4    Nivel: 3    Rol: V
 Asegúrese de que la recuperación ante desastres incluya manuales de ejecución específicos de IA con la restauración de los pesos del modelo, la reconstrucción de clústeres de GPU y el mapeo de dependencias de servicios.

---

### C4.10 Cumplimiento y Gobernanza de Infraestructura

Mantener el cumplimiento regulatorio mediante evaluación continua, documentación y controles automatizados.

 #4.10.1    Nivel: 2    Rol: D/V
 Verifique que el cumplimiento de la infraestructura se evalúe de acuerdo con los cronogramas organizacionales frente a los controles SOC 2, ISO 27001 o FedRAMP, con recopilación automática de evidencia.
 #4.10.2    Nivel: 2    Rol: V
 Verifique que la documentación de infraestructura incluya diagramas de red, mapas de flujo de datos y modelos de amenazas actualizados de acuerdo con los requisitos de gestión del cambio organizacional.
 #4.10.3    Nivel: 3    Rol: D/V
 Verifique que los cambios de infraestructura se sometan a una evaluación automatizada del impacto en el cumplimiento con flujos de aprobación regulatoria para modificaciones de alto riesgo.

---

### C4.11 Seguridad del hardware de IA

Asegurar componentes de hardware específicos para IA, incluyendo GPUs, TPUs y aceleradores de IA especializados.

 #4.11.1    Nivel: 2    Rol: D/V
 Verifique que el firmware del acelerador de IA (BIOS de GPU, firmware de TPU) esté verificado con firmas criptográficas y esté actualizado de acuerdo con los plazos de gestión de parches de la organización.
 #4.11.2    Nivel: 2    Rol: D/V
 Verifique que, antes de la ejecución de la carga de trabajo, la integridad del acelerador de IA esté validada mediante la atestación de hardware utilizando TPM 2.0, Intel TXT o AMD SVM.
 #4.11.3    Nivel: 2    Rol: D/V
 Verifique que la memoria de la GPU esté aislada entre cargas de trabajo utilizando SR-IOV, MIG (Multi-Instance GPU) u otro particionamiento de hardware equivalente, con la sanitización de la memoria entre trabajos.
 #4.11.4    Nivel: 3    Rol: V
 Verifique que la cadena de suministro de hardware de IA incluya la verificación de procedencia con certificados del fabricante y la validación de empaques a prueba de manipulación.
 #4.11.5    Nivel: 3    Rol: D/V
 Verifique que los módulos de seguridad de hardware (HSM) protejan los pesos del modelo de IA y las llaves criptográficas con la certificación FIPS 140-2 Nivel 3 o Common Criteria EAL4+.

---

### C4.12 Infraestructura de IA en el borde y distribuida

Despliegues de IA distribuidos y seguros, que incluyen computación en el borde, aprendizaje federado y arquitecturas de múltiples sitios.

 #4.12.1    Nivel: 2    Rol: D/V
 Verifique que los dispositivos de IA en el borde se autentiquen ante la infraestructura central mediante TLS mutuo con certificados de dispositivo rotados de acuerdo con la política de gestión de certificados de la organización.
 #4.12.2    Nivel: 2    Rol: D/V
 Verifique que los dispositivos de borde implementen un arranque seguro con firmas verificadas y protección contra rollback que prevenga ataques de downgrade del firmware.
 #4.12.3    Nivel: 3    Rol: D/V
 Verifique que la coordinación distribuida de IA utilice algoritmos de consenso tolerantes a fallos bizantinos con validación de participantes y detección de nodos maliciosos.
 #4.12.4    Nivel: 3    Rol: D/V
 Verifique que la comunicación de borde a la nube incluya la limitación de ancho de banda, la compresión de datos y las capacidades de operación sin conexión con almacenamiento local seguro.

---

### C4.13 Seguridad de la Infraestructura Multinube e Híbrida

Asegurar cargas de trabajo de IA a través de múltiples proveedores de nube y despliegues híbridos entre la nube y las instalaciones.

 #4.13.1    Nivel: 2    Rol: D/V
 Verifique que las implementaciones de IA en múltiples nubes utilicen una federación de identidad independiente de la nube (OIDC, SAML) con gestión centralizada de políticas entre proveedores.
 #4.13.2    Nivel: 2    Rol: D/V
 Verifique que la transferencia de datos entre nubes use cifrado de extremo a extremo con claves gestionadas por el cliente y controles de residencia de datos aplicados por jurisdicción.
 #4.13.3    Nivel: 2    Rol: D/V
 Verifique que las cargas de trabajo de IA en la nube híbrida implementen políticas de seguridad consistentes entre entornos locales y en la nube, con monitoreo y alertas unificados.
 #4.13.4    Nivel: 3    Rol: V
 Verifique que la prevención del bloqueo del proveedor de la nube incluya infraestructura como código portátil, APIs estandarizadas y capacidades de exportación de datos con herramientas de conversión de formatos.
 #4.13.5    Nivel: 3    Rol: V
 Verifique que la optimización de costos en entornos multicloud incluya controles de seguridad que eviten la expansión descontrolada de recursos, así como cargos no autorizados por transferencias de datos entre nubes.

---

### C4.14 Automatización de Infraestructura y Seguridad de GitOps

Asegurar las canalizaciones de automatización de infraestructura y los flujos de trabajo GitOps para la gestión de la infraestructura de IA.

 #4.14.1    Nivel: 2    Rol: D/V
 Verifique que los repositorios GitOps exijan commits firmados con claves GPG y reglas de protección de ramas que eviten empujes directos a las ramas principales.
 #4.14.2    Nivel: 2    Rol: D/V
 Verifique que la automatización de la infraestructura incluya detección de deriva con remediación automática y capacidades de reversión activadas de acuerdo con los requisitos de respuesta de la organización ante cambios no autorizados.
 #4.14.3    Nivel: 2    Rol: D/V
 Verifique que el aprovisionamiento automatizado de infraestructura incluya la validación de políticas de seguridad con bloqueo de despliegue para configuraciones no conformes.
 #4.14.4    Nivel: 2    Rol: D/V
 Verifique que los secretos de la automatización de la infraestructura se gestionen a través de operadores externos de secretos (External Secrets Operator, Bank-Vaults) con rotación automática.
 #4.14.5    Nivel: 3    Rol: V
 Verifique que la infraestructura autorreparable incluya la correlación de eventos de seguridad con respuesta automatizada ante incidentes y flujos de trabajo de notificación a las partes interesadas.

---

### Seguridad de la Infraestructura Resistente a la Computación Cuántica

Prepare la infraestructura de IA para las amenazas de la computación cuántica mediante criptografía post-cuántica y protocolos cuánticamente seguros.

 #4.15.1    Nivel: 3    Rol: D/V
 Verifique que la infraestructura de IA implemente los algoritmos criptográficos poscuánticos aprobados por NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para el intercambio de claves y firmas digitales.
 #4.15.2    Nivel: 3    Rol: D/V
 Verifique que los sistemas de distribución cuántica de claves (QKD) estén implementados para comunicaciones de IA de alta seguridad con protocolos de gestión de claves resistentes a la computación cuántica.
 #4.15.3    Nivel: 3    Rol: D/V
 Verifique que los marcos de agilidad criptográfica permitan una migración rápida hacia nuevos algoritmos postcuánticos con rotación automática de certificados y claves.
 #4.15.4    Nivel: 3    Rol: V
 Verifique que el modelado de amenazas cuánticas evalúe la vulnerabilidad de la infraestructura de IA frente a ataques cuánticos, con cronogramas de migración documentados y evaluaciones de riesgos.
 #4.15.5    Nivel: 3    Rol: D/V
 Verifique que los sistemas criptográficos híbridos clásicos-cuánticos proporcionen defensa en profundidad durante el período de transición cuántica con monitoreo del rendimiento.

---

### C4.16 Computación confidencial y enclaves seguros

Proteja las cargas de trabajo de IA y los pesos de los modelos mediante entornos de ejecución confiables basados en hardware y tecnologías de computación confidencial.

 #4.16.1    Nivel: 3    Rol: D/V
 Verifique que los modelos de IA sensibles se ejecuten dentro de enclaves Intel SGX, AMD SEV-SNP o ARM TrustZone con memoria cifrada y verificación de atestación.
 #4.16.2    Nivel: 3    Rol: D/V
 Verifique que los contenedores confidenciales (Kata Containers, gVisor con computación confidencial) aíslen las cargas de trabajo de IA mediante cifrado de memoria a nivel de hardware.
 #4.16.3    Nivel: 3    Rol: D/V
 Verifique que la atestación remota valide la integridad del enclave antes de cargar modelos de IA con una prueba criptográfica de la autenticidad de un entorno de ejecución.
 #4.16.4    Nivel: 3    Rol: D/V
 Verifique que los servicios de inferencia de IA confidenciales eviten la extracción de modelos mediante cálculo cifrado con pesos del modelo sellados y ejecución protegida.
 #4.16.5    Nivel: 3    Rol: D/V
 Verifique que la orquestación del entorno de ejecución confiable (TEE) gestione el ciclo de vida del enclave seguro con atestación remota y canales de comunicación cifrados.
 #4.16.6    Nivel: 3    Rol: D/V
 Verifique que el cómputo seguro entre múltiples partes (SMPC) permita el entrenamiento colaborativo de IA sin exponer conjuntos de datos individuales ni parámetros del modelo.

---

### C4.17 Infraestructura Zero-Knowledge

Implementar sistemas de pruebas de conocimiento cero para la verificación y autenticación de IA que preserven la privacidad sin revelar información sensible.

 #4.17.1    Nivel: 3    Rol: D/V
 Verifique que las pruebas de conocimiento cero (ZK-SNARKs, ZK-STARKs) verifiquen la integridad del modelo de IA y la trazabilidad del entrenamiento sin exponer los pesos del modelo ni los datos de entrenamiento.
 #4.17.2    Nivel: 3    Rol: D/V
 Verifique que los sistemas de autenticación basados en pruebas de conocimiento cero (ZK) permitan una verificación de usuario que preserve la privacidad para servicios de IA sin revelar información relacionada con la identidad.
 #4.17.3    Nivel: 3    Rol: D/V
 Verifique que los protocolos de intersección de conjuntos privados (PSI) permiten el emparejamiento de datos seguro para IA federada sin exponer conjuntos de datos individuales.
 #4.17.4    Nivel: 3    Rol: D/V
 Verifique que los sistemas de aprendizaje automático de conocimiento cero (ZKML) permiten inferencias de IA verificables con una prueba criptográfica de la ejecución correcta.
 #4.17.5    Nivel: 3    Rol: D/V
 Verifique que los ZK-rollups proporcionen un procesamiento de transacciones de IA escalable y que preserven la privacidad, con verificación por lotes y menor sobrecarga computacional.

---

### C4.18 Prevención de ataques por canal lateral

Proteja la infraestructura de IA de ataques de canal lateral basados en temporización, consumo de energía, electromagnetismo y caché que podrían filtrar información sensible.

 #4.18.1    Nivel: 3    Rol: D/V
 Verifique que el tiempo de inferencia de IA esté normalizado mediante algoritmos de tiempo constante y relleno para prevenir ataques de extracción de modelos basados en el tiempo.
 #4.18.2    Nivel: 3    Rol: D/V
 Verifique que la protección contra el análisis de potencia incluya la inyección de ruido, el filtrado de la línea de alimentación y patrones de ejecución aleatorizados para el hardware de IA.
 #4.18.3    Nivel: 3    Rol: D/V
 Verifique que las mitigaciones basadas en caché para canales laterales utilicen la partición de caché, la aleatorización y las instrucciones de vaciado para evitar fugas de información.
 #4.18.4    Nivel: 3    Rol: D/V
 Verifique que la protección contra emanaciones electromagnéticas incluya blindaje, filtrado de señales y procesamiento aleatorio para prevenir ataques de tipo TEMPEST.
 #4.18.5    Nivel: 3    Rol: D/V
 Verifique que las defensas contra canales laterales a nivel de microarquitectura incluyan controles de ejecución especulativa y ofuscación de patrones de acceso a la memoria.

---

### C4.19 Seguridad del hardware de IA neuromórfica y especializada

Asegurar las arquitecturas de hardware de IA emergentes, incluyendo chips neuromórficos, FPGAs, ASICs personalizados y sistemas de computación óptica.

 #4.19.1    Nivel: 3    Rol: D/V
 Verifique que la seguridad del chip neuromórfico incluya cifrado de patrones de picos, protección de pesos sinápticos y validación de reglas de aprendizaje basadas en hardware.
 #4.19.2    Nivel: 3    Rol: D/V
 Verificar que los aceleradores de IA basados en FPGA implementen cifrado del bitstream, mecanismos anti-manipulación y carga de configuración segura con actualizaciones autenticadas.
 #4.19.3    Nivel: 3    Rol: D/V
 Verifique que la seguridad de un ASIC personalizado incluya procesadores de seguridad integrados en el chip, una raíz de confianza de hardware y almacenamiento seguro de claves con detección de manipulación.
 #4.19.4    Nivel: 3    Rol: D/V
 Verifique que los sistemas de computación óptica implementen cifrado óptico a prueba de cuántica, conmutación fotónica segura y procesamiento de señales ópticas protegido.
 #4.19.5    Nivel: 3    Rol: D/V
 Verifique que los chips de IA híbridos analógico-digital incluyan cómputo analógico seguro, almacenamiento de pesos protegido y conversión analógico-digital autenticada.

---

### C4.20 Infraestructura de cómputo que preserva la privacidad

Implementar controles de infraestructura para la computación que preserva la privacidad, para proteger los datos sensibles durante el procesamiento y análisis de IA.

 #4.20.1    Nivel: 3    Rol: D/V
 Verifique que la infraestructura de cifrado homomórfico permita el cómputo cifrado en cargas de trabajo de IA sensibles, con verificación de integridad criptográfica y monitoreo del rendimiento.
 #4.20.2    Nivel: 3    Rol: D/V
 Verifique que los sistemas de recuperación de información privada permitan consultas en bases de datos sin revelar patrones de consulta, mediante la protección criptográfica de los patrones de acceso.
 #4.20.3    Nivel: 3    Rol: D/V
 Verifique que los protocolos de computación multipartita segura permiten una inferencia de IA que preserva la privacidad sin exponer entradas individuales ni cálculos intermedios.
 #4.20.4    Nivel: 3    Rol: D/V
 Verifique que la gestión de claves que preserva la privacidad incluya generación de claves distribuida, criptografía de umbral y rotación de claves segura con protección basada en hardware.
 #4.20.5    Nivel: 3    Rol: D/V
 Verifique que el rendimiento del cómputo con preservación de la privacidad esté optimizado mediante procesamiento por lotes, almacenamiento en caché y aceleración por hardware, manteniendo las garantías de seguridad criptográfica.

---

### C4.15 Marco de Agentes: Integración en la Nube, Seguridad y Despliegue Híbrido

Controles de seguridad para marcos de agentes integrados en la nube con arquitecturas híbridas locales y en la nube.

 #4.15.1    Nivel: 1    Rol: D/V
 Verifique que la integración de almacenamiento en la nube utilice cifrado de extremo a extremo con gestión de claves controlada por el agente.
 #4.15.2    Nivel: 2    Rol: D/V
 Verifique que los límites de seguridad del despliegue híbrido estén claramente definidos con canales de comunicación cifrados.
 #4.15.3    Nivel: 2    Rol: D/V
 Verifique que el acceso a los recursos en la nube incluya verificación de confianza cero con autenticación continua.
 #4.15.4    Nivel: 3    Rol: D/V
 Verifique que los requisitos de residencia de datos se cumplan mediante una atestación criptográfica de las ubicaciones de almacenamiento.
 #4.15.5    Nivel: 3    Rol: D/V
 Verifique que las evaluaciones de seguridad del proveedor de servicios en la nube incluyan modelado de amenazas específico del agente y evaluación de riesgos.

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

## C5 Control de Acceso e Identidad para Componentes de IA y Usuarios

### Objetivo de control

El control de acceso efectivo para los sistemas de IA requiere una gestión de identidades robusta, autorización basada en el contexto y una aplicación en tiempo de ejecución que siga los principios de confianza cero. Estos controles aseguran que personas, servicios y agentes autónomos solo interactúen con modelos, datos y recursos computacionales dentro de alcances explícitamente concedidos, con verificación continua y capacidades de auditoría.

---

### C5.1 Gestión de identidades y autenticación

Establezca identidades respaldadas criptográficamente para todas las entidades, con autenticación multifactor para operaciones privilegiadas.

 #5.1.1    Nivel: 1    Rol: D/V
 Verifique que todos los usuarios humanos y los principales de servicio se autentiquen a través de un proveedor de identidad empresarial centralizado (IdP) utilizando los protocolos OIDC/SAML, con mapeos únicos de identidad a token (sin cuentas ni credenciales compartidas).
 #5.1.2    Nivel: 1    Rol: D/V
 Verifique que las operaciones de alto riesgo (despliegue de modelos, exportación de pesos, acceso a datos de entrenamiento, cambios en la configuración de producción) requieran autenticación multifactor o autenticación reforzada con revalidación de sesión.
 #5.1.3    Nivel: 2    Rol: D
 Asegúrese de que los nuevos principales se sometan a una verificación de identidad que esté alineada con NIST 800-63-3 IAL-2 o estándares equivalentes antes de recibir acceso al sistema de producción.
 #5.1.4    Nivel: 2    Rol: V
 Verifique que las revisiones de acceso se realicen trimestralmente con detección automatizada de cuentas inactivas, cumplimiento de la rotación de credenciales y flujos de desprovisionamiento.
 #5.1.5    Nivel: 3    Rol: D/V
 Verifique que los agentes de IA federados se autentiquen mediante aserciones JWT firmadas que tengan una duración máxima de 24 horas y que incluyan prueba criptográfica de origen.

---

### C5.2 Autorización de recursos y el principio de mínimo privilegio

Implementa controles de acceso granulares para todos los recursos de IA, con modelos de permisos explícitos y registros de auditoría.

 #5.2.1    Nivel: 1    Rol: D/V
 Verifique que cada recurso de IA (conjuntos de datos, modelos, puntos finales, colecciones vectoriales, índices de embeddings, instancias de cómputo) aplique controles de acceso basados en roles con listas de permitidos explícitas y políticas de denegación por defecto.
 #5.2.2    Nivel: 1    Rol: D/V
 Verifique que los principios de mínimo privilegio se apliquen por defecto con cuentas de servicio que comienzan con permisos de solo-lectura y se requiera una justificación comercial documentada para el acceso de escritura.
 #5.2.3    Nivel: 1    Rol: V
 Verifique que todas las modificaciones del control de acceso estén vinculadas a solicitudes de cambio aprobadas y registradas de forma inmutable con marcas de tiempo, identidades de los actores, identificadores de recursos y deltas de permisos.
 #5.2.4    Nivel: 2    Rol: D
 Verifique que las etiquetas de clasificación de datos (PII, PHI, export-controlled, propietarias) se propaguen automáticamente a los recursos derivados (representaciones vectoriales, cachés de indicaciones, salidas del modelo) con la aplicación consistente de la política.
 #5.2.5    Nivel: 2    Rol: D/V
 Verifique que los intentos de acceso no autorizado y los eventos de escalada de privilegios activen alertas en tiempo real con metadatos contextuales a los sistemas SIEM dentro de 5 minutos.

---

### C5.3 Evaluación dinámica de políticas

Desplegar motores de control de acceso basado en atributos (ABAC) para decisiones de autorización sensibles al contexto con capacidades de auditoría.

 #5.3.1    Nivel: 1    Rol: D/V
 Verifique que las decisiones de autorización estén externalizadas a un motor de políticas dedicado (OPA, Cedar, u equivalente) accesible a través de APIs autenticadas con protección de integridad criptográfica.
 #5.3.2    Nivel: 1    Rol: D/V
 Verifique que las políticas evalúen atributos dinámicos en tiempo de ejecución, incluyendo el nivel de autorización del usuario, la clasificación de la sensibilidad del recurso, el contexto de la solicitud, el aislamiento entre inquilinos y las restricciones temporales.
 #5.3.3    Nivel: 2    Rol: D
 Verifique que las definiciones de políticas estén bajo control de versiones, sean revisadas por pares y validadas mediante pruebas automatizadas en pipelines de CI/CD antes del despliegue en producción.
 #5.3.4    Nivel: 2    Rol: V
 Verifique que los resultados de la evaluación de políticas incluyan fundamentos de decisión estructurados y se transmitan a los sistemas SIEM para análisis de correlación y reportes de cumplimiento.
 #5.3.5    Nivel: 3    Rol: D/V
 Verifique que los valores de TTL de la caché de políticas no excedan 5 minutos para recursos de alta sensibilidad y 1 hora para recursos estándar con capacidades de invalidación de caché.

---

### C5.4 Aplicación de seguridad en tiempo de consulta

Implementar controles de seguridad en la capa de base de datos con filtrado obligatorio y políticas de seguridad a nivel de fila.

 #5.4.1    Nivel: 1    Rol: D/V
 Verifique que todas las consultas de bases de datos vectoriales y consultas SQL incluyan filtros de seguridad obligatorios (ID de inquilino, etiquetas de sensibilidad, alcance del usuario) que se apliquen a nivel del motor de la base de datos, y no en el código de la aplicación.
 #5.4.2    Nivel: 1    Rol: D/V
 Verifique que las políticas de seguridad a nivel de fila (RLS) y la ocultación a nivel de campo estén habilitadas con herencia de políticas para todas las bases de datos vectoriales, índices de búsqueda y conjuntos de datos de entrenamiento.
 #5.4.3    Nivel: 2    Rol: D
 Verifique que las evaluaciones de autorización fallidas eviten los ataques del ayudante confundido al abortar de inmediato las consultas y devolver códigos de error de autorización explícitos en lugar de devolver conjuntos de resultados vacíos.
 #5.4.4    Nivel: 2    Rol: V
 Verifique que la latencia de la evaluación de políticas se supervise de forma continua con alertas automáticas para condiciones de tiempo de espera que podrían permitir eludir la autorización.
 #5.4.5    Nivel: 3    Rol: D/V
 Verifique que los mecanismos de reintento de consultas reevalúen las políticas de autorización para tener en cuenta los cambios dinámicos de permisos dentro de las sesiones de usuario activas.

---

### C5.5 Filtrado de salida y Prevención de pérdida de datos

Desplegar controles de posprocesamiento para prevenir la exposición no autorizada de datos en contenido generado por IA.

 #5.5.1    Nivel: 1    Rol: D/V
 Verifique que los mecanismos de filtrado posteriores a la inferencia escaneen y redacten PII no autorizada, información clasificada y datos propietarios antes de entregar el contenido a los solicitantes.
 #5.5.2    Nivel: 1    Rol: D/V
 Verifique que las citas, referencias y atribuciones de origen en las salidas del modelo se validen frente a los derechos del solicitante y se eliminen si se detecta acceso no autorizado.
 #5.5.3    Nivel: 2    Rol: D
 Verifique que las restricciones de formato de salida (PDFs sanitizados, imágenes sin metadatos, tipos de archivos aprobados) se apliquen de acuerdo con los niveles de permisos de usuario y las clasificaciones de datos.
 #5.5.4    Nivel: 2    Rol: V
 Verifique que los algoritmos de enmascaramiento sean deterministas, tengan control de versiones y mantengan registros de auditoría para respaldar investigaciones de cumplimiento y análisis forense.
 #5.5.5    Nivel: 3    Rol: V
 Verificar que los eventos de redacción de alto riesgo generen registros adaptativos que incluyan hashes criptográficos del contenido original para recuperación forense sin exponer los datos.

---

### C5.6 Aislamiento multitenante

Garantice el aislamiento criptográfico y lógico entre inquilinos en una infraestructura de IA compartida.

 #5.6.1    Nivel: 1    Rol: D/V
 Verifique que los espacios de memoria, los almacenes de embeddings, las entradas de caché y los archivos temporales estén segmentados por espacio de nombres para cada inquilino, con purga segura al eliminar el inquilino o al finalizar la sesión.
 #5.6.2    Nivel: 1    Rol: D/V
 Verifique que cada solicitud de API incluya un identificador de inquilino autenticado que esté validado criptográficamente frente al contexto de la sesión y a los derechos del usuario.
 #5.6.3    Nivel: 2    Rol: D
 Verifique que las políticas de red implementen reglas de denegación por defecto para la comunicación entre inquilinos dentro de las mallas de servicios y las plataformas de orquestación de contenedores.
 #5.6.4    Nivel: 3    Rol: D
 Verifique que las claves de cifrado sean únicas por inquilino, con soporte para clave gestionada por el cliente (CMK) y aislamiento criptográfico entre los almacenes de datos de los inquilinos.

---

### C5.7 Autorización de Agente Autónomo

Controlar permisos para los agentes de IA y los sistemas autónomos mediante tokens de capacidad con alcance definido y autorización continua.

 #5.7.1    Nivel: 1    Rol: D/V
 Asegúrese de que los agentes autónomos reciban tokens de capacidad acotados que enumeren explícitamente las acciones permitidas, los recursos accesibles, los límites de tiempo y las restricciones operativas.
 #5.7.2    Nivel: 1    Rol: D/V
 Verifique que las capacidades de alto riesgo (acceso al sistema de archivos, ejecución de código, llamadas a API externas, transacciones financieras) estén deshabilitadas por defecto y requieran autorizaciones explícitas para su activación con justificaciones empresariales.
 #5.7.3    Nivel: 2    Rol: D
 Verifique que los tokens de capacidad estén vinculados a las sesiones de usuario, incluyan protección de integridad criptográfica y asegúrese de que no puedan ser persistidos ni reutilizados en escenarios sin conexión.
 #5.7.4    Nivel: 2    Rol: V
 Verifique que las acciones iniciadas por un agente pasen por una autorización secundaria a través del motor de políticas ABAC con evaluación de contexto completa y registro de auditoría.
 #5.7.5    Nivel: 3    Rol: V
 Verifique que las condiciones de error del agente y el manejo de excepciones incluyan información sobre el alcance de las capacidades para apoyar el análisis de incidentes y la investigación forense.

---

### Referencias

#### Estándares y Marcos

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

## C6 Seguridad de la cadena de suministro para modelos, marcos de trabajo y datos

### Objetivo de control

Los ataques de la cadena de suministro de IA explotan modelos, marcos o conjuntos de datos de terceros para incrustar puertas traseras, sesgos o código explotable. Estos controles proporcionan trazabilidad de extremo a extremo, gestión de vulnerabilidades y monitoreo para proteger todo el ciclo de vida del modelo.

---

### C6.1 Evaluación de modelos preentrenados y su procedencia

Evaluar y autenticar los orígenes, licencias y comportamientos ocultos de los modelos de terceros antes de cualquier ajuste fino o despliegue.

 #6.1.1    Nivel: 1    Rol: D/V
 Verifique que cada artefacto de modelo de terceros incluya un registro de procedencia firmado que identifique el repositorio fuente y el hash de confirmación.
 #6.1.2    Nivel: 1    Rol: D/V
 Verifique que los modelos sean escaneados en busca de capas maliciosas o disparadores de troyanos mediante herramientas automatizadas antes de la importación.
 #6.1.3    Nivel: 2    Rol: D
 Verifique que los ajustes finos por transferencia pasen la evaluación adversarial para detectar comportamientos ocultos.
 #6.1.4    Nivel: 2    Rol: V
 Verifique que las licencias del modelo, las etiquetas de control de exportación y las declaraciones de origen de los datos se registren en una entrada de ML‑BOM.
 #6.1.5    Nivel: 3    Rol: D/V
 Verificar que los modelos de alto riesgo (pesos cargados públicamente, creadores no verificados) permanezcan en cuarentena hasta la revisión y aprobación por parte de un humano.

---

### C6.2 Escaneo de frameworks y bibliotecas

Escanear continuamente marcos y bibliotecas de ML en busca de CVEs y código malicioso para mantener segura la pila de tiempo de ejecución.

 #6.2.1    Nivel: 1    Rol: D/V
 Verifique que los pipelines de CI ejecuten escáneres de dependencias en marcos de IA y bibliotecas críticas.
 #6.2.2    Nivel: 1    Rol: D/V
 Verifique que las vulnerabilidades críticas (CVSS ≥ 7.0) bloqueen la promoción a imágenes de producción.
 #6.2.3    Nivel: 2    Rol: D
 Verifique que el análisis estático de código se ejecute en bibliotecas de ML ramificadas o vendorizadas.
 #6.2.4    Nivel: 2    Rol: V
 Verifique que las propuestas de actualización de marcos incluyan una evaluación de impacto de seguridad que haga referencia a feeds CVE públicos.
 #6.2.5    Nivel: 3    Rol: V
 Verifique que los sensores en tiempo de ejecución emitan alertas ante cargas inesperadas de bibliotecas dinámicas que se desvíen de la SBOM firmada.

---

### C6.3 Fijación de dependencias y verificación

Anclar cada dependencia a sumas de verificación inmutables y reproducir las compilaciones para garantizar artefactos idénticos y libres de manipulación.

 #6.3.1    Nivel: 1    Rol: D/V
 Verifique que todos los gestores de paquetes hagan cumplir la fijación de versiones mediante archivos de bloqueo.
 #6.3.2    Nivel: 1    Rol: D/V
 Verifique que se utilicen digests inmutables en lugar de etiquetas mutables en las referencias de contenedores.
 #6.3.3    Nivel: 2    Rol: D
 Verifique que las verificaciones de construcción reproducible comparen hashes entre ejecuciones de CI para garantizar salidas idénticas.
 #6.3.4    Nivel: 2    Rol: V
 Verifique que las atestaciones de compilación se almacenen durante 18 meses para la trazabilidad de auditoría.
 #6.3.5    Nivel: 3    Rol: D
 Verifique que las dependencias caducadas disparen PRs automatizados para actualizar o bifurcar las versiones fijadas.

---

### C6.4 Cumplimiento de Fuentes Confiables

Permitir descargas de artefactos solo desde fuentes verificadas criptográficamente-aprobadas por la organización y bloquear todo lo demás.

 #6.4.1    Nivel: 1    Rol: D/V
 Verifique que los pesos del modelo, los conjuntos de datos y los contenedores se descarguen solo desde dominios aprobados o registros internos.
 #6.4.2    Nivel: 1    Rol: D/V
 Verifique que las firmas de Sigstore/Cosign validen la identidad del publicador antes de que los artefactos se almacenen en caché localmente.
 #6.4.3    Nivel: 2    Rol: D
 Verifique que los proxies de salida bloqueen las descargas de artefactos no autenticados para hacer cumplir la política trusted‑source.
 #6.4.4    Nivel: 2    Rol: V
 Verifique que las listas de permitidos del repositorio sean revisadas trimestralmente con evidencia de justificación comercial para cada entrada.
 #6.4.5    Nivel: 3    Rol: V
 Verificar que los incumplimientos de políticas desencadenen la cuarentena de artefactos y la reversión de las ejecuciones de pipelines dependientes.

---

### C6.5 Evaluación de riesgos de un conjunto de datos de terceros

Evaluar conjuntos de datos externos para envenenamiento, sesgo y cumplimiento legal, y monitorearlos a lo largo de su ciclo de vida.

 #6.5.1    Nivel: 1    Rol: D/V
 Verifique que los conjuntos de datos externos se sometan a una puntuación de riesgo de envenenamiento (p. ej., huellas digitales de datos, detección de valores atípicos).
 #6.5.2    Nivel: 1    Rol: D
 Verifique que las métricas de sesgo (paridad demográfica, igualdad de oportunidades) se calculen antes de la aprobación del conjunto de datos.
 #6.5.3    Nivel: 2    Rol: V
 Verifique que la proveniencia y los términos de la licencia de los conjuntos de datos estén capturados en las entradas de ML‑BOM.
 #6.5.4    Nivel: 2    Rol: V
 Verificar que el monitoreo periódico detecte deriva o corrupción en conjuntos de datos alojados.
 #6.5.5    Nivel: 3    Rol: D
 Verifique que el contenido no permitido (derechos de autor, información de identificación personal) se elimine mediante depuración automatizada antes del entrenamiento.

---

### C6.6 Monitoreo de ataques a la cadena de suministro

Detectar tempranamente amenazas de la cadena de suministro mediante feeds de CVE, análisis de registros de auditoría y simulaciones de red team.

 #6.6.1    Nivel: 1    Rol: V
 Verifique que los registros de auditoría de CI/CD se transmitan a las detecciones del SIEM para descargas de paquetes anómalas o pasos de compilación manipulados.
 #6.6.2    Nivel: 2    Rol: D
 Verifique que los planes de respuesta a incidentes incluyan procedimientos de reversión para modelos o bibliotecas comprometidos.
 #6.6.3    Nivel: 3    Rol: V
 Verifique que el enriquecimiento de inteligencia de amenazas etiquete indicadores específicos de aprendizaje automático (p. ej., IoCs de envenenamiento de modelos) en el triaje de alertas.

---

### C6.7 ML‑BOM para artefactos del modelo

Genere y firme SBOMs detalladas específicas para ML (ML‑BOMs) para que los consumidores aguas abajo puedan verificar la integridad de los componentes en el momento del despliegue.

 #6.7.1    Nivel: 1    Rol: D/V
 Verifique que cada artefacto del modelo publique un ML‑BOM que liste conjuntos de datos, pesos, hiperparámetros y licencias.
 #6.7.2    Nivel: 1    Rol: D/V
 Verifique que la generación de ML‑BOM y la firma de Cosign estén automatizadas en CI y sean requeridas para la fusión.
 #6.7.3    Nivel: 2    Rol: D
 Verifique que las comprobaciones de completitud de ML‑BOM hagan que la compilación falle si falta algún metadato del componente (hash, licencia).
 #6.7.4    Nivel: 2    Rol: V
 Verifique que los consumidores aguas abajo puedan consultar ML-BOMs a través de una API para validar los modelos importados en el momento del despliegue.
 #6.7.5    Nivel: 3    Rol: V
 Verifique que los ML‑BOMs estén bajo control de versiones y se comparen para detectar modificaciones no autorizadas.

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

## C7 Comportamiento del modelo, control de salida y garantía de seguridad

### Objetivo de control

Los resultados del modelo deben estar estructurados, ser confiables, seguros, explicables y estar monitoreados de forma continua en producción. Hacerlo reduce las alucinaciones, filtraciones de privacidad, contenido dañino y acciones descontroladas, al tiempo que aumenta la confianza de los usuarios y el cumplimiento regulatorio.

---

### C7.1 Cumplimiento del Formato de Salida

Esquemas estrictos, decodificación restringida y validación posterior evitan que el contenido malformado o malintencionado se propague.

 #7.1.1    Nivel: 1    Rol: D/V
 Verifique que los esquemas de respuesta (p. ej., JSON Schema) sean proporcionados en el prompt del sistema y que cada salida se valide automáticamente; las salidas que no cumplan desencadenan reparación o rechazo.
 #7.1.2    Nivel: 1    Rol: D/V
 Verifique que la decodificación restringida (tokens de detención, expresión regular, max-tokens) esté habilitada para prevenir desbordamientos o canales laterales de inyección de indicaciones.
 #7.1.3    Nivel: 2    Rol: D/V
 Verifique que los componentes aguas abajo traten las salidas como no confiables y las validen contra esquemas o deserializadores seguros contra inyección.
 #7.1.4    Nivel: 3    Rol: V
 Verifique que los eventos de salida inapropiada estén registrados, tengan limitación de tasa y se expongan al sistema de monitorización.

---

### C7.2 Detección y Mitigación de Alucinaciones

La estimación de la incertidumbre y las estrategias de respaldo limitan las respuestas fabricadas.

 #7.2.1    Nivel: 1    Rol: D/V
 Verifique que las probabilidades logarítmicas por token, la consistencia del ensamble o los detectores de alucinaciones ajustados asignen una puntuación de confianza a cada respuesta.
 #7.2.2    Nivel: 1    Rol: D/V
 Verifique que las respuestas por debajo de un umbral de confianza configurable activen flujos de trabajo de respaldo (p. ej., generación aumentada por recuperación, modelo secundario o revisión humana).
 #7.2.3    Nivel: 2    Rol: D/V
 Verifique que los incidentes de alucinación estén etiquetados con metadatos de causa raíz y se envíen a los flujos de procesamiento de post-mortem y de ajuste fino.
 #7.2.4    Nivel: 3    Rol: D/V
 Verifique que los umbrales y los detectores se recalibren después de actualizaciones importantes del modelo o de la base de conocimientos.
 #7.2.5    Nivel: 3    Rol: V
 Verifique que las visualizaciones del tablero monitoreen las tasas de alucinación.

---

### C7.3 Filtrado de Seguridad de la Salida y Privacidad

Los filtros de políticas y la cobertura del equipo rojo protegen a los usuarios y a los datos confidenciales.

 #7.3.1    Nivel: 1    Rol: D/V
 Verifique que los clasificadores pre-generación y post-generación bloqueen contenido de odio, acoso, autolesiones, extremismo y contenido sexualmente explícito de acuerdo con la política.
 #7.3.2    Nivel: 1    Rol: D/V
 Verifique que la detección de PII/PCI y la redacción automática se ejecuten en cada respuesta; las violaciones generan un incidente de privacidad.
 #7.3.3    Nivel: 2    Rol: D
 Verifique que las etiquetas de confidencialidad (por ejemplo, secretos comerciales) se propaguen entre modalidades para evitar filtraciones en texto, imágenes o código.
 #7.3.4    Nivel: 3    Rol: D/V
 Verifique que los intentos de eludir los filtros o las clasificaciones de alto riesgo exijan aprobación secundaria o reautenticación del usuario.
 #7.3.5    Nivel: 3    Rol: D/V
 Verifique que los umbrales de filtrado reflejen las jurisdicciones legales y el contexto de edad y rol del usuario.

---

### C7.4 Limitación de salida y acción

Los límites de tasa y las puertas de aprobación previenen abusos y una autonomía excesiva.

 #7.4.1    Nivel: 1    Rol: D
 Verifique que las cuotas por usuario y por clave API limiten las solicitudes, los tokens y el costo con retroceso exponencial ante errores 429.
 #7.4.2    Nivel: 1    Rol: D/V
 Verifique que las acciones privilegiadas (escrituras de archivos, ejecución de código, llamadas de red) requieren aprobación basada en políticas o humano-en-el-bucle.
 #7.4.3    Nivel: 2    Rol: D/V
 Verifique que las comprobaciones de consistencia entre modalidades aseguren que las imágenes, el código y el texto generados para la misma solicitud no puedan utilizarse para introducir contenido malicioso.
 #7.4.4    Nivel: 2    Rol: D
 Verifique que la profundidad de delegación de agentes, los límites de recursión y las listas de herramientas permitidas estén configurados explícitamente.
 #7.4.5    Nivel: 3    Rol: V
 Verifique que la violación de los límites emita eventos de seguridad estructurados para la ingestión en SIEM.

---

### C7.5 Explicabilidad de la salida

Las señales transparentes mejoran la confianza del usuario y la depuración interna.

 #7.5.1    Nivel: 2    Rol: D/V
 Verifique que las puntuaciones de confianza visibles para el usuario o resúmenes breves de razonamiento se muestren cuando la evaluación de riesgos lo estime adecuado.
 #7.5.2    Nivel: 2    Rol: D/V
 Verifique que las explicaciones generadas eviten revelar indicaciones del sistema sensibles o datos propietarios.
 #7.5.3    Nivel: 3    Rol: D
 Verifique que el sistema capture probabilidades logarítmicas por token o mapas de atención y almacene estos datos para inspección autorizada.
 #7.5.4    Nivel: 3    Rol: V
 Verifique que los artefactos de explicabilidad estén bajo control de versiones junto con los lanzamientos de modelos para garantizar la auditabilidad.

---

### C7.6 Integración de monitoreo

La observabilidad en tiempo-real cierra el ciclo entre desarrollo y producción.

 #7.6.1    Nivel: 1    Rol: D
 Verifique que las métricas (violaciones de esquema, tasa de alucinación, toxicidad, filtraciones de PII, latencia, costo) se transmitan a una plataforma de monitoreo central.
 #7.6.2    Nivel: 1    Rol: V
 Verifique que se definan umbrales de alerta para cada métrica de seguridad, con rutas de escalamiento en guardia.
 #7.6.3    Nivel: 2    Rol: V
 Verifique que los paneles de control correlacionen las anomalías de salida con el modelo / versión, la bandera de características y los cambios en los datos de origen.
 #7.6.4    Nivel: 2    Rol: D/V
 Verifique que los datos de monitoreo retroalimenten el reentrenamiento, el ajuste fino o las actualizaciones de reglas dentro de un flujo de trabajo de MLOps documentado.
 #7.6.5    Nivel: 3    Rol: V
 Verifique que los pipelines de monitoreo cuenten con pruebas de penetración y con control de acceso para evitar la filtración de registros sensibles.

---

### 7.7 Salvaguardas de Medios Generativos

Asegúrese de que los sistemas de IA no generen contenido multimedia ilegal, dañino o no autorizado mediante la aplicación de restricciones políticas, la validación de resultados y la trazabilidad.

 #7.7.1    Nivel: 1    Rol: D/V
 Verifique que las indicaciones del sistema y las instrucciones del usuario prohíban explícitamente la generación de medios deepfake ilegales, dañinos o no consensuados (p. ej., imágenes, videos, audios).
 #7.7.2    Nivel: 2    Rol: D/V
 Verifique que las indicaciones estén filtradas para evitar intentos de generar suplantaciones de identidad, deepfakes sexualmente explícitos o medios que representen a personas reales sin su consentimiento.
 #7.7.3    Nivel: 2    Rol: V
 Verifique que el sistema utilice hashing perceptual, detección de marcas de agua o fingerprinting de contenido para prevenir la reproducción no autorizada de medios protegidos por derechos de autor.
 #7.7.4    Nivel: 3    Rol: D/V
 Verifique que todos los medios generados estén firmados criptográficamente, cuenten con marca de agua o estén incrustados con metadatos de procedencia a prueba de manipulación para la trazabilidad aguas abajo.
 #7.7.5    Nivel: 3    Rol: V
 Verifique que los intentos de eludir (p. ej., ofuscación de indicaciones, jerga, redacción adversarial) sean detectados, registrados y limitados por tasa; el abuso repetido se reporte a los sistemas de monitoreo.

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

## C8 Memory, Embeddings y Seguridad de la Base de Datos Vectorial

### Objetivo de control

Representaciones de incrustación y almacenes de vectores actúan como la "memoria en vivo" de los sistemas de IA contemporáneos, aceptando de forma continua datos proporcionados por el usuario y devolviéndolos a los contextos del modelo a través de Generación aumentada por recuperación (RAG). Si no se gobiernan, esta memoria puede filtrarse información de identificación personal (PII), violar el consentimiento o invertirse para reconstruir el texto original. El objetivo de esta familia de controles es endurecer las canalizaciones de memoria y las bases de datos de vectores para garantizar un acceso de mínimo privilegio, la preservación de la privacidad por parte de las representaciones de incrustación, la expiración o revocación bajo demanda de los vectores almacenados, y que la memoria por usuario nunca contamine las solicitudes o las completaciones de otro usuario.

---

### C8.1 Controles de acceso a índices de memoria y RAG

Implemente controles de acceso granulares en cada colección de vectores.

 #8.1.1    Nivel: 1    Rol: D/V
 Verifique que las reglas de control de acceso a nivel de fila o de espacio de nombres limiten las operaciones de inserción, eliminación y consulta por inquilino, colección o etiqueta de documento.
 #8.1.2    Nivel: 1    Rol: D/V
 Verifique que las claves API o los JWT contengan atributos con alcance (por ejemplo, identificadores de colección, verbos de acción) y que se roten al menos cada trimestre.
 #8.1.3    Nivel: 2    Rol: D/V
 Verifique que los intentos de escalamiento de privilegios (p. ej., consultas de similitud entre espacios de nombres) sean detectados y se registren en un SIEM dentro de 5 minutos.
 #8.1.4    Nivel: 2    Rol: D/V
 Verifique que los registros de auditoría de la base de datos vectorial contengan el identificador del sujeto, la operación, el vector ID/namespace, el umbral de similitud y la cantidad de resultados.
 #8.1.5    Nivel: 3    Rol: V
 Verifique que las decisiones de acceso se prueben en busca de fallos de bypass cada vez que se actualicen los motores o cambien las reglas de index-sharding.

---

### C8.2 Sanitización y Validación de Embeddings

Cribar previamente el texto para información de identificación personal (PII), redactar o seudonimizar antes de la vectorización y, opcionalmente, postprocesar los embeddings para eliminar señales residuales.

 #8.2.1    Nivel: 1    Rol: D/V
 Verifique que PII y datos regulados sean detectados mediante clasificadores automatizados y enmascarados, tokenizados o eliminados antes de la incrustación.
 #8.2.2    Nivel: 1    Rol: D
 Verificar que los pipelines de embeddings rechacen o pongan en cuarentena las entradas que contengan código ejecutable o artefactos no UTF-8 que podrían corromper el índice.
 #8.2.3    Nivel: 2    Rol: D/V
 Verifique que se aplique la sanitización con privacidad diferencial local o con privacidad diferencial métrica a los embeddings de oraciones cuya distancia a cualquier token de PII conocido caiga por debajo de un umbral configurable.
 #8.2.4    Nivel: 2    Rol: V
 Verifique que la eficacia de la sanitización (p. ej., la tasa de recall de la redacción de PII, deriva semántica) se valide al menos semestralmente frente a corpora de referencia.
 #8.2.5    Nivel: 3    Rol: D/V
 Verifique que las configuraciones de sanitización estén bajo control de versiones y que los cambios sean revisados por pares.

---

### C8.3 Expiración de la memoria, revocación y eliminación

GDPR "derecho al olvido" y leyes similares exigen un borrado oportuno; por lo tanto, los almacenes de vectores deben soportar TTL (tiempo de vida), borrados definitivos y tombstoning para que los vectores revocados no puedan ser recuperados ni reindexados.

 #8.3.1    Nivel: 1    Rol: D/V
 Verifique que cada vector y registro de metadatos lleve un TTL o una etiqueta de retención explícita, y que estos sean respetados por los trabajos de limpieza automatizados.
 #8.3.2    Nivel: 1    Rol: D/V
 Verifique que las solicitudes de eliminación iniciadas por el usuario purguen vectores, metadatos, copias en caché e índices derivados dentro de 30 días.
 #8.3.3    Nivel: 2    Rol: D
 Verifique que los borrados lógicos vayan seguidos del borrado criptográfico de los bloques de almacenamiento si el hardware lo admite, o de la destrucción de claves en Key Vault.
 #8.3.4    Nivel: 3    Rol: D/V
 Verifique que los vectores caducados estén excluidos de los resultados de la búsqueda del vecino más cercano en < 500 ms después de la expiración.

---

### C8.4 Prevención de la inversión de embeddings y fuga de datos

Defensas recientes—superposición de ruido, redes de proyección, perturbación de neuronas de privacidad y cifrado a nivel de capa de aplicación—pueden reducir las tasas de inversión a nivel de tokens por debajo de 5%.

 #8.4.1    Nivel: 1    Rol: V
 Verifique que exista un modelo de amenazas formal que cubra ataques de inversión, de pertenencia y de inferencia de atributos y que se revise anualmente.
 #8.4.2    Nivel: 2    Rol: D/V
 Verifique que el cifrado a nivel de aplicación o el cifrado buscable proteja los vectores de lecturas directas por parte de los administradores de infraestructura o del personal de la nube.
 #8.4.3    Nivel: 3    Rol: V
 Verifique que los parámetros de defensa (ε para DP, ruido σ, rango de proyección k) equilibren la privacidad ≥ 99 % para la protección de tokens y la utilidad ≤ 3 % para la pérdida de precisión.
 #8.4.4    Nivel: 3    Rol: D/V
 Asegúrese de que las métricas de resiliencia ante la inversión formen parte de las puertas de liberación para actualizaciones de modelos, con presupuestos de regresión definidos.

---

### C8.5 Aplicación del alcance para la memoria específica del usuario

La filtración entre inquilinos sigue siendo uno de los principales riesgos de RAG: consultas de similitud filtradas de forma inapropiada pueden exponer los documentos privados de otro cliente.

 #8.5.1    Nivel: 1    Rol: D/V
 Verifique que cada consulta de recuperación esté filtrada posteriormente por el ID de inquilino/usuario antes de ser enviada al prompt del LLM.
 #8.5.2    Nivel: 1    Rol: D
 Verifique que los nombres de colección o identificadores con espacio de nombres estén salteados por usuario o inquilino para que los vectores no puedan colisionar entre ámbitos.
 #8.5.3    Nivel: 2    Rol: D/V
 Verifique que los resultados de similitud por encima de un umbral de distancia configurable, pero fuera del alcance del llamante, sean descartados y se activen alertas de seguridad.
 #8.5.4    Nivel: 2    Rol: V
 Verifique que las pruebas de estrés multitenantes simulen consultas adversarias que intenten recuperar documentos fuera de alcance y demuestren que no hay filtración de datos.
 #8.5.5    Nivel: 3    Rol: D/V
 Verifique que las claves de cifrado estén segregadas por inquilino, asegurando aislamiento criptográfico incluso si el almacenamiento físico es compartido.

---

### C8.6 Seguridad avanzada del sistema de memoria

Controles de seguridad para arquitecturas de memoria sofisticadas, que incluyen memoria episódica, memoria semántica y memoria de trabajo, con requisitos específicos de aislamiento y validación.

 #8.6.1    Nivel: 1    Rol: D/V
 Verifique que los diferentes tipos de memoria (episódica, semántica y de trabajo) tengan contextos de seguridad aislados con controles de acceso basados en roles, claves de cifrado separadas y patrones de acceso documentados para cada tipo de memoria.
 #8.6.2    Nivel: 2    Rol: D/V
 Verifique que los procesos de consolidación de memoria incluyan validación de seguridad para evitar la inyección de memorias maliciosas mediante la sanitización de contenido, la verificación de origen y las comprobaciones de integridad antes del almacenamiento.
 #8.6.3    Nivel: 2    Rol: D/V
 Verifique que las consultas de recuperación de memoria sean validadas y sanitizadas para evitar la extracción de información no autorizada mediante el análisis de patrones de consulta, la implementación de controles de acceso y el filtrado de resultados.
 #8.6.4    Nivel: 3    Rol: D/V
 Verifique que los mecanismos de borrado de memoria eliminen de forma segura la información sensible, con garantías de borrado criptográfico, utilizando eliminación de claves, sobrescritura en múltiples pasadas o borrado seguro basado en hardware con certificados de verificación.
 #8.6.5    Nivel: 3    Rol: D/V
 Verifique que la integridad del sistema de memoria se supervise de forma continua para detectar modificaciones no autorizadas o corrupción, mediante sumas de verificación, registros de auditoría y alertas automatizadas cuando el contenido de la memoria cambie fuera de las operaciones normales.

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

## 9 Seguridad de la Orquestación Autónoma y de la Acción Agencial

### Objetivo de control

Asegúrese de que los sistemas de IA autónomos o multiagentes solo puedan ejecutar acciones que estén explícitamente previstas, autenticadas y que puedan ser auditadas dentro de umbrales acotados de costo y riesgo. Esto protege contra amenazas tales como compromiso del sistema autónomo, uso indebido de herramientas, detección de bucles de agentes, secuestro de las comunicaciones, suplantación de identidad, manipulación de enjambres y manipulación de la intención.

---

### 9.1 Agente Planificación de Tareas y Presupuestos de Recursión

Ralentizar planes recursivos y forzar puntos de control humanos para acciones privilegiadas.

 #9.1.1    Nivel: 1    Rol: D/V
 Verifique que la profundidad máxima de recursión, la amplitud, el tiempo de reloj real, los tokens y el costo monetario por la ejecución de un agente estén configurados centralmente y bajo control de versiones.
 #9.1.2    Nivel: 1    Rol: D/V
 Verifique que las acciones privilegiadas o irreversibles (p. ej., commits de código, transferencias financieras) requieran aprobación humana explícita a través de un canal auditable antes de la ejecución.
 #9.1.3    Nivel: 2    Rol: D
 Verifique que los monitores de recursos en tiempo real disparen la interrupción del disyuntor cuando se supere cualquier umbral presupuestario, deteniendo la expansión adicional de tareas.
 #9.1.4    Nivel: 2    Rol: D/V
 Verifique que los eventos de disyuntor se registren con la identificación del agente, la condición desencadenante y el estado del plan capturado para revisión forense.
 #9.1.5    Nivel: 3    Rol: V
 Asegúrese de que las pruebas de seguridad cubran los escenarios de agotamiento presupuestario y de plan descontrolado, y confirme una parada segura sin pérdida de datos.
 #9.1.6    Nivel: 3    Rol: D
 Verifique que las políticas de presupuesto estén expresadas como política como código y se apliquen en CI/CD para bloquear la deriva de configuración.

---

### 9.2 Aislamiento de plugins de herramientas

Aislar las interacciones con las herramientas para evitar el acceso no autorizado al sistema o la ejecución de código.

 #9.2.1    Nivel: 1    Rol: D/V
 Verifique que cada herramienta o complemento se ejecute dentro de un sandbox a nivel del sistema operativo, de un contenedor o de WASM, con políticas de privilegios mínimos para el sistema de archivos, la red y las llamadas al sistema.
 #9.2.2    Nivel: 1    Rol: D/V
 Verifique que los límites de recursos del sandbox (CPU, memoria, disco, tráfico de salida de red) y los tiempos de espera de ejecución se apliquen y se registren.
 #9.2.3    Nivel: 2    Rol: D/V
 Verifique que los binarios de la herramienta o los descriptores estén firmados digitalmente; las firmas se validan antes de cargarlos.
 #9.2.4    Nivel: 2    Rol: V
 Verifique que la telemetría del sandbox se envíe a un SIEM; las anomalías (p. ej., intentos de conexiones salientes) generan alertas.
 #9.2.5    Nivel: 3    Rol: V
 Verificar que los plugins de alto riesgo pasen revisión de seguridad y pruebas de penetración antes del despliegue en producción.
 #9.2.6    Nivel: 3    Rol: D/V
 Verifique que los intentos de escape del sandbox se bloqueen automáticamente y que el complemento infractor esté en cuarentena mientras se realiza la investigación.

---

### 9.3 Bucle Autónomo y Limitación de Costos

Detectar y detener la recursión descontrolada de agente-a-agente y las explosiones de costo.

 #9.3.1    Nivel: 1    Rol: D/V
 Verifique que las llamadas entre agentes incluyan un límite de saltos o TTL y que el tiempo de ejecución decremente y haga cumplir ese límite.
 #9.3.2    Nivel: 2    Rol: D
 Verifique que los agentes mantengan un identificador único del grafo de invocación para detectar autoinvocación o patrones cíclicos.
 #9.3.3    Nivel: 2    Rol: D/V
 Verifique que los contadores acumulativos de unidades de cómputo y gasto se rastrean por cadena de solicitudes; al exceder el límite, se aborta la cadena.
 #9.3.4    Nivel: 3    Rol: V
 Verifique que el análisis formal o la verificación de modelos demuestre la ausencia de recursión no acotada en los protocolos de agentes.
 #9.3.5    Nivel: 3    Rol: D
 Verifique que los eventos de interrupción de bucle generen alertas y alimenten métricas de mejora continua.

---

### 9.4 Protección contra el uso indebido a nivel de protocolo

Canales de comunicación seguros entre agentes y sistemas externos para prevenir el secuestro o la manipulación.

 #9.4.1    Nivel: 1    Rol: D/V
 Verifique que todos los mensajes de agente a herramienta y de agente a agente estén autenticados (p. ej., TLS mutuo o JWT) y cifrados de extremo a extremo.
 #9.4.2    Nivel: 1    Rol: D
 Verifique que los esquemas se validen de forma estricta; los campos desconocidos o los mensajes malformados sean rechazados.
 #9.4.3    Nivel: 2    Rol: D/V
 Verifique que las comprobaciones de integridad (MACs o firmas digitales) cubran toda la carga útil del mensaje, incluidos los parámetros de la herramienta.
 #9.4.4    Nivel: 2    Rol: D
 Verifique que la protección contra ataques de repetición (nonces o ventanas de marca de tiempo) se aplique a nivel de la capa de protocolo.
 #9.4.5    Nivel: 3    Rol: V
 Verifique que las implementaciones de protocolo se sometan a fuzzing y análisis estático para detectar fallas de inyección o deserialización.

---

### 9.5 Identidad del Agente y Evidencia de Manipulación

Asegúrese de que las acciones sean atribuibles y las modificaciones sean detectables.

 #9.5.1    Nivel: 1    Rol: D/V
 Verifique que cada instancia de agente posea una identidad criptográfica única (par de claves o credencial basada en hardware).
 #9.5.2    Nivel: 2    Rol: D/V
 Verifique que todas las acciones de los agentes estén firmadas y con marca de tiempo; los registros incluyan la firma para la no repudiación.
 #9.5.3    Nivel: 2    Rol: V
 Verifique que los registros a prueba de manipulaciones se almacenen en un medio de solo escritura (append-only) o de escritura única (write-once).
 #9.5.4    Nivel: 3    Rol: D
 Verificar que las claves de identidad roten de acuerdo con un calendario definido y ante indicadores de compromiso.
 #9.5.5    Nivel: 3    Rol: D/V
 Verifique que los intentos de suplantación o conflicto de claves desencadenen la cuarentena inmediata del agente afectado.

---

### 9.6 Reducción de riesgos del enjambre multi-agente

Mitigar los peligros de comportamiento-colectivo mediante el aislamiento y el modelado formal de la seguridad.

 #9.6.1    Nivel: 1    Rol: D/V
 Verifique que los agentes que operan en diferentes dominios de seguridad se ejecuten en sandboxes de tiempo de ejecución aislados o en segmentos de red.
 #9.6.2    Nivel: 3    Rol: V
 Verifique que los comportamientos de enjambre estén modelados y verificados formalmente para la vivacidad y la seguridad antes del despliegue.
 #9.6.3    Nivel: 3    Rol: D
 Verifique que los monitores en tiempo de ejecución detecten patrones inseguros emergentes (p. ej., oscilaciones e interbloqueos) e inicien una acción correctiva.

---

### 9.7 Autenticación de Usuario y Herramienta / Autorización

Implementa controles de acceso robustos para cada acción desencadenada por el agente.

 #9.7.1    Nivel: 1    Rol: D/V
 Verifique que los agentes se autentiquen como principales de primera clase ante sistemas aguas abajo, sin volver a usar credenciales del usuario final.
 #9.7.2    Nivel: 2    Rol: D
 Verifique que las políticas de autorización granular limiten qué herramientas puede invocar un agente y qué parámetros puede suministrar.
 #9.7.3    Nivel: 2    Rol: V
 Verifique que las verificaciones de privilegios se vuelvan a evaluar en cada llamada (autorización continua), no solo al inicio de la sesión.
 #9.7.4    Nivel: 3    Rol: D
 Verifique que los privilegios delegados expiren automáticamente y requieran volver a obtener el consentimiento tras un tiempo de espera o un cambio en el alcance.

---

### 9.8 Seguridad de la Comunicación entre Agentes

Cifrar y proteger la integridad de todos los mensajes entre agentes para contrarrestar la interceptación y la manipulación.

 #9.8.1    Nivel: 1    Rol: D/V
 Verifique que la autenticación mutua y el cifrado con secreto perfecto hacia adelante (p. ej. TLS 1.3) sean obligatorios para los canales del agente.
 #9.8.2    Nivel: 1    Rol: D
 Verifique que la integridad del mensaje y su origen se validen antes de procesarlo; si falla, se generan alertas y se descarta el mensaje.
 #9.8.3    Nivel: 2    Rol: D/V
 Verifique que los metadatos de la comunicación (sellos de tiempo, números de secuencia) se registren para facilitar la reconstrucción forense.
 #9.8.4    Nivel: 3    Rol: V
 Verifique que la verificación formal o la comprobación de modelos confirme que las máquinas de estados del protocolo no pueden llegar a estados inseguros.

---

### 9.9 Verificación de intenciones y aplicación de restricciones

Verifique que las acciones del agente se alineen con la intención declarada por el usuario y con las restricciones del sistema.

 #9.9.1    Nivel: 1    Rol: D
 Verifique que los solucionadores de restricciones previas a la ejecución verifiquen las acciones propuestas frente a las reglas de seguridad y a las políticas codificadas en el código.
 #9.9.2    Nivel: 2    Rol: D/V
 Verifique que las acciones de alto impacto (financieras, destructivas, sensibles a la privacidad) requieren confirmación explícita de la intención por parte del usuario que inicia.
 #9.9.3    Nivel: 2    Rol: V
 Asegúrese de que las comprobaciones de post-condición verifiquen que las acciones completadas alcanzaron los efectos previstos sin efectos secundarios; las discrepancias desencadenan la reversión.
 #9.9.4    Nivel: 3    Rol: V
 Verifique que los métodos formales (p. ej., verificación de modelos, demostración de teoremas) o las pruebas basadas en propiedades demuestren que los planes del agente cumplen todas las restricciones declaradas.
 #9.9.5    Nivel: 3    Rol: D
 Verifique que los incidentes de desajuste-de-intención o violación-de-restricciones alimenten ciclos-de-mejora-continua y intercambio-de-inteligencia-de-amenazas.

---

### 9.10 Agente Razonamiento Estrategia Seguridad

Selección y ejecución seguras de diferentes estrategias de razonamiento, incluyendo ReAct, Chain-of-Thought y Tree-of-Thoughts.

 #9.10.1    Nivel: 1    Rol: D/V
 Verifique que la selección de la estrategia de razonamiento utilice criterios determinísticos (complejidad de la entrada, tipo de tarea, contexto de seguridad) y que entradas idénticas produzcan selecciones de estrategia idénticas dentro del mismo contexto de seguridad.
 #9.10.2    Nivel: 1    Rol: D/V
 Verifique que cada estrategia de razonamiento (ReAct, Cadena de pensamiento, Árbol de pensamientos) tenga validación de entrada dedicada, sanitización de salida y límites de tiempo de ejecución específicos a su enfoque cognitivo.
 #9.10.3    Nivel: 2    Rol: D/V
 Verifique que las transiciones de la estrategia de razonamiento se registren con el contexto completo, incluyendo las características de entrada, los valores de los criterios de selección y los metadatos de ejecución para la reconstrucción del rastro de auditoría.
 #9.10.4    Nivel: 2    Rol: D/V
 Verifique que el razonamiento Tree-of-Thoughts incluya mecanismos de poda de ramas que terminen la exploración cuando se detecten violaciones de políticas, límites de recursos o límites de seguridad.
 #9.10.5    Nivel: 2    Rol: D/V
 Verifique que los ciclos de ReAct (Reason-Act-Observe) incluyan puntos de control de validación en cada fase: verificación de pasos de razonamiento, autorización de acciones y sanitización de observaciones antes de proceder.
 #9.10.6    Nivel: 3    Rol: D/V
 Verifique que las métricas de rendimiento de la estrategia de razonamiento (tiempo de ejecución, uso de recursos, calidad de la salida) sean monitoreadas con alertas automatizadas cuando las métricas se desvíen más allá de los umbrales configurados.
 #9.10.7    Nivel: 3    Rol: D/V
 Verifique que los enfoques de razonamiento híbrido que combinan múltiples estrategias mantengan la validación de entradas y las restricciones de salida de todas las estrategias constituyentes, sin eludir ningún control de seguridad.
 #9.10.8    Nivel: 3    Rol: D/V
 Verifique que las pruebas de seguridad de la estrategia de razonamiento incluyan fuzzing con entradas malformadas, indicaciones adversarias diseñadas para forzar el cambio de estrategia y pruebas de condiciones límite para cada enfoque cognitivo.

---

### 9.11 Gestión del estado del ciclo de vida del agente y seguridad

Inicialización segura del agente, transiciones de estado y terminación con trazas de auditoría criptográficas y procedimientos de recuperación definidos.

 #9.11.1    Nivel: 1    Rol: D/V
 Verifique que la inicialización del agente incluya el establecimiento de identidad criptográfica con credenciales respaldadas por hardware y registros de auditoría de inicio inmutables que contengan el ID del agente, la marca de tiempo, el hash de configuración y los parámetros de inicialización.
 #9.11.2    Nivel: 2    Rol: D/V
 Verifique que las transiciones de estado del agente estén firmadas criptográficamente, tengan marca de tiempo y se registren con un contexto completo que incluya los eventos desencadenantes, el hash del estado anterior, el hash del nuevo estado y las validaciones de seguridad realizadas.
 #9.11.3    Nivel: 2    Rol: D/V
 Verifique que los procedimientos de apagado del agente incluyan el borrado seguro de la memoria mediante borrado criptográfico o sobreescritura en varias pasadas, la revocación de credenciales con notificación a la autoridad de certificación y la generación de certificados de terminación a prueba de manipulación.
 #9.11.4    Nivel: 3    Rol: D/V
 Verifique que los mecanismos de recuperación de agentes validen la integridad del estado utilizando sumas de verificación criptográficas (SHA-256 como mínimo) y reviertan a estados previamente verificados como válidos cuando se detecte corrupción, con alertas automatizadas y requisitos de aprobación manual.
 #9.11.5    Nivel: 3    Rol: D/V
 Verifique que los mecanismos de persistencia de los agentes cifren los datos de estado sensibles con claves AES-256 por agente y que implementen una rotación de claves segura en intervalos configurables (máximo 90 días) con despliegue sin tiempo de inactividad.

---

### 9.12 Marco de Seguridad de la Integración de Herramientas

Controles de seguridad para la carga dinámica de herramientas, la ejecución y la validación de resultados, con procesos de evaluación de riesgos y aprobación definidos.

 #9.12.1    Nivel: 1    Rol: D/V
 Verifique que los descriptores de herramientas incluyan metadatos de seguridad que especifiquen privilegios requeridos (lectura/escritura/ejecución), niveles de riesgo (bajo/medio/alto), límites de recursos (CPU, memoria, red) y requisitos de validación documentados en los manifiestos de herramientas.
 #9.12.2    Nivel: 1    Rol: D/V
 Verifique que los resultados de la ejecución de la herramienta se validen frente a los esquemas esperados (Esquema JSON, Esquema XML) y a las políticas de seguridad (sanitización de la salida, clasificación de datos) antes de la integración con límites de tiempo y procedimientos de manejo de errores.
 #9.12.3    Nivel: 2    Rol: D/V
 Verifique que los registros de interacción de herramientas incluyan un contexto de seguridad detallado, incluyendo el uso de privilegios, patrones de acceso a datos, tiempo de ejecución, consumo de recursos y códigos de retorno, con registro estructurado para la integración con SIEM.
 #9.12.4    Nivel: 2    Rol: D/V
 Verificar que los mecanismos de carga dinámica de herramientas validen firmas digitales utilizando una infraestructura PKI e implementar protocolos de carga seguros con aislamiento de sandbox y verificación de permisos antes de la ejecución.
 #9.12.5    Nivel: 3    Rol: D/V
 Verifique que las evaluaciones de seguridad de la herramienta se activen automáticamente para nuevas versiones con puertas de aprobación obligatorias, que incluyen análisis estático, pruebas dinámicas y revisión del equipo de seguridad, con criterios de aprobación documentados y requisitos de SLA.

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

## 10 Robustez ante ataques adversariales y defensa de la privacidad

### Objetivo de control

Asegúrese de que los modelos de IA permanezcan fiables, preserven la privacidad y sean resistentes al abuso cuando se enfrenten a ataques de evasión, inferencia, extracción o envenenamiento.

---

### 10.1 Alineación del modelo y seguridad

Prevenga salidas dañinas o que infrinjan políticas.

 #10.1.1    Nivel: 1    Rol: D/V
 Verifique que una suite de pruebas de alineación (prompts red-team, sondas de jailbreak, contenido prohibido) esté versionada y se ejecute en cada lanzamiento del modelo.
 #10.1.2    Nivel: 1    Rol: D
 Verifique que se apliquen las salvaguardas de rechazo y de finalización segura.
 #10.1.3    Nivel: 2    Rol: D/V
 Verifique que un evaluador automatizado mida la tasa de contenido dañino y marque las regresiones que superen un umbral establecido.
 #10.1.4    Nivel: 2    Rol: D
 Verifique que el entrenamiento de contrajailbreak esté documentado y sea reproducible.
 #10.1.5    Nivel: 3    Rol: V
 Verifique que las pruebas formales de cumplimiento de políticas o la monitorización certificada cubran dominios críticos.

---

### 10.2 Adversarial-Example Fortalecimiento frente a ejemplos adversariales

Aumentar la resiliencia frente a entradas manipuladas. El entrenamiento adversarial robusto y la puntuación en benchmarks son la mejor práctica actual.

 #10.2.1    Nivel: 1    Rol: D
 Verifique que los repositorios de los proyectos incluyan configuraciones de entrenamiento adversarial con semillas reproducibles.
 #10.2.2    Nivel: 2    Rol: D/V
 Verifique que la detección de ejemplos adversariales genera alertas de bloqueo en los pipelines de producción.
 #10.2.4    Nivel: 3    Rol: V
 Verifique que las pruebas de robustez certificada o certificados de límites basados en intervalos cubran al menos las clases críticas principales.
 #10.2.5    Nivel: 3    Rol: V
 Verifique que las pruebas de regresión empleen ataques adaptativos para confirmar que no hay pérdida de robustez medible.

---

### 10.3 Mitigación de la inferencia de membresía

Limite la capacidad de decidir si un registro formaba parte de los datos de entrenamiento. La privacidad diferencial y el enmascaramiento de puntuaciones de confianza siguen siendo las defensas conocidas más eficaces.

 #10.3.1    Nivel: 1    Rol: D
 Verifique que la regularización de la entropía por consulta o el escalado por temperatura reduzcan las predicciones excesivamente confiadas.
 #10.3.2    Nivel: 2    Rol: D
 Verifique que el entrenamiento emplee optimización con privacidad diferencial acotada por ε para conjuntos de datos sensibles.
 #10.3.3    Nivel: 2    Rol: V
 Verifique que las simulaciones de ataque (shadow-model o black-box) muestren la AUC de ataque ≤ 0.60 en datos de prueba no vistos.

---

### 10.4 Resistencia a la inversión de modelos

Prevenir la reconstrucción de atributos privados. Las revisiones recientes destacan el truncamiento de la salida y las garantías de privacidad diferencial como defensas prácticas.

 #10.4.1    Nivel: 1    Rol: D
 Verifique que los atributos sensibles nunca se muestren directamente; cuando sea necesario, use intervalos o transformaciones unidireccionales.
 #10.4.2    Nivel: 1    Rol: D/V
 Verifique que los límites de tasa de consultas limiten las consultas adaptativas repetidas del mismo sujeto.
 #10.4.3    Nivel: 2    Rol: D
 Verifique que el modelo esté entrenado con ruido que preserva la privacidad.

---

### 10.5 Defensa contra la extracción de modelos

Detectar y disuadir la clonación no autorizada. Se recomienda el uso de marcas de agua y el análisis de patrones de consultas.

 #10.5.1    Nivel: 1    Rol: D
 Verifique que las pasarelas de inferencia apliquen límites de tasa globales y por clave API, ajustados al umbral de memorización del modelo.
 #10.5.2    Nivel: 2    Rol: D/V
 Verifique que la entropía de consulta y la pluralidad de entradas alimenten un detector de extracción automatizado.
 #10.5.3    Nivel: 2    Rol: V
 Verifique que las marcas de agua frágiles o probabilísticas puedan demostrarse con p < 0.01 en ≤ 1 000 consultas contra un clon sospechado.
 #10.5.4    Nivel: 3    Rol: D
 Verifique que las claves de marca de agua y los conjuntos de disparadores se almacenen en un módulo de seguridad de hardware y se roten anualmente.
 #10.5.5    Nivel: 3    Rol: V
 Verifique que los eventos de alerta de extracción incluyan consultas ofensivas y estén integrados con planes de respuesta ante incidentes.

---

### 10.6 Detección-de-datos-envenenados-en-tiempo-de-inferencia

Identificar y neutralizar entradas con puerta trasera o envenenadas.

 #10.6.1    Nivel: 1    Rol: D
 Verifique que las entradas pasen por un detector de anomalías (p. ej., STRIP, puntuación de consistencia) antes de la inferencia del modelo.
 #10.6.2    Nivel: 1    Rol: V
 Verifique que los umbrales del detector estén ajustados en conjuntos de validación limpios y envenenados para lograr menos del 5% de falsos positivos.
 #10.6.3    Nivel: 2    Rol: D
 Verifique que las entradas marcadas como envenenadas activen el bloqueo suave y los flujos de trabajo de revisión humana.
 #10.6.4    Nivel: 2    Rol: V
 Verifique que los detectores sean sometidos a pruebas de estrés con ataques de puerta trasera adaptativos sin disparador.
 #10.6.5    Nivel: 3    Rol: D
 Verifique que las métricas de eficacia de detección se registren y se reevaluen periódicamente con inteligencia de amenazas actualizada.

---

### 10.7 Adaptación dinámica de la política de seguridad

Actualizaciones de políticas de seguridad en tiempo real basadas en inteligencia de amenazas y análisis conductual.

 #10.7.1    Nivel: 1    Rol: D/V
 Verifique que las políticas de seguridad puedan actualizarse dinámicamente sin reiniciar el agente, manteniendo la integridad de la versión de la política.
 #10.7.2    Nivel: 2    Rol: D/V
 Verifique que las actualizaciones de la política estén firmadas criptográficamente por personal de seguridad autorizado y sean validadas antes de su aplicación.
 #10.7.3    Nivel: 2    Rol: D/V
 Verifique que los cambios dinámicos de políticas se registren con registros de auditoría completos que incluyan la justificación, las cadenas de aprobación y los procedimientos de reversión.
 #10.7.4    Nivel: 3    Rol: D/V
 Verifique que los mecanismos de seguridad adaptativos ajusten la sensibilidad de la detección de amenazas según el contexto de riesgo y los patrones de comportamiento.
 #10.7.5    Nivel: 3    Rol: D/V
 Verifique que las decisiones de adaptación de políticas sean explicables e incluyan rastros de evidencia para la revisión por parte del equipo de seguridad.

---

### 10.8 Análisis de seguridad basado en reflexión

Validación de seguridad mediante la autorreflexión del agente y el análisis metacognitivo.

 #10.8.1    Nivel: 1    Rol: D/V
 Verifique que los mecanismos de reflexión de los agentes incluyan una autoevaluación centrada en la seguridad de las decisiones y acciones.
 #10.8.2    Nivel: 2    Rol: D/V
 Verifique que las salidas de reflexión estén validadas para evitar la manipulación de los mecanismos de autoevaluación por entradas adversarias.
 #10.8.3    Nivel: 2    Rol: D/V
 Verifique que el análisis de seguridad metacognitiva identifique sesgos potenciales, manipulaciones o compromisos en los procesos de razonamiento de los agentes.
 #10.8.4    Nivel: 3    Rol: D/V
 Verifique que las advertencias de seguridad basadas en reflexión activen un monitoreo mejorado y posibles flujos de trabajo de intervención humana.
 #10.8.5    Nivel: 3    Rol: D/V
 Verificar que el aprendizaje continuo a partir de la retroalimentación de seguridad mejore la detección de amenazas sin deteriorar la funcionalidad legítima.

---

### 10.9 Evolución y Seguridad de la Auto-mejora

Controles de seguridad para sistemas basados en agentes capaces de auto-modificación y evolución.

 #10.9.1    Nivel: 1    Rol: D/V
 Verifique que las capacidades de auto-modificación estén restringidas a las áreas seguras designadas con límites de verificación formal.
 #10.9.2    Nivel: 2    Rol: D/V
 Asegúrese de que las propuestas de evolución pasen por una evaluación de impacto de seguridad antes de su implementación.
 #10.9.3    Nivel: 2    Rol: D/V
 Verifique que los mecanismos de auto-mejoramiento incluyan capacidades de reversión con verificación de integridad.
 #10.9.4    Nivel: 3    Rol: D/V
 Verifique que la seguridad del metaaprendizaje impida la manipulación adversaria de los algoritmos de mejora.
 #10.9.5    Nivel: 3    Rol: D/V
 Verifique que el auto-mejoramiento recursivo esté limitado por restricciones de seguridad formales con pruebas matemáticas de convergencia.

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

## 11 Protección de la Privacidad y Gestión de Datos Personales

### Objetivo de control

Mantener garantías de privacidad rigurosas a lo largo de todo el ciclo de vida de la IA—recopilación, entrenamiento, inferencia y respuesta a incidentes—para que los datos personales solo se procesen con consentimiento claro, alcance mínimo necesario, borrado verificable y garantías formales de privacidad.

---

### 11.1 Anonimización & Minimización de Datos

 #11.1.1    Nivel: 1    Rol: D/V
 Verifique que se eliminen los identificadores directos y cuasi-identificadores, y que se calcule un hash.
 #11.1.2    Nivel: 2    Rol: D/V
 Verifique que las auditorías automatizadas midan k-anonimato/l-diversidad y alerten cuando los umbrales caigan por debajo de la política.
 #11.1.3    Nivel: 2    Rol: V
 Verifique que los informes de importancia de las características del modelo demuestren que no exista filtración de identificadores por encima de ε = 0.01 de información mutua.
 #11.1.4    Nivel: 3    Rol: V
 Verifique que las pruebas formales o la certificación de datos sintéticos muestren un riesgo de reidentificación ≤ 0.05, incluso ante ataques de vinculación.

---

### 11.2 Derecho al olvido y cumplimiento de la eliminación

 #11.2.1    Nivel: 1    Rol: D/V
 Verifique que las solicitudes de eliminación de datos de los sujetos se propaguen a conjuntos de datos sin procesar, puntos de control, vectores de embedding, registros y copias de seguridad dentro de los acuerdos de nivel de servicio de menos de 30 días.
 #11.2.2    Nivel: 2    Rol: D
 Verifique que las rutinas de "desaprendizaje automático" reentrenen físicamente o aproximen la eliminación utilizando algoritmos de desaprendizaje certificados.
 #11.2.3    Nivel: 2    Rol: V
 Verifique que la evaluación del modelo sombra demuestre que los registros olvidados influyen en menos del 1% de las salidas tras el desaprendizaje.
 #11.2.4    Nivel: 3    Rol: V
 Verifique que los eventos de eliminación se registren de forma inmutable y sean auditable por los reguladores.

---

### 11.3 Salvaguardas de la Privacidad-Diferencial

 #11.3.1    Nivel: 2    Rol: D/V
 Verifique que los paneles de contabilidad de la pérdida de privacidad alerten cuando la ε acumulada supere los umbrales de la política.
 #11.3.2    Nivel: 2    Rol: V
 Verifique que las auditorías de privacidad de caja negra estimen ε̂ dentro del 10% del valor declarado.
 #11.3.3    Nivel: 3    Rol: V
 Verifique que las pruebas formales cubran todos los ajustes finos y las incrustaciones posteriores al entrenamiento.

---

### 11.4 Propósito-Limitación y Protección contra el Crecimiento del Alcance

 #11.4.1    Nivel: 1    Rol: D
 Verifique que cada conjunto de datos y cada punto de control del modelo lleven una etiqueta de propósito legible por máquina alineada con el consentimiento original.
 #11.4.2    Nivel: 1    Rol: D/V
 Verifique que los monitores en tiempo de ejecución detecten consultas inconsistentes con el propósito declarado y activen un rechazo suave.
 #11.4.3    Nivel: 3    Rol: D
 Verifique que las compuertas de policy-as-code bloqueen la redeploy de modelos a nuevos dominios sin revisión DPIA.
 #11.4.4    Nivel: 3    Rol: V
 Verifique que las pruebas formales de trazabilidad muestren que cada ciclo de vida de los datos personales permanece dentro del alcance consentido.

---

### 11.5 Gestión del consentimiento y seguimiento de la base legal

 #11.5.1    Nivel: 1    Rol: D/V
 Verifique que una Plataforma de Gestión de Consentimiento (CMP) registre el estado de consentimiento, la finalidad y el período de retención por sujeto de datos.
 #11.5.2    Nivel: 2    Rol: D
 Verifique que las APIs expongan tokens de consentimiento; los modelos deben validar el alcance del token antes de la inferencia.
 #11.5.3    Nivel: 2    Rol: D/V
 Verifique que el consentimiento denegado o retirado detenga los flujos de procesamiento dentro de 24 horas.

---

### 11.6 Aprendizaje Federado con Controles de Privacidad

 #11.6.1    Nivel: 1    Rol: D
 Verifique que las actualizaciones de los clientes empleen la adición de ruido de privacidad diferencial local antes de la agregación.
 #11.6.2    Nivel: 2    Rol: D/V
 Verificar que las métricas de entrenamiento sean privadas diferencialmente y nunca revelen la pérdida de un solo cliente.
 #11.6.3    Nivel: 2    Rol: V
 Verifique que la agregación resistente al envenenamiento (por ejemplo, Krum/Trimmed-Mean) esté habilitada.
 #11.6.4    Nivel: 3    Rol: V
 Verifique que las pruebas formales demuestren que el presupuesto global de ε tenga una pérdida de utilidad menor a 5.

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

### Objetivo de control

Esta sección proporciona los requisitos para ofrecer visibilidad en tiempo real y forense de lo que el modelo y otros componentes de IA ven, hacen y devuelven, de modo que las amenazas puedan ser detectadas, priorizadas y de las que se pueda aprender.

### C12.1 Registro de Solicitudes y Respuestas

 #12.1.1    Nivel: 1    Rol: D/V
 Verifique que todas las solicitudes del usuario y las respuestas del modelo se registren con metadatos apropiados (p. ej., marca de tiempo, ID de usuario, ID de sesión, versión del modelo).
 #12.1.2    Nivel: 1    Rol: D/V
 Verifique que los registros se almacenen en repositorios seguros y con control de acceso, con políticas de retención adecuadas y procedimientos de respaldo.
 #12.1.3    Nivel: 1    Rol: D/V
 Verifique que los sistemas de almacenamiento de registros implementen cifrado en reposo y en tránsito para proteger la información sensible contenida en los registros.
 #12.1.4    Nivel: 1    Rol: D/V
 Verifique que los datos sensibles en las indicaciones y en las salidas se enmascaren o se redacten automáticamente antes del registro, con reglas de enmascaramiento configurables para PII (información de identificación personal), credenciales e información propietaria.
 #12.1.5    Nivel: 2    Rol: D/V
 Verifique que las decisiones de política y las acciones de filtrado de seguridad se registren con suficiente detalle para permitir la auditoría y la depuración de los sistemas de moderación de contenido.
 #12.1.6    Nivel: 2    Rol: D/V
 Verifique que la integridad de los registros esté protegida, por ejemplo, mediante firmas criptográficas o almacenamiento de solo escritura.

---

### C12.2 Detección de abuso y alertas

 #12.2.1    Nivel: 1    Rol: D/V
 Verifique que el sistema detecte y alerte sobre patrones conocidos de jailbreak, intentos de inyección de indicaciones y entradas adversarias utilizando detección basada en firmas.
 #12.2.2    Nivel: 1    Rol: D/V
 Verifique que el sistema se integre con las plataformas existentes de Security Information and Event Management (SIEM) utilizando formatos de registro y protocolos estándar.
 #12.2.3    Nivel: 2    Rol: D/V
 Verifique que los eventos de seguridad enriquecidos incluyan contexto específico de IA, como identificadores de modelo, puntuaciones de confianza y decisiones del filtro de seguridad.
 #12.2.4    Nivel: 2    Rol: D/V
 Verifique que la detección de anomalías conductuales identifique patrones de conversación inusuales, intentos de reintento excesivos o comportamientos de sondeo sistemáticos.
 #12.2.5    Nivel: 2    Rol: D/V
 Verifique que los mecanismos de alerta en tiempo-real notifiquen a los equipos de seguridad cuando se detecten posibles violaciones de políticas o intentos de ataque.
 #12.2.6    Nivel: 2    Rol: D/V
 Verifique que se hayan incluido reglas personalizadas para detectar patrones de amenaza específicos de IA, incluyendo intentos coordinados de jailbreak, campañas de inyección de prompts y ataques de extracción de modelos.
 #12.2.7    Nivel: 3    Rol: D/V
 Verifique que los flujos de trabajo automatizados de respuesta a incidentes puedan aislar modelos comprometidos, bloquear usuarios malintencionados y escalar eventos de seguridad críticos.

---

### C12.3 Detección de deriva del modelo

 #12.3.1    Nivel: 1    Rol: D/V
 Verificar que el sistema realiza un seguimiento de métricas de rendimiento básicas, como precisión, puntuaciones de confianza, latencia y tasas de error, a lo largo de las versiones del modelo y de los períodos.
 #12.3.2    Nivel: 2    Rol: D/V
 Verifique que las alertas automatizadas se activen cuando las métricas de rendimiento superen los umbrales de degradación predefinidos o se desvíen significativamente de las líneas base.
 #12.3.3    Nivel: 2    Rol: D/V
 Verifique que los monitores de detección de alucinaciones identifiquen y señalen casos en los que las salidas del modelo contengan información factualmente incorrecta, inconsistente o fabricada.

---

### C12.4 Telemetría de Rendimiento y Comportamiento

 #12.4.1    Nivel: 1    Rol: D/V
 Verifique que las métricas operativas, entre ellas la latencia de las solicitudes, el consumo de tokens, el uso de memoria y el rendimiento, se recolecten y supervisen de forma continua.
 #12.4.2    Nivel: 1    Rol: D/V
 Verifique que las tasas de éxito y de fallo se registren con la categorización de tipos de errores y sus causas raíz.
 #12.4.3    Nivel: 2    Rol: D/V
 Verifique que la supervisión del uso de recursos incluya el uso de GPU/CPU, consumo de memoria y requisitos de almacenamiento, con alertas cuando se superen los umbrales.

---

### C12.5 Planificación y Ejecución de la Respuesta a Incidentes de IA

 #12.5.1    Nivel: 1    Rol: D/V
 Verifique que los planes de respuesta ante incidentes aborden específicamente los eventos de seguridad relacionados con IA, incluidos el compromiso del modelo, el envenenamiento de datos y los ataques adversariales.
 #12.5.2    Nivel: 2    Rol: D/V
 Asegúrese de que los equipos de respuesta a incidentes tengan acceso a herramientas forenses específicas de IA y a la experiencia necesaria para investigar el comportamiento de los modelos y los vectores de ataque.
 #12.5.3    Nivel: 3    Rol: D/V
 Verifique que el análisis posterior al incidente incluya consideraciones de reentrenamiento del modelo, actualizaciones de filtros de seguridad y la integración de las lecciones aprendidas en los controles de seguridad.

---

### C12.5 Detección de la degradación del rendimiento de la IA

Monitorear y detectar la degradación del rendimiento y de la calidad de los modelos de IA a lo largo del tiempo.

 #12.5.1    Nivel: 1    Rol: D/V
 Verifique que la exactitud del modelo, la precisión, la sensibilidad y las puntuaciones F1 se supervisen continuamente y se comparen con umbrales de referencia.
 #12.5.2    Nivel: 1    Rol: D/V
 Verifique que la detección de deriva de datos monitoree los cambios en la distribución de entrada que puedan afectar el rendimiento del modelo.
 #12.5.3    Nivel: 2    Rol: D/V
 Verifique que la detección de deriva de concepto identifique cambios en la relación entre las entradas y las salidas esperadas.
 #12.5.4    Nivel: 2    Rol: D/V
 Asegúrese de que la degradación del rendimiento active alertas automáticas e inicie flujos de trabajo de reentrenamiento o reemplazo del modelo.
 #12.5.5    Nivel: 3    Rol: V
 Verifique que el análisis de la causa raíz de la degradación correlacione las caídas de rendimiento con cambios en los datos, problemas de infraestructura o factores externos.

---

### C12.6 Visualización de DAG y Seguridad del Flujo de Trabajo

Proteja los sistemas de visualización de flujos de trabajo contra la filtración de información y ataques de manipulación.

 #12.6.1    Nivel: 1    Rol: D/V
 Verifique que los datos de visualización de DAG estén sanitizados para eliminar información sensible antes del almacenamiento o la transmisión.
 #12.6.2    Nivel: 1    Rol: D/V
 Verifique que los controles de acceso de la visualización de flujos de trabajo aseguren que solo los usuarios autorizados puedan ver las rutas de decisión del agente y las trazas de razonamiento.
 #12.6.3    Nivel: 2    Rol: D/V
 Verifique que la integridad de los datos del DAG esté protegida mediante firmas criptográficas y mecanismos de almacenamiento a prueba de manipulación.
 #12.6.4    Nivel: 2    Rol: D/V
 Asegúrese de que los sistemas de visualización de flujos de trabajo implementen la validación de entradas para prevenir ataques de inyección a través de datos de nodos o aristas diseñados.
 #12.6.5    Nivel: 3    Rol: D/V
 Verifique que las actualizaciones en tiempo real del DAG estén limitadas por tasa y validadas para prevenir ataques de denegación de servicio en sistemas de visualización.

---

### C12.7 Monitoreo proactivo del comportamiento de seguridad

Detección y prevención de amenazas de seguridad mediante el análisis proactivo del comportamiento de los agentes.

 #12.7.1    Nivel: 1    Rol: D/V
 Verifique que los comportamientos de los agentes proactivos estén validados en términos de seguridad antes de la ejecución con la integración de la evaluación de riesgos.
 #12.7.2    Nivel: 2    Rol: D/V
 Verifique que los disparadores de iniciativas autónomas incluyan la evaluación del contexto de seguridad y la evaluación del panorama de amenazas.
 #12.7.3    Nivel: 2    Rol: D/V
 Verifique que los patrones de comportamiento proactivo se analicen en busca de posibles implicaciones de seguridad y consecuencias no deseadas.
 #12.7.4    Nivel: 3    Rol: D/V
 Verifique que las acciones proactivas críticas para la seguridad requieran cadenas de aprobación explícitas con registros de auditoría.
 #12.7.5    Nivel: 3    Rol: D/V
 Verifique que la detección de anomalías conductuales identifique desviaciones en los patrones de agentes proactivos que podrían indicar compromiso.

---

### Referencias

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Supervisión humana, rendición de cuentas y gobernanza

### Objetivo de control

Este capítulo proporciona requisitos para mantener la supervisión humana y cadenas de rendición de cuentas claras en los sistemas de IA, asegurando explicabilidad, transparencia y una gestión ética a lo largo del ciclo de vida de la IA.

---

### C13.1 Kill-Switch & Mecanismos de Anulación

Proporcionar rutas de apagado o reversión cuando se observe un comportamiento inseguro del sistema de IA.

 #13.1.1    Nivel: 1    Rol: D/V
 Verifique que exista un interruptor de parada manual para detener de inmediato la inferencia del modelo de IA y sus salidas.
 #13.1.2    Nivel: 1    Rol: D
 Verifique que los controles de anulación sean accesibles solo para el personal autorizado.
 #13.1.3    Nivel: 3    Rol: D/V
 Verifique que los procedimientos de reversión puedan volver a versiones anteriores del modelo o a operaciones en modo seguro.
 #13.1.4    Nivel: 3    Rol: V
 Verifique que los mecanismos de anulación se prueben regularmente.

---

### C13.2 Puntos de control de decisiones con intervención humana

Exigir aprobaciones humanas cuando los montos en juego superen umbrales de riesgo predefinidos.

 #13.2.1    Nivel: 1    Rol: D/V
 Verifique que las decisiones de IA de alto riesgo requieran la aprobación explícita de un humano antes de su ejecución.
 #13.2.2    Nivel: 1    Rol: D
 Verifique que los umbrales de riesgo estén claramente definidos y que se activen automáticamente los flujos de trabajo de revisión humana.
 #13.2.3    Nivel: 2    Rol: D
 Verifique que las decisiones sensibles al tiempo cuenten con procedimientos de contingencia cuando no se pueda obtener la aprobación humana dentro de los plazos requeridos.
 #13.2.4    Nivel: 3    Rol: D/V
 Verifique que los procedimientos de escalamiento definan niveles de autoridad claros para diferentes tipos de decisiones o categorías de riesgo, si aplica.

---

### C13.3 Cadena de Responsabilidad y Auditabilidad

Registrar las acciones del operador y las decisiones del modelo.

 #13.3.1    Nivel: 1    Rol: D/V
 Verifique que todas las decisiones del sistema de IA y las intervenciones humanas queden registradas con marcas de tiempo, identidades de usuario y la justificación de la decisión.
 #13.3.2    Nivel: 2    Rol: D
 Verifique que los registros de auditoría no puedan ser manipulados y que se incluyan mecanismos de verificación de integridad.

---

### C13.4 Técnicas de IA explicable

Importancia de características superficiales, contrafactuales y explicaciones locales.

 #13.4.1    Nivel: 1    Rol: D/V
 Verifique que los sistemas de IA proporcionen explicaciones básicas de sus decisiones en un formato legible por humanos.
 #13.4.2    Nivel: 2    Rol: V
 Verifique que la calidad de las explicaciones esté validada mediante estudios de evaluación humana y métricas.
 #13.4.3    Nivel: 3    Rol: D/V
 Verifique que las puntuaciones de importancia de características o los métodos de atribución (SHAP, LIME, etc.) estén disponibles para decisiones críticas.
 #13.4.4    Nivel: 3    Rol: V
 Verifique que las explicaciones contrafactuales muestren cómo podrían modificarse las entradas para cambiar los resultados, si es aplicable al caso de uso y al dominio.

---

### C13.5 Tarjetas de Modelo y Divulgaciones de Uso

Mantenga las tarjetas de modelo para el uso previsto, métricas de rendimiento y consideraciones éticas.

 #13.5.1    Nivel: 1    Rol: D
 Verifique que las tarjetas de modelo documenten los casos de uso previstos, las limitaciones y los modos de fallo conocidos.
 #13.5.2    Nivel: 1    Rol: D/V
 Verifique que se divulguen las métricas de rendimiento para los distintos casos de uso aplicables.
 #13.5.3    Nivel: 2    Rol: D
 Verifique que las consideraciones éticas, las evaluaciones de sesgos, las evaluaciones de equidad, las características de los datos de entrenamiento y las limitaciones conocidas de los datos de entrenamiento estén documentadas y actualizadas regularmente.
 #13.5.4    Nivel: 2    Rol: D/V
 Verifique que las tarjetas de modelo estén bajo control de versiones y se mantengan a lo largo del ciclo de vida del modelo con seguimiento de cambios.

---

### C13.6 Cuantificación de la incertidumbre

Propague puntuaciones de confianza o medidas de entropía en las respuestas.

 #13.6.1    Nivel: 1    Rol: D
 Verifique que los sistemas de IA proporcionen puntuaciones de confianza o medidas de incertidumbre junto con sus salidas.
 #13.6.2    Nivel: 2    Rol: D/V
 Verifique que los umbrales de incertidumbre activen una revisión humana adicional o rutas de decisión alternativas.
 #13.6.3    Nivel: 2    Rol: V
 Verifique que los métodos de cuantificación de la incertidumbre estén calibrados y validados con respecto a datos de referencia.
 #13.6.4    Nivel: 3    Rol: D/V
 Verifique que la propagación de la incertidumbre se mantenga a través de flujos de trabajo de IA de múltiples pasos.

---

### C13.7 Informes de Transparencia para el Usuario

Proporcionar informes periódicos sobre incidentes, deriva de datos y uso de datos.

 #13.7.1    Nivel: 1    Rol: D/V
 Verifique que las políticas de uso de datos y las prácticas de gestión del consentimiento del usuario se comuniquen claramente a las partes interesadas.
 #13.7.2    Nivel: 2    Rol: D/V
 Verifique que se realicen evaluaciones de impacto de IA y que los resultados estén incluidos en los informes.
 #13.7.3    Nivel: 2    Rol: D/V
 Verifique que los informes de transparencia publicados regularmente divulguen incidentes de IA y métricas operativas con un nivel razonable de detalle.

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

This glosario exhaustivo proporciona definiciones de términos clave de IA, ML y seguridad utilizados a lo largo del AISVS para garantizar claridad y comprensión común.

Ejemplo adversarial: Una entrada deliberadamente diseñada para hacer que un modelo de IA cometa un error, a menudo mediante la adición de perturbaciones sutiles imperceptibles para los humanos.
​
Robustez adversarial – La robustez en IA se refiere a la capacidad de un modelo para mantener su rendimiento y resistir ser engañado o manipulado por entradas intencionadamente elaboradas y maliciosas diseñadas para provocar errores.
​
Agente – Los agentes de IA son sistemas de software que utilizan IA para perseguir objetivos y completar tareas en nombre de los usuarios. Muestran razonamiento, planificación y memoria, y tienen un nivel de autonomía para tomar decisiones, aprender y adaptarse.
​
IA con agencia: sistemas de IA que pueden operar con cierto grado de autonomía para lograr objetivos, a menudo tomando decisiones y llevando a cabo acciones sin intervención humana directa.
​
Control de Acceso Basado en Atributos (ABAC): Un paradigma de control de acceso en el que las decisiones de autorización se basan en atributos del usuario, del recurso, de la acción y del entorno, evaluadas en el momento de la consulta.
​
Ataque de puerta trasera: un tipo de ataque de envenenamiento de datos en el que el modelo se entrena para responder de forma específica a ciertos desencadenantes, mientras que se comporta normalmente en otros casos.
​
Sesgo: Errores sistemáticos en las salidas de modelos de IA que pueden conducir a resultados injustos o discriminatorios para ciertos grupos o en contextos específicos.
​
Explotación de sesgos: Una técnica de ataque que aprovecha sesgos conocidos en modelos de IA para manipular salidas o resultados.
​
Cedar: el lenguaje de políticas y el motor de Amazon para permisos de granularidad fina utilizados en la implementación de ABAC para sistemas de IA.
​
Cadena de razonamiento: una técnica para mejorar el razonamiento en modelos de lenguaje mediante la generación de pasos de razonamiento intermedios antes de producir una respuesta final.
​
Disyuntores: Mecanismos que detienen automáticamente las operaciones del sistema de IA cuando se superan umbrales de riesgo específicos.
​
Filtración de datos: exposición no intencionada de información sensible a través de las salidas o el comportamiento de un modelo de IA.
​
Envenenamiento de datos: La corrupción deliberada de los datos de entrenamiento para comprometer la integridad del modelo, a menudo para instalar puertas traseras o degradar el rendimiento.
​
Privacidad diferencial – La privacidad diferencial es un marco matemáticamente riguroso para divulgar información estadística sobre conjuntos de datos, al tiempo que protege la privacidad de los sujetos de datos individuales. Permite al titular de datos compartir patrones agregados del grupo, mientras limita la información que se filtre sobre individuos específicos.
​
Embeddings: Representaciones vectoriales densas de datos (texto, imágenes, etc.) que capturan el significado semántico en un espacio de alta dimensionalidad.
​
Explicabilidad – La explicabilidad en IA es la capacidad de un sistema de IA para proporcionar razones comprensibles para sus decisiones y predicciones, ofreciendo vislumbres de su funcionamiento interno.
​
IA Explicable (XAI): Sistemas de IA diseñados para proporcionar explicaciones comprensibles para los humanos de sus decisiones y comportamientos a través de diversas técnicas y marcos.
​
Aprendizaje Federado: Un enfoque de aprendizaje automático en el que los modelos se entrenan en múltiples dispositivos descentralizados que albergan muestras de datos locales, sin intercambiar los datos en sí.
​
Barreras: Restricciones implementadas para evitar que los sistemas de IA produzcan salidas dañinas, sesgadas o, por lo demás, indeseables.
​
Alucinación – Una alucinación de IA se refiere a un fenómeno en el que un modelo de IA genera información incorrecta o engañosa que no se basa en sus datos de entrenamiento ni en la realidad fáctica.
​
Intervención humana en el bucle (HITL): Sistemas diseñados para exigir supervisión humana, verificación o intervención humana en puntos de decisión críticos.
​
Infraestructura como código (IaC): Gestión y aprovisionamiento de la infraestructura mediante código en lugar de procesos manuales, lo que permite el escaneo de seguridad y despliegues consistentes.
​
Jailbreak: Técnicas utilizadas para eludir las salvaguardas de seguridad en sistemas de IA, especialmente en los grandes modelos de lenguaje, para generar contenido prohibido.
​
Principio de mínimo privilegio: el principio de seguridad que consiste en otorgar solo los derechos de acceso mínimos necesarios para los usuarios y los procesos.
​
LIME (Local Interpretable Model-agnostic Explanations): una técnica para explicar las predicciones de cualquier clasificador de aprendizaje automático, aproximándolo localmente con un modelo interpretable.
​
Ataque de inferencia de membresía: Un ataque cuyo objetivo es determinar si un punto de datos específico se utilizó para entrenar un modelo de aprendizaje automático.
​
MITRE ATLAS: Panorama de amenazas adversarias para sistemas de inteligencia artificial; una base de conocimientos sobre tácticas y técnicas adversarias contra sistemas de IA.
​
Tarjeta de modelo – Una tarjeta de modelo es un documento que proporciona información estandarizada sobre el rendimiento de un modelo de IA, sus limitaciones, usos previstos y consideraciones éticas para promover la transparencia y el desarrollo responsable de la IA.
​
Extracción de modelo: Un ataque en el que un adversario consulta repetidamente un modelo objetivo para crear una copia funcionalmente similar sin autorización.
​
Inversión de modelos: Un ataque que intenta reconstruir los datos de entrenamiento analizando las salidas del modelo.
​
Gestión del ciclo de vida del modelo – La gestión del ciclo de vida de la IA es el proceso de supervisar todas las etapas de la existencia de un modelo de IA, incluido su diseño, desarrollo, despliegue, monitoreo, mantenimiento y eventual retiro, para garantizar que siga siendo eficaz y esté alineado con los objetivos.
​
Envenenamiento de modelos: Introducir vulnerabilidades o puertas traseras directamente en un modelo durante el proceso de entrenamiento.
​
Robo/Extracción de modelos: Extraer una copia o una aproximación de un modelo propietario mediante consultas repetidas.
​
Sistema multiagente: Un sistema compuesto por múltiples agentes de IA que interactúan entre sí, cada uno con capacidades y objetivos potencialmente diferentes.
​
OPA (Open Policy Agent): Un motor de políticas de código abierto que permite la aplicación unificada de políticas en toda la pila.
​
Aprendizaje automático con privacidad (PPML): Técnicas y métodos para entrenar y desplegar modelos de ML mientras se protege la privacidad de los datos de entrenamiento.
​
Inyección de prompt: un ataque en el que instrucciones maliciosas se insertan en las entradas para anular el comportamiento previsto del modelo.
​
RAG (Generación Aumentada por Recuperación): Una técnica que mejora los modelos de lenguaje a gran escala al recuperar información relevante de fuentes de conocimiento externas antes de generar una respuesta.
​
Red-Teaming: la práctica de probar activamente sistemas de IA simulando ataques adversarios para identificar vulnerabilidades.
​
SBOM (Lista de Materiales de Software): Un registro formal que contiene los detalles y las relaciones de la cadena de suministro de varios componentes utilizados para construir software o modelos de IA.
​
SHAP (SHapley Additive exPlanations): Un enfoque teórico de juego para explicar la salida de cualquier modelo de aprendizaje automático al calcular la contribución de cada característica a la predicción.
​
Ataque a la cadena de suministro: Comprometer un sistema apuntando a elementos menos seguros de su cadena de suministro, como bibliotecas de terceros, conjuntos de datos o modelos preentrenados.
​
Aprendizaje por transferencia: Una técnica en la que un modelo desarrollado para una tarea se reutiliza como punto de partida para un modelo en una segunda tarea.
​
Base de datos de vectores: una base de datos especializada diseñada para almacenar vectores de alta dimensionalidad (embeddings) y realizar búsquedas de similitud eficientes.
​
Escaneo de vulnerabilidades: herramientas automatizadas que identifican vulnerabilidades de seguridad conocidas en componentes de software, incluyendo marcos de IA y dependencias.
​
Marcado de agua digital: Técnicas para incrustar marcadores imperceptibles en contenido generado por IA para rastrear su origen o detectar la generación por IA.
​
Vulnerabilidad de día cero: una vulnerabilidad previamente desconocida que los atacantes pueden explotar antes de que los desarrolladores creen e implementen un parche.

## Apéndice B: Referencias

### TODO

## Apéndice C: Gobernanza de Seguridad de IA y Documentación

### Objetivo

Este apéndice proporciona los requisitos fundamentales para establecer estructuras organizativas, políticas y procesos para gobernar la seguridad de la IA a lo largo del ciclo de vida del sistema.

---

### AC.1 Adopción del Marco de Gestión de Riesgos de IA

Proporcionar un marco formal para identificar, evaluar y mitigar los riesgos específicos de la IA a lo largo del ciclo de vida del sistema.

 #AC.1.1    Nivel: 1    Rol: D/V
 Verifique que una metodología de evaluación de riesgos específica para IA esté documentada e implementada.
 #AC.1.2    Nivel: 2    Rol: D
 Verifique que se realicen evaluaciones de riesgos en puntos clave del ciclo de vida de la IA y antes de cambios significativos.
 #AC.1.3    Nivel: 3    Rol: D/V
 Verifique que el marco de gestión de riesgos se alinee con estándares establecidos (p. ej., NIST AI RMF).

---

### AC.2 Política y Procedimientos de Seguridad de IA

Definir y hacer cumplir normas organizativas para el desarrollo, la implementación y la operación seguras de IA.

 #AC.2.1    Nivel: 1    Rol: D/V
 Verifique que existan políticas de seguridad de IA documentadas.
 #AC.2.2    Nivel: 2    Rol: D
 Verifique que las políticas sean revisadas y actualizadas al menos una vez al año y después de cambios significativos en el panorama de amenazas.
 #AC.2.3    Nivel: 3    Rol: D/V
 Verifique que las políticas cubran todas las categorías AISVS y los requisitos regulatorios aplicables.

---

### AC.3 Roles y Responsabilidades para la Seguridad de la IA

Establecer una rendición de cuentas clara para la seguridad de la IA en toda la organización.

 #AC.3.1    Nivel: 1    Rol: D/V
 Verifique que los roles y responsabilidades de la seguridad de la IA estén documentados.
 #AC.3.2    Nivel: 2    Rol: D
 Verifique que las personas responsables posean la competencia adecuada en seguridad.
 #AC.3.3    Nivel: 3    Rol: D/V
 Verifique que se haya establecido un comité de ética de la IA o un consejo de gobernanza para sistemas de IA de alto riesgo.

---

### AC.4 Aplicación de las Directrices Éticas de la IA

Asegúrese de que los sistemas de IA operen de acuerdo con principios éticos establecidos.

 #AC.4.1    Nivel: 1    Rol: D/V
 Verifique que existan directrices éticas para el desarrollo y el despliegue de la IA.
 #AC.4.2    Nivel: 2    Rol: D
 Verifique que existan mecanismos para detectar e informar violaciones éticas.
 #AC.4.3    Nivel: 3    Rol: D/V
 Verifique que se realicen revisiones éticas regulares de los sistemas de IA desplegados.

---

### AC.5 Monitoreo del cumplimiento regulatorio de IA

Mantenerse al tanto de las regulaciones de IA en evolución y cumplirlas.

 #AC.5.1    Nivel: 1    Rol: D/V
 Verifique que existan procesos para identificar las regulaciones de IA aplicables.
 #AC.5.2    Nivel: 2    Rol: D
 Verifique que se evalúe el cumplimiento de todos los requisitos regulatorios.
 #AC.5.3    Nivel: 3    Rol: D/V
 Verificar que los cambios regulatorios disparen revisiones oportunas y actualizaciones de los sistemas de IA.

### AC.6 Gobernanza de datos de entrenamiento, documentación y proceso

 #1.1.2    Nivel: 1    Rol: D/V
 Verifique que solo se permitan conjuntos de datos que hayan sido verificados por su calidad, representatividad, procedencia ética y cumplimiento de licencias, reduciendo así los riesgos de envenenamiento, sesgo incrustado y infracción de la propiedad intelectual.
 #1.1.5    Nivel: 2    Rol: D/V
 Verifique que la calidad de la etiquetación/anotación esté asegurada mediante revisiones cruzadas entre revisores o mediante consenso.
 #1.1.6    Nivel: 2    Rol: D/V
 Verifique que se mantengan las "tarjetas de datos" o las "hojas de datos para conjuntos de datos" para conjuntos de datos de entrenamiento significativos, detallando sus características, motivaciones, composición, procesos de recopilación, preprocesamiento y usos recomendados/desaconsejados.
 #1.3.2    Nivel: 2    Rol: D/V
 Verifique que los sesgos identificados sean mitigados mediante estrategias documentadas, como reequilibrio, aumento de datos focalizado, ajustes algorítmicos (p. ej., técnicas de preprocesamiento, procesamiento durante el entrenamiento, postprocesamiento) o ponderación, y que se evalúe el impacto de la mitigación tanto en la equidad como en el rendimiento general del modelo.
 #1.3.3    Nivel: 2    Rol: D/V
 Verificar que se evalúen y documenten las métricas de equidad posteriores al entrenamiento.
 #1.3.4    Nivel: 3    Rol: D/V
 Verifique que una política de gestión de sesgos del ciclo de vida asigne propietarios y cadencia de revisión.
 #1.4.1    Nivel: 2    Rol: D/V
 Garantizar la calidad del etiquetado/anotación mediante directrices claras, verificaciones cruzadas entre revisores, mecanismos de consenso (p. ej., monitoreo del acuerdo entre anotadores) y procesos definidos para resolver discrepancias.
 #1.4.4    Nivel: 3    Rol: D/V
 Verifique que las etiquetas críticas para la seguridad, la protección o la equidad (p. ej., identificar contenido tóxico, hallazgos médicos críticos) reciban una revisión dual independiente obligatoria u otra verificación robusta equivalente.
 #1.4.6    Nivel: 2    Rol: D/V
 Verifique que las guías de etiquetado y las instrucciones sean exhaustivas, estén bajo control de versiones y sean revisadas por pares.
 #1.4.6    Nivel: 2    Rol: D/V
 Verifique que los esquemas de datos para las etiquetas estén claramente definidos y con control de versiones.
 #1.3.1    Nivel: 1    Rol: D/V
 Verifique que los conjuntos de datos sean evaluados para detectar desequilibrio representacional y sesgos potenciales en atributos protegidos legalmente (por ejemplo, raza, género, edad) y otras características éticamente sensibles relevantes para el dominio de aplicación del modelo (por ejemplo, estatus socioeconómico, ubicación).
 #1.5.3    Nivel: 2    Rol: V
 Verifique que las revisiones manuales puntuales realizadas por expertos en el dominio cubran una muestra estadísticamente significativa (p. ej., ≥1% o 1,000 muestras, lo que sea mayor, o según lo determine la evaluación de riesgos) para identificar problemas de calidad sutiles que no sean detectados por la automatización.
 #1.8.4    Nivel: 2    Rol: D/V
 Verifique que los flujos de etiquetado externalizados o basados en crowdsourcing incluyan salvaguardas técnicas y procedimentales para garantizar la confidencialidad e integridad de los datos, la calidad de las etiquetas y prevenir la filtración de datos.
 #1.5.4    Nivel: 2    Rol: D/V
 Verifique que los pasos de remediación se añadan a los registros de procedencia.
 #1.6.2    Nivel: 2    Rol: D/V
 Verifique que las muestras marcadas desencadenen una revisión manual antes del entrenamiento.
 #1.6.3    Nivel: 2    Rol: V
 Verifique que los resultados alimenten el expediente de seguridad del modelo e informen la inteligencia de amenazas en curso.
 #1.6.4    Nivel: 3    Rol: D/V
 Verifique que la lógica de detección se haya actualizado con la nueva inteligencia de amenazas.
 #1.6.5    Nivel: 3    Rol: D/V
 Verifique que los pipelines de aprendizaje en línea monitoreen la deriva de la distribución.
 #1.7.1    Nivel: 1    Rol: D/V
 Verificar que los flujos de eliminación de datos de entrenamiento eliminen los datos primarios y derivados y evalúen el impacto en el modelo, y que el impacto en los modelos afectados sea evaluado y, si es necesario, abordado (p. ej., mediante reentrenamiento o recalibración).
 #1.7.2    Nivel: 2    Rol: D
 Verifique que existan mecanismos para rastrear y respetar el alcance y estado del consentimiento del usuario (y de las retiradas) para los datos utilizados en el entrenamiento, y que el consentimiento se valide antes de que los datos se incorporen a nuevos procesos de entrenamiento o actualizaciones significativas del modelo.
 #1.7.3    Nivel: 2    Rol: V
 Verifique que los flujos de trabajo se prueben anualmente y se registren.
 #1.8.1    Nivel: 2    Rol: D/V
 Verifique que los proveedores de datos de terceros, incluidos los proveedores de modelos preentrenados y conjuntos de datos externos, se sometan a debida diligencia en seguridad, privacidad, abastecimiento ético y calidad de los datos antes de que sus datos o modelos se integren.
 #1.8.2    Nivel: 1    Rol: D
 Verifique que las transferencias externas utilicen TLS/autenticación y comprobaciones de integridad.
 #1.8.3    Nivel: 2    Rol: D/V
 Verifique que las fuentes de datos de alto-riesgo (p. ej., conjuntos de datos de código abierto con procedencia desconocida, proveedores no verificados) reciban un escrutinio reforzado, como análisis en sandbox, verificaciones exhaustivas de calidad y sesgos, y detección específica de envenenamiento, antes de su uso en aplicaciones sensibles.
 #1.8.4    Nivel: 3    Rol: D/V
 Verifique que los modelos preentrenados obtenidos de terceros sean evaluados en busca de sesgos incrustados, posibles puertas traseras, la integridad de su arquitectura y la procedencia de sus datos de entrenamiento originales, antes de realizar un ajuste fino o desplegarlos.
 #1.5.3    Nivel: 2    Rol: D/V
 Verifique que, en caso de que se utilice el entrenamiento adversarial, la generación, gestión y versionado de los conjuntos de datos adversariales estén documentados y controlados.
 #1.5.3    Nivel: 3    Rol: D/V
 Verifique que el impacto del entrenamiento de robustez adversarial en el rendimiento del modelo (frente a entradas limpias y adversarias) y en las métricas de equidad sea evaluado, documentado y monitoreado.
 #1.5.4    Nivel: 3    Rol: D/V
 Verificar que las estrategias de entrenamiento adversarial y de robustez se revisen y actualicen periódicamente para contrarrestar las técnicas de ataque adversariales en evolución.
 #1.4.2    Nivel: 2    Rol: D/V
 Verifique que los conjuntos de datos fallidos estén aislados con registros de auditoría.
 #1.4.3    Nivel: 2    Rol: D/V
 Verifique que las puertas de calidad bloqueen conjuntos de datos de baja calidad a menos que se aprueben excepciones.
 #1.11.2    Nivel: 2    Rol: D/V
 Verifique que el proceso de generación, los parámetros y el uso previsto de los datos sintéticos estén documentados.
 #1.11.3    Nivel: 2    Rol: D/V
 Verifique que los datos sintéticos sean evaluados en cuanto a sesgo, filtración de privacidad y problemas de representatividad antes de usarlos en el entrenamiento.
 #1.12.3    Nivel: 2    Rol: D/V
 Verifique que se generen alertas para eventos de acceso sospechosos y que se investiguen con prontitud.
 #1.13.1    Nivel: 1    Rol: D/V
 Verifique que se definan períodos de retención explícitos para todos los conjuntos de datos de entrenamiento.
 #1.13.2    Nivel: 2    Rol: D/V
 Verifique que los conjuntos de datos caduquen, se eliminen automáticamente o sean revisados para su eliminación al final de su ciclo de vida.
 #1.13.3    Nivel: 2    Rol: D/V
 Verifique que las acciones de retención y eliminación estén registradas y sean auditables.
 #1.14.1    Nivel: 2    Rol: D/V
 Verifique que se identifiquen y apliquen los requisitos de residencia de datos y de transferencias transfronterizas para todos los conjuntos de datos.
 #1.14.2    Nivel: 2    Rol: D/V
 Verifique que las regulaciones sectoriales (p. ej., atención médica, finanzas) se identifiquen y se aborden en el manejo de datos.
 #1.14.3    Nivel: 2    Rol: D/V
 Verifique que el cumplimiento de las leyes de privacidad relevantes (p. ej., GDPR, CCPA) esté documentado y se revise regularmente.
 #1.16.1    Nivel: 2    Rol: D/V
 Verifique que existan mecanismos para responder a las solicitudes de los interesados de acceso, rectificación, limitación u oposición.
 #1.16.2    Nivel: 2    Rol: D/V
 Verifique que las solicitudes se registren, se rastreen y se cumplan dentro de los plazos legalmente establecidos.
 #1.16.3    Nivel: 2    Rol: D/V
 Verifique que los procesos para ejercer los derechos de los interesados sean probados y revisados regularmente para garantizar su eficacia.
 #1.17.1    Nivel: 2    Rol: D/V
 Verifique que se realice un análisis de impacto antes de actualizar o reemplazar una versión del conjunto de datos, que abarque el rendimiento del modelo, la equidad y el cumplimiento.
 #1.17.2    Nivel: 2    Rol: D/V
 Verifique que los resultados del análisis de impacto estén documentados y sean revisados por las partes interesadas relevantes.
 #1.17.3    Nivel: 2    Rol: D/V
 Verifique que existan planes de reversión en caso de que las nuevas versiones introduzcan riesgos inaceptables o regresiones.
 #1.18.1    Nivel: 2    Rol: D/V
 Verifique que todo el personal involucrado en la anotación de datos cuente con verificación de antecedentes y esté capacitado en seguridad y privacidad de datos.
 #1.18.2    Nivel: 2    Rol: D/V
 Verifique que todo el personal de anotación haya firmado acuerdos de confidencialidad y de no divulgación.
 #1.18.3    Nivel: 2    Rol: D/V
 Verifique que las plataformas de anotación de datos hagan cumplir los controles de acceso y monitoreen las amenazas internas.

#### Referencias

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Apéndice D: Gobernanza y verificación de codificación segura asistida por IA

### Objetivo

Este capítulo define controles organizacionales básicos para el uso seguro y eficaz de herramientas de codificación asistidas por IA durante el desarrollo de software, asegurando la seguridad y la trazabilidad a lo largo del SDLC.

---

### AD.1 Flujo de Codificación-Segura Asistido por IA

Integre herramientas de IA en el ciclo de vida de desarrollo de software seguro de la organización (SSDLC) sin debilitar los puntos de control de seguridad existentes.

 #AD.1.1    Nivel: 1    Rol: D/V
 Asegúrese de que un flujo de trabajo documentado describa cuándo y cómo las herramientas de IA pueden generar, refactorizar o revisar código.
 #AD.1.2    Nivel: 2    Rol: D
 Verifique que el flujo de trabajo se mapee a cada fase del SSDLC (diseño, implementación, revisión de código, pruebas, despliegue).
 #AD.1.3    Nivel: 3    Rol: D/V
 Verifique que las métricas (p. ej., densidad de vulnerabilidades, tiempo medio de detección) se recolecten en código generado por IA y se comparen con bases de referencia exclusivas de humanos.

---

### AD.2 Calificación de herramientas de IA y modelado de amenazas

Asegúrese de que las herramientas de codificación de IA sean evaluadas en cuanto a capacidades de seguridad, riesgos y al impacto de la cadena‑de‑suministro antes de adoptarlas.

 #AD.2.1    Nivel: 1    Rol: D/V
 Verifique que un modelo de amenazas para cada herramienta de IA identifique uso indebido, inversión de modelo, filtración de datos y riesgos de la cadena de dependencias.
 #AD.2.2    Nivel: 2    Rol: D
 Asegúrese de que las evaluaciones de herramientas incluyan análisis estático/dinámico de cualquier componente local y evaluación de los endpoints de SaaS (TLS, autenticación/autorización, registro).
 #AD.2.3    Nivel: 3    Rol: D/V
 Verifique que las evaluaciones sigan un marco reconocido y se vuelvan a realizar después de cambios de versión mayor.

---

### AD.3 Gestión Segura de Prompts y Contexto

Prevenir la filtración de secretos, código propietario y datos personales al construir indicaciones o contextos para modelos de IA.

 #AD.3.1    Nivel: 1    Rol: D/V
 Verifique que las directrices escritas prohíban enviar secretos, credenciales o datos clasificados en las indicaciones.
 #AD.3.2    Nivel: 2    Rol: D
 Verifique que los controles técnicos (ocultación del lado del cliente, filtros de contexto aprobados) eliminen automáticamente artefactos sensibles.
 #AD.3.3    Nivel: 3    Rol: D/V
 Verifique que las indicaciones y las respuestas estén tokenizadas, cifradas en tránsito y en reposo, y que los períodos de retención cumplan con la política de clasificación de datos.

---

### AD.4 Validación del código generado por IA

Detecta y corrige las vulnerabilidades introducidas por la salida de la IA antes de que el código se despliegue.

 #AD.4.1    Nivel: 1    Rol: D/V
 Verifique que el código IA‑generado siempre esté sujeto a revisión humana.
 #AD.4.2    Nivel: 2    Rol: D
 Verifique que los escáneres automatizados (SAST/IAST/DAST) se ejecuten en cada solicitud de extracción que contenga código generado por IA y bloqueen las fusiones ante hallazgos críticos.
 #AD.4.3    Nivel: 3    Rol: D/V
 Verifique que las pruebas de fuzzing diferencial o pruebas property‑based demuestren comportamientos críticos para la seguridad (p. ej., validación de entradas, lógica de autorización).

---

### AD.5 Explicabilidad y trazabilidad de las sugerencias de código

Brindar a los auditores y a los desarrolladores una visión de por qué se hizo una sugerencia y cómo evolucionó.

 #AD.5.1    Nivel: 1    Rol: D/V
 Verifique que los pares de prompt/respuesta se registren con identificadores de confirmación.
 #AD.5.2    Nivel: 2    Rol: D
 Verificar que los desarrolladores puedan mostrar citas del modelo (fragmentos de entrenamiento, documentación) que respalden una sugerencia.
 #AD.5.3    Nivel: 3    Rol: D/V
 Verifique que los informes de explicabilidad se almacenen junto con artefactos de diseño y sean referenciados en las revisiones de seguridad, cumpliendo los principios de trazabilidad de ISO/IEC 42001.

---

### AD.6 Retroalimentación continua y ajuste fino del modelo

Mejorar el rendimiento de la seguridad del modelo con el tiempo, mientras se evita la deriva negativa.

 #AD.6.1    Nivel: 1    Rol: D/V
 Verifique que los desarrolladores puedan marcar sugerencias inseguras o no conformes y que las banderas sean rastreadas.
 #AD.6.2    Nivel: 2    Rol: D
 Verifique que la retroalimentación agregada informe el ajuste fino periódico o la generación aumentada por recuperación con corpus de codificación segura verificados (p. ej., OWASP Cheat Sheets).
 #AD.6.3    Nivel: 3    Rol: D/V
 Verifique que un entorno de evaluación en bucle cerrado ejecute pruebas de regresión después de cada ajuste‑fino; las métricas de seguridad deben cumplir o superar las líneas base previas antes del despliegue.

---

#### Referencias

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Apéndice E: Herramientas y marcos de trabajo de ejemplo

### Objetivo

Este capítulo proporciona ejemplos de herramientas y marcos de trabajo que pueden apoyar la implementación o el cumplimiento de un requisito AISVS dado. Estos no deben interpretarse como recomendaciones ni avales por parte del equipo AISVS o del Proyecto de Seguridad GenAI de OWASP.

---

### AE.1 Gobernanza de datos de entrenamiento y gestión de sesgos

Herramientas utilizadas para el análisis de datos, la gobernanza y la gestión de sesgos.

 #AE.1.1    Sección: 1.1
 Herramientas de inventario de datos: herramientas de gestión de inventario de datos como...
 #AE.1.2    Sección: 1.2
 Cifrado en tránsito: Use TLS para aplicaciones basadas en HTTPS, con herramientas como OpenSSL y de Python.`ssl` biblioteca.

---

### AE.2 Validación de la entrada del usuario

Herramientas para manejar y validar las entradas de usuario.

 #AE.2.1    Sección: 2.1
 Herramientas de defensa contra la inyección de prompts: utilice herramientas de guardrail como NeMo de NVIDIA o Guardrails AI.

---

