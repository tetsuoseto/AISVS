# C4 infrastruktuuri, konfiguraation ja käyttöönoton turvallisuus

## Kontrollitavoite

AI-infrastruktuurin on oltava kovennettu valtuuksien eskalointia, toimitusketjun manipulointia ja sivuttaisliikkeitä vastaan käyttämällä turvallista konfiguraatiota, ajonaikaisen eristyksen, luotettujen käyttöönotto-putkistojen sekä kattavan monitoroinnin avulla. Vain valtuutetut, vahvistetut infrastruktuurikomponentit ja konfiguraatiot pääsevät tuotantoon kontrolloitujen prosessien kautta, jotka ylläpitävät turvallisuutta, eheyttä ja auditointikykyä.

Keskeinen turvallisuustavoite: Vain kryptografisesti allekirjoitetut, haavoittuvuusskannatut infrastruktuurikomponentit saavuttavat tuotannon automaattisten validointiputkien kautta, jotka varmistavat turvallisuuspolitiikkojen noudattamisen ja ylläpitävät muuttumattomia auditointijälkiä.

---

## C4.1 Suoritusympäristön eristäminen

Estä konttien pakeneminen ja oikeuksien korotus ytimen tason eristysprimitiveillä ja pakollisilla pääsynvalvontamekanismeilla.

|   #   | Kuvaus                                                                                                                                                                                                                      | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.1.1 | Varmista, että kaikki tekoälykontit poistavat Linuxin capabiliteetit kokonaan, lukuun ottamatta CAP_SETUID, CAP_SETGID sekä turvallisuusperusteissa dokumentoitujen nimenomaisesti vaadittujen capabiliteettien.            |  1   |  D/V  |
| 4.1.2 | Varmista, että seccomp-profiilit estävät kaikki järjestelmäkutsut lukuun ottamatta ennalta hyväksyttyjä sallintalistoja, jolloin rikkomukset lopettavat kontin ja aiheuttavat turvallisuushälytyksiä.                       |  1   |  D/V  |
| 4.1.3 | Varmista, että tekoälykuormat toimivat lukukelpoisella juuritiedostojärjestelmällä, tilapäistiedot käytetään tmpfs:ää ja pysyvään dataan käytetään nimettyjä volyyumeja siten, että noexec-mount-vaihtoehdot ovat käytössä. |  2   |  D/V  |
| 4.1.4 | Varmista, että eBPF-pohjainen ajonaikainen valvonta (Falco, Tetragon tai vastaava) havaitsee oikeuksien korotusyritykset ja tappaa automaattisesti haitalliset prosessit organisaation reagoimisaikavaatimusten puitteissa. |  2   |  D/V  |
| 4.1.5 | Varmista, että korkean riskin tekoälykuormitukset suoritetaan laitteistisesti eristetyissä ympäristöissä (Intel TXT, AMD SVM, tai omistetut bare-metal-solmut) todentamisen varmistuksella.                                 |  3   |  D/V  |

---

## C4.2 Turvalliset rakennus- ja käyttöönottoputket

Varmista kryptografinen eheys ja toimitusketjun turvallisuus toistettavien rakennusprosessien ja allekirjoitettujen artefaktien avulla.

|   #   | Kuvaus                                                                                                                                                                                                             | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.2.1 | Varmista, että infrastruktuuri-koodi skannataan työkaluilla (tfsec, Checkov tai Terrascan) jokaisessa commitissa, ja yhdistämiset estetään CRITICAL- tai HIGH-tason löydösten perusteella.                         |  1   |  D/V  |
| 4.2.2 | Varmista, että konttien rakentaminen on toistettavissa identtisten SHA256-hashien kanssa eri rakennuksissa, ja luo SLSA Level 3 provenance-todistukset, jotka on allekirjoitettu Sigstorella.                      |  1   |  D/V  |
| 4.2.3 | Varmista, että konttikuva sisältää CycloneDX- tai SPDX SBOM:t ja on Cosignilla allekirjoitettu ennen rekisteriin työntöä, ja että allekirjoittamattomat kuvat hylätään käyttöönoton yhteydessä.                    |  2   |  D/V  |
| 4.2.4 | Varmista, että CI/CD-putket käyttävät OIDC-tunnuksia HashiCorp Vaultista, AWS IAM-rooleista tai Azure Managed Identity -tunnuksia, joiden voimassaoloajat eivät ylitä organisaation turvallisuuspolitiikan rajoja. |  2   |  D/V  |
| 4.2.5 | Varmista, että Cosign-allekirjoitukset ja SLSA-provenanssi validoidaan käyttöönoton aikana ennen kontin suorittamista, ja että vahvistusvirheet aiheuttavat käyttöönoton epäonnistumisen.                          |  2   |  D/V  |
| 4.2.6 | Varmista, että rakennusympäristöt toimivat väliaikaisissa konteissa tai virtuaalikoneissa, joilla ei ole pysyvää tallennustilaa, ja jotka ovat verkkoeristettyjä tuotannon VPC:istä.                               |  2   |  D/V  |

