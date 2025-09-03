# 9 Autonominen Orkestrointi & Agenttinen Toiminta Turvallisuus

## Kontrollitavoite

Varmista, että autonomiset tai moniagenttiset tekoälyjärjestelmät voivat ainoastaan suorittaa toimenpiteitä, jotka ovat erikseen tarkoitettuja, autentikoituja, auditoitavia ja rajoitettujen kustannus- ja riskirajojen puitteissa. Tämä suojaa uhkia vastaan, kuten autonomisen järjestelmän kompromissi, työkalun väärinkäyttö, agentin silmukan havaitseminen, viestinnän kaappaus, identiteetin väärentäminen, parven manipulointi ja tarkoituksen manipulointi.

---

## 9.1 Agentin tehtäväsuunnittelu ja rekursion budjetit

Rajoita rekursiivisia suunnitelmia ja aseta ihmisen tarkastuspisteet pakollisiksi etuoikeutettujen toimintojen suorittamisen yhteydessä.

|   #   | Kuvaus                                                                                                                                                                                | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.1.1 | Varmista, että maksimirekursion syvyys, haun leveys, reaaliaikainen aika, tokenit ja agentin suorituksen rahallinen kustannus ovat keskitetysti määritetyt ja versiohallinnassa.      |  1   |  D/V  |
| 9.1.2 | Varmista, että etuoikeutetut tai peruuttamattomat toiminnot (esim. koodimuutokset, rahansiirrot) vaativat ilmeisen ihmisen hyväksynnän auditointikanavan kautta ennen toteutusta.     |  1   |  D/V  |
| 9.1.3 | Varmista, että reaaliaikaiset resurssiseurantajärjestelmät laukaisevat piirikytkimen katkaisun, kun mikään budjetin kynnysarvo ylitetään, ja pysäyttävät lisätehtävien laajentamisen. |  2   |   D   |
| 9.1.4 | Varmista, että katkaisijan tapahtumat kirjataan agentin tunnuksella, laukaisutilanteella ja tallennetulla suunnitelman tilalla forensiikkatarkastelua varten.                         |  2   |  D/V  |
| 9.1.5 | Varmista, että turvallisuustestit kattavat budjetin loppumisen ja hallitsemattoman suunnitelman skenaariot, ja varmistavat turvallisen pysäytyksen ilman tietojen menetystä.          |  3   |   V   |
| 9.1.6 | Varmista, että budjettipolitiikat on esitetty politiikka-koodina ja ne pannaan täytäntöön CI/CD:ssä estämään konfiguraation poikkeamat.                                               |  3   |   D   |

---

## 9.2 Työkalun lisäosan hiekkalaatikkotestaus

Eristä työkalujen vuorovaikutukset, jotta estetään luvattoman järjestelmän pääsy tai koodin suoritus.

|   #   | Kuvaus                                                                                                                                                                                                                         | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 9.2.1 | Varmista, että jokainen työkalu tai lisäosa suorittaa toimintansa OS-tason, kontti- tai WASM-tason hiekkalaatikkoympäristössä, jossa noudatetaan minimioikeuksien tiedostojärjestelmä-, verkko- ja järjestelmäkutsupolitiikat. |  1   |  D/V  |
| 9.2.2 | Varmista, että hiekkalaatikon resurssikiintiöt (CPU, muisti, levy, verkkoliikenteen ulosmeno) sekä suoritusaikakatkaisut ovat voimassa ja kirjataan.                                                                           |  1   |  D/V  |
| 9.2.3 | Varmista, että työkalujen binäärit tai kuvaustiedostot ovat digitaalisesti allekirjoitetut; allekirjoitukset vahvistetaan ennen lataamista.                                                                                    |  2   |  D/V  |
| 9.2.4 | Varmista, että sandbox-telemetria virtaa SIEMiin; poikkeavuudet (esim. lähteviin yhteyksiin kohdistuneet yritykset) laukaisevat hälytykset.                                                                                    |  2   |   V   |
| 9.2.5 | Varmista, että korkean riskin lisäosat käyvät läpi turvallisuustarkastukset ja tunkeutumistestaukset ennen tuotantoon käyttöönottoa.                                                                                           |  3   |   V   |
| 9.2.6 | Varmista, että hiekkalaatikon pakoyritykset estetään automaattisesti ja haitallinen lisäosa on eristetty tutkimusta varten.                                                                                                    |  3   |  D/V  |

