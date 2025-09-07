# C3-mallin elinkaaren hallinta ja muutosvalvonta

## Ohjaustavoite

tekoälyjärjestelmien on toteutettava muutosten hallintaprosessit, jotka estävät luvattomat tai ei-turvalliset mallimuutokset pääsemästä tuotantoon. Tämä valvonta varmistaa mallin eheyden koko elinkaaren ajan – kehityksestä käyttöönottoon ja poistamiseen – mikä mahdollistaa nopean reagoinnin poikkeustilanteisiin ja ylläpitää vastuullisuutta kaikista muutoksista.

Keskeinen suojaustavoite: Vain valtuutetut, validoidut mallit pääsevät tuotantoon käyttämällä hallittuja prosesseja, jotka ylläpitävät eheyden, jäljitettävyyden ja palautettavuuden.

---

## C3.1 Mallin valtuutus ja eheys

Vain valtuutetut mallityypit, joiden eheys on vahvistettu, pääsevät tuotantoympäristöihin.

|   #   | Kuvaus                                                                                                                                                                                                            | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.1.1 | Varmista, että kaikki mallin artefaktit (painot, konfiguraatiot, tokenisoijat) on kryptografisesti allekirjoitettu valtuutettujen tahojen toimesta ennen käyttöönottoa.                                           |  1   |  D/V  |
| 3.1.2 | Varmista, että mallin eheys tarkistetaan käyttöönottohetkellä ja allekirjoituksen vahvistuksen epäonnistumiset estävät mallin lataamisen.                                                                         |  1   |  D/V  |
| 3.1.3 | Varmista, että mallin jäljitettävyyden tiedoissa on mukana valtuuttavan tahon tunnistetiedot, harjoitusdatan tarkistussummat, validointitestien tulokset läpäisy-/epäonnistumistilanteineen sekä luontiaikaleima. |  2   |  D/V  |
| 3.1.4 | Varmista, että kaikki mallin artefaktit käyttävät semanttista versiointia (MAJOR.MINOR.PATCH) ja että on dokumentoitu kriteerit, jotka määrittävät, milloin kukin version osa kasvaa.                             |  2   |  D/V  |
| 3.1.5 | Varmista, että riippuvuuksien seuranta ylläpitää reaaliaikaista varastotilannetta, joka mahdollistaa kaikkien kuluttavien järjestelmien nopean tunnistamisen.                                                     |  2   |   V   |

---

## C3.2 Mallin validointi ja testaus

Mallit on läpäistävä määritellyt turvallisuus- ja varmistustarkastukset ennen käyttöönottoa.

|   #   | Kuvaus                                                                                                                                                                                                                                                       | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 3.2.1 | Varmista, että mallien läpikäyvät automatisoidut turvallisuustestit, jotka sisältävät syötteen validoinnin, tulosten puhdistuksen ja turvallisuusarvioinnit ennalta sovittujen organisaation läpäisy/epäonnistuminen-rajojen mukaisesti ennen käyttöönottoa. |  1   |  D/V  |
| 3.2.2 | Varmista, että validointivirheet estävät mallin käyttöönoton automaattisesti, ellei ennalta nimetyt valtuutetut henkilöt ole antaneet nimenomaista poikkeuslupaa kirjattujen liiketoimintaperustelujen kanssa.                                               |  1   |  D/V  |
| 3.2.3 | Varmista, että testitulokset ovat kryptografisesti allekirjoitettuja ja muuttumattomasti linkitettyjä vahvistettavan malliversion hajautusarvoon.                                                                                                            |  2   |   V   |
| 3.2.4 | Varmista, että hätäasennukset edellyttävät dokumentoitua tietoturvariskien arviointia ja hyväksyntää ennalta määritellyltä tietoturvaviranomaiselta sovittujen aikataulujen puitteissa.                                                                      |  2   |  D/V  |

---

## C3.3 Hallittu käyttöönotto ja palautus

Mallin käyttöönotot on oltava hallittuja, valvottuja ja peruutettavissa olevia.

|   #   | Kuvaus                                                                                                                                                                                                                                                                                         | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.3.1 | Varmista, että tuotantoon käyttöönotot toteuttavat asteittaiset käyttöönoton mekanismit (kanariakäyttöönotot, sinivihreät käyttöönotot) automaattisilla palautuslaukaisijoilla, jotka perustuvat ennalta sovittuihin virhesuhteisiin, viiveen raja-arvoihin tai tietoturvahälytyskriteereihin. |  1   |   D   |
| 3.3.2 | Varmista, että palautusominaisuudet palauttavat täydellisen mallin tilan (painot, asetukset, riippuvuudet) atomisesti ennalta määriteltyjen organisaation aikarajojen sisällä.                                                                                                                 |  1   |  D/V  |
| 3.3.3 | Varmista, että käyttöönottoprosessit validoivat kryptografiset allekirjoitukset ja laskevat eheystarkistussummat ennen mallin aktivointia, ja epäonnistuvat käyttöönotossa kaikissa poikkeamissa.                                                                                              |  2   |  D/V  |
| 3.3.4 | Varmista, että hätätilan mallin sammutusominaisuudet voivat poistaa mallin päätepisteet käytöstä ennalta määritettyjen vasteaikojen sisällä automaattisten katkaisijoiden tai manuaalisten katkaisukytkinten avulla.                                                                           |  2   |  D/V  |
| 3.3.5 | Varmista, että takaisinperuutuksen artefaktit (aiemmat malliversiot, kokoonpanot, riippuvuudet) säilytetään organisaation käytäntöjen mukaisesti muuttumattomassa tallennustilassa häiriötilanteisiin varautumista varten.                                                                     |  2   |   V   |

