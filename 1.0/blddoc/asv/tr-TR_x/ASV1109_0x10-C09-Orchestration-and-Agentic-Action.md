# 9 Otonom Orkestrasyon ve Temsil Yeteneğine Sahip Ajan Güvenliği

## Kontrol Amacı

Otonom veya çoklu ajan yapay zeka sistemlerinin yalnızca açıkça amaçlanan, doğrulanabilir, denetlenebilir ve belirli maliyet ve risk sınırları içinde kalan eylemleri gerçekleştirebilmesini sağlayın. Bu, Otonom Sistem İhlali, Araç Kötüye Kullanımı, Ajan Döngüsü Tespiti, İletişim Kaçırma, Kimlik Taklidi, Sürü Manipülasyonu ve Niyet Manipülasyonu gibi tehditlere karşı koruma sağlar.

---

## 9.1 Ajan Görev Planlama ve Özyineleme Bütçeleri

İmtiyazlı işlemler için özyinelemeli planları sınırlayın ve insan kontrol noktalarını zorunlu kılın.

|   #   | Açıklama                                                                                                                                                                                                    | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.1.1 | Her bir ajan yürütmesi için maksimum özyineleme derinliği, genişlik, gerçek zamanlı süre, token sayısı ve parasal maliyetin merkezi olarak yapılandırıldığını ve sürüm kontrolünün sağlandığını doğrulayın. |   1    | D/V |
| 9.1.2 | Ayrıcalıklı veya geri alınamaz işlemlerin (örneğin, kod gönderimleri, finansal transferler) yürütülmeden önce denetlenebilir bir kanal aracılığıyla açık insan onayı gerektirdiğini doğrulayın.             |   1    | D/V |
| 9.1.3 | Gerçek zamanlı kaynak izleyicilerin herhangi bir bütçe eşiği aşıldığında devre kesici kesintisini tetikleyerek ilave görev genişlemesini durdurduğunu doğrulayın.                                           |   2    |  D  |
| 9.1.4 | Devre kesici olaylarının, adli inceleme için ajan kimliği, tetikleyici koşul ve yakalanan plan durumu ile kaydedildiğini doğrulayın.                                                                        |   2    | D/V |
| 9.1.5 | Güvenlik testlerinin bütçe tükenmesi ve kontrolsüz plan senaryolarını kapsadığını doğrulayın, veri kaybı olmadan güvenli durdurmayı teyit edin.                                                             |   3    |  V  |
| 9.1.6 | Bütçe politikalarının kod olarak politika şeklinde ifade edildiğini ve yapılandırma sapmasını engellemek için CI/CD'de uygulandığını doğrulayın.                                                            |   3    |  D  |

---

## 9.2 Araç Eklentisi Korumalı Alanı

Araç etkileşimlerini izole ederek yetkisiz sistem erişimi veya kod yürütmesini önleyin.

|   #   | Açıklama                                                                                                                                                                                                    | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.2.1 | Her aracın/eklentinin, en düşük ayrıcalıklı dosya sistemi, ağ ve sistem çağrısı politikalarına sahip bir işletim sistemi, konteyner veya WASM seviyesinde bir korumalı ortam içinde çalıştığını doğrulayın. |   1    | D/V |
| 9.2.2 | Sandbox kaynak kotalarının (CPU, bellek, disk, ağ çıkışı) ve yürütme zaman aşımı sürelerinin uygulanıp uygulanmadığını ve kaydedildiğini doğrulayın.                                                        |   1    | D/V |
| 9.2.3 | Araç ikili dosyalarının veya tanımlayıcılarının dijital olarak imzalandığını doğrulayın; yüklemeden önce imzalar doğrulanır.                                                                                |   2    | D/V |
| 9.2.4 | Sandbox telemetrisinin bir SIEM’e aktarıldığını doğrulayın; anormallikler (örneğin, dışa yönelik bağlantı girişimleri) uyarılar oluşturur.                                                                  |   2    |  V  |
| 9.2.5 | Yüksek riskli eklentilerin üretim ortamına dağıtılmadan önce güvenlik incelemesi ve penetrasyon testinden geçtiğini doğrulayın.                                                                             |   3    |  V  |
| 9.2.6 | Sandbox kaçış girişimlerinin otomatik olarak engellendiğini ve suçlu eklentinin inceleme sürecine kadar karantinaya alındığını doğrulayın.                                                                  |   3    | D/V |

