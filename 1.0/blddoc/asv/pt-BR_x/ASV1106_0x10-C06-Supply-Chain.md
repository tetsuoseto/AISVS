# C6 Segurança da Cadeia de Suprimentos para Modelos, Estruturas e Dados

## Objetivo de Controle

Ataques na cadeia de suprimentos de IA exploram modelos, frameworks ou conjuntos de dados de terceiros para inserir backdoors, viés ou códigos exploráveis. Esses controles fornecem proveniência de ponta a ponta, gerenciamento de vulnerabilidades e monitoramento para proteger todo o ciclo de vida do modelo.

---

## C6.1 Avaliação de Modelo Pré-treinado & Proveniência

Avalie e autentique as origens, licenças e comportamentos ocultos de modelos de terceiros antes de qualquer ajuste fino ou implantação.

|   #   | Descrição                                                                                                                                                  | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.1.1 | Verifique se todo artefato de modelo de terceiros inclui um registro de proveniência assinado que identifique o repositório de origem e o hash do commit.  |   1   |  D/V  |
| 6.1.2 | Verifique se os modelos foram analisados quanto à presença de camadas maliciosas ou gatilhos Trojan usando ferramentas automatizadas antes da importação.  |   1   |  D/V  |
| 6.1.3 | Verifique se o ajuste fino de transfer‑learning passa na avaliação adversarial para detectar comportamentos ocultos.                                       |   2   |   D   |
| 6.1.4 | Verifique se as licenças do modelo, tags de controle de exportação e declarações de origem dos dados estão registradas em uma entrada do ML‑BOM.           |   2   |   V   |
| 6.1.5 | Verifique se os modelos de alto risco ( pesos carregados publicamente, criadores não verificados) permanecem em quarentena até revisão e aprovação humana. |   3   |  D/V  |

---

## C6.2 Varredura de Frameworks & Bibliotecas

Escaneie continuamente frameworks e bibliotecas de ML em busca de CVEs e código malicioso para manter a pilha de tempo de execução segura.

|   #   | Descrição                                                                                                                                     | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.2.1 | Verifique se os pipelines de CI executam varredores de dependências em frameworks de IA e bibliotecas críticas.                               |   1   |  D/V  |
| 6.2.2 | Verifique se vulnerabilidades críticas (CVSS ≥ 7.0) bloqueiam a promoção para imagens de produção.                                            |   1   |  D/V  |
| 6.2.3 | Verifique se a análise de código estático é executada em bibliotecas de ML bifurcadas ou vendidas.                                            |   2   |   D   |
| 6.2.4 | Verifique se as propostas de atualização do framework incluem uma avaliação de impacto de segurança referenciando feeds públicos de CVE.      |   2   |   V   |
| 6.2.5 | Verifique se os sensores em tempo de execução alertam sobre carregamentos inesperados de bibliotecas dinâmicas que divergem do SBOM assinado. |   3   |   V   |

---

## C6.3 Fixação e Verificação de Dependências

Fixe cada dependência em dígitos imutáveis e reproduza builds para garantir artefatos idênticos e livres de adulteração.

|   #   | Descrição                                                                                                                | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 6.3.1 | Verifique se todos os gerenciadores de pacotes aplicam o pinning de versões por meio de arquivos de bloqueio.            |   1   |  D/V  |
| 6.3.2 | Verifique se os resumos imutáveis são usados em vez de tags mutáveis nas referências de container.                       |   1   |  D/V  |
| 6.3.3 | Verifique se as verificações de build reproduzível comparam hashes entre execuções de CI para garantir saídas idênticas. |   2   |   D   |
| 6.3.4 | Verifique se as attestations de build são armazenadas por 18 meses para rastreabilidade de auditoria.                    |   2   |   V   |
| 6.3.5 | Verifique se dependências expiradas acionam PRs automáticos para atualização ou bifurcação de versões fixadas.           |   3   |   D   |

---

## C6.4 Aplicação de Fonte Confiável

Permitir downloads de artefatos apenas de fontes verificadas criptograficamente e aprovada pela organização, bloqueando tudo o mais.

