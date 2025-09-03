# Memória C8, Representações Vetoriais e Segurança de Banco de Dados Vetorial

## Objetivo de Controle

Representações vetoriais e bancos de vetores atuam como a “memória ao vivo” dos sistemas de IA contemporâneos, aceitando continuamente dados fornecidos pelos usuários e retornando-os aos contextos do modelo por meio da Geração Aumentada por Recuperação (RAG). Se ficar sem governança, essa memória pode vazar PII, violar o consentimento ou ser invertida para reconstruir o texto original. O objetivo desta família de controles é fortalecer os pipelines de memória e os bancos de vetores, de modo que o acesso tenha privilégio mínimo, as representações vetoriais preservem a privacidade, os vetores armazenados expirem ou possam ser revogados sob demanda, e a memória por usuário nunca contamine as solicitações ou as saídas de outro usuário.

---

## C8.1 Controles de Acesso à Memória e aos Índices RAG

Implemente controles de acesso granulares em todas as coleções de vetores.

|   #   | Descrição                                                                                                                                                                                      | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.1.1 | Verifique se as regras de controle de acesso em nível de linha ou espaço de nomes restringem as operações de inserção, exclusão e consulta por inquilino, coleção ou tag de documento.         |   1   |  D/V  |
| 8.1.2 | Verifique se as chaves de API ou JWTs contêm declarações com escopo (por exemplo, identificadores de coleção, verbos de ação) e são rotacionadas pelo menos a cada trimestre.                  |   1   |  D/V  |
| 8.1.3 | Verifique se as tentativas de elevação de privilégios (por exemplo, consultas de similaridade entre namespaces) são detectadas e registradas em um SIEM dentro de 5 minutos.                   |   2   |  D/V  |
| 8.1.4 | Verifique se os logs de auditoria do banco de dados de vetores registram o identificador do sujeito, a operação, o ID/namespace do vetor, o limiar de similaridade e a contagem de resultados. |   2   |  D/V  |
| 8.1.5 | Verifique se as decisões de acesso são testadas quanto a falhas de bypass sempre que os motores são atualizados ou as regras de particionamento de índices mudam.                              |   3   |   V   |

---

## C8.2 Sanitização e Validação de Embeddings

Pré-filtre o texto para PII; remova ou adote pseudonimização antes da vetorização; e, opcionalmente, pós-processe os embeddings para eliminar sinais residuais.

|   #   | Descrição                                                                                                                                                                                                                                    | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.2.1 | Verifique se PII e dados sujeitos à regulamentação são detectados por classificadores automatizados e mascarados, tokenizados ou descartados antes do pré-embedding.                                                                         |   1   |  D/V  |
| 8.2.2 | Verifique se os pipelines de embedding rejeitam ou colocam em quarentena entradas contendo código executável ou artefatos que não estejam em UTF-8 e que possam contaminar o índice.                                                         |   1   |   D   |
| 8.2.3 | Verifique se a sanitização de privacidade diferencial local ou de privacidade diferencial métrica é aplicada às representações vetoriais de sentenças cuja distância até qualquer token PII conhecido fica abaixo de um limiar configurável. |   2   |  D/V  |
| 8.2.4 | Verifique se a eficácia da sanitização (por exemplo, recall da remoção de PII, deriva semântica) é validada pelo menos semestralmente contra corpora de referência.                                                                          |   2   |   V   |
| 8.2.5 | Verifique se as configurações de sanitização estão sob controle de versão e se as alterações passam por revisão por pares.                                                                                                                   |   3   |  D/V  |

---

## C8.3 Expiração da Memória, Revogação e Exclusão

GDPR "direito ao esquecimento" e leis similares exigem apagamento em tempo hábil; os bancos de vetores devem, portanto, suportar TTLs, exclusões permanentes e tomb-stoning para que vetores revogados não possam ser recuperados ou reindexados.

|   #   | Descrição                                                                                                                                                                                  | Nível | Papel |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---: | :---: |
| 8.3.1 | Verifique se cada vetor e registro de metadados carrega um TTL ou uma etiqueta de retenção explícita, que seja respeitada pelos trabalhos de limpeza automatizados.                        |   1   |  D/V  |
| 8.3.2 | Verifique se as solicitações de exclusão iniciadas pelo usuário purgam vetores, metadados, cópias em cache e índices derivados no prazo de 30 dias.                                        |   1   |  D/V  |
| 8.3.3 | Verifique se as exclusões lógicas são seguidas pela trituração criptográfica dos blocos de armazenamento, se o hardware oferecer suporte a isso, ou pela destruição da chave no Key Vault. |   2   |   D   |
| 8.3.4 | Verifique se vetores expirados são excluídos dos resultados da busca de vizinhos mais próximos em menos de 500 ms após a expiração.                                                        |   3   |  D/V  |

