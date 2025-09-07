# 10 Vihamielinen kestävyys ja yksityisyyden suojaaminen

## Ohjaustavoite

Varmista, että tekoälymallit pysyvät luotettavina, yksityisyyttä suojelevina ja väärinkäytöksiä kestävinä kohdatessaan kiertäviä, päättelyyn, tiedon poimintaan tai myrkytyshyökkäyksiin.

---

## 10.1 Mallin sovittaminen ja turvallisuus

Suojaa haitallisilta tai politiikkaa rikkovilta tuloksilta.

|   #    | Kuvaus                                                                                                                                                                | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.1.1 | Varmista, että yhdenmukaisuustestisarja (red-team-kehotteet, jailbreak-kyselyt, kielletty sisältö) on versiohallinnassa ja suoritetaan jokaisessa mallin julkaisussa. |  1   |  D/V  |
| 10.1.2 | Varmista, että kieltäytymisen ja turvallisen suorittamisen suojakaiteet ovat käytössä.                                                                                |  1   |   D   |
| 10.1.3 | Varmista, että automaattinen arvioija mittaa haitallisen sisällön määrää ja merkitsee takapakit, jotka ylittävät asetetun kynnyksen.                                  |  2   |  D/V  |
| 10.1.4 | Varmista, että vastaharjoittelumenetelmät on dokumentoitu ja toistettavissa.                                                                                          |  2   |   D   |
| 10.1.5 | Varmista, että viralliset politiikanmukaisuuden todistukset tai sertifioitu valvonta kattavat kriittiset alueet.                                                      |  3   |   V   |

---

## 10.2 Vihamielisten esimerkkien kovettaminen

Lisää vastustuskykyä manipuloiduille syötteille. Vahva vastustajakoulutus ja vertailuarviointi ovat nykyiset parhaat käytännöt.

|   #    | Kuvaus                                                                                                                                           | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 10.2.1 | Varmista, että projektivarastoissa on vastustajakoulutusasetukset toistettavilla siemenillä.                                                     |  1   |   D   |
| 10.2.2 | Varmista, että vastustajasimulaatioiden tunnistus aiheuttaa estäviä hälytyksiä tuotantoputkistoissa.                                             |  2   |  D/V  |
| 10.2.4 | Varmista, että sertifioidut-robustiustodistukset tai väliarvotodistukset kattavat vähintään tärkeimmät kriittiset luokat.                        |  3   |   V   |
| 10.2.5 | Varmista, että regressiotestit käyttävät adaptiivisia hyökkäyksiä vahvistaakseen, ettei havaittavissa ole mittaavaa suorituskyvyn heikkenemistä. |  3   |   V   |

---

## 10.3 Jäsenyystietoisuuden ehkäisy

Rajoita kykyä päätellä, oliko tietue harjoitusdatassa. Differentiaalinen yksityisyys ja luottamusarvopisteen peittäminen ovat edelleen tehokkaimmat tunnetut suojakeinot.

|   #    | Kuvaus                                                                                                                                         | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.3.1 | Varmista, että kyselykohtainen entropian regularisointi tai lämpötilan skaalaus vähentää yliitsevarmoja ennusteita.                            |  1   |   D   |
| 10.3.2 | Varmista, että koulutus käyttää ε-rajoitettua differentiaalisesti yksityistä optimointia arkaluontoisille tietoaineistoille.                   |  2   |   D   |
| 10.3.3 | Varmista, että hyökkäyssimulaatiot (varjomalli tai mustalaatikkomenetelmä) osoittavat hyökkäyksen AUC-arvon ≤ 0,60 pidetyllä testiaineistolla. |  2   |   V   |

---

## 10.4 Mallin käännöstä estävä vastustus

Estä yksityisten attribuuttien uudelleenrakentaminen. Viimeaikaiset tutkimukset korostavat tuloksen katkaisua ja differentiaalisen yksityisyyden (DP) takeita käytännöllisinä puolustuksina.

|   #    | Kuvaus                                                                                                                            | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.4.1 | Varmista, ettei arkaluonteisia attribuutteja koskaan tulosteta suoraan; tarvittaessa käytä luokkia tai yksisuuntaisia muunnoksia. |  1   |   D   |
| 10.4.2 | Varmista, että kyselynopeusrajoitukset rajoittavat saman päähenkilön toistuvia mukautuvia kyselyjä.                               |  1   |  D/V  |
| 10.4.3 | Varmista, että malli on koulutettu yksityisyyttä säilyttävällä melulla.                                                           |  2   |   D   |

---

## 10.5 Mallin poistonesto

Tunnista ja estä luvaton kloonaus. Vesileimauksen ja kyselykuviopohjaisen analyysin käyttöä suositellaan.

|   #    | Kuvaus                                                                                                                                                    | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.5.1 | Vahvista, että päättelyportit noudattavat globaaleja ja API-avaimittain määriteltyjä nopeusrajoja, jotka on säädetty mallin muistamisen kynnyksen mukaan. |  1   |   D   |
| 10.5.2 | Varmista, että kyselyentropia- ja syöttömoninaisuustilastot syöttävät automatisoidun poiminnan havaitsemaan.                                              |  2   |  D/V  |
| 10.5.3 | Varmista, että hauraat tai todennäköisyyttä käyttävät vesileimat voidaan todistaa p < 0,01 tasolla enintään 1 000 kyselyllä epäiltyä kloonia vastaan.     |  2   |   V   |
| 10.5.4 | Varmista, että vesileimauksen avaimet ja laukaisusarjat tallennetaan laitteistoturvamoduuliin ja vaihdetaan vuosittain.                                   |  3   |   D   |
| 10.5.5 | Varmista, että poisto-hälytys tapahtumat sisältävät rikkomuksia aiheuttavat kyselyt ja ne on integroitu tapausreaktio-ohjelmiin.                          |  3   |   V   |

