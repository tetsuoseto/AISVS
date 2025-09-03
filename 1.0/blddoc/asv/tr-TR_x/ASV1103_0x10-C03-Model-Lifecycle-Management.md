# C3 Model Yaşam Döngüsü Yönetimi ve Değişiklik Kontrolü

## Kontrol Amacı

Yapay Zeka sistemleri, yetkisiz veya güvensiz model değişikliklerinin üretim ortamına ulaşmasını önleyen değişiklik kontrol süreçlerini hayata geçirmelidir. Bu kontrol, tüm yaşam döngüsü boyunca model bütünlüğünü sağlar--geliştirmeden dağıtıma ve kullanımdan kaldırmaya kadar--ve bu, hızlı olay müdahalesini mümkün kılar ve tüm değişiklikler için hesap verebilirliği sürdürür.

Temel Güvenlik Hedefi: Yalnızca yetkilendirilmiş, doğrulanmış modeller üretim ortamına ulaşır; bütünlük, izlenebilirlik ve kurtarılabilirliği sağlayan kontrollü süreçler uygulayarak.

---

## C3.1 Model Yetkilendirme ve Bütünlük

Sadece yetkilendirilmiş ve bütünlüğü doğrulanmış modeller üretim ortamlarına ulaşırlar.

|   #   | Açıklama                                                                                                                                                                                                          | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.1.1 | Devreye alınmadan önce tüm model varlıklarının (ağırlıklar, yapılandırmalar, tokenizer'lar) kriptografik olarak yetkili varlıklar tarafından imzalandığını doğrulayın.                                            |   1    | D/V |
| 3.1.2 | Dağıtım sırasında model bütünlüğünün doğrulandığını ve imza doğrulama hatalarının modelin yüklenmesini engellediğini doğrulayın.                                                                                  |   1    | D/V |
| 3.1.3 | Model kökeni kayıtlarının şu öğeleri içerdiğini doğrulayın: yetkili kuruluşun kimliği, eğitim verisinin hash değerleri, doğrulama test sonuçları geçerli/başarısız durumuna ilişkin ve oluşturulma zaman damgası. |   2    | D/V |
| 3.1.4 | Tüm model artefaktlarının semantik sürümlemeyi (MAJOR.MINOR.PATCH) kullandığından emin olun; her sürüm bileşeninin ne zaman artacağını belirten belgelenmiş kriterlerle.                                          |   2    | D/V |
| 3.1.5 | Bağımlılık izlemesinin, tüm tüketen sistemlerin hızlı bir şekilde tanımlanmasını sağlayan gerçek zamanlı bir envanter tuttuğunu doğrulayın.                                                                       |   2    |  V  |

---

## C3.2 Model Doğrulama ve Testler

Modeller, dağıtımdan önce tanımlanmış güvenlik doğrulamalarından geçmelidir.

|   #   | Açıklama                                                                                                                                                                                                                                                  | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.2.1 | Modellerin dağıtımdan önce giriş doğrulama, çıktı temizleme ve güvenlik değerlendirmelerini içeren otomatik güvenlik testlerinden geçtiğini ve bu testlerin önceden üzerinde anlaşılan geçiş/başarısızlık eşiklerine göre değerlendirildiğini doğrulayın. |   1    | D/V |
| 3.2.2 | Doğrulama hatalarının, önceden belirlenmiş yetkili kişilerden gelen açık istisna onayından sonra belgelendirilmiş iş gerekçeleriyle otomatik olarak model dağıtımını engellediğini doğrulayın.                                                            |   1    | D/V |
| 3.2.3 | Test sonuçlarının kriptografik olarak imzalandığını ve doğrulanan belirli model sürümü hash’ine değiştirilemez biçimde bağlandığını doğrulayın.                                                                                                           |   2    |  V  |
| 3.2.4 | Acil dağıtımların belgelenmiş güvenlik risk değerlendirmesi ve önceden belirlenmiş bir güvenlik otoritesinden onay gerektirdiğini, önceden kararlaştırılmış zaman çerçeveleri içinde olduğunun doğrulanmasını sağlayın.                                   |   2    | D/V |

---

## C3.3 Kontrollü Dağıtım ve Geri Alma

Model dağıtımları kontrollü, izlenebilir ve geri alınabilir olmalıdır.

|   #   | Açıklama                                                                                                                                                                                                                                                                                | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.3.1 | Üretim dağıtımlarının kademeli dağıtım mekanizmalarını (kanarya dağıtımları, mavi-yeşil dağıtımları) otomatik geri alma tetikleyicileri ile birlikte uygulandığını doğrulayın, önceden kararlaştırılmış hata oranlarına, gecikme eşiklerine veya güvenlik uyarı kriterlerine dayanarak. |   1    |  D  |
| 3.3.2 | Geri alma yeteneklerinin, ağırlıklar, yapılandırmalar ve bağımlılıklar dahil olmak üzere tam model durumunu atomik olarak önceden tanımlanmış kurumsal zaman dilimleri içinde geri yüklediğini doğrulayın.                                                                              |   1    | D/V |
| 3.3.3 | Dağıtım süreçlerinin kriptografik imzaları doğruladığını ve model etkinleştirilmeden önce bütünlük denetim toplamlarını hesapladığını doğrulayın; herhangi bir uyumsuzluk durumunda dağıtımı başarısız kılın.                                                                           |   2    | D/V |
| 3.3.4 | Acil durum model kapatma yeteneklerinin, otomatik devre kesiciler veya manuel kapatma anahtarları aracılığıyla önceden belirlenmiş yanıt süreleri içinde model uç noktalarını devre dışı bırakabildiğini doğrulayın.                                                                    |   2    | D/V |
| 3.3.5 | Geri alma artefaktlarının (önceki model sürümleri, yapılandırmalar, bağımlılıklar) kurum politikalarına uygun olarak saklandığını, olay müdahalesi için değiştirilemez depolama ile doğrulayın.                                                                                         |   2    |  V  |

