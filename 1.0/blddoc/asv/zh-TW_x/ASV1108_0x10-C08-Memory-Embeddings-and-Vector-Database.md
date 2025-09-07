# C8 記憶體、嵌入向量與向量資料庫安全性

## 控制目標

嵌入向量和向量存儲作為現代 AI 系統的「即時記憶」，持續接受用戶提供的數據，並通過檢索增強生成（RAG）將其呈現在模型上下文中。如果不加以管理，這些記憶可能洩露個人識別信息（PII）、違反同意規定，或被反轉以重建原始文本。此控制類別的目標是加固記憶管道和向量資料庫，以確保存取權限採取最小權限原則，嵌入向量具備隱私保護功能，存儲的向量可設置過期或按需撤銷，且每位用戶的記憶不會污染其他用戶的提示或輸出結果。

---

## C8.1 記憶體與 RAG 指標的存取控制

對每個向量集合施加細粒度的存取控制。

|   #   | 描述                                                          | 等級  | 角色  |
| :---: | ----------------------------------------------------------- | :-: | :-: |
| 8.1.1 | 驗證行/命名空間層級的存取控制規則是否限制每個租戶、集合或文件標籤的插入、刪除和查詢操作。               |  1  | D/V |
| 8.1.2 | 驗證 API 金鑰或 JWT 是否攜帶有範圍限制的權限聲明（例如，集合 ID、操作動詞），並且至少每季度進行一次輪換。 |  1  | D/V |
| 8.1.3 | 確認提升權限的嘗試（例如，跨命名空間的相似性查詢）能在 5 分鐘內被偵測並記錄到 SIEM 中。            |  2  | D/V |
| 8.1.4 | 確認向量資料庫審核記錄中的主體識別碼、操作、向量 ID/命名空間、相似度閾值及結果數量。                |  2  | D/V |
| 8.1.5 | 確認每當引擎升級或索引分片規則更改時，存取決策是否有進行繞過缺陷的測試。                        |  3  |  V  |

---

## C8.2 嵌入消毒與驗證

在向量化之前，預先篩查文本中的個人身份信息（PII），進行遮蔽或假名化，並可選擇對嵌入進行後處理以去除殘留信號。

|   #   | 描述                                                | 等級  | 角色  |
| :---: | ------------------------------------------------- | :-: | :-: |
| 8.2.1 | 確保透過自動分類器偵測到個人識別資訊（PII）及受管制資料，並在嵌入之前進行遮罩、標記化或刪除。  |  1  | D/V |
| 8.2.2 | 驗證嵌入式管線能夠拒絕或隔離含有可執行程式碼或非UTF-8人工製品的輸入，這些內容可能會污染索引。 |  1  |  D  |
| 8.2.3 | 驗證是否對距離任何已知 PI I 令牌低於可配置閾值的句子嵌入應用了本地或度量微分隱私清理。    |  2  | D/V |
| 8.2.4 | 確認清理效果（例如，個人可識別資訊刪除的召回率、語義偏移）至少每半年對標準語料庫進行一次驗證。   |  2  |  V  |
| 8.2.5 | 確認清理配置已進行版本控制，且變更需經過同儕審查。                         |  3  | D/V |

---

## C8.3 記憶體過期、撤銷與刪除

GDPR「被遺忘權」及類似法律要求及時刪除；因此，向量存儲必須支持TTL、硬刪除和墓碑標記，以確保被撤銷的向量無法被恢復或重新索引。

|   #   | 描述                                             | 等級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 8.3.1 | 確認每個向量和元資料記錄都帶有 TTL 或由自動清理作業執行的明確保存標籤。         |  1  | D/V |
| 8.3.2 | 驗證使用者發起的刪除請求是否在30天內清除向量、元資料、快取副本及衍生索引。         |  1  | D/V |
| 8.3.3 | 驗證邏輯刪除是否隨後進行了存儲區塊的密碼學銷毀（如果硬體支持），或通過密鑰庫密鑰銷毀來實現。 |  2  |  D  |
| 8.3.4 | 驗證已過期的向量在過期後 500 毫秒內被排除在最近鄰搜索結果之外。             |  3  | D/V |

