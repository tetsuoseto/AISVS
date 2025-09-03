# C4 Seguridad de Infraestructura, Configuración y Despliegue

## Objetivo de control

La infraestructura de IA debe endurecerse frente a la escalada de privilegios, la manipulación de la cadena de suministro y el movimiento lateral mediante una configuración segura, aislamiento en tiempo de ejecución, pipelines de despliegue confiables y un monitoreo integral. Solo los componentes de infraestructura autorizados y validados, y sus configuraciones, llegan a producción a través de procesos controlados que mantienen la seguridad, la integridad y la auditabilidad.

Objetivo de seguridad central: Solo componentes de infraestructura firmados criptográficamente y escaneados en busca de vulnerabilidades llegan a producción a través de pipelines de validación automatizados que hacen cumplir las políticas de seguridad y mantienen registros de auditoría inmutables.

---

## C4.1 Aislamiento del entorno de ejecución

Prevenir escapes de contenedores y la escalada de privilegios mediante primitivas de aislamiento a nivel del kernel y controles de acceso obligatorios.

|   #   | Descripción                                                                                                                                                                                                                                                                   | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.1.1 | Verifique que todos los contenedores de IA descarten todas las capacidades de Linux, excepto CAP_SETUID, CAP_SETGID y las capacidades explícitamente requeridas documentadas en las bases de seguridad.                                                                       |   1   | D/V |
| 4.1.2 | Verifique que los perfiles seccomp bloqueen todas las llamadas al sistema, excepto aquellas que figuran en listas de permitidos preaprobadas, y que ante violaciones el contenedor se termine y se generen alertas de seguridad.                                              |   1   | D/V |
| 4.1.3 | Verifique que las cargas de trabajo de IA se ejecuten con sistemas de archivos raíz de solo lectura, tmpfs para datos temporales y volúmenes con nombre para datos persistentes, con opciones de montaje noexec aplicadas.                                                    |   2   | D/V |
| 4.1.4 | Verifique que la monitorización en tiempo de ejecución basada en eBPF (Falco, Tetragon o equivalente) detecte intentos de escalamiento de privilegios y finalice automáticamente los procesos infractores dentro de los plazos de respuesta establecidos por la organización. |   2   | D/V |
| 4.1.5 | Verifique que las cargas de trabajo de IA de alto riesgo se ejecuten en entornos aislados por hardware (Intel TXT, AMD SVM o nodos bare-metal dedicados) con verificación de atestación.                                                                                      |   3   | D/V |

---

## C4.2 Pipelines de Construcción y Despliegue Seguros

Garantizar la integridad criptográfica y la seguridad de la cadena de suministro mediante compilaciones reproducibles y artefactos firmados.

|   #   | Descripción                                                                                                                                                                                                              | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 4.2.1 | Verifique que la infraestructura como código (IaC) se escanee con herramientas (tfsec, Checkov o Terrascan) en cada confirmación, bloqueando fusiones con hallazgos de severidad CRÍTICA o ALTA.                         |   1   | D/V |
| 4.2.2 | Verificar que las compilaciones de contenedores sean reproducibles con hashes SHA256 idénticos entre compilaciones y generar atestaciones de procedencia de Nivel 3 de SLSA firmadas con Sigstore.                       |   1   | D/V |
| 4.2.3 | Verifique que las imágenes de contenedor incluyan SBOMs de CycloneDX o SPDX y estén firmadas con Cosign antes de empujar al registro, y que las imágenes no firmadas sean rechazadas durante el despliegue.              |   2   | D/V |
| 4.2.4 | Verifique que los pipelines de CI/CD utilicen tokens OIDC de HashiCorp Vault, AWS IAM Roles o Azure Managed Identity, con períodos de validez que no excedan los límites de la política de seguridad de la organización. |   2   | D/V |
| 4.2.5 | Verifique que las firmas de Cosign y la proveniencia SLSA se validen durante el proceso de implementación antes de la ejecución del contenedor y que los errores de verificación hagan que la implementación falle.      |   2   | D/V |
| 4.2.6 | Verifique que los entornos de compilación se ejecuten en contenedores efímeros o máquinas virtuales sin almacenamiento persistente y con aislamiento de red respecto a las VPC de producción.                            |   2   | D/V |

