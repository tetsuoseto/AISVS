# C7-mallin käyttäytyminen, tuoton hallinta ja turvallisuuden varmistaminen

## Ohjaustavoite

Mallin tuotosten on oltava jäsenneltyjä, luotettavia, turvallisia, selitettäviä ja jatkuvasti valvottuja tuotantoympäristössä. Näin vähennetään harhoja, yksityisyyden vuotoja, haitallista sisältöä ja hallitsemattomia toimintoja sekä lisätään käyttäjien luottamusta ja sääntelyvaatimusten noudattamista.

---

## C7.1 Tulostemuodon noudattamisen varmistaminen

Tiukat skeemat, rajoitettu dekoodaus ja jälkikäteinen validointi estävät virheellisen tai haitallisen sisällön leviämisen.

|   #   | Kuvaus                                                                                                                                                                                                    | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.1.1 | Varmista, että vastauskaavat (esim. JSON Schema) on annettu järjestelmäkehotteessa ja että jokainen lähtö validoidaan automaattisesti; muotoiltumattomat tulosteet aiheuttavat korjauksen tai hylkäyksen. |  1   |  D/V  |
| 7.1.2 | Varmista, että rajoitettu dekoodaus (stop-tokenit, regex, maksimimäärä tokeneita) on käytössä ylivuodon tai kehotteen manipuloinnin sivukanavien estämiseksi.                                             |  1   |  D/V  |
| 7.1.3 | Varmista, että jälkikomponentit käsittelevät tulosteita epäluotettavina ja validoivat ne skeemojen tai injektioilta suojattujen de-serialisoijien avulla.                                                 |  2   |  D/V  |
| 7.1.4 | Varmista, että virheelliset tulostustapahtumat kirjataan, rajoitetaan esiintymistiheydeltään ja tuodaan esiin valvonnassa.                                                                                |  3   |   V   |

---

## C7.2 Hallusinaation tunnistus ja lieventäminen

Epävarmuuden arviointi ja varasuunnitelmat hillitsevät keksittyjä vastauksia.

|   #   | Kuvaus                                                                                                                                                                                                            | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.2.1 | Varmista, että token-tason log-todennäköisyydet, ensemble-itsejohdonmukaisuus tai hienosäädetyt harhanilmaisimet antavat luottamuspisteen jokaiselle vastaukselle.                                                |  1   |  D/V  |
| 7.2.2 | Varmista, että vastaukset, joiden luottamustaso on alle määritettävissä olevan kynnyksen, käynnistävät varajärjestelyjen työnkulut (esim. hakua täydentävä generointi, toissijainen malli tai ihmisen tarkistus). |  1   |  D/V  |
| 7.2.3 | Varmista, että harhakuvitustapaukset on merkitty perussyyn metatiedoilla ja syötetty jälkipuheen ja hienosäätöputkien käsittelyyn.                                                                                |  2   |  D/V  |
| 7.2.4 | Varmista, että kynnysarvot ja tunnistimet kalibroidaan uudelleen merkittävien mallin tai tietopohjan päivitysten jälkeen.                                                                                         |  3   |  D/V  |
| 7.2.5 | Varmista, että kojelaudan visualisoinnit seuraavat harhaluulojen esiintymisprosentteja.                                                                                                                           |  3   |   V   |

---

## C7.3 Tulosteen turvallisuus- ja yksityisyydensuodatus

Politiikkasuodattimet ja punatiimin kattavuus suojaavat käyttäjiä ja luottamuksellisia tietoja.

|   #   | Kuvaus                                                                                                                                                                                              | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.3.1 | Varmista, että esigenerointi- ja jälkigenerointiluokittelijat estävät vihapuheen, häirinnän, itsetuhoisuuden, ääriliikkeet ja seksuaalisesti eksplisiittisen sisällön, joka on politiikan mukaista. |  1   |  D/V  |
| 7.3.2 | Varmista, että PII/PCI-tunnistus ja automaattinen sensurointi suoritetaan jokaisessa vastauksessa; rikkomukset aiheuttavat tietosuojaongelman.                                                      |  1   |  D/V  |
| 7.3.3 | Varmista, että luottamuksellisuusmerkinnät (esim. liikesalaisuudet) leviävät eri formaattien välillä estäen vuotoja tekstissä, kuvissa tai koodissa.                                                |  2   |   D   |
| 7.3.4 | Varmista, että suodattimen ohitusyritykset tai korkean riskin luokitukset vaativat toissijaisen hyväksynnän tai käyttäjän uudelleentunnistautumisen.                                                |  3   |  D/V  |
| 7.3.5 | Varmista, että suodatuskynnykset vastaavat lakisääteisiä toimivalta-alueita sekä käyttäjän ikä- ja roolikontekstia.                                                                                 |  3   |  D/V  |

---

## C7.4 Tulosteen ja toiminnon rajoittaminen

Nopeusrajoitukset ja hyväksyntäportit estävät hyväksikäytön ja liiallisen autonomian.

