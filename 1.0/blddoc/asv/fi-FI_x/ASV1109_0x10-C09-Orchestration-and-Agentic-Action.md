# 9 Autonominen orkestrointi ja agenttipohjainen toiminnan turvallisuus

## Ohjaustavoite

Varmista, että autonomiset tai moniagenttiset tekoälyjärjestelmät voivat suorittaa vain toimenpiteitä, jotka on nimenomaisesti tarkoitettu, todennettu, tarkastettavissa ja jotka pysyvät rajatuissa kustannus- ja riskikynnyksissä. Tämä suojaa uhkilta, kuten autonomisen järjestelmän vaarantuminen, työkalujen väärinkäyttö, agenttien silmukan tunnistus, viestinnän kaappaus, identiteetin väärennös, parven manipulointi ja tarkoituksen manipulointi.

---

## 9.1 Agentin tehtäväsuunnittelu ja rekursiobudjetit

Rajoita rekursiivisia suunnitelmia ja pakota ihmisen tarkistuspisteet valtuutetuissa toiminnoissa.

|   #   | Kuvaus                                                                                                                                                                                                    | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.1.1 | Varmista, että maksimisyvyyden, leveyden, kellonajan, tokenien ja rahallisten kustannusten rajoitukset kunkin agentin suoritukselle ovat keskitetysti määritelty ja versiohallinnassa.                    |  1   |  D/V  |
| 9.1.2 | Varmista, että etuoikeutetut tai peruuttamattomat toimet (esim. koodin tallennukset, rahansiirrot) vaativat eksplisiittisen ihmisen hyväksynnän tarkastettavan kanavan kautta ennen niiden suorittamista. |  1   |  D/V  |
| 9.1.3 | Varmista, että reaaliaikaiset resurssien valvontatyökalut laukaisevat katkaisupiirin keskeytyksen, kun jokin budjettikynnys ylittyy, estäen tehtävän laajentamisen jatkumisen.                            |  2   |   D   |
| 9.1.4 | Varmista, että katkaisijatapahtumat kirjataan agentin tunnuksella, laukaisevalla ehdolla ja tallennetulla suunnitelmatilalla oikeudellista tarkastelua varten.                                            |  2   |  D/V  |
| 9.1.5 | Varmista, että tietoturvatestit kattavat budjetin loppumisen ja hallitsemattoman suunnitelman tilanteet, varmistaen turvallisen pysäytyksen ilman tiedonmenetystä.                                        |  3   |   V   |
| 9.1.6 | Varmista, että budjettipolitiikat on ilmaistu politiikkana-koodina ja ne pannaan täytäntöön CI/CD:ssä konfiguraation poikkeamien estämiseksi.                                                             |  3   |   D   |

---

## 9.2 Työkalulaajennusten hiekkalaatikkotila

Eristä työkalujen vuorovaikutukset estääksesi luvattoman järjestelmän käytön tai koodin suorittamisen.

|   #   | Kuvaus                                                                                                                                                                                                             | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 9.2.1 | Varmista, että jokainen työkalu/laajennus suoritetaan käyttöjärjestelmän, kontin tai WASM-tason hiekkalaatikon sisällä, jossa on vähimmän etuoikeuden tiedostojärjestelmä-, verkko- ja järjestelmäkutsupolitiikat. |  1   |  D/V  |
| 9.2.2 | Varmista, että hiekkalaatikkoresurssien kiintiöt (CPU, muisti, levytila, verkon ulossuuntaus) ja suoritusaikarajat toteutetaan ja kirjataan.                                                                       |  1   |  D/V  |
| 9.2.3 | Varmista, että työkalujen binaaritiedostot tai kuvaukset on digitaalisesti allekirjoitettu; allekirjoitukset tarkistetaan ennen lataamista.                                                                        |  2   |  D/V  |
| 9.2.4 | Varmista, että hiekkalaatikon telemetriatiedot virtaavat SIEM-järjestelmään; poikkeamat (esim. yritykset muodostaa ulospäin suuntautuvia yhteyksiä) laukaisevat hälytykset.                                        |  2   |   V   |
| 9.2.5 | Varmista, että korkean riskin liitännäiset käyvät läpi turvallisuustarkastuksen ja tunkeutumistestauksen ennen tuotantoon käyttöönottoa.                                                                           |  3   |   V   |
| 9.2.6 | Varmista, että hiekkalaatikkopaon yritykset estetään automaattisesti ja kyseinen lisäosa eristetään karanteeniin tutkinnan ajaksi.                                                                                 |  3   |  D/V  |

