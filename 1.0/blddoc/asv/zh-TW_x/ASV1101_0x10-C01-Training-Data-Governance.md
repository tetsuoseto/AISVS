# C1 訓練數據治理與偏差管理

## 控制目標

訓練資料必須以保留來源、保障安全性、維持品質與公平性的方式進行採集、處理與維護。這樣不僅符合法律義務，還能降低在訓練過程中出現偏見、中毒或隱私洩漏的風險，避免影響整個人工智慧生命週期。

---

## C1.1 訓練數據來源

維護所有資料集的可驗證清單，只接受可信來源，並記錄每次更動以便審核。

|   #   | 描述                                                           | 等級  | 角色  |
| :---: | ------------------------------------------------------------ | :-: | :-: |
| 1.1.1 | 確保維護一份最新的培訓數據來源清單，其中包括來源、管理者/擁有者、許可證、收集方法、預期使用限制及處理歷史。       |  1  | D/V |
| 1.1.2 | 確認訓練數據處理過程中排除不必要的特徵、屬性或欄位（例如，未使用的元資料、敏感個人識別資訊（PII）、洩漏的測試數據）。 |  1  | D/V |
| 1.1.3 | 確認所有數據集的更改均需經過有記錄的批准流程。                                      |  2  | D/V |
| 1.1.4 | 在可行的情況下，驗證資料集或子集是否有加水印或指紋識別。                                 |  3  | D/V |

---

## C1.2 訓練數據安全性與完整性

限制對訓練數據的存取，對其靜態及傳輸中的數據進行加密，並驗證其完整性，以防止篡改、竊取或數據中毒。

|   #   | 描述                                        | 等級  | 角色  |
| :---: | ----------------------------------------- | :-: | :-: |
| 1.2.1 | 驗證訪問控制是否保護訓練數據存儲和管道。                      |  1  | D/V |
| 1.2.2 | 驗證所有對訓練數據的訪問均有記錄，包括使用者、時間和操作。             |  2  | D/V |
| 1.2.3 | 確認訓練資料集在傳輸和靜態存儲時均採用業界標準的加密演算法及金鑰管理實務進行加密。 |  2  | D/V |
| 1.2.4 | 驗證是否使用密碼學雜湊或數位簽章以確保訓練數據存儲和傳輸過程中的數據完整性。    |  2  | D/V |
| 1.2.5 | 確認已應用自動化檢測技術以防止訓練資料遭到未經授權的修改或損壞。          |  2  | D/V |
| 1.2.6 | 驗證過時的訓練數據已被安全清除或匿名化。                      |  2  | D/V |
| 1.2.7 | 確認所有訓練資料集版本均獨特識別、不可變更儲存，且可審計，以支援回滾與取證分析。  |  3  | D/V |

---

## C1.3 訓練數據標註質量、完整性與安全性

保護標籤並要求對關鍵資料進行技術審查。

|   #   | 描述                                             | 等級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 1.3.1 | 確認已對標籤工件應用密碼學雜湊或數位簽章，以確保其完整性和真實性。              |  2  | D/V |
| 1.3.2 | 確認標註介面和平台實施強固的存取控制，維護所有標註活動的防篡改稽核日誌，並防止未授權的修改。 |  2  | D/V |
| 1.3.3 | 請確認標籤中的敏感資訊在靜態與傳輸過程中已於資料欄位層級加以遮蔽、匿名化或加密。       |  3  | D/V |

---

## C1.4 訓練數據質量與安全保障

結合自動驗證、人工抽查和記錄的修復措施，以保證數據集的可靠性。

|   #   | 描述                                                                                                                | 等級  | 角色  |
| :---: | ----------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 1.4.1 | 確認自動化測試能在每次資料攝取或重大資料轉換時偵測格式錯誤和空值。                                                                                 |  1  |  D  |
| 1.4.2 | 確認大規模語言模型（LLM）訓練與微調流程實施了中毒偵測與資料完整性驗證（例如，統計方法、異常值偵測、嵌入分析），以識別潛在的中毒攻擊（例如，標籤翻轉、後門觸發插入、角色切換指令、影響力實例攻擊）或訓練資料中的非故意資料損壞。 |  2  | D/V |
| 1.4.3 | 根據風險評估，確認已為相關模型實施並調校適當的防禦措施，例如使用生成的對抗樣本進行對抗訓練、利用擾動輸入進行數據增強，或採用穩健優化技術。                                             |  3  | D/V |
| 1.4.4 | 驗證自動生成的標籤（例如，透過大型語言模型或弱監督產生的標籤）是否經過信心閾值設定及一致性檢查，以偵測幻覺、誤導性或低信心的標籤。                                                 |  2  | D/V |
| 1.4.5 | 驗證自動化測試能夠在每次資料匯入或重大資料轉換時捕捉標籤偏移。                                                                                   |  3  |  D  |

---

## C1.5 數據血緣與可追溯性

追蹤每個數據點從來源到模型輸入的完整旅程，以確保可審計性和事件回應。

|   #   | 描述                                                          | 等級  | 角色  |
| :---: | ----------------------------------------------------------- | :-: | :-: |
| 1.5.1 | 確認每個數據點的血統，包括所有的轉換、增強和合併，都被記錄並且可以重建。                        |  2  | D/V |
| 1.5.2 | 驗證系譜記錄為不可變，更安全地存儲，並可供審計存取。                                  |  2  | D/V |
| 1.5.3 | 確認血統追蹤涵蓋通過隱私保護或生成技術產生的合成數據，並且所有合成數據在整個流程中均被清晰標記且可與真實數據區別開來。 |  2  | D/V |

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

