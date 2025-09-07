# C4-infrastruktuuri, konfigurointi ja käyttöönoton turvallisuus

## Ohjaustavoite

Tekoälyn infrastruktuuri on kovennettava etuoikeuksien eskalaatiota, toimitusketjun manipulointia ja sivuttaisliikettä vastaan turvallisen konfiguraation, suoritusajan eristyksen, luotettavien käyttöönotto-putkien ja kattavan valvonnan avulla. Vain valtuutetut, validoidut infrastruktuurin komponentit ja konfiguraatiot pääsevät tuotantoon hallittujen prosessien kautta, jotka ylläpitävät turvallisuutta, eheyttä ja tarkastettavuutta.

Keskeinen turvallisuustavoite: Vain kryptografisesti allekirjoitetut, haavoittuvuusskannatut infrastruktuurikomponentit pääsevät tuotantoon automatisoitujen validointiputkien kautta, jotka valvovat turvallisuuspolitiikkojen noudattamista ja ylläpitävät muuttumattomia tarkastuslokeja.

---

## C4.1 Suoritusympäristön eristäminen

Estä kontin karkailu ja oikeuksien korotus ydin-tason eristysprimitiivien ja pakollisten pääsynvalvontojen avulla.

|   #   | Kuvaus                                                                                                                                                                                                                                   | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.1.1 | Varmista, että kaikista tekoälysäiliöistä poistetaan KAIKKI Linuxin oikeudet paitsi CAP_SETUID, CAP_SETGID sekä turvallisuusperustasoissa eksplisiittisesti vaaditut oikeudet.                                                           |  1   |  D/V  |
| 4.1.2 | Varmista, että seccomp-profiilit estävät kaikki järjestelmäkutsut poistamalla ne, jotka eivät ole ennakkoon hyväksytyissä sallituissa listoissa, ja että rikkomukset aiheuttavat kontin päättymisen ja tuottavat turvallisuushälytyksiä. |  1   |  D/V  |
| 4.1.3 | Varmista, että tekoälykuormitukset suoritetaan vain-luku -juurijärjestelmillä, tmpfs-väliaikaiselle datalle ja nimetyillä tilavuuksilla pysyvälle datalle siten, että noexec-liitoksen asetukset ovat käytössä.                          |  2   |  D/V  |
| 4.1.4 | Varmista, että eBPF-pohjainen suoritusmonitorointi (Falco, Tetragon tai vastaava) havaitsee oikeuksien korotuspyrkimykset ja lopettaa automaattisesti rikkomukseen syyllistyvät prosessit organisaation vasteaikavaatimusten mukaisesti. |  2   |  D/V  |
| 4.1.5 | Varmista, että korkean riskin tekoälykuormitukset suoritetaan laitteistollisesti eristetyissä ympäristöissä (Intel TXT, AMD SVM tai omistetut bare-metal-solmut) ja että suoritetaan todennusvahvistus.                                  |  3   |  D/V  |

---

## C4.2 Turvalliset rakennus- ja käyttöönotto-putket

Varmista kryptografinen eheys ja toimitusketjun turvallisuus toistettavien rakennusten ja allekirjoitettujen artefaktien avulla.

|   #   | Kuvaus                                                                                                                                                                                                             | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.2.1 | Varmista, että infrastruktuuri-koodina tarkastetaan työkaluilla (tfsec, Checkov tai Terrascan) jokaisessa commitissa, estäen yhdistämiset kriittisillä tai korkealla vakavuudella löytyvien virheiden tapauksessa. |  1   |  D/V  |
| 4.2.2 | Varmista, että konttirakennukset ovat toistettavissa identtisillä SHA256-tiivisteillä eri rakennuskertojen välillä ja luo Sigstorella allekirjoitetut SLSA-tason 3 alkuperätodistukset.                            |  1   |  D/V  |
| 4.2.3 | Varmista, että konttikuvat sisältävät CycloneDX- tai SPDX-SBOM-tiedostot ja ne on allekirjoitettu Cosignilla ennen rekisteriin työnnön tekemistä, ja että allekirjoittamattomat kuvat hylätään käyttöönotossa.     |  2   |  D/V  |
| 4.2.4 | Varmista, että CI/CD-putket käyttävät OIDC-tokeneita HashiCorp Vaultista, AWS IAM -rooleista tai Azure Managed Identityistä, joiden voimassaoloaika ei ylitä organisaation tietoturvakäytännön rajoja.             |  2   |  D/V  |
| 4.2.5 | Varmista, että Cosign-allekirjoitukset ja SLSA-lähdetiedot validoidaan käyttöönoton aikana ennen kontin suorittamista, ja että vahvistusvirheet aiheuttavat käyttöönoton epäonnistumisen.                          |  2   |  D/V  |
| 4.2.6 | Varmista, että rakennusympäristöt toimivat katoavissa säiliöissä tai virtuaalikoneissa ilman pysyvää tallennustilaa ja verkkoeristettyinä tuotantoympäristöjen VPC-verkostoista.                                   |  2   |  D/V  |

---

## C4.3 Verkkoturva ja käyttöoikeuksien hallinta

