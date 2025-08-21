# C1 训练数据治理与偏差管理

## 控制目标

训练数据必须以保留来源、保障安全、保证质量和公正的方式进行获取、处理和维护。这样做既履行了法律义务，也减少了训练过程中可能出现影响整个人工智能生命周期的偏见、投毒或隐私泄露的风险。

---

## C1.1 训练数据来源

维护所有数据集的可验证清单，仅接受可信来源，并记录每次更改以便审计。

|   #   | 描述                                                        | 级别  | 角色  |
| :---: | --------------------------------------------------------- | :-: | :-: |
| 1.1.1 | 确保维护一份最新的所有训练数据来源的清单（来源、管理者/所有者、许可、收集方法、预期使用限制和处理历史）。     |  1  | D/V |
| 1.1.2 | 确认训练数据处理过程中排除了不必要的特征、属性或字段（例如，未使用的元数据、敏感的个人身份信息、泄露的测试数据）。 |  1  | D/V |
| 1.1.3 | 验证所有数据集更改均需经过记录的审批流程。                                     |  2  | D/V |
| 1.1.4 | 在可行的情况下，验证数据集或子集是否带有水印或指纹。                                |  3  | D/V |

---

## C1.2 训练数据安全性与完整性

限制对训练数据的访问，对静态和传输中的数据进行加密，并验证其完整性，以防止篡改、盗窃或数据中毒。

|   #   | 描述                                              | 级别  | 角色  |
| :---: | ----------------------------------------------- | :-: | :-: |
| 1.2.1 | 验证访问控制是否保护训练数据存储和管道。                            |  1  | D/V |
| 1.2.2 | 验证所有对训练数据的访问是否都有日志记录，包括用户、时间和操作。                |  2  | D/V |
| 1.2.3 | 验证训练数据集在传输和静止时均经过加密，使用行业标准的加密算法和密钥管理规范。         |  2  | D/V |
| 1.2.4 | 验证是否使用加密哈希或数字签名来确保训练数据存储和传输过程中的数据完整性。           |  2  | D/V |
| 1.2.5 | 验证是否应用了自动检测技术以防止训练数据的未经授权的修改或损坏。                |  2  | D/V |
| 1.2.6 | 验证过时的训练数据是否已被安全清除或匿名化。                          |  2  | D/V |
| 1.2.7 | 验证所有训练数据集版本均有唯一标识，且以不可篡改的方式存储，并且可审计，以支持回滚和取证分析。 |  3  | D/V |

---

## C1.3 训练数据标注的质量、完整性与安全性

保护标签并对关键数据进行技术审核。

|   #   | 描述                                              | 级别  | 角色  |
| :---: | ----------------------------------------------- | :-: | :-: |
| 1.3.1 | 验证是否对标签工件应用了加密哈希或数字签名，以确保其完整性和真实性。              |  2  | D/V |
| 1.3.2 | 验证标注界面和平台是否执行强访问控制，维护所有标注活动的防篡改审计日志，并防止未经授权的修改。 |  2  | D/V |
| 1.3.3 | 验证标签中的敏感信息在静态和传输过程中是否在数据字段级别被编辑、匿名化或加密。         |  3  | D/V |

---

## C1.4 训练数据质量与安全保障

结合自动验证、人工抽查和记录的修正措施，以保证数据集的可靠性。

|   #   | 描述                                                                                                         | 级别  | 角色  |
| :---: | ---------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 1.4.1 | 验证自动化测试是否能在每次摄取或重大数据转换时捕获格式错误和空值。                                                                          |  1  |  D  |
| 1.4.2 | 验证大语言模型训练和微调管道是否实现了投毒检测与数据完整性验证（例如，统计方法、离群点检测、嵌入分析），以识别潜在的投毒攻击（例如，标签翻转、后门触发插入、角色切换命令、影响实例攻击）或训练数据中的无意数据损坏。 |  2  | D/V |
| 1.4.3 | 根据风险评估，验证是否针对相关模型实施并调整了适当的防御措施，如对抗训练（使用生成的对抗样本）、带扰动输入的数据增强或鲁棒优化技术。                                         |  3  | D/V |
| 1.4.4 | 验证自动生成的标签（例如，通过大型语言模型或弱监督产生的标签）是否遵循置信度阈值和一致性检查，以检测幻觉标签、误导性标签或低置信度标签。                                       |  2  | D/V |
| 1.4.5 | 验证自动化测试是否能在每次数据摄取或重大数据转换时捕捉标签偏移。                                                                           |  3  |  D  |

---

## C1.5 数据溯源和可追踪性

追踪每个数据点从源头到模型输入的完整路径，以确保可审计性和事件响应。

|   #   | 描述                                                          | 级别  | 角色  |
| :---: | ----------------------------------------------------------- | :-: | :-: |
| 1.5.1 | 验证每个数据点的血统，包括所有转换、增强和合并，是否都有记录且可以重建。                        |  2  | D/V |
| 1.5.2 | 验证血统记录是不可更改的，安全存储的，并且可供审计访问。                                |  2  | D/V |
| 1.5.3 | 确保血统追踪涵盖通过隐私保护或生成技术生成的合成数据，并且所有合成数据在整个流程中都被明确标记且可与真实数据区分开来。 |  2  | D/V |

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

