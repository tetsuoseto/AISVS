# C8 Bellek, Gömülü Temsiller ve Vektör Veritabanı Güvenliği

## Kontrol Amacı

Gömme temsilleri ve vektör depoları, günümüz yapay zekâ sistemlerinin "canlı bellek"i olarak görev yapar; kullanıcı tarafından sağlanan verileri sürekli kabul eder ve Retrieval-Augmented Generation (RAG) aracılığıyla model bağlamlarına geri getirir. Yönetimden bağımsız bırakılırsa bu hafıza Kişisel Tanımlanabilir Bilgiler (PII) sızıntısına yol açabilir, rızayı ihlal edebilir veya orijinal metnin yeniden oluşturulmasına yol açabilir. Bu kontrol ailesinin amacı, bellek iş akışlarını ve vektör veritabanlarını güçlendirmek; böylece erişimin en az ayrıcalık ilkesine göre sınırlandırılması, gömme temsillerinin gizliliğinin korunması, depolanan vektörlerin süresinin dolabilmesi veya istek üzerine iptal edilebilmesi ve kullanıcı başına belleğin asla başka bir kullanıcının istemlerini veya tamamlamalarını kirletmemesinin sağlanmasıdır.

---

## C8.1 Bellek Üzerindeki Erişim Denetimleri & RAG Endeksler

Her vektör koleksiyonunda ayrıntılı erişim kontrollerini uygulayın.

|   #   | Açıklama                                                                                                                                                       | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.1.1 | Satır/ad alanı düzeyinde erişim kontrol kurallarının kiracı, koleksiyon veya belge etiketi başına ekleme, silme ve sorgu işlemlerini kısıtladığını doğrulayın. |   1    | D/V |
| 8.1.2 | API anahtarlarının veya JWT'lerin kapsama sahip iddialar taşıdığından ve en az üç ayda bir yeniden rotalandırıldığından emin olun.                             |   1    | D/V |
| 8.1.3 | Yetki yükseltme girişimlerinin (örneğin isim alanları arası benzerlik sorguları) tespit edildiğini ve 5 dakika içinde SIEM'e kaydedildiğini doğrulayın.        |   2    | D/V |
| 8.1.4 | Vektör veritabanı denetim günlüğünün şu alanları kaydettiğini doğrulayın: konu kimliği, işlem, vektör kimliği/ad alanı, benzerlik eşiği ve sonuç sayısı.       |   2    | D/V |
| 8.1.5 | Erişim kararlarının motorlar güncellendiğinde veya indeks bölütleme kuralları değiştiğinde atlatma güvenlik açıkları için test edildiğini doğrulayın.          |   3    |  V  |

---

## C8.2 Gömme Temizleme ve Doğrulama

Metni Kişisel Tanımlayıcı Bilgiler (PII) için ön taramadan geçirin, vektörleştirmeden önce gizleyin veya pseudonimleştirin ve isteğe bağlı olarak gömülü temsilleri son işlemden geçirerek kalıntı sinyallerini temizleyin.

|   #   | Açıklama                                                                                                                                                                                          | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.2.1 | PII ve düzenlenen verilerin otomatik sınıflandırıcılar aracılığıyla tespit edildiğini ve gömme öncesinde maskeleme, tokenleştirme veya çıkarma işlemlerinin uygulanıp uygulanmadığını doğrulayın. |   1    | D/V |
| 8.2.2 | Gömme işlem hatlarının, çalıştırılabilir kod içeren veya UTF-8 olmayan artefaktlar içeren girdileri reddettiğini veya karantinaya aldığını doğrulayın.                                            |   1    |  D  |
| 8.2.3 | Yerel veya metrik diferansiyel gizlilik temizlemesinin, herhangi bir bilinen PII belirtecine olan mesafenin ayarlanabilir bir eşik değerinin altında kaldığı durumlarda uygulanmasını doğrulayın. |   2    | D/V |
| 8.2.4 | Temizleme etkililiğinin (örneğin, PII redaksiyonunun geri çağırma oranı, semantik sapma) yıl içinde en az 2 kez benchmark korpusları karşısında doğrulandığından emin olun.                       |   2    |  V  |
| 8.2.5 | Sanitizasyon yapılandırmalarının sürüm denetimli olduğunu ve değişikliklerin akran incelemesinden geçtiğini doğrulayın.                                                                           |   3    | D/V |

---

## Bellek Süresinin Dolması, İptal ve Silme

GDPR "unutulma hakkı" ve benzeri yasalar zamanında silinmeyi zorunlu kılar; bu nedenle vektör depoları TTL'leri, kalıcı silme işlemlerini ve tombstone kaydı yapmayı desteklemek zorundadır ki iptal edilen vektörler geri getirilemez veya yeniden indekslenemez.

|   #   | Açıklama                                                                                                                                                                                       | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.3.1 | Her vektör ve meta veri kaydının, otomatik temizleme görevleri tarafından dikkate alınan bir TTL veya açık saklama etiketine sahip olduğundan emin olun.                                       |   1    | D/V |
| 8.3.2 | Kullanıcı tarafından başlatılan silme isteklerinin vektörleri, meta verileri, önbellek kopyaları ve türev indeksleri 30 gün içinde temizlediğini doğrulayın.                                   |   1    | D/V |
| 8.3.3 | Mantıksal silme işlemlerinin, donanım bunu destekliyorsa depolama bloklarının kriptografik olarak yok edilmesiyle veya Anahtar Kasası anahtarının yok edilmesiyle takip edildiğini doğrulayın. |   2    |  D  |
| 8.3.4 | Geçerliliğini yitirmiş vektörlerin en yakın komşu arama sonuçlarından hariç tutulduğunu, süresi dolduktan sonra < 500 ms içinde doğrulayın.                                                    |   3    | D/V |

