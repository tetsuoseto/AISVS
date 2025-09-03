# C1 Eğitim Verisi Yönetişimi ve Yanlılık Yönetimi

## Kontrol Amacı

Eğitim verileri, kökeninin korunmasını, güvenliğini, kalitesini ve tarafsızlığını koruyacak şekilde tedarik edilmeli, işlenmeli ve sürdürülmelidir. Bunu yapmak yasal yükümlülükleri yerine getirir ve eğitim sırasında ortaya çıkabilecek önyargı, zehirlenme veya mahremiyet ihlallerinin risklerini azaltır; bu tür riskler tüm Yapay Zeka yaşam döngüsünü etkileyebilir.

---

## C1.1 Eğitim Verisinin Kökeni

Tüm veri kümelerinin doğrulanabilir bir envanterini tutun, yalnızca güvenilir kaynakları kabul edin ve denetim için her değişikliği kaydedin.

|   #   | Açıklama                                                                                                                                                                                | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.1.1 | Her eğitim verisi kaynağının (kaynak, sorumlu/sahibi, lisans, toplama yöntemi, kullanım amacıyla ilgili kısıtlamalar ve işleme geçmişi) güncel bir envanterin tutulduğunu doğrulayın.   |   1    | D/V |
| 1.1.2 | Eğitim verilerini işleyen süreçlerin gereksiz özellikleri, nitelikleri veya alanları hariç tuttuğunu doğrulayın (ör. kullanılmayan meta veriler, hassas PII, sızdırılan test verileri). |   1    | D/V |
| 1.1.3 | Tüm veri kümesi değişikliklerinin kaydedilmiş bir onay iş akışına tabi olduğundan emin olun.                                                                                            |   2    | D/V |
| 1.1.4 | Mümkün olduğunda, veri kümelerinin veya alt kümelerinin su işaretli veya parmak iziyle izlenebilir olduğundan emin olun.                                                                |   3    | D/V |

---

## C1.2 Eğitim Verileri Güvenliği ve Bütünlüğü

Eğitim verilerine erişimi kısıtlayın, verileri dinlenirken ve iletim sırasında şifreleyin ve bozulmayı, hırsızlığı veya veri zehirlenmesini önlemek için bütünlüklerini doğrulayın.

|   #   | Açıklama                                                                                                                                                                                           | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.2.1 | Erişim kontrollerinin eğitim verisi depolama alanını ve iş akışlarını koruduğunu doğrulayın.                                                                                                       |   1    | D/V |
| 1.2.2 | Tüm eğitim verilerine erişimin kaydedildiğini doğrulayın; kullanıcı, zaman ve eylem dahil.                                                                                                         |   2    | D/V |
| 1.2.3 | Eğitim veri kümelerinin aktarım sırasında ve dinlenme halinde şifreli olduğundan emin olun; endüstri standartlarına uygun kriptografik algoritmalar ve anahtar yönetimi uygulamaları kullanın.     |   2    | D/V |
| 1.2.4 | Eğitim verisinin depolanması ve aktarımı sırasında veri bütünlüğünün sağlandığından emin olmak için kriptografik özetlerin veya dijital imzaların kullanıldığını doğrulayın.                       |   2    | D/V |
| 1.2.5 | Eğitim verisinin yetkisiz değişikliklere veya bozulmasına karşı korunması için otomatik tespit tekniklerinin uygulanığından emin olun.                                                             |   2    | D/V |
| 1.2.6 | Kullanım dışı eğitim verilerinin güvenli bir şekilde temizlendiğini veya anonimleştirildiğini doğrulayın.                                                                                          |   2    | D/V |
| 1.2.7 | Tüm eğitim veri kümesi sürümlerinin benzersiz biçimde tanımlandığını, değiştirilemez biçimde saklandığını ve denetlenebilir olduğunu doğrulayın; bu, geri alma işlemini ve adli analizi destekler. |   3    | D/V |

---

## C1.3 Eğitim Verisi Etiketleme Kalitesi, Bütünlüğü ve Güvenliği

Etiketleri koruyun ve kritik veriler için teknik incelemenin yapılmasını zorunlu kılın.

