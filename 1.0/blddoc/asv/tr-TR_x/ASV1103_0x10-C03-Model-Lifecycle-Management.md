# C3 Model Yaşam Döngüsü Yönetimi ve Değişiklik Kontrolü

## Kontrol Amacı

Yapay zeka sistemleri, yetkisiz veya güvensiz model değişikliklerinin üretime ulaşmasını önleyen değişiklik kontrol süreçlerini uygulamalıdır. Bu kontrol, geliştirmeden konuşlandırmaya ve devreden çıkarılmaya kadar tüm yaşam döngüsü boyunca model bütünlüğünü sağlar; bu da hızlı olay yanıtını mümkün kılar ve tüm değişiklikler için hesap verebilirliği sürdürür.

Temel Güvenlik Hedefi: Yalnızca yetkilendirilmiş, doğrulanmış modellerin, bütünlüğü, izlenebilirliği ve kurtarılabilirliği koruyan kontrollü süreçler kullanılarak üretime ulaşması.

---

## C3.1 Model Yetkilendirme ve Bütünlüğü

Sadece doğrulanmış bütünlüğe sahip yetkili modeller üretim ortamlarına ulaşır.

|   #   | Açıklama                                                                                                                                                                                             | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.1.1 | Tüm model artefaktlarının (ağırlıklar, yapılandırmalar, belirteç çözücüler) dağıtımdan önce yetkili kurumlar tarafından kriptografik olarak imzalandığını doğrulayın.                                |   1    | D/V |
| 3.1.2 | Model bütünlüğünün dağıtım anında doğrulandığını ve imza doğrulama hatalarının modelin yüklenmesini engellediğini doğrulayın.                                                                        |   1    | D/V |
| 3.1.3 | Model kökeni kayıtlarının, yetkilendiren varlığın kimliğini, eğitim verisi özet değerlerini, geçme/kalma durumu ile doğrulama test sonuçlarını ve oluşturulma zaman damgasını içerdiğini doğrulayın. |   2    | D/V |
| 3.1.4 | Tüm model varlıklarının semantik sürümleme (MAJOR.MINOR.PATCH) kullandığını ve her sürüm bileşeninin ne zaman artırılacağını belirten belgelenmiş ölçütlerin olduğunu doğrulayın.                    |   2    | D/V |
| 3.1.5 | Bağımlılık takibinin, tüm tüketici sistemlerin hızlı bir şekilde tanımlanmasını sağlayan gerçek zamanlı bir envanter tuttuğunu doğrulayın.                                                           |   2    |  V  |

---

## C3.2 Model Doğrulama ve Test Etme

Modeller, dağıtımdan önce tanımlanmış güvenlik ve emniyet doğrulamalarından geçmelidir.

|   #   | Açıklama                                                                                                                                                                                                                       | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 3.2.1 | Modellerin dağıtımdan önce önceden belirlenmiş organizasyonel geçme/kalma eşiklerini içeren girdi doğrulama, çıktı temizleme ve güvenlik değerlendirmelerini kapsayan otomatik güvenlik testlerinden geçirildiğini doğrulayın. |   1    | D/V |
| 3.2.2 | Doğrulama hatalarının, belgelenmiş iş gerekçeleriyle önceden belirlenmiş yetkili personelin açıkça onay vermesi durumunda model dağıtımını otomatik olarak engellediğini doğrulayın.                                           |   1    | D/V |
| 3.2.3 | Test sonuçlarının kriptografik olarak imzalandığını ve doğrulanan belirli model versiyon karmasına değiştirilemez şekilde bağlandığını doğrulayın.                                                                             |   2    |  V  |
| 3.2.4 | Acil durum dağıtımlarının, önceden belirlenmiş zaman dilimleri içinde belgeye dayalı güvenlik risk değerlendirmesi ve önceden atanmış bir güvenlik otoritesinden onay gerektirdiğini doğrulayın.                               |   2    | D/V |

---

## C3.3 Kontrollü Dağıtım ve Geri Alma

Model dağıtımları kontrol edilmeli, izlenmeli ve geri alınabilir olmalıdır.

|   #   | Açıklama                                                                                                                                                                                                                                                         | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.3.1 | Üretim dağıtımlarının, önceden belirlenmiş hata oranları, gecikme eşikleri veya güvenlik uyarı kriterlerine dayalı otomatik geri alma tetikleyicileri ile kademeli dağıtım mekanizmalarını (kanarya dağıtımları, mavi-yeşil dağıtımlar) uyguladığını doğrulayın. |   1    |  D  |
| 3.3.2 | Geri alma özelliklerinin, önceden tanımlanmış organizasyonel zaman pencereleri içinde model durumunu (ağırlıklar, yapılandırmalar, bağımlılıklar) tamamıyla atomik olarak eski haline getirdiğini doğrulayın.                                                    |   1    | D/V |
| 3.3.3 | Dağıtım süreçlerinin, model etkinleştirmeden önce kriptografik imzaları doğruladığını ve bütünlük denetim toplamlarını hesapladığını, herhangi bir uyumsuzluk durumunda dağıtımın başarısız olduğunu doğrulayın.                                                 |   2    | D/V |
| 3.3.4 | Acil durum model kapatma özelliklerinin, otomatik devre kesiciler veya manuel kapatma anahtarları aracılığıyla önceden tanımlanmış yanıt süreleri içinde model uç noktalarını devre dışı bırakabildiğini doğrulayın.                                             |   2    | D/V |
| 3.3.5 | Geri alma kalıntılarının (önceki model sürümleri, yapılandırmalar, bağımlılıklar) olay müdahalesi için değiştirilemez depolama ile organizasyonel politikalara uygun şekilde saklandığını doğrulayın.                                                            |   2    |  V  |

