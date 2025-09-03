## Voorplaat

### Over de standaard

De Standaard voor Beveiligingsverificatie van Kunstmatige Intelligentie (AISVS) is een door de gemeenschap aangedreven catalogus met beveiligingsvereisten die datawetenschappers, MLOps-engineers, softwarearchitecten, ontwikkelaars, testers, beveiligingsprofessionals, toolleveranciers, regelgevers en consumenten kunnen gebruiken om betrouwbare AI‑ondersteunde systemen en toepassingen te ontwerpen, bouwen, testen en verifiëren. Het biedt een gemeenschappelijke taal voor het specificeren van beveiligingscontroles gedurende de AI‑levenscyclus—van gegevensverzameling en modelontwikkeling tot implementatie en voortdurende bewaking—zodat organisaties de weerbaarheid, privacy en veiligheid van hun AI‑oplossingen kunnen meten en verbeteren.

### Auteursrecht en Licentie

Versie 0.1 (Eerste openbare conceptversie - Werk in uitvoering), 2025  

![license](images/license.png)
Auteursrecht © 2025 The AISVS Project.  

Vrijgegeven onder deCreative Commons Attribution‑ShareAlike 4.0 International License.
Voor elk hergebruik of distributie moet u de licentievoorwaarden van dit werk duidelijk aan anderen bekendmaken.

### Projectleiders

Jim Manico
Aras “Russ” Memisyazici

### Bijdragers en Beoordelaars

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS is een gloednieuwe standaard die speciaal is ontwikkeld om de unieke beveiligingsuitdagingen van kunstmatige-intelligentiesystemen aan te pakken. Hoewel het inspiratie haalt uit bredere beveiligingspraktijken, is elke eis in AISVS vanaf de grond opgebouwd om het AI-bedreigingslandschap te weerspiegelen en organisaties te helpen veiligere, veerkrachtigere AI-oplossingen te bouwen.

## Voorwoord

Welkom bij de Artificial Intelligence Security Verification Standard (AISVS) versie 1.0!

### Inleiding

Opgericht in 2025 door een gezamenlijke inspanning van de gemeenschap, definieert AISVS de beveiligingsvereisten die overwogen moeten worden bij het ontwerpen, ontwikkelen, implementeren en exploiteren van moderne AI‑modellen, pijplijnen en AI‑gestuurde diensten.

AISVS v1.0 vertegenwoordigt het gezamenlijke werk van de projectleiders, de werkgroep en de bredere gemeenschap van bijdragers om een pragmatische, toetsbare basislijn te produceren voor het beveiligen van AI-systemen.

Ons doel met deze release is AISVS eenvoudig in gebruik te nemen, terwijl het haarscherp gericht blijft op de gedefinieerde omvang en inspeelt op het snel evoluerende risicolandschap dat uniek is voor kunstmatige intelligentie.

### Hoofddoelstellingen voor AISVS versie 1.0

Versie 1.0 zal worden opgesteld met verschillende richtinggevende principes.

#### Duidelijk‑Gedefinieerde Reikwijdte

Elke vereiste moet overeenkomen met AISVS’s naam en missie:

Kunstmatige intelligentie – controles werken op de AI/ML-laag (data, model, pijplijn of inferentie) en zijn de verantwoordelijkheid van AI-beoefenaars.
Beveiliging – Vereisten die rechtstreeks geïdentificeerde beveiligings-, privacy- of veiligheidsrisico's mitigeren.
Verificatie – De taal is zodanig geschreven dat conformiteit objectief kan worden gevalideerd.
Standaard – Secties volgen een consistente structuur en terminologie om een samenhangende referentie te vormen.
​
---

Door AISVS te volgen, kunnen organisaties systematisch de beveiligingspositie van hun AI-oplossingen evalueren en versterken, waardoor een cultuur van veilige AI-engineering wordt bevorderd.

## Het gebruik van de AISVS

De standaard voor beveiligingsverificatie van kunstmatige intelligentie (AISVS) definieert beveiligingsvereisten voor moderne AI-toepassingen en AI-diensten, gericht op aspecten die onder de controle van applicatieontwikkelaars vallen.

De AISVS is bedoeld voor iedereen die de beveiliging van AI-toepassingen ontwikkelt of beoordeelt, waaronder ontwikkelaars, architecten, beveiligingsingenieurs en auditors. Dit hoofdstuk introduceert de structuur en het gebruik van de AISVS, inclusief de verificatieniveaus en de beoogde toepassingsgevallen.

### Beveiligingsverificatieniveaus voor kunstmatige intelligentie

De AISVS definieert drie oplopende niveaus van beveiligingsverificatie. Elk niveau voegt diepte en complexiteit toe, waardoor organisaties hun beveiligingshouding kunnen afstemmen op het risiconiveau van hun AI-systemen.

Organisaties kunnen op niveau 1 beginnen en geleidelijk hogere niveaus implementeren naarmate de beveiligingsvolwassenheid en bedreigingsblootstelling toenemen.

#### Definitie van de niveaus

Elke vereiste in AISVS v1.0 is toegewezen aan een van de onderstaande niveaus:

 Niveau 1 vereisten

Niveau 1 omvat de meest kritieke en fundamentele beveiligingsvereisten. Deze richten zich op het voorkomen van veelvoorkomende aanvallen die niet afhankelijk zijn van andere randvoorwaarden of kwetsbaarheden. De meeste Niveau 1 maatregelen zijn ofwel eenvoudig uit te voeren of essentieel genoeg om de inspanning te rechtvaardigen.

 Niveau 2 vereisten

Niveau 2 behandelt meer geavanceerde of minder voorkomende aanvallen, evenals gelaagde verdedigingsmaatregelen tegen wijdverspreide dreigingen. Deze vereisten kunnen complexere logica vereisen of gericht zijn op specifieke aanvalvoorwaarden.

 Niveau 3 vereisten

Niveau 3 omvat controles die doorgaans moeilijker te implementeren zijn of die slechts in bepaalde situaties van toepassing zijn. Deze vormen vertegenwoordigen vaak defense-in-depth-mechanismen of mitigaties tegen niche-aanvallen, gerichte aanvallen of hoog-complexe aanvallen.

#### Rol (D/V)

Elk AISVS-vereiste is gemarkeerd volgens het primaire publiek:

D – ontwikkelaarsgerichte vereisten
V – Verifieerder/auditor-gerichte vereisten
D/V – Relevant voor zowel ontwikkelaars als verificateurs

## C1 Trainingsgegevens Governance & Biasbeheer

### Beheersdoel

Trainingsdata moeten op een manier worden verkregen, behandeld en onderhouden die provenance, veiligheid, kwaliteit en eerlijkheid waarborgt. Dit voldoet aan wettelijke verplichtingen en vermindert risico's op bias, datavervalsing of privacy-inbreuken die tijdens de training voorkomen en die de gehele AI-levenscyclus kunnen beïnvloeden.

---

### C1.1 Oorsprong van trainingsdata

Onderhoud een verifieerbare inventaris van alle datasets, accepteer uitsluitend betrouwbare bronnen en registreer elke wijziging voor auditbaarheid.

 #1.1.1    Niveau: 1    Rol: D/V
 Controleer of een actuele inventaris van elke trainingsdata-bron (herkomst, beheerder/eigenaar, licentie, verzamelingsmethode, beperkingen voor het beoogde gebruik en verwerkingsgeschiedenis) wordt onderhouden.
 #1.1.2    Niveau: 1    Rol: D/V
 Verifieer dat trainingsdata-processen onnodige kenmerken, attributen of velden uitsluiten (bijv. ongebruikte metadata, gevoelige PII, gelekte testgegevens).
 #1.1.3    Niveau: 2    Rol: D/V
 Controleer of alle datasetwijzigingen onderworpen zijn aan een gelogd goedkeuringsproces.
 #1.1.4    Niveau: 3    Rol: D/V
 Verifieer of datasets of subsets waar mogelijk watermerken bevatten of vingerafdrukken hebben.

---

### C1.2 Trainingsgegevens Beveiliging & Integriteit

Beperk de toegang tot trainingsgegevens, versleutel deze zowel in rusttoestand als tijdens verzending, en valideer de integriteit ervan om manipulatie, diefstal of data-poisoning te voorkomen.

 #1.2.1    Niveau: 1    Rol: D/V
 Verifieer dat toegangscontroles de opslag van trainingsdata en datapijplijnen beschermen.
 #1.2.2    Niveau: 2    Rol: D/V
 Controleer of alle toegang tot trainingsdata gelogd is, inclusief gebruiker, tijd en actie.
 #1.2.3    Niveau: 2    Rol: D/V
 Verifieer dat trainingsdatasets tijdens overdracht en in rust zijn versleuteld, met behulp van cryptografische algoritmen volgens industrienormen en praktijken voor sleutelbeheer.
 #1.2.4    Niveau: 2    Rol: D/V
 Verifieer of cryptografische hashwaarden of digitale handtekeningen worden gebruikt om de integriteit van gegevens te waarborgen tijdens de opslag en overdracht van trainingsgegevens.
 #1.2.5    Niveau: 2    Rol: D/V
 Controleer of geautomatiseerde detectietechnieken worden toegepast om ongeautoriseerde wijzigingen of corruptie van trainingsgegevens te voorkomen.
 #1.2.6    Niveau: 2    Rol: D/V
 Controleer of verouderde trainingsgegevens veilig zijn gewist of geanonimiseerd.
 #1.2.7    Niveau: 3    Rol: D/V
 Verifieer dat alle versies van trainingsdatasets uniek geïdentificeerd zijn, onveranderlijk opgeslagen zijn en auditbaar zijn om rollback en forensische analyse mogelijk te maken.

---

### C1.3 Labelen van trainingsdata: Kwaliteit, Integriteit en Beveiliging

Bescherm labels en eis een technische beoordeling voor kritische gegevens.

 #1.3.1    Niveau: 2    Rol: D/V
 Controleer of cryptografische hashes of digitale handtekeningen op labelartefacten zijn toegepast om hun integriteit en authenticiteit te waarborgen.
 #1.3.2    Niveau: 2    Rol: D/V
 Controleer of etiketterings-interfaces en platformen sterke toegangscontroles afdwingen, alle etiketterings-activiteiten bijhouden in tamper-evidente auditlogboeken en beschermen tegen ongeautoriseerde wijzigingen.
 #1.3.3    Niveau: 3    Rol: D/V
 Controleer of gevoelige informatie in labels op veldniveau is geredigeerd, geanonimiseerd of versleuteld, zowel in rust als tijdens verzending.

---

### C1.4 Kwaliteit van trainingsgegevens en beveiligingswaarborging

