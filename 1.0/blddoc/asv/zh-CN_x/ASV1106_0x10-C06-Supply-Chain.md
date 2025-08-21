# C6 模型、框架和数据的供应链安全

## 控制目标

AI供应链攻击利用第三方模型、框架或数据集来嵌入后门、偏见或可利用的代码。这些控制措施提供端到端的源头追踪、漏洞管理和监控，以保护整个模型生命周期。

---

## C6.1 预训练模型审查与来源追踪

在进行任何微调或部署之前，评估并验证第三方模型的来源、许可和隐藏行为。

|   #   | 描述                                        | 等级  | 角色  |
| :---: | ----------------------------------------- | :-: | :-: |
| 6.1.1 | 验证每个第三方模型组件都包含一个签名的来源记录，标识源代码仓库和提交哈希。     |  1  | D/V |
| 6.1.2 | 确保在导入模型之前，使用自动化工具扫描模型是否包含恶意层或木马触发器。       |  1  | D/V |
| 6.1.3 | 验证迁移学习微调通过对抗性评估，以检测隐藏行为。                  |  2  |  D  |
| 6.1.4 | 验证模型许可证、出口控制标签和数据来源声明是否已记录在 ML-BOM 条目中。   |  2  |  V  |
| 6.1.5 | 验证高风险模型（公开上传的权重、未经验证的创建者）在人工审核和签署前保持隔离状态。 |  3  | D/V |

---

## C6.2 框架与库扫描

持续扫描机器学习框架和库中的CVE（公共漏洞与暴露）和恶意代码，以保持运行时堆栈的安全。

|   #   | 描述                                 | 等级  | 角色  |
| :---: | ---------------------------------- | :-: | :-: |
| 6.2.1 | 验证 CI 流水线是否对 AI 框架和关键库运行依赖扫描器。     |  1  | D/V |
| 6.2.2 | 验证关键漏洞（CVSS ≥ 7.0）是否阻止晋升到生产镜像。     |  1  | D/V |
| 6.2.3 | 验证静态代码分析是否在派生或供应的机器学习库上运行。         |  2  |  D  |
| 6.2.4 | 验证框架升级提案是否包含引用公共CVE信息源的安全影响评估。     |  2  |  V  |
| 6.2.5 | 验证运行时传感器是否能够对偏离签名SBOM的意外动态库加载发出警报。 |  3  |  V  |

---

## C6.3 依赖固定与验证

将每个依赖项固定到不可变的摘要，并重现构建以保证生成完全相同且无篡改的工件。

|   #   | 描述                               | 等级  | 角色  |
| :---: | -------------------------------- | :-: | :-: |
| 6.3.1 | 验证所有包管理器是否通过锁文件强制执行版本固定。         |  1  | D/V |
| 6.3.2 | 验证在容器引用中使用的是不可变的摘要而不是可变的标签。      |  1  | D/V |
| 6.3.3 | 验证可重复构建检查是否在持续集成运行中比较哈希值以确保输出一致。 |  2  |  D  |
| 6.3.4 | 验证构建证明已存储18个月以确保审计追溯性。           |  2  |  V  |
| 6.3.5 | 验证过期的依赖是否会触发自动拉取请求以更新或分叉固定版本。    |  3  |  D  |

---

## C6.4 可信来源强制执行

仅允许从经过密码学验证、组织批准的来源下载制品，阻止所有其他来源。

|   #   | 描述                                        | 等级  | 角色  |
| :---: | ----------------------------------------- | :-: | :-: |
| 6.4.1 | 验证模型权重、数据集和容器仅从批准的域或内部注册表下载。              |  1  | D/V |
| 6.4.2 | 验证 Sigstore/Cosign 签名在工件被本地缓存之前是否确认发布者身份。 |  1  | D/V |
| 6.4.3 | 验证出口代理阻止未经过身份验证的工件下载，以执行可信来源策略。           |  2  |  D  |
| 6.4.4 | 验证存储库允许列表是否每季度审查一次，并提供每个条目的业务理由作为证据。      |  2  |  V  |
| 6.4.5 | 验证策略违规是否触发工件的隔离以及相关管道运行的回滚。               |  3  |  V  |

---

## C6.5 第三方数据集风险评估

评估外部数据集的投毒情况、偏差和法律合规性，并在其整个生命周期内进行监控。

|   #   | 描述                                  | 等级  | 角色  |
| :---: | ----------------------------------- | :-: | :-: |
| 6.5.1 | 验证外部数据集是否经过投毒风险评分（例如，数据指纹识别、异常值检测）。 |  1  | D/V |
| 6.5.2 | 在数据集批准之前，验证偏差指标（人口统计平等性、机会均等）是否已计算。 |  1  |  D  |
| 6.5.3 | 验证数据集的来源和许可条款是否被记录在 ML-BOM 条目中。     |  2  |  V  |
| 6.5.4 | 验证定期监控是否能够检测托管数据集中的漂移或损坏。           |  2  |  V  |
| 6.5.5 | 在训练之前，验证通过自动清理已移除禁止内容（版权信息、个人身份信息）。 |  3  |  D  |

---

## C6.6 供应链攻击监控

通过CVE源、审计日志分析和红队模拟，及早发现供应链威胁。

|   #   | 描述                                           | 等级  | 角色  |
| :---: | -------------------------------------------- | :-: | :-: |
| 6.6.1 | 验证 CI/CD 审计日志是否流向 SIEM 以检测异常的软件包拉取或被篡改的构建步骤。 |  1  |  V  |
| 6.6.2 | 确认事件响应剧本中包含针对受损模型或库的回滚流程。                    |  2  |  D  |
| 6.6.3 | 验证威胁情报增强是否在警报分流中标记了特定于机器学习的指标（例如，模型投毒的IoC）。  |  3  |  V  |

---

## C6.7 模型工件的机器学习物料清单 (ML-BOM)

生成并签署详细的专用于机器学习的软体物料清单（ML-BOM），以便下游使用者在部署时能够验证组件的完整性。

|   #   | 描述                                                | 等级  | 角色  |
| :---: | ------------------------------------------------- | :-: | :-: |
| 6.7.1 | 验证每个模型工件是否发布了 ML-BOM，其中列出了数据集、权重、超参数和许可证。         |  1  | D/V |
| 6.7.2 | 验证在持续集成(CI)中，ML-BOM 生成和 Cosign 签名是自动化的，并且是合并所必需的。 |  1  | D/V |
| 6.7.3 | 验证如果任何组件元数据（哈希、许可证）缺失，ML-BOM 完整性检查会导致构建失败。        |  2  |  D  |
| 6.7.4 | 验证下游消费者是否能够通过 API 查询 ML-BOM，以在部署时验证导入的模型。         |  2  |  V  |
| 6.7.5 | 验证 ML-BOM 是否进行版本控制和差异比较，以检测未经授权的修改。               |  3  |  V  |

---

## 参考文献

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