---

## 9.3 Otonom Döngü ve Maliyet Sınırlaması

Kontrolsüz ajanlar arası özyinelemeyi ve maliyet patlamalarını tespit edin ve durdurun.

|   #   | Açıklama                                                                                                                                               | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 9.3.1 | Ara ajanlar arası çağrıların, çalışma zamanı tarafından azaltılan ve uygulanan bir sıçrama sınırı veya TTL içerdiğini doğrulayın.                      |   1    | D/V |
| 9.3.2 | Ajanların kendi kendine çağrıyı veya döngüsel desenleri tespit etmek için benzersiz bir çağrı grafiği kimliğini koruduğunu doğrulayın.                 |   2    |  D  |
| 9.3.3 | Kümülatif hesap birimi ve harcama sayacıların her istek zinciri için izlenip izlenmediğini doğrulayın; limitin aşılması zincirin durmasına neden olur. |   2    | D/V |
| 9.3.4 | Ajan protokollerinde sınırsız özyinelemenin olmadığını göstermek için resmi analiz veya model kontrol yöntemlerinin kullanıldığını doğrulayın.         |   3    |  V  |
| 9.3.5 | Döngü-iptal olaylarının uyarılar oluşturduğunu ve sürekli iyileştirme metriklerini beslediğini doğrulayın.                                             |   3    |  D  |

---

## 9.4 Protokol Düzeyi Kötüye Kullanım Koruması

Elemanlar ile dış sistemler arasında kaçırma veya manipülasyonu önlemek için güvenli iletişim kanalları sağlayın.

