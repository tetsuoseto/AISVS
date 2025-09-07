# C8 Muistin, upotusten ja vektoritietokantojen tietoturva

## Ohjaustavoite

Upotukset ja vektorivarastot toimivat nykyaikaisten tekoälyjärjestelmien "elävänä muistina", vastaanottaen jatkuvasti käyttäjän antamia tietoja ja palauttaen ne mallin konteksteihin hakua vahvistavan generoinnin (RAG) avulla. Jos tätä muistia ei valvota, se voi vuotaa henkilötietoja, rikkoa suostumuksia tai olla käännettävissä alkuperäisen tekstin rekonstruoimiseksi. Tämän kontrolliperheen tavoitteena on vahvistaa muistin käsittelyketjuja ja vektoritietokantoja siten, että pääsy on vähimmän etuoikeuden periaatteen mukaista, upotukset säilyttävät yksityisyyden, tallennetut vektorit vanhenevat tai ne voidaan peruuttaa pyynnöstä, ja yksittäisen käyttäjän muisti ei koskaan saastuta toisen käyttäjän kehotteita tai tuloksia.

---

## C8.1 Pääsynvalvonta muistiin ja RAG-indekseihin

Ota käyttöön yksityiskohtaiset käyttöoikeuksien valvontamekanismit jokaiseen vektorikokoelmaan.

|   #   | Kuvaus                                                                                                                                                                  | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.1.1 | Varmista, että rivin/nimiavaruustason käyttöoikeussäännöt rajoittavat lisäys-, poisto- ja kyselytoiminnot vuokralaisen, kokoelman tai asiakirjan tunnisteen mukaan.     |  1   |  D/V  |
| 8.1.2 | Varmista, että API-avaimet tai JWT:t sisältävät rajattuja lupauksia (esim. kokoelman tunnisteet, toimintoverbit) ja että ne kierrätetään vähintään neljännesvuosittain. |  1   |  D/V  |
| 8.1.3 | Varmista, että oikeuksien korotuspyrkimykset (esim. ristialueen samankaltaisuuskyselyt) havaitaan ja kirjataan SIEM-järjestelmään 5 minuutin kuluessa.                  |  2   |  D/V  |
| 8.1.4 | Varmista, että vektorikanta kirjaa tarkastuslokeihin aiheen tunnisteen, toimenpiteen, vektorin tunnuksen/nimiavaruuden, samankaltaisuuskynnyksen ja tulosten määrän.    |  2   |  D/V  |
| 8.1.5 | Varmista, että pääsypäätöksiä testataan ohitusvirheiden varalta aina, kun moottoreita päivitetään tai hakemistojen shardauksen sääntöjä muutetaan.                      |  3   |   V   |

---

## C8.2 Upotuksen puhdistus ja validointi

Esikäsittele teksti PII:n varalta, sensuroi tai pseudonymisoi ennen vektorisointia, ja tarvittaessa jälkikäsittele upotuksia poistaaksesi jäljellä olevat signaalit.

|   #   | Kuvaus                                                                                                                                                                                                                     | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.2.1 | Varmista, että tunnistettavissa oleva henkilötieto (PII) ja säännelty tieto havaitaan automaattisten luokittelijoiden avulla ja käsitellään peittämällä, tokenisoimalla tai poistamalla ennen upotusta.                    |  1   |  D/V  |
| 8.2.2 | Varmista, että upotusputket hylkäävät tai eristävät syötteet, jotka sisältävät suoritettavaa koodia tai ei-UTF-8-artefakteja, jotka voisivat myrkyttää indeksin.                                                           |  1   |   D   |
| 8.2.3 | Varmista, että lauseiden upotuksiin, joiden etäisyys mihin tahansa tunnettuun henkilötietoon (PII-token) alittaa määriteltävissä olevan kynnyksen, sovelletaan paikallista tai metristä differentiaalisuojatun käsittelyä. |  2   |  D/V  |
| 8.2.4 | Varmista, että puhdistuksen tehokkuus (esim. henkilötietojen poistamisen palauttavuus, semanttinen poikkeama) validoidaan vähintään puolen vuoden välein vertailukorpusten avulla.                                         |  2   |   V   |
| 8.2.5 | Varmista, että puhdistusasetukset ovat versiohallinnassa ja muutokset käyvät läpi vertaisarvioinnin.                                                                                                                       |  3   |  D/V  |

---

## C8.3 Muistin vanhentuminen, peruutus ja poistaminen

GDPR:n "oikeus tulla unohdetuksi" ja vastaavat lait vaativat tietojen oikea-aikaista poistamista; vektorivarastojen on siksi tuettava TTL:a, pysyviä poistoja ja tomb-stoningia, jotta peruutettuja vektoreita ei voida palauttaa tai uudelleenhakemistää.

|   #   | Kuvaus                                                                                                                                                                    | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.3.1 | Varmista, että jokaisella vektorilla ja metatietueella on TTL tai selkeä säilytysmerkintä, jota automaattiset siivoustyöt noudattavat.                                    |  1   |  D/V  |
| 8.3.2 | Varmista, että käyttäjän aloittamat poistopyynnöt poistavat vektoridatat, metatiedot, välimuistikopiot ja johdetut indeksit 30 päivän kuluessa.                           |  1   |  D/V  |
| 8.3.3 | Varmista, että loogisten poistojen jälkeen suoritetaan kryptografinen tietojen hävitys tallennuslohkoista, jos laitteisto tukee sitä, tai avainholvin avaimen tuhoaminen. |  2   |   D   |
| 8.3.4 | Varmista, että vanhentuneet vektorit poistetaan lähimmän naapurin haun tuloksista alle 500 ms kuluttua vanhentumisesta.                                                   |  3   |  D/V  |

