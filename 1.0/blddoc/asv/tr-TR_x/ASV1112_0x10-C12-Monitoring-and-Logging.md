# C12 İzleme, Günlük Kaydı ve Anomali Tespiti

## Kontrol Amacı

Bu bölüm, tehditlerin tespit edilebilmesi, önceliklendirilmesi ve öğrenilebilmesi için modelin ve diğer yapay zeka bileşenlerinin gördükleri, yaptıkları ve döndürdükleri konusunda gerçek zamanlı ve adli görünürlük sağlamaya yönelik gereksinimleri sunar.

## C12.1 İstek ve Yanıt Kaydı

|   #    | Açıklama                                                                                                                                                                                                                                                    | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.1.1 | Tüm kullanıcı istemlerinin ve model yanıtlarının uygun meta verilerle (örneğin, zaman damgası, kullanıcı kimliği, oturum kimliği, model sürümü) kaydedildiğini doğrulayın.                                                                                  |   1    | D/V |
| 12.1.2 | Günlüklerin uygun saklama politikaları ve yedekleme prosedürleriyle birlikte güvenli, erişim kontrollü depolarda saklandığını doğrulayın.                                                                                                                   |   1    | D/V |
| 12.1.3 | Günlüklerde bulunan hassas bilgileri korumak için günlük depolama sistemlerinin dinlenme ve aktarım sırasında şifrelemeyi uyguladığını doğrulayın.                                                                                                          |   1    | D/V |
| 12.1.4 | Promplarda ve çıktılarda yer alan hassas verilerin, PII (kişisel tanımlanabilir bilgiler), kimlik bilgileri ve özel bilgi için yapılandırılabilir sansür kuralları ile kayda alınmadan önce otomatik olarak sansürlendiğini veya maskelendiğini doğrulayın. |   1    | D/V |
| 12.1.5 | Politika kararlarının ve güvenlik filtreleme işlemlerinin, içerik denetim sistemlerinin denetimi ve hata ayıklaması için yeterli ayrıntıyla kaydedildiğini doğrulayın.                                                                                      |   2    | D/V |
| 12.1.6 | Günlük bütünlüğünün, örneğin kriptografik imzalar veya yalnızca yazılabilir depolama kullanılarak korunduğunu doğrulayın.                                                                                                                                   |   2    | D/V |

---

## C12.2 Kötüye Kullanım Tespiti ve Uyarı Sistemi

|   #    | Açıklama                                                                                                                                                                                                                   | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.2.1 | Sistem tarafından bilinen jailbreak desenlerinin, istem enjeksiyonu girişimlerinin ve düşmanca girdilerin imza tabanlı tespit ile algılanıp uyarı verdiğinin doğrulanması.                                                 |   1    | D/V |
| 12.2.2 | Sistemin, standart günlük formatları ve protokolleri kullanarak mevcut Güvenlik Bilgi ve Olay Yönetimi (SIEM) platformlarıyla entegre olduğunu doğrulayın.                                                                 |   1    | D/V |
| 12.2.3 | Zenginleştirilmiş güvenlik olaylarının, model tanımlayıcıları, güven skorları ve güvenlik filtresi kararları gibi AI özel bağlamını içerdiğini doğrulayın.                                                                 |   2    | D/V |
| 12.2.4 | Davranışsal anomali tespitinin, alışılmadık konuşma kalıplarını, aşırı tekrar denemelerini veya sistematik sorgulama davranışlarını tanımladığını doğrulayın.                                                              |   2    | D/V |
| 12.2.5 | Gerçek zamanlı uyarı mekanizmalarının, potansiyel politika ihlalleri veya saldırı girişimleri tespit edildiğinde güvenlik ekiplerini bilgilendirdiğini doğrulayın.                                                         |   2    | D/V |
| 12.2.6 | AI'ye özgü tehdit desenlerini tespit etmek için özel kuralların dahil edildiğini doğrulayın; bunlar arasında koordineli jailbreak girişimleri, prompt enjeksiyonu kampanyaları ve model çıkarma saldırıları bulunmaktadır. |   2    | D/V |
| 12.2.7 | Otomatik olay müdahale iş akışlarının, ele geçirilmiş modelleri izole edebildiğini, kötü niyetli kullanıcıları engelleyebildiğini ve kritik güvenlik olaylarını yükseltebildiğini doğrulayın.                              |   3    | D/V |

---

## C12.3 Model Sapması Tespiti

|   #    | Açıklama                                                                                                                                                                     | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.3.1 | Sistemin model sürümleri ve zaman dilimleri boyunca doğruluk, güven skorları, gecikme ve hata oranları gibi temel performans metriklerini takip ettiğini doğrulayın.         |   1    | D/V |
| 12.3.2 | Otomatik uyarıların, performans metrikleri önceden belirlenmiş bozulma eşiklerini aştığında veya başlangıç değerlerinden önemli ölçüde saptığında tetiklendiğini doğrulayın. |   2    | D/V |
| 12.3.3 | Halüsinasyon tespiti izleyicilerinin, model çıktılarının gerçeğe aykırı, tutarsız veya uydurma bilgiler içerdiği durumları tespit edip işaretlediğini doğrulayın.            |   2    | D/V |

---

## C12.4 Performans ve Davranış Telemetrijisi

