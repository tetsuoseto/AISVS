# C5 Käyttöoikeuksien hallinta ja identiteetti AI-komponenteille ja -käyttäjille

## Ohjaustavoite

Tehokas pääsynhallinta tekoälyjärjestelmissä vaatii vahvaa identiteetin hallintaa, kontekstin huomioon ottavaa valtuutusta ja suoritusaikaisen valvonnan noudattaen nollaluottamusperiaatteita. Nämä hallintamekanismit varmistavat, että ihmiset, palvelut ja autonomiset agentit ovat vuorovaikutuksessa mallien, datan ja laskentaresurssien kanssa vain selkeästi määritellyillä käyttöalueilla, jatkuvalla tarkistuksella ja auditointimahdollisuuksilla.

---

## C5.1 Identiteetin hallinta ja todennus

Perusta kryptografisesti varmennetut identiteetit kaikille yksiköille monivaiheisella todennuksella valtuutettuja toimintoja varten.

|   #   | Kuvaus                                                                                                                                                                                                                                                               | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.1.1 | Varmista, että kaikki ihmiset käyttäjät ja palveluperiaatteet todentuvat keskitetyn yrityksen identiteetin tarjoajan (IdP) kautta käyttäen OIDC/SAML-protokollia ainutlaatuisilla identiteetistä tokeniin kartoittamisilla (ei jaettuja tilejä tai tunnistetietoja). |  1   |  D/V  |
| 5.1.2 | Varmista, että korkean riskin toiminnot (mallin käyttöönotto, painojen vienti, koulutusdatan käyttöoikeus, tuotantoympäristön konfiguraatiomuutokset) vaativat monivaiheisen tunnistautumisen tai vahvistustason korotuksen istunnon uudelleenvahvistuksella.        |  1   |  D/V  |
| 5.1.3 | Varmista, että uudet pääkäyttäjät käyvät läpi henkilöllisyyden todentamisen, joka vastaa NIST 800-63-3 IAL-2 -standardia tai vastaavia vaatimuksia ennen tuotantojärjestelmän käyttöoikeuden saamista.                                                               |  2   |   D   |
| 5.1.4 | Varmista, että käyttöoikeuksien tarkastukset suoritetaan neljännesvuosittain automatisoidun lepotilassa olevien tilien havaitsemisen, tunnistetietojen kierrätyksen valvonnan ja poistoprosessien avulla.                                                            |  2   |   V   |
| 5.1.5 | Varmista, että yhdistetyt tekoälyagentit todentuvat allekirjoitettujen JWT-väitteiden kautta, joiden enimmäiskesto on 24 tuntia ja jotka sisältävät kryptografisen alkuperätodistuksen.                                                                              |  3   |  D/V  |

---

## C5.2 Resurssien valtuutus ja vähimmäisoikeudet

Toteuta hienojakoiset käyttöoikeusvalvonnat kaikille tekoälyresursseille selkeillä lupaamalleilla ja auditointilokeilla.

|   #   | Kuvaus                                                                                                                                                                                                                                                   | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.2.1 | Varmista, että jokainen tekoälyresurssi (aineistot, mallit, päätepisteet, vektorikokoelmat, upotushakemistot, laskenta-instanssit) käyttää roolipohjaista pääsynvalvontaa, jossa on eksplisiittiset sallitut listat ja oletusarvoiset kieltoasetukset.   |  1   |  D/V  |
| 5.2.2 | Varmista, että vähimmän etuoikeuden periaatteet otetaan käyttöön oletuksena palvelutilien osalta, aloittaen vain luku -oikeuksilla, ja että kirjoitusoikeuksille vaaditaan dokumentoitu liiketoiminnan perustelu.                                        |  1   |  D/V  |
| 5.2.3 | Varmista, että kaikki käyttöoikeuksien muutokset liittyvät hyväksyttyihin muutospyyntöihin ja ne kirjataan muuttumattomasti aikaleimojen, tekijäidentiteettien, resurssitunnisteiden ja käyttöoikeuspoikkeamien kera.                                    |  1   |   V   |
| 5.2.4 | Varmista, että tietoluokitusmerkinnät (HENKILÖTIEDOT, POTILASTIEDOT, vientivalvottu, luottamuksellinen) leviävät automaattisesti johdettuihin resursseihin (upotukset, kehotemuistit, mallin tulokset) johdonmukaisesti politiikan noudattamisen kanssa. |  2   |   D   |
| 5.2.5 | Varmista, että luvattomat pääsyyritykset ja oikeuksien eskalointitapahtumat laukaisevat reaaliaikaiset hälytykset kontekstuaalisen metadatan kanssa SIEM-järjestelmiin 5 minuutin sisällä.                                                               |  2   |  D/V  |

