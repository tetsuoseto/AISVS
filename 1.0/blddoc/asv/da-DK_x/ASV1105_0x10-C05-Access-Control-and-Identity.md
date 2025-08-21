# C5 Adgangskontrol og identitet for AI-komponenter og brugere

## Kontrolmål

Effektiv adgangskontrol for AI-systemer kræver robust identitetsstyring, kontekstbevidst autorisation og runtime-håndhævelse i overensstemmelse med zero-trust-principper. Disse kontroller sikrer, at mennesker, tjenester og autonome agenter kun interagerer med modeller, data og beregningsressourcer inden for eksplicit tildelte områder, med løbende verifikation og revisionsmuligheder.

---

## C5.1 Identitetsstyring og autentifikation

Etabler kryptografisk understøttede identiteter for alle enheder med multifaktorgodkendelse til privilegerede operationer.

|   #   | Beskrivelse                                                                                                                                                                                                                                                          | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.1.1 | Bekræft, at alle menneskelige brugere og serviceprincipaler godkendes gennem en centraliseret virksomhedsidentitetsudbyder (IdP) ved brug af OIDC/SAML-protokoller med unikke identitets-til-token-tilknytninger (ingen delte konti eller legitimationsoplysninger). |   1    |  D/V  |
| 5.1.2 | Bekræft, at højrisikooperationer (modelimplementering, vægtekspor, adgang til træningsdata, produktionskonfigurationsændringer) kræver multifaktorautentificering eller trin-op-autentificering med sessiongensvalidering.                                           |   1    |  D/V  |
| 5.1.3 | Bekræft, at nye principper gennemgår identitetsverificering, der er i overensstemmelse med NIST 800-63-3 IAL-2 eller tilsvarende standarder, før de får adgang til produktionssystemet.                                                                              |   2    |   D   |
| 5.1.4 | Bekræft, at adgangsgennemgange udføres kvartalsvis med automatisk detektion af inaktive konti, håndhævelse af adgangsoplysningerotation og arbejdsprocesser for de-provisionering.                                                                                   |   2    |   V   |
| 5.1.5 | Bekræft, at fødererede AI-agenter autentificerer via underskrevne JWT-påstande, der har en maksimal levetid på 24 timer og indeholder kryptografisk bevis for oprindelse.                                                                                            |   3    |  D/V  |

---

## C5.2 Ressourceautorisation & mindst privilegium

Implementer detaljerede adgangskontroller for alle AI-ressourcer med eksplicitte tilladelsesmodeller og revisionsspor.

|   #   | Beskrivelse                                                                                                                                                                                                                          | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 5.2.1 | Bekræft, at alle AI-ressourcer (datasæt, modeller, endpoints, vektorsamlinger, indlejringindekser, beregningsinstanser) håndhæver rollebaserede adgangskontroller med eksplicitte tilladelseslister og standardafvisningspolitikker. |   1    |  D/V  |
| 5.2.2 | Sørg for, at principperne om mindst mulige privilegier håndhæves som standard for servicekonti, startende med skrivebeskyttede tilladelser, og at der kræves dokumenteret forretningsmæssig begrundelse for skriveadgang.            |   1    |  D/V  |
| 5.2.3 | Bekræft, at alle ændringer i adgangskontrol er knyttet til godkendte ændringsanmodninger og logget uforanderligt med tidsstempler, aktøridentiteter, ressourceregistreringer og tilladelsesdifferencer.                              |   1    |   V   |
| 5.2.4 | Bekræft, at data klassifikationsmærker (PII, PHI, eksportkontrolleret, proprietær) automatisk overføres til afledte ressourcer (embedding, prompt caches, modeloutput) med konsekvent håndhævelse af politik.                        |   2    |   D   |
| 5.2.5 | Bekræft, at forsøg på uautoriseret adgang og hændelser med eskalering af privilegier udløser realtidsalarmer med kontekstuel metadata til SIEM-systemer inden for 5 minutter.                                                        |   2    |  D/V  |

---

## C5.3 Dynamisk politikvurdering

Implementer attributbaserede adgangskontrol (ABAC)-motorer til kontekstbevidste autorisationsbeslutninger med revisionsfunktioner.

