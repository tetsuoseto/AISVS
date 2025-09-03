# C5 Control de Acceso e Identidad para Componentes de IA y Usuarios

## Objetivo de control

El control de acceso efectivo para los sistemas de IA requiere una gestión de identidades robusta, autorización basada en el contexto y una aplicación en tiempo de ejecución que siga los principios de confianza cero. Estos controles aseguran que personas, servicios y agentes autónomos solo interactúen con modelos, datos y recursos computacionales dentro de alcances explícitamente concedidos, con verificación continua y capacidades de auditoría.

---

## C5.1 Gestión de identidades y autenticación

Establezca identidades respaldadas criptográficamente para todas las entidades, con autenticación multifactor para operaciones privilegiadas.

|   #   | Descripción                                                                                                                                                                                                                                                                       | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.1.1 | Verifique que todos los usuarios humanos y los principales de servicio se autentiquen a través de un proveedor de identidad empresarial centralizado (IdP) utilizando los protocolos OIDC/SAML, con mapeos únicos de identidad a token (sin cuentas ni credenciales compartidas). |   1   | D/V |
| 5.1.2 | Verifique que las operaciones de alto riesgo (despliegue de modelos, exportación de pesos, acceso a datos de entrenamiento, cambios en la configuración de producción) requieran autenticación multifactor o autenticación reforzada con revalidación de sesión.                  |   1   | D/V |
| 5.1.3 | Asegúrese de que los nuevos principales se sometan a una verificación de identidad que esté alineada con NIST 800-63-3 IAL-2 o estándares equivalentes antes de recibir acceso al sistema de producción.                                                                          |   2   |  D  |
| 5.1.4 | Verifique que las revisiones de acceso se realicen trimestralmente con detección automatizada de cuentas inactivas, cumplimiento de la rotación de credenciales y flujos de desprovisionamiento.                                                                                  |   2   |  V  |
| 5.1.5 | Verifique que los agentes de IA federados se autentiquen mediante aserciones JWT firmadas que tengan una duración máxima de 24 horas y que incluyan prueba criptográfica de origen.                                                                                               |   3   | D/V |

---

## C5.2 Autorización de recursos y el principio de mínimo privilegio

Implementa controles de acceso granulares para todos los recursos de IA, con modelos de permisos explícitos y registros de auditoría.

|   #   | Descripción                                                                                                                                                                                                                                                                      | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.2.1 | Verifique que cada recurso de IA (conjuntos de datos, modelos, puntos finales, colecciones vectoriales, índices de embeddings, instancias de cómputo) aplique controles de acceso basados en roles con listas de permitidos explícitas y políticas de denegación por defecto.    |   1   | D/V |
| 5.2.2 | Verifique que los principios de mínimo privilegio se apliquen por defecto con cuentas de servicio que comienzan con permisos de solo-lectura y se requiera una justificación comercial documentada para el acceso de escritura.                                                  |   1   | D/V |
| 5.2.3 | Verifique que todas las modificaciones del control de acceso estén vinculadas a solicitudes de cambio aprobadas y registradas de forma inmutable con marcas de tiempo, identidades de los actores, identificadores de recursos y deltas de permisos.                             |   1   |  V  |
| 5.2.4 | Verifique que las etiquetas de clasificación de datos (PII, PHI, export-controlled, propietarias) se propaguen automáticamente a los recursos derivados (representaciones vectoriales, cachés de indicaciones, salidas del modelo) con la aplicación consistente de la política. |   2   |  D  |
| 5.2.5 | Verifique que los intentos de acceso no autorizado y los eventos de escalada de privilegios activen alertas en tiempo real con metadatos contextuales a los sistemas SIEM dentro de 5 minutos.                                                                                   |   2   | D/V |

---

## C5.3 Evaluación dinámica de políticas

Desplegar motores de control de acceso basado en atributos (ABAC) para decisiones de autorización sensibles al contexto con capacidades de auditoría.

|   #   | Descripción                                                                                                                                                                                                                                                                    | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 5.3.1 | Verifique que las decisiones de autorización estén externalizadas a un motor de políticas dedicado (OPA, Cedar, u equivalente) accesible a través de APIs autenticadas con protección de integridad criptográfica.                                                             |   1   | D/V |
| 5.3.2 | Verifique que las políticas evalúen atributos dinámicos en tiempo de ejecución, incluyendo el nivel de autorización del usuario, la clasificación de la sensibilidad del recurso, el contexto de la solicitud, el aislamiento entre inquilinos y las restricciones temporales. |   1   | D/V |
| 5.3.3 | Verifique que las definiciones de políticas estén bajo control de versiones, sean revisadas por pares y validadas mediante pruebas automatizadas en pipelines de CI/CD antes del despliegue en producción.                                                                     |   2   |  D  |
| 5.3.4 | Verifique que los resultados de la evaluación de políticas incluyan fundamentos de decisión estructurados y se transmitan a los sistemas SIEM para análisis de correlación y reportes de cumplimiento.                                                                         |   2   |  V  |
| 5.3.5 | Verifique que los valores de TTL de la caché de políticas no excedan 5 minutos para recursos de alta sensibilidad y 1 hora para recursos estándar con capacidades de invalidación de caché.                                                                                    |   3   | D/V |

---

## C5.4 Aplicación de seguridad en tiempo de consulta

Implementar controles de seguridad en la capa de base de datos con filtrado obligatorio y políticas de seguridad a nivel de fila.

