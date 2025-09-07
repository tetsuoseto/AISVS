# C1 Gobernanza de Datos de Entrenamiento y Gestión de Sesgos

## Objetivo de Control

Los datos de entrenamiento deben ser obtenidos, manejados y mantenidos de una manera que preserve la procedencia, seguridad, calidad y equidad. Hacer esto cumple con las obligaciones legales y reduce los riesgos de sesgo, envenenamiento o violaciones de privacidad que puedan aparecer durante el entrenamiento y que podrían afectar todo el ciclo de vida de la IA.

---

## C1.1 Procedencia de los Datos de Entrenamiento

Mantenga un inventario verificable de todos los conjuntos de datos, acepte solo fuentes confiables y registre cada cambio para garantizar la auditabilidad.

|   #   | Descripción                                                                                                                                                                                                                        | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.1.1 | Verifique que se mantenga un inventario actualizado de cada fuente de datos de entrenamiento (origen, responsable/propietario, licencia, método de recopilación, restricciones de uso previstas e historial de procesamiento).     |   1   | D/V |
| 1.1.2 | Verifique que los procesos de datos de entrenamiento excluyan características, atributos o campos innecesarios (por ejemplo, metadatos no utilizados, información de identificación personal sensible, datos de prueba filtrados). |   1   | D/V |
| 1.1.3 | Verifique que todos los cambios en el conjunto de datos estén sujetos a un flujo de trabajo de aprobación registrado.                                                                                                              |   2   | D/V |
| 1.1.4 | Verifique que los conjuntos de datos o subconjuntos estén marcados con marcas de agua o huellas digitales cuando sea posible.                                                                                                      |   3   | D/V |

---

## C1.2 Seguridad e Integridad de los Datos de Entrenamiento

Restringir el acceso a los datos de entrenamiento, encriptarlos en reposo y en tránsito, y validar su integridad para prevenir la manipulación, el robo o el envenenamiento de datos.

|   #   | Descripción                                                                                                                                                                                                    | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.2.1 | Verifique que los controles de acceso protejan el almacenamiento de datos de entrenamiento y las canalizaciones.                                                                                               |   1   | D/V |
| 1.2.2 | Verifique que todo acceso a los datos de entrenamiento esté registrado, incluyendo usuario, hora y acción.                                                                                                     |   2   | D/V |
| 1.2.3 | Verifique que los conjuntos de datos de entrenamiento estén cifrados durante la transferencia y en reposo, utilizando algoritmos criptográficos estándar de la industria y prácticas de gestión de claves.     |   2   | D/V |
| 1.2.4 | Verifique que se utilicen hashes criptográficos o firmas digitales para garantizar la integridad de los datos durante el almacenamiento y la transferencia de datos de entrenamiento.                          |   2   | D/V |
| 1.2.5 | Verifique que se apliquen técnicas automatizadas de detección para proteger contra modificaciones no autorizadas o corrupción de los datos de entrenamiento.                                                   |   2   | D/V |
| 1.2.6 | Verifique que los datos de entrenamiento obsoletos se eliminen de forma segura o se anonimen.                                                                                                                  |   2   | D/V |
| 1.2.7 | Verifique que todas las versiones del conjunto de datos de entrenamiento estén identificadas de manera única, almacenadas de forma inmutable y sean auditables para apoyar la reversión y el análisis forense. |   3   | D/V |

---

## C1.3 Calidad, Integridad y Seguridad del Etiquetado de Datos de Entrenamiento

Proteger las etiquetas y requerir una revisión técnica para los datos críticos.

|   #   | Descripción                                                                                                                                                                                                                                          | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.3.1 | Verifique que se apliquen hashes criptográficos o firmas digitales a los artefactos de etiquetas para garantizar su integridad y autenticidad.                                                                                                       |   2   | D/V |
| 1.3.2 | Verifique que las interfaces y plataformas de etiquetado apliquen controles de acceso estrictos, mantengan registros de auditoría a prueba de manipulaciones de todas las actividades de etiquetado y protejan contra modificaciones no autorizadas. |   2   | D/V |
| 1.3.3 | Verifique que la información sensible en las etiquetas esté redactada, anonimizada o cifrada a nivel de campo de datos en reposo y en tránsito.                                                                                                      |   3   | D/V |

---

## C1.4 Calidad de los Datos de Entrenamiento y Garantía de Seguridad

Combine la validación automatizada, las verificaciones manuales al azar y la remediación registrada para garantizar la fiabilidad del conjunto de datos.

|   #   | Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.4.1 | Verifique que las pruebas automatizadas detecten errores de formato y valores nulos en cada ingestión o transformación de datos significativa.                                                                                                                                                                                                                                                                                                                                                                        |   1   |  D  |
| 1.4.2 | Verifique que las canalizaciones de entrenamiento y ajuste fino de LLM implementen detección de envenenamiento y validación de integridad de datos (por ejemplo, métodos estadísticos, detección de valores atípicos, análisis de embeddings) para identificar posibles ataques de envenenamiento (por ejemplo, cambio de etiqueta, inserción de disparadores de puerta trasera, comandos de intercambio de roles, ataques de instancias influyentes) o corrupción accidental de datos en los datos de entrenamiento. |   2   | D/V |
| 1.4.3 | Verifique que se implementen y ajusten defensas apropiadas, como el entrenamiento adversarial (utilizando ejemplos adversariales generados), la aumentación de datos con entradas perturbadas o técnicas de optimización robusta, para los modelos relevantes según la evaluación de riesgos.                                                                                                                                                                                                                         |   3   | D/V |
| 1.4.4 | Verifique que las etiquetas generadas automáticamente (por ejemplo, mediante LLMs o supervisión débil) estén sujetas a umbrales de confianza y verificaciones de consistencia para detectar etiquetas alucinadas, engañosas o de baja confianza.                                                                                                                                                                                                                                                                      |   2   | D/V |
| 1.4.5 | Verifique que las pruebas automatizadas detecten desviaciones de etiquetas en cada ingestión o transformación de datos significativa.                                                                                                                                                                                                                                                                                                                                                                                 |   3   |  D  |

---

## C1.5 Linaje y trazabilidad de datos

Realice un seguimiento del recorrido completo de cada punto de datos desde la fuente hasta la entrada del modelo para garantizar la auditoría y la respuesta a incidentes.

|   #   | Descripción                                                                                                                                                                                                                                                                                 | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.5.1 | Verifique que la genealogía de cada punto de datos, incluyendo todas las transformaciones, aumentos y fusiones, esté registrada y pueda ser reconstruida.                                                                                                                                   |   2   | D/V |
| 1.5.2 | Verifique que los registros de linaje sean inmutables, estén almacenados de forma segura y sean accesibles para auditorías.                                                                                                                                                                 |   2   | D/V |
| 1.5.3 | Verifique que el seguimiento de linaje cubra los datos sintéticos generados mediante técnicas generativas o de preservación de la privacidad y que todos los datos sintéticos estén claramente etiquetados y sean distinguibles de los datos reales a lo largo de todo el flujo de trabajo. |   2   | D/V |

---

## Referencias

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

