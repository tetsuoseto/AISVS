# C2-käyttäjän syötteen validointi

## Ohjaustavoite

Käyttäjän syötteen vahva validointi on etulinjan puolustuskeino joitakin haitallisimpia hyökkäyksiä vastaan tekoälyjärjestelmiä kohtaan. Kehote-injektiohyökkäykset voivat ohittaa järjestelmäohjeet, vuotaa arkaluonteisia tietoja tai ohjata mallin käyttäytymään sallitsemattomalla tavalla. Ellei erityisiä suodattimia ja ohjehierarkioita ole käytössä, tutkimukset osoittavat, että "multi-shot" jailbreakit, jotka hyödyntävät erittäin pitkiä kontekstiikkunoita, ovat tehokkaita. Myös hienovaraiset vihamieliset häirintäiskut—kuten homoglyph-vaihdot tai leetspeak—voivat hiljaisesti muuttaa mallin päätöksiä.

---

## C2.1 Kehoteinjektion puolustus

Kehotteinjektio on yksi suurimmista riskeistä tekoälyjärjestelmille. Suojautuminen tätä taktiikkaa vastaan käyttää yhdistelmää staattisia mallisuodattimia, dynaamisia luokittelijoita ja ohjeistuksenalaisen hierarkian noudattamisen varmistamista.

|   #   | Kuvaus                                                                                                                                                                                                                                                     | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.1.1 | Varmista, että käyttäjän syötteet tarkistetaan jatkuvasti päivitettyä tunnettujen kehotteiden injektiomallien kirjastoa vastaan (jailbreak-avainsanat, "ignore previous" -komennot, roolipeliketjut, epäsuorat HTML-/URL-hyökkäykset).                     |  1   |  D/V  |
| 2.1.2 | Varmista, että järjestelmä noudattaa ohjeiden hierarkiaa, jossa järjestelmän tai kehittäjän viestit ohittavat käyttäjän ohjeet, myös kontekstikehyksen laajentamisen jälkeen.                                                                              |  1   |  D/V  |
| 2.1.3 | Varmista, että vastustava arviointi (esim. Red Teamin "many-shot" -kehotteet) suoritetaan ennen jokaista mallin tai kehotepohjan julkaisua, asetettujen onnistumisprosenttirajojen ja automaattisten takaisinkytkentäestojen kanssa regressioiden varalta. |  2   |  D/V  |
| 2.1.4 | Varmista, että kolmannen osapuolen sisällöstä (verkkosivut, PDF:t, sähköpostit) peräisin olevat kehotteet puhdistetaan eristetyssä jäsentämiskontekstissa ennen niiden liittämistä pääkehotteeseen.                                                        |  2   |   D   |
| 2.1.5 | Varmista, että kaikki kehotteen suodatussääntöjen päivitykset, luokittelijamalliversiot ja estolistamuutokset ovat versiohallinnassa ja auditoitavissa.                                                                                                    |  3   |  D/V  |

---

## C2.2 Vastustuskyky vihamielisille esimerkeille

Luonnollisen kielen käsittelyn (NLP) mallit ovat edelleen alttiita hienovaraisille merkki- tai sanatasoisille häiriöille, jotka ihmiset usein ohittavat, mutta joiden mallien luokittelu menee yleensä vikaan.

|   #   | Kuvaus                                                                                                                                                                                                             | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 2.2.1 | Varmista, että perus syötteen normalisointivaiheet (Unicode NFC, homoglyph-kartoitus, välilyöntien poistaminen) suoritetaan ennen tokenisointia.                                                                   |  1   |   D   |
| 2.2.2 | Varmista, että tilastollinen poikkeamien havaitseminen tunnistaa syötteet, joilla on epätavallisen suuri muokkausetäisyys kielinormeihin nähden, liiallisesti toistuvia tokeneita tai epänormaaleja upotusmatkoja. |  2   |  D/V  |
| 2.2.3 | Varmista, että päättelyputki tukee valinnaisia vastahyökkäyskoulutuksella vahvistettuja mallivariantteja tai puolustuskerroksia (esim. satunnaistus, puolustava tislaus) korkean riskin päätepisteille.            |  2   |   D   |
| 2.2.4 | Varmista, että epäillyt vihamieliset syötteet eristetään karanteeniin ja kirjataan täydellisten tietosisältöjen kanssa (henkilötietojen peittämisen jälkeen).                                                      |  2   |   V   |
| 2.2.5 | Varmista, että jäykkyysmittarit (tunnettujen hyökkäyspakettien onnistumisprosentti) seurataan ajan myötä ja että taantumat aiheuttavat julkaisun eston.                                                            |  3   |  D/V  |

