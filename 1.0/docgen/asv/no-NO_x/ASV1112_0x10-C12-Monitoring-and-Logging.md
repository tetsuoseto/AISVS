# C12 Overvåkning, logging og anomalideteksjon

## Kontrollmål

Denne seksjonen gir krav for å levere sanntids- og rettsmedisinsk innsikt i hva modellen og andre AI-komponenter ser, gjør og returnerer, slik at trusler kan oppdages, vurderes og læres av.

## C12.1 Forespørsels- og responslogging

|   #    | Beskrivelse                                                                                                                                                                                                                       | Nivå | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.1.1 | Bekreft at alle brukerforespørsler og modellresponser blir logget med riktig metadata (f.eks. tidsstempel, bruker-ID, økt-ID, modellversjon).                                                                                     |  1   |  D/V  |
| 12.1.2 | Bekreft at logger lagres i sikre, tilgangskontrollerte depot med passende retningslinjer for oppbevaring og sikkerhetskopieringsprosedyrer.                                                                                       |  1   |  D/V  |
| 12.1.3 | Bekreft at logglagringssystemer implementerer kryptering i hvilemodus og under overføring for å beskytte sensitiv informasjon som finnes i logger.                                                                                |  1   |  D/V  |
| 12.1.4 | Bekreft at sensitiv data i forespørsler og svar automatisk blir maskert eller fjernet før logging, med konfigurerbare regler for maskering av personlig identifiserbar informasjon (PII), legitimasjon og proprietær informasjon. |  1   |  D/V  |
| 12.1.5 | Bekreft at politiske beslutninger og sikkerhetsfiltreringshandlinger logges med tilstrekkelig detalj for å muliggjøre revisjon og feilsøking av innholdsmodereringssystemer.                                                      |  2   |  D/V  |
| 12.1.6 | Sørg for at loggens integritet er beskyttet gjennom for eksempel kryptografiske signaturer eller skrivebeskyttet lagring.                                                                                                         |  2   |  D/V  |

---

## C12.2 Misbruk Oppdagelse og Varsling

|   #    | Beskrivelse                                                                                                                                                                             | Nivå | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.2.1 | Bekreft at systemet oppdager og varsler om kjente jailbreak-mønstre, forsøk på promptinjeksjon og fiendtlige input ved bruk av signaturbasert deteksjon.                                |  1   |  D/V  |
| 12.2.2 | Verifiser at systemet integreres med eksisterende Security Information and Event Management (SIEM)-plattformer ved bruk av standard loggformater og protokoller.                        |  1   |  D/V  |
| 12.2.3 | Bekreft at berikede sikkerhetshendelser inkluderer AI-spesifikk kontekst som modellidentifikatorer, tillitsvurderinger og beslutninger om sikkerhetsfiltre.                             |  2   |  D/V  |
| 12.2.4 | Bekreft at atferdsavvikdeteksjon identifiserer uvanlige samtalemønstre, overdrevne gjentaksforsøk eller systematiske sonderingsatferder.                                                |  2   |  D/V  |
| 12.2.5 | Verifiser at mekanismer for sanntidsvarsling varsler sikkerhetsteam når potensielle policybrudd eller angrepsforsøk oppdages.                                                           |  2   |  D/V  |
| 12.2.6 | Bekreft at egendefinerte regler er inkludert for å oppdage AI-spesifikke trusselmønstre, inkludert koordinerte jailbreak-forsøk, kampanjer med promptinjeksjon og modelluttrekksangrep. |  2   |  D/V  |
| 12.2.7 | Bekreft at automatiserte arbeidsflyter for hendelsesrespons kan isolere kompromitterte modeller, blokkere ondsinnede brukere og eskalere kritiske sikkerhetshendelser.                  |  3   |  D/V  |

---

## C12.3 Modellavvikdeteksjon

|   #    | Beskrivelse                                                                                                                                                                              | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.3.1 | Verifiser at systemet sporer grunnleggende ytelsesmålinger som nøyaktighet, konfidenspoeng, latenstid og feilrater på tvers av modellversjoner og tidsperioder.                          |  1   |  D/V  |
| 12.3.2 | Verifiser at automatiske varslinger utløses når ytelsesmetrikker overskrider forhåndsdefinerte terskler for nedgang eller avviker betydelig fra baslinjer.                               |  2   |  D/V  |
| 12.3.3 | Bekreft at overvåkingsverktøy for hallusinasjonsdeteksjon identifiserer og markerer tilfeller der modellutdata inneholder faktuelt feilaktig, inkonsekvent eller fabrikkert informasjon. |  2   |  D/V  |

---

## C12.4 Ytelses- og atferdstelemetri

