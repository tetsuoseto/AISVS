# 11 隐私保护与个人数据管理

## 控制目标

在整个 AI 生命周期中保持严格的隐私保障—数据收集、训练、推理和事件响应—以确保个人数据仅在获得明确同意、最小必要范围、可证明的删除以及正式的隐私保障条件下被处理。

---

## 11.1 匿名化 与 数据最小化

|   #    | 描述                                       | 等级  | 角色  |
| :----: | ---------------------------------------- | :-: | :-: |
| 11.1.1 | 验证直接标识符和准识别符是否已被移除并进行哈希处理。               |  1  | D/V |
| 11.1.2 | 验证自动审计是否衡量 k-匿名性/l-多样性，并在阈值低于策略规定时发出警报。  |  2  | D/V |
| 11.1.3 | 验证模型特征重要性报告，证明不存在超出 ε = 0.01 的互信息的标识符泄露。 |  2  |  V  |
| 11.1.4 | 验证形式证明或合成数据认证在连接攻击下也能显示再识别风险 ≤ 0.05。     |  3  |  V  |

---

## 11.2 被遗忘权 & 删除强制执行

|   #    | 描述                                                           | 等级  | 角色  |
| :----: | ------------------------------------------------------------ | :-: | :-: |
| 11.2.1 | 验证 data-subject 删除请求是否在少于 30 天的服务水平协议内传播至原始数据集、检查点、嵌入、日志和备份。 |  1  | D/V |
| 11.2.2 | 验证以下内容：“machine-unlearning” 例程通过实际重新训练，或使用经过认证的遗忘算法来近似移除。    |  2  |  D  |
| 11.2.3 | 验证影子模型评估在完成去学习后证明被遗忘的记录对输出的影响小于1%                            |  2  |  V  |
| 11.2.4 | 验证删除事件是否以不可变的方式记录，并可供监管机构审计。                                 |  3  |  V  |

---

## 11.3 差分-隐私保护措施

|   #    | 描述                               | 等级  | 角色  |
| :----: | -------------------------------- | :-: | :-: |
| 11.3.1 | 验证隐私损失计算仪表板在累计 ε 超过策略阈值时是否会发出警报。 |  2  | D/V |
| 11.3.2 | 验证黑盒-隐私审计的 ε̂ 是否在声明值的 10% 内。     |  2  |  V  |
| 11.3.3 | 验证形式化证明是否覆盖所有训练后微调和嵌入。           |  3  |  V  |

---

## 11.4 目的限定与范围蔓延保护

|   #    | 描述                                          | 等级  | 角色  |
| :----: | ------------------------------------------- | :-: | :-: |
| 11.4.1 | 验证每个数据集和模型检查点是否携带与原始同意保持一致的机器可读用途标签。        |  1  |  D  |
| 11.4.2 | 验证运行时监控是否能够检测到与所声明目的不一致的查询，并触发软拒绝。          |  1  | D/V |
| 11.4.3 | 验证策略即代码的门控是否会在未进行 DPIA 审查的情况下阻止将模型重新部署到新领域。 |  3  |  D  |
| 11.4.4 | 验证形式化可追溯性证明，确保每个个人数据的生命周期保持在经同意的范围内。        |  3  |  V  |

---

## 11.5 同意管理与合法基础-跟踪

|   #    | 描述                                       | 等级  | 角色  |
| :----: | ---------------------------------------- | :-: | :-: |
| 11.5.1 | 验证同意管理平台（CMP）是否为每个数据主体记录了同意状态、处理目的和保留期限。 |  1  | D/V |
| 11.5.2 | 验证 API 是否暴露同意令牌；模型在推断之前必须验证令牌的作用域。       |  2  |  D  |
| 11.5.3 | 验证被拒绝或撤回的同意是否会在24小时内中止处理流水线。             |  2  | D/V |

---

## 11.6 带有隐私控制的联邦学习

|   #    | 描述                                           | 等级  | 角色  |
| :----: | -------------------------------------------- | :-: | :-: |
| 11.6.1 | 请验证客户端更新在聚合之前是否采用本地差分隐私噪声添加。                 |  1  |  D  |
| 11.6.2 | 验证训练指标具有差分隐私保护，并且不会泄露单个客户端的损失。               |  2  | D/V |
| 11.6.3 | 请验证是否已启用对投毒攻击具有鲁棒性的聚合（例如 Krum/Trimmed-Mean）。 |  2  |  V  |
| 11.6.4 | 验证形式证明表明，在总体 ε 预算下，效用损失小于 5。                 |  3  |  V  |

---

### 参考文献

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

