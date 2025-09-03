# 9 Autonome Orkestratie & Beveiliging van agentische acties

## Beheersdoel

Zorg ervoor dat autonome of multi-agent AI-systemen alleen acties kunnen uitvoeren die expliciet bedoeld, geauthenticeerd en auditbaar zijn, en binnen begrensde kosten- en risicodrempels vallen. Dit beschermt tegen bedreigingen zoals autonoom-systeemcompromis, gereedschapmisbruik, agentlusdetectie, communicatiekaping, identiteitsvervalsing, zwermmanipulatie en intentie-manipulatie.

---

## 9.1 Agent Taak-Planning & Recursiebudgetten

Vertraag recursieve plannen en verplicht menselijke controlepunten voor bevoorrechte acties.

|   #   | Beschrijving                                                                                                                                                                                       | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.1.1 | Verifieer dat de maximale recursiediepte, breedte, wall-clock tijd, tokens en de monetaire kosten per agentuitvoering centraal zijn geconfigureerd en onder versiebeheer staan.                    |   1    | D/V |
| 9.1.2 | Verifieer dat bevoorrechte of onomkeerbare acties (bijv. code commits, financiële overboekingen) expliciete menselijke goedkeuring vereisen via een auditbaar kanaal voordat ze worden uitgevoerd. |   1    | D/V |
| 9.1.3 | Verifieer dat real-time resource-monitoren een circuit-breaker onderbreking activeren wanneer een budgetdrempel wordt overschreden, waardoor verdere taakuitbreiding wordt stopgezet.              |   2    |  D  |
| 9.1.4 | Controleer of circuit-breaker-gebeurtenissen worden gelogd met agent-ID, triggerende voorwaarde en vastgelegde planstatus voor forensisch onderzoek.                                               |   2    | D/V |
| 9.1.5 | Verifieer dat beveiligingstests budget-uitputting en runaway-plan scenario's dekken, en bevestig een veilige stilstand zonder gegevensverlies.                                                     |   3    |  V  |
| 9.1.6 | Verifieer dat budgetbeleid wordt uitgedrukt als beleid-als-code en in CI/CD wordt afgedwongen om configuratiedrift tegen te gaan.                                                                  |   3    |  D  |

---

## 9.2 Toolplugin Sandboxing

Isoleer interacties met tools om ongeautoriseerde toegang tot systemen of uitvoering van code te voorkomen.

|   #   | Beschrijving                                                                                                                                                                                     | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 9.2.1 | Verifieer dat elk hulpmiddel of plug-in binnen een OS-, container- of WASM-niveau sandbox uitvoert met beleid voor minimale privileges voor het bestandssysteem, het netwerk en systeemoproepen. |   1    | D/V |
| 9.2.2 | Verifieer dat sandbox-omgeving-bronnenquota's (CPU, geheugen, schijf, uitgaand netwerkverkeer) en time-outs voor uitvoering afgedwongen en gelogd worden.                                        |   1    | D/V |
| 9.2.3 | Controleer of tool-binaries of descriptor-bestanden digitaal ondertekend zijn; de handtekeningen worden gevalideerd voordat ze worden geladen.                                                   |   2    | D/V |
| 9.2.4 | Controleer of sandbox-telemetrie naar een SIEM stroomt; afwijkingen (bijv. pogingen tot uitgaande verbindingen) genereren waarschuwingen.                                                        |   2    |  V  |
| 9.2.5 | Controleer dat hoog-risico-plugins een beveiligingsbeoordeling en penetratietesten ondergaan voordat ze in productie worden uitgerold.                                                           |   3    |  V  |
| 9.2.6 | Controleer dat pogingen tot sandbox-uitbraak automatisch worden geblokkeerd en de betreffende plug-in in quarantaine wordt geplaatst in afwachting van onderzoek.                                |   3    | D/V |

---

## 9.3 Autonome Lus & Kostenbegrenzing

Detecteer en stop onbeheerde agent-tot-agent recursie en kostenexplosies.