|   #   | Descripción                                                                                                                                                                                                                                                                             | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.4.1 | Verifique que todas las consultas de bases de datos vectoriales y consultas SQL incluyan filtros de seguridad obligatorios (ID de inquilino, etiquetas de sensibilidad, alcance del usuario) que se apliquen a nivel del motor de la base de datos, y no en el código de la aplicación. |   1   | D/V |
| 5.4.2 | Verifique que las políticas de seguridad a nivel de fila (RLS) y la ocultación a nivel de campo estén habilitadas con herencia de políticas para todas las bases de datos vectoriales, índices de búsqueda y conjuntos de datos de entrenamiento.                                       |   1   | D/V |
| 5.4.3 | Verifique que las evaluaciones de autorización fallidas eviten los ataques del ayudante confundido al abortar de inmediato las consultas y devolver códigos de error de autorización explícitos en lugar de devolver conjuntos de resultados vacíos.                                    |   2   |  D  |
| 5.4.4 | Verifique que la latencia de la evaluación de políticas se supervise de forma continua con alertas automáticas para condiciones de tiempo de espera que podrían permitir eludir la autorización.                                                                                        |   2   |  V  |
| 5.4.5 | Verifique que los mecanismos de reintento de consultas reevalúen las políticas de autorización para tener en cuenta los cambios dinámicos de permisos dentro de las sesiones de usuario activas.                                                                                        |   3   | D/V |

---

## C5.5 Filtrado de salida y Prevención de pérdida de datos

Desplegar controles de posprocesamiento para prevenir la exposición no autorizada de datos en contenido generado por IA.

|   #   | Descripción                                                                                                                                                                                                                | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.5.1 | Verifique que los mecanismos de filtrado posteriores a la inferencia escaneen y redacten PII no autorizada, información clasificada y datos propietarios antes de entregar el contenido a los solicitantes.                |   1   | D/V |
| 5.5.2 | Verifique que las citas, referencias y atribuciones de origen en las salidas del modelo se validen frente a los derechos del solicitante y se eliminen si se detecta acceso no autorizado.                                 |   1   | D/V |
| 5.5.3 | Verifique que las restricciones de formato de salida (PDFs sanitizados, imágenes sin metadatos, tipos de archivos aprobados) se apliquen de acuerdo con los niveles de permisos de usuario y las clasificaciones de datos. |   2   |  D  |
| 5.5.4 | Verifique que los algoritmos de enmascaramiento sean deterministas, tengan control de versiones y mantengan registros de auditoría para respaldar investigaciones de cumplimiento y análisis forense.                      |   2   |  V  |
| 5.5.5 | Verificar que los eventos de redacción de alto riesgo generen registros adaptativos que incluyan hashes criptográficos del contenido original para recuperación forense sin exponer los datos.                             |   3   |  V  |

---

## C5.6 Aislamiento multitenante

Garantice el aislamiento criptográfico y lógico entre inquilinos en una infraestructura de IA compartida.

|   #   | Descripción                                                                                                                                                                                                                                           | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.6.1 | Verifique que los espacios de memoria, los almacenes de embeddings, las entradas de caché y los archivos temporales estén segmentados por espacio de nombres para cada inquilino, con purga segura al eliminar el inquilino o al finalizar la sesión. |   1   | D/V |
| 5.6.2 | Verifique que cada solicitud de API incluya un identificador de inquilino autenticado que esté validado criptográficamente frente al contexto de la sesión y a los derechos del usuario.                                                              |   1   | D/V |
| 5.6.3 | Verifique que las políticas de red implementen reglas de denegación por defecto para la comunicación entre inquilinos dentro de las mallas de servicios y las plataformas de orquestación de contenedores.                                            |   2   |  D  |
| 5.6.4 | Verifique que las claves de cifrado sean únicas por inquilino, con soporte para clave gestionada por el cliente (CMK) y aislamiento criptográfico entre los almacenes de datos de los inquilinos.                                                     |   3   |  D  |

---

## C5.7 Autorización de Agente Autónomo

Controlar permisos para los agentes de IA y los sistemas autónomos mediante tokens de capacidad con alcance definido y autorización continua.

|   #   | Descripción                                                                                                                                                                                                                                                                        | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.7.1 | Asegúrese de que los agentes autónomos reciban tokens de capacidad acotados que enumeren explícitamente las acciones permitidas, los recursos accesibles, los límites de tiempo y las restricciones operativas.                                                                    |   1   | D/V |
| 5.7.2 | Verifique que las capacidades de alto riesgo (acceso al sistema de archivos, ejecución de código, llamadas a API externas, transacciones financieras) estén deshabilitadas por defecto y requieran autorizaciones explícitas para su activación con justificaciones empresariales. |   1   | D/V |
| 5.7.3 | Verifique que los tokens de capacidad estén vinculados a las sesiones de usuario, incluyan protección de integridad criptográfica y asegúrese de que no puedan ser persistidos ni reutilizados en escenarios sin conexión.                                                         |   2   |  D  |
| 5.7.4 | Verifique que las acciones iniciadas por un agente pasen por una autorización secundaria a través del motor de políticas ABAC con evaluación de contexto completa y registro de auditoría.                                                                                         |   2   |  V  |
| 5.7.5 | Verifique que las condiciones de error del agente y el manejo de excepciones incluyan información sobre el alcance de las capacidades para apoyar el análisis de incidentes y la investigación forense.                                                                            |   3   |  V  |

---

## Referencias

### Estándares y Marcos

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Guías de Implementación

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Seguridad específica de IA

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