---

## C8.4 Estä upotuksen kääntäminen ja vuoto

Viimeaikaiset suojaukset—kohinan ylikytkentä, projektioverkot, yksityisyysneuronin häirintä ja sovelluskerroksen salaus—voivat laskea token-tason käänteisprosentit alle 5%:n.

|   #   | Kuvaus                                                                                                                                                                                     | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 8.4.1 | Varmista, että virallinen uhkamalli, joka kattaa käänteis-, jäsenyys- ja attribuuttipäättelyhyökkäykset, on olemassa ja sitä tarkastellaan vuosittain.                                     |  1   |   V   |
| 8.4.2 | Varmista, että sovelluskerroksen salaus tai haettavissa oleva salaus suojaa vektoreita infrastruktuurin ylläpitäjien tai pilvipalveluhenkilöstön suorilta lukuoikeuksilta.                 |  2   |  D/V  |
| 8.4.3 | Varmista, että suojausparametrit (ε DP:lle, kohina σ, projektion järjestys k) tasapainottavat yksityisyyden ≥ 99 % token-suojauksen ja hyödyllisyyden ≤ 3 % tarkkuuden menetyksen välillä. |  3   |   V   |
| 8.4.4 | Varmista, että kääntöresistenssimittarit ovat osana julkaisukriteerejä mallipäivityksille, ja että regressiorajat on määritelty.                                                           |  3   |  D/V  |

---

## C8.5 Käyttäjäkohtaisen muistin laajuuden valvonta

Vuokralaisten välinen vuoto pysyy edelleen merkittävänä RAG-riskinä: väärin suodatetut samankaltaisuushakujen tulokset voivat paljastaa toisen asiakkaan yksityiset asiakirjat.

|   #   | Kuvaus                                                                                                                                                                                                      | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.5.1 | Varmista, että jokainen hakukysely suodatetaan jälkikäteen vuokralaisen/käyttäjän tunnuksen perusteella ennen sen välittämistä LLM-kehotteeseen.                                                            |  1   |  D/V  |
| 8.5.2 | Varmista, että kokoelman nimet tai nimialueelliset tunnisteet suolataan käyttäjäkohtaisesti tai vuokralaiskohtaisesti, jotta vektorit eivät voi törmätä eri kontekseissa.                                   |  1   |   D   |
| 8.5.3 | Varmista, että samankaltaisuustulokset, jotka ylittävät konfiguroitavan etäisyyskynnyksen mutta ovat kutsujan laajuuden ulkopuolella, hylätään ja laukaisevat tietoturvahälytykset.                         |  2   |  D/V  |
| 8.5.4 | Varmista, että monivuokralaiskuormitustestit simuloivat vastustavia kyselyitä, jotka yrittävät saada käyttöönsä sallitun alueen ulkopuolisia asiakirjoja, ja osoittavat täydellisen tietovuodon poissaolon. |  2   |   V   |
| 8.5.5 | Varmista, että salausavaimet on eroteltu vuokraajittain, varmistaen kryptografisen eristyksen, vaikka fyysinen tallennustila olisi jaettu.                                                                  |  3   |  D/V  |

---

## C8.6 Edistynyt muistojärjestelmän turvallisuus

Turvallisuusvalvontatoimenpiteet kehittyneille muistirakenteille, kuten episodiselle, semanttiselle ja työmuistille, joissa on erityiset eristys- ja validointivaatimukset.

|   #   | Kuvaus                                                                                                                                                                                                                                                            | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.6.1 | Varmista, että eri muistityypeillä (episodinen, semanttinen, työmuisti) on eristetyt suojauskontekstit, joissa on roolipohjaiset käyttöoikeudet, erilliset salausavaimet ja dokumentoidut käyttömallit kullekin muistityypille.                                   |  1   |  D/V  |
| 8.6.2 | Varmista, että muistin konsolidointiprosessit sisältävät turvallisuusvarmistuksen haitallisten muistojen lisäämisen estämiseksi sisällön puhdistuksen, lähteen vahvistamisen ja eheystarkastusten avulla ennen tallennusta.                                       |  2   |  D/V  |
| 8.6.3 | Varmista, että muistihakukyselyt vahvistetaan ja puhdistetaan estämään luvattoman tiedon poiminta kyselymallianalyysin, käyttöoikeuksien valvonnan ja tulosten suodatuksen avulla.                                                                                |  2   |  D/V  |
| 8.6.4 | Varmista, että muistinhukan mekanismit poistavat arkaluonteiset tiedot turvallisesti kryptografisen poistamisen takuilla käyttämällä avaimen poistamista, monikerroksista ylikirjoitusta tai laitteistopohjaista turvallista poistamista varmennustodistuksineen. |  3   |  D/V  |
| 8.6.5 | Varmista, että muistijärjestelmän eheyttä valvotaan jatkuvasti luvattomien muutosten tai korruptoitumisen varalta tarkistussummien, tarkastuslokien ja automaattisten hälytysten avulla, kun muistin sisältö muuttuu normaalitoimintojen ulkopuolella.            |  3   |  D/V  |

---

## Viitteet

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

