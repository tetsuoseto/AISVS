# C6 Seguridad de la cadena de suministro para modelos, marcos de trabajo y datos

## Objetivo de control

Los ataques de la cadena de suministro de IA explotan modelos, marcos o conjuntos de datos de terceros para incrustar puertas traseras, sesgos o código explotable. Estos controles proporcionan trazabilidad de extremo a extremo, gestión de vulnerabilidades y monitoreo para proteger todo el ciclo de vida del modelo.

---

## C6.1 Evaluación de modelos preentrenados y su procedencia

Evaluar y autenticar los orígenes, licencias y comportamientos ocultos de los modelos de terceros antes de cualquier ajuste fino o despliegue.

|   #   | Descripción                                                                                                                                                                       | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.1.1 | Verifique que cada artefacto de modelo de terceros incluya un registro de procedencia firmado que identifique el repositorio fuente y el hash de confirmación.                    |   1   | D/V |
| 6.1.2 | Verifique que los modelos sean escaneados en busca de capas maliciosas o disparadores de troyanos mediante herramientas automatizadas antes de la importación.                    |   1   | D/V |
| 6.1.3 | Verifique que los ajustes finos por transferencia pasen la evaluación adversarial para detectar comportamientos ocultos.                                                          |   2   |  D  |
| 6.1.4 | Verifique que las licencias del modelo, las etiquetas de control de exportación y las declaraciones de origen de los datos se registren en una entrada de ML‑BOM.                 |   2   |  V  |
| 6.1.5 | Verificar que los modelos de alto riesgo (pesos cargados públicamente, creadores no verificados) permanezcan en cuarentena hasta la revisión y aprobación por parte de un humano. |   3   | D/V |

---

## C6.2 Escaneo de frameworks y bibliotecas

Escanear continuamente marcos y bibliotecas de ML en busca de CVEs y código malicioso para mantener segura la pila de tiempo de ejecución.

|   #   | Descripción                                                                                                                                          | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.2.1 | Verifique que los pipelines de CI ejecuten escáneres de dependencias en marcos de IA y bibliotecas críticas.                                         |   1   | D/V |
| 6.2.2 | Verifique que las vulnerabilidades críticas (CVSS ≥ 7.0) bloqueen la promoción a imágenes de producción.                                             |   1   | D/V |
| 6.2.3 | Verifique que el análisis estático de código se ejecute en bibliotecas de ML ramificadas o vendorizadas.                                             |   2   |  D  |
| 6.2.4 | Verifique que las propuestas de actualización de marcos incluyan una evaluación de impacto de seguridad que haga referencia a feeds CVE públicos.    |   2   |  V  |
| 6.2.5 | Verifique que los sensores en tiempo de ejecución emitan alertas ante cargas inesperadas de bibliotecas dinámicas que se desvíen de la SBOM firmada. |   3   |  V  |

---

## C6.3 Fijación de dependencias y verificación

Anclar cada dependencia a sumas de verificación inmutables y reproducir las compilaciones para garantizar artefactos idénticos y libres de manipulación.

|   #   | Descripción                                                                                                                              | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.3.1 | Verifique que todos los gestores de paquetes hagan cumplir la fijación de versiones mediante archivos de bloqueo.                        |   1   | D/V |
| 6.3.2 | Verifique que se utilicen digests inmutables en lugar de etiquetas mutables en las referencias de contenedores.                          |   1   | D/V |
| 6.3.3 | Verifique que las verificaciones de construcción reproducible comparen hashes entre ejecuciones de CI para garantizar salidas idénticas. |   2   |  D  |
| 6.3.4 | Verifique que las atestaciones de compilación se almacenen durante 18 meses para la trazabilidad de auditoría.                           |   2   |  V  |
| 6.3.5 | Verifique que las dependencias caducadas disparen PRs automatizados para actualizar o bifurcar las versiones fijadas.                    |   3   |  D  |

---

## C6.4 Cumplimiento de Fuentes Confiables

Permitir descargas de artefactos solo desde fuentes verificadas criptográficamente-aprobadas por la organización y bloquear todo lo demás.

