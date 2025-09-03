# C1 训练数据治理 & 偏见管理

## 控制目标

训练数据必须以能够保持来源可追溯性、保障安全、质量和公正的方式来获取、处理和维护。这样做可以履行法律义务，降低在训练过程中出现的偏见、数据投毒或隐私泄露等风险，这些风险若在训练阶段暴露，可能影响整个 AI 生命周期。

---

## C1.1 训练数据溯源

维护所有数据集的可核验清单，仅接受可信来源，并记录每次变更以确保可审计性。

|   #   | 描述                                                         | 等级  | 角色  |
| :---: | ---------------------------------------------------------- | :-: | :-: |
| 1.1.1 | 核实并确保对每个训练数据源维持最新的清单（来源、管理者/所有者、许可、数据收集方法、预期用途的限制，以及处理历史）。 |  1  | D/V |
| 1.1.2 | 验证训练数据处理是否排除不必要的特征、属性或字段（例如未使用的元数据、敏感个人身份信息、泄露的测试数据）。      |  1  | D/V |
| 1.1.3 | 验证所有数据集变更都需通过带日志的审批工作流。                                    |  2  | D/V |
| 1.1.4 | 在可行的情况下，验证数据集或子集是否带有水印或指纹标记。                               |  3  | D/V |

---

## C1.2 训练数据的安全性与完整性

限制对训练数据的访问，在静态存储和传输过程中对其进行加密，并验证其完整性以防止篡改、窃取或数据污染。

|   #   | 描述                                             | 等级  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 1.2.1 | 验证访问控制是否保护训练数据的存储和数据管道。                        |  1  | D/V |
| 1.2.2 | 请确保对训练数据的所有访问都已被记录，包括用户、时间和操作。                 |  2  | D/V |
| 1.2.3 | 验证训练数据集在传输过程中和静态存储时是否使用行业标准的加密算法和密钥管理实践进行加密。   |  2  | D/V |
| 1.2.4 | 验证在训练数据的存储与传输过程中，是否使用密码学哈希值或数字签名来确保数据完整性。      |  2  | D/V |
| 1.2.5 | 验证是否已应用自动检测技术，以防止对训练数据的未授权修改或损坏。               |  2  | D/V |
| 1.2.6 | 请验证过时的训练数据是否已被安全清除或匿名化。                        |  2  | D/V |
| 1.2.7 | 验证所有训练数据集版本是否具有唯一标识、以不可变方式存储，并且可审计，以支持回滚和取证分析。 |  3  | D/V |

---

## C1.3 训练数据标注的质量、完整性与安全性

保护标签，并对关键数据进行技术评审。

|   #   | 描述                                                    | 等级  | 角色  |
| :---: | ----------------------------------------------------- | :-: | :-: |
| 1.3.1 | 验证是否对标签工件应用了密码学哈希值或数字签名，以确保它们的完整性和真实性。                |  2  | D/V |
| 1.3.2 | 验证标注接口和平台是否实施强访问控制，是否维护对所有标注活动的防篡改审计日志，以及是否防止未经授权的修改。 |  2  | D/V |
| 1.3.3 | 请验证标签中的敏感信息在静态存储和传输过程中，是否在数据字段级别被脱敏、匿名化或加密。           |  3  | D/V |

---

## C1.4 训练数据质量与安全保障

结合自动化验证、人工抽查和已记录的纠正措施，以确保数据集的可靠性。

|   #   | 描述                                                                                                       | 等级  | 角色  |
| :---: | -------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 1.4.1 | 验证自动化测试能够在每次数据摄取或重大数据转换中捕获格式错误和空值。                                                                       |  1  |  D  |
| 1.4.2 | 验证 LLM 训练和微调管道是否实现中毒检测与数据完整性校验（例如统计方法、离群值检测、嵌入分析），以识别潜在的中毒攻击（例如标签翻转、后门触发器插入、角色切换命令、影响力样本攻击）或训练数据中的非故意损坏。 |  2  | D/V |
| 1.4.3 | 根据风险评估，对相关模型实现并调优合适的防御措施，例如对抗性训练（使用生成的对抗样本）、带扰动输入的数据增强，或鲁棒优化技术。                                          |  3  | D/V |
| 1.4.4 | 验证自动生成的标签（例如，通过 LLMs 或弱监督）是否受置信阈值和一致性检查的约束，以检测幻觉、误导性或低置信度的标签。                                            |  2  | D/V |
| 1.4.5 | 验证自动化测试是否能够在每次数据摄取或任何重大数据转换时捕捉标签偏斜。                                                                      |  3  |  D  |

---

## C1.5 数据血缘与可追溯性

跟踪每个数据点从数据源到模型输入的完整轨迹，以实现可审计性和事件响应。

|   #   | 描述                                                                     | 等级  | 角色  |
| :---: | ---------------------------------------------------------------------- | :-: | :-: |
| 1.5.1 | 验证每个数据点的血统信息（包括所有转换、数据增强和合并）是否已被记录并且可以重建。                              |  2  | D/V |
| 1.5.2 | 验证数据血统记录是否不可变、被安全存储、并且可用于审计。                                           |  2  | D/V |
| 1.5.3 | 验证数据血缘追踪是否覆盖通过隐私保护或生成式技术生成的合成数据，并确保在整个数据管道中，所有合成数据都被清晰标注，且能够与真实数据清晰区分。 |  2  | D/V |

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

