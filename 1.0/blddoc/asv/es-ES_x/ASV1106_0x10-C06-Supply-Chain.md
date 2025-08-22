# C6 Seguridad en la Cadena de Suministro para Modelos, Frameworks y Datos

## Objetivo de Control

Los ataques a la cadena de suministro de IA explotan modelos, frameworks o conjuntos de datos de terceros para insertar puertas traseras, sesgos o código explotable. Estos controles proporcionan un control completo de la procedencia, gestión de vulnerabilidades y monitoreo para proteger todo el ciclo de vida del modelo.

---

## C6.1 Verificación y Procedencia del Modelo Preentrenado

Evaluar y autenticar los orígenes, licencias y comportamientos ocultos de modelos de terceros antes de cualquier ajuste fino o despliegue.

|   #   | Descripción                                                                                                                                                            | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.1.1 | Verifique que cada artefacto de modelo de terceros incluya un registro de procedencia firmado que identifique el repositorio de origen y el hash de la confirmación.   |   1   | D/V |
| 6.1.2 | Verifique que los modelos sean escaneados en busca de capas maliciosas o disparadores de troyanos utilizando herramientas automatizadas antes de la importación.       |   1   | D/V |
| 6.1.3 | Verifique que el ajuste fino de transferencia de aprendizaje supere la evaluación adversarial para detectar comportamientos ocultos.                                   |   2   |  D  |
| 6.1.4 | Verifique que las licencias del modelo, las etiquetas de control de exportación y las declaraciones de origen de los datos estén registradas en una entrada de ML‑BOM. |   2   |  V  |
| 6.1.5 | Verifique que los modelos de alto riesgo (pesos subidos públicamente, creadores no verificados) permanezcan en cuarentena hasta la revisión y aprobación humana.       |   3   | D/V |

---

## C6.2 Escaneo de Framework y Bibliotecas

Escanee continuamente los frameworks y bibliotecas de ML en busca de CVE y código malicioso para mantener segura la pila de ejecución.

|   #   | Descripción                                                                                                                                                | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.2.1 | Verifique que las canalizaciones de CI ejecuten escáneres de dependencias en los frameworks de IA y las bibliotecas críticas.                              |   1   | D/V |
| 6.2.2 | Verifique que las vulnerabilidades críticas (CVSS ≥ 7.0) bloqueen la promoción a imágenes de producción.                                                   |   1   | D/V |
| 6.2.3 | Verifique que el análisis estático de código se ejecute en las bibliotecas de ML bifurcadas o incluidas.                                                   |   2   |  D  |
| 6.2.4 | Verifique que las propuestas de actualización del framework incluyan una evaluación de impacto de seguridad que haga referencia a fuentes públicas de CVE. |   2   |  V  |
| 6.2.5 | Verifique que los sensores en tiempo de ejecución alerten sobre cargas inesperadas de bibliotecas dinámicas que se desvíen del SBOM firmado.               |   3   |  V  |

---

## C6.3 Fijación y Verificación de Dependencias

Fije cada dependencia a sumas de verificación inmutables y reproduzca las compilaciones para garantizar artefactos idénticos y libres de manipulación.

|   #   | Descripción                                                                                                                                 | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.3.1 | Verifique que todos los gestores de paquetes apliquen el bloqueo de versiones mediante archivos de bloqueo.                                 |   1   | D/V |
| 6.3.2 | Verifique que se utilicen resúmenes inmutables en lugar de etiquetas mutables en las referencias de contenedores.                           |   1   | D/V |
| 6.3.3 | Verifique que las comprobaciones de compilación reproducible comparen los hashes entre ejecuciones de CI para garantizar salidas idénticas. |   2   |  D  |
| 6.3.4 | Verifique que las atestaciones de compilación se almacenen durante 18 meses para la trazabilidad de auditoría.                              |   2   |  V  |
| 6.3.5 | Verifique que las dependencias vencidas activen solicitudes de extracción automatizadas para actualizar o bifurcar las versiones fijadas.   |   3   |  D  |

---

## C6.4 Aplicación de Fuente Confiable

Permitir descargas de artefactos solo desde fuentes verificadas criptográficamente y aprobadas por la organización, y bloquear todo lo demás.