---

## C2.3 Skeeman, tyypin ja pituuden validointi

AI-hyökkäykset, jotka sisältävät virheellisiä tai liian suuria syötteitä, voivat aiheuttaa jäsentämisvirheitä, kehotepuolilta tapahtuvaa vuotoa ja resurssien loppumista. Tiukka skeeman valvonta on myös edellytys determinististen työkalukutsujen suorittamiselle.

|   #   | Kuvaus                                                                                                                                                                                                              | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.3.1 | Varmista, että jokainen API- tai funktiokutsun päätepiste määrittelee eksplisiittisen syötteen skeeman (JSON Schema, Protobuf tai multimodaalinen vastine) ja että syötteet validoidaan ennen kehotteen kokoamista. |  1   |   D   |
| 2.3.2 | Varmista, että syötteet, jotka ylittävät enimmäismäärän sanoja tai tavuja, hylätään turvallisella virheilmoituksella eivätkä koskaan katkaistu hiljaisesti.                                                         |  1   |  D/V  |
| 2.3.3 | Varmista, että tyyppitarkistukset (esim. numeeriset arvovälit, enum-arvot, MIME-tyypit kuville/äänille) tehdään palvelinpuolella, eikä ainoastaan asiakasohjelmakoodissa.                                           |  2   |  D/V  |
| 2.3.4 | Varmista, että semanttiset validoijat (esim. JSON Schema) suoritetaan vakioaikaisesti estääkseen algoritmisen DoS-hyökkäyksen.                                                                                      |  2   |   D   |
| 2.3.5 | Varmista, että validointivirheet kirjataan sensuroiduin tietosisällön osin ja yksiselitteisin virhekoodin, jotta turvallisuuden käsittelyä voidaan helpottaa.                                                       |  3   |   V   |

---

## C2.4 Sisällön ja politiikan tarkastus

Kehittäjien tulisi pystyä havaitsemaan syntaktisesti kelvolliset kehotteet, jotka pyytävät kiellettyä sisältöä (kuten laittomia ohjeita, vihapuhetta ja tekijänoikeudella suojattua tekstiä), ja estämään niiden leviämisen.

|   #   | Kuvaus                                                                                                                                                                                                                                   | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.4.1 | Varmista, että sisältöluokittelija (zero shot tai hienosäädetty) arvioi jokaisen syötteen väkivallan, itseen kohdistuvan vahingon, vihan, seksuaalisen sisällön ja laittomat pyynnöt osalta, ja että kynnysarvot ovat konfiguroitavissa. |  1   |   D   |
| 2.4.2 | Varmista, että politiikkoja rikkovat syötteet saavat standardoidut kieltäytymiset tai turvalliset täydennykset, jotta ne eivät siirry alempiin LLM-kutsuihin.                                                                            |  1   |  D/V  |
| 2.4.3 | Varmista, että seulontamalli tai sääntöjoukko koulutetaan uudelleen/päivitetään vähintään neljännesvuosittain, ottaen huomioon äskettäin havaitut jailbreikkaus- tai politiikan kiertämismallit.                                         |  2   |   D   |
| 2.4.4 | Varmista, että seulonta noudattaa käyttäjäkohtaisia politiikkoja (ikä, alueelliset lailliset rajoitukset) käyttöön perustuvien sääntöjen avulla, jotka ratkaistaan pyyntöhetkellä.                                                       |  2   |   D   |
| 2.4.5 | Varmista, että seulontalokit sisältävät luokittelijan luottamuspisteet ja politiikkakategorian tunnisteet SOC:n korrelaatiota ja tulevaa red-teamin uudelleensoitantoa varten.                                                           |  3   |   V   |

---

## C2.5 Syötteen nopeuden rajoittaminen ja väärinkäytön estäminen

Kehittäjien tulisi estää väärinkäytökset, resurssien loppuminen ja automatisoidut hyökkäykset tekoälyjärjestelmiä vastaan rajoittamalla syötteiden määrää ja havaitsemalla poikkeavat käyttökuviot.

|   #   | Kuvaus                                                                                                                                          | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.5.1 | Varmista, että käyttäjäkohtaiset, IP-osoitekohtaiset ja API-avainkohtaiset nopeusrajoitukset toteutetaan kaikilla syöttöpisteillä.              |  1   |  D/V  |
| 2.5.2 | Varmista, että huippu- ja jatkuvat nopeusrajat on säädetty estämään palvelunestohyökkäykset (DoS) ja brutaalivoimahyökkäykset.                  |  2   |  D/V  |
| 2.5.3 | Varmista, että poikkeavat käyttötavat (esim. nopealla tahdilla tehdyt pyynnöt, syötteen tulva) laukaisevat automaattiset estot tai eskaloinnit. |  2   |  D/V  |
| 2.5.4 | Varmista, että väärinkäytösten ehkäisyn lokit säilytetään ja tarkastetaan uusien hyökkäyskuvioiden varalta.                                     |  3   |   V   |

