# C4 Altyapısı, Yapılandırma ve Dağıtım Güvenliği

## Kontrol Amacı

Yapay zeka altyapısı, güvenli yapılandırma, çalışma zamanı izolasyonu, güvenilir dağıtım hatları ve kapsamlı izleme yoluyla ayrıcalık yükseltme, tedarik zinciri manipülasyonu ve yanal hareketlere karşı güçlendirilmelidir. Sadece yetkili, doğrulanmış altyapı bileşenleri ve yapılandırmaları, güvenlik, bütünlük ve denetlenebilirliği koruyan kontrollü süreçler aracılığıyla üretime ulaşır.

Temel Güvenlik Hedefi: Yalnızca kriptografik olarak imzalanmış, güvenlik açıkları taranmış altyapı bileşenleri, güvenlik politikalarını uygulayan ve değiştirilemez denetim kayıtlarını koruyan otomatik doğrulama hatları aracılığıyla üretime ulaşır.

---

## C4.1 Çalışma Zamanı Ortamı İzolasyonu

Çekirdek seviyesi izolasyon ilkelikleri ve zorunlu erişim kontrolleri yoluyla konteyner kaçışlarını ve ayrıcalık yükseltmelerini önleyin.

|   #   | Açıklama                                                                                                                                                                                                                              | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.1.1 | Tüm yapay zeka konteynerlerinin, güvenlik temellerinde belgelenmiş CAP_SETUID, CAP_SETGID ve açıkça gerekli olan yetenekler dışındaki TÜM Linux yeteneklerini devre dışı bıraktığını doğrulayın.                                      |   1    | D/V |
| 4.1.2 | Seccomp profillerinin, önceden onaylanmış izin listelerinde (allowlist) olmayan tüm sistem çağrılarını (syscall) engellediğini, ihlallerin konteynerin sonlanmasına ve güvenlik uyarılarının oluşturulmasına yol açtığını doğrulayın. |   1    | D/V |
| 4.1.3 | AI iş yüklerinin salt okunur kök dosya sistemleri, geçici veriler için tmpfs ve kalıcı veriler için noexec bağlama seçenekleri uygulanmış isimlendirilmiş birimlerle çalıştığını doğrulayın.                                          |   2    | D/V |
| 4.1.4 | eBPF tabanlı çalışma zamanı izleme (Falco, Tetragon veya eşdeğeri) ayrıcalık yükseltme girişimlerini tespit eder ve kuruluşun müdahale süresi gereksinimleri dahilinde hatalı süreçleri otomatik olarak sonlandırdığını doğrulayın.   |   2    | D/V |
| 4.1.5 | Yüksek riskli AI iş yüklerinin, doğrulama kanıtı ile birlikte donanım izoleli ortamlarda (Intel TXT, AMD SVM veya özel çıplak-metal düğümler) çalıştığını doğrulayın.                                                                 |   3    | D/V |

---

## C4.2 Güvenli Derleme ve Dağıtım Hatları

Yeniden üretilebilir derlemeler ve imzalanmış artefaktlar aracılığıyla kriptografik bütünlüğü ve tedarik zinciri güvenliğini sağlayın.

|   #   | Açıklama                                                                                                                                                                                                                                     | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.2.1 | Her commit'te altyapı-kod olarak (infrastructure-as-code) tfsec, Checkov veya Terrascan gibi araçlarla tarandığını doğrulayın, CRITICAL veya HIGH şiddet derecesine sahip bulgularla yapılan birleşmeleri engelleyin.                        |   1    | D/V |
| 4.2.2 | Konteyner derlemelerinin, derlemeler arasında aynı SHA256 karmalarına sahip olacak şekilde yeniden oluşturulabilir olduğunu doğrulayın ve Sigstore ile imzalanmış SLSA Seviye 3 köken kanıtları oluşturun.                                   |   1    | D/V |
| 4.2.3 | Konteyner görüntülerinin, kayıt defterine itmeden önce CycloneDX veya SPDX SBOM'larını gömülü olarak içerdiğini ve Cosign ile imzalandığını doğrulayın; imzasız görüntüler dağıtımda reddedilsin.                                            |   2    | D/V |
| 4.2.4 | CI/CD işlemlerinin, organizasyonun güvenlik politikası sınırlarını aşmayan sürelerde geçerliliğe sahip olan HashiCorp Vault, AWS IAM Rolleri veya Azure Yönetilen Kimlikler tarafından sağlanan OIDC belirteçlerini kullandığını doğrulayın. |   2    | D/V |
| 4.2.5 | Cosign imzalarının ve SLSA köken bilgilerinin, konteyner yürütülmeden önce dağıtım sürecinde doğrulandığını ve doğrulama hatalarının dağıtımın başarısız olmasına neden olduğunu doğrulayın.                                                 |   2    | D/V |
| 4.2.6 | Yapı ortamlarının, kalıcı depolama olmadan ve üretim VPC’lerinden ağ izolasyonuna sahip geçici konteynerler veya VM’lerde çalıştığını doğrulayın.                                                                                            |   2    | D/V |

