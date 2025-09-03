## Etusivun kuvitus

### Standardin tiedot

tekoälyn turvallisuuden varmistusstandardi (AISVS) on yhteisövetoinen turvallisuusvaatimusten luettelo, jota data-tieteilijät, MLOps-insinöörit, ohjelmistoarkkitehdit, kehittäjät, testaajat, turvallisuusammattilaiset, työkalutoimittajat, sääntelyviranomaiset ja kuluttajat voivat käyttää suunnitellakseen, rakentaakseen, testatakseen ja varmistakseen luotettavat tekoälyä hyödyntävät järjestelmät ja sovellukset.

### Tekijänoikeus ja lisenssi

Versio 0.1 (Ensimmäinen julkinen luonnos - Työn alla), 2025  

![license](images/license.png)
Tekijänoikeus © 2025 The AISVS Project.  

Julkaistu lisenssin alaisuudessa  Creative Commons Attribution‑ShareAlike 4.0 International License.
Mikä tahansa uudelleenkäyttö tai jakelu edellyttää, että tämän työn lisenssiehdot ilmoitetaan selvästi muille.

### Projektipäälliköt

Jim Manico
Aras “Russ” Memisyazici

### Tekijät ja arvioijat

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS on brand‑new standardi, joka on luotu erityisesti tekoälyjärjestelmien ainutlaatuisten turvallisuushaasteiden ratkaisemiseksi. Vaikka se ammentaa inspiraationsa laajempien turvallisuusalan parhaiden käytäntöjen pohjalta, jokainen AISVS:n vaatimus on kehitetty alusta alkaen vastaamaan tekoälyuhkien uhkakenttää ja auttamaan organisaatioita rakentamaan turvallisempia ja kestävämpiä tekoälyratkaisuja.

## Esipuhe

Tervetuloa tekoälyn turvallisuuden varmistusstandardiin (AISVS) versio 1.0!

### Johdanto

Perustettu vuonna 2025 yhteisön yhteistyön tuloksena, AISVS määrittelee turvallisuusvaatimukset, jotka on otettava huomioon nykyaikaisten tekoälymallien, putkistojen ja AI‑pohjaisten palveluiden suunnittelussa, kehittämisessä, käyttöönotossa ja käyttämisessä.

AISVS v1.0 edustaa projektijohtajien, työryhmän ja laajemman yhteisön yhteistä panosta tuottaakseen käytännönläheisen, testattavissa olevan perusmallin tekoälyjärjestelmien turvaamiseksi.

Tavoitteenamme tässä julkaisussa on tehdä AISVS:n käyttöönotosta suoraviivaista samalla kun keskitymme tiukasti määriteltyyn laajuuteen ja huomioimme tekoälyyn liittyvän nopeasti kehittyvän riskikentän.

### AISVS-version 1.0:n keskeiset tavoitteet

Versio 1.0 luodaan useilla ohjaavilla periaatteilla.

#### Hyvin määritelty laajuus

Jokaisen vaatimuksen on oltava AISVS:n nimen ja tehtävän kanssa yhdenmukainen:

Tekoäly – Ohjaus toimii AI/ML-tasolla (data, malli, putkisto tai inferenssi) ja on AI-asiantuntijoiden vastuulla.
Turvallisuus – Vaatimukset suoraan lieventävät tunnistetut turvallisuus-, tietosuojariskit tai turvallisuusriskit.
Varmistus – Kieltä on kirjoitettu siten, että noudattaminen voidaan objektiivisesti todentaa.
Standard – Osiot noudattavat johdonmukaista rakennetta ja terminologiaa muodostaen johdonmukaisen viitteen.
​
---

Noudattamalla AISVS:ää organisaatiot voivat järjestelmällisesti arvioida ja vahvistaa tekoälyratkaisujensa turvallisuustilaa, edistäen turvallisen tekoälyn suunnittelun ja kehittämisen kulttuuria.

## AISVS:n käyttö

Tekoälyn turvallisuuden varmistusstandardi (AISVS) määrittelee nykyaikaisten tekoälysovellusten ja -palvelujen turvallisuusvaatimukset, keskittyen niihin näkökohtiin, jotka ovat sovelluskehittäjien hallinnassa.

AISVS on tarkoitettu kaikille, jotka kehittävät tai arvioivat tekoälysovellusten turvallisuutta, mukaan lukien kehittäjät, arkkitehdit, turvallisuusinsinöörit ja auditoijat. Tämä luku esittelee AISVS:n rakenteen ja käytön, mukaan lukien sen varmistustasot ja suunnitellut käyttötapaukset.

### Tekoälyn turvallisuusvarmistustasot

AISVS määrittelee kolme nousevaa turvatarkastustasoa. Jokainen taso lisää syvyyttä ja monimutkaisuutta, jolloin organisaatiot voivat säätää turvallisuusasentoaan AI-järjestelmien riskitasojen mukaan.

Organisaatiot voivat aloittaa tasolta 1 ja omaksua vähitellen korkeampia tasoja, kun turvallisuuskypsyys ja uhkien altistuminen kasvavat.

#### Tasojen määritelmä

Jokaiselle AISVS v1.0:n vaatimukselle on määritetty jokin seuraavista tasoista:

 Tason 1 vaatimukset

Level 1 sisältää kriittisimmät ja perustavanlaatuimmat turvallisuusvaatimukset. Ne keskittyvät estämään yleisiä hyökkäyksiä, jotka eivät perustu muihin edellytyksiin tai haavoittuvuuksiin. Suurin osa Level 1 toimenpiteistä on joko suoraviivaisia toteuttaa tai tarpeeksi olennaisia oikeuttaakseen tämän panostuksen.

 2. tason vaatimukset

Taso 2 käsittelee edistyneempiä tai harvinaisempia hyökkäyksiä sekä kerrostettuja puolustusjärjestelmiä laajalle leviäviä uhkia vastaan. Nämä vaatimukset saattavat edellyttää monimutkaisempaa logiikkaa tai kohdistua erityisiin hyökkäyksen edellytyksiin.

 Tason 3 vaatimukset

Taso 3 sisältää hallintakeinoja, joita on tyypillisesti vaikeampi toteuttaa tai joiden soveltuvuus on tilannekohtaista. Nämä edustavat usein monitasoisen puolustuksen mekanismeja tai lieventäviä toimenpiteitä erikoistuneita, kohdennettuja tai erittäin monimutkaisia hyökkäyksiä vastaan.

#### Rooli (D/V)

Jokainen AISVS-vaatimus on merkitty ensisijaisen yleisön mukaan:

D – Kehittäjä-keskeiset vaatimukset
V – vahvistajaan/auditoijaan keskittyneet vaatimukset
D/V – Sekä kehittäjille että tarkistajille relevantti

## C1 Koulutusdatan hallinta ja vinoumien hallinta

### Kontrollitavoite

Koulutusdata on hankittava, käsiteltävä ja ylläpidettävä tavalla, joka säilyttää sen jäljitettävyyden, turvallisuuden, laadun ja oikeudenmukaisuuden. Näin toimimalla se täyttää oikeudelliset velvoitteet ja vähentää koulutuksen aikana ilmenneiden vinoumien, myrkytysyritysten tai yksityisyyden loukkauksien riskejä, jotka voisivat vaikuttaa koko tekoälyn elinkaareen.

---

### C1.1 Koulutusdatan alkuperä

Pidä yllä todistettavissa olevaa luetteloa kaikista tietojoukoista, hyväksy vain luotettavat lähteet, ja kirjaa jokainen muutos auditointia varten.

 #1.1.1    Taso: 1    Rooli: D/V
 Varmista, että jokaisen koulutusdatan lähteen ajantasainen luettelo pidetään yllä (alkuperä, vastuuhenkilö/omistaja, lisenssi, keräysmenetelmä, käyttötarkoitukseen liittyvät rajoitukset sekä käsittelyhistoria).
 #1.1.2    Taso: 1    Rooli: D/V
 Varmista, että koulutusdatan käsittelyprosesseissa jätetään pois turhat ominaisuudet, attribuutit tai kentät (esim. käyttämättömät metatiedot, arkaluonteiset PII-tiedot, vuotaneet testitiedot).
 #1.1.3    Taso: 2    Rooli: D/V
 Varmista, että kaikki tietojoukon muutokset kuuluvat kirjattuun hyväksyntätyönkulkuun.
 #1.1.4    Taso: 3    Rooli: D/V
 Varmista, että datasetit tai niiden osajoukot ovat vesileimattuja tai sormenjäljitettyjä, jos mahdollista.

---

### C1.2 Koulutusdatan turvallisuus ja eheys

Rajoita pääsy koulutusdataan, salaa se levossa ja siirron aikana, ja varmista sen eheys, jotta estetään manipulointi, varkaus tai datan saastuttaminen.

 #1.2.1    Taso: 1    Rooli: D/V
 Varmista, että käyttöoikeuksien hallinta suojaa koulutusdatan tallennusta ja putkistoja.
 #1.2.2    Taso: 2    Rooli: D/V
 Varmista, että kaikki pääsy koulutusdatoihin on kirjattu, mukaan lukien käyttäjä, aika ja toimenpide.
 #1.2.3    Taso: 2    Rooli: D/V
 Varmista, että koulutusdatasetit ovat salattuja sekä siirron aikana että levossa, käyttämällä alan standardien kryptografisia algoritmeja ja avainhallintakäytäntöjä.
 #1.2.4    Taso: 2    Rooli: D/V
 Varmista, että kryptografiset hajautukset tai digitaaliset allekirjoitukset käytetään varmistamaan koulutusdatan eheys tallennuksen ja siirron aikana.
 #1.2.5    Taso: 2    Rooli: D/V
 Varmista, että automaattiset havaitsemistekniikat ovat otettu käyttöön estämään koulutusdatan luvattomat muutokset tai sen korruptoituminen.
 #1.2.6    Taso: 2    Rooli: D/V
 Varmista, että vanhentunut koulutusdata on turvallisesti Poistettu tai anonymisoitu.
 #1.2.7    Taso: 3    Rooli: D/V
 Varmista, että kaikki koulutusdatan versiot ovat ainutlaatuisesti tunnistettuja, tallennettu muuttumattomasti ja auditoitavissa, jotta palautus ja forensiikka-analyysit ovat mahdollisia.

---

### C1.3 Koulutusdatan merkinnän laatu, eheys ja turvallisuus

Suojaa tunnisteet ja vaadi tekninen tarkastus kriittisille tiedoille.

 #1.3.1    Taso: 2    Rooli: D/V
 Varmista, että kryptografiset hajautukset tai digitaaliset allekirjoitukset on liitetty label-artifakteihin niiden eheyden ja aitouden varmistamiseksi.
 #1.3.2    Taso: 2    Rooli: D/V
 Varmista, että merkintärajapinnat ja -alustat noudattavat vahvoja pääsynhallintakäytäntöjä, pitävät koskemattomat audit-lokit kaikista merkintätoiminnoista ja suojaavat luvattomilta muokkauksilta.
 #1.3.3    Taso: 3    Rooli: D/V
 Varmista, että tunnisteisiin sisältyvä herkkä tieto on piilotettu, anonymisoitu tai salattu tietokenttätasolla sekä levossa että siirrossa.

---

### C1.4 Koulutusdatan laatu ja turvallisuusvarmistus

Yhdistä automaattinen validointi, manuaaliset satunnaistarkastukset ja kirjatut korjaustoimenpiteet tietojoukon luotettavuuden varmistamiseksi.

 #1.4.1    Taso: 1    Rooli: D
 Varmista, että automatisoidut testit havaitsevat formaatti-virheet ja null-arvot jokaisessa tuonnissa tai merkittävässä tietomuunnoksessa.
 #1.4.2    Taso: 2    Rooli: D/V
 Varmista, että LLM:n koulutus- ja hienosäätöputket toteuttavat myrkytyksen havaitsemisen ja tiedon eheyden validoinnin (esim. tilastolliset menetelmät, poikkeavien havaintojen havaitseminen, upotusanalyysi) tunnistaakseen sekä mahdolliset myrkytys­hyökkäykset (esim. tunnisteen vaihtaminen, takaportin laukaisimen lisääminen, roolinvaihdon käskyt, vaikuttavia havaintoja hyödyntävät hyökkäykset) että koulutusdatan tahatonta korruptiota.
 #1.4.3    Taso: 3    Rooli: D/V
 Varmista, että asianmukaiset puolustuskeinot, kuten adversaarinen koulutus (käyttäen generoituja adversaarisia esimerkkejä), data-augmentointi perturboitujen syötteiden avulla tai robustit optimointitekniikat, ovat toteutettu ja viritetty riskinarvioinnin perusteella asianmukaisille malleille.
 #1.4.4    Taso: 2    Rooli: D/V
 Varmista, että automaattisesti genereoidut merkinnät (esim. LLM:ien kautta tai heikolla valvonnalla) noudattavat varmuuskynnyksiä ja johdonmukaisuustarkistuksia, jotta voidaan havaita hallusinaatioita, harhaanjohtavia tai alhaisen varmuuden merkintöjä.
 #1.4.5    Taso: 3    Rooli: D
 Varmista, että automatisoidut testit havaitsevat labelien vinoumat jokaisessa tuonnissa tai merkittävässä datamuunnoksessa.

---

### C1.5 Datan jäljitettävyys ja seurattavuus

Seuraa jokaisen datapisteen koko matkaa lähteestä mallin syötteeseen auditointikelpoisuuden ja häiriövasteen varmistamiseksi.

 #1.5.1    Taso: 2    Rooli: D/V
 Varmista, että kunkin datapisteen jäljitettävyys, mukaan lukien kaikki muunnokset, augmentoinnit ja yhdistämiset, on tallennettu ja että sitä voidaan rekonstruoida.
 #1.5.2    Taso: 2    Rooli: D/V
 Varmista, että lineage-rekisterit ovat muuttumattomia, turvallisesti tallennettuja ja auditointeja varten käytettävissä.
 #1.5.3    Taso: 2    Rooli: D/V
 Varmista, että datan jäljitettävyyden seuranta kattaa synteettisen datan, joka on luotu yksityisyyden suojaamiseen tähtäävillä tai generatiivisilla tekniikoilla, ja että koko putkiston aikana kaikki synteettinen data on selvästi merkitty ja erottuu selkeästi todellisesta datasta.

---

### Lähteet

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

## C2 Käyttäjän syötteen validointi

### Kontrollitavoite

Käyttäjän syötteen vankka validointi on AI-järjestelmiin kohdistuvien tuhoisimpien hyökkäysten ensisijainen puolustus. Kehoite-injektiohyökkäykset voivat ohittaa järjestelmän ohjeet, paljastaa arkaluonteista dataa, tai ohjata mallin käyttäytymistä kohti sallimattomia toimintoja. Jos käytössä ei ole erillisiä suodattimia ja ohjehierarkioita, tutkimukset osoittavat, että 'multi-shot' jailbreak-hyökkäykset, jotka hyödyntävät erittäin pitkiä kontekstikehyksiä, ovat tehokkaita. Myös hienovaraiset vastahyökkäys-perturbaatiohyökkäykset--kuten homoglyph-vaihdot tai leetspeak—-voivat hiljaisesti muuttaa mallin päätöksiä.

---

### C2.1 Kehotteen injektio torjunta

Kehotusinjektio on yksi tekoälyjärjestelmien suurimmista riskeistä. Tämän taktiikan vastatoimet hyödyntävät yhdistelmää staattisia kuviofilttereita, dynaamisia luokittelijoita sekä ohjeiden hierarkian täytäntöönpanoa.

 #2.1.1    Taso: 1    Rooli: D/V
 Varmista, että käyttäjän syötteet seulotaan jatkuvasti päivitetyn tunnettujen kehotteen-injektiomallien kirjaston perusteella (jailbreak-avainsanat, "ohita edellinen", roolipeliketjut, epäsuorat HTML-/URL-hyökkäykset).
 #2.1.2    Taso: 1    Rooli: D/V
 Varmista, että järjestelmä noudattaa ohjeiden hierarkiaa, jossa järjestelmän tai kehittäjän viestit ohittavat käyttäjän ohjeet, jopa kontekstin ikkunan laajentamisen jälkeen.
 #2.1.3    Taso: 2    Rooli: D/V
 Varmista, että adversaariset arviointitestit (esim. Punaisen tiimin "many-shot" -kehotteet) ajetaan ennen jokaista mallin tai prompt-pohjan julkaisua, ja että niissä käytetään menestysprosentin kynnysarvoja sekä regressioiden estoon tarkoitetuja automaattisia estoja.
 #2.1.4    Taso: 2    Rooli: D
 Varmista, että kolmannen osapuolen sisällöstä peräisin olevat kehotteet (verkkosivut, PDF-tiedostot, sähköpostit) puhdistetaan eristetyn jäsentelykontekstin sisällä ennen kuin ne liitetään pääkehotteeseen.
 #2.1.5    Taso: 3    Rooli: D/V
 Varmista, että kaikki prompt-suodatussääntöpäivitykset, luokittelumallien versiot ja blokkilistan muutokset ovat versionhallinnassa ja auditoitavissa.

---

### C2.2 Hyökkäys-esimerkkeihin kohdistuva vastustuskyky

NLP-mallit ovat yhä alttiita hienovaraisiin merkkitasoisiin tai sanatasoisiin perturbatioihin, joita ihmiset usein eivät huomaa, mutta mallit luokittelevat ne virheellisesti.

 #2.2.1    Taso: 1    Rooli: D
 Varmista, että perus syötteen normalisoinnin vaiheet (Unicode NFC, homoglyph-kartoitus, välilyöntien trimmaus) suoritetaan ennen tokenisointia.
 #2.2.2    Taso: 2    Rooli: D/V
 Varmista, että tilastollinen poikkeavuuksien havaitseminen merkitsee syötteet, joilla on poikkeuksellisen suuri Levenshtein-etäisyys kielen normeihin verrattuna, liiallinen toistuvien tokenien määrä tai poikkeavat upotusten etäisyydet.
 #2.2.3    Taso: 2    Rooli: D
 Varmista, että inferenssiputkisto tukee valinnaisia adversarial-training–hardened mallivariantteja tai suojauskerroksia (esim. satunnaistaminen, puolustusdistillointi) korkean riskin päätepisteille.
 #2.2.4    Taso: 2    Rooli: V
 Varmista, että epäillyt adversarial-syötteet ovat karanteenissa, ja niistä on kirjattu täydet payloadit (henkilötietojen poistamisen jälkeen).
 #2.2.5    Taso: 3    Rooli: D/V
 Varmista, että robustisuusmittarit (tunnettujen hyökkäyskokonaisuuksien menestysprosentti) seurataan ajan mittaan ja regressiot laukaisevat julkaisun eston.

---

### C2.3 Skeema, Tyyppi- ja Pituuden Validointi

AI-hyökkäykset, joissa on virheellisiä tai ylisuureita syötteitä, voivat aiheuttaa jäsentelyvirheitä, promptin leviämistä kenttien välillä ja resurssien loppumista. Tiukka skeeman noudattaminen on myös edellytys determinististen työkalukutsujen suorittamisessa.

 #2.3.1    Taso: 1    Rooli: D
 Varmista, että jokainen API- tai funktiokutsupäätepiste määrittelee selkeän syötteen skeeman (JSON Schema, Protobuf tai multimodaalinen vastine) ja että syötteet validoidaan ennen kehotteen muodostamista.
 #2.3.2    Taso: 1    Rooli: D/V
 Varmista, että enimmäistoken- tai tavurajoja ylittävät syötteet hylätään turvallisella virheilmoituksella eikä niitä koskaan katkaista hiljaisesti.
 #2.3.3    Taso: 2    Rooli: D/V
 Varmista, että tyyppitarkistukset (esim. numeeriset vaihteluvälit, enum-arvot, MIME-tyypit kuville ja äänitteille) ovat voimassa palvelinpuolella, eivät ainoastaan asiakaspuolen koodissa.
 #2.3.4    Taso: 2    Rooli: D
 Varmista, että semanttiset validointityökalut (esim. JSON Schema) toimivat vakioaikaisesti estääkseen algoritmisen DoS-hyökkäyksen.
 #2.3.5    Taso: 3    Rooli: V
 Varmista, että validointivirheet kirjataan sensuroiduilla payload-pätkillä ja yksiselitteisilla virhekodeilla, jotka auttavat turvallisuustriagea.

---

### C2.4 Sisällön ja käytäntöjen seulonta

Kehittäjien tulisi pystyä havaitsemaan syntaktisesti kelvolliset kehotteet, jotka pyytävät kiellettyä sisältöä (kuten laittomia ohjeita, vihapuhetta ja tekijänoikeudella suojattua tekstiä), ja estämään niiden leviämisen.

 #2.4.1    Taso: 1    Rooli: D
 Varmista, että sisällön luokitin (zero-shot tai hienosäädetty) pisteyttää jokaisen syötteen väkivallan, itsemurhan, vihaan liittyvän sisällön, seksuaalisen sisällön ja laittomien pyyntöjen osalta, konfiguroitavien kynnysten mukaisesti.
 #2.4.2    Taso: 1    Rooli: D/V
 Varmista, että sääntöjä rikkovat syötteet saavat standardoidut kieltäytymiset tai turvalliset täydennykset, jotta ne eivät päädy myöhempiin LLM-kutsuihin.
 #2.4.3    Taso: 2    Rooli: D
 Varmista, että suodatusmalli tai sääntöjoukko koulutetaan uudelleen tai päivitetään vähintään neljännesvuosittain ottaen mukaan äskettäin havaitut jailbreak- tai politiikan kiertämismallit.
 #2.4.4    Taso: 2    Rooli: D
 Varmista, että seulonta noudattaa käyttäjäkohtaisia politiikkoja (ikä, alueelliset lailliset rajoitukset) attribuuttiperusteisten sääntöjen kautta, jotka ratkaistaan pyynnön hetkellä.
 #2.4.5    Taso: 3    Rooli: V
 Varmista, että suodatuslokit sisältävät luokittelijan luottamusarvot ja politiikan kategorian tunnisteet SOC-korrelaatiota ja tulevaa punaisen tiimin toistoa varten.

---

### C2.5 Syötteen nopeusrajoitus ja väärinkäytön ehkäisy

Ohjelmistokehittäjien tulisi estää väärinkäyttöä, resurssien uupumista ja automatisoituja hyökkäyksiä tekoälyjärjestelmiä vastaan rajoittamalla syötteen nopeuksia ja havaitsemalla poikkeavia käyttömalleja.

 #2.5.1    Taso: 1    Rooli: D/V
 Varmista, että käyttäjäkohtaiset, IP-osoitekohtaiset ja API-avaimen mukaan asetetut nopeusrajoitukset ovat voimassa kaikilla syötteen päätepisteillä.
 #2.5.2    Taso: 2    Rooli: D/V
 Varmista, että burst-rajat ja jatkuvat nopeusrajoitukset on säädetty estämään DoS- ja brute force -hyökkäykset.
 #2.5.3    Taso: 2    Rooli: D/V
 Varmista, että poikkeavat käyttömallit (esim. nopeasti toistuvia pyyntöjä, syötteen tulva) laukaisevat automaattiset estot tai eskaloinnit.
 #2.5.4    Taso: 3    Rooli: V
 Varmista, että väärinkäytön ehkäisylokit säilytetään ja niitä tarkastellaan uusien hyökkäyskuvioiden havaitsemiseksi.

---

### C2.6 Monimodaalisen syötteen validointi

Tekoälyjärjestelmien tulisi sisällyttää vankka validointi ei-tekstuaalisille syötteille (kuvat, äänet, tiedostot) estääkseen injektiot, kiertämisen tai resurssien väärinkäytön.

 #2.6.1    Taso: 1    Rooli: D
 Varmista, että kaikki ei-tekstuaaliset syötteet (kuvat, äänitiedostot ja muut tiedostot) validoidaan tyypin, koon ja formaatin mukaan ennen käsittelyä.
 #2.6.2    Taso: 2    Rooli: D/V
 Varmista, että tiedostot skannataan haittaohjelmien ja steganografisten hyötykuormien varalta ennen tuontia.
 #2.6.3    Taso: 2    Rooli: D/V
 Tarkista, että kuva- ja äänisyötteet tarkastetaan adversarial-perturbaatioiden tai tunnettujen hyökkäysmallien varalta.
 #2.6.4    Taso: 3    Rooli: V
 Varmista, että multimodaalisen syötteen validointivirheet kirjataan ja ne laukaisevat hälytykset tutkimusta varten.

---

### C2.7 Syötteen alkuperä ja attribuutio

AI-järjestelmien tulisi tukea auditointia, väärinkäytösten seuraamista ja vaatimustenmukaisuutta valvomalla ja merkitsemällä kaikkien käyttäjien syötteiden alkuperän.

 #2.7.1    Taso: 1    Rooli: D/V
 Varmista, että kaikilla käyttäjäsyötteillä on tuonnin yhteydessä merkitty metatiedot (käyttäjän tunnus, istunto, lähde, aikaleima, IP-osoite).
 #2.7.2    Taso: 2    Rooli: D/V
 Varmista, että provenance-metatiedot säilyvät ja ovat auditoitavissa kaikille käsitellyille syötteille.
 #2.7.3    Taso: 2    Rooli: D/V
 Varmista, että poikkeukselliset tai epäluotettavat syötteiden lähteet merkitään ja niihin sovelletaan tiukempaa tarkastelua tai estoa.

---

### C2.8 Reaaliaikainen mukautuva uhkien havaitseminen