|   #   | Kuvaus                                                                                                                                                                                      | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.4.1 | Varmista, että käyttäjäkohtaiset ja API-avaimenkohtaiset käyttökiintiöt rajoittavat pyyntöjä, tokeneita ja kustannuksia eksponentiaalisella takaisinkytkennällä 429-virheiden yhteydessä.   |  1   |   D   |
| 7.4.2 | Varmista, että etuoikeutetut toimet (tiedostojen kirjoitus, koodin suoritus, verkkokutsut) vaativat politiikkapohjaisen hyväksynnän tai ihmisen ohjauksen.                                  |  1   |  D/V  |
| 7.4.3 | Varmista, että ristiinmodaliteettien yhdenmukaisuustarkistukset takaavat, etteivät kuvat, koodi ja teksti, jotka on luotu samalle pyynnölle, voi sisältää piilotettua haitallista sisältöä. |  2   |  D/V  |
| 7.4.4 | Varmista, että agentin valtuutuksen syvyys, rekursion rajat ja sallitut työkaluluettelot on nimenomaisesti määritetty.                                                                      |  2   |   D   |
| 7.4.5 | Varmista, että rajojen rikkominen tuottaa jäsenneltyjä tietoturvatapahtumia SIEM:n keräämistä varten.                                                                                       |  3   |   V   |

---

## C7.5 Tulosteen selitettävyys

Läpinäkyvät signaalit parantavat käyttäjän luottamusta ja sisäistä virheenkorjausta.

|   #   | Kuvaus                                                                                                                                  | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.5.1 | Varmista, että käyttäjälle näkyvät luottamuspisteet tai lyhyet perusteluyhteenvedot esitetään, kun riskinarviointi katsoo ne sopiviksi. |  2   |  D/V  |
| 7.5.2 | Varmista, että luodut selitykset eivät paljasta arkaluonteisia järjestelmäkehotteita tai omistusoikeudellisia tietoja.                  |  2   |  D/V  |
| 7.5.3 | Varmista, että järjestelmä tallentaa token-tason lok todennäköisyydet tai huomiokartat valtuutettua tarkastusta varten.                 |  3   |   D   |
| 7.5.4 | Varmista, että selitettävyyteen liittyvät artefaktit ovat versiohallinnassa mallijulkaisujen yhteydessä auditoitavuutta varten.         |  3   |   V   |

---

## C7.6 Valvonnan integrointi

Reaaliaikainen havaittavuus sulkee kehityksen ja tuotannon välisen silmukan.

|   #   | Kuvaus                                                                                                                                                 | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 7.6.1 | Varmista, että mittarit (skeemarikkomukset, harhaluulot, toksisuus, henkilötietovuodot, viive, kustannukset) siirtyvät keskitettyyn valvonta-alustaan. |  1   |   D   |
| 7.6.2 | Varmista, että hälytysrajat on määritelty jokaiselle turvallisuusmittarille, ja että on valmiit reitit hälytyksen eskalointiin päivystäville.          |  1   |   V   |
| 7.6.3 | Varmista, että kojelaudat yhdistävät poikkeamatulokset malliin/versioon, ominaisuuslippuun ja ylösvetoisiin tietomuutoksiin.                           |  2   |   V   |
| 7.6.4 | Varmista, että valvontadata palautuu uudelleenkoulutukseen, hienosäätöön tai sääntöpäivityksiin dokumentoidun MLOps-työnkulun puitteissa.              |  2   |  D/V  |
| 7.6.5 | Varmista, että valvontaputket on suojattu tunkeutumistestein ja käyttöoikeuksin estämään arkaluonteisten lokitietojen vuotaminen.                      |  3   |   V   |

---

## 7.7 Generatiivisen median suojatoimet

Varmista, että tekoälyjärjestelmät eivät tuota laittomia, vahingollisia tai luvattomia mediasisältöjä toteuttamalla käytännesääntöjen rajoituksia, tulosten vahvistamista ja jäljitettävyyttä.

|   #   | Kuvaus                                                                                                                                                                                                           | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 7.7.1 | Varmista, että järjestelmäkehotteet ja käyttäjän ohjeet nimenomaisesti kieltävät laittoman, vahingollisen tai ei-suostumuksellisen deepfake-sisällön (esim. kuvat, videot, äänet) luomisen.                      |  1   |  D/V  |
| 7.7.2 | Varmista, että kehotteet suodatetaan yrittäessään luoda jäljitelmiä, seksuaalisesti eksplisiittisiä deepfake-videoita tai mediaa, joka kuvaa todellisia henkilöitä ilman suostumusta.                            |  2   |  D/V  |
| 7.7.3 | Varmista, että järjestelmä käyttää havaintotiivistämistä, vesileiman tunnistusta tai sormenjälkitunnistusta estääkseen luvattoman kopioinnin tekijänoikeudella suojatusta sisällöstä.                            |  2   |   V   |
| 7.7.4 | Varmista, että kaikki luotu media on kryptografisesti allekirjoitettu, vesileimattu tai varustettu muokkausta kestävällä alkuperätietojen metadatalla jäljitettävyyden varmistamiseksi jatkokäsittelyssä.        |  3   |  D/V  |
| 7.7.5 | Varmista, että ohitusyritykset (esim. kehotteen naamiointi, slangin käyttö, vihamielinen muotoilu) havaitaan, kirjataan ja niiden käyttöä rajoitetaan; toistuva väärinkäyttö raportoidaan valvontajärjestelmiin. |  3   |   V   |

## Viitteet

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

