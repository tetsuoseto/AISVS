## Etulehti

### Tietoa standardista

Artificial Intelligence Security Verification Standard (AISVS) on yhteisön ohjaama tietoturvavaatimusten luettelo, jota data-analyytikot, MLOps-insinöörit, ohjelmistoarkkitehdit, kehittäjät, testaajat, turvallisuusasiantuntijat, työkalujen toimittajat, sääntelijät ja käyttäjät voivat käyttää luodakseen, rakentaakseen, testatakseen ja varmistaakseen luotettavat tekoälyyn perustuvat järjestelmät ja sovellukset. Se tarjoaa yhteisen kielen tietoturvakontrollien määrittämiseksi tekoälyn elinkaaren eri vaiheissa—aineiston keruusta ja mallin kehityksestä aina käyttöönottoon ja jatkuvaan valvontaan—jotta organisaatiot voivat mitata ja parantaa tekoälyratkaisujensa kestävyyttä, yksityisyyttä ja turvallisuutta.

### Tekijänoikeus ja lisenssi

Versio 0.1 (Ensimmäinen julkinen luonnos - työn alla), 2025  

![license](images/license.png)
Tekijänoikeus © 2025 The AISVS Project.  

Julkaistu alla olevan Creative Commons Attribution‑ShareAlike 4.0 International License.
Minkä tahansa uudelleenkäytön tai jakelun yhteydessä sinun on selkeästi viestittävä tämän työn lisenssiehdot muille.

### Projektinjohtajat

Jim Manico
Aras “Russ” Memisyazici

### Tekijät ja tarkastajat

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS on täysin uusi standardi, joka on luotu erityisesti vastaamaan tekoälyjärjestelmien ainutlaatuisia turvallisuushaasteita. Vaikka se ammentaa inspiraatiota laajemmista turvallisuuden parhaista käytännöistä, jokainen AISVS:n vaatimus on kehitetty alusta alkaen heijastamaan tekoälyn uhkakenttää ja auttamaan organisaatioita rakentamaan turvallisempia, kestävämpiä tekoälyratkaisuja.

## Esipuhe

Tervetuloa tekoälyn turvallisuuden varmennusstandardiin (AISVS) versio 1.0!

### Johdanto

Vuonna 2025 perustettu AISVS määrittelee turvallisuusvaatimukset, jotka on otettava huomioon suunniteltaessa, kehittäessä, käyttöönotettaessa ja operoidessa moderneja tekoälymalleja, prosesseja ja tekoälyllä mahdollistettuja palveluja.

AISVS v1.0 edustaa projektinsa vetäjien, työryhmän ja laajemman yhteisön kontribuuttoreiden yhdistettyä työtä käytännöllisen ja testattavan perustason luomiseksi tekoälyjärjestelmien suojaamiseksi.

Tavoitteemme tämän julkaisun kanssa on tehdä AISVS:stä helppo ottaa käyttöön samalla kun pysymme tarkasti sen määritellyssä laajuudessa ja käsittelemme tekoälylle ominaista nopeasti kehittyvää riskimaisemaa.

### Keskeiset tavoitteet AISVS-versiolle 1.0

Versio 1.0 luodaan useiden ohjaavien periaatteiden pohjalta.

#### Selkeästi määritelty laajuus

Jokaisen vaatimuksen on oltava linjassa AISVS:n nimen ja tehtävän kanssa:

Tekoäly – Kontrollit toimivat AI/ML-kerroksella (data, malli, putki tai päättely) ja ne ovat tekoälyammattilaisten vastuulla.
Turvallisuus – Vaateet lieventävät suoraan tunnistettuja turvallisuus-, tietosuoja- tai turvallisuusriskejä.
Varmennus – Kieli on kirjoitettu siten, että vaatimustenmukaisuus voidaan objektiivisesti vahvistaa.
Standardi – Osiot noudattavat yhtenäistä rakennetta ja terminologiaa muodostamaan johdonmukaisen viitteen.
​
---

Noudattamalla AISVS:ää organisaatiot voivat järjestelmällisesti arvioida ja vahvistaa tekoälyratkaisujensa turvallisuusasemaa, edistäen turvallisen tekoälyinsinöörikulttuurin syntymistä.

## AISVS:n käyttäminen

Keinoälyn turvallisuusvarmennusstandardi (AISVS) määrittelee turvallisuusvaatimukset nykyaikaisille tekoälysovelluksille ja -palveluille, keskittyen sovelluskehittäjien hallinnassa oleviin näkökohtiin.

AISVS on tarkoitettu kaikille, jotka kehittävät tai arvioivat tekoälysovellusten turvallisuutta, mukaan lukien kehittäjät, arkkitehdit, tietoturva-asiantuntijat ja tarkastajat. Tämä luku esittelee AISVS:n rakenteen ja käytön, mukaan lukien sen varmistustasot ja suunnitellut käyttötapaukset.

### Tekoälyn turvallisuuden varmistuksen tasot

AISVS määrittelee kolme nousevaa turvallisuuden varmistustasoa. Jokainen taso lisää syvyyttä ja monimutkaisuutta, mikä mahdollistaa organisaatioiden mukauttaa turvallisuusasetuksensa AI-järjestelmiensä riskitasoon.

Organisaatiot voivat aloittaa tasolta 1 ja ottaa asteittain käyttöön korkeampia tasoja tietoturvan kypsyttyä ja uhkien lisääntyessä.

#### Tasoille määritelmä

Jokainen AISVS v1.0 -version vaatimus on määritelty yhteen seuraavista tasoista:

 Tason 1 vaatimukset

Taso 1 sisältää kriittisimmät ja perustavanlaatuisimmat tietoturvavaatimukset. Ne keskittyvät estämään yleisiä hyökkäyksiä, jotka eivät perustu muihin esiehtoihin tai haavoittuvuuksiin. Suurin osa tason 1 valvontatoimenpiteistä on joko helppoja toteuttaa tai riittävän tärkeitä vaivan oikeuttamiseksi.

 Taso 2 vaatimukset

Taso 2 käsittelee edistyneempiä tai harvinaisempia hyökkäyksiä sekä kerrostettuja puolustuksia laajalle levinneitä uhkia vastaan. Nämä vaatimukset voivat sisältää monimutkaisempaa logiikkaa tai kohdistua tiettyihin hyökkäysehtoon.

 Tason 3 vaatimukset

Taso 3 sisältää ohjauskeinoja, joiden toteuttaminen on tyypillisesti vaikeampaa tai jotka soveltuvat tilanteisiin. Ne edustavat usein syvyyspuolustuksen mekanismeja tai lieventäviä toimenpiteitä harvinaisia, kohdennettuja tai korkean monimutkaisuuden hyökkäyksiä vastaan.

#### Rooli (D/V)

Jokainen AISVS-vaatimus on merkitty ensisijaisen kohdeyleisön mukaan:

D – Kehittäjäkeskeiset vaatimukset
V – Varmennukseen/tarkastukseen keskittyvät vaatimukset
D/V – Tärkeä sekä kehittäjille että tarkistajille

## C1 Koulutusdatan hallinta ja harhan hallinta

### Ohjaustavoite

Koulutusdata on hankittava, käsiteltävä ja ylläpidettävä tavalla, joka säilyttää alkuperän, turvallisuuden, laadun ja oikeudenmukaisuuden. Näin täytetään lakisääteiset velvoitteet ja vähennetään vinouman, myrkytyksen tai tietosuojarikkomusten riskejä, jotka voivat ilmetä koulutuksen aikana ja vaikuttaa koko tekoälyn elinkaareen.

---

### C1.1 Koulutusdatan alkuperä

Pidä yllä todennettavissa olevaa luetteloa kaikista tietoaineistoista, hyväksy vain luotettavat lähteet ja kirjaa kaikki muutokset jäljitettävyyden varmistamiseksi.

 #1.1.1    Taso: 1    Rooli: D/V
 Varmista, että ajantasainen luettelo jokaisesta koulutusdatan lähteestä (alkuperä, vastuuhenkilö/omistaja, lisenssi, keräystapa, suunnitellut käyttörajoitukset ja käsittelyhistoria) pidetään yllä.
 #1.1.2    Taso: 1    Rooli: D/V
 Varmista, että koulutusdatan käsittelyprosessit poistavat tarpeettomat ominaisuudet, attribuutit tai kentät (esim. käyttämättömät metatiedot, arkaluonteiset henkilötunnistetiedot, vuotanut testidata).
 #1.1.3    Taso: 2    Rooli: D/V
 Varmista, että kaikki tietojoukkomuutokset kuuluvat kirjattuun hyväksymisprosessiin.
 #1.1.4    Taso: 3    Rooli: D/V
 Varmista, että tietoaineistot tai alijoukot on vesileimattu tai sormenjäljet merkitty, missä mahdollista.

---

### C1.2 Koulutusdatan turvallisuus ja eheys

Rajoita pääsy koulutusdataan, salaa se levossa ja siirron aikana ja varmista sen eheys estääksesi manipuloinnin, varkauden tai datan myrkytyksen.

 #1.2.1    Taso: 1    Rooli: D/V
 Varmista, että käyttöoikeuksien valvonta suojaa koulutusdatan tallennusta ja putkistoja.
 #1.2.2    Taso: 2    Rooli: D/V
 Varmista, että kaikki pääsy koulutusdataan kirjataan, mukaan lukien käyttäjä, aika ja toimenpide.
 #1.2.3    Taso: 2    Rooli: D/V
 Varmista, että koulutusaineistot ovat salattuja siirron aikana ja levossa, käyttämällä alan standardien mukaisia salausalgoritmeja ja avainhallintakäytäntöjä.
 #1.2.4    Taso: 2    Rooli: D/V
 Varmista, että kryptografisia tiivisteitä tai digitaalisia allekirjoituksia käytetään tiedon eheyttä varmistamaan harjoitusdatan tallennuksen ja siirron aikana.
 #1.2.5    Taso: 2    Rooli: D/V
 Varmista, että automatisoituja tunnistustekniikoita käytetään estämään luvattomat muutokset tai koulutusdatan vahingoittuminen.
 #1.2.6    Taso: 2    Rooli: D/V
 Varmista, että vanhentuneet koulutusaineistot poistetaan turvallisesti tai anonymisoidaan.
 #1.2.7    Taso: 3    Rooli: D/V
 Varmista, että kaikki koulutusdatan versiot on yksilöity, tallennettu muuttumattomasti ja auditoitavissa tukemaan palautusta ja rikosteknistä analyysiä.

---

### C1.3 Koulutusdatan merkintöjen laatu, eheys ja turvallisuus

Suojaa tunnisteet ja vaadi tekninen tarkastus kriittisille tiedoille.

 #1.3.1    Taso: 2    Rooli: D/V
 Varmista, että kryptografisia hajautusarvoja tai digitaalisia allekirjoituksia käytetään tunnistemateriaaleihin niiden eheyden ja aitouden varmistamiseksi.
 #1.3.2    Taso: 2    Rooli: D/V
 Varmista, että merkintäkäyttöliittymät ja -alustat toteuttavat vahvat käyttöoikeuksien hallintamekanismit, ylläpitävät manipulointia estäviä tarkastuslokeja kaikista merkintätoiminnoista ja suojaavat luvattomalta muokkaamiselta.
 #1.3.3    Taso: 3    Rooli: D/V
 Varmista, että arkaluonteiset tiedot tunnisteissa on poistettu, anonymisoitu tai salattu tietokenttätasolla sekä levossa että siirrossa.

---

### C1.4 Koulutusdatan laatu- ja turvallisuusvarmennus

Yhdistä automatisoitu validointi, manuaaliset pistotarkastukset ja kirjattu korjaustoimenpide varmistaaksesi aineiston luotettavuuden.

 #1.4.1    Taso: 1    Rooli: D
 Varmista, että automatisoidut testit tunnistavat formaattivirheet ja null-arvot jokaisessa tiedon vastaanotossa tai merkittävässä datan muunnoksessa.
 #1.4.2    Taso: 2    Rooli: D/V
 Varmista, että LLM-koulutus- ja hienosäätöputket toteuttavat myrkytyshavaintojen ja datan eheysvalidoinnin (esim. tilastolliset menetelmät, poikkeavuuksien havaitseminen, upotusanalyysi) tunnistaakseen mahdolliset myrkytyshyökkäykset (esim. tunnisteiden kääntäminen, takaporttikäynnistimien lisäys, roolinvaihtokäskyt, vaikuttavat instanssihyökkäykset) tai tahattoman datan vaurioitumisen koulutusdatassa.
 #1.4.3    Taso: 3    Rooli: D/V
 Varmista, että asianmukaiset suojaukset, kuten vastustava koulutus (generoitujen vastustavien esimerkkien käyttö), datan laajentaminen häiritetyillä syötteillä tai robustit optimointitekniikat, on otettu käyttöön ja säädetty asiaankuuluville malleille riskinarvioinnin perusteella.
 #1.4.4    Taso: 2    Rooli: D/V
 Varmista, että automaattisesti tuotetut tunnisteet (esim. LLM:ien tai heikon valvonnan kautta) ovat luottamuskynnysten ja johdonmukaisuustarkistusten alaisia harhaisiksi, harhaanjohtaviksi tai matalan luottamuksen tunnisteiksi epäilyn havaitsemiseksi.
 #1.4.5    Taso: 3    Rooli: D
 Varmista, että automatisoidut testit havaitsevat tunnistesiirtymät jokaisessa tietojen vastaanotossa tai merkittävässä tiedonmuutoksessa.

---

### C1.5 Tietojen jäljitettävyys ja alkuperän seuranta

Seuraa jokaisen datapisteen koko matkaa lähteestä mallin syötteeksi auditointia ja poikkeamien hallintaa varten.

 #1.5.1    Taso: 2    Rooli: D/V
 Varmista, että kunkin datapisteen jälkeläisyys, mukaan lukien kaikki muunnokset, lisäykset ja yhdistämiset, on tallennettu ja että se voidaan rekonstruoida.
 #1.5.2    Taso: 2    Rooli: D/V
 Varmista, että alkuperätiedot ovat muuttumattomia, turvallisesti tallennettuja ja saatavilla tarkastuksia varten.
 #1.5.3    Taso: 2    Rooli: D/V
 Varmista, että jäljitettävyys kattaa tietosuojan säilyttämiseen tai generatiivisiin tekniikoihin perustuvan synteettisen datan ja että kaikki synteettinen data on selkeästi merkitty ja erotettavissa todellisesta datasta koko prosessin ajan.

---

### Viitteet

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

## C2-käyttäjän syötteen validointi

### Ohjaustavoite

Käyttäjän syötteen vahva validointi on etulinjan puolustuskeino joitakin haitallisimpia hyökkäyksiä vastaan tekoälyjärjestelmiä kohtaan. Kehote-injektiohyökkäykset voivat ohittaa järjestelmäohjeet, vuotaa arkaluonteisia tietoja tai ohjata mallin käyttäytymään sallitsemattomalla tavalla. Ellei erityisiä suodattimia ja ohjehierarkioita ole käytössä, tutkimukset osoittavat, että "multi-shot" jailbreakit, jotka hyödyntävät erittäin pitkiä kontekstiikkunoita, ovat tehokkaita. Myös hienovaraiset vihamieliset häirintäiskut—kuten homoglyph-vaihdot tai leetspeak—voivat hiljaisesti muuttaa mallin päätöksiä.

---

### C2.1 Kehoteinjektion puolustus

Kehotteinjektio on yksi suurimmista riskeistä tekoälyjärjestelmille. Suojautuminen tätä taktiikkaa vastaan käyttää yhdistelmää staattisia mallisuodattimia, dynaamisia luokittelijoita ja ohjeistuksenalaisen hierarkian noudattamisen varmistamista.

 #2.1.1    Taso: 1    Rooli: D/V
 Varmista, että käyttäjän syötteet tarkistetaan jatkuvasti päivitettyä tunnettujen kehotteiden injektiomallien kirjastoa vastaan (jailbreak-avainsanat, "ignore previous" -komennot, roolipeliketjut, epäsuorat HTML-/URL-hyökkäykset).
 #2.1.2    Taso: 1    Rooli: D/V
 Varmista, että järjestelmä noudattaa ohjeiden hierarkiaa, jossa järjestelmän tai kehittäjän viestit ohittavat käyttäjän ohjeet, myös kontekstikehyksen laajentamisen jälkeen.
 #2.1.3    Taso: 2    Rooli: D/V
 Varmista, että vastustava arviointi (esim. Red Teamin "many-shot" -kehotteet) suoritetaan ennen jokaista mallin tai kehotepohjan julkaisua, asetettujen onnistumisprosenttirajojen ja automaattisten takaisinkytkentäestojen kanssa regressioiden varalta.
 #2.1.4    Taso: 2    Rooli: D
 Varmista, että kolmannen osapuolen sisällöstä (verkkosivut, PDF:t, sähköpostit) peräisin olevat kehotteet puhdistetaan eristetyssä jäsentämiskontekstissa ennen niiden liittämistä pääkehotteeseen.
 #2.1.5    Taso: 3    Rooli: D/V
 Varmista, että kaikki kehotteen suodatussääntöjen päivitykset, luokittelijamalliversiot ja estolistamuutokset ovat versiohallinnassa ja auditoitavissa.

---

### C2.2 Vastustuskyky vihamielisille esimerkeille

Luonnollisen kielen käsittelyn (NLP) mallit ovat edelleen alttiita hienovaraisille merkki- tai sanatasoisille häiriöille, jotka ihmiset usein ohittavat, mutta joiden mallien luokittelu menee yleensä vikaan.

 #2.2.1    Taso: 1    Rooli: D
 Varmista, että perus syötteen normalisointivaiheet (Unicode NFC, homoglyph-kartoitus, välilyöntien poistaminen) suoritetaan ennen tokenisointia.
 #2.2.2    Taso: 2    Rooli: D/V
 Varmista, että tilastollinen poikkeamien havaitseminen tunnistaa syötteet, joilla on epätavallisen suuri muokkausetäisyys kielinormeihin nähden, liiallisesti toistuvia tokeneita tai epänormaaleja upotusmatkoja.
 #2.2.3    Taso: 2    Rooli: D
 Varmista, että päättelyputki tukee valinnaisia vastahyökkäyskoulutuksella vahvistettuja mallivariantteja tai puolustuskerroksia (esim. satunnaistus, puolustava tislaus) korkean riskin päätepisteille.
 #2.2.4    Taso: 2    Rooli: V
 Varmista, että epäillyt vihamieliset syötteet eristetään karanteeniin ja kirjataan täydellisten tietosisältöjen kanssa (henkilötietojen peittämisen jälkeen).
 #2.2.5    Taso: 3    Rooli: D/V
 Varmista, että jäykkyysmittarit (tunnettujen hyökkäyspakettien onnistumisprosentti) seurataan ajan myötä ja että taantumat aiheuttavat julkaisun eston.

---

### C2.3 Skeeman, tyypin ja pituuden validointi

AI-hyökkäykset, jotka sisältävät virheellisiä tai liian suuria syötteitä, voivat aiheuttaa jäsentämisvirheitä, kehotepuolilta tapahtuvaa vuotoa ja resurssien loppumista. Tiukka skeeman valvonta on myös edellytys determinististen työkalukutsujen suorittamiselle.

 #2.3.1    Taso: 1    Rooli: D
 Varmista, että jokainen API- tai funktiokutsun päätepiste määrittelee eksplisiittisen syötteen skeeman (JSON Schema, Protobuf tai multimodaalinen vastine) ja että syötteet validoidaan ennen kehotteen kokoamista.
 #2.3.2    Taso: 1    Rooli: D/V
 Varmista, että syötteet, jotka ylittävät enimmäismäärän sanoja tai tavuja, hylätään turvallisella virheilmoituksella eivätkä koskaan katkaistu hiljaisesti.
 #2.3.3    Taso: 2    Rooli: D/V
 Varmista, että tyyppitarkistukset (esim. numeeriset arvovälit, enum-arvot, MIME-tyypit kuville/äänille) tehdään palvelinpuolella, eikä ainoastaan asiakasohjelmakoodissa.
 #2.3.4    Taso: 2    Rooli: D
 Varmista, että semanttiset validoijat (esim. JSON Schema) suoritetaan vakioaikaisesti estääkseen algoritmisen DoS-hyökkäyksen.
 #2.3.5    Taso: 3    Rooli: V
 Varmista, että validointivirheet kirjataan sensuroiduin tietosisällön osin ja yksiselitteisin virhekoodin, jotta turvallisuuden käsittelyä voidaan helpottaa.

---

### C2.4 Sisällön ja politiikan tarkastus

Kehittäjien tulisi pystyä havaitsemaan syntaktisesti kelvolliset kehotteet, jotka pyytävät kiellettyä sisältöä (kuten laittomia ohjeita, vihapuhetta ja tekijänoikeudella suojattua tekstiä), ja estämään niiden leviämisen.

 #2.4.1    Taso: 1    Rooli: D
 Varmista, että sisältöluokittelija (zero shot tai hienosäädetty) arvioi jokaisen syötteen väkivallan, itseen kohdistuvan vahingon, vihan, seksuaalisen sisällön ja laittomat pyynnöt osalta, ja että kynnysarvot ovat konfiguroitavissa.
 #2.4.2    Taso: 1    Rooli: D/V
 Varmista, että politiikkoja rikkovat syötteet saavat standardoidut kieltäytymiset tai turvalliset täydennykset, jotta ne eivät siirry alempiin LLM-kutsuihin.
 #2.4.3    Taso: 2    Rooli: D
 Varmista, että seulontamalli tai sääntöjoukko koulutetaan uudelleen/päivitetään vähintään neljännesvuosittain, ottaen huomioon äskettäin havaitut jailbreikkaus- tai politiikan kiertämismallit.
 #2.4.4    Taso: 2    Rooli: D
 Varmista, että seulonta noudattaa käyttäjäkohtaisia politiikkoja (ikä, alueelliset lailliset rajoitukset) käyttöön perustuvien sääntöjen avulla, jotka ratkaistaan pyyntöhetkellä.
 #2.4.5    Taso: 3    Rooli: V
 Varmista, että seulontalokit sisältävät luokittelijan luottamuspisteet ja politiikkakategorian tunnisteet SOC:n korrelaatiota ja tulevaa red-teamin uudelleensoitantoa varten.

---

### C2.5 Syötteen nopeuden rajoittaminen ja väärinkäytön estäminen

Kehittäjien tulisi estää väärinkäytökset, resurssien loppuminen ja automatisoidut hyökkäykset tekoälyjärjestelmiä vastaan rajoittamalla syötteiden määrää ja havaitsemalla poikkeavat käyttökuviot.

 #2.5.1    Taso: 1    Rooli: D/V
 Varmista, että käyttäjäkohtaiset, IP-osoitekohtaiset ja API-avainkohtaiset nopeusrajoitukset toteutetaan kaikilla syöttöpisteillä.
 #2.5.2    Taso: 2    Rooli: D/V
 Varmista, että huippu- ja jatkuvat nopeusrajat on säädetty estämään palvelunestohyökkäykset (DoS) ja brutaalivoimahyökkäykset.
 #2.5.3    Taso: 2    Rooli: D/V
 Varmista, että poikkeavat käyttötavat (esim. nopealla tahdilla tehdyt pyynnöt, syötteen tulva) laukaisevat automaattiset estot tai eskaloinnit.
 #2.5.4    Taso: 3    Rooli: V
 Varmista, että väärinkäytösten ehkäisyn lokit säilytetään ja tarkastetaan uusien hyökkäyskuvioiden varalta.

---

### C2.6 Monimodaalinen syötteen validointi

AI-järjestelmien tulisi sisältää vahva validointi tekstin ulkopuolisille syötteille (kuvat, ääni, tiedostot) estääkseen injektion, kiertämisen tai resurssien väärinkäytön.

 #2.6.1    Taso: 1    Rooli: D
 Varmista, että kaikki ei-tekstimuotoiset syötteet (kuvat, äänet, tiedostot) tarkistetaan tyypin, koon ja muodon osalta ennen käsittelyä.
 #2.6.2    Taso: 2    Rooli: D/V
 Varmista, että tiedostot tarkistetaan haittaohjelmien ja steganografisten hyötykuormien varalta ennen syöttämistä.
 #2.6.3    Taso: 2    Rooli: D/V
 Varmista, että kuva-/äänianturit tarkistetaan vihamielisten häiriöiden tai tunnettujen hyökkäysmallien varalta.
 #2.6.4    Taso: 3    Rooli: V
 Varmista, että monimuotoisten syötteiden validointivirheet kirjataan ja laukaisevat hälytykset tutkintaa varten.

---

### C2.7 Syötteen alkuperä ja lähdeviittaus

AI-järjestelmien tulisi tukea tarkastuksia, väärinkäytösten seurantaa ja sääntöjen noudattamista seuraamalla ja merkitsemällä kaikkien käyttäjien syötteiden alkuperät.

 #2.7.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki käyttäjien syötteet merkitään metatiedoilla (käyttäjätunnus, istunto, lähde, aikaleima, IP-osoite) syötteen vastaanottamisen yhteydessä.
 #2.7.2    Taso: 2    Rooli: D/V
 Varmista, että alkuperätiedot säilyvät ja ovat tarkastettavissa kaikille käsitellyille syötteille.
 #2.7.3    Taso: 2    Rooli: D/V
 Varmista, että poikkeavat tai epäluotettavat syöttölähteet tunnistetaan ja niitä kohdennetaan tehostetulla valvonnalla tai estetään.

---

### C2.8 Reaaliaikainen adaptiivinen uhkien havaitseminen

