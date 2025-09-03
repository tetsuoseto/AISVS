# Memória C8, Embeddings e Segurança de Banco de Dados de Vetores

## Objetivo de Controle

Embeddings e bancos de vetores atuam como a "memória viva" dos sistemas de IA contemporâneos, aceitando continuamente dados fornecidos pelo usuário e os apresentando de volta aos contextos do modelo por meio da Geração Aumentada pela Recuperação (RAG). Se não forem governados, essa memória pode vazar PII, violar consentimento ou ser invertida para reconstruir o texto original. O objetivo desta família de controles é fortalecer os pipelines de memória e os bancos de dados de vetores, de modo que o acesso seja de privilégio mínimo, os embeddings preservem a privacidade, vetores armazenados expirem ou possam ser revogados sob demanda, e a memória por usuário nunca contamine os prompts ou as gerações de outro usuário.

---

## C8.1 Controles de Acesso em Índices de Memória e RAG

Impor controles de acesso granulares em cada coleção de vetores.

|   #   | Descrição                                                                                                                                                                                      | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.1.1 | Verifique se as regras de controle de acesso em nível de linha ou namespace restringem as operações de inserção, exclusão e consulta por inquilino, coleção ou etiqueta de documento.          |   1   |  D/V  |
| 8.1.2 | Verifique se as chaves de API ou JWTs contêm reivindicações com escopo (por exemplo, identificadores de coleção, verbos de ação) e são rotacionadas pelo menos a cada trimestre.               |   1   |  D/V  |
| 8.1.3 | Verifique se as tentativas de elevação de privilégios (por exemplo, consultas de similaridade entre espaços de nomes) são detectadas e registradas em um SIEM dentro de 5 minutos.             |   2   |  D/V  |
| 8.1.4 | Verifique se os logs de auditoria do banco de dados de vetores registram o identificador do sujeito, a operação, o ID do vetor/namespace, o limiar de similaridade e a contagem de resultados. |   2   |  D/V  |
| 8.1.5 | Verifique se as decisões de acesso são testadas quanto a falhas de bypass sempre que os motores forem atualizados ou as regras de particionamento de índices forem alteradas.                  |   3   |   V   |

---

## C8.2 Sanitização de Embeddings e Validação

Pré-filtrar o texto para PII, ocultar ou pseudonimizar antes da vetorização, e, opcionalmente, pós-processar embeddings para remover sinais residuais.

|   #   | Descrição                                                                                                                                                                                                                        | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.2.1 | Verifique se PII e dados regulamentados são detectados por classificadores automáticos e mascarados, tokenizados ou descartados antes da pré-embedding.                                                                          |   1   |  D/V  |
| 8.2.2 | Verifique se os pipelines de embeddings rejeitam ou colocam em quarentena entradas contendo código executável ou artefatos não-UTF-8 que possam contaminar o índice.                                                             |   1   |   D   |
| 8.2.3 | Verifique se a sanitização por privacidade diferencial local ou por privacidade diferencial métrica é aplicada aos embeddings de sentença cuja distância a qualquer token PII conhecido esteja abaixo de um limiar configurável. |   2   |  D/V  |
| 8.2.4 | Verifique que a eficácia da sanitização (por exemplo, recall da remoção de PII, deriva semântica) seja validada pelo menos semestralmente contra corpora de referência.                                                          |   2   |   V   |
| 8.2.5 | Verifique se as configurações de sanitização estão sob controle de versão e se as alterações passam por revisão por pares.                                                                                                       |   3   |  D/V  |

---

## C8.3 Expiração da Memória, Revogação e Exclusão

GDPR "direito ao esquecimento" e leis semelhantes exigem eliminação em tempo hábil; os armazenamentos de vetores devem, portanto, suportar TTLs, exclusões definitivas e tomb-stoning para que vetores revogados não possam ser recuperados nem reindexados.

|   #   | Descrição                                                                                                                                                                                          | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.3.1 | Verifique se cada vetor e registro de metadados possui TTL ou etiqueta de retenção explícita, respeitada pelos trabalhos de limpeza automatizados.                                                 |   1   |  D/V  |
| 8.3.2 | Verifique se as solicitações de exclusão iniciadas pelo usuário purgam vetores, metadados, cópias em cache e índices derivados dentro de 30 dias.                                                  |   1   |  D/V  |
| 8.3.3 | Verifique se as exclusões lógicas são seguidas pela destruição criptográfica dos blocos de armazenamento, se o hardware oferecer suporte a isso, ou pela destruição das chaves no Cofre de Chaves. |   2   |   D   |
| 8.3.4 | Verifique se vetores expirados são excluídos dos resultados da busca do vizinho mais próximo em < 500 ms após a expiração.                                                                         |   3   |  D/V  |

