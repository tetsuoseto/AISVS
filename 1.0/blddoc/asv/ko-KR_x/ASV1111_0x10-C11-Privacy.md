# 11 개인정보 보호 및 개인 데이터 관리

## 통제 목표

수집, 학습, 추론 및 사고 대응 등 AI 전체 라이프사이클에서 엄격한 개인정보 보호를 유지하여, 개인 데이터가 명확한 동의, 최소한의 필요 범위, 증명 가능한 삭제 및 공식적인 개인정보 보호 보장 하에만 처리되도록 합니다.

---

## 11.1 익명화 및 데이터 최소화

|   #    | 설명                                                             | 레벨  | 역할  |
| :----: | -------------------------------------------------------------- | :-: | :-: |
| 11.1.1 | 직접 식별자와 준식별자가 제거되거나 해시되었는지 확인하십시오.                             |  1  | D/V |
| 11.1.2 | 자동화된 감사가 k-익명성/l-다양성을 측정하고 임계값이 정책 이하로 떨어질 때 경고하는지 확인하십시오.     |  2  | D/V |
| 11.1.3 | 모델 특성 중요도 보고서가 ε = 0.01 상호 정보량을 초과하는 식별자 누출이 없음을 증명하는지 확인하십시오. |  2  |  V  |
| 11.1.4 | 공식 증명이나 합성 데이터 인증이 연계 공격에도 불구하고 재식별 위험이 ≤ 0.05임을 확인하십시오.       |  3  |  V  |

---

## 11.2 잊혀질 권리 및 삭제 집행

|   #    | 설명                                                                                    | 레벨  | 역할  |
| :----: | ------------------------------------------------------------------------------------- | :-: | :-: |
| 11.2.1 | 데이터 주체 삭제 요청이 서비스 수준 계약의 30일 미만 기간 내에 원시 데이터셋, 체크포인트, 임베딩, 로그 및 백업에 전파되는지 확인하십시오.     |  1  | D/V |
| 11.2.2 | "머신 언러닝(machine-unlearning)" 절차가 물리적으로 재학습하거나 인증된 언러닝 알고리즘을 사용하여 근사 제거를 수행하는지 확인하십시오. |  2  |  D  |
| 11.2.3 | 섀도우 모델 평가가 언러닝 후 잊혀진 기록들이 출력의 1% 미만에 영향을 미친다는 것을 증명하는지 확인하십시오.                        |  2  |  V  |
| 11.2.4 | 삭제 이벤트가 변경 불가능하게 기록되고 규제 당국이 감 audit할 수 있도록 확인하십시오.                                   |  3  |  V  |

---

## 11.3 차등 프라이버시 보호장치

|   #    | 설명                                                       | 레벨  | 역할  |
| :----: | -------------------------------------------------------- | :-: | :-: |
| 11.3.1 | 누적된 ε가 정책 임계값을 초과할 때 프라이버시 손실 계산 대시보드가 알림을 제공하는지 확인하십시오. |  2  | D/V |
| 11.3.2 | 블랙박스 프라이버시 감사가 선언된 값의 10% 이내에서 ε̂를 추정하는지 검증합니다.          |  2  |  V  |
| 11.3.3 | 형식화된 증명이 모든 사후 학습 미세조정 및 임베딩을 포괄하는지 확인하십시오.              |  3  |  V  |

---

## 11.4 목적 제한 및 범위 확장 방지

|   #    | 설명                                                                | 레벨  | 역할  |
| :----: | ----------------------------------------------------------------- | :-: | :-: |
| 11.4.1 | 모든 데이터셋과 모델 체크포인트가 원래 동의서에 맞춰 기계가 읽을 수 있는 목적 태그를 포함하고 있는지 확인하십시오. |  1  |  D  |
| 11.4.2 | 런타임 모니터가 선언된 목적과 일치하지 않는 쿼리를 감지하고 소프트 거부를 트리거하는지 검증합니다.           |  1  | D/V |
| 11.4.3 | 정책-코드 게이트가 DPIA 검토 없이 새로운 도메인으로 모델의 재배포를 차단하는지 확인하세요.             |  3  |  D  |
| 11.4.4 | 형식적인 추적성 증거가 모든 개인정보 생명주기가 동의된 범위 내에 있음을 보여주는지 확인합니다.             |  3  |  V  |

---

## 11.5 동의 관리 및 합법적 근거 추적

|   #    | 설명                                                         | 레벨  | 역할  |
| :----: | ---------------------------------------------------------- | :-: | :-: |
| 11.5.1 | 동의 관리 플랫폼(CMP)이 데이터 주체별로 옵트인 상태, 목적 및 보존 기간을 기록하는지 확인하십시오. |  1  | D/V |
| 11.5.2 | API가 동의 토큰을 노출하는지 확인하십시오; 모델은 추론 전에 토큰 범위를 검증해야 합니다.       |  2  |  D  |
| 11.5.3 | 거부되거나 철회된 동의가 24시간 이내에 처리 파이프라인을 중단하는지 확인하십시오.             |  2  | D/V |

---

## 11.6 프라이버시 제어가 적용된 연합 학습

|   #    | 설명                                                      | 레벨  | 역할  |
| :----: | ------------------------------------------------------- | :-: | :-: |
| 11.6.1 | 클라이언트 업데이트가 집계 전에 지역 차등 개인 정보 보호 노이즈 추가를 사용하는지 확인하십시오.  |  1  |  D  |
| 11.6.2 | 훈련 지표가 차등 프라이버시를 준수하며 단일 클라이언트의 손실을 절대 노출하지 않는지 확인하십시오. |  2  | D/V |
| 11.6.3 | 중독 방지 집계(예: Krum/Trimmed-Mean)가 활성화되어 있는지 확인하십시오.       |  2  |  V  |
| 11.6.4 | 형식적인 증명이 전체 ε 예산이 5 미만의 유틸리티 손실을 보임을 입증하는지 확인하십시오.      |  3  |  V  |

---

### 참고 문헌

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