---

## 9.3 Autonominen silmukka ja kustannusten rajoittaminen

Havaitse ja pysäytä hallitsematon agenttien välinen rekursio ja kustannusten räjähdys.

|   #   | Kuvaus                                                                                                                            | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.3.1 | Varmista, että agenttien välisissä viesteissä on hyppyrajoitin tai TTL, jonka suoritusympäristö vähentää ja valvoo.               |  1   |  D/V  |
| 9.3.2 | Varmista, että agentit ylläpitävät ainutlaatuista kutsukartta-ID:tä havaitakseen itse-kutsun tai sykliset kuviot.                 |  2   |   D   |
| 9.3.3 | Varmista, että kertyvät laskenta-yksikkö- ja kulutuskertymät seurataan jokaiselle pyyntöketjulle; rajan ylitys keskeyttää ketjun. |  2   |  D/V  |
| 9.3.4 | Varmista, että formaali analyysi tai mallintarkastus osoittaa agenttiprotokollissa rajoittamattoman rekursion poissaolon.         |  3   |   V   |
| 9.3.5 | Varmista, että silmukan keskeytystapahtumat tuottavat hälytyksiä ja syöttävät jatkuvan parantamisen mittareita.                   |  3   |   D   |

---

## 9.4 Protokollatason väärinkäytön suojaus

Varmista suojatut viestintäkanavat agenttien ja ulkoisten järjestelmien välillä sieppauksen tai manipuloinnin estämiseksi.

|   #   | Kuvaus                                                                                                                                                      | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.4.1 | Varmista, että kaikki agentin ja työkalun sekä agenttien väliset viestit ovat todennettuja (esim. molemminpuolinen TLS tai JWT) ja päästä päähän salattuja. |  1   |  D/V  |
| 9.4.2 | Varmista, että skeemat validoidaan tiukasti; tuntemattomat kentät tai väärin muotoillut viestit hylätään.                                                   |  1   |   D   |
| 9.4.3 | Varmista, että eheystarkastukset (MAC:t tai digitaaliset allekirjoitukset) kattavat koko viestin hyötykuorman, mukaan lukien työkalun parametrit.           |  2   |  D/V  |
| 9.4.4 | Varmista, että uudelleenlähetyssuojaus (nonce-arvot tai aikaleimaikkunat) on toteutettu protokollakerroksella.                                              |  2   |   D   |
| 9.4.5 | Varmista, että protokollan toteutukset käyvät läpi fuzzauksen ja staattisen analyysin injektio- tai deserialisointivikojen varalta.                         |  3   |   V   |

---

## 9.5 Agentin identiteetti ja muokkaussuoja

Varmista, että toimet voidaan kohdistaa ja muutokset havaita.

|   #   | Kuvaus                                                                                                                                          | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.5.1 | Varmista, että jokaisella agentti-instanssilla on ainutlaatuinen kryptografinen identiteetti (avainpari tai laitteistoon perustuva tunniste).   |  1   |  D/V  |
| 9.5.2 | Varmista, että kaikki agenttien toimet on allekirjoitettu ja aikaleimattu; lokit sisältävät allekirjoituksen kiistämättömyyden varmistamiseksi. |  2   |  D/V  |
| 9.5.3 | Varmista, että manipulointia havaitsevat lokit tallennetaan vain lisäämistä tai kirjoittamista kerran sallivaan välineeseen.                    |  2   |   V   |
| 9.5.4 | Varmista, että identiteettiavaimet kiertävät määritellyn aikataulun mukaisesti ja kompromissin indikaattoreiden yhteydessä.                     |  3   |   D   |
| 9.5.5 | Varmista, että väärentäminen tai avainkonfliktin yritykset laukaisevat välittömän karanteenin vaikuttuneelle agentille.                         |  3   |  D/V  |

