# Segurança da Cadeia de Suprimentos C6 para Modelos, Frameworks e Dados

## Objetivo de Controle

Os ataques à cadeia de suprimentos de IA exploram modelos, frameworks ou conjuntos de dados de terceiros para incorporar backdoors, viés ou códigos exploráveis. Esses controles fornecem proveniência de ponta a ponta, gerenciamento de vulnerabilidades e monitoramento para proteger todo o ciclo de vida do modelo.

---

## C6.1 Verificação e Procedência do Modelo Pré-treinado

Avalie e autentique as origens, licenças e comportamentos ocultos de modelos de terceiros antes de qualquer ajuste fino ou implantação.

|   #   | Descrição                                                                                                                                                   | Nível | Função |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 6.1.1 | Verifique se todo artefato de modelo de terceiros inclui um registro de proveniência assinado que identifica o repositório de origem e o hash do commit.    |   1   |  D/V   |
| 6.1.2 | Verifique se os modelos são analisados em busca de camadas maliciosas ou gatilhos de Trojan usando ferramentas automatizadas antes da importação.           |   1   |  D/V   |
| 6.1.3 | Verifique se o fine-tuning de transfer learning passa na avaliação adversarial para detectar comportamentos ocultos.                                        |   2   |   D    |
| 6.1.4 | Verifique se as licenças do modelo, as tags de controle de exportação e as declarações de origem dos dados estão registradas em uma entrada de ML‑BOM.      |   2   |   V    |
| 6.1.5 | Verifique se os modelos de alto risco (pesos carregados publicamente, criadores não verificados) permanecem em quarentena até a revisão e aprovação humana. |   3   |  D/V   |

---

## C6.2 Varredura de Frameworks e Bibliotecas

Escanear continuamente frameworks e bibliotecas de ML em busca de CVEs e código malicioso para manter a pilha de execução segura.

|   #   | Descrição                                                                                                                                    | Nível | Função |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 6.2.1 | Verifique se os pipelines de CI executam scanners de dependências em frameworks de IA e bibliotecas críticas.                                |   1   |  D/V   |
| 6.2.2 | Verifique se as vulnerabilidades críticas (CVSS ≥ 7.0) bloqueiam a promoção para imagens de produção.                                        |   1   |  D/V   |
| 6.2.3 | Verifique se a análise estática de código é executada em bibliotecas de ML bifurcadas ou incorporadas.                                       |   2   |   D    |
| 6.2.4 | Verifique se as propostas de atualização do framework incluem uma avaliação de impacto de segurança referenciando fontes públicas de CVE.    |   2   |   V    |
| 6.2.5 | Verifique se os sensores em tempo de execução alertam sobre carregamentos inesperados de bibliotecas dinâmicas que desviam do SBOM assinado. |   3   |   V    |

---

## C6.3 Fixação e Verificação de Dependências

Fixe todas as dependências em digests imutáveis e reproduza as compilações para garantir artefatos idênticos e livres de adulterações.

|   #   | Descrição                                                                                                                | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------ | :---: | :----: |
| 6.3.1 | Verifique se todos os gerenciadores de pacotes aplicam o bloqueio de versão por meio de arquivos de bloqueio.            |   1   |  D/V   |
| 6.3.2 | Verifique se são usados resumos imutáveis em vez de tags mutáveis nas referências de contêiner.                          |   1   |  D/V   |
| 6.3.3 | Verifique se as verificações de build reprodutível comparam hashes entre execuções de CI para garantir saídas idênticas. |   2   |   D    |
| 6.3.4 | Verifique se as atestações de compilação são armazenadas por 18 meses para rastreabilidade de auditoria.                 |   2   |   V    |
| 6.3.5 | Verifique se dependências expiradas acionam PRs automáticos para atualizar ou bifurcar versões fixadas.                  |   3   |   D    |

---

## C6.4 Aplicação de Fonte Confiável

Permita downloads de artefatos apenas de fontes aprovadas pela organização e verificadas criptograficamente, e bloqueie todo o resto.

