# C13 Ihmisen valvonta, vastuullisuus ja hallinto

## Ohjaustavoite

Tämä luku sisältää vaatimukset ihmisen valvonnan ylläpitämiselle ja selkeiden vastuuketjujen varmistamiselle tekoälyjärjestelmissä sekä selitettävyyden, läpinäkyvyyden ja eettisen hallinnoinnin turvaamiselle koko tekoälyelinkaaren ajan.

---

## C13.1 Hätäpysäytys- ja ohitusmekanismit

Tarjoa sammutus- tai palautusreitit, kun tekoälyjärjestelmän epävakasta käyttäytymistä havaitaan.

|   #    | Kuvaus                                                                                                             | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 13.1.1 | Varmista, että manuaalinen pysäytyskytkin on olemassa AI-mallin päättelyn ja tulosten välittömään keskeyttämiseen. |  1   |  D/V  |
| 13.1.2 | Varmista, että ylikirjoitusvalvonta on käytettävissä vain valtuutetuille henkilöille.                              |  1   |   D   |
| 13.1.3 | Varmista, että rollback-prosessit pystyvät palauttamaan aiempiin malliversioihin tai turvalliseen tilaan.          |  3   |  D/V  |
| 13.1.4 | Varmista, että ylikirjoitusmekanismit testataan säännöllisesti.                                                    |  3   |   V   |

---

## C13.2 Ihminen-silmukassa-päätösten-tarkistuspisteet

Vaatia ihmishyväksynnät, kun panokset ylittävät ennalta määritellyt riskikynnykset.

|   #    | Kuvaus                                                                                                                             | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.2.1 | Varmista, että korkean riskin tekoälypäätökset vaativat nimenomaisen ihmisen hyväksynnän ennen toteutusta.                         |  1   |  D/V  |
| 13.2.2 | Varmista, että riskikynnykset on selvästi määritelty ja ne käynnistävät automaattisesti ihmisen tarkastusprosessit.                |  1   |   D   |
| 13.2.3 | Varmista, että aikarajoihin sidotuissa päätöksissä on varajärjestelyt, jos ihmisen hyväksyntää ei saada vaaditussa ajassa.         |  2   |   D   |
| 13.2.4 | Varmista, että eskalointimenettelyt määrittelevät selkeät valtuustasot eri päätöstyypeille tai riskiluokille, jos sovellettavissa. |  3   |  D/V  |

---

## C13.3 Vastuun ketju & Tarkastettavuus

Loki operaattorin toimet ja mallin päätökset.

|   #    | Kuvaus                                                                                                                                                                      | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.3.1 | Varmista, että kaikkien tekoälyjärjestelmän päätösten ja ihmisen tekemien toimenpiteiden tiedot kirjataan aikaleimojen, käyttäjätunnusten ja päätösten perustelujen kanssa. |  1   |  D/V  |
| 13.3.2 | Varmista, etteivät tilintarkastuslokit ole muokattavissa ja että ne sisältävät eheysvarmennusmekanismeja.                                                                   |  2   |   D   |

---

## C13.4 Selitettävät tekoälymenetelmät

Pintojen ominaisuuksien tärkeys, vastakkaistapaukset ja paikalliset selitykset.

|   #    | Kuvaus                                                                                                                                                                        | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.4.1 | Varmista, että tekoälyjärjestelmät tarjoavat perustason selitykset päätöksistään ihmisen luettavassa muodossa.                                                                |  1   |  D/V  |
| 13.4.2 | Varmista, että selityksen laatu on validoitu ihmisen tekemien arviointitutkimusten ja mittareiden kautta.                                                                     |  2   |   V   |
| 13.4.3 | Varmista, että ominaisuuksien tärkeysarvot tai attribuutiomenetelmät (SHAP, LIME jne.) ovat saatavilla kriittisille päätöksille.                                              |  3   |  D/V  |
| 13.4.4 | Varmista, että kontrafaktuaaliset selitykset osoittavat, miten syötteitä voitaisiin muuttaa tulosten muuttamiseksi, jos se on sovellettavissa käyttötapaukseen ja toimialaan. |  3   |   V   |

---

## C13.5 Mallikortit ja käyttöilmoitukset

Pidä yllä mallikortteja tarkoitettuun käyttöön, suorituskykymittareihin ja eettisiin näkökohtiin liittyen.

|   #    | Kuvaus                                                                                                                                                                                                   | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.5.1 | Varmista, että mallikortit dokumentoivat suunnitellut käyttötapaukset, rajoitukset ja tunnetut virhetilanteet.                                                                                           |  1   |   D   |
| 13.5.2 | Varmista, että suorituskykymittarit eri soveltuvien käyttötapausten osalta on julkistettu.                                                                                                               |  1   |  D/V  |
| 13.5.3 | Varmista, että eettiset näkökohdat, vinoumien arvioinnit, oikeudenmukaisuuden arvioinnit, koulutusdatan ominaisuudet ja tunnetut koulutusdatan rajoitukset on dokumentoitu ja päivitetty säännöllisesti. |  2   |   D   |
| 13.5.4 | Varmista, että mallikortit ovat versionhallinnassa ja niitä ylläpidetään koko mallin elinkaaren ajan muutosten seurannan kera.                                                                           |  2   |  D/V  |

---

## C13.6 Epävarmuuden kvantifiointi

Levitä luottamusarvot tai entropiamittarit vastauksiin.

|   #    | Kuvaus                                                                                                                | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.6.1 | Varmista, että tekoälyjärjestelmät antavat tulostensa mukana luottamus- tai epävarmuusarviot.                         |  1   |   D   |
| 13.6.2 | Varmista, että epävarmuuskynnykset laukaisevat lisäarvioinnin ihmiseltä tai vaihtoehtoiset päätöspolut.               |  2   |  D/V  |
| 13.6.3 | Varmista, että epävarmuuden kvantifiointimenetelmät on kalibroitu ja validoitu todelliseen tosiasiatietoon perustuen. |  2   |   V   |
| 13.6.4 | Varmista, että epävarmuuden eteneminen säilyy monivaiheisissa tekoälytyönkuluissa.                                    |  3   |  D/V  |

---

## C13.7 Käyttäjälle suunnatut läpinäkyvyysraportit

Tarjoa säännöllisiä tietoja tapahtumista, poikkeamista ja datan käytöstä.

|   #    | Kuvaus                                                                                                                                             | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.7.1 | Varmista, että tietojen käyttökäytännöt ja käyttäjäluvan hallintakäytännöt on selkeästi viestitty sidosryhmille.                                   |  1   |  D/V  |
| 13.7.2 | Varmista, että tekoälyn vaikutusten arvioinnit tehdään ja tulokset sisällytetään raportointiin.                                                    |  2   |  D/V  |
| 13.7.3 | Varmista, että säännöllisesti julkaistavat avoimuusraportit paljastavat tekoälyonnettomuudet ja toimintamittarit kohtuullisen yksityiskohtaisesti. |  2   |  D/V  |

### Viitteet

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