---

## C4.3 Verkon turvallisuus ja pääsynhallinta

Toteuta nollaluottamusverkko, jolla on oletuskieltopolitiikat ja salatut yhteydet.

|   #   | Kuvaus                                                                                                                                                                                                                          | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.3.1 | Varmista, että Kubernetes NetworkPolicies tai jokin vastaava toteuttaa oletuskiellon sisään- ja ulostulolle (default-deny ingress/egress) sekä selkeästi sallituilla säännöillä vaadittaville porteille (esim. 443, 8080, jne). |  1   |  D/V  |
| 4.3.2 | Varmista, että SSH (portti 22), RDP (portti 3389) ja pilven metadata-päätepisteet (169.254.169.254) ovat estettyjä tai ne edellyttävät sertifikaattipohjaista todentamista.                                                     |  1   |  D/V  |
| 4.3.3 | Varmista, että ulospäin suuntautuva liikenne suodatetaan HTTP/HTTPS-proxyjen kautta (Squid, Istio tai cloud NAT-gatewayt) domain-allowlistien avulla ja estettyjen pyyntöjen lokitus on käytössä.                               |  2   |  D/V  |
| 4.3.4 | Varmista, että palvelujen välinen viestintä käyttää kaksisuuntaista TLS:ää (mTLS) ja että sertifikaatit kierrätetään organisaation politiikan mukaisesti sekä sertifikaattien validointi on pakollista (ei skip-verify liput).  |  2   |  D/V  |
| 4.3.5 | Varmista, että AI-infrastruktuuri toimii omistetuissa VPC:issä/VNetsissä, joilla ei ole suoraa Internet-yhteyttä, ja että se kommunikoi ainoastaan NAT-yhdyskäytävien tai bastion-koneiden kautta.                              |  2   |  D/V  |

---

## C4.4 Salaisuudet ja kryptografisten avainten hallinta

Suojaa tunnistetiedot laitteistopohjaisella tallennuksella ja automaattisella kierrätyksellä sekä nollaluottamusperiaatteen mukaisella pääsylle.

|   #   | Kuvaus                                                                                                                                                                                                                | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.4.1 | Varmista, että salaisuudet tallennetaan HashiCorp Vaultiin, AWS Secrets Manageriin, Azure Key Vaultiin tai Google Secret Manageriin levyllä salattuna käyttämällä AES-256-salausta.                                   |  1   |  D/V  |
| 4.4.2 | Varmista, että kryptografiset avaimet generoidaan FIPS 140-2 Level 2 HSM:issä (AWS CloudHSM, Azure Dedicated HSM) siten, että avainten kierto noudattaa organisaation kryptografista politiikkaa.                     |  1   |  D/V  |
| 4.4.3 | Varmista, että salasanakierrätys on automatisoitu katkoksittomalla käyttöönotolla ja että kierrätys käynnistyy välittömästi henkilöstömuutosten tai turvallisuustapahtumien yhteydessä.                               |  2   |  D/V  |
| 4.4.4 | Varmista, että säiliökuvat skannataan työkaluilla (GitLeaks, TruffleHog tai detect-secrets) ja että API-avaimia, salasanoja tai sertifikaatteja sisältävät rakennukset estetään.                                      |  2   |  D/V  |
| 4.4.5 | Varmista, että tuotantoympäristön salaisen pääsyn edellytys on MFA laiteperusteisilla tunnisteilla (YubiKey, FIDO2) ja että siitä tallennetaan muuttumattomiin auditointilokeihin käyttäjäidentiteetit ja aikaleimat. |  2   |  D/V  |
| 4.4.6 | Varmista, että salaisuudet injektoidaan Kubernetes-salaisuuksien kautta, liitettyjen volyymien kautta tai init-konttien kautta, ja että salaisuudet eivät koskaan upotu ympäristömuuttujiin tai säiliökuviin.         |  2   |  D/V  |

---

## C4.5 AI-työkuormien hiekkalaatikkokäyttöönotto ja validointi

Erista epäluotettavat tekoälymallit turvallisissa hiekkalaatikoissa kattavan käyttäytymisanalyysin avulla.

