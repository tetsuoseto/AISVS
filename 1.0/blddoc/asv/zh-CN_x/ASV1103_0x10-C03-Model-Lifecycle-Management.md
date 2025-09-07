# C3 模型生命周期管理与变更控制

## 控制目标

人工智能系统必须实施变更控制流程，防止未经授权或不安全的模型修改进入生产环境。该控制确保模型在整个生命周期中的完整性——从开发到部署再到退役——从而实现快速事件响应并保持对所有变更的问责。

核心安全目标：通过采用受控流程确保只有经过授权和验证的模型能够进入生产，以维护完整性、可追溯性和可恢复性。

---

## C3.1 模型授权与完整性

只有经过验证完整性的授权模型才能进入生产环境。

|   #   | 描述                                                           | 级别  | 角色  |
| :---: | ------------------------------------------------------------ | :-: | :-: |
| 3.1.1 | 在部署之前，验证所有模型工件（权重、配置、分词器）均由授权实体进行加密签名。                       |  1  | D/V |
| 3.1.2 | 确保在部署时验证模型的完整性，并且签名验证失败会阻止模型加载。                              |  1  | D/V |
| 3.1.3 | 验证模型来源记录是否包含授权实体的身份、训练数据校验和、带有通过/失败状态的验证测试结果以及创建时间戳。         |  2  | D/V |
| 3.1.4 | 验证所有模型工件是否使用语义化版本控制（MAJOR.MINOR.PATCH），并附有明确的标准说明每个版本组件何时递增。 |  2  | D/V |
| 3.1.5 | 验证依赖关系跟踪是否维护了一个实时库存，从而能够快速识别所有使用该资源的系统。                      |  2  |  V  |

---

## C3.2 模型验证与测试

模型必须通过定义的安全和安全性验证后方可部署。

|   #   | 描述                                                    | 级别  | 角色  |
| :---: | ----------------------------------------------------- | :-: | :-: |
| 3.2.1 | 验证模型在部署前经过自动化安全测试，包括输入验证、输出清理和安全评估，并符合预先商定的组织通过/失败标准。 |  1  | D/V |
| 3.2.2 | 验证验证失败在经过预先指定的授权人员明确覆盖批准并附有书面业务理由后，是否会自动阻止模型部署。       |  1  | D/V |
| 3.2.3 | 验证测试结果是否经过加密签名，并且不可变地链接到正在验证的特定模型版本哈希。                |  2  |  V  |
| 3.2.4 | 确认紧急部署需要在预先约定的时间范围内，由预指定的安全权限机构进行书面安全风险评估和批准。         |  2  | D/V |

---

## C3.3 受控部署与回滚

模型部署必须受到控制、监控并且可以逆转。

|   #   | 描述                                                                 | 级别  | 角色  |
| :---: | ------------------------------------------------------------------ | :-: | :-: |
| 3.3.1 | 验证生产部署是否实施了渐进式发布机制（金丝雀部署、蓝绿部署），并且基于预先约定的错误率、延迟阈值或安全警报标准具备自动回滚触发机制。 |  1  |  D  |
| 3.3.2 | 验证回滚功能是否能够在预定义的组织时间窗口内原子性地恢复完整的模型状态（权重、配置、依赖项）。                    |  1  | D/V |
| 3.3.3 | 验证部署流程在模型激活之前是否验证加密签名并计算完整性校验和，若发现不匹配则部署失败。                        |  2  | D/V |
| 3.3.4 | 验证紧急模型关闭功能是否能通过自动断路器或手动杀死开关在预定义响应时间内禁用模型端点。                        |  2  | D/V |
| 3.3.5 | 验证回滚工件（先前的模型版本、配置、依赖项）是否按照组织政策通过不可变存储进行保留，以便于事件响应。                 |  2  |  V  |

---

## C3.4 变更责任与审计

所有模型生命周期的变更都必须可追溯且可审计。

|   #   | 描述                                                               | 级别  | 角色  |
| :---: | ---------------------------------------------------------------- | :-: | :-: |
| 3.4.1 | 验证所有模型变更（部署、配置、退役）均生成不可变的审计记录，包含时间戳、经过身份验证的操作用户身份、变更类型以及变更前后的状态。 |  1  |  V  |
| 3.4.2 | 验证审计日志访问是否需要适当的授权，并且所有访问尝试均记录用户身份和时间戳。                           |  2  | D/V |
| 3.4.3 | 验证提示模板和系统消息是否在 git 仓库中进行版本控制，并且在部署前必须经过指定审阅者的代码审查和批准。            |  2  | D/V |
| 3.4.4 | 验证审计记录是否包含足够的细节（模型哈希、配置快照、依赖版本），以便在保留期限内的任何时间点完全重建模型状态。          |  2  |  V  |

---

## C3.5 安全开发实践

模型开发和训练过程必须遵循安全实践以防止被破坏。

|   #   | 描述                                                       | 级别  | 角色  |
| :---: | -------------------------------------------------------- | :-: | :-: |
| 3.5.1 | 验证模型开发、测试和生产环境在物理或逻辑上是隔离的。它们没有共享的基础设施，具有独立的访问控制和隔离的数据存储。 |  1  |  D  |
| 3.5.2 | 验证模型训练和微调是否在具有受控网络访问的隔离环境中进行。                            |  1  |  D  |
| 3.5.3 | 确保训练数据源在用于模型开发之前通过完整性检查验证，并通过具有文档化链条的可信来源进行身份验证。         |  1  | D/V |
| 3.5.4 | 验证模型开发工件（超参数、训练脚本、配置文件）已存储在版本控制中，并且在用于训练之前需要经过同行评审批准。    |  2  |  D  |

---

## C3.6 模型退休与退役

当模型不再需要或发现安全问题时，必须安全地退役模型。

|   #   | 描述                                                   | 级别  | 角色  |
| :---: | ---------------------------------------------------- | :-: | :-: |
| 3.6.1 | 验证模型退役流程是否能够自动扫描依赖关系图，识别所有使用系统，并在停用前提供预先约定的通知期限。     |  1  |  D  |
| 3.6.2 | 根据已验证的销毁证书，按照记录的数据保留政策，使用加密擦除或多次覆盖方法，确保退役模型工件被安全清除。  |  1  | D/V |
| 3.6.3 | 验证模型退役事件是否记录了时间戳和执行者身份，并且模型签名是否已被撤销以防止重新使用。          |  2  |  V  |
| 3.6.4 | 验证紧急模型退役是否能够在预设的紧急响应时间范围内，通过自动关闭开关禁用模型访问，以防发现关键安全漏洞。 |  2  | D/V |

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

