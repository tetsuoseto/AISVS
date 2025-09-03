# C8 Memory, 임베딩 및 벡터 데이터베이스 보안

## 통제 목표

임베딩과 벡터 저장소는 현대 AI 시스템의 '라이브 메모리' 역할을 하며, 사용자로부터 제공된 데이터를 지속적으로 수용하고 이를 검색 보강 생성(RAG)을 통해 모델 맥락에 다시 반영합니다. 관리되지 않으면 이 메모리는 PII를 누설하거나 동의를 침해하거나 원문 텍스트를 재구성하기 위해 악용될 수 있습니다. 이 제어 계열의 목표는 메모리 파이프라인과 벡터 데이터베이스를 강화하여 접근을 최소권한으로 제한하고, 임베딩이 프라이버시를 보존하며, 저장된 벡터가 만료되거나 필요 시 해지될 수 있도록 하고, 사용자별 메모리가 다른 사용자의 프롬프트나 생성 결과를 절대 오염시키지 않도록 하는 것입니다.

---

## C8.1 메모리 및 RAG 지표에 대한 접근 제어

각 벡터 컬렉션마다 세밀한 접근 제어를 적용한다.

|   #   | 설명                                                                             | 레벨  | 역할  |
| :---: | ------------------------------------------------------------------------------ | :-: | :-: |
| 8.1.1 | 행/네임스페이스 수준의 접근 제어 규칙이 각 테넌트, 컬렉션 또는 문서 태그에 대해 삽입, 삭제 및 질의 연산을 제한하는지 확인합니다.    |  1  | D/V |
| 8.1.2 | API 키 또는 JWT가 범위가 지정된 클레임(예: 컬렉션 ID, 액션 동사)을 포함하고 있으며, 최소한 매 분기마다 회전되는지 확인합니다. |  1  | D/V |
| 8.1.3 | 권한-상승 시도(예: 네임스페이스-간 유사도 쿼리)가 5분 이내에 탐지되고 SIEM에 로깅되는지 확인하십시오.                  |  2  | D/V |
| 8.1.4 | 벡터 DB의 감사 로그에 주체 식별자, 작업, 벡터 ID/네임스페이스, 유사도 임계값, 그리고 결과 수가 기록되는지 확인합니다.        |  2  | D/V |
| 8.1.5 | 엔진이 업그레이드될 때마다 또는 인덱스 샤딩 규칙이 변경될 때 접근 제어 결정이 우회 취약점에 대해 테스트되는지 확인하십시오.         |  3  |  V  |

---

## C8.2 임베딩 정제 및 검증

텍스트에서 PII(개인식별정보)를 사전 선별하고, 벡터화하기 전에 이를 삭제하거나 가명화하며, 필요 시 잔류 신호를 제거하기 위해 임베딩을 후처리합니다.

|   #   | 설명                                                                                                  | 레벨  | 역할  |
| :---: | --------------------------------------------------------------------------------------------------- | :-: | :-: |
| 8.2.1 | PII 및 규제 데이터가 자동 분류기를 통해 탐지되고, 임베딩 이전에 마스킹되거나 토큰화되거나 드롭되는지 확인하십시오.                                  |  1  | D/V |
| 8.2.2 | 임베딩 파이프라인이 실행 가능한 코드나 UTF-8이 아닌 아티팩트를 포함하는 입력을 거부하거나 격리하는지 확인합니다.                                   |  1  |  D  |
| 8.2.3 | 로컬 또는 메트릭 차등 프라이버시 비식별화가 문장 임베딩에 적용되며, 이 임베딩이 알려진 PII(개인 식별 정보) 토큰과의 거리가 구성 가능한 임계값 아래로 떨어지는지 확인한다. |  2  | D/V |
| 8.2.4 | 비식별화 성능(예: PII 비식별화의 재현율, 시맨틱 드리프트)이 벤치마크 말뭉치에 대해 최소 반년마다 검증되는지 확인한다.                               |  2  |  V  |
| 8.2.5 | 정화 설정이 버전 관리되고 변경 사항이 동료 검토를 거치는지 확인하십시오.                                                           |  3  | D/V |

---

## C8.3 메모리 만료, 해지 및 삭제

GDPR의 "잊혀질 권리" 및 이와 유사한 법률은 시의적절한 삭제를 요구하므로, 벡터 저장소는 TTL, 하드 삭제, 그리고 덤스톤 처리를 지원해야 하며, 취소된 벡터가 복구되거나 재인덱싱될 수 없도록 해야 한다.

|   #   | 설명                                                                                  | 레벨  | 역할  |
| :---: | ----------------------------------------------------------------------------------- | :-: | :-: |
| 8.3.1 | 모든 벡터 및 메타데이터 레코드가 TTL 또는 자동 정리 작업에 의해 준수되는 명시적 보존 라벨을 보유하고 있는지 확인합니다.              |  1  | D/V |
| 8.3.2 | 사용자 주도 삭제 요청이 벡터, 메타데이터, 캐시 복사본 및 파생 인덱스를 30일 이내에 완전히 삭제하는지 확인한다.                   |  1  | D/V |
| 8.3.3 | 하드웨어가 이를 지원하는 경우 논리 삭제가 저장 블록의 암호학적 파쇄로 이어지는지 확인하고, 그렇지 않으면 키 볼트의 키 파괴로 이어지는지 확인한다. |  2  |  D  |
| 8.3.4 | 만료된 벡터들이 만료 후 < 500 ms 이내에 최근접 이웃 탐색 결과에서 제외되는지 확인합니다.                              |  3  | D/V |

