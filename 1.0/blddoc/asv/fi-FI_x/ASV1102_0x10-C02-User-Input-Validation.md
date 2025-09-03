# C2 Käyttäjän syötteen validointi

## Kontrollitavoite

Käyttäjän syötteen vankka validointi on AI-järjestelmiin kohdistuvien tuhoisimpien hyökkäysten ensisijainen puolustus. Kehoite-injektiohyökkäykset voivat ohittaa järjestelmän ohjeet, paljastaa arkaluonteista dataa, tai ohjata mallin käyttäytymistä kohti sallimattomia toimintoja. Jos käytössä ei ole erillisiä suodattimia ja ohjehierarkioita, tutkimukset osoittavat, että 'multi-shot' jailbreak-hyökkäykset, jotka hyödyntävät erittäin pitkiä kontekstikehyksiä, ovat tehokkaita. Myös hienovaraiset vastahyökkäys-perturbaatiohyökkäykset--kuten homoglyph-vaihdot tai leetspeak—-voivat hiljaisesti muuttaa mallin päätöksiä.

---

## C2.1 Kehotteen injektio torjunta

Kehotusinjektio on yksi tekoälyjärjestelmien suurimmista riskeistä. Tämän taktiikan vastatoimet hyödyntävät yhdistelmää staattisia kuviofilttereita, dynaamisia luokittelijoita sekä ohjeiden hierarkian täytäntöönpanoa.

|   #   | Kuvaus                                                                                                                                                                                                                                                                      | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.1.1 | Varmista, että käyttäjän syötteet seulotaan jatkuvasti päivitetyn tunnettujen kehotteen-injektiomallien kirjaston perusteella (jailbreak-avainsanat, "ohita edellinen", roolipeliketjut, epäsuorat HTML-/URL-hyökkäykset).                                                  |  1   |  D/V  |
| 2.1.2 | Varmista, että järjestelmä noudattaa ohjeiden hierarkiaa, jossa järjestelmän tai kehittäjän viestit ohittavat käyttäjän ohjeet, jopa kontekstin ikkunan laajentamisen jälkeen.                                                                                              |  1   |  D/V  |
| 2.1.3 | Varmista, että adversaariset arviointitestit (esim. Punaisen tiimin "many-shot" -kehotteet) ajetaan ennen jokaista mallin tai prompt-pohjan julkaisua, ja että niissä käytetään menestysprosentin kynnysarvoja sekä regressioiden estoon tarkoitetuja automaattisia estoja. |  2   |  D/V  |
| 2.1.4 | Varmista, että kolmannen osapuolen sisällöstä peräisin olevat kehotteet (verkkosivut, PDF-tiedostot, sähköpostit) puhdistetaan eristetyn jäsentelykontekstin sisällä ennen kuin ne liitetään pääkehotteeseen.                                                               |  2   |   D   |
| 2.1.5 | Varmista, että kaikki prompt-suodatussääntöpäivitykset, luokittelumallien versiot ja blokkilistan muutokset ovat versionhallinnassa ja auditoitavissa.                                                                                                                      |  3   |  D/V  |

---

## C2.2 Hyökkäys-esimerkkeihin kohdistuva vastustuskyky

NLP-mallit ovat yhä alttiita hienovaraisiin merkkitasoisiin tai sanatasoisiin perturbatioihin, joita ihmiset usein eivät huomaa, mutta mallit luokittelevat ne virheellisesti.

|   #   | Kuvaus                                                                                                                                                                                                                                      | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.2.1 | Varmista, että perus syötteen normalisoinnin vaiheet (Unicode NFC, homoglyph-kartoitus, välilyöntien trimmaus) suoritetaan ennen tokenisointia.                                                                                             |  1   |   D   |
| 2.2.2 | Varmista, että tilastollinen poikkeavuuksien havaitseminen merkitsee syötteet, joilla on poikkeuksellisen suuri Levenshtein-etäisyys kielen normeihin verrattuna, liiallinen toistuvien tokenien määrä tai poikkeavat upotusten etäisyydet. |  2   |  D/V  |
| 2.2.3 | Varmista, että inferenssiputkisto tukee valinnaisia adversarial-training–hardened mallivariantteja tai suojauskerroksia (esim. satunnaistaminen, puolustusdistillointi) korkean riskin päätepisteille.                                      |  2   |   D   |
| 2.2.4 | Varmista, että epäillyt adversarial-syötteet ovat karanteenissa, ja niistä on kirjattu täydet payloadit (henkilötietojen poistamisen jälkeen).                                                                                              |  2   |   V   |
| 2.2.5 | Varmista, että robustisuusmittarit (tunnettujen hyökkäyskokonaisuuksien menestysprosentti) seurataan ajan mittaan ja regressiot laukaisevat julkaisun eston.                                                                                |  3   |  D/V  |

