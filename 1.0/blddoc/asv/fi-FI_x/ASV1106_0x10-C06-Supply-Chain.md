# C6 Mallien, kehysten ja datan toimitusketjun turvallisuus

## Kontrollitavoite

tekoäly‑toimitusketjuhyökkäykset hyödyntävät kolmannen osapuolen malleja, kehyksiä tai aineistoja takaporttien, vinouksen tai haavoittuvan koodin sisäänrakentamiseen. Nämä kontrollit tarjoavat loppupään jäljitettävyyden, haavoittuvuuksien hallinnan ja seurannan koko mallin elinkaaren suojaamiseksi.

---

## C6.1 Esikoulutetun mallin tarkastus ja jäljitettävyys

Arvioi ja varmista kolmannen osapuolen mallien alkuperät, lisenssit ja piilotetut käytökset ennen minkään hienosäätöä tai käyttöönottoa.

|   #   | Kuvaus                                                                                                                                                                  | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.1.1 | Varmista, että jokainen kolmannen osapuolen malliartefakti sisältää allekirjoitetun provenanssirekisterin, jossa on sekä lähdevarasto että commit-hash.                 |  1   |  D/V  |
| 6.1.2 | Varmista, että malleja skannataan automatisoiduilla työkaluilla haitallisten kerrosten tai Troijan laukaisimien varalta ennen tuontia.                                  |  1   |  D/V  |
| 6.1.3 | Varmista, että transfer‑learning fine‑tunes läpäisevät adversarial-arvioinnin ja havaitsevat piilotetut käyttäytymiset.                                                 |  2   |   D   |
| 6.1.4 | Varmista, että mallilisenssit, vientivalvonta-tunnisteet ja tietojen alkuperää koskevat lausumat tallennetaan ML‑BOM-tietueeseen.                                       |  2   |   V   |
| 6.1.5 | Varmista, että korkean‑riskin mallit (julkisesti ladatut painot, vahvistamattomat tekijät) pysyvät karanteenissa, kunnes inhimillinen tarkastus ja hyväksyntä on tehty. |  3   |  D/V  |

---

## C6.2 Kehysten ja kirjastojen skannaus

Jatkuvasti skannaa ML-kehyksiä ja kirjastoja CVE-haavoittuvuuksien ja haitallisen koodin varalta pitääkseen ajonaikaisen pinon turvallisena.

|   #   | Kuvaus                                                                                                                                             | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.2.1 | Varmista, että CI-putket käyttävät riippuvuusskannereita tekoälykehyksille ja kriittisille kirjastoille.                                           |  1   |  D/V  |
| 6.2.2 | Varmista, että kriittiset haavoittuvuudet (CVSS ≥ 7.0) estävät siirtymisen tuotantokuviin.                                                         |  1   |  D/V  |
| 6.2.3 | Varmista, että staattinen koodianalyysi suoritetaan haarukoiduilla tai vendoroiduilla ML-kirjastoilla.                                             |  2   |   D   |
| 6.2.4 | Varmista, että kehyspäivitysehdotukset sisältävät turvallisuusvaikutusten arvioinnin, joka viittaa julkisiin CVE-syötteisiin.                      |  2   |   V   |
| 6.2.5 | Varmista, että ajoaikaiset sensorit varoittavat odottamattomista dynaamisten kirjastojen latauksista, jotka poikkeavat allekirjoitetusta SBOM:sta. |  3   |   V   |

---

## C6.3 Riippuvuuksien kiinnitys ja varmistus

Lukitse jokainen riippuvuus muuttumattomiin tiivisteisiin ja toista rakennusprosessit taatakseen identtiset, manipuloimattomat artefaktit.

|   #   | Kuvaus                                                                                                                                              | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.3.1 | Varmista, että kaikki pakettienhallintajärjestelmät pakottavat version kiinnityksen lockfilejen kautta.                                             |  1   |  D/V  |
| 6.3.2 | Varmista, että konttiviitteissä käytetään muuttumattomia tiivisteitä sen sijaan, että käytetään muuttuvia tageja.                                   |  1   |  D/V  |
| 6.3.3 | Varmista, että toistettavien rakennusten tarkistukset vertaavat hajautusarvoja CI-ajojen välillä ja varmistavat identtiset tulokset.                |  2   |   D   |
| 6.3.4 | Tarkista, että koontitodistukset tallennetaan 18 kuukauden ajaksi auditoitavuuden varmistamiseksi.                                                  |  2   |   V   |
| 6.3.5 | Varmista, että vanhentuneet riippuvuudet laukaisevat automaattiset PR:t päivittämiseksi tai kiinnitettyjen versioiden haarukoinnin suorittamiseksi. |  3   |   D   |

---

## C6.4 Luotettujen lähteiden täytäntöönpano

Salli artefaktien lataukset vain kryptografisesti varmennetuista lähteistä, jotka organisaatio on hyväksynyt, ja estä kaikki muut.

|   #   | Kuvaus                                                                                                                                                                           | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.4.1 | Varmista, että mallin painot, datasetit ja kontit ladataan ainoastaan hyväksytyistä verkkotunnuksista tai sisäisistä rekistereistä.                                              |  1   |  D/V  |
| 6.4.2 | Varmista, että Sigstore/Cosign-allekirjoitukset vahvistavat julkaisijan identiteetin ennen kuin artefaktit tallennetaan paikallisesti välimuistiin.                              |  1   |  D/V  |
| 6.4.3 | Varmista, että ulospäin suuntautuvat proxy-palvelimet estävät artefaktien lataukset ilman autentikointia, jotta luotettujen lähteiden politiikka toteutuu.                       |  2   |   D   |
| 6.4.4 | Varmista, että varaston sallittujen luetteloiden tarkastukset suoritetaan neljännesvuosittain ja että kunkin merkinnän yhteydessä on todiste liiketoiminnallisesta perustelusta. |  2   |   V   |
| 6.4.5 | Varmista, että politiikan rikkomukset laukaisevat artefaktien karanteeniin asettamisen sekä riippuvaisten pipeline-ajojen palautuksen.                                           |  3   |   V   |