---

## 9.6 Moniagenttisen ryömintäjoukon riskien vähentäminen

Vähennä kollektiivisen käyttäytymisen riskejä eristämisen ja muodollisen turvallisuusmallinnuksen avulla.

|   #   | Kuvaus                                                                                                                                                    | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.6.1 | Varmista, että eri turvallisuusalueilla toimivat agentit suoritetaan eristetyissä suoritusaikojen hiekkalaatikoissa tai verkkosegmenteissä.               |  1   |  D/V  |
| 9.6.2 | Varmista, että parviekäytymät on mallinnettu ja muodollisesti varmennettu elinvoimaisuuden ja turvallisuuden osalta ennen käyttöönottoa.                  |  3   |   V   |
| 9.6.3 | Varmista, että suoritusajan valvontatyökalut havaitsevat nousevat vaaralliset mallit (esim. sykliilmiöt, umpikujat) ja aloittavat korjaavat toimenpiteet. |  3   |   D   |

---

## 9.7 Käyttäjän ja työkalun todennus / valtuutus

Toteuta vahvat käyttöoikeusvalvonnat jokaiseen agentin käynnistämään toimintaan.

|   #   | Kuvaus                                                                                                                                          | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.7.1 | Varmista, että agentit todennetaan ensiluokkaisina päämiehinä alajärjestelmissä eivätkä koskaan käytä loppukäyttäjän tunnistetietoja uudelleen. |  1   |  D/V  |
| 9.7.2 | Varmista, että hienojakoiset valtuutuspolitiikat rajoittavat, mitä työkaluja agentti saa käyttää ja mitä parametreja se saa syöttää.            |  2   |   D   |
| 9.7.3 | Varmista, että oikeustarkistukset arvioidaan uudelleen jokaisella kutsulla (jatkuva valtuutus), ei vain istunnon alussa.                        |  2   |   V   |
| 9.7.4 | Varmista, että valtuutetut oikeudet vanhenevat automaattisesti ja vaativat uudelleen hyväksynnän aikakatkaisun tai laajuuden muutoksen jälkeen. |  3   |   D   |

---

## 9.8 Agenttien välinen viestintäturvallisuus

Salaa ja suojaa kaikkien agenttien väliset viestit eavesdroppauksen ja väärentämisen estämiseksi.

|   #   | Kuvaus                                                                                                                                   | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.8.1 | Varmista, että keskinäinen todennus ja täydellinen eteenpäin suuntautuva salaus (esim. TLS 1.3) ovat pakollisia agenttikanaville.        |  1   |  D/V  |
| 9.8.2 | Varmista, että viestin eheys ja alkuperä on varmennettu ennen käsittelyä; epäonnistumiset aiheuttavat hälytyksiä ja viestin hylkäämisen. |  1   |   D   |
| 9.8.3 | Varmista, että viestinnän metatiedot (aikaleimat, sekvenssinumerot) kirjataan tukemaan oikeuslääketieteellistä rekonstruointia.          |  2   |  D/V  |
| 9.8.4 | Varmista, että formaali tarkastus tai mallintarkastus vahvistaa, ettei protokollan tilakoneita voida ohjata vaarallisiin tiloihin.       |  3   |   V   |

---

## 9.9 Aikomuksen varmistus ja rajoitusten noudattaminen

Varmista, että agentin toimet vastaavat käyttäjän ilmaisemaa tarkoitusta ja järjestelmän rajoituksia.