Kehittäjien tulisi käyttää kehittyneitä uhkien tunnistusjärjestelmiä tekoälylle, jotka sopeutuvat uusiin hyökkäysmalleihin ja tarjoavat reaaliaikaista suojaa koottuun mallien tunnistukseen perustuen.

 #2.8.1    Taso: 1    Rooli: D/V
 Varmista, että uhkien tunnistusmallit on käännetty optimoiduiksi regex-moottoreiksi korkeaa suorituskykyä varten reaaliaikaiseen suodatukseen, jossa viivevaikutus on minimaalinen.
 #2.8.2    Taso: 1    Rooli: D/V
 Varmista, että uhkien tunnistusjärjestelmät ylläpitävät erillisiä mallikirjastoja eri uhkakategorioille (kehotusinjektio, haitallinen sisältö, arkaluonteiset tiedot, järjestelmäkomennot).
 #2.8.3    Taso: 2    Rooli: D/V
 Varmista, että adaptatiivinen uhkien havaitseminen sisältää koneoppimismallit, jotka päivittävät uhan herkkyyttä hyökkäysten esiintymistiheyden ja onnistumisprosenttien perusteella.
 #2.8.4    Taso: 2    Rooli: D/V
 Varmista, että reaaliaikaiset uhkatiedon syötteet päivittävät automaattisesti mallikirjastoja uusilla hyökkäysallekirjoituksilla ja IOC:illa (kompromissin indikaattorit).
 #2.8.5    Taso: 3    Rooli: D/V
 Varmista, että uhkien tunnistuksen väärien positiivisten määrät seurataan jatkuvasti ja mallin spesifisyyttä säädetään automaattisesti minimoimaan laillisten käyttötapausten häiriöt.
 #2.8.6    Taso: 3    Rooli: D/V
 Varmista, että kontekstuaalinen uhka-analyysi ottaa huomioon syötteen lähteen, käyttäytymismallit ja istunnon historian parantaakseen tunnistuksen tarkkuutta.
 #2.8.7    Taso: 3    Rooli: D/V
 Varmista, että uhkien havaitsemisen suorituskykymittarit (havaintataajuus, käsittelyviive, resurssien käyttö) seurataan ja optimoidaan reaaliajassa.

---

### C2.9 Monimodaalinen turvallisuuden validointiputki

Kehittäjien tulisi tarjota turvallisuusvarmennus tekstille, kuvalle, äänelle ja muille tekoälyn syötemodaaliteeteille käyttämällä erityyppistä uhkien havaitsemista ja resurssien eristämistä.

 #2.9.1    Taso: 1    Rooli: D/V
 Varmista, että jokaisella syötemodaliteetilla on omistautuneet turvallisuustarkastajat, joilla on dokumentoidut uhkamallit (teksti: kehotteen injektio, kuvat: steganografia, ääni: spektrogrammihyökkäykset) ja havaitsemiskynnykset.
 #2.9.2    Taso: 2    Rooli: D/V
 Varmista, että monimuotoiset syötteet käsitellään eristetyissä hiekkalaatikoissa, joissa on määritellyt resurssirajoitukset (muisti, suorittimen käyttö, käsittelyaika) kullekin modaliteettityypille erikseen ja jotka on dokumentoitu turvallisuuspolitiikoissa.
 #2.9.3    Taso: 2    Rooli: D/V
 Varmista, että ristimodaalinen hyökkäyksen tunnistus havaitsee koordinoidut hyökkäykset, jotka kattavat useita syötetyyppejä (esim. steganografiset kuormitukset kuvissa yhdistettynä kehotteen injektioon tekstissä) korrelaatiosääntöjen ja hälytyksen generoinnin avulla.
 #2.9.4    Taso: 3    Rooli: D/V
 Varmista, että monimuotoisen validoinnin epäonnistumiset laukaisevat yksityiskohtaisen lokituksen, joka sisältää kaikki syötemodaalit, validointitulokset, uhkapisteet ja korrelaatioanalyysin rakenteellisissa lokimuodoissa SIEM-integraatiota varten.
 #2.9.5    Taso: 3    Rooli: D/V
 Varmista, että modality-kohtaiset sisältöluokittelijat päivitetään dokumentoitujen aikataulujen mukaisesti (vähintään neljännesvuosittain) uusilla uhkamalleilla, vihamielisillä esimerkeillä ja suorituskykymittareilla, jotka pidetään perustasojen yläpuolella.

---

### Viitteet

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

## C3-mallin elinkaaren hallinta ja muutosvalvonta

### Ohjaustavoite

tekoälyjärjestelmien on toteutettava muutosten hallintaprosessit, jotka estävät luvattomat tai ei-turvalliset mallimuutokset pääsemästä tuotantoon. Tämä valvonta varmistaa mallin eheyden koko elinkaaren ajan – kehityksestä käyttöönottoon ja poistamiseen – mikä mahdollistaa nopean reagoinnin poikkeustilanteisiin ja ylläpitää vastuullisuutta kaikista muutoksista.

Keskeinen suojaustavoite: Vain valtuutetut, validoidut mallit pääsevät tuotantoon käyttämällä hallittuja prosesseja, jotka ylläpitävät eheyden, jäljitettävyyden ja palautettavuuden.

---

### C3.1 Mallin valtuutus ja eheys

Vain valtuutetut mallityypit, joiden eheys on vahvistettu, pääsevät tuotantoympäristöihin.

 #3.1.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki mallin artefaktit (painot, konfiguraatiot, tokenisoijat) on kryptografisesti allekirjoitettu valtuutettujen tahojen toimesta ennen käyttöönottoa.
 #3.1.2    Taso: 1    Rooli: D/V
 Varmista, että mallin eheys tarkistetaan käyttöönottohetkellä ja allekirjoituksen vahvistuksen epäonnistumiset estävät mallin lataamisen.
 #3.1.3    Taso: 2    Rooli: D/V
 Varmista, että mallin jäljitettävyyden tiedoissa on mukana valtuuttavan tahon tunnistetiedot, harjoitusdatan tarkistussummat, validointitestien tulokset läpäisy-/epäonnistumistilanteineen sekä luontiaikaleima.
 #3.1.4    Taso: 2    Rooli: D/V
 Varmista, että kaikki mallin artefaktit käyttävät semanttista versiointia (MAJOR.MINOR.PATCH) ja että on dokumentoitu kriteerit, jotka määrittävät, milloin kukin version osa kasvaa.
 #3.1.5    Taso: 2    Rooli: V
 Varmista, että riippuvuuksien seuranta ylläpitää reaaliaikaista varastotilannetta, joka mahdollistaa kaikkien kuluttavien järjestelmien nopean tunnistamisen.

---

### C3.2 Mallin validointi ja testaus

Mallit on läpäistävä määritellyt turvallisuus- ja varmistustarkastukset ennen käyttöönottoa.

 #3.2.1    Taso: 1    Rooli: D/V
 Varmista, että mallien läpikäyvät automatisoidut turvallisuustestit, jotka sisältävät syötteen validoinnin, tulosten puhdistuksen ja turvallisuusarvioinnit ennalta sovittujen organisaation läpäisy/epäonnistuminen-rajojen mukaisesti ennen käyttöönottoa.
 #3.2.2    Taso: 1    Rooli: D/V
 Varmista, että validointivirheet estävät mallin käyttöönoton automaattisesti, ellei ennalta nimetyt valtuutetut henkilöt ole antaneet nimenomaista poikkeuslupaa kirjattujen liiketoimintaperustelujen kanssa.
 #3.2.3    Taso: 2    Rooli: V
 Varmista, että testitulokset ovat kryptografisesti allekirjoitettuja ja muuttumattomasti linkitettyjä vahvistettavan malliversion hajautusarvoon.
 #3.2.4    Taso: 2    Rooli: D/V
 Varmista, että hätäasennukset edellyttävät dokumentoitua tietoturvariskien arviointia ja hyväksyntää ennalta määritellyltä tietoturvaviranomaiselta sovittujen aikataulujen puitteissa.

---

### C3.3 Hallittu käyttöönotto ja palautus

Mallin käyttöönotot on oltava hallittuja, valvottuja ja peruutettavissa olevia.

 #3.3.1    Taso: 1    Rooli: D
 Varmista, että tuotantoon käyttöönotot toteuttavat asteittaiset käyttöönoton mekanismit (kanariakäyttöönotot, sinivihreät käyttöönotot) automaattisilla palautuslaukaisijoilla, jotka perustuvat ennalta sovittuihin virhesuhteisiin, viiveen raja-arvoihin tai tietoturvahälytyskriteereihin.
 #3.3.2    Taso: 1    Rooli: D/V
 Varmista, että palautusominaisuudet palauttavat täydellisen mallin tilan (painot, asetukset, riippuvuudet) atomisesti ennalta määriteltyjen organisaation aikarajojen sisällä.
 #3.3.3    Taso: 2    Rooli: D/V
 Varmista, että käyttöönottoprosessit validoivat kryptografiset allekirjoitukset ja laskevat eheystarkistussummat ennen mallin aktivointia, ja epäonnistuvat käyttöönotossa kaikissa poikkeamissa.
 #3.3.4    Taso: 2    Rooli: D/V
 Varmista, että hätätilan mallin sammutusominaisuudet voivat poistaa mallin päätepisteet käytöstä ennalta määritettyjen vasteaikojen sisällä automaattisten katkaisijoiden tai manuaalisten katkaisukytkinten avulla.
 #3.3.5    Taso: 2    Rooli: V
 Varmista, että takaisinperuutuksen artefaktit (aiemmat malliversiot, kokoonpanot, riippuvuudet) säilytetään organisaation käytäntöjen mukaisesti muuttumattomassa tallennustilassa häiriötilanteisiin varautumista varten.

---

### C3.4 Muutosten vastuullisuus ja auditointi

Kaikkien mallin elinkaaren muutosten on oltava jäljitettäviä ja tarkastettavissa.

 #3.4.1    Taso: 1    Rooli: V
 Varmista, että kaikki mallin muutokset (käyttöönotto, konfigurointi, käytöstä poisto) tuottavat muuttumattomia tarkastustietueita, jotka sisältävät aikaleiman, todennetun toimijan tunnisteen, muutostyypin sekä ennen ja jälkeen -tilat.
 #3.4.2    Taso: 2    Rooli: D/V
 Varmista, että tilintarkastuslokin käyttö vaatii asianmukaisen valtuutuksen ja kaikki käyttöyritykset kirjataan käyttäjätunnuksella ja aikaleimalla.
 #3.4.3    Taso: 2    Rooli: D/V
 Varmista, että kehotemallit ja järjestelmäviestit ovat versionhallinnassa git-repositorioissa, ja että niihin liittyy pakollinen koodikatselmointi sekä hyväksyntä nimetyiltä tarkastajilta ennen käyttöönottoa.
 #3.4.4    Taso: 2    Rooli: V
 Varmista, että auditointitiedot sisältävät riittävät yksityiskohdat (mallin tiivisteet, kokoonpanon tilannevedokset, riippuvuuksien versiot) mahdollistamaan mallin tilan täydellisen rekonstruoinnin mille tahansa säilytysjakson aikaleimalle.

---

### C3.5 Turvalliset kehityskäytännöt

Mallin kehitys- ja koulutusprosessien on noudatettava turvallisia käytäntöjä estääkseen vaarantumisen.

 #3.5.1    Taso: 1    Rooli: D
 Varmista, että mallin kehitys-, testaus- ja tuotantoympäristöt ovat fyysisesti tai loogisesti erillään. Niillä ei ole yhteistä infrastruktuuria, ne käyttävät erillisiä pääsynvalvontoja ja niillä on eristetyt tietovarastot.
 #3.5.2    Taso: 1    Rooli: D
 Varmista, että mallin koulutus ja hienosäätö tapahtuvat eristetyissä ympäristöissä, joissa on hallittu verkon käyttöoikeus.
 #3.5.3    Taso: 1    Rooli: D/V
 Varmista, että koulutusdat lähteet tarkistetaan eheystarkastuksilla ja varmennetaan luotettavista lähteistä dokumentoidun omistajuusketjun avulla ennen niiden käyttöä mallin kehityksessä.
 #3.5.4    Taso: 2    Rooli: D
 Varmista, että mallin kehityksen artefaktit (hyperparametrit, koulutusskriptit, kokoonpanotiedostot) tallennetaan versiohallintaan ja vaativat vertaisarvioinnin hyväksynnän ennen käyttöönottoa koulutuksessa.

---

### C3.6 Mallin käytöstäpoisto ja poistaminen käytöstä

Mallit on poistettava käytöstä turvallisesti, kun niitä ei enää tarvita tai kun turvallisuusongelmia havaitaan.

 #3.6.1    Taso: 1    Rooli: D
 Varmista, että mallin käytöstäpoistoprosessit skannaavat automaattisesti riippuvuuskartat, tunnistavat kaikki kuluttavat järjestelmät ja tarjoavat ennalta sovitut ennakkoilmoitusajat ennen käytöstä poistamista.
 #3.6.2    Taso: 1    Rooli: D/V
 Varmista, että eläkkeelle jääneet mallien tiedostot pyyhitään turvallisesti kryptografisella tuhoamisella tai monikertaisella ylikirjoituksella dokumentoitujen tietojen säilytyskäytäntöjen mukaisesti, ja että tuhoamistodistukset on varmennettu.
 #3.6.3    Taso: 2    Rooli: V
 Varmista, että mallin poistotapahtumat kirjataan aikaleiman ja toimijan tunnistetiedon kanssa, sekä että mallin allekirjoitukset peruutetaan uudelleenkäytön estämiseksi.
 #3.6.4    Taso: 2    Rooli: D/V
 Varmista, että hätätilan mallin poistaminen käytöstä voi estää mallin pääsyn ennalta määritettyjen hätätilan vasteaikojen puitteissa automatisoitujen pysäytyskytkinten avulla, jos kriittisiä tietoturva-aukkoja havaitaan.

---

### Viitteet

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

## C4-infrastruktuuri, konfigurointi ja käyttöönoton turvallisuus

### Ohjaustavoite

Tekoälyn infrastruktuuri on kovennettava etuoikeuksien eskalaatiota, toimitusketjun manipulointia ja sivuttaisliikettä vastaan turvallisen konfiguraation, suoritusajan eristyksen, luotettavien käyttöönotto-putkien ja kattavan valvonnan avulla. Vain valtuutetut, validoidut infrastruktuurin komponentit ja konfiguraatiot pääsevät tuotantoon hallittujen prosessien kautta, jotka ylläpitävät turvallisuutta, eheyttä ja tarkastettavuutta.

Keskeinen turvallisuustavoite: Vain kryptografisesti allekirjoitetut, haavoittuvuusskannatut infrastruktuurikomponentit pääsevät tuotantoon automatisoitujen validointiputkien kautta, jotka valvovat turvallisuuspolitiikkojen noudattamista ja ylläpitävät muuttumattomia tarkastuslokeja.

---

### C4.1 Suoritusympäristön eristäminen

Estä kontin karkailu ja oikeuksien korotus ydin-tason eristysprimitiivien ja pakollisten pääsynvalvontojen avulla.

 #4.1.1    Taso: 1    Rooli: D/V
 Varmista, että kaikista tekoälysäiliöistä poistetaan KAIKKI Linuxin oikeudet paitsi CAP_SETUID, CAP_SETGID sekä turvallisuusperustasoissa eksplisiittisesti vaaditut oikeudet.
 #4.1.2    Taso: 1    Rooli: D/V
 Varmista, että seccomp-profiilit estävät kaikki järjestelmäkutsut poistamalla ne, jotka eivät ole ennakkoon hyväksytyissä sallituissa listoissa, ja että rikkomukset aiheuttavat kontin päättymisen ja tuottavat turvallisuushälytyksiä.
 #4.1.3    Taso: 2    Rooli: D/V
 Varmista, että tekoälykuormitukset suoritetaan vain-luku -juurijärjestelmillä, tmpfs-väliaikaiselle datalle ja nimetyillä tilavuuksilla pysyvälle datalle siten, että noexec-liitoksen asetukset ovat käytössä.
 #4.1.4    Taso: 2    Rooli: D/V
 Varmista, että eBPF-pohjainen suoritusmonitorointi (Falco, Tetragon tai vastaava) havaitsee oikeuksien korotuspyrkimykset ja lopettaa automaattisesti rikkomukseen syyllistyvät prosessit organisaation vasteaikavaatimusten mukaisesti.
 #4.1.5    Taso: 3    Rooli: D/V
 Varmista, että korkean riskin tekoälykuormitukset suoritetaan laitteistollisesti eristetyissä ympäristöissä (Intel TXT, AMD SVM tai omistetut bare-metal-solmut) ja että suoritetaan todennusvahvistus.

---

### C4.2 Turvalliset rakennus- ja käyttöönotto-putket

Varmista kryptografinen eheys ja toimitusketjun turvallisuus toistettavien rakennusten ja allekirjoitettujen artefaktien avulla.

 #4.2.1    Taso: 1    Rooli: D/V
 Varmista, että infrastruktuuri-koodina tarkastetaan työkaluilla (tfsec, Checkov tai Terrascan) jokaisessa commitissa, estäen yhdistämiset kriittisillä tai korkealla vakavuudella löytyvien virheiden tapauksessa.
 #4.2.2    Taso: 1    Rooli: D/V
 Varmista, että konttirakennukset ovat toistettavissa identtisillä SHA256-tiivisteillä eri rakennuskertojen välillä ja luo Sigstorella allekirjoitetut SLSA-tason 3 alkuperätodistukset.
 #4.2.3    Taso: 2    Rooli: D/V
 Varmista, että konttikuvat sisältävät CycloneDX- tai SPDX-SBOM-tiedostot ja ne on allekirjoitettu Cosignilla ennen rekisteriin työnnön tekemistä, ja että allekirjoittamattomat kuvat hylätään käyttöönotossa.
 #4.2.4    Taso: 2    Rooli: D/V
 Varmista, että CI/CD-putket käyttävät OIDC-tokeneita HashiCorp Vaultista, AWS IAM -rooleista tai Azure Managed Identityistä, joiden voimassaoloaika ei ylitä organisaation tietoturvakäytännön rajoja.
 #4.2.5    Taso: 2    Rooli: D/V
 Varmista, että Cosign-allekirjoitukset ja SLSA-lähdetiedot validoidaan käyttöönoton aikana ennen kontin suorittamista, ja että vahvistusvirheet aiheuttavat käyttöönoton epäonnistumisen.
 #4.2.6    Taso: 2    Rooli: D/V
 Varmista, että rakennusympäristöt toimivat katoavissa säiliöissä tai virtuaalikoneissa ilman pysyvää tallennustilaa ja verkkoeristettyinä tuotantoympäristöjen VPC-verkostoista.

---

### C4.3 Verkkoturva ja käyttöoikeuksien hallinta

Ota käyttöön zero-trust-verkotus oletuskieltopolitiikoilla ja salatuilla viestinnöillä.

 #4.3.1    Taso: 1    Rooli: D/V
 Varmista, että Kubernetes NetworkPolicies tai vastaava toteuttaa oletuksena estävän saapuvan/lähtevän liikenteen säännön, jossa sallitaan nimenomaisesti vaaditut portit (443, 8080 jne.).
 #4.3.2    Taso: 1    Rooli: D/V
 Varmista, että SSH (portti 22), RDP (portti 3389) ja pilven metatietopäätepisteet (169.254.169.254) ovat estettyjä tai vaativat sertifikaattiin perustuvan todennuksen.
 #4.3.3    Taso: 2    Rooli: D/V
 Varmista, että ulospäin suuntautuva liikenne suodatetaan HTTP/HTTPS-välityspalvelimien (Squid, Istio tai pilvi-NAT-porttien) kautta käyttämällä sallittujen verkkotunnusten luetteloita, ja estetyt pyynnöt kirjataan.
 #4.3.4    Taso: 2    Rooli: D/V
 Varmista, että palveluiden välinen viestintä käyttää keskinäistä TLS-yhteyttä, jossa sertifikaatit kierrätetään organisaation käytännön mukaisesti ja sertifikaattien validointi on pakollinen (ei ohitus- tai skip-verify-lippuja).
 #4.3.5    Taso: 2    Rooli: D/V
 Varmista, että tekoälyinfrastruktuuri toimii omistetuissa VPC:issä/VNet:issä ilman suoraa internet-yhteyttä ja kommunikoi ainoastaan NAT-porttien tai bastion-palvelimien kautta.

---

### C4.4 Salaisuuksien ja kryptografisten avainten hallinta

Suojaa tunnistetiedot laitteistopohjaisella tallennuksella ja automatisoidulla kierrätyksellä nollas luottamuksen pääsystä.

 #4.4.1    Taso: 1    Rooli: D/V
 Varmista, että salaisuudet tallennetaan HashiCorp Vaultiin, AWS Secrets Manageriin, Azure Key Vaultiin tai Google Secret Manageriin käyttäen levossa olevaa AES-256-salausta.
 #4.4.2    Taso: 1    Rooli: D/V
 Varmista, että kryptografiset avaimet generoidaan FIPS 140-2 Tason 2 HSM-laitteissa (AWS CloudHSM, Azure Dedicated HSM) ja että avainten vaihtaminen tapahtuu organisaation kryptografisen politiikan mukaisesti.
 #4.4.3    Taso: 2    Rooli: D/V
 Varmista, että salaisuuksien kierto on automatisoitu ilman käyttökatkoksia toteutetun käyttöönoton yhteydessä ja että kierto käynnistyy välittömästi henkilöstömuutosten tai turvallisuustapahtumien seurauksena.
 #4.4.4    Taso: 2    Rooli: D/V
 Varmista, että säiliökuvat skannataan työkaluilla (GitLeaks, TruffleHog tai detect-secrets), jotka estävät rakentamisen, jos ne sisältävät API-avaimia, salasanoja tai sertifikaatteja.
 #4.4.5    Taso: 2    Rooli: D/V
 Varmista, että tuotannon salaisen pääsyn edellyttää MFA:ta laitteistotunnisteilla (YubiKey, FIDO2) ja että se kirjataan muuttumattomiin auditointilokeihin käyttäjätunnuksineen ja aikaleimoineen.
 #4.4.6    Taso: 2    Rooli: D/V
 Varmista, että salaisuudet injektoidaan Kubernetes-salasanojen, liitettyjen tallennustilojen tai init-konttien kautta, ja varmista, ettei salaisuuksia koskaan upoteta ympäristömuuttujiin tai kuviin.

---

### C4.5 AI Työkuorman eristys ja validointi

Eristä epäluotettavat tekoälymallit turvallisiin hiekkalaatikoihin kattavalla käyttäytymisanalyysillä.

 #4.5.1    Taso: 1    Rooli: D/V
 Varmista, että ulkoiset tekoälymallit suoritetaan gVisorissa, microVM:issä (kuten Firecracker, CrossVM) tai Docker-konteissa käyttäen --security-opt=no-new-privileges ja --read-only -lippuja.
 #4.5.2    Taso: 1    Rooli: D/V
 Varmista, että hiekkalaatikkoympäristöillä ei ole verkkoyhteyttä (--network=none) tai niillä on vain localhost-yhteys, ja kaikki ulkoiset pyynnöt estetään iptables-säännöillä.
 #4.5.3    Taso: 2    Rooli: D/V
 Varmista, että tekoälymallin validointi sisältää automatisoidun red-tiimin testaamisen organisaation määrittelemällä testikattavuudella ja käyttäytymisanalyysillä takaporttien havaitsemiseksi.
 #4.5.4    Taso: 2    Rooli: D/V
 Varmista, että ennen kuin tekoälymalli otetaan tuotantokäyttöön, sen hiekkalaatikkotulokset allekirjoitetaan kryptografisesti valtuutettujen turvallisuushenkilöiden toimesta ja tallennetaan muuttumattomiin tarkastuslokikirjoihin.
 #4.5.5    Taso: 2    Rooli: D/V
 Varmista, että hiekkalaatikkoympäristöt tuhotaan ja luodaan uudelleen kultakuvista arviointien välillä täydellisellä tiedostojärjestelmän ja muistin puhdistuksella.

---

### C4.6 Infrastruktuurin turvallisuuden valvonta

Jatkuvasti skannaa ja valvo infrastruktuuria automatisoidulla korjauksella ja reaaliaikaisella hälytyksellä.

 #4.6.1    Taso: 1    Rooli: D/V
 Varmista, että säilökuvat tarkastetaan organisaation aikataulujen mukaisesti siten, että KRIITTISEN tason haavoittuvuudet estävät käyttöönoton organisaation riskikynnysten perusteella.
 #4.6.2    Taso: 1    Rooli: D/V
 Varmista, että infrastruktuuri täyttää CIS Benchmarkit tai NIST 800-53 -ohjaimet organisaation määrittämillä vaatimustenmukaisuusrajoilla ja automatisoidulla korjauksella epäonnistuneisiin tarkastuksiin.
 #4.6.3    Taso: 2    Rooli: D/V
 Varmista, että KORKEAN vakavuuden haavoittuvuudet on korjattu organisaation riskienhallinnan aikataulujen mukaisesti, ja että käytössä on hätämenettelyt aktiivisesti hyödynnettyjen CVE-tietoturva-aukkojen varalta.
 #4.6.4    Taso: 2    Rooli: V
 Varmista, että turvallisuushälytykset integroituvat SIEM-alustoihin (Splunk, Elastic tai Sentinel) käyttäen CEF- tai STIX/TAXII-muotoja automaattisen rikastamisen kanssa.
 #4.6.5    Taso: 3    Rooli: V
 Varmista, että infrastruktuurin mittarit viedään valvontajärjestelmiin (Prometheus, DataDog) SLA-hallintapaneeleilla ja johdon raportoinnilla.
 #4.6.6    Taso: 2    Rooli: D/V
 Varmista, että konfiguraation poikkeamat havaitaan työkalujen (Chef InSpec, AWS Config) avulla organisaation valvontavaatimusten mukaisesti, ja että luvattomille muutoksille on automaattinen palautus.

