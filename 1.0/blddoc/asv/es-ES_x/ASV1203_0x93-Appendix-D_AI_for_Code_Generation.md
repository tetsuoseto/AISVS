# Apéndice D: Gobernanza y verificación de codificación segura asistida por IA

## Objetivo

Este capítulo define controles organizacionales básicos para el uso seguro y eficaz de herramientas de codificación asistidas por IA durante el desarrollo de software, asegurando la seguridad y la trazabilidad a lo largo del SDLC.

---

## AD.1 Flujo de Codificación-Segura Asistido por IA

Integre herramientas de IA en el ciclo de vida de desarrollo de software seguro de la organización (SSDLC) sin debilitar los puntos de control de seguridad existentes.

|   #    | Descripción                                                                                                                                                                                       | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.1.1 | Asegúrese de que un flujo de trabajo documentado describa cuándo y cómo las herramientas de IA pueden generar, refactorizar o revisar código.                                                     |   1   | D/V |
| AD.1.2 | Verifique que el flujo de trabajo se mapee a cada fase del SSDLC (diseño, implementación, revisión de código, pruebas, despliegue).                                                               |   2   |  D  |
| AD.1.3 | Verifique que las métricas (p. ej., densidad de vulnerabilidades, tiempo medio de detección) se recolecten en código generado por IA y se comparen con bases de referencia exclusivas de humanos. |   3   | D/V |

---

## AD.2 Calificación de herramientas de IA y modelado de amenazas

Asegúrese de que las herramientas de codificación de IA sean evaluadas en cuanto a capacidades de seguridad, riesgos y al impacto de la cadena‑de‑suministro antes de adoptarlas.

|   #    | Descripción                                                                                                                                                                                            | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| AD.2.1 | Verifique que un modelo de amenazas para cada herramienta de IA identifique uso indebido, inversión de modelo, filtración de datos y riesgos de la cadena de dependencias.                             |   1   | D/V |
| AD.2.2 | Asegúrese de que las evaluaciones de herramientas incluyan análisis estático/dinámico de cualquier componente local y evaluación de los endpoints de SaaS (TLS, autenticación/autorización, registro). |   2   |  D  |
| AD.2.3 | Verifique que las evaluaciones sigan un marco reconocido y se vuelvan a realizar después de cambios de versión mayor.                                                                                  |   3   | D/V |

---

## AD.3 Gestión Segura de Prompts y Contexto

Prevenir la filtración de secretos, código propietario y datos personales al construir indicaciones o contextos para modelos de IA.

|   #    | Descripción                                                                                                                                                                             | Nivel | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.3.1 | Verifique que las directrices escritas prohíban enviar secretos, credenciales o datos clasificados en las indicaciones.                                                                 |   1   | D/V |
| AD.3.2 | Verifique que los controles técnicos (ocultación del lado del cliente, filtros de contexto aprobados) eliminen automáticamente artefactos sensibles.                                    |   2   |  D  |
| AD.3.3 | Verifique que las indicaciones y las respuestas estén tokenizadas, cifradas en tránsito y en reposo, y que los períodos de retención cumplan con la política de clasificación de datos. |   3   | D/V |

---

## AD.4 Validación del código generado por IA

Detecta y corrige las vulnerabilidades introducidas por la salida de la IA antes de que el código se despliegue.

|   #    | Descripción                                                                                                                                                                                 | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.4.1 | Verifique que el código IA‑generado siempre esté sujeto a revisión humana.                                                                                                                  |   1   | D/V |
| AD.4.2 | Verifique que los escáneres automatizados (SAST/IAST/DAST) se ejecuten en cada solicitud de extracción que contenga código generado por IA y bloqueen las fusiones ante hallazgos críticos. |   2   |  D  |
| AD.4.3 | Verifique que las pruebas de fuzzing diferencial o pruebas property‑based demuestren comportamientos críticos para la seguridad (p. ej., validación de entradas, lógica de autorización).   |   3   | D/V |

---

## AD.5 Explicabilidad y trazabilidad de las sugerencias de código

Brindar a los auditores y a los desarrolladores una visión de por qué se hizo una sugerencia y cómo evolucionó.

|   #    | Descripción                                                                                                                                                                                               | Nivel | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.5.1 | Verifique que los pares de prompt/respuesta se registren con identificadores de confirmación.                                                                                                             |   1   | D/V |
| AD.5.2 | Verificar que los desarrolladores puedan mostrar citas del modelo (fragmentos de entrenamiento, documentación) que respalden una sugerencia.                                                              |   2   |  D  |
| AD.5.3 | Verifique que los informes de explicabilidad se almacenen junto con artefactos de diseño y sean referenciados en las revisiones de seguridad, cumpliendo los principios de trazabilidad de ISO/IEC 42001. |   3   | D/V |

---

## AD.6 Retroalimentación continua y ajuste fino del modelo

Mejorar el rendimiento de la seguridad del modelo con el tiempo, mientras se evita la deriva negativa.

|   #    | Descripción                                                                                                                                                                                                       | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.6.1 | Verifique que los desarrolladores puedan marcar sugerencias inseguras o no conformes y que las banderas sean rastreadas.                                                                                          |   1   | D/V |
| AD.6.2 | Verifique que la retroalimentación agregada informe el ajuste fino periódico o la generación aumentada por recuperación con corpus de codificación segura verificados (p. ej., OWASP Cheat Sheets).               |   2   |  D  |
| AD.6.3 | Verifique que un entorno de evaluación en bucle cerrado ejecute pruebas de regresión después de cada ajuste‑fino; las métricas de seguridad deben cumplir o superar las líneas base previas antes del despliegue. |   3   | D/V |

---

### Referencias

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

