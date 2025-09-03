# C1 Koulutusdatan hallinta ja vinoumien hallinta

## Kontrollitavoite

Koulutusdata on hankittava, käsiteltävä ja ylläpidettävä tavalla, joka säilyttää sen jäljitettävyyden, turvallisuuden, laadun ja oikeudenmukaisuuden. Näin toimimalla se täyttää oikeudelliset velvoitteet ja vähentää koulutuksen aikana ilmenneiden vinoumien, myrkytysyritysten tai yksityisyyden loukkauksien riskejä, jotka voisivat vaikuttaa koko tekoälyn elinkaareen.

---

## C1.1 Koulutusdatan alkuperä

Pidä yllä todistettavissa olevaa luetteloa kaikista tietojoukoista, hyväksy vain luotettavat lähteet, ja kirjaa jokainen muutos auditointia varten.

|   #   | Kuvaus                                                                                                                                                                                                             | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 1.1.1 | Varmista, että jokaisen koulutusdatan lähteen ajantasainen luettelo pidetään yllä (alkuperä, vastuuhenkilö/omistaja, lisenssi, keräysmenetelmä, käyttötarkoitukseen liittyvät rajoitukset sekä käsittelyhistoria). |  1   |  D/V  |
| 1.1.2 | Varmista, että koulutusdatan käsittelyprosesseissa jätetään pois turhat ominaisuudet, attribuutit tai kentät (esim. käyttämättömät metatiedot, arkaluonteiset PII-tiedot, vuotaneet testitiedot).                  |  1   |  D/V  |
| 1.1.3 | Varmista, että kaikki tietojoukon muutokset kuuluvat kirjattuun hyväksyntätyönkulkuun.                                                                                                                             |  2   |  D/V  |
| 1.1.4 | Varmista, että datasetit tai niiden osajoukot ovat vesileimattuja tai sormenjäljitettyjä, jos mahdollista.                                                                                                         |  3   |  D/V  |

---

## C1.2 Koulutusdatan turvallisuus ja eheys

Rajoita pääsy koulutusdataan, salaa se levossa ja siirron aikana, ja varmista sen eheys, jotta estetään manipulointi, varkaus tai datan saastuttaminen.

|   #   | Kuvaus                                                                                                                                                                                     | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 1.2.1 | Varmista, että käyttöoikeuksien hallinta suojaa koulutusdatan tallennusta ja putkistoja.                                                                                                   |  1   |  D/V  |
| 1.2.2 | Varmista, että kaikki pääsy koulutusdatoihin on kirjattu, mukaan lukien käyttäjä, aika ja toimenpide.                                                                                      |  2   |  D/V  |
| 1.2.3 | Varmista, että koulutusdatasetit ovat salattuja sekä siirron aikana että levossa, käyttämällä alan standardien kryptografisia algoritmeja ja avainhallintakäytäntöjä.                      |  2   |  D/V  |
| 1.2.4 | Varmista, että kryptografiset hajautukset tai digitaaliset allekirjoitukset käytetään varmistamaan koulutusdatan eheys tallennuksen ja siirron aikana.                                     |  2   |  D/V  |
| 1.2.5 | Varmista, että automaattiset havaitsemistekniikat ovat otettu käyttöön estämään koulutusdatan luvattomat muutokset tai sen korruptoituminen.                                               |  2   |  D/V  |
| 1.2.6 | Varmista, että vanhentunut koulutusdata on turvallisesti Poistettu tai anonymisoitu.                                                                                                       |  2   |  D/V  |
| 1.2.7 | Varmista, että kaikki koulutusdatan versiot ovat ainutlaatuisesti tunnistettuja, tallennettu muuttumattomasti ja auditoitavissa, jotta palautus ja forensiikka-analyysit ovat mahdollisia. |  3   |  D/V  |

---

## C1.3 Koulutusdatan merkinnän laatu, eheys ja turvallisuus

Suojaa tunnisteet ja vaadi tekninen tarkastus kriittisille tiedoille.

|   #   | Kuvaus                                                                                                                                                                                               | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.3.1 | Varmista, että kryptografiset hajautukset tai digitaaliset allekirjoitukset on liitetty label-artifakteihin niiden eheyden ja aitouden varmistamiseksi.                                              |  2   |  D/V  |
| 1.3.2 | Varmista, että merkintärajapinnat ja -alustat noudattavat vahvoja pääsynhallintakäytäntöjä, pitävät koskemattomat audit-lokit kaikista merkintätoiminnoista ja suojaavat luvattomilta muokkauksilta. |  2   |  D/V  |
| 1.3.3 | Varmista, että tunnisteisiin sisältyvä herkkä tieto on piilotettu, anonymisoitu tai salattu tietokenttätasolla sekä levossa että siirrossa.                                                          |  3   |  D/V  |

---

## C1.4 Koulutusdatan laatu ja turvallisuusvarmistus