---

## C3.4 Muutosten vastuullisuus ja auditointi

Kaikkien mallin elinkaaren muutosten on oltava jäljitettäviä ja tarkastettavissa.

|   #   | Kuvaus                                                                                                                                                                                                                                           | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 3.4.1 | Varmista, että kaikki mallin muutokset (käyttöönotto, konfigurointi, käytöstä poisto) tuottavat muuttumattomia tarkastustietueita, jotka sisältävät aikaleiman, todennetun toimijan tunnisteen, muutostyypin sekä ennen ja jälkeen -tilat.       |  1   |   V   |
| 3.4.2 | Varmista, että tilintarkastuslokin käyttö vaatii asianmukaisen valtuutuksen ja kaikki käyttöyritykset kirjataan käyttäjätunnuksella ja aikaleimalla.                                                                                             |  2   |  D/V  |
| 3.4.3 | Varmista, että kehotemallit ja järjestelmäviestit ovat versionhallinnassa git-repositorioissa, ja että niihin liittyy pakollinen koodikatselmointi sekä hyväksyntä nimetyiltä tarkastajilta ennen käyttöönottoa.                                 |  2   |  D/V  |
| 3.4.4 | Varmista, että auditointitiedot sisältävät riittävät yksityiskohdat (mallin tiivisteet, kokoonpanon tilannevedokset, riippuvuuksien versiot) mahdollistamaan mallin tilan täydellisen rekonstruoinnin mille tahansa säilytysjakson aikaleimalle. |  2   |   V   |

---

## C3.5 Turvalliset kehityskäytännöt

Mallin kehitys- ja koulutusprosessien on noudatettava turvallisia käytäntöjä estääkseen vaarantumisen.

|   #   | Kuvaus                                                                                                                                                                                                                         | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 3.5.1 | Varmista, että mallin kehitys-, testaus- ja tuotantoympäristöt ovat fyysisesti tai loogisesti erillään. Niillä ei ole yhteistä infrastruktuuria, ne käyttävät erillisiä pääsynvalvontoja ja niillä on eristetyt tietovarastot. |  1   |   D   |
| 3.5.2 | Varmista, että mallin koulutus ja hienosäätö tapahtuvat eristetyissä ympäristöissä, joissa on hallittu verkon käyttöoikeus.                                                                                                    |  1   |   D   |
| 3.5.3 | Varmista, että koulutusdat lähteet tarkistetaan eheystarkastuksilla ja varmennetaan luotettavista lähteistä dokumentoidun omistajuusketjun avulla ennen niiden käyttöä mallin kehityksessä.                                    |  1   |  D/V  |
| 3.5.4 | Varmista, että mallin kehityksen artefaktit (hyperparametrit, koulutusskriptit, kokoonpanotiedostot) tallennetaan versiohallintaan ja vaativat vertaisarvioinnin hyväksynnän ennen käyttöönottoa koulutuksessa.                |  2   |   D   |

---

## C3.6 Mallin käytöstäpoisto ja poistaminen käytöstä

Mallit on poistettava käytöstä turvallisesti, kun niitä ei enää tarvita tai kun turvallisuusongelmia havaitaan.

|   #   | Kuvaus                                                                                                                                                                                                                                               | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.6.1 | Varmista, että mallin käytöstäpoistoprosessit skannaavat automaattisesti riippuvuuskartat, tunnistavat kaikki kuluttavat järjestelmät ja tarjoavat ennalta sovitut ennakkoilmoitusajat ennen käytöstä poistamista.                                   |  1   |   D   |
| 3.6.2 | Varmista, että eläkkeelle jääneet mallien tiedostot pyyhitään turvallisesti kryptografisella tuhoamisella tai monikertaisella ylikirjoituksella dokumentoitujen tietojen säilytyskäytäntöjen mukaisesti, ja että tuhoamistodistukset on varmennettu. |  1   |  D/V  |
| 3.6.3 | Varmista, että mallin poistotapahtumat kirjataan aikaleiman ja toimijan tunnistetiedon kanssa, sekä että mallin allekirjoitukset peruutetaan uudelleenkäytön estämiseksi.                                                                            |  2   |   V   |
| 3.6.4 | Varmista, että hätätilan mallin poistaminen käytöstä voi estää mallin pääsyn ennalta määritettyjen hätätilan vasteaikojen puitteissa automatisoitujen pysäytyskytkinten avulla, jos kriittisiä tietoturva-aukkoja havaitaan.                         |  2   |  D/V  |

---

## Viitteet

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