---

## C2.3 Skeema, Tyyppi- ja Pituuden Validointi

AI-hyökkäykset, joissa on virheellisiä tai ylisuureita syötteitä, voivat aiheuttaa jäsentelyvirheitä, promptin leviämistä kenttien välillä ja resurssien loppumista. Tiukka skeeman noudattaminen on myös edellytys determinististen työkalukutsujen suorittamisessa.

|   #   | Kuvaus                                                                                                                                                                                                       | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 2.3.1 | Varmista, että jokainen API- tai funktiokutsupäätepiste määrittelee selkeän syötteen skeeman (JSON Schema, Protobuf tai multimodaalinen vastine) ja että syötteet validoidaan ennen kehotteen muodostamista. |  1   |   D   |
| 2.3.2 | Varmista, että enimmäistoken- tai tavurajoja ylittävät syötteet hylätään turvallisella virheilmoituksella eikä niitä koskaan katkaista hiljaisesti.                                                          |  1   |  D/V  |
| 2.3.3 | Varmista, että tyyppitarkistukset (esim. numeeriset vaihteluvälit, enum-arvot, MIME-tyypit kuville ja äänitteille) ovat voimassa palvelinpuolella, eivät ainoastaan asiakaspuolen koodissa.                  |  2   |  D/V  |
| 2.3.4 | Varmista, että semanttiset validointityökalut (esim. JSON Schema) toimivat vakioaikaisesti estääkseen algoritmisen DoS-hyökkäyksen.                                                                          |  2   |   D   |
| 2.3.5 | Varmista, että validointivirheet kirjataan sensuroiduilla payload-pätkillä ja yksiselitteisilla virhekodeilla, jotka auttavat turvallisuustriagea.                                                           |  3   |   V   |

---

## C2.4 Sisällön ja käytäntöjen seulonta

Kehittäjien tulisi pystyä havaitsemaan syntaktisesti kelvolliset kehotteet, jotka pyytävät kiellettyä sisältöä (kuten laittomia ohjeita, vihapuhetta ja tekijänoikeudella suojattua tekstiä), ja estämään niiden leviämisen.

|   #   | Kuvaus                                                                                                                                                                                                                                      | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.4.1 | Varmista, että sisällön luokitin (zero-shot tai hienosäädetty) pisteyttää jokaisen syötteen väkivallan, itsemurhan, vihaan liittyvän sisällön, seksuaalisen sisällön ja laittomien pyyntöjen osalta, konfiguroitavien kynnysten mukaisesti. |  1   |   D   |
| 2.4.2 | Varmista, että sääntöjä rikkovat syötteet saavat standardoidut kieltäytymiset tai turvalliset täydennykset, jotta ne eivät päädy myöhempiin LLM-kutsuihin.                                                                                  |  1   |  D/V  |
| 2.4.3 | Varmista, että suodatusmalli tai sääntöjoukko koulutetaan uudelleen tai päivitetään vähintään neljännesvuosittain ottaen mukaan äskettäin havaitut jailbreak- tai politiikan kiertämismallit.                                               |  2   |   D   |
| 2.4.4 | Varmista, että seulonta noudattaa käyttäjäkohtaisia politiikkoja (ikä, alueelliset lailliset rajoitukset) attribuuttiperusteisten sääntöjen kautta, jotka ratkaistaan pyynnön hetkellä.                                                     |  2   |   D   |
| 2.4.5 | Varmista, että suodatuslokit sisältävät luokittelijan luottamusarvot ja politiikan kategorian tunnisteet SOC-korrelaatiota ja tulevaa punaisen tiimin toistoa varten.                                                                       |  3   |   V   |

