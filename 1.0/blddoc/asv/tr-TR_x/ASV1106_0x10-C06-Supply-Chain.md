# C6 Modeller, Çerçeveler ve Veri için Tedarik Zinciri Güvenliği

## Kontrol Amacı

Yapay zeka tedarik zinciri saldırıları, üçüncü taraf modelleri, çerçeveleri veya veri kümelerini kullanarak arka kapılar, önyargılar veya kullanılabilir kodlar yerleştirir. Bu kontroller, tüm model yaşam döngüsünü korumak için uçtan uca köken takibi, zafiyet yönetimi ve izleme sağlar.

---

## C6.1 Önceden Eğitilmiş Modelin İncelenmesi ve Kökeni

Herhangi bir ince ayar veya dağıtımdan önce üçüncü taraf model kaynaklarını, lisanslarını ve gizli davranışlarını değerlendirin ve doğrulayın.

|   #   | Açıklama                                                                                                                                                     | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 6.1.1 | Her üçüncü taraf model öğesinin, kaynak deposunu ve commit hash'ini belirten imzalı bir köken kaydı içerdiğini doğrulayın.                                   |   1    | D/V |
| 6.1.2 | Modellerin, içe aktarılmadan önce otomatik araçlar kullanılarak kötü amaçlı katmanlar veya Truva tetikleyicileri açısından tarandığından emin olun.          |   1    | D/V |
| 6.1.3 | Transfer öğreniminin ince ayarının, gizli davranışları tespit etmek için düşmanca değerlendirmeyi geçtiğini doğrulayın.                                      |   2    |  D  |
| 6.1.4 | Model lisanslarının, ihracat kontrol etiketlerinin ve veri kaynağı beyanlarının bir ML-BOM girdisinde kaydedildiğini doğrulayın.                             |   2    |  V  |
| 6.1.5 | Yüksek riskli modellerin (kamuya yüklenmiş ağırlıklar, doğrulanmamış yaratıcılar) insan incelemesi ve onayı yapılana kadar karantinada kaldığını doğrulayın. |   3    | D/V |

---

## C6.2 Çerçeve ve Kütüphane Tarama

Çalışma zamanı yığınını güvenli tutmak için ML çerçevelerini ve kütüphanelerini sürekli olarak CVE'ler ve kötü amaçlı kodlar açısından tarayın.

|   #   | Açıklama                                                                                                                                  | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.2.1 | CI boru hatlarının AI çerçeveleri ve kritik kütüphaneler üzerinde bağımlılık tarayıcılarını çalıştırdığını doğrulayın.                    |   1    | D/V |
| 6.2.2 | Kritik güvenlik açıklarının (CVSS ≥ 7.0) üretim imajlarına geçişi engellediğini doğrulayın.                                               |   1    | D/V |
| 6.2.3 | Çatallanmış veya satın alınmış ML kütüphanelerinde statik kod analizinin çalıştığını doğrulayın.                                          |   2    |  D  |
| 6.2.4 | Çerçeve yükseltme önerilerinin, genel CVE beslemelerine atıfta bulunan bir güvenlik etki değerlendirmesi içerdiğini doğrulayın.           |   2    |  V  |
| 6.2.5 | Çalışma zamanı sensörlerinin, imzalanmış SBOM'dan sapma gösteren beklenmeyen dinamik kütüphane yüklemelerinde uyarı verdiğini doğrulayın. |   3    |  V  |

---

## C6.3 Bağımlılık Sabitleme ve Doğrulama

Her bağımlılığı değişmez özetlere sabitleyin ve aynı, müdahale edilmemiş yapıları garanti etmek için yapıları yeniden üretin.

|   #   | Açıklama                                                                                                                                         | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 6.3.1 | Tüm paket yöneticilerinin sürüm sabitlemesini kilit dosyaları aracılığıyla zorunlu kıldığını doğrulayın.                                         |   1    | D/V |
| 6.3.2 | Konteyner referanslarında değiştirilebilir etiketler yerine değiştirilemez özetlerin kullanıldığını doğrulayın.                                  |   1    | D/V |
| 6.3.3 | Tekrar üretilebilir derleme kontrollerinin, aynı çıktıları sağlamak için CI çalışmaları arasında karma değerlerini karşılaştırdığını doğrulayın. |   2    |  D  |
| 6.3.4 | Denetim izlenebilirliği için yapı doğrulamaların 18 ay süreyle saklandığını doğrulayın.                                                          |   2    |  V  |
| 6.3.5 | Süresi dolmuş bağımlılıkların, sabitlenmiş sürümleri güncellemek veya çatallamak için otomatik PR’leri tetiklediğini doğrulayın.                 |   3    |  D  |

---

## C6.4 Güvenilir Kaynak Uygulaması

Sadece kriptografik olarak doğrulanmış, organizasyon tarafından onaylanmış kaynaklardan eser indirmelerine izin verin ve diğer her şeyi engelleyin.

