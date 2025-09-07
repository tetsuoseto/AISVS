# C5 AI Bileşenleri ve Kullanıcıları için Erişim Kontrolü ve Kimlik

## Kontrol Amacı

Yapay zeka sistemleri için etkili erişim kontrolü, sağlam kimlik yönetimi, bağlam farkındalığına sahip yetkilendirme ve sıfır güven ilkelerine uygun çalışma zamanı denetimini gerektirir. Bu kontroller, insanların, servislerin ve otonom ajanların yalnızca açıkça verilen kapsamlar içinde modellerle, verilerle ve hesaplama kaynaklarıyla etkileşimde bulunmasını sağlar ve sürekli doğrulama ile denetim yeteneklerini içerir.

---

## C5.1 Kimlik Yönetimi ve Doğrulama

Tüm varlıklar için ayrıcalıklı işlemlerde çok faktörlü kimlik doğrulama ile kriptografik olarak desteklenen kimlikler oluşturun.

|   #   | Açıklama                                                                                                                                                                                                                                                                     | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.1.1 | Tüm insan kullanıcıların ve hizmet ilkelerinin, benzersiz kimlik-tenkü tokan eşlemeleriyle (paylaşılan hesaplar veya kimlik bilgileri olmadan) OIDC/SAML protokolleri kullanarak merkezi bir kurumsal kimlik sağlayıcısı (IdP) aracılığıyla kimlik doğrulamasını doğrulayın. |   1    | D/V |
| 5.1.2 | Yüksek riskli işlemlerin (model dağıtımı, ağırlık ihracı, eğitim verisi erişimi, üretim yapılandırma değişiklikleri) çok faktörlü kimlik doğrulama veya oturum yeniden doğrulaması ile adım yükseltme kimlik doğrulaması gerektirdiğini doğrulayın.                          |   1    | D/V |
| 5.1.3 | Yeni yöneticilerin, üretim sistemi erişimi almadan önce NIST 800-63-3 IAL-2 veya eşdeğer standartlara uygun kimlik doğrulamasından geçtiğini doğrulayın.                                                                                                                     |   2    |  D  |
| 5.1.4 | Erişim incelemelerinin, otomatik olarak atıl hesapların tespiti, kimlik bilgisi döndürme zorunluluğu ve kullanım dışı bırakma iş akışları ile üç ayda bir yapıldığını doğrulayın.                                                                                            |   2    |  V  |
| 5.1.5 | Federated AI ajanlarının, maksimum 24 saatlik bir süreye sahip ve kökenin kriptografik kanıtını içeren imzalı JWT beyanları aracılığıyla kimlik doğrulaması yaptığını doğrulayın.                                                                                            |   3    | D/V |

---

## C5.2 Kaynak Yetkilendirmesi ve Asgari Ayrıcalık

Tüm AI kaynakları için açık izin modelleri ve denetim izleriyle ayrıntılı erişim kontrolleri uygulayın.

|   #   | Açıklama                                                                                                                                                                                                                                       | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.2.1 | Her AI kaynağının (veri setleri, modeller, uç noktalar, vektör koleksiyonları, gömme dizinleri, hesaplama örnekleri) açık izin listeleri ve varsayılan reddetme politikalarıyla rol tabanlı erişim kontrollerini zorunlu kıldığını doğrulayın. |   1    | D/V |
| 5.2.2 | Hizmet hesaplarında en az ayrıcalık prensiplerinin varsayılan olarak uygulandığını, izinlerin okuma-eşliğinde başladığını ve yazma erişimi için belgelenmiş iş gerekçesinin gerektiğini doğrulayın.                                            |   1    | D/V |
| 5.2.3 | Tüm erişim kontrolü değişikliklerinin onaylanmış değişiklik taleplerine bağlı olduğunu ve zaman damgaları, işlemci kimlikleri, kaynak tanımlayıcıları ve izin farkları ile değiştirilemez biçimde kaydedildiğini doğrulayın.                   |   1    |  V  |
| 5.2.4 | Veri sınıflandırma etiketlerinin (KİB, PHI, ihracat kontrollü, özel) türetilmiş kaynaklara (gömülü veriler, komut önbellekleri, model çıktıları) otomatik olarak yayıldığını ve tutarlı politika uygulamasının sağlandığını doğrulayın.        |   2    |  D  |
| 5.2.5 | Yetkisiz erişim girişimleri ve ayrıcalık yükseltme olaylarının, bağlamsal meta verilerle birlikte 5 dakika içinde SIEM sistemlerine gerçek zamanlı uyarılar tetiklediğini doğrulayın.                                                          |   2    | D/V |

