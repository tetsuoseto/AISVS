# C8 Bellek, Gömülü Temsiller ve Vektör Veritabanı Güvenliği

## Kontrol Amacı

Embeddingler ve vektör mağazaları, çağdaş yapay zeka sistemlerinin "canlı belleği" olarak işlev görür, kullanıcı tarafından sağlanan verileri sürekli kabul eder ve bunları Retrieval-Augmented Generation (RAG) aracılığıyla model bağlamlarına geri getirir. Yönetilmezse, bu bellek kişisel olarak tanımlanabilir bilgilerin (PII) sızmasına, onay ihlaline veya orijinal metnin yeniden yapılandırılması için tersine çevrilmesine neden olabilir. Bu kontrol ailesinin amacı, bellek boru hatlarını ve vektör veritabanlarını güçlendirmek, erişimin en az ayrıcalıklı olmasını sağlamak, embeddinglerin gizliliği korumasını temin etmek, depolanan vektörlerin süresinin dolmasını veya talep üzerine iptal edilmesini sağlamak ve kullanıcı başına belleğin asla başka bir kullanıcının istemlerini veya tamamlamalarını kirletmemesini sağlamaktır.

---

## C8.1 Bellek ve RAG İndekslerinde Erişim Kontrolleri

Her vektör koleksiyonunda ince taneli erişim kontrollerini zorunlu kılın.

|   #   | Açıklama                                                                                                                                                                | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.1.1 | Satır/isim alanı düzeyindeki erişim kontrol kurallarının, kiracı, koleksiyon veya belge etiketi başına ekleme, silme ve sorgulama işlemlerini kısıtladığını doğrulayın. |   1    | D/V |
| 8.1.2 | API anahtarları veya JWT'lerin kapsamlı iddialar (örneğin, koleksiyon kimlikleri, işlem fiilleri) taşıdığını ve en az üç ayda bir döndürüldüğünü doğrulayın.            |   1    | D/V |
| 8.1.3 | Ayrıcalık yükseltme girişimlerinin (örneğin, alan adları arasında benzerlik sorguları) tespit edildiği ve 5 dakika içinde bir SIEM'e kaydedildiği doğrulanmalıdır.      |   2    | D/V |
| 8.1.4 | Vektör veritabanı denetimlerinin günlüklerinde konu tanımlayıcı, işlem, vektör kimliği/isim alanı, benzerlik eşiği ve sonuç sayısını doğrulayın.                        |   2    | D/V |
| 8.1.5 | Motorlar yükseltildiğinde veya indeks-parçalama kuralları değiştiğinde, erişim kararlarının atlama açıkları için test edildiğini doğrulayın.                            |   3    |  V  |

---

## C8.2 Gömme Temizleme ve Doğrulama

Vektörleştirmeden önce metni Kişisel Tanımlanabilir Bilgiler (PII) için ön taramadan geçir, karart veya takma ad kullan ve isteğe bağlı olarak kalıntı sinyalleri kaldırmak için gömülü temsilleri (embedding) son işlemden geçir.

|   #   | Açıklama                                                                                                                                                                                                                                         | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 8.2.1 | Kişisel Tanımlayıcı Bilgilerin (PII) ve düzenlemeye tabi verilerin otomatik sınıflandırıcılar aracılığıyla tespit edilip maskeleme, tokenleştirme veya gömme öncesi çıkarma işlemlerinin yapıldığını doğrulayın.                                 |   1    | D/V |
| 8.2.2 | Gömülü işleme hatlarının, dizini zehirleyebilecek çalıştırılabilir kod veya UTF-8 olmayan kalıntılar içeren girdileri reddettiğini veya karantinaya aldığını doğrulayın.                                                                         |   1    |  D  |
| 8.2.3 | Herhangi bir bilinen Kişisel Tanımlanabilir Bilgi (PII) tokenına olan mesafesi yapılandırılabilir bir eşik değerinin altına düşen cümle gömme vektörlerine yerel veya metrik diferansiyel gizlilik temizleme işleminin uygulandığını doğrulayın. |   2    | D/V |
| 8.2.4 | Sanitasyon etkinliğinin (örneğin, KİB düzeltmesinin geri çağrılması, anlamsal kayma) en az altı ayda bir kıyaslama metinleri karşısında doğrulandığından emin olun.                                                                              |   2    |  V  |
| 8.2.5 | Temizleme yapılandırmalarının sürüm kontrolünde olduğunu ve değişikliklerin eşler arası incelemeden geçtiğini doğrulayın.                                                                                                                        |   3    | D/V |

---

## C8.3 Bellek Süresinin Dolması, İptali ve Silinmesi

GDPR "unutulma hakkı" ve benzeri yasalar zamanında silmeyi gerektirir; bu nedenle vektör depolarının, iptal edilen vektörlerin kurtarılamaması veya yeniden indekslenememesi için TTL, kalıcı silme ve mezar taşı (tomb-stoning) desteklemesi gerekir.

|   #   | Açıklama                                                                                                                                                                              | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.3.1 | Her vektör ve meta veri kaydının TTL veya otomatik temizlik işleri tarafından dikkate alınan açık bir saklama etiketi taşıdığını doğrulayın.                                          |   1    | D/V |
| 8.3.2 | Kullanıcı tarafından başlatılan silme taleplerinin, 30 gün içinde vektörleri, meta verileri, önbellek kopyalarını ve türetilmiş indeksleri tamamen temizlediğini doğrulayın.          |   1    | D/V |
| 8.3.3 | Mantıksal silmelerin, donanım destekliyorsa depolama bloklarının kriptografik olarak imha edilmesinden veya anahtar kasası anahtarının yok edilmesinden sonra yapıldığını doğrulayın. |   2    |  D  |
| 8.3.4 | Son kullanma süresi dolmuş vektörlerin, süresi dolduktan sonra < 500 ms içinde en yakın komşu arama sonuçlarından hariç tutulduğunu doğrulayın.                                       |   3    | D/V |