Yhdistä automaattinen validointi, manuaaliset satunnaistarkastukset ja kirjatut korjaustoimenpiteet tietojoukon luotettavuuden varmistamiseksi.

|   #   | Kuvaus                                                                                                                                                                                                                                                                                                                                                                                                                                                | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.4.1 | Varmista, että automatisoidut testit havaitsevat formaatti-virheet ja null-arvot jokaisessa tuonnissa tai merkittävässä tietomuunnoksessa.                                                                                                                                                                                                                                                                                                            |  1   |   D   |
| 1.4.2 | Varmista, että LLM:n koulutus- ja hienosäätöputket toteuttavat myrkytyksen havaitsemisen ja tiedon eheyden validoinnin (esim. tilastolliset menetelmät, poikkeavien havaintojen havaitseminen, upotusanalyysi) tunnistaakseen sekä mahdolliset myrkytys­hyökkäykset (esim. tunnisteen vaihtaminen, takaportin laukaisimen lisääminen, roolinvaihdon käskyt, vaikuttavia havaintoja hyödyntävät hyökkäykset) että koulutusdatan tahatonta korruptiota. |  2   |  D/V  |
| 1.4.3 | Varmista, että asianmukaiset puolustuskeinot, kuten adversaarinen koulutus (käyttäen generoituja adversaarisia esimerkkejä), data-augmentointi perturboitujen syötteiden avulla tai robustit optimointitekniikat, ovat toteutettu ja viritetty riskinarvioinnin perusteella asianmukaisille malleille.                                                                                                                                                |  3   |  D/V  |
| 1.4.4 | Varmista, että automaattisesti genereoidut merkinnät (esim. LLM:ien kautta tai heikolla valvonnalla) noudattavat varmuuskynnyksiä ja johdonmukaisuustarkistuksia, jotta voidaan havaita hallusinaatioita, harhaanjohtavia tai alhaisen varmuuden merkintöjä.                                                                                                                                                                                          |  2   |  D/V  |
| 1.4.5 | Varmista, että automatisoidut testit havaitsevat labelien vinoumat jokaisessa tuonnissa tai merkittävässä datamuunnoksessa.                                                                                                                                                                                                                                                                                                                           |  3   |   D   |

---

## C1.5 Datan jäljitettävyys ja seurattavuus

Seuraa jokaisen datapisteen koko matkaa lähteestä mallin syötteeseen auditointikelpoisuuden ja häiriövasteen varmistamiseksi.

|   #   | Kuvaus                                                                                                                                                                                                                                                                                   | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.5.1 | Varmista, että kunkin datapisteen jäljitettävyys, mukaan lukien kaikki muunnokset, augmentoinnit ja yhdistämiset, on tallennettu ja että sitä voidaan rekonstruoida.                                                                                                                     |  2   |  D/V  |
| 1.5.2 | Varmista, että lineage-rekisterit ovat muuttumattomia, turvallisesti tallennettuja ja auditointeja varten käytettävissä.                                                                                                                                                                 |  2   |  D/V  |
| 1.5.3 | Varmista, että datan jäljitettävyyden seuranta kattaa synteettisen datan, joka on luotu yksityisyyden suojaamiseen tähtäävillä tai generatiivisilla tekniikoilla, ja että koko putkiston aikana kaikki synteettinen data on selvästi merkitty ja erottuu selkeästi todellisesta datasta. |  2   |  D/V  |

---

## Lähteet

* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [EU AI Act – Article 10: Data & Data Governance](https://artificialintelligenceact.eu/article/10/)
* [MITRE ATLAS: Adversary Tactics for AI](https://atlas.mitre.org/)
* [Survey of ML Bias Mitigation Techniques – MDPI](https://www.mdpi.com/2673-6470/4/1/1)
* [Data Provenance & Lineage Best Practices – Nightfall AI](https://www.nightfall.ai/ai-security-101/data-provenance-and-lineage)
* [Data Labeling Quality Standards – LabelYourData](https://labelyourdata.com/articles/data-labeling-quality-and-how-to-measure-it)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [CISA Advisory: Securing Data for AI Systems](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [ISO/IEC 23053: AI Management Systems Framework](https://www.iso.org/sectors/it-technologies/ai)
* [IBM: What is AI Governance?](https://www.ibm.com/think/topics/ai-governance)
* [Google AI Principles](https://ai.google/principles/)
* [GDPR & AI Training Data – DataProtectionReport](https://www.dataprotectionreport.com/2024/08/recent-regulatory-developments-in-training-artificial-intelligence-ai-models-under-the-gdpr/)
* [Supply-Chain Security for AI Data – AppSOC](https://www.appsoc.com/blog/ai-is-the-new-frontier-of-supply-chain-security)
* [OpenAI Privacy Center – Data Deletion Controls](https://privacy.openai.com/policies?modal=take-control)
* [Adversarial ML Dataset – Kaggle](https://www.kaggle.com/datasets/cnrieiit/adversarial-machine-learning-dataset)