---

## C5.3 Dynaaminen politiikan arviointi

Ota käyttöön attribuutteihin perustuvat pääsynvalvontamoottorit (ABAC) kontekstia tunnistavia valtuutuspäätöksiä varten, joissa on auditointimahdollisuudet.

|   #   | Kuvaus                                                                                                                                                                                                            | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.3.1 | Varmista, että valtuutuspäätökset on ulkoistettu omistetulle politiikkamoottorille (OPA, Cedar tai vastaava), johon pääsee käsiksi todennettujen API-rajapintojen kautta, joissa on kryptografinen eheys suojaus. |  1   |  D/V  |
| 5.3.2 | Varmista, että politiikat arvioivat dynaamisia attribuutteja ajonaikaisesti, mukaan lukien käyttäjän pääsyoikeustaso, resurssin herkkyysluokitus, pyyntöympäristö, vuokralaiseristys ja ajalliset rajoitukset.    |  1   |  D/V  |
| 5.3.3 | Varmista, että politiikan määritelmät ovat versionhallinnan alaisia, vertaisarvioituja ja validoituja automaattisten testien avulla CI/CD-putkistoissa ennen tuotantoon käyttöönottoa.                            |  2   |   D   |
| 5.3.4 | Varmista, että politiikan arvioinnin tulokset sisältävät jäsennellyt päätöksentekosisällöt ja ne välitetään SIEM-järjestelmille korrelaatioanalyysiä ja vaatimustenmukaisuusraportointia varten.                  |  2   |   V   |
| 5.3.5 | Varmista, että politiikan välimuistin elinaika-arvot (TTL) eivät ylitä 5 minuuttia korkean herkkyyden resursseille ja 1 tuntia vakiovarastoresursseille, joilla on välimuistin mitätöintiominaisuudet.            |  3   |  D/V  |

---

## C5.4 Kyselyajan turvallisuuden valvonta

Ota käyttöön tietokantakerroksen turvatoimet pakollisella suodatuksella ja rivikohtaisilla suojauspolitiikoilla.

|   #   | Kuvaus                                                                                                                                                                                                                                 | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.4.1 | Varmista, että kaikki vektoritietokannan ja SQL-kyselyt sisältävät pakolliset tietoturvasuodattimet (vuokraajan tunnus, herkkyysluokat, käyttäjän käyttöoikeudet), jotka toteutetaan tietokantamoottorin tasolla, ei sovelluskoodissa. |  1   |  D/V  |
| 5.4.2 | Varmista, että rivitason turvallisuuspolitiikat (RLS) ja kenttätason naamiointi ovat käytössä politiikan periytymisen kanssa kaikissa vektoritietokannoissa, hakemistoissa ja koulutusdatoissa.                                        |  1   |  D/V  |
| 5.4.3 | Varmista, että epäonnistuneet valtuutustarkastukset estävät "sekaantuneen edustajan hyökkäykset" keskeyttämällä haut välittömästi ja palauttamalla selkeät valtuutusvirhekoodit tyhjien tulosjoukkojen palauttamisen sijaan.           |  2   |   D   |
| 5.4.4 | Varmista, että käytäntöjen arviointiviivettä seurataan jatkuvasti automaattisilla hälytyksillä aikakatkaisuehtojen varalta, jotka voisivat mahdollistaa valtuutuksen ohittamisen.                                                      |  2   |   V   |
| 5.4.5 | Varmista, että kyselyn uudelleenyrittomekanismit arvioivat valtuutuspolitiikat uudelleen ottaen huomioon dynaamiset käyttöoikeusmuutokset aktiivisten käyttäjäistuntojen aikana.                                                       |  3   |  D/V  |

---

## C5.5 Tulosteen suodatus ja tiedonmenetyksen ehkäisy

Ota käyttöön jälkikäsittelyn valvontamekanismit estääksesi luvattoman tietojen paljastumisen tekoälyn generoimassa sisällössä.