Ota käyttöön zero-trust-verkotus oletuskieltopolitiikoilla ja salatuilla viestinnöillä.

|   #   | Kuvaus                                                                                                                                                                                                                               | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.3.1 | Varmista, että Kubernetes NetworkPolicies tai vastaava toteuttaa oletuksena estävän saapuvan/lähtevän liikenteen säännön, jossa sallitaan nimenomaisesti vaaditut portit (443, 8080 jne.).                                           |  1   |  D/V  |
| 4.3.2 | Varmista, että SSH (portti 22), RDP (portti 3389) ja pilven metatietopäätepisteet (169.254.169.254) ovat estettyjä tai vaativat sertifikaattiin perustuvan todennuksen.                                                              |  1   |  D/V  |
| 4.3.3 | Varmista, että ulospäin suuntautuva liikenne suodatetaan HTTP/HTTPS-välityspalvelimien (Squid, Istio tai pilvi-NAT-porttien) kautta käyttämällä sallittujen verkkotunnusten luetteloita, ja estetyt pyynnöt kirjataan.               |  2   |  D/V  |
| 4.3.4 | Varmista, että palveluiden välinen viestintä käyttää keskinäistä TLS-yhteyttä, jossa sertifikaatit kierrätetään organisaation käytännön mukaisesti ja sertifikaattien validointi on pakollinen (ei ohitus- tai skip-verify-lippuja). |  2   |  D/V  |
| 4.3.5 | Varmista, että tekoälyinfrastruktuuri toimii omistetuissa VPC:issä/VNet:issä ilman suoraa internet-yhteyttä ja kommunikoi ainoastaan NAT-porttien tai bastion-palvelimien kautta.                                                    |  2   |  D/V  |

---

## C4.4 Salaisuuksien ja kryptografisten avainten hallinta

Suojaa tunnistetiedot laitteistopohjaisella tallennuksella ja automatisoidulla kierrätyksellä nollas luottamuksen pääsystä.

|   #   | Kuvaus                                                                                                                                                                                                            | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.4.1 | Varmista, että salaisuudet tallennetaan HashiCorp Vaultiin, AWS Secrets Manageriin, Azure Key Vaultiin tai Google Secret Manageriin käyttäen levossa olevaa AES-256-salausta.                                     |  1   |  D/V  |
| 4.4.2 | Varmista, että kryptografiset avaimet generoidaan FIPS 140-2 Tason 2 HSM-laitteissa (AWS CloudHSM, Azure Dedicated HSM) ja että avainten vaihtaminen tapahtuu organisaation kryptografisen politiikan mukaisesti. |  1   |  D/V  |
| 4.4.3 | Varmista, että salaisuuksien kierto on automatisoitu ilman käyttökatkoksia toteutetun käyttöönoton yhteydessä ja että kierto käynnistyy välittömästi henkilöstömuutosten tai turvallisuustapahtumien seurauksena. |  2   |  D/V  |
| 4.4.4 | Varmista, että säiliökuvat skannataan työkaluilla (GitLeaks, TruffleHog tai detect-secrets), jotka estävät rakentamisen, jos ne sisältävät API-avaimia, salasanoja tai sertifikaatteja.                           |  2   |  D/V  |
| 4.4.5 | Varmista, että tuotannon salaisen pääsyn edellyttää MFA:ta laitteistotunnisteilla (YubiKey, FIDO2) ja että se kirjataan muuttumattomiin auditointilokeihin käyttäjätunnuksineen ja aikaleimoineen.                |  2   |  D/V  |
| 4.4.6 | Varmista, että salaisuudet injektoidaan Kubernetes-salasanojen, liitettyjen tallennustilojen tai init-konttien kautta, ja varmista, ettei salaisuuksia koskaan upoteta ympäristömuuttujiin tai kuviin.            |  2   |  D/V  |

---

## C4.5 AI Työkuorman eristys ja validointi

Eristä epäluotettavat tekoälymallit turvallisiin hiekkalaatikoihin kattavalla käyttäytymisanalyysillä.

|   #   | Kuvaus                                                                                                                                                                                                                                | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.5.1 | Varmista, että ulkoiset tekoälymallit suoritetaan gVisorissa, microVM:issä (kuten Firecracker, CrossVM) tai Docker-konteissa käyttäen --security-opt=no-new-privileges ja --read-only -lippuja.                                       |  1   |  D/V  |
| 4.5.2 | Varmista, että hiekkalaatikkoympäristöillä ei ole verkkoyhteyttä (--network=none) tai niillä on vain localhost-yhteys, ja kaikki ulkoiset pyynnöt estetään iptables-säännöillä.                                                       |  1   |  D/V  |
| 4.5.3 | Varmista, että tekoälymallin validointi sisältää automatisoidun red-tiimin testaamisen organisaation määrittelemällä testikattavuudella ja käyttäytymisanalyysillä takaporttien havaitsemiseksi.                                      |  2   |  D/V  |
| 4.5.4 | Varmista, että ennen kuin tekoälymalli otetaan tuotantokäyttöön, sen hiekkalaatikkotulokset allekirjoitetaan kryptografisesti valtuutettujen turvallisuushenkilöiden toimesta ja tallennetaan muuttumattomiin tarkastuslokikirjoihin. |  2   |  D/V  |
| 4.5.5 | Varmista, että hiekkalaatikkoympäristöt tuhotaan ja luodaan uudelleen kultakuvista arviointien välillä täydellisellä tiedostojärjestelmän ja muistin puhdistuksella.                                                                  |  2   |  D/V  |