---

## C4.3 Ağ Güvenliği ve Erişim Kontrolü

Varsayılan reddet politikaları ve şifreli iletişimle sıfır güven ağı uygulayın.

|   #   | Açıklama                                                                                                                                                                                                                            | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.3.1 | Kubernetes NetworkPolicies veya herhangi bir eşdeğerinin, gerekli portlar (443, 8080 vb.) için açıkça izin kurallarıyla varsayılan olarak gelen/giden trafiği engelleyen (default-deny) bir yapılandırmayı uyguladığını doğrulayın. |   1    | D/V |
| 4.3.2 | SSH (port 22), RDP (port 3389) ve bulut metadata uç noktalarının (169.254.169.254) engellendiğini veya sertifika tabanlı kimlik doğrulaması gerektirdiğini doğrulayın.                                                              |   1    | D/V |
| 4.3.3 | Çıkış trafiğinin, alan adı izin listeleri kullanılarak HTTP/HTTPS proxyleri (Squid, Istio veya bulut NAT geçitleri) üzerinden filtrelendiğini ve engellenen isteklerin kayıt altına alındığını doğrulayın.                          |   2    | D/V |
| 4.3.4 | Hizmetler arası iletişimin, kurumsal politikaya uygun olarak döndürülen sertifikalarla karşılıklı TLS kullandığını ve sertifika doğrulamasının (skip-verify bayrakları olmadan) zorunlu tutulduğunu doğrulayın.                     |   2    | D/V |
| 4.3.5 | Yapay zeka altyapısının, doğrudan internet erişimi olmayan ayrı VPC/VNet’lerde çalıştığını ve yalnızca NAT ağ geçitleri veya bastion hostlar aracılığıyla iletişim kurduğunu doğrulayın.                                            |   2    | D/V |

---

## C4.4 Gizli Bilgi & Kriptografik Anahtar Yönetimi

Kimlik bilgilerini donanım destekli depolama ve sıfır güven erişimi ile otomatik döndürme yoluyla koruyun.

|   #   | Açıklama                                                                                                                                                                                                                                   | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.4.1 | Şifrelerin, AES-256 kullanılarak dinlenme sırasında şifreleme ile HashiCorp Vault, AWS Secrets Manager, Azure Key Vault veya Google Secret Manager içinde saklandığını doğrulayın.                                                         |   1    | D/V |
| 4.4.2 | Kriptografik anahtarların, kurumsal kriptografik politikaya uygun anahtar rotasyonu ile birlikte FIPS 140-2 Seviye 2 HSM'lerde (AWS CloudHSM, Azure Dedicated HSM) oluşturulduğunu doğrulayın.                                             |   1    | D/V |
| 4.4.3 | Personel değişiklikleri veya güvenlik olaylarıyla tetiklenen anında rotasyon ile sıfır kesinti süreli dağıtımda sırların otomatik olarak döndürüldüğünü doğrulayın.                                                                        |   2    | D/V |
| 4.4.4 | Konteyner imajlarının, API anahtarları, parolalar veya sertifikalar içeren derlemeleri engelleyen araçlarla (GitLeaks, TruffleHog veya detect-secrets) tarandığını doğrulayın.                                                             |   2    | D/V |
| 4.4.5 | Üretim gizli erişiminin donanım tokenları (YubiKey, FIDO2) ile MFA gerektirdiğini ve kullanıcı kimlikleri ile zaman damgalarıyla değiştirilemeyen denetim günlükleri tarafından kaydedildiğini doğrulayın.                                 |   2    | D/V |
| 4.4.6 | Gizli bilgilerinin Kubernetes gizli bilgileri aracılığıyla, monte edilmiş hacimlerle veya init konteynerleriyle enjekte edildiğini doğrulayın ve gizli bilgilerin asla ortam değişkenlerinde veya imajlarda gömülü olmadığından emin olun. |   2    | D/V |

---

## C4.5 AI İş Yükü Kum Havuzu ve Doğrulama

Kapsamlı davranış analizi ile güvensiz AI modellerini güvenli kum havuzlarında izole edin.