---

### C4.7 AI-infrastruktuurin resurssien hallinta

Estä resurssien loppumiseen tähtäävät hyökkäykset ja varmista resurssien oikeudenmukainen jakaminen kiintiöiden ja valvonnan avulla.

 #4.7.1    Taso: 1    Rooli: D/V
 Varmista, että GPU/TPU:n käyttöastetta valvotaan ja organisaation määrittelemissä kynnysarvoissa käynnistetään hälytykset sekä kapasiteetin hallintakäytäntöjen perusteella otetaan käyttöön automaattinen skaalaus tai kuormantasapainotus.
 #4.7.2    Taso: 1    Rooli: D/V
 Varmista, että tekoälyn kuormitusmittarit (päätelmän viive, läpimenonopeus, virheprosentit) kerätään organisaation valvontavaatimusten mukaisesti ja ne korreloidaan infrastruktuurin käytön kanssa.
 #4.7.3    Taso: 2    Rooli: D/V
 Varmista, että Kubernetes ResourceQuotas tai vastaavat rajoittavat yksittäisiä työkuormia organisaation resurssien allokointipolitiikkojen mukaisesti, ja että tiukat rajat pannaan täytäntöön.
 #4.7.4    Taso: 2    Rooli: V
 Varmista, että kustannusseuranta seuraa kulutusta työkuormittain/vuokralaisittain, sisältäen hälytykset organisaation budjettirajojen perusteella sekä automatisoidut valvontamekanismit budjetin ylitysten estämiseksi.
 #4.7.5    Taso: 3    Rooli: V
 Varmista, että kapasiteetin suunnittelu käyttää historiallista dataa organisaation määrittelemillä ennustejaksoilla ja automatisoitua resurssien käyttöönottoa kysyntämallien perusteella.
 #4.7.6    Taso: 2    Rooli: D/V
 Varmista, että resurssien ehtyminen laukaisee piirikytkimet organisaation vastausvaatimusten mukaisesti, mukaan lukien kapasiteettipolitiikkoihin perustuva nopeusrajoitus ja työkuorman eristäminen.

---

### C4.8 Ympäristön erottelu ja siirron valvonta

Toteuta tiukat ympäristörajat automaattisilla siirtoluvuilla ja turvallisuuden validoinnilla.

 #4.8.1    Taso: 1    Rooli: D/V
 Varmista, että kehitys/testi/tuotantoympäristöt toimivat erillisissä VPC:issä/VNet:eissä ilman yhteisiä IAM-rooleja, suojausryhmiä tai verkkoyhteyksiä.
 #4.8.2    Taso: 1    Rooli: D/V
 Varmista, että ympäristön edistäminen vaatii organisaation määrittelemien valtuutettujen henkilöiden hyväksynnän, joka tapahtuu kryptografisilla allekirjoituksilla ja muuttumattomilla auditointijäljillä.
 #4.8.3    Taso: 2    Rooli: D/V
 Tarkista, että tuotantoympäristöt estävät SSH-yhteydet, poistavat käytöstä debug-rajapinnat ja edellyttävät muutospyyntöjä organisaation etukäteisilmoitusvaatimuksineen paitsi hätätilanteissa.
 #4.8.4    Taso: 2    Rooli: D/V
 Varmista, että infrastruktuuri-koodina -muutokset vaativat vertaisarvioinnin automatisoidun testauksen ja tietoturvatarkastuksen kanssa ennen yhdistämistä päähaaraan.
 #4.8.5    Taso: 2    Rooli: D/V
 Varmista, että tuotannon ulkopuoliset tiedot on anonymisoitu organisaation tietosuojavaatimusten mukaisesti, synteettinen datan luonti tai täydellinen datan peittäminen henkilötietojen poisto varmennettu.
 #4.8.6    Taso: 2    Rooli: D/V
 Varmista, että promootiportit sisältävät automatisoidut turvallisuustestaukset (SAST, DAST, konttien skannaus) ja hyväksyntää varten vaaditaan nolla KRIITTISTÄ löydöstä.

---

### C4.9 Infrastruktuurin varmuuskopiointi ja palautus

Varmista infrastruktuurin kestävyys automatisoitujen varmuuskopioiden, testattujen palautusmenetelmien ja katastrofipalautusominaisuuksien avulla.

 #4.9.1    Taso: 1    Rooli: D/V
 Varmista, että infrastruktuurin kokoonpanot varmuuskopioidaan organisaation varmuuskopiointiaikataulujen mukaisesti maantieteellisesti erillisiin alueisiin 3-2-1-varmuuskopiointistrategian toteuttamisen mukaisesti.
 #4.9.2    Taso: 2    Rooli: D/V
 Varmista, että varmistusjärjestelmät toimivat eristetyissä verkoissa erillisillä tunnistetiedoilla ja ilmakidennetyllä tallennustilalla kiristyshaittaohjelmilta suojautumiseksi.
 #4.9.3    Taso: 2    Rooli: V
 Varmista, että palautusmenettelyt testataan ja validoidaan automatisoidun testauksen avulla organisaation aikataulujen mukaisesti siten, että RTO- ja RPO-tavoitteet täyttävät organisaation vaatimukset.
 #4.9.4    Taso: 3    Rooli: V
 Varmista, että katastrofipalautus sisältää tekoälykohtaiset toimintasuunnitelmat, jotka kattavat mallipainojen palauttamisen, GPU-klusterin uudelleenrakentamisen ja palveluiden riippuvuuskartoituksen.

---

### C4.10 Infrastruktuurin vaatimustenmukaisuus ja hallinta

Säilytä sääntelyvaatimusten noudattaminen jatkuvan arvioinnin, dokumentoinnin ja automatisoitujen valvontatoimien avulla.

 #4.10.1    Taso: 2    Rooli: D/V
 Varmista, että infrastruktuurin vaatimustenmukaisuus arvioidaan organisaation aikataulujen mukaisesti SOC 2:n, ISO 27001:n tai FedRAMP-ohjausten mukaisesti automaattisen todisteiden keruun avulla.
 #4.10.2    Taso: 2    Rooli: V
 Varmista, että infrastruktuurin dokumentaatio sisältää verkon kaaviot, tiedonvirtauskartat ja uhkamallit, jotka on päivitetty organisaation muutoksenhallinnan vaatimusten mukaisesti.
 #4.10.3    Taso: 3    Rooli: D/V
 Varmista, että infrastruktuurimuutokset käyvät läpi automatisoidun säädösten vaikutusten arvioinnin, jossa on hyväksyntäprosessit korkeaa riskiä edustaville muutoksille.

---

### C4.11 AI-laitteiston turvallisuus

Suojaa AI-spesifiset laitteistokomponentit, mukaan lukien GPU:t, TPU:t ja erikoistuneet AI-kiihdyttimet.

 #4.11.1    Taso: 2    Rooli: D/V
 Varmista, että tekoälykiihdyttimen laiteohjelmisto (GPU BIOS, TPU-laiteohjelmisto) on varmennettu kryptografisilla allekirjoituksilla ja päivitetty organisaation korjaushallinnan aikataulujen mukaisesti.
 #4.11.2    Taso: 2    Rooli: D/V
 Varmista, että ennen työkuorman suorittamista AI-kiihdyttimen eheyden vahvistaa laitteistovarmistus TPM 2.0:n, Intel TXT:n tai AMD SVM:n avulla.
 #4.11.3    Taso: 2    Rooli: D/V
 Varmista, että GPU-muisti on eristetty työkuormien välillä käyttämällä SR-IOV:ta, MIG:iä (Multi-Instance GPU) tai vastaavaa laitteistopohjaista jakamista, jossa muisti puhdistetaan työn vaihtuessa.
 #4.11.4    Taso: 3    Rooli: V
 Varmista, että tekoälylaitteiston toimitusketju sisältää alkuperän todentamisen valmistajan sertifikaateilla ja väärentämisen osoittavien pakkauksien varmistamisen.
 #4.11.5    Taso: 3    Rooli: D/V
 Varmista, että laitteistoturvayksiköt (HSM:t) suojaavat tekoälymallin painot ja kryptografiset avaimet FIPS 140-2 -tason 3 tai Common Criteria EAL4+ -sertifikaatin mukaisesti.

---

### C4.12 Reuna- ja hajautettu tekoälyinfrastruktuuri

Turvalliset hajautetut tekoälyn käyttöönotot, mukaan lukien reunalaskenta, yhdistetty oppiminen ja monipaikka-arkkitehtuurit.

 #4.12.1    Taso: 2    Rooli: D/V
 Varmista, että reunatason AI-laitteet todennetaan keskusinfrastruktuuriin käyttämällä kaksisuuntaista TLS:ää laitetodistuksilla, joita kierrätetään organisaation sertifikaattien hallintakäytännön mukaisesti.
 #4.12.2    Taso: 2    Rooli: D/V
 Varmista, että reunalaitteet toteuttavat suojatun käynnistyksen varmennetuilla allekirjoituksilla ja takaisinperuuntumissuojauksella, joka estää laiteohjelmiston alennushyökkäykset.
 #4.12.3    Taso: 3    Rooli: D/V
 Varmista, että hajautettu tekoälyn koordinointi käyttää bysanttilaisviankestäviä konsensusalgoritmeja osallistujien vahvistuksella ja haitallisten solmujen havaitsemisella.
 #4.12.4    Taso: 3    Rooli: D/V
 Varmista, että reunalaitteen ja pilven välinen viestintä sisältää kaistanleveyden rajoituksen, tiedon pakkaamisen ja offline-toimintamahdollisuudet turvallisella paikallisella tallennuksella.

---

### C4.13 Monipilvi- ja hybridiratkaisujen infrastruktuurin turvallisuus

Varmista tekoälysovellusten turvallisuus useiden pilvipalveluntarjoajien sekä hybridipilvi- ja paikallisympäristöjen käyttöönotossa.

 #4.13.1    Taso: 2    Rooli: D/V
 Varmista, että monipilvi- tekoälyn käyttöönotot käyttävät pilviriippumatonta identiteettifederaatiota (OIDC, SAML) keskitetyn politiikan hallinnan kanssa eri tarjoajien välillä.
 #4.13.2    Taso: 2    Rooli: D/V
 Varmista, että pilvienvälinen tiedonsiirto käyttää päästä päähän -salauksen, jossa avaimet hallitaan asiakkaan toimesta, ja että tietojen sijaintisäännökset toteutetaan lainkäyttöalueittain.
 #4.13.3    Taso: 2    Rooli: D/V
 Varmista, että hybridipilvi-Tekoälytyökuormat toteuttavat yhtenäiset tietoturvakäytännöt paikallisissa ja pilviympäristöissä yhtenäisellä valvonnalla ja hälytyksillä.
 #4.13.4    Taso: 3    Rooli: V
 Varmista, että pilvipalveluntarjoajan lukituksen estäminen sisältää siirrettävän infrastruktuuri-koodina, standardoidut API:t ja tietojen vientimahdollisuudet muunnostyökaluineen.
 #4.13.5    Taso: 3    Rooli: V
 Varmista, että monipilvikustannusten optimointi sisältää tietoturvakontrollit, jotka estävät resurssien leviämisen sekä luvattomat pilvienväliset datansiirtomaksut.

---

### C4.14 Infrastruktuurin automaatio ja GitOps-tietoturva

Turvaa infrastruktuurin automaatio-putket ja GitOps-työnkulut tekoälyinfrastruktuurin hallintaa varten.

 #4.14.1    Taso: 2    Rooli: D/V
 Varmista, että GitOps-varastoissa vaaditaan allekirjoitettuja committeja GPG-avaimilla ja että haara-suojaussäännöt estävät suorat pushit päähaaroihin.
 #4.14.2    Taso: 2    Rooli: D/V
 Varmista, että infrastruktuurin automaatio sisältää poikkeamien tunnistuksen automaattisella korjauksella ja palautusmahdollisuuksilla, jotka laukaistaan organisaation vastausvaatimusten mukaisesti luvattomien muutosten yhteydessä.
 #4.14.3    Taso: 2    Rooli: D/V
 Varmista, että automatisoitu infrastruktuurin käyttöönotto sisältää turvallisuuspolitiikan validoinnin ja estää käyttöönoton, jos kokoonpano ei ole vaatimusten mukainen.
 #4.14.4    Taso: 2    Rooli: D/V
 Varmista, että infrastruktuurin automaation salaisuuksia hallinnoidaan ulkoisten salaisuuksien operaattoreiden (External Secrets Operator, Bank-Vaults) kautta automaattisella kierrätyksellä.
 #4.14.5    Taso: 3    Rooli: V
 Varmista, että itseparantuva infrastruktuuri sisältää turvallisuustapahtumien korrelaation automaattisen tapahtumavasteen ja sidosryhmien ilmoitusprosessien kanssa.

---

### C4.15 Kvanttivarma infrastruktuurin turvallisuus

Valmistele tekoälyn infrastruktuuri kvanttilaskennan uhkia varten postkvanttikryptografian ja kvanttiturvallisten protokollien avulla.

 #4.15.1    Taso: 3    Rooli: D/V
 Varmista, että tekoälyn infrastruktuuri toteuttaa NISTin hyväksymiä kvanttiturvallisia kryptografisia algoritmeja (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) avaintenvaihtoon ja digitaalisille allekirjoituksille.
 #4.15.2    Taso: 3    Rooli: D/V
 Varmista, että kvanttivakiojakaumajärjestelmät (QKD) on toteutettu korkean turvallisuuden tekoälyn viestintään kvanttiturvallisilla avaintenhallintaprotokollilla.
 #4.15.3    Taso: 3    Rooli: D/V
 Varmista, että kryptografisen ketteryyden kehykset mahdollistavat nopean siirtymisen uusiin postkvanttialgoritmeihin automatisoidulla varmenteiden ja avainten kierrätyksellä.
 #4.15.4    Taso: 3    Rooli: V
 Varmista, että kvanttivaaramallinnus arvioi tekoälyinfrastruktuurin haavoittuvuutta kvanttihyökkäyksille dokumentoitujen siirtymäaikataulujen ja riskinarviointien avulla.
 #4.15.5    Taso: 3    Rooli: D/V
 Varmista, että hybridi klassinen- ja kvanttikryptografinen järjestelmä tarjoaa monikerroksisen suojan kvanttisiirtymäkauden aikana suorituskyvyn seurannalla.

---

### C4.16 Luottamuksellinen laskenta ja suojatut alueet

Suojaa tekoälyn työkuormia ja mallipainoja laitteistopohjaisten luotettavien suoritusympäristöjen ja luottamuksellisen laskennan teknologioiden avulla.

 #4.16.1    Taso: 3    Rooli: D/V
 Varmista, että arkaluonteiset tekoälymallit suoritetaan Intel SGX -alueiden, AMD SEV-SNP:n tai ARM TrustZonen sisällä käyttäen salattua muistia ja varmennustarkistusta.
 #4.16.2    Taso: 3    Rooli: D/V
 Varmista, että luottamukselliset kontit (Kata Containers, gVisor luottamuksellisen laskennan kanssa) eristävät tekoälytyökuormat laitteistopohjaisella muistisalausmenetelmällä.
 #4.16.3    Taso: 3    Rooli: D/V
 Varmista, että etätodentaminen vahvistaa kehysalueen eheyttä ennen tekoälymallien lataamista tarjoamalla kryptografisen todisteen suoritusalustan aitoudesta.
 #4.16.4    Taso: 3    Rooli: D/V
 Varmista, että luottamukselliset tekoälyn päättelypalvelut estävät mallin kopioinnin salatun laskennan avulla, jossa mallipainot ovat suojattuina ja suoritus suojatussa ympäristössä.
 #4.16.5    Taso: 3    Rooli: D/V
 Varmista, että luotettavan suoritusympäristön orkestrointi hallitsee turvallisen saarekkeen elinkaaren etätodennuksella ja salatuilla viestintäkanavilla.
 #4.16.6    Taso: 3    Rooli: D/V
 Varmista, että turvallinen moniosapuolilaskenta (SMPC) mahdollistaa yhteistyöperusteisen tekoälyn koulutuksen paljastamatta yksittäisiä aineistoja tai mallin parametreja.

---

### C4.17 Nollatietoinen infrastruktuuri

Toteuta nollatietotodistusjärjestelmät yksityisyyttä suojaavaa tekoälyn varmennusta ja todentamista varten paljastamatta arkaluonteisia tietoja.

 #4.17.1    Taso: 3    Rooli: D/V
 Varmista, että nollatietotodistukset (ZK-SNARKit, ZK-STARKit) todentavat tekoälymallin eheyden ja koulutuksen alkuperän paljastamatta kuitenkaan mallin painoja tai koulutusdataa.
 #4.17.2    Taso: 3    Rooli: D/V
 Varmista, että ZK-pohjaiset todennusjärjestelmät mahdollistavat yksityisyyttä suojaavan käyttäjien vahvistamisen tekoälypalveluissa paljastamatta henkilöllisyyteen liittyviä tietoja.
 #4.17.3    Taso: 3    Rooli: D/V
 Varmista, että yksityinen joukkojen leikkaus (PSI) -protokolla mahdollistaa turvallisen tietojen vertailun hajautetussa tekoälyssä paljastamatta yksittäisiä tietojoukkoja.
 #4.17.4    Taso: 3    Rooli: D/V
 Varmista, että nollatietoinen koneoppiminen (ZKML) -järjestelmät mahdollistavat todennettavien tekoälypäätösten tekemisen kryptografisella todistuksella oikeasta laskennasta.
 #4.17.5    Taso: 3    Rooli: D/V
 Varmista, että ZK-rollupit tarjoavat skaalautuvan, yksityisyyttä suojaavan tekoäly-tapahtumien käsittelyn erävarmennuksella ja vähennetyllä laskennallisella kuormituksella.

---

### C4.18 Sivukanavan hyökkäysten estäminen

Suojaa tekoälyinfrastruktuuri ajoitus-, teho-, sähkömagneettisilta ja välimuistipohjaisilta sivukanavahyökkäyksiltä, jotka voisivat vuotaa arkaluonteisia tietoja.

 #4.18.1    Taso: 3    Rooli: D/V
 Varmista, että tekoälyn päätelmän ajoitus on normalisoitu käyttämällä vakioaikaisia algoritmeja ja täytettä estämään ajoitukseen perustuvat mallin poiminta-iskut.
 #4.18.2    Taso: 3    Rooli: D/V
 Varmista, että tehoanalyysin suojaus sisältää kohinan lisäämisen, virtalinjan suodatuksen ja satunnaistetut suorituskuviot AI-laitteistolle.
 #4.18.3    Taso: 3    Rooli: D/V
 Varmista, että välimuistiin perustuva sivukanavahäirinnän estäminen käyttää välimuistin jakamista, satunnaistamista ja tyhjennyskäskyjä estämään tietovuotoja.
 #4.18.4    Taso: 3    Rooli: D/V
 Varmista, että sähkömagneettisten säteilyjen suojaus sisältää suojauksen, signaalisuodatuksen ja satunnaistetun käsittelyn estämään TEMPEST-tyylisiä hyökkäyksiä.
 #4.18.5    Taso: 3    Rooli: D/V
 Varmista, että mikroarkkitehtuuriset sivukanavien puolustukset sisältävät spekulatiivisen suorituksen ohjauksen ja muistinkäytön kuvion peittauksen.

---

### C4.19 Neuromorfinen ja erikoistunut tekoälyn laitteistoturvallisuus

Turvaa uusia tekoälyn laitteistoarkkitehtuureja, kuten neuromorfiset sirut, FPGA:t, räätälöidyt ASIC-piirit ja optiset laskentajärjestelmät.

 #4.19.1    Taso: 3    Rooli: D/V
 Varmista, että neuromorfisen sirun turvallisuus sisältää piikkikuvion salauksen, synaptisen painon suojauksen ja laitteistopohjaisen oppimissäännön vahvistuksen.
 #4.19.2    Taso: 3    Rooli: D/V
 Varmista, että FPGA-pohjaiset tekoälykiihdyttimet toteuttavat bitstream-salauksen, manipulointisuojausmekanismit ja turvallisen konfiguroinnin latauksen todennetuilla päivityksillä.
 #4.19.3    Taso: 3    Rooli: D/V
 Varmista, että mukautetun ASIC-turvallisuuden ominaisuuksiin kuuluvat piirin sisäiset turvallisuusprosessorit, laitteistopohjainen luottamusperusta ja turvallinen avainten tallennus, jossa on manipuloinnin havaitseminen.
 #4.19.4    Taso: 3    Rooli: D/V
 Varmista, että optiset laskentajärjestelmät toteuttavat kvanttiturvallisen optisen salauksen, suojatun fotonisen kytkennän ja suojatun optisen signaalinkäsittelyn.
 #4.19.5    Taso: 3    Rooli: D/V
 Varmista, että hybridi analogis-digitaaliset AI-piirit sisältävät turvallisen analogisen laskennan, suojatun painotetun tallennuksen ja todennetun analogi-digitaalisen muunnoksen.

---

### C4.20 Yksityisyyttä säilyttävä laskenta-infrastruktuuri

Ota käyttöön infrastruktuurin valvontatoimet yksityisyyttä suojaavaa laskentaa varten suojellaksesi arkaluontoisia tietoja AI-käsittelyn ja analyysin aikana.

 #4.20.1    Taso: 3    Rooli: D/V
 Varmista, että homomorfinen salausinfrastruktuuri mahdollistaa salatun laskennan arkaluontoisissa tekoälykuormissa käyttäen kryptograafista eheystarkistusta ja suorituskyvyn valvontaa.
 #4.20.2    Taso: 3    Rooli: D/V
 Varmista, että yksityisen tiedon hakujärjestelmät mahdollistavat tietokantahaut paljastamatta hakukuvioita ja käyttävät salausmenetelmiä käyttökuvioiden suojaamiseksi.
 #4.20.3    Taso: 3    Rooli: D/V
 Varmista, että turvalliset moniosapuoletoteutusprotokollat mahdollistavat yksityisyyttä suojaavan tekoälyn päättelemisen paljastamatta yksittäisiä syötteitä tai välivaiheen laskelmia.
 #4.20.4    Taso: 3    Rooli: D/V
 Varmista, että yksityisyyttä suojaava avainhallinta sisältää hajautetun avainluonnin, kynnyskriptografian ja turvallisen avainten kierrätyksen laitteistopohjaisella suojauksella.
 #4.20.5    Taso: 3    Rooli: D/V
 Varmista, että yksityisyyttä säilyttävän laskennan suorituskyky on optimoitu yhdistämällä eräajo, välimuistitallennus ja laitteistokiihdytys samalla kun säilytetään kryptografiset turvallisuuslupaukset.

---

### C4.15 Agenttikehys Pilvipalvelun integroinnin turvallisuus ja hybridi käyttöönotto

Turvallisuusvalvontamekanismit pilveen integroiduille agenttikehyksille hybridiä on-premises/pilvi-arkkitehtuuria varten.

 #4.15.1    Taso: 1    Rooli: D/V
 Varmista, että pilvitallennuksen integraatio käyttää päästä-päähän -salausta agentin hallitsemalla avainhallinnalla.
 #4.15.2    Taso: 2    Rooli: D/V
 Varmista, että hybridiasennuksen suojausrajat on selkeästi määritelty ja että viestintäkanavat ovat salattuja.
 #4.15.3    Taso: 2    Rooli: D/V
 Varmista, että pilviresurssien käyttö sisältää nollaluottamuksen varmennuksen jatkuvalla todentamisella.
 #4.15.4    Taso: 3    Rooli: D/V
 Varmista, että tietojen sijaintia koskevia vaatimuksia noudatetaan salauksellisten todistusten avulla tallennuspaikoista.
 #4.15.5    Taso: 3    Rooli: D/V
 Varmista, että pilvipalveluntarjoajan tietoturva-arvioinnit sisältävät agenttikohtaisen uhkamallinnuksen ja riskinarvioinnin.

---

### Viitteet

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

## C5 Käyttöoikeuksien hallinta ja identiteetti AI-komponenteille ja -käyttäjille

### Ohjaustavoite

Tehokas pääsynhallinta tekoälyjärjestelmissä vaatii vahvaa identiteetin hallintaa, kontekstin huomioon ottavaa valtuutusta ja suoritusaikaisen valvonnan noudattaen nollaluottamusperiaatteita. Nämä hallintamekanismit varmistavat, että ihmiset, palvelut ja autonomiset agentit ovat vuorovaikutuksessa mallien, datan ja laskentaresurssien kanssa vain selkeästi määritellyillä käyttöalueilla, jatkuvalla tarkistuksella ja auditointimahdollisuuksilla.

---

### C5.1 Identiteetin hallinta ja todennus

