# C1 培訓數據治理與偏差管理

## 控制目標

訓練數據必須以保存來源、 安全性、 質量和公平性的方式取得、 處理和維護。 如此可履行法律責任， 並降低在訓練過程中出現的偏見、 破壞或隱私洩漏風險， 這些風險可能影響整個人工智慧生命週期。

---

## C1.1 訓練數據來源

維持可驗證的所有資料集清單，只接受可信來源，並記錄每次更動以便審計。

|   #   | 描述                                                       | 層級  | 角色  |
| :---: | -------------------------------------------------------- | :-: | :-: |
| 1.1.1 | 確認維護一份最新的每個訓練數據來源（來源、管理者/擁有者、授權、收集方法、預期使用限制與處理歷史）的清單。    |  1  | D/V |
| 1.1.2 | 驗證訓練數據處理過程中排除不必要的特徵、屬性或欄位（例如，未使用的元資料、敏感的個人身份資訊、洩漏的測試數據）。 |  1  | D/V |
| 1.1.3 | 驗證所有數據集變更均需經過已記錄的審批工作流程。                                 |  2  | D/V |
| 1.1.4 | 確認在可行的情況下，資料集或子集已被加上水印或指紋標記。                             |  3  | D/V |

---

## C1.2 訓練數據安全性與完整性

限制對訓練數據的存取，並在靜止和傳輸過程中對其進行加密，驗證其完整性，以防篡改、竊取或數據中毒。

|   #   | 描述                                             | 層級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 1.2.1 | 驗證存取控制是否保護訓練數據存儲和流程管線。                         |  1  | D/V |
| 1.2.2 | 驗證所有對訓練數據的存取是否有記錄，包括使用者、時間和操作。                 |  2  | D/V |
| 1.2.3 | 驗證訓練資料集在傳輸和靜態存儲時均已加密，並使用業界標準的加密演算法及密鑰管理實踐。     |  2  | D/V |
| 1.2.4 | 確認在訓練數據儲存和傳輸過程中使用密碼散列或數位簽名來確保數據完整性。            |  2  | D/V |
| 1.2.5 | 確認已應用自動化偵測技術以防止訓練資料的未授權修改或損毀。                  |  2  | D/V |
| 1.2.6 | 確認已安全地清除或匿名化過時的訓練數據。                           |  2  | D/V |
| 1.2.7 | 驗證所有訓練數據集版本是否具有唯一標識、以不可變方式儲存，並且可審計，以支持回滾和取證分析。 |  3  | D/V |

---

## C1.3 訓練資料標註的品質、完整性與安全性

保護標籤並要求對關鍵數據進行技術審查。

|   #   | 描述                                                  | 層級  | 角色  |
| :---: | --------------------------------------------------- | :-: | :-: |
| 1.3.1 | 驗證是否對標籤產物應用了密碼學雜湊或數位簽章，以確保其完整性和真實性。                 |  2  | D/V |
| 1.3.2 | 驗證標註介面和平台是否強制執行嚴格的存取控制，維護所有標註活動的防篡改審計日誌，並防止未經授權的修改。 |  2  | D/V |
| 1.3.3 | 確認標籤中的敏感資訊在靜態及傳輸過程中於資料欄位層級已被刪除、匿名化或加密。              |  3  | D/V |

---

## C1.4 訓練數據質量與安全保障

結合自動驗證、手動抽查以及記錄的修復，以確保數據集的可靠性。

|   #   | 描述                                                                                                                   | 層級  | 角色  |
| :---: | -------------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 1.4.1 | 驗證自動化測試是否能在每次資料擷取或重大資料轉換時捕捉格式錯誤和空值。                                                                                  |  1  |  D  |
| 1.4.2 | 驗證大型語言模型（LLM）訓練和微調流程是否實施了中毒檢測與數據完整性驗證（例如，統計方法、異常值檢測、嵌入分析），以識別潛在的中毒攻擊（例如，標籤翻轉、後門觸發插入、角色切換命令、有影響力的實例攻擊）或訓練數據中的非故意數據損壞。 |  2  | D/V |
| 1.4.3 | 確認根據風險評估，對相關模型實施並調整適當的防禦措施，例如對抗訓練（使用生成的對抗樣本）、帶有擾動輸入的資料增強，或強健優化技術。                                                    |  3  | D/V |
| 1.4.4 | 驗證自動生成的標籤（例如，通過大型語言模型或弱監督）是否受到信心閾值和一致性檢查的約束，以檢測虛構、誤導或低信心的標籤。                                                         |  2  | D/V |
| 1.4.5 | 驗證自動化測試能在每次資料導入或重大資料轉換時抓取標籤偏移。                                                                                       |  3  |  D  |

---

## C1.5 資料沿革與可追蹤性

追蹤每個數據點從來源到模型輸入的完整過程，以便審計和事件應對。

|   #   | 描述                                                         | 層級  | 角色  |
| :---: | ---------------------------------------------------------- | :-: | :-: |
| 1.5.1 | 確認每個數據點的血統，包括所有轉換、增強和合併都被記錄並且可以重建。                         |  2  | D/V |
| 1.5.2 | 驗證血統記錄是不可變更、安全存儲且可供審計訪問的。                                  |  2  | D/V |
| 1.5.3 | 確認血統追蹤涵蓋通過隱私保護或生成技術生成的合成數據，並確保所有合成數據在整個流程中都被清楚標示且可與真實數據區分。 |  2  | D/V |

---

## 參考文獻

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

