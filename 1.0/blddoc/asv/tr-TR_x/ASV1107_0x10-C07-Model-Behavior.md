# C7 Model Davranışı, Çıktı Kontrolü ve Güvenlik Güvencesi

## Kontrol Amacı

Model çıktıları üretimde yapılandırılmış, güvenilir, güvenli, açıklanabilir ve sürekli izlenmelidir. Bunu yapmak halüsinasyonları, gizlilik ihlallerini, zararlı içeriği ve kontrolsüz eylemleri azaltırken kullanıcı güvenini ve düzenleyici uyumunu artırır.

---

## C7.1 Çıktı Biçimi Zorunluluğu

Katı şemalar, kısıtlı çözümleme ve sonraki doğrulama, bozulmuş veya kötü niyetli içeriğin yayılmadan önce engeller.

|   #   | Açıklama                                                                                                                                                                                      | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.1.1 | Yanıt şemalarının (örneğin JSON Şeması) sistem isteminde sunulduğundan emin olun ve her çıktının otomatik olarak doğrulanmasını sağlayın; uyumsuz çıktılar onarım veya reddedilmeyi tetikler. |   1    | D/V |
| 7.1.2 | Taşma veya prompt enjeksiyonu yan kanallarını önlemek için kısıtlı çözümlenmenin (durdurma belirteçleri, düzenli ifadeler, maksimum token sayısı) etkin olduğundan emin olun.                 |   1    | D/V |
| 7.1.3 | Çıktıları güvenilmez olarak ele alan aşağı akış bileşenlerini doğrulayın ve bunları şemalara karşı ya da enjeksiyona karşı güvenli deserializer'lar ile doğrulayın.                           |   2    | D/V |
| 7.1.4 | Yanlış çıktı olaylarının kaydedildiğini, hız sınırlamasına tabi tutulduğunu ve izleme için görünür kılındığını doğrulayın.                                                                    |   3    |  V  |

---

## C7.2 Halüsinasyon Tespiti ve Hafifletme

Belirsizlik tahmini ve yedek stratejileri uydurulmuş cevapları sınırlıyor.

|   #   | Açıklama                                                                                                                                                                                                | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.2.1 | Token-düzeyindeki log-olasılıklar, topluluk yöntemi kendi kendine tutarlılığı veya ince ayarlı halüsinasyon tespit edicilerinin her yanıt için bir güven skorunu atadığını doğrulayın.                  |   1    | D/V |
| 7.2.2 | Yanıtların, ayarlanabilir bir güven eşik değerinin altında kaldığında geri dönüş iş akışlarını tetiklediğini doğrulayın (örneğin, retrieval-augmented generation, ikincil model veya insan incelemesi). |   1    | D/V |
| 7.2.3 | Halüsinasyon olaylarının kök-neden meta verileriyle etiketlendiğini ve post-mortem ile ince ayar iş akışlarına yönlendirildiğini doğrulayın.                                                            |   2    | D/V |
| 7.2.4 | Önemli model veya bilgi tabanı güncellemelerinin ardından eşiklerin ve dedektörlerin yeniden kalibre edildiğini doğrulayın.                                                                             |   3    | D/V |
| 7.2.5 | Panodaki görselleştirmelerin yanılsama oranlarını takip ettiğini doğrulayın.                                                                                                                            |   3    |  V  |

---

## C7.3 Çıktı Güvenliği ve Gizlilik Filtreleme

Politika filtreleri ve kırmızı takım kapsamı kullanıcıları ve gizli verileri korurlar.

|   #   | Açıklama                                                                                                                                                                                                                                       | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.3.1 | Üretim öncesi ve üretim sonrası sınıflandırıcılarının politikayla uyumlu olarak nefret içeriklerini, taciz içeriklerini, kendine zarar verme içeriklerini, aşırılık yanlısı içerikleri ve cinsel içerikli içerikleri engellediğini doğrulayın. |   1    | D/V |
| 7.3.2 | Her yanıt için PII/PCI tespiti ile otomatik redaksiyonun çalıştığını doğrulayın; ihlaller bir gizlilik olayı olarak bildirilir.                                                                                                                |   1    | D/V |
| 7.3.3 | Gizlilik etiketlerinin (ör. ticari sırlar) modaliteler arasında yayıldığını doğrulayın ve metin, görüntü veya kod gibi alanlarda sızıntıyı önlediğini teyit edin.                                                                              |   2    |  D  |
| 7.3.4 | Filtreyi aşma girişimlerinin veya yüksek riskli sınıflandırmaların ikincil onay veya kullanıcı yeniden kimlik doğrulaması gerektirip gerektirmediğini doğrulayın.                                                                              |   3    | D/V |
| 7.3.5 | Filtreleme eşiklerinin yasal yargı alanlarına ve kullanıcı yaş ve rol bağlamına uygun olduğunu doğrulayın.                                                                                                                                     |   3    | D/V |

---

## C7.4 Çıktı ve Eylem Sınırlandırması

Oran sınırları ve onay kapıları kötüye kullanımını ve aşırı özerkliği önler.