---

## C4.6 Infrastruktuurin turvallisuuden valvonta

Jatkuvasti skannaa ja valvo infrastruktuuria automatisoidulla korjauksella ja reaaliaikaisella hälytyksellä.

|   #   | Kuvaus                                                                                                                                                                                                                | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.6.1 | Varmista, että säilökuvat tarkastetaan organisaation aikataulujen mukaisesti siten, että KRIITTISEN tason haavoittuvuudet estävät käyttöönoton organisaation riskikynnysten perusteella.                              |  1   |  D/V  |
| 4.6.2 | Varmista, että infrastruktuuri täyttää CIS Benchmarkit tai NIST 800-53 -ohjaimet organisaation määrittämillä vaatimustenmukaisuusrajoilla ja automatisoidulla korjauksella epäonnistuneisiin tarkastuksiin.           |  1   |  D/V  |
| 4.6.3 | Varmista, että KORKEAN vakavuuden haavoittuvuudet on korjattu organisaation riskienhallinnan aikataulujen mukaisesti, ja että käytössä on hätämenettelyt aktiivisesti hyödynnettyjen CVE-tietoturva-aukkojen varalta. |  2   |  D/V  |
| 4.6.4 | Varmista, että turvallisuushälytykset integroituvat SIEM-alustoihin (Splunk, Elastic tai Sentinel) käyttäen CEF- tai STIX/TAXII-muotoja automaattisen rikastamisen kanssa.                                            |  2   |   V   |
| 4.6.5 | Varmista, että infrastruktuurin mittarit viedään valvontajärjestelmiin (Prometheus, DataDog) SLA-hallintapaneeleilla ja johdon raportoinnilla.                                                                        |  3   |   V   |
| 4.6.6 | Varmista, että konfiguraation poikkeamat havaitaan työkalujen (Chef InSpec, AWS Config) avulla organisaation valvontavaatimusten mukaisesti, ja että luvattomille muutoksille on automaattinen palautus.              |  2   |  D/V  |

---

## C4.7 AI-infrastruktuurin resurssien hallinta

Estä resurssien loppumiseen tähtäävät hyökkäykset ja varmista resurssien oikeudenmukainen jakaminen kiintiöiden ja valvonnan avulla.

|   #   | Kuvaus                                                                                                                                                                                                                                       | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.7.1 | Varmista, että GPU/TPU:n käyttöastetta valvotaan ja organisaation määrittelemissä kynnysarvoissa käynnistetään hälytykset sekä kapasiteetin hallintakäytäntöjen perusteella otetaan käyttöön automaattinen skaalaus tai kuormantasapainotus. |  1   |  D/V  |
| 4.7.2 | Varmista, että tekoälyn kuormitusmittarit (päätelmän viive, läpimenonopeus, virheprosentit) kerätään organisaation valvontavaatimusten mukaisesti ja ne korreloidaan infrastruktuurin käytön kanssa.                                         |  1   |  D/V  |
| 4.7.3 | Varmista, että Kubernetes ResourceQuotas tai vastaavat rajoittavat yksittäisiä työkuormia organisaation resurssien allokointipolitiikkojen mukaisesti, ja että tiukat rajat pannaan täytäntöön.                                              |  2   |  D/V  |
| 4.7.4 | Varmista, että kustannusseuranta seuraa kulutusta työkuormittain/vuokralaisittain, sisältäen hälytykset organisaation budjettirajojen perusteella sekä automatisoidut valvontamekanismit budjetin ylitysten estämiseksi.                     |  2   |   V   |
| 4.7.5 | Varmista, että kapasiteetin suunnittelu käyttää historiallista dataa organisaation määrittelemillä ennustejaksoilla ja automatisoitua resurssien käyttöönottoa kysyntämallien perusteella.                                                   |  3   |   V   |
| 4.7.6 | Varmista, että resurssien ehtyminen laukaisee piirikytkimet organisaation vastausvaatimusten mukaisesti, mukaan lukien kapasiteettipolitiikkoihin perustuva nopeusrajoitus ja työkuorman eristäminen.                                        |  2   |  D/V  |

---

## C4.8 Ympäristön erottelu ja siirron valvonta

Toteuta tiukat ympäristörajat automaattisilla siirtoluvuilla ja turvallisuuden validoinnilla.

