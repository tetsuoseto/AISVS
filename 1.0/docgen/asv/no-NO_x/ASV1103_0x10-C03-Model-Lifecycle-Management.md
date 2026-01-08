# C3 Modell livssyklusadministrasjon og endringskontroll

## Kontrollmål

AI-systemer må implementere endringskontrollprosesser som forhindrer uautorisert eller usikker modellendring fra å nå produksjon. Denne kontrollen sikrer modellens integritet gjennom hele livssyklusen—fra utvikling gjennom utrulling til avvikling—noe som muliggjør rask hendelseshåndtering og opprettholder ansvarlighet for alle endringer.

Kjerne sikkerhetsmål: Kun autoriserte, validerte modeller når produksjon ved å bruke kontrollerte prosesser som opprettholder integritet, sporbarhet og gjenopprettbarhet.

---

## C3.1 Modellautorisasjon og integritet

Kun autoriserte modeller med verifisert integritet når produksjonsmiljøer.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                                                        | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.1.1 | Verifiser at alle modellartefakter (vekter, konfigurasjoner, tokenizere, basismodeller, finjusteringer, adaptere som LoRA, og sikkerhets-/policy-modeller) er kryptografisk signert av autoriserte enheter og verifisert ved distribusjonsgodkjenning (og ved lasting), og blokkerer enhver usignert eller manipulert artefakt.                    |  1   |  D/V  |
| 3.1.2 | Bekreft at avhengighetssporing opprettholder et sanntidslager via et modellregister og en opprinnelses-/avhengighetsgraf, og produserer en maskinlesbar Modell/AI Materialliste (MBOM/AIBOM) (f.eks. SPDX eller CycloneDX) som muliggjør identifisering av alle konsumtjenester/agenter per miljø (f.eks. utvikling, staging, produksjon, region). |  2   |   V   |
| 3.1.3 | Bekreft at modellens opprinnelsesintegritet og sporingsregistre inkluderer en autoriserende enhets identitet, sjekksummer for treningsdata, valideringstestresultater med godkjent/ikke godkjent status, signaturfingeravtrykk/certifikatkjede-ID, et opprettelsestidspunkt og godkjente distribusjonsmiljøer.                                     |  3   |  D/V  |

---

## C3.2 Modellvalidering og testing

Modeller må bestå definerte sikkerhets- og trygghetsvalideringer før implementering.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                                                                                                                                           | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.2.1 | Bekreft at modeller gjennomgår automatisert sikkerhetstesting som inkluderer inputvalidering, outputrensing og sikkerhetsevalueringer med forhåndsavtalte organisatoriske bestått/ikke-bestått terskler før implementering, som dekker agentarbeidsflyter (planlegging, verktøy- eller MCP-kall, RAG/minne, multimodal) og sikkerhetsrammer (policy-/sikkerhetsmodeller eller deteksjonstjenester) med en versjonert evalueringstest. |  1   |  D/V  |
| 3.2.2 | Bekreft at alle modellendringer (utrulling, konfigurasjon, avvikling) genererer immutables revisjonsspor som inkluderer et tidsstempel, en autentisert aktøridentitet, en endringstype, og før/etter tilstander, med sporemetadata (miljø og forbrukende tjenester/agenter) og en modelidentifikator (versjon/digest/signatur).                                                                                                       |  1   |   V   |
| 3.2.3 | Bekreft at valideringsfeil automatisk blokkerer modellutrulling med mindre det foreligger en eksplisitt overstyringsgodkjenning fra forhåndsbestemte autoriserte personer med dokumenterte forretningsbegrunnelser.                                                                                                                                                                                                                   |  2   |  D/V  |

---

## C3.3 Kontrollert distribusjon og tilbakeføring