Kehittäjien tulisi käyttää kehittyneitä uhkatunnistusjärjestelmiä tekoälyä varten, jotka sopeutuvat uusiin hyökkäysmalleihin ja tarjoavat reaaliaikaisen suojan käännetyllä kuvioetsinnällä.

 #2.8.1    Taso: 1    Rooli: D/V
 Varmista, että uhkien havaitsemisen mallit käännetään optimoituihin regex-moottoreihin, jotta reaaliaikaisessa suodatuksessa saavutetaan korkea suorituskyky ja mahdollisimman pieni viive.
 #2.8.2    Taso: 1    Rooli: D/V
 Varmista, että uhkien havaitsemisjärjestelmät pitävät erilliset mallikirjastot eri uhkakategorioille (kehotteen injektio, haitallinen sisältö, herkät tiedot, järjestelmäkomennot).
 #2.8.3    Taso: 2    Rooli: D/V
 Varmista, että adaptiivinen uhkien havaitseminen sisältää koneoppimismallit, jotka päivittävät uhkien herkkyystasoa hyökkäysten taajuuden ja menestysasteiden perusteella.
 #2.8.4    Taso: 2    Rooli: D/V
 Varmista, että reaaliaikaiset uhkatiedustelusyötteet päivittävät automaattisesti mallikirjastot uusilla hyökkäystunnisteilla ja IOCs (kompromissin indikaattorit).
 #2.8.5    Taso: 3    Rooli: D/V
 Varmista, että uhkien havaitsemisen vääriä positiivisia osuuksia seurataan jatkuvasti ja mallien spesifisyyttä säädetään automaattisesti, jotta laillisten käyttötapausten häiriöt minimoidaan.
 #2.8.6    Taso: 3    Rooli: D/V
 Varmista, että kontekstuaalinen uhkianalyysi ottaa huomioon syötteen lähteen, käyttäjän käyttäytymismallit ja istunnon historian, jotta tunnistustarkkuutta voidaan parantaa.
 #2.8.7    Taso: 3    Rooli: D/V
 Varmista, että uhkien havaitsemisen suorituskykymittarit (havaitsemisnopeus, käsittelylatenssi, resurssien käyttö) seurataan ja optimoidaan reaaliajassa.

---

### C2.9 Multimodaalinen turvallisuusvalidointiputkisto

Ohjelmistokehittäjien tulisi tarjota turvallisuustarkastus tekoälysyötteille, kuten tekstille, kuville ja äänelle sekä muille vastaaville modaliteeteille, ja käyttää erityyppistä uhkien havaitsemista sekä resurssien eristämistä.

 #2.9.1    Taso: 1    Rooli: D/V
 Varmista, että jokaisella syötteen modaalisuudella on omat turvallisuusvalidaattorinsa, joilla on dokumentoidut uhkamallit (teksti: prompt injection, kuvat: steganografia, ääni: spektrogrammihyökkäykset) ja havaitsemiskynnykset.
 #2.9.2    Taso: 2    Rooli: D/V
 Varmista, että monimodaaliset syötteet käsitellään eristetyissä hiekkalaatikoissa määritellyillä resurssirajoituksilla (muisti, CPU, käsittelyaika), jotka ovat kullekin modaalisuustyypille ominaisia ja jotka on dokumentoitu turvallisuuspolitiikoissa.
 #2.9.3    Taso: 2    Rooli: D/V
 Varmista, että ristiinmodaalinen hyökkäysten havaitseminen tunnistaa koordinoituja hyökkäyksiä, jotka ulottuvat useisiin syötteen tyyppeihin (esim. steganografiset payloadit kuvissa sekä tekstissä tehty prompt-injektointi) korrelaatiosääntöjen ja hälytyksen generoinnin avulla.
 #2.9.4    Taso: 3    Rooli: D/V
 Varmista, että monimodaalisen validoinnin epäonnistumiset laukaisevat yksityiskohtaisen lokituksen, mukaan lukien kaikki syöttömodaliteetit, validointitulokset, uhkaspisteet ja korrelaatioanalyysi strukturoitujen lokimuotojen avulla SIEM-integraatiota varten.
 #2.9.5    Taso: 3    Rooli: D/V
 Varmista, että modaalisuuspohjaiset sisältöluokittelijat päivitetään dokumentoitujen aikataulujen mukaan (vähintään neljännesvuosittain) uusien uhkamallien ja vastustuskelpoisten esimerkkien sekä suorituskykymittareiden osalta siten, että suorituskyky pysyy baseline-kynnysten yläpuolella.

---

### Lähteet

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

## C3 Mallin elinkaaren hallinta ja muutoksenhallinta

### Kontrollitavoite

Tekoälyjärjestelmien on toteutettava muutoksenhallintaprosesseja, jotka estävät luvattomat tai turvallisuusriskeihin johtavat mallimuutokset pääsemästä tuotantoon. Tämä hallintakeino varmistaa mallin eheyden koko elinkaaren ajan--kehityksestä käyttöönottoon ja poistamiseen käytöstä--joka mahdollistaa nopean reagoinnin häiriötilanteisiin ja vastuullisuuden ylläpidon kaikista muutoksista.

Pääasiallinen turvallisuustavoite: Ainoastaan valtuutetut, validoidut mallit otetaan tuotantoon käyttämällä hallittuja prosesseja, jotka ylläpitävät eheyden, jäljitettävyyden ja palautettavuuden.

---

### C3.1 Mallin valtuutus ja eheys

Ainoastaan valtuutetut mallit, joilla on varmennettu eheys, pääsevät tuotantoympäristöihin.

 #3.1.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki mallin artefaktit (painot, konfiguraatiot, tokenisoijat) ovat kryptografisesti allekirjoitetut valtuutettujen tahojen toimesta ennen käyttöönottoa.
 #3.1.2    Taso: 1    Rooli: D/V
 Varmista, että mallin eheys tarkistetaan käyttöönoton aikana, ja allekirjoituksen vahvistuksen epäonnistuminen estää mallin lataamisen.
 #3.1.3    Taso: 2    Rooli: D/V
 Varmista, että mallin alkuperäistiedot sisältävät valtuuttavan tahon identiteetin, koulutusdatan tarkistussummat, validointitestien tulokset, joissa on läpäisty/epäonnistunut tila, sekä luontiaikaleima.
 #3.1.4    Taso: 2    Rooli: D/V
 Varmista, että kaikki malli-artefaktit noudattavat semanttista versionointia (MAJOR.MINOR.PATCH) dokumentoitujen kriteerien mukaan, jotka määrittävät, milloin kunkin version komponentti kasvaa.
 #3.1.5    Taso: 2    Rooli: V
 Varmista, että riippuvuuksien seuranta ylläpitää reaaliaikaista varastoa, joka mahdollistaa kaikkien kuluttavien järjestelmien nopean tunnistamisen.

---

### C3.2 Mallin validointi ja testaus

Mallien on läpäistävä määritellyt turvallisuus- ja varmistusarvioinnit ennen käyttöönottoa.

 #3.2.1    Taso: 1    Rooli: D/V
 Varmista, että mallit käyvät läpi automaattisen turvallisuustestauksen, johon kuuluu syötteen validointi, tulosten sanitointi ja turvallisuusarvioinnit ennen käyttöönottoa, sekä että etukäteen sovitut organisaation läpäisy- ja hylkäyskynnykset täyttyvät.
 #3.2.2    Taso: 1    Rooli: D/V
 Varmista, että validointivirheet estävät automaattisesti mallin käyttöönoton sen jälkeen, kun on saatu nimenomainen ohituslupa ennalta määrätyiltä valtuutetuilta henkilöiltä, joilla on dokumentoidut liiketoimintaperusteet.
 #3.2.3    Taso: 2    Rooli: V
 Varmista, että testitulokset ovat kryptografisesti allekirjoitettuja ja muuttumattomasti linkitettyjä tietyn malliversion hash-arvoon, jota validoidaan.
 #3.2.4    Taso: 2    Rooli: D/V
 Varmista, että hätäkäyttöönotot edellyttävät dokumentoidun turvallisuusriskinarvioinnin sekä ennalta määrätyn turvallisuusviranomaisen hyväksynnän ennalta sovittujen aikarajojen puitteissa.

---

### C3.3 Säännelty käyttöönotto & palautus

Mallien käyttöönotot ovat hallittavia, valvottavia ja palautettavissa.

 #3.3.1    Taso: 1    Rooli: D
 Varmista, että tuotantokäyttöönotot toteuttavat asteittaisia käyttöönotto­mekanismeja (canary-käyttöönotot, blue-green-käyttöönotot) automaattisilla peruutuslaukaimilla, jotka perustuvat ennalta sovittuihin virheprosentteihin, latenssi-kynnysarvoihin tai turvallisuushälytys-kriteereihin.
 #3.3.2    Taso: 1    Rooli: D/V
 Varmista, että palautusominaisuudet palauttavat koko mallin tilan (painot, konfiguraatiot, riippuvuudet) atomisesti ennalta määriteltyjen organisaation aikavälejen puitteissa.
 #3.3.3    Taso: 2    Rooli: D/V
 Varmista, että käyttöönoton prosessit vahvistavat kryptografiset allekirjoitukset ja laskevat eheystarkisteet ennen mallin aktivointia, ja käyttöönotto epäonnistuu, jos niissä on ristiriita.
 #3.3.4    Taso: 2    Rooli: D/V
 Varmista, että hätätilan mallin sulkemistoiminnot voivat ottaa mallin päätepisteet pois käytöstä ennalta määriteltyjen vasteaikojen puitteissa automatisoitujen katkaisijoiden tai manuaalisten tappokytkinten avulla.
 #3.3.5    Taso: 2    Rooli: V
 Varmista, että palautusartefaktit (aiemmat malliversiot, konfiguraatiot, riippuvuudet) säilytetään organisaation politiikkojen mukaan muuttumattomassa tallennuksessa häiriötilanteisiin vastaamista varten.

---

### C3.4 Muutosvastuu ja auditointi

Kaikki mallin elinkaaren muutokset ovat jäljitettävissä ja auditoitavissa.

 #3.4.1    Taso: 1    Rooli: V
 Varmista, että kaikki mallimuutokset (käyttöönotto, konfiguraatio, poistaminen käytöstä) tuottavat muuttumattomia auditointitietueita, jotka sisältävät aikaleiman, todennetun toimijan identiteetin, muutostyypin sekä ennen/jälkeen tilat.
 #3.4.2    Taso: 2    Rooli: D/V
 Varmista, että auditlokin pääsy edellyttää asianmukaista valtuutusta ja kaikki pääsyyritykset kirjataan käyttäjän identiteetillä ja aikaleimalla.
 #3.4.3    Taso: 2    Rooli: D/V
 Varmista, että prompt-mallit ja järjestelmäviestit ovat git-repositorioissa versionhallinnassa, ja niihin on pakollinen koodikatselmointi ja hyväksyntä nimettyjen tarkastajien toimesta ennen käyttöönottoa.
 #3.4.4    Taso: 2    Rooli: V
 Varmista, että auditointilokit sisältävät riittävän yksityiskohtaiset tiedot (mallin hash-arvot, kokoonpanon tilannekuvat, riippuvuuksien versiot), jotta mallin tilan täydellinen rekonstruointi on mahdollista minkä tahansa aikaleiman sisällä säilytysjakson aikana.

---

### C3.5 Turvalliset kehityskäytännöt

Mallin kehitys- ja koulutusprosesseja on noudatettava turvallisten käytäntöjen mukaan, jotta kompromissilta vältytään.

 #3.5.1    Taso: 1    Rooli: D
 Varmista, että mallin kehitys-, testaus- ja tuotantoympäristöt ovat fyysisesti tai loogisesti erillisiä. Niillä ei ole jaettua infrastruktuuria, niillä on erilliset pääsynhallintajärjestelmät ja eristetyt tietovarastot.
 #3.5.2    Taso: 1    Rooli: D
 Varmista, että mallin koulutus ja hienosäätö tapahtuvat eristetyissä ympäristöissä, joihin pääsy verkkoon on rajoitettua.
 #3.5.3    Taso: 1    Rooli: D/V
 Varmista, että koulutusdatan lähteet on validoitu eheystarkistuksilla ja todennettu luotettujen lähteiden kautta dokumentoidulla hallussapitoketjulla ennen niiden käyttöä mallin kehittämisessä.
 #3.5.4    Taso: 2    Rooli: D
 Varmista, että mallikehityksen artefaktit (hyperparametrit, koulutusskriptit, konfiguraatiotiedostot) ovat tallennettu versionhallintaan ja että vertaisarvioinnin hyväksyntä vaaditaan ennen niiden käyttöä koulutuksessa.

---

### C3.6 Mallin poistaminen käytöstä

Mallien on poistuttava turvallisesti, kun niitä ei enää tarvita tai kun turvallisuusongelmat on tunnistettu.

 #3.6.1    Taso: 1    Rooli: D
 Varmista, että mallien käytöstä poistamisen prosessit skannaavat automaattisesti riippuvuuskarttoja, tunnistavat kaikki mallia käyttävät järjestelmät ja antavat ennalta sovitut varoitusajat ennen poistamista käytöstä.
 #3.6.2    Taso: 1    Rooli: D/V
 Varmista, että käytöstä poistetut malliartefaktit pyyhitetään turvallisesti kryptografisen tyhjennyksen tai moninkertaisen ylikirjoituksen avulla dokumentoitujen tietojen säilyttämiskäytäntöjen mukaan sekä vahvistetuilla hävityksen todistuksilla.
 #3.6.3    Taso: 2    Rooli: V
 Varmista, että mallin käytöstä poistamiseen liittyvät tapahtumat kirjataan aikaleimalla ja tekijäidentiteetillä, ja mallin allekirjoitukset peruutetaan estämään uudelleenkäyttöä.
 #3.6.4    Taso: 2    Rooli: D/V
 Varmista, että hätämallin poistaminen käytöstä voi estää mallin pääsyn ennalta määriteltyjen hätävasteen aikajaksojen puitteissa automaattisten tappokytkinten avulla, jos kriittisiä turvallisuushaavoittuvuuksia havaitaan.

---

### Lähteet

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

## C4 infrastruktuuri, konfiguraation ja käyttöönoton turvallisuus

### Kontrollitavoite

AI-infrastruktuurin on oltava kovennettu valtuuksien eskalointia, toimitusketjun manipulointia ja sivuttaisliikkeitä vastaan käyttämällä turvallista konfiguraatiota, ajonaikaisen eristyksen, luotettujen käyttöönotto-putkistojen sekä kattavan monitoroinnin avulla. Vain valtuutetut, vahvistetut infrastruktuurikomponentit ja konfiguraatiot pääsevät tuotantoon kontrolloitujen prosessien kautta, jotka ylläpitävät turvallisuutta, eheyttä ja auditointikykyä.

Keskeinen turvallisuustavoite: Vain kryptografisesti allekirjoitetut, haavoittuvuusskannatut infrastruktuurikomponentit saavuttavat tuotannon automaattisten validointiputkien kautta, jotka varmistavat turvallisuuspolitiikkojen noudattamisen ja ylläpitävät muuttumattomia auditointijälkiä.

---

### C4.1 Suoritusympäristön eristäminen

Estä konttien pakeneminen ja oikeuksien korotus ytimen tason eristysprimitiveillä ja pakollisilla pääsynvalvontamekanismeilla.

 #4.1.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki tekoälykontit poistavat Linuxin capabiliteetit kokonaan, lukuun ottamatta CAP_SETUID, CAP_SETGID sekä turvallisuusperusteissa dokumentoitujen nimenomaisesti vaadittujen capabiliteettien.
 #4.1.2    Taso: 1    Rooli: D/V
 Varmista, että seccomp-profiilit estävät kaikki järjestelmäkutsut lukuun ottamatta ennalta hyväksyttyjä sallintalistoja, jolloin rikkomukset lopettavat kontin ja aiheuttavat turvallisuushälytyksiä.
 #4.1.3    Taso: 2    Rooli: D/V
 Varmista, että tekoälykuormat toimivat lukukelpoisella juuritiedostojärjestelmällä, tilapäistiedot käytetään tmpfs:ää ja pysyvään dataan käytetään nimettyjä volyyumeja siten, että noexec-mount-vaihtoehdot ovat käytössä.
 #4.1.4    Taso: 2    Rooli: D/V
 Varmista, että eBPF-pohjainen ajonaikainen valvonta (Falco, Tetragon tai vastaava) havaitsee oikeuksien korotusyritykset ja tappaa automaattisesti haitalliset prosessit organisaation reagoimisaikavaatimusten puitteissa.
 #4.1.5    Taso: 3    Rooli: D/V
 Varmista, että korkean riskin tekoälykuormitukset suoritetaan laitteistisesti eristetyissä ympäristöissä (Intel TXT, AMD SVM, tai omistetut bare-metal-solmut) todentamisen varmistuksella.

---

### C4.2 Turvalliset rakennus- ja käyttöönottoputket

Varmista kryptografinen eheys ja toimitusketjun turvallisuus toistettavien rakennusprosessien ja allekirjoitettujen artefaktien avulla.

 #4.2.1    Taso: 1    Rooli: D/V
 Varmista, että infrastruktuuri-koodi skannataan työkaluilla (tfsec, Checkov tai Terrascan) jokaisessa commitissa, ja yhdistämiset estetään CRITICAL- tai HIGH-tason löydösten perusteella.
 #4.2.2    Taso: 1    Rooli: D/V
 Varmista, että konttien rakentaminen on toistettavissa identtisten SHA256-hashien kanssa eri rakennuksissa, ja luo SLSA Level 3 provenance-todistukset, jotka on allekirjoitettu Sigstorella.
 #4.2.3    Taso: 2    Rooli: D/V
 Varmista, että konttikuva sisältää CycloneDX- tai SPDX SBOM:t ja on Cosignilla allekirjoitettu ennen rekisteriin työntöä, ja että allekirjoittamattomat kuvat hylätään käyttöönoton yhteydessä.
 #4.2.4    Taso: 2    Rooli: D/V
 Varmista, että CI/CD-putket käyttävät OIDC-tunnuksia HashiCorp Vaultista, AWS IAM-rooleista tai Azure Managed Identity -tunnuksia, joiden voimassaoloajat eivät ylitä organisaation turvallisuuspolitiikan rajoja.
 #4.2.5    Taso: 2    Rooli: D/V
 Varmista, että Cosign-allekirjoitukset ja SLSA-provenanssi validoidaan käyttöönoton aikana ennen kontin suorittamista, ja että vahvistusvirheet aiheuttavat käyttöönoton epäonnistumisen.
 #4.2.6    Taso: 2    Rooli: D/V
 Varmista, että rakennusympäristöt toimivat väliaikaisissa konteissa tai virtuaalikoneissa, joilla ei ole pysyvää tallennustilaa, ja jotka ovat verkkoeristettyjä tuotannon VPC:istä.

---

### C4.3 Verkon turvallisuus ja pääsynhallinta

Toteuta nollaluottamusverkko, jolla on oletuskieltopolitiikat ja salatut yhteydet.

 #4.3.1    Taso: 1    Rooli: D/V
 Varmista, että Kubernetes NetworkPolicies tai jokin vastaava toteuttaa oletuskiellon sisään- ja ulostulolle (default-deny ingress/egress) sekä selkeästi sallituilla säännöillä vaadittaville porteille (esim. 443, 8080, jne).
 #4.3.2    Taso: 1    Rooli: D/V
 Varmista, että SSH (portti 22), RDP (portti 3389) ja pilven metadata-päätepisteet (169.254.169.254) ovat estettyjä tai ne edellyttävät sertifikaattipohjaista todentamista.
 #4.3.3    Taso: 2    Rooli: D/V
 Varmista, että ulospäin suuntautuva liikenne suodatetaan HTTP/HTTPS-proxyjen kautta (Squid, Istio tai cloud NAT-gatewayt) domain-allowlistien avulla ja estettyjen pyyntöjen lokitus on käytössä.
 #4.3.4    Taso: 2    Rooli: D/V
 Varmista, että palvelujen välinen viestintä käyttää kaksisuuntaista TLS:ää (mTLS) ja että sertifikaatit kierrätetään organisaation politiikan mukaisesti sekä sertifikaattien validointi on pakollista (ei skip-verify liput).
 #4.3.5    Taso: 2    Rooli: D/V
 Varmista, että AI-infrastruktuuri toimii omistetuissa VPC:issä/VNetsissä, joilla ei ole suoraa Internet-yhteyttä, ja että se kommunikoi ainoastaan NAT-yhdyskäytävien tai bastion-koneiden kautta.

---

### C4.4 Salaisuudet ja kryptografisten avainten hallinta

Suojaa tunnistetiedot laitteistopohjaisella tallennuksella ja automaattisella kierrätyksellä sekä nollaluottamusperiaatteen mukaisella pääsylle.

 #4.4.1    Taso: 1    Rooli: D/V
 Varmista, että salaisuudet tallennetaan HashiCorp Vaultiin, AWS Secrets Manageriin, Azure Key Vaultiin tai Google Secret Manageriin levyllä salattuna käyttämällä AES-256-salausta.
 #4.4.2    Taso: 1    Rooli: D/V
 Varmista, että kryptografiset avaimet generoidaan FIPS 140-2 Level 2 HSM:issä (AWS CloudHSM, Azure Dedicated HSM) siten, että avainten kierto noudattaa organisaation kryptografista politiikkaa.
 #4.4.3    Taso: 2    Rooli: D/V
 Varmista, että salasanakierrätys on automatisoitu katkoksittomalla käyttöönotolla ja että kierrätys käynnistyy välittömästi henkilöstömuutosten tai turvallisuustapahtumien yhteydessä.
 #4.4.4    Taso: 2    Rooli: D/V
 Varmista, että säiliökuvat skannataan työkaluilla (GitLeaks, TruffleHog tai detect-secrets) ja että API-avaimia, salasanoja tai sertifikaatteja sisältävät rakennukset estetään.
 #4.4.5    Taso: 2    Rooli: D/V
 Varmista, että tuotantoympäristön salaisen pääsyn edellytys on MFA laiteperusteisilla tunnisteilla (YubiKey, FIDO2) ja että siitä tallennetaan muuttumattomiin auditointilokeihin käyttäjäidentiteetit ja aikaleimat.
 #4.4.6    Taso: 2    Rooli: D/V
 Varmista, että salaisuudet injektoidaan Kubernetes-salaisuuksien kautta, liitettyjen volyymien kautta tai init-konttien kautta, ja että salaisuudet eivät koskaan upotu ympäristömuuttujiin tai säiliökuviin.

---

### C4.5 AI-työkuormien hiekkalaatikkokäyttöönotto ja validointi

Erista epäluotettavat tekoälymallit turvallisissa hiekkalaatikoissa kattavan käyttäytymisanalyysin avulla.

 #4.5.1    Taso: 1    Rooli: D/V
 Tarkista, että ulkoiset tekoälymallit suorittuvat gVisorissa, microVM-ympäristöissä (kuten Firecracker, CrossVM) tai Docker-konttien sisällä, lipuilla --security-opt=no-new-privileges ja --read-only.
 #4.5.2    Taso: 1    Rooli: D/V
 Varmista, että sandbox-ympäristöt eivät ole verkkoon yhteydessä (--network=none) tai että niihin on pääsy vain localhostiin, ja kaikki ulkoiset pyynnöt on estetty iptables-säännöillä.
 #4.5.3    Taso: 2    Rooli: D/V
 Varmista, että tekoälymallin validointi sisältää automaattisen red-team-testaamisen organisaation määrittelemällä testikattavuudella ja käyttäytymisanalyysillä takaportin havaitsemiseksi.
 #4.5.4    Taso: 2    Rooli: D/V
 Varmista, että ennen AI-mallin tuotantoon siirtämistä sen hiekkalaatikkotulokset ovat kryptografisesti allekirjoitetut valtuutettujen turvallisuushenkilöstön toimesta ja tallennetut muuttumattomiin audit-lokeihin.
 #4.5.5    Taso: 2    Rooli: D/V
 Varmista, että hiekkalaatikkoympäristöt tuhoutuvat ja luodaan uudelleen referenssikuvista arviointien välillä täydellisen tiedostojärjestelmän ja muistin puhdistuksella.

---

### C4.6 Infrastruktuurin turvallisuusvalvonta

Jatkuva skannaus ja infrastruktuurin valvonta automatisoidulla korjaustoiminnalla ja reaaliaikaisilla hälytyksillä.

 #4.6.1    Taso: 1    Rooli: D/V
 Varmista, että säiliökuvat skannataan organisaation aikataulujen mukaan, ja että kriittiset haavoittuvuudet estävät käyttöönoton organisaation riskikynnysten perusteella.
 #4.6.2    Taso: 1    Rooli: D/V
 Varmista, että infrastruktuuri täyttää CIS Benchmarksit tai NIST 800-53 -ohjaimet organisaation määrittelemillä noudattamisen kynnystasoilla sekä epäonnistuneiden tarkastusten automatisoidulla korjaustoiminnalla.
 #4.6.3    Taso: 2    Rooli: D/V
 Varmista, että korkean vakavuuden haavoittuvuudet on korjattu organisaation riskienhallinnan aikataulujen mukaan hätätoimenpiteiden kanssa aktiivisesti hyväksikäytettyjen CVE-tunnusten varalta.
 #4.6.4    Taso: 2    Rooli: V
 Varmista, että turvallisuushälytykset integroituvat SIEM-alustoihin (Splunk, Elastic tai Sentinel) käyttämällä CEF tai STIX/TAXII-muotoja automaattisella rikastuksella.
 #4.6.5    Taso: 3    Rooli: V
 Varmista, että infrastruktuurin mittarit viedään valvontajärjestelmiin (Prometheus, DataDog) SLA-koontinäytöineen ja johtajille suunnatun raportoinnin kera.
 #4.6.6    Taso: 2    Rooli: D/V
 Varmista, että konfiguraatioero havaitaan käyttämällä työkaluja (Chef InSpec, AWS Config) organisaation monitorointivaatimusten mukaan ja että luvattomien muutosten varalta toteutetaan automaattinen palautus.

