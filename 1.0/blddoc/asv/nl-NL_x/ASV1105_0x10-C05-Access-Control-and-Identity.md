# C5 Toegangscontrole & Identiteit voor AI-componenten & gebruikers

## Beheersingsdoelstelling

Effectieve toegangscontrole voor AI-systemen vereist robuust identiteitsbeheer, contextbewuste autorisatie en runtime handhaving volgens zero-trust principes. Deze controles zorgen ervoor dat mensen, services en autonome agenten alleen interactie hebben met modellen, data en rekenmiddelen binnen expliciet toegewezen reikwijdtes, met continue verificatie- en auditmogelijkheden.

---

## C5.1 Identiteitsbeheer & Authenticatie

Stel cryptografisch ondersteunde identiteiten in voor alle entiteiten met multi-factor authenticatie voor bevoorrechte handelingen.

|   #   | Beschrijving                                                                                                                                                                                                                                                     | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.1.1 | Controleer of alle menselijke gebruikers en serviceprincipals zich authenticeren via een gecentraliseerde enterprise identity provider (IdP) met behulp van OIDC/SAML-protocollen met unieke identity-to-token mappings (geen gedeelde accounts of referenties). |   1    | D/V |
| 5.1.2 | Controleer of risicovolle handelingen (modelimplementatie, export van gewichten, toegang tot trainingsgegevens, wijzigingen in productieconfiguraties) multi-factor authenticatie of step-up authenticatie met sessiehervalidatie vereisen.                      |   1    | D/V |
| 5.1.3 | Verifieer dat nieuwe principals een identiteitstoetsing ondergaan die overeenkomt met NIST 800-63-3 IAL-2 of gelijkwaardige standaarden voordat zij toegang krijgen tot het productiesysteem.                                                                    |   2    |  D  |
| 5.1.4 | Controleer of toegangsbeoordelingen elk kwartaal worden uitgevoerd met geautomatiseerde detectie van inactieve accounts, afdwinging van wachtwoordrotatie en workflows voor het intrekken van toegang.                                                           |   2    |  V  |
| 5.1.5 | Verifieer dat gefedereerde AI-agenten zich authenticeren via ondertekende JWT-asserties die een maximale levensduur van 24 uur hebben en cryptografisch bewijs van oorsprong bevatten.                                                                           |   3    | D/V |

---

## C5.2 Brontoestemming & Minimaal Privilege

Implementeer fijnmazige toegangscontroles voor alle AI-middelen met expliciete toestemmingsmodellen en controlelogboeken.

|   #   | Beschrijving                                                                                                                                                                                                                             | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.2.1 | Controleer of elke AI-bron (datasets, modellen, endpoints, vectorverzamelingen, embed-indexen, compute-instanties) rolgebaseerde toegangscontroles afdwingt met expliciete toestemmingslijsten en standaard-weigerbeleid.                |   1    | D/V |
| 5.2.2 | Verifieer dat het principe van minste-privilege standaard wordt afgedwongen bij serviceaccounts, te beginnen met alleen-lezen machtigingen en dat een gedocumenteerde zakelijke rechtvaardiging vereist is voor schrijfaccess.           |   1    | D/V |
| 5.2.3 | Controleer of alle wijzigingen in de toegangscontrole gekoppeld zijn aan goedgekeurde wijzigingsverzoeken en onveranderlijk zijn vastgelegd met tijdstempels, identiteiten van actoren, resource-identificaties en permissieverschillen. |   1    |  V  |
| 5.2.4 | Controleer of dataclassificatielabels (PII, PHI, exportbeperkt, eigendom) automatisch worden doorgegeven aan afgeleide bronnen (embeddings, promptcaches, modeluitvoer) met consistente beleidsafhandeling.                              |   2    |  D  |
| 5.2.5 | Controleer of pogingen tot onbevoegde toegang en privilege-escalatiegebeurtenissen binnen 5 minuten realtime waarschuwingen met contextuele metadata naar SIEM-systemen verzenden.                                                       |   2    | D/V |

