# 9 Autonome Orkestratie & Agentische Actiebeveiliging

## Beheersingsdoelstelling

Zorg ervoor dat autonome of multi-agent AI-systemen alleen acties kunnen uitvoeren die uitdrukkelijk bedoeld, geverifieerd, controleerbaar en binnen afgebakende kosten- en risicodrempels vallen. Dit beschermt tegen bedreigingen zoals compromittering van autonome systemen, misbruik van tools, detectie van agentloops, kaping van communicatie, identiteitsvervalsing, zwermmanipulatie en manipulatie van intenties.

---

## 9.1 Agent Taakplanning & Recursiebudgetten

Beperk recursieve plannen en verplicht menselijke controles voor bevoorrechte acties.

|   #   | Beschrijving                                                                                                                                                                                                   | Niveau | Rol |
| :---: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.1.1 | Controleer of de maximale recursiediepte, breedte, wall-clock tijd, tokens en monetaire kosten per agentuitvoering centraal zijn geconfigureerd en versiebeheer ondergaan.                                     |   1    | D/V |
| 9.1.2 | Verifieer dat bevoorrechte of onomkeerbare acties (bijvoorbeeld code commits, financiële overboekingen) expliciete menselijke goedkeuring vereisen via een controleerbaar kanaal voordat ze worden uitgevoerd. |   1    | D/V |
| 9.1.3 | Controleer of realtime resourcebewakers een circuitonderbreker-onderbreking activeren wanneer een budgetdrempel wordt overschreden, waardoor verdere taakuitbreiding wordt gestopt.                            |   2    |  D  |
| 9.1.4 | Verifieer dat circuit-breaker gebeurtenissen worden geregistreerd met agent-ID, triggerconditie en vastgelegde plantoestand voor forensische beoordeling.                                                      |   2    | D/V |
| 9.1.5 | Verifieer dat beveiligingstests scenario's met budget-uitputting en ontspoorde plannen dekken, en bevestig dat veilig stoppen zonder gegevensverlies plaatsvindt.                                              |   3    |  V  |
| 9.1.6 | Controleer of budgetbeleid wordt uitgedrukt als beleid-als-code en wordt afgedwongen in CI/CD om configuratie-afwijking te blokkeren.                                                                          |   3    |  D  |

---

## 9.2 Sandboxing van Tool-plugins

Isoleer toolinteracties om ongeautoriseerde systeemtoegang of code-uitvoering te voorkomen.

|   #   | Beschrijving                                                                                                                                                                                     | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 9.2.1 | Controleer of elke tool/plugin wordt uitgevoerd binnen een OS-, container- of WASM-niveau sandbox met beleid voor bestandssysteem, netwerk en systeemoproepen die het minste privilege vereisen. |   1    | D/V |
| 9.2.2 | Controleer of sandbox resourcequota's (CPU, geheugen, schijf, netwerkuitgaand verkeer) en uitvoeringstijdslimieten worden afgedwongen en gelogd.                                                 |   1    | D/V |
| 9.2.3 | Controleer of tool-binaries of descriptors digitaal zijn ondertekend; handtekeningen worden gevalideerd voordat ze worden geladen.                                                               |   2    | D/V |
| 9.2.4 | Controleer of sandbox-telemetrie naar een SIEM stroomt; afwijkingen (bijv. pogingen tot uitgaande verbindingen) veroorzaken waarschuwingen.                                                      |   2    |  V  |
| 9.2.5 | Verifieer dat risicovolle plugins een beveiligingsreview en penetratietest ondergaan voordat ze in productie worden ingezet.                                                                     |   3    |  V  |
| 9.2.6 | Controleer of pogingen tot het ontsnappen uit de sandbox automatisch worden geblokkeerd en dat de overtredende plugin in quarantaine wordt geplaatst in afwachting van onderzoek.                |   3    | D/V |

---

## 9.3 Autonome Lus & Kostenbegrenzing

Detecteer en stop ongecontroleerde agent-naar-agent recursie en kostenexplosies.

|   #   | Beschrijving                                                                                                                                        | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.3.1 | Controleer of inter-agent oproepen een hoplimiet of TTL bevatten die door de runtime wordt verminderd en afgedwongen.                               |   1    | D/V |
| 9.3.2 | Controleer of agenten een unieke oproepgrafiek-ID behouden om zelfoproepen of cyclische patronen te detecteren.                                     |   2    |  D  |
| 9.3.3 | Verifieer dat cumulatieve compute-unit en uitgaven tellers per verzoekketen worden bijgehouden; het overschrijden van de limiet breekt de keten af. |   2    | D/V |
| 9.3.4 | Controleer of formele analyse of model checking het ontbreken van onbeperkte recursie in agentprotocollen aantoont.                                 |   3    |  V  |
| 9.3.5 | Controleer of loop-afbreekgebeurtenissen waarschuwingen genereren en continue-verbeteringsstatistieken aanleveren.                                  |   3    |  D  |