---

## C8.4 預防嵌入反轉與洩漏

最近的防禦措施——噪聲疊加、投影網絡、隱私神經元擾動和應用層加密——能將令牌級逆向率降至低於5%。

|   #   | 描述                                                                   | 等級  | 角色  |
| :---: | -------------------------------------------------------------------- | :-: | :-: |
| 8.4.1 | 確認是否存在涵蓋反演、成員資格及屬性推斷攻擊的正式威脅模型，並且該模型每年均有進行審查。                         |  1  |  V  |
| 8.4.2 | 確認應用層加密或可搜尋加密能保護向量，避免基礎設施管理員或雲端人員直接讀取。                               |  2  | D/V |
| 8.4.3 | 驗證防禦參數（DP 的 ε、噪聲 σ、投影維度 k）是否在隱私保護 ≥ 99% 代幣保護與效用損失 ≤ 3% 的準確率損失之間取得平衡。 |  3  |  V  |
| 8.4.4 | 確認反轉韌性指標是模型更新發布門檻的一部分，並且定義了回歸預算。                                     |  3  | D/V |

---

## C8.5 用戶專屬記憶的範圍執行

跨租戶洩漏仍然是主要的RAG風險：未經適當過濾的相似性查詢可能會暴露其他客戶的私人文件。

|   #   | 描述                                             | 等級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 8.5.1 | 確認每個檢索查詢在傳遞給大型語言模型（LLM）提示之前，均已依租戶/使用者ID進行後置篩選。 |  1  | D/V |
| 8.5.2 | 驗證集合名稱或命名空間 ID 是否依據用戶或租戶進行加鹽，以防止向量在不同範疇間發生碰撞。  |  1  |  D  |
| 8.5.3 | 確認超過可配置距離閾值但超出呼叫者範圍的相似性結果被丟棄並觸發安全警報。           |  2  | D/V |
| 8.5.4 | 驗證多租戶壓力測試模擬嘗試檢索範圍外文件的對抗性查詢，並展示零洩漏。             |  2  |  V  |
| 8.5.5 | 驗證加密金鑰是否按租戶劃分，確保即使物理存儲共用時仍維持密碼學隔離。             |  3  | D/V |

---

## C8.6 先進記憶系統安全性

針對複雜記憶體架構（包括情節記憶、語意記憶和工作記憶）之安全控制，涵蓋特定的隔離與驗證要求。

|   #   | 描述                                                                          | 等級  | 角色  |
| :---: | --------------------------------------------------------------------------- | :-: | :-: |
| 8.6.1 | 驗證不同記憶類型（情節記憶、語意記憶、工作記憶）是否具有隔離的安全上下文，包括基於角色的存取控制、獨立的加密密鑰，以及每種記憶類型的存取模式文件記錄。 |  1  | D/V |
| 8.6.2 | 確認記憶整合過程包含安全驗證，以透過內容清理、來源驗證和完整性檢查防止惡意記憶的注入，並在儲存前進行此類驗證。                     |  2  | D/V |
| 8.6.3 | 驗證記憶檢索查詢是否經過驗證和淨化，以防止透過查詢模式分析、存取控制執行及結果過濾來提取未經授權的資訊。                        |  2  | D/V |
| 8.6.4 | 驗證記憶體遺忘機制是否透過密鑰刪除、多重覆寫或具驗證證書的硬體安全刪除，並具備密碼學擦除保證，安全刪除敏感資訊。                    |  3  | D/V |
| 8.6.5 | 確認記憶體系統完整性透過校驗和、稽核日誌及自動警報持續監控，以防止未經授權的修改或損壞，當記憶體內容在正常操作之外改變時即發出警報。          |  3  | D/V |

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