---

## C2.6 Monimodaalinen syötteen validointi

AI-järjestelmien tulisi sisältää vahva validointi tekstin ulkopuolisille syötteille (kuvat, ääni, tiedostot) estääkseen injektion, kiertämisen tai resurssien väärinkäytön.

|   #   | Kuvaus                                                                                                                                   | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.6.1 | Varmista, että kaikki ei-tekstimuotoiset syötteet (kuvat, äänet, tiedostot) tarkistetaan tyypin, koon ja muodon osalta ennen käsittelyä. |  1   |   D   |
| 2.6.2 | Varmista, että tiedostot tarkistetaan haittaohjelmien ja steganografisten hyötykuormien varalta ennen syöttämistä.                       |  2   |  D/V  |
| 2.6.3 | Varmista, että kuva-/äänianturit tarkistetaan vihamielisten häiriöiden tai tunnettujen hyökkäysmallien varalta.                          |  2   |  D/V  |
| 2.6.4 | Varmista, että monimuotoisten syötteiden validointivirheet kirjataan ja laukaisevat hälytykset tutkintaa varten.                         |  3   |   V   |

---

## C2.7 Syötteen alkuperä ja lähdeviittaus

AI-järjestelmien tulisi tukea tarkastuksia, väärinkäytösten seurantaa ja sääntöjen noudattamista seuraamalla ja merkitsemällä kaikkien käyttäjien syötteiden alkuperät.

|   #   | Kuvaus                                                                                                                                                         | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.7.1 | Varmista, että kaikki käyttäjien syötteet merkitään metatiedoilla (käyttäjätunnus, istunto, lähde, aikaleima, IP-osoite) syötteen vastaanottamisen yhteydessä. |  1   |  D/V  |
| 2.7.2 | Varmista, että alkuperätiedot säilyvät ja ovat tarkastettavissa kaikille käsitellyille syötteille.                                                             |  2   |  D/V  |
| 2.7.3 | Varmista, että poikkeavat tai epäluotettavat syöttölähteet tunnistetaan ja niitä kohdennetaan tehostetulla valvonnalla tai estetään.                           |  2   |  D/V  |

---

## C2.8 Reaaliaikainen adaptiivinen uhkien havaitseminen

Kehittäjien tulisi käyttää kehittyneitä uhkien tunnistusjärjestelmiä tekoälylle, jotka sopeutuvat uusiin hyökkäysmalleihin ja tarjoavat reaaliaikaista suojaa koottuun mallien tunnistukseen perustuen.

|   #   | Kuvaus                                                                                                                                                                                      | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.8.1 | Varmista, että uhkien tunnistusmallit on käännetty optimoiduiksi regex-moottoreiksi korkeaa suorituskykyä varten reaaliaikaiseen suodatukseen, jossa viivevaikutus on minimaalinen.         |  1   |  D/V  |
| 2.8.2 | Varmista, että uhkien tunnistusjärjestelmät ylläpitävät erillisiä mallikirjastoja eri uhkakategorioille (kehotusinjektio, haitallinen sisältö, arkaluonteiset tiedot, järjestelmäkomennot). |  1   |  D/V  |
| 2.8.3 | Varmista, että adaptatiivinen uhkien havaitseminen sisältää koneoppimismallit, jotka päivittävät uhan herkkyyttä hyökkäysten esiintymistiheyden ja onnistumisprosenttien perusteella.       |  2   |  D/V  |
| 2.8.4 | Varmista, että reaaliaikaiset uhkatiedon syötteet päivittävät automaattisesti mallikirjastoja uusilla hyökkäysallekirjoituksilla ja IOC:illa (kompromissin indikaattorit).                  |  2   |  D/V  |
| 2.8.5 | Varmista, että uhkien tunnistuksen väärien positiivisten määrät seurataan jatkuvasti ja mallin spesifisyyttä säädetään automaattisesti minimoimaan laillisten käyttötapausten häiriöt.      |  3   |  D/V  |
| 2.8.6 | Varmista, että kontekstuaalinen uhka-analyysi ottaa huomioon syötteen lähteen, käyttäytymismallit ja istunnon historian parantaakseen tunnistuksen tarkkuutta.                              |  3   |  D/V  |
| 2.8.7 | Varmista, että uhkien havaitsemisen suorituskykymittarit (havaintataajuus, käsittelyviive, resurssien käyttö) seurataan ja optimoidaan reaaliajassa.                                        |  3   |  D/V  |

