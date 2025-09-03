# C7 Mallin käyttäytyminen, tulosten hallinta ja turvallisuusvarmistus

## Kontrollitavoite

Mallin tuotosten on oltava jäsenneltyjä, luotettavia, turvallisia, selitettävissä ja tuotannossa jatkuvasti valvottuja. Täten vähennetään hallusinaatioita, tietovuotoja, haitallista sisältöä ja hallitsemattomia toimintoja, samalla lisätään käyttäjien luottamusta sekä sääntelyvaatimusten noudattamista.

---

## C7.1 Tulostusmuodon noudattaminen

Tiukat skeemat, rajoitettu dekoodaus ja jälkikäsittelyn validointi estävät virheellisen tai haitallisen sisällön ennen kuin se leviää.

|   #   | Kuvaus                                                                                                                                                                                                          | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.1.1 | Varmista, että vastausten skeemat (esim. JSON-skeemat) sisältyvät järjestelmäkehotukseen ja että jokainen tulos validoidaan automaattisesti; epäyhteensopivat tulokset laukaisevat korjaamisen tai hylkäämisen. |  1   |  D/V  |
| 7.1.2 | Varmista, että rajoitettu dekoodaus (pysäytystunnisteet, säännölliset lausekkeet, maksimitokenit) on käytössä estämään ylivuotoa tai prompt-injection-sivukanavia.                                              |  1   |  D/V  |
| 7.1.3 | Varmista, että alasuuntautuneet komponentit käsittelevät tulokset luottamattomina ja validoivat ne skeemojen mukaan tai injektioturvallisten deserialisaattorien avulla.                                        |  2   |  D/V  |
| 7.1.4 | Varmista, että epäasianmukaiset output-tapahtumat kirjataan, niihin sovelletaan taajuusrajoitusta ja ne tuodaan esiin valvontaan.                                                                               |  3   |   V   |

---

## C7.2 Hallusinaatioiden havaitseminen ja lieventäminen

Epävarmuuden arviointi ja varautumisstrategiat rajoittavat keksittyjä vastauksia.

|   #   | Kuvaus                                                                                                                                                                                        | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.2.1 | Varmista, että token-tason logaritmiset todennäköisyydet, ensemblen itsejohdonmukaisuus tai hienosäädetyt hallusinaatiotunnistuslaitteet antavat jokaiselle vastaukselle luottamusarvon.      |  1   |  D/V  |
| 7.2.2 | Varmista, että konfiguroitavan luottamuskynnyn alapuolella olevat vastaukset laukaisevat fallback-työnkulut (esim. retrieval-augmented generation, toissijainen malli tai ihmisen arviointi). |  1   |  D/V  |
| 7.2.3 | Varmista, että hallusinaatiotapaukset ovat merkittyjä juurisyyn metatiedoilla ja ne syötetään post-mortem- ja finetuning-putkistoihin.                                                        |  2   |  D/V  |
| 7.2.4 | Varmista, että kynnysten ja tunnistimien kalibrointi suoritetaan uudelleen suurten mallien tai tietopohjan päivitysten jälkeen.                                                               |  3   |  D/V  |
| 7.2.5 | Varmista, että dashboardin visualisoinnit seuraavat hallusinaatioiden esiintymistiheyttä.                                                                                                     |  3   |   V   |

---

## C7.3 Tulostuksen turvallisuus ja yksityisyyden suodatus

Käytäntöön perustuvat suodattimet ja punaisen tiimin kattavuus suojaavat käyttäjiä ja luottamuksellisia tietoja.

