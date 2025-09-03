# C5 Pääsynhallinta ja identiteetti tekoälykomponentteja ja käyttäjiä varten

## Kontrollitavoite

Tehokas pääsynhallinta tekoälyjärjestelmissä edellyttää vankkaa identiteetin hallintaa, kontekstisidonnaista valtuutusta ja ajonaikaista täytäntöönpanoa noudattaen zero-trust-periaatteita. Nämä kontrollit varmistavat, että ihmiset, palvelut ja autonomiset agentit ovat vuorovaikutuksessa mallien, datan ja laskennallisten resurssien kanssa ainoastaan selkeästi myönnettyjen oikeusalueiden puitteissa, jatkuvalla varmistuksella ja auditointimahdollisuuksilla.

---

## C5.1 Identiteetin hallinta ja todentaminen

Perusta kryptografisesti varmennetut identiteetit kaikille entiteeteille, ja ota käyttöön monivaiheinen todennus valtuutettujen toimintojen turvaamiseksi.

|   #   | Kuvaus                                                                                                                                                                                                                                                              | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.1.1 | Varmista, että kaikki inhimilliset käyttäjät ja palvelutilit todentuvat keskitetyn yrityksen identiteetin tarjoajan (IdP) kautta käyttämällä OIDC/SAML-protokollia, joissa on yksilölliset identiteetin ja tokenin vastaavuudet (ei jaettuja tilejä tai tunnuksia). |  1   |  D/V  |
| 5.1.2 | Varmista, että korkean riskin toiminnot (mallin käyttöönotto, painojen vienti, koulutusdatan pääsy, tuotantokonfiguraation muutokset) edellyttävät monivaiheista todennusta tai vaiheistetun todennuksen, jossa istunto uudelleentodennetaan.                       |  1   |  D/V  |
| 5.1.3 | Varmista, että uudet identiteetit käyvät läpi identiteetin todentamisen, joka on NIST 800-63-3 IAL-2:n tai vastaavien standardien mukainen, ennen tuotantojärjestelmän käyttöoikeuksien myöntämistä.                                                                |  2   |   D   |
| 5.1.4 | Varmista, että käyttöoikeustarkastukset suoritetaan neljännesvuosittain automaattisen inaktiivisten tilien havaitsemisen sekä tunnusten kierrätyksen pakottamisen ja poistamisen työnkulkujen avulla.                                                               |  2   |   V   |
| 5.1.5 | Varmista, että federatiiviset tekoäly-agentit todentavat itsensä käyttämällä allekirjoitettuja JWT-väitteitä, joilla on enintään 24 tunnin voimassaoloaika ja jotka sisältävät kryptografisen alkuperätodisteen.                                                    |  3   |  D/V  |

---

## C5.2 Resurssien valtuutus ja minimioikeuksien periaate

Ota käyttöön hienojakoiset pääsynhallintajärjestelmät kaikille tekoälyresursseille, joissa on selkeät lupamallit ja auditointilokit.

|   #   | Kuvaus                                                                                                                                                                                                                                | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.2.1 | Varmista, että jokainen AI-resurssi (tietojoukot, mallit, rajapinnat, vektorikokoelmat, upotusten indeksit, laskenta-instanssit) noudattaa roolipohjaista pääsynhallintaa sekä selkeitä sallimislistoja että oletuskieltopolitiikat.  |  1   |  D/V  |
| 5.2.2 | Varmista, että pienimmän oikeuden periaate on oletusarvoisesti voimassa siten, että palvelutilit aloittavat pelkät lukuoikeudet ja kirjoitusoikeuksille vaaditaan dokumentoitu liiketoiminnallinen peruste.                           |  1   |  D/V  |
| 5.2.3 | Varmista, että kaikki pääsynhallinnan muutokset on linkitetty hyväksyttyihin muutospyyntöihin ja kirjattu muuttumattomasti aikaleimoineen, toimijoiden identiteetteineen, resurssitunnisteineen sekä käyttöoikeusmuutosten arvoineen. |  1   |   V   |
| 5.2.4 | Varmista, että tietoluokitusmerkinnät (PII, PHI, export-controlled, proprietary) leviävät automaattisesti johdettuihin resursseihin (embeddings, prompt caches, model outputs) yhdenmukaisen käytäntöjen noudattamisen kanssa.        |  2   |   D   |
| 5.2.5 | Varmista, että luvattomat pääsyritykset ja käyttöoikeuksien korottumistapahtumat laukaisevat reaaliaikaiset hälytykset kontekstuaalisen metatiedon kanssa SIEM-järjestelmiin enintään 5 minuutin kuluessa.                            |  2   |  D/V  |

