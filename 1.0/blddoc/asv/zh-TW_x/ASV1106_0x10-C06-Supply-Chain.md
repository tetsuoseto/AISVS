# C6 模型、框架與數據的供應鏈安全

## 控制目標

AI 供應鏈攻擊利用第三方模型、框架或數據集來嵌入後門、偏見或可被利用的代碼。這些控制措施提供端到端的溯源、漏洞管理和監控，以保護整個模型生命週期。

---

## C6.1 預訓練模型審查與來源管理

在進行任何微調或部署之前，評估並驗證第三方模型的來源、許可和隱藏行為。

|   #   | 描述                                         | 等級  | 角色  |
| :---: | ------------------------------------------ | :-: | :-: |
| 6.1.1 | 確認每個第三方模型產物均包含簽署的來源記錄，標明來源儲存庫和提交哈希。        |  1  | D/V |
| 6.1.2 | 在導入模型之前，請使用自動化工具驗證模型是否已掃描惡意層或特洛伊觸發器。       |  1  | D/V |
| 6.1.3 | 驗證遷移學習微調通過對抗評估以偵測隱藏行為。                     |  2  |  D  |
| 6.1.4 | 確認模型授權、出口管制標籤及資料來源聲明已記錄於 ML-BOM 條目中。       |  2  |  V  |
| 6.1.5 | 驗證高風險模型（公開上傳的權重、未經驗證的創作者）在人工審查和批准之前保持隔離狀態。 |  3  | D/V |

---

## C6.2 框架與函式庫掃描

持續掃描機器學習框架和庫的已知漏洞（CVE）及惡意代碼，以保持運行時堆疊的安全。

|   #   | 描述                                 | 等級  | 角色  |
| :---: | ---------------------------------- | :-: | :-: |
| 6.2.1 | 驗證 CI 管道是否在 AI 框架和關鍵函式庫上執行依賴掃描器。   |  1  | D/V |
| 6.2.2 | 驗證關鍵漏洞（CVSS ≥ 7.0）是否阻止推廣到生產映像。     |  1  | D/V |
| 6.2.3 | 驗證靜態程式碼分析是否在派生或外包的機器學習庫上執行。        |  2  |  D  |
| 6.2.4 | 確認框架升級提案包含參考公共CVE資料來源的安全影響評估。      |  2  |  V  |
| 6.2.5 | 驗證運行時感測器是否對偏離簽署 SBOM 的異常動態庫載入發出警報。 |  3  |  V  |

---

## C6.3 依賴鎖定與驗證

將每個依賴鎖定到不可變的摘要，並重現構建以確保產生相同且無篡改的工件。

|   #   | 描述                                   | 等級  | 角色  |
| :---: | ------------------------------------ | :-: | :-: |
| 6.3.1 | 確認所有套件管理器均透過鎖定檔強制版本固定。               |  1  | D/V |
| 6.3.2 | 驗證在容器參考中使用的是不可變摘要而非可變標籤。             |  1  | D/V |
| 6.3.3 | 確認可重現構建檢查在不同的 CI 運行中比較雜湊值，以確保輸出結果一致。 |  2  |  D  |
| 6.3.4 | 驗證建置證明已保存18個月以供審計追蹤。                 |  2  |  V  |
| 6.3.5 | 確認過期的相依性會觸發自動拉取請求，以更新或分支固定版本。        |  3  |  D  |

---

## C6.4 可信來源執行

僅允許從經加密驗證且組織核准的來源下載工件，並阻擋所有其他來源。

|   #   | 描述                                       | 等級  | 角色  |
| :---: | ---------------------------------------- | :-: | :-: |
| 6.4.1 | 驗證模型權重、資料集和容器僅從核准的網域或內部註冊庫下載。            |  1  | D/V |
| 6.4.2 | 驗證 Sigstore/Cosign 簽章在工件本地快取之前，能確認發佈者身份。 |  1  | D/V |
| 6.4.3 | 驗證出口代理是否阻止未經驗證的工件下載以執行受信任來源政策。           |  2  |  D  |
| 6.4.4 | 驗證儲存庫允許清單是否每季度審查一次，並且每個條目均有業務理由的證據。      |  2  |  V  |
| 6.4.5 | 驗證政策違規是否會觸發對工件的隔離以及相關管線運行的回滾。            |  3  |  V  |

---

## C6.5 第三方資料集風險評估

評估外部數據集的中毒、偏見和法律合規性，並在其整個生命周期內進行監控。

|   #   | 描述                                    | 等級  | 角色  |
| :---: | ------------------------------------- | :-: | :-: |
| 6.5.1 | 驗證外部數據集是否經過中毒風險評分（例如，數據指紋識別、異常值檢測）。   |  1  | D/V |
| 6.5.2 | 請確認在數據集批准之前已計算偏差指標（人口統計平等、機會均等）。      |  1  |  D  |
| 6.5.3 | 確認資料集的來源和許可條款已記錄在 ML-BOM 條目中。         |  2  |  V  |
| 6.5.4 | 驗證週期性監控是否能偵測到託管資料集中的漂移或損壞。            |  2  |  V  |
| 6.5.5 | 確認在訓練之前，透過自動清除機制移除不允許的內容（版權、個人可識別資訊）。 |  3  |  D  |

---

## C6.6 供應鏈攻擊監控

透過 CVE 資訊來源、審計日誌分析以及紅隊模擬，及早偵測供應鏈威脅。

|   #   | 描述                                              | 等級  | 角色  |
| :---: | ----------------------------------------------- | :-: | :-: |
| 6.6.1 | 驗證 CI/CD 審計日誌是否流向 SIEM 偵測，以監測異常的套件拉取或已被篡改的建置步驟。 |  1  |  V  |
| 6.6.2 | 確認事故應對手冊包含對受損模型或庫的回滾程序。                         |  2  |  D  |
| 6.6.3 | 驗證威脅情報豐富化標籤於警報分流中是否標註了機器學習專用指標（例如，模型中毒的事件跡象）。   |  3  |  V  |

---

## C6.7 用於模型工件的機器學習物料清單（ML-BOM）

生成並簽署詳細的機器學習專用軟體物料清單（ML‑BOM），以便下游使用者在部署時驗證組件的完整性。

|   #   | 描述                                              | 等級  | 角色  |
| :---: | ----------------------------------------------- | :-: | :-: |
| 6.7.1 | 確認每個模型產物都會發布包含資料集、權重、超參數和許可證的 ML‑BOM。           |  1  | D/V |
| 6.7.2 | 請確認 ML-BOM 生成和 Cosign 簽名已在持續整合（CI）中自動化，且為合併所必需。 |  1  | D/V |
| 6.7.3 | 驗證如果任何組件元數據（哈希、許可證）缺失，ML‑BOM 完整性檢查會導致構建失敗。      |  2  |  D  |
| 6.7.4 | 驗證下游使用者是否能夠透過 API 查詢 ML-BOM，以在部署時驗證匯入的模型。       |  2  |  V  |
| 6.7.5 | 驗證機器學習物料清單（ML-BOMs）是否進行版本控制並進行差異比較，以檢測未授權的修改。   |  3  |  V  |

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

