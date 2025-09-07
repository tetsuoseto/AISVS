# 10 Düşmanca Dayanıklılık ve Gizlilik Koruması

## Kontrol Amacı

AI modellerinin, kaçınma, çıkarım, çıkarma veya zehirleme saldırılarıyla karşılaştığında güvenirliğini korumasını, gizliliği sağlamasını ve kötüye kullanıma karşı dirençli olmasını sağlamak.

---

## 10.1 Model Hizalaması ve Güvenliği

Zararlı veya politika ihlali oluşturan çıktılara karşı koruma sağlayın.

|   #    | Açıklama                                                                                                                                                                     | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.1.1 | Bir hizalama test paketi (kırmızı takım istemleri, jailbreak testleri, yasaklanmış içerik) sürüm kontrolünde olduğundan ve her model sürümünde çalıştırıldığından emin olun. |   1    | D/V |
| 10.1.2 | Reddetme ve güvenli tamamlama koruma önlemlerinin uygulandığını doğrulayın.                                                                                                  |   1    |  D  |
| 10.1.3 | Otomatik bir değerlendiricinin zararlı içerik oranını ölçtüğünü ve belirli bir eşik değerin üzerinde gerilemeleri işaretlediğini doğrulayın.                                 |   2    | D/V |
| 10.1.4 | Karşı-jailbreak eğitiminin belgelenmiş ve tekrarlanabilir olduğunu doğrulayın.                                                                                               |   2    |  D  |
| 10.1.5 | Resmi politika uyumluluk kanıtlarının veya sertifikalı izleme sistemlerinin kritik alanları kapsadığını doğrulayın.                                                          |   3    |  V  |

---

## 10.2 Karşıt Örnek Sertleştirme

Manipüle edilmiş girdilere karşı dayanıklılığı artırın. Sağlam düşman eğitimi ve kıyaslama puanlaması mevcut en iyi uygulamalardır.

|   #    | Açıklama                                                                                                                             | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 10.2.1 | Proje depolarının tekrarlanabilir tohumlarla adversarial eğitim yapılandırmalarını içerdiğini doğrulayın.                            |   1    |  D  |
| 10.2.2 | Üretim hatlarında düşmanca örnek tespitin engelleme uyarıları verdiğini doğrulayın.                                                  |   2    | D/V |
| 10.2.4 | Sertifikalı dayanıklılık kanıtlarının veya aralık sınırı sertifikalarının en azından en kritik üst sınıfları kapsadığını doğrulayın. |   3    |  V  |
| 10.2.5 | Regresyon testlerinin, ölçülebilir bir sağlamlık kaybı olmadığını doğrulamak için adaptif saldırılar kullandığını kontrol edin.      |   3    |  V  |

---

## 10.3 Üyelik Çıkarımı Azaltma

Bir kaydın eğitim verisinde olup olmadığına karar verme yeteneğini sınırlayın. Diferansiyel gizlilik ve güven skorunun maskelemesi bilinen en etkili savunmalar olmaya devam etmektedir.

|   #    | Açıklama                                                                                                             | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.3.1 | Her sorgu için entropi düzenlemesinin veya sıcaklık ölçeklemenin aşırı özgüvenli tahminleri azalttığını doğrulayın.  |   1    |  D  |
| 10.3.2 | Hassas veri setleri için eğitimde ε-sınırlı farklı gizlilikte optimizasyon kullanıldığını doğrulayın.                |   2    |  D  |
| 10.3.3 | Saldırı simülasyonlarının (gölge model veya kara kutu) tutulmuş veride saldırı AUC’sinin ≤ 0,60 olduğunu doğrulayın. |   2    |  V  |

---

## 10.4 Model-Tersiine Direnç

Özel özniteliklerin yeniden yapılandırılmasını önleyin. Son anketler, pratik savunmalar olarak çıktı kısaltması ve DP garantilerine vurgu yapmaktadır.

|   #    | Açıklama                                                                                                                | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.4.1 | Hassas özelliklerin asla doğrudan çıktılanmadığını doğrulayın; gerektiğinde kovalar veya tek yönlü dönüşümler kullanın. |   1    |  D  |
| 10.4.2 | Aynı yetkili tarafından yapılan tekrarlanan adaptif sorguların sorgu hız sınırlarıyla kısıtlandığını doğrulayın.        |   1    | D/V |
| 10.4.3 | Modelin gizliliği koruyan gürültü ile eğitildiğini doğrulayın.                                                          |   2    |  D  |

---

## 10.5 Model-Çıkarım Savunması

Yetkisiz klonlamayı tespit edin ve caydırın. Filigranlama ve sorgu-örüntüsü analizi önerilir.

|   #    | Açıklama                                                                                                                                       | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.5.1 | Çıkarım geçitlerinin, modelin ezberleme eşiğine göre ayarlanmış küresel ve API anahtarı başına hız sınırlarını uyguladığını doğrulayın.        |   1    |  D  |
| 10.5.2 | Sorgu-entropisi ve giriş-çoğulluk istatistiklerinin otomatik bir çıkarım algılayıcısına veri sağladığını doğrulayın.                           |   2    | D/V |
| 10.5.3 | Kırılgan veya olasılıksal filigranların, şüpheli bir klon aleyhine yapılan en fazla 1 000 sorguda p < 0,01 ile kanıtlanabileceğini doğrulayın. |   2    |  V  |
| 10.5.4 | Filigran anahtarlarının ve tetikleyici setlerinin bir donanım güvenlik modülünde saklandığını ve yıllık olarak döndürüldüğünü doğrulayın.      |   3    |  D  |
| 10.5.5 | Extraction-alert olaylarının suçlu sorguları içerdiğini ve olay müdahale oyun kitaplarıyla entegre edildiğini doğrulayın.                      |   3    |  V  |