---

### C4.7 tekoälyinfrastruktuurin resurssien hallinta

Estä resurssien loppumisen hyökkäykset ja varmista oikeudenmukainen resurssien jakaminen kiintiöiden ja seurannan avulla.

 #4.7.1    Taso: 1    Rooli: D/V
 Varmista, että GPU/TPU-käyttöä seurataan ja hälytykset laukaistaan organisaation määrittelemien kynnysten mukaan sekä automaattinen skaalautuminen tai kuormituksen tasapainotus otetaan käyttöön kapasiteetin hallintapolitiikkojen perusteella.
 #4.7.2    Taso: 1    Rooli: D/V
 Varmista, että tekoälyn työkuorman mittarit (inferenssin viive, läpäisynopeus, virheprosentit) kerätään organisaation valvontavaatimusten mukaan ja korreloidaan infrastruktuurin käyttöasteen kanssa.
 #4.7.3    Taso: 2    Rooli: D/V
 Varmista, että Kubernetesin ResourceQuotas tai vastaavat rajoittavat yksittäisiä työkuormia organisaation resurssien allokointikäytäntöjen mukaisesti ja että kovia rajoja noudatetaan.
 #4.7.4    Taso: 2    Rooli: V
 Varmista, että kustannusten seuranta seuraa menoja jokaiselle työkuormalle/vuokraajalle siten, että hälytykset perustuvat organisaation budjettikynnyksiin ja että budjetin ylityksiä vastaan on automaattiset kontrollit.
 #4.7.5    Taso: 3    Rooli: V
 Varmista, että kapasiteetin suunnittelu käyttää historiallisia tietoja organisaation määrittelemillä ennustejaksoilla ja että automaattinen resurssien provisiointi perustuu kysyntäkuvioihin.
 #4.7.6    Taso: 2    Rooli: D/V
 Varmista, että resurssien loppuminen laukaisee sulakekatkaisijat organisaation vastausvaatimusten mukaan, mukaan lukien kapasiteettopolitiikkojen perusteella tapahtuva nopeusrajoitus ja työkuorman eristäminen.

---

### C4.8 Ympäristöjen erottaminen ja julkaisujen hallinta

Varmista tiukat ympäristörajat automatisoiduilla siirtoporteilla ja turvallisuusvalidaatiolla.

 #4.8.1    Taso: 1    Rooli: D/V
 Varmista, että kehitys-, testi- ja tuotantoympäristöt toimivat erillisissä VPC- ja VNets-verkoissa siten, ettei niillä ole jaettuja IAM-rooleja, turvallisuusryhmiä tai verkkoyhteyksiä.
 #4.8.2    Taso: 1    Rooli: D/V
 Varmista, että ympäristön käyttöönoton hyväksyntä edellyttää organisaation määrittelemien valtuutettujen henkilöiden kryptografisia allekirjoituksia ja muuttumattomia auditointijälkiä.
 #4.8.3    Taso: 2    Rooli: D/V
 Varmista, että tuotantoympäristöt estävät SSH-pääsyn, poistavat debug-päätepisteet käytöstä ja edellyttävät muutospyynnöt organisaation etukäteen ilmoitusvaatimusten mukaisesti, lukuun ottamatta hätätilanteita.
 #4.8.4    Taso: 2    Rooli: D/V
 Varmista, että infrastruktuuri-koodimuutokset vaativat vertaisarvioinnin, automaattisen testauksen ja turvallisuusskannauksen ennen yhdistämistä päähaaraan.
 #4.8.5    Taso: 2    Rooli: D/V
 Varmista, että ei-tuotantodataa on anonymisoitu organisaation tietosuojavaatimusten mukaisesti, synteettisen datan generoinnin avulla tai täydellisen datan maskauksen yhteydessä, jossa PII-poisto on varmistettu.
 #4.8.6    Taso: 2    Rooli: D/V
 Varmista, että edistyskynnysten portit sisältävät automatisoidut turvallisuustestit (SAST, DAST, konttiskannaus) ja että hyväksyntään vaaditaan nolla CRITICAL-löydöksiä.

---

### C4.9 Infrastruktuurin varmuuskopiointi ja palautus

Varmista infrastruktuurin resilienssi automatisoiduilla varmuuskopioilla, testatuilla palautusmenetelmillä ja katastrofapalautumiskyvyillä.

 #4.9.1    Taso: 1    Rooli: D/V
 Varmista, että infrastruktuurikokoonpanot varmuuskopioidaan organisaation varmuuskopiointiaikataulujen mukaan maantieteellisesti erillisiin alueisiin 3-2-1-varmuuskopiointistrategian toteuttamisen yhteydessä.
 #4.9.2    Taso: 2    Rooli: D/V
 Varmista, että varmuuskopiojärjestelmät toimivat eristetyissä verkoissa, niillä on omat erilliset tunnukset ja ilman verkkoyhteyttä oleva tallennus ransomware-suojaksi.
 #4.9.3    Taso: 2    Rooli: V
 Varmista, että palautusmenettelyt testataan ja validoidaan automaattisella testauksella organisaation aikataulujen mukaisesti ja RTO- ja RPO-tavoitteet täyttävät organisaation vaatimukset.
 #4.9.4    Taso: 3    Rooli: V
 Varmista, että katastrofipalautuminen sisältää AI-spesifiset runbookit, jotka kattavat mallin painojen palautuksen, GPU-klusterin uudelleenrakentamisen ja palveluiden riippuvuuskartoituksen.

---

### C4.10 Infrastruktuurin vaatimustenmukaisuus ja hallinto

Säilytä säädösten noudattaminen jatkuvan arvioinnin, dokumentoinnin ja automatisoitujen kontrollien avulla.

 #4.10.1    Taso: 2    Rooli: D/V
 Varmista, että infrastruktuurin vaatimustenmukaisuutta arvioidaan organisaation aikataulujen mukaan SOC 2, ISO 27001 tai FedRAMP-ohjausten perusteella automaattisen todistusaineiston keräämisen avulla.
 #4.10.2    Taso: 2    Rooli: V
 Varmista, että infrastrukturiudokumentaatio sisältää verkkokaaviot, tiedonvirtakartat ja uhkamallit, jotka on päivitetty organisaation muutosjohtamisen vaatimusten mukaan.
 #4.10.3    Taso: 3    Rooli: D/V
 Varmista, että infrastruktuurimuutokset käyvät läpi automaattisen vaatimustenmukaisuuden vaikutusarvioinnin sekä niihin liittyvät sääntelyhyväksyntätyönkulut korkean riskin muutoksille.

---

### C4.11 Tekoälylaitteistojen turvallisuus

Turvalliset tekoälyyn liittyvät laitteistokomponentit, mukaan lukien GPU:t, TPU:t ja erikoistuneet tekoälykiihdyttimet.

 #4.11.1    Taso: 2    Rooli: D/V
 Varmista, että tekoälykiihdyttimen laiteohjelmisto (GPU BIOS, TPU-laiteohjelmisto) on kryptografisilla allekirjoituksilla varmennettu ja päivitetty organisaation päivityshallinnan aikataulujen mukaisesti.
 #4.11.2    Taso: 2    Rooli: D/V
 Varmista, että ennen työkuorman suoritusta tekoälykiihdyttimen eheys varmistetaan laitteistotodennuksella käyttämällä TPM 2.0, Intel TXT tai AMD SVM.
 #4.11.3    Taso: 2    Rooli: D/V
 Varmista, että GPU:n muisti on eristetty työkuormien välillä käyttämällä SR-IOV:ia, MIG:ia (Multi-Instance GPU) tai vastaavaa laitteistollista ositusmenetelmää muistin sanitoinnin avulla työn välillä.
 #4.11.4    Taso: 3    Rooli: V
 Varmista, että tekoälylaitteistojen toimitusketju sisältää alkuperäisyyden todentamisen valmistajan sertifikaattien avulla sekä väärennösten estävän pakkausvalidaation.
 #4.11.5    Taso: 3    Rooli: D/V
 Varmista, että laitteistoturvamoduulit (HSM:t) suojaavat tekoälymallien painot ja kryptografiset avaimet FIPS 140-2 tason 3 tai Common Criteria EAL4+-sertifioinnin kanssa.

---

### C4.12 Reuna- ja hajautettu tekoälyinfrastruktuuri

Turvalliset hajautetut tekoälyjärjestelmät, mukaan lukien reunalaskenta, federaatio-oppiminen ja monipaikkaiset arkkitehtuurit.

 #4.12.1    Taso: 2    Rooli: D/V
 Varmista, että reuna-AI-laitteet todentavat itsensä keskitettyyn infrastruktuuriin käyttämällä kaksisuuntaista TLS:ää, ja että laitteiden varmenteet kierrätetään organisaation varmenteidenhallintapolitiikan mukaisesti.
 #4.12.2    Taso: 2    Rooli: D/V
 Varmista, että reunalaitteet toteuttavat turvallisen käynnistyksen todennetuilla allekirjoituksilla ja rollback-suojan, joka estää firmware-päivitysten downgrade-hyökkäykset.
 #4.12.3    Taso: 3    Rooli: D/V
 Varmista, että hajautettu tekoälyn koordinointi käyttää Byzantiinivirheenkestäviä konsensusalgoritmeja, joissa on osallistujien validointi ja haitallisten solmujen havaitseminen.
 #4.12.4    Taso: 3    Rooli: D/V
 Varmista, että reuna-pilvi-yhteys sisältää kaistanleveyden rajoittamisen, tiedonpakkaamisen ja offline-toimintakyvyn sekä turvallisen paikallisen tallennuksen.

---

### C4.13 Monipilvi- ja hybridi-infrastruktuurin tietoturva

Turvaa tekoälykuormit useissa pilvipalveluntarjoajissa sekä hybridi-pilvi- ja paikan päällä toteutetuissa käyttöönotuksissa.

 #4.13.1    Taso: 2    Rooli: D/V
 Varmista, että monipilvi-tekoälykäyttöönotot käyttävät pilviympäristöriippumatonta identiteettifederointia (OIDC, SAML) ja keskitettyä politiikan hallintaa toimittajien välillä.
 #4.13.2    Taso: 2    Rooli: D/V
 Varmista, että pilvien välisessä tiedonsiirrossa käytetään loppuun asti salattua tiedonsiirtoa asiakkaan hallinnoimilla avaimilla ja että tietojen residenssivalvontaa sovelletaan kunkin lainkäyttöalueen mukaan.
 #4.13.3    Taso: 2    Rooli: D/V
 Varmista, että hybridi-pilvi tekoälykuormat toteuttavat yhdenmukaiset turvapolitiikat paikallisten ympäristöjen ja pilviympäristöjen välillä, sekä niissä on yhtenäinen monitorointi ja hälytys.
 #4.13.4    Taso: 3    Rooli: V
 Varmista, että pilvitoimittajariippuvuuden estäminen sisältää siirrettävän infrastruktuuri-koodin, standardoidut API:t ja tietojen vientiominaisuudet formaattimuunnostyökaluineen.
 #4.13.5    Taso: 3    Rooli: V
 Varmista, että multicloud-kustannusten optimointi sisältää turvallisuusvalvontatoimenpiteet, jotka estävät sekä resurssien leviäminen että luvattomien pilvien välisten datansiirtomaksujen syntymisen.

---

### C4.14 Infrastruktuurin automatisointi ja GitOps-turvallisuus

Varmista infrastruktuurin automatisointiputkien ja GitOps-työnkulkujen turvallisuus tekoälyinfrastruktuurin hallintaa varten.

 #4.14.1    Taso: 2    Rooli: D/V
 Varmista, että GitOps-repositoriot vaativat allekirjoitetut commitit GPG-avaimilla ja haaran suojaussäännöt estävät suorat pushit päähaaroihin.
 #4.14.2    Taso: 2    Rooli: D/V
 Varmista, että infrastruktuurin automaatiossa on poikkeamien havaitseminen, automaattiset korjaustoimenpiteet ja palautusominaisuudet, jotka laukaistaan organisaation reaktiovaatimusten mukaisesti luvattomien muutosten varalta.
 #4.14.3    Taso: 2    Rooli: D/V
 Varmista, että automatisoitu infrastruktuurin provisionointi sisältää turvallisuuspolitiikan validoinnin, joka estää käyttöönoton epäyhteensopiville konfiguraatioille.
 #4.14.4    Taso: 2    Rooli: D/V
 Varmista, että infrastruktuurin automatisoinnin salaisuudet hallitaan ulkoisten salaisuustoimittajien kautta (External Secrets Operator, Bank-Vaults) automaattisella kierrätyksellä.
 #4.14.5    Taso: 3    Rooli: V
 Varmista, että itsekorjaava infrastruktuuri sisältää turvallisuustapahtumien korrelaation automaattisten incidenttivastausten sekä sidosryhille suunnattujen ilmoitus- ja työnkulkujen kanssa.

---

### C4.15 Kvanttivarmennettu infrastruktuuriturvallisuus

Valmistele tekoälyinfrastruktuuri kvanttitietokoneiden uhkia varten käyttämällä postkvanttikryptografiaa ja kvanttiturvallisia protokollia.

 #4.15.1    Taso: 3    Rooli: D/V
 Varmista, että tekoälyinfrastruktuuri toteuttaa NIST:n hyväksymiä postkvanttisia kryptografisia algoritmeja (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) avainvaihdolle ja digitaalisiin allekirjoituksiin.
 #4.15.2    Taso: 3    Rooli: D/V
 Varmista, että kvanttiavaintenjakelujärjestelmät on otettu käyttöön korkean turvallisuuden AI-viestintää varten kvanttisuojaavien avainhallintaprotokollien kanssa.
 #4.15.3    Taso: 3    Rooli: D/V
 Varmista, että kryptografisen ketteryyden kehykset mahdollistavat nopean siirtymisen uusiin post-kvanttialgoritmeihin automaattisella sertifikaattien ja avainten kierrätyksellä.
 #4.15.4    Taso: 3    Rooli: V
 Varmista, että kvanttuhkamallinnus arvioi tekoälyinfrastruktuurin haavoittuvuuden kvanttihyökkäyksiä vastaan dokumentoitujen siirtymäaikojen ja riskinarvioiden kanssa.
 #4.15.5    Taso: 3    Rooli: D/V
 Varmista, että hybridit klassisen ja kvanttikryptografian järjestelmät tarjoavat monitasoisen suojauksen kvanttisiirtymäkauden aikana sekä suorituskykyseurannan.

---

### C4.16 Luottamuksellinen laskenta & turvalliset enklavit

Suojataan tekoälyn työkuormia ja mallien painoja käyttämällä laitteistopohjaisia luotettavia suoritusympäristöjä ja luottamuksellisia laskentatekniikoita.

 #4.16.1    Taso: 3    Rooli: D/V
 Varmista, että arkaluonteiset AI-mallit suorittuvat Intel SGX-enklaaveissa, AMD SEV-SNP-turvasäiliöissä tai ARM TrustZone-turva-alueella salatun muistin ja todentamisen varmistuksen avulla.
 #4.16.2    Taso: 3    Rooli: D/V
 Varmista, että salassapitokontit (Kata Containers, gVisor, jolla on salassapitolaskenta) eristävät tekoälytyökuormat laitteistossa toteutetulla muistinsalauksella.
 #4.16.3    Taso: 3    Rooli: D/V
 Varmista, että etävarmennus vahvistaa enclave-eheyden ennen tekoälymallien lataamista kryptografisen todistuksen avulla, joka osoittaa suoritusympäristön aitouden.
 #4.16.4    Taso: 3    Rooli: D/V
 Tarkista, että luottamukselliset tekoälyn inferenssipalvelut estävät mallin kopioinnin salatun laskennan kautta, jossa mallipainot ovat sinetöidyt ja suoritus on suojattu.
 #4.16.5    Taso: 3    Rooli: D/V
 Varmista, että luotetun suoritusympäristön orkestrointi hallinnoi turvallisen suljetun ympäristön elinkaarta etävarmennuksen ja salattujen viestintäkanavien avulla.
 #4.16.6    Taso: 3    Rooli: D/V
 Varmista, että turvallinen monen osapuolen laskenta (SMPC) mahdollistaa yhteistoiminnallisen tekoälykoulutuksen paljastamatta yksittäisiä tietojoukkoja tai malliparametreja.

---

### C4.17 Nollatietoinfrastruktuuri

Toteuta nollatietotodistejärjestelmiä yksityisyyttä suojaavan tekoälyn vahvistamiseen ja todennukseen paljastamatta arkaluonteista tietoa.

 #4.17.1    Taso: 3    Rooli: D/V
 Varmista, että nollatietotodistukset (ZK-SNARKs, ZK-STARKs) vahvistavat AI-mallin eheyden ja koulutuksen alkuperän paljastamatta mallin painoja tai koulutusdataa.
 #4.17.2    Taso: 3    Rooli: D/V
 Varmista, että ZK-pohjaiset todennusjärjestelmät mahdollistavat yksityisyyden suojaa säilyttävän käyttäjän vahvistamisen tekoälypalveluissa paljastamatta henkilöllisyyteen liittyviä tietoja.
 #4.17.3    Taso: 3    Rooli: D/V
 Varmista, että yksityisen joukon leikkaus (PSI) protokollat mahdollistavat turvallisen tietojen vastaavuuden federatiivisessa tekoälyssä ilman, että yksittäisiä tietojoukkoja paljastetaan.
 #4.17.4    Taso: 3    Rooli: D/V
 Tarkista, että nollatietoon perustuvat koneoppimisen (ZKML) järjestelmät mahdollistavat verifioitavat tekoälyn inferenssit kryptografisen oikeellisuustodistuksen avulla.
 #4.17.5    Taso: 3    Rooli: D/V
 Varmista, että ZK-rollupit tarjoavat skaalautuvaa, yksityisyyttä suojaavaa tekoälytransaktioiden käsittelyä erävahvistuksen avulla ja pienemmän laskennallisen kuormituksen kautta.

---

### C4.18 Sivukanava-hyökkäysten ehkäisy

Suojaa tekoälyinfrastruktuuria aikahyökkäyksiltä, virtahyökkäyksiltä, elektromagneettisilta sivukanavahyökkäyksiltä ja välimuistiin perustuvilta sivukanavahyökkäyksiltä, jotka voisivat vuotaa arkaluontoista tietoa.

 #4.18.1    Taso: 3    Rooli: D/V
 Varmista, että tekoälyn inferenssiaika on aikavakioitu käyttämällä aikavakioalgoritmeja ja täytettä estämään aikaperusteleisia mallinpoimintahyökkäyksiä.
 #4.18.2    Taso: 3    Rooli: D/V
 Varmista, että tehoanalyysinsuojaus sisältää kohinan injektoinnin, syöttölinjan suodatuksen ja satunnaistetut suoritusmallit AI-laitteistolle.
 #4.18.3    Taso: 3    Rooli: D/V
 Varmista, että välimuistiin perustuva sivuväyläkanavien torjunta käyttää välimuistin osituksen, satunnaistamisen ja tyhjennyskäskyjen yhdistelmää tiedon vuotamisen estämiseksi.
 #4.18.4    Taso: 3    Rooli: D/V
 Varmista, että elektromagneettisten päästöjen suojaus sisältää suojauksen, signaalisuodatuksen ja satunnaistetun käsittelyn TEMPEST-tyylisten hyökkäysten estämiseksi.
 #4.18.5    Taso: 3    Rooli: D/V
 Varmista, että mikroarkkitehtuuriin perustuvat sivukanavien puolustukset sisältävät spekulatiivisen suorituksen hallinnan sekä muistin pääsyn kuvioiden hämärtämisen.

---

### C4.19 Neuromorfinen ja erikoistunut tekoälyn laitteistoturva

Varmista kehittyvien tekoälylaitteistojen arkkitehtuurien turvallisuus, mukaan lukien neuromorfiset sirut, FPGA:t, räätälöidyt ASIC:t ja optisen laskennan järjestelmät.

 #4.19.1    Taso: 3    Rooli: D/V
 Varmista, että neuromorfisen sirun turvallisuus sisältää piikkikuvioiden salauksen, synapsien painojen suojauksen sekä laitteistopohjaista oppimissääntöjen validointia.
 #4.19.2    Taso: 3    Rooli: D/V
 Varmista, että FPGA-pohjaiset tekoälykiihdyttimet toteuttavat bitstream-salauksen, manipuloinnin estävät mekanismit ja turvallisen konfiguraation lataamisen autentikoiduilla päivityksillä.
 #4.19.3    Taso: 3    Rooli: D/V
 Varmista, että räätälöidyn ASIC-turvallisuuden piiriin kuuluvat sirun sisäiset turvaprosessorit, laitteistopohjainen luottamusjuuri sekä manipulointihavaitsemisjärjestelmällä varustettu turvallinen avainvarasto.
 #4.19.4    Taso: 3    Rooli: D/V
 Varmista, että optisen laskennan järjestelmät toteuttavat kvanttivarmennetun optisen salauksen, turvallisen fotoniikkakytkennän ja suojatun optisen signaaliprosessoinnin.
 #4.19.5    Taso: 3    Rooli: D/V
 Varmista, että hybridi-analog-digitaaliset tekoälysirut sisältävät turvallisen analogisen laskennan, suojatun painojen tallennuksen ja todentuneen analogidigitaalimuunnoksen.

---

### C4.20 Tietosuojaan-perustuva laskenta-infrastruktuuri

Ota käyttöön infrastruktuurin hallintakeinot, joilla varmistetaan yksityisyyttä suojaavan laskennan turvallisuus ja arkaluontoisten tietojen suojaus AI:n käsittelyn ja analyysin aikana.

 #4.20.1    Taso: 3    Rooli: D/V
 Varmista, että homomorfinen salausinfrastruktuuri mahdollistaa salatun laskennan arkaluonteisilla tekoälykuormilla kryptografisen eheyden varmistuksen ja suorituskyvyn seurannan kanssa.
 #4.20.2    Taso: 3    Rooli: D/V
 Varmista, että yksityisen tiedonhaun järjestelmät mahdollistavat tietokantakyselyt paljastamatta kyselymalleja kryptografisen pääsynmallien suojauksen avulla.
 #4.20.3    Taso: 3    Rooli: D/V
 Varmista, että turvalliset usean osapuolen laskentaprotokollat mahdollistavat yksityisyyden suojaavan tekoälyn inferenssin ilman, että yksittäisiä syötteitä tai välituloksia paljastetaan.
 #4.20.4    Taso: 3    Rooli: D/V
 Varmista, että yksityisyyden suojaava avainhallinta sisältää jaetun avainten generoinnin, kynnyskriptografian sekä laitteistopohjaisen suojauksen kanssa tapahtuvan turvallisen avainten kierrätyksen.
 #4.20.5    Taso: 3    Rooli: D/V
 Varmista, että yksityisyyden suojaan perustuvan laskennan suorituskyky on optimoitu ryhmittelyn, välimuistin ja laitteistokiihdytyksen kautta samalla kun kryptografiset turvatakuut säilyvät.

---

### C4.15 Agenttikehys pilvi-integraatio turvallisuus & hybridi käyttöönotto

Pilvi-integroitujen agenttikehikkojen turvallisuustoimenpiteet hybridiympäristöihin, joissa on sekä on-premises- että pilviarkkitehtuureja.

 #4.15.1    Taso: 1    Rooli: D/V
 Varmista, että pilvitallennuksen integraatio käyttää end-to-end-salausta, jonka avainhallinta on agentin hallinnassa.
 #4.15.2    Taso: 2    Rooli: D/V
 Varmista, että hybridi-käyttöönoton turvallisuusrajat on määritelty selkeästi salatuilla viestintäkanavilla.
 #4.15.3    Taso: 2    Rooli: D/V
 Varmista, että pilviresurssien pääsy sisältää nolla-trustin todentamisen jatkuvalla todennuksella.
 #4.15.4    Taso: 3    Rooli: D/V
 Varmista, että datan sijaintivaatimukset noudatetaan kryptografisen todentamisen avulla tallennuspaikoista.
 #4.15.5    Taso: 3    Rooli: D/V
 Varmista, että pilvipalveluntarjoajan turvallisuusarvioinnit sisältävät agenttikohtaisen uhkamallinnan ja riskinarvioinnin.

---

### Lähteet

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

## C5 Pääsynhallinta ja identiteetti tekoälykomponentteja ja käyttäjiä varten

### Kontrollitavoite

Tehokas pääsynhallinta tekoälyjärjestelmissä edellyttää vankkaa identiteetin hallintaa, kontekstisidonnaista valtuutusta ja ajonaikaista täytäntöönpanoa noudattaen zero-trust-periaatteita. Nämä kontrollit varmistavat, että ihmiset, palvelut ja autonomiset agentit ovat vuorovaikutuksessa mallien, datan ja laskennallisten resurssien kanssa ainoastaan selkeästi myönnettyjen oikeusalueiden puitteissa, jatkuvalla varmistuksella ja auditointimahdollisuuksilla.

---

### C5.1 Identiteetin hallinta ja todentaminen