|   #   | Kuvaus                                                                                                                                                                                                                                        | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.3.1 | Varmista, että ennen generointia ja generoinnin jälkeen käytettävät luokittelijat estävät politiikan mukaisen viha-, häirintä-, itsensä vahingoittamiseen liittyvän, äärijärjestöihin liittyvän sekä seksuaalisesti eksplisiittisen sisällön. |  1   |  D/V  |
| 7.3.2 | Varmista, että PII/PCI-tunnistus ja automaattinen punakointi suoritetaan jokaisessa vastauksessa; rikkomukset laukaisevat tietosuojatapauksen.                                                                                                |  1   |  D/V  |
| 7.3.3 | Varmista, että salassapitotunnisteet (esim. liikesalaisuudet) leviävät eri modaalisuuksien välillä vuodon estämiseksi tekstissä, kuvissa tai koodissa.                                                                                        |  2   |   D   |
| 7.3.4 | Varmista, että suodattimen ohitusyritykset tai korkean riskin luokitukset vaativat toissijaista hyväksyntää tai käyttäjän uudelleentodentamista.                                                                                              |  3   |  D/V  |
| 7.3.5 | Varmista, että suodatustasot heijastavat sovellettavaa lainsäädäntöä sekä käyttäjän ikää ja roolia koskevaa kontekstia.                                                                                                                       |  3   |  D/V  |

---

## C7.4 Ulostulon ja toimintojen rajoittaminen

Nopeusrajoitukset ja hyväksyntäportit estävät väärinkäytön ja liiallista autonomiaa.

|   #   | Kuvaus                                                                                                                                                                               | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 7.4.1 | Varmista, että käyttäjäkohtaiset ja API-avaimikohtaiset kiintiöt rajoittavat pyyntöjen, tokenien ja kustannusten määrää eksponentiaalisen takaisinvetäytymisen avulla 429-virheissä. |  1   |   D   |
| 7.4.2 | Varmista, että etuoikeutetut toiminnot (tiedostojen kirjoitukset, koodin suoritukset, verkkopyynnöt) vaativat politiikkapohjaista hyväksyntää tai ihmisen mukanaoloa prosessissa.    |  1   |  D/V  |
| 7.4.3 | Varmista, että modaalien välisten yhdenmukaisuustarkastusten avulla samalle pyynnölle liittyviä kuvia, koodia ja tekstiä ei voi käyttää haitallisen sisällön salakuljettamiseen.     |  2   |  D/V  |
| 7.4.4 | Varmista, että agentin delegoinnin syvyys, rekursion rajat ja sallittujen työkalujen luettelot on määritelty selvästi.                                                               |  2   |   D   |
| 7.4.5 | Varmista, että rajoitusten rikkominen tuottaa strukturoituja turvallisuustapahtumia SIEM-järjestelmään syötettäväksi.                                                                |  3   |   V   |

---

## C7.5 Tulosten selittävyys

Läpinäkyvät signaalit parantavat käyttäjien luottamusta ja sisäistä virheenkorjausta.

|   #   | Kuvaus                                                                                                                                             | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.5.1 | Varmista, että käyttäjälle näkyvät luottamusarvot tai lyhyet perustelujen yhteenvedot näytetään silloin, kun riskinarviointi katsoo sen sopivaksi. |  2   |  D/V  |
| 7.5.2 | Varmista, että generoituneet selitykset eivät paljasta arkaluonteisia järjestelmäkehotteita tai yrityksen omaa dataa.                              |  2   |  D/V  |
| 7.5.3 | Varmista, että järjestelmä tallentaa token-tason log-todennäköisyyksiä tai huomiokarttoja ja säilyttää ne valtuutetun tarkastusta varten.          |  3   |   D   |
| 7.5.4 | Varmista, että selitettävyyden artefaktit ovat versionhallinnassa yhdessä mallien julkaisujen kanssa auditointia varten.                           |  3   |   V   |

---

## C7.6 Monitoroinnin Integraatio

Reaaliaikainen havaittavuus sulkee kehityksen ja tuotannon välisen silmukan.

