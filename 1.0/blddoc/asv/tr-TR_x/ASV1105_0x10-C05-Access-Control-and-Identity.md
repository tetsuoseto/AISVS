# C5 Yapay Zeka Bileşenleri ve Kullanıcılar İçin Erişim Kontrolü ve Kimlik Yönetimi

## Kontrol Amacı

AI sistemleri için etkili erişim kontrolü, sağlam kimlik yönetimi, bağlam duyarlı yetkilendirme ve sıfır güven ilkelerine uygun olarak çalışma zamanında yürütmeyi gerektirir; bu kontroller, insanlar, hizmetler ve otonom ajanların yalnızca açıkça verilen kapsamlar içinde modeller, veriler ve hesaplama kaynaklarıyla etkileşime girmesini sağlar; ayrıca sürekli doğrulama ve denetim yetenekleriyle desteklenir.

---

## C5.1 Kimlik Yönetimi ve Doğrulama

Tüm varlıklar için kriptografik olarak doğrulanabilir kimlikler oluşturun ve yetkili işlemler için çok faktörlü kimlik doğrulama uygulayın.

|   #   | Açıklama                                                                                                                                                                                                                                                                                               | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 5.1.1 | Doğrulayın ki tüm insan kullanıcılar ve hizmet ilkeleri, OIDC/SAML protokollerini kullanarak merkezi kurumsal bir kimlik sağlayıcısı (IdP) üzerinden kimlik doğrulaması gerçekleştirir ve benzersiz kimlikten belirteç eşleşmeleri ile paylaşılan hesaplar veya kimlik bilgilerinin olmaması sağlanır. |   1    | D/V |
| 5.1.2 | Yüksek-riskli işlemlerin (model devreye alınması, ağırlıkların dışa aktarılması, eğitim verilerine erişim, üretim yapılandırması değişiklikleri) çok faktörlü kimlik doğrulama veya oturum yeniden doğrulama ile adımlı kimlik doğrulama gerektirdiğini doğrulayın.                                    |   1    | D/V |
| 5.1.3 | Yeni yetkili kullanıcıların, üretim sistemi erişimini elde etmeden önce NIST 800-63-3 IAL-2 veya buna eşdeğer standartlarla uyumlu bir kimlik kanıtlamasından geçtiğini doğrulayın.                                                                                                                    |   2    |  D  |
| 5.1.4 | Erişim incelemelerinin üç ayda bir gerçekleştirilmesini, pasif hesapların otomatik olarak tespit edilmesini, kimlik bilgileri rotasyonunun uygulanmasını ve devre dışı bırakma iş akışlarını doğrulayın.                                                                                               |   2    |  V  |
| 5.1.5 | Federasyonel yapay zeka ajanları, imzalanmış JWT iddiaları aracılığıyla kimlik doğrulaması yapar; bu iddialar en fazla 24 saatlik yaşam süresine sahiptir ve kaynağın kriptografik kanıtını içerir.                                                                                                    |   3    | D/V |

---

## C5.2 Kaynak Yetkilendirme ve En Az Yetki Prensibi

Tüm AI kaynakları için ince ayrıntılı erişim kontrollerini açık izin modelleriyle ve denetim izleriyle uygulayın.

|   #   | Açıklama                                                                                                                                                                                                                                                  | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.2.1 | Her bir AI kaynağı için (veri kümeleri, modeller, uç noktalar, vektör koleksiyonları, gömme indeksleri, hesaplama örnekleri) rol tabanlı erişim kontrollerinin açık izin listeleri ve varsayılan reddetme politikaları ile uygulanmasını doğrulayın.      |   1    | D/V |
| 5.2.2 | En az ayrıcalık ilkelerinin varsayılan olarak uygulanığını doğrulayın; hizmet hesaplarının başlangıçta yalnızca okuma izinleriyle başlaması ve yazma erişimi için belgelenmiş bir iş gerekçesinin gerekli olması.                                         |   1    | D/V |
| 5.2.3 | Tüm erişim kontrolü değişikliklerinin onaylı değişiklik isteklerine bağlı olduğunu ve zaman damgaları, aktör kimlikleri, kaynak tanımlayıcıları ve izin değişiklikleri ile değiştirilmez biçimde günlüğe kaydedildiğini doğrulayın.                       |   1    |  V  |
| 5.2.4 | Veri sınıflandırma etiketlerinin (PII, PHI, ihracat kontrollü, tescilli) türetilmiş kaynaklara (gömme temsilleri, istem önbellekleri, model çıktıları) otomatik olarak yayıldığını ve bu süreçte tutarlı politika uygulanmasının sağlandığını doğrulayın. |   2    |  D  |
| 5.2.5 | Yetkisiz erişim girişimleri ve yetki yükseltme olaylarının, bağlamsal meta verilerle birlikte, SIEM sistemlerine 5 dakika içinde gerçek zamanlı uyarılar tetiklediğini doğrulayın.                                                                        |   2    | D/V |