|   #    | Açıklama                                                                                                                                                       | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.4.1 | İstek gecikmesi, token tüketimi, bellek kullanımı ve verimlilik gibi operasyonel metriklerin sürekli olarak toplanıp izlenip izlenmediğini doğrulayın.         |   1    | D/V |
| 12.4.2 | Başarı ve başarısızlık oranlarının, hata türlerinin ve bunların temel nedenlerinin kategorize edilerek izlendiğini doğrulayın.                                 |   1    | D/V |
| 12.4.3 | Kaynak kullanım izleme işleminin GPU/CPU kullanımı, bellek tüketimi ve depolama gereksinimlerini içerdiğini ve eşik ihlallerinde uyarı verildiğini doğrulayın. |   2    | D/V |

---

## C12.5 Yapay Zeka Olay Müdahale Planlaması ve Yürütülmesi

|   #    | Açıklama                                                                                                                                                                                         | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.5.1 | Olay müdahale planlarının, model ihlali, veri zehirlenmesi ve düşmanca saldırılar dahil olmak üzere yapay zeka ile ilgili güvenlik olaylarını özellikle ele aldığını doğrulayın.                 |   1    | D/V |
| 12.5.2 | Olay müdahale ekiplerinin, model davranışı ve saldırı vektörlerini araştırmak için yapay zeka özel adli bilişim araçlarına ve uzmanlığına erişimi olduğunu doğrulayın.                           |   2    | D/V |
| 12.5.3 | Olay sonrası analizde model yeniden eğitimi dikkate alındığından, güvenlik filtresi güncellemelerinin yapıldığından ve edinilen derslerin güvenlik kontrollerine entegre edildiğinden emin olun. |   3    | D/V |

---

## C12.5 AI Performans Bozulması Tespiti

AI model performansı ve kalitesindeki zaman içindeki bozulmayı izleyin ve tespit edin.

|   #    | Açıklama                                                                                                                                         | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.5.1 | Model doğruluğunun, kesinliğinin, duyarlılığının ve F1 skorlarının sürekli olarak izlenip temel eşik değerlerle karşılaştırıldığından emin olun. |   1    | D/V |
| 12.5.2 | Veri sapması tespiti, model performansını etkileyebilecek giriş dağılımı değişikliklerini izler.                                                 |   1    | D/V |
| 12.5.3 | Konsept kayması tespitin, girdiler ile beklenen çıktılar arasındaki ilişkideki değişiklikleri tanımladığını doğrulayın.                          |   2    | D/V |
| 12.5.4 | Performans düşüşünün otomatik uyarılar tetiklediğini ve modelin yeniden eğitilmesi veya değiştirilmesi iş akışlarını başlattığını doğrulayın.    |   2    | D/V |
| 12.5.5 | Performans düşüşlerini veri değişiklikleri, altyapı sorunları veya dış etkenlerle ilişkilendiren bozulma kök neden analizini doğrulayın.         |   3    |  V  |

---

## C12.6 DAG Görselleştirme ve İş Akışı Güvenliği

İş akışı görselleştirme sistemlerini bilgi sızıntısı ve manipülasyon saldırılarından koruyun.

|   #    | Açıklama                                                                                                                                                                             | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.6.1 | DAG görselleştirme verilerinin depolama veya iletim öncesinde hassas bilgileri kaldırmak için temizlendiğini doğrulayın.                                                             |   1    | D/V |
| 12.6.2 | İş akışı görselleştirme erişim kontrollerinin sadece yetkili kullanıcıların ajan karar yollarını ve gerekçe izlerini görüntüleyebildiğini doğrulayın.                                |   1    | D/V |
| 12.6.3 | DAG veri bütünlüğünün kriptografik imzalar ve müdahaleye karşı kanıt sağlayan depolama mekanizmaları ile korunduğunu doğrulayın.                                                     |   2    | D/V |
| 12.6.4 | İş akışı görselleştirme sistemlerinin, düzenlenmiş düğüm veya bağlantı verileri yoluyla enjeksiyon saldırılarını önlemek için giriş doğrulaması uyguladığını doğrulayın.             |   2    | D/V |
| 12.6.5 | Gerçek zamanlı DAG güncellemelerinin, görselleştirme sistemlerine yönelik hizmet reddi saldırılarını önlemek için hız sınırlamasına tabi tutulduğunu ve doğrulandığını kontrol edin. |   3    | D/V |

---

## C12.7 Proaktif Güvenlik Davranışı İzleme

Güvenlik tehditlerinin tespit edilmesi ve önlenmesi, proaktif ajan davranışı analizi yoluyla.

|   #    | Açıklama                                                                                                                       | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.7.1 | Proaktif ajan davranışlarının yürütmeden önce risk değerlendirme entegrasyonuyla güvenlik açısından doğrulandığını teyit edin. |   1    | D/V |
| 12.7.2 | Otonom inisiyatif tetikleyicilerinin güvenlik bağlamı değerlendirmesi ve tehdit manzarası analizini içerdiğini doğrulayın.     |   2    | D/V |
| 12.7.3 | Proaktif davranış kalıplarının potansiyel güvenlik etkileri ve istenmeyen sonuçlar açısından analiz edildiğini doğrulayın.     |   2    | D/V |
| 12.7.4 | Güvenlik açısından kritik proaktif eylemlerin açık onay zincirleri ve denetim izleri gerektirdiğini doğrulayın.                |   3    | D/V |
| 12.7.5 | Davranışsal anomali tespitinin, tehlike gösterebilecek proaktif ajan kalıplarındaki sapmaları belirlediğini doğrulayın.        |   3    | D/V |

---

## Referanslar

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

