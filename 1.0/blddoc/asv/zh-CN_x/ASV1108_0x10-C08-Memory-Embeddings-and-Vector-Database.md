# C8 存储器、嵌入和向量数据库安全

## 控制目标

嵌入和向量存储作为当代人工智能系统的“实时记忆”，不断接收用户提供的数据，并通过检索增强生成（RAG）将其重新呈现在模型上下文中。如果不加以管理，这种记忆可能泄露个人身份信息（PII）、违反用户同意，或者被逆向工程以重建原始文本。该控制类别的目标是强化记忆管道和向量数据库，确保访问权限最小化，嵌入具有隐私保护功能，存储的向量具有过期机制或能够按需撤销，并且每个用户的记忆绝不污染其他用户的提示或生成内容。

---

## C8.1 内存和RAG索引的访问控制

对每个向量集合实施细粒度访问控制。

|   #   | 描述                                                   | 等级  | 角色  |
| :---: | ---------------------------------------------------- | :-: | :-: |
| 8.1.1 | 验证行/命名空间级访问控制规则是否限制每个租户、集合或文档标签的插入、删除和查询操作。          |  1  | D/V |
| 8.1.2 | 验证 API 密钥或 JWT 是否包含作用域声明（例如，集合 ID、操作动词），并且至少每季度轮换一次。 |  1  | D/V |
| 8.1.3 | 验证权限提升尝试（例如，跨命名空间的相似性查询）是否在5分钟内被检测并记录到SIEM中。         |  2  | D/V |
| 8.1.4 | 验证向量数据库审计日志是否记录了主体标识符、操作、向量ID/命名空间、相似度阈值和结果数量。       |  2  | D/V |
| 8.1.5 | 确保在引擎升级或索引分片规则变更时，访问决策经过旁路缺陷测试。                      |  3  |  V  |

---

## C8.2 嵌入清理与验证

在向量化之前，对文本进行预筛查以识别个人身份信息（PII），并进行遮盖或假名化，必要时对嵌入进行后处理以去除残留信号。

|   #   | 描述                                                  | 等级  | 角色  |
| :---: | --------------------------------------------------- | :-: | :-: |
| 8.2.1 | 验证通过自动分类器检测到的个人身份信息（PII）和受监管数据是否在嵌入前被屏蔽、标记化或丢弃。     |  1  | D/V |
| 8.2.2 | 验证嵌入管道是否拒绝或隔离包含可执行代码或非 UTF-8 代码片段的输入，这些代码片段可能会污染索引。 |  1  |  D  |
| 8.2.3 | 验证对与任何已知个人身份信息（PII）标记的距离低于可配置阈值的句子嵌入应用了局部或度量差分隐私清理。 |  2  | D/V |
| 8.2.4 | 验证清理效果（例如，个人身份信息去除的召回率、语义漂移）是否至少每半年针对基准语料库进行一次验证。   |  2  |  V  |
| 8.2.5 | 验证清理配置是否受到版本控制，并且更改经过同行评审。                          |  3  | D/V |

---

## C8.3 内存过期、撤销与删除

GDPR中的“被遗忘权”及类似法律要求及时删除；因此，向量存储必须支持TTL、硬删除和墓碑标记，以确保被撤销的向量无法恢复或重新索引。

|   #   | 描述                                          | 等级  | 角色  |
| :---: | ------------------------------------------- | :-: | :-: |
| 8.3.1 | 验证每个向量和元数据记录是否包含由自动清理任务遵守的TTL或显式保留标签。       |  1  | D/V |
| 8.3.2 | 验证用户发起的删除请求在30天内清除向量、元数据、缓存副本和派生索引。         |  1  | D/V |
| 8.3.3 | 验证逻辑删除后，如果硬件支持，应进行存储块的加密销毁；否则应通过密钥库密钥销毁来完成。 |  2  |  D  |
| 8.3.4 | 验证过期向量在过期后500毫秒内从最近邻搜索结果中被排除。               |  3  | D/V |

---

## C8.4 防止嵌入反演和泄露

最近的防御措施——噪声叠加、投影网络、隐私神经扰动和应用层加密——可以将令牌级反转率降低到5%以下。

|   #   | 描述                                                   | 等级  | 角色  |
| :---: | ---------------------------------------------------- | :-: | :-: |
| 8.4.1 | 验证是否存在涵盖反演攻击、成员资格攻击和属性推断攻击的正式威胁模型，并且该模型每年进行审核。       |  1  |  V  |
| 8.4.2 | 验证应用层加密或可搜索加密是否能防止基础设施管理员或云工作人员直接读取向量。               |  2  | D/V |
| 8.4.3 | 验证防御参数（DP的ε值，噪声σ，投影秩k）在隐私保护≥99%令牌保护和效用≤3%准确率损失之间的平衡。 |  3  |  V  |
| 8.4.4 | 验证反转抗性指标是否作为模型更新发布门控的一部分，同时定义回归预算。                   |  3  | D/V |

---

## C8.5 针对用户特定内存的范围强制执行

跨租户泄露仍然是RAG的主要风险：不当过滤的相似性查询可能会暴露其他客户的私人文档。

|   #   | 描述                                                  | 等级  | 角色  |
| :---: | --------------------------------------------------- | :-: | :-: |
| 8.5.1 | 在传递给大型语言模型（LLM）提示之前，确保每个检索查询都经过租户/用户ID的后过滤。         |  1  | D/V |
| 8.5.2 | 验证集合名称或命名空间 ID 是否针对每个用户或租户进行了加盐处理，以确保向量在不同作用域间不会冲突。 |  1  |  D  |
| 8.5.3 | 验证超出调用者范围但超过可配置距离阈值的相似性结果是否被丢弃并触发安全警报。              |  2  | D/V |
| 8.5.4 | 验证多租户压力测试模拟了试图检索超出范围文档的对抗性查询，并且证明没有信息泄露。            |  2  |  V  |
| 8.5.5 | 验证加密密钥是否按租户隔离，确保即使物理存储共享也能实现密码学隔离。                  |  3  | D/V |

---

## C8.6 高级内存系统安全

针对复杂内存架构（包括情景记忆、语义记忆和工作记忆）具有特定隔离和验证要求的安全控制。

|   #   | 描述                                                                         | 等级  | 角色  |
| :---: | -------------------------------------------------------------------------- | :-: | :-: |
| 8.6.1 | 验证不同的记忆类型（情景记忆、语义记忆、工作记忆）是否具有隔离的安全上下文，配备基于角色的访问控制、独立的加密密钥以及每种记忆类型的文档化访问模式。 |  1  | D/V |
| 8.6.2 | 验证记忆巩固过程是否包含安全验证，通过内容净化、来源验证和存储前的完整性检查，防止恶意记忆的注入。                          |  2  | D/V |
| 8.6.3 | 验证内存检索查询是否经过验证和清理，以防止通过查询模式分析、访问控制执行和结果过滤提取未授权的信息。                         |  2  | D/V |
| 8.6.4 | 验证内存遗忘机制是否通过密钥删除、多重覆盖或带有验证证书的基于硬件的安全删除，提供具有密码学擦除保证的敏感信息安全删除。               |  3  | D/V |
| 8.6.5 | 通过校验和、审计日志以及当内存内容在正常操作之外发生变化时的自动警报，验证内存系统完整性是否被持续监控，以防止未经授权的修改或损坏。         |  3  | D/V |

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

