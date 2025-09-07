# Ek D: Yapay Zeka Destekli Güvenli Kodlama Yönetimi ve Doğrulaması

## Amaç

Bu bölüm, yazılım geliştirme sürecinde AI destekli kodlama araçlarının güvenli ve etkili kullanımına yönelik temel organizasyonel kontrolleri tanımlayarak, SDLC boyunca güvenlik ve izlenebilirlik sağlamaktadır.

---

## AD.1 Yapay Zeka Destekli Güvenli Kodlama İş Akışı

AI araçlarını, mevcut güvenlik kapılarını zayıflatmadan, kuruluşun güvenli yazılım geliştirme yaşam döngüsüne (SSDLC) entegre edin.

|   #    | Açıklama                                                                                                                                                                                                                | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.1.1 | Belgelenmiş bir iş akışının, yapay zeka araçlarının kodu ne zaman ve nasıl oluşturabileceğini, yeniden düzenleyebileceğini veya inceleyebileceğini tanımladığını doğrulayın.                                            |   1    | D/V |
| AD.1.2 | İş akışının her SSDLC aşamasına (tasarım, uygulama, kod incelemesi, test, dağıtım) uyduğunu doğrulayın.                                                                                                                 |   2    |  D  |
| AD.1.3 | AI tarafından üretilen kod üzerinde ölçütlerin (örneğin, güvenlik açığı yoğunluğu, ortalama tespit süresi) toplanıp toplanmadığını ve insan kaynaklı temel değerlerle karşılaştırılıp karşılaştırılmadığını doğrulayın. |   3    | D/V |

---

## AD.2 Yapay Zeka Aracı Nitelendirme ve Tehdit Modelleme

Yapay zeka kodlama araçlarının benimsenmeden önce güvenlik yetenekleri, riskleri ve tedarik zinciri etkileri açısından değerlendirilmesini sağlayın.

|   #    | Açıklama                                                                                                                                                                                            | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.2.1 | Her AI aracı için tehdit modelinin, kötüye kullanım, model tersine çevirme, veri sızıntısı ve bağımlılık zinciri risklerini tanımladığını doğrulayın.                                               |   1    | D/V |
| AD.2.2 | Araç değerlendirmelerinin, herhangi bir yerel bileşenin statik/dinamik analizini ve SaaS uç noktalarının (TLS, kimlik doğrulama/izinlendirme, kayıt tutma) değerlendirmesini içerdiğini doğrulayın. |   2    |  D  |
| AD.2.3 | Değerlendirmelerin tanınmış bir çerçeveye uygun olduğunu ve büyük sürüm değişikliklerinden sonra yeniden yapıldığını doğrulayın.                                                                    |   3    | D/V |

---

## AD.3 Güvenli İstek ve Bağlam Yönetimi

AI modelleri için istemler veya bağlamlar oluşturulurken gizli bilgiler, özel kodlar ve kişisel verilerin sızmasını önleyin.

|   #    | Açıklama                                                                                                                                                                                     | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.3.1 | Yazılı rehberliğin, gizli bilgilerin, kimlik doğrulama verilerinin veya sınıflandırılmış verilerin istemlerde gönderilmesini yasakladığını doğrulayın.                                       |   1    | D/V |
| AD.3.2 | Teknik kontrollerin (istemci tarafı redaksiyon, onaylanmış bağlam filtreleri) hassas öğeleri otomatik olarak kaldırdığını doğrulayın.                                                        |   2    |  D  |
| AD.3.3 | İsteklerin ve yanıtların tokenlaştırıldığını, iletim sırasında ve depolanırken şifrelendiğini doğrulayın ve saklama sürelerinin veri sınıflandırma politikasına uygun olduğunu kontrol edin. |   3    | D/V |

---

## AD.4 Yapay Zeka ile Üretilen Kodun Doğrulanması

AI çıktısı tarafından tanıtılan güvenlik açıklarını tespit edin ve kod birleştirilmeden veya dağıtılmadan önce giderin.

|   #    | Açıklama                                                                                                                                                                    | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.4.1 | AI tarafından oluşturulan kodun her zaman insan kod incelemesine tabi tutulduğunu doğrulayın.                                                                               |   1    | D/V |
| AD.4.2 | Otomatik tarayıcıların (SAST/IAST/DAST) AI tarafından üretilen kod içeren her çekme talebinde çalıştığını doğrulayın ve kritik bulgular üzerine birleştirmeleri engelleyin. |   2    |  D  |
| AD.4.3 | Farklılaştırılmış fuzz testi veya özellik tabanlı testlerin, güvenlik kritik davranışları (örneğin, girdi doğrulama, yetkilendirme mantığı) kanıtladığını doğrulayın.       |   3    | D/V |

---

## AD.5 Kod Önerilerinin Açıklanabilirliği ve İzlenebilirliği

Denetçilere ve geliştiricilere, bir önerinin neden yapıldığı ve nasıl geliştiği hakkında bilgi verin.

|   #    | Açıklama                                                                                                                                                                                                      | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.5.1 | İstemi/yanıt çiftlerinin commit kimlikleri ile kaydedildiğini doğrulayın.                                                                                                                                     |   1    | D/V |
| AD.5.2 | Geliştiricilerin bir öneriyi destekleyen model atıflarını (eğitim parçacıkları, dokümantasyon) gösterebildiklerini doğrulayın.                                                                                |   2    |  D  |
| AD.5.3 | Açıklanabilirlik raporlarının tasarım öğeleriyle birlikte saklandığını ve güvenlik incelemelerinde referans verildiğini doğrulayarak, ISO/IEC 42001 izlenebilirlik prensiplerinin karşılandığından emin olun. |   3    | D/V |

---

## AD.6 Sürekli Geri Bildirim ve Model İnce Ayarı

Model güvenlik performansını zaman içinde iyileştirirken negatif kaymanın önlenmesini sağlar.

|   #    | Açıklama                                                                                                                                                                                                                                                                | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.6.1 | Geliştiricilerin güvensiz veya uyumsuz önerileri işaretleyebildiğini ve bu işaretlerin takip edildiğini doğrulayın.                                                                                                                                                     |   1    | D/V |
| AD.6.2 | Toplanan geri bildirimin, doğrulanmış güvenli kodlama kütüphaneleriyle (örneğin, OWASP Cheat Sheets) periyodik olarak ince ayar yapılmasını veya doğrulanmış güvenli kodlama kütüphaneleriyle desteklenen sorgu artırımlı üretim sürecini bilgilendirdiğini doğrulayın. |   2    |  D  |
| AD.6.3 | Kapalı döngü değerlendirme aracıyla her ince ayardan sonra regresyon testlerinin yapıldığını doğrulayın; güvenlik metrikleri, dağıtımdan önce önceki temel değerleri karşılamalı veya aşmalıdır.                                                                        |   3    | D/V |

---

### Referanslar

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