|   #   | Kuvaus                                                                                                                                                                                                                | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.5.1 | Tarkista, että ulkoiset tekoälymallit suorittuvat gVisorissa, microVM-ympäristöissä (kuten Firecracker, CrossVM) tai Docker-konttien sisällä, lipuilla --security-opt=no-new-privileges ja --read-only.               |  1   |  D/V  |
| 4.5.2 | Varmista, että sandbox-ympäristöt eivät ole verkkoon yhteydessä (--network=none) tai että niihin on pääsy vain localhostiin, ja kaikki ulkoiset pyynnöt on estetty iptables-säännöillä.                               |  1   |  D/V  |
| 4.5.3 | Varmista, että tekoälymallin validointi sisältää automaattisen red-team-testaamisen organisaation määrittelemällä testikattavuudella ja käyttäytymisanalyysillä takaportin havaitsemiseksi.                           |  2   |  D/V  |
| 4.5.4 | Varmista, että ennen AI-mallin tuotantoon siirtämistä sen hiekkalaatikkotulokset ovat kryptografisesti allekirjoitetut valtuutettujen turvallisuushenkilöstön toimesta ja tallennetut muuttumattomiin audit-lokeihin. |  2   |  D/V  |
| 4.5.5 | Varmista, että hiekkalaatikkoympäristöt tuhoutuvat ja luodaan uudelleen referenssikuvista arviointien välillä täydellisen tiedostojärjestelmän ja muistin puhdistuksella.                                             |  2   |  D/V  |

---

## C4.6 Infrastruktuurin turvallisuusvalvonta

Jatkuva skannaus ja infrastruktuurin valvonta automatisoidulla korjaustoiminnalla ja reaaliaikaisilla hälytyksillä.

|   #   | Kuvaus                                                                                                                                                                                                               | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.6.1 | Varmista, että säiliökuvat skannataan organisaation aikataulujen mukaan, ja että kriittiset haavoittuvuudet estävät käyttöönoton organisaation riskikynnysten perusteella.                                           |  1   |  D/V  |
| 4.6.2 | Varmista, että infrastruktuuri täyttää CIS Benchmarksit tai NIST 800-53 -ohjaimet organisaation määrittelemillä noudattamisen kynnystasoilla sekä epäonnistuneiden tarkastusten automatisoidulla korjaustoiminnalla. |  1   |  D/V  |
| 4.6.3 | Varmista, että korkean vakavuuden haavoittuvuudet on korjattu organisaation riskienhallinnan aikataulujen mukaan hätätoimenpiteiden kanssa aktiivisesti hyväksikäytettyjen CVE-tunnusten varalta.                    |  2   |  D/V  |
| 4.6.4 | Varmista, että turvallisuushälytykset integroituvat SIEM-alustoihin (Splunk, Elastic tai Sentinel) käyttämällä CEF tai STIX/TAXII-muotoja automaattisella rikastuksella.                                             |  2   |   V   |
| 4.6.5 | Varmista, että infrastruktuurin mittarit viedään valvontajärjestelmiin (Prometheus, DataDog) SLA-koontinäytöineen ja johtajille suunnatun raportoinnin kera.                                                         |  3   |   V   |
| 4.6.6 | Varmista, että konfiguraatioero havaitaan käyttämällä työkaluja (Chef InSpec, AWS Config) organisaation monitorointivaatimusten mukaan ja että luvattomien muutosten varalta toteutetaan automaattinen palautus.     |  2   |  D/V  |

---

## C4.7 tekoälyinfrastruktuurin resurssien hallinta

Estä resurssien loppumisen hyökkäykset ja varmista oikeudenmukainen resurssien jakaminen kiintiöiden ja seurannan avulla.

|   #   | Kuvaus                                                                                                                                                                                                                                            | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.7.1 | Varmista, että GPU/TPU-käyttöä seurataan ja hälytykset laukaistaan organisaation määrittelemien kynnysten mukaan sekä automaattinen skaalautuminen tai kuormituksen tasapainotus otetaan käyttöön kapasiteetin hallintapolitiikkojen perusteella. |  1   |  D/V  |
| 4.7.2 | Varmista, että tekoälyn työkuorman mittarit (inferenssin viive, läpäisynopeus, virheprosentit) kerätään organisaation valvontavaatimusten mukaan ja korreloidaan infrastruktuurin käyttöasteen kanssa.                                            |  1   |  D/V  |
| 4.7.3 | Varmista, että Kubernetesin ResourceQuotas tai vastaavat rajoittavat yksittäisiä työkuormia organisaation resurssien allokointikäytäntöjen mukaisesti ja että kovia rajoja noudatetaan.                                                           |  2   |  D/V  |
| 4.7.4 | Varmista, että kustannusten seuranta seuraa menoja jokaiselle työkuormalle/vuokraajalle siten, että hälytykset perustuvat organisaation budjettikynnyksiin ja että budjetin ylityksiä vastaan on automaattiset kontrollit.                        |  2   |   V   |
| 4.7.5 | Varmista, että kapasiteetin suunnittelu käyttää historiallisia tietoja organisaation määrittelemillä ennustejaksoilla ja että automaattinen resurssien provisiointi perustuu kysyntäkuvioihin.                                                    |  3   |   V   |
| 4.7.6 | Varmista, että resurssien loppuminen laukaisee sulakekatkaisijat organisaation vastausvaatimusten mukaan, mukaan lukien kapasiteettopolitiikkojen perusteella tapahtuva nopeusrajoitus ja työkuorman eristäminen.                                 |  2   |  D/V  |

