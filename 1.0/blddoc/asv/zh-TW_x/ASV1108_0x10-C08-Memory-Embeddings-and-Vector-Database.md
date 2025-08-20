# C8 記憶體、嵌入式向量與向量資料庫安全性

## 控制目標

嵌入和向量存儲作為當代 AI 系統的「即時記憶」，持續接收用戶提供的數據，並通過檢索增強生成（Retrieval-Augmented Generation，RAG）將其重新呈現到模型上下文中。如果沒有適當的治理，這種記憶可能會洩露個人識別信息（PII）、違反同意條款，或被反轉以重建原始文本。該控制集的目標是加固記憶管道和向量資料庫，確保訪問權限遵循最小權限原則，嵌入具備隱私保護功能，存儲的向量可設置過期或按需撤銷，並且每位用戶的記憶不會污染其他用戶的提示或生成結果。

---

## C8.1 記憶體與 RAG 指標的存取控制

對每個向量集合實施細粒度的存取控制。

|   #   | 描述                                                      | 層級  | 角色  |
| :---: | ------------------------------------------------------- | :-: | :-: |
| 8.1.1 | 驗證列/命名空間層級的存取控制規則是否限制每個租戶、集合或文件標籤的插入、刪除和查詢操作。           |  1  | D/V |
| 8.1.2 | 驗證 API 金鑰或 JWT 是否攜帶範圍限定的聲明（例如，集合 ID、操作動詞），並且至少每季進行一次輪替。 |  1  | D/V |
| 8.1.3 | 驗證權限提升嘗試（例如，跨命名空間的相似性查詢）是否能在 5 分鐘內被檢測並記錄到 SIEM。         |  2  | D/V |
| 8.1.4 | 驗證向量資料庫是否審核日誌中的主體識別碼、操作、向量 ID/命名空間、相似度閾值以及結果數量。         |  2  | D/V |
| 8.1.5 | 確保在更新引擎或更改索引分片規則時，訪問決策會被測試是否存在繞過漏洞。                     |  3  |  V  |

---

## C8.2 嵌入清理與驗證

在向量化之前，預先篩選文字中的個人識別資訊（PII），進行遮蔽或假名化，並可選擇在後處理嵌入時去除殘留訊號。

|   #   | 描述                                                       | 層級  | 角色  |
| :---: | -------------------------------------------------------- | :-: | :-: |
| 8.2.1 | 驗證個人識別資訊（PII）和受管制資料是否透過自動分類器被偵測，並在嵌入前進行遮蔽、標記化或刪除。        |  1  | D/V |
| 8.2.2 | 驗證嵌入管道是否拒絕或隔離包含可執行程式碼或非 UTF-8 文本異常的輸入，避免污染索引。            |  1  |  D  |
| 8.2.3 | 驗證對於與任何已知個人識別資訊（PII）標記距離低於可配置閾值的句子嵌入，是否應用了本地或度量差分隱私消毒處理。 |  2  | D/V |
| 8.2.4 | 驗證清理效果（例如，個人識別信息去除的召回率、語義漂移）至少每半年針對基準語料庫進行一次驗證。          |  2  |  V  |
| 8.2.5 | 確認清理配置受到版本控制，且變更需經過同儕審查。                                 |  3  | D/V |

---

## C8.3 記憶體到期、撤銷與刪除

GDPR「被遺忘權」及類似法律要求及時刪除；因此，向量庫必須支援 TTL、硬刪除和墓碑標記，以確保被撤銷的向量無法被恢復或重新索引。

|   #   | 描述                                              | 層級  | 角色  |
| :---: | ----------------------------------------------- | :-: | :-: |
| 8.3.1 | 驗證每個向量和元資料記錄是否帶有 TTL 或由自動清理作業遵守的明確保留標籤。         |  1  | D/V |
| 8.3.2 | 驗證使用者發起的刪除請求是否在 30 天內清除向量、元資料、快取副本和衍生索引。        |  1  | D/V |
| 8.3.3 | 驗證邏輯刪除是否緊接著進行存儲區塊的加密銷毀（如果硬體支持），或通過金鑰保管庫的金鑰銷毀方式。 |  2  |  D  |
| 8.3.4 | 驗證已過期的向量在過期後小於 500 毫秒內被排除在最近鄰搜尋結果之外。            |  3  | D/V |