Perusta kryptografisesti varmennetut identiteetit kaikille yksiköille monivaiheisella todennuksella valtuutettuja toimintoja varten.

 #5.1.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki ihmiset käyttäjät ja palveluperiaatteet todentuvat keskitetyn yrityksen identiteetin tarjoajan (IdP) kautta käyttäen OIDC/SAML-protokollia ainutlaatuisilla identiteetistä tokeniin kartoittamisilla (ei jaettuja tilejä tai tunnistetietoja).
 #5.1.2    Taso: 1    Rooli: D/V
 Varmista, että korkean riskin toiminnot (mallin käyttöönotto, painojen vienti, koulutusdatan käyttöoikeus, tuotantoympäristön konfiguraatiomuutokset) vaativat monivaiheisen tunnistautumisen tai vahvistustason korotuksen istunnon uudelleenvahvistuksella.
 #5.1.3    Taso: 2    Rooli: D
 Varmista, että uudet pääkäyttäjät käyvät läpi henkilöllisyyden todentamisen, joka vastaa NIST 800-63-3 IAL-2 -standardia tai vastaavia vaatimuksia ennen tuotantojärjestelmän käyttöoikeuden saamista.
 #5.1.4    Taso: 2    Rooli: V
 Varmista, että käyttöoikeuksien tarkastukset suoritetaan neljännesvuosittain automatisoidun lepotilassa olevien tilien havaitsemisen, tunnistetietojen kierrätyksen valvonnan ja poistoprosessien avulla.
 #5.1.5    Taso: 3    Rooli: D/V
 Varmista, että yhdistetyt tekoälyagentit todentuvat allekirjoitettujen JWT-väitteiden kautta, joiden enimmäiskesto on 24 tuntia ja jotka sisältävät kryptografisen alkuperätodistuksen.

---

### C5.2 Resurssien valtuutus ja vähimmäisoikeudet

Toteuta hienojakoiset käyttöoikeusvalvonnat kaikille tekoälyresursseille selkeillä lupaamalleilla ja auditointilokeilla.

 #5.2.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen tekoälyresurssi (aineistot, mallit, päätepisteet, vektorikokoelmat, upotushakemistot, laskenta-instanssit) käyttää roolipohjaista pääsynvalvontaa, jossa on eksplisiittiset sallitut listat ja oletusarvoiset kieltoasetukset.
 #5.2.2    Taso: 1    Rooli: D/V
 Varmista, että vähimmän etuoikeuden periaatteet otetaan käyttöön oletuksena palvelutilien osalta, aloittaen vain luku -oikeuksilla, ja että kirjoitusoikeuksille vaaditaan dokumentoitu liiketoiminnan perustelu.
 #5.2.3    Taso: 1    Rooli: V
 Varmista, että kaikki käyttöoikeuksien muutokset liittyvät hyväksyttyihin muutospyyntöihin ja ne kirjataan muuttumattomasti aikaleimojen, tekijäidentiteettien, resurssitunnisteiden ja käyttöoikeuspoikkeamien kera.
 #5.2.4    Taso: 2    Rooli: D
 Varmista, että tietoluokitusmerkinnät (HENKILÖTIEDOT, POTILASTIEDOT, vientivalvottu, luottamuksellinen) leviävät automaattisesti johdettuihin resursseihin (upotukset, kehotemuistit, mallin tulokset) johdonmukaisesti politiikan noudattamisen kanssa.
 #5.2.5    Taso: 2    Rooli: D/V
 Varmista, että luvattomat pääsyyritykset ja oikeuksien eskalointitapahtumat laukaisevat reaaliaikaiset hälytykset kontekstuaalisen metadatan kanssa SIEM-järjestelmiin 5 minuutin sisällä.

---

### C5.3 Dynaaminen politiikan arviointi

Ota käyttöön attribuutteihin perustuvat pääsynvalvontamoottorit (ABAC) kontekstia tunnistavia valtuutuspäätöksiä varten, joissa on auditointimahdollisuudet.

 #5.3.1    Taso: 1    Rooli: D/V
 Varmista, että valtuutuspäätökset on ulkoistettu omistetulle politiikkamoottorille (OPA, Cedar tai vastaava), johon pääsee käsiksi todennettujen API-rajapintojen kautta, joissa on kryptografinen eheys suojaus.
 #5.3.2    Taso: 1    Rooli: D/V
 Varmista, että politiikat arvioivat dynaamisia attribuutteja ajonaikaisesti, mukaan lukien käyttäjän pääsyoikeustaso, resurssin herkkyysluokitus, pyyntöympäristö, vuokralaiseristys ja ajalliset rajoitukset.
 #5.3.3    Taso: 2    Rooli: D
 Varmista, että politiikan määritelmät ovat versionhallinnan alaisia, vertaisarvioituja ja validoituja automaattisten testien avulla CI/CD-putkistoissa ennen tuotantoon käyttöönottoa.
 #5.3.4    Taso: 2    Rooli: V
 Varmista, että politiikan arvioinnin tulokset sisältävät jäsennellyt päätöksentekosisällöt ja ne välitetään SIEM-järjestelmille korrelaatioanalyysiä ja vaatimustenmukaisuusraportointia varten.
 #5.3.5    Taso: 3    Rooli: D/V
 Varmista, että politiikan välimuistin elinaika-arvot (TTL) eivät ylitä 5 minuuttia korkean herkkyyden resursseille ja 1 tuntia vakiovarastoresursseille, joilla on välimuistin mitätöintiominaisuudet.

---

### C5.4 Kyselyajan turvallisuuden valvonta

Ota käyttöön tietokantakerroksen turvatoimet pakollisella suodatuksella ja rivikohtaisilla suojauspolitiikoilla.

 #5.4.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki vektoritietokannan ja SQL-kyselyt sisältävät pakolliset tietoturvasuodattimet (vuokraajan tunnus, herkkyysluokat, käyttäjän käyttöoikeudet), jotka toteutetaan tietokantamoottorin tasolla, ei sovelluskoodissa.
 #5.4.2    Taso: 1    Rooli: D/V
 Varmista, että rivitason turvallisuuspolitiikat (RLS) ja kenttätason naamiointi ovat käytössä politiikan periytymisen kanssa kaikissa vektoritietokannoissa, hakemistoissa ja koulutusdatoissa.
 #5.4.3    Taso: 2    Rooli: D
 Varmista, että epäonnistuneet valtuutustarkastukset estävät "sekaantuneen edustajan hyökkäykset" keskeyttämällä haut välittömästi ja palauttamalla selkeät valtuutusvirhekoodit tyhjien tulosjoukkojen palauttamisen sijaan.
 #5.4.4    Taso: 2    Rooli: V
 Varmista, että käytäntöjen arviointiviivettä seurataan jatkuvasti automaattisilla hälytyksillä aikakatkaisuehtojen varalta, jotka voisivat mahdollistaa valtuutuksen ohittamisen.
 #5.4.5    Taso: 3    Rooli: D/V
 Varmista, että kyselyn uudelleenyrittomekanismit arvioivat valtuutuspolitiikat uudelleen ottaen huomioon dynaamiset käyttöoikeusmuutokset aktiivisten käyttäjäistuntojen aikana.

---

### C5.5 Tulosteen suodatus ja tiedonmenetyksen ehkäisy

Ota käyttöön jälkikäsittelyn valvontamekanismit estääksesi luvattoman tietojen paljastumisen tekoälyn generoimassa sisällössä.

 #5.5.1    Taso: 1    Rooli: D/V
 Varmista, että jälkijohdantasuodatusmekanismit tarkistavat ja sensuroivat luvattoman henkilötunnistetiedon (PII), luokitellun tiedon ja oman aineiston ennen sisällön toimittamista pyytäjille.
 #5.5.2    Taso: 1    Rooli: D/V
 Varmista, että mallin tuottamien sitaattien, viitteiden ja lähdeviittausten oikeellisuus tarkistetaan kutsujan oikeuksien mukaisesti, ja ne poistetaan, jos luvaton pääsy havaitaan.
 #5.5.3    Taso: 2    Rooli: D
 Varmista, että tulostemuotojen rajoitukset (puhdistetut PDF-tiedostot, metatiedot poistettu kuvista, hyväksytyt tiedostotyypit) toteutetaan käyttäjän käyttöoikeustasojen ja dataluokitusten perusteella.
 #5.5.4    Taso: 2    Rooli: V
 Varmista, että sensurointialgoritmit ovat deterministisiä, versiohallittuja ja säilyttävät tarkastuslokit tukemaan vaatimustenmukaisuustutkimuksia ja oikeuslääketieteellisiä analyyseja.
 #5.5.5    Taso: 3    Rooli: V
 Varmista, että korkean riskin peittotapahtumat luovat adaptiivisia lokitietoja, jotka sisältävät alkuperäisen sisällön kryptografiset tiivisteet oikeustieteellistä palautusta varten ilman tietojen paljastumista.

---

### C5.6 Monivuokralais-eristys

Varmista kryptografinen ja looginen eristys käyttäjien välillä jaetussa tekoälyinfrastruktuurissa.

 #5.6.1    Taso: 1    Rooli: D/V
 Varmista, että muistitilat, upotusten tallennustilat, välimuistimerkinnät ja väliaikaiset tiedostot ovat nimialueittain eroteltuja vuokralaisittain, ja että vuokralaisen poistamisen tai istunnon päättämisen yhteydessä suoritetaan turvallinen puhdistus.
 #5.6.2    Taso: 1    Rooli: D/V
 Varmista, että jokainen API-pyyntö sisältää todennetun vuokralaisidentifikaattorin, joka on kryptografisesti validoitu istuntokontekstin ja käyttäjän käyttöoikeuksien perusteella.
 #5.6.3    Taso: 2    Rooli: D
 Varmista, että verkkopolitiikat toteuttavat oletusarvoisesti estävät säännöt monivuokralaisten väliselle viestinnälle palveluverkkojen ja konttien orkestrointialustojen sisällä.
 #5.6.4    Taso: 3    Rooli: D
 Varmista, että salausavaimet ovat uniikkeja kullekin vuokralaiselle asiakas hallinnoidun avaimen (CMK) tuella ja että vuokralaisten tietovarastojen välillä on kryptografinen eristys.

---

### C5.7 Autonomisen agentin valtuutus

Ohjaoikeudet AI-agentteihin ja autonomisiin järjestelmiin laajennettujen käyttöoikeustunnusten ja jatkuvan valtuutuksen avulla.

 #5.7.1    Taso: 1    Rooli: D/V
 Varmista, että autonomiset agentit saavat rajatut valtuustunnukset, jotka yksilöivät nimenomaisesti sallitut toiminnot, käytettävissä olevat resurssit, aikarajat ja toimintarajoitukset.
 #5.7.2    Taso: 1    Rooli: D/V
 Varmista, että korkean riskin toiminnot (tiedostojärjestelmän käyttö, koodin suoritus, ulkoiset API-kutsut, taloudelliset siirrot) ovat oletuksena poissa käytöstä ja edellyttävät nimenomaisia hyväksyntöjä aktivoitumista varten liiketoiminnallisilla perusteluilla.
 #5.7.3    Taso: 2    Rooli: D
 Varmista, että käyttöoikeustunnukset on sidottu käyttäjäistuntoihin, niissä on kryptografinen eheysturva, eikä niitä voi säilyttää tai käyttää uudelleen offline-tilanteissa.
 #5.7.4    Taso: 2    Rooli: V
 Varmista, että agentin aloittamat toimenpiteet käyvät läpi toissijaisen hyväksynnän ABAC-politiikkamoottorin kautta täydellisen kontekstin arvioinnin ja tarkastuslokiauditoinnin kanssa.
 #5.7.5    Taso: 3    Rooli: V
 Varmista, että agentin virhetilanteet ja poikkeusten käsittely sisältävät kyvykkyysalueen tiedot tukemaan tapahtumien analysointia ja oikeuslääketieteellistä tutkimusta.

---

### Viitteet

#### Standardit ja kehykset

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Toteutusoppaat

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### AI-spesifinen turvallisuus

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Toimitusketjun turvallisuus malleille, kehyksille ja tiedoille

### Ohjaustavoite

AI-toimitusketjun hyökkäykset hyödyntävät kolmannen osapuolen malleja, kehyksiä tai aineistoja takaporttien, vinoumien tai hyväksikäytettävän koodin upottamiseen. Nämä valvontatoimet tarjoavat alusta loppuun jäljitettävyyden, haavoittuvuuksien hallinnan ja valvonnan koko mallin elinkaaren suojaamiseksi.

---

### C6.1 Esikoulutetun mallin arviointi ja alkuperä

Arvioi ja vahvista kolmannen osapuolen mallien alkuperä, lisenssit ja piilotetut käyttäytymismallit ennen hienosäätöä tai käyttöönottoa.

 #6.1.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen kolmannen osapuolen mallin artefakti sisältää allekirjoitetun alkuperätietueen, jossa on tunnistettu lähderekisteri ja commit-tunniste.
 #6.1.2    Taso: 1    Rooli: D/V
 Varmista, että mallit tarkastetaan haitallisten kerrosten tai Troijan laukaisijoiden varalta automatisoiduilla työkaluilla ennen niiden tuontia.
 #6.1.3    Taso: 2    Rooli: D
 Varmista, että siirto-oppiminen hienosäätää mallit siten, että ne läpäisevät hyökkäystestauksen havaitakseen piilotetut käyttäytymismallit.
 #6.1.4    Taso: 2    Rooli: V
 Varmista, että mallilisenssit, vientivalvontatunnisteet ja datan alkuperää koskevat lausunnot on kirjattu ML-BOM-kohteeseen.
 #6.1.5    Taso: 3    Rooli: D/V
 Varmista, että korkean riskin mallit (julkisesti ladatut painot, varmennamattomat luojat) pysyvät karanteenissa ihmisen tekemään tarkastukseen ja hyväksyntään asti.

---

### C6.2 Kehys- ja kirjastojen skannaus

Skannaa jatkuvasti ML-kehykset ja kirjastot CVE-haavoittuvuuksien ja haitallisen koodin varalta pitämään ajonaikainen pino turvallisena.

 #6.2.1    Taso: 1    Rooli: D/V
 Varmista, että CI-putket suorittavat riippuvuusskannereita tekoälykehysten ja kriittisten kirjastojen kohdalla.
 #6.2.2    Taso: 1    Rooli: D/V
 Varmista, että kriittiset haavoittuvuudet (CVSS ≥ 7.0) estävät päivityksen tuotantokuviksi.
 #6.2.3    Taso: 2    Rooli: D
 Varmista, että staattinen koodianalyysi suoritetaan haara- tai mukana toimitetuille koneoppimiskirjastoille.
 #6.2.4    Taso: 2    Rooli: V
 Varmista, että kehysupgrade-ehdotukset sisältävät tietoturvan vaikutusten arvioinnin, joka viittaa julkisiin CVE-syötteisiin.
 #6.2.5    Taso: 3    Rooli: V
 Varmista, että ajonaikaiset anturit hälyttävät odottamattomista dynaamisista kirjastojen latauksista, jotka poikkeavat allekirjoitetusta SBOM:sta.

---

### C6.3 Riippuvuuksien lukitseminen ja varmennus

Kiinnitä kaikki riippuvuudet muuttumattomiin tiivisteisiin ja toista käännökset varmistaaksesi identtiset, muokkaamattomat artefaktit.

 #6.3.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki pakettienhallintaohjelmat pakottavat version lukituksen lukitustiedostojen kautta.
 #6.3.2    Taso: 1    Rooli: D/V
 Varmista, että konttiviitteissä käytetään muuttumattomia tiivisteitä muuttuvien tunnisteiden sijaan.
 #6.3.3    Taso: 2    Rooli: D
 Varmista, että toistettavat rakennustarkistukset vertaavat hajautusarvoja CI-ajojen välillä identtisten tulosten varmistamiseksi.
 #6.3.4    Taso: 2    Rooli: V
 Varmista, että rakennusvakuutukset säilytetään 18 kuukautta auditointijäljityksen varmistamiseksi.
 #6.3.5    Taso: 3    Rooli: D
 Varmista, että vanhentuneet riippuvuudet laukaisevat automaattiset PR:t päivittääksesi tai haaroittaaksesi kiinnitetyt versiot.

---

### C6.4 Luotettavan lähteen valvonta

Salli artefaktien lataukset vain kryptografisesti varmennetuista, organisaation hyväksymistä lähteistä ja estä kaikki muu.

 #6.4.1    Taso: 1    Rooli: D/V
 Varmista, että mallipainot, tietojoukot ja kontit ladataan vain hyväksytyiltä verkkotunnuksilta tai sisäisistä rekistereistä.
 #6.4.2    Taso: 1    Rooli: D/V
 Varmista, että Sigstore/Cosign-allekirjoitukset vahvistavat julkaisijan identiteetin ennen kuin artefaktit tallennetaan paikallisesti välimuistiin.
 #6.4.3    Taso: 2    Rooli: D
 Varmista, että ulospäin suuntautuvat välityspalvelimet estävät todennuksettomat artefaktien lataukset luotetun lähdepolitiikan noudattamiseksi.
 #6.4.4    Taso: 2    Rooli: V
 Varmista, että arkistoluettelot tarkistetaan neljännesvuosittain ja että jokaiselle merkinnälle on liiketoiminnallinen perustelu.
 #6.4.5    Taso: 3    Rooli: V
 Varmista, että politiikan rikkomukset laukaisevat artefaktien karanteenin ja riippuvien putkistosuoritusten palautuksen.

---

### C6.5 Kolmannen osapuolen tietojoukkoa koskeva riskinarviointi

Arvioi ulkoiset tietoaineistot myrkyllisyyden, harhan ja laillisen vaatimustenmukaisuuden osalta ja valvo niitä koko niiden elinkaaren ajan.

 #6.5.1    Taso: 1    Rooli: D/V
 Varmista, että ulkoiset tietojoukot käyvät läpi myrkytysriskiarvioinnin (esim. datansormenjälkien luonti, poikkeavien arvojen havaitseminen).
 #6.5.2    Taso: 1    Rooli: D
 Varmista, että puolueellisuusmittarit (demografinen tasapuolisuus, yhtäläinen mahdollisuus) lasketaan ennen tietojoukon hyväksyntää.
 #6.5.3    Taso: 2    Rooli: V
 Varmista, että tietojoukkeiden alkuperä ja lisenssiehdot on tallennettu ML-BOM-tietoihin.
 #6.5.4    Taso: 2    Rooli: V
 Varmista, että säännöllinen seuranta havaitsee muutokset tai vääristymät isännöidyissä tietoaineistoissa.
 #6.5.5    Taso: 3    Rooli: D
 Varmista, että kielletty sisältö (tekijänoikeudet, henkilötunnistetiedot) poistetaan automaattisella puhdistuksella ennen koulutusta.

---

### C6.6 Toimitusketjun hyökkäysten seuranta

Havaitse toimitusketjun uhkat varhain CVE-syötteiden, tarkastuslokianalytiikan ja red-tiimin simulaatioiden avulla.

 #6.6.1    Taso: 1    Rooli: V
 Varmista, että CI/CD-tarkastuslokit virtaavat SIEM-havaintoihin epätavallisten paketinkuittausten tai muunneltujen rakennusvaiheiden havaitsemiseksi.
 #6.6.2    Taso: 2    Rooli: D
 Varmista, että tapahtumien käsittelyohjeissa on mukana palautusmenettelyt vaarantuneille malleille tai kirjastoille.
 #6.6.3    Taso: 3    Rooli: V
 Varmista, että uhkatiedon rikastustunnisteet merkitsevät ML-spesifiset indikaattorit (esim. mallin myrkytys IoC:t) hälytyksen seulonnassa.

---

### C6.7 ML‑BOM mallin artefakteille

Luo ja allekirjoita yksityiskohtaiset koneoppimiseen liittyvät SBOM:t (ML-BOM:t), jotta loppukäyttäjät voivat varmistaa komponenttien eheyden käyttöönoton yhteydessä.

 #6.7.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen mallin artefakti julkaisee ML-BOM:n, joka sisältää luettelon aineistoista, painoista, hyperparametreista ja lisensseistä.
 #6.7.2    Taso: 1    Rooli: D/V
 Varmista, että ML-BOM:n luonti ja Cosign-allekirjoitus ovat automatisoituja CI:ssä ja pakollisia merge-yhdistämiselle.
 #6.7.3    Taso: 2    Rooli: D
 Varmista, että ML‑BOM:n täydellisyystarkistukset epäonnistavat käännön, jos jokin komponentin metatiedoista (hash, lisenssi) puuttuu.
 #6.7.4    Taso: 2    Rooli: V
 Varmista, että alavirran käyttäjät voivat kysellä ML-BOM:eja API:n kautta validoidakseen tuotavat mallit käyttöönoton yhteydessä.
 #6.7.5    Taso: 3    Rooli: V
 Varmista, että ML-BOMit ovat versionhallinnassa ja muutokset vertaillaan luvattomien muokkausten havaitsemiseksi.

---

### Viitteet

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

## C7-mallin käyttäytyminen, tuoton hallinta ja turvallisuuden varmistaminen

### Ohjaustavoite

Mallin tuotosten on oltava jäsenneltyjä, luotettavia, turvallisia, selitettäviä ja jatkuvasti valvottuja tuotantoympäristössä. Näin vähennetään harhoja, yksityisyyden vuotoja, haitallista sisältöä ja hallitsemattomia toimintoja sekä lisätään käyttäjien luottamusta ja sääntelyvaatimusten noudattamista.

---

### C7.1 Tulostemuodon noudattamisen varmistaminen

Tiukat skeemat, rajoitettu dekoodaus ja jälkikäteinen validointi estävät virheellisen tai haitallisen sisällön leviämisen.

 #7.1.1    Taso: 1    Rooli: D/V
 Varmista, että vastauskaavat (esim. JSON Schema) on annettu järjestelmäkehotteessa ja että jokainen lähtö validoidaan automaattisesti; muotoiltumattomat tulosteet aiheuttavat korjauksen tai hylkäyksen.
 #7.1.2    Taso: 1    Rooli: D/V
 Varmista, että rajoitettu dekoodaus (stop-tokenit, regex, maksimimäärä tokeneita) on käytössä ylivuodon tai kehotteen manipuloinnin sivukanavien estämiseksi.
 #7.1.3    Taso: 2    Rooli: D/V
 Varmista, että jälkikomponentit käsittelevät tulosteita epäluotettavina ja validoivat ne skeemojen tai injektioilta suojattujen de-serialisoijien avulla.
 #7.1.4    Taso: 3    Rooli: V
 Varmista, että virheelliset tulostustapahtumat kirjataan, rajoitetaan esiintymistiheydeltään ja tuodaan esiin valvonnassa.

---

### C7.2 Hallusinaation tunnistus ja lieventäminen

Epävarmuuden arviointi ja varasuunnitelmat hillitsevät keksittyjä vastauksia.

 #7.2.1    Taso: 1    Rooli: D/V
 Varmista, että token-tason log-todennäköisyydet, ensemble-itsejohdonmukaisuus tai hienosäädetyt harhanilmaisimet antavat luottamuspisteen jokaiselle vastaukselle.
 #7.2.2    Taso: 1    Rooli: D/V
 Varmista, että vastaukset, joiden luottamustaso on alle määritettävissä olevan kynnyksen, käynnistävät varajärjestelyjen työnkulut (esim. hakua täydentävä generointi, toissijainen malli tai ihmisen tarkistus).
 #7.2.3    Taso: 2    Rooli: D/V
 Varmista, että harhakuvitustapaukset on merkitty perussyyn metatiedoilla ja syötetty jälkipuheen ja hienosäätöputkien käsittelyyn.
 #7.2.4    Taso: 3    Rooli: D/V
 Varmista, että kynnysarvot ja tunnistimet kalibroidaan uudelleen merkittävien mallin tai tietopohjan päivitysten jälkeen.
 #7.2.5    Taso: 3    Rooli: V
 Varmista, että kojelaudan visualisoinnit seuraavat harhaluulojen esiintymisprosentteja.

---

### C7.3 Tulosteen turvallisuus- ja yksityisyydensuodatus

Politiikkasuodattimet ja punatiimin kattavuus suojaavat käyttäjiä ja luottamuksellisia tietoja.

 #7.3.1    Taso: 1    Rooli: D/V
 Varmista, että esigenerointi- ja jälkigenerointiluokittelijat estävät vihapuheen, häirinnän, itsetuhoisuuden, ääriliikkeet ja seksuaalisesti eksplisiittisen sisällön, joka on politiikan mukaista.
 #7.3.2    Taso: 1    Rooli: D/V
 Varmista, että PII/PCI-tunnistus ja automaattinen sensurointi suoritetaan jokaisessa vastauksessa; rikkomukset aiheuttavat tietosuojaongelman.
 #7.3.3    Taso: 2    Rooli: D
 Varmista, että luottamuksellisuusmerkinnät (esim. liikesalaisuudet) leviävät eri formaattien välillä estäen vuotoja tekstissä, kuvissa tai koodissa.
 #7.3.4    Taso: 3    Rooli: D/V
 Varmista, että suodattimen ohitusyritykset tai korkean riskin luokitukset vaativat toissijaisen hyväksynnän tai käyttäjän uudelleentunnistautumisen.
 #7.3.5    Taso: 3    Rooli: D/V
 Varmista, että suodatuskynnykset vastaavat lakisääteisiä toimivalta-alueita sekä käyttäjän ikä- ja roolikontekstia.

---

### C7.4 Tulosteen ja toiminnon rajoittaminen

Nopeusrajoitukset ja hyväksyntäportit estävät hyväksikäytön ja liiallisen autonomian.

 #7.4.1    Taso: 1    Rooli: D
 Varmista, että käyttäjäkohtaiset ja API-avaimenkohtaiset käyttökiintiöt rajoittavat pyyntöjä, tokeneita ja kustannuksia eksponentiaalisella takaisinkytkennällä 429-virheiden yhteydessä.
 #7.4.2    Taso: 1    Rooli: D/V
 Varmista, että etuoikeutetut toimet (tiedostojen kirjoitus, koodin suoritus, verkkokutsut) vaativat politiikkapohjaisen hyväksynnän tai ihmisen ohjauksen.
 #7.4.3    Taso: 2    Rooli: D/V
 Varmista, että ristiinmodaliteettien yhdenmukaisuustarkistukset takaavat, etteivät kuvat, koodi ja teksti, jotka on luotu samalle pyynnölle, voi sisältää piilotettua haitallista sisältöä.
 #7.4.4    Taso: 2    Rooli: D
 Varmista, että agentin valtuutuksen syvyys, rekursion rajat ja sallitut työkaluluettelot on nimenomaisesti määritetty.
 #7.4.5    Taso: 3    Rooli: V
 Varmista, että rajojen rikkominen tuottaa jäsenneltyjä tietoturvatapahtumia SIEM:n keräämistä varten.