---

## C4.8 Ympäristöjen erottaminen ja julkaisujen hallinta

Varmista tiukat ympäristörajat automatisoiduilla siirtoporteilla ja turvallisuusvalidaatiolla.

|   #   | Kuvaus                                                                                                                                                                                                              | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.8.1 | Varmista, että kehitys-, testi- ja tuotantoympäristöt toimivat erillisissä VPC- ja VNets-verkoissa siten, ettei niillä ole jaettuja IAM-rooleja, turvallisuusryhmiä tai verkkoyhteyksiä.                            |  1   |  D/V  |
| 4.8.2 | Varmista, että ympäristön käyttöönoton hyväksyntä edellyttää organisaation määrittelemien valtuutettujen henkilöiden kryptografisia allekirjoituksia ja muuttumattomia auditointijälkiä.                            |  1   |  D/V  |
| 4.8.3 | Varmista, että tuotantoympäristöt estävät SSH-pääsyn, poistavat debug-päätepisteet käytöstä ja edellyttävät muutospyynnöt organisaation etukäteen ilmoitusvaatimusten mukaisesti, lukuun ottamatta hätätilanteita.  |  2   |  D/V  |
| 4.8.4 | Varmista, että infrastruktuuri-koodimuutokset vaativat vertaisarvioinnin, automaattisen testauksen ja turvallisuusskannauksen ennen yhdistämistä päähaaraan.                                                        |  2   |  D/V  |
| 4.8.5 | Varmista, että ei-tuotantodataa on anonymisoitu organisaation tietosuojavaatimusten mukaisesti, synteettisen datan generoinnin avulla tai täydellisen datan maskauksen yhteydessä, jossa PII-poisto on varmistettu. |  2   |  D/V  |
| 4.8.6 | Varmista, että edistyskynnysten portit sisältävät automatisoidut turvallisuustestit (SAST, DAST, konttiskannaus) ja että hyväksyntään vaaditaan nolla CRITICAL-löydöksiä.                                           |  2   |  D/V  |

---

## C4.9 Infrastruktuurin varmuuskopiointi ja palautus

Varmista infrastruktuurin resilienssi automatisoiduilla varmuuskopioilla, testatuilla palautusmenetelmillä ja katastrofapalautumiskyvyillä.

|   #   | Kuvaus                                                                                                                                                                                                           | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.9.1 | Varmista, että infrastruktuurikokoonpanot varmuuskopioidaan organisaation varmuuskopiointiaikataulujen mukaan maantieteellisesti erillisiin alueisiin 3-2-1-varmuuskopiointistrategian toteuttamisen yhteydessä. |  1   |  D/V  |
| 4.9.2 | Varmista, että varmuuskopiojärjestelmät toimivat eristetyissä verkoissa, niillä on omat erilliset tunnukset ja ilman verkkoyhteyttä oleva tallennus ransomware-suojaksi.                                         |  2   |  D/V  |
| 4.9.3 | Varmista, että palautusmenettelyt testataan ja validoidaan automaattisella testauksella organisaation aikataulujen mukaisesti ja RTO- ja RPO-tavoitteet täyttävät organisaation vaatimukset.                     |  2   |   V   |
| 4.9.4 | Varmista, että katastrofipalautuminen sisältää AI-spesifiset runbookit, jotka kattavat mallin painojen palautuksen, GPU-klusterin uudelleenrakentamisen ja palveluiden riippuvuuskartoituksen.                   |  3   |   V   |

---

## C4.10 Infrastruktuurin vaatimustenmukaisuus ja hallinto

Säilytä säädösten noudattaminen jatkuvan arvioinnin, dokumentoinnin ja automatisoitujen kontrollien avulla.

|   #    | Kuvaus                                                                                                                                                                                                    | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.10.1 | Varmista, että infrastruktuurin vaatimustenmukaisuutta arvioidaan organisaation aikataulujen mukaan SOC 2, ISO 27001 tai FedRAMP-ohjausten perusteella automaattisen todistusaineiston keräämisen avulla. |  2   |  D/V  |
| 4.10.2 | Varmista, että infrastrukturiudokumentaatio sisältää verkkokaaviot, tiedonvirtakartat ja uhkamallit, jotka on päivitetty organisaation muutosjohtamisen vaatimusten mukaan.                               |  2   |   V   |
| 4.10.3 | Varmista, että infrastruktuurimuutokset käyvät läpi automaattisen vaatimustenmukaisuuden vaikutusarvioinnin sekä niihin liittyvät sääntelyhyväksyntätyönkulut korkean riskin muutoksille.                 |  3   |  D/V  |

