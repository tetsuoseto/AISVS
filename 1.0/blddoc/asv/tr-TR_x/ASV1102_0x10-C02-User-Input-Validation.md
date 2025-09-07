# C2 Kullanıcı Girdisi Doğrulaması

## Kontrol Amacı

Kullanıcı girdisinin sağlam şekilde doğrulanması, yapay zeka sistemlerine yönelik en zararlı saldırılara karşı birinci savunma hattıdır. Prompt enjeksiyonu saldırıları, sistem talimatlarını geçersiz kılabilir, hassas verileri sızdırabilir veya modeli izin verilmeyen davranışlara yönlendirebilir. Özel filtreler ve talimat hiyerarşileri uygulanmadığı sürece, araştırmalar çok uzun bağlam pencerelerini kullanan "çoklu atış" jailbreaklerin etkili olacağını göstermektedir. Ayrıca, homoglifi değişiklikleri veya leetspeak gibi ince düşmanca bozulma saldırıları, modelin kararlarını sessizce değiştirebilir.

---

## C2.1 İstem Enjeksiyonu Savunması

Prompt enjeksiyonu, yapay zeka sistemleri için en büyük risklerden biridir. Bu taktiğe karşı savunmalar, statik desen filtreleri, dinamik sınıflandırıcılar ve talimat hiyerarşisi uygulamasının bir kombinasyonunu kullanır.

|   #   | Açıklama                                                                                                                                                                                                                                | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.1.1 | Kullanıcı girdilerinin, sürekli güncellenen bilinen istem enjeksiyonu kalıpları (jailbreak anahtar kelimeleri, "öncekileri yok say", rol yapma zincirleri, dolaylı HTML/URL saldırıları) kütüphanesine karşı tarandığının doğrulanması. |   1    | D/V |
| 2.1.2 | Sistemin, bağlam penceresi genişletildikten sonra bile, sistem veya geliştirici mesajlarının kullanıcı talimatlarının yerine geçtiği bir talimat hiyerarşisini zorladığını doğrulayın.                                                  |   1    | D/V |
| 2.1.3 | Her model veya prompt-şablon sürümünden önce, başarı oranı eşikleri ve gerilemeler için otomatik engelleyicilerle birlikte, adversarial değerlendirme testlerinin (örneğin, Red Team "çoklu-atış" istemleri) yürütüldüğünü doğrulayın.  |   2    | D/V |
| 2.1.4 | Üçüncü taraf içeriklerinden (web sayfaları, PDF’ler, e-postalar) gelen istemlerin, ana isteme eklenmeden önce izole bir ayrıştırma bağlamında temizlendiğinin doğrulanması.                                                             |   2    |  D  |
| 2.1.5 | Tüm istemci-filtre kural güncellemelerinin, sınıflandırıcı model sürümlerinin ve engelleme listesi değişikliklerinin sürüm kontrolü altında ve denetlenebilir olduğunu doğrulayın.                                                      |   3    | D/V |

---

## C2.2 Karşıt-Örnek Direnci

Doğal Dil İşleme (NLP) modelleri, insanlar tarafından sıklıkla fark edilmeyen ancak modellerin yanlış sınıflandırma eğiliminde olduğu ince karakter veya kelime düzeyindeki bozulmalara karşı hâlâ savunmasızdır.

