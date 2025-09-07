# 11 Protección de la Privacidad y Gestión de Datos Personales

## Objetivo de Control

Mantenga rigurosas garantías de privacidad a lo largo de todo el ciclo de vida de la IA—recolección, entrenamiento, inferencia y respuesta a incidentes—de modo que los datos personales se procesen únicamente con consentimiento claro, ámbito mínimo necesario, eliminación demostrable y garantías formales de privacidad.

---

## 11.1 Anonimización y Minimización de Datos

|   #    | Descripción                                                                                                                                                               | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 11.1.1 | Verifique que los identificadores directos y cuasi-identificadores sean eliminados o codificados mediante hash.                                                           |   1   | D/V |
| 11.1.2 | Verifique que las auditorías automatizadas midan k-anonimato/l-diversidad y alerten cuando los umbrales caigan por debajo de la política.                                 |   2   | D/V |
| 11.1.3 | Verifique que los informes de importancia de características del modelo demuestren que no existe filtración de identificadores más allá de ε = 0.01 de información mutua. |   2   |  V  |
| 11.1.4 | Verifique que las pruebas formales o la certificación con datos sintéticos demuestren que el riesgo de reidentificación sea ≤ 0.05 incluso bajo ataques de enlace.        |   3   |  V  |

---

## 11.2 Derecho a ser olvidado y aplicación de la eliminación

|   #    | Descripción                                                                                                                                                                                                                                             | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 11.2.1 | Verifique que las solicitudes de eliminación de datos personales se propagan a los conjuntos de datos sin procesar, puntos de control, incrustaciones, registros y copias de seguridad dentro de los acuerdos de nivel de servicio de menos de 30 días. |   1   | D/V |
| 11.2.2 | Verifique que las rutinas de "desaprendizaje automático" reentrenen físicamente o aproximen la eliminación utilizando algoritmos certificados de desaprendizaje.                                                                                        |   2   |  D  |
| 11.2.3 | Verifique que la evaluación del modelo sombra demuestre que los registros olvidados influyen en menos del 1% de los resultados después del olvido.                                                                                                      |   2   |  V  |
| 11.2.4 | Verifique que los eventos de eliminación se registren de forma inmutable y sean auditables para los reguladores.                                                                                                                                        |   3   |  V  |

---

## 11.3 Salvaguardas de privacidad diferencial

|   #    | Descripción                                                                                                                                    | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 11.3.1 | Verifique que los paneles de control de contabilidad de pérdida de privacidad alerten cuando ε acumulativo exceda los umbrales de la política. |   2   | D/V |
| 11.3.2 | Verifique que las auditorías de privacidad de caja negra estimen ε̂ dentro del 10% del valor declarado.                                        |   2   |  V  |
| 11.3.3 | Verifique que las pruebas formales cubran todos los afinamientos y embeddings posteriores al entrenamiento.                                    |   3   |  V  |

---

## 11.4 Limitación de Propósito y Protección contra la Expansión del Alcance

|   #    | Descripción                                                                                                                                                     | Nivel | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 11.4.1 | Verifique que cada conjunto de datos y punto de control del modelo lleve una etiqueta de propósito legible por máquina alineada con el consentimiento original. |   1   |  D  |
| 11.4.2 | Verifique que los monitores de tiempo de ejecución detecten consultas inconsistentes con el propósito declarado y activen una negativa suave.                   |   1   | D/V |
| 11.4.3 | Verifique que las puertas de política como código bloqueen la redeployación de modelos a nuevos dominios sin una revisión de DPIA.                              |   3   |  D  |
| 11.4.4 | Verifique que las pruebas formales de trazabilidad muestren que todo el ciclo de vida de los datos personales permanece dentro del alcance consentido.          |   3   |  V  |

---

## 11.5 Gestión del Consentimiento y Seguimiento con Base Jurídica

|   #    | Descripción                                                                                                                                                   | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 11.5.1 | Verifique que una Plataforma de Gestión de Consentimiento (CMP) registre el estado de aceptación, el propósito y el período de retención por sujeto de datos. |   1   | D/V |
| 11.5.2 | Verifique que las API expongan tokens de consentimiento; los modelos deben validar el alcance del token antes de la inferencia.                               |   2   |  D  |
| 11.5.3 | Verifique que el consentimiento denegado o retirado detenga las cadenas de procesamiento dentro de las 24 horas.                                              |   2   | D/V |

---

## 11.6 Aprendizaje Federado con Controles de Privacidad

|   #    | Descripción                                                                                                                        | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 11.6.1 | Verifique que las actualizaciones del cliente utilicen la adición de ruido de privacidad diferencial local antes de la agregación. |   1   |  D  |
| 11.6.2 | Verifique que las métricas de entrenamiento sean privadamente diferenciales y nunca revelen la pérdida de un solo cliente.         |   2   | D/V |
| 11.6.3 | Verifique que la agregación resistente a envenenamiento (por ejemplo, Krum/Trimmed-Mean) esté habilitada.                          |   2   |  V  |
| 11.6.4 | Verifique que las pruebas formales demuestren un presupuesto total de ε con una pérdida de utilidad inferior a 5.                  |   3   |  V  |

---

### Referencias

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

