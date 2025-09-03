## Ön sayfa illüstrasyonu

### Standart Hakkında

Yapay Zeka Güvenlik Doğrulama Standardı (AISVS), veri bilimciler, MLOps mühendisleri, yazılım mimarları, geliştiriciler, test uzmanları, güvenlik profesyonelleri, araç tedarikçileri, düzenleyiciler ve tüketicilerin güvenilir AI‑destekli sistemler ve uygulamalar tasarlamak, inşa etmek, test etmek ve doğrulamak için kullanabileceği topluluk odaklı bir güvenlik gereksinimleri kataloğudur. Yapay Zeka yaşam döngüsü boyunca güvenlik kontrollerini tanımlamak için ortak bir dil sağlar—veri toplama ve model geliştirmeden dağıtıma ve sürekli izlemeye kadar—böylece kuruluşlar Yapay Zeka çözümlerinin dayanıklılığını, gizliliğini ve güvenliğini ölçebilir ve iyileştirebilir.

### Telif Hakkı ve Lisans

Sürüm 0.1 (İlk Genel Taslak - Geliştirme Aşamasında), 2025  

![license](images/license.png)
Telif Hakkı © 2025 The AISVS Project.  

Aşağıdaki lisans altında yayımlanmıştır.Creative Commons Attribution‑ShareAlike 4.0 International License.
Her türlü yeniden kullanım veya dağıtım için, bu çalışmanın lisans şartlarını başkalarına açıkça iletmeniz gerekir.

### Proje Liderleri

Jim Manico
Aras “Russ” Memisyazici

### Katkıda Bulunanlar ve Gözden Geçirenler

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS, yapay-zeka sistemlerinin özgün güvenlik zorluklarını ele almak üzere özel olarak oluşturulmuş yepyeni bir standarttır. Geniş güvenlik en iyi uygulamalarından ilham alsa da AISVS'deki her gereksinim, yapay zeka tehdit ortamını yansıtacak şekilde baştan tasarlanmıştır ve kuruluşların daha güvenli, daha dirençli yapay zeka çözümleri geliştirmelerine yardımcı olur.

## Önsöz

Yapay Zeka Güvenlik Doğrulama Standardı (AISVS) sürümü 1.0'a hoş geldiniz!

### Giriş

Topluluk işbirliğiyle 2025 yılında kurulan AISVS, modern yapay zeka modelleri, boru hatları ve AI‑destekli hizmetler tasarlanırken, geliştirilirken, dağıtılırken ve işletilirken göz önünde bulundurulması gereken güvenlik gereksinimlerini tanımlar.

AISVS v1.0, proje liderleri, çalışma grubu ve daha geniş topluluk katkıda bulunanlarının birleşik çalışmalarını temsil eder ve yapay zeka sistemlerini güvence altına almak için pragmatik, test edilebilir bir temel oluşturmaya yöneliktir.

Bu sürümle amacımız AISVS'nin benimsenmesini kolaylaştırmak, belirlenmiş kapsama keskin bir odakla odaklanmayı sürdürmek ve yapay zekaya özgü hızla değişen risk ortamını ele almaktır.

### AISVS Sürüm 1.0 için Ana Hedefler

Sürüm 1.0, birkaç rehber ilke ile oluşturulacaktır.

#### İyi-Tanımlanmış Kapsam

Her bir gereklilik AISVS'in adı ve misyonuyla uyumlu olmalıdır:

Yapay Zeka – Kontroller AI/ML katmanında (veri, model, boru hattı veya çıkarım) çalışır ve AI uygulayıcılarının sorumluluğundadır.
Güvenlik – Belirlenen güvenlik, gizlilik veya emniyet risklerini doğrudan azaltır.
Doğrulama – Uygunluğun nesnel olarak doğrulanabilir olması için dil yazılır.
Standart – Bölümler tutarlı bir yapı ve terminoloji izleyerek bütünleşik bir referans oluşturur.
​
---

AISVS'ye uyarak, kuruluşlar yapay zeka çözümlerinin güvenlik durumunu sistematik olarak değerlendirebilir ve güçlendirebilir; bu, güvenli yapay zeka mühendisliğine yönelik bir kültürün oluşmasını teşvik eder.

## AISVS'yi kullanmak

Yapay Zeka Güvenliği Doğrulama Standardı (AISVS), modern yapay zeka uygulamaları ve hizmetleri için güvenlik gereksinimlerini tanımlar ve uygulama geliştiricilerinin kontrolü altındaki yönlere odaklanır.

AISVS, yapay zeka uygulamalarının güvenliğini geliştiren veya değerlendiren herhangi biri için tasarlanmıştır; buna geliştiriciler, mimarlar, güvenlik mühendisleri ve denetçiler dahildir. Bu bölüm AISVS'nin yapısını ve kullanımını, doğrulama düzeylerini ve amaçlanan kullanım senaryolarını tanıtır.

### Yapay Zeka Güvenlik Doğrulama Seviyeleri

AISVS, güvenlik doğrulaması için üç artan seviye tanımlar. Her seviye derinlik ve karmaşıklık katar; bu da kuruluşların güvenlik yaklaşımını yapay zeka sistemlerinin risk düzeyine göre uyarlamasını sağlar.

Organizasyonlar Seviye 1'den başlayabilir ve güvenlik olgunluğu ile tehdit maruziyeti arttıkça giderek daha yüksek seviyeleri benimseyebilir.

#### Düzeylerin Tanımı

AISVS sürüm 1.0'daki her gereksinim aşağıdaki seviyelerden birine atanır:

 Seviye 1 gereksinimleri

Seviye 1, en kritik ve temel güvenlik gereksinimlerini içerir. Bunlar, diğer ön koşullara veya güvenlik açıklarına bağlı olmayan yaygın saldırıları önlemeye odaklanır. Çoğu Seviye 1 kontrolü ya uygulanması kolaydır ya da bu çabayı haklı çıkaracak kadar önemlidir.

 Seviye 2 gereksinimleri

Seviye 2, daha gelişmiş veya daha az yaygın saldırıları ele alır ve yaygın tehditlere karşı katmanlı savunmalar içerir. Bu gereksinimler daha karmaşık mantık içerebilir veya belirli saldırı önkoşullarını hedefleyebilir.

 Seviye 3 Gereksinimleri

Seviye 3, tipik olarak uygulanması daha zor olan veya uygulanabilirlik bakımından duruma bağlı olan kontrolleri içerir. Bunlar genellikle çok katmanlı savunma mekanizmalarını veya niş, hedefli veya yüksek karmaşıklıkta saldırılara karşı önlemleri temsil eder.

#### Rol (D/V)

Her AISVS gereksinimi birincil hedef kitleye göre işaretlenmiştir:

D – Geliştirici odaklı gereksinimler
V – Doğrulayıcı/denetleyici odaklı gereksinimler
D/V – Hem geliştiriciler hem de doğrulayıcılar için ilgili

## C1 Eğitim Verisi Yönetişimi ve Yanlılık Yönetimi

### Kontrol Amacı

Eğitim verileri, kökeninin korunmasını, güvenliğini, kalitesini ve tarafsızlığını koruyacak şekilde tedarik edilmeli, işlenmeli ve sürdürülmelidir. Bunu yapmak yasal yükümlülükleri yerine getirir ve eğitim sırasında ortaya çıkabilecek önyargı, zehirlenme veya mahremiyet ihlallerinin risklerini azaltır; bu tür riskler tüm Yapay Zeka yaşam döngüsünü etkileyebilir.

---

### C1.1 Eğitim Verisinin Kökeni

Tüm veri kümelerinin doğrulanabilir bir envanterini tutun, yalnızca güvenilir kaynakları kabul edin ve denetim için her değişikliği kaydedin.

 #1.1.1    Seviye: 1    Rol: D/V
 Her eğitim verisi kaynağının (kaynak, sorumlu/sahibi, lisans, toplama yöntemi, kullanım amacıyla ilgili kısıtlamalar ve işleme geçmişi) güncel bir envanterin tutulduğunu doğrulayın.
 #1.1.2    Seviye: 1    Rol: D/V
 Eğitim verilerini işleyen süreçlerin gereksiz özellikleri, nitelikleri veya alanları hariç tuttuğunu doğrulayın (ör. kullanılmayan meta veriler, hassas PII, sızdırılan test verileri).
 #1.1.3    Seviye: 2    Rol: D/V
 Tüm veri kümesi değişikliklerinin kaydedilmiş bir onay iş akışına tabi olduğundan emin olun.
 #1.1.4    Seviye: 3    Rol: D/V
 Mümkün olduğunda, veri kümelerinin veya alt kümelerinin su işaretli veya parmak iziyle izlenebilir olduğundan emin olun.

---

### C1.2 Eğitim Verileri Güvenliği ve Bütünlüğü

Eğitim verilerine erişimi kısıtlayın, verileri dinlenirken ve iletim sırasında şifreleyin ve bozulmayı, hırsızlığı veya veri zehirlenmesini önlemek için bütünlüklerini doğrulayın.

 #1.2.1    Seviye: 1    Rol: D/V
 Erişim kontrollerinin eğitim verisi depolama alanını ve iş akışlarını koruduğunu doğrulayın.
 #1.2.2    Seviye: 2    Rol: D/V
 Tüm eğitim verilerine erişimin kaydedildiğini doğrulayın; kullanıcı, zaman ve eylem dahil.
 #1.2.3    Seviye: 2    Rol: D/V
 Eğitim veri kümelerinin aktarım sırasında ve dinlenme halinde şifreli olduğundan emin olun; endüstri standartlarına uygun kriptografik algoritmalar ve anahtar yönetimi uygulamaları kullanın.
 #1.2.4    Seviye: 2    Rol: D/V
 Eğitim verisinin depolanması ve aktarımı sırasında veri bütünlüğünün sağlandığından emin olmak için kriptografik özetlerin veya dijital imzaların kullanıldığını doğrulayın.
 #1.2.5    Seviye: 2    Rol: D/V
 Eğitim verisinin yetkisiz değişikliklere veya bozulmasına karşı korunması için otomatik tespit tekniklerinin uygulanığından emin olun.
 #1.2.6    Seviye: 2    Rol: D/V
 Kullanım dışı eğitim verilerinin güvenli bir şekilde temizlendiğini veya anonimleştirildiğini doğrulayın.
 #1.2.7    Seviye: 3    Rol: D/V
 Tüm eğitim veri kümesi sürümlerinin benzersiz biçimde tanımlandığını, değiştirilemez biçimde saklandığını ve denetlenebilir olduğunu doğrulayın; bu, geri alma işlemini ve adli analizi destekler.

---

### C1.3 Eğitim Verisi Etiketleme Kalitesi, Bütünlüğü ve Güvenliği

Etiketleri koruyun ve kritik veriler için teknik incelemenin yapılmasını zorunlu kılın.

 #1.3.1    Seviye: 2    Rol: D/V
 Etiketlenen artefaktlara kriptografik özetlerin veya dijital imzaların uygulandığından emin olun; böylece bütünlükleri ve özgünlükleri sağlanır.
 #1.3.2    Seviye: 2    Rol: D/V
 Etiketleme arabirimlerinin ve platformlarının güçlü erişim kontrollerini uyguladığından, tüm etiketleme aktivitelerinin bozulmaz denetim günlüklerini sürdürdüğünden ve yetkisiz değişikliklere karşı korunduğundan emin olun.
 #1.3.3    Seviye: 3    Rol: D/V
 Etiketlerdeki hassas bilgilerin veri alanı düzeyinde dinlenim halinde ve iletim sırasında kırpılmış, anonimleştirilmiş veya şifreli olduğundan emin olun.

---

### C1.4 Eğitim Verisinin Kalitesi ve Güvenliğinin Sağlanması

Veri setinin güvenilirliğini garanti etmek için otomatik doğrulamayı, manuel rastgele kontrolleri ve kaydedilmiş düzeltmeleri birleştirin.

 #1.4.1    Seviye: 1    Rol: D
 Otomatik testlerin her veri içe aktarımında veya önemli veri dönüşümünde biçim hatalarını ve null değerlerini yakaladığını doğrulayın.
 #1.4.2    Seviye: 2    Rol: D/V
 LLM eğitim ve ince ayar iş akışlarının zehirlenme tespiti ve veri bütünlüğü doğrulamasını uyguladığını doğrulayın (ör. istatistiksel yöntemler, aykırı değer tespiti, gömme analizi) ve bunun potansiyel zehirlenme saldırılarını (ör. etiket değiştirme, arka kapı tetikleyici ekleme, rol değiştirme komutları, etkili örnek saldırıları) veya eğitim verilerindeki istemsiz veri bozulmasını belirlemek için kullanıldığını teyit edin.
 #1.4.3    Seviye: 3    Rol: D/V
 Risk değerlendirmesine dayanarak, adversarial eğitim (üretilen adversarial örnekler kullanılarak), bozulmuş girdilerle veri artırımı veya dayanıklı optimizasyon teknikleri gibi uygun savunmaların uygulanıp ayarlandığından emin olun.
 #1.4.4    Seviye: 2    Rol: D/V
 Otomatik olarak oluşturulan etiketlerin (örneğin LLM’ler veya zayıf denetim yoluyla elde edilenlerin) güven eşiklerine ve tutarlılık kontrollerine tabi olduğunu doğrulayın; bu kontroller, hayal ürünü, yanıltıcı veya düşük güvenilirliğe sahip etiketleri tespit etmek için uygulanır.
 #1.4.5    Seviye: 3    Rol: D
 Otomatik testlerin her veri içe aktarımında veya önemli veri dönüşümünde etiket sapmalarını yakalamasını doğrulayın.

---

### C1.5 Veri Kökeni ve İzlenebilirlik

Her veri noktasının kaynaktan model girdisine kadar olan tam sürecini denetlenebilirlik ve olay müdahalesi için izleyin.

 #1.5.1    Seviye: 2    Rol: D/V
 Her bir veri noktasının kökeninin, tüm dönüşümlerin, artırmaların ve birleşmelerin dahil olduğu şekilde kaydedildiğini ve yeniden oluşturulabileceğini doğrulayın.
 #1.5.2    Seviye: 2    Rol: D/V
 Veri soyağacı kayıtlarının değiştirilemez, güvenli bir şekilde saklandığını ve denetimler için erişilebilir olduğunu doğrulayın.
 #1.5.3    Seviye: 2    Rol: D/V
 Doğrulayın ki veri kökeninin izlenmesi, mahremiyeti koruyan veya üretken tekniklerle üretilen sentetik verileri kapsıyor ve tüm sentetik veriler açıkça etiketlenmiş ve gerçek veriden iş akışı boyunca ayırt edilebilir durumda.

---

### Kaynaklar

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
MITRE ATLAS: Adversary Tactics for AI
Survey of ML Bias Mitigation Techniques – MDPI
Data Provenance & Lineage Best Practices – Nightfall AI
Data Labeling Quality Standards – LabelYourData
Training Data Poisoning Guide – Lakera.ai
CISA Advisory: Securing Data for AI Systems
ISO/IEC 23053: AI Management Systems Framework
IBM: What is AI Governance?
Google AI Principles
GDPR & AI Training Data – DataProtectionReport
Supply-Chain Security for AI Data – AppSOC
OpenAI Privacy Center – Data Deletion Controls
Adversarial ML Dataset – Kaggle

## C2 Kullanıcı Girdi Doğrulaması

### Kontrol Amacı

Kullanıcı girdisinin sağlam doğrulanması, yapay zekâ sistemlerine yönelik en zararlı saldırılardan bazılarına karşı birinci savunma hattını oluşturur. İstem enjeksiyonu saldırıları, sistem talimatlarını geçersiz kılabilir, hassas verileri sızdırabilir veya modelin izin verilmeyen davranışlara yönlendirilmesine yol açabilir. Özel filtreler ve talimat hiyerarşileri mevcut olmadığında, çok uzun bağlam pencerelerinden yararlanarak yapılan "multi-shot" jailbreak'lerin etkili olacağını gösteren araştırmalar bulunmaktadır. Ayrıca, homoglif değişimleri veya leetspeak gibi ince adversarial perturbasyon saldırıları—-bir modelin kararlarını sessizce değiştirebilir.

---

### C2.1 Prompt Enjeksiyonu Savunması