Modellutrullinger må kontrolleres, overvåkes og kunne reverseres.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                  | Nivå | Rolle |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.3.1 | Bekreft at distribusjonsprosessene validerer kryptografiske signaturer og beregner integritetskontroller før aktivering eller lasting av modellen, og at distribusjonen feiler ved eventuelle avvik.                                                                                         |  1   |  D/V  |
| 3.3.2 | Sjekk at produksjonsdistribusjoner implementerer mekanismer for gradvis utrulling (canary-distribusjoner, blue-green-distribusjoner) med automatiske tilbakestillingsutløsere basert på forhåndsavtalte feilrater, latensgrenser, sikkerhets-/jailbreak-varsler eller verktøy/MCP-feilrater. |  1   |   D   |
| 3.3.3 | Bekreft at rollback-muligheter gjenoppretter den komplette modelltilstanden (vekter, konfigurasjoner, avhengigheter inkludert adaptere og sikkerhets-/policy-modeller) atomisk.                                                                                                              |  2   |  D/V  |
| 3.3.4 | Bekreft at nødmodellsystemavstengningsfunksjoner kan deaktivere modellendepunkter og deaktivere agentverktøy eller MCP-tilgang, RAG/tilkoblinger og database/API-legitimasjon, samt minnelagerbindinger innen en forhåndsdefinert responstid.                                                |  3   |  D/V  |

---

## C3.4 Sikker utviklingspraksis

Modellutviklings- og treningsprosesser må følge sikre praksiser for å forhindre kompromittering.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                                                | Nivå | Rolle |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 3.4.1 | Bekreft at modellutvikling, testing og produksjonsmiljøer er fysisk eller logisk separert. De har ingen delt infrastruktur, separate tilgangskontroller og isolerte datalagre, og agentorkestrering samt verktøy- eller MCP-servere er også isolerte.                                                                                      |  1   |  D/V  |
| 3.4.2 | Bekreft at artefakter for modellutvikling (hyperparametere, treningsskript, konfigurasjonsfiler, maler for prompt, agentpolicyer/ruteringsgrafer, verktøy- eller MCP-kontrakter/skjemaer, og handlingskataloger eller tillatelseslister for kapasiteter) lagres i versjonskontroll og krever godkjenning fra kollegaer før bruk i trening. |  1   |   D   |
| 3.4.3 | Bekreft at modelltrening og finjustering skjer i isolerte miljøer med kontrollert nettverkstilgang ved bruk av utgående tillatlister og uten tilgang til produksjonsverktøy eller MCP-ressurser.                                                                                                                                           |  2   |  D/V  |
| 3.4.4 | Bekreft at treningsdatakilder er validert gjennom integritetskontroller og autentisert via pålitelige kilder med dokumentert kjede av eierskap før bruk i modellutvikling, inkludert RAG-indekser, verktøylogger og agentgenererte data brukt til finjustering.                                                                            |  2   |   D   |

---

## C3.5 Modellpensjonering og nedleggelse

Modeller må pensjoneres sikkert når de ikke lenger er nødvendige eller når sikkerhetsproblemer oppdages.

|   #   | Beskrivelse                                                                                                                                                                                                                                                                                                                                                      | Nivå | Rolle |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 3.5.1 | Bekreft at pensjonerte modelldata (inkludert adaptere og sikkerhets-/policy-modeller) slettes sikkert ved bruk av sikker kryptografisk utsletting.                                                                                                                                                                                                               |  1   |  D/V  |
| 3.5.2 | Bekreft at modellpensjoneringshendelser logges med tidsstempel og aktøridentitet, modellidentifikator (versjon/digest/signatur) og sporingsmetadata (miljø og konsumerende tjenester/agenter); modellsignaturer tilbakekalles, og register-/serveringsnektelister samt ugyldiggjøring av lastingsbuffer forhindrer at agenter laster inn pensjonerte artefakter. |  2   |   V   |

---

## Referanser

* [MITRE ATLAS](https://atlas.mitre.org/)
* [MLOps Principles](https://ml-ops.org/content/mlops-principles)
* [Reinforcement fine-tuning](https://platform.openai.com/docs/guides/reinforcement-fine-tuning)
* [What is AI adversarial robustness? – IBM Research](https://research.ibm.com/blog/securing-ai-workflows-with-adversarial-robustness)

