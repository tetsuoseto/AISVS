# 11 Gizlilik Koruması ve Kişisel Veri Yönetimi

## Kontrol Amacı

Kişisel verilerin ancak net onay, asgari gerekli kapsam, kanıtlanabilir silme ve resmi gizlilik güvenceleri ile işlenmesini sağlamak için yapay zeka yaşam döngüsünün tamamında—toplama, eğitim, çıkarım ve olay müdahalesi süreçlerinde—katı gizlilik taahhütleri sürdürülmelidir.

---

## 11.1 Anonimleştirme ve Veri Azaltma

|   #    | Açıklama                                                                                                                                                                   | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.1.1 | Doğrudan ve yarı tanımlayıcıların kaldırıldığını, karma işlemine tabi tutulduğunu doğrulayın.                                                                              |   1    | D/V |
| 11.1.2 | Otomatik denetimlerin k-anonimlik/l-çeşitliliği ölçtüğünü ve eşik değerler politika altında düştüğünde uyarı verdiğini doğrulayın.                                         |   2    | D/V |
| 11.1.3 | Model özellik-önem raporlarının, ε = 0.01 karşılıklı bilgi sınırını aşan herhangi bir tanımlayıcı sızıntısını kanıtlamadığını doğrulayın.                                  |   2    |  V  |
| 11.1.4 | Bağlantı saldırıları altında bile yeniden tanımlama riskinin ≤ 0.05 olduğunu göstermek için resmi kanıtların veya sentetik veri sertifikasyonunun doğrulanmasını sağlayın. |   3    |  V  |

---

## 11.2 Unutulma Hakkı ve Silme Zorlaması

|   #    | Açıklama                                                                                                                                                                                                              | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.2.1 | Veri konusu silme taleplerinin, hizmet seviyesi anlaşmaları kapsamında 30 günden daha kısa sürede ham veri setlerine, kontrol noktalarına, gömme işlemlerine, kayıt dosyalarına ve yedeklere iletildiğini doğrulayın. |   1    | D/V |
| 11.2.2 | "Makine-unlearning" rutinlerinin sertifikalı unlearning algoritmaları kullanarak fiziksel olarak yeniden eğitme veya yaklaşık kaldırmayı sağladığını doğrulayın.                                                      |   2    |  D  |
| 11.2.3 | Gölge-model değerlendirmesinin, unutma işleminden sonra unutulan kayıtların çıktılarının %1'inden daha azını etkilediğini kanıtladığını doğrulayın.                                                                   |   2    |  V  |
| 11.2.4 | Silme olaylarının değiştirilemez şekilde kaydedildiğini ve düzenleyiciler için denetlenebilir olduğunu doğrulayın.                                                                                                    |   3    |  V  |

---

## 11.3 Diferansiyel-Gizlilik Koruyucuları

|   #    | Açıklama                                                                                                     | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 11.3.1 | Toplam ε politika eşiklerini aştığında gizlilik kaybı muhasebesi panolarının uyarı verdiğini doğrulayın.     |   2    | D/V |
| 11.3.2 | Kara kutu gizlilik denetimlerinin, ε̂ değerini beyan edilen değerin %10’u içinde tahmin ettiğini doğrulayın. |   2    |  V  |
| 11.3.3 | Resmi kanıtların tüm eğitim sonrası ince ayarları ve yerleştirmeleri kapsadığını doğrulayın.                 |   3    |  V  |

---

## 11.4 Amaç-Sınırlama ve Kapsam Kayması Koruması

|   #    | Açıklama                                                                                                                                  | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.4.1 | Her veri seti ve model kontrol noktası için, orijinal onayla uyumlu makine tarafından okunabilir bir amaç etiketi bulunduğunu doğrulayın. |   1    |  D  |
| 11.4.2 | Çalışma zamanı izleyicilerinin, beyan edilen amaçla tutarsız sorguları tespit ettiğini ve yumuşak reddi tetiklediğini doğrulayın.         |   1    | D/V |
| 11.4.3 | Politika-kod olarak belirlenen engellerin, DPIA incelemesi olmadan modellerin yeni alanlara yeniden dağıtımını engellediğini doğrulayın.  |   3    |  D  |
| 11.4.4 | Resmi izlenebilirlik kanıtlarının her kişisel veri yaşam döngüsünün onaylanmış kapsam içinde kaldığını gösterdiğini doğrulayın.           |   3    |  V  |

---

## 11.5 Onay Yönetimi ve Hukuka Uygun Dayanak Takibi

|   #    | Açıklama                                                                                                                         | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.5.1 | Bir Onay Yönetim Platformunun (CMP), veri sahibi başına onay durumu, amaç ve saklama süresini kaydettiğini doğrulayın.           |   1    | D/V |
| 11.5.2 | API'lerin onay belirteçlerini açığa çıkardığını doğrulayın; modeller ön çıkarım yapmadan önce belirteç kapsamını doğrulamalıdır. |   2    |  D  |
| 11.5.3 | Reddedilen veya geri çekilen onayın işleme boru hatlarını 24 saat içinde durdurduğunu doğrulayın.                                |   2    | D/V |

---

## 11.6 Gizlilik Kontrolleri ile Federated Learning

|   #    | Açıklama                                                                                                                       | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 11.6.1 | İstemci güncellemelerinin toplama öncesinde yerel diferansiyel gizlilik gürültüsü eklemesi kullandığını doğrulayın.            |   1    |  D  |
| 11.6.2 | Eğitim metriklerinin farklılaştırılmış gizlilikte olduğunu ve asla tek bir müşteriye ait kaybı açığa çıkarmadığını doğrulayın. |   2    | D/V |
| 11.6.3 | Zehirlemeye dayanıklı toplama (örneğin, Krum/Trimmed-Mean) özelliğinin etkinleştirildiğini doğrulayın.                         |   2    |  V  |
| 11.6.4 | Resmi kanıtların, toplam ε bütçesini 5'ten az fayda kaybıyla gösterdiğini doğrulayın.                                          |   3    |  V  |

---

### Referanslar

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

