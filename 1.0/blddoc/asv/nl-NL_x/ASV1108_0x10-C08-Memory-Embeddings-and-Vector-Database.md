# C8 Geheugen, Embeddings en Vector Database Beveiliging

## Beheersingsdoelstelling

Embeddings en vectoropslag fungeren als het "actieve geheugen" van hedendaagse AI-systemen, waarbij ze continu door gebruikers aangeleverde data accepteren en deze terug in modelcontexten brengen via Retrieval-Augmented Generation (RAG). Als dit geheugen niet wordt beheerd, kan het PII lekken, consent schenden of worden omgekeerd om de originele tekst te reconstrueren. Het doel van deze controlegroep is om geheugenpijplijnen en vectordatabases te versterken zodat toegang op basis van het minste-privilege is, embeddings privacybeschermend zijn, opgeslagen vectoren verlopen of op verzoek kunnen worden ingetrokken, en het geheugen per gebruiker nooit de prompts of uitkomsten van een andere gebruiker besmet.

---

## C8.1 Toegangscontroles op geheugen- en RAG-indexen

Handhaaf fijnmazige toegangscontroles op elke vectorverzameling.

|   #   | Beschrijving                                                                                                                                                   | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.1.1 | Verifieer dat toegangscontroleregels op rij-/namespace-niveau insert-, delete- en query-bewerkingen beperken per tenant, collectie of documenttag.             |   1    | D/V |
| 8.1.2 | Controleer of API-sleutels of JWT's gescopeerde claims bevatten (bijv. collectie-ID's, actie-werkwoorden) en minimaal elk kwartaal worden vervangen.           |   1    | D/V |
| 8.1.3 | Verifieer dat pogingen tot privilege-escalatie (bijv. cross-namespace similarity queries) worden gedetecteerd en binnen 5 minuten worden gelogd naar een SIEM. |   2    | D/V |
| 8.1.4 | Controleer of de vector-DB de auditlog bijhoudt van subject-identificatie, bewerking, vector-ID/namespace, gelijkenisdrempel en resultaataantal.               |   2    | D/V |
| 8.1.5 | Controleer of toegangsbeslissingen worden getest op omzeilingsfouten telkens wanneer engines worden bijgewerkt of regels voor index-sharding veranderen.       |   3    |  V  |

---

## C8.2 Inbedding Sanering & Validatie

Controleer tekst vooraf op PII, redacteer of pseudonimiseer voordat vectorisatie plaatsvindt, en bewerk optioneel de embeddings achteraf om resterende signalen te verwijderen.

|   #   | Beschrijving                                                                                                                                                                                  | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.2.1 | Verifieer dat PII en gereguleerde gegevens worden gedetecteerd via geautomatiseerde classifieringssystemen en voorafgaand aan embedding worden gemaskeerd, getokeniseerd of verwijderd.       |   1    | D/V |
| 8.2.2 | Verifieer dat embedding-pijplijnen invoer met uitvoerbare code of niet-UTF-8-artikelen die de index kunnen besmetten, afwijzen of in quarantaine plaatsen.                                    |   1    |  D  |
| 8.2.3 | Controleer of lokale of metrische differentiële privacy-sanitatie wordt toegepast op zin-embedings waarvan de afstand tot een bekende PII-token onder een configureerbare drempelwaarde valt. |   2    | D/V |
| 8.2.4 | Verifieer dat de effectiviteit van sanering (bijvoorbeeld recall van PII-redactie, semantische verschuiving) minstens halfjaarlijks wordt gevalideerd aan de hand van benchmarkcorpora.       |   2    |  V  |
| 8.2.5 | Controleer of sanitatieconfiguraties versiebeheer hebben en dat wijzigingen een peer review ondergaan.                                                                                        |   3    | D/V |

---

## C8.3 Geheugenverval, intrekking en verwijdering

De GDPR "recht om vergeten te worden" en vergelijkbare wetten vereisen tijdige verwijdering; vectoropslag moet daarom TTL's, harde verwijderingen en tomb-stoning ondersteunen, zodat ingetrokken vectoren niet kunnen worden hersteld of opnieuw geïndexeerd.

|   #   | Beschrijving                                                                                                                                                                                  | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.3.1 | Verifieer dat elke vector- en metadatarecord een TTL of expliciet retentielabel heeft dat wordt gehonoreerd door geautomatiseerde opruimtaken.                                                |   1    | D/V |
| 8.3.2 | Controleer of door de gebruiker geïnitieerde verwijderingsverzoeken vectoren, metadata, cachekopieën en afgeleide indexen binnen 30 dagen wissen.                                             |   1    | D/V |
| 8.3.3 | Controleer of logische verwijderingen worden gevolgd door cryptografisch vernietigen van opslagblokken als de hardware dit ondersteunt, of door vernietiging van sleutel in het sleutelkluis. |   2    |  D  |
| 8.3.4 | Controleer of verlopen vectoren binnen < 500 ms na verlopen worden uitgesloten van de resultaten van de dichtstbijzijnde buurzoektocht.                                                       |   3    | D/V |