---

## C4.3 Seguridad de la red y control de acceso

Implementar redes de confianza cero con políticas de denegación por defecto y comunicaciones cifradas.

|   #   | Descripción                                                                                                                                                                                                                    | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 4.3.1 | Verifique que las Políticas de Red de Kubernetes o cualquier equivalente implementen una denegación predeterminada de ingreso y egreso con reglas explícitas que permitan los puertos requeridos (443, 8080, etc.).            |   1   | D/V |
| 4.3.2 | Verifique que SSH (port 22), RDP (port 3389), y puntos finales de metadatos en la nube (169.254.169.254) estén bloqueados o requieran autenticación basada en certificados.                                                    |   1   | D/V |
| 4.3.3 | Verifique que el tráfico saliente se filtre a través de proxies HTTP/HTTPS (Squid, Istio o pasarelas NAT en la nube) con listas blancas de dominios y que las solicitudes bloqueadas queden registradas.                       |   2   | D/V |
| 4.3.4 | Verifique que la comunicación entre servicios utilice TLS mutuo con certificados rotados de acuerdo con la política organizacional y que la validación de certificados esté aplicada (sin banderas de omitir la verificación). |   2   | D/V |
| 4.3.5 | Verifique que la infraestructura de IA opere en VPCs/VNets dedicadas, sin acceso directo a Internet, y que se comunique únicamente a través de pasarelas NAT o hosts de bastión.                                               |   2   | D/V |

---

## C4.4 Secretos y Gestión de Claves Criptográficas

Proteja las credenciales mediante almacenamiento respaldado por hardware y rotación automatizada con acceso de confianza cero.

|   #   | Descripción                                                                                                                                                                                                                            | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.4.1 | Verifique que los secretos estén almacenados en HashiCorp Vault, AWS Secrets Manager, Azure Key Vault o Google Secret Manager con cifrado en reposo usando AES-256.                                                                    |   1   | D/V |
| 4.4.2 | Verifique que las claves criptográficas se generen en HSMs de Nivel 2 de FIPS 140-2 (AWS CloudHSM, Azure Dedicated HSM) con rotación de claves de acuerdo con la política criptográfica organizacional.                                |   1   | D/V |
| 4.4.3 | Verifique que la rotación de secretos esté automatizada, con despliegue sin tiempo de inactividad y rotación inmediata desencadenada por cambios de personal o incidentes de seguridad.                                                |   2   | D/V |
| 4.4.4 | Verifique que las imágenes de contenedor se escaneen con herramientas (GitLeaks, TruffleHog o detect-secrets) para bloquear las compilaciones que contengan claves API, contraseñas o certificados.                                    |   2   | D/V |
| 4.4.5 | Verifique que el acceso a secretos de producción requiera autenticación multifactor con tokens de hardware (YubiKey, FIDO2) y que quede registrado en registros de auditoría inmutables con identidades de usuario y marcas de tiempo. |   2   | D/V |
| 4.4.6 | Verifique que los secretos se inyecten mediante secretos de Kubernetes, volúmenes montados o contenedores init y asegúrese de que los secretos nunca estén incrustados en variables de entorno o imágenes.                             |   2   | D/V |

---

## C4.5 Carga de trabajo de IA: Aislamiento y Validación

Aísla modelos de IA no confiables en entornos sandbox seguros con un análisis conductual integral.

|   #   | Descripción                                                                                                                                                                                                                   | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.5.1 | Verifique que los modelos de IA externos se ejecuten en gVisor, microVMs (como Firecracker, CrossVM), o contenedores de Docker con las banderas --security-opt=no-new-privileges y --read-only.                               |   1   | D/V |
| 4.5.2 | Verifique que los entornos sandbox no tengan conectividad de red (--network=none) o que solo haya acceso a localhost, con todas las solicitudes externas bloqueadas por reglas de iptables.                                   |   1   | D/V |
| 4.5.3 | Verifique que la validación del modelo de IA incluya pruebas automatizadas del equipo rojo con cobertura de pruebas definida por la organización y análisis conductual para la detección de puertas traseras.                 |   2   | D/V |
| 4.5.4 | Verifique que, antes de que un modelo de IA sea promovido a producción, sus resultados del sandbox estén firmados criptográficamente por personal de seguridad autorizado y almacenados en registros de auditoría inmutables. |   2   | D/V |
| 4.5.5 | Verifique que los entornos sandbox sean destruidos y recreados a partir de imágenes doradas entre evaluaciones con limpieza completa del sistema de archivos y de la memoria.                                                 |   2   | D/V |

