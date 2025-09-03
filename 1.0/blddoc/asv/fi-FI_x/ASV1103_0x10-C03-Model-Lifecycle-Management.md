# C3 Mallin elinkaaren hallinta ja muutoksenhallinta

## Kontrollitavoite

Tekoälyjärjestelmien on toteutettava muutoksenhallintaprosesseja, jotka estävät luvattomat tai turvallisuusriskeihin johtavat mallimuutokset pääsemästä tuotantoon. Tämä hallintakeino varmistaa mallin eheyden koko elinkaaren ajan--kehityksestä käyttöönottoon ja poistamiseen käytöstä--joka mahdollistaa nopean reagoinnin häiriötilanteisiin ja vastuullisuuden ylläpidon kaikista muutoksista.

Pääasiallinen turvallisuustavoite: Ainoastaan valtuutetut, validoidut mallit otetaan tuotantoon käyttämällä hallittuja prosesseja, jotka ylläpitävät eheyden, jäljitettävyyden ja palautettavuuden.

---

## C3.1 Mallin valtuutus ja eheys

Ainoastaan valtuutetut mallit, joilla on varmennettu eheys, pääsevät tuotantoympäristöihin.

|   #   | Kuvaus                                                                                                                                                                                                     | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.1.1 | Varmista, että kaikki mallin artefaktit (painot, konfiguraatiot, tokenisoijat) ovat kryptografisesti allekirjoitetut valtuutettujen tahojen toimesta ennen käyttöönottoa.                                  |  1   |  D/V  |
| 3.1.2 | Varmista, että mallin eheys tarkistetaan käyttöönoton aikana, ja allekirjoituksen vahvistuksen epäonnistuminen estää mallin lataamisen.                                                                    |  1   |  D/V  |
| 3.1.3 | Varmista, että mallin alkuperäistiedot sisältävät valtuuttavan tahon identiteetin, koulutusdatan tarkistussummat, validointitestien tulokset, joissa on läpäisty/epäonnistunut tila, sekä luontiaikaleima. |  2   |  D/V  |
| 3.1.4 | Varmista, että kaikki malli-artefaktit noudattavat semanttista versionointia (MAJOR.MINOR.PATCH) dokumentoitujen kriteerien mukaan, jotka määrittävät, milloin kunkin version komponentti kasvaa.          |  2   |  D/V  |
| 3.1.5 | Varmista, että riippuvuuksien seuranta ylläpitää reaaliaikaista varastoa, joka mahdollistaa kaikkien kuluttavien järjestelmien nopean tunnistamisen.                                                       |  2   |   V   |

---

## C3.2 Mallin validointi ja testaus

Mallien on läpäistävä määritellyt turvallisuus- ja varmistusarvioinnit ennen käyttöönottoa.

|   #   | Kuvaus                                                                                                                                                                                                                                                         | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.2.1 | Varmista, että mallit käyvät läpi automaattisen turvallisuustestauksen, johon kuuluu syötteen validointi, tulosten sanitointi ja turvallisuusarvioinnit ennen käyttöönottoa, sekä että etukäteen sovitut organisaation läpäisy- ja hylkäyskynnykset täyttyvät. |  1   |  D/V  |
| 3.2.2 | Varmista, että validointivirheet estävät automaattisesti mallin käyttöönoton sen jälkeen, kun on saatu nimenomainen ohituslupa ennalta määrätyiltä valtuutetuilta henkilöiltä, joilla on dokumentoidut liiketoimintaperusteet.                                 |  1   |  D/V  |
| 3.2.3 | Varmista, että testitulokset ovat kryptografisesti allekirjoitettuja ja muuttumattomasti linkitettyjä tietyn malliversion hash-arvoon, jota validoidaan.                                                                                                       |  2   |   V   |
| 3.2.4 | Varmista, että hätäkäyttöönotot edellyttävät dokumentoidun turvallisuusriskinarvioinnin sekä ennalta määrätyn turvallisuusviranomaisen hyväksynnän ennalta sovittujen aikarajojen puitteissa.                                                                  |  2   |  D/V  |

