# 11 隱私保護與個人資料管理

## 控制目標

在整個人工智慧生命週期中——資料收集、訓練、推論和事件回應——維持嚴格的隱私保障，確保個人資料僅在明確同意、最小必要範圍、可證明的刪除及正式的隱私保證下進行處理。

---

## 11.1 匿名化與資料最小化

|   #    | 描述                                     | 層級  | 角色  |
| :----: | -------------------------------------- | :-: | :-: |
| 11.1.1 | 確認直接識別碼和準識別碼已被移除或哈希處理。                 |  1  | D/V |
| 11.1.2 | 驗證自動審計是否測量 k-匿名性/l-多樣性，並在閾值低於政策時發出警報。  |  2  | D/V |
| 11.1.3 | 驗證模型特徵重要性報告以證明識別碼洩漏的互信息不超過 ε = 0.01。   |  2  |  V  |
| 11.1.4 | 驗證形式證明或合成數據認證即使在連結攻擊下，也顯示重識別風險 ≤ 0.05。 |  3  |  V  |

---

## 11.2 被遺忘權與刪除強制執行

|   #    | 描述                                                 | 層級  | 角色  |
| :----: | -------------------------------------------------- | :-: | :-: |
| 11.2.1 | 驗證數據主體刪除請求能在少於 30 天的服務水平協議內，傳播至原始數據集、檢查點、嵌入、日誌和備份。 |  1  | D/V |
| 11.2.2 | 驗證「機器遺忘」程序是否透過經認證的遺忘演算法，實際重新訓練或近似移除資料。             |  2  |  D  |
| 11.2.3 | 驗證影子模型評估證明，在遺忘後，被遺忘的記錄對輸出影響不到1%。                   |  2  |  V  |
| 11.2.4 | 驗證刪除事件是否被不可變地記錄並可供監管機構審核。                          |  3  |  V  |

---

## 11.3 差分隱私防護措施

|   #    | 描述                            | 層級  | 角色  |
| :----: | ----------------------------- | :-: | :-: |
| 11.3.1 | 驗證當累積ε超過政策門檻時，隱私損失計算儀表板會發出警報。 |  2  | D/V |
| 11.3.2 | 確認黑盒隱私審計估計的 ε̂ 在宣稱值的 10% 範圍內。 |  2  |  V  |
| 11.3.3 | 驗證形式化證明是否涵蓋所有訓練後微調和嵌入。        |  3  |  V  |

---

## 11.4 目的限制與範圍擴張保護

|   #    | 描述                                                  | 層級  | 角色  |
| :----: | --------------------------------------------------- | :-: | :-: |
| 11.4.1 | 確認每個資料集和模型檢查點都帶有與原始同意書一致的機器可讀目標標籤。                  |  1  |  D  |
| 11.4.2 | 驗證執行時監視器是否能偵測與宣告目的不一致的查詢並觸發軟拒絕。                     |  1  | D/V |
| 11.4.3 | 驗證政策即代碼門禁是否阻止在未經數據保護影響評估 (DPIA) 審查的情況下，將模型重新部署到新領域。 |  3  |  D  |
| 11.4.4 | 驗證正式的可追蹤性證明顯示每個個人資料生命週期均保持在同意的範圍內。                  |  3  |  V  |

---

## 11.5 同意管理與合法依據追蹤

|   #    | 描述                                      | 層級  | 角色  |
| :----: | --------------------------------------- | :-: | :-: |
| 11.5.1 | 驗證同意管理平台（CMP）是否記錄每個資料主體的選擇加入狀態、目的及保留期間。 |  1  | D/V |
| 11.5.2 | 驗證 API 是否公開同意權杖；模型必須在推論前驗證權杖範圍。         |  2  |  D  |
| 11.5.3 | 確認拒絕或撤回同意會在 24 小時內停止處理流程。               |  2  | D/V |

---

## 11.6 帶有隱私控制的聯邦學習

|   #    | 描述                           | 層級  | 角色  |
| :----: | ---------------------------- | :-: | :-: |
| 11.6.1 | 驗證客戶端更新在聚合前是否使用了本地差分隱私噪聲添加。  |  1  |  D  |
| 11.6.2 | 驗證訓練指標具備差分隱私性，且絕不洩露單一客戶端的損失。 |  2  | D/V |
| 11.6.3 | 確認已啟用抗中毒聚合（例如，Krum/修剪均值）。    |  2  |  V  |
| 11.6.4 | 驗證形式證明展示整體ε預算的效用損失小於5。       |  3  |  V  |

---

### 參考文獻

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

