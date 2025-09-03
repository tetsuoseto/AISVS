# C12 Monitorointi, lokitus ja poikkeavuuksien havaitseminen

## Kontrollitavoite

Tämä osio määrittelee vaatimukset reaaliaikaisen ja forensisen näkyvyyden toteuttamiselle siihen, mitä malli ja muut tekoälykomponentit näkevät, tekevät ja palauttavat, jotta uhkia voidaan havaita, priorisoida ja niistä voidaan oppia.

## C12.1 Pyyntö- ja vastekirjaus

|   #    | Kuvaus                                                                                                                                                                                                                                                | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.1.1 | Varmista, että kaikki käyttäjän syötteet ja mallin vastaukset kirjataan asianmukaisilla metatiedoilla (esim. aikaleima, käyttäjä-ID, istunnon ID, mallin versio).                                                                                     |  1   |  D/V  |
| 12.1.2 | Varmista, että lokit tallennetaan turvallisiin, pääsynvalvontaan rajoitettuihin varastoihin, joihin liittyvät asianmukaiset säilytyspolitiikat ja varmuuskopiointimenettelyt.                                                                         |  1   |  D/V  |
| 12.1.3 | Varmista, että lokien tallennusjärjestelmät käyttävät sekä levon että siirron salausmenetelmiä suojatakseen lokien sisältämää arkaluonteista tietoa.                                                                                                  |  1   |  D/V  |
| 12.1.4 | Varmista, että kehotteiden ja tulosteiden herkät tiedot on automaattisesti piilotettu tai peitetty ennen lokitusta, konfiguroitavissa olevien piilotussääntöjen avulla henkilötietojen, tunnistetietojen ja yrityksen omistaman tiedon suojaamiseksi. |  1   |  D/V  |
| 12.1.5 | Varmista, että politiikkapäätökset ja turvallisuussuodatustoimenpiteet kirjataan riittävän yksityiskohtaisesti, jotta sisällön moderointijärjestelmien auditointi ja virheenkorjaus ovat mahdollisia.                                                 |  2   |  D/V  |
| 12.1.6 | Varmista, että lokin eheys on turvattu esimerkiksi kryptografisilla allekirjoituksilla tai kirjoitusrajoitetulla tallennuksella.                                                                                                                      |  2   |  D/V  |

---

## C12.2 Väärinkäytösten havaitseminen ja hälyttäminen

|   #    | Kuvaus                                                                                                                                                                                                | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.2.1 | Varmista, että järjestelmä havaitsee ja varoittaa tunnetuista jailbreak-malleista, kehotteen injektiokokeista ja vihamielisistä syötteistä käyttämällä allekirjoitusperusteista havaitsemista.        |  1   |  D/V  |
| 12.2.2 | Varmista, että järjestelmä integroituu olemassa olevien SIEM-alustojen kanssa käyttämällä standardeja lokimuotoja ja protokollia.                                                                     |  1   |  D/V  |
| 12.2.3 | Varmista, että rikastetut turvallisuustapahtumat sisältävät tekoälyyn liittyvää kontekstia, kuten mallien tunnisteet, todennäköisyysarvot ja turvallisuussuodattimen päätökset.                       |  2   |  D/V  |
| 12.2.4 | Varmista, että käyttäytymisen poikkeavuuksien havaitsemisjärjestelmä tunnistaa epätavallisia keskustelukuvioita, liiallisia uusintayrityksiä tai järjestelmällisiä tiedustelukäyttäytymisiä.          |  2   |  D/V  |
| 12.2.5 | Varmista, että reaaliaikaiset hälytysjärjestelmät ilmoittavat turvallisuustiimille, kun havaitaan mahdolliset käytäntöjen rikkomukset tai hyökkäysyritykset.                                          |  2   |  D/V  |
| 12.2.6 | Varmista, että mukautetut säännöt sisältyvät tekoälyyn liittyvien uhkakuvioiden havaitsemiseen, mukaan lukien koordinoidut jailbreakyritykset, prompt injection kampanjat ja mallinpoistohyökkäykset. |  2   |  D/V  |
| 12.2.7 | Varmista, että automatisoidut häiriötilanteisiin reagoivat työnkulut voivat eristää kompromettoituneet mallit, estää haitalliset käyttäjät ja eskaloida kriittisiä turvallisuustapahtumia.            |  3   |  D/V  |

---

## C12.3 Mallin driftin havaitseminen

|   #    | Kuvaus                                                                                                                                                                                                          | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.3.1 | Varmista, että järjestelmä seuraa perussuorituskykymittareita, kuten tarkkuutta, luottamusarvoja, latenssia ja virheprosentteja malliversioiden ja aikajaksojen välillä.                                        |  1   |  D/V  |
| 12.3.2 | Varmista, että automatisoidut hälytykset laukaisevat, kun suorituskykymittarit ylittävät ennalta määritetyt heikentymisrajat tai poikkeavat merkittävästi viitearvoista.                                        |  2   |  D/V  |
| 12.3.3 | Varmista, että hallusinaatioiden havaitsemista varten tarkoitetut monitorit tunnistavat ja merkitsevät tilanteet, joissa mallin tuottama tieto on faktuaalisesti virheellistä, epäjohdonmukaista tai keksittyä. |  2   |  D/V  |

---

## C12.4 Suorituskyvyn ja käyttäytymisen telemetria

|   #    | Kuvaus                                                                                                                                                      | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.4.1 | Varmista, että operatiiviset mittarit, kuten pyyntöviive, tokenien kulutus, muistin käyttö ja läpäisynopeus, kerätään ja seurataan jatkuvasti.              |  1   |  D/V  |
| 12.4.2 | Varmista, että menestys- ja epäonnistumisprosentit seurataan virhetyyppien ja niiden juurisyiden kategorisoinnilla.                                         |  1   |  D/V  |
| 12.4.3 | Varmista, että resurssien käytön seuranta sisältää GPU:n ja CPU:n käytön, muistin käytön ja tallennusvaatimukset sekä hälytykset, kun raja-arvot ylittyvät. |  2   |  D/V  |

