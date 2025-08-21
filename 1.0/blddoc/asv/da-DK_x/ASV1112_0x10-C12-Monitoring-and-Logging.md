# C12 Overvågning, Logning og Anomalidetektion

## Kontrolmål

Denne sektion giver krav til levering af realtids- og retsmedicinsk synlighed i, hvad modellen og andre AI-komponenter ser, gør og returnerer, så trusler kan opdages, prioriteres og læres af.

## C12.1 Anmodning og svar logning

|   #    | Beskrivelse                                                                                                                                                                                                                                       | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.1.1 | Bekræft, at alle brugerforespørgsler og modelresponser bliver logget med passende metadata (f.eks. tidsstempel, bruger-ID, sessions-ID, modelversion).                                                                                            |   1    |  D/V  |
| 12.1.2 | Bekræft, at logs gemmes i sikre, adgangskontrollerede arkiver med passende opbevaringspolitikker og backupprocedurer.                                                                                                                             |   1    |  D/V  |
| 12.1.3 | Bekræft, at loglagringssystemer implementerer kryptering både ved lagring og under overførsel for at beskytte følsomme oplysninger indeholdt i logs.                                                                                              |   1    |  D/V  |
| 12.1.4 | Bekræft, at følsomme data i prompts og output automatisk bliver redigeret eller maskeret før logning, med konfigurerbare redigeringsregler for personligt identificerbare oplysninger (PII), legitimationsoplysninger og proprietære oplysninger. |   1    |  D/V  |
| 12.1.5 | Bekræft, at politiske beslutninger og sikkerhedsfiltreringshandlinger logges med tilstrækkelig detaljeringsgrad for at muliggøre revision og fejlfinding af indholdsmoderationssystemer.                                                          |   2    |  D/V  |
| 12.1.6 | Bekræft, at logintegriteten er beskyttet gennem f.eks. kryptografiske signaturer eller skrivebeskyttet lagring.                                                                                                                                   |   2    |  D/V  |

---

## C12.2 Misbrugsdetektion og alarmering

|   #    | Beskrivelse                                                                                                                                                                                 | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.2.1 | Bekræft, at systemet registrerer og alarmerer om kendte jailbreak-mønstre, forsøg på promptinjektion og modstridende input ved hjælp af signaturbaseret detektion.                          |   1    |  D/V  |
| 12.2.2 | Bekræft, at systemet integreres med eksisterende Security Information and Event Management (SIEM)-platforme ved hjælp af standard logformater og -protokoller.                              |   1    |  D/V  |
| 12.2.3 | Bekræft, at berigede sikkerhedshændelser inkluderer AI-specifik kontekst såsom modelidentifikatorer, tillidsvurderinger og beslutninger fra sikkerhedsfiltre.                               |   2    |  D/V  |
| 12.2.4 | Bekræft, at opdagelse af adfærdsafvigelser identificerer usædvanlige samtalemønstre, overdrevne forsøg på genforsøg eller systematiske sonderingsadfærd.                                    |   2    |  D/V  |
| 12.2.5 | Bekræft, at realtidsalarmeringsmekanismer underretter sikkerhedsteams, når potentielle politikovertrædelser eller angrebsforsøg opdages.                                                    |   2    |  D/V  |
| 12.2.6 | Bekræft, at brugerdefinerede regler er inkluderet for at opdage AI-specifikke trusselsmønstre, herunder koordinerede jailbreak-forsøg, promptinjektionskampagner og modeludtrækningsangreb. |   2    |  D/V  |
| 12.2.7 | Bekræft, at automatiserede hændelsesrespons-workflows kan isolere kompromitterede modeller, blokere ondsindede brugere og eskalere kritiske sikkerhedshændelser.                            |   3    |  D/V  |

---

## C12.3 Model Drift Overvågning

|   #    | Beskrivelse                                                                                                                                                                                | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 12.3.1 | Bekræft, at systemet sporer grundlæggende ydelsesmetrikker såsom nøjagtighed, tillidsværdier, latenstid og fejlrater på tværs af modelversioner og tidsperioder.                           |   1    |  D/V  |
| 12.3.2 | Bekræft, at automatiseret alarmering udløses, når ydeevnemålinger overskrider foruddefinerede nedbrydningsterskler eller afviger markant fra baselineværdier.                              |   2    |  D/V  |
| 12.3.3 | Bekræft, at overvågningsværktøjer til hallucinationsdetektion identificerer og markerer tilfælde, hvor modeloutput indeholder faktuelt forkert, inkonsistent eller fabrikeret information. |   2    |  D/V  |

---

## C12.4 Ydelse og Adfærd Telemetri

