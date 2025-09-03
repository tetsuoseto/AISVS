# 11 Tietosuoja ja henkilötietojen hallinta

## Kontrollitavoite

Pidä tiukat yksityisyyden takeet koko tekoälyelinkaaren aikana—keruusta, koulutuksesta, inferenssistä ja tapahtumien käsittelystä—siten, että henkilötietoja käsitellään vain selkeän suostumuksen perusteella, mahdollisimman pienellä välttämättömällä laajuudella, todistettavalla poistamisella ja muodollisilla yksityisyyden takeilla.

---

## 11.1 Anonymisointi ja tietojen minimointi

|   #    | Kuvaus                                                                                                                                                              | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.1.1 | Varmista, että suorat tunnisteet ja kvasi-identifikaattorit on poistettu ja hashattu.                                                                               |  1   |  D/V  |
| 11.1.2 | Varmista, että automatisoidut auditoinnit mittaavat k-anonymiteetin ja l-diversiteetin, ja hälyttävät, kun kynnysarvot laskevat alle politiikan asettamien arvojen. |  2   |  D/V  |
| 11.1.3 | Varmista, että mallin ominaisuuksien tärkeysraportit osoittavat, ettei tunnistevuotoa ole yli ε = 0.01 mutual information tasolla.                                  |  2   |   V   |
| 11.1.4 | Varmista, että muodolliset todisteet tai synteettistä dataa koskeva sertifiointi osoittavat uudelleen-identifioinnin riskin ≤ 0.05 jopa linkityshyökkäysten aikana. |  3   |   V   |

---

## 11.2 Oikeus tulla unohdetuksi ja poistamisen täytäntöönpano

|   #    | Kuvaus                                                                                                                                                                                                      | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.2.1 | Varmista, että rekisteröityjen poistopyyntöjen leviäminen ulottuu raakadatasetteihin, tallennuspisteisiin, upotuksiin, lokitietoihin ja varmuuskopioihin palvelutasosopimusten mukaisesti alle 30 päivässä. |  1   |  D/V  |
| 11.2.2 | Varmista, että "machine-unlearning" -rutiinit fyysisesti uudelleenkouluttavat tai arvioivat poistamisen toteutusta käyttämällä sertifioituja unlearning-algoritmeja.                                        |  2   |   D   |
| 11.2.3 | Tarkista, että varjomallin arviointi osoittaa unohtuneiden tietueiden vaikutuksen olevan alle 1 %:n tuloksista unohduksen jälkeen.                                                                          |  2   |   V   |
| 11.2.4 | Varmista, että poistotapahtumat kirjataan muuttumattomasti ja ovat auditoitavissa sääntelyviranomaisia varten.                                                                                              |  3   |   V   |

---

## 11.3 Differentiaalisen yksityisyyden turvatoimet

|   #    | Kuvaus                                                                                                             | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 11.3.1 | Varmista, että privacy-loss accounting -kojelautat varoittavat, kun kumulatiivinen ε ylittää politiikan kynnykset. |  2   |  D/V  |
| 11.3.2 | Varmista, että mustan laatikon tietosuoja-auditoinnit arvioivat ε̂:n 10%:n sisällä ilmoitetusta arvosta.           |  2   |   V   |
| 11.3.3 | Tarkista, että formaalit todistukset kattavat kaikki koulutuksen jälkeiset hienosäädöt ja upotukset.               |  3   |   V   |

---

## 11.4 Tarkoituksen rajoittaminen ja laajuuden laajentumisen ehkäisy

|   #    | Kuvaus                                                                                                                                                               | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.4.1 | Varmista, että jokaisella datasettillä ja mallin tallennuspisteellä on koneellisesti luettava tarkoitustagi, joka on yhdenmukainen alkuperäisen suostumuksen kanssa. |  1   |   D   |
| 11.4.2 | Varmista, että ajonaikaiset valvontajärjestelmät havaitsevat ilmoitetun tarkoituksen kanssa ristiriitaiset kyselyt ja laukaisevat pehmeän kieltäytymisen.            |  1   |  D/V  |
| 11.4.3 | Varmista, että policy-as-code-portit estävät mallien uudelleenkäyttöönoton uusiin alueisiin ilman DPIA-arviointia.                                                   |  3   |   D   |
| 11.4.4 | Varmista, että muodolliset jäljittävyystodisteet osoittavat, että jokaisen henkilötiedon elinkaari pysyy suostumuksella määritellyn laajuuden sisällä.               |  3   |   V   |

---

## 11.5 Suostumuksen hallinta & lainmukaisten-perusteiden seuranta

|   #    | Kuvaus                                                                                                                           | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.5.1 | Varmista, että Suostumushallintajärjestelmä (CMP) tallentaa opt-in-tila, tarkoituksen ja säilytysajan kullekin tietosubjektille. |  1   |  D/V  |
| 11.5.2 | Varmista, että API:t paljastavat suostumustokenit; malleilla on vahvistettava tokenin laajuus ennen inferenssia.                 |  2   |   D   |
| 11.5.3 | Varmista, että hylätty tai peruutettu suostumus pysäyttää käsittelyputket 24 tunnin kuluessa.                                    |  2   |  D/V  |

---

## 11.6 Hajautettu oppiminen yksityisyydenhallintakeinojen kanssa

|   #    | Kuvaus                                                                                                                                         | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.6.1 | Varmista, että asiakaspäivitykset käyttävät paikallisen differentiaalisen yksityisyyden melun lisäämistä ennen aggregointia.                   |  1   |   D   |
| 11.6.2 | Varmista, että koulutuksen mittarit ovat differentiaalisen yksityisyyden suojaamia eikä ne koskaan paljasta yksittäisen asiakkaan tappioarvoa. |  2   |  D/V  |
| 11.6.3 | Varmista, että myrkytysresistentti aggregointi (esim. Krum/Trimmed-Mean) on käytössä.                                                          |  2   |   V   |
| 11.6.4 | Varmista, että muodolliset todistukset osoittavat kokonais-ε-budjetin, jossa hyötymenetys on alle 5.                                           |  3   |   V   |

---

### Lähteet

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

