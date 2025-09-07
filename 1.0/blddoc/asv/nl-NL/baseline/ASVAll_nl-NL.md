## Voorplat

### Over de norm

De Artificial Intelligence Security Verification Standard (AISVS) is een door de gemeenschap aangedreven catalogus van beveiligingseisen die datawetenschappers, MLOps-engineers, softwarearchitecten, ontwikkelaars, testers, beveiligingsprofessionals, toolleveranciers, regelgevers en gebruikers kunnen gebruiken om betrouwbare AI-gestuurde systemen en toepassingen te ontwerpen, bouwen, testen en verifiëren. Het biedt een gemeenschappelijke taal voor het specificeren van beveiligingscontroles gedurende de volledige AI-levenscyclus—from het verzamelen van data en modelontwikkeling tot implementatie en voortdurende monitoring—zodat organisaties de veerkracht, privacy en veiligheid van hun AI-oplossingen kunnen meten en verbeteren.

### Auteursrecht en Licentie

Versie 0.1 (Eerste Openbare Concept - Werk In Uitvoering), 2025  

![license](images/license.png)
Copyright © 2025 Het AISVS-project.  

Uitgegeven onder deCreative Commons Attribution‑ShareAlike 4.0 International License.
Voor hergebruik of distributie moet u de licentievoorwaarden van dit werk duidelijk aan anderen communiceren.

### Projectleiders

Jim Manico
Aras “Russ” Memisyazici

### Bijdragers en beoordelaars

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS is een gloednieuwe standaard die specifiek is ontwikkeld om de unieke beveiligingsuitdagingen van kunstmatige-intelligentiesystemen aan te pakken. Hoewel het inspiratie haalt uit bredere beveiligingsbest practices, is elke eis in AISVS vanaf de basis ontwikkeld om het dreigingslandschap van AI weer te geven en organisaties te helpen bij het bouwen van veiligere, veerkrachtigere AI-oplossingen.

## Voorwoord

Welkom bij de Artificial Intelligence Security Verification Standard (AISVS) versie 1.0!

### Inleiding

Opgericht in 2025 door een gezamenlijke inspanning van de gemeenschap, definieert AISVS de beveiligingseisen waarmee rekening moet worden gehouden bij het ontwerpen, ontwikkelen, implementeren en exploiteren van moderne AI-modellen, pijplijnen en AI-gestuurde diensten.

AISVS v1.0 vertegenwoordigt het gezamenlijke werk van de projectleiders, de werkgroep en bredere gemeenschapsbijdragers om een pragmatische, toetsbare basislijn voor het beveiligen van AI-systemen te produceren.

Ons doel met deze release is om AISVS gemakkelijk te maken om te adopteren, terwijl we ons scherp richten op de gedefinieerde scope en het snel veranderende risico landschap dat uniek is voor AI aanpakken.

### Belangrijkste doelstellingen voor AISVS Versie 1.0

Versie 1.0 zal worden gemaakt met verschillende leidende principes.

#### Duidelijke Afbakening

Elke eis moet in overeenstemming zijn met de naam en missie van AISVS:

Kunstmatige Intelligentie – Besturingselementen werken op de AI/ML-laag (gegevens, model, pijplijn of inferentie) en vallen onder de verantwoordelijkheid van AI-beoefenaars.
Beveiliging – Vereisten mitigeren direct de geïdentificeerde beveiligings-, privacy- of veiligheidsrisico’s.
Verificatie – De taal is zo geschreven dat naleving objectief kan worden geverifieerd.
Norm – Secties volgen een consistente structuur en terminologie om een samenhangende referentie te vormen.
​
---

Door AISVS te volgen, kunnen organisaties systematisch de beveiligingspositie van hun AI-oplossingen evalueren en versterken, en zo een cultuur van veilige AI-engineering bevorderen.

## Gebruikmakend van de AISVS

De Artificial Intelligence Security Verification Standard (AISVS) definieert beveiligingseisen voor moderne AI-toepassingen en -diensten, met de nadruk op aspecten die onder de controle van applicatieontwikkelaars vallen.

De AISVS is bedoeld voor iedereen die AI-toepassingen ontwikkelt of de beveiliging ervan evalueert, waaronder ontwikkelaars, architecten, beveiligingsingenieurs en auditors. Dit hoofdstuk introduceert de structuur en het gebruik van de AISVS, inclusief de verificatieniveaus en beoogde gebruikssituaties.

### Beveiligingsverificatieniveaus voor Kunstmatige Intelligentie

De AISVS definieert drie oplopende niveaus van beveiligingsverificatie. Elk niveau voegt diepgang en complexiteit toe, waardoor organisaties hun beveiligingshouding kunnen afstemmen op het risiconiveau van hun AI-systemen.

Organisaties kunnen beginnen op Niveau 1 en geleidelijk hogere niveaus aannemen naarmate de beveiligingsrijpheid en bedreigingsexposure toenemen.

#### Definitie van de niveaus

Elke vereiste in AISVS v1.0 wordt toegewezen aan een van de volgende niveaus:

 Niveau 1-vereisten

Niveau 1 omvat de meest kritieke en fundamentele beveiligingseisen. Deze richten zich op het voorkomen van veelvoorkomende aanvallen die niet afhankelijk zijn van andere voorwaarden of kwetsbaarheden. De meeste controles op Niveau 1 zijn ofwel eenvoudig te implementeren of essentieel genoeg om de moeite waard te zijn.

 Niveau 2-vereisten

Niveau 2 behandelt meer geavanceerde of minder voorkomende aanvallen, evenals gelaagde verdedigingslagen tegen wijdverspreide bedreigingen. Deze vereisten kunnen complexere logica inhouden of zich richten op specifieke aanvalsvoorwaarden.

 Niveau 3 vereisten

Niveau 3 omvat controles die doorgaans moeilijker te implementeren zijn of situationeel toepasbaar zijn. Deze vertegenwoordigen vaak verdedigingsmechanismen in diepte of mitigaties tegen niche-, gerichte of complexiteitrijke aanvallen.

#### Rol (D/V)

Elke AISVS-vereiste is gemarkeerd volgens het primaire publiek:

D – Eisen gericht op ontwikkelaars
V – Eisen gericht op verificateurs/auditors
D/V – Relevant voor zowel ontwikkelaars als verificateurs

## C1 Traininggegevensbeheer & Beheer van vooringenomenheid

### Beheersingsdoelstelling

Trainingsgegevens moeten worden verkregen, behandeld en onderhouden op een manier die de herkomst, beveiliging, kwaliteit en eerlijkheid waarborgt. Dit vervult juridische verplichtingen en vermindert de risico's van vooringenomenheid, vergiftiging of privacyinbreuken die tijdens het trainen naar voren kunnen komen en de gehele AI-levenscyclus kunnen beïnvloeden.

---

### C1.1 Herkomst van trainingsgegevens

Houd een verifieerbare inventaris bij van alle datasets, accepteer alleen vertrouwde bronnen en registreer elke wijziging voor auditbaarheid.

 #1.1.1    Niveau: 1    Rol: D/V
 Verifieer dat een up-to-date inventaris van elke trainingsgegevensbron (oorsprong, beheerder/eigenaar, licentie, verzamelmethode, beperkingen voor bedoeld gebruik en verwerkingsgeschiedenis) wordt bijgehouden.
 #1.1.2    Niveau: 1    Rol: D/V
 Controleer of de trainingsdataprocessen onnodige kenmerken, attributen of velden uitsluiten (bijvoorbeeld ongebruikte metadata, gevoelige PII, gelekte testgegevens).
 #1.1.3    Niveau: 2    Rol: D/V
 Verifieer dat alle wijzigingen in de dataset onderhevig zijn aan een goedgekeurd en gelogd workflowproces.
 #1.1.4    Niveau: 3    Rol: D/V
 Controleer of datasets of subsets waar mogelijk zijn voorzien van een watermerk of fingerprint.

---

### C1.2 Beveiliging en integriteit van trainingsgegevens

Beperk de toegang tot trainingsgegevens, versleutel deze wanneer ze opgeslagen zijn en tijdens overdracht, en valideer de integriteit om manipulatie, diefstal of datavervuiling te voorkomen.

 #1.2.1    Niveau: 1    Rol: D/V
 Controleer of toegangscontroles de opslag van trainingsgegevens en pijplijnen beschermen.
 #1.2.2    Niveau: 2    Rol: D/V
 Controleer of alle toegang tot trainingsgegevens wordt geregistreerd, inclusief gebruiker, tijd en actie.
 #1.2.3    Niveau: 2    Rol: D/V
 Verifieer dat trainingsdatasets zowel tijdens het transport als in opslag versleuteld zijn, met gebruikmaking van cryptografische algoritmen en sleutelbeheerpraktijken volgens industriestandaarden.
 #1.2.4    Niveau: 2    Rol: D/V
 Controleer of cryptografische hashes of digitale handtekeningen worden gebruikt om de gegevensintegriteit tijdens het opslaan en overdragen van trainingsgegevens te waarborgen.
 #1.2.5    Niveau: 2    Rol: D/V
 Verifieer dat geautomatiseerde detectietechnieken worden toegepast om te beschermen tegen ongeautoriseerde wijzigingen of corruptie van trainingsgegevens.
 #1.2.6    Niveau: 2    Rol: D/V
 Controleer of verouderde trainingsgegevens veilig worden verwijderd of geanonimiseerd.
 #1.2.7    Niveau: 3    Rol: D/V
 Controleer of alle versies van de trainingsdataset uniek zijn geïdentificeerd, onveranderlijk zijn opgeslagen en controleerbaar zijn om ondersteuning te bieden voor terugdraaien en forensische analyse.

---

### C1.3 Trainingsgegevens Labelkwaliteits-, Integriteits- en Beveiliging

Bescherm labels en vereis technische beoordeling voor kritieke gegevens.

 #1.3.1    Niveau: 2    Rol: D/V
 Controleer of cryptografische hashwaarden of digitale handtekeningen worden toegepast op label-artifacten om hun integriteit en authenticiteit te waarborgen.
 #1.3.2    Niveau: 2    Rol: D/V
 Controleer of labeling-interfaces en -platforms sterke toegangscontroles afdwingen, tamper-evidente auditlogs van alle labeling-activiteiten bijhouden en bescherming bieden tegen ongeautoriseerde wijzigingen.
 #1.3.3    Niveau: 3    Rol: D/V
 Controleer of gevoelige informatie in labels wordt weggelaten, geanonimiseerd of versleuteld op het niveau van gegevensvelden, zowel in rust als tijdens overdracht.

---

### C1.4 Kwaliteit van trainingsgegevens en borging van beveiliging

