# C13 人類監督、問責與治理

## 控制目標

本章節提供在 AI 系統中維持人類監督與清晰問責鏈的要求，確保在整個 AI 生命週期中具可解釋性、透明度與倫理治理。

---

## C13.1 緊急停止開關與覆蓋機制

當觀察到 AI 系統出現不安全行為時，提供關機或回滾的路徑。

|   #    | 描述                                  | 等級  | 角色  |
| :----: | ----------------------------------- | :-: | :-: |
| 13.1.1 | 驗證是否存在手動緊急停止開關機制，以便立即中止 AI 模型推理與輸出。 |  1  | D/V |
| 13.1.2 | 驗證覆寫控制僅供經授權人員使用。                    |  1  |  D  |
| 13.1.3 | 驗證回滾程序是否能回到先前的模型版本，或在安全模式下運作。       |  3  | D/V |
| 13.1.4 | 驗證覆寫機制是否已定期進行測試。                    |  3  |  V  |

---

## C13.2 人類在迴路中的決策檢查點

當風險水準超過預先設定的風險閾值時，需取得人工批准。

|   #    | 描述                                    | 等級  | 角色  |
| :----: | ------------------------------------- | :-: | :-: |
| 13.2.1 | 確認高風險的人工智能（AI）決策在執行前必須取得明確的人類批准。      |  1  | D/V |
| 13.2.2 | 驗證風險閾值是否已清楚定義，並自動觸發人工審查工作流程。          |  1  |  D  |
| 13.2.3 | 驗證在時間敏感的決策中，若無法在所需時限內取得人類批准，是否具備後備程序。 |  2  |  D  |
| 13.2.4 | 確保升級程序能為不同決策類型或風險類別定義明確的授權等級（如適用）。    |  3  | D/V |

---

## C13.3 責任鏈模式與可審計性

記錄操作人員的動作與模型決策。

|   #    | 描述                                        | 等級  | 角色  |
| :----: | ----------------------------------------- | :-: | :-: |
| 13.3.1 | 請驗證所有 AI 系統決策與人為干預均已被紀錄，包含時間戳、使用者身分與決策理由。 |  1  | D/V |
| 13.3.2 | 驗證審計日誌不可被篡改，並包含完整性驗證機制。                   |  2  |  D  |

---

## C13.4 可解釋的人工智慧技術

表面特徵的重要性、反事實解釋，以及局部解釋。

|   #    | 描述                                         | 等級  | 角色  |
| :----: | ------------------------------------------ | :-: | :-: |
| 13.4.1 | 驗證 AI 系統是否以人類可讀的格式提供其決策的基本解釋。              |  1  | D/V |
| 13.4.2 | 驗證解釋品質是否透過人工評估研究與指標來驗證。                    |  2  |  V  |
| 13.4.3 | 驗證特徵重要性分數或歸因方法（SHAP、LIME 等）是否可用於關鍵決策。      |  3  | D/V |
| 13.4.4 | 核實反事實解釋是否能顯示若修改輸入，結果將如何變化，前提是該做法適用於該用例與領域。 |  3  |  V  |

---

## C13.5 模型卡片與使用披露

維護模型卡，涵蓋預期用途、性能指標與倫理考量。

|   #    | 描述                                            | 等級  | 角色  |
| :----: | --------------------------------------------- | :-: | :-: |
| 13.5.1 | 確保模型卡片記錄了預期使用情境、限制，以及已知的失效模式。                 |  1  |  D  |
| 13.5.2 | 確認在不同適用用例中的性能指標已披露。                           |  1  | D/V |
| 13.5.3 | 確認倫理考量、偏見評估、公平性評估、訓練資料特性，以及已知訓練資料限制已被紀錄並定期更新。 |  2  |  D  |
| 13.5.4 | 驗證模型卡在整個模型生命週期中是否受版本控制，並透過變更追蹤進行維護。           |  2  | D/V |

---

## C13.6 不確定性量化

在回應中傳遞信心分數或熵度量。

|   #    | 描述                             | 等級  | 角色  |
| :----: | ------------------------------ | :-: | :-: |
| 13.6.1 | 驗證 AI 系統在其輸出中提供置信度分數或不確定性指標。   |  1  |  D  |
| 13.6.2 | 驗證不確定性閾值是否會觸發額外的人類審查或替代決策路徑。   |  2  | D/V |
| 13.6.3 | 請驗證不確定性量化方法是否已針對地面真值資料完成校準與驗證。 |  2  |  V  |
| 13.6.4 | 驗證在多步驟 AI 工作流程中是否保持不確定性傳遞。     |  3  | D/V |

---

## C13.7 面向用戶的透明度報告

定期披露有關事件、概念漂移與資料使用情況。

|   #    | 描述                                 | 等級  | 角色  |
| :----: | ---------------------------------- | :-: | :-: |
| 13.7.1 | 驗證數據使用政策與用戶同意管理實踐是否已清楚地傳達給利益相關者。   |  1  | D/V |
| 13.7.2 | 請確認已執行人工智能影響評估，並將結果納入報告。           |  2  | D/V |
| 13.7.3 | 核實定期發布的透明度報告是否以合理的細節披露人工智慧事件與營運指標。 |  2  | D/V |

### 參考文獻

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