|   #   | Kuvaus                                                                                                                                                                                                       | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.8.1 | Varmista, että kehitys/testi/tuotantoympäristöt toimivat erillisissä VPC:issä/VNet:eissä ilman yhteisiä IAM-rooleja, suojausryhmiä tai verkkoyhteyksiä.                                                      |  1   |  D/V  |
| 4.8.2 | Varmista, että ympäristön edistäminen vaatii organisaation määrittelemien valtuutettujen henkilöiden hyväksynnän, joka tapahtuu kryptografisilla allekirjoituksilla ja muuttumattomilla auditointijäljillä.  |  1   |  D/V  |
| 4.8.3 | Tarkista, että tuotantoympäristöt estävät SSH-yhteydet, poistavat käytöstä debug-rajapinnat ja edellyttävät muutospyyntöjä organisaation etukäteisilmoitusvaatimuksineen paitsi hätätilanteissa.             |  2   |  D/V  |
| 4.8.4 | Varmista, että infrastruktuuri-koodina -muutokset vaativat vertaisarvioinnin automatisoidun testauksen ja tietoturvatarkastuksen kanssa ennen yhdistämistä päähaaraan.                                       |  2   |  D/V  |
| 4.8.5 | Varmista, että tuotannon ulkopuoliset tiedot on anonymisoitu organisaation tietosuojavaatimusten mukaisesti, synteettinen datan luonti tai täydellinen datan peittäminen henkilötietojen poisto varmennettu. |  2   |  D/V  |
| 4.8.6 | Varmista, että promootiportit sisältävät automatisoidut turvallisuustestaukset (SAST, DAST, konttien skannaus) ja hyväksyntää varten vaaditaan nolla KRIITTISTÄ löydöstä.                                    |  2   |  D/V  |

---

## C4.9 Infrastruktuurin varmuuskopiointi ja palautus

Varmista infrastruktuurin kestävyys automatisoitujen varmuuskopioiden, testattujen palautusmenetelmien ja katastrofipalautusominaisuuksien avulla.

|   #   | Kuvaus                                                                                                                                                                                                                 | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.9.1 | Varmista, että infrastruktuurin kokoonpanot varmuuskopioidaan organisaation varmuuskopiointiaikataulujen mukaisesti maantieteellisesti erillisiin alueisiin 3-2-1-varmuuskopiointistrategian toteuttamisen mukaisesti. |  1   |  D/V  |
| 4.9.2 | Varmista, että varmistusjärjestelmät toimivat eristetyissä verkoissa erillisillä tunnistetiedoilla ja ilmakidennetyllä tallennustilalla kiristyshaittaohjelmilta suojautumiseksi.                                      |  2   |  D/V  |
| 4.9.3 | Varmista, että palautusmenettelyt testataan ja validoidaan automatisoidun testauksen avulla organisaation aikataulujen mukaisesti siten, että RTO- ja RPO-tavoitteet täyttävät organisaation vaatimukset.              |  2   |   V   |
| 4.9.4 | Varmista, että katastrofipalautus sisältää tekoälykohtaiset toimintasuunnitelmat, jotka kattavat mallipainojen palauttamisen, GPU-klusterin uudelleenrakentamisen ja palveluiden riippuvuuskartoituksen.               |  3   |   V   |

---

## C4.10 Infrastruktuurin vaatimustenmukaisuus ja hallinta

Säilytä sääntelyvaatimusten noudattaminen jatkuvan arvioinnin, dokumentoinnin ja automatisoitujen valvontatoimien avulla.

|   #    | Kuvaus                                                                                                                                                                                               | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.10.1 | Varmista, että infrastruktuurin vaatimustenmukaisuus arvioidaan organisaation aikataulujen mukaisesti SOC 2:n, ISO 27001:n tai FedRAMP-ohjausten mukaisesti automaattisen todisteiden keruun avulla. |  2   |  D/V  |
| 4.10.2 | Varmista, että infrastruktuurin dokumentaatio sisältää verkon kaaviot, tiedonvirtauskartat ja uhkamallit, jotka on päivitetty organisaation muutoksenhallinnan vaatimusten mukaisesti.               |  2   |   V   |
| 4.10.3 | Varmista, että infrastruktuurimuutokset käyvät läpi automatisoidun säädösten vaikutusten arvioinnin, jossa on hyväksyntäprosessit korkeaa riskiä edustaville muutoksille.                            |  3   |  D/V  |

---

## C4.11 AI-laitteiston turvallisuus

Suojaa AI-spesifiset laitteistokomponentit, mukaan lukien GPU:t, TPU:t ja erikoistuneet AI-kiihdyttimet.

|   #    | Kuvaus                                                                                                                                                                                                      | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.11.1 | Varmista, että tekoälykiihdyttimen laiteohjelmisto (GPU BIOS, TPU-laiteohjelmisto) on varmennettu kryptografisilla allekirjoituksilla ja päivitetty organisaation korjaushallinnan aikataulujen mukaisesti. |  2   |  D/V  |
| 4.11.2 | Varmista, että ennen työkuorman suorittamista AI-kiihdyttimen eheyden vahvistaa laitteistovarmistus TPM 2.0:n, Intel TXT:n tai AMD SVM:n avulla.                                                            |  2   |  D/V  |
| 4.11.3 | Varmista, että GPU-muisti on eristetty työkuormien välillä käyttämällä SR-IOV:ta, MIG:iä (Multi-Instance GPU) tai vastaavaa laitteistopohjaista jakamista, jossa muisti puhdistetaan työn vaihtuessa.       |  2   |  D/V  |
| 4.11.4 | Varmista, että tekoälylaitteiston toimitusketju sisältää alkuperän todentamisen valmistajan sertifikaateilla ja väärentämisen osoittavien pakkauksien varmistamisen.                                        |  3   |   V   |
| 4.11.5 | Varmista, että laitteistoturvayksiköt (HSM:t) suojaavat tekoälymallin painot ja kryptografiset avaimet FIPS 140-2 -tason 3 tai Common Criteria EAL4+ -sertifikaatin mukaisesti.                             |  3   |  D/V  |

