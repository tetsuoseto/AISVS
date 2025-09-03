# C6 Segurança da Cadeia de Suprimentos para Modelos, Frameworks e Dados

## Objetivo de Controle

Ataques na cadeia de suprimentos de IA exploram modelos, frameworks ou conjuntos de dados de terceiros para inserir portas traseiras, vieses ou código explorável. Esses controles fornecem proveniência de ponta a ponta, gerenciamento de vulnerabilidades e monitoramento para proteger todo o ciclo de vida do modelo.

---

## C6.1 Avaliação de Modelos Pré-Treinados e Proveniência

Avalie e autentique as origens de modelos de terceiros, licenças e comportamentos ocultos antes de qualquer ajuste fino ou implantação.

|   #   | Descrição                                                                                                                                                     | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.1.1 | Verifique se cada artefato de modelo de terceiros inclui um registro de proveniência assinado que identifique o repositório de origem e o hash do commit.     |   1   |  D/V  |
| 6.1.2 | Verifique se os modelos são inspecionados em busca de camadas maliciosas ou gatilhos de Cavalo de Troia usando ferramentas automatizadas antes da importação. |   1   |  D/V  |
| 6.1.3 | Verifique se os ajustes finos de transferência passam pela avaliação adversarial para detectar comportamentos ocultos.                                        |   2   |   D   |
| 6.1.4 | Verifique se as licenças de modelo, as etiquetas de controle de exportação e as declarações de origem dos dados estão registradas em uma entrada ML‑BOM.      |   2   |   V   |
| 6.1.5 | Verifique que modelos de alto‑risco (pesos carregados publicamente, criadores não verificados) permaneçam em quarentena até revisão humana e aprovação.       |   3   |  D/V  |

---

## C6.2 Varredura de Frameworks e Bibliotecas

Escaneie continuamente os frameworks e bibliotecas de ML em busca de CVEs e código malicioso para manter a pilha de tempo de execução segura.

|   #   | Descrição                                                                                                                                         | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.2.1 | Verifique se os pipelines de CI executam analisadores de dependências em frameworks de IA e bibliotecas críticas.                                 |   1   |  D/V  |
| 6.2.2 | Verifique se as vulnerabilidades críticas (CVSS ≥ 7.0) bloqueiam a promoção de imagens para produção.                                             |   1   |  D/V  |
| 6.2.3 | Verifique se a análise estática de código é executada em bibliotecas ML forkadas ou vendorizadas.                                                 |   2   |   D   |
| 6.2.4 | Verifique se as propostas de atualização de frameworks incluem uma avaliação de impacto de segurança que faça referência a feeds públicos de CVE. |   2   |   V   |
| 6.2.5 | Verifique se os sensores em tempo de execução alertam para carregamentos inesperados de bibliotecas dinâmicas que se desviem da SBOM assinada.    |   3   |   V   |

---

## C6.3 Fixação de Dependências e Verificação

Fixar cada dependência a digests imutáveis e reproduzir as compilações para garantir artefatos idênticos e à prova de adulteração.

|   #   | Descrição                                                                                                                                      | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.3.1 | Verifique se todos os gerenciadores de pacotes aplicam a fixação de versões por meio de arquivos de bloqueio.                                  |   1   |  D/V  |
| 6.3.2 | Verifique se os digests imutáveis são usados em vez de tags mutáveis em referências de contêiner.                                              |   1   |  D/V  |
| 6.3.3 | Verifique se as verificações de reprodutibilidade de compilação comparam valores de hash entre execuções de CI para garantir saídas idênticas. |   2   |   D   |
| 6.3.4 | Verifique se as atestações de build são armazenadas por 18 meses para rastreabilidade de auditoria.                                            |   2   |   V   |
| 6.3.5 | Verifique se dependências expiradas disparam PRs automatizados para atualizar ou forkar versões fixadas.                                       |   3   |   D   |

---

## C6.4 Aplicação de Fontes Confiáveis

Permitir o download de artefatos apenas de fontes criptograficamente verificadas e aprovadas pela organização, e bloquear tudo o mais.