---

## C5.3 Dynaaminen politiikan arviointi

Ota käyttöön attribuuttipohjaiset pääsynvalvontamoottorit kontekstinmukaisia valtuutuspäätöksiä varten, auditointiominaisuuksilla varustettuina.

|   #   | Kuvaus                                                                                                                                                                                                                   | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 5.3.1 | Varmista, että valtuutuspäätökset ulkoistetaan omistetulle politiikkamoottorille (OPA, Cedar tai vastaava), joka on saavutettavissa autentikoitujen API-rajapintojen kautta ja jonka eheys on kryptografisesti suojattu. |  1   |  D/V  |
| 5.3.2 | Varmista, että politiikat arvioivat dynaamisia attribuutteja ajonaikaisesti, mukaan lukien käyttäjän luokitustaso, resurssin herkkyysluokitus, pyynnön konteksti, vuokralaisen eristys ja aikarajoitteet.                |  1   |  D/V  |
| 5.3.3 | Varmista, että politiikkamääritelmät ovat versionhallinnassa, vertaisarvioidut ja validoidut automaattisen testauksen avulla CI/CD-putkistoissa ennen tuotantoon käyttöönottoa.                                          |  2   |   D   |
| 5.3.4 | Varmista, että politiikan arviointitulokset sisältävät rakenteelliset päätösten perusteet ja että ne siirretään SIEM-järjestelmiin korrelaatioanalyysiä ja vaatimustenmukaisuusraportointia varten.                      |  2   |   V   |
| 5.3.5 | Varmista, että politiikkavälimuistin TTL-arvot eivät ylitä 5 minuuttia korkean herkkyyden resursseille ja 1 tunti standardiresursseille, joilla on välimuistin invalidointikyky.                                         |  3   |  D/V  |

---

## C5.4 Kyselyaikainen tietoturvan toimeenpano

Ota käyttöön tietokantakerroksen turvallisuustoimenpiteet pakollisella suodatuksella ja rivitasoisilla pääsynvalvontasäännöillä.

|   #   | Kuvaus                                                                                                                                                                                                                                   | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.4.1 | Varmista, että kaikki vektoritietokannan ja SQL-kyselyt sisältävät pakolliset turvallisuussuodattimet (vuokraajatunnus, herkkyysmerkinnät, käyttäjän laajuus), jotka on toteutettu tietokantamoottoritasolla, eikä sovelluskoodissa.     |  1   |  D/V  |
| 5.4.2 | Varmista, että rivitasoinen turvallisuus (RLS) -politiikat sekä kenttäkohtainen maskaus ovat käytössä politiikkojen periytymisen kanssa kaikissa vektoripohjaisissa tietokannoissa, hakindekseissä ja koulutusdataseteissä.              |  1   |  D/V  |
| 5.4.3 | Varmista, että epäonnistuneet valtuutusarvioinnit estävät 'confused deputy attacks' hyökkäykset välittömästi keskeyttämällä kyselyt ja palauttamalla selkeät valtuutusvirhekoodit sen sijaan, että palautettaisiin tyhjiä tulosjoukkoja. |  2   |   D   |
| 5.4.4 | Varmista, että politiikan arvioinnin viive seurataan jatkuvasti automaattisten hälytysten avulla aikakatkaisutilanteiden varalta, jotka voisivat mahdollistaa valtuutuksen ohituksen.                                                    |  2   |   V   |
| 5.4.5 | Varmista, että kyselyjen uudelleenkäynnistysmekanismit arvioivat uudelleen autorisointipolitiikkoja ottaen huomioon aktiivisten käyttäjäsessioiden aikana tapahtuvat dynaamiset käyttöoikeuksien muutokset.                              |  3   |  D/V  |

---

## C5.5 Ulostulon suodatus & Tietojen menetyksen esto

Ota käyttöön jälkikäsittelyn hallintatoimenpiteet luvattoman datan paljastumisen estämiseksi tekoälyn tuottamassa sisällössä.