---

## 9.3 Omatoiminen silmukka ja kustannusten rajoitus

Havaitse ja pysäytä hallitsematon agenttien välinen rekursio sekä kustannusten räjähtävä kasvu.

|   #   | Kuvaus                                                                                                                                        | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.3.1 | Varmista, että agenttien välisissä kutsuissa on hop-limit tai TTL, jonka ajonaikainen ympäristö pienentää ja valvoo.                          |  1   |  D/V  |
| 9.3.2 | Varmista, että agentit säilyttävät ainutlaatuisen kutsujen graafin tunnisteen, jotta voidaan havaita itsensä kutsumista tai syklisiä malleja. |  2   |   D   |
| 9.3.3 | Varmista, että kumulatiiviset laskentayksikkö- ja kululaskurit seurataan jokaisessa pyyntöketjussa; rajan ylitys keskeyttää ketjun.           |  2   |  D/V  |
| 9.3.4 | Varmista, että formaali analyysi tai mallintarkastus osoittaa, ettei agenttien protokollissa ole rajatonta rekursiota.                        |  3   |   V   |
| 9.3.5 | Varmista, että silmukan keskeytys-tapahtumat tuottavat hälytyksiä ja syöttävät jatkuvan parantamisen mittareita.                              |  3   |   D   |

---

## 9.4 Protokollatasoinen väärinkäytön esto

Varmista agenttien ja ulkoisten järjestelmien välisten turvallisten viestintäkanavien käyttö estääkseen kaappaamisen tai manipuloinnin.

|   #   | Kuvaus                                                                                                                                                   | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.4.1 | Varmista, että kaikki agentin ja työkalun välinen viestintä sekä agentin ja agentin välinen viestintä on todentettu ja end-to-end-salaus on käytössä.    |  1   |  D/V  |
| 9.4.2 | Varmista, että skeemat validoidaan tiukasti; tuntemattomat kentät tai virheelliset viestit hylätään.                                                     |  1   |   D   |
| 9.4.3 | Varmista, että eheystarkistukset (MAC-tarkistukset tai digitaaliset allekirjoitukset) kattavat koko viestin payloadin mukaan lukien työkalun parametrit. |  2   |  D/V  |
| 9.4.4 | Varmista, että uudelleenkäytön esto (nonce-arvot tai aikaleimaikkunat) on toteutettu protokollakerroksessa.                                              |  2   |   D   |
| 9.4.5 | Varmista, että protokollien toteutukset altistuvat fuzzingille ja staattiselle analyysille injektointi- tai deserialisointivirheiden varalta.            |  3   |   V   |

---

## Agentin identiteetti ja manipulointitodiste

Varmista, että toimet ovat jäljitettävissä ja muutokset havaittavissa.

|   #   | Kuvaus                                                                                                                                        | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.5.1 | Varmista, että jokaisella agentin instanssilla on ainutlaatuinen kryptografinen identiteetti (avainpari tai laitteistopohjainen tunniste).    |  1   |  D/V  |
| 9.5.2 | Varmista, että kaikki agentin toimet on allekirjoitettu ja aikaleimattu; lokit sisältävät allekirjoituksen kiistämättömyyden varmistamiseksi. |  2   |  D/V  |
| 9.5.3 | Varmista, että manipuloinnin todentavat lokit tallennetaan append-only- tai write-once-mediassa.                                              |  2   |   V   |
| 9.5.4 | Varmista, että identiteettisavaimet kierrätetään määritellyn aikataulun mukaan ja kompromissin indikaattoreiden perusteella.                  |  3   |   D   |
| 9.5.5 | Tarkista, että spoofing- tai avaimen-konfliktiyritykset laukaisevat välittömän karanteenin kyseiselle agentille.                              |  3   |  D/V  |

---

## 9.6 Moni-Agenttinen parven riskin vähentäminen

