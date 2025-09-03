# C8 Geheugen, Embeddings en Vector Database Beveiliging

## Beheersdoel

Embeddings en vectoropslagen fungeren als het "live geheugen" van hedendaagse AI-systemen, die continu door gebruikers aangeleverde data accepteren en deze via Retrieval-Augmented Generation (RAG) terugbrengen in modelcontexten. Als dit geheugen niet wordt beheerd, kan persoonlijke identificeerbare informatie (PII) lekken, toestemming schenden, of worden omgekeerd om de oorspronkelijke tekst te reconstrueren. Het doel van deze controlefamilie is om geheugenpijplijnen en vectordatabanken te verharden, zodat de toegang gebaseerd is op het principe van minimale rechten, embeddings privacybeschermend zijn, opgeslagen vectoren verlopen of op verzoek kunnen worden ingetrokken, en per-gebruiker geheugen nooit de prompts of voltooiingen van een andere gebruiker besmet.

---

## C8.1 Toegangscontroles op Geheugen & RAG-indexen

Handhaaf fijnmazige toegangscontroles op elke vectorverzameling.

|   #   | Beschrijving                                                                                                                                                       | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 8.1.1 | Verifieer dat rij-/naamruimte-niveau toegangscontroleregels de insert, delete en query-operaties beperken per huurder, collectie of documenttag.                   |   1    | D/V |
| 8.1.2 | Controleer of API-sleutels of JWTs scope-claims bevatten (bijv. collectie-ID's, actie-werkwoorden) en minstens elk kwartaal worden geroteerd.                      |   1    | D/V |
| 8.1.3 | Controleer of privilege-escalatiepogingen (bijv. similariteitsquery's tussen naamruimtes) binnen 5 minuten worden gedetecteerd en in een SIEM worden gelogd.       |   2    | D/V |
| 8.1.4 | Controleer of de auditlog van de vector-databank de velden subject-identificator, operatie, vector-ID/naamruimte, similariteitsdrempel en aantal resultaten bevat. |   2    | D/V |
| 8.1.5 | Verifieer dat toegangsbeslissingen worden getest op omzeilingsfouten telkens wanneer engines worden bijgewerkt of index-sharding regels wijzigen.                  |   3    |  V  |

---

## C8.2 Embedding sanitatie & validatie

Tekst vooraf controleren op persoonlijk identificeerbare informatie (PII), redigeren of pseudonimiseren voordat vectorisatie plaatsvindt, en optioneel embeddings achteraf verwerken om resterende signalen te verwijderen.

|   #   | Beschrijving                                                                                                                                                                                            | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.2.1 | Verifieer dat persoonsidentificeerbare informatie (PII) en gereguleerde gegevens worden gedetecteerd via geautomatiseerde classificatoren en vóór de embedding gemaskeerd, getokeniseerd of verwijderd. |   1    | D/V |
| 8.2.2 | Verifieer dat embedding-pijplijnen invoer afwijzen of in quarantaine plaatsen die uitvoerbare code bevatten of niet-UTF-8 artefacten die de index kunnen vergiftigen.                                   |   1    |  D  |
| 8.2.3 | Controleer of lokale of metrische differentiële privacy-sanitatie wordt toegepast op zin-embeddings waarvan de afstand tot elk bekend PII-token onder een configureerbare drempel ligt.                 |   2    | D/V |
| 8.2.4 | Controleer dat de sanitatie-effectiviteit (bijv. recall van PII-redactie, semantische drift) ten minste halfjaarlijks wordt gevalideerd tegen benchmark-corpora.                                        |   2    |  V  |
| 8.2.5 | Controleer of sanitatieconfiguraties onder versiebeheer staan en of wijzigingen een collegiale beoordeling ondergaan.                                                                                   |   3    | D/V |

---

## C8.3 Geheugenvervaldatum, Intrekking en Verwijdering

GDPR, het 'recht op vergetelheid' en vergelijkbare wetten vereisen tijdige verwijdering; vectoropslagen moeten daarom TTL's, harde verwijderingen en tomb-stoning ondersteunen, zodat ingetrokken vectoren niet kunnen worden teruggehaald of opnieuw geïndexeerd worden.

|   #   | Beschrijving                                                                                                                                                                               | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 8.3.1 | Verifieer dat elk vectorrecord en metadatarecord een TTL of expliciet retentie-label bevat dat wordt gerespecteerd door geautomatiseerde opruimtaken.                                      |   1    | D/V |
| 8.3.2 | Verifieer dat door de gebruiker geïnitieerde verwijderingsverzoeken vectoren, metadata, cachekopieën en afgeleide indexen binnen 30 dagen worden gewist.                                   |   1    | D/V |
| 8.3.3 | Controleer dat logische verwijderingen gevolgd worden door cryptografische vernietiging van opslagblokken als de hardware dit ondersteunt, of door vernietiging van sleutels in Key Vault. |   2    |  D  |
| 8.3.4 | Controleer of verlopen vectoren zijn uitgesloten van de resultaten van de zoekopdracht naar de nabijste buur binnen < 500 ms na verval.                                                    |   3    | D/V |

---

## C8.4 Voorkom embedding-inversie en lekkage

Recente afweermaatregelen—ruis-superpositie, projectie-netwerken, privacy-neuronverstoring, en applicatielaag-versleuteling—kunnen tokenniveau-inversieratio's onder de 5% brengen.

|   #   | Beschrijving                                                                                                                                                                          | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.4.1 | Controleer of er een formeel bedreigingsmodel bestaat dat inversie-, lidmaatschap- en attribuut-inferentie-aanvallen bestrijkt en jaarlijks wordt beoordeeld.                         |   1    |  V  |
| 8.4.2 | Bevestig dat versleuteling op applicatieniveau of doorzoekbare encryptie de vectoren beschermt tegen directe lectuur door infrastructuurbeheerders of cloudmedewerkers.               |   2    | D/V |
| 8.4.3 | Controleer dat de verdedigingsparameters (ε voor DP, ruis σ, projectierang k) in evenwicht zijn tussen privacy ≥ 99 % tokenbescherming en bruikbaarheid ≤ 3 % nauwkeurigheidsverlies. |   3    |  V  |
| 8.4.4 | Verifieer of inversie-weerstandmetingen deel uitmaken van releasepoorten voor modelupdates, met gedefinieerde regressiebudgetten.                                                     |   3    | D/V |

---

## C8.5 Bereikhandhaving voor gebruikersspecifiek geheugen

Cross-tenant-lekkage blijft een van de grootste RAG-risico's: onjuist gefilterde similariteitsopvragen kunnen de privé-documenten van een andere klant aan het licht brengen.

|   #   | Beschrijving                                                                                                                                                                                                  | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.5.1 | Verifieer dat elke opvraging na filtering op basis van tenant-/gebruiker-ID wordt doorgegeven aan de LLM-prompt.                                                                                              |   1    | D/V |
| 8.5.2 | Controleer of collectienamen of naamruimte-ID's per gebruiker of per tenant met zout zijn gehashd, zodat vectoren tussen scopes niet kunnen botsen.                                                           |   1    |  D  |
| 8.5.3 | Verifieer dat gelijkenisresultaten die boven een instelbare afstandsdrempel liggen maar buiten het bereik van de aanroepende code vallen, worden verwijderd en beveiligingswaarschuwingen worden geactiveerd. |   2    | D/V |
| 8.5.4 | Controleer dat multi-tenant-stresstests tegenaanvallende query's simuleren die proberen documenten buiten de scope op te halen, en toon aan dat er geen lekkage is.                                           |   2    |  V  |
| 8.5.5 | Verifieer dat versleutelingssleutels per tenant gescheiden zijn, zodat cryptografische isolatie gewaarborgd blijft, zelfs als fysieke opslag gedeeld is.                                                      |   3    | D/V |

---

## C8.6 Geavanceerde beveiliging van het geheugensysteem

Beveiligingscontroles voor geavanceerde geheugenarchitecturen, waaronder episodisch geheugen, semantisch geheugen en werkgeheugen, met specifieke isolatie- en validatie-eisen.

|   #   | Beschrijving                                                                                                                                                                                                                                                            | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.6.1 | Verifieer dat verschillende geheugentypen (episodisch, semantisch, werkgeheugen) geïsoleerde beveiligingscontexten hebben met op rollen gebaseerde toegangscontroles, aparte encryptiesleutels en gedocumenteerde toegangspatronen voor elk geheugentype.               |   1    | D/V |
| 8.6.2 | Controleer of geheugenconsolidatieprocessen beveiligingsvalidatie bevatten om injectie van kwaadaardige geheugeninhoud te voorkomen door middel van inhoudsanitatie, bronverificatie en integriteitscontroles vóór opslag.                                              |   2    | D/V |
| 8.6.3 | Controleer of geheugenopvragingen worden gevalideerd en geschoond om te voorkomen dat onbevoegde informatie wordt onttrokken via analyse van query-patronen, handhaving van toegangscontrole en filtratie van resultaten.                                               |   2    | D/V |
| 8.6.4 | Verifieer dat geheugenvernietigingsmechanismen gevoelige informatie veilig verwijderen met cryptografische uitwisgaranties door middel van sleutelverwijdering, meerdere passes overschrijven, of hardware-gebaseerde veilige verwijdering met verificatiecertificaten. |   3    | D/V |
| 8.6.5 | Controleer dat de integriteit van het geheugensysteem continu wordt gemonitord op ongeautoriseerde wijzigingen of corruptie via checksums, audit logs en automatische meldingen wanneer de geheugeninhoud buiten de normale werking verandert.                          |   3    | D/V |

---

## Referenties

* [Vector database security: Pinecone – IronCore Labs](https://ironcorelabs.com/vectordbs/pinecone-security/)
* [Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera](https://privacera.com/blog/securing-the-backbone-of-ai-safeguarding-vector-databases-and-embeddings/)
* [Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances](https://ai.gopubby.com/enhancing-data-security-with-role-based-access-control-of-qdrant-vector-database-3878769bec83)
* [Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv](https://arxiv.org/html/2411.05034v1)
* [DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview](https://openreview.net/forum?id=DF5TVzpTW0)
* [Art. 17 GDPR – Right to Erasure](https://gdpr-info.eu/art-17-gdpr/)
* [Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai](https://www.tonic.ai/blog/sensitive-data-in-text-embeddings-is-recoverable)
* [PII Identification and Removal – NVIDIA NeMo Docs](https://docs.nvidia.com/nemo-framework/user-guide/latest/datacuration/personalidentifiableinformationidentificationandremoval.html)
* [De-identifying Sensitive Data – Google Cloud DLP](https://cloud.google.com/sensitive-data-protection/docs/deidentify-sensitive-data)
* [Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails](https://docs.aws.amazon.com/bedrock/latest/userguide/guardrails-sensitive-filters.html)
* [Think Your RAG Is Secure? Think Again – Medium](https://medium.com/%40vijay.poudel1/think-your-rag-is-secure-think-again-heres-how-to-actually-lock-it-down-c4c30e3864e7)
* [Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/ai-ml/guide/secure-multitenant-rag)
* [Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog](https://milvus.io/blog/build-multi-tenancy-rag-with-milvus-best-practices-part-one.md)

