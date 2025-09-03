# C8 内存、嵌入与向量数据库安全

## 控制目标

嵌入向量与向量存储充当当代 AI 系统的“实时记忆”，持续接受用户提供的数据，并通过检索增强生成（RAG）将其重新引入到模型上下文中。若不加治理，这些记忆可能泄露个人身份信息（PII）、侵犯同意，或被反向利用以重构原始文本。本控制族的目标是对内存管线和向量数据库进行加固，使访问遵循最小权限原则，嵌入向量实现隐私保护，存储的向量到期或可按需撤销，且每个用户的记忆不会污染其他用户的提示或完成内容。

---

## C8.1 内存 & RAG 指标的访问控制

对每个向量集合实施细粒度访问控制。

|   #   | 描述                                                         | 等级  | 角色  |
| :---: | ---------------------------------------------------------- | :-: | :-: |
| 8.1.1 | 验证行级和命名空间级访问控制规则是否对按租户、集合或文档标签的插入、删除和查询操作进行限制。             |  1  | D/V |
| 8.1.2 | 验证 API 密钥或 JWTs 是否携带具有作用域的声明（例如集合 ID、操作动词），并且至少每季度轮换一次。    |  1  | D/V |
| 8.1.3 | 验证 是否 权限升级 尝试（例如，跨命名空间相似性查询） 是否 被 检测 并 记录 到 SIEM 在 5 分钟 内。 |  2  | D/V |
| 8.1.4 | 验证向量数据库的审计日志是否记录主体标识符、操作、向量 ID/命名空间、相似性阈值和结果计数。            |  2  | D/V |
| 8.1.5 | 请确保在引擎升级或 index-sharding 规则变更时，对访问控制决策进行绕过漏洞测试。            |  3  |  V  |

---

## C8.2 嵌入净化与验证

在向量化之前对文本进行 PII 的预筛查、对敏感信息进行涂黑或伪匿名化处理，并可选择对嵌入向量进行后处理以去除残留信号。

|   #   | 描述                                                                      | 等级  | 角色  |
| :---: | ----------------------------------------------------------------------- | :-: | :-: |
| 8.2.1 | 验证 个人身份信息 和 受监管数据 是否 通过 自动 分类器 检测 到，并 在 嵌入 前 进行 屏蔽、 令牌化 或 丢弃。           |  1  | D/V |
| 8.2.2 | 验证嵌入管线是否会拒绝或对包含可执行代码或非 UTF-8 片段的输入进行隔离，这些输入可能污染索引。                      |  1  |  D  |
| 8.2.3 | 验证对句子嵌入应用的本地差分-隐私净化（或度量差分-隐私净化）是否被应用于与任何已知个人身份信息（PII）令牌的距离低于可配置阈值的句子嵌入。 |  2  | D/V |
| 8.2.4 | 请验证脱敏有效性（例如，PII 脱敏的召回率、语义漂移）是否至少每六个月针对基准语料库进行验证。                        |  2  |  V  |
| 8.2.5 | 确保净化配置处于版本控制之中，变更需经过同行评审。                                               |  3  | D/V |

---

## C8.3 记忆到期、撤销与删除

GDPR 的“被遗忘权”和类似法律要求及时删除；因此，向量存储必须支持 TTL（生存时间）、硬删除和墓碑化处理，以确保被撤销的向量无法被恢复或重新索引。

|   #   | 描述                                                       | 等级  | 角色  |
| :---: | -------------------------------------------------------- | :-: | :-: |
| 8.3.1 | 请验证每个向量及其元数据记录是否携带 TTL 或显式保留标签，并且自动清理作业会遵循该标签。           |  1  | D/V |
| 8.3.2 | 验证用户发起的删除请求在 30 天内清除向量、元数据、缓存副本和派生索引。                    |  1  | D/V |
| 8.3.3 | 验证逻辑删除在硬件支持的情况下是否随之对存储块进行加密擦除；如果硬件不支持，则通过密钥保管库中的密钥销毁来实现。 |  2  |  D  |
| 8.3.4 | 验证在过期后不到 500 毫秒内，已过期的向量是否会被排除在最近邻搜索结果之外。                 |  3  | D/V |

