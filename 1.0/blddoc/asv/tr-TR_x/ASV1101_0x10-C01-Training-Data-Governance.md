# C1 Eğitim Verisi Yönetimi ve Önyargı Yönetimi

## Kontrol Amacı

Eğitim verileri, köken, güvenlik, kalite ve adaleti koruyacak şekilde temin edilmeli, işlenmeli ve sürdürülmelidir. Bu, yasal sorumlulukların yerine getirilmesini sağlar ve tüm Yapay Zeka yaşam döngüsünü etkileyebilecek önyargı, zehirlenme veya gizlilik ihlalleri risklerini azaltır.

---

## C1.1 Eğitim Verisi Kökeni

Tüm veri setlerinin doğrulanabilir bir envanterini tutun, yalnızca güvenilir kaynakları kabul edin ve denetlenebilirlik için her değişikliği kaydedin.

|   #   | Açıklama                                                                                                                                                                      | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.1.1 | Her eğitim veri kaynağının (kaynak, sorumlu/sahip, lisans, toplama yöntemi, amaçlanan kullanım kısıtlamaları ve işleme geçmişi) güncel envanterinin tutulduğunu doğrulayın.   |   1    | D/V |
| 1.1.2 | Eğitim veri işlemlerinin gereksiz özellikleri, nitelikleri veya alanları (örneğin, kullanılmayan meta veriler, hassas KİB, sızdırılmış test verileri) dışladığını doğrulayın. |   1    | D/V |
| 1.1.3 | Tüm veri kümesi değişikliklerinin kaydedilmiş bir onay iş akışına tabi olduğunu doğrulayın.                                                                                   |   2    | D/V |
| 1.1.4 | Veri kümelerinin veya alt kümelerin mümkün olduğunda filigranlı veya parmak izli olduğundan emin olun.                                                                        |   3    | D/V |

---

## C1.2 Eğitim Verisi Güvenliği ve Bütünlüğü

Erişimi eğitim verilerine kısıtlayın, verileri dinlenme ve aktarım sırasında şifreleyin ve değişiklik, hırsızlık veya veri zehirlenmesini önlemek için bütünlüğünü doğrulayın.

|   #   | Açıklama                                                                                                                                                                                 | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.2.1 | Erişim kontrollerinin eğitim verisi depolama ve veri işleme hatlarını koruduğunu doğrulayın.                                                                                             |   1    | D/V |
| 1.2.2 | Erişim yapan kişi, zaman ve işlemi de içerecek şekilde, eğitim verisine yapılan tüm erişimlerin kaydedildiğini doğrulayın.                                                               |   2    | D/V |
| 1.2.3 | Eğitim veri setlerinin, sektör standardı kriptografik algoritmalar ve anahtar yönetimi uygulamaları kullanılarak hem iletim sırasında hem de depolama halinde şifrelendiğini doğrulayın. |   2    | D/V |
| 1.2.4 | Eğitim verilerinin depolanması ve aktarımı sırasında veri bütünlüğünü sağlamak için kriptografik özetlerin veya dijital imzaların kullanıldığını doğrulayın.                             |   2    | D/V |
| 1.2.5 | Otomatik tespit tekniklerinin, eğitim verilerinin yetkisiz değişikliklere veya bozulmalara karşı korunması için uygulandığını doğrulayın.                                                |   2    | D/V |
| 1.2.6 | Eski eğitim verilerinin güvenli bir şekilde silindiğini veya anonim hale getirildiğini doğrulayın.                                                                                       |   2    | D/V |
| 1.2.7 | Tüm eğitim veri seti sürümlerinin benzersiz şekilde tanımlandığını, değiştirilemez şekilde saklandığını ve geri alma ile adli analiz desteği için denetlenebilir olduğunu doğrulayın.    |   3    | D/V |

---

## C1.3 Eğitim Verisi Etiketleme Kalitesi, Bütünlüğü ve Güvenliği

Etiketleri koruyun ve kritik veriler için teknik inceleme gerektirin.