---

## 10.6 Päättelyaikainen myrkyllisen datan havaitseminen

Tunnista ja neutralisoi takaportilla varustetut tai myrkylliset syötteet.

|   #    | Kuvaus                                                                                                                                                  | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.6.1 | Varmista, että syötteet käyvät läpi poikkeavuuksien havaitsemisen ennen mallin päätelmää (esim. STRIP, johdonmukaisuuspisteytys).                       |  1   |   D   |
| 10.6.2 | Varmista, että havaitin kynnysarvot on säädetty puhtaille/myrkyllisille validointiaineistoille niin, että virheellisten positiivisten osuus on alle 5%. |  1   |   V   |
| 10.6.3 | Varmista, että myrkytyksiksi merkatut syötteet laukaisevat pehmeän eston ja ihmisen tarkastusprosessit.                                                 |  2   |   D   |
| 10.6.4 | Varmista, että tunnistimet testataan rasituksella adaptiivisilla, laukaisimettomilla takaovihyökkäyksillä.                                              |  2   |   V   |
| 10.6.5 | Varmista, että havaitsemisen tehokkuusmittarit kirjataan ja arvioidaan säännöllisesti uudelleen uusien uhkatietojen perusteella.                        |  3   |   D   |

---

## 10.7 Dynaaminen turvallisuuspolitiikan mukauttaminen

Reaaliaikaiset tietoturvapolitiikan päivitykset uhkatiedon ja käyttäytymisanalyysin perusteella.

|   #    | Kuvaus                                                                                                                                                      | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.7.1 | Varmista, että turvallisuuspolitiikkoja voidaan päivittää dynaamisesti ilman agentin uudelleenkäynnistystä säilyttäen samalla politiikkaversion eheys.      |  1   |  D/V  |
| 10.7.2 | Varmista, että politiikan päivitykset on kryptografisesti allekirjoitettu valtuutetun turvallisuushenkilöstön toimesta ja vahvistettu ennen käyttöönottoa.  |  2   |  D/V  |
| 10.7.3 | Varmista, että dynaamiset politiikkamuutokset kirjataan täydellisesti tarkastelujäljillä, mukaan lukien perustelut, hyväksymisketjut ja palautusmenettelyt. |  2   |  D/V  |
| 10.7.4 | Varmista, että sopeutuvat tietoturvamekanismit säätävät uhkien tunnistuksen herkkyyttä riskikontekstin ja käyttäytymismallien perusteella.                  |  3   |  D/V  |
| 10.7.5 | Varmista, että politiikan sopeutuspäätökset ovat selitettäviä ja sisältävät todisteketjuja tietoturvatiimin tarkastelua varten.                             |  3   |  D/V  |

---

## 10.8 Heijastusperusteinen turvallisuusanalyysi

Turvallisuuden varmistaminen agentin itsearvioinnin ja metakognitiivisen analyysin avulla.

|   #    | Kuvaus                                                                                                                                                      | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.8.1 | Varmista, että agentin reflektiomekanismit sisältävät turvallisuuteen keskittyvän itsetarkastelun päätöksistä ja toimista.                                  |  1   |  D/V  |
| 10.8.2 | Varmista, että heijastusulostulot validoidaan estämään itsearviointimekanismien manipulointi vihamielisten syötteiden avulla.                               |  2   |  D/V  |
| 10.8.3 | Varmista, että metakognitiivinen turvallisuusanalyysi tunnistaa mahdollisen puolueellisuuden, manipuloinnin tai vaarantumisen agentin päättelyprosesseissa. |  2   |  D/V  |
| 10.8.4 | Varmista, että heijastukseen perustuvat turvallisuusvaroitukset laukaisevat tehostetun valvonnan ja mahdolliset ihmisen väliintulon työnkulut.              |  3   |  D/V  |
| 10.8.5 | Varmista, että jatkuva oppiminen turvallisuusheijastuksista parantaa uhkien havaitsemista ilman, että se heikentää laillista toimintaa.                     |  3   |  D/V  |

---

## 10.9 Kehittyminen ja itseparantumisen turvallisuus

Turvallisuusvalvontatoimet itsensä muokkaamiseen ja kehittymiseen kykeneville agenttijärjestelmille.

|   #    | Kuvaus                                                                                                                                      | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.9.1 | Varmista, että itse-muokkausominaisuudet on rajoitettu määritettyihin turvallisiin alueisiin muodollisen varmennuksen rajoissa.             |  1   |  D/V  |
| 10.9.2 | Varmista, että evolution ehdotukset käyvät läpi turvallisuusvaikutusten arvioinnin ennen käyttöönottoa.                                     |  2   |  D/V  |
| 10.9.3 | Varmista, että itseparannusmekanismit sisältävät palautusmahdollisuudet eheyden tarkistuksella.                                             |  2   |  D/V  |
| 10.9.4 | Varmista, että meta-oppimisen turvallisuus estää parannusalgoritmien vastustavan manipuloinnin.                                             |  3   |  D/V  |
| 10.9.5 | Varmista, että rekursiivinen itseparannus on rajoitettu muodollisilla turvallisuusrajoitteilla matemaattisilla todisteilla konvergenssista. |  3   |  D/V  |

---

### Viitteet

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