Perusta kryptografisesti varmennetut identiteetit kaikille entiteeteille, ja ota käyttöön monivaiheinen todennus valtuutettujen toimintojen turvaamiseksi.

 #5.1.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki inhimilliset käyttäjät ja palvelutilit todentuvat keskitetyn yrityksen identiteetin tarjoajan (IdP) kautta käyttämällä OIDC/SAML-protokollia, joissa on yksilölliset identiteetin ja tokenin vastaavuudet (ei jaettuja tilejä tai tunnuksia).
 #5.1.2    Taso: 1    Rooli: D/V
 Varmista, että korkean riskin toiminnot (mallin käyttöönotto, painojen vienti, koulutusdatan pääsy, tuotantokonfiguraation muutokset) edellyttävät monivaiheista todennusta tai vaiheistetun todennuksen, jossa istunto uudelleentodennetaan.
 #5.1.3    Taso: 2    Rooli: D
 Varmista, että uudet identiteetit käyvät läpi identiteetin todentamisen, joka on NIST 800-63-3 IAL-2:n tai vastaavien standardien mukainen, ennen tuotantojärjestelmän käyttöoikeuksien myöntämistä.
 #5.1.4    Taso: 2    Rooli: V
 Varmista, että käyttöoikeustarkastukset suoritetaan neljännesvuosittain automaattisen inaktiivisten tilien havaitsemisen sekä tunnusten kierrätyksen pakottamisen ja poistamisen työnkulkujen avulla.
 #5.1.5    Taso: 3    Rooli: D/V
 Varmista, että federatiiviset tekoäly-agentit todentavat itsensä käyttämällä allekirjoitettuja JWT-väitteitä, joilla on enintään 24 tunnin voimassaoloaika ja jotka sisältävät kryptografisen alkuperätodisteen.

---

### C5.2 Resurssien valtuutus ja minimioikeuksien periaate

Ota käyttöön hienojakoiset pääsynhallintajärjestelmät kaikille tekoälyresursseille, joissa on selkeät lupamallit ja auditointilokit.

 #5.2.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen AI-resurssi (tietojoukot, mallit, rajapinnat, vektorikokoelmat, upotusten indeksit, laskenta-instanssit) noudattaa roolipohjaista pääsynhallintaa sekä selkeitä sallimislistoja että oletuskieltopolitiikat.
 #5.2.2    Taso: 1    Rooli: D/V
 Varmista, että pienimmän oikeuden periaate on oletusarvoisesti voimassa siten, että palvelutilit aloittavat pelkät lukuoikeudet ja kirjoitusoikeuksille vaaditaan dokumentoitu liiketoiminnallinen peruste.
 #5.2.3    Taso: 1    Rooli: V
 Varmista, että kaikki pääsynhallinnan muutokset on linkitetty hyväksyttyihin muutospyyntöihin ja kirjattu muuttumattomasti aikaleimoineen, toimijoiden identiteetteineen, resurssitunnisteineen sekä käyttöoikeusmuutosten arvoineen.
 #5.2.4    Taso: 2    Rooli: D
 Varmista, että tietoluokitusmerkinnät (PII, PHI, export-controlled, proprietary) leviävät automaattisesti johdettuihin resursseihin (embeddings, prompt caches, model outputs) yhdenmukaisen käytäntöjen noudattamisen kanssa.
 #5.2.5    Taso: 2    Rooli: D/V
 Varmista, että luvattomat pääsyritykset ja käyttöoikeuksien korottumistapahtumat laukaisevat reaaliaikaiset hälytykset kontekstuaalisen metatiedon kanssa SIEM-järjestelmiin enintään 5 minuutin kuluessa.

---

### C5.3 Dynaaminen politiikan arviointi

Ota käyttöön attribuuttipohjaiset pääsynvalvontamoottorit kontekstinmukaisia valtuutuspäätöksiä varten, auditointiominaisuuksilla varustettuina.

 #5.3.1    Taso: 1    Rooli: D/V
 Varmista, että valtuutuspäätökset ulkoistetaan omistetulle politiikkamoottorille (OPA, Cedar tai vastaava), joka on saavutettavissa autentikoitujen API-rajapintojen kautta ja jonka eheys on kryptografisesti suojattu.
 #5.3.2    Taso: 1    Rooli: D/V
 Varmista, että politiikat arvioivat dynaamisia attribuutteja ajonaikaisesti, mukaan lukien käyttäjän luokitustaso, resurssin herkkyysluokitus, pyynnön konteksti, vuokralaisen eristys ja aikarajoitteet.
 #5.3.3    Taso: 2    Rooli: D
 Varmista, että politiikkamääritelmät ovat versionhallinnassa, vertaisarvioidut ja validoidut automaattisen testauksen avulla CI/CD-putkistoissa ennen tuotantoon käyttöönottoa.
 #5.3.4    Taso: 2    Rooli: V
 Varmista, että politiikan arviointitulokset sisältävät rakenteelliset päätösten perusteet ja että ne siirretään SIEM-järjestelmiin korrelaatioanalyysiä ja vaatimustenmukaisuusraportointia varten.
 #5.3.5    Taso: 3    Rooli: D/V
 Varmista, että politiikkavälimuistin TTL-arvot eivät ylitä 5 minuuttia korkean herkkyyden resursseille ja 1 tunti standardiresursseille, joilla on välimuistin invalidointikyky.

---

### C5.4 Kyselyaikainen tietoturvan toimeenpano

Ota käyttöön tietokantakerroksen turvallisuustoimenpiteet pakollisella suodatuksella ja rivitasoisilla pääsynvalvontasäännöillä.

 #5.4.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki vektoritietokannan ja SQL-kyselyt sisältävät pakolliset turvallisuussuodattimet (vuokraajatunnus, herkkyysmerkinnät, käyttäjän laajuus), jotka on toteutettu tietokantamoottoritasolla, eikä sovelluskoodissa.
 #5.4.2    Taso: 1    Rooli: D/V
 Varmista, että rivitasoinen turvallisuus (RLS) -politiikat sekä kenttäkohtainen maskaus ovat käytössä politiikkojen periytymisen kanssa kaikissa vektoripohjaisissa tietokannoissa, hakindekseissä ja koulutusdataseteissä.
 #5.4.3    Taso: 2    Rooli: D
 Varmista, että epäonnistuneet valtuutusarvioinnit estävät 'confused deputy attacks' hyökkäykset välittömästi keskeyttämällä kyselyt ja palauttamalla selkeät valtuutusvirhekoodit sen sijaan, että palautettaisiin tyhjiä tulosjoukkoja.
 #5.4.4    Taso: 2    Rooli: V
 Varmista, että politiikan arvioinnin viive seurataan jatkuvasti automaattisten hälytysten avulla aikakatkaisutilanteiden varalta, jotka voisivat mahdollistaa valtuutuksen ohituksen.
 #5.4.5    Taso: 3    Rooli: D/V
 Varmista, että kyselyjen uudelleenkäynnistysmekanismit arvioivat uudelleen autorisointipolitiikkoja ottaen huomioon aktiivisten käyttäjäsessioiden aikana tapahtuvat dynaamiset käyttöoikeuksien muutokset.

---

### C5.5 Ulostulon suodatus & Tietojen menetyksen esto

Ota käyttöön jälkikäsittelyn hallintatoimenpiteet luvattoman datan paljastumisen estämiseksi tekoälyn tuottamassa sisällössä.

 #5.5.1    Taso: 1    Rooli: D/V
 Varmista, että ennusteen jälkeiset suodatusmekanismit skannaavat ja piilottavat luvattomat PII-tiedot, luokitellut tiedot sekä omistusoikeudellisesti suojatun datan ennen sisällön toimittamista pyytäjille.
 #5.5.2    Taso: 1    Rooli: D/V
 Varmista, että mallien tuotoksissa olevat viitteet, lähdeviitteet ja lähdeilmoitukset on validoitu kutsujan oikeuksien mukaan, ja ne poistetaan, jos havaitaan luvaton pääsy.
 #5.5.3    Taso: 2    Rooli: D
 Varmista, että ulostulomuotojen rajoitukset (siivotut PDF-tiedostot, kuvat, joista metatiedot on poistettu, hyväksytyt tiedostotyypit) ovat voimassa käyttäjäoikeustasojen ja dataluokitusten perusteella.
 #5.5.4    Taso: 2    Rooli: V
 Varmista, että redaktiointialgoritmit ovat deterministisiä, versionhallintaan liittyviä ja pitävät yllä audit-lokeja tukeakseen vaatimustenmukaisuustutkimuksia ja forensiikka-analyysiä.
 #5.5.5    Taso: 3    Rooli: V
 Varmista, että korkean riskin redaktiotapahtumat tuottavat adaptiiviset lokit, jotka sisältävät alkuperäisen sisällön kryptografiset hajautusarvot forensiikkaa varten ilman tietojen paljastumista.

---

### C5.6 Monivuokraus eristys

Varmista kryptografinen ja looginen eristys vuokraajien välillä jaetussa tekoälyinfrastruktuurissa.

 #5.6.1    Taso: 1    Rooli: D/V
 Varmista, että muistialueet, upotustallennustilat, välimuistitietueet ja väliaikaiset tiedostot ovat nimialueittain eriytettyjä jokaiselle vuokraajalle, ja että turvallinen pyyhkiminen tapahtuu vuokraajan poistamisen tai istunnon päättymisen yhteydessä.
 #5.6.2    Taso: 1    Rooli: D/V
 Varmista, että jokainen API-pyyntö sisältää autentikoidun vuokraajan tunnisteen, joka on kryptografisesti validoitu suhteessa istuntokontekstiin ja käyttäjäoikeuksiin.
 #5.6.3    Taso: 2    Rooli: D
 Varmista, että verkkopolitiikat toteuttavat oletuskieltosäännöt tenanttienväliseen kommunikaatioon palvelumeshien ja konttien orkestrointialustojen sisällä.
 #5.6.4    Taso: 3    Rooli: D
 Varmista, että salausavaimet ovat jokaiselle vuokraajalle ainutlaatuisia CMK-tuen avulla ja että vuokraajien tietovarastojen välillä on kryptografinen eristys.

---

### C5.7 Autonomisen agentin valtuutus

Hallinnoi tekoälyagenttien ja autonomisten järjestelmien käyttöoikeuksia rajattujen kyvykkyystokenien sekä jatkuvan valtuutuksen avulla.

 #5.7.1    Taso: 1    Rooli: D/V
 Varmista, että autonomiset agentit saavat laajuudeltaan rajatut kyvykkyystokenit, jotka nimenomaisesti luettelevat sallitut toiminnot, käytettävissä olevat resurssit, aikarajat ja toimintarajoitteet.
 #5.7.2    Taso: 1    Rooli: D/V
 Varmista, että korkeaan riskin kyvykkyydet (tiedostojärjestelmän pääsy, koodin suorittaminen, ulkoiset API-kutsut, taloudelliset tapahtumat) ovat oletusarvoisesti pois käytöstä ja vaativat aktivointiin nimenomaiset hyväksynnät liiketoiminnallisten perustelujen kera.
 #5.7.3    Taso: 2    Rooli: D
 Varmista, että kyvykkyystokenit sidotaan käyttäjäistuntoihin, sisällytä kryptografinen eheyden suojaus, ja varmista, että niitä ei voi tallentaa pysyvästi tai käyttää uudelleen offline-tilanteissa.
 #5.7.4    Taso: 2    Rooli: V
 Varmista, että agentin käynnistämät toiminnot käyvät läpi ABAC-politiikkamoottorin kautta toissijaisessa valtuutuksessa, jossa suoritetaan koko kontekstin arviointi ja auditointilokit tallennetaan.
 #5.7.5    Taso: 3    Rooli: V
 Varmista, että agentin virhetilanteet ja poikkeusten käsittely sisältävät kyvykkyyden laajuutta koskevat tiedot tukemaan tapahtuma-analyysiä ja forensista tutkimusta.

---

### Lähteet

#### Standardit ja viitekehykset

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Toteutusohjeet

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### Tekoälyyn liittyvä turvallisuus

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Mallien, kehysten ja datan toimitusketjun turvallisuus

### Kontrollitavoite

tekoäly‑toimitusketjuhyökkäykset hyödyntävät kolmannen osapuolen malleja, kehyksiä tai aineistoja takaporttien, vinouksen tai haavoittuvan koodin sisäänrakentamiseen. Nämä kontrollit tarjoavat loppupään jäljitettävyyden, haavoittuvuuksien hallinnan ja seurannan koko mallin elinkaaren suojaamiseksi.

---

### C6.1 Esikoulutetun mallin tarkastus ja jäljitettävyys

Arvioi ja varmista kolmannen osapuolen mallien alkuperät, lisenssit ja piilotetut käytökset ennen minkään hienosäätöä tai käyttöönottoa.

 #6.1.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen kolmannen osapuolen malliartefakti sisältää allekirjoitetun provenanssirekisterin, jossa on sekä lähdevarasto että commit-hash.
 #6.1.2    Taso: 1    Rooli: D/V
 Varmista, että malleja skannataan automatisoiduilla työkaluilla haitallisten kerrosten tai Troijan laukaisimien varalta ennen tuontia.
 #6.1.3    Taso: 2    Rooli: D
 Varmista, että transfer‑learning fine‑tunes läpäisevät adversarial-arvioinnin ja havaitsevat piilotetut käyttäytymiset.
 #6.1.4    Taso: 2    Rooli: V
 Varmista, että mallilisenssit, vientivalvonta-tunnisteet ja tietojen alkuperää koskevat lausumat tallennetaan ML‑BOM-tietueeseen.
 #6.1.5    Taso: 3    Rooli: D/V
 Varmista, että korkean‑riskin mallit (julkisesti ladatut painot, vahvistamattomat tekijät) pysyvät karanteenissa, kunnes inhimillinen tarkastus ja hyväksyntä on tehty.

---

### C6.2 Kehysten ja kirjastojen skannaus

Jatkuvasti skannaa ML-kehyksiä ja kirjastoja CVE-haavoittuvuuksien ja haitallisen koodin varalta pitääkseen ajonaikaisen pinon turvallisena.

 #6.2.1    Taso: 1    Rooli: D/V
 Varmista, että CI-putket käyttävät riippuvuusskannereita tekoälykehyksille ja kriittisille kirjastoille.
 #6.2.2    Taso: 1    Rooli: D/V
 Varmista, että kriittiset haavoittuvuudet (CVSS ≥ 7.0) estävät siirtymisen tuotantokuviin.
 #6.2.3    Taso: 2    Rooli: D
 Varmista, että staattinen koodianalyysi suoritetaan haarukoiduilla tai vendoroiduilla ML-kirjastoilla.
 #6.2.4    Taso: 2    Rooli: V
 Varmista, että kehyspäivitysehdotukset sisältävät turvallisuusvaikutusten arvioinnin, joka viittaa julkisiin CVE-syötteisiin.
 #6.2.5    Taso: 3    Rooli: V
 Varmista, että ajoaikaiset sensorit varoittavat odottamattomista dynaamisten kirjastojen latauksista, jotka poikkeavat allekirjoitetusta SBOM:sta.

---

### C6.3 Riippuvuuksien kiinnitys ja varmistus

Lukitse jokainen riippuvuus muuttumattomiin tiivisteisiin ja toista rakennusprosessit taatakseen identtiset, manipuloimattomat artefaktit.

 #6.3.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki pakettienhallintajärjestelmät pakottavat version kiinnityksen lockfilejen kautta.
 #6.3.2    Taso: 1    Rooli: D/V
 Varmista, että konttiviitteissä käytetään muuttumattomia tiivisteitä sen sijaan, että käytetään muuttuvia tageja.
 #6.3.3    Taso: 2    Rooli: D
 Varmista, että toistettavien rakennusten tarkistukset vertaavat hajautusarvoja CI-ajojen välillä ja varmistavat identtiset tulokset.
 #6.3.4    Taso: 2    Rooli: V
 Tarkista, että koontitodistukset tallennetaan 18 kuukauden ajaksi auditoitavuuden varmistamiseksi.
 #6.3.5    Taso: 3    Rooli: D
 Varmista, että vanhentuneet riippuvuudet laukaisevat automaattiset PR:t päivittämiseksi tai kiinnitettyjen versioiden haarukoinnin suorittamiseksi.

---

### C6.4 Luotettujen lähteiden täytäntöönpano

Salli artefaktien lataukset vain kryptografisesti varmennetuista lähteistä, jotka organisaatio on hyväksynyt, ja estä kaikki muut.

 #6.4.1    Taso: 1    Rooli: D/V
 Varmista, että mallin painot, datasetit ja kontit ladataan ainoastaan hyväksytyistä verkkotunnuksista tai sisäisistä rekistereistä.
 #6.4.2    Taso: 1    Rooli: D/V
 Varmista, että Sigstore/Cosign-allekirjoitukset vahvistavat julkaisijan identiteetin ennen kuin artefaktit tallennetaan paikallisesti välimuistiin.
 #6.4.3    Taso: 2    Rooli: D
 Varmista, että ulospäin suuntautuvat proxy-palvelimet estävät artefaktien lataukset ilman autentikointia, jotta luotettujen lähteiden politiikka toteutuu.
 #6.4.4    Taso: 2    Rooli: V
 Varmista, että varaston sallittujen luetteloiden tarkastukset suoritetaan neljännesvuosittain ja että kunkin merkinnän yhteydessä on todiste liiketoiminnallisesta perustelusta.
 #6.4.5    Taso: 3    Rooli: V
 Varmista, että politiikan rikkomukset laukaisevat artefaktien karanteeniin asettamisen sekä riippuvaisten pipeline-ajojen palautuksen.

---

### C6.5 Kolmannen osapuolen tietojoukon riskinarviointi

Arvioi ulkoiset datasetit niiden myrkyttämisen, vinoutumisen ja lainsäädännön noudattamisen varalta, ja seuraa niitä koko niiden elinkaaren ajan.

 #6.5.1    Taso: 1    Rooli: D/V
 Varmista, että ulkoiset aineistot käyvät läpi myrkyttämisriskin pisteytyksen (esim. datan sormenjälkitunnistus, poikkeavuuksien havaitseminen).
 #6.5.2    Taso: 1    Rooli: D
 Varmista, että puolueellisuusmittarit (demografinen tasapuolisuus, mahdollisuuksien tasa-arvo) lasketaan ennen datasetin hyväksyntää.
 #6.5.3    Taso: 2    Rooli: V
 Varmista, että datan alkuperä ja lisenssiehdot tallentuvat ML‑BOM-tietueisiin.
 #6.5.4    Taso: 2    Rooli: V
 Varmista, että säännöllinen seuranta havaitsee datan poikkeaman tai korruptoitumisen isännöidyissä tietojoukoissa.
 #6.5.5    Taso: 3    Rooli: D
 Varmista, että kielletty sisältö (tekijänoikeudet, PII) poistetaan automaattisen puhdistuksen avulla ennen koulutusta.

---

### C6.6 Toimitusketjun hyökkäysten seuranta

Havaitse toimitusketjun uhkat varhain CVE‑syötteiden, audit‑lokien analytiikan ja red‑team-simulaatioiden avulla.

 #6.6.1    Taso: 1    Rooli: V
 Varmista, että CI/CD-auditlokit virtaavat SIEMin havaitsemiin epäilyttäviin pakettien noutoihin tai muokattuihin rakennusvaiheisiin liittyviin tapahtumiin.
 #6.6.2    Taso: 2    Rooli: D
 Varmista, että incident response -pelikirjat sisältävät palautusmenettelyt kompromettoituneille malleille tai kirjastoille.
 #6.6.3    Taso: 3    Rooli: V
 Varmista, että uhkatiedustelun rikastuttamisen tunnisteet viittaavat ML‑spesifisiin indikaattoreihin (esim. mallinmyrkytyksen IoCs) hälytyksen priorisoinnissa.

---

### C6.7 ML‑BOM mallin artefaktit

Luo ja allekirjoita yksityiskohtaiset ML-spesifiset SBOM:t (ML‑BOM:t), jotta jälkikäyttäjät voivat vahvistaa komponenttien eheyden käyttöönoton aikana.

 #6.7.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen malliartefakti julkaisee ML‑BOMin, joka listaa tietojoukot, painot, hyperparametrit ja lisenssit.
 #6.7.2    Taso: 1    Rooli: D/V
 Varmista, että ML‑BOM:n generointi ja Cosignin allekirjoitus automatisoidaan CI:ssä ja että ne ovat pakollisia yhdistämiseen.
 #6.7.3    Taso: 2    Rooli: D
 Varmista, että ML‑BOMin täydellisyystarkastukset epäonnistuttavat rakennusvaiheessa, jos jokin komponentin metatieto (hash, lisenssi) puuttuu.
 #6.7.4    Taso: 2    Rooli: V
 Varmista, että downstream-kuluttajat voivat kysyä ML-BOM:eja API:n kautta validoidakseen tuodut mallit käyttöönoton yhteydessä.
 #6.7.5    Taso: 3    Rooli: V
 Varmista, että ML‑BOMit ovat versionhallinnassa ja niihin tehdään diff, jotta luvattomat muutokset voidaan havaita.

---

### Lähteet

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

## C7 Mallin käyttäytyminen, tulosten hallinta ja turvallisuusvarmistus

### Kontrollitavoite

Mallin tuotosten on oltava jäsenneltyjä, luotettavia, turvallisia, selitettävissä ja tuotannossa jatkuvasti valvottuja. Täten vähennetään hallusinaatioita, tietovuotoja, haitallista sisältöä ja hallitsemattomia toimintoja, samalla lisätään käyttäjien luottamusta sekä sääntelyvaatimusten noudattamista.

---

### C7.1 Tulostusmuodon noudattaminen

Tiukat skeemat, rajoitettu dekoodaus ja jälkikäsittelyn validointi estävät virheellisen tai haitallisen sisällön ennen kuin se leviää.

 #7.1.1    Taso: 1    Rooli: D/V
 Varmista, että vastausten skeemat (esim. JSON-skeemat) sisältyvät järjestelmäkehotukseen ja että jokainen tulos validoidaan automaattisesti; epäyhteensopivat tulokset laukaisevat korjaamisen tai hylkäämisen.
 #7.1.2    Taso: 1    Rooli: D/V
 Varmista, että rajoitettu dekoodaus (pysäytystunnisteet, säännölliset lausekkeet, maksimitokenit) on käytössä estämään ylivuotoa tai prompt-injection-sivukanavia.
 #7.1.3    Taso: 2    Rooli: D/V
 Varmista, että alasuuntautuneet komponentit käsittelevät tulokset luottamattomina ja validoivat ne skeemojen mukaan tai injektioturvallisten deserialisaattorien avulla.
 #7.1.4    Taso: 3    Rooli: V
 Varmista, että epäasianmukaiset output-tapahtumat kirjataan, niihin sovelletaan taajuusrajoitusta ja ne tuodaan esiin valvontaan.

---

### C7.2 Hallusinaatioiden havaitseminen ja lieventäminen

Epävarmuuden arviointi ja varautumisstrategiat rajoittavat keksittyjä vastauksia.

 #7.2.1    Taso: 1    Rooli: D/V
 Varmista, että token-tason logaritmiset todennäköisyydet, ensemblen itsejohdonmukaisuus tai hienosäädetyt hallusinaatiotunnistuslaitteet antavat jokaiselle vastaukselle luottamusarvon.
 #7.2.2    Taso: 1    Rooli: D/V
 Varmista, että konfiguroitavan luottamuskynnyn alapuolella olevat vastaukset laukaisevat fallback-työnkulut (esim. retrieval-augmented generation, toissijainen malli tai ihmisen arviointi).
 #7.2.3    Taso: 2    Rooli: D/V
 Varmista, että hallusinaatiotapaukset ovat merkittyjä juurisyyn metatiedoilla ja ne syötetään post-mortem- ja finetuning-putkistoihin.
 #7.2.4    Taso: 3    Rooli: D/V
 Varmista, että kynnysten ja tunnistimien kalibrointi suoritetaan uudelleen suurten mallien tai tietopohjan päivitysten jälkeen.
 #7.2.5    Taso: 3    Rooli: V
 Varmista, että dashboardin visualisoinnit seuraavat hallusinaatioiden esiintymistiheyttä.

---

### C7.3 Tulostuksen turvallisuus ja yksityisyyden suodatus

Käytäntöön perustuvat suodattimet ja punaisen tiimin kattavuus suojaavat käyttäjiä ja luottamuksellisia tietoja.

 #7.3.1    Taso: 1    Rooli: D/V
 Varmista, että ennen generointia ja generoinnin jälkeen käytettävät luokittelijat estävät politiikan mukaisen viha-, häirintä-, itsensä vahingoittamiseen liittyvän, äärijärjestöihin liittyvän sekä seksuaalisesti eksplisiittisen sisällön.
 #7.3.2    Taso: 1    Rooli: D/V
 Varmista, että PII/PCI-tunnistus ja automaattinen punakointi suoritetaan jokaisessa vastauksessa; rikkomukset laukaisevat tietosuojatapauksen.
 #7.3.3    Taso: 2    Rooli: D
 Varmista, että salassapitotunnisteet (esim. liikesalaisuudet) leviävät eri modaalisuuksien välillä vuodon estämiseksi tekstissä, kuvissa tai koodissa.
 #7.3.4    Taso: 3    Rooli: D/V
 Varmista, että suodattimen ohitusyritykset tai korkean riskin luokitukset vaativat toissijaista hyväksyntää tai käyttäjän uudelleentodentamista.
 #7.3.5    Taso: 3    Rooli: D/V
 Varmista, että suodatustasot heijastavat sovellettavaa lainsäädäntöä sekä käyttäjän ikää ja roolia koskevaa kontekstia.

---

### C7.4 Ulostulon ja toimintojen rajoittaminen

