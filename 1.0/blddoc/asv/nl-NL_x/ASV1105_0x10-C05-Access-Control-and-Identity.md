# C5 Toegangscontrole en Identiteit voor AI-componenten en Gebruikers

## Beheersdoel

Effectieve toegangscontrole voor AI-systemen vereist robuust identiteitsbeheer, contextbewuste autorisatie en runtime-handhaving volgens de principes van zero-trust. Deze controles zorgen ervoor dat mensen, diensten en autonome agenten alleen interageren met modellen, gegevens en rekenbronnen binnen expliciet toegekende toegangsrechten, met voortdurende verificatie- en auditmogelijkheden.

---

## C5.1 Identiteitsbeheer en authenticatie

Implementeer cryptografisch onderbouwde identiteiten voor alle entiteiten met multifactorauthenticatie voor bevoorrechte operaties.

|   #   | Beschrijving                                                                                                                                                                                                                                                                       | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.1.1 | Controleer dat alle menselijke gebruikers en service principals zich authenticeren via een gecentraliseerde ondernemingsidentiteitsprovider (IdP) die OIDC/SAML-protocollen gebruikt, met unieke koppelingen tussen identiteit en token (geen gedeelde accounts of inloggegevens). |   1    | D/V |
| 5.1.2 | Verifieer dat operaties met hoog risico (modeluitrol, gewichtsexport, toegang tot trainingsgegevens, wijzigingen in productieconfiguratie) multifactorauthenticatie of stap-gewijze authenticatie met sessie-herverificatie vereisen.                                              |   1    | D/V |
| 5.1.3 | Verifieer dat nieuwe entiteiten een identiteitsverificatie ondergaan die is afgestemd op NIST 800-63-3 IAL-2 of vergelijkbare standaarden, voordat zij toegang krijgen tot het productiesysteem.                                                                                   |   2    |  D  |
| 5.1.4 | Controleer of toegangsbeoordelingen elk kwartaal worden uitgevoerd met geautomatiseerde detectie van inactieve accounts, afdwinging van rotatie van referenties en workflows voor deprovisioning.                                                                                  |   2    |  V  |
| 5.1.5 | Verifieer dat gefedereerde AI-agenten zich authenticeren via ondertekende JWT-verklaringen die een maximale geldigheidsduur van 24 uur hebben en cryptografisch bewijs van oorsprong bevatten.                                                                                     |   3    | D/V |

---

## C5.2 Middelenautorisatie & Minimale toegangsrechten

Implementeer granulaire toegangscontroles voor alle AI-bronnen met expliciete machtigingsmodellen en auditsporen.

|   #   | Beschrijving                                                                                                                                                                                                                           | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.2.1 | Controleer of elke AI-bron (datasets, modellen, eindpunten, vectorverzamelingen, embedding-indexen, compute-instanties) rolgebaseerde toegangscontroles afdwingt met expliciete toestemmingslijsten en standaard-weigeringsbeleid.     |   1    | D/V |
| 5.2.2 | Controleer dat het principe van minimale rechten standaard wordt toegepast, met service-accounts die beginnen bij alleen-lezen machtigingen en dat voor schrijftoegang een gedocumenteerde zakelijke rechtvaardiging vereist is.       |   1    | D/V |
| 5.2.3 | Verifieer dat alle wijzigingen in toegangscontrole zijn gekoppeld aan goedgekeurde wijzigingsverzoeken en onveranderlijk worden vastgelegd met tijdstempels, identiteiten van acteurs, resource-identificatoren en rechtenwijzigingen. |   1    |  V  |
| 5.2.4 | Verifieer dat gegevensclassificatielabels (PII, PHI, export-controlled, proprietary) automatisch doorstromen naar afgeleide bronnen (embeddings, prompt caches, modeluitgangen) met consistente beleidshandhaving.                     |   2    |  D  |
| 5.2.5 | Verifieer dat onbevoegde toegangspogingen en privilege-escalatiegebeurtenissen real-time waarschuwingen activeren met contextuele metadata naar SIEM-systemen binnen 5 minuten.                                                        |   2    | D/V |