---

## C3.3 Säännelty käyttöönotto & palautus

Mallien käyttöönotot ovat hallittavia, valvottavia ja palautettavissa.

|   #   | Kuvaus                                                                                                                                                                                                                                                                                           | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 3.3.1 | Varmista, että tuotantokäyttöönotot toteuttavat asteittaisia käyttöönotto­mekanismeja (canary-käyttöönotot, blue-green-käyttöönotot) automaattisilla peruutuslaukaimilla, jotka perustuvat ennalta sovittuihin virheprosentteihin, latenssi-kynnysarvoihin tai turvallisuushälytys-kriteereihin. |  1   |   D   |
| 3.3.2 | Varmista, että palautusominaisuudet palauttavat koko mallin tilan (painot, konfiguraatiot, riippuvuudet) atomisesti ennalta määriteltyjen organisaation aikavälejen puitteissa.                                                                                                                  |  1   |  D/V  |
| 3.3.3 | Varmista, että käyttöönoton prosessit vahvistavat kryptografiset allekirjoitukset ja laskevat eheystarkisteet ennen mallin aktivointia, ja käyttöönotto epäonnistuu, jos niissä on ristiriita.                                                                                                   |  2   |  D/V  |
| 3.3.4 | Varmista, että hätätilan mallin sulkemistoiminnot voivat ottaa mallin päätepisteet pois käytöstä ennalta määriteltyjen vasteaikojen puitteissa automatisoitujen katkaisijoiden tai manuaalisten tappokytkinten avulla.                                                                           |  2   |  D/V  |
| 3.3.5 | Varmista, että palautusartefaktit (aiemmat malliversiot, konfiguraatiot, riippuvuudet) säilytetään organisaation politiikkojen mukaan muuttumattomassa tallennuksessa häiriötilanteisiin vastaamista varten.                                                                                     |  2   |   V   |

---

## C3.4 Muutosvastuu ja auditointi

Kaikki mallin elinkaaren muutokset ovat jäljitettävissä ja auditoitavissa.

|   #   | Kuvaus                                                                                                                                                                                                                                                                   | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 3.4.1 | Varmista, että kaikki mallimuutokset (käyttöönotto, konfiguraatio, poistaminen käytöstä) tuottavat muuttumattomia auditointitietueita, jotka sisältävät aikaleiman, todennetun toimijan identiteetin, muutostyypin sekä ennen/jälkeen tilat.                             |  1   |   V   |
| 3.4.2 | Varmista, että auditlokin pääsy edellyttää asianmukaista valtuutusta ja kaikki pääsyyritykset kirjataan käyttäjän identiteetillä ja aikaleimalla.                                                                                                                        |  2   |  D/V  |
| 3.4.3 | Varmista, että prompt-mallit ja järjestelmäviestit ovat git-repositorioissa versionhallinnassa, ja niihin on pakollinen koodikatselmointi ja hyväksyntä nimettyjen tarkastajien toimesta ennen käyttöönottoa.                                                            |  2   |  D/V  |
| 3.4.4 | Varmista, että auditointilokit sisältävät riittävän yksityiskohtaiset tiedot (mallin hash-arvot, kokoonpanon tilannekuvat, riippuvuuksien versiot), jotta mallin tilan täydellinen rekonstruointi on mahdollista minkä tahansa aikaleiman sisällä säilytysjakson aikana. |  2   |   V   |

---

## C3.5 Turvalliset kehityskäytännöt

Mallin kehitys- ja koulutusprosesseja on noudatettava turvallisten käytäntöjen mukaan, jotta kompromissilta vältytään.