---

## C5.3 Dynamische beleidsevaluatie

Implementeer attribute-based access control (ABAC) engines voor contextbewuste autorisatiebeslissingen met auditmogelijkheden.

|   #   | Beschrijving                                                                                                                                                                                                                                     | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 5.3.1 | Controleer of autorisatiebeslissingen zijn uitbesteed aan een speciale beleidsengine (OPA, Cedar of equivalent) die toegankelijk is via geverifieerde API's met cryptografische integriteitsbescherming.                                         |   1    | D/V |
| 5.3.2 | Controleer of beleidsregels dynamische attributen evalueren tijdens runtime, waaronder het beveiligingsniveau van de gebruiker, de gevoeligheidsclassificatie van de bron, de context van het verzoek, tenant-isolatie en temporele beperkingen. |   1    | D/V |
| 5.3.3 | Verifieer dat beleidsdefinities versiebeheer hebben, door collega's zijn beoordeeld en gevalideerd worden via geautomatiseerde tests in CI/CD-pijplijnen voordat ze in productie worden ingezet.                                                 |   2    |  D  |
| 5.3.4 | Verifieer dat de resultaten van beleidsbeoordeling gestructureerde besluitvormingsredenen bevatten en worden verzonden naar SIEM-systemen voor correlatieanalyse en nalevingsrapportage.                                                         |   2    |  V  |
| 5.3.5 | Controleer of de time-to-live (TTL) waarden van het beleidscache de 5 minuten niet overschrijden voor hooggevoelige bronnen en 1 uur voor standaardbronnen met cache-invalideringsmogelijkheden.                                                 |   3    | D/V |

---

## C5.4 Beveiligingshandhaving tijdens query-uitvoering

Implementeer beveiligingscontroles op databaselaag met verplichte filtering en beveiligingsbeleid op rijniveau.

|   #   | Beschrijving                                                                                                                                                                                                                         | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 5.4.1 | Verifieer dat alle vector database- en SQL-query's verplichte beveiligingsfilters bevatten (tenant-ID, gevoeligheidslabels, gebruikersscope) die worden afgedwongen op het niveau van de database-engine, niet in de applicatiecode. |   1    | D/V |
| 5.4.2 | Controleer of row-level security (RLS)-beleid en veldniveau-maskering met beleids-erfenis zijn ingeschakeld voor alle vector-databases, zoekindexen en trainingsdatasets.                                                            |   1    | D/V |
| 5.4.3 | Verifieer dat mislukte autorisatie-evaluaties "confused deputy-aanvallen" voorkomen door queries onmiddellijk te stoppen en expliciete autorisatiefoutcodes terug te geven in plaats van lege resultaatsets te retourneren.          |   2    |  D  |
| 5.4.4 | Controleer of de beleidsbeoordelingsvertraging continu wordt gemonitord met geautomatiseerde waarschuwingen voor time-outvoorwaarden die een omzeiling van autorisatie mogelijk kunnen maken.                                        |   2    |  V  |
| 5.4.5 | Controleer of query-herhaalmethoden autorisatiebeleid opnieuw evalueren om rekening te houden met dynamische permissiewijzigingen binnen actieve gebruikerssessies.                                                                  |   3    | D/V |

---

## C5.5 Uitvoerfiltering & Gegevensverliespreventie

Implementeer nabehandelingscontroles om ongeautoriseerde blootstelling van gegevens in door AI gegenereerde inhoud te voorkomen.