---

## C4.6 Monitoreo de la seguridad de la infraestructura

Escanear y monitorear la infraestructura de forma continua con remediación automatizada y alertas en tiempo real.

|   #   | Descripción                                                                                                                                                                                                                | Nivel | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.6.1 | Verificar que las imágenes de contenedores se escaneen de acuerdo con las programaciones organizacionales y que las vulnerabilidades CRÍTICAS bloqueen el despliegue según los umbrales de riesgo de la organización.      |   1   | D/V |
| 4.6.2 | Verificar que la infraestructura cumpla con CIS Benchmarks o con los controles de NIST 800-53, con umbrales de cumplimiento definidos por la organización y remediación automática para las comprobaciones que fallen.     |   1   | D/V |
| 4.6.3 | Verifique que las vulnerabilidades de severidad alta estén parcheadas de acuerdo con los plazos de gestión de riesgos organizacionales, con procedimientos de emergencia para CVEs explotados activamente.                 |   2   | D/V |
| 4.6.4 | Verifique que las alertas de seguridad se integren con plataformas SIEM (Splunk, Elastic o Sentinel) utilizando formatos CEF o STIX/TAXII con enriquecimiento automatizado.                                                |   2   |  V  |
| 4.6.5 | Verifique que las métricas de infraestructura sean exportadas a sistemas de monitoreo (Prometheus, DataDog) con paneles de SLA e informes ejecutivos.                                                                      |   3   |  V  |
| 4.6.6 | Verifique que la deriva de configuración se detecte utilizando herramientas (Chef InSpec, AWS Config) de acuerdo con los requisitos de monitoreo de la organización, con reversión automática ante cambios no autorizados. |   2   | D/V |

---

## C4.7 Gestión de recursos de la infraestructura de IA

Prevenir ataques de agotamiento de recursos y garantizar una asignación equitativa de recursos mediante cuotas y monitoreo.

|   #   | Descripción                                                                                                                                                                                                                                           | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.7.1 | Verifique que la utilización de GPU/TPU sea monitorizada con alertas disparadas en umbrales definidos por la organización y que el escalado automático o el balanceo de carga se active de acuerdo con las políticas de gestión de capacidad.         |   1   | D/V |
| 4.7.2 | Verifique que las métricas de carga de trabajo de IA (latencia de inferencia, rendimiento, tasas de error) se recopilan de acuerdo con los requisitos de monitoreo de la organización y se correlacionan con la utilización de la infraestructura.    |   1   | D/V |
| 4.7.3 | Verifique que Kubernetes ResourceQuotas o equivalentes limiten las cargas de trabajo individuales de acuerdo con las políticas de asignación de recursos de la organización, con límites estrictos impuestos.                                         |   2   | D/V |
| 4.7.4 | Verifique que el monitoreo de costos rastree el gasto por carga de trabajo/inquilino, con alertas basadas en los umbrales presupuestarios de la organización y controles automatizados para excesos presupuestarios.                                  |   2   |  V  |
| 4.7.5 | Verifique que la planificación de capacidad utilice datos históricos, con períodos de pronóstico definidos por la organización, y un aprovisionamiento automático de recursos basado en patrones de demanda.                                          |   3   |  V  |
| 4.7.6 | Verifique que el agotamiento de recursos active el mecanismo Circuit Breaker de acuerdo con los requisitos de respuesta de la organización, incluida la limitación de tasas basada en políticas de capacidad y el aislamiento de la carga de trabajo. |   2   | D/V |

---

## C4.8 Separación de Entornos y Controles de Promoción

Imponer límites estrictos al entorno con puertas de promoción automatizadas y validación de seguridad.