---

## C5.3 Dinamik Politika Değerlendirmesi

Denetim yeteneklerine sahip bağlam farkındalıklı yetkilendirme kararları için öznitelik tabanlı erişim kontrolü (ABAC) motorlarını dağıtın.

|   #   | Açıklama                                                                                                                                                                                                                     | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.3.1 | Yetkilendirme kararlarının, kimlik doğrulamalı API’ler aracılığıyla erişilebilen ve kriptografik bütünlük korumasına sahip özel bir politika motoruna (OPA, Cedar veya eşdeğeri) dış kaynaklı olarak verildiğini doğrulayın. |   1    | D/V |
| 5.3.2 | Politikaların kullanıcı yetki seviyesi, kaynak hassasiyeti sınıflandırması, istek bağlamı, kiracı izolasyonu ve zamansal kısıtlamalar gibi dinamik öznitelikleri çalışma zamanında değerlendirdiğini doğrulayın.             |   1    | D/V |
| 5.3.3 | Politika tanımlarının sürüm kontrolü yapıldığını, eş düzey incelemesinden geçtiğini ve üretim dağıtımı öncesinde CI/CD boru hatlarında otomatik testlerle doğrulandığını teyit edin.                                         |   2    |  D  |
| 5.3.4 | Politika değerlendirme sonuçlarının yapılandırılmış karar gerekçelerini içerdiğini ve korelasyon analizi ile uyumluluk raporlaması için SIEM sistemlerine iletildiğini doğrulayın.                                           |   2    |  V  |
| 5.3.5 | Politika önbellek zaman aşımı (TTL) değerlerinin, yüksek hassasiyetli kaynaklar için 5 dakikayı ve önbellek geçersiz kılma özelliklerine sahip standart kaynaklar için 1 saati aşmadığını doğrulayın.                        |   3    | D/V |

---

## C5.4 Sorgu Zamanı Güvenlik Uygulaması

Zorunlu filtreleme ve satır düzeyinde güvenlik politikaları ile veritabanı katmanı güvenlik kontrolleri uygulayın.

|   #   | Açıklama                                                                                                                                                                                                           | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 5.4.1 | Tüm vektör veritabanı ve SQL sorgularının, uygulama kodu değil, veritabanı motoru seviyesinde zorunlu güvenlik filtrelerini (kiracı kimliği, hassasiyet etiketleri, kullanıcı kapsamı) içerdiğini doğrulayın.      |   1    | D/V |
| 5.4.2 | Tüm vektör veritabanları, arama indeksleri ve eğitim veri kümeleri için politika devralma ile satır seviyesi güvenlik (RLS) politikalarının ve alan seviyesi maskelenmenin etkin olduğundan emin olun.             |   1    | D/V |
| 5.4.3 | Başarısız yetkilendirme değerlendirmelerinin, sorguları hemen sonlandırarak ve boş sonuç kümeleri döndürmek yerine açık yetkilendirme hata kodları vererek "karışmış vekil saldırılarını" önleyeceğini doğrulayın. |   2    |  D  |
| 5.4.4 | Politika değerlendirme gecikmesinin, yetkilendirme atlamasına olanak tanıyabilecek zaman aşımı durumları için otomatik uyarılarla sürekli olarak izlenip izlenmediğini doğrulayın.                                 |   2    |  V  |
| 5.4.5 | Sorgu yeniden deneme mekanizmalarının, aktif kullanıcı oturumları içinde dinamik izin değişikliklerini dikkate almak için yetkilendirme politikalarını yeniden değerlendirdiğini doğrulayın.                       |   3    | D/V |

---

## C5.5 Çıktı Filtreleme ve Veri Kayıp Önleme

İzinsiz veri açığa çıkmasını önlemek için AI tarafından oluşturulan içerikte son işlem kontrolü uygulayın.