---

## C2.9 Monimodaalinen turvallisuuden validointiputki

Kehittäjien tulisi tarjota turvallisuusvarmennus tekstille, kuvalle, äänelle ja muille tekoälyn syötemodaaliteeteille käyttämällä erityyppistä uhkien havaitsemista ja resurssien eristämistä.

|   #   | Kuvaus                                                                                                                                                                                                                                                                       | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.9.1 | Varmista, että jokaisella syötemodaliteetilla on omistautuneet turvallisuustarkastajat, joilla on dokumentoidut uhkamallit (teksti: kehotteen injektio, kuvat: steganografia, ääni: spektrogrammihyökkäykset) ja havaitsemiskynnykset.                                       |  1   |  D/V  |
| 2.9.2 | Varmista, että monimuotoiset syötteet käsitellään eristetyissä hiekkalaatikoissa, joissa on määritellyt resurssirajoitukset (muisti, suorittimen käyttö, käsittelyaika) kullekin modaliteettityypille erikseen ja jotka on dokumentoitu turvallisuuspolitiikoissa.           |  2   |  D/V  |
| 2.9.3 | Varmista, että ristimodaalinen hyökkäyksen tunnistus havaitsee koordinoidut hyökkäykset, jotka kattavat useita syötetyyppejä (esim. steganografiset kuormitukset kuvissa yhdistettynä kehotteen injektioon tekstissä) korrelaatiosääntöjen ja hälytyksen generoinnin avulla. |  2   |  D/V  |
| 2.9.4 | Varmista, että monimuotoisen validoinnin epäonnistumiset laukaisevat yksityiskohtaisen lokituksen, joka sisältää kaikki syötemodaalit, validointitulokset, uhkapisteet ja korrelaatioanalyysin rakenteellisissa lokimuodoissa SIEM-integraatiota varten.                     |  3   |  D/V  |
| 2.9.5 | Varmista, että modality-kohtaiset sisältöluokittelijat päivitetään dokumentoitujen aikataulujen mukaisesti (vähintään neljännesvuosittain) uusilla uhkamalleilla, vihamielisillä esimerkeillä ja suorituskykymittareilla, jotka pidetään perustasojen yläpuolella.           |  3   |  D/V  |

---

## Viitteet

* [LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security](https://genai.owasp.org/llmrisk/llm01-prompt-injection/)
* [Generative AI's Biggest Security Flaw Is Not Easy to Fix](https://www.wired.com/story/generative-ai-prompt-injection-hacking)
* [Many-shot jailbreaking \ Anthropic](https://www.anthropic.com/research/many-shot-jailbreaking)
* [$PDF$ OpenAI GPT-4.5 System Card](https://cdn.openai.com/gpt-4-5-system-card-2272025.pdf)
* [Notebook for the CheckThat Lab at CLEF 2024](https://ceur-ws.org/Vol-3740/paper-53.pdf)
* [Mitigate jailbreaks and prompt injections – Anthropic](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks)
* [Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis](https://ama.drwhy.ai/mitre-attck.html)
* [OWASP Top 10 for LLM Applications 2025 – WorldTech IT](https://wtit.com/blog/2025/04/17/owasp-top-10-for-llm-applications-2025/)
* [OWASP Machine Learning Security Top Ten](https://owasp.org/www-project-machine-learning-security-top-10/)
* [Few words about AI Security – Jussi Metso](https://www.jussimetso.com/index.php/2024/09/28/few-words-about-ai-security/)
* [How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry](https://modelmetry.com/blog/how-to-ensure-llm-output-adheres-to-a-json-schema)
* [Easily enforcing valid JSON schema following – API](https://community.openai.com/t/feature-request-function-calling-easily-enforcing-valid-json-schema-following/263515?utm_source)
* [AI Safety + Cybersecurity R\&D Tracker – Fairly AI](https://www.fairly.ai/blog/ai-cybersecurity-tracker)
* [Anthropic makes 'jailbreak' advance to stop AI models producing harmful results](https://www.ft.com/content/cf11ebd8-aa0b-4ed4-945b-a5d4401d186e)
* [Pattern matching filter rules - IBM](https://www.ibm.com/docs/ssw_aix_71/security/intrusion_pattern_matching_filter_rules.html)
* [Real-time Threat Detection](https://www.darktrace.com/cyber-ai-glossary/real-time-threat-detection)

