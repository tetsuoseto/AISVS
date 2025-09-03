# Liite D: AI-avusteinen turvallisen ohjelmoinnin hallinto ja verifiointi

## Tavoite

Tämä luku määrittelee perusorganisatoriset hallintatoimenpiteet tekoälyavusteisten koodausvälineiden turvalliseen ja tehokkaaseen käyttöön ohjelmistokehityksen aikana, varmistamalla turvallisuuden ja jäljitettävyyden koko SDLC:n ajan.

---

## AD.1 tekoäly-avusteinen turvallisen-koodauksen työnkulku

Integroi tekoälytyökalut organisaation turvallisen‑ohjelmistokehityksen elinkaareen (SSDLC) siten, ettei nykyisiä turvallisuusportteja heikennetä.

|   #    | Kuvaus                                                                                                                                                                                           | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AD.1.1 | Varmista, että dokumentoitu työnkulku kuvaa milloin ja miten tekoälytyökalut voivat luoda, refaktoroida tai tarkastella koodia.                                                                  |  1   |  D/V  |
| AD.1.2 | Varmista, että työnkulku vastaa kunkin SSDLC-vaiheen (suunnittelu, toteutus, koodikatselmointi, testaus, käyttöönotto).                                                                          |  2   |   D   |
| AD.1.3 | Varmista, että mittarit (esim. haavoittuvuuksien tiheys, keskimääräinen havaitsemisaika) kerätään tekoälyn‑tuottamalle koodille ja verrataan ainoastaan ihmisillä tuotettuihin vertailuarvoihin. |  3   |  D/V  |

---

## AD.2 AI-työkalun kelpuutus ja uhkamallinnus

Varmista, että tekoälykoodausvälineet arvioidaan turvallisuusominaisuuksien, riskin ja toimitusketjun vaikutuksen osalta ennen käyttöönottoa.

|   #    | Kuvaus                                                                                                                                                                             | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.2.1 | Varmista, että jokaisen tekoälytyökalun uhkamalli tunnistaa väärinkäytön, mallin inversio, tietovuodon ja riippuvuuksien ketjun riskit.                                            |  1   |  D/V  |
| AD.2.2 | Varmista, että työkalujen arvioinnit sisältävät paikallisten komponenttien staattinen/dynaaminen analyysi ja SaaS-päätepisteiden arviointi (TLS, todentaminen/valtuutus, lokitus). |  2   |   D   |
| AD.2.3 | Varmista, että arvioinnit noudattavat tunnustettua viitekehystä ja ne suoritetaan uudelleen suurten pääversioiden jälkeen.                                                         |  3   |  D/V  |

---

## AD.3 Turvallinen kehotteen ja kontekstinhallinta

Estä salaisuuksien, yrityksen omistaman koodin ja henkilötietojen vuotuminen, kun laadit kehotteita tai konteksteja tekoälymalleja varten.

|   #    | Kuvaus                                                                                                                                            | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.3.1 | Varmista, että kirjallinen ohjeistus kieltää salaisuuksien, tunnusten tai luokiteltujen tietojen lähettämisen kehotteissa.                        |  1   |  D/V  |
| AD.3.2 | Varmista, että tekniset kontrollit (asiakaspuoleinen redaktointi, hyväksytyt kontekstisuodattimet) poistavat automaattisesti herkät artefaktit.   |  2   |   D   |
| AD.3.3 | Varmista, että syötteet ja vastaukset tokenisoidaan, siirron aikana ja levossa salataan, ja säilytysajat noudattavat tiedonluokittelupolitiikkaa. |  3   |  D/V  |

---

## AD.4 Tekoälyn generoiman koodin validointi

Havaitse ja korjaa tekoälyn tuottamien tulosten aiheuttamat haavoittuvuudet ennen koodin yhdistämistä tai käyttöönottoa.

|   #    | Kuvaus                                                                                                                                                                                | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.4.1 | Varmista, että tekoälyn‑tuottama koodi käy aina läpi ihmisen koodikatselmoinnin.                                                                                                      |  1   |  D/V  |
| AD.4.2 | Varmista, että automaattiset skannerit (SAST/IAST/DAST) suorittavat jokaisen vetopyynnön, joka sisältää AI‑generated koodia, ja estävät yhdistämisen kriittisten löydösten ilmetessä. |  2   |   D   |
| AD.4.3 | Varmista, että differentiaalinen fuzz-testaus tai ominaisuus-pohjaiset testit todistavat turvallisuuskriittisiä käyttäytymisiä (esim. syötteen validointi, valtuutuslogiikka).        |  3   |  D/V  |

---

## AD.5 Koodiehdotusten selittävyys ja jäljitettävyys

Tarjoa tilintarkastajille ja kehittäjille näkemys siitä, miksi ehdotus tehtiin ja miten se kehittyi.

|   #    | Kuvaus                                                                                                                                                                      | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.5.1 | Tarkista, että kehotus/vastausparit kirjataan commit-tunnisteilla.                                                                                                          |  1   |  D/V  |
| AD.5.2 | Varmista, että kehittäjät voivat tuoda esiin mallin viitteet (koulutusnäytteet, dokumentaatio), jotka tukevat ehdotusta.                                                    |  2   |   D   |
| AD.5.3 | Varmista, että selittävyysraportit tallennetaan design-artefaktien yhteydessä ja viitataan turvallisuuskatsauksissa, täyttäen ISO/IEC 42001:n jäljitettävyyden periaatteet. |  3   |  D/V  |

---

## AD.6 Jatkuva palaute & mallin hienosäätö

Paranna mallin turvallisuustasoa ajan mittaan samalla estäen negatiivisen harhaantumisen.

|   #    | Kuvaus                                                                                                                                                                                                     | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.6.1 | Varmista, että kehittäjät voivat merkitä turvattomia tai sääntöjen vastaisia ehdotuksia, ja että liput seurataan.                                                                                          |  1   |  D/V  |
| AD.6.2 | Varmista, että koottu palaute ohjaa säännöllistä fine‑tuningia tai retrieval‑augmented generationia hyväksyttyjen turvallisen koodauksen korpusten avulla (esim. OWASP Cheat Sheets).                      |  2   |   D   |
| AD.6.3 | Varmista, että suljetun silmukan arviointityökalu suorittaa regressiotestit jokaisen hienosäädön jälkeen; turvallisuusmittareiden on täytettävä tai ylitettävä aiemmat baseline-arvot ennen käyttöönottoa. |  3   |  D/V  |

---

### Lähteet

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

