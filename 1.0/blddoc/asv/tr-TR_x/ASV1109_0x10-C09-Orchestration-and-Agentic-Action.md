# 9 Otonom Orkestrasyon ve Ajanik Eylem Güvenliği

## Kontrol Amacı

Otonom veya çok ajanlı yapay zeka sistemlerinin yalnızca açıkça amaçlanan, kimlik doğrulanmış, denetlenebilir ve sınırlı maliyet ve risk eşiklerinin sınırları içinde eylemler gerçekleştirmesini sağlayın. Bu, şu tehditlere karşı korunmayı sağlar: Otonom Sistemlerin Ele Geçirilmesi, Araçların Kötüye Kullanımı, Ajan Döngüsü Tespiti, İletişimin Ele Geçirilmesi, Kimlik Sahteciliği, Sürü Manipülasyonu ve Niyet Manipülasyonu.

---

## 9.1 Ajan Görev-Planlama ve Özyineleme Bütçeleri

Özyinelemeli planları kısıtla ve yetkili işlemler için insan kontrol noktalarını zorunlu kıl.

|   #   | Açıklama                                                                                                                                                                               | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.1.1 | Maksimum özyineleme derinliği, genişlik, gerçek zaman süresi, tokenlar ve ajan başına yürütme maliyetinin merkezi olarak yapılandırıldığı ve sürüm kontrollü olduğunun doğrulanması.   |   1    | D/V |
| 9.1.2 | Yetkili veya geri alınamaz işlemlerin (örneğin kod değişiklikleri, finansal transferler) yürütülmeden önce izlenebilir bir kanal üzerinden açık insan onayının gerektiğini doğrulayın. |   1    | D/V |
| 9.1.3 | Herhangi bir bütçe eşiği aşıldığında gerçek zamanlı kaynak izleyicilerinin devre kesici kesintisini tetiklediğini doğrulayın; bu, daha fazla görevin genişletilmesini durdurur.        |   2    |  D  |
| 9.1.4 | Devre kesici olaylarının adli inceleme için ajan kimliği, tetikleyici koşul ve yakalanmış plan durumu ile kaydedildiğini doğrulayın.                                                   |   2    | D/V |
| 9.1.5 | Güvenlik testlerinin bütçe tükenmesi ve kontrolden çıkmış plan senaryolarını kapsadığından emin olun ve veri kaybı olmadan güvenli bir şekilde durdurulduğunu doğrulayın.              |   3    |  V  |
| 9.1.6 | Bütçe politikalarının policy-as-code olarak ifade edildiğini ve CI/CD'de uygulanarak yapılandırma sapmasının engellendiğini doğrulayın.                                                |   3    |  D  |

---

## 9.2 Araç Eklenti İzolaması

İzinsiz sistem erişimini veya kod çalıştırmayı önlemek için araç etkileşimlerini izole edin.

|   #   | Açıklama                                                                                                                                                                                                                            | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.2.1 | Her araç/eklentiğin İşletim Sistemi (OS), konteyner veya WASM düzeyinde bir sandbox içinde çalıştığından emin olun; dosya sistemi, ağ ve sistem çağrısı politikalarının en az ayrıcalık ilkesine uygun şekilde uygulanması gerekir. |   1    | D/V |
| 9.2.2 | Sandbox kaynak kotalarının (CPU, bellek, disk, ağ çıkışı) ve yürütme zaman aşımı sürelerinin uygulanıp kaydedildiğini doğrulayın.                                                                                                   |   1    | D/V |
| 9.2.3 | Araçların ikili dosyaları ve tanımlayıcılarının dijital olarak imzalandığını doğrulayın; imzalar yüklemeden önce doğrulanır.                                                                                                        |   2    | D/V |
| 9.2.4 | Sandbox telemetri akışlarının SIEM'e iletilmesini doğrulayın; anomalilerin (ör. çıkış bağlantı denemeleri) uyarılarının tetiklenmesini doğrulayın.                                                                                  |   2    |  V  |
| 9.2.5 | Yüksek riskli eklentilerin üretim ortamına dağıtılmadan önce güvenlik incelemesi ve sızma testlerinden geçirildiğini doğrulayın.                                                                                                    |   3    |  V  |
| 9.2.6 | Sandbox kaçış girişimlerinin otomatik olarak engellendiğini ve ihlal eden eklentinin inceleme sürerken karantinaya alındığını doğrulayın.                                                                                           |   3    | D/V |