---

## C2.5 Syötteen nopeusrajoitus ja väärinkäytön ehkäisy

Ohjelmistokehittäjien tulisi estää väärinkäyttöä, resurssien uupumista ja automatisoituja hyökkäyksiä tekoälyjärjestelmiä vastaan rajoittamalla syötteen nopeuksia ja havaitsemalla poikkeavia käyttömalleja.

|   #   | Kuvaus                                                                                                                                                | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.5.1 | Varmista, että käyttäjäkohtaiset, IP-osoitekohtaiset ja API-avaimen mukaan asetetut nopeusrajoitukset ovat voimassa kaikilla syötteen päätepisteillä. |  1   |  D/V  |
| 2.5.2 | Varmista, että burst-rajat ja jatkuvat nopeusrajoitukset on säädetty estämään DoS- ja brute force -hyökkäykset.                                       |  2   |  D/V  |
| 2.5.3 | Varmista, että poikkeavat käyttömallit (esim. nopeasti toistuvia pyyntöjä, syötteen tulva) laukaisevat automaattiset estot tai eskaloinnit.           |  2   |  D/V  |
| 2.5.4 | Varmista, että väärinkäytön ehkäisylokit säilytetään ja niitä tarkastellaan uusien hyökkäyskuvioiden havaitsemiseksi.                                 |  3   |   V   |

---

## C2.6 Monimodaalisen syötteen validointi

Tekoälyjärjestelmien tulisi sisällyttää vankka validointi ei-tekstuaalisille syötteille (kuvat, äänet, tiedostot) estääkseen injektiot, kiertämisen tai resurssien väärinkäytön.

|   #   | Kuvaus                                                                                                                                                  | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.6.1 | Varmista, että kaikki ei-tekstuaaliset syötteet (kuvat, äänitiedostot ja muut tiedostot) validoidaan tyypin, koon ja formaatin mukaan ennen käsittelyä. |  1   |   D   |
| 2.6.2 | Varmista, että tiedostot skannataan haittaohjelmien ja steganografisten hyötykuormien varalta ennen tuontia.                                            |  2   |  D/V  |
| 2.6.3 | Tarkista, että kuva- ja äänisyötteet tarkastetaan adversarial-perturbaatioiden tai tunnettujen hyökkäysmallien varalta.                                 |  2   |  D/V  |
| 2.6.4 | Varmista, että multimodaalisen syötteen validointivirheet kirjataan ja ne laukaisevat hälytykset tutkimusta varten.                                     |  3   |   V   |

---

## C2.7 Syötteen alkuperä ja attribuutio

AI-järjestelmien tulisi tukea auditointia, väärinkäytösten seuraamista ja vaatimustenmukaisuutta valvomalla ja merkitsemällä kaikkien käyttäjien syötteiden alkuperän.

|   #   | Kuvaus                                                                                                                                         | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.7.1 | Varmista, että kaikilla käyttäjäsyötteillä on tuonnin yhteydessä merkitty metatiedot (käyttäjän tunnus, istunto, lähde, aikaleima, IP-osoite). |  1   |  D/V  |
| 2.7.2 | Varmista, että provenance-metatiedot säilyvät ja ovat auditoitavissa kaikille käsitellyille syötteille.                                        |  2   |  D/V  |
| 2.7.3 | Varmista, että poikkeukselliset tai epäluotettavat syötteiden lähteet merkitään ja niihin sovelletaan tiukempaa tarkastelua tai estoa.         |  2   |  D/V  |

---

## C2.8 Reaaliaikainen mukautuva uhkien havaitseminen

Kehittäjien tulisi käyttää kehittyneitä uhkatunnistusjärjestelmiä tekoälyä varten, jotka sopeutuvat uusiin hyökkäysmalleihin ja tarjoavat reaaliaikaisen suojan käännetyllä kuvioetsinnällä.