---

## C6.5 Kolmannen osapuolen tietojoukon riskinarviointi

Arvioi ulkoiset datasetit niiden myrkyttämisen, vinoutumisen ja lainsäädännön noudattamisen varalta, ja seuraa niitä koko niiden elinkaaren ajan.

|   #   | Kuvaus                                                                                                                                          | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.5.1 | Varmista, että ulkoiset aineistot käyvät läpi myrkyttämisriskin pisteytyksen (esim. datan sormenjälkitunnistus, poikkeavuuksien havaitseminen). |  1   |  D/V  |
| 6.5.2 | Varmista, että puolueellisuusmittarit (demografinen tasapuolisuus, mahdollisuuksien tasa-arvo) lasketaan ennen datasetin hyväksyntää.           |  1   |   D   |
| 6.5.3 | Varmista, että datan alkuperä ja lisenssiehdot tallentuvat ML‑BOM-tietueisiin.                                                                  |  2   |   V   |
| 6.5.4 | Varmista, että säännöllinen seuranta havaitsee datan poikkeaman tai korruptoitumisen isännöidyissä tietojoukoissa.                              |  2   |   V   |
| 6.5.5 | Varmista, että kielletty sisältö (tekijänoikeudet, PII) poistetaan automaattisen puhdistuksen avulla ennen koulutusta.                          |  3   |   D   |

---

## C6.6 Toimitusketjun hyökkäysten seuranta

Havaitse toimitusketjun uhkat varhain CVE‑syötteiden, audit‑lokien analytiikan ja red‑team-simulaatioiden avulla.

|   #   | Kuvaus                                                                                                                                                          | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.6.1 | Varmista, että CI/CD-auditlokit virtaavat SIEMin havaitsemiin epäilyttäviin pakettien noutoihin tai muokattuihin rakennusvaiheisiin liittyviin tapahtumiin.     |  1   |   V   |
| 6.6.2 | Varmista, että incident response -pelikirjat sisältävät palautusmenettelyt kompromettoituneille malleille tai kirjastoille.                                     |  2   |   D   |
| 6.6.3 | Varmista, että uhkatiedustelun rikastuttamisen tunnisteet viittaavat ML‑spesifisiin indikaattoreihin (esim. mallinmyrkytyksen IoCs) hälytyksen priorisoinnissa. |  3   |   V   |

---

## C6.7 ML‑BOM mallin artefaktit

Luo ja allekirjoita yksityiskohtaiset ML-spesifiset SBOM:t (ML‑BOM:t), jotta jälkikäyttäjät voivat vahvistaa komponenttien eheyden käyttöönoton aikana.

|   #   | Kuvaus                                                                                                                                         | Taso | Rooli |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.7.1 | Varmista, että jokainen malliartefakti julkaisee ML‑BOMin, joka listaa tietojoukot, painot, hyperparametrit ja lisenssit.                      |  1   |  D/V  |
| 6.7.2 | Varmista, että ML‑BOM:n generointi ja Cosignin allekirjoitus automatisoidaan CI:ssä ja että ne ovat pakollisia yhdistämiseen.                  |  1   |  D/V  |
| 6.7.3 | Varmista, että ML‑BOMin täydellisyystarkastukset epäonnistuttavat rakennusvaiheessa, jos jokin komponentin metatieto (hash, lisenssi) puuttuu. |  2   |   D   |
| 6.7.4 | Varmista, että downstream-kuluttajat voivat kysyä ML-BOM:eja API:n kautta validoidakseen tuodut mallit käyttöönoton yhteydessä.                |  2   |   V   |
| 6.7.5 | Varmista, että ML‑BOMit ovat versionhallinnassa ja niihin tehdään diff, jotta luvattomat muutokset voidaan havaita.                            |  3   |   V   |

---

## Lähteet

* [ML Supply Chain Compromise – MITRE ATLAS](https://misp-galaxy.org/mitre-atlas-attack-pattern/)
* [Supply‑chain Levels for Software Artifacts (SLSA)](https://slsa.dev/)
* [CycloneDX – Machine Learning Bill of Materials](https://cyclonedx.org/capabilities/mlbom/)
* [What is Data Poisoning? – SentinelOne](https://www.sentinelone.com/cybersecurity-101/cybersecurity/data-poisoning/)
* [Transfer Learning Attack – OWASP ML Security Top 10](https://owasp.org/www-project-machine-learning-security-top-10/docs/ML07_2023-Transfer_Learning_Attack)
* [AI Data Security Best Practices – CISA](https://www.cisa.gov/news-events/cybersecurity-advisories/aa25-142a)
* [Secure CI/CD Supply Chain – Sumo Logic](https://www.sumologic.com/blog/secure-azure-devops-github-supply-chain-attacks)
* [AI & Transparency: Protect ML Models – ReversingLabs](https://www.reversinglabs.com/blog/ai-and-transparency-how-ml-model-creators-can-protect-against-supply-chain-attacks)
* [SBOM Overview – CISA](https://www.cisa.gov/sbom)
* [Training Data Poisoning Guide – Lakera.ai](https://www.lakera.ai/blog/training-data-poisoning)
* [Dependency Pinning for Reproducible Python – Medium](https://medium.com/data-science-collective/guarantee-a-locked-reproducible-environment-with-every-python-run-c0e2bf19fb53)