|   #   | Açıklama                                                                                                                                                                                                                                  | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.3.1 | Etiket artefaktlarının bütünlüğünü ve özgünlüğünü sağlamak için kriptografik özetlerin veya dijital imzaların uygulandığını doğrulayın.                                                                                                   |   2    | D/V |
| 1.3.2 | Etiketleme arayüzlerinin ve platformlarının güçlü erişim kontrolleri uyguladığını, tüm etiketleme faaliyetlerinin tahrifata karşı dayanıklı denetim kayıtlarını tuttuğunu ve yetkisiz değişikliklere karşı koruma sağladığını doğrulayın. |   2    | D/V |
| 1.3.3 | Etiketlerdeki hassas bilgilerin, veri alanı düzeyinde, hem dururken hem de iletim halinde sansürlendiğini, anonimleştirildiğini veya şifrelenmiş olduğunu doğrulayın.                                                                     |   3    | D/V |

---

## C1.4 Eğitim Verisi Kalitesi ve Güvenlik Güvencesi

Veri seti güvenilirliğini garanti altına almak için otomatik doğrulama, manuel örnekleme kontrolleri ve kaydedilmiş düzeltmeler birleştirin.

|   #   | Açıklama                                                                                                                                                                                                                                                                                                                                                                                                      | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.4.1 | Otomatik testlerin her ingest veya önemli veri dönüşümünde format hatalarını ve null değerleri yakaladığını doğrulayın.                                                                                                                                                                                                                                                                                       |   1    |  D  |
| 1.4.2 | LLM eğitim ve ince ayar işlemlerinin, potansiyel zehirleme saldırılarını (örneğin, etiket çevirme, arka kapı tetikleyici ekleme, rol değiştirme komutları, etkili örnek saldırıları) veya eğitim verilerindeki kasıtsız veri bozulmalarını tanımlamak için zehirleme tespiti ve veri bütünlüğü doğrulamasını (örneğin, istatistiksel yöntemler, aykırı değer tespiti, gömme analizi) uyguladığını doğrulayın. |   2    | D/V |
| 1.4.3 | Risk değerlendirmesine dayalı olarak ilgili modeller için üretilmiş adversaryal örnekler kullanılarak adversaryal eğitim, bozulmuş girdilerle veri artırımı veya sağlam optimizasyon teknikleri gibi uygun savunmaların uygulanmış ve ayarlanmış olduğunu doğrulayın.                                                                                                                                         |   3    | D/V |
| 1.4.4 | Otomatik olarak oluşturulan etiketlerin (örneğin, LLM'ler veya zayıf denetim yoluyla) halüsinasyonlu, yanıltıcı veya düşük güvenilirlikteki etiketleri tespit etmek için güven eşiği ve tutarlılık kontrollerine tabi tutulduğunu doğrulayın.                                                                                                                                                                 |   2    | D/V |
| 1.4.5 | Otomatik testlerin, her veri alma veya önemli veri dönüşümünde etiket kaymalarını yakaladığını doğrulayın.                                                                                                                                                                                                                                                                                                    |   3    |  D  |

---

## C1.5 Veri Soyu ve İzlenebilirlik

Denetlenebilirlik ve olay müdahalesi için her veri noktasının kaynaktan modele girişe kadar olan tam yolculuğunu izleyin.

|   #   | Açıklama                                                                                                                                                                                                                                   | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 1.5.1 | Her veri noktasının soy geçmişinin, tüm dönüşümler, artırmalar ve birleştirmeler dahil olmak üzere, kaydedildiğini ve yeniden oluşturulabileceğini doğrulayın.                                                                             |   2    | D/V |
| 1.5.2 | Soy kütüğü kayıtlarının değiştirilemez, güvenli bir şekilde saklandığından ve denetimler için erişilebilir olduğundan emin olun.                                                                                                           |   2    | D/V |
| 1.5.3 | Soy izleme mekanizmasının gizliliği koruyan veya üretici tekniklerle oluşturulan sentetik verileri kapsadığını ve tüm sentetik verilerin boru hattı boyunca gerçek verilerden açıkça etiketlenmiş ve ayırt edilebilir olduğunu doğrulayın. |   2    | D/V |

---

## Referanslar

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

