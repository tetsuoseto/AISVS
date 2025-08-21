# C7 模型行为、输出控制与安全保障

## 控制目标

模型输出必须具有结构化、可靠、安全、可解释性，并在生产环境中持续监控。这样可以减少幻觉、隐私泄露、有害内容和失控行为，同时提升用户信任和合规性。

---

## C7.1 输出格式强制执行

严格的模式、受限解码和下游验证在错误或恶意内容传播之前加以阻止。

|   #   | 描述                                                               | 级别  | 角色  |
| :---: | ---------------------------------------------------------------- | :-: | :-: |
| 7.1.1 | 验证系统提示中是否提供了响应模式（例如，JSON Schema），并且每个输出都自动进行验证；不符合规范的输出将触发修复或拒绝。 |  1  | D/V |
| 7.1.2 | 验证是否启用了受限解码（停止标记、正则表达式、最大令牌数）以防止溢出或提示注入侧信道。                      |  1  | D/V |
| 7.1.3 | 验证下游组件将输出视为不受信任，并根据架构或注入安全的反序列化器对其进行验证。                          |  2  | D/V |
| 7.1.4 | 验证不当输出事件已被记录、限速，并显示在监控中。                                         |  3  |  V  |

---

## C7.2 幻觉检测与缓解

不确定性估计和回退策略抑制虚构答案。

|   #   | 描述                                               | 级别  | 角色  |
| :---: | ------------------------------------------------ | :-: | :-: |
| 7.2.1 | 验证令牌级别的对数概率、集成自洽性或微调的虚假信息检测器是否为每个答案分配置信度得分。      |  1  | D/V |
| 7.2.2 | 验证低于可配置置信度阈值的响应是否会触发回退工作流程（例如，增强检索生成、二级模型或人工审核）。 |  1  | D/V |
| 7.2.3 | 确保幻觉事件带有根本原因元数据标签，并输入到事后分析和微调管道中。                |  2  | D/V |
| 7.2.4 | 确认在重大模型或知识库更新后，阈值和检测器已重新校准。                      |  3  | D/V |
| 7.2.5 | 确认仪表板可视化跟踪幻觉率。                                   |  3  |  V  |

---

## C7.3 输出安全性与隐私过滤

策略过滤器和红队覆盖保护用户和机密数据。

|   #   | 描述                                        | 级别  | 角色  |
| :---: | ----------------------------------------- | :-: | :-: |
| 7.3.1 | 验证生成前后分类器是否阻止符合政策的仇恨、骚扰、自残、极端主义和性露骨内容。    |  1  | D/V |
| 7.3.2 | 验证每个响应中是否运行了PII/PCI检测和自动编辑；违规行为将引发隐私事件。   |  1  | D/V |
| 7.3.3 | 验证机密性标签（例如，商业秘密）是否能跨模态传播，以防止在文本、图像或代码中泄露。 |  2  |  D  |
| 7.3.4 | 验证过滤器绕过尝试或高风险分类是否需要二次审批或用户重新身份验证。         |  3  | D/V |
| 7.3.5 | 验证过滤阈值是否反映法律管辖区以及用户年龄/角色的上下文。             |  3  | D/V |

---

## C7.4 输出与动作限制

速率限制和审批关卡防止滥用和过度自主。

|   #   | 描述                                                    | 级别  | 角色  |
| :---: | ----------------------------------------------------- | :-: | :-: |
| 7.4.1 | 验证每个用户和每个 API 密钥的配额是否限制请求、令牌和成本，并在遇到 429 错误时采用指数退避策略。 |  1  |  D  |
| 7.4.2 | 验证特权操作（文件写入、代码执行、网络调用）是否需要基于策略的批准或人工干预。               |  1  | D/V |
| 7.4.3 | 验证跨模态一致性检查确保为同一请求生成的图像、代码和文本不能用于走私恶意内容。               |  2  | D/V |
| 7.4.4 | 验证代理委托深度、递归限制和允许的工具列表是否已明确配置。                         |  2  |  D  |
| 7.4.5 | 验证超出限制是否会触发结构化的安全事件以供SIEM摄取。                          |  3  |  V  |

---

## C7.5 输出可解释性

透明信号提升用户信任和内部调试能力。

|   #   | 描述                                    | 级别  | 角色  |
| :---: | ------------------------------------- | :-: | :-: |
| 7.5.1 | 确认在风险评估认为适当时，向用户展示置信度分数或简要推理总结。       |  2  | D/V |
| 7.5.2 | 验证生成的解释是否避免泄露敏感的系统提示或专有数据。            |  2  | D/V |
| 7.5.3 | 验证系统是否捕获了令牌级别的对数概率或注意力映射，并将其存储以供授权检查。 |  3  |  D  |
| 7.5.4 | 确保可解释性产物与模型发布一起进行版本控制，以便审计。           |  3  |  V  |

---

## C7.6 监控集成

实时可观测性实现了开发与生产之间的闭环。

|   #   | 描述                                           | 级别  | 角色  |
| :---: | -------------------------------------------- | :-: | :-: |
| 7.6.1 | 验证指标（模式违规、幻觉率、毒性、个人身份信息泄露、延迟、成本）是否传输到中央监控平台。 |  1  |  D  |
| 7.6.2 | 验证是否为每个安全指标定义了警报阈值，并设有值班升级路径。                |  1  |  V  |
| 7.6.3 | 验证仪表板是否将输出异常与模型/版本、功能标志和上游数据更改相关联。           |  2  |  V  |
| 7.6.4 | 验证监控数据是否反馈到已记录的 MLOps 工作流程中的再训练、微调或规则更新中。    |  2  | D/V |
| 7.6.5 | 确保监控流水线经过渗透测试并实施访问控制，以避免敏感日志泄露。              |  3  |  V  |

---

## 7.7 生成媒体安全措施

通过执行政策约束、输出验证和可追溯性，确保人工智能系统不生成非法、有害或未经授权的媒体内容。

|   #   | 描述                                                    | 级别  | 角色  |
| :---: | ----------------------------------------------------- | :-: | :-: |
| 7.7.1 | 确保系统提示和用户指令明确禁止生成非法、有害或未经同意的深度伪造媒体（例如图像、视频、音频）。       |  1  | D/V |
| 7.7.2 | 验证提示是否经过过滤，以防止生成冒充行为、色情深度伪造内容或未经同意展示真实个人的媒体。          |  2  | D/V |
| 7.7.3 | 验证系统是否使用感知哈希、水印检测或指纹识别来防止未经授权复制受版权保护的媒体。              |  2  |  V  |
| 7.7.4 | 验证所有生成的媒体是否经过加密签名、加水印，或嵌入防篡改的来源元数据，以便后续追踪。            |  3  | D/V |
| 7.7.5 | 验证绕过尝试（例如，提示混淆、俚语、对抗性措辞）是否被检测、记录和限速；重复滥用情况是否被反馈到监控系统。 |  3  |  V  |

## 参考文献

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