---

## C3.4 Değişiklik Sorumluluğu ve Denetimi

Tüm model yaşam döngüsü değişiklikleri izlenebilir ve denetlenebilir olmalıdır.

|   #   | Açıklama                                                                                                                                                                                                                                                         | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.4.1 | Tüm model değişikliklerinin (dağıtım, yapılandırma, kullanımdan kaldırma) değiştirilmez denetim kayıtları ürettiğini doğrulayın; bu kayıtlar bir zaman damgası, doğrulanmış aktör kimliği, değişiklik türü ve önceki ile sonraki durumları içermelidir.          |   1    |  V  |
| 3.4.2 | Denetim günlüğü erişiminin uygun yetkilendirme gerektirdiğini ve tüm erişim girişimlerinin kullanıcı kimliği ile bir zaman damgası kaydedildiğini doğrulayın.                                                                                                    |   2    | D/V |
| 3.4.3 | Dağıtımdan önce, prompt şablonları ve sistem mesajlarının Git depolarında sürüm kontrolü altında olduğundan ve zorunlu kod incelemesi ile belirlenen inceleyenlerden onay alındığından emin olun.                                                                |   2    | D/V |
| 3.4.4 | Denetim kayıtlarının saklama süresi içindeki herhangi bir zaman damgası için model durumunun eksiksiz yeniden oluşturulmasını sağlayacak kadar ayrıntıya sahip olduğunu doğrulayın (model hash değerleri, yapılandırma anlık görüntüleri, bağımlılık sürümleri). |   2    |  V  |

---

## C3.5 Güvenli Yazılım Geliştirme Uygulamaları

Model geliştirme ve eğitim süreçleri, güvenli uygulamaları izleyerek güvenliğini bozulmadan korumalıdır.

|   #   | Açıklama                                                                                                                                                                                                                             | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 3.5.1 | Model geliştirme, test ve üretim ortamlarının fiziksel olarak veya mantıksal olarak ayrı olduğundan emin olun. Bu ortamlar paylaşılan altyapıya sahip değildir; farklı erişim kontrollerine ve izole veri depolarına sahiptirler.    |   1    |  D  |
| 3.5.2 | Model eğitiminin ve ince ayarın izole ortamlarda kontrollü ağ erişimiyle gerçekleştiğini doğrulayın.                                                                                                                                 |   1    |  D  |
| 3.5.3 | Model geliştirme öncesinde, eğitim veri kaynaklarının bütünlük kontrolleriyle doğrulanmış ve güvenilir kaynaklar aracılığıyla kimlik doğrulaması yapılmış olduğundan ve belgelenmiş sahiplik zinciriyle desteklendiğinden emin olun. |   1    | D/V |
| 3.5.4 | Model geliştirme artefaktlarının (hiperparametreler, eğitim betikleri, yapılandırma dosyaları) sürüm kontrolünde saklandığını ve eğitimde kullanılmadan önce eşler arası inceleme onayı gerektirdiğini doğrulayın.                   |   2    |  D  |

---

## C3.6 Model Emekliliği ve Devre Dışı Bırakma

Modeller artık ihtiyaç duyulmadığında veya güvenlik sorunları tespit edildiğinde güvenli bir şekilde kullanımdan kaldırılmalıdır.

|   #   | Açıklama                                                                                                                                                                                                                                              | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.6.1 | Modelin kullanım dışı bırakılmasına yönelik süreçlerin bağımlılık grafiğini otomatik olarak taradığını, tüm tüketen sistemleri belirlediğini ve devre dışı bırakmadan önce üzerinde uzlaşılmış ön bildirim sürelerini sağladığını doğrulayın.         |   1    |  D  |
| 3.6.2 | Kullanımdan kaldırılan model artefaktlarının belgelendirilmiş veri saklama politikalarına göre kriptografik silme veya çok geçişli üzerine yazma ile güvenli bir şekilde silindiğini ve doğrulanmış imha sertifikaları ile belgelendiğini doğrulayın. |   1    | D/V |
| 3.6.3 | Model emeklilik olaylarının zaman damgası ve aktör kimliği ile kaydedildiğini ve model imzalarının yeniden kullanımını engellemek için iptal edildiğini doğrulayın.                                                                                   |   2    |  V  |
| 3.6.4 | Acil durum modelinin emekli edilmesiyle, kritik güvenlik açıkları tespit edildiğinde otomatik kilitleme anahtarları aracılığıyla önceden belirlenmiş acil yanıt süreleri içinde modele erişiminin devre dışı bırakılabildiğini doğrulayın.            |   2    | D/V |

---

## Kaynaklar

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

