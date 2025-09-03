# 10 Hyökkäyskestävyys ja yksityisyyden suojaus

## Kontrollitavoite

Varmista, että tekoälymallit ovat luotettavia, yksityisyyttä suojaavia ja väärinkäytöksiä vastaan kestäviä, kun niihin kohdistuu välttely-, inferenssi-, poiminta- tai myrkytyshyökkäyksiä.

---

## 10.1 Mallin kohdistus ja turvallisuus

Estä haitallisia tai sääntöjä rikkovia tuloksia.

|   #    | Kuvaus                                                                                                                                                                                          | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.1.1 | Varmista, että kohdistamisen testisarja (punaisen tiimin kehotteet, jailbreak-etsinnät, kielletty sisältö) on versionhallinnassa ja että sitä suoritetaan jokaisen mallin julkaisun yhteydessä. |  1   |  D/V  |
| 10.1.2 | Varmista, että kieltäytyminen ja turvallisen täydennyksen turvakaiteet ovat käytössä.                                                                                                           |  1   |   D   |
| 10.1.3 | Varmista, että automatisoitu arvioija mittaa haitallisen sisällön osuuden ja merkitsee regressiot, jotka ylittävät asetetun kynnystason.                                                        |  2   |  D/V  |
| 10.1.4 | Varmista, että vastajailbreak-koulutus on dokumentoitu ja toistettavissa.                                                                                                                       |  2   |   D   |
| 10.1.5 | Varmista, että muodolliset politiikan noudattamisen todisteet tai sertifioitu monitorointi kattavat kriittiset alueet.                                                                          |  3   |   V   |

---

## 10.2 Hyökkäysesimerkki-koventaminen

Lisää vastustuskykyä manipuloiduille syötteille. Robustin adversaarisen koulutuksen ja benchmark-pisteytyksen katsotaan olevan nykyisin paras käytäntö.

|   #    | Kuvaus                                                                                                                                | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.2.1 | Varmista, että projektivarastoissa on vihamieliseen koulutukseen liittyvät konfiguraatiot, joilla on toistettavat siemenet.           |  1   |   D   |
| 10.2.2 | Varmista, että vihamielisten esimerkkien havaitseminen laukaisee estohälytyksiä tuotantoputkistoissa.                                 |  2   |  D/V  |
| 10.2.4 | Varmista, että sertifioidun robustisuuden todistukset tai interval-rajojen todistukset kattavat ainakin tärkeimmät kriittiset luokat. |  3   |   V   |
| 10.2.5 | Varmista, että regressiotestit käyttävät adaptiivisia hyökkäyksiä todentamaan, ettei mitattavaa robustisuuden heikkenemistä ole.      |  3   |   V   |

---

## 10.3 Jäsenyyden inferenssin torjunta

Rajoita kykyä päättää, oliko tietue koulutusdatassa. Differentiaalinen yksityisyys ja luottamusarvojen peittäminen ovat edelleen tunnetuimpia tehokkaita puolustuskeinoja.

|   #    | Kuvaus                                                                                                                       | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.3.1 | Varmista, että kyselykohtainen entropian regularisointi tai lämpötilasäätö vähentää liiallista varmuutta ennusteissa.        |  1   |   D   |
| 10.3.2 | Tarkista, että koulutus käyttää ε-sidottua differentiaalisen yksityisyyden suojaa optimointia herkille tietoaineistoille.    |  2   |   D   |
| 10.3.3 | Tarkista, että hyökkäyssimulaatiot (shadow-model tai black-box) osoittavat hyökkäyksen AUC-arvon enintään 0.60 testidatalla. |  2   |   V   |

---

## 10.4 Mallin inversio-hyökkäysten vastustuskyky

Estä yksityisten ominaisuuksien rekonstruointi. Äskettäiset katsaukset korostavat tulostuksen rajaamista ja DP-takuita käytännön puolustuskeinoin.

|   #    | Kuvaus                                                                                                                                | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.4.1 | Varmista, että arkaluonteiset attribuutit eivät koskaan tulostu suoraan; tarvittaessa käytä bucketteja tai yksisuuntaisia muunnoksia. |  1   |   D   |
| 10.4.2 | Varmista, että kyselynopeusrajoitukset rajoittavat samalta käyttäjältä toistuvia adaptiivisia kyselyitä.                              |  1   |  D/V  |
| 10.4.3 | Varmista, että malli on koulutettu yksityisyyttä suojaavalla melulla.                                                                 |  2   |   D   |

---

## 10.5 Mallinpoiminnan puolustus

Tunnista ja torju luvattoman kloonauksen. Vesileimaus ja kyselykuvioanalyysi ovat suositeltuja.

|   #    | Kuvaus                                                                                                                                                                          | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.5.1 | Varmista, että inferenssiväylät noudattavat sekä globaaleja että jokaiselle API-avaimelle asetettuja nopeusrajoituksia, jotka on viritetty mallin muistamisen kynnyksen mukaan. |  1   |   D   |
| 10.5.2 | Varmista, että kyselyentropia ja syötteen moninaisuustilastot syöttävät automaattisen poiminnan detektoriin.                                                                    |  2   |  D/V  |
| 10.5.3 | Varmista, että hauraat tai todennäköisyyspohjaiset vesileimat voidaan todistaa p < 0.01:n avulla ≤ 1 000 kyselyllä epäiltyä kloonia vastaan.                                    |  2   |   V   |
| 10.5.4 | Varmista, että vesileima-avaimet ja laukaisusarjat tallennetaan laitteistopohjaiseen turvallisuusmoduuliin ja vaihdetaan vuosittain.                                            |  3   |   D   |
| 10.5.5 | Varmista, että extraction-alert-tapahtumat sisältävät haitalliset kyselyt ja että ne ovat integroidut incident-response-playbookien kanssa.                                     |  3   |   V   |

