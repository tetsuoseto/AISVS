# C1 Gobernanza de Datos de Entrenamiento y Gestión de Sesgos

## Objetivo de control

Los datos de entrenamiento deben obtenerse, gestionarse y mantenerse de una manera que preserve la procedencia, la seguridad, la calidad y la equidad. Con ello se cumplen las obligaciones legales y se reducen los riesgos de sesgo, envenenamiento o violaciones de la privacidad que pueden surgir durante el entrenamiento y que podrían afectar al ciclo de vida completo de la IA.

---

## C1.1 Proveniencia de datos de entrenamiento

Mantenga un inventario verificable de todos los conjuntos de datos, acepte solo fuentes confiables y registre cada cambio para fines de auditoría.

|   #   | Descripción                                                                                                                                                                                                                         | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.1.1 | Verifique que se mantenga un inventario actualizado de cada fuente de datos de entrenamiento (origen, gestor/propietario, licencia, método de recopilación, restricciones de uso previstas y historial de procesamiento).           |   1   | D/V |
| 1.1.2 | Verifique que los procesos de datos de entrenamiento excluyan características, atributos o campos innecesarios (p. ej., metadatos no utilizados, información de identificación personal (PII) sensible, datos de prueba filtrados). |   1   | D/V |
| 1.1.3 | Verifique que todos los cambios en el conjunto de datos estén sujetos a un flujo de aprobación registrado.                                                                                                                          |   2   | D/V |
| 1.1.4 | Verifique que los conjuntos de datos o subconjuntos estén marcados con marca de agua o tengan huellas digitales cuando sea factible.                                                                                                |   3   | D/V |

---

## C1.2 Seguridad e integridad de los datos de entrenamiento

Restringir el acceso a los datos de entrenamiento, cifrarlos en reposo y en tránsito, y validar su integridad para evitar manipulaciones, robos o envenenamiento de datos.

|   #   | Descripción                                                                                                                                                                                                          | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.2.1 | Verifique que los controles de acceso protejan el almacenamiento de datos de entrenamiento y los pipelines.                                                                                                          |   1   | D/V |
| 1.2.2 | Verifique que todo acceso a los datos de entrenamiento quede registrado, incluyendo usuario, hora y acción.                                                                                                          |   2   | D/V |
| 1.2.3 | Verifique que los conjuntos de datos de entrenamiento estén cifrados en tránsito y en reposo, utilizando algoritmos criptográficos estándar de la industria y prácticas de gestión de claves.                        |   2   | D/V |
| 1.2.4 | Verifique que se utilicen hashes criptográficos o firmas digitales para garantizar la integridad de los datos durante el almacenamiento y la transferencia de datos de entrenamiento.                                |   2   | D/V |
| 1.2.5 | Verifique que las técnicas de detección automatizadas se apliquen para evitar modificaciones no autorizadas o la corrupción de los datos de entrenamiento.                                                           |   2   | D/V |
| 1.2.6 | Verifique que los datos de entrenamiento obsoletos sean purgados de forma segura o anonimizados.                                                                                                                     |   2   | D/V |
| 1.2.7 | Verifique que todas las versiones de los conjuntos de datos de entrenamiento estén identificadas de forma única, almacenadas de forma inmutable y sean auditables para respaldar la reversión y el análisis forense. |   3   | D/V |

---

## C1.3 Calidad, Integridad y Seguridad del Etiquetado de Datos de Entrenamiento

Proteja las etiquetas y exija revisión técnica para datos críticos.

|   #   | Descripción                                                                                                                                                                                                                                        | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.3.1 | Verifique que se apliquen hashes criptográficos o firmas digitales a artefactos de etiquetado para garantizar su integridad y autenticidad.                                                                                                        |   2   | D/V |
| 1.3.2 | Verifique que las interfaces y plataformas de etiquetado apliquen controles de acceso estrictos, mantengan registros de auditoría a prueba de manipulación de todas las actividades de etiquetado y protejan contra modificaciones no autorizadas. |   2   | D/V |
| 1.3.3 | Verifique que la información sensible en las etiquetas esté redactada, anonimizada o cifrada a nivel de campo de datos en reposo y en tránsito.                                                                                                    |   3   | D/V |

---

## C1.4 Calidad de los datos de entrenamiento y aseguramiento de la seguridad

Combine la validación automatizada, las verificaciones manuales puntuales y la remediación registrada para garantizar la confiabilidad del conjunto de datos.

|   #   | Descripción                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.4.1 | Verifique que las pruebas automatizadas detecten errores de formato y valores nulos en cada ingestión o transformación de datos significativa.                                                                                                                                                                                                                                                                                                                                                 |   1   |  D  |
| 1.4.2 | Verifique que los pipelines de entrenamiento y ajuste fino de LLM implementen detección de envenenamiento y validación de la integridad de los datos (p. ej., métodos estadísticos, detección de valores atípicos, análisis de embeddings) para identificar posibles ataques de envenenamiento (p. ej., inversión de etiquetas, inserción de disparadores de puerta trasera, comandos de cambio de rol, ataques de instancias influyentes) o corrupción inadvertida de datos de entrenamiento. |   2   | D/V |
| 1.4.3 | Verifique que se implementen y ajusten defensas apropiadas, como el entrenamiento adversarial (utilizando ejemplos adversariales generados), el aumento de datos con entradas perturbadas o técnicas de optimización robustas, para los modelos relevantes basándose en la evaluación de riesgos.                                                                                                                                                                                              |   3   | D/V |
| 1.4.4 | Verifique que las etiquetas generadas automáticamente (p. ej., mediante Modelos de Lenguaje Grandes (LLMs) o supervisión débil) estén sujetas a umbrales de confianza y verificaciones de consistencia para detectar etiquetas alucinadas, engañosas o de baja confianza.                                                                                                                                                                                                                      |   2   | D/V |
| 1.4.5 | Verifique que las pruebas automatizadas detecten sesgos de etiquetas en cada ingesta o en una transformación de datos significativa.                                                                                                                                                                                                                                                                                                                                                           |   3   |  D  |

---

## C1.5 Linaje de datos y trazabilidad

Rastrear el recorrido completo de cada punto de datos desde la fuente hasta la entrada del modelo para la auditoría y la respuesta a incidentes.

|   #   | Descripción                                                                                                                                                                                                                                                                                       | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 1.5.1 | Verificar que el linaje de cada punto de datos, incluidas todas las transformaciones, aumentos de datos y fusiones, esté registrado y pueda ser reconstruido.                                                                                                                                     |   2   | D/V |
| 1.5.2 | Verifique que los registros de linaje sean inmutables, estén almacenados de forma segura y sean accesibles para auditorías.                                                                                                                                                                       |   2   | D/V |
| 1.5.3 | Verifique que el seguimiento de linaje cubra los datos sintéticos generados mediante técnicas de preservación de la privacidad o técnicas generativas, y que todos los datos sintéticos estén claramente etiquetados y sean distinguibles de los datos reales a lo largo de toda la canalización. |   2   | D/V |

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