---

## 9.3 Otonom Döngü ve Maliyet Sınırlandırması

Kontrolsüz ajanlar-arası özyinelemeyi ve maliyet patlamalarını tespit edin ve durdurun.

|   #   | Açıklama                                                                                                                                            | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.3.1 | Ajanslar arası çağrıların, çalışma zamanı tarafından azaltılan ve uygulanması gereken bir hop-limit veya TTL içerdiğini doğrulayın.                 |   1    | D/V |
| 9.3.2 | Ajanların kendini çağırmayı veya döngüsel kalıpları tespit etmek için benzersiz bir çağrı-grafiği kimliğini sürdürdüğünü doğrulayın.                |   2    |  D  |
| 9.3.3 | Her istek zinciri için kümülatif hesaplama birimi sayaçlarının ve harcama sayaçlarının izlendiğini doğrulayın; sınır aşıldığında zincir durdurulur. |   2    | D/V |
| 9.3.4 | Formal analiz veya model denetiminin ajan protokollerinde sınırsız özyinelemenin yokluğunu gösterdiğini doğrulayın.                                 |   3    |  V  |
| 9.3.5 | Loop-abort olaylarının uyarılar üretmesini ve sürekli iyileştirme metriklerini beslemesini doğrulayın.                                              |   3    |  D  |

---

## 9.4 Protokol Seviyesinde Kötüye Kullanım Önleme

Ajanlar ile harici sistemler arasındaki güvenli iletişim kanallarını, ele geçirilmesini veya manipülasyonu önlemek için güvence altına alın.

