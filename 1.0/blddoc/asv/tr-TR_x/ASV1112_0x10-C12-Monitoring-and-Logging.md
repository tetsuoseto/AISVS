# C12 İzleme, Günlükleme ve Anomali Tespiti

## Kontrol Amacı

Bu bölüm, modelin ve diğer yapay zeka bileşenlerinin ne gördüğünü, ne yaptığını ve ne döndürdüğünü gerçek zamanlı ve adli görünüm altında izlemenin gereksinimlerini sunar; tehditler tespit edilebilir, triage edilip bunlardan öğrenilebilir.

## C12.1 İstek ve Yanıt Günlüğü

|   #    | Açıklama                                                                                                                                                                                                                     | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.1.1 | Tüm kullanıcı istemlerinin ve model yanıtlarının uygun meta verilerle kaydedildiğini doğrulayın (ör. zaman damgası, kullanıcı kimliği, oturum kimliği, model sürümü).                                                        |   1    | D/V |
| 12.1.2 | Günlüklerin güvenli, erişim kontrollü depolama depolarında saklandığından emin olun ve uygun saklama politikaları ile yedekleme prosedürlerinin uygulanıp uygulanmadığını doğrulayın.                                        |   1    | D/V |
| 12.1.3 | Günlük depolama sistemlerinin dinlenme halinde ve iletim sırasında şifrelemeyi uyguladığını doğrulayın; bu, günlüklerde bulunan hassas bilgilerin korunmasını sağlar.                                                        |   1    | D/V |
| 12.1.4 | Prompts ve çıktılardaki hassas verilerin günlüğe kaydedilmeden önce otomatik olarak kırpıldığı veya maskelediğini doğrulayın; PII, kimlik bilgileri ve özel bilgiler için yapılandırılabilir kırpma/maskeleme kuralları ile. |   1    | D/V |
| 12.1.5 | Politika kararlarının ve güvenlik filtreleme işlemlerinin içerik moderasyon sistemlerinin denetlenmesi ve hata ayıklaması için yeterli ayrıntıyla kaydedildiğini doğrulayın.                                                 |   2    | D/V |
| 12.1.6 | Günlük bütünlüğünün, örneğin kriptografik imzalar veya yalnızca yazılabilir depolama ile korunduğunu doğrulayın.                                                                                                             |   2    | D/V |

---

## C12.2 Kötüye Kullanım Tespiti ve Uyarı

|   #    | Açıklama                                                                                                                                                                                                              | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.2.1 | Sistemin, bilinen jailbreak kalıplarını, prompt enjeksiyonu girişimlerini ve adversarial girdileri imza tabanlı tespit kullanarak tespit ettiğini ve uyarı verdiğini doğrulayın.                                      |   1    | D/V |
| 12.2.2 | Sistemin mevcut Güvenlik Bilgi ve Olay Yönetimi (SIEM) platformlarıyla standart günlük formatları ve protokollerini kullanarak entegrasyon sağladığını doğrulayın.                                                    |   1    | D/V |
| 12.2.3 | Zenginleştirilmiş güvenlik olaylarının Yapay Zeka'ya özgü bağlam içerdiğini doğrulayın; örneğin model tanımlayıcıları, güven skorları ve güvenlik filtresi kararları.                                                 |   2    | D/V |
| 12.2.4 | Davranışsal anomali tespitinin olağandışı konuşma kalıplarını, aşırı yeniden deneme girişimlerini veya sistematik keşif davranışlarını belirlediğini doğrulayın.                                                      |   2    | D/V |
| 12.2.5 | Potansiyel politika ihlallerinin veya saldırı girişimlerinin tespit edildiği durumlarda gerçek zamanlı uyarı mekanizmalarının güvenlik ekiplerini bilgilendirdiğini doğrulayın.                                       |   2    | D/V |
| 12.2.6 | Koordineli jailbreak girişimleri, prompt enjeksiyonu kampanyaları ve model çıkarımı saldırıları dahil olmak üzere yapay zekaya özgü tehdit desenlerini tespit etmek için özel kuralların dahil edildiğini doğrulayın. |   2    | D/V |
| 12.2.7 | Otomatik olay müdahale iş akışlarının zarar görmüş modelleri izole edebildiğini, kötü niyetli kullanıcıları engelleyebildiğini ve kritik güvenlik olaylarını yükseltebildiğini doğrulayın.                            |   3    | D/V |

---

## C12.3 Model Kayması Tespiti

|   #    | Açıklama                                                                                                                                                                                   | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.3.1 | Sistemin, doğruluk oranı, güven skorları, gecikme süresi ve hata oranları gibi temel performans metriklerini model sürümleri ve zaman dilimleri boyunca izlediğini doğrulayın.             |   1    | D/V |
| 12.3.2 | Performans metrikleri önceden tanımlanmış bozulma eşiklerini aştığında veya temel referans değerlerinden belirgin şekilde sapması durumunda otomatik uyarıların tetiklendiğini doğrulayın. |   2    | D/V |
| 12.3.3 | Halüsinasyon tespit monitörlerinin, model çıktılarında gerçeklere aykırı, tutarsız veya uydurma bilgiler içeren durumları tespit edip işaret ettiğini doğrulayın.                          |   2    | D/V |

---

## C12.4 Performans ve Davranış Telemetri