Nopeusrajoitukset ja hyväksyntäportit estävät väärinkäytön ja liiallista autonomiaa.

 #7.4.1    Taso: 1    Rooli: D
 Varmista, että käyttäjäkohtaiset ja API-avaimikohtaiset kiintiöt rajoittavat pyyntöjen, tokenien ja kustannusten määrää eksponentiaalisen takaisinvetäytymisen avulla 429-virheissä.
 #7.4.2    Taso: 1    Rooli: D/V
 Varmista, että etuoikeutetut toiminnot (tiedostojen kirjoitukset, koodin suoritukset, verkkopyynnöt) vaativat politiikkapohjaista hyväksyntää tai ihmisen mukanaoloa prosessissa.
 #7.4.3    Taso: 2    Rooli: D/V
 Varmista, että modaalien välisten yhdenmukaisuustarkastusten avulla samalle pyynnölle liittyviä kuvia, koodia ja tekstiä ei voi käyttää haitallisen sisällön salakuljettamiseen.
 #7.4.4    Taso: 2    Rooli: D
 Varmista, että agentin delegoinnin syvyys, rekursion rajat ja sallittujen työkalujen luettelot on määritelty selvästi.
 #7.4.5    Taso: 3    Rooli: V
 Varmista, että rajoitusten rikkominen tuottaa strukturoituja turvallisuustapahtumia SIEM-järjestelmään syötettäväksi.

---

### C7.5 Tulosten selittävyys

Läpinäkyvät signaalit parantavat käyttäjien luottamusta ja sisäistä virheenkorjausta.

 #7.5.1    Taso: 2    Rooli: D/V
 Varmista, että käyttäjälle näkyvät luottamusarvot tai lyhyet perustelujen yhteenvedot näytetään silloin, kun riskinarviointi katsoo sen sopivaksi.
 #7.5.2    Taso: 2    Rooli: D/V
 Varmista, että generoituneet selitykset eivät paljasta arkaluonteisia järjestelmäkehotteita tai yrityksen omaa dataa.
 #7.5.3    Taso: 3    Rooli: D
 Varmista, että järjestelmä tallentaa token-tason log-todennäköisyyksiä tai huomiokarttoja ja säilyttää ne valtuutetun tarkastusta varten.
 #7.5.4    Taso: 3    Rooli: V
 Varmista, että selitettävyyden artefaktit ovat versionhallinnassa yhdessä mallien julkaisujen kanssa auditointia varten.

---

### C7.6 Monitoroinnin Integraatio

Reaaliaikainen havaittavuus sulkee kehityksen ja tuotannon välisen silmukan.

 #7.6.1    Taso: 1    Rooli: D
 Varmista, että mittarit (skeeman rikkomukset, hallusinaatioiden osuus, myrkyllisyys, henkilötietojen vuotaminen, viive, kustannukset) virtaavat keskitetylle valvonta-alustalle.
 #7.6.2    Taso: 1    Rooli: V
 Varmista, että jokaiselle turvallisuusmittarille on määritelty hälytysraja-arvot ja että on-call eskalointireitit ovat käytössä.
 #7.6.3    Taso: 2    Rooli: V
 Varmista, että koontinäytöt korreloivat tulospoikkeamien kanssa mallin/version, ominaisuuslipun ja ylävirran datamuutosten kanssa.
 #7.6.4    Taso: 2    Rooli: D/V
 Varmista, että valvontatiedot palaavat takaisin uudelleenkoulutukseen, hienosäätöön tai sääntöpäivityksiin dokumentoidun MLOps-työnkulun puitteissa.
 #7.6.5    Taso: 3    Rooli: V
 Varmista, että seurantaputket on penetraatiotestattu ja niihin on otettu käyttöön pääsynhallinta, jotta arkaluontoisten lokien vuotaminen estetään.

---

### 7.7 Generatiivisen median turvatoimet

Varmista, että tekoälyjärjestelmät eivät tuota laittomia, haitallisia tai luvattomia mediasisältöjä noudattamalla politiikan rajoituksia, tulosten validointia ja jäljitettävyyttä.

 #7.7.1    Taso: 1    Rooli: D/V
 Tarkista, että järjestelmän kehotteet ja käyttäjän ohjeet kieltävät nimenomaan laittoman, haitallisen tai suostumuksetta tuotetun deepfake-median tuottamisen (esim. kuva, video, ääni).
 #7.7.2    Taso: 2    Rooli: D/V
 Varmista, että kehotteet suodatetaan, kun yritetään luoda henkilöllisyyden jäljittelyä, seksuaalisesti eksplisiittisiä deepfake-videoita tai materiaalia, joka esittää oikeita henkilöitä ilman heidän suostumustaan.
 #7.7.3    Taso: 2    Rooli: V
 Varmista, että järjestelmä käyttää havaintoperusteista hajautusta, vesileiman havaitsemista tai sormenjälkitunnistusta estääkseen tekijänoikeudella suojatun median luvattoman kopioinnin.
 #7.7.4    Taso: 3    Rooli: D/V
 Varmista, että kaikki tuotetut mediat on kryptografisesti allekirjoitettu, vesileimattu tai upotettu murtovarmennettuihin provenanssi-metatietoihin, jotta jäljitettävyys on taattu seuraavissa vaiheissa.
 #7.7.5    Taso: 3    Rooli: V
 Varmista, että kiertämisyritykset (esim. kehotteen hämärtäminen, slangi, vastustuksellinen sanamuoto) havaitaan, kirjataan ylös ja taajuusrajoitetaan; toistuva väärinkäyttö raportoidaan valvontajärjestelmiin.

### Lähteet

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

## C8-muisti, upotukset & vektoritietokantojen turvallisuus

### Kontrollitavoite

Embeddingit ja vektorivarastot toimivat nykyaikaisten tekoälyjärjestelmien 'elävänä muistina', jotka jatkuvasti vastaanottavat käyttäjältä annettua dataa ja tuovat sen takaisin mallien konteksteihin RAG-menetelmän kautta. Jos tätä muistia ei hallita, se voi vuotaa henkilötietoja (PII), rikkoa suostumuksia tai johtaa alkuperäisen tekstin rekonstruointiin. Tämän kontrolliperheen tavoitteena on vahvistaa muistiputkia ja vektorivarastoja siten, että pääsy on least-privilege-periaatteen mukaista, embeddingit ovat yksityisyyttä suojaavia, tallennetut vektorit vanhenevat tai voidaan peruuttaa pyydettäessä, ja kunkin käyttäjän muisti ei koskaan saastuta toisen käyttäjän pyyntöjä tai vastauksia.

---

### C8.1 Pääsynhallinta muistissa ja RAG-indekseissä

Toteuta hienojakoiset pääsynvalvonnat jokaiselle vektorikokoelmalle.

 #8.1.1    Taso: 1    Rooli: D/V
 Varmista, että rivitaso- ja nimialuetason pääsynvalvontasäännöt rajoittavat lisäys-, poisto- ja kyselytoiminnot kunkin asiakkaan, kokoelman tai asiakirjamerkinnän mukaan.
 #8.1.2    Taso: 1    Rooli: D/V
 Varmista, että API-avaimet tai JWT:t kantavat rajattuja vaatimuksia (esim. kokoelmatunnisteet, toimintaverbit) ja ne kierrätetään vähintään neljännesvuosittain.
 #8.1.3    Taso: 2    Rooli: D/V
 Varmista, että oikeuksien korottamisen yritykset (esim. nimialueiden väliset samankaltaisuuskyselyt) havaitaan ja kirjataan SIEMiin 5 minuutin kuluessa.
 #8.1.4    Taso: 2    Rooli: D/V
 Varmista, että vektoritietokannan auditlokit kirjaavat käyttäjätunnisteen, toimenpiteen, vektori-ID/namespace, samankaltaisuuskynnys ja tulosten määrän.
 #8.1.5    Taso: 3    Rooli: V
 Varmista, että pääsynhallinnan päätökset testataan ohitusaukkojen varalta aina, kun moottoreita päivitetään tai indeksin shardauksen säännöt muuttuvat.

---

### C8.2 Upotusten sanitointi & validointi

Tarkista teksti etukäteen henkilötietojen varalta, piilota tai pseudonyymisoi ennen vektorointia, ja tarvittaessa jälkikäsitellä upotukset poistaaksesi jäljellä olevat signaalit.

 #8.2.1    Taso: 1    Rooli: D/V
 Varmista, että PII ja säännelty data tunnistetaan automaattisilla luokittelijoilla ja maskataan, tokenisoidaan tai poistetaan ennen upottamista.
 #8.2.2    Taso: 1    Rooli: D
 Varmista, että upotusputket hylkäävät tai eristävät syötteet, jotka sisältävät suoritettavaa koodia tai ei-UTF-8-artifakteja, jotka voisivat saastuttaa indeksin.
 #8.2.3    Taso: 2    Rooli: D/V
 Varmista, että paikallinen tai metrinen differentiaalisen yksityisyyden sanitointi sovelletaan lauseen upotusvektoreihin, joiden etäisyys mihinkä tahansa tunnettuun PII-tunnukseen on alle määritettävän kynnysarvon.
 #8.2.4    Taso: 2    Rooli: V
 Varmista, että sanitoinnin tehokkuus (esim. PII:n punaisoinnin kattavuus, semanttinen muutos) validoidaan vähintään puolivuosittain benchmark-korpora vastaan.
 #8.2.5    Taso: 3    Rooli: D/V
 Varmista, että sanitointikonfiguraatiot ovat versionhallinnassa ja muutokset käyvät vertaisarvioinnin läpi.

---

### C8.3 Muistin vanhentuminen, peruutus ja poisto

GDPR 'oikeus tulla unohdetuksi' ja vastaavat lait edellyttävät oikea-aikaista poistamista; vektorivarastojen on siksi tuettava TTL-arvot, kovapoistot ja hautausmerkinnät, jotta peruutetut vektorit eivät voi palautua tai uudelleenindeksoida.

 #8.3.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen vektori- ja metadata-tietue sisältää TTL:n tai selkeän säilytysmerkinnän, jota automatisoidut siivoustoiminnot noudattavat.
 #8.3.2    Taso: 1    Rooli: D/V
 Varmista, että käyttäjän aloittamat poistopyynnöt poistavat vektorit, metatiedot, välimuistikopiot ja johdannaisindeksit 30 päivän kuluessa.
 #8.3.3    Taso: 2    Rooli: D
 Varmista, että loogiset poistot toteutetaan kryptografisella tuhoamisella tallennuslohkoille, jos laitteisto tukee sitä, tai että avainvaraston avaimet tuhotaan.
 #8.3.4    Taso: 3    Rooli: D/V
 Varmista, että vanhentuneet vektorit poistetaan lähimmän naapurin haun tuloksista alle 500 ms kuluttua vanhentumisesta.

---

### C8.4 Estä upotusten inversio & vuoto

Viimeaikaiset puolustukset—kohinan superpositio, projektioverkot, privacy-neuronin perturbointi ja sovelluskerroksen salaus—voivat alentaa token-tason inversioprosentteja alle 5%.

 #8.4.1    Taso: 1    Rooli: V
 Varmista, että muodollinen uhkamalli, joka kattaa inversiohyökkäykset, jäsenyyden inferenssi-hyökkäykset ja attribuuttien inferenssi-hyökkäykset, on olemassa ja sitä tarkastellaan vuosittain.
 #8.4.2    Taso: 2    Rooli: D/V
 Varmista, että sovelluskerroksen salaus tai haettavissa oleva salaus suojaa vektoreita suorilta lukemilta infrastruktuurin ylläpitäjien tai pilviympäristön henkilöstön toimesta.
 #8.4.3    Taso: 3    Rooli: V
 Varmista, että suojausparametrit (ε DP:lle, kohinan σ, projektion rank k) tasapainottavat yksityisyyden ≥ 99 % tokenin suojauksen ja hyödyllisyyden ≤ 3 % tarkkuuden menetys.
 #8.4.4    Taso: 3    Rooli: D/V
 Varmista, että inversio-resilienssimittarit ovat osa julkaisun portteja mallipäivityksiä varten, ja että niille on määritelty regressiobudjetit.

---

### C8.5 Käyttäjäkohtaisen muistin laajuuden valvonta

Cross-tenant leakage on edelleen yksi suurimmista RAG-riskeistä: virheellisesti suodatetut samankaltaisuuskyselyt voivat paljastaa toisen asiakkaan yksityiset dokumentit.

 #8.5.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen haun kysely on jälkisuodatettu vuokraajan tai käyttäjän tunnisteen mukaan ennen kuin se siirretään LLM:n kehotteeseen.
 #8.5.2    Taso: 1    Rooli: D
 Varmista, että kokoelman nimet tai nimiavaruus-ID:t ovat suolatut kunkin käyttäjän tai vuokraajan mukaan, jotta vektorit eivät törmää toisiinsa eri konteksteissa.
 #8.5.3    Taso: 2    Rooli: D/V
 Varmista, että konfiguroitavan etäisyyskynnyksen ylittävät samankaltaisuustulokset, jotka ovat kutsujan toiminnan ulkopuolella, hylätään ja laukaistaan turvallisuusvaroituksia.
 #8.5.4    Taso: 2    Rooli: V
 Varmista, että moniasiakkaiden kuormitustestit simuloivat hyökkäysyrityksiä, joissa yritetään hakea rajojen ulkopuolisia asiakirjoja, ja osoittavat, ettei tapahdu tietovuotoja.
 #8.5.5    Taso: 3    Rooli: D/V
 Varmista, että salausavaimet on eroteltu kunkin vuokralaisen mukaan, jotta kryptografinen eristys säilyy, vaikka fyysinen tallennus on jaettu.

---

### C8.6 Kehittyneen muistijärjestelmän turvallisuus

kehittyneille muistirakenteille suunnatut turvallisuusvalvontatoimet, jotka kattavat episodisen, semanttisen ja työmuistin sekä niihin liittyvät erityiset eristys- ja validointivaatimukset.

 #8.6.1    Taso: 1    Rooli: D/V
 Varmista, että erilaisilla muistityypeillä (episodinen muisti, semanttinen muisti, työmuisti) on erilliset turvallisuuskontekstit, roolipohjainen pääsynvalvonta, erilliset salausavaimet sekä jokaiselle muistityypille dokumentoidut pääsynmallit.
 #8.6.2    Taso: 2    Rooli: D/V
 Varmista, että muistien konsolidointiprosessit sisältävät turvallisuusvarmennuksen estämään haitallisten muistojen syöttöä sisällön puhdistuksen, lähteen varmennuksen ja eheysvalvonnan kautta ennen tallennusta.
 #8.6.3    Taso: 2    Rooli: D/V
 Varmista, että muistista haettavat hakupyynnöt validoidaan ja puhdistetaan, jotta luvattomien tietojen paljastuminen estetään kyselykaavojen analyysin, pääsynvalvonnan toteuttamisen ja tulosten suodatuksen kautta.
 #8.6.4    Taso: 3    Rooli: D/V
 Varmista, että muistin pyyhkimisen mekanismit poistavat arkaluontoiset tiedot turvallisesti kryptografisen poistamisen takuilla käyttämällä avaimen poistamista, moninkertaista ylikirjoitusta tai laitteistopohjaista turvallista poistamista varmistustodistuksin.
 #8.6.5    Taso: 3    Rooli: D/V
 Varmista, että muistijärjestelmän eheys valvotaan jatkuvasti luvattomien muutosten tai korruptoitumisen varalta, käyttämällä tarkistussummia, auditlokkeja ja automatisoituja hälytyksiä, kun muistisisältö muuttuu normaalin toiminnan ulkopuolelle.

---

### Lähteet

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

## 9 Autonominen Orkestrointi & Agenttinen Toiminta Turvallisuus

### Kontrollitavoite

Varmista, että autonomiset tai moniagenttiset tekoälyjärjestelmät voivat ainoastaan suorittaa toimenpiteitä, jotka ovat erikseen tarkoitettuja, autentikoituja, auditoitavia ja rajoitettujen kustannus- ja riskirajojen puitteissa. Tämä suojaa uhkia vastaan, kuten autonomisen järjestelmän kompromissi, työkalun väärinkäyttö, agentin silmukan havaitseminen, viestinnän kaappaus, identiteetin väärentäminen, parven manipulointi ja tarkoituksen manipulointi.

---

### 9.1 Agentin tehtäväsuunnittelu ja rekursion budjetit

Rajoita rekursiivisia suunnitelmia ja aseta ihmisen tarkastuspisteet pakollisiksi etuoikeutettujen toimintojen suorittamisen yhteydessä.

 #9.1.1    Taso: 1    Rooli: D/V
 Varmista, että maksimirekursion syvyys, haun leveys, reaaliaikainen aika, tokenit ja agentin suorituksen rahallinen kustannus ovat keskitetysti määritetyt ja versiohallinnassa.
 #9.1.2    Taso: 1    Rooli: D/V
 Varmista, että etuoikeutetut tai peruuttamattomat toiminnot (esim. koodimuutokset, rahansiirrot) vaativat ilmeisen ihmisen hyväksynnän auditointikanavan kautta ennen toteutusta.
 #9.1.3    Taso: 2    Rooli: D
 Varmista, että reaaliaikaiset resurssiseurantajärjestelmät laukaisevat piirikytkimen katkaisun, kun mikään budjetin kynnysarvo ylitetään, ja pysäyttävät lisätehtävien laajentamisen.
 #9.1.4    Taso: 2    Rooli: D/V
 Varmista, että katkaisijan tapahtumat kirjataan agentin tunnuksella, laukaisutilanteella ja tallennetulla suunnitelman tilalla forensiikkatarkastelua varten.
 #9.1.5    Taso: 3    Rooli: V
 Varmista, että turvallisuustestit kattavat budjetin loppumisen ja hallitsemattoman suunnitelman skenaariot, ja varmistavat turvallisen pysäytyksen ilman tietojen menetystä.
 #9.1.6    Taso: 3    Rooli: D
 Varmista, että budjettipolitiikat on esitetty politiikka-koodina ja ne pannaan täytäntöön CI/CD:ssä estämään konfiguraation poikkeamat.

---

### 9.2 Työkalun lisäosan hiekkalaatikkotestaus

Eristä työkalujen vuorovaikutukset, jotta estetään luvattoman järjestelmän pääsy tai koodin suoritus.

 #9.2.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen työkalu tai lisäosa suorittaa toimintansa OS-tason, kontti- tai WASM-tason hiekkalaatikkoympäristössä, jossa noudatetaan minimioikeuksien tiedostojärjestelmä-, verkko- ja järjestelmäkutsupolitiikat.
 #9.2.2    Taso: 1    Rooli: D/V
 Varmista, että hiekkalaatikon resurssikiintiöt (CPU, muisti, levy, verkkoliikenteen ulosmeno) sekä suoritusaikakatkaisut ovat voimassa ja kirjataan.
 #9.2.3    Taso: 2    Rooli: D/V
 Varmista, että työkalujen binäärit tai kuvaustiedostot ovat digitaalisesti allekirjoitetut; allekirjoitukset vahvistetaan ennen lataamista.
 #9.2.4    Taso: 2    Rooli: V
 Varmista, että sandbox-telemetria virtaa SIEMiin; poikkeavuudet (esim. lähteviin yhteyksiin kohdistuneet yritykset) laukaisevat hälytykset.
 #9.2.5    Taso: 3    Rooli: V
 Varmista, että korkean riskin lisäosat käyvät läpi turvallisuustarkastukset ja tunkeutumistestaukset ennen tuotantoon käyttöönottoa.
 #9.2.6    Taso: 3    Rooli: D/V
 Varmista, että hiekkalaatikon pakoyritykset estetään automaattisesti ja haitallinen lisäosa on eristetty tutkimusta varten.

---

### 9.3 Omatoiminen silmukka ja kustannusten rajoitus

Havaitse ja pysäytä hallitsematon agenttien välinen rekursio sekä kustannusten räjähtävä kasvu.

 #9.3.1    Taso: 1    Rooli: D/V
 Varmista, että agenttien välisissä kutsuissa on hop-limit tai TTL, jonka ajonaikainen ympäristö pienentää ja valvoo.
 #9.3.2    Taso: 2    Rooli: D
 Varmista, että agentit säilyttävät ainutlaatuisen kutsujen graafin tunnisteen, jotta voidaan havaita itsensä kutsumista tai syklisiä malleja.
 #9.3.3    Taso: 2    Rooli: D/V
 Varmista, että kumulatiiviset laskentayksikkö- ja kululaskurit seurataan jokaisessa pyyntöketjussa; rajan ylitys keskeyttää ketjun.
 #9.3.4    Taso: 3    Rooli: V
 Varmista, että formaali analyysi tai mallintarkastus osoittaa, ettei agenttien protokollissa ole rajatonta rekursiota.
 #9.3.5    Taso: 3    Rooli: D
 Varmista, että silmukan keskeytys-tapahtumat tuottavat hälytyksiä ja syöttävät jatkuvan parantamisen mittareita.

---

### 9.4 Protokollatasoinen väärinkäytön esto

Varmista agenttien ja ulkoisten järjestelmien välisten turvallisten viestintäkanavien käyttö estääkseen kaappaamisen tai manipuloinnin.

 #9.4.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki agentin ja työkalun välinen viestintä sekä agentin ja agentin välinen viestintä on todentettu ja end-to-end-salaus on käytössä.
 #9.4.2    Taso: 1    Rooli: D
 Varmista, että skeemat validoidaan tiukasti; tuntemattomat kentät tai virheelliset viestit hylätään.
 #9.4.3    Taso: 2    Rooli: D/V
 Varmista, että eheystarkistukset (MAC-tarkistukset tai digitaaliset allekirjoitukset) kattavat koko viestin payloadin mukaan lukien työkalun parametrit.
 #9.4.4    Taso: 2    Rooli: D
 Varmista, että uudelleenkäytön esto (nonce-arvot tai aikaleimaikkunat) on toteutettu protokollakerroksessa.
 #9.4.5    Taso: 3    Rooli: V
 Varmista, että protokollien toteutukset altistuvat fuzzingille ja staattiselle analyysille injektointi- tai deserialisointivirheiden varalta.

---

### Agentin identiteetti ja manipulointitodiste

Varmista, että toimet ovat jäljitettävissä ja muutokset havaittavissa.

 #9.5.1    Taso: 1    Rooli: D/V
 Varmista, että jokaisella agentin instanssilla on ainutlaatuinen kryptografinen identiteetti (avainpari tai laitteistopohjainen tunniste).
 #9.5.2    Taso: 2    Rooli: D/V
 Varmista, että kaikki agentin toimet on allekirjoitettu ja aikaleimattu; lokit sisältävät allekirjoituksen kiistämättömyyden varmistamiseksi.
 #9.5.3    Taso: 2    Rooli: V
 Varmista, että manipuloinnin todentavat lokit tallennetaan append-only- tai write-once-mediassa.
 #9.5.4    Taso: 3    Rooli: D
 Varmista, että identiteettisavaimet kierrätetään määritellyn aikataulun mukaan ja kompromissin indikaattoreiden perusteella.
 #9.5.5    Taso: 3    Rooli: D/V
 Tarkista, että spoofing- tai avaimen-konfliktiyritykset laukaisevat välittömän karanteenin kyseiselle agentille.

---

### 9.6 Moni-Agenttinen parven riskin vähentäminen

Vähennä kollektiivisen-käyttäytymisen vaaroja eristyksen ja formaalin turvallisuusmallinnuksen avulla.

 #9.6.1    Taso: 1    Rooli: D/V
 Varmista, että eri turvallisuusalueilla toimivat agentit suorittavat toimintansa erillisissä ajonaikaisissa sandbox-ympäristöissä tai verkkosegmentteissä.
 #9.6.2    Taso: 3    Rooli: V
 Varmista, että parven käyttäytymistä on mallinnettu ja formalisesti todistettu elävyyden ja turvallisuuden varmistamiseksi ennen käyttöönottoa.
 #9.6.3    Taso: 3    Rooli: D
 Varmista, että ajonaikaiset valvontajärjestelmät havaitsevat ilmaantuvat vaaralliset käytösmallit (esim. oscilointi, kuolleet lukitukset) ja käynnistä korjaavat toimenpiteet.

---

### 9.7 Käyttäjän ja työkalun todennus / valtuutus

Ota käyttöön vahvat pääsynhallintamenettelyt jokaiselle agentin käynnistämälle toiminnolle.

 #9.7.1    Taso: 1    Rooli: D/V
 Varmista, että agentit todentavat itsensä ensiluokkaisina identiteetteina alijärjestelmiin, eikä koskaan käytä loppukäyttäjän tunnuksia.
 #9.7.2    Taso: 2    Rooli: D
 Varmista, että hienojakoiset valtuutuspolitiikat rajoittavat sekä sitä, mitkä työkalut agentti voi kutsua että mitkä parametrit sen on mahdollista toimittaa.
 #9.7.3    Taso: 2    Rooli: V
 Varmista, että oikeuksien tarkistukset arvioidaan uudelleen jokaisella kutsulla (jatkuva valtuutus), ei ainoastaan istunnon alussa.
 #9.7.4    Taso: 3    Rooli: D
 Varmista, että delegoidut oikeudet vanhentuvat automaattisesti ja vaativat uudelleen suostumuksen aikakatkaisun jälkeen tai laajuuden muutoksen jälkeen.

---

### 9.8 Agent-to-Agent Viestinnän turvallisuus

Salaa ja suojaa kaikkien agenttien välisten viestien eheyden estääkseen salakuuntelun ja manipuloinnin.

 #9.8.1    Taso: 1    Rooli: D/V
 Varmista, että molemminpuolinen todentaminen ja perfect-forward-secret encryption (esim. TLS 1.3) ovat agenttikanavien kannalta pakollisia.
 #9.8.2    Taso: 1    Rooli: D
 Varmista, että viestin eheys ja alkuperä varmistetaan ennen käsittelyä; epäonnistumiset laukaisevat hälytykset ja viesti hylätään.
 #9.8.3    Taso: 2    Rooli: D/V
 Varmista, että viestinnän metatiedot (aikaleimat, sekvenssinumerot) kirjataan talteen forensisen rekonstruoinnin tueksi.
 #9.8.4    Taso: 3    Rooli: V
 Varmista, että muodollinen todentaminen tai mallintarkastus vahvistaa, ettei protokollan tilakoneita voida ajaa turvattomiin tiloihin.

