# 11 Personvern og styring av personopplysninger

## Kontrollmål

Oppretthold strenge personvernforpliktelser gjennom hele AI-livssyklusen—innsamling, trening, inferens og hendelseshåndtering—slik at personopplysninger kun behandles med tydelig samtykke, minimum nødvendig omfang, påvisbar sletting og formelle personverngarantier.

---

## 11.1 Anonymisering og dataminimering

|   #    | Beskrivelse                                                                                                                                      | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 11.1.1 | Bekreft at direkte og kvasi-identifikatorer er fjernet eller hashet.                                                                             |  1   |  D/V  |
| 11.1.2 | Verifiser at automatiserte revisjoner måler k-anonymitet/l-mangfold og gir varsler når terskelverdier faller under policy.                       |  2   |  D/V  |
| 11.1.3 | Verifiser at modellens rapporter om funksjonsviktighet bekrefter at det ikke er lekkasje av identifikator utover ε = 0,01 gjensidig informasjon. |  2   |   V   |
| 11.1.4 | Verifiser at formelle bevis eller sertifisering med syntetiske data viser at risikoen for re-identifisering er ≤ 0,05 selv under koblingsangrep. |  3   |   V   |

---

## 11.2 Rett-til-å-bli-glemt og håndheving av sletting

|   #    | Beskrivelse                                                                                                                                                                                       | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.2.1 | Bekreft at forespørsler om sletting av datasubjekter blir videreført til rådatasett, sjekkpunkter, innebygginger, logger og sikkerhetskopier innenfor tjenestenivåavtaler på mindre enn 30 dager. |  1   |  D/V  |
| 11.2.2 | Bekreft at "maskin-avlærings" rutiner fysisk retrener eller tilnærmer fjerning ved bruk av sertifiserte avlæringsalgoritmer.                                                                      |  2   |   D   |
| 11.2.3 | Bekreft at evaluering med skyggemodell viser at glemt data påvirker mindre enn 1 % av resultatene etter glemming.                                                                                 |  2   |   V   |
| 11.2.4 | Bekreft at slettingseventer blir immutabelt loggført og reviderbare for regulatorer.                                                                                                              |  3   |   V   |

---

## 11.3 Differensialpersonvern-sikkerhetstiltak

|   #    | Beskrivelse                                                                                       | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.3.1 | Bekreft at personverntap-regnskapets dashbord varsler når kumulativ ε overskrider policygrensene. |  2   |  D/V  |
| 11.3.2 | Verifiser at black-box personvernsrevisjoner estimerer ε̂ innenfor 10 % av erklært verdi.         |  2   |   V   |
| 11.3.3 | Bekreft at formelle bevis dekker alle etter-trening finjusteringer og innebygginger.              |  3   |   V   |

---

## 11.4 Formålsbegrensning og beskyttelse mot omfangsutvidelse

|   #    | Beskrivelse                                                                                                                       | Nivå | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.4.1 | Bekreft at hvert datasett og modell-sjekkpunkt har en maskinlesbar formålsmerking som er i samsvar med den opprinnelige samtykke. |  1   |   D   |
| 11.4.2 | Verifiser at kjøretidsovervåkere oppdager spørringer som er inkonsistente med deklarert formål og utløser myk avvisning.          |  1   |  D/V  |
| 11.4.3 | Bekreft at policy-as-code-porter blokkerer omdistribusjon av modeller til nye domener uten DPIA-gjennomgang.                      |  3   |   D   |
| 11.4.4 | Bekreft at formelle sporbarhetsbevis viser at hele livssyklusen for personopplysninger forblir innenfor det samtykkede omfanget.  |  3   |   V   |

---

## 11.5 Samtykkebehandling og lovlig grunnlag for sporing

|   #    | Beskrivelse                                                                                                                     | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.5.1 | Bekreft at en samtykkeadministrasjonsplattform (CMP) registrerer opt-in-status, formål og oppbevaringsperiode per datamottaker. |  1   |  D/V  |
| 11.5.2 | Bekreft at API-er eksponerer samtykkebrikker; modeller må validere brikkens omfang før inferens.                                |  2   |   D   |
| 11.5.3 | Bekreft at nektet eller trukket tilbake samtykke stopper behandlingspipelines innen 24 timer.                                   |  2   |  D/V  |

---

## 11.6 Federert læring med personvernkontroller

|   #    | Beskrivelse                                                                                       | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------- | :--: | :---: |
| 11.6.1 | Bekreft at klientoppdateringer benytter lokal differensiell personvernstøy før aggregering.       |  1   |   D   |
| 11.6.2 | Verifiser at treningsmetrikker er differensielt private og aldri avslører tap for enkeltklienter. |  2   |  D/V  |
| 11.6.3 | Bekreft at forgiftningsresistent aggregering (f.eks. Krum/Trimmed-Mean) er aktivert.              |  2   |   V   |
| 11.6.4 | Verifiser at formelle bevis viser en total ε-budsjett med mindre enn 5 nytte-tap.                 |  3   |   V   |

---

### Referanser

* [GDPR & AI Compliance Best Practices](https://www.exabeam.com/explainers/gdpr-compliance/the-intersection-of-gdpr-and-ai-and-6-compliance-best-practices/)
* [EU Parliament Study on GDPR & AI, 2020](https://www.europarl.europa.eu/RegData/etudes/STUD/2020/641530/EPRS_STU%282020%29641530_EN.pdf)
* [ISO 31700-1:2023 — Privacy by Design for Consumer Products](https://www.iso.org/standard/84977.html)
* [NIST Privacy Framework 1.1 (2025 Draft)](https://www.nist.gov/privacy-framework)
* [Machine Unlearning: Right-to-Be-Forgotten Techniques](https://www.kaggle.com/code/tamlhp/machine-unlearning-the-right-to-be-forgotten)
* [A Survey of Machine Unlearning, 2024](https://arxiv.org/html/2209.02299v6)
* [Auditing DP-SGD — ArXiv 2024](https://arxiv.org/html/2405.14106v4)
* [DP-SGD Explained — PyTorch Blog](https://medium.com/pytorch/differential-privacy-series-part-1-dp-sgd-algorithm-explained-12512c3959a3)
* [Purpose-Limitation for AI — IJLIT 2025](https://academic.oup.com/ijlit/article/doi/10.1093/ijlit/eaaf003/8121663)
* [Data-Protection Considerations for AI — URM Consulting](https://www.urmconsulting.com/blog/data-protection-considerations-for-artificial-intelligence-ai)
* [Top Consent-Management Platforms, 2025](https://www.enzuzo.com/blog/best-consent-management-platforms)
* [Secure Aggregation in DP Federated Learning — ArXiv 2024](https://arxiv.org/abs/2407.19286)