|   #   | Kuvaus                                                                                                                                                                                          | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.8.1 | Varmista, että uhkien havaitsemisen mallit käännetään optimoituihin regex-moottoreihin, jotta reaaliaikaisessa suodatuksessa saavutetaan korkea suorituskyky ja mahdollisimman pieni viive.     |  1   |  D/V  |
| 2.8.2 | Varmista, että uhkien havaitsemisjärjestelmät pitävät erilliset mallikirjastot eri uhkakategorioille (kehotteen injektio, haitallinen sisältö, herkät tiedot, järjestelmäkomennot).             |  1   |  D/V  |
| 2.8.3 | Varmista, että adaptiivinen uhkien havaitseminen sisältää koneoppimismallit, jotka päivittävät uhkien herkkyystasoa hyökkäysten taajuuden ja menestysasteiden perusteella.                      |  2   |  D/V  |
| 2.8.4 | Varmista, että reaaliaikaiset uhkatiedustelusyötteet päivittävät automaattisesti mallikirjastot uusilla hyökkäystunnisteilla ja IOCs (kompromissin indikaattorit).                              |  2   |  D/V  |
| 2.8.5 | Varmista, että uhkien havaitsemisen vääriä positiivisia osuuksia seurataan jatkuvasti ja mallien spesifisyyttä säädetään automaattisesti, jotta laillisten käyttötapausten häiriöt minimoidaan. |  3   |  D/V  |
| 2.8.6 | Varmista, että kontekstuaalinen uhkianalyysi ottaa huomioon syötteen lähteen, käyttäjän käyttäytymismallit ja istunnon historian, jotta tunnistustarkkuutta voidaan parantaa.                   |  3   |  D/V  |
| 2.8.7 | Varmista, että uhkien havaitsemisen suorituskykymittarit (havaitsemisnopeus, käsittelylatenssi, resurssien käyttö) seurataan ja optimoidaan reaaliajassa.                                       |  3   |  D/V  |

---

## C2.9 Multimodaalinen turvallisuusvalidointiputkisto

Ohjelmistokehittäjien tulisi tarjota turvallisuustarkastus tekoälysyötteille, kuten tekstille, kuville ja äänelle sekä muille vastaaville modaliteeteille, ja käyttää erityyppistä uhkien havaitsemista sekä resurssien eristämistä.

|   #   | Kuvaus                                                                                                                                                                                                                                                                                            | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 2.9.1 | Varmista, että jokaisella syötteen modaalisuudella on omat turvallisuusvalidaattorinsa, joilla on dokumentoidut uhkamallit (teksti: prompt injection, kuvat: steganografia, ääni: spektrogrammihyökkäykset) ja havaitsemiskynnykset.                                                              |  1   |  D/V  |
| 2.9.2 | Varmista, että monimodaaliset syötteet käsitellään eristetyissä hiekkalaatikoissa määritellyillä resurssirajoituksilla (muisti, CPU, käsittelyaika), jotka ovat kullekin modaalisuustyypille ominaisia ja jotka on dokumentoitu turvallisuuspolitiikoissa.                                        |  2   |  D/V  |
| 2.9.3 | Varmista, että ristiinmodaalinen hyökkäysten havaitseminen tunnistaa koordinoituja hyökkäyksiä, jotka ulottuvat useisiin syötteen tyyppeihin (esim. steganografiset payloadit kuvissa sekä tekstissä tehty prompt-injektointi) korrelaatiosääntöjen ja hälytyksen generoinnin avulla.             |  2   |  D/V  |
| 2.9.4 | Varmista, että monimodaalisen validoinnin epäonnistumiset laukaisevat yksityiskohtaisen lokituksen, mukaan lukien kaikki syöttömodaliteetit, validointitulokset, uhkaspisteet ja korrelaatioanalyysi strukturoitujen lokimuotojen avulla SIEM-integraatiota varten.                               |  3   |  D/V  |
| 2.9.5 | Varmista, että modaalisuuspohjaiset sisältöluokittelijat päivitetään dokumentoitujen aikataulujen mukaan (vähintään neljännesvuosittain) uusien uhkamallien ja vastustuskelpoisten esimerkkien sekä suorituskykymittareiden osalta siten, että suorituskyky pysyy baseline-kynnysten yläpuolella. |  3   |  D/V  |

---

## Lähteet

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

