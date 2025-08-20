# C13 Supervisión Humana, Responsabilidad y Gobernanza

## Objetivo de Control

Este capítulo proporciona requisitos para mantener la supervisión humana y cadenas claras de responsabilidad en los sistemas de IA, garantizando explicabilidad, transparencia y gestión ética a lo largo del ciclo de vida de la IA.

---

## C13.1 Mecanismos de Interruptor de Emergencia y Anulación

Proporcione rutas de apagado o reversión cuando se observe un comportamiento inseguro del sistema de IA.

|   #    | Descripción                                                                                                                           | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 13.1.1 | Verifique que exista un mecanismo manual de interrupción para detener inmediatamente la inferencia y los resultados del modelo de IA. |   1   | D/V |
| 13.1.2 | Verifique que los controles de anulación sean accesibles únicamente al personal autorizado.                                           |   1   |  D  |
| 13.1.3 | Verifique que los procedimientos de reversión puedan restaurar versiones anteriores del modelo o funciones en modo seguro.            |   3   | D/V |
| 13.1.4 | Verifique que los mecanismos de anulación se prueben regularmente.                                                                    |   3   |  V  |

---

## C13.2 Puntos de Control de Decisión con Intervención Humana

Requerir aprobaciones humanas cuando las apuestas superen los umbrales de riesgo predefinidos.

|   #    | Descripción                                                                                                                                                         | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 13.2.1 | Verifique que las decisiones de IA de alto riesgo requieran aprobación humana explícita antes de su ejecución.                                                      |   1   | D/V |
| 13.2.2 | Verifique que los umbrales de riesgo estén claramente definidos y que activen automáticamente los flujos de trabajo de revisión humana.                             |   1   |  D  |
| 13.2.3 | Verifique que las decisiones sensibles al tiempo tengan procedimientos de respaldo cuando no se pueda obtener la aprobación humana dentro de los plazos requeridos. |   2   |  D  |
| 13.2.4 | Verifique que los procedimientos de escalamiento definan niveles claros de autoridad para diferentes tipos de decisiones o categorías de riesgo, si corresponde.    |   3   | D/V |

---

## C13.3 Cadena de Responsabilidad y Auditabilidad

Registrar las acciones del operador y las decisiones del modelo.

|   #    | Descripción                                                                                                                                                                         | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 13.3.1 | Verifique que todas las decisiones del sistema de IA y las intervenciones humanas estén registradas con marcas de tiempo, identidades de usuario y la justificación de la decisión. |   1   | D/V |
| 13.3.2 | Verifique que los registros de auditoría no puedan ser manipulados e incluyan mecanismos de verificación de integridad.                                                             |   2   |  D  |

---

## C13.4 Técnicas de IA Explicable

Importancia de características superficiales, contra-factuales y explicaciones locales.

|   #    | Descripción                                                                                                                                                               | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 13.4.1 | Verifique que los sistemas de IA proporcionen explicaciones básicas de sus decisiones en un formato comprensible para los humanos.                                        |   1   | D/V |
| 13.4.2 | Verifique que la calidad de la explicación esté validada mediante estudios de evaluación humana y métricas.                                                               |   2   |  V  |
| 13.4.3 | Verifique que las puntuaciones de importancia de características o los métodos de atribución (SHAP, LIME, etc.) estén disponibles para decisiones críticas.               |   3   | D/V |
| 13.4.4 | Verifique que las explicaciones contrafactuales muestren cómo se podrían modificar las entradas para cambiar los resultados, si es aplicable al caso de uso y al dominio. |   3   |  V  |

---

## C13.5 Tarjetas de Modelo y Divulgaciones de Uso

Mantener tarjetas de modelo para el uso previsto, métricas de rendimiento y consideraciones éticas.

|   #    | Descripción                                                                                                                                                                                                                                      | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 13.5.1 | Verifique que las tarjetas de modelo documenten los casos de uso previstos, las limitaciones y los modos de fallo conocidos.                                                                                                                     |   1   |  D  |
| 13.5.2 | Verifique que se divulguen las métricas de rendimiento en los diferentes casos de uso aplicables.                                                                                                                                                |   1   | D/V |
| 13.5.3 | Verifique que las consideraciones éticas, evaluaciones de sesgos, evaluaciones de justicia, características de los datos de entrenamiento y limitaciones conocidas de los datos de entrenamiento estén documentadas y actualizadas regularmente. |   2   |  D  |
| 13.5.4 | Verifique que las tarjetas de modelo estén bajo control de versiones y se mantengan durante todo el ciclo de vida del modelo con seguimiento de cambios.                                                                                         |   2   | D/V |

---

## C13.6 Cuantificación de la Incertidumbre

Propagar las puntuaciones de confianza o las medidas de entropía en las respuestas.

|   #    | Descripción                                                                                                             | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 13.6.1 | Verifique que los sistemas de IA proporcionen puntuaciones de confianza o medidas de incertidumbre con sus salidas.     |   1   |  D  |
| 13.6.2 | Verifique que los umbrales de incertidumbre activen una revisión humana adicional o vías de decisión alternativas.      |   2   | D/V |
| 13.6.3 | Verifique que los métodos de cuantificación de incertidumbre estén calibrados y validados con datos de referencia.      |   2   |  V  |
| 13.6.4 | Verifique que la propagación de incertidumbre se mantenga a lo largo de los flujos de trabajo de IA de múltiples pasos. |   3   | D/V |

---

## C13.7 Informes de Transparencia para Usuarios

Proporcionar divulgaciones periódicas sobre incidentes, desviaciones y uso de datos.

|   #    | Descripción                                                                                                                                              | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 13.7.1 | Verifique que las políticas de uso de datos y las prácticas de gestión del consentimiento del usuario se comuniquen claramente a las partes interesadas. |   1   | D/V |
| 13.7.2 | Verificar que se realicen evaluaciones de impacto de IA y que los resultados se incluyan en los informes.                                                |   2   | D/V |
| 13.7.3 | Verifique que los informes de transparencia publicados regularmente revelen incidentes de IA y métricas operativas con un detalle razonable.             |   2   | D/V |

### Referencias

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

