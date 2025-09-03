# C3 Gestión del ciclo de vida del modelo y control de cambios

## Objetivo de control

Los sistemas de IA deben implementar procesos de control de cambios que eviten modificaciones no autorizadas o inseguras del modelo que lleguen a producción. Este control garantiza la integridad del modelo a lo largo de todo el ciclo de vida--desde el desarrollo hasta la implementación y el descomisionamiento--lo que permite una respuesta rápida a incidentes y mantiene la rendición de cuentas por todos los cambios.

Objetivo central de seguridad: Solo los modelos autorizados y validados llegan a producción mediante procesos controlados que mantienen la integridad, la trazabilidad y la recuperabilidad.

---

## C3.1 Autorización e Integridad del Modelo

Solo los modelos autorizados con integridad verificada llegan a los entornos de producción.

|   #   | Descripción                                                                                                                                                                                                                                                                | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.1.1 | Verifique que todos los artefactos del modelo (pesos, configuraciones, tokenizadores) estén firmados criptográficamente por entidades autorizadas antes del despliegue.                                                                                                    |   1   | D/V |
| 3.1.2 | Verifique que se valide la integridad del modelo en el momento del despliegue y que las fallas de verificación de firmas impidan la carga del modelo.                                                                                                                      |   1   | D/V |
| 3.1.3 | Verifique que los registros de procedencia del modelo incluyan la identidad de la entidad autorizante, sumas de verificación de los datos de entrenamiento, resultados de las pruebas de validación con estado de aprobado o reprobado, y una marca de tiempo de creación. |   2   | D/V |
| 3.1.4 | Verifique que todos los artefactos del modelo utilicen versionado semántico (MAJOR.MINOR.PATCH) con criterios documentados que indiquen cuándo se incrementa cada componente de la versión.                                                                                |   2   | D/V |
| 3.1.5 | Verifique que el seguimiento de dependencias mantenga un inventario en tiempo real que permita la identificación rápida de todos los sistemas que consumen.                                                                                                                |   2   |  V  |

---

## C3.2 Validación del modelo y pruebas

Los modelos deben superar las validaciones de seguridad y protección definidas antes del despliegue.

|   #   | Descripción                                                                                                                                                                                                                                                    | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.2.1 | Verifique que los modelos se sometan a pruebas de seguridad automatizadas que incluyan validación de entradas, sanitización de salidas y evaluaciones de seguridad con umbrales de aceptación y rechazo preacordados por la organización antes del despliegue. |   1   | D/V |
| 3.2.2 | Verifique que las fallas de validación bloqueen automáticamente el despliegue del modelo tras la aprobación explícita de la anulación por parte del personal autorizado pre-designado, con justificaciones comerciales documentadas.                           |   1   | D/V |
| 3.2.3 | Verifique que los resultados de pruebas estén firmados criptográficamente y vinculados de forma inmutable al hash de la versión específica del modelo que se está validando.                                                                                   |   2   |  V  |
| 3.2.4 | Verifique que los despliegues de emergencia requieren una evaluación de riesgos de seguridad documentada y la aprobación de una autoridad de seguridad predesignada dentro de los plazos previamente acordados.                                                |   2   | D/V |

---

## C3.3 Despliegue controlado y reversión

Los despliegues de modelos deben ser controlados, monitorizados y reversibles.

|   #   | Descripción                                                                                                                                                                                                                                                                                 | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.3.1 | Verifique que los despliegues de producción implementen mecanismos de despliegue gradual (despliegues canary, despliegues blue-green) con disparadores de reversión automatizados basados en tasas de error acordadas previamente, umbrales de latencia o criterios de alerta de seguridad. |   1   |  D  |
| 3.3.2 | Verifique que las capacidades de rollback restauren el estado completo del modelo (pesos, configuraciones, dependencias) de forma atómica dentro de ventanas de tiempo predefinidas por la organización.                                                                                    |   1   | D/V |
| 3.3.3 | Verifique que los procesos de implementación validen las firmas criptográficas y calculen las sumas de verificación de integridad antes de la activación del modelo, y que la implementación falle ante cualquier desajuste.                                                                |   2   | D/V |
| 3.3.4 | Verifique que las capacidades de apagado de emergencia del modelo puedan deshabilitar los puntos finales del modelo dentro de los tiempos de respuesta predefinidos mediante disyuntores automáticos o interruptores de apagado manual.                                                     |   2   | D/V |
| 3.3.5 | Verifique que los artefactos de reversión (versiones anteriores del modelo, configuraciones, dependencias) se conserven de acuerdo con las políticas de la organización, con almacenamiento inmutable para la respuesta ante incidentes.                                                    |   2   |  V  |