Vähennä kollektiivisen-käyttäytymisen vaaroja eristyksen ja formaalin turvallisuusmallinnuksen avulla.

|   #   | Kuvaus                                                                                                                                                                         | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 9.6.1 | Varmista, että eri turvallisuusalueilla toimivat agentit suorittavat toimintansa erillisissä ajonaikaisissa sandbox-ympäristöissä tai verkkosegmentteissä.                     |  1   |  D/V  |
| 9.6.2 | Varmista, että parven käyttäytymistä on mallinnettu ja formalisesti todistettu elävyyden ja turvallisuuden varmistamiseksi ennen käyttöönottoa.                                |  3   |   V   |
| 9.6.3 | Varmista, että ajonaikaiset valvontajärjestelmät havaitsevat ilmaantuvat vaaralliset käytösmallit (esim. oscilointi, kuolleet lukitukset) ja käynnistä korjaavat toimenpiteet. |  3   |   D   |

---

## 9.7 Käyttäjän ja työkalun todennus / valtuutus

Ota käyttöön vahvat pääsynhallintamenettelyt jokaiselle agentin käynnistämälle toiminnolle.

|   #   | Kuvaus                                                                                                                                                        | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.7.1 | Varmista, että agentit todentavat itsensä ensiluokkaisina identiteetteina alijärjestelmiin, eikä koskaan käytä loppukäyttäjän tunnuksia.                      |  1   |  D/V  |
| 9.7.2 | Varmista, että hienojakoiset valtuutuspolitiikat rajoittavat sekä sitä, mitkä työkalut agentti voi kutsua että mitkä parametrit sen on mahdollista toimittaa. |  2   |   D   |
| 9.7.3 | Varmista, että oikeuksien tarkistukset arvioidaan uudelleen jokaisella kutsulla (jatkuva valtuutus), ei ainoastaan istunnon alussa.                           |  2   |   V   |
| 9.7.4 | Varmista, että delegoidut oikeudet vanhentuvat automaattisesti ja vaativat uudelleen suostumuksen aikakatkaisun jälkeen tai laajuuden muutoksen jälkeen.      |  3   |   D   |

---

## 9.8 Agent-to-Agent Viestinnän turvallisuus

Salaa ja suojaa kaikkien agenttien välisten viestien eheyden estääkseen salakuuntelun ja manipuloinnin.

|   #   | Kuvaus                                                                                                                                      | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.8.1 | Varmista, että molemminpuolinen todentaminen ja perfect-forward-secret encryption (esim. TLS 1.3) ovat agenttikanavien kannalta pakollisia. |  1   |  D/V  |
| 9.8.2 | Varmista, että viestin eheys ja alkuperä varmistetaan ennen käsittelyä; epäonnistumiset laukaisevat hälytykset ja viesti hylätään.          |  1   |   D   |
| 9.8.3 | Varmista, että viestinnän metatiedot (aikaleimat, sekvenssinumerot) kirjataan talteen forensisen rekonstruoinnin tueksi.                    |  2   |  D/V  |
| 9.8.4 | Varmista, että muodollinen todentaminen tai mallintarkastus vahvistaa, ettei protokollan tilakoneita voida ajaa turvattomiin tiloihin.      |  3   |   V   |

---

## 9.9 Tarkoituksen varmistaminen ja rajoitteiden täytäntöönpano

Varmista, että agentin toimet ovat käyttäjän ilmoittaman aikomuksen ja järjestelmän rajoitteiden mukaisia.