|   #   | Açıklama                                                                                                                                                    | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.4.1 | Tüm ajan-aracı ve ajan-ajan mesajlarının kimlik doğrulamasının yapıldığını (örneğin, karşılıklı TLS veya JWT) ve uçtan uca şifrelenmiş olduğunu doğrulayın. |   1    | D/V |
| 9.4.2 | Şemaların kesinlikle doğrulandığını, bilinmeyen alanların veya hatalı biçimlendirilmiş mesajların reddedildiğini doğrulayın.                                |   1    |  D  |
| 9.4.3 | Bütün mesaj yükünü, araç parametreleri de dahil olmak üzere, bütünlüğünü kontrol eden doğrulama (MAC'ler veya dijital imzalar) ile kapsandığını doğrulayın. |   2    | D/V |
| 9.4.4 | Yeniden oynatma korumasının (nonce'lar veya zaman damgası pencereleri) protokol katmanında zorunlu kılındığını doğrulayın.                                  |   2    |  D  |
| 9.4.5 | Protokol uygulamalarının enjeksiyon veya serileştirme hataları için fuzzing ve statik analizden geçirildiğini doğrulayın.                                   |   3    |  V  |

---

## 9.5 Ajan Kimliği ve Değiştirme Kanıtı

Eylemlerin izlenebilir olmasını ve değişikliklerin tespit edilebilir olmasını sağlayın.

|   #   | Açıklama                                                                                                                             | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 9.5.1 | Her ajan örneğinin benzersiz bir kriptografik kimliğe (anahtar çifti veya donanıma dayalı kimlik bilgisi) sahip olduğunu doğrulayın. |   1    | D/V |
| 9.5.2 | Tüm ajan eylemlerinin imzalandığını ve zaman damgalı olduğunu doğrulayın; günlükler, inkâr edilememe için imzayı içermelidir.        |   2    | D/V |
| 9.5.3 | Tahrif edilmiş kayıtların eklemeye izin veren ya da sadece bir kez yazılabilen bir ortamda saklandığını doğrulayın.                  |   2    |  V  |
| 9.5.4 | Kimlik anahtarlarının belirlenen bir takvime göre ve ihlal göstergelerinde döndürüldüğünü doğrulayın.                                |   3    |  D  |
| 9.5.5 | Taklit ya da anahtar çatışması girişimlerinin etkilenmiş ajan üzerinde derhal karantina tetiklediğini doğrulayın.                    |   3    | D/V |

---

## 9.6 Çoklu Ajan Sürü Risk Azaltımı

Toplu davranış tehlikelerini izolasyon ve resmi güvenlik modellemesi yoluyla hafifletin.

|   #   | Açıklama                                                                                                                                                         | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.6.1 | Farklı güvenlik alanlarında çalışan ajanların izole çalışma zamanı kum havuzlarında veya ağ segmentlerinde yürütüldüğünü doğrulayın.                             |   1    | D/V |
| 9.6.2 | Sürülmeden önce sürü davranışlarının canlılık ve güvenlik açısından modellenip resmi olarak doğrulandığından emin olunuz.                                        |   3    |  V  |
| 9.6.3 | Çalışma zamanı izleyicilerinin ortaya çıkan tehlikeli desenleri (örneğin, salınımlar, kilitlenmeler) tespit ettiğini ve düzeltici önlem başlattığını doğrulayın. |   3    |  D  |

---

## 9.7 Kullanıcı ve Araç Kimlik Doğrulama / Yetkilendirme

Her ajan tarafından tetiklenen işlem için sağlam erişim kontrolleri uygulayın.

|   #   | Açıklama                                                                                                                                                          | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.7.1 | Ajanların, son kullanıcı kimlik bilgilerini asla yeniden kullanmadan, aşağı akış sistemlere birinci sınıf prensip olarak kimlik doğrulaması yaptığını doğrulayın. |   1    | D/V |
| 9.7.2 | Ajanın hangi araçları çağırabileceğini ve hangi parametreleri sağlayabileceğini sınırlayan ince taneli yetkilendirme politikalarını doğrulayın.                   |   2    |  D  |
| 9.7.3 | İzin kontrollerinin yalnızca oturum başlangıcında değil, her çağrıda (sürekli yetkilendirme) yeniden değerlendirildiğini doğrulayın.                              |   2    |  V  |
| 9.7.4 | Delegelenmiş ayrıcalıkların otomatik olarak sona erdiğini ve zaman aşımı veya kapsam değişikliği sonrasında yeniden onay gerektirdiğini doğrulayın.               |   3    |  D  |

---

## 9.8 Ajanlar Arası İletişim Güvenliği

Tüm ajanlar arası mesajları dinlemeye ve değiştirmeye karşı korumak için şifreleyin ve bütünlük koruması sağlayın.

|   #   | Açıklama                                                                                                                                     | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.8.1 | Ajan kanalları için karşılıklı kimlik doğrulama ve mükemmel ileri gizlilik şifrelemesinin (örneğin TLS 1.3) zorunlu olduğunu doğrulayın.     |   1    | D/V |
| 9.8.2 | İşlemeden önce mesaj bütünlüğünün ve kaynağının doğrulandığından emin olun; başarısızlık durumunda uyarılar oluşturulur ve mesaj reddedilir. |   1    |  D  |
| 9.8.3 | İletişim meta verilerinin (zaman damgaları, sıra numaraları) adli yeniden yapılandırmayı destekleyecek şekilde kaydedildiğini doğrulayın.    |   2    | D/V |
| 9.8.4 | Protokol durum makinelerinin güvensiz durumlara sürülemeyeceğini resmi doğrulama veya model kontrolünün onayladığını doğrulayın.             |   3    |  V  |

---

## 9.9 Niyet Doğrulama ve Kısıtlama Uygulaması

Ajan eylemlerinin kullanıcının belirtilen niyeti ve sistem kısıtlamalarıyla uyumlu olduğunu doğrulayın.

|   #   | Açıklama                                                                                                                                                                                          | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.9.1 | Ön yürütme kısıtlayıcı çözücülerin, önerilen eylemleri sabit kodlanmış güvenlik ve politika kurallarına karşı kontrol ettiğini doğrulayın.                                                        |   1    |  D  |
| 9.9.2 | Yüksek etkili işlemlerin (mali, yıkıcı, gizlilik açısından hassas) başlatan kullanıcıdan açık niyet onayı gerektirdiğini doğrulayın.                                                              |   2    | D/V |
| 9.9.3 | Tamamlanmış işlemlerin amaçlanan etkileri yan etkiler olmadan gerçekleştirildiğini doğrulamak için son koşul kontrollerinin geçerliliğini doğrulayın; tutarsızlıklar geri alma işlemini tetikler. |   2    |  V  |
| 9.9.4 | Ajan planlarının tüm beyan edilmiş kısıtlamaları sağladığını göstermek için resmi yöntemlerin (örneğin, model kontrolü, teorem ispatı) veya özellik tabanlı testlerin doğrulanmasını sağlayın.    |   3    |  V  |
| 9.9.5 | Niyet uyumsuzluğu veya kısıtlama ihlali olaylarının sürekli iyileştirme döngülerini ve tehdit istihbaratı paylaşımını beslediğini doğrulayın.                                                     |   3    |  D  |

---

## 9.10 Ajan Akıl Yürütme Stratejisi Güvenliği

ReAct, Chain-of-Thought ve Tree-of-Thoughts yaklaşımlarını içeren farklı muhakeme stratejilerinin güvenli seçimi ve yürütülmesi.

|   #    | Açıklama                                                                                                                                                                                                             | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.10.1 | Mantık stratejisi seçiminin deterministik kriterler (girdi karmaşıklığı, görev türü, güvenlik bağlamı) kullandığını ve aynı güvenlik bağlamı içinde özdeş girdilerin özdeş strateji seçimleri ürettiğini doğrulayın. |   1    | D/V |
| 9.10.2 | Her bir muhakeme stratejisinin (ReAct, Chain-of-Thought, Tree-of-Thoughts) kendi bilişsel yaklaşımına özgü giriş doğrulaması, çıktı temizleme ve yürütme süre sınırlarına sahip olduğunu doğrulayın.                 |   1    | D/V |
| 9.10.3 | Denetim izinin yeniden oluşturulması için giriş özellikleri, seçim kriteri değerleri ve yürütme meta verileri dahil olmak üzere gerekçelendirme stratejisi geçişlerinin tam bağlamıyla kaydedildiğini doğrulayın.    |   2    | D/V |
| 9.10.4 | Tree-of-Thoughts muhakemesinin, politika ihlalleri, kaynak sınırları veya güvenlik sınırları tespit edildiğinde keşfi sonlandıran dal budama mekanizmalarını içerdiğini doğrulayın.                                  |   2    | D/V |
| 9.10.5 | ReAct (Reason-Act-Observe) döngülerinin her aşamada doğrulama kontrol noktaları içerdiğini doğrulayın: akıl yürütme adımı doğrulaması, eylem yetkilendirmesi ve ilerlemeden önce gözlem temizliği.                   |   2    | D/V |
| 9.10.6 | Akıl yürütme stratejisi performans metriklerinin (çalışma süresi, kaynak kullanımı, çıktı kalitesi) yapılandırılmış eşiklerin dışına çıktığında otomatik uyarılarla izlenip izlenmediğini doğrulayın.                |   3    | D/V |
| 9.10.7 | Birden fazla stratejiyi birleştiren hibrit muhakeme yaklaşımlarının, herhangi bir güvenlik kontrolünü atlamadan tüm bileşen stratejilerin giriş doğrulamasını ve çıktı kısıtlamalarını koruduğunu doğrulayın.        |   3    | D/V |
| 9.10.8 | Mantık stratejisi güvenlik testinin, hatalı girdilerle yapılan fuzzing, strateji değiştirmeye zorlayan düşmanca yönlendirmeler ve her bilişsel yaklaşım için sınır durumu testlerini içerdiğini doğrulayın.          |   3    | D/V |

---

## 9.11 Ajan Yaşam Döngüsü Durum Yönetimi ve Güvenlik

Kriptografik denetim izleri ve tanımlı kurtarma prosedürleri ile güvenli ajan başlatma, durum geçişleri ve sonlandırma.

|   #    | Açıklama                                                                                                                                                                                                                                                                        | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.11.1 | Ajan başlatmasının, donanım destekli kimlik bilgileriyle kriptografik kimlik kurulumu ve ajan kimliği, zaman damgası, yapılandırma karma değeri ve başlatma parametrelerini içeren değişmez başlatma denetim günlükleri içerdiğini doğrulayın.                                  |   1    | D/V |
| 9.11.2 | Ajan durum geçişlerinin kriptografik olarak imzalandığını, zaman damgalı olduğunu ve tetikleyici olaylar, önceki durum karması, yeni durum karması ve gerçekleştirilen güvenlik doğrulamaları dahil olmak üzere tam bağlamla birlikte kaydedildiğini doğrulayın.                |   2    | D/V |
| 9.11.3 | Ajan kapatma prosedürlerinin, kriptografik silme veya çok geçişli üzerine yazma kullanarak güvenli bellek temizliğini, sertifika otoritesine bildirimle kimlik bilgisi iptalini ve müdahale kanıtı sağlayan sonlandırma sertifikalarının oluşturulmasını içerdiğini doğrulayın. |   2    | D/V |
| 9.11.4 | Ajan kurtarma mekanizmalarının durum bütünlüğünü kriptografik özetler (en az SHA-256) kullanarak doğruladığını ve bozulma tespit edildiğinde otomatik uyarılar ve manuel onay gereksinimleri ile bilinen iyi durumlara geri alındığını doğrulayın.                              |   3    | D/V |
| 9.11.5 | Ajan kalıcılık mekanizmalarının, her ajan için ayrı AES-256 anahtarlarıyla hassas durum verilerini şifrelediğini ve yapılandırılabilir zaman çizelgeleriyle (en fazla 90 gün) güvenli anahtar döndürmesini sıfır kesinti süresi ile dağıtacak şekilde uyguladığını doğrulayın.  |   3    | D/V |

---

## 9.12 Araç Entegrasyonu Güvenlik Çerçevesi

Tanımlanmış risk değerlendirme ve onay süreçleri ile dinamik araç yükleme, yürütme ve sonuç doğrulama için güvenlik kontrolleri.

|   #    | Açıklama                                                                                                                                                                                                                                                                           | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.12.1 | Araç tanımlayıcılarının, araç manifestolarında belgelenmiş olan gerekli ayrıcalıkları (okuma/yazma/çalıştırma), risk seviyelerini (düşük/orta/yüksek), kaynak sınırlarını (CPU, bellek, ağ) ve doğrulama gereksinimlerini belirten güvenlik meta verilerini içerdiğini doğrulayın. |   1    | D/V |
| 9.12.2 | Araç yürütme sonuçlarının, entegrasyon öncesinde beklenen şemalarla (JSON Şeması, XML Şeması) ve güvenlik politikalarıyla (çıkışın temizlenmesi, veri sınıflandırması) doğrulandığını; ayrıca zaman aşımı sınırları ve hata yönetim prosedürleriyle kontrol edildiğini teyit edin. |   1    | D/V |
| 9.12.3 | Araç etkileşim günlüklerinin, ayrıcalık kullanımı, veri erişim desenleri, yürütme süresi, kaynak tüketimi ve dönüş kodları dahil olmak üzere ayrıntılı güvenlik bağlamını içermesini ve SIEM entegrasyonu için yapılandırılmış günlük kaydını doğrulayın.                          |   2    | D/V |
| 9.12.4 | Dinamik araç yükleme mekanizmalarının, dijital imzaları PKI altyapısı kullanarak doğruladığını ve yürütmeden önce kum havuzu izolasyonu ve izin doğrulama ile güvenli yükleme protokollerini uyguladığını doğrulayın.                                                              |   2    | D/V |
| 9.12.5 | Araç güvenlik değerlendirmelerinin; statik analiz, dinamik test ve güvenlik ekibi incelemesini içeren zorunlu onay kapılarıyla birlikte belgelenmiş onay kriterleri ve SLA gereksinimleri doğrultusunda, yeni sürümler için otomatik olarak tetiklendiğini doğrulayın.             |   3    | D/V |

---

### Referanslar

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

