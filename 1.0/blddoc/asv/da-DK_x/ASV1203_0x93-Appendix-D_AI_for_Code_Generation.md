# Appendiks D: AI-assisteret styring og verifikation af sikker kodning

## Mål

Dette kapitel definerer baseline organisatoriske kontroller for sikker og effektiv brug af AI-assisterede kodningsværktøjer under softwareudvikling og sikrer sikkerhed og sporbarhed gennem hele SDLC.

---

## AD.1 AI-assisteret sikker-kodings arbejdsgang

Integrer AI-værktøjer i organisationens sikre softwareudviklingslivscyklus (SSDLC) uden at svække de eksisterende sikkerhedsporter.

|   #    | Beskrivelse                                                                                                                                                      | Niveau | Rolle |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| AD.1.1 | Bekræft, at en dokumenteret arbejdsgang beskriver, hvornår og hvordan AI-værktøjer kan generere, omstrukturere eller gennemgå kode.                              |   1    |  D/V  |
| AD.1.2 | Bekræft, at workflowet svarer til hver fase i SSDLC (design, implementering, kodegennemgang, test, implementering).                                              |   2    |   D   |
| AD.1.3 | Bekræft, at metrikker (f.eks. sårbarhedstæthed, gennemsnitlig tid til opdagelse) indsamles for AI-genereret kode og sammenlignes med kun menneskelige baselines. |   3    |  D/V  |

---

## AD.2 AI-værktøjskvalificering og trusselsmodellering

Sørg for, at AI-kodeværktøjer vurderes for sikkerhedsfunktioner, risiko og forsyningskædepåvirkning inden implementering.

|   #    | Beskrivelse                                                                                                                                                                                     | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| AD.2.1 | Bekræft, at en trusselsmodel for hvert AI-værktøj identificerer misbrug, modelinversion, data lækage og afhængighedskæde-risici.                                                                |   1    |  D/V  |
| AD.2.2 | Bekræft, at blivevurderinger af værktøjer inkluderer statisk/dynamisk analyse af eventuelle lokale komponenter samt vurdering af SaaS-endepunkter (TLS, autentificering/autorisation, logning). |   2    |   D   |
| AD.2.3 | Verificer, at evalueringer følger en anerkendt ramme og udføres igen efter større versionsændringer.                                                                                            |   3    |  D/V  |

---

## AD.3 Sikker Prompt- og Kontekststyring

Forebyg lækage af hemmeligheder, proprietær kode og persondata ved opbygning af prompts eller kontekster til AI-modeller.

|   #    | Beskrivelse                                                                                                                                                  | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :---: |
| AD.3.1 | Bekræft, at skriftlige retningslinjer forbyder at sende hemmeligheder, legitimationsoplysninger eller klassificerede data i prompts.                         |   1    |  D/V  |
| AD.3.2 | Bekræft, at tekniske kontroller (klient-side redigering, godkendte kontekstfiltre) automatisk fjerner følsomme elementer.                                    |   2    |   D   |
| AD.3.3 | Bekræft, at prompts og svar bliver tokeniseret, krypteret under overførsel og i hvile, og at opbevaringsperioderne overholder dataklassifikationspolitikken. |   3    |  D/V  |

---

## AD.4 Validering af AI-genereret kode

Registrer og udbedr sårbarheder, som AI-output har introduceret, før koden flettes eller implementeres.

|   #    | Beskrivelse                                                                                                                                                          | Niveau | Rolle |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| AD.4.1 | Sørg for, at AI-genereret kode altid gennemgås af mennesker.                                                                                                         |   1    |  D/V  |
| AD.4.2 | Bekræft, at automatiserede scannere (SAST/IAST/DAST) kører på hver pull-anmodning, der indeholder AI-genereret kode, og blokerer sammenfletninger ved kritiske fund. |   2    |   D   |
| AD.4.3 | Bekræft, at differential fuzz testing eller egenskabsbaserede tests beviser sikkerhedskritiske adfærd (f.eks. inputvalidering, autorisationslogik).                  |   3    |  D/V  |

---

## AD.5 Forklarbarhed og Sporbarhed af Kodeforslag

Giv revisorer og udviklere indsigt i, hvorfor et forslag blev fremsat, og hvordan det udviklede sig.

|   #    | Beskrivelse                                                                                                                                                               | Niveau | Rolle |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| AD.5.1 | Bekræft, at prompt-/responspar logges med commit-ID'er.                                                                                                                   |   1    |  D/V  |
| AD.5.2 | Sørg for, at udviklere kan fremvise modellens referencer (træningsudsnit, dokumentation), der understøtter et forslag.                                                    |   2    |   D   |
| AD.5.3 | Bekræft, at forklaringsrapporter gemmes sammen med designartefakter og refereres til i sikkerhedsgennemgange, således at de opfylder ISO/IEC 42001 sporbarhedsprincipper. |   3    |  D/V  |

---

## AD.6 Kontinuerlig feedback og modeljustering

Forbedr modelens sikkerhedsydelse over tid samtidig med at forhindre negativ drift.

|   #    | Beskrivelse                                                                                                                                                                               | Niveau | Rolle |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :---: |
| AD.6.1 | Bekræft, at udviklere kan markere usikre eller ikke-overholdende forslag, og at markeringerne bliver registreret.                                                                         |   1    |  D/V  |
| AD.6.2 | Bekræft, at samlet feedback informerer periodisk finjustering eller retrieval-augmenteret generering med gennemgåede sikre-kodingskorpora (f.eks. OWASP Cheat Sheets).                    |   2    |   D   |
| AD.6.3 | Bekræft, at et lukket system evalueringsværktøj kører regressions tests efter hver finjustering; sikkerhedsmetrikker skal opfylde eller overstige tidligere baselines før implementering. |   3    |  D/V  |

---

### Referencer

* [NIST AI Risk Management Framework 1.0](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [ISO/IEC 42001:2023 — AI Management Systems Requirements](https://www.iso.org/standard/81230.html)
* [OWASP Secure Coding Practices — Quick Reference Guide](https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/)