---

## C8.4 임베딩 역전 및 누출 방지

최근 방어 기법—노이즈 중첩, 투영 네트워크, 프라이버시-뉴런 섭동, 그리고 응용-계층 암호화—은 토큰 수준의 역공률을 5% 미만으로 낮출 수 있다.

|   #   | 설명                                                                                     | 레벨  | 역할  |
| :---: | -------------------------------------------------------------------------------------- | :-: | :-: |
| 8.4.1 | 역추론 공격, 멤버십 추론 공격 및 속성 추론 공격을 포괄하는 정식 위협 모델이 존재하고 매년 검토되는지 확인합니다.                      |  1  |  V  |
| 8.4.2 | 애플리케이션 계층 암호화 또는 검색 가능한 암호화가 인프라 관리자나 클라우드 직원의 직접 열람으로부터 벡터를 보호하는지 확인하십시오.             |  2  | D/V |
| 8.4.3 | 방어 매개변수( DP용 ε, 노이즈 σ, 투영 랭크 k )가 프라이버시를 ≥ 99 %로 보호하고, 유용성을 ≤ 3 %의 정확도 손실로 유지하는지 확인한다. |  3  |  V  |
| 8.4.4 | 역전 공격에 대한 내성 지표가 모델 업데이트를 위한 릴리스 게이트의 일부인지 확인하고, 회귀 예산이 정의되어 있는지 확인합니다.                |  3  | D/V |

---

## C8.5 사용자별 메모리 범위 적용

다중 테넌트 간 누출은 여전히 주요 RAG 위험입니다: 부적절하게 필터링된 유사도 쿼리가 다른 고객의 비공개 문서를 노출시킬 수 있습니다.

|   #   | 설명                                                                            | 레벨  | 역할  |
| :---: | ----------------------------------------------------------------------------- | :-: | :-: |
| 8.5.1 | 모든 검색 쿼리가 LLM 프롬프트로 전달되기 전에 테넌트 ID와 사용자 ID로 후처리 필터링되었는지 확인하십시오.               |  1  | D/V |
| 8.5.2 | 컬렉션 이름 또는 네임스페이스 ID가 사용자별 또는 테넌트별로 솔트되도록 확인하여 벡터가 스코프 간에 충돌하지 않도록 한다.         |  1  |  D  |
| 8.5.3 | 구성 가능한 거리 임계치를 초과하고 호출자의 범위를 벗어난 유사도 결과를 버리고 보안 경보를 발령하는지 확인합니다.              |  2  | D/V |
| 8.5.4 | 다중 테넌트 스트레스 테스트가 범위를 벗어난 문서를 검색하려는 적대적 쿼리를 시뮬레이션하고, 정보 누출이 전혀 없음을 입증하는지 확인한다. |  2  |  V  |
| 8.5.5 | 테넌트별로 암호화 키가 구분되어 있는지 확인하고, 물리적 저장소가 공유되더라도 암호학적 격리가 유지되도록 보장합니다.             |  3  | D/V |

---

## C8.6 고급 메모리 시스템 보안

에피소딕 기억, 시맨틱 기억 및 작업 기억을 포함하는 정교한 메모리 아키텍처를 위한 보안 제어와 특정 격리 및 검증 요구사항.

|   #   | 설명                                                                                                                          | 레벨  | 역할  |
| :---: | --------------------------------------------------------------------------------------------------------------------------- | :-: | :-: |
| 8.6.1 | 다양한 메모리 유형(에피소딕 메모리, 시맨틱 메모리, 워킹 메모리)이 서로 격리된 보안 컨텍스트를 가지며, 역할 기반 접근 제어, 별도 암호화 키, 그리고 각 메모리 유형에 대해 문서화된 접근 패턴을 갖는지 확인하십시오. |  1  | D/V |
| 8.6.2 | 저장하기 전에 콘텐츠 정화, 출처 검증 및 무결성 검사를 통해 악성 메모리 주입을 방지하기 위한 보안 검증이 메모리 통합 프로세스에 포함되어 있는지 확인하십시오.                                  |  2  | D/V |
| 8.6.3 | 메모리 검색 쿼리가 유효성 검사되고 정제되었는지 확인하여 쿼리 패턴 분석, 접근 제어 시행, 그리고 결과 필터링을 통해 권한이 없는 정보의 추출을 방지합니다.                                    |  2  | D/V |
| 8.6.4 | 메모리 보안 소거 메커니즘이 암호학적 소거 보장을 제공하면서 키 삭제, 다중 패스 덮어쓰기 또는 검증 인증서가 포함된 하드웨어 기반 보안 소거를 사용하여 민감한 정보를 안전하게 삭제하는지 검증한다.              |  3  | D/V |
| 8.6.5 | 메모리 시스템의 무결성이 무단 수정이나 손상에 대해 체크섬, 감사 로그, 그리고 메모리 내용이 정상 작동 범위를 벗어나 변경될 때 자동 경고를 통해 지속적으로 모니터링되고 있는지 확인한다.                   |  3  | D/V |

---

## 참고문헌

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

