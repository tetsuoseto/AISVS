# C4 Altyapı, Yapılandırma ve Dağıtım Güvenliği

## Kontrol Amacı

Yapay Zeka altyapısı, yetki yükseltme, tedarik zinciri manipülasyonu ve yatay hareketlere karşı güvenli yapılandırma, çalışma zamanı izolasyonu, güvenilir dağıtım boru hatları ve kapsamlı izleme yoluyla sertleşmelidir. Yalnızca yetkili ve doğrulanmış altyapı bileşenleri ile yapılandırmaları, güvenliği, bütünlüğü ve denetlenebilirliği koruyan kontrollü süreçler yoluyla üretime ulaşır.

Ana Güvenlik Hedefi: Yalnızca kriptografik olarak imzalanmış, güvenlik açığı taraması yapılmış altyapı bileşenleri, güvenlik politikalarını uygulayan ve değiştirilmez denetim izlerini sürdüren otomatik doğrulama süreçleri aracılığıyla üretime ulaşır.

---

## C4.1 Çalışma Zamanı Ortamı İzolasyonu

Konteynerlerden kaçışı ve yetki yükseltmeyi, çekirdek düzeyinde izolasyon mekanizmaları ve zorunlu erişim denetimleri aracılığıyla önleyin.

|   #   | Açıklama                                                                                                                                                                                                                                             | Seviye | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.1.1 | CAP_SETUID, CAP_SETGID dışındaki tüm Linux yeteneklerini kaldırdığından emin olun ve güvenlik tabanlarında belgelenen açıkça gerekli yeteneklerin kullanıma sunulduğunu doğrulayın.                                                                  |   1    | D/V |
| 4.1.2 | Seccomp profillerinin, önceden onaylanmış izin listelerindeki dışındaki tüm sistem çağrılarını engellediğini doğrulayın; ihlaller konteyneri sonlandırır ve güvenlik uyarıları üretir.                                                               |   1    | D/V |
| 4.1.3 | AI iş yüklerinin kök dosya sistemi salt okunur olacak şekilde, geçici veriler için tmpfs kullanılacak ve kalıcı veriler için adlandırılmış hacimler kullanılacak şekilde çalıştığını ve noexec mount seçeneklerinin uygulanmış olduğundan emin olun. |   2    | D/V |
| 4.1.4 | eBPF tabanlı çalışma zamanı izleme (Falco, Tetragon veya eşdeğerleri) yetki yükseltme girişimlerini tespit eder ve tehdit oluşturan süreçleri kurumsal yanıt süresi gereksinimleri kapsamında otomatik olarak sonlandırır.                           |   2    | D/V |
| 4.1.5 | Yüksek-riskli yapay zeka iş yüklerinin attestation doğrulaması ile donanıma izole edilmiş ortamlarda (Intel TXT, AMD SVM veya özel bare-metal düğümleri) çalıştığını doğrulayın.                                                                     |   3    | D/V |

---

## C4.2 Güvenli Derleme ve Dağıtım Boru Hatları

Yeniden üretilebilir derlemeler ve imzalanmış artefaktlar aracılığıyla kriptografik bütünlüğü ve tedarik zinciri güvenliğini sağlayın.

|   #   | Açıklama                                                                                                                                                                                                          | Seviye | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.2.1 | Her commit'te infrastructure-as-code'un tfsec, Checkov veya Terrascan araçlarıyla tarandığından emin olun; CRITICAL veya HIGH seviyesindeki bulgular nedeniyle birleştirmelerin engellenmesini sağlayın.          |   1    | D/V |
| 4.2.2 | Konteyner derlemelerinin, derlemeler arasında aynı SHA256 özetine sahip olacak şekilde tekrarlanabilir olduğunu doğrulayın ve Sigstore ile imzalanmış SLSA Seviye 3 provenance beyanları üretin.                  |   1    | D/V |
| 4.2.3 | Konteyner görüntülerinin CycloneDX veya SPDX SBOM'larını içerdiğini ve Cosign ile imzalandığını registry push öncesinde doğrulayın; imzasız görüntüler dağıtım sırasında reddedilsin.                             |   2    | D/V |
| 4.2.4 | CI/CD boru hatlarının HashiCorp Vault, AWS IAM Rolleri veya Azure Managed Identity'den gelen OIDC belirteçlerini, kurumsal güvenlik politikası sınırlarını aşmayan ömürlerle kullandığını doğrulayın.             |   2    | D/V |
| 4.2.5 | Dağıtım süreci sırasında konteyner çalıştırılmadan önce Cosign imzalarının ve SLSA köken bilgilerinin doğrulandığından emin olun ve doğrulama hatalarının dağıtımın başarısız olmasına neden olduğunu teyit edin. |   2    | D/V |
| 4.2.6 | Build ortamlarının geçici konteynerler veya VM'lerde çalıştığını, kalıcı depolama içermediğini ve üretim VPC'lerinden ağ izolasyonuna sahip olduğunu doğrulayın.                                                  |   2    | D/V |