|   #   | Descripción                                                                                                                                          | Nivel | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.4.1 | Verifique que los pesos del modelo, los conjuntos de datos y los contenedores se descarguen solo desde dominios aprobados o registros internos.      |   1   | D/V |
| 6.4.2 | Verifique que las firmas de Sigstore/Cosign validen la identidad del publicador antes de que los artefactos se almacenen en caché localmente.        |   1   | D/V |
| 6.4.3 | Verifique que los proxies de salida bloqueen las descargas de artefactos no autenticados para hacer cumplir la política trusted‑source.              |   2   |  D  |
| 6.4.4 | Verifique que las listas de permitidos del repositorio sean revisadas trimestralmente con evidencia de justificación comercial para cada entrada.    |   2   |  V  |
| 6.4.5 | Verificar que los incumplimientos de políticas desencadenen la cuarentena de artefactos y la reversión de las ejecuciones de pipelines dependientes. |   3   |  V  |

---

## C6.5 Evaluación de riesgos de un conjunto de datos de terceros

Evaluar conjuntos de datos externos para envenenamiento, sesgo y cumplimiento legal, y monitorearlos a lo largo de su ciclo de vida.

|   #   | Descripción                                                                                                                                                                | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.5.1 | Verifique que los conjuntos de datos externos se sometan a una puntuación de riesgo de envenenamiento (p. ej., huellas digitales de datos, detección de valores atípicos). |   1   | D/V |
| 6.5.2 | Verifique que las métricas de sesgo (paridad demográfica, igualdad de oportunidades) se calculen antes de la aprobación del conjunto de datos.                             |   1   |  D  |
| 6.5.3 | Verifique que la proveniencia y los términos de la licencia de los conjuntos de datos estén capturados en las entradas de ML‑BOM.                                          |   2   |  V  |
| 6.5.4 | Verificar que el monitoreo periódico detecte deriva o corrupción en conjuntos de datos alojados.                                                                           |   2   |  V  |
| 6.5.5 | Verifique que el contenido no permitido (derechos de autor, información de identificación personal) se elimine mediante depuración automatizada antes del entrenamiento.   |   3   |  D  |

---

## C6.6 Monitoreo de ataques a la cadena de suministro

Detectar tempranamente amenazas de la cadena de suministro mediante feeds de CVE, análisis de registros de auditoría y simulaciones de red team.

|   #   | Descripción                                                                                                                                                                                  | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.6.1 | Verifique que los registros de auditoría de CI/CD se transmitan a las detecciones del SIEM para descargas de paquetes anómalas o pasos de compilación manipulados.                           |   1   |  V  |
| 6.6.2 | Verifique que los planes de respuesta a incidentes incluyan procedimientos de reversión para modelos o bibliotecas comprometidos.                                                            |   2   |  D  |
| 6.6.3 | Verifique que el enriquecimiento de inteligencia de amenazas etiquete indicadores específicos de aprendizaje automático (p. ej., IoCs de envenenamiento de modelos) en el triaje de alertas. |   3   |  V  |

---

## C6.7 ML‑BOM para artefactos del modelo

Genere y firme SBOMs detalladas específicas para ML (ML‑BOMs) para que los consumidores aguas abajo puedan verificar la integridad de los componentes en el momento del despliegue.

|   #   | Descripción                                                                                                                                               | Nivel | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 6.7.1 | Verifique que cada artefacto del modelo publique un ML‑BOM que liste conjuntos de datos, pesos, hiperparámetros y licencias.                              |   1   | D/V |
| 6.7.2 | Verifique que la generación de ML‑BOM y la firma de Cosign estén automatizadas en CI y sean requeridas para la fusión.                                    |   1   | D/V |
| 6.7.3 | Verifique que las comprobaciones de completitud de ML‑BOM hagan que la compilación falle si falta algún metadato del componente (hash, licencia).         |   2   |  D  |
| 6.7.4 | Verifique que los consumidores aguas abajo puedan consultar ML-BOMs a través de una API para validar los modelos importados en el momento del despliegue. |   2   |  V  |
| 6.7.5 | Verifique que los ML‑BOMs estén bajo control de versiones y se comparen para detectar modificaciones no autorizadas.                                      |   3   |  V  |

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