|   #   | Kuvaus                                                                                                                                                                                                              | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.5.1 | Varmista, että jälkijohdantasuodatusmekanismit tarkistavat ja sensuroivat luvattoman henkilötunnistetiedon (PII), luokitellun tiedon ja oman aineiston ennen sisällön toimittamista pyytäjille.                     |  1   |  D/V  |
| 5.5.2 | Varmista, että mallin tuottamien sitaattien, viitteiden ja lähdeviittausten oikeellisuus tarkistetaan kutsujan oikeuksien mukaisesti, ja ne poistetaan, jos luvaton pääsy havaitaan.                                |  1   |  D/V  |
| 5.5.3 | Varmista, että tulostemuotojen rajoitukset (puhdistetut PDF-tiedostot, metatiedot poistettu kuvista, hyväksytyt tiedostotyypit) toteutetaan käyttäjän käyttöoikeustasojen ja dataluokitusten perusteella.           |  2   |   D   |
| 5.5.4 | Varmista, että sensurointialgoritmit ovat deterministisiä, versiohallittuja ja säilyttävät tarkastuslokit tukemaan vaatimustenmukaisuustutkimuksia ja oikeuslääketieteellisiä analyyseja.                           |  2   |   V   |
| 5.5.5 | Varmista, että korkean riskin peittotapahtumat luovat adaptiivisia lokitietoja, jotka sisältävät alkuperäisen sisällön kryptografiset tiivisteet oikeustieteellistä palautusta varten ilman tietojen paljastumista. |  3   |   V   |

---

## C5.6 Monivuokralais-eristys

Varmista kryptografinen ja looginen eristys käyttäjien välillä jaetussa tekoälyinfrastruktuurissa.

|   #   | Kuvaus                                                                                                                                                                                                                                                       | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 5.6.1 | Varmista, että muistitilat, upotusten tallennustilat, välimuistimerkinnät ja väliaikaiset tiedostot ovat nimialueittain eroteltuja vuokralaisittain, ja että vuokralaisen poistamisen tai istunnon päättämisen yhteydessä suoritetaan turvallinen puhdistus. |  1   |  D/V  |
| 5.6.2 | Varmista, että jokainen API-pyyntö sisältää todennetun vuokralaisidentifikaattorin, joka on kryptografisesti validoitu istuntokontekstin ja käyttäjän käyttöoikeuksien perusteella.                                                                          |  1   |  D/V  |
| 5.6.3 | Varmista, että verkkopolitiikat toteuttavat oletusarvoisesti estävät säännöt monivuokralaisten väliselle viestinnälle palveluverkkojen ja konttien orkestrointialustojen sisällä.                                                                            |  2   |   D   |
| 5.6.4 | Varmista, että salausavaimet ovat uniikkeja kullekin vuokralaiselle asiakas hallinnoidun avaimen (CMK) tuella ja että vuokralaisten tietovarastojen välillä on kryptografinen eristys.                                                                       |  3   |   D   |

---

## C5.7 Autonomisen agentin valtuutus

Ohjaoikeudet AI-agentteihin ja autonomisiin järjestelmiin laajennettujen käyttöoikeustunnusten ja jatkuvan valtuutuksen avulla.

|   #   | Kuvaus                                                                                                                                                                                                                                                                  | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 5.7.1 | Varmista, että autonomiset agentit saavat rajatut valtuustunnukset, jotka yksilöivät nimenomaisesti sallitut toiminnot, käytettävissä olevat resurssit, aikarajat ja toimintarajoitukset.                                                                               |  1   |  D/V  |
| 5.7.2 | Varmista, että korkean riskin toiminnot (tiedostojärjestelmän käyttö, koodin suoritus, ulkoiset API-kutsut, taloudelliset siirrot) ovat oletuksena poissa käytöstä ja edellyttävät nimenomaisia hyväksyntöjä aktivoitumista varten liiketoiminnallisilla perusteluilla. |  1   |  D/V  |
| 5.7.3 | Varmista, että käyttöoikeustunnukset on sidottu käyttäjäistuntoihin, niissä on kryptografinen eheysturva, eikä niitä voi säilyttää tai käyttää uudelleen offline-tilanteissa.                                                                                           |  2   |   D   |
| 5.7.4 | Varmista, että agentin aloittamat toimenpiteet käyvät läpi toissijaisen hyväksynnän ABAC-politiikkamoottorin kautta täydellisen kontekstin arvioinnin ja tarkastuslokiauditoinnin kanssa.                                                                               |  2   |   V   |
| 5.7.5 | Varmista, että agentin virhetilanteet ja poikkeusten käsittely sisältävät kyvykkyysalueen tiedot tukemaan tapahtumien analysointia ja oikeuslääketieteellistä tutkimusta.                                                                                               |  3   |   V   |

---

## Viitteet

### Standardit ja kehykset

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Toteutusoppaat

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### AI-spesifinen turvallisuus

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

