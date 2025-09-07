# C1 교육 데이터 거버넌스 및 편향 관리

## 제어 목표

학습 데이터는 출처, 보안, 품질 및 공정성을 유지하는 방식으로 수집, 처리 및 관리되어야 합니다. 이렇게 함으로써 법적 의무를 이행하고 편향, 데이터 오염 또는 학습 과정 중 발생할 수 있는 개인정보 침해의 위험을 줄여 전체 AI 생명주기에 영향을 미칠 수 있는 문제를 방지할 수 있습니다.

---

## C1.1 훈련 데이터 출처

모든 데이터셋의 검증 가능한 목록을 유지하고, 신뢰할 수 있는 출처만 허용하며, 감사 가능성을 위해 모든 변경 사항을 기록하십시오.

|   #   | 설명                                                                                               | 레벨  | 역할  |
| :---: | ------------------------------------------------------------------------------------------------ | :-: | :-: |
| 1.1.1 | 교육 데이터 소스(출처, 관리/소유자, 라이선스, 수집 방법, 의도된 사용 제약, 처리 이력)에 대한 최신 재고 목록이 유지되고 있는지 확인하십시오.              |  1  | D/V |
| 1.1.2 | 훈련 데이터 처리 과정에서 불필요한 특징, 속성 또는 필드(예: 사용되지 않은 메타데이터, 민감한 개인 식별 정보(PII), 유출된 테스트 데이터)를 제외했는지 확인합니다. |  1  | D/V |
| 1.1.3 | 모든 데이터셋 변경 사항이 기록된 승인 워크플로우의 적용을 받는지 확인하십시오.                                                     |  2  | D/V |
| 1.1.4 | 가능한 경우 데이터셋 또는 하위 집합에 워터마크나 지문이 포함되어 있는지 확인하십시오.                                                 |  3  | D/V |

---

## C1.2 학습 데이터 보안 및 무결성

학습 데이터에 대한 접근을 제한하고, 저장 중 및 전송 중에 암호화하며, 변조, 도난 또는 데이터 중독을 방지하기 위해 그 무결성을 검증합니다.

|   #   | 설명                                                                          | 레벨  | 역할  |
| :---: | --------------------------------------------------------------------------- | :-: | :-: |
| 1.2.1 | 교육 데이터 저장소 및 파이프라인이 접근 제어로 보호되는지 확인하세요.                                     |  1  | D/V |
| 1.2.2 | 학습 데이터에 대한 모든 접근이 사용자, 시간, 작업을 포함하여 기록되었는지 확인하십시오.                          |  2  | D/V |
| 1.2.3 | 훈련 데이터셋이 전송 중 및 저장 중에 업계 표준 암호화 알고리즘과 키 관리 방식을 사용하여 암호화되어 있는지 확인하십시오.       |  2  | D/V |
| 1.2.4 | 학습 데이터 저장 및 전송 중 데이터 무결성을 보장하기 위해 암호화 해시 또는 디지털 서명이 사용되는지 확인하십시오.           |  2  | D/V |
| 1.2.5 | 자동화된 탐지 기법이 학습 데이터의 무단 변경 또는 손상을 방지하기 위해 적용되었는지 확인하십시오.                     |  2  | D/V |
| 1.2.6 | 구식 학습 데이터가 안전하게 삭제되거나 익명화되었는지 확인하십시오.                                       |  2  | D/V |
| 1.2.7 | 모든 학습 데이터셋 버전이 고유하게 식별되고, 불변으로 저장되며, 롤백 및 포렌식 분석을 지원할 수 있도록 감사 가능함을 확인하십시오. |  3  | D/V |

---

## C1.3 훈련 데이터 라벨링 품질, 무결성 및 보안

레이블을 보호하고 중요한 데이터에 대해 기술 검토를 요구하십시오.

|   #   | 설명                                                                                        | 레벨  | 역할  |
| :---: | ----------------------------------------------------------------------------------------- | :-: | :-: |
| 1.3.1 | 암호화 해시 또는 디지털 서명이 라벨 아티팩트에 적용되어 무결성과 진위성을 보장하는지 검증하십시오.                                   |  2  | D/V |
| 1.3.2 | 라벨링 인터페이스와 플랫폼이 강력한 접근 통제를 시행하고, 모든 라벨링 활동에 대한 변조 감지 감사 로그를 유지하며, 무단 수정으로부터 보호하는지 확인하십시오. |  2  | D/V |
| 1.3.3 | 라벨의 민감한 정보가 저장 시 및 전송 중 데이터 필드 수준에서 삭제되었거나 익명화되었거나 암호화되었는지 확인하십시오.                        |  3  | D/V |

---

## C1.4 학습 데이터 품질 및 보안 보증

자동화된 검증, 수동 샘플 검사 및 기록된 수정 조치를 결합하여 데이터셋 신뢰성을 보장합니다.

|   #   | 설명                                                                                                                                                                                | 레벨  | 역할  |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 1.4.1 | 자동화 테스트가 모든 인게스트 또는 중요한 데이터 변환 시 형식 오류 및 널 값을 감지하는지 확인하십시오.                                                                                                                       |  1  |  D  |
| 1.4.2 | LLM 훈련 및 미세조정 파이프라인이 잠재적인 중독 공격(예: 레이블 플리핑, 백도어 트리거 삽입, 역할 전환 명령, 영향력 있는 인스턴스 공격) 또는 훈련 데이터에서의 의도치 않은 데이터 손상을 식별하기 위해 중독 탐지 및 데이터 무결성 검증(예: 통계 방법, 이상치 탐지, 임베딩 분석)을 구현하는지 확인하십시오. |  2  | D/V |
| 1.4.3 | 적절한 방어책(생성된 적대적 예제를 사용한 적대적 학습, 변형된 입력을 통한 데이터 증강, 또는 강인한 최적화 기법 등)이 위험 평가에 근거하여 관련 모델에 구현되고 조정되었는지 검증합니다.                                                                        |  3  | D/V |
| 1.4.4 | 자동으로 생성된 라벨(예: LLM 또는 약한 감독을 통해 생성된 라벨)이 허위 정보, 오도된 내용 또는 신뢰도가 낮은 라벨을 감지하기 위해 신뢰도 임계값과 일관성 검사를 거치도록 확인하십시오.                                                                       |  2  | D/V |
| 1.4.5 | 자동화된 테스트가 모든 수집 또는 중요한 데이터 변환 시 라벨 스큐를 감지하는지 확인하십시오.                                                                                                                              |  3  |  D  |

---

## C1.5 데이터 계보 및 추적 가능성

감사 추적 가능성과 사고 대응을 위해 각 데이터 포인트가 출처에서 모델 입력까지의 전체 여정을 추적합니다.

|   #   | 설명                                                                                                            | 레벨  | 역할  |
| :---: | ------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 1.5.1 | 각 데이터 포인트의 모든 변환, 증강, 병합을 포함한 출처가 기록되고 재구성될 수 있는지 확인하십시오.                                                     |  2  | D/V |
| 1.5.2 | 계보 기록이 불변하며, 안전하게 저장되고, 감사를 위해 접근 가능함을 확인하십시오.                                                                |  2  | D/V |
| 1.5.3 | 개인정보 보호 또는 생성 기법을 통해 생성된 합성 데이터가 계보 추적에 포함되는지 확인하고, 모든 합성 데이터가 파이프라인 전반에 걸쳐 실제 데이터와 명확히 구분되고 표시되어 있는지 확인하십시오. |  2  | D/V |

---

## 참고 문헌

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