|   #   | Beschrijving                                                                                                                                              | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.3.1 | Controleer of inter-agent-aanroepen een hop-limiet of TTL bevatten die door de runtime wordt afgetrokken en afgedwongen.                                  |   1    | D/V |
| 9.3.2 | Verifieer dat agenten een uniek invocation-graph-ID bijhouden om zelfinvocatie of cyclische patronen te detecteren.                                       |   2    |  D  |
| 9.3.3 | Controleer of de cumulatieve rekeneenheden en bestedings-tellers per verzoekketen worden bijgehouden; het overschrijden van de limiet beëindigt de keten. |   2    | D/V |
| 9.3.4 | Verifieer dat formele analyse of model checking de afwezigheid van onbeperkte recursie in agentprotocollen aantoont.                                      |   3    |  V  |
| 9.3.5 | Controleer of lus-afbrekingsgebeurtenissen waarschuwingen genereren en input leveren voor continue-verbeteringsmetingen.                                  |   3    |  D  |

---

## 9.4 Bescherming tegen misbruik op protocolniveau

Beveiligde communicatiekanalen tussen agenten en externe systemen om kaping of manipulatie te voorkomen.

|   #   | Beschrijving                                                                                                                                                    | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.4.1 | Verifieer dat alle berichten van agent-naar-tool en van agent-naar-agent geauthenticeerd zijn (bijv. wederzijdse TLS of JWT) en eind-tot-eind versleuteld zijn. |   1    | D/V |
| 9.4.2 | Controleer dat schema's strikt gevalideerd worden; onbekende velden of misvormde berichten worden geweigerd.                                                    |   1    |  D  |
| 9.4.3 | Verifieer dat integriteitscontroles (MAC's of digitale handtekeningen) de gehele berichtpayload inclusief toolparameters dekken.                                |   2    | D/V |
| 9.4.4 | Verifieer dat replaybescherming (nonces of tijdstempelvensters) op de protocollaag wordt afgedwongen.                                                           |   2    |  D  |
| 9.4.5 | Controleer of protocolimplementaties fuzzing en statische analyse ondergaan om injectie- of deserialisatiefouten op te sporen.                                  |   3    |  V  |

---

## 9.5 Agentidentiteit en Tamper-bewijs

Zorg ervoor dat acties toerekenbaar zijn en wijzigingen detecteerbaar zijn.

|   #   | Beschrijving                                                                                                                                                 | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 9.5.1 | Verifieer dat elke agentinstantie een unieke cryptografische identiteit bezit (sleutelpaar of hardware-gebonden authenticatiegegevens).                      |   1    | D/V |
| 9.5.2 | Verifieer dat alle acties van de agenten zijn ondertekend en voorzien van een tijdstempel; de logs bevatten de handtekeningen voor niet-tegensprekelijkheid. |   2    | D/V |
| 9.5.3 | Verifieer of tamper-evidente logbestanden op een append-only opslagmedium zijn opgeslagen.                                                                   |   2    |  V  |
| 9.5.4 | Controleer dat identiteitssleutels volgens een vast schema en bij indicaties van compromittering roteren.                                                    |   3    |  D  |
| 9.5.5 | Controleer of spoofing- of sleutel-conflictpogingen onmiddellijk de quarantaine van de getroffen agent in gang zetten.                                       |   3    | D/V |

---

## 9.6 Multi-Agent Zwerm Risicoreductie

Beperk de gevaren van collectief gedrag door isolatie en formele veiligheidsmodellering.

|   #   | Beschrijving                                                                                                                             | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.6.1 | Verifieer dat agenten die in verschillende beveiligingsdomeinen opereren, in geïsoleerde runtime-sandboxen of netwerksegmenten draaien.  |   1    | D/V |
| 9.6.2 | Controleer of zwermgedragingen gemodelleerd zijn en formeel geverifieerd op levensvatbaarheid en veiligheid vóór implementatie.          |   3    |  V  |
| 9.6.3 | Controleer of runtime-monitoren opkomende onveilige patronen (bijv. oscillaties, deadlocks) detecteren en corrigerende actie ondernemen. |   3    |  D  |

---

## 9.7 Gebruiker- en Tool-authenticatie / Autorisatie

Implementeer robuuste toegangscontroles voor elke door de agent getriggerde actie.

|   #   | Beschrijving                                                                                                                                              | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.7.1 | Verifieer dat agenten zich authenticeren als first-class principals bij downstream-systemen, en nooit de inloggegevens van de eindgebruiker hergebruiken. |   1    | D/V |
| 9.7.2 | Controleer of fijnmazige autorisatiebeleidsregels beperken welke tools een agent mag aanroepen en welke parameters hij mag meegeven.                      |   2    |  D  |
| 9.7.3 | Verifieer dat machtigingscontroles bij elke oproep opnieuw worden geëvalueerd (doorlopende autorisatie), en niet alleen bij het starten van de sessie.    |   2    |  V  |
| 9.7.4 | Controleer of gedelegeerde machtigingen automatisch verlopen en na time-out of wijziging van de scope opnieuw toestemming vereisen.                       |   3    |  D  |

---

## 9.8 Agent-naar-Agent Communicatiebeveiliging

Versleutel en bescherm de integriteit van alle inter-agent-berichten om afluisteren en manipulatie tegen te gaan.

|   #   | Beschrijving                                                                                                                                                                | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.8.1 | Controleer of wederzijdse authenticatie en encryptie met Perfect Forward Secrecy (PFS) (bijv. TLS 1.3) verplicht zijn voor agentkanalen.                                    |   1    | D/V |
| 9.8.2 | Verifieer dat de integriteit en de herkomst van het bericht vóór verwerking zijn gevalideerd; bij mislukkingen worden meldingen gegenereerd en het bericht wordt verworpen. |   1    |  D  |
| 9.8.3 | Controleer of de communicatie-metagegevens (tijdstempels, sequentienummers) worden gelogd ter ondersteuning van forensische reconstructie.                                  |   2    | D/V |
| 9.8.4 | Verifieer dat formele verificatie of modelcontrole bevestigt dat de toestandsmachines van het protocol niet in onveilige toestanden kunnen worden gebracht.                 |   3    |  V  |

---

## 9.9 Intentieverificatie en Handhaving van Beperkingen

Valideer dat de acties van de agent in overeenstemming zijn met de door de gebruiker aangegeven intentie en de systeembeperkingen.

|   #   | Beschrijving                                                                                                                                                                 | Niveau | Rol |
| :---: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.9.1 | Verifieer dat pre-execution constraint solvers de voorgestelde acties controleren tegen hardgecodeerde veiligheids- en beleidsregels.                                        |   1    |  D  |
| 9.9.2 | Controleer of hoog-impact acties (financiële, destructieve, privacy-gevoelige) expliciete bevestiging van de intentie vereisen door de initiërende gebruiker.                |   2    | D/V |
| 9.9.3 | Verifieer dat postconditiecontroles valideren dat voltooide acties de beoogde effecten hebben bereikt zonder bijwerkingen; afwijkingen leiden tot terugrollen.               |   2    |  V  |
| 9.9.4 | Verifieer dat formele methoden (bijv. modelcontrole, theorembewijzen) of tests op basis van eigenschappen aantonen dat agentplannen aan alle aangegeven beperkingen voldoen. |   3    |  V  |
| 9.9.5 | Verifieer dat intentie-mismatch of constraint-violatie-incidenten bijdragen aan continue-verbeteringscycli en aan het delen van bedreigingsinlichtingen.                     |   3    |  D  |

---

## 9.10 Agent Redeneringsstrategie Beveiliging

Veilige selectie en uitvoering van verschillende redeneringsstrategieën, waaronder ReAct, Chain-of-Thought en Tree-of-Thoughts-benaderingen.

|   #    | Beschrijving                                                                                                                                                                                                                                       | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.10.1 | Verifieer dat de selectie van de redeneringsstrategie deterministische criteria hanteert (invoercomplexiteit, taaktype, beveiligingscontext) en dat identieke inputs identieke strategiekeuzes oplevert binnen dezelfde beveiligingscontext.       |   1    | D/V |
| 9.10.2 | Controleer of elke redeneringsstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) beschikt over specifieke invoervalidatie, uitvoersanitatie en uitvoeringstijdlimieten die specifiek zijn voor haar cognitieve benadering.                      |   1    | D/V |
| 9.10.3 | Controleer dat de overgangen tussen redeneringsstrategieën volledig worden gelogd met volledige context, inclusief kenmerken van de invoer, waarden van selectiecriteria en uitvoeringsmetadata voor reconstructie van een audit trail.            |   2    | D/V |
| 9.10.4 | Controleer of de Tree-of-Thoughts redenering takkenafsnijmechanismen bevat die de exploratie beëindigen wanneer beleidsovertredingen, bronnenlimieten of veiligheidsgrenzen worden gedetecteerd.                                                   |   2    | D/V |
| 9.10.5 | Controleer of ReAct (Reason-Act-Observe) cycli validatiepunten bevatten bij elke fase: verificatie van de redeneringsstap, actie-autorisatie en observatie-sanitatie voordat men verdergaat.                                                       |   2    | D/V |
| 9.10.6 | Verifieer dat de prestaties van de redeneringsstrategie (uitvoeringstijd, bronnenverbruik, outputkwaliteit) worden bewaakt met automatische meldingen wanneer de metingen afwijken van de ingestelde drempels.                                     |   3    | D/V |
| 9.10.7 | Verifieer dat hybride redeneringsbenaderingen die meerdere strategieën combineren de invoervalidatie en uitvoerbeperkingen van alle onderliggende strategieën handhaven zonder beveiligingscontroles te omzeilen.                                  |   3    | D/V |
| 9.10.8 | Verifieer dat veiligheidstesten van redeneringsstrategieën fuzzing met misvormde invoer omvatten, adversariële prompts ontworpen om tot een wisseling van strategie te dwingen, en het testen van randvoorwaarden voor elke cognitieve benadering. |   3    | D/V |