|   #   | Beskrivelse                                                                                                                                                                                                              | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 5.3.1 | Bekræft, at autorisationsbeslutninger er eksternt placeret i en dedikeret politikmotor (OPA, Cedar eller tilsvarende), som er tilgængelig via autentificerede API'er med kryptografisk integritetsbeskyttelse.           |   1    |  D/V  |
| 5.3.2 | Bekræft, at politikker evaluerer dynamiske attributter ved kørselstidspunkt, herunder brugerens sikkerhedsklarering, ressourcefølsomhedsklassifikation, anmodningskontekst, lejerisolation og tidsmæssige begrænsninger. |   1    |  D/V  |
| 5.3.3 | Bekræft, at politikdefinitioner er versionsstyrede, peer-reviewed og validerede gennem automatiseret test i CI/CD-pipelines inden produktionsimplementering.                                                             |   2    |   D   |
| 5.3.4 | Bekræft, at politikvurderingsresultater inkluderer strukturerede beslutningsbegrundelser og overføres til SIEM-systemer til korrelationsanalyse og overholdelsesrapportering.                                            |   2    |   V   |
| 5.3.5 | Bekræft, at politikcachens time-to-live (TTL) værdier ikke overstiger 5 minutter for ressourcer med høj følsomhed og 1 time for standardressourcer med cache-ugyldiggørelsesfunktioner.                                  |   3    |  D/V  |

---

## C5.4 Sikkerhedshåndhævelse ved forespørgselstidspunktet

Implementer sikkerhedskontroller på databaseniveau med obligatorisk filtrering og politikker for række-niveau sikkerhed.

|   #   | Beskrivelse                                                                                                                                                                                                                       | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.4.1 | Bekræft, at alle vektordatabaser og SQL-forespørgsler inkluderer obligatoriske sikkerhedsfiltre (lejer-ID, følsomhedsetiketter, brugerområde), som håndhæves på databasmotor-niveau og ikke i applikationskoden.                  |   1    |  D/V  |
| 5.4.2 | Bekræft, at politikker for rækkebaseret sikkerhed (RLS) og maskering på feltniveau er aktiveret med politikarv for alle vektordatabaser, søgeindekser og træningsdatasæt.                                                         |   1    |  D/V  |
| 5.4.3 | Bekræft, at mislykkede autorisationsvurderinger forhindrer "forvirrede stedfortræder-angreb" ved straks at afbryde forespørgsler og returnere eksplicitte autorisationsfejlkoder i stedet for at returnere tomme resultatmængder. |   2    |   D   |
| 5.4.4 | Bekræft, at politikvurderingsforsinkelse løbende overvåges med automatiserede advarsler for timeout-betingelser, der kan muliggøre omgåelse af autorisation.                                                                      |   2    |   V   |
| 5.4.5 | Bekræft, at forespørgselsretry-mekanismer genvurderer autorisationspolitikker for at tage højde for dynamiske tilladelsesændringer inden for aktive brugersessioner.                                                              |   3    |  D/V  |

---

## C5.5 Output-filtrering og datatabsforebyggelse

Implementer efterbehandlingskontroller for at forhindre uautoriseret dataeksponering i AI-genereret indhold.

