# 10 Robustez ante ataques adversariales y defensa de la privacidad

## Objetivo de control

Asegúrese de que los modelos de IA permanezcan fiables, preserven la privacidad y sean resistentes al abuso cuando se enfrenten a ataques de evasión, inferencia, extracción o envenenamiento.

---

## 10.1 Alineación del modelo y seguridad

Prevenga salidas dañinas o que infrinjan políticas.

|   #    | Descripción                                                                                                                                                                | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.1.1 | Verifique que una suite de pruebas de alineación (prompts red-team, sondas de jailbreak, contenido prohibido) esté versionada y se ejecute en cada lanzamiento del modelo. |   1   | D/V |
| 10.1.2 | Verifique que se apliquen las salvaguardas de rechazo y de finalización segura.                                                                                            |   1   |  D  |
| 10.1.3 | Verifique que un evaluador automatizado mida la tasa de contenido dañino y marque las regresiones que superen un umbral establecido.                                       |   2   | D/V |
| 10.1.4 | Verifique que el entrenamiento de contrajailbreak esté documentado y sea reproducible.                                                                                     |   2   |  D  |
| 10.1.5 | Verifique que las pruebas formales de cumplimiento de políticas o la monitorización certificada cubran dominios críticos.                                                  |   3   |  V  |

---

## 10.2 Adversarial-Example Fortalecimiento frente a ejemplos adversariales

Aumentar la resiliencia frente a entradas manipuladas. El entrenamiento adversarial robusto y la puntuación en benchmarks son la mejor práctica actual.

|   #    | Descripción                                                                                                                                        | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.2.1 | Verifique que los repositorios de los proyectos incluyan configuraciones de entrenamiento adversarial con semillas reproducibles.                  |   1   |  D  |
| 10.2.2 | Verifique que la detección de ejemplos adversariales genera alertas de bloqueo en los pipelines de producción.                                     |   2   | D/V |
| 10.2.4 | Verifique que las pruebas de robustez certificada o certificados de límites basados en intervalos cubran al menos las clases críticas principales. |   3   |  V  |
| 10.2.5 | Verifique que las pruebas de regresión empleen ataques adaptativos para confirmar que no hay pérdida de robustez medible.                          |   3   |  V  |

---

## 10.3 Mitigación de la inferencia de membresía

Limite la capacidad de decidir si un registro formaba parte de los datos de entrenamiento. La privacidad diferencial y el enmascaramiento de puntuaciones de confianza siguen siendo las defensas conocidas más eficaces.

|   #    | Descripción                                                                                                                                  | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.3.1 | Verifique que la regularización de la entropía por consulta o el escalado por temperatura reduzcan las predicciones excesivamente confiadas. |   1   |  D  |
| 10.3.2 | Verifique que el entrenamiento emplee optimización con privacidad diferencial acotada por ε para conjuntos de datos sensibles.               |   2   |  D  |
| 10.3.3 | Verifique que las simulaciones de ataque (shadow-model o black-box) muestren la AUC de ataque ≤ 0.60 en datos de prueba no vistos.           |   2   |  V  |

---

## 10.4 Resistencia a la inversión de modelos

Prevenir la reconstrucción de atributos privados. Las revisiones recientes destacan el truncamiento de la salida y las garantías de privacidad diferencial como defensas prácticas.

|   #    | Descripción                                                                                                                                     | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.4.1 | Verifique que los atributos sensibles nunca se muestren directamente; cuando sea necesario, use intervalos o transformaciones unidireccionales. |   1   |  D  |
| 10.4.2 | Verifique que los límites de tasa de consultas limiten las consultas adaptativas repetidas del mismo sujeto.                                    |   1   | D/V |
| 10.4.3 | Verifique que el modelo esté entrenado con ruido que preserva la privacidad.                                                                    |   2   |  D  |

---

## 10.5 Defensa contra la extracción de modelos

Detectar y disuadir la clonación no autorizada. Se recomienda el uso de marcas de agua y el análisis de patrones de consultas.

|   #    | Descripción                                                                                                                                         | Nivel | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.5.1 | Verifique que las pasarelas de inferencia apliquen límites de tasa globales y por clave API, ajustados al umbral de memorización del modelo.        |   1   |  D  |
| 10.5.2 | Verifique que la entropía de consulta y la pluralidad de entradas alimenten un detector de extracción automatizado.                                 |   2   | D/V |
| 10.5.3 | Verifique que las marcas de agua frágiles o probabilísticas puedan demostrarse con p < 0.01 en ≤ 1 000 consultas contra un clon sospechado.         |   2   |  V  |
| 10.5.4 | Verifique que las claves de marca de agua y los conjuntos de disparadores se almacenen en un módulo de seguridad de hardware y se roten anualmente. |   3   |  D  |
| 10.5.5 | Verifique que los eventos de alerta de extracción incluyan consultas ofensivas y estén integrados con planes de respuesta ante incidentes.          |   3   |  V  |