---

## 9.11 Agent Levenscyclus Toestandsbeheer en Beveiliging

Beveiligde agentinitialisatie, toestandsovergangen en beëindiging met cryptografische auditsporen en gedefinieerde herstelprocedures.

|   #    | Beschrijving                                                                                                                                                                                                                                                                                                                  | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.11.1 | Verifieer dat de agentinitialisatie cryptografische identiteitsvaststelling omvat met hardware-ondersteunde referenties en onveranderlijke opstartauditlogboeken die agent-ID, tijdstempel, configuratie-hash en initialisatieparameters bevatten.                                                                            |   1    | D/V |
| 9.11.2 | Verifieer dat agenttoestandsovergangen cryptografisch ondertekend, tijdstempeld en vastgelegd zijn met volledige context, inclusief triggerende gebeurtenissen, hash van de vorige toestand, hash van de nieuwe toestand en uitgevoerde beveiligingsvalidaties.                                                               |   2    | D/V |
| 9.11.3 | Controleer of de uitschakelprocedures van de agent de volgende elementen omvatten: beveiligde geheugenwis met cryptografische uitwissing of meerdere passes overschrijven; intrekking van referenties met melding aan de certificaatautoriteit; en generatie van tamper-evident beëindigingcertificaten.                      |   2    | D/V |
| 9.11.4 | Controleer dat de herstelmechanismen voor agenten de integriteit van de toestand valideren door middel van cryptografische controlesommen (minimaal SHA-256) en terugrollen naar bekende-goede toestanden wanneer corruptie wordt gedetecteerd, met geautomatiseerde waarschuwingen en vereisten voor handmatige goedkeuring. |   3    | D/V |
| 9.11.5 | Verifieer dat de agent-persistentie-mechanismen gevoelige toestandgegevens versleutelen met per-agent AES-256-sleutels en implementeer een veilige sleutelrotatie op configureerbare schema's (maximaal 90 dagen) met zero-downtime-uitrol.                                                                                   |   3    | D/V |