|   #   | Kuvaus                                                                                                                                                                                               | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.9.1 | Varmista, että esisuorituksen rajoitusten ratkaisutarkastimet tarkistavat ehdotetut toimet kovakoodattuja turvallisuus- ja politiikkasääntöjä vastaan.                                               |  1   |   D   |
| 9.9.2 | Varmista, että suurivaikutteiset toimet (taloudelliset, tuhoisat, yksityisyyteen liittyvät) edellyttävät aloittavan käyttäjän nimenomaista aikomuksen vahvistamista.                                 |  2   |  D/V  |
| 9.9.3 | Varmista, että jälkiehdon tarkistukset varmistavat, että suoritetut toimenpiteet saavuttivat tarkoitetut vaikutukset ilman sivuvaikutuksia; poikkeamat laukaisevat palautuksen.                      |  2   |   V   |
| 9.9.4 | Varmista, että formaalit menetelmät (esim. mallintarkastus, teoreemojen todistus) tai ominaisuuksiin perustuvat testit osoittavat, että agentin suunnitelmat täyttävät kaikki ilmoitetut rajoitteet. |  3   |   V   |
| 9.9.5 | Varmista, että tarkoituksenmukaisuuden poikkeamat tai rajoitteiden rikkomiset ohjaavat jatkuvan parantamisen jaksoja ja uhkatiedon jakamista.                                                        |  3   |   D   |

---

## 9.10 Agenttien päättelystrategian turvallisuus

Turvallinen eri päättelystrategioiden valinta ja suorittaminen, mukaan lukien ReAct-, Chain-of-Thought- ja Tree-of-Thoughts-lähestymistavat.

|   #    | Kuvaus                                                                                                                                                                                                                                                        | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.10.1 | Varmista, että päättelystrategian valinta käyttää deterministisiä kriteereitä (syötetyn monimutkaisuus, tehtävätyyppi, turvallisuuskonteksti) ja että identtiset syötteet tuottavat identtiset strategian valinnat samassa turvallisuuskontekstissa.          |  1   |  D/V  |
| 9.10.2 | Varmista, että jokaisella päättelystrategialla (ReAct, Chain-of-Thought, Tree-of-Thoughts) on omistettu syötteen validointi, tulosteen puhdistus ja suoritusajan rajoitukset, jotka ovat spesifisiä sen kognitiiviselle lähestymistavalle.                    |  1   |  D/V  |
| 9.10.3 | Varmista, että päättelystrategian siirtymät kirjataan täydellisellä kontekstilla, mukaan lukien syötteen ominaisuudet, valintakriteerien arvot ja suoritusmetatiedot, jotta auditointijäljen rekonstruointi on mahdollista.                                   |  2   |  D/V  |
| 9.10.4 | Varmista, että Tree-of-Thoughts-päätöksentekoprosessi sisältää oksan karsintamekanismit, jotka lopettavat tutkimisen, kun havaitaan politiikan rikkomuksia, resurssirajoja tai turvallisuusrajoja.                                                            |  2   |  D/V  |
| 9.10.5 | Varmista, että ReAct (Reason-Act-Observe) -syklit sisältävät validointipisteet jokaisessa vaiheessa: päättelyvaiheen tarkastus, toiminnon vahvistus ja havainnon puhdistus ennen etenemistä.                                                                  |  2   |  D/V  |
| 9.10.6 | Varmista, että päättelystrategian suorituskykymittareita (suoritusaika, resurssien käyttö, tuloksen laatu) seurataan automaattisten hälytysten avulla, kun mittarit poikkeavat määritettyjen kynnysten ulkopuolelle.                                          |  3   |  D/V  |
| 9.10.7 | Varmista, että hybridi-päättelymenetelmät, jotka yhdistävät useita strategioita, säilyttävät kaikkien osastrategioiden syötteen validoinnin ja tulosten rajoitukset ilman, että ohitetaan mitään turvallisuusvalvontoja.                                      |  3   |  D/V  |
| 9.10.8 | Varmista, että päättelystrategian turvallisuustestaus sisältää väärinmuotoisten syötteiden fuzzauksen, vihamieliset kehotteet, jotka on suunniteltu pakottamaan strategian vaihtaminen, sekä rajatapaustestauksen kullekin kognitiiviselle lähestymistavalle. |  3   |  D/V  |

---

## 9.11 Agentin elinkaaren tilanhallinta ja tietoturva

Turvallinen agentin alustaminen, tilasiirtymät ja päättäminen kryptografisten tarkastuslokkien sekä määriteltyjen palautusmenettelyjen avulla.