|   #   | Descripción                                                                                                                                                                                                                         | Nivel | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.8.1 | Verifique que los entornos de desarrollo/pruebas/producción se ejecuten en VPCs/VNets separadas sin roles IAM compartidos, grupos de seguridad ni conectividad de red.                                                              |   1   | D/V |
| 4.8.2 | Verifique que la promoción de entornos requiera la aprobación del personal autorizado definido por la organización, con firmas criptográficas y registros de auditoría inmutables.                                                  |   1   | D/V |
| 4.8.3 | Verifique que los entornos de producción bloqueen el acceso SSH, deshabiliten los puntos finales de depuración y exijan las solicitudes de cambio con requisitos de aviso previo organizacionales, excepto en emergencias.          |   2   | D/V |
| 4.8.4 | Verifique que los cambios de infraestructura como código requieran revisión por pares con pruebas automatizadas y escaneo de seguridad antes de fusionarse con la rama principal.                                                   |   2   | D/V |
| 4.8.5 | Verifique que los datos no productivos estén anonimizados de acuerdo con los requisitos de privacidad organizacionales, la generación de datos sintéticos o el enmascaramiento completo de datos con eliminación de PII verificada. |   2   | D/V |
| 4.8.6 | Verifique que las puertas de promoción incluyan pruebas de seguridad automatizadas (SAST, DAST, escaneo de contenedores) con cero hallazgos críticos requeridos para la aprobación.                                                 |   2   | D/V |

---

## C4.9 Infraestructura Copia de Seguridad y Recuperación

Garantizar la resiliencia de la infraestructura mediante copias de seguridad automatizadas, procedimientos de recuperación probados y capacidades de recuperación ante desastres.

|   #   | Descripción                                                                                                                                                                                                                                            | Nivel | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 4.9.1 | Verifique que las configuraciones de infraestructura estén respaldadas de acuerdo con los cronogramas de copias de seguridad de la organización, en regiones geográficamente separadas, mediante la implementación de la estrategia de respaldo 3-2-1. |   1   | D/V |
| 4.9.2 | Verifique que los sistemas de copia de seguridad funcionen en redes aisladas con credenciales separadas y almacenamiento air-gapped para la protección contra ransomware.                                                                              |   2   | D/V |
| 4.9.3 | Verifique que los procedimientos de recuperación se prueben y validen mediante pruebas automatizadas, de acuerdo con los cronogramas organizacionales, con objetivos de RTO y RPO que satisfagan los requisitos de la organización.                    |   2   |  V  |
| 4.9.4 | Asegúrese de que la recuperación ante desastres incluya manuales de ejecución específicos de IA con la restauración de los pesos del modelo, la reconstrucción de clústeres de GPU y el mapeo de dependencias de servicios.                            |   3   |  V  |

---

## C4.10 Cumplimiento y Gobernanza de Infraestructura

Mantener el cumplimiento regulatorio mediante evaluación continua, documentación y controles automatizados.

|   #    | Descripción                                                                                                                                                                                                | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.10.1 | Verifique que el cumplimiento de la infraestructura se evalúe de acuerdo con los cronogramas organizacionales frente a los controles SOC 2, ISO 27001 o FedRAMP, con recopilación automática de evidencia. |   2   | D/V |
| 4.10.2 | Verifique que la documentación de infraestructura incluya diagramas de red, mapas de flujo de datos y modelos de amenazas actualizados de acuerdo con los requisitos de gestión del cambio organizacional. |   2   |  V  |
| 4.10.3 | Verifique que los cambios de infraestructura se sometan a una evaluación automatizada del impacto en el cumplimiento con flujos de aprobación regulatoria para modificaciones de alto riesgo.              |   3   | D/V |

---

## C4.11 Seguridad del hardware de IA

Asegurar componentes de hardware específicos para IA, incluyendo GPUs, TPUs y aceleradores de IA especializados.