|   #   | Kuvaus                                                                                                                                                                                                | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.9.1 | Varmista, että suoritusta edeltävät rajoitteiden ratkaisut tarkistavat ehdotetut toimet kovakoodattujen turvallisuus- ja ohjesääntöjen mukaisesti.                                                    |  1   |   D   |
| 9.9.2 | Varmista, että vaikutukseltaan suuria toimintoja (rahoitus-, tuho-, ja yksityisyyteen liittyviä) vaativat aloittaneen käyttäjän ilmeisen aikomuksen vahvistuksen.                                     |  2   |  D/V  |
| 9.9.3 | Varmista, että jälkivaiheen ehtotarkastukset varmistavat, että suoritetut toimet saavuttivat halutut vaikutukset ilman sivuvaikutuksia; poikkeamat laukaisevat palautuksen.                           |  2   |   V   |
| 9.9.4 | Varmista, että formaaliset menetelmät (esim. mallintarkastus, teoreemien todistaminen) tai ominaisuusperusteiset testit osoittavat, että agenttisuunnitelmat täyttävät kaikki määritellyt rajoitteet. |  3   |   V   |
| 9.9.5 | Varmista, että intent-mismatch tai constraint-violation-tapaukset ruokkivat jatkuvan parantamisen kiertokulkuja ja uhkatiedon jakamista.                                                              |  3   |   D   |

---

## 9.10 Agentin päättelystrategia turvallisuus

Erilaisten päättelystrategioiden turvallinen valinta ja toteutus, mukaan lukien ReAct, Chain-of-Thought ja Tree-of-Thoughts-lähestymistavat.

|   #    | Kuvaus                                                                                                                                                                                                                                                                                             | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.10.1 | Varmista, että päättelystrategian valinta noudattaa deterministisiä kriteerejä (syötteen monimutkaisuus, tehtävätyyppi, turvallisuuskonteksti) ja identtiset syötteet tuottavat samat strategian valinnat samassa turvallisuuskontekstissa.                                                        |  1   |  D/V  |
| 9.10.2 | Varmista, että jokaisella päättelystrategialla (ReAct, Chain-of-Thought, Tree-of-Thoughts) on omistetut syötteen validointi, tuloksen sanitointi ja suoritusaikarajat, jotka vastaavat sen kognitiivista lähestymistapaa.                                                                          |  1   |  D/V  |
| 9.10.3 | Varmista, että päättelystrategian siirtymät kirjataan täydellisellä kontekstilla, mukaan lukien syötteen ominaisuudet, valintakriteerien arvot ja suoritustiedot auditointipolun rekonstruointia varten.                                                                                           |  2   |  D/V  |
| 9.10.4 | Varmista, että Tree-of-Thoughts päättely sisältää haarojen karsimismekanismit, jotka lopettavat etsinnän, kun havaitaan sääntöjen rikkomuksia, resurssirajoituksia tai turvallisuusrajoja.                                                                                                         |  2   |  D/V  |
| 9.10.5 | Varmista, että ReAct (Reason-Act-Observe) syklit sisältävät jokaisessa vaiheessa validointipisteet: päättelyaskeleen tarkistus, toiminnan valtuutus ja havainnon puhdistus ennen etenemistä.                                                                                                       |  2   |  D/V  |
| 9.10.6 | Varmista, että päättelystrategian suorituskykymittarit (suoritusaika, resurssien käyttö, tulosteen laatu) seurataan automaattisilla hälytyksillä, kun mittarit poikkeavat määritellyistä kynnysarvoista.                                                                                           |  3   |  D/V  |
| 9.10.7 | Varmista, että useista strategioista koostuvat hybridi-päätöksentekomenetelmät säilyttävät kaikkien koostettujen strategioiden syötteen validoinnin ja tulosteiden rajoitteet ilman, että mikään turvallisuusvalvonta ohitetaan.                                                                   |  3   |  D/V  |
| 9.10.8 | Varmista, että päättelystrategian turvallisuustestaus sisältää virheellisesti muotoiltujen syötteiden fuzzingin, suunnitellut adversarial-kehotteet, joiden tarkoituksena on pakottaa strategian vaihtaminen, sekä jokaiselle kognitiiviselle lähestymistavalle tarkoitetun reunatilan testauksen. |  3   |  D/V  |

---

## 9.11 Agentin elinkaaren tilanhallinta ja turvallisuus

Turvallisen agentin alustus, tilansiirtymät ja lopetus kryptografisilla auditointijäljillä sekä määritellyillä palautusmenettelyillä.

