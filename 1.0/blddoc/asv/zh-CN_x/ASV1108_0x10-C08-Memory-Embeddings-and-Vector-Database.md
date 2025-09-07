# C8 存储器、嵌入表示与向量数据库安全

## 控制目标

嵌入和向量存储作为当代人工智能系统的“实时记忆”，不断接受用户提供的数据，并通过检索增强生成（RAG）将其反馈到模型上下文中。如果不加以管理，这种记忆可能会泄露个人身份信息（PII）、违反同意，或被反转以重构原始文本。该控制类别的目标是强化记忆流程和向量数据库，使访问权限最小化，嵌入具备隐私保护，存储的向量能过期或按需撤销，并且每个用户的记忆不会污染其他用户的提示或生成内容。

---

## C8.1 对内存和RAG索引的访问控制

对每个向量集合实施细粒度访问控制。

|   #   | 描述                                                     | 级别  | 角色  |
| :---: | ------------------------------------------------------ | :-: | :-: |
| 8.1.1 | 验证行级/命名空间级访问控制规则是否限制了每个租户、集合或文档标签的插入、删除和查询操作。          |  1  | D/V |
| 8.1.2 | 验证 API 密钥或 JWT 是否携带限定的声明（例如，集合 ID、操作动词），并且至少每季度进行一次轮换。 |  1  | D/V |
| 8.1.3 | 验证特权提升尝试（例如跨命名空间的相似性查询）是否在5分钟内被检测到并记录到SIEM中。           |  2  | D/V |
| 8.1.4 | 验证向量数据库的审计日志中是否记录了主体标识符、操作、向量 ID/命名空间、相似度阈值和结果数量。      |  2  | D/V |
| 8.1.5 | 每当引擎升级或索引分片规则变化时，验证访问决策是否存在绕过缺陷。                       |  3  |  V  |

---

## C8.2 嵌入的清理与验证

预先筛查文本中的个人身份信息（PII），在向量化之前进行删除或假名处理，并可选择在嵌入后处理阶段去除残留信号。

|   #   | 描述                                                 | 级别  | 角色  |
| :---: | -------------------------------------------------- | :-: | :-: |
| 8.2.1 | 验证通过自动分类器检测到的个人身份信息（PII）和受监管数据，并在嵌入处理前进行掩码、标记化或丢弃。 |  1  | D/V |
| 8.2.2 | 验证嵌入管道是否拒绝或隔离包含可执行代码或非UTF-8不良数据的输入，这些内容可能会污染索引。    |  1  |  D  |
| 8.2.3 | 验证对与任何已知PII令牌距离低于可配置阈值的句子嵌入应用了本地或度量差分隐私清理。         |  2  | D/V |
| 8.2.4 | 验证清理效果（例如，个人身份信息消除的召回率、语义漂移）至少每半年通过基准语料库进行验证。      |  2  |  V  |
| 8.2.5 | 验证清理配置是否实行版本控制，并确保变更经过同级审查。                        |  3  | D/V |

---

## C8.3 内存到期、撤销与删除

GDPR“被遗忘权”和类似法律要求及时删除；因此，向量存储必须支持TTL、硬删除和墓碑机制，以确保被撤销的向量无法被恢复或重新索引。

|   #   | 描述                                             | 级别  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 8.3.1 | 验证每个向量和元数据记录是否具有由自动清理任务执行的TTL或明确保留标签。          |  1  | D/V |
| 8.3.2 | 确认用户发起的删除请求在30天内清除向量、元数据、缓存副本和派生索引。            |  1  | D/V |
| 8.3.3 | 验证逻辑删除后，如果硬件支持，则紧随其后进行存储块的加密销毁，或者通过密钥库密钥销毁来实现。 |  2  |  D  |
| 8.3.4 | 验证过期向量在过期后500毫秒内被排除在最近邻搜索结果之外。                 |  3  | D/V |

---

## C8.4 防止嵌入反演与泄露

最近的防御措施——噪声叠加、投影网络、隐私神经元扰动和应用层加密——可以将令牌级别的反演率降低到5%以下。

|   #   | 描述                                                                 | 级别  | 角色  |
| :---: | ------------------------------------------------------------------ | :-: | :-: |
| 8.4.1 | 确认存在涵盖反演攻击、成员攻击和属性推断攻击的正式威胁模型，并且该模型每年进行审查。                         |  1  |  V  |
| 8.4.2 | 验证应用层加密或可搜索加密能否保护向量，防止基础设施管理员或云工作人员直接读取。                           |  2  | D/V |
| 8.4.3 | 验证防御参数（DP 的 ε，噪声 σ，投影秩 k）是否在隐私保护 ≥ 99% 令牌保护和效用损失 ≤ 3% 准确率下降之间取得平衡。 |  3  |  V  |
| 8.4.4 | 验证逆转稳健性指标是否作为模型更新的发布门控的一部分，并定义回归预算。                                |  3  | D/V |

---

## C8.5 用户特定内存的范围强制执行

跨租户泄漏仍然是RAG的主要风险：未正确过滤的相似性查询可能会暴露其他客户的私人文档。

|   #   | 描述                                               | 级别  | 角色  |
| :---: | ------------------------------------------------ | :-: | :-: |
| 8.5.1 | 验证每个检索查询在传递给大语言模型提示之前，是否通过租户/用户ID进行了后过滤。         |  1  | D/V |
| 8.5.2 | 验证集合名称或命名空间ID是否针对每个用户或租户进行了加盐处理，以防止向量在不同范围内发生冲突。 |  1  |  D  |
| 8.5.3 | 验证超过可配置距离阈值但超出调用者范围的相似性结果被丢弃并触发安全警报。             |  2  | D/V |
| 8.5.4 | 验证多租户压力测试是否模拟了试图检索超出范围文档的对抗性查询，并展示零泄露情况。         |  2  |  V  |
| 8.5.5 | 验证加密密钥是否按租户隔离，确保即使物理存储共享也能实现密码学隔离。               |  3  | D/V |

---

## C8.6 高级内存系统安全

针对复杂内存架构（包括情景记忆、语义记忆和工作记忆）具有特定隔离和验证要求的安全控制。

|   #   | 描述                                                                          | 级别  | 角色  |
| :---: | --------------------------------------------------------------------------- | :-: | :-: |
| 8.6.1 | 验证不同类型的记忆（情景记忆、语义记忆、工作记忆）是否具有隔离的安全上下文，配备基于角色的访问控制、独立的加密密钥，以及为每种记忆类型记录的访问模式。 |  1  | D/V |
| 8.6.2 | 验证记忆整合过程包括安全验证，以通过内容清理、来源验证和存储前的完整性检查，防止恶意记忆的注入。                            |  2  | D/V |
| 8.6.3 | 验证内存检索查询是否经过验证和清理，以防止通过查询模式分析、访问控制执行和结果过滤提取未授权的信息。                          |  2  | D/V |
| 8.6.4 | 验证内存遗忘机制是否通过密钥删除、多遍覆盖或带有验证证书的硬件安全删除，以密码擦除保证安全地删除敏感信息。                       |  3  | D/V |
| 8.6.5 | 验证通过校验和、审计日志以及当内存内容在正常操作之外发生变化时的自动警报，持续监控内存系统的完整性是否遭到未经授权的修改或损坏。            |  3  | D/V |

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

