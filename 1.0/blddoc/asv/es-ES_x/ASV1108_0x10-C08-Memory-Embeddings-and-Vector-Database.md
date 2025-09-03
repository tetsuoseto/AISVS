# C8 Memory, Embeddings y Seguridad de la Base de Datos Vectorial

## Objetivo de control

Representaciones de incrustación y almacenes de vectores actúan como la "memoria en vivo" de los sistemas de IA contemporáneos, aceptando de forma continua datos proporcionados por el usuario y devolviéndolos a los contextos del modelo a través de Generación aumentada por recuperación (RAG). Si no se gobiernan, esta memoria puede filtrarse información de identificación personal (PII), violar el consentimiento o invertirse para reconstruir el texto original. El objetivo de esta familia de controles es endurecer las canalizaciones de memoria y las bases de datos de vectores para garantizar un acceso de mínimo privilegio, la preservación de la privacidad por parte de las representaciones de incrustación, la expiración o revocación bajo demanda de los vectores almacenados, y que la memoria por usuario nunca contamine las solicitudes o las completaciones de otro usuario.

---

## C8.1 Controles de acceso a índices de memoria y RAG

Implemente controles de acceso granulares en cada colección de vectores.

|   #   | Descripción                                                                                                                                                                                             | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.1.1 | Verifique que las reglas de control de acceso a nivel de fila o de espacio de nombres limiten las operaciones de inserción, eliminación y consulta por inquilino, colección o etiqueta de documento.    |   1   | D/V |
| 8.1.2 | Verifique que las claves API o los JWT contengan atributos con alcance (por ejemplo, identificadores de colección, verbos de acción) y que se roten al menos cada trimestre.                            |   1   | D/V |
| 8.1.3 | Verifique que los intentos de escalamiento de privilegios (p. ej., consultas de similitud entre espacios de nombres) sean detectados y se registren en un SIEM dentro de 5 minutos.                     |   2   | D/V |
| 8.1.4 | Verifique que los registros de auditoría de la base de datos vectorial contengan el identificador del sujeto, la operación, el vector ID/namespace, el umbral de similitud y la cantidad de resultados. |   2   | D/V |
| 8.1.5 | Verifique que las decisiones de acceso se prueben en busca de fallos de bypass cada vez que se actualicen los motores o cambien las reglas de index-sharding.                                           |   3   |  V  |

---

## C8.2 Sanitización y Validación de Embeddings

Cribar previamente el texto para información de identificación personal (PII), redactar o seudonimizar antes de la vectorización y, opcionalmente, postprocesar los embeddings para eliminar señales residuales.

|   #   | Descripción                                                                                                                                                                                                                               | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.2.1 | Verifique que PII y datos regulados sean detectados mediante clasificadores automatizados y enmascarados, tokenizados o eliminados antes de la incrustación.                                                                              |   1   | D/V |
| 8.2.2 | Verificar que los pipelines de embeddings rechacen o pongan en cuarentena las entradas que contengan código ejecutable o artefactos no UTF-8 que podrían corromper el índice.                                                             |   1   |  D  |
| 8.2.3 | Verifique que se aplique la sanitización con privacidad diferencial local o con privacidad diferencial métrica a los embeddings de oraciones cuya distancia a cualquier token de PII conocido caiga por debajo de un umbral configurable. |   2   | D/V |
| 8.2.4 | Verifique que la eficacia de la sanitización (p. ej., la tasa de recall de la redacción de PII, deriva semántica) se valide al menos semestralmente frente a corpora de referencia.                                                       |   2   |  V  |
| 8.2.5 | Verifique que las configuraciones de sanitización estén bajo control de versiones y que los cambios sean revisados por pares.                                                                                                             |   3   | D/V |

---

## C8.3 Expiración de la memoria, revocación y eliminación

GDPR "derecho al olvido" y leyes similares exigen un borrado oportuno; por lo tanto, los almacenes de vectores deben soportar TTL (tiempo de vida), borrados definitivos y tombstoning para que los vectores revocados no puedan ser recuperados ni reindexados.

|   #   | Descripción                                                                                                                                                                        | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.3.1 | Verifique que cada vector y registro de metadatos lleve un TTL o una etiqueta de retención explícita, y que estos sean respetados por los trabajos de limpieza automatizados.      |   1   | D/V |
| 8.3.2 | Verifique que las solicitudes de eliminación iniciadas por el usuario purguen vectores, metadatos, copias en caché e índices derivados dentro de 30 días.                          |   1   | D/V |
| 8.3.3 | Verifique que los borrados lógicos vayan seguidos del borrado criptográfico de los bloques de almacenamiento si el hardware lo admite, o de la destrucción de claves en Key Vault. |   2   |  D  |
| 8.3.4 | Verifique que los vectores caducados estén excluidos de los resultados de la búsqueda del vecino más cercano en < 500 ms después de la expiración.                                 |   3   | D/V |