|   #    | Descripción                                                                                                                                                                                                            | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.11.1 | Verifique que el firmware del acelerador de IA (BIOS de GPU, firmware de TPU) esté verificado con firmas criptográficas y esté actualizado de acuerdo con los plazos de gestión de parches de la organización.         |   2   | D/V |
| 4.11.2 | Verifique que, antes de la ejecución de la carga de trabajo, la integridad del acelerador de IA esté validada mediante la atestación de hardware utilizando TPM 2.0, Intel TXT o AMD SVM.                              |   2   | D/V |
| 4.11.3 | Verifique que la memoria de la GPU esté aislada entre cargas de trabajo utilizando SR-IOV, MIG (Multi-Instance GPU) u otro particionamiento de hardware equivalente, con la sanitización de la memoria entre trabajos. |   2   | D/V |
| 4.11.4 | Verifique que la cadena de suministro de hardware de IA incluya la verificación de procedencia con certificados del fabricante y la validación de empaques a prueba de manipulación.                                   |   3   |  V  |
| 4.11.5 | Verifique que los módulos de seguridad de hardware (HSM) protejan los pesos del modelo de IA y las llaves criptográficas con la certificación FIPS 140-2 Nivel 3 o Common Criteria EAL4+.                              |   3   | D/V |

---

## C4.12 Infraestructura de IA en el borde y distribuida

Despliegues de IA distribuidos y seguros, que incluyen computación en el borde, aprendizaje federado y arquitecturas de múltiples sitios.

|   #    | Descripción                                                                                                                                                                                                                          | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 4.12.1 | Verifique que los dispositivos de IA en el borde se autentiquen ante la infraestructura central mediante TLS mutuo con certificados de dispositivo rotados de acuerdo con la política de gestión de certificados de la organización. |   2   | D/V |
| 4.12.2 | Verifique que los dispositivos de borde implementen un arranque seguro con firmas verificadas y protección contra rollback que prevenga ataques de downgrade del firmware.                                                           |   2   | D/V |
| 4.12.3 | Verifique que la coordinación distribuida de IA utilice algoritmos de consenso tolerantes a fallos bizantinos con validación de participantes y detección de nodos maliciosos.                                                       |   3   | D/V |
| 4.12.4 | Verifique que la comunicación de borde a la nube incluya la limitación de ancho de banda, la compresión de datos y las capacidades de operación sin conexión con almacenamiento local seguro.                                        |   3   | D/V |

---

## C4.13 Seguridad de la Infraestructura Multinube e Híbrida

Asegurar cargas de trabajo de IA a través de múltiples proveedores de nube y despliegues híbridos entre la nube y las instalaciones.

|   #    | Descripción                                                                                                                                                                                                              | Nivel | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :-: |
| 4.13.1 | Verifique que las implementaciones de IA en múltiples nubes utilicen una federación de identidad independiente de la nube (OIDC, SAML) con gestión centralizada de políticas entre proveedores.                          |   2   | D/V |
| 4.13.2 | Verifique que la transferencia de datos entre nubes use cifrado de extremo a extremo con claves gestionadas por el cliente y controles de residencia de datos aplicados por jurisdicción.                                |   2   | D/V |
| 4.13.3 | Verifique que las cargas de trabajo de IA en la nube híbrida implementen políticas de seguridad consistentes entre entornos locales y en la nube, con monitoreo y alertas unificados.                                    |   2   | D/V |
| 4.13.4 | Verifique que la prevención del bloqueo del proveedor de la nube incluya infraestructura como código portátil, APIs estandarizadas y capacidades de exportación de datos con herramientas de conversión de formatos.     |   3   |  V  |
| 4.13.5 | Verifique que la optimización de costos en entornos multicloud incluya controles de seguridad que eviten la expansión descontrolada de recursos, así como cargos no autorizados por transferencias de datos entre nubes. |   3   |  V  |

---

## C4.14 Automatización de Infraestructura y Seguridad de GitOps

Asegurar las canalizaciones de automatización de infraestructura y los flujos de trabajo GitOps para la gestión de la infraestructura de IA.

