# C3 模型生命周期管理与变更控制

## 控制目标

AI 系统必须实施变更控制流程，防止未经授权或不安全的模型修改进入生产环境。该控制措施确保在整个生命周期--从开发到部署再到退役--从而实现快速事件响应并对所有变更保持问责。

核心安全目标：仅有经授权、经过验证的模型通过采用能够维护完整性、可追溯性和可恢复性的受控流程进入生产环境。

---

## C3.1 模型授权与完整性

只有经授权且完整性已验证的模型才能进入生产环境。

|   #   | 描述                                                                | 等级  | 角色  |
| :---: | ----------------------------------------------------------------- | :-: | :-: |
| 3.1.1 | 在部署之前，验证所有模型产物（权重、配置、分词器）是否已由经授权的实体进行密码学签名。                       |  1  | D/V |
| 3.1.2 | 确保在部署时对模型完整性进行验证，若签名验证失败将阻止模型加载。                                  |  1  | D/V |
| 3.1.3 | 验证模型溯源记录是否包含授权实体的身份、训练数据校验和、带有通过/失败状态的验证测试结果，以及创建时间戳。             |  2  | D/V |
| 3.1.4 | 验证所有模型产物是否使用语义化版本控制（MAJOR.MINOR.PATCH），并附有文档化的标准，规定何时对每个版本组件进行递增。 |  2  | D/V |
| 3.1.5 | 验证依赖跟踪是否维护一个实时清单，以便快速识别所有使用中的系统。                                  |  2  |  V  |

---

## C3.2 模型验证与测试

模型在部署前必须通过已定义的安全性和稳健性验证。

|   #   | 描述                                                              | 等级  | 角色  |
| :---: | --------------------------------------------------------------- | :-: | :-: |
| 3.2.1 | 在部署之前，验证模型是否经过自动化的安全测试，该测试包括输入验证、输出净化，以及带有事先商定的组织通过/不通过阈值的安全评估。 |  1  | D/V |
| 3.2.2 | 请验证：在获得来自预先指定的授权人员且附有书面业务理由的明确覆盖批准后，验证失败会自动阻止模型部署。              |  1  | D/V |
| 3.2.3 | 验证测试结果是否已进行密码学签名，并且与正在验证的特定模型版本哈希值不可变地关联。                       |  2  |  V  |
| 3.2.4 | 请确认，紧急部署需要有书面的安全风险评估，并在事先约定的时间框架内获得来自事先指定的安全权威的批准。              |  2  | D/V |

---

## C3.3 受控部署与回滚

模型部署必须可控、可监控，并且可逆。

|   #   | 描述                                                                    | 等级  | 角色  |
| :---: | --------------------------------------------------------------------- | :-: | :-: |
| 3.3.1 | 请验证生产环境部署是否实现了渐进式部署机制（金丝雀部署、蓝绿部署），并具备基于事先约定的错误率、延迟阈值或安全警报标准的自动回滚触发条件。 |  1  |  D  |
| 3.3.2 | 验证回滚能力是否能够在预定义的组织时间窗口内原子地恢复完整的模型状态（权重、配置、依赖项）。                        |  1  | D/V |
| 3.3.3 | 确保部署流程在模型激活之前验证数字签名并计算完整性校验和，若有任一不匹配，部署将失败。                           |  2  | D/V |
| 3.3.4 | 验证紧急模型停机能力是否能够在预定义的响应时间内，通过自动断路器或手动停止开关，禁用模型端点。                       |  2  | D/V |
| 3.3.5 | 确保回滚制品（先前的模型版本、配置和依赖项）按照组织政策进行保留，并使用不可变存储以用于事件响应。                     |  2  |  V  |

---

## C3.4 变更问责与审计

所有模型生命周期的变更必须可追踪并可审计。

|   #   | 描述                                                                      | 等级  | 角色  |
| :---: | ----------------------------------------------------------------------- | :-: | :-: |
| 3.4.1 | 确保所有模型变更（部署、配置、下线）生成不可变的审计记录，这些记录应包括时间戳、经身份验证的执行者身份、变更类型，以及变更前状态与变更后状态。 |  1  |  V  |
| 3.4.2 | 验证审计日志的访问是否需要适当授权，并且所有访问尝试都应记录用户身份和时间戳。                                 |  2  | D/V |
| 3.4.3 | 验证提示模板和系统消息在 Git 仓库中进行版本控制，并在部署前必须经过指定评审人员的代码审查与批准。                     |  2  | D/V |
| 3.4.4 | 验证审计记录是否包含足够的细节（模型哈希、配置快照、依赖版本），以在保留期内的任意时间戳实现对模型状态的完整重建。               |  2  |  V  |

---

## C3.5 安全开发实践

模型开发与训练过程必须遵循安全实践，以防止被妥协。

|   #   | 描述                                                           | 等级  | 角色  |
| :---: | ------------------------------------------------------------ | :-: | :-: |
| 3.5.1 | 验证模型开发、测试和生产环境在物理上或逻辑上是分离的。它们没有共享的基础设施、各自独立的访问控制，并且数据存储彼此隔离。 |  1  |  D  |
| 3.5.2 | 请验证模型训练和微调是否在隔离的环境中进行，且网络访问受控。                               |  1  |  D  |
| 3.5.3 | 在用于模型开发之前，确保训练数据源已通过完整性检查进行验证，并通过可信来源进行身份认证，并具备文档化的保管链以便追溯。  |  1  | D/V |
| 3.5.4 | 验证模型开发工件（超参数、训练脚本、配置文件）是否已被放入版本控制，并且在用于训练之前需要获得同行评审的批准。      |  2  |  D  |

---

## C3.6 模型退役与下线

模型在不再需要或发现安全问题时，必须被安全地退役。

|   #   | 描述                                                                     | 等级  | 角色  |
| :---: | ---------------------------------------------------------------------- | :-: | :-: |
| 3.6.1 | 验证模型退役流程是否会自动扫描依赖图、识别所有使用该模型输出结果的系统，并在退役之前提供事先商定的通知期。                  |  1  |  D  |
| 3.6.2 | 验证已退役的模型工件是否通过密码擦除或多次覆盖被安全清除，符合已记录的数据保留策略，并附有经过验证的销毁证明。                |  1  | D/V |
| 3.6.3 | 验证模型下线事件是否记录了时间戳和执行者身份，以及模型签名是否已被吊销以防止重复使用。                            |  2  |  V  |
| 3.6.4 | 验证在发现关键安全漏洞时，紧急模型退役是否能够在 pre-established 应急响应时间框架内，通过自动化的关停开关禁用对模型的访问。 |  2  | D/V |

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