---

## C8.4 Gömme Tersine Çevirme ve Sızıntıyı Önleme

Son savunmalar—gürültü üst üste koyma, projeksiyon ağları, mahremiyet-nöron bozulması ve uygulama katmanı şifrelemesi—token düzeyinde tersine çevirme oranlarını %5'in altında düşürebilir.

|   #   | Açıklama                                                                                                                                                                                                                     | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.4.1 | İnversiyon saldırılarını, üyelik çıkarımı saldırılarını ve öznitelik çıkarımı saldırılarını kapsayan resmi bir tehdit modelinin mevcut olduğunu ve yıllık olarak gözden geçirildiğini doğrulayın.                            |   1    |  V  |
| 8.4.2 | Uygulama katmanı şifrelemesi veya aramalı şifrelemenin altyapı yöneticileri veya bulut personeli tarafından yapılan doğrudan okumalarından vektörleri koruduğunu doğrulayın.                                                 |   2    | D/V |
| 8.4.3 | Savunma parametrelerinin (Differential Privacy için ε, gürültü σ, projeksiyon derecesi k) mahremiyetinin %99 veya daha yüksek token korumasını ve yararlılığın %3 veya daha düşük doğruluk kaybını dengelediğini doğrulayın. |   3    |  V  |
| 8.4.4 | İnversion-resilience metriklerinin model güncellemeleri için yayın kapılarının bir parçası olduğundan emin olun; regresyon bütçelerinin tanımlı olduğundan.                                                                  |   3    | D/V |

---

## C8.5 Kullanıcıya Özel Bellek İçin Kapsamın Uygulanması

Çapraz kiracı sızıntısı, RAG açısından en önemli risklerden biri olmaya devam ediyor: yanlış filtrelenmiş benzerlik sorguları başka bir müşterinin özel belgelerini ortaya çıkarabilir.

|   #   | Açıklama                                                                                                                                                                            | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.5.1 | Tüm geri alma sorgularının LLM istemine iletilmeden önce kiracı/kullanıcı kimliğine göre son filtrelendiğini doğrulayın.                                                            |   1    | D/V |
| 8.5.2 | Koleksiyon adlarının veya isim alanı kimliklerinin kullanıcıya veya kiracıya göre tuzlandığından emin olun; böylece vektörler kapsamlar arasında çakışmaz.                          |   1    |  D  |
| 8.5.3 | Yapılandırılabilir bir mesafe eşiğini aşan ancak çağıranın kapsamı dışında kalan benzerlik sonuçlarının reddedildiğini doğrulayın ve güvenlik uyarılarının tetiklenmesini sağlayın. |   2    | D/V |
| 8.5.4 | Çok kiracılı stres testlerinin, kapsama dışı belgeleri elde etmeye çalışan adversarial sorgularını simüle ettiğini ve sıfır sızıntı gösterdiğini doğrulayın.                        |   2    |  V  |
| 8.5.5 | Şifreleme anahtarlarının her kiracı için izole edildiğini doğrulayın; böylece fiziksel depolama paylaşılsa bile kriptografik izolasyon sağlanır.                                    |   3    | D/V |

---

## C8.6 Gelişmiş Bellek Sistemi Güvenliği

Epizodik, anlamsal ve çalışma belleğini kapsayan sofistike bellek mimarileri için belirli izolasyon ve doğrulama gereksinimlerine sahip güvenlik kontrolleri.

|   #   | Açıklama                                                                                                                                                                                                                                                  | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.6.1 | Farklı bellek türlerinin (episodik, semantik, çalışma) izole güvenlik bağlamlarına sahip olduğundan, rol tabanlı erişim kontrolleri, ayrı şifreleme anahtarları ve her bellek türü için belgelenmiş erişim desenlerinin bulunup bulunmadığını doğrulayın. |   1    | D/V |
| 8.6.2 | Bellek konsolidasyonu süreçlerinin, depolama öncesinde içerik temizleme, kaynak doğrulama ve bütünlük kontrolleri yoluyla kötü niyetli belleklerin enjeksiyonunu önlemek için güvenlik doğrulamasını içerdiğini doğrulayın.                               |   2    | D/V |
| 8.6.3 | Bellek geri getirme sorgularının doğrulanıp temizlendiğini, sorgu desen analizi, erişim kontrolünün uygulanması ve sonuç filtrelemesi yoluyla yetkisiz bilgilerin çıkarılmasının engellendiğini teyit edin.                                               |   2    | D/V |
| 8.6.4 | Bellek silme mekanizmalarının hassas bilgileri güvenli bir şekilde sildiğini kriptografik silme garantileriyle doğrulayın; bu, anahtar silme, çok geçişli yazma veya doğrulama sertifikalarıyla donanım tabanlı güvenli silme kullanılarak sağlanır.      |   3    | D/V |
| 8.6.5 | Bellek sistemi bütünlüğünün, bellek içeriği normal dışı değişiklikler gösterdiğinde otomatik uyarılarla, checksum'lar ve denetim günlükleri aracılığıyla yetkisiz değişikliklere veya bozulmaya karşı sürekli izlendiğini doğrulayın.                     |   3    | D/V |

---

## Kaynaklar

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

