# C12 Valvonta, lokitus ja poikkeavuuksien havaitseminen

## Ohjaustavoite

Tämä osio sisältää vaatimukset reaaliaikaisen ja forensisen näkyvyyden tarjoamiseksi siihen, mitä malli ja muut tekoälykomponentit havaitsevat, tekevät ja palauttavat, jotta uhkat voidaan havaita, luokitella ja oppia niistä.

## C12.1 Pyyntöjen ja vastausten lokitus

|   #    | Kuvaus                                                                                                                                                                                                                                                                    | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.1.1 | Varmista, että kaikki käyttäjän kehotteet ja mallin vastaukset kirjataan asianmukaisin metatiedoin (esim. aikaleima, käyttäjätunnus, istunnon tunnus, malliversio).                                                                                                       |  1   |  D/V  |
| 12.1.2 | Varmista, että lokit tallennetaan turvallisiin, pääsynvalvottuihin arkistoihin, joissa on asianmukaiset säilytyskäytännöt ja varmuuskopiointimenettelyt.                                                                                                                  |  1   |  D/V  |
| 12.1.3 | Varmista, että lokien tallennusjärjestelmät toteuttavat salauksen levossa ja siirrossa suojatakseen lokien sisältämää arkaluontoista tietoa.                                                                                                                              |  1   |  D/V  |
| 12.1.4 | Varmista, että herkkä tieto kehotteissa ja vastauksissa suodatetaan tai peitetään automaattisesti ennen kirjaamista, käyttäen konfiguroitavia suodatussääntöjä henkilökohtaisesti tunnistettavien tietojen (PII), tunnistetietojen ja luottamuksellisten tietojen osalta. |  1   |  D/V  |
| 12.1.5 | Varmista, että politiikkapäätökset ja turvallisuussuodatustoimet kirjataan riittävällä yksityiskohtaisuudella, jotta sisältömoderaatiojärjestelmien tarkastus ja virheenkorjaus on mahdollista.                                                                           |  2   |  D/V  |
| 12.1.6 | Varmista, että lokin eheys on suojattu esimerkiksi kryptografisilla allekirjoituksilla tai kirjoituskyvyttömällä tallennuksella.                                                                                                                                          |  2   |  D/V  |

---

## C12.2 Väärinkäytösten tunnistaminen ja hälytys

|   #    | Kuvaus                                                                                                                                                                                                | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.2.1 | Varmista, että järjestelmä havaitsee ja varoittaa tunnetuista jailbreak-kuvioista, kehotuksen injektointiyrityksistä ja vihamielisistä syötteistä käyttämällä allekirjoitusperusteista havaitsemista. |  1   |  D/V  |
| 12.2.2 | Varmista, että järjestelmä integroituu olemassa oleviin Security Information and Event Management (SIEM) -alustoihin käyttämällä standardoituja lokimuotoja ja protokollia.                           |  1   |  D/V  |
| 12.2.3 | Varmista, että rikastetuissa turvatapahtumissa on mukana tekoälyyn liittyvää kontekstia, kuten mallin tunnisteet, luottamusarvot ja turvallisuussuodattimen päätökset.                                |  2   |  D/V  |
| 12.2.4 | Varmista, että käyttäytymisanomalian havainnointi tunnistaa epätavalliset keskustelumallit, liialliset uudelleenyritykset tai järjestelmälliset testauskäyttäytymismallit.                            |  2   |  D/V  |
| 12.2.5 | Varmista, että reaaliaikaiset hälytysmekanismit ilmoittavat tietoturvatiimeille, kun mahdollisia sääntörikkomuksia tai hyökkäysyrityksiä havaitaan.                                                   |  2   |  D/V  |
| 12.2.6 | Varmista, että mukautetut säännöt sisältyvät tekoälyyn liittyvien uhkamallien, kuten koordinoitujen jailbreak-yritysten, kehotteen injektointikampanjoiden ja mallin uuttamisiskujen havaitsemiseen.  |  2   |  D/V  |
| 12.2.7 | Varmista, että automatisoidut häiriötilanteiden reagointityönkulut voivat eristää vaarantuneet mallit, estää haitalliset käyttäjät ja eskaloida kriittiset tietoturvatapahtumat.                      |  3   |  D/V  |

---

## C12.3 Mallin harhan havaitseminen

|   #    | Kuvaus                                                                                                                                                                                                            | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.3.1 | Varmista, että järjestelmä seuraa perussuorituskykymittareita, kuten tarkkuutta, luottamusarvoja, viivettä ja virheprosentteja malliversioiden ja aikajaksojen välillä.                                           |  1   |  D/V  |
| 12.3.2 | Varmista, että automaattinen hälytys laukeaa, kun suorituskykymittarit ylittävät ennalta määritellyt heikkenemiskynnykset tai poikkeavat merkittävästi vertailuarvoista.                                          |  2   |  D/V  |
| 12.3.3 | Varmista, että harhallisuuden tunnistuksen valvontajärjestelmät tunnistavat ja merkitsevät tapaukset, joissa mallin tuottamassa sisällössä on tosiasiallisesti virheellistä, ristiriitaista tai tekaistua tietoa. |  2   |  D/V  |

---

## C12.4 Suorituskyky- ja käyttäytymistietojen keruu

