# C3 模型生命周期管理與變更控制

## 控制目標

人工智慧系統必須實施變更控制流程，以防止未經授權或不安全的模型修改進入生產環境。此控制確保模型在整個生命週期中保持完整性——從開發、部署到退役——從而實現快速事件回應並維護所有變更的問責制。

核心安全目標：僅授權且經驗證的模型通過受控流程進入生產，該流程維持完整性、可追溯性及可恢復性。

---

## C3.1 模型授權與完整性

只有經過驗證完整性的授權模型才能進入生產環境。

|   #   | 描述                                                        | 等級  | 角色  |
| :---: | --------------------------------------------------------- | :-: | :-: |
| 3.1.1 | 在部署前，請確認所有模型產物（權重、配置、分詞器）皆由授權實體進行加密簽章。                    |  1  | D/V |
| 3.1.2 | 驗證模型完整性是否在部署時經過確認，且簽名驗證失敗將阻止模型載入。                         |  1  | D/V |
| 3.1.3 | 驗證模型來源記錄是否包含授權實體的身份、訓練數據檢查碼、帶有通過/失敗狀態的驗證測試結果，以及創建時間戳。     |  2  | D/V |
| 3.1.4 | 驗證所有模型產物均使用語義版本控制（MAJOR.MINOR.PATCH），並附有說明各版本組件升級時機的文檔標準。 |  2  | D/V |
| 3.1.5 | 驗證依賴追蹤是否維持即時庫存，以便快速識別所有使用系統。                              |  2  |  V  |

---

## C3.2 模型驗證與測試

模型在部署前必須通過已定義的安全性和安全驗證。

|   #   | 描述                                                      | 等級  | 角色  |
| :---: | ------------------------------------------------------- | :-: | :-: |
| 3.2.1 | 確認模型在部署前經過自動化安全測試，包含輸入驗證、輸出淨化，以及依據預先同意的組織通過/失敗標準進行安全評估。 |  1  | D/V |
| 3.2.2 | 確認驗證失敗在經過預先指定的授權人員明確的覆核批准且有書面商業理由後，能自動阻止模型部署。           |  1  | D/V |
| 3.2.3 | 驗證測試結果是否經過密碼學簽名並不可變地連結到正在驗證的特定模型版本哈希值。                  |  2  |  V  |
| 3.2.4 | 確認緊急部署需在預先同意的時間範圍內，進行有文件記錄的安全風險評估，並獲得預先指定的安全權限批准。       |  2  | D/V |

---

## C3.3 控制部署與回滾

模型部署必須受到控制、監控，且可逆轉。

|   #   | 描述                                                                  | 等級  | 角色  |
| :---: | ------------------------------------------------------------------- | :-: | :-: |
| 3.3.1 | 確認生產環境部署實施了漸進式推出機制（金絲雀部署、藍綠部署），並且基於預先約定的錯誤率、延遲閾值或安全警報標準設置了自動回滾觸發條件。 |  1  |  D  |
| 3.3.2 | 驗證回滾功能是否能在預定的組織時間窗口內，原子性地還原完整的模型狀態（權重、配置、依賴關係）。                     |  1  | D/V |
| 3.3.3 | 驗證部署流程在模型啟動前是否驗證密碼簽名並計算完整性校驗和，若有任何不符則使部署失敗。                         |  2  | D/V |
| 3.3.4 | 驗證緊急模型關閉功能能夠通過自動斷路器或手動終止開關，在預定的響應時間內禁用模型端點。                         |  2  | D/V |
| 3.3.5 | 驗證回滾工件（先前的模型版本、設定、依賴）是否依據組織政策保留，並使用不可變儲存以支援事件回應。                    |  2  |  V  |

---

## C3.4 變更問責制與審計

所有模型生命週期的變更必須可追蹤且可審計。

|   #   | 描述                                                                 | 等級  | 角色  |
| :---: | ------------------------------------------------------------------ | :-: | :-: |
| 3.4.1 | 驗證所有模型變更（部署、配置、退役）皆會產生不可變更的稽核紀錄，包含時間戳記、經身份驗證的執行者身分、變更類型，以及變更前後的狀態。 |  1  |  V  |
| 3.4.2 | 驗證審計日誌存取是否需要適當的授權，並且所有存取嘗試都記錄有使用者身份和時間戳記。                          |  2  | D/V |
| 3.4.3 | 確認提示模板和系統訊息在 git 儲存庫中受到版本控制，並且在部署前必須經過指定審查員的代碼審查及批准。               |  2  | D/V |
| 3.4.4 | 驗證審核記錄是否包含足夠的細節（模型雜湊值、配置快照、依賴版本），以便在保留期限內針對任何時間點完整重建模型狀態。          |  2  |  V  |

---

## C3.5 安全開發實務

模型開發和訓練過程必須遵循安全實踐以防止被侵害。

|   #   | 描述                                                      | 等級  | 角色  |
| :---: | ------------------------------------------------------- | :-: | :-: |
| 3.5.1 | 確認模型開發、測試和生產環境在物理上或邏輯上彼此分離。它們不共享基礎設施，具有獨立的存取控制及隔離的數據存儲。 |  1  |  D  |
| 3.5.2 | 確認模型訓練和微調在具有限制網路存取的獨立環境中進行。                             |  1  |  D  |
| 3.5.3 | 確認訓練數據來源在模型開發前，經過完整性檢查驗證並透過具有文件化監管鏈的可信來源進行身份認證。         |  1  | D/V |
| 3.5.4 | 確認模型開發產物（超參數、訓練腳本、配置文件）已存放於版本控制中，且在用於訓練前需經同儕審核批准。       |  2  |  D  |

---

## C3.6 模型退役與停用

當模型不再需要或發現安全問題時，必須安全地退役。

|   #   | 描述                                                     | 等級  | 角色  |
| :---: | ------------------------------------------------------ | :-: | :-: |
| 3.6.1 | 驗證模型退役流程是否自動掃描依賴圖，識別所有使用系統，並在退役前提供事先約定的提前通知期限。         |  1  |  D  |
| 3.6.2 | 依據已記錄的資料保留政策，確認已退休的模型工件透過密碼學抹除或多遍覆寫方式安全刪除，並取得經驗證的銷毀證明。 |  1  | D/V |
| 3.6.3 | 確認模型退役事件已記錄時間戳和執行者身份，並撤銷模型簽名以防止重複使用。                   |  2  |  V  |
| 3.6.4 | 驗證緊急模型退役能否在預先設定的緊急應變時間內，透過自動終止開關停用模型存取權限，若發現關鍵安全漏洞。    |  2  | D/V |

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

