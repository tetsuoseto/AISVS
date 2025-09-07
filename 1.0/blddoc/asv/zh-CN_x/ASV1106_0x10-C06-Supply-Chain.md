# C6 模型、框架与数据的供应链安全

## 控制目标

AI 供应链攻击利用第三方模型、框架或数据集植入后门、偏见或可利用的代码。这些控制措施提供端到端的来源管理、漏洞管理和监控，以保护整个模型生命周期。

---

## C6.1 预训练模型审查与来源验证

在进行任何微调或部署之前，评估并验证第三方模型的来源、许可证和隐藏行为。

|   #   | 描述                                         | 级别  | 角色  |
| :---: | ------------------------------------------ | :-: | :-: |
| 6.1.1 | 验证每个第三方模型工件是否包含一个签名的来源记录，以识别源代码库和提交哈希。     |  1  | D/V |
| 6.1.2 | 确保在导入模型之前，使用自动化工具扫描模型中的恶意层或特洛伊木马触发器。       |  1  | D/V |
| 6.1.3 | 验证迁移学习微调通过对抗性评估以检测隐藏行为。                    |  2  |  D  |
| 6.1.4 | 验证模型许可证、出口管制标签和数据来源声明是否已记录在 ML-BOM 条目中。    |  2  |  V  |
| 6.1.5 | 验证高风险模型（公开上传的权重、未经验证的创建者）在人工审核和签署之前保持隔离状态。 |  3  | D/V |

---

## C6.2 框架与库扫描

持续扫描机器学习框架和库中的CVE漏洞及恶意代码，以确保运行时堆栈的安全。

|   #   | 描述                                 | 级别  | 角色  |
| :---: | ---------------------------------- | :-: | :-: |
| 6.2.1 | 验证 CI 管道是否对 AI 框架和关键库运行依赖扫描器。      |  1  | D/V |
| 6.2.2 | 验证严重漏洞（CVSS ≥ 7.0）是否阻止推广到生产镜像。     |  1  | D/V |
| 6.2.3 | 验证静态代码分析是否在派生或内置的机器学习库上运行。         |  2  |  D  |
| 6.2.4 | 验证框架升级提案是否包含引用公共CVE源的安全影响评估。       |  2  |  V  |
| 6.2.5 | 验证运行时传感器是否对偏离签名 SBOM 的意外动态库加载发出警报。 |  3  |  V  |

---

## C6.3 依赖项固定与验证

将每个依赖项固定到不可变的摘要，并重现构建以保证生成相同且防篡改的工件。

|   #   | 描述                                   | 级别  | 角色  |
| :---: | ------------------------------------ | :-: | :-: |
| 6.3.1 | 验证所有包管理器是否通过锁定文件强制执行版本固定。            |  1  | D/V |
| 6.3.2 | 验证在容器引用中使用的是不可变摘要，而不是可变标签。           |  1  | D/V |
| 6.3.3 | 验证可重现构建检查在持续集成（CI）运行之间比较哈希值，以确保输出一致。 |  2  |  D  |
| 6.3.4 | 验证构建证明是否存储了18个月以确保审计可追溯性。            |  2  |  V  |
| 6.3.5 | 验证过期的依赖项是否会触发自动拉取请求以更新或分叉固定版本。       |  3  |  D  |

---

## C6.4 可信来源执行

只允许从经过密码学验证且组织批准的来源下载工件，阻止所有其他来源。

|   #   | 描述                                         | 级别  | 角色  |
| :---: | ------------------------------------------ | :-: | :-: |
| 6.4.1 | 验证模型权重、数据集和容器仅从批准的域或内部注册表下载。               |  1  | D/V |
| 6.4.2 | 验证 Sigstore/Cosign 签名以确认发布者身份，然后再将制品缓存到本地。 |  1  | D/V |
| 6.4.3 | 验证出口代理是否阻止未经身份验证的制品下载，以强制执行可信来源策略。         |  2  |  D  |
| 6.4.4 | 验证存储库允许列表是否每季度审查一次，并提供每个条目的业务理由证明。         |  2  |  V  |
| 6.4.5 | 验证策略违规是否会触发工件隔离和依赖流水线运行的回滚。                |  3  |  V  |

---

## C6.5 第三方数据集风险评估

评估外部数据集的投毒、偏差和法律合规性，并在其整个生命周期内进行监控。

|   #   | 描述                                 | 级别  | 角色  |
| :---: | ---------------------------------- | :-: | :-: |
| 6.5.1 | 验证外部数据集是否经过中毒风险评分（例如，数据指纹识别、离群检测）。 |  1  | D/V |
| 6.5.2 | 确认在数据集批准之前计算偏差指标（人口统计平等性、均等机会）。    |  1  |  D  |
| 6.5.3 | 验证数据集的来源和许可条款是否已记录在 ML-BOM 条目中。    |  2  |  V  |
| 6.5.4 | 验证定期监控是否能够检测托管数据集中的漂移或损坏。          |  2  |  V  |
| 6.5.5 | 确认在训练前通过自动清理移除禁止内容（版权、个人身份信息）。     |  3  |  D  |

---

## C6.6 供应链攻击监控

通过CVE信息源、审计日志分析和红队模拟，及早发现供应链威胁。

|   #   | 描述                                            | 级别  | 角色  |
| :---: | --------------------------------------------- | :-: | :-: |
| 6.6.1 | 验证 CI/CD 审计日志是否传输到 SIEM 以检测异常的软件包拉取或被篡改的构建步骤。 |  1  |  V  |
| 6.6.2 | 验证事件响应剧本中是否包含受损模型或库的回滚程序。                     |  2  |  D  |
| 6.6.3 | 验证威胁情报增强是否在警报分类中标记了机器学习特定指标（例如，模型投毒指示器）。      |  3  |  V  |

---

## C6.7 模型工件的机器学习物料清单 (ML-BOM)

生成并签署详细的特定于机器学习的软体物料清单（ML-BOMs），以便下游使用者能够在部署时验证组件的完整性。

|   #   | 描述                                                  | 级别  | 角色  |
| :---: | --------------------------------------------------- | :-: | :-: |
| 6.7.1 | 验证每个模型工件是否发布了包含数据集、权重、超参数和许可证的机器学习物料清单（ML-BOM）。     |  1  | D/V |
| 6.7.2 | 验证 ML‑BOM 生成和 Cosign 签名是否在持续集成（CI）中自动执行，并且是合并的必需条件。 |  1  | D/V |
| 6.7.3 | 验证如果任何组件元数据（哈希、许可证）缺失，ML-BOM 完整性检查会导致构建失败。          |  2  |  D  |
| 6.7.4 | 验证下游消费者是否可以通过API查询ML-BOM，以在部署时验证导入的模型。              |  2  |  V  |
| 6.7.5 | 验证 ML‑BOM 是否进行了版本控制并差异比较，以检测未经授权的修改。                |  3  |  V  |

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

