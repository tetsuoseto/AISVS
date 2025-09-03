# Segurança de Memória C8, Embeddings e Banco de Dados de Vetores

## Objetivo de Controle

Embeddings e bancos de vetores atuam como a "memória ao vivo" dos sistemas de IA contemporâneos, aceitando continuamente dados fornecidos pelo usuário e trazendo-os de volta aos contextos do modelo por meio da Geração Aumentada por Recuperação (RAG). Se não forem governados, essa memória pode vazar PII, violar consentimento ou ser invertida para reconstruir o texto original. O objetivo desta família de controles é fortalecer pipelines de memória e bancos de vetores para que o acesso seja de privilégio mínimo, embeddings sejam privacidade-resguardados, vetores armazenados expirem ou possam ser revogados sob demanda, e a memória por usuário nunca contamine os prompts ou conclusões de outro usuário.

---

## C8.1 Controles de Acesso à Memória & Índices RAG

Impor stricter controles de acesso detalhados em cada coleção de vetores.

|   #   | Descrição                                                                                                                                                                         | Nível | Papel |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.1.1 | Verifique se as regras de controle de acesso a nível de linha/namespace restringem as operações de inserir, excluir e consultar por locatário, coleção ou etiqueta de documento.  |   1   |  D/V  |
| 8.1.2 | Verifique se as chaves de API ou JWTs carregam declarações de escopo (por exemplo, IDs de coleção, verbos de ação) e são rotacionados pelo menos a cada trimestre.                |   1   |  D/V  |
| 8.1.3 | Verifique se as tentativas de escalonamento de privilégios (por exemplo, consultas de similaridade entre namespaces) são detectadas e registradas em um SIEM dentro de 5 minutos. |   2   |  D/V  |
| 8.1.4 | Verifique se o log de auditoria do banco de dados vetorial registra o identificador do sujeito, operação, ID/namespace do vetor, limiar de similaridade e contagem de resultados. |   2   |  D/V  |
| 8.1.5 | Verifique se as decisões de acesso são testadas quanto a falhas de bypass sempre que os mecanismos são atualizados ou as regras de sharding de índice são alteradas.              |   3   |   V   |

---

## C8.2 Sanitização e Validação de Embeddings

Pré-selecionar o texto para PII, redigir ou pseudonimizar antes da vetorização, e opcionalmente pós-processar as embeddings para remover sinais residuais.

|   #   | Descrição                                                                                                                                                                                                  | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.2.1 | Verifique se PII e dados regulamentados são detectados por meio de classificadores automatizados e mascarados, tokenizados ou descartados antes de serem incorporados.                                     |   1   |  D/V  |
| 8.2.2 | Verifique se os pipelines de embedamento rejeitam ou colocam em quarentena entradas que contenham código executável ou artefatos não-UTF-8 que possam contaminar o índice.                                 |   1   |   D   |
| 8.2.3 | Verifique se a sanitização local ou métrica de privacidade diferencial foi aplicada às embedagens de sentença cujas distâncias para qualquer token de PII conhecido caem abaixo de um limiar configurável. |   2   |  D/V  |
| 8.2.4 | Verifique se a eficácia da sanitização (por exemplo, recall da redação de PII, drift semântico) é validada pelo menos semestralmente usando corpora de referência.                                         |   2   |   V   |
| 8.2.5 | Verifique se as configurações de sanitização estão sob controle de versão e se as alterações passam por revisão por pares.                                                                                 |   3   |  D/V  |

---

## C8.3 Expiração, Revogação e Exclusão de Memória

O GDPR "direito ao esquecimento" e leis similares exigem exclusão oportuna; portanto, os armazenamentos vetoriais devem suportar TTLs, exclusões permanentes e tombstoning para que vetores revogados não possam ser recuperados ou reindexados.

|   #   | Descrição                                                                                                                                                                           | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.3.1 | Verifique se cada vetor e registro de metadados possui um TTL ou rótulo de retenção explícito, respeitado pelos trabalhos de limpeza automatizados.                                 |   1   |  D/V  |
| 8.3.2 | Verifique se as solicitações de exclusão iniciadas pelo usuário eliminam vetores, metadados, cópias em cache e índices derivados dentro de 30 dias.                                 |   1   |  D/V  |
| 8.3.3 | Verifique se as exclusões lógicas são seguidas pela destruição criptográfica dos blocos de armazenamento, se o hardware suportar, ou pela destruição da chave no coffers de chaves. |   2   |   D   |
| 8.3.4 | Verifique se vetores expirados são excluídos dos resultados da busca pelos vizinhos mais próximos em menos de 500 ms após a expiração.                                              |   3   |  D/V  |