|   #   | Açıklama                                                                                                                                                                                                   | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.5.1 | Harici AI modellerinin gVisor, mikroVM’ler (örneğin Firecracker, CrossVM) veya --security-opt=no-new-privileges ve --read-only bayrakları ile Docker konteynerlerinde çalıştığını doğrulayın.              |   1    | D/V |
| 4.5.2 | Sandbox ortamlarının ağ bağlantısının olmadığını (--network=none) veya yalnızca localhost erişimine izin verildiğini ve tüm dış taleplerin iptables kurallarıyla engellendiğini doğrulayın.                |   1    | D/V |
| 4.5.3 | AI model doğrulamasının, organizasyon tarafından tanımlanmış test kapsamı ve davranış analizi ile birlikte otomatik kırmızı takım testlerini içerdiğini doğrulayın ve arka kapı tespiti yapın.             |   2    | D/V |
| 4.5.4 | Bir yapay zeka modeli üretime alınmadan önce, sandbox sonuçlarının yetkili güvenlik personeli tarafından kriptografik olarak imzalandığını ve değiştirilemez denetim kayıtlarında saklandığını doğrulayın. |   2    | D/V |
| 4.5.5 | Değerlendirmeler arasında samba kutusu ortamlarının altın görüntülerden tamamen dosya sistemi ve bellek temizliği ile yok edilip yeniden oluşturulduğunu doğrulayın.                                       |   2    | D/V |

---

## C4.6 Altyapı Güvenliği İzleme

Altyapıyı sürekli olarak otomatik iyileştirme ve gerçek zamanlı uyarılar ile tarayın ve izleyin.

|   #   | Açıklama                                                                                                                                                                                             | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.6.1 | Konteyner imajlarının, kurumsal risk eşiklerine göre CRITICAL (KRİTİK) güvenlik açıkları bulunanların dağıtımını engelleyecek şekilde, kurumsal programlara uygun olarak tarandığını doğrulayın.     |   1    | D/V |
| 4.6.2 | Altyapının, kuruluş tarafından tanımlanan uyumluluk eşik değerleri ve başarısız kontroller için otomatik düzeltme ile CIS Kriterleri veya NIST 800-53 kontrollerini geçtiğini doğrulayın.            |   1    | D/V |
| 4.6.3 | Yüksek şiddetteki güvenlik açıklarının, kurumsal risk yönetimi takvimlerine uygun olarak yamalandığını ve aktif olarak sömürülen CVE'ler için acil durum prosedürlerinin uygulandığını doğrulayın.   |   2    | D/V |
| 4.6.4 | Güvenlik uyarılarının CEF veya STIX/TAXII formatlarını kullanarak SIEM platformlarıyla (Splunk, Elastic veya Sentinel) otomatik zenginleştirme ile entegre olduğunu doğrulayın.                      |   2    |  V  |
| 4.6.5 | Altyapı metriklerinin SLA panoları ve üst yönetim raporlaması ile birlikte izleme sistemlerine (Prometheus, DataDog) aktarıldığını doğrulayın.                                                       |   3    |  V  |
| 4.6.6 | Organizasyonel izleme gereksinimlerine göre, yetkisiz değişiklikler için otomatik geri alma ile yapılandırma sapmasının araçlar (Chef InSpec, AWS Config) kullanılarak tespit edildiğini doğrulayın. |   2    | D/V |

---

## C4.7 AI Altyapı Kaynak Yönetimi

Kaynak tükenme saldırılarını önleyin ve kotalar ile izleme yoluyla adil kaynak tahsisini sağlayın.

|   #   | Açıklama                                                                                                                                                                                                                                                         | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.7.1 | GPU/TPU kullanımının, kuruluş tarafından belirlenen eşik değerlerde tetiklenen uyarılarla izlenip izlenmediğini ve kapasite yönetimi politikalarına dayalı olarak otomatik ölçeklendirme veya yük dengelemenin etkinleştirilip etkinleştirilmediğini doğrulayın. |   1    | D/V |
| 4.7.2 | Yapay zeka iş yükü metriklerinin (çıkarım gecikmesi, işlem hacmi, hata oranları) kurumsal izleme gereksinimlerine uygun olarak toplandığını ve altyapı kullanım oranlarıyla ilişkilendirildiğini doğrulayın.                                                     |   1    | D/V |
| 4.7.3 | Kubernetes ResourceQuotas veya eşdeğerinin, organizasyonun kaynak tahsis politikalarına uygun olarak bireysel iş yüklerini sınırlandırdığını ve katı sınırların uygulandığını doğrulayın.                                                                        |   2    | D/V |
| 4.7.4 | Maliyet izleme sisteminin, organizasyonun bütçe eşiklerine dayalı uyarılar ve bütçe aşımı durumları için otomatik kontrollerle birlikte, iş yükü/kiracı başına harcamayı izlediğini doğrulayın.                                                                  |   2    |  V  |
| 4.7.5 | Kapasite planlamasının, örgütsel olarak tanımlanmış tahmin dönemleriyle tarihsel verileri kullandığını ve talep desenlerine dayalı otomatik kaynak sağlama yaptığını doğrulayın.                                                                                 |   3    |  V  |
| 4.7.6 | Kaynak tükenmesinin, kapasite politikalarına dayalı hız sınırlandırma ve iş yükü izolasyonu dahil olmak üzere, organizasyon yanıt gereksinimlerine uygun olarak devre kesicileri tetiklediğini doğrulayın.                                                       |   2    | D/V |

