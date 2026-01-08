# C13 Menneskelig tilsyn, ansvarlighet og styring

## Kontrollmål

Dette kapittelet gir krav for å opprettholde menneskelig tilsyn og klare ansvarskjeder i AI-systemer, og sikrer forklarbarhet, åpenhet og etisk forvaltning gjennom hele AI-livssyklusen.

---

## C13.1 Drep-knapp og overstyringsmekanismer

Gi avstengings- eller tilbakestillingsmuligheter når utrygg oppførsel hos AI-systemet observeres.

|   #    | Beskrivelse                                                                                                            | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.1.1 | Bekreft at det finnes en manuell avstengingsmekanisme for å umiddelbart stoppe AI-modellens inferens og utdata.        |  1   |  D/V  |
| 13.1.2 | Bekreft at overstyringskontroller kun er tilgjengelige for autorisert personell.                                       |  1   |   D   |
| 13.1.3 | Bekreft at tilbakestillingsprosedyrer kan gjenopprette til tidligere modellversjoner eller sikkerhetsmodusoperasjoner. |  3   |  D/V  |
| 13.1.4 | Sørg for at overstyringsmekanismer testes jevnlig.                                                                     |  3   |   V   |

---

## C13.2 Mennesket-i-sløyfen beslutningskontrollpunkter

Krev menneskelig godkjenning når innsatsen overskrider forhåndsdefinerte risikogrenseverdier.

|   #    | Beskrivelse                                                                                                                             | Nivå | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.2.1 | Bekreft at høy-risiko AI-beslutninger krever eksplisitt menneskelig godkjenning før utførelse.                                          |  1   |  D/V  |
| 13.2.2 | Bekreft at risikogrensene er klart definert og automatisk utløser arbeidsflyter for menneskelig gjennomgang.                            |  1   |   D   |
| 13.2.3 | Bekreft at tidskritiske beslutninger har reserveprosedyrer når menneskelig godkjenning ikke kan oppnås innen de nødvendige tidsrammene. |  2   |   D   |
| 13.2.4 | Bekreft at opptrappingsprosedyrer definerer klare myndighetsnivåer for ulike beslutningstyper eller risikokategorier, hvis aktuelt.     |  3   |  D/V  |

---

## C13.3 Kjede av ansvar & Reviderbarhet

Loggfør operatørhandlinger og modellbeslutninger.

|   #    | Beskrivelse                                                                                                                                 | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.3.1 | Bekreft at alle AI-systembeslutninger og menneskelige inngrep blir loggført med tidsstempler, brukeridentiteter og beslutningsbegrunnelser. |  1   |  D/V  |
| 13.3.2 | Verifiser at revisjonslogger ikke kan manipuleres og inkluder integritetsverifikasjonsmekanismer.                                           |  2   |   D   |

---

## C13.4 Forklarbare AI-teknikker

Overflatefunksjonsviktighet, kontrafaktiske tilfeller og lokale forklaringer.

|   #    | Beskrivelse                                                                                                                                    | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.4.1 | Bekreft at KI-systemer gir grunnleggende forklaringer på sine avgjørelser i et menneskelig lesbart format.                                     |  1   |  D/V  |
| 13.4.2 | Bekreft at forklaringskvaliteten er validert gjennom menneskelige evalueringsstudier og målemetoder.                                           |  2   |   V   |
| 13.4.3 | Bekreft at funksjonsviktighetsresultater eller attribusjonsmetoder (SHAP, LIME osv.) er tilgjengelige for kritiske beslutninger.               |  3   |  D/V  |
| 13.4.4 | Bekreft at kontrafaktiske forklaringer viser hvordan innganger kan endres for å endre utfall, hvis det er aktuelt for bruksområdet og domenet. |  3   |   V   |

---

## C13.5 Modellkort og bruksopplysninger

Oppretthold modellkort for tilsiktet bruk, ytelsesmålinger og etiske hensyn.

|   #    | Beskrivelse                                                                                                                                                                               | Nivå | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.5.1 | Bekreft at modellkort dokumenterer tiltenkte bruksområder, begrensninger og kjente feilmåter.                                                                                             |  1   |   D   |
| 13.5.2 | Bekreft at ytelsesmålinger for ulike relevante bruksområder er oppgitt.                                                                                                                   |  1   |  D/V  |
| 13.5.3 | Bekreft at etiske hensyn, vurderinger av skjevhet, evalueringer av rettferdighet, egenskaper ved treningsdata og kjente begrensninger i treningsdata er dokumentert og oppdatert jevnlig. |  2   |   D   |
| 13.5.4 | Bekreft at modellkortene er versjonskontrollert og vedlikeholdt gjennom hele modellens livssyklus med sporing av endringer.                                                               |  2   |  D/V  |

---

## C13.6 Usikkerhetskvantifisering

Propager konfidenspoeng eller entropimål i svar.

|   #    | Beskrivelse                                                                                                    | Nivå | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.6.1 | Bekreft at AI-systemer gir konfidenspoeng eller usikkerhetsmål sammen med sine resultater.                     |  1   |   D   |
| 13.6.2 | Bekreft at usikkerhetsterskler utløser ytterligere menneskelig gjennomgang eller alternative beslutningsveier. |  2   |  D/V  |
| 13.6.3 | Bekreft at metoder for usikkerhetskvantifisering er kalibrert og validert mot faktiske data.                   |  2   |   V   |
| 13.6.4 | Bekreft at usikkerhetspropagasjon opprettholdes gjennom flerstegs AI-arbeidsflyter.                            |  3   |  D/V  |

---

## C13.7 Brukerrettede transparensrapporter

Gi periodiske avsløringer om hendelser, avvik og databruk.

|   #    | Beskrivelse                                                                                                                  | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 13.7.1 | Bekreft at retningslinjer for databruk og praksis for håndtering av brukersamtykke er tydelig kommunisert til interessenter. |  1   |  D/V  |
| 13.7.2 | Verifiser at AI-påvirkningsvurderinger gjennomføres og at resultatene inkluderes i rapporteringen.                           |  2   |  D/V  |
| 13.7.3 | Bekreft at rapporter om åpenhet som publiseres regelmessig, offentliggjør AI-hendelser og driftsmålinger i rimelig detalj.   |  2   |  D/V  |

### Referanser

* [EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
* [ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management](https://www.iso.org/standard/77304.html)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [NIST SP 800-53 Revision 5 — Security and Privacy Controls](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-53r5.pdf)
* [A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)](https://arxiv.org/abs/1705.07874)
* [Model Cards for Model Reporting (Mitchell et al., 2018)](https://arxiv.org/abs/1810.03993)
* [Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)](https://arxiv.org/abs/1506.02142)
* [ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods](https://www.iso.org/standard/79804.html)
* [IEEE 7001-2021 — Transparency of Autonomous Systems](https://standards.ieee.org/ieee/7001/6929/)
* [Human Oversight under Article 14 of the EU AI Act (Fink, 2025)](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=5147196)

