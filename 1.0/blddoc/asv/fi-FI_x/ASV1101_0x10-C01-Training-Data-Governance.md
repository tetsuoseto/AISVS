# C1 Koulutusdatan hallinta ja harhan hallinta

## Ohjaustavoite

Koulutusdata on hankittava, käsiteltävä ja ylläpidettävä tavalla, joka säilyttää alkuperän, turvallisuuden, laadun ja oikeudenmukaisuuden. Näin täytetään lakisääteiset velvoitteet ja vähennetään vinouman, myrkytyksen tai tietosuojarikkomusten riskejä, jotka voivat ilmetä koulutuksen aikana ja vaikuttaa koko tekoälyn elinkaareen.

---

## C1.1 Koulutusdatan alkuperä

Pidä yllä todennettavissa olevaa luetteloa kaikista tietoaineistoista, hyväksy vain luotettavat lähteet ja kirjaa kaikki muutokset jäljitettävyyden varmistamiseksi.

|   #   | Kuvaus                                                                                                                                                                                                   | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.1.1 | Varmista, että ajantasainen luettelo jokaisesta koulutusdatan lähteestä (alkuperä, vastuuhenkilö/omistaja, lisenssi, keräystapa, suunnitellut käyttörajoitukset ja käsittelyhistoria) pidetään yllä.     |  1   |  D/V  |
| 1.1.2 | Varmista, että koulutusdatan käsittelyprosessit poistavat tarpeettomat ominaisuudet, attribuutit tai kentät (esim. käyttämättömät metatiedot, arkaluonteiset henkilötunnistetiedot, vuotanut testidata). |  1   |  D/V  |
| 1.1.3 | Varmista, että kaikki tietojoukkomuutokset kuuluvat kirjattuun hyväksymisprosessiin.                                                                                                                     |  2   |  D/V  |
| 1.1.4 | Varmista, että tietoaineistot tai alijoukot on vesileimattu tai sormenjäljet merkitty, missä mahdollista.                                                                                                |  3   |  D/V  |

---

## C1.2 Koulutusdatan turvallisuus ja eheys

Rajoita pääsy koulutusdataan, salaa se levossa ja siirron aikana ja varmista sen eheys estääksesi manipuloinnin, varkauden tai datan myrkytyksen.

|   #   | Kuvaus                                                                                                                                                           | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.2.1 | Varmista, että käyttöoikeuksien valvonta suojaa koulutusdatan tallennusta ja putkistoja.                                                                         |  1   |  D/V  |
| 1.2.2 | Varmista, että kaikki pääsy koulutusdataan kirjataan, mukaan lukien käyttäjä, aika ja toimenpide.                                                                |  2   |  D/V  |
| 1.2.3 | Varmista, että koulutusaineistot ovat salattuja siirron aikana ja levossa, käyttämällä alan standardien mukaisia salausalgoritmeja ja avainhallintakäytäntöjä.   |  2   |  D/V  |
| 1.2.4 | Varmista, että kryptografisia tiivisteitä tai digitaalisia allekirjoituksia käytetään tiedon eheyttä varmistamaan harjoitusdatan tallennuksen ja siirron aikana. |  2   |  D/V  |
| 1.2.5 | Varmista, että automatisoituja tunnistustekniikoita käytetään estämään luvattomat muutokset tai koulutusdatan vahingoittuminen.                                  |  2   |  D/V  |
| 1.2.6 | Varmista, että vanhentuneet koulutusaineistot poistetaan turvallisesti tai anonymisoidaan.                                                                       |  2   |  D/V  |
| 1.2.7 | Varmista, että kaikki koulutusdatan versiot on yksilöity, tallennettu muuttumattomasti ja auditoitavissa tukemaan palautusta ja rikosteknistä analyysiä.         |  3   |  D/V  |

---

## C1.3 Koulutusdatan merkintöjen laatu, eheys ja turvallisuus

Suojaa tunnisteet ja vaadi tekninen tarkastus kriittisille tiedoille.

