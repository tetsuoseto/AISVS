# Segurança de Memória C8, Embeddings e Banco de Dados Vetoriais

## Objetivo de Controle

Incorporação e armazenamentos vetoriais atuam como a "memória viva" dos sistemas de IA contemporâneos, aceitando continuamente dados fornecidos pelo usuário e os trazendo de volta para os contextos do modelo por meio da Geração Aumentada por Recuperação (RAG). Se deixada sem governança, essa memória pode vazar informações pessoalmente identificáveis (PII), violar consentimentos ou ser invertida para reconstruir o texto original. O objetivo desta família de controles é fortalecer os pipelines de memória e os bancos de dados vetoriais para que o acesso seja de privilégio mínimo, as incorporações preservem a privacidade, os vetores armazenados expirem ou possam ser revogados sob demanda, e a memória por usuário nunca contamine as solicitações ou respostas de outro usuário.

---

## C8.1 Controles de Acesso na Memória e Índices RAG

Implemente controles de acesso granulares em cada coleção de vetores.

|   #   | Descrição                                                                                                                                                                                | Nível | Função |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 8.1.1 | Verifique se as regras de controle de acesso em nível de linha/espaço de nomes restringem as operações de inserção, exclusão e consulta por locatário, coleção ou etiqueta de documento. |   1   |  D/V   |
| 8.1.2 | Verifique se as chaves de API ou os JWTs possuem claims com escopo definido (por exemplo, IDs de coleção, verbos de ação) e são rotacionados pelo menos trimestralmente.                 |   1   |  D/V   |
| 8.1.3 | Verifique se as tentativas de escalonamento de privilégios (por exemplo, consultas de similaridade entre namespaces) são detectadas e registradas em um SIEM em até 5 minutos.           |   2   |  D/V   |
| 8.1.4 | Verifique se o banco de dados vetorial registra no log o identificador do sujeito, a operação, o ID/namespace do vetor, o limite de similaridade e a contagem de resultados.             |   2   |  D/V   |
| 8.1.5 | Verifique se as decisões de acesso são testadas para falhas de bypass sempre que os motores são atualizados ou as regras de segmentação de índices são alteradas.                        |   3   |   V    |

---

## C8.2 Sanitização e Validação de Embeddings

Pré-filtre o texto para informações pessoalmente identificáveis (PII), faça a redação ou pseudonimização antes da vetorização e, opcionalmente, pós-processe as embeddings para remover sinais residuais.

|   #   | Descrição                                                                                                                                                                                            | Nível | Função |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 8.2.1 | Verifique se os dados PII e regulados são detectados por classificadores automatizados e mascarados, tokenizados ou descartados antes da incorporação.                                               |   1   |  D/V   |
| 8.2.2 | Verifique se os pipelines de incorporação rejeitam ou colocam em quarentena entradas que contenham código executável ou artefatos não UTF-8 que possam contaminar o índice.                          |   1   |   D    |
| 8.2.3 | Verifique se a sanitização de privacidade diferencial local ou métrica é aplicada aos embeddings de sentenças cuja distância para qualquer token PII conhecido cai abaixo de um limite configurável. |   2   |  D/V   |
| 8.2.4 | Verifique se a eficácia da sanitização (por exemplo, recall da redação de PII, deriva semântica) é validada pelo menos semestralmente contra corpora de referência.                                  |   2   |   V    |
| 8.2.5 | Verifique se as configurações de sanitização estão controladas por versão e se as alterações passam por revisão por pares.                                                                           |   3   |  D/V   |

---

## C8.3 Expiração, Revogação e Exclusão de Memória

A "direito ao esquecimento" do GDPR e leis semelhantes exigem a exclusão em tempo hábil; portanto, os armazenamentos vetoriais devem suportar TTLs, exclusões definitivas e tomb-stoning para que vetores revogados não possam ser recuperados ou reindexados.

|   #   | Descrição                                                                                                                                                                            | Nível | Função |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :----: |
| 8.3.1 | Verifique se cada vetor e registro de metadados possui um TTL ou um rótulo de retenção explícito respeitado por trabalhos automatizados de limpeza.                                  |   1   |  D/V   |
| 8.3.2 | Verifique se as solicitações de exclusão iniciadas pelo usuário eliminam vetores, metadados, cópias em cache e índices derivados dentro de 30 dias.                                  |   1   |  D/V   |
| 8.3.3 | Verifique se as exclusões lógicas são seguidas pela destruição criptográfica dos blocos de armazenamento, caso o hardware o suporte, ou pela destruição da chave do cofre de chaves. |   2   |   D    |
| 8.3.4 | Verifique se os vetores expirados são excluídos dos resultados da busca por vizinhos mais próximos em menos de 500 ms após a expiração.                                              |   3   |  D/V   |

