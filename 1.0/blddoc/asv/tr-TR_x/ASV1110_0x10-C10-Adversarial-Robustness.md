# 10 Saldırılara Karşı Dayanıklılık & Gizlilik Koruması

## Kontrol Amacı

AI modellerinin kaçınma, çıkarım, veri çıkarma veya zehirleme saldırılarına karşı güvenilir, mahremiyeti koruyan ve kötüye kullanıma karşı dayanıklı kalmasını sağlayın.

---

## 10.1 Model Uyum ve Güvenlik

Zararlı veya politika ihlali içeren çıktılara karşı koruma sağlayın.

|   #    | Açıklama                                                                                                                                                                           | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.1.1 | Bir uyum test kümesinin (kırmızı takım istemleri, jailbreak tetkikleri, yasak içerik) versiyon kontrollü olduğunu ve her model sürümü yayımlandığında çalıştırıldığını doğrulayın. |   1    | D/V |
| 10.1.2 | Reddetme ve güvenli tamamlama için belirlenen kısıtlayıcı önlemlerin uygulanıp uygulanmadığını doğrulayın.                                                                         |   1    |  D  |
| 10.1.3 | Otomatik bir değerlendiricinin zararlı içerik oranını ölçtüğünü ve belirli bir eşik değerinin ötesindeki gerilemeleri işaretlediğini doğrulayın.                                   |   2    | D/V |
| 10.1.4 | counter-jailbreak eğitiminin belgelendiğini ve tekrarlanabilir olduğunu doğrulayın.                                                                                                |   2    |  D  |
| 10.1.5 | Resmi politika uygunluğu kanıtlarının veya sertifikalı izlemenin kritik alanları kapsadığını doğrulayın.                                                                           |   3    |  V  |

---

## 10.2 Saldırgan-Örnek Sertleştirme

Manipüle edilmiş girdilere karşı dayanıklılığı artırın. Sağlam adversarial eğitimi ve kıyaslama puanlaması şu anda en iyi uygulamalardır.

|   #    | Açıklama                                                                                                                             | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 10.2.1 | Projelerin depolarında tekrarlanabilir tohumlara sahip adversarial eğitim yapılandırmalarının bulunduğunu doğrulayın.                |   1    |  D  |
| 10.2.2 | Kötü niyetli örnek tespitinin üretim hatlarında engelleyici uyarılar tetiklediğini doğrulayın.                                       |   2    | D/V |
| 10.2.4 | Sertifikalı-sağlamlık kanıtlarının veya aralık-sınırlı sertifikaların en üstteki kritik sınıfları en azından kapsadığını doğrulayın. |   3    |  V  |
| 10.2.5 | Regresyon testlerinin ölçülebilir dayanıklılık kaybı olmadığını doğrulamak için adaptif saldırılar kullandığını doğrulayın.          |   3    |  V  |

---

## 10.3 Üyelik-Çıkarımı Saldırısına Karşı Önlemler

Bir kaydın eğitim verilerinde yer alıp almadığını belirleme yeteneğini sınırlayın. Farklılaştırmalı gizlilik ve güven-skoru maskeleme, bilinen en etkili savunmalar olarak kalmaya devam ediyor.

|   #    | Açıklama                                                                                                                                | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.3.1 | Sorgu başına entropi regularizasyonunun veya sıcaklık ölçeklendirmesinin aşırı güvenli tahminleri azalttığını doğrulayın.               |   1    |  D  |
| 10.3.2 | Eğitimin, hassas veri kümeleri için ε-sınırlandırılmış diferansiyel gizlilikle optimizasyon kullandığını doğrulayın.                    |   2    |  D  |
| 10.3.3 | Saldırı simülasyonlarının (gölge-modeli veya kara kutu) ayrılmış veriler üzerinde AUC'nin 0.60'a eşit veya daha az olduğunu doğrulayın. |   2    |  V  |

---

## 10.4 Model-İnversiyon Direnci

Gizli özniteliklerin yeniden türetilmesini engelleyin. Son araştırmalar çıktı kırpma ve DP güvencelerini pratik savunmalar olarak vurguluyor.

|   #    | Açıklama                                                                                                                         | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.4.1 | Hassas öznitelikler asla doğrudan çıktı olarak verilmemelidir; gerektiğinde, bucket'lar veya tek yönlü dönüşümler kullanın.      |   1    |  D  |
| 10.4.2 | Aynı kullanıcı kimliğinden gelen yinelenen uyarlanabilir sorguların, sorgu oranı sınırları tarafından kısıtlandığını doğrulayın. |   1    | D/V |
| 10.4.3 | Modelin gizlilik korumalı gürültüyle eğitildiğini doğrulayın.                                                                    |   2    |  D  |

---

## 10.5 Model-Çıkarımına Karşı Savunma

Yetkisiz klonlamayı tespit edin ve caydırın. Filigranlama ve sorgu desenleri analizi önerilir.

|   #    | Açıklama                                                                                                                                       | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.5.1 | İnferans geçitlerinin, modelin ezberleme eşiğine göre ayarlanmış küresel ve API anahtarına özgü istek hız sınırlarını uyguladığını doğrulayın. |   1    |  D  |
| 10.5.2 | Sorgu-entropisi ve girdi-çoğulluk istatistiklerinin otomatik çıkarım dedektörünü beslediğini doğrulayın.                                       |   2    | D/V |
| 10.5.3 | Zayıf veya olasılıksal su işaretlerinin, şüpheli bir klon karşısında p < 0.01 ile kanıtlanabileceğini doğrulayın.                              |   2    |  V  |
| 10.5.4 | Filigran anahtarlarının ve tetikleyici setlerin donanım güvenlik modülünde saklandığını ve her yıl yenilendiğini doğrulayın.                   |   3    |  D  |
| 10.5.5 | Extraction-alert olaylarının zararlı sorguları içerdiğini ve olay müdahale senaryolarıyla entegre edildiğini doğrulayın.                       |   3    |  V  |