---

## C4.12 Reuna- ja hajautettu tekoälyinfrastruktuuri

Turvalliset hajautetut tekoälyn käyttöönotot, mukaan lukien reunalaskenta, yhdistetty oppiminen ja monipaikka-arkkitehtuurit.

|   #    | Kuvaus                                                                                                                                                                                                          | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.12.1 | Varmista, että reunatason AI-laitteet todennetaan keskusinfrastruktuuriin käyttämällä kaksisuuntaista TLS:ää laitetodistuksilla, joita kierrätetään organisaation sertifikaattien hallintakäytännön mukaisesti. |  2   |  D/V  |
| 4.12.2 | Varmista, että reunalaitteet toteuttavat suojatun käynnistyksen varmennetuilla allekirjoituksilla ja takaisinperuuntumissuojauksella, joka estää laiteohjelmiston alennushyökkäykset.                           |  2   |  D/V  |
| 4.12.3 | Varmista, että hajautettu tekoälyn koordinointi käyttää bysanttilaisviankestäviä konsensusalgoritmeja osallistujien vahvistuksella ja haitallisten solmujen havaitsemisella.                                    |  3   |  D/V  |
| 4.12.4 | Varmista, että reunalaitteen ja pilven välinen viestintä sisältää kaistanleveyden rajoituksen, tiedon pakkaamisen ja offline-toimintamahdollisuudet turvallisella paikallisella tallennuksella.                 |  3   |  D/V  |

---

## C4.13 Monipilvi- ja hybridiratkaisujen infrastruktuurin turvallisuus

Varmista tekoälysovellusten turvallisuus useiden pilvipalveluntarjoajien sekä hybridipilvi- ja paikallisympäristöjen käyttöönotossa.

|   #    | Kuvaus                                                                                                                                                                                         | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.13.1 | Varmista, että monipilvi- tekoälyn käyttöönotot käyttävät pilviriippumatonta identiteettifederaatiota (OIDC, SAML) keskitetyn politiikan hallinnan kanssa eri tarjoajien välillä.              |  2   |  D/V  |
| 4.13.2 | Varmista, että pilvienvälinen tiedonsiirto käyttää päästä päähän -salauksen, jossa avaimet hallitaan asiakkaan toimesta, ja että tietojen sijaintisäännökset toteutetaan lainkäyttöalueittain. |  2   |  D/V  |
| 4.13.3 | Varmista, että hybridipilvi-Tekoälytyökuormat toteuttavat yhtenäiset tietoturvakäytännöt paikallisissa ja pilviympäristöissä yhtenäisellä valvonnalla ja hälytyksillä.                         |  2   |  D/V  |
| 4.13.4 | Varmista, että pilvipalveluntarjoajan lukituksen estäminen sisältää siirrettävän infrastruktuuri-koodina, standardoidut API:t ja tietojen vientimahdollisuudet muunnostyökaluineen.            |  3   |   V   |
| 4.13.5 | Varmista, että monipilvikustannusten optimointi sisältää tietoturvakontrollit, jotka estävät resurssien leviämisen sekä luvattomat pilvienväliset datansiirtomaksut.                           |  3   |   V   |

---

## C4.14 Infrastruktuurin automaatio ja GitOps-tietoturva

Turvaa infrastruktuurin automaatio-putket ja GitOps-työnkulut tekoälyinfrastruktuurin hallintaa varten.

|   #    | Kuvaus                                                                                                                                                                                                                                  | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.14.1 | Varmista, että GitOps-varastoissa vaaditaan allekirjoitettuja committeja GPG-avaimilla ja että haara-suojaussäännöt estävät suorat pushit päähaaroihin.                                                                                 |  2   |  D/V  |
| 4.14.2 | Varmista, että infrastruktuurin automaatio sisältää poikkeamien tunnistuksen automaattisella korjauksella ja palautusmahdollisuuksilla, jotka laukaistaan organisaation vastausvaatimusten mukaisesti luvattomien muutosten yhteydessä. |  2   |  D/V  |
| 4.14.3 | Varmista, että automatisoitu infrastruktuurin käyttöönotto sisältää turvallisuuspolitiikan validoinnin ja estää käyttöönoton, jos kokoonpano ei ole vaatimusten mukainen.                                                               |  2   |  D/V  |
| 4.14.4 | Varmista, että infrastruktuurin automaation salaisuuksia hallinnoidaan ulkoisten salaisuuksien operaattoreiden (External Secrets Operator, Bank-Vaults) kautta automaattisella kierrätyksellä.                                          |  2   |  D/V  |
| 4.14.5 | Varmista, että itseparantuva infrastruktuuri sisältää turvallisuustapahtumien korrelaation automaattisen tapahtumavasteen ja sidosryhmien ilmoitusprosessien kanssa.                                                                    |  3   |   V   |