---

## C4.8 Ortam Ayrımı ve Terfi Kontrolleri

Otomatik tanıtım kapıları ve güvenlik doğrulaması ile katı ortam sınırlarını zorunlu kılın.

|   #   | Açıklama                                                                                                                                                                                                                                        | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.8.1 | Dev/test/prod ortamlarının ayrı VPC/VNetlerde çalıştığını ve ortak IAM rolleri, güvenlik grupları veya ağ bağlantısı bulunmadığını doğrulayın.                                                                                                  |   1    | D/V |
| 4.8.2 | Çevre terfisinin, organizasyon tarafından tanımlanmış yetkili kişilerden kriptografik imzalar ve değiştirilemez denetim kayıtları ile onay gerektirdiğini doğrulayın.                                                                           |   1    | D/V |
| 4.8.3 | Üretim ortamlarının SSH erişimini engellediğini, hata ayıklama uç noktalarını devre dışı bıraktığını ve acil durumlar hariç olmak üzere organizasyonun önceden bildirim gereksinimleri ile değişiklik taleplerini zorunlu kıldığını doğrulayın. |   2    | D/V |
| 4.8.4 | Altyapı-kod olarak değişikliklerin, ana dal ile birleştirilmeden önce otomatik test ve güvenlik taraması ile eş incelemesi gerektirdiğini doğrulayın.                                                                                           |   2    | D/V |
| 4.8.5 | Üretim dışı verilerin, kurumsal gizlilik gereksinimlerine uygun olarak anonimleştirildiğini, sentetik veri üretimini veya KİB kaldırma ile tam veri maskelenmesini doğrulayın.                                                                  |   2    | D/V |
| 4.8.6 | Onay için sıfır KRİTİK bulgu gerektiren otomatik güvenlik testlerinin (SAST, DAST, konteyner taraması) terfi kapılarına dahil edildiğini doğrulayın.                                                                                            |   2    | D/V |

---

## C4.9 Altyapı Yedekleme ve Kurtarma

Altyapı dayanıklılığını otomatik yedeklemeler, test edilmiş kurtarma prosedürleri ve felaket kurtarma yetenekleri ile sağlayın.

|   #   | Açıklama                                                                                                                                                                                                | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.9.1 | Altyapı yapılandırmalarının, 3-2-1 yedekleme stratejisi uygulaması ile teşkilatın yedekleme programlarına uygun olarak coğrafi olarak ayrı bölgelere yedeklendiğini doğrulayın.                         |   1    | D/V |
| 4.9.2 | Yedekleme sistemlerinin fidye yazılımı koruması için ayrı kimlik bilgileri ve hava aralıklı depolama ile izole ağlarda çalıştığını doğrulayın.                                                          |   2    | D/V |
| 4.9.3 | Kurtarma prosedürlerinin, organizasyonel programlara göre RTO ve RPO hedeflerinin organizasyon gereksinimlerini karşılayacak şekilde otomatik testler yoluyla test edilip doğrulandığını teyit edin.    |   2    |  V  |
| 4.9.4 | Felaket kurtarma işleminin, model ağırlıklarının geri yüklenmesi, GPU kümesi yeniden inşası ve hizmet bağımlılığı eşlemesi içeren yapay zeka özgü çalışma kitaplarını (runbook) kapsadığını doğrulayın. |   3    |  V  |

---

## C4.10 Altyapı Uyumu ve Yönetişimi

Sürekli değerlendirme, dokümantasyon ve otomatik kontroller aracılığıyla düzenleyici uyumu sürdürün.

|   #    | Açıklama                                                                                                                                                                            | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.10.1 | Altyapı uyumluluğunun, SOC 2, ISO 27001 veya FedRAMP kontrollerine karşı kurumsal takvimlere uygun olarak otomatik kanıt toplama ile değerlendirildiğini doğrulayın.                |   2    | D/V |
| 4.10.2 | Altyapı dokümantasyonunun, organizasyonel değişiklik yönetimi gereksinimlerine göre güncellenmiş ağ diyagramları, veri akış haritaları ve tehdit modellerini içerdiğini doğrulayın. |   2    |  V  |
| 4.10.3 | Altyapı değişikliklerinin, yüksek riskli modifikasyonlar için düzenleyici onay iş akışlarıyla birlikte otomatik uyumluluk etki değerlendirmesine tabi tutulduğunu doğrulayın.       |   3    | D/V |

---

## C4.11 Yapay Zeka Donanım Güvenliği

GPU'lar, TPU'lar ve özel AI hızlandırıcılar dahil olmak üzere AI'ye özgü donanım bileşenlerini güvence altına alın.