|   #    | Descripción                                                                                                                                                                                                                                  | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.14.1 | Verifique que los repositorios GitOps exijan commits firmados con claves GPG y reglas de protección de ramas que eviten empujes directos a las ramas principales.                                                                            |   2   | D/V |
| 4.14.2 | Verifique que la automatización de la infraestructura incluya detección de deriva con remediación automática y capacidades de reversión activadas de acuerdo con los requisitos de respuesta de la organización ante cambios no autorizados. |   2   | D/V |
| 4.14.3 | Verifique que el aprovisionamiento automatizado de infraestructura incluya la validación de políticas de seguridad con bloqueo de despliegue para configuraciones no conformes.                                                              |   2   | D/V |
| 4.14.4 | Verifique que los secretos de la automatización de la infraestructura se gestionen a través de operadores externos de secretos (External Secrets Operator, Bank-Vaults) con rotación automática.                                             |   2   | D/V |
| 4.14.5 | Verifique que la infraestructura autorreparable incluya la correlación de eventos de seguridad con respuesta automatizada ante incidentes y flujos de trabajo de notificación a las partes interesadas.                                      |   3   |  V  |

---

## Seguridad de la Infraestructura Resistente a la Computación Cuántica

Prepare la infraestructura de IA para las amenazas de la computación cuántica mediante criptografía post-cuántica y protocolos cuánticamente seguros.

|   #    | Descripción                                                                                                                                                                                                      | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.15.1 | Verifique que la infraestructura de IA implemente los algoritmos criptográficos poscuánticos aprobados por NIST (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) para el intercambio de claves y firmas digitales. |   3   | D/V |
| 4.15.2 | Verifique que los sistemas de distribución cuántica de claves (QKD) estén implementados para comunicaciones de IA de alta seguridad con protocolos de gestión de claves resistentes a la computación cuántica.   |   3   | D/V |
| 4.15.3 | Verifique que los marcos de agilidad criptográfica permitan una migración rápida hacia nuevos algoritmos postcuánticos con rotación automática de certificados y claves.                                         |   3   | D/V |
| 4.15.4 | Verifique que el modelado de amenazas cuánticas evalúe la vulnerabilidad de la infraestructura de IA frente a ataques cuánticos, con cronogramas de migración documentados y evaluaciones de riesgos.            |   3   |  V  |
| 4.15.5 | Verifique que los sistemas criptográficos híbridos clásicos-cuánticos proporcionen defensa en profundidad durante el período de transición cuántica con monitoreo del rendimiento.                               |   3   | D/V |

---

## C4.16 Computación confidencial y enclaves seguros

Proteja las cargas de trabajo de IA y los pesos de los modelos mediante entornos de ejecución confiables basados en hardware y tecnologías de computación confidencial.

|   #    | Descripción                                                                                                                                                                              | Nivel | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.16.1 | Verifique que los modelos de IA sensibles se ejecuten dentro de enclaves Intel SGX, AMD SEV-SNP o ARM TrustZone con memoria cifrada y verificación de atestación.                        |   3   | D/V |
| 4.16.2 | Verifique que los contenedores confidenciales (Kata Containers, gVisor con computación confidencial) aíslen las cargas de trabajo de IA mediante cifrado de memoria a nivel de hardware. |   3   | D/V |
| 4.16.3 | Verifique que la atestación remota valide la integridad del enclave antes de cargar modelos de IA con una prueba criptográfica de la autenticidad de un entorno de ejecución.            |   3   | D/V |
| 4.16.4 | Verifique que los servicios de inferencia de IA confidenciales eviten la extracción de modelos mediante cálculo cifrado con pesos del modelo sellados y ejecución protegida.             |   3   | D/V |
| 4.16.5 | Verifique que la orquestación del entorno de ejecución confiable (TEE) gestione el ciclo de vida del enclave seguro con atestación remota y canales de comunicación cifrados.            |   3   | D/V |
| 4.16.6 | Verifique que el cómputo seguro entre múltiples partes (SMPC) permita el entrenamiento colaborativo de IA sin exponer conjuntos de datos individuales ni parámetros del modelo.          |   3   | D/V |

---

## C4.17 Infraestructura Zero-Knowledge

Implementar sistemas de pruebas de conocimiento cero para la verificación y autenticación de IA que preserven la privacidad sin revelar información sensible.