|   #   | Açıklama                                                                                                                                                                                                                             | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 2.2.1 | Temel girdi normalizasyon adımlarının (Unicode NFC, homoglif eşlemesi, boşluk kırpma) tokenlemeden önce çalıştığını doğrulayın.                                                                                                      |   1    |  D  |
| 2.2.2 | İstatistiksel anomali tespitinin, dil normlarına göre olağanüstü yüksek düzenleme mesafesine, aşırı tekrar eden tokenlara veya anormal gömme mesafelerine sahip girdileri işaretlediğini doğrulayın.                                 |   2    | D/V |
| 2.2.3 | Çıkarım hattının, yüksek riskli uç noktalar için isteğe bağlı olarak adversaryal eğitimle güçlendirilmiş model varyantlarını veya savunma katmanlarını (örneğin, rastgeleleştirme, savunmacı distilasyon) desteklediğini doğrulayın. |   2    |  D  |
| 2.2.4 | Şüpheli düşmanca girişlerin karantinaya alındığını, tam yüklerle birlikte kaydedildiğini (KİB'in çıkarılmasından sonra) doğrulayın.                                                                                                  |   2    |  V  |
| 2.2.5 | Dayanıklılık metriklerinin (bilinen saldırı setlerinin başarı oranı) zaman içinde takip edildiğini ve gerilemelerin sürüm engelleyicisini tetiklediğini doğrulayın.                                                                  |   3    | D/V |

---

## C2.3 Şema, Tür ve Uzunluk Doğrulaması

Bozuk veya aşırı büyük girdiler içeren Yapay Zeka saldırıları, ayrıştırma hatalarına, alanlar arasında istem taşmasına ve kaynak tükenmesine neden olabilir. Kesin araç çağrıları gerçekleştirilirken katı şema uygulaması da ön koşuldur.

|   #   | Açıklama                                                                                                                                                                                            | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.3.1 | Her API veya fonksiyon çağrısı uç noktasının açık bir giriş şeması (JSON Şeması, Protobuf veya çok modlu eşdeğeri) tanımladığını ve girdilerin istem oluşturulmadan önce doğrulandığını doğrulayın. |   1    |  D  |
| 2.3.2 | Girişlerin maksimum token veya byte sınırlarını aşması durumunda güvenli bir hata ile reddedildiğini ve asla sessizce kısaltılmadığını doğrulayın.                                                  |   1    | D/V |
| 2.3.3 | Tür türü denetimlerinin (örneğin, sayısal aralıklar, enum değerleri, görüntü/ses için MIME türleri) sadece istemci kodunda değil, sunucu tarafında da zorunlu kılındığını doğrulayın.               |   2    | D/V |
| 2.3.4 | Anlamsal doğrulayıcıların (örneğin, JSON Şeması) algoritmik hizmet reddi (DoS) saldırılarını önlemek için sabit zamanda çalıştığını doğrulayın.                                                     |   2    |  D  |
| 2.3.5 | Doğrulama hatalarının, güvenlik sınıflandırmasına yardımcı olmak için sansürlenmiş veri parçacıkları ve net hata kodlarıyla kaydedildiğini doğrulayın.                                              |   3    |  V  |

---

## C2.4 İçerik ve Politika Tarama

Geliştiriciler, yasaklanmış içerik talep eden (örneğin, yasa dışı talimatlar, nefret söylemi ve telif hakkıyla korunan metinler gibi) sözdizimsel olarak geçerli istemleri tespit edebilmeli ve bunların yayılmasını engellemelidir.

|   #   | Açıklama                                                                                                                                                                                                                                | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.4.1 | Bir içerik sınıflandırıcısının (sıfır atış veya ince ayarlanmış) her girdiyi şiddet, kendine zarar verme, nefret, cinsel içerik ve yasa dışı talepler açısından puanladığını, eşik değerlerinin yapılandırılabilir olduğunu doğrulayın. |   1    |  D  |
| 2.4.2 | Politikaları ihlal eden girdilerin, standartlaştırılmış reddedilmeler veya güvenli tamamlamalar alacağını ve böylece aşağı akıştaki LLM çağrılarına yayılmayacağını doğrulayın.                                                         |   1    | D/V |
| 2.4.3 | Tarama modelinin veya kural setinin, yeni gözlemlenen jailbreak veya politika atlatma kalıplarını dahil ederek en az üç aylık dönemlerde yeniden eğitildiğini/güncellendiğini doğrulayın.                                               |   2    |  D  |
| 2.4.4 | Kullanıcıya özgü politikaların (yaş, bölgesel yasal kısıtlamalar) taleple çözülme zamanında nitelik tabanlı kurallar aracılığıyla korunduğunu doğrulayın.                                                                               |   2    |  D  |
| 2.4.5 | Tarama günlüklerinin SOC korelasyonu ve gelecekteki kırmızı takım tekrarı için sınıflandırıcı güven skorlarını ve politika kategori etiketlerini içerdiğini doğrulayın.                                                                 |   3    |  V  |

---

## C2.5 Girdi Hızı Sınırlaması ve Kötüye Kullanım Önleme

Geliştiriciler, giriş hızlarını sınırlayarak ve anormal kullanım kalıplarını tespit ederek AI sistemlerine yönelik kötüye kullanımı, kaynak tükenmesini ve otomatik saldırıları önlemelidir.

|   #   | Açıklama                                                                                                                                        | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.5.1 | Tüm giriş uç noktaları için kullanıcı başına, IP başına ve API anahtarı başına hız sınırlarının uygulandığını doğrulayın.                       |   1    | D/V |
| 2.5.2 | Patlama ve sürekli hız sınırlarının DoS ve kaba kuvvet saldırılarını önleyecek şekilde ayarlandığını doğrulayın.                                |   2    | D/V |
| 2.5.3 | Anormal kullanım kalıplarının (örneğin, hızlı istekler, giriş bombardımanı) otomatik engellemeleri veya yükseltmeleri tetiklediğini doğrulayın. |   2    | D/V |
| 2.5.4 | Kötüye kullanım önleme kayıtlarının saklandığını ve ortaya çıkan saldırı kalıpları için incelendiğini doğrulayın.                               |   3    |  V  |

---

## C2.6 Çok Modlu Girdi Doğrulaması

Yapay zeka sistemleri, enjeksiyon, kaçınma veya kaynak kötüye kullanımını önlemek için metin dışı girdiler (görseller, ses, dosyalar) için sağlam doğrulama içermelidir.

|   #   | Açıklama                                                                                                                            | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.6.1 | Tüm metin dışı girdilerin (görseller, sesler, dosyalar) işlenmeden önce tür, boyut ve format açısından doğrulandığını kontrol edin. |   1    |  D  |
| 2.6.2 | Dosyaların alım öncesinde kötü amaçlı yazılım ve steganografik yükler için tarandığını doğrulayın.                                  |   2    | D/V |
| 2.6.3 | Görüntü/ses girdilerinin, düşmanca bozulumlar veya bilinen saldırı desenleri açısından kontrol edildiğini doğrulayın.               |   2    | D/V |
| 2.6.4 | Çok modlu giriş doğrulama hatalarının kaydedildiğini ve inceleme için uyarılar tetiklediğini doğrulayın.                            |   3    |  V  |

---

## C2.7 Girdi Kökeni ve Atıf

Yapay zeka sistemleri, tüm kullanıcı girdilerinin kaynaklarını izleyerek, etiketleyerek ve denetleyerek denetim, kötüye kullanım takibi ve uyumluluğu desteklemelidir.

|   #   | Açıklama                                                                                                                                             | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.7.1 | Tüm kullanıcı girdilerinin alınma sırasında meta verilerle (kullanıcı kimliği, oturum, kaynak, zaman damgası, IP adresi) etiketlendiğini doğrulayın. |   1    | D/V |
| 2.7.2 | İşlenen tüm girdiler için kaynağa ilişkin meta verilerin saklandığını ve denetlenebilir olduğunu doğrulayın.                                         |   2    | D/V |
| 2.7.3 | Anormal veya güvenilmeyen giriş kaynaklarının işaretlendiğini ve artırılmış denetime veya engellemeye tabi tutulduğunu doğrulayın.                   |   2    | D/V |

---

## C2.8 Gerçek Zamanlı Uyarlanabilir Tehdit Tespiti

Geliştiriciler, yeni saldırı desenlerine uyum sağlayan ve derlenmiş desen eşlemesi ile gerçek zamanlı koruma sunan gelişmiş tehdit algılama sistemlerini yapay zeka için kullanmalıdır.

|   #   | Açıklama                                                                                                                                                                                     | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.8.1 | Tehdit tespit kalıplarının, minimum gecikme etkisiyle yüksek performanslı gerçek zamanlı filtreleme için optimize edilmiş regex motorlarına derlendiğini doğrulayın.                         |   1    | D/V |
| 2.8.2 | Tehdit algılama sistemlerinin farklı tehdit kategorileri (prompt enjeksiyonu, zararlı içerik, hassas veri, sistem komutları) için ayrı desen kütüphaneleri tuttuğunu doğrulayın.             |   1    | D/V |
| 2.8.3 | Uyarlanabilir tehdit tespitinin, saldırı sıklığı ve başarı oranlarına dayalı olarak tehdit hassasiyetini güncelleyen makine öğrenimi modellerini içerdiğini doğrulayın.                      |   2    | D/V |
| 2.8.4 | Gerçek zamanlı tehdit istihbaratı akışlarının, yeni saldırı imzaları ve IOC'ler (Zararlı Faaliyet Göstergeleri) ile desen kütüphanelerini otomatik olarak güncellediğini doğrulayın.         |   2    | D/V |
| 2.8.5 | Tehdit tespiti yanlış pozitif oranlarının sürekli olarak izlendiğini ve desen özgüllüğünün meşru kullanım durumuna müdahaleyi en aza indirmek için otomatik olarak ayarlandığını doğrulayın. |   3    | D/V |
| 2.8.6 | Bağlamsal tehdit analizinin algılama doğruluğunu artırmak için girdi kaynağını, kullanıcı davranış kalıplarını ve oturum geçmişini dikkate aldığını doğrulayın.                              |   3    | D/V |
| 2.8.7 | Tehdit tespiti performans metriklerinin (tespit oranı, işleme gecikmesi, kaynak kullanımı) gerçek zamanlı olarak izlendiği ve optimize edildiği doğrulanmalıdır.                             |   3    | D/V |

---

## C2.9 Çok Modlu Güvenlik Doğrulama Boru Hattı

Geliştiriciler, metin, görüntü, ses ve diğer AI giriş biçimleri için belirli türde tehdit algılama ve kaynak izolasyonu ile güvenlik doğrulaması sağlamalıdır.

|   #   | Açıklama                                                                                                                                                                                                                                          | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 2.9.1 | Her giriş modalitesinin, belgelenmiş tehdit desenlerine (metin: istem enjeksiyonu, görüntüler: steganografi, ses: spektrogram saldırıları) ve tespit eşiklerine sahip özel güvenlik doğrulayıcılarına sahip olduğunu doğrulayın.                  |   1    | D/V |
| 2.9.2 | Çok modlu girdilerin, her modül türüne özgü tanımlanmış kaynak sınırlarına (bellek, CPU, işleme süresi) sahip izole kum havuzlarında işlendiğini ve bunun güvenlik politikalarında belgelenmiş olduğunu doğrulayın.                               |   2    | D/V |
| 2.9.3 | Çapraz modal saldırı tespitinin, korelasyon kuralları ve uyarı oluşturma ile birden fazla girdi türünü kapsayan (örneğin, görüntülerde steganografik yükler ile metinde istem enjeksiyonu) koordineli saldırıları tanımladığını doğrulayın.       |   2    | D/V |
| 2.9.4 | Çok modlu doğrulama hatalarının, tüm giriş modları, doğrulama sonuçları, tehdit puanları ve SIEM entegrasyonu için yapılandırılmış günlük formatları ile korelasyon analizini içeren ayrıntılı günlük kaydını tetiklediğini doğrulayın.           |   3    | D/V |
| 2.9.5 | Modaliteye özgü içerik sınıflandırıcılarının, belgelenmiş programlara (en az üç aylık) göre yeni tehdit kalıpları, adversaryal örnekler ve temel performans eşiklerinin üzerinde tutulan performans kıyaslamaları ile güncellendiğini doğrulayın. |   3    | D/V |

---

## Referanslar

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

