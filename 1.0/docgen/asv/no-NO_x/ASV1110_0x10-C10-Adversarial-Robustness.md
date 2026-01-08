# 10 Adversarial robusthet og personvernsforsvar

## Kontrollmål

Sørg for at AI-modeller forblir pålitelige, personvernbevarende og motstandsdyktige mot misbruk når de møter unnvikelse-, inferens-, utvinnings- eller forgiftningsangrep.

---

## 10.1 Modelljustering og sikkerhet

Beskytter mot skadelig eller policy-bruddende utdata.

|   #    | Beskrivelse                                                                                                                                              | Nivå | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.1.1 | Bekreft at en justerings-testpakke (red-team prompts, jailbreak-prober, ikke tillatt innhold) er versjonskontrollert og kjøres ved hver modellutgivelse. |  1   |  D/V  |
| 10.1.2 | Sjekk at nektelse og sikker fullføringsbeskyttelse er håndhevet.                                                                                         |  1   |   D   |
| 10.1.3 | Verifiser at en automatisert evaluator måler andelen skadelig innhold og merker tilbakefall som overskrider en satt terskel.                             |  2   |  D/V  |
| 10.1.4 | Verifiser at treningen mot jailbreak er dokumentert og kan gjenskapes.                                                                                   |  2   |   D   |
| 10.1.5 | Bekreft at formelle bevis for etterlevelse av policy eller sertifisert overvåking dekker kritiske domener.                                               |  3   |   V   |

---

## 10.2 Motstandsdyktighet mot angrepseksempler

Øk motstandsdyktigheten mot manipulerte inndata. Robust adversarial-trening og vurdering med referansedata er dagens beste praksis.

|   #    | Beskrivelse                                                                                                            | Nivå | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.2.1 | Bekreft at prosjektrepositorier inkluderer konfigurasjoner for adversarial-trening med reproduserbare frø.             |  1   |   D   |
| 10.2.2 | Bekreft at deteksjon av adversariale eksempler utløser blokkeringvarsler i produksjonspipelines.                       |  2   |  D/V  |
| 10.2.4 | Bekreft at sertifiserte robusthetsbevis eller intervallgrense-sertifikater dekker minst de mest kritiske toppklassene. |  3   |   V   |
| 10.2.5 | Bekreft at regresjonstester bruker adaptive angrep for å bekrefte at det ikke er noe målbar reduksjon i robusthet.     |  3   |   V   |

---

## 10.3 Dempe mot medlemskap-inferens

Begrens muligheten til å avgjøre om en post var i treningsdataene. Differensialpersonvern og maskering av konfidensscore forblir de mest effektive kjente forsvarsmekanismene.

|   #    | Beskrivelse                                                                                                  | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------ | :--: | :---: |
| 10.3.1 | Verifiser at entropiregulering per spørring eller temperaturskalering reduserer overkonfidente prediksjoner. |  1   |   D   |
| 10.3.2 | Bekreft at treningen bruker ε-avgrenset differensielt privat optimalisering for sensitive datasett.          |  2   |   D   |
| 10.3.3 | Bekreft at angrepssimuleringer (skyggemodell eller black-box) viser angreps-AUC ≤ 0,60 på hold-out data.     |  2   |   V   |

---

## 10.4 Motstandsdyktighet mot modellinversjon

Forhindre rekonstruksjon av private attributter. Nyere undersøkelser understreker utdataforkortelse og DP-garantier som praktiske forsvar.

|   #    | Beskrivelse                                                                                                                | Nivå | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.4.1 | Sørg for at sensitive attributter aldri blir direkte vist; bruk bøtter eller enveis transformasjoner der det er nødvendig. |  1   |   D   |
| 10.4.2 | Bekreft at spørringsfrekvensgrenser begrenser gjentatte adaptive spørringer fra samme prinsipal.                           |  1   |  D/V  |
| 10.4.3 | Bekreft at modellen er trent med personvernbevarende støy.                                                                 |  2   |   D   |

---

## 10.5 Modellutvinningsforsvar

Oppdag og avskrekk uautorisert kloning. Vannmerking og analyse av spørringsmønstre anbefales.

|   #    | Beskrivelse                                                                                                                         | Nivå | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.5.1 | Bekreft at inferens-gatewayer håndhever globale og per-API-nøkkel hastighetsbegrensninger tilpasset modellens memoriseringsterskel. |  1   |   D   |
| 10.5.2 | Bekreft at query-entropi og input-mangfoldighetsstatistikk mater en automatisk ekstraksjonsdetektor.                                |  2   |  D/V  |
| 10.5.3 | Bekreft at skjøre eller sannsynlighetsbaserte vannmerker kan bevises med p < 0,01 i ≤ 1 000 spørringer mot en mistenkt klone.       |  2   |   V   |
| 10.5.4 | Bekreft at vannmerkingsnøkler og utløsersett lagres i en hardware-sikkerhetsmodul og roteres årlig.                                 |  3   |   D   |
| 10.5.5 | Sørg for at extraction-alert-hendelser inkluderer de feilaktige spørringene og er integrert med hendelsesrespons-spillebøker.       |  3   |   V   |

---

## 10.6 Oppdagelse av forgiftede data under inferenstidspunktet

Identifisere og nøytralisere bakdøråpnede eller forgiftede innganger.

