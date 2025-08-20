# C3 模型生命週期管理與變更控制

## 控制目標

人工智慧系統必須實施變更控制流程，以防止未經授權或不安全的模型修改進入生產環境。此控制確保模型在整個生命週期中——從開發、部署到退役——的完整性，從而實現快速事件回應並維持對所有變更的問責。

核心安全目標：僅允許經授權且驗證過的模型通過受控流程進入生產環境，該流程維持完整性、可追蹤性與可恢復性。

---

## C3.1 模型授權與完整性

只有通過驗證完整性的授權模型才能進入生產環境。

|   #   | 描述                                                           | 層級  | 角色  |
| :---: | ------------------------------------------------------------ | :-: | :-: |
| 3.1.1 | 在部署之前，請驗證所有模型工件（權重、配置、分詞器）均由授權實體進行了加密簽名。                     |  1  | D/V |
| 3.1.2 | 確認模型完整性在部署時被驗證，且簽名驗證失敗會阻止模型加載。                               |  1  | D/V |
| 3.1.3 | 驗證模型來源紀錄是否包含授權實體的身份、訓練數據的校驗和、驗證測試結果及通過/未通過狀態，以及建立時間戳記。       |  2  | D/V |
| 3.1.4 | 確認所有模型產物皆使用語義版本控制（MAJOR.MINOR.PATCH），並具備明確記錄的標準說明每個版本組件何時遞增。 |  2  | D/V |
| 3.1.5 | 驗證相依性追蹤能維持即時庫存，從而能快速識別所有消費系統。                                |  2  |  V  |

---

## C3.2 模型驗證與測試

模型必須在部署前通過已定義的安全與防護驗證。

|   #   | 描述                                                       | 層級  | 角色  |
| :---: | -------------------------------------------------------- | :-: | :-: |
| 3.2.1 | 確認模型在部署前進行自動化安全測試，包括輸入驗證、輸出淨化以及根據事先約定的組織通過/未通過標準進行安全性評估。 |  1  | D/V |
| 3.2.2 | 驗證在經過預先指定授權人員的明確覆核批准並附具書面業務理由後，驗證失敗是否會自動阻止模型部署。          |  1  | D/V |
| 3.2.3 | 驗證測試結果是否經過密碼學簽名，並不可變地鏈接到被驗證的特定模型版本哈希。                    |  2  |  V  |
| 3.2.4 | 確認緊急部署需要有文件化的安全風險評估，並且在預先約定的時限內獲得預先指定的安全主管的批准。           |  2  | D/V |

---

## C3.3 控制部署與回滾

模型部署必須受到控制、監控，並且能夠逆轉。

|   #   | 描述                                                               | 層級  | 角色  |
| :---: | ---------------------------------------------------------------- | :-: | :-: |
| 3.3.1 | 確認生產部署實施了漸進式發布機制（金絲雀部署、藍綠部署），並根據事先約定的錯誤率、延遲閾值或安全警報標準設置了自動回滾觸發條件。 |  1  |  D  |
| 3.3.2 | 驗證回滾功能能在預定的組織時間窗口內，原子性地恢復完整的模型狀態（權重、配置、依賴關係）。                    |  1  | D/V |
| 3.3.3 | 驗證部署流程在模型啟動前會檢查密碼簽章並計算完整性校驗和，若有任何不匹配則部署失敗。                       |  2  | D/V |
| 3.3.4 | 驗證緊急模型關閉功能能夠透過自動斷路器或手動終止開關，在預定的響應時間內停用模型端點。                      |  2  | D/V |
| 3.3.5 | 驗證回滾工件（先前的模型版本、配置、依賴項）是否根據組織政策保留，並使用不可變存儲以應對事件響應。                |  2  |  V  |

---

## C3.4 變更問責制與稽核

所有模型生命周期的變更必須可追蹤且可審計。

|   #   | 描述                                                             | 層級  | 角色  |
| :---: | -------------------------------------------------------------- | :-: | :-: |
| 3.4.1 | 驗證所有模型變更（部署、配置、退役）皆產生包含時間戳記、經過身份驗證的執行者身份、變更類型以及變更前後狀態的不可變審計記錄。 |  1  |  V  |
| 3.4.2 | 驗證審計日誌的存取是否需要適當授權，並且所有存取嘗試都記錄有使用者身份和時間戳記。                      |  2  | D/V |
| 3.4.3 | 確認提示模板和系統訊息在 git 儲存庫中進行版本控制，並且在部署前必須經過指定審查者的強制程式碼審查和批准。        |  2  | D/V |
| 3.4.4 | 確認審計記錄包含足夠的詳細資料（模型哈希、配置快照、依賴版本），以便在保存期限內的任何時間點能夠完整重建模型狀態。      |  2  |  V  |

---

## C3.5 安全開發實踐

模型開發和訓練過程必須遵循安全實踐以防止被入侵。

|   #   | 描述                                                       | 層級  | 角色  |
| :---: | -------------------------------------------------------- | :-: | :-: |
| 3.5.1 | 確認模型開發、測試及生產環境在實體或邏輯上分離。它們沒有共用基礎設施，具有獨立的存取控制，並且資料存放互相隔離。 |  1  |  D  |
| 3.5.2 | 確認模型訓練和微調在具備受控網路存取的隔離環境中進行。                              |  1  |  D  |
| 3.5.3 | 確保訓練數據來源在用於模型開發前，通過完整性檢查進行驗證，並經由具有文件化監管鏈的可信來源進行身份認證。     |  1  | D/V |
| 3.5.4 | 確認模型開發相關成果（超參數、訓練腳本、配置文件）已儲存在版本控制系統中，且在用於訓練前需經同儕審核批准。    |  2  |  D  |

---

## C3.6 模型退役與停用

當模型不再需要或發現安全問題時，必須安全地將其退役。

|   #   | 描述                                                    | 層級  | 角色  |
| :---: | ----------------------------------------------------- | :-: | :-: |
| 3.6.1 | 驗證模型退役流程是否自動掃描依賴圖，識別所有使用系統，並在退役前提供事先約定的提前通知期限。        |  1  |  D  |
| 3.6.2 | 根據已記錄的資料保留政策並附有經驗證的銷毀證明，驗證已退役模型工件是否使用密碼擦除或多重覆寫方式安全清除。 |  1  | D/V |
| 3.6.3 | 驗證模型退役事件是否有帶有時間戳記和行為者身份的日誌紀錄，並撤銷模型簽名以防止重複使用。          |  2  |  V  |
| 3.6.4 | 驗證緊急模型退役是否能在預先設定的緊急響應時間內，透過自動中止開關禁用模型存取，以防發現關鍵安全漏洞。   |  2  | D/V |

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

