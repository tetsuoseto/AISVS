# C6 模型、框架與數據的供應鏈安全

## 控制目標

AI 供應鏈攻擊利用第三方模型、框架或資料集來嵌入後門、偏見或可被利用的程式碼。這些控制措施提供端到端的來源追蹤、漏洞管理和監控，以保護整個模型生命週期。

---

## C6.1 預訓練模型審核與來源追蹤

在進行任何微調或部署之前，評估並驗證第三方模型的來源、許可證和隱藏行為。

|   #   | 描述                                         | 層級  | 角色  |
| :---: | ------------------------------------------ | :-: | :-: |
| 6.1.1 | 驗證每個第三方模型工件是否包含簽署的來源記錄，該記錄識別源代碼庫和提交哈希值。    |  1  | D/V |
| 6.1.2 | 確認模型在導入前已使用自動化工具掃描是否含有惡意層或特洛伊觸發器。          |  1  | D/V |
| 6.1.3 | 驗證轉移學習微調是否通過對抗性評估以偵測隱藏行為。                  |  2  |  D  |
| 6.1.4 | 確認模型許可證、出口管制標籤和數據來源聲明是否已記錄在 ML-BOM 條目中。    |  2  |  V  |
| 6.1.5 | 驗證高風險模型（公開上傳的權重、未經驗證的創作者）在人工審核和簽核之前保持隔離狀態。 |  3  | D/V |

---

## C6.2 框架與函式庫掃描

持續掃描機器學習框架和函式庫中的已知漏洞（CVE）及惡意代碼，以維持運行時堆疊的安全性。

|   #   | 描述                                   | 層級  | 角色  |
| :---: | ------------------------------------ | :-: | :-: |
| 6.2.1 | 確認 CI 管道在 AI 框架和關鍵函式庫上執行依賴掃描器。       |  1  | D/V |
| 6.2.2 | 驗證關鍵漏洞（CVSS ≥ 7.0）是否阻止推廣到生產映像。       |  1  | D/V |
| 6.2.3 | 確認靜態程式碼分析是否在派生或外掛的機器學習庫上執行。          |  2  |  D  |
| 6.2.4 | 驗證框架升級提案是否包含參考公開 CVE 資料庫的安全影響評估。     |  2  |  V  |
| 6.2.5 | 驗證運行時感測器是否會對偏離已簽署 SBOM 的異常動態庫載入發出警報。 |  3  |  V  |

---

## C6.3 依賴固定與驗證

將每個依賴項釘選至不可變的摘要，並重現構建以確保產物完全相同且未被篡改。

|   #   | 描述                                                         | 層級  | 角色  |
| :---: | ---------------------------------------------------------- | :-: | :-: |
| 6.3.1 | 確認所有套件管理員皆透過鎖定檔強制版本固定。                                     |  1  | D/V |
| 6.3.2 | 確認在容器引用中使用不可變的摘要（immutable digests），而非可變的標籤（mutable tags）。 |  1  | D/V |
| 6.3.3 | 確認可重現構建檢查比較 CI 執行期間的雜湊值，以確保輸出一致。                           |  2  |  D  |
| 6.3.4 | 確認建置證明已儲存18個月以供稽核追蹤使用。                                     |  2  |  V  |
| 6.3.5 | 驗證過期的相依性是否會觸發自動化的拉取請求以更新或分叉鎖定版本。                           |  3  |  D  |

---

## C6.4 可信來源強制執行

只允許從經加密驗證並獲組織批准的來源下載工件，阻擋所有其他來源。

|   #   | 描述                                        | 層級  | 角色  |
| :---: | ----------------------------------------- | :-: | :-: |
| 6.4.1 | 驗證模型權重、資料集和容器僅從核准的網域或內部註冊表下載。             |  1  | D/V |
| 6.4.2 | 在工件被本地快取之前，確認 Sigstore/Cosign 簽章以驗證發布者身份。 |  1  | D/V |
| 6.4.3 | 驗證出口代理是否阻止未經身份驗證的工件下載，以強制執行受信任來源政策。       |  2  |  D  |
| 6.4.4 | 確認儲存庫允許清單每季進行審查，並有每個條目的業務理由證據。            |  2  |  V  |
| 6.4.5 | 驗證政策違規是否會觸發工件的隔離以及依賴管線執行的回滾。              |  3  |  V  |

---

## C6.5 第三方數據集風險評估

評估外部資料集的中毒、偏見及法律合規性，並在其生命周期中持續監控。

|   #   | 描述                                   | 層級  | 角色  |
| :---: | ------------------------------------ | :-: | :-: |
| 6.5.1 | 確認外部數據集進行了中毒風險評分（例如，數據指紋識別、異常值檢測）。   |  1  | D/V |
| 6.5.2 | 確認在數據集核准之前已計算偏差指標（人口統計平價、平等機會）。      |  1  |  D  |
| 6.5.3 | 確認在 ML-BOM 條目中已記錄資料集的來源及許可條款。        |  2  |  V  |
| 6.5.4 | 驗證定期監控是否能偵測託管資料集中的漂移或損壞。             |  2  |  V  |
| 6.5.5 | 在訓練之前，請確認已透過自動清理移除不允許的內容（版權、個人識別資訊）。 |  3  |  D  |

---

## C6.6 供應鏈攻擊監控

透過 CVE 資料饋送、稽核日誌分析及紅隊模擬，提前偵測供應鏈威脅。

|   #   | 描述                                           | 層級  | 角色  |
| :---: | -------------------------------------------- | :-: | :-: |
| 6.6.1 | 確認 CI/CD 審計日誌是否串流至 SIEM，以偵測異常的套件拉取或被竄改的構建步驟。 |  1  |  V  |
| 6.6.2 | 確認事件響應手冊中包含對受損模型或庫的回滾程序。                     |  2  |  D  |
| 6.6.3 | 驗證威脅情報增強是否在告警分類中標記機器學習特定指標（例如，模型中毒的 IoC）。    |  3  |  V  |

---

## C6.7 模型構件的 ML‑BOM

生成並簽署詳細的機器學習專用軟體物料清單（ML‑BOM），以便下游使用者能在部署時驗證組件的完整性。

|   #   | 描述                                             | 層級  | 角色  |
| :---: | ---------------------------------------------- | :-: | :-: |
| 6.7.1 | 確認每個模型工件都發布包含數據集、權重、超參數和授權的 ML-BOM。            |  1  | D/V |
| 6.7.2 | 確認 ML-BOM 生成和 Cosign 簽署已在持續整合（CI）中自動化，且為合併所必需。 |  1  | D/V |
| 6.7.3 | 驗證如果任何元件元資料（雜湊值、授權）缺失，ML‑BOM 完整性檢查會使建置失敗。      |  2  |  D  |
| 6.7.4 | 驗證下游使用者是否能透過 API 查詢 ML-BOM 以在部署時驗證匯入的模型。       |  2  |  V  |
| 6.7.5 | 驗證 ML-BOM 是否有版本控制並進行差異比較以偵測未經授權的修改。            |  3  |  V  |

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

