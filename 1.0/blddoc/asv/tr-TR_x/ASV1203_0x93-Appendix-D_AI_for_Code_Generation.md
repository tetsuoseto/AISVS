# Ek D: Yapay Zeka-Destekli Güvenli Kodlama Yönetişimi ve Doğrulama

## Amaç

Bu bölüm, yazılım geliştirme süreci boyunca yapay zeka destekli kodlama araçlarının güvenli ve etkili kullanımına yönelik temel örgütsel kontrolleri tanımlar ve SDLC boyunca güvenlik ile izlenebilirliği sağlar.

---

## AD.1 Yapay Zeka Destekli Güvenli‑Kodlama İş Akışı

Kuruluşun güvenli‑yazılım‑geliştirme yaşam döngüsüne (SSDLC) yapay zeka araçlarını entegre etmek, mevcut güvenlik kapılarının zayıflatılmasına yol açmamak.

|   #    | Açıklama                                                                                                                                                                                                            | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.1.1 | Belgelenmiş bir iş akışının, yapay zeka araçlarının ne zaman ve nasıl kod üretebileceğini, kodu yeniden düzenleyebileceğini veya inceleyebileceğini açıkladığını doğrulayın.                                        |   1    | D/V |
| AD.1.2 | İş akışının her SSDLC aşamasına (tasarım, uygulama, kod incelemesi, test, dağıtım) karşılık gelip gelmediğini doğrulayın.                                                                                           |   2    |  D  |
| AD.1.3 | AI tarafından üretilen kod üzerinde metriklerin (örneğin güvenlik açığı yoğunluğu, tespit için ortalama süre) toplandığını ve bunların yalnızca insanlardan oluşan temel değerlerle karşılaştırıldığını doğrulayın. |   3    | D/V |

---

## AD.2 Yapay Zeka Aracı Yeterlilik ve Tehdit Modelleme

Kullanıma alınmadan önce AI kodlama araçlarının güvenlik yetenekleri, riskleri ve tedarik‑zinciri etkileri açısından değerlendirildiğinden emin olun.

|   #    | Açıklama                                                                                                                                                                                        | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.2.1 | Her yapay zeka aracı için bir tehdit modelinin kötüye kullanımı, model‑inversion, veri sızıntısı ve bağımlılık zinciri risklerini belirlediğini doğrulayın.                                     |   1    | D/V |
| AD.2.2 | Araç değerlendirmelerinin herhangi bir yerel bileşenin statik/dinamik analizini ve SaaS uç noktalarının (TLS, kimlik doğrulama/yetkilendirme, loglama) değerlendirmesini içerdiğini doğrulayın. |   2    |  D  |
| AD.2.3 | Değerlendirmelerin tanınmış bir çerçeveye uyduğunu doğrulayın ve ana sürüm değişikliklerinden sonra bunların yeniden gerçekleştirilmesini sağlayın.                                             |   3    | D/V |

---

## AD.3 Güvenli İstem ve Bağlam Yönetimi

Yapay zeka modelleri için istemler veya bağlamlar oluştururken gizli bilgilerin, tescilli kodun ve kişisel verilerin sızdırılmasını önleyin.

|   #    | Açıklama                                                                                                                                                                                      | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.3.1 | Yazılı kılavuzun, istemlerde gizli bilgiler, kimlik bilgileri veya sınıflandırılmış verilerin gönderilmesini yasakladığını doğrulayın.                                                        |   1    | D/V |
| AD.3.2 | Teknik kontrollerin (istemci tarafı kırpma, onaylı bağlam filtreleri) duyarlı artefaktları otomatik olarak temizlediğini doğrulayın.                                                          |   2    |  D  |
| AD.3.3 | İstemlerin ve yanıtların tokenleştirilmiş olduğundan, iletim sırasında ve dinlenirken şifreli olduğundan ve saklama sürelerinin veri sınıflandırma politikasıyla uyumlu olduğundan emin olun. |   3    | D/V |

---

## AD.4 Yapay Zeka Tarafından Üretilen Kodun Doğrulanması

Kod birleştirilmeden veya dağıtılmadan önce yapay zeka çıktısı ile ortaya çıkan güvenlik açıklarını tespit edin ve düzeltin.

|   #    | Açıklama                                                                                                                                                                                     | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.4.1 | AI‑tarafından üretilen kodun her zaman insan tarafından kod incelemesine tabi olduğundan emin olun.                                                                                          |   1    | D/V |
| AD.4.2 | AI‑generated kod içeren her çekme isteğinde otomatik tarayıcıların (SAST/IAST/DAST) çalıştığını doğrulayın ve kritik bulgular söz konusu olduğunda birleştirmelerin engellenmesini sağlayın. |   2    |  D  |
| AD.4.3 | Farklılaştırılmış fuzz testi veya özellik tabanlı testlerin güvenlik‑kritik davranışları kanıtladıklarını doğrulayın (örneğin, giriş doğrulama, yetkilendirme mantığı).                      |   3    | D/V |

---

## AD.5 Kod Önerilerinin Açıklanabilirliği ve İzlenebilirliği

Denetçilere ve geliştiricilere, bir önerinin neden sunulduğunu ve nasıl evrildiğini gösteren içgörü sağlayın.

|   #    | Açıklama                                                                                                                                                                                    | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| AD.5.1 | İstem/cevap çiftlerinin commit ID'leriyle kaydedildiğini doğrulayın.                                                                                                                        |   1    | D/V |
| AD.5.2 | Geliştiricilerin bir öneriyi destekleyen model atıflarını (eğitim parçacıkları, belgeler) ortaya çıkarabildiğini doğrulayın.                                                                |   2    |  D  |
| AD.5.3 | Açıklanabilirlik raporlarının tasarım çıktılarıyla birlikte depolandığını ve güvenlik incelemelerinde referans gösterildiğini doğrulayın; ISO/IEC 42001 izlenebilirlik ilkelerini karşılar. |   3    | D/V |

---

## AD.6 Sürekli Geri Bildirim ve Modelin İnce Ayarı

Zaman içinde modelin güvenlik performansını artırırken, olumsuz sapmayı önlemek.

|   #    | Açıklama                                                                                                                                                                                                           | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| AD.6.1 | Geliştiricilerin güvensiz veya uygunsuz önerileri işaretleyebilmesini ve bu işaretlerin izlenmesini doğrulayın.                                                                                                    |   1    | D/V |
| AD.6.2 | Toplanmış geribildirimlerin, periyodik ince ayar veya geri-getirme ile güçlendirilmiş üretim süreçlerini doğrulanmış güvenli-kodlama korpusları ile bilgilendirdiğini doğrulayın (örn. OWASP Cheat Sheets).        |   2    |  D  |
| AD.6.3 | Her ince ayardan sonra kapalı‑döngü değerlendirme aracının regresyon testlerini yürüttüğünden emin olun; güvenlik metrikleri, dağıtımdan önceki referans değerlerini karşılamalı veya bunların üzerinde olmalıdır. |   3    | D/V |

---

### Kaynaklar

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

