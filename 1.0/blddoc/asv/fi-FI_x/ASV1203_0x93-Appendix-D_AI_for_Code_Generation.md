# Liite D: Tekoälyn avustama turvallisen koodauksen hallinta ja varmistus

## Tavoite

Tässä luvussa määritellään perustason organisatoriset valvontatoimet tekoälyavusteisten koodausvälineiden turvalliseen ja tehokkaaseen käyttöön ohjelmistokehityksen aikana, varmistaen turvallisuuden ja jäljitettävyyden SDLC:n kaikissa vaiheissa.

---

## AD.1 AI-avusteinen turvallinen koodaus työnkulku

Integroi tekoälytyökalut organisaation turvalliseen ohjelmistokehityksen elinkaareen (SSDLC) heikentämättä olemassa olevia turvallisuusportteja.

|   #    | Kuvaus                                                                                                                                                                                 | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.1.1 | Varmista, että dokumentoitu työnkulku kuvaa, milloin ja miten tekoälytyökaluja voidaan käyttää koodin generointiin, refaktorointiin tai tarkistamiseen.                                |  1   |  D/V  |
| AD.1.2 | Varmista, että työnkulku vastaa kutakin SSDLC-vaihetta (suunnittelu, toteutus, koodikatselmointi, testaus, käyttöönotto).                                                              |  2   |   D   |
| AD.1.3 | Varmista, että mittarit (esim. haavoittuvuustiheys, keskimääräinen havainta-aika) kerätään tekoälyn tuottamasta koodista ja verrataan ihmisten ainoastaan tuottamiin vertailuarvoihin. |  3   |  D/V  |

---

## AD.2 AI-työkalujen kelpoistaminen ja uhkamallinnus

Varmista, että tekoälykoodausvälineet arvioidaan turvallisuusominaisuuksien, riskien ja toimitusketjun vaikutusten osalta ennen käyttöönottoa.

|   #    | Kuvaus                                                                                                                                                                             | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.2.1 | Varmista, että kunkin tekoälytyökalun uhkamalli tunnistaa väärinkäytön, mallin käänteisen manipuloinnin, tietovuodon ja riippuvuusketjuriskit.                                     |  1   |  D/V  |
| AD.2.2 | Varmista, että työkalujen arvioinnit sisältävät paikallisten komponenttien staattisen/dynaamisen analyysin sekä SaaS-päätepisteiden (TLS, todennus/valtuutus, lokitus) arvioinnin. |  2   |   D   |
| AD.2.3 | Varmista, että arvioinnit noudattavat tunnustettua viitekehystä ja että ne suoritetaan uudelleen merkittävien versionmuutosten jälkeen.                                            |  3   |  D/V  |

---

## AD.3 Turvallinen kehotteiden ja kontekstinhallinta

Estä salaisuuksien, omistetun koodin ja henkilötietojen vuotaminen, kun rakennat kehyksiä tai konteksteja tekoälymalleille.

|   #    | Kuvaus                                                                                                                                              | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.3.1 | Varmista, että kirjallinen ohjeistus kieltää salaisuuksien, tunnistetietojen tai luokitellun tiedon lähettämisen kehotteissa.                       |  1   |  D/V  |
| AD.3.2 | Varmista, että tekniset kontrollit (asiakaspuolen sensurointi, hyväksytyt kontekstisuodattimet) poistavat automaattisesti arkaluonteiset aineistot. |  2   |   D   |
| AD.3.3 | Varmista, että kehotteet ja vastaukset tokenisoidaan, salataan siirron aikana ja levossa, ja että säilytysaika noudattaa tietoluokituspolitiikkaa.  |  3   |  D/V  |

---

## AD.4 Tekoälyn generoiman koodin validointi

Tunnista ja korjaa tekoälyn tuottamista tuloksista aiheutuneet haavoittuvuudet ennen kuin koodi yhdistetään tai otetaan käyttöön.

|   #    | Kuvaus                                                                                                                                                                                 | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.4.1 | Varmista, että tekoälyn luoma koodi käy aina ihmisen tekemän koodikatselmoinnin läpi.                                                                                                  |  1   |  D/V  |
| AD.4.2 | Varmista, että automaattiset tarkastimet (SAST/IAST/DAST) suoritetaan jokaisessa AI:n generoimaa koodia sisältävässä pull-pyynnössä ja estä yhdistämiset kriittisten löydösten osalta. |  2   |   D   |
| AD.4.3 | Varmista, että differentiaalinen fuzz-testaus tai ominaisuuksiin perustuvat testit todistavat turvallisuuskriittiset toiminnot (esim. syötteen validointi, valtuutuslogiikka).         |  3   |  D/V  |

---

## AD.5 Koodiehdotusten selitettävyys ja jäljitettävyys

Tarjoa tarkastajille ja kehittäjille näkemyksiä siitä, miksi ehdotus tehtiin ja kuinka se kehittyi.

|   #    | Kuvaus                                                                                                                                                                                 | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.5.1 | Varmista, että kehotteen/vastauksen parit tallennetaan commit-tunnuksilla.                                                                                                             |  1   |  D/V  |
| AD.5.2 | Varmista, että kehittäjät voivat näyttää mallin lainaukset (koulutuskatkelmat, dokumentaatio), jotka tukevat ehdotusta.                                                                |  2   |   D   |
| AD.5.3 | Varmista, että selitettävyysselosteet tallennetaan suunnittelukokonaisuuksien kanssa ja viitataan niihin turvallisuusarvioinneissa, täyttäen ISO/IEC 42001 -jäljitettävyysperiaatteet. |  3   |  D/V  |

---

## AD.6 Jatkuva palaute ja mallin hienosäätö

Paranna mallin turvallisuuskykyä ajan myötä samalla estäen negatiivinen liike.

|   #    | Kuvaus                                                                                                                                                                                                        | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.6.1 | Varmista, että kehittäjät voivat merkitä epävarmat tai vaatimusten vastaiset ehdotukset, ja että merkinnät seurataan.                                                                                         |  1   |  D/V  |
| AD.6.2 | Varmista, että koottu palaute ohjaa säännöllistä hienosäätöä tai hakua täydentävää generaatiota tarkastettujen turvallisen koodauksen korpusten avulla (esim. OWASP Cheat Sheets).                            |  2   |   D   |
| AD.6.3 | Varmista, että suljetun silmukan arviointijärjestelmä suorittaa regressiotestit jokaisen hienosäädön jälkeen; turvallisuusmittareiden on täytettävä tai ylityttävä aiemmat vertailuarvot ennen käyttöönottoa. |  3   |  D/V  |

---

### Viitteet

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