|   #   | Descripción                                                                                                                                             | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.4.1 | Verifique que los pesos del modelo, los conjuntos de datos y los contenedores se descarguen únicamente de dominios aprobados o registros internos.      |   1   | D/V |
| 6.4.2 | Verifique que las firmas de Sigstore/Cosign validen la identidad del editor antes de que los artefactos se almacenen en caché localmente.               |   1   | D/V |
| 6.4.3 | Verifique que los proxies de salida bloqueen las descargas de artefactos no autenticadas para hacer cumplir la política de fuente confiable.            |   2   |  D  |
| 6.4.4 | Verifique que las listas de permitidos del repositorio se revisen trimestralmente con evidencia de justificación comercial para cada entrada.           |   2   |  V  |
| 6.4.5 | Verifique que las violaciones de la política desencadenen el aislamiento de los artefactos y la reversión de las ejecuciones dependientes del pipeline. |   3   |  V  |

---

## C6.5 Evaluación de Riesgos de Conjuntos de Datos de Terceros

Evalúe los conjuntos de datos externos para detectar envenenamiento, sesgo y cumplimiento legal, y monitoree su ciclo de vida completo.

|   #   | Descripción                                                                                                                                                                     | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.5.1 | Verifique que los conjuntos de datos externos se sometan a una puntuación de riesgo de envenenamiento (por ejemplo, huellas digitales de datos, detección de valores atípicos). |   1   | D/V |
| 6.5.2 | Verifique que las métricas de sesgo (paridad demográfica, igualdad de oportunidades) se calculen antes de la aprobación del conjunto de datos.                                  |   1   |  D  |
| 6.5.3 | Verifique que el origen y los términos de licencia de los conjuntos de datos estén capturados en las entradas de ML‑BOM.                                                        |   2   |  V  |
| 6.5.4 | Verifique que la monitorización periódica detecte desviaciones o corrupciones en los conjuntos de datos alojados.                                                               |   2   |  V  |
| 6.5.5 | Verifique que el contenido no permitido (derechos de autor, información personal identificable) sea eliminado mediante un proceso automatizado antes del entrenamiento.         |   3   |  D  |

---

## C6.6 Monitoreo de Ataques en la Cadena de Suministro

Detecte amenazas en la cadena de suministro temprano a través de fuentes CVE, análisis de registros de auditoría y simulaciones de equipos rojos.

|   #   | Descripción                                                                                                                                                                                | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 6.6.1 | Verifique que los registros de auditoría de CI/CD se transmitan al SIEM para detectar extracciones de paquetes anómalas o pasos de compilación manipulados.                                |   1   |  V  |
| 6.6.2 | Verifique que los playbooks de respuesta a incidentes incluyan procedimientos de reversión para modelos o bibliotecas comprometidos.                                                       |   2   |  D  |
| 6.6.3 | Verifique que las etiquetas de enriquecimiento de inteligencia de amenazas marquen indicadores específicos de ML (por ejemplo, IoCs de envenenamiento de modelos) en el triaje de alertas. |   3   |  V  |

---

## C6.7 ML‑BOM para Artefactos de Modelos

Genere y firme SBOMs detallados específicos para ML (ML‑BOMs) para que los consumidores posteriores puedan verificar la integridad de los componentes en el momento del despliegue.

|   #   | Descripción                                                                                                                                              | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.7.1 | Verifique que cada artefacto de modelo publique un ML-BOM que liste conjuntos de datos, pesos, hiperparámetros y licencias.                              |   1   | D/V |
| 6.7.2 | Verifique que la generación de ML-BOM y la firma con Cosign estén automatizadas en CI y sean requeridas para la fusión.                                  |   1   | D/V |
| 6.7.3 | Verifique que las comprobaciones de integridad del ML-BOM fallen la compilación si falta algún metadato del componente (hash, licencia).                 |   2   |  D  |
| 6.7.4 | Verificar que los consumidores aguas abajo puedan consultar ML-BOMs a través de la API para validar los modelos importados en el momento del despliegue. |   2   |  V  |
| 6.7.5 | Verifique que los ML‑BOMs estén controlados por versión y comparados para detectar modificaciones no autorizadas.                                        |   3   |  V  |

---

## Referencias

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

