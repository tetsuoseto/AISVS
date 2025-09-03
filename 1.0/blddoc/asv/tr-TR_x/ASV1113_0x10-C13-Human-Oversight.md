# C13 İnsan Gözetimi, Hesap Verebilirlik ve Yönetişim

## Kontrol Amacı

Bu bölüm, yapay zeka sistemlerinde insan denetimini sürdürmeye ve net hesap verebilirlik zincirlerinin kurulmasına ilişkin gereksinimleri sunar; bu gereksinimler, yapay zeka yaşam döngüsü boyunca açıklık, şeffaflık ve etik sorumluluk bilincinin sağlanmasını güvence altına alır.

---

## C13.1 Kill-Switch & Geçersiz Kılma Mekanizmaları

Güvensiz davranış gözlemlendiğinde yapay zeka sistemi için kapatma veya geri alma yollarını sağlayın.

|   #    | Açıklama                                                                                                                                 | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.1.1 | Yapay zeka modelinin çıkarımını ve çıktılarını derhal durdurmak için manuel bir acil durdurma mekanizmasının mevcut olduğunu doğrulayın. |   1    | D/V |
| 13.1.2 | Override kontrollerinin yalnızca yetkili personelin erişimine açık olduğundan emin olun.                                                 |   1    |  D  |
| 13.1.3 | Geri alma prosedürlerinin önceki model sürümlerine veya güvenli mod işlemlerine geri dönebileceğini doğrulayın.                          |   3    | D/V |
| 13.1.4 | Override mekanizmalarının düzenli olarak test edildiğini doğrulayın.                                                                     |   3    |  V  |

---

## C13.2 İnsan Katılımlı Karar Noktaları

Belirlenen risk eşiklerini aştığında insan onayı gerekir.

|   #    | Açıklama                                                                                                                                        | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.2.1 | Yüksek riskli yapay zeka kararlarının icra edilmeden önce açık insan onayını gerektirdiğini doğrulayın.                                         |   1    | D/V |
| 13.2.2 | Risk eşiklerinin açıkça tanımlandığından emin olun ve bu eşikler otomatik olarak insan incelemesi iş akışlarını tetiklesin.                     |   1    |  D  |
| 13.2.3 | Zamana duyarlı kararlar için gereken süreler içinde insan onayı alınamazsa yedek prosedürlerin mevcut olduğundan emin olun.                     |   2    |  D  |
| 13.2.4 | Yükseltme prosedürlerinin, uygulanabilir ise, farklı karar türleri veya risk kategorileri için net yetki seviyelerini tanımladığını doğrulayın. |   3    | D/V |

---

## C13.3 Sorumluluk Zinciri ve Denetlenebilirlik

Operatör eylemlerini ve model kararlarını kaydedin.

|   #    | Açıklama                                                                                                                                              | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.3.1 | Tüm yapay zeka sistemi kararlarının ve insan müdahalelerinin zaman damgaları, kullanıcı kimlikleri ve karar gerekçeleriyle kaydedildiğini doğrulayın. |   1    | D/V |
| 13.3.2 | Denetim günlüklerinin değiştirilmez olduğunu doğrulayın ve bütünlük doğrulama mekanizmalarını dahil edin.                                             |   2    |  D  |

---

## C13.4 Açıklanabilir-Yapay Zeka Teknikleri

Yüzeysel Özelliklerin Önemi, Karşı-olgusal Açıklamalar ve Yerel Açıklamalar.

|   #    | Açıklama                                                                                                                                                             | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.4.1 | AI sistemlerinin kararlarını insanlar tarafından okunabilir bir biçimde temel açıklamalarla sunmalarını doğrulayın.                                                  |   1    | D/V |
| 13.4.2 | Açıklama kalitesinin insan değerlendirme çalışmaları ve metriklerle doğrulandığını doğrulayın.                                                                       |   2    |  V  |
| 13.4.3 | Kritik kararlar için öznitelik önem skorlarının veya atıf yöntemlerinin (SHAP, LIME, vb.) mevcut olduğundan emin olun.                                               |   3    | D/V |
| 13.4.4 | Kullanım vakasına ve alanına uygulanabilir ise, girdilerin çıktılarını değiştirmek için nasıl değiştirilebileceğini gösteren karşıt olgusal açıklamaları doğrulayın. |   3    |  V  |

---

## C13.5 Model Kartları ve Kullanım Açıklamaları

Kullanım amacı, performans metrikleri ve etik hususlar için model kartlarını sürdürün.

|   #    | Açıklama                                                                                                                                                                                                        | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.5.1 | Model kartlarının amaçlanan kullanım durumlarını, sınırlamaları ve bilinen başarısızlık modlarını belgelediğini doğrulayın.                                                                                     |   1    |  D  |
| 13.5.2 | Çeşitli ilgili kullanım senaryoları arasında performans metriklerinin açıklanmış olduğundan emin olun.                                                                                                          |   1    | D/V |
| 13.5.3 | Etik hususların, önyargı değerlendirmelerinin, adalet değerlendirmelerinin, eğitim verisi özelliklerinin ve bilinen eğitim verisi kısıtlamalarının belgelendiğini ve düzenli olarak güncellendiğini doğrulayın. |   2    |  D  |
| 13.5.4 | Model kartlarının sürüm kontrolüne tabi olduğundan ve değişiklik takibiyle model yaşam döngüsü boyunca güncel tutulduğundan emin olun.                                                                          |   2    | D/V |

---

## C13.6 Belirsizlik Nicelleştirme

Yanıtlar içinde güven skorlarını veya entropi ölçütlerini iletin.

|   #    | Açıklama                                                                                                           | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 13.6.1 | AI sistemlerinin çıktılarıyla güven skorları veya belirsizlik ölçütleri sağlandığını doğrulayın.                   |   1    |  D  |
| 13.6.2 | Belirsizlik eşiklerinin ilave insan incelemesini veya alternatif karar yollarını tetiklediğini doğrulayın.         |   2    | D/V |
| 13.6.3 | Belirsizlik nicelleştirme yöntemlerinin, gerçek değer verileriyle kalibre edildiğini ve doğrulandığını doğrulayın. |   2    |  V  |
| 13.6.4 | Çok adımlı yapay zeka iş akışları boyunca belirsizlik yayılımının korunup korunmadığını doğrulayın.                |   3    | D/V |

---

## C13.7 Kullanıcıya Yönelik Şeffaflık Raporları

Olaylar, kavram kayması ve veri kullanımıyla ilgili periyodik açıklamalar sunun.

|   #    | Açıklama                                                                                                                                                            | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 13.7.1 | Veri kullanım politikalarının ve kullanıcı onamı yönetim uygulamalarının paydaşlara açıkça iletildiğini doğrulayın.                                                 |   1    | D/V |
| 13.7.2 | Yapay zeka etki değerlendirmelerinin yapıldığını ve sonuçların raporlamaya dahil edildiğini doğrulayın.                                                             |   2    | D/V |
| 13.7.3 | Periyodik olarak yayımlanan şeffaflık raporlarının yapay zeka ile ilgili olayları ve operasyonel metrikleri makul düzeyde ayrıntılı olarak açıkladığını doğrulayın. |   2    | D/V |

### Kaynaklar

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

