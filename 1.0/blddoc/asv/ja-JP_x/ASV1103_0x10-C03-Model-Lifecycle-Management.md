# C3モデルライフサイクル管理および変更管理

## 制御目標

AIシステムは、許可されていないまたは安全でないモデルの変更が本番環境に反映されるのを防ぐ変更管理プロセスを実装しなければなりません。この管理は、開発から展開、廃止までのモデルのライフサイクル全体を通じてモデルの整合性を保証し、迅速なインシデント対応を可能にし、すべての変更に対する責任を維持します。

コアセキュリティ目標: 整合性、トレーサビリティ、および回復力を維持する制御されたプロセスを採用することにより、認可され検証されたモデルのみが本番環境に到達すること。

---

## C3.1 モデル承認と完全性

検証済みの整合性を持つ認可モデルのみが本番環境に到達します。

|   #   | 説明                                                                                            | レベル | 役割  |
| :---: | --------------------------------------------------------------------------------------------- | :-: | :-: |
| 3.1.1 | 展開前に、すべてのモデル成果物（重み、構成、トークナイザー）が承認されたエンティティによって暗号的に署名されていることを検証してください。                         |  1  | D/V |
| 3.1.2 | 依存関係の追跡が、すべての消費システムを特定できるリアルタイムのインベントリを維持していることを確認してください。                                     |  2  |  V  |
| 3.1.3 | モデルの起源記録に、承認する主体の識別情報、トレーニングデータのチェックサム、合格/不合格のステータスを含む検証テスト結果、および作成タイムスタンプが含まれていることを確認してください。 |  3  | D/V |

---

## C3.2 モデル検証およびテスト

モデルは展開前に定義されたセキュリティおよび安全性の検証を通過しなければなりません。

|   #   | 説明                                                                                   | レベル | 役割  |
| :---: | ------------------------------------------------------------------------------------ | :-: | :-: |
| 3.2.1 | モデルが展開前に、事前に合意された組織の合否基準を用いて、入力検証、出力サニタイズ、および安全性評価を含む自動化されたセキュリティテストを受けることを確認してください。 |  1  | D/V |
| 3.2.2 | すべてのモデル変更（展開、構成、廃止）が、タイムスタンプ、認証された実行者の識別、変更タイプ、および変更前後の状態を含む不変の監査記録を生成することを確認してください。 |  1  |  V  |
| 3.2.3 | 検証失敗が、文書化された業務上の正当な理由を持つ事前指名された権限者による明示的なオーバーライド承認後も自動的にモデルの展開をブロックすることを確認してください。    |  2  | D/V |

---

## C3.3 制御された展開とロールバック

モデルのデプロイメントは、制御され、監視され、かつ元に戻せるものでなければなりません。

|   #   | 説明                                                                                                                              | レベル | 役割  |
| :---: | ------------------------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 3.3.1 | 展開プロセスがモデルの有効化前に暗号署名を検証し、整合性チェックサムを計算することを確認し、不一致があった場合は展開を失敗させること。                                                             |  1  | D/V |
| 3.3.2 | 本番環境への展開が、事前に合意されたエラー率、レイテンシ閾値、またはセキュリティアラート基準に基づく自動ロールバックトリガーを伴う段階的なロールアウトメカニズム（カナリアデプロイメント、ブルーグリーンデプロイメント）を実装していることを確認してください。 |  1  |  D  |
| 3.3.3 | ロールバック機能がモデルの完全な状態（重み、構成、依存関係）を原子性を保って復元することを検証してください。                                                                          |  2  | D/V |
| 3.3.4 | 緊急モデルシャットダウン機能が、事前定義された応答時間内にモデルエンドポイントを無効にできることを検証してください。                                                                      |  3  | D/V |

---

## C3.4 セキュア開発プラクティス

モデルの開発およびトレーニングプロセスは、妥協を防ぐために安全な手法に従う必要があります。

|   #   | 説明                                                                                                          | レベル | 役割  |
| :---: | ----------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 3.4.1 | モデルの開発、テスト、および本番環境が物理的または論理的に分離されていることを確認してください。それらは共有インフラストラクチャを持たず、アクセス制御が異なり、データストアも分離されています。            |  1  | D/V |
| 3.4.2 | モデル開発の成果物（ハイパーパラメータ、トレーニングスクリプト、設定ファイル、プロンプトテンプレートなど）がバージョン管理に保存され、トレーニングで使用する前にピアレビューの承認が必要であることを確認してください。 |  1  |  D  |
| 3.4.3 | モデルのトレーニングおよびファインチューニングが、ネットワークアクセスが制御された隔離環境で行われていることを確認してください。                                            |  2  | D/V |
| 3.4.4 | トレーニングデータソースがモデル開発に使用される前に、整合性チェックを通じて検証され、文書化された受け渡し記録を伴う信頼できるソースによって認証されていることを確認してください。                   |  2  |  D  |

---

## C3.5 モデルの廃止と退役

モデルは、もはや必要でない場合やセキュリティ上の問題が特定された場合に、安全に廃止されなければなりません。

|   #   | 説明                                                                                | レベル | 役割  |
| :---: | --------------------------------------------------------------------------------- | :-: | :-: |
| 3.5.1 | 退役したモデルのアーティファクトが安全な暗号消去によって確実に消去されていることを確認する。                                    |  1  | D/V |
| 3.5.2 | モデルの廃止イベントがタイムスタンプとアクターの識別情報と共に記録されていること、ならびに再利用を防ぐためにモデルの署名が取り消されていることを確認してください。 |  2  |  V  |

---

## 参考文献

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