|   #   | Açıklama                                                                                                                                                                                                                       | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 1.3.1 | Etiketlenen artefaktlara kriptografik özetlerin veya dijital imzaların uygulandığından emin olun; böylece bütünlükleri ve özgünlükleri sağlanır.                                                                               |   2    | D/V |
| 1.3.2 | Etiketleme arabirimlerinin ve platformlarının güçlü erişim kontrollerini uyguladığından, tüm etiketleme aktivitelerinin bozulmaz denetim günlüklerini sürdürdüğünden ve yetkisiz değişikliklere karşı korunduğundan emin olun. |   2    | D/V |
| 1.3.3 | Etiketlerdeki hassas bilgilerin veri alanı düzeyinde dinlenim halinde ve iletim sırasında kırpılmış, anonimleştirilmiş veya şifreli olduğundan emin olun.                                                                      |   3    | D/V |

---

## C1.4 Eğitim Verisinin Kalitesi ve Güvenliğinin Sağlanması

Veri setinin güvenilirliğini garanti etmek için otomatik doğrulamayı, manuel rastgele kontrolleri ve kaydedilmiş düzeltmeleri birleştirin.

|   #   | Açıklama                                                                                                                                                                                                                                                                                                                                                                                                                                   | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 1.4.1 | Otomatik testlerin her veri içe aktarımında veya önemli veri dönüşümünde biçim hatalarını ve null değerlerini yakaladığını doğrulayın.                                                                                                                                                                                                                                                                                                     |   1    |  D  |
| 1.4.2 | LLM eğitim ve ince ayar iş akışlarının zehirlenme tespiti ve veri bütünlüğü doğrulamasını uyguladığını doğrulayın (ör. istatistiksel yöntemler, aykırı değer tespiti, gömme analizi) ve bunun potansiyel zehirlenme saldırılarını (ör. etiket değiştirme, arka kapı tetikleyici ekleme, rol değiştirme komutları, etkili örnek saldırıları) veya eğitim verilerindeki istemsiz veri bozulmasını belirlemek için kullanıldığını teyit edin. |   2    | D/V |
| 1.4.3 | Risk değerlendirmesine dayanarak, adversarial eğitim (üretilen adversarial örnekler kullanılarak), bozulmuş girdilerle veri artırımı veya dayanıklı optimizasyon teknikleri gibi uygun savunmaların uygulanıp ayarlandığından emin olun.                                                                                                                                                                                                   |   3    | D/V |
| 1.4.4 | Otomatik olarak oluşturulan etiketlerin (örneğin LLM’ler veya zayıf denetim yoluyla elde edilenlerin) güven eşiklerine ve tutarlılık kontrollerine tabi olduğunu doğrulayın; bu kontroller, hayal ürünü, yanıltıcı veya düşük güvenilirliğe sahip etiketleri tespit etmek için uygulanır.                                                                                                                                                  |   2    | D/V |
| 1.4.5 | Otomatik testlerin her veri içe aktarımında veya önemli veri dönüşümünde etiket sapmalarını yakalamasını doğrulayın.                                                                                                                                                                                                                                                                                                                       |   3    |  D  |

---

## C1.5 Veri Kökeni ve İzlenebilirlik

Her veri noktasının kaynaktan model girdisine kadar olan tam sürecini denetlenebilirlik ve olay müdahalesi için izleyin.

|   #   | Açıklama                                                                                                                                                                                                                          | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 1.5.1 | Her bir veri noktasının kökeninin, tüm dönüşümlerin, artırmaların ve birleşmelerin dahil olduğu şekilde kaydedildiğini ve yeniden oluşturulabileceğini doğrulayın.                                                                |   2    | D/V |
| 1.5.2 | Veri soyağacı kayıtlarının değiştirilemez, güvenli bir şekilde saklandığını ve denetimler için erişilebilir olduğunu doğrulayın.                                                                                                  |   2    | D/V |
| 1.5.3 | Doğrulayın ki veri kökeninin izlenmesi, mahremiyeti koruyan veya üretken tekniklerle üretilen sentetik verileri kapsıyor ve tüm sentetik veriler açıkça etiketlenmiş ve gerçek veriden iş akışı boyunca ayırt edilebilir durumda. |   2    | D/V |

---

## Kaynaklar

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

