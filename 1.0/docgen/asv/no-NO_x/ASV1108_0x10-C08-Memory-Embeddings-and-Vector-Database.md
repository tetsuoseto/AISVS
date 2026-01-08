# C8 Minne, Innebygde representasjoner og Vektordatabasesikkerhet

## Kontrollmål

Inbeddinger og vektorlager fungerer som den "levende hukommelsen" i moderne AI-systemer, og mottar kontinuerlig data levert av brukeren og bringer det tilbake i modellkontekster via Retrieval-Augmented Generation (RAG). Hvis denne hukommelsen ikke styres, kan den lekke personidentifiserbar informasjon (PII), bryte samtykke eller bli invertet for å rekonstruere originalteksten. Målet med denne kontrollfamilien er å styrke minnepipelines og vektordatabaser slik at tilgang er minst mulig privilegert, innbeddinger er personvernbevarende, lagrede vektorer utløper eller kan tilbakekalles på forespørsel, og at per-brukers minne aldri forurenser en annen brukers forespørsler eller svar.

---

## C8.1 Tilgangskontroller på minne og RAG-indekser

Håndhev detaljert tilgangskontroll på hver vektorsamling.

|   #   | Beskrivelse                                                                                                                                                    | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.1.1 | Bekreft at tilgangskontrollregler på rad-/navneromsnivå begrenser innsettings-, slettings- og spørringsoperasjoner per leietaker, samling eller dokumentmerke. |  1   |  D/V  |
| 8.1.2 | Bekreft at API-nøkler eller JWT-er inneholder avgrensede krav (f.eks. samlings-ID-er, handlingsverb) og roteres minst hvert kvartal.                           |  1   |  D/V  |
| 8.1.3 | Bekreft at forsøk på privilegieeskalering (f.eks. tverr-namespace likhetsspørringer) oppdages og logges til en SIEM innen 5 minutter.                          |  2   |  D/V  |
| 8.1.4 | Bekreft at vektordatabase reviderer loggene for subjekt-identifikator, operasjon, vektor-ID/område, likhetsterskel og resultatantall.                          |  2   |  D/V  |
| 8.1.5 | Sørg for at tilgangsbeslutninger testes for omgåelsesfeil hver gang motorer oppgraderes eller regler for indeks-sharding endres.                               |  3   |   V   |

---

## C8.2 Innholdsrensing og validering

Forhåndssjekk tekst for PII, sensurer eller pseudonymiser før vektorisering, og eventuelt etterbehandle innebygde data for å fjerne gjenværende signaler.

|   #   | Beskrivelse                                                                                                                                                                       | Nivå | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.2.1 | Bekreft at PII og regulerte data blir oppdaget via automatiserte klassifikatorer og maskert, tokenisert eller fjernet før embedding.                                              |  1   |  D/V  |
| 8.2.2 | Verifiser at embedding-pipelines avviser eller isolerer inndata som inneholder kjørbar kode eller ikke-UTF-8-artefakter som kan forgifte indeksen.                                |  1   |   D   |
| 8.2.3 | Verifiser at lokal eller metrisk differensial-personvernsanitering blir brukt på setningsinnebygginger hvis avstand til en kjent PII-token faller under en konfigurerbar terskel. |  2   |  D/V  |
| 8.2.4 | Sørg for at rensningseffektivitet (f.eks. tilbakekalling av PII-redigering, semantisk avvik) valideres minst annenhvert halvår mot referansekorpora.                              |  2   |   V   |
| 8.2.5 | Verifiser at sanitæringskonfigurasjoner er versjonskontrollert og at endringer gjennomgår kollegavurdering.                                                                       |  3   |  D/V  |

---

## C8.3 Minneutløp, tilbakekalling og sletting

GDPR "retten til å bli glemt" og lignende lover krever rettidig sletting; vektorlagre må derfor støtte TTL-er, hard sletting og tomb-stoning slik at tilbakekalte vektorer ikke kan gjenopprettes eller re-indekseres.

|   #   | Beskrivelse                                                                                                                                                             | Nivå | Rolle |
| :---: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.3.1 | Bekreft at hver vektor- og metadataoppføring har en TTL eller en eksplisitt oppbevaringsetikett som respekteres av automatiserte ryddejobber.                           |  1   |  D/V  |
| 8.3.2 | Bekreft at sletteforespørsler initiert av brukeren fjerner vektorer, metadata, cache-kopier og derivatindekser innen 30 dager.                                          |  1   |  D/V  |
| 8.3.3 | Bekreft at logiske slettinger følges opp med kryptografisk sletting av lagringsblokker hvis maskinvaren støtter det, eller ved destruksjon av nøkkelen i nøkkellageret. |  2   |   D   |
| 8.3.4 | Bekreft at utløpte vektorer blir ekskludert fra nærmeste-nabo-søkeresultater innen < 500 ms etter utløp.                                                                |  3   |  D/V  |

