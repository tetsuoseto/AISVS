# C7 模型行為、輸出控制與安全保障

## 控制目標

模型輸出必須在生產環境中結構化、可靠、安全、可解釋，並持續監控。這樣可以降低幻覺、隱私洩漏、有害內容、以及失控行為，同時提高使用者信任與法規遵循。

---

## C7.1 輸出格式強制

嚴格的模式、受限的解碼，以及下游驗證，能在內容傳播之前阻止格式錯誤或惡意內容。

|   #   | 描述                                                           | 等級  | 角色  |
| :---: | ------------------------------------------------------------ | :-: | :-: |
| 7.1.1 | 驗證在系統提示中是否提供回應架構（例如 JSON Schema），並確保每個輸出都會自動驗證；不符合者將觸發修正或拒絕。 |  1  | D/V |
| 7.1.2 | 驗證是否已啟用受限解碼（停止標記、正則表達式、最大詞元數），以防止溢出或提示注入副通道。                 |  1  | D/V |
| 7.1.3 | 確認下游元件將輸出視為不可信，並根據模式對其進行驗證，或使用具防注入功能的反序列化器進行驗證。              |  2  | D/V |
| 7.1.4 | 驗證不當輸出事件是否已被記錄、是否已實施速率限制，並呈現給監控系統。                           |  3  |  V  |

---

## C7.2 幻覺偵測與緩解

不確定性估計與回退策略可抑制編造的回答。

|   #   | 描述                                                   | 等級  | 角色  |
| :---: | ---------------------------------------------------- | :-: | :-: |
| 7.2.1 | 驗證以 token 為單位的對數機率、集成自洽性，或經過微調的幻覺檢測器，是否能為每個答案分配信心分數。 |  1  | D/V |
| 7.2.2 | 驗證低於可配置的置信度閾值的回應是否會觸發回退工作流程（例如，檢索增強生成、次要模型或人工審核）。    |  1  | D/V |
| 7.2.3 | 驗證幻覺事件是否已標註根本原因元資料，並送入事後分析與微調管線。                     |  2  | D/V |
| 7.2.4 | 驗證在重大模型或知識庫更新之後，閾值與偵測器是否已重新校準。                       |  3  | D/V |
| 7.2.5 | 驗證儀表板的可視化是否能追蹤幻覺率。                                   |  3  |  V  |

---

## C7.3 輸出 安全性 & 隱私 過濾

政策過濾與紅隊覆蓋保護用戶與機密資料。

|   #   | 描述                                             | 等級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 7.3.1 | 驗證生成前與生成後的分類器是否能阻止仇恨、騷擾、自我傷害、極端主義以及色情內容，且符合政策。 |  1  | D/V |
| 7.3.2 | 請確保在每次回應中都執行 PII/PCI 偵測與自動遮蔽；若有違規，將引發隱私事件。     |  1  | D/V |
| 7.3.3 | 驗證機密標籤（例如商業秘密）是否能在跨模態間傳播，以防止洩漏到文本、圖像或程式碼中。     |  2  |  D  |
| 7.3.4 | 確認過濾器繞過嘗試或高風險分類是否需要二次批准或使用者重新認證。               |  3  | D/V |
| 7.3.5 | 驗證過濾閾值是否反映法律管轄區與使用者年齡/角色的情境。                   |  3  | D/V |

---

## C7.4 輸出與行動限制

速率限制與審核門檻可防止濫用與過度自治。

|   #   | 描述                                                          | 等級  | 角色  |
| :---: | ----------------------------------------------------------- | :-: | :-: |
| 7.4.1 | 驗證 per-user 和 per-API-key 配額在 429 錯誤時對請求、代幣和成本施加限制，並採用指數退避。 |  1  |  D  |
| 7.4.2 | 驗證特權操作（檔案寫入、程式碼執行、網路呼叫）是否需要以政策為基礎的批准或人工介入。                  |  1  | D/V |
| 7.4.3 | 驗證跨模態一致性檢查，確保同一請求產生的影像、程式碼與文字不能被用來走私惡意內容。                   |  2  | D/V |
| 7.4.4 | 驗證代理委派深度、遞迴限制，以及允許的工具清單是否已明確配置。                             |  2  |  D  |
| 7.4.5 | 驗證超出限制的情況是否會產生結構化的安全事件，以供 SIEM 匯入。                          |  3  |  V  |

---

## C7.5 輸出可解釋性

透明的信號能提升用戶信任與內部除錯能力。

|   #   | 描述                                      | 等級  | 角色  |
| :---: | --------------------------------------- | :-: | :-: |
| 7.5.1 | 驗證在風險評估認為適當時，是否向使用者顯示可信度分數或簡要推理摘要。      |  2  | D/V |
| 7.5.2 | 驗證生成的解釋是否避免洩露敏感的系統提示或專有資料。              |  2  | D/V |
| 7.5.3 | 驗證系統是否會捕捉以詞元為單位的對數機率或注意力圖，並將它們儲存以供授權檢查。 |  3  |  D  |
| 7.5.4 | 驗證可解釋性工件是否與模型發布同時進行版本控制，以確保審計可追溯性。      |  3  |  V  |

---

## C7.6 監控整合

實時可觀測性在開發與生產之間建立閉環。

|   #   | 描述                                            | 等級  | 角色  |
| :---: | --------------------------------------------- | :-: | :-: |
| 7.6.1 | 驗證指標（架構違規、幻覺率、有害性、PII 洩漏、延遲、成本）是否流向中央監控平台。    |  1  |  D  |
| 7.6.2 | 請確認每個安全指標均已定義警報閾值，並具備待命升級路徑。                  |  1  |  V  |
| 7.6.3 | 驗證儀表板是否能將輸出異常與模型/版本、功能旗標以及上游資料變更相關聯。          |  2  |  V  |
| 7.6.4 | 驗證監控資料是否會回饋至再訓練、微調或規則更新，並納入已文件化的 MLOps 工作流程中。 |  2  | D/V |
| 7.6.5 | 驗證監控管線是否已經過滲透測試，並實施存取控制，以防止敏感日誌洩漏。            |  3  |  V  |

---

## 7.7 生成式媒體安全措施

透過執行政策約束、輸出驗證與可追溯性，確保 AI 系統不會產生非法、有害或未經授權的媒體內容。

|   #   | 描述                                                    | 等級  | 角色  |
| :---: | ----------------------------------------------------- | :-: | :-: |
| 7.7.1 | 確認系統提示與使用者指示是否明確禁止生成非法、有害或未經同意的深偽媒體（例如圖像、視頻、音頻）。      |  1  | D/V |
| 7.7.2 | 驗證提示是否已過濾，以防止試圖生成冒充他人、含性露骨內容的深度偽造影像，或未經同意而描繪真人的媒體。    |  2  | D/V |
| 7.7.3 | 驗證系統是否使用感知雜湊、水印檢測或內容指紋技術，以防止未經授權複製受版權保護的媒體內容。         |  2  |  V  |
| 7.7.4 | 請確認所有生成的媒體均以密碼學簽名、嵌入水印，或嵌入具防篡改性的溯源元資料，以利下游追溯。         |  3  | D/V |
| 7.7.5 | 驗證繞過嘗試（例如提示混淆、俚語、對抗性措辭）是否被偵測、記錄並施以速率限制；重複濫用會被上報至監控系統。 |  3  |  V  |

## 參考文獻

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