---

## 10.6 Çıkarım Sırasında Zehirli-Veri Tespiti

Arka kapılı veya zehirlenmiş girdileri tespit edin ve etkisiz hale getirin.

|   #    | Açıklama                                                                                                                                 | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.6.1 | Girdilerin model çıkarımı öncesinde bir anomali dedektöründen geçtiğini doğrulayın (örn. STRIP, tutarlılık puanlaması).                  |   1    |  D  |
| 10.6.2 | Algılayıcı eşiklerinin temiz/zehirlenmiş doğrulama setlerinde ayarlandığını doğrulayın; böylece %5'ten az yanlış pozitif elde edin.      |   1    |  V  |
| 10.6.3 | Zehirli olarak işaretlenen girdilerin yumuşak engellemeyi ve insan inceleme iş akışlarını tetiklediğini doğrulayın.                      |   2    |  D  |
| 10.6.4 | Dedektörlerin uyarlanabilir ve tetikleyicisiz arka kapı saldırılarıyla stres testine tabi tutulduğunu doğrulayın.                        |   2    |  V  |
| 10.6.5 | Tespit etkililiği metriklerinin kaydedildiğini ve güncel tehdit istihbaratı ile periyodik olarak yeniden değerlendirildiğini doğrulayın. |   3    |  D  |

---

## 10.7 Dinamik Güvenlik Politikası Uyarlaması

Tehdit istihbaratı ve davranışsal analize dayalı olarak gerçek zamanlı güvenlik politikası güncellemeleri.

|   #    | Açıklama                                                                                                                                              | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.7.1 | Güvenlik politikalarının ajan yeniden başlatılmadan dinamik olarak güncellenebildiğini ve politika sürüm bütünlüğünün korunduğunu doğrulayın.         |   1    | D/V |
| 10.7.2 | Politika güncellemelerinin yetkili güvenlik personeli tarafından kriptografik olarak imzalandığını ve uygulanmadan önce doğrulandığını doğrulayın.    |   2    | D/V |
| 10.7.3 | Dinamik politika değişikliklerinin gerekçe, onay zincirleri ve geri alma prosedürleri dahil olmak üzere tam denetim iziyle kaydedildiğini doğrulayın. |   2    | D/V |
| 10.7.4 | Adaptif güvenlik mekanizmalarının tehdit tespitinin hassasiyetini risk bağlamına ve davranışsal kalıplara göre ayarladığını doğrulayın.               |   3    | D/V |
| 10.7.5 | Politika uyarlama kararlarının açıklanabilir olduğundan emin olun ve güvenlik ekibinin incelemesi için kanıt izleri ekleyin.                          |   3    | D/V |

---

## 10.8 Yansıma-Tabanlı Güvenlik Analizi

Ajanın öz-yansıtması ve metakognitif analizi yoluyla güvenlik doğrulaması.

|   #    | Açıklama                                                                                                                                                       | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.8.1 | Ajan yansıtma mekanizmalarının kararlar ve eylemler için güvenlik odaklı öz-değerlendirme içerdiğini doğrulayın.                                               |   1    | D/V |
| 10.8.2 | Yansıma çıktılarının, öz-değerlendirme mekanizmalarının adversarial girdiler tarafından manipüle edilmesini önlemek amacıyla doğrulanmış olduğundan emin olun. |   2    | D/V |
| 10.8.3 | Meta-bilişsel güvenlik analizinin ajan akıl yürütme süreçlerinde olası önyargı, manipülasyon veya güvenliğin zedelenmesini tespit ettiğini doğrulayın.         |   2    | D/V |
| 10.8.4 | Refleksiyon tabanlı güvenlik uyarılarının geliştirilmiş izleme ve potansiyel insan müdahalesi iş akışlarını tetiklediğini doğrulayın.                          |   3    | D/V |
| 10.8.5 | Güvenlik geri bildirimlerinden sürekli öğrenmenin tehdit tespitini iyileştirdiğini ve meşru işlevselliği bozmadığını doğrulayın.                               |   3    | D/V |

---

## 10.9 Evrim ve Öz-Gelişim Güvenliği

Kendi kendini değiştirebilen ve evrimleşebilen ajan sistemleri için güvenlik kontrolleri.

|   #    | Açıklama                                                                                                                                            | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 10.9.1 | Kendini değiştirme yeteneklerinin belirlenmiş güvenli alanlarla ve resmî doğrulama sınırlarıyla sınırlı olduğunu doğrulayın.                        |   1    | D/V |
| 10.9.2 | Gelişim önerilerinin uygulanmadan önce güvenlik etkisi değerlendirmesinden geçtiğini doğrulayın.                                                    |   2    | D/V |
| 10.9.3 | Kendi kendini geliştirme mekanizmalarının bütünlük doğrulamasıyla geri alma yeteneklerini içerdiğini doğrulayın.                                    |   2    | D/V |
| 10.9.4 | Meta-öğrenme güvenliğinin iyileştirme algoritmalarını adversarial manipülasyonundan koruduğunu doğrulayın.                                          |   3    | D/V |
| 10.9.5 | Özyinelemeli kendi kendine geliştirme işleminin biçimsel güvenlik kısıtlarıyla sınırlı olduğunu, yakınsama için matematiksel kanıtlarla doğrulayın. |   3    | D/V |

---

### Kaynaklar

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