|   #    | Kuvaus                                                                                                                                                     | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.4.1 | Varmista, että operatiiviset mittarit, kuten pyyntöviive, tokenien kulutus, muistin käyttö ja läpimeno, kerätään ja seurataan jatkuvasti.                  |  1   |  D/V  |
| 12.4.2 | Varmista, että onnistumis- ja epäonnistumisprosentteja seurataan virhetyyppien ja niiden juurisyiden luokittelun kanssa.                                   |  1   |  D/V  |
| 12.4.3 | Varmista, että resurssien käyttöön liittyvä valvonta kattaa GPU-/CPU-käytön, muistin kulutuksen ja tallennustarpeet sekä hälyttää raja-arvojen ylittyessä. |  2   |  D/V  |

---

## C12.5 Tekoälyonnettomuuksien hallinnan suunnittelu ja toteutus

|   #    | Kuvaus                                                                                                                                                                                                          | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.5.1 | Varmista, että tapauskohtaiset reagointisuunnitelmat käsittelevät nimenomaisesti tekoälyyn liittyviä tietoturvatapahtumia, mukaan lukien mallin vaarantuminen, datan myrkyttäminen ja vihamieliset hyökkäykset. |  1   |  D/V  |
| 12.5.2 | Varmista, että tapahtumien käsittelytiimeillä on käytössään tekoälyyn erikoistuneita forensiikkatyökaluja ja asiantuntemusta mallin käyttäytymisen ja hyökkäysvektoreiden tutkimiseksi.                         |  2   |  D/V  |
| 12.5.3 | Varmista, että jälkitapahtuma-analyysissä otetaan huomioon mallin uudelleenkoulutus, turvallisuussuodattimien päivitykset ja opittujen asioiden integrointi turvatoimiin.                                       |  3   |  D/V  |

---

## C12.5 AI-suorituskyvyn heikkenemisen havaitseminen

Valvoa ja havaita AI-mallin suorituskyvyn ja laadun heikkeneminen ajan myötä.

|   #    | Kuvaus                                                                                                                                          | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.5.1 | Varmista, että mallin tarkkuutta, tarkkuutta, palautusta ja F1-pisteitä seurataan jatkuvasti ja verrataan lähtötason kynnysarvoihin.            |  1   |  D/V  |
| 12.5.2 | Varmista, että datan siirtymän havaitseminen valvoo syötteen jakauman muutoksia, jotka voivat vaikuttaa mallin suorituskykyyn.                  |  1   |  D/V  |
| 12.5.3 | Varmista, että konseptin muutoksen havaitseminen tunnistaa muutokset syötteiden ja odotettujen tulosten välisessä suhteessa.                    |  2   |  D/V  |
| 12.5.4 | Varmista, että suorituskyvyn heikkeneminen laukaisee automaattiset hälytykset ja käynnistää mallin uudelleenkoulutus- tai korvausprosessit.     |  2   |  D/V  |
| 12.5.5 | Varmista, että heikkenemisen juurisyyanalyysi yhdistää suorituskyvyn laskut tietomuutoksiin, infrastruktuuriongelmiin tai ulkoisiin tekijöihin. |  3   |   V   |

---

## C12.6 DAG-visualisointi ja työnkulun tietoturva

Suojaa työnkulun visualisointijärjestelmät tietovuodoilta ja manipulointihyökkäyksiltä.

|   #    | Kuvaus                                                                                                                                                       | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 12.6.1 | Varmista, että DAG-visualisointidataa puhdistetaan poistamalla arkaluonteiset tiedot ennen tallennusta tai siirtoa.                                          |  1   |  D/V  |
| 12.6.2 | Varmista, että työnkulun visualisoinnin käyttöoikeudet takaavat, että vain valtuutetut käyttäjät voivat tarkastella agentin päätöspolkuja ja päättelyjälkiä. |  1   |  D/V  |
| 12.6.3 | Varmista, että DAG-tietojen eheys on suojattu kryptografisilla allekirjoituksilla ja väärentämisen havaitsemista tukevilla tallennusmekanismeilla.           |  2   |  D/V  |
| 12.6.4 | Varmista, että työnkulun visualisointijärjestelmät toteuttavat syötteen validoinnin estääkseen injektiohyökkäykset muokatun solmu- tai kaaritiedon kautta.   |  2   |  D/V  |
| 12.6.5 | Varmista, että reaaliaikaiset DAG-päivitykset ovat nopeusrajoitettuja ja validoituja estämään palvelunestohyökkäykset visualisointijärjestelmiin.            |  3   |  D/V  |

---

## C12.7 Proaktiivinen turvallisuuskäyttäytymisen seuranta

Turvallisuusuhkien havaitseminen ja estäminen proaktiivisen agentin käyttäytymisanalyysin avulla.

|   #    | Kuvaus                                                                                                                                                | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.7.1 | Varmista, että ennakoivat agenttien toiminnot on turvallisuusvarmennettu ennen suoritusta riskinarvioinnin integroinnin avulla.                       |  1   |  D/V  |
| 12.7.2 | Varmista, että autonomisen aloitteen laukaisimet sisältävät turvallisuuskontekstin arvioinnin ja uhkaympäristön kartoituksen.                         |  2   |  D/V  |
| 12.7.3 | Varmista, että ennakoivia käyttäytymismalleja analysoidaan mahdollisten turvallisuusvaikutusten ja ei-toivottujen seurausten varalta.                 |  2   |  D/V  |
| 12.7.4 | Varmista, että turvallisuuskriittiset ennakoivat toimenpiteet vaativat nimenomaiset hyväksymisketjut ja tarkastuskulut.                               |  3   |  D/V  |
| 12.7.5 | Varmista, että käyttäytymisen poikkeavuuksien havaitseminen tunnistaa poikkeamat ennakoivien agenttien malleissa, jotka voivat viitata kompromissiin. |  3   |  D/V  |

---

## Viitteet

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