---

## C4.11 Tekoälylaitteistojen turvallisuus

Turvalliset tekoälyyn liittyvät laitteistokomponentit, mukaan lukien GPU:t, TPU:t ja erikoistuneet tekoälykiihdyttimet.

|   #    | Kuvaus                                                                                                                                                                                                       | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.11.1 | Varmista, että tekoälykiihdyttimen laiteohjelmisto (GPU BIOS, TPU-laiteohjelmisto) on kryptografisilla allekirjoituksilla varmennettu ja päivitetty organisaation päivityshallinnan aikataulujen mukaisesti. |  2   |  D/V  |
| 4.11.2 | Varmista, että ennen työkuorman suoritusta tekoälykiihdyttimen eheys varmistetaan laitteistotodennuksella käyttämällä TPM 2.0, Intel TXT tai AMD SVM.                                                        |  2   |  D/V  |
| 4.11.3 | Varmista, että GPU:n muisti on eristetty työkuormien välillä käyttämällä SR-IOV:ia, MIG:ia (Multi-Instance GPU) tai vastaavaa laitteistollista ositusmenetelmää muistin sanitoinnin avulla työn välillä.     |  2   |  D/V  |
| 4.11.4 | Varmista, että tekoälylaitteistojen toimitusketju sisältää alkuperäisyyden todentamisen valmistajan sertifikaattien avulla sekä väärennösten estävän pakkausvalidaation.                                     |  3   |   V   |
| 4.11.5 | Varmista, että laitteistoturvamoduulit (HSM:t) suojaavat tekoälymallien painot ja kryptografiset avaimet FIPS 140-2 tason 3 tai Common Criteria EAL4+-sertifioinnin kanssa.                                  |  3   |  D/V  |

---

## C4.12 Reuna- ja hajautettu tekoälyinfrastruktuuri

Turvalliset hajautetut tekoälyjärjestelmät, mukaan lukien reunalaskenta, federaatio-oppiminen ja monipaikkaiset arkkitehtuurit.

|   #    | Kuvaus                                                                                                                                                                                                                     | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.12.1 | Varmista, että reuna-AI-laitteet todentavat itsensä keskitettyyn infrastruktuuriin käyttämällä kaksisuuntaista TLS:ää, ja että laitteiden varmenteet kierrätetään organisaation varmenteidenhallintapolitiikan mukaisesti. |  2   |  D/V  |
| 4.12.2 | Varmista, että reunalaitteet toteuttavat turvallisen käynnistyksen todennetuilla allekirjoituksilla ja rollback-suojan, joka estää firmware-päivitysten downgrade-hyökkäykset.                                             |  2   |  D/V  |
| 4.12.3 | Varmista, että hajautettu tekoälyn koordinointi käyttää Byzantiinivirheenkestäviä konsensusalgoritmeja, joissa on osallistujien validointi ja haitallisten solmujen havaitseminen.                                         |  3   |  D/V  |
| 4.12.4 | Varmista, että reuna-pilvi-yhteys sisältää kaistanleveyden rajoittamisen, tiedonpakkaamisen ja offline-toimintakyvyn sekä turvallisen paikallisen tallennuksen.                                                            |  3   |  D/V  |

---

## C4.13 Monipilvi- ja hybridi-infrastruktuurin tietoturva

Turvaa tekoälykuormit useissa pilvipalveluntarjoajissa sekä hybridi-pilvi- ja paikan päällä toteutetuissa käyttöönotuksissa.

|   #    | Kuvaus                                                                                                                                                                                                             | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.13.1 | Varmista, että monipilvi-tekoälykäyttöönotot käyttävät pilviympäristöriippumatonta identiteettifederointia (OIDC, SAML) ja keskitettyä politiikan hallintaa toimittajien välillä.                                  |  2   |  D/V  |
| 4.13.2 | Varmista, että pilvien välisessä tiedonsiirrossa käytetään loppuun asti salattua tiedonsiirtoa asiakkaan hallinnoimilla avaimilla ja että tietojen residenssivalvontaa sovelletaan kunkin lainkäyttöalueen mukaan. |  2   |  D/V  |
| 4.13.3 | Varmista, että hybridi-pilvi tekoälykuormat toteuttavat yhdenmukaiset turvapolitiikat paikallisten ympäristöjen ja pilviympäristöjen välillä, sekä niissä on yhtenäinen monitorointi ja hälytys.                   |  2   |  D/V  |
| 4.13.4 | Varmista, että pilvitoimittajariippuvuuden estäminen sisältää siirrettävän infrastruktuuri-koodin, standardoidut API:t ja tietojen vientiominaisuudet formaattimuunnostyökaluineen.                                |  3   |   V   |
| 4.13.5 | Varmista, että multicloud-kustannusten optimointi sisältää turvallisuusvalvontatoimenpiteet, jotka estävät sekä resurssien leviäminen että luvattomien pilvien välisten datansiirtomaksujen syntymisen.            |  3   |   V   |

