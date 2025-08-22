# Apéndice D: Gobernanza y Verificación de Codificación Segura Asistida por IA

## Objetivo

Este capítulo define controles organizacionales básicos para el uso seguro y efectivo de herramientas de codificación asistida por IA durante el desarrollo de software, asegurando la seguridad y la trazabilidad en todo el SDLC.

---

## AD.1 Flujo de trabajo de codificación segura asistida por IA

Integrar herramientas de IA en el ciclo de vida de desarrollo de software seguro (SSDLC) de la organización sin debilitar las puertas de seguridad existentes.

|   #    | Descripción                                                                                                                                                                                              | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.1.1 | Verifique que un flujo de trabajo documentado describa cuándo y cómo las herramientas de IA pueden generar, refactorizar o revisar código.                                                               |   1   | D/V |
| AD.1.2 | Verifique que el flujo de trabajo corresponda a cada fase del SSDLC (diseño, implementación, revisión de código, pruebas, despliegue).                                                                   |   2   |  D  |
| AD.1.3 | Verifique que las métricas (por ejemplo, densidad de vulnerabilidades, tiempo medio para detectar) se recopilen sobre el código producido por IA y se comparen con las bases de referencia solo humanas. |   3   | D/V |

---

## Calificación de herramientas de IA AD.2 y modelado de amenazas

Asegúrese de que las herramientas de codificación de IA sean evaluadas en cuanto a capacidades de seguridad, riesgo e impacto en la cadena de suministro antes de su adopción.

|   #    | Descripción                                                                                                                                                                                        | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.2.1 | Verifique que un modelo de amenaza para cada herramienta de IA identifique el uso indebido, inversión de modelo, fuga de datos y riesgos de cadena de dependencias.                                |   1   | D/V |
| AD.2.2 | Verifique que las evaluaciones de la herramienta incluyan análisis estático/dinámico de cualquier componente local y evaluación de los endpoints SaaS (TLS, autenticación/autorización, registro). |   2   |  D  |
| AD.2.3 | Verifique que las evaluaciones sigan un marco reconocido y se realicen nuevamente después de cambios importantes de versión.                                                                       |   3   | D/V |

---

## AD.3 Gestión Segura de Instrucciones y Contexto

Prevenir la filtración de secretos, código propietario y datos personales al construir indicaciones o contextos para modelos de IA.

|   #    | Descripción                                                                                                                                                                                      | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| AD.3.1 | Verifique que las directrices escritas prohíban enviar secretos, credenciales o datos clasificados en las indicaciones.                                                                          |   1   | D/V |
| AD.3.2 | Verifique que los controles técnicos (redacción del lado del cliente, filtros de contexto aprobados) eliminen automáticamente los artefactos sensibles.                                          |   2   |  D  |
| AD.3.3 | Verifique que los prompts y las respuestas estén tokenizados, encriptados durante la transmisión y en reposo, y que los períodos de retención cumplan con la política de clasificación de datos. |   3   | D/V |

---

## AD.4 Validación del Código Generado por IA

Detectar y corregir vulnerabilidades introducidas por la salida de IA antes de que el código sea fusionado o desplegado.

|   #    | Descripción                                                                                                                                                                                                      | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.4.1 | Verifique que el código generado por IA siempre sea sometido a una revisión humana del código.                                                                                                                   |   1   | D/V |
| AD.4.2 | Verifique que los escáneres automatizados (SAST/IAST/DAST) se ejecuten en cada solicitud de incorporación de cambios que contenga código generado por IA y bloqueen las fusiones en caso de hallazgos críticos.  |   2   |  D  |
| AD.4.3 | Verifique que las pruebas de fuzzing diferencial o las pruebas basadas en propiedades demuestren comportamientos críticos para la seguridad (por ejemplo, la validación de entradas, la lógica de autorización). |   3   | D/V |

---

## AD.5 Explicabilidad y trazabilidad de las sugerencias de código

Proporcione a los auditores y desarrolladores una visión sobre por qué se hizo una sugerencia y cómo evolucionó.

|   #    | Descripción                                                                                                                                                                                                            | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.5.1 | Verifique que los pares de solicitud/respuesta se registren con los IDs de confirmación.                                                                                                                               |   1   | D/V |
| AD.5.2 | Verifique que los desarrolladores puedan mostrar citas del modelo (fragmentos de entrenamiento, documentación) que respalden una sugerencia.                                                                           |   2   |  D  |
| AD.5.3 | Verifique que los informes de explicabilidad se almacenen junto con los artefactos de diseño y se referencien en las revisiones de seguridad, cumpliendo con los principios de trazabilidad de la norma ISO/IEC 42001. |   3   | D/V |

---

## AD.6 Retroalimentación Continua y Ajuste Fino del Modelo

Mejorar el rendimiento de la seguridad del modelo con el tiempo mientras se previene la deriva negativa.

|   #    | Descripción                                                                                                                                                                                                           | Nivel | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| AD.6.1 | Verificar que los desarrolladores puedan señalar sugerencias inseguras o no conformes, y que dichas señales sean registradas.                                                                                         |   1   | D/V |
| AD.6.2 | Verifique que la retroalimentación agregada informe la afinación periódica o la generación aumentada por recuperación con corpora de codificación segura verificados (por ejemplo, OWASP Cheat Sheets).               |   2   |  D  |
| AD.6.3 | Verifique que un arnés de evaluación de circuito cerrado ejecute pruebas de regresión después de cada ajuste fino; las métricas de seguridad deben cumplir o superar las líneas base anteriores antes del despliegue. |   3   | D/V |

---

### Referencias

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