|   #    | Açıklama                                                                                                                                                     | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.4.1 | Operasyonel metriklerin, istek gecikmesi, token tüketimi, bellek kullanımı ve işlem hacmi dahil olmak üzere, sürekli olarak toplanıp izlenmesini doğrulayın. |   1    | D/V |
| 12.4.2 | Başarı ve başarısızlık oranlarının, hata türlerinin ve kök nedenlerinin kategorize edilip izlendiğini doğrulayın.                                            |   1    | D/V |
| 12.4.3 | Kaynak kullanımını izlemenin GPU/CPU kullanımı, bellek tüketimi ve depolama gereksinimlerini kapsadığını ve eşik aşımlarında uyarı verdiğini doğrulayın.     |   2    | D/V |

---

## C12.5 Yapay Zeka Olay Müdahale Planlama ve Uygulama

|   #    | Açıklama                                                                                                                                                                                      | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.5.1 | Olay müdahale planlarının özellikle yapay zeka ile ilgili güvenlik olaylarını, modelin ele geçirilmesi, veri zehirlenmesi ve adversarial saldırılar dahil olmak üzere kapsadığını doğrulayın. |   1    | D/V |
| 12.5.2 | Olay müdahale ekiplerinin yapay zekâya özgü adli bilişim araçlarına ve bu araçları kullanma konusundaki uzmanlığa erişiminin olduğunu doğrulayın.                                             |   2    | D/V |
| 12.5.3 | Olay sonrası analizinin model yeniden eğitimi için hususları, güvenlik filtrelerinin güncellemelerini ve edinilen derslerin güvenlik kontrollerine entegrasyonunu içerdiğini doğrulayın.      |   3    | D/V |

---

## C12.5 AI Performans Bozulması Tespiti

Zaman içinde yapay zeka modelinin performansında ve kalitesinde gerilemenin izlenmesi ve tespit edilmesi.

|   #    | Açıklama                                                                                                                                      | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.5.1 | Modelin doğruluğu, kesinliği, duyarlılığı ve F1 skorlarının sürekli olarak izlenip temel eşik değerleriyle karşılaştırıldığından emin olun.   |   1    | D/V |
| 12.5.2 | Veri sürüklenmesi tespitinin, model performansını etkileyebilecek girdi dağılımı değişikliklerini izlediğini doğrulayın.                      |   1    | D/V |
| 12.5.3 | Kavram sürüklenmesi tespitinin girdiler ile beklenen çıktılar arasındaki ilişkinin değişikliklerini belirlediğini doğrulayın.                 |   2    | D/V |
| 12.5.4 | Performans düşüşünün otomatik uyarılar tetiklediğini ve modelin yeniden eğitilmesini veya değiştirme iş akışlarını başlattığını doğrulayın.   |   2    | D/V |
| 12.5.5 | Bozulma kök neden analizinin performans düşüşlerini veri değişiklikleri, altyapı sorunları veya dış etkenlerle ilişkilendirdiğini doğrulayın. |   3    |  V  |

---

## C12.6 DAG Görselleştirme ve İş Akışı Güvenliği

İş akışı görselleştirme sistemlerini bilgi sızıntısı ve manipülasyon saldırılarından koruyun.

|   #    | Açıklama                                                                                                                                                                             | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 12.6.1 | DAG görselleştirme verilerinin saklama veya iletimden önce hassas bilgilerden arındırıldığını doğrulayın.                                                                            |   1    | D/V |
| 12.6.2 | İş akışı görselleştirme erişim kontrollerinin yalnızca yetkili kullanıcıların ajan karar yollarını ve akıl yürütme izlerini görüntüleyebilmesini sağladığını doğrulayın.             |   1    | D/V |
| 12.6.3 | DAG veri bütünlüğünün kriptografik imzalar ve müdahaleyi kanıtlayan depolama mekanizmalarıyla korunduğunu doğrulayın.                                                                |   2    | D/V |
| 12.6.4 | İş akışı görselleştirme sistemlerinin, özenle tasarlanmış düğüm veya kenar verileri üzerinden enjeksiyon saldırılarını önlemek amacıyla giriş doğrulamasını uyguladığını doğrulayın. |   2    | D/V |
| 12.6.5 | Gerçek zamanlı DAG güncellemelerinin hız sınırına tabi olduğundan ve görselleştirme sistemlerini DoS saldırılarına karşı korumak için doğrulandığından emin olun.                    |   3    | D/V |

---

## C12.7 Proaktif Güvenlik Davranışlarının İzlenmesi

Güvenlik tehditlerinin tespiti ve proaktif ajan davranışı analizi yoluyla önlenmesi.

|   #    | Açıklama                                                                                                                                              | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 12.7.1 | Proaktif ajan davranışlarının yürütülmeden önce güvenlik açısından doğrulanmış olduğundan emin olun; risk değerlendirme entegrasyonu ile doğrulayın.  |   1    | D/V |
| 12.7.2 | Otonom inisiyatif tetikleyicilerinin güvenlik bağlamı değerlendirmesi ve tehdit ortamı değerlendirmesi içerdiğini doğrulayın.                         |   2    | D/V |
| 12.7.3 | Proaktif davranış kalıplarının potansiyel güvenlik etkileri ve istenmeyen sonuçlar açısından analiz edildiğini doğrulayın.                            |   2    | D/V |
| 12.7.4 | Güvenlik açısından kritik proaktif eylemlerin açık onay zincirleri ile denetim izleri gerektirdiğini doğrulayın.                                      |   3    | D/V |
| 12.7.5 | Davranışsal anomali tespitinin, proaktif ajan kalıplarındaki sapmaları tespit ettiğini ve bunların güvenlik ihlaline işaret edebileceğini doğrulayın. |   3    | D/V |

---

## Kaynaklar

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