---

## 9.12 Toolintegratie Beveiligingskader

Beveiligingsmaatregelen voor het dynamisch laden van tools, uitvoering en validatie van resultaten met gedefinieerde risicobeoordelings- en goedkeuringsprocessen.

|   #    | Beschrijving                                                                                                                                                                                                                                                                           | Niveau | Rol |
| :----: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.12.1 | Verifieer dat toolbeschrijvingen beveiligingsmetadata bevatten die vereiste machtigingen (lezen/schrijven/uitvoeren), risiconiveaus (laag/middel/hoog), beperkingen van hulpbronnen (CPU, geheugen, netwerk) aangeven, en validatie-eisen die zijn vastgelegd in toolmanifesten.       |   1    | D/V |
| 9.12.2 | Verifieer dat de resultaten van de tooluitvoering worden gevalideerd tegen de verwachte schema's (JSON Schema, XML Schema) en beveiligingsbeleid (uitvoer sanitatie, gegevensclassificatie) voordat integratie plaatsvindt met time-outlimieten en foutafhandelingsprocedures.         |   1    | D/V |
| 9.12.3 | Verifieer dat de logs van toolinteracties een gedetailleerde beveiligingscontext bevatten, inclusief privilegegebruik, gegevenstoegangspatronen, uitvoeringstijd, resourceverbruik en terugkeercodes, met gestructureerde logging voor SIEM-integratie.                                |   2    | D/V |
| 9.12.4 | Zorg ervoor dat dynamische tool-laadmechanismen digitale handtekeningen valideren met behulp van PKI-infrastructuur en implementeer beveiligde laadprotocollen met sandbox-isolatie en machtigingsverificatie vóór uitvoering.                                                         |   2    | D/V |
| 9.12.5 | Controleer of beveiligingsbeoordelingen van tools automatisch worden geactiveerd voor nieuwe versies, met verplichte goedkeuringspunten waaronder statische analyse, dynamische tests en beoordeling door het beveiligingsteam, met gedocumenteerde goedkeuringscriteria en SLA-eisen. |   3    | D/V |