---

## C4.15 Kvanttivarma infrastruktuurin turvallisuus

Valmistele tekoälyn infrastruktuuri kvanttilaskennan uhkia varten postkvanttikryptografian ja kvanttiturvallisten protokollien avulla.

|   #    | Kuvaus                                                                                                                                                                                                                  | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.15.1 | Varmista, että tekoälyn infrastruktuuri toteuttaa NISTin hyväksymiä kvanttiturvallisia kryptografisia algoritmeja (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) avaintenvaihtoon ja digitaalisille allekirjoituksille. |  3   |  D/V  |
| 4.15.2 | Varmista, että kvanttivakiojakaumajärjestelmät (QKD) on toteutettu korkean turvallisuuden tekoälyn viestintään kvanttiturvallisilla avaintenhallintaprotokollilla.                                                      |  3   |  D/V  |
| 4.15.3 | Varmista, että kryptografisen ketteryyden kehykset mahdollistavat nopean siirtymisen uusiin postkvanttialgoritmeihin automatisoidulla varmenteiden ja avainten kierrätyksellä.                                          |  3   |  D/V  |
| 4.15.4 | Varmista, että kvanttivaaramallinnus arvioi tekoälyinfrastruktuurin haavoittuvuutta kvanttihyökkäyksille dokumentoitujen siirtymäaikataulujen ja riskinarviointien avulla.                                              |  3   |   V   |
| 4.15.5 | Varmista, että hybridi klassinen- ja kvanttikryptografinen järjestelmä tarjoaa monikerroksisen suojan kvanttisiirtymäkauden aikana suorituskyvyn seurannalla.                                                           |  3   |  D/V  |

---

## C4.16 Luottamuksellinen laskenta ja suojatut alueet

Suojaa tekoälyn työkuormia ja mallipainoja laitteistopohjaisten luotettavien suoritusympäristöjen ja luottamuksellisen laskennan teknologioiden avulla.

|   #    | Kuvaus                                                                                                                                                                                 | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.16.1 | Varmista, että arkaluonteiset tekoälymallit suoritetaan Intel SGX -alueiden, AMD SEV-SNP:n tai ARM TrustZonen sisällä käyttäen salattua muistia ja varmennustarkistusta.               |  3   |  D/V  |
| 4.16.2 | Varmista, että luottamukselliset kontit (Kata Containers, gVisor luottamuksellisen laskennan kanssa) eristävät tekoälytyökuormat laitteistopohjaisella muistisalausmenetelmällä.       |  3   |  D/V  |
| 4.16.3 | Varmista, että etätodentaminen vahvistaa kehysalueen eheyttä ennen tekoälymallien lataamista tarjoamalla kryptografisen todisteen suoritusalustan aitoudesta.                          |  3   |  D/V  |
| 4.16.4 | Varmista, että luottamukselliset tekoälyn päättelypalvelut estävät mallin kopioinnin salatun laskennan avulla, jossa mallipainot ovat suojattuina ja suoritus suojatussa ympäristössä. |  3   |  D/V  |
| 4.16.5 | Varmista, että luotettavan suoritusympäristön orkestrointi hallitsee turvallisen saarekkeen elinkaaren etätodennuksella ja salatuilla viestintäkanavilla.                              |  3   |  D/V  |
| 4.16.6 | Varmista, että turvallinen moniosapuolilaskenta (SMPC) mahdollistaa yhteistyöperusteisen tekoälyn koulutuksen paljastamatta yksittäisiä aineistoja tai mallin parametreja.             |  3   |  D/V  |

---

## C4.17 Nollatietoinen infrastruktuuri

Toteuta nollatietotodistusjärjestelmät yksityisyyttä suojaavaa tekoälyn varmennusta ja todentamista varten paljastamatta arkaluonteisia tietoja.

|   #    | Kuvaus                                                                                                                                                                                 | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.17.1 | Varmista, että nollatietotodistukset (ZK-SNARKit, ZK-STARKit) todentavat tekoälymallin eheyden ja koulutuksen alkuperän paljastamatta kuitenkaan mallin painoja tai koulutusdataa.     |  3   |  D/V  |
| 4.17.2 | Varmista, että ZK-pohjaiset todennusjärjestelmät mahdollistavat yksityisyyttä suojaavan käyttäjien vahvistamisen tekoälypalveluissa paljastamatta henkilöllisyyteen liittyviä tietoja. |  3   |  D/V  |
| 4.17.3 | Varmista, että yksityinen joukkojen leikkaus (PSI) -protokolla mahdollistaa turvallisen tietojen vertailun hajautetussa tekoälyssä paljastamatta yksittäisiä tietojoukkoja.            |  3   |  D/V  |
| 4.17.4 | Varmista, että nollatietoinen koneoppiminen (ZKML) -järjestelmät mahdollistavat todennettavien tekoälypäätösten tekemisen kryptografisella todistuksella oikeasta laskennasta.         |  3   |  D/V  |
| 4.17.5 | Varmista, että ZK-rollupit tarjoavat skaalautuvan, yksityisyyttä suojaavan tekoäly-tapahtumien käsittelyn erävarmennuksella ja vähennetyllä laskennallisella kuormituksella.           |  3   |  D/V  |