---

## C4.3 Ağ Güvenliği ve Erişim Kontrolü

Varsayılan reddetme politikaları ve şifreli iletişimlerle sıfır güvenlikli ağı uygulayın.

|   #   | Açıklama                                                                                                                                                                                                                                    | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.3.1 | Kubernetes NetworkPolicies veya eşdeğeri herhangi birinin, gerekli portlar (443, 8080, vb.) için açık izin kurallarıyla birlikte varsayılan-deny giriş/çıkış uyguladığını doğrulayın.                                                       |   1    | D/V |
| 4.3.2 | SSH (port 22), RDP (port 3389) ve bulut meta veri uç noktalarının (169.254.169.254) engellendiğini veya sertifika tabanlı kimlik doğrulaması gerektirip gerekmediğini doğrulayın.                                                           |   1    | D/V |
| 4.3.3 | Çıkış trafiğinin HTTP/HTTPS proxy'leri (Squid, Istio veya bulut NAT geçitleri) üzerinden filtrelendiğini, alan adlarına yönelik izin listeleriyle ve engellenen isteklerin kaydedildiğini doğrulayın.                                       |   2    | D/V |
| 4.3.4 | Servisler arası iletişimin karşılıklı TLS (mTLS) kullandığından, sertifikaların kurumsal politika doğrultusunda yenilendiğinden ve sertifika doğrulamasının zorunlu kılındığından (skip-verify bayraklarının kullanılmadığından) emin olun. |   2    | D/V |
| 4.3.5 | Yapay zeka altyapısının yalnızca özel VPC'ler/VNet'ler üzerinde çalıştığını, doğrudan internet erişiminin olmadığını ve iletişimin yalnızca NAT geçitleri veya bastion sunucuları üzerinden gerçekleştirildiğini doğrulayın.                |   2    | D/V |

---

## C4.4 Gizli Bilgiler ve Kriptografik Anahtar Yönetimi

Donanım destekli depolama ile kimlik bilgilerini koruyun ve sıfır güvenlik erişimiyle otomatik olarak yenileyin.

|   #   | Açıklama                                                                                                                                                                                                                 | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.4.1 | Gizli verilerin saklama sırasında AES-256 ile şifrelenmiş olarak HashiCorp Vault, AWS Secrets Manager, Azure Key Vault veya Google Secret Manager'da depolandığını doğrulayın.                                           |   1    | D/V |
| 4.4.2 | Kriptografik anahtarların FIPS 140-2 Seviye 2 HSM'lerinde (AWS CloudHSM, Azure Dedicated HSM) kurumsal kriptografik politikaya uygun olarak anahtar rotasyonu uygulanmış biçimde üretilmesini doğrulayın.                |   1    | D/V |
| 4.4.3 | Gizli anahtarların rotasyonunun kesintisiz dağıtımla otomatik olarak gerçekleştirildiğinden ve personel değişiklikleri veya güvenlik olayları nedeniyle anında rotasyonun tetiklendiğinden emin olun.                    |   2    | D/V |
| 4.4.4 | Konteyner görüntülerinin API anahtarları, parolalar veya sertifikaları içeren derlemeleri engelleyen araçlarla tarandığından emin olun (GitLeaks, TruffleHog veya detect-secrets).                                       |   2    | D/V |
| 4.4.5 | Üretim ortamında gizli verilere erişimin, donanım jetonları (YubiKey, FIDO2) ile MFA gerektirdiğini ve kullanıcı kimlikleri ile zaman damgalarını içeren değiştirilemez denetim günlükleriyle kaydedildiğini doğrulayın. |   2    | D/V |
| 4.4.6 | Gizli verilerin Kubernetes Secrets, bağlanmış hacimler veya init container'lar aracılığıyla enjekte edildiğini doğrulayın ve gizli verilerin asla ortam değişkenlerinde veya görüntülerde gömülü olmadığından emin olun. |   2    | D/V |

---

## C4.5 Yapay Zeka İş Yükü Sandboxing ve Doğrulama

Güvensiz yapay zeka modellerini güvenli sandbox'larda kapsamlı davranışsal analizlerle izole edin.

