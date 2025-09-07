## Önkapak

### Standart Hakkında

Yapay Zeka Güvenlik Doğrulama Standardı (AISVS), veri bilimciler, MLOps mühendisleri, yazılım mimarları, geliştiriciler, test uzmanları, güvenlik profesyonelleri, araç satıcıları, düzenleyiciler ve kullanıcılar tarafından güvenilir yapay zeka destekli sistemler ve uygulamalar tasarlamak, oluşturmak, test etmek ve doğrulamak için kullanılabilecek topluluk odaklı güvenlik gereksinimleri kataloğudur. Veri toplama ve model geliştirmeden dağıtım ve sürekli izlemeye kadar yapay zeka yaşam döngüsü boyunca güvenlik kontrollerini belirlemek için ortak bir dil sağlar; böylece kuruluşlar yapay zeka çözümlerinin dayanıklılığını, gizliliğini ve güvenliğini ölçüp geliştirebilirler.

### Telif Hakkı ve Lisans

Sürüm 0.1 (İlk Kamu Taslağı - Çalışma Devam Ediyor), 2025  

![license](images/license.png)
Telif Hakkı © 2025 The AISVS Projesi.  

Altında yayımlanmıştırCreative Commons Attribution‑ShareAlike 4.0 International License.
Herhangi bir yeniden kullanım veya dağıtım için, bu çalışmanın lisans koşullarını başkalarına açıkça iletmelisiniz.

### Proje Yöneticileri

Jim Manico
Aras “Russ” Memisyazıcı

### Katkıda Bulunanlar ve İnceleyenler

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS, yapay zeka sistemlerinin benzersiz güvenlik zorluklarını ele almak için özel olarak oluşturulan yepyeni bir standarttır. Daha geniş güvenlik en iyi uygulamalarından ilham alırken, AISVS’deki her gereklilik, AI tehdit ortamını yansıtmak ve kuruluşların daha güvenli, daha dayanıklı AI çözümleri geliştirmesine yardımcı olmak amacıyla baştan sona geliştirilmiştir.

## Önsöz

Yapay Zeka Güvenlik Doğrulama Standardı (AISVS) sürüm 1.0'a hoş geldiniz!

### Giriş

2025 yılında iş birliği içinde kurulan AISVS, modern AI modelleri, boru hatları ve AI destekli hizmetlerin tasarımı, geliştirilmesi, dağıtımı ve işletilmesi sırasında dikkate alınması gereken güvenlik gereksinimlerini tanımlar.

AISVS v1.0, proje liderleri, çalışma grubu ve daha geniş topluluk katkıları tarafından yap pragmatik, test edilebilir bir temel oluşturmak için AI sistemlerini güvence altına almak amacıyla ortak çalışmaların bir birleşimidir.

Bu sürümle amacımız, AISVS'yi benimsemeyi basit hale getirmek ve tanımlı kapsamına sıkı sıkıya odaklanırken, AI'ya özgü hızlı değişen risk ortamını ele almaktır.

### AISVS Sürüm 1.0 İçin Ana Hedefler

Sürüm 1.0, birkaç temel ilke doğrultusunda oluşturulacaktır.

#### İyi Tanımlanmış Kapsam

Her gereksinim AISVS'nin adı ve misyonuyla uyumlu olmalıdır:

Yapay Zeka – Kontroller AI/ML katmanında (veri, model, boru hattı veya çıkarım) çalışır ve AI uzmanlarının sorumluluğundadır.
Güvenlik – Gereksinimler, belirlenen güvenlik, gizlilik veya emniyet risklerini doğrudan azaltır.
Doğrulama – Dil, uygunluğun nesnel olarak doğrulanabilmesi için yazılmıştır.
Standart – Bölümler tutarlı bir yapı ve terminoloji izleyerek uyumlu bir referans oluşturur.
​
---

AISVS’yi takip ederek, kuruluşlar AI çözümlerinin güvenlik duruşunu sistematik olarak değerlendirebilir ve güçlendirebilir, böylece güvenli AI mühendisliği kültürünü teşvik edebilirler.

## AISVS kullanarak

Yapay Zeka Güvenlik Doğrulama Standardı (AISVS), modern yapay zeka uygulamaları ve hizmetleri için güvenlik gereksinimlerini tanımlar ve uygulama geliştiricilerin kontrolü altındaki yönlere odaklanır.

AISVS, geliştiriciler, mimarlar, güvenlik mühendisleri ve denetçiler dahil olmak üzere AI uygulamalarının güvenliğini geliştiren veya değerlendiren herkes için tasarlanmıştır. Bu bölüm, AISVS'nin yapısını ve kullanımını, doğrulama seviyelerini ve hedeflenen kullanım durumlarını tanıtmaktadır.

### Yapay Zeka Güvenlik Doğrulama Düzeyleri

AISVS, üç artan güvenlik doğrulama seviyesi tanımlar. Her seviye, derinlik ve karmaşıklık ekleyerek, kuruluşların yapay zeka sistemlerinin risk seviyesine göre güvenlik duruşlarını özelleştirmelerine olanak tanır.

Kuruluşlar, Seviye 1'den başlayabilir ve güvenlik olgunluğu ve tehdit maruziyeti arttıkça kademeli olarak daha yüksek seviyeleri benimseyebilir.

#### Düzeylerin Tanımı

AISVS v1.0'daki her gereksinim aşağıdaki seviyelerden birine atanır:

 Seviye 1 gereksinimleri

Seviye 1, en kritik ve temel güvenlik gereksinimlerini içerir. Bunlar, diğer ön koşullara veya güvenlik açıklarına dayanmayan yaygın saldırıları önlemeye odaklanır. Seviye 1 kontrollerinin çoğu ya uygulanması oldukça basittir ya da çabayı hak edecek kadar önemlidir.

 Seviye 2 gereksinimleri

Seviye 2, daha gelişmiş veya daha az yaygın saldırıları ve yaygın tehditlere karşı katmanlı savunmaları ele alır. Bu gereksinimler, daha karmaşık mantık içerebilir veya belirli saldırı önkoşullarını hedefleyebilir.

 Seviye 3 gereksinimleri

Seviye 3, genellikle uygulanması daha zor olan veya duruma bağlı olarak geçerli olan kontrolleri içerir. Bunlar genellikle derinlemesine savunma mekanizmalarını veya niş, hedefe yönelik ya da yüksek karmaşıklıktaki saldırılara karşı hafifletmeleri temsil eder.

#### Rol (D/V)

Her AISVS gereksinimi, birincil hedef kitleye göre işaretlenmiştir:

D – Geliştirici odaklı gereksinimler
V – Doğrulayıcı/müfettiş odaklı gereksinimler
D/V – Hem geliştiriciler hem de doğrulayıcılar için geçerlidir

## C1 Eğitim Verisi Yönetimi ve Önyargı Yönetimi

### Kontrol Amacı

Eğitim verileri, köken, güvenlik, kalite ve adaleti koruyacak şekilde temin edilmeli, işlenmeli ve sürdürülmelidir. Bu, yasal sorumlulukların yerine getirilmesini sağlar ve tüm Yapay Zeka yaşam döngüsünü etkileyebilecek önyargı, zehirlenme veya gizlilik ihlalleri risklerini azaltır.

---

### C1.1 Eğitim Verisi Kökeni

Tüm veri setlerinin doğrulanabilir bir envanterini tutun, yalnızca güvenilir kaynakları kabul edin ve denetlenebilirlik için her değişikliği kaydedin.

 #1.1.1    Seviye: 1    Rol: D/V
 Her eğitim veri kaynağının (kaynak, sorumlu/sahip, lisans, toplama yöntemi, amaçlanan kullanım kısıtlamaları ve işleme geçmişi) güncel envanterinin tutulduğunu doğrulayın.
 #1.1.2    Seviye: 1    Rol: D/V
 Eğitim veri işlemlerinin gereksiz özellikleri, nitelikleri veya alanları (örneğin, kullanılmayan meta veriler, hassas KİB, sızdırılmış test verileri) dışladığını doğrulayın.
 #1.1.3    Seviye: 2    Rol: D/V
 Tüm veri kümesi değişikliklerinin kaydedilmiş bir onay iş akışına tabi olduğunu doğrulayın.
 #1.1.4    Seviye: 3    Rol: D/V
 Veri kümelerinin veya alt kümelerin mümkün olduğunda filigranlı veya parmak izli olduğundan emin olun.

---

### C1.2 Eğitim Verisi Güvenliği ve Bütünlüğü

Erişimi eğitim verilerine kısıtlayın, verileri dinlenme ve aktarım sırasında şifreleyin ve değişiklik, hırsızlık veya veri zehirlenmesini önlemek için bütünlüğünü doğrulayın.

 #1.2.1    Seviye: 1    Rol: D/V
 Erişim kontrollerinin eğitim verisi depolama ve veri işleme hatlarını koruduğunu doğrulayın.
 #1.2.2    Seviye: 2    Rol: D/V
 Erişim yapan kişi, zaman ve işlemi de içerecek şekilde, eğitim verisine yapılan tüm erişimlerin kaydedildiğini doğrulayın.
 #1.2.3    Seviye: 2    Rol: D/V
 Eğitim veri setlerinin, sektör standardı kriptografik algoritmalar ve anahtar yönetimi uygulamaları kullanılarak hem iletim sırasında hem de depolama halinde şifrelendiğini doğrulayın.
 #1.2.4    Seviye: 2    Rol: D/V
 Eğitim verilerinin depolanması ve aktarımı sırasında veri bütünlüğünü sağlamak için kriptografik özetlerin veya dijital imzaların kullanıldığını doğrulayın.
 #1.2.5    Seviye: 2    Rol: D/V
 Otomatik tespit tekniklerinin, eğitim verilerinin yetkisiz değişikliklere veya bozulmalara karşı korunması için uygulandığını doğrulayın.
 #1.2.6    Seviye: 2    Rol: D/V
 Eski eğitim verilerinin güvenli bir şekilde silindiğini veya anonim hale getirildiğini doğrulayın.
 #1.2.7    Seviye: 3    Rol: D/V
 Tüm eğitim veri seti sürümlerinin benzersiz şekilde tanımlandığını, değiştirilemez şekilde saklandığını ve geri alma ile adli analiz desteği için denetlenebilir olduğunu doğrulayın.

---

### C1.3 Eğitim Verisi Etiketleme Kalitesi, Bütünlüğü ve Güvenliği

Etiketleri koruyun ve kritik veriler için teknik inceleme gerektirin.

 #1.3.1    Seviye: 2    Rol: D/V
 Etiket artefaktlarının bütünlüğünü ve özgünlüğünü sağlamak için kriptografik özetlerin veya dijital imzaların uygulandığını doğrulayın.
 #1.3.2    Seviye: 2    Rol: D/V
 Etiketleme arayüzlerinin ve platformlarının güçlü erişim kontrolleri uyguladığını, tüm etiketleme faaliyetlerinin tahrifata karşı dayanıklı denetim kayıtlarını tuttuğunu ve yetkisiz değişikliklere karşı koruma sağladığını doğrulayın.
 #1.3.3    Seviye: 3    Rol: D/V
 Etiketlerdeki hassas bilgilerin, veri alanı düzeyinde, hem dururken hem de iletim halinde sansürlendiğini, anonimleştirildiğini veya şifrelenmiş olduğunu doğrulayın.

---

### C1.4 Eğitim Verisi Kalitesi ve Güvenlik Güvencesi