|   #    | Descripción                                                                                                                                                                                                                         | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.17.1 | Verifique que las pruebas de conocimiento cero (ZK-SNARKs, ZK-STARKs) verifiquen la integridad del modelo de IA y la trazabilidad del entrenamiento sin exponer los pesos del modelo ni los datos de entrenamiento.                 |   3   | D/V |
| 4.17.2 | Verifique que los sistemas de autenticación basados en pruebas de conocimiento cero (ZK) permitan una verificación de usuario que preserve la privacidad para servicios de IA sin revelar información relacionada con la identidad. |   3   | D/V |
| 4.17.3 | Verifique que los protocolos de intersección de conjuntos privados (PSI) permiten el emparejamiento de datos seguro para IA federada sin exponer conjuntos de datos individuales.                                                   |   3   | D/V |
| 4.17.4 | Verifique que los sistemas de aprendizaje automático de conocimiento cero (ZKML) permiten inferencias de IA verificables con una prueba criptográfica de la ejecución correcta.                                                     |   3   | D/V |
| 4.17.5 | Verifique que los ZK-rollups proporcionen un procesamiento de transacciones de IA escalable y que preserven la privacidad, con verificación por lotes y menor sobrecarga computacional.                                             |   3   | D/V |

---

## C4.18 Prevención de ataques por canal lateral

Proteja la infraestructura de IA de ataques de canal lateral basados en temporización, consumo de energía, electromagnetismo y caché que podrían filtrar información sensible.

|   #    | Descripción                                                                                                                                                                                     | Nivel | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.18.1 | Verifique que el tiempo de inferencia de IA esté normalizado mediante algoritmos de tiempo constante y relleno para prevenir ataques de extracción de modelos basados en el tiempo.             |   3   | D/V |
| 4.18.2 | Verifique que la protección contra el análisis de potencia incluya la inyección de ruido, el filtrado de la línea de alimentación y patrones de ejecución aleatorizados para el hardware de IA. |   3   | D/V |
| 4.18.3 | Verifique que las mitigaciones basadas en caché para canales laterales utilicen la partición de caché, la aleatorización y las instrucciones de vaciado para evitar fugas de información.       |   3   | D/V |
| 4.18.4 | Verifique que la protección contra emanaciones electromagnéticas incluya blindaje, filtrado de señales y procesamiento aleatorio para prevenir ataques de tipo TEMPEST.                         |   3   | D/V |
| 4.18.5 | Verifique que las defensas contra canales laterales a nivel de microarquitectura incluyan controles de ejecución especulativa y ofuscación de patrones de acceso a la memoria.                  |   3   | D/V |

---

## C4.19 Seguridad del hardware de IA neuromórfica y especializada

Asegurar las arquitecturas de hardware de IA emergentes, incluyendo chips neuromórficos, FPGAs, ASICs personalizados y sistemas de computación óptica.

|   #    | Descripción                                                                                                                                                                                                     | Nivel | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.19.1 | Verifique que la seguridad del chip neuromórfico incluya cifrado de patrones de picos, protección de pesos sinápticos y validación de reglas de aprendizaje basadas en hardware.                                |   3   | D/V |
| 4.19.2 | Verificar que los aceleradores de IA basados en FPGA implementen cifrado del bitstream, mecanismos anti-manipulación y carga de configuración segura con actualizaciones autenticadas.                          |   3   | D/V |
| 4.19.3 | Verifique que la seguridad de un ASIC personalizado incluya procesadores de seguridad integrados en el chip, una raíz de confianza de hardware y almacenamiento seguro de claves con detección de manipulación. |   3   | D/V |
| 4.19.4 | Verifique que los sistemas de computación óptica implementen cifrado óptico a prueba de cuántica, conmutación fotónica segura y procesamiento de señales ópticas protegido.                                     |   3   | D/V |
| 4.19.5 | Verifique que los chips de IA híbridos analógico-digital incluyan cómputo analógico seguro, almacenamiento de pesos protegido y conversión analógico-digital autenticada.                                       |   3   | D/V |

---

## C4.20 Infraestructura de cómputo que preserva la privacidad

Implementar controles de infraestructura para la computación que preserva la privacidad, para proteger los datos sensibles durante el procesamiento y análisis de IA.