---

## C5.3 Dynamische beleidsbeoordeling

Implementeer attribuut-gebaseerde toegangscontrole (ABAC) engines voor context-gevoelige autorisatiebeslissingen met auditmogelijkheden.

|   #   | Beschrijving                                                                                                                                                                                                                                | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.3.1 | Controleer of autorisatiebeslissingen extern worden ondergebracht bij een toegewijde beleidsmotor (OPA, Cedar, of een gelijkwaardige oplossing) die toegankelijk is via geauthenticeerde API's met cryptografische integriteitsbescherming. |   1    | D/V |
| 5.3.2 | Verifieer dat beleidsregels dynamische attributen tijdens uitvoering evalueren, inclusief gebruikerstoegangsniveau, classificatie van de gevoeligheid van bronnen, verzoekcontext, tenant-isolatie en tijdgebonden beperkingen.             |   1    | D/V |
| 5.3.3 | Verifieer dat beleidsdefinities onder versiebeheer staan, door vakgenoten beoordeeld zijn en gevalideerd worden via geautomatiseerd testen in CI/CD-pijplijnen vóór productie-uitrol.                                                       |   2    |  D  |
| 5.3.4 | Verifieer dat de resultaten van de beleidsbeoordeling gestructureerde besluitvormingsredenen bevatten en dat deze worden verzonden naar SIEM-systemen voor correlatieanalyse en conformiteitsrapportage.                                    |   2    |  V  |
| 5.3.5 | Controleer dat de TTL-waarden van de beleid-cache niet hoger zijn dan 5 minuten voor bronnen met hoge gevoeligheid en 1 uur voor standaardbronnen met cache-invalidatiecapaciteiten.                                                        |   3    | D/V |

---

## C5.4 Query-Tijd Beveiligingsafdwinging

Implementeer beveiligingscontroles op database-layer met verplichte filtering en rijniveau-beveiligingsbeleid.

|   #   | Beschrijving                                                                                                                                                                                                                               | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 5.4.1 | Verifieer dat alle vector-databases en SQL-query's verplichte beveiligingsfilters bevatten (tenant-ID, sensitiviteitslabels, gebruikersreikwijdte) die op het niveau van de database-engine worden gehandhaafd, niet in de applicatiecode. |   1    | D/V |
| 5.4.2 | Controleer of RLS-beleidslijnen en veldniveau-maskering zijn ingeschakeld met beleidsovererving voor alle vectordatabases, zoekindexen en trainingsdatasets.                                                                               |   1    | D/V |
| 5.4.3 | Verifieer dat mislukte autorisatie-evaluaties voorkomen dat 'verwarde plaatsvervanger-aanvallen' optreden door queries onmiddellijk af te breken en expliciete autorisatiefoutcodes terug te geven in plaats van lege resultsets.          |   2    |  D  |
| 5.4.4 | Controleer of de latentie bij beleidsbeoordeling continu wordt gemonitord met geautomatiseerde meldingen voor time-outcondities die autorisatie-omzeiling mogelijk kunnen maken.                                                           |   2    |  V  |
| 5.4.5 | Controleer of query-herhaalmechanismen het autorisatiebeleid opnieuw evalueren om rekening te houden met dynamische machtigingswijzigingen tijdens actieve gebruikerssessies.                                                              |   3    | D/V |

---

## C5.5 Uitvoerfiltering & Gegevensverliespreventie

Implementeer nabewerkingcontroles om ongeautoriseerde blootstelling van gegevens te voorkomen in door kunstmatige intelligentie gegenereerde inhoud.

