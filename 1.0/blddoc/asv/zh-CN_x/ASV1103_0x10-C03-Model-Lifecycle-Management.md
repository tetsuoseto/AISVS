# C3 模型生命周期管理与变更控制

## 控制目标

人工智能系统必须实施变更控制流程，防止未经授权或不安全的模型修改进入生产环境。该控制确保模型在整个生命周期中的完整性——从开发到部署再到退役——从而实现快速事件响应并保持对所有变更的责任追踪。

核心安全目标：通过采用受控流程，确保只有经过授权和验证的模型才能进入生产环境，并保持完整性、可追溯性和可恢复性。

---

## C3.1 模型授权与完整性

只有经过验证完整性的授权模型才能进入生产环境。

|   #   | 描述                                                         | 等级  | 角色  |
| :---: | ---------------------------------------------------------- | :-: | :-: |
| 3.1.1 | 在部署之前，验证所有模型工件（权重、配置、分词器）是否由授权实体进行过密码学签名。                  |  1  | D/V |
| 3.1.2 | 验证模型完整性在部署时已被确认，并且签名验证失败会阻止模型加载。                           |  1  | D/V |
| 3.1.3 | 验证模型溯源记录是否包含授权实体的身份、训练数据校验和、带有通过/未通过状态的验证测试结果以及创建时间戳。      |  2  | D/V |
| 3.1.4 | 验证所有模型产物均使用语义版本控制（MAJOR.MINOR.PATCH），并具备规定每个版本组件递增条件的文档说明。 |  2  | D/V |
| 3.1.5 | 验证依赖跟踪能够维护实时库存，从而实现对所有使用系统的快速识别。                           |  2  |  V  |

---

## C3.2 模型验证与测试

模型在部署前必须通过定义的安全性和可靠性验证。

|   #   | 描述                                                              | 等级  | 角色  |
| :---: | --------------------------------------------------------------- | :-: | :-: |
| 3.2.1 | 验证模型在部署前必须经过自动化安全测试，测试内容包括输入验证、输出清理以及安全评估，并且需符合事先约定的组织通过/不通过标准。 |  1  | D/V |
| 3.2.2 | 验证在经过预先指定的授权人员明确覆盖批准并附有书面业务理由后，验证失败是否会自动阻止模型部署。                 |  1  | D/V |
| 3.2.3 | 验证测试结果是否经过加密签名，并且不可变地链接到正在验证的特定模型版本哈希。                          |  2  |  V  |
| 3.2.4 | 验证紧急部署是否需要在预先约定的时间范围内，经过预先指定的安全权威进行记录的安全风险评估和批准。                |  2  | D/V |

---

## C3.3 受控部署与回滚

模型部署必须受到控制、监控且可逆。

|   #   | 描述                                                             | 等级  | 角色  |
| :---: | -------------------------------------------------------------- | :-: | :-: |
| 3.3.1 | 验证生产部署是否实施渐进式发布机制（灰度发布、蓝绿部署），并基于预先约定的错误率、延迟阈值或安全警报标准设置自动回滚触发器。 |  1  |  D  |
| 3.3.2 | 验证回滚功能是否在预定义的组织时间窗口内，原子性地恢复完整的模型状态（权重、配置、依赖项）。                 |  1  | D/V |
| 3.3.3 | 验证部署过程在模型激活前是否验证了加密签名并计算了完整性校验和，若有任何不匹配则使部署失败。                 |  2  | D/V |
| 3.3.4 | 验证紧急模型关闭功能能够通过自动断路器或手动终止开关在预定义响应时间内禁用模型端点。                     |  2  | D/V |
| 3.3.5 | 验证回滚工件（先前的模型版本、配置、依赖项）是否根据组织政策保留，并使用不可变存储以便于事故响应。              |  2  |  V  |

---

## C3.4 变更问责与审计

所有模型生命周期的更改必须可追踪和可审计。

|   #   | 描述                                                              | 等级  | 角色  |
| :---: | --------------------------------------------------------------- | :-: | :-: |
| 3.4.1 | 验证所有模型变更（部署、配置、淘汰）均生成不可变的审计记录，包括时间戳、经过身份验证的操作人员身份、变更类型以及变更前后状态。 |  1  |  V  |
| 3.4.2 | 验证审计日志访问是否需要适当的授权，并且所有访问尝试均记录用户身份和时间戳。                          |  2  | D/V |
| 3.4.3 | 验证提示模板和系统消息是否在git代码库中进行版本控制，并且在部署之前必须经过指定审核者的代码审查和批准。           |  2  | D/V |
| 3.4.4 | 验证审计记录是否包含足够的详细信息（模型哈希值、配置快照、依赖版本），以便在保留期限内的任何时间点能够完整重建模型状态。    |  2  |  V  |

---

## C3.5 安全开发实践

模型开发和训练过程必须遵循安全规范以防止被攻破。

|   #   | 描述                                                           | 等级  | 角色  |
| :---: | ------------------------------------------------------------ | :-: | :-: |
| 3.5.1 | 验证模型开发、测试和生产环境在物理上或逻辑上是分离的。它们没有共享的基础设施，具有独立的访问控制，并且数据存储是隔离的。 |  1  |  D  |
| 3.5.2 | 验证模型训练和微调是否在具有受控网络访问的隔离环境中进行。                                |  1  |  D  |
| 3.5.3 | 确保训练数据源在用于模型开发之前通过完整性检查进行验证，并通过有文档记录的监管链由可信来源进行身份验证。         |  1  | D/V |
| 3.5.4 | 验证模型开发工件（超参数、训练脚本、配置文件）是否存储在版本控制中，并且在用于训练之前需要同行评审批准。         |  2  |  D  |

---

## C3.6 模型退役与停用

模型在不再需要或发现安全问题时必须安全退役。

|   #   | 描述                                                     | 等级  | 角色  |
| :---: | ------------------------------------------------------ | :-: | :-: |
| 3.6.1 | 验证模型退役流程是否自动扫描依赖图，识别所有使用系统，并在退役前提供预先商定的通知期。            |  1  |  D  |
| 3.6.2 | 根据记录的数据保留政策，使用加密擦除或多遍覆盖方法，验证已退役模型工件的安全擦除，并确保有已验证的销毁证书。 |  1  | D/V |
| 3.6.3 | 验证模型退役事件是否带有时间戳和行为者身份的日志记录，并且模型签名已被吊销以防止重复使用。          |  2  |  V  |
| 3.6.4 | 验证紧急模型退役是否能够通过自动杀死开关，在预先设定的紧急响应时间内禁用模型访问，以防发现关键安全漏洞。   |  2  | D/V |

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