|   #   | Descrição                                                                                                                                       | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.4.1 | Verifique se os pesos do modelo, conjuntos de dados e containers são baixados apenas de domínios aprovados ou registros internos.               |   1   |  D/V  |
| 6.4.2 | Verifique se as assinaturas do Sigstore/Cosign validam a identidade do publicador antes que os artefatos sejam armazenados em cache localmente. |   1   |  D/V  |
| 6.4.3 | Verifique se proxies de saída bloqueiam downloads de artefatos não autenticados para garantir a política de fonte confiável.                    |   2   |   D   |
| 6.4.4 | Verifique se as listas de permissão do repositório são revisadas trimestralmente com evidências de justificativa de negócios para cada entrada. |   2   |   V   |
| 6.4.5 | Verifique se violações de política acionam o quarentena de artefatos e rollback de execuções de pipeline dependentes.                           |   3   |   V   |

---

## C6.5 Avaliação de Risco de Conjuntos de Dados de Terceiros

Avalie conjuntos de dados externos quanto a envenenamento, viés e conformidade legal, e monitore-os ao longo de seu ciclo de vida.

|   #   | Descrição                                                                                                                                                       | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.5.1 | Verifique se os conjuntos de dados externos passam por uma avaliação de risco de envenenamento (por exemplo, impressão digital de dados, detecção de outliers). |   1   |  D/V  |
| 6.5.2 | Verifique se as métricas de viés (paridade demográfica, oportunidade igual) são calculadas antes da aprovação do conjunto de dados.                             |   1   |   D   |
| 6.5.3 | Verifique se a proveniência e os termos de licença para conjuntos de dados estão registrados nas entradas do ML‑BOM.                                            |   2   |   V   |
| 6.5.4 | Verifique se a monitorização periódica detecta deriva ou corrupção nos conjuntos de dados hospedados.                                                           |   2   |   V   |
| 6.5.5 | Verifique se o conteúdo não permitido (direitos autorais, PII) foi removido por meio de limpeza automatizada antes do treinamento.                              |   3   |   D   |

---

## C6.6 Monitoramento de Ataques na Cadeia de Fornecimento

Detecte ameaças na cadeia de suprimentos cedo através de feeds CVE, análise de logs de auditoria e simulações de equipe vermelha.

|   #   | Descrição                                                                                                                                                                    | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.6.1 | Verifique se os registros de auditoria CI/CD são transmitidos para as detecções SIEM por pulls de pacote anômalicos ou etapas de build adulteradas.                          |   1   |   V   |
| 6.6.2 | Verifique se os playbooks de resposta a incidentes incluem procedimentos de rollback para modelos ou bibliotecas comprometidos.                                              |   2   |   D   |
| 6.6.3 | Verifique se as tags de enriquecimento de inteligência de ameaça indicam indicadores específicos de ML (por exemplo, IoCs de envenenamento de modelo) na triagem de alertas. |   3   |   V   |

---

## C6.7 ML‑BOM para Artefatos de Modelo

Gerar e assinar SBOMs específicos de ML‑ (ML‑BOMs) detalhados para que os consumidores downstream possam verificar a integridade dos componentes no momento do deploy.

|   #   | Descrição                                                                                                                                     | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.7.1 | Verifique se cada artefato de modelo publica uma ML‑BOM que liste conjuntos de dados, pesos, hiperparâmetros e licenças.                      |   1   |  D/V  |
| 6.7.2 | Verifique se a geração de ML‑BOM e a assinatura do Cosign estão automatizadas no CI e são necessárias para a mesclagem.                       |   1   |  D/V  |
| 6.7.3 | Verifique se as verificações de completude do ML‑BOM falham na construção se algum metadado do componente (hash, licença) estiver ausente.    |   2   |   D   |
| 6.7.4 | Verifique se os consumidores downstream podem consultar os ML-BOMs via API para validar os modelos importados durante o tempo de implantação. |   2   |   V   |
| 6.7.5 | Verifique se os ML‑BOMs estão sob controle de versão e com diferenças monitoradas para detectar modificações não autorizadas.                 |   3   |   V   |

---

## Referências

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