|   #   | Beschrijving                                                                                                                                                                                                                 | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.5.1 | Controleer of de na-inferentiefilters ongeautoriseerde PII, geclassificeerde informatie en eigen gegevens scannen en redigeren voordat de inhoud aan verzoekers wordt geleverd.                                              |   1    | D/V |
| 5.5.2 | Verifieer dat citaten, referenties en bronvermeldingen in de uitvoer van het model worden gevalideerd tegen de rechten van de aanroeper en verwijderd indien ongeautoriseerde toegang wordt gedetecteerd.                    |   1    | D/V |
| 5.5.3 | Controleer of de beperkingen op uitvoerformaten (geschoonde PDF's, afbeeldingen zonder metadata, goedgekeurde bestandstypen) worden gehandhaafd op basis van de machtigingsniveaus van gebruikers en gegevensclassificaties. |   2    |  D  |
| 5.5.4 | Verifieer dat anonimisering-algoritmen deterministisch zijn, onder versiecontrole staan, en auditlogs bijhouden ter ondersteuning van nalevingsonderzoeken en forensische analyse.                                           |   2    |  V  |
| 5.5.5 | Controleer of hoog-risico-redactiegebeurtenissen adaptieve logbestanden genereren die cryptografische hash-waarden van de oorspronkelijke inhoud bevatten voor forensisch terugvinden zonder gegevensblootstelling.          |   3    |  V  |

---

## C5.6 Multi-Tenant Isolatie

Zorg voor cryptografische en logische isolatie tussen huurders in een gedeelde AI-infrastructuur.

|   #   | Beschrijving                                                                                                                                                                                                | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.6.1 | Verifieer dat geheugenruimten, embedding-opslagen, cache-items en tijdelijke bestanden per tenant zijn gescheiden in namespaces en dat ze bij tenantverwijdering of sessiebeëindiging veilig worden gewist. |   1    | D/V |
| 5.6.2 | Controleer dat elke API-aanvraag een geauthenticeerde tenant-id bevat die cryptografisch wordt gevalideerd tegen de sessiecontext en de rechten van de gebruiker.                                           |   1    | D/V |
| 5.6.3 | Verifieer dat netwerkbeleid standaard-deny-regels implementeert voor communicatie tussen tenants binnen servicemeshes en containerorkestratieplatforms.                                                     |   2    |  D  |
| 5.6.4 | Verifieer dat versleutelingssleutels per huurder uniek zijn, met ondersteuning voor klant-beheerde sleutels (CMK) en cryptografische isolatie tussen huurdersgegevensopslagen.                              |   3    |  D  |

---

## C5.7 Autonome agentmachtiging

Beheer machtigingen voor AI-agenten en autonome systemen via afgebakende bevoegdheidstokens en doorlopende autorisatie.

|   #   | Beschrijving                                                                                                                                                                                                                                              | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 5.7.1 | Controleer dat autonome agenten omschreven machtigingstokens ontvangen die expliciet de toegestane acties, toegankelijke bronnen, tijdslimieten en operationele beperkingen specificeren.                                                                 |   1    | D/V |
| 5.7.2 | Verifieer dat hoogrisico-mogelijkheden (toegang tot het bestandssysteem, code-uitvoering, externe API-aanroepen, financiële transacties) standaard zijn uitgeschakeld en expliciete autorisaties vereisen voor activatie met zakelijke rechtvaardigingen. |   1    | D/V |
| 5.7.3 | Verifieer dat capability tokens aan gebruikerssessies zijn gebonden, cryptografische integriteitsbescherming bieden en voorkomen dat ze worden opgeslagen of hergebruikt in offline scenario's.                                                           |   2    |  D  |
| 5.7.4 | Verifieer dat acties die door een agent zijn geïnitieerd onderworpen zijn aan secundaire autorisatie via de ABAC-beleidsmotor met volledige contextevaluatie en auditlogging.                                                                             |   2    |  V  |
| 5.7.5 | Verifieer dat de foutcondities van de agent en de foutafhandeling informatie bevatten over de reikwijdte van de mogelijkheden ter ondersteuning van incidentanalyse en forensisch onderzoek.                                                              |   3    |  V  |

---

## Referenties

### Standaarden & Raamwerken

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

