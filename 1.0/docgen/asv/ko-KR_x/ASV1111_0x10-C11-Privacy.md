# 11 개인정보 보호 및 개인 데이터 관리

## 제어 목표

개인 데이터가 명확한 동의, 최소한의 필요한 범위, 입증 가능한 삭제 및 공식적인 개인정보 보호 보장을 통해서만 처리되도록 AI 수명 주기 전반—수집, 학습, 추론, 사고 대응—에 걸쳐 엄격한 개인정보 보호를 유지하십시오.

---

## 11.1 익명화 및 데이터 최소화

|   #    | 설명                                                             | 레벨  | 역할  |
| :----: | -------------------------------------------------------------- | :-: | :-: |
| 11.1.1 | 직접 및 준식별자가 제거되거나 해시 처리되었는지 확인하십시오.                             |  1  | D/V |
| 11.1.2 | 자동화된 감사가 k-익명성/l-다양성을 측정하고 임계값이 정책 아래로 떨어질 때 경고하는지 확인합니다.      |  2  | D/V |
| 11.1.3 | 모델 특성 중요도 보고서가 ε = 0.01 상호 정보량을 초과하는 식별자 누출이 없음을 증명하는지 확인하십시오. |  2  |  V  |
| 11.1.4 | 형식적 증명 또는 합성 데이터 인증이 연계 공격 하에서도 재식별 위험이 ≤ 0.05임을 확인하십시오.       |  3  |  V  |

---

## 11.2 잊힐 권리 및 삭제 집행

|   #    | 설명                                                                                 | 레벨  | 역할  |
| :----: | ---------------------------------------------------------------------------------- | :-: | :-: |
| 11.2.1 | 데이터 주체 삭제 요청이 원시 데이터셋, 체크포인트, 임베딩, 로그 및 백업에 서비스 수준 계약 내 30일 미만으로 전파되는지 확인하십시오.     |  1  | D/V |
| 11.2.2 | "머신 언러닝(machine-unlearning)" 루틴이 인증된 언러닝 알고리즘을 사용하여 실제로 재학습하거나 근사적으로 제거하는지 검증하십시오. |  2  |  D  |
| 11.2.3 | 섀도우 모델 평가가 언러닝 후 삭제된 기록이 출력에 미치는 영향이 1% 미만임을 증명하는지 확인하십시오.                         |  2  |  V  |
| 11.2.4 | 삭제 이벤트가 변경 불가능하게 기록되고 규제 기관이 감 auditor할 수 있도록 확인하십시오.                              |  3  |  V  |

---

## 11.3 차분 개인정보 보호 장치

|   #    | 설명                                                 | 레벨  | 역할  |
| :----: | -------------------------------------------------- | :-: | :-: |
| 11.3.1 | 누적 ε가 정책 임계값을 초과할 때 개인정보 손실 계정 대시보드가 경고하는지 확인하십시오. |  2  | D/V |
| 11.3.2 | 블랙박스 프라이버시 감사가 선언된 값의 10% 이내로 ε̂를 추정하는지 확인하십시오.    |  2  |  V  |
| 11.3.3 | 형식 증명이 모든 사후 훈련 미세 조정 및 임베딩을 포함하는지 확인하십시오.         |  3  |  V  |

---

## 11.4 목적 제한 및 범위 확장 방지

|   #    | 설명                                                               | 레벨  | 역할  |
| :----: | ---------------------------------------------------------------- | :-: | :-: |
| 11.4.1 | 모든 데이터셋과 모델 체크포인트가 원래의 동의에 맞춰 기계가 읽을 수 있는 목적 태그를 포함하고 있는지 확인하세요. |  1  |  D  |
| 11.4.2 | 런타임 모니터가 선언된 목적과 일치하지 않는 쿼리를 감지하고 소프트 거부를 트리거하는지 검증하십시오.         |  1  | D/V |
| 11.4.3 | 정책을 코드로 구현한 게이트가 DPIA 검토 없이 모델을 새로운 도메인에 재배포하는 것을 차단하는지 확인하십시오.  |  3  |  D  |
| 11.4.4 | 형식적인 추적 가능성 증명이 모든 개인 데이터 수명 주기가 동의된 범위 내에 유지되는지 확인하십시오.         |  3  |  V  |

---

## 11.5 동의 관리 및 적법한 근거 추적

|   #    | 설명                                                         | 레벨  | 역할  |
| :----: | ---------------------------------------------------------- | :-: | :-: |
| 11.5.1 | 동의 관리 플랫폼(CMP)이 데이터 주체별로 옵트인 상태, 목적 및 보유 기간을 기록하는지 확인하십시오. |  1  | D/V |
| 11.5.2 | API가 동의 토큰을 노출하는지 확인하십시오; 모델은 추론 전에 토큰 범위를 검증해야 합니다.       |  2  |  D  |
| 11.5.3 | 거부되거나 철회된 동의가 24시간 이내에 처리 파이프라인을 중단하는지 확인하십시오.             |  2  | D/V |

---

## 11.6 개인 정보 보호 제어가 포함된 연합 학습

|   #    | 설명                                                     | 레벨  | 역할  |
| :----: | ------------------------------------------------------ | :-: | :-: |
| 11.6.1 | 클라이언트 업데이트가 집계 전에 로컬 차등 개인 정보 보호 노이즈 추가를 사용하는지 확인합니다.  |  1  |  D  |
| 11.6.2 | 훈련 지표가 차등 프라이버시를 보장하며 단일 클라이언트 손실을 절대 공개하지 않는지 확인하십시오. |  2  | D/V |
| 11.6.3 | 포이즈닝 저항 집계(예: Krum/Trimmed-Mean)가 활성화되어 있는지 확인하십시오.    |  2  |  V  |
| 11.6.4 | 형식적인 증명이 전체 ε 예산을 5 미만의 유틸리티 손실로 보여주는지 확인하십시오.         |  3  |  V  |

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

