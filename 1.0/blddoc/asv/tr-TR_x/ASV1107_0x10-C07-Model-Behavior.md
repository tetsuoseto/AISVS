# C7 Model Davranışı, Çıktı Kontrolü ve Güvenlik Garantisi

## Kontrol Amacı

Model çıktıları yapılandırılmış, güvenilir, güvenli, açıklanabilir olmalı ve üretimde sürekli izlenmelidir. Bunu yapmak, hayal ürünlerini, gizlilik sızıntılarını, zararlı içeriği ve kontrolsüz eylemleri azaltırken, kullanıcı güvenini ve düzenleyici uyumu artırır.

---

## C7.1 Çıktı Formatı Uygulaması

Katı şemalar, kısıtlı çözümleme ve sonraki doğrulama, bozuk veya kötü amaçlı içeriğin yayılmasını önler.

|   #   | Açıklama                                                                                                                                                                                                       | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.1.1 | Yanıt şemalarının (örneğin, JSON Şeması) sistem isteminde sağlandığını ve her çıktının otomatik olarak doğrulandığını; uygun olmayan çıktılar için düzeltme veya reddetme işleminin tetiklendiğini doğrulayın. |   1    | D/V |
| 7.1.2 | Taşma veya istem enjeksiyonu yan kanal saldırılarını önlemek için kısıtlanmış çözümleme (durdurma tokenleri, regex, maksimum token sayısı) etkinleştirildiğini doğrulayın.                                     |   1    | D/V |
| 7.1.3 | Alt bileşenlerin çıktıları güvensiz olarak değerlendirip bunları şemalara veya enjeksiyona karşı güvenli serileştirme çözümleyicilerine karşı doğruladığını teyit edin.                                        |   2    | D/V |
| 7.1.4 | Yanlış çıktı olaylarının kaydedildiğini, hız sınırlamasına tabi tutulduğunu ve izlemeye yansıtıldığını doğrulayın.                                                                                             |   3    |  V  |

---

## C7.2 Halüsinasyon Tespiti ve Azaltılması

Belirsizlik tahmini ve yedekleme stratejileri, uydurulmuş cevapları sınırlar.

|   #   | Açıklama                                                                                                                                                                                              | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.2.1 | Token düzeyinde log-olasılıkların, toplu kendi-tutarlılığın veya ince ayarlı halüsinasyon tespitçilerinin her yanıta bir güven skoru atadığını doğrulayın.                                            |   1    | D/V |
| 7.2.2 | Yanıtların, yapılandırılabilir bir güven eşiğinin altında olması durumunda yedek iş akışlarını (örneğin, geri getirme destekli üretim, ikincil model veya insan incelemesi) tetiklediğini doğrulayın. |   1    | D/V |
| 7.2.3 | Halüsinasyon olaylarının kök neden meta verisiyle etiketlendiğini ve ölüm sonrası analiz ile ince ayar iş akışlarına aktarıldığını doğrulayın.                                                        |   2    | D/V |
| 7.2.4 | Önemli model veya bilgi tabanı güncellemelerinden sonra eşik değerlerin ve dedektörlerin yeniden kalibrasyonunun yapıldığını doğrulayın.                                                              |   3    | D/V |
| 7.2.5 | Gösterge paneli görselleştirmelerinin halüsinasyon oranlarını takip ettiğini doğrulayın.                                                                                                              |   3    |  V  |

---

## C7.3 Çıktı Güvenliği ve Gizlilik Filtreleme

Politika filtreleri ve kırmızı takım kapsamı kullanıcıları ve gizli verileri korur.

|   #   | Açıklama                                                                                                                                                                               | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.3.1 | Politikaya uygun olarak nefret, taciz, kendine zarar verme, aşırılıkçı ve cinsel içerikli içeriklerin ön ve sonrası oluşturma sınıflandırıcıları tarafından engellendiğini doğrulayın. |   1    | D/V |
| 7.3.2 | Her yanıtta Kişisel Tanımlanabilir Bilgi (PII)/Ödeme Kartı Endüstrisi (PCI) tespiti ve otomatik sansürün çalıştığını doğrulayın; ihlaller bir gizlilik olayı tetikler.                 |   1    | D/V |
| 7.3.3 | Gizlilik etiketlerinin (örneğin, ticari sırlar) metin, görüntü veya kodda sızıntıyı önlemek için modlar arasında yayılmasını doğrulayın.                                               |   2    |  D  |
| 7.3.4 | Filtre atlama girişimlerinin veya yüksek riskli sınıflandırmaların ikinci onay veya kullanıcı yeniden kimlik doğrulaması gerektirdiğini doğrulayın.                                    |   3    | D/V |
| 7.3.5 | Filtreleme eşiklerinin yasal yargı bölgeleri ve kullanıcı yaşı/rolu bağlamını yansıttığını doğrulayın.                                                                                 |   3    | D/V |

---

## C7.4 Çıktı ve Eylem Sınırlaması

Oran sınırları ve onay kapıları, kötüye kullanımı ve aşırı özerkliği önler.

