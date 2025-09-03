# C6 Modeller, Çerçeveler ve Veriler için Tedarik Zinciri Güvenliği

## Kontrol Amacı

Yapay zeka tedarik zinciri saldırıları, üçüncü taraf modelleri, çerçeveler veya veri kümelerini arka kapılar, önyargı veya istismar edilebilir kod eklemek amacıyla kullanır. Bu kontroller uçtan uca köken bilgisi, zafiyet yönetimi ve izleme sağlayarak tüm model yaşam döngüsünü korur.

---

## C6.1 Önceden Eğitilmiş Modelin Değerlendirilmesi ve Kökeni

Üçüncü taraf model kökenlerini, lisanslarını ve gizli davranışlarını herhangi bir ince ayar veya devreye alma öncesinde değerlendirip doğrulayın.

|   #   | Açıklama                                                                                                                                                                   | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.1.1 | Her üçüncü taraf model artefaktının imzalı bir menşe kaydı içerdiğini ve bu kaydın kaynak deposunu ve commit hash'ini tanımladığını doğrulayın.                            |   1    | D/V |
| 6.1.2 | Modellerin içe aktarılmadan önce otomatik araçlarla kötü niyetli katmanlar veya Trojan tetikleyicileri için tarandığından emin olun.                                       |   1    | D/V |
| 6.1.3 | Doğrulayın ki transfer‑learning ile yapılan ince ayarların adversarial değerlendirmenin geçmesini sağlayıp gizli davranışları tespit ettiğini.                             |   2    |  D  |
| 6.1.4 | Model lisanslarının, ihracat kontrol etiketlerinin ve veri kökeni beyanlarının ML-BOM girdisine kaydedildiğini doğrulayın.                                                 |   2    |  V  |
| 6.1.5 | Yüksek riskli modellerin (halka açık olarak yüklenen ağırlıklar, doğrulanmamış geliştiriciler) insan incelemesi ve onayı tamamlanana kadar karantinada kalmasını sağlayın. |   3    | D/V |

---

## C6.2 Çerçeve ve Kütüphane Taraması

Çalışma zamanı yığını güvenli tutmak için ML çerçeveleri ve kütüphanelerini CVE'ler ve zararlı kod için sürekli olarak tarayın.

|   #   | Açıklama                                                                                                                                        | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.2.1 | CI süreçlerinin yapay zeka çerçeveleri ve kritik kütüphaneler üzerinde bağımlılık tarama araçlarını çalıştırdığından emin olun.                 |   1    | D/V |
| 6.2.2 | Kritik güvenlik açıklarının (CVSS ≥ 7.0) üretim görüntülerine geçişi engellediğini doğrulayın.                                                  |   1    | D/V |
| 6.2.3 | Fork edilmiş veya vendor edilen ML kütüphanelerinde statik kod analizi çalıştığını doğrulayın.                                                  |   2    |  D  |
| 6.2.4 | Çerçeve yükseltme önerilerinin, halka açık CVE beslemelerine atıfta bulunan bir güvenlik etkisi değerlendirmesi içerdiğini doğrulayın.          |   2    |  V  |
| 6.2.5 | İmzalanmış SBOM'dan sapacak şekilde beklenmeyen dinamik kütüphane yüklemeleri üzerinde çalışma zamanı sensörlerinin uyarı verdiğini doğrulayın. |   3    |  V  |

---

## C6.3 Bağımlılık Sabitleme ve Doğrulama

Her bağımlılığı değiştirilemez özetlerle kilitleyin ve derlemeleri yeniden üretin; böylece aynı, değiştirilmemiş çıktıların elde edilmesini garanti edin.

|   #   | Açıklama                                                                                                                                                 | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.3.1 | Tüm paket yöneticilerinin sürüm kilitlemesini kilit dosyaları aracılığıyla zorunlu kıldığını doğrulayın.                                                 |   1    | D/V |
| 6.3.2 | Konteyner referanslarında değiştirilemez özetlerin, değiştirilebilir etiketler yerine kullanıldığını doğrulayın.                                         |   1    | D/V |
| 6.3.3 | reproducible‑build kontrollerinin CI çalışmaları arasındaki hash değerlerini karşılaştırdığını doğrulayın ve çıktıların aynı olduğundan emin olun.       |   2    |  D  |
| 6.3.4 | Denetim izlenebilirliği için derleme doğrulamalarının 18 ay boyunca saklandığından emin olun.                                                            |   2    |  V  |
| 6.3.5 | Geçerliliğini yitirmiş bağımlılıkların otomatik PR'leri tetikleyerek sabitlenmiş sürümlerin güncellenmesini veya fork edilmesini sağladığını doğrulayın. |   3    |  D  |

---

## C6.4 Güvenilir Kaynak Denetimi

Sadece kriptografik olarak doğrulanmış, kuruluş tarafından onaylanmış kaynaklardan artefakt indirmelerine izin verin ve diğer her şeyi engelleyin.

