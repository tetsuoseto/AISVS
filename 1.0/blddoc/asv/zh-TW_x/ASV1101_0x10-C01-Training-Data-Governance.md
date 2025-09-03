# C1 訓練數據治理與偏見管理

## 控制目標

訓練資料必須以保持來源可追溯性、安全性、品質與公平性的方式取得、處理與維護。 如此作法可履行法定義務，並降低在訓練期間出現的偏見、資料污染或隱私洩露的風險，這些風險可能影響整個 AI 生命週期。

---

## C1.1 訓練資料溯源

維護所有資料集的可驗證清單，僅接受可信來源，並記錄每次變更以便審計。

|   #   | 描述                                                            | 等級  | 角色  |
| :---: | ------------------------------------------------------------- | :-: | :-: |
| 1.1.1 | 確保每一個訓練資料來源的最新清單被維護，其內容包括：來源、管理者/所有者、授權、收集方法、預期用途限制，以及處理紀錄。   |  1  | D/V |
| 1.1.2 | 驗證訓練資料處理過程是否排除不必要的特徵、屬性或欄位（例如未使用的元資料、敏感 PII（個人識別資訊）、洩露的測試資料）。 |  1  | D/V |
| 1.1.3 | 確認所有資料集變更均需遵循有日誌記錄的審批工作流程。                                    |  2  | D/V |
| 1.1.4 | 在可行的情況下，驗證資料集或子集是否已加上水印或指紋。                                   |  3  | D/V |

---

## C1.2 訓練資料安全與完整性

限制對訓練資料的存取，於靜態存儲時與傳輸中對其進行加密，並驗證其完整性以防止篡改、竊取或資料污染。

|   #   | 描述                                             | 等級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 1.2.1 | 驗證存取控制是否能保護訓練資料的儲存與資料管道。                       |  1  | D/V |
| 1.2.2 | 驗證對訓練資料的所有存取是否已被記錄，包括使用者、時間與動作。                |  2  | D/V |
| 1.2.3 | 驗證訓練資料集在傳輸中與靜態存放時均已加密，並採用業界標準的密碼學演算法與金鑰管理實務。   |  2  | D/V |
| 1.2.4 | 驗證在訓練資料的儲存與傳輸過程中，是否使用密碼學雜湊值或數位簽名以確保資料完整性。      |  2  | D/V |
| 1.2.5 | 請確認是否已採用自動化偵測技術，以防止訓練資料遭未經授權修改或損壞。             |  2  | D/V |
| 1.2.6 | 驗證過時的訓練資料是否已被安全地清除或匿名化。                        |  2  | D/V |
| 1.2.7 | 驗證所有訓練資料集版本均具唯一識別性，且以不可變的方式儲存，並可審計，以支援回滾與取證分析。 |  3  | D/V |

---

## C1.3 訓練資料標註的品質、完整性與安全性

保護標籤，並對關鍵數據進行技術審查。

|   #   | 描述                                                  | 等級  | 角色  |
| :---: | --------------------------------------------------- | :-: | :-: |
| 1.3.1 | 驗證是否已對標籤工件應用密碼雜湊值或數位簽章，以確保其完整性與真實性。                 |  2  | D/V |
| 1.3.2 | 驗證標註介面與平台是否實施嚴格的存取控制、維護對所有標註活動的可防篡改審計日誌，並防範未經授權的修改。 |  2  | D/V |
| 1.3.3 | 驗證標籤中的敏感資訊是否在資料欄位層級於靜態存放時與在傳輸過程中被遮蔽、去識別化或加密。        |  3  | D/V |

---

## C1.4 訓練資料品質與安全性保證

結合自動化驗證、手動抽查，以及有紀錄的補救措施，以確保資料集的可靠性。

|   #   | 描述                                                                                                                  | 等級  | 角色  |
| :---: | ------------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 1.4.1 | 驗證自動化測試是否能在每次資料攝取或重大資料轉換時捕捉格式錯誤與空值。                                                                                 |  1  |  D  |
| 1.4.2 | 驗證大型語言模型（LLM）訓練與微調管道是否實施中毒偵測與資料完整性驗證（例如，統計方法、離群值偵測、嵌入分析），以識別潛在的中毒攻擊（例如，標籤翻轉、後門觸發插入、角色切換指令、具影響力的實例攻擊）或訓練數據中的非故意資料損壞。 |  2  | D/V |
| 1.4.3 | 根據風險評估，驗證是否已在相關模型上實施並調整適當的防禦措施，例如對抗性訓練（使用生成的對抗性樣本）、對被擾動輸入進行資料增強，或穩健優化技術。                                            |  3  | D/V |
| 1.4.4 | 驗證自動生成的標籤（例如透過大型語言模型（LLMs）或弱監督）是否受信心閾值與一致性檢查的約束，以檢測幻覺、誤導性或低信心的標籤。                                                   |  2  | D/V |
| 1.4.5 | 驗證自動化測試在每次資料攝取或重大資料轉換時能捕捉到標籤偏斜。                                                                                     |  3  |  D  |

---

## C1.5 資料血統與可追溯性

追蹤每個資料點從來源到模型輸入的完整流程，以利審計與事件回應。

|   #   | 描述                                                                | 等級  | 角色  |
| :---: | ----------------------------------------------------------------- | :-: | :-: |
| 1.5.1 | 驗證每個資料點的資料血統，包括所有轉換、增強與合併，是否已被記錄，並且可以重建。                          |  2  | D/V |
| 1.5.2 | 驗證資料血統紀錄是否不可變、是否安全儲存，並可供審計存取。                                     |  2  | D/V |
| 1.5.3 | 驗證資料血統追蹤是否涵蓋由隱私保護或生成式技術產生的合成資料，並確保在整個資料流程中，所有合成資料均清楚標示，且能與真實資料區分。 |  2  | D/V |

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

