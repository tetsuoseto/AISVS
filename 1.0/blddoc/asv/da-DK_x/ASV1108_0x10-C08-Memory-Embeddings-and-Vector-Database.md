# C8 Hukommelse, Embeddings & Vektordatabase Sikkerhed

## Kontrolmål

Indlejringer og vektorlagre fungerer som det "aktive hukommelse" i moderne AI-systemer, der kontinuerligt modtager brugerleverede data og bringer dem tilbage i modelkontekster via Retrieval-Augmented Generation (RAG). Hvis denne hukommelse ikke styres, kan den lække personligt identificerbare oplysninger (PII), krænke samtykke eller vendes om for at genskabe den oprindelige tekst. Formålet med denne kontrolgruppe er at styrke hukommelsespipeline og vektordatabaser, så adgangen er mindst mulig, indlejringer er privatlivsbeskyttende, lagrede vektorer udløber eller kan tilbagekaldes efter behov, og at hukommelse pr. bruger aldrig forurener en anden brugers prompts eller resultater.

---

## C8.1 Adgangskontrol på hukommelse og RAG-indekser

Håndhæv detaljerede adgangskontroller på hver enkelt vektorsamling.

|   #   | Beskrivelse                                                                                                                                                       | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.1.1 | Bekræft, at adgangskontrolregler på række-/navneområdeniveau begrænser indsættelses-, slette- og forespørgselsoperationer pr. lejer, samling eller dokumentmærke. |   1    |  D/V  |
| 8.1.2 | Bekræft, at API-nøgler eller JWT'er indeholder scoped claims (f.eks. samlings-ID'er, handlingsverber) og roteres mindst kvartalsvis.                              |   1    |  D/V  |
| 8.1.3 | Bekræft, at forsøg på privilegieeskalering (f.eks. forespørgsler om ligheder på tværs af namespaces) opdages og logges i et SIEM inden for 5 minutter.            |   2    |  D/V  |
| 8.1.4 | Bekræft, at vector DB logger revisionsspor for emne-identifikator, operation, vector ID/namespace, lighedstærskel og resultattælling.                             |   2    |  D/V  |
| 8.1.5 | Sørg for, at adgangsbeslutninger testes for omgåelsesfejl, hver gang motorer opgraderes eller regler for index-sharding ændres.                                   |   3    |   V   |

---

## C8.2 Integreringssikkerhed og validering

Forhåndsscreen tekst for PII, slør eller pseudonymiser før vektoriserering, og efterbehandl eventuelt indlejringerne for at fjerne resterende signaler.

|   #   | Beskrivelse                                                                                                                                                                      | Niveau | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.2.1 | Bekræft, at PII og regulerede data opdages via automatiserede klassifikatorer og maskeres, tokeniseres eller fjernes før embedding.                                              |   1    |  D/V  |
| 8.2.2 | Verificer, at embeddingspipelines afviser eller isolerer input, der indeholder eksekverbar kode eller ikke-UTF-8 artefakter, som kunne forurene indekset.                        |   1    |   D   |
| 8.2.3 | Bekræft, at lokal eller metrisk differential-privacy sanitering anvendes på sætningsindlejringer, hvis afstand til enhver kendt PII-token falder under en konfigurerbar tærskel. |   2    |  D/V  |
| 8.2.4 | Bekræft, at effektiviteten af sanitering (f.eks. tilbagekaldelse af PII-redigering, semantisk afvigelse) valideres mindst to gange årligt mod referencekorpusser.                |   2    |   V   |
| 8.2.5 | Bekræft, at saniteringskonfigurationer er versionskontrollerede, og at ændringer gennemgår kollegial gennemgang.                                                                 |   3    |  D/V  |

---

## C8.3 Hukommelsesudløb, Tilbagekaldelse og Sletning

GDPR "ret til at blive glemt" og lignende love kræver rettidig sletning; derfor skal vektorlagre understøtte TTL'er, hårde sletninger og tomb-stoning, så tilbagekaldte vektorer ikke kan gendannes eller reindekseres.

|   #   | Beskrivelse                                                                                                                                                              | Niveau | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 8.3.1 | Bekræft, at hver vektor- og metadataregistrering har en TTL eller en eksplicit opbevaringsmærkat, som overholdes af automatiserede oprydningsjob.                        |   1    |  D/V  |
| 8.3.2 | Bekræft, at brugerinitierede sletningsanmodninger fjerner vektorer, metadata, cachekopier og afledte indekser inden for 30 dage.                                         |   1    |  D/V  |
| 8.3.3 | Bekræft, at logiske sletninger efterfølges af kryptografisk sletning af lagringsblokke, hvis hardwaren understøtter det, eller ved destruktion af nøgler i nøglevaulten. |   2    |   D   |
| 8.3.4 | Bekræft, at udløbne vektorer udelukkes fra nærmeste-nabo-søgeresultater inden for < 500 ms efter udløb.                                                                  |   3    |  D/V  |