|   #   | Kuvaus                                                                                                                                                                                                        | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.5.1 | Varmista, että ennusteen jälkeiset suodatusmekanismit skannaavat ja piilottavat luvattomat PII-tiedot, luokitellut tiedot sekä omistusoikeudellisesti suojatun datan ennen sisällön toimittamista pyytäjille. |  1   |  D/V  |
| 5.5.2 | Varmista, että mallien tuotoksissa olevat viitteet, lähdeviitteet ja lähdeilmoitukset on validoitu kutsujan oikeuksien mukaan, ja ne poistetaan, jos havaitaan luvaton pääsy.                                 |  1   |  D/V  |
| 5.5.3 | Varmista, että ulostulomuotojen rajoitukset (siivotut PDF-tiedostot, kuvat, joista metatiedot on poistettu, hyväksytyt tiedostotyypit) ovat voimassa käyttäjäoikeustasojen ja dataluokitusten perusteella.    |  2   |   D   |
| 5.5.4 | Varmista, että redaktiointialgoritmit ovat deterministisiä, versionhallintaan liittyviä ja pitävät yllä audit-lokeja tukeakseen vaatimustenmukaisuustutkimuksia ja forensiikka-analyysiä.                     |  2   |   V   |
| 5.5.5 | Varmista, että korkean riskin redaktiotapahtumat tuottavat adaptiiviset lokit, jotka sisältävät alkuperäisen sisällön kryptografiset hajautusarvot forensiikkaa varten ilman tietojen paljastumista.          |  3   |   V   |

---

## C5.6 Monivuokraus eristys

Varmista kryptografinen ja looginen eristys vuokraajien välillä jaetussa tekoälyinfrastruktuurissa.

|   #   | Kuvaus                                                                                                                                                                                                                                                        | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.6.1 | Varmista, että muistialueet, upotustallennustilat, välimuistitietueet ja väliaikaiset tiedostot ovat nimialueittain eriytettyjä jokaiselle vuokraajalle, ja että turvallinen pyyhkiminen tapahtuu vuokraajan poistamisen tai istunnon päättymisen yhteydessä. |  1   |  D/V  |
| 5.6.2 | Varmista, että jokainen API-pyyntö sisältää autentikoidun vuokraajan tunnisteen, joka on kryptografisesti validoitu suhteessa istuntokontekstiin ja käyttäjäoikeuksiin.                                                                                       |  1   |  D/V  |
| 5.6.3 | Varmista, että verkkopolitiikat toteuttavat oletuskieltosäännöt tenanttienväliseen kommunikaatioon palvelumeshien ja konttien orkestrointialustojen sisällä.                                                                                                  |  2   |   D   |
| 5.6.4 | Varmista, että salausavaimet ovat jokaiselle vuokraajalle ainutlaatuisia CMK-tuen avulla ja että vuokraajien tietovarastojen välillä on kryptografinen eristys.                                                                                               |  3   |   D   |

---

## C5.7 Autonomisen agentin valtuutus

Hallinnoi tekoälyagenttien ja autonomisten järjestelmien käyttöoikeuksia rajattujen kyvykkyystokenien sekä jatkuvan valtuutuksen avulla.

|   #   | Kuvaus                                                                                                                                                                                                                                                                     | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.7.1 | Varmista, että autonomiset agentit saavat laajuudeltaan rajatut kyvykkyystokenit, jotka nimenomaisesti luettelevat sallitut toiminnot, käytettävissä olevat resurssit, aikarajat ja toimintarajoitteet.                                                                    |  1   |  D/V  |
| 5.7.2 | Varmista, että korkeaan riskin kyvykkyydet (tiedostojärjestelmän pääsy, koodin suorittaminen, ulkoiset API-kutsut, taloudelliset tapahtumat) ovat oletusarvoisesti pois käytöstä ja vaativat aktivointiin nimenomaiset hyväksynnät liiketoiminnallisten perustelujen kera. |  1   |  D/V  |
| 5.7.3 | Varmista, että kyvykkyystokenit sidotaan käyttäjäistuntoihin, sisällytä kryptografinen eheyden suojaus, ja varmista, että niitä ei voi tallentaa pysyvästi tai käyttää uudelleen offline-tilanteissa.                                                                      |  2   |   D   |
| 5.7.4 | Varmista, että agentin käynnistämät toiminnot käyvät läpi ABAC-politiikkamoottorin kautta toissijaisessa valtuutuksessa, jossa suoritetaan koko kontekstin arviointi ja auditointilokit tallennetaan.                                                                      |  2   |   V   |
| 5.7.5 | Varmista, että agentin virhetilanteet ja poikkeusten käsittely sisältävät kyvykkyyden laajuutta koskevat tiedot tukemaan tapahtuma-analyysiä ja forensista tutkimusta.                                                                                                     |  3   |   V   |

---

## Lähteet

### Standardit ja viitekehykset

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Toteutusohjeet

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### Tekoälyyn liittyvä turvallisuus

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

