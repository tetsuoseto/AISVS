# 11 Tietosuojan suojaus ja henkilötietojen hallinta

## Ohjaustavoite

Säilytä tiukat yksityisyyden suojan takeet koko tekoälyn elinkaaren ajan—keräyksestä, koulutuksesta, päättelystä ja häiriötilanteisiin reagoinnista—niin että henkilötietoja käsitellään vain selkeällä suostumuksella, mahdollisimman suppeassa laajuudessa, todennettavissa olevalla poistamisella ja virallisilla yksityisyydensuojan takeilla.

---

## 11.1 Anonymisointi ja tietojen minimointi

|   #    | Kuvaus                                                                                                                                                | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.1.1 | Varmista, että suorat ja kvasi-tunnisteet on poistettu tai hajautettu.                                                                                |  1   |  D/V  |
| 11.1.2 | Varmista, että automatisoidut tarkastukset mittaavat k-anonymiteettia/l-monimuotoisuutta ja hälyttävät, kun kynnysarvot laskevat alle politiikan.     |  2   |  D/V  |
| 11.1.3 | Varmista, että mallin ominaisuuksien tärkeysraportit todistavat, ettei tunnistevuotoa esiinny yli ε = 0.01 yhteisen informaation.                     |  2   |   V   |
| 11.1.4 | Varmista, että muodolliset todistukset tai synteettisen datan sertifiointi osoittavat uudelleentunnistamisriskin olevan ≤ 0,05 jopa linkitysiskuissa. |  3   |   V   |

---

## 11.2 Oikeus tulla unohdetuksi ja poistamisen valvonta

|   #    | Kuvaus                                                                                                                                                                                                    | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.2.1 | Varmista, että data-subjectin poistopyynnöt leviävät raakadatakokoelmiin, tarkistuspisteisiin, upotuksiin, lokitietoihin ja varmuuskopioihin palvelutasosopimusten puitteissa, jotka ovat alle 30 päivää. |  1   |  D/V  |
| 11.2.2 | Varmista, että "machine-unlearning" -rutiinit fyysisesti uudelleenkouluttavat tai likimääräisesti poistavat tiedot käyttäen sertifioituja unlearning-algoritmeja.                                         |  2   |   D   |
| 11.2.3 | Varmista, että varjomallin arviointi todistaa unohdettujen tietueiden vaikuttavan alle 1 % tuloksista unlearningin jälkeen.                                                                               |  2   |   V   |
| 11.2.4 | Varmista, että poistotapahtumat kirjataan pysyvästi ja ne ovat tarkastettavissa sääntelyviranomaisille.                                                                                                   |  3   |   V   |

---

## 11.3 Differentiaalisen yksityisyyden suojatoimet

|   #    | Kuvaus                                                                                                                      | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.3.1 | Varmista, että tietosuojahäviön kirjaamista esittävät kojelaudat hälyttävät, kun kumulatiivinen ε ylittää politiikan rajat. |  2   |  D/V  |
| 11.3.2 | Varmista, että mustan laatikon yksityisyystarkastukset arvioivat ε̂:n 10 %:n tarkkuudella ilmoitetusta arvosta.             |  2   |   V   |
| 11.3.3 | Varmista, että muodolliset todistukset kattavat kaikki jälkikoulutuksen hienosäädöt ja upotukset.                           |  3   |   V   |

---

## 11.4 Tarkoituksen rajoittaminen ja laajuuden hallinta

|   #    | Kuvaus                                                                                                                                                                  | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.4.1 | Varmista, että jokaisella tietoaineistolla ja mallin tarkistuspisteellä on koneellisesti luettava tarkoitustunniste, joka on linjassa alkuperäisen suostumuksen kanssa. |  1   |   D   |
| 11.4.2 | Varmista, että ajoaikaiset valvontajärjestelmät havaitsevat tarkoituksenmukaisuutta rikkovat kyselyt ja laukaisevat pehmeän kieltoonvieton.                             |  1   |  D/V  |
| 11.4.3 | Varmista, että politiikka-koodina -portit estävät mallien uudelleenvientin uusille toimialueille ilman DPIA-arviointia.                                                 |  3   |   D   |
| 11.4.4 | Varmista, että muodolliset jäljitettävyystodistukset osoittavat jokaisen henkilötietojen elinkaaren pysyvän suostumuksen mukaisessa laajuudessa.                        |  3   |   V   |

---

## 11.5 Suostumuksen hallinta ja lainmukaisen perustan seuranta

|   #    | Kuvaus                                                                                                                                                                                          | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.5.1 | Varmista, että suostumus- ja hallintajärjestelmä (Consent-Management Platform, CMP) tallentaa rekisteröidyn suostumuksen tilan, käyttötarkoituksen ja säilytysajan kunkin rekisteröidyn osalta. |  1   |  D/V  |
| 11.5.2 | Varmista, että API:t tarjoavat suostumusmerkkejä; mallien on validoitava merkin laajuus ennen päättelyä.                                                                                        |  2   |   D   |
| 11.5.3 | Varmista, että evätty tai peruutettu suostumus pysäyttää käsittelyputket 24 tunnin kuluessa.                                                                                                    |  2   |  D/V  |

---

## 11.6 Federated Learning yksityisyyden hallinnalla

|   #    | Kuvaus                                                                                                                         | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 11.6.1 | Varmista, että asiakaspäivityksissä käytetään paikallisen differentiaalisen yksityisyyden melun lisäämistä ennen yhdistämistä. |  1   |   D   |
| 11.6.2 | Varmista, että koulutusmittarit ovat differentiaalisesti yksityisiä eivätkä koskaan paljasta yksittäisen asiakkaan häviötä.    |  2   |  D/V  |
| 11.6.3 | Varmista, että myrkytyksenkestävä aggregointi (esim. Krum/Trimmed-Mean) on otettu käyttöön.                                    |  2   |   V   |
| 11.6.4 | Varmista, että muodolliset todistukset osoittavat kokonais-ε-budjetin vähemmän kuin 5 hyötymenetyksellä.                       |  3   |   V   |

---

### Viitteet

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