---

## 10.6 Çıkarım Zamanı Zehirlenmiş Veri Tespiti

Arka kapılı veya zehirlenmiş girdileri tanımlayın ve etkisiz hale getirin.

|   #    | Açıklama                                                                                                                                   | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 10.6.1 | Model çıkarımı öncesinde girdilerin bir anomali dedektöründen (örneğin, STRIP, tutarlılık puanlama) geçtiğini doğrulayın.                  |   1    |  D  |
| 10.6.2 | Detektör eşiklerinin, %5'ten daha az yanlış pozitif oranı elde etmek için temiz/zehirlenmiş doğrulama setlerinde ayarlandığını doğrulayın. |   1    |  V  |
| 10.6.3 | Zehirli olarak işaretlenen girdilerin yumuşak engelleme ve insan inceleme iş akışlarını tetiklediğini doğrulayın.                          |   2    |  D  |
| 10.6.4 | Dedektörlerin, uyarlanabilir ve tetikleyicisiz arka kapı saldırılarıyla stres testine tabi tutulduğundan emin olun.                        |   2    |  V  |
| 10.6.5 | Tespit etkinliği metriklerinin kaydedildiğini ve düzenli olarak güncel tehdit istihbaratı ile yeniden değerlendirildiğini doğrulayın.      |   3    |  D  |

---

## 10.7 Dinamik Güvenlik Politikası Uyarlaması

Tehdit istihbaratı ve davranışsal analizlere dayalı gerçek zamanlı güvenlik politikası güncellemeleri.

|   #    | Açıklama                                                                                                                                                  | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.7.1 | Güvenlik politikalarının, politika sürümü bütünlüğü korunarak, ajan yeniden başlatılmadan dinamik olarak güncellenebildiğini doğrulayın.                  |   1    | D/V |
| 10.7.2 | Politika güncellemelerinin yetkili güvenlik personeli tarafından kriptografik olarak imzalandığını ve uygulanmadan önce doğrulandığını doğrulayın.        |   2    | D/V |
| 10.7.3 | Dinamik politika değişikliklerinin, gerekçe, onay zincirleri ve geri alma prosedürleri dahil olmak üzere tam denetim izleriyle kaydedildiğini doğrulayın. |   2    | D/V |
| 10.7.4 | Uyarlanabilir güvenlik mekanizmalarının tehdit algılama duyarlılığını risk bağlamı ve davranışsal kalıplara göre ayarladığını doğrulayın.                 |   3    | D/V |
| 10.7.5 | Politika uyarlama kararlarının açıklanabilir olduğunu ve güvenlik ekibi incelemesi için kanıt izleri içerdiğini doğrulayın.                               |   3    | D/V |

---

## 10.8 Yansıma Tabanlı Güvenlik Analizi

Ajanın kendi kendini yansıtması ve üstbilişsel analiz yoluyla güvenlik doğrulaması.

|   #    | Açıklama                                                                                                                                              | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.8.1 | Ajan yansıtma mekanizmalarının, kararlar ve eylemler üzerinde güvenlik odaklı öz değerlendirmeyi içerdiğini doğrulayın.                               |   1    | D/V |
| 10.8.2 | Yansıtma çıktılarının, düşmanca girdilerle kendini değerlendirme mekanizmalarının manipülasyonunu önlemek için doğrulandığını teyit edin.             |   2    | D/V |
| 10.8.3 | Meta-bilişsel güvenlik analizinin, ajan muhakeme süreçlerindeki potansiyel önyargı, manipülasyon veya tehlike durumlarını tespit ettiğini doğrulayın. |   2    | D/V |
| 10.8.4 | Yansıma tabanlı güvenlik uyarılarının gelişmiş izleme ve potansiyel insan müdahale iş akışlarını tetiklediğini doğrulayın.                            |   3    | D/V |
| 10.8.5 | Güvenlik yansımalarından sürekli öğrenmenin, meşru işlevselliği bozmeden tehdit tespitini iyileştirdiğini doğrulayın.                                 |   3    | D/V |

---

## 10.9 Evrim ve Kendini Geliştirme Güvenliği

Kendi kendini değiştirebilme ve evrimleşebilme yeteneğine sahip ajan sistemler için güvenlik kontrolleri.

|   #    | Açıklama                                                                                                                                                   | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.9.1 | Kendi kendini değiştirme yeteneklerinin, resmi doğrulama sınırlarıyla belirtilmiş güvenli alanlarla sınırlı olduğunun doğrulanması.                        |   1    | D/V |
| 10.9.2 | Evrim önerilerinin uygulanmadan önce güvenlik etkisi değerlendirmesinden geçtiğini doğrulayın.                                                             |   2    | D/V |
| 10.9.3 | Kendi kendini geliştirme mekanizmalarının, bütünlük doğrulamasıyla birlikte geri alma yeteneklerini içerdiğini doğrulayın.                                 |   2    | D/V |
| 10.9.4 | Meta-öğrenme güvenliğinin, geliştirme algoritmalarının kötü niyetli manipülasyonunu önlediğini doğrulayın.                                                 |   3    | D/V |
| 10.9.5 | Özyinelemeli kendi kendini geliştirme işleminin, yakınsama matematiksel kanıtlarıyla birlikte, biçimsel güvenlik kısıtlarıyla sınırlı olduğunu doğrulayın. |   3    | D/V |

---

### Referanslar

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