|   #    | Açıklama                                                                                                                                                                          | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.11.1 | AI hızlandırıcı firmware'inin (GPU BIOS, TPU firmware) kriptografik imzalarla doğrulandığını ve organizasyonun yama yönetimi zaman çizelgelerine göre güncellendiğini doğrulayın. |   2    | D/V |
| 4.11.2 | İş yükü yürütülmeden önce, AI hızlandırıcı bütünlüğünün TPM 2.0, Intel TXT veya AMD SVM kullanılarak donanım doğrulamasıyla doğrulandığını teyit edin.                            |   2    | D/V |
| 4.11.3 | İşler arasında bellek temizliği ile SR-IOV, MIG (Çoklu Örnek GPU) veya eşdeğer donanım bölümlendirmesi kullanarak GPU belleğinin iş yükleri arasında izole olduğunu doğrulayın.   |   2    | D/V |
| 4.11.4 | Yapay zeka donanımı tedarik zincirinin, üretici sertifikalarıyla köken doğrulaması ve müdahale tespit edilebilir ambalaj doğrulaması içerdiğini doğrulayın.                       |   3    |  V  |
| 4.11.5 | Donanım güvenlik modüllerinin (HSM) AI model ağırlıklarını ve kriptografik anahtarları FIPS 140-2 Seviye 3 veya Common Criteria EAL4+ sertifikası ile koruduğunu doğrulayın.      |   3    | D/V |

---

## C4.12 Kenar ve Dağıtılmış Yapay Zeka Altyapısı

Uç bilişim, federated learning ve çoklu site mimarileri dahil olmak üzere güvenli dağıtılmış AI dağıtımları.

|   #    | Açıklama                                                                                                                                                                                | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.12.1 | Edge AI cihazlarının, kurumsal sertifika yönetim politikası doğrultusunda döndürülen cihaz sertifikaları kullanılarak karşılıklı TLS ile merkezi altyapıya doğrulandığını kontrol edin. |   2    | D/V |
| 4.12.2 | Uç cihazların, doğrulanmış imzalarla güvenli önyükleme gerçekleştirdiğini ve firmware düşürme saldırılarını önleyen geri alma koruması uyguladığını doğrulayın.                         |   2    | D/V |
| 4.12.3 | Dağıtık yapay zeka koordinasyonunun, katılımcı doğrulaması ve kötü niyetli düğüm tespiti ile birlikte Bizans hata toleranslı uzlaşma algoritmaları kullandığını doğrulayın.             |   3    | D/V |
| 4.12.4 | Uçtan buluta iletişimin bant genişliği sınırlandırması, veri sıkıştırma ve güvenli yerel depolama ile çevrimdışı çalışma yeteneklerini içerdiğini doğrulayın.                           |   3    | D/V |

---

## C4.13 Çoklu Bulut ve Hibrit Altyapı Güvenliği

Çoklu bulut sağlayıcıları ve hibrit bulut-yerel dağıtımlarda güvenli AI iş yüklerini koruyun.

|   #    | Açıklama                                                                                                                                                                                       | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.13.1 | Çoklu bulut AI dağıtımlarının, sağlayıcılar arasında merkezi politika yönetimi ile bulut bağımsız kimlik federasyonu (OIDC, SAML) kullandığını doğrulayın.                                     |   2    | D/V |
| 4.13.2 | Çapraz bulut veri transferinin müşteri tarafından yönetilen anahtarlarla uçtan uca şifreleme kullandığını ve veri ikametgahı kontrollerinin her yargı bölgesine göre uygulandığını doğrulayın. |   2    | D/V |
| 4.13.3 | Hibrit bulut yapay zeka iş yüklerinin, birleşik izleme ve uyarı sistemiyle yerinde ve bulut ortamlarında tutarlı güvenlik politikalarını uyguladığını doğrulayın.                              |   2    | D/V |
| 4.13.4 | Bulut sağlayıcı bağımlılığını önlemenin taşınabilir altyapı-kod olarak, standartlaştırılmış API'ler ve format dönüştürme araçları ile veri dışa aktarım yeteneklerini içerdiğini doğrulayın.   |   3    |  V  |
| 4.13.5 | Çoklu bulut maliyet optimizasyonunun, kaynak yayılmasını önleyen güvenlik kontrollerini ve yetkisiz bulutlar arası veri transferi ücretlerini içerdiğini doğrulayın.                           |   3    |  V  |

---

## C4.14 Altyapı Otomasyonu ve GitOps Güvenliği

AI altyapı yönetimi için güvenli altyapı otomasyon boru hatları ve GitOps iş akışları.

