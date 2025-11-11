# C8 메모리, 임베딩 및 벡터 데이터베이스 보안

## 제어 목표

임베딩과 벡터 저장소는 현대 AI 시스템의 "실시간 메모리" 역할을 하며, 사용자 제공 데이터를 지속적으로 수용하고 검색 증강 생성(RAG)을 통해 모델 컨텍스트에 다시 반영합니다. 관리되지 않으면 이 메모리는 PII를 유출하거나 동의를 위반하며, 원본 텍스트를 재구성하는 데 악용될 수 있습니다. 이 통제 집합의 목적은 메모리 파이프라인과 벡터 데이터베이스를 강화하여 접근 권한을 최소 권한으로 제한하고, 임베딩이 프라이버시를 보호하며, 저장된 벡터가 만료되거나 요청 시 폐기될 수 있도록 하며, 사용자별 메모리가 다른 사용자의 프롬프트나 완성에 영향을 미치지 않도록 하는 것입니다.

---

## C8.1 메모리 및 RAG 인덱스에 대한 접근 제어

모든 벡터 컬렉션에 대해 세분화된 접근 제어를 적용하세요.

|   #   | 설명                                                                          | 수준  | 역할  |
| :---: | --------------------------------------------------------------------------- | :-: | :-: |
| 8.1.1 | 행/네임스페이스 수준의 접근 제어 규칙이 테넌트, 컬렉션 또는 문서 태그별로 삽입, 삭제 및 조회 작업을 제한하는지 검증하세요.     |  1  | D/V |
| 8.1.2 | API 키 또는 JWT가 범위가 지정된 클레임(예: 컬렉션 ID, 동작 동사)을 포함하고 있으며 최소 분기별로 교체되는지 확인하십시오. |  1  | D/V |
| 8.1.3 | 권한 상승 시도(예: 교차 네임스페이스 유사성 쿼리)가 탐지되어 5분 이내에 SIEM에 기록되는지 확인하십시오.              |  2  | D/V |
| 8.1.4 | 벡터 DB가 감사 로그에 주체 식별자, 작업, 벡터 ID/네임스페이스, 유사도 임계값 및 결과 수를 기록하는지 확인하십시오.       |  2  | D/V |
| 8.1.5 | 엔진이 업그레이드되거나 인덱스 샤딩 규칙이 변경될 때마다 액세스 결정이 우회 결함에 대해 테스트되는지 검증하십시오.            |  3  |  V  |

---

## C8.2 임베딩 정제 및 검증

벡터화 전에 PII(개인 식별 정보)를 사전 검사하고, 삭제하거나 가명 처리하며, 선택적으로 임베딩 후처리를 통해 잔여 신호를 제거합니다.

|   #   | 설명                                                                                    | 수준  | 역할  |
| :---: | ------------------------------------------------------------------------------------- | :-: | :-: |
| 8.2.1 | PII 및 규제 데이터를 자동 분류기를 통해 감지하고, 임베딩 전 마스킹, 토큰화 또는 삭제하는지 확인하십시오.                        |  1  | D/V |
| 8.2.2 | 임베딩 파이프라인이 인덱스를 오염시킬 수 있는 실행 가능한 코드 또는 비UTF-8 아티팩트를 포함하는 입력을 거부하거나 격리하는지 확인하십시오.      |  1  |  D  |
| 8.2.3 | 구성 가능한 임계값 이하로 알려진 PII 토큰과의 거리가 떨어지는 문장 임베딩에 대해 지역 또는 메트릭 차분 프라이버시 세정이 적용되었는지 확인하십시오. |  2  | D/V |
| 8.2.4 | 정제 효능(예: PII 삭제의 재현율, 의미 변화)이 벤치마크 말뭉치를 기준으로 최소 반기마다 검증되는지 확인하십시오.                    |  2  |  V  |
| 8.2.5 | 정제 구성(sanitization configs)이 버전 관리되고 변경 사항이 동료 검토(peer review)를 거치는지 확인하십시오.          |  3  | D/V |

---

## C8.3 메모리 만료, 폐기 및 삭제

GDPR의 "잊혀질 권리" 및 유사한 법률은 신속한 삭제를 요구하므로, 벡터 저장소는 취소된 벡터가 복구되거나 재인덱싱되지 않도록 TTL, 하드 삭제, 그리고 톰스톤 방식을 지원해야 합니다.

|   #   | 설명                                                                                                            | 수준  | 역할  |
| :---: | ------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 8.3.1 | 모든 벡터 및 메타데이터 기록이 TTL 또는 자동 정리 작업에서 준수되는 명시적 보존 라벨을 가지고 있는지 확인하십시오.                                           |  1  | D/V |
| 8.3.2 | 사용자가 시작한 삭제 요청이 30일 이내에 벡터, 메타데이터, 캐시 복사본 및 파생 인덱스를 완전히 삭제하는지 확인합니다.                                          |  1  | D/V |
| 8.3.3 | 하드웨어가 이를 지원하는 경우 논리적 삭제가 스토리지 블록의 암호화 삭제(cryptographic shredding)를 따르는지, 그렇지 않으면 키-볼트 키 파괴에 의해 이루어지는지 확인하십시오. |  2  |  D  |
| 8.3.4 | 만료된 벡터가 만료 후 500ms 이내에 최근접 이웃 검색 결과에서 제외되는지 확인하십시오.                                                           |  3  | D/V |

