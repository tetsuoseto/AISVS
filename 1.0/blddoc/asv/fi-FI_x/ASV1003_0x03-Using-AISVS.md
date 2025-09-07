# AISVS:n käyttäminen

Keinoälyn turvallisuusvarmennusstandardi (AISVS) määrittelee turvallisuusvaatimukset nykyaikaisille tekoälysovelluksille ja -palveluille, keskittyen sovelluskehittäjien hallinnassa oleviin näkökohtiin.

AISVS on tarkoitettu kaikille, jotka kehittävät tai arvioivat tekoälysovellusten turvallisuutta, mukaan lukien kehittäjät, arkkitehdit, tietoturva-asiantuntijat ja tarkastajat. Tämä luku esittelee AISVS:n rakenteen ja käytön, mukaan lukien sen varmistustasot ja suunnitellut käyttötapaukset.

## Tekoälyn turvallisuuden varmistuksen tasot

AISVS määrittelee kolme nousevaa turvallisuuden varmistustasoa. Jokainen taso lisää syvyyttä ja monimutkaisuutta, mikä mahdollistaa organisaatioiden mukauttaa turvallisuusasetuksensa AI-järjestelmiensä riskitasoon.

Organisaatiot voivat aloittaa tasolta 1 ja ottaa asteittain käyttöön korkeampia tasoja tietoturvan kypsyttyä ja uhkien lisääntyessä.

### Tasoille määritelmä

Jokainen AISVS v1.0 -version vaatimus on määritelty yhteen seuraavista tasoista:

#### Tason 1 vaatimukset

Taso 1 sisältää kriittisimmät ja perustavanlaatuisimmat tietoturvavaatimukset. Ne keskittyvät estämään yleisiä hyökkäyksiä, jotka eivät perustu muihin esiehtoihin tai haavoittuvuuksiin. Suurin osa tason 1 valvontatoimenpiteistä on joko helppoja toteuttaa tai riittävän tärkeitä vaivan oikeuttamiseksi.

#### Taso 2 vaatimukset

Taso 2 käsittelee edistyneempiä tai harvinaisempia hyökkäyksiä sekä kerrostettuja puolustuksia laajalle levinneitä uhkia vastaan. Nämä vaatimukset voivat sisältää monimutkaisempaa logiikkaa tai kohdistua tiettyihin hyökkäysehtoon.

#### Tason 3 vaatimukset

Taso 3 sisältää ohjauskeinoja, joiden toteuttaminen on tyypillisesti vaikeampaa tai jotka soveltuvat tilanteisiin. Ne edustavat usein syvyyspuolustuksen mekanismeja tai lieventäviä toimenpiteitä harvinaisia, kohdennettuja tai korkean monimutkaisuuden hyökkäyksiä vastaan.

### Rooli (D/V)

Jokainen AISVS-vaatimus on merkitty ensisijaisen kohdeyleisön mukaan:

* D – Kehittäjäkeskeiset vaatimukset
* V – Varmennukseen/tarkastukseen keskittyvät vaatimukset
* D/V – Tärkeä sekä kehittäjille että tarkistajille