---

## C8.4 Forhindre embedding-inversion og lækage

Nylige forsvar—støj-superposition, projektnetværk, privatlivs-neuronforstyrrelse og kryptering på applikationslaget—kan reducere token-niveau inversion satser til under 5%.

|   #   | Beskrivelse                                                                                                                                                           | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.4.1 | Sørg for, at der findes en formel trusselsmodel, der dækker inversion, medlemskabs- og attributinferenzangreb, og at den gennemgås årligt.                            |   1    |   V   |
| 8.4.2 | Bekræft, at applikationslagskryptering eller søgbar kryptering beskytter vektorer mod direkte læsning af infrastrukturområdets administratorer eller cloud-personale. |   2    |  D/V  |
| 8.4.3 | Bekræft, at forsvarsparametrene (ε for DP, støj σ, projektionens rang k) balancerer privatliv ≥ 99 % tokenbeskyttelse og nytte ≤ 3 % præcisionstab.                   |   3    |   V   |
| 8.4.4 | Sørg for, at målinger for inversion-resiliens er en del af frigivelsesporte for modelopdateringer, med definerede regressionsbudgetter.                               |   3    |  D/V  |

---

## C8.5 Omfangshåndhævelse for brugerspecifik hukommelse

Lækage på tværs af lejere forbliver en af de største risici ved RAG: Forkert filtrerede lighedsspørgsmål kan vise en anden kundes private dokumenter.

|   #   | Beskrivelse                                                                                                                                               | Niveau | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.5.1 | Bekræft, at hver forespørgsel til hentning efterfiltreres af lejer-/bruger-ID, før den sendes til LLM-prompten.                                           |   1    |  D/V  |
| 8.5.2 | Bekræft, at samlingsnavne eller navngivne ID'er saltes pr. bruger eller lejer, så vektorer ikke kan kollidere på tværs af scopes.                         |   1    |   D   |
| 8.5.3 | Bekræft, at lighedsresultater over en konfigurerbar afstandstærskel, men uden for kalders rækkevidde, bliver afvist og udløser sikkerhedsadvarsler.       |   2    |  D/V  |
| 8.5.4 | Bekræft, at multi-tenant stresstest simulerer modstridende forespørgsler, der forsøger at hente dokumenter uden for omfanget, og demonstrerer nul lækage. |   2    |   V   |
| 8.5.5 | Bekræft, at krypteringsnøgler er adskilt pr. lejer, for at sikre kryptografisk isolation, selvom fysisk lagring deles.                                    |   3    |  D/V  |

---

## C8.6 Avanceret Hukommelsessystem Sikkerhed

Sikkerhedskontroller for sofistikerede hukommelsesarkitekturer, herunder episodisk, semantisk og arbejdshukommelse med specifikke isolations- og valideringskrav.

|   #   | Beskrivelse                                                                                                                                                                                                                                     | Niveau | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 8.6.1 | Bekræft, at forskellige hukommelsestyper (episodisk, semantisk, arbejdshukommelse) har isolerede sikkerhedskontekster med rollebaserede adgangskontroller, separate krypteringsnøgler og dokumenterede adgangsmønstre for hver hukommelsestype. |   1    |  D/V  |
| 8.6.2 | Bekræft, at hukommelseskonsolideringsprocesser inkluderer sikkerhedsgodkendelse for at forhindre indsprøjtning af ondsindede minder gennem indholdsrensning, kildeverifikation og integritetskontroller før lagring.                            |   2    |  D/V  |
| 8.6.3 | Bekræft, at forespørgsler til hukommelsesudtræk valideres og renses for at forhindre udtrækning af uautoriseret information gennem analyse af forespørgselsmønstre, håndhævelse af adgangskontrol og filtrering af resultater.                  |   2    |  D/V  |
| 8.6.4 | Bekræft, at hukommelsesglemmemekanismer sikkert sletter følsomme oplysninger med kryptografiske slettegarantier ved hjælp af nøgle-sletning, flergangsover-skrivning eller hardware-baseret sikker sletning med verifikationscertifikater.      |   3    |  D/V  |
| 8.6.5 | Bekræft, at hukommelsessystemets integritet kontinuerligt overvåges for uautoriserede ændringer eller korruption gennem checksums, revisionslogfiler og automatiske advarsler, når hukommelsesindhold ændres uden for normale operationer.      |   3    |  D/V  |

---

## Referencer

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

