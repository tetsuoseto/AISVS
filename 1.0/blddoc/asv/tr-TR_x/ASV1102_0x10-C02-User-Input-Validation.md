# C2 Kullanıcı Girdi Doğrulaması

## Kontrol Amacı

Kullanıcı girdisinin sağlam doğrulanması, yapay zekâ sistemlerine yönelik en zararlı saldırılardan bazılarına karşı birinci savunma hattını oluşturur. İstem enjeksiyonu saldırıları, sistem talimatlarını geçersiz kılabilir, hassas verileri sızdırabilir veya modelin izin verilmeyen davranışlara yönlendirilmesine yol açabilir. Özel filtreler ve talimat hiyerarşileri mevcut olmadığında, çok uzun bağlam pencerelerinden yararlanarak yapılan "multi-shot" jailbreak'lerin etkili olacağını gösteren araştırmalar bulunmaktadır. Ayrıca, homoglif değişimleri veya leetspeak gibi ince adversarial perturbasyon saldırıları—-bir modelin kararlarını sessizce değiştirebilir.

---

## C2.1 Prompt Enjeksiyonu Savunması

İstem enjeksiyonu, yapay zeka sistemleri için en büyük risklerden biridir. Bu taktiğe karşı savunmalar, statik desen filtrelerinin, dinamik sınıflandırıcıların ve talimat hiyerarşisinin uygulanmasının bir kombinasyonunu kullanır.