|   #    | Açıklama                                                                                                                                                                                                 | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.14.1 | GitOps depolarının, main dallarına doğrudan push yapılmasını engelleyen branş koruma kuralları ve GPG anahtarlarıyla imzalanmış commitler gerektirdiğini doğrulayın.                                     |   2    | D/V |
| 4.14.2 | Altyapı otomasyonunun, yetkisiz değişiklikler için organizasyonel yanıt gereksinimlerine göre tetiklenen otomatik iyileştirme ve geri alma yetenekleri ile birlikte sapma tespiti içerdiğini doğrulayın. |   2    | D/V |
| 4.14.3 | Otomatik altyapı sağlama işleminin, uygun olmayan yapılandırmalar için dağıtımı engelleyen güvenlik politikası doğrulamasını içerdiğini doğrulayın.                                                      |   2    | D/V |
| 4.14.4 | Altyapı otomasyon sırlarının otomatik rotasyon ile dış gizli operatörler (External Secrets Operator, Bank-Vaults) aracılığıyla yönetildiğini doğrulayın.                                                 |   2    | D/V |
| 4.14.5 | Kendi kendini iyileştiren altyapının, otomatik olay müdahalesi ve paydaş bildirim iş akışlarıyla güvenlik olayı korelasyonu içerdiğini doğrulayın.                                                       |   3    |  V  |

---

## C4.15 Kuantum Dirençli Altyapı Güvenliği

Kuantum bilgisayar tehditlerine karşı kuantum sonrası kriptografi ve kuantum güvenli protokoller ile AI altyapısını hazırlayın.

|   #    | Açıklama                                                                                                                                                                                                   | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.15.1 | AI altyapısının anahtar değişimi ve dijital imzalar için NIST onaylı kuantum sonrası kriptografik algoritmaları (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) uyguladığını doğrulayın.                    |   3    | D/V |
| 4.15.2 | Kuantum anahtar dağıtım (QKD) sistemlerinin, kuantum güvenli anahtar yönetim protokolleriyle yüksek güvenlikli yapay zeka iletişimleri için uygulandığını doğrulayın.                                      |   3    | D/V |
| 4.15.3 | Kriptografik çeviklik frameworklerinin, otomatik sertifika ve anahtar döndürme ile yeni kuantum sonrası algoritmalara hızlı geçişi sağladığını doğrulayın.                                                 |   3    | D/V |
| 4.15.4 | Kuantum tehdit modellemesinin, belgelenmiş geçiş zaman çizelgeleri ve risk değerlendirmeleri ile birlikte kuantum saldırılarına karşı yapay zeka altyapısının zayıflıklarını değerlendirdiğini doğrulayın. |   3    |  V  |
| 4.15.5 | Karma klasik-kuantum kriptografik sistemlerin kuantum geçiş dönemi sırasında çok katmanlı savunma sağladığını performans izleme ile doğrulayın.                                                            |   3    | D/V |

---

## C4.16 Gizli Hesaplama ve Güvenli Alanlar

Donanım tabanlı güvenilir yürütme ortamları ve gizli hesaplama teknolojileri kullanarak AI iş yüklerini ve model ağırlıklarını koruyun.

|   #    | Açıklama                                                                                                                                                           | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.16.1 | Hassas AI modellerinin, şifreli bellek ve onay doğrulaması ile Intel SGX muhafazalarında, AMD SEV-SNP veya ARM TrustZone içinde çalıştığını doğrulayın.            |   3    | D/V |
| 4.16.2 | Gizli konteynerlerin (Kata Containers, gizli hesaplama ile gVisor) donanım destekli bellek şifrelemesi ile AI iş yüklerini izole ettiğini doğrulayın.              |   3    | D/V |
| 4.16.3 | AI modelleri yüklemeden önce, uzak doğrulamanın yürütme ortamının özgünlüğüne dair kriptografik kanıtla enclave bütünlüğünü doğruladığını kontrol edin.            |   3    | D/V |
| 4.16.4 | Gizli AI çıkarım hizmetlerinin, mühürlenmiş model ağırlıkları ve korumalı yürütme ile şifreli hesaplama yoluyla model çıkarımını engellediğini doğrulayın.         |   3    | D/V |
| 4.16.5 | Güvenilir yürütme ortamı orkestrasyonunun, uzak doğrulama ve şifreli iletişim kanalları ile güvenli bölge yaşam döngüsünü yönettiğini doğrulayın.                  |   3    | D/V |
| 4.16.6 | Güvenli çok taraflı hesaplamanın (SMPC), bireysel veri setlerini veya model parametrelerini açığa çıkarmadan işbirlikçi yapay zeka eğitimi sağlamasını doğrulayın. |   3    | D/V |

---

## C4.17 Sıfır Bilgi Altyapısı

Hassas bilgileri açığa çıkarmadan gizlilik korumalı AI doğrulama ve kimlik doğrulama için sıfır bilgi kanıtı sistemleri uygulayın.