|   #    | Beskrivelse                                                                                                                                            | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 12.4.1 | Sørg for at driftsmålinger, inkludert forespørselsforsinkelse, tokenforbruk, minnebruk og gjennomstrømning, kontinuerlig blir samlet inn og overvåket. |  1   |  D/V  |
| 12.4.2 | Bekreft at suksess- og feilsatser spores med kategorisering av feiltyper og deres grunnårsaker.                                                        |  1   |  D/V  |
| 12.4.3 | Bekreft at overvåking av ressursbruk inkluderer GPU/CPU-bruk, minneforbruk og lagringsbehov med varsling ved terskeloverskridelser.                    |  2   |  D/V  |

---

## C12.5 Planlegging og gjennomføring av AI-hendelseshåndtering

|   #    | Beskrivelse                                                                                                                                                         | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.5.1 | Bekreft at beredskapsplaner for hendelser spesifikt dekker AI-relaterte sikkerhetshendelser, inkludert modellkompromittering, datatoksinering og fiendtlige angrep. |  1   |  D/V  |
| 12.5.2 | Sørg for at hendelsesresponsteam har tilgang til AI-spesifikke rettsmedisinske verktøy og ekspertise for å undersøke modellens oppførsel og angrepsvektorer.        |  2   |  D/V  |
| 12.5.3 | Bekreft at post-incident-analyse inkluderer vurderinger av modellretraining, oppdateringer av sikkerhetsfiltre og integrering av lærdommer i sikkerhetskontroller.  |  3   |  D/V  |

---

## C12.6 AI-ytelsesnedgangsdeteksjon

Overvåk og oppdag nedgang i AI-modellens ytelse og kvalitet over tid.

|   #    | Beskrivelse                                                                                                                          | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 12.6.1 | Sikre at modellens nøyaktighet, presisjon, tilbakekalling og F1-poeng kontinuerlig overvåkes og sammenlignes med baselinenivåene.    |  1   |  D/V  |
| 12.6.2 | Bekreft at overvåking av dataavvik oppdager endringer i inngangsfordelingen som kan påvirke modellens ytelse.                        |  1   |  D/V  |
| 12.6.3 | Verifiser at konseptdriftoppdagelse identifiserer endringer i forholdet mellom innganger og forventede utganger.                     |  2   |  D/V  |
| 12.6.4 | Bekreft at ytelsesforringelse utløser automatiske varsler og starter arbeidsflyter for modell-omtrening eller utskiftning.           |  2   |  D/V  |
| 12.6.5 | Bekreft at rotårsaksanalyse for degradering korrelerer ytelsesfall med datendringer, infrastrukturproblemer eller eksterne faktorer. |  3   |   V   |

---

## C12.7 DAG-visualisering og arbeidsflytsikkerhet

Beskytt arbeidsflytvisualiseringssystemer mot informasjonslekkasje og manipuleringsangrep.

|   #    | Beskrivelse                                                                                                                                                 | Nivå | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 12.7.1 | Verifiser at DAG-visualiseringsdata blir renset for å fjerne sensitiv informasjon før lagring eller overføring.                                             |  1   |  D/V  |
| 12.7.2 | Bekreft at tilgangskontroller for arbeidsflytvisualisering sikrer at kun autoriserte brukere kan se agentens beslutningsveier og resonnementsspor.          |  1   |  D/V  |
| 12.7.3 | Verifiser at integriteten til DAG-data beskyttes gjennom kryptografiske signaturer og manipulasjonsbevisste lagringsmekanismer.                             |  2   |  D/V  |
| 12.7.4 | Bekreft at systemer for arbeidsflytvisualisering implementerer inndata-validering for å forhindre injeksjonsangrep gjennom konstruerte nod- eller kantdata. |  2   |  D/V  |
| 12.7.5 | Bekreft at sanntidsoppdateringer av DAG er hastighetsbegrenset og validert for å forhindre tjenestenektangrep på visualiseringssystemer.                    |  3   |  D/V  |

---

## C12.8 Proaktiv overvåking av sikkerhetsatferd

Deteksjon og forebygging av sikkerhetstrusler gjennom proaktiv agentatferdsanalyse.

|   #    | Beskrivelse                                                                                                              | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 12.8.1 | Bekreft at proaktive agentatferder er sikkerhetsvalidert før utførelse med integrasjon av risikovurdering.               |  1   |  D/V  |
| 12.8.2 | Bekreft at autonome initiativutløsere inkluderer evaluering av sikkerhetskontekst og vurdering av trussellandskapet.     |  2   |  D/V  |
| 12.8.3 | Sørg for at proaktive atferdsmønstre blir analysert for potensielle sikkerhetsimplikasjoner og utilsiktede konsekvenser. |  2   |  D/V  |
| 12.8.4 | Bekreft at sikkerhetskritiske proaktive handlinger krever eksplisitte godkjenningskjeder med revisjonsspor.              |  3   |  D/V  |
| 12.8.5 | Bekreft at oppdagelse av atferdsavvik identifiserer avvik i proaktive agentmønstre som kan indikere kompromittering.     |  3   |  D/V  |

---

## Referanser

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)