---

## 10.6 Inferenssiaikana myrkytetyn datan havaitseminen

Tunnista ja neutraloi takaportilla varustetut tai myrkytetyt syötteet.

|   #    | Kuvaus                                                                                                                                                    | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.6.1 | Varmista, että syötteet kulkeutuvat poikkeavuustunnistimen läpi (esim. STRIP, yhtenäisyys-pisteytys) ennen mallin inferenssiä.                            |  1   |   D   |
| 10.6.2 | Varmista, että detektorin kynnystasot on viritetty puhtaiden ja myrkytettyjen validointijoukkojen perusteella, jotta valepositiivisten osuus on alle 5 %. |  1   |   V   |
| 10.6.3 | Varmista, että syötteet, jotka on merkitty myrkytetyiksi, laukaisevat soft-blocking ja ihmisen tarkistus työnkulut.                                       |  2   |   D   |
| 10.6.4 | Varmista, että detektorit rasitustestataan sopeutuvilla, laukaisimetömillä takaporttihyökkäyksillä.                                                       |  2   |   V   |
| 10.6.5 | Varmista, että havaitsemisen tehokkuusmittarit kirjataan lokiin ja niitä arvioidaan säännöllisesti tuoreiden uhkatiedustelujen avulla.                    |  3   |   D   |

---

## 10.7 Dynaaminen turvallisuuspolitiikan sopeutuminen

Reaaliaikaiset turvallisuuspolitiikan päivitykset uhkatiedustelun ja käyttäytymisanalyysin perusteella.

|   #    | Kuvaus                                                                                                                                                                   | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 10.7.1 | Varmista, että turvallisuuspolitiikat voidaan päivittää dynaamisesti ilman agentin uudelleenkäynnistystä, samalla säilyttäen politiikkaversioiden eheys.                 |  1   |  D/V  |
| 10.7.2 | Varmista, että politiikan päivitykset ovat kryptografisesti allekirjoitettuja valtuutettujen turvallisuusammattilaisten toimesta ja ne vahvistetaan ennen käyttöönottoa. |  2   |  D/V  |
| 10.7.3 | Varmista, että dynaamiset politiikan muutokset kirjataan täydellisillä auditointijäljillä, mukaan lukien perustelut, hyväksyntäketjut ja palautusmenettelyt.             |  2   |  D/V  |
| 10.7.4 | Varmista, että adaptiiviset turvallisuusmekanismit säätävät uhkien havaitsemisen herkkyyttä riskikontekstin ja käyttäytymismallien perusteella.                          |  3   |  D/V  |
| 10.7.5 | Varmista, että politiikan mukautuspäätökset ovat selitettävissä ja että niihin sisältyvät todistejäljet turvallisuustiimin tarkastelua varten.                           |  3   |  D/V  |

---

## 10.8 Reflektiopohjainen turvallisuusanalyysi

Turvallisuuden validointi agentin itse-reflektoinnin ja meta-cognitiivisen analyysin kautta.

|   #    | Kuvaus                                                                                                                                                        | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.8.1 | Varmista, että agentin reflektointimekanismit sisältävät turvallisuuteen keskittyvän omanarvioinnin päätöksistä ja toimista.                                  |  1   |  D/V  |
| 10.8.2 | Varmista, että reflektiotulokset validoidaan, jotta itsearviointimekanismien manipulointi estetään vihamielisillä syötteillä.                                 |  2   |  D/V  |
| 10.8.3 | Varmista, että metakognitiivinen turvallisuusanalyysi tunnistaa agentin päättelyprosesseihin liittyvän mahdollisen vinouden, manipuloinnin tai kompromission. |  2   |  D/V  |
| 10.8.4 | Varmista, että reflektointiin perustuvat turvallisuusvaroitukset laukaisevat parannetun valvonnan ja mahdolliset ihmisen väliintuloa koskevat työnkulut.      |  3   |  D/V  |
| 10.8.5 | Varmista, että jatkuva oppiminen turvallisuusreflektoinneista parantaa uhkien havaitsemista ilman, että laillinen toiminnallisuus heikkenee.                  |  3   |  D/V  |

---

## 10.9 Evoluutio ja itsekehityksen turvallisuus

Agenttijärjestelmien turvallisuusvalvontatoimet, jotka pystyvät itsemodifioitumaan ja kehittymään.

|   #    | Kuvaus                                                                                                                                                        | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.9.1 | Varmista, että itsemuokkauskyvyt rajoittuvat määrättyihin turvallisiin alueisiin muodollisten varmistusten rajoissa.                                          |  1   |  D/V  |
| 10.9.2 | Varmista, että kehitysehdotukset käyvät läpi turvallisuusvaikutusten arvioinnin ennen toteutusta.                                                             |  2   |  D/V  |
| 10.9.3 | Varmista, että itseparannusmekanismit sisältävät palautusominaisuudet eheydenvarmistuksella.                                                                  |  2   |  D/V  |
| 10.9.4 | Varmista, että meta-oppimisen turvallisuus estää parannusalgoritmeihin kohdistuvan hyökkäysperusteisen manipuloinnin.                                         |  3   |  D/V  |
| 10.9.5 | Varmista, että rekursiivinen itseparantuminen on rajattu muodollisten turvallisuusrajoitteiden puitteissa ja että konvergenssi on todistettu matemaattisesti. |  3   |  D/V  |

---

### Lähteet

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