---

### 9.9 Tarkoituksen varmistaminen ja rajoitteiden täytäntöönpano

Varmista, että agentin toimet ovat käyttäjän ilmoittaman aikomuksen ja järjestelmän rajoitteiden mukaisia.

 #9.9.1    Taso: 1    Rooli: D
 Varmista, että suoritusta edeltävät rajoitteiden ratkaisut tarkistavat ehdotetut toimet kovakoodattujen turvallisuus- ja ohjesääntöjen mukaisesti.
 #9.9.2    Taso: 2    Rooli: D/V
 Varmista, että vaikutukseltaan suuria toimintoja (rahoitus-, tuho-, ja yksityisyyteen liittyviä) vaativat aloittaneen käyttäjän ilmeisen aikomuksen vahvistuksen.
 #9.9.3    Taso: 2    Rooli: V
 Varmista, että jälkivaiheen ehtotarkastukset varmistavat, että suoritetut toimet saavuttivat halutut vaikutukset ilman sivuvaikutuksia; poikkeamat laukaisevat palautuksen.
 #9.9.4    Taso: 3    Rooli: V
 Varmista, että formaaliset menetelmät (esim. mallintarkastus, teoreemien todistaminen) tai ominaisuusperusteiset testit osoittavat, että agenttisuunnitelmat täyttävät kaikki määritellyt rajoitteet.
 #9.9.5    Taso: 3    Rooli: D
 Varmista, että intent-mismatch tai constraint-violation-tapaukset ruokkivat jatkuvan parantamisen kiertokulkuja ja uhkatiedon jakamista.

---

### 9.10 Agentin päättelystrategia turvallisuus

Erilaisten päättelystrategioiden turvallinen valinta ja toteutus, mukaan lukien ReAct, Chain-of-Thought ja Tree-of-Thoughts-lähestymistavat.

 #9.10.1    Taso: 1    Rooli: D/V
 Varmista, että päättelystrategian valinta noudattaa deterministisiä kriteerejä (syötteen monimutkaisuus, tehtävätyyppi, turvallisuuskonteksti) ja identtiset syötteet tuottavat samat strategian valinnat samassa turvallisuuskontekstissa.
 #9.10.2    Taso: 1    Rooli: D/V
 Varmista, että jokaisella päättelystrategialla (ReAct, Chain-of-Thought, Tree-of-Thoughts) on omistetut syötteen validointi, tuloksen sanitointi ja suoritusaikarajat, jotka vastaavat sen kognitiivista lähestymistapaa.
 #9.10.3    Taso: 2    Rooli: D/V
 Varmista, että päättelystrategian siirtymät kirjataan täydellisellä kontekstilla, mukaan lukien syötteen ominaisuudet, valintakriteerien arvot ja suoritustiedot auditointipolun rekonstruointia varten.
 #9.10.4    Taso: 2    Rooli: D/V
 Varmista, että Tree-of-Thoughts päättely sisältää haarojen karsimismekanismit, jotka lopettavat etsinnän, kun havaitaan sääntöjen rikkomuksia, resurssirajoituksia tai turvallisuusrajoja.
 #9.10.5    Taso: 2    Rooli: D/V
 Varmista, että ReAct (Reason-Act-Observe) syklit sisältävät jokaisessa vaiheessa validointipisteet: päättelyaskeleen tarkistus, toiminnan valtuutus ja havainnon puhdistus ennen etenemistä.
 #9.10.6    Taso: 3    Rooli: D/V
 Varmista, että päättelystrategian suorituskykymittarit (suoritusaika, resurssien käyttö, tulosteen laatu) seurataan automaattisilla hälytyksillä, kun mittarit poikkeavat määritellyistä kynnysarvoista.
 #9.10.7    Taso: 3    Rooli: D/V
 Varmista, että useista strategioista koostuvat hybridi-päätöksentekomenetelmät säilyttävät kaikkien koostettujen strategioiden syötteen validoinnin ja tulosteiden rajoitteet ilman, että mikään turvallisuusvalvonta ohitetaan.
 #9.10.8    Taso: 3    Rooli: D/V
 Varmista, että päättelystrategian turvallisuustestaus sisältää virheellisesti muotoiltujen syötteiden fuzzingin, suunnitellut adversarial-kehotteet, joiden tarkoituksena on pakottaa strategian vaihtaminen, sekä jokaiselle kognitiiviselle lähestymistavalle tarkoitetun reunatilan testauksen.

---

### 9.11 Agentin elinkaaren tilanhallinta ja turvallisuus

Turvallisen agentin alustus, tilansiirtymät ja lopetus kryptografisilla auditointijäljillä sekä määritellyillä palautusmenettelyillä.

 #9.11.1    Taso: 1    Rooli: D/V
 Varmista, että agentin käynnistys sisältää kryptografisen identiteetin muodostamisen laitteistopohjaisten tunnisteiden avulla ja muuttumattomat käynnistysauditointilokit, jotka sisältävät agentin tunnuksen (ID), aikaleiman, konfiguraatiohajautteen sekä käynnistysparametrit.
 #9.11.2    Taso: 2    Rooli: D/V
 Varmista, että agentin tilansiirtymät ovat kryptografisesti allekirjoitettuja, aikaleimattuja ja lokitettuja täydellisen kontekstin kanssa, mukaan lukien laukaisutapahtumat, aiemman tilan hash-arvo, uuden tilan hash-arvo sekä suoritetut turvallisuustarkastukset.
 #9.11.3    Taso: 2    Rooli: D/V
 Varmista, että agentin sammuttamisproseduureihin sisältyy turvallinen muistin pyyhkiminen kryptografisen tyhjennyksen tai moninkertaisen ylikirjoitusmenetelmän avulla, tunnistetietojen mitätöinti varmenteen myöntäjän ilmoituksella sekä törmäyksen todentavien lopetustodistusten luominen.
 #9.11.4    Taso: 3    Rooli: D/V
 Varmista, että agentin palautusmekanismit validoivat tilan eheyden kryptografisilla tarkistussummilla (SHA-256 vähintään) ja palauttavat tunnettuun hyvään tilaan, kun korruptio havaitaan, käyttäen automaattisia hälytyksiä ja manuaalisia hyväksyntävaatimuksia.
 #9.11.5    Taso: 3    Rooli: D/V
 Varmista, että agentin pysyvyyteen liittyvät mekanismit salavat arkaluonteiset tilatiedot jokaiselle agentille omilla AES-256-avaimilla ja toteuttavat turvallisen avainten kierrätyksen määritettävissä aikatauluissa (enintään 90 päivää) katkottomalla käyttöönotolla.

---

### 9.12 Työkalujen integraation turvallisuuskehys

Turvallisuustoimenpiteet dynaamisten työkalujen lataamiseen, suorittamiseen ja tulosten validointiin sekä määritellyt riskinarviointi- ja hyväksyntäprosessit.

 #9.12.1    Taso: 1    Rooli: D/V
 Varmista, että työkalukuvaukset sisältävät turvallisuustiedot, jotka määrittelevät vaaditut oikeudet (luku/kirjoitus/suoritus), riskitasot (matala/keskitaso/korkea), resurssirajoitteet (CPU, muist, verkko) sekä validointivaatimukset, jotka on dokumentoitu työkalujen manifeeteissä.
 #9.12.2    Taso: 1    Rooli: D/V
 Varmista, että työkalun suoritustulokset validoidaan odotettujen skeemojen (JSON Schema, XML Schema) ja turvallisuuspolitiikkojen (tuloksen puhdistus, datan luokittelu) mukaan ennen integraatiota, jossa sovelletaan aikakatkaisurajoja ja virheenkäsittelymenettelyjä.
 #9.12.3    Taso: 2    Rooli: D/V
 Varmista, että työkalujen vuorovaikutuslokit sisältävät yksityiskohtaisen turvallisuuskontekstin, mukaan lukien oikeuksien käytön, tiedon käyttömallit, suoritusajan, resurssien kulutuksen ja palautuskoodit sekä SIEM-integraatiota varten strukturoitu lokitus.
 #9.12.4    Taso: 2    Rooli: D/V
 Varmista, että dynaamiset työkalujen latausmekanismit vahvistavat digitaalisten allekirjoitusten oikeellisuuden PKI-infrastruktuurin avulla ja toteuttavat turvalliset latausprotokollat hiekkalaatikkoeristyksen ja käyttöoikeuksien varmistamisen ennen suoritusta.
 #9.12.5    Taso: 3    Rooli: D/V
 Varmista, että työkalun turvallisuusarvioinnit käynnistetään automaattisesti uusille versioille, joissa on pakolliset hyväksyntäportit, mukaan lukien staattinen analyysi, dynaaminen testaus ja turvallisuustiimin tarkastus, dokumentoiduilla hyväksyntäkriteereillä ja SLA-vaatimuksilla.

---

#### Lähteet

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

## 10 Hyökkäyskestävyys ja yksityisyyden suojaus

### Kontrollitavoite

Varmista, että tekoälymallit ovat luotettavia, yksityisyyttä suojaavia ja väärinkäytöksiä vastaan kestäviä, kun niihin kohdistuu välttely-, inferenssi-, poiminta- tai myrkytyshyökkäyksiä.

---

### 10.1 Mallin kohdistus ja turvallisuus

Estä haitallisia tai sääntöjä rikkovia tuloksia.

 #10.1.1    Taso: 1    Rooli: D/V
 Varmista, että kohdistamisen testisarja (punaisen tiimin kehotteet, jailbreak-etsinnät, kielletty sisältö) on versionhallinnassa ja että sitä suoritetaan jokaisen mallin julkaisun yhteydessä.
 #10.1.2    Taso: 1    Rooli: D
 Varmista, että kieltäytyminen ja turvallisen täydennyksen turvakaiteet ovat käytössä.
 #10.1.3    Taso: 2    Rooli: D/V
 Varmista, että automatisoitu arvioija mittaa haitallisen sisällön osuuden ja merkitsee regressiot, jotka ylittävät asetetun kynnystason.
 #10.1.4    Taso: 2    Rooli: D
 Varmista, että vastajailbreak-koulutus on dokumentoitu ja toistettavissa.
 #10.1.5    Taso: 3    Rooli: V
 Varmista, että muodolliset politiikan noudattamisen todisteet tai sertifioitu monitorointi kattavat kriittiset alueet.

---

### 10.2 Hyökkäysesimerkki-koventaminen

Lisää vastustuskykyä manipuloiduille syötteille. Robustin adversaarisen koulutuksen ja benchmark-pisteytyksen katsotaan olevan nykyisin paras käytäntö.

 #10.2.1    Taso: 1    Rooli: D
 Varmista, että projektivarastoissa on vihamieliseen koulutukseen liittyvät konfiguraatiot, joilla on toistettavat siemenet.
 #10.2.2    Taso: 2    Rooli: D/V
 Varmista, että vihamielisten esimerkkien havaitseminen laukaisee estohälytyksiä tuotantoputkistoissa.
 #10.2.4    Taso: 3    Rooli: V
 Varmista, että sertifioidun robustisuuden todistukset tai interval-rajojen todistukset kattavat ainakin tärkeimmät kriittiset luokat.
 #10.2.5    Taso: 3    Rooli: V
 Varmista, että regressiotestit käyttävät adaptiivisia hyökkäyksiä todentamaan, ettei mitattavaa robustisuuden heikkenemistä ole.

---

### 10.3 Jäsenyyden inferenssin torjunta

Rajoita kykyä päättää, oliko tietue koulutusdatassa. Differentiaalinen yksityisyys ja luottamusarvojen peittäminen ovat edelleen tunnetuimpia tehokkaita puolustuskeinoja.

 #10.3.1    Taso: 1    Rooli: D
 Varmista, että kyselykohtainen entropian regularisointi tai lämpötilasäätö vähentää liiallista varmuutta ennusteissa.
 #10.3.2    Taso: 2    Rooli: D
 Tarkista, että koulutus käyttää ε-sidottua differentiaalisen yksityisyyden suojaa optimointia herkille tietoaineistoille.
 #10.3.3    Taso: 2    Rooli: V
 Tarkista, että hyökkäyssimulaatiot (shadow-model tai black-box) osoittavat hyökkäyksen AUC-arvon enintään 0.60 testidatalla.

---

### 10.4 Mallin inversio-hyökkäysten vastustuskyky

Estä yksityisten ominaisuuksien rekonstruointi. Äskettäiset katsaukset korostavat tulostuksen rajaamista ja DP-takuita käytännön puolustuskeinoin.

 #10.4.1    Taso: 1    Rooli: D
 Varmista, että arkaluonteiset attribuutit eivät koskaan tulostu suoraan; tarvittaessa käytä bucketteja tai yksisuuntaisia muunnoksia.
 #10.4.2    Taso: 1    Rooli: D/V
 Varmista, että kyselynopeusrajoitukset rajoittavat samalta käyttäjältä toistuvia adaptiivisia kyselyitä.
 #10.4.3    Taso: 2    Rooli: D
 Varmista, että malli on koulutettu yksityisyyttä suojaavalla melulla.

---

### 10.5 Mallinpoiminnan puolustus

Tunnista ja torju luvattoman kloonauksen. Vesileimaus ja kyselykuvioanalyysi ovat suositeltuja.

 #10.5.1    Taso: 1    Rooli: D
 Varmista, että inferenssiväylät noudattavat sekä globaaleja että jokaiselle API-avaimelle asetettuja nopeusrajoituksia, jotka on viritetty mallin muistamisen kynnyksen mukaan.
 #10.5.2    Taso: 2    Rooli: D/V
 Varmista, että kyselyentropia ja syötteen moninaisuustilastot syöttävät automaattisen poiminnan detektoriin.
 #10.5.3    Taso: 2    Rooli: V
 Varmista, että hauraat tai todennäköisyyspohjaiset vesileimat voidaan todistaa p < 0.01:n avulla ≤ 1 000 kyselyllä epäiltyä kloonia vastaan.
 #10.5.4    Taso: 3    Rooli: D
 Varmista, että vesileima-avaimet ja laukaisusarjat tallennetaan laitteistopohjaiseen turvallisuusmoduuliin ja vaihdetaan vuosittain.
 #10.5.5    Taso: 3    Rooli: V
 Varmista, että extraction-alert-tapahtumat sisältävät haitalliset kyselyt ja että ne ovat integroidut incident-response-playbookien kanssa.

---

### 10.6 Inferenssiaikana myrkytetyn datan havaitseminen

Tunnista ja neutraloi takaportilla varustetut tai myrkytetyt syötteet.

 #10.6.1    Taso: 1    Rooli: D
 Varmista, että syötteet kulkeutuvat poikkeavuustunnistimen läpi (esim. STRIP, yhtenäisyys-pisteytys) ennen mallin inferenssiä.
 #10.6.2    Taso: 1    Rooli: V
 Varmista, että detektorin kynnystasot on viritetty puhtaiden ja myrkytettyjen validointijoukkojen perusteella, jotta valepositiivisten osuus on alle 5 %.
 #10.6.3    Taso: 2    Rooli: D
 Varmista, että syötteet, jotka on merkitty myrkytetyiksi, laukaisevat soft-blocking ja ihmisen tarkistus työnkulut.
 #10.6.4    Taso: 2    Rooli: V
 Varmista, että detektorit rasitustestataan sopeutuvilla, laukaisimetömillä takaporttihyökkäyksillä.
 #10.6.5    Taso: 3    Rooli: D
 Varmista, että havaitsemisen tehokkuusmittarit kirjataan lokiin ja niitä arvioidaan säännöllisesti tuoreiden uhkatiedustelujen avulla.

---

### 10.7 Dynaaminen turvallisuuspolitiikan sopeutuminen

Reaaliaikaiset turvallisuuspolitiikan päivitykset uhkatiedustelun ja käyttäytymisanalyysin perusteella.

 #10.7.1    Taso: 1    Rooli: D/V
 Varmista, että turvallisuuspolitiikat voidaan päivittää dynaamisesti ilman agentin uudelleenkäynnistystä, samalla säilyttäen politiikkaversioiden eheys.
 #10.7.2    Taso: 2    Rooli: D/V
 Varmista, että politiikan päivitykset ovat kryptografisesti allekirjoitettuja valtuutettujen turvallisuusammattilaisten toimesta ja ne vahvistetaan ennen käyttöönottoa.
 #10.7.3    Taso: 2    Rooli: D/V
 Varmista, että dynaamiset politiikan muutokset kirjataan täydellisillä auditointijäljillä, mukaan lukien perustelut, hyväksyntäketjut ja palautusmenettelyt.
 #10.7.4    Taso: 3    Rooli: D/V
 Varmista, että adaptiiviset turvallisuusmekanismit säätävät uhkien havaitsemisen herkkyyttä riskikontekstin ja käyttäytymismallien perusteella.
 #10.7.5    Taso: 3    Rooli: D/V
 Varmista, että politiikan mukautuspäätökset ovat selitettävissä ja että niihin sisältyvät todistejäljet turvallisuustiimin tarkastelua varten.

---

### 10.8 Reflektiopohjainen turvallisuusanalyysi

Turvallisuuden validointi agentin itse-reflektoinnin ja meta-cognitiivisen analyysin kautta.

 #10.8.1    Taso: 1    Rooli: D/V
 Varmista, että agentin reflektointimekanismit sisältävät turvallisuuteen keskittyvän omanarvioinnin päätöksistä ja toimista.
 #10.8.2    Taso: 2    Rooli: D/V
 Varmista, että reflektiotulokset validoidaan, jotta itsearviointimekanismien manipulointi estetään vihamielisillä syötteillä.
 #10.8.3    Taso: 2    Rooli: D/V
 Varmista, että metakognitiivinen turvallisuusanalyysi tunnistaa agentin päättelyprosesseihin liittyvän mahdollisen vinouden, manipuloinnin tai kompromission.
 #10.8.4    Taso: 3    Rooli: D/V
 Varmista, että reflektointiin perustuvat turvallisuusvaroitukset laukaisevat parannetun valvonnan ja mahdolliset ihmisen väliintuloa koskevat työnkulut.
 #10.8.5    Taso: 3    Rooli: D/V
 Varmista, että jatkuva oppiminen turvallisuusreflektoinneista parantaa uhkien havaitsemista ilman, että laillinen toiminnallisuus heikkenee.

---

### 10.9 Evoluutio ja itsekehityksen turvallisuus

Agenttijärjestelmien turvallisuusvalvontatoimet, jotka pystyvät itsemodifioitumaan ja kehittymään.

 #10.9.1    Taso: 1    Rooli: D/V
 Varmista, että itsemuokkauskyvyt rajoittuvat määrättyihin turvallisiin alueisiin muodollisten varmistusten rajoissa.
 #10.9.2    Taso: 2    Rooli: D/V
 Varmista, että kehitysehdotukset käyvät läpi turvallisuusvaikutusten arvioinnin ennen toteutusta.
 #10.9.3    Taso: 2    Rooli: D/V
 Varmista, että itseparannusmekanismit sisältävät palautusominaisuudet eheydenvarmistuksella.
 #10.9.4    Taso: 3    Rooli: D/V
 Varmista, että meta-oppimisen turvallisuus estää parannusalgoritmeihin kohdistuvan hyökkäysperusteisen manipuloinnin.
 #10.9.5    Taso: 3    Rooli: D/V
 Varmista, että rekursiivinen itseparantuminen on rajattu muodollisten turvallisuusrajoitteiden puitteissa ja että konvergenssi on todistettu matemaattisesti.

---

#### Lähteet

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

## 11 Tietosuoja ja henkilötietojen hallinta

### Kontrollitavoite

Pidä tiukat yksityisyyden takeet koko tekoälyelinkaaren aikana—keruusta, koulutuksesta, inferenssistä ja tapahtumien käsittelystä—siten, että henkilötietoja käsitellään vain selkeän suostumuksen perusteella, mahdollisimman pienellä välttämättömällä laajuudella, todistettavalla poistamisella ja muodollisilla yksityisyyden takeilla.

---

### 11.1 Anonymisointi ja tietojen minimointi

 #11.1.1    Taso: 1    Rooli: D/V
 Varmista, että suorat tunnisteet ja kvasi-identifikaattorit on poistettu ja hashattu.
 #11.1.2    Taso: 2    Rooli: D/V
 Varmista, että automatisoidut auditoinnit mittaavat k-anonymiteetin ja l-diversiteetin, ja hälyttävät, kun kynnysarvot laskevat alle politiikan asettamien arvojen.
 #11.1.3    Taso: 2    Rooli: V
 Varmista, että mallin ominaisuuksien tärkeysraportit osoittavat, ettei tunnistevuotoa ole yli ε = 0.01 mutual information tasolla.
 #11.1.4    Taso: 3    Rooli: V
 Varmista, että muodolliset todisteet tai synteettistä dataa koskeva sertifiointi osoittavat uudelleen-identifioinnin riskin ≤ 0.05 jopa linkityshyökkäysten aikana.

---

### 11.2 Oikeus tulla unohdetuksi ja poistamisen täytäntöönpano

 #11.2.1    Taso: 1    Rooli: D/V
 Varmista, että rekisteröityjen poistopyyntöjen leviäminen ulottuu raakadatasetteihin, tallennuspisteisiin, upotuksiin, lokitietoihin ja varmuuskopioihin palvelutasosopimusten mukaisesti alle 30 päivässä.
 #11.2.2    Taso: 2    Rooli: D
 Varmista, että "machine-unlearning" -rutiinit fyysisesti uudelleenkouluttavat tai arvioivat poistamisen toteutusta käyttämällä sertifioituja unlearning-algoritmeja.
 #11.2.3    Taso: 2    Rooli: V
 Tarkista, että varjomallin arviointi osoittaa unohtuneiden tietueiden vaikutuksen olevan alle 1 %:n tuloksista unohduksen jälkeen.
 #11.2.4    Taso: 3    Rooli: V
 Varmista, että poistotapahtumat kirjataan muuttumattomasti ja ovat auditoitavissa sääntelyviranomaisia varten.

---

### 11.3 Differentiaalisen yksityisyyden turvatoimet

 #11.3.1    Taso: 2    Rooli: D/V
 Varmista, että privacy-loss accounting -kojelautat varoittavat, kun kumulatiivinen ε ylittää politiikan kynnykset.
 #11.3.2    Taso: 2    Rooli: V
 Varmista, että mustan laatikon tietosuoja-auditoinnit arvioivat ε̂:n 10%:n sisällä ilmoitetusta arvosta.
 #11.3.3    Taso: 3    Rooli: V
 Tarkista, että formaalit todistukset kattavat kaikki koulutuksen jälkeiset hienosäädöt ja upotukset.

---

### 11.4 Tarkoituksen rajoittaminen ja laajuuden laajentumisen ehkäisy

 #11.4.1    Taso: 1    Rooli: D
 Varmista, että jokaisella datasettillä ja mallin tallennuspisteellä on koneellisesti luettava tarkoitustagi, joka on yhdenmukainen alkuperäisen suostumuksen kanssa.
 #11.4.2    Taso: 1    Rooli: D/V
 Varmista, että ajonaikaiset valvontajärjestelmät havaitsevat ilmoitetun tarkoituksen kanssa ristiriitaiset kyselyt ja laukaisevat pehmeän kieltäytymisen.
 #11.4.3    Taso: 3    Rooli: D
 Varmista, että policy-as-code-portit estävät mallien uudelleenkäyttöönoton uusiin alueisiin ilman DPIA-arviointia.
 #11.4.4    Taso: 3    Rooli: V
 Varmista, että muodolliset jäljittävyystodisteet osoittavat, että jokaisen henkilötiedon elinkaari pysyy suostumuksella määritellyn laajuuden sisällä.

---

### 11.5 Suostumuksen hallinta & lainmukaisten-perusteiden seuranta

 #11.5.1    Taso: 1    Rooli: D/V
 Varmista, että Suostumushallintajärjestelmä (CMP) tallentaa opt-in-tila, tarkoituksen ja säilytysajan kullekin tietosubjektille.
 #11.5.2    Taso: 2    Rooli: D
 Varmista, että API:t paljastavat suostumustokenit; malleilla on vahvistettava tokenin laajuus ennen inferenssia.
 #11.5.3    Taso: 2    Rooli: D/V
 Varmista, että hylätty tai peruutettu suostumus pysäyttää käsittelyputket 24 tunnin kuluessa.

---

### 11.6 Hajautettu oppiminen yksityisyydenhallintakeinojen kanssa

 #11.6.1    Taso: 1    Rooli: D
 Varmista, että asiakaspäivitykset käyttävät paikallisen differentiaalisen yksityisyyden melun lisäämistä ennen aggregointia.
 #11.6.2    Taso: 2    Rooli: D/V
 Varmista, että koulutuksen mittarit ovat differentiaalisen yksityisyyden suojaamia eikä ne koskaan paljasta yksittäisen asiakkaan tappioarvoa.
 #11.6.3    Taso: 2    Rooli: V
 Varmista, että myrkytysresistentti aggregointi (esim. Krum/Trimmed-Mean) on käytössä.
 #11.6.4    Taso: 3    Rooli: V
 Varmista, että muodolliset todistukset osoittavat kokonais-ε-budjetin, jossa hyötymenetys on alle 5.

---

#### Lähteet

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

## C12 Monitorointi, lokitus ja poikkeavuuksien havaitseminen

### Kontrollitavoite

Tämä osio määrittelee vaatimukset reaaliaikaisen ja forensisen näkyvyyden toteuttamiselle siihen, mitä malli ja muut tekoälykomponentit näkevät, tekevät ja palauttavat, jotta uhkia voidaan havaita, priorisoida ja niistä voidaan oppia.