|   #   | Beschrijving                                                                                                                                                                                                              | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.5.1 | Verifieer dat mechanismen voor filtering na inferentie ongeautoriseerde PII, geclassificeerde informatie en eigendomsgegevens scannen en schrappen voordat de inhoud aan verzoekers wordt geleverd.                       |   1    | D/V |
| 5.5.2 | Controleer of citaties, referenties en bronvermeldingen in modeluitvoer worden geverifieerd aan de hand van caller-autoriteiten en verwijder deze indien onbevoegde toegang wordt gedetecteerd.                           |   1    | D/V |
| 5.5.3 | Controleer of de beperkingen voor uitvoerformaten (gesaniteerde PDF's, met metadata ontdane afbeeldingen, goedgekeurde bestandstypen) worden gehandhaafd op basis van gebruikersmachtigingsniveaus en dataclassificaties. |   2    |  D  |
| 5.5.4 | Controleer of redactie-algoritmen deterministisch zijn, versiebeheer hebben en auditlogboeken bijhouden om compliance-onderzoeken en forensische analyses te ondersteunen.                                                |   2    |  V  |
| 5.5.5 | Verifieer dat hoge-risico redactie-evenementen adaptieve logs genereren die cryptografische hashes van de originele inhoud bevatten voor forensische terughaalbaarheid zonder datagebruik.                                |   3    |  V  |

---

## C5.6 Multi-Tenant Isolatie

Zorg voor cryptografische en logische isolatie tussen huurders in gedeelde AI-infrastructuur.

|   #   | Beschrijving                                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.6.1 | Controleer of geheugenruimtes, embedding-opslag, cache-items en tijdelijke bestanden gescheiden zijn per namespace per huurder, met veilige verwijdering bij het verwijderen van de huurder of het beëindigen van de sessie. |   1    | D/V |
| 5.6.2 | Controleer of elke API-aanvraag een geverifieerde tenant-identificatie bevat die cryptografisch wordt gevalideerd aan de hand van de sessiecontext en gebruikersrechten.                                                     |   1    | D/V |
| 5.6.3 | Verifieer dat netwerkbeleid standaard-weigerregels implementeert voor communicatie tussen verschillende tenants binnen servicenetwerken en containerorchestratietools.                                                       |   2    |  D  |
| 5.6.4 | Verifieer dat encryptiesleutels uniek zijn per tenant met ondersteuning voor door de klant beheerde sleutels (CMK) en cryptografische isolatie tussen tenant-datastores.                                                     |   3    |  D  |

---

## C5.7 Autorisatie van autonome agenten

Beheer toestemming voor AI-agents en autonome systemen via gescopeerde capaciteits tokens en continue autorisatie.

|   #   | Beschrijving                                                                                                                                                                                                                                          | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.7.1 | Controleer of autonome agenten gescopeerde capability-tokens ontvangen die expliciet de toegestane acties, toegankelijke bronnen, tijdsgrenzen en operationele beperkingen opsommen.                                                                  |   1    | D/V |
| 5.7.2 | Controleer of hoog-risico functies (toegang tot het bestandssysteem, code-uitvoering, externe API-aanroepen, financiële transacties) standaard zijn uitgeschakeld en expliciete autorisaties vereisen voor activatie met zakelijke rechtvaardigingen. |   1    | D/V |
| 5.7.3 | Verifieer dat capaciteitstokens gebonden zijn aan gebruikerssessies, cryptografische integriteitsbescherming bevatten, en zorg ervoor dat ze niet kunnen worden opgeslagen of hergebruikt in offline scenario's.                                      |   2    |  D  |
| 5.7.4 | Verifieer dat door agent geïnitieerde acties een secundaire autorisatie ondergaan via de ABAC-beleidsengine met volledige contextevaluatie en auditlogboeken.                                                                                         |   2    |  V  |
| 5.7.5 | Controleer of foutcondities van agenten en uitzonderingafhandeling informatie over het capaciteitsbereik bevatten om ondersteuning te bieden bij incidentenanalyse en forensisch onderzoek.                                                           |   3    |  V  |

---

## Referenties

### Normen & Kaders

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Implementatiehandleidingen

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### AI-specifieke beveiliging

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

