# C8-muisti, upotukset & vektoritietokantojen turvallisuus

## Kontrollitavoite

Embeddingit ja vektorivarastot toimivat nykyaikaisten tekoälyjärjestelmien 'elävänä muistina', jotka jatkuvasti vastaanottavat käyttäjältä annettua dataa ja tuovat sen takaisin mallien konteksteihin RAG-menetelmän kautta. Jos tätä muistia ei hallita, se voi vuotaa henkilötietoja (PII), rikkoa suostumuksia tai johtaa alkuperäisen tekstin rekonstruointiin. Tämän kontrolliperheen tavoitteena on vahvistaa muistiputkia ja vektorivarastoja siten, että pääsy on least-privilege-periaatteen mukaista, embeddingit ovat yksityisyyttä suojaavia, tallennetut vektorit vanhenevat tai voidaan peruuttaa pyydettäessä, ja kunkin käyttäjän muisti ei koskaan saastuta toisen käyttäjän pyyntöjä tai vastauksia.

---

## C8.1 Pääsynhallinta muistissa ja RAG-indekseissä

Toteuta hienojakoiset pääsynvalvonnat jokaiselle vektorikokoelmalle.

|   #   | Kuvaus                                                                                                                                                                     | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.1.1 | Varmista, että rivitaso- ja nimialuetason pääsynvalvontasäännöt rajoittavat lisäys-, poisto- ja kyselytoiminnot kunkin asiakkaan, kokoelman tai asiakirjamerkinnän mukaan. |  1   |  D/V  |
| 8.1.2 | Varmista, että API-avaimet tai JWT:t kantavat rajattuja vaatimuksia (esim. kokoelmatunnisteet, toimintaverbit) ja ne kierrätetään vähintään neljännesvuosittain.           |  1   |  D/V  |
| 8.1.3 | Varmista, että oikeuksien korottamisen yritykset (esim. nimialueiden väliset samankaltaisuuskyselyt) havaitaan ja kirjataan SIEMiin 5 minuutin kuluessa.                   |  2   |  D/V  |
| 8.1.4 | Varmista, että vektoritietokannan auditlokit kirjaavat käyttäjätunnisteen, toimenpiteen, vektori-ID/namespace, samankaltaisuuskynnys ja tulosten määrän.                   |  2   |  D/V  |
| 8.1.5 | Varmista, että pääsynhallinnan päätökset testataan ohitusaukkojen varalta aina, kun moottoreita päivitetään tai indeksin shardauksen säännöt muuttuvat.                    |  3   |   V   |

---

## C8.2 Upotusten sanitointi & validointi

Tarkista teksti etukäteen henkilötietojen varalta, piilota tai pseudonyymisoi ennen vektorointia, ja tarvittaessa jälkikäsitellä upotukset poistaaksesi jäljellä olevat signaalit.

|   #   | Kuvaus                                                                                                                                                                                                                 | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.2.1 | Varmista, että PII ja säännelty data tunnistetaan automaattisilla luokittelijoilla ja maskataan, tokenisoidaan tai poistetaan ennen upottamista.                                                                       |  1   |  D/V  |
| 8.2.2 | Varmista, että upotusputket hylkäävät tai eristävät syötteet, jotka sisältävät suoritettavaa koodia tai ei-UTF-8-artifakteja, jotka voisivat saastuttaa indeksin.                                                      |  1   |   D   |
| 8.2.3 | Varmista, että paikallinen tai metrinen differentiaalisen yksityisyyden sanitointi sovelletaan lauseen upotusvektoreihin, joiden etäisyys mihinkä tahansa tunnettuun PII-tunnukseen on alle määritettävän kynnysarvon. |  2   |  D/V  |
| 8.2.4 | Varmista, että sanitoinnin tehokkuus (esim. PII:n punaisoinnin kattavuus, semanttinen muutos) validoidaan vähintään puolivuosittain benchmark-korpora vastaan.                                                         |  2   |   V   |
| 8.2.5 | Varmista, että sanitointikonfiguraatiot ovat versionhallinnassa ja muutokset käyvät vertaisarvioinnin läpi.                                                                                                            |  3   |  D/V  |

---

## C8.3 Muistin vanhentuminen, peruutus ja poisto

GDPR 'oikeus tulla unohdetuksi' ja vastaavat lait edellyttävät oikea-aikaista poistamista; vektorivarastojen on siksi tuettava TTL-arvot, kovapoistot ja hautausmerkinnät, jotta peruutetut vektorit eivät voi palautua tai uudelleenindeksoida.

|   #   | Kuvaus                                                                                                                                                            | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.3.1 | Varmista, että jokainen vektori- ja metadata-tietue sisältää TTL:n tai selkeän säilytysmerkinnän, jota automatisoidut siivoustoiminnot noudattavat.               |  1   |  D/V  |
| 8.3.2 | Varmista, että käyttäjän aloittamat poistopyynnöt poistavat vektorit, metatiedot, välimuistikopiot ja johdannaisindeksit 30 päivän kuluessa.                      |  1   |  D/V  |
| 8.3.3 | Varmista, että loogiset poistot toteutetaan kryptografisella tuhoamisella tallennuslohkoille, jos laitteisto tukee sitä, tai että avainvaraston avaimet tuhotaan. |  2   |   D   |
| 8.3.4 | Varmista, että vanhentuneet vektorit poistetaan lähimmän naapurin haun tuloksista alle 500 ms kuluttua vanhentumisesta.                                           |  3   |  D/V  |

