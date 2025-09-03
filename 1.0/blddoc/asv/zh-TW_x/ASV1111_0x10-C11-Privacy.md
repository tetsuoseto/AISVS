# 11 隱私保護與個人資料管理

## 控制目標

在整個人工智慧生命週期中維護嚴格的隱私保障—包括資料收集、訓練、推理與事件回應—以確保個人資料僅在取得明確同意、最小必要範圍、可證明的刪除，以及正式的隱私保障下被處理。

---

## 11.1 匿名化與資料最小化

|   #    | 描述                                         | 等級  | 角色  |
| :----: | ------------------------------------------ | :-: | :-: |
| 11.1.1 | 驗證直接識別符與準識別符是否已移除，且已進行雜湊處理。                |  1  | D/V |
| 11.1.2 | 驗證自動化審計是否衡量 k-匿名性/l-多樣性，並在閾值低於政策時發出警報。     |  2  | D/V |
| 11.1.3 | 驗證模型的特徵重要性報告，證明不存在超過 ε = 0.01 的互信息的識別資訊洩漏。 |  2  |  V  |
| 11.1.4 | 驗證正式證明或合成數據認證顯示，即使在連結攻擊下，重新識別風險也不超過 0.05。  |  3  |  V  |

---

## 11.2 被遺忘權與刪除執行

|   #    | 描述                                                        | 等級  | 角色  |
| :----: | --------------------------------------------------------- | :-: | :-: |
| 11.2.1 | 驗證個人資料主體刪除請求是否能在小於 30 天的服務水平協議內傳播至原始資料集、檢查點、嵌入向量、日誌與備份。   |  1  | D/V |
| 11.2.2 | 驗證「machine-unlearning」流程是否透過實際重新訓練，或以近似方式移除，並採用經認證的遺忘演算法。 |  2  |  D  |
| 11.2.3 | 驗證顯示，影子模型評估在完成模型遺忘後，被遺忘的資料對輸出之影響少於 1%                     |  2  |  V  |
| 11.2.4 | 驗證刪除事件是否以不可變的方式被記錄，且可供監管機構審計。                             |  3  |  V  |

---

## 11.3 差分隱私防護措施

|   #    | 描述                                            | 等級  | 角色  |
| :----: | --------------------------------------------- | :-: | :-: |
| 11.3.1 | 驗證 隱私-損失 核算 儀表板 在 累積 ε 超過 政策 閾值 時 是否 會 發出 警報。 |  2  | D/V |
| 11.3.2 | 驗證黑箱隱私審計對 ε̂ 的估計是否在宣稱值的 10% 內。                |  2  |  V  |
| 11.3.3 | 驗證正式證明是否涵蓋所有訓練後微調與嵌入向量。                       |  3  |  V  |

---

## 11.4 目的限制與範圍蔓延防護

|   #    | 描述                                          | 等級  | 角色  |
| :----: | ------------------------------------------- | :-: | :-: |
| 11.4.1 | 驗證每個資料集與模型檢查點是否具備機器可讀的用途標籤，且與原始同意保持一致。      |  1  |  D  |
| 11.4.2 | 驗證運行時監控是否能檢測到與聲明用途不一致的查詢，並觸發軟性拒絕。           |  1  | D/V |
| 11.4.3 | 驗證以政策即代碼的閘門是否能在未經 DPIA 評審的情況下，阻止模型重新部署到新領域。 |  3  |  D  |
| 11.4.4 | 驗證正式的可追溯性證明顯示每個個人資料的生命週期均保持在已同意的範圍內。        |  3  |  V  |

---

## 11.5 同意管理與合法依據-追蹤

|   #    | 描述                                            | 等級  | 角色  |
| :----: | --------------------------------------------- | :-: | :-: |
| 11.5.1 | 驗證一個同意管理平台（CMP）是否能根據每位資料主體記錄同意加入狀態、用途與資料保留期限。 |  1  | D/V |
| 11.5.2 | 驗證 API 是否暴露同意令牌；模型必須在推理之前驗證令牌的作用域。            |  2  |  D  |
| 11.5.3 | 確認被拒絕或撤回的同意是否會在 24 小時內停止處理流程。                 |  2  | D/V |

---

## 11.6 具備隱私控制的聯邦學習

|   #    | 描述                                           | 等級  | 角色  |
| :----: | -------------------------------------------- | :-: | :-: |
| 11.6.1 | 驗證客戶端更新在聚合之前是否採用了局部差分隱私噪聲添加。                 |  1  |  D  |
| 11.6.2 | 驗證訓練指標具有差分隱私性，且絕不洩露單一客戶端的損失值。                |  2  | D/V |
| 11.6.3 | 驗證是否已啟用對資料污染具魯棒性的聚合方法（例如 Krum/Trimmed-Mean）。 |  2  |  V  |
| 11.6.4 | 驗證正式證明顯示整體 ε 預算下的效用損失小於 5。                   |  3  |  V  |

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

