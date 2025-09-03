# C3 模型生命週期管理與變更控管

## 控制目標

AI 系統必須實施變更控管流程，以防止未經授權或不安全的模型修改進入生產環境。這項控管在整個生命週期--從開發到部署再到退役--確保模型完整性，從而能迅速回應事件並對所有變更保持可追溯性。

核心安全目標：只有經過授權與驗證的模型才能佈署至生產環境，透過受控流程維護完整性、可追溯性與可恢復性。

---

## C3.1 模型授權與完整性

只有經過授權且經過完整性驗證的模型才能進入生產環境。

|   #   | 描述                                                            | 等級  | 角色  |
| :---: | ------------------------------------------------------------- | :-: | :-: |
| 3.1.1 | 在部署之前，驗證所有模型工件（權重、配置、分詞器）是否已由授權實體以密碼學簽名。                      |  1  | D/V |
| 3.1.2 | 確保在部署時驗證模型完整性，簽名驗證失敗將阻止模型載入。                                  |  1  | D/V |
| 3.1.3 | 驗證模型溯源記錄是否包含授權實體的身份、訓練數據的雜湊值、帶有通過/失敗狀態的驗證測試結果，以及建立時間戳。        |  2  | D/V |
| 3.1.4 | 驗證所有模型工件是否使用語義化版本控制（MAJOR.MINOR.PATCH），並具備文件化的標準，說明何時遞增各版本分量。 |  2  | D/V |
| 3.1.5 | 驗證依賴關係追蹤是否能維持實時庫存，並能快速識別所有正在消耗資源的系統。                          |  2  |  V  |

---

## C3.2 模型驗證與測試

模型必須在部署前通過已定義的安全與風險驗證。

|   #   | 描述                                                                  | 等級  | 角色  |
| :---: | ------------------------------------------------------------------- | :-: | :-: |
| 3.2.1 | 在部署之前，確保模型經過自動化的安全性測試，該測試包含輸入驗證、輸出淨化，以及具事前約定之組織通過/不通過閾值的安全性評估。      |  1  | D/V |
| 3.2.2 | 確認在取得事先指定的授權人員之明確覆蓋批准並附有書面商業理由後，驗證失敗會自動阻止模型部署。                      |  1  | D/V |
| 3.2.3 | 驗證測試結果是否已以密碼學簽名，且與正在驗證之特定模型版本哈希值不可變地相連。                             |  2  |  V  |
| 3.2.4 | 驗證緊急部署是否需要有文件化的安全風險評估，並在 pre-designated 安全主管的 pre-agreed 時間範圍內取得批准。 |  2  | D/V |

---

## C3.3 受控 部署 & 回滾

模型部署必須受到控管、監控，且可逆。

|   #   | 描述                                                                 | 等級  | 角色  |
| :---: | ------------------------------------------------------------------ | :-: | :-: |
| 3.3.1 | 驗證生產部署是否實施漸進式發布機制（金絲雀部署、藍綠部署），並具備自動回滾觸發機制，根據事先商定的錯誤率、延遲閾值，或安全警報條件。 |  1  |  D  |
| 3.3.2 | 驗證回滾能力是否能在事先定義的組織時間窗內，以原子性方式恢復完整的模型狀態（權重、配置、依賴）。                   |  1  | D/V |
| 3.3.3 | 驗證部署流程在模型啟用前，是否會驗證數位簽章並計算完整性校驗和；若有任何不匹配，部署將失敗。                     |  2  | D/V |
| 3.3.4 | 驗證緊急模型關閉能力是否能在預先設定的回應時間內，透過自動斷路器或手動終止開關停用模型端點。                     |  2  | D/V |
| 3.3.5 | 驗證回滾工件（先前的模型版本、配置、依賴項）依據組織政策保留，並採用不可變儲存以便事件回應。                     |  2  |  V  |

---

## C3.4 變更問責與審計

所有模型生命週期變更必須可追溯且可審計。

|   #   | 描述                                                           | 等級  | 角色  |
| :---: | ------------------------------------------------------------ | :-: | :-: |
| 3.4.1 | 確保所有模型變更（部署、配置、退役）產生不可變的審計紀錄，包含時間戳記、經過驗證的執行者身份、變更類型，以及前/後狀態。 |  1  |  V  |
| 3.4.2 | 驗證對審計日誌的存取需要適當的授權，且所有存取嘗試都會記錄使用者身份與時間戳記。                     |  2  | D/V |
| 3.4.3 | 請確認提示模板與系統訊息在 Git 倉庫中已進行版本控制，且在部署之前必須經由指定審核人員進行程式碼審查與批准。     |  2  | D/V |
| 3.4.4 | 驗證審計記錄是否包含足夠的細節 （模型哈希值、配置快照、依賴版本） 以便在保留期內的任意時間戳重建模型狀態。       |  2  |  V  |

---

## C3.5 安全開發實踐

模型開發與訓練過程必須遵循安全實踐，以防止遭到妥協。

|   #   | 描述                                                           | 等級  | 角色  |
| :---: | ------------------------------------------------------------ | :-: | :-: |
| 3.5.1 | 請確認模型開發、測試與生產環境在物理上或邏輯上分離。它們沒有共用的基礎設施、具備不同的存取控制，並且資料儲存庫彼此隔離。 |  1  |  D  |
| 3.5.2 | 驗證模型訓練與微調是否在隔離的環境中進行，且網路存取受控。                                |  1  |  D  |
| 3.5.3 | 在用於模型開發之前，驗證訓練資料來源，透過完整性檢查進行驗證，並以可信來源進行認證，且具備文檔化的保管鏈。        |  1  | D/V |
| 3.5.4 | 驗證模型開發工件（超參數、訓練腳本、設定檔）是否已存放於版本控制中，並在訓練前需經同儕審核批准。             |  2  |  D  |

---

## C3.6 模型退役與下線

模型在不再需要或識別出安全問題時，必須被安全地退役。

|   #   | 描述                                                         | 等級  | 角色  |
| :---: | ---------------------------------------------------------- | :-: | :-: |
| 3.6.1 | 驗證模型退役流程是否能自動掃描依賴關係圖、識別所有使用該模型的系統，並在退役之前提供事先商定的提前通知期限。     |  1  |  D  |
| 3.6.2 | 驗證已退役的模型產物是否已安全清除，採用密碼學擦除或多次覆寫，依據已文檔化的資料保留政策，並附有經過驗證的銷毀證明。 |  1  | D/V |
| 3.6.3 | 驗證模型退役事件是否已被記錄，且記錄包含時間戳與執行者身分，同時撤銷模型簽名以防止再次使用。             |  2  |  V  |
| 3.6.4 | 驗證在發現關鍵安全漏洞時，是否能透過自動化終止開關，在事前設定的緊急響應時間框架內實現緊急模型退役並禁用模型存取。  |  2  | D/V |

---

## 參考文獻

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

