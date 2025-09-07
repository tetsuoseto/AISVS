# C7 模型行為、輸出控制與安全保障

## 控制目標

模型輸出必須具備結構化、可靠、安全、可解釋性，並在生產環境中持續監控。如此可減少幻覺現象、隱私洩漏、有害內容及失控行為，同時提升用戶信任與法規遵循。

---

## C7.1 輸出格式強制執行

嚴格的結構、受限制的解碼以及後續驗證可在錯誤格式或惡意內容傳播之前予以阻止。

|   #   | 描述                                                                 | 等級  | 角色  |
| :---: | ------------------------------------------------------------------ | :-: | :-: |
| 7.1.1 | 驗證回應結構（例如，JSON Schema）是否已在系統提示中提供，並且每個輸出都會自動進行驗證；不符合要求的輸出會觸發修正或拒絕。 |  1  | D/V |
| 7.1.2 | 確認已啟用受限解碼（停止標記、正則表達式、最大標記數）以防止溢位或提示注入側信道。                          |  1  | D/V |
| 7.1.3 | 確認下游組件將輸出視為不可信，並根據架構或注入安全的反序列化器進行驗證。                               |  2  | D/V |
| 7.1.4 | 驗證不當輸出事件是否被記錄、速率限制，並呈現於監控系統中。                                      |  3  |  V  |

---

## C7.2 幻覺檢測與緩解

不確定性估計和備援策略抑制虛構答案。

|   #   | 描述                                              | 等級  | 角色  |
| :---: | ----------------------------------------------- | :-: | :-: |
| 7.2.1 | 驗證標記級別的對數機率、集成自洽性或微調的幻想檢測器是否為每個答案分配信心分數。        |  1  | D/V |
| 7.2.2 | 驗證低於可配置信心水準的回應是否會觸發備援工作流程（例如，檢索增強生成、次要模型或人工審查）。 |  1  | D/V |
| 7.2.3 | 確認幻覺事件已標記根本原因元資料，並送入事後分析及微調流程。                  |  2  | D/V |
| 7.2.4 | 確認在重大模型或知識庫更新後，閾值和偵測器已重新校準。                     |  3  | D/V |
| 7.2.5 | 驗證儀表板視覺化是否追蹤幻覺率。                                |  3  |  V  |

---

## C7.3 輸出安全與隱私過濾

政策篩選器和紅隊覆蓋保護用戶和機密數據。

|   #   | 描述                                          | 等級  | 角色  |
| :---: | ------------------------------------------- | :-: | :-: |
| 7.3.1 | 驗證生成前和生成後的分類器是否根據政策阻擋仇恨、騷擾、自我傷害、極端主義和性露骨內容。 |  1  | D/V |
| 7.3.2 | 確認每個回應都執行 PII/PCI 偵測和自動遮蔽；違規會引發隱私事件。        |  1  | D/V |
| 7.3.3 | 確認機密標籤（例如，商業秘密）能跨模態傳遞，以防止在文本、圖像或程式碼中洩漏。     |  2  |  D  |
| 7.3.4 | 驗證過濾器繞過嘗試或高風險分類是否需要二次批准或用戶重新驗證。             |  3  | D/V |
| 7.3.5 | 確認過濾門檻符合法律管轄範圍及使用者年齡/角色的情境。                 |  3  | D/V |

---

## C7.4 輸出與行動限制

速率限制和批准門檻可防止濫用和過度自主。

|   #   | 描述                                                  | 等級  | 角色  |
| :---: | --------------------------------------------------- | :-: | :-: |
| 7.4.1 | 驗證每用戶和每 API 密鑰的配額是否限制請求、令牌和成本，並在遇到 429 錯誤時採用指數退避策略。 |  1  |  D  |
| 7.4.2 | 驗證特權操作（檔案寫入、程式碼執行、網路呼叫）是否需要基於政策的批准或人工介入。            |  1  | D/V |
| 7.4.3 | 驗證跨模態一致性檢查能確保為同一請求生成的圖像、程式碼和文本無法用於夾帶惡意內容。           |  2  | D/V |
| 7.4.4 | 確認代理委派深度、遞歸限制和允許的工具列表已明確配置。                         |  2  |  D  |
| 7.4.5 | 驗證違反限制是否會發出結構化的安全事件，以供 SIEM 吸收。                     |  3  |  V  |

---

## C7.5 輸出可解釋性

透明信號提升使用者信任與內部除錯能力。

|   #   | 描述                                   | 等級  | 角色  |
| :---: | ------------------------------------ | :-: | :-: |
| 7.5.1 | 確認在風險評估認為適當時，會顯示面向用戶的信心分數或簡要的推理摘要。   |  2  | D/V |
| 7.5.2 | 確認生成的解釋避免透露敏感系統提示或專有數據。              |  2  | D/V |
| 7.5.3 | 驗證系統是否擷取了標記層級的對數機率或注意力圖，並將其存儲以供授權檢查。 |  3  |  D  |
| 7.5.4 | 確認可解釋性產物與模型發佈一同進行版本控制，以確保可審核性。       |  3  |  V  |

---

## C7.6 監控整合

即時可觀察性締結了開發與生產之間的閉環。

|   #   | 描述                                           | 等級  | 角色  |
| :---: | -------------------------------------------- | :-: | :-: |
| 7.6.1 | 驗證指標（架構違規、幻覺率、有害性、個人識別資訊洩漏、延遲、成本）是否流向中央監控平台。 |  1  |  D  |
| 7.6.2 | 確認每個安全指標都有設定警報閾值，並且具備值班升級路徑。                 |  1  |  V  |
| 7.6.3 | 驗證儀表板是否將輸出異常與模型/版本、功能標誌以及上游數據變更相關聯。          |  2  |  V  |
| 7.6.4 | 確認監控數據反饋回重新訓練、微調或規則更新，並納入有文件記錄的 MLOps 工作流程中。 |  2  | D/V |
| 7.6.5 | 確認監控管線已經過滲透測試並設有存取控制，以避免敏感日誌洩漏。              |  3  |  V  |

---

## 7.7 生成媒體防護措施

確保 AI 系統透過執行政策限制、輸出驗證和可追溯性，不生成非法、有害或未經授權的媒體內容。

|   #   | 描述                                                     | 等級  | 角色  |
| :---: | ------------------------------------------------------ | :-: | :-: |
| 7.7.1 | 確認系統提示和用戶指示明確禁止生成非法、有害或未經同意的合成媒體（例如，圖片、視頻、音頻）。         |  1  | D/V |
| 7.7.2 | 確認提示詞是否經過篩選，以阻止生成冒充行為、色情深度偽造或未經同意描繪真實個人的媒體。            |  2  | D/V |
| 7.7.3 | 確認系統使用感知哈希、浮水印檢測或指紋技術，以防止未經授權複製受版權保護的媒體。               |  2  |  V  |
| 7.7.4 | 驗證所有生成的媒體均經過密碼學簽名、加水印，或嵌入防篡改的來源元資料，以便下游追蹤。             |  3  | D/V |
| 7.7.5 | 驗證繞過嘗試（例如，提示混淆、俚語、對抗性措辭）是否被偵測、記錄及速率限制；重複濫用行為應被呈報至監控系統。 |  3  |  V  |

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

