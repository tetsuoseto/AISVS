# Gestión del Ciclo de Vida del Modelo C3 y Control de Cambios

## Objetivo de Control

Los sistemas de IA deben implementar procesos de control de cambios que eviten que modificaciones no autorizadas o inseguras del modelo lleguen a producción. Este control garantiza la integridad del modelo a lo largo de todo su ciclo de vida, desde el desarrollo hasta el despliegue y la desactivación, lo que permite una respuesta rápida ante incidentes y mantiene la responsabilidad por todos los cambios.

Objetivo de Seguridad Principal: Solo los modelos autorizados y validados llegan a producción mediante la aplicación de procesos controlados que mantienen la integridad, trazabilidad y recuperabilidad.

---

## C3.1 Autorización e Integridad del Modelo

Solo los modelos autorizados con integridad verificada llegan a los entornos de producción.

|   #   | Descripción                                                                                                                                                                                                                                                       | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.1.1 | Verifique que todos los artefactos del modelo (pesos, configuraciones, tokenizadores) estén firmados criptográficamente por entidades autorizadas antes del despliegue.                                                                                           |   1   | D/V |
| 3.1.2 | Verifique que la integridad del modelo se valide en el momento del despliegue y que las fallas en la verificación de la firma impidan la carga del modelo.                                                                                                        |   1   | D/V |
| 3.1.3 | Verifique que los registros de procedencia del modelo incluyan la identidad de la entidad autorizante, sumas de comprobación de los datos de entrenamiento, resultados de pruebas de validación con estado de aprobado/fallado y una marca de tiempo de creación. |   2   | D/V |
| 3.1.4 | Verifique que todos los artefactos del modelo utilicen versionado semántico (MAYOR.MENOR.PARCHE) con criterios documentados que especifiquen cuándo se incrementa cada componente de la versión.                                                                  |   2   | D/V |
| 3.1.5 | Verifique que el seguimiento de dependencias mantenga un inventario en tiempo real que permita la identificación rápida de todos los sistemas consumidores.                                                                                                       |   2   |  V  |

---

## C3.2 Validación y Pruebas del Modelo

Los modelos deben pasar las validaciones definidas de seguridad y seguridad antes del despliegue.

|   #   | Descripción                                                                                                                                                                                                                                                  | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 3.2.1 | Verifique que los modelos se sometan a pruebas de seguridad automatizadas que incluyan validación de entradas, saneamiento de salidas y evaluaciones de seguridad con umbrales de aprobación/reprobación organizacionales preacordados antes del despliegue. |   1   | D/V |
| 3.2.2 | Verifique que las fallas de validación bloqueen automáticamente el despliegue del modelo después de la aprobación explícita de anulación por parte del personal autorizado predesignado con justificaciones comerciales documentadas.                        |   1   | D/V |
| 3.2.3 | Verifique que los resultados de las pruebas estén firmados criptográficamente y vinculados de forma inmutable al hash de la versión específica del modelo que se está validando.                                                                             |   2   |  V  |
| 3.2.4 | Verifique que los despliegues de emergencia requieran una evaluación de riesgos de seguridad documentada y la aprobación de una autoridad de seguridad predesignada dentro de los plazos previamente acordados.                                              |   2   | D/V |

---

## C3.3 Despliegue Controlado y Reversión

Las implementaciones de modelos deben ser controladas, monitoreadas y reversibles.

|   #   | Descripción                                                                                                                                                                                                                                                                         | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.3.1 | Verifique que las implementaciones en producción utilicen mecanismos de despliegue gradual (despliegues canarios, despliegues azul-verde) con activadores automáticos de reversión basados en tasas de error, umbrales de latencia o criterios de alerta de seguridad preacordados. |   1   |  D  |
| 3.3.2 | Verifique que las capacidades de reversión restauren el estado completo del modelo (pesos, configuraciones, dependencias) de manera atómica dentro de las ventanas de tiempo organizacionales predefinidas.                                                                         |   1   | D/V |
| 3.3.3 | Verifique que los procesos de implementación validen las firmas criptográficas y calculen sumas de verificación de integridad antes de la activación del modelo, y que la implementación falle ante cualquier discrepancia.                                                         |   2   | D/V |
| 3.3.4 | Verifique que las capacidades de apagado de emergencia del modelo puedan deshabilitar los puntos finales del modelo dentro de los tiempos de respuesta predefinidos mediante interruptores automáticos de circuito o interruptores de apagado manuales.                             |   2   | D/V |
| 3.3.5 | Verifique que los artefactos de reversión (versiones anteriores del modelo, configuraciones, dependencias) se conserven según las políticas organizacionales con almacenamiento inmutable para la respuesta a incidentes.                                                           |   2   |  V  |