|   #   | Açıklama                                                                                                                                                                                             | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.5.1 | İçeriği talep edenlere sunmadan önce, çıkarım sonrası filtreleme mekanizmalarının yetkisiz KİT, sınıflandırılmış bilgiler ve özel verileri tarayıp sansürlediğini doğrulayın.                        |   1    | D/V |
| 5.5.2 | Model çıktılarındaki atıfların, referansların ve kaynak atıflarının çağıran hakları ile doğrulandığını ve yetkisiz erişim tespit edilirse kaldırıldığını doğrulayın.                                 |   1    | D/V |
| 5.5.3 | Kullanıcı izin seviyelerine ve veri sınıflandırmalarına göre çıktı formatı kısıtlamalarının (temizlenmiş PDF'ler, meta verisi kaldırılmış görseller, onaylı dosya türleri) uygulandığını doğrulayın. |   2    |  D  |
| 5.5.4 | Kırpma algoritmalarının deterministik, sürüm kontrollü olduğunu ve uyum soruşturmalarını ve adli analizleri desteklemek için denetim günlüklerini tuttuğunu doğrulayın.                              |   2    |  V  |
| 5.5.5 | Yüksek riskli sansürleme olaylarının, veri maruziyeti olmaksızın adli inceleme için orijinal içeriğin kriptografik özetlerini içeren uyarlanabilir günlükler oluşturduğunu doğrulayın.               |   3    |  V  |

---

## C5.6 Çok Kiracılı İzolasyon

Paylaşılan yapay zeka altyapısında kiracılar arasında kriptografik ve mantıksal izolasyonu sağlayın.

|   #   | Açıklama                                                                                                                                                                                                                                         | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 5.6.1 | Bellek alanlarının, gömme depolarının, önbellek girdilerinin ve geçici dosyaların, kiracı başına ad alanı ayrılmış şekilde olduğunu doğrulayın ve kiracı silindiğinde veya oturum sonlandırıldığında güvenli şekilde temizlendiğinden emin olun. |   1    | D/V |
| 5.6.2 | Her API isteğinin, oturum bağlamı ve kullanıcı yetkilerine karşı kriptografik olarak doğrulanan kimlik doğrulanmış bir kiracı tanımlayıcısı içerdiğini doğrulayın.                                                                               |   1    | D/V |
| 5.6.3 | Ağ politikalarının hizmet dokuları ve konteyner orkestra platformları içinde kiracılar arası iletişim için varsayılan reddetme kuralları uyguladığını doğrulayın.                                                                                |   2    |  D  |
| 5.6.4 | Müşteri tarafından yönetilen anahtar (CMK) desteği ve kiracı veri depoları arasında kriptografik izolasyon ile şifreleme anahtarlarının her kiracı için benzersiz olduğunu doğrulayın.                                                           |   3    |  D  |

---

## C5.7 Otonom Ajan Yetkilendirmesi

Kapsamlı yetenek jetonları ve sürekli yetkilendirme yoluyla yapay zeka ajanları ve otonom sistemler için kontrol izinleri.

|   #   | Açıklama                                                                                                                                                                                                                               | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.7.1 | Otonom ajanların, izin verilen eylemleri açıkça listeleyen, erişilebilir kaynakları, zaman sınırlarını ve operasyonel kısıtlamaları içeren kapsamlı yetki belirteçleri aldığını doğrulayın.                                            |   1    | D/V |
| 5.7.2 | Yüksek riskli yeteneklerin (dosya sistemi erişimi, kod yürütme, harici API çağrıları, finansal işlemler) varsayılan olarak devre dışı bırakıldığını ve etkinleştirilmesi için iş gerekçeleriyle açık onayların gerektiğini doğrulayın. |   1    | D/V |
| 5.7.3 | Yetenek belirteçlerinin kullanıcı oturumlarına bağlı olduğunu doğrulayın, kriptografik bütünlük koruması içermesini sağlayın ve çevrimdışı senaryolarda saklanamaması veya yeniden kullanılamaması gerektiğini garanti edin.           |   2    |  D  |
| 5.7.4 | Ajan tarafından başlatılan eylemlerin, tam bağlam değerlendirmesi ve denetim kaydı ile ABAC politika motoru aracılığıyla ikincil yetkilendirmeye tabi tutulduğunu doğrulayın.                                                          |   2    |  V  |
| 5.7.5 | Ajan hata durumları ve istisna yönetiminin, olay analizi ve adli inceleme desteği sağlamak için yetenek kapsamı bilgilerini içerdiğini doğrulayın.                                                                                     |   3    |  V  |

---

## Referanslar

### Standartlar ve Çerçeveler

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Uygulama Kılavuzları

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Yapay Zeka'ya Özgü Güvenlik

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

