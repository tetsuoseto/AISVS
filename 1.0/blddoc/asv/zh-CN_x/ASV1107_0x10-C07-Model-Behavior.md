# C7 模型行为、 输出控制与安全保障

## 控制目标

模型输出在生产环境中必须具备结构化、可靠、安全、可解释，并且要持续监控。这将有助于减少幻觉、隐私泄露、有害内容和失控行为，同时提高用户信任与监管合规性。

---

## C7.1 输出格式强制执行

严格的模式、受限解码和下游验证在传播之前就能阻止格式错误或恶意内容。

|   #   | 描述                                                             | 等级  | 角色  |
| :---: | -------------------------------------------------------------- | :-: | :-: |
| 7.1.1 | 验证系统提示中是否提供响应模式（例如 JSON Schema），并对每个输出进行自动验证；不符合要求的输出将触发修复或拒绝。 |  1  | D/V |
| 7.1.2 | 验证已启用受约束解码（停止标记、正则表达式、最大令牌数），以防止溢出或提示注入相关的侧信道。                 |  1  | D/V |
| 7.1.3 | 验证下游组件将输出视为不可信，并基于模式对其进行校验，或使用防注入的反序列化器进行校验。                   |  2  | D/V |
| 7.1.4 | 验证不当输出事件是否已被记录、已进行速率限制、并暴露给监控系统。                               |  3  |  V  |

---

## C7.2 幻觉检测与缓解

不确定性估计和回退策略抑制编造的回答。

|   #   | 描述                                                                                                           | 等级  | 角色  |
| :---: | ------------------------------------------------------------------------------------------------------------ | :-: | :-: |
| 7.2.1 | 验证 token-level log-probabilities、ensemble self-consistency、或 fine-tuned hallucination detectors为每个答案分配置信度分数。 |  1  | D/V |
| 7.2.2 | 验证低于可配置的置信阈值的响应是否会触发回退工作流（例如，检索增强生成、次级模型或人工审核）。                                                              |  1  | D/V |
| 7.2.3 | 验证幻觉事件是否带有根本原因元数据，并将其送入事后分析管线和微调管线。                                                                          |  2  | D/V |
| 7.2.4 | 验证在重大模型或知识库更新后，阈值与检测器是否已重新校准。                                                                                |  3  | D/V |
| 7.2.5 | 验证仪表板的可视化是否跟踪幻觉率。                                                                                            |  3  |  V  |

---

## C7.3 输出安全性与隐私过滤

策略过滤器和红队覆盖保护用户和机密数据。

|   #   | 描述                                            | 等级  | 角色  |
| :---: | --------------------------------------------- | :-: | :-: |
| 7.3.1 | 验证生成前的分类器和生成后的分类器是否按政策屏蔽仇恨、骚扰、自残、极端主义以及露骨性内容。 |  1  | D/V |
| 7.3.2 | 验证 PII/PCI 检测和自动脱敏是否在每个响应中运行；违规将引发隐私事件。       |  1  | D/V |
| 7.3.3 | 验证保密标签（例如商业秘密）是否能够在跨模态之间传播，以防止文本、图像或代码泄漏。     |  2  |  D  |
| 7.3.4 | 验证过滤绕过尝试或高风险分类是否需要二次审批或用户重新认证。                |  3  | D/V |
| 7.3.5 | 验证过滤阈值是否考虑到法律辖区和用户年龄/角色上下文。                   |  3  | D/V |

---

## C7.4 输出 & 动作限制

速率限制与审批门槛可防止滥用和过度自治。

|   #   | 描述                                                     | 等级  | 角色  |
| :---: | ------------------------------------------------------ | :-: | :-: |
| 7.4.1 | 验证每个用户和每个 API 密钥的配额是否对请求、令牌和成本施加限制，并在 429 错误时使用指数退避策略。 |  1  |  D  |
| 7.4.2 | 验证特权操作（文件写入、代码执行、网络调用）是否需要基于策略的审批或人工在环。                |  1  | D/V |
| 7.4.3 | 验证跨模态一致性检查，确保为同一请求生成的图像、代码和文本不能被用于隐藏恶意内容。              |  2  | D/V |
| 7.4.4 | 验证智能体的委托深度、递归限制以及允许的工具列表是否已显式配置。                       |  2  |  D  |
| 7.4.5 | 验证对超出限制的违规行为是否会产生结构化的安全事件，以供 SIEM 摄取。                  |  3  |  V  |

---

## C7.5 输出可解释性

透明的信号提升用户信任和内部调试效率。

|   #   | 描述                                      | 等级  | 角色  |
| :---: | --------------------------------------- | :-: | :-: |
| 7.5.1 | 验证在风险评估被认为适当时，是否向用户披露置信度分数或简要推理摘要。      |  2  | D/V |
| 7.5.2 | 验证生成的解释是否避免泄露敏感的系统提示或专有数据。              |  2  | D/V |
| 7.5.3 | 验证系统是否能够捕获逐个令牌的对数概率或注意力图，并将其存储以供授权人员查看。 |  3  |  D  |
| 7.5.4 | 请验证可解释性产物是否与模型发布一起进行版本控制，以便审计。          |  3  |  V  |

---

## C7.6 监控集成

实时可观测性在开发与生产之间实现闭环。

|   #   | 描述                                            | 等级  | 角色  |
| :---: | --------------------------------------------- | :-: | :-: |
| 7.6.1 | 验证这些指标（模式违规、幻觉率、有害性、PII 泄漏、延迟、成本）是否传输到中央监控平台。 |  1  |  D  |
| 7.6.2 | 验证是否为每个安全指标定义了告警阈值，并具备值班升级路径。                 |  1  |  V  |
| 7.6.3 | 验证仪表板是否将输出异常与模型/版本、功能开关以及上游数据变更相关联。           |  2  |  V  |
| 7.6.4 | 验证监控数据是否在有文档化的 MLOps 工作流中反馈用于再训练、微调或规则更新。     |  2  | D/V |
| 7.6.5 | 确保监控管线经过渗透测试并实施访问控制，以防止敏感日志泄漏。                |  3  |  V  |

---

## 7.7 生成式媒体安全措施

通过执行政策约束、输出验证和可追溯性来确保 AI 系统不生成非法、有害或未经授权的媒体内容。

|   #   | 描述                                                    | 等级  | 角色  |
| :---: | ----------------------------------------------------- | :-: | :-: |
| 7.7.1 | 验证系统提示和用户指令是否明确禁止生成非法、有害或未经同意的深度伪造媒体（例如图像、视频、音频）。     |  1  | D/V |
| 7.7.2 | 请确保对试图生成冒充、性露骨的深度伪造内容，或未获同意便展示真实个人的媒体内容的尝试进行过滤。       |  2  | D/V |
| 7.7.3 | 请验证系统是否使用感知哈希算法、水印检测或指纹识别来防止未经授权复制受版权保护的媒体。           |  2  |  V  |
| 7.7.4 | 验证所有生成的媒体是否进行了密码学签名、嵌入水印，或嵌入防篡改的溯源元数据，以实现下游可追溯性。      |  3  | D/V |
| 7.7.5 | 验证旁路尝试（例如，提示混淆、俚语、对抗性措辞）是否被检测、记录并实施速率限制；重复滥用将上报至监控系统。 |  3  |  V  |

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

