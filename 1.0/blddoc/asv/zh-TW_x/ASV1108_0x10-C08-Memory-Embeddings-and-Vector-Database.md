# C8 記憶體、嵌入向量與向量資料庫安全性

## 控制目標

嵌入向量與向量資料庫充當當代 AI 系統的「實時記憶」，不斷接受使用者提供的資料，並透過檢索增強生成（Retrieval-Augmented Generation，RAG）將其重新引入模型上下文。若不加以治理，這段記憶可能洩漏個人識別資訊（PII）、侵犯同意，或被逆向還原以重建原始文本。本控制系列的目標是加固記憶管道與向量資料庫，使存取具備最小特權、嵌入向量具備隱私保護特性、儲存的向量到期或可按需撤銷，且每位使用者的記憶絕不會污染其他使用者的提示或完成內容。

---

## C8.1 記憶體與 RAG 索引的存取控制

在每個向量集合上實施細粒度存取控制。

|   #   | 描述                                                                                                      | 等級  | 角色  |
| :---: | ------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 8.1.1 | 驗證行級與命名空間級存取控制規則是否對每個租戶、集合或文件標籤限制插入、刪除與查詢操作。                                                            |  1  | D/V |
| 8.1.2 | 驗證 API 金鑰或 JWT 是否包含有作用域的聲明（例如集合 ID、動作動詞），且至少每季輪換一次。                                                     |  1  | D/V |
| 8.1.3 | 驗證特權提升嘗試（例如跨命名空間的相似性查詢）是否在 5 分鐘內被偵測並記錄至 SIEM。                                                           |  2  | D/V |
| 8.1.4 | 驗證向量資料庫的審計日誌是否記錄 subject-identifier、operation、vector ID/namespace、similarity threshold，以及 result count。 |  2  | D/V |
| 8.1.5 | 在引擎升級或索引分片規則變更時，請驗證存取決策是否已針對繞過漏洞進行測試。                                                                   |  3  |  V  |

---

## C8.2 嵌入向量的淨化與驗證

事前篩選文本以識別個人身份資訊（PII），在向量化之前將其遮蔽或偽名化，並可選地對嵌入進行後處理以去除殘留信號。

|   #   | 描述                                                       | 等級  | 角色  |
| :---: | -------------------------------------------------------- | :-: | :-: |
| 8.2.1 | 驗證 PII 和受管制資料是否透過自動化分類器被檢測，並在嵌入前進行遮罩、令牌化或丟棄。             |  1  | D/V |
| 8.2.2 | 驗證嵌入管線是否會拒絕或將包含可執行程式碼或非 UTF-8 產物的輸入隔離，以防止污染索引。           |  1  |  D  |
| 8.2.3 | 驗證是否對與任何已知 PII 令牌的距離低於可配置閾值的句子嵌入，套用局部差分隱私或度量差分隱私的去識別化處理。 |  2  | D/V |
| 8.2.4 | 確保資料脫敏效能（例如，PII 脫敏的召回率、語義漂移）至少每半年在基準語料庫上進行驗證。            |  2  |  V  |
| 8.2.5 | 確保資料淨化設定受版本控管，且變更需經同儕審查。                                 |  3  | D/V |

---

## C8.3 記憶過期、撤銷與刪除

GDPR 的「被遺忘權」以及類似法規要求及時刪除；因此向量存儲必須支援 TTL、硬刪除和墓碑化，以確保已撤銷的向量無法被恢復或重新索引。

|   #   | 描述                                                       | 等級  | 角色  |
| :---: | -------------------------------------------------------- | :-: | :-: |
| 8.3.1 | 驗證每個向量及其元資料記錄是否具備 TTL（存活時間）或明確的保留標籤，並由自動清理作業遵循。          |  1  | D/V |
| 8.3.2 | 驗證使用者發起的刪除請求是否在 30 天內清除向量、元資料、快取副本與衍生索引。                 |  1  | D/V |
| 8.3.3 | 驗證在硬體支援時，邏輯刪除是否會跟著對儲存區塊進行密碼學銷毀；若硬體不支援，則以金鑰保管庫中的金鑰銷毀作為替代。 |  2  |  D  |
| 8.3.4 | 驗證過期向量是否在過期後的 < 500 毫秒內被排除在最近鄰搜尋結果之外。                    |  3  | D/V |