---

## C4.14 Infrastruktuurin automatisointi ja GitOps-turvallisuus

Varmista infrastruktuurin automatisointiputkien ja GitOps-työnkulkujen turvallisuus tekoälyinfrastruktuurin hallintaa varten.

|   #    | Kuvaus                                                                                                                                                                                                                              | Taso | Rooli |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.14.1 | Varmista, että GitOps-repositoriot vaativat allekirjoitetut commitit GPG-avaimilla ja haaran suojaussäännöt estävät suorat pushit päähaaroihin.                                                                                     |  2   |  D/V  |
| 4.14.2 | Varmista, että infrastruktuurin automaatiossa on poikkeamien havaitseminen, automaattiset korjaustoimenpiteet ja palautusominaisuudet, jotka laukaistaan organisaation reaktiovaatimusten mukaisesti luvattomien muutosten varalta. |  2   |  D/V  |
| 4.14.3 | Varmista, että automatisoitu infrastruktuurin provisionointi sisältää turvallisuuspolitiikan validoinnin, joka estää käyttöönoton epäyhteensopiville konfiguraatioille.                                                             |  2   |  D/V  |
| 4.14.4 | Varmista, että infrastruktuurin automatisoinnin salaisuudet hallitaan ulkoisten salaisuustoimittajien kautta (External Secrets Operator, Bank-Vaults) automaattisella kierrätyksellä.                                               |  2   |  D/V  |
| 4.14.5 | Varmista, että itsekorjaava infrastruktuuri sisältää turvallisuustapahtumien korrelaation automaattisten incidenttivastausten sekä sidosryhille suunnattujen ilmoitus- ja työnkulkujen kanssa.                                      |  3   |   V   |

---

## C4.15 Kvanttivarmennettu infrastruktuuriturvallisuus

Valmistele tekoälyinfrastruktuuri kvanttitietokoneiden uhkia varten käyttämällä postkvanttikryptografiaa ja kvanttiturvallisia protokollia.

|   #    | Kuvaus                                                                                                                                                                                                        | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.15.1 | Varmista, että tekoälyinfrastruktuuri toteuttaa NIST:n hyväksymiä postkvanttisia kryptografisia algoritmeja (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) avainvaihdolle ja digitaalisiin allekirjoituksiin. |  3   |  D/V  |
| 4.15.2 | Varmista, että kvanttiavaintenjakelujärjestelmät on otettu käyttöön korkean turvallisuuden AI-viestintää varten kvanttisuojaavien avainhallintaprotokollien kanssa.                                           |  3   |  D/V  |
| 4.15.3 | Varmista, että kryptografisen ketteryyden kehykset mahdollistavat nopean siirtymisen uusiin post-kvanttialgoritmeihin automaattisella sertifikaattien ja avainten kierrätyksellä.                             |  3   |  D/V  |
| 4.15.4 | Varmista, että kvanttuhkamallinnus arvioi tekoälyinfrastruktuurin haavoittuvuuden kvanttihyökkäyksiä vastaan dokumentoitujen siirtymäaikojen ja riskinarvioiden kanssa.                                       |  3   |   V   |
| 4.15.5 | Varmista, että hybridit klassisen ja kvanttikryptografian järjestelmät tarjoavat monitasoisen suojauksen kvanttisiirtymäkauden aikana sekä suorituskykyseurannan.                                             |  3   |  D/V  |

---

## C4.16 Luottamuksellinen laskenta & turvalliset enklavit

Suojataan tekoälyn työkuormia ja mallien painoja käyttämällä laitteistopohjaisia luotettavia suoritusympäristöjä ja luottamuksellisia laskentatekniikoita.