|   #    | Beskrivelse                                                                                                             | Nivå | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.6.1 | Bekreft at inndata passerer gjennom en anomalidetektor (f.eks. STRIP, konsistensscore) før modellinferens.              |  1   |   D   |
| 10.6.2 | Bekreft at detektortersklene er justert på rene/forurensede valideringssett for å oppnå mindre enn 5 % falske positive. |  1   |   V   |
| 10.6.3 | Bekreft at inndata merket som forgiftet utløser myk-blokkering og arbeidsflyter for menneskelig gjennomgang.            |  2   |   D   |
| 10.6.4 | Verifiser at detektorer blir stresstestet med adaptive, utløserfrie bakdørangrep.                                       |  2   |   V   |
| 10.6.5 | Bekreft at måleparametere for deteksjonseffektivitet blir loggført og periodisk revurdert med oppdatert trusselintel.   |  3   |   D   |

---

## 10.7 Dynamisk tilpasning av sikkerhetspolicy

Sanntidsoppdateringer av sikkerhetspolicy basert på trusselintelligens og atferdsanalyse.

|   #    | Beskrivelse                                                                                                                                           | Nivå | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.7.1 | Bekreft at sikkerhetspolicyer kan oppdateres dynamisk uten at agenten må startes på nytt, samtidig som policyversjonens integritet opprettholdes.     |  1   |  D/V  |
| 10.7.2 | Sørg for at policyoppdateringer er kryptografisk signert av autorisert sikkerhetspersonell og validert før de brukes.                                 |  2   |  D/V  |
| 10.7.3 | Bekreft at dynamiske policyendringer loggføres med fullstendige revisjonsspor, inkludert begrunnelse, godkjenningskjeder og tilbakeføringsprosedyrer. |  2   |  D/V  |
| 10.7.4 | Bekreft at adaptive sikkerhetsmekanismer justerer sensitiviteten i trusseldeteksjon basert på risikokontekst og atferdsmønstre.                       |  3   |  D/V  |
| 10.7.5 | Sørg for at beslutninger om tilpasning av retningslinjer er forklarlige og inkluderer bevisstier for sikkerhetsteamets gjennomgang.                   |  3   |  D/V  |

---

## 10.8 Refleksjonsbasert sikkerhetsanalyse

Sikkerhetsvalidering gjennom agentens selvrefleksjon og metakognitiv analyse.

|   #    | Beskrivelse                                                                                                                                       | Nivå | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.8.1 | Bekreft at agentens refleksjonsmekanismer inkluderer sikkerhetsfokusert egenvurdering av beslutninger og handlinger.                              |  1   |  D/V  |
| 10.8.2 | Verifiser at refleksjonsutdata valideres for å forhindre manipulering av egenvurderingsmekanismer ved hjelp av fiendtlige inndata.                |  2   |  D/V  |
| 10.8.3 | Bekreft at meta-kognitiv sikkerhetsanalyse identifiserer potensiell skjevhet, manipulasjon eller kompromittering i agenters resonnementprosesser. |  2   |  D/V  |
| 10.8.4 | Bekreft at sikkerhetsvarsler basert på refleksjon utløser forbedret overvåking og potensielle arbeidsflyter for menneskelig inngripen.            |  3   |  D/V  |
| 10.8.5 | Bekreft at kontinuerlig læring fra sikkerhetsrefleksjoner forbedrer trusseldeteksjon uten å forringe legitim funksjonalitet.                      |  3   |  D/V  |

---

## 10.9 Evolusjon og selvforbedringssikkerhet

Sikkerhetskontroller for agentsystemer som er i stand til selvmodifisering og evolusjon.

|   #    | Beskrivelse                                                                                                                 | Nivå | Rolle |
| :----: | --------------------------------------------------------------------------------------------------------------------------- | :--: | :---: |
| 10.9.1 | Bekreft at selvmodifiseringsmuligheter er begrenset til utpekte sikre områder med formelle verifikasjonsgrenser.            |  1   |  D/V  |
| 10.9.2 | Sørg for at evolusjonsforslag gjennomgår sikkerhetseffektvurdering før implementering.                                      |  2   |  D/V  |
| 10.9.3 | Verifiser at selvforbedringsmekanismer inkluderer tilbakeføringsmuligheter med integritetsverifisering.                     |  2   |  D/V  |
| 10.9.4 | Verifiser at meta-læringssikkerhet forhindrer fiendtlig manipulasjon av forbedringsalgoritmer.                              |  3   |  D/V  |
| 10.9.5 | Verifiser at rekursiv selvforbedring er begrenset av formelle sikkerhetsbegrensninger med matematiske bevis for konvergens. |  3   |  D/V  |

---

### Referanser

* [MITRE ATLAS adversary tactics for ML](https://atlas.mitre.org/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Adversarial Training: A Survey — Zhao et al., 2024](https://arxiv.org/abs/2410.15042)
* [RobustBench adversarial-robustness benchmark](https://robustbench.github.io/)
* [Membership-Inference & Model-Inversion Risk Survey, 2025](https://www.sciencedirect.com/science/article/abs/pii/S0950705125003867)
* [PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023](https://ojs.aaai.org/index.php/AAAI/article/view/26289)
* [Model-Inversion Attacks & Defenses Survey — AI Review, 2025](https://link.springer.com/article/10.1007/s10462-025-11248-0)
* [Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024](https://doi.org/10.1109/TDSC.2023.3261327)
* [Fragile Model Watermarking Survey — 2025](https://www.sciencedirect.com/science/article/abs/pii/S0165168425002026)
* [Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025](https://arxiv.org/abs/2503.22759)
* [BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024](https://arxiv.org/abs/2405.15269)