|   #   | Beskrivelse                                                                                                                                                                        | Niveau | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.5.1 | Bekræft, at post-inferens filtreringsmekanismer scanner og slører uautoriserede PII, klassificerede oplysninger og proprietære data, før indhold leveres til anmodere.             |   1    |  D/V  |
| 5.5.2 | Bekræft, at citater, henvisninger og kildeangivelser i modeloutput valideres i forhold til callerens rettigheder og fjernes, hvis uautoriseret adgang konstateres.                 |   1    |  D/V  |
| 5.5.3 | Bekræft, at outputformatrestriktioner (rensede PDF'er, metadata-fjernede billeder, godkendte filtyper) håndhæves baseret på brugerens tilladelsesniveauer og dataklassifikationer. |   2    |   D   |
| 5.5.4 | Bekræft, at redigeringsalgoritmer er deterministiske, versionskontrollerede og opretholder revisionslogfiler for at støtte overholdelsesundersøgelser og retsmedicinsk analyse.    |   2    |   V   |
| 5.5.5 | Bekræft, at højrisiko-redaktionsevents genererer adaptive logfiler, der inkluderer kryptografiske hashes af det originale indhold til retsmedicinsk genfinding uden datalækage.    |   3    |   V   |

---

## C5.6 Multi-Tenant Isolation

Sørg for kryptografisk og logisk isolation mellem lejere i delt AI-infrastruktur.

|   #   | Beskrivelse                                                                                                                                                                                     | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.6.1 | Bekræft, at hukommelsesområder, indlejringslagre, cacheposter og midlertidige filer er navneområdesegregerede pr. lejer med sikker oprydning ved sletning af lejer eller afslutning af session. |   1    |  D/V  |
| 5.6.2 | Bekræft, at hver API-anmodning inkluderer en autentificeret lejeridentifikator, der er kryptografisk valideret i forhold til sessionskontekst og brugerrettigheder.                             |   1    |  D/V  |
| 5.6.3 | Bekræft, at netværkspolitikker implementerer standard-afvis-regler for kommunikation på tværs af lejere inden for servicemeshes og containerorkestreringsplatforme.                             |   2    |   D   |
| 5.6.4 | Bekræft, at krypteringsnøgler er unikke pr. lejer med kundestyret nøgle (CMK) understøttelse og kryptografisk isolation mellem lejerens datalagre.                                              |   3    |   D   |

---

## C5.7 Autonom Agentgodkendelse

Kontroller tilladelser for AI-agenter og autonome systemer gennem scoped capability tokens og kontinuerlig autorisation.

|   #   | Beskrivelse                                                                                                                                                                                                                                 | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 5.7.1 | Bekræft, at autonome agenter modtager scoped kapabilitetstokener, der eksplicit opregner tilladte handlinger, tilgængelige ressourcer, tidsgrænser og driftsmæssige begrænsninger.                                                          |   1    |  D/V  |
| 5.7.2 | Bekræft, at højrisiko-funktioner (adgang til filsystemet, kodeeksekvering, eksterne API-kald, finansielle transaktioner) er deaktiveret som standard og kræver eksplicitte godkendelser for aktivering med forretningsmæssige begrundelser. |   1    |  D/V  |
| 5.7.3 | Bekræft, at kapabilitetstoken er bundet til brugersessioner, inkluderer kryptografisk integritetsbeskyttelse, og sikr, at de ikke kan gemmes eller genbruges i offline-scenarier.                                                           |   2    |   D   |
| 5.7.4 | Bekræft, at agent-initierede handlinger gennemgår sekundær autorisation via ABAC-politikmotoren med fuld kontekst evaluering og revisionslogføring.                                                                                         |   2    |   V   |
| 5.7.5 | Bekræft, at agentfejltilstande og undtagelseshåndtering inkluderer oplysnigner om kapabilitetens omfang for at understøtte hændelsesanalyse og retsmedicinsk undersøgelse.                                                                  |   3    |   V   |

---

## Referencer

### Standarder & Rammeværk

* [NIST SP 800-63-3: Digital Identity Guidelines](https://pages.nist.gov/800-63-3/)
* [Zero Trust Architecture – NIST SP 800-207](https://nvlpubs.nist.gov/nistpubs/specialpublications/NIST.SP.800-207.pdf)
* [OWASP Application Security Verification Standard (AISVS)](https://owasp.org/www-project-application-security-verification-standard/)
  ​
### Implementeringsvejledninger

* [Identity and Access Management in the AI Era: 2025 Guide – IDSA](https://www.idsalliance.org/blog/identity-and-access-management-in-the-ai-era-2025-guide/)
* [Attribute-Based Access Control with OPA – Permify](https://medium.com/permify-tech-blog/attribute-based-access-control-abac-implementation-with-open-policy-agent-opa-b47052248f29)
* [How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS](https://aws.amazon.com/blogs/security/how-we-designed-cedar-to-be-intuitive-to-use-fast-and-safe/)
  ​
### AI-specifik sikkerhed

* [Row Level Security in Vector DBs for RAG – Bluetuple.ai](https://medium.com/bluetuple-ai/implementing-row-level-security-in-vector-dbs-for-rag-applications-fdbccb63d464)
* [Tenant Isolation in Multi-Tenant Systems – WorkOS](https://workos.com/blog/tenant-isolation-in-multi-tenant-systems)
* [Handling AI Agent Permissions – Stytch](https://stytch.com/blog/handling-ai-agent-permissions/)
* [OWASP Top 10 for Large Language Model Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