---

## C8.4 Prevenir a inversão de embeddings e vazamento de dados

Defesas recentes—superposição de ruído, redes de projeção, perturbação de neurônios de privacidade e criptografia da camada de aplicação—podem reduzir as taxas de inversão em nível de token para abaixo de 5%.

|   #   | Descrição                                                                                                                                                                                    | Nível | Papel |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.4.1 | Verifique se existe um modelo de ameaça formal que abranja ataques de inversão, ataques de inferência de pertencimento e ataques de inferência de atributos, e se ele é revisado anualmente. |   1   |   V   |
| 8.4.2 | Verifique se a criptografia na camada de aplicação ou a criptografia pesquisável protege os vetores contra leituras diretas por administradores de infraestrutura ou pela equipe de nuvem.   |   2   |  D/V  |
| 8.4.3 | Verifique que os parâmetros de defesa (ε para DP, ruído σ, posto de projeção k) equilibrem a privacidade ≥ 99 % com proteção de token e a utilidade ≤ 3 % com perda de precisão.             |   3   |   V   |
| 8.4.4 | Verifique se as métricas de resiliência à inversão de modelo fazem parte dos portões de liberação para atualizações de modelo, com orçamentos de regressão definidos.                        |   3   |  D/V  |

---

## C8.5 Imposição do Escopo para Memória Específica do Usuário

Vazamento entre inquilinos continua sendo um dos maiores riscos de RAG: consultas de similaridade filtradas de forma inadequada podem expor documentos privados de outro cliente.

|   #   | Descrição                                                                                                                                                              | Nível | Papel |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.5.1 | Verifique se toda consulta de recuperação é filtrada pelo ID do inquilino/usuário antes de ser encaminhada para o prompt do LLM.                                       |   1   |  D/V  |
| 8.5.2 | Verifique se os nomes de coleção ou IDs com espaço de nomes recebem um sal por usuário ou por inquilino, para que os vetores não entrem em colisão entre escopos.      |   1   |   D   |
| 8.5.3 | Verifique que os resultados de similaridade acima do limiar de distância configurável, mas fora do escopo do chamador, sejam descartados e gerem alertas de segurança. |   2   |  D/V  |
| 8.5.4 | Verifique que os testes de estresse multi-tenant simulam consultas adversariais que tentam recuperar documentos fora do escopo e demonstrem zero vazamento.            |   2   |   V   |
| 8.5.5 | Verifique se as chaves criptográficas estão segregadas por inquilino, garantindo isolamento criptográfico mesmo que o armazenamento físico seja compartilhado.         |   3   |  D/V  |

---

## C8.6 Segurança Avançada do Sistema de Memória

Controles de segurança para arquiteturas de memória sofisticadas, incluindo memória episódica, memória semântica e memória de trabalho, com requisitos específicos de isolamento e validação.

|   #   | Descrição                                                                                                                                                                                                                                                                     | Nível | Papel |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---: | :---: |
| 8.6.1 | Verifique se os diferentes tipos de memória (episódica, semântica, de trabalho) possuem contextos de segurança isolados com controles de acesso baseados em papéis, chaves de criptografia separadas e padrões de acesso documentados para cada tipo de memória.              |   1   |  D/V  |
| 8.6.2 | Verifique se os processos de consolidação de memória incluem validação de segurança para impedir a injeção de memórias maliciosas por meio de sanitização de conteúdo, verificação de origem e checagens de integridade antes do armazenamento.                               |   2   |  D/V  |
| 8.6.3 | Verifique se as consultas de recuperação de memória são validadas e sanitizadas para impedir a extração de informações não autorizadas por meio de análise de padrões de consulta, aplicação do controle de acesso e filtragem de resultados.                                 |   2   |  D/V  |
| 8.6.4 | Verifique se os mecanismos de apagamento de memória eliminam com segurança informações sensíveis com garantias de eliminação criptográfica, usando exclusão de chaves, sobrescrita em várias passadas ou exclusão segura baseada em hardware com certificados de verificação. |   3   |  D/V  |
| 8.6.5 | Verifique se a integridade do sistema de memória é monitorada continuamente quanto a modificações não autorizadas ou corrupção, por meio de checksums, logs de auditoria e alertas automatizados quando o conteúdo da memória muda fora das operações normais.                |   3   |  D/V  |

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