|   #   | Açıklama                                                                                                                                                                                                   | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.4.1 | 429 hatalarında üssel geri çekilme ile kullanıcı başına ve API anahtarı başına kota sınırlarının istekleri, tokenları ve maliyeti sınırladığını doğrulayın.                                                |   1    |  D  |
| 7.4.2 | Ayrıcalıklı işlemlerin (dosya yazımları, kod yürütme, ağ çağrıları) politika tabanlı onay veya insan müdahalesi gerektirdiğini doğrulayın.                                                                 |   1    | D/V |
| 7.4.3 | Aynı istek için oluşturulan görüntülerin, kodların ve metinlerin kötü amaçlı içerik gizlemek için kullanılamayacağını garanti etmek üzere, çapraz modal tutarlılık kontrollerinin sağlandığını doğrulayın. |   2    | D/V |
| 7.4.4 | Ajan temsil derinliği, özyineleme sınırları ve izin verilen araç listelerinin açıkça yapılandırıldığını doğrulayın.                                                                                        |   2    |  D  |
| 7.4.5 | Limit ihlallerinin SIEM alımı için yapılandırılmış güvenlik olayları yayınladığını doğrulayın.                                                                                                             |   3    |  V  |

---

## C7.5 Çıktı Açıklanabilirliği

Şeffaf sinyaller, kullanıcı güvenini ve dahili hata ayıklamayı artırır.

|   #   | Açıklama                                                                                                                         | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.5.1 | Kullanıcıya yönelik güven puanlarının veya kısa sebep özetlerinin risk değerlendirmesi uygun gördüğünde sunulduğunu doğrulayın.  |   2    | D/V |
| 7.5.2 | Oluşturulan açıklamaların hassas sistem istemlerini veya tescilli verileri ortaya çıkarmadığını doğrulayın.                      |   2    | D/V |
| 7.5.3 | Sistemin, yetkili inceleme için token düzeyinde olasılık günlüklerini veya dikkat haritalarını yakalayıp sakladığını doğrulayın. |   3    |  D  |
| 7.5.4 | Açıklanabilirlik artefaktlarının denetlenebilirlik için model sürümleriyle birlikte sürüm kontrolü altında olduğunu doğrulayın.  |   3    |  V  |

---

## C7.6 İzleme Entegrasyonu

Gerçek zamanlı gözlemlenebilirlik, geliştirme ile üretim arasındaki döngüyü kapatır.

|   #   | Açıklama                                                                                                                                                       | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.6.1 | Metriklerin (şema ihlalleri, halüsinasyon oranı, toksisite, KİB sızıntıları, gecikme süresi, maliyet) merkezi bir izleme platformuna aktarıldığını doğrulayın. |   1    |  D  |
| 7.6.2 | Her güvenlik metriği için uyarı eşiklerinin tanımlandığını ve çağrı sırası yükseltme yollarının bulunduğunu doğrulayın.                                        |   1    |  V  |
| 7.6.3 | Gösterge tablolarının çıktı anomalilerini model/sürüm, özellik bayrağı ve yukarı akış veri değişiklikleri ile ilişkilendirdiğini doğrulayın.                   |   2    |  V  |
| 7.6.4 | İzleme verilerinin, belgelenmiş bir MLOps iş akışı içinde yeniden eğitim, ince ayar veya kural güncellemelerine geri besleme yapıldığını doğrulayın.           |   2    | D/V |
| 7.6.5 | İzleme hatlarının, hassas günlüklerin sızmasını önlemek için penetrasyon testinden geçirilmiş ve erişim kontrolüne tabi tutulmuş olduğunu doğrulayın.          |   3    |  V  |

---

## 7.7 Üretken Medya Güvenceleri

AI sistemlerinin yasa dışı, zararlı veya yetkisiz medya içeriği üretmemesini sağlamak için politika kısıtlamalarını, çıktı doğrulamasını ve izlenebilirliği uygulayın.

|   #   | Açıklama                                                                                                                                                                                                                              | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 7.7.1 | Sistem istemlerinin ve kullanıcı talimatlarının, yasadışı, zararlı veya rızaya dayanmayan deepfake medya (örneğin, görüntü, video, ses) üretimini açıkça yasakladığını doğrulayın.                                                    |   1    | D/V |
| 7.7.2 | Taklit üretme girişimleri, cinsel içerikli derin sahte görüntüler veya gerçek kişileri rıza olmadan tasvir eden medyanın oluşturulması için gelen istemlerin filtrelendiğini doğrulayın.                                              |   2    | D/V |
| 7.7.3 | Sistemin, telif hakkıyla korunan medyanın izinsiz çoğaltılmasını önlemek için algısal karmalama, filigran tespiti veya parmak izi yöntemlerini kullandığını doğrulayın.                                                               |   2    |  V  |
| 7.7.4 | Tüm oluşturulan medyanın, aşağı yönlü izlenebilirlik için kriptografik olarak imzalanmış, filigranlı veya manipülasyona dayanıklı köken metadatalarıyla gömülü olduğunu doğrulayın.                                                   |   3    | D/V |
| 7.7.5 | Bypass girişimlerinin (örneğin, istem gizleme, argo, saldırgan ifadeler) tespit edildiğinden, kaydedildiğinden ve hız sınırlandırmasına tabi tutulduğundan emin olun; tekrar eden kötüye kullanımlar izleme sistemlerine bildirilsin. |   3    |  V  |

## Referanslar

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