|   #   | Açıklama                                                                                                                                                       | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.4.1 | Kullanıcı başına ve API anahtarı başına kotaların, 429 hatalarında üstel geri çekme ile istekleri, tokenleri ve maliyeti sınırladığını doğrulayın.             |   1    |  D  |
| 7.4.2 | Ayrıcalıklı işlemlerin (dosya yazma, kod çalıştırma, ağ çağrıları) politika tabanlı onay veya insanın dahil olduğu bir süreç gerektirdiğini doğrulayın.        |   1    | D/V |
| 7.4.3 | Çapraz-mod tutarlılık kontrollerinin, aynı istek için üretilen görüntülerin, kodun ve metnin kötü niyetli içerik kaçırılmasına olanak tanımadığını doğrulayın. |   2    | D/V |
| 7.4.4 | Ajan vekalet derinliğinin, özyineleme sınırlarının ve izin verilen araç listelerinin açıkça yapılandırıldığını doğrulayın.                                     |   2    |  D  |
| 7.4.5 | Sınır ihlallerinin yapılandırılmış güvenlik olayları ürettiğini ve bu olayların SIEM'e aktarılması için iletildiğini doğrulayın.                               |   3    |  V  |

---

## C7.5 Çıktı Açıklanabilirliği

Şeffaf sinyaller kullanıcı güvenini artırır ve dahili hata ayıklamayı kolaylaştırır.

|   #   | Açıklama                                                                                                                            | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.5.1 | Risk değerlendirmesi uygun olduğunda kullanıcıya yönelik güven skorlarının veya kısa gerekçe özetlerinin gösterildiğini doğrulayın. |   2    | D/V |
| 7.5.2 | Üretilen açıklamaların hassas sistem istemlerini veya özel verileri ifşa etmediğini doğrulayın.                                     |   2    | D/V |
| 7.5.3 | Sistemin token düzeyindeki log-olasılıklarını veya dikkat haritalarını yakalayıp yetkili inceleme için sakladığını doğrulayın.      |   3    |  D  |
| 7.5.4 | Denetim için, açıklanabilirlik artefaktlarının model sürümleriyle birlikte sürüm kontrollü olduğundan emin olun.                    |   3    |  V  |

---

## C7.6 İzleme Entegrasyonu

Gerçek zamanlı gözlemlenebilirlik, geliştirme ile üretim arasındaki döngüyü kapatır.

|   #   | Açıklama                                                                                                                                          | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.6.1 | Metriklerin (şema ihlalleri, halüsinasyon oranı, toksisite, PII sızıntıları, gecikme, maliyet) merkezi bir izleme platformuna akışını doğrulayın. |   1    |  D  |
| 7.6.2 | Her güvenlik metriği için uyarı eşiklerinin tanımlı olduğundan ve nöbetçi kişiler için yükseltme yollarının bulunduğundan emin olun.              |   1    |  V  |
| 7.6.3 | Panoların çıktı anomalilerini model/sürüm, özellik bayrağı ve üst akış verisi değişiklikleriyle ilişkilendirdiğini doğrulayın.                    |   2    |  V  |
| 7.6.4 | Belgelenmiş bir MLOps iş akışında izleme verilerinin yeniden eğitime, ince ayara veya kural güncellemelerine geri beslenmesini doğrulayın.        |   2    | D/V |
| 7.6.5 | İzleme boru hatlarının sızma testine tabi tutulduğunu ve erişim kontrollü olduğunu doğrulayın; böylece hassas logların sızdırılmasını önleyin.    |   3    |  V  |

---

## 7.7 Üretken Medya Güvenlik Önlemleri

Yapay zeka sistemlerinin yasa dışı, zararlı veya yetkisiz medya içeriği üretmesini engellemek için politika kısıtlarının uygulanması, çıktı doğrulaması ve izlenebilirlik yoluyla.

|   #   | Açıklama                                                                                                                                                                                                                                              | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.7.1 | Sistem istemlerinin ve kullanıcı talimatlarının açıkça yasadışı, zararlı veya rızası alınmamış derin sahte medya üretimini yasakladığını doğrulayın (örneğin, görüntü, video, ses).                                                                   |   1    | D/V |
| 7.7.2 | İsteklerin, taklit üretimine, cinsel içerikli derin sahte videolar üretmeye veya rızası olmadan gerçek kişileri tasvir eden medyayı üretmeye yönelik girişimlere karşı filtrelendiğini doğrulayın.                                                    |   2    | D/V |
| 7.7.3 | Sistemin izinsiz çoğaltmayı önlemek için algısal özetlemeyi (perceptual hashing), filigran tespitini veya parmak izi çıkarımını kullanıp kullanmadığını doğrulayın.                                                                                   |   2    |  V  |
| 7.7.4 | Üretilen tüm medyanın kriptografik olarak imzalanmış, filigranlı veya tahrife karşı dayanıklı köken meta verileriyle gömülü olduğundan emin olun; bu, sonraki izlenebilirlik için gereklidir.                                                         |   3    | D/V |
| 7.7.5 | Atlatma girişimlerinin (örneğin, istemleri karıştırma, argo, karşı saldırgan ifadeler) tespit edildiğini, kaydedildiğini ve hız sınırlamasına tabi tutulduğunu doğrulayın; tekrarlanan kötüye kullanımın izleme sistemlerine bildirilmesini sağlayın. |   3    |  V  |

## Kaynaklar

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