|   #    | Açıklama                                                                                                                                                                               | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.17.1 | Sıfır bilgi ispatlarının (ZK-SNARKs, ZK-STARKs) model ağırlıklarını veya eğitim verilerini açığa çıkarmadan yapay zeka model bütünlüğünü ve eğitim kaynağını doğruladığını teyit edin. |   3    | D/V |
| 4.17.2 | ZK tabanlı kimlik doğrulama sistemlerinin, kimlikle ilgili bilgileri ifşa etmeden AI hizmetleri için gizliliği koruyan kullanıcı doğrulaması sağladığını doğrulayın.                   |   3    | D/V |
| 4.17.3 | Özel küme kesişimi (PSI) protokollerinin, bireysel veri setlerini açığa çıkarmadan federatif yapay zeka için güvenli veri eşleştirme sağladığını doğrulayın.                           |   3    | D/V |
| 4.17.4 | Sıfır-bilgi makine öğrenimi (ZKML) sistemlerinin, doğru hesaplamanın kriptografik kanıtıyla doğrulanabilir yapay zeka çıkarımlarını mümkün kıldığını doğrulayın.                       |   3    | D/V |
| 4.17.5 | ZK-rollupların toplu doğrulama ve azaltılmış hesaplama yükü ile ölçeklenebilir, gizliliği koruyan AI işlem işleme sağladığını doğrulayın.                                              |   3    | D/V |

---

## C4.18 Yan Kanal Saldırısı Önleme

Zamanlama, güç, elektromanyetik ve önbellek tabanlı yan kanal saldırılarından dolayı hassas bilgilerin sızmasını engellemek için AI altyapısını koruyun.

|   #    | Açıklama                                                                                                                                                                                            | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.18.1 | AI çıkarım zamanlamasının, zaman tabanlı model çıkarma saldırılarını önlemek için sabit zaman algoritmaları ve dolgu kullanılarak normalize edildiğini doğrulayın.                                  |   3    | D/V |
| 4.18.2 | Güç analizi korumasının, yapay zeka donanımı için gürültü enjeksiyonunu, güç hattı filtrelemesini ve rastgeleleştirilmiş yürütme desenlerini içerdiğini doğrulayın.                                 |   3    | D/V |
| 4.18.3 | Önbellek tabanlı yan kanal saldırılarını önleme yöntemlerinin, bilgi sızıntısını engellemek için önbellek bölümlendirmesi, rastgeleleştirme ve temizleme (flush) komutları kullandığını doğrulayın. |   3    | D/V |
| 4.18.4 | Elektromanyetik yayılım korumasının TEMPEST tarzı saldırıları önlemek için koruma, sinyal filtreleme ve rastgele işleme içermesini doğrulayın.                                                      |   3    | D/V |
| 4.18.5 | Mikro mimari yan kanal savunmalarının spekülatif yürütme kontrolleri ve bellek erişim deseni gizleme yöntemlerini içerdiğini doğrulayın.                                                            |   3    | D/V |

---

## C4.19 Nörömorfik ve Özelleşmiş AI Donanım Güvenliği

Nöral mimari çipler, FPGA'lar, özel ASIC'ler ve optik hesaplama sistemleri dahil olmak üzere gelişmekte olan yapay zeka donanım mimarilerini güvence altına alın.

|   #    | Açıklama                                                                                                                                                                                   | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.19.1 | Nöromorfik çip güvenliğinin, spike pattern şifrelemesi, sinaptik ağırlık koruması ve donanım tabanlı öğrenme kuralı doğrulamasını içerdiğini doğrulayın.                                   |   3    | D/V |
| 4.19.2 | FPGA tabanlı yapay zeka hızlandırıcılarının bitstream şifrelemesi, müdahale önleyici mekanizmalar ve doğrulanmış güncellemelerle güvenli yapılandırma yüklemesini uyguladığını doğrulayın. |   3    | D/V |
| 4.19.3 | Özel ASIC güvenliğinin, üzerinde çip güvenlik işlemcileri, donanım tabanlı güven kökü ve müdahale tespitli güvenli anahtar depolamayı içerdiğini doğrulayın.                               |   3    | D/V |
| 4.19.4 | Optik hesaplama sistemlerinin kuantum güvenli optik şifreleme, güvenli fotonik anahtarlama ve korumalı optik sinyal işleme uyguladığını doğrulayın.                                        |   3    | D/V |
| 4.19.5 | Hibrit analog-dijital yapay zeka çiplerinin güvenli analog hesaplama, korumalı ağırlık depolama ve kimlik doğrulamalı analogdan dijitale dönüştürmeyi içerdiğini doğrulayın.               |   3    | D/V |

---

## C4.20 Gizliliği Koruyan Hesaplama Altyapısı

AI işleme ve analiz sırasında hassas verileri korumak için gizliliği koruyan hesaplama altyapı kontrollerini uygulayın.