|   #   | Açıklama                                                                                                                                               | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 6.4.1 | Model ağırlıklarının, veri setlerinin ve konteynerlerin yalnızca onaylanmış alan adlarından veya dahili kayıt defterlerinden indirildiğini doğrulayın. |   1    | D/V |
| 6.4.2 | Sigstore/Cosign imzalarının, eserler yerel olarak önbelleğe alınmadan önce yayımcı kimliğini doğruladığını kontrol edin.                               |   1    | D/V |
| 6.4.3 | Çıkış vekillerinin, güvenilir kaynak politikasını uygulamak için kimlik doğrulaması yapılmamış eser indirmelerini engellediğini doğrulayın.            |   2    |  D  |
| 6.4.4 | Depo izin listelerinin her bir giriş için iş gerekçesi kanıtı ile birlikte çeyrek dönemlerde gözden geçirildiğini doğrulayın.                          |   2    |  V  |
| 6.4.5 | Politika ihlallerinin, artefaktların karantinaya alınmasını ve bağlı pipeline çalışmalarının geri alınmasını tetiklediğini doğrulayın.                 |   3    |  V  |

---

## C6.5 Üçüncü Taraf Veri Seti Risk Değerlendirmesi

Dış veri setlerini zehirlenme, önyargı ve yasal uyumluluk açısından değerlendirin ve yaşam döngüleri boyunca izlemesini yapın.

|   #   | Açıklama                                                                                                                               | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.5.1 | Dış veri setlerinin zehirlenme riski puanlamasından geçirildiğini doğrulayın (örneğin, veri parmak izi çıkarma, aykırı değer tespiti). |   1    | D/V |
| 6.5.2 | Önyargı metriklerinin (demografik denklik, eşit fırsat) veri seti onayından önce hesaplandığını doğrulayın.                            |   1    |  D  |
| 6.5.3 | Verilerin kökeni ve lisans koşullarının ML-BOM girdilerinde kaydedildiğini doğrulayın.                                                 |   2    |  V  |
| 6.5.4 | Barındırılan veri setlerindeki kayma veya bozulmanın düzenli izleme ile tespit edildiğini doğrulayın.                                  |   2    |  V  |
| 6.5.5 | Eğitim öncesinde, yasaklanmış içeriklerin (telif hakkı, KİB) otomatik temizleme yoluyla kaldırıldığını doğrulayın.                     |   3    |  D  |

---

## C6.6 Tedarik Zinciri Saldırısı İzleme

CVE beslemeleri, denetim kaydı analizleri ve kırmızı takım simülasyonları aracılığıyla tedarik zinciri tehditlerini erken tespit edin.

|   #   | Açıklama                                                                                                                                                  | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.6.1 | Anormal paket çekimleri veya değiştirilmiş derleme adımları için CI/CD denetim günlüklerinin SIEM algılamalarına aktarıldığını doğrulayın.                |   1    |  V  |
| 6.6.2 | Olay müdahale oyun kitaplarının, ele geçirilmiş modeller veya kütüphaneler için geri alma prosedürlerini içerdiğini doğrulayın.                           |   2    |  D  |
| 6.6.3 | Tehdit istihbaratı zenginleştirme etiketlerinin, uyarı üçlemesinde ML'ye özgü göstergeleri (örneğin, model zehirleme IoC'leri) doğruladığından emin olun. |   3    |  V  |

---

## C6.7 Model Nesneleri için ML-BOM

Ayrıntılı ML'ye özgü SBOM'lar (ML-BOM'lar) oluşturun ve imzalayın, böylece sonraki kullanıcılar bileşen bütünlüğünü dağıtım zamanında doğrulayabilir.

|   #   | Açıklama                                                                                                                                       | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.7.1 | Her model öğesinin veri setlerini, ağırlıkları, hiperparametreleri ve lisansları listeleyen bir ML-BOM yayınladığını doğrulayın.               |   1    | D/V |
| 6.7.2 | ML-BOM üretimi ve Cosign imzasının CI'da otomatikleştirildiğini ve birleştirme için zorunlu olduğunu doğrulayın.                               |   1    | D/V |
| 6.7.3 | Herhangi bir bileşen meta verisi (hash, lisans) eksikse, ML‑BOM tamlık kontrollerinin derlemeyi başarısız kıldığını doğrulayın.                |   2    |  D  |
| 6.7.4 | Aşağıdaki kullanıcıların, dağıtım zamanında ithal edilen modelleri doğrulamak için API aracılığıyla ML-BOM'ları sorgulayabildiğini doğrulayın. |   2    |  V  |
| 6.7.5 | ML‑BOM'ların sürüm kontrolünün yapıldığını ve yetkisiz değişiklikleri tespit etmek için farklarının alındığını doğrulayın.                     |   3    |  V  |

---

## Referanslar

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