---

### Referenties

* [MITRE ATLAS tactics ML09](https://atlas.mitre.org/)
* [Circuit-breaker research for AI agents — Zou et al., 2024](https://arxiv.org/abs/2406.04313)
* [Trend Micro analysis of sandbox escapes in AI agents — Park, 2025](https://www.trendmicro.com/vinfo/us/security/news/cybercrime-and-digital-threats/unveiling-ai-agent-vulnerabilities-code-execution)
* [Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025](https://auth0.com/blog/secure-human-in-the-loop-interactions-for-ai-agents/)
* [Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025](https://medium.com/%40foraisec/security-analysis-potential-ai-agent-hijacking-via-mcp-and-a2a-protocol-insights-cd1ec5e6045f)
* [Rapid7 fundamentals on spoofing attack prevention — 2024](https://www.rapid7.com/fundamentals/spoofing-attacks/)
* [Imperial College verification of swarm systems — Lomuscio et al.](https://sail.doc.ic.ac.uk/projects/swarms/)
* [NIST AI Risk Management Framework 1.0, 2023](https://nvlpubs.nist.gov/nistpubs/ai/nist.ai.100-1.pdf)
* [WIRED security briefing on encryption best practices, 2024](https://www.wired.com/story/encryption-apps-chinese-telecom-hacking-hydra-russia-exxon)
* [OWASP Top 10 for LLM Applications, 2025](https://owasp.org/www-project-top-10-for-large-language-model-applications/)
* [Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS](https://arxiv.org/html/2506.01245v1)
* [How Is LLM Reasoning Distracted by Irrelevant Context?
  An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
* [Large Language Model Sentinel: LLM Agent for Adversarial Purification](https://arxiv.org/pdf/2405.20770)
* [Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents](https://arxiv.org/html/2504.19956v2)