---

## C3.4 Cambio de Responsabilidad y Auditoría

Todos los cambios en el ciclo de vida del modelo deben ser rastreables y auditables.

|   #   | Descripción                                                                                                                                                                                                                                                                     | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.4.1 | Verifique que todos los cambios en el modelo (implementación, configuración, retiro) generen registros de auditoría inmutables que incluyan una marca de tiempo, una identidad de actor autenticada, un tipo de cambio y los estados antes/después.                             |   1   |  V  |
| 3.4.2 | Verifique que el acceso al registro de auditoría requiera la autorización adecuada y que todos los intentos de acceso se registren con la identidad del usuario y una marca de tiempo.                                                                                          |   2   | D/V |
| 3.4.3 | Verifique que las plantillas de indicaciones y los mensajes del sistema estén controlados por versiones en repositorios git con revisión de código obligatoria y aprobación de revisores designados antes de la implementación.                                                 |   2   | D/V |
| 3.4.4 | Verifique que los registros de auditoría incluyan detalles suficientes (hashes de modelos, capturas de configuración, versiones de dependencias) para permitir la reconstrucción completa del estado del modelo para cualquier marca de tiempo dentro del período de retención. |   2   |  V  |

---

## C3.5 Prácticas de Desarrollo Seguro

Los procesos de desarrollo y entrenamiento del modelo deben seguir prácticas seguras para prevenir compromisos.

|   #   | Descripción                                                                                                                                                                                                                                                    | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.5.1 | Verifique que los entornos de desarrollo, prueba y producción del modelo estén separados física o lógicamente. No deben compartir infraestructura, deben tener controles de acceso distintos y almacenes de datos aislados.                                    |   1   |  D  |
| 3.5.2 | Verifique que el entrenamiento y la afinación del modelo se realicen en entornos aislados con acceso de red controlado.                                                                                                                                        |   1   |  D  |
| 3.5.3 | Verifique que las fuentes de datos de entrenamiento sean validadas mediante controles de integridad y autenticadas a través de fuentes confiables con una cadena de custodia documentada antes de su uso en el desarrollo del modelo.                          |   1   | D/V |
| 3.5.4 | Verifique que los artefactos de desarrollo del modelo (hiperparámetros, scripts de entrenamiento, archivos de configuración) estén almacenados en control de versiones y requieran aprobación mediante revisión por pares antes de usarse en el entrenamiento. |   2   |  D  |

---

## C3.6 Retiro y Desmantelamiento del Modelo

Los modelos deben ser retirados de manera segura cuando ya no son necesarios o cuando se identifican problemas de seguridad.

|   #   | Descripción                                                                                                                                                                                                                                                      | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 3.6.1 | Verifique que los procesos de retiro de modelos escaneen automáticamente los grafos de dependencias, identifiquen todos los sistemas consumidores y proporcionen períodos de aviso previo acordados antes de la desactivación.                                   |   1   |  D  |
| 3.6.2 | Verifique que los artefactos de modelos retirados sean eliminados de forma segura utilizando borrado criptográfico o sobrescritura múltiple conforme a las políticas documentadas de retención de datos, con certificados de destrucción verificados.            |   1   | D/V |
| 3.6.3 | Verifique que los eventos de retiro del modelo se registren con marca de tiempo e identidad del actor, y que las firmas del modelo sean revocadas para prevenir su reutilización.                                                                                |   2   |  V  |
| 3.6.4 | Verifique que la retirada de modelos de emergencia pueda deshabilitar el acceso al modelo dentro de los plazos preestablecidos de respuesta a emergencias mediante interruptores automáticos en caso de que se descubran vulnerabilidades críticas de seguridad. |   2   | D/V |

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