---

## C8.4 Voorkom omkering en lekkage van embedding

Recente verdedigingsmethoden—ruis-superpositie, projectienetwerken, privacy-neuronperturbatie en encryptie op applicatielaag—kunnen de token-niveau inversieratio's terugbrengen tot onder de 5%.

|   #   | Beschrijving                                                                                                                                                            | Niveau | Rol |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.4.1 | Controleer of er een formeel dreigingsmodel bestaat dat inversie-, lidmaatschaps- en kenmerk-inferentieaanvallen omvat en dat jaarlijks wordt herzien.                  |   1    |  V  |
| 8.4.2 | Controleer of applicatielaag-encryptie of doorzoekbare encryptie vectoren beschermt tegen directe uitlezing door infrastructuurbeheerders of cloudmedewerkers.          |   2    | D/V |
| 8.4.3 | Verifieer dat verdedigingsparameters (ε voor DP, ruis σ, projectierang k) privacy ≥ 99% tokenbescherming en bruikbaarheid ≤ 3% nauwkeurigheidsverlies in balans houden. |   3    |  V  |
| 8.4.4 | Verifieer dat inversion-resilience metrics onderdeel zijn van release gates voor modelupdates, met gedefinieerde regressiebudgetten.                                    |   3    | D/V |

---

## C8.5 Toepassing van het Toegangsbeheer voor Gebruikersspecifiek Geheugen

Cross-tenant lekkage blijft een van de grootste RAG-risico's: onjuist gefilterde gelijkeniszoekopdrachten kunnen de privédocumenten van een andere klant aan het licht brengen.

|   #   | Beschrijving                                                                                                                                                                    | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.5.1 | Verifieer of elke opvraag voor gegevensverwerking wordt nagesorteerd op tenant-/gebruikers-ID voordat deze aan de LLM-prompt wordt doorgegeven.                                 |   1    | D/V |
| 8.5.2 | Controleer of collectie namen of genamespaceerde ID's per gebruiker of huurder gezouten zijn zodat vectoren niet kunnen botsen tussen scopes.                                   |   1    |  D  |
| 8.5.3 | Controleer of gelijkenisresultaten boven een configureerbare afstandsdrempel maar buiten het bereik van de aanroeper worden weggegooid en beveiligingswaarschuwingen activeren. |   2    | D/V |
| 8.5.4 | Verifieer dat multi-tenant stresstests adversariële queries simuleren die proberen documenten buiten de scope op te vragen en toon aan dat er geen lekken zijn.                 |   2    |  V  |
| 8.5.5 | Verifieer dat encryptiesleutels per huurder gescheiden zijn, waarbij cryptografische isolatie wordt gegarandeerd, zelfs als fysieke opslag gedeeld wordt.                       |   3    | D/V |

---

## C8.6 Geavanceerde Beveiliging van Geheugensystemen

Beveiligingscontroles voor geavanceerde geheugenarchitecturen, inclusief episodisch, semantisch en werkgeheugen met specifieke isolatie- en validatievereisten.

|   #   | Beschrijving                                                                                                                                                                                                                                                        | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 8.6.1 | Controleer of verschillende geheugen typen (episodisch, semantisch, werkgeheugen) geïsoleerde beveiligingscontexten hebben met op rollen gebaseerde toegangscontroles, aparte encryptiesleutels, en gedocumenteerde toegangs patronen voor elk geheugentype.        |   1    | D/V |
| 8.6.2 | Controleer of het geheugenconsolidatieproces een beveiligingsvalidatie omvat om te voorkomen dat kwaadaardige herinneringen worden geïnjecteerd via inhoudssanering, bronverificatie en integriteitscontroles vóór opslag.                                          |   2    | D/V |
| 8.6.3 | Controleer of geheugenophaalqueries worden gevalideerd en geschoond om te voorkomen dat ongeautoriseerde informatie wordt geëxtraheerd via analyse van querypatronen, handhaving van toegangscontrole en filtratie van resultaten.                                  |   2    | D/V |
| 8.6.4 | Controleer of geheugenvergeetmechanismen gevoelige informatie veilig verwijderen met cryptografische wissen-garanties door middel van sleuteldeling, meervoudig overschrijven of hardwaregebaseerde veilige verwijdering met verificatiecertificaten.               |   3    | D/V |
| 8.6.5 | Verifieer dat de integriteit van het geheugensysteem continu wordt gecontroleerd op ongeautoriseerde wijzigingen of beschadigingen via controlesommen, auditlogboeken en automatische waarschuwingen wanneer de geheugeninhoud verandert buiten de normale werking. |   3    | D/V |

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