---

## C8.4 Prevenir Inversão de Embeddings e Vazamento

Defesas recentes—superposição de ruído, redes de projeção, perturbação do neurônio de privacidade e criptografia na camada de aplicação—podem reduzir as taxas de inversão em nível de token para abaixo de 5%.

|   #   | Descrição                                                                                                                                                                                   | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.4.1 | Verifique se existe um modelo formal de ameaça que cubra ataques de inversão, ataques de inferência de pertencimento e ataques de inferência de atributos, e que seja revisado anualmente.  |   1   |   V   |
| 8.4.2 | Verifique se a criptografia na camada de aplicação ou a criptografia pesquisável protegem os vetores contra leituras diretas por administradores de infraestrutura ou pela equipe de nuvem. |   2   |  D/V  |
| 8.4.3 | Verifique se os parâmetros de defesa (ε para DP, ruído σ, posto de projeção k) equilibram privacidade ≥ 99 % proteção de token e utilidade ≤ 3 % de perda de precisão.                      |   3   |   V   |
| 8.4.4 | Verifique se as métricas de resiliência à inversão são parte dos critérios de liberação para atualizações de modelos, com orçamentos de regressão definidos.                                |   3   |  D/V  |

---

## C8.5 Aplicação do Escopo para Memória Específica do Usuário

Vazamento entre inquilinos continua sendo um dos maiores riscos do RAG: consultas de similaridade mal filtradas podem revelar documentos privados de outro cliente.

|   #   | Descrição                                                                                                                                                                 | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.5.1 | Verifique se cada consulta de recuperação é pós-filtrada pelo ID do inquilino/usuário antes de ser passada para o prompt da LLM.                                          |   1   |  D/V  |
| 8.5.2 | Verifique se os nomes de coleção ou IDs com espaço de nomes são salteados por usuário ou inquilino, para que os vetores não possam colidir entre os escopos.              |   1   |   D   |
| 8.5.3 | Verifique que os resultados de similaridade acima de um limiar de distância configurável, mas fora do escopo do chamador, sejam descartados e gerem alertas de segurança. |   2   |  D/V  |
| 8.5.4 | Verifique se os testes de estresse multi-tenant simulam consultas adversárias que tentam recuperar documentos fora do escopo e demonstram que não há vazamento de dados.  |   2   |   V   |
| 8.5.5 | Verifique se as chaves de criptografia estão segregadas por inquilino, garantindo isolamento criptográfico, mesmo que o armazenamento físico seja compartilhado.          |   3   |  D/V  |

---

## C8.6 Segurança Avançada do Sistema de Memória

Controles de segurança para arquiteturas de memória sofisticadas, incluindo memória episódica, memória semântica e memória de trabalho, com requisitos específicos de isolamento e validação.

|   #   | Descrição                                                                                                                                                                                                                                                                       | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.6.1 | Verifique se os diferentes tipos de memória (episódica, semântica, de trabalho) possuem contextos de segurança isolados com controles de acesso baseados em funções, chaves de criptografia separadas e padrões de acesso documentados para cada tipo de memória.               |   1   |  D/V  |
| 8.6.2 | Verifique que os processos de consolidação de memória incluam validação de segurança para impedir a injeção de memórias maliciosas por meio de sanitização de conteúdo, verificação de fonte e verificações de integridade antes do armazenamento.                              |   2   |  D/V  |
| 8.6.3 | Verifique se as consultas de recuperação de memória são validadas e sanitizadas para impedir a extração de informações não autorizadas por meio de análise de padrões de consulta, aplicação de controle de acesso e filtragem de resultados.                                   |   2   |  D/V  |
| 8.6.4 | Verifique se os mecanismos de apagamento de memória eliminam com segurança informações sensíveis com garantias de apagamento criptográfico, usando exclusão de chaves, sobrescrição em várias passagens ou exclusão segura baseada em hardware com certificados de verificação. |   3   |  D/V  |
| 8.6.5 | Verifique se a integridade do sistema de memória é monitorada continuamente quanto a modificações não autorizadas ou corrupção, por meio de checksums, registros de auditoria e alertas automáticos quando o conteúdo da memória muda fora das operações normais.               |   3   |  D/V  |

---

## Referências

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

