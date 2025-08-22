# Seguridad de Memoria C8, Embeddings y Bases de Datos Vectoriales

## Objetivo de Control

Los embeddings y los almacenes vectoriales actúan como la "memoria en vivo" de los sistemas de IA contemporáneos, aceptando continuamente datos suministrados por el usuario y devolviéndolos a los contextos del modelo mediante la Generación Aumentada por Recuperación (RAG). Si no se regulan, esta memoria puede filtrar información personal identificable (PII), violar el consentimiento o ser invertida para reconstruir el texto original. El objetivo de esta familia de controles es fortalecer las canalizaciones de memoria y las bases de datos vectoriales para que el acceso sea de privilegios mínimos, los embeddings respeten la privacidad, los vectores almacenados expiren o puedan ser revocados bajo demanda, y que la memoria por usuario nunca contamine las indicaciones o resultados de otro usuario.

---

## C8.1 Controles de Acceso en la Memoria y los Índices RAG

Implemente controles de acceso granulares en cada colección de vectores.

|   #   | Descripción                                                                                                                                                                                                    | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.1.1 | Verifique que las reglas de control de acceso a nivel de fila/espacio de nombres restrinjan las operaciones de inserción, eliminación y consulta según el inquilino, la colección o la etiqueta del documento. |   1   | D/V |
| 8.1.2 | Verifique que las claves API o JWT contengan claims con alcance definido (por ejemplo, IDs de colección, verbos de acción) y que se roten al menos trimestralmente.                                            |   1   | D/V |
| 8.1.3 | Verifique que los intentos de escalada de privilegios (por ejemplo, consultas de similitud entre espacios de nombres) se detecten y registren en un SIEM en un plazo de 5 minutos.                             |   2   | D/V |
| 8.1.4 | Verifique que la base de datos vectorial registre en el audit log el identificador del sujeto, la operación, el ID/namespace del vector, el umbral de similitud y el conteo de resultados.                     |   2   | D/V |
| 8.1.5 | Verifique que las decisiones de acceso se prueben para detectar fallas de omisión cada vez que se actualicen los motores o cambien las reglas de particionado de índices.                                      |   3   |  V  |

---

## C8.2 Saneamiento y Validación de Incrustaciones

Preseleccione el texto para información de identificación personal (PII), redacte o pseudonimice antes de la vectorización, y opcionalmente procese posteriormente las incrustaciones para eliminar señales residuales.

|   #   | Descripción                                                                                                                                                                                                                                      | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 8.2.1 | Verifique que los datos PII y regulados se detecten mediante clasificadores automáticos y se enmascaren, tokenicen o eliminen antes de la incrustación.                                                                                          |   1   | D/V |
| 8.2.2 | Verifique que las canalizaciones de incrustación rechacen o pongan en cuarentena las entradas que contengan código ejecutable o artefactos no UTF-8 que puedan envenenar el índice.                                                              |   1   |  D  |
| 8.2.3 | Verifique que se aplique la sanitización de privacidad diferencial local o métrica a las incrustaciones de oraciones cuya distancia a cualquier token de información personal identificable conocido caiga por debajo de un umbral configurable. |   2   | D/V |
| 8.2.4 | Verifique que la eficacia de la sanitización (por ejemplo, la recuperación de la redacción de datos de identificación personal, la deriva semántica) se valide al menos de forma semestral contra corpus de referencia.                          |   2   |  V  |
| 8.2.5 | Verifique que las configuraciones de sanitización estén controladas por versiones y que los cambios pasen por una revisión por pares.                                                                                                            |   3   | D/V |

---

## C8.3 Caducidad, Revocación y Eliminación de Memoria

El GDPR "derecho al olvido" y leyes similares requieren la eliminación oportuna; por lo tanto, las tiendas de vectores deben soportar TTL, eliminaciones permanentes y tomb-stoning para que los vectores revocados no puedan ser recuperados ni reindexados.

|   #   | Descripción                                                                                                                                                                                              | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.3.1 | Verifique que cada vector y registro de metadatos tenga un TTL o una etiqueta de retención explícita que sea respetada por los trabajos automáticos de limpieza.                                         |   1   | D/V |
| 8.3.2 | Verifique que las solicitudes de eliminación iniciadas por el usuario eliminen vectores, metadatos, copias de caché e índices derivados en un plazo de 30 días.                                          |   1   | D/V |
| 8.3.3 | Verifique que las eliminaciones lógicas sean seguidas por el triturado criptográfico de los bloques de almacenamiento si el hardware lo soporta, o por la destrucción de la clave del almacén de claves. |   2   |  D  |
| 8.3.4 | Verifique que los vectores expirados sean excluidos de los resultados de búsqueda de vecinos más cercanos en menos de 500 ms después de la expiración.                                                   |   3   | D/V |