---

## C8.4 防止嵌入反演與洩漏

最近的防禦措施—雜訊疊加、投影網路、隱私神經元擾動，以及應用層加密—可以將詞元級反演率降至低於 5%。

|   #   | 描述                                                             | 等級  | 角色  |
| :---: | -------------------------------------------------------------- | :-: | :-: |
| 8.4.1 | 請確認是否存在一個正式的威脅模型，涵蓋反演攻擊、成員推論攻擊與屬性推論攻擊，且每年進行審查。                 |  1  |  V  |
| 8.4.2 | 驗證應用層加密或可搜尋加密是否能使向量免於被基礎設施管理員或雲端工作人員直接讀取。                      |  2  | D/V |
| 8.4.3 | 防禦參數 (ε for DP、噪聲 σ、投影秩 k) 平衡 隱私 ≥ 99 % 令牌保護 與 效用 ≤ 3 % 準確度損失。 |  3  |  V  |
| 8.4.4 | 確認逆向韌性指標是否納入模型更新的發布門檻，並定義回歸預算。                                 |  3  | D/V |

---

## C8.5 使用者特定記憶體的範圍強制執行

跨租戶洩漏仍是最嚴重的 RAG 風險：未經適當過濾的相似性查詢可能洩露另一位客戶的私人文檔。

|   #   | 描述                                             | 等級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 8.5.1 | 確保每個檢索查詢在被傳遞給 LLM 提示之前，已經以租戶/用戶 ID 進行後置過濾。     |  1  | D/V |
| 8.5.2 | 驗證集合名稱或命名空間 ID 是否對每位使用者或租戶分別加鹽，以防止跨作用域的向量發生碰撞。 |  1  |  D  |
| 8.5.3 | 驗證高於可配置的距離閾值但超出呼叫者範圍的相似度結果將被丟棄，並觸發安全警報。        |  2  | D/V |
| 8.5.4 | 驗證多租戶壓力測試是否能模擬對抗性查詢，試圖檢索超出範圍的文件，並證明零洩漏。        |  2  |  V  |
| 8.5.5 | 驗證每個租戶的加密金鑰是否已分離，以確保即使物理儲存被共享，也能實現密碼學隔離。       |  3  | D/V |

---

## C8.6 先進的記憶體系統安全

針對包含情節記憶、語意記憶與工作記憶的先進記憶體架構之安全控制，具備特定的隔離與驗證需求。

|   #   | 描述                                                                         | 等級  | 角色  |
| :---: | -------------------------------------------------------------------------- | :-: | :-: |
| 8.6.1 | 驗證不同的記憶類型（情節記憶、語意記憶、工作記憶）具備彼此隔離的安全上下文、基於角色的存取控制、分離的加密密鑰，以及對每種記憶類型的文件化存取模式。 |  1  | D/V |
| 8.6.2 | 驗證記憶整合過程是否包含安全性驗證，以在儲存之前透過內容淨化、來源驗證與完整性檢查，防止注入惡意記憶。                        |  2  | D/V |
| 8.6.3 | 驗證並淨化記憶檢索查詢，以防止藉由查詢模式分析、強制執行存取控制，以及結果過濾而提取未經授權的資訊。                         |  2  | D/V |
| 8.6.4 | 驗證記憶體擦除機制是否能在具備密碼學擦除保證的前提下，透過金鑰刪除、多次覆寫，或以硬體為基礎且提供驗證證書的安全刪除方式，安全地刪除敏感資訊。    |  3  | D/V |
| 8.6.5 | 驗證記憶體系統的完整性是否持續被監控，以偵測未經授權的修改或損壞，透過校驗和、審計日誌，以及在記憶體內容超出正常運作範圍時自動發出警報。       |  3  | D/V |

---

## 參考文獻

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

