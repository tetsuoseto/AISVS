# 11 隐私保护与个人数据管理

## 控制目标

在整个 AI 生命周期——数据收集、训练、推理和事件响应中保持严格的隐私保障，确保个人数据仅在明确同意、最小必要范围、可证明的删除以及正式的隐私保证下被处理。

---

## 11.1 匿名化与数据最小化

|   #    | 描述                                     | 级别  | 角色  |
| :----: | -------------------------------------- | :-: | :-: |
| 11.1.1 | 验证直接标识符和准标识符是否被删除或哈希处理。                |  1  | D/V |
| 11.1.2 | 验证自动审核是否测量k-匿名性/l-多样性，并在阈值低于策略时发出警报。   |  2  | D/V |
| 11.1.3 | 验证模型特征重要性报告，证明标识符泄露的互信息不超过ε = 0.01。    |  2  |  V  |
| 11.1.4 | 验证正式证明或合成数据认证即使在关联攻击下也能显示再识别风险 ≤ 0.05。 |  3  |  V  |

---

## 11.2 被遗忘权与删除执行

|   #    | 描述                                               | 级别  | 角色  |
| :----: | ------------------------------------------------ | :-: | :-: |
| 11.2.1 | 验证数据主体删除请求是否在少于30天的服务级别协议内传播到原始数据集、检查点、嵌入、日志和备份。 |  1  | D/V |
| 11.2.2 | 验证“机器遗忘”程序是否通过经过认证的遗忘算法实际重新训练或近似删除。              |  2  |  D  |
| 11.2.3 | 验证影子模型评估证明遗忘记录在遗忘后对输出的影响少于1%。                    |  2  |  V  |
| 11.2.4 | 验证删除事件是否以不可变方式记录并可供监管机构审计。                       |  3  |  V  |

---

## 11.3 差分隐私保护措施

|   #    | 描述                          | 级别  | 角色  |
| :----: | --------------------------- | :-: | :-: |
| 11.3.1 | 验证隐私损失核算仪表板在累积ε超过政策阈值时发出警报。 |  2  | D/V |
| 11.3.2 | 验证黑箱隐私审计在宣称值的10%范围内估计ε̂。    |  2  |  V  |
| 11.3.3 | 验证形式化证明涵盖所有训练后微调和嵌入。        |  3  |  V  |

---

## 11.4 目的限制与范围蔓延保护

|   #    | 描述                                    | 级别  | 角色  |
| :----: | ------------------------------------- | :-: | :-: |
| 11.4.1 | 验证每个数据集和模型检查点是否附有与原始同意一致的机器可读用途标签。    |  1  |  D  |
| 11.4.2 | 验证运行时监视器是否能够检测出与声明用途不一致的查询并触发软拒绝。     |  1  | D/V |
| 11.4.3 | 验证策略即代码门禁，确保未经DPIA审查，模型不能重新部署到新领域。    |  3  |  D  |
| 11.4.4 | 验证正式的可追溯性证明，确保每一个个人数据生命周期都保持在已同意的范围内。 |  3  |  V  |

---

## 11.5 同意管理与合法依据跟踪

|   #    | 描述                                       | 级别  | 角色  |
| :----: | ---------------------------------------- | :-: | :-: |
| 11.5.1 | 验证同意管理平台（CMP）是否记录了每个数据主体的选择加入状态、目的和保留期限。 |  1  | D/V |
| 11.5.2 | 验证API是否公开了同意令牌；模型在推理前必须验证令牌的范围。          |  2  |  D  |
| 11.5.3 | 验证拒绝或撤销的同意是否在24小时内停止处理流程。                |  2  | D/V |

---

## 11.6 带隐私控制的联邦学习

|   #    | 描述                           | 级别  | 角色  |
| :----: | ---------------------------- | :-: | :-: |
| 11.6.1 | 验证客户端更新在聚合之前是否采用了本地差分隐私噪声添加。 |  1  |  D  |
| 11.6.2 | 验证训练指标具有差分隐私性，且绝不泄露单个客户的损失。  |  2  | D/V |
| 11.6.3 | 确认已启用抗中毒聚合（例如，Krum/修剪均值）。    |  2  |  V  |
| 11.6.4 | 验证形式证明显示整体 ε 预算的效用损失小于 5。    |  3  |  V  |

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

