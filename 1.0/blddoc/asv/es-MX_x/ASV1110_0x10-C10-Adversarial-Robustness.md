# 10 Robustez adversarial y defensa de la privacidad

## Objetivo de Control

Asegurar que los modelos de IA permanezcan confiables, preserven la privacidad y sean resistentes al abuso cuando enfrentan ataques de evasión, inferencia, extracción o envenenamiento.

---

## 10.1 Alineación y Seguridad del Modelo

Protéjase contra salidas dañinas o que violen la política.

|   #    | Descripción                                                                                                                                                                                        | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.1.1 | Verifique que un conjunto de pruebas de alineación (prompts de red team, sondeos de jailbreak, contenido no permitido) esté bajo control de versiones y se ejecute en cada lanzamiento del modelo. |   1   | D/V |
| 10.1.2 | Verifique que se apliquen las restricciones de rechazo y de finalización segura.                                                                                                                   |   1   |  D  |
| 10.1.3 | Verifique que un evaluador automatizado mida la tasa de contenido perjudicial y señale regresiones que superen un umbral establecido.                                                              |   2   | D/V |
| 10.1.4 | Verifique que el entrenamiento contra jailbreak esté documentado y sea reproducible.                                                                                                               |   2   |  D  |
| 10.1.5 | Verifique que las pruebas formales de cumplimiento de políticas o la supervisión certificada cubran los dominios críticos.                                                                         |   3   |  V  |

---

## 10.2 Endurecimiento contra Ejemplos Adversariales

Aumentar la resiliencia frente a entradas manipuladas. El entrenamiento adversarial robusto y la puntuación de referencia son las mejores prácticas actuales.

|   #    | Descripción                                                                                                                                   | Nivel | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.2.1 | Verifique que los repositorios del proyecto incluyan configuraciones de entrenamiento adversarial con semillas reproducibles.                 |   1   |  D  |
| 10.2.2 | Verifique que la detección de ejemplos adversarios genere alertas de bloqueo en los pipelines de producción.                                  |   2   | D/V |
| 10.2.4 | Verifique que las pruebas de robustez certificada o los certificados de límites de intervalo cubran al menos las clases críticas principales. |   3   |  V  |
| 10.2.5 | Verifique que las pruebas de regresión utilicen ataques adaptativos para confirmar que no haya pérdida de robustez medible.                   |   3   |  V  |

---

## 10.3 Mitigación de la inferencia de membresía

Limitar la capacidad de decidir si un registro formaba parte de los datos de entrenamiento. La privacidad diferencial y el enmascaramiento de la puntuación de confianza siguen siendo las defensas conocidas más efectivas.

|   #    | Descripción                                                                                                                            | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.3.1 | Verifique que la regularización de entropía por consulta o el escalado de temperatura reduce las predicciones excesivamente confiadas. |   1   |  D  |
| 10.3.2 | Verifique que el entrenamiento utilice una optimización diferencialmente privada con límite ε para conjuntos de datos sensibles.       |   2   |  D  |
| 10.3.3 | Verificar que las simulaciones de ataque (modelo sombra o caja negra) muestren un AUC de ataque ≤ 0.60 en datos retenidos.             |   2   |  V  |

---

## 10.4 Resistencia a la inversión de modelo

Prevenir la reconstrucción de atributos privados. Encuestas recientes enfatizan la truncación de salida y las garantías de DP como defensas prácticas.

|   #    | Descripción                                                                                                                                           | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.4.1 | Verifique que los atributos sensibles nunca se muestren directamente; cuando sea necesario, utilice agrupaciones o transformaciones unidireccionales. |   1   |  D  |
| 10.4.2 | Verifique que los límites de tasa de consultas restrinjan las consultas adaptativas repetidas del mismo principal.                                    |   1   | D/V |
| 10.4.3 | Verifique que el modelo esté entrenado con ruido que preserva la privacidad.                                                                          |   2   |  D  |

---

## 10.5 Defensa contra la extracción de modelos

Detectar y disuadir la clonación no autorizada. Se recomiendan el marcaje digital y el análisis de patrones de consulta.

|   #    | Descripción                                                                                                                                                  | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 10.5.1 | Verifique que las puertas de enlace de inferencia apliquen límites de tasa tanto globales como por clave API ajustados al umbral de memorización del modelo. |   1   |  D  |
| 10.5.2 | Verifique que las estadísticas de entropía de consulta y pluralidad de entrada alimenten un detector de extracción automatizado.                             |   2   | D/V |
| 10.5.3 | Verifique que las marcas de agua frágiles o probabilísticas puedan demostrarse con p < 0.01 en ≤ 1 000 consultas contra un clon sospechoso.                  |   2   |  V  |
| 10.5.4 | Verifique que las claves de marca de agua y los conjuntos de activación se almacenen en un módulo de seguridad de hardware y se roten anualmente.            |   3   |  D  |
| 10.5.5 | Verifique que los eventos de alerta de extracción incluyan consultas infractoras y estén integrados con los protocolos de respuesta a incidentes.            |   3   |  V  |