|   #   | Kuvaus                                                                                                                                                                                                                      | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.5.1 | Varmista, että mallin kehitys-, testaus- ja tuotantoympäristöt ovat fyysisesti tai loogisesti erillisiä. Niillä ei ole jaettua infrastruktuuria, niillä on erilliset pääsynhallintajärjestelmät ja eristetyt tietovarastot. |  1   |   D   |
| 3.5.2 | Varmista, että mallin koulutus ja hienosäätö tapahtuvat eristetyissä ympäristöissä, joihin pääsy verkkoon on rajoitettua.                                                                                                   |  1   |   D   |
| 3.5.3 | Varmista, että koulutusdatan lähteet on validoitu eheystarkistuksilla ja todennettu luotettujen lähteiden kautta dokumentoidulla hallussapitoketjulla ennen niiden käyttöä mallin kehittämisessä.                           |  1   |  D/V  |
| 3.5.4 | Varmista, että mallikehityksen artefaktit (hyperparametrit, koulutusskriptit, konfiguraatiotiedostot) ovat tallennettu versionhallintaan ja että vertaisarvioinnin hyväksyntä vaaditaan ennen niiden käyttöä koulutuksessa. |  2   |   D   |

---

## C3.6 Mallin poistaminen käytöstä

Mallien on poistuttava turvallisesti, kun niitä ei enää tarvita tai kun turvallisuusongelmat on tunnistettu.

|   #   | Kuvaus                                                                                                                                                                                                                                                 | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 3.6.1 | Varmista, että mallien käytöstä poistamisen prosessit skannaavat automaattisesti riippuvuuskarttoja, tunnistavat kaikki mallia käyttävät järjestelmät ja antavat ennalta sovitut varoitusajat ennen poistamista käytöstä.                              |  1   |   D   |
| 3.6.2 | Varmista, että käytöstä poistetut malliartefaktit pyyhitetään turvallisesti kryptografisen tyhjennyksen tai moninkertaisen ylikirjoituksen avulla dokumentoitujen tietojen säilyttämiskäytäntöjen mukaan sekä vahvistetuilla hävityksen todistuksilla. |  1   |  D/V  |
| 3.6.3 | Varmista, että mallin käytöstä poistamiseen liittyvät tapahtumat kirjataan aikaleimalla ja tekijäidentiteetillä, ja mallin allekirjoitukset peruutetaan estämään uudelleenkäyttöä.                                                                     |  2   |   V   |
| 3.6.4 | Varmista, että hätämallin poistaminen käytöstä voi estää mallin pääsyn ennalta määriteltyjen hätävasteen aikajaksojen puitteissa automaattisten tappokytkinten avulla, jos kriittisiä turvallisuushaavoittuvuuksia havaitaan.                          |  2   |  D/V  |

---

## Lähteet

* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Securing AI/ML Ops – Cisco.com](https://sec.cloudapps.cisco.com/security/center/resources/SecuringAIMLOps)
* [Audit logs security: cryptographically signed tamper-proof logs](https://www.cossacklabs.com/blog/audit-logs-security/)
* [Machine Learning Model Versioning: Top Tools & Best Practices](https://lakefs.io/blog/model-versioning/)
* [AI Hygiene Starts with Models and Data Loaders – SEI Blog](https://insights.sei.cmu.edu/documents/6190/AI-Hygiene-Starts-with-Models-and-Data-Loaders_1G0KTRh.pdf)
* [How to handle versioning and rollback of a deployed ML model?](https://learn.microsoft.com/en-au/answers/questions/1845378/how-to-handle-versioning-and-rollback-of-a-deploye)
* [Reinforcement fine-tuning – OpenAI API](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [Auditing Machine Learning models: Governance, Data Security and …](https://www.linkedin.com/pulse/auditing-machine-learning-models-governance-data-security-negrete-yn81f)
* [Adversarial Training to Improve Model Robustness](https://medium.com/%40amit25173/adversarial-training-to-improve-model-robustness-5e285b516713)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)
* [Exploring Data Provenance: Ensuring Data Integrity and Authenticity](https://www.astera.com/type/blog/data-provenance/)
* [MITRE ATLAS](https://atlas.mitre.org/)
* [AWS Prescriptive Guidance – Best practices for retiring applications …](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/migration-app-retirement-best-practices/migration-app-retirement-best-practices.pdf)