|   #    | Kuvaus                                                                                                                                                                                                                                                                              | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.11.1 | Varmista, että agentin alustukseen sisältyy kryptografisen identiteetin muodostaminen laitteistotukea hyödyntävillä todennustiedoilla sekä muuttumattomat käynnistyslokiot, jotka sisältävät agentin tunnuksen, aikaleiman, kokoonpanon hajautusarvon ja alustuksen parametrit.     |  1   |  D/V  |
| 9.11.2 | Varmista, että agentin tilasiirtymät on kryptografisesti allekirjoitettu, aikaleimattu ja kirjattu täydellisen kontekstin kanssa, mukaan lukien laukaisevat tapahtumat, edellisen tilan tiiviste, uuden tilan tiiviste ja suoritetut turvallisuustarkastukset.                      |  2   |  D/V  |
| 9.11.3 | Varmista, että agentin sammutusmenettelyt sisältävät turvallisen muistin pyyhinnän kryptografisella tuhoamisella tai monivaiheisella ylikirjoituksella, tunnistetietojen mitätöinnin sertifikaattiviranomaiselle ilmoittamalla, sekä väärentämättömien lopetustodistusten luomisen. |  2   |  D/V  |
| 9.11.4 | Varmista, että agentin toipumismekanismit validoivat tilan eheyttä käyttämällä kryptografisia tarkistussummia (vähintään SHA-256) ja palautuvat tunnetusti ehjiin tiloihin havaittaessa korruptiota, sisältäen automaattiset hälytykset ja manuaaliset hyväksyntävaatimukset.       |  3   |  D/V  |
| 9.11.5 | Varmista, että agenttien pysyvyysmekanismit salakirjoittavat arkaluontoiset tilatiedot kullekin agentille erikseen määritellyillä AES-256-avaimilla ja toteuttavat turvallisen avaintenvaihdon asetettavissa aikatauluissa (enintään 90 päivän välein) ilman käyttökatkoa.          |  3   |  D/V  |

---

## 9.12 Työkalujen integroinnin turvallisuuskehys

Turvallisuusohjaimet dynaamiselle työkalujen lataukselle, suorittamiselle ja tulosten validoinnille määriteltyjen riskinarviointi- ja hyväksymisprosessien mukaisesti.

|   #    | Kuvaus                                                                                                                                                                                                                                                                                           | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 9.12.1 | Varmista, että työkalukuvaajat sisältävät turvallisuusmetatiedot, joissa määritellään vaaditut oikeudet (luku/kirjoitus/suoritus), riskitasot (matala/keski/korkea), resurssirajat (CPU, muisti, verkko) sekä validointivaatimukset, jotka on dokumentoitu työkalun manifestissa.                |  1   |  D/V  |
| 9.12.2 | Varmista, että työkalun suoritus tulokset validoidaan odotettuja skeemoja (JSON-skeema, XML-skeema) ja turvallisuuspolitiikkoja (tulosteen puhdistus, tietoluokitus) vastaan ennen integrointia aikakatkaisu- ja virheenkäsittelymenettelyjen kanssa.                                            |  1   |  D/V  |
| 9.12.3 | Varmista, että työkalun vuorovaikutuslokeissa on yksityiskohtainen suojauskonteksti, mukaan lukien käyttöoikeuksien käyttö, datan käyttökuviot, suoritusajan, resurssien kulutus ja paluuarvokoodit, rakenteellisen lokituksen avulla SIEM-integraatiota varten.                                 |  2   |  D/V  |
| 9.12.4 | Varmista, että dynaamiset työkalujen latausmekanismit validoivat digitaaliset allekirjoitukset PKI-infrastruktuurin avulla ja toteuttavat turvalliset latausprotokollat hiekkalaatikkoympäristön eristämisellä sekä käyttöoikeuksien tarkistuksella ennen suorittamista.                         |  2   |  D/V  |
| 9.12.5 | Varmista, että työkalujen turvallisuusarvioinnit käynnistyvät automaattisesti uusille versioille pakollisilla hyväksyntäporteilla, jotka kattavat staattisen analyysin, dynaamisen testauksen ja turvallisuustiimin tarkastelun, joissa on dokumentoidut hyväksymiskriteerit ja SLA-vaatimukset. |  3   |  D/V  |

---

### Viitteet

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