|   #    | Kuvaus                                                                                                                                                                                                                                                                                          | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.11.1 | Varmista, että agentin käynnistys sisältää kryptografisen identiteetin muodostamisen laitteistopohjaisten tunnisteiden avulla ja muuttumattomat käynnistysauditointilokit, jotka sisältävät agentin tunnuksen (ID), aikaleiman, konfiguraatiohajautteen sekä käynnistysparametrit.              |  1   |  D/V  |
| 9.11.2 | Varmista, että agentin tilansiirtymät ovat kryptografisesti allekirjoitettuja, aikaleimattuja ja lokitettuja täydellisen kontekstin kanssa, mukaan lukien laukaisutapahtumat, aiemman tilan hash-arvo, uuden tilan hash-arvo sekä suoritetut turvallisuustarkastukset.                          |  2   |  D/V  |
| 9.11.3 | Varmista, että agentin sammuttamisproseduureihin sisältyy turvallinen muistin pyyhkiminen kryptografisen tyhjennyksen tai moninkertaisen ylikirjoitusmenetelmän avulla, tunnistetietojen mitätöinti varmenteen myöntäjän ilmoituksella sekä törmäyksen todentavien lopetustodistusten luominen. |  2   |  D/V  |
| 9.11.4 | Varmista, että agentin palautusmekanismit validoivat tilan eheyden kryptografisilla tarkistussummilla (SHA-256 vähintään) ja palauttavat tunnettuun hyvään tilaan, kun korruptio havaitaan, käyttäen automaattisia hälytyksiä ja manuaalisia hyväksyntävaatimuksia.                             |  3   |  D/V  |
| 9.11.5 | Varmista, että agentin pysyvyyteen liittyvät mekanismit salavat arkaluonteiset tilatiedot jokaiselle agentille omilla AES-256-avaimilla ja toteuttavat turvallisen avainten kierrätyksen määritettävissä aikatauluissa (enintään 90 päivää) katkottomalla käyttöönotolla.                       |  3   |  D/V  |

---

## 9.12 Työkalujen integraation turvallisuuskehys

Turvallisuustoimenpiteet dynaamisten työkalujen lataamiseen, suorittamiseen ja tulosten validointiin sekä määritellyt riskinarviointi- ja hyväksyntäprosessit.

|   #    | Kuvaus                                                                                                                                                                                                                                                                                       | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 9.12.1 | Varmista, että työkalukuvaukset sisältävät turvallisuustiedot, jotka määrittelevät vaaditut oikeudet (luku/kirjoitus/suoritus), riskitasot (matala/keskitaso/korkea), resurssirajoitteet (CPU, muist, verkko) sekä validointivaatimukset, jotka on dokumentoitu työkalujen manifeeteissä.    |  1   |  D/V  |
| 9.12.2 | Varmista, että työkalun suoritustulokset validoidaan odotettujen skeemojen (JSON Schema, XML Schema) ja turvallisuuspolitiikkojen (tuloksen puhdistus, datan luokittelu) mukaan ennen integraatiota, jossa sovelletaan aikakatkaisurajoja ja virheenkäsittelymenettelyjä.                    |  1   |  D/V  |
| 9.12.3 | Varmista, että työkalujen vuorovaikutuslokit sisältävät yksityiskohtaisen turvallisuuskontekstin, mukaan lukien oikeuksien käytön, tiedon käyttömallit, suoritusajan, resurssien kulutuksen ja palautuskoodit sekä SIEM-integraatiota varten strukturoitu lokitus.                           |  2   |  D/V  |
| 9.12.4 | Varmista, että dynaamiset työkalujen latausmekanismit vahvistavat digitaalisten allekirjoitusten oikeellisuuden PKI-infrastruktuurin avulla ja toteuttavat turvalliset latausprotokollat hiekkalaatikkoeristyksen ja käyttöoikeuksien varmistamisen ennen suoritusta.                        |  2   |  D/V  |
| 9.12.5 | Varmista, että työkalun turvallisuusarvioinnit käynnistetään automaattisesti uusille versioille, joissa on pakolliset hyväksyntäportit, mukaan lukien staattinen analyysi, dynaaminen testaus ja turvallisuustiimin tarkastus, dokumentoiduilla hyväksyntäkriteereillä ja SLA-vaatimuksilla. |  3   |  D/V  |

---

### Lähteet

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