---

## C8.4 Estä upotusten inversio & vuoto

Viimeaikaiset puolustukset—kohinan superpositio, projektioverkot, privacy-neuronin perturbointi ja sovelluskerroksen salaus—voivat alentaa token-tason inversioprosentteja alle 5%.

|   #   | Kuvaus                                                                                                                                                                                          | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.4.1 | Varmista, että muodollinen uhkamalli, joka kattaa inversiohyökkäykset, jäsenyyden inferenssi-hyökkäykset ja attribuuttien inferenssi-hyökkäykset, on olemassa ja sitä tarkastellaan vuosittain. |  1   |   V   |
| 8.4.2 | Varmista, että sovelluskerroksen salaus tai haettavissa oleva salaus suojaa vektoreita suorilta lukemilta infrastruktuurin ylläpitäjien tai pilviympäristön henkilöstön toimesta.               |  2   |  D/V  |
| 8.4.3 | Varmista, että suojausparametrit (ε DP:lle, kohinan σ, projektion rank k) tasapainottavat yksityisyyden ≥ 99 % tokenin suojauksen ja hyödyllisyyden ≤ 3 % tarkkuuden menetys.                   |  3   |   V   |
| 8.4.4 | Varmista, että inversio-resilienssimittarit ovat osa julkaisun portteja mallipäivityksiä varten, ja että niille on määritelty regressiobudjetit.                                                |  3   |  D/V  |

---

## C8.5 Käyttäjäkohtaisen muistin laajuuden valvonta

Cross-tenant leakage on edelleen yksi suurimmista RAG-riskeistä: virheellisesti suodatetut samankaltaisuuskyselyt voivat paljastaa toisen asiakkaan yksityiset dokumentit.

|   #   | Kuvaus                                                                                                                                                                           | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.5.1 | Varmista, että jokainen haun kysely on jälkisuodatettu vuokraajan tai käyttäjän tunnisteen mukaan ennen kuin se siirretään LLM:n kehotteeseen.                                   |  1   |  D/V  |
| 8.5.2 | Varmista, että kokoelman nimet tai nimiavaruus-ID:t ovat suolatut kunkin käyttäjän tai vuokraajan mukaan, jotta vektorit eivät törmää toisiinsa eri konteksteissa.               |  1   |   D   |
| 8.5.3 | Varmista, että konfiguroitavan etäisyyskynnyksen ylittävät samankaltaisuustulokset, jotka ovat kutsujan toiminnan ulkopuolella, hylätään ja laukaistaan turvallisuusvaroituksia. |  2   |  D/V  |
| 8.5.4 | Varmista, että moniasiakkaiden kuormitustestit simuloivat hyökkäysyrityksiä, joissa yritetään hakea rajojen ulkopuolisia asiakirjoja, ja osoittavat, ettei tapahdu tietovuotoja. |  2   |   V   |
| 8.5.5 | Varmista, että salausavaimet on eroteltu kunkin vuokralaisen mukaan, jotta kryptografinen eristys säilyy, vaikka fyysinen tallennus on jaettu.                                   |  3   |  D/V  |

---

## C8.6 Kehittyneen muistijärjestelmän turvallisuus

kehittyneille muistirakenteille suunnatut turvallisuusvalvontatoimet, jotka kattavat episodisen, semanttisen ja työmuistin sekä niihin liittyvät erityiset eristys- ja validointivaatimukset.

|   #   | Kuvaus                                                                                                                                                                                                                                                               | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.6.1 | Varmista, että erilaisilla muistityypeillä (episodinen muisti, semanttinen muisti, työmuisti) on erilliset turvallisuuskontekstit, roolipohjainen pääsynvalvonta, erilliset salausavaimet sekä jokaiselle muistityypille dokumentoidut pääsynmallit.                 |  1   |  D/V  |
| 8.6.2 | Varmista, että muistien konsolidointiprosessit sisältävät turvallisuusvarmennuksen estämään haitallisten muistojen syöttöä sisällön puhdistuksen, lähteen varmennuksen ja eheysvalvonnan kautta ennen tallennusta.                                                   |  2   |  D/V  |
| 8.6.3 | Varmista, että muistista haettavat hakupyynnöt validoidaan ja puhdistetaan, jotta luvattomien tietojen paljastuminen estetään kyselykaavojen analyysin, pääsynvalvonnan toteuttamisen ja tulosten suodatuksen kautta.                                                |  2   |  D/V  |
| 8.6.4 | Varmista, että muistin pyyhkimisen mekanismit poistavat arkaluontoiset tiedot turvallisesti kryptografisen poistamisen takuilla käyttämällä avaimen poistamista, moninkertaista ylikirjoitusta tai laitteistopohjaista turvallista poistamista varmistustodistuksin. |  3   |  D/V  |
| 8.6.5 | Varmista, että muistijärjestelmän eheys valvotaan jatkuvasti luvattomien muutosten tai korruptoitumisen varalta, käyttämällä tarkistussummia, auditlokkeja ja automatisoituja hälytyksiä, kun muistisisältö muuttuu normaalin toiminnan ulkopuolelle.                |  3   |  D/V  |

---

## Lähteet

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