### C12.1 Pyyntö- ja vastekirjaus

 #12.1.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki käyttäjän syötteet ja mallin vastaukset kirjataan asianmukaisilla metatiedoilla (esim. aikaleima, käyttäjä-ID, istunnon ID, mallin versio).
 #12.1.2    Taso: 1    Rooli: D/V
 Varmista, että lokit tallennetaan turvallisiin, pääsynvalvontaan rajoitettuihin varastoihin, joihin liittyvät asianmukaiset säilytyspolitiikat ja varmuuskopiointimenettelyt.
 #12.1.3    Taso: 1    Rooli: D/V
 Varmista, että lokien tallennusjärjestelmät käyttävät sekä levon että siirron salausmenetelmiä suojatakseen lokien sisältämää arkaluonteista tietoa.
 #12.1.4    Taso: 1    Rooli: D/V
 Varmista, että kehotteiden ja tulosteiden herkät tiedot on automaattisesti piilotettu tai peitetty ennen lokitusta, konfiguroitavissa olevien piilotussääntöjen avulla henkilötietojen, tunnistetietojen ja yrityksen omistaman tiedon suojaamiseksi.
 #12.1.5    Taso: 2    Rooli: D/V
 Varmista, että politiikkapäätökset ja turvallisuussuodatustoimenpiteet kirjataan riittävän yksityiskohtaisesti, jotta sisällön moderointijärjestelmien auditointi ja virheenkorjaus ovat mahdollisia.
 #12.1.6    Taso: 2    Rooli: D/V
 Varmista, että lokin eheys on turvattu esimerkiksi kryptografisilla allekirjoituksilla tai kirjoitusrajoitetulla tallennuksella.

---

### C12.2 Väärinkäytösten havaitseminen ja hälyttäminen

 #12.2.1    Taso: 1    Rooli: D/V
 Varmista, että järjestelmä havaitsee ja varoittaa tunnetuista jailbreak-malleista, kehotteen injektiokokeista ja vihamielisistä syötteistä käyttämällä allekirjoitusperusteista havaitsemista.
 #12.2.2    Taso: 1    Rooli: D/V
 Varmista, että järjestelmä integroituu olemassa olevien SIEM-alustojen kanssa käyttämällä standardeja lokimuotoja ja protokollia.
 #12.2.3    Taso: 2    Rooli: D/V
 Varmista, että rikastetut turvallisuustapahtumat sisältävät tekoälyyn liittyvää kontekstia, kuten mallien tunnisteet, todennäköisyysarvot ja turvallisuussuodattimen päätökset.
 #12.2.4    Taso: 2    Rooli: D/V
 Varmista, että käyttäytymisen poikkeavuuksien havaitsemisjärjestelmä tunnistaa epätavallisia keskustelukuvioita, liiallisia uusintayrityksiä tai järjestelmällisiä tiedustelukäyttäytymisiä.
 #12.2.5    Taso: 2    Rooli: D/V
 Varmista, että reaaliaikaiset hälytysjärjestelmät ilmoittavat turvallisuustiimille, kun havaitaan mahdolliset käytäntöjen rikkomukset tai hyökkäysyritykset.
 #12.2.6    Taso: 2    Rooli: D/V
 Varmista, että mukautetut säännöt sisältyvät tekoälyyn liittyvien uhkakuvioiden havaitsemiseen, mukaan lukien koordinoidut jailbreakyritykset, prompt injection kampanjat ja mallinpoistohyökkäykset.
 #12.2.7    Taso: 3    Rooli: D/V
 Varmista, että automatisoidut häiriötilanteisiin reagoivat työnkulut voivat eristää kompromettoituneet mallit, estää haitalliset käyttäjät ja eskaloida kriittisiä turvallisuustapahtumia.

---

### C12.3 Mallin driftin havaitseminen

 #12.3.1    Taso: 1    Rooli: D/V
 Varmista, että järjestelmä seuraa perussuorituskykymittareita, kuten tarkkuutta, luottamusarvoja, latenssia ja virheprosentteja malliversioiden ja aikajaksojen välillä.
 #12.3.2    Taso: 2    Rooli: D/V
 Varmista, että automatisoidut hälytykset laukaisevat, kun suorituskykymittarit ylittävät ennalta määritetyt heikentymisrajat tai poikkeavat merkittävästi viitearvoista.
 #12.3.3    Taso: 2    Rooli: D/V
 Varmista, että hallusinaatioiden havaitsemista varten tarkoitetut monitorit tunnistavat ja merkitsevät tilanteet, joissa mallin tuottama tieto on faktuaalisesti virheellistä, epäjohdonmukaista tai keksittyä.

---

### C12.4 Suorituskyvyn ja käyttäytymisen telemetria

 #12.4.1    Taso: 1    Rooli: D/V
 Varmista, että operatiiviset mittarit, kuten pyyntöviive, tokenien kulutus, muistin käyttö ja läpäisynopeus, kerätään ja seurataan jatkuvasti.
 #12.4.2    Taso: 1    Rooli: D/V
 Varmista, että menestys- ja epäonnistumisprosentit seurataan virhetyyppien ja niiden juurisyiden kategorisoinnilla.
 #12.4.3    Taso: 2    Rooli: D/V
 Varmista, että resurssien käytön seuranta sisältää GPU:n ja CPU:n käytön, muistin käytön ja tallennusvaatimukset sekä hälytykset, kun raja-arvot ylittyvät.

---

### C12.5 tekoälyn tapahtumavasteen suunnittelu ja toteutus

 #12.5.1    Taso: 1    Rooli: D/V
 Varmista, että tapahtumiin reagoimisen suunnitelmat ottavat erityisesti huomioon tekoälyyn liittyvät turvallisuustapahtumat, mukaan lukien mallin kompromissi, datan myrkyttäminen ja vastustajahyökkäykset.
 #12.5.2    Taso: 2    Rooli: D/V
 Varmista, että incident response-tiimeillä on pääsy AI-spesifisiin forensiikkatyökaluihin ja asiantuntemukseen mallin käyttäytymisen ja hyökkäysvektoreiden tutkimiseksi.
 #12.5.3    Taso: 3    Rooli: D/V
 Varmista, että tapahtuman jälkeinen analyysi sisältää mallin uudelleenkoulutuksen harkinnan, turvallisuussuodattimien päivitykset sekä opittujen kokemusten integroinnin turvallisuustoimenpiteisiin.

---

### C12.5 Tekoälyn suorituskyvyn heikkenemisen havaitseminen

Seuraa ja havaitse tekoälymallin suorituskyvyn ja laadun heikkenemistä ajan kuluessa.

 #12.5.1    Taso: 1    Rooli: D/V
 Varmista, että mallin tarkkuus, precision, recall ja F1-arvot ovat jatkuvassa seurannassa ja niitä verrataan peruskynnysarvoihin.
 #12.5.2    Taso: 1    Rooli: D/V
 Varmista, että datan poikkeaman havaitseminen seuraa syötteen jakauman muutoksia, jotka voivat vaikuttaa mallin suorituskykyyn.
 #12.5.3    Taso: 2    Rooli: D/V
 Varmista, että konseptimuutoksen havaitseminen tunnistaa syötteiden ja odotettujen tulosten välisen suhteen muutoksia.
 #12.5.4    Taso: 2    Rooli: D/V
 Varmista, että suorituskyvyn heikkeneminen laukaisee automaattiset hälytykset ja käynnistää mallin uudelleenkoulutuksen tai korvaavien työnkulkujen prosessit.
 #12.5.5    Taso: 3    Rooli: V
 Varmista, että heikentymisen juurisyiden analyysi korreloi suorituskyvyn heikkenemisen kanssa datamuutosten, infrastruktuuri-ongelmien tai ulkoisten tekijöiden kanssa.

---

### C12.6 DAG-visualisointi ja työnkulun turvallisuus

Suojaa työnkulun visualisointijärjestelmiä tiedon vuotumiselta ja manipulointihyökkäyksiltä.

 #12.6.1    Taso: 1    Rooli: D/V
 Varmista, että DAG-visuaatiotiedot on puhdistettu poistamaan arkaluontoiset tiedot ennen tallennusta tai siirtämistä.
 #12.6.2    Taso: 1    Rooli: D/V
 Varmista, että työnkulun visualisoinnin käyttöoikeuksien hallinta takaa, että vain valtuutetut käyttäjät voivat nähdä agentin päätöspolut ja päättelyn jäljet.
 #12.6.3    Taso: 2    Rooli: D/V
 Varmista, että DAG-tiedon eheys on suojattu kryptografisilla allekirjoituksilla ja muokkauksen havaitsemiseen tarkoitetuilla tallennusmekanismeilla.
 #12.6.4    Taso: 2    Rooli: D/V
 Varmista, että työnkulun visualisointijärjestelmät toteuttavat syötteen validoinnin estääkseen injektiohyökkäykset, joita muokatut solmu- tai kaaritiedot voivat aiheuttaa.
 #12.6.5    Taso: 3    Rooli: D/V
 Varmista, että reaaliaikaiset DAG-päivitykset ovat nopeusrajoitettuja ja vahvistettuja estämään palvelunestohyökkäyksiä visualisointijärjestelmissä.

---

### C12.7 Proaktiivinen turvallisuuskäyttäytymisen seuranta

Turvallisuusuhkien havaitseminen ja ehkäisy proaktiivisen agentin käyttäytymisanalyysin kautta.

 #12.7.1    Taso: 1    Rooli: D/V
 Varmista, että proaktiivisten agenttien käyttäytyminen on turvallisuusvarmennettu ennen suoritusta riskinarvioinnin integroinnin avulla.
 #12.7.2    Taso: 2    Rooli: D/V
 Varmista, että autonomisten aloitteiden laukaisimet sisältävät turvallisuuskontekstin arvioinnin ja uhkakuvan arvioinnin.
 #12.7.3    Taso: 2    Rooli: D/V
 Varmista, että proaktiiviset käyttäytymismallit analysoidaan mahdollisten turvallisuusvaikutusten ja tahattomien seurausten varalta.
 #12.7.4    Taso: 3    Rooli: D/V
 Varmista, että turvallisuuskriittiset proaktiiviset toimenpiteet vaativat nimenomaiset hyväksyntäketjut, joihin liittyy auditointijälkiä.
 #12.7.5    Taso: 3    Rooli: D/V
 Varmista, että käyttäytymisen poikkeavuuksien havaitseminen tunnistaa proaktiivisten agenttien toimintamalleissa ilmenevät poikkeavuudet, jotka voivat viitata kompromissiin.

---

### Lähteet

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Ihmisen valvonta, vastuullisuus ja hallinto

### Kontrollitavoite

Tämä luku määrittelee vaatimukset ihmisen valvonnan ylläpitämiseksi sekä selkeiden vastuuketjujen varmistamiseksi tekoälyjärjestelmissä, ja se varmistaa selitettävyyden, läpinäkyvyyden sekä eettisen hallinnan koko tekoälyn elinkaaren ajan.

---

### C13.1 Sammutus-katkaisija ja ohitusmekanismit

Tarjoa sammuttamis- ja palautuspolut, kun tekoälyjärjestelmän turvallisuusriskiä aiheuttava käyttäytyminen havaitaan.

 #13.1.1    Taso: 1    Rooli: D/V
 Varmista, että manuaalinen tappokytkinmekanismi on olemassa ja että se pysäyttää välittömästi AI-mallin inferenssin ja sen tuottamat tulosteet.
 #13.1.2    Taso: 1    Rooli: D
 Varmista, että ohituskontrollit ovat ainoastaan valtuutettujen henkilöstön käytettävissä.
 #13.1.3    Taso: 3    Rooli: D/V
 Varmista, että palautusmenettelyt voivat palauttaa aiemmat malliversiot tai toimia turvallisessa tilassa.
 #13.1.4    Taso: 3    Rooli: V
 Varmista, että ohitusmekanismit testataan säännöllisesti.

---

### C13.2 Ihmisen mukana prosessissa päätösten tarkistuspaikat

Vaatikaa ihmisten hyväksyntöjä, kun panokset ylittävät ennalta määritellyt riskirajat.

 #13.2.1    Taso: 1    Rooli: D/V
 Tarkista, että korkean riskin tekoälypäätökset edellyttävät ihmisen nimenomaista hyväksyntää ennen toteutusta.
 #13.2.2    Taso: 1    Rooli: D
 Varmista, että riskirajat on määritelty selkeästi ja että ne automaattisesti käynnistävät ihmisten tarkastusprosessit.
 #13.2.3    Taso: 2    Rooli: D
 Varmista, että aikakriittisissä päätöksissä on varajärjestelyjä, kun ihmisen hyväksyntää ei saada vaadituissa aikarajoissa.
 #13.2.4    Taso: 3    Rooli: D/V
 Varmista, että eskalointimenettelyt määrittelevät selkeät valtuudet eri päätöstyypeille tai riskiluokille, mikäli sovellettavissa on.

---

### C13.3 Vastuun ketju ja auditointi

Kirjaa operaattorin toimet ja mallin päätökset.

 #13.3.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki tekoälyjärjestelmien päätökset ja ihmisten väliintulot kirjataan aikaleimoilla, käyttäjäidentiteeteillä ja päätöksen perusteilla.
 #13.3.2    Taso: 2    Rooli: D
 Varmista, että auditlokit eivät ole muokattavissa ja että niihin on sisällytetty eheysvarmennusmekanismit.

---

### C13.4 Selitettävä-AI Tekniikat

Pintaominaisuuksien tärkeys, counter-factuals, ja paikalliset selitykset.

 #13.4.1    Taso: 1    Rooli: D/V
 Varmista, että tekoälyjärjestelmät antavat päätöksilleen perusselitykset ihmisluettavassa muodossa.
 #13.4.2    Taso: 2    Rooli: V
 Varmista, että selityksen laatu on validoitu inhimillisten arviointitutkimusten ja mittareiden kautta.
 #13.4.3    Taso: 3    Rooli: D/V
 Varmista, että ominaisuuksien tärkeysarvot tai attribuutiomenetelmät (SHAP, LIME jne.) ovat saatavilla kriittisille päätöksille.
 #13.4.4    Taso: 3    Rooli: V
 Varmista, että counterfactual-selitykset osoittavat, miten syötteitä voitaisiin muuttaa, jotta lopputulokset muuttuisivat, jos se on sovellettavissa käyttötapaukseen ja alaan.

---

### C13.5 Mallikortit ja käyttöilmoitukset

Pidä yllä mallikortteja aiotun käytön, suorituskykymittareiden ja eettisten näkökohtien varalta.

 #13.5.1    Taso: 1    Rooli: D
 Varmista, että mallikortit dokumentoivat tarkoitetut käyttötapaukset, rajoitukset ja tunnetut vika- tai epäonnistumistavat.
 #13.5.2    Taso: 1    Rooli: D/V
 Varmista, että suorituskykymittarit on julkaistu eri soveltuvien käyttötapausten osalta.
 #13.5.3    Taso: 2    Rooli: D
 Varmista, että eettiset näkökulmat, vinouman arvioinnit, oikeudenmukaisuuden arvioinnit, koulutusdatan ominaisuudet sekä tunnetut koulutusdatan rajoitteet dokumentoidaan ja päivitetään säännöllisesti.
 #13.5.4    Taso: 2    Rooli: D/V
 Varmista, että mallikortit ovat versionhallinnassa ja niitä ylläpidetään koko mallin elinkaaren ajan muutosten seuraamisen avulla.

---

### C13.6 Epävarmuuden kvantifiointi

Välitä vastauksissa luottamusarvot tai entropiamittarit.

 #13.6.1    Taso: 1    Rooli: D
 Varmista, että tekoälyjärjestelmät tarjoavat luottamusarviot tai epävarmuusmittarit tuloksilleen.
 #13.6.2    Taso: 2    Rooli: D/V
 Varmista, että epävarmuuskynnysarvot saavat aikaan lisäarvioinnin tai vaihtoehtoisia päätöksentekopolkuja.
 #13.6.3    Taso: 2    Rooli: V
 Varmista, että epävarmuuden kvantifiointimenetelmät on kalibroitu ja validoitu ground truth dataa vastaan.
 #13.6.4    Taso: 3    Rooli: D/V
 Tarkista, että epävarmuuden leviäminen säilyy monivaiheisten tekoälytyöprosessien aikana.

---

### C13.7 Käyttäjille suunnatut läpinäkyvyysraportit

Tarjoa säännöllisiä paljastuksia tapahtumista, driftistä ja datan käytöstä.

 #13.7.1    Taso: 1    Rooli: D/V
 Varmista, että tietojen käytön politiikat ja käyttäjien suostumuksen hallintaan liittyvät käytännöt viestitään sidosryhmille selkeästi.
 #13.7.2    Taso: 2    Rooli: D/V
 Varmista, että tekoälyn vaikutusarvioinnit ovat tehty ja tulokset sisällytetään raportointiin.
 #13.7.3    Taso: 2    Rooli: D/V
 Varmista, että säännöllisesti julkaistut läpinäkyvyysraportit paljastavat tekoälyyn liittyvät tapahtumat ja toiminnalliset mittarit kohtuullisen yksityiskohtaisesti.

#### Lähteet

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

## Liite A: Sanasto

Tämä kattava sanasto sisältää AISVS:ssä käytettyjen keskeisten tekoäly-, koneoppimisen ja turvallisuus-termien määritelmiä varmistaen selkeyden ja yhteisen ymmärryksen.

Vihamielinen esimerkki: syöte, joka on tarkoituksella laadittu saattamaan tekoälymallin tekemään virheen, usein lisäämällä ihmisten havaittamattomia hienovaraisia perturbaatioita.
​
Hyökkäyskestävyys – Tekoälyssä se tarkoittaa mallin kykyä säilyttää suorituskykynsä ja torjua tarkoituksella suunniteltuja, pahantahtoisia syötteitä, joiden tavoitteena on aiheuttaa virheitä.
​
Agentti – AI-agentit ovat ohjelmistojärjestelmiä, jotka käyttävät tekoälyä tavoitteiden saavuttamiseen ja tehtävien suorittamiseen käyttäjien puolesta. Ne osoittavat päättelyä, suunnittelua ja muistia, ja niillä on autonomia tehdä päätöksiä, oppia ja sopeutua.
​
Agenttinen tekoäly: tekoälyjärjestelmät, jotka voivat toimia jonkin asteisen autonomian avulla tavoitteiden saavuttamiseksi, ja jotka usein tekevät päätöksiä sekä ryhtyvät toimiin ilman suoraa ihmisen puuttumista.
​
Attribuutteihin perustuva pääsynvalvonta (ABAC): pääsynvalvontamalli, jossa valtuutuspäätökset perustuvat käyttäjän, resurssin, toiminnon ja ympäristön attribuuteihin, arvioidaan kyselyaikana.
​
Takaporttihyökkäys: eräänlainen datan myrkytyshyökkäyksen tyyppi, jossa malli opetetaan vastaamaan tietyllä tavalla joillekin laukaisimille, kun se muuten käyttäytyy normaalisti.
​
Vinouma: Järjestelmälliset virheet tekoälymallin tuloksissa, jotka voivat johtaa epäoikeudenmukaisiin tai syrjiviin lopputuloksiin tietyille ryhmille tai tietyissä konteksteissa.
​
Vinouksien hyödyntäminen: Hyökkäystekniikka, joka hyödyntää tekoälymallien tunnettuja vinouksia manipuloidakseen tuloksia tai lopputuloksia.
​
Cedar: Amazonin politiikkakieli ja moottori hienorakeisten käyttöoikeuksien toteuttamiseen ABACin tekoälyjärjestelmissä.
​
Ajatteluketju: Tekniikka, jolla parannetaan kielimallien päättelykykyä tuottamalla välivaiheita ennen lopullisen vastauksen antamista.
​
Katkaisijat: Mekanismit, jotka pysäyttävät tekoälyjärjestelmän toiminnot automaattisesti, kun tietyt riskirajat ylittyvät.
​
Tietovuoto: arkaluonteisten tietojen tahattomasta paljastumisesta AI-mallin tulosteiden tai käyttäytymisen kautta.
​
Datan myrkyttäminen: Koulutusdatan tahallinen vääristely mallin eheyden vaarantamiseksi, usein takaporttien asentamiseen tai suorituskyvyn heikentämiseen.
​
Differentiaalinen yksityisyys – Differentiaalinen yksityisyys on matemaattisesti tiukka kehys tilastollisen tiedon julkaisemiseksi tietoaineistoista samalla suojaten yksittäisten henkilöiden yksityisyyttä. Se mahdollistaa datan omistajan jakaa ryhmän yhdistetyt piirteet samalla rajoittaen sitä, millaista tietoa yksittäisistä henkilöistä vuotaa.
​
Upotukset: Tiheät vektoriedustukset datasta (teksti, kuvat jne.), jotka kuvaavat semanttista merkitystä korkeidimensionaalisessa avaruudessa.
​
Selitettävyyys – Selitettävyyden tekoälyssä on kyky tarjota ihmisille ymmärrettäviä syitä sen päätöksille ja ennusteille, tarjoten näkemyksiä sen sisäisestä toiminnasta.
​
Selitettävä tekoäly (XAI): tekoälyjärjestelmät, jotka on suunniteltu tarjoamaan ihmisille ymmärrettäviä selityksiä niiden päätöksistä ja käyttäytymisestään erilaisten tekniikoiden ja kehyksien kautta.
​
Federated Learning: koneoppimisen lähestymistapa, jossa mallit koulutetaan useiden hajautettujen laitteiden kautta, joilla on paikalliset datanäytteet, ilman että dataa vaihdetaan keskenään.
​
Turvakaiteet: AI-järjestelmien haitallisten, puolueellisten tai muuten epätoivottujen tulosten syntymisen estämiseksi toteutetut rajoitteet.
​
Hallusinaatio – tekoälyhallusinaatio viittaa ilmiöön, jossa tekoälymalli tuottaa virheellistä tai harhaanjohtavaa tietoa, joka ei perustu sen koulutusdataan tai todelliseen faktaan.
​
Ihmisen ohjaama silmukka (HITL): Järjestelmät, jotka on suunniteltu vaatimaan ihmisen valvontaa, varmistusta tai puuttumista kriittisissä päätöksentekopisteissä.
​
Infrastruktuuri koodina (IaC): Infrastruktuurin hallinta ja provisionointi koodin kautta manuaalisten prosessien sijaan, mahdollistaa turvallisuusskannauksen ja johdonmukaiset käyttöönotot.
​
Jailbreak: Tekniikat, joita käytetään kiertämään tekoälyjärjestelmien turvakaiteita, erityisesti suurissa kielimalleissa, jotta voidaan tuottaa kiellettyä sisältöä.
​
Oikeuksien minimoinnin periaate: Turvallisuusperiaate, jossa annetaan vain käyttäjille ja prosesseille tarvittavat minimioikeudet.
​
LIME (Local Interpretable Model-agnostic Explanations): Tekniikka, jolla selitetään minkä tahansa koneoppimisluokittelijan ennusteet lähentämällä sen paikallisesti tulkittavalla mallilla.
​
Jäsenyyden inferenssihyökkäys: hyökkäys, jonka tavoitteena on selvittää, käytettiinkö tietty datapiste kouluttamaan koneoppimismallia.
​
MITRE ATLAS: Vastustajien uhkakartta tekoälyjärjestelmille; tietopankki vastustajien taktiikoista ja tekniikoista tekoälyjärjestelmiä vastaan.
​
Mallikortti – Mallikortti on dokumentti, joka tarjoaa standardoitua tietoa tekoälymallin suorituskyvystä, rajoitteista, käyttötarkoituksista sekä eettisistä näkökohdista läpinäkyvyyden ja vastuullisen tekoälyn kehityksen edistämiseksi.
​
Mallin poimintahyökkäys: Hyökkäys, jossa hyökkääjä toistuvasti tekee kyselyitä kohdemallille luodakseen toiminnallisesti samankaltaisen kopion ilman valtuutusta.
​
Mallin inversiohyökkäys: hyökkäys, jonka tarkoituksena on rekonstruoida koulutusdata analysoimalla mallin tuottamia tuloksia.
​
Model Lifecycle Management – Tekoälymallin elinkaaren hallinta on prosessi, jossa valvotaan kaikkia tekoälymallin olemassaolon vaiheita, mukaan lukien sen suunnittelu, kehittäminen, käyttöönotto, seuranta, ylläpito ja lopullinen eläköityminen, jotta se pysyy tehokkaana ja tavoitteisiin nähden linjassa.
​
Mallin myrkyttäminen: Haavoittuvuuksien tai takaporttien lisääminen suoraan malliin koulutusprosessin aikana.
​
Mallin varastaminen/varkaus: Toistuvien kyselyjen kautta omistetun mallin kopion tai likimääräisen version hankkiminen.
​
Moni-agenttijärjestelmä: Järjestelmä, joka koostuu useista vuorovaikutteisista tekoälyagentteista, joilla on mahdollisesti erilaiset kyvykkyydet ja tavoitteet.
​
OPA (Open Policy Agent): avoimen lähdekoodin politiikan moottori, joka mahdollistaa yhtenäisen politiikan täytäntöönpanon koko pinon läpi.
​
Yksityisyyttä suojaava koneoppiminen (PPML): Tekniikat ja menetelmät, joilla koulutetaan ja otetaan käyttöön ML-malleja samalla kun suojataan koulutusdatan yksityisyyttä.
​
Kehote-injektio: Hyökkäys, jossa haitalliset ohjeet upotetaan syötteisiin, jotta mallin suunniteltu käyttäytyminen ohitetaan.
​
RAG (Retrieval-Augmented Generation): Tekniikka, joka parantaa suuria kielimalleja hakemalla olennaista tietoa ulkoisista tietolähteistä ennen vastauksen tuottamista.
​
Punaisen tiimin testaus: Aktiivisen testaamisen käytäntö tekoälyjärjestelmille simuloimalla vihamielisiä hyökkäyksiä haavoittuvuuksien tunnistamiseksi.
​
SBOM (Software Bill of Materials): Virallinen rekisteri, joka sisältää ohjelmiston tai tekoälymallien rakentamiseen käytettyjen erilaisten komponenttien yksityiskohdat ja toimitusketjun suhteet.
​
SHAP (SHapley Additive exPlanations): Peliteoreettinen lähestymistapa selittää minkä tahansa koneoppimismallin tuloksen laskemalla kunkin ominaisuuden panoksen ennusteeseen.
​
Toimitusketjuhyökkäys: Järjestelmän vahingoittaminen kohdistamalla toimitusketjun heikosti suojattuihin osiin, kuten kolmansien osapuolien kirjastoihin, datasetteihin tai esikoulutetuihin malleihin.
​
Siirtäminen oppimiseen: Tekniikka, jossa yhdelle tehtävälle kehitettyä mallia käytetään lähtökohtana toisen tehtävän mallille.
​
Vektoritietokanta: Erityisesti korkeidimensionaalisten vektoreiden (upotukset) tallentamiseen suunniteltu tietokanta sekä tehokkaiden samankaltaisuushakujen suorittaminen.
​
Haavoittuvuusskannaus: Automaattiset työkalut, jotka tunnistavat tunnettuja turvallisuushaavoittuvuuksia ohjelmistokomponenteissa, mukaan lukien tekoälykehykset ja riippuvuudet.
​
Vesileimaus: Tekniikat, joilla tekoälyn luomalle sisällölle upotetaan huomaamattomia merkkejä sen alkuperän seuraamiseksi tai tekoälyn tuottaman sisällön havaitsemiseksi.
​
Nollapäivähaavoittuvuus: aiemmin tuntematon haavoittuvuus, jota hyökkääjät voivat hyödyntää ennen kuin kehittäjät luovat ja ottavat käyttöön paikkauksen.