|   #   | Descrição                                                                                                                                     | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.4.1 | Verifique se os pesos do modelo, os conjuntos de dados e os contêineres são baixados apenas de domínios aprovados ou de registros internos.   |   1   |  D/V  |
| 6.4.2 | Verifique se as assinaturas Sigstore/Cosign validam a identidade do publicador antes que os artefatos sejam armazenados em cache localmente.  |   1   |  D/V  |
| 6.4.3 | Verifique se os proxies de saída bloqueiam downloads de artefatos não autenticados para impor a política trusted‑source.                      |   2   |   D   |
| 6.4.4 | Verifique se as listas de permitidos do repositório são revistas trimestralmente, com evidência de justificativa comercial para cada entrada. |   2   |   V   |
| 6.4.5 | Verifique se violações de políticas acionam a quarentena de artefatos e a reversão de execuções de pipeline dependentes.                      |   3   |   V   |

---

## C6.5 Avaliação de Risco de Conjunto de Dados de Terceiros

Avaliar conjuntos de dados externos quanto a envenenamento de dados, viés e conformidade legal, e monitorá-los ao longo de seu ciclo de vida.

|   #   | Descrição                                                                                                                                                      | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.5.1 | Verifique se conjuntos de dados externos passam por pontuação de risco de envenenamento de dados (por exemplo, fingerprinting de dados, detecção de outliers). |   1   |  D/V  |
| 6.5.2 | Verifique se as métricas de viés (paridade demográfica, igualdade de oportunidades) são calculadas antes da aprovação do conjunto de dados.                    |   1   |   D   |
| 6.5.3 | Verifique se a proveniência e os termos de licença dos conjuntos de dados estão registrados nas entradas ML‑BOM.                                               |   2   |   V   |
| 6.5.4 | Verifique se o monitoramento periódico detecta deriva de dados ou corrupção em conjuntos de dados hospedados.                                                  |   2   |   V   |
| 6.5.5 | Verifique se o conteúdo proibido (direitos autorais, PII) é removido por meio de limpeza automatizada antes do treinamento.                                    |   3   |   D   |

---

## C6.6 Monitoramento de Ataques na Cadeia de Suprimentos

Detectar ameaças na cadeia de suprimentos precocemente por meio de feeds CVE, análise de logs de auditoria e simulações de red-team.

|   #   | Descrição                                                                                                                                                       | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.6.1 | Verifique se os logs de auditoria de CI/CD fluem para as detecções do SIEM para requisições de pacotes anômalas ou etapas de build adulteradas.                 |   1   |   V   |
| 6.6.2 | Verifique se os playbooks de resposta a incidentes incluem procedimentos de rollback para modelos ou bibliotecas comprometidos.                                 |   2   |   D   |
| 6.6.3 | Verifique se o enriquecimento de inteligência‑de‑ameaças marca indicadores ML‑específicos (por exemplo, IoCs de envenenamento de modelo) na triagem de alertas. |   3   |   V   |

---

## C6.7 ML‑BOM para Artefatos do Modelo

Gerar e assinar SBOMs detalhadas específicas de ML (ML‑BOMs) para que os consumidores a jusante possam verificar a integridade dos componentes no momento da implantação.

|   #   | Descrição                                                                                                                                               | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 6.7.1 | Verifique se cada artefato do modelo publica um ML‑BOM que liste conjuntos de dados, pesos, hiperparâmetros e licenças.                                 |   1   |  D/V  |
| 6.7.2 | Verifique se a geração de ML‑BOM e a assinatura Cosign estão automatizadas na CI e são obrigatórias para o merge.                                       |   1   |  D/V  |
| 6.7.3 | Verifique se as verificações de completude do ML‑BOM fazem com que a compilação falhe caso algum metadado do componente (hash, licença) esteja ausente. |   2   |   D   |
| 6.7.4 | Verifique se os consumidores a jusante podem consultar ML-BOMs via API para validar modelos importados no momento da implantação.                       |   2   |   V   |
| 6.7.5 | Verifique se os ML‑BOMs estão sob controle de versão e passam por comparação de diferenças (diff) para detectar modificações não autorizadas.           |   3   |   V   |

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