---

## C4.18 Sivukanavan hyökkäysten estäminen

Suojaa tekoälyinfrastruktuuri ajoitus-, teho-, sähkömagneettisilta ja välimuistipohjaisilta sivukanavahyökkäyksiltä, jotka voisivat vuotaa arkaluonteisia tietoja.

|   #    | Kuvaus                                                                                                                                                             | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.18.1 | Varmista, että tekoälyn päätelmän ajoitus on normalisoitu käyttämällä vakioaikaisia algoritmeja ja täytettä estämään ajoitukseen perustuvat mallin poiminta-iskut. |  3   |  D/V  |
| 4.18.2 | Varmista, että tehoanalyysin suojaus sisältää kohinan lisäämisen, virtalinjan suodatuksen ja satunnaistetut suorituskuviot AI-laitteistolle.                       |  3   |  D/V  |
| 4.18.3 | Varmista, että välimuistiin perustuva sivukanavahäirinnän estäminen käyttää välimuistin jakamista, satunnaistamista ja tyhjennyskäskyjä estämään tietovuotoja.     |  3   |  D/V  |
| 4.18.4 | Varmista, että sähkömagneettisten säteilyjen suojaus sisältää suojauksen, signaalisuodatuksen ja satunnaistetun käsittelyn estämään TEMPEST-tyylisiä hyökkäyksiä.  |  3   |  D/V  |
| 4.18.5 | Varmista, että mikroarkkitehtuuriset sivukanavien puolustukset sisältävät spekulatiivisen suorituksen ohjauksen ja muistinkäytön kuvion peittauksen.               |  3   |  D/V  |

---

## C4.19 Neuromorfinen ja erikoistunut tekoälyn laitteistoturvallisuus

Turvaa uusia tekoälyn laitteistoarkkitehtuureja, kuten neuromorfiset sirut, FPGA:t, räätälöidyt ASIC-piirit ja optiset laskentajärjestelmät.

|   #    | Kuvaus                                                                                                                                                                                                                       | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.19.1 | Varmista, että neuromorfisen sirun turvallisuus sisältää piikkikuvion salauksen, synaptisen painon suojauksen ja laitteistopohjaisen oppimissäännön vahvistuksen.                                                            |  3   |  D/V  |
| 4.19.2 | Varmista, että FPGA-pohjaiset tekoälykiihdyttimet toteuttavat bitstream-salauksen, manipulointisuojausmekanismit ja turvallisen konfiguroinnin latauksen todennetuilla päivityksillä.                                        |  3   |  D/V  |
| 4.19.3 | Varmista, että mukautetun ASIC-turvallisuuden ominaisuuksiin kuuluvat piirin sisäiset turvallisuusprosessorit, laitteistopohjainen luottamusperusta ja turvallinen avainten tallennus, jossa on manipuloinnin havaitseminen. |  3   |  D/V  |
| 4.19.4 | Varmista, että optiset laskentajärjestelmät toteuttavat kvanttiturvallisen optisen salauksen, suojatun fotonisen kytkennän ja suojatun optisen signaalinkäsittelyn.                                                          |  3   |  D/V  |
| 4.19.5 | Varmista, että hybridi analogis-digitaaliset AI-piirit sisältävät turvallisen analogisen laskennan, suojatun painotetun tallennuksen ja todennetun analogi-digitaalisen muunnoksen.                                          |  3   |  D/V  |

---

## C4.20 Yksityisyyttä säilyttävä laskenta-infrastruktuuri

Ota käyttöön infrastruktuurin valvontatoimet yksityisyyttä suojaavaa laskentaa varten suojellaksesi arkaluontoisia tietoja AI-käsittelyn ja analyysin aikana.

|   #    | Kuvaus                                                                                                                                                                                                     | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.20.1 | Varmista, että homomorfinen salausinfrastruktuuri mahdollistaa salatun laskennan arkaluontoisissa tekoälykuormissa käyttäen kryptograafista eheystarkistusta ja suorituskyvyn valvontaa.                   |  3   |  D/V  |
| 4.20.2 | Varmista, että yksityisen tiedon hakujärjestelmät mahdollistavat tietokantahaut paljastamatta hakukuvioita ja käyttävät salausmenetelmiä käyttökuvioiden suojaamiseksi.                                    |  3   |  D/V  |
| 4.20.3 | Varmista, että turvalliset moniosapuoletoteutusprotokollat mahdollistavat yksityisyyttä suojaavan tekoälyn päättelemisen paljastamatta yksittäisiä syötteitä tai välivaiheen laskelmia.                    |  3   |  D/V  |
| 4.20.4 | Varmista, että yksityisyyttä suojaava avainhallinta sisältää hajautetun avainluonnin, kynnyskriptografian ja turvallisen avainten kierrätyksen laitteistopohjaisella suojauksella.                         |  3   |  D/V  |
| 4.20.5 | Varmista, että yksityisyyttä säilyttävän laskennan suorituskyky on optimoitu yhdistämällä eräajo, välimuistitallennus ja laitteistokiihdytys samalla kun säilytetään kryptografiset turvallisuuslupaukset. |  3   |  D/V  |