---

## C8.4 Forhindre innkapslingsinversjon og lekkasje

Nylige forsvar—støy-supersisjon, projeksjonsnettverk, personvern-nevronforstyrrelse og applikasjonslagskryptering—kan redusere token-nivå inversjonsrater til under 5%.

|   #   | Beskrivelse                                                                                                                                               | Nivå | Rolle |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.4.1 | Bekreft at en formell trusselmodell som dekker inversjons-, medlemskaps- og attributt-inferensangrep eksisterer og gjennomgås årlig.                      |  1   |   V   |
| 8.4.2 | Bekreft at applikasjonslagskryptering eller søkbar kryptering beskytter vektorer fra direkte lesing av infrastrukturadministratorer eller skyansatte.     |  2   |  D/V  |
| 8.4.3 | Verifiser at forsvarsparametrene (ε for DP, støy σ, projeksjonsrang k) balanserer personvern ≥ 99 % tokenbeskyttelse og nytteverdi ≤ 3 % nøyaktighetstap. |  3   |   V   |
| 8.4.4 | Bekreft at metrikkene for inversion-motstand er en del av utgivelsesgrenser for modelloppdateringer, med definerte regresjonsbudsjetter.                  |  3   |  D/V  |

---

## C8.5 Omfangshåndheving for brukerspesifikk minne

Kryss-lekkasje mellom leietakere forblir en topp RAG-risiko: feilaktig filtrerte likhetsspørringer kan avdekke en annen kundes private dokumenter.

|   #   | Beskrivelse                                                                                                                                        | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.5.1 | Bekreft at hver gjenopprettingsforespørsel blir etterfiltrert etter leietaker-/bruker-ID før den sendes til LLM-prompten.                          |  1   |  D/V  |
| 8.5.2 | Bekreft at samlingsnavn eller navneområder med ID-er er saltet per bruker eller leietaker slik at vektorer ikke kan kollidere på tvers av områder. |  1   |   D   |
| 8.5.3 | Bekreft at likhetsresultater over en konfigurerbar avstandsterskel, men utenfor anroperens omfang, forkastes og utløser sikkerhetsvarsler.         |  2   |  D/V  |
| 8.5.4 | Bekreft at flerleietakerstresstester simulerer motstridende forespørsler som forsøker å hente dokumenter utenfor omfang, og viser null lekkasje.   |  2   |   V   |
| 8.5.5 | Bekreft at krypteringsnøkler er delt opp per leietaker, og sikrer kryptografisk isolasjon selv om fysisk lagring deles.                            |  3   |  D/V  |

---

## C8.6 Avansert minnesystem-sikkerhet

Sikkerhetskontroller for sofistikerte minnearkitekturer inkludert episodisk, semantisk og arbeidsminne med spesifikke isolasjons- og valideringskrav.

|   #   | Beskrivelse                                                                                                                                                                                                                                  | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 8.6.1 | Verifiser at forskjellige minnetyper (episodisk, semantisk, arbeidsminne) har isolerte sikkerhetskontekster med rollebaserte tilgangskontroller, separate krypteringsnøkler, og dokumenterte tilgangsmønstre for hver minnetype.             |  1   |  D/V  |
| 8.6.2 | Bekreft at prosesser for minnekonsolidering inkluderer sikkerhetsvalidering for å forhindre injeksjon av skadelige minner gjennom innholdsrensing, kildeverifisering og integritetssjekker før lagring.                                      |  2   |  D/V  |
| 8.6.3 | Verifiser at spørringer for minnehenting blir validert og renset for å forhindre utvinning av uautorisert informasjon gjennom analyse av spørringsmønstre, håndheving av tilgangskontroll og filtrering av resultater.                       |  2   |  D/V  |
| 8.6.4 | Verifiser at mekanismer for glemming av minne sletter sensitiv informasjon sikkert med kryptografiske slettingsgarantier ved bruk av nøkkelsletting, flerpass-skriving eller maskinvarebasert sikker sletting med verifikasjonssertifikater. |  3   |  D/V  |
| 8.6.5 | Bekreft at minnesystemets integritet kontinuerlig overvåkes for uautoriserte endringer eller korrupsjon gjennom sjekksummer, revisjonslogger og automatiske varsler når minneinnhold endres utenfor normale operasjoner.                     |  3   |  D/V  |

---

## Referanser

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