Veri seti güvenilirliğini garanti altına almak için otomatik doğrulama, manuel örnekleme kontrolleri ve kaydedilmiş düzeltmeler birleştirin.

 #1.4.1    Seviye: 1    Rol: D
 Otomatik testlerin her ingest veya önemli veri dönüşümünde format hatalarını ve null değerleri yakaladığını doğrulayın.
 #1.4.2    Seviye: 2    Rol: D/V
 LLM eğitim ve ince ayar işlemlerinin, potansiyel zehirleme saldırılarını (örneğin, etiket çevirme, arka kapı tetikleyici ekleme, rol değiştirme komutları, etkili örnek saldırıları) veya eğitim verilerindeki kasıtsız veri bozulmalarını tanımlamak için zehirleme tespiti ve veri bütünlüğü doğrulamasını (örneğin, istatistiksel yöntemler, aykırı değer tespiti, gömme analizi) uyguladığını doğrulayın.
 #1.4.3    Seviye: 3    Rol: D/V
 Risk değerlendirmesine dayalı olarak ilgili modeller için üretilmiş adversaryal örnekler kullanılarak adversaryal eğitim, bozulmuş girdilerle veri artırımı veya sağlam optimizasyon teknikleri gibi uygun savunmaların uygulanmış ve ayarlanmış olduğunu doğrulayın.
 #1.4.4    Seviye: 2    Rol: D/V
 Otomatik olarak oluşturulan etiketlerin (örneğin, LLM'ler veya zayıf denetim yoluyla) halüsinasyonlu, yanıltıcı veya düşük güvenilirlikteki etiketleri tespit etmek için güven eşiği ve tutarlılık kontrollerine tabi tutulduğunu doğrulayın.
 #1.4.5    Seviye: 3    Rol: D
 Otomatik testlerin, her veri alma veya önemli veri dönüşümünde etiket kaymalarını yakaladığını doğrulayın.

---

### C1.5 Veri Soyu ve İzlenebilirlik

Denetlenebilirlik ve olay müdahalesi için her veri noktasının kaynaktan modele girişe kadar olan tam yolculuğunu izleyin.

 #1.5.1    Seviye: 2    Rol: D/V
 Her veri noktasının soy geçmişinin, tüm dönüşümler, artırmalar ve birleştirmeler dahil olmak üzere, kaydedildiğini ve yeniden oluşturulabileceğini doğrulayın.
 #1.5.2    Seviye: 2    Rol: D/V
 Soy kütüğü kayıtlarının değiştirilemez, güvenli bir şekilde saklandığından ve denetimler için erişilebilir olduğundan emin olun.
 #1.5.3    Seviye: 2    Rol: D/V
 Soy izleme mekanizmasının gizliliği koruyan veya üretici tekniklerle oluşturulan sentetik verileri kapsadığını ve tüm sentetik verilerin boru hattı boyunca gerçek verilerden açıkça etiketlenmiş ve ayırt edilebilir olduğunu doğrulayın.

---

### Referanslar

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

## C2 Kullanıcı Girdisi Doğrulaması

### Kontrol Amacı

Kullanıcı girdisinin sağlam şekilde doğrulanması, yapay zeka sistemlerine yönelik en zararlı saldırılara karşı birinci savunma hattıdır. Prompt enjeksiyonu saldırıları, sistem talimatlarını geçersiz kılabilir, hassas verileri sızdırabilir veya modeli izin verilmeyen davranışlara yönlendirebilir. Özel filtreler ve talimat hiyerarşileri uygulanmadığı sürece, araştırmalar çok uzun bağlam pencerelerini kullanan "çoklu atış" jailbreaklerin etkili olacağını göstermektedir. Ayrıca, homoglifi değişiklikleri veya leetspeak gibi ince düşmanca bozulma saldırıları, modelin kararlarını sessizce değiştirebilir.

---

### C2.1 İstem Enjeksiyonu Savunması

Prompt enjeksiyonu, yapay zeka sistemleri için en büyük risklerden biridir. Bu taktiğe karşı savunmalar, statik desen filtreleri, dinamik sınıflandırıcılar ve talimat hiyerarşisi uygulamasının bir kombinasyonunu kullanır.

 #2.1.1    Seviye: 1    Rol: D/V
 Kullanıcı girdilerinin, sürekli güncellenen bilinen istem enjeksiyonu kalıpları (jailbreak anahtar kelimeleri, "öncekileri yok say", rol yapma zincirleri, dolaylı HTML/URL saldırıları) kütüphanesine karşı tarandığının doğrulanması.
 #2.1.2    Seviye: 1    Rol: D/V
 Sistemin, bağlam penceresi genişletildikten sonra bile, sistem veya geliştirici mesajlarının kullanıcı talimatlarının yerine geçtiği bir talimat hiyerarşisini zorladığını doğrulayın.
 #2.1.3    Seviye: 2    Rol: D/V
 Her model veya prompt-şablon sürümünden önce, başarı oranı eşikleri ve gerilemeler için otomatik engelleyicilerle birlikte, adversarial değerlendirme testlerinin (örneğin, Red Team "çoklu-atış" istemleri) yürütüldüğünü doğrulayın.
 #2.1.4    Seviye: 2    Rol: D
 Üçüncü taraf içeriklerinden (web sayfaları, PDF’ler, e-postalar) gelen istemlerin, ana isteme eklenmeden önce izole bir ayrıştırma bağlamında temizlendiğinin doğrulanması.
 #2.1.5    Seviye: 3    Rol: D/V
 Tüm istemci-filtre kural güncellemelerinin, sınıflandırıcı model sürümlerinin ve engelleme listesi değişikliklerinin sürüm kontrolü altında ve denetlenebilir olduğunu doğrulayın.

---

### C2.2 Karşıt-Örnek Direnci

Doğal Dil İşleme (NLP) modelleri, insanlar tarafından sıklıkla fark edilmeyen ancak modellerin yanlış sınıflandırma eğiliminde olduğu ince karakter veya kelime düzeyindeki bozulmalara karşı hâlâ savunmasızdır.

 #2.2.1    Seviye: 1    Rol: D
 Temel girdi normalizasyon adımlarının (Unicode NFC, homoglif eşlemesi, boşluk kırpma) tokenlemeden önce çalıştığını doğrulayın.
 #2.2.2    Seviye: 2    Rol: D/V
 İstatistiksel anomali tespitinin, dil normlarına göre olağanüstü yüksek düzenleme mesafesine, aşırı tekrar eden tokenlara veya anormal gömme mesafelerine sahip girdileri işaretlediğini doğrulayın.
 #2.2.3    Seviye: 2    Rol: D
 Çıkarım hattının, yüksek riskli uç noktalar için isteğe bağlı olarak adversaryal eğitimle güçlendirilmiş model varyantlarını veya savunma katmanlarını (örneğin, rastgeleleştirme, savunmacı distilasyon) desteklediğini doğrulayın.
 #2.2.4    Seviye: 2    Rol: V
 Şüpheli düşmanca girişlerin karantinaya alındığını, tam yüklerle birlikte kaydedildiğini (KİB'in çıkarılmasından sonra) doğrulayın.
 #2.2.5    Seviye: 3    Rol: D/V
 Dayanıklılık metriklerinin (bilinen saldırı setlerinin başarı oranı) zaman içinde takip edildiğini ve gerilemelerin sürüm engelleyicisini tetiklediğini doğrulayın.

---

### C2.3 Şema, Tür ve Uzunluk Doğrulaması

Bozuk veya aşırı büyük girdiler içeren Yapay Zeka saldırıları, ayrıştırma hatalarına, alanlar arasında istem taşmasına ve kaynak tükenmesine neden olabilir. Kesin araç çağrıları gerçekleştirilirken katı şema uygulaması da ön koşuldur.

 #2.3.1    Seviye: 1    Rol: D
 Her API veya fonksiyon çağrısı uç noktasının açık bir giriş şeması (JSON Şeması, Protobuf veya çok modlu eşdeğeri) tanımladığını ve girdilerin istem oluşturulmadan önce doğrulandığını doğrulayın.
 #2.3.2    Seviye: 1    Rol: D/V
 Girişlerin maksimum token veya byte sınırlarını aşması durumunda güvenli bir hata ile reddedildiğini ve asla sessizce kısaltılmadığını doğrulayın.
 #2.3.3    Seviye: 2    Rol: D/V
 Tür türü denetimlerinin (örneğin, sayısal aralıklar, enum değerleri, görüntü/ses için MIME türleri) sadece istemci kodunda değil, sunucu tarafında da zorunlu kılındığını doğrulayın.
 #2.3.4    Seviye: 2    Rol: D
 Anlamsal doğrulayıcıların (örneğin, JSON Şeması) algoritmik hizmet reddi (DoS) saldırılarını önlemek için sabit zamanda çalıştığını doğrulayın.
 #2.3.5    Seviye: 3    Rol: V
 Doğrulama hatalarının, güvenlik sınıflandırmasına yardımcı olmak için sansürlenmiş veri parçacıkları ve net hata kodlarıyla kaydedildiğini doğrulayın.

---

### C2.4 İçerik ve Politika Tarama

Geliştiriciler, yasaklanmış içerik talep eden (örneğin, yasa dışı talimatlar, nefret söylemi ve telif hakkıyla korunan metinler gibi) sözdizimsel olarak geçerli istemleri tespit edebilmeli ve bunların yayılmasını engellemelidir.

 #2.4.1    Seviye: 1    Rol: D
 Bir içerik sınıflandırıcısının (sıfır atış veya ince ayarlanmış) her girdiyi şiddet, kendine zarar verme, nefret, cinsel içerik ve yasa dışı talepler açısından puanladığını, eşik değerlerinin yapılandırılabilir olduğunu doğrulayın.
 #2.4.2    Seviye: 1    Rol: D/V
 Politikaları ihlal eden girdilerin, standartlaştırılmış reddedilmeler veya güvenli tamamlamalar alacağını ve böylece aşağı akıştaki LLM çağrılarına yayılmayacağını doğrulayın.
 #2.4.3    Seviye: 2    Rol: D
 Tarama modelinin veya kural setinin, yeni gözlemlenen jailbreak veya politika atlatma kalıplarını dahil ederek en az üç aylık dönemlerde yeniden eğitildiğini/güncellendiğini doğrulayın.
 #2.4.4    Seviye: 2    Rol: D
 Kullanıcıya özgü politikaların (yaş, bölgesel yasal kısıtlamalar) taleple çözülme zamanında nitelik tabanlı kurallar aracılığıyla korunduğunu doğrulayın.
 #2.4.5    Seviye: 3    Rol: V
 Tarama günlüklerinin SOC korelasyonu ve gelecekteki kırmızı takım tekrarı için sınıflandırıcı güven skorlarını ve politika kategori etiketlerini içerdiğini doğrulayın.

---

### C2.5 Girdi Hızı Sınırlaması ve Kötüye Kullanım Önleme

Geliştiriciler, giriş hızlarını sınırlayarak ve anormal kullanım kalıplarını tespit ederek AI sistemlerine yönelik kötüye kullanımı, kaynak tükenmesini ve otomatik saldırıları önlemelidir.

 #2.5.1    Seviye: 1    Rol: D/V
 Tüm giriş uç noktaları için kullanıcı başına, IP başına ve API anahtarı başına hız sınırlarının uygulandığını doğrulayın.
 #2.5.2    Seviye: 2    Rol: D/V
 Patlama ve sürekli hız sınırlarının DoS ve kaba kuvvet saldırılarını önleyecek şekilde ayarlandığını doğrulayın.
 #2.5.3    Seviye: 2    Rol: D/V
 Anormal kullanım kalıplarının (örneğin, hızlı istekler, giriş bombardımanı) otomatik engellemeleri veya yükseltmeleri tetiklediğini doğrulayın.
 #2.5.4    Seviye: 3    Rol: V
 Kötüye kullanım önleme kayıtlarının saklandığını ve ortaya çıkan saldırı kalıpları için incelendiğini doğrulayın.

---

### C2.6 Çok Modlu Girdi Doğrulaması

Yapay zeka sistemleri, enjeksiyon, kaçınma veya kaynak kötüye kullanımını önlemek için metin dışı girdiler (görseller, ses, dosyalar) için sağlam doğrulama içermelidir.

 #2.6.1    Seviye: 1    Rol: D
 Tüm metin dışı girdilerin (görseller, sesler, dosyalar) işlenmeden önce tür, boyut ve format açısından doğrulandığını kontrol edin.
 #2.6.2    Seviye: 2    Rol: D/V
 Dosyaların alım öncesinde kötü amaçlı yazılım ve steganografik yükler için tarandığını doğrulayın.
 #2.6.3    Seviye: 2    Rol: D/V
 Görüntü/ses girdilerinin, düşmanca bozulumlar veya bilinen saldırı desenleri açısından kontrol edildiğini doğrulayın.
 #2.6.4    Seviye: 3    Rol: V
 Çok modlu giriş doğrulama hatalarının kaydedildiğini ve inceleme için uyarılar tetiklediğini doğrulayın.

---

### C2.7 Girdi Kökeni ve Atıf

Yapay zeka sistemleri, tüm kullanıcı girdilerinin kaynaklarını izleyerek, etiketleyerek ve denetleyerek denetim, kötüye kullanım takibi ve uyumluluğu desteklemelidir.

 #2.7.1    Seviye: 1    Rol: D/V
 Tüm kullanıcı girdilerinin alınma sırasında meta verilerle (kullanıcı kimliği, oturum, kaynak, zaman damgası, IP adresi) etiketlendiğini doğrulayın.
 #2.7.2    Seviye: 2    Rol: D/V
 İşlenen tüm girdiler için kaynağa ilişkin meta verilerin saklandığını ve denetlenebilir olduğunu doğrulayın.
 #2.7.3    Seviye: 2    Rol: D/V
 Anormal veya güvenilmeyen giriş kaynaklarının işaretlendiğini ve artırılmış denetime veya engellemeye tabi tutulduğunu doğrulayın.

---

### C2.8 Gerçek Zamanlı Uyarlanabilir Tehdit Tespiti

Geliştiriciler, yeni saldırı desenlerine uyum sağlayan ve derlenmiş desen eşlemesi ile gerçek zamanlı koruma sunan gelişmiş tehdit algılama sistemlerini yapay zeka için kullanmalıdır.

 #2.8.1    Seviye: 1    Rol: D/V
 Tehdit tespit kalıplarının, minimum gecikme etkisiyle yüksek performanslı gerçek zamanlı filtreleme için optimize edilmiş regex motorlarına derlendiğini doğrulayın.
 #2.8.2    Seviye: 1    Rol: D/V
 Tehdit algılama sistemlerinin farklı tehdit kategorileri (prompt enjeksiyonu, zararlı içerik, hassas veri, sistem komutları) için ayrı desen kütüphaneleri tuttuğunu doğrulayın.
 #2.8.3    Seviye: 2    Rol: D/V
 Uyarlanabilir tehdit tespitinin, saldırı sıklığı ve başarı oranlarına dayalı olarak tehdit hassasiyetini güncelleyen makine öğrenimi modellerini içerdiğini doğrulayın.
 #2.8.4    Seviye: 2    Rol: D/V
 Gerçek zamanlı tehdit istihbaratı akışlarının, yeni saldırı imzaları ve IOC'ler (Zararlı Faaliyet Göstergeleri) ile desen kütüphanelerini otomatik olarak güncellediğini doğrulayın.
 #2.8.5    Seviye: 3    Rol: D/V
 Tehdit tespiti yanlış pozitif oranlarının sürekli olarak izlendiğini ve desen özgüllüğünün meşru kullanım durumuna müdahaleyi en aza indirmek için otomatik olarak ayarlandığını doğrulayın.
 #2.8.6    Seviye: 3    Rol: D/V
 Bağlamsal tehdit analizinin algılama doğruluğunu artırmak için girdi kaynağını, kullanıcı davranış kalıplarını ve oturum geçmişini dikkate aldığını doğrulayın.
 #2.8.7    Seviye: 3    Rol: D/V
 Tehdit tespiti performans metriklerinin (tespit oranı, işleme gecikmesi, kaynak kullanımı) gerçek zamanlı olarak izlendiği ve optimize edildiği doğrulanmalıdır.

---

### C2.9 Çok Modlu Güvenlik Doğrulama Boru Hattı

Geliştiriciler, metin, görüntü, ses ve diğer AI giriş biçimleri için belirli türde tehdit algılama ve kaynak izolasyonu ile güvenlik doğrulaması sağlamalıdır.

 #2.9.1    Seviye: 1    Rol: D/V
 Her giriş modalitesinin, belgelenmiş tehdit desenlerine (metin: istem enjeksiyonu, görüntüler: steganografi, ses: spektrogram saldırıları) ve tespit eşiklerine sahip özel güvenlik doğrulayıcılarına sahip olduğunu doğrulayın.
 #2.9.2    Seviye: 2    Rol: D/V
 Çok modlu girdilerin, her modül türüne özgü tanımlanmış kaynak sınırlarına (bellek, CPU, işleme süresi) sahip izole kum havuzlarında işlendiğini ve bunun güvenlik politikalarında belgelenmiş olduğunu doğrulayın.
 #2.9.3    Seviye: 2    Rol: D/V
 Çapraz modal saldırı tespitinin, korelasyon kuralları ve uyarı oluşturma ile birden fazla girdi türünü kapsayan (örneğin, görüntülerde steganografik yükler ile metinde istem enjeksiyonu) koordineli saldırıları tanımladığını doğrulayın.
 #2.9.4    Seviye: 3    Rol: D/V
 Çok modlu doğrulama hatalarının, tüm giriş modları, doğrulama sonuçları, tehdit puanları ve SIEM entegrasyonu için yapılandırılmış günlük formatları ile korelasyon analizini içeren ayrıntılı günlük kaydını tetiklediğini doğrulayın.
 #2.9.5    Seviye: 3    Rol: D/V
 Modaliteye özgü içerik sınıflandırıcılarının, belgelenmiş programlara (en az üç aylık) göre yeni tehdit kalıpları, adversaryal örnekler ve temel performans eşiklerinin üzerinde tutulan performans kıyaslamaları ile güncellendiğini doğrulayın.

---

### Referanslar

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

Yapay zeka sistemleri, yetkisiz veya güvensiz model değişikliklerinin üretime ulaşmasını önleyen değişiklik kontrol süreçlerini uygulamalıdır. Bu kontrol, geliştirmeden konuşlandırmaya ve devreden çıkarılmaya kadar tüm yaşam döngüsü boyunca model bütünlüğünü sağlar; bu da hızlı olay yanıtını mümkün kılar ve tüm değişiklikler için hesap verebilirliği sürdürür.

Temel Güvenlik Hedefi: Yalnızca yetkilendirilmiş, doğrulanmış modellerin, bütünlüğü, izlenebilirliği ve kurtarılabilirliği koruyan kontrollü süreçler kullanılarak üretime ulaşması.

---

### C3.1 Model Yetkilendirme ve Bütünlüğü

Sadece doğrulanmış bütünlüğe sahip yetkili modeller üretim ortamlarına ulaşır.

 #3.1.1    Seviye: 1    Rol: D/V
 Tüm model artefaktlarının (ağırlıklar, yapılandırmalar, belirteç çözücüler) dağıtımdan önce yetkili kurumlar tarafından kriptografik olarak imzalandığını doğrulayın.
 #3.1.2    Seviye: 1    Rol: D/V
 Model bütünlüğünün dağıtım anında doğrulandığını ve imza doğrulama hatalarının modelin yüklenmesini engellediğini doğrulayın.
 #3.1.3    Seviye: 2    Rol: D/V
 Model kökeni kayıtlarının, yetkilendiren varlığın kimliğini, eğitim verisi özet değerlerini, geçme/kalma durumu ile doğrulama test sonuçlarını ve oluşturulma zaman damgasını içerdiğini doğrulayın.
 #3.1.4    Seviye: 2    Rol: D/V
 Tüm model varlıklarının semantik sürümleme (MAJOR.MINOR.PATCH) kullandığını ve her sürüm bileşeninin ne zaman artırılacağını belirten belgelenmiş ölçütlerin olduğunu doğrulayın.
 #3.1.5    Seviye: 2    Rol: V
 Bağımlılık takibinin, tüm tüketici sistemlerin hızlı bir şekilde tanımlanmasını sağlayan gerçek zamanlı bir envanter tuttuğunu doğrulayın.

---

### C3.2 Model Doğrulama ve Test Etme

Modeller, dağıtımdan önce tanımlanmış güvenlik ve emniyet doğrulamalarından geçmelidir.

 #3.2.1    Seviye: 1    Rol: D/V
 Modellerin dağıtımdan önce önceden belirlenmiş organizasyonel geçme/kalma eşiklerini içeren girdi doğrulama, çıktı temizleme ve güvenlik değerlendirmelerini kapsayan otomatik güvenlik testlerinden geçirildiğini doğrulayın.
 #3.2.2    Seviye: 1    Rol: D/V
 Doğrulama hatalarının, belgelenmiş iş gerekçeleriyle önceden belirlenmiş yetkili personelin açıkça onay vermesi durumunda model dağıtımını otomatik olarak engellediğini doğrulayın.
 #3.2.3    Seviye: 2    Rol: V
 Test sonuçlarının kriptografik olarak imzalandığını ve doğrulanan belirli model versiyon karmasına değiştirilemez şekilde bağlandığını doğrulayın.
 #3.2.4    Seviye: 2    Rol: D/V
 Acil durum dağıtımlarının, önceden belirlenmiş zaman dilimleri içinde belgeye dayalı güvenlik risk değerlendirmesi ve önceden atanmış bir güvenlik otoritesinden onay gerektirdiğini doğrulayın.

---

### C3.3 Kontrollü Dağıtım ve Geri Alma

Model dağıtımları kontrol edilmeli, izlenmeli ve geri alınabilir olmalıdır.

 #3.3.1    Seviye: 1    Rol: D
 Üretim dağıtımlarının, önceden belirlenmiş hata oranları, gecikme eşikleri veya güvenlik uyarı kriterlerine dayalı otomatik geri alma tetikleyicileri ile kademeli dağıtım mekanizmalarını (kanarya dağıtımları, mavi-yeşil dağıtımlar) uyguladığını doğrulayın.
 #3.3.2    Seviye: 1    Rol: D/V
 Geri alma özelliklerinin, önceden tanımlanmış organizasyonel zaman pencereleri içinde model durumunu (ağırlıklar, yapılandırmalar, bağımlılıklar) tamamıyla atomik olarak eski haline getirdiğini doğrulayın.
 #3.3.3    Seviye: 2    Rol: D/V
 Dağıtım süreçlerinin, model etkinleştirmeden önce kriptografik imzaları doğruladığını ve bütünlük denetim toplamlarını hesapladığını, herhangi bir uyumsuzluk durumunda dağıtımın başarısız olduğunu doğrulayın.
 #3.3.4    Seviye: 2    Rol: D/V
 Acil durum model kapatma özelliklerinin, otomatik devre kesiciler veya manuel kapatma anahtarları aracılığıyla önceden tanımlanmış yanıt süreleri içinde model uç noktalarını devre dışı bırakabildiğini doğrulayın.
 #3.3.5    Seviye: 2    Rol: V
 Geri alma kalıntılarının (önceki model sürümleri, yapılandırmalar, bağımlılıklar) olay müdahalesi için değiştirilemez depolama ile organizasyonel politikalara uygun şekilde saklandığını doğrulayın.

---

### C3.4 Değişiklik Hesap Verebilirliği ve Denetimi

Tüm model yaşam döngüsü değişiklikleri izlenebilir ve denetlenebilir olmalıdır.

 #3.4.1    Seviye: 1    Rol: V
 Tüm model değişikliklerinin (dağıtım, yapılandırma, emeklilik) zaman damgası, doğrulanmış kullanıcı kimliği, değişiklik türü ve önce/sonra durumları dahil olmak üzere değiştirilemez denetim kayıtları oluşturduğunu doğrulayın.
 #3.4.2    Seviye: 2    Rol: D/V
 Denetim günlüğü erişiminin uygun yetkilendirme gerektirdiğini ve tüm erişim girişimlerinin kullanıcı kimliği ve zaman damgası ile kaydedildiğini doğrulayın.
 #3.4.3    Seviye: 2    Rol: D/V
 Prompt şablonlarının ve sistem mesajlarının, zorunlu kod incelemesi ve belirlenmiş inceleyicilerin onayıyla birlikte git depolarında sürüm kontrolünün yapıldığını doğrulayın.
 #3.4.4    Seviye: 2    Rol: V
 Denetim kayıtlarının, saklama süresi içinde herhangi bir zaman damgası için model durumunun tam yeniden yapılandırılmasını sağlamak üzere yeterli ayrıntıyı (model karmaları, yapılandırma anlık görüntüleri, bağımlılık sürümleri) içerdiğini doğrulayın.

---

### C3.5 Güvenli Geliştirme Uygulamaları

Model geliştirme ve eğitim süreçleri, güvenlik ihlallerini önlemek için güvenli uygulamalara uygun olmalıdır.

 #3.5.1    Seviye: 1    Rol: D
 Model geliştirme, test ve üretim ortamlarının fiziksel veya mantıksal olarak ayrı olduğundan emin olun. Ortak altyapıları yoktur, farklı erişim kontrollerine sahiptirler ve izole veri depoları bulunur.
 #3.5.2    Seviye: 1    Rol: D
 Model eğitimi ve ince ayarının, kontrol edilen ağ erişimine sahip izole ortamlarda gerçekleştiğini doğrulayın.
 #3.5.3    Seviye: 1    Rol: D/V
 Eğitim veri kaynaklarının, model geliştirme öncesinde belgelenmiş devriye zinciriyle birlikte bütünlük kontrolleri aracılığıyla doğrulandığını ve güvenilir kaynaklar tarafından doğrulandığını teyit edin.
 #3.5.4    Seviye: 2    Rol: D
 Model geliştirme eserlerinin (hiperparametreler, eğitim betikleri, yapılandırma dosyaları) sürüm kontrolünde saklandığını ve eğitimde kullanılmadan önce eş inceleme onayı gerektirdiğini doğrulayın.

---

### C3.6 Model Emekliliği ve Hizmet Dışı Bırakılması

Modeller, artık gerekmediğinde veya güvenlik sorunları tespit edildiğinde güvenli bir şekilde kullanımdan kaldırılmalıdır.

 #3.6.1    Seviye: 1    Rol: D
 Model emeklilik süreçlerinin otomatik olarak bağımlılık grafiklerini taradığını, tüm tüketici sistemleri belirlediğini ve hizmetten kaldırmadan önce önceden kararlaştırılmış bildirim süreleri sağladığını doğrulayın.
 #3.6.2    Seviye: 1    Rol: D/V
 Emekliye ayrılmış model varlıklarının, doğrulanmış imha sertifikaları ile belgelenmiş veri saklama politikalarına uygun olarak kriptografik silme veya çok geçişli üzerine yazma yöntemleriyle güvenli bir şekilde silindiğini doğrulayın.
 #3.6.3    Seviye: 2    Rol: V
 Model emeklilik olaylarının zaman damgası ve işlemci kimliği ile kaydedildiğini ve model imzalarının yeniden kullanımını önlemek için iptal edildiğini doğrulayın.
 #3.6.4    Seviye: 2    Rol: D/V
 Acil durumda modelin emekliye ayrılmasının, kritik güvenlik açıkları keşfedildiğinde otomatik durdurma anahtarları aracılığıyla önceden belirlenmiş acil müdahale süreleri içinde model erişimini devre dışı bırakabileceğini doğrulayın.

---

### Referanslar

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

## C4 Altyapısı, Yapılandırma ve Dağıtım Güvenliği

### Kontrol Amacı

Yapay zeka altyapısı, güvenli yapılandırma, çalışma zamanı izolasyonu, güvenilir dağıtım hatları ve kapsamlı izleme yoluyla ayrıcalık yükseltme, tedarik zinciri manipülasyonu ve yanal hareketlere karşı güçlendirilmelidir. Sadece yetkili, doğrulanmış altyapı bileşenleri ve yapılandırmaları, güvenlik, bütünlük ve denetlenebilirliği koruyan kontrollü süreçler aracılığıyla üretime ulaşır.

Temel Güvenlik Hedefi: Yalnızca kriptografik olarak imzalanmış, güvenlik açıkları taranmış altyapı bileşenleri, güvenlik politikalarını uygulayan ve değiştirilemez denetim kayıtlarını koruyan otomatik doğrulama hatları aracılığıyla üretime ulaşır.

---

### C4.1 Çalışma Zamanı Ortamı İzolasyonu

Çekirdek seviyesi izolasyon ilkelikleri ve zorunlu erişim kontrolleri yoluyla konteyner kaçışlarını ve ayrıcalık yükseltmelerini önleyin.

 #4.1.1    Seviye: 1    Rol: D/V
 Tüm yapay zeka konteynerlerinin, güvenlik temellerinde belgelenmiş CAP_SETUID, CAP_SETGID ve açıkça gerekli olan yetenekler dışındaki TÜM Linux yeteneklerini devre dışı bıraktığını doğrulayın.
 #4.1.2    Seviye: 1    Rol: D/V
 Seccomp profillerinin, önceden onaylanmış izin listelerinde (allowlist) olmayan tüm sistem çağrılarını (syscall) engellediğini, ihlallerin konteynerin sonlanmasına ve güvenlik uyarılarının oluşturulmasına yol açtığını doğrulayın.
 #4.1.3    Seviye: 2    Rol: D/V
 AI iş yüklerinin salt okunur kök dosya sistemleri, geçici veriler için tmpfs ve kalıcı veriler için noexec bağlama seçenekleri uygulanmış isimlendirilmiş birimlerle çalıştığını doğrulayın.
 #4.1.4    Seviye: 2    Rol: D/V
 eBPF tabanlı çalışma zamanı izleme (Falco, Tetragon veya eşdeğeri) ayrıcalık yükseltme girişimlerini tespit eder ve kuruluşun müdahale süresi gereksinimleri dahilinde hatalı süreçleri otomatik olarak sonlandırdığını doğrulayın.
 #4.1.5    Seviye: 3    Rol: D/V
 Yüksek riskli AI iş yüklerinin, doğrulama kanıtı ile birlikte donanım izoleli ortamlarda (Intel TXT, AMD SVM veya özel çıplak-metal düğümler) çalıştığını doğrulayın.

---

### C4.2 Güvenli Derleme ve Dağıtım Hatları

Yeniden üretilebilir derlemeler ve imzalanmış artefaktlar aracılığıyla kriptografik bütünlüğü ve tedarik zinciri güvenliğini sağlayın.

 #4.2.1    Seviye: 1    Rol: D/V
 Her commit'te altyapı-kod olarak (infrastructure-as-code) tfsec, Checkov veya Terrascan gibi araçlarla tarandığını doğrulayın, CRITICAL veya HIGH şiddet derecesine sahip bulgularla yapılan birleşmeleri engelleyin.
 #4.2.2    Seviye: 1    Rol: D/V
 Konteyner derlemelerinin, derlemeler arasında aynı SHA256 karmalarına sahip olacak şekilde yeniden oluşturulabilir olduğunu doğrulayın ve Sigstore ile imzalanmış SLSA Seviye 3 köken kanıtları oluşturun.
 #4.2.3    Seviye: 2    Rol: D/V
 Konteyner görüntülerinin, kayıt defterine itmeden önce CycloneDX veya SPDX SBOM'larını gömülü olarak içerdiğini ve Cosign ile imzalandığını doğrulayın; imzasız görüntüler dağıtımda reddedilsin.
 #4.2.4    Seviye: 2    Rol: D/V
 CI/CD işlemlerinin, organizasyonun güvenlik politikası sınırlarını aşmayan sürelerde geçerliliğe sahip olan HashiCorp Vault, AWS IAM Rolleri veya Azure Yönetilen Kimlikler tarafından sağlanan OIDC belirteçlerini kullandığını doğrulayın.
 #4.2.5    Seviye: 2    Rol: D/V
 Cosign imzalarının ve SLSA köken bilgilerinin, konteyner yürütülmeden önce dağıtım sürecinde doğrulandığını ve doğrulama hatalarının dağıtımın başarısız olmasına neden olduğunu doğrulayın.
 #4.2.6    Seviye: 2    Rol: D/V
 Yapı ortamlarının, kalıcı depolama olmadan ve üretim VPC’lerinden ağ izolasyonuna sahip geçici konteynerler veya VM’lerde çalıştığını doğrulayın.

---

### C4.3 Ağ Güvenliği ve Erişim Kontrolü

Varsayılan reddet politikaları ve şifreli iletişimle sıfır güven ağı uygulayın.

 #4.3.1    Seviye: 1    Rol: D/V
 Kubernetes NetworkPolicies veya herhangi bir eşdeğerinin, gerekli portlar (443, 8080 vb.) için açıkça izin kurallarıyla varsayılan olarak gelen/giden trafiği engelleyen (default-deny) bir yapılandırmayı uyguladığını doğrulayın.
 #4.3.2    Seviye: 1    Rol: D/V
 SSH (port 22), RDP (port 3389) ve bulut metadata uç noktalarının (169.254.169.254) engellendiğini veya sertifika tabanlı kimlik doğrulaması gerektirdiğini doğrulayın.
 #4.3.3    Seviye: 2    Rol: D/V
 Çıkış trafiğinin, alan adı izin listeleri kullanılarak HTTP/HTTPS proxyleri (Squid, Istio veya bulut NAT geçitleri) üzerinden filtrelendiğini ve engellenen isteklerin kayıt altına alındığını doğrulayın.
 #4.3.4    Seviye: 2    Rol: D/V
 Hizmetler arası iletişimin, kurumsal politikaya uygun olarak döndürülen sertifikalarla karşılıklı TLS kullandığını ve sertifika doğrulamasının (skip-verify bayrakları olmadan) zorunlu tutulduğunu doğrulayın.
 #4.3.5    Seviye: 2    Rol: D/V
 Yapay zeka altyapısının, doğrudan internet erişimi olmayan ayrı VPC/VNet’lerde çalıştığını ve yalnızca NAT ağ geçitleri veya bastion hostlar aracılığıyla iletişim kurduğunu doğrulayın.

---

### C4.4 Gizli Bilgi & Kriptografik Anahtar Yönetimi

Kimlik bilgilerini donanım destekli depolama ve sıfır güven erişimi ile otomatik döndürme yoluyla koruyun.

 #4.4.1    Seviye: 1    Rol: D/V
 Şifrelerin, AES-256 kullanılarak dinlenme sırasında şifreleme ile HashiCorp Vault, AWS Secrets Manager, Azure Key Vault veya Google Secret Manager içinde saklandığını doğrulayın.
 #4.4.2    Seviye: 1    Rol: D/V
 Kriptografik anahtarların, kurumsal kriptografik politikaya uygun anahtar rotasyonu ile birlikte FIPS 140-2 Seviye 2 HSM'lerde (AWS CloudHSM, Azure Dedicated HSM) oluşturulduğunu doğrulayın.
 #4.4.3    Seviye: 2    Rol: D/V
 Personel değişiklikleri veya güvenlik olaylarıyla tetiklenen anında rotasyon ile sıfır kesinti süreli dağıtımda sırların otomatik olarak döndürüldüğünü doğrulayın.
 #4.4.4    Seviye: 2    Rol: D/V
 Konteyner imajlarının, API anahtarları, parolalar veya sertifikalar içeren derlemeleri engelleyen araçlarla (GitLeaks, TruffleHog veya detect-secrets) tarandığını doğrulayın.
 #4.4.5    Seviye: 2    Rol: D/V
 Üretim gizli erişiminin donanım tokenları (YubiKey, FIDO2) ile MFA gerektirdiğini ve kullanıcı kimlikleri ile zaman damgalarıyla değiştirilemeyen denetim günlükleri tarafından kaydedildiğini doğrulayın.
 #4.4.6    Seviye: 2    Rol: D/V
 Gizli bilgilerinin Kubernetes gizli bilgileri aracılığıyla, monte edilmiş hacimlerle veya init konteynerleriyle enjekte edildiğini doğrulayın ve gizli bilgilerin asla ortam değişkenlerinde veya imajlarda gömülü olmadığından emin olun.

---

### C4.5 AI İş Yükü Kum Havuzu ve Doğrulama

Kapsamlı davranış analizi ile güvensiz AI modellerini güvenli kum havuzlarında izole edin.

 #4.5.1    Seviye: 1    Rol: D/V
 Harici AI modellerinin gVisor, mikroVM’ler (örneğin Firecracker, CrossVM) veya --security-opt=no-new-privileges ve --read-only bayrakları ile Docker konteynerlerinde çalıştığını doğrulayın.
 #4.5.2    Seviye: 1    Rol: D/V
 Sandbox ortamlarının ağ bağlantısının olmadığını (--network=none) veya yalnızca localhost erişimine izin verildiğini ve tüm dış taleplerin iptables kurallarıyla engellendiğini doğrulayın.
 #4.5.3    Seviye: 2    Rol: D/V
 AI model doğrulamasının, organizasyon tarafından tanımlanmış test kapsamı ve davranış analizi ile birlikte otomatik kırmızı takım testlerini içerdiğini doğrulayın ve arka kapı tespiti yapın.
 #4.5.4    Seviye: 2    Rol: D/V
 Bir yapay zeka modeli üretime alınmadan önce, sandbox sonuçlarının yetkili güvenlik personeli tarafından kriptografik olarak imzalandığını ve değiştirilemez denetim kayıtlarında saklandığını doğrulayın.
 #4.5.5    Seviye: 2    Rol: D/V
 Değerlendirmeler arasında samba kutusu ortamlarının altın görüntülerden tamamen dosya sistemi ve bellek temizliği ile yok edilip yeniden oluşturulduğunu doğrulayın.

---

### C4.6 Altyapı Güvenliği İzleme

Altyapıyı sürekli olarak otomatik iyileştirme ve gerçek zamanlı uyarılar ile tarayın ve izleyin.

 #4.6.1    Seviye: 1    Rol: D/V
 Konteyner imajlarının, kurumsal risk eşiklerine göre CRITICAL (KRİTİK) güvenlik açıkları bulunanların dağıtımını engelleyecek şekilde, kurumsal programlara uygun olarak tarandığını doğrulayın.
 #4.6.2    Seviye: 1    Rol: D/V
 Altyapının, kuruluş tarafından tanımlanan uyumluluk eşik değerleri ve başarısız kontroller için otomatik düzeltme ile CIS Kriterleri veya NIST 800-53 kontrollerini geçtiğini doğrulayın.
 #4.6.3    Seviye: 2    Rol: D/V
 Yüksek şiddetteki güvenlik açıklarının, kurumsal risk yönetimi takvimlerine uygun olarak yamalandığını ve aktif olarak sömürülen CVE'ler için acil durum prosedürlerinin uygulandığını doğrulayın.
 #4.6.4    Seviye: 2    Rol: V
 Güvenlik uyarılarının CEF veya STIX/TAXII formatlarını kullanarak SIEM platformlarıyla (Splunk, Elastic veya Sentinel) otomatik zenginleştirme ile entegre olduğunu doğrulayın.
 #4.6.5    Seviye: 3    Rol: V
 Altyapı metriklerinin SLA panoları ve üst yönetim raporlaması ile birlikte izleme sistemlerine (Prometheus, DataDog) aktarıldığını doğrulayın.
 #4.6.6    Seviye: 2    Rol: D/V
 Organizasyonel izleme gereksinimlerine göre, yetkisiz değişiklikler için otomatik geri alma ile yapılandırma sapmasının araçlar (Chef InSpec, AWS Config) kullanılarak tespit edildiğini doğrulayın.

---

### C4.7 AI Altyapı Kaynak Yönetimi

Kaynak tükenme saldırılarını önleyin ve kotalar ile izleme yoluyla adil kaynak tahsisini sağlayın.

 #4.7.1    Seviye: 1    Rol: D/V
 GPU/TPU kullanımının, kuruluş tarafından belirlenen eşik değerlerde tetiklenen uyarılarla izlenip izlenmediğini ve kapasite yönetimi politikalarına dayalı olarak otomatik ölçeklendirme veya yük dengelemenin etkinleştirilip etkinleştirilmediğini doğrulayın.
 #4.7.2    Seviye: 1    Rol: D/V
 Yapay zeka iş yükü metriklerinin (çıkarım gecikmesi, işlem hacmi, hata oranları) kurumsal izleme gereksinimlerine uygun olarak toplandığını ve altyapı kullanım oranlarıyla ilişkilendirildiğini doğrulayın.
 #4.7.3    Seviye: 2    Rol: D/V
 Kubernetes ResourceQuotas veya eşdeğerinin, organizasyonun kaynak tahsis politikalarına uygun olarak bireysel iş yüklerini sınırlandırdığını ve katı sınırların uygulandığını doğrulayın.
 #4.7.4    Seviye: 2    Rol: V
 Maliyet izleme sisteminin, organizasyonun bütçe eşiklerine dayalı uyarılar ve bütçe aşımı durumları için otomatik kontrollerle birlikte, iş yükü/kiracı başına harcamayı izlediğini doğrulayın.
 #4.7.5    Seviye: 3    Rol: V
 Kapasite planlamasının, örgütsel olarak tanımlanmış tahmin dönemleriyle tarihsel verileri kullandığını ve talep desenlerine dayalı otomatik kaynak sağlama yaptığını doğrulayın.
 #4.7.6    Seviye: 2    Rol: D/V
 Kaynak tükenmesinin, kapasite politikalarına dayalı hız sınırlandırma ve iş yükü izolasyonu dahil olmak üzere, organizasyon yanıt gereksinimlerine uygun olarak devre kesicileri tetiklediğini doğrulayın.

---

### C4.8 Ortam Ayrımı ve Terfi Kontrolleri

Otomatik tanıtım kapıları ve güvenlik doğrulaması ile katı ortam sınırlarını zorunlu kılın.

 #4.8.1    Seviye: 1    Rol: D/V
 Dev/test/prod ortamlarının ayrı VPC/VNetlerde çalıştığını ve ortak IAM rolleri, güvenlik grupları veya ağ bağlantısı bulunmadığını doğrulayın.
 #4.8.2    Seviye: 1    Rol: D/V
 Çevre terfisinin, organizasyon tarafından tanımlanmış yetkili kişilerden kriptografik imzalar ve değiştirilemez denetim kayıtları ile onay gerektirdiğini doğrulayın.
 #4.8.3    Seviye: 2    Rol: D/V
 Üretim ortamlarının SSH erişimini engellediğini, hata ayıklama uç noktalarını devre dışı bıraktığını ve acil durumlar hariç olmak üzere organizasyonun önceden bildirim gereksinimleri ile değişiklik taleplerini zorunlu kıldığını doğrulayın.
 #4.8.4    Seviye: 2    Rol: D/V
 Altyapı-kod olarak değişikliklerin, ana dal ile birleştirilmeden önce otomatik test ve güvenlik taraması ile eş incelemesi gerektirdiğini doğrulayın.
 #4.8.5    Seviye: 2    Rol: D/V
 Üretim dışı verilerin, kurumsal gizlilik gereksinimlerine uygun olarak anonimleştirildiğini, sentetik veri üretimini veya KİB kaldırma ile tam veri maskelenmesini doğrulayın.
 #4.8.6    Seviye: 2    Rol: D/V
 Onay için sıfır KRİTİK bulgu gerektiren otomatik güvenlik testlerinin (SAST, DAST, konteyner taraması) terfi kapılarına dahil edildiğini doğrulayın.

---

### C4.9 Altyapı Yedekleme ve Kurtarma

Altyapı dayanıklılığını otomatik yedeklemeler, test edilmiş kurtarma prosedürleri ve felaket kurtarma yetenekleri ile sağlayın.

 #4.9.1    Seviye: 1    Rol: D/V
 Altyapı yapılandırmalarının, 3-2-1 yedekleme stratejisi uygulaması ile teşkilatın yedekleme programlarına uygun olarak coğrafi olarak ayrı bölgelere yedeklendiğini doğrulayın.
 #4.9.2    Seviye: 2    Rol: D/V
 Yedekleme sistemlerinin fidye yazılımı koruması için ayrı kimlik bilgileri ve hava aralıklı depolama ile izole ağlarda çalıştığını doğrulayın.
 #4.9.3    Seviye: 2    Rol: V
 Kurtarma prosedürlerinin, organizasyonel programlara göre RTO ve RPO hedeflerinin organizasyon gereksinimlerini karşılayacak şekilde otomatik testler yoluyla test edilip doğrulandığını teyit edin.
 #4.9.4    Seviye: 3    Rol: V
 Felaket kurtarma işleminin, model ağırlıklarının geri yüklenmesi, GPU kümesi yeniden inşası ve hizmet bağımlılığı eşlemesi içeren yapay zeka özgü çalışma kitaplarını (runbook) kapsadığını doğrulayın.

---

### C4.10 Altyapı Uyumu ve Yönetişimi

Sürekli değerlendirme, dokümantasyon ve otomatik kontroller aracılığıyla düzenleyici uyumu sürdürün.

 #4.10.1    Seviye: 2    Rol: D/V
 Altyapı uyumluluğunun, SOC 2, ISO 27001 veya FedRAMP kontrollerine karşı kurumsal takvimlere uygun olarak otomatik kanıt toplama ile değerlendirildiğini doğrulayın.
 #4.10.2    Seviye: 2    Rol: V
 Altyapı dokümantasyonunun, organizasyonel değişiklik yönetimi gereksinimlerine göre güncellenmiş ağ diyagramları, veri akış haritaları ve tehdit modellerini içerdiğini doğrulayın.
 #4.10.3    Seviye: 3    Rol: D/V
 Altyapı değişikliklerinin, yüksek riskli modifikasyonlar için düzenleyici onay iş akışlarıyla birlikte otomatik uyumluluk etki değerlendirmesine tabi tutulduğunu doğrulayın.

---

### C4.11 Yapay Zeka Donanım Güvenliği

GPU'lar, TPU'lar ve özel AI hızlandırıcılar dahil olmak üzere AI'ye özgü donanım bileşenlerini güvence altına alın.

 #4.11.1    Seviye: 2    Rol: D/V
 AI hızlandırıcı firmware'inin (GPU BIOS, TPU firmware) kriptografik imzalarla doğrulandığını ve organizasyonun yama yönetimi zaman çizelgelerine göre güncellendiğini doğrulayın.
 #4.11.2    Seviye: 2    Rol: D/V
 İş yükü yürütülmeden önce, AI hızlandırıcı bütünlüğünün TPM 2.0, Intel TXT veya AMD SVM kullanılarak donanım doğrulamasıyla doğrulandığını teyit edin.
 #4.11.3    Seviye: 2    Rol: D/V
 İşler arasında bellek temizliği ile SR-IOV, MIG (Çoklu Örnek GPU) veya eşdeğer donanım bölümlendirmesi kullanarak GPU belleğinin iş yükleri arasında izole olduğunu doğrulayın.
 #4.11.4    Seviye: 3    Rol: V
 Yapay zeka donanımı tedarik zincirinin, üretici sertifikalarıyla köken doğrulaması ve müdahale tespit edilebilir ambalaj doğrulaması içerdiğini doğrulayın.
 #4.11.5    Seviye: 3    Rol: D/V
 Donanım güvenlik modüllerinin (HSM) AI model ağırlıklarını ve kriptografik anahtarları FIPS 140-2 Seviye 3 veya Common Criteria EAL4+ sertifikası ile koruduğunu doğrulayın.

---

### C4.12 Kenar ve Dağıtılmış Yapay Zeka Altyapısı

Uç bilişim, federated learning ve çoklu site mimarileri dahil olmak üzere güvenli dağıtılmış AI dağıtımları.

 #4.12.1    Seviye: 2    Rol: D/V
 Edge AI cihazlarının, kurumsal sertifika yönetim politikası doğrultusunda döndürülen cihaz sertifikaları kullanılarak karşılıklı TLS ile merkezi altyapıya doğrulandığını kontrol edin.
 #4.12.2    Seviye: 2    Rol: D/V
 Uç cihazların, doğrulanmış imzalarla güvenli önyükleme gerçekleştirdiğini ve firmware düşürme saldırılarını önleyen geri alma koruması uyguladığını doğrulayın.
 #4.12.3    Seviye: 3    Rol: D/V
 Dağıtık yapay zeka koordinasyonunun, katılımcı doğrulaması ve kötü niyetli düğüm tespiti ile birlikte Bizans hata toleranslı uzlaşma algoritmaları kullandığını doğrulayın.
 #4.12.4    Seviye: 3    Rol: D/V
 Uçtan buluta iletişimin bant genişliği sınırlandırması, veri sıkıştırma ve güvenli yerel depolama ile çevrimdışı çalışma yeteneklerini içerdiğini doğrulayın.

---

### C4.13 Çoklu Bulut ve Hibrit Altyapı Güvenliği

Çoklu bulut sağlayıcıları ve hibrit bulut-yerel dağıtımlarda güvenli AI iş yüklerini koruyun.

 #4.13.1    Seviye: 2    Rol: D/V
 Çoklu bulut AI dağıtımlarının, sağlayıcılar arasında merkezi politika yönetimi ile bulut bağımsız kimlik federasyonu (OIDC, SAML) kullandığını doğrulayın.
 #4.13.2    Seviye: 2    Rol: D/V
 Çapraz bulut veri transferinin müşteri tarafından yönetilen anahtarlarla uçtan uca şifreleme kullandığını ve veri ikametgahı kontrollerinin her yargı bölgesine göre uygulandığını doğrulayın.
 #4.13.3    Seviye: 2    Rol: D/V
 Hibrit bulut yapay zeka iş yüklerinin, birleşik izleme ve uyarı sistemiyle yerinde ve bulut ortamlarında tutarlı güvenlik politikalarını uyguladığını doğrulayın.
 #4.13.4    Seviye: 3    Rol: V
 Bulut sağlayıcı bağımlılığını önlemenin taşınabilir altyapı-kod olarak, standartlaştırılmış API'ler ve format dönüştürme araçları ile veri dışa aktarım yeteneklerini içerdiğini doğrulayın.
 #4.13.5    Seviye: 3    Rol: V
 Çoklu bulut maliyet optimizasyonunun, kaynak yayılmasını önleyen güvenlik kontrollerini ve yetkisiz bulutlar arası veri transferi ücretlerini içerdiğini doğrulayın.

---

### C4.14 Altyapı Otomasyonu ve GitOps Güvenliği

AI altyapı yönetimi için güvenli altyapı otomasyon boru hatları ve GitOps iş akışları.

 #4.14.1    Seviye: 2    Rol: D/V
 GitOps depolarının, main dallarına doğrudan push yapılmasını engelleyen branş koruma kuralları ve GPG anahtarlarıyla imzalanmış commitler gerektirdiğini doğrulayın.
 #4.14.2    Seviye: 2    Rol: D/V
 Altyapı otomasyonunun, yetkisiz değişiklikler için organizasyonel yanıt gereksinimlerine göre tetiklenen otomatik iyileştirme ve geri alma yetenekleri ile birlikte sapma tespiti içerdiğini doğrulayın.
 #4.14.3    Seviye: 2    Rol: D/V
 Otomatik altyapı sağlama işleminin, uygun olmayan yapılandırmalar için dağıtımı engelleyen güvenlik politikası doğrulamasını içerdiğini doğrulayın.
 #4.14.4    Seviye: 2    Rol: D/V
 Altyapı otomasyon sırlarının otomatik rotasyon ile dış gizli operatörler (External Secrets Operator, Bank-Vaults) aracılığıyla yönetildiğini doğrulayın.
 #4.14.5    Seviye: 3    Rol: V
 Kendi kendini iyileştiren altyapının, otomatik olay müdahalesi ve paydaş bildirim iş akışlarıyla güvenlik olayı korelasyonu içerdiğini doğrulayın.

---

### C4.15 Kuantum Dirençli Altyapı Güvenliği

Kuantum bilgisayar tehditlerine karşı kuantum sonrası kriptografi ve kuantum güvenli protokoller ile AI altyapısını hazırlayın.

 #4.15.1    Seviye: 3    Rol: D/V
 AI altyapısının anahtar değişimi ve dijital imzalar için NIST onaylı kuantum sonrası kriptografik algoritmaları (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) uyguladığını doğrulayın.
 #4.15.2    Seviye: 3    Rol: D/V
 Kuantum anahtar dağıtım (QKD) sistemlerinin, kuantum güvenli anahtar yönetim protokolleriyle yüksek güvenlikli yapay zeka iletişimleri için uygulandığını doğrulayın.
 #4.15.3    Seviye: 3    Rol: D/V
 Kriptografik çeviklik frameworklerinin, otomatik sertifika ve anahtar döndürme ile yeni kuantum sonrası algoritmalara hızlı geçişi sağladığını doğrulayın.
 #4.15.4    Seviye: 3    Rol: V
 Kuantum tehdit modellemesinin, belgelenmiş geçiş zaman çizelgeleri ve risk değerlendirmeleri ile birlikte kuantum saldırılarına karşı yapay zeka altyapısının zayıflıklarını değerlendirdiğini doğrulayın.
 #4.15.5    Seviye: 3    Rol: D/V
 Karma klasik-kuantum kriptografik sistemlerin kuantum geçiş dönemi sırasında çok katmanlı savunma sağladığını performans izleme ile doğrulayın.

---

### C4.16 Gizli Hesaplama ve Güvenli Alanlar

Donanım tabanlı güvenilir yürütme ortamları ve gizli hesaplama teknolojileri kullanarak AI iş yüklerini ve model ağırlıklarını koruyun.

 #4.16.1    Seviye: 3    Rol: D/V
 Hassas AI modellerinin, şifreli bellek ve onay doğrulaması ile Intel SGX muhafazalarında, AMD SEV-SNP veya ARM TrustZone içinde çalıştığını doğrulayın.
 #4.16.2    Seviye: 3    Rol: D/V
 Gizli konteynerlerin (Kata Containers, gizli hesaplama ile gVisor) donanım destekli bellek şifrelemesi ile AI iş yüklerini izole ettiğini doğrulayın.
 #4.16.3    Seviye: 3    Rol: D/V
 AI modelleri yüklemeden önce, uzak doğrulamanın yürütme ortamının özgünlüğüne dair kriptografik kanıtla enclave bütünlüğünü doğruladığını kontrol edin.
 #4.16.4    Seviye: 3    Rol: D/V
 Gizli AI çıkarım hizmetlerinin, mühürlenmiş model ağırlıkları ve korumalı yürütme ile şifreli hesaplama yoluyla model çıkarımını engellediğini doğrulayın.
 #4.16.5    Seviye: 3    Rol: D/V
 Güvenilir yürütme ortamı orkestrasyonunun, uzak doğrulama ve şifreli iletişim kanalları ile güvenli bölge yaşam döngüsünü yönettiğini doğrulayın.
 #4.16.6    Seviye: 3    Rol: D/V
 Güvenli çok taraflı hesaplamanın (SMPC), bireysel veri setlerini veya model parametrelerini açığa çıkarmadan işbirlikçi yapay zeka eğitimi sağlamasını doğrulayın.

---

### C4.17 Sıfır Bilgi Altyapısı

Hassas bilgileri açığa çıkarmadan gizlilik korumalı AI doğrulama ve kimlik doğrulama için sıfır bilgi kanıtı sistemleri uygulayın.

 #4.17.1    Seviye: 3    Rol: D/V
 Sıfır bilgi ispatlarının (ZK-SNARKs, ZK-STARKs) model ağırlıklarını veya eğitim verilerini açığa çıkarmadan yapay zeka model bütünlüğünü ve eğitim kaynağını doğruladığını teyit edin.
 #4.17.2    Seviye: 3    Rol: D/V
 ZK tabanlı kimlik doğrulama sistemlerinin, kimlikle ilgili bilgileri ifşa etmeden AI hizmetleri için gizliliği koruyan kullanıcı doğrulaması sağladığını doğrulayın.
 #4.17.3    Seviye: 3    Rol: D/V
 Özel küme kesişimi (PSI) protokollerinin, bireysel veri setlerini açığa çıkarmadan federatif yapay zeka için güvenli veri eşleştirme sağladığını doğrulayın.
 #4.17.4    Seviye: 3    Rol: D/V
 Sıfır-bilgi makine öğrenimi (ZKML) sistemlerinin, doğru hesaplamanın kriptografik kanıtıyla doğrulanabilir yapay zeka çıkarımlarını mümkün kıldığını doğrulayın.
 #4.17.5    Seviye: 3    Rol: D/V
 ZK-rollupların toplu doğrulama ve azaltılmış hesaplama yükü ile ölçeklenebilir, gizliliği koruyan AI işlem işleme sağladığını doğrulayın.

---

### C4.18 Yan Kanal Saldırısı Önleme

Zamanlama, güç, elektromanyetik ve önbellek tabanlı yan kanal saldırılarından dolayı hassas bilgilerin sızmasını engellemek için AI altyapısını koruyun.

 #4.18.1    Seviye: 3    Rol: D/V
 AI çıkarım zamanlamasının, zaman tabanlı model çıkarma saldırılarını önlemek için sabit zaman algoritmaları ve dolgu kullanılarak normalize edildiğini doğrulayın.
 #4.18.2    Seviye: 3    Rol: D/V
 Güç analizi korumasının, yapay zeka donanımı için gürültü enjeksiyonunu, güç hattı filtrelemesini ve rastgeleleştirilmiş yürütme desenlerini içerdiğini doğrulayın.
 #4.18.3    Seviye: 3    Rol: D/V
 Önbellek tabanlı yan kanal saldırılarını önleme yöntemlerinin, bilgi sızıntısını engellemek için önbellek bölümlendirmesi, rastgeleleştirme ve temizleme (flush) komutları kullandığını doğrulayın.
 #4.18.4    Seviye: 3    Rol: D/V
 Elektromanyetik yayılım korumasının TEMPEST tarzı saldırıları önlemek için koruma, sinyal filtreleme ve rastgele işleme içermesini doğrulayın.
 #4.18.5    Seviye: 3    Rol: D/V
 Mikro mimari yan kanal savunmalarının spekülatif yürütme kontrolleri ve bellek erişim deseni gizleme yöntemlerini içerdiğini doğrulayın.

---

### C4.19 Nörömorfik ve Özelleşmiş AI Donanım Güvenliği

Nöral mimari çipler, FPGA'lar, özel ASIC'ler ve optik hesaplama sistemleri dahil olmak üzere gelişmekte olan yapay zeka donanım mimarilerini güvence altına alın.

 #4.19.1    Seviye: 3    Rol: D/V
 Nöromorfik çip güvenliğinin, spike pattern şifrelemesi, sinaptik ağırlık koruması ve donanım tabanlı öğrenme kuralı doğrulamasını içerdiğini doğrulayın.
 #4.19.2    Seviye: 3    Rol: D/V
 FPGA tabanlı yapay zeka hızlandırıcılarının bitstream şifrelemesi, müdahale önleyici mekanizmalar ve doğrulanmış güncellemelerle güvenli yapılandırma yüklemesini uyguladığını doğrulayın.
 #4.19.3    Seviye: 3    Rol: D/V
 Özel ASIC güvenliğinin, üzerinde çip güvenlik işlemcileri, donanım tabanlı güven kökü ve müdahale tespitli güvenli anahtar depolamayı içerdiğini doğrulayın.
 #4.19.4    Seviye: 3    Rol: D/V
 Optik hesaplama sistemlerinin kuantum güvenli optik şifreleme, güvenli fotonik anahtarlama ve korumalı optik sinyal işleme uyguladığını doğrulayın.
 #4.19.5    Seviye: 3    Rol: D/V
 Hibrit analog-dijital yapay zeka çiplerinin güvenli analog hesaplama, korumalı ağırlık depolama ve kimlik doğrulamalı analogdan dijitale dönüştürmeyi içerdiğini doğrulayın.

---

### C4.20 Gizliliği Koruyan Hesaplama Altyapısı

AI işleme ve analiz sırasında hassas verileri korumak için gizliliği koruyan hesaplama altyapı kontrollerini uygulayın.

 #4.20.1    Seviye: 3    Rol: D/V
 Homomorfik şifreleme altyapısının, kriptografik bütünlük doğrulaması ve performans izleme ile hassas Yapay Zeka iş yükleri üzerinde şifrelenmiş hesaplamaya olanak sağladığını doğrulayın.
 #4.20.2    Seviye: 3    Rol: D/V
 Özel bilgi alma sistemlerinin, erişim desenlerinin kriptografik korumasıyla sorgu desenlerini ifşa etmeden veritabanı sorgularını mümkün kıldığını doğrulayın.
 #4.20.3    Seviye: 3    Rol: D/V
 Güvenli çok taraflı hesaplama protokollerinin, bireysel girdileri veya ara hesaplamaları açığa çıkarmadan gizliliği koruyan AI çıkarımı sağladığını doğrulayın.
 #4.20.4    Seviye: 3    Rol: D/V
 Gizliliği koruyan anahtar yönetiminin, donanım destekli koruma ile dağıtık anahtar oluşturma, eşik kriptografi ve güvenli anahtar döndürmeyi içerdiğini doğrulayın.
 #4.20.5    Seviye: 3    Rol: D/V
 Kriptografik güvenlik garantilerini koruyarak, gizliliği koruyan hesaplama performansının toplu işleme, önbellekleme ve donanım hızlandırma ile optimize edildiğini doğrulayın.

---

### C4.15 Ajan Çerçevesi Bulut Entegrasyon Güvenliği ve Hibrit Dağıtım

Hibrit yerinde/bulut mimarilerine sahip bulut entegrasyonlu ajan çerçeveleri için güvenlik kontrolleri.

 #4.15.1    Seviye: 1    Rol: D/V
 Bulut depolama entegrasyonunun, ajan tarafından kontrol edilen anahtar yönetimi ile uçtan uca şifreleme kullandığını doğrulayın.
 #4.15.2    Seviye: 2    Rol: D/V
 Hibrit dağıtım güvenlik sınırlarının şifreli iletişim kanallarıyla net bir şekilde tanımlandığını doğrulayın.
 #4.15.3    Seviye: 2    Rol: D/V
 Bulut kaynaklarına erişimin sürekli kimlik doğrulama ile sıfır güven doğrulamasını içerdiğini doğrulayın.
 #4.15.4    Seviye: 3    Rol: D/V
 Veri yerleşim gereksinimlerinin, depolama konumlarının kriptografik doğrulamasıyla uygulandığını doğrulayın.
 #4.15.5    Seviye: 3    Rol: D/V
 Bulut sağlayıcı güvenlik değerlendirmelerinin, ajan-spesifik tehdit modellemesi ve risk değerlendirmesini içerdiğini doğrulayın.

---

### Referanslar

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

## C5 AI Bileşenleri ve Kullanıcıları için Erişim Kontrolü ve Kimlik

### Kontrol Amacı

Yapay zeka sistemleri için etkili erişim kontrolü, sağlam kimlik yönetimi, bağlam farkındalığına sahip yetkilendirme ve sıfır güven ilkelerine uygun çalışma zamanı denetimini gerektirir. Bu kontroller, insanların, servislerin ve otonom ajanların yalnızca açıkça verilen kapsamlar içinde modellerle, verilerle ve hesaplama kaynaklarıyla etkileşimde bulunmasını sağlar ve sürekli doğrulama ile denetim yeteneklerini içerir.

---

### C5.1 Kimlik Yönetimi ve Doğrulama

Tüm varlıklar için ayrıcalıklı işlemlerde çok faktörlü kimlik doğrulama ile kriptografik olarak desteklenen kimlikler oluşturun.

 #5.1.1    Seviye: 1    Rol: D/V
 Tüm insan kullanıcıların ve hizmet ilkelerinin, benzersiz kimlik-tenkü tokan eşlemeleriyle (paylaşılan hesaplar veya kimlik bilgileri olmadan) OIDC/SAML protokolleri kullanarak merkezi bir kurumsal kimlik sağlayıcısı (IdP) aracılığıyla kimlik doğrulamasını doğrulayın.
 #5.1.2    Seviye: 1    Rol: D/V
 Yüksek riskli işlemlerin (model dağıtımı, ağırlık ihracı, eğitim verisi erişimi, üretim yapılandırma değişiklikleri) çok faktörlü kimlik doğrulama veya oturum yeniden doğrulaması ile adım yükseltme kimlik doğrulaması gerektirdiğini doğrulayın.
 #5.1.3    Seviye: 2    Rol: D
 Yeni yöneticilerin, üretim sistemi erişimi almadan önce NIST 800-63-3 IAL-2 veya eşdeğer standartlara uygun kimlik doğrulamasından geçtiğini doğrulayın.
 #5.1.4    Seviye: 2    Rol: V
 Erişim incelemelerinin, otomatik olarak atıl hesapların tespiti, kimlik bilgisi döndürme zorunluluğu ve kullanım dışı bırakma iş akışları ile üç ayda bir yapıldığını doğrulayın.
 #5.1.5    Seviye: 3    Rol: D/V
 Federated AI ajanlarının, maksimum 24 saatlik bir süreye sahip ve kökenin kriptografik kanıtını içeren imzalı JWT beyanları aracılığıyla kimlik doğrulaması yaptığını doğrulayın.

---

### C5.2 Kaynak Yetkilendirmesi ve Asgari Ayrıcalık

Tüm AI kaynakları için açık izin modelleri ve denetim izleriyle ayrıntılı erişim kontrolleri uygulayın.

 #5.2.1    Seviye: 1    Rol: D/V
 Her AI kaynağının (veri setleri, modeller, uç noktalar, vektör koleksiyonları, gömme dizinleri, hesaplama örnekleri) açık izin listeleri ve varsayılan reddetme politikalarıyla rol tabanlı erişim kontrollerini zorunlu kıldığını doğrulayın.
 #5.2.2    Seviye: 1    Rol: D/V
 Hizmet hesaplarında en az ayrıcalık prensiplerinin varsayılan olarak uygulandığını, izinlerin okuma-eşliğinde başladığını ve yazma erişimi için belgelenmiş iş gerekçesinin gerektiğini doğrulayın.
 #5.2.3    Seviye: 1    Rol: V
 Tüm erişim kontrolü değişikliklerinin onaylanmış değişiklik taleplerine bağlı olduğunu ve zaman damgaları, işlemci kimlikleri, kaynak tanımlayıcıları ve izin farkları ile değiştirilemez biçimde kaydedildiğini doğrulayın.
 #5.2.4    Seviye: 2    Rol: D
 Veri sınıflandırma etiketlerinin (KİB, PHI, ihracat kontrollü, özel) türetilmiş kaynaklara (gömülü veriler, komut önbellekleri, model çıktıları) otomatik olarak yayıldığını ve tutarlı politika uygulamasının sağlandığını doğrulayın.
 #5.2.5    Seviye: 2    Rol: D/V
 Yetkisiz erişim girişimleri ve ayrıcalık yükseltme olaylarının, bağlamsal meta verilerle birlikte 5 dakika içinde SIEM sistemlerine gerçek zamanlı uyarılar tetiklediğini doğrulayın.

---

### C5.3 Dinamik Politika Değerlendirmesi

Denetim yeteneklerine sahip bağlam farkındalıklı yetkilendirme kararları için öznitelik tabanlı erişim kontrolü (ABAC) motorlarını dağıtın.

 #5.3.1    Seviye: 1    Rol: D/V
 Yetkilendirme kararlarının, kimlik doğrulamalı API’ler aracılığıyla erişilebilen ve kriptografik bütünlük korumasına sahip özel bir politika motoruna (OPA, Cedar veya eşdeğeri) dış kaynaklı olarak verildiğini doğrulayın.
 #5.3.2    Seviye: 1    Rol: D/V
 Politikaların kullanıcı yetki seviyesi, kaynak hassasiyeti sınıflandırması, istek bağlamı, kiracı izolasyonu ve zamansal kısıtlamalar gibi dinamik öznitelikleri çalışma zamanında değerlendirdiğini doğrulayın.
 #5.3.3    Seviye: 2    Rol: D
 Politika tanımlarının sürüm kontrolü yapıldığını, eş düzey incelemesinden geçtiğini ve üretim dağıtımı öncesinde CI/CD boru hatlarında otomatik testlerle doğrulandığını teyit edin.
 #5.3.4    Seviye: 2    Rol: V
 Politika değerlendirme sonuçlarının yapılandırılmış karar gerekçelerini içerdiğini ve korelasyon analizi ile uyumluluk raporlaması için SIEM sistemlerine iletildiğini doğrulayın.
 #5.3.5    Seviye: 3    Rol: D/V
 Politika önbellek zaman aşımı (TTL) değerlerinin, yüksek hassasiyetli kaynaklar için 5 dakikayı ve önbellek geçersiz kılma özelliklerine sahip standart kaynaklar için 1 saati aşmadığını doğrulayın.

---

### C5.4 Sorgu Zamanı Güvenlik Uygulaması

Zorunlu filtreleme ve satır düzeyinde güvenlik politikaları ile veritabanı katmanı güvenlik kontrolleri uygulayın.

 #5.4.1    Seviye: 1    Rol: D/V
 Tüm vektör veritabanı ve SQL sorgularının, uygulama kodu değil, veritabanı motoru seviyesinde zorunlu güvenlik filtrelerini (kiracı kimliği, hassasiyet etiketleri, kullanıcı kapsamı) içerdiğini doğrulayın.
 #5.4.2    Seviye: 1    Rol: D/V
 Tüm vektör veritabanları, arama indeksleri ve eğitim veri kümeleri için politika devralma ile satır seviyesi güvenlik (RLS) politikalarının ve alan seviyesi maskelenmenin etkin olduğundan emin olun.
 #5.4.3    Seviye: 2    Rol: D
 Başarısız yetkilendirme değerlendirmelerinin, sorguları hemen sonlandırarak ve boş sonuç kümeleri döndürmek yerine açık yetkilendirme hata kodları vererek "karışmış vekil saldırılarını" önleyeceğini doğrulayın.
 #5.4.4    Seviye: 2    Rol: V
 Politika değerlendirme gecikmesinin, yetkilendirme atlamasına olanak tanıyabilecek zaman aşımı durumları için otomatik uyarılarla sürekli olarak izlenip izlenmediğini doğrulayın.
 #5.4.5    Seviye: 3    Rol: D/V
 Sorgu yeniden deneme mekanizmalarının, aktif kullanıcı oturumları içinde dinamik izin değişikliklerini dikkate almak için yetkilendirme politikalarını yeniden değerlendirdiğini doğrulayın.

---

### C5.5 Çıktı Filtreleme ve Veri Kayıp Önleme

İzinsiz veri açığa çıkmasını önlemek için AI tarafından oluşturulan içerikte son işlem kontrolü uygulayın.

 #5.5.1    Seviye: 1    Rol: D/V
 İçeriği talep edenlere sunmadan önce, çıkarım sonrası filtreleme mekanizmalarının yetkisiz KİT, sınıflandırılmış bilgiler ve özel verileri tarayıp sansürlediğini doğrulayın.
 #5.5.2    Seviye: 1    Rol: D/V
 Model çıktılarındaki atıfların, referansların ve kaynak atıflarının çağıran hakları ile doğrulandığını ve yetkisiz erişim tespit edilirse kaldırıldığını doğrulayın.
 #5.5.3    Seviye: 2    Rol: D
 Kullanıcı izin seviyelerine ve veri sınıflandırmalarına göre çıktı formatı kısıtlamalarının (temizlenmiş PDF'ler, meta verisi kaldırılmış görseller, onaylı dosya türleri) uygulandığını doğrulayın.
 #5.5.4    Seviye: 2    Rol: V
 Kırpma algoritmalarının deterministik, sürüm kontrollü olduğunu ve uyum soruşturmalarını ve adli analizleri desteklemek için denetim günlüklerini tuttuğunu doğrulayın.
 #5.5.5    Seviye: 3    Rol: V
 Yüksek riskli sansürleme olaylarının, veri maruziyeti olmaksızın adli inceleme için orijinal içeriğin kriptografik özetlerini içeren uyarlanabilir günlükler oluşturduğunu doğrulayın.

---

### C5.6 Çok Kiracılı İzolasyon

Paylaşılan yapay zeka altyapısında kiracılar arasında kriptografik ve mantıksal izolasyonu sağlayın.

 #5.6.1    Seviye: 1    Rol: D/V
 Bellek alanlarının, gömme depolarının, önbellek girdilerinin ve geçici dosyaların, kiracı başına ad alanı ayrılmış şekilde olduğunu doğrulayın ve kiracı silindiğinde veya oturum sonlandırıldığında güvenli şekilde temizlendiğinden emin olun.
 #5.6.2    Seviye: 1    Rol: D/V
 Her API isteğinin, oturum bağlamı ve kullanıcı yetkilerine karşı kriptografik olarak doğrulanan kimlik doğrulanmış bir kiracı tanımlayıcısı içerdiğini doğrulayın.
 #5.6.3    Seviye: 2    Rol: D
 Ağ politikalarının hizmet dokuları ve konteyner orkestra platformları içinde kiracılar arası iletişim için varsayılan reddetme kuralları uyguladığını doğrulayın.
 #5.6.4    Seviye: 3    Rol: D
 Müşteri tarafından yönetilen anahtar (CMK) desteği ve kiracı veri depoları arasında kriptografik izolasyon ile şifreleme anahtarlarının her kiracı için benzersiz olduğunu doğrulayın.

---

### C5.7 Otonom Ajan Yetkilendirmesi

Kapsamlı yetenek jetonları ve sürekli yetkilendirme yoluyla yapay zeka ajanları ve otonom sistemler için kontrol izinleri.

 #5.7.1    Seviye: 1    Rol: D/V
 Otonom ajanların, izin verilen eylemleri açıkça listeleyen, erişilebilir kaynakları, zaman sınırlarını ve operasyonel kısıtlamaları içeren kapsamlı yetki belirteçleri aldığını doğrulayın.
 #5.7.2    Seviye: 1    Rol: D/V
 Yüksek riskli yeteneklerin (dosya sistemi erişimi, kod yürütme, harici API çağrıları, finansal işlemler) varsayılan olarak devre dışı bırakıldığını ve etkinleştirilmesi için iş gerekçeleriyle açık onayların gerektiğini doğrulayın.
 #5.7.3    Seviye: 2    Rol: D
 Yetenek belirteçlerinin kullanıcı oturumlarına bağlı olduğunu doğrulayın, kriptografik bütünlük koruması içermesini sağlayın ve çevrimdışı senaryolarda saklanamaması veya yeniden kullanılamaması gerektiğini garanti edin.
 #5.7.4    Seviye: 2    Rol: V
 Ajan tarafından başlatılan eylemlerin, tam bağlam değerlendirmesi ve denetim kaydı ile ABAC politika motoru aracılığıyla ikincil yetkilendirmeye tabi tutulduğunu doğrulayın.
 #5.7.5    Seviye: 3    Rol: V
 Ajan hata durumları ve istisna yönetiminin, olay analizi ve adli inceleme desteği sağlamak için yetenek kapsamı bilgilerini içerdiğini doğrulayın.

---

### Referanslar

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
#### Yapay Zeka'ya Özgü Güvenlik

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Modeller, Çerçeveler ve Veri için Tedarik Zinciri Güvenliği

### Kontrol Amacı

Yapay zeka tedarik zinciri saldırıları, üçüncü taraf modelleri, çerçeveleri veya veri kümelerini kullanarak arka kapılar, önyargılar veya kullanılabilir kodlar yerleştirir. Bu kontroller, tüm model yaşam döngüsünü korumak için uçtan uca köken takibi, zafiyet yönetimi ve izleme sağlar.

---

### C6.1 Önceden Eğitilmiş Modelin İncelenmesi ve Kökeni

Herhangi bir ince ayar veya dağıtımdan önce üçüncü taraf model kaynaklarını, lisanslarını ve gizli davranışlarını değerlendirin ve doğrulayın.

 #6.1.1    Seviye: 1    Rol: D/V
 Her üçüncü taraf model öğesinin, kaynak deposunu ve commit hash'ini belirten imzalı bir köken kaydı içerdiğini doğrulayın.
 #6.1.2    Seviye: 1    Rol: D/V
 Modellerin, içe aktarılmadan önce otomatik araçlar kullanılarak kötü amaçlı katmanlar veya Truva tetikleyicileri açısından tarandığından emin olun.
 #6.1.3    Seviye: 2    Rol: D
 Transfer öğreniminin ince ayarının, gizli davranışları tespit etmek için düşmanca değerlendirmeyi geçtiğini doğrulayın.
 #6.1.4    Seviye: 2    Rol: V
 Model lisanslarının, ihracat kontrol etiketlerinin ve veri kaynağı beyanlarının bir ML-BOM girdisinde kaydedildiğini doğrulayın.
 #6.1.5    Seviye: 3    Rol: D/V
 Yüksek riskli modellerin (kamuya yüklenmiş ağırlıklar, doğrulanmamış yaratıcılar) insan incelemesi ve onayı yapılana kadar karantinada kaldığını doğrulayın.

---

### C6.2 Çerçeve ve Kütüphane Tarama

Çalışma zamanı yığınını güvenli tutmak için ML çerçevelerini ve kütüphanelerini sürekli olarak CVE'ler ve kötü amaçlı kodlar açısından tarayın.

 #6.2.1    Seviye: 1    Rol: D/V
 CI boru hatlarının AI çerçeveleri ve kritik kütüphaneler üzerinde bağımlılık tarayıcılarını çalıştırdığını doğrulayın.
 #6.2.2    Seviye: 1    Rol: D/V
 Kritik güvenlik açıklarının (CVSS ≥ 7.0) üretim imajlarına geçişi engellediğini doğrulayın.
 #6.2.3    Seviye: 2    Rol: D
 Çatallanmış veya satın alınmış ML kütüphanelerinde statik kod analizinin çalıştığını doğrulayın.
 #6.2.4    Seviye: 2    Rol: V
 Çerçeve yükseltme önerilerinin, genel CVE beslemelerine atıfta bulunan bir güvenlik etki değerlendirmesi içerdiğini doğrulayın.
 #6.2.5    Seviye: 3    Rol: V
 Çalışma zamanı sensörlerinin, imzalanmış SBOM'dan sapma gösteren beklenmeyen dinamik kütüphane yüklemelerinde uyarı verdiğini doğrulayın.

---

### C6.3 Bağımlılık Sabitleme ve Doğrulama

Her bağımlılığı değişmez özetlere sabitleyin ve aynı, müdahale edilmemiş yapıları garanti etmek için yapıları yeniden üretin.

 #6.3.1    Seviye: 1    Rol: D/V
 Tüm paket yöneticilerinin sürüm sabitlemesini kilit dosyaları aracılığıyla zorunlu kıldığını doğrulayın.
 #6.3.2    Seviye: 1    Rol: D/V
 Konteyner referanslarında değiştirilebilir etiketler yerine değiştirilemez özetlerin kullanıldığını doğrulayın.
 #6.3.3    Seviye: 2    Rol: D
 Tekrar üretilebilir derleme kontrollerinin, aynı çıktıları sağlamak için CI çalışmaları arasında karma değerlerini karşılaştırdığını doğrulayın.
 #6.3.4    Seviye: 2    Rol: V
 Denetim izlenebilirliği için yapı doğrulamaların 18 ay süreyle saklandığını doğrulayın.
 #6.3.5    Seviye: 3    Rol: D
 Süresi dolmuş bağımlılıkların, sabitlenmiş sürümleri güncellemek veya çatallamak için otomatik PR’leri tetiklediğini doğrulayın.

---

### C6.4 Güvenilir Kaynak Uygulaması

Sadece kriptografik olarak doğrulanmış, organizasyon tarafından onaylanmış kaynaklardan eser indirmelerine izin verin ve diğer her şeyi engelleyin.

 #6.4.1    Seviye: 1    Rol: D/V
 Model ağırlıklarının, veri setlerinin ve konteynerlerin yalnızca onaylanmış alan adlarından veya dahili kayıt defterlerinden indirildiğini doğrulayın.
 #6.4.2    Seviye: 1    Rol: D/V
 Sigstore/Cosign imzalarının, eserler yerel olarak önbelleğe alınmadan önce yayımcı kimliğini doğruladığını kontrol edin.
 #6.4.3    Seviye: 2    Rol: D
 Çıkış vekillerinin, güvenilir kaynak politikasını uygulamak için kimlik doğrulaması yapılmamış eser indirmelerini engellediğini doğrulayın.
 #6.4.4    Seviye: 2    Rol: V
 Depo izin listelerinin her bir giriş için iş gerekçesi kanıtı ile birlikte çeyrek dönemlerde gözden geçirildiğini doğrulayın.
 #6.4.5    Seviye: 3    Rol: V
 Politika ihlallerinin, artefaktların karantinaya alınmasını ve bağlı pipeline çalışmalarının geri alınmasını tetiklediğini doğrulayın.

---

### C6.5 Üçüncü Taraf Veri Seti Risk Değerlendirmesi

Dış veri setlerini zehirlenme, önyargı ve yasal uyumluluk açısından değerlendirin ve yaşam döngüleri boyunca izlemesini yapın.

 #6.5.1    Seviye: 1    Rol: D/V
 Dış veri setlerinin zehirlenme riski puanlamasından geçirildiğini doğrulayın (örneğin, veri parmak izi çıkarma, aykırı değer tespiti).
 #6.5.2    Seviye: 1    Rol: D
 Önyargı metriklerinin (demografik denklik, eşit fırsat) veri seti onayından önce hesaplandığını doğrulayın.
 #6.5.3    Seviye: 2    Rol: V
 Verilerin kökeni ve lisans koşullarının ML-BOM girdilerinde kaydedildiğini doğrulayın.
 #6.5.4    Seviye: 2    Rol: V
 Barındırılan veri setlerindeki kayma veya bozulmanın düzenli izleme ile tespit edildiğini doğrulayın.
 #6.5.5    Seviye: 3    Rol: D
 Eğitim öncesinde, yasaklanmış içeriklerin (telif hakkı, KİB) otomatik temizleme yoluyla kaldırıldığını doğrulayın.

---

### C6.6 Tedarik Zinciri Saldırısı İzleme

CVE beslemeleri, denetim kaydı analizleri ve kırmızı takım simülasyonları aracılığıyla tedarik zinciri tehditlerini erken tespit edin.

 #6.6.1    Seviye: 1    Rol: V
 Anormal paket çekimleri veya değiştirilmiş derleme adımları için CI/CD denetim günlüklerinin SIEM algılamalarına aktarıldığını doğrulayın.
 #6.6.2    Seviye: 2    Rol: D
 Olay müdahale oyun kitaplarının, ele geçirilmiş modeller veya kütüphaneler için geri alma prosedürlerini içerdiğini doğrulayın.
 #6.6.3    Seviye: 3    Rol: V
 Tehdit istihbaratı zenginleştirme etiketlerinin, uyarı üçlemesinde ML'ye özgü göstergeleri (örneğin, model zehirleme IoC'leri) doğruladığından emin olun.

---

### C6.7 Model Nesneleri için ML-BOM

Ayrıntılı ML'ye özgü SBOM'lar (ML-BOM'lar) oluşturun ve imzalayın, böylece sonraki kullanıcılar bileşen bütünlüğünü dağıtım zamanında doğrulayabilir.

 #6.7.1    Seviye: 1    Rol: D/V
 Her model öğesinin veri setlerini, ağırlıkları, hiperparametreleri ve lisansları listeleyen bir ML-BOM yayınladığını doğrulayın.
 #6.7.2    Seviye: 1    Rol: D/V
 ML-BOM üretimi ve Cosign imzasının CI'da otomatikleştirildiğini ve birleştirme için zorunlu olduğunu doğrulayın.
 #6.7.3    Seviye: 2    Rol: D
 Herhangi bir bileşen meta verisi (hash, lisans) eksikse, ML‑BOM tamlık kontrollerinin derlemeyi başarısız kıldığını doğrulayın.
 #6.7.4    Seviye: 2    Rol: V
 Aşağıdaki kullanıcıların, dağıtım zamanında ithal edilen modelleri doğrulamak için API aracılığıyla ML-BOM'ları sorgulayabildiğini doğrulayın.
 #6.7.5    Seviye: 3    Rol: V
 ML‑BOM'ların sürüm kontrolünün yapıldığını ve yetkisiz değişiklikleri tespit etmek için farklarının alındığını doğrulayın.

---

### Referanslar

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

## C7 Model Davranışı, Çıktı Kontrolü ve Güvenlik Garantisi

### Kontrol Amacı

Model çıktıları yapılandırılmış, güvenilir, güvenli, açıklanabilir olmalı ve üretimde sürekli izlenmelidir. Bunu yapmak, hayal ürünlerini, gizlilik sızıntılarını, zararlı içeriği ve kontrolsüz eylemleri azaltırken, kullanıcı güvenini ve düzenleyici uyumu artırır.

---

### C7.1 Çıktı Formatı Uygulaması

Katı şemalar, kısıtlı çözümleme ve sonraki doğrulama, bozuk veya kötü amaçlı içeriğin yayılmasını önler.

 #7.1.1    Seviye: 1    Rol: D/V
 Yanıt şemalarının (örneğin, JSON Şeması) sistem isteminde sağlandığını ve her çıktının otomatik olarak doğrulandığını; uygun olmayan çıktılar için düzeltme veya reddetme işleminin tetiklendiğini doğrulayın.
 #7.1.2    Seviye: 1    Rol: D/V
 Taşma veya istem enjeksiyonu yan kanal saldırılarını önlemek için kısıtlanmış çözümleme (durdurma tokenleri, regex, maksimum token sayısı) etkinleştirildiğini doğrulayın.
 #7.1.3    Seviye: 2    Rol: D/V
 Alt bileşenlerin çıktıları güvensiz olarak değerlendirip bunları şemalara veya enjeksiyona karşı güvenli serileştirme çözümleyicilerine karşı doğruladığını teyit edin.
 #7.1.4    Seviye: 3    Rol: V
 Yanlış çıktı olaylarının kaydedildiğini, hız sınırlamasına tabi tutulduğunu ve izlemeye yansıtıldığını doğrulayın.

---

### C7.2 Halüsinasyon Tespiti ve Azaltılması

Belirsizlik tahmini ve yedekleme stratejileri, uydurulmuş cevapları sınırlar.

 #7.2.1    Seviye: 1    Rol: D/V
 Token düzeyinde log-olasılıkların, toplu kendi-tutarlılığın veya ince ayarlı halüsinasyon tespitçilerinin her yanıta bir güven skoru atadığını doğrulayın.
 #7.2.2    Seviye: 1    Rol: D/V
 Yanıtların, yapılandırılabilir bir güven eşiğinin altında olması durumunda yedek iş akışlarını (örneğin, geri getirme destekli üretim, ikincil model veya insan incelemesi) tetiklediğini doğrulayın.
 #7.2.3    Seviye: 2    Rol: D/V
 Halüsinasyon olaylarının kök neden meta verisiyle etiketlendiğini ve ölüm sonrası analiz ile ince ayar iş akışlarına aktarıldığını doğrulayın.
 #7.2.4    Seviye: 3    Rol: D/V
 Önemli model veya bilgi tabanı güncellemelerinden sonra eşik değerlerin ve dedektörlerin yeniden kalibrasyonunun yapıldığını doğrulayın.
 #7.2.5    Seviye: 3    Rol: V
 Gösterge paneli görselleştirmelerinin halüsinasyon oranlarını takip ettiğini doğrulayın.

---

### C7.3 Çıktı Güvenliği ve Gizlilik Filtreleme

Politika filtreleri ve kırmızı takım kapsamı kullanıcıları ve gizli verileri korur.

 #7.3.1    Seviye: 1    Rol: D/V
 Politikaya uygun olarak nefret, taciz, kendine zarar verme, aşırılıkçı ve cinsel içerikli içeriklerin ön ve sonrası oluşturma sınıflandırıcıları tarafından engellendiğini doğrulayın.
 #7.3.2    Seviye: 1    Rol: D/V
 Her yanıtta Kişisel Tanımlanabilir Bilgi (PII)/Ödeme Kartı Endüstrisi (PCI) tespiti ve otomatik sansürün çalıştığını doğrulayın; ihlaller bir gizlilik olayı tetikler.
 #7.3.3    Seviye: 2    Rol: D
 Gizlilik etiketlerinin (örneğin, ticari sırlar) metin, görüntü veya kodda sızıntıyı önlemek için modlar arasında yayılmasını doğrulayın.
 #7.3.4    Seviye: 3    Rol: D/V
 Filtre atlama girişimlerinin veya yüksek riskli sınıflandırmaların ikinci onay veya kullanıcı yeniden kimlik doğrulaması gerektirdiğini doğrulayın.
 #7.3.5    Seviye: 3    Rol: D/V
 Filtreleme eşiklerinin yasal yargı bölgeleri ve kullanıcı yaşı/rolu bağlamını yansıttığını doğrulayın.

---

### C7.4 Çıktı ve Eylem Sınırlaması

Oran sınırları ve onay kapıları, kötüye kullanımı ve aşırı özerkliği önler.

 #7.4.1    Seviye: 1    Rol: D
 429 hatalarında üssel geri çekilme ile kullanıcı başına ve API anahtarı başına kota sınırlarının istekleri, tokenları ve maliyeti sınırladığını doğrulayın.
 #7.4.2    Seviye: 1    Rol: D/V
 Ayrıcalıklı işlemlerin (dosya yazımları, kod yürütme, ağ çağrıları) politika tabanlı onay veya insan müdahalesi gerektirdiğini doğrulayın.
 #7.4.3    Seviye: 2    Rol: D/V
 Aynı istek için oluşturulan görüntülerin, kodların ve metinlerin kötü amaçlı içerik gizlemek için kullanılamayacağını garanti etmek üzere, çapraz modal tutarlılık kontrollerinin sağlandığını doğrulayın.
 #7.4.4    Seviye: 2    Rol: D
 Ajan temsil derinliği, özyineleme sınırları ve izin verilen araç listelerinin açıkça yapılandırıldığını doğrulayın.
 #7.4.5    Seviye: 3    Rol: V
 Limit ihlallerinin SIEM alımı için yapılandırılmış güvenlik olayları yayınladığını doğrulayın.

---

### C7.5 Çıktı Açıklanabilirliği

Şeffaf sinyaller, kullanıcı güvenini ve dahili hata ayıklamayı artırır.

 #7.5.1    Seviye: 2    Rol: D/V
 Kullanıcıya yönelik güven puanlarının veya kısa sebep özetlerinin risk değerlendirmesi uygun gördüğünde sunulduğunu doğrulayın.
 #7.5.2    Seviye: 2    Rol: D/V
 Oluşturulan açıklamaların hassas sistem istemlerini veya tescilli verileri ortaya çıkarmadığını doğrulayın.
 #7.5.3    Seviye: 3    Rol: D
 Sistemin, yetkili inceleme için token düzeyinde olasılık günlüklerini veya dikkat haritalarını yakalayıp sakladığını doğrulayın.
 #7.5.4    Seviye: 3    Rol: V
 Açıklanabilirlik artefaktlarının denetlenebilirlik için model sürümleriyle birlikte sürüm kontrolü altında olduğunu doğrulayın.

---

### C7.6 İzleme Entegrasyonu

Gerçek zamanlı gözlemlenebilirlik, geliştirme ile üretim arasındaki döngüyü kapatır.

 #7.6.1    Seviye: 1    Rol: D
 Metriklerin (şema ihlalleri, halüsinasyon oranı, toksisite, KİB sızıntıları, gecikme süresi, maliyet) merkezi bir izleme platformuna aktarıldığını doğrulayın.
 #7.6.2    Seviye: 1    Rol: V
 Her güvenlik metriği için uyarı eşiklerinin tanımlandığını ve çağrı sırası yükseltme yollarının bulunduğunu doğrulayın.
 #7.6.3    Seviye: 2    Rol: V
 Gösterge tablolarının çıktı anomalilerini model/sürüm, özellik bayrağı ve yukarı akış veri değişiklikleri ile ilişkilendirdiğini doğrulayın.
 #7.6.4    Seviye: 2    Rol: D/V
 İzleme verilerinin, belgelenmiş bir MLOps iş akışı içinde yeniden eğitim, ince ayar veya kural güncellemelerine geri besleme yapıldığını doğrulayın.
 #7.6.5    Seviye: 3    Rol: V
 İzleme hatlarının, hassas günlüklerin sızmasını önlemek için penetrasyon testinden geçirilmiş ve erişim kontrolüne tabi tutulmuş olduğunu doğrulayın.

---

### 7.7 Üretken Medya Güvenceleri

AI sistemlerinin yasa dışı, zararlı veya yetkisiz medya içeriği üretmemesini sağlamak için politika kısıtlamalarını, çıktı doğrulamasını ve izlenebilirliği uygulayın.

 #7.7.1    Seviye: 1    Rol: D/V
 Sistem istemlerinin ve kullanıcı talimatlarının, yasadışı, zararlı veya rızaya dayanmayan deepfake medya (örneğin, görüntü, video, ses) üretimini açıkça yasakladığını doğrulayın.
 #7.7.2    Seviye: 2    Rol: D/V
 Taklit üretme girişimleri, cinsel içerikli derin sahte görüntüler veya gerçek kişileri rıza olmadan tasvir eden medyanın oluşturulması için gelen istemlerin filtrelendiğini doğrulayın.
 #7.7.3    Seviye: 2    Rol: V
 Sistemin, telif hakkıyla korunan medyanın izinsiz çoğaltılmasını önlemek için algısal karmalama, filigran tespiti veya parmak izi yöntemlerini kullandığını doğrulayın.
 #7.7.4    Seviye: 3    Rol: D/V
 Tüm oluşturulan medyanın, aşağı yönlü izlenebilirlik için kriptografik olarak imzalanmış, filigranlı veya manipülasyona dayanıklı köken metadatalarıyla gömülü olduğunu doğrulayın.
 #7.7.5    Seviye: 3    Rol: V
 Bypass girişimlerinin (örneğin, istem gizleme, argo, saldırgan ifadeler) tespit edildiğinden, kaydedildiğinden ve hız sınırlandırmasına tabi tutulduğundan emin olun; tekrar eden kötüye kullanımlar izleme sistemlerine bildirilsin.

### Referanslar

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

Embeddingler ve vektör mağazaları, çağdaş yapay zeka sistemlerinin "canlı belleği" olarak işlev görür, kullanıcı tarafından sağlanan verileri sürekli kabul eder ve bunları Retrieval-Augmented Generation (RAG) aracılığıyla model bağlamlarına geri getirir. Yönetilmezse, bu bellek kişisel olarak tanımlanabilir bilgilerin (PII) sızmasına, onay ihlaline veya orijinal metnin yeniden yapılandırılması için tersine çevrilmesine neden olabilir. Bu kontrol ailesinin amacı, bellek boru hatlarını ve vektör veritabanlarını güçlendirmek, erişimin en az ayrıcalıklı olmasını sağlamak, embeddinglerin gizliliği korumasını temin etmek, depolanan vektörlerin süresinin dolmasını veya talep üzerine iptal edilmesini sağlamak ve kullanıcı başına belleğin asla başka bir kullanıcının istemlerini veya tamamlamalarını kirletmemesini sağlamaktır.

---

### C8.1 Bellek ve RAG İndekslerinde Erişim Kontrolleri

Her vektör koleksiyonunda ince taneli erişim kontrollerini zorunlu kılın.

 #8.1.1    Seviye: 1    Rol: D/V
 Satır/isim alanı düzeyindeki erişim kontrol kurallarının, kiracı, koleksiyon veya belge etiketi başına ekleme, silme ve sorgulama işlemlerini kısıtladığını doğrulayın.
 #8.1.2    Seviye: 1    Rol: D/V
 API anahtarları veya JWT'lerin kapsamlı iddialar (örneğin, koleksiyon kimlikleri, işlem fiilleri) taşıdığını ve en az üç ayda bir döndürüldüğünü doğrulayın.
 #8.1.3    Seviye: 2    Rol: D/V
 Ayrıcalık yükseltme girişimlerinin (örneğin, alan adları arasında benzerlik sorguları) tespit edildiği ve 5 dakika içinde bir SIEM'e kaydedildiği doğrulanmalıdır.
 #8.1.4    Seviye: 2    Rol: D/V
 Vektör veritabanı denetimlerinin günlüklerinde konu tanımlayıcı, işlem, vektör kimliği/isim alanı, benzerlik eşiği ve sonuç sayısını doğrulayın.
 #8.1.5    Seviye: 3    Rol: V
 Motorlar yükseltildiğinde veya indeks-parçalama kuralları değiştiğinde, erişim kararlarının atlama açıkları için test edildiğini doğrulayın.

---

### C8.2 Gömme Temizleme ve Doğrulama

Vektörleştirmeden önce metni Kişisel Tanımlanabilir Bilgiler (PII) için ön taramadan geçir, karart veya takma ad kullan ve isteğe bağlı olarak kalıntı sinyalleri kaldırmak için gömülü temsilleri (embedding) son işlemden geçir.

 #8.2.1    Seviye: 1    Rol: D/V
 Kişisel Tanımlayıcı Bilgilerin (PII) ve düzenlemeye tabi verilerin otomatik sınıflandırıcılar aracılığıyla tespit edilip maskeleme, tokenleştirme veya gömme öncesi çıkarma işlemlerinin yapıldığını doğrulayın.
 #8.2.2    Seviye: 1    Rol: D
 Gömülü işleme hatlarının, dizini zehirleyebilecek çalıştırılabilir kod veya UTF-8 olmayan kalıntılar içeren girdileri reddettiğini veya karantinaya aldığını doğrulayın.
 #8.2.3    Seviye: 2    Rol: D/V
 Herhangi bir bilinen Kişisel Tanımlanabilir Bilgi (PII) tokenına olan mesafesi yapılandırılabilir bir eşik değerinin altına düşen cümle gömme vektörlerine yerel veya metrik diferansiyel gizlilik temizleme işleminin uygulandığını doğrulayın.
 #8.2.4    Seviye: 2    Rol: V
 Sanitasyon etkinliğinin (örneğin, KİB düzeltmesinin geri çağrılması, anlamsal kayma) en az altı ayda bir kıyaslama metinleri karşısında doğrulandığından emin olun.
 #8.2.5    Seviye: 3    Rol: D/V
 Temizleme yapılandırmalarının sürüm kontrolünde olduğunu ve değişikliklerin eşler arası incelemeden geçtiğini doğrulayın.

---

### C8.3 Bellek Süresinin Dolması, İptali ve Silinmesi

GDPR "unutulma hakkı" ve benzeri yasalar zamanında silmeyi gerektirir; bu nedenle vektör depolarının, iptal edilen vektörlerin kurtarılamaması veya yeniden indekslenememesi için TTL, kalıcı silme ve mezar taşı (tomb-stoning) desteklemesi gerekir.

 #8.3.1    Seviye: 1    Rol: D/V
 Her vektör ve meta veri kaydının TTL veya otomatik temizlik işleri tarafından dikkate alınan açık bir saklama etiketi taşıdığını doğrulayın.
 #8.3.2    Seviye: 1    Rol: D/V
 Kullanıcı tarafından başlatılan silme taleplerinin, 30 gün içinde vektörleri, meta verileri, önbellek kopyalarını ve türetilmiş indeksleri tamamen temizlediğini doğrulayın.
 #8.3.3    Seviye: 2    Rol: D
 Mantıksal silmelerin, donanım destekliyorsa depolama bloklarının kriptografik olarak imha edilmesinden veya anahtar kasası anahtarının yok edilmesinden sonra yapıldığını doğrulayın.
 #8.3.4    Seviye: 3    Rol: D/V
 Son kullanma süresi dolmuş vektörlerin, süresi dolduktan sonra < 500 ms içinde en yakın komşu arama sonuçlarından hariç tutulduğunu doğrulayın.

---

### C8.4 Gömme Tersine Çevirme ve Sızıntısını Önleme

Son savunma yöntemleri—gürültü üst üste bindirme, projeksiyon ağları, gizlilik-nöron bozulması ve uygulama katmanı şifrelemesi—token seviyesindeki tersine çevirme oranlarını %5'in altına düşürebilir.

 #8.4.1    Seviye: 1    Rol: V
 Tersine çevirme, üyelik ve özellik çıkarımı saldırılarını kapsayan resmi bir tehdit modelinin var olduğunu ve yıllık olarak gözden geçirildiğini doğrulayın.
 #8.4.2    Seviye: 2    Rol: D/V
 Uygulama katmanı şifrelemesinin veya aranabilir şifrelemenin, vektörleri altyapı yöneticileri veya bulut personeli tarafından doğrudan okunmalardan koruduğunu doğrulayın.
 #8.4.3    Seviye: 3    Rol: V
 Savunma parametrelerinin (DP için ε, gürültü σ, projeksiyon rankı k) gizliliği ≥ %99 token koruması ve faydayı ≤ %3 doğruluk kaybı ile dengelediğini doğrulayın.
 #8.4.4    Seviye: 3    Rol: D/V
 Model güncellemeleri için sürüm kapılarının bir parçası olarak tersine dayanıklılık metriklerinin doğrulandığından emin olun ve regresyon bütçelerinin tanımlı olduğundan emin olun.

---

### C8.5 Kullanıcıya Özel Bellek İçin Kapsam Uygulaması

Çoklu kiracı sızıntısı hâlâ en önemli RAG riskidir: yanlış filtrelenmiş benzerlik sorguları başka bir müşterinin özel belgelerini ortaya çıkarabilir.

 #8.5.1    Seviye: 1    Rol: D/V
 Her sorgulama sorgusunun LLM istemine iletilmeden önce kiracı/kullanıcı kimliği ile son filtrelemesinin yapıldığını doğrulayın.
 #8.5.2    Seviye: 1    Rol: D
 Koleksiyon adlarının veya ad alanlı kimliklerin, vektörlerin kapsamlar arasında çakışmaması için kullanıcıya veya kiracıya göre tuzlandığını doğrulayın.
 #8.5.3    Seviye: 2    Rol: D/V
 Benzerlik sonuçlarının, yapılandırılabilir bir mesafe eşiğinin üzerinde ancak çağıranın kapsamı dışında kalması durumunda reddedildiğini ve güvenlik uyarılarını tetiklediğini doğrulayın.
 #8.5.4    Seviye: 2    Rol: V
 Çok kiracılı stres testlerinin kapsam dışı belgeleri almaya çalışan düşmanca sorguları simüle ettiğini ve sıfır bilgi sızıntısını gösterdiğini doğrulayın.
 #8.5.5    Seviye: 3    Rol: D/V
 Şifreleme anahtarlarının her kiracı için ayrı tutulduğunu doğrulayın, fiziksel depolama paylaşılsa bile kriptografik izolasyonun sağlandığından emin olun.

---

### C8.6 Gelişmiş Bellek Sistemi Güvenliği

Episodik, semantik ve çalışma belleği gibi gelişmiş bellek mimarileri için, özel izolasyon ve doğrulama gereksinimlerini içeren güvenlik kontrolleri.

 #8.6.1    Seviye: 1    Rol: D/V
 Farklı bellek türlerinin (epizodik, semantik, çalışma) rol tabanlı erişim kontrolleri, ayrı şifreleme anahtarları ve her bellek türü için belgelenmiş erişim desenleri ile izole güvenlik bağlamlarına sahip olduğunu doğrulayın.
 #8.6.2    Seviye: 2    Rol: D/V
 Bellek konsolidasyon süreçlerinin, depolamadan önce içerik temizliği, kaynak doğrulaması ve bütünlük kontrolleri yoluyla kötü amaçlı belleklerin enjekte edilmesini önlemek için güvenlik doğrulamasını içerdiğini doğrulayın.
 #8.6.3    Seviye: 2    Rol: D/V
 Bellek sorgusu taleplerinin, sorgu desen analizi, erişim kontrolü uygulanması ve sonuçların filtrelenmesi yoluyla yetkisiz bilgi çıkarımını önlemek amacıyla doğrulandığından ve temizlendiğinden emin olun.
 #8.6.4    Seviye: 3    Rol: D/V
 Anahtar silme, çok geçişli üzerine yazma veya doğrulama sertifikaları ile donanım tabanlı güvenli silme yöntemlerini kullanarak, hafıza unutma mekanizmalarının hassas bilgileri kriptografik silme garantileriyle güvenli bir şekilde sildiğini doğrulayın.
 #8.6.5    Seviye: 3    Rol: D/V
 Hafıza sisteminin bütünlüğünün, normal işlemler dışındaki bellek içeriği değişikliklerinde özet değerleri, denetim günlükleri ve otomatik uyarılar aracılığıyla yetkisiz değişiklikler veya bozulmalar için sürekli olarak izlenmesini doğrulayın.

---

### Referanslar

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

## 9 Otonom Orkestrasyon ve Temsil Yeteneğine Sahip Ajan Güvenliği

### Kontrol Amacı

Otonom veya çoklu ajan yapay zeka sistemlerinin yalnızca açıkça amaçlanan, doğrulanabilir, denetlenebilir ve belirli maliyet ve risk sınırları içinde kalan eylemleri gerçekleştirebilmesini sağlayın. Bu, Otonom Sistem İhlali, Araç Kötüye Kullanımı, Ajan Döngüsü Tespiti, İletişim Kaçırma, Kimlik Taklidi, Sürü Manipülasyonu ve Niyet Manipülasyonu gibi tehditlere karşı koruma sağlar.

---

### 9.1 Ajan Görev Planlama ve Özyineleme Bütçeleri

İmtiyazlı işlemler için özyinelemeli planları sınırlayın ve insan kontrol noktalarını zorunlu kılın.

 #9.1.1    Seviye: 1    Rol: D/V
 Her bir ajan yürütmesi için maksimum özyineleme derinliği, genişlik, gerçek zamanlı süre, token sayısı ve parasal maliyetin merkezi olarak yapılandırıldığını ve sürüm kontrolünün sağlandığını doğrulayın.
 #9.1.2    Seviye: 1    Rol: D/V
 Ayrıcalıklı veya geri alınamaz işlemlerin (örneğin, kod gönderimleri, finansal transferler) yürütülmeden önce denetlenebilir bir kanal aracılığıyla açık insan onayı gerektirdiğini doğrulayın.
 #9.1.3    Seviye: 2    Rol: D
 Gerçek zamanlı kaynak izleyicilerin herhangi bir bütçe eşiği aşıldığında devre kesici kesintisini tetikleyerek ilave görev genişlemesini durdurduğunu doğrulayın.
 #9.1.4    Seviye: 2    Rol: D/V
 Devre kesici olaylarının, adli inceleme için ajan kimliği, tetikleyici koşul ve yakalanan plan durumu ile kaydedildiğini doğrulayın.
 #9.1.5    Seviye: 3    Rol: V
 Güvenlik testlerinin bütçe tükenmesi ve kontrolsüz plan senaryolarını kapsadığını doğrulayın, veri kaybı olmadan güvenli durdurmayı teyit edin.
 #9.1.6    Seviye: 3    Rol: D
 Bütçe politikalarının kod olarak politika şeklinde ifade edildiğini ve yapılandırma sapmasını engellemek için CI/CD'de uygulandığını doğrulayın.

---

### 9.2 Araç Eklentisi Korumalı Alanı

Araç etkileşimlerini izole ederek yetkisiz sistem erişimi veya kod yürütmesini önleyin.

 #9.2.1    Seviye: 1    Rol: D/V
 Her aracın/eklentinin, en düşük ayrıcalıklı dosya sistemi, ağ ve sistem çağrısı politikalarına sahip bir işletim sistemi, konteyner veya WASM seviyesinde bir korumalı ortam içinde çalıştığını doğrulayın.
 #9.2.2    Seviye: 1    Rol: D/V
 Sandbox kaynak kotalarının (CPU, bellek, disk, ağ çıkışı) ve yürütme zaman aşımı sürelerinin uygulanıp uygulanmadığını ve kaydedildiğini doğrulayın.
 #9.2.3    Seviye: 2    Rol: D/V
 Araç ikili dosyalarının veya tanımlayıcılarının dijital olarak imzalandığını doğrulayın; yüklemeden önce imzalar doğrulanır.
 #9.2.4    Seviye: 2    Rol: V
 Sandbox telemetrisinin bir SIEM’e aktarıldığını doğrulayın; anormallikler (örneğin, dışa yönelik bağlantı girişimleri) uyarılar oluşturur.
 #9.2.5    Seviye: 3    Rol: V
 Yüksek riskli eklentilerin üretim ortamına dağıtılmadan önce güvenlik incelemesi ve penetrasyon testinden geçtiğini doğrulayın.
 #9.2.6    Seviye: 3    Rol: D/V
 Sandbox kaçış girişimlerinin otomatik olarak engellendiğini ve suçlu eklentinin inceleme sürecine kadar karantinaya alındığını doğrulayın.

---

### 9.3 Otonom Döngü ve Maliyet Sınırlaması

Kontrolsüz ajanlar arası özyinelemeyi ve maliyet patlamalarını tespit edin ve durdurun.

 #9.3.1    Seviye: 1    Rol: D/V
 Ara ajanlar arası çağrıların, çalışma zamanı tarafından azaltılan ve uygulanan bir sıçrama sınırı veya TTL içerdiğini doğrulayın.
 #9.3.2    Seviye: 2    Rol: D
 Ajanların kendi kendine çağrıyı veya döngüsel desenleri tespit etmek için benzersiz bir çağrı grafiği kimliğini koruduğunu doğrulayın.
 #9.3.3    Seviye: 2    Rol: D/V
 Kümülatif hesap birimi ve harcama sayacıların her istek zinciri için izlenip izlenmediğini doğrulayın; limitin aşılması zincirin durmasına neden olur.
 #9.3.4    Seviye: 3    Rol: V
 Ajan protokollerinde sınırsız özyinelemenin olmadığını göstermek için resmi analiz veya model kontrol yöntemlerinin kullanıldığını doğrulayın.
 #9.3.5    Seviye: 3    Rol: D
 Döngü-iptal olaylarının uyarılar oluşturduğunu ve sürekli iyileştirme metriklerini beslediğini doğrulayın.

---

### 9.4 Protokol Düzeyi Kötüye Kullanım Koruması

Elemanlar ile dış sistemler arasında kaçırma veya manipülasyonu önlemek için güvenli iletişim kanalları sağlayın.

 #9.4.1    Seviye: 1    Rol: D/V
 Tüm ajan-aracı ve ajan-ajan mesajlarının kimlik doğrulamasının yapıldığını (örneğin, karşılıklı TLS veya JWT) ve uçtan uca şifrelenmiş olduğunu doğrulayın.
 #9.4.2    Seviye: 1    Rol: D
 Şemaların kesinlikle doğrulandığını, bilinmeyen alanların veya hatalı biçimlendirilmiş mesajların reddedildiğini doğrulayın.
 #9.4.3    Seviye: 2    Rol: D/V
 Bütün mesaj yükünü, araç parametreleri de dahil olmak üzere, bütünlüğünü kontrol eden doğrulama (MAC'ler veya dijital imzalar) ile kapsandığını doğrulayın.
 #9.4.4    Seviye: 2    Rol: D
 Yeniden oynatma korumasının (nonce'lar veya zaman damgası pencereleri) protokol katmanında zorunlu kılındığını doğrulayın.
 #9.4.5    Seviye: 3    Rol: V
 Protokol uygulamalarının enjeksiyon veya serileştirme hataları için fuzzing ve statik analizden geçirildiğini doğrulayın.

---

### 9.5 Ajan Kimliği ve Değiştirme Kanıtı

Eylemlerin izlenebilir olmasını ve değişikliklerin tespit edilebilir olmasını sağlayın.

 #9.5.1    Seviye: 1    Rol: D/V
 Her ajan örneğinin benzersiz bir kriptografik kimliğe (anahtar çifti veya donanıma dayalı kimlik bilgisi) sahip olduğunu doğrulayın.
 #9.5.2    Seviye: 2    Rol: D/V
 Tüm ajan eylemlerinin imzalandığını ve zaman damgalı olduğunu doğrulayın; günlükler, inkâr edilememe için imzayı içermelidir.
 #9.5.3    Seviye: 2    Rol: V
 Tahrif edilmiş kayıtların eklemeye izin veren ya da sadece bir kez yazılabilen bir ortamda saklandığını doğrulayın.
 #9.5.4    Seviye: 3    Rol: D
 Kimlik anahtarlarının belirlenen bir takvime göre ve ihlal göstergelerinde döndürüldüğünü doğrulayın.
 #9.5.5    Seviye: 3    Rol: D/V
 Taklit ya da anahtar çatışması girişimlerinin etkilenmiş ajan üzerinde derhal karantina tetiklediğini doğrulayın.

---

### 9.6 Çoklu Ajan Sürü Risk Azaltımı

Toplu davranış tehlikelerini izolasyon ve resmi güvenlik modellemesi yoluyla hafifletin.

 #9.6.1    Seviye: 1    Rol: D/V
 Farklı güvenlik alanlarında çalışan ajanların izole çalışma zamanı kum havuzlarında veya ağ segmentlerinde yürütüldüğünü doğrulayın.
 #9.6.2    Seviye: 3    Rol: V
 Sürülmeden önce sürü davranışlarının canlılık ve güvenlik açısından modellenip resmi olarak doğrulandığından emin olunuz.
 #9.6.3    Seviye: 3    Rol: D
 Çalışma zamanı izleyicilerinin ortaya çıkan tehlikeli desenleri (örneğin, salınımlar, kilitlenmeler) tespit ettiğini ve düzeltici önlem başlattığını doğrulayın.

---

### 9.7 Kullanıcı ve Araç Kimlik Doğrulama / Yetkilendirme

Her ajan tarafından tetiklenen işlem için sağlam erişim kontrolleri uygulayın.

 #9.7.1    Seviye: 1    Rol: D/V
 Ajanların, son kullanıcı kimlik bilgilerini asla yeniden kullanmadan, aşağı akış sistemlere birinci sınıf prensip olarak kimlik doğrulaması yaptığını doğrulayın.
 #9.7.2    Seviye: 2    Rol: D
 Ajanın hangi araçları çağırabileceğini ve hangi parametreleri sağlayabileceğini sınırlayan ince taneli yetkilendirme politikalarını doğrulayın.
 #9.7.3    Seviye: 2    Rol: V
 İzin kontrollerinin yalnızca oturum başlangıcında değil, her çağrıda (sürekli yetkilendirme) yeniden değerlendirildiğini doğrulayın.
 #9.7.4    Seviye: 3    Rol: D
 Delegelenmiş ayrıcalıkların otomatik olarak sona erdiğini ve zaman aşımı veya kapsam değişikliği sonrasında yeniden onay gerektirdiğini doğrulayın.

---

### 9.8 Ajanlar Arası İletişim Güvenliği

Tüm ajanlar arası mesajları dinlemeye ve değiştirmeye karşı korumak için şifreleyin ve bütünlük koruması sağlayın.

 #9.8.1    Seviye: 1    Rol: D/V
 Ajan kanalları için karşılıklı kimlik doğrulama ve mükemmel ileri gizlilik şifrelemesinin (örneğin TLS 1.3) zorunlu olduğunu doğrulayın.
 #9.8.2    Seviye: 1    Rol: D
 İşlemeden önce mesaj bütünlüğünün ve kaynağının doğrulandığından emin olun; başarısızlık durumunda uyarılar oluşturulur ve mesaj reddedilir.
 #9.8.3    Seviye: 2    Rol: D/V
 İletişim meta verilerinin (zaman damgaları, sıra numaraları) adli yeniden yapılandırmayı destekleyecek şekilde kaydedildiğini doğrulayın.
 #9.8.4    Seviye: 3    Rol: V
 Protokol durum makinelerinin güvensiz durumlara sürülemeyeceğini resmi doğrulama veya model kontrolünün onayladığını doğrulayın.

---

### 9.9 Niyet Doğrulama ve Kısıtlama Uygulaması

Ajan eylemlerinin kullanıcının belirtilen niyeti ve sistem kısıtlamalarıyla uyumlu olduğunu doğrulayın.

 #9.9.1    Seviye: 1    Rol: D
 Ön yürütme kısıtlayıcı çözücülerin, önerilen eylemleri sabit kodlanmış güvenlik ve politika kurallarına karşı kontrol ettiğini doğrulayın.
 #9.9.2    Seviye: 2    Rol: D/V
 Yüksek etkili işlemlerin (mali, yıkıcı, gizlilik açısından hassas) başlatan kullanıcıdan açık niyet onayı gerektirdiğini doğrulayın.
 #9.9.3    Seviye: 2    Rol: V
 Tamamlanmış işlemlerin amaçlanan etkileri yan etkiler olmadan gerçekleştirildiğini doğrulamak için son koşul kontrollerinin geçerliliğini doğrulayın; tutarsızlıklar geri alma işlemini tetikler.
 #9.9.4    Seviye: 3    Rol: V
 Ajan planlarının tüm beyan edilmiş kısıtlamaları sağladığını göstermek için resmi yöntemlerin (örneğin, model kontrolü, teorem ispatı) veya özellik tabanlı testlerin doğrulanmasını sağlayın.
 #9.9.5    Seviye: 3    Rol: D
 Niyet uyumsuzluğu veya kısıtlama ihlali olaylarının sürekli iyileştirme döngülerini ve tehdit istihbaratı paylaşımını beslediğini doğrulayın.

---

### 9.10 Ajan Akıl Yürütme Stratejisi Güvenliği

ReAct, Chain-of-Thought ve Tree-of-Thoughts yaklaşımlarını içeren farklı muhakeme stratejilerinin güvenli seçimi ve yürütülmesi.

 #9.10.1    Seviye: 1    Rol: D/V
 Mantık stratejisi seçiminin deterministik kriterler (girdi karmaşıklığı, görev türü, güvenlik bağlamı) kullandığını ve aynı güvenlik bağlamı içinde özdeş girdilerin özdeş strateji seçimleri ürettiğini doğrulayın.
 #9.10.2    Seviye: 1    Rol: D/V
 Her bir muhakeme stratejisinin (ReAct, Chain-of-Thought, Tree-of-Thoughts) kendi bilişsel yaklaşımına özgü giriş doğrulaması, çıktı temizleme ve yürütme süre sınırlarına sahip olduğunu doğrulayın.
 #9.10.3    Seviye: 2    Rol: D/V
 Denetim izinin yeniden oluşturulması için giriş özellikleri, seçim kriteri değerleri ve yürütme meta verileri dahil olmak üzere gerekçelendirme stratejisi geçişlerinin tam bağlamıyla kaydedildiğini doğrulayın.
 #9.10.4    Seviye: 2    Rol: D/V
 Tree-of-Thoughts muhakemesinin, politika ihlalleri, kaynak sınırları veya güvenlik sınırları tespit edildiğinde keşfi sonlandıran dal budama mekanizmalarını içerdiğini doğrulayın.
 #9.10.5    Seviye: 2    Rol: D/V
 ReAct (Reason-Act-Observe) döngülerinin her aşamada doğrulama kontrol noktaları içerdiğini doğrulayın: akıl yürütme adımı doğrulaması, eylem yetkilendirmesi ve ilerlemeden önce gözlem temizliği.
 #9.10.6    Seviye: 3    Rol: D/V
 Akıl yürütme stratejisi performans metriklerinin (çalışma süresi, kaynak kullanımı, çıktı kalitesi) yapılandırılmış eşiklerin dışına çıktığında otomatik uyarılarla izlenip izlenmediğini doğrulayın.
 #9.10.7    Seviye: 3    Rol: D/V
 Birden fazla stratejiyi birleştiren hibrit muhakeme yaklaşımlarının, herhangi bir güvenlik kontrolünü atlamadan tüm bileşen stratejilerin giriş doğrulamasını ve çıktı kısıtlamalarını koruduğunu doğrulayın.
 #9.10.8    Seviye: 3    Rol: D/V
 Mantık stratejisi güvenlik testinin, hatalı girdilerle yapılan fuzzing, strateji değiştirmeye zorlayan düşmanca yönlendirmeler ve her bilişsel yaklaşım için sınır durumu testlerini içerdiğini doğrulayın.

---

### 9.11 Ajan Yaşam Döngüsü Durum Yönetimi ve Güvenlik

Kriptografik denetim izleri ve tanımlı kurtarma prosedürleri ile güvenli ajan başlatma, durum geçişleri ve sonlandırma.

 #9.11.1    Seviye: 1    Rol: D/V
 Ajan başlatmasının, donanım destekli kimlik bilgileriyle kriptografik kimlik kurulumu ve ajan kimliği, zaman damgası, yapılandırma karma değeri ve başlatma parametrelerini içeren değişmez başlatma denetim günlükleri içerdiğini doğrulayın.
 #9.11.2    Seviye: 2    Rol: D/V
 Ajan durum geçişlerinin kriptografik olarak imzalandığını, zaman damgalı olduğunu ve tetikleyici olaylar, önceki durum karması, yeni durum karması ve gerçekleştirilen güvenlik doğrulamaları dahil olmak üzere tam bağlamla birlikte kaydedildiğini doğrulayın.
 #9.11.3    Seviye: 2    Rol: D/V
 Ajan kapatma prosedürlerinin, kriptografik silme veya çok geçişli üzerine yazma kullanarak güvenli bellek temizliğini, sertifika otoritesine bildirimle kimlik bilgisi iptalini ve müdahale kanıtı sağlayan sonlandırma sertifikalarının oluşturulmasını içerdiğini doğrulayın.
 #9.11.4    Seviye: 3    Rol: D/V
 Ajan kurtarma mekanizmalarının durum bütünlüğünü kriptografik özetler (en az SHA-256) kullanarak doğruladığını ve bozulma tespit edildiğinde otomatik uyarılar ve manuel onay gereksinimleri ile bilinen iyi durumlara geri alındığını doğrulayın.
 #9.11.5    Seviye: 3    Rol: D/V
 Ajan kalıcılık mekanizmalarının, her ajan için ayrı AES-256 anahtarlarıyla hassas durum verilerini şifrelediğini ve yapılandırılabilir zaman çizelgeleriyle (en fazla 90 gün) güvenli anahtar döndürmesini sıfır kesinti süresi ile dağıtacak şekilde uyguladığını doğrulayın.

---

### 9.12 Araç Entegrasyonu Güvenlik Çerçevesi

Tanımlanmış risk değerlendirme ve onay süreçleri ile dinamik araç yükleme, yürütme ve sonuç doğrulama için güvenlik kontrolleri.

 #9.12.1    Seviye: 1    Rol: D/V
 Araç tanımlayıcılarının, araç manifestolarında belgelenmiş olan gerekli ayrıcalıkları (okuma/yazma/çalıştırma), risk seviyelerini (düşük/orta/yüksek), kaynak sınırlarını (CPU, bellek, ağ) ve doğrulama gereksinimlerini belirten güvenlik meta verilerini içerdiğini doğrulayın.
 #9.12.2    Seviye: 1    Rol: D/V
 Araç yürütme sonuçlarının, entegrasyon öncesinde beklenen şemalarla (JSON Şeması, XML Şeması) ve güvenlik politikalarıyla (çıkışın temizlenmesi, veri sınıflandırması) doğrulandığını; ayrıca zaman aşımı sınırları ve hata yönetim prosedürleriyle kontrol edildiğini teyit edin.
 #9.12.3    Seviye: 2    Rol: D/V
 Araç etkileşim günlüklerinin, ayrıcalık kullanımı, veri erişim desenleri, yürütme süresi, kaynak tüketimi ve dönüş kodları dahil olmak üzere ayrıntılı güvenlik bağlamını içermesini ve SIEM entegrasyonu için yapılandırılmış günlük kaydını doğrulayın.
 #9.12.4    Seviye: 2    Rol: D/V
 Dinamik araç yükleme mekanizmalarının, dijital imzaları PKI altyapısı kullanarak doğruladığını ve yürütmeden önce kum havuzu izolasyonu ve izin doğrulama ile güvenli yükleme protokollerini uyguladığını doğrulayın.
 #9.12.5    Seviye: 3    Rol: D/V
 Araç güvenlik değerlendirmelerinin; statik analiz, dinamik test ve güvenlik ekibi incelemesini içeren zorunlu onay kapılarıyla birlikte belgelenmiş onay kriterleri ve SLA gereksinimleri doğrultusunda, yeni sürümler için otomatik olarak tetiklendiğini doğrulayın.

---

#### Referanslar

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

## 10 Düşmanca Dayanıklılık ve Gizlilik Koruması

### Kontrol Amacı

AI modellerinin, kaçınma, çıkarım, çıkarma veya zehirleme saldırılarıyla karşılaştığında güvenirliğini korumasını, gizliliği sağlamasını ve kötüye kullanıma karşı dirençli olmasını sağlamak.

---

### 10.1 Model Hizalaması ve Güvenliği

Zararlı veya politika ihlali oluşturan çıktılara karşı koruma sağlayın.

 #10.1.1    Seviye: 1    Rol: D/V
 Bir hizalama test paketi (kırmızı takım istemleri, jailbreak testleri, yasaklanmış içerik) sürüm kontrolünde olduğundan ve her model sürümünde çalıştırıldığından emin olun.
 #10.1.2    Seviye: 1    Rol: D
 Reddetme ve güvenli tamamlama koruma önlemlerinin uygulandığını doğrulayın.
 #10.1.3    Seviye: 2    Rol: D/V
 Otomatik bir değerlendiricinin zararlı içerik oranını ölçtüğünü ve belirli bir eşik değerin üzerinde gerilemeleri işaretlediğini doğrulayın.
 #10.1.4    Seviye: 2    Rol: D
 Karşı-jailbreak eğitiminin belgelenmiş ve tekrarlanabilir olduğunu doğrulayın.
 #10.1.5    Seviye: 3    Rol: V
 Resmi politika uyumluluk kanıtlarının veya sertifikalı izleme sistemlerinin kritik alanları kapsadığını doğrulayın.

---

### 10.2 Karşıt Örnek Sertleştirme

Manipüle edilmiş girdilere karşı dayanıklılığı artırın. Sağlam düşman eğitimi ve kıyaslama puanlaması mevcut en iyi uygulamalardır.

 #10.2.1    Seviye: 1    Rol: D
 Proje depolarının tekrarlanabilir tohumlarla adversarial eğitim yapılandırmalarını içerdiğini doğrulayın.
 #10.2.2    Seviye: 2    Rol: D/V
 Üretim hatlarında düşmanca örnek tespitin engelleme uyarıları verdiğini doğrulayın.
 #10.2.4    Seviye: 3    Rol: V
 Sertifikalı dayanıklılık kanıtlarının veya aralık sınırı sertifikalarının en azından en kritik üst sınıfları kapsadığını doğrulayın.
 #10.2.5    Seviye: 3    Rol: V
 Regresyon testlerinin, ölçülebilir bir sağlamlık kaybı olmadığını doğrulamak için adaptif saldırılar kullandığını kontrol edin.

---

### 10.3 Üyelik Çıkarımı Azaltma

Bir kaydın eğitim verisinde olup olmadığına karar verme yeteneğini sınırlayın. Diferansiyel gizlilik ve güven skorunun maskelemesi bilinen en etkili savunmalar olmaya devam etmektedir.

 #10.3.1    Seviye: 1    Rol: D
 Her sorgu için entropi düzenlemesinin veya sıcaklık ölçeklemenin aşırı özgüvenli tahminleri azalttığını doğrulayın.
 #10.3.2    Seviye: 2    Rol: D
 Hassas veri setleri için eğitimde ε-sınırlı farklı gizlilikte optimizasyon kullanıldığını doğrulayın.
 #10.3.3    Seviye: 2    Rol: V
 Saldırı simülasyonlarının (gölge model veya kara kutu) tutulmuş veride saldırı AUC’sinin ≤ 0,60 olduğunu doğrulayın.

---

### 10.4 Model-Tersiine Direnç

Özel özniteliklerin yeniden yapılandırılmasını önleyin. Son anketler, pratik savunmalar olarak çıktı kısaltması ve DP garantilerine vurgu yapmaktadır.

 #10.4.1    Seviye: 1    Rol: D
 Hassas özelliklerin asla doğrudan çıktılanmadığını doğrulayın; gerektiğinde kovalar veya tek yönlü dönüşümler kullanın.
 #10.4.2    Seviye: 1    Rol: D/V
 Aynı yetkili tarafından yapılan tekrarlanan adaptif sorguların sorgu hız sınırlarıyla kısıtlandığını doğrulayın.
 #10.4.3    Seviye: 2    Rol: D
 Modelin gizliliği koruyan gürültü ile eğitildiğini doğrulayın.

---

### 10.5 Model-Çıkarım Savunması

Yetkisiz klonlamayı tespit edin ve caydırın. Filigranlama ve sorgu-örüntüsü analizi önerilir.

 #10.5.1    Seviye: 1    Rol: D
 Çıkarım geçitlerinin, modelin ezberleme eşiğine göre ayarlanmış küresel ve API anahtarı başına hız sınırlarını uyguladığını doğrulayın.
 #10.5.2    Seviye: 2    Rol: D/V
 Sorgu-entropisi ve giriş-çoğulluk istatistiklerinin otomatik bir çıkarım algılayıcısına veri sağladığını doğrulayın.
 #10.5.3    Seviye: 2    Rol: V
 Kırılgan veya olasılıksal filigranların, şüpheli bir klon aleyhine yapılan en fazla 1 000 sorguda p < 0,01 ile kanıtlanabileceğini doğrulayın.
 #10.5.4    Seviye: 3    Rol: D
 Filigran anahtarlarının ve tetikleyici setlerinin bir donanım güvenlik modülünde saklandığını ve yıllık olarak döndürüldüğünü doğrulayın.
 #10.5.5    Seviye: 3    Rol: V
 Extraction-alert olaylarının suçlu sorguları içerdiğini ve olay müdahale oyun kitaplarıyla entegre edildiğini doğrulayın.

---

### 10.6 Çıkarım Zamanı Zehirlenmiş Veri Tespiti

Arka kapılı veya zehirlenmiş girdileri tanımlayın ve etkisiz hale getirin.

 #10.6.1    Seviye: 1    Rol: D
 Model çıkarımı öncesinde girdilerin bir anomali dedektöründen (örneğin, STRIP, tutarlılık puanlama) geçtiğini doğrulayın.
 #10.6.2    Seviye: 1    Rol: V
 Detektör eşiklerinin, %5'ten daha az yanlış pozitif oranı elde etmek için temiz/zehirlenmiş doğrulama setlerinde ayarlandığını doğrulayın.
 #10.6.3    Seviye: 2    Rol: D
 Zehirli olarak işaretlenen girdilerin yumuşak engelleme ve insan inceleme iş akışlarını tetiklediğini doğrulayın.
 #10.6.4    Seviye: 2    Rol: V
 Dedektörlerin, uyarlanabilir ve tetikleyicisiz arka kapı saldırılarıyla stres testine tabi tutulduğundan emin olun.
 #10.6.5    Seviye: 3    Rol: D
 Tespit etkinliği metriklerinin kaydedildiğini ve düzenli olarak güncel tehdit istihbaratı ile yeniden değerlendirildiğini doğrulayın.

---

### 10.7 Dinamik Güvenlik Politikası Uyarlaması

Tehdit istihbaratı ve davranışsal analizlere dayalı gerçek zamanlı güvenlik politikası güncellemeleri.

 #10.7.1    Seviye: 1    Rol: D/V
 Güvenlik politikalarının, politika sürümü bütünlüğü korunarak, ajan yeniden başlatılmadan dinamik olarak güncellenebildiğini doğrulayın.
 #10.7.2    Seviye: 2    Rol: D/V
 Politika güncellemelerinin yetkili güvenlik personeli tarafından kriptografik olarak imzalandığını ve uygulanmadan önce doğrulandığını doğrulayın.
 #10.7.3    Seviye: 2    Rol: D/V
 Dinamik politika değişikliklerinin, gerekçe, onay zincirleri ve geri alma prosedürleri dahil olmak üzere tam denetim izleriyle kaydedildiğini doğrulayın.
 #10.7.4    Seviye: 3    Rol: D/V
 Uyarlanabilir güvenlik mekanizmalarının tehdit algılama duyarlılığını risk bağlamı ve davranışsal kalıplara göre ayarladığını doğrulayın.
 #10.7.5    Seviye: 3    Rol: D/V
 Politika uyarlama kararlarının açıklanabilir olduğunu ve güvenlik ekibi incelemesi için kanıt izleri içerdiğini doğrulayın.

---

### 10.8 Yansıma Tabanlı Güvenlik Analizi

Ajanın kendi kendini yansıtması ve üstbilişsel analiz yoluyla güvenlik doğrulaması.

 #10.8.1    Seviye: 1    Rol: D/V
 Ajan yansıtma mekanizmalarının, kararlar ve eylemler üzerinde güvenlik odaklı öz değerlendirmeyi içerdiğini doğrulayın.
 #10.8.2    Seviye: 2    Rol: D/V
 Yansıtma çıktılarının, düşmanca girdilerle kendini değerlendirme mekanizmalarının manipülasyonunu önlemek için doğrulandığını teyit edin.
 #10.8.3    Seviye: 2    Rol: D/V
 Meta-bilişsel güvenlik analizinin, ajan muhakeme süreçlerindeki potansiyel önyargı, manipülasyon veya tehlike durumlarını tespit ettiğini doğrulayın.
 #10.8.4    Seviye: 3    Rol: D/V
 Yansıma tabanlı güvenlik uyarılarının gelişmiş izleme ve potansiyel insan müdahale iş akışlarını tetiklediğini doğrulayın.
 #10.8.5    Seviye: 3    Rol: D/V
 Güvenlik yansımalarından sürekli öğrenmenin, meşru işlevselliği bozmeden tehdit tespitini iyileştirdiğini doğrulayın.

---

### 10.9 Evrim ve Kendini Geliştirme Güvenliği

Kendi kendini değiştirebilme ve evrimleşebilme yeteneğine sahip ajan sistemler için güvenlik kontrolleri.

 #10.9.1    Seviye: 1    Rol: D/V
 Kendi kendini değiştirme yeteneklerinin, resmi doğrulama sınırlarıyla belirtilmiş güvenli alanlarla sınırlı olduğunun doğrulanması.
 #10.9.2    Seviye: 2    Rol: D/V
 Evrim önerilerinin uygulanmadan önce güvenlik etkisi değerlendirmesinden geçtiğini doğrulayın.
 #10.9.3    Seviye: 2    Rol: D/V
 Kendi kendini geliştirme mekanizmalarının, bütünlük doğrulamasıyla birlikte geri alma yeteneklerini içerdiğini doğrulayın.
 #10.9.4    Seviye: 3    Rol: D/V
 Meta-öğrenme güvenliğinin, geliştirme algoritmalarının kötü niyetli manipülasyonunu önlediğini doğrulayın.
 #10.9.5    Seviye: 3    Rol: D/V
 Özyinelemeli kendi kendini geliştirme işleminin, yakınsama matematiksel kanıtlarıyla birlikte, biçimsel güvenlik kısıtlarıyla sınırlı olduğunu doğrulayın.

---

#### Referanslar

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

Kişisel verilerin ancak net onay, asgari gerekli kapsam, kanıtlanabilir silme ve resmi gizlilik güvenceleri ile işlenmesini sağlamak için yapay zeka yaşam döngüsünün tamamında—toplama, eğitim, çıkarım ve olay müdahalesi süreçlerinde—katı gizlilik taahhütleri sürdürülmelidir.

---

### 11.1 Anonimleştirme ve Veri Azaltma

 #11.1.1    Seviye: 1    Rol: D/V
 Doğrudan ve yarı tanımlayıcıların kaldırıldığını, karma işlemine tabi tutulduğunu doğrulayın.
 #11.1.2    Seviye: 2    Rol: D/V
 Otomatik denetimlerin k-anonimlik/l-çeşitliliği ölçtüğünü ve eşik değerler politika altında düştüğünde uyarı verdiğini doğrulayın.
 #11.1.3    Seviye: 2    Rol: V
 Model özellik-önem raporlarının, ε = 0.01 karşılıklı bilgi sınırını aşan herhangi bir tanımlayıcı sızıntısını kanıtlamadığını doğrulayın.
 #11.1.4    Seviye: 3    Rol: V
 Bağlantı saldırıları altında bile yeniden tanımlama riskinin ≤ 0.05 olduğunu göstermek için resmi kanıtların veya sentetik veri sertifikasyonunun doğrulanmasını sağlayın.

---

### 11.2 Unutulma Hakkı ve Silme Zorlaması

 #11.2.1    Seviye: 1    Rol: D/V
 Veri konusu silme taleplerinin, hizmet seviyesi anlaşmaları kapsamında 30 günden daha kısa sürede ham veri setlerine, kontrol noktalarına, gömme işlemlerine, kayıt dosyalarına ve yedeklere iletildiğini doğrulayın.
 #11.2.2    Seviye: 2    Rol: D
 "Makine-unlearning" rutinlerinin sertifikalı unlearning algoritmaları kullanarak fiziksel olarak yeniden eğitme veya yaklaşık kaldırmayı sağladığını doğrulayın.
 #11.2.3    Seviye: 2    Rol: V
 Gölge-model değerlendirmesinin, unutma işleminden sonra unutulan kayıtların çıktılarının %1'inden daha azını etkilediğini kanıtladığını doğrulayın.
 #11.2.4    Seviye: 3    Rol: V
 Silme olaylarının değiştirilemez şekilde kaydedildiğini ve düzenleyiciler için denetlenebilir olduğunu doğrulayın.

---

### 11.3 Diferansiyel-Gizlilik Koruyucuları

 #11.3.1    Seviye: 2    Rol: D/V
 Toplam ε politika eşiklerini aştığında gizlilik kaybı muhasebesi panolarının uyarı verdiğini doğrulayın.
 #11.3.2    Seviye: 2    Rol: V
 Kara kutu gizlilik denetimlerinin, ε̂ değerini beyan edilen değerin %10’u içinde tahmin ettiğini doğrulayın.
 #11.3.3    Seviye: 3    Rol: V
 Resmi kanıtların tüm eğitim sonrası ince ayarları ve yerleştirmeleri kapsadığını doğrulayın.

---

### 11.4 Amaç-Sınırlama ve Kapsam Kayması Koruması

 #11.4.1    Seviye: 1    Rol: D
 Her veri seti ve model kontrol noktası için, orijinal onayla uyumlu makine tarafından okunabilir bir amaç etiketi bulunduğunu doğrulayın.
 #11.4.2    Seviye: 1    Rol: D/V
 Çalışma zamanı izleyicilerinin, beyan edilen amaçla tutarsız sorguları tespit ettiğini ve yumuşak reddi tetiklediğini doğrulayın.
 #11.4.3    Seviye: 3    Rol: D
 Politika-kod olarak belirlenen engellerin, DPIA incelemesi olmadan modellerin yeni alanlara yeniden dağıtımını engellediğini doğrulayın.
 #11.4.4    Seviye: 3    Rol: V
 Resmi izlenebilirlik kanıtlarının her kişisel veri yaşam döngüsünün onaylanmış kapsam içinde kaldığını gösterdiğini doğrulayın.

---

### 11.5 Onay Yönetimi ve Hukuka Uygun Dayanak Takibi

 #11.5.1    Seviye: 1    Rol: D/V
 Bir Onay Yönetim Platformunun (CMP), veri sahibi başına onay durumu, amaç ve saklama süresini kaydettiğini doğrulayın.
 #11.5.2    Seviye: 2    Rol: D
 API'lerin onay belirteçlerini açığa çıkardığını doğrulayın; modeller ön çıkarım yapmadan önce belirteç kapsamını doğrulamalıdır.
 #11.5.3    Seviye: 2    Rol: D/V
 Reddedilen veya geri çekilen onayın işleme boru hatlarını 24 saat içinde durdurduğunu doğrulayın.

---

### 11.6 Gizlilik Kontrolleri ile Federated Learning

 #11.6.1    Seviye: 1    Rol: D
 İstemci güncellemelerinin toplama öncesinde yerel diferansiyel gizlilik gürültüsü eklemesi kullandığını doğrulayın.
 #11.6.2    Seviye: 2    Rol: D/V
 Eğitim metriklerinin farklılaştırılmış gizlilikte olduğunu ve asla tek bir müşteriye ait kaybı açığa çıkarmadığını doğrulayın.
 #11.6.3    Seviye: 2    Rol: V
 Zehirlemeye dayanıklı toplama (örneğin, Krum/Trimmed-Mean) özelliğinin etkinleştirildiğini doğrulayın.
 #11.6.4    Seviye: 3    Rol: V
 Resmi kanıtların, toplam ε bütçesini 5'ten az fayda kaybıyla gösterdiğini doğrulayın.

---

#### Referanslar

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

## C12 İzleme, Günlük Kaydı ve Anomali Tespiti

### Kontrol Amacı

Bu bölüm, tehditlerin tespit edilebilmesi, önceliklendirilmesi ve öğrenilebilmesi için modelin ve diğer yapay zeka bileşenlerinin gördükleri, yaptıkları ve döndürdükleri konusunda gerçek zamanlı ve adli görünürlük sağlamaya yönelik gereksinimleri sunar.

### C12.1 İstek ve Yanıt Kaydı

 #12.1.1    Seviye: 1    Rol: D/V
 Tüm kullanıcı istemlerinin ve model yanıtlarının uygun meta verilerle (örneğin, zaman damgası, kullanıcı kimliği, oturum kimliği, model sürümü) kaydedildiğini doğrulayın.
 #12.1.2    Seviye: 1    Rol: D/V
 Günlüklerin uygun saklama politikaları ve yedekleme prosedürleriyle birlikte güvenli, erişim kontrollü depolarda saklandığını doğrulayın.
 #12.1.3    Seviye: 1    Rol: D/V
 Günlüklerde bulunan hassas bilgileri korumak için günlük depolama sistemlerinin dinlenme ve aktarım sırasında şifrelemeyi uyguladığını doğrulayın.
 #12.1.4    Seviye: 1    Rol: D/V
 Promplarda ve çıktılarda yer alan hassas verilerin, PII (kişisel tanımlanabilir bilgiler), kimlik bilgileri ve özel bilgi için yapılandırılabilir sansür kuralları ile kayda alınmadan önce otomatik olarak sansürlendiğini veya maskelendiğini doğrulayın.
 #12.1.5    Seviye: 2    Rol: D/V
 Politika kararlarının ve güvenlik filtreleme işlemlerinin, içerik denetim sistemlerinin denetimi ve hata ayıklaması için yeterli ayrıntıyla kaydedildiğini doğrulayın.
 #12.1.6    Seviye: 2    Rol: D/V
 Günlük bütünlüğünün, örneğin kriptografik imzalar veya yalnızca yazılabilir depolama kullanılarak korunduğunu doğrulayın.

---

### C12.2 Kötüye Kullanım Tespiti ve Uyarı Sistemi

 #12.2.1    Seviye: 1    Rol: D/V
 Sistem tarafından bilinen jailbreak desenlerinin, istem enjeksiyonu girişimlerinin ve düşmanca girdilerin imza tabanlı tespit ile algılanıp uyarı verdiğinin doğrulanması.
 #12.2.2    Seviye: 1    Rol: D/V
 Sistemin, standart günlük formatları ve protokolleri kullanarak mevcut Güvenlik Bilgi ve Olay Yönetimi (SIEM) platformlarıyla entegre olduğunu doğrulayın.
 #12.2.3    Seviye: 2    Rol: D/V
 Zenginleştirilmiş güvenlik olaylarının, model tanımlayıcıları, güven skorları ve güvenlik filtresi kararları gibi AI özel bağlamını içerdiğini doğrulayın.
 #12.2.4    Seviye: 2    Rol: D/V
 Davranışsal anomali tespitinin, alışılmadık konuşma kalıplarını, aşırı tekrar denemelerini veya sistematik sorgulama davranışlarını tanımladığını doğrulayın.
 #12.2.5    Seviye: 2    Rol: D/V
 Gerçek zamanlı uyarı mekanizmalarının, potansiyel politika ihlalleri veya saldırı girişimleri tespit edildiğinde güvenlik ekiplerini bilgilendirdiğini doğrulayın.
 #12.2.6    Seviye: 2    Rol: D/V
 AI'ye özgü tehdit desenlerini tespit etmek için özel kuralların dahil edildiğini doğrulayın; bunlar arasında koordineli jailbreak girişimleri, prompt enjeksiyonu kampanyaları ve model çıkarma saldırıları bulunmaktadır.
 #12.2.7    Seviye: 3    Rol: D/V
 Otomatik olay müdahale iş akışlarının, ele geçirilmiş modelleri izole edebildiğini, kötü niyetli kullanıcıları engelleyebildiğini ve kritik güvenlik olaylarını yükseltebildiğini doğrulayın.

---

### C12.3 Model Sapması Tespiti

 #12.3.1    Seviye: 1    Rol: D/V
 Sistemin model sürümleri ve zaman dilimleri boyunca doğruluk, güven skorları, gecikme ve hata oranları gibi temel performans metriklerini takip ettiğini doğrulayın.
 #12.3.2    Seviye: 2    Rol: D/V
 Otomatik uyarıların, performans metrikleri önceden belirlenmiş bozulma eşiklerini aştığında veya başlangıç değerlerinden önemli ölçüde saptığında tetiklendiğini doğrulayın.
 #12.3.3    Seviye: 2    Rol: D/V
 Halüsinasyon tespiti izleyicilerinin, model çıktılarının gerçeğe aykırı, tutarsız veya uydurma bilgiler içerdiği durumları tespit edip işaretlediğini doğrulayın.

---

### C12.4 Performans ve Davranış Telemetrijisi

 #12.4.1    Seviye: 1    Rol: D/V
 İstek gecikmesi, token tüketimi, bellek kullanımı ve verimlilik gibi operasyonel metriklerin sürekli olarak toplanıp izlenip izlenmediğini doğrulayın.
 #12.4.2    Seviye: 1    Rol: D/V
 Başarı ve başarısızlık oranlarının, hata türlerinin ve bunların temel nedenlerinin kategorize edilerek izlendiğini doğrulayın.
 #12.4.3    Seviye: 2    Rol: D/V
 Kaynak kullanım izleme işleminin GPU/CPU kullanımı, bellek tüketimi ve depolama gereksinimlerini içerdiğini ve eşik ihlallerinde uyarı verildiğini doğrulayın.

---

### C12.5 Yapay Zeka Olay Müdahale Planlaması ve Yürütülmesi

 #12.5.1    Seviye: 1    Rol: D/V
 Olay müdahale planlarının, model ihlali, veri zehirlenmesi ve düşmanca saldırılar dahil olmak üzere yapay zeka ile ilgili güvenlik olaylarını özellikle ele aldığını doğrulayın.
 #12.5.2    Seviye: 2    Rol: D/V
 Olay müdahale ekiplerinin, model davranışı ve saldırı vektörlerini araştırmak için yapay zeka özel adli bilişim araçlarına ve uzmanlığına erişimi olduğunu doğrulayın.
 #12.5.3    Seviye: 3    Rol: D/V
 Olay sonrası analizde model yeniden eğitimi dikkate alındığından, güvenlik filtresi güncellemelerinin yapıldığından ve edinilen derslerin güvenlik kontrollerine entegre edildiğinden emin olun.

---

### C12.5 AI Performans Bozulması Tespiti

AI model performansı ve kalitesindeki zaman içindeki bozulmayı izleyin ve tespit edin.

 #12.5.1    Seviye: 1    Rol: D/V
 Model doğruluğunun, kesinliğinin, duyarlılığının ve F1 skorlarının sürekli olarak izlenip temel eşik değerlerle karşılaştırıldığından emin olun.
 #12.5.2    Seviye: 1    Rol: D/V
 Veri sapması tespiti, model performansını etkileyebilecek giriş dağılımı değişikliklerini izler.
 #12.5.3    Seviye: 2    Rol: D/V
 Konsept kayması tespitin, girdiler ile beklenen çıktılar arasındaki ilişkideki değişiklikleri tanımladığını doğrulayın.
 #12.5.4    Seviye: 2    Rol: D/V
 Performans düşüşünün otomatik uyarılar tetiklediğini ve modelin yeniden eğitilmesi veya değiştirilmesi iş akışlarını başlattığını doğrulayın.
 #12.5.5    Seviye: 3    Rol: V
 Performans düşüşlerini veri değişiklikleri, altyapı sorunları veya dış etkenlerle ilişkilendiren bozulma kök neden analizini doğrulayın.

---

### C12.6 DAG Görselleştirme ve İş Akışı Güvenliği

İş akışı görselleştirme sistemlerini bilgi sızıntısı ve manipülasyon saldırılarından koruyun.

 #12.6.1    Seviye: 1    Rol: D/V
 DAG görselleştirme verilerinin depolama veya iletim öncesinde hassas bilgileri kaldırmak için temizlendiğini doğrulayın.
 #12.6.2    Seviye: 1    Rol: D/V
 İş akışı görselleştirme erişim kontrollerinin sadece yetkili kullanıcıların ajan karar yollarını ve gerekçe izlerini görüntüleyebildiğini doğrulayın.
 #12.6.3    Seviye: 2    Rol: D/V
 DAG veri bütünlüğünün kriptografik imzalar ve müdahaleye karşı kanıt sağlayan depolama mekanizmaları ile korunduğunu doğrulayın.
 #12.6.4    Seviye: 2    Rol: D/V
 İş akışı görselleştirme sistemlerinin, düzenlenmiş düğüm veya bağlantı verileri yoluyla enjeksiyon saldırılarını önlemek için giriş doğrulaması uyguladığını doğrulayın.
 #12.6.5    Seviye: 3    Rol: D/V
 Gerçek zamanlı DAG güncellemelerinin, görselleştirme sistemlerine yönelik hizmet reddi saldırılarını önlemek için hız sınırlamasına tabi tutulduğunu ve doğrulandığını kontrol edin.

---

### C12.7 Proaktif Güvenlik Davranışı İzleme

Güvenlik tehditlerinin tespit edilmesi ve önlenmesi, proaktif ajan davranışı analizi yoluyla.

 #12.7.1    Seviye: 1    Rol: D/V
 Proaktif ajan davranışlarının yürütmeden önce risk değerlendirme entegrasyonuyla güvenlik açısından doğrulandığını teyit edin.
 #12.7.2    Seviye: 2    Rol: D/V
 Otonom inisiyatif tetikleyicilerinin güvenlik bağlamı değerlendirmesi ve tehdit manzarası analizini içerdiğini doğrulayın.
 #12.7.3    Seviye: 2    Rol: D/V
 Proaktif davranış kalıplarının potansiyel güvenlik etkileri ve istenmeyen sonuçlar açısından analiz edildiğini doğrulayın.
 #12.7.4    Seviye: 3    Rol: D/V
 Güvenlik açısından kritik proaktif eylemlerin açık onay zincirleri ve denetim izleri gerektirdiğini doğrulayın.
 #12.7.5    Seviye: 3    Rol: D/V
 Davranışsal anomali tespitinin, tehlike gösterebilecek proaktif ajan kalıplarındaki sapmaları belirlediğini doğrulayın.

---

### Referanslar

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 İnsan Gözetimi, Hesap Verebilirlik ve Yönetişim

### Kontrol Amacı

Bu bölüm, AI sistemlerinde insan gözetiminin sürdürülmesi ve net hesap verebilirlik zincirlerinin sağlanması için gereksinimleri sunar; AI yaşam döngüsü boyunca açıklanabilirlik, şeffaflık ve etik yönetimi garanti eder.

---

### C13.1 Öldürme Anahtarı ve Geçersiz Kılma Mekanizmaları

AI sisteminin güvensiz davranışı gözlemlendiğinde kapanma veya geri alma yolları sağlayın.

 #13.1.1    Seviye: 1    Rol: D/V
 AI model çıkarımı ve çıktıları hemen durdurmak için manuel bir öldürme-kapama mekanizmasının var olduğunu doğrulayın.
 #13.1.2    Seviye: 1    Rol: D
 Geçersiz kılma kontrollerinin yalnızca yetkili personele erişilebilir olduğunu doğrulayın.
 #13.1.3    Seviye: 3    Rol: D/V
 Geri alma prosedürlerinin önceki model sürümlerine veya güvenli mod işlemlerine dönebileceğini doğrulayın.
 #13.1.4    Seviye: 3    Rol: V
 Üstünlük mekanizmalarının düzenli olarak test edildiğini doğrulayın.

---

### C13.2 İnsan-Döngüsünde Karar Kontrol Noktaları

Risk eşiklerini aştığında insan onayı gerektirir.

 #13.2.1    Seviye: 1    Rol: D/V
 Yüksek riskli yapay zeka kararlarının yürütülmeden önce açık insan onayı gerektirdiğini doğrulayın.
 #13.2.2    Seviye: 1    Rol: D
 Risk eşiklerinin net bir şekilde tanımlandığını ve otomatik olarak insan inceleme iş akışlarını tetiklediğini doğrulayın.
 #13.2.3    Seviye: 2    Rol: D
 Zaman duyarlı kararların, insan onayı gereken süre içinde alınamadığında yedek prosedürlere sahip olduğunu doğrulayın.
 #13.2.4    Seviye: 3    Rol: D/V
 Varsa, tırmanma prosedürlerinin farklı karar türleri veya risk kategorileri için net yetki seviyelerini belirttiğini doğrulayın.

---

### C13.3 Sorumluluk Zinciri ve Denetlenebilirlik

Operatör işlemlerini ve model kararlarını kaydedin.

 #13.3.1    Seviye: 1    Rol: D/V
 Tüm Yapay Zeka sistemi kararlarının ve insan müdahalelerinin zaman damgaları, kullanıcı kimlikleri ve karar gerekçeleri ile kaydedildiğini doğrulayın.
 #13.3.2    Seviye: 2    Rol: D
 Denetim kayıtlarının değiştirilmesinin imkansız olduğunu doğrulayın ve bütünlük doğrulama mekanizmalarını içermesini sağlayın.

---

### C13.4 Açıklanabilir-YZ Teknikleri

Yüzey özellik önemi, karşı-olaylar ve yerel açıklamalar.

 #13.4.1    Seviye: 1    Rol: D/V
 Yapay zeka sistemlerinin kararları için insan tarafından okunabilir formatta temel açıklamalar sağladığını doğrulayın.
 #13.4.2    Seviye: 2    Rol: V
 Açıklama kalitesinin insan değerlendirme çalışmaları ve metrikler aracılığıyla doğrulandığını teyit edin.
 #13.4.3    Seviye: 3    Rol: D/V
 Önemli kararlar için özellik önem puanları veya atıf yöntemlerinin (SHAP, LIME, vb.) mevcut olduğunu doğrulayın.
 #13.4.4    Seviye: 3    Rol: V
 Karşıt gerçeklik açıklamalarının, kullanım durumu ve alana uygulanabiliyorsa, girdilerin sonuçları değiştirmek için nasıl değiştirilebileceğini gösterdiğini doğrulayın.

---

### C13.5 Model Kartları ve Kullanım Açıklamaları

Model kartlarını amaçlanan kullanım, performans metrikleri ve etik hususlar için güncel tutun.

 #13.5.1    Seviye: 1    Rol: D
 Model kartlarının amaçlanan kullanım durumlarını, sınırlamalarını ve bilinen hata modlarını belgelediğini doğrulayın.
 #13.5.2    Seviye: 1    Rol: D/V
 Farklı uygulanabilir kullanım senaryoları arasında performans metriklerinin açıklandığını doğrulayın.
 #13.5.3    Seviye: 2    Rol: D
 Etik değerlendirmelerin, önyargı analizlerinin, adalet değerlendirmelerinin, eğitim veri özelliklerinin ve bilinen eğitim veri sınırlamalarının belgelenip düzenli olarak güncellendiğini doğrulayın.
 #13.5.4    Seviye: 2    Rol: D/V
 Model kartlarının sürüm kontrolünün yapıldığını ve değişiklik takibi ile model yaşam döngüsü boyunca korunduğunu doğrulayın.

---

### C13.6 Belirsizlik Nicelleştirme

Yanıtlar içinde güven skorlarını veya entropi ölçümlerini yaydırın.

 #13.6.1    Seviye: 1    Rol: D
 AI sistemlerinin çıktılarıyla birlikte güven skorları veya belirsizlik ölçüleri sağladığını doğrulayın.
 #13.6.2    Seviye: 2    Rol: D/V
 Belirsizlik eşiklerinin ek insan incelemesini veya alternatif karar yollarını tetiklediğini doğrulayın.
 #13.6.3    Seviye: 2    Rol: V
 Belirsizlik nicelleme yöntemlerinin kalibre edilmiş ve gerçek veri ile doğrulanmış olduğunu teyit edin.
 #13.6.4    Seviye: 3    Rol: D/V
 Belirsizlik yayılımının çok adımlı AI iş akışları boyunca sürdürüldüğünü doğrulayın.

---

### C13.7 Kullanıcıya Yönelik Şeffaflık Raporları

Olaylar, sapma ve veri kullanımı hakkında periyodik bildirimler sağlayın.

 #13.7.1    Seviye: 1    Rol: D/V
 Veri kullanımı politikalarının ve kullanıcı onay yönetimi uygulamalarının paydaşlara açıkça iletildiğini doğrulayın.
 #13.7.2    Seviye: 2    Rol: D/V
 Yapay zeka etki değerlendirmelerinin yapıldığını ve sonuçların raporlamaya dahil edildiğini doğrulayın.
 #13.7.3    Seviye: 2    Rol: D/V
 Düzenli olarak yayınlanan şeffaflık raporlarının, makul ayrıntılarla Yapay Zeka olaylarını ve operasyonel metrikleri açıkladığını doğrulayın.

#### Referanslar

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

Bu kapsamlı sözlük, AISVS genelinde kullanılan temel AI, ML ve güvenlik terimlerinin tanımlarını sunarak açıklık ve ortak anlayış sağlamaktadır.

Rakip Örnek: İnsanların fark edemeyeceği ince bozulmalar ekleyerek bir yapay zeka modelinin hata yapmasına neden olmak için kasıtlı olarak hazırlanmış bir giriş.
​
Rekabetçi Dayanıklılık – Yapay zekada rekabetçi dayanıklılık, bir modelin performansını koruma ve hataya sebep olmak için kasıtlı olarak tasarlanmış kötü niyetli girdiler tarafından kandırılmaya veya manipüle edilmeye karşı direnç gösterme yeteneğini ifade eder.
​
Agent – Yapay zeka ajanları, kullanıcılar adına hedeflere ulaşmak ve görevleri tamamlamak için yapay zekayı kullanan yazılım sistemleridir. Akıl yürütme, planlama ve hafıza gösterirler ve karar verme, öğrenme ve uyum sağlama konusunda belirli bir özerkliğe sahiptirler.
​
Agentik AI: Belirli bir dereceye kadar özerklikle hedeflere ulaşabilen, genellikle doğrudan insan müdahalesi olmadan kararlar alan ve eylemler gerçekleştiren AI sistemleri.
​
Öznitelik Tabanlı Erişim Kontrolü (ABAC): Yetkilendirme kararlarının, sorgu zamanında değerlendirilen kullanıcının, kaynağın, eylemin ve çevrenin özniteliklerine dayandığı bir erişim kontrol paradigması.
​
Arka Kapı Saldırısı: Modelin belirli tetikleyicilere karşı özel bir şekilde yanıt vermesi için eğitildiği, aksi takdirde normal davrandığı bir tür veri zehirleme saldırısıdır.
​
Önyargı: Belirli gruplar veya belirli bağlamlarda adaletsiz veya ayrımcı sonuçlara yol açabilen yapay zeka modeli çıktılarındaki sistematik hatalar.
​
Önyargı Sömürüsü: Çıktıları veya sonuçları manipüle etmek için yapay zeka modellerindeki bilinen önyargılardan yararlanan bir saldırı tekniği.
​
Cedar: AI sistemleri için ABAC uygulanmasında kullanılan ayrıntılı izinler için Amazon’un politika dili ve motoru.
​
Düşünce Zinciri: Son cevabı üretmeden önce ara akıl yürütme adımları oluşturarak dil modellerindeki akıl yürütmeyi geliştirme tekniği.
​
Devre Kesiciler: Belirli risk eşiklerinin aşılması durumunda yapay zeka sistemi işlemlerini otomatik olarak durduran mekanizmalar.
​
Veri Sızıntısı: AI modeli çıktıları veya davranışı aracılığıyla hassas bilgilerin istem dışı ifşası.
​
Veri Zehirlenmesi: Model bütünlüğünü tehlikeye atmak amacıyla eğitim verilerinin kasıtlı olarak bozulması, genellikle arka kapılar kurmak veya performansı düşürmek için.
​
Diferansiyel Mahremiyet – Diferansiyel mahremiyet, bireysel veri sahiplerinin gizliliğini korurken veri setleri hakkında istatistiksel bilgilerin yayınlanması için matematiksel olarak sağlam bir çerçevedir. Bu, veri sahibinin grup genelindeki toplu desenleri paylaşmasına olanak tanırken, belirli bireyler hakkında sızan bilgileri sınırlar.
​
Gömülü Temsiller: Verinin (metin, resimler vb.) yüksek boyutlu bir uzayda anlamsal anlamını yakalayan yoğun vektör temsilleri.
​
Açıklanabilirlik – Yapay zekada açıklanabilirlik, bir yapay zeka sisteminin kararları ve tahminleri için insan tarafından anlaşılabilir nedenler sunma yeteneğidir; bu da sistemin iç işleyişine dair içgörüler sağlamaktadır.
​
Açıklanabilir Yapay Zeka (XAI): Kararları ve davranışları için insan tarafından anlaşılabilir açıklamalar sunmak üzere çeşitli teknikler ve çerçeveler kullanarak tasarlanmış yapay zeka sistemleri.
​
Federated Learning: Verilerin kendisi değiş tokuş edilmeden, yerel veri örneklerine sahip çok sayıda merkezi olmayan cihaz üzerinde modellerin eğitildiği bir makine öğrenimi yaklaşımı.
​
Koruyucu Önlemler: Yapay zeka sistemlerinin zararlı, yanlı veya diğer istenmeyen çıktılar üretmesini önlemek için uygulanan kısıtlamalar.
​
Halüsinasyon – Bir yapay zeka halüsinasyonu, bir yapay zeka modelinin eğitim verilerine veya gerçek olgulara dayanmayan, yanlış veya yanıltıcı bilgi üretmesi durumunu ifade eder.
​
İnsanlı Döngü (HITL): Önemli karar noktalarında insan denetimi, doğrulaması veya müdahalesi gerektirecek şekilde tasarlanmış sistemler.
​
Kod olarak Altyapı (IaC): Altyapıyı manuel süreçler yerine kod aracılığıyla yönetme ve sağlama, bu sayede güvenlik taraması ve tutarlı dağıtımların mümkün kılınması.
​
Jailbreak: Özellikle büyük dil modellerinde, yasaklanmış içerik üretmek için yapay zeka sistemlerindeki güvenlik önlemlerini aşmak amacıyla kullanılan teknikler.
​
En Az Ayrıcalık: Kullanıcılar ve süreçler için yalnızca gerekli minimum erişim haklarının verilmesi güvenlik prensibi.
​
LIME (Yerel Yorumlanabilir Model-Agnostik Açıklamalar): Herhangi bir makine öğrenimi sınıflandırıcısının tahminlerini, yerel olarak yorumlanabilir bir modelle yaklaşık olarak açıklamak için bir teknik.
​
Üyelik Çıkarımı Saldırısı: Belirli bir veri noktasının bir makine öğrenimi modelini eğitmek için kullanılıp kullanılmadığını belirlemeyi amaçlayan bir saldırı.
​
MITRE ATLAS: Yapay Zeka Sistemleri için Düşmanca Tehdit Manzarası; yapay zeka sistemlerine karşı düşmanca taktikler ve tekniklerin bilgi tabanı.
​
Model Kartı – Model kartı, bir yapay zeka modelinin performansı, sınırlamaları, amaçlanan kullanımları ve etik değerlendirmeleri hakkında standartlaştırılmış bilgiler sağlayan, şeffaflığı ve sorumlu yapay zeka geliştirmeyi teşvik eden bir belgedir.
​
Model Çıkarımı: Bir saldırı türü olup, saldırganın hedef modeli yetkisiz olarak işlevsel olarak benzer bir kopya oluşturmak için tekrar tekrar sorgulamasıdır.
​
Model İnversiyonu: Model çıktıları analiz edilerek eğitim verilerini yeniden oluşturmayı amaçlayan bir saldırı.
​
Model Yaşam Döngüsü Yönetimi – AI Model Yaşam Döngüsü Yönetimi, bir yapay zeka modelinin tasarımı, geliştirilmesi, dağıtımı, izlenmesi, bakımı ve nihai emekliliği dahil olmak üzere tüm varlık aşamalarının denetlenmesi sürecidir; böylece modelin etkili kalması ve hedeflerle uyumlu olması sağlanır.
​
Model Zehirleme: Eğitme süreci sırasında doğrudan bir modele güvenlik açıkları veya arka kapılar eklemek.
​
Model Çalma/Hırsızlığı: Tekrarlanan sorgular yoluyla bir tescilli modelin kopyasının veya yaklaşık bir versiyonunun çıkarılması.
​
Çok ajanlı Sistem: Farklı yeteneklere ve hedeflere sahip olabilecek birden çok etkileşimde bulunan Yapay Zeka ajanından oluşan bir sistem.
​
OPA (Open Policy Agent): Yığın genelinde birleşik politika uygulamasını sağlayan açık kaynaklı bir politika motoru.
​
Gizliliği Koruyan Makine Öğrenimi (PPML): Eğitim verilerinin gizliliğini korurken ML modellerini eğitmek ve dağıtmak için teknikler ve yöntemler.
​
Prompt Enjeksiyonu: Kötü niyetli talimatların, bir modelin amaçlanan davranışını geçersiz kılmak için girdilere gömüldüğü bir saldırı türü.
​
RAG (Retrieval-Augmented Generation): Yanıt oluşturmadan önce harici bilgi kaynaklarından ilgili bilgileri alarak büyük dil modellerini geliştiren bir tekniktir.
​
Kırmızı Takım Çalışması: Zayıf noktaları belirlemek için yapay zeka sistemlerini düşmanca saldırılar simüle ederek aktif olarak test etme uygulaması.
​
SBOM (Yazılım Malzeme Listesi): Yazılım veya yapay zeka modelleri oluşturulurken kullanılan çeşitli bileşenlerin detaylarını ve tedarik zinciri ilişkilerini içeren resmi kayıt.
​
SHAP (SHapley Additive exPlanations): Herhangi bir makine öğrenimi modelinin çıktısını açıklamak için her özelliğin tahmine katkısını hesaplayan oyun teorisi temelli bir yaklaşımdır.
​
Tedarik Zinciri Saldırısı: Üçüncü taraf kütüphaneler, veri setleri veya önceden eğitilmiş modeller gibi tedarik zincirindeki daha az güvenli unsurları hedef alarak bir sistemi tehlikeye atma.
​
Transfer Learning: Bir görev için geliştirilen bir modelin, ikinci bir görevde kullanılacak model için başlangıç noktası olarak yeniden kullanıldığı bir tekniktir.
​
Vektör Veritabanı: Yüksek boyutlu vektörleri (gömülü temsilleri) depolamak ve etkili benzerlik aramaları yapmak için tasarlanmış özel bir veritabanı.
​
Zafiyet Tarama: AI çerçeveleri ve bağımlılıkları dahil olmak üzere yazılım bileşenlerindeki bilinen güvenlik açıklarını tanımlayan otomatik araçlar.
​
Filigranlama: AI tarafından oluşturulan içeriklerde kaynağını takip etmek veya AI üretimini tespit etmek için algılanamayan işaretler yerleştirme teknikleri.
​
Sıfır-Gün Açığı: Geliştiriciler bir yama oluşturup dağıtmadan önce saldırganların istismar edebileceği daha önce bilinmeyen bir güvenlik açığı.

## Ek B: Kaynaklar

### TODO

## Ek C: AI Güvenlik Yönetişimi ve Dokümantasyon

### Amaç

Bu ek, sistem yaşam döngüsü boyunca AI güvenliğini yönetmek için örgütsel yapılar, politikalar ve süreçlerin kurulmasına yönelik temel gereksinimleri sağlar.

---

### AC.1 Yapay Zeka Risk Yönetimi Çerçevesi Kabulü

Sistem yaşam döngüsü boyunca yapay zekaya özgü riskleri tanımlamak, değerlendirmek ve azaltmak için resmi bir çerçeve sağlayın.

 #AC.1.1    Seviye: 1    Rol: D/V
 Bir yapay zeka (YZ) özel risk değerlendirme metodolojisinin belgelendiğini ve uygulandığını doğrulayın.
 #AC.1.2    Seviye: 2    Rol: D
 AI yaşam döngüsündeki kilit noktalarda ve önemli değişiklikler öncesinde risk değerlendirmelerinin yapıldığını doğrulayın.
 #AC.1.3    Seviye: 3    Rol: D/V
 Risk yönetim çerçevesinin, belirlenmiş standartlarla (örneğin, NIST AI RMF) uyumlu olduğunu doğrulayın.

---

### AC.2 AI Güvenlik Politikası ve Prosedürleri

Güvenli yapay zeka geliştirme, dağıtım ve işletme için kurumsal standartları tanımlayın ve uygulayın.

 #AC.2.1    Seviye: 1    Rol: D/V
 Belgelenmiş AI güvenlik politikalarının var olduğunu doğrulayın.
 #AC.2.2    Seviye: 2    Rol: D
 Politikaların en az yılda bir kez ve önemli tehdit ortamı değişikliklerinden sonra gözden geçirildiğini ve güncellendiğini doğrulayın.
 #AC.2.3    Seviye: 3    Rol: D/V
 Politikaların tüm AISVS kategorilerini ve geçerli düzenleyici gereklilikleri kapsadığını doğrulayın.

---

### AC.3 AI Güvenliği için Roller ve Sorumluluklar

Kuruluş genelinde yapay zeka güvenliği için net sorumluluklar belirleyin.

 #AC.3.1    Seviye: 1    Rol: D/V
 Yapay zeka güvenlik rolleri ve sorumluluklarının belgelenip belgelenmediğini doğrulayın.
 #AC.3.2    Seviye: 2    Rol: D
 Sorumlu kişilerin uygun güvenlik uzmanlığına sahip olduğunu doğrulayın.
 #AC.3.3    Seviye: 3    Rol: D/V
 Yüksek riskli yapay zeka sistemleri için bir yapay zeka etik komitesi veya yönetişim kurulu kurulduğunu doğrulayın.

---

### AC.4 Etik Yapay Zeka İlkelerinin Uygulanması

Yapay zeka sistemlerinin belirlenmiş etik ilkelere uygun şekilde çalışmasını sağlamak.

 #AC.4.1    Seviye: 1    Rol: D/V
 Yapay zeka geliştirme ve uygulanması için etik yönergelerin var olduğunu doğrulayın.
 #AC.4.2    Seviye: 2    Rol: D
 Etik ihlalleri tespit etmek ve raporlamak için mekanizmaların mevcut olduğunu doğrulayın.
 #AC.4.3    Seviye: 3    Rol: D/V
 Uygulanan yapay zeka sistemlerinin düzenli etik incelemelerinin yapıldığını doğrulayın.

---

### AC.5 AI Düzenleyici Uyum İzleme

Gelişen yapay zeka düzenlemeleri konusunda farkındalığı ve uyumu sürdürün.

 #AC.5.1    Seviye: 1    Rol: D/V
 Uygulanabilir AI düzenlemelerini belirlemek için süreçlerin var olduğunu doğrulayın.
 #AC.5.2    Seviye: 2    Rol: D
 Tüm düzenleyici gerekliliklere uyumun değerlendirilmesini doğrulayın.
 #AC.5.3    Seviye: 3    Rol: D/V
 Düzenleyici değişikliklerin yapay zeka sistemlerinde zamanında incelemeleri ve güncellemeleri tetiklediğini doğrulayın.

### AC.6 Eğitim Verisi Yönetimi, Dokümantasyon ve Süreç

 #1.1.2    Seviye: 1    Rol: D/V
 Yalnızca kalite, temsil kabiliyeti, etik kaynak kullanımı ve lisans uyumluluğu açısından doğrulanmış veri setlerinin kullanılmasına izin verildiğini doğrulayarak, zehirlenme, gömülü önyargı ve fikri mülkiyet ihlali risklerini azaltın.
 #1.1.5    Seviye: 2    Rol: D/V
 Etiketleme/yorumlama kalitesinin, inceleyenlerin karşılıklı kontrolleri veya fikir birliği yoluyla sağlandığını doğrulayın.
 #1.1.6    Seviye: 2    Rol: D/V
 Önemli eğitim veri setleri için "veri kartlarının" veya "veri setleri için veri sayfalarının" tutulduğunu doğrulayın; bu belgeler özellikler, amaçlar, bileşim, toplama süreçleri, ön işleme ve önerilen/önerilmeyen kullanımlar hakkında ayrıntılı bilgi içermelidir.
 #1.3.2    Seviye: 2    Rol: D/V
 Belirlenen önyargıların, yeniden dengeleme, hedeflenmiş veri artırımı, algoritmik ayarlamalar (örneğin, ön işleme, işlem içi ve işlem sonrası teknikler) veya yeniden ağırlıklandırma gibi belgelenmiş stratejilerle hafifletildiği doğrulanmalı ve hafifletmenin hem adalet hem de genel model performansı üzerindeki etkisi değerlendirilmelidir.
 #1.3.3    Seviye: 2    Rol: D/V
 Eğitim sonrası adalet metriklerinin değerlendirildiğinden ve belgelenmiş olduğundan emin olun.
 #1.3.4    Seviye: 3    Rol: D/V
 Bir yaşam döngüsü önyargı yönetimi politikasının sahipleri ve inceleme sıklığını atadığını doğrulayın.
 #1.4.1    Seviye: 2    Rol: D/V
 Etiketleme/örnekleme kalitesinin, net yönergeler, değerlendirici çapraz kontrolleri, uzlaşma mekanizmaları (örneğin, değerlendiriciler arası uyumun izlenmesi) ve tutarsızlıkların çözümü için tanımlanmış süreçler aracılığıyla sağlandığını doğrulayın.
 #1.4.4    Seviye: 3    Rol: D/V
 Güvenlik, emniyet veya adalet açısından kritik olan etiketlerin (örneğin, zararlı içeriği tanımlayan, kritik tıbbi bulguları içeren) zorunlu bağımsız çift incelemeden veya eşdeğer sağlam doğrulamadan geçmesini sağlayın.
 #1.4.6    Seviye: 2    Rol: D/V
 Etiketleme rehberlerinin ve talimatlarının kapsamlı, sürüm kontrolüne tabi ve akran değerlendirmesinden geçmiş olduğunu doğrulayın.
 #1.4.6    Seviye: 2    Rol: D/V
 Etiketler için veri şemalarının net bir şekilde tanımlandığını ve sürüm kontrolünün yapıldığını doğrulayın.
 #1.3.1    Seviye: 1    Rol: D/V
 Veri setlerinin, yasal olarak korunan özellikler (örneğin, ırk, cinsiyet, yaş) ve modelin uygulama alanıyla ilgili diğer etik açıdan hassas özellikler (örneğin, sosyo-ekonomik durum, konum) açısından temsil dengesizliği ve potansiyel önyargılar için profillendiğini doğrulayın.
 #1.5.3    Seviye: 2    Rol: V
 Alan uzmanları tarafından yapılan manuel rastgele kontrollerin, otomasyon tarafından tespit edilemeyen ince kalite sorunlarını belirlemek için istatistiksel olarak anlamlı bir örneklem (örneğin, ≥%1 veya 1.000 örnek, hangisi daha büyükse veya risk değerlendirmesi ile belirlenen) kapsadığını doğrulayın.
 #1.8.4    Seviye: 2    Rol: D/V
 Dış kaynaklı veya kitle kaynaklı etiketleme iş akışlarının, veri gizliliği, bütünlüğü, etiket kalitesi sağlamak ve veri sızıntısını önlemek için teknik/prosedürel güvenlik önlemlerini içerdiğini doğrulayın.
 #1.5.4    Seviye: 2    Rol: D/V
 Düzeltme adımlarının kaynak kayıtlarına eklendiğini doğrulayın.
 #1.6.2    Seviye: 2    Rol: D/V
 İşaretlenen örneklerin eğitime başlamadan önce manuel incelemeyi tetiklediğini doğrulayın.
 #1.6.3    Seviye: 2    Rol: V
 Sonuçların, modelin güvenlik dosyasını beslediğini ve devam eden tehdit istihbaratını bilgilendirdiğini doğrulayın.
 #1.6.4    Seviye: 3    Rol: D/V
 Tespit mantığının yeni tehdit istihbaratı ile güncellendiğini doğrulayın.
 #1.6.5    Seviye: 3    Rol: D/V
 Çevrimiçi öğrenme boru hatlarının dağılım sapmasını izlediğini doğrulayın.
 #1.7.1    Seviye: 1    Rol: D/V
 Eğitim verisi silme iş akışlarının birincil ve türetilmiş verileri temizlediğini ve model üzerindeki etkisini doğrulayın; ayrıca etkilenen modeller üzerindeki etkinin değerlendirildiğinden ve gerekirse yeniden eğitim veya yeniden kalibrasyon yoluyla ele alındığından emin olun.
 #1.7.2    Seviye: 2    Rol: D
 Kullanıcı onayının kapsamını ve durumunu (ve geri çekmelerini) izlemek ve saygı göstermek için mekanizmaların mevcut olduğunu ve onayın, verilerin yeni eğitim süreçlerine veya önemli model güncellemelerine dahil edilmeden önce doğrulandığını kontrol edin.
 #1.7.3    Seviye: 2    Rol: V
 İş akışlarının yıllık olarak test edildiğini ve kaydedildiğini doğrulayın.
 #1.8.1    Seviye: 2    Rol: D/V
 Üçüncü taraf veri tedarikçilerinin, önceden eğitilmiş modellerin ve harici veri setlerinin sağlayıcıları da dahil olmak üzere, verileri veya modelleri entegre edilmeden önce güvenlik, gizlilik, etik kaynak kullanımı ve veri kalitesi açısından durum tespiti süreçlerinden geçtiğini doğrulayın.
 #1.8.2    Seviye: 1    Rol: D
 Harici transferlerin TLS/doğrulama ve bütünlük kontrolleri kullandığını doğrulayın.
 #1.8.3    Seviye: 2    Rol: D/V
 Yüksek riskli veri kaynaklarının (örneğin, bilinmeyen kaynaklardan elde edilen açık kaynak veri setleri, doğrulanmamış tedarikçiler) kullanılan duyarlı uygulamalarda kullanılmadan önce, sandbox analizi, kapsamlı kalite/yanlılık kontrolleri ve hedefli zehirlenme tespiti gibi artırılmış incelemeye tabi tutulduğundan emin olun.
 #1.8.4    Seviye: 3    Rol: D/V
 Üçüncü taraflardan elde edilen önceden eğitilmiş modellerin, ince ayar yapılmadan veya dağıtıma alınmadan önce gömülü önyargılar, potansiyel arka kapılar, mimarilerinin bütünlüğü ve orijinal eğitim verilerinin kaynakları açısından değerlendirildiğini doğrulayın.
 #1.5.3    Seviye: 2    Rol: D/V
 Adversarial eğitim kullanılıyorsa, adversarial veri setlerinin oluşturulması, yönetimi ve versiyonlamasının belgelenip kontrol edildiğini doğrulayın.
 #1.5.3    Seviye: 3    Rol: D/V
 Adversarial dayanıklılık eğitiminin model performansı (hem temiz hem de adversaryal girdilere karşı) ve adalet metrikleri üzerindeki etkisinin değerlendirildiğini, belgelendiğini ve izlendiğini doğrulayın.
 #1.5.4    Seviye: 3    Rol: D/V
 Evrilen düşmanca saldırı tekniklerine karşı koymak için düşmanca eğitim ve dayanıklılık stratejilerinin periyodik olarak gözden geçirilip güncellendiğini doğrulayın.
 #1.4.2    Seviye: 2    Rol: D/V
 Başarısız veri setlerinin denetim izleri ile karantinaya alındığını doğrulayın.
 #1.4.3    Seviye: 2    Rol: D/V
 Kalite kapılarının, istisnalar onaylanmadıkça düşük kaliteli veri setlerini engellediğini doğrulayın.
 #1.11.2    Seviye: 2    Rol: D/V
 Sentetik verinin oluşturulma süreci, parametreleri ve amaçlanan kullanımı belgelenmiş olduğundan emin olun.
 #1.11.3    Seviye: 2    Rol: D/V
 Sentetik verinin eğitim için kullanılmadan önce önyargı, gizlilik sızıntısı ve temsiliyet sorunları açısından risk değerlendirmesinin yapılmasını doğrulayın.
 #1.12.3    Seviye: 2    Rol: D/V
 Şüpheli erişim olayları için uyarıların oluşturulduğunu ve derhal araştırıldığını doğrulayın.
 #1.13.1    Seviye: 1    Rol: D/V
 Tüm eğitim veri setleri için açık tutulma sürelerinin tanımlandığını doğrulayın.
 #1.13.2    Seviye: 2    Rol: D/V
 Veri setlerinin yaşam döngülerinin sonunda otomatik olarak süresinin dolduğunu, silindiğini veya silinme için gözden geçirildiğini doğrulayın.
 #1.13.3    Seviye: 2    Rol: D/V
 Saklama ve silme işlemlerinin kaydedildiğini ve denetlenebilir olduğunu doğrulayın.
 #1.14.1    Seviye: 2    Rol: D/V
 Tüm veri kümeleri için veri yerleşimi ve sınır ötesi transfer gereksinimlerinin tanımlandığını ve uygulandığını doğrulayın.
 #1.14.2    Seviye: 2    Rol: D/V
 Sektör spesifik düzenlemelerin (örneğin, sağlık, finans) tespit edildiğini ve veri işlemede ele alındığını doğrulayın.
 #1.14.3    Seviye: 2    Rol: D/V
 İlgili gizlilik yasalarına (örneğin, GDPR, CCPA) uyumun belgelenip düzenli olarak gözden geçirildiğini doğrulayın.
 #1.16.1    Seviye: 2    Rol: D/V
 Veri sahibi taleplerine erişim, düzeltme, kısıtlama veya itiraz için yanıt verilebilmesi amacıyla mekanizmaların var olduğunu doğrulayın.
 #1.16.2    Seviye: 2    Rol: D/V
 Taleplerin yasal olarak zorunlu kılınan süreler içinde kaydedildiğini, takip edildiğini ve yerine getirildiğini doğrulayın.
 #1.16.3    Seviye: 2    Rol: D/V
 Veri sahibi hakları süreçlerinin etkinliği için düzenli olarak test edildiği ve gözden geçirildiği doğrulanmalıdır.
 #1.17.1    Seviye: 2    Rol: D/V
 Bir veri seti sürümünü güncellemeden veya değiştirmeden önce, model performansı, adalet ve uyumluluğu kapsayan bir etki analizinin yapıldığını doğrulayın.
 #1.17.2    Seviye: 2    Rol: D/V
 Etkileşim analizinin sonuçlarının belgelenip ilgili paydaşlar tarafından incelendiğini doğrulayın.
 #1.17.3    Seviye: 2    Rol: D/V
 Yeni sürümler kabul edilemez riskler veya gerilemeler getirdiğinde geri alma planlarının mevcut olduğunu doğrulayın.
 #1.18.1    Seviye: 2    Rol: D/V
 Veri açıklamasıyla ilgili tüm personelin arka plan kontrolünden geçirildiğini ve veri güvenliği ile gizliliği konusunda eğitim aldığını doğrulayın.
 #1.18.2    Seviye: 2    Rol: D/V
 Tüm anotasyon personelinin gizlilik ve gizlilik sözleşmelerini imzaladığını doğrulayın.
 #1.18.3    Seviye: 2    Rol: D/V
 Anotasyon platformlarının erişim kontrollerini uyguladığını ve içeriden gelebilecek tehditleri izlediğini doğrulayın.

#### Referanslar

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Ek D: Yapay Zeka Destekli Güvenli Kodlama Yönetimi ve Doğrulaması

### Amaç

Bu bölüm, yazılım geliştirme sürecinde AI destekli kodlama araçlarının güvenli ve etkili kullanımına yönelik temel organizasyonel kontrolleri tanımlayarak, SDLC boyunca güvenlik ve izlenebilirlik sağlamaktadır.

---

### AD.1 Yapay Zeka Destekli Güvenli Kodlama İş Akışı

AI araçlarını, mevcut güvenlik kapılarını zayıflatmadan, kuruluşun güvenli yazılım geliştirme yaşam döngüsüne (SSDLC) entegre edin.

 #AD.1.1    Seviye: 1    Rol: D/V
 Belgelenmiş bir iş akışının, yapay zeka araçlarının kodu ne zaman ve nasıl oluşturabileceğini, yeniden düzenleyebileceğini veya inceleyebileceğini tanımladığını doğrulayın.
 #AD.1.2    Seviye: 2    Rol: D
 İş akışının her SSDLC aşamasına (tasarım, uygulama, kod incelemesi, test, dağıtım) uyduğunu doğrulayın.
 #AD.1.3    Seviye: 3    Rol: D/V
 AI tarafından üretilen kod üzerinde ölçütlerin (örneğin, güvenlik açığı yoğunluğu, ortalama tespit süresi) toplanıp toplanmadığını ve insan kaynaklı temel değerlerle karşılaştırılıp karşılaştırılmadığını doğrulayın.

---

### AD.2 Yapay Zeka Aracı Nitelendirme ve Tehdit Modelleme

Yapay zeka kodlama araçlarının benimsenmeden önce güvenlik yetenekleri, riskleri ve tedarik zinciri etkileri açısından değerlendirilmesini sağlayın.

 #AD.2.1    Seviye: 1    Rol: D/V
 Her AI aracı için tehdit modelinin, kötüye kullanım, model tersine çevirme, veri sızıntısı ve bağımlılık zinciri risklerini tanımladığını doğrulayın.
 #AD.2.2    Seviye: 2    Rol: D
 Araç değerlendirmelerinin, herhangi bir yerel bileşenin statik/dinamik analizini ve SaaS uç noktalarının (TLS, kimlik doğrulama/izinlendirme, kayıt tutma) değerlendirmesini içerdiğini doğrulayın.
 #AD.2.3    Seviye: 3    Rol: D/V
 Değerlendirmelerin tanınmış bir çerçeveye uygun olduğunu ve büyük sürüm değişikliklerinden sonra yeniden yapıldığını doğrulayın.

---

### AD.3 Güvenli İstek ve Bağlam Yönetimi

AI modelleri için istemler veya bağlamlar oluşturulurken gizli bilgiler, özel kodlar ve kişisel verilerin sızmasını önleyin.

 #AD.3.1    Seviye: 1    Rol: D/V
 Yazılı rehberliğin, gizli bilgilerin, kimlik doğrulama verilerinin veya sınıflandırılmış verilerin istemlerde gönderilmesini yasakladığını doğrulayın.
 #AD.3.2    Seviye: 2    Rol: D
 Teknik kontrollerin (istemci tarafı redaksiyon, onaylanmış bağlam filtreleri) hassas öğeleri otomatik olarak kaldırdığını doğrulayın.
 #AD.3.3    Seviye: 3    Rol: D/V
 İsteklerin ve yanıtların tokenlaştırıldığını, iletim sırasında ve depolanırken şifrelendiğini doğrulayın ve saklama sürelerinin veri sınıflandırma politikasına uygun olduğunu kontrol edin.

---

### AD.4 Yapay Zeka ile Üretilen Kodun Doğrulanması

AI çıktısı tarafından tanıtılan güvenlik açıklarını tespit edin ve kod birleştirilmeden veya dağıtılmadan önce giderin.

 #AD.4.1    Seviye: 1    Rol: D/V
 AI tarafından oluşturulan kodun her zaman insan kod incelemesine tabi tutulduğunu doğrulayın.
 #AD.4.2    Seviye: 2    Rol: D
 Otomatik tarayıcıların (SAST/IAST/DAST) AI tarafından üretilen kod içeren her çekme talebinde çalıştığını doğrulayın ve kritik bulgular üzerine birleştirmeleri engelleyin.
 #AD.4.3    Seviye: 3    Rol: D/V
 Farklılaştırılmış fuzz testi veya özellik tabanlı testlerin, güvenlik kritik davranışları (örneğin, girdi doğrulama, yetkilendirme mantığı) kanıtladığını doğrulayın.

---

### AD.5 Kod Önerilerinin Açıklanabilirliği ve İzlenebilirliği

Denetçilere ve geliştiricilere, bir önerinin neden yapıldığı ve nasıl geliştiği hakkında bilgi verin.

 #AD.5.1    Seviye: 1    Rol: D/V
 İstemi/yanıt çiftlerinin commit kimlikleri ile kaydedildiğini doğrulayın.
 #AD.5.2    Seviye: 2    Rol: D
 Geliştiricilerin bir öneriyi destekleyen model atıflarını (eğitim parçacıkları, dokümantasyon) gösterebildiklerini doğrulayın.
 #AD.5.3    Seviye: 3    Rol: D/V
 Açıklanabilirlik raporlarının tasarım öğeleriyle birlikte saklandığını ve güvenlik incelemelerinde referans verildiğini doğrulayarak, ISO/IEC 42001 izlenebilirlik prensiplerinin karşılandığından emin olun.

---

### AD.6 Sürekli Geri Bildirim ve Model İnce Ayarı

Model güvenlik performansını zaman içinde iyileştirirken negatif kaymanın önlenmesini sağlar.

 #AD.6.1    Seviye: 1    Rol: D/V
 Geliştiricilerin güvensiz veya uyumsuz önerileri işaretleyebildiğini ve bu işaretlerin takip edildiğini doğrulayın.
 #AD.6.2    Seviye: 2    Rol: D
 Toplanan geri bildirimin, doğrulanmış güvenli kodlama kütüphaneleriyle (örneğin, OWASP Cheat Sheets) periyodik olarak ince ayar yapılmasını veya doğrulanmış güvenli kodlama kütüphaneleriyle desteklenen sorgu artırımlı üretim sürecini bilgilendirdiğini doğrulayın.
 #AD.6.3    Seviye: 3    Rol: D/V
 Kapalı döngü değerlendirme aracıyla her ince ayardan sonra regresyon testlerinin yapıldığını doğrulayın; güvenlik metrikleri, dağıtımdan önce önceki temel değerleri karşılamalı veya aşmalıdır.

---

#### Referanslar

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Ek E: Örnek Araçlar ve Çerçeveler

### Amaç

Bu bölüm, belirli bir AISVS gereksiniminin uygulanmasını veya yerine getirilmesini destekleyebilecek araçlar ve çerçeveler için örnekler sağlar. Bunlar, AISVS ekibi veya OWASP GenAI Güvenlik Projesi tarafından tavsiye veya onay olarak görülmemelidir.

---

### AE.1 Eğitim Verisi Yönetişimi ve Önyargı Yönetimi

Veri analitiği, yönetişim ve önyargı yönetimi için kullanılan araçlar.

 #AE.1.1    Bölüm: 1.1
 Veri Envanteri Araçları: Veri envanteri yönetimi araçları gibi...
 #AE.1.2    Bölüm: 1.2
 Aktarım Sırasında Şifreleme HTTPS tabanlı uygulamalar için openSSL ve python gibi araçlarla TLS kullanın`ssl`kütüphane.

---

### AE.2 Kullanıcı Girişi Doğrulaması

Kullanıcı girdilerini işlemek ve doğrulamak için araçlar.

 #AE.2.1    Bölüm: 2.1
 Komut Enjeksiyonu Savunma Araçları: NVIDIA'nın NeMo veya Guardrails AI gibi koruyucu araçları kullanın.

---