|   #    | Kuvaus                                                                                                                                                                                        | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.16.1 | Varmista, että arkaluonteiset AI-mallit suorittuvat Intel SGX-enklaaveissa, AMD SEV-SNP-turvasäiliöissä tai ARM TrustZone-turva-alueella salatun muistin ja todentamisen varmistuksen avulla. |  3   |  D/V  |
| 4.16.2 | Varmista, että salassapitokontit (Kata Containers, gVisor, jolla on salassapitolaskenta) eristävät tekoälytyökuormat laitteistossa toteutetulla muistinsalauksella.                           |  3   |  D/V  |
| 4.16.3 | Varmista, että etävarmennus vahvistaa enclave-eheyden ennen tekoälymallien lataamista kryptografisen todistuksen avulla, joka osoittaa suoritusympäristön aitouden.                           |  3   |  D/V  |
| 4.16.4 | Tarkista, että luottamukselliset tekoälyn inferenssipalvelut estävät mallin kopioinnin salatun laskennan kautta, jossa mallipainot ovat sinetöidyt ja suoritus on suojattu.                   |  3   |  D/V  |
| 4.16.5 | Varmista, että luotetun suoritusympäristön orkestrointi hallinnoi turvallisen suljetun ympäristön elinkaarta etävarmennuksen ja salattujen viestintäkanavien avulla.                          |  3   |  D/V  |
| 4.16.6 | Varmista, että turvallinen monen osapuolen laskenta (SMPC) mahdollistaa yhteistoiminnallisen tekoälykoulutuksen paljastamatta yksittäisiä tietojoukkoja tai malliparametreja.                 |  3   |  D/V  |

---

## C4.17 Nollatietoinfrastruktuuri

Toteuta nollatietotodistejärjestelmiä yksityisyyttä suojaavan tekoälyn vahvistamiseen ja todennukseen paljastamatta arkaluonteista tietoa.

|   #    | Kuvaus                                                                                                                                                                                         | Taso | Rooli |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.17.1 | Varmista, että nollatietotodistukset (ZK-SNARKs, ZK-STARKs) vahvistavat AI-mallin eheyden ja koulutuksen alkuperän paljastamatta mallin painoja tai koulutusdataa.                             |  3   |  D/V  |
| 4.17.2 | Varmista, että ZK-pohjaiset todennusjärjestelmät mahdollistavat yksityisyyden suojaa säilyttävän käyttäjän vahvistamisen tekoälypalveluissa paljastamatta henkilöllisyyteen liittyviä tietoja. |  3   |  D/V  |
| 4.17.3 | Varmista, että yksityisen joukon leikkaus (PSI) protokollat mahdollistavat turvallisen tietojen vastaavuuden federatiivisessa tekoälyssä ilman, että yksittäisiä tietojoukkoja paljastetaan.   |  3   |  D/V  |
| 4.17.4 | Tarkista, että nollatietoon perustuvat koneoppimisen (ZKML) järjestelmät mahdollistavat verifioitavat tekoälyn inferenssit kryptografisen oikeellisuustodistuksen avulla.                      |  3   |  D/V  |
| 4.17.5 | Varmista, että ZK-rollupit tarjoavat skaalautuvaa, yksityisyyttä suojaavaa tekoälytransaktioiden käsittelyä erävahvistuksen avulla ja pienemmän laskennallisen kuormituksen kautta.            |  3   |  D/V  |

---

## C4.18 Sivukanava-hyökkäysten ehkäisy

Suojaa tekoälyinfrastruktuuria aikahyökkäyksiltä, virtahyökkäyksiltä, elektromagneettisilta sivukanavahyökkäyksiltä ja välimuistiin perustuvilta sivukanavahyökkäyksiltä, jotka voisivat vuotaa arkaluontoista tietoa.

|   #    | Kuvaus                                                                                                                                                                           | Taso | Rooli |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.18.1 | Varmista, että tekoälyn inferenssiaika on aikavakioitu käyttämällä aikavakioalgoritmeja ja täytettä estämään aikaperusteleisia mallinpoimintahyökkäyksiä.                        |  3   |  D/V  |
| 4.18.2 | Varmista, että tehoanalyysinsuojaus sisältää kohinan injektoinnin, syöttölinjan suodatuksen ja satunnaistetut suoritusmallit AI-laitteistolle.                                   |  3   |  D/V  |
| 4.18.3 | Varmista, että välimuistiin perustuva sivuväyläkanavien torjunta käyttää välimuistin osituksen, satunnaistamisen ja tyhjennyskäskyjen yhdistelmää tiedon vuotamisen estämiseksi. |  3   |  D/V  |
| 4.18.4 | Varmista, että elektromagneettisten päästöjen suojaus sisältää suojauksen, signaalisuodatuksen ja satunnaistetun käsittelyn TEMPEST-tyylisten hyökkäysten estämiseksi.           |  3   |  D/V  |
| 4.18.5 | Varmista, että mikroarkkitehtuuriin perustuvat sivukanavien puolustukset sisältävät spekulatiivisen suorituksen hallinnan sekä muistin pääsyn kuvioiden hämärtämisen.            |  3   |  D/V  |

---

## C4.19 Neuromorfinen ja erikoistunut tekoälyn laitteistoturva

