# 11 Gizlilik Koruması ve Kişisel Veri Yönetimi

## Kontrol Amacı

Yapay zeka yaşam döngüsü boyunca—toplama, eğitim, çıkarım ve olay müdahalesi—sıkı gizlilik güvencelerini sürdürün; böylece kişisel veriler yalnızca açık rıza ile, gereken asgari kapsamla, kanıtlanabilir silme ile ve resmi gizlilik garantileriyle işlenir.

---

## 11.1 Anonimleştirme ve Veri Minimizasyonu

|   #    | Açıklama                                                                                                                                       | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.1.1 | Doğrudan ve yarı tanımlayıcıların kaldırıldığından ve hash'lenmiş olduğundan emin olun.                                                        |   1    | D/V |
| 11.1.2 | Otomatik denetimlerin k-anonimlik ve l-çeşitliliği ölçtüğünü doğrulayın ve politikaya göre belirlenen eşiklerin altına düştüğünde uyarı verin. |   2    | D/V |
| 11.1.3 | Modelin özellik-önemi raporlarının ε = 0.01 karşılıklı bilgi değerinin ötesinde herhangi bir kimlik sızıntısını kanıtlamadığını doğrulayın.    |   2    |  V  |
| 11.1.4 | Resmi kanıtlar veya sentetik veri sertifikasyonunun yeniden kimliklendirme riskinin ≤ 0.05 olduğunu gösterdiğini doğrulayın.                   |   3    |  V  |

---

## 11.2 Unutulma Hakkı ve Silme Uygulaması

|   #    | Açıklama                                                                                                                                                                                                  | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.2.1 | Veri sahibi silme taleplerinin ham veri kümelerine, kontrol noktalarına, gömme temsillerine, günlük kayıtlara ve yedeklere 30 günden daha kısa SLA'lar kapsamında iletilmesini doğrulayın.                |   1    | D/V |
| 11.2.2 | ‘machine-unlearning’ rutinlerinin, sertifikalı unlearning algoritmaları kullanılarak fiziksel olarak yeniden eğitilmesini veya kaldırmayı yaklaşık olarak gerçekleştirip gerçekleştirmediğini doğrulayın. |   2    |  D  |
| 11.2.3 | Unlearning işlemi sonrası gölge-model değerlendirmesinin unutulan kayıtların çıktılarına %1'inden daha azına etki ettiğini doğrulayın.                                                                    |   2    |  V  |
| 11.2.4 | Silme olaylarının değiştirilemez biçimde kaydedildiğini ve regülatörler için denetlenebilir olduğunu doğrulayın.                                                                                          |   3    |  V  |

---

## 11.3 Diferansiyel-Gizlilik Önlemleri

|   #    | Açıklama                                                                                                              | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.3.1 | Kümülatif ε politika eşiklerini aştığında mahremiyet kaybı muhasebe panolarının uyarı verdiğini doğrulayın.           |   2    | D/V |
| 11.3.2 | Kara kutu gizlilik denetimlerinin ε̂ değerinin beyan edilen değerin ±%10'luk aralığında tahmin edildiğini doğrulayın. |   2    |  V  |
| 11.3.3 | Resmi kanıtların tüm eğitim sonrası ince ayarlamaları ve gömme vektörlerini kapsadığını doğrulayın.                   |   3    |  V  |

---

## 11.4 Amaç-Sınırlaması & Kapsam-Kayması Koruması

|   #    | Açıklama                                                                                                                                       | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.4.1 | Her veri kümesi ve her model kontrol noktası, orijinal rızaya uygun olarak makine okunabilir bir amaç etiketi taşıdığından emin olun.          |   1    |  D  |
| 11.4.2 | Çalışma zamanı izleme mekanizmalarının, beyan edilen amaçla tutarsız sorguları tespit ettiğini ve yumuşak reddetmeyi tetiklediğini doğrulayın. |   1    | D/V |
| 11.4.3 | Policy-as-code geçitlerinin DPIA incelemesi olmaksızın modellerin yeni alanlara yeniden konuşlandırılmasını engellediğini doğrulayın.          |   3    |  D  |
| 11.4.4 | Resmi izlenebilirlik kanıtlarının, her bir kişisel verinin yaşam döngüsünün rızaya uygun kapsam içinde kaldığını gösterdiğini doğrulayın.      |   3    |  V  |

---

## 11.5 Rıza Yönetimi & Yasal-Dayanak Takibi

|   #    | Açıklama                                                                                                                | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.5.1 | Bir Rıza Yönetim Platformu (CMP) veri öznesi başına rıza durumunu, amacını ve saklama süresini kaydettiğini doğrulayın. |   1    | D/V |
| 11.5.2 | API'lerin rıza belirteçlerini sunduğunu doğrulayın; modeller çıkarım öncesinde belirteç kapsamını doğrulamalıdır.       |   2    |  D  |
| 11.5.3 | Reddedilmiş veya geri çekilmiş rızanın işlem hatlarını 24 saat içinde durdurduğunu doğrulayın.                          |   2    | D/V |

---

## 11.6 Gizlilik Kontrolleri ile Dağıtık Öğrenme

|   #    | Açıklama                                                                                                                            | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 11.6.1 | İstemci güncellemelerinin birleştirme işleminden önce yerel diferansiyel gizlilik gürültüsünün eklenmesini kullandığını doğrulayın. |   1    |  D  |
| 11.6.2 | Eğitim metriklerinin diferansiyel gizlilik sağladığını ve tek bir istemcinin kaybını asla ifşa etmediğini doğrulayın.               |   2    | D/V |
| 11.6.3 | Zararlı veriye karşı dayanıklı agregasyonun (örneğin Krum/Trimmed-Mean) etkinleştirildiğini doğrulayın.                             |   2    |  V  |
| 11.6.4 | Formel kanıtların toplam ε bütçesini, 5'ten az yarar kaybı ile gösterdiğini doğrulayın.                                             |   3    |  V  |

---

### Kaynaklar

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