|   #   | Açıklama                                                                                                                                                                                                       | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.5.1 | Harici yapay zeka modellerinin gVisor, mikroVM'ler (ör. Firecracker, CrossVM) veya Docker konteynerlerinde --security-opt=no-new-privileges ve --read-only bayraklarıyla çalıştığını doğrulayın.               |   1    | D/V |
| 4.5.2 | Sandbox ortamlarının ya hiç ağ bağlantısına sahip olmadığını (--network=none) ya da yalnızca localhost erişimine sahip olduğunu ve tüm dış isteklerin iptables kurallarıyla engellendiğini doğrulayın.         |   1    | D/V |
| 4.5.3 | Yapay zeka modeli doğrulamasının, kurumsal olarak tanımlanmış test kapsamı ve arka kapı tespiti için davranışsal analiz ile otomatik kırmızı takım testlerini içerdiğini doğrulayın.                           |   2    | D/V |
| 4.5.4 | Bir yapay zeka modeli üretime geçirilmeden önce, sandbox sonuçlarının yetkili güvenlik personeli tarafından kriptografik olarak imzalandığını ve değiştirilemez denetim günlüklerinde saklandığını doğrulayın. |   2    | D/V |
| 4.5.5 | Değerlendirmeler arasındaki süreçte sandbox ortamlarının, tam dosya sistemi ve bellek temizliği ile birlikte altın görüntülerden yok edilip yeniden oluşturulduğunu doğrulayın.                                |   2    | D/V |

---

## C4.6 Altyapı Güvenlik İzleme

Altyapıyı otomatik düzeltme ve gerçek zamanlı uyarılar ile sürekli tarayın ve izleyin.

|   #   | Açıklama                                                                                                                                                                                                      | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.6.1 | Container görüntülerinin kurumsal takvimlere göre tarandığını ve kurumsal risk eşiğine dayanarak dağıtımı engelleyen KRİTİK güvenlik açıklarının bulunduğunu doğrulayın.                                      |   1    | D/V |
| 4.6.2 | Altyapının CIS Benchmarks veya NIST 800-53 kontrollerini karşılamasını, kurumsal olarak tanımlanmış uyum eşik değerleri ve başarısız kontroller için otomatik düzeltme ile doğrulayın.                        |   1    | D/V |
| 4.6.3 | Zafiyetlerin kurumsal risk yönetimi zaman çizelgelerine göre yamalandığından emin olun; aktif olarak istismar edilen CVE'ler için acil durum prosedürlerinin uygulanmasını doğrulayın.                        |   2    | D/V |
| 4.6.4 | Güvenlik uyarılarının SIEM platformlarıyla (Splunk, Elastic veya Sentinel) CEF veya STIX/TAXII formatlarını kullanarak otomatik zenginleştirme ile entegrasyonunu doğrulayın.                                 |   2    |  V  |
| 4.6.5 | Altyapı metriklerinin izleme sistemlerine (Prometheus, DataDog) SLA panoları ve yöneticilere yönelik raporlama ile aktarıldığını doğrulayın.                                                                  |   3    |  V  |
| 4.6.6 | Konfigürasyon sapmasının, organizasyonel izleme gereksinimlerine göre araçlar (Chef InSpec, AWS Config) kullanılarak tespit edildiğini doğrulayın ve yetkisiz değişiklikler için otomatik geri alım sağlayın. |   2    | D/V |

---

## C4.7 Yapay Zeka Altyapı Kaynak Yönetimi

Kaynak tüketim saldırılarını önleyin ve kota ve izleme yoluyla adil kaynak tahsisini sağlayın.

|   #   | Açıklama                                                                                                                                                                                                                   | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.7.1 | GPU/TPU kullanımının izlenmesi, kurumsal olarak belirlenen eşiklerde tetiklenen uyarılarla ve kapasite yönetim politikalarına göre otomatik ölçeklendirme veya yük dengelemenin etkinleştirilmesinin doğrulanması gerekir. |   1    | D/V |
| 4.7.2 | AI iş yükü metriklerinin (çıkarım gecikmesi, işlem hacmi, hata oranları) kurumsal izleme gereksinimlerine göre toplandığını ve altyapı kullanım düzeyiyle korelasyon içinde olduğunu doğrulayın.                           |   1    | D/V |
| 4.7.3 | Kurumsal kaynak tahsis politikalarına göre bireysel iş yüklerini sınırlandıran ve katı sınırların uygulanmasını sağlayan Kubernetes ResourceQuotas'ın veya eşdeğerinin düzgün çalıştığını doğrulayın.                      |   2    | D/V |
| 4.7.4 | Harcamaların iş yükü/kiracı başına izlendiğini, kurumsal bütçe eşiklerine dayalı uyarılar ve bütçe aşımlarını önlemek için otomatik kontrollerin mevcut olduğunu doğrulayın.                                               |   2    |  V  |
| 4.7.5 | Kapasite planlamasının, kurumsal olarak tanımlanmış tahmin dönemleriyle geçmiş verilere dayandığını ve talep desenlerine bağlı olarak otomatik kaynak sağlama yapıldığını doğrulayın.                                      |   3    |  V  |
| 4.7.6 | Kaynak tükenmesinin örgütsel yanıt gereksinimlerine uygun olarak devre kesicileri tetiklediğini doğrulayın; kapasite politikalarına dayalı hız sınırlaması ve iş yükü izolasyonu dahil.                                    |   2    | D/V |

