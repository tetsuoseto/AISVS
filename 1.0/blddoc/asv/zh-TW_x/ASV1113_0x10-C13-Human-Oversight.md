# C13 人類監督、問責與治理

## 控制目標

本章提供了維持人工監督和明確問責鏈的要求，確保在整個人工智慧生命周期中具備可解釋性、透明性及道德管理。

---

## C13.1 緊急停止開關與覆寫機制

當觀察到 AI 系統有不安全行為時，需提供關機或回滾方案。

|   #    | 描述                              | 層級  | 角色  |
| :----: | ------------------------------- | :-: | :-: |
| 13.1.1 | 確認存在手動緊急停止機制，可立即停止 AI 模型的推理和輸出。 |  1  | D/V |
| 13.1.2 | 確認覆蓋控制僅限授權人員能夠訪問。               |  1  |  D  |
| 13.1.3 | 驗證回滾程序能夠還原到先前的模型版本或安全模式操作。      |  3  | D/V |
| 13.1.4 | 確認覆寫機制已定期進行測試。                  |  3  |  V  |

---

## C13.2 人機互動決策檢查點

當風險超過預先定義的門檻時，需取得人工批准。

|   #    | 描述                                  | 層級  | 角色  |
| :----: | ----------------------------------- | :-: | :-: |
| 13.2.1 | 確認高風險的人工智能決策在執行前需要明確的人類批准。          |  1  | D/V |
| 13.2.2 | 確認風險閾值已明確定義，並能自動觸發人工審查工作流程。         |  1  |  D  |
| 13.2.3 | 確保在無法於規定時間內取得人為核准時，時間敏感的決策具備備援程序。   |  2  |  D  |
| 13.2.4 | 確認升級程序是否定義了不同決策類型或風險類別的明確權限等級（如適用）。 |  3  | D/V |

---

## C13.3 責任鏈與可稽核性

記錄操作員行為和模型決策。

|   #    | 描述                                        | 層級  | 角色  |
| :----: | ----------------------------------------- | :-: | :-: |
| 13.3.1 | 確認所有 AI 系統的決策和人工干預均有記錄，並包含時間戳記、用戶身份及決策理由。 |  1  | D/V |
| 13.3.2 | 驗證審計日誌無法被篡改，並包括完整性驗證機制。                   |  2  |  D  |

---

## C13.4 可解釋人工智慧技術

表面特徵重要性、反事實分析和局部解釋。

|   #    | 描述                                        | 層級  | 角色  |
| :----: | ----------------------------------------- | :-: | :-: |
| 13.4.1 | 確認 AI 系統以人類可讀的格式提供其決策的基本解釋。               |  1  | D/V |
| 13.4.2 | 驗證說明品質是否通過人工評估研究和指標進行驗證。                  |  2  |  V  |
| 13.4.3 | 確認關鍵決策是否具備特徵重要性分數或歸因方法（如 SHAP、LIME 等）。    |  3  | D/V |
| 13.4.4 | 驗證反事實解釋是否顯示輸入如何被修改以改變結果，前提是該方法適用於使用案例和領域。 |  3  |  V  |

---

## C13.5 模型卡與使用揭露

維護模型卡以記錄預期用途、性能指標與倫理考量。

|   #    | 描述                                          | 層級  | 角色  |
| :----: | ------------------------------------------- | :-: | :-: |
| 13.5.1 | 驗證模型卡是否記錄預期的使用情境、限制以及已知的失效模式。               |  1  |  D  |
| 13.5.2 | 驗證是否披露了不同適用用例中的性能指標。                        |  1  | D/V |
| 13.5.3 | 確認道德考量、偏見評估、公平性評估、訓練資料特性及已知訓練資料限制均有記錄並定期更新。 |  2  |  D  |
| 13.5.4 | 驗證模型卡是否在整個模型生命週期中進行版本控制和維護，並且有變更追蹤。         |  2  | D/V |

---

## C13.6 不確定性量化

在回應中傳播置信度分數或熵度量。

|   #    | 描述                           | 層級  | 角色  |
| :----: | ---------------------------- | :-: | :-: |
| 13.6.1 | 驗證 AI 系統是否隨其輸出提供信心分數或不確定性測量。 |  1  |  D  |
| 13.6.2 | 驗證不確定性門檻是否會觸發額外的人為審查或替代決策途徑。 |  2  | D/V |
| 13.6.3 | 確認不確定性量化方法已針對真實資料進行校正和驗證。    |  2  |  V  |
| 13.6.4 | 驗證不確定性傳播在多步驟 AI 工作流程中得以維持。   |  3  | D/V |

---

## C13.7 面向用戶的透明度報告

定期披露事件、漂移和數據使用情況。

|   #    | 描述                                | 層級  | 角色  |
| :----: | --------------------------------- | :-: | :-: |
| 13.7.1 | 確認數據使用政策和用戶同意管理措施已清楚傳達給利益相關者。     |  1  | D/V |
| 13.7.2 | 確認已進行 AI 影響評估，並將結果納入報告中。          |  2  | D/V |
| 13.7.3 | 確認定期發布的透明度報告中合理詳盡地披露了 AI 事件和運營指標。 |  2  | D/V |

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