|   #   | Açıklama                                                                                                                                              | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.4.1 | Tüm ajan-araç ve ajan-ajan mesajlarının kimlik doğrulamasının yapıldığını (örneğin karşılıklı TLS veya JWT) ve uçtan uca şifreli olduğunu doğrulayın. |   1    | D/V |
| 9.4.2 | Şemaların katı biçimde doğrulandığını doğrulayın; bilinmeyen alanlar veya hatalı biçimlendirilmiş iletiler reddedilir.                                |   1    |  D  |
| 9.4.3 | Bütünlük kontrollerinin (MAC'ler veya dijital imzalar) tüm mesaj yükünü, araç parametreleri dahil olmak üzere, kapsadığını doğrulayın.                |   2    | D/V |
| 9.4.4 | Protokol katmanında yeniden oynatma korumasının (nonce'lar veya zaman damgası pencereleri) uygulanmış olduğundan emin olun.                           |   2    |  D  |
| 9.4.5 | Protokol uygulamalarının enjeksiyon veya deserileştirme hataları için fuzzing ve statik analizden geçirildiğini doğrulayın.                           |   3    |  V  |

---

## 9.5 Ajan Kimliği ve Tahrifat Kanıtı

Eylemler atfedilebilir olmalı ve değişiklikler tespit edilebilir olmalıdır.

|   #   | Açıklama                                                                                                                                 | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.5.1 | Her bir ajan örneğinin benzersiz bir kriptografik kimliğe sahip olduğunu doğrulayın (anahtar çifti veya donanım tabanlı kimlik bilgisi). |   1    | D/V |
| 9.5.2 | Tüm ajan eylemlerinin imzalanıp zaman damgası alındığını doğrulayın; günlükler reddedilemezlik için imzayı içermelidir.                  |   2    | D/V |
| 9.5.3 | Tamper-evident günlüklerin yalnızca eklenebilir veya bir kez yazılabilir bir ortamda saklandığından emin olun.                           |   2    |  V  |
| 9.5.4 | Kimlik anahtarlarının belirlenen bir takvime göre ve ihlal göstergelerinde rotasyona uğradığını doğrulayın.                              |   3    |  D  |
| 9.5.5 | Kimlik sahteciliği veya anahtar çakışması girişimlerinin, etkilenen ajanın derhal karantinaya alınmasını tetiklediğini doğrulayın.       |   3    | D/V |

---

## 9.6 Çok-Ajanlı Sürü Risk Azaltma

İzolasyon ve biçimsel güvenlik modellemesi yoluyla kolektif-davranış tehlikelerini azaltın.

|   #   | Açıklama                                                                                                                                                               | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.6.1 | Farklı güvenlik alanlarında çalışan ajanların izole çalışma zamanı sandbox'larında veya ağ segmentlerinde yürütüldüğünden emin olun.                                   |   1    | D/V |
| 9.6.2 | Dağıtımdan önce sürü davranışlarının modellenip yaşamsallık ve güvenlik açısından resmen doğrulandığından emin olun.                                                   |   3    |  V  |
| 9.6.3 | Çalışma zamanı izleyicilerinin ortaya çıkan güvenli olmayan desenleri (ör. salınımlar, kilitlenmeler) tespit ettiğini ve düzeltici önlemleri başlatacağını doğrulayın. |   3    |  D  |

---

## 9.7 Kullanıcı ve Araç Kimlik Doğrulama / Yetkilendirme

Her ajan tarafından tetiklenen her eylem için sağlam erişim kontrolleri uygulayın.

|   #   | Açıklama                                                                                                                                                                            | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.7.1 | Ajanların alt sistemlere karşı birinci sınıf prensipler olarak kimlik doğrulaması yaptığını doğrulayın; son kullanıcı kimlik bilgilerinin asla yeniden kullanılmadığını doğrulayın. |   1    | D/V |
| 9.7.2 | İnce ayrıntılı yetkilendirme politikalarının bir ajanın hangi araçları çağırabileceğini ve hangi parametreleri sunabileceğini kısıtladığını doğrulayın.                             |   2    |  D  |
| 9.7.3 | Yetki kontrollerinin her çağrıda yeniden değerlendirildiğini (sürekli yetkilendirme) doğrulayın; yalnızca oturum başlangıcında değil.                                               |   2    |  V  |
| 9.7.4 | Devredilen yetkilerin otomatik olarak süresinin dolduğunu ve zaman aşımı veya kapsam değişikliği sonrasında yeniden onay gerektirdiğini doğrulayın.                                 |   3    |  D  |

---

## 9.8 Ajanlar Arası İletişim Güvenliği

Tüm ajanlar-arası mesajları şifreleyin ve bütünlüklerini koruyun; böylece dinlemeyi ve müdahaleyi engelleyin.

|   #   | Açıklama                                                                                                                                                          | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.8.1 | Agent kanalları için karşılıklı kimlik doğrulamanın ve mükemmel ileriye dönük gizlilik içeren şifrelemenin (örn. TLS 1.3) zorunlu olduğunun doğrulanması gerekir. |   1    | D/V |
| 9.8.2 | İşleme öncesinde mesaj bütünlüğünün ve kaynağının doğrulandığından emin olun; doğrulama başarısız olduğunda uyarılar tetiklenir ve mesaj reddedilir.              |   1    |  D  |
| 9.8.3 | İletişim meta verisinin (zaman damgaları, sıra numaraları) adli bilişim yeniden yapılandırmasını desteklemek amacıyla kaydedildiğini doğrulayın.                  |   2    | D/V |
| 9.8.4 | Protokol durum makinelerinin güvenli olmayan durumlara sürüklenemeyeceğini, formal doğrulama veya model denetimi ile doğrulandığını teyit edin.                   |   3    |  V  |

---

## 9.9 Niyet Doğrulaması ve Kısıtlamaların Uygulanması

Ajanın eylemlerinin kullanıcının beyan ettiği amacı ve sistem kısıtlarıyla uyumlu olduğunu doğrulayın.

|   #   | Açıklama                                                                                                                                                                      | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.9.1 | Ön yürütme kısıtlama çözücülerinin önerilen eylemleri sert kodlanmış güvenlik ve politika kurallarına göre kontrol ettiğini doğrulayın.                                       |   1    |  D  |
| 9.9.2 | Yüksek etkiye sahip işlemlerin (finansal, yıkıcı, gizlilik açısından hassas) başlatan kullanıcıdan açık niyet teyidi gerektirdiğini doğrulayın.                               |   2    | D/V |
| 9.9.3 | Tamamlanan eylemlerin amaçlanan etkileri elde ettiğini ve yan etkilerin olmadığını doğrulayan son durum koşullarını kontrol edin; tutarsızlıklar geri alma işlemini tetikler. |   2    |  V  |
| 9.9.4 | Ajan planlarının tüm açıklanan kısıtlamaları karşıladığını gösteren formal yöntemler (ör. model kontrolü, teorem ispatı) veya özellik tabanlı testler ile doğrulayın.         |   3    |  V  |
| 9.9.5 | Intent-mismatch veya constraint-violation olaylarının continuous-improvement döngülerini ve threat-intel paylaşımını beslediğini doğrulayın.                                  |   3    |  D  |

---

## 9.10 Ajan akıl yürütme stratejisi güvenlik

ReAct, Chain-of-Thought ve Tree-of-Thoughts yaklaşımlarını içeren farklı akıl yürütme stratejilerinin güvenli seçimi ve uygulanması.

|   #    | Açıklama                                                                                                                                                                                                                                    | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.10.1 | Akıl yürütme stratejisi seçiminin deterministik kriterlere dayandığını doğrulayın; girdi karmaşıklığı, görev türü ve güvenlik bağlamı dahil, aynı güvenlik bağlamında aynı girdiler aynı strateji seçimlerini üretir.                       |   1    | D/V |
| 9.10.2 | Her bir muhakeme stratejisinin (ReAct, Chain-of-Thought, Tree-of-Thoughts) kendi bilişsel yaklaşımına özgü girdi doğrulama, çıktı temizleme ve çalışma süresi sınırlarına sahip olduğundan emin olun.                                       |   1    | D/V |
| 9.10.3 | Denetim izi yeniden oluşturma amacıyla, akıl yürütme stratejisi geçişlerinin tam bağlamla kaydedildiğini doğrulayın; bu bağlam girdi özelliklerini, seçim kriteri değerlerini ve yürütme meta verisini içerir.                              |   2    | D/V |
| 9.10.4 | Düşünce Ağacı akıl yürütmesinin, politika ihlallerinin, kaynak sınırlarının veya güvenlik sınırlarının tespit edildiği durumlarda keşfi sonlandıran dal budama mekanizmalarını içerdiğini doğrulayın.                                       |   2    | D/V |
| 9.10.5 | ReAct (Reason-Act-Observe) döngülerinin her aşamada doğrulama noktalarını içerdiğini doğrulayın: akıl yürütme adımı doğrulaması, eylem yetkilendirmesi ve gözlem sanitizasyonunun ilerlemeden önce yapılması.                               |   2    | D/V |
| 9.10.6 | Çalıştırma süresi, kaynak kullanımı ve çıktı kalitesi gibi akıl yürütme stratejisinin performans ölçütlerinin yapılandırılmış eşiklerin ötesine çıktığında otomatik uyarılarla izlendiğini doğrulayın.                                      |   3    | D/V |
| 9.10.7 | Birden çok stratejiyi birleştiren hibrit akıl yürütme yaklaşımlarının, tüm bileşen stratejilerinin giriş doğrulamasını ve çıktı kısıtlamalarını koruduğunu ve hiçbir güvenlik kontrolünü atlatmadığını doğrulayın.                          |   3    | D/V |
| 9.10.8 | Akıl yürütme stratejisi güvenlik testlerinin bozuk girdilerle fuzzing içerdiğini, strateji değişimini zorlamak için tasarlanmış adversarial promptlar içerdiğini ve her bir bilişsel yaklaşım için sınır durum testi içerdiğini doğrulayın. |   3    | D/V |

---

## 9.11 Ajan Yaşam Döngüsü Durum Yönetimi ve Güvenliği

Güvenli ajan başlatma, durum geçişleri ve sonlandırma, kriptografik denetim izleri ve tanımlanmış kurtarma prosedürleriyle.

|   #    | Açıklama                                                                                                                                                                                                                                                                                             | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.11.1 | Ajının başlatılmasının, donanım destekli kimlik bilgileriyle kriptografik kimliğin oluşturulmasını ve ajan kimliği, zaman damgası, yapılandırma hash değeri ile başlatma parametrelerini içeren değiştirilemez başlangıç denetim günlüklerini kapsamasını doğrulayın.                                |   1    | D/V |
| 9.11.2 | Ajanın durum geçişlerinin kriptografik olarak imzalandığını, zaman damgası ile kaydedildiğini ve tetikleyici olaylar, önceki durum hash değeri, yeni durum hash değeri ve gerçekleştirilen güvenlik doğrulamaları dahil olmak üzere tam bağlamla birlikte loglandığını doğrulayın.                   |   2    | D/V |
| 9.11.3 | Ajan kapatma prosedürlerinin kriptografik silme veya çok geçişli üzerine yazma kullanılarak güvenli bellek temizlemesini içerdiğini, kimlik bilgisi iptalinin sertifika otoritesine bildirimle gerçekleştirilmesini ve tahrifata karşı kanıtlı sonlandırma sertifikalarının üretilmesini doğrulayın. |   2    | D/V |
| 9.11.4 | Ajan kurtarma mekanizmalarının durum bütünlüğünü kriptografik özetler (SHA-256 en az) kullanarak doğruladığını ve bozulma tespit edildiğinde otomatik uyarılar ve manuel onay gereksinimleriyle bilinen güvenli durumlara geri dönmesini sağladığını doğrulayın.                                     |   3    | D/V |
| 9.11.5 | Ajana özgü AES-256 anahtarlarıyla hassas durum verilerini şifreleyen ajanın kalıcılık mekanizmalarını doğrulayın ve yapılandırılabilir zaman çizelgelerinde (maksimum 90 gün) güvenli anahtar rotasyonunu ve sıfır kesintiyle dağıtımı uygulayın.                                                    |   3    | D/V |

---

## 9.12 Araç Entegrasyonu Güvenlik Çerçevesi

Tanımlanmış risk değerlendirme ve onay süreçleriyle dinamik araç yükleme, çalıştırma ve sonuç doğrulaması için güvenlik kontrolleri.

|   #    | Açıklama                                                                                                                                                                                                                                                                                                 | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.12.1 | Araç tanımlayıcılarının güvenlik meta verilerini içerdiğinden emin olun; bu meta verileri, gerekli ayrıcalıkları (okuma/yazma/çalıştırma), risk düzeylerini (düşük/orta/yüksek), kaynak sınırlarını (CPU, bellek, ağ) ve araç manifestolarında belgelenen doğrulama gereksinimlerini belirtir.           |   1    | D/V |
| 9.12.2 | Araç yürütme sonuçlarının beklenen şemalara (JSON Şeması, XML Şeması) ve güvenlik politikalarına (çıktı arındırma, veri sınıflandırması) uygun olduğunun doğrulandığından emin olun ve entegrasyondan önce zaman aşımı sınırları ile hata işleme prosedürleriyle bu doğrulamanın yapıldığını teyit edin. |   1    | D/V |
| 9.12.3 | Araç etkileşim günlüklerinin güvenlik bağlamını ayrıntılı olarak içerdiğini doğrulayın: ayrıcalık kullanımı, veri erişim desenleri, yürütme süresi, kaynak tüketimi ve sonuç kodları gibi öğelerin SIEM entegrasyonu için yapılandırılmış günlüklerle kaydedildiğini sağlayın.                           |   2    | D/V |
| 9.12.4 | Dinamik araç yükleme mekanizmalarının dijital imzaları PKI altyapısını kullanarak doğruladığından emin olun ve çalıştırmadan önce sandbox izolasyonu ile izin doğrulamasını içeren güvenli yükleme protokollerini uygulayın.                                                                             |   2    | D/V |
| 9.12.5 | Yeni sürümler için zorunlu onay kapılarıyla otomatik olarak tetiklenen araç güvenlik değerlendirmelerinin, statik analiz, dinamik testler ve güvenlik ekibi incelemesi dahil olmak üzere belgelendirilmiş onay kriterleri ve SLA gereksinimleriyle birlikte tetiklenmesini doğrulayın.                   |   3    | D/V |

---

### Kaynaklar

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