|   #    | Beskrivelse                                                                                                                                                | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.4.1 | Bekræft, at operationelle metrics, herunder forespørgselsforsinkelse, tokenforbrug, hukommelsesforbrug og gennemløb, kontinuerligt indsamles og overvåges. |   1    |  D/V  |
| 12.4.2 | Bekræft, at succes- og fejlsatser spores med kategorisering af fejltyper og deres grundårsager.                                                            |   1    |  D/V  |
| 12.4.3 | Bekræft, at overvågning af ressourceudnyttelse inkluderer GPU/CPU-brug, hukommelsesforbrug og lagerkrav med alarmering ved overskridelse af tærskler.      |   2    |  D/V  |

---

## C12.5 AI hændelsesresponsplanlægning og -udførelse

|   #    | Beskrivelse                                                                                                                                                             | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.5.1 | Verificer, at beredskabsplaner for hændelser specifikt omhandler AI-relaterede sikkerhedshændelser, herunder modelkompromittering, datapoisning og adversariale angreb. |   1    |  D/V  |
| 12.5.2 | Sørg for, at incident response-hold har adgang til AI-specifikke retsmedicinske værktøjer og ekspertise til at undersøge modeladfærd og angrebsvinkler.                 |   2    |  D/V  |
| 12.5.3 | Bekræft, at efter-incident-analyse inkluderer overvejelser om modelgenindlæring, opdateringer af sikkerhedsfiltre og integration af erfaringer i sikkerhedskontroller.  |   3    |  D/V  |

---

## C12.5 AI-ydelsesforringelsesdetektion

Overvåg og påvis forringelse i AI-modelpræstation og kvalitet over tid.

|   #    | Beskrivelse                                                                                                                              | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.5.1 | Sørg for, at modelpræcision, nøjagtighed, tilbagekaldelse og F1-scores løbende overvåges og sammenlignes med baseline-grænseværdier.     |   1    |  D/V  |
| 12.5.2 | Bekræft, at data drift-overvågning registrerer ændringer i inputfordelingen, der kan påvirke modellens ydeevne.                          |   1    |  D/V  |
| 12.5.3 | Bekræft, at konceptdrejningsdetektion identificerer ændringer i forholdet mellem input og forventede output.                             |   2    |  D/V  |
| 12.5.4 | Bekræft, at ydelsesforringelse udløser automatiserede alarmer og igangsætter arbejdsgange for omtræning eller udskiftning af modellen.   |   2    |  D/V  |
| 12.5.5 | Bekræft, at årsagsanalysen for forringelse korrelerer ydelsesfald med datændringer, infrastrukturelle problemer eller eksterne faktorer. |   3    |   V   |

---

## C12.6 DAG-visualisering og workflow-sikkerhed

Beskyt workflow-visualiseringssystemer mod informationslækage og manipulationsangreb.

|   #    | Beskrivelse                                                                                                                                             | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| 12.6.1 | Bekræft, at DAG-visualiseringsdata er renset for at fjerne følsomme oplysninger, inden de lagres eller overføres.                                       |   1    |  D/V  |
| 12.6.2 | Bekræft, at adgangskontroller til workflow-visualisering sikrer, at kun autoriserede brugere kan se agentens beslutningsstier og ræsonnementsspor.      |   1    |  D/V  |
| 12.6.3 | Bekræft, at DAG-dataintegriteten er beskyttet gennem kryptografiske signaturer og manipulation-synlige lagringsmekanismer.                              |   2    |  D/V  |
| 12.6.4 | Verificer, at workflow-visualiseringssystemer implementerer inputvalidering for at forhindre injektionsangreb gennem manipulerede node- eller kantdata. |   2    |  D/V  |
| 12.6.5 | Bekræft, at opdateringer af realtids-DAG'er er ratebegrænsede og validerede for at forhindre denial-of-service-angreb på visualiseringssystemer.        |   3    |  D/V  |

---

## C12.7 Proaktiv overvågning af sikkerhedsadfærd

Detektion og forebyggelse af sikkerhedstrusler gennem proaktiv agentadfærdsanalyse.

|   #    | Beskrivelse                                                                                                                    | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| 12.7.1 | Verificer, at proaktive agentadfærd er sikkerhedsvaliderede før udførelse med integration af risikovurdering.                  |   1    |  D/V  |
| 12.7.2 | Bekræft, at autonome initiativudløsere inkluderer evaluering af sikkerhedskontekst og vurdering af trusselslandskabet.         |   2    |  D/V  |
| 12.7.3 | Bekræft, at proaktive adfærdsmønstre analyseres for potentielle sikkerhedsmæssige konsekvenser og utilsigtede følgevirkninger. |   2    |  D/V  |
| 12.7.4 | Bekræft, at sikkerhedskritiske proaktive handlinger kræver eksplicitte godkendelseskæder med revisionsspor.                    |   3    |  D/V  |
| 12.7.5 | Bekræft, at adfærdsafvigelsesdetektion identificerer afvigelser i proaktive agentmønstre, der kan indikere kompromittering.    |   3    |  D/V  |

---

## Referencer

* [NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6](https://www.iso.org/standard/81230.html)
* [EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R1689)