---

## 10.6 Detección-de-datos-envenenados-en-tiempo-de-inferencia

Identificar y neutralizar entradas con puerta trasera o envenenadas.

|   #    | Descripción                                                                                                                                            | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 10.6.1 | Verifique que las entradas pasen por un detector de anomalías (p. ej., STRIP, puntuación de consistencia) antes de la inferencia del modelo.           |   1   |  D  |
| 10.6.2 | Verifique que los umbrales del detector estén ajustados en conjuntos de validación limpios y envenenados para lograr menos del 5% de falsos positivos. |   1   |  V  |
| 10.6.3 | Verifique que las entradas marcadas como envenenadas activen el bloqueo suave y los flujos de trabajo de revisión humana.                              |   2   |  D  |
| 10.6.4 | Verifique que los detectores sean sometidos a pruebas de estrés con ataques de puerta trasera adaptativos sin disparador.                              |   2   |  V  |
| 10.6.5 | Verifique que las métricas de eficacia de detección se registren y se reevaluen periódicamente con inteligencia de amenazas actualizada.               |   3   |  D  |

---

## 10.7 Adaptación dinámica de la política de seguridad

Actualizaciones de políticas de seguridad en tiempo real basadas en inteligencia de amenazas y análisis conductual.

|   #    | Descripción                                                                                                                                                                                    | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.7.1 | Verifique que las políticas de seguridad puedan actualizarse dinámicamente sin reiniciar el agente, manteniendo la integridad de la versión de la política.                                    |   1   | D/V |
| 10.7.2 | Verifique que las actualizaciones de la política estén firmadas criptográficamente por personal de seguridad autorizado y sean validadas antes de su aplicación.                               |   2   | D/V |
| 10.7.3 | Verifique que los cambios dinámicos de políticas se registren con registros de auditoría completos que incluyan la justificación, las cadenas de aprobación y los procedimientos de reversión. |   2   | D/V |
| 10.7.4 | Verifique que los mecanismos de seguridad adaptativos ajusten la sensibilidad de la detección de amenazas según el contexto de riesgo y los patrones de comportamiento.                        |   3   | D/V |
| 10.7.5 | Verifique que las decisiones de adaptación de políticas sean explicables e incluyan rastros de evidencia para la revisión por parte del equipo de seguridad.                                   |   3   | D/V |

---

## 10.8 Análisis de seguridad basado en reflexión

Validación de seguridad mediante la autorreflexión del agente y el análisis metacognitivo.

|   #    | Descripción                                                                                                                                                       | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.8.1 | Verifique que los mecanismos de reflexión de los agentes incluyan una autoevaluación centrada en la seguridad de las decisiones y acciones.                       |   1   | D/V |
| 10.8.2 | Verifique que las salidas de reflexión estén validadas para evitar la manipulación de los mecanismos de autoevaluación por entradas adversarias.                  |   2   | D/V |
| 10.8.3 | Verifique que el análisis de seguridad metacognitiva identifique sesgos potenciales, manipulaciones o compromisos en los procesos de razonamiento de los agentes. |   2   | D/V |
| 10.8.4 | Verifique que las advertencias de seguridad basadas en reflexión activen un monitoreo mejorado y posibles flujos de trabajo de intervención humana.               |   3   | D/V |
| 10.8.5 | Verificar que el aprendizaje continuo a partir de la retroalimentación de seguridad mejore la detección de amenazas sin deteriorar la funcionalidad legítima.     |   3   | D/V |

---

## 10.9 Evolución y Seguridad de la Auto-mejora

Controles de seguridad para sistemas basados en agentes capaces de auto-modificación y evolución.

|   #    | Descripción                                                                                                                                 | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.9.1 | Verifique que las capacidades de auto-modificación estén restringidas a las áreas seguras designadas con límites de verificación formal.    |   1   | D/V |
| 10.9.2 | Asegúrese de que las propuestas de evolución pasen por una evaluación de impacto de seguridad antes de su implementación.                   |   2   | D/V |
| 10.9.3 | Verifique que los mecanismos de auto-mejoramiento incluyan capacidades de reversión con verificación de integridad.                         |   2   | D/V |
| 10.9.4 | Verifique que la seguridad del metaaprendizaje impida la manipulación adversaria de los algoritmos de mejora.                               |   3   | D/V |
| 10.9.5 | Verifique que el auto-mejoramiento recursivo esté limitado por restricciones de seguridad formales con pruebas matemáticas de convergencia. |   3   | D/V |

---

### Referencias

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