Varmista kehittyvien tekoälylaitteistojen arkkitehtuurien turvallisuus, mukaan lukien neuromorfiset sirut, FPGA:t, räätälöidyt ASIC:t ja optisen laskennan järjestelmät.

|   #    | Kuvaus                                                                                                                                                                                                              | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.19.1 | Varmista, että neuromorfisen sirun turvallisuus sisältää piikkikuvioiden salauksen, synapsien painojen suojauksen sekä laitteistopohjaista oppimissääntöjen validointia.                                            |  3   |  D/V  |
| 4.19.2 | Varmista, että FPGA-pohjaiset tekoälykiihdyttimet toteuttavat bitstream-salauksen, manipuloinnin estävät mekanismit ja turvallisen konfiguraation lataamisen autentikoiduilla päivityksillä.                        |  3   |  D/V  |
| 4.19.3 | Varmista, että räätälöidyn ASIC-turvallisuuden piiriin kuuluvat sirun sisäiset turvaprosessorit, laitteistopohjainen luottamusjuuri sekä manipulointihavaitsemisjärjestelmällä varustettu turvallinen avainvarasto. |  3   |  D/V  |
| 4.19.4 | Varmista, että optisen laskennan järjestelmät toteuttavat kvanttivarmennetun optisen salauksen, turvallisen fotoniikkakytkennän ja suojatun optisen signaaliprosessoinnin.                                          |  3   |  D/V  |
| 4.19.5 | Varmista, että hybridi-analog-digitaaliset tekoälysirut sisältävät turvallisen analogisen laskennan, suojatun painojen tallennuksen ja todentuneen analogidigitaalimuunnoksen.                                      |  3   |  D/V  |

---

## C4.20 Tietosuojaan-perustuva laskenta-infrastruktuuri

Ota käyttöön infrastruktuurin hallintakeinot, joilla varmistetaan yksityisyyttä suojaavan laskennan turvallisuus ja arkaluontoisten tietojen suojaus AI:n käsittelyn ja analyysin aikana.

|   #    | Kuvaus                                                                                                                                                                                                 | Taso | Rooli |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 4.20.1 | Varmista, että homomorfinen salausinfrastruktuuri mahdollistaa salatun laskennan arkaluonteisilla tekoälykuormilla kryptografisen eheyden varmistuksen ja suorituskyvyn seurannan kanssa.              |  3   |  D/V  |
| 4.20.2 | Varmista, että yksityisen tiedonhaun järjestelmät mahdollistavat tietokantakyselyt paljastamatta kyselymalleja kryptografisen pääsynmallien suojauksen avulla.                                         |  3   |  D/V  |
| 4.20.3 | Varmista, että turvalliset usean osapuolen laskentaprotokollat mahdollistavat yksityisyyden suojaavan tekoälyn inferenssin ilman, että yksittäisiä syötteitä tai välituloksia paljastetaan.            |  3   |  D/V  |
| 4.20.4 | Varmista, että yksityisyyden suojaava avainhallinta sisältää jaetun avainten generoinnin, kynnyskriptografian sekä laitteistopohjaisen suojauksen kanssa tapahtuvan turvallisen avainten kierrätyksen. |  3   |  D/V  |
| 4.20.5 | Varmista, että yksityisyyden suojaan perustuvan laskennan suorituskyky on optimoitu ryhmittelyn, välimuistin ja laitteistokiihdytyksen kautta samalla kun kryptografiset turvatakuut säilyvät.         |  3   |  D/V  |

---

## C4.15 Agenttikehys pilvi-integraatio turvallisuus & hybridi käyttöönotto

Pilvi-integroitujen agenttikehikkojen turvallisuustoimenpiteet hybridiympäristöihin, joissa on sekä on-premises- että pilviarkkitehtuureja.

|   #    | Kuvaus                                                                                                                      | Taso | Rooli |
| :----: | --------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 4.15.1 | Varmista, että pilvitallennuksen integraatio käyttää end-to-end-salausta, jonka avainhallinta on agentin hallinnassa.       |  1   |  D/V  |
| 4.15.2 | Varmista, että hybridi-käyttöönoton turvallisuusrajat on määritelty selkeästi salatuilla viestintäkanavilla.                |  2   |  D/V  |
| 4.15.3 | Varmista, että pilviresurssien pääsy sisältää nolla-trustin todentamisen jatkuvalla todennuksella.                          |  2   |  D/V  |
| 4.15.4 | Varmista, että datan sijaintivaatimukset noudatetaan kryptografisen todentamisen avulla tallennuspaikoista.                 |  3   |  D/V  |
| 4.15.5 | Varmista, että pilvipalveluntarjoajan turvallisuusarvioinnit sisältävät agenttikohtaisen uhkamallinnan ja riskinarvioinnin. |  3   |  D/V  |

---

## Lähteet

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

