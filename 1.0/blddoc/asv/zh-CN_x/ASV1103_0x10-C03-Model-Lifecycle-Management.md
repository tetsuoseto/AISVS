# C3 模型生命周期管理与变更控制

## 控制目标

人工智能系统必须实施变更控制流程，防止未经授权或不安全的模型修改进入生产环节。此控制确保模型在整个生命周期内的完整性——从开发到部署再到退役——从而实现快速事件响应并保持对所有变更的问责。

核心安全目标：通过采用受控流程，确保只有经过授权和验证的模型才能进入生产，保持完整性、可追溯性和可恢复性。

---

## C3.1 模型授权与完整性

只有经过验证完整性的授权模型才能进入生产环境。

|   #   | 描述                                                            | 等级  | 角色  |
| :---: | ------------------------------------------------------------- | :-: | :-: |
| 3.1.1 | 在部署之前，验证所有模型工件（权重、配置、分词器）均由授权实体进行加密签名。                        |  1  | D/V |
| 3.1.2 | 验证模型完整性在部署时得到确认，且签名验证失败会阻止模型加载。                               |  1  | D/V |
| 3.1.3 | 验证模型来源记录是否包括授权实体的身份、训练数据校验和、带有通过/失败状态的验证测试结果以及创建时间戳。          |  2  | D/V |
| 3.1.4 | 验证所有模型工件均使用语义版本控制（MAJOR.MINOR.PATCH），并具备明确记录的标准，规定每个版本组件何时递增。 |  2  | D/V |
| 3.1.5 | 验证依赖跟踪是否维护了实时库存，从而实现快速识别所有使用系统。                               |  2  |  V  |

---

## C3.2 模型验证与测试

模型必须通过定义的安全和安全性验证后才能部署。

|   #   | 描述                                                       | 等级  | 角色  |
| :---: | -------------------------------------------------------- | :-: | :-: |
| 3.2.1 | 验证模型在部署前是否经过自动化安全测试，包括输入验证、输出净化和安全评估，并且达到预先商定的组织通过/失败阈值。 |  1  | D/V |
| 3.2.2 | 验证当预先指定的授权人员明确批准覆盖且有书面业务理由时，验证失败是否会自动阻止模型部署。             |  1  | D/V |
| 3.2.3 | 验证测试结果是否经过加密签名，并与被验证的特定模型版本哈希不可变地关联。                     |  2  |  V  |
| 3.2.4 | 验证紧急部署是否需要在预先约定的时间范围内，由预先指定的安全权限机构进行记录在案的安全风险评估和批准。      |  2  | D/V |

---

## C3.3 受控部署与回滚

模型部署必须受到控制、监控并且可逆。

|   #   | 描述                                                                  | 等级  | 角色  |
| :---: | ------------------------------------------------------------------- | :-: | :-: |
| 3.3.1 | 验证生产环境部署是否实施了渐进式发布机制（金丝雀发布，蓝绿发布），并基于预先约定的错误率、延迟阈值或安全警报标准具备自动回滚触发功能。 |  1  |  D  |
| 3.3.2 | 验证回滚功能在预定义的组织时间窗口内以原子方式恢复完整的模型状态（权重、配置、依赖关系）。                       |  1  | D/V |
| 3.3.3 | 验证部署流程在模型激活前是否验证加密签名并计算完整性校验和，如有不匹配则部署失败。                           |  2  | D/V |
| 3.3.4 | 验证紧急模型关闭功能能够通过自动断路器或手动断开开关，在预定义的响应时间内禁用模型端点。                        |  2  | D/V |
| 3.3.5 | 验证回滚工件（先前的模型版本、配置、依赖项）是否根据组织政策保留，并采用不可变存储以支持事件响应。                   |  2  |  V  |

---

## C3.4 变更责任与审计

所有模型生命周期的变更必须可追溯且可审计。

|   #   | 描述                                                              | 等级  | 角色  |
| :---: | --------------------------------------------------------------- | :-: | :-: |
| 3.4.1 | 验证所有模型变更（部署、配置、退役）都生成不可变的审计记录，包括时间戳、经过身份验证的操作身份、变更类型以及变更前/后的状态。 |  1  |  V  |
| 3.4.2 | 验证审计日志访问是否需要适当的授权，并确保所有访问尝试都记录有用户身份和时间戳。                        |  2  | D/V |
| 3.4.3 | 验证提示模板和系统消息是否在git代码库中进行版本控制，并且在部署前必须经过指定审阅者的代码审查和批准。            |  2  | D/V |
| 3.4.4 | 验证审计记录是否包含足够的详细信息（模型哈希、配置快照、依赖版本），以便能够在保留期限内的任何时间戳完整重建模型状态。     |  2  |  V  |

---

## C3.5 安全开发实践

模型开发和训练过程必须遵循安全规范以防止被攻破。

|   #   | 描述                                                           | 等级  | 角色  |
| :---: | ------------------------------------------------------------ | :-: | :-: |
| 3.5.1 | 验证模型开发、测试和生产环境在物理上或逻辑上是分开的。它们没有共享的基础设施，具有不同的访问控制，并且数据存储是隔离的。 |  1  |  D  |
| 3.5.2 | 验证模型训练和微调是否在具有受控网络访问的隔离环境中进行。                                |  1  |  D  |
| 3.5.3 | 验证训练数据源通过完整性检查并通过可信源进行身份验证，且在模型开发使用前具有记录的托管链。                |  1  | D/V |
| 3.5.4 | 验证模型开发工件（超参数、训练脚本、配置文件）是否存储在版本控制中，并且在用于训练之前需要经过同行评审批准。       |  2  |  D  |

---

## C3.6 模型退役与停用

模型在不再需要或发现安全问题时，必须安全退役。

|   #   | 描述                                                     | 等级  | 角色  |
| :---: | ------------------------------------------------------ | :-: | :-: |
| 3.6.1 | 确认模型退役流程能自动扫描依赖关系图，识别所有使用系统，并在退役前提供预先约定的通知期限。          |  1  |  D  |
| 3.6.2 | 根据已验证的销毁证明，按照记录的数据保留政策，使用加密擦除或多遍覆盖的方法，确认已退役的模型工件被安全擦除。 |  1  | D/V |
| 3.6.3 | 核实模型退役事件是否被记录了时间戳和操作人员身份，并且模型签名是否被撤销以防止重复使用。           |  2  |  V  |
| 3.6.4 | 验证紧急模型退役是否能够通过自动终止开关，在预先设定的紧急响应时间内禁用模型访问，以防发现关键安全漏洞。   |  2  | D/V |

---

## 参考文献

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