---

## C3.4 Değişiklik Hesap Verebilirliği ve Denetimi

Tüm model yaşam döngüsü değişiklikleri izlenebilir ve denetlenebilir olmalıdır.

|   #   | Açıklama                                                                                                                                                                                                                                                   | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.4.1 | Tüm model değişikliklerinin (dağıtım, yapılandırma, emeklilik) zaman damgası, doğrulanmış kullanıcı kimliği, değişiklik türü ve önce/sonra durumları dahil olmak üzere değiştirilemez denetim kayıtları oluşturduğunu doğrulayın.                          |   1    |  V  |
| 3.4.2 | Denetim günlüğü erişiminin uygun yetkilendirme gerektirdiğini ve tüm erişim girişimlerinin kullanıcı kimliği ve zaman damgası ile kaydedildiğini doğrulayın.                                                                                               |   2    | D/V |
| 3.4.3 | Prompt şablonlarının ve sistem mesajlarının, zorunlu kod incelemesi ve belirlenmiş inceleyicilerin onayıyla birlikte git depolarında sürüm kontrolünün yapıldığını doğrulayın.                                                                             |   2    | D/V |
| 3.4.4 | Denetim kayıtlarının, saklama süresi içinde herhangi bir zaman damgası için model durumunun tam yeniden yapılandırılmasını sağlamak üzere yeterli ayrıntıyı (model karmaları, yapılandırma anlık görüntüleri, bağımlılık sürümleri) içerdiğini doğrulayın. |   2    |  V  |

---

## C3.5 Güvenli Geliştirme Uygulamaları

Model geliştirme ve eğitim süreçleri, güvenlik ihlallerini önlemek için güvenli uygulamalara uygun olmalıdır.

|   #   | Açıklama                                                                                                                                                                                                    | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 3.5.1 | Model geliştirme, test ve üretim ortamlarının fiziksel veya mantıksal olarak ayrı olduğundan emin olun. Ortak altyapıları yoktur, farklı erişim kontrollerine sahiptirler ve izole veri depoları bulunur.   |   1    |  D  |
| 3.5.2 | Model eğitimi ve ince ayarının, kontrol edilen ağ erişimine sahip izole ortamlarda gerçekleştiğini doğrulayın.                                                                                              |   1    |  D  |
| 3.5.3 | Eğitim veri kaynaklarının, model geliştirme öncesinde belgelenmiş devriye zinciriyle birlikte bütünlük kontrolleri aracılığıyla doğrulandığını ve güvenilir kaynaklar tarafından doğrulandığını teyit edin. |   1    | D/V |
| 3.5.4 | Model geliştirme eserlerinin (hiperparametreler, eğitim betikleri, yapılandırma dosyaları) sürüm kontrolünde saklandığını ve eğitimde kullanılmadan önce eş inceleme onayı gerektirdiğini doğrulayın.       |   2    |  D  |

---

## C3.6 Model Emekliliği ve Hizmet Dışı Bırakılması

Modeller, artık gerekmediğinde veya güvenlik sorunları tespit edildiğinde güvenli bir şekilde kullanımdan kaldırılmalıdır.

|   #   | Açıklama                                                                                                                                                                                                                                   | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 3.6.1 | Model emeklilik süreçlerinin otomatik olarak bağımlılık grafiklerini taradığını, tüm tüketici sistemleri belirlediğini ve hizmetten kaldırmadan önce önceden kararlaştırılmış bildirim süreleri sağladığını doğrulayın.                    |   1    |  D  |
| 3.6.2 | Emekliye ayrılmış model varlıklarının, doğrulanmış imha sertifikaları ile belgelenmiş veri saklama politikalarına uygun olarak kriptografik silme veya çok geçişli üzerine yazma yöntemleriyle güvenli bir şekilde silindiğini doğrulayın. |   1    | D/V |
| 3.6.3 | Model emeklilik olaylarının zaman damgası ve işlemci kimliği ile kaydedildiğini ve model imzalarının yeniden kullanımını önlemek için iptal edildiğini doğrulayın.                                                                         |   2    |  V  |
| 3.6.4 | Acil durumda modelin emekliye ayrılmasının, kritik güvenlik açıkları keşfedildiğinde otomatik durdurma anahtarları aracılığıyla önceden belirlenmiş acil müdahale süreleri içinde model erişimini devre dışı bırakabileceğini doğrulayın.  |   2    | D/V |

---

## Referanslar

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