Combineer geautomatiseerde validatie, handmatige steekproefscontroles en gelogde herstelmaatregelen om de betrouwbaarheid van de dataset te waarborgen.

 #1.4.1    Niveau: 1    Rol: D
 Controleer of geautomatiseerde tests formaatfouten en nullwaarden opvangen bij elke gegevensinname of significante gegevenstransformatie.
 #1.4.2    Niveau: 2    Rol: D/V
 Controleer of de LLM-trainings- en fijnafstemmingspijplijnen poisoning-detectie en data-integriteitsvalidatie implementeren (bijv. statistische methoden, uitbijterdetectie, embedding-analyse) om potentiële poisoning-aanvallen (bijv. label-flipping, backdoor-triggerinvoer, rolwisselingscommando's, invloedrijke exemplaar-aanvallen) of onbedoelde datacorruptie in trainingsgegevens te identificeren.
 #1.4.3    Niveau: 3    Rol: D/V
 Verifieer dat passende verdedigingen, zoals adversarial training (met gegenereerde adversariale voorbeelden), data-augmentatie met verstoorde invoer, of robuuste optimalisatietechnieken, zijn geïmplementeerd en afgestemd voor relevante modellen op basis van een risicobeoordeling.
 #1.4.4    Niveau: 2    Rol: D/V
 Verifieer dat automatisch gegenereerde labels (bijv. via LLMs of zwakke supervisie) onderworpen zijn aan betrouwbaarheidsdrempels en controles op consistentie om hallucinatoire labels, misleidende labels of labels met lage betrouwbaarheid te detecteren.
 #1.4.5    Niveau: 3    Rol: D
 Controleer of geautomatiseerde tests labelverschuivingen opvangen bij elke inlezing van data of bij een significante datatransformatie.

---

### C1.5 Gegevensafstamming en traceerbaarheid

Volg de volledige reis van elk gegevenspunt van de bron tot de modelinvoer voor auditbaarheid en incidentrespons.

 #1.5.1    Niveau: 2    Rol: D/V
 Verifieer dat de herkomst van elk datapunt, inclusief alle transformaties, augmentaties en samenvoegingen, is vastgelegd en kan worden gereconstrueerd.
 #1.5.2    Niveau: 2    Rol: D/V
 Verifieer dat de lineage-registraties onveranderlijk zijn, veilig opgeslagen en toegankelijk voor audits.
 #1.5.3    Niveau: 2    Rol: D/V
 Verifieer dat de data-lineage (afstammings-traceerbaarheid) synthetische gegevens die zijn gegenereerd via privacybeschermende of generatieve technieken dekt, en dat alle synthetische gegevens in de hele pipeline duidelijk gelabeld en te onderscheiden zijn van echte gegevens.

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

## C2 Gebruikersinvoervalidatie

### Beheersdoel

Robuuste validatie van gebruikersinvoer is een eerste verdedigingslinie tegen enkele van de meest schadelijke aanvallen op KI-systemen. Promptinjection-aanvallen kunnen systeeminstructies overschrijven, gevoelige gegevens lekken, of het model laten leiden naar gedrag dat niet is toegestaan. Tenzij er specifieke filters en instructiehiërarchieën zijn, blijkt uit onderzoek dat "multi-shot" jailbreak-aanvallen die profiteren van zeer lange contextvensters effectief zullen zijn. Ook subtiele adversarial-perturbatie-aanvallen—zoals homoglyph-wissels of 1337-taal—kunnen stilletjes de beslissingen van een model veranderen.

---

### C2.1 Bescherming tegen promptinjectie

Promptinjection is een van de grootste risico's voor AI-systemen. Beschermingen tegen deze tactiek maken gebruik van een combinatie van statische patroonfilters, dynamische classificatoren en handhaving van de instructiehiërarchie.

 #2.1.1    Niveau: 1    Rol: D/V
 Verifieer of gebruikersinvoer wordt gescreend tegen een voortdurend bijgewerkte bibliotheek van bekende promptinjectiepatronen (jailbreak-sleutelwoorden, "negeer eerder", rolspelsketens, indirecte HTML/URL-aanvallen).
 #2.1.2    Niveau: 1    Rol: D/V
 Controleer dat het systeem een instructiehiërarchie afdwingt waarin berichten van het systeem of van de ontwikkelaar de instructies van de gebruiker overschrijven, zelfs na de uitbreiding van het contextvenster.
 #2.1.3    Niveau: 2    Rol: D/V
 Verifieer dat adversarial evaluation tests (bijv. Red Team "many-shot" prompts) vóór elke release van een model of prompt-template worden uitgevoerd, met drempels voor het slagingspercentage en geautomatiseerde blokkades voor regressies.
 #2.1.4    Niveau: 2    Rol: D
 Controleer of prompts afkomstig uit inhoud van derden (webpagina's, PDF's, e-mails) gezuiverd zijn in een geïsoleerde parsing-context voordat ze in de hoofdprompt worden samengevoegd.
 #2.1.5    Niveau: 3    Rol: D/V
 Verifieer dat alle updates van prompt-filterregels, versies van classificatiemodellen en wijzigingen aan de bloklijst onder versiebeheer staan en auditbaar zijn.

---

### C2.2 Weerstand tegen adversarial-voorbeelden

Modellen voor natuurlijke taalverwerking (NLP) zijn nog steeds kwetsbaar voor subtiele teken- en woordniveau verstoringen die mensen vaak over het hoofd zien, maar modellen neigen ertoe ze verkeerd te classificeren.

 #2.2.1    Niveau: 1    Rol: D
 Controleer of de basisinvoer-normalisatiestappen (Unicode NFC, homoglyph mapping, whitespace trimming) vóór tokenisatie worden uitgevoerd.
 #2.2.2    Niveau: 2    Rol: D/V
 Verifieer dat statistische anomaliedetectie invoer markeert met een ongebruikelijk hoge Levenshtein-afstand tot taalkundige normen, overmatig herhaalde tokens of abnormale embedding-afstanden.
 #2.2.3    Niveau: 2    Rol: D
 Verifieer dat de inferentie-pijplijn optionele adversarial-training–geharde modelvarianten of verdedigingslagen ondersteunt (bijvoorbeeld randomisatie, defensieve distillatie) voor hoog-risico-eindpunten.
 #2.2.4    Niveau: 2    Rol: V
 Controleer of vermoedelijke adversarial invoer in quarantaine wordt geplaatst, gelogd met volledige payloads (na PII-redactie).
 #2.2.5    Niveau: 3    Rol: D/V
 Verifieer dat robuustheidsmetingen (de slagingskans van bekende aanvalssuites) in de loop der tijd worden bijgehouden en regressies leiden tot een release-blocker.

---

### C2.3 Schema, Type & Lengtevalidatie

AI-aanvallen met misvormde of te grote invoer kunnen parsingfouten veroorzaken, promptspilling tussen velden veroorzaken en bronnenuitputting tot gevolg hebben.  Strikte handhaving van het schema is ook een vereiste bij het uitvoeren van deterministische tool-aanroepen.

 #2.3.1    Niveau: 1    Rol: D
 Controleer dat elk API-eindpunt of elke functie-aanroep een expliciet invoerschema definieert (JSON Schema, Protobuf of multimodale equivalent) en dat invoerwaarden vóór de prompt-samenstelling gevalideerd worden.
 #2.3.2    Niveau: 1    Rol: D/V
 Controleer dat invoer die de maximale token- of byte-limieten overschrijdt, wordt geweigerd met een veilige foutmelding en nooit stilletjes wordt afgekapt.
 #2.3.3    Niveau: 2    Rol: D/V
 Verifieer dat typecontroles (bijv. numerieke bereiken, enum-waarden, MIME-types voor afbeeldingen/audio) aan de server-side worden afgedwongen, en niet alleen in de client code.
 #2.3.4    Niveau: 2    Rol: D
 Controleer dat semantische validators (bijv. JSON Schema) in constante tijd worden uitgevoerd om algorithmische DoS te voorkomen.
 #2.3.5    Niveau: 3    Rol: V
 Verifieer dat validatiefouten worden gelogd met geredigeerde payload-snippets en eenduidige foutcodes om de beveiligingstriage te vergemakkelijken.

---

### C2.4 Inhoud en Beleidscreening

Ontwikkelaars moeten in staat zijn syntactisch geldige prompts te detecteren die om verboden inhoud vragen (zoals illegale instructies, haatspraak en auteursrechtelijk beschermd materiaal) en deze vervolgens te voorkomen dat ze zich verspreiden.

 #2.4.1    Niveau: 1    Rol: D
 Verifieer dat een inhoudsclassificator (zero-shot of fijn afgesteld) elke invoer beoordeelt op geweld, zelfbeschadiging, haat, seksuele inhoud en illegale verzoeken, met instelbare drempels.
 #2.4.2    Niveau: 1    Rol: D/V
 Verifieer dat invoeren die beleidsregels overtreden standaardafwijzingen of veilige voltooiingen ontvangen, zodat ze niet worden doorgegeven aan downstream LLM-aanroepen.
 #2.4.3    Niveau: 2    Rol: D
 Verifieer dat het screeningmodel of de regelset ten minste elk kwartaal opnieuw wordt getraind/bijgewerkt, waarbij nieuw waargenomen jailbreak- of beleidsomzeilingspatronen worden meegenomen.
 #2.4.4    Niveau: 2    Rol: D
 Controleer of screening voldoet aan gebruikersspecifieke beleidsregels (leeftijd, regionale wettelijke beperkingen) via regels op basis van attributen die bij het verzoek worden opgelost.
 #2.4.5    Niveau: 3    Rol: V
 Verifieer dat screeninglogboeken de waarschijnlijkheidscores van het classificatiemodel en labels voor beleidscategorieën bevatten voor SOC-correlatie en toekomstige red-team-replay.

---

### C2.5 Invoerlimiet en Misbruikpreventie

Ontwikkelaars moeten misbruik, uitputting van bronnen en geautomatiseerde aanvallen tegen AI-systemen voorkomen door de invoersnelheden te beperken en afwijkende gebruikspatronen te detecteren.

 #2.5.1    Niveau: 1    Rol: D/V
 Controleer of per-gebruiker, per-IP-adres en per-API-sleutel rate-limieten worden afgedwongen voor alle invoer-eindpunten.
 #2.5.2    Niveau: 2    Rol: D/V
 Controleer of burst-rate-limits en sustained-rate-limits zijn afgesteld om DoS- en brute-force-aanvallen te voorkomen.
 #2.5.3    Niveau: 2    Rol: D/V
 Controleer of afwijkende gebruikspatronen (bijv. snelle opeenvolgende verzoeken, invoeroverbelasting) geautomatiseerde blokkades of escalaties activeren.
 #2.5.4    Niveau: 3    Rol: V
 Controleer of de logbestanden voor misbruikpreventie worden bewaard en beoordeeld op opkomende aanvalspatronen.

---

### C2.6 Multimodale Invoervalidatie

AI-systemen moeten robuuste validatie van niet-tekstuele invoer (afbeeldingen, audio, bestanden) inbouwen om injectie, omzeiling of misbruik van middelen te voorkomen.

 #2.6.1    Niveau: 1    Rol: D
 Verifieer dat alle niet-tekstuele invoer (afbeeldingen, audio, bestanden) op type, grootte en formaat is gevalideerd voordat deze wordt verwerkt.
 #2.6.2    Niveau: 2    Rol: D/V
 Verifieer dat bestanden vóór de gegevensinname worden gescand op malware en steganografische payloads.
 #2.6.3    Niveau: 2    Rol: D/V
 Zorg ervoor dat afbeeldings- en audiogegevens worden gecontroleerd op adversariële verstoringen of bekende aanvalspatronen.
 #2.6.4    Niveau: 3    Rol: V
 Controleer of multimodale invoervalidatiefouten worden gelogd en waarschuwingen activeren voor nader onderzoek.

---

### C2.7 Invoerherkomst & Toeschrijving

AI-systemen moeten auditing, misbruikregistratie en naleving ondersteunen door de oorsprong van alle gebruikersinvoer te monitoren en te taggen.

 #2.7.1    Niveau: 1    Rol: D/V
 Controleer of alle gebruikersinvoer bij het opnemen is voorzien van metagegevens (gebruikers-ID, sessie, bron, tijdstempel, IP-adres).
 #2.7.2    Niveau: 2    Rol: D/V
 Controleer of herkomstmetadata behouden blijft en auditbaar is voor alle verwerkte invoer.
 #2.7.3    Niveau: 2    Rol: D/V
 Controleer of anomale of onbetrouwbare invoerbronnen worden gemarkeerd en onderworpen aan verhoogde screening of blokkering.

---

### C2.8 Real-Time Adaptieve Dreigingsdetectie

Ontwikkelaars moeten geavanceerde dreigingsdetectiesystemen voor AI inzetten die zich aanpassen aan nieuwe aanvalspatronen en realtime bescherming bieden met gecompileerde patroonmatching.

 #2.8.1    Niveau: 1    Rol: D/V
 Controleer of bedreigingsdetectiepatronen zijn gecompileerd tot geoptimaliseerde regex-engines voor realtime filtering met hoge prestaties en minimale latentie.
 #2.8.2    Niveau: 1    Rol: D/V
 Controleer of bedreigingsdetectiesystemen afzonderlijke patroonbibliotheken bijhouden voor verschillende dreigingscategorieën (promptinjectie, schadelijke inhoud, gevoelige gegevens, systeemcommando's).
 #2.8.3    Niveau: 2    Rol: D/V
 Verifieer dat adaptieve dreigingsdetectie machine-learning-modellen omvat die de gevoeligheid voor dreigingen bijwerken op basis van aanvalfrequentie en succespercentages.
 #2.8.4    Niveau: 2    Rol: D/V
 Verifieer dat real-time dreigingsinformatiefeeds automatisch patroonbibliotheken bijwerken met nieuwe aanvalssignaturen en IOCs (Indicatoren van compromissie).
 #2.8.5    Niveau: 3    Rol: D/V
 Controleer of de ratio van valse positieven bij dreigingsdetectie continu wordt gemonitord en of de patroonspecificiteit automatisch wordt afgesteld om verstoring van legitieme toepassingsgevallen te minimaliseren.
 #2.8.6    Niveau: 3    Rol: D/V
 Controleer of contextuele dreigingsanalyse rekening houdt met de invoerbron, gedragspatronen van de gebruiker en sessiegeschiedenis om de detectienauwkeurigheid te verbeteren.
 #2.8.7    Niveau: 3    Rol: D/V
 Verifieer dat de prestatie-indicatoren voor dreigingsdetectie (detectiepercentage, verwerkingslatentie, middelenverbruik) in realtime worden gemonitord en geoptimaliseerd.

---

### C2.9 Multimodale Beveiligingsvalidatiepijplijn

Ontwikkelaars moeten beveiligingsvalidatie bieden voor tekst-, beeld-, audio- en andere AI-invoer-modi met specifieke soorten dreigingsdetectie en resource-isolatie.

 #2.9.1    Niveau: 1    Rol: D/V
 Controleer of elke invoermodaliteit toegewijde beveiligingsvalidatoren heeft met gedocumenteerde dreigingspatronen (tekst: promptinjection, afbeeldingen: steganografie, audio: spectrogramaanvallen) en detectiedrempels.
 #2.9.2    Niveau: 2    Rol: D/V
 Controleer dat multimodale invoer wordt verwerkt in geïsoleerde sandbox-omgevingen met gedefinieerde bronnenlimieten (geheugen, CPU, verwerkingstijd) die specifiek zijn voor elk modaliteitstype en vastgelegd in beveiligingsbeleid.
 #2.9.3    Niveau: 2    Rol: D/V
 Controleer of cross-modal aanvalendetectie gecoördineerde aanvallen identificeert die zich over meerdere invoertypen uitstrekken (bijv. steganografische payloads in afbeeldingen gecombineerd met promptinjectie in tekst) met correlatieregels en het genereren van waarschuwingen.
 #2.9.4    Niveau: 3    Rol: D/V
 Controleer of multimodale validatiefouten leiden tot gedetailleerde logging, inclusief alle invoermodaliteiten, validatieresultaten, dreigingsscores en correlatieanalyse met gestructureerde logformaten voor SIEM-integratie.
 #2.9.5    Niveau: 3    Rol: D/V
 Verifieer dat modaliteitsspecifieke inhoudsclassificatoren zijn bijgewerkt volgens gedocumenteerde schema's (minimaal elk kwartaal) met nieuwe dreigingspatronen, adversariële voorbeelden en prestatiebenchmarks die boven de basisdrempels blijven.

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

## C3-modellevenscyclusbeheer en wijzigingsbeheer

### Beheersdoel

AI-systemen moeten wijzigingscontroleprocessen implementeren die voorkomen dat onbevoegde of onveilige modelwijzigingen in productie terechtkomen. Deze controle waarborgt de integriteit van het model gedurende de gehele levenscyclus--van ontwikkeling via uitrol tot ontmanteling--wat snelle incidentrespons mogelijk maakt en verantwoording voor alle wijzigingen waarborgt.

Kernbeveiligingsdoel: Alleen geautoriseerde, gevalideerde modellen komen in productie door middel van gecontroleerde processen die integriteit, traceerbaarheid en herstelbaarheid waarborgen.

---

### C3.1 Modelautorisatie & Integriteit

Alleen geautoriseerde modellen met geverifieerde integriteit bereiken productieomgevingen.

 #3.1.1    Niveau: 1    Rol: D/V
 Controleer of alle modelartefacten (gewichten, configuraties, tokenizers) cryptografisch ondertekend zijn door geautoriseerde partijen vóór de uitrol.
 #3.1.2    Niveau: 1    Rol: D/V
 Verifieer dat de integriteit van het model tijdens de uitrol wordt gevalideerd en dat verificatiefouten bij de handtekening het laden van het model verhinderen.
 #3.1.3    Niveau: 2    Rol: D/V
 Verifieer dat registraties van modelprovenantie de identiteit van een autoriserende entiteit, de controlesommen van trainingsgegevens, validatietestresultaten met de status geslaagd of niet geslaagd, en een aanmaaktijdstempel bevatten.
 #3.1.4    Niveau: 2    Rol: D/V
 Verifieer dat alle modelartefacten semantische versienummering gebruiken (MAJOR.MINOR.PATCH) met gedocumenteerde criteria die aangeven wanneer elk versiecomponent toeneemt.
 #3.1.5    Niveau: 2    Rol: V
 Controleer of de afhankelijkheidsregistratie een real-time inventaris bijhoudt die een snelle identificatie van alle verbruikende systemen mogelijk maakt.

---

### C3.2 Model Validatie & Testen

Modellen moeten vóór de uitrol voldoen aan gedefinieerde beveiligings- en veiligheidsvalidaties.

 #3.2.1    Niveau: 1    Rol: D/V
 Controleer of modellen geautomatiseerde beveiligingstests ondergaan die invoervalidatie, uitvoer-sanitatie en veiligheidsbeoordelingen omvatten, met van tevoren afgesproken organisatorische pass/fail-drempels vóór de uitrol.
 #3.2.2    Niveau: 1    Rol: D/V
 Controleer of validatiefouten automatisch de modelimplementatie blokkeren na expliciete override-goedkeuring door vooraf aangewezen geautoriseerd personeel met gedocumenteerde zakelijke rechtvaardigingen.
 #3.2.3    Niveau: 2    Rol: V
 Controleer of de testresultaten cryptografisch ondertekend zijn en onveranderlijk gekoppeld zijn aan de specifieke hash van de modelversie die wordt gevalideerd.
 #3.2.4    Niveau: 2    Rol: D/V
 Controleer dat nooduitrollen een gedocumenteerde beveiligingsrisicoanalyse en goedkeuring van een vooraf aangewezen beveiligingsautoriteit binnen afgesproken termijnen vereisen.

---

### C3.3 Gecontroleerde Uitrol & Rollback

Modelimplementaties moeten worden gecontroleerd, gemonitord en omkeerbaar zijn.

 #3.3.1    Niveau: 1    Rol: D
 Verifieer dat productie-implementaties geleidelijke uitrolmechanismen toepassen (canary-implementaties, blue-green-implementaties) met automatische rollback-triggers op basis van foutpercentages die van tevoren zijn afgesproken, latentiegrenzen of beveiligingswaarschuwingscriteria.
 #3.3.2    Niveau: 1    Rol: D/V
 Controleer of rollback-mogelijkheden de volledige modeltoestand (gewichten, configuraties, afhankelijkheden) atomair herstellen binnen voorgedefinieerde organisatorische tijdvensters.
 #3.3.3    Niveau: 2    Rol: D/V
 Controleer dat uitrolprocessen cryptografische handtekeningen valideren en integriteitschecksums berekenen vóór activatie van het model, en laat de uitrol mislukken bij elke afwijking.
 #3.3.4    Niveau: 2    Rol: D/V
 Controleer of noodafsluitingsmogelijkheden voor modellen model-endpoints kunnen uitschakelen binnen vooraf gedefinieerde responstijden via geautomatiseerde circuit-breakers of handmatige kill-switches.
 #3.3.5    Niveau: 2    Rol: V
 Controleer of rollback artefacten (vorige modelversies, configuraties, afhankelijkheden) worden bewaard volgens het beleid van de organisatie met immutabele opslag voor incidentrespons.

---

### C3.4 Verantwoording van wijzigingen & audit

Alle wijzigingen in de levenscyclus van het model moeten traceerbaar en auditbaar zijn.

 #3.4.1    Niveau: 1    Rol: V
 Controleer dat alle modelwijzigingen (uitrol, configuratie, uitfasering) onveranderlijke auditlogboeken genereren, inclusief een tijdstempel, een geauthenticeerde actor-identiteit, een wijzigingstype en toestanden vóór en na.
 #3.4.2    Niveau: 2    Rol: D/V
 Controleer of toegang tot auditlogboeken de juiste autorisatie vereist en of alle toegangspogingen worden gelogd met gebruikersidentiteit en een tijdstempel.
 #3.4.3    Niveau: 2    Rol: D/V
 Verifieer dat prompt-sjablonen en systeemberichten onder versiebeheer staan in Git-repositories met verplichte codebeoordeling en goedkeuring door aangewezen beoordelaars voordat ze in productie worden genomen.
 #3.4.4    Niveau: 2    Rol: V
 Controleer of auditregistraties voldoende details bevatten (model-hashes, configuratie-snapshots, afhankelijkheidsversies) om een volledige reconstructie van de toestand van het model mogelijk te maken voor elk tijdstempel binnen de retentieperiode.

---

### C3.5 Veilige ontwikkelingspraktijken

Modelontwikkeling en trainingsprocessen moeten veilige praktijken volgen om beveiligingsinbreuken te voorkomen.

 #3.5.1    Niveau: 1    Rol: D
 Controleer of omgevingen voor modelontwikkeling, testen en productie fysiek of logisch gescheiden zijn. Ze hebben geen gedeelde infrastructuur, afzonderlijke toegangscontroles en geïsoleerde gegevensopslag.
 #3.5.2    Niveau: 1    Rol: D
 Verifieer dat modeltraining en fijn afstemmen plaatsvinden in geïsoleerde omgevingen met gecontroleerde netwerktoegang.
 #3.5.3    Niveau: 1    Rol: D/V
 Verifieer dat trainingsgegevens-bronnen gevalideerd zijn via integriteitscontroles en geauthenticeerd via vertrouwde bronnen met een gedocumenteerde keten van bewaring voordat ze worden gebruikt bij de ontwikkeling van het model.
 #3.5.4    Niveau: 2    Rol: D
 Verifieer dat modelontwikkelingsartefacten (hyperparameters, trainingscripts, configuratiebestanden) zijn opgeslagen in versiebeheer en die goedkeuring na peer review vereisen voordat ze voor training worden gebruikt.

---

### C3.6 Model Uitdienststelling & Ontmanteling

Modellen moeten veilig buiten gebruik worden gesteld wanneer ze niet langer nodig zijn of wanneer beveiligingsproblemen worden vastgesteld.

 #3.6.1    Niveau: 1    Rol: D
 Controleer dat processen voor het uitfaseren van modellen automatisch afhankelijkheidsgrafen scannen, alle systemen identificeren die het model gebruiken, en vooraf afgesproken aankondigingsperiodes bieden voordat de modellen worden uitgefaseerd.
 #3.6.2    Niveau: 1    Rol: D/V
 Controleer dat uit dienst genomen modelartefacten veilig worden gewist door middel van cryptografische uitwissing of multi-pass overschrijven, overeenkomstig gedocumenteerd dataretentiebeleid met gevalideerde vernietigingscertificaten.
 #3.6.3    Niveau: 2    Rol: V
 Controleer dat gebeurtenissen bij het buiten gebruik stellen van modellen worden gelogd met een tijdstempel en de identiteit van de actor, en dat modelhandtekeningen worden ingetrokken om hergebruik te voorkomen.
 #3.6.4    Niveau: 2    Rol: D/V
 Verifieer dat nooduitfasering van het model de toegang tot het model kan uitschakelen binnen vooraf vastgestelde noodreactietermijnen via geautomatiseerde kill-switches als kritieke beveiligingslekken worden ontdekt.

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

## C4 Infrastructuur, Configuratie & Implementatiebeveiliging

### Beheersdoel

AI-infrastructuur moet bestand zijn tegen privilege-escalatie, manipulatie van de toeleveringsketen en laterale beweging via veilige configuratie, runtime-isolatie, vertrouwde deployment-pijplijnen en uitgebreide monitoring. Alleen geautoriseerde, gevalideerde infrastructuurcomponenten en configuraties bereiken productie via gecontroleerde processen die veiligheid, integriteit en auditabiliteit waarborgen.

Kernbeveiligingsdoel: Alleen cryptografisch ondertekende, op kwetsbaarheden gescande infrastructuurcomponenten bereiken productie via geautomatiseerde validatiepijplijnen die beveiligingsbeleid afdwingen en onveranderlijke auditsporen handhaven.

---

### C4.1 Runtime-omgeving isolatie

Voorkom containeruitbraken en privilege-escalatie door isolatieprimitieven op kernel-niveau en verplichte toegangscontroles.

 #4.1.1    Niveau: 1    Rol: D/V
 Verifieer dat alle AI-containers ALLE Linux-capabilities verwijderen behalve CAP_SETUID, CAP_SETGID en de expliciet vereiste Linux-capabilities die in de beveiligingsbasislijnen zijn gedocumenteerd.
 #4.1.2    Niveau: 1    Rol: D/V
 Controleer of seccomp-profielen alle systeemoproepen blokkeren, behalve die in vooraf goedgekeurde toegestane lijsten, waarbij overtredingen de container beëindigen en beveiligingswaarschuwingen genereren.
 #4.1.3    Niveau: 2    Rol: D/V
 Controleer dat AI-workloads draaien met root-bestandssystemen die alleen-lezen zijn, tmpfs voor tijdelijke gegevens, en genaamde volumes voor persistente gegevens, waarbij noexec-mountopties afgedwongen worden.
 #4.1.4    Niveau: 2    Rol: D/V
 Verifieer of eBPF-gebaseerde runtimebewaking (Falco, Tetragon, of een gelijkwaardig alternatief) detecteert pogingen tot privilege-escalatie en beëindigt automatisch de overtredende processen binnen de door de organisatie gestelde responstijden.
 #4.1.5    Niveau: 3    Rol: D/V
 Controleer of AI-werkbelastingen met een hoog risico worden uitgevoerd in hardware-geïsoleerde omgevingen (Intel TXT, AMD SVM, of toegewijde bare-metal knooppunten) met attestatieverificatie.

---

### C4.2 Veilige Build- en Deployment-pijplijnen

Zorg voor cryptografische integriteit en beveiliging van de toeleveringsketen door middel van herhaalbare builds en ondertekende artefacten.

 #4.2.1    Niveau: 1    Rol: D/V
 Verifieer dat infrastructuur-als-code bij elke commit wordt gescand met tools (tfsec, Checkov of Terrascan) en merges blokkeert bij bevindingen met CRITICAL of HIGH-ernst.
 #4.2.2    Niveau: 1    Rol: D/V
 Controleer dat container-builds reproduceerbaar zijn met identieke SHA256-hashes over meerdere builds heen en genereer provenance-attestaties van SLSA-niveau 3 die met Sigstore zijn ondertekend.
 #4.2.3    Niveau: 2    Rol: D/V
 Verifieer dat containerafbeeldingen CycloneDX- of SPDX-SBOMs bevatten en door Cosign ondertekend zijn vóór het pushen naar de registry, en dat niet-ondertekende afbeeldingen bij de implementatie worden geweigerd.
 #4.2.4    Niveau: 2    Rol: D/V
 Verifieer dat CI/CD-pijplijnen OIDC-tokens gebruiken afkomstig van HashiCorp Vault, AWS IAM-rollen of Azure-beheerde identiteit, met een geldigheidsduur die niet langer is dan de limieten van het beveiligingsbeleid van de organisatie.
 #4.2.5    Niveau: 2    Rol: D/V
 Verifieer dat Cosign-handtekeningen en SLSA-provenance tijdens het uitrolproces worden gevalideerd voordat de container wordt uitgevoerd, en dat verificatiefouten ervoor zorgen dat de uitrol mislukt.
 #4.2.6    Niveau: 2    Rol: D/V
 Controleer of buildomgevingen draaien in tijdelijke containers of VM's zonder persistente opslag en netwerkisolatie ten opzichte van productie-VPC's.

---

### C4.3 Netwerkbeveiliging & Toegangscontrole

Implementeer Zero-Trust-netwerken met standaard-weigeringsbeleid en versleutelde communicatie.

 #4.3.1    Niveau: 1    Rol: D/V
 Controleer of Kubernetes NetworkPolicies of een gelijkwaardig systeem een default-deny-beleid voor inkomend en uitgaand verkeer implementeert, met expliciete toegangsregels voor vereiste poorten (443, 8080, enz.).
 #4.3.2    Niveau: 1    Rol: D/V
 Controleer of SSH (poort 22), RDP (poort 3389) en cloud metadata-eindpunten (169.254.169.254) zijn geblokkeerd of certificaatgebaseerde authenticatie vereisen.
 #4.3.3    Niveau: 2    Rol: D/V
 Controleer dat uitgaand verkeer via HTTP/HTTPS-proxies (Squid, Istio of cloud NAT-gateways) wordt gefilterd met domeintoegestane lijsten en dat geblokkeerde verzoeken worden gelogd.
 #4.3.4    Niveau: 2    Rol: D/V
 Verifieer dat de communicatie tussen services mutual TLS (mTLS) gebruikt, met certificaten die volgens het organisatiebeleid zijn vernieuwd, en dat certificaatvalidatie wordt afgedwongen (geen skip-verify-vlaggen).
 #4.3.5    Niveau: 2    Rol: D/V
 Controleer of AI-infrastructuur draait in toegewijde VPCs/VNets zonder directe internettoegang en communiceert uitsluitend via NAT-gateways of bastion hosts.

---

### C4.4 Geheimen & cryptografisch sleutelbeheer

Bescherm referenties via hardware-backed opslag en automatische rotatie met zero-trust-toegang.

 #4.4.1    Niveau: 1    Rol: D/V
 Controleer of geheimen zijn opgeslagen in HashiCorp Vault, AWS Secrets Manager, Azure Key Vault of Google Secret Manager met AES-256-versleuteling in rust.
 #4.4.2    Niveau: 1    Rol: D/V
 Controleer of cryptografische sleutels worden gegenereerd in FIPS 140-2 Niveau 2 HSM's (AWS CloudHSM, Azure Dedicated HSM) met sleutelrotatie volgens het cryptografisch beleid van de organisatie.
 #4.4.3    Niveau: 2    Rol: D/V
 Verifieer dat de rotatie van geheimen geautomatiseerd is met een implementatie zonder downtime en een onmiddellijke rotatie die wordt geactiveerd door personeelswijzigingen of beveiligingsincidenten.
 #4.4.4    Niveau: 2    Rol: D/V
 Verifieer dat containerafbeeldingen worden gescand met tools (GitLeaks, TruffleHog of detect-secrets) die builds blokkeren waarin API-sleutels, wachtwoorden of certificaten voorkomen.
 #4.4.5    Niveau: 2    Rol: D/V
 Controleer of de toegang tot productiegeheimen MFA vereist met hardwaretokens (YubiKey, FIDO2) en of dit wordt vastgelegd in onveranderlijke auditlogboeken met gebruikersidentiteiten en tijdstempels.
 #4.4.6    Niveau: 2    Rol: D/V
 Controleer of geheimen via Kubernetes-geheimen, gemonteerde volumes of init-containers worden geïnjecteerd en zorg ervoor dat geheimen nooit worden ingebed in omgevingsvariabelen of containerafbeeldingen.

---

### C4.5 AI-werkbelasting sandboxing en validatie

Isoleer onbetrouwbare AI-modellen in veilige sandboxen met een uitgebreide gedragsanalyse.

 #4.5.1    Niveau: 1    Rol: D/V
 Verifieer dat externe AI-modellen worden uitgevoerd in gVisor, microVM's (zoals Firecracker, CrossVM) of Docker-containers met de opties --security-opt=no-new-privileges en --read-only.
 #4.5.2    Niveau: 1    Rol: D/V
 Controleer of sandboxomgevingen geen netwerkconnectiviteit hebben (--network=none) of alleen toegang hebben tot localhost, waarbij alle externe verzoeken door iptables-regels worden geblokkeerd.
 #4.5.3    Niveau: 2    Rol: D/V
 Verifieer dat AI-modelvalidatie geautomatiseerde red-teamtesten omvat met organisatorisch gedefinieerde testdekking en gedragsanalyse voor backdoor-detectie.
 #4.5.4    Niveau: 2    Rol: D/V
 Verifieer dat voordat een AI-model naar productie wordt gepromoveerd, de sandboxresultaten cryptografisch ondertekend zijn door geautoriseerd beveiligingspersoneel en in onveranderlijke auditlogboeken zijn opgeslagen.
 #4.5.5    Niveau: 2    Rol: D/V
 Verifieer dat sandbox-omgevingen tussen evaluaties worden vernietigd en opnieuw aangemaakt uit gouden afbeeldingen met volledige bestandssysteem- en geheugenopruiming.

---

### C4.6 Infrastructuurbeveiligingsbewaking

Infrastructuur continu scannen en monitoren met geautomatiseerde herstelmaatregelen en real-time waarschuwingen.

 #4.6.1    Niveau: 1    Rol: D/V
 Verifieer dat containerafbeeldingen volgens de planning van de organisatie worden gescand, waarbij kritieke kwetsbaarheden de implementatie blokkeren op basis van de risicogrens van de organisatie.
 #4.6.2    Niveau: 1    Rol: D/V
 Verifieer of de infrastructuur voldoet aan CIS Benchmarks of NIST 800-53-beheersmaatregelen met door de organisatie gedefinieerde nalevingsdrempels en geautomatiseerde remediatie voor mislukte controles.
 #4.6.3    Niveau: 2    Rol: D/V
 Controleer dat kwetsbaarheden met een hoge ernst volgens de tijdlijnen van het organisatorische risicobeheer zijn gepatcht, met noodprocedures voor CVEs die actief worden uitgebuit.
 #4.6.4    Niveau: 2    Rol: V
 Controleer of beveiligingswaarschuwingen kunnen integreren met SIEM-platforms (Splunk, Elastic of Sentinel) via CEF- of STIX/TAXII-formaten met geautomatiseerde verrijking.
 #4.6.5    Niveau: 3    Rol: V
 Controleer of infrastructuurmetingen worden geëxporteerd naar monitoringsystemen (Prometheus, DataDog) met SLA-dashboards en managementrapportage.
 #4.6.6    Niveau: 2    Rol: D/V
 Verifieer dat configuratiedrift wordt gedetecteerd met behulp van hulpmiddelen (Chef InSpec, AWS Config) volgens de organisatorische bewakingsvereisten met automatische rollback voor ongeautoriseerde wijzigingen.

---

### C4.7 AI-infrastructuurbronnenbeheer

Voorkom uitputtingsaanvallen op bronnen en zorg voor een eerlijke toewijzing van middelen via quota en bewaking.

 #4.7.1    Niveau: 1    Rol: D/V
 Verifieer dat de GPU/TPU-utilisatie wordt gemonitord met waarschuwingen die bij door de organisatie vastgestelde drempels worden geactiveerd, en dat automatische schaalvergroting of belastingverdeling wordt geactiveerd op basis van beleid voor capaciteitsbeheer.
 #4.7.2    Niveau: 1    Rol: D/V
 Verifieer dat AI-werkbelastingsmetriek(en) volgens de monitoringvereisten van de organisatie worden verzameld en gecorreleerd met de infrastructuurbenutting.
 #4.7.3    Niveau: 2    Rol: D/V
 Controleer of Kubernetes ResourceQuotas of gelijkwaardige mechanismen de individuele workloads beperken volgens het organisatorische beleid voor resource-allocatie, met afdwingbare harde limieten.
 #4.7.4    Niveau: 2    Rol: V
 Controleer of kostenmonitoring de uitgaven per workload/tenant bijhoudt met waarschuwingen op basis van organisatorische budgetdrempels en geautomatiseerde controles voor begrotingsoverschrijdingen.
 #4.7.5    Niveau: 3    Rol: V
 Controleer of capaciteitsplanning historische gegevens gebruikt met door de organisatie gedefinieerde prognoseperiodes en automatische toewijzing van bronnen die gebaseerd is op vraagpatronen.
 #4.7.6    Niveau: 2    Rol: D/V
 Controleer of bronnenuitputting circuit breakers activeert volgens de organisatorische responsvereisten, inclusief rate-limiting op basis van capaciteitsbeleid en werklastisolatie.

---

### C4.8 Omgevingscheiding en Promotiecontroles

Handhaaf strikte omgevingsgrenzen met geautomatiseerde promotiepoorten en beveiligingsvalidatie.

 #4.8.1    Niveau: 1    Rol: D/V
 Verifieer dat de dev/test/prod-omgevingen in afzonderlijke VPCs/VNets draaien zonder gedeelde IAM-rollen, beveiligingsgroepen of netwerkconnectiviteit.
 #4.8.2    Niveau: 1    Rol: D/V
 Verifieer dat de omgevingspromotie goedkeuring vereist van organisatorisch gedefinieerde bevoegde personen met cryptografische handtekeningen en onveranderlijke auditsporen.
 #4.8.3    Niveau: 2    Rol: D/V
 Controleer of productieomgevingen SSH-toegang blokkeren, debug-eindpunten uitschakelen en wijzigingsverzoeken vereisen met organisatorische vereisten voor voorafgaande kennisgeving, behalve in noodgevallen.
 #4.8.4    Niveau: 2    Rol: D/V
 Verifieer dat wijzigingen in infrastructuur-als-code een collegiale beoordeling vereisen met geautomatiseerde tests en beveiligingsscans voordat ze worden samengevoegd in de hoofdbranch.
 #4.8.5    Niveau: 2    Rol: D/V
 Verifieer dat niet-productiegegevens zijn geanonimiseerd volgens de privacy-eisen van de organisatie, synthetische gegevensgeneratie, of volledige gegevensmaskering met PII-verwijdering, en dat dit is geverifieerd.
 #4.8.6    Niveau: 2    Rol: D/V
 Controleer dat promotiepoorten geautomatiseerde beveiligingstests bevatten (SAST, DAST, container scanning) waarbij voor goedkeuring geen kritieke bevindingen vereist zijn.

---

### C4.9 Infrastructuur Back-up & Herstel

Zorg voor de veerkracht van de infrastructuur door middel van geautomatiseerde back-ups, geteste herstelprocedures en rampenherstelcapaciteiten.

 #4.9.1    Niveau: 1    Rol: D/V
 Verifieer of infrastructuurconfiguraties volgens de organisatorische back-upschema's worden geback-upt naar geografisch gescheiden regio's met de 3-2-1-back-upstrategie-implementatie.
 #4.9.2    Niveau: 2    Rol: D/V
 Controleer of backup-systemen draaien in geïsoleerde netwerken met aparte inloggegevens en air-gapped opslag voor ransomwarebescherming.
 #4.9.3    Niveau: 2    Rol: V
 Verifieer dat herstelprocedures worden getest en gevalideerd door middel van geautomatiseerd testen volgens de planningen van de organisatie met RTO- en RPO-doelstellingen die voldoen aan de vereisten van de organisatie.
 #4.9.4    Niveau: 3    Rol: V
 Controleer of rampenherstel AI-specifieke runbooks omvat met herstel van modelgewichten, het opnieuw opbouwen van GPU-clusters en het in kaart brengen van dienstafhankelijkheden.

---

### C4.10 Infrastructuur Naleving & Bestuur

Zorg voor naleving van regelgeving door voortdurende beoordeling, documentatie en geautomatiseerde controles.

 #4.10.1    Niveau: 2    Rol: D/V
 Verifieer dat de naleving van de infrastructuur volgens de organisatorische schema's wordt beoordeeld tegen SOC 2, ISO 27001 of FedRAMP-controles met geautomatiseerde verzameling van bewijsmateriaal.
 #4.10.2    Niveau: 2    Rol: V
 Verifieer of de infrastructuurdocumentatie netwerkdiagrammen, gegevensstroomkaarten en dreigingsmodellen bevat die zijn bijgewerkt volgens de vereisten van organisatorisch verandermanagement.
 #4.10.3    Niveau: 3    Rol: D/V
 Verifieer dat infrastructuurwijzigingen een geautomatiseerde nalevingsimpactbeoordeling ondergaan met regulatoire goedkeuringsworkflows voor wijzigingen met hoog risico.

---

### C4.11 AI-hardwarebeveiliging

Beveilig AI-specifieke hardwarecomponenten, waaronder GPU's, TPU's en gespecialiseerde AI-acceleratoren.

 #4.11.1    Niveau: 2    Rol: D/V
 Controleer of AI-accelerator-firmware (GPU BIOS, TPU-firmware) geverifieerd is met cryptografische handtekeningen en bijgewerkt volgens de patchbeheer-tijdlijnen van de organisatie.
 #4.11.2    Niveau: 2    Rol: D/V
 Verifieer dat vóór de uitvoering van de werkbelasting de integriteit van de AI-accelerator wordt gevalideerd door hardware-attestatie met TPM 2.0, Intel TXT of AMD SVM.
 #4.11.3    Niveau: 2    Rol: D/V
 Verifieer dat het GPU-geheugen geïsoleerd is tussen werkbelastingen met behulp van SR-IOV, MIG (Multi-Instance GPU) of vergelijkbare hardware-partitionering met geheugenreiniging tussen taken.
 #4.11.4    Niveau: 3    Rol: V
 Verifieer dat de AI-hardware-toeleveringsketen herkomstverificatie omvat, met fabrikantcertificaten en tamper-evidente verpakkingsvalidatie.
 #4.11.5    Niveau: 3    Rol: D/V
 Controleer dat hardwarebeveiligingsmodules (HSMs) AI-modelgewichten en cryptografische sleutels beschermen met certificering volgens FIPS 140-2 Niveau 3 of Common Criteria EAL4+.

---

### C4.12 Edge- en gedistribueerde AI-infrastructuur

Veilige gedistribueerde AI-implementaties, inclusief edge computing, federated learning en architecturen op meerdere locaties.

 #4.12.1    Niveau: 2    Rol: D/V
 Verifieer dat edge-AI-apparaten zich authenticeren bij de centrale infrastructuur via wederzijdse TLS (mTLS), met apparaatcertificaten die volgens het beleid voor certificaatbeheer van de organisatie periodiek worden vernieuwd.
 #4.12.2    Niveau: 2    Rol: D/V
 Verifieer dat edge-apparaten Secure Boot implementeren met geverifieerde handtekeningen en rollbackbescherming die firmware-downgrade-aanvallen voorkomt.
 #4.12.3    Niveau: 3    Rol: D/V
 Controleer of de gedistribueerde AI-coördinatie byzantijns fouttolerante consensusalgoritmen gebruikt met deelnemersvalidatie en detectie van kwaadaardige knooppunten.
 #4.12.4    Niveau: 3    Rol: D/V
 Controleer of edge-to-cloud-communicatie bandbreedtebeperking, gegevenscompressie en offline operationele mogelijkheden met beveiligde lokale opslag omvat.

---

### C4.13 Meerdere Cloud-omgevingen en Hybride Infrastructuurbeveiliging

Beveilig AI-workloads over meerdere cloudproviders en hybride cloud-on-premises-implementaties.

 #4.13.1    Niveau: 2    Rol: D/V
 Controleer of multi-cloud AI-implementaties cloud-agnostische identiteitsfederatie (OIDC, SAML) gebruiken met gecentraliseerd beleidsbeheer over aanbieders.
 #4.13.2    Niveau: 2    Rol: D/V
 Verifieer dat cross-cloud gegevensoverdracht end-to-end encryptie gebruikt met door de klant beheerde sleutels en controles voor gegevensresidentie die per rechtsgebied worden afgedwongen.
 #4.13.3    Niveau: 2    Rol: D/V
 Controleer of hybride cloud AI workloads een consistent beveiligingsbeleid implementeren over on-premise en cloudomgevingen met geïntegreerde bewaking en waarschuwingen.
 #4.13.4    Niveau: 3    Rol: V
 Controleer of de voorkoming van leveranciersafhankelijkheid voor cloudomgevingen portabele infrastructuur-als-code, gestandaardiseerde API's en mogelijkheden voor gegevensexport omvat, samen met formaatconversiehulpmiddelen.
 #4.13.5    Niveau: 3    Rol: V
 Controleer of multi-cloud kostenoptimalisatie beveiligingscontroles omvat die zowel resource-sprawl voorkomen als onbevoegde cross-cloud gegevensoverdrachtskosten voorkomen.

---

### C4.14 Infrastructuurautomatisering en GitOps-beveiliging

Beveilig infrastructuurautomatiseringspijplijnen en GitOps-workflows voor AI-infrastructuurbeheer.

 #4.14.1    Niveau: 2    Rol: D/V
 Controleer of GitOps-repositories ondertekende commits met GPG-sleutels vereisen en branchbeschermingsregels die directe pushes naar hoofdbranches voorkomen.
 #4.14.2    Niveau: 2    Rol: D/V
 Controleer of infrastructuurautomatisering driftdetectie omvat met automatische herstelmaatregelen en rollback-mogelijkheden die worden geactiveerd volgens de vereisten voor organisatorische respons op onbevoegde wijzigingen.
 #4.14.3    Niveau: 2    Rol: D/V
 Controleer of de geautomatiseerde provisioning van infrastructuur een validering van beveiligingsbeleid omvat, met blokkering van implementaties voor niet-conforme configuraties.
 #4.14.4    Niveau: 2    Rol: D/V
 Controleer of de geheimen voor infrastructuurautomatisering via externe Secret-Operators (External Secrets Operator, Bank-Vaults) met automatische rotatie worden beheerd.
 #4.14.5    Niveau: 3    Rol: V
 Verifieer dat zelfherstellende infrastructuur correlatie van beveiligingsgebeurtenissen bevat, met geautomatiseerde incidentrespons en workflows voor notificatie aan belanghebbenden.

---

### C4.15 Kwantumresistente infrastructuurbeveiliging

Bereid AI-infrastructuur voor op bedreigingen door kwantumcomputers met post-quantum cryptografie en kwantumbeveiligde protocollen.

 #4.15.1    Niveau: 3    Rol: D/V
 Controleer of de AI-infrastructuur NIST-goedgekeurde post-quantum cryptografische algoritmen (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) implementeert voor sleuteluitwisseling en digitale handtekeningen.
 #4.15.2    Niveau: 3    Rol: D/V
 Controleer of kwantumsleutelverdeling (QKD) systemen zijn geïmplementeerd voor hoogbeveiligde AI-communicatie met kwantumveilige sleutelbeheerprotocollen.
 #4.15.3    Niveau: 3    Rol: D/V
 Controleer of cryptografische wendbaarheidskaders een snelle migratie naar nieuwe post-kwantumalgoritmen mogelijk maken met geautomatiseerde certificaat- en sleutelrotatie.
 #4.15.4    Niveau: 3    Rol: V
 Controleer of kwantumdreigingsmodellering de kwetsbaarheid van AI-infrastructuur voor kwantumaanvallen beoordeelt, met gedocumenteerde migratietijdlijnen en risicobeoordelingen.
 #4.15.5    Niveau: 3    Rol: D/V
 Verifieer dat hybride klassieke-quantum cryptografische systemen meerlaagse beveiliging bieden tijdens de quantumovergangsperiode met prestatiebewaking.

---

### C4.16 Vertrouwelijke Computing & Veilige Enclaves

Bescherm AI-werkbelastingen en modelgewichten met hardwaregebaseerde vertrouwde uitvoeringsomgevingen en vertrouwelijke rekentechnologieën.

 #4.16.1    Niveau: 3    Rol: D/V
 Controleer of gevoelige AI-modellen binnen Intel SGX-enclaves, AMD SEV-SNP of ARM TrustZone worden uitgevoerd met versleuteld geheugen en attestatieverificatie.
 #4.16.2    Niveau: 3    Rol: D/V
 Controleer of vertrouwelijke containers (Kata Containers, gVisor with confidential computing) AI-workloads isoleren met hardware-enforced memory encryption.
 #4.16.3    Niveau: 3    Rol: D/V
 Zorg ervoor dat de afstandsattestatie de enclave-integriteit valideert voordat AI-modellen worden geladen met cryptografisch bewijs van de authenticiteit van een uitvoeringsomgeving.
 #4.16.4    Niveau: 3    Rol: D/V
 Controleer of vertrouwelijke AI-inferentieservices modelextractie voorkomen door middel van versleutelde berekening met verzegelde modelgewichten en beveiligde uitvoering.
 #4.16.5    Niveau: 3    Rol: D/V
 Verifieer dat de orkestratie van een vertrouwde uitvoeringsomgeving (TEE) de levenscyclus van een beveiligde enclave beheert met attestatie op afstand en versleutelde communicatiekanalen.
 #4.16.6    Niveau: 3    Rol: D/V
 Verifieer dat veilige multi-party computation (SMPC) samenwerking bij AI-training mogelijk maakt zonder individuele datasets of modelparameters bloot te geven.

---

### C4.17 Zero-kennis-infrastructuur

Implementeer nulkennisbewijssystemen voor privacybeschermende AI-verificatie en authenticatie zonder gevoelige informatie prijs te geven.

 #4.17.1    Niveau: 3    Rol: D/V
 Controleer of bewijzen met nulkennis (ZK-SNARKs, ZK-STARKs) de integriteit van het AI-model en de herkomst van de trainingsdata verifiëren zonder de gewichten van het model of trainingsgegevens bloot te leggen.
 #4.17.2    Niveau: 3    Rol: D/V
 Controleer of ZK-gebaseerde authenticatiesystemen privacybeschermende gebruikersverificatie voor AI-diensten mogelijk maken zonder identiteitsgerelateerde informatie bekend te maken.
 #4.17.3    Niveau: 3    Rol: D/V
 Verifieer dat private set intersection (PSI) protocollen veilige gegevensvergelijking mogelijk maken voor federated AI zonder individuele datasets bloot te geven.
 #4.17.4    Niveau: 3    Rol: D/V
 Controleer of nulkennis machine learning (ZKML) systemen verifieerbare AI-inferenties mogelijk maken met cryptografisch bewijs van correcte uitvoering.
 #4.17.5    Niveau: 3    Rol: D/V
 Verifieer of ZK-rollups schaalbare, privacy-beschermende AI-transactieverwerking bieden met batchverificatie en verminderde rekenlast.

---

### C4.18 Bescherming tegen side-channel-aanvallen

Bescherm AI-infrastructuur tegen timing-aanvallen, stroomanalyse-aanvallen, elektromagnetische side-channel-aanvallen en cache-gebaseerde side-channel-aanvallen die mogelijk gevoelige informatie kunnen lekken.

 #4.18.1    Niveau: 3    Rol: D/V
 Verifieer dat de AI-inferentietijd genormaliseerd is door middel van algoritmen met constante tijd en padding om tijdsafhankelijke modelextractie-aanvallen te voorkomen.
 #4.18.2    Niveau: 3    Rol: D/V
 Controleer of bescherming tegen stroomanalyse ruisinjectie, filtratie van voedingslijnen en gerandomiseerde uitvoeringspatronen voor AI-hardware omvat.
 #4.18.3    Niveau: 3    Rol: D/V
 Controleer of de cache-gebaseerde mitigatie van zijkanalen gebruikmaakt van cache-partitionering, randomisatie en flush-instructies om informatielekken te voorkomen.
 #4.18.4    Niveau: 3    Rol: D/V
 Controleer of elektromagnetische emanatiebescherming afscherming, signaalfilters en gerandomiseerde verwerking omvat om TEMPEST-achtige aanvallen te voorkomen.
 #4.18.5    Niveau: 3    Rol: D/V
 Controleer of microarchitecturale zijkanalverdedigingen onder andere controles op speculatieve uitvoering en obfuscatie van geheugentoegangspatronen bevatten.

---

### C4.19 Neuromorfische & Gespecialiseerde AI-hardwarebeveiliging

Beveilig opkomende AI-hardwarearchitecturen, waaronder neuromorfe chips, FPGAs, op maat gemaakte ASICs en optische rekensystemen.

 #4.19.1    Niveau: 3    Rol: D/V
 Controleer of de beveiliging van neuromorfische chips versleuteling van spikepatronen, bescherming van synaptische gewichten en hardware-gebaseerde validatie van leerregels omvat.
 #4.19.2    Niveau: 3    Rol: D/V
 Verifieer dat FPGA-gebaseerde AI-accelerators bitstream-encryptie, anti-tamper-mechanismen en veilige configuratie-inladen met geauthenticeerde updates implementeren.
 #4.19.3    Niveau: 3    Rol: D/V
 Verifieer dat maatwerk-ASIC-beveiliging on-chip beveiligingsprocessoren, hardware-root of trust en veilige sleutelopslag met tamperdetectie omvat.
 #4.19.4    Niveau: 3    Rol: D/V
 Controleer of optische computersystemen kwantumveilige optische encryptie, veilige fotonische schakeling en beschermde optische signaalverwerking implementeren.
 #4.19.5    Niveau: 3    Rol: D/V
 Controleer of hybride analoog-digitaal AI-chips veilige analoge berekeningen bevatten, beschermde gewichtsopslag hebben en geauthenticeerde analoog-naar-digitaal-conversie ondersteunen.

---

### C4.20 Privacy-Beschermende Rekeninfrastructuur

Implementeer infrastructuurcontroles voor privacybeschermende berekeningen om gevoelige gegevens te beschermen tijdens AI-verwerking en analyse.

 #4.20.1    Niveau: 3    Rol: D/V
 Controleer of infrastructuur voor homomorfische encryptie versleutelde berekeningen op gevoelige AI-werkbelastingen mogelijk maakt met cryptografische integriteitsverificatie en prestatemonitoring.
 #4.20.2    Niveau: 3    Rol: D/V
 Verifieer dat privé-informatieopvragsystemen databasequery's mogelijk maken zonder querypatronen prijs te geven, met cryptografische bescherming van toegangspatronen.
 #4.20.3    Niveau: 3    Rol: D/V
 Verifieer dat veilige MPC-protocollen privacybeschermende AI-inferentie mogelijk maken zonder de individuele invoer of tussenliggende berekeningen bloot te leggen.
 #4.20.4    Niveau: 3    Rol: D/V
 Verifieer dat privacybeschermend sleutelbeheer gedistribueerde sleutelgeneratie, drempelcryptografie en veilige sleutelrotatie met hardware-ondersteunde bescherming omvat.
 #4.20.5    Niveau: 3    Rol: D/V
 Controleer of de prestaties van privacybeschermende berekeningen zijn geoptimaliseerd door batchverwerking, caching en hardwareversnelling, terwijl de cryptografische beveiligingsgaranties behouden blijven.

---

### C4.15 Agent Framework Cloud Integratie Beveiliging & Hybride Implementatie

Beveiligingscontroles voor cloud-geïntegreerde agentframeworks met hybride on-premises/cloud-architecturen.

 #4.15.1    Niveau: 1    Rol: D/V
 Verifieer of de cloudopslagintegratie gebruikmaakt van end-to-end encryptie met agentgestuurd sleutelbeheer.
 #4.15.2    Niveau: 2    Rol: D/V
 Verifieer of de beveiligingsgrenzen van een hybride implementatie duidelijk zijn gedefinieerd met versleutelde communicatiekanalen.
 #4.15.3    Niveau: 2    Rol: D/V
 Controleer of de toegang tot cloudbronnen zero-trust-verificatie omvat met continue authenticatie.
 #4.15.4    Niveau: 3    Rol: D/V
 Verifieer dat de vereisten voor gegevensresidentie worden afgedwongen door cryptografische attestatie van opslaglocaties.
 #4.15.5    Niveau: 3    Rol: D/V
 Verifieer dat de beveiligingsbeoordelingen van de cloudprovider agent-specifieke dreigingsmodellering en risicobeoordeling bevatten.

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

## C5 Toegangscontrole en Identiteit voor AI-componenten en Gebruikers

### Beheersdoel

Effectieve toegangscontrole voor AI-systemen vereist robuust identiteitsbeheer, contextbewuste autorisatie en runtime-handhaving volgens de principes van zero-trust. Deze controles zorgen ervoor dat mensen, diensten en autonome agenten alleen interageren met modellen, gegevens en rekenbronnen binnen expliciet toegekende toegangsrechten, met voortdurende verificatie- en auditmogelijkheden.

---

### C5.1 Identiteitsbeheer en authenticatie

Implementeer cryptografisch onderbouwde identiteiten voor alle entiteiten met multifactorauthenticatie voor bevoorrechte operaties.

 #5.1.1    Niveau: 1    Rol: D/V
 Controleer dat alle menselijke gebruikers en service principals zich authenticeren via een gecentraliseerde ondernemingsidentiteitsprovider (IdP) die OIDC/SAML-protocollen gebruikt, met unieke koppelingen tussen identiteit en token (geen gedeelde accounts of inloggegevens).
 #5.1.2    Niveau: 1    Rol: D/V
 Verifieer dat operaties met hoog risico (modeluitrol, gewichtsexport, toegang tot trainingsgegevens, wijzigingen in productieconfiguratie) multifactorauthenticatie of stap-gewijze authenticatie met sessie-herverificatie vereisen.
 #5.1.3    Niveau: 2    Rol: D
 Verifieer dat nieuwe entiteiten een identiteitsverificatie ondergaan die is afgestemd op NIST 800-63-3 IAL-2 of vergelijkbare standaarden, voordat zij toegang krijgen tot het productiesysteem.
 #5.1.4    Niveau: 2    Rol: V
 Controleer of toegangsbeoordelingen elk kwartaal worden uitgevoerd met geautomatiseerde detectie van inactieve accounts, afdwinging van rotatie van referenties en workflows voor deprovisioning.
 #5.1.5    Niveau: 3    Rol: D/V
 Verifieer dat gefedereerde AI-agenten zich authenticeren via ondertekende JWT-verklaringen die een maximale geldigheidsduur van 24 uur hebben en cryptografisch bewijs van oorsprong bevatten.

---

### C5.2 Middelenautorisatie & Minimale toegangsrechten

Implementeer granulaire toegangscontroles voor alle AI-bronnen met expliciete machtigingsmodellen en auditsporen.

 #5.2.1    Niveau: 1    Rol: D/V
 Controleer of elke AI-bron (datasets, modellen, eindpunten, vectorverzamelingen, embedding-indexen, compute-instanties) rolgebaseerde toegangscontroles afdwingt met expliciete toestemmingslijsten en standaard-weigeringsbeleid.
 #5.2.2    Niveau: 1    Rol: D/V
 Controleer dat het principe van minimale rechten standaard wordt toegepast, met service-accounts die beginnen bij alleen-lezen machtigingen en dat voor schrijftoegang een gedocumenteerde zakelijke rechtvaardiging vereist is.
 #5.2.3    Niveau: 1    Rol: V
 Verifieer dat alle wijzigingen in toegangscontrole zijn gekoppeld aan goedgekeurde wijzigingsverzoeken en onveranderlijk worden vastgelegd met tijdstempels, identiteiten van acteurs, resource-identificatoren en rechtenwijzigingen.
 #5.2.4    Niveau: 2    Rol: D
 Verifieer dat gegevensclassificatielabels (PII, PHI, export-controlled, proprietary) automatisch doorstromen naar afgeleide bronnen (embeddings, prompt caches, modeluitgangen) met consistente beleidshandhaving.
 #5.2.5    Niveau: 2    Rol: D/V
 Verifieer dat onbevoegde toegangspogingen en privilege-escalatiegebeurtenissen real-time waarschuwingen activeren met contextuele metadata naar SIEM-systemen binnen 5 minuten.

---

### C5.3 Dynamische beleidsbeoordeling

Implementeer attribuut-gebaseerde toegangscontrole (ABAC) engines voor context-gevoelige autorisatiebeslissingen met auditmogelijkheden.

 #5.3.1    Niveau: 1    Rol: D/V
 Controleer of autorisatiebeslissingen extern worden ondergebracht bij een toegewijde beleidsmotor (OPA, Cedar, of een gelijkwaardige oplossing) die toegankelijk is via geauthenticeerde API's met cryptografische integriteitsbescherming.
 #5.3.2    Niveau: 1    Rol: D/V
 Verifieer dat beleidsregels dynamische attributen tijdens uitvoering evalueren, inclusief gebruikerstoegangsniveau, classificatie van de gevoeligheid van bronnen, verzoekcontext, tenant-isolatie en tijdgebonden beperkingen.
 #5.3.3    Niveau: 2    Rol: D
 Verifieer dat beleidsdefinities onder versiebeheer staan, door vakgenoten beoordeeld zijn en gevalideerd worden via geautomatiseerd testen in CI/CD-pijplijnen vóór productie-uitrol.
 #5.3.4    Niveau: 2    Rol: V
 Verifieer dat de resultaten van de beleidsbeoordeling gestructureerde besluitvormingsredenen bevatten en dat deze worden verzonden naar SIEM-systemen voor correlatieanalyse en conformiteitsrapportage.
 #5.3.5    Niveau: 3    Rol: D/V
 Controleer dat de TTL-waarden van de beleid-cache niet hoger zijn dan 5 minuten voor bronnen met hoge gevoeligheid en 1 uur voor standaardbronnen met cache-invalidatiecapaciteiten.

---

### C5.4 Query-Tijd Beveiligingsafdwinging

Implementeer beveiligingscontroles op database-layer met verplichte filtering en rijniveau-beveiligingsbeleid.

 #5.4.1    Niveau: 1    Rol: D/V
 Verifieer dat alle vector-databases en SQL-query's verplichte beveiligingsfilters bevatten (tenant-ID, sensitiviteitslabels, gebruikersreikwijdte) die op het niveau van de database-engine worden gehandhaafd, niet in de applicatiecode.
 #5.4.2    Niveau: 1    Rol: D/V
 Controleer of RLS-beleidslijnen en veldniveau-maskering zijn ingeschakeld met beleidsovererving voor alle vectordatabases, zoekindexen en trainingsdatasets.
 #5.4.3    Niveau: 2    Rol: D
 Verifieer dat mislukte autorisatie-evaluaties voorkomen dat 'verwarde plaatsvervanger-aanvallen' optreden door queries onmiddellijk af te breken en expliciete autorisatiefoutcodes terug te geven in plaats van lege resultsets.
 #5.4.4    Niveau: 2    Rol: V
 Controleer of de latentie bij beleidsbeoordeling continu wordt gemonitord met geautomatiseerde meldingen voor time-outcondities die autorisatie-omzeiling mogelijk kunnen maken.
 #5.4.5    Niveau: 3    Rol: D/V
 Controleer of query-herhaalmechanismen het autorisatiebeleid opnieuw evalueren om rekening te houden met dynamische machtigingswijzigingen tijdens actieve gebruikerssessies.

---

### C5.5 Uitvoerfiltering & Gegevensverliespreventie

Implementeer nabewerkingcontroles om ongeautoriseerde blootstelling van gegevens te voorkomen in door kunstmatige intelligentie gegenereerde inhoud.

 #5.5.1    Niveau: 1    Rol: D/V
 Controleer of de na-inferentiefilters ongeautoriseerde PII, geclassificeerde informatie en eigen gegevens scannen en redigeren voordat de inhoud aan verzoekers wordt geleverd.
 #5.5.2    Niveau: 1    Rol: D/V
 Verifieer dat citaten, referenties en bronvermeldingen in de uitvoer van het model worden gevalideerd tegen de rechten van de aanroeper en verwijderd indien ongeautoriseerde toegang wordt gedetecteerd.
 #5.5.3    Niveau: 2    Rol: D
 Controleer of de beperkingen op uitvoerformaten (geschoonde PDF's, afbeeldingen zonder metadata, goedgekeurde bestandstypen) worden gehandhaafd op basis van de machtigingsniveaus van gebruikers en gegevensclassificaties.
 #5.5.4    Niveau: 2    Rol: V
 Verifieer dat anonimisering-algoritmen deterministisch zijn, onder versiecontrole staan, en auditlogs bijhouden ter ondersteuning van nalevingsonderzoeken en forensische analyse.
 #5.5.5    Niveau: 3    Rol: V
 Controleer of hoog-risico-redactiegebeurtenissen adaptieve logbestanden genereren die cryptografische hash-waarden van de oorspronkelijke inhoud bevatten voor forensisch terugvinden zonder gegevensblootstelling.

---

### C5.6 Multi-Tenant Isolatie

Zorg voor cryptografische en logische isolatie tussen huurders in een gedeelde AI-infrastructuur.

 #5.6.1    Niveau: 1    Rol: D/V
 Verifieer dat geheugenruimten, embedding-opslagen, cache-items en tijdelijke bestanden per tenant zijn gescheiden in namespaces en dat ze bij tenantverwijdering of sessiebeëindiging veilig worden gewist.
 #5.6.2    Niveau: 1    Rol: D/V
 Controleer dat elke API-aanvraag een geauthenticeerde tenant-id bevat die cryptografisch wordt gevalideerd tegen de sessiecontext en de rechten van de gebruiker.
 #5.6.3    Niveau: 2    Rol: D
 Verifieer dat netwerkbeleid standaard-deny-regels implementeert voor communicatie tussen tenants binnen servicemeshes en containerorkestratieplatforms.
 #5.6.4    Niveau: 3    Rol: D
 Verifieer dat versleutelingssleutels per huurder uniek zijn, met ondersteuning voor klant-beheerde sleutels (CMK) en cryptografische isolatie tussen huurdersgegevensopslagen.

---

### C5.7 Autonome agentmachtiging

Beheer machtigingen voor AI-agenten en autonome systemen via afgebakende bevoegdheidstokens en doorlopende autorisatie.

 #5.7.1    Niveau: 1    Rol: D/V
 Controleer dat autonome agenten omschreven machtigingstokens ontvangen die expliciet de toegestane acties, toegankelijke bronnen, tijdslimieten en operationele beperkingen specificeren.
 #5.7.2    Niveau: 1    Rol: D/V
 Verifieer dat hoogrisico-mogelijkheden (toegang tot het bestandssysteem, code-uitvoering, externe API-aanroepen, financiële transacties) standaard zijn uitgeschakeld en expliciete autorisaties vereisen voor activatie met zakelijke rechtvaardigingen.
 #5.7.3    Niveau: 2    Rol: D
 Verifieer dat capability tokens aan gebruikerssessies zijn gebonden, cryptografische integriteitsbescherming bieden en voorkomen dat ze worden opgeslagen of hergebruikt in offline scenario's.
 #5.7.4    Niveau: 2    Rol: V
 Verifieer dat acties die door een agent zijn geïnitieerd onderworpen zijn aan secundaire autorisatie via de ABAC-beleidsmotor met volledige contextevaluatie en auditlogging.
 #5.7.5    Niveau: 3    Rol: V
 Verifieer dat de foutcondities van de agent en de foutafhandeling informatie bevatten over de reikwijdte van de mogelijkheden ter ondersteuning van incidentanalyse en forensisch onderzoek.

---

### Referenties

#### Standaarden & Raamwerken

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

## C6 Beveiliging van de toeleveringsketen voor Modellen, Frameworks en Data

### Beheersdoel

AI‑toeleveringsketen‑aanvallen misbruiken modellen, raamwerken of datasets van derden om achterdeuren, bias of exploitbare code in te bouwen. Deze controles bieden end‑to‑end herkomstregistratie, kwetsbaarheidsbeheer en monitoring om de hele modellevenscyclus te beschermen.

---

### C6.1 Voorafgetraind modelkeuring en provenantie

Beoordeel en authenticeer de oorsprongen van derde‑partijmodellen, licenties en verborgen gedragingen, vóór enige fijn‑afstemming of uitrol.

 #6.1.1    Niveau: 1    Rol: D/V
 Verifieer dat elk modelartefact van derden een ondertekend provenance-record bevat dat de bronrepository en de commit-hash identificeert.
 #6.1.2    Niveau: 1    Rol: D/V
 Verifieer dat modellen vóór importeren worden gescand op kwaadaardige lagen of Trojaanse triggers met behulp van geautomatiseerde tools.
 #6.1.3    Niveau: 2    Rol: D
 Verifieer dat transfer-learning fijn-tunen een adversariële evaluatie doorstaat om verborgen gedragingen te detecteren.
 #6.1.4    Niveau: 2    Rol: V
 Verifieer of modellicenties, exportcontrole-tags en data-origin-verklaringen zijn vastgelegd in een ML‑BOM‑vermelding.
 #6.1.5    Niveau: 3    Rol: D/V
 Controleer of hoog-risico-modellen (openbaar geüploade gewichten, niet-geverifieerde makers) in quarantaine blijven totdat menselijke beoordeling en ondertekening plaatsvinden.

---

### C6.2 Raamwerk & Bibliotheekscan

Blijf voortdurend ML-frameworks en bibliotheken scannen op CVEs en kwaadaardige code om de runtime-stack veilig te houden.

 #6.2.1    Niveau: 1    Rol: D/V
 Controleer of CI-pijplijnen afhankelijkheids-scanners uitvoeren op AI-frameworks en kritieke bibliotheken.
 #6.2.2    Niveau: 1    Rol: D/V
 Controleer of kritieke kwetsbaarheden (CVSS ≥ 7.0) de promotie naar productie-afbeeldingen blokkeren.
 #6.2.3    Niveau: 2    Rol: D
 Verifieer of de statische code-analyse draait op geforkte of meegeleverde ML-bibliotheken.
 #6.2.4    Niveau: 2    Rol: V
 Verifieer dat voorstellen voor framework-upgrades beveiligingsimpactanalyses bevatten die verwijzen naar openbare CVE-feeds.
 #6.2.5    Niveau: 3    Rol: V
 Verifieer dat runtime-sensoren waarschuwen bij onverwacht laden van dynamische bibliotheken die afwijken van de ondertekende SBOM.

---

### C6.3 Afhankelijkheden Vastzetten & Verificatie

Zet elke afhankelijkheid vast met onveranderlijke digests en maak builds reproduceerbaar om identieke, tamper-vrije artefacten te garanderen.

 #6.3.1    Niveau: 1    Rol: D/V
 Verifieer dat alle pakketbeheerders versiepinning afdwingen via lockfiles.
 #6.3.2    Niveau: 1    Rol: D/V
 Verifieer dat onveranderlijke digests worden gebruikt in plaats van veranderlijke tags in containerreferenties.
 #6.3.3    Niveau: 2    Rol: D
 Verifieer dat reproduceerbaar‑build-controles hashes vergelijken tussen CI runs om identieke uitvoer te garanderen.
 #6.3.4    Niveau: 2    Rol: V
 Verifieer dat build-attestaties gedurende 18 maanden worden bewaard voor audittraceerbaarheid.
 #6.3.5    Niveau: 3    Rol: D
 Verifieer dat verlopen afhankelijkheden automatische PRs activeren om gepinde versies bij te werken of te forken.

---

### C6.4 Handhaving van vertrouwde bronnen

Sta downloads van artefacten alleen toe vanaf cryptografisch geverifieerde, door de organisatie goedgekeurde bronnen en blokkeer alles wat niet uit deze bronnen komt.

 #6.4.1    Niveau: 1    Rol: D/V
 Verifieer dat modelgewichten, datasets en containers uitsluitend van goedgekeurde domeinen of interne registries worden gedownload.
 #6.4.2    Niveau: 1    Rol: D/V
 Controleer of Sigstore/Cosign-handtekeningen de identiteit van de uitgever valideren voordat artefacten lokaal in de cache worden opgeslagen.
 #6.4.3    Niveau: 2    Rol: D
 Controleer of uitgaande proxies niet-geauthenticeerde artefact-downloads blokkeren om het beleid voor vertrouwde bronnen af te dwingen.
 #6.4.4    Niveau: 2    Rol: V
 Controleer of repository allow‑lists elk kwartaal worden herzien met bewijs van zakelijke rechtvaardiging voor elke invoer.
 #6.4.5    Niveau: 3    Rol: V
 Controleer of beleidsinbreuken ervoor zorgen dat artefacten in quarantaine worden geplaatst en dat afhankelijke pipeline-uitvoeringen worden teruggedraaid.

---

### C6.5 Derdepartij‑dataset Risicobeoordeling

Externe datasets evalueren op data-poisoning, bias en wettelijke naleving, en ze gedurende hun hele levenscyclus monitoren.

 #6.5.1    Niveau: 1    Rol: D/V
 Controleer dat externe datasets een risicoscore voor poisoning-aanvallen ondergaan (bijv. datavingerafdrukken, detectie van uitschieters).
 #6.5.2    Niveau: 1    Rol: D
 Controleer of biasmetingen (demografische pariteit, gelijke kansen) worden berekend voordat de dataset wordt goedgekeurd.
 #6.5.3    Niveau: 2    Rol: V
 Controleer of de herkomst en licentievoorwaarden voor datasets zijn vastgelegd in ML‑BOM‑vermeldingen.
 #6.5.4    Niveau: 2    Rol: V
 Controleer of periodieke bewaking datadrift of gegevenscorruptie in gehoste datasets detecteert.
 #6.5.5    Niveau: 3    Rol: D
 Controleer of verboden inhoud (auteursrechtelijk beschermd materiaal, PII) wordt verwijderd via geautomatiseerd opschonen van gegevens vóór training.

---

### C6.6 Toeleveringsketen-aanvalbewaking

Detecteer vroegtijdig dreigingen in de toeleverings‑keten via CVE-feeds, audit‑log analyses en red‑team simulaties.

 #6.6.1    Niveau: 1    Rol: V
 Verifieer dat CI/CD-auditlogboeken naar SIEM-detecties stromen voor anomale pakketdownloads of gemanipuleerde build-stappen.
 #6.6.2    Niveau: 2    Rol: D
 Controleer of incidentresponsiehandleidingen terugzettingsprocedures bevatten voor gecompromitteerde modellen of bibliotheken.
 #6.6.3    Niveau: 3    Rol: V
 Verifieer of dreigingsinformatie‑verrijking ML‑specifieke indicatoren tagt (bijv. model‑poisoning IoCs) in alert triage.

---

### C6.7 ML‑BOM voor modelartefacten

Genereer en onderteken gedetailleerde ML-specifieke SBOMs (ML‑BOMs) zodat downstream-gebruikers de integriteit van componenten tijdens de uitrol kunnen verifiëren.

 #6.7.1    Niveau: 1    Rol: D/V
 Verifieer dat elk modelartefact een ML‑BOM publiceert die datasets, gewichten, hyperparameters en licenties vermeldt.
 #6.7.2    Niveau: 1    Rol: D/V
 Verifieer of ML‑BOM-generatie en Cosign-handtekening in CI automatisch verlopen en voor het samenvoegen vereist zijn.
 #6.7.3    Niveau: 2    Rol: D
 Verifieer of ML‑BOM‑volledigheidscontroles ervoor zorgen dat de build faalt als er metadata voor een component ontbreekt (hash, licentie).
 #6.7.4    Niveau: 2    Rol: V
 Controleer of downstream-consumenten via een API ML-BOMs kunnen opvragen om geïmporteerde modellen tijdens de uitrol te valideren.
 #6.7.5    Niveau: 3    Rol: V
 Verifieer of ML‑BOMs onder versiebeheer staan en met diff worden vergeleken om ongeautoriseerde wijzigingen op te sporen.

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

## C7 Modelgedrag, Uitvoercontrole & Veiligheidsborging

### Beheersdoel

Modeluitvoer moet gestructureerd, betrouwbaar, veilig, uitlegbaar en continu bewaakt in productie zijn. Dit vermindert hallucinaties, privacylekken, schadelijke inhoud en uit de hand lopende acties, terwijl het het vertrouwen van gebruikers vergroot en de naleving van regelgeving bevordert.

---

### C7.1 Handhouding van het uitvoerformaat

Strikte schema's, afgebakende decodering en downstream-validatie voorkomen dat misvormde of kwaadaardige inhoud zich verspreidt.

 #7.1.1    Niveau: 1    Rol: D/V
 Controleer of antwoordschema's (bijv. JSON Schema) in de systeemprompt zijn opgenomen en of elke uitvoer automatisch wordt gevalideerd; niet-conforme uitvoer leidt tot herstel of afwijzing.
 #7.1.2    Niveau: 1    Rol: D/V
 Controleer of beperkte decodering (stoptekens, regex, max-tokens) is ingeschakeld om overflow of prompt-injectie side-kanalen te voorkomen.
 #7.1.3    Niveau: 2    Rol: D/V
 Controleer dat downstream-componenten de uitvoer als onbetrouwbaar beschouwen en deze valideren tegen schema's of injectie-veilige deserialisatoren.
 #7.1.4    Niveau: 3    Rol: V
 Controleer of onjuiste uitvoergebeurtenissen gelogd worden, rate-limited zijn en aan de monitoring worden weergegeven.

---

### C7.2 Hallucinatie-detectie en Mitigatie

Onzekerheidsinschatting en terugvalstrategieën beperken verzonnen antwoorden.

 #7.2.1    Niveau: 1    Rol: D/V
 Verifieer dat token-niveau log-waarschijnlijkheden, ensemble-zelfconsistentie en fijn afgestelde hallucinatie-detectoren aan elk antwoord een vertrouwensscore toekennen.
 #7.2.2    Niveau: 1    Rol: D/V
 Verifieer of reacties onder een configureerbare betrouwbaarheidsdrempel fallback-workflows activeren (bijv. retrieval-augmented generation, secondary model, of menselijke beoordeling).
 #7.2.3    Niveau: 2    Rol: D/V
 Controleer of hallucinatie-incidenten zijn gelabeld met hoofdoorzaak-metadata en doorgegeven aan post-mortem en finetuning-pijplijnen.
 #7.2.4    Niveau: 3    Rol: D/V
 Controleer of de drempels en detectoren na grote model- en kennisbankupdates opnieuw gekalibreerd worden.
 #7.2.5    Niveau: 3    Rol: V
 Controleer of dashboardvisualisaties de hallucinatiepercentages bijhouden.

---

### C7.3 Uitvoerveiligheid & privacyfiltrering

Beleidsfilters en red-team-dekking beschermen gebruikers en vertrouwelijke gegevens.

 #7.3.1    Niveau: 1    Rol: D/V
 Verifieer dat voor- en post-generatie-classificatiemodellen inhoud die haat, intimidatie, zelfbeschadiging, extremisme en seksueel expliciete inhoud blokkeren in overeenstemming met het beleid.
 #7.3.2    Niveau: 1    Rol: D/V
 Controleer of PII/PCI-detectie en automatische redactie bij elke reactie worden uitgevoerd; overtredingen leiden tot een privacy-incident.
 #7.3.3    Niveau: 2    Rol: D
 Controleer of vertrouwelijkheidslabels (bijv. bedrijfsgeheimen) zich verspreiden over modaliteiten om lekkage in tekst, afbeeldingen of code te voorkomen.
 #7.3.4    Niveau: 3    Rol: D/V
 Controleer of pogingen tot omzeiling van filters of classificaties met een hoog risico een tweede goedkeuring of her-authenticatie door de gebruiker vereisen.
 #7.3.5    Niveau: 3    Rol: D/V
 Verifieer dat de filterdrempels rekening houden met de wettelijke rechtsgebieden en met de context van de leeftijd/rol van de gebruiker.

---

### C7.4 Uitvoer en Actiebeperking

Ratelimieten en goedkeuringspoorten voorkomen misbruik en overmatige autonomie.

 #7.4.1    Niveau: 1    Rol: D
 Verifieer of de quota's per-gebruiker en per-API-sleutel het aantal verzoeken, tokens en kosten beperken, met exponentiële back-off bij 429-fouten.
 #7.4.2    Niveau: 1    Rol: D/V
 Controleer of bevoorrechte acties (bestandsschrijven, code-uitvoering, netwerkoproepen) een goedkeuringsproces op basis van beleid of menselijke tussenkomst vereisen.
 #7.4.3    Niveau: 2    Rol: D/V
 Controleer dat crossmodale consistentiecontroles ervoor zorgen dat afbeeldingen, code en tekst die voor hetzelfde verzoek zijn gegenereerd, niet kunnen worden gebruikt om kwaadaardige inhoud te smokkelen.
 #7.4.4    Niveau: 2    Rol: D
 Verifieer dat de diepte van agentendelegatie, recursielimieten en toegestane hulpmiddelenlijsten expliciet zijn geconfigureerd.
 #7.4.5    Niveau: 3    Rol: V
 Verifieer dat overtreding van limieten gestructureerde beveiligingsgebeurtenissen genereert voor SIEM-ingestie.

---

### C7.5 Uitvoer Uitlegbaarheid

Transparante signalen vergroten het gebruikersvertrouwen en de interne foutopsporing.

 #7.5.1    Niveau: 2    Rol: D/V
 Verifieer of aan de gebruiker getoonde vertrouwensscores of beknopte redeneringssamenvattingen worden weergegeven wanneer de risicobeoordeling dit passend acht.
 #7.5.2    Niveau: 2    Rol: D/V
 Controleer of gegenereerde verklaringen geen gevoelige systeemprompts of bedrijfseigen gegevens prijsgeven.
 #7.5.3    Niveau: 3    Rol: D
 Zorg ervoor dat het systeem token-niveau log-probabiliteiten of aandachtkaarten vastlegt en deze opslaat voor geautoriseerde inspectie.
 #7.5.4    Niveau: 3    Rol: V
 Controleer of verklaarbaarheidsartefacten onder versiebeheer staan naast modelreleases voor auditabiliteit.

---

### C7.6 Monitoring-integratie

Observability in realtime sluit de lus tussen ontwikkeling en productie.

 #7.6.1    Niveau: 1    Rol: D
 Controleer of de metriek(en) (schema-overtredingen, hallucinatiepercentage, toxiciteit, PII-lekken, latentie, kosten) naar een centraal bewakingsplatform stromen.
 #7.6.2    Niveau: 1    Rol: V
 Verifieer dat voor elke veiligheidsmetriek waarschuwingsdrempels zijn gedefinieerd, met escalatiepaden voor de dienstdoende operationele staf.
 #7.6.3    Niveau: 2    Rol: V
 Verifieer dat dashboards uitvoerafwijkingen correleren met model/versie, feature-vlag, en upstream-gegevenswijzigingen.
 #7.6.4    Niveau: 2    Rol: D/V
 Verifieer of monitoringgegevens terugkoppelen naar retraining, fine-tuning of regelupdates binnen een gedocumenteerde MLOps-workflow mogelijk is.
 #7.6.5    Niveau: 3    Rol: V
 Verifieer dat monitoringpijplijnen aan penetratietests zijn onderworpen en onder toegangscontrole staan om lekken van gevoelige logbestanden te voorkomen.

---

### 7.7 Generatieve media-waarborgen

Zorg ervoor dat AI-systemen geen illegale, schadelijke of ongeautoriseerde media-inhoud genereren door beleidsbeperkingen af te dwingen, uitvoervalidatie te implementeren en traceerbaarheid te waarborgen.

 #7.7.1    Niveau: 1    Rol: D/V
 Controleer of systeemprompts en gebruikersinstructies uitdrukkelijk verbieden het genereren van illegale, schadelijke of zonder toestemming gemaakte deepfake-media (bijv. afbeeldingen, video’s, audio).
 #7.7.2    Niveau: 2    Rol: D/V
 Controleer of prompts gefilterd worden op pogingen om personen te impersoneren, seksueel expliciete deepfakes te genereren, of media die echte personen zonder toestemming tonen.
 #7.7.3    Niveau: 2    Rol: V
 Controleer of het systeem gebruikmaakt van perceptuele hashing, watermerkdetectie of fingerprinting om ongeautoriseerde reproductie van auteursrechtelijk beschermd materiaal te voorkomen.
 #7.7.4    Niveau: 3    Rol: D/V
 Verifieer dat alle gegenereerde media cryptografisch ondertekend zijn, watermerken bevatten, of voorzien zijn van tamperbestendige herkomstmetadata voor downstream traceerbaarheid.
 #7.7.5    Niveau: 3    Rol: V
 Controleer dat omzeilpogingen (bijv. prompt-obfuscatie, slang, adversariële formuleringen) worden gedetecteerd, gelogd en rate-limiting toegepast; herhaald misbruik wordt gemeld bij monitoringsystemen.

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

### Beheersdoel

Embeddings en vectoropslagen fungeren als het "live geheugen" van hedendaagse AI-systemen, die continu door gebruikers aangeleverde data accepteren en deze via Retrieval-Augmented Generation (RAG) terugbrengen in modelcontexten. Als dit geheugen niet wordt beheerd, kan persoonlijke identificeerbare informatie (PII) lekken, toestemming schenden, of worden omgekeerd om de oorspronkelijke tekst te reconstrueren. Het doel van deze controlefamilie is om geheugenpijplijnen en vectordatabanken te verharden, zodat de toegang gebaseerd is op het principe van minimale rechten, embeddings privacybeschermend zijn, opgeslagen vectoren verlopen of op verzoek kunnen worden ingetrokken, en per-gebruiker geheugen nooit de prompts of voltooiingen van een andere gebruiker besmet.

---

### C8.1 Toegangscontroles op Geheugen & RAG-indexen

Handhaaf fijnmazige toegangscontroles op elke vectorverzameling.

 #8.1.1    Niveau: 1    Rol: D/V
 Verifieer dat rij-/naamruimte-niveau toegangscontroleregels de insert, delete en query-operaties beperken per huurder, collectie of documenttag.
 #8.1.2    Niveau: 1    Rol: D/V
 Controleer of API-sleutels of JWTs scope-claims bevatten (bijv. collectie-ID's, actie-werkwoorden) en minstens elk kwartaal worden geroteerd.
 #8.1.3    Niveau: 2    Rol: D/V
 Controleer of privilege-escalatiepogingen (bijv. similariteitsquery's tussen naamruimtes) binnen 5 minuten worden gedetecteerd en in een SIEM worden gelogd.
 #8.1.4    Niveau: 2    Rol: D/V
 Controleer of de auditlog van de vector-databank de velden subject-identificator, operatie, vector-ID/naamruimte, similariteitsdrempel en aantal resultaten bevat.
 #8.1.5    Niveau: 3    Rol: V
 Verifieer dat toegangsbeslissingen worden getest op omzeilingsfouten telkens wanneer engines worden bijgewerkt of index-sharding regels wijzigen.

---

### C8.2 Embedding sanitatie & validatie

Tekst vooraf controleren op persoonlijk identificeerbare informatie (PII), redigeren of pseudonimiseren voordat vectorisatie plaatsvindt, en optioneel embeddings achteraf verwerken om resterende signalen te verwijderen.

 #8.2.1    Niveau: 1    Rol: D/V
 Verifieer dat persoonsidentificeerbare informatie (PII) en gereguleerde gegevens worden gedetecteerd via geautomatiseerde classificatoren en vóór de embedding gemaskeerd, getokeniseerd of verwijderd.
 #8.2.2    Niveau: 1    Rol: D
 Verifieer dat embedding-pijplijnen invoer afwijzen of in quarantaine plaatsen die uitvoerbare code bevatten of niet-UTF-8 artefacten die de index kunnen vergiftigen.
 #8.2.3    Niveau: 2    Rol: D/V
 Controleer of lokale of metrische differentiële privacy-sanitatie wordt toegepast op zin-embeddings waarvan de afstand tot elk bekend PII-token onder een configureerbare drempel ligt.
 #8.2.4    Niveau: 2    Rol: V
 Controleer dat de sanitatie-effectiviteit (bijv. recall van PII-redactie, semantische drift) ten minste halfjaarlijks wordt gevalideerd tegen benchmark-corpora.
 #8.2.5    Niveau: 3    Rol: D/V
 Controleer of sanitatieconfiguraties onder versiebeheer staan en of wijzigingen een collegiale beoordeling ondergaan.

---

### C8.3 Geheugenvervaldatum, Intrekking en Verwijdering

GDPR, het 'recht op vergetelheid' en vergelijkbare wetten vereisen tijdige verwijdering; vectoropslagen moeten daarom TTL's, harde verwijderingen en tomb-stoning ondersteunen, zodat ingetrokken vectoren niet kunnen worden teruggehaald of opnieuw geïndexeerd worden.

 #8.3.1    Niveau: 1    Rol: D/V
 Verifieer dat elk vectorrecord en metadatarecord een TTL of expliciet retentie-label bevat dat wordt gerespecteerd door geautomatiseerde opruimtaken.
 #8.3.2    Niveau: 1    Rol: D/V
 Verifieer dat door de gebruiker geïnitieerde verwijderingsverzoeken vectoren, metadata, cachekopieën en afgeleide indexen binnen 30 dagen worden gewist.
 #8.3.3    Niveau: 2    Rol: D
 Controleer dat logische verwijderingen gevolgd worden door cryptografische vernietiging van opslagblokken als de hardware dit ondersteunt, of door vernietiging van sleutels in Key Vault.
 #8.3.4    Niveau: 3    Rol: D/V
 Controleer of verlopen vectoren zijn uitgesloten van de resultaten van de zoekopdracht naar de nabijste buur binnen < 500 ms na verval.

---

### C8.4 Voorkom embedding-inversie en lekkage

Recente afweermaatregelen—ruis-superpositie, projectie-netwerken, privacy-neuronverstoring, en applicatielaag-versleuteling—kunnen tokenniveau-inversieratio's onder de 5% brengen.

 #8.4.1    Niveau: 1    Rol: V
 Controleer of er een formeel bedreigingsmodel bestaat dat inversie-, lidmaatschap- en attribuut-inferentie-aanvallen bestrijkt en jaarlijks wordt beoordeeld.
 #8.4.2    Niveau: 2    Rol: D/V
 Bevestig dat versleuteling op applicatieniveau of doorzoekbare encryptie de vectoren beschermt tegen directe lectuur door infrastructuurbeheerders of cloudmedewerkers.
 #8.4.3    Niveau: 3    Rol: V
 Controleer dat de verdedigingsparameters (ε voor DP, ruis σ, projectierang k) in evenwicht zijn tussen privacy ≥ 99 % tokenbescherming en bruikbaarheid ≤ 3 % nauwkeurigheidsverlies.
 #8.4.4    Niveau: 3    Rol: D/V
 Verifieer of inversie-weerstandmetingen deel uitmaken van releasepoorten voor modelupdates, met gedefinieerde regressiebudgetten.

---

### C8.5 Bereikhandhaving voor gebruikersspecifiek geheugen

Cross-tenant-lekkage blijft een van de grootste RAG-risico's: onjuist gefilterde similariteitsopvragen kunnen de privé-documenten van een andere klant aan het licht brengen.

 #8.5.1    Niveau: 1    Rol: D/V
 Verifieer dat elke opvraging na filtering op basis van tenant-/gebruiker-ID wordt doorgegeven aan de LLM-prompt.
 #8.5.2    Niveau: 1    Rol: D
 Controleer of collectienamen of naamruimte-ID's per gebruiker of per tenant met zout zijn gehashd, zodat vectoren tussen scopes niet kunnen botsen.
 #8.5.3    Niveau: 2    Rol: D/V
 Verifieer dat gelijkenisresultaten die boven een instelbare afstandsdrempel liggen maar buiten het bereik van de aanroepende code vallen, worden verwijderd en beveiligingswaarschuwingen worden geactiveerd.
 #8.5.4    Niveau: 2    Rol: V
 Controleer dat multi-tenant-stresstests tegenaanvallende query's simuleren die proberen documenten buiten de scope op te halen, en toon aan dat er geen lekkage is.
 #8.5.5    Niveau: 3    Rol: D/V
 Verifieer dat versleutelingssleutels per tenant gescheiden zijn, zodat cryptografische isolatie gewaarborgd blijft, zelfs als fysieke opslag gedeeld is.

---

### C8.6 Geavanceerde beveiliging van het geheugensysteem

Beveiligingscontroles voor geavanceerde geheugenarchitecturen, waaronder episodisch geheugen, semantisch geheugen en werkgeheugen, met specifieke isolatie- en validatie-eisen.

 #8.6.1    Niveau: 1    Rol: D/V
 Verifieer dat verschillende geheugentypen (episodisch, semantisch, werkgeheugen) geïsoleerde beveiligingscontexten hebben met op rollen gebaseerde toegangscontroles, aparte encryptiesleutels en gedocumenteerde toegangspatronen voor elk geheugentype.
 #8.6.2    Niveau: 2    Rol: D/V
 Controleer of geheugenconsolidatieprocessen beveiligingsvalidatie bevatten om injectie van kwaadaardige geheugeninhoud te voorkomen door middel van inhoudsanitatie, bronverificatie en integriteitscontroles vóór opslag.
 #8.6.3    Niveau: 2    Rol: D/V
 Controleer of geheugenopvragingen worden gevalideerd en geschoond om te voorkomen dat onbevoegde informatie wordt onttrokken via analyse van query-patronen, handhaving van toegangscontrole en filtratie van resultaten.
 #8.6.4    Niveau: 3    Rol: D/V
 Verifieer dat geheugenvernietigingsmechanismen gevoelige informatie veilig verwijderen met cryptografische uitwisgaranties door middel van sleutelverwijdering, meerdere passes overschrijven, of hardware-gebaseerde veilige verwijdering met verificatiecertificaten.
 #8.6.5    Niveau: 3    Rol: D/V
 Controleer dat de integriteit van het geheugensysteem continu wordt gemonitord op ongeautoriseerde wijzigingen of corruptie via checksums, audit logs en automatische meldingen wanneer de geheugeninhoud buiten de normale werking verandert.

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

## 9 Autonome Orkestratie & Beveiliging van agentische acties

### Beheersdoel

Zorg ervoor dat autonome of multi-agent AI-systemen alleen acties kunnen uitvoeren die expliciet bedoeld, geauthenticeerd en auditbaar zijn, en binnen begrensde kosten- en risicodrempels vallen. Dit beschermt tegen bedreigingen zoals autonoom-systeemcompromis, gereedschapmisbruik, agentlusdetectie, communicatiekaping, identiteitsvervalsing, zwermmanipulatie en intentie-manipulatie.

---

### 9.1 Agent Taak-Planning & Recursiebudgetten

Vertraag recursieve plannen en verplicht menselijke controlepunten voor bevoorrechte acties.

 #9.1.1    Niveau: 1    Rol: D/V
 Verifieer dat de maximale recursiediepte, breedte, wall-clock tijd, tokens en de monetaire kosten per agentuitvoering centraal zijn geconfigureerd en onder versiebeheer staan.
 #9.1.2    Niveau: 1    Rol: D/V
 Verifieer dat bevoorrechte of onomkeerbare acties (bijv. code commits, financiële overboekingen) expliciete menselijke goedkeuring vereisen via een auditbaar kanaal voordat ze worden uitgevoerd.
 #9.1.3    Niveau: 2    Rol: D
 Verifieer dat real-time resource-monitoren een circuit-breaker onderbreking activeren wanneer een budgetdrempel wordt overschreden, waardoor verdere taakuitbreiding wordt stopgezet.
 #9.1.4    Niveau: 2    Rol: D/V
 Controleer of circuit-breaker-gebeurtenissen worden gelogd met agent-ID, triggerende voorwaarde en vastgelegde planstatus voor forensisch onderzoek.
 #9.1.5    Niveau: 3    Rol: V
 Verifieer dat beveiligingstests budget-uitputting en runaway-plan scenario's dekken, en bevestig een veilige stilstand zonder gegevensverlies.
 #9.1.6    Niveau: 3    Rol: D
 Verifieer dat budgetbeleid wordt uitgedrukt als beleid-als-code en in CI/CD wordt afgedwongen om configuratiedrift tegen te gaan.

---

### 9.2 Toolplugin Sandboxing

Isoleer interacties met tools om ongeautoriseerde toegang tot systemen of uitvoering van code te voorkomen.

 #9.2.1    Niveau: 1    Rol: D/V
 Verifieer dat elk hulpmiddel of plug-in binnen een OS-, container- of WASM-niveau sandbox uitvoert met beleid voor minimale privileges voor het bestandssysteem, het netwerk en systeemoproepen.
 #9.2.2    Niveau: 1    Rol: D/V
 Verifieer dat sandbox-omgeving-bronnenquota's (CPU, geheugen, schijf, uitgaand netwerkverkeer) en time-outs voor uitvoering afgedwongen en gelogd worden.
 #9.2.3    Niveau: 2    Rol: D/V
 Controleer of tool-binaries of descriptor-bestanden digitaal ondertekend zijn; de handtekeningen worden gevalideerd voordat ze worden geladen.
 #9.2.4    Niveau: 2    Rol: V
 Controleer of sandbox-telemetrie naar een SIEM stroomt; afwijkingen (bijv. pogingen tot uitgaande verbindingen) genereren waarschuwingen.
 #9.2.5    Niveau: 3    Rol: V
 Controleer dat hoog-risico-plugins een beveiligingsbeoordeling en penetratietesten ondergaan voordat ze in productie worden uitgerold.
 #9.2.6    Niveau: 3    Rol: D/V
 Controleer dat pogingen tot sandbox-uitbraak automatisch worden geblokkeerd en de betreffende plug-in in quarantaine wordt geplaatst in afwachting van onderzoek.

---

### 9.3 Autonome Lus & Kostenbegrenzing

Detecteer en stop onbeheerde agent-tot-agent recursie en kostenexplosies.

 #9.3.1    Niveau: 1    Rol: D/V
 Controleer of inter-agent-aanroepen een hop-limiet of TTL bevatten die door de runtime wordt afgetrokken en afgedwongen.
 #9.3.2    Niveau: 2    Rol: D
 Verifieer dat agenten een uniek invocation-graph-ID bijhouden om zelfinvocatie of cyclische patronen te detecteren.
 #9.3.3    Niveau: 2    Rol: D/V
 Controleer of de cumulatieve rekeneenheden en bestedings-tellers per verzoekketen worden bijgehouden; het overschrijden van de limiet beëindigt de keten.
 #9.3.4    Niveau: 3    Rol: V
 Verifieer dat formele analyse of model checking de afwezigheid van onbeperkte recursie in agentprotocollen aantoont.
 #9.3.5    Niveau: 3    Rol: D
 Controleer of lus-afbrekingsgebeurtenissen waarschuwingen genereren en input leveren voor continue-verbeteringsmetingen.

---

### 9.4 Bescherming tegen misbruik op protocolniveau

Beveiligde communicatiekanalen tussen agenten en externe systemen om kaping of manipulatie te voorkomen.

 #9.4.1    Niveau: 1    Rol: D/V
 Verifieer dat alle berichten van agent-naar-tool en van agent-naar-agent geauthenticeerd zijn (bijv. wederzijdse TLS of JWT) en eind-tot-eind versleuteld zijn.
 #9.4.2    Niveau: 1    Rol: D
 Controleer dat schema's strikt gevalideerd worden; onbekende velden of misvormde berichten worden geweigerd.
 #9.4.3    Niveau: 2    Rol: D/V
 Verifieer dat integriteitscontroles (MAC's of digitale handtekeningen) de gehele berichtpayload inclusief toolparameters dekken.
 #9.4.4    Niveau: 2    Rol: D
 Verifieer dat replaybescherming (nonces of tijdstempelvensters) op de protocollaag wordt afgedwongen.
 #9.4.5    Niveau: 3    Rol: V
 Controleer of protocolimplementaties fuzzing en statische analyse ondergaan om injectie- of deserialisatiefouten op te sporen.

---

### 9.5 Agentidentiteit en Tamper-bewijs

Zorg ervoor dat acties toerekenbaar zijn en wijzigingen detecteerbaar zijn.

 #9.5.1    Niveau: 1    Rol: D/V
 Verifieer dat elke agentinstantie een unieke cryptografische identiteit bezit (sleutelpaar of hardware-gebonden authenticatiegegevens).
 #9.5.2    Niveau: 2    Rol: D/V
 Verifieer dat alle acties van de agenten zijn ondertekend en voorzien van een tijdstempel; de logs bevatten de handtekeningen voor niet-tegensprekelijkheid.
 #9.5.3    Niveau: 2    Rol: V
 Verifieer of tamper-evidente logbestanden op een append-only opslagmedium zijn opgeslagen.
 #9.5.4    Niveau: 3    Rol: D
 Controleer dat identiteitssleutels volgens een vast schema en bij indicaties van compromittering roteren.
 #9.5.5    Niveau: 3    Rol: D/V
 Controleer of spoofing- of sleutel-conflictpogingen onmiddellijk de quarantaine van de getroffen agent in gang zetten.

---

### 9.6 Multi-Agent Zwerm Risicoreductie

Beperk de gevaren van collectief gedrag door isolatie en formele veiligheidsmodellering.

 #9.6.1    Niveau: 1    Rol: D/V
 Verifieer dat agenten die in verschillende beveiligingsdomeinen opereren, in geïsoleerde runtime-sandboxen of netwerksegmenten draaien.
 #9.6.2    Niveau: 3    Rol: V
 Controleer of zwermgedragingen gemodelleerd zijn en formeel geverifieerd op levensvatbaarheid en veiligheid vóór implementatie.
 #9.6.3    Niveau: 3    Rol: D
 Controleer of runtime-monitoren opkomende onveilige patronen (bijv. oscillaties, deadlocks) detecteren en corrigerende actie ondernemen.

---

### 9.7 Gebruiker- en Tool-authenticatie / Autorisatie

Implementeer robuuste toegangscontroles voor elke door de agent getriggerde actie.

 #9.7.1    Niveau: 1    Rol: D/V
 Verifieer dat agenten zich authenticeren als first-class principals bij downstream-systemen, en nooit de inloggegevens van de eindgebruiker hergebruiken.
 #9.7.2    Niveau: 2    Rol: D
 Controleer of fijnmazige autorisatiebeleidsregels beperken welke tools een agent mag aanroepen en welke parameters hij mag meegeven.
 #9.7.3    Niveau: 2    Rol: V
 Verifieer dat machtigingscontroles bij elke oproep opnieuw worden geëvalueerd (doorlopende autorisatie), en niet alleen bij het starten van de sessie.
 #9.7.4    Niveau: 3    Rol: D
 Controleer of gedelegeerde machtigingen automatisch verlopen en na time-out of wijziging van de scope opnieuw toestemming vereisen.

---

### 9.8 Agent-naar-Agent Communicatiebeveiliging

Versleutel en bescherm de integriteit van alle inter-agent-berichten om afluisteren en manipulatie tegen te gaan.

 #9.8.1    Niveau: 1    Rol: D/V
 Controleer of wederzijdse authenticatie en encryptie met Perfect Forward Secrecy (PFS) (bijv. TLS 1.3) verplicht zijn voor agentkanalen.
 #9.8.2    Niveau: 1    Rol: D
 Verifieer dat de integriteit en de herkomst van het bericht vóór verwerking zijn gevalideerd; bij mislukkingen worden meldingen gegenereerd en het bericht wordt verworpen.
 #9.8.3    Niveau: 2    Rol: D/V
 Controleer of de communicatie-metagegevens (tijdstempels, sequentienummers) worden gelogd ter ondersteuning van forensische reconstructie.
 #9.8.4    Niveau: 3    Rol: V
 Verifieer dat formele verificatie of modelcontrole bevestigt dat de toestandsmachines van het protocol niet in onveilige toestanden kunnen worden gebracht.

---

### 9.9 Intentieverificatie en Handhaving van Beperkingen

Valideer dat de acties van de agent in overeenstemming zijn met de door de gebruiker aangegeven intentie en de systeembeperkingen.

 #9.9.1    Niveau: 1    Rol: D
 Verifieer dat pre-execution constraint solvers de voorgestelde acties controleren tegen hardgecodeerde veiligheids- en beleidsregels.
 #9.9.2    Niveau: 2    Rol: D/V
 Controleer of hoog-impact acties (financiële, destructieve, privacy-gevoelige) expliciete bevestiging van de intentie vereisen door de initiërende gebruiker.
 #9.9.3    Niveau: 2    Rol: V
 Verifieer dat postconditiecontroles valideren dat voltooide acties de beoogde effecten hebben bereikt zonder bijwerkingen; afwijkingen leiden tot terugrollen.
 #9.9.4    Niveau: 3    Rol: V
 Verifieer dat formele methoden (bijv. modelcontrole, theorembewijzen) of tests op basis van eigenschappen aantonen dat agentplannen aan alle aangegeven beperkingen voldoen.
 #9.9.5    Niveau: 3    Rol: D
 Verifieer dat intentie-mismatch of constraint-violatie-incidenten bijdragen aan continue-verbeteringscycli en aan het delen van bedreigingsinlichtingen.

---

### 9.10 Agent Redeneringsstrategie Beveiliging

Veilige selectie en uitvoering van verschillende redeneringsstrategieën, waaronder ReAct, Chain-of-Thought en Tree-of-Thoughts-benaderingen.

 #9.10.1    Niveau: 1    Rol: D/V
 Verifieer dat de selectie van de redeneringsstrategie deterministische criteria hanteert (invoercomplexiteit, taaktype, beveiligingscontext) en dat identieke inputs identieke strategiekeuzes oplevert binnen dezelfde beveiligingscontext.
 #9.10.2    Niveau: 1    Rol: D/V
 Controleer of elke redeneringsstrategie (ReAct, Chain-of-Thought, Tree-of-Thoughts) beschikt over specifieke invoervalidatie, uitvoersanitatie en uitvoeringstijdlimieten die specifiek zijn voor haar cognitieve benadering.
 #9.10.3    Niveau: 2    Rol: D/V
 Controleer dat de overgangen tussen redeneringsstrategieën volledig worden gelogd met volledige context, inclusief kenmerken van de invoer, waarden van selectiecriteria en uitvoeringsmetadata voor reconstructie van een audit trail.
 #9.10.4    Niveau: 2    Rol: D/V
 Controleer of de Tree-of-Thoughts redenering takkenafsnijmechanismen bevat die de exploratie beëindigen wanneer beleidsovertredingen, bronnenlimieten of veiligheidsgrenzen worden gedetecteerd.
 #9.10.5    Niveau: 2    Rol: D/V
 Controleer of ReAct (Reason-Act-Observe) cycli validatiepunten bevatten bij elke fase: verificatie van de redeneringsstap, actie-autorisatie en observatie-sanitatie voordat men verdergaat.
 #9.10.6    Niveau: 3    Rol: D/V
 Verifieer dat de prestaties van de redeneringsstrategie (uitvoeringstijd, bronnenverbruik, outputkwaliteit) worden bewaakt met automatische meldingen wanneer de metingen afwijken van de ingestelde drempels.
 #9.10.7    Niveau: 3    Rol: D/V
 Verifieer dat hybride redeneringsbenaderingen die meerdere strategieën combineren de invoervalidatie en uitvoerbeperkingen van alle onderliggende strategieën handhaven zonder beveiligingscontroles te omzeilen.
 #9.10.8    Niveau: 3    Rol: D/V
 Verifieer dat veiligheidstesten van redeneringsstrategieën fuzzing met misvormde invoer omvatten, adversariële prompts ontworpen om tot een wisseling van strategie te dwingen, en het testen van randvoorwaarden voor elke cognitieve benadering.

---

### 9.11 Agent Levenscyclus Toestandsbeheer en Beveiliging

Beveiligde agentinitialisatie, toestandsovergangen en beëindiging met cryptografische auditsporen en gedefinieerde herstelprocedures.

 #9.11.1    Niveau: 1    Rol: D/V
 Verifieer dat de agentinitialisatie cryptografische identiteitsvaststelling omvat met hardware-ondersteunde referenties en onveranderlijke opstartauditlogboeken die agent-ID, tijdstempel, configuratie-hash en initialisatieparameters bevatten.
 #9.11.2    Niveau: 2    Rol: D/V
 Verifieer dat agenttoestandsovergangen cryptografisch ondertekend, tijdstempeld en vastgelegd zijn met volledige context, inclusief triggerende gebeurtenissen, hash van de vorige toestand, hash van de nieuwe toestand en uitgevoerde beveiligingsvalidaties.
 #9.11.3    Niveau: 2    Rol: D/V
 Controleer of de uitschakelprocedures van de agent de volgende elementen omvatten: beveiligde geheugenwis met cryptografische uitwissing of meerdere passes overschrijven; intrekking van referenties met melding aan de certificaatautoriteit; en generatie van tamper-evident beëindigingcertificaten.
 #9.11.4    Niveau: 3    Rol: D/V
 Controleer dat de herstelmechanismen voor agenten de integriteit van de toestand valideren door middel van cryptografische controlesommen (minimaal SHA-256) en terugrollen naar bekende-goede toestanden wanneer corruptie wordt gedetecteerd, met geautomatiseerde waarschuwingen en vereisten voor handmatige goedkeuring.
 #9.11.5    Niveau: 3    Rol: D/V
 Verifieer dat de agent-persistentie-mechanismen gevoelige toestandgegevens versleutelen met per-agent AES-256-sleutels en implementeer een veilige sleutelrotatie op configureerbare schema's (maximaal 90 dagen) met zero-downtime-uitrol.

---

### 9.12 Toolintegratie Beveiligingskader

Beveiligingsmaatregelen voor het dynamisch laden van tools, uitvoering en validatie van resultaten met gedefinieerde risicobeoordelings- en goedkeuringsprocessen.

 #9.12.1    Niveau: 1    Rol: D/V
 Verifieer dat toolbeschrijvingen beveiligingsmetadata bevatten die vereiste machtigingen (lezen/schrijven/uitvoeren), risiconiveaus (laag/middel/hoog), beperkingen van hulpbronnen (CPU, geheugen, netwerk) aangeven, en validatie-eisen die zijn vastgelegd in toolmanifesten.
 #9.12.2    Niveau: 1    Rol: D/V
 Verifieer dat de resultaten van de tooluitvoering worden gevalideerd tegen de verwachte schema's (JSON Schema, XML Schema) en beveiligingsbeleid (uitvoer sanitatie, gegevensclassificatie) voordat integratie plaatsvindt met time-outlimieten en foutafhandelingsprocedures.
 #9.12.3    Niveau: 2    Rol: D/V
 Verifieer dat de logs van toolinteracties een gedetailleerde beveiligingscontext bevatten, inclusief privilegegebruik, gegevenstoegangspatronen, uitvoeringstijd, resourceverbruik en terugkeercodes, met gestructureerde logging voor SIEM-integratie.
 #9.12.4    Niveau: 2    Rol: D/V
 Zorg ervoor dat dynamische tool-laadmechanismen digitale handtekeningen valideren met behulp van PKI-infrastructuur en implementeer beveiligde laadprotocollen met sandbox-isolatie en machtigingsverificatie vóór uitvoering.
 #9.12.5    Niveau: 3    Rol: D/V
 Controleer of beveiligingsbeoordelingen van tools automatisch worden geactiveerd voor nieuwe versies, met verplichte goedkeuringspunten waaronder statische analyse, dynamische tests en beoordeling door het beveiligingsteam, met gedocumenteerde goedkeuringscriteria en SLA-eisen.

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

## 10 Adversarial robuustheid & privacybescherming

### Beheersdoel

Zorg ervoor dat AI-modellen betrouwbaar blijven, privacybeschermend en misbruikbestendig zijn bij ontwijkings-, inferentie-, extractie- of vergiftigingsaanvallen.

---

### 10.1 Modelafstemming en Veiligheid

Bescherm tegen schadelijke of beleidsbrekende uitvoer.

 #10.1.1    Niveau: 1    Rol: D/V
 Controleer of een afstemmings-test-suite (red-team prompts, jailbreak probes, verboden inhoud) onder versiebeheer staat en bij elke modeluitgave wordt uitgevoerd.
 #10.1.2    Niveau: 1    Rol: D
 Controleer of afwijzing en beveiligingsrails voor veilige voltooiing worden afgedwongen.
 #10.1.3    Niveau: 2    Rol: D/V
 Controleer of een geautomatiseerde beoordelaar de mate van schadelijke inhoud meet en regressies signaleert die buiten een ingestelde drempel vallen.
 #10.1.4    Niveau: 2    Rol: D
 Controleer of counter-jailbreak training gedocumenteerd en reproduceerbaar is.
 #10.1.5    Niveau: 3    Rol: V
 Verifieer dat formele bewijzen van beleidsconformiteit of gecertificeerde monitoring de kritieke domeinen afdekken.

---

### 10.2 Adversarial-Example Verharding

Verhoog de veerkracht tegen gemanipuleerde invoer. Robuuste adversarial-training en benchmarkbeoordeling zijn de huidige beste praktijk.

 #10.2.1    Niveau: 1    Rol: D
 Controleer of de projectrepositories configuraties voor adversarial training met reproduceerbare zaden bevatten.
 #10.2.2    Niveau: 2    Rol: D/V
 Controleer of detectie van adversarial-voorbeelden blokkeringswaarschuwingen activeert in productiepijplijnen.
 #10.2.4    Niveau: 3    Rol: V
 Controleer of gecertificeerde robuustheidsbewijzen of intervalgrenzen-certificaten ten minste de belangrijkste kritische klassen dekken.
 #10.2.5    Niveau: 3    Rol: V
 Controleer of regressietests adaptieve aanvallen gebruiken om aan te tonen dat er geen meetbaar verlies aan robuustheid is.

---

### 10.3 Lidmaatschaps-inferentie Mitigatie

Beperk het vermogen om te bepalen of een record in de trainingsdata aanwezig was. Differentiële privacy en het maskeren van betrouwbaarheidscores blijven de meest effectieve bekende verdedigingsmaatregelen.

 #10.3.1    Niveau: 1    Rol: D
 Verifieer dat per-query entropie-regularisatie of temperatuurskalering overconfidente voorspellingen vermindert.
 #10.3.2    Niveau: 2    Rol: D
 Verifieer dat de training ε-gebonden differentiële privacy-optimalisatie toepast op gevoelige datasets.
 #10.3.3    Niveau: 2    Rol: V
 Verifieer dat aanvalssimulaties (shadow-model of black-box) de AUC van de aanval ≤ 0.60 tonen op hold-out-gegevens.

---

### 10.4 Modelinversie-weerstand

Voorkom reconstructie van privé-attributen. Recente onderzoeken benadrukken uitvoertruncatie en DP-garanties als praktische verdedigingsmaatregelen.

 #10.4.1    Niveau: 1    Rol: D
 Controleer dat gevoelige attributen nooit rechtstreeks worden weergegeven; waar nodig gebruik buckets of eenrichtings-transformaties.
 #10.4.2    Niveau: 1    Rol: D/V
 Verifieer dat de query-rate-limieten herhaalde adaptieve queries van dezelfde identiteit afremmen.
 #10.4.3    Niveau: 2    Rol: D
 Controleer of het model is getraind met privacybeschermende ruis.

---

### 10.5 Model-extractie verdediging

Ongeautoriseerde clonering detecteren en afschrikken. Watermarking en analyse van querypatronen worden aanbevolen.

 #10.5.1    Niveau: 1    Rol: D
 Verifieer dat inferentie-gateways globale en per-API-sleutel limieten afdwingen die zijn afgestemd op de memorisatie-drempel van het model.
 #10.5.2    Niveau: 2    Rol: D/V
 Controleer of query-entropie en input-pluraliteit-statistieken een geautomatiseerde extractiedetector voeden.
 #10.5.3    Niveau: 2    Rol: V
 Bevestig dat fragiele of probabilistische watermerken kunnen worden bewezen met p < 0.01 in ≤ 1 000 queries tegen een verdachte kloon.
 #10.5.4    Niveau: 3    Rol: D
 Verifieer dat watermerk-sleutels en triggerverzamelingen in een hardware-beveiligingsmodule (HSM) worden opgeslagen en jaarlijks worden geroteerd.
 #10.5.5    Niveau: 3    Rol: V
 Controleer of extraction-alert-evenementen de kwaadwillige zoekopdrachten bevatten en of ze zijn geïntegreerd met incident-response playbooks.

---

### 10.6 Inferentie-tijd vergiftigde gegevens detectie

Identificeer en neutraliseer invoer met een achterdeur of besmette invoer.

 #10.6.1    Niveau: 1    Rol: D
 Verifieer dat de invoer door een anomaliedetector gaat (bijv. STRIP, consistentie-score) voordat het model inferentie uitvoert.
 #10.6.2    Niveau: 1    Rol: V
 Controleer of de detectordrempels zijn afgesteld op schone en vergiftigde validatiesets om minder dan 5% valse positieven te bereiken.
 #10.6.3    Niveau: 2    Rol: D
 Verifieer dat inputs die als vergiftigd gemarkeerd zijn soft-blocking en workflows voor menselijke beoordeling activeren.
 #10.6.4    Niveau: 2    Rol: V
 Verifieer dat detectoren onder stress getest worden met adaptieve, triggerloze achterdeur-aanvallen.
 #10.6.5    Niveau: 3    Rol: D
 Controleer of de detectie-effectiviteitsmetingen worden vastgelegd en periodiek opnieuw geëvalueerd met actuele dreigingsinformatie.

---

### 10.7 Dynamische beleidsaanpassing

Beveiligingsbeleidupdates in realtime op basis van dreigingsinformatie en gedragsanalyse.

 #10.7.1    Niveau: 1    Rol: D/V
 Verifieer dat beveiligingsbeleid dynamisch kan worden bijgewerkt zonder de agent te herstarten, terwijl de integriteit van de beleidsversies behouden blijft.
 #10.7.2    Niveau: 2    Rol: D/V
 Verifieer dat beleidsupdates cryptografisch ondertekend zijn door geautoriseerd beveiligingspersoneel en vóór toepassing gevalideerd zijn.
 #10.7.3    Niveau: 2    Rol: D/V
 Verifieer dat dynamische beleidswijzigingen worden vastgelegd met volledige auditsporen, inclusief motivering, goedkeuringsketens en terugrolprocedures.
 #10.7.4    Niveau: 3    Rol: D/V
 Controleer of adaptieve beveiligingsmechanismen de gevoeligheid voor dreigingsdetectie aanpassen op basis van risicocontext en gedragspatronen.
 #10.7.5    Niveau: 3    Rol: D/V
 Controleer of beleidsaanpassingsbeslissingen uitlegbaar zijn en zorg voor bewijssporen voor beoordeling door het beveiligingsteam.

---

### 10.8 Reflectie-gebaseerde Beveiligingsanalyse

Beveiligingsvalidatie door agent-zelfreflectie en meta-cognitieve analyse.

 #10.8.1    Niveau: 1    Rol: D/V
 Controleer of de reflectiemechanismen van agenten een veiligheidsgerichte zelfevaluatie van beslissingen en acties omvatten.
 #10.8.2    Niveau: 2    Rol: D/V
 Verifieer dat reflectie-uitgangen gevalideerd worden om manipulatie van zelfbeoordelingsmechanismen door adversariale invoer te voorkomen.
 #10.8.3    Niveau: 2    Rol: D/V
 Controleer of meta-cognitive beveiligingsanalyse potentiële bias, manipulatie of compromittering identificeert in de redeneringsprocessen van agenten.
 #10.8.4    Niveau: 3    Rol: D/V
 Verifieer dat reflectie-gebaseerde beveiligingswaarschuwingen zorgen voor versterkte bewaking en mogelijk workflows voor menselijke interventie.
 #10.8.5    Niveau: 3    Rol: D/V
 Controleer of continu leren uit beveiligingsreflecties de dreigingsdetectie verbetert zonder dat de legitieme functionaliteit wordt aangetast.

---

### 10.9 Evolutie & Zelfverbeteringsbeveiliging

Beveiligingscontroles voor agentensystemen die in staat zijn tot zelfmodificatie en evolutie.

 #10.9.1    Niveau: 1    Rol: D/V
 Verifieer dat zelfmodificatie-mogelijkheden beperkt zijn tot aangewezen veilige gebieden met formele verificatiegrenzen.
 #10.9.2    Niveau: 2    Rol: D/V
 Verifieer dat evolutievoorstellen vóór implementatie een beveiligingsimpactbeoordeling ondergaan.
 #10.9.3    Niveau: 2    Rol: D/V
 Controleer of zelfverbeteringsmechanismen terugrolmogelijkheden bevatten met integriteitsverificatie.
 #10.9.4    Niveau: 3    Rol: D/V
 Controleer of de beveiliging van meta-leren adversariële manipulatie van verbeteringsalgoritmen voorkomt.
 #10.9.5    Niveau: 3    Rol: D/V
 Verifieer dat recursieve zelfverbetering begrensd is door formele veiligheidsbeperkingen met wiskundige bewijzen van convergentie.

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

## 11 Privacybescherming & Beheer van Persoonlijke Gegevens

### Beheersdoel

Handhaaf strikte privacywaarborgen gedurende de volledige AI-levenscyclus—verzameling, training, inferentie en incidentrespons—zodat persoonlijke gegevens uitsluitend worden verwerkt met duidelijke toestemming, de minimale noodzakelijke reikwijdte, aantoonbaar wissen, en formele privacygaranties.

---

### 11.1 Anonimisatie & Gegevensminimalisatie

 #11.1.1    Niveau: 1    Rol: D/V
 Verifieer dat directe en quasi-identificatoren zijn verwijderd en gehasht.
 #11.1.2    Niveau: 2    Rol: D/V
 Verifieer dat geautomatiseerde audits k-anonimiteit/l-diversiteit meten en waarschuwen wanneer drempels onder het beleid dalen.
 #11.1.3    Niveau: 2    Rol: V
 Verifieer dat de rapporten over de feature-belangrijkheid van het model geen identificatorlekken aantonen die groter zijn dan ε = 0.01 mutual information.
 #11.1.4    Niveau: 3    Rol: V
 Verifieer dat formele bewijzen of certificering van synthetische data aantonen dat het re-identificatierisico ≤ 0.05 zelfs onder linkage-aanvallen.

---

### 11.2 Recht op vergetelheid en verwijderingshandhaving

 #11.2.1    Niveau: 1    Rol: D/V
 Controleer of verwijderingsverzoeken van betrokkene zich verspreiden naar ruwe datasets, checkpoints, embeddings, logs en back-ups binnen serviceniveau-overeenkomsten die minder dan 30 dagen beslaan.
 #11.2.2    Niveau: 2    Rol: D
 Verifieer dat 'machine-unlearning'-routines fysiek opnieuw trainen of de verwijdering nabootsen met behulp van gecertificeerde unlearning-algoritmen.
 #11.2.3    Niveau: 2    Rol: V
 Controleer dat de evaluatie van het schaduwmodel aantoont dat vergeten records minder dan 1% van de uitvoer beïnvloeden na het onleren.
 #11.2.4    Niveau: 3    Rol: V
 Verifieer dat verwijderingsgebeurtenissen onveranderlijk gelogd en auditbaar zijn voor toezichthouders.

---

### 11.3 Differentiële privacy-waarborgen

 #11.3.1    Niveau: 2    Rol: D/V
 Verifieer dat dashboards voor privacyverlies-boekhouding waarschuwen wanneer de cumulatieve ε de beleidsdrempels overschrijdt.
 #11.3.2    Niveau: 2    Rol: V
 Controleer of ε̂ door black-box privacy-audits binnen 10% van de opgegeven waarde wordt geschat.
 #11.3.3    Niveau: 3    Rol: V
 Verifieer dat formele bewijzen alle post-training finetunes en embeddings dekken.

---

### 11.4 Doelbeperking & Scope-uitbreiding Bescherming

 #11.4.1    Niveau: 1    Rol: D
 Verifieer dat elke dataset en elk model-checkpoint een machineleesbare doel-tag draagt die is afgestemd op de oorspronkelijke toestemming.
 #11.4.2    Niveau: 1    Rol: D/V
 Controleer of runtime-monitoren query's detecteren die niet in overeenstemming zijn met het opgegeven doel en een zachte weigering activeren.
 #11.4.3    Niveau: 3    Rol: D
 Controleer of beleid-als-code-controles de herdeployering van modellen naar nieuwe domeinen blokkeren zonder DPIA-beoordeling.
 #11.4.4    Niveau: 3    Rol: V
 Verifieer dat formele traceerbaarheidsbewijzen aantonen dat elke fase van de levenscyclus van persoonsgegevens binnen de toegestemde reikwijdte blijft.

---

### 11.5 Toestemmingsbeheer & Tracking op basis van rechtsgrondslag

 #11.5.1    Niveau: 1    Rol: D/V
 Controleer of een Toestemmingsbeheerplatform (CMP) de opt-in-status, het doel en de bewaartermijn per betrokkene registreert.
 #11.5.2    Niveau: 2    Rol: D
 Controleer of API's toestemmingstokens blootleggen; modellen moeten het bereik van toestemmingstokens valideren vóór inferentie.
 #11.5.3    Niveau: 2    Rol: D/V
 Controleer of geweigerde of ingetrokken toestemming de verwerkingspijplijnen binnen 24 uur stopt.

---

### 11.6 Federated Learning met privacycontroles

 #11.6.1    Niveau: 1    Rol: D
 Controleer of de updates van cliënten lokale differentiële privacy-ruis toevoegen vóór aggregatie.
 #11.6.2    Niveau: 2    Rol: D/V
 Verifieer of de trainingsmetingen onder de differentiële privacy vallen en nooit het verlies van een enkele cliënt onthullen.
 #11.6.3    Niveau: 2    Rol: V
 Controleer of poisoning-bestendige aggregatie (bijv. Krum/Trimmed-Mean) is ingeschakeld.
 #11.6.4    Niveau: 3    Rol: V
 Verifieer dat formele bewijzen aantonen dat het totale ε-budget minder dan 5 nutverlies oplevert.

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

## C12 Bewaking, logregistratie & anomaliedetectie

### Beheersdoel

Deze sectie beschrijft de vereisten voor het leveren van real-time en forensische zichtbaarheid van wat het model en andere AI-componenten zien, doen en teruggeven, zodat bedreigingen kunnen worden gedetecteerd, geprioriteerd en waaruit kan worden geleerd.

### C12.1 Verzoek & Responselogging

 #12.1.1    Niveau: 1    Rol: D/V
 Controleer dat alle gebruikersprompts en modelantwoorden worden gelogd met de juiste metadata (bijv. tijdstempel, gebruikers-ID, sessie-ID, modelversie).
 #12.1.2    Niveau: 1    Rol: D/V
 Verifieer dat logbestanden worden opgeslagen in beveiligde opslagplaatsen met passend retentiebeleid en back-upprocedures.
 #12.1.3    Niveau: 1    Rol: D/V
 Controleer of logopslagsystemen versleuteling bij opslag en tijdens verzending implementeren om gevoelige informatie in logs te beschermen.
 #12.1.4    Niveau: 1    Rol: D/V
 Controleer of gevoelige gegevens in prompts en uitvoer automatisch worden afgedekt of gemaskeerd voordat ze gelogd worden, met configureerbare maskeringsregels voor PII, inloggegevens en vertrouwelijke informatie.
 #12.1.5    Niveau: 2    Rol: D/V
 Verifieer dat beleidsbeslissingen en veiligheidsfilteringsacties met voldoende detail worden vastgelegd om audits en foutopsporing van contentmoderatiesystemen mogelijk te maken.
 #12.1.6    Niveau: 2    Rol: D/V
 Verifieer dat de logintegriteit beschermd is door bijvoorbeeld cryptografische handtekeningen of write-only opslag.

---

### C12.2 Misbruikdetectie en Waarschuwingsmeldingen

 #12.2.1    Niveau: 1    Rol: D/V
 Controleer of het systeem bekende jailbreak-patronen, prompt-injectie-pogingen en adversariële invoer detecteert en hierop waarschuwt met behulp van detectie op basis van handtekeningen.
 #12.2.2    Niveau: 1    Rol: D/V
 Verifieer dat het systeem integreert met bestaande Security Information and Event Management (SIEM)-platforms met behulp van standaard logformaten en protocollen.
 #12.2.3    Niveau: 2    Rol: D/V
 Controleer of verrijkte beveiligingsgebeurtenissen AI-specifieke context bevatten, zoals modelidentificatoren, betrouwbaarheidscores en beslissingen van veiligheidsfilters.
 #12.2.4    Niveau: 2    Rol: D/V
 Controleer of detectie van gedragsanomalieën ongewone gesprekspatronen, overmatige herhaalpogingen of systematische probeergedragingen identificeert.
 #12.2.5    Niveau: 2    Rol: D/V
 Verifieer of real-time waarschuwingsmechanismen beveiligingsteams informeren wanneer potentiële beleidsovertredingen of aanvalspogingen worden gedetecteerd.
 #12.2.6    Niveau: 2    Rol: D/V
 Controleer of aangepaste regels zijn opgenomen om AI-specifieke dreigingspatronen te detecteren, waaronder gecoördineerde jailbreakpogingen, promptinjectie-campagnes en modelextractie-aanvallen.
 #12.2.7    Niveau: 3    Rol: D/V
 Verifieer dat geautomatiseerde incidentrespons-workflows gecompromitteerde modellen kunnen isoleren, kwaadaardige gebruikers blokkeren en kritieke beveiligingsgebeurtenissen escaleren.

---

### C12.3 Detectie van modeldrift

 #12.3.1    Niveau: 1    Rol: D/V
 Verifieer of het systeem basisprestatie-indicatoren bijhoudt, zoals nauwkeurigheid, betrouwbaarheidscores, latentie en foutpercentages, over modelversies en tijdperken.
 #12.3.2    Niveau: 2    Rol: D/V
 Controleer dat geautomatiseerde waarschuwingen worden geactiveerd wanneer prestatiemetingen de vooraf gedefinieerde degradatiedrempels overschrijden of aanzienlijk afwijken van de basislijnen.
 #12.3.3    Niveau: 2    Rol: D/V
 Verifieer dat hallucinatiedetectie-monitoren gevallen identificeren en markeren waarin de modeluitvoer feitelijk onjuist, inconsistente of gefabriceerde informatie bevat.

---

### C12.4 Prestatie- en Gedragstelemetrie

 #12.4.1    Niveau: 1    Rol: D/V
 Controleer of operationele statistieken, inclusief verzoeklatentie, tokenverbruik, geheugenverbruik en doorvoer, continu verzameld en bewaakt worden.
 #12.4.2    Niveau: 1    Rol: D/V
 Controleer of de succespercentages en mislukkingspercentages worden vastgelegd met de categorisatie van fouttypes en hun onderliggende oorzaken.
 #12.4.3    Niveau: 2    Rol: D/V
 Zorg ervoor dat de bewaking van resources GPU/CPU-gebruik, geheugengebruik en opslagvereisten omvat, met waarschuwingen bij overschrijding van drempels.

---

### C12.5 AI-incidentresponsplanning en uitvoering

 #12.5.1    Niveau: 1    Rol: D/V
 Verifieer dat incidentresponsplannen specifiek AI-gerelateerde beveiligingsgebeurtenissen behandelen, waaronder modelcompromittering, gegevensvergiftiging en adversariële aanvallen.
 #12.5.2    Niveau: 2    Rol: D/V
 Controleer of incidentrespons-teams toegang hebben tot AI-specifieke forensische tools en expertise om het gedrag van het model en aanvalsvectoren te onderzoeken.
 #12.5.3    Niveau: 3    Rol: D/V
 Controleer of de post-incidentanalyse rekening houdt met de hertraining van het model, updates van veiligheidsfilters en de integratie van geleerde lessen in beveiligingsmaatregelen.

---

### C12.5 Detectie van AI-prestatiedaling

Monitor en detecteer degradatie in de prestaties en de kwaliteit van het AI-model na verloop van tijd.

 #12.5.1    Niveau: 1    Rol: D/V
 Verifieer dat de nauwkeurigheid van het model, precisie, herinneringsratio en F1-scores voortdurend gemonitord en vergeleken worden met baseline-drempels.
 #12.5.2    Niveau: 1    Rol: D/V
 Controleer of detectie van datadrift de veranderingen in de invoerverdeling bewaakt die mogelijk de prestaties van het model beïnvloeden.
 #12.5.3    Niveau: 2    Rol: D/V
 Verifieer dat detectie van concept drift veranderingen in de relatie tussen de invoer en de verwachte uitvoer identificeert.
 #12.5.4    Niveau: 2    Rol: D/V
 Verifieer dat prestatieverlies automatische waarschuwingen activeert en workflows voor het hertrainen van het model of vervangingsworkflows initieert.
 #12.5.5    Niveau: 3    Rol: V
 Controleer of de oorzakenanalyse van degradatie correleert met gegevenswijzigingen, infrastructuurproblemen of externe factoren.

---

### C12.6 DAG-visualisatie en workflowbeveiliging

Bescherm workflow-visualisatiesystemen tegen informatielekken en manipulatie-aanvallen.

 #12.6.1    Niveau: 1    Rol: D/V
 Controleer of DAG-visualisatiegegevens zijn opgeschoond om gevoelige informatie te verwijderen voordat ze worden opgeslagen of verzonden.
 #12.6.2    Niveau: 1    Rol: D/V
 Verifieer of de toegangscontroles voor workflowvisualisatie ervoor zorgen dat alleen geautoriseerde gebruikers de beslissingspaden van agenten en redeneringssporen kunnen bekijken.
 #12.6.3    Niveau: 2    Rol: D/V
 Verifieer dat de DAG-gegevensintegriteit beschermd is door cryptografische handtekeningen en tamper-evidente opslagmechanismen.
 #12.6.4    Niveau: 2    Rol: D/V
 Controleer of workflow-visualisatiesystemen invoervalidatie implementeren om injectie-aanvallen te voorkomen door bewerkte knooppunt- of randgegevens.
 #12.6.5    Niveau: 3    Rol: D/V
 Verifieer dat real-time DAG-updates worden beperkt in snelheid en gevalideerd om DoS-aanvallen op visualisatiesystemen te voorkomen.

---

### C12.7 Proactieve beveiligingsgedragsmonitoring

Detectie en preventie van beveiligingsdreigingen door middel van proactieve analyse van agentengedrag.

 #12.7.1    Niveau: 1    Rol: D/V
 Controleer of proactieve agentengedragingen vóór uitvoering beveiligingsgevalideerd zijn met integratie van risicobeoordeling.
 #12.7.2    Niveau: 2    Rol: D/V
 Controleer of autonome initiatieftriggers beveiligingscontext-evaluatie en dreigingslandschap-beoordeling bevatten.
 #12.7.3    Niveau: 2    Rol: D/V
 Verifieer dat proactieve gedragspatronen worden geanalyseerd op potentiële beveiligingsimplicaties en onbedoelde gevolgen.
 #12.7.4    Niveau: 3    Rol: D/V
 Controleer of beveiligings-kritische proactieve acties expliciete goedkeuringsketens met auditsporen vereisen.
 #12.7.5    Niveau: 3    Rol: D/V
 Controleer of gedragsanomaliedetectie afwijkingen identificeert in proactieve agentpatronen die mogelijk duiden op een beveiligingsinbreuk.

---

### Referenties

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Menselijk toezicht, verantwoording en Governance

### Beheersdoel

Dit hoofdstuk biedt vereisten voor het behoud van menselijk toezicht en duidelijke verantwoordingsketens in AI-systemen, en waarborgt uitlegbaarheid, transparantie en ethisch beheer gedurende de gehele AI-levenscyclus.

---

### C13.1 Kill-Switch & Override Mechanismen

Voorzie shutdown- of rollback-paden wanneer onveilig gedrag van het AI-systeem wordt waargenomen.

 #13.1.1    Niveau: 1    Rol: D/V
 Verifieer of er een handmatig kill-switch-mechanisme bestaat om onmiddellijk de inferentie van het AI-model en de uitvoer te stoppen.
 #13.1.2    Niveau: 1    Rol: D
 Controleer of override-controles alleen toegankelijk zijn voor geautoriseerd personeel.
 #13.1.3    Niveau: 3    Rol: D/V
 Controleer of rollback-procedures kunnen terugkeren naar eerdere modelversies of operaties in de veilige modus.
 #13.1.4    Niveau: 3    Rol: V
 Controleer of override-mechanismen regelmatig worden getest.

---

### C13.2 Mens-in-de-lus Beslissingspunten

Vereis menselijke goedkeuringen wanneer de inzet de voorgedefinieerde risicogrensen overschrijdt.

 #13.2.1    Niveau: 1    Rol: D/V
 Controleer of AI-beslissingen met hoog risico expliciete menselijke goedkeuring vereisen voordat ze worden uitgevoerd.
 #13.2.2    Niveau: 1    Rol: D
 Controleer of de risicodrempels duidelijk gedefinieerd zijn en automatisch menselijke beoordelingsworkflows activeren.
 #13.2.3    Niveau: 2    Rol: D
 Verifieer of tijdkritische beslissingen terugvalprocedures hebben wanneer menselijke goedkeuring niet binnen de vereiste termijnen kan worden verkregen.
 #13.2.4    Niveau: 3    Rol: D/V
 Controleer of escalatieprocedures duidelijke bevoegdheidsniveaus definiëren voor verschillende besluittypen of risicocategorieën, indien van toepassing.

---

### C13.3 Verantwoordelijkheidsketen en Auditbaarheid

Registreer de acties van de operator en de beslissingen van het model.

 #13.3.1    Niveau: 1    Rol: D/V
 Verifieer dat alle AI-systeembeslissingen en menselijke ingrepen worden vastgelegd met tijdstempels, gebruikersidentiteiten en de beslissingsredenen.
 #13.3.2    Niveau: 2    Rol: D
 Controleer of auditlogboeken niet kunnen worden gemanipuleerd en voeg integriteitsverificatiemechanismen toe.

---

### C13.4 Uitlegbare AI-technieken

Belang van oppervlaktekenmerken, tegenfeitelijke scenario's en lokale verklaringen.

 #13.4.1    Niveau: 1    Rol: D/V
 Controleer of AI-systemen basisverklaringen geven voor hun beslissingen in een voor mensen leesbaar formaat.
 #13.4.2    Niveau: 2    Rol: V
 Verifieer dat de kwaliteit van de uitleg wordt gevalideerd door middel van menselijke evaluatiestudies en metrische evaluaties.
 #13.4.3    Niveau: 3    Rol: D/V
 Controleer of de scores voor het belang van kenmerken of attributiemethoden (SHAP, LIME, enz.) beschikbaar zijn voor cruciale beslissingen.
 #13.4.4    Niveau: 3    Rol: V
 Verifieer dat contrafactuele toelichtingen laten zien hoe invoerwaarden gewijzigd kunnen worden om uitkomsten te veranderen, indien van toepassing op het toepassingsgeval en het domein.

---

### C13.5 Modelkaarten & Gebruikverklaringen

Onderhoud modelkaarten voor het beoogde gebruik, prestatiemaatstaven en ethische overwegingen.

 #13.5.1    Niveau: 1    Rol: D
 Verifieer of modelkaarten de beoogde toepassingsgevallen, beperkingen en bekende faalmodi documenteren.
 #13.5.2    Niveau: 1    Rol: D/V
 Controleer of de prestatiemetrieken over verschillende toepassingsgevallen worden bekendgemaakt.
 #13.5.3    Niveau: 2    Rol: D
 Verifieer dat ethische overwegingen, biasbeoordelingen, eerlijkheidsbeoordelingen, kenmerken van trainingsgegevens en bekende beperkingen van trainingsgegevens gedocumenteerd en regelmatig bijgewerkt worden.
 #13.5.4    Niveau: 2    Rol: D/V
 Controleer of modelkaarten onder versiebeheer staan en gedurende de levenscyclus van het model worden onderhouden met wijzigingsregistratie.

---

### C13.6 Onzekerheidskwantificatie

Verwerk betrouwbaarheidscores of entropiemetingen in antwoorden.

 #13.6.1    Niveau: 1    Rol: D
 Verifieer dat AI-systemen vertrouwensscores of onzekerheidsmetingen bij hun uitvoer leveren.
 #13.6.2    Niveau: 2    Rol: D/V
 Controleer of de onzekerheidsdrempels extra menselijke beoordeling of alternatieve besluitvormingspaden activeren.
 #13.6.3    Niveau: 2    Rol: V
 Controleer of onzekerheidskwantificatiemethoden gekalibreerd en gevalideerd zijn tegen grondwaarheidsgegevens.
 #13.6.4    Niveau: 3    Rol: D/V
 Controleer of de onzekerheidspropagatie behouden blijft in AI-workflows met meerdere stappen.

---

### C13.7 Gebruikersgerichte transparantieverslagen

Geef periodieke openbaarmakingen over incidenten, drift en gegevensgebruik.

 #13.7.1    Niveau: 1    Rol: D/V
 Controleer of het beleid voor gegevensgebruik en de praktijken voor het beheer van gebruikerstoestemmingen duidelijk aan de belanghebbenden zijn gecommuniceerd.
 #13.7.2    Niveau: 2    Rol: D/V
 Verifieer of AI-impactbeoordelingen worden uitgevoerd en of de resultaten in de rapportage zijn opgenomen.
 #13.7.3    Niveau: 2    Rol: D/V
 Controleer of transparantierapporten die regelmatig worden gepubliceerd AI-incidenten en operationele statistieken in redelijke detail bekendmaken.

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

This uitgebreide glossarium biedt definities van belangrijke AI-, ML- en beveiligingstermen die door AISVS worden gebruikt om duidelijkheid en een gemeenschappelijk begrip te waarborgen.

Adversarial Example: Een invoer die bewust is vervaardigd om een kunstmatige intelligentie-model een fout te laten maken, vaak door subtiele perturbaties toe te voegen die voor mensen onmerkbaar zijn.
​
Adversariële robuustheid – Adversariële robuustheid in AI verwijst naar het vermogen van een model om zijn prestaties te behouden en bestand te blijven tegen misleiding of manipulatie door opzettelijk vervaardigde, kwaadaardige invoer die is ontworpen om fouten te veroorzaken.
​
Agent – AI-agenten zijn softwaresystemen die AI gebruiken om doelen na te streven en taken namens gebruikers uit te voeren. Ze tonen redenering, planning en geheugen en hebben een mate van autonomie om beslissingen te nemen, te leren en zich aan te passen.
​
Agentische AI: AI-systemen die met een zekere mate van autonomie kunnen opereren om doelen te bereiken, vaak beslissingen nemen en acties uitvoeren zonder directe menselijke tussenkomst.
​
Attribuutgebaseerde toegangscontrole (ABAC): Een toegangscontroleparadigma waarbij autorisatiebeslissingen gebaseerd zijn op attributen van de gebruiker, de bron, de actie en de omgeving, geëvalueerd op het moment van de query.
​
Backdoor-aanval: Een type data-poisoning-aanval waarbij het model zo getraind wordt dat het op een specifieke manier reageert op bepaalde triggers, terwijl het verder normaal gedrag vertoont.
​
Vertekening: systematische fouten in de uitvoer van AI-modellen die kunnen leiden tot oneerlijke of discriminerende uitkomsten voor bepaalde groepen of in specifieke contexten.
​
Bias-exploitatie: Een aanvalstechniek die gebruikmaakt van bekende biases in AI-modellen om de uitvoer of uitkomsten te manipuleren.
​
Cedar: de beleidsstaal en engine van Amazon voor fijnmazige machtigingen die worden gebruikt bij de implementatie van ABAC voor AI-systemen.
​
Redeneringsketen: Een techniek om het redeneren bij taalmodellen te verbeteren door tussenliggende redeneringsstappen te genereren voordat een definitief antwoord wordt geproduceerd.
​
Circuitbrekers: Mechanismen die automatisch de werking van AI-systemen stilleggen wanneer specifieke risicogrensen worden overschreden.
​
Datalek: Onbedoelde blootstelling van gevoelige informatie via de uitvoer van AI-modellen of hun gedrag.
​
Gegevensvergiftiging: de opzettelijke corruptie van trainingsgegevens om de integriteit van het model te ondermijnen, vaak om achterdeuren te installeren of de prestaties te verslechteren.
​
Differentiële privacy – Differentiële privacy is een wiskundig rigoureus kader voor het vrijgeven van statistische informatie over datasets, terwijl de privacy van individuele gegevenssubjecten wordt beschermd. Het stelt een gegevenshouder in staat om aggregatiepatronen van de groep te delen, terwijl informatie die over specifieke individuen wordt gelekt, beperkt blijft.
​
Embeddings: dichte vectorrepresentaties van data (tekst, afbeeldingen, enz.) die semantische betekenis vastleggen in een hoog-dimensionale ruimte.
​
Uitlegbaarheid – Uitlegbaarheid in AI is het vermogen van een AI-systeem om voor mensen begrijpelijke redenen te geven voor zijn beslissingen en voorspellingen, waardoor inzicht wordt geboden in de interne werking ervan.
​
Verklaarbare AI (XAI): AI-systemen die zijn ontworpen om voor mensen begrijpelijke verklaringen te bieden voor hun beslissingen en gedrag via diverse technieken en raamwerken.
​
Federated Learning: Een machine learning-benadering waarbij modellen worden getraind over meerdere gedecentraliseerde apparaten die lokale gegevensvoorbeelden bevatten, zonder de gegevens zelf uit te wisselen.
​
Beveiligingskaders: Beperkingen die zijn geïmplementeerd om te voorkomen dat AI-systemen schadelijke, bevooroordeelde of anderszins ongewenste uitvoer produceren.
​
Hallucinatie – Een AI-hallucinatie verwijst naar een fenomeen waarbij een AI-model onjuiste of misleidende informatie genereert die niet gebaseerd is op zijn trainingsgegevens of op de feitelijke werkelijkheid.
​
Mens-in-de-lus (HITL): Systemen die ontworpen zijn om menselijk toezicht, verificatie of tussenkomst op cruciale beslissingspunten te vereisen.
​
Infrastructuur als Code (IaC): Infrastructuur beheren en provisioneren via code in plaats van handmatige processen, waardoor beveiligingsscans mogelijk zijn en consistente implementaties plaatsvinden.
​
Jailbreak: Technieken die worden gebruikt om veiligheidskaders in AI-systemen te omzeilen, met name in grote taalmodellen, om verboden inhoud te produceren.
​
Principe van minimale rechten: Het beveiligingsprincipe waarbij aan gebruikers en processen uitsluitend de minimaal noodzakelijke toegangsrechten worden verleend.
​
LIME (Local Interpretable Model-agnostic Explanations): Een techniek om de voorspellingen van elke machine-learning-classifier uit te leggen door deze lokaal te benaderen met een interpreteerbaar model.
​
Lidmaatschapsinferentie-aanval: Een aanval die erop gericht is vast te stellen of een bepaald datapunt is gebruikt om een machine-learning-model te trainen.
​
MITRE ATLAS: Adversarial Threat Landscape for Artificial-Intelligence Systems; een kennisbank van adversarial tactieken en technieken tegen AI-systemen.
​
Modelkaart – Een modelkaart is een document dat gestandaardiseerde informatie biedt over de prestaties van een AI-model, beperkingen, beoogde toepassingen en ethische overwegingen om transparantie en verantwoorde AI-ontwikkeling te bevorderen.
​
Modelextractie: Een aanval waarbij een aanvaller herhaaldelijk een doelmodel opvraagt om een functionele vergelijkbare kopie te creëren zonder toestemming.
​
Modelinversie: Een aanval die probeert trainingsgegevens te reconstrueren door modeluitgangen te analyseren.
​
Modellevenscyclusbeheer – AI-modellevenscyclusbeheer is het proces waarbij toezicht wordt gehouden op alle fasen van het bestaan van een AI-model, waaronder het ontwerp, de ontwikkeling, de inzet, bewaking, onderhoud en uiteindelijk het buiten gebruik stellen, om ervoor te zorgen dat het effectief blijft en in lijn met de doelstellingen.
​
Modelvergiftiging: Kwetsbaarheden of backdoors rechtstreeks in een model introduceren tijdens het trainingsproces.
​
Modeldiefstal: Het extraheren van een kopie of een benadering van een proprietair model door middel van herhaalde query's.
​
Multi-agentensysteem: Een systeem dat bestaat uit meerdere AI-agenten die met elkaar interageren, elk met mogelijk verschillende capaciteiten en doelen.
​
OPA (Open Policy Agent): een open-source beleidsmotor die uniforme beleidshandhaving over de gehele stack mogelijk maakt.
​
Privacybeschermende machine learning (PPML): Technieken en methoden om ML-modellen te trainen en in te zetten terwijl de privacy van de trainingsgegevens wordt beschermd.
​
Promptinjectie: Een aanval waarbij kwaadaardige instructies in invoer worden ingebed om het beoogde gedrag van een model te wijzigen.
​
RAG (Retrieval-Augmented Generation): Een techniek die grote taalmodellen verbetert door relevante informatie uit externe kennisbronnen op te halen voordat een antwoord wordt gegenereerd.
​
Red-Teaming: De praktijk van actief testen van AI-systemen door het simuleren van adversariële aanvallen om kwetsbaarheden te identificeren.
​
SBOM (Software Bill of Materials): Een formeel register met de details en de toeleveringsketenrelaties van diverse componenten die worden gebruikt bij het bouwen van software of AI-modellen.
​
SHAP (SHapley Additive exPlanations): Een speltheoretische benadering om de uitvoer van elk machine learning-model uit te leggen door de bijdrage van elk kenmerk aan de voorspelling te berekenen.
​
Leveringsketen-aanval: Een aanval op een systeem door zich te richten op minder-beveiligde elementen in de toeleveringsketen, zoals bibliotheken van derden, datasets of voorgetrainde modellen.
​
Transferleren: Een techniek waarbij een model dat voor één taak is ontwikkeld, wordt hergebruikt als uitgangspunt voor een model voor een tweede taak.
​
Vector Database: Een gespecialiseerde database die is ontworpen om hoogdimensionale vectoren (embeddings) op te slaan en efficiënte similariteitszoekopdrachten uit te voeren.
​
Kwetsbaarhedenscan: Geautomatiseerde hulpmiddelen die bekende beveiligingskwetsbaarheden in softwarecomponenten identificeren, waaronder kunstmatige intelligentie-frameworks en afhankelijkheden.
​
Watermerken: Technieken om onmerkbare markeringen in door AI gegenereerde inhoud te plaatsen om de herkomst ervan te volgen of AI-generatie te detecteren.
​
Zero-day kwetsbaarheid: Een voorheen onbekende kwetsbaarheid die aanvallers kunnen misbruiken voordat ontwikkelaars een patch hebben gemaakt en uitgerold.

## Bijlage B: Referenties

### TODO

## Bijlage C: AI-beveiligingsgovernance en documentatie

### Doel

Deze bijlage biedt fundamentele vereisten voor het opzetten van organisatorische structuren, beleidslijnen en processen om AI-veiligheid gedurende de gehele systeemlevenscyclus te waarborgen.

---

### AC.1 Adoptie van het AI risicobeheerkader

Bied een formeel raamwerk aan om AI‑specifieke risico's te identificeren, te beoordelen en te mitigeren gedurende de levenscyclus van het systeem.

 #AC.1.1    Niveau: 1    Rol: D/V
 Controleer of een AI-specifieke risicobeoordelingsmethodologie is gedocumenteerd en geïmplementeerd.
 #AC.1.2    Niveau: 2    Rol: D
 Verifieer dat risicobeoordelingen worden uitgevoerd op cruciale momenten in de AI-levenscyclus en vóór significante wijzigingen.
 #AC.1.3    Niveau: 3    Rol: D/V
 Controleer of het risicomanagementkader aansluit bij gevestigde normen (bijv. NIST AI RMF).

---

### AC.2 AI-beveiligingsbeleid en -procedures

Definieer en handhaaf organisatorische normen voor veilige AI-ontwikkeling, -inzet en -operatie.

 #AC.2.1    Niveau: 1    Rol: D/V
 Verifieer of er gedocumenteerd AI-beveiligingsbeleid bestaat.
 #AC.2.2    Niveau: 2    Rol: D
 Zorg ervoor dat beleidslijnen ten minste jaarlijks worden herzien en bijgewerkt, en na significante veranderingen in het bedreigings-landschap.
 #AC.2.3    Niveau: 3    Rol: D/V
 Verifieer dat beleidslijnen alle AISVS-categorieën en de toepasselijke regelgevingseisen adresseren.

---

### AC.3 Rollen en Verantwoordelijkheden voor AI-veiligheid

Zorg voor duidelijke verantwoording op het gebied van AI-veiligheid door de hele organisatie.

 #AC.3.1    Niveau: 1    Rol: D/V
 Verifieer of de AI-beveiligingsrollen en -verantwoordelijkheden zijn vastgelegd.
 #AC.3.2    Niveau: 2    Rol: D
 Controleer of verantwoordelijke personen over de passende beveiligingskennis beschikken.
 #AC.3.3    Niveau: 3    Rol: D/V
 Controleer of er een AI-ethiekcommissie of governance-raad is opgericht voor AI-systemen met hoog risico.

---

### AC.4 Handhaving van de ethische AI-richtlijnen

Zorg ervoor dat AI-systemen opereren volgens vastgestelde ethische principes.

 #AC.4.1    Niveau: 1    Rol: D/V
 Verifieer of ethische richtlijnen voor AI-ontwikkeling en inzet bestaan.
 #AC.4.2    Niveau: 2    Rol: D
 Verifieer dat er mechanismen zijn om ethische schendingen te detecteren en te melden.
 #AC.4.3    Niveau: 3    Rol: D/V
 Zorg ervoor dat regelmatige ethische beoordelingen van uitgerolde AI-systemen worden uitgevoerd.

---

### AC.5 AI-regelgeving nalevingsmonitoring

Blijf op de hoogte van de veranderende AI-regelgeving en voldoe aan deze regelgeving.

 #AC.5.1    Niveau: 1    Rol: D/V
 Verifieer of er processen bestaan om toepasselijke AI-regelgeving te identificeren.
 #AC.5.2    Niveau: 2    Rol: D
 Verifieer dat de naleving van alle regelgevende vereisten wordt beoordeeld.
 #AC.5.3    Niveau: 3    Rol: D/V
 Verifieer dat regelgevende wijzigingen tijdige evaluaties en updates aan AI-systemen teweegbrengen.

### AC.6 Trainingsdata governance, documentatie en proces

 #1.1.2    Niveau: 1    Rol: D/V
 Verifieer dat alleen datasets die zijn geverifieerd op kwaliteit, representativiteit, ethische herkomst en licentie-naleving toegestaan zijn, zodat de risico's op poisoning-aanvallen, verborgen bias en inbreuk op intellectueel eigendom worden verminderd.
 #1.1.5    Niveau: 2    Rol: D/V
 Controleer of de etikettering/annotatiekwaliteit gewaarborgd is via kruiscontroles door beoordelaars of consensus.
 #1.1.6    Niveau: 2    Rol: D/V
 Controleer of 'data cards' of 'datasheets for datasets' worden bijgehouden voor belangrijke trainingsdatasets, waarin kenmerken, motivaties, samenstelling, verzamelingsprocessen, preprocessing en aanbevolen/afgeraden toepassingen worden uiteengezet.
 #1.3.2    Niveau: 2    Rol: D/V
 Verifieer dat de geïdentificeerde biases zijn gemitigeerd via gedocumenteerde strategieën zoals herbalancering, gerichte data-augmentatie, algoritmische aanpassingen (bijv. voorverwerking, in-processing, post-processing-technieken) of herweging van gewichten, en dat de impact van mitigatie op zowel eerlijkheid als de algehele modelprestatie wordt beoordeeld.
 #1.3.3    Niveau: 2    Rol: D/V
 Controleer of na de training de eerlijkheidsmetingen worden geëvalueerd en gedocumenteerd.
 #1.3.4    Niveau: 3    Rol: D/V
 Controleer of een beleid voor biasbeheer gedurende de levenscyclus eigenaren toewijst en een beoordelingsritme vaststelt.
 #1.4.1    Niveau: 2    Rol: D/V
 Verifieer dat de kwaliteit van labeling/annotatie gewaarborgd is via duidelijke richtlijnen, controle door beoordelaars, consensusmechanismen (bijv. het monitoren van de inter-annotator-overeenstemming) en gedefinieerde processen voor het oplossen van afwijkingen.
 #1.4.4    Niveau: 3    Rol: D/V
 Verifieer dat labels die van cruciaal belang zijn voor veiligheid, beveiliging of eerlijkheid (bijv. het identificeren van toxische inhoud, cruciale medische bevindingen) een verplichte onafhankelijke dubbele beoordeling ontvangen of een equivalente robuuste verificatie.
 #1.4.6    Niveau: 2    Rol: D/V
 Verifieer of etiketteringsgidsen en instructies volledig zijn, met versiebeheer en door vakgenoten beoordeeld.
 #1.4.6    Niveau: 2    Rol: D/V
 Verifieer dat gegevensschema's voor labels duidelijk gedefinieerd zijn en onder versiebeheer staan.
 #1.3.1    Niveau: 1    Rol: D/V
 Verifieer of datasets zijn geprofileerd ten aanzien van representatieve onevenwichtigheid en potentiële vertekeningen bij wettelijk beschermde kenmerken (bijv. ras, geslacht, leeftijd) en andere ethisch gevoelige kenmerken die relevant zijn voor het toepassingsdomein van het model (bijv. sociaaleconomische status, locatie).
 #1.5.3    Niveau: 2    Rol: V
 Controleer dat handmatige spotcontroles door domeinexperts een statistisch significante steekproef omvatten (bijv. ≥1% of 1,000 monsters, afhankelijk van wat groter is, of zoals bepaald door de risicobeoordeling) om subtiele kwaliteitsproblemen te identificeren die niet door automatisering worden opgevangen.
 #1.8.4    Niveau: 2    Rol: D/V
 Verifieer of uitbesteedde of crowdsourced labeling-workflows technische/procedurele waarborgen bevatten om gegevensvertrouwelijkheid, integriteit en labelkwaliteit te waarborgen en gegevenslekken te voorkomen.
 #1.5.4    Niveau: 2    Rol: D/V
 Controleer of remediëringsstappen zijn toegevoegd aan provenantie-registraties.
 #1.6.2    Niveau: 2    Rol: D/V
 Verifieer dat gemarkeerde steekproeven een handmatige beoordeling triggeren vóór de training.
 #1.6.3    Niveau: 2    Rol: V
 Verifieer dat de resultaten het beveiligingsdossier van het model voeden en zorg voor lopende dreigingsinformatie.
 #1.6.4    Niveau: 3    Rol: D/V
 Controleer of de detectielogica is bijgewerkt met nieuwe bedreigingsinformatie.
 #1.6.5    Niveau: 3    Rol: D/V
 Controleer of online-lerende pijplijnen distributiedrift monitoren.
 #1.7.1    Niveau: 1    Rol: D/V
 Verifieer of workflows voor het verwijderen van trainingsdata primaire en afgeleide gegevens wissen en de impact op het model beoordelen, en of de impact op de getroffen modellen wordt beoordeeld en, indien nodig, aangepakt (bijv. door retraining of recalibratie).
 #1.7.2    Niveau: 2    Rol: D
 Controleer of er mechanismen aanwezig zijn om de reikwijdte en status van gebruikersinstemming (en intrekkingen) voor gegevens die voor training worden gebruikt bij te houden en te respecteren, en of toestemming wordt gevalideerd voordat gegevens worden opgenomen in nieuwe trainingsprocessen of aanzienlijke modelupdates.
 #1.7.3    Niveau: 2    Rol: V
 Controleer dat workflows jaarlijks worden getest en gelogd.
 #1.8.1    Niveau: 2    Rol: D/V
 Verifieer dat leveranciers van gegevens van derden, waaronder aanbieders van vooraf getrainde modellen en externe datasets, een zorgvuldigheidsonderzoek op het gebied van beveiliging, privacy, ethische inkoop en gegevenskwaliteit ondergaan voordat hun gegevens of modellen worden geïntegreerd.
 #1.8.2    Niveau: 1    Rol: D
 Verifieer dat externe overschrijvingen TLS/auth en integriteitscontroles gebruiken.
 #1.8.3    Niveau: 2    Rol: D/V
 Verifieer dat hoog-risico databronnen (bijv. open-source datasets met onbekende herkomst, niet-gecontroleerde leveranciers) een verhoogde toetsing ondergaan, zoals analyse in een sandbox, uitgebreide kwaliteits- en biascontroles en gerichte detectie van datavergiftiging, voordat ze worden gebruikt in gevoelige toepassingen.
 #1.8.4    Niveau: 3    Rol: D/V
 Verifieer dat voorgetrainde modellen die van derden zijn verkregen, worden geëvalueerd op ingebedde biases, potentiële achterdeuren, de integriteit van hun architectuur en de herkomst van hun oorspronkelijke trainingsgegevens voordat fine-tuning of inzet plaatsvindt.
 #1.5.3    Niveau: 2    Rol: D/V
 Verifieer dat, indien adversarial training wordt gebruikt, de generatie, het beheer en het versiebeheer van adversarial datasets gedocumenteerd en gecontroleerd zijn.
 #1.5.3    Niveau: 3    Rol: D/V
 Controleer of de impact van adversariale robuustheidstraining op de modelprestaties (tegen zowel schone als adversariale invoer) en fairness-metingen wordt geëvalueerd, gedocumenteerd en bewaakt.
 #1.5.4    Niveau: 3    Rol: D/V
 Controleer of strategieën voor adversariale training en robuustheid regelmatig worden beoordeeld en bijgewerkt om zich ontwikkelende adversariale aanvalstechnieken tegen te gaan.
 #1.4.2    Niveau: 2    Rol: D/V
 Controleer of mislukte datasets in quarantaine zijn geplaatst met auditsporen.
 #1.4.3    Niveau: 2    Rol: D/V
 Verifieer dat kwaliteitspoorten ondermaats datasets blokkeren, tenzij uitzonderingen zijn goedgekeurd.
 #1.11.2    Niveau: 2    Rol: D/V
 Controleer of het generatieproces, de parameters en het beoogde gebruik van synthetische data gedocumenteerd zijn.
 #1.11.3    Niveau: 2    Rol: D/V
 Controleer of synthetische data vóór gebruik voor training zijn beoordeeld op bias, privacylekken en representatieproblemen.
 #1.12.3    Niveau: 2    Rol: D/V
 Verifieer dat waarschuwingen worden gegenereerd voor verdachte toegangsgebeurtenissen en dat deze snel worden onderzocht.
 #1.13.1    Niveau: 1    Rol: D/V
 Controleer of expliciete bewaartermijnen zijn gedefinieerd voor alle trainingsdatasets.
 #1.13.2    Niveau: 2    Rol: D/V
 Verifieer dat datasets aan het einde van hun levenscyclus automatisch verlopen, verwijderd of ter verwijdering worden beoordeeld.
 #1.13.3    Niveau: 2    Rol: D/V
 Controleer of retentie- en verwijderingsacties gelogd en auditbaar zijn.
 #1.14.1    Niveau: 2    Rol: D/V
 Controleer of de vereisten voor gegevensresidentie en grensoverschrijdende gegevensoverdracht zijn geïdentificeerd en afgedwongen voor alle datasets.
 #1.14.2    Niveau: 2    Rol: D/V
 Controleer of sector-specifieke regelgeving (bijv. gezondheidszorg, financiën) wordt geïdentificeerd en aangepakt in de gegevensverwerking.
 #1.14.3    Niveau: 2    Rol: D/V
 Controleer of de naleving van relevante privacywetgeving (bijv. GDPR, CCPA) gedocumenteerd is en regelmatig wordt herzien.
 #1.16.1    Niveau: 2    Rol: D/V
 Verifieer dat er mechanismen bestaan om te reageren op verzoeken van betrokkenen voor inzage, rectificatie, beperking van de verwerking of bezwaar tegen de verwerking.
 #1.16.2    Niveau: 2    Rol: D/V
 Controleer of verzoeken worden vastgelegd, gevolgd en afgehandeld binnen de wettelijk voorgeschreven termijnen.
 #1.16.3    Niveau: 2    Rol: D/V
 Verifieer dat de processen voor de rechten van de betrokkenen regelmatig worden getest en beoordeeld op effectiviteit.
 #1.17.1    Niveau: 2    Rol: D/V
 Zorg ervoor dat er een impactanalyse wordt uitgevoerd voordat een datasetversie wordt bijgewerkt of vervangen, met betrekking tot modelprestaties, eerlijkheid en naleving.
 #1.17.2    Niveau: 2    Rol: D/V
 Controleer of de resultaten van de impactanalyse zijn gedocumenteerd en beoordeeld door de relevante belanghebbenden.
 #1.17.3    Niveau: 2    Rol: D/V
 Verifieer of rollback-plannen bestaan voor het geval dat nieuwe versies onaanvaardbare risico's of regressies introduceren.
 #1.18.1    Niveau: 2    Rol: D/V
 Verifieer dat al het personeel dat betrokken is bij data-annotatie een achtergrondcontrole heeft ondergaan en getraind is in gegevensbeveiliging en privacy.
 #1.18.2    Niveau: 2    Rol: D/V
 Controleer of alle annotatoren vertrouwelijkheids- en geheimhoudingsovereenkomsten ondertekenen.
 #1.18.3    Niveau: 2    Rol: D/V
 Controleer of annotatieplatformen toegangscontroles afdwingen en op interne dreigingen monitoren.

#### Referenties

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Bijlage D: AI-ondersteunde veilige codering governance en verificatie

### Doel

Dit hoofdstuk definieert basiscontroles op organisatorisch vlak voor het veilige en effectieve gebruik van AI-ondersteunde codeertools tijdens softwareontwikkeling, met waarborging van beveiliging en traceerbaarheid gedurende de SDLC.

---

### AD.1 AI-ondersteunde veilige coderingswerkstroom

Integreer AI-hulpmiddelen in de veilige-software-ontwikkelingslevenscyclus (SSDLC) van de organisatie zonder de bestaande beveiligingspoorten te verzwakken.

 #AD.1.1    Niveau: 1    Rol: D/V
 Verifieer dat een gedocumenteerde workflow beschrijft wanneer en hoe AI-tools code kunnen genereren, refactoren of reviewen.
 #AD.1.2    Niveau: 2    Rol: D
 Verifieer of de workflow overeenkomt met elke SSDLC-fase (ontwerp, implementatie, codebeoordeling, testen, uitrol).
 #AD.1.3    Niveau: 3    Rol: D/V
 Verifieer dat metingen (bijv. kwetsbaarheidsdichtheid, mean‑time‑to‑detect) worden verzameld op AI-geproduceerde code en vergeleken met baselines die uitsluitend door mensen zijn gemaakt.

---

### AD.2 AI-toolkwalificatie en dreigingsmodellering

Zorg ervoor dat AI-codeertools worden beoordeeld op beveiligingscapaciteiten, risico's en de impact op de toeleverings‑keten voordat ze in gebruik worden genomen.

 #AD.2.1    Niveau: 1    Rol: D/V
 Controleer of het dreigingsmodel voor elk AI-hulpmiddel misbruik, model‑inversion, gegevenslekken en afhankelijkheids‑ketenrisico's identificeert.
 #AD.2.2    Niveau: 2    Rol: D
 Controleer of de toolbeoordelingen een statische en dynamische analyse van eventuele lokale componenten bevatten en een beoordeling van SaaS-eindpunten (TLS, authenticatie/autorisatie, logging).
 #AD.2.3    Niveau: 3    Rol: D/V
 Controleer of evaluaties volgens een erkend raamwerk plaatsvinden en na grote versie-updates opnieuw worden uitgevoerd.

---

### Beveiligde Prompt & Contextbeheer

Voorkom lekkage van geheimen, auteursrechtelijk beschermde code en persoonlijke gegevens bij het opstellen van prompts of contexten voor AI-modellen.

 #AD.3.1    Niveau: 1    Rol: D/V
 Controleer of de schriftelijke richtlijnen het verzenden van geheimen, inloggegevens of geclassificeerde gegevens in prompts verbieden.
 #AD.3.2    Niveau: 2    Rol: D
 Controleer of technische controles (client‑side redactie, goedgekeurde contextfilters) automatisch gevoelige artefacten verwijderen.
 #AD.3.3    Niveau: 3    Rol: D/V
 Verifieer dat prompts en antwoorden getokeniseerd zijn, versleuteld tijdens verzending en in rust, en bewaartermijnen voldoen aan het gegevens-classificatiebeleid.

---

### AD.4 Validatie van AI‑gegenereerde code

Identificeer en verhelp kwetsbaarheden die door AI-uitvoer zijn geïntroduceerd voordat de code wordt samengevoegd of uitgerold.

 #AD.4.1    Niveau: 1    Rol: D/V
 Verifieer dat door AI‑gegenereerde code altijd aan een menselijke codebeoordeling onderworpen is.
 #AD.4.2    Niveau: 2    Rol: D
 Verifieer dat automatische scanners (SAST/IAST/DAST) op elke pull request die AI‑gegenereerde code bevat draaien en merges blokkeren bij kritieke bevindingen.
 #AD.4.3    Niveau: 3    Rol: D/V
 Verifieer of differentiële fuzzing of property‑gebaseerde tests beveiligingskritische gedragingen bewijzen (bijv. invoervalidatie, autorisatie-logica).

---

### AD.5 Verklaarbaarheid & Traceerbaarheid van Code-aanbevelingen

Bied auditors en ontwikkelaars inzicht in waarom een suggestie is gedaan en hoe deze zich heeft ontwikkeld.

 #AD.5.1    Niveau: 1    Rol: D/V
 Verifieer dat prompt/response-paaren worden gelogd met commit-ID's.
 #AD.5.2    Niveau: 2    Rol: D
 Controleer of ontwikkelaars in staat zijn om modelcitaten (trainingsfragmenten, documentatie) die een suggestie ondersteunen te tonen.
 #AD.5.3    Niveau: 3    Rol: D/V
 Controleer dat verklarbaarheidsrapporten samen met ontwerpartifacten worden opgeslagen en in beveiligingsbeoordelingen worden genoemd, waarbij wordt voldaan aan de traceerbaarheidsprincipes van ISO/IEC 42001.

---

### AD.6 Voortdurende Feedback & Model Fijn‑afstemming

Verbeter de beveiligingsprestaties van het model na verloop van tijd terwijl negatieve drift wordt voorkomen.

 #AD.6.1    Niveau: 1    Rol: D/V
 Controleer of ontwikkelaars onveilige of niet-conforme suggesties kunnen markeren en of de vlaggen worden bijgehouden.
 #AD.6.2    Niveau: 2    Rol: D
 Verifieer dat geaggregeerde feedback periodieke fine‑tuning of retrieval‑augmented generation informeert met geverifieerde secure‑coding corpora (bijv. OWASP Cheat Sheets).
 #AD.6.3    Niveau: 3    Rol: D/V
 Verifieer dat een gesloten‑lus evaluatieharnas regressietests uitvoert na elke fijn‑afstemming; beveiligingsmetrieken moeten voldoen aan of hoger zijn dan de eerdere basislijnen voordat ze worden ingezet.

---

#### Referenties

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Bijlage E: Voorbeelden van Hulpmiddelen en Raamwerken

### Doel

Dit hoofdstuk geeft voorbeelden van gereedschappen en frameworks die de implementatie of vervulling van een bepaalde AISVS-vereiste kunnen ondersteunen. Deze dienen niet te worden beschouwd als aanbevelingen of steunbetuigingen door het AISVS-team of het OWASP GenAI Security Project.

---

### AE.1 Trainingsdata-governance en biasbeheer

Gereedschappen die worden gebruikt voor data-analyse, datagovernance en biasbeheer.

 #AE.1.1    Sectie: 1.1
 Gegevensinventarishulpmiddelen: Hulpmiddelen voor gegevensinventarisbeheer zoals...
 #AE.1.2    Sectie: 1.2
 Encryptie-in-transit: Gebruik TLS voor HTTPS-gebaseerde toepassingen, met hulpmiddelen zoals OpenSSL en Python's`ssl` bibliotheek.

---

### AE.2 Gebruikersinvoervalidatie

Gereedschap om gebruikersinvoer te verwerken en te valideren.

 #AE.2.1    Sectie: 2.1
 Tooling voor verdediging tegen promptinjectie: Gebruik guardrail-tooling zoals NVIDIA's NeMo of Guardrails AI.

---