---

## C4.15 Agenttikehys Pilvipalvelun integroinnin turvallisuus ja hybridi käyttöönotto

Turvallisuusvalvontamekanismit pilveen integroiduille agenttikehyksille hybridiä on-premises/pilvi-arkkitehtuuria varten.

|   #    | Kuvaus                                                                                                                        | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.15.1 | Varmista, että pilvitallennuksen integraatio käyttää päästä-päähän -salausta agentin hallitsemalla avainhallinnalla.          |  1   |  D/V  |
| 4.15.2 | Varmista, että hybridiasennuksen suojausrajat on selkeästi määritelty ja että viestintäkanavat ovat salattuja.                |  2   |  D/V  |
| 4.15.3 | Varmista, että pilviresurssien käyttö sisältää nollaluottamuksen varmennuksen jatkuvalla todentamisella.                      |  2   |  D/V  |
| 4.15.4 | Varmista, että tietojen sijaintia koskevia vaatimuksia noudatetaan salauksellisten todistusten avulla tallennuspaikoista.     |  3   |  D/V  |
| 4.15.5 | Varmista, että pilvipalveluntarjoajan tietoturva-arvioinnit sisältävät agenttikohtaisen uhkamallinnuksen ja riskinarvioinnin. |  3   |  D/V  |

---

## Viitteet

* [NIST Cybersecurity Framework 2.0](https://www.nist.gov/cyberframework)
* [CIS Controls v8](https://www.cisecurity.org/controls/v8)
* [OWASP Container Security Verification Standard](https://github.com/OWASP/Container-Security-Verification-Standard)
* [Kubernetes Security Best Practices](https://kubernetes.io/docs/concepts/security/)
* [SLSA Supply Chain Security Framework](https://slsa.dev/)
* [NIST SP 800-190: Application Container Security Guide](https://csrc.nist.gov/publications/detail/sp/800-190/final)
* [Cloud Security Alliance: Cloud Controls Matrix](https://cloudsecurityalliance.org/research/cloud-controls-matrix/)
* [ENISA: Secure Infrastructure Design](https://www.enisa.europa.eu/topics/critical-information-infrastructures-and-services)
* [NIST SP 800-53: Security Controls for Federal Information Systems](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final)
* [ISO 27001:2022 Information Security Management](https://www.iso.org/standard/27001)
* [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework)
* [CIS Kubernetes Benchmark](https://www.cisecurity.org/benchmark/kubernetes)
* [FIPS 140-2 Security Requirements](https://csrc.nist.gov/publications/detail/fips/140/2/final)
* [NIST SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/publications/detail/sp/800-207/final)
* [IEEE 2857: Privacy Engineering for AI Systems](https://standards.ieee.org/ieee/2857/7273/)
* [NIST SP 800-161: Cybersecurity Supply Chain Risk Management](https://csrc.nist.gov/publications/detail/sp/800-161/rev-1/final)
* [NIST Post-Quantum Cryptography Standards](https://csrc.nist.gov/Projects/post-quantum-cryptography)
* [Intel SGX Developer Guide](https://www.intel.com/content/www/us/en/developer/tools/software-guard-extensions/overview.html)
* [AMD SEV-SNP White Paper](https://www.amd.com/system/files/TechDocs/SEV-SNP-strengthening-vm-isolation-with-integrity-protection-and-more.pdf)
* [ARM TrustZone Technology](https://developer.arm.com/ip-products/security-ip/trustzone)
* [ZK-SNARKs: A Gentle Introduction](https://blog.ethereum.org/2016/12/05/zksnarks-in-a-nutshell/)
* [NIST SP 800-57: Cryptographic Key Management](https://csrc.nist.gov/publications/detail/sp/800-57-part-1/rev-5/final)
* [Side-Channel Attack Countermeasures](https://link.springer.com/book/10.1007/978-3-319-75268-6)
* [Neuromorphic Computing Security Challenges](https://ieeexplore.ieee.org/document/9458103)
* [FPGA Security: Fundamentals, Evaluation, and Countermeasures](https://link.springer.com/book/10.1007/978-3-319-90385-9)
* [Microsoft SEAL: Homomorphic Encryption Library](https://github.com/Microsoft/SEAL)
* [HElib: Homomorphic Encryption Library](https://github.com/homenc/HElib)
* [PALISADE Lattice Cryptography Library](https://palisade-crypto.org/)
* [Differential Privacy: A Survey of Results](https://link.springer.com/chapter/10.1007/978-3-540-79228-4_1)
* [Secure Aggregation for Federated Learning](https://eprint.iacr.org/2017/281.pdf)
* [Private Information Retrieval: Concepts and Constructions](https://link.springer.com/book/10.1007/978-3-030-16234-8)