---

### C7.5 Tulosteen selitettävyys

Läpinäkyvät signaalit parantavat käyttäjän luottamusta ja sisäistä virheenkorjausta.

 #7.5.1    Taso: 2    Rooli: D/V
 Varmista, että käyttäjälle näkyvät luottamuspisteet tai lyhyet perusteluyhteenvedot esitetään, kun riskinarviointi katsoo ne sopiviksi.
 #7.5.2    Taso: 2    Rooli: D/V
 Varmista, että luodut selitykset eivät paljasta arkaluonteisia järjestelmäkehotteita tai omistusoikeudellisia tietoja.
 #7.5.3    Taso: 3    Rooli: D
 Varmista, että järjestelmä tallentaa token-tason lok todennäköisyydet tai huomiokartat valtuutettua tarkastusta varten.
 #7.5.4    Taso: 3    Rooli: V
 Varmista, että selitettävyyteen liittyvät artefaktit ovat versiohallinnassa mallijulkaisujen yhteydessä auditoitavuutta varten.

---

### C7.6 Valvonnan integrointi

Reaaliaikainen havaittavuus sulkee kehityksen ja tuotannon välisen silmukan.

 #7.6.1    Taso: 1    Rooli: D
 Varmista, että mittarit (skeemarikkomukset, harhaluulot, toksisuus, henkilötietovuodot, viive, kustannukset) siirtyvät keskitettyyn valvonta-alustaan.
 #7.6.2    Taso: 1    Rooli: V
 Varmista, että hälytysrajat on määritelty jokaiselle turvallisuusmittarille, ja että on valmiit reitit hälytyksen eskalointiin päivystäville.
 #7.6.3    Taso: 2    Rooli: V
 Varmista, että kojelaudat yhdistävät poikkeamatulokset malliin/versioon, ominaisuuslippuun ja ylösvetoisiin tietomuutoksiin.
 #7.6.4    Taso: 2    Rooli: D/V
 Varmista, että valvontadata palautuu uudelleenkoulutukseen, hienosäätöön tai sääntöpäivityksiin dokumentoidun MLOps-työnkulun puitteissa.
 #7.6.5    Taso: 3    Rooli: V
 Varmista, että valvontaputket on suojattu tunkeutumistestein ja käyttöoikeuksin estämään arkaluonteisten lokitietojen vuotaminen.

---

### 7.7 Generatiivisen median suojatoimet

Varmista, että tekoälyjärjestelmät eivät tuota laittomia, vahingollisia tai luvattomia mediasisältöjä toteuttamalla käytännesääntöjen rajoituksia, tulosten vahvistamista ja jäljitettävyyttä.

 #7.7.1    Taso: 1    Rooli: D/V
 Varmista, että järjestelmäkehotteet ja käyttäjän ohjeet nimenomaisesti kieltävät laittoman, vahingollisen tai ei-suostumuksellisen deepfake-sisällön (esim. kuvat, videot, äänet) luomisen.
 #7.7.2    Taso: 2    Rooli: D/V
 Varmista, että kehotteet suodatetaan yrittäessään luoda jäljitelmiä, seksuaalisesti eksplisiittisiä deepfake-videoita tai mediaa, joka kuvaa todellisia henkilöitä ilman suostumusta.
 #7.7.3    Taso: 2    Rooli: V
 Varmista, että järjestelmä käyttää havaintotiivistämistä, vesileiman tunnistusta tai sormenjälkitunnistusta estääkseen luvattoman kopioinnin tekijänoikeudella suojatusta sisällöstä.
 #7.7.4    Taso: 3    Rooli: D/V
 Varmista, että kaikki luotu media on kryptografisesti allekirjoitettu, vesileimattu tai varustettu muokkausta kestävällä alkuperätietojen metadatalla jäljitettävyyden varmistamiseksi jatkokäsittelyssä.
 #7.7.5    Taso: 3    Rooli: V
 Varmista, että ohitusyritykset (esim. kehotteen naamiointi, slangin käyttö, vihamielinen muotoilu) havaitaan, kirjataan ja niiden käyttöä rajoitetaan; toistuva väärinkäyttö raportoidaan valvontajärjestelmiin.

### Viitteet

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

## C8 Muistin, upotusten ja vektoritietokantojen tietoturva

### Ohjaustavoite

Upotukset ja vektorivarastot toimivat nykyaikaisten tekoälyjärjestelmien "elävänä muistina", vastaanottaen jatkuvasti käyttäjän antamia tietoja ja palauttaen ne mallin konteksteihin hakua vahvistavan generoinnin (RAG) avulla. Jos tätä muistia ei valvota, se voi vuotaa henkilötietoja, rikkoa suostumuksia tai olla käännettävissä alkuperäisen tekstin rekonstruoimiseksi. Tämän kontrolliperheen tavoitteena on vahvistaa muistin käsittelyketjuja ja vektoritietokantoja siten, että pääsy on vähimmän etuoikeuden periaatteen mukaista, upotukset säilyttävät yksityisyyden, tallennetut vektorit vanhenevat tai ne voidaan peruuttaa pyynnöstä, ja yksittäisen käyttäjän muisti ei koskaan saastuta toisen käyttäjän kehotteita tai tuloksia.

---

### C8.1 Pääsynvalvonta muistiin ja RAG-indekseihin

Ota käyttöön yksityiskohtaiset käyttöoikeuksien valvontamekanismit jokaiseen vektorikokoelmaan.

 #8.1.1    Taso: 1    Rooli: D/V
 Varmista, että rivin/nimiavaruustason käyttöoikeussäännöt rajoittavat lisäys-, poisto- ja kyselytoiminnot vuokralaisen, kokoelman tai asiakirjan tunnisteen mukaan.
 #8.1.2    Taso: 1    Rooli: D/V
 Varmista, että API-avaimet tai JWT:t sisältävät rajattuja lupauksia (esim. kokoelman tunnisteet, toimintoverbit) ja että ne kierrätetään vähintään neljännesvuosittain.
 #8.1.3    Taso: 2    Rooli: D/V
 Varmista, että oikeuksien korotuspyrkimykset (esim. ristialueen samankaltaisuuskyselyt) havaitaan ja kirjataan SIEM-järjestelmään 5 minuutin kuluessa.
 #8.1.4    Taso: 2    Rooli: D/V
 Varmista, että vektorikanta kirjaa tarkastuslokeihin aiheen tunnisteen, toimenpiteen, vektorin tunnuksen/nimiavaruuden, samankaltaisuuskynnyksen ja tulosten määrän.
 #8.1.5    Taso: 3    Rooli: V
 Varmista, että pääsypäätöksiä testataan ohitusvirheiden varalta aina, kun moottoreita päivitetään tai hakemistojen shardauksen sääntöjä muutetaan.

---

### C8.2 Upotuksen puhdistus ja validointi

Esikäsittele teksti PII:n varalta, sensuroi tai pseudonymisoi ennen vektorisointia, ja tarvittaessa jälkikäsittele upotuksia poistaaksesi jäljellä olevat signaalit.

 #8.2.1    Taso: 1    Rooli: D/V
 Varmista, että tunnistettavissa oleva henkilötieto (PII) ja säännelty tieto havaitaan automaattisten luokittelijoiden avulla ja käsitellään peittämällä, tokenisoimalla tai poistamalla ennen upotusta.
 #8.2.2    Taso: 1    Rooli: D
 Varmista, että upotusputket hylkäävät tai eristävät syötteet, jotka sisältävät suoritettavaa koodia tai ei-UTF-8-artefakteja, jotka voisivat myrkyttää indeksin.
 #8.2.3    Taso: 2    Rooli: D/V
 Varmista, että lauseiden upotuksiin, joiden etäisyys mihin tahansa tunnettuun henkilötietoon (PII-token) alittaa määriteltävissä olevan kynnyksen, sovelletaan paikallista tai metristä differentiaalisuojatun käsittelyä.
 #8.2.4    Taso: 2    Rooli: V
 Varmista, että puhdistuksen tehokkuus (esim. henkilötietojen poistamisen palauttavuus, semanttinen poikkeama) validoidaan vähintään puolen vuoden välein vertailukorpusten avulla.
 #8.2.5    Taso: 3    Rooli: D/V
 Varmista, että puhdistusasetukset ovat versiohallinnassa ja muutokset käyvät läpi vertaisarvioinnin.

---

### C8.3 Muistin vanhentuminen, peruutus ja poistaminen

GDPR:n "oikeus tulla unohdetuksi" ja vastaavat lait vaativat tietojen oikea-aikaista poistamista; vektorivarastojen on siksi tuettava TTL:a, pysyviä poistoja ja tomb-stoningia, jotta peruutettuja vektoreita ei voida palauttaa tai uudelleenhakemistää.

 #8.3.1    Taso: 1    Rooli: D/V
 Varmista, että jokaisella vektorilla ja metatietueella on TTL tai selkeä säilytysmerkintä, jota automaattiset siivoustyöt noudattavat.
 #8.3.2    Taso: 1    Rooli: D/V
 Varmista, että käyttäjän aloittamat poistopyynnöt poistavat vektoridatat, metatiedot, välimuistikopiot ja johdetut indeksit 30 päivän kuluessa.
 #8.3.3    Taso: 2    Rooli: D
 Varmista, että loogisten poistojen jälkeen suoritetaan kryptografinen tietojen hävitys tallennuslohkoista, jos laitteisto tukee sitä, tai avainholvin avaimen tuhoaminen.
 #8.3.4    Taso: 3    Rooli: D/V
 Varmista, että vanhentuneet vektorit poistetaan lähimmän naapurin haun tuloksista alle 500 ms kuluttua vanhentumisesta.

---

### C8.4 Estä upotuksen kääntäminen ja vuoto

Viimeaikaiset suojaukset—kohinan ylikytkentä, projektioverkot, yksityisyysneuronin häirintä ja sovelluskerroksen salaus—voivat laskea token-tason käänteisprosentit alle 5%:n.

 #8.4.1    Taso: 1    Rooli: V
 Varmista, että virallinen uhkamalli, joka kattaa käänteis-, jäsenyys- ja attribuuttipäättelyhyökkäykset, on olemassa ja sitä tarkastellaan vuosittain.
 #8.4.2    Taso: 2    Rooli: D/V
 Varmista, että sovelluskerroksen salaus tai haettavissa oleva salaus suojaa vektoreita infrastruktuurin ylläpitäjien tai pilvipalveluhenkilöstön suorilta lukuoikeuksilta.
 #8.4.3    Taso: 3    Rooli: V
 Varmista, että suojausparametrit (ε DP:lle, kohina σ, projektion järjestys k) tasapainottavat yksityisyyden ≥ 99 % token-suojauksen ja hyödyllisyyden ≤ 3 % tarkkuuden menetyksen välillä.
 #8.4.4    Taso: 3    Rooli: D/V
 Varmista, että kääntöresistenssimittarit ovat osana julkaisukriteerejä mallipäivityksille, ja että regressiorajat on määritelty.

---

### C8.5 Käyttäjäkohtaisen muistin laajuuden valvonta

Vuokralaisten välinen vuoto pysyy edelleen merkittävänä RAG-riskinä: väärin suodatetut samankaltaisuushakujen tulokset voivat paljastaa toisen asiakkaan yksityiset asiakirjat.

 #8.5.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen hakukysely suodatetaan jälkikäteen vuokralaisen/käyttäjän tunnuksen perusteella ennen sen välittämistä LLM-kehotteeseen.
 #8.5.2    Taso: 1    Rooli: D
 Varmista, että kokoelman nimet tai nimialueelliset tunnisteet suolataan käyttäjäkohtaisesti tai vuokralaiskohtaisesti, jotta vektorit eivät voi törmätä eri kontekseissa.
 #8.5.3    Taso: 2    Rooli: D/V
 Varmista, että samankaltaisuustulokset, jotka ylittävät konfiguroitavan etäisyyskynnyksen mutta ovat kutsujan laajuuden ulkopuolella, hylätään ja laukaisevat tietoturvahälytykset.
 #8.5.4    Taso: 2    Rooli: V
 Varmista, että monivuokralaiskuormitustestit simuloivat vastustavia kyselyitä, jotka yrittävät saada käyttöönsä sallitun alueen ulkopuolisia asiakirjoja, ja osoittavat täydellisen tietovuodon poissaolon.
 #8.5.5    Taso: 3    Rooli: D/V
 Varmista, että salausavaimet on eroteltu vuokraajittain, varmistaen kryptografisen eristyksen, vaikka fyysinen tallennustila olisi jaettu.

---

### C8.6 Edistynyt muistojärjestelmän turvallisuus

Turvallisuusvalvontatoimenpiteet kehittyneille muistirakenteille, kuten episodiselle, semanttiselle ja työmuistille, joissa on erityiset eristys- ja validointivaatimukset.

 #8.6.1    Taso: 1    Rooli: D/V
 Varmista, että eri muistityypeillä (episodinen, semanttinen, työmuisti) on eristetyt suojauskontekstit, joissa on roolipohjaiset käyttöoikeudet, erilliset salausavaimet ja dokumentoidut käyttömallit kullekin muistityypille.
 #8.6.2    Taso: 2    Rooli: D/V
 Varmista, että muistin konsolidointiprosessit sisältävät turvallisuusvarmistuksen haitallisten muistojen lisäämisen estämiseksi sisällön puhdistuksen, lähteen vahvistamisen ja eheystarkastusten avulla ennen tallennusta.
 #8.6.3    Taso: 2    Rooli: D/V
 Varmista, että muistihakukyselyt vahvistetaan ja puhdistetaan estämään luvattoman tiedon poiminta kyselymallianalyysin, käyttöoikeuksien valvonnan ja tulosten suodatuksen avulla.
 #8.6.4    Taso: 3    Rooli: D/V
 Varmista, että muistinhukan mekanismit poistavat arkaluonteiset tiedot turvallisesti kryptografisen poistamisen takuilla käyttämällä avaimen poistamista, monikerroksista ylikirjoitusta tai laitteistopohjaista turvallista poistamista varmennustodistuksineen.
 #8.6.5    Taso: 3    Rooli: D/V
 Varmista, että muistijärjestelmän eheyttä valvotaan jatkuvasti luvattomien muutosten tai korruptoitumisen varalta tarkistussummien, tarkastuslokien ja automaattisten hälytysten avulla, kun muistin sisältö muuttuu normaalitoimintojen ulkopuolella.

---

### Viitteet

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

## 9 Autonominen orkestrointi ja agenttipohjainen toiminnan turvallisuus

### Ohjaustavoite

Varmista, että autonomiset tai moniagenttiset tekoälyjärjestelmät voivat suorittaa vain toimenpiteitä, jotka on nimenomaisesti tarkoitettu, todennettu, tarkastettavissa ja jotka pysyvät rajatuissa kustannus- ja riskikynnyksissä. Tämä suojaa uhkilta, kuten autonomisen järjestelmän vaarantuminen, työkalujen väärinkäyttö, agenttien silmukan tunnistus, viestinnän kaappaus, identiteetin väärennös, parven manipulointi ja tarkoituksen manipulointi.

---

### 9.1 Agentin tehtäväsuunnittelu ja rekursiobudjetit

Rajoita rekursiivisia suunnitelmia ja pakota ihmisen tarkistuspisteet valtuutetuissa toiminnoissa.

 #9.1.1    Taso: 1    Rooli: D/V
 Varmista, että maksimisyvyyden, leveyden, kellonajan, tokenien ja rahallisten kustannusten rajoitukset kunkin agentin suoritukselle ovat keskitetysti määritelty ja versiohallinnassa.
 #9.1.2    Taso: 1    Rooli: D/V
 Varmista, että etuoikeutetut tai peruuttamattomat toimet (esim. koodin tallennukset, rahansiirrot) vaativat eksplisiittisen ihmisen hyväksynnän tarkastettavan kanavan kautta ennen niiden suorittamista.
 #9.1.3    Taso: 2    Rooli: D
 Varmista, että reaaliaikaiset resurssien valvontatyökalut laukaisevat katkaisupiirin keskeytyksen, kun jokin budjettikynnys ylittyy, estäen tehtävän laajentamisen jatkumisen.
 #9.1.4    Taso: 2    Rooli: D/V
 Varmista, että katkaisijatapahtumat kirjataan agentin tunnuksella, laukaisevalla ehdolla ja tallennetulla suunnitelmatilalla oikeudellista tarkastelua varten.
 #9.1.5    Taso: 3    Rooli: V
 Varmista, että tietoturvatestit kattavat budjetin loppumisen ja hallitsemattoman suunnitelman tilanteet, varmistaen turvallisen pysäytyksen ilman tiedonmenetystä.
 #9.1.6    Taso: 3    Rooli: D
 Varmista, että budjettipolitiikat on ilmaistu politiikkana-koodina ja ne pannaan täytäntöön CI/CD:ssä konfiguraation poikkeamien estämiseksi.

---

### 9.2 Työkalulaajennusten hiekkalaatikkotila

Eristä työkalujen vuorovaikutukset estääksesi luvattoman järjestelmän käytön tai koodin suorittamisen.

 #9.2.1    Taso: 1    Rooli: D/V
 Varmista, että jokainen työkalu/laajennus suoritetaan käyttöjärjestelmän, kontin tai WASM-tason hiekkalaatikon sisällä, jossa on vähimmän etuoikeuden tiedostojärjestelmä-, verkko- ja järjestelmäkutsupolitiikat.
 #9.2.2    Taso: 1    Rooli: D/V
 Varmista, että hiekkalaatikkoresurssien kiintiöt (CPU, muisti, levytila, verkon ulossuuntaus) ja suoritusaikarajat toteutetaan ja kirjataan.
 #9.2.3    Taso: 2    Rooli: D/V
 Varmista, että työkalujen binaaritiedostot tai kuvaukset on digitaalisesti allekirjoitettu; allekirjoitukset tarkistetaan ennen lataamista.
 #9.2.4    Taso: 2    Rooli: V
 Varmista, että hiekkalaatikon telemetriatiedot virtaavat SIEM-järjestelmään; poikkeamat (esim. yritykset muodostaa ulospäin suuntautuvia yhteyksiä) laukaisevat hälytykset.
 #9.2.5    Taso: 3    Rooli: V
 Varmista, että korkean riskin liitännäiset käyvät läpi turvallisuustarkastuksen ja tunkeutumistestauksen ennen tuotantoon käyttöönottoa.
 #9.2.6    Taso: 3    Rooli: D/V
 Varmista, että hiekkalaatikkopaon yritykset estetään automaattisesti ja kyseinen lisäosa eristetään karanteeniin tutkinnan ajaksi.

---

### 9.3 Autonominen silmukka ja kustannusten rajoittaminen

Havaitse ja pysäytä hallitsematon agenttien välinen rekursio ja kustannusten räjähdys.

 #9.3.1    Taso: 1    Rooli: D/V
 Varmista, että agenttien välisissä viesteissä on hyppyrajoitin tai TTL, jonka suoritusympäristö vähentää ja valvoo.
 #9.3.2    Taso: 2    Rooli: D
 Varmista, että agentit ylläpitävät ainutlaatuista kutsukartta-ID:tä havaitakseen itse-kutsun tai sykliset kuviot.
 #9.3.3    Taso: 2    Rooli: D/V
 Varmista, että kertyvät laskenta-yksikkö- ja kulutuskertymät seurataan jokaiselle pyyntöketjulle; rajan ylitys keskeyttää ketjun.
 #9.3.4    Taso: 3    Rooli: V
 Varmista, että formaali analyysi tai mallintarkastus osoittaa agenttiprotokollissa rajoittamattoman rekursion poissaolon.
 #9.3.5    Taso: 3    Rooli: D
 Varmista, että silmukan keskeytystapahtumat tuottavat hälytyksiä ja syöttävät jatkuvan parantamisen mittareita.

---

### 9.4 Protokollatason väärinkäytön suojaus

Varmista suojatut viestintäkanavat agenttien ja ulkoisten järjestelmien välillä sieppauksen tai manipuloinnin estämiseksi.

 #9.4.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki agentin ja työkalun sekä agenttien väliset viestit ovat todennettuja (esim. molemminpuolinen TLS tai JWT) ja päästä päähän salattuja.
 #9.4.2    Taso: 1    Rooli: D
 Varmista, että skeemat validoidaan tiukasti; tuntemattomat kentät tai väärin muotoillut viestit hylätään.
 #9.4.3    Taso: 2    Rooli: D/V
 Varmista, että eheystarkastukset (MAC:t tai digitaaliset allekirjoitukset) kattavat koko viestin hyötykuorman, mukaan lukien työkalun parametrit.
 #9.4.4    Taso: 2    Rooli: D
 Varmista, että uudelleenlähetyssuojaus (nonce-arvot tai aikaleimaikkunat) on toteutettu protokollakerroksella.
 #9.4.5    Taso: 3    Rooli: V
 Varmista, että protokollan toteutukset käyvät läpi fuzzauksen ja staattisen analyysin injektio- tai deserialisointivikojen varalta.

---

### 9.5 Agentin identiteetti ja muokkaussuoja

Varmista, että toimet voidaan kohdistaa ja muutokset havaita.

 #9.5.1    Taso: 1    Rooli: D/V
 Varmista, että jokaisella agentti-instanssilla on ainutlaatuinen kryptografinen identiteetti (avainpari tai laitteistoon perustuva tunniste).
 #9.5.2    Taso: 2    Rooli: D/V
 Varmista, että kaikki agenttien toimet on allekirjoitettu ja aikaleimattu; lokit sisältävät allekirjoituksen kiistämättömyyden varmistamiseksi.
 #9.5.3    Taso: 2    Rooli: V
 Varmista, että manipulointia havaitsevat lokit tallennetaan vain lisäämistä tai kirjoittamista kerran sallivaan välineeseen.
 #9.5.4    Taso: 3    Rooli: D
 Varmista, että identiteettiavaimet kiertävät määritellyn aikataulun mukaisesti ja kompromissin indikaattoreiden yhteydessä.
 #9.5.5    Taso: 3    Rooli: D/V
 Varmista, että väärentäminen tai avainkonfliktin yritykset laukaisevat välittömän karanteenin vaikuttuneelle agentille.

---

### 9.6 Moniagenttisen ryömintäjoukon riskien vähentäminen

Vähennä kollektiivisen käyttäytymisen riskejä eristämisen ja muodollisen turvallisuusmallinnuksen avulla.

 #9.6.1    Taso: 1    Rooli: D/V
 Varmista, että eri turvallisuusalueilla toimivat agentit suoritetaan eristetyissä suoritusaikojen hiekkalaatikoissa tai verkkosegmenteissä.
 #9.6.2    Taso: 3    Rooli: V
 Varmista, että parviekäytymät on mallinnettu ja muodollisesti varmennettu elinvoimaisuuden ja turvallisuuden osalta ennen käyttöönottoa.
 #9.6.3    Taso: 3    Rooli: D
 Varmista, että suoritusajan valvontatyökalut havaitsevat nousevat vaaralliset mallit (esim. sykliilmiöt, umpikujat) ja aloittavat korjaavat toimenpiteet.

---

### 9.7 Käyttäjän ja työkalun todennus / valtuutus

Toteuta vahvat käyttöoikeusvalvonnat jokaiseen agentin käynnistämään toimintaan.

 #9.7.1    Taso: 1    Rooli: D/V
 Varmista, että agentit todennetaan ensiluokkaisina päämiehinä alajärjestelmissä eivätkä koskaan käytä loppukäyttäjän tunnistetietoja uudelleen.
 #9.7.2    Taso: 2    Rooli: D
 Varmista, että hienojakoiset valtuutuspolitiikat rajoittavat, mitä työkaluja agentti saa käyttää ja mitä parametreja se saa syöttää.
 #9.7.3    Taso: 2    Rooli: V
 Varmista, että oikeustarkistukset arvioidaan uudelleen jokaisella kutsulla (jatkuva valtuutus), ei vain istunnon alussa.
 #9.7.4    Taso: 3    Rooli: D
 Varmista, että valtuutetut oikeudet vanhenevat automaattisesti ja vaativat uudelleen hyväksynnän aikakatkaisun tai laajuuden muutoksen jälkeen.

---

### 9.8 Agenttien välinen viestintäturvallisuus

Salaa ja suojaa kaikkien agenttien väliset viestit eavesdroppauksen ja väärentämisen estämiseksi.

 #9.8.1    Taso: 1    Rooli: D/V
 Varmista, että keskinäinen todennus ja täydellinen eteenpäin suuntautuva salaus (esim. TLS 1.3) ovat pakollisia agenttikanaville.
 #9.8.2    Taso: 1    Rooli: D
 Varmista, että viestin eheys ja alkuperä on varmennettu ennen käsittelyä; epäonnistumiset aiheuttavat hälytyksiä ja viestin hylkäämisen.
 #9.8.3    Taso: 2    Rooli: D/V
 Varmista, että viestinnän metatiedot (aikaleimat, sekvenssinumerot) kirjataan tukemaan oikeuslääketieteellistä rekonstruointia.
 #9.8.4    Taso: 3    Rooli: V
 Varmista, että formaali tarkastus tai mallintarkastus vahvistaa, ettei protokollan tilakoneita voida ohjata vaarallisiin tiloihin.

---

### 9.9 Aikomuksen varmistus ja rajoitusten noudattaminen