---

## C4.8 Çevre Ayrımı ve Taşıma Kontrolleri

Otomatik geçiş kapıları ve güvenlik doğrulaması ile sıkı ortam sınırlarını uygulayın.

|   #   | Açıklama                                                                                                                                                                                                                                    | Seviye | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.8.1 | Geliştirme, test ve üretim ortamlarının ayrı VPC'lerde ve VNets'te çalıştığını ve IAM rollerinin, güvenlik gruplarının veya ağ bağlantısının paylaşılmadığını doğrulayın.                                                                   |   1    | D/V |
| 4.8.2 | Ortam yükseltmesinin, kurumsal olarak tanımlanmış yetkili kişilerden onay gerektirdiğini kriptografik imzalar ve değiştirilemez denetim izleriyle doğrulayın.                                                                               |   1    | D/V |
| 4.8.3 | Üretim ortamlarının SSH erişimini engellediğini doğrulayın, hata ayıklama uç noktalarını devre dışı bırakın ve acil durumlar hariç kurumsal ileri bildirim gerekliliklerine uygun olarak değişiklik taleplerinin zorunlu olmasını sağlayın. |   2    | D/V |
| 4.8.4 | Altyapıyı kod olarak değiştiren değişikliklerin, ana dala birleştirilmeden önce eşler arası inceleme ile otomatik test ve güvenlik taramasını gerektirdiğini doğrulayın.                                                                    |   2    | D/V |
| 4.8.5 | Üretim dışı verilerin, kurumsal gizlilik gereksinimlerine göre anonimleştirildiğini, ya da sentetik veri üretiminin gerçekleştirildiğini veya PII çıkarımıyla tamamlanmış veri maskelemesinin doğrulandığını teyit edin.                    |   2    | D/V |
| 4.8.6 | Terfi kapılarının otomatik güvenlik testlerini (SAST, DAST, konteyner taraması) içerdiğini ve onay için sıfır kritik bulgu gerekliliğini doğrulayın.                                                                                        |   2    | D/V |

---

## C4.9 Altyapı Yedekleme ve Kurtarma

Altyapının dayanıklılığını otomatik yedeklemeler, test edilmiş kurtarma prosedürleri ve felaket kurtarma yetenekleri ile güvence altına alın.

|   #   | Açıklama                                                                                                                                                                                                                         | Seviye | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.9.1 | Altyapı yapılandırmalarının 3-2-1 yedekleme stratejisinin uygulanmasıyla coğrafi olarak ayrılmış bölgelerde kurumsal yedekleme planlarına göre yedeklendiğini doğrulayın.                                                        |   1    | D/V |
| 4.9.2 | Ransomware koruması için yedekleme sistemlerinin izole ağlarda ayrı kimlik bilgileriyle ve hava yalıtımlı depolama ile çalıştığını doğrulayın.                                                                                   |   2    | D/V |
| 4.9.3 | Kurtarma prosedürlerinin, organizasyonel takvimlere uygun olarak otomatik testlerle test edildiğini ve doğrulandığını teyit edin; bu süreçte RTO ve RPO hedeflerinin organizasyonel gereksinimleri karşıladığından emin olun.    |   2    |  V  |
| 4.9.4 | Yapay zekaya özgü çalıştırma kılavuzlarının, model ağırlıklarının geri yüklenmesini, GPU kümesinin yeniden oluşturulmasını ve hizmet bağımlılıklarının haritalanmasını içerecek şekilde felaket kurtarma süreçlerini doğrulayın. |   3    |  V  |

---

## C4.10 Altyapı Uyum ve Yönetişim

Sürekli değerlendirme, belgelendirme ve otomatik kontroller yoluyla mevzuata uygunluğu sürdürün.