|   #   | Açıklama                                                                                                                                      | Seviye | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.4.1 | Model ağırlıklarının, veri kümelerinin ve konteynerlerin yalnızca onaylı alanlardan veya dahili kayıt depolarından indirildiğini doğrulayın.  |   1    | D/V |
| 6.4.2 | Sigstore/Cosign imzalarının yayımlayıcı kimliğini, artefaktlar yerel olarak önbelleğe alınmadan önce doğrulayın.                              |   1    | D/V |
| 6.4.3 | Güvenilir‑kaynak politikası uygulamak için çıkış proxy'lerinin kimlik doğrulaması yapılmamış artefakt indirmelerini engellediğini doğrulayın. |   2    |  D  |
| 6.4.4 | Depo izin listelerinin her giriş için işletme gerekçesi kanıtı ile birlikte üç ayda bir gözden geçirildiğini doğrulayın.                      |   2    |  V  |
| 6.4.5 | Politika ihlallerinin artefaktların karantinaya alınmasına ve bağımlı pipeline çalıştırmalarının geri alınmasına yol açtığını doğrulayın.     |   3    |  V  |

---

## C6.5 Üçüncü‑Taraf Veri Kümesi Risk Değerlendirmesi

Dış veri setlerini zehirlenmeye karşı, yanlılık ve yasal uygunluk açısından değerlendirip yaşam döngüsü boyunca izleyin.

|   #   | Açıklama                                                                                                                                     | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.5.1 | Harici veri kümelerinin zehirlenme riski puanlamasına tabi tutulduğunu doğrulayın (örneğin, veri parmak izi çıkarımı, aykırı değer tespiti). |   1    | D/V |
| 6.5.2 | Veri kümesinin onayından önce önyargı metriklerinin (demografik eşitlik, eşit fırsat) hesaplandığından emin olun.                            |   1    |  D  |
| 6.5.3 | Veri kümeleri için köken ve lisans koşullarının ML‑BOM girdilerine kaydedildiğini doğrulayın.                                                |   2    |  V  |
| 6.5.4 | Barındırılan veri kümelerinde periyodik izlemenin drift veya bozulmayı tespit ettiğini doğrulayın.                                           |   2    |  V  |
| 6.5.5 | İzinsiz içeriğin (telif hakkı, PII) eğitime başlamadan önce otomatik temizleme ile kaldırıldığını doğrulayın.                                |   3    |  D  |

---

## C6.6 Tedarik Zinciri Saldırı İzleme

Tedarik-zinciri tehditlerini CVE beslemeleri, audit-log analitiği ve red-team simülasyonları yoluyla erken tespit edin.

|   #   | Açıklama                                                                                                                                              | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.6.1 | CI/CD denetim günlüklerinin anormal paket çekmeleri veya değiştirilmiş derleme adımları için SIEM tespitlerine iletilmesini doğrulayın.               |   1    |  V  |
| 6.6.2 | Olay müdahale kılavuzlarının, ele geçirilmiş modeller veya kütüphaneler için geri alma prosedürlerini içerdiğini doğrulayın.                          |   2    |  D  |
| 6.6.3 | Tehdit‑istihbaratı zenginleştirmesinin ML‑e özgü göstergeleri etiketlediğini uyarı triage'inde doğrulayın (örnek olarak model‑zehirlenmesi IoC'leri). |   3    |  V  |

---

## C6.7 Model Artefaktları için ML‑BOM

Dağıtım zamanında bileşen bütünlüğünü doğrulayabilmeleri için ayrıntılı ML'e özgü SBOM'lar (ML-BOM'lar) oluşturun ve imzalayın.

|   #   | Açıklama                                                                                                                                                      | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 6.7.1 | Her model artefaktının, veri setlerini, ağırlıkları, hiperparametreleri ve lisansları içeren bir ML‑BOM yayımladığını doğrulayın.                             |   1    | D/V |
| 6.7.2 | ML‑BOM üretiminin ve Cosign imzalama işlemlerinin CI'de otomatikleştirildiğini ve birleştirme için zorunlu olduğunu doğrulayın.                               |   1    | D/V |
| 6.7.3 | ML‑BOM tamamlık kontrollerinin herhangi bir bileşen meta verisi (hash değeri, lisans) eksik olduğunda derlemenin başarısız olmasına yol açacağını doğrulayın. |   2    |  D  |
| 6.7.4 | Aşağı akıştaki tüketicilerin dağıtım zamanında içe aktarılan modelleri doğrulamak için API üzerinden ML-BOM'ları sorgulayabildiğini doğrulayın.               |   2    |  V  |
| 6.7.5 | ML‑BOM’lar sürüm kontrolünde tutulduğundan ve yetkisiz değişiklikleri tespit etmek için fark karşılaştırması yapıldığından emin olun.                         |   3    |  V  |

---

## Kaynaklar

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

