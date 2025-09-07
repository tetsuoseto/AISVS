# Control de Acceso C5 e Identidad para Componentes y Usuarios de IA

## Objetivo de Control

El control de acceso efectivo para los sistemas de IA requiere una gestión de identidad robusta, autorización consciente del contexto y aplicación en tiempo de ejecución siguiendo los principios de confianza cero. Estos controles garantizan que los humanos, servicios y agentes autónomos solo interactúen con modelos, datos y recursos computacionales dentro de los ámbitos explícitamente otorgados, con capacidades continuas de verificación y auditoría.

---

## C5.1 Gestión de Identidad y Autenticación

Establecer identidades respaldadas criptográficamente para todas las entidades con autenticación multifactor para operaciones privilegiadas.

|   #   | Descripción                                                                                                                                                                                                                                                                       | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.1.1 | Verifique que todos los usuarios humanos y principales de servicio se autentiquen a través de un proveedor de identidad empresarial centralizado (IdP) utilizando los protocolos OIDC/SAML con asignaciones únicas de identidad a token (sin cuentas o credenciales compartidas). |   1   | D/V |
| 5.1.2 | Verifique que las operaciones de alto riesgo (despliegue de modelos, exportación de pesos, acceso a datos de entrenamiento, cambios en la configuración de producción) requieran autenticación multifactor o autenticación escalonada con revalidación de sesión.                 |   1   | D/V |
| 5.1.3 | Verifique que los nuevos responsables se sometan a una verificación de identidad que esté alineada con NIST 800-63-3 IAL-2 o estándares equivalentes antes de recibir acceso al sistema de producción.                                                                            |   2   |  D  |
| 5.1.4 | Verifique que las revisiones de acceso se realicen trimestralmente con detección automática de cuentas inactivas, aplicación de la rotación de credenciales y flujos de trabajo de desprovimiento.                                                                                |   2   |  V  |
| 5.1.5 | Verifique que los agentes de IA federados se autentiquen mediante aserciones JWT firmadas que tengan una vida útil máxima de 24 horas e incluyan prueba criptográfica de origen.                                                                                                  |   3   | D/V |

---

## C5.2 Autorización de Recursos y Mínimos Privilegios

Implemente controles de acceso detallados para todos los recursos de IA con modelos de permiso explícitos y registros de auditoría.

|   #   | Descripción                                                                                                                                                                                                                                                                            | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.2.1 | Verifique que cada recurso de IA (conjuntos de datos, modelos, puntos finales, colecciones vectoriales, índices de incrustación, instancias de computación) implemente controles de acceso basados en roles con listas de permitidos explícitas y políticas de denegación por defecto. |   1   | D/V |
| 5.2.2 | Verifique que los principios de mínimo privilegio se apliquen por defecto con las cuentas de servicio, comenzando con permisos de solo lectura y requiriendo una justificación comercial documentada para el acceso de escritura.                                                      |   1   | D/V |
| 5.2.3 | Verifique que todas las modificaciones de control de acceso estén vinculadas a solicitudes de cambio aprobadas y registradas de forma inmutable con marcas de tiempo, identidades de actores, identificadores de recursos y deltas de permisos.                                        |   1   |  V  |
| 5.2.4 | Verifique que las etiquetas de clasificación de datos (PII, PHI, controladas por exportación, propietarias) se propaguen automáticamente a los recursos derivados (embeddings, cachés de prompts, salidas del modelo) con una aplicación de políticas coherente.                       |   2   |  D  |
| 5.2.5 | Verifique que los intentos de acceso no autorizados y los eventos de escalada de privilegios desencadenen alertas en tiempo real con metadatos contextuales hacia los sistemas SIEM dentro de los 5 minutos.                                                                           |   2   | D/V |

---

## C5.3 Evaluación Dinámica de Políticas

Implemente motores de control de acceso basado en atributos (ABAC) para decisiones de autorización conscientes del contexto con capacidades de auditoría.

|   #   | Descripción                                                                                                                                                                                                                                                              | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 5.3.1 | Verificar que las decisiones de autorización estén externalizadas a un motor de políticas dedicado (OPA, Cedar o equivalente) accesible mediante APIs autenticadas con protección de integridad criptográfica.                                                           |   1   | D/V |
| 5.3.2 | Verifique que las políticas evalúen atributos dinámicos en tiempo de ejecución, incluyendo el nivel de autorización del usuario, la clasificación de sensibilidad del recurso, el contexto de la solicitud, el aislamiento del inquilino y las restricciones temporales. |   1   | D/V |
| 5.3.3 | Verifique que las definiciones de políticas estén controladas por versiones, revisadas por pares y validadas mediante pruebas automatizadas en los pipelines de CI/CD antes del despliegue en producción.                                                                |   2   |  D  |
| 5.3.4 | Verifique que los resultados de la evaluación de políticas incluyan fundamentos estructurados de las decisiones y se transmitan a los sistemas SIEM para análisis de correlación e informes de cumplimiento.                                                             |   2   |  V  |
| 5.3.5 | Verifique que los valores de tiempo de vida (TTL) de la caché de políticas no superen los 5 minutos para recursos de alta sensibilidad y 1 hora para recursos estándar con capacidades de invalidación de caché.                                                         |   3   | D/V |

---

## C5.4 Aplicación de Seguridad en Tiempo de Consulta

Implemente controles de seguridad en la capa de base de datos con filtrado obligatorio y políticas de seguridad a nivel de fila.