---

## C5.3 Dinamik Politika Değerlendirmesi

Bağlam farkındalığına sahip yetkilendirme kararları için özelliklere dayalı erişim kontrolü (ABAC) motorlarını dağıtın ve denetim yetenekleriyle donatın.

|   #   | Açıklama                                                                                                                                                                                                                                                   | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.3.1 | Yetkilendirme kararlarının, kimlik doğrulamalı API'ler üzerinden erişilebilen, kriptografik bütünlük korumasına sahip özel bir politika motoruna (OPA, Cedar veya eşdeğeri) dışa aktarıldığını doğrulayın.                                                 |   1    | D/V |
| 5.3.2 | Politikaların çalışma zamanında dinamik öznitelikleri değerlendirip değerlendirmediğini doğrulayın; bunlar arasında kullanıcı yetki seviyesi, kaynak hassasiyeti sınıflandırması, istek bağlamı, kiracı izolasyonu ve zamansal kısıtlamalar bulunmaktadır. |   1    | D/V |
| 5.3.3 | Politika tanımlarının üretime dağıtımdan önce sürüm kontrollü, akran incelemesine tabi ve otomatik testlerle CI/CD süreçlerinde doğrulanmış olduğundan emin olun.                                                                                          |   2    |  D  |
| 5.3.4 | Politika değerlendirme sonuçlarının yapılandırılmış karar gerekçelerini içerdiğini ve bu sonuçların SIEM sistemlerine korelasyon analizi ve uyum raporlaması için iletildiğini doğrulayın.                                                                 |   2    |  V  |
| 5.3.5 | Politika önbelleği yaşam süresi (TTL) değerlerinin yüksek hassasiyetli kaynaklar için 5 dakikayı aşmaması ve önbellek geçersizleştirme özelliğine sahip standart kaynaklar için 1 saati aşmaması gerektiğini doğrulayın.                                   |   3    | D/V |

---

## C5.4 Sorgu Zamanı Güvenlik Uygulaması

Veritabanı katmanı güvenlik kontrollerini zorunlu filtreleme ve satır düzeyi güvenlik politikaları ile uygulayın.

|   #   | Açıklama                                                                                                                                                                                                                                                                     | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.4.1 | Tüm vektör veritabanları ve SQL sorgularının, veritabanı motoru düzeyinde zorunlu güvenlik filtrelerini (kiracı kimliği, hassasiyet etiketleri, kullanıcı kapsamı) içermesini ve bu filtrelerin uygulama kodunda değil veritabanı motoru düzeyinde uygulanmasını doğrulayın. |   1    | D/V |
| 5.4.2 | Satır seviyesi güvenlik (RLS) politikalarının ve alan düzeyinde maskelemenin politika kalıtımı ile etkinleştirildiğini tüm vektör veritabanları, arama indeksleri ve eğitim veri kümeleri için doğrulayın.                                                                   |   1    | D/V |
| 5.4.3 | Başarısız yetkilendirme değerlendirmelerinin, sorguları derhal iptal ederek ve boş sonuç kümeleri döndürmek yerine açık yetkilendirme hata kodları döndürerek 'confused deputy attacks' olarak bilinen saldırıları önleyeceğini doğrulayın.                                  |   2    |  D  |
| 5.4.4 | Politika değerlendirme gecikmesinin yetkilendirme atlamasına yol açabilecek zaman aşımı durumları için otomatik uyarılarla sürekli olarak izlendiğini doğrulayın.                                                                                                            |   2    |  V  |
| 5.4.5 | Sorgu yeniden deneme mekanizmalarının, aktif kullanıcı oturumları süresince dinamik izin değişikliklerini hesaba katarak yetkilendirme politikalarını yeniden değerlendirdiğini doğrulayın.                                                                                  |   3    | D/V |

---

## C5.5 Çıktı Filtreleme ve Veri Kaybı Önleme

Yapay zeka tarafından üretilen içeriklerde yetkisiz veri ifşasını önlemek için son işlem kontrollerini devreye alın.