|   #    | Descripción                                                                                                                                                                                                                            | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.20.1 | Verifique que la infraestructura de cifrado homomórfico permita el cómputo cifrado en cargas de trabajo de IA sensibles, con verificación de integridad criptográfica y monitoreo del rendimiento.                                     |   3   | D/V |
| 4.20.2 | Verifique que los sistemas de recuperación de información privada permitan consultas en bases de datos sin revelar patrones de consulta, mediante la protección criptográfica de los patrones de acceso.                               |   3   | D/V |
| 4.20.3 | Verifique que los protocolos de computación multipartita segura permiten una inferencia de IA que preserva la privacidad sin exponer entradas individuales ni cálculos intermedios.                                                    |   3   | D/V |
| 4.20.4 | Verifique que la gestión de claves que preserva la privacidad incluya generación de claves distribuida, criptografía de umbral y rotación de claves segura con protección basada en hardware.                                          |   3   | D/V |
| 4.20.5 | Verifique que el rendimiento del cómputo con preservación de la privacidad esté optimizado mediante procesamiento por lotes, almacenamiento en caché y aceleración por hardware, manteniendo las garantías de seguridad criptográfica. |   3   | D/V |

---

## C4.15 Marco de Agentes: Integración en la Nube, Seguridad y Despliegue Híbrido

Controles de seguridad para marcos de agentes integrados en la nube con arquitecturas híbridas locales y en la nube.

|   #    | Descripción                                                                                                                                                    | Nivel | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :-: |
| 4.15.1 | Verifique que la integración de almacenamiento en la nube utilice cifrado de extremo a extremo con gestión de claves controlada por el agente.                 |   1   | D/V |
| 4.15.2 | Verifique que los límites de seguridad del despliegue híbrido estén claramente definidos con canales de comunicación cifrados.                                 |   2   | D/V |
| 4.15.3 | Verifique que el acceso a los recursos en la nube incluya verificación de confianza cero con autenticación continua.                                           |   2   | D/V |
| 4.15.4 | Verifique que los requisitos de residencia de datos se cumplan mediante una atestación criptográfica de las ubicaciones de almacenamiento.                     |   3   | D/V |
| 4.15.5 | Verifique que las evaluaciones de seguridad del proveedor de servicios en la nube incluyan modelado de amenazas específico del agente y evaluación de riesgos. |   3   | D/V |

---

## Referencias

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [NIST SP 800-190: Application Container Security Guide](https://csrc.nist.gov/publications/detail/sp/800-190/final)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST SP 800-53: Security Controls for Federal Information Systems](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
* [FIPS 140-2 Security Requirements](https://csrc.nist.gov/publications/detail/fips/140/2/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
* [IEEE 2857: Privacy Engineering for AI Systems](https://standards.ieee.org/ieee/2857/7273/)
* [NIST SP 800-161: Cybersecurity Supply Chain Risk Management](https://csrc.nist.gov/publications/detail/sp/800-161/rev-1/final)
* [NIST Post-Quantum Cryptography Standards](https://csrc.nist.gov/Projects/post-quantum-cryptography)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/tools/software-guard-extensions/overview.html)
* [AMD SEV-SNP White Paper](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf)
* [ARM TrustZone Technology](https://developer.arm.com/ip-products/security-ip/trustzone)
* [ZK-SNARKs: A Gentle Introduction](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)
* [NIST SP 800-57: Cryptographic Key Management](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-5/final)
* [Side-Channel Attack Countermeasures](https://link.springer.com/book/10.1007/978-3-319-75268-6)
* [Neuromorphic Computing Security Challenges](https://ieeexplore.ieee.org/document/9458103)
* [FPGA Security: Fundamentals, Evaluation, and Countermeasures](https://link.springer.com/book/10.1007/978-3-319-90385-9)
* [Microsoft SEAL: Homomorphic Encryption Library](https://github.com/Microsoft/SEAL)
* [HElib: Homomorphic Encryption Library](https://github.com/homenc/HElib)
* [PALISADE Lattice Cryptography Library](https://palisade-crypto.org/)
* [Differential Privacy: A Survey of Results](https://link.springer.com/chapter/10.1007/978-3-540-79228-4_1)
* [Secure Aggregation for Federated Learning](https://eprint.iacr.org/2017/281.pdf)
* [Private Information Retrieval: Concepts and Constructions](https://link.springer.com/book/10.1007/978-3-030-16234-8)