|   #   | Kuvaus                                                                                                                                                                                                                               | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 1.3.1 | Varmista, että kryptografisia hajautusarvoja tai digitaalisia allekirjoituksia käytetään tunnistemateriaaleihin niiden eheyden ja aitouden varmistamiseksi.                                                                          |  2   |  D/V  |
| 1.3.2 | Varmista, että merkintäkäyttöliittymät ja -alustat toteuttavat vahvat käyttöoikeuksien hallintamekanismit, ylläpitävät manipulointia estäviä tarkastuslokeja kaikista merkintätoiminnoista ja suojaavat luvattomalta muokkaamiselta. |  2   |  D/V  |
| 1.3.3 | Varmista, että arkaluonteiset tiedot tunnisteissa on poistettu, anonymisoitu tai salattu tietokenttätasolla sekä levossa että siirrossa.                                                                                             |  3   |  D/V  |

---

## C1.4 Koulutusdatan laatu- ja turvallisuusvarmennus

Yhdistä automatisoitu validointi, manuaaliset pistotarkastukset ja kirjattu korjaustoimenpide varmistaaksesi aineiston luotettavuuden.

|   #   | Kuvaus                                                                                                                                                                                                                                                                                                                                                                                                                | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 1.4.1 | Varmista, että automatisoidut testit tunnistavat formaattivirheet ja null-arvot jokaisessa tiedon vastaanotossa tai merkittävässä datan muunnoksessa.                                                                                                                                                                                                                                                                 |  1   |   D   |
| 1.4.2 | Varmista, että LLM-koulutus- ja hienosäätöputket toteuttavat myrkytyshavaintojen ja datan eheysvalidoinnin (esim. tilastolliset menetelmät, poikkeavuuksien havaitseminen, upotusanalyysi) tunnistaakseen mahdolliset myrkytyshyökkäykset (esim. tunnisteiden kääntäminen, takaporttikäynnistimien lisäys, roolinvaihtokäskyt, vaikuttavat instanssihyökkäykset) tai tahattoman datan vaurioitumisen koulutusdatassa. |  2   |  D/V  |
| 1.4.3 | Varmista, että asianmukaiset suojaukset, kuten vastustava koulutus (generoitujen vastustavien esimerkkien käyttö), datan laajentaminen häiritetyillä syötteillä tai robustit optimointitekniikat, on otettu käyttöön ja säädetty asiaankuuluville malleille riskinarvioinnin perusteella.                                                                                                                             |  3   |  D/V  |
| 1.4.4 | Varmista, että automaattisesti tuotetut tunnisteet (esim. LLM:ien tai heikon valvonnan kautta) ovat luottamuskynnysten ja johdonmukaisuustarkistusten alaisia harhaisiksi, harhaanjohtaviksi tai matalan luottamuksen tunnisteiksi epäilyn havaitsemiseksi.                                                                                                                                                           |  2   |  D/V  |
| 1.4.5 | Varmista, että automatisoidut testit havaitsevat tunnistesiirtymät jokaisessa tietojen vastaanotossa tai merkittävässä tiedonmuutoksessa.                                                                                                                                                                                                                                                                             |  3   |   D   |

---

## C1.5 Tietojen jäljitettävyys ja alkuperän seuranta

Seuraa jokaisen datapisteen koko matkaa lähteestä mallin syötteeksi auditointia ja poikkeamien hallintaa varten.

|   #   | Kuvaus                                                                                                                                                                                                                                           | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 1.5.1 | Varmista, että kunkin datapisteen jälkeläisyys, mukaan lukien kaikki muunnokset, lisäykset ja yhdistämiset, on tallennettu ja että se voidaan rekonstruoida.                                                                                     |  2   |  D/V  |
| 1.5.2 | Varmista, että alkuperätiedot ovat muuttumattomia, turvallisesti tallennettuja ja saatavilla tarkastuksia varten.                                                                                                                                |  2   |  D/V  |
| 1.5.3 | Varmista, että jäljitettävyys kattaa tietosuojan säilyttämiseen tai generatiivisiin tekniikoihin perustuvan synteettisen datan ja että kaikki synteettinen data on selkeästi merkitty ja erotettavissa todellisesta datasta koko prosessin ajan. |  2   |  D/V  |

---

## Viitteet

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