---

## C8.4 Prevenir Inversão de Embedding & Vazamento

Defesas recentes—superposição de ruído, redes de projeção, perturbação de neurônios de privacidade e criptografia na camada de aplicação—podem reduzir as taxas de inversão ao nível de token abaixo de 5%.

|   #   | Descrição                                                                                                                                                                      | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.4.1 | Verifique se existe um modelo formal de ameaça que cobre ataques de inversão, de pertencimento e de inferência de atributos e se ele é revisado anualmente.                    |   1   |   V   |
| 8.4.2 | Verifique se a criptografia de camada de aplicação ou criptografia pesquisável protegem os vetores de leitura direta por administradores de infraestrutura ou equipe de nuvem. |   2   |  D/V  |
| 8.4.3 | Verifique se os parâmetros de defesa (ε para DP, ruído σ, rank de projeção k) equilibram privacidade ≥ 99 % proteção do token e utilidade ≤ 3 % perda de precisão.             |   3   |   V   |
| 8.4.4 | Verifique se as métricas de resiliência à inversão fazem parte das portas de liberação para atualizações de modelos, com orçamentos de regressão definidos.                    |   3   |  D/V  |

---

## C8.5 Aplicação de Escopo para Memória Específica do Usuário

Vazamentos entre locatários continuam sendo um risco principal de RAG: consultas de similaridade filtradas de forma inadequada podem revelar documentos privados de outro cliente.

|   #   | Descrição                                                                                                                                                                | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.5.1 | Verifique se cada consulta de recuperação é filtrada posteriormente pelo ID do inquilino/usuário antes de ser encaminhada ao prompt do LLM.                              |   1   |  D/V  |
| 8.5.2 | Verifique se os nomes de coleções ou IDs de namespace são salteados por usuário ou locatário, para que os vetores não possam colidir entre escopos.                      |   1   |   D   |
| 8.5.3 | Verifique se os resultados de similaridade acima de um limiar de distância configurável, mas fora do escopo do chamador, são descartados e acionam alertas de segurança. |   2   |  D/V  |
| 8.5.4 | Verifique se os testes de estresse multi-inquilino simulam consultas adversariais tentando recuperar documentos fora do escopo e demonstre ausência de vazamento.        |   2   |   V   |
| 8.5.5 | Verifique se as chaves de criptografia estão segregadas por locatário, garantindo isolamento criptográfico mesmo que o armazenamento físico seja compartilhado.          |   3   |  D/V  |

---

## C8.6 Segurança Avançada de Sistemas de Memória

Controles de segurança para arquiteturas de memória sofisticadas, incluindo memória episódica, semântica e de trabalho, com requisitos específicos de isolamento e validação.

|   #   | Descrição                                                                                                                                                                                                                                                                                  | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.6.1 | Verifique se os diferentes tipos de memória (episódica, semântica, de trabalho) possuem contextos de segurança isolados com controles de acesso baseados em papéis, chaves de criptografia separadas e padrões de acesso documentados para cada tipo de memória.                           |   1   |  D/V  |
| 8.6.2 | Verifique se os processos de consolidação da memória incluem validação de segurança para evitar a injeção de memórias maliciosas por meio de sanitização de conteúdo, verificação da fonte e verificações de integridade antes do armazenamento.                                           |   2   |  D/V  |
| 8.6.3 | Verifique se as consultas de recuperação de memória são validadas e sanitizadas para prevenir a extração de informações não autorizadas por meio de análise de padrão de consulta, aplicação de controle de acesso e filtragem de resultados.                                              |   2   |  D/V  |
| 8.6.4 | Verifique se os mecanismos de esquecimento de memória excluem de forma segura informações confidenciais, garantindo eliminação criptográfica usando apagamento de chave, sobrescrita múltipla ou exclusão segura baseada em hardware com certificados de verificação.                      |   3   |  D/V  |
| 8.6.5 | Verifique se a integridade do sistema de memória está sendo monitorada continuamente para detectar modificações ou corrupção não autorizadas através de somas de verificação, registros de auditoria e alertas automatizados quando o conteúdo da memória muda fora das operações normais. |   3   |  D/V  |

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

