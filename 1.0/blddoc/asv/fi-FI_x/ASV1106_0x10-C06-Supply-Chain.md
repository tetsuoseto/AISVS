# C6 Toimitusketjun turvallisuus malleille, kehyksille ja tiedoille

## Ohjaustavoite

AI-toimitusketjun hyökkäykset hyödyntävät kolmannen osapuolen malleja, kehyksiä tai aineistoja takaporttien, vinoumien tai hyväksikäytettävän koodin upottamiseen. Nämä valvontatoimet tarjoavat alusta loppuun jäljitettävyyden, haavoittuvuuksien hallinnan ja valvonnan koko mallin elinkaaren suojaamiseksi.

---

## C6.1 Esikoulutetun mallin arviointi ja alkuperä

Arvioi ja vahvista kolmannen osapuolen mallien alkuperä, lisenssit ja piilotetut käyttäytymismallit ennen hienosäätöä tai käyttöönottoa.

|   #   | Kuvaus                                                                                                                                                               | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.1.1 | Varmista, että jokainen kolmannen osapuolen mallin artefakti sisältää allekirjoitetun alkuperätietueen, jossa on tunnistettu lähderekisteri ja commit-tunniste.      |  1   |  D/V  |
| 6.1.2 | Varmista, että mallit tarkastetaan haitallisten kerrosten tai Troijan laukaisijoiden varalta automatisoiduilla työkaluilla ennen niiden tuontia.                     |  1   |  D/V  |
| 6.1.3 | Varmista, että siirto-oppiminen hienosäätää mallit siten, että ne läpäisevät hyökkäystestauksen havaitakseen piilotetut käyttäytymismallit.                          |  2   |   D   |
| 6.1.4 | Varmista, että mallilisenssit, vientivalvontatunnisteet ja datan alkuperää koskevat lausunnot on kirjattu ML-BOM-kohteeseen.                                         |  2   |   V   |
| 6.1.5 | Varmista, että korkean riskin mallit (julkisesti ladatut painot, varmennamattomat luojat) pysyvät karanteenissa ihmisen tekemään tarkastukseen ja hyväksyntään asti. |  3   |  D/V  |

---

## C6.2 Kehys- ja kirjastojen skannaus

Skannaa jatkuvasti ML-kehykset ja kirjastot CVE-haavoittuvuuksien ja haitallisen koodin varalta pitämään ajonaikainen pino turvallisena.

|   #   | Kuvaus                                                                                                                                             | Taso | Rooli |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.2.1 | Varmista, että CI-putket suorittavat riippuvuusskannereita tekoälykehysten ja kriittisten kirjastojen kohdalla.                                    |  1   |  D/V  |
| 6.2.2 | Varmista, että kriittiset haavoittuvuudet (CVSS ≥ 7.0) estävät päivityksen tuotantokuviksi.                                                        |  1   |  D/V  |
| 6.2.3 | Varmista, että staattinen koodianalyysi suoritetaan haara- tai mukana toimitetuille koneoppimiskirjastoille.                                       |  2   |   D   |
| 6.2.4 | Varmista, että kehysupgrade-ehdotukset sisältävät tietoturvan vaikutusten arvioinnin, joka viittaa julkisiin CVE-syötteisiin.                      |  2   |   V   |
| 6.2.5 | Varmista, että ajonaikaiset anturit hälyttävät odottamattomista dynaamisista kirjastojen latauksista, jotka poikkeavat allekirjoitetusta SBOM:sta. |  3   |   V   |

---

## C6.3 Riippuvuuksien lukitseminen ja varmennus

Kiinnitä kaikki riippuvuudet muuttumattomiin tiivisteisiin ja toista käännökset varmistaaksesi identtiset, muokkaamattomat artefaktit.

|   #   | Kuvaus                                                                                                                            | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.3.1 | Varmista, että kaikki pakettienhallintaohjelmat pakottavat version lukituksen lukitustiedostojen kautta.                          |  1   |  D/V  |
| 6.3.2 | Varmista, että konttiviitteissä käytetään muuttumattomia tiivisteitä muuttuvien tunnisteiden sijaan.                              |  1   |  D/V  |
| 6.3.3 | Varmista, että toistettavat rakennustarkistukset vertaavat hajautusarvoja CI-ajojen välillä identtisten tulosten varmistamiseksi. |  2   |   D   |
| 6.3.4 | Varmista, että rakennusvakuutukset säilytetään 18 kuukautta auditointijäljityksen varmistamiseksi.                                |  2   |   V   |
| 6.3.5 | Varmista, että vanhentuneet riippuvuudet laukaisevat automaattiset PR:t päivittääksesi tai haaroittaaksesi kiinnitetyt versiot.   |  3   |   D   |

---

## C6.4 Luotettavan lähteen valvonta

Salli artefaktien lataukset vain kryptografisesti varmennetuista, organisaation hyväksymistä lähteistä ja estä kaikki muu.

