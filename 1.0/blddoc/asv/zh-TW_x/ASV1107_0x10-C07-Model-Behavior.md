# C7 模型行為、輸出控制與安全保障

## 控制目標

模型輸出必須具備結構化、可靠、安全、可解釋性，並在生產環境中持續監控。這樣做可以減少幻覺、隱私洩漏、有害內容和失控行為，同時提升用戶信任和法規遵從。

---

## C7.1 輸出格式強制執行

嚴格的結構、限制解碼和後續驗證可以在錯誤格式或惡意內容傳播之前將其阻止。

|   #   | 描述                                                                | 層級  | 角色  |
| :---: | ----------------------------------------------------------------- | :-: | :-: |
| 7.1.1 | 驗證系統提示中是否提供了回應結構（例如 JSON Schema），並且每個輸出都會自動進行驗證；不符合規範的輸出會觸發修正或拒絕。 |  1  | D/V |
| 7.1.2 | 確認已啟用受限解碼（停止符號、正則表達式、最大令牌數）以防止溢出或提示注入旁道攻擊。                        |  1  | D/V |
| 7.1.3 | 確保下游元件將輸出視為不受信任，並根據架構驗證或使用防注入的反序列化器進行驗證。                          |  2  | D/V |
| 7.1.4 | 確認不當輸出事件是否被記錄、速率限制，並呈現於監控系統。                                      |  3  |  V  |

---

## C7.2 幻覺檢測與緩解

不確定性估計和應急策略限制了虛構答案的出現。

|   #   | 描述                                              | 層級  | 角色  |
| :---: | ----------------------------------------------- | :-: | :-: |
| 7.2.1 | 確認標記級別的對數機率、集成自我一致性或微調的虛假資訊檢測器是否為每個答案分配信心分數。    |  1  | D/V |
| 7.2.2 | 驗證低於可配置信心閾值的回應是否會觸發後備流程（例如，檢索增強生成功能、次要模型或人工審查）。 |  1  | D/V |
| 7.2.3 | 確認幻覺事件已標註根本原因元數據，並輸入到事後分析及微調流程中。                |  2  | D/V |
| 7.2.4 | 確認在重大模型或知識庫更新後，閾值和檢測器已重新校準。                     |  3  | D/V |
| 7.2.5 | 驗證儀表板視覺化是否追蹤幻覺率。                                |  3  |  V  |

---

## C7.3 輸出安全性與隱私過濾

政策過濾器和紅隊覆蓋保護用戶和機密數據。

|   #   | 描述                                         | 層級  | 角色  |
| :---: | ------------------------------------------ | :-: | :-: |
| 7.3.1 | 驗證生成前和生成後的分類器是否依政策阻擋仇恨、騷擾、自我傷害、極端主義和性露骨內容。 |  1  | D/V |
| 7.3.2 | 確認在每個回應中執行 PII/PCI 偵測與自動遮蔽；違規情況會引發隱私事件。    |  1  | D/V |
| 7.3.3 | 驗證機密標籤（例如，商業機密）是否能跨模態傳播，以防止在文字、圖像或程式碼中洩漏。  |  2  |  D  |
| 7.3.4 | 確認過濾器繞過嘗試或高風險分類需要次級批准或用戶重新身份驗證。            |  3  | D/V |
| 7.3.5 | 驗證篩選閾值是否反映法律管轄區以及使用者年齡/角色的上下文。             |  3  | D/V |

---

## C7.4 輸出與行動限制

速率限制和審核門檻可防止濫用和過度自主。

|   #   | 描述                                                 | 層級  | 角色  |
| :---: | -------------------------------------------------- | :-: | :-: |
| 7.4.1 | 驗證每用戶和每 API 金鑰配額是否限制請求數、令牌數和成本，並在遇到 429 錯誤時採用指數退避。 |  1  |  D  |
| 7.4.2 | 驗證特權操作（檔案寫入、程式碼執行、網路呼叫）是否需要基於政策的批准或人機介入。           |  1  | D/V |
| 7.4.3 | 驗證跨模態一致性檢查確保為相同請求生成的圖像、代碼和文本無法用於夾帶惡意內容。            |  2  | D/V |
| 7.4.4 | 確認代理授權深度、遞迴限制和允許的工具清單已明確配置。                        |  2  |  D  |
| 7.4.5 | 驗證違反限制是否會發出結構化的安全事件以供 SIEM 收集。                     |  3  |  V  |

---

## C7.5 輸出可解釋性

透明信號提升用戶信任與內部除錯效能。

|   #   | 描述                                   | 層級  | 角色  |
| :---: | ------------------------------------ | :-: | :-: |
| 7.5.1 | 當風險評估認為適當時，請確認向使用者顯示信心分數或簡要推理摘要。     |  2  | D/V |
| 7.5.2 | 確認生成的解釋避免洩露敏感的系統提示或專有數據。             |  2  | D/V |
| 7.5.3 | 驗證系統是否擷取了詞元層級的對數機率或注意力圖，並將其儲存以供授權檢查。 |  3  |  D  |
| 7.5.4 | 確認解釋性工件與模型版本發布一同進行版本控制，以確保可審計性。      |  3  |  V  |

---

## C7.6 監控整合

即時可觀察性縮短了開發與生產之間的回饋環。

|   #   | 描述                                            | 層級  | 角色  |
| :---: | --------------------------------------------- | :-: | :-: |
| 7.6.1 | 驗證指標（架構違規、幻覺率、有害性、個人識別資訊洩漏、延遲、成本）是否能流向中央監控平台。 |  1  |  D  |
| 7.6.2 | 確認已為每個安全指標定義警報閾值，並設有隨叫隨到的升級路徑。                |  1  |  V  |
| 7.6.3 | 驗證儀表板是否將輸出異常與模型/版本、功能標誌和上游數據變更相關聯。            |  2  |  V  |
| 7.6.4 | 確認監控數據能反饋至重新訓練、微調或在有文件記錄的 MLOps 工作流程中進行規則更新。  |  2  | D/V |
| 7.6.5 | 確認監控管道已進行滲透測試並具備存取控制，以避免敏感日誌洩漏。               |  3  |  V  |

---

## 7.7 生成媒體防護措施

確保 AI 系統透過執行政策限制、輸出驗證及可追溯性，不產生違法、有害或未經授權的媒體內容。

|   #   | 描述                                                     | 層級  | 角色  |
| :---: | ------------------------------------------------------ | :-: | :-: |
| 7.7.1 | 請確認系統提示和用戶指示明確禁止生成非法、有害或未經同意的深度偽造媒體（例如，圖像、視頻、音頻）。      |  1  | D/V |
| 7.7.2 | 驗證提示是否已過濾試圖生成冒充、色情深度合成或未經同意描繪真實個體的媒體的內容。               |  2  | D/V |
| 7.7.3 | 確認系統使用感知式雜湊、浮水印檢測或指紋識別，以防止未經授權的版權媒體複製。                 |  2  |  V  |
| 7.7.4 | 驗證所有生成的媒體是否經過加密簽名、加水印，或嵌入具有防篡改功能的來源元資料，以利下游追蹤。         |  3  | D/V |
| 7.7.5 | 確認繞過嘗試（例如，提示混淆、俚語、對抗性措辭）被偵測、記錄並進行速率限制；重複濫用行為會被呈現給監控系統。 |  3  |  V  |

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