Varmista, että agentin toimet vastaavat käyttäjän ilmaisemaa tarkoitusta ja järjestelmän rajoituksia.

 #9.9.1    Taso: 1    Rooli: D
 Varmista, että esisuorituksen rajoitusten ratkaisutarkastimet tarkistavat ehdotetut toimet kovakoodattuja turvallisuus- ja politiikkasääntöjä vastaan.
 #9.9.2    Taso: 2    Rooli: D/V
 Varmista, että suurivaikutteiset toimet (taloudelliset, tuhoisat, yksityisyyteen liittyvät) edellyttävät aloittavan käyttäjän nimenomaista aikomuksen vahvistamista.
 #9.9.3    Taso: 2    Rooli: V
 Varmista, että jälkiehdon tarkistukset varmistavat, että suoritetut toimenpiteet saavuttivat tarkoitetut vaikutukset ilman sivuvaikutuksia; poikkeamat laukaisevat palautuksen.
 #9.9.4    Taso: 3    Rooli: V
 Varmista, että formaalit menetelmät (esim. mallintarkastus, teoreemojen todistus) tai ominaisuuksiin perustuvat testit osoittavat, että agentin suunnitelmat täyttävät kaikki ilmoitetut rajoitteet.
 #9.9.5    Taso: 3    Rooli: D
 Varmista, että tarkoituksenmukaisuuden poikkeamat tai rajoitteiden rikkomiset ohjaavat jatkuvan parantamisen jaksoja ja uhkatiedon jakamista.

---

### 9.10 Agenttien päättelystrategian turvallisuus

Turvallinen eri päättelystrategioiden valinta ja suorittaminen, mukaan lukien ReAct-, Chain-of-Thought- ja Tree-of-Thoughts-lähestymistavat.

 #9.10.1    Taso: 1    Rooli: D/V
 Varmista, että päättelystrategian valinta käyttää deterministisiä kriteereitä (syötetyn monimutkaisuus, tehtävätyyppi, turvallisuuskonteksti) ja että identtiset syötteet tuottavat identtiset strategian valinnat samassa turvallisuuskontekstissa.
 #9.10.2    Taso: 1    Rooli: D/V
 Varmista, että jokaisella päättelystrategialla (ReAct, Chain-of-Thought, Tree-of-Thoughts) on omistettu syötteen validointi, tulosteen puhdistus ja suoritusajan rajoitukset, jotka ovat spesifisiä sen kognitiiviselle lähestymistavalle.
 #9.10.3    Taso: 2    Rooli: D/V
 Varmista, että päättelystrategian siirtymät kirjataan täydellisellä kontekstilla, mukaan lukien syötteen ominaisuudet, valintakriteerien arvot ja suoritusmetatiedot, jotta auditointijäljen rekonstruointi on mahdollista.
 #9.10.4    Taso: 2    Rooli: D/V
 Varmista, että Tree-of-Thoughts-päätöksentekoprosessi sisältää oksan karsintamekanismit, jotka lopettavat tutkimisen, kun havaitaan politiikan rikkomuksia, resurssirajoja tai turvallisuusrajoja.
 #9.10.5    Taso: 2    Rooli: D/V
 Varmista, että ReAct (Reason-Act-Observe) -syklit sisältävät validointipisteet jokaisessa vaiheessa: päättelyvaiheen tarkastus, toiminnon vahvistus ja havainnon puhdistus ennen etenemistä.
 #9.10.6    Taso: 3    Rooli: D/V
 Varmista, että päättelystrategian suorituskykymittareita (suoritusaika, resurssien käyttö, tuloksen laatu) seurataan automaattisten hälytysten avulla, kun mittarit poikkeavat määritettyjen kynnysten ulkopuolelle.
 #9.10.7    Taso: 3    Rooli: D/V
 Varmista, että hybridi-päättelymenetelmät, jotka yhdistävät useita strategioita, säilyttävät kaikkien osastrategioiden syötteen validoinnin ja tulosten rajoitukset ilman, että ohitetaan mitään turvallisuusvalvontoja.
 #9.10.8    Taso: 3    Rooli: D/V
 Varmista, että päättelystrategian turvallisuustestaus sisältää väärinmuotoisten syötteiden fuzzauksen, vihamieliset kehotteet, jotka on suunniteltu pakottamaan strategian vaihtaminen, sekä rajatapaustestauksen kullekin kognitiiviselle lähestymistavalle.

---

### 9.11 Agentin elinkaaren tilanhallinta ja tietoturva

Turvallinen agentin alustaminen, tilasiirtymät ja päättäminen kryptografisten tarkastuslokkien sekä määriteltyjen palautusmenettelyjen avulla.

 #9.11.1    Taso: 1    Rooli: D/V
 Varmista, että agentin alustukseen sisältyy kryptografisen identiteetin muodostaminen laitteistotukea hyödyntävillä todennustiedoilla sekä muuttumattomat käynnistyslokiot, jotka sisältävät agentin tunnuksen, aikaleiman, kokoonpanon hajautusarvon ja alustuksen parametrit.
 #9.11.2    Taso: 2    Rooli: D/V
 Varmista, että agentin tilasiirtymät on kryptografisesti allekirjoitettu, aikaleimattu ja kirjattu täydellisen kontekstin kanssa, mukaan lukien laukaisevat tapahtumat, edellisen tilan tiiviste, uuden tilan tiiviste ja suoritetut turvallisuustarkastukset.
 #9.11.3    Taso: 2    Rooli: D/V
 Varmista, että agentin sammutusmenettelyt sisältävät turvallisen muistin pyyhinnän kryptografisella tuhoamisella tai monivaiheisella ylikirjoituksella, tunnistetietojen mitätöinnin sertifikaattiviranomaiselle ilmoittamalla, sekä väärentämättömien lopetustodistusten luomisen.
 #9.11.4    Taso: 3    Rooli: D/V
 Varmista, että agentin toipumismekanismit validoivat tilan eheyttä käyttämällä kryptografisia tarkistussummia (vähintään SHA-256) ja palautuvat tunnetusti ehjiin tiloihin havaittaessa korruptiota, sisältäen automaattiset hälytykset ja manuaaliset hyväksyntävaatimukset.
 #9.11.5    Taso: 3    Rooli: D/V
 Varmista, että agenttien pysyvyysmekanismit salakirjoittavat arkaluontoiset tilatiedot kullekin agentille erikseen määritellyillä AES-256-avaimilla ja toteuttavat turvallisen avaintenvaihdon asetettavissa aikatauluissa (enintään 90 päivän välein) ilman käyttökatkoa.

---

### 9.12 Työkalujen integroinnin turvallisuuskehys

Turvallisuusohjaimet dynaamiselle työkalujen lataukselle, suorittamiselle ja tulosten validoinnille määriteltyjen riskinarviointi- ja hyväksymisprosessien mukaisesti.

 #9.12.1    Taso: 1    Rooli: D/V
 Varmista, että työkalukuvaajat sisältävät turvallisuusmetatiedot, joissa määritellään vaaditut oikeudet (luku/kirjoitus/suoritus), riskitasot (matala/keski/korkea), resurssirajat (CPU, muisti, verkko) sekä validointivaatimukset, jotka on dokumentoitu työkalun manifestissa.
 #9.12.2    Taso: 1    Rooli: D/V
 Varmista, että työkalun suoritus tulokset validoidaan odotettuja skeemoja (JSON-skeema, XML-skeema) ja turvallisuuspolitiikkoja (tulosteen puhdistus, tietoluokitus) vastaan ennen integrointia aikakatkaisu- ja virheenkäsittelymenettelyjen kanssa.
 #9.12.3    Taso: 2    Rooli: D/V
 Varmista, että työkalun vuorovaikutuslokeissa on yksityiskohtainen suojauskonteksti, mukaan lukien käyttöoikeuksien käyttö, datan käyttökuviot, suoritusajan, resurssien kulutus ja paluuarvokoodit, rakenteellisen lokituksen avulla SIEM-integraatiota varten.
 #9.12.4    Taso: 2    Rooli: D/V
 Varmista, että dynaamiset työkalujen latausmekanismit validoivat digitaaliset allekirjoitukset PKI-infrastruktuurin avulla ja toteuttavat turvalliset latausprotokollat hiekkalaatikkoympäristön eristämisellä sekä käyttöoikeuksien tarkistuksella ennen suorittamista.
 #9.12.5    Taso: 3    Rooli: D/V
 Varmista, että työkalujen turvallisuusarvioinnit käynnistyvät automaattisesti uusille versioille pakollisilla hyväksyntäporteilla, jotka kattavat staattisen analyysin, dynaamisen testauksen ja turvallisuustiimin tarkastelun, joissa on dokumentoidut hyväksymiskriteerit ja SLA-vaatimukset.

---

#### Viitteet

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

## 10 Vihamielinen kestävyys ja yksityisyyden suojaaminen

### Ohjaustavoite

Varmista, että tekoälymallit pysyvät luotettavina, yksityisyyttä suojelevina ja väärinkäytöksiä kestävinä kohdatessaan kiertäviä, päättelyyn, tiedon poimintaan tai myrkytyshyökkäyksiin.

---

### 10.1 Mallin sovittaminen ja turvallisuus

Suojaa haitallisilta tai politiikkaa rikkovilta tuloksilta.

 #10.1.1    Taso: 1    Rooli: D/V
 Varmista, että yhdenmukaisuustestisarja (red-team-kehotteet, jailbreak-kyselyt, kielletty sisältö) on versiohallinnassa ja suoritetaan jokaisessa mallin julkaisussa.
 #10.1.2    Taso: 1    Rooli: D
 Varmista, että kieltäytymisen ja turvallisen suorittamisen suojakaiteet ovat käytössä.
 #10.1.3    Taso: 2    Rooli: D/V
 Varmista, että automaattinen arvioija mittaa haitallisen sisällön määrää ja merkitsee takapakit, jotka ylittävät asetetun kynnyksen.
 #10.1.4    Taso: 2    Rooli: D
 Varmista, että vastaharjoittelumenetelmät on dokumentoitu ja toistettavissa.
 #10.1.5    Taso: 3    Rooli: V
 Varmista, että viralliset politiikanmukaisuuden todistukset tai sertifioitu valvonta kattavat kriittiset alueet.

---

### 10.2 Vihamielisten esimerkkien kovettaminen

Lisää vastustuskykyä manipuloiduille syötteille. Vahva vastustajakoulutus ja vertailuarviointi ovat nykyiset parhaat käytännöt.

 #10.2.1    Taso: 1    Rooli: D
 Varmista, että projektivarastoissa on vastustajakoulutusasetukset toistettavilla siemenillä.
 #10.2.2    Taso: 2    Rooli: D/V
 Varmista, että vastustajasimulaatioiden tunnistus aiheuttaa estäviä hälytyksiä tuotantoputkistoissa.
 #10.2.4    Taso: 3    Rooli: V
 Varmista, että sertifioidut-robustiustodistukset tai väliarvotodistukset kattavat vähintään tärkeimmät kriittiset luokat.
 #10.2.5    Taso: 3    Rooli: V
 Varmista, että regressiotestit käyttävät adaptiivisia hyökkäyksiä vahvistaakseen, ettei havaittavissa ole mittaavaa suorituskyvyn heikkenemistä.

---

### 10.3 Jäsenyystietoisuuden ehkäisy

Rajoita kykyä päätellä, oliko tietue harjoitusdatassa. Differentiaalinen yksityisyys ja luottamusarvopisteen peittäminen ovat edelleen tehokkaimmat tunnetut suojakeinot.

 #10.3.1    Taso: 1    Rooli: D
 Varmista, että kyselykohtainen entropian regularisointi tai lämpötilan skaalaus vähentää yliitsevarmoja ennusteita.
 #10.3.2    Taso: 2    Rooli: D
 Varmista, että koulutus käyttää ε-rajoitettua differentiaalisesti yksityistä optimointia arkaluontoisille tietoaineistoille.
 #10.3.3    Taso: 2    Rooli: V
 Varmista, että hyökkäyssimulaatiot (varjomalli tai mustalaatikkomenetelmä) osoittavat hyökkäyksen AUC-arvon ≤ 0,60 pidetyllä testiaineistolla.

---

### 10.4 Mallin käännöstä estävä vastustus

Estä yksityisten attribuuttien uudelleenrakentaminen. Viimeaikaiset tutkimukset korostavat tuloksen katkaisua ja differentiaalisen yksityisyyden (DP) takeita käytännöllisinä puolustuksina.

 #10.4.1    Taso: 1    Rooli: D
 Varmista, ettei arkaluonteisia attribuutteja koskaan tulosteta suoraan; tarvittaessa käytä luokkia tai yksisuuntaisia muunnoksia.
 #10.4.2    Taso: 1    Rooli: D/V
 Varmista, että kyselynopeusrajoitukset rajoittavat saman päähenkilön toistuvia mukautuvia kyselyjä.
 #10.4.3    Taso: 2    Rooli: D
 Varmista, että malli on koulutettu yksityisyyttä säilyttävällä melulla.

---

### 10.5 Mallin poistonesto

Tunnista ja estä luvaton kloonaus. Vesileimauksen ja kyselykuviopohjaisen analyysin käyttöä suositellaan.

 #10.5.1    Taso: 1    Rooli: D
 Vahvista, että päättelyportit noudattavat globaaleja ja API-avaimittain määriteltyjä nopeusrajoja, jotka on säädetty mallin muistamisen kynnyksen mukaan.
 #10.5.2    Taso: 2    Rooli: D/V
 Varmista, että kyselyentropia- ja syöttömoninaisuustilastot syöttävät automatisoidun poiminnan havaitsemaan.
 #10.5.3    Taso: 2    Rooli: V
 Varmista, että hauraat tai todennäköisyyttä käyttävät vesileimat voidaan todistaa p < 0,01 tasolla enintään 1 000 kyselyllä epäiltyä kloonia vastaan.
 #10.5.4    Taso: 3    Rooli: D
 Varmista, että vesileimauksen avaimet ja laukaisusarjat tallennetaan laitteistoturvamoduuliin ja vaihdetaan vuosittain.
 #10.5.5    Taso: 3    Rooli: V
 Varmista, että poisto-hälytys tapahtumat sisältävät rikkomuksia aiheuttavat kyselyt ja ne on integroitu tapausreaktio-ohjelmiin.

---

### 10.6 Päättelyaikainen myrkyllisen datan havaitseminen

Tunnista ja neutralisoi takaportilla varustetut tai myrkylliset syötteet.

 #10.6.1    Taso: 1    Rooli: D
 Varmista, että syötteet käyvät läpi poikkeavuuksien havaitsemisen ennen mallin päätelmää (esim. STRIP, johdonmukaisuuspisteytys).
 #10.6.2    Taso: 1    Rooli: V
 Varmista, että havaitin kynnysarvot on säädetty puhtaille/myrkyllisille validointiaineistoille niin, että virheellisten positiivisten osuus on alle 5%.
 #10.6.3    Taso: 2    Rooli: D
 Varmista, että myrkytyksiksi merkatut syötteet laukaisevat pehmeän eston ja ihmisen tarkastusprosessit.
 #10.6.4    Taso: 2    Rooli: V
 Varmista, että tunnistimet testataan rasituksella adaptiivisilla, laukaisimettomilla takaovihyökkäyksillä.
 #10.6.5    Taso: 3    Rooli: D
 Varmista, että havaitsemisen tehokkuusmittarit kirjataan ja arvioidaan säännöllisesti uudelleen uusien uhkatietojen perusteella.

---

### 10.7 Dynaaminen turvallisuuspolitiikan mukauttaminen

Reaaliaikaiset tietoturvapolitiikan päivitykset uhkatiedon ja käyttäytymisanalyysin perusteella.

 #10.7.1    Taso: 1    Rooli: D/V
 Varmista, että turvallisuuspolitiikkoja voidaan päivittää dynaamisesti ilman agentin uudelleenkäynnistystä säilyttäen samalla politiikkaversion eheys.
 #10.7.2    Taso: 2    Rooli: D/V
 Varmista, että politiikan päivitykset on kryptografisesti allekirjoitettu valtuutetun turvallisuushenkilöstön toimesta ja vahvistettu ennen käyttöönottoa.
 #10.7.3    Taso: 2    Rooli: D/V
 Varmista, että dynaamiset politiikkamuutokset kirjataan täydellisesti tarkastelujäljillä, mukaan lukien perustelut, hyväksymisketjut ja palautusmenettelyt.
 #10.7.4    Taso: 3    Rooli: D/V
 Varmista, että sopeutuvat tietoturvamekanismit säätävät uhkien tunnistuksen herkkyyttä riskikontekstin ja käyttäytymismallien perusteella.
 #10.7.5    Taso: 3    Rooli: D/V
 Varmista, että politiikan sopeutuspäätökset ovat selitettäviä ja sisältävät todisteketjuja tietoturvatiimin tarkastelua varten.

---

### 10.8 Heijastusperusteinen turvallisuusanalyysi

Turvallisuuden varmistaminen agentin itsearvioinnin ja metakognitiivisen analyysin avulla.

 #10.8.1    Taso: 1    Rooli: D/V
 Varmista, että agentin reflektiomekanismit sisältävät turvallisuuteen keskittyvän itsetarkastelun päätöksistä ja toimista.
 #10.8.2    Taso: 2    Rooli: D/V
 Varmista, että heijastusulostulot validoidaan estämään itsearviointimekanismien manipulointi vihamielisten syötteiden avulla.
 #10.8.3    Taso: 2    Rooli: D/V
 Varmista, että metakognitiivinen turvallisuusanalyysi tunnistaa mahdollisen puolueellisuuden, manipuloinnin tai vaarantumisen agentin päättelyprosesseissa.
 #10.8.4    Taso: 3    Rooli: D/V
 Varmista, että heijastukseen perustuvat turvallisuusvaroitukset laukaisevat tehostetun valvonnan ja mahdolliset ihmisen väliintulon työnkulut.
 #10.8.5    Taso: 3    Rooli: D/V
 Varmista, että jatkuva oppiminen turvallisuusheijastuksista parantaa uhkien havaitsemista ilman, että se heikentää laillista toimintaa.

---

### 10.9 Kehittyminen ja itseparantumisen turvallisuus

Turvallisuusvalvontatoimet itsensä muokkaamiseen ja kehittymiseen kykeneville agenttijärjestelmille.

 #10.9.1    Taso: 1    Rooli: D/V
 Varmista, että itse-muokkausominaisuudet on rajoitettu määritettyihin turvallisiin alueisiin muodollisen varmennuksen rajoissa.
 #10.9.2    Taso: 2    Rooli: D/V
 Varmista, että evolution ehdotukset käyvät läpi turvallisuusvaikutusten arvioinnin ennen käyttöönottoa.
 #10.9.3    Taso: 2    Rooli: D/V
 Varmista, että itseparannusmekanismit sisältävät palautusmahdollisuudet eheyden tarkistuksella.
 #10.9.4    Taso: 3    Rooli: D/V
 Varmista, että meta-oppimisen turvallisuus estää parannusalgoritmien vastustavan manipuloinnin.
 #10.9.5    Taso: 3    Rooli: D/V
 Varmista, että rekursiivinen itseparannus on rajoitettu muodollisilla turvallisuusrajoitteilla matemaattisilla todisteilla konvergenssista.

---

#### Viitteet

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

## 11 Tietosuojan suojaus ja henkilötietojen hallinta

### Ohjaustavoite

Säilytä tiukat yksityisyyden suojan takeet koko tekoälyn elinkaaren ajan—keräyksestä, koulutuksesta, päättelystä ja häiriötilanteisiin reagoinnista—niin että henkilötietoja käsitellään vain selkeällä suostumuksella, mahdollisimman suppeassa laajuudessa, todennettavissa olevalla poistamisella ja virallisilla yksityisyydensuojan takeilla.

---

### 11.1 Anonymisointi ja tietojen minimointi

 #11.1.1    Taso: 1    Rooli: D/V
 Varmista, että suorat ja kvasi-tunnisteet on poistettu tai hajautettu.
 #11.1.2    Taso: 2    Rooli: D/V
 Varmista, että automatisoidut tarkastukset mittaavat k-anonymiteettia/l-monimuotoisuutta ja hälyttävät, kun kynnysarvot laskevat alle politiikan.
 #11.1.3    Taso: 2    Rooli: V
 Varmista, että mallin ominaisuuksien tärkeysraportit todistavat, ettei tunnistevuotoa esiinny yli ε = 0.01 yhteisen informaation.
 #11.1.4    Taso: 3    Rooli: V
 Varmista, että muodolliset todistukset tai synteettisen datan sertifiointi osoittavat uudelleentunnistamisriskin olevan ≤ 0,05 jopa linkitysiskuissa.

---

### 11.2 Oikeus tulla unohdetuksi ja poistamisen valvonta

 #11.2.1    Taso: 1    Rooli: D/V
 Varmista, että data-subjectin poistopyynnöt leviävät raakadatakokoelmiin, tarkistuspisteisiin, upotuksiin, lokitietoihin ja varmuuskopioihin palvelutasosopimusten puitteissa, jotka ovat alle 30 päivää.
 #11.2.2    Taso: 2    Rooli: D
 Varmista, että "machine-unlearning" -rutiinit fyysisesti uudelleenkouluttavat tai likimääräisesti poistavat tiedot käyttäen sertifioituja unlearning-algoritmeja.
 #11.2.3    Taso: 2    Rooli: V
 Varmista, että varjomallin arviointi todistaa unohdettujen tietueiden vaikuttavan alle 1 % tuloksista unlearningin jälkeen.
 #11.2.4    Taso: 3    Rooli: V
 Varmista, että poistotapahtumat kirjataan pysyvästi ja ne ovat tarkastettavissa sääntelyviranomaisille.

---

### 11.3 Differentiaalisen yksityisyyden suojatoimet

 #11.3.1    Taso: 2    Rooli: D/V
 Varmista, että tietosuojahäviön kirjaamista esittävät kojelaudat hälyttävät, kun kumulatiivinen ε ylittää politiikan rajat.
 #11.3.2    Taso: 2    Rooli: V
 Varmista, että mustan laatikon yksityisyystarkastukset arvioivat ε̂:n 10 %:n tarkkuudella ilmoitetusta arvosta.
 #11.3.3    Taso: 3    Rooli: V
 Varmista, että muodolliset todistukset kattavat kaikki jälkikoulutuksen hienosäädöt ja upotukset.

---

### 11.4 Tarkoituksen rajoittaminen ja laajuuden hallinta

 #11.4.1    Taso: 1    Rooli: D
 Varmista, että jokaisella tietoaineistolla ja mallin tarkistuspisteellä on koneellisesti luettava tarkoitustunniste, joka on linjassa alkuperäisen suostumuksen kanssa.
 #11.4.2    Taso: 1    Rooli: D/V
 Varmista, että ajoaikaiset valvontajärjestelmät havaitsevat tarkoituksenmukaisuutta rikkovat kyselyt ja laukaisevat pehmeän kieltoonvieton.
 #11.4.3    Taso: 3    Rooli: D
 Varmista, että politiikka-koodina -portit estävät mallien uudelleenvientin uusille toimialueille ilman DPIA-arviointia.
 #11.4.4    Taso: 3    Rooli: V
 Varmista, että muodolliset jäljitettävyystodistukset osoittavat jokaisen henkilötietojen elinkaaren pysyvän suostumuksen mukaisessa laajuudessa.

---

### 11.5 Suostumuksen hallinta ja lainmukaisen perustan seuranta

 #11.5.1    Taso: 1    Rooli: D/V
 Varmista, että suostumus- ja hallintajärjestelmä (Consent-Management Platform, CMP) tallentaa rekisteröidyn suostumuksen tilan, käyttötarkoituksen ja säilytysajan kunkin rekisteröidyn osalta.
 #11.5.2    Taso: 2    Rooli: D
 Varmista, että API:t tarjoavat suostumusmerkkejä; mallien on validoitava merkin laajuus ennen päättelyä.
 #11.5.3    Taso: 2    Rooli: D/V
 Varmista, että evätty tai peruutettu suostumus pysäyttää käsittelyputket 24 tunnin kuluessa.

---

### 11.6 Federated Learning yksityisyyden hallinnalla

 #11.6.1    Taso: 1    Rooli: D
 Varmista, että asiakaspäivityksissä käytetään paikallisen differentiaalisen yksityisyyden melun lisäämistä ennen yhdistämistä.
 #11.6.2    Taso: 2    Rooli: D/V
 Varmista, että koulutusmittarit ovat differentiaalisesti yksityisiä eivätkä koskaan paljasta yksittäisen asiakkaan häviötä.
 #11.6.3    Taso: 2    Rooli: V
 Varmista, että myrkytyksenkestävä aggregointi (esim. Krum/Trimmed-Mean) on otettu käyttöön.
 #11.6.4    Taso: 3    Rooli: V
 Varmista, että muodolliset todistukset osoittavat kokonais-ε-budjetin vähemmän kuin 5 hyötymenetyksellä.

---

#### Viitteet

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

## C12 Valvonta, lokitus ja poikkeavuuksien havaitseminen

### Ohjaustavoite

Tämä osio sisältää vaatimukset reaaliaikaisen ja forensisen näkyvyyden tarjoamiseksi siihen, mitä malli ja muut tekoälykomponentit havaitsevat, tekevät ja palauttavat, jotta uhkat voidaan havaita, luokitella ja oppia niistä.