---

## C8.4 防止嵌入反演與洩漏

近期的防禦技術——噪聲疊加、投影網絡、隱私神經元擾動以及應用層加密——能將令牌層級的反演率降低至5%以下。

|   #   | 描述                                                              | 層級  | 角色  |
| :---: | --------------------------------------------------------------- | :-: | :-: |
| 8.4.1 | 確認存在涵蓋反演攻擊、成員資格攻擊及屬性推斷攻擊的正式威脅模型，並且該模型每年進行審查。                    |  1  |  V  |
| 8.4.2 | 確認應用層加密或可搜尋加密可防止基礎設施管理員或雲端人員直接讀取向量。                             |  2  | D/V |
| 8.4.3 | 驗證防護參數（DP 的 ε、噪聲 σ、投影秩 k）是否在隱私保護 ≥ 99% 令牌保護和效用 ≤ 3% 精度損失之間取得平衡。 |  3  |  V  |
| 8.4.4 | 確認反轉韌性指標是模型更新的發布門檻之一，並且已定義回歸預算。                                 |  3  | D/V |

---

## C8.5 用戶特定記憶體的範圍強制執行

跨租戶洩漏仍然是 RAG 的主要風險：過濾不當的相似度查詢可能會暴露其他客戶的私人文件。

|   #   | 描述                                             | 層級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 8.5.1 | 確認每個檢索查詢在傳遞給大型語言模型提示之前均經由租戶/使用者ID進行後置過濾。       |  1  | D/V |
| 8.5.2 | 驗證集合名稱或命名空間 ID 是否根據使用者或租戶進行加鹽，以避免向量在不同範圍間發生碰撞。 |  1  |  D  |
| 8.5.3 | 驗證相似度結果在可配置的距離閾值以上但超出呼叫者範圍時被丟棄並觸發安全警報。         |  2  | D/V |
| 8.5.4 | 驗證多租戶壓力測試能夠模擬嘗試檢索超出範圍文件的對抗性查詢，並展示零洩漏。          |  2  |  V  |
| 8.5.5 | 確認加密金鑰依據租戶進行隔離，確保即使物理儲存共用，也能實現密碼學上的隔離。         |  3  | D/V |

---

## C8.6 先進記憶系統安全性

針對包含情節記憶、語意記憶與工作記憶的複雜記憶架構所設計的安全控制，具備特定的隔離及驗證要求。

|   #   | 描述                                                                       | 層級  | 角色  |
| :---: | ------------------------------------------------------------------------ | :-: | :-: |
| 8.6.1 | 驗證不同記憶類型（情節記憶、語義記憶、工作記憶）具有獨立的安全上下文，包含基於角色的存取控制、獨立的加密金鑰，以及每種記憶類型的文件化存取模式。 |  1  | D/V |
| 8.6.2 | 確認記憶鞏固過程包含安全驗證，以透過內容清理、來源驗證和儲存前的完整性檢查，防止惡意記憶的注入。                         |  2  | D/V |
| 8.6.3 | 驗證記憶體檢索查詢是否經過驗證和清理，以防止通過查詢模式分析、存取控制執行和結果過濾提取未授權資訊。                       |  2  | D/V |
| 8.6.4 | 驗證記憶體遺忘機制是否通過密鑰刪除、多重覆寫或具備驗證憑證的硬體安全刪除，來以具加密銷毀保證的方式安全刪除敏感資訊。               |  3  | D/V |
| 8.6.5 | 驗證記憶體系統的完整性是否持續透過檢查碼、稽核日誌及自動警報進行監控，以偵測未經授權的修改或損毀，特別是在記憶體內容異常變更時。         |  3  | D/V |

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

