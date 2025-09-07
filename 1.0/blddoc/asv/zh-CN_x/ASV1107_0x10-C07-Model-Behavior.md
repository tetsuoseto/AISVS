# C7 模型行为、输出控制与安全保障

## 控制目标

模型输出必须结构化、可靠、安全、可解释，并在生产中持续监控。这样可以减少幻觉、隐私泄露、有害内容和失控行为，同时提升用户信任和法规合规性。

---

## C7.1 输出格式强制执行

严格的模式、受限解码和下游验证在错误或恶意内容传播之前予以阻止。

|   #   | 描述                                                            | 级别  | 角色  |
| :---: | ------------------------------------------------------------- | :-: | :-: |
| 7.1.1 | 验证系统提示中是否提供了响应模式（例如，JSON 模式），并确保每个输出都经过自动验证；不符合规范的输出将触发修复或拒绝。 |  1  | D/V |
| 7.1.2 | 验证已启用约束解码（停止令牌、正则表达式、最大令牌数）以防止溢出或提示注入侧信道。                     |  1  | D/V |
| 7.1.3 | 验证下游组件将输出视为不可信，并根据模式或防注入的反序列化器进行验证。                           |  2  | D/V |
| 7.1.4 | 验证不当输出事件是否被记录、限流，并显示在监控中。                                     |  3  |  V  |

---

## C7.2 幻觉检测与缓解

不确定性估计和回退策略抑制虚构答案。

|   #   | 描述                                              | 级别  | 角色  |
| :---: | ----------------------------------------------- | :-: | :-: |
| 7.2.1 | 验证令牌级别的对数概率、集成自洽性或微调的幻觉检测器是否为每个答案分配置信度评分。       |  1  | D/V |
| 7.2.2 | 验证低于可配置置信度阈值的响应是否会触发后备工作流（例如，检索增强生成、辅助模型或人工审核）。 |  1  | D/V |
| 7.2.3 | 验证幻觉事件是否带有根本原因元数据标签，并送入事后分析和微调流程。               |  2  | D/V |
| 7.2.4 | 确认在重大模型或知识库更新后阈值和检测器已重新校准。                      |  3  | D/V |
| 7.2.5 | 验证仪表板可视化是否跟踪幻觉率。                                |  3  |  V  |

---

## C7.3 输出安全与隐私过滤

策略过滤器和红队覆盖保护用户和机密数据。

|   #   | 描述                                           | 级别  | 角色  |
| :---: | -------------------------------------------- | :-: | :-: |
| 7.3.1 | 验证生成前和生成后分类器是否按照政策阻止仇恨、骚扰、自残、极端主义和性露骨内容。     |  1  | D/V |
| 7.3.2 | 验证每个响应中是否运行了个人身份信息/支付卡信息检测和自动涂黑；违规行为会引发隐私事件。 |  1  | D/V |
| 7.3.3 | 验证机密性标签（例如商业秘密）是否在不同模态间传播，以防止文本、图像或代码泄露。     |  2  |  D  |
| 7.3.4 | 验证过滤器绕过尝试或高风险分类是否需要二次批准或用户重新认证。              |  3  | D/V |
| 7.3.5 | 验证过滤阈值是否反映法律管辖区以及用户年龄/角色的上下文。                |  3  | D/V |

---

## C7.4 输出与动作限制

速率限制和批准门控防止滥用和过度自主。

|   #   | 描述                                                     | 级别  | 角色  |
| :---: | ------------------------------------------------------ | :-: | :-: |
| 7.4.1 | 验证每个用户和每个 API 密钥的配额限制请求次数、令牌数和成本，并在遇到 429 错误时采用指数退避机制。 |  1  |  D  |
| 7.4.2 | 验证特权操作（文件写入、代码执行、网络调用）是否需要基于策略的批准或人为干预。                |  1  | D/V |
| 7.4.3 | 验证跨模态一致性检查确保为同一请求生成的图像、代码和文本不能被用来夹带恶意内容。               |  2  | D/V |
| 7.4.4 | 验证代理委托深度、递归限制和允许的工具列表是否已明确配置。                          |  2  |  D  |
| 7.4.5 | 验证超限违规则是否会生成结构化的安全事件以供SIEM采集。                          |  3  |  V  |

---

## C7.5 输出可解释性

透明信号提升用户信任并有助于内部调试。

|   #   | 描述                                     | 级别  | 角色  |
| :---: | -------------------------------------- | :-: | :-: |
| 7.5.1 | 在风险评估认为适当时，验证是否公开了面向用户的置信度评分或简要推理摘要。   |  2  | D/V |
| 7.5.2 | 验证生成的解释是否避免泄露敏感的系统提示或专有数据。             |  2  | D/V |
| 7.5.3 | 验证系统是否捕捉了令牌级别的对数概率或注意力图，并为授权检查存储了这些数据。 |  3  |  D  |
| 7.5.4 | 验证解释性工件是否与模型发布一起进行版本控制，以便于审计。          |  3  |  V  |

---

## C7.6 监控集成

实时可观测性实现了开发与生产之间的闭环。

|   #   | 描述                                            | 级别  | 角色  |
| :---: | --------------------------------------------- | :-: | :-: |
| 7.6.1 | 验证度量指标（架构违规、幻觉率、毒性、个人身份信息泄露、延迟、成本）是否流向中央监控平台。 |  1  |  D  |
| 7.6.2 | 验证是否为每个安全指标定义了警报阈值，并且设置了值班升级路径。               |  1  |  V  |
| 7.6.3 | 验证仪表板是否将输出异常与模型/版本、功能开关和上游数据变化相关联。            |  2  |  V  |
| 7.6.4 | 验证监控数据是否反馈到带有文档记录的MLOps工作流中的重新训练、微调或规则更新。     |  2  | D/V |
| 7.6.5 | 验证监控流水线是否经过渗透测试并实施了访问控制，以避免敏感日志泄露。            |  3  |  V  |

---

## 7.7 生成媒体防护措施

确保人工智能系统通过执行政策约束、输出验证和可追溯性，避免生成非法、有害或未经授权的媒体内容。

|   #   | 描述                                                 | 级别  | 角色  |
| :---: | -------------------------------------------------- | :-: | :-: |
| 7.7.1 | 请确认系统提示和用户指令明确禁止生成非法、有害或未经同意的深度伪造媒体（例如图像、视频、音频）。   |  1  | D/V |
| 7.7.2 | 验证提示是否经过筛选，以防止生成冒充、性露骨深度伪造，或未经同意描绘真实个人的媒体。         |  2  | D/V |
| 7.7.3 | 验证系统是否使用感知哈希、水印检测或指纹识别来防止未经授权复制受版权保护的媒体。           |  2  |  V  |
| 7.7.4 | 验证所有生成的媒体是否经过加密签名、加水印，或嵌入防篡改的来源元数据，以确保下游的可追溯性。     |  3  | D/V |
| 7.7.5 | 验证绕过尝试（例如，提示混淆、俚语、对抗性措辞）是否被检测、记录和限速；重复滥用应被反馈到监控系统。 |  3  |  V  |

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

