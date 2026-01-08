# Vedlegg D: AI-støttet styring og verifisering av sikker koding

## Målsetting

Dette kapitlet definerer grunnleggende organisatoriske kontroller for sikker og effektiv bruk av AI-assisterte kodingsverktøy under programvareutvikling, og sikrer sikkerhet og sporbarhet gjennom hele SDLC.

---

## AD.1 AI-assistert sikker-koding arbeidsflyt

Integrer AI-verktøy i organisasjonens sikre programvareutviklingslivssyklus (SSDLC) uten å svekke eksisterende sikkerhetsporter.

|   #    | Beskrivelse                                                                                                                                                                                | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AD.1.1 | Bekreft at en dokumentert arbeidsflyt beskriver når og hvordan AI-verktøy kan generere, refaktorere eller gjennomgå kode.                                                                  |  1   |  D/V  |
| AD.1.2 | Bekreft at arbeidsflyten samsvarer med hver fase i SSDLC (design, implementering, kodegjennomgang, testing, distribusjon).                                                                 |  2   |   D   |
| AD.1.3 | Bekreft at måleparametere (f.eks. sårbarhetstetthet, gjennomsnittlig tid til oppdagelse) samles inn for AI-generert kode og sammenlignes med baser som kun bruker menneskelig utført kode. |  3   |  D/V  |

---

## AD.2 AI-verktøy Kvalifisering og Trusselmodellering

Sørg for at AI-kodeverktøy evalueres for sikkerhetskapasiteter, risiko og forsyningskjedeeffekt før de tas i bruk.

|   #    | Beskrivelse                                                                                                                                                                        | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.2.1 | Verifiser at en trusselmodell for hvert AI-verktøy identifiserer misbruk, modelinvertasjon, datalekkasjer og avhengighetskjede-risikoer.                                           |  1   |  D/V  |
| AD.2.2 | Verifiser at verktøyevurderinger inkluderer statisk/dynamisk analyse av eventuelle lokale komponenter og vurdering av SaaS-endepunkter (TLS, autentisering/autorisasjon, logging). |  2   |   D   |
| AD.2.3 | Verifiser at evalueringer følger en anerkjent rammeverk og blir utført på nytt etter større versjonsendringer.                                                                     |  3   |  D/V  |

---

## AD.3 Sikker ledelse av prompt og kontekst

Forhindre lekkasje av hemmeligheter, proprietær kode og personopplysninger når du konstruerer prompts eller kontekster for AI-modeller.

|   #    | Beskrivelse                                                                                                                                           | Nivå | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.3.1 | Bekreft at skriftlige retningslinjer forbyr å sende hemmeligheter, legitimasjon eller klassifiserte data i forespørsler.                              |  1   |  D/V  |
| AD.3.2 | Bekreft at tekniske kontroller (redigering på klientsiden, godkjente kontekstfiltre) automatisk fjerner sensitive elementer.                          |  2   |   D   |
| AD.3.3 | Bekreft at forespørsler og svar blir tokenisert, kryptert under overføring og i hvile, og at lagringsperioder overholder dataklassifiseringspolicyen. |  3   |  D/V  |

---

## AD.4 Validering av AI-generert kode

Oppdag og utbedre sårbarheter introdusert av AI-utdata før koden slås sammen eller distribueres.

|   #    | Beskrivelse                                                                                                                                                  | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| AD.4.1 | Sørg for at AI-generert kode alltid blir gjenstand for menneskelig kodegjennomgang.                                                                          |  1   |  D/V  |
| AD.4.2 | Bekreft at automatiserte skannere (SAST/IAST/DAST) kjører på hver pull request som inneholder AI-generert kode, og blokker sammenslåinger ved kritiske funn. |  2   |   D   |
| AD.4.3 | Bekreft at differensial fuzz-testing eller egenskapsbaserte tester beviser sikkerhetskritiske atferder (f.eks. inputvalidering, autorisasjonslogikk).        |  3   |  D/V  |

---

## AD.5 Forklarbarhet og sporbarhet av kodeforslag

Gi revisorer og utviklere innsikt i hvorfor et forslag ble gitt og hvordan det utviklet seg.

|   #    | Beskrivelse                                                                                                                                                          | Nivå | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.5.1 | Bekreft at prompt-/responspar blir logget med commit-IDer.                                                                                                           |  1   |  D/V  |
| AD.5.2 | Bekreft at utviklere kan vise modellhenvisninger (treningsutdrag, dokumentasjon) som støtter et forslag.                                                             |  2   |   D   |
| AD.5.3 | Bekreft at forklaringsrapporter lagres sammen med designartefakter og refereres til i sikkerhetsgjennomganger, og oppfyller ISO/IEC 42001 prinsipper for sporbarhet. |  3   |  D/V  |

---

## AD.6 Kontinuerlig tilbakemelding og modellfinjustering

Forbedre modellens sikkerhetsytelse over tid samtidig som du forhindrer negativ drift.

|   #    | Beskrivelse                                                                                                                                                                             | Nivå | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| AD.6.1 | Bekreft at utviklere kan merke usikre eller ikke-kompatible forslag, og at merkingene blir dokumentert.                                                                                 |  1   |  D/V  |
| AD.6.2 | Bekreft at aggregert tilbakemelding informerer periodisk finjustering eller gjenhentingsforsterket generering med godkjente sikre-kodingskorpus (f.eks. OWASP Cheat Sheets).            |  2   |   D   |
| AD.6.3 | Verifiser at en lukket sløyfe evalueringsplattform kjører regresjonstester etter hver finjustering; sikkerhetsmetrikkene må oppfylle eller overgå tidligere baselines før distribusjon. |  3   |  D/V  |

---

### Referanser

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

