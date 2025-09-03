# C6 供應鏈安全：模型、框架與資料

## 控制目標

AI 供應‑鏈 攻擊利用第三方模型、框架或數據集來嵌入後門、偏見或可利用的程式碼。這些控管提供端到端溯源、漏洞管理與監控，以保護整個模型生命週期。

---

## C6.1 預訓練模型審核與溯源

在任何微調或部署之前，評估並驗證第三‑方模型的來源、許可證及隱藏行為。

|   #   | 描述                                         | 等級  | 角色  |
| :---: | ------------------------------------------ | :-: | :-: |
| 6.1.1 | 驗證每個第三方模型產物是否包含簽名的溯源紀錄，以識別源代碼庫與提交哈希值。      |  1  | D/V |
| 6.1.2 | 在匯入之前，請使用自動化工具對模型進行掃描，以檢測是否存在惡意層或木馬觸發器。    |  1  | D/V |
| 6.1.3 | 驗證轉移學習-微調是否通過對抗性評估，以偵測隱藏行為。                |  2  |  D  |
| 6.1.4 | 驗證模型授權、出口管制標籤與資料來源聲明是否已記錄在 ML‑BOM 條目中。     |  2  |  V  |
| 6.1.5 | 請確保高風險模型（公開上傳的權重、未經驗證的創作者）在人工審查與簽核之前仍保持隔離。 |  3  | D/V |

---

## C6.2 框架 & 函式庫 掃描

持續掃描機器學習（ML）框架與函式庫中的 CVE 漏洞與惡意程式碼，以確保執行時堆疊的安全。

|   #   | 描述                                       | 等級  | 角色  |
| :---: | ---------------------------------------- | :-: | :-: |
| 6.2.1 | 驗證 CI 流水線是否對 AI 框架和關鍵函式庫執行依賴性掃描工具。       |  1  | D/V |
| 6.2.2 | 驗證關鍵漏洞（CVSS ≥ 7.0）是否會阻止推廣至生產映像檔。         |  1  | D/V |
| 6.2.3 | 驗證靜態程式碼分析是否能對分叉或放入專案中的機器學習函式庫進行分析。       |  2  |  D  |
| 6.2.4 | 驗證框架升級提案是否包含安全影響評估，並參考公開的 CVE 資料來源。      |  2  |  V  |
| 6.2.5 | 驗證執行時感測器是否會對偏離已簽署的 SBOM 的非預期動態函式庫載入發出警報。 |  3  |  V  |

---

## C6.3 依賴鎖定與驗證

將每個依賴鎖定為不可變的雜湊值，並重現建置，以確保產物完全相同且防篡改。

|   #   | 描述                                    | 等級  | 角色  |
| :---: | ------------------------------------- | :-: | :-: |
| 6.3.1 | 驗證所有套件管理器是否透過鎖檔強制進行版本鎖定。              |  1  | D/V |
| 6.3.2 | 驗證在容器引用中使用不可變的摘要，而不是可變的標籤。            |  1  | D/V |
| 6.3.3 | 驗證可重現‑建置檢查是否在跨 CI 執行間比較雜湊值，以確保輸出完全一致。 |  2  |  D  |
| 6.3.4 | 驗證建置簽章是否會保存18個月，以確保審計可追溯性。            |  2  |  V  |
| 6.3.5 | 驗證過期的相依性是否會觸發自動化拉取請求，以更新或分叉固定版本。      |  3  |  D  |

---

## C6.4 可信來源強制執行

僅允許從經過密碼學驗證、經組織核可的來源下載工件，並阻止其他一切。

|   #   | 描述                                         | 等級  | 角色  |
| :---: | ------------------------------------------ | :-: | :-: |
| 6.4.1 | 請確認模型權重、資料集與容器僅從經批准的域名或內部註冊表下載。            |  1  | D/V |
| 6.4.2 | 確保 Sigstore/Cosign 簽名在工件被快取到本地之前就能驗證發布者身份。 |  1  | D/V |
| 6.4.3 | 驗證出站代理是否阻止未經身份驗證的工件下載，以落實可信來源政策。           |  2  |  D  |
| 6.4.4 | 確保儲存庫的允許‑清單按季度審查，且每個條目均附有商業正當性證據。          |  2  |  V  |
| 6.4.5 | 驗證政策違規是否會觸發對工件的隔離，以及相依流水線執行的回滾。            |  3  |  V  |

---

## C6.5 第三方資料集風險評估

評估外部資料集在資料中毒、偏見與法規遵循方面，並在整個生命週期內對其進行監控。

|   #   | 描述                                         | 等級  | 角色  |
| :---: | ------------------------------------------ | :-: | :-: |
| 6.5.1 | 驗證外部資料集是否經過中毒風險評分（例如資料指紋比對、離群值檢測）。         |  1  | D/V |
| 6.5.2 | 請確保在資料集審核通過之前，已計算偏倚指標（人口統計平等、平等機會）。        |  1  |  D  |
| 6.5.3 | 驗證資料集的來源與授權條款是否已被納入 ML‑BOM 條目中。            |  2  |  V  |
| 6.5.4 | 驗證定期監控是否能偵測託管資料集中的漂移或損壞。                   |  2  |  V  |
| 6.5.5 | 驗證在訓練之前，透過自動化清理移除不允許的內容（版權內容、PII（個人識別資訊））。 |  3  |  D  |

---

## C6.6 供應鏈攻擊監控

透過 CVE 資訊源、審計‑日誌分析，以及紅隊‑模擬，及早偵測供應‑鏈威脅。

|   #   | 描述                                             | 等級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 6.6.1 | 驗證 CI/CD 的審計日誌是否能流向 SIEM 以偵測異常的套件拉取或被竄改的建置步驟。  |  1  |  V  |
| 6.6.2 | 確認事件回應流程手冊是否包含針對被入侵的模型或函式庫的回滾程序。               |  2  |  D  |
| 6.6.3 | 驗證在警報分流中，威脅情報增強標籤是否包含機器學習‑特定指標（例如，模型‑中毒 IoCs）。 |  3  |  V  |

---

## C6.7 ML‑BOM 用於模型工件

生成並簽署詳盡的機器學習專用 SBOM（ML‑BOM），以便下游消費者在部署時驗證元件完整性。

|   #   | 描述                                            | 等級  | 角色  |
| :---: | --------------------------------------------- | :-: | :-: |
| 6.7.1 | 驗證每個模型工件發布一份 ML‑BOM，其中列出資料集、權重、超參數和許可證。       |  1  | D/V |
| 6.7.2 | 確保 ML‑BOM 的生成與 Cosign 簽署在 CI 中自動化，且成為合併的必須條件。 |  1  | D/V |
| 6.7.3 | 若任一元件元資料（雜湊值、授權條款）缺失，ML‑BOM 的完整性檢查將導致建置失敗。    |  2  |  D  |
| 6.7.4 | 驗證下游使用者能透過 API 查詢 ML-BOMs，以在部署時驗證已匯入的模型。      |  2  |  V  |
| 6.7.5 | 驗證 ML‑BOMs 是否已進行版本控管與差異比對，以檢測未經授權的修改。         |  3  |  V  |

---

## 參考文獻

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