|   #   | Açıklama                                                                                                                                                                                                                 | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 5.5.1 | İstek sahiplerine içerik iletilmeden önce, çıkarım sonrası filtreleme mekanizmalarının yetkisiz Kişisel Tanımlanabilir Bilgiler (PII), sınıflandırılmış bilgiler ve tescilli verileri tarayıp sansürlediğini doğrulayın. |   1    | D/V |
| 5.5.2 | Model çıktılarındaki alıntıların, referansların ve kaynak atıflarının çağıranların yetkileriyle doğrulandığını ve yetkisiz erişim tespit edildiğinde kaldırıldığını doğrulayın.                                          |   1    | D/V |
| 5.5.3 | Çıktı biçimi sınırlamalarının (temizlenmiş PDF'ler, meta verileri kaldırılmış görüntüler, onaylı dosya türleri) kullanıcı izin seviyelerine ve veri sınıflandırmalarına göre uygulanıp uygulanmadığını doğrulayın.       |   2    |  D  |
| 5.5.4 | Karartma algoritmalarının deterministik olduğundan, sürüm kontrollü olduğundan ve uyum incelemeleri ile adli analizleri desteklemek için denetim günlükleri tuttuğundan emin olun.                                       |   2    |  V  |
| 5.5.5 | Yüksek riskli redaksiyon olaylarının, adli inceleme için veri sızdırılmadan orijinal içeriğin kriptografik hash değerlerini içeren adaptif günlükler ürettiğini doğrulayın.                                              |   3    |  V  |

---

## C5.6 Çoklu-Kiracı İzolasyonu

Paylaşılan yapay zeka altyapısında kiracılar arasında kriptografik ve mantıksal izolasyonu sağlayın.

|   #   | Açıklama                                                                                                                                                                                                                           | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.6.1 | Kiracı başına isim alanına göre ayrıştırılmış bellek alanları, gömme depoları, önbellek girdileri ve geçici dosyaların, kiracı silindiğinde veya oturum sonlandırıldığında güvenli silme işlemi ile temizlendiğini doğrulayın.     |   1    | D/V |
| 5.6.2 | Her API isteğinin, oturum bağlamına ve kullanıcı yetkilendirmelerine karşı kriptografik olarak doğrulanmış bir kiracı tanımlayıcısını içerdiğini doğrulayın.                                                                       |   1    | D/V |
| 5.6.3 | Service mesh'leri ve konteyner orkestrasyon platformları içinde çapraz kiracı iletişimi için ağ politikalarının varsayılan reddetme kurallarını uyguladığını doğrulayın.                                                           |   2    |  D  |
| 5.6.4 | Her kiracı için benzersiz şifreleme anahtarlarının mevcut olduğundan emin olun; CMK (müşteri tarafından yönetilen anahtar) desteği ile kiracıların veri depolama alanları arasında kriptografik izolasyon sağlandığını doğrulayın. |   3    |  D  |

---

## C5.7 Otonom Ajan Yetkilendirmesi

AI ajanları ve otonom sistemler için izinleri, kapsamlı yetenek belirteçleri ve sürekli yetkilendirme yoluyla yönetin.

|   #   | Açıklama                                                                                                                                                                                                                         | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.7.1 | Otonom ajanların, izin verilen eylemleri, erişilebilir kaynakları, zaman sınırlarını ve operasyonel kısıtlamaları açıkça sıralayan kapsama sahip yetki belirteçleri aldıklarını doğrulayın.                                      |   1    | D/V |
| 5.7.2 | Yüksek riskli yetenekler (dosya sistemi erişimi, kod çalıştırma, harici API çağrıları, finansal işlemler) varsayılan olarak devre dışı bırakılmıştır ve etkinleştirme için işletme gerekçeleriyle açık yetkilendirme gerektirir. |   1    | D/V |
| 5.7.3 | Kullanıcı oturumlarına bağlı olduklarını doğrulayın, kriptografik bütünlük korumasını içermesini sağlayın ve bunların çevrimdışı senaryolarda kalıcı olarak saklanamayacağını veya yeniden kullanılamayacağını garanti edin.     |   2    |  D  |
| 5.7.4 | Ajan tarafından başlatılan eylemlerin ABAC politika motoru üzerinden tam bağlam değerlendirmesiyle ve denetim kayıtlarıyla ikincil yetkilendirmeden geçtiğini doğrulayın.                                                        |   2    |  V  |
| 5.7.5 | Ajanın hata durumları ve istisna işlemesinin kapsama alanı bilgisini içerdiğini doğrulayın; bu, olay analizi ve adli soruşturmayı destekler.                                                                                     |   3    |  V  |

---

## Kaynaklar

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
### AI-Özel Güvenlik

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