|   #   | Kuvaus                                                                                                                                              | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.4.1 | Varmista, että mallipainot, tietojoukot ja kontit ladataan vain hyväksytyiltä verkkotunnuksilta tai sisäisistä rekistereistä.                       |  1   |  D/V  |
| 6.4.2 | Varmista, että Sigstore/Cosign-allekirjoitukset vahvistavat julkaisijan identiteetin ennen kuin artefaktit tallennetaan paikallisesti välimuistiin. |  1   |  D/V  |
| 6.4.3 | Varmista, että ulospäin suuntautuvat välityspalvelimet estävät todennuksettomat artefaktien lataukset luotetun lähdepolitiikan noudattamiseksi.     |  2   |   D   |
| 6.4.4 | Varmista, että arkistoluettelot tarkistetaan neljännesvuosittain ja että jokaiselle merkinnälle on liiketoiminnallinen perustelu.                   |  2   |   V   |
| 6.4.5 | Varmista, että politiikan rikkomukset laukaisevat artefaktien karanteenin ja riippuvien putkistosuoritusten palautuksen.                            |  3   |   V   |

---

## C6.5 Kolmannen osapuolen tietojoukkoa koskeva riskinarviointi

Arvioi ulkoiset tietoaineistot myrkyllisyyden, harhan ja laillisen vaatimustenmukaisuuden osalta ja valvo niitä koko niiden elinkaaren ajan.

|   #   | Kuvaus                                                                                                                                        | Taso | Rooli |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.5.1 | Varmista, että ulkoiset tietojoukot käyvät läpi myrkytysriskiarvioinnin (esim. datansormenjälkien luonti, poikkeavien arvojen havaitseminen). |  1   |  D/V  |
| 6.5.2 | Varmista, että puolueellisuusmittarit (demografinen tasapuolisuus, yhtäläinen mahdollisuus) lasketaan ennen tietojoukon hyväksyntää.          |  1   |   D   |
| 6.5.3 | Varmista, että tietojoukkeiden alkuperä ja lisenssiehdot on tallennettu ML-BOM-tietoihin.                                                     |  2   |   V   |
| 6.5.4 | Varmista, että säännöllinen seuranta havaitsee muutokset tai vääristymät isännöidyissä tietoaineistoissa.                                     |  2   |   V   |
| 6.5.5 | Varmista, että kielletty sisältö (tekijänoikeudet, henkilötunnistetiedot) poistetaan automaattisella puhdistuksella ennen koulutusta.         |  3   |   D   |

---

## C6.6 Toimitusketjun hyökkäysten seuranta

Havaitse toimitusketjun uhkat varhain CVE-syötteiden, tarkastuslokianalytiikan ja red-tiimin simulaatioiden avulla.

|   #   | Kuvaus                                                                                                                                                | Taso | Rooli |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.6.1 | Varmista, että CI/CD-tarkastuslokit virtaavat SIEM-havaintoihin epätavallisten paketinkuittausten tai muunneltujen rakennusvaiheiden havaitsemiseksi. |  1   |   V   |
| 6.6.2 | Varmista, että tapahtumien käsittelyohjeissa on mukana palautusmenettelyt vaarantuneille malleille tai kirjastoille.                                  |  2   |   D   |
| 6.6.3 | Varmista, että uhkatiedon rikastustunnisteet merkitsevät ML-spesifiset indikaattorit (esim. mallin myrkytys IoC:t) hälytyksen seulonnassa.            |  3   |   V   |

---

## C6.7 ML‑BOM mallin artefakteille

Luo ja allekirjoita yksityiskohtaiset koneoppimiseen liittyvät SBOM:t (ML-BOM:t), jotta loppukäyttäjät voivat varmistaa komponenttien eheyden käyttöönoton yhteydessä.

|   #   | Kuvaus                                                                                                                                            | Taso | Rooli |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 6.7.1 | Varmista, että jokainen mallin artefakti julkaisee ML-BOM:n, joka sisältää luettelon aineistoista, painoista, hyperparametreista ja lisensseistä. |  1   |  D/V  |
| 6.7.2 | Varmista, että ML-BOM:n luonti ja Cosign-allekirjoitus ovat automatisoituja CI:ssä ja pakollisia merge-yhdistämiselle.                            |  1   |  D/V  |
| 6.7.3 | Varmista, että ML‑BOM:n täydellisyystarkistukset epäonnistavat käännön, jos jokin komponentin metatiedoista (hash, lisenssi) puuttuu.             |  2   |   D   |
| 6.7.4 | Varmista, että alavirran käyttäjät voivat kysellä ML-BOM:eja API:n kautta validoidakseen tuotavat mallit käyttöönoton yhteydessä.                 |  2   |   V   |
| 6.7.5 | Varmista, että ML-BOMit ovat versionhallinnassa ja muutokset vertaillaan luvattomien muokkausten havaitsemiseksi.                                 |  3   |   V   |

---

## Viitteet

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