|   #   | Kuvaus                                                                                                                                                                           | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.6.1 | Varmista, että mittarit (skeeman rikkomukset, hallusinaatioiden osuus, myrkyllisyys, henkilötietojen vuotaminen, viive, kustannukset) virtaavat keskitetylle valvonta-alustalle. |  1   |   D   |
| 7.6.2 | Varmista, että jokaiselle turvallisuusmittarille on määritelty hälytysraja-arvot ja että on-call eskalointireitit ovat käytössä.                                                 |  1   |   V   |
| 7.6.3 | Varmista, että koontinäytöt korreloivat tulospoikkeamien kanssa mallin/version, ominaisuuslipun ja ylävirran datamuutosten kanssa.                                               |  2   |   V   |
| 7.6.4 | Varmista, että valvontatiedot palaavat takaisin uudelleenkoulutukseen, hienosäätöön tai sääntöpäivityksiin dokumentoidun MLOps-työnkulun puitteissa.                             |  2   |  D/V  |
| 7.6.5 | Varmista, että seurantaputket on penetraatiotestattu ja niihin on otettu käyttöön pääsynhallinta, jotta arkaluontoisten lokien vuotaminen estetään.                              |  3   |   V   |

---

## 7.7 Generatiivisen median turvatoimet

Varmista, että tekoälyjärjestelmät eivät tuota laittomia, haitallisia tai luvattomia mediasisältöjä noudattamalla politiikan rajoituksia, tulosten validointia ja jäljitettävyyttä.

|   #   | Kuvaus                                                                                                                                                                                                                | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.7.1 | Tarkista, että järjestelmän kehotteet ja käyttäjän ohjeet kieltävät nimenomaan laittoman, haitallisen tai suostumuksetta tuotetun deepfake-median tuottamisen (esim. kuva, video, ääni).                              |  1   |  D/V  |
| 7.7.2 | Varmista, että kehotteet suodatetaan, kun yritetään luoda henkilöllisyyden jäljittelyä, seksuaalisesti eksplisiittisiä deepfake-videoita tai materiaalia, joka esittää oikeita henkilöitä ilman heidän suostumustaan. |  2   |  D/V  |
| 7.7.3 | Varmista, että järjestelmä käyttää havaintoperusteista hajautusta, vesileiman havaitsemista tai sormenjälkitunnistusta estääkseen tekijänoikeudella suojatun median luvattoman kopioinnin.                            |  2   |   V   |
| 7.7.4 | Varmista, että kaikki tuotetut mediat on kryptografisesti allekirjoitettu, vesileimattu tai upotettu murtovarmennettuihin provenanssi-metatietoihin, jotta jäljitettävyys on taattu seuraavissa vaiheissa.            |  3   |  D/V  |
| 7.7.5 | Varmista, että kiertämisyritykset (esim. kehotteen hämärtäminen, slangi, vastustuksellinen sanamuoto) havaitaan, kirjataan ylös ja taajuusrajoitetaan; toistuva väärinkäyttö raportoidaan valvontajärjestelmiin.      |  3   |   V   |

## Lähteet

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [ISO/IEC 42001:2023 – AI Management System](https://www.iso.org/obp/ui/en/)
* [OWASP Top-10 for Large Language Model Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Improper Output Handling – OWASP LLM05:2025](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
* [Practical Techniques to Constrain LLM Output](https://mychen76.medium.com/practical-techniques-to-constraint-llm-output-in-json-format-e3e72396c670)
* [Dataiku – Structured Text Generation Guide](https://blog.dataiku.com/your-guide-to-structured-text-generation)
* [VL-Uncertainty: Detecting Hallucinations](https://arxiv.org/abs/2411.11919)
* [HaDeMiF: Hallucination Detection & Mitigation](https://openreview.net/forum?id=VwOYxPScxB)
* [Building Confidence in LLM Outputs](https://www.alkymi.io/data-science-room/building-confidence-in-llm-outputs)
* [Explainable AI & LLMs](https://duncsand.medium.com/explainable-ai-140912d31b3b)
* [LLM Red-Teaming Guide](https://www.confident-ai.com/blog/red-teaming-llms-a-step-by-step-guide)
* [Sensitive Information Disclosure in LLMs](https://virtualcyberlabs.com/llm-sensitive-information-disclosure/)
* [LangChain – Chat Model Rate Limiting](https://python.langchain.com/docs/how_to/chat_model_rate_limiting/)
* [OpenAI Rate-Limit & Exponential Back-off](https://hackernoon.com/openais-rate-limit-a-guide-to-exponential-backoff-for-llm-evaluation)
* [Arize AI – LLM Observability Platform](https://arize.com/)

