# C13 İnsan Gözetimi, Hesap Verebilirlik ve Yönetişim

## Kontrol Amacı

Bu bölüm, AI sistemlerinde insan gözetiminin sürdürülmesi ve net hesap verebilirlik zincirlerinin sağlanması için gereksinimleri sunar; AI yaşam döngüsü boyunca açıklanabilirlik, şeffaflık ve etik yönetimi garanti eder.

---

## C13.1 Öldürme Anahtarı ve Geçersiz Kılma Mekanizmaları

AI sisteminin güvensiz davranışı gözlemlendiğinde kapanma veya geri alma yolları sağlayın.

|   #    | Açıklama                                                                                                              | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.1.1 | AI model çıkarımı ve çıktıları hemen durdurmak için manuel bir öldürme-kapama mekanizmasının var olduğunu doğrulayın. |   1    | D/V |
| 13.1.2 | Geçersiz kılma kontrollerinin yalnızca yetkili personele erişilebilir olduğunu doğrulayın.                            |   1    |  D  |
| 13.1.3 | Geri alma prosedürlerinin önceki model sürümlerine veya güvenli mod işlemlerine dönebileceğini doğrulayın.            |   3    | D/V |
| 13.1.4 | Üstünlük mekanizmalarının düzenli olarak test edildiğini doğrulayın.                                                  |   3    |  V  |

---

## C13.2 İnsan-Döngüsünde Karar Kontrol Noktaları

Risk eşiklerini aştığında insan onayı gerektirir.

|   #    | Açıklama                                                                                                                         | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.2.1 | Yüksek riskli yapay zeka kararlarının yürütülmeden önce açık insan onayı gerektirdiğini doğrulayın.                              |   1    | D/V |
| 13.2.2 | Risk eşiklerinin net bir şekilde tanımlandığını ve otomatik olarak insan inceleme iş akışlarını tetiklediğini doğrulayın.        |   1    |  D  |
| 13.2.3 | Zaman duyarlı kararların, insan onayı gereken süre içinde alınamadığında yedek prosedürlere sahip olduğunu doğrulayın.           |   2    |  D  |
| 13.2.4 | Varsa, tırmanma prosedürlerinin farklı karar türleri veya risk kategorileri için net yetki seviyelerini belirttiğini doğrulayın. |   3    | D/V |

---

## C13.3 Sorumluluk Zinciri ve Denetlenebilirlik

Operatör işlemlerini ve model kararlarını kaydedin.

|   #    | Açıklama                                                                                                                                               | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 13.3.1 | Tüm Yapay Zeka sistemi kararlarının ve insan müdahalelerinin zaman damgaları, kullanıcı kimlikleri ve karar gerekçeleri ile kaydedildiğini doğrulayın. |   1    | D/V |
| 13.3.2 | Denetim kayıtlarının değiştirilmesinin imkansız olduğunu doğrulayın ve bütünlük doğrulama mekanizmalarını içermesini sağlayın.                         |   2    |  D  |

---

## C13.4 Açıklanabilir-YZ Teknikleri

Yüzey özellik önemi, karşı-olaylar ve yerel açıklamalar.

|   #    | Açıklama                                                                                                                                                                 | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 13.4.1 | Yapay zeka sistemlerinin kararları için insan tarafından okunabilir formatta temel açıklamalar sağladığını doğrulayın.                                                   |   1    | D/V |
| 13.4.2 | Açıklama kalitesinin insan değerlendirme çalışmaları ve metrikler aracılığıyla doğrulandığını teyit edin.                                                                |   2    |  V  |
| 13.4.3 | Önemli kararlar için özellik önem puanları veya atıf yöntemlerinin (SHAP, LIME, vb.) mevcut olduğunu doğrulayın.                                                         |   3    | D/V |
| 13.4.4 | Karşıt gerçeklik açıklamalarının, kullanım durumu ve alana uygulanabiliyorsa, girdilerin sonuçları değiştirmek için nasıl değiştirilebileceğini gösterdiğini doğrulayın. |   3    |  V  |

---

## C13.5 Model Kartları ve Kullanım Açıklamaları

Model kartlarını amaçlanan kullanım, performans metrikleri ve etik hususlar için güncel tutun.

|   #    | Açıklama                                                                                                                                                                                              | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.5.1 | Model kartlarının amaçlanan kullanım durumlarını, sınırlamalarını ve bilinen hata modlarını belgelediğini doğrulayın.                                                                                 |   1    |  D  |
| 13.5.2 | Farklı uygulanabilir kullanım senaryoları arasında performans metriklerinin açıklandığını doğrulayın.                                                                                                 |   1    | D/V |
| 13.5.3 | Etik değerlendirmelerin, önyargı analizlerinin, adalet değerlendirmelerinin, eğitim veri özelliklerinin ve bilinen eğitim veri sınırlamalarının belgelenip düzenli olarak güncellendiğini doğrulayın. |   2    |  D  |
| 13.5.4 | Model kartlarının sürüm kontrolünün yapıldığını ve değişiklik takibi ile model yaşam döngüsü boyunca korunduğunu doğrulayın.                                                                          |   2    | D/V |

---

## C13.6 Belirsizlik Nicelleştirme

Yanıtlar içinde güven skorlarını veya entropi ölçümlerini yaydırın.

|   #    | Açıklama                                                                                                | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.6.1 | AI sistemlerinin çıktılarıyla birlikte güven skorları veya belirsizlik ölçüleri sağladığını doğrulayın. |   1    |  D  |
| 13.6.2 | Belirsizlik eşiklerinin ek insan incelemesini veya alternatif karar yollarını tetiklediğini doğrulayın. |   2    | D/V |
| 13.6.3 | Belirsizlik nicelleme yöntemlerinin kalibre edilmiş ve gerçek veri ile doğrulanmış olduğunu teyit edin. |   2    |  V  |
| 13.6.4 | Belirsizlik yayılımının çok adımlı AI iş akışları boyunca sürdürüldüğünü doğrulayın.                    |   3    | D/V |

---

## C13.7 Kullanıcıya Yönelik Şeffaflık Raporları

Olaylar, sapma ve veri kullanımı hakkında periyodik bildirimler sağlayın.

|   #    | Açıklama                                                                                                                                      | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.7.1 | Veri kullanımı politikalarının ve kullanıcı onay yönetimi uygulamalarının paydaşlara açıkça iletildiğini doğrulayın.                          |   1    | D/V |
| 13.7.2 | Yapay zeka etki değerlendirmelerinin yapıldığını ve sonuçların raporlamaya dahil edildiğini doğrulayın.                                       |   2    | D/V |
| 13.7.3 | Düzenli olarak yayınlanan şeffaflık raporlarının, makul ayrıntılarla Yapay Zeka olaylarını ve operasyonel metrikleri açıkladığını doğrulayın. |   2    | D/V |

### Referanslar

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

