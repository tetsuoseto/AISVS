# C1 训练数据治理与偏差管理

## 控制目标

训练数据必须以保留来源、保障安全、确保质量和公平的方式进行获取、处理和维护。这样不仅履行法律义务，还能减少在训练过程中出现的偏见、数据中毒或隐私泄露等风险，这些风险可能影响整个人工智能生命周期。

---

## C1.1 训练数据来源

维护所有数据集的可验证清单，仅接受可信来源，并记录每次更改以便审计。

|   #   | 描述                                                        | 等级  | 角色  |
| :---: | --------------------------------------------------------- | :-: | :-: |
| 1.1.1 | 确保维护一份最新的培训数据源清单，涵盖每个数据源的来源、管理员/所有者、许可、收集方法、预期使用限制以及处理历史。 |  1  | D/V |
| 1.1.2 | 验证训练数据处理是否排除了不必要的特征、属性或字段（例如，未使用的元数据、敏感的个人身份信息、泄露的测试数据）。  |  1  | D/V |
| 1.1.3 | 验证所有数据集更改均需经过记录的审批流程。                                     |  2  | D/V |
| 1.1.4 | 在可行的情况下，验证数据集或子集是否进行了水印或指纹识别。                             |  3  | D/V |

---

## C1.2 训练数据安全性与完整性

限制对训练数据的访问，对静态和传输中的数据进行加密，并验证其完整性，以防止篡改、盗窃或数据投毒。

|   #   | 描述                                           | 等级  | 角色  |
| :---: | -------------------------------------------- | :-: | :-: |
| 1.2.1 | 验证访问控制是否保护训练数据存储和管道。                         |  1  | D/V |
| 1.2.2 | 验证所有对训练数据的访问均有记录，包括用户、时间和操作。                 |  2  | D/V |
| 1.2.3 | 验证训练数据集在传输和静态存储时均经过加密，采用行业标准的密码算法和密钥管理实践。    |  2  | D/V |
| 1.2.4 | 验证在训练数据存储和传输过程中是否使用了密码哈希或数字签名以确保数据完整性。       |  2  | D/V |
| 1.2.5 | 验证是否应用了自动检测技术以防止训练数据的未授权修改或损坏。               |  2  | D/V |
| 1.2.6 | 确保过时的训练数据被安全清除或匿名化。                          |  2  | D/V |
| 1.2.7 | 验证所有训练数据集版本均具有唯一标识，且以不可变方式存储且可审计，以支持回滚和取证分析。 |  3  | D/V |

---

## C1.3 训练数据标注质量、完整性与安全性

保护标签并对关键数据要求技术审核。

|   #   | 描述                                                | 等级  | 角色  |
| :---: | ------------------------------------------------- | :-: | :-: |
| 1.3.1 | 验证是否对标签工件应用了加密哈希或数字签名，以确保其完整性和真实性。                |  2  | D/V |
| 1.3.2 | 验证标注接口和平台是否执行严格的访问控制，保持所有标注活动的防篡改审计日志，并防止未经授权的修改。 |  2  | D/V |
| 1.3.3 | 验证标签中的敏感信息在静态和传输过程中的数据字段级别是否被编辑、匿名化或加密。           |  3  | D/V |

---

## C1.4 训练数据质量与安全保障

结合自动验证、手动抽查和记录的补救措施，以确保数据集的可靠性。

|   #   | 描述                                                                                                                    | 等级  | 角色  |
| :---: | --------------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 1.4.1 | 验证自动化测试是否在每次数据摄取或重大数据转换时捕捉格式错误和空值。                                                                                    |  1  |  D  |
| 1.4.2 | 验证大规模语言模型（LLM）训练和微调流程是否实施了投毒检测与数据完整性验证（例如，统计方法、异常点检测、嵌入分析），以识别潜在的投毒攻击（例如，标签翻转、后门触发器插入、角色切换命令、有影响力的实例攻击）或训练数据中的无意数据损坏。 |  2  | D/V |
| 1.4.3 | 验证是否根据风险评估为相关模型实施并调整了适当的防御措施，例如对抗训练（使用生成的对抗样本）、带扰动输入的数据增强或鲁棒优化技术。                                                     |  3  | D/V |
| 1.4.4 | 验证自动生成的标签（例如，通过大语言模型或弱监督生成的标签）是否经过置信度阈值和一致性检查，以检测虚假、误导或置信度低的标签。                                                       |  2  | D/V |
| 1.4.5 | 验证自动化测试是否能够捕捉到每次数据摄取或重大数据转换中的标签偏移。                                                                                    |  3  |  D  |

---

## C1.5 数据血缘和可追溯性

跟踪每个数据点从来源到模型输入的完整历程，以便审计和事件响应。

|   #   | 描述                                                         | 等级  | 角色  |
| :---: | ---------------------------------------------------------- | :-: | :-: |
| 1.5.1 | 验证每个数据点的血统，包括所有转换、增强和合并，均已记录且能够重构。                         |  2  | D/V |
| 1.5.2 | 验证血缘记录是不可篡改的，安全存储的，并且可供审计访问。                               |  2  | D/V |
| 1.5.3 | 验证系谱追踪涵盖通过隐私保护或生成技术生成的合成数据，并确保所有合成数据在整个流程中都有明确标注且可区分于真实数据。 |  2  | D/V |

---

## 参考文献

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