---

## C8.4 Prevenir Inversão e Vazamento de Embeddings

Defesas recentes—sobreposição de ruído, redes de projeção, perturbação de neurônios de privacidade e criptografia na camada de aplicação—podem reduzir as taxas de inversão ao nível do token para menos de 5%.

|   #   | Descrição                                                                                                                                                                                    | Nível | Função |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 8.4.1 | Verificar se existe um modelo formal de ameaça que cubra ataques de inversão, de associação e de inferência de atributos, e se ele é revisado anualmente.                                    |   1   |   V    |
| 8.4.2 | Verifique se a criptografia na camada de aplicação ou a criptografia pesquisável protegem os vetores contra leituras diretas por administradores de infraestrutura ou funcionários da nuvem. |   2   |  D/V   |
| 8.4.3 | Verifique se os parâmetros de defesa (ε para DP, ruído σ, posto de projeção k) equilibram a privacidade ≥ 99% de proteção de tokens e utilidade ≤ 3% de perda de precisão.                   |   3   |   V    |
| 8.4.4 | Verifique se as métricas de resistência à inversão fazem parte dos critérios de liberação para atualizações do modelo, com orçamentos de regressão definidos.                                |   3   |  D/V   |

---

## C8.5 Aplicação de Escopo para Memória Específica do Usuário

O vazamento entre inquilinos continua sendo um dos principais riscos do RAG: consultas de similaridade filtradas incorretamente podem expor documentos privados de outro cliente.

|   #   | Descrição                                                                                                                                                                  | Nível | Função |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 8.5.1 | Verifique se cada consulta de recuperação é pós-filtrada pelo ID de locatário/usuário antes de ser passada para o prompt do LLM.                                           |   1   |  D/V   |
| 8.5.2 | Verifique se os nomes de coleções ou IDs com namespaces são salinizados por usuário ou inquilino para que os vetores não possam colidir entre diferentes escopos.          |   1   |   D    |
| 8.5.3 | Verifique se os resultados de similaridade acima de um limite de distância configurável, mas fora do escopo do chamador, são descartados e acionam alertas de segurança.   |   2   |  D/V   |
| 8.5.4 | Verifique se os testes de estresse multi-inquilino simulam consultas adversariais que tentam recuperar documentos fora do escopo e demonstrem ausência total de vazamento. |   2   |   V    |
| 8.5.5 | Verifique se as chaves de criptografia são segregadas por locatário, garantindo isolamento criptográfico mesmo que o armazenamento físico seja compartilhado.              |   3   |  D/V   |

---

## C8.6 Segurança Avançada do Sistema de Memória

Controles de segurança para arquiteturas de memória sofisticadas, incluindo memória episódica, semântica e de trabalho, com requisitos específicos de isolamento e validação.

|   #   | Descrição                                                                                                                                                                                                                                                                   | Nível | Função |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :----: |
| 8.6.1 | Verifique se os diferentes tipos de memória (episódica, semântica, de trabalho) possuem contextos de segurança isolados com controles de acesso baseados em função, chaves de criptografia separadas e padrões de acesso documentados para cada tipo de memória.            |   1   |  D/V   |
| 8.6.2 | Verifique se os processos de consolidação de memória incluem validação de segurança para prevenir a injeção de memórias maliciosas por meio de sanitização de conteúdo, verificação de fonte e checagens de integridade antes do armazenamento.                             |   2   |  D/V   |
| 8.6.3 | Verifique se as consultas de recuperação de memória são validadas e higienizadas para evitar a extração de informações não autorizadas por meio da análise de padrões de consulta, aplicação de controle de acesso e filtragem de resultados.                               |   2   |  D/V   |
| 8.6.4 | Verifique se os mecanismos de esquecimento de memória excluem informações sensíveis de forma segura com garantias de apagamento criptográfico utilizando exclusão de chave, sobregravação múltipla ou exclusão segura baseada em hardware com certificados de verificação.  |   3   |  D/V   |
| 8.6.5 | Verifique se a integridade do sistema de memória é continuamente monitorada para modificações ou corrupções não autorizadas por meio de somas de verificação, registros de auditoria e alertas automatizados quando o conteúdo da memória mudar fora das operações normais. |   3   |  D/V   |

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