|   #   | Descripción                                                                                                                                                                                                                                                       | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.4.1 | Verifique que todas las consultas a bases de datos vectoriales y SQL incluyan filtros de seguridad obligatorios (ID de inquilino, etiquetas de sensibilidad, alcance del usuario) aplicados a nivel del motor de base de datos, no en el código de la aplicación. |   1   | D/V |
| 5.4.2 | Verifique que las políticas de seguridad a nivel de fila (RLS) y el enmascaramiento a nivel de campo estén habilitados con herencia de políticas para todas las bases de datos vectoriales, índices de búsqueda y conjuntos de datos de entrenamiento.            |   1   | D/V |
| 5.4.3 | Verifique que las evaluaciones de autorización fallidas evitarán los "ataques de delegado confundido" al abortar inmediatamente las consultas y devolver códigos de error de autorización explícitos en lugar de devolver conjuntos de resultados vacíos.         |   2   |  D  |
| 5.4.4 | Verifique que la latencia de evaluación de políticas se monitoree continuamente con alertas automatizadas para condiciones de tiempo de espera que podrían permitir la omisión de la autorización.                                                                |   2   |  V  |
| 5.4.5 | Verifique que los mecanismos de reintento de consultas vuelvan a evaluar las políticas de autorización para tener en cuenta los cambios dinámicos de permisos dentro de sesiones de usuario activas.                                                              |   3   | D/V |

---

## Filtrado de Salida C5.5 y Prevención de Pérdida de Datos

Implementar controles de postprocesamiento para prevenir la exposición no autorizada de datos en contenido generado por IA.

|   #   | Descripción                                                                                                                                                                                                                                        | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.5.1 | Verifique que los mecanismos de filtrado posterior a la inferencia escaneen y redacten información de identificación personal (PII) no autorizada, información clasificada y datos propietarios antes de entregar el contenido a los solicitantes. |   1   | D/V |
| 5.5.2 | Verifique que las citas, referencias y atribuciones de fuentes en las salidas del modelo estén validadas según los derechos del solicitante y se eliminen si se detecta acceso no autorizado.                                                      |   1   | D/V |
| 5.5.3 | Verificar que se apliquen las restricciones de formato de salida (PDFs sanitizados, imágenes con metadatos eliminados, tipos de archivos aprobados) según los niveles de permiso del usuario y las clasificaciones de datos.                       |   2   |  D  |
| 5.5.4 | Verifique que los algoritmos de redacción sean deterministas, controlados por versiones y mantengan registros de auditoría para respaldar las investigaciones de cumplimiento y el análisis forense.                                               |   2   |  V  |
| 5.5.5 | Verifique que los eventos de redacción de alto riesgo generen registros adaptativos que incluyan hashes criptográficos del contenido original para su recuperación forense sin exposición de datos.                                                |   3   |  V  |

---

## C5.6 Aislamiento Multiinquilino

Asegurar el aislamiento criptográfico y lógico entre inquilinos en una infraestructura de IA compartida.

|   #   | Descripción                                                                                                                                                                                                                                            | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 5.6.1 | Verifique que los espacios de memoria, los almacenes de incrustaciones, las entradas de caché y los archivos temporales estén segregados por espacio de nombres para cada inquilino, con purgado seguro al eliminar el inquilino o terminar la sesión. |   1   | D/V |
| 5.6.2 | Verifique que cada solicitud de API incluya un identificador de inquilino autenticado que esté validado criptográficamente contra el contexto de sesión y los derechos del usuario.                                                                    |   1   | D/V |
| 5.6.3 | Verifique que las políticas de red implementen reglas de denegación predeterminada para la comunicación entre inquilinos dentro de mallas de servicio y plataformas de orquestación de contenedores.                                                   |   2   |  D  |
| 5.6.4 | Verifique que las claves de cifrado sean únicas por inquilino con soporte de claves gestionadas por el cliente (CMK) y aislamiento criptográfico entre los almacenes de datos de los inquilinos.                                                       |   3   |  D  |

---

## C5.7 Autorización de Agente Autónomo

Controla los permisos para agentes de IA y sistemas autónomos mediante tokens de capacidad limitados y autorización continua.

|   #   | Descripción                                                                                                                                                                                                                                                                      | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 5.7.1 | Verifique que los agentes autónomos reciban tokens de capacidad con alcance que enumeren explícitamente las acciones permitidas, los recursos accesibles, los límites de tiempo y las restricciones operativas.                                                                  |   1   | D/V |
| 5.7.2 | Verifique que las capacidades de alto riesgo (acceso al sistema de archivos, ejecución de código, llamadas a API externas, transacciones financieras) estén deshabilitadas por defecto y requieran autorizaciones explícitas para su activación con justificaciones comerciales. |   1   | D/V |
| 5.7.3 | Verifique que los tokens de capacidad estén vinculados a las sesiones de usuario, incluyan protección criptográfica de integridad y aseguren que no puedan persistirse o reutilizarse en escenarios sin conexión.                                                                |   2   |  D  |
| 5.7.4 | Verifique que las acciones iniciadas por el agente pasen por una autorización secundaria a través del motor de políticas ABAC con evaluación de contexto completa y registro de auditoría.                                                                                       |   2   |  V  |
| 5.7.5 | Verifique que las condiciones de error del agente y el manejo de excepciones incluyan información del alcance de la capacidad para respaldar el análisis de incidentes y la investigación forense.                                                                               |   3   |  V  |

---

## Referencias

### Normas y Marcos de Trabajo

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Guías de Implementación

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Seguridad específica para IA

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