|   #   | Descrição                                                                                                                                     | Nível | Função |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 6.4.1 | Verifique se os pesos do modelo, os conjuntos de dados e os contêineres são baixados somente de domínios aprovados ou registradores internos. |   1   |  D/V   |
| 6.4.2 | Verifique se as assinaturas Sigstore/Cosign validam a identidade do publicador antes que os artefatos sejam armazenados em cache localmente.  |   1   |  D/V   |
| 6.4.3 | Verifique se os proxies de saída bloqueiam downloads de artefatos não autenticados para aplicar a política de fonte confiável.                |   2   |   D    |
| 6.4.4 | Verifique se as listas de permissões do repositório são revisadas trimestralmente com evidência de justificativa comercial para cada entrada. |   2   |   V    |
| 6.4.5 | Verifique se as violações de política acionam o isolamento dos artefatos e o rollback das execuções das pipelines dependentes.                |   3   |   V    |

---

## C6.5 Avaliação de Risco de Conjunto de Dados de Terceiros

Avalie conjuntos de dados externos quanto a envenenamento, viés e conformidade legal, e monitore-os ao longo de todo o seu ciclo de vida.

|   #   | Descrição                                                                                                                                                        | Nível | Função |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 6.5.1 | Verificar se os conjuntos de dados externos passam por uma avaliação de risco de envenenamento (por exemplo, impressão digital dos dados, detecção de outliers). |   1   |  D/V   |
| 6.5.2 | Verifique se as métricas de viés (paridade demográfica, igualdade de oportunidade) são calculadas antes da aprovação do conjunto de dados.                       |   1   |   D    |
| 6.5.3 | Verifique se a proveniência e os termos de licença dos conjuntos de dados estão capturados nas entradas do ML‑BOM.                                               |   2   |   V    |
| 6.5.4 | Verifique se o monitoramento periódico detecta deriva ou corrupção nos conjuntos de dados hospedados.                                                            |   2   |   V    |
| 6.5.5 | Verifique se o conteúdo não permitido (direitos autorais, informações pessoais identificáveis) é removido por meio de limpeza automatizada antes do treinamento. |   3   |   D    |

---

## C6.6 Monitoramento de Ataque na Cadeia de Suprimentos

Detecte ameaças à cadeia de suprimentos cedo por meio de feeds CVE, análises de logs de auditoria e simulações de equipe vermelha.

|   #   | Descrição                                                                                                                                                                         | Nível | Função |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 6.6.1 | Verifique se os logs de auditoria do CI/CD são transmitidos para as detecções do SIEM para identificar puxadas de pacotes anômalas ou etapas de construção adulteradas.           |   1   |   V    |
| 6.6.2 | Verifique se os playbooks de resposta a incidentes incluem procedimentos de reversão para modelos ou bibliotecas comprometidos.                                                   |   2   |   D    |
| 6.6.3 | Verifique se as tags de enriquecimento de inteligência de ameaças identificam indicadores específicos de ML (por exemplo, IoCs de envenenamento de modelo) na triagem de alertas. |   3   |   V    |

---

## C6.7 ML‑BOM para Artefatos de Modelo

Gere e assine SBOMs específicas para ML detalhadas (ML-BOMs) para que os consumidores finais possam verificar a integridade dos componentes no momento da implantação.

|   #   | Descrição                                                                                                                                  | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :----: |
| 6.7.1 | Verifique se todo artefato do modelo publica um ML-BOM que lista conjuntos de dados, pesos, hiperparâmetros e licenças.                    |   1   |  D/V   |
| 6.7.2 | Verifique se a geração do ML‑BOM e a assinatura Cosign estão automatizadas na CI e são obrigatórias para o merge.                          |   1   |  D/V   |
| 6.7.3 | Verifique se as verificações de completude do ML-BOM falham na compilação se algum metadado do componente (hash, licença) estiver ausente. |   2   |   D    |
| 6.7.4 | Verifique se os consumidores a jusante podem consultar ML-BOMs via API para validar modelos importados no momento da implantação.          |   2   |   V    |
| 6.7.5 | Verifique se os ML‑BOMs são controlados por versão e comparados para detectar modificações não autorizadas.                                |   3   |   V    |

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