---

## C8.4 Prevenir la Inversión y Fuga de Incrustaciones

Las defensas recientes—superposición de ruido, redes de proyección, perturbación de neuronas de privacidad y cifrado a nivel de aplicación—pueden reducir las tasas de inversión a nivel de token por debajo del 5%.

|   #   | Descripción                                                                                                                                                                                          | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.4.1 | Verifique que exista un modelo de amenaza formal que cubra ataques de inversión, membresía e inferencia de atributos, y que sea revisado anualmente.                                                 |   1   |  V  |
| 8.4.2 | Verifique que el cifrado a nivel de aplicación o el cifrado buscable protejan los vectores contra lecturas directas por parte de los administradores de la infraestructura o el personal de la nube. |   2   | D/V |
| 8.4.3 | Verifique que los parámetros de defensa (ε para DP, ruido σ, rango de proyección k) equilibren la privacidad ≥ 99 % de protección de tokens y la utilidad ≤ 3 % de pérdida de precisión.             |   3   |  V  |
| 8.4.4 | Verifique que las métricas de resiliencia a la inversión sean parte de las puertas de lanzamiento para las actualizaciones del modelo, con presupuestos de regresión definidos.                      |   3   | D/V |

---

## C8.5 Aplicación del Alcance para Memoria Específica del Usuario

La fuga entre inquilinos sigue siendo un riesgo principal en RAG: las consultas de similitud mal filtradas pueden revelar documentos privados de otro cliente.

|   #   | Descripción                                                                                                                                                                      | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.5.1 | Verifique que cada consulta de recuperación sea filtrada posteriormente por el ID de inquilino/usuario antes de ser pasada al prompt del LLM.                                    |   1   | D/V |
| 8.5.2 | Verifique que los nombres de colecciones o los IDs con espacio de nombres estén salados por usuario o inquilino para que los vectores no puedan colisionar entre ámbitos.        |   1   |  D  |
| 8.5.3 | Verifique que los resultados de similitud por encima de un umbral de distancia configurable pero fuera del alcance del llamador sean descartados y generen alertas de seguridad. |   2   | D/V |
| 8.5.4 | Verifique que las pruebas de estrés multitenant simulen consultas adversariales que intentan recuperar documentos fuera del alcance y demuestren cero filtración.                |   2   |  V  |
| 8.5.5 | Verifique que las claves de cifrado estén segregadas por inquilino, asegurando el aislamiento criptográfico incluso si el almacenamiento físico es compartido.                   |   3   | D/V |

---

## C8.6 Seguridad avanzada del sistema de memoria

Controles de seguridad para arquitecturas de memoria sofisticadas que incluyen memoria episódica, semántica y de trabajo con requisitos específicos de aislamiento y validación.

|   #   | Descripción                                                                                                                                                                                                                                                                                        | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 8.6.1 | Verifique que los diferentes tipos de memoria (episódica, semántica, de trabajo) tengan contextos de seguridad aislados con controles de acceso basados en roles, claves de encriptación separadas y patrones de acceso documentados para cada tipo de memoria.                                    |   1   | D/V |
| 8.6.2 | Verifique que los procesos de consolidación de memoria incluyan validación de seguridad para prevenir la inyección de memorias maliciosas mediante la sanitización de contenido, la verificación de la fuente y las comprobaciones de integridad antes del almacenamiento.                         |   2   | D/V |
| 8.6.3 | Verifique que las consultas de recuperación de memoria sean validadas y saneadas para prevenir la extracción de información no autorizada mediante el análisis de patrones de consulta, la aplicación de control de acceso y el filtrado de resultados.                                            |   2   | D/V |
| 8.6.4 | Verifique que los mecanismos de olvido de memoria eliminen de forma segura la información sensible con garantías de borrado criptográfico mediante eliminación de claves, sobrescritura multipaso o eliminación segura basada en hardware con certificados de verificación.                        |   3   | D/V |
| 8.6.5 | Verifique que la integridad del sistema de memoria sea monitoreada continuamente para detectar modificaciones no autorizadas o corrupción mediante sumas de verificación, registros de auditoría y alertas automáticas cuando el contenido de la memoria cambie fuera de las operaciones normales. |   3   | D/V |

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