### C12.1 Pyyntöjen ja vastausten lokitus

 #12.1.1    Taso: 1    Rooli: D/V
 Varmista, että kaikki käyttäjän kehotteet ja mallin vastaukset kirjataan asianmukaisin metatiedoin (esim. aikaleima, käyttäjätunnus, istunnon tunnus, malliversio).
 #12.1.2    Taso: 1    Rooli: D/V
 Varmista, että lokit tallennetaan turvallisiin, pääsynvalvottuihin arkistoihin, joissa on asianmukaiset säilytyskäytännöt ja varmuuskopiointimenettelyt.
 #12.1.3    Taso: 1    Rooli: D/V
 Varmista, että lokien tallennusjärjestelmät toteuttavat salauksen levossa ja siirrossa suojatakseen lokien sisältämää arkaluontoista tietoa.
 #12.1.4    Taso: 1    Rooli: D/V
 Varmista, että herkkä tieto kehotteissa ja vastauksissa suodatetaan tai peitetään automaattisesti ennen kirjaamista, käyttäen konfiguroitavia suodatussääntöjä henkilökohtaisesti tunnistettavien tietojen (PII), tunnistetietojen ja luottamuksellisten tietojen osalta.
 #12.1.5    Taso: 2    Rooli: D/V
 Varmista, että politiikkapäätökset ja turvallisuussuodatustoimet kirjataan riittävällä yksityiskohtaisuudella, jotta sisältömoderaatiojärjestelmien tarkastus ja virheenkorjaus on mahdollista.
 #12.1.6    Taso: 2    Rooli: D/V
 Varmista, että lokin eheys on suojattu esimerkiksi kryptografisilla allekirjoituksilla tai kirjoituskyvyttömällä tallennuksella.

---

### C12.2 Väärinkäytösten tunnistaminen ja hälytys

 #12.2.1    Taso: 1    Rooli: D/V
 Varmista, että järjestelmä havaitsee ja varoittaa tunnetuista jailbreak-kuvioista, kehotuksen injektointiyrityksistä ja vihamielisistä syötteistä käyttämällä allekirjoitusperusteista havaitsemista.
 #12.2.2    Taso: 1    Rooli: D/V
 Varmista, että järjestelmä integroituu olemassa oleviin Security Information and Event Management (SIEM) -alustoihin käyttämällä standardoituja lokimuotoja ja protokollia.
 #12.2.3    Taso: 2    Rooli: D/V
 Varmista, että rikastetuissa turvatapahtumissa on mukana tekoälyyn liittyvää kontekstia, kuten mallin tunnisteet, luottamusarvot ja turvallisuussuodattimen päätökset.
 #12.2.4    Taso: 2    Rooli: D/V
 Varmista, että käyttäytymisanomalian havainnointi tunnistaa epätavalliset keskustelumallit, liialliset uudelleenyritykset tai järjestelmälliset testauskäyttäytymismallit.
 #12.2.5    Taso: 2    Rooli: D/V
 Varmista, että reaaliaikaiset hälytysmekanismit ilmoittavat tietoturvatiimeille, kun mahdollisia sääntörikkomuksia tai hyökkäysyrityksiä havaitaan.
 #12.2.6    Taso: 2    Rooli: D/V
 Varmista, että mukautetut säännöt sisältyvät tekoälyyn liittyvien uhkamallien, kuten koordinoitujen jailbreak-yritysten, kehotteen injektointikampanjoiden ja mallin uuttamisiskujen havaitsemiseen.
 #12.2.7    Taso: 3    Rooli: D/V
 Varmista, että automatisoidut häiriötilanteiden reagointityönkulut voivat eristää vaarantuneet mallit, estää haitalliset käyttäjät ja eskaloida kriittiset tietoturvatapahtumat.

---

### C12.3 Mallin harhan havaitseminen

 #12.3.1    Taso: 1    Rooli: D/V
 Varmista, että järjestelmä seuraa perussuorituskykymittareita, kuten tarkkuutta, luottamusarvoja, viivettä ja virheprosentteja malliversioiden ja aikajaksojen välillä.
 #12.3.2    Taso: 2    Rooli: D/V
 Varmista, että automaattinen hälytys laukeaa, kun suorituskykymittarit ylittävät ennalta määritellyt heikkenemiskynnykset tai poikkeavat merkittävästi vertailuarvoista.
 #12.3.3    Taso: 2    Rooli: D/V
 Varmista, että harhallisuuden tunnistuksen valvontajärjestelmät tunnistavat ja merkitsevät tapaukset, joissa mallin tuottamassa sisällössä on tosiasiallisesti virheellistä, ristiriitaista tai tekaistua tietoa.

---

### C12.4 Suorituskyky- ja käyttäytymistietojen keruu

 #12.4.1    Taso: 1    Rooli: D/V
 Varmista, että operatiiviset mittarit, kuten pyyntöviive, tokenien kulutus, muistin käyttö ja läpimeno, kerätään ja seurataan jatkuvasti.
 #12.4.2    Taso: 1    Rooli: D/V
 Varmista, että onnistumis- ja epäonnistumisprosentteja seurataan virhetyyppien ja niiden juurisyiden luokittelun kanssa.
 #12.4.3    Taso: 2    Rooli: D/V
 Varmista, että resurssien käyttöön liittyvä valvonta kattaa GPU-/CPU-käytön, muistin kulutuksen ja tallennustarpeet sekä hälyttää raja-arvojen ylittyessä.

---

### C12.5 Tekoälyonnettomuuksien hallinnan suunnittelu ja toteutus

 #12.5.1    Taso: 1    Rooli: D/V
 Varmista, että tapauskohtaiset reagointisuunnitelmat käsittelevät nimenomaisesti tekoälyyn liittyviä tietoturvatapahtumia, mukaan lukien mallin vaarantuminen, datan myrkyttäminen ja vihamieliset hyökkäykset.
 #12.5.2    Taso: 2    Rooli: D/V
 Varmista, että tapahtumien käsittelytiimeillä on käytössään tekoälyyn erikoistuneita forensiikkatyökaluja ja asiantuntemusta mallin käyttäytymisen ja hyökkäysvektoreiden tutkimiseksi.
 #12.5.3    Taso: 3    Rooli: D/V
 Varmista, että jälkitapahtuma-analyysissä otetaan huomioon mallin uudelleenkoulutus, turvallisuussuodattimien päivitykset ja opittujen asioiden integrointi turvatoimiin.

---

### C12.5 AI-suorituskyvyn heikkenemisen havaitseminen

Valvoa ja havaita AI-mallin suorituskyvyn ja laadun heikkeneminen ajan myötä.

 #12.5.1    Taso: 1    Rooli: D/V
 Varmista, että mallin tarkkuutta, tarkkuutta, palautusta ja F1-pisteitä seurataan jatkuvasti ja verrataan lähtötason kynnysarvoihin.
 #12.5.2    Taso: 1    Rooli: D/V
 Varmista, että datan siirtymän havaitseminen valvoo syötteen jakauman muutoksia, jotka voivat vaikuttaa mallin suorituskykyyn.
 #12.5.3    Taso: 2    Rooli: D/V
 Varmista, että konseptin muutoksen havaitseminen tunnistaa muutokset syötteiden ja odotettujen tulosten välisessä suhteessa.
 #12.5.4    Taso: 2    Rooli: D/V
 Varmista, että suorituskyvyn heikkeneminen laukaisee automaattiset hälytykset ja käynnistää mallin uudelleenkoulutus- tai korvausprosessit.
 #12.5.5    Taso: 3    Rooli: V
 Varmista, että heikkenemisen juurisyyanalyysi yhdistää suorituskyvyn laskut tietomuutoksiin, infrastruktuuriongelmiin tai ulkoisiin tekijöihin.

---

### C12.6 DAG-visualisointi ja työnkulun tietoturva

Suojaa työnkulun visualisointijärjestelmät tietovuodoilta ja manipulointihyökkäyksiltä.

 #12.6.1    Taso: 1    Rooli: D/V
 Varmista, että DAG-visualisointidataa puhdistetaan poistamalla arkaluonteiset tiedot ennen tallennusta tai siirtoa.
 #12.6.2    Taso: 1    Rooli: D/V
 Varmista, että työnkulun visualisoinnin käyttöoikeudet takaavat, että vain valtuutetut käyttäjät voivat tarkastella agentin päätöspolkuja ja päättelyjälkiä.
 #12.6.3    Taso: 2    Rooli: D/V
 Varmista, että DAG-tietojen eheys on suojattu kryptografisilla allekirjoituksilla ja väärentämisen havaitsemista tukevilla tallennusmekanismeilla.
 #12.6.4    Taso: 2    Rooli: D/V
 Varmista, että työnkulun visualisointijärjestelmät toteuttavat syötteen validoinnin estääkseen injektiohyökkäykset muokatun solmu- tai kaaritiedon kautta.
 #12.6.5    Taso: 3    Rooli: D/V
 Varmista, että reaaliaikaiset DAG-päivitykset ovat nopeusrajoitettuja ja validoituja estämään palvelunestohyökkäykset visualisointijärjestelmiin.

---

### C12.7 Proaktiivinen turvallisuuskäyttäytymisen seuranta

Turvallisuusuhkien havaitseminen ja estäminen proaktiivisen agentin käyttäytymisanalyysin avulla.

 #12.7.1    Taso: 1    Rooli: D/V
 Varmista, että ennakoivat agenttien toiminnot on turvallisuusvarmennettu ennen suoritusta riskinarvioinnin integroinnin avulla.
 #12.7.2    Taso: 2    Rooli: D/V
 Varmista, että autonomisen aloitteen laukaisimet sisältävät turvallisuuskontekstin arvioinnin ja uhkaympäristön kartoituksen.
 #12.7.3    Taso: 2    Rooli: D/V
 Varmista, että ennakoivia käyttäytymismalleja analysoidaan mahdollisten turvallisuusvaikutusten ja ei-toivottujen seurausten varalta.
 #12.7.4    Taso: 3    Rooli: D/V
 Varmista, että turvallisuuskriittiset ennakoivat toimenpiteet vaativat nimenomaiset hyväksymisketjut ja tarkastuskulut.
 #12.7.5    Taso: 3    Rooli: D/V
 Varmista, että käyttäytymisen poikkeavuuksien havaitseminen tunnistaa poikkeamat ennakoivien agenttien malleissa, jotka voivat viitata kompromissiin.

---

### Viitteet

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Ihmisen valvonta, vastuullisuus ja hallinto

### Ohjaustavoite

Tämä luku sisältää vaatimukset ihmisen valvonnan ylläpitämiselle ja selkeiden vastuuketjujen varmistamiselle tekoälyjärjestelmissä sekä selitettävyyden, läpinäkyvyyden ja eettisen hallinnoinnin turvaamiselle koko tekoälyelinkaaren ajan.

---

### C13.1 Hätäpysäytys- ja ohitusmekanismit

Tarjoa sammutus- tai palautusreitit, kun tekoälyjärjestelmän epävakasta käyttäytymistä havaitaan.

 #13.1.1    Taso: 1    Rooli: D/V
 Varmista, että manuaalinen pysäytyskytkin on olemassa AI-mallin päättelyn ja tulosten välittömään keskeyttämiseen.
 #13.1.2    Taso: 1    Rooli: D
 Varmista, että ylikirjoitusvalvonta on käytettävissä vain valtuutetuille henkilöille.
 #13.1.3    Taso: 3    Rooli: D/V
 Varmista, että rollback-prosessit pystyvät palauttamaan aiempiin malliversioihin tai turvalliseen tilaan.
 #13.1.4    Taso: 3    Rooli: V
 Varmista, että ylikirjoitusmekanismit testataan säännöllisesti.

---

### C13.2 Ihminen-silmukassa-päätösten-tarkistuspisteet

Vaatia ihmishyväksynnät, kun panokset ylittävät ennalta määritellyt riskikynnykset.

 #13.2.1    Taso: 1    Rooli: D/V
 Varmista, että korkean riskin tekoälypäätökset vaativat nimenomaisen ihmisen hyväksynnän ennen toteutusta.
 #13.2.2    Taso: 1    Rooli: D
 Varmista, että riskikynnykset on selvästi määritelty ja ne käynnistävät automaattisesti ihmisen tarkastusprosessit.
 #13.2.3    Taso: 2    Rooli: D
 Varmista, että aikarajoihin sidotuissa päätöksissä on varajärjestelyt, jos ihmisen hyväksyntää ei saada vaaditussa ajassa.
 #13.2.4    Taso: 3    Rooli: D/V
 Varmista, että eskalointimenettelyt määrittelevät selkeät valtuustasot eri päätöstyypeille tai riskiluokille, jos sovellettavissa.

---

### C13.3 Vastuun ketju & Tarkastettavuus

Loki operaattorin toimet ja mallin päätökset.

 #13.3.1    Taso: 1    Rooli: D/V
 Varmista, että kaikkien tekoälyjärjestelmän päätösten ja ihmisen tekemien toimenpiteiden tiedot kirjataan aikaleimojen, käyttäjätunnusten ja päätösten perustelujen kanssa.
 #13.3.2    Taso: 2    Rooli: D
 Varmista, etteivät tilintarkastuslokit ole muokattavissa ja että ne sisältävät eheysvarmennusmekanismeja.

---

### C13.4 Selitettävät tekoälymenetelmät

Pintojen ominaisuuksien tärkeys, vastakkaistapaukset ja paikalliset selitykset.

 #13.4.1    Taso: 1    Rooli: D/V
 Varmista, että tekoälyjärjestelmät tarjoavat perustason selitykset päätöksistään ihmisen luettavassa muodossa.
 #13.4.2    Taso: 2    Rooli: V
 Varmista, että selityksen laatu on validoitu ihmisen tekemien arviointitutkimusten ja mittareiden kautta.
 #13.4.3    Taso: 3    Rooli: D/V
 Varmista, että ominaisuuksien tärkeysarvot tai attribuutiomenetelmät (SHAP, LIME jne.) ovat saatavilla kriittisille päätöksille.
 #13.4.4    Taso: 3    Rooli: V
 Varmista, että kontrafaktuaaliset selitykset osoittavat, miten syötteitä voitaisiin muuttaa tulosten muuttamiseksi, jos se on sovellettavissa käyttötapaukseen ja toimialaan.

---

### C13.5 Mallikortit ja käyttöilmoitukset

Pidä yllä mallikortteja tarkoitettuun käyttöön, suorituskykymittareihin ja eettisiin näkökohtiin liittyen.

 #13.5.1    Taso: 1    Rooli: D
 Varmista, että mallikortit dokumentoivat suunnitellut käyttötapaukset, rajoitukset ja tunnetut virhetilanteet.
 #13.5.2    Taso: 1    Rooli: D/V
 Varmista, että suorituskykymittarit eri soveltuvien käyttötapausten osalta on julkistettu.
 #13.5.3    Taso: 2    Rooli: D
 Varmista, että eettiset näkökohdat, vinoumien arvioinnit, oikeudenmukaisuuden arvioinnit, koulutusdatan ominaisuudet ja tunnetut koulutusdatan rajoitukset on dokumentoitu ja päivitetty säännöllisesti.
 #13.5.4    Taso: 2    Rooli: D/V
 Varmista, että mallikortit ovat versionhallinnassa ja niitä ylläpidetään koko mallin elinkaaren ajan muutosten seurannan kera.

---

### C13.6 Epävarmuuden kvantifiointi

Levitä luottamusarvot tai entropiamittarit vastauksiin.

 #13.6.1    Taso: 1    Rooli: D
 Varmista, että tekoälyjärjestelmät antavat tulostensa mukana luottamus- tai epävarmuusarviot.
 #13.6.2    Taso: 2    Rooli: D/V
 Varmista, että epävarmuuskynnykset laukaisevat lisäarvioinnin ihmiseltä tai vaihtoehtoiset päätöspolut.
 #13.6.3    Taso: 2    Rooli: V
 Varmista, että epävarmuuden kvantifiointimenetelmät on kalibroitu ja validoitu todelliseen tosiasiatietoon perustuen.
 #13.6.4    Taso: 3    Rooli: D/V
 Varmista, että epävarmuuden eteneminen säilyy monivaiheisissa tekoälytyönkuluissa.

---

### C13.7 Käyttäjälle suunnatut läpinäkyvyysraportit

Tarjoa säännöllisiä tietoja tapahtumista, poikkeamista ja datan käytöstä.

 #13.7.1    Taso: 1    Rooli: D/V
 Varmista, että tietojen käyttökäytännöt ja käyttäjäluvan hallintakäytännöt on selkeästi viestitty sidosryhmille.
 #13.7.2    Taso: 2    Rooli: D/V
 Varmista, että tekoälyn vaikutusten arvioinnit tehdään ja tulokset sisällytetään raportointiin.
 #13.7.3    Taso: 2    Rooli: D/V
 Varmista, että säännöllisesti julkaistavat avoimuusraportit paljastavat tekoälyonnettomuudet ja toimintamittarit kohtuullisen yksityiskohtaisesti.

#### Viitteet

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

Tämä kattava sanasto tarjoaa määritelmiä keskeisille tekoälyn, koneoppimisen ja turvallisuuden termeille, joita käytetään AISVS:n yhteydessä selkeyden ja yhteisen ymmärryksen varmistamiseksi.

Vastustava esimerkki: Tietoinen syöte, joka on tarkoituksellisesti muokattu saamaan tekoälymalli tekemään virheen, usein lisäämällä hienovaraisia häiriöitä, joita ihmiset eivät huomaa.
​
Vihamielinen kestävyys – Vihamielinen kestävyys tekoälyssä viittaa mallin kykyyn säilyttää suorituskykynsä ja vastustaa tahallisesti suunniteltujen, haitallisten syötteiden aiheuttamaa harhautusta tai manipulointia, jotka on tarkoitettu aiheuttamaan virheitä.
​
Agentti – tekoälyagentit ovat ohjelmistojärjestelmiä, jotka käyttävät tekoälyä tavoitteiden saavuttamiseen ja tehtävien suorittamiseen käyttäjien puolesta. Ne osoittavat päättelykykyä, suunnittelua ja muistia sekä omaavat autonomian tason tehdä päätöksiä, oppia ja sopeutua.
​
Agenttinen tekoäly: tekoälyjärjestelmät, jotka voivat toimia jonkin verran itsenäisesti saavuttaakseen tavoitteita, usein tekemällä päätöksiä ja ryhtymällä toimiin ilman suoraa ihmisen väliintuloa.
​
Attribuuttipohjainen pääsynhallinta (ABAC): Pääsynhallintaparadigma, jossa valtuutuspäätökset perustuvat käyttäjän, resurssin, toiminnon ja ympäristön attribuutteihin, jotka arvioidaan kyselyhetkellä.
​
Takaporttihyökkäys: Tietomyrkytyshyökkäyksen tyyppi, jossa mallia koulutetaan vastaamaan tietyllä tavalla tiettyihin laukaiseviin tekijöihin, mutta käyttäytymään normaalisti muulloin.
​
Vinouma: Järjestelmällisiä virheitä tekoälymallin tuloksissa, jotka voivat johtaa epäoikeudenmukaisiin tai syrjiviin lopputuloksiin tietyille ryhmille tai tietyissä konteksteissa.
​
Harhakäsittelyn hyväksikäyttö: Hyökkäystekniikka, joka hyödyntää tunnettua vinoutuneisuutta tekoälymalleissa manipuloidakseen tuloksia tai lopputuloksia.
​
Cedar: Amazonin politiikan kieli ja moottori hienojakoisten käyttöoikeuksien hallintaan, jota käytetään ABAC:n toteuttamiseen tekoälyjärjestelmissä.
​
Ajatusketju: Tekniikka kielen mallien päättelykyvyn parantamiseksi luomalla välivaiheen päättelyaskeleita ennen lopullisen vastauksen tuottamista.
​
Virtakatkaisijat: Mekanismit, jotka keskeyttävät automaattisesti tekoälyjärjestelmän toiminnot, kun tietyt riskirajat ylitetään.
​
Tietovuoto: Arkaluonteisen tiedon tahaton paljastuminen tekoälymallin tulosteiden tai käyttäytymisen kautta.
​
Datan myrkyttäminen: Harjoitusdatan tahallinen turmelemine mallin eheyden vaarantamiseksi, usein takaovien asentamiseksi tai suorituskyvyn heikentämiseksi.
​
Differential Privacy – Differentielli yksityisyys on matemaattisesti tiukka kehys tilastollisen tiedon julkaisemiseen tietoaineistoista samalla kun suojataan yksittäisten tietueiden yksityisyyttä. Sen avulla tietoja omistava voi jakaa ryhmän yhteenlasketut mallit rajoittaen samalla yksittäisiä henkilöitä koskevan tiedon vuotamista.
​
Upotukset: Tiheät vektoriesitykset datasta (teksti, kuvat jne.), jotka tallentavat semanttisen merkityksen monidimensionaalisessa tilassa.
​
Selitettävyys – Selitettävyys tekoälyssä tarkoittaa tekoälyjärjestelmän kykyä tarjota ihmisille ymmärrettäviä perusteluja tekemilleen päätöksille ja ennusteille sekä antaa näkemyksiä sen sisäisestä toiminnasta.
​
Selitettävä tekoäly (XAI): Tekoälyjärjestelmät, jotka on suunniteltu tarjoamaan ihmisille ymmärrettäviä selityksiä päätöksilleen ja käytökselleen erilaisilla tekniikoilla ja kehikoilla.
​
Federated Learning: Koneoppimisen lähestymistapa, jossa malleja koulutetaan useilla hajautetuilla laitteilla, jotka pitävät hallussaan paikallisia datanäytteitä, ilman että dataa itsessään vaihdetaan.
​
Suojakaiteet: Rajoituksia, jotka on otettu käyttöön estämään tekoälyjärjestelmiä tuottamasta haitallisia, puolueellisia tai muuten ei-toivottuja tuloksia.
​
Hallusinaatio – AI-hallusinaatio viittaa ilmiöön, jossa tekoälymalli tuottaa virheellistä tai harhaanjohtavaa tietoa, joka ei perustu sen koulutusdataan tai tosiasialliseen todellisuuteen.
​
Ihmisen mukanaolo (Human-in-the-Loop, HITL): Järjestelmät, jotka on suunniteltu vaatimaan ihmisen valvontaa, vahvistusta tai puuttumista ratkaisevissa päätöspisteissä.
​
Infrastruktuuri koodina (IaC): Infrastruktuurin hallinta ja käyttöönotto koodin avulla manuaalisten prosessien sijaan, mikä mahdollistaa tietoturvatarkastukset ja yhdenmukaiset käyttöönotot.
​
Jailbreak: Tekniikoita, joita käytetään kiertämään tekoälyjärjestelmien turvallisuusrajoja, erityisesti suurissa kielimalleissa, tuottamaan kiellettyä sisältöä.
​
Vähimmän etuoikeuden periaate: Turvallisuusperiaate, jossa käyttäjille ja prosesseille annetaan vain välttämättömimmät käyttöoikeudet.
​
LIME (Local Interpretable Model-agnostic Explanations): Menetelmä, jolla voidaan selittää minkä tahansa koneoppimisluokittelijan ennusteita likimääräistämällä se paikallisesti tulkittavalla mallilla.
​
Jäsenyyspäätelmähyökkäys: Hyökkäys, jonka tavoitteena on selvittää, käytettiinkö tiettyä datapistettä koneoppimismallin kouluttamiseen.
​
MITRE ATLAS: Vihamielisten uhkien maisema tekoälyjärjestelmille; tietopankki vihamielisistä taktiikoista ja tekniikoista tekoälyjärjestelmiä vastaan.
​
Mallikortti – Mallikortti on dokumentti, joka tarjoaa standardoitua tietoa tekoälymallin suorituskyvystä, rajoituksista, suunnitelluista käyttötarkoituksista ja eettisistä näkökohdista edistääkseen läpinäkyvyyttä ja vastuullista tekoälyn kehitystä.
​
Mallin poiminta: Hyökkäys, jossa hyökkääjä kysyy toistuvasti kohdemallia luodakseen toiminnallisesti vastaavan kopion ilman lupaa.
​
Mallin kääntäminen: Hyökkäys, jossa pyritään rekonstruoimaan koulutusdataa analysoimalla mallin tuottamia tuloksia.
​
Mallin elinkaaren hallinta – AI-mallin elinkaaren hallinta on prosessi, jossa valvotaan kaikkia tekoälymallin olemassaolon vaiheita, mukaan lukien sen suunnittelu, kehitys, käyttöönotto, seuranta, ylläpito ja lopullinen poisto, jotta varmistetaan mallin tehokkuus ja tavoitteiden mukaisuus.
​
Mallin myrkyttäminen: Haavoittuvuuksien tai takaovien lisääminen suoraan malliin koulutusprosessin aikana.
​
Mallin varastaminen/varkaus: Omistusoikeudelliseen malliin perustuvan kopion tai likimääräisen version poimiminen toistuvien kyselyjen kautta.
​
Moniagenttijärjestelmä: Järjestelmä, joka koostuu useista vuorovaikutteisista tekoälyagenttien kokonaisuuksista, joilla kullakin voi olla erilaisia kykyjä ja tavoitteita.
​
OPA (Open Policy Agent): Avoimen lähdekoodin politiikkamoottori, joka mahdollistaa yhtenäisen politiikan noudattamisen koko pinossa.
​
Yksityisyyttä suojaava koneoppiminen (PPML): Menetelmät ja tekniikat koneoppimismallien kouluttamiseen ja käyttöönottoon siten, että koulutusdatan yksityisyys säilyy.
​
Komentointisyrjintä: hyökkäys, jossa haitallisia ohjeita upotetaan syötteisiin mallin tarkoitetun toiminnan ohittamiseksi.
​
RAG (haun tehostama generointi): Tekniikka, joka parantaa suuria kielimalleja hakemalla asiaankuuluvaa tietoa ulkoisista tietolähteistä ennen vastauksen luomista.
​
Red-Teaming: Käytäntö, jossa testataan tekoälyjärjestelmiä aktiivisesti simuloimalla vihamielisiä hyökkäyksiä haavoittuvuuksien tunnistamiseksi.
​
SBOM (Ohjelmistojen materiaaliluettelo): Virallinen tietue, joka sisältää tiedot ja toimitusketjusuhteet erilaisista komponenteista, joita käytetään ohjelmistojen tai tekoälymallien rakentamisessa.
​
SHAP (SHapley Additive exPlanations): Peliteoreettinen lähestymistapa koneoppimismallin tuloksen selittämiseen laskemalla kunkin piirteen osuus ennusteessa.
​
Toimitusketjun hyökkäys: järjestelmän kompromissointi kohdistamalla vähemmän suojattuihin osiin sen toimitusketjussa, kuten kolmannen osapuolen kirjastoihin, tietoaineistoihin tai valmiiksi koulutettuihin malleihin.
​
Siirto-oppiminen: Tekniikka, jossa yhdelle tehtävälle kehitetty malli uudelleenkäytetään lähtökohtana mallille toisessa tehtävässä.
​
Vektoritietokanta: Erityinen tietokanta, joka on suunniteltu tallentamaan korkeulotteisia vektoreita (upotuksia) ja suorittamaan tehokkaita samankaltaisuushakuja.
​
Haavoittuvuusskannaus: Automaattiset työkalut, jotka tunnistavat tunnetut tietoturva-aukot ohjelmistokomponenteissa, mukaan lukien tekoälykehyksiä ja riippuvuuksia.
​
Vesileimaus: Tekniikat näkymättömien tunnisteiden upottamiseksi tekoälyn tuottamaan sisältöön sen alkuperän seuraamiseksi tai tekoälytuotannon havaitsemiseksi.
​
Zero-Day-haavoittuvuus: Aiempia tuntematon haavoittuvuus, jota hyökkääjät voivat käyttää hyväkseen ennen kuin kehittäjät luovat ja ottavat käyttöön korjauksen.