---

## 9.4 Bescherming tegen misbruik op protocolniveau

Beveilig communicatiekanalen tussen agenten en externe systemen om kaping of manipulatie te voorkomen.

|   #   | Beschrijving                                                                                                                                                    | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.4.1 | Verifieer dat alle berichten van agent naar tool en van agent naar agent geverifieerd zijn (bijvoorbeeld met mutual TLS of JWT) en end-to-end versleuteld zijn. |   1    | D/V |
| 9.4.2 | Controleer of schema's strikt worden gevalideerd; onbekende velden of verkeerd gevormde berichten worden afgewezen.                                             |   1    |  D  |
| 9.4.3 | Controleer of integriteitscontroles (MAC's of digitale handtekeningen) het gehele berichtpayload inclusief toolparameters omvatten.                             |   2    | D/V |
| 9.4.4 | Controleer of replay-bescherming (nonces of tijdstempelvensters) wordt afgedwongen op het protocolniveau.                                                       |   2    |  D  |
| 9.4.5 | Verifieer dat protocollimplementaties worden onderworpen aan fuzzing en statische analyse op injectie- of deserialisatiefouten.                                 |   3    |  V  |

---

## 9.5 Agentidentiteit & Manipulatieweerbaarheid

Zorg ervoor dat acties toerekenbaar zijn en dat wijzigingen detecteerbaar zijn.

|   #   | Beschrijving                                                                                                                                | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.5.1 | Verifieer dat elke agentinstantie een unieke cryptografische identiteit bezit (sleutelpaar of hardware-verankerde referentie).              |   1    | D/V |
| 9.5.2 | Controleer of alle agentacties ondertekend en van een tijdstempel voorzien zijn; logs bevatten de handtekening voor ontkenningsbeveiliging. |   2    | D/V |
| 9.5.3 | Verifieer dat manipulatiebestendige logs worden opgeslagen in een alleen-toevoegmedium of een schrijf-eenmaal medium.                       |   2    |  V  |
| 9.5.4 | Controleer of identiteits-sleutels roteren volgens een vastgesteld schema en bij aanwijzingen voor compromittering.                         |   3    |  D  |
| 9.5.5 | Controleer of pogingen tot spoofing of sleutelconflicten onmiddellijke quarantaine van de getroffen agent veroorzaken.                      |   3    | D/V |

---

## 9.6 Multi-Agent Zwerm Risicobeperking

Beperk gevaren van collectief gedrag door isolatie en formele veiligheidsmodellering.

|   #   | Beschrijving                                                                                                                                      | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.6.1 | Controleer of agenten die in verschillende beveiligingsdomeinen opereren, worden uitgevoerd in geïsoleerde runtime sandboxes of netwerksegmenten. |   1    | D/V |
| 9.6.2 | Verifieer dat zwermgedragingen worden gemodelleerd en formeel geverifieerd op levendigheid en veiligheid voordat ze worden ingezet.               |   3    |  V  |
| 9.6.3 | Controleer of runtime monitors opkomende onveilige patronen (bijv. oscillaties, deadlocks) detecteren en corrigerende acties initiëren.           |   3    |  D  |

---

## 9.7 Gebruikers- en Toolauthenticatie / -autorisatie

Implementeer robuuste toegangscontroles voor elke door een agent geactiveerde actie.

|   #   | Beschrijving                                                                                                                                              | Niveau | Rol |
| :---: | --------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.7.1 | Controleer of agenten zich authentiseren als eersteklas hoofdpersonen bij downstream-systemen, en nooit de inloggegevens van eindgebruikers hergebruiken. |   1    | D/V |
| 9.7.2 | Controleer of fijnmazige autorisatiebeleidsregels beperken welke tools een agent mag aanroepen en welke parameters deze mag leveren.                      |   2    |  D  |
| 9.7.3 | Controleer of machtigingscontroles bij elke oproep opnieuw worden geëvalueerd (continue autorisatie), en niet alleen bij het begin van de sessie.         |   2    |  V  |
| 9.7.4 | Controleer of gedelegeerde privileges automatisch verlopen en dat opnieuw toestemming vereist is na time-out of wijziging van het bereik.                 |   3    |  D  |

---

## 9.8 Beveiliging van communicatie tussen agenten

Versleutel en bescherm alle berichten tussen agenten tegen integriteitsverlies om afluisteren en manipulatie te voorkomen.

|   #   | Beschrijving                                                                                                                                                       | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 9.8.1 | Controleer of wederzijdse authenticatie en perfect-forward-secret encryptie (bijvoorbeeld TLS 1.3) verplicht zijn voor agentkanalen.                               |   1    | D/V |
| 9.8.2 | Controleer of de berichtintegriteit en -herkomst worden geverifieerd vóór verwerking; fouten veroorzaken waarschuwingen en leiden tot het negeren van het bericht. |   1    |  D  |
| 9.8.3 | Controleer of communicatiemetagegevens (tijdstempels, volgnummer) worden vastgelegd om forensische reconstructie te ondersteunen.                                  |   2    | D/V |
| 9.8.4 | Controleer of formele verificatie of model checking bevestigt dat protocol-toestandsmachines niet in onveilige toestanden kunnen worden gebracht.                  |   3    |  V  |

---

## 9.9 Intentiecontrole & Handhaving van beperkingen

Valideer dat agentacties overeenkomen met de door de gebruiker aangegeven intentie en systeembeperkingen.

|   #   | Beschrijving                                                                                                                                                                   | Niveau | Rol |
| :---: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :----: | :-: |
| 9.9.1 | Controleer of pre-executie constraintsolvers voorgestelde acties verifiëren aan harde gecodeerde veiligheids- en beleidsregels.                                                |   1    |  D  |
| 9.9.2 | Controleer of acties met grote impact (financieel, destructief, privacygevoelig) expliciete intentiebevestiging van de initiërende gebruiker vereisen.                         |   2    | D/V |
| 9.9.3 | Controleer dat na-voorwaardecontroles bevestigen dat voltooide acties de beoogde effecten hebben bereikt zonder neveneffecten; afwijkingen veroorzaken een terugdraaiing.      |   2    |  V  |
| 9.9.4 | Verifieer dat formele methoden (bijv. model checking, theorem proving) of op eigenschappen gebaseerde tests aantonen dat agentplannen aan alle verklaarde beperkingen voldoen. |   3    |  V  |
| 9.9.5 | Verifieer dat incidenten van intentie-ongelijkheid of schending van beperkingen bijdragen aan continue verbeteringscycli en het delen van dreigingsinformatie.                 |   3    |  D  |

---

## 9.10 Beveiliging van de Redeneringsstrategie van Agenten

Veilige selectie en uitvoering van verschillende redeneerstrategieën, waaronder ReAct-, Chain-of-Thought- en Tree-of-Thoughts-benaderingen.

|   #    | Beschrijving                                                                                                                                                                                                                                         | Niveau | Rol |
| :----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.10.1 | Verifieer dat de selectie van redeneringsstrategie deterministische criteria gebruikt (invoercomplexiteit, type taak, beveiligingscontext) en dat identieke invoer identieke strategiekeuzes oplevert binnen dezelfde beveiligingscontext.           |   1    | D/V |
| 9.10.2 | Controleer of elke redeneermethode (ReAct, Chain-of-Thought, Tree-of-Thoughts) beschikt over specifieke invoervalidatie, uitvoeropschoning en uitvoeringstijdlimieten die zijn afgestemd op de betreffende cognitieve aanpak.                        |   1    | D/V |
| 9.10.3 | Verifieer dat overgangen van redeneerstrategieën worden vastgelegd met volledige context, inclusief invoerkenmerken, waarden van selectiecriteria en uitvoeringsmetadata voor reconstructie van het auditspoor.                                      |   2    | D/V |
| 9.10.4 | Controleer of Tree-of-Thoughts-redenering vertakkingsbesnoeiingsmechanismen omvat die de verkenning beëindigen wanneer beleidschendingen, resourcebeperkingen of veiligheidsgrenzen worden gedetecteerd.                                             |   2    | D/V |
| 9.10.5 | Controleer of ReAct (Reason-Act-Observe) cycli validatiecontroles bevatten in elke fase: verificatie van de redeneerstap, autorisatie van de actie en sanering van de observatie voordat wordt doorgegaan.                                           |   2    | D/V |
| 9.10.6 | Controleer of prestatiestatistieken van redeneringsstrategieën (uitvoeringstijd, resourcegebruik, outputkwaliteit) worden gemonitord met geautomatiseerde waarschuwingen wanneer de statistieken afwijken van de geconfigureerde drempels.           |   3    | D/V |
| 9.10.7 | Controleer of hybride redeneermethoden die meerdere strategieën combineren, de invoervalidatie en uitvoerbeperkingen van alle samenstellende strategieën handhaven zonder beveiligingscontroles te omzeilen.                                         |   3    | D/V |
| 9.10.8 | Controleer of de beveiligingstests van redeneringsstrategieën fuzzing met verkeerd gevormde invoer bevatten, kwaadaardige prompts die bedoeld zijn om het wisselen van strategie af te dwingen, en grenswaardetests voor elke cognitieve benadering. |   3    | D/V |

---

## 9.11 Agentlevenscyclusstatusbeheer & Beveiliging

Veilige agentinitialisatie, toestandovergangen en beëindiging met cryptografische auditsporen en gedefinieerde herstelprocedures.

|   #    | Beschrijving                                                                                                                                                                                                                                                                                          | Niveau | Rol |
| :----: | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.11.1 | Controleer of de agent-initialisatie cryptografische identiteitsvaststelling omvat met hardware-ondersteunde referenties en onveranderlijke opstartauditlogs die agent-ID, tijdstempel, configuratiehash en initialisatieparameters bevatten.                                                         |   1    | D/V |
| 9.11.2 | Controleer of agent-statusovergangen cryptografisch zijn ondertekend, voorzien van een tijdstempel en worden vastgelegd met volledige context, inclusief de activerende gebeurtenissen, de hash van de vorige status, de hash van de nieuwe status en de uitgevoerde beveiligingsvalidaties.          |   2    | D/V |
| 9.11.3 | Controleer of de agent afsluitprocedures een veilige geheugenwissing omvatten met behulp van cryptografische verwijdering of meervoudig overschrijven, intrekking van referenties met kennisgeving aan de certificaatautoriteit, en het genereren van manipulatiebestendige beëindigingscertificaten. |   2    | D/V |
| 9.11.4 | Verifieer dat agentherstelsystemen de integriteit van de status valideren met behulp van cryptografische checksums (minimaal SHA-256) en terugkeren naar bekende goede staten wanneer corruptie wordt gedetecteerd, met automatische waarschuwingen en vereisten voor handmatige goedkeuring.         |   3    | D/V |
| 9.11.5 | Controleer of agentpersistentiemechanismen gevoelige statusgegevens versleutelen met per-agent AES-256-sleutels en implementeer veilige sleutelrotatie op configureerbare schema's (maximaal 90 dagen) met zero-downtime implementatie.                                                               |   3    | D/V |

---

## 9.12 Beveiligingsframework voor toolintegratie

Beveiligingscontroles voor dynamische toolloading, uitvoering en resultaatvalidatie met gedefinieerde risicobeoordeling- en goedkeuringsprocessen.

|   #    | Beschrijving                                                                                                                                                                                                                                                                                | Niveau | Rol |
| :----: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----: | :-: |
| 9.12.1 | Controleer of toolomschrijvingen beveiligingsmetadata bevatten die de vereiste privileges specificeren (lezen/schrijven/uitvoeren), risiconiveaus (laag/middel/hoog), resourcebeperkingen (CPU, geheugen, netwerk) en validatievereisten die gedocumenteerd zijn in toolmanifests.          |   1    | D/V |
| 9.12.2 | Verifieer dat de uitvoeringsresultaten van tools worden gevalideerd aan de hand van verwachte schema's (JSON Schema, XML Schema) en beveiligingsbeleid (outputsanering, dataclassificatie) voordat ze worden geïntegreerd met time-outlimieten en procedures voor foutafhandeling.          |   1    | D/V |
| 9.12.3 | Verifieer dat toolinteractielogs een gedetailleerde beveiligingscontext bevatten, inclusief het gebruik van privileges, datatoegangs­patronen, uitvoeringstijd, resourceverbruik en retourcodes, met gestructureerde logging voor SIEM-integratie.                                          |   2    | D/V |
| 9.12.4 | Controleer of dynamische hulpmiddel-laadmechanismen digitale handtekeningen valideren met behulp van PKI-infrastructuur en implementeer veilige laadprotocollen met sandbox-isolatie en machtigingsverificatie voorafgaand aan uitvoering.                                                  |   2    | D/V |
| 9.12.5 | Verifieer dat beveiligingsbeoordelingen van tools automatisch worden geactiveerd voor nieuwe versies met verplichte goedkeuringspoorten, inclusief statische analyse, dynamische testen en beoordeling door het beveiligingsteam met gedocumenteerde goedkeuringscriteria en SLA-vereisten. |   3    | D/V |

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