|   #    | Açıklama                                                                                                                                                                                   | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.20.1 | Homomorfik şifreleme altyapısının, kriptografik bütünlük doğrulaması ve performans izleme ile hassas Yapay Zeka iş yükleri üzerinde şifrelenmiş hesaplamaya olanak sağladığını doğrulayın. |   3    | D/V |
| 4.20.2 | Özel bilgi alma sistemlerinin, erişim desenlerinin kriptografik korumasıyla sorgu desenlerini ifşa etmeden veritabanı sorgularını mümkün kıldığını doğrulayın.                             |   3    | D/V |
| 4.20.3 | Güvenli çok taraflı hesaplama protokollerinin, bireysel girdileri veya ara hesaplamaları açığa çıkarmadan gizliliği koruyan AI çıkarımı sağladığını doğrulayın.                            |   3    | D/V |
| 4.20.4 | Gizliliği koruyan anahtar yönetiminin, donanım destekli koruma ile dağıtık anahtar oluşturma, eşik kriptografi ve güvenli anahtar döndürmeyi içerdiğini doğrulayın.                        |   3    | D/V |
| 4.20.5 | Kriptografik güvenlik garantilerini koruyarak, gizliliği koruyan hesaplama performansının toplu işleme, önbellekleme ve donanım hızlandırma ile optimize edildiğini doğrulayın.            |   3    | D/V |

---

## C4.15 Ajan Çerçevesi Bulut Entegrasyon Güvenliği ve Hibrit Dağıtım

Hibrit yerinde/bulut mimarilerine sahip bulut entegrasyonlu ajan çerçeveleri için güvenlik kontrolleri.

|   #    | Açıklama                                                                                                                         | Seviye | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.15.1 | Bulut depolama entegrasyonunun, ajan tarafından kontrol edilen anahtar yönetimi ile uçtan uca şifreleme kullandığını doğrulayın. |   1    | D/V |
| 4.15.2 | Hibrit dağıtım güvenlik sınırlarının şifreli iletişim kanallarıyla net bir şekilde tanımlandığını doğrulayın.                    |   2    | D/V |
| 4.15.3 | Bulut kaynaklarına erişimin sürekli kimlik doğrulama ile sıfır güven doğrulamasını içerdiğini doğrulayın.                        |   2    | D/V |
| 4.15.4 | Veri yerleşim gereksinimlerinin, depolama konumlarının kriptografik doğrulamasıyla uygulandığını doğrulayın.                     |   3    | D/V |
| 4.15.5 | Bulut sağlayıcı güvenlik değerlendirmelerinin, ajan-spesifik tehdit modellemesi ve risk değerlendirmesini içerdiğini doğrulayın. |   3    | D/V |

---

## Referanslar

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [NIST SP 800-190: Application Container Security Guide](https://csrc.nist.gov/publications/detail/sp/800-190/final)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST SP 800-53: Security Controls for Federal Information Systems](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
* [FIPS 140-2 Security Requirements](https://csrc.nist.gov/publications/detail/fips/140/2/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
* [IEEE 2857: Privacy Engineering for AI Systems](https://standards.ieee.org/ieee/2857/7273/)
* [NIST SP 800-161: Cybersecurity Supply Chain Risk Management](https://csrc.nist.gov/publications/detail/sp/800-161/rev-1/final)
* [NIST Post-Quantum Cryptography Standards](https://csrc.nist.gov/Projects/post-quantum-cryptography)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/tools/software-guard-extensions/overview.html)
* [AMD SEV-SNP White Paper](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf)
* [ARM TrustZone Technology](https://developer.arm.com/ip-products/security-ip/trustzone)
* [ZK-SNARKs: A Gentle Introduction](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)
* [NIST SP 800-57: Cryptographic Key Management](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-5/final)
* [Side-Channel Attack Countermeasures](https://link.springer.com/book/10.1007/978-3-319-75268-6)
* [Neuromorphic Computing Security Challenges](https://ieeexplore.ieee.org/document/9458103)
* [FPGA Security: Fundamentals, Evaluation, and Countermeasures](https://link.springer.com/book/10.1007/978-3-319-90385-9)
* [Microsoft SEAL: Homomorphic Encryption Library](https://github.com/Microsoft/SEAL)
* [HElib: Homomorphic Encryption Library](https://github.com/homenc/HElib)
* [PALISADE Lattice Cryptography Library](https://palisade-crypto.org/)
* [Differential Privacy: A Survey of Results](https://link.springer.com/chapter/10.1007/978-3-540-79228-4_1)
* [Secure Aggregation for Federated Learning](https://eprint.iacr.org/2017/281.pdf)
* [Private Information Retrieval: Concepts and Constructions](https://link.springer.com/book/10.1007/978-3-030-16234-8)