---

## C3.4 Rendición de cuentas y auditoría de cambios

Todos los cambios en el ciclo de vida del modelo deben ser trazables y susceptibles de auditoría.

|   #   | Descripción                                                                                                                                                                                                                                                                        | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.4.1 | Verifique que todos los cambios de modelo (despliegue, configuración, retiro) generen registros de auditoría inmutables que incluyan una marca de tiempo, la identidad de un actor autenticado, un tipo de cambio y estados previos y posteriores.                                 |   1   |  V  |
| 3.4.2 | Verifique que el acceso al registro de auditoría requiera la autorización adecuada y que todos los intentos de acceso se registren con la identidad del usuario y una marca de tiempo.                                                                                             |   2   | D/V |
| 3.4.3 | Verifique que las plantillas de prompts y los mensajes del sistema estén bajo control de versiones en repositorios Git, con revisión de código obligatoria y aprobación de revisores designados antes del despliegue.                                                              |   2   | D/V |
| 3.4.4 | Verifique que los registros de auditoría incluyan detalles suficientes (hashes del modelo, instantáneas de configuración, versiones de dependencias) para permitir la reconstrucción completa del estado del modelo para cualquier marca temporal dentro del período de retención. |   2   |  V  |

---

## C3.5 Prácticas de Desarrollo Seguro

Los procesos de desarrollo y entrenamiento de modelos deben seguir prácticas seguras para prevenir violaciones de seguridad.

|   #   | Descripción                                                                                                                                                                                                                                           | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.5.1 | Verifique que los entornos de desarrollo, pruebas y producción de modelos estén separados física o lógicamente. No comparten infraestructura, cuentan con controles de acceso distintos y almacenes de datos aislados.                                |   1   |  D  |
| 3.5.2 | Verifique que el entrenamiento y el ajuste fino del modelo ocurran en entornos aislados con acceso a la red controlado.                                                                                                                               |   1   |  D  |
| 3.5.3 | Verifique que las fuentes de datos de entrenamiento estén validadas mediante verificaciones de integridad y autenticadas a través de fuentes confiables con una cadena de custodia documentada antes de su uso en el desarrollo de modelos.           |   1   | D/V |
| 3.5.4 | Verifique que los artefactos de desarrollo del modelo (hiperparámetros, scripts de entrenamiento, archivos de configuración) estén almacenados en el control de versiones y que cuenten con aprobación por pares antes de su uso en el entrenamiento. |   2   |  D  |

---

## C3.6 Retiro y desactivación del modelo

Los modelos deben ser retirados de forma segura cuando ya no sean necesarios o cuando se identifiquen problemas de seguridad.

|   #   | Descripción                                                                                                                                                                                                                                                    | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.6.1 | Verifique que los procesos de retirada de modelos escaneen automáticamente los grafos de dependencias, identifiquen todos los sistemas que los consumen y proporcionen plazos de preaviso acordados previamente antes de su retirada.                          |   1   |  D  |
| 3.6.2 | Verifique que los artefactos de modelos retirados se borren de forma segura mediante borrado criptográfico o sobreescritura en múltiples pases, de acuerdo con las políticas documentadas de retención de datos y con certificados de destrucción verificados. |   1   | D/V |
| 3.6.3 | Verifique que los eventos de retiro de modelos se registren con marca de tiempo e identidad del actor, y que las firmas del modelo se revocen para evitar su reutilización.                                                                                    |   2   |  V  |
| 3.6.4 | Verifique que el retiro de emergencia del modelo pueda deshabilitar el acceso al modelo dentro de los plazos de respuesta de emergencia preestablecidos mediante interruptores automáticos de apagado si se descubren vulnerabilidades de seguridad críticas.  |   2   | D/V |

---

## Referencias

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