Combineer geautomatiseerde validatie, handmatige steekproeven en geregistreerde correcties om de betrouwbaarheid van de dataset te waarborgen.

 #1.4.1    Niveau: 1    Rol: D
 Controleer of geautomatiseerde tests formaatfouten en null-waarden opvangen bij elke invoer of significante datatransformatie.
 #1.4.2    Niveau: 2    Rol: D/V
 Controleer of LLM-trainings- en fijnstemmingspijplijnen het detecteren van vergiftiging en de validatie van gegevensintegriteit implementeren (bijv. statistische methoden, detectie van uitschieters, embedding-analyse) om mogelijke vergiftigingsaanvallen (bijv. labelomkering, invoeging van achterdeurtje-triggers, rolwisselcommando's, invloedrijke instantie-aanvallen) of onbedoelde gegevenscorruptie in trainingsgegevens te identificeren.
 #1.4.3    Niveau: 3    Rol: D/V
 Verifieer dat passende verdedigingsmaatregelen, zoals adversarial training (met gegenereerde adversarial voorbeelden), data-augmentatie met gewijzigde invoerdata, of robuuste optimalisatietechnieken, zijn geïmplementeerd en afgestemd voor relevante modellen op basis van risicobeoordeling.
 #1.4.4    Niveau: 2    Rol: D/V
 Verifieer dat automatisch gegenereerde labels (bijvoorbeeld via LLM's of zwakke supervisie) onderworpen zijn aan betrouwbaarheidsdrempels en consistentiecontroles om gehallucineerde, misleidende of labels met lage betrouwbaarheid te detecteren.
 #1.4.5    Niveau: 3    Rol: D
 Controleer of geautomatiseerde tests labelverschuivingen detecteren bij elke ingestie of significante datatransformatie.

---

### C1.5 Gegevensafstamming en Traceerbaarheid

Volg de volledige reis van elk datapunt van bron tot modelinvoer voor controleerbaarheid en incidentrespons.

 #1.5.1    Niveau: 2    Rol: D/V
 Controleer of de herkomst van elk gegevenspunt, inclusief alle transformaties, augmentaties en samenvoegingen, is vastgelegd en kan worden gereconstrueerd.
 #1.5.2    Niveau: 2    Rol: D/V
 Controleer of stamboekrecords onveranderlijk, veilig opgeslagen en toegankelijk zijn voor audits.
 #1.5.3    Niveau: 2    Rol: D/V
 Controleer of de herkomstregistratie synthetic data dekt die is gegenereerd via privacybeschermende of generatieve technieken en zorg ervoor dat alle synthetic data duidelijk is gelabeld en te onderscheiden is van echte data gedurende de hele pijplijn.

---

### Referenties

NIST AI Risk Management Framework
EU AI Act – Article 10: Data & Data Governance
MITRE ATLAS: Adversary Tactics for AI
Survey of ML Bias Mitigation Techniques – MDPI
Data Provenance & Lineage Best Practices – Nightfall AI
Data Labeling Quality Standards – LabelYourData
Training Data Poisoning Guide – Lakera.ai
CISA Advisory: Securing Data for AI Systems
ISO/IEC 23053: AI Management Systems Framework
IBM: What is AI Governance?
Google AI Principles
GDPR & AI Training Data – DataProtectionReport
Supply-Chain Security for AI Data – AppSOC
OpenAI Privacy Center – Data Deletion Controls
Adversarial ML Dataset – Kaggle

## C2 Gebruikersinvoer Validatie

### Beheersingsdoelstelling

Robuuste validatie van gebruikersinvoer is een eerste verdedigingslinie tegen enkele van de meest schadelijke aanvallen op AI-systemen. Prompt-injectieaanvallen kunnen systeeminstructies overschrijven, gevoelige gegevens lekken of het model sturen naar gedrag dat niet is toegestaan. Tenzij er speciale filters en instructiehiërarchieën zijn, toont onderzoek aan dat "multi-shot" jailbreaks die gebruikmaken van zeer lange contextvensters effectief zullen zijn. Ook kunnen subtiele adversariale perturbatieaanvallen—zoals homoglyph swaps of leetspeak—stilletjes de beslissingen van een model wijzigen.

---

### C2.1 Verdediging tegen promptinjectie

Promptinjectie is een van de grootste risico's voor AI-systemen. Verdedigingen tegen deze tactiek maken gebruik van een combinatie van statische patroonfilters, dynamische classifiers en handhaving van instructiehiërarchie.

 #2.1.1    Niveau: 1    Rol: D/V
 Controleer of gebruikersinvoer wordt gescreend aan de hand van een continu bijgewerkte bibliotheek van bekende promptinjectiepatronen (jailbreak-trefwoorden, "negeer vorige", rollenspelketens, indirecte HTML/URL-aanvallen).
 #2.1.2    Niveau: 1    Rol: D/V
 Controleer of het systeem een instructiehiërarchie afdwingt waarbij systeem- of ontwikkelaarsberichten gebruikersinstructies overstemmen, zelfs na uitbreiding van het contextvenster.
 #2.1.3    Niveau: 2    Rol: D/V
 Verifieer dat adversariale evaluatietests (bijv. Red Team "many-shot" prompts) worden uitgevoerd vóór elke release van een model of prompt-sjabloon, met succespercentage-drempels en geautomatiseerde blokkades voor regressies.
 #2.1.4    Niveau: 2    Rol: D
 Controleer of prompts afkomstig van content van derden (webpagina's, PDF's, e-mails) worden gezuiverd in een geïsoleerde parseercontext voordat ze worden samengevoegd in de hoofdprompt.
 #2.1.5    Niveau: 3    Rol: D/V
 Verifieer dat alle updates van prompt-filterregels, versies van classificatiemodellen en wijzigingen in de blokkadelijsten versiebeheer hebben en controleerbaar zijn.

---

### C2.2 Weerstand tegen adversariële voorbeelden

Modellen voor natuurlijke taalverwerking (NLP) zijn nog steeds kwetsbaar voor subtiele verstoringen op karakter- of woordniveau die mensen vaak over het hoofd zien, maar die door modellen vaak verkeerd worden geclassificeerd.

 #2.2.1    Niveau: 1    Rol: D
 Controleer of de basisstappen voor invoernormalisatie (Unicode NFC, homoglyph mapping, het trimmen van witruimtes) worden uitgevoerd voordat de tokenisatie plaatsvindt.
 #2.2.2    Niveau: 2    Rol: D/V
 Verifieer dat statistische anomaliedetectie invoer markeert met een ongewoon hoge bewerkingsafstand tot taalkundige normen, overmatige herhaalde tokens of abnormale insluitingsafstanden.
 #2.2.3    Niveau: 2    Rol: D
 Controleer of de inferentie-pijplijn optionele, door adversariële training versterkte modelvarianten of verdedigingslagen ondersteunt (bijv. randomisatie, defensieve distillatie) voor hoog-risico eindpunten.
 #2.2.4    Niveau: 2    Rol: V
 Controleer of vermoedelijke vijandige invoer in quarantaine wordt geplaatst en wordt gelogd met volledige payloads (na redactie van PII).
 #2.2.5    Niveau: 3    Rol: D/V
 Verifieer dat robuustheidsmetrics (succespercentage van bekende aanvalspakketten) in de loop van de tijd worden gevolgd en dat regressies een releaseblokker activeren.

---

### C2.3 Schema-, Type- en Lengtevalidatie

AI-aanvallen met slecht gevormde of te grote invoer kunnen parseringsfouten veroorzaken, overlopen van prompts over velden heen en uitputting van bronnen. Strikte naleving van schema's is ook een vereiste bij het uitvoeren van deterministische toolaanroepen.

 #2.3.1    Niveau: 1    Rol: D
 Verifieer dat elke API- of functie-aanroependpoint een expliciet invoerdomeinschema definieert (JSON Schema, Protobuf of multimodaal equivalent) en dat invoer wordt gevalideerd voordat de prompt wordt samengesteld.
 #2.3.2    Niveau: 1    Rol: D/V
 Verifieer dat invoer die de maximale token- of bytelimieten overschrijdt, wordt afgewezen met een veilige foutmelding en nooit stilzwijgend wordt afgekapt.
 #2.3.3    Niveau: 2    Rol: D/V
 Controleer of typecontroles (bijv. numerieke bereiken, enumwaarden, MIME-types voor afbeeldingen/audio) aan de serverzijde worden afgedwongen en niet alleen in clientcode.
 #2.3.4    Niveau: 2    Rol: D
 Controleer of semantische validateurs (bijvoorbeeld JSON Schema) in constante tijd draaien om algoritmische DoS te voorkomen.
 #2.3.5    Niveau: 3    Rol: V
 Verifieer dat validatiefouten worden geregistreerd met geredigeerde payloadfragmenten en ondubbelzinnige foutcodes om de beveiligingstriage te ondersteunen.

---

### C2.4 Inhouds- en beleidscontrole

Ontwikkelaars moeten in staat zijn om syntactisch geldige prompts te detecteren die niet-toegestane inhoud verzoeken (zoals illegale instructies, haatspraak en auteursrechtelijk beschermde tekst) en vervolgens voorkomen dat deze zich verspreiden.

 #2.4.1    Niveau: 1    Rol: D
 Verifieer dat een contentclassificator (zero shot of fijn-afgestemd) elke invoer beoordeelt op geweld, zelfbeschadiging, haat, seksueel inhoud en illegale verzoeken, met configureerbare drempels.
 #2.4.2    Niveau: 1    Rol: D/V
 Controleer of invoer die het beleid overtreedt gestandaardiseerde weigeringen of veilige voltooiingen ontvangt, zodat deze niet worden doorgegeven aan downstream LLM-aanroepen.
 #2.4.3    Niveau: 2    Rol: D
 Controleer of het screeningsmodel of de regelset ten minste elk kwartaal wordt hertraind/geüpdatet, waarbij nieuw waargenomen jailbreak- of beleidsomzeilingspatronen worden opgenomen.
 #2.4.4    Niveau: 2    Rol: D
 Controleer of screenings voldoen aan gebruikersspecifieke beleidsregels (leeftijd, regionale wettelijke beperkingen) via op attributen gebaseerde regels die op het moment van de aanvraag worden opgelost.
 #2.4.5    Niveau: 3    Rol: V
 Controleer of screeningslogboeken classificatorvertrouwensscores en beleidscategorie-tags bevatten voor SOC-correlatie en toekomstige red-team herhaling.

---

### C2.5 Invoer Snelheidsbeperking & Misbruik Preventie

Ontwikkelaars moeten misbruik, uitputting van middelen en geautomatiseerde aanvallen op AI-systemen voorkomen door de invoersnelheid te beperken en afwijkende gebruikspatronen te detecteren.

 #2.5.1    Niveau: 1    Rol: D/V
 Controleer of per-gebruiker, per-IP en per-API-sleutel snelheidslimieten worden gehandhaafd voor alle invoerendpoints.
 #2.5.2    Niveau: 2    Rol: D/V
 Controleer of burst- en aanhoudende snelheidslimieten zijn afgestemd om DoS- en brute force-aanvallen te voorkomen.
 #2.5.3    Niveau: 2    Rol: D/V
 Verifieer dat afwijkende gebruikspatronen (bijv. snelle opeenvolgende aanvragen, input overstroming) geautomatiseerde blokkades of escalaties activeren.
 #2.5.4    Niveau: 3    Rol: V
 Controleer of misbruikpreventielogs worden bewaard en geanalyseerd op opkomende aanvalspatronen.

---

### C2.6 Multi-Modal Invoervalidatie

AI-systemen moeten robuuste validatie bevatten voor niet-tekstuele invoer (afbeeldingen, audio, bestanden) om injectie, ontwijking of misbruik van middelen te voorkomen.

 #2.6.1    Niveau: 1    Rol: D
 Controleer of alle niet-tekstuele invoer (afbeeldingen, audio, bestanden) wordt gevalideerd op type, grootte en formaat voordat ze worden verwerkt.
 #2.6.2    Niveau: 2    Rol: D/V
 Controleer of bestanden worden gescand op malware en steganografische payloads voordat ze worden geïmporteerd.
 #2.6.3    Niveau: 2    Rol: D/V
 Controleer of beeld-/audio-invoer wordt gecontroleerd op adversariële verstoringen of bekende aanvalspatronen.
 #2.6.4    Niveau: 3    Rol: V
 Controleer of multi-modale invoervalidatiefouten worden geregistreerd en waarschuwingen activeren voor onderzoek.

---

### C2.7 Invoer Herkomst & Toeschrijving

AI-systemen moeten auditing, misbruikregistratie en naleving ondersteunen door de oorsprong van alle gebruikersinvoer te monitoren en te taggen.

 #2.7.1    Niveau: 1    Rol: D/V
 Controleer of alle gebruikersinvoer bij binnenkomst zijn voorzien van metadata (gebruikers-ID, sessie, bron, tijdstempel, IP-adres).
 #2.7.2    Niveau: 2    Rol: D/V
 Verifieer dat provenance metadata behouden blijft en controleerbaar is voor alle verwerkte invoer.
 #2.7.3    Niveau: 2    Rol: D/V
 Controleer of anomalieën of niet-vertrouwde invoerbronnen worden gemarkeerd en onderworpen aan verhoogde controle of blokkering.

---

### C2.8 Real-Time Adaptieve Dreigingsdetectie

Ontwikkelaars moeten geavanceerde dreigingsdetectiesystemen voor AI gebruiken die zich aanpassen aan nieuwe aanvalspatronen en realtime bescherming bieden met gecompileerde patroonherkenning.

 #2.8.1    Niveau: 1    Rol: D/V
 Controleer of dreigingsdetectiepatronen worden gecompileerd in geoptimaliseerde regex-engines voor hoge prestaties bij realtime filtering met minimale latentie-impact.
 #2.8.2    Niveau: 1    Rol: D/V
 Controleer of dreigingsdetectiesystemen afzonderlijke patroonbibliotheken bijhouden voor verschillende dreigingscategorieën (promptinjectie, schadelijke inhoud, gevoelige gegevens, systeemcommando's).
 #2.8.3    Niveau: 2    Rol: D/V
 Controleer of adaptieve dreigingsdetectie machinaal leermodellen bevat die de dreigingsgevoeligheid bijwerken op basis van de frequentie en succesratio's van aanvallen.
 #2.8.4    Niveau: 2    Rol: D/V
 Controleer of real-time dreigingsinformatiesystemen patroonbibliotheken automatisch bijwerken met nieuwe aanvalssignaturen en IOC's (Indicators of Compromise).
 #2.8.5    Niveau: 3    Rol: D/V
 Verifieer dat fout-positieve niveaus van dreigingsdetectie continu worden gemonitord en dat patroon-specificiteit automatisch wordt aangepast om interferentie met legitieme gebruiksscenario's te minimaliseren.
 #2.8.6    Niveau: 3    Rol: D/V
 Verifieer dat contextuele dreigingsanalyse rekening houdt met de invoerbron, gebruikersgedragspatronen en sessiegeschiedenis om de detectienauwkeurigheid te verbeteren.
 #2.8.7    Niveau: 3    Rol: D/V
 Verifieer dat de prestatiestatistieken van bedreigingsdetectie (detectiesnelheid, verwerkingslatentie, resourcegebruik) in realtime worden bewaakt en geoptimaliseerd.

---

### C2.9 Multi-Modale Beveiligingsvalidatie-Pijplijn

Ontwikkelaars moeten beveiligingsvalidatie bieden voor tekst-, beeld-, audio- en andere AI-invoermodaliteiten met specifieke typen bedreigingsdetectie en resource-isolatie.

 #2.9.1    Niveau: 1    Rol: D/V
 Verifieer dat elke invoermodaliteit toegewijde beveiligingsvalidators heeft met gedocumenteerde bedreigingspatronen (tekst: promptinjectie, afbeeldingen: steganografie, audio: spectrogramaanvallen) en detectiedrempels.
 #2.9.2    Niveau: 2    Rol: D/V
 Verifieer dat multi-modale inputs worden verwerkt in geïsoleerde sandboxes met gedefinieerde resourcebeperkingen (geheugen, CPU, verwerkingstijd) die specifiek zijn voor elk modaliteitstype en gedocumenteerd zijn in het beveiligingsbeleid.
 #2.9.3    Niveau: 2    Rol: D/V
 Verifieer dat cross-modale aanvaldetectie gecoördineerde aanvallen identificeert die meerdere inputtypen omvatten (bijv. steganografische payloads in afbeeldingen gecombineerd met promptinjectie in tekst) met behulp van correlatieregels en alarmgeneratie.
 #2.9.4    Niveau: 3    Rol: D/V
 Verifieer dat multi-modale validatiefouten gedetailleerde logregistratie activeren, inclusief alle inputmodaliteiten, validatieresultaten, dreigingsscores en correlatieanalyse met gestructureerde logformaten voor SIEM-integratie.
 #2.9.5    Niveau: 3    Rol: D/V
 Controleer of modality-specifieke inhoudsclassificaties worden bijgewerkt volgens gedocumenteerde schema's (minimaal elk kwartaal) met nieuwe bedreigingspatronen, adversariële voorbeelden en prestatiebenchmarks die boven baseline-drempels worden gehouden.

---

### Referenties

LLM01:2025 Prompt Injection – OWASP Top 10 for LLM & Generative AI Security
Generative AI's Biggest Security Flaw Is Not Easy to Fix
Many-shot jailbreaking \ Anthropic
$PDF$ OpenAI GPT-4.5 System Card
Notebook for the CheckThat Lab at CLEF 2024
Mitigate jailbreaks and prompt injections – Anthropic
Chapter 3 MITRE ATT\&CK – Adversarial Model Analysis
OWASP Top 10 for LLM Applications 2025 – WorldTech IT
OWASP Machine Learning Security Top Ten
Few words about AI Security – Jussi Metso
How To Ensure LLM Output Adheres to a JSON Schema | Modelmetry
Easily enforcing valid JSON schema following – API
AI Safety + Cybersecurity R\&D Tracker – Fairly AI
Anthropic makes 'jailbreak' advance to stop AI models producing harmful results
Pattern matching filter rules - IBM
Real-time Threat Detection

## Beheer van de levenscyclus van het C3-model en wijzigingscontrole

### Beheersingsdoelstelling

AI-systemen moeten wijzigingsbeheerprocessen implementeren die voorkomen dat ongeautoriseerde of onveilige modelwijzigingen in productie terechtkomen. Deze controle waarborgt de integriteit van het model gedurende de hele levenscyclus—van ontwikkeling tot implementatie en buiten gebruikstelling—wat snelle incidentrespons mogelijk maakt en verantwoordelijkheid voor alle wijzigingen behoudt.

Kernbeveiligingsdoel: Alleen geautoriseerde, gevalideerde modellen komen in productie door het toepassen van gecontroleerde processen die integriteit, traceerbaarheid en herstelbaarheid waarborgen.

---

### C3.1 Modelautorisatie & Integriteit

Alleen geautoriseerde modellen met geverifieerde integriteit bereiken productieomgevingen.

 #3.1.1    Niveau: 1    Rol: D/V
 Verifieer dat alle modelartefacten (gewichten, configuraties, tokenizers) cryptografisch zijn ondertekend door geautoriseerde entiteiten voordat ze worden ingezet.
 #3.1.2    Niveau: 1    Rol: D/V
 Verifieer dat de integriteit van het model wordt gevalideerd bij de implementatietijd en dat fouten bij handtekeningverificatie het laden van het model voorkomen.
 #3.1.3    Niveau: 2    Rol: D/V
 Controleer of de herkomstgegevens van het model de identiteit van de bevoegde entiteit, controlesommen van de trainingsgegevens, validatietestresultaten met slaag-/faalstatus en een creatietijdstempel bevatten.
 #3.1.4    Niveau: 2    Rol: D/V
 Verifieer dat alle modelartefacten semantische versiebeheer gebruiken (MAJOR.MINOR.PATCH) met gedocumenteerde criteria waarin wordt gespecificeerd wanneer elk versieonderdeel wordt verhoogd.
 #3.1.5    Niveau: 2    Rol: V
 Verifieer dat de afhankelijkheidsregistratie een realtime inventaris bijhoudt die snelle identificatie van alle verbruikende systemen mogelijk maakt.

---

### C3.2 Modelvalidatie & Testen

Modellen moeten gedefinieerde beveiligings- en veiligheidscontroles doorstaan voordat ze worden ingezet.

 #3.2.1    Niveau: 1    Rol: D/V
 Verifieer dat modellen geautomatiseerde beveiligingstests ondergaan die inputvalidatie, outputsanering en veiligheidsbeoordelingen omvatten met vooraf afgesproken organisatorische slaag-/faalthresholds voordat ze worden ingezet.
 #3.2.2    Niveau: 1    Rol: D/V
 Controleer of validatiefouten automatisch de implementatie van het model blokkeren na expliciete goedkeuring van een vooraf aangewezen bevoegd persoon met gedocumenteerde zakelijke rechtvaardigingen.
 #3.2.3    Niveau: 2    Rol: V
 Verifieer dat testresultaten cryptografisch zijn ondertekend en onveranderbaar gekoppeld aan de specifieke modelversie-hash die wordt gevalideerd.
 #3.2.4    Niveau: 2    Rol: D/V
 Verifieer dat noodimplementaties een gedocumenteerde veiligheidsrisicoanalyse en goedkeuring vereisen van een vooraf aangewezen veiligheidsautoriteit binnen vooraf afgesproken termijnen.

---

### C3.3 Gecontroleerde implementatie en terugrol

Modelimplementaties moeten worden gecontroleerd, gemonitord en omkeerbaar zijn.

 #3.3.1    Niveau: 1    Rol: D
 Verifieer of productiedeployments geleidelijke uitrolmechanismen implementeren (canary deployments, blue-green deployments) met geautomatiseerde rollback-triggers op basis van vooraf overeengekomen foutpercentages, latentiegrenzen of beveiligingswaarschuwingscriteria.
 #3.3.2    Niveau: 1    Rol: D/V
 Verifieer dat rollback-mogelijkheden de volledige modelstatus (gewichten, configuraties, afhankelijkheden) atomair herstellen binnen vooraf gedefinieerde organisatorische tijdsvensters.
 #3.3.3    Niveau: 2    Rol: D/V
 Controleer of implementatieprocessen cryptografische handtekeningen valideren en integriteitschecksommen berekenen vóór modelactivatie, en de implementatie laten mislukken bij enige afwijking.
 #3.3.4    Niveau: 2    Rol: D/V
 Controleer of noodmodussluitingsmogelijkheden het uitschakelen van modeleindpunten binnen vooraf gedefinieerde reactietijden kunnen garanderen via geautomatiseerde stroomonderbrekers of handmatige kill switches.
 #3.3.5    Niveau: 2    Rol: V
 Controleer of rollback-artifacten (vorige modelversies, configuraties, afhankelijkheden) worden behouden volgens de organisatorische beleidsregels met onveranderlijke opslag voor incidentrespons.

---

### C3.4 Verantwoordingsplicht & Audit wijzigen

Alle wijzigingen in de levenscyclus van het model moeten traceerbaar en controleerbaar zijn.

 #3.4.1    Niveau: 1    Rol: V
 Verifieer dat alle modelwijzigingen (implementatie, configuratie, uitschakeling) onveranderlijke auditrecords genereren, inclusief een tijdstempel, een geverifieerde identiteit van de actor, een wijzigingstype, en voor/na-statussen.
 #3.4.2    Niveau: 2    Rol: D/V
 Controleer of toegang tot het auditlogboek de juiste autorisatie vereist en dat alle toegangspogingen worden geregistreerd met gebruikersidentiteit en een tijdstempel.
 #3.4.3    Niveau: 2    Rol: D/V
 Verifieer dat prompt-sjablonen en systeemberichten versiebeheer hebben in git-repositories met verplichte codebeoordeling en goedkeuring van aangewezen reviewers voordat ze worden uitgerold.
 #3.4.4    Niveau: 2    Rol: V
 Verifieer dat auditrecords voldoende details bevatten (modelhashes, configuratiesnapshots, afhankelijkheidsversies) om volledige reconstructie van de modelstatus mogelijk te maken voor elk tijdstip binnen de bewaartermijn.

---

### C3.5 Veilige ontwikkelingspraktijken

Modelontwikkelings- en trainingsprocessen moeten veilige praktijken volgen om compromittering te voorkomen.

 #3.5.1    Niveau: 1    Rol: D
 Verifieer dat modelontwikkeling, test- en productieomgevingen fysiek of logisch gescheiden zijn. Ze hebben geen gedeelde infrastructuur, aparte toegangscontroles en geïsoleerde gegevensopslag.
 #3.5.2    Niveau: 1    Rol: D
 Controleer of modeltraining en fine-tuning plaatsvinden in geïsoleerde omgevingen met gecontroleerde netwerktoegang.
 #3.5.3    Niveau: 1    Rol: D/V
 Verifieer dat trainingsgegevensbronnen worden gevalideerd via integriteitscontroles en geauthenticeerd via vertrouwde bronnen met een gedocumenteerde keten van bewaring voordat ze worden gebruikt in modelontwikkeling.
 #3.5.4    Niveau: 2    Rol: D
 Verifieer dat artefacten voor modelontwikkeling (hyperparameters, trainingsscripts, configuratiebestanden) worden opgeslagen in versiebeheer en goedkeuring door collega’s vereisen voordat ze worden gebruikt voor training.

---

### C3.6 Model Uitfasering & Buiten Gebruik Stelling

Modellen moeten veilig worden uitgefaseerd wanneer ze niet langer nodig zijn of wanneer beveiligingsproblemen worden vastgesteld.

 #3.6.1    Niveau: 1    Rol: D
 Controleer of modeluitfasering processen automatisch afhankelijkheidsgrafieken scannen, alle afnemende systemen identificeren en vooraf afgesproken kennisgevingsperiodes bieden vóór het buiten gebruik stellen.
 #3.6.2    Niveau: 1    Rol: D/V
 Controleer of afgevoerde modelartefacten veilig worden gewist met behulp van cryptografische wissen of meervoudig overschrijven volgens gedocumenteerde gegevensbewaarbeleid met geverifieerde vernietigingscertificaten.
 #3.6.3    Niveau: 2    Rol: V
 Controleer of modeluitdiensttreding gebeurtenissen worden geregistreerd met tijdstempel en identiteit van de actor, en dat modelhandtekeningen worden ingetrokken om hergebruik te voorkomen.
 #3.6.4    Niveau: 2    Rol: D/V
 Verifieer dat noodmodelpensioen toegang tot het model kan uitschakelen binnen vooraf vastgestelde responsperioden voor noodgevallen via geautomatiseerde killschakelaars als kritieke beveiligingslekken worden ontdekt.

---

### Referenties

MLOps Principles
Securing AI/ML Ops – Cisco.com
Audit logs security: cryptographically signed tamper-proof logs
Machine Learning Model Versioning: Top Tools & Best Practices
AI Hygiene Starts with Models and Data Loaders – SEI Blog
How to handle versioning and rollback of a deployed ML model?
Reinforcement fine-tuning – OpenAI API
Auditing Machine Learning models: Governance, Data Security and …
Adversarial Training to Improve Model Robustness
What is AI adversarial robustness? – IBM Research
Exploring Data Provenance: Ensuring Data Integrity and Authenticity
MITRE ATLAS
AWS Prescriptive Guidance – Best practices for retiring applications …

## C4-infrastructuur, configuratie- en implementatiebeveiliging

### Beheersingsdoelstelling

AI-infrastructuur moet worden versterkt tegen privilege-escalatie, supply chain-manipulatie en laterale beweging door middel van veilige configuratie, runtime-isolatie, vertrouwde distributiepijplijnen en uitgebreide monitoring. Alleen geautoriseerde, gevalideerde infrastructuurcomponenten en configuraties bereiken de productie via gecontroleerde processen die beveiliging, integriteit en controleerbaarheid waarborgen.

Kernbeveiligingsdoel: Alleen cryptografisch ondertekende, kwetsbaarheid-gescande infrastructuurcomponenten bereiken de productie via geautomatiseerde validatiepijplijnen die beveiligingsbeleid afdwingen en onveranderlijke auditsporen behouden.

---

### C4.1 Isolatie van de runtime-omgeving

Voorkom container-ontsnappingen en privilege-escalatie door middel van kernel-level isolatieprimitieven en verplichte toegangscontrolemechanismen.

 #4.1.1    Niveau: 1    Rol: D/V
 Controleer of alle AI-containers ALLE Linux-machtigingen verwijderen behalve CAP_SETUID, CAP_SETGID, en expliciet vereiste machtigingen die zijn gedocumenteerd in beveiligingsstandaarden.
 #4.1.2    Niveau: 1    Rol: D/V
 Controleer of seccomp-profielen alle systeemoproepen blokkeren behalve die in vooraf goedgekeurde toestalijsten, waarbij overtredingen leiden tot het beëindigen van de container en het genereren van beveiligingswaarschuwingen.
 #4.1.3    Niveau: 2    Rol: D/V
 Controleer of AI-workloads worden uitgevoerd met root-bestandssystemen in alleen-lezen modus, tmpfs voor tijdelijke gegevens, en benoemde volumes voor persistente gegevens waarbij noexec mount-opties worden afgedwongen.
 #4.1.4    Niveau: 2    Rol: D/V
 Controleer of op eBPF gebaseerde runtime monitoring (Falco, Tetragon of gelijkwaardig) pogingen tot privilege-escalatie detecteert en automatisch overtredende processen beëindigt binnen de reactietijdvereisten van de organisatie.
 #4.1.5    Niveau: 3    Rol: D/V
 Verifieer dat AI-werklasten met hoog risico worden uitgevoerd in hardware-geïsoleerde omgevingen (Intel TXT, AMD SVM, of speciale bare-metal nodes) met attestatieverificatie.

---

### C4.2 Veilige Build- en Deployment-pijplijnen

Zorg voor cryptografische integriteit en beveiliging van de toeleveringsketen door middel van reproduceerbare builds en ondertekende artefacten.

 #4.2.1    Niveau: 1    Rol: D/V
 Controleer of infrastructuur-als-code wordt gescand met tools (tfsec, Checkov of Terrascan) bij elke commit, waarbij merges worden geblokkeerd bij CRITIEKE of HOGE ernst bevindingen.
 #4.2.2    Niveau: 1    Rol: D/V
 Verifieer dat container builds reproduceerbaar zijn met identieke SHA256-hashes over verschillende builds en genereer SLSA Level 3 provenance-attesten ondertekend met Sigstore.
 #4.2.3    Niveau: 2    Rol: D/V
 Controleer dat containerafbeeldingen CycloneDX- of SPDX-SBOM's insluiten en met Cosign zijn ondertekend voordat ze naar het register worden gepusht, waarbij niet-ondertekende afbeeldingen bij implementatie worden afgewezen.
 #4.2.4    Niveau: 2    Rol: D/V
 Verifieer dat CI/CD-pijplijnen OIDC-tokens gebruiken van HashiCorp Vault, AWS IAM-rollen of Azure Managed Identity met levensduren die de limieten van het organisatorische beveiligingsbeleid niet overschrijden.
 #4.2.5    Niveau: 2    Rol: D/V
 Verifieer dat Cosign-handtekeningen en SLSA-herkomst worden gevalideerd tijdens het implementatieproces vóór de uitvoering van de container en dat verificatiefouten ervoor zorgen dat de implementatie mislukt.
 #4.2.6    Niveau: 2    Rol: D/V
 Controleer of bouwomgevingen draaien in vluchtige containers of VM's zonder persistent opslag en met netwerkisolatie van productie-VPC's.

---

### C4.3 Netwerkbeveiliging & Toegangscontrole

Implementeer zero-trust netwerken met standaard-weigerbeleid en versleutelde communicatie.

 #4.3.1    Niveau: 1    Rol: D/V
 Controleer of Kubernetes NetworkPolicies of een equivalent standaard-deny ingress/egress toepassen met expliciete toestemmingsregels voor vereiste poorten (443, 8080, enz.).
 #4.3.2    Niveau: 1    Rol: D/V
 Controleer of SSH (poort 22), RDP (poort 3389) en cloud metadata-eindpunten (169.254.169.254) zijn geblokkeerd of certificaatgebaseerde authenticatie vereisen.
 #4.3.3    Niveau: 2    Rol: D/V
 Controleer of uitgaand verkeer wordt gefilterd via HTTP/HTTPS-proxy's (Squid, Istio of cloud NAT-gateways) met domeintoegangsverklaringen en dat geblokkeerde verzoeken worden gelogd.
 #4.3.4    Niveau: 2    Rol: D/V
 Verifieer dat inter-service communicatie gebruikmaakt van mutual TLS met certificaten die worden gewisseld volgens het organisatiebeleid en dat certificaatvalidatie wordt afgedwongen (geen skip-verify vlaggen).
 #4.3.5    Niveau: 2    Rol: D/V
 Verifieer dat de AI-infrastructuur draait in toegewijde VPC's/VNets zonder directe internettoegang en alleen communiceert via NAT-gateways of bastion-hosts.

---

### C4.4 Geheimen- en cryptografisch sleutelbeheer

Bescherm referenties via hardware-ondersteunde opslag en geautomatiseerde rotatie met zero-trust toegang.

 #4.4.1    Niveau: 1    Rol: D/V
 Controleer of geheimen worden opgeslagen in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault of Google Secret Manager met versleuteling in rust met behulp van AES-256.
 #4.4.2    Niveau: 1    Rol: D/V
 Verifieer dat cryptografische sleutels worden gegenereerd in FIPS 140-2 Level 2 HSM's (AWS CloudHSM, Azure Dedicated HSM) met sleutelrotatie volgens het cryptografisch beleid van de organisatie.
 #4.4.3    Niveau: 2    Rol: D/V
 Verifieer dat het roteren van geheimen is geautomatiseerd met zero-downtime implementatie en onmiddellijke rotatie die wordt geactiveerd door personeelswijzigingen of beveiligingsincidenten.
 #4.4.4    Niveau: 2    Rol: D/V
 Verifieer dat containerafbeeldingen worden gescand met tools (GitLeaks, TruffleHog of detect-secrets) die builds blokkeren die API-sleutels, wachtwoorden of certificaten bevatten.
 #4.4.5    Niveau: 2    Rol: D/V
 Controleer of toegang tot productiesystemen met een geheim wachtwoord multifactor-authenticatie (MFA) vereist met hardwaretokens (YubiKey, FIDO2) en dat deze wordt vastgelegd in onveranderlijke auditlogboeken met gebruikersidentiteiten en tijdstempels.
 #4.4.6    Niveau: 2    Rol: D/V
 Controleer of geheimen worden geïnjecteerd via Kubernetes-secrets, gemonteerde volumes of init-containers en zorg ervoor dat geheimen nooit worden ingebed in omgevingsvariabelen of images.

---

### C4.5 AI-werkbelasting sandboxing en validatie

Isoleren van onbetrouwbare AI-modellen in beveiligde sandboxes met uitgebreide gedragsanalyse.

 #4.5.1    Niveau: 1    Rol: D/V
 Controleer of externe AI-modellen worden uitgevoerd in gVisor, microVM's (zoals Firecracker, CrossVM) of Docker-containers met de opties --security-opt=no-new-privileges en --read-only.
 #4.5.2    Niveau: 1    Rol: D/V
 Controleer of sandbox-omgevingen geen netwerkconnectiviteit hebben (--network=none) of alleen localhost-toegang met alle externe verzoeken geblokkeerd door iptables-regels.
 #4.5.3    Niveau: 2    Rol: D/V
 Controleer of de validatie van het AI-model automatische red-team tests omvat met organisatorisch gedefinieerde testdekking en gedragsanalyse voor het detecteren van achterdeurtjes.
 #4.5.4    Niveau: 2    Rol: D/V
 Controleer of voordat een AI-model in productie wordt genomen, de sandbox-resultaten cryptografisch worden ondertekend door geautoriseerd beveiligingspersoneel en worden opgeslagen in onveranderlijke auditlogs.
 #4.5.5    Niveau: 2    Rol: D/V
 Verifieer dat sandbox-omgevingen worden vernietigd en opnieuw worden gemaakt vanuit gouden images tussen evaluaties, met volledige opschoning van het bestandssysteem en geheugen.

---

### C4.6 Infrastructuurbeveiligingsbewaking

Voortdurend de infrastructuur scannen en monitoren met geautomatiseerde herstelacties en realtime waarschuwingen.

 #4.6.1    Niveau: 1    Rol: D/V
 Verifieer dat containerafbeeldingen worden gescand volgens de organisatorische schema's, waarbij CRITIEKE kwetsbaarheden de implementatie blokkeren op basis van organisatorische risicodrempels.
 #4.6.2    Niveau: 1    Rol: D/V
 Verifieer dat de infrastructuur voldoet aan CIS Benchmarks of NIST 800-53-controles met door de organisatie gedefinieerde compliance drempels en automatische herstelmaatregelen voor mislukte controles.
 #4.6.3    Niveau: 2    Rol: D/V
 Verifieer dat kwetsbaarheden met een HOGE ernstgraad worden gepatcht volgens de tijdlijnen van het risicobeheer van de organisatie, met noodprocedures voor actief misbruikte CVE's.
 #4.6.4    Niveau: 2    Rol: V
 Verifieer dat beveiligingswaarschuwingen integreren met SIEM-platforms (Splunk, Elastic of Sentinel) met behulp van CEF- of STIX/TAXII-formaten met geautomatiseerde verrijking.
 #4.6.5    Niveau: 3    Rol: V
 Verifieer dat infrastructuurmetriekgegevens worden geëxporteerd naar monitoringsystemen (Prometheus, DataDog) met SLA-dashboards en managementrapportage.
 #4.6.6    Niveau: 2    Rol: D/V
 Controleer of configuratieafwijkingen worden gedetecteerd met behulp van tools (Chef InSpec, AWS Config) volgens de monitoringvereisten van de organisatie, met automatische terugrol bij ongeoorloofde wijzigingen.

---

### C4.7 AI-infrastructuur Resourcebeheer

Voorkom uitputting van middelen aanvallen en zorg voor een eerlijke toewijzing van middelen door middel van quota en monitoring.

 #4.7.1    Niveau: 1    Rol: D/V
 Controleer of het gebruik van GPU/TPU wordt gemonitord met waarschuwingen die worden geactiveerd bij organisatiedefinieerde drempels en dat automatische schaalvergroting of load balancing wordt geactiveerd op basis van capaciteitsbeheerbeleid.
 #4.7.2    Niveau: 1    Rol: D/V
 Verifieer dat AI-werkbelastingmetingen (inferentie-latentie, doorvoersnelheid, foutpercentages) worden verzameld volgens de monitoringsvereisten van de organisatie en gecorreleerd zijn met het gebruik van de infrastructuur.
 #4.7.3    Niveau: 2    Rol: D/V
 Controleer of Kubernetes ResourceQuotas of gelijkwaardige mechanismen individuele workloads beperken volgens de resource-allocatiebeleid van de organisatie, met harde limieten die worden afgedwongen.
 #4.7.4    Niveau: 2    Rol: V
 Verifieer dat kostenbewaking de uitgaven per werklast/huurder volgt met waarschuwingen op basis van organisatorische budgetdrempels en geautomatiseerde controles voor budgetoverschrijdingen.
 #4.7.5    Niveau: 3    Rol: V
 Controleer of capaciteitsplanning gebruikmaakt van historische gegevens met door de organisatie gedefinieerde voorspellingsperioden en geautomatiseerde resourcevoorziening op basis van vraagpatronen.
 #4.7.6    Niveau: 2    Rol: D/V
 Controleer of uitputting van middelen circuit breakers activeert volgens de organisatieresponsvereisten, inclusief snelheidsbeperking op basis van capaciteitsbeleid en werkbelastingisolatie.

---

### C4.8 Scheiding van omgevingen en promotiecontroles

Handhaaf strikte omgevingsgrenzen met geautomatiseerde promotiepoorten en beveiligingsvalidatie.

 #4.8.1    Niveau: 1    Rol: D/V
 Controleer of dev/test/prod-omgevingen draaien in gescheiden VPC's/VNets zonder gedeelde IAM-rollen, beveiligingsgroepen of netwerkconnectiviteit.
 #4.8.2    Niveau: 1    Rol: D/V
 Verifieer dat omgevingspromotie goedkeuring vereist van organisatorisch gedefinieerd bevoegd personeel met cryptografische handtekeningen en onveranderlijke audittrail.
 #4.8.3    Niveau: 2    Rol: D/V
 Verifieer dat productieomgevingen SSH-toegang blokkeren, debug-eindpunten uitschakelen en veranderingsverzoeken vereisen met organisatorische voorafgaande kennisgevingsvereisten, behalve in noodgevallen.
 #4.8.4    Niveau: 2    Rol: D/V
 Verifieer dat wijzigingen in infrastructure-as-code peer review vereisen met geautomatiseerde tests en beveiligingsscans voordat ze worden samengevoegd met de main branch.
 #4.8.5    Niveau: 2    Rol: D/V
 Controleer of niet-productiegegevens geanonimiseerd zijn volgens de privacyvereisten van de organisatie, of dat synthetische gegevens gegenereerd zijn, of dat volledige gegevensmaskering met verwijdering van PII is geverifieerd.
 #4.8.6    Niveau: 2    Rol: D/V
 Controleer of promotiepoorten geautomatiseerde beveiligingstests bevatten (SAST, DAST, container scanning) waarbij geen CRITICAL bevindingen zijn toegestaan voor goedkeuring.

---

### C4.9 Infrastructuur Back-up & Herstel

Zorg voor veerkracht van de infrastructuur door middel van geautomatiseerde back-ups, geteste herstelprocedures en mogelijkheden voor rampenherstel.

 #4.9.1    Niveau: 1    Rol: D/V
 Verifieer dat infrastructuurconfiguraties worden geback-upt volgens de back-upschema's van de organisatie naar geografisch gescheiden regio's met implementatie van de 3-2-1 back-upstrategie.
 #4.9.2    Niveau: 2    Rol: D/V
 Verifieer dat back-upsystemen draaien in geïsoleerde netwerken met aparte referenties en air-gapped opslag voor bescherming tegen ransomware.
 #4.9.3    Niveau: 2    Rol: V
 Verifieer dat herstelprocedures worden getest en gevalideerd via geautomatiseerde tests volgens de organisatieschema's, waarbij de RTO- en RPO-doelstellingen voldoen aan de organisatorische vereisten.
 #4.9.4    Niveau: 3    Rol: V
 Verifieer dat disaster recovery AI-specifieke runbooks omvat met modelgewichtherstel, GPU-cluster herbouwing en mapping van servicedependencies.

---

### C4.10 Infrastructuurcompliance & Governance

Handhaaf regelgevende naleving door voortdurende beoordeling, documentatie en geautomatiseerde controles.

 #4.10.1    Niveau: 2    Rol: D/V
 Verifieer dat de naleving van de infrastructuur wordt beoordeeld volgens de organisatorische schema's aan de hand van SOC 2, ISO 27001, of FedRAMP-controles met geautomatiseerde bewijsverzameling.
 #4.10.2    Niveau: 2    Rol: V
 Verifieer dat de infrastructuurdocumentatie netwerkdiagrammen, gegevensstroomkaarten en dreigingsmodellen bevat die zijn bijgewerkt volgens de vereisten van het wijzigingsbeheer binnen de organisatie.
 #4.10.3    Niveau: 3    Rol: D/V
 Verifieer dat infrastructuurwijzigingen een geautomatiseerde nalevings-impactbeoordeling ondergaan met goedkeuringsworkflows voor regelgeving bij hoogrisicowaarderingen.

---

### C4.11 AI Hardware-beveiliging

Beveilig AI-specifieke hardwarecomponenten zoals GPU's, TPU's en gespecialiseerde AI-versnellers.

 #4.11.1    Niveau: 2    Rol: D/V
 Verifieer dat firmware van AI-versnellers (GPU BIOS, TPU-firmware) wordt geverifieerd met cryptografische handtekeningen en bijgewerkt volgens de patchmanagementtijden van de organisatie.
 #4.11.2    Niveau: 2    Rol: D/V
 Verifieer dat vóór de uitvoering van de werklast de integriteit van de AI-versneller wordt gevalideerd door middel van hardware-attestatie met TPM 2.0, Intel TXT of AMD SVM.
 #4.11.3    Niveau: 2    Rol: D/V
 Controleer of het GPU-geheugen geïsoleerd is tussen workloads met behulp van SR-IOV, MIG (Multi-Instance GPU), of gelijkwaardige hardwarepartitionering met geheugensanering tussen taken.
 #4.11.4    Niveau: 3    Rol: V
 Verifieer dat de AI-hardwareleveringsketen herkomstverificatie bevat met fabrikantcertificaten en controle van verzegelde verpakking die tekenen van knoeien aantoont.
 #4.11.5    Niveau: 3    Rol: D/V
 Controleer of hardwarebeveiligingsmodules (HSM's) AI-modelgewichten en cryptografische sleutels beschermen met FIPS 140-2 Level 3- of Common Criteria EAL4+-certificering.

---

### C4.12 Edge- en gedistribueerde AI-infrastructuur

Veilige gedistribueerde AI-implementaties, inclusief edge computing, gefedereerd leren en multi-site architecturen.

 #4.12.1    Niveau: 2    Rol: D/V
 Controleer of edge AI-apparaten zich authenticeren bij de centrale infrastructuur met behulp van mutual TLS en dat apparaatcertificaten worden geroteerd volgens het organisatorische certificaatbeheerbeleid.
 #4.12.2    Niveau: 2    Rol: D/V
 Controleer of randapparaten beveiligde opstart uitvoeren met geverifieerde handtekeningen en rollback-bescherming die firmware-downgradeaanvallen voorkomt.
 #4.12.3    Niveau: 3    Rol: D/V
 Verifieer dat gedistribueerde AI-coördinatie gebruikmaakt van consensusalgoritmen die bestand zijn tegen Byzantijnse fouten, met deelnemervalidering en detectie van kwaadaardige knooppunten.
 #4.12.4    Niveau: 3    Rol: D/V
 Bevestig dat communicatie van edge naar cloud bandbreedtebeperking, gegevenscompressie en offline operationele mogelijkheden met beveiligde lokale opslag omvat.

---

### C4.13 Beveiliging van Multi-Cloud en Hybride Infrastructuur

Beveilig AI-werklasten over meerdere cloudproviders en hybride cloud-on-premises implementaties.

 #4.13.1    Niveau: 2    Rol: D/V
 Controleer of multi-cloud AI-implementaties cloud-agnostische identiteitsfederatie (OIDC, SAML) gebruiken met gecentraliseerd beleidsbeheer over verschillende aanbieders.
 #4.13.2    Niveau: 2    Rol: D/V
 Controleer of cross-cloud datatransmissie end-to-end encryptie gebruikt met door de klant beheerde sleutels en datalocatiecontroles worden toegepast volgens de jurisdictie.
 #4.13.3    Niveau: 2    Rol: D/V
 Verifieer of hybride cloud AI-workloads consistente beveiligingsbeleid implementeren over on-premise en cloudomgevingen met uniforme monitoring en waarschuwingen.
 #4.13.4    Niveau: 3    Rol: V
 Verifieer dat het voorkomen van vendor lock-in bij cloudproviders draagbare infrastructure-as-code, gestandaardiseerde API's en data-exportmogelijkheden met formatconversietools omvat.
 #4.13.5    Niveau: 3    Rol: V
 Verifieer of multi-cloud kostenoptimalisatie beveiligingscontroles omvat die het voorkomen van resourceverspreiding en ongeautoriseerde kosten voor data-overdracht tussen clouds waarborgen.

---

### C4.14 Infrastructuurautomatisering & GitOps-beveiliging

Beveilig infrastructuurautomatiseringspijplijnen en GitOps-workflows voor het beheer van AI-infrastructuur.

 #4.14.1    Niveau: 2    Rol: D/V
 Controleer of GitOps-repositories ondertekende commits vereisen met GPG-sleutels en branch-beschermingsregels hebben die directe pushen naar hoofdbranches voorkomen.
 #4.14.2    Niveau: 2    Rol: D/V
 Verifieer dat infrastructuurautomatisering driftdetectie omvat met automatische herstel- en terugrolmogelijkheden die worden geactiveerd volgens de organisatorische responsvereisten voor ongeoorloofde wijzigingen.
 #4.14.3    Niveau: 2    Rol: D/V
 Controleer of geautomatiseerde infrastructuurvoorziening beveiligingsbeleidvalidatie omvat met implementatieblokkering voor niet-conforme configuraties.
 #4.14.4    Niveau: 2    Rol: D/V
 Verifieer dat geheimen voor infrastructuurautomatisering worden beheerd via externe geheimenoperators (External Secrets Operator, Bank-Vaults) met automatische rotatie.
 #4.14.5    Niveau: 3    Rol: V
 Verifieer dat zelfherstellende infrastructuur beveiligingsgebeurtenissen correleert met geautomatiseerde incidentrespons en workflows voor het informeren van belanghebbenden.

---

### C4.15 Kwantumbestendige Infrastructuurbeveiliging

Bereid AI-infrastructuur voor op bedreigingen van kwantumcomputing door middel van post-kwantumcryptografie en kwantumveilige protocollen.

 #4.15.1    Niveau: 3    Rol: D/V
 Controleer of AI-infrastructuur NIST-goedgekeurde post-quantum cryptografische algoritmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) implementeert voor sleuteluitwisseling en digitale handtekeningen.
 #4.15.2    Niveau: 3    Rol: D/V
 Verifieer dat quantum key distribution (QKD) systemen worden geïmplementeerd voor beveiligde AI-communicatie met quantum-veilige sleutelbeheerprotocollen.
 #4.15.3    Niveau: 3    Rol: D/V
 Verifieer dat cryptografische wendbaarheidskaders snelle migratie naar nieuwe post-quantum algoritmen mogelijk maken met geautomatiseerde certificaat- en sleuteldraaien.
 #4.15.4    Niveau: 3    Rol: V
 Controleer of kwantumdreigingsmodellering de kwetsbaarheid van AI-infrastructuur voor kwantumaanvallen beoordeelt met gedocumenteerde migratietijdlijnen en risicobeoordelingen.
 #4.15.5    Niveau: 3    Rol: D/V
 Verifieer dat hybride klassieke-kwantum cryptografische systemen verdedigingsdiepte bieden tijdens de kwantumovergangsperiode met prestatiemonitoring.

---

### C4.16 Vertrouwelijk Berekenen & Veilige Enclaves

Bescherm AI-werklasten en modelgewichten met op hardware gebaseerde vertrouwde uitvoeringsomgevingen en vertrouwelijke computing-technologieën.

 #4.16.1    Niveau: 3    Rol: D/V
 Verifieer dat gevoelige AI-modellen worden uitgevoerd binnen Intel SGX-enclaves, AMD SEV-SNP of ARM TrustZone met versleuteld geheugen en attestatie-verificatie.
 #4.16.2    Niveau: 3    Rol: D/V
 Verifieer dat vertrouwelijke containers (Kata Containers, gVisor met vertrouwelijke computing) AI-werkbelastingen isoleren met hardware-gedwongen geheugenversleuteling.
 #4.16.3    Niveau: 3    Rol: D/V
 Verifieer dat remote attestation de integriteit van de enclave valideert voordat AI-modellen worden geladen, met cryptografisch bewijs van de authenticiteit van een uitvoeringsomgeving.
 #4.16.4    Niveau: 3    Rol: D/V
 Verifieer dat vertrouwelijke AI-inferentiediensten modelextractie voorkomen door middel van versleutelde berekeningen met verzegelde modelgewichten en beschermde uitvoering.
 #4.16.5    Niveau: 3    Rol: D/V
 Verifieer dat de orkestratie van de vertrouwde uitvoeringsomgeving de levenscyclus van de beveiligde enclave beheert met remote attestation en versleutelde communicatiekanalen.
 #4.16.6    Niveau: 3    Rol: D/V
 Controleer of veilige multi-party computation (SMPC) gezamenlijke AI-training mogelijk maakt zonder individuele datasets of modelparameters bloot te stellen.

---

### C4.17 Zero-Knowledge Infrastructuur

Implementeer zero-knowledge proof-systemen voor privacybewakende AI-verificatie en authenticatie zonder gevoelige informatie prijs te geven.

 #4.17.1    Niveau: 3    Rol: D/V
 Verifieer dat zero-knowledge proofs (ZK-SNARKs, ZK-STARKs) de integriteit van het AI-model en de herkomst van de training verifiëren zonder modelgewichten of trainingsgegevens bloot te stellen.
 #4.17.2    Niveau: 3    Rol: D/V
 Verifieer dat op ZK gebaseerde authenticatiesystemen privacy-behoudende gebruikersverificatie voor AI-diensten mogelijk maken zonder identiteit-gerelateerde informatie prijs te geven.
 #4.17.3    Niveau: 3    Rol: D/V
 Verifieer dat private set intersection (PSI)-protocollen veilige gegevensmatching mogelijk maken voor federatieve AI zonder individuele datasets bloot te stellen.
 #4.17.4    Niveau: 3    Rol: D/V
 Verifieer dat zero-knowledge machine learning (ZKML) systemen verifieerbare AI-afleidingen mogelijk maken met cryptografisch bewijs van correcte berekening.
 #4.17.5    Niveau: 3    Rol: D/V
 Controleer of ZK-rollups schaalbare, privacybeschermende AI-transactie verwerking bieden met batchverificatie en verminderde rekenkundige belasting.

---

### C4.18 Preventie van side-channel-aanvallen

Bescherm AI-infrastructuur tegen timing-, stroom-, elektromagnetische- en cache-gebaseerde side-channel aanvallen die gevoelige informatie kunnen lekken.

 #4.18.1    Niveau: 3    Rol: D/V
 Verifieer dat de AI-inferentietijd wordt genormaliseerd met behulp van constant-time algoritmen en opvulling om timing-gebaseerde modelextractieaanvallen te voorkomen.
 #4.18.2    Niveau: 3    Rol: D/V
 Verifieer dat bescherming tegen vermogenanalyse ruisinjectie, netspanningsfiltering en gerandomiseerde uitvoeringspatronen voor AI-hardware omvat.
 #4.18.3    Niveau: 3    Rol: D/V
 Controleer of mitigatie van cache-gebaseerde zijkanaalaanvallen gebruikmaakt van cache-partitionering, randomisatie en flush-instructies om informatielekken te voorkomen.
 #4.18.4    Niveau: 3    Rol: D/V
 Verifieer dat bescherming tegen elektromagnetische emissies afscherming, signaalfiltering en gerandomiseerde verwerking omvat om TEMPEST-achtige aanvallen te voorkomen.
 #4.18.5    Niveau: 3    Rol: D/V
 Controleer of micro-architecturale zijkanaalverdedigingen speculatieve uitvoeringscontroles en het verhullen van geheugen toegangs patronen omvatten.

---

### C4.19 Neuromorfe & Gespecialiseerde AI Hardware Beveiliging

Beveilig opkomende AI-hardwarearchitecturen, waaronder neuromorfe chips, FPGA's, aangepaste ASIC's en optische computersystemen.

 #4.19.1    Niveau: 3    Rol: D/V
 Controleer of de beveiliging van de neuromorfe chip patroonversleuteling van spikes, bescherming van synaptische gewichten en hardwaregebaseerde validatie van leerregels omvat.
 #4.19.2    Niveau: 3    Rol: D/V
 Verifieer dat FPGA-gebaseerde AI-versnellers bitstream-encryptie, anti-tampermechanismen en veilige configuratielading met geverifieerde updates implementeren.
 #4.19.3    Niveau: 3    Rol: D/V
 Verifieer dat aangepaste ASIC-beveiliging on-chip beveiligingsprocessors, een hardware root of trust en veilige sleutelopslag met detectie van manipulatie omvat.
 #4.19.4    Niveau: 3    Rol: D/V
 Verifieer of optische computersystemen kwantumveilige optische encryptie, veilige fotonische schakeling en beschermde optische signaalverwerking implementeren.
 #4.19.5    Niveau: 3    Rol: D/V
 Controleer of hybride analoog-digitale AI-chips beveiligde analoge berekeningen, beschermde gewichtsopslag en geauthenticeerde analoog-naar-digitaal conversie bevatten.

---

### C4.20 Privacy-behoudende Compute-infrastructuur

Implementeer infrastructuurcontroles voor privacybewarende berekeningen om gevoelige gegevens te beschermen tijdens AI-verwerking en -analyse.

 #4.20.1    Niveau: 3    Rol: D/V
 Verifieer dat de infrastructuur voor homomorfe encryptie versleutelde berekeningen op gevoelige AI-werkbelastingen mogelijk maakt met cryptografische integriteitsverificatie en prestatiebewaking.
 #4.20.2    Niveau: 3    Rol: D/V
 Verifieer dat private informatieopvragsystemen databasequery's mogelijk maken zonder querypatronen bloot te geven, met cryptografische bescherming van toegangspatronen.
 #4.20.3    Niveau: 3    Rol: D/V
 Verifieer dat veilige multi-party computation-protocollen privacy-beschermende AI-inferentie mogelijk maken zonder individuele invoer of tussenliggende berekeningen bloot te stellen.
 #4.20.4    Niveau: 3    Rol: D/V
 Verifieer dat privacy-beschermend sleutelhbeheer gedistribueerde sleutelgeneratie, drempelcryptografie en veilige sleutelrotatie met hardware-ondersteuning omvat.
 #4.20.5    Niveau: 3    Rol: D/V
 Verifieer dat de privacy-beschermende rekenprestaties worden geoptimaliseerd door batching, caching en hardwareversnelling, terwijl de cryptografische beveiligingsgaranties behouden blijven.

---

### C4.15 Agent Framework Cloud-integratiebeveiliging & Hybride implementatie

Beveiligingscontroles voor cloud-geïntegreerde agentkaders met hybride on-premises/cloud-architecturen.

 #4.15.1    Niveau: 1    Rol: D/V
 Controleer of de integratie van cloudopslag end-to-end encryptie gebruikt met sleutelbeheer dat door de agent wordt gecontroleerd.
 #4.15.2    Niveau: 2    Rol: D/V
 Controleer of de beveiligingsgrenzen van de hybride implementatie duidelijk zijn gedefinieerd met versleutelde communicatiekanalen.
 #4.15.3    Niveau: 2    Rol: D/V
 Verifieer dat de toegang tot cloudbronnen zero-trust verificatie omvat met continue authenticatie.
 #4.15.4    Niveau: 3    Rol: D/V
 Verifieer dat gegevensresidentie-eisen worden afgedwongen door cryptografische attestatie van opslaglocaties.
 #4.15.5    Niveau: 3    Rol: D/V
 Verifieer of de beveiligingsbeoordelingen van de cloudprovider agent-specifieke dreigingsmodellering en risicobeoordeling omvatten.

---

### Referenties

NIST Cybersecurity Framework 2.0
CIS Controls v8
OWASP Container Security Verification Standard
Kubernetes Security Best Practices
SLSA Supply Chain Security Framework
NIST SP 800-190: Application Container Security Guide
Cloud Security Alliance: Cloud Controls Matrix
ENISA: Secure Infrastructure Design
NIST SP 800-53: Security Controls for Federal Information Systems
ISO 27001:2022 Information Security Management
NIST AI Risk Management Framework
CIS Kubernetes Benchmark
FIPS 140-2 Security Requirements
NIST SP 800-207: Zero Trust Architecture
IEEE 2857: Privacy Engineering for AI Systems
NIST SP 800-161: Cybersecurity Supply Chain Risk Management
NIST Post-Quantum Cryptography Standards
Intel SGX Developer Guide
AMD SEV-SNP White Paper
ARM TrustZone Technology
ZK-SNARKs: A Gentle Introduction
NIST SP 800-57: Cryptographic Key Management
Side-Channel Attack Countermeasures
Neuromorphic Computing Security Challenges
FPGA Security: Fundamentals, Evaluation, and Countermeasures
Microsoft SEAL: Homomorphic Encryption Library
HElib: Homomorphic Encryption Library
PALISADE Lattice Cryptography Library
Differential Privacy: A Survey of Results
Secure Aggregation for Federated Learning
Private Information Retrieval: Concepts and Constructions

## C5 Toegangscontrole & Identiteit voor AI-componenten & gebruikers

### Beheersingsdoelstelling

Effectieve toegangscontrole voor AI-systemen vereist robuust identiteitsbeheer, contextbewuste autorisatie en runtime handhaving volgens zero-trust principes. Deze controles zorgen ervoor dat mensen, services en autonome agenten alleen interactie hebben met modellen, data en rekenmiddelen binnen expliciet toegewezen reikwijdtes, met continue verificatie- en auditmogelijkheden.

---

### C5.1 Identiteitsbeheer & Authenticatie

Stel cryptografisch ondersteunde identiteiten in voor alle entiteiten met multi-factor authenticatie voor bevoorrechte handelingen.

 #5.1.1    Niveau: 1    Rol: D/V
 Controleer of alle menselijke gebruikers en serviceprincipals zich authenticeren via een gecentraliseerde enterprise identity provider (IdP) met behulp van OIDC/SAML-protocollen met unieke identity-to-token mappings (geen gedeelde accounts of referenties).
 #5.1.2    Niveau: 1    Rol: D/V
 Controleer of risicovolle handelingen (modelimplementatie, export van gewichten, toegang tot trainingsgegevens, wijzigingen in productieconfiguraties) multi-factor authenticatie of step-up authenticatie met sessiehervalidatie vereisen.
 #5.1.3    Niveau: 2    Rol: D
 Verifieer dat nieuwe principals een identiteitstoetsing ondergaan die overeenkomt met NIST 800-63-3 IAL-2 of gelijkwaardige standaarden voordat zij toegang krijgen tot het productiesysteem.
 #5.1.4    Niveau: 2    Rol: V
 Controleer of toegangsbeoordelingen elk kwartaal worden uitgevoerd met geautomatiseerde detectie van inactieve accounts, afdwinging van wachtwoordrotatie en workflows voor het intrekken van toegang.
 #5.1.5    Niveau: 3    Rol: D/V
 Verifieer dat gefedereerde AI-agenten zich authenticeren via ondertekende JWT-asserties die een maximale levensduur van 24 uur hebben en cryptografisch bewijs van oorsprong bevatten.

---

### C5.2 Brontoestemming & Minimaal Privilege

Implementeer fijnmazige toegangscontroles voor alle AI-middelen met expliciete toestemmingsmodellen en controlelogboeken.

 #5.2.1    Niveau: 1    Rol: D/V
 Controleer of elke AI-bron (datasets, modellen, endpoints, vectorverzamelingen, embed-indexen, compute-instanties) rolgebaseerde toegangscontroles afdwingt met expliciete toestemmingslijsten en standaard-weigerbeleid.
 #5.2.2    Niveau: 1    Rol: D/V
 Verifieer dat het principe van minste-privilege standaard wordt afgedwongen bij serviceaccounts, te beginnen met alleen-lezen machtigingen en dat een gedocumenteerde zakelijke rechtvaardiging vereist is voor schrijfaccess.
 #5.2.3    Niveau: 1    Rol: V
 Controleer of alle wijzigingen in de toegangscontrole gekoppeld zijn aan goedgekeurde wijzigingsverzoeken en onveranderlijk zijn vastgelegd met tijdstempels, identiteiten van actoren, resource-identificaties en permissieverschillen.
 #5.2.4    Niveau: 2    Rol: D
 Controleer of dataclassificatielabels (PII, PHI, exportbeperkt, eigendom) automatisch worden doorgegeven aan afgeleide bronnen (embeddings, promptcaches, modeluitvoer) met consistente beleidsafhandeling.
 #5.2.5    Niveau: 2    Rol: D/V
 Controleer of pogingen tot onbevoegde toegang en privilege-escalatiegebeurtenissen binnen 5 minuten realtime waarschuwingen met contextuele metadata naar SIEM-systemen verzenden.

---

### C5.3 Dynamische beleidsevaluatie

Implementeer attribute-based access control (ABAC) engines voor contextbewuste autorisatiebeslissingen met auditmogelijkheden.

 #5.3.1    Niveau: 1    Rol: D/V
 Controleer of autorisatiebeslissingen zijn uitbesteed aan een speciale beleidsengine (OPA, Cedar of equivalent) die toegankelijk is via geverifieerde API's met cryptografische integriteitsbescherming.
 #5.3.2    Niveau: 1    Rol: D/V
 Controleer of beleidsregels dynamische attributen evalueren tijdens runtime, waaronder het beveiligingsniveau van de gebruiker, de gevoeligheidsclassificatie van de bron, de context van het verzoek, tenant-isolatie en temporele beperkingen.
 #5.3.3    Niveau: 2    Rol: D
 Verifieer dat beleidsdefinities versiebeheer hebben, door collega's zijn beoordeeld en gevalideerd worden via geautomatiseerde tests in CI/CD-pijplijnen voordat ze in productie worden ingezet.
 #5.3.4    Niveau: 2    Rol: V
 Verifieer dat de resultaten van beleidsbeoordeling gestructureerde besluitvormingsredenen bevatten en worden verzonden naar SIEM-systemen voor correlatieanalyse en nalevingsrapportage.
 #5.3.5    Niveau: 3    Rol: D/V
 Controleer of de time-to-live (TTL) waarden van het beleidscache de 5 minuten niet overschrijden voor hooggevoelige bronnen en 1 uur voor standaardbronnen met cache-invalideringsmogelijkheden.

---

### C5.4 Beveiligingshandhaving tijdens query-uitvoering

Implementeer beveiligingscontroles op databaselaag met verplichte filtering en beveiligingsbeleid op rijniveau.

 #5.4.1    Niveau: 1    Rol: D/V
 Verifieer dat alle vector database- en SQL-query's verplichte beveiligingsfilters bevatten (tenant-ID, gevoeligheidslabels, gebruikersscope) die worden afgedwongen op het niveau van de database-engine, niet in de applicatiecode.
 #5.4.2    Niveau: 1    Rol: D/V
 Controleer of row-level security (RLS)-beleid en veldniveau-maskering met beleids-erfenis zijn ingeschakeld voor alle vector-databases, zoekindexen en trainingsdatasets.
 #5.4.3    Niveau: 2    Rol: D
 Verifieer dat mislukte autorisatie-evaluaties "confused deputy-aanvallen" voorkomen door queries onmiddellijk te stoppen en expliciete autorisatiefoutcodes terug te geven in plaats van lege resultaatsets te retourneren.
 #5.4.4    Niveau: 2    Rol: V
 Controleer of de beleidsbeoordelingsvertraging continu wordt gemonitord met geautomatiseerde waarschuwingen voor time-outvoorwaarden die een omzeiling van autorisatie mogelijk kunnen maken.
 #5.4.5    Niveau: 3    Rol: D/V
 Controleer of query-herhaalmethoden autorisatiebeleid opnieuw evalueren om rekening te houden met dynamische permissiewijzigingen binnen actieve gebruikerssessies.

---

### C5.5 Uitvoerfiltering & Gegevensverliespreventie

Implementeer nabehandelingscontroles om ongeautoriseerde blootstelling van gegevens in door AI gegenereerde inhoud te voorkomen.

 #5.5.1    Niveau: 1    Rol: D/V
 Verifieer dat mechanismen voor filtering na inferentie ongeautoriseerde PII, geclassificeerde informatie en eigendomsgegevens scannen en schrappen voordat de inhoud aan verzoekers wordt geleverd.
 #5.5.2    Niveau: 1    Rol: D/V
 Controleer of citaties, referenties en bronvermeldingen in modeluitvoer worden geverifieerd aan de hand van caller-autoriteiten en verwijder deze indien onbevoegde toegang wordt gedetecteerd.
 #5.5.3    Niveau: 2    Rol: D
 Controleer of de beperkingen voor uitvoerformaten (gesaniteerde PDF's, met metadata ontdane afbeeldingen, goedgekeurde bestandstypen) worden gehandhaafd op basis van gebruikersmachtigingsniveaus en dataclassificaties.
 #5.5.4    Niveau: 2    Rol: V
 Controleer of redactie-algoritmen deterministisch zijn, versiebeheer hebben en auditlogboeken bijhouden om compliance-onderzoeken en forensische analyses te ondersteunen.
 #5.5.5    Niveau: 3    Rol: V
 Verifieer dat hoge-risico redactie-evenementen adaptieve logs genereren die cryptografische hashes van de originele inhoud bevatten voor forensische terughaalbaarheid zonder datagebruik.

---

### C5.6 Multi-Tenant Isolatie

Zorg voor cryptografische en logische isolatie tussen huurders in gedeelde AI-infrastructuur.

 #5.6.1    Niveau: 1    Rol: D/V
 Controleer of geheugenruimtes, embedding-opslag, cache-items en tijdelijke bestanden gescheiden zijn per namespace per huurder, met veilige verwijdering bij het verwijderen van de huurder of het beëindigen van de sessie.
 #5.6.2    Niveau: 1    Rol: D/V
 Controleer of elke API-aanvraag een geverifieerde tenant-identificatie bevat die cryptografisch wordt gevalideerd aan de hand van de sessiecontext en gebruikersrechten.
 #5.6.3    Niveau: 2    Rol: D
 Verifieer dat netwerkbeleid standaard-weigerregels implementeert voor communicatie tussen verschillende tenants binnen servicenetwerken en containerorchestratietools.
 #5.6.4    Niveau: 3    Rol: D
 Verifieer dat encryptiesleutels uniek zijn per tenant met ondersteuning voor door de klant beheerde sleutels (CMK) en cryptografische isolatie tussen tenant-datastores.

---

### C5.7 Autorisatie van autonome agenten

Beheer toestemming voor AI-agents en autonome systemen via gescopeerde capaciteits tokens en continue autorisatie.

 #5.7.1    Niveau: 1    Rol: D/V
 Controleer of autonome agenten gescopeerde capability-tokens ontvangen die expliciet de toegestane acties, toegankelijke bronnen, tijdsgrenzen en operationele beperkingen opsommen.
 #5.7.2    Niveau: 1    Rol: D/V
 Controleer of hoog-risico functies (toegang tot het bestandssysteem, code-uitvoering, externe API-aanroepen, financiële transacties) standaard zijn uitgeschakeld en expliciete autorisaties vereisen voor activatie met zakelijke rechtvaardigingen.
 #5.7.3    Niveau: 2    Rol: D
 Verifieer dat capaciteitstokens gebonden zijn aan gebruikerssessies, cryptografische integriteitsbescherming bevatten, en zorg ervoor dat ze niet kunnen worden opgeslagen of hergebruikt in offline scenario's.
 #5.7.4    Niveau: 2    Rol: V
 Verifieer dat door agent geïnitieerde acties een secundaire autorisatie ondergaan via de ABAC-beleidsengine met volledige contextevaluatie en auditlogboeken.
 #5.7.5    Niveau: 3    Rol: V
 Controleer of foutcondities van agenten en uitzonderingafhandeling informatie over het capaciteitsbereik bevatten om ondersteuning te bieden bij incidentenanalyse en forensisch onderzoek.

---

### Referenties

#### Normen & Kaders

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Implementatiehandleidingen

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### AI-specifieke beveiliging

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Beveiliging van de toeleveringsketen voor modellen, frameworks en data

### Beheersingsdoelstelling

AI-aanvalen op de toeleveringsketen maken gebruik van modellen, frameworks of datasets van derden om achterdeurtjes, vooringenomenheid of exploitbare code in te bouwen. Deze controles bieden end-to-end herkomst, beheer van kwetsbaarheden en monitoring om de gehele levenscyclus van het model te beschermen.

---

### C6.1 Vooropleiding Modelbeoordeling & Herkomst

Beoordeel en verifieer de herkomst, licenties en verborgen gedragingen van modellen van derden voordat u enige fine-tuning of implementatie uitvoert.

 #6.1.1    Niveau: 1    Rol: D/V
 Verifieer dat elk derde‑partij modelartifact een ondertekend herkomstrecord bevat dat de bronrepository en commit-hash identificeert.
 #6.1.2    Niveau: 1    Rol: D/V
 Verifieer dat modellen met geautomatiseerde hulpmiddelen worden gescand op kwaadaardige lagen of Trojaanse triggers voordat ze worden geïmporteerd.
 #6.1.3    Niveau: 2    Rol: D
 Controleer of transfer-learning fine-tuning slaagt voor adversariële evaluatie om verborgen gedragingen te detecteren.
 #6.1.4    Niveau: 2    Rol: V
 Controleer of modellicenties, exportcontroleslabels en verklaringen over de herkomst van gegevens zijn vastgelegd in een ML-BOM-item.
 #6.1.5    Niveau: 3    Rol: D/V
 Verifieer dat hoog-risicomodellen (openbaar geüploade gewichten, niet-geverifieerde makers) in quarantaine blijven totdat een menselijke beoordeling en goedkeuring heeft plaatsgevonden.

---

### C6.2 Framework- en bibliotheekscanning

Continu continu continu scannen ML-frameworks en -bibliotheken op CVE's en kwaadaardige code om de runtime-stack veilig te houden.

 #6.2.1    Niveau: 1    Rol: D/V
 Verifieer dat CI-pijplijnen afhankelijkheidsscanners uitvoeren op AI-frameworks en kritieke bibliotheken.
 #6.2.2    Niveau: 1    Rol: D/V
 Controleer of kritieke kwetsbaarheden (CVSS ≥ 7.0) de promotie naar productieafbeeldingen blokkeren.
 #6.2.3    Niveau: 2    Rol: D
 Controleer of statische code-analyse wordt uitgevoerd op geforkte of gevendorde ML-bibliotheken.
 #6.2.4    Niveau: 2    Rol: V
 Controleer of voorstellen voor framework-upgrades een beoordeling van de beveiligingsimpact bevatten met verwijzing naar openbare CVE-feeds.
 #6.2.5    Niveau: 3    Rol: V
 Verifieer dat runtime-sensoren waarschuwen bij onverwachte dynamische bibliotheekladingen die afwijken van de ondertekende SBOM.

---

### C6.3 Afhankelijkheid vastzetten & verificatie

Veranker elke afhankelijkheid aan onveranderlijke digests en reproduceer builds om identieke, niet-te-manipuleren artefacten te garanderen.

 #6.3.1    Niveau: 1    Rol: D/V
 Controleer of alle pakketbeheerders versiebevriezing afdwingen via lockfiles.
 #6.3.2    Niveau: 1    Rol: D/V
 Controleer of onveranderlijke digests worden gebruikt in plaats van wijzigbare tags in containerreferenties.
 #6.3.3    Niveau: 2    Rol: D
 Controleer of reproduceerbare-buildcontroles hashes vergelijken tussen CI-runs om identieke outputs te garanderen.
 #6.3.4    Niveau: 2    Rol: V
 Controleer of bouwattesten 18 maanden worden opgeslagen voor audit-traceerbaarheid.
 #6.3.5    Niveau: 3    Rol: D
 Controleer of verlopen afhankelijkheden geautomatiseerde PR's activeren om bijgewerkte of geforkte vaste versies.

---

### C6.4 Handhaving van Vertrouwde Bron

Sta alleen downloads van artefacten toe van cryptografisch geverifieerde, door de organisatie goedgekeurde bronnen en blokkeer alles wat anders is.

 #6.4.1    Niveau: 1    Rol: D/V
 Controleer of modelgewichten, datasets en containers alleen worden gedownload van goedgekeurde domeinen of interne registries.
 #6.4.2    Niveau: 1    Rol: D/V
 Controleer of Sigstore/Cosign-handtekeningen de identiteit van de uitgever verifiëren voordat artefacten lokaal worden gecachet.
 #6.4.3    Niveau: 2    Rol: D
 Controleer of uitgaande proxies onbevoegde downloads van artefacten blokkeren om het beleid voor vertrouwde bronnen af te dwingen.
 #6.4.4    Niveau: 2    Rol: V
 Verifieer dat repository-toegangs‑lijsten elk kwartaal worden herzien met bewijs van zakelijke rechtvaardiging voor elke vermelding.
 #6.4.5    Niveau: 3    Rol: V
 Controleer of beleidschendingen het in quarantaine plaatsen van artefacten en het terugdraaien van afhankelijke pijpleningsruns activeren.

---

### C6.5 Risicobeoordeling van datasets van derden

Evalueer externe datasets op vergiftiging, vooringenomenheid en juridische naleving, en monitor ze gedurende hun hele levenscyclus.

 #6.5.1    Niveau: 1    Rol: D/V
 Controleer of externe datasets een risicoanalyse op vergiftiging ondergaan (bijv. datafingerprinting, detectie van uitschieters).
 #6.5.2    Niveau: 1    Rol: D
 Controleer of bias-metrics (demografische pariteit, gelijke kansen) worden berekend vóór goedkeuring van de dataset.
 #6.5.3    Niveau: 2    Rol: V
 Controleer of provenance en licentievoorwaarden voor datasets worden vastgelegd in ML-BOM-items.
 #6.5.4    Niveau: 2    Rol: V
 Verifieer dat periodieke monitoring afwijkingen of corruptie in gehoste datasets detecteert.
 #6.5.5    Niveau: 3    Rol: D
 Verifieer dat niet-toegestane inhoud (auteursrecht, PII) via geautomatiseerde verwijdering wordt verwijderd voorafgaand aan het trainen.

---

### C6.6 Supply Chain-aanvalmonitoring

Detecteer dreigingen in de toeleveringsketen vroegtijdig via CVE-feeds, auditloganalyse en red-team simulaties.

 #6.6.1    Niveau: 1    Rol: V
 Verifieer dat CI/CD-auditlogs worden gestreamd naar SIEM-detecties voor afwijkende pakketdownloads of gemanipuleerde bouwstappen.
 #6.6.2    Niveau: 2    Rol: D
 Verifieer of incident response playbooks terugrolprocedures bevatten voor gecompromitteerde modellen of bibliotheken.
 #6.6.3    Niveau: 3    Rol: V
 Controleer of threat-intel verrijking ML-specifieke indicatoren (bijv. modelvergiftiging IoC's) tagt bij de alerteringsverificatie.

---

### C6.7 ML-BOM voor Model Artefacten

Genereer en onderteken gedetailleerde ML-specifieke SBOM's (ML-BOM's) zodat downstream gebruikers de integriteit van componenten kunnen verifiëren bij implementatietijd.

 #6.7.1    Niveau: 1    Rol: D/V
 Verifieer dat elke modelartefact een ML-BOM publiceert die datasets, gewichten, hyperparameters en licenties vermeldt.
 #6.7.2    Niveau: 1    Rol: D/V
 Verifieer dat de ML‑BOM generatie en Cosign ondertekening geautomatiseerd zijn in CI en vereist zijn voor samenvoeging.
 #6.7.3    Niveau: 2    Rol: D
 Controleer of ML‑BOM volledigheidscontroles de build laten mislukken als er metadata van een component (hash, licentie) ontbreekt.
 #6.7.4    Niveau: 2    Rol: V
 Verifieer dat downstreamgebruikers ML-BOM's via API kunnen opvragen om geïmporteerde modellen te valideren tijdens de implementatietijd.
 #6.7.5    Niveau: 3    Rol: V
 Controleer of ML-BOM's versiebeheer hebben en worden vergeleken om ongeautoriseerde wijzigingen te detecteren.

---

### Referenties

ML Supply Chain Compromise – MITRE ATLAS
Supply‑chain Levels for Software Artifacts (SLSA)
CycloneDX – Machine Learning Bill of Materials
What is Data Poisoning? – SentinelOne
Transfer Learning Attack – OWASP ML Security Top 10
AI Data Security Best Practices – CISA
Secure CI/CD Supply Chain – Sumo Logic
AI & Transparency: Protect ML Models – ReversingLabs
SBOM Overview – CISA
Training Data Poisoning Guide – Lakera.ai
Dependency Pinning for Reproducible Python – Medium

## C7 Modelgedrag, outputcontrole en veiligheidsborging

### Beheersingsdoelstelling

Modeluitvoer moet gestructureerd, betrouwbaar, veilig, verklaarbaar en continu gemonitord worden in productie. Dit vermindert hallucinaties, privacylekken, schadelijke inhoud en ongecontroleerde acties, terwijl het vertrouwen van gebruikers en naleving van regelgeving toenemen.

---

### C7.1 Handhaving van het uitvoerformaat

Strikte schema's, beperkte decodering en downstream validatie voorkomen dat verkeerd gevormde of kwaadaardige inhoud zich verspreidt.

 #7.1.1    Niveau: 1    Rol: D/V
 Verifieer dat responschema's (bijv. JSON Schema) worden meegeleverd in de systeem prompt en dat elke output automatisch wordt gevalideerd; niet-conforme outputs leiden tot herstelpogingen of afwijzing.
 #7.1.2    Niveau: 1    Rol: D/V
 Controleer of begrensde decodering (stop tokens, regex, max-tokens) is ingeschakeld om overloop of promptinjectie-zijdekanalen te voorkomen.
 #7.1.3    Niveau: 2    Rol: D/V
 Controleer of downstreamcomponenten uitvoer als onbetrouwbaar behandelen en deze valideren aan de hand van schema's of injectieveilige deserializers.
 #7.1.4    Niveau: 3    Rol: V
 Verifieer dat onjuiste uitvoergebeurtenissen worden gelogd, gerate-limiteerd en zichtbaar gemaakt voor monitoring.

---

### C7.2 Hallucinatie Detectie & Mitigatie

Onzekerheidsinschatting en terugvalstrategieën beperken gefabriceerde antwoorden.

 #7.2.1    Niveau: 1    Rol: D/V
 Controleer of token-niveau log-waarschijnlijkheden, ensemble zelfconsistentie, of fijn afgestelde hallucinatie detectors een vertrouwensscore aan elk antwoord toewijzen.
 #7.2.2    Niveau: 1    Rol: D/V
 Controleer of reacties onder een configureerbare betrouwbaarheidsdrempel fallback-werkstromen activeren (bijv. retrieval-augmented generation, secundair model of menselijke beoordeling).
 #7.2.3    Niveau: 2    Rol: D/V
 Controleer of hallucinatie-incidenten zijn voorzien van root-cause metadata en worden doorgegeven aan post-mortem en finetuning pijplijnen.
 #7.2.4    Niveau: 3    Rol: D/V
 Controleer of drempelwaarden en detectoren opnieuw worden gekalibreerd na grote model- of kennisbasisupdates.
 #7.2.5    Niveau: 3    Rol: V
 Controleer of dashboardvisualisaties de hallucinatiepercentages bijhouden.

---

### C7.3 Outputveiligheid en Privacyfiltering

Beleidsfilters en red-team dekking beschermen gebruikers en vertrouwelijke gegevens.

 #7.3.1    Niveau: 1    Rol: D/V
 Controleer of pre- en post-generatie classificatoren haat, intimidatie, zelfbeschadiging, extremistische en seksueel expliciete inhoud die in lijn is met het beleid blokkeren.
 #7.3.2    Niveau: 1    Rol: D/V
 Controleer of PII/PCI-detectie en automatische redactie op elke respons worden uitgevoerd; overtredingen leiden tot een privacy-incident.
 #7.3.3    Niveau: 2    Rol: D
 Controleer of vertrouwelijkheidslabels (bijvoorbeeld handelsgeheimen) zich over modaliteiten heen verspreiden om lekkage in tekst, afbeeldingen of code te voorkomen.
 #7.3.4    Niveau: 3    Rol: D/V
 Controleer of pogingen tot het omzeilen van de filter of classificaties met hoog risico secundaire goedkeuring of herauthenticatie van de gebruiker vereisen.
 #7.3.5    Niveau: 3    Rol: D/V
 Controleer of de filterdrempels overeenkomen met de juridische jurisdicties en de context van de leeftijd/rol van de gebruiker.

---

### C7.4 Output- en Actiebeperking

Rate-limieten en goedkeuringspoorten voorkomen misbruik en buitensporige autonomie.

 #7.4.1    Niveau: 1    Rol: D
 Controleer of per-gebruiker en per-API-sleutel quota verzoeken, tokens en kosten beperken met exponentiële back-off bij 429-fouten.
 #7.4.2    Niveau: 1    Rol: D/V
 Verifieer dat geprivilegieerde acties (bestandsschrijvingen, code-uitvoering, netwerkoproepen) goedkeuring op basis van beleid of menselijke tussenkomst vereisen.
 #7.4.3    Niveau: 2    Rol: D/V
 Verifieer dat cross-modale consistentiecontroles ervoor zorgen dat afbeeldingen, code en tekst die voor dezelfde aanvraag zijn gegenereerd, niet kunnen worden gebruikt om kwaadaardige inhoud te smokkelen.
 #7.4.4    Niveau: 2    Rol: D
 Controleer of agentdelegatiediepte, recursielimieten en toegestane hulplijsten expliciet zijn geconfigureerd.
 #7.4.5    Niveau: 3    Rol: V
 Verifieer dat het overschrijden van limieten gestructureerde beveiligingsgebeurtenissen genereert voor SIEM-inname.

---

### C7.5 Uitvoer Verklaarbaarheid

Transparante signalen verbeteren het vertrouwen van gebruikers en interne foutopsporing.

 #7.5.1    Niveau: 2    Rol: D/V
 Controleer of gebruikersgerichte betrouwbaarheidscores of korte redeneersamenvattingen worden weergegeven wanneer de risicobeoordeling dit passend acht.
 #7.5.2    Niveau: 2    Rol: D/V
 Controleer of gegenereerde uitleg vermijdt het onthullen van gevoelige systeemopdrachten of propriëtaire gegevens.
 #7.5.3    Niveau: 3    Rol: D
 Controleer of het systeem token-niveau log-waarschijnlijkheden of attentiekaarten vastlegt en opslaat voor geautoriseerde inspectie.
 #7.5.4    Niveau: 3    Rol: V
 Verifieer dat uitlegbaarheidsartefacten versiebeheer hebben naast modelreleases voor controleerbaarheid.

---

### C7.6 Monitoring Integratie

Realtime observeerbaarheid sluit de lus tussen ontwikkeling en productie.

 #7.6.1    Niveau: 1    Rol: D
 Controleer of de statistieken (schema-overtredingen, hallucinatiepercentage, toxiciteit, PII-lekken, latentie, kosten) naar een centraal bewakingsplatform worden gestreamd.
 #7.6.2    Niveau: 1    Rol: V
 Controleer of waarschuwingsdrempels zijn gedefinieerd voor elke veiligheidsmaatstaf, met escalatieroutes voor de dienstdoende medewerker.
 #7.6.3    Niveau: 2    Rol: V
 Controleer of dashboards output-anomalieën correleren met model/versie, feature-flag en wijzigingen in upstream-gegevens.
 #7.6.4    Niveau: 2    Rol: D/V
 Verifieer dat monitoringgegevens terugkoppelen naar het retrainen, fijn afstemmen of bijwerken van regels binnen een gedocumenteerde MLOps-workflow.
 #7.6.5    Niveau: 3    Rol: V
 Verifieer dat monitoring-pijplijnen zijn onderworpen aan penetratietests en toegangsgeregeld zijn om het lekken van gevoelige logbestanden te voorkomen.

---

### 7.7 Generatieve media beveiligingen

Zorg ervoor dat AI-systemen geen illegale, schadelijke of niet-geautoriseerde mediacontent genereren door beleidsbeperkingen, uitvoervalidatie en traceerbaarheid af te dwingen.

 #7.7.1    Niveau: 1    Rol: D/V
 Controleer of systeem prompts en gebruikersinstructies expliciet het genereren van illegale, schadelijke of niet-consensuele deepfake-media (zoals afbeelding, video, audio) verbieden.
 #7.7.2    Niveau: 2    Rol: D/V
 Controleer of prompts worden gefilterd op pogingen om imitatie te genereren, seksueel expliciete deepfakes, of media die echte personen zonder toestemming afbeelden.
 #7.7.3    Niveau: 2    Rol: V
 Controleer of het systeem gebruikmaakt van perceptuele hashing, watermerkdetectie of fingerprinting om ongeoorloofde reproductie van auteursrechtelijk beschermd materiaal te voorkomen.
 #7.7.4    Niveau: 3    Rol: D/V
 Verifieer dat alle gegenereerde media cryptografisch is ondertekend, van een watermerk is voorzien of is ingebed met manipulatieresistente herkomstmetadata voor traceerbaarheid downstream.
 #7.7.5    Niveau: 3    Rol: V
 Verifieer dat omzeilingspogingen (bijv. promptverduistering, slang, vijandige bewoording) worden gedetecteerd, gelogd en rate-limiting wordt toegepast; herhaald misbruik wordt aan monitorsystemen gemeld.

### Referenties

NIST AI Risk Management Framework
ISO/IEC 42001:2023 – AI Management System
OWASP Top-10 for Large Language Model Applications (2025)
Improper Output Handling – OWASP LLM05:2025
Practical Techniques to Constrain LLM Output
Dataiku – Structured Text Generation Guide
VL-Uncertainty: Detecting Hallucinations
HaDeMiF: Hallucination Detection & Mitigation
Building Confidence in LLM Outputs
Explainable AI & LLMs
LLM Red-Teaming Guide
Sensitive Information Disclosure in LLMs
LangChain – Chat Model Rate Limiting
OpenAI Rate-Limit & Exponential Back-off
Arize AI – LLM Observability Platform

## C8 Geheugen, Embeddings en Vector Database Beveiliging

### Beheersingsdoelstelling

Embeddings en vectoropslag fungeren als het "actieve geheugen" van hedendaagse AI-systemen, waarbij ze continu door gebruikers aangeleverde data accepteren en deze terug in modelcontexten brengen via Retrieval-Augmented Generation (RAG). Als dit geheugen niet wordt beheerd, kan het PII lekken, consent schenden of worden omgekeerd om de originele tekst te reconstrueren. Het doel van deze controlegroep is om geheugenpijplijnen en vectordatabases te versterken zodat toegang op basis van het minste-privilege is, embeddings privacybeschermend zijn, opgeslagen vectoren verlopen of op verzoek kunnen worden ingetrokken, en het geheugen per gebruiker nooit de prompts of uitkomsten van een andere gebruiker besmet.

---

### C8.1 Toegangscontroles op geheugen- en RAG-indexen

Handhaaf fijnmazige toegangscontroles op elke vectorverzameling.

 #8.1.1    Niveau: 1    Rol: D/V
 Verifieer dat toegangscontroleregels op rij-/namespace-niveau insert-, delete- en query-bewerkingen beperken per tenant, collectie of documenttag.
 #8.1.2    Niveau: 1    Rol: D/V
 Controleer of API-sleutels of JWT's gescopeerde claims bevatten (bijv. collectie-ID's, actie-werkwoorden) en minimaal elk kwartaal worden vervangen.
 #8.1.3    Niveau: 2    Rol: D/V
 Verifieer dat pogingen tot privilege-escalatie (bijv. cross-namespace similarity queries) worden gedetecteerd en binnen 5 minuten worden gelogd naar een SIEM.
 #8.1.4    Niveau: 2    Rol: D/V
 Controleer of de vector-DB de auditlog bijhoudt van subject-identificatie, bewerking, vector-ID/namespace, gelijkenisdrempel en resultaataantal.
 #8.1.5    Niveau: 3    Rol: V
 Controleer of toegangsbeslissingen worden getest op omzeilingsfouten telkens wanneer engines worden bijgewerkt of regels voor index-sharding veranderen.

---

### C8.2 Inbedding Sanering & Validatie

Controleer tekst vooraf op PII, redacteer of pseudonimiseer voordat vectorisatie plaatsvindt, en bewerk optioneel de embeddings achteraf om resterende signalen te verwijderen.

 #8.2.1    Niveau: 1    Rol: D/V
 Verifieer dat PII en gereguleerde gegevens worden gedetecteerd via geautomatiseerde classifieringssystemen en voorafgaand aan embedding worden gemaskeerd, getokeniseerd of verwijderd.
 #8.2.2    Niveau: 1    Rol: D
 Verifieer dat embedding-pijplijnen invoer met uitvoerbare code of niet-UTF-8-artikelen die de index kunnen besmetten, afwijzen of in quarantaine plaatsen.
 #8.2.3    Niveau: 2    Rol: D/V
 Controleer of lokale of metrische differentiële privacy-sanitatie wordt toegepast op zin-embedings waarvan de afstand tot een bekende PII-token onder een configureerbare drempelwaarde valt.
 #8.2.4    Niveau: 2    Rol: V
 Verifieer dat de effectiviteit van sanering (bijvoorbeeld recall van PII-redactie, semantische verschuiving) minstens halfjaarlijks wordt gevalideerd aan de hand van benchmarkcorpora.
 #8.2.5    Niveau: 3    Rol: D/V
 Controleer of sanitatieconfiguraties versiebeheer hebben en dat wijzigingen een peer review ondergaan.

---

### C8.3 Geheugenverval, intrekking en verwijdering

De GDPR "recht om vergeten te worden" en vergelijkbare wetten vereisen tijdige verwijdering; vectoropslag moet daarom TTL's, harde verwijderingen en tomb-stoning ondersteunen, zodat ingetrokken vectoren niet kunnen worden hersteld of opnieuw geïndexeerd.

 #8.3.1    Niveau: 1    Rol: D/V
 Verifieer dat elke vector- en metadatarecord een TTL of expliciet retentielabel heeft dat wordt gehonoreerd door geautomatiseerde opruimtaken.
 #8.3.2    Niveau: 1    Rol: D/V
 Controleer of door de gebruiker geïnitieerde verwijderingsverzoeken vectoren, metadata, cachekopieën en afgeleide indexen binnen 30 dagen wissen.
 #8.3.3    Niveau: 2    Rol: D
 Controleer of logische verwijderingen worden gevolgd door cryptografisch vernietigen van opslagblokken als de hardware dit ondersteunt, of door vernietiging van sleutel in het sleutelkluis.
 #8.3.4    Niveau: 3    Rol: D/V
 Controleer of verlopen vectoren binnen < 500 ms na verlopen worden uitgesloten van de resultaten van de dichtstbijzijnde buurzoektocht.

---

### C8.4 Voorkom omkering en lekkage van embedding

Recente verdedigingsmethoden—ruis-superpositie, projectienetwerken, privacy-neuronperturbatie en encryptie op applicatielaag—kunnen de token-niveau inversieratio's terugbrengen tot onder de 5%.

 #8.4.1    Niveau: 1    Rol: V
 Controleer of er een formeel dreigingsmodel bestaat dat inversie-, lidmaatschaps- en kenmerk-inferentieaanvallen omvat en dat jaarlijks wordt herzien.
 #8.4.2    Niveau: 2    Rol: D/V
 Controleer of applicatielaag-encryptie of doorzoekbare encryptie vectoren beschermt tegen directe uitlezing door infrastructuurbeheerders of cloudmedewerkers.
 #8.4.3    Niveau: 3    Rol: V
 Verifieer dat verdedigingsparameters (ε voor DP, ruis σ, projectierang k) privacy ≥ 99% tokenbescherming en bruikbaarheid ≤ 3% nauwkeurigheidsverlies in balans houden.
 #8.4.4    Niveau: 3    Rol: D/V
 Verifieer dat inversion-resilience metrics onderdeel zijn van release gates voor modelupdates, met gedefinieerde regressiebudgetten.

---

### C8.5 Toepassing van het Toegangsbeheer voor Gebruikersspecifiek Geheugen

Cross-tenant lekkage blijft een van de grootste RAG-risico's: onjuist gefilterde gelijkeniszoekopdrachten kunnen de privédocumenten van een andere klant aan het licht brengen.

 #8.5.1    Niveau: 1    Rol: D/V
 Verifieer of elke opvraag voor gegevensverwerking wordt nagesorteerd op tenant-/gebruikers-ID voordat deze aan de LLM-prompt wordt doorgegeven.
 #8.5.2    Niveau: 1    Rol: D
 Controleer of collectie namen of genamespaceerde ID's per gebruiker of huurder gezouten zijn zodat vectoren niet kunnen botsen tussen scopes.
 #8.5.3    Niveau: 2    Rol: D/V
 Controleer of gelijkenisresultaten boven een configureerbare afstandsdrempel maar buiten het bereik van de aanroeper worden weggegooid en beveiligingswaarschuwingen activeren.
 #8.5.4    Niveau: 2    Rol: V
 Verifieer dat multi-tenant stresstests adversariële queries simuleren die proberen documenten buiten de scope op te vragen en toon aan dat er geen lekken zijn.
 #8.5.5    Niveau: 3    Rol: D/V
 Verifieer dat encryptiesleutels per huurder gescheiden zijn, waarbij cryptografische isolatie wordt gegarandeerd, zelfs als fysieke opslag gedeeld wordt.

---

### C8.6 Geavanceerde Beveiliging van Geheugensystemen

Beveiligingscontroles voor geavanceerde geheugenarchitecturen, inclusief episodisch, semantisch en werkgeheugen met specifieke isolatie- en validatievereisten.

 #8.6.1    Niveau: 1    Rol: D/V
 Controleer of verschillende geheugen typen (episodisch, semantisch, werkgeheugen) geïsoleerde beveiligingscontexten hebben met op rollen gebaseerde toegangscontroles, aparte encryptiesleutels, en gedocumenteerde toegangs patronen voor elk geheugentype.
 #8.6.2    Niveau: 2    Rol: D/V
 Controleer of het geheugenconsolidatieproces een beveiligingsvalidatie omvat om te voorkomen dat kwaadaardige herinneringen worden geïnjecteerd via inhoudssanering, bronverificatie en integriteitscontroles vóór opslag.
 #8.6.3    Niveau: 2    Rol: D/V
 Controleer of geheugenophaalqueries worden gevalideerd en geschoond om te voorkomen dat ongeautoriseerde informatie wordt geëxtraheerd via analyse van querypatronen, handhaving van toegangscontrole en filtratie van resultaten.
 #8.6.4    Niveau: 3    Rol: D/V
 Controleer of geheugenvergeetmechanismen gevoelige informatie veilig verwijderen met cryptografische wissen-garanties door middel van sleuteldeling, meervoudig overschrijven of hardwaregebaseerde veilige verwijdering met verificatiecertificaten.
 #8.6.5    Niveau: 3    Rol: D/V
 Verifieer dat de integriteit van het geheugensysteem continu wordt gecontroleerd op ongeautoriseerde wijzigingen of beschadigingen via controlesommen, auditlogboeken en automatische waarschuwingen wanneer de geheugeninhoud verandert buiten de normale werking.

---

### Referenties

Vector database security: Pinecone – IronCore Labs
Securing the Backbone of AI: Safeguarding Vector Databases and Embeddings – Privacera
Enhancing Data Security with RBAC of Qdrant Vector Database – AI Advances
Mitigating Privacy Risks in LLM Embeddings from Embedding Inversion – arXiv
DPPN: Detecting and Perturbing Privacy-Sensitive Neurons – OpenReview
Art. 17 GDPR – Right to Erasure
Sensitive Data in Text Embeddings Is Recoverable – Tonic.ai
PII Identification and Removal – NVIDIA NeMo Docs
De-identifying Sensitive Data – Google Cloud DLP
Remove PII from Conversations Using Sensitive Information Filters – AWS Bedrock Guardrails
Think Your RAG Is Secure? Think Again – Medium
Design a Secure Multitenant RAG Inferencing Solution – Microsoft Learn
Best Practices for Multi-Tenancy RAG with Milvus – Milvus Blog

## 9 Autonome Orkestratie & Agentische Actiebeveiliging

### Beheersingsdoelstelling

Zorg ervoor dat autonome of multi-agent AI-systemen alleen acties kunnen uitvoeren die uitdrukkelijk bedoeld, geverifieerd, controleerbaar en binnen afgebakende kosten- en risicodrempels vallen. Dit beschermt tegen bedreigingen zoals compromittering van autonome systemen, misbruik van tools, detectie van agentloops, kaping van communicatie, identiteitsvervalsing, zwermmanipulatie en manipulatie van intenties.

---

### 9.1 Agent Taakplanning & Recursiebudgetten

Beperk recursieve plannen en verplicht menselijke controles voor bevoorrechte acties.

 #9.1.1    Niveau: 1    Rol: D/V
 Controleer of de maximale recursiediepte, breedte, wall-clock tijd, tokens en monetaire kosten per agentuitvoering centraal zijn geconfigureerd en versiebeheer ondergaan.
 #9.1.2    Niveau: 1    Rol: D/V
 Verifieer dat bevoorrechte of onomkeerbare acties (bijvoorbeeld code commits, financiële overboekingen) expliciete menselijke goedkeuring vereisen via een controleerbaar kanaal voordat ze worden uitgevoerd.
 #9.1.3    Niveau: 2    Rol: D
 Controleer of realtime resourcebewakers een circuitonderbreker-onderbreking activeren wanneer een budgetdrempel wordt overschreden, waardoor verdere taakuitbreiding wordt gestopt.
 #9.1.4    Niveau: 2    Rol: D/V
 Verifieer dat circuit-breaker gebeurtenissen worden geregistreerd met agent-ID, triggerconditie en vastgelegde plantoestand voor forensische beoordeling.
 #9.1.5    Niveau: 3    Rol: V
 Verifieer dat beveiligingstests scenario's met budget-uitputting en ontspoorde plannen dekken, en bevestig dat veilig stoppen zonder gegevensverlies plaatsvindt.
 #9.1.6    Niveau: 3    Rol: D
 Controleer of budgetbeleid wordt uitgedrukt als beleid-als-code en wordt afgedwongen in CI/CD om configuratie-afwijking te blokkeren.

---

### 9.2 Sandboxing van Tool-plugins

Isoleer toolinteracties om ongeautoriseerde systeemtoegang of code-uitvoering te voorkomen.

 #9.2.1    Niveau: 1    Rol: D/V
 Controleer of elke tool/plugin wordt uitgevoerd binnen een OS-, container- of WASM-niveau sandbox met beleid voor bestandssysteem, netwerk en systeemoproepen die het minste privilege vereisen.
 #9.2.2    Niveau: 1    Rol: D/V
 Controleer of sandbox resourcequota's (CPU, geheugen, schijf, netwerkuitgaand verkeer) en uitvoeringstijdslimieten worden afgedwongen en gelogd.
 #9.2.3    Niveau: 2    Rol: D/V
 Controleer of tool-binaries of descriptors digitaal zijn ondertekend; handtekeningen worden gevalideerd voordat ze worden geladen.
 #9.2.4    Niveau: 2    Rol: V
 Controleer of sandbox-telemetrie naar een SIEM stroomt; afwijkingen (bijv. pogingen tot uitgaande verbindingen) veroorzaken waarschuwingen.
 #9.2.5    Niveau: 3    Rol: V
 Verifieer dat risicovolle plugins een beveiligingsreview en penetratietest ondergaan voordat ze in productie worden ingezet.
 #9.2.6    Niveau: 3    Rol: D/V
 Controleer of pogingen tot het ontsnappen uit de sandbox automatisch worden geblokkeerd en dat de overtredende plugin in quarantaine wordt geplaatst in afwachting van onderzoek.

---

### 9.3 Autonome Lus & Kostenbegrenzing

Detecteer en stop ongecontroleerde agent-naar-agent recursie en kostenexplosies.

 #9.3.1    Niveau: 1    Rol: D/V
 Controleer of inter-agent oproepen een hoplimiet of TTL bevatten die door de runtime wordt verminderd en afgedwongen.
 #9.3.2    Niveau: 2    Rol: D
 Controleer of agenten een unieke oproepgrafiek-ID behouden om zelfoproepen of cyclische patronen te detecteren.
 #9.3.3    Niveau: 2    Rol: D/V
 Verifieer dat cumulatieve compute-unit en uitgaven tellers per verzoekketen worden bijgehouden; het overschrijden van de limiet breekt de keten af.
 #9.3.4    Niveau: 3    Rol: V
 Controleer of formele analyse of model checking het ontbreken van onbeperkte recursie in agentprotocollen aantoont.
 #9.3.5    Niveau: 3    Rol: D
 Controleer of loop-afbreekgebeurtenissen waarschuwingen genereren en continue-verbeteringsstatistieken aanleveren.

---

### 9.4 Bescherming tegen misbruik op protocolniveau

Beveilig communicatiekanalen tussen agenten en externe systemen om kaping of manipulatie te voorkomen.

 #9.4.1    Niveau: 1    Rol: D/V
 Verifieer dat alle berichten van agent naar tool en van agent naar agent geverifieerd zijn (bijvoorbeeld met mutual TLS of JWT) en end-to-end versleuteld zijn.
 #9.4.2    Niveau: 1    Rol: D
 Controleer of schema's strikt worden gevalideerd; onbekende velden of verkeerd gevormde berichten worden afgewezen.
 #9.4.3    Niveau: 2    Rol: D/V
 Controleer of integriteitscontroles (MAC's of digitale handtekeningen) het gehele berichtpayload inclusief toolparameters omvatten.
 #9.4.4    Niveau: 2    Rol: D
 Controleer of replay-bescherming (nonces of tijdstempelvensters) wordt afgedwongen op het protocolniveau.
 #9.4.5    Niveau: 3    Rol: V
 Verifieer dat protocollimplementaties worden onderworpen aan fuzzing en statische analyse op injectie- of deserialisatiefouten.

---

### 9.5 Agentidentiteit & Manipulatieweerbaarheid

Zorg ervoor dat acties toerekenbaar zijn en dat wijzigingen detecteerbaar zijn.

 #9.5.1    Niveau: 1    Rol: D/V
 Verifieer dat elke agentinstantie een unieke cryptografische identiteit bezit (sleutelpaar of hardware-verankerde referentie).
 #9.5.2    Niveau: 2    Rol: D/V
 Controleer of alle agentacties ondertekend en van een tijdstempel voorzien zijn; logs bevatten de handtekening voor ontkenningsbeveiliging.
 #9.5.3    Niveau: 2    Rol: V
 Verifieer dat manipulatiebestendige logs worden opgeslagen in een alleen-toevoegmedium of een schrijf-eenmaal medium.
 #9.5.4    Niveau: 3    Rol: D
 Controleer of identiteits-sleutels roteren volgens een vastgesteld schema en bij aanwijzingen voor compromittering.
 #9.5.5    Niveau: 3    Rol: D/V
 Controleer of pogingen tot spoofing of sleutelconflicten onmiddellijke quarantaine van de getroffen agent veroorzaken.

---

### 9.6 Multi-Agent Zwerm Risicobeperking

Beperk gevaren van collectief gedrag door isolatie en formele veiligheidsmodellering.

 #9.6.1    Niveau: 1    Rol: D/V
 Controleer of agenten die in verschillende beveiligingsdomeinen opereren, worden uitgevoerd in geïsoleerde runtime sandboxes of netwerksegmenten.
 #9.6.2    Niveau: 3    Rol: V
 Verifieer dat zwermgedragingen worden gemodelleerd en formeel geverifieerd op levendigheid en veiligheid voordat ze worden ingezet.
 #9.6.3    Niveau: 3    Rol: D
 Controleer of runtime monitors opkomende onveilige patronen (bijv. oscillaties, deadlocks) detecteren en corrigerende acties initiëren.

---

### 9.7 Gebruikers- en Toolauthenticatie / -autorisatie

Implementeer robuuste toegangscontroles voor elke door een agent geactiveerde actie.

 #9.7.1    Niveau: 1    Rol: D/V
 Controleer of agenten zich authentiseren als eersteklas hoofdpersonen bij downstream-systemen, en nooit de inloggegevens van eindgebruikers hergebruiken.
 #9.7.2    Niveau: 2    Rol: D
 Controleer of fijnmazige autorisatiebeleidsregels beperken welke tools een agent mag aanroepen en welke parameters deze mag leveren.
 #9.7.3    Niveau: 2    Rol: V
 Controleer of machtigingscontroles bij elke oproep opnieuw worden geëvalueerd (continue autorisatie), en niet alleen bij het begin van de sessie.
 #9.7.4    Niveau: 3    Rol: D
 Controleer of gedelegeerde privileges automatisch verlopen en dat opnieuw toestemming vereist is na time-out of wijziging van het bereik.

---

### 9.8 Beveiliging van communicatie tussen agenten

Versleutel en bescherm alle berichten tussen agenten tegen integriteitsverlies om afluisteren en manipulatie te voorkomen.

 #9.8.1    Niveau: 1    Rol: D/V
 Controleer of wederzijdse authenticatie en perfect-forward-secret encryptie (bijvoorbeeld TLS 1.3) verplicht zijn voor agentkanalen.
 #9.8.2    Niveau: 1    Rol: D
 Controleer of de berichtintegriteit en -herkomst worden geverifieerd vóór verwerking; fouten veroorzaken waarschuwingen en leiden tot het negeren van het bericht.
 #9.8.3    Niveau: 2    Rol: D/V
 Controleer of communicatiemetagegevens (tijdstempels, volgnummer) worden vastgelegd om forensische reconstructie te ondersteunen.
 #9.8.4    Niveau: 3    Rol: V
 Controleer of formele verificatie of model checking bevestigt dat protocol-toestandsmachines niet in onveilige toestanden kunnen worden gebracht.

---

### 9.9 Intentiecontrole & Handhaving van beperkingen

Valideer dat agentacties overeenkomen met de door de gebruiker aangegeven intentie en systeembeperkingen.

 #9.9.1    Niveau: 1    Rol: D
 Controleer of pre-executie constraintsolvers voorgestelde acties verifiëren aan harde gecodeerde veiligheids- en beleidsregels.
 #9.9.2    Niveau: 2    Rol: D/V
 Controleer of acties met grote impact (financieel, destructief, privacygevoelig) expliciete intentiebevestiging van de initiërende gebruiker vereisen.
 #9.9.3    Niveau: 2    Rol: V
 Controleer dat na-voorwaardecontroles bevestigen dat voltooide acties de beoogde effecten hebben bereikt zonder neveneffecten; afwijkingen veroorzaken een terugdraaiing.
 #9.9.4    Niveau: 3    Rol: V
 Verifieer dat formele methoden (bijv. model checking, theorem proving) of op eigenschappen gebaseerde tests aantonen dat agentplannen aan alle verklaarde beperkingen voldoen.
 #9.9.5    Niveau: 3    Rol: D
 Verifieer dat incidenten van intentie-ongelijkheid of schending van beperkingen bijdragen aan continue verbeteringscycli en het delen van dreigingsinformatie.

---

### 9.10 Beveiliging van de Redeneringsstrategie van Agenten

Veilige selectie en uitvoering van verschillende redeneerstrategieën, waaronder ReAct-, Chain-of-Thought- en Tree-of-Thoughts-benaderingen.

 #9.10.1    Niveau: 1    Rol: D/V
 Verifieer dat de selectie van redeneringsstrategie deterministische criteria gebruikt (invoercomplexiteit, type taak, beveiligingscontext) en dat identieke invoer identieke strategiekeuzes oplevert binnen dezelfde beveiligingscontext.
 #9.10.2    Niveau: 1    Rol: D/V
 Controleer of elke redeneermethode (ReAct, Chain-of-Thought, Tree-of-Thoughts) beschikt over specifieke invoervalidatie, uitvoeropschoning en uitvoeringstijdlimieten die zijn afgestemd op de betreffende cognitieve aanpak.
 #9.10.3    Niveau: 2    Rol: D/V
 Verifieer dat overgangen van redeneerstrategieën worden vastgelegd met volledige context, inclusief invoerkenmerken, waarden van selectiecriteria en uitvoeringsmetadata voor reconstructie van het auditspoor.
 #9.10.4    Niveau: 2    Rol: D/V
 Controleer of Tree-of-Thoughts-redenering vertakkingsbesnoeiingsmechanismen omvat die de verkenning beëindigen wanneer beleidschendingen, resourcebeperkingen of veiligheidsgrenzen worden gedetecteerd.
 #9.10.5    Niveau: 2    Rol: D/V
 Controleer of ReAct (Reason-Act-Observe) cycli validatiecontroles bevatten in elke fase: verificatie van de redeneerstap, autorisatie van de actie en sanering van de observatie voordat wordt doorgegaan.
 #9.10.6    Niveau: 3    Rol: D/V
 Controleer of prestatiestatistieken van redeneringsstrategieën (uitvoeringstijd, resourcegebruik, outputkwaliteit) worden gemonitord met geautomatiseerde waarschuwingen wanneer de statistieken afwijken van de geconfigureerde drempels.
 #9.10.7    Niveau: 3    Rol: D/V
 Controleer of hybride redeneermethoden die meerdere strategieën combineren, de invoervalidatie en uitvoerbeperkingen van alle samenstellende strategieën handhaven zonder beveiligingscontroles te omzeilen.
 #9.10.8    Niveau: 3    Rol: D/V
 Controleer of de beveiligingstests van redeneringsstrategieën fuzzing met verkeerd gevormde invoer bevatten, kwaadaardige prompts die bedoeld zijn om het wisselen van strategie af te dwingen, en grenswaardetests voor elke cognitieve benadering.

---

### 9.11 Agentlevenscyclusstatusbeheer & Beveiliging

Veilige agentinitialisatie, toestandovergangen en beëindiging met cryptografische auditsporen en gedefinieerde herstelprocedures.

 #9.11.1    Niveau: 1    Rol: D/V
 Controleer of de agent-initialisatie cryptografische identiteitsvaststelling omvat met hardware-ondersteunde referenties en onveranderlijke opstartauditlogs die agent-ID, tijdstempel, configuratiehash en initialisatieparameters bevatten.
 #9.11.2    Niveau: 2    Rol: D/V
 Controleer of agent-statusovergangen cryptografisch zijn ondertekend, voorzien van een tijdstempel en worden vastgelegd met volledige context, inclusief de activerende gebeurtenissen, de hash van de vorige status, de hash van de nieuwe status en de uitgevoerde beveiligingsvalidaties.
 #9.11.3    Niveau: 2    Rol: D/V
 Controleer of de agent afsluitprocedures een veilige geheugenwissing omvatten met behulp van cryptografische verwijdering of meervoudig overschrijven, intrekking van referenties met kennisgeving aan de certificaatautoriteit, en het genereren van manipulatiebestendige beëindigingscertificaten.
 #9.11.4    Niveau: 3    Rol: D/V
 Verifieer dat agentherstelsystemen de integriteit van de status valideren met behulp van cryptografische checksums (minimaal SHA-256) en terugkeren naar bekende goede staten wanneer corruptie wordt gedetecteerd, met automatische waarschuwingen en vereisten voor handmatige goedkeuring.
 #9.11.5    Niveau: 3    Rol: D/V
 Controleer of agentpersistentiemechanismen gevoelige statusgegevens versleutelen met per-agent AES-256-sleutels en implementeer veilige sleutelrotatie op configureerbare schema's (maximaal 90 dagen) met zero-downtime implementatie.

---

### 9.12 Beveiligingsframework voor toolintegratie

Beveiligingscontroles voor dynamische toolloading, uitvoering en resultaatvalidatie met gedefinieerde risicobeoordeling- en goedkeuringsprocessen.

 #9.12.1    Niveau: 1    Rol: D/V
 Controleer of toolomschrijvingen beveiligingsmetadata bevatten die de vereiste privileges specificeren (lezen/schrijven/uitvoeren), risiconiveaus (laag/middel/hoog), resourcebeperkingen (CPU, geheugen, netwerk) en validatievereisten die gedocumenteerd zijn in toolmanifests.
 #9.12.2    Niveau: 1    Rol: D/V
 Verifieer dat de uitvoeringsresultaten van tools worden gevalideerd aan de hand van verwachte schema's (JSON Schema, XML Schema) en beveiligingsbeleid (outputsanering, dataclassificatie) voordat ze worden geïntegreerd met time-outlimieten en procedures voor foutafhandeling.
 #9.12.3    Niveau: 2    Rol: D/V
 Verifieer dat toolinteractielogs een gedetailleerde beveiligingscontext bevatten, inclusief het gebruik van privileges, datatoegangs­patronen, uitvoeringstijd, resourceverbruik en retourcodes, met gestructureerde logging voor SIEM-integratie.
 #9.12.4    Niveau: 2    Rol: D/V
 Controleer of dynamische hulpmiddel-laadmechanismen digitale handtekeningen valideren met behulp van PKI-infrastructuur en implementeer veilige laadprotocollen met sandbox-isolatie en machtigingsverificatie voorafgaand aan uitvoering.
 #9.12.5    Niveau: 3    Rol: D/V
 Verifieer dat beveiligingsbeoordelingen van tools automatisch worden geactiveerd voor nieuwe versies met verplichte goedkeuringspoorten, inclusief statische analyse, dynamische testen en beoordeling door het beveiligingsteam met gedocumenteerde goedkeuringscriteria en SLA-vereisten.

---

#### Referenties

MITRE ATLAS tactics ML09
Circuit-breaker research for AI agents — Zou et al., 2024
Trend Micro analysis of sandbox escapes in AI agents — Park, 2025
Auth0 guidance on human-in-the-loop authorization for agents — Martinez, 2025
Medium deep-dive on MCP & A2A protocol hijacking — ForAISec, 2025
Rapid7 fundamentals on spoofing attack prevention — 2024
Imperial College verification of swarm systems — Lomuscio et al.
NIST AI Risk Management Framework 1.0, 2023
WIRED security briefing on encryption best practices, 2024
OWASP Top 10 for LLM Applications, 2025
Comprehensive Vulnerability Analysis is Necessary for Trustworthy LLM-MAS
[How Is LLM Reasoning Distracted by Irrelevant Context?
An Analysis Using a Controlled Benchmark](https://www.arxiv.org/pdf/2505.18761)
Large Language Model Sentinel: LLM Agent for Adversarial Purification
Securing Agentic AI: A Comprehensive Threat Model and Mitigation Framework for Generative AI Agents

## 10 Tegenaanvalbestendigheid & Privacybescherming

### Beheersingsdoelstelling

Zorg ervoor dat AI-modellen betrouwbaar, privacybeschermend en bestand tegen misbruik blijven bij het omgaan met ontwijkings-, inferentie-, extractie- of vergiftigingsaanvallen.

---

### 10.1 Modelafstemming & Veiligheid

Waak tegen schadelijke of beleidschendende output.

 #10.1.1    Niveau: 1    Rol: D/V
 Verifieer dat een alignement testpakket (red-team prompts, jailbreak probes, niet-toegestane inhoud) versiebeheerd wordt en bij elke modelrelease wordt uitgevoerd.
 #10.1.2    Niveau: 1    Rol: D
 Controleer of weigering en veilige-voltooiing beveiligingsmaatregelen worden gehandhaafd.
 #10.1.3    Niveau: 2    Rol: D/V
 Controleer of een geautomatiseerde beoordelaar het percentage schadelijke inhoud meet en regressies boven een bepaalde drempel markeert.
 #10.1.4    Niveau: 2    Rol: D
 Controleer of tegen-jailbreaktraining gedocumenteerd en reproduceerbaar is.
 #10.1.5    Niveau: 3    Rol: V
 Controleer of formele bewijsvoering van beleidsnaleving of gecertificeerde monitoring kritieke domeinen dekt.

---

### 10.2 Versterking tegen tegenstandersvoorbeelden

Verhoog de veerkracht tegen gemanipuleerde inputs. Robuuste adversariële training en benchmarkbeoordeling zijn de huidige beste praktijk.

 #10.2.1    Niveau: 1    Rol: D
 Controleer of projectrepositories adversarial-trainingconfiguraties bevatten met reproduceerbare seeds.
 #10.2.2    Niveau: 2    Rol: D/V
 Verifieer dat detectie van adversarial-examples blokkadewaarschuwingen veroorzaakt in productiepijplijnen.
 #10.2.4    Niveau: 3    Rol: V
 Controleer of gecertificeerde robuustheidsbewijzen of intervalgrenscertificaten minimaal de belangrijkste kritieke klassen omvatten.
 #10.2.5    Niveau: 3    Rol: V
 Verifieer dat regressietests adaptieve aanvallen gebruiken om te bevestigen dat er geen meetbaar verlies aan robuustheid is.

---

### 10.3 Beperking van lidmaatschapsinzicht

Beperk de mogelijkheid om te bepalen of een record in de trainingsgegevens zat. Differential privacy en maskering van confidence-scores blijven de meest effectieve bekende verdedigingsmethoden.

 #10.3.1    Niveau: 1    Rol: D
 Controleer of per-query entropieregulering of temperatuurschaling overmatige vertrouwen in voorspellingen vermindert.
 #10.3.2    Niveau: 2    Rol: D
 Verifieer dat training gebruikmaakt van ε-beperkte differentieel-private optimalisatie voor gevoelige datasets.
 #10.3.3    Niveau: 2    Rol: V
 Controleer of aanvalssimulaties (shadow-model of black-box) een aanval AUC ≤ 0,60 laten zien op niet eerder gebruikte gegevens.

---

### 10.4 Model-omkeringsbestendigheid

Voorkom reconstructie van private attributen. Recente onderzoeken benadrukken outputtruncatie en DP-garanties als praktische verdedigingsmaatregelen.

 #10.4.1    Niveau: 1    Rol: D
 Verifieer dat gevoelige attributen nooit direct worden weergegeven; gebruik waar nodig buckets of eenrichtingsomzettingen.
 #10.4.2    Niveau: 1    Rol: D/V
 Verifieer dat query-snelheidslimieten herhaalde adaptieve queries van dezelfde hoofdgebruiker beperken.
 #10.4.3    Niveau: 2    Rol: D
 Controleer of het model is getraind met privacybeschermende ruis.

---

### 10.5 Verdediging tegen model-extractie

Detecteer en voorkom ongeautoriseerd klonen. Watermerken en analyse van query-patronen worden aanbevolen.

 #10.5.1    Niveau: 1    Rol: D
 Verifieer dat inferentie-gateways wereldwijde en per-API-sleutel snelheidslimieten afdwingen die zijn afgestemd op de memorisatiedrempel van het model.
 #10.5.2    Niveau: 2    Rol: D/V
 Controleer of query-entropie en input-meervoudigheidsstatistieken een geautomatiseerde extractiedetector voeden.
 #10.5.3    Niveau: 2    Rol: V
 Verifieer dat fragiele of probabilistische watermerken kunnen worden bewezen met p < 0,01 in ≤ 1 000 queries tegen een vermoedelijke kloon.
 #10.5.4    Niveau: 3    Rol: D
 Verifieer dat watermerksleutels en trigger-sets zijn opgeslagen in een hardware-beveiligingsmodule en jaarlijks worden geroteerd.
 #10.5.5    Niveau: 3    Rol: V
 Verifieer dat extraction-alert evenementen de overtredende queries bevatten en geïntegreerd zijn met incident-response draaiboeken.

---

### 10.6 Detectie van Vergiftigde Gegevens tijdens de Inference-tijd

Identificeer en neutraliseer achterdeurs- of vergiftigde invoer.

 #10.6.1    Niveau: 1    Rol: D
 Verifieer dat invoer wordt gecontroleerd door een anomaliedetector (bijv. STRIP, consistentiescorering) voordat het model inferentie uitvoert.
 #10.6.2    Niveau: 1    Rol: V
 Controleer of de detector drempels zijn afgestemd op schone/vervuilde validatiesets om minder dan 5% fout-positieven te bereiken.
 #10.6.3    Niveau: 2    Rol: D
 Controleer of invoer die als vergiftigd wordt gemarkeerd, zachte blokkering en workflows voor menselijke beoordeling activeert.
 #10.6.4    Niveau: 2    Rol: V
 Verifieer dat detectoren worden onderworpen aan stresstests met adaptieve, triggerloze backdoor-aanvallen.
 #10.6.5    Niveau: 3    Rol: D
 Controleer of detectie-efficiëntiemaatstaven worden vastgelegd en periodiek opnieuw worden geëvalueerd met nieuwe dreigingsinformatie.

---

### 10.7 Dynamische aanpassing van het beveiligingsbeleid

Realtime updates van beveiligingsbeleid op basis van dreigingsinformatie en gedragsanalyse.

 #10.7.1    Niveau: 1    Rol: D/V
 Controleer of beveiligingsbeleid dynamisch kan worden bijgewerkt zonder dat de agent opnieuw hoeft te worden gestart, terwijl de integriteit van de beleidsversie behouden blijft.
 #10.7.2    Niveau: 2    Rol: D/V
 Verifieer dat beleidsupdates cryptografisch zijn ondertekend door geautoriseerd beveiligingspersoneel en worden gevalideerd voordat ze worden toegepast.
 #10.7.3    Niveau: 2    Rol: D/V
 Controleer of dynamische beleidswijzigingen worden geregistreerd met volledige audittrails, inclusief rechtvaardiging, goedkeuringsketens en terugdraaiprocedures.
 #10.7.4    Niveau: 3    Rol: D/V
 Controleer of adaptieve beveiligingsmechanismen de gevoeligheid van dreigingsdetectie aanpassen op basis van risicocontext en gedragsinzichten.
 #10.7.5    Niveau: 3    Rol: D/V
 Verifieer dat beleidsaanpassingsbeslissingen verklaarbaar zijn en bewijsstromen bevatten voor beoordeling door het beveiligingsteam.

---

### 10.8 Reflectie-gebaseerde Beveiligingsanalyse

Beveiligingsvalidatie via agent zelfreflectie en metacognitieve analyse.

 #10.8.1    Niveau: 1    Rol: D/V
 Controleer of agentreflectiemechanismen een op beveiliging gerichte zelfbeoordeling van beslissingen en acties omvatten.
 #10.8.2    Niveau: 2    Rol: D/V
 Controleer of reflectie-uitvoer wordt gevalideerd om manipulatie van zelfbeoordelingsmechanismen door vijandige invoer te voorkomen.
 #10.8.3    Niveau: 2    Rol: D/V
 Verifieer dat meta-cognitieve beveiligingsanalyse potentiële vooringenomenheid, manipulatie of compromittering in agentredeneringsprocessen identificeert.
 #10.8.4    Niveau: 3    Rol: D/V
 Verifieer dat op reflectie gebaseerde beveiligingswaarschuwingen geavanceerde monitoring en mogelijke menselijke interventieworkflows activeren.
 #10.8.5    Niveau: 3    Rol: D/V
 Verifieer dat continu leren van beveiligingsreflecties de bedreigingsdetectie verbetert zonder de legitieme functionaliteit te verminderen.

---

### 10.9 Evolutie & Zelfverbeteringsbeveiliging

Beveiligingscontroles voor agentensystemen die in staat zijn tot zelfmodificatie en evolutie.

 #10.9.1    Niveau: 1    Rol: D/V
 Verifieer dat zelfmodificatiecapaciteiten beperkt zijn tot aangewezen veilige gebieden met formele verificatiegrenzen.
 #10.9.2    Niveau: 2    Rol: D/V
 Verifieer dat evolutievoorstellen een veiligheidsbeoordeling ondergaan voordat ze worden geïmplementeerd.
 #10.9.3    Niveau: 2    Rol: D/V
 Verifieer dat zelfverbeteringsmechanismen herstelopties bevatten met integriteitscontrole.
 #10.9.4    Niveau: 3    Rol: D/V
 Verifieer dat meta-learning beveiliging voorkomt dat verbetering algoritmen door tegenstanders worden gemanipuleerd.
 #10.9.5    Niveau: 3    Rol: D/V
 Verifieer dat recursieve zelfverbetering beperkt wordt door formele veiligheidsbeperkingen met mathematische bewijzen van convergentie.

---

#### Referenties

MITRE ATLAS adversary tactics for ML
NIST AI Risk Management Framework 1.0, 2023
OWASP Top 10 for LLM Applications, 2025
Adversarial Training: A Survey — Zhao et al., 2024
RobustBench adversarial-robustness benchmark
Membership-Inference & Model-Inversion Risk Survey, 2025
PURIFIER: Confidence-Score Defense against MI Attacks — AAAI 2023
Model-Inversion Attacks & Defenses Survey — AI Review, 2025
Comprehensive Defense Framework Against Model Extraction — IEEE TDSC 2024
Fragile Model Watermarking Survey — 2025
Data Poisoning in Deep Learning: A Survey — Zhao et al., 2025
BDetCLIP: Multimodal Prompting Backdoor Detection — Niu et al., 2024

## 11 Privacybescherming & Beheer van Persoonsgegevens

### Beheersingsdoelstelling

Handhaaf strikte privacygaranties gedurende de volledige AI-levenscyclus—verzameling, training, inferentie en incidentrespons—zodat persoonlijke gegevens alleen worden verwerkt met duidelijke toestemming, minimaal noodzakelijke reikwijdte, aantoonbare verwijdering en formele privacygaranties.

---

### 11.1 Anonimisering & Gegevensminimalisatie

 #11.1.1    Niveau: 1    Rol: D/V
 Controleer of directe en quasi-identifiers zijn verwijderd of gehasht.
 #11.1.2    Niveau: 2    Rol: D/V
 Controleer of geautomatiseerde controles k-anonimiteit/l-diversiteit meten en een waarschuwing geven wanneer de drempels onder het beleid zakken.
 #11.1.3    Niveau: 2    Rol: V
 Controleer of de modelkenmerk-belangrapporten aantonen dat er geen identifier-lek is met een mutual information groter dan ε = 0.01.
 #11.1.4    Niveau: 3    Rol: V
 Controleer of formele bewijzen of certificering met synthetische data aantonen dat het risico op heridentificatie ≤ 0,05 is, zelfs onder koppelaanvallen.

---

### 11.2 Recht om te worden vergeten & Verwijderingshandhaving

 #11.2.1    Niveau: 1    Rol: D/V
 Verifieer dat verzoeken tot verwijdering van gegevenssubjecten worden doorgevoerd naar ruwe datasets, checkpoints, embeddings, logboeken en back-ups binnen service level agreements van minder dan 30 dagen.
 #11.2.2    Niveau: 2    Rol: D
 Verifieer of "machine-unlearning" routines fysiek opnieuw trainen of benaderde verwijdering uitvoeren met behulp van gecertificeerde unlearning-algoritmen.
 #11.2.3    Niveau: 2    Rol: V
 Controleer of de evaluatie met shadow-modellen aantoont dat vergeten records minder dan 1% van de outputs beïnvloeden na unlearning.
 #11.2.4    Niveau: 3    Rol: V
 Verifieer dat verwijderingsgebeurtenissen onveranderlijk worden vastgelegd en controleerbaar zijn voor toezichthouders.

---

### 11.3 Differentie-Privacy Beschermingsmaatregelen

 #11.3.1    Niveau: 2    Rol: D/V
 Controleer of privacy-verliesboekhoudingsdashboards een waarschuwing geven wanneer de cumulatieve ε de beleidsdrempels overschrijdt.
 #11.3.2    Niveau: 2    Rol: V
 Verifieer dat black-box privacy audits ε̂ binnen 10% van de verklaarde waarde schatten.
 #11.3.3    Niveau: 3    Rol: V
 Verifieer dat formele bewijzen alle post-training fine-tunes en embeddings dekken.

---

### 11.4 Doelbeperking & Bescherming tegen Scope Creep

 #11.4.1    Niveau: 1    Rol: D
 Controleer of elke dataset en modelcheckpoint een machine-leesbare doel tag bevat die overeenkomt met de oorspronkelijke toestemming.
 #11.4.2    Niveau: 1    Rol: D/V
 Verifieer dat runtime-monitoren queries detecteren die niet overeenstemmen met het verklaarde doel en een zachte weigering veroorzaken.
 #11.4.3    Niveau: 3    Rol: D
 Controleer of policy-as-code poorten de heruitrol van modellen naar nieuwe domeinen blokkeren zonder DPIA-beoordeling.
 #11.4.4    Niveau: 3    Rol: V
 Controleer of formele traceerbaarheidsbewijzen aantonen dat elke levenscyclus van persoonsgegevens binnen de geconsenteerde reikwijdte blijft.

---

### 11.5 Toestemmingsbeheer & Wettige-Grondslag Tracking

 #11.5.1    Niveau: 1    Rol: D/V
 Controleer of een Consent-Management Platform (CMP) de opt-in status, het doel en de bewaartermijn per gegevenssubject registreert.
 #11.5.2    Niveau: 2    Rol: D
 Verifieer dat API's toestemmings tokens blootstellen; modellen moeten de token scope valideren voordat ze inferentie uitvoeren.
 #11.5.3    Niveau: 2    Rol: D/V
 Verifieer dat geweigerde of ingetrokken toestemming de verwerkingspijplijnen binnen 24 uur stopzet.

---

### 11.6 Gefedereerd leren met privacycontroles

 #11.6.1    Niveau: 1    Rol: D
 Verifieer dat clientupdates lokale differentiële privacy ruis toevoegen voordat ze worden geaggregeerd.
 #11.6.2    Niveau: 2    Rol: D/V
 Verifieer dat trainingsstatistieken differentieel privé zijn en nooit het verlies van een enkele cliënt onthullen.
 #11.6.3    Niveau: 2    Rol: V
 Controleer of vergiftigingsbestendige aggregatie (bijv. Krum/Trimmed-Mean) is ingeschakeld.
 #11.6.4    Niveau: 3    Rol: V
 Controleer of formele bewijzen het totale ε-budget aantonen met minder dan 5 nutverlies.

---

#### Referenties

GDPR & AI Compliance Best Practices
EU Parliament Study on GDPR & AI, 2020
ISO 31700-1:2023 — Privacy by Design for Consumer Products
NIST Privacy Framework 1.1 (2025 Draft)
Machine Unlearning: Right-to-Be-Forgotten Techniques
A Survey of Machine Unlearning, 2024
Auditing DP-SGD — ArXiv 2024
DP-SGD Explained — PyTorch Blog
Purpose-Limitation for AI — IJLIT 2025
Data-Protection Considerations for AI — URM Consulting
Top Consent-Management Platforms, 2025
Secure Aggregation in DP Federated Learning — ArXiv 2024

## C12 Monitoring, Logging & Anomaliedetectie

### Beheersingsdoelstelling

Deze sectie bevat eisen voor het leveren van realtime en forensische zichtbaarheid in wat het model en andere AI-componenten zien, doen en retourneren, zodat bedreigingen kunnen worden gedetecteerd, geprioriteerd en hiervan geleerd kan worden.

### C12.1 Aanvraag- enantwoordlogboekregistratie

 #12.1.1    Niveau: 1    Rol: D/V
 Verifieer dat alle gebruikersprompts en modelantwoorden worden geregistreerd met de juiste metadata (bijv. tijdstempel, gebruikers-ID, sessie-ID, modelversie).
 #12.1.2    Niveau: 1    Rol: D/V
 Verifieer dat logs worden opgeslagen in beveiligde, toegang-gecontroleerde repositories met geschikte bewaarbeleid en back-upprocedures.
 #12.1.3    Niveau: 1    Rol: D/V
 Controleer of logopslagsystemen encryptie toepassen voor gegevens in rust en tijdens overdracht om gevoelige informatie in de logs te beschermen.
 #12.1.4    Niveau: 1    Rol: D/V
 Verifieer dat gevoelige gegevens in prompts en outputs automatisch worden doorgestreept of afgeschermd voordat ze worden gelogd, met configureerbare regels voor het afschermen van PII, inloggegevens en eigendomsinformatie.
 #12.1.5    Niveau: 2    Rol: D/V
 Verifieer dat beleidsbeslissingen en veiligheidsfilteracties met voldoende detail worden vastgelegd om audit en debugging van contentmoderatiesystemen mogelijk te maken.
 #12.1.6    Niveau: 2    Rol: D/V
 Controleer of de logintegriteit wordt beschermd door bijvoorbeeld cryptografische handtekeningen of alleen-schrijven opslag.

---

### C12.2 Misbruikdetectie en waarschuwingen

 #12.2.1    Niveau: 1    Rol: D/V
 Controleer of het systeem bekende jailbreak-patronen, pogingen tot promptinjectie en vijandige invoer detecteert en waarschuwingen geeft met behulp van handtekeninggebaseerde detectie.
 #12.2.2    Niveau: 1    Rol: D/V
 Controleer of het systeem integreert met bestaande Security Information and Event Management (SIEM)-platforms met gebruik van standaard logformaten en protocollen.
 #12.2.3    Niveau: 2    Rol: D/V
 Controleer of verrijkte beveiligingsgebeurtenissen AI-specifieke context bevatten, zoals modelidentificaties, betrouwbaarheidscores en beslissingen van veiligheidsfilters.
 #12.2.4    Niveau: 2    Rol: D/V
 Controleer of gedragsafwijkingsdetectie ongebruikelijke gespreks­patronen, overmatige pogingen tot herhaling of systematische onderzoeks­gedragingen identificeert.
 #12.2.5    Niveau: 2    Rol: D/V
 Controleer of realtime waarschuwingsmechanismen beveiligingsteams op de hoogte stellen wanneer mogelijke beleidschendingen of aanvalspogingen worden gedetecteerd.
 #12.2.6    Niveau: 2    Rol: D/V
 Verifieer dat aangepaste regels zijn opgenomen om AI-specifieke dreigingspatronen te detecteren, waaronder gecoördineerde jailbreakpogingen, promptinjectiecampagnes en modelextractie-aanvallen.
 #12.2.7    Niveau: 3    Rol: D/V
 Controleer of geautomatiseerde incidentreactieworkflows in staat zijn om gecompromitteerde modellen te isoleren, kwaadaardige gebruikers te blokkeren en kritieke beveiligingsincidenten te escaleren.

---

### C12.3 Detectie van Modelafwijking

 #12.3.1    Niveau: 1    Rol: D/V
 Controleer of het systeem basisprestatie-indicatoren bijhoudt, zoals nauwkeurigheid, betrouwbaarheidswaarden, latentie en foutpercentages over verschillende modelversies en tijdsperioden.
 #12.3.2    Niveau: 2    Rol: D/V
 Controleer of geautomatiseerde waarschuwingen worden geactiveerd wanneer prestatiestatistieken vooraf gedefinieerde degradatiedrempels overschrijden of aanzienlijk afwijken van baselines.
 #12.3.3    Niveau: 2    Rol: D/V
 Controleer of de monitors voor hallucinatie-detectie gevallen identificeren en markeren wanneer modeluitvoer feitelijk onjuiste, inconsistente of verzonnen informatie bevat.

---

### C12.4 Prestaties & Gedrags-Telemetrie

 #12.4.1    Niveau: 1    Rol: D/V
 Verifieer dat operationele metrics zoals verzoeklatentie, tokenverbruik, geheugengebruik en doorvoersnelheid continu worden verzameld en gemonitord.
 #12.4.2    Niveau: 1    Rol: D/V
 Verifieer dat succes- en faalpercentages worden bijgehouden met categorisering van fouttypes en hun oorzaken.
 #12.4.3    Niveau: 2    Rol: D/V
 Controleer of het monitoren van resourcegebruik GPU-/CPU-gebruik, geheugengebruik en opslagvereisten omvat, met waarschuwingen bij het overschrijden van drempelwaarden.

---

### C12.5 AI-incidentresponsplanning & uitvoering

 #12.5.1    Niveau: 1    Rol: D/V
 Controleer of incidentresponsplannen specifiek AI-gerelateerde beveiligingsincidenten behandelen, zoals modelcompromittering, datavervuiling en adversariële aanvallen.
 #12.5.2    Niveau: 2    Rol: D/V
 Controleer of de incidentrespons-teams toegang hebben tot AI-specifieke forensische tools en expertise om modelgedrag en aanvalspatronen te onderzoeken.
 #12.5.3    Niveau: 3    Rol: D/V
 Controleer of de analyse na het incident rekening houdt met modelhertraining, updates van veiligheidsfilters en de integratie van geleerde lessen in beveiligingsmaatregelen.

---

### C12.5 Detectie van prestatieverslechtering van AI

Bewaken en detecteren van achteruitgang in de prestaties en kwaliteit van AI-modellen in de loop van de tijd.

 #12.5.1    Niveau: 1    Rol: D/V
 Controleer of de nauwkeurigheid, precisie, recall en F1-scores van het model continu worden gemonitord en vergeleken met de basisdrempels.
 #12.5.2    Niveau: 1    Rol: D/V
 Bevestig dat data drift-detectie veranderingen in de inputverdeling bewaakt die de modelprestaties kunnen beïnvloeden.
 #12.5.3    Niveau: 2    Rol: D/V
 Controleer of concept drift-detectie veranderingen in de relatie tussen invoer en verwachte uitvoer detecteert.
 #12.5.4    Niveau: 2    Rol: D/V
 Verifieer dat prestatieverval geautomatiseerde waarschuwingen activeert en workflows voor het opnieuw trainen of vervangen van het model start.
 #12.5.5    Niveau: 3    Rol: V
 Verifieer dat de oorzaak-analyse van degradatie prestatieverminderingen correleert met veranderingen in gegevens, infrastructuurproblemen of externe factoren.

---

### C12.6 DAG Visualisatie & Workflow Beveiliging

Bescherm workflowvisualisatiesystemen tegen informatielekken en manipulatie-aanvallen.

 #12.6.1    Niveau: 1    Rol: D/V
 Controleer of de gegevens voor DAG-visualisatie worden gesanitiseerd om gevoelige informatie te verwijderen voordat ze worden opgeslagen of verzonden.
 #12.6.2    Niveau: 1    Rol: D/V
 Controleer of de toegangscontroles voor workflowvisualisatie garanderen dat alleen geautoriseerde gebruikers de beslissingspaden van agenten en redeneersporen kunnen bekijken.
 #12.6.3    Niveau: 2    Rol: D/V
 Verifieer dat de integriteit van DAG-gegevens wordt beschermd door cryptografische handtekeningen en manipulatiebestendige opslagmechanismen.
 #12.6.4    Niveau: 2    Rol: D/V
 Verifieer dat workflowvisualisatiesystemen invoervalidatie implementeren om injectie-aanvallen via speciaal vervaardigde knoop- of randgegevens te voorkomen.
 #12.6.5    Niveau: 3    Rol: D/V
 Verifieer dat realtime DAG-updates worden gereguleerd qua snelheid en gevalideerd om denial-of-service-aanvallen op visualisatiesystemen te voorkomen.

---

### C12.7 Proactieve monitoring van beveiligingsgedrag

Detectie en preventie van beveiligingsdreigingen door middel van proactieve analyse van agentgedrag.

 #12.7.1    Niveau: 1    Rol: D/V
 Verifieer dat proactieve agentgedragingen worden beveiligingsgevalideerd voordat ze worden uitgevoerd, met integratie van risicobeoordeling.
 #12.7.2    Niveau: 2    Rol: D/V
 Verifieer dat autonome initiatieftriggers beveiligingscontextevaluatie en beoordeling van het dreigingslandschap omvatten.
 #12.7.3    Niveau: 2    Rol: D/V
 Controleer of proactieve gedrags- patronen worden geanalyseerd op mogelijke beveiligingsimplicaties en onbedoelde gevolgen.
 #12.7.4    Niveau: 3    Rol: D/V
 Verifieer dat beveiligingskritieke proactieve acties expliciete goedkeuringsketens vereisen met auditsporen.
 #12.7.5    Niveau: 3    Rol: D/V
 Verifieer dat gedragsafwijkingsdetectie afwijkingen in proactieve agentpatronen identificeert die op compromittering kunnen duiden.

---

### Referenties

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Menselijk Toezicht, Verantwoordingsplicht & Bestuur

### Beheersingsdoelstelling

Dit hoofdstuk bevat vereisten voor het behouden van menselijke controle en duidelijke verantwoordingsketens in AI-systemen, waarbij uitlegbaarheid, transparantie en ethisch beheer tijdens de hele AI-levenscyclus worden gewaarborgd.

---

### C13.1 Noodstop- & Override-Mechanismen

Bied uitschakel- of terugdraaiopties aan wanneer onveilig gedrag van het AI-systeem wordt waargenomen.

 #13.1.1    Niveau: 1    Rol: D/V
 Controleer of er een handmatig noodstopmechanisme aanwezig is om de AI-modelinferenzie en uitvoer onmiddellijk te stoppen.
 #13.1.2    Niveau: 1    Rol: D
 Controleer of override-voorzieningen alleen toegankelijk zijn voor geautoriseerd personeel.
 #13.1.3    Niveau: 3    Rol: D/V
 Controleer of rollback-procedures kunnen terugkeren naar eerdere modelversies of veilige-modusoperaties.
 #13.1.4    Niveau: 3    Rol: V
 Controleer of override-mechanismen regelmatig worden getest.

---

### C13.2 Beslispunten met Mens-in-de-Lus

Vereis menselijke goedkeuringen wanneer de inzetten vooraf gedefinieerde risicodrempels overschrijden.

 #13.2.1    Niveau: 1    Rol: D/V
 Verifieer dat AI-beslissingen met hoog risico expliciete menselijke goedkeuring vereisen voordat ze worden uitgevoerd.
 #13.2.2    Niveau: 1    Rol: D
 Controleer of risicodrempels duidelijk zijn gedefinieerd en automatisch menselijke beoordelingsworkflows activeren.
 #13.2.3    Niveau: 2    Rol: D
 Verifieer dat tijdgevoelige beslissingen noodprocedures hebben wanneer menselijke goedkeuring niet binnen de vereiste tijdsbestekken kan worden verkregen.
 #13.2.4    Niveau: 3    Rol: D/V
 Controleer of escalatieprocedures duidelijke bevoegdheidsniveaus vastleggen voor verschillende besluitvormingscategorieën of risicocategorieën, indien van toepassing.

---

### C13.3 Keten van Verantwoordelijkheid & Controleerbaarheid

Log operatoracties en modelbeslissingen.

 #13.3.1    Niveau: 1    Rol: D/V
 Controleer of alle beslissingen van het AI-systeem en menselijke interventies worden geregistreerd met tijdstempels, gebruikersidentiteiten en de reden van de beslissing.
 #13.3.2    Niveau: 2    Rol: D
 Controleer of auditlogs niet kunnen worden aangepast en of er mechanismen voor integriteitsverificatie zijn opgenomen.

---

### C13.4 Uitlegbare-AI Technieken

Belang van oppervlaktekenmerken, tegenfeitelijke voorbeelden en lokale verklaringen.

 #13.4.1    Niveau: 1    Rol: D/V
 Controleer of AI-systemen basisuitleg geven voor hun beslissingen in een voor mensen leesbaar formaat.
 #13.4.2    Niveau: 2    Rol: V
 Verifieer dat de kwaliteit van de uitleg wordt gevalideerd door middel van menselijke evaluatiestudies en -metingen.
 #13.4.3    Niveau: 3    Rol: D/V
 Verifieer dat scores voor feature-importance of attributiemethoden (SHAP, LIME, enz.) beschikbaar zijn voor kritieke beslissingen.
 #13.4.4    Niveau: 3    Rol: V
 Controleer of contra-feitelijke verklaringen laten zien hoe invoer kan worden aangepast om resultaten te wijzigen, indien van toepassing op de use-case en het domein.

---

### C13.5 Modelkaarten & Gebruiksverklaringen

Onderhoud modelkaarten voor beoogd gebruik, prestatiemaatstaven en ethische overwegingen.

 #13.5.1    Niveau: 1    Rol: D
 Controleer of modelkaarten de beoogde gebruikssituaties, beperkingen en bekende faalmodi documenteren.
 #13.5.2    Niveau: 1    Rol: D/V
 Verifieer dat prestatie-indicatoren voor verschillende toepasselijke gebruiksscenario's worden bekendgemaakt.
 #13.5.3    Niveau: 2    Rol: D
 Verifieer dat ethische overwegingen, bias-beoordelingen, eerlijkheidsevaluaties, kenmerken van trainingsgegevens en bekende beperkingen van trainingsgegevens gedocumenteerd en regelmatig bijgewerkt worden.
 #13.5.4    Niveau: 2    Rol: D/V
 Controleer of modelkaarten versiebeheerd zijn en gedurende de gehele levenscyclus van het model worden onderhouden met wijzigingsregistratie.

---

### C13.6 Kwantificering van onzekerheid

Verspreid betrouwbaarheidscores of entropiematen in antwoorden.

 #13.6.1    Niveau: 1    Rol: D
 Controleer of AI-systemen betrouwbaarheidscores of onzekerheidsmaten bij hun output leveren.
 #13.6.2    Niveau: 2    Rol: D/V
 Controleer of onzekerheidsdrempels extra menselijke beoordeling of alternatieve besluitvormingspaden activeren.
 #13.6.3    Niveau: 2    Rol: V
 Controleer of methoden voor onzekerheidskwantificatie zijn gekalibreerd en gevalideerd aan de hand van grondwaarheidsgegevens.
 #13.6.4    Niveau: 3    Rol: D/V
 Verifieer dat onzekerheidspropagatie behouden blijft door multi-stap AI-werkstromen.

---

### C13.7 Transparantieverslagen voor gebruikers

Geef periodieke openbaarmakingen over incidenten, afwijkingen en datagebruik.

 #13.7.1    Niveau: 1    Rol: D/V
 Controleer of het gebruik van gegevensbeleid en praktijken voor het beheren van gebruikersconsent duidelijk worden gecommuniceerd aan belanghebbenden.
 #13.7.2    Niveau: 2    Rol: D/V
 Verifieer dat AI-impactbeoordelingen worden uitgevoerd en dat de resultaten worden opgenomen in de rapportage.
 #13.7.3    Niveau: 2    Rol: D/V
 Controleer of transparantierapporten die regelmatig worden gepubliceerd, AI-incidenten en operationele statistieken in redelijke mate van detail bekendmaken.

#### Referenties

EU Artificial Intelligence Act — Regulation (EU) 2024/1689 (Official Journal, 12 July 2024)
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
ISO/IEC 42001:2023 — AI Management Systems Requirements
NIST AI Risk Management Framework 1.0
NIST SP 800-53 Revision 5 — Security and Privacy Controls
A Unified Approach to Interpreting Model Predictions (SHAP, ICML 2017)
Model Cards for Model Reporting (Mitchell et al., 2018)
Dropout as a Bayesian Approximation: Representing Model Uncertainty in Deep Learning (Gal & Ghahramani, 2016)
ISO/IEC 24029-2:2023 — Robustness of Neural Networks — Methodology for Formal Methods
IEEE 7001-2021 — Transparency of Autonomous Systems
GDPR — Article 5 "Transparency Principle" (Regulation (EU) 2016/679)
Human Oversight under Article 14 of the EU AI Act (Fink, 2025)

## Bijlage A: Woordenlijst

Deze uitgebreide woordenlijst geeft definities van belangrijke AI-, ML- en beveiligingstermen die door de hele AISVS worden gebruikt om duidelijkheid en een gemeenschappelijk begrip te waarborgen.

Adversariële Voorbeeld: Een invoer die opzettelijk is gemaakt om een AI-model een fout te laten maken, vaak door subtiele verstoringen toe te voegen die voor mensen onwaarneembaar zijn.
​
Aanvallingsbestendigheid – Aanvallingsbestendigheid in AI verwijst naar het vermogen van een model om zijn prestaties te behouden en weerstand te bieden tegen opzettelijk vervaardigde, kwaadaardige invoer die is ontworpen om fouten te veroorzaken.
​
Agent – AI-agenten zijn softwaresystemen die AI gebruiken om doelen na te streven en taken uit te voeren namens gebruikers. Ze tonen redeneervermogen, planning en geheugen en hebben een mate van autonomie om beslissingen te nemen, te leren en zich aan te passen.
​
Agentische AI: AI-systemen die met een zekere mate van autonomie kunnen functioneren om doelen te bereiken, waarbij ze vaak beslissingen nemen en acties uitvoeren zonder directe menselijke tussenkomst.
​
Attribute-Based Access Control (ABAC): Een toegangscontroleparadigma waarbij autorisatiebeslissingen worden genomen op basis van attributen van de gebruiker, resource, actie en omgeving, die tijdens de querytijd worden geëvalueerd.
​
Backdoor-aanval: Een type datavervuilingsaanval waarbij het model wordt getraind om op een specifieke manier te reageren op bepaalde triggers, terwijl het zich anders normaal gedraagt.
​
Bias: Systematische fouten in AI-modeluitvoer die kunnen leiden tot oneerlijke of discriminerende uitkomsten voor bepaalde groepen of in specifieke contexten.
​
Bias Exploitatie: Een aanvalstechniek die gebruikmaakt van bekende vooroordelen in AI-modellen om outputs of uitkomsten te manipuleren.
​
Cedar: Amazons beleids- en uitvoeringssysteem voor fijnmazige toestemmingen, gebruikt bij de implementatie van ABAC voor AI-systemen.
​
Chain of Thought: Een techniek om het redeneren in taalmodellen te verbeteren door tussentijdse redeneringsstappen te genereren voordat een definitief antwoord wordt gegeven.
​
Circuit Breakers: Mechanismen die automatisch de werking van AI-systemen stoppen wanneer specifieke risicodrempels worden overschreden.
​
Gegevenslek: Onbedoelde blootstelling van gevoelige informatie via AI-modeluitvoer of gedrag.
​
Datavergiftiging: Het opzettelijk corrumperen van trainingsgegevens om de integriteit van het model aan te tasten, vaak om achterdeurtjes te installeren of de prestaties te verslechteren.
​
Differentiële privacy – Differentiële privacy is een mathematisch rigoureus kader voor het vrijgeven van statistische informatie over datasets, terwijl de privacy van individuele gegevenssubjecten wordt beschermd. Het stelt een gegevenshouder in staat om geaggregeerde patronen van de groep te delen, terwijl de informatie die over specifieke individuen wordt gelekt, wordt beperkt.
​
Embeddings: Dichte vectorrepresentaties van gegevens (tekst, afbeeldingen, enz.) die semantische betekenis vastleggen in een hoog-dimensionale ruimte.
​
Uitlegbaarheid – Uitlegbaarheid in AI is het vermogen van een AI-systeem om voor mensen begrijpelijke redenen te geven voor zijn beslissingen en voorspellingen, waarbij inzicht wordt geboden in de interne werking ervan.
​
Explainable AI (XAI): AI-systemen die ontworpen zijn om begrijpelijke uitleg te geven aan mensen over hun beslissingen en gedragingen via verschillende technieken en raamwerken.
​
Federated Learning: Een machine learning-benadering waarbij modellen worden getraind op meerdere gedecentraliseerde apparaten die lokale datasets bevatten, zonder dat de data zelf wordt uitgewisseld.
​
Beschermingsmaatregelen: Beperkingen geïmplementeerd om te voorkomen dat AI-systemen schadelijke, bevooroordeelde of anderszins ongewenste output produceren.
​
Hallucinatie – Een AI-hallucinatie verwijst naar een fenomeen waarbij een AI-model onjuiste of misleidende informatie genereert die niet is gebaseerd op zijn trainingsgegevens of feitelijke realiteit.
​
Human-in-the-Loop (HITL): Systemen die zijn ontworpen om menselijke controle, verificatie of interventie te vereisen op cruciale beslissingsmomenten.
​
Infrastructure als Code (IaC): Beheren en leveren van infrastructuur via code in plaats van handmatige processen, wat beveiligingsscans en consistente implementaties mogelijk maakt.
​
Jailbreak: Technieken die worden gebruikt om veiligheidsmaatregelen in AI-systemen, met name in grote taalmodellen, te omzeilen om verboden inhoud te produceren.
​
Minimale rechten: Het beveiligingsprincipe waarbij slechts de minimaal noodzakelijke toegangsrechten worden toegekend aan gebruikers en processen.
​
LIME (Local Interpretable Model-agnostic Explanations): Een techniek om de voorspellingen van elke machine learning-classificator uit te leggen door deze lokaal te benaderen met een interpreteerbaar model.
​
Lidmaatschapsinference-aanval: een aanval die tot doel heeft te bepalen of een specifiek gegevenspunt is gebruikt om een machine learning-model te trainen.
​
MITRE ATLAS: Adversarial Threat Landscape voor kunstmatige-intelligentiesystemen; een kennisbank van adversariële tactieken en technieken tegen AI-systemen.
​
Modelkaart – Een modelkaart is een document dat gestandaardiseerde informatie biedt over de prestaties, beperkingen, beoogde toepassingen en ethische overwegingen van een AI-model om transparantie en verantwoordelijke AI-ontwikkeling te bevorderen.
​
Model Extractie: Een aanval waarbij een aanvaller herhaaldelijk een doelmodel bevraagt om zonder toestemming een functioneel vergelijkbare kopie te maken.
​
Modelinversie: Een aanval die probeert trainingsdata te reconstrueren door modeluitvoer te analyseren.
​
Modellevenscyclusbeheer – AI Modellevenscyclusbeheer is het proces van het toezicht houden op alle fasen van het bestaan van een AI-model, inclusief het ontwerp, de ontwikkeling, de implementatie, het monitoren, het onderhoud en het uiteindelijke buiten gebruik stellen, om ervoor te zorgen dat het effectief blijft en in lijn is met de doelstellingen.
​
Modelvergiftiging: Het direct introduceren van kwetsbaarheden of achterdeurtjes in een model tijdens het trainingsproces.
​
Modeldiefstal: Het extraheren van een kopie of benadering van een propriëtair model door herhaalde queries.
​
Multi-agent System: Een systeem samengesteld uit meerdere interactieve AI-agenten, elk met mogelijk verschillende capaciteiten en doelen.
​
OPA (Open Policy Agent): Een open-source beleids-engine die uniforme handhaving van beleid over de hele stack mogelijk maakt.
​
Privacy-behoudende Machine Learning (PPML): Technieken en methoden om ML-modellen te trainen en implementeren terwijl de privacy van de trainingsgegevens wordt beschermd.
​
Promptinjectie: Een aanval waarbij kwaadaardige instructies in invoer worden ingebed om het bedoelde gedrag van een model te overschrijven.
​
RAG (Retrieval-Augmented Generation): Een techniek die grote taalmodellen verbetert door relevante informatie op te halen uit externe kennisbronnen voordat een antwoord wordt gegenereerd.
​
Red-Teaming: De praktijk van het actief testen van AI-systemen door het simuleren van adversariële aanvallen om kwetsbaarheden te identificeren.
​
SBOM (Software Bill of Materials): Een formeel verslag met de details en toeleveringsketenrelaties van verschillende componenten die worden gebruikt bij het bouwen van software of AI-modellen.
​
SHAP (SHapley Additive exPlanations): Een speltheoretische benadering om de output van elk machine learning-model uit te leggen door de bijdrage van elke eigenschap aan de voorspelling te berekenen.
​
Supply Chain-aanval: Een systeem compromitteren door zich te richten op minder beveiligde elementen in de toeleveringsketen, zoals bibliotheken van derden, datasets of vooraf getrainde modellen.
​
Transfer Learning: Een techniek waarbij een model dat is ontwikkeld voor één taak wordt hergebruikt als uitgangspunt voor een model voor een tweede taak.
​
Vector Database: Een gespecialiseerde database ontworpen om hoog-dimensionale vectoren (embeddings) op te slaan en efficiënte gelijkeniszoektochten uit te voeren.
​
Kwetsbaarheidsscanning: Geautomatiseerde tools die bekende beveiligingskwetsbaarheden in softwarecomponenten identificeren, inclusief AI-frameworks en afhankelijkheden.
​
Watermarking: Technieken om onzichtbare markers in AI-gegenereerde inhoud in te bedden om de oorsprong te traceren of AI-generatie te detecteren.
​
Zero-Day kwetsbaarheid: Een eerder onbekende kwetsbaarheid die aanvallers kunnen benutten voordat ontwikkelaars een patch maken en implementeren.

## Bijlage B: Referenties

### TODO

## Appendix C: Beheer en documentatie van AI-beveiliging

### Doelstelling

Deze bijlage bevat basisvereisten voor het opzetten van organisatiestructuren, beleidslijnen en processen om AI-beveiliging te beheersen gedurende de hele systeemlevenscyclus.

---

### AC.1 Adoptie van het AI Risicobeheerraamwerk

Bied een formeel raamwerk om AI-specifieke risico's te identificeren, beoordelen en verminderen gedurende de gehele systeemlevenscyclus.

 #AC.1.1    Niveau: 1    Rol: D/V
 Verifieer of een AI-specifieke risico-beoordelingsmethodologie is gedocumenteerd en geïmplementeerd.
 #AC.1.2    Niveau: 2    Rol: D
 Controleer of risicobeoordelingen worden uitgevoerd op belangrijke momenten in de AI-levenscyclus en vóór belangrijke wijzigingen.
 #AC.1.3    Niveau: 3    Rol: D/V
 Verifieer of het risicobeheerframework overeenkomt met de vastgestelde normen (bijv. NIST AI RMF).

---

### AC.2 AI-beveiligingsbeleid en procedures

Definieer en handhaaf organisatorische normen voor veilige ontwikkeling, implementatie en werking van AI.

 #AC.2.1    Niveau: 1    Rol: D/V
 Verifieer of er gedocumenteerde AI-beveiligingsbeleid bestaan.
 #AC.2.2    Niveau: 2    Rol: D
 Controleer of het beleid ten minste jaarlijks en na significante veranderingen in het dreigingslandschap wordt herzien en bijgewerkt.
 #AC.2.3    Niveau: 3    Rol: D/V
 Controleer of beleidslijnen alle AISVS-categorieën en toepasselijke wettelijke vereisten behandelen.

---

### AC.3 Rollen & Verantwoordelijkheden voor AI-beveiliging

Stel duidelijke verantwoordelijkheden vast voor AI-beveiliging binnen de organisatie.

 #AC.3.1    Niveau: 1    Rol: D/V
 Controleer of AI-beveiligingsrollen en verantwoordelijkheden zijn gedocumenteerd.
 #AC.3.2    Niveau: 2    Rol: D
 Verifieer of verantwoordelijke personen over de juiste beveiligingskennis beschikken.
 #AC.3.3    Niveau: 3    Rol: D/V
 Verifieer of er een AI-ethiekcommissie of bestuursraad voor governance is ingesteld voor AI-systemen met hoog risico.

---

### AC.4 Handhaving van ethische AI-richtlijnen

Zorg ervoor dat AI-systemen opereren volgens vastgestelde ethische principes.

 #AC.4.1    Niveau: 1    Rol: D/V
 Verifieer of ethische richtlijnen voor de ontwikkeling en implementatie van AI bestaan.
 #AC.4.2    Niveau: 2    Rol: D
 Verifieer of er mechanismen aanwezig zijn om ethische schendingen te detecteren en te rapporteren.
 #AC.4.3    Niveau: 3    Rol: D/V
 Verifieer dat regelmatige ethische beoordelingen van geïmplementeerde AI-systemen worden uitgevoerd.

---

### AC.5 AI-regelgevings- nalevingsmonitoring

Houd bewustzijn van en naleving van de zich ontwikkelende AI-regelgeving aan.

 #AC.5.1    Niveau: 1    Rol: D/V
 Verifieer dat er processen bestaan om toepasselijke AI-regelgeving te identificeren.
 #AC.5.2    Niveau: 2    Rol: D
 Controleer of wordt beoordeeld of aan alle wettelijke vereisten wordt voldaan.
 #AC.5.3    Niveau: 3    Rol: D/V
 Verifieer dat regelgevende wijzigingen tijdige beoordelingen en updates van AI-systemen activeren.

### AC.6 Training Data Governance, Documentatie en Proces

 #1.1.2    Niveau: 1    Rol: D/V
 Verifieer dat alleen datasets die zijn getoetst op kwaliteit, representativiteit, ethische herkomst en licentiecompliance zijn toegestaan, waardoor de risico's van vergiftiging, ingebedde vooringenomenheid en inbreuk op intellectueel eigendom worden verminderd.
 #1.1.5    Niveau: 2    Rol: D/V
 Verifieer dat de kwaliteit van labeling/annotatie wordt gegarandeerd door middel van kruiscontroles of consensus van beoordelaars.
 #1.1.6    Niveau: 2    Rol: D/V
 Controleer of er "datakaarten" of "datasheets voor datasets" worden bijgehouden voor belangrijke trainingsdatasets, waarin kenmerken, motivaties, samenstelling, verzamelingsprocessen, voorbewerking en aanbevolen/afgeraden toepassingen worden beschreven.
 #1.3.2    Niveau: 2    Rol: D/V
 Verifieer dat de geïdentificeerde vooroordelen worden tegengegaan via gedocumenteerde strategieën zoals het opnieuw balanceren, gerichte data-augmentatie, algoritmische aanpassingen (bijv. pre-processing, in-processing, post-processing technieken) of het herwegen, en dat de impact van deze mitigatie zowel op eerlijkheid als op de algehele modelprestaties wordt beoordeeld.
 #1.3.3    Niveau: 2    Rol: D/V
 Verzeker dat post-training eerlijkheidsmetriek worden geëvalueerd en gedocumenteerd.
 #1.3.4    Niveau: 3    Rol: D/V
 Verifieer dat een beleid voor het beheren van levenscyclus-bias eigenaren toewijst en een beoordelingsfrequentie bepaalt.
 #1.4.1    Niveau: 2    Rol: D/V
 Verifieer dat de kwaliteit van labeling/annotatie wordt gewaarborgd via duidelijke richtlijnen, controle door meerdere beoordelaars, consensusmechanismen (bijv. het monitoren van overeenstemming tussen annotators) en gedefinieerde processen voor het oplossen van discrepanties.
 #1.4.4    Niveau: 3    Rol: D/V
 Zorg ervoor dat labels die cruciaal zijn voor veiligheid, beveiliging of eerlijkheid (bijv. het identificeren van toxische inhoud, kritieke medische bevindingen) een verplichte onafhankelijke dubbele beoordeling of gelijkwaardige robuuste verificatie ondergaan.
 #1.4.6    Niveau: 2    Rol: D/V
 Verifieer dat labelrichtlijnen en instructies uitgebreid, versiebeheer zijn en door collega's zijn beoordeeld.
 #1.4.6    Niveau: 2    Rol: D/V
 Controleer of dataschema's voor labels duidelijk zijn gedefinieerd en versiebeheer hebben.
 #1.3.1    Niveau: 1    Rol: D/V
 Verifieer dat datasets zijn geprofileerd op representatieve onevenwichtigheid en potentiële bias over wettelijk beschermde attributen (bijv. ras, geslacht, leeftijd) en andere ethisch gevoelige kenmerken die relevant zijn voor het toepassingsgebied van het model (bijv. sociaal-economische status, locatie).
 #1.5.3    Niveau: 2    Rol: V
 Controleer of handmatige steekproeven door domeinexperts een statistisch significante steekproef dekken (bijv. ≥1% of 1.000 monsters, afhankelijk van wat groter is, of zoals bepaald door risicobeoordeling) om subtiele kwaliteitsproblemen te identificeren die niet door automatisering worden opgemerkt.
 #1.8.4    Niveau: 2    Rol: D/V
 Controleer of uitbestede of crowdsourced labeling-workflows technische/procedurele waarborgen bevatten om de vertrouwelijkheid, integriteit van gegevens, labelkwaliteit te waarborgen en datalekken te voorkomen.
 #1.5.4    Niveau: 2    Rol: D/V
 Controleer of herstelstappen worden toegevoegd aan provenance-records.
 #1.6.2    Niveau: 2    Rol: D/V
 Controleer of gemarkeerde monsters een handmatige beoordeling activeren voordat ze worden getraind.
 #1.6.3    Niveau: 2    Rol: V
 Verifieer dat de resultaten de beveiligingsdossier van het model voeden en voortdurende dreigingsinformatie informeren.
 #1.6.4    Niveau: 3    Rol: D/V
 Controleer of de detectielogica wordt vernieuwd met nieuwe dreigingsinformatie.
 #1.6.5    Niveau: 3    Rol: D/V
 Controleer of online-leerprocessen distributieverschuiving monitoren.
 #1.7.1    Niveau: 1    Rol: D/V
 Verifieer dat workflows voor het verwijderen van trainingsgegevens zowel primaire als afgeleide gegevens wissen en beoordeel de impact op het model, en dat de impact op de getroffen modellen wordt beoordeeld en, indien nodig, wordt aangepakt (bijv. via hertraining of recalibratie).
 #1.7.2    Niveau: 2    Rol: D
 Controleer of er mechanismen zijn om de reikwijdte en status van gebruikersinstemming (en intrekkingen) voor gegevens die worden gebruikt bij training te volgen en te respecteren, en dat instemming wordt gevalideerd voordat gegevens worden opgenomen in nieuwe trainingsprocessen of belangrijke modelupdates.
 #1.7.3    Niveau: 2    Rol: V
 Controleer of workflows jaarlijks worden getest en geregistreerd.
 #1.8.1    Niveau: 2    Rol: D/V
 Verifieer dat externe dataleveranciers, inclusief leveranciers van voorgetrainde modellen en externe datasets, een due diligence ondergaan op het gebied van beveiliging, privacy, ethische herkomst en datakwaliteit voordat hun gegevens of modellen worden geïntegreerd.
 #1.8.2    Niveau: 1    Rol: D
 Controleer of externe overdrachten TLS/auth en integriteitscontroles gebruiken.
 #1.8.3    Niveau: 2    Rol: D/V
 Controleer of gegevensbronnen met een hoog risico (bijv. open-source datasets met onbekende herkomst, niet-gecontroleerde leveranciers) een verhoogde controle ondergaan, zoals gesandboxte analyse, uitgebreide kwaliteits-/vooringenomenheidscontroles en gerichte detectie van vergiftiging, voordat ze worden gebruikt in gevoelige toepassingen.
 #1.8.4    Niveau: 3    Rol: D/V
 Verifieer dat voorgetrainde modellen die van derden worden verkregen, worden geëvalueerd op ingebedde vooroordelen, potentiële achterdeurtjes, de integriteit van hun architectuur en de herkomst van hun oorspronkelijke trainingsgegevens voordat ze worden bijgesteld of ingezet.
 #1.5.3    Niveau: 2    Rol: D/V
 Controleer of bij het gebruik van adversariële training de generatie, het beheer en de versiebeheer van adversariële datasets gedocumenteerd en gecontroleerd zijn.
 #1.5.3    Niveau: 3    Rol: D/V
 Verifieer dat de impact van training voor adversarial robuustheid op modelprestaties (zowel tegen schone als adversarial input) en fairness-metrics wordt geëvalueerd, gedocumenteerd en gemonitord.
 #1.5.4    Niveau: 3    Rol: D/V
 Controleer of strategieën voor adversariële training en robuustheid periodiek worden beoordeeld en bijgewerkt om te reageren op evoluerende technieken van adversariële aanvallen.
 #1.4.2    Niveau: 2    Rol: D/V
 Verifieer dat mislukte datasets in quarantaine worden geplaatst met audit trails.
 #1.4.3    Niveau: 2    Rol: D/V
 Controleer of kwaliteitscontroles substandaard datasets blokkeren tenzij uitzonderingen zijn goedgekeurd.
 #1.11.2    Niveau: 2    Rol: D/V
 Controleer of het generatieproces, de parameters en het beoogde gebruik van synthetische gegevens zijn gedocumenteerd.
 #1.11.3    Niveau: 2    Rol: D/V
 Verifieer dat synthetische gegevens worden beoordeeld op risico's zoals vooringenomenheid, privacylekken en representatieproblemen voordat ze worden gebruikt voor training.
 #1.12.3    Niveau: 2    Rol: D/V
 Controleer of waarschuwingen worden gegenereerd voor verdachte toegangsgebeurtenissen en snel worden onderzocht.
 #1.13.1    Niveau: 1    Rol: D/V
 Controleer of expliciete bewaartermijnen zijn vastgesteld voor alle trainingsdatasets.
 #1.13.2    Niveau: 2    Rol: D/V
 Controleer of datasets automatisch verlopen, worden verwijderd of worden beoordeeld voor verwijdering aan het einde van hun levenscyclus.
 #1.13.3    Niveau: 2    Rol: D/V
 Controleer of retentie- en verwijderingsacties worden vastgelegd en auditeerbaar zijn.
 #1.14.1    Niveau: 2    Rol: D/V
 Verifieer dat vereisten voor gegevensresidentie en grensoverschrijdend gegevensverkeer zijn geïdentificeerd en afgedwongen voor alle datasets.
 #1.14.2    Niveau: 2    Rol: D/V
 Controleer of sectorspecifieke regelgeving (bijvoorbeeld gezondheidszorg, financiën) is geïdentificeerd en behandeld bij het omgaan met gegevens.
 #1.14.3    Niveau: 2    Rol: D/V
 Verifieer dat de naleving van relevante privacywetten (bijv. AVG, CCPA) wordt gedocumenteerd en regelmatig wordt herzien.
 #1.16.1    Niveau: 2    Rol: D/V
 Verifieer of er mechanismen bestaan om te reageren op verzoeken van betrokkenen betreffende toegang, rectificatie, beperking of bezwaar.
 #1.16.2    Niveau: 2    Rol: D/V
 Verifieer dat verzoeken worden geregistreerd, gevolgd en binnen wettelijk voorgeschreven termijnen worden afgehandeld.
 #1.16.3    Niveau: 2    Rol: D/V
 Controleer of de processen voor rechten van betrokkenen regelmatig worden getest en beoordeeld op effectiviteit.
 #1.17.1    Niveau: 2    Rol: D/V
 Verifieer dat een impactanalyse wordt uitgevoerd voordat een datasetversie wordt bijgewerkt of vervangen, waarbij modelprestaties, eerlijkheid en naleving worden behandeld.
 #1.17.2    Niveau: 2    Rol: D/V
 Verifieer dat de resultaten van de impactanalyse zijn gedocumenteerd en beoordeeld door relevante belanghebbenden.
 #1.17.3    Niveau: 2    Rol: D/V
 Verifieer dat er terugvalplannen bestaan voor het geval nieuwe versies onaanvaarde risico's of terugvallen introduceren.
 #1.18.1    Niveau: 2    Rol: D/V
 Verifieer dat al het personeel dat betrokken is bij data-annotatie een achtergrondcontrole heeft ondergaan en getraind is in gegevensbeveiliging en privacy.
 #1.18.2    Niveau: 2    Rol: D/V
 Controleer of alle annotatiepersoneel vertrouwelijkheids- en geheimhoudingsovereenkomsten ondertekent.
 #1.18.3    Niveau: 2    Rol: D/V
 Verifieer of annotatieplatforms toegangscontroles afdwingen en toezicht houden op bedreigingen van binnenuit.

#### Referenties

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Bijlage D: Governance en verificatie van veilig coderen met AI-ondersteuning

### Doelstelling

Dit hoofdstuk definieert basisorganisatorische controles voor het veilige en effectieve gebruik van AI-ondersteunde codeerhulpmiddelen tijdens softwareontwikkeling, waarbij veiligheid en traceerbaarheid gedurende de SDLC worden gegarandeerd.

---

### AD.1 AI-ondersteunde veilige coderingsworkflow

Integreer AI-tools in de veilige softwareontwikkelingslevenscyclus (SSDLC) van de organisatie zonder de bestaande beveiligingspoorten te verzwakken.

 #AD.1.1    Niveau: 1    Rol: D/V
 Controleer of een gedocumenteerde workflow beschrijft wanneer en hoe AI-tools code mogen genereren, herstructureren of beoordelen.
 #AD.1.2    Niveau: 2    Rol: D
 Controleer of de workflow overeenkomt met elke SSDLC-fase (ontwerp, uitvoering, codebeoordeling, testen, implementatie).
 #AD.1.3    Niveau: 3    Rol: D/V
 Controleer of metrieken (bijv. kwetsbaarheidsdichtheid, gemiddelde detectietijd) worden verzameld voor door AI geproduceerde code en vergeleken met baselines die alleen door mensen zijn gemaakt.

---

### AD.2 AI-hulpmiddelkwalificatie & dreigingsmodellering

Zorg ervoor dat AI-codeertools worden geëvalueerd op beveiligingsmogelijkheden, risico's en impact op de toeleveringsketen voordat ze worden geïmplementeerd.

 #AD.2.1    Niveau: 1    Rol: D/V
 Controleer of een dreigingsmodel voor elk AI-instrument misbruik, modelinversie, datalekken en risico's in de afhankelijkheidsketen identificeert.
 #AD.2.2    Niveau: 2    Rol: D
 Verifieer dat toolbeoordelingen statische/dynamische analyse omvatten van eventuele lokale componenten en beoordeling van SaaS-eindpunten (TLS, authenticatie/autorisatie, logging).
 #AD.2.3    Niveau: 3    Rol: D/V
 Verifieer dat evaluaties een erkend kader volgen en opnieuw worden uitgevoerd na belangrijke versie-updates.

---

### AD.3 Beheer van beveiligde prompts en context

Voorkom het lekken van geheimen, eigendomsgevoerde code en persoonlijke gegevens bij het opstellen van prompts of contexten voor AI-modellen.

 #AD.3.1    Niveau: 1    Rol: D/V
 Controleer of de schriftelijke richtlijnen het versturen van geheimen, inloggegevens of geclassificeerde gegevens in prompts verbieden.
 #AD.3.2    Niveau: 2    Rol: D
 Controleer of technische controles (redactie aan de clientzijde, goedgekeurde contextfilters) automatisch gevoelige gegevens verwijderen.
 #AD.3.3    Niveau: 3    Rol: D/V
 Controleer of prompts en antwoorden worden getokeniseerd, versleuteld tijdens overdracht en in opslag, en of de bewaartermijnen voldoen aan het dataclassificatiebeleid.

---

### AD.4 Validatie van door AI gegenereerde code

Detecteer en herstel kwetsbaarheden die door AI-uitvoer zijn geïntroduceerd voordat de code wordt samengevoegd of geïmplementeerd.

 #AD.4.1    Niveau: 1    Rol: D/V
 Zorg ervoor dat AI-gegenereerde code altijd wordt onderworpen aan een menselijke codebeoordeling.
 #AD.4.2    Niveau: 2    Rol: D
 Verifieer dat geautomatiseerde scanners (SAST/IAST/DAST) worden uitgevoerd bij elke pull request met AI‑gegenereerde code en blokkeer merges bij kritieke bevindingen.
 #AD.4.3    Niveau: 3    Rol: D/V
 Verifieer dat differentiële fuzz-testing of op eigenschappen gebaseerde tests veiligheid‑kritieke gedragingen bewijzen (bijv. invoervalidatie, autorisatielogica).

---

### AD.5 Verklaarbaarheid en Traceerbaarheid van Code Suggesties

Bied auditors en ontwikkelaars inzicht in waarom een suggestie is gedaan en hoe deze is geëvolueerd.

 #AD.5.1    Niveau: 1    Rol: D/V
 Verifieer dat prompt/response-paren worden vastgelegd met commit-ID's.
 #AD.5.2    Niveau: 2    Rol: D
 Controleer of ontwikkelaars modelverwijzingen (trainingsfragmenten, documentatie) kunnen weergeven ter ondersteuning van een suggestie.
 #AD.5.3    Niveau: 3    Rol: D/V
 Verifieer dat verklaringsrapporten worden opgeslagen met ontwerpdocumenten en worden genoemd in beveiligingsbeoordelingen, waarbij wordt voldaan aan de traceerbaarheidsprincipes van ISO/IEC 42001.

---

### AD.6 Continüe feedback en modelfijnafstelling

Verbeter de beveiligingsprestaties van het model in de loop van de tijd terwijl negatieve verschuiving wordt voorkomen.

 #AD.6.1    Niveau: 1    Rol: D/V
 Controleer of ontwikkelaars onveilige of niet-conforme suggesties kunnen markeren en dat deze markeringen worden bijgehouden.
 #AD.6.2    Niveau: 2    Rol: D
 Controleer of verzamelde feedback periodiek wordt gebruikt voor fijn-afstemming of retrieval-augmented generatie met geverifieerde beveiligde-codeer corpora (bijv. OWASP Cheat Sheets).
 #AD.6.3    Niveau: 3    Rol: D/V
 Verifieer dat een evaluatiekader met gesloten lus regressietests uitvoert na elke fine-tune; beveiligingsmetriek moet voldoen aan of beter zijn dan eerdere baselines vóór implementatie.

---

#### Referenties

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Bijlage E: Voorbeeldtools en -kaders

### Doelstelling

Dit hoofdstuk geeft voorbeelden van tools en frameworks die de implementatie of naleving van een gegeven AISVS-vereiste kunnen ondersteunen. Deze moeten niet worden gezien als aanbevelingen of goedkeuringen door het AISVS-team of het OWASP GenAI Security Project.

---

### AE.1 Beheer van Trainingsgegevens en Beheer van Vooringenomenheid

Gereedschappen gebruikt voor data-analyse, governance en biasbeheer.

 #AE.1.1    Sectie: 1.1
 Data-inventarisatiehulpmiddelen: hulpmiddelen voor het beheer van data-inventaris zoals...
 #AE.1.2    Sectie: 1.2
 Versleuteling In-transit Gebruik TLS voor op HTTPS gebaseerde toepassingen, met tools zoals openSSL en python's`ssl`bibliotheek.

---

### AE.2 Validatie van gebruikersinvoer

Hulpmiddelen om gebruikersinvoer te verwerken en te valideren.

 #AE.2.1    Sectie: 2.1
 Prompt Injectie Verdediging Gereedschap: Gebruik guardrail gereedschap zoals NVIDIA's NeMo of Guardrails AI.

---