---

## C12.5 tekoälyn tapahtumavasteen suunnittelu ja toteutus

|   #    | Kuvaus                                                                                                                                                                                                       | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 12.5.1 | Varmista, että tapahtumiin reagoimisen suunnitelmat ottavat erityisesti huomioon tekoälyyn liittyvät turvallisuustapahtumat, mukaan lukien mallin kompromissi, datan myrkyttäminen ja vastustajahyökkäykset. |  1   |  D/V  |
| 12.5.2 | Varmista, että incident response-tiimeillä on pääsy AI-spesifisiin forensiikkatyökaluihin ja asiantuntemukseen mallin käyttäytymisen ja hyökkäysvektoreiden tutkimiseksi.                                    |  2   |  D/V  |
| 12.5.3 | Varmista, että tapahtuman jälkeinen analyysi sisältää mallin uudelleenkoulutuksen harkinnan, turvallisuussuodattimien päivitykset sekä opittujen kokemusten integroinnin turvallisuustoimenpiteisiin.        |  3   |  D/V  |

---

## C12.5 Tekoälyn suorituskyvyn heikkenemisen havaitseminen

Seuraa ja havaitse tekoälymallin suorituskyvyn ja laadun heikkenemistä ajan kuluessa.

|   #    | Kuvaus                                                                                                                                                                  | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.5.1 | Varmista, että mallin tarkkuus, precision, recall ja F1-arvot ovat jatkuvassa seurannassa ja niitä verrataan peruskynnysarvoihin.                                       |  1   |  D/V  |
| 12.5.2 | Varmista, että datan poikkeaman havaitseminen seuraa syötteen jakauman muutoksia, jotka voivat vaikuttaa mallin suorituskykyyn.                                         |  1   |  D/V  |
| 12.5.3 | Varmista, että konseptimuutoksen havaitseminen tunnistaa syötteiden ja odotettujen tulosten välisen suhteen muutoksia.                                                  |  2   |  D/V  |
| 12.5.4 | Varmista, että suorituskyvyn heikkeneminen laukaisee automaattiset hälytykset ja käynnistää mallin uudelleenkoulutuksen tai korvaavien työnkulkujen prosessit.          |  2   |  D/V  |
| 12.5.5 | Varmista, että heikentymisen juurisyiden analyysi korreloi suorituskyvyn heikkenemisen kanssa datamuutosten, infrastruktuuri-ongelmien tai ulkoisten tekijöiden kanssa. |  3   |   V   |

---

## C12.6 DAG-visualisointi ja työnkulun turvallisuus

Suojaa työnkulun visualisointijärjestelmiä tiedon vuotumiselta ja manipulointihyökkäyksiltä.

|   #    | Kuvaus                                                                                                                                                                      | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.6.1 | Varmista, että DAG-visuaatiotiedot on puhdistettu poistamaan arkaluontoiset tiedot ennen tallennusta tai siirtämistä.                                                       |  1   |  D/V  |
| 12.6.2 | Varmista, että työnkulun visualisoinnin käyttöoikeuksien hallinta takaa, että vain valtuutetut käyttäjät voivat nähdä agentin päätöspolut ja päättelyn jäljet.              |  1   |  D/V  |
| 12.6.3 | Varmista, että DAG-tiedon eheys on suojattu kryptografisilla allekirjoituksilla ja muokkauksen havaitsemiseen tarkoitetuilla tallennusmekanismeilla.                        |  2   |  D/V  |
| 12.6.4 | Varmista, että työnkulun visualisointijärjestelmät toteuttavat syötteen validoinnin estääkseen injektiohyökkäykset, joita muokatut solmu- tai kaaritiedot voivat aiheuttaa. |  2   |  D/V  |
| 12.6.5 | Varmista, että reaaliaikaiset DAG-päivitykset ovat nopeusrajoitettuja ja vahvistettuja estämään palvelunestohyökkäyksiä visualisointijärjestelmissä.                        |  3   |  D/V  |

---

## C12.7 Proaktiivinen turvallisuuskäyttäytymisen seuranta

Turvallisuusuhkien havaitseminen ja ehkäisy proaktiivisen agentin käyttäytymisanalyysin kautta.

|   #    | Kuvaus                                                                                                                                                                        | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.7.1 | Varmista, että proaktiivisten agenttien käyttäytyminen on turvallisuusvarmennettu ennen suoritusta riskinarvioinnin integroinnin avulla.                                      |  1   |  D/V  |
| 12.7.2 | Varmista, että autonomisten aloitteiden laukaisimet sisältävät turvallisuuskontekstin arvioinnin ja uhkakuvan arvioinnin.                                                     |  2   |  D/V  |
| 12.7.3 | Varmista, että proaktiiviset käyttäytymismallit analysoidaan mahdollisten turvallisuusvaikutusten ja tahattomien seurausten varalta.                                          |  2   |  D/V  |
| 12.7.4 | Varmista, että turvallisuuskriittiset proaktiiviset toimenpiteet vaativat nimenomaiset hyväksyntäketjut, joihin liittyy auditointijälkiä.                                     |  3   |  D/V  |
| 12.7.5 | Varmista, että käyttäytymisen poikkeavuuksien havaitseminen tunnistaa proaktiivisten agenttien toimintamalleissa ilmenevät poikkeavuudet, jotka voivat viitata kompromissiin. |  3   |  D/V  |

---

## Lähteet

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