---

## C8.4 임베딩 역전 및 누출 방지

최근 방어 기법인 노이즈 중첩, 투영 네트워크, 개인정보 뉴런 교란, 애플리케이션 계층 암호화는 토큰 수준 역전율을 5% 이하로 줄일 수 있습니다.

|   #   | 설명                                                                                             | 수준  | 역할  |
| :---: | ---------------------------------------------------------------------------------------------- | :-: | :-: |
| 8.4.1 | 역전 공격, 멤버십 공격 및 속성 추론 공격을 포함하는 공식 위협 모델이 존재하며 매년 검토되는지 확인합니다.                                  |  1  |  V  |
| 8.4.2 | 애플리케이션 계층 암호화 또는 검색 가능한 암호화가 인프라 관리자나 클라우드 직원에 의한 벡터 직접 읽기로부터 벡터를 보호하는지 확인하십시오.                |  2  | D/V |
| 8.4.3 | 방어 매개변수(ε for DP, 노이즈 σ, 투영 랭크 k)가 개인정보 보호 ≥ 99 % 토큰 보호와 유틸리티 ≤ 3 % 정확도 손실을 균형 있게 유지하는지 검증합니다. |  3  |  V  |
| 8.4.4 | 모델 업데이트의 릴리스 게이트에 반전 저항성 지표가 포함되어 있는지 확인하고, 회귀 예산이 정의되어 있는지 검증하세요.                             |  3  | D/V |

---

## C8.5 사용자별 메모리에 대한 범위 집행

테넌트 간 누출은 여전히 주요 RAG 위험 요소입니다: 부적절하게 필터링된 유사도 쿼리는 다른 고객의 비공개 문서를 노출시킬 수 있습니다.

|   #   | 설명                                                                     | 수준  | 역할  |
| :---: | ---------------------------------------------------------------------- | :-: | :-: |
| 8.5.1 | 모든 검색 쿼리가 LLM 프롬프트에 전달되기 전에 테넌트/사용자 ID로 사후 필터링되는지 확인하십시오.              |  1  | D/V |
| 8.5.2 | 벡터가 범위 간에 충돌하지 않도록 사용자 또는 테넌트별로 컬렉션 이름 또는 네임스페이스 ID가 솔팅되어 있는지 확인하십시오.  |  1  |  D  |
| 8.5.3 | 호출자의 범위를 벗어나지만 구성 가능한 거리 임계값을 초과하는 유사성 결과가 폐기되고 보안 경고를 발생시키는지 확인하십시오.  |  2  | D/V |
| 8.5.4 | 멀티 테넌트 부하 테스트가 범위 외 문서를 검색하려는 적대적 쿼리를 시뮬레이션하고 누출이 전혀 없음을 입증하는지 검증하십시오. |  2  |  V  |
| 8.5.5 | 암호화 키가 각 테넌트별로 분리되어 있는지 확인하여, 물리적 저장소가 공유되더라도 암호학적 격리가 보장되도록 합니다.      |  3  | D/V |

---

## C8.6 고급 메모리 시스템 보안

에피소드 메모리, 시맨틱 메모리, 워킹 메모리를 포함한 정교한 메모리 아키텍처에 대한 특정 분리 및 검증 요구 사항을 갖춘 보안 제어.

|   #   | 설명                                                                                                                    | 수준  | 역할  |
| :---: | --------------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 8.6.1 | 서로 다른 메모리 유형(에피소드 메모리, 의미 메모리, 작업 메모리)이 역할 기반 접근 제어, 별도의 암호화 키, 각 메모리 유형별 문서화된 접근 패턴을 통해 격리된 보안 컨텍스트를 가지고 있는지 확인하십시오. |  1  | D/V |
| 8.6.2 | 메모리 통합 과정에 콘텐츠 정화, 출처 검증, 무결성 검사 등을 통해 악성 메모리 주입을 방지하는 보안 검증이 포함되어 있는지 확인하십시오.                                        |  2  | D/V |
| 8.6.3 | 메모리 검색 쿼리가 쿼리 패턴 분석, 접근 제어 시행 및 결과 필터링을 통해 무단 정보 추출을 방지하도록 검증되고 정제되는지 확인하십시오.                                         |  2  | D/V |
| 8.6.4 | 키 삭제, 다중 덮어쓰기, 또는 검증 인증서가 포함된 하드웨어 기반 보안 삭제를 사용하여 암호 삭제 보증과 함께 민감한 정보를 안전하게 삭제하는 메모리 삭제 메커니즘을 검증하십시오.                 |  3  | D/V |
| 8.6.5 | 메모리 시스템 무결성이 체크섬, 감사 로그 및 정상 작동 범위를 벗어난 메모리 내용 변경 시 자동 경고를 통해 무단 수정 또는 손상 여부를 지속적으로 모니터링하는지 확인합니다.                    |  3  | D/V |

---

## 참고 문헌

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

