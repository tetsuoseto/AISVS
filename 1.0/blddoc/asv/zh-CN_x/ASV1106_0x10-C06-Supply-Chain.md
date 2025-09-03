# C6 模型、框架与数据的供应链安全

## 控制目标

AI 供应‑链攻击 利用 第三方 模型、框架 或 数据集 来 植入 后门、偏见 或 易被 利用 的 代码。这些 控制 措施 提供 端‑到‑端 的 溯源、漏洞 管理 和 监控，以 保护 整个 模型 生命周期。

---

## C6.1 预训练模型审核与溯源

在进行任何微调或部署之前，评估并认证第三方模型的来源、许可和隐藏行为。

|   #   | 描述                                            | 等级  | 角色  |
| :---: | --------------------------------------------- | :-: | :-: |
| 6.1.1 | 验证确保每个第三方模型产物包含一个已签名的溯源记录，该记录标识源代码仓库及提交哈希。    |  1  | D/V |
| 6.1.2 | 在导入之前，使用自动化工具对模型进行扫描，以检查是否存在恶意层或木马触发器。        |  1  | D/V |
| 6.1.3 | 验证迁移学习中的微调是否通过对抗性评估，以检测隐藏行为。                  |  2  |  D  |
| 6.1.4 | 核实在 ML‑BOM 条目中是否记录了模型许可、出口控制标签和数据来源声明。        |  2  |  V  |
| 6.1.5 | 验证高风险模型（公开上传的权重、未经验证的创建者）在经过人工审查和签署批准之前仍保持隔离。 |  3  | D/V |

---

## C6.2 框架与库扫描

持续对机器学习框架和库进行 CVE 漏洞和恶意代码的扫描，以确保运行时栈的安全。

|   #   | 描述                                     | 等级  | 角色  |
| :---: | -------------------------------------- | :-: | :-: |
| 6.2.1 | 验证 CI 流水线是否对 AI 框架和关键库运行依赖性扫描工具。       |  1  | D/V |
| 6.2.2 | 验证关键漏洞（CVSS ≥ 7.0）是否会阻止将镜像推广到生产环境。     |  1  | D/V |
| 6.2.3 | 验证静态代码分析是否能够在分叉的或 vendor 目录中的机器学习库上运行。 |  2  |  D  |
| 6.2.4 | 请确保框架升级提案包含安全影响评估，并引用公开的 CVE 数据源。      |  2  |  V  |
| 6.2.5 | 验证运行时传感器是否对偏离已签名的 SBOM 的意外动态库加载发出告警。   |  3  |  V  |

---

## C6.3 依赖项锁定与验证

将每个依赖项锁定到不可变摘要值，并重现构建以确保产物完全相同且防篡改。

|   #   | 描述                                 | 等级  | 角色  |
| :---: | ---------------------------------- | :-: | :-: |
| 6.3.1 | 验证所有包管理器是否通过锁定文件执行版本锁定。            |  1  | D/V |
| 6.3.2 | 验证在容器引用中使用不可变摘要，而不是可变标签。           |  1  | D/V |
| 6.3.3 | 验证可复现构建检查在 CI 运行之间比较哈希值，以确保输出完全一致。 |  2  |  D  |
| 6.3.4 | 验证构建鉴证信息是否存储18个月，以确保审计可追溯性。        |  2  |  V  |
| 6.3.5 | 验证过期的依赖是否会触发自动化拉取请求来更新或分叉固定版本。     |  3  |  D  |

---

## C6.4 可信来源的强制执行

仅允许从经过密码学验证、经组织‑批准的来源下载制品，并阻止其他一切来源。

|   #   | 描述                                       | 等级  | 角色  |
| :---: | ---------------------------------------- | :-: | :-: |
| 6.4.1 | 请确保模型权重、数据集和容器仅从经批准的域名或内部注册表下载。          |  1  | D/V |
| 6.4.2 | 在本地缓存工件之前，验证 Sigstore/Cosign 签名以确保发布者身份。 |  1  | D/V |
| 6.4.3 | 验证出站代理是否阻止未认证制品的下载，以强制执行可信源策略。           |  2  |  D  |
| 6.4.4 | 验证代码库的允许名单是否每季度进行审查，并为每个条目提供业务合理性证据。     |  2  |  V  |
| 6.4.5 | 验证策略违规是否会触发对工件的隔离以及对依赖流水线运行的回滚。          |  3  |  V  |

---

## C6.5 第三方-数据集 风险评估

评估外部数据集的数据污染、偏见和法律合规性，并在它们的整个生命周期内对它们进行监控。

|   #   | 描述                                      | 等级  | 角色  |
| :---: | --------------------------------------- | :-: | :-: |
| 6.5.1 | 验证外部数据集是否经过污染风险评分（例如，数据指纹分析、异常检测）。      |  1  | D/V |
| 6.5.2 | 在数据集批准之前，确认偏倚指标（人口统计平等、机会均等）已被计算。       |  1  |  D  |
| 6.5.3 | 核实数据集的溯源信息和许可条款是否已在 ML‑BOM 条目中被记录。      |  2  |  V  |
| 6.5.4 | 验证定期监控是否能够检测托管数据集中的数据漂移或损坏。             |  2  |  V  |
| 6.5.5 | 在训练之前，验证不允许的内容（版权信息、个人身份信息）是否已通过自动清洗移除。 |  3  |  D  |

---

## C6.6 供应链攻击监控

通过 CVE 数据源、审计日志分析和红队演练，及早发现供应链威胁。

|   #   | 描述                                             | 等级  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 6.6.1 | 验证 CI/CD 审计日志是否流入 SIEM，以检测异常的包拉取或被篡改的构建步骤。     |  1  |  V  |
| 6.6.2 | 请验证事件响应手册是否包含针对被入侵的模型或库的回滚程序。                  |  2  |  D  |
| 6.6.3 | 验证在告警分诊中，威胁情报富集标签是否对 ML 专用指标（例如模型中毒 IoCs）进行标记。 |  3  |  V  |

---

## C6.7 ML‑BOM 用于模型产物

生成并对详细的面向 ML 的 SBOMs（ML‑BOMs）进行签名，以便下游用户在部署时验证组件完整性。

|   #   | 描述                                             | 等级  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 6.7.1 | 验证每个模型产物是否发布一个 ML‑BOM，其中列出数据集、权重、超参数和许可证。      |  1  | D/V |
| 6.7.2 | 验证 ML‑BOM 生成和 Cosign 签名在持续集成中实现自动化，并且在合并时是必需的。 |  1  | D/V |
| 6.7.3 | 验证在缺少任意组件元数据（哈希值、许可证）时，ML‑BOM 完整性检查是否会导致构建失败。  |  2  |  D  |
| 6.7.4 | 验证下游消费者是否能够通过 API 查询 ML-BOMs，以在部署时验证导入的模型。     |  2  |  V  |
| 6.7.5 | 验证 ML‑BOMs 是否处于版本控制并进行差异比对，以检测未授权修改。           |  3  |  V  |

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