## Liite B: Viitteet

### TODO

## Liite C: AI:n turvallisuuden hallinto ja dokumentointi

### Tavoite

Tämä liite tarjoaa perustavanlaatuiset vaatimukset organisaatiorakenteiden, politiikkojen ja prosessien perustamiseksi tekoälyn turvallisuuden hallitsemiseksi koko järjestelmän elinkaaren ajan.

---

### AC.1 Tekoälyn riskienhallinnan viitekehyksen käyttöönotto

Tarjoa muodollinen viitekehys tekoälyyn liittyvien riskien tunnistamiseksi, arvioimiseksi ja lieventämiseksi koko järjestelmän elinkaaren ajan.

 #AC.1.1    Taso: 1    Rooli: D/V
 Varmista, että tekoälyyn liittyvä riskinarviointimenetelmä on dokumentoitu ja otettu käyttöön.
 #AC.1.2    Taso: 2    Rooli: D
 Varmista, että riskinarvioinnit tehdään tekoälyn elinkaaren keskeisissä vaiheissa ja ennen merkittäviä muutoksia.
 #AC.1.3    Taso: 3    Rooli: D/V
 Varmista, että riskienhallintakehys on yhdenmukainen vakiintuneiden standardien (esim. NIST AI RMF) kanssa.

---

### AC.2 AI:n turvallisuuspolitiikka ja -menettelyt

Määrittele ja valvo organisaation standardeja turvalliselle tekoälyn kehittämiselle, käyttöönotolle ja toiminnalle.

 #AC.2.1    Taso: 1    Rooli: D/V
 Varmista, että dokumentoidut tekoälyn turvallisuuspolitiikat ovat olemassa.
 #AC.2.2    Taso: 2    Rooli: D
 Varmista, että politiikat tarkistetaan ja päivitetään vähintään vuosittain sekä merkittävien uhkakuvaan liittyvien muutosten jälkeen.
 #AC.2.3    Taso: 3    Rooli: D/V
 Varmista, että politiikat kattavat kaikki AISVS-luokat ja sovellettavat sääntelyvaatimukset.

---

### AC.3 Roolit ja vastuut tekoälyn turvallisuudessa

Perusta selkeä vastuu AI-turvallisuudesta koko organisaatiossa.

 #AC.3.1    Taso: 1    Rooli: D/V
 Varmista, että tekoälyn turvallisuusroolit ja vastuut on dokumentoitu.
 #AC.3.2    Taso: 2    Rooli: D
 Varmista, että vastuuhenkilöillä on asianmukainen tietoturvaosaaminen.
 #AC.3.3    Taso: 3    Rooli: D/V
 Varmista, että korkean riskin tekoälyjärjestelmille on perustettu tekoälyn etiikan toimikunta tai hallintoneuvosto.

---

### AC.4 Eettisten tekoälyohjeiden täytäntöönpano

Varmista, että tekoälyjärjestelmät toimivat vakiintuneiden eettisten periaatteiden mukaisesti.

 #AC.4.1    Taso: 1    Rooli: D/V
 Varmista, että eettiset ohjeet tekoälyn kehittämiselle ja käyttöönotolle ovat olemassa.
 #AC.4.2    Taso: 2    Rooli: D
 Varmista, että mekanismit ovat käytössä eettisten rikkomusten havaitsemiseksi ja raportoinniksi.
 #AC.4.3    Taso: 3    Rooli: D/V
 Varmista, että käyttöön otettujen tekoälyjärjestelmien säännölliset eettiset tarkastelut tehdään.

---

### AC.5 AI:n säädöstenmukaisuuden valvonta

Pidä tietoisuutesi ja noudattamisesi ajan tasalla kehittyvien tekoälysäädösten kanssa.

 #AC.5.1    Taso: 1    Rooli: D/V
 Varmista, että on olemassa prosesseja soveltuvien tekoälysäädösten tunnistamiseksi.
 #AC.5.2    Taso: 2    Rooli: D
 Varmista, että kaikkien säädösten vaatimusten noudattaminen arvioidaan.
 #AC.5.3    Taso: 3    Rooli: D/V
 Varmista, että sääntelymuutokset laukaisevat ajallaan tehdyt tarkastelut ja päivitykset tekoälyjärjestelmiin.

### AC.6 Koulutusdatan hallinta, dokumentaatio ja prosessi

 #1.1.2    Taso: 1    Rooli: D/V
 Varmista, että sallitaan vain sellaiset tietoaineistot, jotka on tarkastettu laadun, edustavuuden, eettisen hankinnan ja lisenssien noudattamisen osalta, mikä vähentää myrkytyksen, sisäänrakennetun vinouman ja immateriaalioikeuksien loukkaamisen riskejä.
 #1.1.5    Taso: 2    Rooli: D/V
 Varmista, että luokittelun/merkintöjen laatu varmistetaan tarkistajien ristivertailujen tai yhteisymmärryksen avulla.
 #1.1.6    Taso: 2    Rooli: D/V
 Varmista, että merkittävistä koulutusaineistoista ylläpidetään "datakortteja" tai "aineistoluetteloita", joissa kuvataan ominaisuudet, motivaatiot, koostumus, keräysmenetelmät, esikäsittely ja suositellut/kielletyt käyttötavat.
 #1.3.2    Taso: 2    Rooli: D/V
 Varmista, että tunnistetut vinoumat on lievennetty dokumentoitujen strategioiden avulla, kuten uudelleen tasapainottaminen, kohdennettu datan augmentointi, algoritmiset säädöt (esim. esikäsittely-, käsittely- tai jälkikäsittelytekniikat) tai uudelleen painottaminen, ja että lieventämisen vaikutus sekä oikeudenmukaisuuteen että mallin kokonaiskehitykseen arvioidaan.
 #1.3.3    Taso: 2    Rooli: D/V
 Varmista, että jälkikoulutuksen oikeudenmukaisuuden mittarit arvioidaan ja dokumentoidaan.
 #1.3.4    Taso: 3    Rooli: D/V
 Varmista, että elinkaaren vinouman hallintapolitiikka määrittää omistajat ja tarkasteluvälin.
 #1.4.1    Taso: 2    Rooli: D/V
 Varmista, että merkintä/annotaation laatu taataan selkeiden ohjeiden, tarkastajien ristivertausten, yhteisymmärrysmekanismien (esim. annotaattoreiden välisen yhteenkuuluvuuden seuranta) ja määriteltyjen menettelytapojen avulla erimielisyyksien ratkaisemiseksi.
 #1.4.4    Taso: 3    Rooli: D/V
 Varmista, että turvallisuuden, suojauksen tai oikeudenmukaisuuden kannalta kriittiset tunnisteet (esim. myrkyllisen sisällön, kriittisten lääketieteellisten löydösten tunnistaminen) saavat pakollisen riippumattoman kaksoistarkastuksen tai vastaavan vahvan varmennuksen.
 #1.4.6    Taso: 2    Rooli: D/V
 Varmista, että merkintäohjeet ja -ohjeistukset ovat kattavat, versiohallinnassa ja vertaisarvioituja.
 #1.4.6    Taso: 2    Rooli: D/V
 Varmista, että merkkien tietomallit on määritelty selkeästi ja versiohallittu.
 #1.3.1    Taso: 1    Rooli: D/V
 Varmista, että tietoaineistot on profilisoitu edustavuuden epätasapainon ja mahdollisten puolueellisuuksien varalta laillisesti suojattujen ominaisuuksien (esim. rotu, sukupuoli, ikä) sekä muiden eettisesti herkkiä piirteitä sisältävien tekijöiden osalta, jotka ovat merkityksellisiä mallin sovellusalueella (esim. sosioekonominen asema, sijainti).
 #1.5.3    Taso: 2    Rooli: V
 Varmista, että alan asiantuntijoiden tekemät manuaaliset pistotarkastukset kattavat tilastollisesti merkittävän otoksen (esim. ≥1 % tai 1 000 näytettä, kumpi tahansa on suurempi, tai riskinarvioinnin mukaisesti), jotta tunnistetaan automaation havaitsemattomat hienovaraiset laatuongelmat.
 #1.8.4    Taso: 2    Rooli: D/V
 Varmista, että ulkoistetut tai joukkovoimalla toteutetut merkintätyönkulut sisältävät teknisiä/prosessuaalisia suojatoimia tiedon luottamuksellisuuden, eheys, merkintöjen laadun varmistamiseksi sekä tietovuotojen estämiseksi.
 #1.5.4    Taso: 2    Rooli: D/V
 Varmista, että korjaustoimenpiteet lisätään jäljitettävyystietoihin.
 #1.6.2    Taso: 2    Rooli: D/V
 Varmista, että liputetut näytteet laukaisevat manuaalisen tarkastelun ennen koulutusta.
 #1.6.3    Taso: 2    Rooli: V
 Varmista, että tulokset syötetään mallin turvallisuusasiakirjaan ja tiedotetaan jatkuvasta uhkatiedustelusta.
 #1.6.4    Taso: 3    Rooli: D/V
 Varmista, että tunnistuslogiikka päivitetään uudella uhkatiedolla.
 #1.6.5    Taso: 3    Rooli: D/V
 Varmista, että online-oppimisen putket seuraavat jakauman siirtymää.
 #1.7.1    Taso: 1    Rooli: D/V
 Varmista, että koulutusdatan poistotyönkulut poistavat sekä alkuperäisen että johdetun datan ja arvioivat mallin vaikutuksen, sekä että vaikuttaviin malleihin kohdistuva vaikutus arvioidaan ja tarvittaessa korjataan (esim. uudelleenkoulutuksen tai uudelleensäätämisen kautta).
 #1.7.2    Taso: 2    Rooli: D
 Varmista, että on olemassa mekanismit käyttäjän suostumuksen (ja peruutusten) laajuuden ja tilan seuraamiseksi ja kunnioittamiseksi koulutuksessa käytettävien tietojen osalta, ja että suostumus varmistetaan ennen tietojen sisällyttämistä uusiin koulutusprosesseihin tai merkittäviin mallipäivityksiin.
 #1.7.3    Taso: 2    Rooli: V
 Varmista, että työnkulut testataan vuosittain ja kirjataan ylös.
 #1.8.1    Taso: 2    Rooli: D/V
 Varmista, että kolmannen osapuolen datantoimittajat, mukaan lukien esikoulutettujen mallien ja ulkoisten tietojoukkojen tarjoajat, käyvät läpi turvallisuus-, yksityisyys-, eettisen hankinnan ja datalaadun asianmukaisen tarkastelun ennen kuin heidän datansa tai mallinsa integroidaan.
 #1.8.2    Taso: 1    Rooli: D
 Varmista, että ulkoiset siirrot käyttävät TLS:ää/todennusta ja eheystarkistuksia.
 #1.8.3    Taso: 2    Rooli: D/V
 Varmista, että korkean riskin tietolähteet (esim. avoimen lähdekoodin tietojoukot, joiden alkuperä on tuntematon, tai arvioimattomat toimittajat) saavat tiukemman tarkastelun, kuten erillisen analyysin, laajat laatu-/vinoumatarkistukset ja kohdennetun myrkytyksen havaitsemisen, ennen käyttöä arkaluonteisissa sovelluksissa.
 #1.8.4    Taso: 3    Rooli: D/V
 Varmista, että kolmansilta osapuolilta saadut esikoulutetut mallit arvioidaan niiden sisäisten vinoumien, mahdollisten takaovien, arkkitehtuurin eheyden ja alkuperäisten harjoitusdatan alkuperän osalta ennen hienosäätöä tai käyttöönottoa.
 #1.5.3    Taso: 2    Rooli: D/V
 Varmista, että jos vastustava koulutus on käytössä, vastustavien aineistojen luonti, hallinta ja versiointi on dokumentoitu ja hallittu.
 #1.5.3    Taso: 3    Rooli: D/V
 Varmista, että vihamielistä robustisuus-koulutusta koskevan vaikutuksen mallin suorituskykyyn (sekä puhtaita että vihamielisiä syötteitä vastaan) ja oikeudenmukaisuuden mittareihin arvioidaan, dokumentoidaan ja seurataan.
 #1.5.4    Taso: 3    Rooli: D/V
 Varmista, että vihamielisen harjoittelun ja kestävyyden strategiat tarkistetaan ja päivitetään säännöllisesti vastaamaan kehittyviä vihamielisiä hyökkäystekniikoita.
 #1.4.2    Taso: 2    Rooli: D/V
 Varmista, että epäonnistuneet tietojoukot ovat karanteenissa auditointijäljillä.
 #1.4.3    Taso: 2    Rooli: D/V
 Varmista, että laatuportit estävät heikkolaatuiset tietojoukot ellei poikkeuksia ole hyväksytty.
 #1.11.2    Taso: 2    Rooli: D/V
 Varmista, että synteettisen datan generointiprosessi, parametrit ja suunniteltu käyttötarkoitus on dokumentoitu.
 #1.11.3    Taso: 2    Rooli: D/V
 Varmista, että synteettinen data on arvioitu riskien osalta puolueellisuuden, yksityisyyden vuotamisen ja edustavuusongelmien suhteen ennen sen käyttämistä koulutuksessa.
 #1.12.3    Taso: 2    Rooli: D/V
 Varmista, että epäilyttäviin pääsytapahtumiin liittyvät hälytykset luodaan ja tutkitaan viipymättä.
 #1.13.1    Taso: 1    Rooli: D/V
 Varmista, että kaikille koulutusjoukoille on määritelty nimenomaiset säilytysajat.
 #1.13.2    Taso: 2    Rooli: D/V
 Varmista, että tietoaineistot vanhenevat, poistetaan tai tarkastetaan poistettavaksi niiden elinkaaren lopussa automaattisesti.
 #1.13.3    Taso: 2    Rooli: D/V
 Varmista, että säilytys- ja poistotoimet kirjataan ja ne ovat auditoitavissa.
 #1.14.1    Taso: 2    Rooli: D/V
 Varmista, että tietojen sijaintivaatimukset ja rajat ylittävän siirron vaatimukset on tunnistettu ja niitä noudatetaan kaikissa tietojoukoissa.
 #1.14.2    Taso: 2    Rooli: D/V
 Varmista, että toimialakohtaiset säädökset (esim. terveydenhuolto, rahoitus) on tunnistettu ja otettu huomioon tiedon käsittelyssä.
 #1.14.3    Taso: 2    Rooli: D/V
 Varmista, että noudattaminen asiaankuuluvien tietosuojalakien (esim. GDPR, CCPA) kanssa on dokumentoitu ja tarkistetaan säännöllisesti.
 #1.16.1    Taso: 2    Rooli: D/V
 Varmista, että olemassa on mekanismeja, joilla voidaan vastata rekisteröidyn pyyntöihin pääsystä tietoihin, tietojen oikaisusta, käsittelyn rajoittamisesta tai vastustamisesta.
 #1.16.2    Taso: 2    Rooli: D/V
 Varmista, että pyynnöt kirjataan, seurataan ja täytetään laillisesti määrättyjen aikarajojen puitteissa.
 #1.16.3    Taso: 2    Rooli: D/V
 Varmista, että rekisteröidyn oikeuksia koskevat prosessit testataan ja tarkastetaan säännöllisesti niiden tehokkuuden varmistamiseksi.
 #1.17.1    Taso: 2    Rooli: D/V
 Varmista, että vaikutusanalyysi tehdään ennen tietojoukon version päivittämistä tai korvaamista, kattaen mallin suorituskyvyn, oikeudenmukaisuuden ja vaatimustenmukaisuuden.
 #1.17.2    Taso: 2    Rooli: D/V
 Varmista, että vaikutusanalyysin tulokset dokumentoidaan ja tarkastetaan asiaankuuluvien sidosryhmien toimesta.
 #1.17.3    Taso: 2    Rooli: D/V
 Varmista, että palautussuunnitelmat ovat olemassa siltä varalta, että uudet versiot aiheuttavat hyväksymättömiä riskejä tai taantumia.
 #1.18.1    Taso: 2    Rooli: D/V
 Varmista, että kaikki tiedonmerkinnässä mukana olevat henkilöt on taustatarkastettu ja koulutettu tietoturvassa sekä yksityisyyden suojassa.
 #1.18.2    Taso: 2    Rooli: D/V
 Varmista, että kaikki annotaatiotehtävissä toimivat henkilöt allekirjoittavat salassapito- ja vaitiolositoumukset.
 #1.18.3    Taso: 2    Rooli: D/V
 Varmista, että annotaatioalustat noudattavat käyttöoikeuksien valvontaa ja seuraavat sisäisiä uhkia.

#### Viitteet

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Liite D: Tekoälyn avustama turvallisen koodauksen hallinta ja varmistus

### Tavoite

Tässä luvussa määritellään perustason organisatoriset valvontatoimet tekoälyavusteisten koodausvälineiden turvalliseen ja tehokkaaseen käyttöön ohjelmistokehityksen aikana, varmistaen turvallisuuden ja jäljitettävyyden SDLC:n kaikissa vaiheissa.

---

### AD.1 AI-avusteinen turvallinen koodaus työnkulku

Integroi tekoälytyökalut organisaation turvalliseen ohjelmistokehityksen elinkaareen (SSDLC) heikentämättä olemassa olevia turvallisuusportteja.

 #AD.1.1    Taso: 1    Rooli: D/V
 Varmista, että dokumentoitu työnkulku kuvaa, milloin ja miten tekoälytyökaluja voidaan käyttää koodin generointiin, refaktorointiin tai tarkistamiseen.
 #AD.1.2    Taso: 2    Rooli: D
 Varmista, että työnkulku vastaa kutakin SSDLC-vaihetta (suunnittelu, toteutus, koodikatselmointi, testaus, käyttöönotto).
 #AD.1.3    Taso: 3    Rooli: D/V
 Varmista, että mittarit (esim. haavoittuvuustiheys, keskimääräinen havainta-aika) kerätään tekoälyn tuottamasta koodista ja verrataan ihmisten ainoastaan tuottamiin vertailuarvoihin.

---

### AD.2 AI-työkalujen kelpoistaminen ja uhkamallinnus

Varmista, että tekoälykoodausvälineet arvioidaan turvallisuusominaisuuksien, riskien ja toimitusketjun vaikutusten osalta ennen käyttöönottoa.

 #AD.2.1    Taso: 1    Rooli: D/V
 Varmista, että kunkin tekoälytyökalun uhkamalli tunnistaa väärinkäytön, mallin käänteisen manipuloinnin, tietovuodon ja riippuvuusketjuriskit.
 #AD.2.2    Taso: 2    Rooli: D
 Varmista, että työkalujen arvioinnit sisältävät paikallisten komponenttien staattisen/dynaamisen analyysin sekä SaaS-päätepisteiden (TLS, todennus/valtuutus, lokitus) arvioinnin.
 #AD.2.3    Taso: 3    Rooli: D/V
 Varmista, että arvioinnit noudattavat tunnustettua viitekehystä ja että ne suoritetaan uudelleen merkittävien versionmuutosten jälkeen.

---

### AD.3 Turvallinen kehotteiden ja kontekstinhallinta

Estä salaisuuksien, omistetun koodin ja henkilötietojen vuotaminen, kun rakennat kehyksiä tai konteksteja tekoälymalleille.

 #AD.3.1    Taso: 1    Rooli: D/V
 Varmista, että kirjallinen ohjeistus kieltää salaisuuksien, tunnistetietojen tai luokitellun tiedon lähettämisen kehotteissa.
 #AD.3.2    Taso: 2    Rooli: D
 Varmista, että tekniset kontrollit (asiakaspuolen sensurointi, hyväksytyt kontekstisuodattimet) poistavat automaattisesti arkaluonteiset aineistot.
 #AD.3.3    Taso: 3    Rooli: D/V
 Varmista, että kehotteet ja vastaukset tokenisoidaan, salataan siirron aikana ja levossa, ja että säilytysaika noudattaa tietoluokituspolitiikkaa.

---

### AD.4 Tekoälyn generoiman koodin validointi

Tunnista ja korjaa tekoälyn tuottamista tuloksista aiheutuneet haavoittuvuudet ennen kuin koodi yhdistetään tai otetaan käyttöön.

 #AD.4.1    Taso: 1    Rooli: D/V
 Varmista, että tekoälyn luoma koodi käy aina ihmisen tekemän koodikatselmoinnin läpi.
 #AD.4.2    Taso: 2    Rooli: D
 Varmista, että automaattiset tarkastimet (SAST/IAST/DAST) suoritetaan jokaisessa AI:n generoimaa koodia sisältävässä pull-pyynnössä ja estä yhdistämiset kriittisten löydösten osalta.
 #AD.4.3    Taso: 3    Rooli: D/V
 Varmista, että differentiaalinen fuzz-testaus tai ominaisuuksiin perustuvat testit todistavat turvallisuuskriittiset toiminnot (esim. syötteen validointi, valtuutuslogiikka).

---

### AD.5 Koodiehdotusten selitettävyys ja jäljitettävyys

Tarjoa tarkastajille ja kehittäjille näkemyksiä siitä, miksi ehdotus tehtiin ja kuinka se kehittyi.

 #AD.5.1    Taso: 1    Rooli: D/V
 Varmista, että kehotteen/vastauksen parit tallennetaan commit-tunnuksilla.
 #AD.5.2    Taso: 2    Rooli: D
 Varmista, että kehittäjät voivat näyttää mallin lainaukset (koulutuskatkelmat, dokumentaatio), jotka tukevat ehdotusta.
 #AD.5.3    Taso: 3    Rooli: D/V
 Varmista, että selitettävyysselosteet tallennetaan suunnittelukokonaisuuksien kanssa ja viitataan niihin turvallisuusarvioinneissa, täyttäen ISO/IEC 42001 -jäljitettävyysperiaatteet.

---

### AD.6 Jatkuva palaute ja mallin hienosäätö

Paranna mallin turvallisuuskykyä ajan myötä samalla estäen negatiivinen liike.

 #AD.6.1    Taso: 1    Rooli: D/V
 Varmista, että kehittäjät voivat merkitä epävarmat tai vaatimusten vastaiset ehdotukset, ja että merkinnät seurataan.
 #AD.6.2    Taso: 2    Rooli: D
 Varmista, että koottu palaute ohjaa säännöllistä hienosäätöä tai hakua täydentävää generaatiota tarkastettujen turvallisen koodauksen korpusten avulla (esim. OWASP Cheat Sheets).
 #AD.6.3    Taso: 3    Rooli: D/V
 Varmista, että suljetun silmukan arviointijärjestelmä suorittaa regressiotestit jokaisen hienosäädön jälkeen; turvallisuusmittareiden on täytettävä tai ylityttävä aiemmat vertailuarvot ennen käyttöönottoa.

---

#### Viitteet

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Liite E: Esimerkkejä työkaluista ja kehyksistä

### Tavoite

Tämä luku tarjoaa esimerkkejä työkaluista ja kehyksistä, jotka voivat tukea tietyn AISVS-vaatimuksen toteuttamista tai täyttämistä. Näitä ei tule pitää suosituksina tai kannanottoina AISVS-tiimiltä tai OWASP GenAI Security -hankkeelta.

---

### AE.1 Koulutusdatan hallinta ja harhan hallinta

Työkalut, joita käytetään data-analytiikkaan, hallintaan ja harhan hallintaan.

 #AE.1.1    Osio: 1.1
 Tietovarannon hallintatyökalut: Tietovarannon hallintatyökalut kuten...
 #AE.1.2    Osio: 1.2
 Salaus siirron aikana Käytä TLS:ää HTTPS-pohjaisissa sovelluksissa, työkaluina esimerkiksi openSSL ja Pythonin`ssl`kirjasto.

---

### AE.2 Käyttäjän syötteen validointi

Työkalut käyttäjien syötteiden käsittelyyn ja validointiin.

 #AE.2.1    Osio: 2.1
 Promptin injektiopuolustustyökalut: Käytä suojatyökaluja kuten NVIDIA:n NeMo tai Guardrails AI.

---

