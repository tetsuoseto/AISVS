# C13 Ihmisen valvonta, vastuullisuus ja hallinto

## Kontrollitavoite

Tämä luku määrittelee vaatimukset ihmisen valvonnan ylläpitämiseksi sekä selkeiden vastuuketjujen varmistamiseksi tekoälyjärjestelmissä, ja se varmistaa selitettävyyden, läpinäkyvyyden sekä eettisen hallinnan koko tekoälyn elinkaaren ajan.

---

## C13.1 Sammutus-katkaisija ja ohitusmekanismit

Tarjoa sammuttamis- ja palautuspolut, kun tekoälyjärjestelmän turvallisuusriskiä aiheuttava käyttäytyminen havaitaan.

|   #    | Kuvaus                                                                                                                                          | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.1.1 | Varmista, että manuaalinen tappokytkinmekanismi on olemassa ja että se pysäyttää välittömästi AI-mallin inferenssin ja sen tuottamat tulosteet. |  1   |  D/V  |
| 13.1.2 | Varmista, että ohituskontrollit ovat ainoastaan valtuutettujen henkilöstön käytettävissä.                                                       |  1   |   D   |
| 13.1.3 | Varmista, että palautusmenettelyt voivat palauttaa aiemmat malliversiot tai toimia turvallisessa tilassa.                                       |  3   |  D/V  |
| 13.1.4 | Varmista, että ohitusmekanismit testataan säännöllisesti.                                                                                       |  3   |   V   |

---

## C13.2 Ihmisen mukana prosessissa päätösten tarkistuspaikat

Vaatikaa ihmisten hyväksyntöjä, kun panokset ylittävät ennalta määritellyt riskirajat.

|   #    | Kuvaus                                                                                                                                | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.2.1 | Tarkista, että korkean riskin tekoälypäätökset edellyttävät ihmisen nimenomaista hyväksyntää ennen toteutusta.                        |  1   |  D/V  |
| 13.2.2 | Varmista, että riskirajat on määritelty selkeästi ja että ne automaattisesti käynnistävät ihmisten tarkastusprosessit.                |  1   |   D   |
| 13.2.3 | Varmista, että aikakriittisissä päätöksissä on varajärjestelyjä, kun ihmisen hyväksyntää ei saada vaadituissa aikarajoissa.           |  2   |   D   |
| 13.2.4 | Varmista, että eskalointimenettelyt määrittelevät selkeät valtuudet eri päätöstyypeille tai riskiluokille, mikäli sovellettavissa on. |  3   |  D/V  |

---

## C13.3 Vastuun ketju ja auditointi

Kirjaa operaattorin toimet ja mallin päätökset.

|   #    | Kuvaus                                                                                                                                                  | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.3.1 | Varmista, että kaikki tekoälyjärjestelmien päätökset ja ihmisten väliintulot kirjataan aikaleimoilla, käyttäjäidentiteeteillä ja päätöksen perusteilla. |  1   |  D/V  |
| 13.3.2 | Varmista, että auditlokit eivät ole muokattavissa ja että niihin on sisällytetty eheysvarmennusmekanismit.                                              |  2   |   D   |

---

## C13.4 Selitettävä-AI Tekniikat

Pintaominaisuuksien tärkeys, counter-factuals, ja paikalliset selitykset.

|   #    | Kuvaus                                                                                                                                                                          | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.4.1 | Varmista, että tekoälyjärjestelmät antavat päätöksilleen perusselitykset ihmisluettavassa muodossa.                                                                             |  1   |  D/V  |
| 13.4.2 | Varmista, että selityksen laatu on validoitu inhimillisten arviointitutkimusten ja mittareiden kautta.                                                                          |  2   |   V   |
| 13.4.3 | Varmista, että ominaisuuksien tärkeysarvot tai attribuutiomenetelmät (SHAP, LIME jne.) ovat saatavilla kriittisille päätöksille.                                                |  3   |  D/V  |
| 13.4.4 | Varmista, että counterfactual-selitykset osoittavat, miten syötteitä voitaisiin muuttaa, jotta lopputulokset muuttuisivat, jos se on sovellettavissa käyttötapaukseen ja alaan. |  3   |   V   |

---

## C13.5 Mallikortit ja käyttöilmoitukset

Pidä yllä mallikortteja aiotun käytön, suorituskykymittareiden ja eettisten näkökohtien varalta.

|   #    | Kuvaus                                                                                                                                                                                                   | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.5.1 | Varmista, että mallikortit dokumentoivat tarkoitetut käyttötapaukset, rajoitukset ja tunnetut vika- tai epäonnistumistavat.                                                                              |  1   |   D   |
| 13.5.2 | Varmista, että suorituskykymittarit on julkaistu eri soveltuvien käyttötapausten osalta.                                                                                                                 |  1   |  D/V  |
| 13.5.3 | Varmista, että eettiset näkökulmat, vinouman arvioinnit, oikeudenmukaisuuden arvioinnit, koulutusdatan ominaisuudet sekä tunnetut koulutusdatan rajoitteet dokumentoidaan ja päivitetään säännöllisesti. |  2   |   D   |
| 13.5.4 | Varmista, että mallikortit ovat versionhallinnassa ja niitä ylläpidetään koko mallin elinkaaren ajan muutosten seuraamisen avulla.                                                                       |  2   |  D/V  |

---

## C13.6 Epävarmuuden kvantifiointi

Välitä vastauksissa luottamusarvot tai entropiamittarit.

|   #    | Kuvaus                                                                                                     | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.6.1 | Varmista, että tekoälyjärjestelmät tarjoavat luottamusarviot tai epävarmuusmittarit tuloksilleen.          |  1   |   D   |
| 13.6.2 | Varmista, että epävarmuuskynnysarvot saavat aikaan lisäarvioinnin tai vaihtoehtoisia päätöksentekopolkuja. |  2   |  D/V  |
| 13.6.3 | Varmista, että epävarmuuden kvantifiointimenetelmät on kalibroitu ja validoitu ground truth dataa vastaan. |  2   |   V   |
| 13.6.4 | Tarkista, että epävarmuuden leviäminen säilyy monivaiheisten tekoälytyöprosessien aikana.                  |  3   |  D/V  |

---

## C13.7 Käyttäjille suunnatut läpinäkyvyysraportit

Tarjoa säännöllisiä paljastuksia tapahtumista, driftistä ja datan käytöstä.

|   #    | Kuvaus                                                                                                                                                                | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.7.1 | Varmista, että tietojen käytön politiikat ja käyttäjien suostumuksen hallintaan liittyvät käytännöt viestitään sidosryhmille selkeästi.                               |  1   |  D/V  |
| 13.7.2 | Varmista, että tekoälyn vaikutusarvioinnit ovat tehty ja tulokset sisällytetään raportointiin.                                                                        |  2   |  D/V  |
| 13.7.3 | Varmista, että säännöllisesti julkaistut läpinäkyvyysraportit paljastavat tekoälyyn liittyvät tapahtumat ja toiminnalliset mittarit kohtuullisen yksityiskohtaisesti. |  2   |  D/V  |

### Lähteet

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)](https://eur-lex.europa.eu/legal-content/EN/TXT/PDF/?uri=CELEX%3A32016R0679)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