---

## C8.4 Gömme Tersine Çevirme ve Sızıntısını Önleme

Son savunma yöntemleri—gürültü üst üste bindirme, projeksiyon ağları, gizlilik-nöron bozulması ve uygulama katmanı şifrelemesi—token seviyesindeki tersine çevirme oranlarını %5'in altına düşürebilir.

|   #   | Açıklama                                                                                                                                                                             | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 8.4.1 | Tersine çevirme, üyelik ve özellik çıkarımı saldırılarını kapsayan resmi bir tehdit modelinin var olduğunu ve yıllık olarak gözden geçirildiğini doğrulayın.                         |   1    |  V  |
| 8.4.2 | Uygulama katmanı şifrelemesinin veya aranabilir şifrelemenin, vektörleri altyapı yöneticileri veya bulut personeli tarafından doğrudan okunmalardan koruduğunu doğrulayın.           |   2    | D/V |
| 8.4.3 | Savunma parametrelerinin (DP için ε, gürültü σ, projeksiyon rankı k) gizliliği ≥ %99 token koruması ve faydayı ≤ %3 doğruluk kaybı ile dengelediğini doğrulayın.                     |   3    |  V  |
| 8.4.4 | Model güncellemeleri için sürüm kapılarının bir parçası olarak tersine dayanıklılık metriklerinin doğrulandığından emin olun ve regresyon bütçelerinin tanımlı olduğundan emin olun. |   3    | D/V |

---

## C8.5 Kullanıcıya Özel Bellek İçin Kapsam Uygulaması

Çoklu kiracı sızıntısı hâlâ en önemli RAG riskidir: yanlış filtrelenmiş benzerlik sorguları başka bir müşterinin özel belgelerini ortaya çıkarabilir.

|   #   | Açıklama                                                                                                                                                                                   | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 8.5.1 | Her sorgulama sorgusunun LLM istemine iletilmeden önce kiracı/kullanıcı kimliği ile son filtrelemesinin yapıldığını doğrulayın.                                                            |   1    | D/V |
| 8.5.2 | Koleksiyon adlarının veya ad alanlı kimliklerin, vektörlerin kapsamlar arasında çakışmaması için kullanıcıya veya kiracıya göre tuzlandığını doğrulayın.                                   |   1    |  D  |
| 8.5.3 | Benzerlik sonuçlarının, yapılandırılabilir bir mesafe eşiğinin üzerinde ancak çağıranın kapsamı dışında kalması durumunda reddedildiğini ve güvenlik uyarılarını tetiklediğini doğrulayın. |   2    | D/V |
| 8.5.4 | Çok kiracılı stres testlerinin kapsam dışı belgeleri almaya çalışan düşmanca sorguları simüle ettiğini ve sıfır bilgi sızıntısını gösterdiğini doğrulayın.                                 |   2    |  V  |
| 8.5.5 | Şifreleme anahtarlarının her kiracı için ayrı tutulduğunu doğrulayın, fiziksel depolama paylaşılsa bile kriptografik izolasyonun sağlandığından emin olun.                                 |   3    | D/V |

---

## C8.6 Gelişmiş Bellek Sistemi Güvenliği

Episodik, semantik ve çalışma belleği gibi gelişmiş bellek mimarileri için, özel izolasyon ve doğrulama gereksinimlerini içeren güvenlik kontrolleri.

|   #   | Açıklama                                                                                                                                                                                                                                                     | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 8.6.1 | Farklı bellek türlerinin (epizodik, semantik, çalışma) rol tabanlı erişim kontrolleri, ayrı şifreleme anahtarları ve her bellek türü için belgelenmiş erişim desenleri ile izole güvenlik bağlamlarına sahip olduğunu doğrulayın.                            |   1    | D/V |
| 8.6.2 | Bellek konsolidasyon süreçlerinin, depolamadan önce içerik temizliği, kaynak doğrulaması ve bütünlük kontrolleri yoluyla kötü amaçlı belleklerin enjekte edilmesini önlemek için güvenlik doğrulamasını içerdiğini doğrulayın.                               |   2    | D/V |
| 8.6.3 | Bellek sorgusu taleplerinin, sorgu desen analizi, erişim kontrolü uygulanması ve sonuçların filtrelenmesi yoluyla yetkisiz bilgi çıkarımını önlemek amacıyla doğrulandığından ve temizlendiğinden emin olun.                                                 |   2    | D/V |
| 8.6.4 | Anahtar silme, çok geçişli üzerine yazma veya doğrulama sertifikaları ile donanım tabanlı güvenli silme yöntemlerini kullanarak, hafıza unutma mekanizmalarının hassas bilgileri kriptografik silme garantileriyle güvenli bir şekilde sildiğini doğrulayın. |   3    | D/V |
| 8.6.5 | Hafıza sisteminin bütünlüğünün, normal işlemler dışındaki bellek içeriği değişikliklerinde özet değerleri, denetim günlükleri ve otomatik uyarılar aracılığıyla yetkisiz değişiklikler veya bozulmalar için sürekli olarak izlenmesini doğrulayın.           |   3    | D/V |

---

## Referanslar

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