|   #   | Açıklama                                                                                                                                                                                                                                                 | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.1.1 | Kullanıcı girdilerinin, sürekli güncellenen bilinen istem enjeksiyonu desenleri kütüphanesine karşı tarandığından emin olun (jailbreak anahtar kelimeleri, "ignore previous", rol oynama zincirleri, dolaylı HTML/URL saldırıları).                      |   1    | D/V |
| 2.1.2 | Sistemin, bağlam penceresi genişletildikten sonra bile sistem veya geliştirici mesajlarının kullanıcı talimatlarını geçersiz kıldığı bir talimat hiyerarşisini zorunlu kıldığını doğrulayın.                                                             |   1    | D/V |
| 2.1.3 | Her model veya istem-şablonu sürümünden önce adversarial değerlendirme testlerinin (örneğin Red Team 'many-shot' istemleri) yürütüldüğünü doğrulayın; bu süreç için başarı oranı eşiği ve regresyonlar için otomatik engelleyicilerin bulunması gerekir. |   2    | D/V |
| 2.1.4 | Üçüncü taraf içeriğinden gelen istemlerin (web sayfaları, PDF'ler, e-postalar) ana isteme eklenmeden önce izole bir ayrıştırma bağlamında arındırıldığını doğrulayın.                                                                                    |   2    |  D  |
| 2.1.5 | Tüm prompt-filter kural güncellemelerinin, sınıflandırıcı model sürümlerinin ve block-list değişikliklerinin sürüm kontrolünde ve denetlenebilir olmasını doğrulayın.                                                                                    |   3    | D/V |

---

## C2.2 Saldırıya Karşı Örnek Direnci

Doğal Dil İşleme (NLP) modelleri, insanlar çoğu zaman fark etmediği fakat modellerin yanlış sınıflandırmaya eğilim gösterdiği ince karakter veya kelime düzeyindeki perturbasyonlara karşı hâlâ savunmasızdır.

|   #   | Açıklama                                                                                                                                                                                                              | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.2.1 | Temel giriş normalizasyonu adımlarının (Unicode NFC, homoglif eşleme, boşlukların kırpılması) tokenleştirmeden önce çalıştığından emin olun.                                                                          |   1    |  D  |
| 2.2.2 | İstatistiksel anomali tespitinin, dil normlarına göre olağanüstü yüksek düzenleme mesafesi, aşırı tekrarlanan tokenler veya anormal gömme uzaklıkları olan girdileri işaretlediğini doğrulayın.                       |   2    | D/V |
| 2.2.3 | Çıkarım hattının, yüksek riskli uç noktalar içinisteğe bağlı adversarial-training–hardened model varyantlarını veya savunma katmanlarını desteklediğini doğrulayın (örneğin, rastgeleleştirme, savunma distilasyonu). |   2    |  D  |
| 2.2.4 | Şüpheli adversarial girdilerin karantinaya alındığını, tam payload'larla kaydedildiğini (PII redaksiyonu sonrası) doğrulayın.                                                                                         |   2    |  V  |
| 2.2.5 | Dayanıklılık metriklerinin (bilinen saldırı kümelerinin başarı oranı) zaman içinde izlenmesini ve regresyonların bir sürüm engelleyici tetiklemesini doğrulayın.                                                      |   3    | D/V |

---

## C2.3 Şema, Tip ve Uzunluk Doğrulaması

Yapay Zeka saldırıları, biçimlendirilmemiş veya çok büyük girdiler içerdiğinde ayrıştırma hatalarına, alanlar arasında istemin taşmasına ve kaynak tükenmesine yol açabilir.  Deterministik araç çağrılarını gerçekleştirirken sıkı şema denetimi de bir önkoşuldur.

|   #   | Açıklama                                                                                                                                                                                            | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.3.1 | Her API veya fonksiyon çağrısı uç noktasının açık bir girdi şeması (JSON Şeması, Protobuf veya çok modlu eşdeğeri) tanımladığını ve girdilerin prompt derlemesinden önce doğrulandığını doğrulayın. |   1    |  D  |
| 2.3.2 | Maksimum belirteç veya bayt sınırlarını aşan girdilerin güvenli bir hata ile reddedildiğini ve asla sessizce kesilmediğini doğrulayın.                                                              |   1    | D/V |
| 2.3.3 | Tip kontrollerinin (örneğin sayısal aralıklar, enum değerleri, resimler ve sesler için MIME türleri) yalnızca istemci tarafında değil, sunucu tarafında da uygulanmasını doğrulayın.                |   2    | D/V |
| 2.3.4 | Semantik doğrulayıcıların (örneğin JSON Şeması) sabit zamanda çalıştığını doğrulayın; böylece algoritmik DoS saldırısı önlenir.                                                                     |   2    |  D  |
| 2.3.5 | Doğrulama hatalarının sansürlenmiş yük parçacıkları ve açık hata kodlarıyla kaydedildiğini doğrulayın; bu, güvenlik triage'ını kolaylaştırır.                                                       |   3    |  V  |

---

## C2.4 İçerik ve Politika Tarama

Geliştiricilerin, yasak içerik talep eden sözdizimsel olarak geçerli istemleri tespit edebilmesi ve bunların yayılmasını engelleyebilmesi gerekir.

|   #   | Açıklama                                                                                                                                                                                                                               | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.4.1 | Bir içerik sınıflandırıcısının (sıfır atışlı veya ince ayarlı) her girdiyi şiddet, kendi kendine zarar verme, nefret, cinsel içerik ve yasa dışı istekler açısından skorladığını doğrulayın; bu skorlar ayarlanabilir eşiklerle olsun. |   1    |  D  |
| 2.4.2 | Politikalara aykırı girdilerin standart reddedilmelerle veya güvenli tamamlamalarla ele alınacağını doğrulayın; böylece bunlar sonraki LLM çağrılarına yayılmaz.                                                                       |   1    | D/V |
| 2.4.3 | Tarama modeli veya kural setinin en az üç ayda bir yeniden eğitildiğini/güncellendiğini doğrulayın; yeni gözlemlenen jailbreak veya politika atlatma kalıplarını içerecek şekilde güncellemeleri de dahil edin.                        |   2    |  D  |
| 2.4.4 | Taramanın kullanıcıya özgü politikalara (yaş, bölgesel yasal kısıtlamalar) uyduğunu istek anında belirlenen nitelik tabanlı kurallar aracılığıyla doğrulayın.                                                                          |   2    |  D  |
| 2.4.5 | Tarama günlüklerinin SOC korelasyonu ve gelecekteki red-team tekrarı için sınıflandırıcı güven skorlarını ve politika kategori etiketlerini içerdiğini doğrulayın.                                                                     |   3    |  V  |

---

## C2.5 Girdi Hızı Sınırlandırması ve Kötüye Kullanımın Önlenmesi

Geliştiriciler, yapay zekâ sistemlerine karşı kötüye kullanımı, kaynak tükenmesini ve otomatik saldırıları önlemek için girdi hızlarını sınırlamalı ve anormal kullanım desenlerini tespit etmelidir.

|   #   | Açıklama                                                                                                                                            | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.5.1 | Kullanıcı başına, IP adresine göre ve API anahtarına göre hız sınırlarının tüm giriş uç noktaları için uygulanıp uygulanmadığını doğrulayın.        |   1    | D/V |
| 2.5.2 | DoS ve brute force saldırılarını önlemek için ani ve sürekli hız sınırlarının ayarlandığından emin olun.                                            |   2    | D/V |
| 2.5.3 | Anormal kullanım kalıplarının (örneğin, peş peşe gelen istekler, giriş bombardımanı) otomatik blokları veya yükseltmeleri tetiklediğini doğrulayın. |   2    | D/V |
| 2.5.4 | Kötüye kullanım önleme günlüklerinin saklandığından ve ortaya çıkan saldırı kalıpları için incelendiğinden emin olun.                               |   3    |  V  |

---

## C2.6 Çok Modlu Girdi Doğrulaması

Yapay zeka sistemleri, enjeksiyonu, kaçınmayı veya kaynak suistimalini önlemek amacıyla metin dışı girdiler (görüntüler, sesler ve dosyalar) için sağlam doğrulama içermelidir.

|   #   | Açıklama                                                                                                                      | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.6.1 | İşlemden önce tüm metin dışı girdilerin (görüntüler, sesler, dosyalar) tür, boyut ve biçim açısından doğrulanmasını sağlayın. |   1    |  D  |
| 2.6.2 | Dosyaların içe aktarılmadan önce zararlı yazılımlar ve steganografik yükler için tarandığından emin olun.                     |   2    | D/V |
| 2.6.3 | Görüntü ve ses girdilerinin adversarial perturbasyonlar veya bilinen saldırı kalıpları için kontrol edildiğini doğrulayın.    |   2    | D/V |
| 2.6.4 | Çok modlu giriş doğrulama hatalarının kaydedildiğini ve inceleme için uyarıların tetiklendiğini doğrulayın.                   |   3    |  V  |

---

## C2.7 Girdi Kökeni ve Atıf

Yapay zeka sistemleri, tüm kullanıcı girdilerinin kökenlerini izleyip etiketleyerek denetim, kötüye kullanım takibi ve uyumluluğu desteklemelidir.

|   #   | Açıklama                                                                                                                                                    | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.7.1 | Tüm kullanıcı girdilerinin içe aktarım sırasında meta verileriyle (kullanıcı kimliği, oturum, kaynak, zaman damgası, IP adresi) etiketlendiğini doğrulayın. |   1    | D/V |
| 2.7.2 | Tüm işlenen girdiler için köken meta verilerinin korunup denetlenebilir olduğundan emin olun.                                                               |   2    | D/V |
| 2.7.3 | Anormal veya güvenilmez giriş kaynaklarının işaretlendiğini ve artırılmış inceleme veya engellemeye tabi tutulduğunu doğrulayın.                            |   2    | D/V |

---

## C2.8 Gerçek Zamanlı Adaptif Tehdit Tespiti

Geliştiriciler, AI için yeni saldırı kalıplarına uyum sağlayan ve derlenmiş desen eşleşmesiyle gerçek zamanlı koruma sağlayan gelişmiş tehdit tespit sistemlerini kullanmalıdır.

|   #   | Açıklama                                                                                                                                                                                                 | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.8.1 | Tehdit tespit desenlerinin yüksek performanslı gerçek zamanlı filtreleme için minimum gecikme etkisiyle optimize edilmiş regex motorlarına derlendiğini doğrulayın.                                      |   1    | D/V |
| 2.8.2 | Tehdit algılama sistemlerinin farklı tehdit kategorileri için ayrı desen kütüphanelerine sahip olduğunu doğrulayın (istem enjeksiyonu, zararlı içerik, hassas veriler, sistem komutları).                |   1    | D/V |
| 2.8.3 | Uyarlanabilir tehdit tespitinin, saldırı sıklığı ve başarı oranlarına dayanarak tehdit hassasiyetini güncelleyen makine öğrenimi modellerini entegre ettiğini doğrulayın.                                |   2    | D/V |
| 2.8.4 | Gerçek zamanlı tehdit istihbaratı akışlarının, yeni saldırı imzaları ve İhlal Göstergeleri ile birlikte desen kütüphanelerini otomatik olarak güncellediğini doğrulayın.                                 |   2    | D/V |
| 2.8.5 | Tehdit tespitinin yanlış pozitif oranlarının sürekli izlendiğini ve desen özgüllüğünün meşru kullanım durumlarına müdahale edilmesini en aza indirecek şekilde otomatik olarak ayarlandığını doğrulayın. |   3    | D/V |
| 2.8.6 | Bağlamsal tehdit analizinin girdi kaynağını, kullanıcı davranış kalıplarını ve oturum geçmişini dikkate alarak tespit doğruluğunu artırdığını doğrulayın.                                                |   3    | D/V |
| 2.8.7 | Tehdit tespiti performans göstergelerinin (tespit oranı, işleme gecikmesi, kaynak kullanımı) gerçek zamanlı olarak izlendiğini ve optimize edildiğini doğrulayın.                                        |   3    | D/V |

---

## C2.9 Çok-Modlu Güvenlik Doğrulama İş Akışı

Geliştiriciler, metin, görüntü, ses ve diğer AI giriş biçimleri için belirli tehdit tespiti türleri ve kaynak izolasyonu ile güvenlik doğrulaması sağlamalıdır.

|   #   | Açıklama                                                                                                                                                                                                                                                                        | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.9.1 | Her bir girdi modu için belgelenmiş tehdit desenlerine sahip özel güvenlik doğrulayıcıları ve tespit eşiklerine sahip olduğundan emin olun (metin: prompt enjeksiyonu, görüntüler: steganografi, ses: spektrogram saldırıları).                                                 |   1    | D/V |
| 2.9.2 | Çok modlu girdilerin her mod tipi için belirlenen kaynak sınırlamalarıyla (bellek, CPU, işleme süresi) izole sandbox'larda işlendiğini ve güvenlik politikalarında belgelendiğini doğrulayın.                                                                                   |   2    | D/V |
| 2.9.3 | Çapraz-mod saldırı tespitinin, birden çok giriş türünü kapsayan koordine edilmiş saldırıları (örneğin resimlerdeki steganografik yükler ile metindeki prompt enjeksiyonu) korelasyon kuralları ve uyarı üretimi ile tanımladığını doğrulayın.                                   |   2    | D/V |
| 2.9.4 | Çok modlu doğrulama hatalarının, SIEM entegrasyonu için yapılandırılmış günlük formatlarıyla tüm girdi modlarını, doğrulama sonuçlarını, tehdit skorlarını ve korelasyon analizini içeren ayrıntılı günlük kaydını tetiklediğini doğrulayın.                                    |   3    | D/V |
| 2.9.5 | Belgelere dayalı takvime göre (asgari olarak her çeyrekte bir) modalliklere özgü içerik sınıflandırıcılarının güncellendiğini ve bu süreçte yeni tehdit kalıpları, adversarial örnekler ile baz eşiklerinin üzerinde tutulan performans göstergelerinin korunduğunu doğrulayın. |   3    | D/V |

---

## Kaynaklar

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