|   #    | Açıklama                                                                                                                                                                        | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.10.1 | Altyapı uyumunun, kurumsal takvimlere göre SOC 2, ISO 27001 veya FedRAMP kontrollerine karşı değerlendirildiğini otomatik kanıt toplama ile doğrulayın.                         |   2    | D/V |
| 4.10.2 | Altyapı dokümantasyonunun ağ diyagramlarının, veri akış haritalarının ve tehdit modellerinin kuruluşun değişim yönetimi gereksinimlerine göre güncellenmiş olduğunu doğrulayın. |   2    |  V  |
| 4.10.3 | Yüksek riskli değişiklikler için düzenleyici onay iş akışlarıyla birlikte altyapı değişikliklerinin otomatik uyum etki değerlendirmesinden geçtiğini doğrulayın.                |   3    | D/V |

---

## C4.11 Yapay Zeka Donanım Güvenliği

GPU'lar, TPU'lar ve özel yapay zeka hızlandırıcıları dahil olmak üzere Yapay Zeka’ya özgü donanım bileşenlerini güvenli hale getirin.

|   #    | Açıklama                                                                                                                                                                                    | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.11.1 | AI hızlandırıcı donanım yazılımının (GPU BIOS, TPU donanım yazılımı) kriptografik imzalarla doğrulandığını ve kurumsal yama yönetimi zaman çizelgelerine göre güncellendiğini doğrulayın.   |   2    | D/V |
| 4.11.2 | Çalışma yükü yürütülmeden önce, yapay zeka hızlandırıcısının bütünlüğünün TPM 2.0, Intel TXT veya AMD SVM kullanılarak donanım tasdiki ile doğrulandığından emin olun.                      |   2    | D/V |
| 4.11.3 | Çalışma yükleri arasında GPU belleğinin SR-IOV, MIG (Multi-Instance GPU) veya eşdeğer donanım bölümleme kullanılarak bellek temizlemesiyle izole edildiğini doğrulayın.                     |   2    | D/V |
| 4.11.4 | Yapay zeka donanım tedarik zincirinin üretici sertifikalarıyla birlikte menşe doğrulaması ve müdahaleye karşı kanıtlayıcı ambalaj doğrulamasını içerdiğini doğrulayın.                      |   3    |  V  |
| 4.11.5 | Donanım güvenlik modüllerinin (HSM'lerin) AI modellerinin ağırlıklarını ve kriptografik anahtarları FIPS 140-2 Seviyesi 3 veya Common Criteria EAL4+ sertifikası ile koruduğunu doğrulayın. |   3    | D/V |

---

## C4.12 Uç Bilişim ve Dağıtık Yapay Zeka Altyapısı

Uç bilişim, federatif öğrenme ve çok konumlu mimarileri de kapsayan güvenli dağıtılmış yapay zeka uygulamaları.

|   #    | Açıklama                                                                                                                                                                                       | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.12.1 | Uç yapay zeka cihazlarının merkezi altyapıya karşılıklı TLS kullanarak kimlik doğruladığını ve cihaz sertifikalarının kurumsal sertifika yönetim politikalarına göre yenilendiğini doğrulayın. |   2    | D/V |
| 4.12.2 | Kenar cihazlarının doğrulanmış imzalarla güvenli önyükleme uyguladığından ve firmware sürüm düşürme saldırılarını önleyen geri dönüş korumasına sahip olduğundan emin olun.                    |   2    | D/V |
| 4.12.3 | Dağıtık yapay zeka koordinasyonunun, katılımcı doğrulaması ve kötü niyetli düğüm tespitiyle Byzantine hata toleranslı uzlaşma algoritmalarını kullandığını doğrulayın.                         |   3    | D/V |
| 4.12.4 | Uçtan buluta iletişiminin bant genişliği kısıtlaması, veri sıkıştırması ve güvenli yerel depolama ile çevrimdışı çalışma yeteneklerini içerdiğini doğrulayın.                                  |   3    | D/V |

---

## C4.13 Çoklu Bulut ve Hibrit Altyapı Güvenliği

Birden çok bulut sağlayıcısı ve hibrit bulut-yerinde dağıtımlarda güvenli Yapay Zeka iş yükleri.

|   #    | Açıklama                                                                                                                                                                                            | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.13.1 | Çoklu bulut AI dağıtımlarının bulut-bağımsız kimlik federasyonunu (OIDC, SAML) ve sağlayıcılar arasında merkezi politika yönetimini kullandığını doğrulayın.                                        |   2    | D/V |
| 4.13.2 | Bulutlararası veri aktarımının uçtan uca şifreleme ile müşteri tarafından yönetilen anahtarlar ve yargı alanına göre uygulanan veri coğrafi konum kontrolleri ile gerçekleştirildiğini doğrulayın.  |   2    | D/V |
| 4.13.3 | Hibrit bulut yapay zeka iş yüklerinin yerinde ve bulut ortamlarında tutarlı güvenlik politikalarını uyguladığını, birleşik izleme ve uyarı ile birlikte doğrulayın.                                 |   2    | D/V |
| 4.13.4 | Bulut sağlayıcısına kilitlenmeyi önlemenin taşınabilir altyapı olarak kod (IaC), standartlaştırılmış API'ler ve biçim dönüştürme araçlarıyla veri dışa aktarma yeteneklerini içerdiğini doğrulayın. |   3    |  V  |
| 4.13.5 | Çoklu bulut maliyet optimizasyonunun, kaynak yayılımını önleyen güvenlik kontrollerini ve ayrıca yetkisiz bulutlar arası veri aktarım ücretlerini de kapsadığını doğrulayın.                        |   3    |  V  |

---

## C4.14 Altyapı Otomasyonu ve GitOps Güvenliği

AI altyapı yönetimi için altyapı otomasyon boru hatlarını ve GitOps iş akışlarını güvenli hale getirin.

|   #    | Açıklama                                                                                                                                                                              | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.14.1 | GitOps depolarının GPG anahtarlarıyla imzalanmış commit'ler gerektirdiğini ve ana dallara doğrudan push yapılmasını engelleyen dal koruma kurallarını doğrulayın.                     |   2    | D/V |
| 4.14.2 | Altyapı otomasyonunun yetkisiz değişiklikler için kurumsal yanıt gereksinimlerine göre tetiklenen otomatik düzeltme ve geri alma yetenekleri ile drift tespiti içerdiğini doğrulayın. |   2    | D/V |
| 4.14.3 | Otomatik altyapı sağlama sürecinin, uyumsuz yapılandırmalar için dağıtımı engelleme özelliğiyle güvenlik politikası doğrulamasını içerdiğini doğrulayın.                              |   2    | D/V |
| 4.14.4 | Altyapı otomasyonu gizli bilgilerinin otomatik rotasyon ile harici gizli bilgi operatörleri (External Secrets Operator, Bank-Vaults) aracılığıyla yönetildiğini doğrulayın.           |   2    | D/V |
| 4.14.5 | Kendini onaran altyapının, güvenlik olaylarının korelasyonu ile otomatik olay müdahalesi ve paydaş bildirim iş akışlarını içerdiğini doğrulayın.                                      |   3    |  V  |

---

## C4.15 Kuantum-Dirençli Altyapı Güvenliği

Kuantum hesaplama tehditlerine karşı yapay zeka altyapısını post-kuantum kriptografi ve kuantum güvenli protokollerle hazırlayın.

|   #    | Açıklama                                                                                                                                                                                                  | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.15.1 | Yapay zeka altyapısının NIST onaylı kuantum sonrası kriptografik algoritmaları (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) anahtar değişimi ve dijital imzalar için uyguladığını doğrulayın.           |   3    | D/V |
| 4.15.2 | Kuantum anahtar dağıtımı (QKD) sistemlerinin, kuantuma dayanıklı anahtar yönetim protokolleriyle yüksek güvenlikli yapay zeka iletişimleri için uygulanıp uygulanmadığını doğrulayın.                     |   3    | D/V |
| 4.15.3 | Kriptografik çeviklik çerçevelerinin otomatik sertifika ve anahtar döndürme ile yeni post-kuantum algoritmalarına hızlı geçişi mümkün kıldığını doğrulayın.                                               |   3    | D/V |
| 4.15.4 | Kuantum tehdit modellemesinin, AI altyapısının kuantum saldırılarına karşı savunmasızlığını belgelendirilmiş geçiş zaman çizelgeleri ve risk değerlendirmeleri ile birlikte değerlendirdiğini doğrulayın. |   3    |  V  |
| 4.15.5 | Kuantum geçiş dönemi boyunca hibrit klasik-kuantum kriptografik sistemlerin çok katmanlı savunma sağladığını performans izleme yoluyla doğrulayın.                                                        |   3    | D/V |

---

## C4.16 Gizli Bilgi İşlem ve Güvenli Enklavlar

Donanım tabanlı güvenilir yürütme ortamları ve gizli hesaplama teknolojileri kullanarak yapay zeka iş yüklerini ve model ağırlıklarını koruyun.

|   #    | Açıklama                                                                                                                                                                | Seviye | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.16.1 | Hassas yapay zeka modellerinin Intel SGX enclave'larında, AMD SEV-SNP'de veya ARM TrustZone'da şifreli bellek ve doğrulama ile çalıştığını doğrulayın.                  |   3    | D/V |
| 4.16.2 | Doğrulayın ki gizli konteynerler (Kata Containers, mahrem hesaplama ile gVisor) yapay zeka iş yüklerini donanım tarafından uygulanan bellek şifrelemesi ile izole eder. |   3    | D/V |
| 4.16.3 | Uzak doğrulamanın, AI modellerini yüklemeden önce yürütme ortamının özgünlüğünü kriptografik kanıtla doğruladığını doğrulayın.                                          |   3    | D/V |
| 4.16.4 | Gizli yapay zeka çıkarım hizmetlerinin, mühürlü model ağırlıkları ve korumalı yürütme ile şifreli hesaplama yoluyla model çıkarımını engellediğini doğrulayın.          |   3    | D/V |
| 4.16.5 | Güvenilir yürütme ortamı orkestrasyonunun uzaktan doğrulama ve şifreli iletişim kanallarıyla güvenli enclave yaşam döngüsünü yönettiğini doğrulayın.                    |   3    | D/V |
| 4.16.6 | Güvenli çok taraflı hesaplama (SMPC) ile bireysel veri kümelerinin veya model parametrelerinin ifşa edilmeden ortak yapay zeka eğitiminin mümkün olduğunu doğrulayın.   |   3    | D/V |

---

## C4.17 Sıfır Bilgi Altyapısı

Mahremiyeti koruyan yapay zeka doğrulama ve kimlik doğrulaması için hassas bilgileri ifşa etmeden sıfır bilgi kanıtı sistemlerini uygulayın.

|   #    | Açıklama                                                                                                                                                                                       | Seviye | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.17.1 | Sıfır bilgi kanıtlarının (ZK-SNARK'lar, ZK-STARK'lar) AI modelinin bütünlüğünü ve eğitim kökenini, model ağırlıklarını veya eğitim verilerini açığa çıkarmadan doğrulayabileceğini doğrulayın. |   3    | D/V |
| 4.17.2 | ZK-tabanlı kimlik doğrulama sistemlerinin yapay zeka hizmetleri için gizliliği koruyan kullanıcı doğrulamasını, kimlik bilgilerini ifşa etmeden mümkün kıldığını doğrulayın.                   |   3    | D/V |
| 4.17.3 | Özel küme kesişimi (PSI) protokollerinin, bireysel veri kümelerini ifşa etmeden federasyonel yapay zeka için güvenli veri eşleşmesini sağladığını doğrulayın.                                  |   3    | D/V |
| 4.17.4 | ZKML sistemlerinin, doğru hesaplamanın kriptografik kanıtıyla doğrulanabilir yapay zeka çıkarımları sağlayabildiğini doğrulayın.                                                               |   3    | D/V |
| 4.17.5 | ZK-rollups'in ölçeklenebilir, gizlilik odaklı yapay zeka işlem süreçlerini toplu doğrulama ve azaltılmış hesaplama yüküyle sağladığını doğrulayın.                                             |   3    | D/V |

---

## C4.18 Yan-Kanal Saldırı Önleme

Yapay Zeka altyapısını, hassas bilgilerin sızdırılmasına yol açabilecek zamanlama, güç, elektromanyetik ve önbellek tabanlı yan kanal saldırılarından koruyun.

|   #    | Açıklama                                                                                                                                                                       | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.18.1 | Yapay zeka çıkarım süresinin, zaman tabanlı model çıkarma saldırılarını önlemek için sabit zamanlı algoritmalar ve doldurma kullanılarak normalize edildiğini doğrulayın.      |   3    | D/V |
| 4.18.2 | Güç analizi korumasının gürültü enjeksiyonu, güç hattı filtrelemesi ve yapay zeka donanımı için rastgele yürütme desenleri içerdiğini doğrulayın.                              |   3    | D/V |
| 4.18.3 | Önbelleğe dayalı yan-kanal güvenlik önleminin, bilgi sızıntısını önlemek amacıyla önbellek bölümlendirme, rastgeleleştirme ve temizleme talimatlarını kullandığını doğrulayın. |   3    | D/V |
| 4.18.4 | Elektromanyetik yayıntıya karşı korumanın, kalkanlama, sinyal filtrelemesi ve rastgele işleme içerdiğini TEMPEST tarzı saldırıları önlemek için doğrulayın.                    |   3    | D/V |
| 4.18.5 | Mikro mimari yan kanal savunmalarının spekülatif yürütme kontrollerini ve bellek erişim desenlerinin gizlenmesini içerdiğini doğrulayın.                                       |   3    | D/V |

---

## C4.19 Nöromorfik ve Özel Yapay Zeka Donanım Güvenliği

Gelişmekte olan yapay zeka donanım mimarilerini güvenli hale getirin; bunlar arasında nöromorfik çipler, FPGA'lar, özel amaçlı ASIC'ler ve optik hesaplama sistemleri bulunmaktadır.

|   #    | Açıklama                                                                                                                                                                                         | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 4.19.1 | Neuromorfik çip güvenliğinin spike desenlerinin şifrelemesini, sinaptik ağırlıkların korunmasını ve donanım tabanlı öğrenme kuralı doğrulamasını içerdiğini doğrulayın.                          |   3    | D/V |
| 4.19.2 | FPGA-tabanlı yapay zeka hızlandırıcılarının bitstream şifrelemesini, anti-tamper mekanizmalarını ve kimlik doğrulamalı güncellemelerle güvenli yapılandırma yüklemesini uyguladığını doğrulayın. |   3    | D/V |
| 4.19.3 | Özel tasarımlı ASIC güvenliğinin çip üzerinde güvenlik işlemcilerini, donanım güven kökünü ve manipülasyon tespiti ile güvenli anahtar depolamasını içerdiğini doğrulayın.                       |   3    | D/V |
| 4.19.4 | Optik hesaplama sistemlerinin kuantum güvenli optik şifreleme, güvenli fotonik anahtarlama ve korumalı optik sinyal işleme uyguladığını doğrulayın.                                              |   3    | D/V |
| 4.19.5 | Hibrit analog-dijital yapay zeka çiplerinin güvenli analog hesaplama, korumalı ağırlık depolama ve kimlik doğrulamalı analog-dijital dönüşüm içerdiğini doğrulayın.                              |   3    | D/V |

---

## C4.20 Gizlilik-Koruyan Hesaplama Altyapısı

Hassas verileri AI işleme ve analizleri sırasında korumak amacıyla gizlilik korumalı hesaplama için altyapı kontrollerini uygulayın.

|   #    | Açıklama                                                                                                                                                                                          | Seviye | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.20.1 | Homomorfik şifreleme altyapısının hassas yapay zeka iş yüklerinde şifreli hesaplama yapılmasına olanak tanıdığını kriptografik bütünlük doğrulaması ve performans izleme ile doğrulayın.          |   3    | D/V |
| 4.20.2 | Özel bilgi edinme (PIR) sistemlerinin, sorgu desenlerini ifşa etmeden veritabanı sorgularını mümkün kıldığını kriptografik erişim deseni korumasıyla doğrulayın.                                  |   3    | D/V |
| 4.20.3 | Güvenli çok taraflı hesaplama protokollerinin, bireysel girdileri veya ara hesaplamaları açığa çıkarmadan mahremiyeti koruyan yapay zeka çıkarımını mümkün kıldığını doğrulayın.                  |   3    | D/V |
| 4.20.4 | Gizliliği koruyan anahtar yönetiminin dağıtık anahtar üretimi, eşik kriptografisi ve donanım destekli koruma ile güvenli anahtar rotasyonunu içerdiğini doğrulayın.                               |   3    | D/V |
| 4.20.5 | Gizliliği koruyan hesaplama performansının, toplu işleme, önbellekleme ve donanım hızlandırmasıyla optimize edildiğini ve bu süreçte kriptografik güvenlik garantilerinin korunduğunu doğrulayın. |   3    | D/V |

---

## C4.15 Ajan Çerçevesi Bulut Entegrasyonu Güvenliği ve Hibrit Dağıtım

Bulutla entegre ajan çerçeveleri için güvenlik kontrolleri, hibrit yerinde ve bulut mimarileriyle.

|   #    | Açıklama                                                                                                                          | Seviye | Rol |
| :----: | --------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 4.15.1 | Bulut depolama entegrasyonunun ajan tarafından kontrol edilen anahtar yönetimiyle uçtan uca şifreleme kullandığını doğrulayın.    |   1    | D/V |
| 4.15.2 | Hibrit dağıtım güvenlik sınırlarının açıkça tanımlandığından ve şifreli iletişim kanallarıyla gerçekleştirildiğinden emin olun.   |   2    | D/V |
| 4.15.3 | Bulut kaynak erişiminin sürekli kimlik doğrulama ile sıfır güven doğrulamasını içerdiğini doğrulayın.                             |   2    | D/V |
| 4.15.4 | Veri ikametgahı gereksinimlerinin, depolama konumlarının kriptografik teyidiyle uygulanıp uygulanmadığını doğrulayın.             |   3    | D/V |
| 4.15.5 | Bulut sağlayıcısının güvenlik değerlendirmelerinin ajan tabanlı tehdit modellemesi ve risk değerlendirmesi içerdiğini doğrulayın. |   3    | D/V |

---

## Kaynaklar

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

