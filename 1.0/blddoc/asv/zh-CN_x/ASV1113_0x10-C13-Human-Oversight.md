# C13 人类监督、问责与治理

## 控制目标

本章提供了在人工智能系统中维护人类监督和明确责任链的要求，确保在整个人工智能生命周期中实现可解释性、透明度和伦理管理。

---

## C13.1 终止开关与覆盖机制

当观察到人工智能系统存在不安全行为时，应提供关机或回滚路径。

|   #    | 描述                               | 级别  | 角色  |
| :----: | -------------------------------- | :-: | :-: |
| 13.1.1 | 验证是否存在手动杀死开关机制，以立即停止 AI 模型推理和输出。 |  1  | D/V |
| 13.1.2 | 确认覆盖控制仅对授权人员可访问。                 |  1  |  D  |
| 13.1.3 | 验证回滚程序能够恢复到先前的模型版本或安全模式操作。       |  3  | D/V |
| 13.1.4 | 验证覆盖机制是否定期测试。                    |  3  |  V  |

---

## C13.2 人类参与决策检查点

当风险超出预设阈值时，要求人工审批。

|   #    | 描述                                   | 级别  | 角色  |
| :----: | ------------------------------------ | :-: | :-: |
| 13.2.1 | 验证高风险的人工智能决策在执行前需要明确的人类批准。           |  1  | D/V |
| 13.2.2 | 验证风险阈值是否被明确定义并自动触发人工审核工作流程。          |  1  |  D  |
| 13.2.3 | 确认在无法在规定时间内获得人工批准时，时间敏感的决策有备选程序。     |  2  |  D  |
| 13.2.4 | 如适用，验证升级程序是否为不同的决策类型或风险类别定义了明确的权限级别。 |  3  | D/V |

---

## C13.3 责任链与可审计性

记录操作员动作和模型决策。

|   #    | 描述                                   | 级别  | 角色  |
| :----: | ------------------------------------ | :-: | :-: |
| 13.3.1 | 验证所有人工智能系统的决策和人工干预均记录有时间戳、用户身份和决策理由。 |  1  | D/V |
| 13.3.2 | 验证审计日志无法被篡改，并包含完整性验证机制。              |  2  |  D  |

---

## C13.4 可解释人工智能技术

表面特征重要性、反事实和局部解释。

|   #    | 描述                                     | 级别  | 角色  |
| :----: | -------------------------------------- | :-: | :-: |
| 13.4.1 | 验证人工智能系统是否以人类可读的格式提供其决策的基本解释。          |  1  | D/V |
| 13.4.2 | 通过人工评估研究和指标验证解释质量。                     |  2  |  V  |
| 13.4.3 | 验证关键决策是否提供特征重要性分数或归因方法（SHAP、LIME 等）。   |  3  | D/V |
| 13.4.4 | 验证反事实解释是否展示了如何修改输入以改变结果（如果适用于使用案例和领域）。 |  3  |  V  |

---

## C13.5 模型卡与使用披露

维护模型卡片，以记录预期用途、性能指标和伦理考量。

|   #    | 描述                                            | 级别  | 角色  |
| :----: | --------------------------------------------- | :-: | :-: |
| 13.5.1 | 验证模型卡是否记录了预期的使用场景、限制条件和已知的失败模式。               |  1  |  D  |
| 13.5.2 | 核实是否披露了不同适用用例中的性能指标。                          |  1  | D/V |
| 13.5.3 | 确认伦理考量、偏见评估、公平性评价、训练数据特征以及已知的训练数据限制已被记录并定期更新。 |  2  |  D  |
| 13.5.4 | 确认模型卡在整个模型生命周期中经过版本控制和维护，并进行变更跟踪。             |  2  | D/V |

---

## C13.6 不确定性量化

在响应中传播置信度分数或熵度量。

|   #    | 描述                             | 级别  | 角色  |
| :----: | ------------------------------ | :-: | :-: |
| 13.6.1 | 验证 AI 系统是否在其输出中提供置信度评分或不确定性度量。 |  1  |  D  |
| 13.6.2 | 验证不确定性阈值是否触发额外的人类审核或替代决策路径。    |  2  | D/V |
| 13.6.3 | 验证不确定性量化方法是否经过校准并且已针对真实数据进行验证。 |  2  |  V  |
| 13.6.4 | 验证不确定性传播在多步骤人工智能工作流中得以维持。      |  3  | D/V |

---

## C13.7 面向用户的透明度报告

定期披露事件、漂移和数据使用情况。

|   #    | 描述                                  | 级别  | 角色  |
| :----: | ----------------------------------- | :-: | :-: |
| 13.7.1 | 确认数据使用政策和用户同意管理实践已清晰传达给利益相关者。       |  1  | D/V |
| 13.7.2 | 验证是否已进行人工智能影响评估，并将结果纳入报告中。          |  2  | D/V |
| 13.7.3 | 验证定期发布的透明度报告是否以合理的细节披露了人工智能事件和运营指标。 |  2  | D/V |

### 参考文献

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