---

## 10.6 Detección de datos envenenados en tiempo de inferencia

Identificar y neutralizar entradas con puertas traseras o envenenadas.

|   #    | Descripción                                                                                                                                          | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.6.1 | Verifique que las entradas pasen por un detector de anomalías (por ejemplo, STRIP, puntuación de consistencia) antes de la inferencia del modelo.    |   1   |  D  |
| 10.6.2 | Verifique que los umbrales del detector estén ajustados en conjuntos de validación limpios/envenenados para lograr menos del 5% de falsos positivos. |   1   |  V  |
| 10.6.3 | Verifique que las entradas marcadas como envenenadas desencadenen bloqueos suaves y flujos de trabajo de revisión humana.                            |   2   |  D  |
| 10.6.4 | Verifique que los detectores sean sometidos a pruebas de esfuerzo con ataques de puerta trasera adaptativos y sin disparadores.                      |   2   |  V  |
| 10.6.5 | Verifique que las métricas de eficacia de detección se registren y se reevalúen periódicamente con información actualizada sobre amenazas.           |   3   |  D  |

---

## 10.7 Adaptación Dinámica de Políticas de Seguridad

Actualizaciones en tiempo real de políticas de seguridad basadas en inteligencia de amenazas y análisis de comportamiento.

|   #    | Descripción                                                                                                                                                            | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.7.1 | Verifique que las políticas de seguridad puedan actualizarse dinámicamente sin reiniciar el agente y manteniendo la integridad de la versión de la política.           |   1   | D/V |
| 10.7.2 | Verifique que las actualizaciones de políticas estén firmadas criptográficamente por el personal de seguridad autorizado y validadas antes de su aplicación.           |   2   | D/V |
| 10.7.3 | Verifique que los cambios de política dinámicos se registren con auditorías completas que incluyan justificación, cadenas de aprobación y procedimientos de reversión. |   2   | D/V |
| 10.7.4 | Verifique que los mecanismos de seguridad adaptativa ajusten la sensibilidad de detección de amenazas según el contexto de riesgo y los patrones de comportamiento.    |   3   | D/V |
| 10.7.5 | Verifique que las decisiones de adaptación de políticas sean explicables e incluyan rastros de evidencia para la revisión del equipo de seguridad.                     |   3   | D/V |

---

## 10.8 Análisis de Seguridad Basado en Reflexión

Validación de seguridad mediante autorreflexión del agente y análisis metacognitivo.

|   #    | Descripción                                                                                                                                                 | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.8.1 | Verifique que los mecanismos de reflexión del agente incluyan una autoevaluación enfocada en la seguridad de las decisiones y acciones.                     |   1   | D/V |
| 10.8.2 | Verifique que las salidas de reflexión sean validadas para prevenir la manipulación de los mecanismos de autoevaluación por entradas adversas.              |   2   | D/V |
| 10.8.3 | Verifique que el análisis de seguridad meta-cognitivo identifique posibles sesgos, manipulaciones o compromisos en los procesos de razonamiento del agente. |   2   | D/V |
| 10.8.4 | Verifique que las advertencias de seguridad basadas en reflexión activen la supervisión mejorada y los posibles flujos de trabajo de intervención humana.   |   3   | D/V |
| 10.8.5 | Verifique que el aprendizaje continuo a partir de reflexiones de seguridad mejora la detección de amenazas sin degradar la funcionalidad legítima.          |   3   | D/V |

---

## 10.9 Seguridad en Evolución y Auto-mejora

Controles de seguridad para sistemas agentes capaces de auto-modificación y evolución.

|   #    | Descripción                                                                                                                                 | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 10.9.1 | Verifique que las capacidades de auto-modificación estén restringidas a áreas designadas como seguras con límites formales de verificación. |   1   | D/V |
| 10.9.2 | Verifique que las propuestas de evolución se sometan a una evaluación de impacto en la seguridad antes de su implementación.                |   2   | D/V |
| 10.9.3 | Verifique que los mecanismos de auto-mejora incluyan capacidades de reversión con verificación de integridad.                               |   2   | D/V |
| 10.9.4 | Verifique que la seguridad de meta-aprendizaje previene la manipulación adversaria de los algoritmos de mejora.                             |   3   | D/V |
| 10.9.5 | Verificar que la auto-mejora recursiva esté limitada por restricciones formales de seguridad con pruebas matemáticas de convergencia.       |   3   | D/V |

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