## Liite B: Viitteet

### TODO

## Liite C: Tekoälyn turvallisuuden hallinto ja dokumentaatio

### Tavoite

Tämä liite tarjoaa perustavaa laatua olevia vaatimuksia organisaatiorakenteiden, politiikkojen ja prosessien perustamiseen tekoälyn turvallisuuden hallinnan varmistamiseksi koko järjestelmän elinkaaren ajan.

---

### AC.1 AI-riskienhallintakehyksen käyttöönotto

Tarjoa muodollinen kehys tekoälyyn liittyvien riskien tunnistamiseen, arviointiin ja lieventämiseen koko järjestelmän elinkaaren ajan.

 #AC.1.1    Taso: 1    Rooli: D/V
 Varmista, että tekoäly-kohtainen riskinarviointimetodologia on dokumentoitu ja otettu käyttöön.
 #AC.1.2    Taso: 2    Rooli: D
 Varmista, että riskinarvioinnit suoritetaan tekoälyn elinkaaren keskeisissä vaiheissa ja ennen merkittäviä muutoksia.
 #AC.1.3    Taso: 3    Rooli: D/V
 Varmista, että riskienhallintakehys on vakiintuneiden standardien mukainen (esim. NIST AI RMF).

---

### AC.2 Tekoälyn tietoturvapolitiikka ja menettelyt

Määrittele ja valvo organisaation turvallisen tekoälyn kehittämisen, käyttöönoton ja toiminnan standardeja.

 #AC.2.1    Taso: 1    Rooli: D/V
 Varmista, että dokumentoidut tekoälyn tietoturvapolitiikat ovat olemassa.
 #AC.2.2    Taso: 2    Rooli: D
 Varmista, että politiikat tarkistetaan ja päivitetään vähintään kerran vuodessa sekä merkittävien uhkakentän muutosten jälkeen.
 #AC.2.3    Taso: 3    Rooli: D/V
 Varmista, että politiikat kattavat kaikki AISVS-kategoriat ja sovellettavat sääntelyvaatimukset.

---

### AC.3 Roolit ja vastuut tekoälyturvallisuudessa

Aseta selkeä vastuu tekoälyn turvallisuudesta koko organisaatiossa.

 #AC.3.1    Taso: 1    Rooli: D/V
 Varmista, että tekoälyn turvallisuusroolit ja vastuut ovat dokumentoidut.
 #AC.3.2    Taso: 2    Rooli: D
 Varmista, että vastuulliset henkilöt omaavat asianmukaisen turvallisuusosaamisen.
 #AC.3.3    Taso: 3    Rooli: D/V
 Varmista, että korkean riskin tekoälyjärjestelmiä varten on perustettu tekoälyn etiikan komitea tai hallintoneuvosto.

---

### AC.4 Eettisten tekoälyohjeiden noudattamisen valvonta

Varmista, että tekoälyjärjestelmät toimivat vakiintuneiden eettisten periaatteiden mukaisesti.

 #AC.4.1    Taso: 1    Rooli: D/V
 Varmista, että tekoälyn kehittämistä ja käyttöönottoa koskevat eettiset ohjeet ovat olemassa.
 #AC.4.2    Taso: 2    Rooli: D
 Varmista, että eettisten loukkauksien havaitsemiseen ja raportoimiseen on olemassa mekanismeja.
 #AC.4.3    Taso: 3    Rooli: D/V
 Varmista, että käytössä olevien tekoälyjärjestelmien säännölliset eettiset arvioinnit suoritetaan.

---

### AC.5 AI-lainsäädäntöön liittyvän noudattamisen valvonta

Pysy ajan tasalla kehittyvistä tekoälyä koskevista säännöksistä ja noudata niitä.

 #AC.5.1    Taso: 1    Rooli: D/V
 Varmista, että on olemassa prosesseja, joiden avulla tunnistetaan sovellettavat tekoälysäännökset.
 #AC.5.2    Taso: 2    Rooli: D
 Varmista, että kaikkien sääntelyvaatimusten noudattaminen arvioidaan.
 #AC.5.3    Taso: 3    Rooli: D/V
 Varmista, että sääntelymuutokset laukaisevat ajantasaiset tarkastukset ja päivitykset tekoälyjärjestelmiin.

### AC.6 Koulutusdatan hallinta, dokumentointi ja prosessi

 #1.1.2    Taso: 1    Rooli: D/V
 Varmista, että sallittuja ovat ainoastaan laadun, edustavuuden, eettisen hankinnan ja lisenssien noudattamisen suhteen tarkastetut aineistot, ja näin vähennetään tiedon myrkytyksen, sisäänrakennetun vinouden ja immateriaalioikeuksien loukkauksien riskejä.
 #1.1.5    Taso: 2    Rooli: D/V
 Varmista, että merkintä-/annotointilaatu varmistuu joko arvioijien ristiintarkastusten kautta tai konsensuksella.
 #1.1.6    Taso: 2    Rooli: D/V
 Varmista, että merkittäville koulutusdatoille pidetään yllä "data cards" tai "datasheets for datasets" -dokumentteja, joissa eritellään ominaisuudet, motivaatiot, koostumus, keruuprosessit, esikäsittely sekä suositellut/kielletyt käyttötarkoitukset.
 #1.3.2    Taso: 2    Rooli: D/V
 Varmista, että tunnistetut vinoumat on lievitetty dokumentoitujen strategioiden avulla, kuten tasapainottaminen, kohdennettu datan augmentointi, algoritmisiin säätöihin liittyvät toimenpiteet (esim. esikäsittely, käsittelyn aikaiset ja jälkikäsittelytekniikat) tai uudelleen painottaminen, ja lievityksen vaikutus sekä tasapuolisuuteen että kokonaismallin suorituskykyyn arvioidaan.
 #1.3.3    Taso: 2    Rooli: D/V
 Varmista, että koulutuksen jälkeiset oikeudenmukaisuusmittarit arvioidaan ja dokumentoidaan.
 #1.3.4    Taso: 3    Rooli: D/V
 Varmista, että elinkaaren biasinhallintapolitiikka määrittää omistajat ja arvioinnin tiheyden.
 #1.4.1    Taso: 2    Rooli: D/V
 Varmista, että merkintöjen/annotoinnin laatu varmistetaan selkeiden ohjeiden, arvioijien välisten tarkastusten, konsensusmekanismien (esim. annotaattorien välisen konsensuksen seuranta) sekä erimielisyyksien ratkaisemiseksi määriteltyjen prosessien avulla.
 #1.4.4    Taso: 3    Rooli: D/V
 Varmista, että turvallisuuteen, turvallisuuteen tai oikeudenmukaisuuteen liittyvät merkinnät saavat pakollisen itsenäisen kaksinkertaisen tarkastuksen tai vastaavan vankan varmistuksen.
 #1.4.6    Taso: 2    Rooli: D/V
 Varmista, että merkintäoppaat ja ohjeet ovat kattavia, versiohallinnassa olevia ja vertaisarvioituja.
 #1.4.6    Taso: 2    Rooli: D/V
 Varmista, että tunnisteiden tietomallit ovat selkeästi määriteltyjä ja versionhallinnassa.
 #1.3.1    Taso: 1    Rooli: D/V
 Varmista, että tietojoukot on profiloitu edustuksellisen epätasapainon ja mahdollisten vinoumien varalta lailla suojattujen ominaisuuksien osalta (esim. rotu, sukupuoli, ikä) sekä mallin sovellusalueen kannalta olennaisten muiden eettisesti herkkiä ominaisuuksien suhteen (esim. sosioekonominen asema, sijainti).
 #1.5.3    Taso: 2    Rooli: V
 Varmista, että alan asiantuntijoiden suorittamat manuaaliset spot-checkit kattavat tilastollisesti merkitsevän otoksen (esim. ≥1% tai 1,000 näytettä, kumpi tahansa suurempi, tai riskinarvioinnin mukaan määritetty) tunnistaakseen hienovaraiset laatuongelmat, joita automaatio ei havaitse.
 #1.8.4    Taso: 2    Rooli: D/V
 Varmista, että ulkoistetut tai yleisön osallistumiseen perustuvat merkintätyöprosessit sisältävät teknisiä ja menettelyllisiä turvatoimia, joilla varmistetaan tietojen luottamuksellisuus, eheys ja merkintöjen laatu sekä estetään tietovuoto.
 #1.5.4    Taso: 2    Rooli: D/V
 Varmista, että korjaavat toimenpiteet lisätään provenance-tietueisiin.
 #1.6.2    Taso: 2    Rooli: D/V
 Varmista, että liputetut näytteet käynnistävät manuaalisen tarkastuksen ennen koulutusta.
 #1.6.3    Taso: 2    Rooli: V
 Varmista, että tulokset syöttävät mallin turvallisuustiedostoon ja antavat tietoa käynnissä olevasta uhkatiedustelusta.
 #1.6.4    Taso: 3    Rooli: D/V
 Varmista, että tunnistuslogiikka päivitetään uusilla uhkatiedusteluilla.
 #1.6.5    Taso: 3    Rooli: D/V
 Varmista, että online-oppimisen putket seuraavat jakauman muutoksia.
 #1.7.1    Taso: 1    Rooli: D/V
 Varmista, että koulutusaineiston poistamisen työnkulut poistavat sekä alkuperäisen että johdetun datan ja arvioivat mallin vaikutuksen, sekä että vaikutus kyseisiin malleihin arvioidaan ja tarvittaessa käsitellään (esim. uudelleenkoulutuksella tai kalibroinnilla).
 #1.7.2    Taso: 2    Rooli: D
 Varmista, että käytössä on mekanismit, joilla seurataan ja kunnioitetaan käyttäjän suostumuksen (sekä sen peruutusten) laajuutta ja tilaa koulutuksessa käytetyn datan osalta, sekä että suostumus validoidaan ennen datan sisällyttämistä uusiin koulutusprosesseihin tai merkittäviin mallipäivityksiin.
 #1.7.3    Taso: 2    Rooli: V
 Varmista, että työnkulut testataan vuosittain ja kirjataan ylös.
 #1.8.1    Taso: 2    Rooli: D/V
 Varmista, että kolmannen osapuolen datatoimittajat, mukaan lukien esikoulutettujen mallien tarjoajat ja ulkoiset tietojoukot, käyvät läpi turvallisuus-, yksityisyyden-, eettisen hankinnan ja tietojen laadun due diligence-arvioinnit ennen kuin heidän tietonsa tai mallit integroidaan.
 #1.8.2    Taso: 1    Rooli: D
 Varmista, että ulkoiset siirrot käyttävät TLS-autentikointia ja eheyden tarkistuksia.
 #1.8.3    Taso: 2    Rooli: D/V
 Varmista, että korkean riskin datalähteet (esim. avoimen lähdekoodin aineistot, joiden alkuperä on tuntematon, tarkastamattomat toimittajat) saavat lisättyä tarkastelua, kuten hiekkalaatikkoympäristössä suoritettavaa analyysiä, laajat laadun ja vinouden tarkastukset sekä kohdennetun myrkytyksen havaitseminen ennen niiden käyttöä herkissä sovelluksissa.
 #1.8.4    Taso: 3    Rooli: D/V
 Varmista, että Varmista, että kolmansilta osapuolilta hankitut esikoulutetut mallit arvioidaan upotettujen vinouksien, mahdollisten takaporttien, arkkitehtuurin eheyden sekä alkuperäisen koulutusdatan alkuperän kannalta ennen hienosäätöä tai käyttöönottoa.
 #1.5.3    Taso: 2    Rooli: D/V
 Varmista, että jos adversaali koulutus käytössä on, adversaaliset datasetit ovat dokumentoituja ja kontrolloituja niiden generoinnin, hallinnan ja versionoinnin osalta.
 #1.5.3    Taso: 3    Rooli: D/V
 Varmista, että adversaarisen robustisuuden koulutuksen vaikutus mallin suorituskykyyn (sekä puhtaisiin että adversaarisiin syötteisiin) sekä oikeudenmukaisuusmittareihin on arvioitu, dokumentoitu ja seurattu.
 #1.5.4    Taso: 3    Rooli: D/V
 Varmista, että vihamieliseen koulutukseen ja robustisuuteen liittyvät strategiat tarkistetaan ja päivitetään säännöllisesti kehittyvien vihamielisten hyökkäystekniikoiden torjumiseksi.
 #1.4.2    Taso: 2    Rooli: D/V
 Varmista, että epäonnistuneet datasetit ovat karanteenissa ja niihin liittyvät audit-lokit ovat käytössä.
 #1.4.3    Taso: 2    Rooli: D/V
 Varmista, että laadunportit estävät huonolaatuiset tietoaineistot, ellei poikkeuksia ole hyväksytty.
 #1.11.2    Taso: 2    Rooli: D/V
 Varmista, että synteettisen datan generoinnin prosessi, sen parametrit ja käyttötarkoitus on dokumentoitu.
 #1.11.3    Taso: 2    Rooli: D/V
 Varmista, että synteettisen datan riskinarviointi on tehty epäoikeudenmukaisuuksien, yksityisyyden vuodon ja edustavuusongelmien varalta ennen sen käyttöä koulutuksessa.
 #1.12.3    Taso: 2    Rooli: D/V
 Varmista, että epäilyttävien pääsytapahtumien yhteydessä syntyy hälytyksiä ja ne tutkitaan ripeästi.
 #1.13.1    Taso: 1    Rooli: D/V
 Varmista, että kaikille koulutusdatoille on määritelty selkeät säilytysajat.
 #1.13.2    Taso: 2    Rooli: D/V
 Varmista, että tietojoukot vanhentuvat automaattisesti, poistetaan tai niiden poistoa harkitaan elinkaarensa lopussa.
 #1.13.3    Taso: 2    Rooli: D/V
 Varmista, että säilytys- ja poistotoimet ovat kirjattuja ja auditoitavissa.
 #1.14.1    Taso: 2    Rooli: D/V
 Varmista, että datan sijaintia koskevat vaatimukset sekä rajat ylittävien siirtojen vaatimukset on tunnistettu ja niihin on otettu käyttöön kaikissa tietojoukoissa.
 #1.14.2    Taso: 2    Rooli: D/V
 Varmista, että toimialakohtaiset säädökset (esim. terveydenhuolto, rahoitus) ovat tunnistettu ja niihin on puututtu datan käsittelyssä.
 #1.14.3    Taso: 2    Rooli: D/V
 Varmista, että asianmukaisten tietosuojalakien noudattaminen on dokumentoitu ja säännöllisesti tarkistettu (esim. GDPR, CCPA).
 #1.16.1    Taso: 2    Rooli: D/V
 Varmista, että on olemassa mekanismeja vastata rekisteröidyn pyyntöihin, jotka koskevat pääsyä omiin henkilötietoihinsa, oikaisua, käsittelyn rajoittamista tai vastustamista.
 #1.16.2    Taso: 2    Rooli: D/V
 Varmista, että pyynnöt kirjataan, seurataan ja täytetään lain vaatimien aikarajojen mukaisesti.
 #1.16.3    Taso: 2    Rooli: D/V
 Varmista, että rekisteröidyn oikeuksien käsittelyprosesseja testataan ja tarkastellaan säännöllisesti niiden tehokkuuden varmistamiseksi.
 #1.17.1    Taso: 2    Rooli: D/V
 Varmista, että vaikutusarviointi tehdään ennen datasetin version päivittämistä tai korvaamista, ja että se kattaa mallin suorituskyvyn, oikeudenmukaisuuden ja säädöstenmukaisuuden.
 #1.17.2    Taso: 2    Rooli: D/V
 Varmista, että vaikutusanalyysin tulokset on dokumentoitu ja ne on tarkastettu asianmukaisten sidosryhmien toimesta.
 #1.17.3    Taso: 2    Rooli: D/V
 Varmista, että palautussuunnitelmat ovat olemassa siltä varalta, että uudet versiot aiheuttavat hyväksymättömiä riskejä tai regressioita.
 #1.18.1    Taso: 2    Rooli: D/V
 Varmista, että kaikki datan annotointiin osallistuvat henkilöt ovat taustatarkastettuja ja koulutettuja tietoturvaan ja yksityisyyteen.
 #1.18.2    Taso: 2    Rooli: D/V
 Varmista, että kaikki annotointihenkilöstö allekirjoittavat luottamuksellisuus- ja salassapitovelvollisuussopimukset.
 #1.18.3    Taso: 2    Rooli: D/V
 Varmista, että annotointialustat noudattavat käyttöoikeuksien hallintaa ja valvovat sisäisiä uhkia.

#### Lähteet

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Liite D: AI-avusteinen turvallisen ohjelmoinnin hallinto ja verifiointi

### Tavoite

Tämä luku määrittelee perusorganisatoriset hallintatoimenpiteet tekoälyavusteisten koodausvälineiden turvalliseen ja tehokkaaseen käyttöön ohjelmistokehityksen aikana, varmistamalla turvallisuuden ja jäljitettävyyden koko SDLC:n ajan.

---

### AD.1 tekoäly-avusteinen turvallisen-koodauksen työnkulku

Integroi tekoälytyökalut organisaation turvallisen‑ohjelmistokehityksen elinkaareen (SSDLC) siten, ettei nykyisiä turvallisuusportteja heikennetä.

 #AD.1.1    Taso: 1    Rooli: D/V
 Varmista, että dokumentoitu työnkulku kuvaa milloin ja miten tekoälytyökalut voivat luoda, refaktoroida tai tarkastella koodia.
 #AD.1.2    Taso: 2    Rooli: D
 Varmista, että työnkulku vastaa kunkin SSDLC-vaiheen (suunnittelu, toteutus, koodikatselmointi, testaus, käyttöönotto).
 #AD.1.3    Taso: 3    Rooli: D/V
 Varmista, että mittarit (esim. haavoittuvuuksien tiheys, keskimääräinen havaitsemisaika) kerätään tekoälyn‑tuottamalle koodille ja verrataan ainoastaan ihmisillä tuotettuihin vertailuarvoihin.

---

### AD.2 AI-työkalun kelpuutus ja uhkamallinnus

Varmista, että tekoälykoodausvälineet arvioidaan turvallisuusominaisuuksien, riskin ja toimitusketjun vaikutuksen osalta ennen käyttöönottoa.

 #AD.2.1    Taso: 1    Rooli: D/V
 Varmista, että jokaisen tekoälytyökalun uhkamalli tunnistaa väärinkäytön, mallin inversio, tietovuodon ja riippuvuuksien ketjun riskit.
 #AD.2.2    Taso: 2    Rooli: D
 Varmista, että työkalujen arvioinnit sisältävät paikallisten komponenttien staattinen/dynaaminen analyysi ja SaaS-päätepisteiden arviointi (TLS, todentaminen/valtuutus, lokitus).
 #AD.2.3    Taso: 3    Rooli: D/V
 Varmista, että arvioinnit noudattavat tunnustettua viitekehystä ja ne suoritetaan uudelleen suurten pääversioiden jälkeen.

---

### AD.3 Turvallinen kehotteen ja kontekstinhallinta

Estä salaisuuksien, yrityksen omistaman koodin ja henkilötietojen vuotuminen, kun laadit kehotteita tai konteksteja tekoälymalleja varten.

 #AD.3.1    Taso: 1    Rooli: D/V
 Varmista, että kirjallinen ohjeistus kieltää salaisuuksien, tunnusten tai luokiteltujen tietojen lähettämisen kehotteissa.
 #AD.3.2    Taso: 2    Rooli: D
 Varmista, että tekniset kontrollit (asiakaspuoleinen redaktointi, hyväksytyt kontekstisuodattimet) poistavat automaattisesti herkät artefaktit.
 #AD.3.3    Taso: 3    Rooli: D/V
 Varmista, että syötteet ja vastaukset tokenisoidaan, siirron aikana ja levossa salataan, ja säilytysajat noudattavat tiedonluokittelupolitiikkaa.

---

### AD.4 Tekoälyn generoiman koodin validointi

Havaitse ja korjaa tekoälyn tuottamien tulosten aiheuttamat haavoittuvuudet ennen koodin yhdistämistä tai käyttöönottoa.

 #AD.4.1    Taso: 1    Rooli: D/V
 Varmista, että tekoälyn‑tuottama koodi käy aina läpi ihmisen koodikatselmoinnin.
 #AD.4.2    Taso: 2    Rooli: D
 Varmista, että automaattiset skannerit (SAST/IAST/DAST) suorittavat jokaisen vetopyynnön, joka sisältää AI‑generated koodia, ja estävät yhdistämisen kriittisten löydösten ilmetessä.
 #AD.4.3    Taso: 3    Rooli: D/V
 Varmista, että differentiaalinen fuzz-testaus tai ominaisuus-pohjaiset testit todistavat turvallisuuskriittisiä käyttäytymisiä (esim. syötteen validointi, valtuutuslogiikka).

---

### AD.5 Koodiehdotusten selittävyys ja jäljitettävyys

Tarjoa tilintarkastajille ja kehittäjille näkemys siitä, miksi ehdotus tehtiin ja miten se kehittyi.

 #AD.5.1    Taso: 1    Rooli: D/V
 Tarkista, että kehotus/vastausparit kirjataan commit-tunnisteilla.
 #AD.5.2    Taso: 2    Rooli: D
 Varmista, että kehittäjät voivat tuoda esiin mallin viitteet (koulutusnäytteet, dokumentaatio), jotka tukevat ehdotusta.
 #AD.5.3    Taso: 3    Rooli: D/V
 Varmista, että selittävyysraportit tallennetaan design-artefaktien yhteydessä ja viitataan turvallisuuskatsauksissa, täyttäen ISO/IEC 42001:n jäljitettävyyden periaatteet.

---

### AD.6 Jatkuva palaute & mallin hienosäätö

Paranna mallin turvallisuustasoa ajan mittaan samalla estäen negatiivisen harhaantumisen.

 #AD.6.1    Taso: 1    Rooli: D/V
 Varmista, että kehittäjät voivat merkitä turvattomia tai sääntöjen vastaisia ehdotuksia, ja että liput seurataan.
 #AD.6.2    Taso: 2    Rooli: D
 Varmista, että koottu palaute ohjaa säännöllistä fine‑tuningia tai retrieval‑augmented generationia hyväksyttyjen turvallisen koodauksen korpusten avulla (esim. OWASP Cheat Sheets).
 #AD.6.3    Taso: 3    Rooli: D/V
 Varmista, että suljetun silmukan arviointityökalu suorittaa regressiotestit jokaisen hienosäädön jälkeen; turvallisuusmittareiden on täytettävä tai ylitettävä aiemmat baseline-arvot ennen käyttöönottoa.

---

#### Lähteet

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Liite E: Esimerkkityökalut ja kehykset

### Tavoite

Tämä luku tarjoaa esimerkkejä työkaluista ja kehyksistä, jotka voivat tukea määrätyn AISVS-vaatimuksen toteuttamista tai täyttämistä. Näitä ei tule pitää AISVS-tiimin tai OWASP GenAI Security Projectin suosituksina tai hyväksyntöinä.

---

### AE.1 Koulutusdatan hallinta ja vinouman hallinta

Data-analytiikkaan, hallintoon ja vinouman hallintaan käytetyt työkalut.

 #AE.1.1    Osio: 1.1
 Datan inventaarion työkalut: Datan inventaarion hallintatyökalut kuten...
 #AE.1.2    Osio: 1.2
 Siirron aikainen salaus: Käytä TLS:ää HTTPS-pohjaisissa sovelluksissa, kuten OpenSSL ja Pythonin kanssa.`ssl` kirjsato?

---

### AE.2 Käyttäjän syötteen validointi

Käyttäjien syötteiden käsittelyyn ja validointiin tarkoitetut työkalut.

 #AE.2.1    Osio: 2.1
 Prompt Injection -torjuntatyökalut: Käytä guardrail-työkaluja, kuten NVIDIA:n NeMo tai Guardrails AI.

---