İstem enjeksiyonu, yapay zeka sistemleri için en büyük risklerden biridir. Bu taktiğe karşı savunmalar, statik desen filtrelerinin, dinamik sınıflandırıcıların ve talimat hiyerarşisinin uygulanmasının bir kombinasyonunu kullanır.

 #2.1.1    Seviye: 1    Rol: D/V
 Kullanıcı girdilerinin, sürekli güncellenen bilinen istem enjeksiyonu desenleri kütüphanesine karşı tarandığından emin olun (jailbreak anahtar kelimeleri, "ignore previous", rol oynama zincirleri, dolaylı HTML/URL saldırıları).
 #2.1.2    Seviye: 1    Rol: D/V
 Sistemin, bağlam penceresi genişletildikten sonra bile sistem veya geliştirici mesajlarının kullanıcı talimatlarını geçersiz kıldığı bir talimat hiyerarşisini zorunlu kıldığını doğrulayın.
 #2.1.3    Seviye: 2    Rol: D/V
 Her model veya istem-şablonu sürümünden önce adversarial değerlendirme testlerinin (örneğin Red Team 'many-shot' istemleri) yürütüldüğünü doğrulayın; bu süreç için başarı oranı eşiği ve regresyonlar için otomatik engelleyicilerin bulunması gerekir.
 #2.1.4    Seviye: 2    Rol: D
 Üçüncü taraf içeriğinden gelen istemlerin (web sayfaları, PDF'ler, e-postalar) ana isteme eklenmeden önce izole bir ayrıştırma bağlamında arındırıldığını doğrulayın.
 #2.1.5    Seviye: 3    Rol: D/V
 Tüm prompt-filter kural güncellemelerinin, sınıflandırıcı model sürümlerinin ve block-list değişikliklerinin sürüm kontrolünde ve denetlenebilir olmasını doğrulayın.

---

### C2.2 Saldırıya Karşı Örnek Direnci

Doğal Dil İşleme (NLP) modelleri, insanlar çoğu zaman fark etmediği fakat modellerin yanlış sınıflandırmaya eğilim gösterdiği ince karakter veya kelime düzeyindeki perturbasyonlara karşı hâlâ savunmasızdır.

 #2.2.1    Seviye: 1    Rol: D
 Temel giriş normalizasyonu adımlarının (Unicode NFC, homoglif eşleme, boşlukların kırpılması) tokenleştirmeden önce çalıştığından emin olun.
 #2.2.2    Seviye: 2    Rol: D/V
 İstatistiksel anomali tespitinin, dil normlarına göre olağanüstü yüksek düzenleme mesafesi, aşırı tekrarlanan tokenler veya anormal gömme uzaklıkları olan girdileri işaretlediğini doğrulayın.
 #2.2.3    Seviye: 2    Rol: D
 Çıkarım hattının, yüksek riskli uç noktalar içinisteğe bağlı adversarial-training–hardened model varyantlarını veya savunma katmanlarını desteklediğini doğrulayın (örneğin, rastgeleleştirme, savunma distilasyonu).
 #2.2.4    Seviye: 2    Rol: V
 Şüpheli adversarial girdilerin karantinaya alındığını, tam payload'larla kaydedildiğini (PII redaksiyonu sonrası) doğrulayın.
 #2.2.5    Seviye: 3    Rol: D/V
 Dayanıklılık metriklerinin (bilinen saldırı kümelerinin başarı oranı) zaman içinde izlenmesini ve regresyonların bir sürüm engelleyici tetiklemesini doğrulayın.

---

### C2.3 Şema, Tip ve Uzunluk Doğrulaması

Yapay Zeka saldırıları, biçimlendirilmemiş veya çok büyük girdiler içerdiğinde ayrıştırma hatalarına, alanlar arasında istemin taşmasına ve kaynak tükenmesine yol açabilir.  Deterministik araç çağrılarını gerçekleştirirken sıkı şema denetimi de bir önkoşuldur.

 #2.3.1    Seviye: 1    Rol: D
 Her API veya fonksiyon çağrısı uç noktasının açık bir girdi şeması (JSON Şeması, Protobuf veya çok modlu eşdeğeri) tanımladığını ve girdilerin prompt derlemesinden önce doğrulandığını doğrulayın.
 #2.3.2    Seviye: 1    Rol: D/V
 Maksimum belirteç veya bayt sınırlarını aşan girdilerin güvenli bir hata ile reddedildiğini ve asla sessizce kesilmediğini doğrulayın.
 #2.3.3    Seviye: 2    Rol: D/V
 Tip kontrollerinin (örneğin sayısal aralıklar, enum değerleri, resimler ve sesler için MIME türleri) yalnızca istemci tarafında değil, sunucu tarafında da uygulanmasını doğrulayın.
 #2.3.4    Seviye: 2    Rol: D
 Semantik doğrulayıcıların (örneğin JSON Şeması) sabit zamanda çalıştığını doğrulayın; böylece algoritmik DoS saldırısı önlenir.
 #2.3.5    Seviye: 3    Rol: V
 Doğrulama hatalarının sansürlenmiş yük parçacıkları ve açık hata kodlarıyla kaydedildiğini doğrulayın; bu, güvenlik triage'ını kolaylaştırır.

---

### C2.4 İçerik ve Politika Tarama

Geliştiricilerin, yasak içerik talep eden sözdizimsel olarak geçerli istemleri tespit edebilmesi ve bunların yayılmasını engelleyebilmesi gerekir.

 #2.4.1    Seviye: 1    Rol: D
 Bir içerik sınıflandırıcısının (sıfır atışlı veya ince ayarlı) her girdiyi şiddet, kendi kendine zarar verme, nefret, cinsel içerik ve yasa dışı istekler açısından skorladığını doğrulayın; bu skorlar ayarlanabilir eşiklerle olsun.
 #2.4.2    Seviye: 1    Rol: D/V
 Politikalara aykırı girdilerin standart reddedilmelerle veya güvenli tamamlamalarla ele alınacağını doğrulayın; böylece bunlar sonraki LLM çağrılarına yayılmaz.
 #2.4.3    Seviye: 2    Rol: D
 Tarama modeli veya kural setinin en az üç ayda bir yeniden eğitildiğini/güncellendiğini doğrulayın; yeni gözlemlenen jailbreak veya politika atlatma kalıplarını içerecek şekilde güncellemeleri de dahil edin.
 #2.4.4    Seviye: 2    Rol: D
 Taramanın kullanıcıya özgü politikalara (yaş, bölgesel yasal kısıtlamalar) uyduğunu istek anında belirlenen nitelik tabanlı kurallar aracılığıyla doğrulayın.
 #2.4.5    Seviye: 3    Rol: V
 Tarama günlüklerinin SOC korelasyonu ve gelecekteki red-team tekrarı için sınıflandırıcı güven skorlarını ve politika kategori etiketlerini içerdiğini doğrulayın.

---

### C2.5 Girdi Hızı Sınırlandırması ve Kötüye Kullanımın Önlenmesi

Geliştiriciler, yapay zekâ sistemlerine karşı kötüye kullanımı, kaynak tükenmesini ve otomatik saldırıları önlemek için girdi hızlarını sınırlamalı ve anormal kullanım desenlerini tespit etmelidir.

 #2.5.1    Seviye: 1    Rol: D/V
 Kullanıcı başına, IP adresine göre ve API anahtarına göre hız sınırlarının tüm giriş uç noktaları için uygulanıp uygulanmadığını doğrulayın.
 #2.5.2    Seviye: 2    Rol: D/V
 DoS ve brute force saldırılarını önlemek için ani ve sürekli hız sınırlarının ayarlandığından emin olun.
 #2.5.3    Seviye: 2    Rol: D/V
 Anormal kullanım kalıplarının (örneğin, peş peşe gelen istekler, giriş bombardımanı) otomatik blokları veya yükseltmeleri tetiklediğini doğrulayın.
 #2.5.4    Seviye: 3    Rol: V
 Kötüye kullanım önleme günlüklerinin saklandığından ve ortaya çıkan saldırı kalıpları için incelendiğinden emin olun.

---

### C2.6 Çok Modlu Girdi Doğrulaması

Yapay zeka sistemleri, enjeksiyonu, kaçınmayı veya kaynak suistimalini önlemek amacıyla metin dışı girdiler (görüntüler, sesler ve dosyalar) için sağlam doğrulama içermelidir.

 #2.6.1    Seviye: 1    Rol: D
 İşlemden önce tüm metin dışı girdilerin (görüntüler, sesler, dosyalar) tür, boyut ve biçim açısından doğrulanmasını sağlayın.
 #2.6.2    Seviye: 2    Rol: D/V
 Dosyaların içe aktarılmadan önce zararlı yazılımlar ve steganografik yükler için tarandığından emin olun.
 #2.6.3    Seviye: 2    Rol: D/V
 Görüntü ve ses girdilerinin adversarial perturbasyonlar veya bilinen saldırı kalıpları için kontrol edildiğini doğrulayın.
 #2.6.4    Seviye: 3    Rol: V
 Çok modlu giriş doğrulama hatalarının kaydedildiğini ve inceleme için uyarıların tetiklendiğini doğrulayın.

---

### C2.7 Girdi Kökeni ve Atıf

Yapay zeka sistemleri, tüm kullanıcı girdilerinin kökenlerini izleyip etiketleyerek denetim, kötüye kullanım takibi ve uyumluluğu desteklemelidir.

 #2.7.1    Seviye: 1    Rol: D/V
 Tüm kullanıcı girdilerinin içe aktarım sırasında meta verileriyle (kullanıcı kimliği, oturum, kaynak, zaman damgası, IP adresi) etiketlendiğini doğrulayın.
 #2.7.2    Seviye: 2    Rol: D/V
 Tüm işlenen girdiler için köken meta verilerinin korunup denetlenebilir olduğundan emin olun.
 #2.7.3    Seviye: 2    Rol: D/V
 Anormal veya güvenilmez giriş kaynaklarının işaretlendiğini ve artırılmış inceleme veya engellemeye tabi tutulduğunu doğrulayın.

---

### C2.8 Gerçek Zamanlı Adaptif Tehdit Tespiti

Geliştiriciler, AI için yeni saldırı kalıplarına uyum sağlayan ve derlenmiş desen eşleşmesiyle gerçek zamanlı koruma sağlayan gelişmiş tehdit tespit sistemlerini kullanmalıdır.

 #2.8.1    Seviye: 1    Rol: D/V
 Tehdit tespit desenlerinin yüksek performanslı gerçek zamanlı filtreleme için minimum gecikme etkisiyle optimize edilmiş regex motorlarına derlendiğini doğrulayın.
 #2.8.2    Seviye: 1    Rol: D/V
 Tehdit algılama sistemlerinin farklı tehdit kategorileri için ayrı desen kütüphanelerine sahip olduğunu doğrulayın (istem enjeksiyonu, zararlı içerik, hassas veriler, sistem komutları).
 #2.8.3    Seviye: 2    Rol: D/V
 Uyarlanabilir tehdit tespitinin, saldırı sıklığı ve başarı oranlarına dayanarak tehdit hassasiyetini güncelleyen makine öğrenimi modellerini entegre ettiğini doğrulayın.
 #2.8.4    Seviye: 2    Rol: D/V
 Gerçek zamanlı tehdit istihbaratı akışlarının, yeni saldırı imzaları ve İhlal Göstergeleri ile birlikte desen kütüphanelerini otomatik olarak güncellediğini doğrulayın.
 #2.8.5    Seviye: 3    Rol: D/V
 Tehdit tespitinin yanlış pozitif oranlarının sürekli izlendiğini ve desen özgüllüğünün meşru kullanım durumlarına müdahale edilmesini en aza indirecek şekilde otomatik olarak ayarlandığını doğrulayın.
 #2.8.6    Seviye: 3    Rol: D/V
 Bağlamsal tehdit analizinin girdi kaynağını, kullanıcı davranış kalıplarını ve oturum geçmişini dikkate alarak tespit doğruluğunu artırdığını doğrulayın.
 #2.8.7    Seviye: 3    Rol: D/V
 Tehdit tespiti performans göstergelerinin (tespit oranı, işleme gecikmesi, kaynak kullanımı) gerçek zamanlı olarak izlendiğini ve optimize edildiğini doğrulayın.

---

### C2.9 Çok-Modlu Güvenlik Doğrulama İş Akışı

Geliştiriciler, metin, görüntü, ses ve diğer AI giriş biçimleri için belirli tehdit tespiti türleri ve kaynak izolasyonu ile güvenlik doğrulaması sağlamalıdır.

 #2.9.1    Seviye: 1    Rol: D/V
 Her bir girdi modu için belgelenmiş tehdit desenlerine sahip özel güvenlik doğrulayıcıları ve tespit eşiklerine sahip olduğundan emin olun (metin: prompt enjeksiyonu, görüntüler: steganografi, ses: spektrogram saldırıları).
 #2.9.2    Seviye: 2    Rol: D/V
 Çok modlu girdilerin her mod tipi için belirlenen kaynak sınırlamalarıyla (bellek, CPU, işleme süresi) izole sandbox'larda işlendiğini ve güvenlik politikalarında belgelendiğini doğrulayın.
 #2.9.3    Seviye: 2    Rol: D/V
 Çapraz-mod saldırı tespitinin, birden çok giriş türünü kapsayan koordine edilmiş saldırıları (örneğin resimlerdeki steganografik yükler ile metindeki prompt enjeksiyonu) korelasyon kuralları ve uyarı üretimi ile tanımladığını doğrulayın.
 #2.9.4    Seviye: 3    Rol: D/V
 Çok modlu doğrulama hatalarının, SIEM entegrasyonu için yapılandırılmış günlük formatlarıyla tüm girdi modlarını, doğrulama sonuçlarını, tehdit skorlarını ve korelasyon analizini içeren ayrıntılı günlük kaydını tetiklediğini doğrulayın.
 #2.9.5    Seviye: 3    Rol: D/V
 Belgelere dayalı takvime göre (asgari olarak her çeyrekte bir) modalliklere özgü içerik sınıflandırıcılarının güncellendiğini ve bu süreçte yeni tehdit kalıpları, adversarial örnekler ile baz eşiklerinin üzerinde tutulan performans göstergelerinin korunduğunu doğrulayın.

---

### Kaynaklar

LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security
Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
$PDF$ OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
Easily enforcing valid JSON schema following – API
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## C3 Model Yaşam Döngüsü Yönetimi ve Değişiklik Kontrolü

### Kontrol Amacı

Yapay Zeka sistemleri, yetkisiz veya güvensiz model değişikliklerinin üretim ortamına ulaşmasını önleyen değişiklik kontrol süreçlerini hayata geçirmelidir. Bu kontrol, tüm yaşam döngüsü boyunca model bütünlüğünü sağlar--geliştirmeden dağıtıma ve kullanımdan kaldırmaya kadar--ve bu, hızlı olay müdahalesini mümkün kılar ve tüm değişiklikler için hesap verebilirliği sürdürür.

Temel Güvenlik Hedefi: Yalnızca yetkilendirilmiş, doğrulanmış modeller üretim ortamına ulaşır; bütünlük, izlenebilirlik ve kurtarılabilirliği sağlayan kontrollü süreçler uygulayarak.

---

### C3.1 Model Yetkilendirme ve Bütünlük

Sadece yetkilendirilmiş ve bütünlüğü doğrulanmış modeller üretim ortamlarına ulaşırlar.

 #3.1.1    Seviye: 1    Rol: D/V
 Devreye alınmadan önce tüm model varlıklarının (ağırlıklar, yapılandırmalar, tokenizer'lar) kriptografik olarak yetkili varlıklar tarafından imzalandığını doğrulayın.
 #3.1.2    Seviye: 1    Rol: D/V
 Dağıtım sırasında model bütünlüğünün doğrulandığını ve imza doğrulama hatalarının modelin yüklenmesini engellediğini doğrulayın.
 #3.1.3    Seviye: 2    Rol: D/V
 Model kökeni kayıtlarının şu öğeleri içerdiğini doğrulayın: yetkili kuruluşun kimliği, eğitim verisinin hash değerleri, doğrulama test sonuçları geçerli/başarısız durumuna ilişkin ve oluşturulma zaman damgası.
 #3.1.4    Seviye: 2    Rol: D/V
 Tüm model artefaktlarının semantik sürümlemeyi (MAJOR.MINOR.PATCH) kullandığından emin olun; her sürüm bileşeninin ne zaman artacağını belirten belgelenmiş kriterlerle.
 #3.1.5    Seviye: 2    Rol: V
 Bağımlılık izlemesinin, tüm tüketen sistemlerin hızlı bir şekilde tanımlanmasını sağlayan gerçek zamanlı bir envanter tuttuğunu doğrulayın.

---

### C3.2 Model Doğrulama ve Testler

Modeller, dağıtımdan önce tanımlanmış güvenlik doğrulamalarından geçmelidir.

 #3.2.1    Seviye: 1    Rol: D/V
 Modellerin dağıtımdan önce giriş doğrulama, çıktı temizleme ve güvenlik değerlendirmelerini içeren otomatik güvenlik testlerinden geçtiğini ve bu testlerin önceden üzerinde anlaşılan geçiş/başarısızlık eşiklerine göre değerlendirildiğini doğrulayın.
 #3.2.2    Seviye: 1    Rol: D/V
 Doğrulama hatalarının, önceden belirlenmiş yetkili kişilerden gelen açık istisna onayından sonra belgelendirilmiş iş gerekçeleriyle otomatik olarak model dağıtımını engellediğini doğrulayın.
 #3.2.3    Seviye: 2    Rol: V
 Test sonuçlarının kriptografik olarak imzalandığını ve doğrulanan belirli model sürümü hash’ine değiştirilemez biçimde bağlandığını doğrulayın.
 #3.2.4    Seviye: 2    Rol: D/V
 Acil dağıtımların belgelenmiş güvenlik risk değerlendirmesi ve önceden belirlenmiş bir güvenlik otoritesinden onay gerektirdiğini, önceden kararlaştırılmış zaman çerçeveleri içinde olduğunun doğrulanmasını sağlayın.

---

### C3.3 Kontrollü Dağıtım ve Geri Alma

Model dağıtımları kontrollü, izlenebilir ve geri alınabilir olmalıdır.

 #3.3.1    Seviye: 1    Rol: D
 Üretim dağıtımlarının kademeli dağıtım mekanizmalarını (kanarya dağıtımları, mavi-yeşil dağıtımları) otomatik geri alma tetikleyicileri ile birlikte uygulandığını doğrulayın, önceden kararlaştırılmış hata oranlarına, gecikme eşiklerine veya güvenlik uyarı kriterlerine dayanarak.
 #3.3.2    Seviye: 1    Rol: D/V
 Geri alma yeteneklerinin, ağırlıklar, yapılandırmalar ve bağımlılıklar dahil olmak üzere tam model durumunu atomik olarak önceden tanımlanmış kurumsal zaman dilimleri içinde geri yüklediğini doğrulayın.
 #3.3.3    Seviye: 2    Rol: D/V
 Dağıtım süreçlerinin kriptografik imzaları doğruladığını ve model etkinleştirilmeden önce bütünlük denetim toplamlarını hesapladığını doğrulayın; herhangi bir uyumsuzluk durumunda dağıtımı başarısız kılın.
 #3.3.4    Seviye: 2    Rol: D/V
 Acil durum model kapatma yeteneklerinin, otomatik devre kesiciler veya manuel kapatma anahtarları aracılığıyla önceden belirlenmiş yanıt süreleri içinde model uç noktalarını devre dışı bırakabildiğini doğrulayın.
 #3.3.5    Seviye: 2    Rol: V
 Geri alma artefaktlarının (önceki model sürümleri, yapılandırmalar, bağımlılıklar) kurum politikalarına uygun olarak saklandığını, olay müdahalesi için değiştirilemez depolama ile doğrulayın.

---

### C3.4 Değişiklik Sorumluluğu ve Denetimi

Tüm model yaşam döngüsü değişiklikleri izlenebilir ve denetlenebilir olmalıdır.

 #3.4.1    Seviye: 1    Rol: V
 Tüm model değişikliklerinin (dağıtım, yapılandırma, kullanımdan kaldırma) değiştirilmez denetim kayıtları ürettiğini doğrulayın; bu kayıtlar bir zaman damgası, doğrulanmış aktör kimliği, değişiklik türü ve önceki ile sonraki durumları içermelidir.
 #3.4.2    Seviye: 2    Rol: D/V
 Denetim günlüğü erişiminin uygun yetkilendirme gerektirdiğini ve tüm erişim girişimlerinin kullanıcı kimliği ile bir zaman damgası kaydedildiğini doğrulayın.
 #3.4.3    Seviye: 2    Rol: D/V
 Dağıtımdan önce, prompt şablonları ve sistem mesajlarının Git depolarında sürüm kontrolü altında olduğundan ve zorunlu kod incelemesi ile belirlenen inceleyenlerden onay alındığından emin olun.
 #3.4.4    Seviye: 2    Rol: V
 Denetim kayıtlarının saklama süresi içindeki herhangi bir zaman damgası için model durumunun eksiksiz yeniden oluşturulmasını sağlayacak kadar ayrıntıya sahip olduğunu doğrulayın (model hash değerleri, yapılandırma anlık görüntüleri, bağımlılık sürümleri).

---

### C3.5 Güvenli Yazılım Geliştirme Uygulamaları

Model geliştirme ve eğitim süreçleri, güvenli uygulamaları izleyerek güvenliğini bozulmadan korumalıdır.

 #3.5.1    Seviye: 1    Rol: D
 Model geliştirme, test ve üretim ortamlarının fiziksel olarak veya mantıksal olarak ayrı olduğundan emin olun. Bu ortamlar paylaşılan altyapıya sahip değildir; farklı erişim kontrollerine ve izole veri depolarına sahiptirler.
 #3.5.2    Seviye: 1    Rol: D
 Model eğitiminin ve ince ayarın izole ortamlarda kontrollü ağ erişimiyle gerçekleştiğini doğrulayın.
 #3.5.3    Seviye: 1    Rol: D/V
 Model geliştirme öncesinde, eğitim veri kaynaklarının bütünlük kontrolleriyle doğrulanmış ve güvenilir kaynaklar aracılığıyla kimlik doğrulaması yapılmış olduğundan ve belgelenmiş sahiplik zinciriyle desteklendiğinden emin olun.
 #3.5.4    Seviye: 2    Rol: D
 Model geliştirme artefaktlarının (hiperparametreler, eğitim betikleri, yapılandırma dosyaları) sürüm kontrolünde saklandığını ve eğitimde kullanılmadan önce eşler arası inceleme onayı gerektirdiğini doğrulayın.

---

### C3.6 Model Emekliliği ve Devre Dışı Bırakma

Modeller artık ihtiyaç duyulmadığında veya güvenlik sorunları tespit edildiğinde güvenli bir şekilde kullanımdan kaldırılmalıdır.

 #3.6.1    Seviye: 1    Rol: D
 Modelin kullanım dışı bırakılmasına yönelik süreçlerin bağımlılık grafiğini otomatik olarak taradığını, tüm tüketen sistemleri belirlediğini ve devre dışı bırakmadan önce üzerinde uzlaşılmış ön bildirim sürelerini sağladığını doğrulayın.
 #3.6.2    Seviye: 1    Rol: D/V
 Kullanımdan kaldırılan model artefaktlarının belgelendirilmiş veri saklama politikalarına göre kriptografik silme veya çok geçişli üzerine yazma ile güvenli bir şekilde silindiğini ve doğrulanmış imha sertifikaları ile belgelendiğini doğrulayın.
 #3.6.3    Seviye: 2    Rol: V
 Model emeklilik olaylarının zaman damgası ve aktör kimliği ile kaydedildiğini ve model imzalarının yeniden kullanımını engellemek için iptal edildiğini doğrulayın.
 #3.6.4    Seviye: 2    Rol: D/V
 Acil durum modelinin emekli edilmesiyle, kritik güvenlik açıkları tespit edildiğinde otomatik kilitleme anahtarları aracılığıyla önceden belirlenmiş acil yanıt süreleri içinde modele erişiminin devre dışı bırakılabildiğini doğrulayın.

---

### Kaynaklar

MLOps Principles
Securing AI/ML Ops – Cisco.com
Audit logs security: cryptographically signed tamper-proof logs
Machine Learning Model Versioning: Top Tools & Best Practices
AI Hygiene Starts with Models and Data Loaders – SEI Blog
How to handle versioning and rollback of a deployed ML model?
Reinforcement fine-tuning – OpenAI API
Auditing Machine Learning models: Governance, Data Security and …
Adversarial Training to Improve Model Robustness
What is AI adversarial robustness? – IBM Research
Exploring Data Provenance: Ensuring Data Integrity and Authenticity
MITRE ATLAS
AWS Prescriptive Guidance – Best practices for retiring applications …

## C4 Altyapı, Yapılandırma ve Dağıtım Güvenliği

### Kontrol Amacı

Yapay Zeka altyapısı, yetki yükseltme, tedarik zinciri manipülasyonu ve yatay hareketlere karşı güvenli yapılandırma, çalışma zamanı izolasyonu, güvenilir dağıtım boru hatları ve kapsamlı izleme yoluyla sertleşmelidir. Yalnızca yetkili ve doğrulanmış altyapı bileşenleri ile yapılandırmaları, güvenliği, bütünlüğü ve denetlenebilirliği koruyan kontrollü süreçler yoluyla üretime ulaşır.

Ana Güvenlik Hedefi: Yalnızca kriptografik olarak imzalanmış, güvenlik açığı taraması yapılmış altyapı bileşenleri, güvenlik politikalarını uygulayan ve değiştirilmez denetim izlerini sürdüren otomatik doğrulama süreçleri aracılığıyla üretime ulaşır.

---

### C4.1 Çalışma Zamanı Ortamı İzolasyonu

Konteynerlerden kaçışı ve yetki yükseltmeyi, çekirdek düzeyinde izolasyon mekanizmaları ve zorunlu erişim denetimleri aracılığıyla önleyin.

 #4.1.1    Seviye: 1    Rol: D/V
 CAP_SETUID, CAP_SETGID dışındaki tüm Linux yeteneklerini kaldırdığından emin olun ve güvenlik tabanlarında belgelenen açıkça gerekli yeteneklerin kullanıma sunulduğunu doğrulayın.
 #4.1.2    Seviye: 1    Rol: D/V
 Seccomp profillerinin, önceden onaylanmış izin listelerindeki dışındaki tüm sistem çağrılarını engellediğini doğrulayın; ihlaller konteyneri sonlandırır ve güvenlik uyarıları üretir.
 #4.1.3    Seviye: 2    Rol: D/V
 AI iş yüklerinin kök dosya sistemi salt okunur olacak şekilde, geçici veriler için tmpfs kullanılacak ve kalıcı veriler için adlandırılmış hacimler kullanılacak şekilde çalıştığını ve noexec mount seçeneklerinin uygulanmış olduğundan emin olun.
 #4.1.4    Seviye: 2    Rol: D/V
 eBPF tabanlı çalışma zamanı izleme (Falco, Tetragon veya eşdeğerleri) yetki yükseltme girişimlerini tespit eder ve tehdit oluşturan süreçleri kurumsal yanıt süresi gereksinimleri kapsamında otomatik olarak sonlandırır.
 #4.1.5    Seviye: 3    Rol: D/V
 Yüksek-riskli yapay zeka iş yüklerinin attestation doğrulaması ile donanıma izole edilmiş ortamlarda (Intel TXT, AMD SVM veya özel bare-metal düğümleri) çalıştığını doğrulayın.

---

### C4.2 Güvenli Derleme ve Dağıtım Boru Hatları

Yeniden üretilebilir derlemeler ve imzalanmış artefaktlar aracılığıyla kriptografik bütünlüğü ve tedarik zinciri güvenliğini sağlayın.

 #4.2.1    Seviye: 1    Rol: D/V
 Her commit'te infrastructure-as-code'un tfsec, Checkov veya Terrascan araçlarıyla tarandığından emin olun; CRITICAL veya HIGH seviyesindeki bulgular nedeniyle birleştirmelerin engellenmesini sağlayın.
 #4.2.2    Seviye: 1    Rol: D/V
 Konteyner derlemelerinin, derlemeler arasında aynı SHA256 özetine sahip olacak şekilde tekrarlanabilir olduğunu doğrulayın ve Sigstore ile imzalanmış SLSA Seviye 3 provenance beyanları üretin.
 #4.2.3    Seviye: 2    Rol: D/V
 Konteyner görüntülerinin CycloneDX veya SPDX SBOM'larını içerdiğini ve Cosign ile imzalandığını registry push öncesinde doğrulayın; imzasız görüntüler dağıtım sırasında reddedilsin.
 #4.2.4    Seviye: 2    Rol: D/V
 CI/CD boru hatlarının HashiCorp Vault, AWS IAM Rolleri veya Azure Managed Identity'den gelen OIDC belirteçlerini, kurumsal güvenlik politikası sınırlarını aşmayan ömürlerle kullandığını doğrulayın.
 #4.2.5    Seviye: 2    Rol: D/V
 Dağıtım süreci sırasında konteyner çalıştırılmadan önce Cosign imzalarının ve SLSA köken bilgilerinin doğrulandığından emin olun ve doğrulama hatalarının dağıtımın başarısız olmasına neden olduğunu teyit edin.
 #4.2.6    Seviye: 2    Rol: D/V
 Build ortamlarının geçici konteynerler veya VM'lerde çalıştığını, kalıcı depolama içermediğini ve üretim VPC'lerinden ağ izolasyonuna sahip olduğunu doğrulayın.

---

### C4.3 Ağ Güvenliği ve Erişim Kontrolü

Varsayılan reddetme politikaları ve şifreli iletişimlerle sıfır güvenlikli ağı uygulayın.

 #4.3.1    Seviye: 1    Rol: D/V
 Kubernetes NetworkPolicies veya eşdeğeri herhangi birinin, gerekli portlar (443, 8080, vb.) için açık izin kurallarıyla birlikte varsayılan-deny giriş/çıkış uyguladığını doğrulayın.
 #4.3.2    Seviye: 1    Rol: D/V
 SSH (port 22), RDP (port 3389) ve bulut meta veri uç noktalarının (169.254.169.254) engellendiğini veya sertifika tabanlı kimlik doğrulaması gerektirip gerekmediğini doğrulayın.
 #4.3.3    Seviye: 2    Rol: D/V
 Çıkış trafiğinin HTTP/HTTPS proxy'leri (Squid, Istio veya bulut NAT geçitleri) üzerinden filtrelendiğini, alan adlarına yönelik izin listeleriyle ve engellenen isteklerin kaydedildiğini doğrulayın.
 #4.3.4    Seviye: 2    Rol: D/V
 Servisler arası iletişimin karşılıklı TLS (mTLS) kullandığından, sertifikaların kurumsal politika doğrultusunda yenilendiğinden ve sertifika doğrulamasının zorunlu kılındığından (skip-verify bayraklarının kullanılmadığından) emin olun.
 #4.3.5    Seviye: 2    Rol: D/V
 Yapay zeka altyapısının yalnızca özel VPC'ler/VNet'ler üzerinde çalıştığını, doğrudan internet erişiminin olmadığını ve iletişimin yalnızca NAT geçitleri veya bastion sunucuları üzerinden gerçekleştirildiğini doğrulayın.

---

### C4.4 Gizli Bilgiler ve Kriptografik Anahtar Yönetimi

Donanım destekli depolama ile kimlik bilgilerini koruyun ve sıfır güvenlik erişimiyle otomatik olarak yenileyin.

 #4.4.1    Seviye: 1    Rol: D/V
 Gizli verilerin saklama sırasında AES-256 ile şifrelenmiş olarak HashiCorp Vault, AWS Secrets Manager, Azure Key Vault veya Google Secret Manager'da depolandığını doğrulayın.
 #4.4.2    Seviye: 1    Rol: D/V
 Kriptografik anahtarların FIPS 140-2 Seviye 2 HSM'lerinde (AWS CloudHSM, Azure Dedicated HSM) kurumsal kriptografik politikaya uygun olarak anahtar rotasyonu uygulanmış biçimde üretilmesini doğrulayın.
 #4.4.3    Seviye: 2    Rol: D/V
 Gizli anahtarların rotasyonunun kesintisiz dağıtımla otomatik olarak gerçekleştirildiğinden ve personel değişiklikleri veya güvenlik olayları nedeniyle anında rotasyonun tetiklendiğinden emin olun.
 #4.4.4    Seviye: 2    Rol: D/V
 Konteyner görüntülerinin API anahtarları, parolalar veya sertifikaları içeren derlemeleri engelleyen araçlarla tarandığından emin olun (GitLeaks, TruffleHog veya detect-secrets).
 #4.4.5    Seviye: 2    Rol: D/V
 Üretim ortamında gizli verilere erişimin, donanım jetonları (YubiKey, FIDO2) ile MFA gerektirdiğini ve kullanıcı kimlikleri ile zaman damgalarını içeren değiştirilemez denetim günlükleriyle kaydedildiğini doğrulayın.
 #4.4.6    Seviye: 2    Rol: D/V
 Gizli verilerin Kubernetes Secrets, bağlanmış hacimler veya init container'lar aracılığıyla enjekte edildiğini doğrulayın ve gizli verilerin asla ortam değişkenlerinde veya görüntülerde gömülü olmadığından emin olun.

---

### C4.5 Yapay Zeka İş Yükü Sandboxing ve Doğrulama

Güvensiz yapay zeka modellerini güvenli sandbox'larda kapsamlı davranışsal analizlerle izole edin.

 #4.5.1    Seviye: 1    Rol: D/V
 Harici yapay zeka modellerinin gVisor, mikroVM'ler (ör. Firecracker, CrossVM) veya Docker konteynerlerinde --security-opt=no-new-privileges ve --read-only bayraklarıyla çalıştığını doğrulayın.
 #4.5.2    Seviye: 1    Rol: D/V
 Sandbox ortamlarının ya hiç ağ bağlantısına sahip olmadığını (--network=none) ya da yalnızca localhost erişimine sahip olduğunu ve tüm dış isteklerin iptables kurallarıyla engellendiğini doğrulayın.
 #4.5.3    Seviye: 2    Rol: D/V
 Yapay zeka modeli doğrulamasının, kurumsal olarak tanımlanmış test kapsamı ve arka kapı tespiti için davranışsal analiz ile otomatik kırmızı takım testlerini içerdiğini doğrulayın.
 #4.5.4    Seviye: 2    Rol: D/V
 Bir yapay zeka modeli üretime geçirilmeden önce, sandbox sonuçlarının yetkili güvenlik personeli tarafından kriptografik olarak imzalandığını ve değiştirilemez denetim günlüklerinde saklandığını doğrulayın.
 #4.5.5    Seviye: 2    Rol: D/V
 Değerlendirmeler arasındaki süreçte sandbox ortamlarının, tam dosya sistemi ve bellek temizliği ile birlikte altın görüntülerden yok edilip yeniden oluşturulduğunu doğrulayın.

---

### C4.6 Altyapı Güvenlik İzleme

Altyapıyı otomatik düzeltme ve gerçek zamanlı uyarılar ile sürekli tarayın ve izleyin.

 #4.6.1    Seviye: 1    Rol: D/V
 Container görüntülerinin kurumsal takvimlere göre tarandığını ve kurumsal risk eşiğine dayanarak dağıtımı engelleyen KRİTİK güvenlik açıklarının bulunduğunu doğrulayın.
 #4.6.2    Seviye: 1    Rol: D/V
 Altyapının CIS Benchmarks veya NIST 800-53 kontrollerini karşılamasını, kurumsal olarak tanımlanmış uyum eşik değerleri ve başarısız kontroller için otomatik düzeltme ile doğrulayın.
 #4.6.3    Seviye: 2    Rol: D/V
 Zafiyetlerin kurumsal risk yönetimi zaman çizelgelerine göre yamalandığından emin olun; aktif olarak istismar edilen CVE'ler için acil durum prosedürlerinin uygulanmasını doğrulayın.
 #4.6.4    Seviye: 2    Rol: V
 Güvenlik uyarılarının SIEM platformlarıyla (Splunk, Elastic veya Sentinel) CEF veya STIX/TAXII formatlarını kullanarak otomatik zenginleştirme ile entegrasyonunu doğrulayın.
 #4.6.5    Seviye: 3    Rol: V
 Altyapı metriklerinin izleme sistemlerine (Prometheus, DataDog) SLA panoları ve yöneticilere yönelik raporlama ile aktarıldığını doğrulayın.
 #4.6.6    Seviye: 2    Rol: D/V
 Konfigürasyon sapmasının, organizasyonel izleme gereksinimlerine göre araçlar (Chef InSpec, AWS Config) kullanılarak tespit edildiğini doğrulayın ve yetkisiz değişiklikler için otomatik geri alım sağlayın.

---

### C4.7 Yapay Zeka Altyapı Kaynak Yönetimi

Kaynak tüketim saldırılarını önleyin ve kota ve izleme yoluyla adil kaynak tahsisini sağlayın.

 #4.7.1    Seviye: 1    Rol: D/V
 GPU/TPU kullanımının izlenmesi, kurumsal olarak belirlenen eşiklerde tetiklenen uyarılarla ve kapasite yönetim politikalarına göre otomatik ölçeklendirme veya yük dengelemenin etkinleştirilmesinin doğrulanması gerekir.
 #4.7.2    Seviye: 1    Rol: D/V
 AI iş yükü metriklerinin (çıkarım gecikmesi, işlem hacmi, hata oranları) kurumsal izleme gereksinimlerine göre toplandığını ve altyapı kullanım düzeyiyle korelasyon içinde olduğunu doğrulayın.
 #4.7.3    Seviye: 2    Rol: D/V
 Kurumsal kaynak tahsis politikalarına göre bireysel iş yüklerini sınırlandıran ve katı sınırların uygulanmasını sağlayan Kubernetes ResourceQuotas'ın veya eşdeğerinin düzgün çalıştığını doğrulayın.
 #4.7.4    Seviye: 2    Rol: V
 Harcamaların iş yükü/kiracı başına izlendiğini, kurumsal bütçe eşiklerine dayalı uyarılar ve bütçe aşımlarını önlemek için otomatik kontrollerin mevcut olduğunu doğrulayın.
 #4.7.5    Seviye: 3    Rol: V
 Kapasite planlamasının, kurumsal olarak tanımlanmış tahmin dönemleriyle geçmiş verilere dayandığını ve talep desenlerine bağlı olarak otomatik kaynak sağlama yapıldığını doğrulayın.
 #4.7.6    Seviye: 2    Rol: D/V
 Kaynak tükenmesinin örgütsel yanıt gereksinimlerine uygun olarak devre kesicileri tetiklediğini doğrulayın; kapasite politikalarına dayalı hız sınırlaması ve iş yükü izolasyonu dahil.

---

### C4.8 Çevre Ayrımı ve Taşıma Kontrolleri

Otomatik geçiş kapıları ve güvenlik doğrulaması ile sıkı ortam sınırlarını uygulayın.

 #4.8.1    Seviye: 1    Rol: D/V
 Geliştirme, test ve üretim ortamlarının ayrı VPC'lerde ve VNets'te çalıştığını ve IAM rollerinin, güvenlik gruplarının veya ağ bağlantısının paylaşılmadığını doğrulayın.
 #4.8.2    Seviye: 1    Rol: D/V
 Ortam yükseltmesinin, kurumsal olarak tanımlanmış yetkili kişilerden onay gerektirdiğini kriptografik imzalar ve değiştirilemez denetim izleriyle doğrulayın.
 #4.8.3    Seviye: 2    Rol: D/V
 Üretim ortamlarının SSH erişimini engellediğini doğrulayın, hata ayıklama uç noktalarını devre dışı bırakın ve acil durumlar hariç kurumsal ileri bildirim gerekliliklerine uygun olarak değişiklik taleplerinin zorunlu olmasını sağlayın.
 #4.8.4    Seviye: 2    Rol: D/V
 Altyapıyı kod olarak değiştiren değişikliklerin, ana dala birleştirilmeden önce eşler arası inceleme ile otomatik test ve güvenlik taramasını gerektirdiğini doğrulayın.
 #4.8.5    Seviye: 2    Rol: D/V
 Üretim dışı verilerin, kurumsal gizlilik gereksinimlerine göre anonimleştirildiğini, ya da sentetik veri üretiminin gerçekleştirildiğini veya PII çıkarımıyla tamamlanmış veri maskelemesinin doğrulandığını teyit edin.
 #4.8.6    Seviye: 2    Rol: D/V
 Terfi kapılarının otomatik güvenlik testlerini (SAST, DAST, konteyner taraması) içerdiğini ve onay için sıfır kritik bulgu gerekliliğini doğrulayın.

---

### C4.9 Altyapı Yedekleme ve Kurtarma

Altyapının dayanıklılığını otomatik yedeklemeler, test edilmiş kurtarma prosedürleri ve felaket kurtarma yetenekleri ile güvence altına alın.

 #4.9.1    Seviye: 1    Rol: D/V
 Altyapı yapılandırmalarının 3-2-1 yedekleme stratejisinin uygulanmasıyla coğrafi olarak ayrılmış bölgelerde kurumsal yedekleme planlarına göre yedeklendiğini doğrulayın.
 #4.9.2    Seviye: 2    Rol: D/V
 Ransomware koruması için yedekleme sistemlerinin izole ağlarda ayrı kimlik bilgileriyle ve hava yalıtımlı depolama ile çalıştığını doğrulayın.
 #4.9.3    Seviye: 2    Rol: V
 Kurtarma prosedürlerinin, organizasyonel takvimlere uygun olarak otomatik testlerle test edildiğini ve doğrulandığını teyit edin; bu süreçte RTO ve RPO hedeflerinin organizasyonel gereksinimleri karşıladığından emin olun.
 #4.9.4    Seviye: 3    Rol: V
 Yapay zekaya özgü çalıştırma kılavuzlarının, model ağırlıklarının geri yüklenmesini, GPU kümesinin yeniden oluşturulmasını ve hizmet bağımlılıklarının haritalanmasını içerecek şekilde felaket kurtarma süreçlerini doğrulayın.

---

### C4.10 Altyapı Uyum ve Yönetişim

Sürekli değerlendirme, belgelendirme ve otomatik kontroller yoluyla mevzuata uygunluğu sürdürün.

 #4.10.1    Seviye: 2    Rol: D/V
 Altyapı uyumunun, kurumsal takvimlere göre SOC 2, ISO 27001 veya FedRAMP kontrollerine karşı değerlendirildiğini otomatik kanıt toplama ile doğrulayın.
 #4.10.2    Seviye: 2    Rol: V
 Altyapı dokümantasyonunun ağ diyagramlarının, veri akış haritalarının ve tehdit modellerinin kuruluşun değişim yönetimi gereksinimlerine göre güncellenmiş olduğunu doğrulayın.
 #4.10.3    Seviye: 3    Rol: D/V
 Yüksek riskli değişiklikler için düzenleyici onay iş akışlarıyla birlikte altyapı değişikliklerinin otomatik uyum etki değerlendirmesinden geçtiğini doğrulayın.

---

### C4.11 Yapay Zeka Donanım Güvenliği

GPU'lar, TPU'lar ve özel yapay zeka hızlandırıcıları dahil olmak üzere Yapay Zeka’ya özgü donanım bileşenlerini güvenli hale getirin.

 #4.11.1    Seviye: 2    Rol: D/V
 AI hızlandırıcı donanım yazılımının (GPU BIOS, TPU donanım yazılımı) kriptografik imzalarla doğrulandığını ve kurumsal yama yönetimi zaman çizelgelerine göre güncellendiğini doğrulayın.
 #4.11.2    Seviye: 2    Rol: D/V
 Çalışma yükü yürütülmeden önce, yapay zeka hızlandırıcısının bütünlüğünün TPM 2.0, Intel TXT veya AMD SVM kullanılarak donanım tasdiki ile doğrulandığından emin olun.
 #4.11.3    Seviye: 2    Rol: D/V
 Çalışma yükleri arasında GPU belleğinin SR-IOV, MIG (Multi-Instance GPU) veya eşdeğer donanım bölümleme kullanılarak bellek temizlemesiyle izole edildiğini doğrulayın.
 #4.11.4    Seviye: 3    Rol: V
 Yapay zeka donanım tedarik zincirinin üretici sertifikalarıyla birlikte menşe doğrulaması ve müdahaleye karşı kanıtlayıcı ambalaj doğrulamasını içerdiğini doğrulayın.
 #4.11.5    Seviye: 3    Rol: D/V
 Donanım güvenlik modüllerinin (HSM'lerin) AI modellerinin ağırlıklarını ve kriptografik anahtarları FIPS 140-2 Seviyesi 3 veya Common Criteria EAL4+ sertifikası ile koruduğunu doğrulayın.

---

### C4.12 Uç Bilişim ve Dağıtık Yapay Zeka Altyapısı

Uç bilişim, federatif öğrenme ve çok konumlu mimarileri de kapsayan güvenli dağıtılmış yapay zeka uygulamaları.

 #4.12.1    Seviye: 2    Rol: D/V
 Uç yapay zeka cihazlarının merkezi altyapıya karşılıklı TLS kullanarak kimlik doğruladığını ve cihaz sertifikalarının kurumsal sertifika yönetim politikalarına göre yenilendiğini doğrulayın.
 #4.12.2    Seviye: 2    Rol: D/V
 Kenar cihazlarının doğrulanmış imzalarla güvenli önyükleme uyguladığından ve firmware sürüm düşürme saldırılarını önleyen geri dönüş korumasına sahip olduğundan emin olun.
 #4.12.3    Seviye: 3    Rol: D/V
 Dağıtık yapay zeka koordinasyonunun, katılımcı doğrulaması ve kötü niyetli düğüm tespitiyle Byzantine hata toleranslı uzlaşma algoritmalarını kullandığını doğrulayın.
 #4.12.4    Seviye: 3    Rol: D/V
 Uçtan buluta iletişiminin bant genişliği kısıtlaması, veri sıkıştırması ve güvenli yerel depolama ile çevrimdışı çalışma yeteneklerini içerdiğini doğrulayın.

---

### C4.13 Çoklu Bulut ve Hibrit Altyapı Güvenliği

Birden çok bulut sağlayıcısı ve hibrit bulut-yerinde dağıtımlarda güvenli Yapay Zeka iş yükleri.

 #4.13.1    Seviye: 2    Rol: D/V
 Çoklu bulut AI dağıtımlarının bulut-bağımsız kimlik federasyonunu (OIDC, SAML) ve sağlayıcılar arasında merkezi politika yönetimini kullandığını doğrulayın.
 #4.13.2    Seviye: 2    Rol: D/V
 Bulutlararası veri aktarımının uçtan uca şifreleme ile müşteri tarafından yönetilen anahtarlar ve yargı alanına göre uygulanan veri coğrafi konum kontrolleri ile gerçekleştirildiğini doğrulayın.
 #4.13.3    Seviye: 2    Rol: D/V
 Hibrit bulut yapay zeka iş yüklerinin yerinde ve bulut ortamlarında tutarlı güvenlik politikalarını uyguladığını, birleşik izleme ve uyarı ile birlikte doğrulayın.
 #4.13.4    Seviye: 3    Rol: V
 Bulut sağlayıcısına kilitlenmeyi önlemenin taşınabilir altyapı olarak kod (IaC), standartlaştırılmış API'ler ve biçim dönüştürme araçlarıyla veri dışa aktarma yeteneklerini içerdiğini doğrulayın.
 #4.13.5    Seviye: 3    Rol: V
 Çoklu bulut maliyet optimizasyonunun, kaynak yayılımını önleyen güvenlik kontrollerini ve ayrıca yetkisiz bulutlar arası veri aktarım ücretlerini de kapsadığını doğrulayın.

---

### C4.14 Altyapı Otomasyonu ve GitOps Güvenliği

AI altyapı yönetimi için altyapı otomasyon boru hatlarını ve GitOps iş akışlarını güvenli hale getirin.

 #4.14.1    Seviye: 2    Rol: D/V
 GitOps depolarının GPG anahtarlarıyla imzalanmış commit'ler gerektirdiğini ve ana dallara doğrudan push yapılmasını engelleyen dal koruma kurallarını doğrulayın.
 #4.14.2    Seviye: 2    Rol: D/V
 Altyapı otomasyonunun yetkisiz değişiklikler için kurumsal yanıt gereksinimlerine göre tetiklenen otomatik düzeltme ve geri alma yetenekleri ile drift tespiti içerdiğini doğrulayın.
 #4.14.3    Seviye: 2    Rol: D/V
 Otomatik altyapı sağlama sürecinin, uyumsuz yapılandırmalar için dağıtımı engelleme özelliğiyle güvenlik politikası doğrulamasını içerdiğini doğrulayın.
 #4.14.4    Seviye: 2    Rol: D/V
 Altyapı otomasyonu gizli bilgilerinin otomatik rotasyon ile harici gizli bilgi operatörleri (External Secrets Operator, Bank-Vaults) aracılığıyla yönetildiğini doğrulayın.
 #4.14.5    Seviye: 3    Rol: V
 Kendini onaran altyapının, güvenlik olaylarının korelasyonu ile otomatik olay müdahalesi ve paydaş bildirim iş akışlarını içerdiğini doğrulayın.

---

### C4.15 Kuantum-Dirençli Altyapı Güvenliği

Kuantum hesaplama tehditlerine karşı yapay zeka altyapısını post-kuantum kriptografi ve kuantum güvenli protokollerle hazırlayın.

 #4.15.1    Seviye: 3    Rol: D/V
 Yapay zeka altyapısının NIST onaylı kuantum sonrası kriptografik algoritmaları (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) anahtar değişimi ve dijital imzalar için uyguladığını doğrulayın.
 #4.15.2    Seviye: 3    Rol: D/V
 Kuantum anahtar dağıtımı (QKD) sistemlerinin, kuantuma dayanıklı anahtar yönetim protokolleriyle yüksek güvenlikli yapay zeka iletişimleri için uygulanıp uygulanmadığını doğrulayın.
 #4.15.3    Seviye: 3    Rol: D/V
 Kriptografik çeviklik çerçevelerinin otomatik sertifika ve anahtar döndürme ile yeni post-kuantum algoritmalarına hızlı geçişi mümkün kıldığını doğrulayın.
 #4.15.4    Seviye: 3    Rol: V
 Kuantum tehdit modellemesinin, AI altyapısının kuantum saldırılarına karşı savunmasızlığını belgelendirilmiş geçiş zaman çizelgeleri ve risk değerlendirmeleri ile birlikte değerlendirdiğini doğrulayın.
 #4.15.5    Seviye: 3    Rol: D/V
 Kuantum geçiş dönemi boyunca hibrit klasik-kuantum kriptografik sistemlerin çok katmanlı savunma sağladığını performans izleme yoluyla doğrulayın.

---

### C4.16 Gizli Bilgi İşlem ve Güvenli Enklavlar

Donanım tabanlı güvenilir yürütme ortamları ve gizli hesaplama teknolojileri kullanarak yapay zeka iş yüklerini ve model ağırlıklarını koruyun.

 #4.16.1    Seviye: 3    Rol: D/V
 Hassas yapay zeka modellerinin Intel SGX enclave'larında, AMD SEV-SNP'de veya ARM TrustZone'da şifreli bellek ve doğrulama ile çalıştığını doğrulayın.
 #4.16.2    Seviye: 3    Rol: D/V
 Doğrulayın ki gizli konteynerler (Kata Containers, mahrem hesaplama ile gVisor) yapay zeka iş yüklerini donanım tarafından uygulanan bellek şifrelemesi ile izole eder.
 #4.16.3    Seviye: 3    Rol: D/V
 Uzak doğrulamanın, AI modellerini yüklemeden önce yürütme ortamının özgünlüğünü kriptografik kanıtla doğruladığını doğrulayın.
 #4.16.4    Seviye: 3    Rol: D/V
 Gizli yapay zeka çıkarım hizmetlerinin, mühürlü model ağırlıkları ve korumalı yürütme ile şifreli hesaplama yoluyla model çıkarımını engellediğini doğrulayın.
 #4.16.5    Seviye: 3    Rol: D/V
 Güvenilir yürütme ortamı orkestrasyonunun uzaktan doğrulama ve şifreli iletişim kanallarıyla güvenli enclave yaşam döngüsünü yönettiğini doğrulayın.
 #4.16.6    Seviye: 3    Rol: D/V
 Güvenli çok taraflı hesaplama (SMPC) ile bireysel veri kümelerinin veya model parametrelerinin ifşa edilmeden ortak yapay zeka eğitiminin mümkün olduğunu doğrulayın.

---

### C4.17 Sıfır Bilgi Altyapısı

Mahremiyeti koruyan yapay zeka doğrulama ve kimlik doğrulaması için hassas bilgileri ifşa etmeden sıfır bilgi kanıtı sistemlerini uygulayın.

 #4.17.1    Seviye: 3    Rol: D/V
 Sıfır bilgi kanıtlarının (ZK-SNARK'lar, ZK-STARK'lar) AI modelinin bütünlüğünü ve eğitim kökenini, model ağırlıklarını veya eğitim verilerini açığa çıkarmadan doğrulayabileceğini doğrulayın.
 #4.17.2    Seviye: 3    Rol: D/V
 ZK-tabanlı kimlik doğrulama sistemlerinin yapay zeka hizmetleri için gizliliği koruyan kullanıcı doğrulamasını, kimlik bilgilerini ifşa etmeden mümkün kıldığını doğrulayın.
 #4.17.3    Seviye: 3    Rol: D/V
 Özel küme kesişimi (PSI) protokollerinin, bireysel veri kümelerini ifşa etmeden federasyonel yapay zeka için güvenli veri eşleşmesini sağladığını doğrulayın.
 #4.17.4    Seviye: 3    Rol: D/V
 ZKML sistemlerinin, doğru hesaplamanın kriptografik kanıtıyla doğrulanabilir yapay zeka çıkarımları sağlayabildiğini doğrulayın.
 #4.17.5    Seviye: 3    Rol: D/V
 ZK-rollups'in ölçeklenebilir, gizlilik odaklı yapay zeka işlem süreçlerini toplu doğrulama ve azaltılmış hesaplama yüküyle sağladığını doğrulayın.

---

### C4.18 Yan-Kanal Saldırı Önleme

Yapay Zeka altyapısını, hassas bilgilerin sızdırılmasına yol açabilecek zamanlama, güç, elektromanyetik ve önbellek tabanlı yan kanal saldırılarından koruyun.

 #4.18.1    Seviye: 3    Rol: D/V
 Yapay zeka çıkarım süresinin, zaman tabanlı model çıkarma saldırılarını önlemek için sabit zamanlı algoritmalar ve doldurma kullanılarak normalize edildiğini doğrulayın.
 #4.18.2    Seviye: 3    Rol: D/V
 Güç analizi korumasının gürültü enjeksiyonu, güç hattı filtrelemesi ve yapay zeka donanımı için rastgele yürütme desenleri içerdiğini doğrulayın.
 #4.18.3    Seviye: 3    Rol: D/V
 Önbelleğe dayalı yan-kanal güvenlik önleminin, bilgi sızıntısını önlemek amacıyla önbellek bölümlendirme, rastgeleleştirme ve temizleme talimatlarını kullandığını doğrulayın.
 #4.18.4    Seviye: 3    Rol: D/V
 Elektromanyetik yayıntıya karşı korumanın, kalkanlama, sinyal filtrelemesi ve rastgele işleme içerdiğini TEMPEST tarzı saldırıları önlemek için doğrulayın.
 #4.18.5    Seviye: 3    Rol: D/V
 Mikro mimari yan kanal savunmalarının spekülatif yürütme kontrollerini ve bellek erişim desenlerinin gizlenmesini içerdiğini doğrulayın.

---

### C4.19 Nöromorfik ve Özel Yapay Zeka Donanım Güvenliği

Gelişmekte olan yapay zeka donanım mimarilerini güvenli hale getirin; bunlar arasında nöromorfik çipler, FPGA'lar, özel amaçlı ASIC'ler ve optik hesaplama sistemleri bulunmaktadır.

 #4.19.1    Seviye: 3    Rol: D/V
 Neuromorfik çip güvenliğinin spike desenlerinin şifrelemesini, sinaptik ağırlıkların korunmasını ve donanım tabanlı öğrenme kuralı doğrulamasını içerdiğini doğrulayın.
 #4.19.2    Seviye: 3    Rol: D/V
 FPGA-tabanlı yapay zeka hızlandırıcılarının bitstream şifrelemesini, anti-tamper mekanizmalarını ve kimlik doğrulamalı güncellemelerle güvenli yapılandırma yüklemesini uyguladığını doğrulayın.
 #4.19.3    Seviye: 3    Rol: D/V
 Özel tasarımlı ASIC güvenliğinin çip üzerinde güvenlik işlemcilerini, donanım güven kökünü ve manipülasyon tespiti ile güvenli anahtar depolamasını içerdiğini doğrulayın.
 #4.19.4    Seviye: 3    Rol: D/V
 Optik hesaplama sistemlerinin kuantum güvenli optik şifreleme, güvenli fotonik anahtarlama ve korumalı optik sinyal işleme uyguladığını doğrulayın.
 #4.19.5    Seviye: 3    Rol: D/V
 Hibrit analog-dijital yapay zeka çiplerinin güvenli analog hesaplama, korumalı ağırlık depolama ve kimlik doğrulamalı analog-dijital dönüşüm içerdiğini doğrulayın.

---

### C4.20 Gizlilik-Koruyan Hesaplama Altyapısı

Hassas verileri AI işleme ve analizleri sırasında korumak amacıyla gizlilik korumalı hesaplama için altyapı kontrollerini uygulayın.

 #4.20.1    Seviye: 3    Rol: D/V
 Homomorfik şifreleme altyapısının hassas yapay zeka iş yüklerinde şifreli hesaplama yapılmasına olanak tanıdığını kriptografik bütünlük doğrulaması ve performans izleme ile doğrulayın.
 #4.20.2    Seviye: 3    Rol: D/V
 Özel bilgi edinme (PIR) sistemlerinin, sorgu desenlerini ifşa etmeden veritabanı sorgularını mümkün kıldığını kriptografik erişim deseni korumasıyla doğrulayın.
 #4.20.3    Seviye: 3    Rol: D/V
 Güvenli çok taraflı hesaplama protokollerinin, bireysel girdileri veya ara hesaplamaları açığa çıkarmadan mahremiyeti koruyan yapay zeka çıkarımını mümkün kıldığını doğrulayın.
 #4.20.4    Seviye: 3    Rol: D/V
 Gizliliği koruyan anahtar yönetiminin dağıtık anahtar üretimi, eşik kriptografisi ve donanım destekli koruma ile güvenli anahtar rotasyonunu içerdiğini doğrulayın.
 #4.20.5    Seviye: 3    Rol: D/V
 Gizliliği koruyan hesaplama performansının, toplu işleme, önbellekleme ve donanım hızlandırmasıyla optimize edildiğini ve bu süreçte kriptografik güvenlik garantilerinin korunduğunu doğrulayın.

---

### C4.15 Ajan Çerçevesi Bulut Entegrasyonu Güvenliği ve Hibrit Dağıtım

Bulutla entegre ajan çerçeveleri için güvenlik kontrolleri, hibrit yerinde ve bulut mimarileriyle.

 #4.15.1    Seviye: 1    Rol: D/V
 Bulut depolama entegrasyonunun ajan tarafından kontrol edilen anahtar yönetimiyle uçtan uca şifreleme kullandığını doğrulayın.
 #4.15.2    Seviye: 2    Rol: D/V
 Hibrit dağıtım güvenlik sınırlarının açıkça tanımlandığından ve şifreli iletişim kanallarıyla gerçekleştirildiğinden emin olun.
 #4.15.3    Seviye: 2    Rol: D/V
 Bulut kaynak erişiminin sürekli kimlik doğrulama ile sıfır güven doğrulamasını içerdiğini doğrulayın.
 #4.15.4    Seviye: 3    Rol: D/V
 Veri ikametgahı gereksinimlerinin, depolama konumlarının kriptografik teyidiyle uygulanıp uygulanmadığını doğrulayın.
 #4.15.5    Seviye: 3    Rol: D/V
 Bulut sağlayıcısının güvenlik değerlendirmelerinin ajan tabanlı tehdit modellemesi ve risk değerlendirmesi içerdiğini doğrulayın.

---

### Kaynaklar

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
NIST SP 800-190: Application Container Security Guide
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
NIST SP 800-53: Security Controls for Federal Information Systems
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework
CIS Kubernetes Benchmark
FIPS 140-2 Security Requirements
NIST SP 800-207: Zero Trust Architecture
IEEE 2857: Privacy Engineering for AI Systems
NIST SP 800-161: Cybersecurity Supply Chain Risk Management
NIST Post-Quantum Cryptography Standards
Intel SGX Developer Guide
AMD SEV-SNP White Paper
ARM TrustZone Technology
ZK-SNARKs: A Gentle Introduction
NIST SP 800-57: Cryptographic Key Management
Side-Channel Attack Countermeasures
Neuromorphic Computing Security Challenges
FPGA Security: Fundamentals, Evaluation, and Countermeasures
Microsoft SEAL: Homomorphic Encryption Library
HElib: Homomorphic Encryption Library
PALISADE Lattice Cryptography Library
Differential Privacy: A Survey of Results
Secure Aggregation for Federated Learning
Private Information Retrieval: Concepts and Constructions

## C5 Yapay Zeka Bileşenleri ve Kullanıcılar İçin Erişim Kontrolü ve Kimlik Yönetimi

### Kontrol Amacı

AI sistemleri için etkili erişim kontrolü, sağlam kimlik yönetimi, bağlam duyarlı yetkilendirme ve sıfır güven ilkelerine uygun olarak çalışma zamanında yürütmeyi gerektirir; bu kontroller, insanlar, hizmetler ve otonom ajanların yalnızca açıkça verilen kapsamlar içinde modeller, veriler ve hesaplama kaynaklarıyla etkileşime girmesini sağlar; ayrıca sürekli doğrulama ve denetim yetenekleriyle desteklenir.

---

### C5.1 Kimlik Yönetimi ve Doğrulama

Tüm varlıklar için kriptografik olarak doğrulanabilir kimlikler oluşturun ve yetkili işlemler için çok faktörlü kimlik doğrulama uygulayın.

 #5.1.1    Seviye: 1    Rol: D/V
 Doğrulayın ki tüm insan kullanıcılar ve hizmet ilkeleri, OIDC/SAML protokollerini kullanarak merkezi kurumsal bir kimlik sağlayıcısı (IdP) üzerinden kimlik doğrulaması gerçekleştirir ve benzersiz kimlikten belirteç eşleşmeleri ile paylaşılan hesaplar veya kimlik bilgilerinin olmaması sağlanır.
 #5.1.2    Seviye: 1    Rol: D/V
 Yüksek-riskli işlemlerin (model devreye alınması, ağırlıkların dışa aktarılması, eğitim verilerine erişim, üretim yapılandırması değişiklikleri) çok faktörlü kimlik doğrulama veya oturum yeniden doğrulama ile adımlı kimlik doğrulama gerektirdiğini doğrulayın.
 #5.1.3    Seviye: 2    Rol: D
 Yeni yetkili kullanıcıların, üretim sistemi erişimini elde etmeden önce NIST 800-63-3 IAL-2 veya buna eşdeğer standartlarla uyumlu bir kimlik kanıtlamasından geçtiğini doğrulayın.
 #5.1.4    Seviye: 2    Rol: V
 Erişim incelemelerinin üç ayda bir gerçekleştirilmesini, pasif hesapların otomatik olarak tespit edilmesini, kimlik bilgileri rotasyonunun uygulanmasını ve devre dışı bırakma iş akışlarını doğrulayın.
 #5.1.5    Seviye: 3    Rol: D/V
 Federasyonel yapay zeka ajanları, imzalanmış JWT iddiaları aracılığıyla kimlik doğrulaması yapar; bu iddialar en fazla 24 saatlik yaşam süresine sahiptir ve kaynağın kriptografik kanıtını içerir.

---

### C5.2 Kaynak Yetkilendirme ve En Az Yetki Prensibi

Tüm AI kaynakları için ince ayrıntılı erişim kontrollerini açık izin modelleriyle ve denetim izleriyle uygulayın.

 #5.2.1    Seviye: 1    Rol: D/V
 Her bir AI kaynağı için (veri kümeleri, modeller, uç noktalar, vektör koleksiyonları, gömme indeksleri, hesaplama örnekleri) rol tabanlı erişim kontrollerinin açık izin listeleri ve varsayılan reddetme politikaları ile uygulanmasını doğrulayın.
 #5.2.2    Seviye: 1    Rol: D/V
 En az ayrıcalık ilkelerinin varsayılan olarak uygulanığını doğrulayın; hizmet hesaplarının başlangıçta yalnızca okuma izinleriyle başlaması ve yazma erişimi için belgelenmiş bir iş gerekçesinin gerekli olması.
 #5.2.3    Seviye: 1    Rol: V
 Tüm erişim kontrolü değişikliklerinin onaylı değişiklik isteklerine bağlı olduğunu ve zaman damgaları, aktör kimlikleri, kaynak tanımlayıcıları ve izin değişiklikleri ile değiştirilmez biçimde günlüğe kaydedildiğini doğrulayın.
 #5.2.4    Seviye: 2    Rol: D
 Veri sınıflandırma etiketlerinin (PII, PHI, ihracat kontrollü, tescilli) türetilmiş kaynaklara (gömme temsilleri, istem önbellekleri, model çıktıları) otomatik olarak yayıldığını ve bu süreçte tutarlı politika uygulanmasının sağlandığını doğrulayın.
 #5.2.5    Seviye: 2    Rol: D/V
 Yetkisiz erişim girişimleri ve yetki yükseltme olaylarının, bağlamsal meta verilerle birlikte, SIEM sistemlerine 5 dakika içinde gerçek zamanlı uyarılar tetiklediğini doğrulayın.

---

### C5.3 Dinamik Politika Değerlendirmesi

Bağlam farkındalığına sahip yetkilendirme kararları için özelliklere dayalı erişim kontrolü (ABAC) motorlarını dağıtın ve denetim yetenekleriyle donatın.

 #5.3.1    Seviye: 1    Rol: D/V
 Yetkilendirme kararlarının, kimlik doğrulamalı API'ler üzerinden erişilebilen, kriptografik bütünlük korumasına sahip özel bir politika motoruna (OPA, Cedar veya eşdeğeri) dışa aktarıldığını doğrulayın.
 #5.3.2    Seviye: 1    Rol: D/V
 Politikaların çalışma zamanında dinamik öznitelikleri değerlendirip değerlendirmediğini doğrulayın; bunlar arasında kullanıcı yetki seviyesi, kaynak hassasiyeti sınıflandırması, istek bağlamı, kiracı izolasyonu ve zamansal kısıtlamalar bulunmaktadır.
 #5.3.3    Seviye: 2    Rol: D
 Politika tanımlarının üretime dağıtımdan önce sürüm kontrollü, akran incelemesine tabi ve otomatik testlerle CI/CD süreçlerinde doğrulanmış olduğundan emin olun.
 #5.3.4    Seviye: 2    Rol: V
 Politika değerlendirme sonuçlarının yapılandırılmış karar gerekçelerini içerdiğini ve bu sonuçların SIEM sistemlerine korelasyon analizi ve uyum raporlaması için iletildiğini doğrulayın.
 #5.3.5    Seviye: 3    Rol: D/V
 Politika önbelleği yaşam süresi (TTL) değerlerinin yüksek hassasiyetli kaynaklar için 5 dakikayı aşmaması ve önbellek geçersizleştirme özelliğine sahip standart kaynaklar için 1 saati aşmaması gerektiğini doğrulayın.

---

### C5.4 Sorgu Zamanı Güvenlik Uygulaması

Veritabanı katmanı güvenlik kontrollerini zorunlu filtreleme ve satır düzeyi güvenlik politikaları ile uygulayın.

 #5.4.1    Seviye: 1    Rol: D/V
 Tüm vektör veritabanları ve SQL sorgularının, veritabanı motoru düzeyinde zorunlu güvenlik filtrelerini (kiracı kimliği, hassasiyet etiketleri, kullanıcı kapsamı) içermesini ve bu filtrelerin uygulama kodunda değil veritabanı motoru düzeyinde uygulanmasını doğrulayın.
 #5.4.2    Seviye: 1    Rol: D/V
 Satır seviyesi güvenlik (RLS) politikalarının ve alan düzeyinde maskelemenin politika kalıtımı ile etkinleştirildiğini tüm vektör veritabanları, arama indeksleri ve eğitim veri kümeleri için doğrulayın.
 #5.4.3    Seviye: 2    Rol: D
 Başarısız yetkilendirme değerlendirmelerinin, sorguları derhal iptal ederek ve boş sonuç kümeleri döndürmek yerine açık yetkilendirme hata kodları döndürerek 'confused deputy attacks' olarak bilinen saldırıları önleyeceğini doğrulayın.
 #5.4.4    Seviye: 2    Rol: V
 Politika değerlendirme gecikmesinin yetkilendirme atlamasına yol açabilecek zaman aşımı durumları için otomatik uyarılarla sürekli olarak izlendiğini doğrulayın.
 #5.4.5    Seviye: 3    Rol: D/V
 Sorgu yeniden deneme mekanizmalarının, aktif kullanıcı oturumları süresince dinamik izin değişikliklerini hesaba katarak yetkilendirme politikalarını yeniden değerlendirdiğini doğrulayın.

---

### C5.5 Çıktı Filtreleme ve Veri Kaybı Önleme

Yapay zeka tarafından üretilen içeriklerde yetkisiz veri ifşasını önlemek için son işlem kontrollerini devreye alın.

 #5.5.1    Seviye: 1    Rol: D/V
 İstek sahiplerine içerik iletilmeden önce, çıkarım sonrası filtreleme mekanizmalarının yetkisiz Kişisel Tanımlanabilir Bilgiler (PII), sınıflandırılmış bilgiler ve tescilli verileri tarayıp sansürlediğini doğrulayın.
 #5.5.2    Seviye: 1    Rol: D/V
 Model çıktılarındaki alıntıların, referansların ve kaynak atıflarının çağıranların yetkileriyle doğrulandığını ve yetkisiz erişim tespit edildiğinde kaldırıldığını doğrulayın.
 #5.5.3    Seviye: 2    Rol: D
 Çıktı biçimi sınırlamalarının (temizlenmiş PDF'ler, meta verileri kaldırılmış görüntüler, onaylı dosya türleri) kullanıcı izin seviyelerine ve veri sınıflandırmalarına göre uygulanıp uygulanmadığını doğrulayın.
 #5.5.4    Seviye: 2    Rol: V
 Karartma algoritmalarının deterministik olduğundan, sürüm kontrollü olduğundan ve uyum incelemeleri ile adli analizleri desteklemek için denetim günlükleri tuttuğundan emin olun.
 #5.5.5    Seviye: 3    Rol: V
 Yüksek riskli redaksiyon olaylarının, adli inceleme için veri sızdırılmadan orijinal içeriğin kriptografik hash değerlerini içeren adaptif günlükler ürettiğini doğrulayın.

---

### C5.6 Çoklu-Kiracı İzolasyonu

Paylaşılan yapay zeka altyapısında kiracılar arasında kriptografik ve mantıksal izolasyonu sağlayın.

 #5.6.1    Seviye: 1    Rol: D/V
 Kiracı başına isim alanına göre ayrıştırılmış bellek alanları, gömme depoları, önbellek girdileri ve geçici dosyaların, kiracı silindiğinde veya oturum sonlandırıldığında güvenli silme işlemi ile temizlendiğini doğrulayın.
 #5.6.2    Seviye: 1    Rol: D/V
 Her API isteğinin, oturum bağlamına ve kullanıcı yetkilendirmelerine karşı kriptografik olarak doğrulanmış bir kiracı tanımlayıcısını içerdiğini doğrulayın.
 #5.6.3    Seviye: 2    Rol: D
 Service mesh'leri ve konteyner orkestrasyon platformları içinde çapraz kiracı iletişimi için ağ politikalarının varsayılan reddetme kurallarını uyguladığını doğrulayın.
 #5.6.4    Seviye: 3    Rol: D
 Her kiracı için benzersiz şifreleme anahtarlarının mevcut olduğundan emin olun; CMK (müşteri tarafından yönetilen anahtar) desteği ile kiracıların veri depolama alanları arasında kriptografik izolasyon sağlandığını doğrulayın.

---

### C5.7 Otonom Ajan Yetkilendirmesi

AI ajanları ve otonom sistemler için izinleri, kapsamlı yetenek belirteçleri ve sürekli yetkilendirme yoluyla yönetin.

 #5.7.1    Seviye: 1    Rol: D/V
 Otonom ajanların, izin verilen eylemleri, erişilebilir kaynakları, zaman sınırlarını ve operasyonel kısıtlamaları açıkça sıralayan kapsama sahip yetki belirteçleri aldıklarını doğrulayın.
 #5.7.2    Seviye: 1    Rol: D/V
 Yüksek riskli yetenekler (dosya sistemi erişimi, kod çalıştırma, harici API çağrıları, finansal işlemler) varsayılan olarak devre dışı bırakılmıştır ve etkinleştirme için işletme gerekçeleriyle açık yetkilendirme gerektirir.
 #5.7.3    Seviye: 2    Rol: D
 Kullanıcı oturumlarına bağlı olduklarını doğrulayın, kriptografik bütünlük korumasını içermesini sağlayın ve bunların çevrimdışı senaryolarda kalıcı olarak saklanamayacağını veya yeniden kullanılamayacağını garanti edin.
 #5.7.4    Seviye: 2    Rol: V
 Ajan tarafından başlatılan eylemlerin ABAC politika motoru üzerinden tam bağlam değerlendirmesiyle ve denetim kayıtlarıyla ikincil yetkilendirmeden geçtiğini doğrulayın.
 #5.7.5    Seviye: 3    Rol: V
 Ajanın hata durumları ve istisna işlemesinin kapsama alanı bilgisini içerdiğini doğrulayın; bu, olay analizi ve adli soruşturmayı destekler.

---

### Kaynaklar

#### Standartlar ve Çerçeveler

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Uygulama Kılavuzları

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### AI-Özel Güvenlik

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Modeller, Çerçeveler ve Veriler için Tedarik Zinciri Güvenliği

### Kontrol Amacı

Yapay zeka tedarik zinciri saldırıları, üçüncü taraf modelleri, çerçeveler veya veri kümelerini arka kapılar, önyargı veya istismar edilebilir kod eklemek amacıyla kullanır. Bu kontroller uçtan uca köken bilgisi, zafiyet yönetimi ve izleme sağlayarak tüm model yaşam döngüsünü korur.

---

### C6.1 Önceden Eğitilmiş Modelin Değerlendirilmesi ve Kökeni

Üçüncü taraf model kökenlerini, lisanslarını ve gizli davranışlarını herhangi bir ince ayar veya devreye alma öncesinde değerlendirip doğrulayın.

 #6.1.1    Seviye: 1    Rol: D/V
 Her üçüncü taraf model artefaktının imzalı bir menşe kaydı içerdiğini ve bu kaydın kaynak deposunu ve commit hash'ini tanımladığını doğrulayın.
 #6.1.2    Seviye: 1    Rol: D/V
 Modellerin içe aktarılmadan önce otomatik araçlarla kötü niyetli katmanlar veya Trojan tetikleyicileri için tarandığından emin olun.
 #6.1.3    Seviye: 2    Rol: D
 Doğrulayın ki transfer‑learning ile yapılan ince ayarların adversarial değerlendirmenin geçmesini sağlayıp gizli davranışları tespit ettiğini.
 #6.1.4    Seviye: 2    Rol: V
 Model lisanslarının, ihracat kontrol etiketlerinin ve veri kökeni beyanlarının ML-BOM girdisine kaydedildiğini doğrulayın.
 #6.1.5    Seviye: 3    Rol: D/V
 Yüksek riskli modellerin (halka açık olarak yüklenen ağırlıklar, doğrulanmamış geliştiriciler) insan incelemesi ve onayı tamamlanana kadar karantinada kalmasını sağlayın.

---

### C6.2 Çerçeve ve Kütüphane Taraması

Çalışma zamanı yığını güvenli tutmak için ML çerçeveleri ve kütüphanelerini CVE'ler ve zararlı kod için sürekli olarak tarayın.

 #6.2.1    Seviye: 1    Rol: D/V
 CI süreçlerinin yapay zeka çerçeveleri ve kritik kütüphaneler üzerinde bağımlılık tarama araçlarını çalıştırdığından emin olun.
 #6.2.2    Seviye: 1    Rol: D/V
 Kritik güvenlik açıklarının (CVSS ≥ 7.0) üretim görüntülerine geçişi engellediğini doğrulayın.
 #6.2.3    Seviye: 2    Rol: D
 Fork edilmiş veya vendor edilen ML kütüphanelerinde statik kod analizi çalıştığını doğrulayın.
 #6.2.4    Seviye: 2    Rol: V
 Çerçeve yükseltme önerilerinin, halka açık CVE beslemelerine atıfta bulunan bir güvenlik etkisi değerlendirmesi içerdiğini doğrulayın.
 #6.2.5    Seviye: 3    Rol: V
 İmzalanmış SBOM'dan sapacak şekilde beklenmeyen dinamik kütüphane yüklemeleri üzerinde çalışma zamanı sensörlerinin uyarı verdiğini doğrulayın.

---

### C6.3 Bağımlılık Sabitleme ve Doğrulama

Her bağımlılığı değiştirilemez özetlerle kilitleyin ve derlemeleri yeniden üretin; böylece aynı, değiştirilmemiş çıktıların elde edilmesini garanti edin.

 #6.3.1    Seviye: 1    Rol: D/V
 Tüm paket yöneticilerinin sürüm kilitlemesini kilit dosyaları aracılığıyla zorunlu kıldığını doğrulayın.
 #6.3.2    Seviye: 1    Rol: D/V
 Konteyner referanslarında değiştirilemez özetlerin, değiştirilebilir etiketler yerine kullanıldığını doğrulayın.
 #6.3.3    Seviye: 2    Rol: D
 reproducible‑build kontrollerinin CI çalışmaları arasındaki hash değerlerini karşılaştırdığını doğrulayın ve çıktıların aynı olduğundan emin olun.
 #6.3.4    Seviye: 2    Rol: V
 Denetim izlenebilirliği için derleme doğrulamalarının 18 ay boyunca saklandığından emin olun.
 #6.3.5    Seviye: 3    Rol: D
 Geçerliliğini yitirmiş bağımlılıkların otomatik PR'leri tetikleyerek sabitlenmiş sürümlerin güncellenmesini veya fork edilmesini sağladığını doğrulayın.

---

### C6.4 Güvenilir Kaynak Denetimi

Sadece kriptografik olarak doğrulanmış, kuruluş tarafından onaylanmış kaynaklardan artefakt indirmelerine izin verin ve diğer her şeyi engelleyin.

 #6.4.1    Seviye: 1    Rol: D/V
 Model ağırlıklarının, veri kümelerinin ve konteynerlerin yalnızca onaylı alanlardan veya dahili kayıt depolarından indirildiğini doğrulayın.
 #6.4.2    Seviye: 1    Rol: D/V
 Sigstore/Cosign imzalarının yayımlayıcı kimliğini, artefaktlar yerel olarak önbelleğe alınmadan önce doğrulayın.
 #6.4.3    Seviye: 2    Rol: D
 Güvenilir‑kaynak politikası uygulamak için çıkış proxy'lerinin kimlik doğrulaması yapılmamış artefakt indirmelerini engellediğini doğrulayın.
 #6.4.4    Seviye: 2    Rol: V
 Depo izin listelerinin her giriş için işletme gerekçesi kanıtı ile birlikte üç ayda bir gözden geçirildiğini doğrulayın.
 #6.4.5    Seviye: 3    Rol: V
 Politika ihlallerinin artefaktların karantinaya alınmasına ve bağımlı pipeline çalıştırmalarının geri alınmasına yol açtığını doğrulayın.

---

### C6.5 Üçüncü‑Taraf Veri Kümesi Risk Değerlendirmesi

Dış veri setlerini zehirlenmeye karşı, yanlılık ve yasal uygunluk açısından değerlendirip yaşam döngüsü boyunca izleyin.

 #6.5.1    Seviye: 1    Rol: D/V
 Harici veri kümelerinin zehirlenme riski puanlamasına tabi tutulduğunu doğrulayın (örneğin, veri parmak izi çıkarımı, aykırı değer tespiti).
 #6.5.2    Seviye: 1    Rol: D
 Veri kümesinin onayından önce önyargı metriklerinin (demografik eşitlik, eşit fırsat) hesaplandığından emin olun.
 #6.5.3    Seviye: 2    Rol: V
 Veri kümeleri için köken ve lisans koşullarının ML‑BOM girdilerine kaydedildiğini doğrulayın.
 #6.5.4    Seviye: 2    Rol: V
 Barındırılan veri kümelerinde periyodik izlemenin drift veya bozulmayı tespit ettiğini doğrulayın.
 #6.5.5    Seviye: 3    Rol: D
 İzinsiz içeriğin (telif hakkı, PII) eğitime başlamadan önce otomatik temizleme ile kaldırıldığını doğrulayın.

---

### C6.6 Tedarik Zinciri Saldırı İzleme

Tedarik-zinciri tehditlerini CVE beslemeleri, audit-log analitiği ve red-team simülasyonları yoluyla erken tespit edin.

 #6.6.1    Seviye: 1    Rol: V
 CI/CD denetim günlüklerinin anormal paket çekmeleri veya değiştirilmiş derleme adımları için SIEM tespitlerine iletilmesini doğrulayın.
 #6.6.2    Seviye: 2    Rol: D
 Olay müdahale kılavuzlarının, ele geçirilmiş modeller veya kütüphaneler için geri alma prosedürlerini içerdiğini doğrulayın.
 #6.6.3    Seviye: 3    Rol: V
 Tehdit‑istihbaratı zenginleştirmesinin ML‑e özgü göstergeleri etiketlediğini uyarı triage'inde doğrulayın (örnek olarak model‑zehirlenmesi IoC'leri).

---

### C6.7 Model Artefaktları için ML‑BOM

Dağıtım zamanında bileşen bütünlüğünü doğrulayabilmeleri için ayrıntılı ML'e özgü SBOM'lar (ML-BOM'lar) oluşturun ve imzalayın.

 #6.7.1    Seviye: 1    Rol: D/V
 Her model artefaktının, veri setlerini, ağırlıkları, hiperparametreleri ve lisansları içeren bir ML‑BOM yayımladığını doğrulayın.
 #6.7.2    Seviye: 1    Rol: D/V
 ML‑BOM üretiminin ve Cosign imzalama işlemlerinin CI'de otomatikleştirildiğini ve birleştirme için zorunlu olduğunu doğrulayın.
 #6.7.3    Seviye: 2    Rol: D
 ML‑BOM tamamlık kontrollerinin herhangi bir bileşen meta verisi (hash değeri, lisans) eksik olduğunda derlemenin başarısız olmasına yol açacağını doğrulayın.
 #6.7.4    Seviye: 2    Rol: V
 Aşağı akıştaki tüketicilerin dağıtım zamanında içe aktarılan modelleri doğrulamak için API üzerinden ML-BOM'ları sorgulayabildiğini doğrulayın.
 #6.7.5    Seviye: 3    Rol: V
 ML‑BOM’lar sürüm kontrolünde tutulduğundan ve yetkisiz değişiklikleri tespit etmek için fark karşılaştırması yapıldığından emin olun.

---

### Kaynaklar

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
AI & Transparency: Protect ML Models – ReversingLabs
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## C7 Model Davranışı, Çıktı Kontrolü ve Güvenlik Güvencesi

### Kontrol Amacı

Model çıktıları üretimde yapılandırılmış, güvenilir, güvenli, açıklanabilir ve sürekli izlenmelidir. Bunu yapmak halüsinasyonları, gizlilik ihlallerini, zararlı içeriği ve kontrolsüz eylemleri azaltırken kullanıcı güvenini ve düzenleyici uyumunu artırır.

---

### C7.1 Çıktı Biçimi Zorunluluğu

Katı şemalar, kısıtlı çözümleme ve sonraki doğrulama, bozulmuş veya kötü niyetli içeriğin yayılmadan önce engeller.

 #7.1.1    Seviye: 1    Rol: D/V
 Yanıt şemalarının (örneğin JSON Şeması) sistem isteminde sunulduğundan emin olun ve her çıktının otomatik olarak doğrulanmasını sağlayın; uyumsuz çıktılar onarım veya reddedilmeyi tetikler.
 #7.1.2    Seviye: 1    Rol: D/V
 Taşma veya prompt enjeksiyonu yan kanallarını önlemek için kısıtlı çözümlenmenin (durdurma belirteçleri, düzenli ifadeler, maksimum token sayısı) etkin olduğundan emin olun.
 #7.1.3    Seviye: 2    Rol: D/V
 Çıktıları güvenilmez olarak ele alan aşağı akış bileşenlerini doğrulayın ve bunları şemalara karşı ya da enjeksiyona karşı güvenli deserializer'lar ile doğrulayın.
 #7.1.4    Seviye: 3    Rol: V
 Yanlış çıktı olaylarının kaydedildiğini, hız sınırlamasına tabi tutulduğunu ve izleme için görünür kılındığını doğrulayın.

---

### C7.2 Halüsinasyon Tespiti ve Hafifletme

Belirsizlik tahmini ve yedek stratejileri uydurulmuş cevapları sınırlıyor.

 #7.2.1    Seviye: 1    Rol: D/V
 Token-düzeyindeki log-olasılıklar, topluluk yöntemi kendi kendine tutarlılığı veya ince ayarlı halüsinasyon tespit edicilerinin her yanıt için bir güven skorunu atadığını doğrulayın.
 #7.2.2    Seviye: 1    Rol: D/V
 Yanıtların, ayarlanabilir bir güven eşik değerinin altında kaldığında geri dönüş iş akışlarını tetiklediğini doğrulayın (örneğin, retrieval-augmented generation, ikincil model veya insan incelemesi).
 #7.2.3    Seviye: 2    Rol: D/V
 Halüsinasyon olaylarının kök-neden meta verileriyle etiketlendiğini ve post-mortem ile ince ayar iş akışlarına yönlendirildiğini doğrulayın.
 #7.2.4    Seviye: 3    Rol: D/V
 Önemli model veya bilgi tabanı güncellemelerinin ardından eşiklerin ve dedektörlerin yeniden kalibre edildiğini doğrulayın.
 #7.2.5    Seviye: 3    Rol: V
 Panodaki görselleştirmelerin yanılsama oranlarını takip ettiğini doğrulayın.

---

### C7.3 Çıktı Güvenliği ve Gizlilik Filtreleme

Politika filtreleri ve kırmızı takım kapsamı kullanıcıları ve gizli verileri korurlar.

 #7.3.1    Seviye: 1    Rol: D/V
 Üretim öncesi ve üretim sonrası sınıflandırıcılarının politikayla uyumlu olarak nefret içeriklerini, taciz içeriklerini, kendine zarar verme içeriklerini, aşırılık yanlısı içerikleri ve cinsel içerikli içerikleri engellediğini doğrulayın.
 #7.3.2    Seviye: 1    Rol: D/V
 Her yanıt için PII/PCI tespiti ile otomatik redaksiyonun çalıştığını doğrulayın; ihlaller bir gizlilik olayı olarak bildirilir.
 #7.3.3    Seviye: 2    Rol: D
 Gizlilik etiketlerinin (ör. ticari sırlar) modaliteler arasında yayıldığını doğrulayın ve metin, görüntü veya kod gibi alanlarda sızıntıyı önlediğini teyit edin.
 #7.3.4    Seviye: 3    Rol: D/V
 Filtreyi aşma girişimlerinin veya yüksek riskli sınıflandırmaların ikincil onay veya kullanıcı yeniden kimlik doğrulaması gerektirip gerektirmediğini doğrulayın.
 #7.3.5    Seviye: 3    Rol: D/V
 Filtreleme eşiklerinin yasal yargı alanlarına ve kullanıcı yaş ve rol bağlamına uygun olduğunu doğrulayın.

---

### C7.4 Çıktı ve Eylem Sınırlandırması

Oran sınırları ve onay kapıları kötüye kullanımını ve aşırı özerkliği önler.

 #7.4.1    Seviye: 1    Rol: D
 Kullanıcı başına ve API anahtarı başına kotaların, 429 hatalarında üstel geri çekme ile istekleri, tokenleri ve maliyeti sınırladığını doğrulayın.
 #7.4.2    Seviye: 1    Rol: D/V
 Ayrıcalıklı işlemlerin (dosya yazma, kod çalıştırma, ağ çağrıları) politika tabanlı onay veya insanın dahil olduğu bir süreç gerektirdiğini doğrulayın.
 #7.4.3    Seviye: 2    Rol: D/V
 Çapraz-mod tutarlılık kontrollerinin, aynı istek için üretilen görüntülerin, kodun ve metnin kötü niyetli içerik kaçırılmasına olanak tanımadığını doğrulayın.
 #7.4.4    Seviye: 2    Rol: D
 Ajan vekalet derinliğinin, özyineleme sınırlarının ve izin verilen araç listelerinin açıkça yapılandırıldığını doğrulayın.
 #7.4.5    Seviye: 3    Rol: V
 Sınır ihlallerinin yapılandırılmış güvenlik olayları ürettiğini ve bu olayların SIEM'e aktarılması için iletildiğini doğrulayın.

---

### C7.5 Çıktı Açıklanabilirliği

Şeffaf sinyaller kullanıcı güvenini artırır ve dahili hata ayıklamayı kolaylaştırır.

 #7.5.1    Seviye: 2    Rol: D/V
 Risk değerlendirmesi uygun olduğunda kullanıcıya yönelik güven skorlarının veya kısa gerekçe özetlerinin gösterildiğini doğrulayın.
 #7.5.2    Seviye: 2    Rol: D/V
 Üretilen açıklamaların hassas sistem istemlerini veya özel verileri ifşa etmediğini doğrulayın.
 #7.5.3    Seviye: 3    Rol: D
 Sistemin token düzeyindeki log-olasılıklarını veya dikkat haritalarını yakalayıp yetkili inceleme için sakladığını doğrulayın.
 #7.5.4    Seviye: 3    Rol: V
 Denetim için, açıklanabilirlik artefaktlarının model sürümleriyle birlikte sürüm kontrollü olduğundan emin olun.

---

### C7.6 İzleme Entegrasyonu

Gerçek zamanlı gözlemlenebilirlik, geliştirme ile üretim arasındaki döngüyü kapatır.

 #7.6.1    Seviye: 1    Rol: D
 Metriklerin (şema ihlalleri, halüsinasyon oranı, toksisite, PII sızıntıları, gecikme, maliyet) merkezi bir izleme platformuna akışını doğrulayın.
 #7.6.2    Seviye: 1    Rol: V
 Her güvenlik metriği için uyarı eşiklerinin tanımlı olduğundan ve nöbetçi kişiler için yükseltme yollarının bulunduğundan emin olun.
 #7.6.3    Seviye: 2    Rol: V
 Panoların çıktı anomalilerini model/sürüm, özellik bayrağı ve üst akış verisi değişiklikleriyle ilişkilendirdiğini doğrulayın.
 #7.6.4    Seviye: 2    Rol: D/V
 Belgelenmiş bir MLOps iş akışında izleme verilerinin yeniden eğitime, ince ayara veya kural güncellemelerine geri beslenmesini doğrulayın.
 #7.6.5    Seviye: 3    Rol: V
 İzleme boru hatlarının sızma testine tabi tutulduğunu ve erişim kontrollü olduğunu doğrulayın; böylece hassas logların sızdırılmasını önleyin.

---

### 7.7 Üretken Medya Güvenlik Önlemleri

Yapay zeka sistemlerinin yasa dışı, zararlı veya yetkisiz medya içeriği üretmesini engellemek için politika kısıtlarının uygulanması, çıktı doğrulaması ve izlenebilirlik yoluyla.

 #7.7.1    Seviye: 1    Rol: D/V
 Sistem istemlerinin ve kullanıcı talimatlarının açıkça yasadışı, zararlı veya rızası alınmamış derin sahte medya üretimini yasakladığını doğrulayın (örneğin, görüntü, video, ses).
 #7.7.2    Seviye: 2    Rol: D/V
 İsteklerin, taklit üretimine, cinsel içerikli derin sahte videolar üretmeye veya rızası olmadan gerçek kişileri tasvir eden medyayı üretmeye yönelik girişimlere karşı filtrelendiğini doğrulayın.
 #7.7.3    Seviye: 2    Rol: V
 Sistemin izinsiz çoğaltmayı önlemek için algısal özetlemeyi (perceptual hashing), filigran tespitini veya parmak izi çıkarımını kullanıp kullanmadığını doğrulayın.
 #7.7.4    Seviye: 3    Rol: D/V
 Üretilen tüm medyanın kriptografik olarak imzalanmış, filigranlı veya tahrife karşı dayanıklı köken meta verileriyle gömülü olduğundan emin olun; bu, sonraki izlenebilirlik için gereklidir.
 #7.7.5    Seviye: 3    Rol: V
 Atlatma girişimlerinin (örneğin, istemleri karıştırma, argo, karşı saldırgan ifadeler) tespit edildiğini, kaydedildiğini ve hız sınırlamasına tabi tutulduğunu doğrulayın; tekrarlanan kötüye kullanımın izleme sistemlerine bildirilmesini sağlayın.

### Kaynaklar

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Improper Output Handling – OWASP LLM05:2025
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
LLM Red-Teaming Guide
Sensitive Information Disclosure in LLMs
LangChain – Chat Model Rate Limiting
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## C8 Bellek, Gömülü Temsiller ve Vektör Veritabanı Güvenliği

### Kontrol Amacı

Gömme temsilleri ve vektör depoları, günümüz yapay zekâ sistemlerinin "canlı bellek"i olarak görev yapar; kullanıcı tarafından sağlanan verileri sürekli kabul eder ve Retrieval-Augmented Generation (RAG) aracılığıyla model bağlamlarına geri getirir. Yönetimden bağımsız bırakılırsa bu hafıza Kişisel Tanımlanabilir Bilgiler (PII) sızıntısına yol açabilir, rızayı ihlal edebilir veya orijinal metnin yeniden oluşturulmasına yol açabilir. Bu kontrol ailesinin amacı, bellek iş akışlarını ve vektör veritabanlarını güçlendirmek; böylece erişimin en az ayrıcalık ilkesine göre sınırlandırılması, gömme temsillerinin gizliliğinin korunması, depolanan vektörlerin süresinin dolabilmesi veya istek üzerine iptal edilebilmesi ve kullanıcı başına belleğin asla başka bir kullanıcının istemlerini veya tamamlamalarını kirletmemesinin sağlanmasıdır.

---

### C8.1 Bellek Üzerindeki Erişim Denetimleri & RAG Endeksler

Her vektör koleksiyonunda ayrıntılı erişim kontrollerini uygulayın.

 #8.1.1    Seviye: 1    Rol: D/V
 Satır/ad alanı düzeyinde erişim kontrol kurallarının kiracı, koleksiyon veya belge etiketi başına ekleme, silme ve sorgu işlemlerini kısıtladığını doğrulayın.
 #8.1.2    Seviye: 1    Rol: D/V
 API anahtarlarının veya JWT'lerin kapsama sahip iddialar taşıdığından ve en az üç ayda bir yeniden rotalandırıldığından emin olun.
 #8.1.3    Seviye: 2    Rol: D/V
 Yetki yükseltme girişimlerinin (örneğin isim alanları arası benzerlik sorguları) tespit edildiğini ve 5 dakika içinde SIEM'e kaydedildiğini doğrulayın.
 #8.1.4    Seviye: 2    Rol: D/V
 Vektör veritabanı denetim günlüğünün şu alanları kaydettiğini doğrulayın: konu kimliği, işlem, vektör kimliği/ad alanı, benzerlik eşiği ve sonuç sayısı.
 #8.1.5    Seviye: 3    Rol: V
 Erişim kararlarının motorlar güncellendiğinde veya indeks bölütleme kuralları değiştiğinde atlatma güvenlik açıkları için test edildiğini doğrulayın.

---

### C8.2 Gömme Temizleme ve Doğrulama

Metni Kişisel Tanımlayıcı Bilgiler (PII) için ön taramadan geçirin, vektörleştirmeden önce gizleyin veya pseudonimleştirin ve isteğe bağlı olarak gömülü temsilleri son işlemden geçirerek kalıntı sinyallerini temizleyin.

 #8.2.1    Seviye: 1    Rol: D/V
 PII ve düzenlenen verilerin otomatik sınıflandırıcılar aracılığıyla tespit edildiğini ve gömme öncesinde maskeleme, tokenleştirme veya çıkarma işlemlerinin uygulanıp uygulanmadığını doğrulayın.
 #8.2.2    Seviye: 1    Rol: D
 Gömme işlem hatlarının, çalıştırılabilir kod içeren veya UTF-8 olmayan artefaktlar içeren girdileri reddettiğini veya karantinaya aldığını doğrulayın.
 #8.2.3    Seviye: 2    Rol: D/V
 Yerel veya metrik diferansiyel gizlilik temizlemesinin, herhangi bir bilinen PII belirtecine olan mesafenin ayarlanabilir bir eşik değerinin altında kaldığı durumlarda uygulanmasını doğrulayın.
 #8.2.4    Seviye: 2    Rol: V
 Temizleme etkililiğinin (örneğin, PII redaksiyonunun geri çağırma oranı, semantik sapma) yıl içinde en az 2 kez benchmark korpusları karşısında doğrulandığından emin olun.
 #8.2.5    Seviye: 3    Rol: D/V
 Sanitizasyon yapılandırmalarının sürüm denetimli olduğunu ve değişikliklerin akran incelemesinden geçtiğini doğrulayın.

---

### Bellek Süresinin Dolması, İptal ve Silme

GDPR "unutulma hakkı" ve benzeri yasalar zamanında silinmeyi zorunlu kılar; bu nedenle vektör depoları TTL'leri, kalıcı silme işlemlerini ve tombstone kaydı yapmayı desteklemek zorundadır ki iptal edilen vektörler geri getirilemez veya yeniden indekslenemez.

 #8.3.1    Seviye: 1    Rol: D/V
 Her vektör ve meta veri kaydının, otomatik temizleme görevleri tarafından dikkate alınan bir TTL veya açık saklama etiketine sahip olduğundan emin olun.
 #8.3.2    Seviye: 1    Rol: D/V
 Kullanıcı tarafından başlatılan silme isteklerinin vektörleri, meta verileri, önbellek kopyaları ve türev indeksleri 30 gün içinde temizlediğini doğrulayın.
 #8.3.3    Seviye: 2    Rol: D
 Mantıksal silme işlemlerinin, donanım bunu destekliyorsa depolama bloklarının kriptografik olarak yok edilmesiyle veya Anahtar Kasası anahtarının yok edilmesiyle takip edildiğini doğrulayın.
 #8.3.4    Seviye: 3    Rol: D/V
 Geçerliliğini yitirmiş vektörlerin en yakın komşu arama sonuçlarından hariç tutulduğunu, süresi dolduktan sonra < 500 ms içinde doğrulayın.

---

### C8.4 Gömme Tersine Çevirme ve Sızıntıyı Önleme

Son savunmalar—gürültü üst üste koyma, projeksiyon ağları, mahremiyet-nöron bozulması ve uygulama katmanı şifrelemesi—token düzeyinde tersine çevirme oranlarını %5'in altında düşürebilir.

 #8.4.1    Seviye: 1    Rol: V
 İnversiyon saldırılarını, üyelik çıkarımı saldırılarını ve öznitelik çıkarımı saldırılarını kapsayan resmi bir tehdit modelinin mevcut olduğunu ve yıllık olarak gözden geçirildiğini doğrulayın.
 #8.4.2    Seviye: 2    Rol: D/V
 Uygulama katmanı şifrelemesi veya aramalı şifrelemenin altyapı yöneticileri veya bulut personeli tarafından yapılan doğrudan okumalarından vektörleri koruduğunu doğrulayın.
 #8.4.3    Seviye: 3    Rol: V
 Savunma parametrelerinin (Differential Privacy için ε, gürültü σ, projeksiyon derecesi k) mahremiyetinin %99 veya daha yüksek token korumasını ve yararlılığın %3 veya daha düşük doğruluk kaybını dengelediğini doğrulayın.
 #8.4.4    Seviye: 3    Rol: D/V
 İnversion-resilience metriklerinin model güncellemeleri için yayın kapılarının bir parçası olduğundan emin olun; regresyon bütçelerinin tanımlı olduğundan.

---

### C8.5 Kullanıcıya Özel Bellek İçin Kapsamın Uygulanması

Çapraz kiracı sızıntısı, RAG açısından en önemli risklerden biri olmaya devam ediyor: yanlış filtrelenmiş benzerlik sorguları başka bir müşterinin özel belgelerini ortaya çıkarabilir.

 #8.5.1    Seviye: 1    Rol: D/V
 Tüm geri alma sorgularının LLM istemine iletilmeden önce kiracı/kullanıcı kimliğine göre son filtrelendiğini doğrulayın.
 #8.5.2    Seviye: 1    Rol: D
 Koleksiyon adlarının veya isim alanı kimliklerinin kullanıcıya veya kiracıya göre tuzlandığından emin olun; böylece vektörler kapsamlar arasında çakışmaz.
 #8.5.3    Seviye: 2    Rol: D/V
 Yapılandırılabilir bir mesafe eşiğini aşan ancak çağıranın kapsamı dışında kalan benzerlik sonuçlarının reddedildiğini doğrulayın ve güvenlik uyarılarının tetiklenmesini sağlayın.
 #8.5.4    Seviye: 2    Rol: V
 Çok kiracılı stres testlerinin, kapsama dışı belgeleri elde etmeye çalışan adversarial sorgularını simüle ettiğini ve sıfır sızıntı gösterdiğini doğrulayın.
 #8.5.5    Seviye: 3    Rol: D/V
 Şifreleme anahtarlarının her kiracı için izole edildiğini doğrulayın; böylece fiziksel depolama paylaşılsa bile kriptografik izolasyon sağlanır.

---

### C8.6 Gelişmiş Bellek Sistemi Güvenliği

Epizodik, anlamsal ve çalışma belleğini kapsayan sofistike bellek mimarileri için belirli izolasyon ve doğrulama gereksinimlerine sahip güvenlik kontrolleri.

 #8.6.1    Seviye: 1    Rol: D/V
 Farklı bellek türlerinin (episodik, semantik, çalışma) izole güvenlik bağlamlarına sahip olduğundan, rol tabanlı erişim kontrolleri, ayrı şifreleme anahtarları ve her bellek türü için belgelenmiş erişim desenlerinin bulunup bulunmadığını doğrulayın.
 #8.6.2    Seviye: 2    Rol: D/V
 Bellek konsolidasyonu süreçlerinin, depolama öncesinde içerik temizleme, kaynak doğrulama ve bütünlük kontrolleri yoluyla kötü niyetli belleklerin enjeksiyonunu önlemek için güvenlik doğrulamasını içerdiğini doğrulayın.
 #8.6.3    Seviye: 2    Rol: D/V
 Bellek geri getirme sorgularının doğrulanıp temizlendiğini, sorgu desen analizi, erişim kontrolünün uygulanması ve sonuç filtrelemesi yoluyla yetkisiz bilgilerin çıkarılmasının engellendiğini teyit edin.
 #8.6.4    Seviye: 3    Rol: D/V
 Bellek silme mekanizmalarının hassas bilgileri güvenli bir şekilde sildiğini kriptografik silme garantileriyle doğrulayın; bu, anahtar silme, çok geçişli yazma veya doğrulama sertifikalarıyla donanım tabanlı güvenli silme kullanılarak sağlanır.
 #8.6.5    Seviye: 3    Rol: D/V
 Bellek sistemi bütünlüğünün, bellek içeriği normal dışı değişiklikler gösterdiğinde otomatik uyarılarla, checksum'lar ve denetim günlükleri aracılığıyla yetkisiz değişikliklere veya bozulmaya karşı sürekli izlendiğini doğrulayın.

---

### Kaynaklar

Vector database security: Pinecone – IronCore Labs
Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera
Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances
Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv
DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview
Art. 17 GDPR – Right to Erasure
Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai
PII Identification and Removal – NVIDIA NeMo Docs
De-identifying Sensitive Data – Google Cloud DLP
Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails
Think Your RAG Is Secure? Think Again – Medium
Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn
Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog

## 9 Otonom Orkestrasyon ve Ajanik Eylem Güvenliği

### Kontrol Amacı

Otonom veya çok ajanlı yapay zeka sistemlerinin yalnızca açıkça amaçlanan, kimlik doğrulanmış, denetlenebilir ve sınırlı maliyet ve risk eşiklerinin sınırları içinde eylemler gerçekleştirmesini sağlayın. Bu, şu tehditlere karşı korunmayı sağlar: Otonom Sistemlerin Ele Geçirilmesi, Araçların Kötüye Kullanımı, Ajan Döngüsü Tespiti, İletişimin Ele Geçirilmesi, Kimlik Sahteciliği, Sürü Manipülasyonu ve Niyet Manipülasyonu.

---

### 9.1 Ajan Görev-Planlama ve Özyineleme Bütçeleri

Özyinelemeli planları kısıtla ve yetkili işlemler için insan kontrol noktalarını zorunlu kıl.

 #9.1.1    Seviye: 1    Rol: D/V
 Maksimum özyineleme derinliği, genişlik, gerçek zaman süresi, tokenlar ve ajan başına yürütme maliyetinin merkezi olarak yapılandırıldığı ve sürüm kontrollü olduğunun doğrulanması.
 #9.1.2    Seviye: 1    Rol: D/V
 Yetkili veya geri alınamaz işlemlerin (örneğin kod değişiklikleri, finansal transferler) yürütülmeden önce izlenebilir bir kanal üzerinden açık insan onayının gerektiğini doğrulayın.
 #9.1.3    Seviye: 2    Rol: D
 Herhangi bir bütçe eşiği aşıldığında gerçek zamanlı kaynak izleyicilerinin devre kesici kesintisini tetiklediğini doğrulayın; bu, daha fazla görevin genişletilmesini durdurur.
 #9.1.4    Seviye: 2    Rol: D/V
 Devre kesici olaylarının adli inceleme için ajan kimliği, tetikleyici koşul ve yakalanmış plan durumu ile kaydedildiğini doğrulayın.
 #9.1.5    Seviye: 3    Rol: V
 Güvenlik testlerinin bütçe tükenmesi ve kontrolden çıkmış plan senaryolarını kapsadığından emin olun ve veri kaybı olmadan güvenli bir şekilde durdurulduğunu doğrulayın.
 #9.1.6    Seviye: 3    Rol: D
 Bütçe politikalarının policy-as-code olarak ifade edildiğini ve CI/CD'de uygulanarak yapılandırma sapmasının engellendiğini doğrulayın.

---

### 9.2 Araç Eklenti İzolaması

İzinsiz sistem erişimini veya kod çalıştırmayı önlemek için araç etkileşimlerini izole edin.

 #9.2.1    Seviye: 1    Rol: D/V
 Her araç/eklentiğin İşletim Sistemi (OS), konteyner veya WASM düzeyinde bir sandbox içinde çalıştığından emin olun; dosya sistemi, ağ ve sistem çağrısı politikalarının en az ayrıcalık ilkesine uygun şekilde uygulanması gerekir.
 #9.2.2    Seviye: 1    Rol: D/V
 Sandbox kaynak kotalarının (CPU, bellek, disk, ağ çıkışı) ve yürütme zaman aşımı sürelerinin uygulanıp kaydedildiğini doğrulayın.
 #9.2.3    Seviye: 2    Rol: D/V
 Araçların ikili dosyaları ve tanımlayıcılarının dijital olarak imzalandığını doğrulayın; imzalar yüklemeden önce doğrulanır.
 #9.2.4    Seviye: 2    Rol: V
 Sandbox telemetri akışlarının SIEM'e iletilmesini doğrulayın; anomalilerin (ör. çıkış bağlantı denemeleri) uyarılarının tetiklenmesini doğrulayın.
 #9.2.5    Seviye: 3    Rol: V
 Yüksek riskli eklentilerin üretim ortamına dağıtılmadan önce güvenlik incelemesi ve sızma testlerinden geçirildiğini doğrulayın.
 #9.2.6    Seviye: 3    Rol: D/V
 Sandbox kaçış girişimlerinin otomatik olarak engellendiğini ve ihlal eden eklentinin inceleme sürerken karantinaya alındığını doğrulayın.

---

### 9.3 Otonom Döngü ve Maliyet Sınırlandırması

Kontrolsüz ajanlar-arası özyinelemeyi ve maliyet patlamalarını tespit edin ve durdurun.

 #9.3.1    Seviye: 1    Rol: D/V
 Ajanslar arası çağrıların, çalışma zamanı tarafından azaltılan ve uygulanması gereken bir hop-limit veya TTL içerdiğini doğrulayın.
 #9.3.2    Seviye: 2    Rol: D
 Ajanların kendini çağırmayı veya döngüsel kalıpları tespit etmek için benzersiz bir çağrı-grafiği kimliğini sürdürdüğünü doğrulayın.
 #9.3.3    Seviye: 2    Rol: D/V
 Her istek zinciri için kümülatif hesaplama birimi sayaçlarının ve harcama sayaçlarının izlendiğini doğrulayın; sınır aşıldığında zincir durdurulur.
 #9.3.4    Seviye: 3    Rol: V
 Formal analiz veya model denetiminin ajan protokollerinde sınırsız özyinelemenin yokluğunu gösterdiğini doğrulayın.
 #9.3.5    Seviye: 3    Rol: D
 Loop-abort olaylarının uyarılar üretmesini ve sürekli iyileştirme metriklerini beslemesini doğrulayın.

---

### 9.4 Protokol Seviyesinde Kötüye Kullanım Önleme

Ajanlar ile harici sistemler arasındaki güvenli iletişim kanallarını, ele geçirilmesini veya manipülasyonu önlemek için güvence altına alın.

 #9.4.1    Seviye: 1    Rol: D/V
 Tüm ajan-araç ve ajan-ajan mesajlarının kimlik doğrulamasının yapıldığını (örneğin karşılıklı TLS veya JWT) ve uçtan uca şifreli olduğunu doğrulayın.
 #9.4.2    Seviye: 1    Rol: D
 Şemaların katı biçimde doğrulandığını doğrulayın; bilinmeyen alanlar veya hatalı biçimlendirilmiş iletiler reddedilir.
 #9.4.3    Seviye: 2    Rol: D/V
 Bütünlük kontrollerinin (MAC'ler veya dijital imzalar) tüm mesaj yükünü, araç parametreleri dahil olmak üzere, kapsadığını doğrulayın.
 #9.4.4    Seviye: 2    Rol: D
 Protokol katmanında yeniden oynatma korumasının (nonce'lar veya zaman damgası pencereleri) uygulanmış olduğundan emin olun.
 #9.4.5    Seviye: 3    Rol: V
 Protokol uygulamalarının enjeksiyon veya deserileştirme hataları için fuzzing ve statik analizden geçirildiğini doğrulayın.

---

### 9.5 Ajan Kimliği ve Tahrifat Kanıtı

Eylemler atfedilebilir olmalı ve değişiklikler tespit edilebilir olmalıdır.

 #9.5.1    Seviye: 1    Rol: D/V
 Her bir ajan örneğinin benzersiz bir kriptografik kimliğe sahip olduğunu doğrulayın (anahtar çifti veya donanım tabanlı kimlik bilgisi).
 #9.5.2    Seviye: 2    Rol: D/V
 Tüm ajan eylemlerinin imzalanıp zaman damgası alındığını doğrulayın; günlükler reddedilemezlik için imzayı içermelidir.
 #9.5.3    Seviye: 2    Rol: V
 Tamper-evident günlüklerin yalnızca eklenebilir veya bir kez yazılabilir bir ortamda saklandığından emin olun.
 #9.5.4    Seviye: 3    Rol: D
 Kimlik anahtarlarının belirlenen bir takvime göre ve ihlal göstergelerinde rotasyona uğradığını doğrulayın.
 #9.5.5    Seviye: 3    Rol: D/V
 Kimlik sahteciliği veya anahtar çakışması girişimlerinin, etkilenen ajanın derhal karantinaya alınmasını tetiklediğini doğrulayın.

---

### 9.6 Çok-Ajanlı Sürü Risk Azaltma

İzolasyon ve biçimsel güvenlik modellemesi yoluyla kolektif-davranış tehlikelerini azaltın.

 #9.6.1    Seviye: 1    Rol: D/V
 Farklı güvenlik alanlarında çalışan ajanların izole çalışma zamanı sandbox'larında veya ağ segmentlerinde yürütüldüğünden emin olun.
 #9.6.2    Seviye: 3    Rol: V
 Dağıtımdan önce sürü davranışlarının modellenip yaşamsallık ve güvenlik açısından resmen doğrulandığından emin olun.
 #9.6.3    Seviye: 3    Rol: D
 Çalışma zamanı izleyicilerinin ortaya çıkan güvenli olmayan desenleri (ör. salınımlar, kilitlenmeler) tespit ettiğini ve düzeltici önlemleri başlatacağını doğrulayın.

---

### 9.7 Kullanıcı ve Araç Kimlik Doğrulama / Yetkilendirme

Her ajan tarafından tetiklenen her eylem için sağlam erişim kontrolleri uygulayın.

 #9.7.1    Seviye: 1    Rol: D/V
 Ajanların alt sistemlere karşı birinci sınıf prensipler olarak kimlik doğrulaması yaptığını doğrulayın; son kullanıcı kimlik bilgilerinin asla yeniden kullanılmadığını doğrulayın.
 #9.7.2    Seviye: 2    Rol: D
 İnce ayrıntılı yetkilendirme politikalarının bir ajanın hangi araçları çağırabileceğini ve hangi parametreleri sunabileceğini kısıtladığını doğrulayın.
 #9.7.3    Seviye: 2    Rol: V
 Yetki kontrollerinin her çağrıda yeniden değerlendirildiğini (sürekli yetkilendirme) doğrulayın; yalnızca oturum başlangıcında değil.
 #9.7.4    Seviye: 3    Rol: D
 Devredilen yetkilerin otomatik olarak süresinin dolduğunu ve zaman aşımı veya kapsam değişikliği sonrasında yeniden onay gerektirdiğini doğrulayın.

---

### 9.8 Ajanlar Arası İletişim Güvenliği

Tüm ajanlar-arası mesajları şifreleyin ve bütünlüklerini koruyun; böylece dinlemeyi ve müdahaleyi engelleyin.

 #9.8.1    Seviye: 1    Rol: D/V
 Agent kanalları için karşılıklı kimlik doğrulamanın ve mükemmel ileriye dönük gizlilik içeren şifrelemenin (örn. TLS 1.3) zorunlu olduğunun doğrulanması gerekir.
 #9.8.2    Seviye: 1    Rol: D
 İşleme öncesinde mesaj bütünlüğünün ve kaynağının doğrulandığından emin olun; doğrulama başarısız olduğunda uyarılar tetiklenir ve mesaj reddedilir.
 #9.8.3    Seviye: 2    Rol: D/V
 İletişim meta verisinin (zaman damgaları, sıra numaraları) adli bilişim yeniden yapılandırmasını desteklemek amacıyla kaydedildiğini doğrulayın.
 #9.8.4    Seviye: 3    Rol: V
 Protokol durum makinelerinin güvenli olmayan durumlara sürüklenemeyeceğini, formal doğrulama veya model denetimi ile doğrulandığını teyit edin.

---

### 9.9 Niyet Doğrulaması ve Kısıtlamaların Uygulanması

Ajanın eylemlerinin kullanıcının beyan ettiği amacı ve sistem kısıtlarıyla uyumlu olduğunu doğrulayın.

 #9.9.1    Seviye: 1    Rol: D
 Ön yürütme kısıtlama çözücülerinin önerilen eylemleri sert kodlanmış güvenlik ve politika kurallarına göre kontrol ettiğini doğrulayın.
 #9.9.2    Seviye: 2    Rol: D/V
 Yüksek etkiye sahip işlemlerin (finansal, yıkıcı, gizlilik açısından hassas) başlatan kullanıcıdan açık niyet teyidi gerektirdiğini doğrulayın.
 #9.9.3    Seviye: 2    Rol: V
 Tamamlanan eylemlerin amaçlanan etkileri elde ettiğini ve yan etkilerin olmadığını doğrulayan son durum koşullarını kontrol edin; tutarsızlıklar geri alma işlemini tetikler.
 #9.9.4    Seviye: 3    Rol: V
 Ajan planlarının tüm açıklanan kısıtlamaları karşıladığını gösteren formal yöntemler (ör. model kontrolü, teorem ispatı) veya özellik tabanlı testler ile doğrulayın.
 #9.9.5    Seviye: 3    Rol: D
 Intent-mismatch veya constraint-violation olaylarının continuous-improvement döngülerini ve threat-intel paylaşımını beslediğini doğrulayın.

---

### 9.10 Ajan akıl yürütme stratejisi güvenlik

ReAct, Chain-of-Thought ve Tree-of-Thoughts yaklaşımlarını içeren farklı akıl yürütme stratejilerinin güvenli seçimi ve uygulanması.

 #9.10.1    Seviye: 1    Rol: D/V
 Akıl yürütme stratejisi seçiminin deterministik kriterlere dayandığını doğrulayın; girdi karmaşıklığı, görev türü ve güvenlik bağlamı dahil, aynı güvenlik bağlamında aynı girdiler aynı strateji seçimlerini üretir.
 #9.10.2    Seviye: 1    Rol: D/V
 Her bir muhakeme stratejisinin (ReAct, Chain-of-Thought, Tree-of-Thoughts) kendi bilişsel yaklaşımına özgü girdi doğrulama, çıktı temizleme ve çalışma süresi sınırlarına sahip olduğundan emin olun.
 #9.10.3    Seviye: 2    Rol: D/V
 Denetim izi yeniden oluşturma amacıyla, akıl yürütme stratejisi geçişlerinin tam bağlamla kaydedildiğini doğrulayın; bu bağlam girdi özelliklerini, seçim kriteri değerlerini ve yürütme meta verisini içerir.
 #9.10.4    Seviye: 2    Rol: D/V
 Düşünce Ağacı akıl yürütmesinin, politika ihlallerinin, kaynak sınırlarının veya güvenlik sınırlarının tespit edildiği durumlarda keşfi sonlandıran dal budama mekanizmalarını içerdiğini doğrulayın.
 #9.10.5    Seviye: 2    Rol: D/V
 ReAct (Reason-Act-Observe) döngülerinin her aşamada doğrulama noktalarını içerdiğini doğrulayın: akıl yürütme adımı doğrulaması, eylem yetkilendirmesi ve gözlem sanitizasyonunun ilerlemeden önce yapılması.
 #9.10.6    Seviye: 3    Rol: D/V
 Çalıştırma süresi, kaynak kullanımı ve çıktı kalitesi gibi akıl yürütme stratejisinin performans ölçütlerinin yapılandırılmış eşiklerin ötesine çıktığında otomatik uyarılarla izlendiğini doğrulayın.
 #9.10.7    Seviye: 3    Rol: D/V
 Birden çok stratejiyi birleştiren hibrit akıl yürütme yaklaşımlarının, tüm bileşen stratejilerinin giriş doğrulamasını ve çıktı kısıtlamalarını koruduğunu ve hiçbir güvenlik kontrolünü atlatmadığını doğrulayın.
 #9.10.8    Seviye: 3    Rol: D/V
 Akıl yürütme stratejisi güvenlik testlerinin bozuk girdilerle fuzzing içerdiğini, strateji değişimini zorlamak için tasarlanmış adversarial promptlar içerdiğini ve her bir bilişsel yaklaşım için sınır durum testi içerdiğini doğrulayın.

---

### 9.11 Ajan Yaşam Döngüsü Durum Yönetimi ve Güvenliği

Güvenli ajan başlatma, durum geçişleri ve sonlandırma, kriptografik denetim izleri ve tanımlanmış kurtarma prosedürleriyle.

 #9.11.1    Seviye: 1    Rol: D/V
 Ajının başlatılmasının, donanım destekli kimlik bilgileriyle kriptografik kimliğin oluşturulmasını ve ajan kimliği, zaman damgası, yapılandırma hash değeri ile başlatma parametrelerini içeren değiştirilemez başlangıç denetim günlüklerini kapsamasını doğrulayın.
 #9.11.2    Seviye: 2    Rol: D/V
 Ajanın durum geçişlerinin kriptografik olarak imzalandığını, zaman damgası ile kaydedildiğini ve tetikleyici olaylar, önceki durum hash değeri, yeni durum hash değeri ve gerçekleştirilen güvenlik doğrulamaları dahil olmak üzere tam bağlamla birlikte loglandığını doğrulayın.
 #9.11.3    Seviye: 2    Rol: D/V
 Ajan kapatma prosedürlerinin kriptografik silme veya çok geçişli üzerine yazma kullanılarak güvenli bellek temizlemesini içerdiğini, kimlik bilgisi iptalinin sertifika otoritesine bildirimle gerçekleştirilmesini ve tahrifata karşı kanıtlı sonlandırma sertifikalarının üretilmesini doğrulayın.
 #9.11.4    Seviye: 3    Rol: D/V
 Ajan kurtarma mekanizmalarının durum bütünlüğünü kriptografik özetler (SHA-256 en az) kullanarak doğruladığını ve bozulma tespit edildiğinde otomatik uyarılar ve manuel onay gereksinimleriyle bilinen güvenli durumlara geri dönmesini sağladığını doğrulayın.
 #9.11.5    Seviye: 3    Rol: D/V
 Ajana özgü AES-256 anahtarlarıyla hassas durum verilerini şifreleyen ajanın kalıcılık mekanizmalarını doğrulayın ve yapılandırılabilir zaman çizelgelerinde (maksimum 90 gün) güvenli anahtar rotasyonunu ve sıfır kesintiyle dağıtımı uygulayın.

---

### 9.12 Araç Entegrasyonu Güvenlik Çerçevesi

Tanımlanmış risk değerlendirme ve onay süreçleriyle dinamik araç yükleme, çalıştırma ve sonuç doğrulaması için güvenlik kontrolleri.

 #9.12.1    Seviye: 1    Rol: D/V
 Araç tanımlayıcılarının güvenlik meta verilerini içerdiğinden emin olun; bu meta verileri, gerekli ayrıcalıkları (okuma/yazma/çalıştırma), risk düzeylerini (düşük/orta/yüksek), kaynak sınırlarını (CPU, bellek, ağ) ve araç manifestolarında belgelenen doğrulama gereksinimlerini belirtir.
 #9.12.2    Seviye: 1    Rol: D/V
 Araç yürütme sonuçlarının beklenen şemalara (JSON Şeması, XML Şeması) ve güvenlik politikalarına (çıktı arındırma, veri sınıflandırması) uygun olduğunun doğrulandığından emin olun ve entegrasyondan önce zaman aşımı sınırları ile hata işleme prosedürleriyle bu doğrulamanın yapıldığını teyit edin.
 #9.12.3    Seviye: 2    Rol: D/V
 Araç etkileşim günlüklerinin güvenlik bağlamını ayrıntılı olarak içerdiğini doğrulayın: ayrıcalık kullanımı, veri erişim desenleri, yürütme süresi, kaynak tüketimi ve sonuç kodları gibi öğelerin SIEM entegrasyonu için yapılandırılmış günlüklerle kaydedildiğini sağlayın.
 #9.12.4    Seviye: 2    Rol: D/V
 Dinamik araç yükleme mekanizmalarının dijital imzaları PKI altyapısını kullanarak doğruladığından emin olun ve çalıştırmadan önce sandbox izolasyonu ile izin doğrulamasını içeren güvenli yükleme protokollerini uygulayın.
 #9.12.5    Seviye: 3    Rol: D/V
 Yeni sürümler için zorunlu onay kapılarıyla otomatik olarak tetiklenen araç güvenlik değerlendirmelerinin, statik analiz, dinamik testler ve güvenlik ekibi incelemesi dahil olmak üzere belgelendirilmiş onay kriterleri ve SLA gereksinimleriyle birlikte tetiklenmesini doğrulayın.

---

#### Kaynaklar

MITRE ATLAS tactics ML09
Circuit-breaker research for AI agents — Zou et al., 2024
Trend Micro analysis of sandbox escapes in AI agents — Park, 2025
Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025
Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025
Rapid7 fundamentals on spoofing attack prevention — 2024
Imperial College verification of swarm systems — Lomuscio et al.
NIST AI Risk Management Framework 1.0, 2023
WIRED security briefing on encryption best practices, 2024
OWASP Top 10 for LLM Applications, 2025
Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS
[How Is LLM Reasoning Distracted by Irrelevant Context?
An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
Large Language Model Sentinel: LLM Agent for Adversarial Purification
Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents

## 10 Saldırılara Karşı Dayanıklılık & Gizlilik Koruması

### Kontrol Amacı

AI modellerinin kaçınma, çıkarım, veri çıkarma veya zehirleme saldırılarına karşı güvenilir, mahremiyeti koruyan ve kötüye kullanıma karşı dayanıklı kalmasını sağlayın.

---

### 10.1 Model Uyum ve Güvenlik

Zararlı veya politika ihlali içeren çıktılara karşı koruma sağlayın.

 #10.1.1    Seviye: 1    Rol: D/V
 Bir uyum test kümesinin (kırmızı takım istemleri, jailbreak tetkikleri, yasak içerik) versiyon kontrollü olduğunu ve her model sürümü yayımlandığında çalıştırıldığını doğrulayın.
 #10.1.2    Seviye: 1    Rol: D
 Reddetme ve güvenli tamamlama için belirlenen kısıtlayıcı önlemlerin uygulanıp uygulanmadığını doğrulayın.
 #10.1.3    Seviye: 2    Rol: D/V
 Otomatik bir değerlendiricinin zararlı içerik oranını ölçtüğünü ve belirli bir eşik değerinin ötesindeki gerilemeleri işaretlediğini doğrulayın.
 #10.1.4    Seviye: 2    Rol: D
 counter-jailbreak eğitiminin belgelendiğini ve tekrarlanabilir olduğunu doğrulayın.
 #10.1.5    Seviye: 3    Rol: V
 Resmi politika uygunluğu kanıtlarının veya sertifikalı izlemenin kritik alanları kapsadığını doğrulayın.

---

### 10.2 Saldırgan-Örnek Sertleştirme

Manipüle edilmiş girdilere karşı dayanıklılığı artırın. Sağlam adversarial eğitimi ve kıyaslama puanlaması şu anda en iyi uygulamalardır.

 #10.2.1    Seviye: 1    Rol: D
 Projelerin depolarında tekrarlanabilir tohumlara sahip adversarial eğitim yapılandırmalarının bulunduğunu doğrulayın.
 #10.2.2    Seviye: 2    Rol: D/V
 Kötü niyetli örnek tespitinin üretim hatlarında engelleyici uyarılar tetiklediğini doğrulayın.
 #10.2.4    Seviye: 3    Rol: V
 Sertifikalı-sağlamlık kanıtlarının veya aralık-sınırlı sertifikaların en üstteki kritik sınıfları en azından kapsadığını doğrulayın.
 #10.2.5    Seviye: 3    Rol: V
 Regresyon testlerinin ölçülebilir dayanıklılık kaybı olmadığını doğrulamak için adaptif saldırılar kullandığını doğrulayın.

---

### 10.3 Üyelik-Çıkarımı Saldırısına Karşı Önlemler

Bir kaydın eğitim verilerinde yer alıp almadığını belirleme yeteneğini sınırlayın. Farklılaştırmalı gizlilik ve güven-skoru maskeleme, bilinen en etkili savunmalar olarak kalmaya devam ediyor.

 #10.3.1    Seviye: 1    Rol: D
 Sorgu başına entropi regularizasyonunun veya sıcaklık ölçeklendirmesinin aşırı güvenli tahminleri azalttığını doğrulayın.
 #10.3.2    Seviye: 2    Rol: D
 Eğitimin, hassas veri kümeleri için ε-sınırlandırılmış diferansiyel gizlilikle optimizasyon kullandığını doğrulayın.
 #10.3.3    Seviye: 2    Rol: V
 Saldırı simülasyonlarının (gölge-modeli veya kara kutu) ayrılmış veriler üzerinde AUC'nin 0.60'a eşit veya daha az olduğunu doğrulayın.

---

### 10.4 Model-İnversiyon Direnci

Gizli özniteliklerin yeniden türetilmesini engelleyin. Son araştırmalar çıktı kırpma ve DP güvencelerini pratik savunmalar olarak vurguluyor.

 #10.4.1    Seviye: 1    Rol: D
 Hassas öznitelikler asla doğrudan çıktı olarak verilmemelidir; gerektiğinde, bucket'lar veya tek yönlü dönüşümler kullanın.
 #10.4.2    Seviye: 1    Rol: D/V
 Aynı kullanıcı kimliğinden gelen yinelenen uyarlanabilir sorguların, sorgu oranı sınırları tarafından kısıtlandığını doğrulayın.
 #10.4.3    Seviye: 2    Rol: D
 Modelin gizlilik korumalı gürültüyle eğitildiğini doğrulayın.

---

### 10.5 Model-Çıkarımına Karşı Savunma

Yetkisiz klonlamayı tespit edin ve caydırın. Filigranlama ve sorgu desenleri analizi önerilir.

 #10.5.1    Seviye: 1    Rol: D
 İnferans geçitlerinin, modelin ezberleme eşiğine göre ayarlanmış küresel ve API anahtarına özgü istek hız sınırlarını uyguladığını doğrulayın.
 #10.5.2    Seviye: 2    Rol: D/V
 Sorgu-entropisi ve girdi-çoğulluk istatistiklerinin otomatik çıkarım dedektörünü beslediğini doğrulayın.
 #10.5.3    Seviye: 2    Rol: V
 Zayıf veya olasılıksal su işaretlerinin, şüpheli bir klon karşısında p < 0.01 ile kanıtlanabileceğini doğrulayın.
 #10.5.4    Seviye: 3    Rol: D
 Filigran anahtarlarının ve tetikleyici setlerin donanım güvenlik modülünde saklandığını ve her yıl yenilendiğini doğrulayın.
 #10.5.5    Seviye: 3    Rol: V
 Extraction-alert olaylarının zararlı sorguları içerdiğini ve olay müdahale senaryolarıyla entegre edildiğini doğrulayın.

---

### 10.6 Çıkarım Sırasında Zehirli-Veri Tespiti

Arka kapılı veya zehirlenmiş girdileri tespit edin ve etkisiz hale getirin.

 #10.6.1    Seviye: 1    Rol: D
 Girdilerin model çıkarımı öncesinde bir anomali dedektöründen geçtiğini doğrulayın (örn. STRIP, tutarlılık puanlaması).
 #10.6.2    Seviye: 1    Rol: V
 Algılayıcı eşiklerinin temiz/zehirlenmiş doğrulama setlerinde ayarlandığını doğrulayın; böylece %5'ten az yanlış pozitif elde edin.
 #10.6.3    Seviye: 2    Rol: D
 Zehirli olarak işaretlenen girdilerin yumuşak engellemeyi ve insan inceleme iş akışlarını tetiklediğini doğrulayın.
 #10.6.4    Seviye: 2    Rol: V
 Dedektörlerin uyarlanabilir ve tetikleyicisiz arka kapı saldırılarıyla stres testine tabi tutulduğunu doğrulayın.
 #10.6.5    Seviye: 3    Rol: D
 Tespit etkililiği metriklerinin kaydedildiğini ve güncel tehdit istihbaratı ile periyodik olarak yeniden değerlendirildiğini doğrulayın.

---

### 10.7 Dinamik Güvenlik Politikası Uyarlaması

Tehdit istihbaratı ve davranışsal analize dayalı olarak gerçek zamanlı güvenlik politikası güncellemeleri.

 #10.7.1    Seviye: 1    Rol: D/V
 Güvenlik politikalarının ajan yeniden başlatılmadan dinamik olarak güncellenebildiğini ve politika sürüm bütünlüğünün korunduğunu doğrulayın.
 #10.7.2    Seviye: 2    Rol: D/V
 Politika güncellemelerinin yetkili güvenlik personeli tarafından kriptografik olarak imzalandığını ve uygulanmadan önce doğrulandığını doğrulayın.
 #10.7.3    Seviye: 2    Rol: D/V
 Dinamik politika değişikliklerinin gerekçe, onay zincirleri ve geri alma prosedürleri dahil olmak üzere tam denetim iziyle kaydedildiğini doğrulayın.
 #10.7.4    Seviye: 3    Rol: D/V
 Adaptif güvenlik mekanizmalarının tehdit tespitinin hassasiyetini risk bağlamına ve davranışsal kalıplara göre ayarladığını doğrulayın.
 #10.7.5    Seviye: 3    Rol: D/V
 Politika uyarlama kararlarının açıklanabilir olduğundan emin olun ve güvenlik ekibinin incelemesi için kanıt izleri ekleyin.

---

### 10.8 Yansıma-Tabanlı Güvenlik Analizi

Ajanın öz-yansıtması ve metakognitif analizi yoluyla güvenlik doğrulaması.

 #10.8.1    Seviye: 1    Rol: D/V
 Ajan yansıtma mekanizmalarının kararlar ve eylemler için güvenlik odaklı öz-değerlendirme içerdiğini doğrulayın.
 #10.8.2    Seviye: 2    Rol: D/V
 Yansıma çıktılarının, öz-değerlendirme mekanizmalarının adversarial girdiler tarafından manipüle edilmesini önlemek amacıyla doğrulanmış olduğundan emin olun.
 #10.8.3    Seviye: 2    Rol: D/V
 Meta-bilişsel güvenlik analizinin ajan akıl yürütme süreçlerinde olası önyargı, manipülasyon veya güvenliğin zedelenmesini tespit ettiğini doğrulayın.
 #10.8.4    Seviye: 3    Rol: D/V
 Refleksiyon tabanlı güvenlik uyarılarının geliştirilmiş izleme ve potansiyel insan müdahalesi iş akışlarını tetiklediğini doğrulayın.
 #10.8.5    Seviye: 3    Rol: D/V
 Güvenlik geri bildirimlerinden sürekli öğrenmenin tehdit tespitini iyileştirdiğini ve meşru işlevselliği bozmadığını doğrulayın.

---

### 10.9 Evrim ve Öz-Gelişim Güvenliği

Kendi kendini değiştirebilen ve evrimleşebilen ajan sistemleri için güvenlik kontrolleri.

 #10.9.1    Seviye: 1    Rol: D/V
 Kendini değiştirme yeteneklerinin belirlenmiş güvenli alanlarla ve resmî doğrulama sınırlarıyla sınırlı olduğunu doğrulayın.
 #10.9.2    Seviye: 2    Rol: D/V
 Gelişim önerilerinin uygulanmadan önce güvenlik etkisi değerlendirmesinden geçtiğini doğrulayın.
 #10.9.3    Seviye: 2    Rol: D/V
 Kendi kendini geliştirme mekanizmalarının bütünlük doğrulamasıyla geri alma yeteneklerini içerdiğini doğrulayın.
 #10.9.4    Seviye: 3    Rol: D/V
 Meta-öğrenme güvenliğinin iyileştirme algoritmalarını adversarial manipülasyonundan koruduğunu doğrulayın.
 #10.9.5    Seviye: 3    Rol: D/V
 Özyinelemeli kendi kendine geliştirme işleminin biçimsel güvenlik kısıtlarıyla sınırlı olduğunu, yakınsama için matematiksel kanıtlarla doğrulayın.

---

#### Kaynaklar

MITRE ATLAS adversary tactics for ML
NIST AI Risk Management Framework 1.0, 2023
OWASP Top 10 for LLM Applications, 2025
Adversarial Training: A Survey — Zhao et al., 2024
RobustBench adversarial-robustness benchmark
Membership-Inference & Model-Inversion Risk Survey, 2025
PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023
Model-Inversion Attacks & Defenses Survey — AI Review, 2025
Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024
Fragile Model Watermarking Survey — 2025
Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025
BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024

## 11 Gizlilik Koruması ve Kişisel Veri Yönetimi

### Kontrol Amacı

Yapay zeka yaşam döngüsü boyunca—toplama, eğitim, çıkarım ve olay müdahalesi—sıkı gizlilik güvencelerini sürdürün; böylece kişisel veriler yalnızca açık rıza ile, gereken asgari kapsamla, kanıtlanabilir silme ile ve resmi gizlilik garantileriyle işlenir.

---

### 11.1 Anonimleştirme ve Veri Minimizasyonu

 #11.1.1    Seviye: 1    Rol: D/V
 Doğrudan ve yarı tanımlayıcıların kaldırıldığından ve hash'lenmiş olduğundan emin olun.
 #11.1.2    Seviye: 2    Rol: D/V
 Otomatik denetimlerin k-anonimlik ve l-çeşitliliği ölçtüğünü doğrulayın ve politikaya göre belirlenen eşiklerin altına düştüğünde uyarı verin.
 #11.1.3    Seviye: 2    Rol: V
 Modelin özellik-önemi raporlarının ε = 0.01 karşılıklı bilgi değerinin ötesinde herhangi bir kimlik sızıntısını kanıtlamadığını doğrulayın.
 #11.1.4    Seviye: 3    Rol: V
 Resmi kanıtlar veya sentetik veri sertifikasyonunun yeniden kimliklendirme riskinin ≤ 0.05 olduğunu gösterdiğini doğrulayın.

---

### 11.2 Unutulma Hakkı ve Silme Uygulaması

 #11.2.1    Seviye: 1    Rol: D/V
 Veri sahibi silme taleplerinin ham veri kümelerine, kontrol noktalarına, gömme temsillerine, günlük kayıtlara ve yedeklere 30 günden daha kısa SLA'lar kapsamında iletilmesini doğrulayın.
 #11.2.2    Seviye: 2    Rol: D
 ‘machine-unlearning’ rutinlerinin, sertifikalı unlearning algoritmaları kullanılarak fiziksel olarak yeniden eğitilmesini veya kaldırmayı yaklaşık olarak gerçekleştirip gerçekleştirmediğini doğrulayın.
 #11.2.3    Seviye: 2    Rol: V
 Unlearning işlemi sonrası gölge-model değerlendirmesinin unutulan kayıtların çıktılarına %1'inden daha azına etki ettiğini doğrulayın.
 #11.2.4    Seviye: 3    Rol: V
 Silme olaylarının değiştirilemez biçimde kaydedildiğini ve regülatörler için denetlenebilir olduğunu doğrulayın.

---

### 11.3 Diferansiyel-Gizlilik Önlemleri

 #11.3.1    Seviye: 2    Rol: D/V
 Kümülatif ε politika eşiklerini aştığında mahremiyet kaybı muhasebe panolarının uyarı verdiğini doğrulayın.
 #11.3.2    Seviye: 2    Rol: V
 Kara kutu gizlilik denetimlerinin ε̂ değerinin beyan edilen değerin ±%10'luk aralığında tahmin edildiğini doğrulayın.
 #11.3.3    Seviye: 3    Rol: V
 Resmi kanıtların tüm eğitim sonrası ince ayarlamaları ve gömme vektörlerini kapsadığını doğrulayın.

---

### 11.4 Amaç-Sınırlaması & Kapsam-Kayması Koruması

 #11.4.1    Seviye: 1    Rol: D
 Her veri kümesi ve her model kontrol noktası, orijinal rızaya uygun olarak makine okunabilir bir amaç etiketi taşıdığından emin olun.
 #11.4.2    Seviye: 1    Rol: D/V
 Çalışma zamanı izleme mekanizmalarının, beyan edilen amaçla tutarsız sorguları tespit ettiğini ve yumuşak reddetmeyi tetiklediğini doğrulayın.
 #11.4.3    Seviye: 3    Rol: D
 Policy-as-code geçitlerinin DPIA incelemesi olmaksızın modellerin yeni alanlara yeniden konuşlandırılmasını engellediğini doğrulayın.
 #11.4.4    Seviye: 3    Rol: V
 Resmi izlenebilirlik kanıtlarının, her bir kişisel verinin yaşam döngüsünün rızaya uygun kapsam içinde kaldığını gösterdiğini doğrulayın.

---

### 11.5 Rıza Yönetimi & Yasal-Dayanak Takibi

 #11.5.1    Seviye: 1    Rol: D/V
 Bir Rıza Yönetim Platformu (CMP) veri öznesi başına rıza durumunu, amacını ve saklama süresini kaydettiğini doğrulayın.
 #11.5.2    Seviye: 2    Rol: D
 API'lerin rıza belirteçlerini sunduğunu doğrulayın; modeller çıkarım öncesinde belirteç kapsamını doğrulamalıdır.
 #11.5.3    Seviye: 2    Rol: D/V
 Reddedilmiş veya geri çekilmiş rızanın işlem hatlarını 24 saat içinde durdurduğunu doğrulayın.

---

### 11.6 Gizlilik Kontrolleri ile Dağıtık Öğrenme

 #11.6.1    Seviye: 1    Rol: D
 İstemci güncellemelerinin birleştirme işleminden önce yerel diferansiyel gizlilik gürültüsünün eklenmesini kullandığını doğrulayın.
 #11.6.2    Seviye: 2    Rol: D/V
 Eğitim metriklerinin diferansiyel gizlilik sağladığını ve tek bir istemcinin kaybını asla ifşa etmediğini doğrulayın.
 #11.6.3    Seviye: 2    Rol: V
 Zararlı veriye karşı dayanıklı agregasyonun (örneğin Krum/Trimmed-Mean) etkinleştirildiğini doğrulayın.
 #11.6.4    Seviye: 3    Rol: V
 Formel kanıtların toplam ε bütçesini, 5'ten az yarar kaybı ile gösterdiğini doğrulayın.

---

#### Kaynaklar

GDPR & AI Compliance Best Practices
EU Parliament Study on GDPR & AI, 2020
ISO 31700-1:2023 — Privacy by Design for Consumer Products
NIST Privacy Framework 1.1 (2025 Draft)
Machine Unlearning: Right-to-Be-Forgotten Techniques
A Survey of Machine Unlearning, 2024
Auditing DP-SGD — ArXiv 2024
DP-SGD Explained — PyTorch Blog
Purpose-Limitation for AI — IJLIT 2025
Data-Protection Considerations for AI — URM Consulting
Top Consent-Management Platforms, 2025
Secure Aggregation in DP Federated Learning — ArXiv 2024

## C12 İzleme, Günlükleme ve Anomali Tespiti

### Kontrol Amacı

Bu bölüm, modelin ve diğer yapay zeka bileşenlerinin ne gördüğünü, ne yaptığını ve ne döndürdüğünü gerçek zamanlı ve adli görünüm altında izlemenin gereksinimlerini sunar; tehditler tespit edilebilir, triage edilip bunlardan öğrenilebilir.

### C12.1 İstek ve Yanıt Günlüğü

 #12.1.1    Seviye: 1    Rol: D/V
 Tüm kullanıcı istemlerinin ve model yanıtlarının uygun meta verilerle kaydedildiğini doğrulayın (ör. zaman damgası, kullanıcı kimliği, oturum kimliği, model sürümü).
 #12.1.2    Seviye: 1    Rol: D/V
 Günlüklerin güvenli, erişim kontrollü depolama depolarında saklandığından emin olun ve uygun saklama politikaları ile yedekleme prosedürlerinin uygulanıp uygulanmadığını doğrulayın.
 #12.1.3    Seviye: 1    Rol: D/V
 Günlük depolama sistemlerinin dinlenme halinde ve iletim sırasında şifrelemeyi uyguladığını doğrulayın; bu, günlüklerde bulunan hassas bilgilerin korunmasını sağlar.
 #12.1.4    Seviye: 1    Rol: D/V
 Prompts ve çıktılardaki hassas verilerin günlüğe kaydedilmeden önce otomatik olarak kırpıldığı veya maskelediğini doğrulayın; PII, kimlik bilgileri ve özel bilgiler için yapılandırılabilir kırpma/maskeleme kuralları ile.
 #12.1.5    Seviye: 2    Rol: D/V
 Politika kararlarının ve güvenlik filtreleme işlemlerinin içerik moderasyon sistemlerinin denetlenmesi ve hata ayıklaması için yeterli ayrıntıyla kaydedildiğini doğrulayın.
 #12.1.6    Seviye: 2    Rol: D/V
 Günlük bütünlüğünün, örneğin kriptografik imzalar veya yalnızca yazılabilir depolama ile korunduğunu doğrulayın.

---

### C12.2 Kötüye Kullanım Tespiti ve Uyarı

 #12.2.1    Seviye: 1    Rol: D/V
 Sistemin, bilinen jailbreak kalıplarını, prompt enjeksiyonu girişimlerini ve adversarial girdileri imza tabanlı tespit kullanarak tespit ettiğini ve uyarı verdiğini doğrulayın.
 #12.2.2    Seviye: 1    Rol: D/V
 Sistemin mevcut Güvenlik Bilgi ve Olay Yönetimi (SIEM) platformlarıyla standart günlük formatları ve protokollerini kullanarak entegrasyon sağladığını doğrulayın.
 #12.2.3    Seviye: 2    Rol: D/V
 Zenginleştirilmiş güvenlik olaylarının Yapay Zeka'ya özgü bağlam içerdiğini doğrulayın; örneğin model tanımlayıcıları, güven skorları ve güvenlik filtresi kararları.
 #12.2.4    Seviye: 2    Rol: D/V
 Davranışsal anomali tespitinin olağandışı konuşma kalıplarını, aşırı yeniden deneme girişimlerini veya sistematik keşif davranışlarını belirlediğini doğrulayın.
 #12.2.5    Seviye: 2    Rol: D/V
 Potansiyel politika ihlallerinin veya saldırı girişimlerinin tespit edildiği durumlarda gerçek zamanlı uyarı mekanizmalarının güvenlik ekiplerini bilgilendirdiğini doğrulayın.
 #12.2.6    Seviye: 2    Rol: D/V
 Koordineli jailbreak girişimleri, prompt enjeksiyonu kampanyaları ve model çıkarımı saldırıları dahil olmak üzere yapay zekaya özgü tehdit desenlerini tespit etmek için özel kuralların dahil edildiğini doğrulayın.
 #12.2.7    Seviye: 3    Rol: D/V
 Otomatik olay müdahale iş akışlarının zarar görmüş modelleri izole edebildiğini, kötü niyetli kullanıcıları engelleyebildiğini ve kritik güvenlik olaylarını yükseltebildiğini doğrulayın.

---

### C12.3 Model Kayması Tespiti

 #12.3.1    Seviye: 1    Rol: D/V
 Sistemin, doğruluk oranı, güven skorları, gecikme süresi ve hata oranları gibi temel performans metriklerini model sürümleri ve zaman dilimleri boyunca izlediğini doğrulayın.
 #12.3.2    Seviye: 2    Rol: D/V
 Performans metrikleri önceden tanımlanmış bozulma eşiklerini aştığında veya temel referans değerlerinden belirgin şekilde sapması durumunda otomatik uyarıların tetiklendiğini doğrulayın.
 #12.3.3    Seviye: 2    Rol: D/V
 Halüsinasyon tespit monitörlerinin, model çıktılarında gerçeklere aykırı, tutarsız veya uydurma bilgiler içeren durumları tespit edip işaret ettiğini doğrulayın.

---

### C12.4 Performans ve Davranış Telemetri

 #12.4.1    Seviye: 1    Rol: D/V
 Operasyonel metriklerin, istek gecikmesi, token tüketimi, bellek kullanımı ve işlem hacmi dahil olmak üzere, sürekli olarak toplanıp izlenmesini doğrulayın.
 #12.4.2    Seviye: 1    Rol: D/V
 Başarı ve başarısızlık oranlarının, hata türlerinin ve kök nedenlerinin kategorize edilip izlendiğini doğrulayın.
 #12.4.3    Seviye: 2    Rol: D/V
 Kaynak kullanımını izlemenin GPU/CPU kullanımı, bellek tüketimi ve depolama gereksinimlerini kapsadığını ve eşik aşımlarında uyarı verdiğini doğrulayın.

---

### C12.5 Yapay Zeka Olay Müdahale Planlama ve Uygulama

 #12.5.1    Seviye: 1    Rol: D/V
 Olay müdahale planlarının özellikle yapay zeka ile ilgili güvenlik olaylarını, modelin ele geçirilmesi, veri zehirlenmesi ve adversarial saldırılar dahil olmak üzere kapsadığını doğrulayın.
 #12.5.2    Seviye: 2    Rol: D/V
 Olay müdahale ekiplerinin yapay zekâya özgü adli bilişim araçlarına ve bu araçları kullanma konusundaki uzmanlığa erişiminin olduğunu doğrulayın.
 #12.5.3    Seviye: 3    Rol: D/V
 Olay sonrası analizinin model yeniden eğitimi için hususları, güvenlik filtrelerinin güncellemelerini ve edinilen derslerin güvenlik kontrollerine entegrasyonunu içerdiğini doğrulayın.

---

### C12.5 AI Performans Bozulması Tespiti

Zaman içinde yapay zeka modelinin performansında ve kalitesinde gerilemenin izlenmesi ve tespit edilmesi.

 #12.5.1    Seviye: 1    Rol: D/V
 Modelin doğruluğu, kesinliği, duyarlılığı ve F1 skorlarının sürekli olarak izlenip temel eşik değerleriyle karşılaştırıldığından emin olun.
 #12.5.2    Seviye: 1    Rol: D/V
 Veri sürüklenmesi tespitinin, model performansını etkileyebilecek girdi dağılımı değişikliklerini izlediğini doğrulayın.
 #12.5.3    Seviye: 2    Rol: D/V
 Kavram sürüklenmesi tespitinin girdiler ile beklenen çıktılar arasındaki ilişkinin değişikliklerini belirlediğini doğrulayın.
 #12.5.4    Seviye: 2    Rol: D/V
 Performans düşüşünün otomatik uyarılar tetiklediğini ve modelin yeniden eğitilmesini veya değiştirme iş akışlarını başlattığını doğrulayın.
 #12.5.5    Seviye: 3    Rol: V
 Bozulma kök neden analizinin performans düşüşlerini veri değişiklikleri, altyapı sorunları veya dış etkenlerle ilişkilendirdiğini doğrulayın.

---

### C12.6 DAG Görselleştirme ve İş Akışı Güvenliği

İş akışı görselleştirme sistemlerini bilgi sızıntısı ve manipülasyon saldırılarından koruyun.

 #12.6.1    Seviye: 1    Rol: D/V
 DAG görselleştirme verilerinin saklama veya iletimden önce hassas bilgilerden arındırıldığını doğrulayın.
 #12.6.2    Seviye: 1    Rol: D/V
 İş akışı görselleştirme erişim kontrollerinin yalnızca yetkili kullanıcıların ajan karar yollarını ve akıl yürütme izlerini görüntüleyebilmesini sağladığını doğrulayın.
 #12.6.3    Seviye: 2    Rol: D/V
 DAG veri bütünlüğünün kriptografik imzalar ve müdahaleyi kanıtlayan depolama mekanizmalarıyla korunduğunu doğrulayın.
 #12.6.4    Seviye: 2    Rol: D/V
 İş akışı görselleştirme sistemlerinin, özenle tasarlanmış düğüm veya kenar verileri üzerinden enjeksiyon saldırılarını önlemek amacıyla giriş doğrulamasını uyguladığını doğrulayın.
 #12.6.5    Seviye: 3    Rol: D/V
 Gerçek zamanlı DAG güncellemelerinin hız sınırına tabi olduğundan ve görselleştirme sistemlerini DoS saldırılarına karşı korumak için doğrulandığından emin olun.

---

### C12.7 Proaktif Güvenlik Davranışlarının İzlenmesi

Güvenlik tehditlerinin tespiti ve proaktif ajan davranışı analizi yoluyla önlenmesi.

 #12.7.1    Seviye: 1    Rol: D/V
 Proaktif ajan davranışlarının yürütülmeden önce güvenlik açısından doğrulanmış olduğundan emin olun; risk değerlendirme entegrasyonu ile doğrulayın.
 #12.7.2    Seviye: 2    Rol: D/V
 Otonom inisiyatif tetikleyicilerinin güvenlik bağlamı değerlendirmesi ve tehdit ortamı değerlendirmesi içerdiğini doğrulayın.
 #12.7.3    Seviye: 2    Rol: D/V
 Proaktif davranış kalıplarının potansiyel güvenlik etkileri ve istenmeyen sonuçlar açısından analiz edildiğini doğrulayın.
 #12.7.4    Seviye: 3    Rol: D/V
 Güvenlik açısından kritik proaktif eylemlerin açık onay zincirleri ile denetim izleri gerektirdiğini doğrulayın.
 #12.7.5    Seviye: 3    Rol: D/V
 Davranışsal anomali tespitinin, proaktif ajan kalıplarındaki sapmaları tespit ettiğini ve bunların güvenlik ihlaline işaret edebileceğini doğrulayın.

---

### Kaynaklar

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 İnsan Gözetimi, Hesap Verebilirlik ve Yönetişim

### Kontrol Amacı

Bu bölüm, yapay zeka sistemlerinde insan denetimini sürdürmeye ve net hesap verebilirlik zincirlerinin kurulmasına ilişkin gereksinimleri sunar; bu gereksinimler, yapay zeka yaşam döngüsü boyunca açıklık, şeffaflık ve etik sorumluluk bilincinin sağlanmasını güvence altına alır.

---

### C13.1 Kill-Switch & Geçersiz Kılma Mekanizmaları

Güvensiz davranış gözlemlendiğinde yapay zeka sistemi için kapatma veya geri alma yollarını sağlayın.

 #13.1.1    Seviye: 1    Rol: D/V
 Yapay zeka modelinin çıkarımını ve çıktılarını derhal durdurmak için manuel bir acil durdurma mekanizmasının mevcut olduğunu doğrulayın.
 #13.1.2    Seviye: 1    Rol: D
 Override kontrollerinin yalnızca yetkili personelin erişimine açık olduğundan emin olun.
 #13.1.3    Seviye: 3    Rol: D/V
 Geri alma prosedürlerinin önceki model sürümlerine veya güvenli mod işlemlerine geri dönebileceğini doğrulayın.
 #13.1.4    Seviye: 3    Rol: V
 Override mekanizmalarının düzenli olarak test edildiğini doğrulayın.

---

### C13.2 İnsan Katılımlı Karar Noktaları

Belirlenen risk eşiklerini aştığında insan onayı gerekir.

 #13.2.1    Seviye: 1    Rol: D/V
 Yüksek riskli yapay zeka kararlarının icra edilmeden önce açık insan onayını gerektirdiğini doğrulayın.
 #13.2.2    Seviye: 1    Rol: D
 Risk eşiklerinin açıkça tanımlandığından emin olun ve bu eşikler otomatik olarak insan incelemesi iş akışlarını tetiklesin.
 #13.2.3    Seviye: 2    Rol: D
 Zamana duyarlı kararlar için gereken süreler içinde insan onayı alınamazsa yedek prosedürlerin mevcut olduğundan emin olun.
 #13.2.4    Seviye: 3    Rol: D/V
 Yükseltme prosedürlerinin, uygulanabilir ise, farklı karar türleri veya risk kategorileri için net yetki seviyelerini tanımladığını doğrulayın.

---

### C13.3 Sorumluluk Zinciri ve Denetlenebilirlik

Operatör eylemlerini ve model kararlarını kaydedin.

 #13.3.1    Seviye: 1    Rol: D/V
 Tüm yapay zeka sistemi kararlarının ve insan müdahalelerinin zaman damgaları, kullanıcı kimlikleri ve karar gerekçeleriyle kaydedildiğini doğrulayın.
 #13.3.2    Seviye: 2    Rol: D
 Denetim günlüklerinin değiştirilmez olduğunu doğrulayın ve bütünlük doğrulama mekanizmalarını dahil edin.

---

### C13.4 Açıklanabilir-Yapay Zeka Teknikleri

Yüzeysel Özelliklerin Önemi, Karşı-olgusal Açıklamalar ve Yerel Açıklamalar.

 #13.4.1    Seviye: 1    Rol: D/V
 AI sistemlerinin kararlarını insanlar tarafından okunabilir bir biçimde temel açıklamalarla sunmalarını doğrulayın.
 #13.4.2    Seviye: 2    Rol: V
 Açıklama kalitesinin insan değerlendirme çalışmaları ve metriklerle doğrulandığını doğrulayın.
 #13.4.3    Seviye: 3    Rol: D/V
 Kritik kararlar için öznitelik önem skorlarının veya atıf yöntemlerinin (SHAP, LIME, vb.) mevcut olduğundan emin olun.
 #13.4.4    Seviye: 3    Rol: V
 Kullanım vakasına ve alanına uygulanabilir ise, girdilerin çıktılarını değiştirmek için nasıl değiştirilebileceğini gösteren karşıt olgusal açıklamaları doğrulayın.

---

### C13.5 Model Kartları ve Kullanım Açıklamaları

Kullanım amacı, performans metrikleri ve etik hususlar için model kartlarını sürdürün.

 #13.5.1    Seviye: 1    Rol: D
 Model kartlarının amaçlanan kullanım durumlarını, sınırlamaları ve bilinen başarısızlık modlarını belgelediğini doğrulayın.
 #13.5.2    Seviye: 1    Rol: D/V
 Çeşitli ilgili kullanım senaryoları arasında performans metriklerinin açıklanmış olduğundan emin olun.
 #13.5.3    Seviye: 2    Rol: D
 Etik hususların, önyargı değerlendirmelerinin, adalet değerlendirmelerinin, eğitim verisi özelliklerinin ve bilinen eğitim verisi kısıtlamalarının belgelendiğini ve düzenli olarak güncellendiğini doğrulayın.
 #13.5.4    Seviye: 2    Rol: D/V
 Model kartlarının sürüm kontrolüne tabi olduğundan ve değişiklik takibiyle model yaşam döngüsü boyunca güncel tutulduğundan emin olun.

---

### C13.6 Belirsizlik Nicelleştirme

Yanıtlar içinde güven skorlarını veya entropi ölçütlerini iletin.

 #13.6.1    Seviye: 1    Rol: D
 AI sistemlerinin çıktılarıyla güven skorları veya belirsizlik ölçütleri sağlandığını doğrulayın.
 #13.6.2    Seviye: 2    Rol: D/V
 Belirsizlik eşiklerinin ilave insan incelemesini veya alternatif karar yollarını tetiklediğini doğrulayın.
 #13.6.3    Seviye: 2    Rol: V
 Belirsizlik nicelleştirme yöntemlerinin, gerçek değer verileriyle kalibre edildiğini ve doğrulandığını doğrulayın.
 #13.6.4    Seviye: 3    Rol: D/V
 Çok adımlı yapay zeka iş akışları boyunca belirsizlik yayılımının korunup korunmadığını doğrulayın.

---

### C13.7 Kullanıcıya Yönelik Şeffaflık Raporları

Olaylar, kavram kayması ve veri kullanımıyla ilgili periyodik açıklamalar sunun.

 #13.7.1    Seviye: 1    Rol: D/V
 Veri kullanım politikalarının ve kullanıcı onamı yönetim uygulamalarının paydaşlara açıkça iletildiğini doğrulayın.
 #13.7.2    Seviye: 2    Rol: D/V
 Yapay zeka etki değerlendirmelerinin yapıldığını ve sonuçların raporlamaya dahil edildiğini doğrulayın.
 #13.7.3    Seviye: 2    Rol: D/V
 Periyodik olarak yayımlanan şeffaflık raporlarının yapay zeka ile ilgili olayları ve operasyonel metrikleri makul düzeyde ayrıntılı olarak açıkladığını doğrulayın.

#### Kaynaklar

EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
ISO/IEC 42001:2023 — AI Management Systems Requirements
NIST AI Risk Management Framework 1.0
NIST SP 800-53 Revision 5 — Security and Privacy Controls
A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)
Model Cards for Model Reporting (Mitchell et al., 2018)
Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)
ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods
IEEE 7001-2021 — Transparency of Autonomous Systems
GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Ek A: Terimler Sözlüğü

This kapsamlı sözlük AISVS genelinde kullanılan temel yapay zeka (AI), makine öğrenmesi (ML) ve güvenlik terimlerinin tanımlarını sağlar; açıklık ve ortak anlayışın sağlanması amacıyla.

Adversarial Örnek: Bir girdi, yapay zeka modelinin hata yapmasına yol açmak için kasıtlı olarak tasarlanmıştır; genellikle insanlar tarafından algılanamayan ince pertürbasyonlar eklenir.
​
Adversarial Dayanıklılık – Yapay Zeka'da bu kavram, bir modelin performansını sürdürme ve kasıtlı olarak tasarlanmış, kötü niyetli girdiler tarafından kandırılmaya veya manipüle edilmeye karşı direnç gösterme yeteneğini ifade eder.
​
Ajan – Yapay zeka ajanları, kullanıcılar adına hedeflere ulaşmak ve görevleri yerine getirmek için yapay zekayı kullanan yazılım sistemleridir. Akıl yürütmeyi, planlamayı ve belleği gösterirler ve kararlar almak, öğrenmek ve uyum sağlamak için belirli bir özerklik düzeyine sahiptirler.
​
Ajansal Yapay Zeka: Hedeflere ulaşmak için bir dereceye kadar özerklikle çalışabilen ve genellikle insan müdahalesi olmadan kararlar alıp eylemler gerçekleştiren yapay zeka sistemleri.
​
Öznitelik Tabanlı Erişim Denetimi (ABAC): Yetkilendirme kararlarının, kullanıcı, kaynak, eylem ve ortam özniteliklerine dayalı olarak sorgu anında değerlendirildiği bir erişim kontrol paradigması.
​
Arka Kapı Saldırısı: Modelin belirli tetikleyicilere karşı belirli bir şekilde yanıt vermesi için eğitildiği, aksi halde normal davranan bir veri zehirleme saldırısı türüdür.
​
Yanlılık: Yapay zeka model çıktılarında bulunan sistematik hatalar, belirli gruplar için veya belirli bağlamlarda adil olmayan veya ayrımcı sonuçlara yol açabilir.
​
Önyargı Sömürüsü: Yapay zeka modellerindeki bilinen önyargılardan faydalanarak çıktıların veya sonuçların manipüle edilmesini amaçlayan bir saldırı tekniğidir.
​
Cedar: Yapay zeka sistemleri için ABAC'ın uygulanmasında kullanılan, ince ayrıntılı izinler için Amazon'un politika dili ve motoru.
​
Düşünce Zinciri: Nihai yanıtı üretmeden önce ara akıl yürütme adımları üreterek dil modellerinde akıl yürütmeyi geliştirmeye yönelik bir tekniktir.
​
Devre Kesiciler: Belirli risk eşiklerinin aşılması durumunda yapay zeka sistemi operasyonlarını otomatik olarak durduran mekanizmalar.
​
Veri Sızıntısı: Yapay zeka modelinin çıktıları veya davranışı yoluyla hassas bilgilerin istenmeyen ifşası.
​
Veri Zehirlenmesi: Eğitim verilerinin kasıtlı olarak bozulmasıyla model bütünlüğünün tehlikeye atılması, çoğunlukla arka kapılar kurmak veya performansı düşürmek amacıyla.
​
Farklılaştırılmış Gizlilik – Matematiksel olarak sıkı bir çerçeve, veri kümeleri hakkında istatistiksel bilgi yayımlarken bireylerin mahremiyetini korumayı sağlar. Bu, veri sahibinin grubun toplu desenlerini paylaşmasına olanak tanırken belirli bireyler hakkında sızdırılan bilgileri sınırlamaya yardımcı olur.
​
Gömülü Temsiller: Verilerin (metin, görüntü vb.) semantik anlamını yüksek boyutlu bir uzayda yakalayan yoğun vektör temsilleri.
​
Açıklanabilirlik – Yapay Zeka'da açıklanabilirlik, bir yapay zeka sisteminin kararları ve tahminleri için insanlar tarafından anlaşılabilir gerekçeler sunma yeteneğidir ve iç işleyişine dair içgörüler sağlar.
​
Açıklanabilir Yapay Zeka (XAI): Kararları ve davranışları için insanların anlayabileceği açıklamalar sunmak üzere tasarlanmış yapay zeka sistemleri; çeşitli teknikler ve çerçeveler aracılığıyla.
​
Federated Learning: Verilerin kendisini paylaşmadan, yerel veri örneklerini tutan birden çok merkezi olmayan cihaz üzerinde modellerin eğitildiği bir makine öğrenimi yaklaşımıdır.
​
Koruma Önlemleri: Yapay zeka sistemlerinin zararlı, önyargılı veya başka biçimde istenmeyen çıktılar üretmesini önlemek için uygulanmış kısıtlamalar.
​
Halüsinasyon – Bir yapay zeka halüsinasyonu, bir yapay zeka modelinin eğitim verilerine veya gerçekliğe dayanmayan yanlış veya yanıltıcı bilgiler ürettiği bir olguya işaret eder.
​
İnsan-dahil Döngü (HITL): Kritik karar noktalarında insan gözetimi, doğrulama veya müdahalesi gerektirecek biçimde tasarlanmış sistemler.
​
Kod Olarak Altyapı (IaC): Manuel süreçler yerine kod aracılığıyla altyapının yönetimi ve sağlanması, güvenlik taramasını mümkün kılarak tutarlı dağıtımlar sağlar.
​
Jailbreak: Yapay zeka sistemlerindeki güvenlik kısıtlamalarını aşmak için kullanılan teknikler, özellikle büyük dil modellerinde, yasak içerik üretmek amacıyla.
​
En Az Yetki İlkesi: Kullanıcılara ve süreçlere yalnızca gerekli minimum erişim haklarının verilmesi güvenlik ilkesidir.
​
LIME (Yerel Yorumlanabilir Model-agnostik Açıklamalar): Herhangi bir makine öğrenimi sınıflandırıcısının tahminlerini yerel olarak yorumlanabilir bir modelle yaklaşık olarak açıklayan bir tekniktir.
​
Üyelik çıkarım saldırısı: Belirli bir veri noktasının bir makine öğrenimi modelinin eğitilmesinde kullanılıp kullanılmadığını belirlemeyi amaçlayan bir saldırı.
​
MITRE ATLAS: Yapay-Zeka Sistemleri İçin Kasıtlı Tehdit Manzarası; Yapay-Zeka Sistemlerine Karşı Kasıtlı Taktik ve Teknikler Hakkında Bilgi Tabanı.
​
Model Kartı – Bir model kartı, bir yapay zeka modelinin performansı, sınırlamaları, amaçlanan kullanımları ve etik hususları hakkında standartlaştırılmış bilgiler sunan bir belgedir; şeffaflığı artırmak ve sorumlu yapay zeka geliştirmeyi teşvik etmek amacıyla.
​
Model Çıkarımı: Yetkisiz bir tarafın hedef modele tekrarlı sorgular yaparak, yetkisi olmadan fonksiyonel olarak benzer bir kopya oluşturmaya çalıştığı bir saldırı türüdür.
​
Model İnversiyonu: Model çıktılarının analiziyle eğitim verisini yeniden oluşturmaya çalışan bir saldırı.
​
Model Yaşam Döngüsü Yönetimi – Yapay Zeka Model Yaşam Döngüsü Yönetimi, bir yapay zeka modelinin varoluşunun tüm aşamalarını gözetim altında tutma sürecidir; tasarımı, geliştirilmesi, dağıtımı, izlenmesi, bakımı ve nihai emekliliğini kapsar; bunun amacı modelin etkili kalmasını ve hedeflerle uyumlu olmasını sağlamaktır.
​
Model zehirlenmesi: Eğitim süreci sırasında bir modele doğrudan güvenlik açıkları veya arka kapılar enjekte etmek.
​
Model Çalınması/Hırsı: Tekrarlı sorgular yoluyla tescilli bir modelin bir kopyasının veya yaklaşık bir sürümünün elde edilmesi.
​
Çok ajanlı sistem: Birden çok etkileşimli yapay zeka ajanından oluşan bir sistem olup, her biri potansiyel olarak farklı yeteneklere ve hedeflere sahip olabilir.
​
OPA (Open Policy Agent): Yığının tüm katmanlarında birleşik politika uygulanmasını sağlayan açık kaynaklı bir politika motoru.
​
Gizliliği Korumaya Yönelik Makine Öğrenimi (PPML): Eğitim verilerinin gizliliğini korurken ML modellerini eğitmek ve kullanıma sunmak için teknikler ve yöntemler.
​
İstem Enjeksiyonu: Zararlı talimatların girdilere gömüldüğü ve bir modelin amaçlanan davranışını devre dışı bırakmak veya değiştirmek amacıyla yapılan bir saldırıdır.
​
RAG (Retrieval-Augmented Generation): Yanıt üretmeden önce harici bilgi kaynaklarından ilgili bilgileri getirerek büyük dil modellerini güçlendiren bir tekniktir.
​
Kırmızı Takım Çalışması: Yapay Zeka (AI) sistemlerini güvenlik açıklarını belirlemek amacıyla adversarial saldırıları simüle ederek aktif olarak test etme uygulamasıdır.
​
SBOM (Software Bill of Materials): yazılım veya yapay zeka modellerinin inşa edilmesi için kullanılan çeşitli bileşenlerin ayrıntılarını ve tedarik zinciri ilişkilerini içeren resmi bir kayıt.
​
SHAP (SHapley Additive exPlanations): Her özelliğin tahmine katkısını hesaplayarak herhangi bir makine öğrenimi modelinin çıktısını açıklamaya yönelik oyun kuramına dayalı bir yaklaşım.
​
Tedarik Zinciri Saldırısı: Bir sistemi, tedarik zincirindeki daha güvenli olmayan unsurları hedef alarak ele geçirmektir; örneğin üçüncü taraf kütüphaneler, veri kümeleri veya önceden eğitilmiş modeller gibi öğeler.
​
Transfer Öğrenimi: Bir görev için geliştirilmiş bir modelin, ikinci bir görev için bir modelin başlangıç noktası olarak yeniden kullanıldığı bir tekniktir.
​
Vektör Veritabanı: Yüksek boyutlu vektörleri (gömülü temsiller) depolamak ve verimli benzerlik aramaları gerçekleştirmek için tasarlanmış özel bir veritabanıdır.
​
Zafiyet Taraması: Otomatik araçlar, yazılım bileşenlerinde bilinen güvenlik açıklarını tespit eden, yapay zeka çerçeveleri ve bağımlılıkları da dahil.
​
Filigranlama: Yapay Zeka tarafından üretilen içeriğe algılanmayan işaretler yerleştirme teknikleriyle içeriğin kökenini izlemek veya yapay zeka üretimini tespit etmek.
​
Sıfır Gün Açığı: Geliştiriciler bir yama oluşturup dağıtmadan önce saldırganların istismar edebileceği, daha önce bilinmeyen bir güvenlik açığıdır.

## Ek B: Kaynaklar

### TODO

## Ek C: Yapay Zeka Güvenlik Yönetişimi ve Dokümantasyon

### Amaç

Bu ek bölüm, sistem yaşam döngüsü boyunca yapay zeka güvenliğini yöneten örgütsel yapılar, politikalar ve süreçlerin kurulumuna ilişkin temel gereksinimleri sunar.

---

### AC.1 Yapay Zeka Risk Yönetim Çerçevesinin Benimsenmesi

Sistem yaşam döngüsü boyunca Yapay Zeka'ya özgü riskleri tanımlamaya, değerlendirmeye ve hafifletmeye yönelik resmi bir çerçeve sunun.

 #AC.1.1    Seviye: 1    Rol: D/V
 AI‑özel risk değerlendirme metodolojisinin belgelendiğini ve uygulandığını doğrulayın.
 #AC.1.2    Seviye: 2    Rol: D
 Yapay zeka yaşam döngüsü boyunca kilit noktalarda ve önemli değişikliklerden önce risk değerlendirmelerinin yapıldığını doğrulayın.
 #AC.1.3    Seviye: 3    Rol: D/V
 Risk yönetimi çerçevesinin belirlenen standartlarla uyumlu olduğunu doğrulayın (örneğin NIST AI RMF).

---

### AC.2 Yapay Zeka Güvenlik Politikası ve Prosedürleri

Güvenli yapay zeka geliştirme, dağıtımı ve işletimi için kurumsal standartları tanımlayın ve bunları uygulayın.

 #AC.2.1    Seviye: 1    Rol: D/V
 Belgelendirilmiş yapay zeka güvenlik politikalarının mevcut olduğundan emin olun.
 #AC.2.2    Seviye: 2    Rol: D
 Politikaların en az yılda bir kez ve önemli tehdit-ortamı değişikliklerinden sonra gözden geçirildiğini ve güncellendiğini doğrulayın.
 #AC.2.3    Seviye: 3    Rol: D/V
 Politikaların AISVS kategorilerini ve ilgili düzenleyici gereklilikleri kapsadığını doğrulayın.

---

### AC.3 Yapay Zeka Güvenliği İçin Roller ve Sorumluluklar

Organizasyon genelinde yapay zeka güvenliği için açık hesap verebilirlik sağlayın.

 #AC.3.1    Seviye: 1    Rol: D/V
 Yapay Zeka güvenlik rollerinin ve sorumluluklarının belgelendiğini doğrulayın.
 #AC.3.2    Seviye: 2    Rol: D
 Sorumlu kişilerin uygun güvenlik uzmanlığına sahip olduklarını doğrulayın.
 #AC.3.3    Seviye: 3    Rol: D/V
 Yüksek-riskli yapay zeka sistemleri için bir yapay zeka etiği komitesi veya yönetişim kurulu kurulduğunu doğrulayın.

---

### AC.4 Etik Yapay Zeka İlkeleri Uygulanması

Yapay Zeka sistemlerinin belirlenmiş etik ilkelere göre çalışmasını sağlayın.

 #AC.4.1    Seviye: 1    Rol: D/V
 Yapay zeka geliştirme ve dağıtımı için etik yönergelerin mevcut olduğuna doğrulayın.
 #AC.4.2    Seviye: 2    Rol: D
 Etik ihlallerinin tespit edilmesi ve raporlanması için mekanizmaların mevcut olduğundan emin olun.
 #AC.4.3    Seviye: 3    Rol: D/V
 Dağıtılan yapay zeka sistemlerinin düzenli etik incelemelerinin yapıldığından emin olun.

---

### AC.5 Yapay Zeka Düzenleyici Uyum İzleme

Gelişen yapay zeka düzenlemelerinin farkında olmak ve bu düzenlemelere uyum sağlamak.

 #AC.5.1    Seviye: 1    Rol: D/V
 Uygulanabilir yapay zeka mevzuatını belirlemek için süreçlerin mevcut olduğundan emin olun.
 #AC.5.2    Seviye: 2    Rol: D
 Tüm düzenleyici gerekliliklere uyumun değerlendirildiğini doğrulayın.
 #AC.5.3    Seviye: 3    Rol: D/V
 Düzenleyici değişikliklerin yapay zeka sistemlerinde zamanında incelemeler ve güncellemelerin tetiklendiğini doğrulayın.

### AC.6 Eğitim Verisi Yönetişimi, Dokümantasyon ve Süreç

 #1.1.2    Seviye: 1    Rol: D/V
 Kalite, temsiliyet, etik kaynak temini ve lisans uyumu açısından gözden geçirilmiş veri kümelerinin yalnızca kabul edildiğini doğrulayın; bu, zehirlenme, gömülü önyargı ve fikri mülkiyet ihlali risklerini azaltır.
 #1.1.5    Seviye: 2    Rol: D/V
 Etiketleme/yorumlama kalitesinin, inceleyici çapraz kontrolleri veya fikir birliği yoluyla güvence altına alındığını doğrulayın.
 #1.1.6    Seviye: 2    Rol: D/V
 Önemli eğitim veri kümeleri için "data cards" veya "datasheets for datasets"in tutulduğunu doğrulayın; bunlar özellikler, motivasyonlar, bileşim, toplama süreçleri, ön işleme ve önerilen/kaçınılan kullanımlar gibi ayrıntıları içermelidir.
 #1.3.2    Seviye: 2    Rol: D/V
 Belirlenen önyargıların belgelendirilmiş stratejilerle hafifletildiğini doğrulayın; bu stratejiler arasında yeniden dengelenme, hedefli veri çoğaltması, algoritmik ayarlamalar (ör. ön işleme, işleme sırasında, çıktı sonrası işlemler teknikleri) veya yeniden ağırlıklandırma yer alır; hafifletmenin adaletlilik ile genel model performansı üzerindeki etkisinin değerlendirildiği de gözlemlenir.
 #1.3.3    Seviye: 2    Rol: D/V
 Eğitim sonrası adalet metriklerinin değerlendirildiğini ve belgelendiğini doğrulayın.
 #1.3.4    Seviye: 3    Rol: D/V
 Bir yaşam döngüsü önyargı yönetim politikası sahipleri atar ve inceleme sıklığını belirler mi?
 #1.4.1    Seviye: 2    Rol: D/V
 Etiketleme/yorumlama kalitesinin net yönergeler, inceleyenler arası çapraz kontroller, fikir birliği mekanizmaları (örneğin, etiketleyiciler arası uyumun izlenmesi) ve farklılıkları çözmek için tanımlanmış süreçler aracılığıyla sağlandığını doğrulayın.
 #1.4.4    Seviye: 3    Rol: D/V
 Güvenlik, emniyet veya adalet açısından kritik olan etiketlerin zorunlu bağımsız çift incelemelerini veya bununla eşdeğer sağlam bir doğrulama sürecini almasını doğrulayın.
 #1.4.6    Seviye: 2    Rol: D/V
 Etiketleme kılavuzlarının ve talimatlarının kapsamlı, sürüm kontrollü ve akran incelemeli olduğundan emin olun.
 #1.4.6    Seviye: 2    Rol: D/V
 Etiketler için veri şemalarının açıkça tanımlandığından ve sürüm kontrolüne alındığından emin olun.
 #1.3.1    Seviye: 1    Rol: D/V
 Veri setlerinin, temsili dengesizliğin ve potansiyel önyargıların, yasal olarak korunan nitelikler (ör. ırk, cinsiyet, yaş) ile modelin uygulama alanına ilişkin diğer etik olarak hassas özellikler (ör. sosyoekonomik durum, konum) üzerinde profillendiğini doğrulayın.
 #1.5.3    Seviye: 2    Rol: V
 Alan uzmanları tarafından yapılan manuel yerinde kontrollerin istatistiksel olarak anlamlı bir örneklem kapsadığını doğrulayın (örneğin ≥1% veya 1,000 örneklem, hangisi büyükse ya da risk değerlendirmesiyle belirlenen).
 #1.8.4    Seviye: 2    Rol: D/V
 Dış kaynaklı veya kitle kaynaklı etiketleme iş akışlarının, veri gizliliğini, bütünlüğünü, etiket kalitesini sağlamak ve veri sızıntısını önlemek için teknik/prosedüel güvenlik önlemlerine sahip olduğunu doğrulayın.
 #1.5.4    Seviye: 2    Rol: D/V
 Düzeltici adımların provenance kayıtlarına eklenip eklenmediğini doğrulayın.
 #1.6.2    Seviye: 2    Rol: D/V
 İşaretlenmiş örneklerin eğitimden önce manuel incelemeyi tetiklediğini doğrulayın.
 #1.6.3    Seviye: 2    Rol: V
 Sonuçların modelin güvenlik dosyasını beslediğini ve devam eden tehdit istihbaratını bilgilendirdiğini doğrulayın.
 #1.6.4    Seviye: 3    Rol: D/V
 Tespit mantığının yeni tehdit istihbaratı ile güncellendiğini doğrulayın.
 #1.6.5    Seviye: 3    Rol: D/V
 Çevrimiçi öğrenme boru hatlarının dağılım sürüklenmesini izlediğini doğrulayın.
 #1.7.1    Seviye: 1    Rol: D/V
 Eğitim verisi silme iş akışlarının birincil ve türetilmiş verileri temizlediğini doğrulayın ve model etkisini değerlendirin; ayrıca etkilenen modeller üzerindeki etkisinin değerlendirildiğini ve gerekirse (örneğin yeniden eğitim veya yeniden kalibrasyon yoluyla) ele alınmasını teyit edin.
 #1.7.2    Seviye: 2    Rol: D
 Kullanıcı onayının kapsamını ve durumunu (ve rızanın geri çekilmesini) izlemek ve buna saygı göstermek için mekanizmaların mevcut olduğundan emin olun; ayrıca verinin yeni eğitim süreçlerine veya önemli model güncellemelerine dahil edilmeden önce rızanın doğrulanmış olduğundan emin olun.
 #1.7.3    Seviye: 2    Rol: V
 İş akışlarının yıllık olarak test edildiğini ve kaydedildiğini doğrulayın.
 #1.8.1    Seviye: 2    Rol: D/V
 Üçüncü taraf veri sağlayıcılarının, önceden eğitilmiş modellerin ve harici veri kümelerinin sağlayıcılarını da içerecek şekilde, verileri veya modelleri entegre etmeden önce güvenlik, gizlilik, etik kaynak temini ve veri kalitesi açısından gerekli özeni gösterdiklerini doğrulayın.
 #1.8.2    Seviye: 1    Rol: D
 Harici transferlerin TLS/kimlik doğrulama ve bütünlük kontrollerini kullandığından emin olun.
 #1.8.3    Seviye: 2    Rol: D/V
 Yüksek riskli veri kaynaklarının (örneğin kökeni bilinmeyen açık kaynak veri setleri, denetlenmemiş tedarikçiler) hassas uygulamalarda kullanılmadan önce sandbox analizi, kapsamlı kalite/önyargı kontrolleri ve hedefli zehirlenme tespiti gibi geliştirilmiş incelemelere tabi tutulduğunu doğrulayın.
 #1.8.4    Seviye: 3    Rol: D/V
 Üçüncü taraflardan elde edilen önceden eğitilmiş modellerin, ince ayar yapmadan veya dağıtım öncesinde, gömülü önyargılar, potansiyel arka kapılar, mimari bütünlüğü ve orijinal eğitim verilerinin kökeni açısından değerlendirildiğini doğrulayın.
 #1.5.3    Seviye: 2    Rol: D/V
 Adversarial eğitim kullanılıyorsa, adversarial veri setlerinin üretilmesi, yönetimi ve sürümlemesinin belgelendiğini ve kontrol edildiğini doğrulayın.
 #1.5.3    Seviye: 3    Rol: D/V
 Zararlı saldırılara karşı dayanıklılık eğitiminin, temiz ve zararlı saldırı girdilerine karşı model performansı ile adalet ölçütleri üzerindeki etkisinin değerlendirildiği, belgelendiği ve izlendiği doğrulanmalıdır.
 #1.5.4    Seviye: 3    Rol: D/V
 Adversarial eğitim ve dayanıklılık stratejilerinin, gelişen adversarial saldırı tekniklerine karşı koymak amacıyla periyodik olarak gözden geçirildiğini ve güncellendiğini doğrulayın.
 #1.4.2    Seviye: 2    Rol: D/V
 Başarısız veri kümelerinin denetim izleriyle karantinaya alındığından emin olun.
 #1.4.3    Seviye: 2    Rol: D/V
 Kalite kapılarının, istisnalar onaylanmadıkça, kalitesi düşük veri kümelerini engellediğini doğrulayın.
 #1.11.2    Seviye: 2    Rol: D/V
 Üretim süreci, parametreler ve sentetik verinin amaçlanan kullanımıyla ilgili belgelerin mevcut olduğunu doğrulayın.
 #1.11.3    Seviye: 2    Rol: D/V
 Eğitimde kullanılmadan önce sentetik verinin önyargı, gizlilik sızıntısı ve temsil sorunları açısından risk değerlendirmesinden geçirildiğini doğrulayın.
 #1.12.3    Seviye: 2    Rol: D/V
 Şüpheli erişim olayları için uyarıların oluşturulduğunu ve derhal incelendiğini doğrulayın.
 #1.13.1    Seviye: 1    Rol: D/V
 Tüm eğitim veri setleri için açık saklama sürelerinin tanımlı olduğundan emin olun.
 #1.13.2    Seviye: 2    Rol: D/V
 Veri kümelerinin yaşam döngüsünün sonunda otomatik olarak süresinin dolduğunu, silindiğini veya silinmesi için gözden geçirilmesini doğrulayın.
 #1.13.3    Seviye: 2    Rol: D/V
 Saklama ve silme işlemlerinin kaydedildiğini ve denetlenebilir olduğunu doğrulayın.
 #1.14.1    Seviye: 2    Rol: D/V
 Tüm veri kümeleri için veri ikametgahı ve sınırötesi transfer gerekliliklerinin belirlendiğini ve uygulanıldığını doğrulayın.
 #1.14.2    Seviye: 2    Rol: D/V
 Sektöre özgü düzenlemelerin (örn. sağlık, finans) veri işleme süreçlerinde belirlenip ele alındığının doğrulanması.
 #1.14.3    Seviye: 2    Rol: D/V
 İlgili gizlilik yasalarına (örn. GDPR, CCPA) uyumunun belgelendiğini ve düzenli olarak gözden geçirildiğini doğrulayın.
 #1.16.1    Seviye: 2    Rol: D/V
 Veri konusu taleplerine (erişim, düzeltme, kısıtlama veya itiraz) yanıt verecek mekanizmaların mevcut olduğunu doğrulayın.
 #1.16.2    Seviye: 2    Rol: D/V
 İsteklerin kaydedildiğini, izlendiğini ve yasal olarak belirlenen süreler içinde yerine getirildiğini doğrulayın.
 #1.16.3    Seviye: 2    Rol: D/V
 Kişisel veri sahiplerinin hakları süreçlerinin etkinliği için düzenli olarak test edildiğini ve gözden geçirildiğini doğrulayın.
 #1.17.1    Seviye: 2    Rol: D/V
 Bir veri kümesi sürümünü güncellemeden veya değiştirmeden önce etki analizinin gerçekleştirilmesini doğrulayın; bu analiz model performansını, adalet ve uyumluluğu kapsamalıdır.
 #1.17.2    Seviye: 2    Rol: D/V
 Etki analizi sonuçlarının belgelendiğini ve ilgili paydaşlar tarafından incelendiğini doğrulayın.
 #1.17.3    Seviye: 2    Rol: D/V
 Yeni sürümler kabul edilemez riskler veya regresyonlar ortaya çıkarırsa geri alma planlarının mevcut olduğundan emin olun.
 #1.18.1    Seviye: 2    Rol: D/V
 Veri etiketlemeyle ilgili tüm personelin arka plan kontrolünden geçirildiğini ve veri güvenliği ile gizlilik konularında eğitimli olduğunu doğrulayın.
 #1.18.2    Seviye: 2    Rol: D/V
 Tüm etiketleyici personelin gizlilik ve ifşa etmeme sözleşmeleri imzalamış olduğundan emin olun.
 #1.18.3    Seviye: 2    Rol: D/V
 Etiketleme platformlarının erişim kontrollerini uyguladıklarını ve iç tehditleri izlediklerini doğrulayın.

#### Kaynaklar

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Ek D: Yapay Zeka-Destekli Güvenli Kodlama Yönetişimi ve Doğrulama

### Amaç

Bu bölüm, yazılım geliştirme süreci boyunca yapay zeka destekli kodlama araçlarının güvenli ve etkili kullanımına yönelik temel örgütsel kontrolleri tanımlar ve SDLC boyunca güvenlik ile izlenebilirliği sağlar.

---

### AD.1 Yapay Zeka Destekli Güvenli‑Kodlama İş Akışı

Kuruluşun güvenli‑yazılım‑geliştirme yaşam döngüsüne (SSDLC) yapay zeka araçlarını entegre etmek, mevcut güvenlik kapılarının zayıflatılmasına yol açmamak.

 #AD.1.1    Seviye: 1    Rol: D/V
 Belgelenmiş bir iş akışının, yapay zeka araçlarının ne zaman ve nasıl kod üretebileceğini, kodu yeniden düzenleyebileceğini veya inceleyebileceğini açıkladığını doğrulayın.
 #AD.1.2    Seviye: 2    Rol: D
 İş akışının her SSDLC aşamasına (tasarım, uygulama, kod incelemesi, test, dağıtım) karşılık gelip gelmediğini doğrulayın.
 #AD.1.3    Seviye: 3    Rol: D/V
 AI tarafından üretilen kod üzerinde metriklerin (örneğin güvenlik açığı yoğunluğu, tespit için ortalama süre) toplandığını ve bunların yalnızca insanlardan oluşan temel değerlerle karşılaştırıldığını doğrulayın.

---

### AD.2 Yapay Zeka Aracı Yeterlilik ve Tehdit Modelleme

Kullanıma alınmadan önce AI kodlama araçlarının güvenlik yetenekleri, riskleri ve tedarik‑zinciri etkileri açısından değerlendirildiğinden emin olun.

 #AD.2.1    Seviye: 1    Rol: D/V
 Her yapay zeka aracı için bir tehdit modelinin kötüye kullanımı, model‑inversion, veri sızıntısı ve bağımlılık zinciri risklerini belirlediğini doğrulayın.
 #AD.2.2    Seviye: 2    Rol: D
 Araç değerlendirmelerinin herhangi bir yerel bileşenin statik/dinamik analizini ve SaaS uç noktalarının (TLS, kimlik doğrulama/yetkilendirme, loglama) değerlendirmesini içerdiğini doğrulayın.
 #AD.2.3    Seviye: 3    Rol: D/V
 Değerlendirmelerin tanınmış bir çerçeveye uyduğunu doğrulayın ve ana sürüm değişikliklerinden sonra bunların yeniden gerçekleştirilmesini sağlayın.

---

### AD.3 Güvenli İstem ve Bağlam Yönetimi

Yapay zeka modelleri için istemler veya bağlamlar oluştururken gizli bilgilerin, tescilli kodun ve kişisel verilerin sızdırılmasını önleyin.

 #AD.3.1    Seviye: 1    Rol: D/V
 Yazılı kılavuzun, istemlerde gizli bilgiler, kimlik bilgileri veya sınıflandırılmış verilerin gönderilmesini yasakladığını doğrulayın.
 #AD.3.2    Seviye: 2    Rol: D
 Teknik kontrollerin (istemci tarafı kırpma, onaylı bağlam filtreleri) duyarlı artefaktları otomatik olarak temizlediğini doğrulayın.
 #AD.3.3    Seviye: 3    Rol: D/V
 İstemlerin ve yanıtların tokenleştirilmiş olduğundan, iletim sırasında ve dinlenirken şifreli olduğundan ve saklama sürelerinin veri sınıflandırma politikasıyla uyumlu olduğundan emin olun.

---

### AD.4 Yapay Zeka Tarafından Üretilen Kodun Doğrulanması

Kod birleştirilmeden veya dağıtılmadan önce yapay zeka çıktısı ile ortaya çıkan güvenlik açıklarını tespit edin ve düzeltin.

 #AD.4.1    Seviye: 1    Rol: D/V
 AI‑tarafından üretilen kodun her zaman insan tarafından kod incelemesine tabi olduğundan emin olun.
 #AD.4.2    Seviye: 2    Rol: D
 AI‑generated kod içeren her çekme isteğinde otomatik tarayıcıların (SAST/IAST/DAST) çalıştığını doğrulayın ve kritik bulgular söz konusu olduğunda birleştirmelerin engellenmesini sağlayın.
 #AD.4.3    Seviye: 3    Rol: D/V
 Farklılaştırılmış fuzz testi veya özellik tabanlı testlerin güvenlik‑kritik davranışları kanıtladıklarını doğrulayın (örneğin, giriş doğrulama, yetkilendirme mantığı).

---

### AD.5 Kod Önerilerinin Açıklanabilirliği ve İzlenebilirliği

Denetçilere ve geliştiricilere, bir önerinin neden sunulduğunu ve nasıl evrildiğini gösteren içgörü sağlayın.

 #AD.5.1    Seviye: 1    Rol: D/V
 İstem/cevap çiftlerinin commit ID'leriyle kaydedildiğini doğrulayın.
 #AD.5.2    Seviye: 2    Rol: D
 Geliştiricilerin bir öneriyi destekleyen model atıflarını (eğitim parçacıkları, belgeler) ortaya çıkarabildiğini doğrulayın.
 #AD.5.3    Seviye: 3    Rol: D/V
 Açıklanabilirlik raporlarının tasarım çıktılarıyla birlikte depolandığını ve güvenlik incelemelerinde referans gösterildiğini doğrulayın; ISO/IEC 42001 izlenebilirlik ilkelerini karşılar.

---

### AD.6 Sürekli Geri Bildirim ve Modelin İnce Ayarı

Zaman içinde modelin güvenlik performansını artırırken, olumsuz sapmayı önlemek.

 #AD.6.1    Seviye: 1    Rol: D/V
 Geliştiricilerin güvensiz veya uygunsuz önerileri işaretleyebilmesini ve bu işaretlerin izlenmesini doğrulayın.
 #AD.6.2    Seviye: 2    Rol: D
 Toplanmış geribildirimlerin, periyodik ince ayar veya geri-getirme ile güçlendirilmiş üretim süreçlerini doğrulanmış güvenli-kodlama korpusları ile bilgilendirdiğini doğrulayın (örn. OWASP Cheat Sheets).
 #AD.6.3    Seviye: 3    Rol: D/V
 Her ince ayardan sonra kapalı‑döngü değerlendirme aracının regresyon testlerini yürüttüğünden emin olun; güvenlik metrikleri, dağıtımdan önceki referans değerlerini karşılamalı veya bunların üzerinde olmalıdır.

---

#### Kaynaklar

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Ek E: Örnek Araçlar ve Çerçeveler

### Amaç

Bu bölüm, verilen bir AISVS gereksiniminin uygulanmasına veya yerine getirilmesine destek olabilecek araçlar ve çerçeveler için örnekler sunar. Bunlar AISVS ekibi veya OWASP GenAI Güvenlik Projesi tarafından öneri veya onay olarak görülmemelidir.

---

### AE.1 Eğitim Verisi Yönetişimi ve Önyargı Yönetimi

Veri analitiği, yönetişim ve önyargı yönetimi için kullanılan araçlar.

 #AE.1.1    Bölüm: 1.1
 Veri Envanteri Araçları: Veri envanteri yönetimi araçları gibi...
 #AE.1.2    Bölüm: 1.2
 Taşıma Sırasındaki Şifreleme TLS'yi HTTPS-based uygulamalar için kullanın, openSSL ve Python'un gibi araçlarla`ssl` kütüphane.

---

### AE.2 Kullanıcı Girişi Doğrulaması

Kullanıcı girdilerini ele almak ve doğrulamak için araçlar.

 #AE.2.1    Bölüm: 2.1
 İstem Enjeksiyonu Savunma Araçları: NVIDIA'nın NeMo'su veya Guardrails AI gibi guardrail araçlarını kullanın.

---