---

## C8.4 Prevención de la inversión de embeddings y fuga de datos

Defensas recientes—superposición de ruido, redes de proyección, perturbación de neuronas de privacidad y cifrado a nivel de capa de aplicación—pueden reducir las tasas de inversión a nivel de tokens por debajo de 5%.

|   #   | Descripción                                                                                                                                                                                        | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.4.1 | Verifique que exista un modelo de amenazas formal que cubra ataques de inversión, de pertenencia y de inferencia de atributos y que se revise anualmente.                                          |   1   |  V  |
| 8.4.2 | Verifique que el cifrado a nivel de aplicación o el cifrado buscable proteja los vectores de lecturas directas por parte de los administradores de infraestructura o del personal de la nube.      |   2   | D/V |
| 8.4.3 | Verifique que los parámetros de defensa (ε para DP, ruido σ, rango de proyección k) equilibren la privacidad ≥ 99 % para la protección de tokens y la utilidad ≤ 3 % para la pérdida de precisión. |   3   |  V  |
| 8.4.4 | Asegúrese de que las métricas de resiliencia ante la inversión formen parte de las puertas de liberación para actualizaciones de modelos, con presupuestos de regresión definidos.                 |   3   | D/V |

---

## C8.5 Aplicación del alcance para la memoria específica del usuario

La filtración entre inquilinos sigue siendo uno de los principales riesgos de RAG: consultas de similitud filtradas de forma inapropiada pueden exponer los documentos privados de otro cliente.

|   #   | Descripción                                                                                                                                                                           | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.5.1 | Verifique que cada consulta de recuperación esté filtrada posteriormente por el ID de inquilino/usuario antes de ser enviada al prompt del LLM.                                       |   1   | D/V |
| 8.5.2 | Verifique que los nombres de colección o identificadores con espacio de nombres estén salteados por usuario o inquilino para que los vectores no puedan colisionar entre ámbitos.     |   1   |  D  |
| 8.5.3 | Verifique que los resultados de similitud por encima de un umbral de distancia configurable, pero fuera del alcance del llamante, sean descartados y se activen alertas de seguridad. |   2   | D/V |
| 8.5.4 | Verifique que las pruebas de estrés multitenantes simulen consultas adversarias que intenten recuperar documentos fuera de alcance y demuestren que no hay filtración de datos.       |   2   |  V  |
| 8.5.5 | Verifique que las claves de cifrado estén segregadas por inquilino, asegurando aislamiento criptográfico incluso si el almacenamiento físico es compartido.                           |   3   | D/V |

---

## C8.6 Seguridad avanzada del sistema de memoria

Controles de seguridad para arquitecturas de memoria sofisticadas, que incluyen memoria episódica, memoria semántica y memoria de trabajo, con requisitos específicos de aislamiento y validación.

|   #   | Descripción                                                                                                                                                                                                                                                                                            | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 8.6.1 | Verifique que los diferentes tipos de memoria (episódica, semántica y de trabajo) tengan contextos de seguridad aislados con controles de acceso basados en roles, claves de cifrado separadas y patrones de acceso documentados para cada tipo de memoria.                                            |   1   | D/V |
| 8.6.2 | Verifique que los procesos de consolidación de memoria incluyan validación de seguridad para evitar la inyección de memorias maliciosas mediante la sanitización de contenido, la verificación de origen y las comprobaciones de integridad antes del almacenamiento.                                  |   2   | D/V |
| 8.6.3 | Verifique que las consultas de recuperación de memoria sean validadas y sanitizadas para evitar la extracción de información no autorizada mediante el análisis de patrones de consulta, la implementación de controles de acceso y el filtrado de resultados.                                         |   2   | D/V |
| 8.6.4 | Verifique que los mecanismos de borrado de memoria eliminen de forma segura la información sensible, con garantías de borrado criptográfico, utilizando eliminación de claves, sobrescritura en múltiples pasadas o borrado seguro basado en hardware con certificados de verificación.                |   3   | D/V |
| 8.6.5 | Verifique que la integridad del sistema de memoria se supervise de forma continua para detectar modificaciones no autorizadas o corrupción, mediante sumas de verificación, registros de auditoría y alertas automatizadas cuando el contenido de la memoria cambie fuera de las operaciones normales. |   3   | D/V |

---

## Referencias

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

