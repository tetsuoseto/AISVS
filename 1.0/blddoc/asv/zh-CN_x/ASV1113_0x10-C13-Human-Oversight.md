# C13 人工监督、问责与治理

## 控制目标

本章提供在人工智能系统中维持人类监督与明确的问责链的要求，确保在整个人工智能生命周期内实现可解释性、透明度和伦理治理。

---

## C13.1 紧急停止开关与覆盖机制

在检测到 AI 系统存在不安全行为时，提供关机或回滚的路径。

|   #    | 描述                                   | 等级  | 角色  |
| :----: | ------------------------------------ | :-: | :-: |
| 13.1.1 | 验证是否存在手动紧急停止开关机制，以便立即中止 AI 模型的推理和输出。 |  1  | D/V |
| 13.1.2 | 验证覆写控制是否仅对经授权人员开放。                   |  1  |  D  |
| 13.1.3 | 验证回滚过程能否回退到先前的模型版本或安全模式下的运行状态。       |  3  | D/V |
| 13.1.4 | 请确保覆盖机制经过定期测试。                       |  3  |  V  |

---

## C13.2 人类-在-环 决策检查点

当风险水平超过预设阈值时，需要人工批准。

|   #    | 描述                                      | 等级  | 角色  |
| :----: | --------------------------------------- | :-: | :-: |
| 13.2.1 | 验证高风险的人工智能决策在执行之前需要获得明确的人类批准。           |  1  | D/V |
| 13.2.2 | 验证风险阈值是否被明确定义，并自动触发人工审核工作流。             |  1  |  D  |
| 13.2.3 | 核实在时效性决策中，当无法在规定的时间框架内获得人工批准时，是否存在回退机制。 |  2  |  D  |
| 13.2.4 | 验证升级程序是否为不同的决策类型或风险类别定义了清晰的授权级别（如适用）。   |  3  | D/V |

---

## C13.3 职责链与可审计性

记录操作员的操作和模型决策。

|   #    | 描述                                          | 等级  | 角色  |
| :----: | ------------------------------------------- | :-: | :-: |
| 13.3.1 | 请验证所有 AI 系统决策和人工干预是否被记录，且记录包含时间戳、用户身份和决策依据。 |  1  | D/V |
| 13.3.2 | 验证审计日志不可被篡改，并包含完整性校验机制。                     |  2  |  D  |

---

## C13.4 可解释-AI 技术

表面特征重要性、反事实以及局部解释。

|   #    | 描述                                         | 等级  | 角色  |
| :----: | ------------------------------------------ | :-: | :-: |
| 13.4.1 | 验证人工智能系统是否能够以人类可读的格式为其决策提供基本解释。            |  1  | D/V |
| 13.4.2 | 验证解释质量是否已通过人工评估研究和指标进行验证。                  |  2  |  V  |
| 13.4.3 | 请确认在关键决策中，特征重要性分数或归因方法（如 SHAP、LIME 等）是否可用。 |  3  | D/V |
| 13.4.4 | 验证反事实解释是否展示了输入如何被修改以改变结果（如适用于该用例和领域）。      |  3  |  V  |

---

## C13.5 模型卡与使用披露

为预期用途、性能指标和伦理考量维护模型卡。

|   #    | 描述                                            | 等级  | 角色  |
| :----: | --------------------------------------------- | :-: | :-: |
| 13.5.1 | 确保模型卡记录了预期的使用场景、局限性以及已知的失效模式。                 |  1  |  D  |
| 13.5.2 | 核实在不同适用场景中的性能指标是否已披露。                         |  1  | D/V |
| 13.5.3 | 确保伦理考量、偏见评估、公平性评估、训练数据特征以及已知的训练数据局限性被记录并定期更新。 |  2  |  D  |
| 13.5.4 | 验证模型卡在整个模型生命周期内是否实现版本控制并得到维护，并具备变更跟踪。         |  2  | D/V |

---

## C13.6 不确定性量化

在回答中传递置信度分数或熵测量。

|   #    | 描述                                      | 等级  | 角色  |
| :----: | --------------------------------------- | :-: | :-: |
| 13.6.1 | 验证 AI 系统 在 输出 中 是否 提供 置信度 分数 或 不确定性 度量。 |  1  |  D  |
| 13.6.2 | 验证不确定性阈值是否会触发额外的人工审核或替代决策路径。            |  2  | D/V |
| 13.6.3 | 验证不确定性量化方法是否已针对地面真值数据进行校准和验证。           |  2  |  V  |
| 13.6.4 | 验证在多步人工智能工作流中是否保持了不确定性传播。               |  3  | D/V |

---

## C13.7 面向用户的透明度报告

就事件、漂移和数据使用情况进行定期披露。

|   #    | 描述                                   | 等级  | 角色  |
| :----: | ------------------------------------ | :-: | :-: |
| 13.7.1 | 核实数据使用政策和用户同意管理做法是否已向利益相关者清晰传达。      |  1  | D/V |
| 13.7.2 | 确保 AI 影响评估已进行，并将结果纳入报告中。             |  2  | D/V |
| 13.7.3 | 核实定期发布的透明度报告是否在合理细节范围内披露人工智能事件和运营指标。 |  2  | D/V |

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