---

## C8.4 防止嵌入反演与信息泄露

最近的防御措施—噪声叠加、投影网络、隐私神经元扰动，以及应用层加密—可以将令牌级反演率降低到5%以下。

|   #   | 描述                                                              | 等级  | 角色  |
| :---: | --------------------------------------------------------------- | :-: | :-: |
| 8.4.1 | 请核实是否存在覆盖反演攻击、成员推断攻击和属性推断攻击的正式威胁模型，并且每年对其进行审查。                  |  1  |  V  |
| 8.4.2 | 验证应用层加密或可搜索加密是否能够防止向量被基础设施管理员或云端工作人员直接读取。                       |  2  | D/V |
| 8.4.3 | 验证防御参数（ε 对 DP，噪声 σ，投影秩 k）在隐私 ≥ 99 % 的令牌保护和效用 ≤ 3 % 的精度损失之间达到平衡。 |  3  |  V  |
| 8.4.4 | 请验证在模型更新的发布门控中，是否包含对模型反演攻击的鲁棒性指标，并已定义回归预算。                      |  3  | D/V |

---

## C8.5 作用域 强制 针对 用户特定 内存

跨租户泄漏仍然是 RAG 风险中的主要风险之一： 未正确过滤的相似性查询可能暴露另一位客户的私有文档。

|   #   | 描述                                             | 等级  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 8.5.1 | 请验证每个检索查询在传递给 LLM 提示之前，是否已按租户/用户 ID 进行事后过滤。    |  1  | D/V |
| 8.5.2 | 验证集合名称或带命名空间的ID是否按每个用户或租户进行加盐，以使跨作用域的向量不会发生碰撞。 |  1  |  D  |
| 8.5.3 | 验证在可配置的距离阈值之上但超出调用方的范围的相似性结果将被丢弃并触发安全警报。       |  2  | D/V |
| 8.5.4 | 验证多租户压力测试是否能够模拟对抗性查询，试图检索超出范围的文档，并证明零泄漏。       |  2  |  V  |
| 8.5.5 | 验证每个租户的加密密钥是否已分离，以确保即使物理存储被共享，也能实现密码学隔离。       |  3  | D/V |

---

## C8.6 高级内存系统安全

针对复杂内存架构的安全控制，包括事件记忆、语义记忆和工作记忆，并具备特定的隔离和验证要求。

|   #   | 描述                                                                            | 等级  | 角色  |
| :---: | ----------------------------------------------------------------------------- | :-: | :-: |
| 8.6.1 | 验证不同的记忆类型（事件记忆、语义记忆、工作记忆）是否具备彼此隔离的安全上下文、基于角色的访问控制、独立的加密密钥，以及针对每种记忆类型的文档化访问模式。 |  1  | D/V |
| 8.6.2 | 验证记忆巩固过程是否包含安全性验证，以在存储之前通过内容净化、来源验证和完整性检查来防止恶意记忆的注入。                          |  2  | D/V |
| 8.6.3 | 验证记忆检索查询是否已经过验证并净化，以防止通过查询模式分析、访问控制执行和结果过滤提取未授权信息。                            |  2  | D/V |
| 8.6.4 | 验证内存擦除机制是否能够在具备密码学擦除保证的前提下安全删除敏感信息，方法包括使用密钥删除、多次覆盖，或带有验证证书的基于硬件的安全删除。         |  3  | D/V |
| 8.6.5 | 验证内存系统的完整性是否持续受到监控，以防止未经授权的修改或损坏，监控方式包括校验和、审计日志，以及在内存内容超出正常操作范围时触发的自动警报。      |  3  | D/V |

---

## 参考文献

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

