## Forsideillustration

### Om standarden

Artificial Intelligence Security Verification Standard (AISVS) er en fællesskabsdrevet katalog over sikkerhedskrav, som dataforskere, MLOps-ingeniører, softwarearkitekter, udviklere, testere, sikkerhedsprofessionelle, leverandører af værktøjer, regulatorer og forbrugere kan bruge til at designe, udvikle, teste og verificere pålidelige AI-drevne systemer og applikationer. Det giver et fælles sprog til at specificere sikkerhedskontroller på tværs af AI-livscyklussen—fra dataindsamling og modeludvikling til implementering og løbende overvågning—så organisationer kan måle og forbedre modstandsdygtigheden, privatlivets fred og sikkerheden i deres AI-løsninger.

### Ophavsret og Licens

Version 0.1 (Første offentlige udkast - Under udarbejdelse), 2025  

![license](images/license.png)
Copyright © 2025 The AISVS Project.  

Udgivet under theCreative Commons Attribution‑ShareAlike 4.0 International License.
For enhver genbrug eller distribution skal du tydeligt formidle licensbetingelserne for dette arbejde til andre.

### Projektledere

Jim Manico
Aras “Russ” Memisyazici

### Bidragydere og anmeldere

https://github.com/ottosulin
https://github.com/mbhatt1
https://github.com/vineethsai
https://github.com/cciprofm
https://github.com/deepakrpandey12


---

AISVS er en helt ny standard, skabt specifikt til at håndtere de unikke sikkerhedsudfordringer i kunstige intelligenssystemer. Selvom den henter inspiration fra mere generelle sikkerhedsbedste praksis, er hvert krav i AISVS udviklet fra bunden for at afspejle trusselslandskabet inden for AI og hjælpe organisationer med at bygge sikrere, mere modstandsdygtige AI-løsninger.

## Forord

Velkommen til Artificial Intelligence Security Verification Standard (AISVS) version 1.0!

### Introduktion

Etableret i 2025 gennem en samarbejdende fællesskabsindsats definerer AISVS de sikkerhedskrav, der skal overvejes ved design, udvikling, udrulning og drift af moderne AI-modeller, pipelines og AI-aktiverede tjenester.

AISVS v1.0 repræsenterer det samlede arbejde fra dets projektledere, arbejdsgruppe og bredere samfundsbidragydere for at skabe en pragmatisk, testbar baseline for sikring af AI-systemer.

Vores mål med denne udgivelse er at gøre AISVS let at tage i brug, samtidig med at vi forbliver laserskarpt fokuserede på dets definerede omfang og adresserer det hurtigt udviklende risikobillede, der er unikt for AI.

### Nøglemål for AISVS Version 1.0

Version 1.0 vil blive oprettet med flere vejledende principper.

#### Veldefineret omfang

Hver krav skal stemme overens med AISVS’s navn og mission:

Kunstig intelligens – Kontroller fungerer på AI/ML-laget (data, model, pipeline eller inferens) og er ansvaret for AI-praktikere.
Sikkerhed – Kravene afhjælper direkte identificerede sikkerheds-, privatlivs- eller sikkerhedsrisici.
Verifikation – Sproget er skrevet, så overensstemmelse kan valideres objektivt.
Standard – Sektioner følger en konsekvent struktur og terminologi for at danne en sammenhængende reference.
​
---

Ved at følge AISVS kan organisationer systematisk evaluere og styrke sikkerhedspositionen for deres AI-løsninger og fremme en kultur for sikker AI-udvikling.

## Brug af AISVS

Den kunstige intelligens sikkerhedsverifikationsstandard (AISVS) definerer sikkerhedskrav for moderne AI-applikationer og -tjenester med fokus på aspekter, der ligger inden for applikationsudvikleres kontrol.

AISVS er beregnet til alle, der udvikler eller vurderer sikkerheden af AI-applikationer, herunder udviklere, arkitekter, sikkerhedsingeniører og revisorer. Dette kapitel introducerer strukturen og brugen af AISVS, herunder dets verifikationsniveauer og tilsigtede anvendelsestilfælde.

### Sikkerhedsgodkendelsesniveauer for kunstig intelligens

AISVS definerer tre stigende niveauer af sikkerhedsverifikation. Hvert niveau tilføjer dybde og kompleksitet, hvilket giver organisationer mulighed for at tilpasse deres sikkerhedsposition til risikoniveauet for deres AI-systemer.

Organisationer kan starte på Niveau 1 og gradvist adoptere højere niveauer, efterhånden som sikkerhedsmodenhed og trusselsniveau stiger.

#### Definition af niveauerne

Hvert krav i AISVS v1.0 tildeles et af følgende niveauer:

 Niveau 1 krav

Niveau 1 omfatter de mest kritiske og grundlæggende sikkerhedskrav. Disse fokuserer på at forhindre almindelige angreb, som ikke er afhængige af andre forudsætninger eller sårbarheder. De fleste kontrolforanstaltninger på Niveau 1 er enten enkle at implementere eller så væsentlige, at de retfærdiggør indsatsen.

 Krav på niveau 2

Niveau 2 omhandler mere avancerede eller mindre almindelige angreb samt lagdelte forsvar mod udbredte trusler. Disse krav kan involvere mere kompleks logik eller målrette specifikke forudsætninger for angreb.

 Krav for niveau 3

Niveau 3 inkluderer kontroller, der typisk er sværere at implementere eller anvendelige i særlige situationer. Disse repræsenterer ofte forsvar-i-dybden mekanismer eller afbødning mod nicheprægede, målrettede eller høj-kompleksitetsangreb.

#### Rolle (D/V)

Hvert AISVS-krav er markeret i henhold til den primære målgruppe:

D – Udviklerfokuserede krav
V – Krav med fokus på verificer/auditor
D/V – Relevant for både udviklere og verificatorer

## C1 Træningsdataforvaltning & Håndtering af bias

### Kontrolmål

Træningsdata skal indsamles, håndteres og vedligeholdes på en måde, der bevarer oprindelse, sikkerhed, kvalitet og retfærdighed. Dette opfylder juridiske forpligtelser og reducerer risikoen for bias, forgiftning eller brud på privatlivets fred, som kan opstå under træningen og påvirke hele AI-livscyklussen.

---

### C1.1 Oprindelse af træningsdata

Oprethold et verificerbart inventar over alle datasæt, accepter kun betroede kilder, og log hver ændring for revisionssikkerhed.

 #1.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at der vedligeholdes en opdateret oversigt over alle træningsdatakilder (oprindelse, forvalter/ejer, licens, indsamlingmetode, tilsigtede brugsbegrænsninger og behandlingshistorik).
 #1.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at træningsdata-processer udelukker unødvendige funktioner, attributter eller felter (f.eks. ubrugt metadata, følsomme persondata, lækket testdata).
 #1.1.3    Niveau: 2    Rolle: D/V
 Bekræft, at alle ændringer i datasættet er underlagt en registreret godkendelsesproces.
 #1.1.4    Niveau: 3    Rolle: D/V
 Sørg for, at datasæt eller delmængder er vandmærket eller fingeraftrykt, hvor det er muligt.

---

### C1.2 Sikkerhed og Integritet af Træningsdata

Begræns adgangen til træningsdata, krypter det både i hvile og under overførsel, og valider dets integritet for at forhindre manipulation, tyveri eller datamisbrug.

 #1.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at adgangskontroller beskytter lagring af træningsdata og pipelines.
 #1.2.2    Niveau: 2    Rolle: D/V
 Bekræft, at al adgang til træningsdata logges, inklusive bruger, tid og handling.
 #1.2.3    Niveau: 2    Rolle: D/V
 Bekræft, at træningsdatasæt er krypteret under overførsel og i hvile, ved brug af branchesstandard kryptografiske algoritmer og nøglehåndteringsmetoder.
 #1.2.4    Niveau: 2    Rolle: D/V
 Bekræft, at kryptografiske hashes eller digitale signaturer bruges til at sikre dataintegritet under lagring og overførsel af træningsdata.
 #1.2.5    Niveau: 2    Rolle: D/V
 Bekræft, at automatiserede detektionsteknikker anvendes til at beskytte mod uautoriserede ændringer eller korruption af træningsdata.
 #1.2.6    Niveau: 2    Rolle: D/V
 Sørg for, at forældede træningsdata bliver sikkert slettet eller anonymiseret.
 #1.2.7    Niveau: 3    Rolle: D/V
 Sørg for, at alle versioner af træningsdatasættet er entydigt identificeret, lagret uforanderligt og reviderbare for at understøtte tilbagetrækning og retsmedicinsk analyse.

---

### C1.3 Kvalitet, integritet og sikkerhed for træningsdatalabeling

Beskyt etiketter og kræv teknisk gennemgang for kritiske data.

 #1.3.1    Niveau: 2    Rolle: D/V
 Bekræft, at kryptografiske hashværdier eller digitale signaturer anvendes på mærkningsartefakter for at sikre deres integritet og ægthed.
 #1.3.2    Niveau: 2    Rolle: D/V
 Verificer, at mærkningsgrænseflader og platforme håndhæver stærke adgangskontroller, opretholder manipulationssikre revisionslogfiler for alle mærkningsaktiviteter og beskytter mod uautoriserede ændringer.
 #1.3.3    Niveau: 3    Rolle: D/V
 Bekræft, at følsomme oplysninger i etiketter er maskeret, anonymiseret eller krypteret på datafeltniveau både i hvile og under overførsel.

---

### C1.4 Kvalitet af træningsdata og sikring af sikkerhed

Kombiner automatiseret validering, manuel stikprøvekontrol og logget afhjælpning for at garantere datasæt-pålidelighed.

 #1.4.1    Niveau: 1    Rolle: D
 Bekræft, at automatiserede tests fanger formateringsfejl og null-værdier ved hver indlæsning eller væsentlig datatransformation.
 #1.4.2    Niveau: 2    Rolle: D/V
 Sørg for, at LLM-trænings- og finjusteringspipelines implementerer forgiftningsdetektion og validering af dataintegritet (f.eks. statistiske metoder, outlier-detektion, indlejringsanalyse) for at identificere potentielle forgiftningsangreb (f.eks. label-flipping, indsættelse af backdoor-triggers, rolleombytningskommandoer, indflydelsesrige instansangreb) eller utilsigtet datakorruption i træningsdata.
 #1.4.3    Niveau: 3    Rolle: D/V
 Bekræft, at passende forsvar, såsom modstridstræning (ved brug af genererede modstridende eksempler), dataforøgelse med perturbede input eller robuste optimeringsteknikker, er implementeret og justeret for relevante modeller baseret på risikovurdering.
 #1.4.4    Niveau: 2    Rolle: D/V
 Bekræft, at automatisk genererede etiketter (f.eks. via LLM'er eller svag supervision) er underlagt tillidsgrænser og konsistenskontroller for at opdage hallucinerede, vildledende eller lavtillids-etiketter.
 #1.4.5    Niveau: 3    Rolle: D
 Bekræft, at automatiserede tests opdager label-skævheder ved hver indlæsning eller væsentlig datatransformation.

---

### C1.5 Data Stifternes Oprindelse og Sporbarhed

Spor hele rejsen for hvert datapunkt fra kilde til modelinput for revisionssporbarhed og hændelsesrespons.

 #1.5.1    Niveau: 2    Rolle: D/V
 Bekræft, at afstamningen for hvert datapunkt, inklusive alle transformationer, augmentationer og sammenlægninger, er registreret og kan rekonstrueres.
 #1.5.2    Niveau: 2    Rolle: D/V
 Bekræft, at slægtsoplysninger er uforanderlige, sikkert opbevaret og tilgængelige til revision.
 #1.5.3    Niveau: 2    Rolle: D/V
 Bekræft, at sporing af oprindelse dækker syntetiske data, der genereres via privatlivsbevarende eller generative teknikker, og at alle syntetiske data tydeligt er mærket og kan skelnes fra rigtige data gennem hele processen.

---

### Referencer

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

## C2 Brugerinputvalidering

### Kontrolmål

Robust validering af brugerinput er en førstelinjeforsvar mod nogle af de mest skadelige angreb på AI-systemer. Prompt injection-angreb kan tilsidesætte systeminstruktioner, lække følsomme data eller styre modellen mod adfærd, der ikke er tilladt. Medmindre dedikerede filtre og instruktionshierarkier er på plads, viser forskning, at "multi-shot" jailbreaks, der udnytter meget lange kontekstvinduer, vil være effektive. Også subtile adversariale perturbationsangreb—såsom homoglyf-udskiftninger eller leetspeak—kan stille og roligt ændre en models beslutninger.

---

### C2.1 Forsvar mod promptinjektion

Prompt injection er en af de største risici for AI-systemer. Forsvar mod denne taktik anvender en kombination af statiske mønstermasker, dynamiske klassifikatorer og håndhævelse af instruktionshierarki.

 #2.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at brugerinput gennemgås mod et løbende opdateret bibliotek af kendte prompt-injektionsmønstre (jailbreak-nøgleord, "ignorer tidligere", rollespils-kæder, indirekte HTML/URL-angreb).
 #2.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at systemet håndhæver en instruktionshierarki, hvor system- eller udviklerbeskeder tilsidesætter brugerens instruktioner, selv efter udvidelse af kontekstvinduet.
 #2.1.3    Niveau: 2    Rolle: D/V
 Bekræft, at avancerede evaluerings-tests (f.eks. Red Team "many-shot" prompts) køres før hver model- eller prompt-skabelonudgivelse, med succesrategrænser og automatiserede blokeringer for regressioner.
 #2.1.4    Niveau: 2    Rolle: D
 Bekræft, at prompts, der stammer fra tredjepartsindhold (websider, PDF'er, e-mails), bliver renset i en isoleret parseringskontekst, inden de bliver sammenkædet i hovedprompten.
 #2.1.5    Niveau: 3    Rolle: D/V
 Bekræft, at alle opdateringer af prompt-filterregler, versioner af klassifikationsmodeller og ændringer i bloklisten er versionsstyrede og kan revideres.

---

### C2.2 Modstandsdygtighed over for adversarielle eksempler

Modeller inden for Natural Language Processing (NLP) er stadig sårbare over for subtile forstyrrelser på tegn- eller ordniveau, som mennesker ofte overser, men som modeller har tendens til at fejlkategorisere.

 #2.2.1    Niveau: 1    Rolle: D
 Bekræft, at grundlæggende inputnormaliseringstrin (Unicode NFC, homoglyphkortlægning, fjernelse af mellemrum) kører før tokenisering.
 #2.2.2    Niveau: 2    Rolle: D/V
 Bekræft, at statistisk anomalidetektion markerer input med usædvanligt høj redigeringsafstand til sprognormer, overdreven gentagelse af tokens eller unormale indlejringafstande.
 #2.2.3    Niveau: 2    Rolle: D
 Bekræft, at inferenspipelinens understøtter valgfrie modelvarianter eller forsvarslag for hærdning gennem modstandertræning (f.eks. randomisering, defensiv destillation) til højrisiko-endpoints.
 #2.2.4    Niveau: 2    Rolle: V
 Sørg for, at mistænkte fjendtlige input bliver sat i karantæne og logget med fulde nyttelaster (efter fjernelse af PII).
 #2.2.5    Niveau: 3    Rolle: D/V
 Sørg for, at robusthedsmål (succesrate for kendte angrebssuiter) overvåges over tid, og at tilbageskridt udløser en udgivelsesblokering.

---

### C2.3 Skema-, type- og længdevalidering

AI-angreb med skadede eller overdimensionerede input kan forårsage parsefejl, promptudslip på tværs af felter og ressourceudtømning. Streng skemahåndhævelse er også en forudsætning ved udførelse af deterministiske værktøjskald.

 #2.3.1    Niveau: 1    Rolle: D
 Bekræft, at hvert API- eller funktionskalds-endpoint definerer et eksplicit inputskema (JSON Schema, Protobuf eller multimodal ækvivalent) og at input valideres, før promptsamling sker.
 #2.3.2    Niveau: 1    Rolle: D/V
 Bekræft, at input, der overskrider de maksimale token- eller bytelimitter, afvises med en sikker fejl og aldrig bliver tavst afkortet.
 #2.3.3    Niveau: 2    Rolle: D/V
 Bekræft, at typekontroller (f.eks. numeriske intervaller, enum-værdier, MIME-typer for billeder/lyd) håndhæves på serversiden, ikke kun i klientkode.
 #2.3.4    Niveau: 2    Rolle: D
 Bekræft, at semantiske validatorer (f.eks. JSON Schema) kører i konstant tid for at forhindre algoritmisk DoS.
 #2.3.5    Niveau: 3    Rolle: V
 Bekræft, at valideringsfejl registreres med redigerede nyttedatauddrag og entydige fejlkoder for at lette sikkerhedstriangulering.

---

### C2.4 Indholds- og politikscreening

Udviklere bør kunne opdage syntaktisk gyldige prompts, der anmoder om ikke-tilladt indhold (såsom ulovlige instruktioner, hadetale og ophavsretligt beskyttet tekst), og derefter forhindre, at disse spredes.

 #2.4.1    Niveau: 1    Rolle: D
 Bekræft, at en indholdsklassificerer (zero shot eller finjusteret) scorer hvert input for vold, selvskade, had, seksuelt indhold og ulovlige anmodninger, med konfigurerbare tærskelværdier.
 #2.4.2    Niveau: 1    Rolle: D/V
 Bekræft, at input, der overtræder politikker, vil modtage standardiserede afvisninger eller sikre færdiggørelser, så de ikke videreføres til efterfølgende LLM-kald.
 #2.4.3    Niveau: 2    Rolle: D
 Bekræft, at screeningsmodellen eller regelsættet genuddannes/opdateres mindst kvartalsvis, og at nye observerede jailbreak- eller politikomgåelsesmønstre indarbejdes.
 #2.4.4    Niveau: 2    Rolle: D
 Bekræft, at screening overholder brugerspecifikke politikker (alder, regionale lovmæssige begrænsninger) via attributbaserede regler, der løses ved anmodningstidspunktet.
 #2.4.5    Niveau: 3    Rolle: V
 Bekræft, at screeningslogs inkluderer klassifikatorens tillidsvurderinger og politikkategori-tags til SOC-korrelation og fremtidig red-team genspilning.

---

### C2.5 Input Rate Begrænsning & Misbrugsforebyggelse

Udviklere bør forhindre misbrug, ressourceudtømning og automatiserede angreb mod AI-systemer ved at begrænse inputhastigheder og opdage unormale brugsmønstre.

 #2.5.1    Niveau: 1    Rolle: D/V
 Bekræft, at grænser for hastighed pr. bruger, pr. IP og pr. API-nøgle håndhæves for alle inputendepunkter.
 #2.5.2    Niveau: 2    Rolle: D/V
 Bekræft, at burst- og vedvarende hastighedsbegrænsninger er indstillet til at forhindre DoS- og brute force-angreb.
 #2.5.3    Niveau: 2    Rolle: D/V
 Bekræft, at unormale brugsmønstre (f.eks. hurtige anmodninger, input-overbelastning) udløser automatiserede blokeringer eller eskaleringer.
 #2.5.4    Niveau: 3    Rolle: V
 Bekræft, at logs for misbrugsforebyggelse opbevares og gennemgås for nye angrebsmønstre.

---

### C2.6 Multi-Modale Inputvalidering

AI-systemer bør inkludere robust validering af ikke-tekstuelle input (billeder, lyd, filer) for at forhindre injektion, unddragelse eller misbrug af ressourcer.

 #2.6.1    Niveau: 1    Rolle: D
 Bekræft, at alle ikke-tekst input (billeder, lyd, filer) valideres for type, størrelse og format før behandling.
 #2.6.2    Niveau: 2    Rolle: D/V
 Bekræft, at filer scannes for malware og steganografiske payloads før indtagelse.
 #2.6.3    Niveau: 2    Rolle: D/V
 Bekræft, at billede-/lydinput kontrolleres for fjendtlige forstyrrelser eller kendte angrebsmønstre.
 #2.6.4    Niveau: 3    Rolle: V
 Bekræft, at fejl i multimodal inputvalidering bliver logget og udløser advarsler til undersøgelse.

---

### C2.7 Input-kilde og attribution

AI-systemer bør understøtte revision, misbrugsregistrering og overholdelse ved at overvåge og mærke oprindelsen af alle brugerinput.

 #2.7.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle brugerinput er markeret med metadata (bruger-ID, session, kilde, tidsstempel, IP-adresse) ved indtagelse.
 #2.7.2    Niveau: 2    Rolle: D/V
 Bekræft, at oprindelsesmetadata bevares og kan revideres for alle behandlede input.
 #2.7.3    Niveau: 2    Rolle: D/V
 Bekræft, at anomaløse eller ikke-pålidelige inputkilder bliver markeret og underlagt forøget kontrol eller blokering.

---

### C2.8 Realtids Tilpasset Trusselsdetektion

Udviklere bør anvende avancerede trusselsdetekteringssystemer til AI, som tilpasser sig nye angrebsmønstre og giver realtidsbeskyttelse med kompileret mønstergenkendelse.

 #2.8.1    Niveau: 1    Rolle: D/V
 Bekræft, at trusselsdetektionsmønstre er kompileret til optimerede regex-motorer for højtydende realtidsfiltrering med minimal latensepåvirkning.
 #2.8.2    Niveau: 1    Rolle: D/V
 Sørg for, at trusselsdetekteringssystemer opretholder separate mønstrekataloger for forskellige trussels kategorier (promptinjektion, skadeligt indhold, følsomme data, systemkommandoer).
 #2.8.3    Niveau: 2    Rolle: D/V
 Bekræft, at adaptiv trusselsdetektion inkorporerer maskinlæringsmodeller, der opdaterer trusselsfølsomheden baseret på angrebsfrekvens og succesrater.
 #2.8.4    Niveau: 2    Rolle: D/V
 Bekræft, at realtids trusselsintelligensfeeds automatisk opdaterer mønst bibliotekker med nye angrebssignaturer og IOCs (Indicators of Compromise).
 #2.8.5    Niveau: 3    Rolle: D/V
 Bekræft, at falske positive fejlrater for trusselsdetektion løbende overvåges, og at mønsterspecificiteten automatisk tilpasses for at minimere forstyrrelser af legitime brugsscenarier.
 #2.8.6    Niveau: 3    Rolle: D/V
 Bekræft, at kontekstuel trusselsanalyse tager hensyn til inputkilde, brugeradfærdsmønstre og sessionshistorik for at forbedre detektionsnøjagtigheden.
 #2.8.7    Niveau: 3    Rolle: D/V
 Bekræft, at ydelsesmetriker for trusselsdetektion (detektionsrate, behandlingstidsforsinkelse, ressourceudnyttelse) overvåges og optimeres i realtid.

---

### C2.9 Multi-Modal sikkerhedsvalideringspipeline

Udviklere bør levere sikkerhedsvalidering for tekst-, billede-, lyd- og andre AI-inputmodaliteter med specifikke typer trusselsdetektion og ressourceisolation.

 #2.9.1    Niveau: 1    Rolle: D/V
 Bekræft, at hver inputmodalitet har dedikerede sikkerhedsvalidatorer med dokumenterede trusselsmønstre (tekst: promptinjektion, billeder: steganografi, lyd: spektrogramangreb) og detektionsgrænser.
 #2.9.2    Niveau: 2    Rolle: D/V
 Bekræft, at multimodale input behandles i isolerede sandkasser med definerede ressourcebegrænsninger (hukommelse, CPU, behandlingstid), som er specifikke for hver modalitytype og dokumenteret i sikkerhedspolitikker.
 #2.9.3    Niveau: 2    Rolle: D/V
 Bekræft, at detektionssystemet for tværmodal angreb identificerer koordinerede angreb, der spænder over flere inputtyper (f.eks. steganografiske payloads i billeder kombineret med promptinjektion i tekst) ved hjælp af korrelationsregler og alarmering.
 #2.9.4    Niveau: 3    Rolle: D/V
 Bekræft, at multi-modale valideringsfejl udløser detaljeret logning, inklusive alle inputmodaliteter, valideringsresultater, trusselscores og korrelationsanalyse med strukturerede logformater til SIEM-integration.
 #2.9.5    Niveau: 3    Rolle: D/V
 Bekræft, at modalitetsspecifikke indholdsklassifikatorer opdateres i overensstemmelse med dokumenterede tidsplaner (minimum kvartalsvis) med nye trusselsmønstre, adversarielle eksempler og ydeevnebenchmark, der opretholdes over baseline-grænser.

---

### Referencer

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

## C3 Model Livscyklusstyring & Ændringskontrol

### Kontrolmål

AI-systemer skal implementere ændringskontrolprocesser, der forhindrer uautoriserede eller usikre modelændringer i at nå produktionen. Denne kontrol sikrer modelintegritet gennem hele livscyklussen – fra udvikling gennem implementering til udfasning – hvilket muliggør hurtig hændelsesrespons og opretholder ansvarlighed for alle ændringer.

Kerne Sikkerhedsmål: Kun autoriserede, validerede modeller når produktion ved brug af kontrollerede processer, der opretholder integritet, sporbarhed og genoprettelighed.

---

### C3.1 Modelautorisation og integritet

Kun autoriserede modeller med verificeret integritet når produktionsmiljøer.

 #3.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle modelartefakter (vægt, konfigurationer, tokenizere) er kryptografisk underskrevet af autoriserede enheder før implementering.
 #3.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at modelintegriteten valideres ved implementeringstidspunktet, og at underskriftsverifikationsfejl forhindrer indlæsning af modellen.
 #3.1.3    Niveau: 2    Rolle: D/V
 Bekræft, at modelproveniensregistreringer indeholder en autoriserende enheds identitet, checksums for træningsdata, valideringstestresultater med bestået/ikke-bestået status og et oprettelsestidsstempel.
 #3.1.4    Niveau: 2    Rolle: D/V
 Bekræft, at alle modelartefakter bruger semantisk versionering (MAJOR.MINOR.PATCH) med dokumenterede kriterier, der specificerer, hvornår hver versionskomponent øges.
 #3.1.5    Niveau: 2    Rolle: V
 Bekræft, at afhængighedssporing opretholder et realtidslager, som muliggør hurtig identifikation af alle forbrugende systemer.

---

### C3.2 Modelvalidering og testning

Modeller skal bestå definerede sikkerheds- og tryghedsgodkendelser før implementering.

 #3.2.1    Niveau: 1    Rolle: D/V
 Sørg for, at modeller gennemgår automatiseret sikkerhedstestning, der inkluderer inputvalidering, outputsanitering og sikkerhedsevalueringer med forudbestemte organisatoriske beståelses-/ikke-beståelsesgrænser, før de implementeres.
 #3.2.2    Niveau: 1    Rolle: D/V
 Bekræft, at valideringsfejl automatisk blokerer modeludrulning efter eksplicit overstyringsgodkendelse fra forudbestemte autoriserede personer med dokumenterede forretningsmæssige begrundelser.
 #3.2.3    Niveau: 2    Rolle: V
 Bekræft, at testresultater er kryptografisk underskrevet og uforanderligt knyttet til den specifikke modelversions hash, der valideres.
 #3.2.4    Niveau: 2    Rolle: D/V
 Bekræft, at nødudrulninger kræver dokumenteret sikkerhedsrisikovurdering og godkendelse fra en forudbestemt sikkerhedsmyndighed inden for forhåndsaftalte tidsfrister.

---

### C3.3 Kontrolleret Udrulning & Tilbageførsel

Modelimplementeringer skal kontrolleres, overvåges og være reversible.

 #3.3.1    Niveau: 1    Rolle: D
 Bekræft, at produktionsudrulninger implementerer gradvise udrulningsmekanismer (canary-udrulninger, blue-green-udrulninger) med automatiserede rollback-trigger baseret på forud aftalte fejlprocenter, latenstærskler eller sikkerhedsalarmeringskriterier.
 #3.3.2    Niveau: 1    Rolle: D/V
 Bekræft, at rollback-funktioner gendanner hele modeltilstanden (vægtninger, konfigurationer, afhængigheder) atomisk inden for foruddefinerede organisatoriske tidsvinduer.
 #3.3.3    Niveau: 2    Rolle: D/V
 Bekræft, at implementeringsprocesser validerer kryptografiske signaturer og beregner integritetskontrolsummer før modelaktivering, og at implementeringen mislykkes ved enhver uoverensstemmelse.
 #3.3.4    Niveau: 2    Rolle: D/V
 Bekræft, at nødafbrydelsesfunktioner for modellen kan deaktivere modelendepunkter inden for foruddefinerede svartider via automatiserede afbrydere eller manuelle dræberkontakter.
 #3.3.5    Niveau: 2    Rolle: V
 Bekræft, at rollback-artifakter (tidligere modelversioner, konfigurationer, afhængigheder) opbevares i overensstemmelse med organisationspolitikker med uforanderlig lagring til hændelsesrespons.

---

### C3.4 Ændringsansvar og Revision

Alle ændringer i modellens livscyklus skal kunne spores og revideres.

 #3.4.1    Niveau: 1    Rolle: V
 Bekræft, at alle modelændringer (implementering, konfiguration, pensionering) genererer uforanderlige revisionsposter, der inkluderer et tidsstempel, en autentificeret aktøridentitet, en ændringstype samt tilstande før og efter ændringen.
 #3.4.2    Niveau: 2    Rolle: D/V
 Bekræft, at adgang til revisionslog kræver passende autorisation, og at alle adgangsforsøg logges med brugeridentitet og et tidsstempel.
 #3.4.3    Niveau: 2    Rolle: D/V
 Bekræft, at promptskabeloner og systemmeddelelser er versionskontrolleret i git-repositorier med obligatorisk kodegennemgang og godkendelse fra udpegede anmeldere før implementering.
 #3.4.4    Niveau: 2    Rolle: V
 Bekræft, at revisionsposter indeholder tilstrækkelige detaljer (modelhashes, konfigurationsøjebliksbilleder, afhængighedsudgaver) for at muliggøre fuldstændig genskabelse af modeltilstanden for et vilkårligt tidsstempel inden for opbevaringsperioden.

---

### C3.5 Sikker udviklingspraksis

Modeludviklings- og træningsprocesser skal følge sikre praksisser for at forhindre kompromittering.

 #3.5.1    Niveau: 1    Rolle: D
 Verificer, at modeludviklings-, test- og produktionsmiljøer er fysisk eller logisk adskilte. De må ikke have delt infrastruktur, meningsfulde adgangskontroller og isolerede datalagre.
 #3.5.2    Niveau: 1    Rolle: D
 Bekræft, at modeltræning og finjustering foregår i isolerede miljøer med kontrolleret netværksadgang.
 #3.5.3    Niveau: 1    Rolle: D/V
 Bekræft, at træningsdatakilder valideres gennem integritetskontroller og autentificeres via betroede kilder med dokumenteret ansvarskæde, før de bruges i modeludvikling.
 #3.5.4    Niveau: 2    Rolle: D
 Bekræft, at modeludviklingsartefakter (hyperparametre, træningsscripts, konfigurationsfiler) gemmes i versionskontrol og kræver godkendelse fra kollegaer, før de anvendes i træning.

---

### C3.6 Model Pensionering & Udrangering

Modeller skal sikkert udfases, når de ikke længere er nødvendige, eller når sikkerhedsproblemer identificeres.

 #3.6.1    Niveau: 1    Rolle: D
 Bekræft, at modelafviklingsprocesser automatisk gennemgår afhængighedsgrafer, identificerer alle forbrugende systemer og giver forhåndsaftalte varselsperioder, inden afvikling.
 #3.6.2    Niveau: 1    Rolle: D/V
 Bekræft, at pensionerede modelartefakter slettes sikkert ved hjælp af kryptografisk sletning eller multi-pass overskrivning i overensstemmelse med dokumenterede politikker for datalagring med verificerede destruktionscertifikater.
 #3.6.3    Niveau: 2    Rolle: V
 Bekræft, at modelpensio-neringsbegivenheder logges med tidsstempel og aktøridentitet, og at model-signaturer tilbagekaldes for at forhindre genbrug.
 #3.6.4    Niveau: 2    Rolle: D/V
 Bekræft, at nødmodel-fasthævelse kan deaktivere modeladgang inden for forudbestemte nødresponstidsrammer via automatiserede afbrydelsesbryder, hvis kritiske sikkerheds-sårbarheder opdages.

---

### Referencer

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

## C4 Infrastruktur, Konfiguration & Udrulningssikkerhed

### Kontrolmål

AI-infrastruktur skal gøres modstandsdygtig over for privilegieeskalering, manipulation af forsyningskæden og lateral bevægelse gennem sikker konfiguration, runtime-isolering, betroede deployments pipelines og omfattende overvågning. Kun autoriserede, validerede infrastrukturkomponenter og konfigurationer når produktion gennem kontrollerede processer, der opretholder sikkerhed, integritet og revisionsevne.

Kerne Sikkerhedsmål: Kun kryptografisk signerede, sårbarhedsscannede infrastrukturobjekter når produktion gennem automatiserede valideringspipelines, som håndhæver sikkerhedspolitikker og opretholder uforanderlige revisionsspor.

---

### C4.1 Runtime-miljøisolering

Forhindr container-udbrud og rettighedsoptrapning gennem kerne-niveau isolationsprimitiver og obligatoriske adgangskontroller.

 #4.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle AI-containere fjerner ALLE Linux-evner undtagen CAP_SETUID, CAP_SETGID samt eksplicit påkrævede evner dokumenteret i sikkerhedsbaselines.
 #4.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at seccomp-profiler blokerer alle systemkald undtagen dem, der er på forhånd godkendte tilladelseslister, hvor overtrædelser fører til, at containeren afsluttes, og der genereres sikkerhedsalarmer.
 #4.1.3    Niveau: 2    Rolle: D/V
 Bekræft, at AI-arbejdsbelastninger kører med skrivebeskyttede rodfilsystemer, tmpfs til midlertidige data og navngivne volumener til vedvarende data med noexec monteringsmuligheder håndhævet.
 #4.1.4    Niveau: 2    Rolle: D/V
 Bekræft, at eBPF-baseret runtime-overvågning (Falco, Tetragon eller tilsvarende) opdager forsøg på privilegieoptrapning og automatisk dræber krænkende processer inden for organisationens svartidskrav.
 #4.1.5    Niveau: 3    Rolle: D/V
 Bekræft, at højrisiko AI-arbejdsbelastninger kører i hardware-isolerede miljøer (Intel TXT, AMD SVM eller dedikerede bare-metal noder) med attestationsverifikation.

---

### C4.2 Sikker build- og deployments-pipelines

Sikre kryptografisk integritet og forsyningskædesikkerhed gennem reproducerbare builds og underskrevne artefakter.

 #4.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at infrastruktur-som-kode bliver scannet med værktøjer (tfsec, Checkov eller Terrascan) ved hver commit, og at merges blokeres ved fund af KRITISKE eller HØJ alvorlighedsgrad.
 #4.2.2    Niveau: 1    Rolle: D/V
 Bekræft, at containerbygninger er reproducerbare med identiske SHA256-hashværdier på tværs af builds, og generer SLSA niveau 3 oprindelsesattester underskrevet med Sigstore.
 #4.2.3    Niveau: 2    Rolle: D/V
 Bekræft, at containerbilleder indeholder CycloneDX- eller SPDX SBOM'er og er signeret med Cosign, før de skubbes til registreringsdatabasen, hvor usignerede billeder afvises ved implementering.
 #4.2.4    Niveau: 2    Rolle: D/V
 Bekræft, at CI/CD-pipelines bruger OIDC-tokens fra HashiCorp Vault, AWS IAM-roller eller Azure Managed Identity med levetider, der ikke overstiger organisationens sikkerhedspolitiske grænser.
 #4.2.5    Niveau: 2    Rolle: D/V
 Bekræft, at Cosign-signaturer og SLSA-proveniens valideres under udrulningsprocessen før container-eksekvering, og at verificeringsfejl får udrulningen til at fejle.
 #4.2.6    Niveau: 2    Rolle: D/V
 Bekræft, at bygge-miljøer kører i flygtige containere eller virtuelle maskiner uden vedvarende lagring og med netværks-isolering fra produktions VPC’er.

---

### C4.3 Netværkssikkerhed & Adgangskontrol

Implementer zero-trust netværk med standard-afvis-politikker og krypteret kommunikation.

 #4.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at Kubernetes NetworkPolicies eller en tilsvarende løsning implementerer default-deny ingress/egress med eksplicitte tilladelsesregler for nødvendige porte (443, 8080, osv.).
 #4.3.2    Niveau: 1    Rolle: D/V
 Bekræft, at SSH (port 22), RDP (port 3389) og cloud metadata-endpoints (169.254.169.254) er blokeret eller kræver certifikatbaseret autentificering.
 #4.3.3    Niveau: 2    Rolle: D/V
 Bekræft, at egress-trafik filtreres gennem HTTP/HTTPS-proxies (Squid, Istio eller cloud NAT-gateways) med domænetilladelseslister, og at blokerede forespørgsler logges.
 #4.3.4    Niveau: 2    Rolle: D/V
 Bekræft, at inter-service kommunikation anvender mutual TLS med certifikater, der roteres i henhold til organisationspolitikken, og at certifikatvalidering håndhæves (ingen skip-verify flag).
 #4.3.5    Niveau: 2    Rolle: D/V
 Bekræft, at AI-infrastrukturen kører i dedikerede VPC'er/VNets uden direkte internetadgang og kun kommunikerer gennem NAT-gateways eller bastionhosts.

---

### C4.4 Hemmeligheder og kryptografisk nøglehåndtering

Beskyt legitimationsoplysninger gennem hardware-baseret lagring og automatiseret rotation med zero-trust adgang.

 #4.4.1    Niveau: 1    Rolle: D/V
 Bekræft, at hemmeligheder opbevares i HashiCorp Vault, AWS Secrets Manager, Azure Key Vault eller Google Secret Manager med kryptering ved hvile ved brug af AES-256.
 #4.4.2    Niveau: 1    Rolle: D/V
 Bekræft, at kryptografiske nøgler genereres i FIPS 140-2 Level 2 HSM'er (AWS CloudHSM, Azure Dedicated HSM) med nøgleudskiftning i overensstemmelse med den organisatoriske kryptografipolitik.
 #4.4.3    Niveau: 2    Rolle: D/V
 Bekræft, at automatisk rotation af hemmeligheder sker med nul nedetid ved implementering og øjeblikkelig rotation udløst af personaleændringer eller sikkerhedshændelser.
 #4.4.4    Niveau: 2    Rolle: D/V
 Bekræft, at containerbilleder scannes med værktøjer (GitLeaks, TruffleHog eller detect-secrets), der blokerer builds, der indeholder API-nøgler, adgangskoder eller certifikater.
 #4.4.5    Niveau: 2    Rolle: D/V
 Bekræft, at adgang til produktionshemmeligheder kræver MFA med hardwaretokens (YubiKey, FIDO2) og registreres i uforanderlige revisionslogfiler med brugeridentiteter og tidsstempler.
 #4.4.6    Niveau: 2    Rolle: D/V
 Bekræft, at hemmeligheder indsættes via Kubernetes-hemmeligheder, monterede volumener eller init-containere, og sørg for, at hemmeligheder aldrig indlejres i miljøvariabler eller billeder.

---

### C4.5 AI Arbejdsbelastnings-sandkasse og validering

Isoler uautoriserede AI-modeller i sikre sandkasser med omfattende adfærdsanalyse.

 #4.5.1    Niveau: 1    Rolle: D/V
 Bekræft, at eksterne AI-modeller kører i gVisor, microVMs (såsom Firecracker, CrossVM) eller Docker-containere med --security-opt=no-new-privileges og --read-only flag.
 #4.5.2    Niveau: 1    Rolle: D/V
 Bekræft, at sandbox-miljøer ikke har netværksforbindelse (--network=none) eller kun adgang til localhost, hvor alle eksterne forespørgsler blokeres af iptables-regler.
 #4.5.3    Niveau: 2    Rolle: D/V
 Bekræft, at validering af AI-modeller inkluderer automatiseret red-team testning med organisatorisk defineret testdækning og adfærdsanalyse til bagdørsdetektion.
 #4.5.4    Niveau: 2    Rolle: D/V
 Bekræft, at før en AI-model promoveres til produktion, er dens sandbox-resultater kryptografisk underskrevet af autoriseret sikkerhedspersonale og gemt i uforanderlige revisionslogfiler.
 #4.5.5    Niveau: 2    Rolle: D/V
 Bekræft, at sandkassemiljøer bliver ødelagt og genskabt fra gyldne billeder mellem evalueringerne med fuldstændig oprydning af filsystem og hukommelse.

---

### C4.6 Infrastruktur Sikkerhedsovervågning

Kontinuerligt scanne og overvåge infrastrukturen med automatiseret udbedring og realtidsadvarsler.

 #4.6.1    Niveau: 1    Rolle: D/V
 Bekræft, at containerbilleder bliver scannet i henhold til organisatoriske tidsplaner, hvor KRITISKE sårbarheder blokerer implementering baseret på organisatoriske risikothresholds.
 #4.6.2    Niveau: 1    Rolle: D/V
 Bekræft, at infrastrukturen overholder CIS Benchmarks eller NIST 800-53-kontroller med organisatorisk definerede overholdelsestærskler og automatiseret afhjælpning for mislykkede kontroller.
 #4.6.3    Niveau: 2    Rolle: D/V
 Verificer, at sårbarheder med HØJ alvorlighed bliver patchet i overensstemmelse med organisationens risikostyringstidslinjer, med nødprocedurer for aktivt udnyttede CVE'er.
 #4.6.4    Niveau: 2    Rolle: V
 Bekræft, at sikkerhedsalarmer integreres med SIEM-platforme (Splunk, Elastic eller Sentinel) ved hjælp af CEF- eller STIX/TAXII-formater med automatiseret berigelse.
 #4.6.5    Niveau: 3    Rolle: V
 Verificer, at infrastrukturmålinger eksporteres til overvågningssystemer (Prometheus, DataDog) med SLA-dashboard og ledelsesrapportering.
 #4.6.6    Niveau: 2    Rolle: D/V
 Verificer, at konfigurationsafvigelse opdages ved brug af værktøjer (Chef InSpec, AWS Config) i henhold til organisatoriske overvågningskrav med automatisk tilbageførsel for uautoriserede ændringer.

---

### C4.7 AI Infrastruktur Ressourcehåndtering

Forebyg ressourceudtrætningsangreb og sikr retfærdig ressourcefordeling gennem kvoter og overvågning.

 #4.7.1    Niveau: 1    Rolle: D/V
 Bekræft, at GPU/TPU-udnyttelse overvåges med alarmer, der aktiveres ved organisatorisk definerede tærskler, og at automatisk skalering eller loadbalancering aktiveres baseret på kapacitetsstyringspolitikker.
 #4.7.2    Niveau: 1    Rolle: D/V
 Bekræft, at AI-arbejdsbyrdemålinger (inferenzlatens, gennemløb, fejlprocenter) indsamles i overensstemmelse med organisatoriske overvågningskrav og korreleres med infrastrukturudnyttelsen.
 #4.7.3    Niveau: 2    Rolle: D/V
 Verificer, at Kubernetes ResourceQuotas eller tilsvarende begrænser individuelle arbejdsbelastninger i henhold til organisatoriske ressourcetildelingspolitikker med håndhævede hårde grænser.
 #4.7.4    Niveau: 2    Rolle: V
 Bekræft, at omkostningsovervågning sporer forbrug pr. arbejdsbyrde/lejer med alarmer baseret på organisatoriske budgetgrænser og automatiserede kontroller for budgetoverskridelser.
 #4.7.5    Niveau: 3    Rolle: V
 Bekræft, at kapacitetsplanlægning bruger historiske data med organisationsdefinerede prognoseperioder og automatiseret ressourceallokering baseret på efterspørgselsmønstre.
 #4.7.6    Niveau: 2    Rolle: D/V
 Bekræft, at ressourceudmattelse udløser kredsløbsafbrydere i henhold til organisatoriske responskrav, herunder hastighedsbegrænsning baseret på kapacitets-politikker og arbejdsbelastningsisolation.

---

### C4.8 Adskillelse af miljøer og kontrol med promotion

Håndhæv strenge miljøgrænser med automatiserede promoveringsporte og sikkerhedsvalidering.

 #4.8.1    Niveau: 1    Rolle: D/V
 Bekræft, at dev/test/prod-miljøer kører i separate VPC’er/VNets uden delte IAM-roller, sikkerhedsgrupper eller netværksforbindelser.
 #4.8.2    Niveau: 1    Rolle: D/V
 Bekræft, at forfremmelse af miljøet kræver godkendelse fra organisatorisk defineret autoriseret personale med kryptografiske signaturer og uforanderlige revisionsspor.
 #4.8.3    Niveau: 2    Rolle: D/V
 Bekræft, at produktionsmiljøer blokerer SSH-adgang, deaktiverer debug-endpoints og kræver ændringsanmodninger med organisatoriske varslingskrav på forhånd, undtagen i nødstilfælde.
 #4.8.4    Niveau: 2    Rolle: D/V
 Bekræft, at infrastruktur-som-kode ændringer kræver peer review med automatiseret testning og sikkerhedsscanning, inden de flettes til hovedgrenen.
 #4.8.5    Niveau: 2    Rolle: D/V
 Bekræft, at ikke-produktionsdata er anonymiseret i overensstemmelse med organisatoriske privatlivskrav, syntetisk datagenerering eller komplet datamaskering med verificeret fjernelse af personligt identificerbare oplysninger (PII).
 #4.8.6    Niveau: 2    Rolle: D/V
 Bekræft, at promotionsporte inkluderer automatiserede sikkerhedstest (SAST, DAST, container scanning) med krav om nul KRITISKE fund for godkendelse.

---

### C4.9 Infrastruktur Backup & Gendannelse

Sikre infrastrukturens robusthed gennem automatiserede backups, testede genoprettelsesprocedurer og katastrofeberedskabskapaciteter.

 #4.9.1    Niveau: 1    Rolle: D/V
 Bekræft, at infrastrukturkonfigurationer sikkerhedskopieres i overensstemmelse med organisationens backup-planer til geografisk adskilte regioner med implementering af 3-2-1 backup-strategi.
 #4.9.2    Niveau: 2    Rolle: D/V
 Bekræft, at backup-systemer kører i isolerede netværk med separate legitimationsoplysninger og luftadskilt lagring for beskyttelse mod ransomware.
 #4.9.3    Niveau: 2    Rolle: V
 Bekræft, at genoprettelsesprocedurer testes og valideres gennem automatiseret test i henhold til organisatoriske tidsplaner, hvor RTO- og RPO-mål opfylder organisationens krav.
 #4.9.4    Niveau: 3    Rolle: V
 Bekræft, at katastrofe-genopretning inkluderer AI-specifikke runbooks med modelvægt-gendannelse, genopbygning af GPU-klynger og kortlægning af servicedependenser.

---

### C4.10 Infrastrukturoverholdelse og -styring

Oprethold overholdelse af regler gennem kontinuerlig vurdering, dokumentation og automatiserede kontrolforanstaltninger.

 #4.10.1    Niveau: 2    Rolle: D/V
 Bekræft, at infrastrukturens overholdelse vurderes i henhold til organisatoriske tidsplaner mod SOC 2, ISO 27001 eller FedRAMP-kontroller med automatiseret indsamling af bevismateriale.
 #4.10.2    Niveau: 2    Rolle: V
 Sørg for, at infrastrukturens dokumentation inkluderer netværksdiagrammer, dataflowkort og trusselsmodeller, der er opdateret i henhold til organisationens krav til ændringsstyring.
 #4.10.3    Niveau: 3    Rolle: D/V
 Sørg for, at infrastrukturændringer gennemgår automatiseret vurdering af compliance-påvirkning med regulatoriske godkendelsesarbejdsgange for højrisikomodifikationer.

---

### C4.11 AI Hardware Sikkerhed

Sikre AI-specifikke hardwarekomponenter, herunder GPU'er, TPU'er og specialiserede AI-acceleratorer.

 #4.11.1    Niveau: 2    Rolle: D/V
 Bekræft, at AI-accelerator firmware (GPU BIOS, TPU firmware) er verificeret med kryptografiske signaturer og opdateret i overensstemmelse med organisationens patch-management tidsplaner.
 #4.11.2    Niveau: 2    Rolle: D/V
 Bekræft, at inden arbejdsbelastningens udførelse valideres AI-acceleratorens integritet ved hardwareattestation ved hjælp af TPM 2.0, Intel TXT eller AMD SVM.
 #4.11.3    Niveau: 2    Rolle: D/V
 Verificer, at GPU-hukommelsen er isoleret mellem arbejdsbelastninger ved brug af SR-IOV, MIG (Multi-Instance GPU) eller tilsvarende hardwarepartitionering med hukommelsessanitering mellem opgaver.
 #4.11.4    Niveau: 3    Rolle: V
 Bekræft, at AI-hardwareforsyningskæden inkluderer oprindelsesverifikation med producentcertifikater og validering af manipulationssikkert emballage.
 #4.11.5    Niveau: 3    Rolle: D/V
 Bekræft, at hardware-sikkerhedsmoduler (HSM'er) beskytter AI-modelvægt og kryptografiske nøgler med FIPS 140-2 Level 3 eller Common Criteria EAL4+ certificering.

---

### C4.12 Edge & Distribueret AI Infrastruktur

Sikre distribuerede AI-implementeringer inklusive edge computing, fødereret læring og multi-site arkitekturer.

 #4.12.1    Niveau: 2    Rolle: D/V
 Bekræft, at edge AI-enheder autentificerer til den centrale infrastruktur ved hjælp af mutual TLS med enhedscertifikater, der roteres i henhold til organisationens politik for certifikatadministration.
 #4.12.2    Niveau: 2    Rolle: D/V
 Bekræft, at edge-enheder implementerer secure boot med verificerede signaturer og rollback-beskyttelse, der forhindrer firmware-nedgraderingsangreb.
 #4.12.3    Niveau: 3    Rolle: D/V
 Bekræft, at distribueret AI-koordinering bruger byzantinsk fejltolerante konsensusalgoritmer med deltagervalidering og detektion af ondsindede noder.
 #4.12.4    Niveau: 3    Rolle: D/V
 Bekræft, at kommunikation fra edge til cloud inkluderer båndbreddebegrænsning, datakomprimering og offline driftsmuligheder med sikker lokal lagring.

---

### C4.13 Sikkerhed i Multi-Cloud og Hybrid Infrastruktur

Sikre AI-arbejdsmængder på tværs af flere cloud-udbydere og hybride cloud-on-premises implementeringer.

 #4.13.1    Niveau: 2    Rolle: D/V
 Bekræft, at multi-cloud AI-implementeringer bruger cloud-agnostisk identitetsfederation (OIDC, SAML) med centraliseret politikstyring på tværs af udbydere.
 #4.13.2    Niveau: 2    Rolle: D/V
 Bekræft, at kryds-cloud dataoverførsel bruger ende-til-ende kryptering med kundeadministrerede nøgler og datalokalitetkontroller håndhævet i henhold til jurisdiktion.
 #4.13.3    Niveau: 2    Rolle: D/V
 Bekræft, at hybrid cloud AI-arbejdsbelastninger implementerer konsekvente sikkerhedspolitikker på tværs af on-premise og cloud-miljøer med enhedsovervågning og advarsler.
 #4.13.4    Niveau: 3    Rolle: V
 Bekræft, at forebyggelse af cloud-leverandørlåsning inkluderer portabel infrastruktur-som-kode, standardiserede API'er og datalekportfunktioner med værktøjer til formatkonvertering.
 #4.13.5    Niveau: 3    Rolle: V
 Sørg for, at multi-cloud omkostningsoptimering inkluderer sikkerhedskontroller, der forhindrer ressourceudbredelse samt uautoriserede tvær-cloud dataoverførselsgebyrer.

---

### C4.14 Infrastrukturautomatisering & GitOps-sikkerhed

Sikre automatiseringspipelines for infrastruktur og GitOps-arbejdsgange til AI-infrastrukturstyring.

 #4.14.1    Niveau: 2    Rolle: D/V
 Bekræft, at GitOps-repositorier kræver underskrevne commits med GPG-nøgler og branch-beskyttelsesregler, der forhindrer direkte push til hovedbrancher.
 #4.14.2    Niveau: 2    Rolle: D/V
 Bekræft, at infrastrukturautomatisering inkluderer driftregistrering med automatiske udbedrings- og rollback-funktioner, som udløses i henhold til organisatoriske responskrav for uautoriserede ændringer.
 #4.14.3    Niveau: 2    Rolle: D/V
 Bekræft, at automatiseret infrastrukturudrulning inkluderer validering af sikkerhedspolitikker med udrulningsblokering for ikke-overholdende konfigurationer.
 #4.14.4    Niveau: 2    Rolle: D/V
 Bekræft, at hemmeligheder til infrastrukturautomatisering håndteres gennem eksterne hemmelighedsoperatører (External Secrets Operator, Bank-Vaults) med automatisk rotation.
 #4.14.5    Niveau: 3    Rolle: V
 Bekræft, at selvhelende infrastruktur inkluderer korrelation af sikkerhedshændelser med automatiseret hændelsesrespons og arbejdsgange til underretning af interessenter.

---

### C4.15 Kvantesikret Infrastruktur Sikkerhed

Forbered AI-infrastrukturen på trusler fra kvantecomputing gennem post-kvantekryptografi og kvantesikre protokoller.

 #4.15.1    Niveau: 3    Rolle: D/V
 Bekræft, at AI-infrastrukturen implementerer NIST-godkendte post-kvante kryptografiske algoritmer (CRYSTALS-Kyber, CRYSTALS-Dilithium, SPHINCS+) til nøgleudveksling og digitale signaturer.
 #4.15.2    Niveau: 3    Rolle: D/V
 Bekræft, at kvante-nøglefordelingssystemer (QKD) implementeres til højsikkerheds-AI-kommunikation med kvantesikre nøglestyringsprotokoller.
 #4.15.3    Niveau: 3    Rolle: D/V
 Bekræft, at kryptografiske agilitetssystemer muliggør hurtig overgang til nye post-kvante algoritmer med automatiseret certifikat- og nøgleudskiftning.
 #4.15.4    Niveau: 3    Rolle: V
 Bekræft, at kvantetrusselsmodellering vurderer AI-infrastrukturs sårbarhed over for kvanteangreb med dokumenterede migrations-tidslinjer og risikovurderinger.
 #4.15.5    Niveau: 3    Rolle: D/V
 Verificer, at hybride klassiske-kvantemæssige kryptografiske systemer giver forsvar-i-dybden under kvanteovergangsperioden med ydelsesovervågning.

---

### C4.16 Fortrolig Computing & Sikkerhedsindelinger

Beskyt AI-arbejdsbelastninger og modelvægte ved hjælp af hardwarebaserede betroede udførelsesmiljøer og fortrolige beregningsteknologier.

 #4.16.1    Niveau: 3    Rolle: D/V
 Bekræft, at følsomme AI-modeller kører inden for Intel SGX-enklaver, AMD SEV-SNP eller ARM TrustZone med krypteret hukommelse og attestationsverifikation.
 #4.16.2    Niveau: 3    Rolle: D/V
 Bekræft, at fortrolige containere (Kata Containers, gVisor med fortrolig computing) isolerer AI-arbejdsmængder med hardwareunderstøttet hukommelseskryptering.
 #4.16.3    Niveau: 3    Rolle: D/V
 Bekræft, at fjernattestering validerer enclave-integritet, før AI-modeller indlæses, med kryptografisk bevis for et eksekveringsmiljøs ægthed.
 #4.16.4    Niveau: 3    Rolle: D/V
 Bekræft, at fortrolige AI-inferencetjenester forhindrer modelekstraktion gennem krypteret beregning med forseglede modelvægte og beskyttet udførelse.
 #4.16.5    Niveau: 3    Rolle: D/V
 Bekræft, at orkestrering af trusted execution environment styrer den sikre enclave-livscyklus med fjernattestation og krypterede kommunikationskanaler.
 #4.16.6    Niveau: 3    Rolle: D/V
 Bekræft, at sikker multi-part beregning (SMPC) muliggør samarbejdende AI-træning uden at afsløre individuelle datasæt eller modelparametre.

---

### C4.17 Zero-Knowledge Infrastruktur

Implementer nul-videns bevis systemer til privatlivsbeskyttende AI-verifikation og autentificering uden at afsløre følsomme oplysninger.

 #4.17.1    Niveau: 3    Rolle: D/V
 Bekræft, at zero-knowledge beviser (ZK-SNARKs, ZK-STARKs) verificerer AI-modelintegritet og træningsoprindelse uden at afsløre modelvægte eller træningsdata.
 #4.17.2    Niveau: 3    Rolle: D/V
 Bekræft, at ZK-baserede autentificeringssystemer muliggør privatlivsbevarende brugerbekræftelse for AI-tjenester uden at afsløre identitetsrelaterede oplysninger.
 #4.17.3    Niveau: 3    Rolle: D/V
 Bekræft, at private set intersection (PSI) protokoller muliggør sikker datamatchning for fødereret AI uden at eksponere individuelle datasæt.
 #4.17.4    Niveau: 3    Rolle: D/V
 Bekræft, at zero-knowledge maskinlæringssystemer (ZKML) muliggør verificerbare AI-afledninger med kryptografisk bevis for korrekt beregning.
 #4.17.5    Niveau: 3    Rolle: D/V
 Bekræft, at ZK-rollups leverer skalerbar, privatlivsbevarende AI-transaktionsbehandling med batchverifikation og reduceret beregningsmæssigt overhead.

---

### C4.18 Forebyggelse af sidekanalangreb

Beskyt AI-infrastruktur mod timing-, strøm-, elektromagnetiske og cache-baserede sidekanalangreb, der kan lække følsomme oplysninger.

 #4.18.1    Niveau: 3    Rolle: D/V
 Bekræft, at AI-inferens timing er normaliseret ved brug af algoritmer med konstant tid og udfyldning for at forhindre timing-baserede modeludtrækningsangreb.
 #4.18.2    Niveau: 3    Rolle: D/V
 Bekræft, at beskyttelse mod strøm-analyse inkluderer støjindsprøjtning, filtrering af strømforsyningslinjer og tilfældige udførelsesmønstre for AI-hardware.
 #4.18.3    Niveau: 3    Rolle: D/V
 Bekræft, at cache-baseret side-channel afbødning bruger cache-partitionering, randomisering og flush-instruktioner for at forhindre informationslækage.
 #4.18.4    Niveau: 3    Rolle: D/V
 Bekræft, at beskyttelse mod elektromagnetisk udsendelse omfatter afskærmning, signalfiltrering og tilfældig behandling for at forhindre TEMPEST-lignende angreb.
 #4.18.5    Niveau: 3    Rolle: D/V
 Bekræft, at mikroarkitekturens sidekanal-foranstaltninger inkluderer kontrol med spekulativ udførelse og obfuskering af hukommelsesadgangsmønstre.

---

### C4.19 Neuromorfisk & Specialiseret AI Hardware Sikkerhed

Sikre fremadstormende AI-hardwarearkitekturer, herunder neuromorfe chips, FPGA'er, tilpassede ASIC'er og optiske computersystemer.

 #4.19.1    Niveau: 3    Rolle: D/V
 Bekræft, at neuromorfe chip-sikkerhed inkluderer kryptering af spike-mønstre, beskyttelse af synaptiske vægte og hardwarebaseret validering af læringsregler.
 #4.19.2    Niveau: 3    Rolle: D/V
 Bekræft, at FPGA-baserede AI-acceleratorer implementerer bitstream-kryptering, anti-manipulationsmekanismer og sikker konfigurationsindlæsning med autentificerede opdateringer.
 #4.19.3    Niveau: 3    Rolle: D/V
 Bekræft, at brugerdefineret ASIC-sikkerhed inkluderer indbyggede sikkerhedsprocessorer, hardware root of trust og sikker nøglelagring med manipulationsdetektion.
 #4.19.4    Niveau: 3    Rolle: D/V
 Bekræft, at optiske computersystemer implementerer kvantesikret optisk kryptering, sikker fotonisk switching og beskyttet optisk signalbehandling.
 #4.19.5    Niveau: 3    Rolle: D/V
 Bekræft, at hybride analoge-digitale AI-chips inkluderer sikker analog beregning, beskyttet vægtlagring og autentificeret analog-til-digital konvertering.

---

### C4.20 Privatlivsbevarende beregningsinfrastruktur

Implementer infrastrukturelle kontroller for privatlivsbeskyttende beregning for at beskytte følsomme data under AI-behandling og analyse.

 #4.20.1    Niveau: 3    Rolle: D/V
 Bekræft, at homomorf krypteringsinfrastruktur muliggør krypteret beregning på følsomme AI-arbejdsbelastninger med kryptografisk integritetsverifikation og ydeevneovervågning.
 #4.20.2    Niveau: 3    Rolle: D/V
 Bekræft, at private information retrieval-systemer muliggør databaseforespørgsler uden at afsløre forespørgsmønstre med kryptografisk beskyttelse af adgangsmønstre.
 #4.20.3    Niveau: 3    Rolle: D/V
 Bekræft, at sikre multi-parti beregningsprotokoller muliggør privatlivsbevarende AI-inferens uden at afsløre individuelle input eller mellemliggende beregninger.
 #4.20.4    Niveau: 3    Rolle: D/V
 Bekræft, at privatlivsbevarende nøglehåndtering omfatter distribueret nøglegenerering, tærskelkryptografi og sikker nøglerotation med hardware-understøttet beskyttelse.
 #4.20.5    Niveau: 3    Rolle: D/V
 Bekræft, at ydeevnen for privatlivsbeskyttende beregninger er optimeret gennem batching, caching og hardwareacceleration, samtidig med at kryptografiske sikkerhedsgarantier opretholdes.

---

### C4.15 Agent Framework Cloud Integration Sikkerhed & Hybrid Implementering

Sikkerhedskontroller for sky-integrerede agentrammer med hybride lokale/sky-arkitekturer.

 #4.15.1    Niveau: 1    Rolle: D/V
 Bekræft, at cloud-lagringsintegration bruger ende-til-ende-kryptering med agentstyret nøglehåndtering.
 #4.15.2    Niveau: 2    Rolle: D/V
 Bekræft, at sikkerhedsgrænserne for hybridimplementering er klart definerede med krypterede kommunikationskanaler.
 #4.15.3    Niveau: 2    Rolle: D/V
 Bekræft, at adgang til cloud-ressourcer inkluderer zero-trust-verifikation med kontinuerlig autentificering.
 #4.15.4    Niveau: 3    Rolle: D/V
 Bekræft, at krav til datalagring overholdes ved kryptografisk attestering af lagringssteder.
 #4.15.5    Niveau: 3    Rolle: D/V
 Bekræft, at sikkerhedsvurderinger fra cloud-udbyderen inkluderer agent-specifik trusselsmodellering og risikovurdering.

---

### Referencer

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

## C5 Adgangskontrol og identitet for AI-komponenter og brugere

### Kontrolmål

Effektiv adgangskontrol for AI-systemer kræver robust identitetsstyring, kontekstbevidst autorisation og runtime-håndhævelse i overensstemmelse med zero-trust-principper. Disse kontroller sikrer, at mennesker, tjenester og autonome agenter kun interagerer med modeller, data og beregningsressourcer inden for eksplicit tildelte områder, med løbende verifikation og revisionsmuligheder.

---

### C5.1 Identitetsstyring og autentifikation

Etabler kryptografisk understøttede identiteter for alle enheder med multifaktorgodkendelse til privilegerede operationer.

 #5.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle menneskelige brugere og serviceprincipaler godkendes gennem en centraliseret virksomhedsidentitetsudbyder (IdP) ved brug af OIDC/SAML-protokoller med unikke identitets-til-token-tilknytninger (ingen delte konti eller legitimationsoplysninger).
 #5.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at højrisikooperationer (modelimplementering, vægtekspor, adgang til træningsdata, produktionskonfigurationsændringer) kræver multifaktorautentificering eller trin-op-autentificering med sessiongensvalidering.
 #5.1.3    Niveau: 2    Rolle: D
 Bekræft, at nye principper gennemgår identitetsverificering, der er i overensstemmelse med NIST 800-63-3 IAL-2 eller tilsvarende standarder, før de får adgang til produktionssystemet.
 #5.1.4    Niveau: 2    Rolle: V
 Bekræft, at adgangsgennemgange udføres kvartalsvis med automatisk detektion af inaktive konti, håndhævelse af adgangsoplysningerotation og arbejdsprocesser for de-provisionering.
 #5.1.5    Niveau: 3    Rolle: D/V
 Bekræft, at fødererede AI-agenter autentificerer via underskrevne JWT-påstande, der har en maksimal levetid på 24 timer og indeholder kryptografisk bevis for oprindelse.

---

### C5.2 Ressourceautorisation & mindst privilegium

Implementer detaljerede adgangskontroller for alle AI-ressourcer med eksplicitte tilladelsesmodeller og revisionsspor.

 #5.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle AI-ressourcer (datasæt, modeller, endpoints, vektorsamlinger, indlejringindekser, beregningsinstanser) håndhæver rollebaserede adgangskontroller med eksplicitte tilladelseslister og standardafvisningspolitikker.
 #5.2.2    Niveau: 1    Rolle: D/V
 Sørg for, at principperne om mindst mulige privilegier håndhæves som standard for servicekonti, startende med skrivebeskyttede tilladelser, og at der kræves dokumenteret forretningsmæssig begrundelse for skriveadgang.
 #5.2.3    Niveau: 1    Rolle: V
 Bekræft, at alle ændringer i adgangskontrol er knyttet til godkendte ændringsanmodninger og logget uforanderligt med tidsstempler, aktøridentiteter, ressourceregistreringer og tilladelsesdifferencer.
 #5.2.4    Niveau: 2    Rolle: D
 Bekræft, at data klassifikationsmærker (PII, PHI, eksportkontrolleret, proprietær) automatisk overføres til afledte ressourcer (embedding, prompt caches, modeloutput) med konsekvent håndhævelse af politik.
 #5.2.5    Niveau: 2    Rolle: D/V
 Bekræft, at forsøg på uautoriseret adgang og hændelser med eskalering af privilegier udløser realtidsalarmer med kontekstuel metadata til SIEM-systemer inden for 5 minutter.

---

### C5.3 Dynamisk politikvurdering

Implementer attributbaserede adgangskontrol (ABAC)-motorer til kontekstbevidste autorisationsbeslutninger med revisionsfunktioner.

 #5.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at autorisationsbeslutninger er eksternt placeret i en dedikeret politikmotor (OPA, Cedar eller tilsvarende), som er tilgængelig via autentificerede API'er med kryptografisk integritetsbeskyttelse.
 #5.3.2    Niveau: 1    Rolle: D/V
 Bekræft, at politikker evaluerer dynamiske attributter ved kørselstidspunkt, herunder brugerens sikkerhedsklarering, ressourcefølsomhedsklassifikation, anmodningskontekst, lejerisolation og tidsmæssige begrænsninger.
 #5.3.3    Niveau: 2    Rolle: D
 Bekræft, at politikdefinitioner er versionsstyrede, peer-reviewed og validerede gennem automatiseret test i CI/CD-pipelines inden produktionsimplementering.
 #5.3.4    Niveau: 2    Rolle: V
 Bekræft, at politikvurderingsresultater inkluderer strukturerede beslutningsbegrundelser og overføres til SIEM-systemer til korrelationsanalyse og overholdelsesrapportering.
 #5.3.5    Niveau: 3    Rolle: D/V
 Bekræft, at politikcachens time-to-live (TTL) værdier ikke overstiger 5 minutter for ressourcer med høj følsomhed og 1 time for standardressourcer med cache-ugyldiggørelsesfunktioner.

---

### C5.4 Sikkerhedshåndhævelse ved forespørgselstidspunktet

Implementer sikkerhedskontroller på databaseniveau med obligatorisk filtrering og politikker for række-niveau sikkerhed.

 #5.4.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle vektordatabaser og SQL-forespørgsler inkluderer obligatoriske sikkerhedsfiltre (lejer-ID, følsomhedsetiketter, brugerområde), som håndhæves på databasmotor-niveau og ikke i applikationskoden.
 #5.4.2    Niveau: 1    Rolle: D/V
 Bekræft, at politikker for rækkebaseret sikkerhed (RLS) og maskering på feltniveau er aktiveret med politikarv for alle vektordatabaser, søgeindekser og træningsdatasæt.
 #5.4.3    Niveau: 2    Rolle: D
 Bekræft, at mislykkede autorisationsvurderinger forhindrer "forvirrede stedfortræder-angreb" ved straks at afbryde forespørgsler og returnere eksplicitte autorisationsfejlkoder i stedet for at returnere tomme resultatmængder.
 #5.4.4    Niveau: 2    Rolle: V
 Bekræft, at politikvurderingsforsinkelse løbende overvåges med automatiserede advarsler for timeout-betingelser, der kan muliggøre omgåelse af autorisation.
 #5.4.5    Niveau: 3    Rolle: D/V
 Bekræft, at forespørgselsretry-mekanismer genvurderer autorisationspolitikker for at tage højde for dynamiske tilladelsesændringer inden for aktive brugersessioner.

---

### C5.5 Output-filtrering og datatabsforebyggelse

Implementer efterbehandlingskontroller for at forhindre uautoriseret dataeksponering i AI-genereret indhold.

 #5.5.1    Niveau: 1    Rolle: D/V
 Bekræft, at post-inferens filtreringsmekanismer scanner og slører uautoriserede PII, klassificerede oplysninger og proprietære data, før indhold leveres til anmodere.
 #5.5.2    Niveau: 1    Rolle: D/V
 Bekræft, at citater, henvisninger og kildeangivelser i modeloutput valideres i forhold til callerens rettigheder og fjernes, hvis uautoriseret adgang konstateres.
 #5.5.3    Niveau: 2    Rolle: D
 Bekræft, at outputformatrestriktioner (rensede PDF'er, metadata-fjernede billeder, godkendte filtyper) håndhæves baseret på brugerens tilladelsesniveauer og dataklassifikationer.
 #5.5.4    Niveau: 2    Rolle: V
 Bekræft, at redigeringsalgoritmer er deterministiske, versionskontrollerede og opretholder revisionslogfiler for at støtte overholdelsesundersøgelser og retsmedicinsk analyse.
 #5.5.5    Niveau: 3    Rolle: V
 Bekræft, at højrisiko-redaktionsevents genererer adaptive logfiler, der inkluderer kryptografiske hashes af det originale indhold til retsmedicinsk genfinding uden datalækage.

---

### C5.6 Multi-Tenant Isolation

Sørg for kryptografisk og logisk isolation mellem lejere i delt AI-infrastruktur.

 #5.6.1    Niveau: 1    Rolle: D/V
 Bekræft, at hukommelsesområder, indlejringslagre, cacheposter og midlertidige filer er navneområdesegregerede pr. lejer med sikker oprydning ved sletning af lejer eller afslutning af session.
 #5.6.2    Niveau: 1    Rolle: D/V
 Bekræft, at hver API-anmodning inkluderer en autentificeret lejeridentifikator, der er kryptografisk valideret i forhold til sessionskontekst og brugerrettigheder.
 #5.6.3    Niveau: 2    Rolle: D
 Bekræft, at netværkspolitikker implementerer standard-afvis-regler for kommunikation på tværs af lejere inden for servicemeshes og containerorkestreringsplatforme.
 #5.6.4    Niveau: 3    Rolle: D
 Bekræft, at krypteringsnøgler er unikke pr. lejer med kundestyret nøgle (CMK) understøttelse og kryptografisk isolation mellem lejerens datalagre.

---

### C5.7 Autonom Agentgodkendelse

Kontroller tilladelser for AI-agenter og autonome systemer gennem scoped capability tokens og kontinuerlig autorisation.

 #5.7.1    Niveau: 1    Rolle: D/V
 Bekræft, at autonome agenter modtager scoped kapabilitetstokener, der eksplicit opregner tilladte handlinger, tilgængelige ressourcer, tidsgrænser og driftsmæssige begrænsninger.
 #5.7.2    Niveau: 1    Rolle: D/V
 Bekræft, at højrisiko-funktioner (adgang til filsystemet, kodeeksekvering, eksterne API-kald, finansielle transaktioner) er deaktiveret som standard og kræver eksplicitte godkendelser for aktivering med forretningsmæssige begrundelser.
 #5.7.3    Niveau: 2    Rolle: D
 Bekræft, at kapabilitetstoken er bundet til brugersessioner, inkluderer kryptografisk integritetsbeskyttelse, og sikr, at de ikke kan gemmes eller genbruges i offline-scenarier.
 #5.7.4    Niveau: 2    Rolle: V
 Bekræft, at agent-initierede handlinger gennemgår sekundær autorisation via ABAC-politikmotoren med fuld kontekst evaluering og revisionslogføring.
 #5.7.5    Niveau: 3    Rolle: V
 Bekræft, at agentfejltilstande og undtagelseshåndtering inkluderer oplysnigner om kapabilitetens omfang for at understøtte hændelsesanalyse og retsmedicinsk undersøgelse.

---

### Referencer

#### Standarder & Rammeværk

NIST SP 800-63-3: Digital Identity Guidelines
Zero Trust Architecture – NIST SP 800-207
OWASP Application Security Verification Standard (AISVS)
​
#### Implementeringsvejledninger

Identity and Access Management in the AI Era: 2025 Guide – IDSA
Attribute-Based Access Control with OPA – Permify
How We Designed Cedar to Be Intuitive, Fast, and Safe – AWS
​
#### AI-specifik sikkerhed

Row Level Security in Vector DBs for RAG – Bluetuple.ai
Tenant Isolation in Multi-Tenant Systems – WorkOS
Handling AI Agent Permissions – Stytch
OWASP Top 10 for Large Language Model Applications

## C6 Forsyningskædesikkerhed for Modeller, Frameworks & Data

### Kontrolmål

AI-forsyningskædeangreb udnytter tredjepartsmodeller, -rammer eller -datasæt til at indlejre bagdøre, bias eller udnyttelig kode. Disse kontroller tilbyder ende-til-ende oprindelsesoplysninger, sårbarhedsstyring og overvågning for at beskytte hele modellens livscyklus.

---

### C6.1 Forhåndstrænet Model Vurdering & Oprindelse

Vurder og godkend tredjeparts modelers oprindelse, licenser og skjulte adfærd, før der foretages finjustering eller implementering.

 #6.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at hvert tredjeparts modelartefakt inkluderer en underskrevet oprindelsesregistrering, der identificerer kildearkivet og commit-hashen.
 #6.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at modeller bliver scannet for ondsindede lag eller Trojan-udløsere ved hjælp af automatiserede værktøjer før import.
 #6.1.3    Niveau: 2    Rolle: D
 Bekræft, at transfer-learning finjusterer og består adversarial evaluering for at opdage skjulte adfærd.
 #6.1.4    Niveau: 2    Rolle: V
 Bekræft, at modellicenser, eksportkontrolmærker og dataoprindelseserklæringer er registreret i en ML-BOM-post.
 #6.1.5    Niveau: 3    Rolle: D/V
 Bekræft, at højrisikomodeller (offentligt uploadede vægte, uverificerede skabere) forbliver i karantæne indtil menneskelig gennemgang og godkendelse.

---

### C6.2 Framework- og biblioteks-scanning

Skann løbende ML-rammeværk og biblioteker for CVE'er og ondsindet kode for at holde runtime-stakken sikker.

 #6.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at CI-pipelines kører afhængighedsscannere på AI-rammeværk og kritiske biblioteker.
 #6.2.2    Niveau: 1    Rolle: D/V
 Bekræft, at kritiske sårbarheder (CVSS ≥ 7.0) blokerer for promovering til produktionsbilleder.
 #6.2.3    Niveau: 2    Rolle: D
 Bekræft, at statisk kodeanalyse kører på forgrenede eller leverede ML-biblioteker.
 #6.2.4    Niveau: 2    Rolle: V
 Bekræft, at forslag til opgradering af framework inkluderer en sikkerhedsvurdering med reference til offentlige CVE-feeds.
 #6.2.5    Niveau: 3    Rolle: V
 Bekræft, at runtime-sensorer advarer ved uventede indlæsninger af dynamiske biblioteker, der afviger fra den signerede SBOM.

---

### C6.3 Fastlåsning og verifikation af afhængigheder

Fastlås hver afhængighed til uforanderlige digests og reproducer builds for at garantere identiske, manipulationsfrie artefakter.

 #6.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle pakkestyringsværktøjer håndhæver versionsfastlåsning via låsefiler.
 #6.3.2    Niveau: 1    Rolle: D/V
 Bekræft, at uforanderlige digest-værdier anvendes i stedet for foranderlige tags i containerhenvisninger.
 #6.3.3    Niveau: 2    Rolle: D
 Bekræft, at reproducible‑build kontroller sammenligner hashes på tværs af CI-kørsler for at sikre identiske output.
 #6.3.4    Niveau: 2    Rolle: V
 Bekræft, at build-attestationer opbevares i 18 måneder for revisionssporbarhed.
 #6.3.5    Niveau: 3    Rolle: D
 Bekræft, at udløbne afhængigheder udløser automatiserede PR'er for at opdatere eller forgrejne fastlåste versioner.

---

### C6.4 Håndhævelse af betroede kilder

Tillad kun download af artefakter fra kryptografisk verificerede, organisationsgodkendte kilder og bloker alt andet.

 #6.4.1    Niveau: 1    Rolle: D/V
 Bekræft, at modelvægte, datasæt og containere kun downloades fra godkendte domæner eller interne registre.
 #6.4.2    Niveau: 1    Rolle: D/V
 Bekræft, at Sigstore/Cosign-signaturer validerer udgiverens identitet, før artefakter caches lokalt.
 #6.4.3    Niveau: 2    Rolle: D
 Bekræft, at egress-proxyer blokerer uautoriserede download af artefakter for at håndhæve politikken om betroede kilder.
 #6.4.4    Niveau: 2    Rolle: V
 Bekræft, at repository tilladelseslister gennemgås kvartalsvist med dokumentation for forretningsmæssig begrundelse for hver post.
 #6.4.5    Niveau: 3    Rolle: V
 Bekræft, at politikovertrædelser udløser karantæne af artefakter og tilbagerulning af afhængige pipeline-kørsler.

---

### C6.5 Vurdering af risiko ved tredjepartsdatasæt

Evaluer eksterne datasæt for forgiftning, bias og juridisk overholdelse, og overvåg dem gennem hele deres livscyklus.

 #6.5.1    Niveau: 1    Rolle: D/V
 Bekræft, at eksterne datasæt gennemgår vurdering af forgiftningsrisiko (f.eks. datafingeraftryk, outlier-detektion).
 #6.5.2    Niveau: 1    Rolle: D
 Bekræft, at bias-målinger (demografisk paritet, lige mulighed) beregnes før godkendelse af datasættet.
 #6.5.3    Niveau: 2    Rolle: V
 Bekræft, at oprindelse og licensbetingelser for datasæt er registreret i ML‑BOM-poster.
 #6.5.4    Niveau: 2    Rolle: V
 Bekræft, at periodisk overvågning opdager drift eller korruption i hostede datasæt.
 #6.5.5    Niveau: 3    Rolle: D
 Bekræft, at forbudt indhold (ophavsret, personligt identificerbare oplysninger) fjernes via automatiseret rensning inden træning.

---

### C6.6 Overvågning af angreb på forsyningskæden

Opdag trusler mod forsyningskæden tidligt gennem CVE-feeds, audit-loganalyse og red-team-simulationer.

 #6.6.1    Niveau: 1    Rolle: V
 Bekræft, at CI/CD-revisionslogfiler strømmer til SIEM-detektioner for unormale pakkeudtræk eller manipulerede byggetrin.
 #6.6.2    Niveau: 2    Rolle: D
 Kontroller, at procedurer for hændelsesrespons inkluderer tilbageførselsprocedurer for kompromitterede modeller eller biblioteker.
 #6.6.3    Niveau: 3    Rolle: V
 Bekræft, at trusselsintelligensberigelse markerer ML-specifikke indikatorer (f.eks. modelforgiftning IoC’er) i alarmernes triage.

---

### C6.7 ML‑BOM for Model Artefakter

Generer og signer detaljerede ML-specifikke SBOM'er (ML-BOM'er), så downstream-forbrugere kan verificere komponentintegritet ved implementeringstidspunktet.

 #6.7.1    Niveau: 1    Rolle: D/V
 Bekræft, at hver modelartefakt udgiver en ML‑BOM, der angiver datasæt, vægte, hyperparametre og licenser.
 #6.7.2    Niveau: 1    Rolle: D/V
 Bekræft, at ML-BOM-generering og Cosign-signering er automatiseret i CI og påkrævet for sammenfletning.
 #6.7.3    Niveau: 2    Rolle: D
 Bekræft, at ML‑BOM komplethedstjek fejler byggeprocessen, hvis nogen komponentmetadata (hash, licens) mangler.
 #6.7.4    Niveau: 2    Rolle: V
 Bekræft, at downstream-forbrugere kan forespørge ML-BOM'er via API for at validere importerede modeller ved implementeringstidspunktet.
 #6.7.5    Niveau: 3    Rolle: V
 Bekræft, at ML-BOM'er er versionsstyrede og sammenlignet for at opdage uautoriserede ændringer.

---

### Referencer

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

## C7 Modeladfærd, outputkontrol og sikkerhedssikring

### Kontrolmål

Modeloutputs skal være strukturerede, pålidelige, sikre, forklarlige og kontinuerligt overvågede i produktion. Dette reducerer hallucinationer, privatlivslækager, skadeligt indhold og ukontrollerede handlinger, samtidig med at det øger brugerens tillid og overholdelse af regler.

---

### C7.1 Håndhævelse af outputformat

Strenge skemaer, begrænset dekodning og efterfølgende validering stopper forkert formateret eller ondsindet indhold, inden det spreder sig.

 #7.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at svarskemaer (f.eks. JSON Schema) er angivet i systemprompten, og at alle output automatisk valideres; ikke-overensstemmende output udløser reparation eller afvisning.
 #7.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at begrænset dekodning (stop tokens, regex, max-tokens) er aktiveret for at forhindre overflow eller prompt-injektions-sidokanaler.
 #7.1.3    Niveau: 2    Rolle: D/V
 Bekræft, at efterfølgende komponenter behandler output som utroværdige og validerer dem mod skemaer eller injektionssikre de-serialisatorer.
 #7.1.4    Niveau: 3    Rolle: V
 Bekræft, at fejlbehæftede output-hændelser logges, hastighedsbegrænses og vises i overvågningen.

---

### C7.2 Hallucinationsdetektion og afbødning

Usikkerhedsvurdering og tilbagefaldsstrategier begrænser fabrikerede svar.

 #7.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at token-niveau log-sandsynligheder, ensemble selvkonsistens eller finjusterede hallucinationsdetektorer tildeler en konfidensscore til hvert svar.
 #7.2.2    Niveau: 1    Rolle: D/V
 Bekræft, at svar under en konfigurerbar tillidsgrænse udløser fallback-workflows (f.eks. opslag-forstærket generering, sekundær model eller manuel gennemgang).
 #7.2.3    Niveau: 2    Rolle: D/V
 Bekræft, at hallucinationshændelser er tagget med årsagsmetadata og ført ind i post-mortem- og finjusterings-pipelines.
 #7.2.4    Niveau: 3    Rolle: D/V
 Bekræft, at tærskler og detektorer genkalibreres efter større opdateringer af model eller vidensbase.
 #7.2.5    Niveau: 3    Rolle: V
 Bekræft, at dashboardvisualiseringer registrerer hallucinationsrater.

---

### C7.3 Output-sikkerheds- og privatlivsfiltrering

Politikfiltre og red-team dækning beskytter brugere og fortrolige data.

 #7.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at før- og eftergenerationsklassificeringer blokerer had, chikane, selvskade, ekstremistisk og seksuelt eksplicit indhold i overensstemmelse med politikken.
 #7.3.2    Niveau: 1    Rolle: D/V
 Bekræft, at PII/PCI-detektion og automatisk redigering kører på hvert svar; overtrædelser udløser en privatlivsincident.
 #7.3.3    Niveau: 2    Rolle: D
 Bekræft, at fortrolighedsetiketter (f.eks. forretningshemmeligheder) videreføres på tværs af modaliteter for at forhindre lækage i tekst, billeder eller kode.
 #7.3.4    Niveau: 3    Rolle: D/V
 Bekræft, at forsøg på omgåelse af filter eller klassifikationer med høj risiko kræver sekundær godkendelse eller brugerens genautentificering.
 #7.3.5    Niveau: 3    Rolle: D/V
 Bekræft, at filtreringsterskler afspejler juridiske jurisdiktioner samt brugerens alder/rolle-kontekst.

---

### C7.4 Output- og handlingsbegrænsning

Rate-begrænsninger og godkendelsesporte forhindrer misbrug og overdreven autonomi.

 #7.4.1    Niveau: 1    Rolle: D
 Bekræft, at kvoter pr. bruger og pr. API-nøgle begrænser forespørgsler, tokens og omkostninger med eksponentiel tilbagefald ved 429-fejl.
 #7.4.2    Niveau: 1    Rolle: D/V
 Bekræft, at privilegerede handlinger (filskrivninger, kodeudførelse, netværkskald) kræver politikbaseret godkendelse eller menneskelig indblanding.
 #7.4.3    Niveau: 2    Rolle: D/V
 Bekræft, at tværmodal konsistenskontrol sikrer, at billeder, kode og tekst genereret til den samme forespørgsel ikke kan bruges til at smugle skadeligt indhold.
 #7.4.4    Niveau: 2    Rolle: D
 Bekræft, at agentdelegeringsdybde, rekursionsgrænser og tilladte værktøjslister er eksplicit konfigureret.
 #7.4.5    Niveau: 3    Rolle: V
 Verificer, at overtrædelse af grænser udsender strukturerede sikkerhedshændelser til SIEM-indtagning.

---

### C7.5 Output Forklarbarhed

Gennemsigtige signaler forbedrer brugerens tillid og intern fejlfinding.

 #7.5.1    Niveau: 2    Rolle: D/V
 Bekræft, at brugerorienterede konfidensscore eller korte resuméer af begrundelser vises, når risikovurderingen vurderer det som passende.
 #7.5.2    Niveau: 2    Rolle: D/V
 Bekræft, at genererede forklaringer undgår at afsløre følsomme systemprompter eller proprietære data.
 #7.5.3    Niveau: 3    Rolle: D
 Bekræft, at systemet indfanger token-niveau log-sandsynligheder eller opmærksomhedskort og gemmer dem til autoriseret inspektion.
 #7.5.4    Niveau: 3    Rolle: V
 Bekræft, at forklarbarhedsartefakter er versionsstyrede sammen med modeludgivelser for revisionssporbarhed.

---

### C7.6 Overvågningsintegration

Real-time observability lukker løkken mellem udvikling og produktion.

 #7.6.1    Niveau: 1    Rolle: D
 Bekræft, at målinger (skemabrud, hallucinationsrate, toksicitet, PII-lækager, latenstid, omkostninger) strømmer til en central overvågningsplatform.
 #7.6.2    Niveau: 1    Rolle: V
 Bekræft, at alarmsgrænser er defineret for hver sikkerhedsmåling, med vagteskalationsveje.
 #7.6.3    Niveau: 2    Rolle: V
 Bekræft, at dashboards korrelerer output-anomalier med model/version, feature-flag og upstream dataændringer.
 #7.6.4    Niveau: 2    Rolle: D/V
 Bekræft, at overvågningsdata fødes tilbage til retræning, finjustering eller regelopdateringer inden for en dokumenteret MLOps-arbejdsgang.
 #7.6.5    Niveau: 3    Rolle: V
 Sørg for, at overvågningspipelines er penetrationstestede og adgangskontrollerede for at undgå lækage af følsomme logfiler.

---

### 7.7 Generative Mediesikkerhedsforanstaltninger

Sørg for, at AI-systemer ikke genererer ulovligt, skadeligt eller uautoriseret medieindhold ved at håndhæve politikrestriktioner, outputvalidering og sporbarhed.

 #7.7.1    Niveau: 1    Rolle: D/V
 Bekræft, at systemprompt og brugerinstruktioner udtrykkeligt forbyder generering af ulovligt, skadeligt eller ikke-samtykkende deepfake-medie (f.eks. billede, video, lyd).
 #7.7.2    Niveau: 2    Rolle: D/V
 Bekræft, at prompts filtreres for forsøg på at generere efterligninger, seksuelt eksplicitte deepfakes eller medier, der viser rigtige personer uden samtykke.
 #7.7.3    Niveau: 2    Rolle: V
 Bekræft, at systemet bruger perceptuel hashing, vandmærke-detektion eller fingerprinting for at forhindre uautoriseret gengivelse af ophavsretligt beskyttet materiale.
 #7.7.4    Niveau: 3    Rolle: D/V
 Bekræft, at alt genereret medie er kryptografisk signeret, vandmærket eller indlejret med manipulationstæt oprindelsesmetadata for efterfølgende sporbarhed.
 #7.7.5    Niveau: 3    Rolle: V
 Bekræft, at forsøgs på omgåelse (f.eks. prompt-forvirring, slang, modstridende formuleringer) bliver opdaget, logget og hastighedsbegrænset; gentagen misbrug rapporteres til overvågningssystemer.

### Referencer

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

## C8 Hukommelse, Embeddings & Vektordatabase Sikkerhed

### Kontrolmål

Indlejringer og vektorlagre fungerer som det "aktive hukommelse" i moderne AI-systemer, der kontinuerligt modtager brugerleverede data og bringer dem tilbage i modelkontekster via Retrieval-Augmented Generation (RAG). Hvis denne hukommelse ikke styres, kan den lække personligt identificerbare oplysninger (PII), krænke samtykke eller vendes om for at genskabe den oprindelige tekst. Formålet med denne kontrolgruppe er at styrke hukommelsespipeline og vektordatabaser, så adgangen er mindst mulig, indlejringer er privatlivsbeskyttende, lagrede vektorer udløber eller kan tilbagekaldes efter behov, og at hukommelse pr. bruger aldrig forurener en anden brugers prompts eller resultater.

---

### C8.1 Adgangskontrol på hukommelse og RAG-indekser

Håndhæv detaljerede adgangskontroller på hver enkelt vektorsamling.

 #8.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at adgangskontrolregler på række-/navneområdeniveau begrænser indsættelses-, slette- og forespørgselsoperationer pr. lejer, samling eller dokumentmærke.
 #8.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at API-nøgler eller JWT'er indeholder scoped claims (f.eks. samlings-ID'er, handlingsverber) og roteres mindst kvartalsvis.
 #8.1.3    Niveau: 2    Rolle: D/V
 Bekræft, at forsøg på privilegieeskalering (f.eks. forespørgsler om ligheder på tværs af namespaces) opdages og logges i et SIEM inden for 5 minutter.
 #8.1.4    Niveau: 2    Rolle: D/V
 Bekræft, at vector DB logger revisionsspor for emne-identifikator, operation, vector ID/namespace, lighedstærskel og resultattælling.
 #8.1.5    Niveau: 3    Rolle: V
 Sørg for, at adgangsbeslutninger testes for omgåelsesfejl, hver gang motorer opgraderes eller regler for index-sharding ændres.

---

### C8.2 Integreringssikkerhed og validering

Forhåndsscreen tekst for PII, slør eller pseudonymiser før vektoriserering, og efterbehandl eventuelt indlejringerne for at fjerne resterende signaler.

 #8.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at PII og regulerede data opdages via automatiserede klassifikatorer og maskeres, tokeniseres eller fjernes før embedding.
 #8.2.2    Niveau: 1    Rolle: D
 Verificer, at embeddingspipelines afviser eller isolerer input, der indeholder eksekverbar kode eller ikke-UTF-8 artefakter, som kunne forurene indekset.
 #8.2.3    Niveau: 2    Rolle: D/V
 Bekræft, at lokal eller metrisk differential-privacy sanitering anvendes på sætningsindlejringer, hvis afstand til enhver kendt PII-token falder under en konfigurerbar tærskel.
 #8.2.4    Niveau: 2    Rolle: V
 Bekræft, at effektiviteten af sanitering (f.eks. tilbagekaldelse af PII-redigering, semantisk afvigelse) valideres mindst to gange årligt mod referencekorpusser.
 #8.2.5    Niveau: 3    Rolle: D/V
 Bekræft, at saniteringskonfigurationer er versionskontrollerede, og at ændringer gennemgår kollegial gennemgang.

---

### C8.3 Hukommelsesudløb, Tilbagekaldelse og Sletning

GDPR "ret til at blive glemt" og lignende love kræver rettidig sletning; derfor skal vektorlagre understøtte TTL'er, hårde sletninger og tomb-stoning, så tilbagekaldte vektorer ikke kan gendannes eller reindekseres.

 #8.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at hver vektor- og metadataregistrering har en TTL eller en eksplicit opbevaringsmærkat, som overholdes af automatiserede oprydningsjob.
 #8.3.2    Niveau: 1    Rolle: D/V
 Bekræft, at brugerinitierede sletningsanmodninger fjerner vektorer, metadata, cachekopier og afledte indekser inden for 30 dage.
 #8.3.3    Niveau: 2    Rolle: D
 Bekræft, at logiske sletninger efterfølges af kryptografisk sletning af lagringsblokke, hvis hardwaren understøtter det, eller ved destruktion af nøgler i nøglevaulten.
 #8.3.4    Niveau: 3    Rolle: D/V
 Bekræft, at udløbne vektorer udelukkes fra nærmeste-nabo-søgeresultater inden for < 500 ms efter udløb.

---

### C8.4 Forhindre embedding-inversion og lækage

Nylige forsvar—støj-superposition, projektnetværk, privatlivs-neuronforstyrrelse og kryptering på applikationslaget—kan reducere token-niveau inversion satser til under 5%.

 #8.4.1    Niveau: 1    Rolle: V
 Sørg for, at der findes en formel trusselsmodel, der dækker inversion, medlemskabs- og attributinferenzangreb, og at den gennemgås årligt.
 #8.4.2    Niveau: 2    Rolle: D/V
 Bekræft, at applikationslagskryptering eller søgbar kryptering beskytter vektorer mod direkte læsning af infrastrukturområdets administratorer eller cloud-personale.
 #8.4.3    Niveau: 3    Rolle: V
 Bekræft, at forsvarsparametrene (ε for DP, støj σ, projektionens rang k) balancerer privatliv ≥ 99 % tokenbeskyttelse og nytte ≤ 3 % præcisionstab.
 #8.4.4    Niveau: 3    Rolle: D/V
 Sørg for, at målinger for inversion-resiliens er en del af frigivelsesporte for modelopdateringer, med definerede regressionsbudgetter.

---

### C8.5 Omfangshåndhævelse for brugerspecifik hukommelse

Lækage på tværs af lejere forbliver en af de største risici ved RAG: Forkert filtrerede lighedsspørgsmål kan vise en anden kundes private dokumenter.

 #8.5.1    Niveau: 1    Rolle: D/V
 Bekræft, at hver forespørgsel til hentning efterfiltreres af lejer-/bruger-ID, før den sendes til LLM-prompten.
 #8.5.2    Niveau: 1    Rolle: D
 Bekræft, at samlingsnavne eller navngivne ID'er saltes pr. bruger eller lejer, så vektorer ikke kan kollidere på tværs af scopes.
 #8.5.3    Niveau: 2    Rolle: D/V
 Bekræft, at lighedsresultater over en konfigurerbar afstandstærskel, men uden for kalders rækkevidde, bliver afvist og udløser sikkerhedsadvarsler.
 #8.5.4    Niveau: 2    Rolle: V
 Bekræft, at multi-tenant stresstest simulerer modstridende forespørgsler, der forsøger at hente dokumenter uden for omfanget, og demonstrerer nul lækage.
 #8.5.5    Niveau: 3    Rolle: D/V
 Bekræft, at krypteringsnøgler er adskilt pr. lejer, for at sikre kryptografisk isolation, selvom fysisk lagring deles.

---

### C8.6 Avanceret Hukommelsessystem Sikkerhed

Sikkerhedskontroller for sofistikerede hukommelsesarkitekturer, herunder episodisk, semantisk og arbejdshukommelse med specifikke isolations- og valideringskrav.

 #8.6.1    Niveau: 1    Rolle: D/V
 Bekræft, at forskellige hukommelsestyper (episodisk, semantisk, arbejdshukommelse) har isolerede sikkerhedskontekster med rollebaserede adgangskontroller, separate krypteringsnøgler og dokumenterede adgangsmønstre for hver hukommelsestype.
 #8.6.2    Niveau: 2    Rolle: D/V
 Bekræft, at hukommelseskonsolideringsprocesser inkluderer sikkerhedsgodkendelse for at forhindre indsprøjtning af ondsindede minder gennem indholdsrensning, kildeverifikation og integritetskontroller før lagring.
 #8.6.3    Niveau: 2    Rolle: D/V
 Bekræft, at forespørgsler til hukommelsesudtræk valideres og renses for at forhindre udtrækning af uautoriseret information gennem analyse af forespørgselsmønstre, håndhævelse af adgangskontrol og filtrering af resultater.
 #8.6.4    Niveau: 3    Rolle: D/V
 Bekræft, at hukommelsesglemmemekanismer sikkert sletter følsomme oplysninger med kryptografiske slettegarantier ved hjælp af nøgle-sletning, flergangsover-skrivning eller hardware-baseret sikker sletning med verifikationscertifikater.
 #8.6.5    Niveau: 3    Rolle: D/V
 Bekræft, at hukommelsessystemets integritet kontinuerligt overvåges for uautoriserede ændringer eller korruption gennem checksums, revisionslogfiler og automatiske advarsler, når hukommelsesindhold ændres uden for normale operationer.

---

### Referencer

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

## 9 Autonom orkestrering og agentisk handlingssikkerhed

### Kontrolmål

Sørg for, at autonome eller multi-agent AI-systemer kun kan udføre handlinger, der er eksplicit tiltænkt, autentificeret, reviderbare og inden for afgrænsede omkostnings- og risikogrenser. Dette beskytter mod trusler såsom kompromittering af autonome systemer, misbrug af værktøjer, agentloop-detektion, kapring af kommunikation, identitetsspoofing, sværmmanipulation og hensigtsmanipulation.

---

### 9.1 Agentopgaveplanlægning og rekursionsbudgetter

Begræns rekursive planer og kræv menneskelige kontrolpunkter for privilegerede handlinger.

 #9.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at maksimal rekursionsdybde, bredde, vægurstid, tokens og monetære omkostninger pr. agentudførelse er centralt konfigureret og versionsstyret.
 #9.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at privilegerede eller irreversible handlinger (f.eks. kodeindsendelser, finansielle overførsler) kræver eksplicit menneskelig godkendelse via en auditerbar kanal før udførelse.
 #9.1.3    Niveau: 2    Rolle: D
 Bekræft, at realtidsressourcemonitorer udløser afbrydelse via kredsløbsafbryder, når nogen budgetgrænse overskrides, og stopper yderligere opgaveudvidelse.
 #9.1.4    Niveau: 2    Rolle: D/V
 Bekræft, at circuit-breaker-hændelser logges med agent-ID, udløsende betingelse og optaget planstatus til retsmedicinsk gennemgang.
 #9.1.5    Niveau: 3    Rolle: V
 Bekræft, at sikkerhedstests dækker budget-udtømnings- og løbe-amok-plan-scenarier, og sikrer sikker standsning uden datatab.
 #9.1.6    Niveau: 3    Rolle: D
 Bekræft, at budgetpolitikker er udtrykt som policy-som-kode og håndhæves i CI/CD for at forhindre konfigurationsdrift.

---

### 9.2 Værktøjsplugin Sandboxing

Isolér værktøjsinteraktioner for at forhindre uautoriseret systemadgang eller kodeeksekvering.

 #9.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at hvert værktøj/plugin kører inden for et OS-, container- eller WASM-niveau sandbox med mindst-privilegier for filsystem-, netværks- og systemkaldspolitikker.
 #9.2.2    Niveau: 1    Rolle: D/V
 Bekræft, at begrænsninger for sandbox-ressourcer (CPU, hukommelse, disk, netværksudgående trafik) og udførelsestidsgrænser håndhæves og logges.
 #9.2.3    Niveau: 2    Rolle: D/V
 Bekræft, at værktøjsbinærer eller beskrivelser er digitalt signerede; signaturer valideres før indlæsning.
 #9.2.4    Niveau: 2    Rolle: V
 Bekræft, at sandbox-telemetri strømmer til en SIEM; afvigelser (f.eks. forsøg på udgående forbindelser) udløser alarmer.
 #9.2.5    Niveau: 3    Rolle: V
 Bekræft, at højrisko-plugins gennemgår sikkerhedsvurdering og penetrationstest, inden de tages i brug i produktion.
 #9.2.6    Niveau: 3    Rolle: D/V
 Bekræft, at forsøg på at undslippe sandbox automatisk bliver blokeret, og at den overtrædende plugin sættes i karantæne, indtil efterforskning er afsluttet.

---

### 9.3 Autonom løkke og omkostningsbegrænsning

Registrer og stop ukontrolleret agent-til-agent rekursion og omkostningseksplosioner.

 #9.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at opkald mellem agenter inkluderer en hop-grænse eller TTL, som runtime-miljøet tæller ned og håndhæver.
 #9.3.2    Niveau: 2    Rolle: D
 Bekræft, at agenter opretholder et unikt invocation-graph ID for at opdage selv-påberåbelse eller cykliske mønstre.
 #9.3.3    Niveau: 2    Rolle: D/V
 Bekræft, at akkumulerede compute-unit og forbrugs-tællere spores pr. anmodningskæde; overskridelse af grænsen afbryder kæden.
 #9.3.4    Niveau: 3    Rolle: V
 Bekræft, at formel analyse eller modelkontrol demonstrerer fraværet af ubegrænset rekursion i agentprotokoller.
 #9.3.5    Niveau: 3    Rolle: D
 Bekræft, at loop-afbruds-begivenheder genererer advarsler og leverer målinger til løbende forbedring.

---

### 9.4 Beskyttelse mod misbrug på protokolniveau

Sikre kommunikationskanaler mellem agenter og eksterne systemer for at forhindre kapring eller manipulation.

 #9.4.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle agent-til-værktøj og agent-til-agent beskeder er autentificerede (f.eks. gensidig TLS eller JWT) og end-to-end krypterede.
 #9.4.2    Niveau: 1    Rolle: D
 Sørg for, at skemaer er strengt validerede; ukendte felter eller fejlbehæftede meddelelser afvises.
 #9.4.3    Niveau: 2    Rolle: D/V
 Bekræft, at integritetskontroller (MAC'er eller digitale signaturer) dækker hele meddelelsens nyttelast, inklusive værktøjsparametre.
 #9.4.4    Niveau: 2    Rolle: D
 Bekræft, at gengivelsesbeskyttelse (noncer eller tidsstempelvinduer) håndhæves på protokolniveau.
 #9.4.5    Niveau: 3    Rolle: V
 Bekræft, at protokolimplementeringer gennemgår fuzzing og statisk analyse for injektions- eller deserialiseringsfejl.

---

### 9.5 Agentidentitet og Manipulationssikkerhed

Sørg for, at handlinger kan tilskrives, og at ændringer kan opdages.

 #9.5.1    Niveau: 1    Rolle: D/V
 Bekræft, at hver agentinstans har en unik kryptografisk identitet (nøglepar eller hardware-forankret legitimationsoplysninger).
 #9.5.2    Niveau: 2    Rolle: D/V
 Bekræft, at alle agenthandlinger er underskrevet og tidsstemplet; logfiler inkluderer signaturen for ikke-afvisning.
 #9.5.3    Niveau: 2    Rolle: V
 Bekræft, at manipulationssikre logs gemmes i et kun-tilføj eller skriv-en-gang medie.
 #9.5.4    Niveau: 3    Rolle: D
 Bekræft, at identitetsnøgler roterer efter en defineret tidsplan og ved tegn på kompromittering.
 #9.5.5    Niveau: 3    Rolle: D/V
 Bekræft, at forsøg på spoofing eller nøglekonflikt straks udløser karantæne af den berørte agent.

---

### 9.6 Multi-Agent Swarm Risikoreduktion

Afbød kollektive adfærdssikkerhedsrisici gennem isolation og formel sikkerhedsmodellering.

 #9.6.1    Niveau: 1    Rolle: D/V
 Bekræft, at agenter, der opererer i forskellige sikkerhedsdomaener, kører i isolerede runtime-sandboxe eller netværkssegmenter.
 #9.6.2    Niveau: 3    Rolle: V
 Bekræft, at sværmadfærd modelleres og formelt verificeres for livlighed og sikkerhed inden implementering.
 #9.6.3    Niveau: 3    Rolle: D
 Bekræft, at runtime-monitors opdager fremspirende usikre mønstre (f.eks. oscillationer, deadlocks) og igangsætter korrigerende handlinger.

---

### 9.7 Bruger- og værktøjsautentificering / -autorisation

Implementer robuste adgangskontroller for hver agent-udløste handling.

 #9.7.1    Niveau: 1    Rolle: D/V
 Bekræft, at agenter godkender som førsteklasses principper til downstream-systemer og aldrig genbruger slutbrugerens legitimationsoplysninger.
 #9.7.2    Niveau: 2    Rolle: D
 Verificer, at detaljerede autorisationspolitikker begrænser, hvilke værktøjer en agent må anvende, og hvilke parametre den må angive.
 #9.7.3    Niveau: 2    Rolle: V
 Bekræft, at privilegietjek genvurderes ved hvert opkald (kontinuerlig autorisation), ikke kun ved sessionens start.
 #9.7.4    Niveau: 3    Rolle: D
 Bekræft, at delegerede privilegier udløber automatisk og kræver gensamtykke efter timeout eller ændring i omfang.

---

### 9.8 Agent-til-Agent Kommunikationssikkerhed

Krypter og beskytt integriteten af alle beskeder mellem agenter for at forhindre aflytning og manipulation.

 #9.8.1    Niveau: 1    Rolle: D/V
 Bekræft, at gensidig autentificering og perfekt-fremad-sikker kryptering (f.eks. TLS 1.3) er obligatorisk for agentkanaler.
 #9.8.2    Niveau: 1    Rolle: D
 Bekræft, at meddelelsens integritet og oprindelse valideres, før den behandles; fejl udløser advarsler og afvisning af meddelelsen.
 #9.8.3    Niveau: 2    Rolle: D/V
 Bekræft, at kommunikationsmetadata (tidsstempler, sekvensnumre) bliver logget for at understøtte retsmedicinsk rekonstruktion.
 #9.8.4    Niveau: 3    Rolle: V
 Bekræft, at formel verifikation eller modelkontrol bekræfter, at protokoltilstandsmaskiner ikke kan bringes ind i usikre tilstande.

---

### 9.9 Intentverifikation og håndhævelse af begrænsninger

Bekræft, at agentens handlinger stemmer overens med brugerens angivne intention og systemets begrænsninger.

 #9.9.1    Niveau: 1    Rolle: D
 Bekræft, at constraint-løsere før udførelse kontrollerer foreslåede handlinger mod hardkodede sikkerheds- og politikregler.
 #9.9.2    Niveau: 2    Rolle: D/V
 Bekræft, at handlinger med høj påvirkning (finansielle, destruktive, privatlivsfølsomme) kræver eksplicit hensigtsbekræftelse fra den igangsættende bruger.
 #9.9.3    Niveau: 2    Rolle: V
 Bekræft, at post-betingelsestjek validerer, at afsluttede handlinger opnåede tilsigtede effekter uden bivirkninger; uoverensstemmelser udløser tilbageførsel.
 #9.9.4    Niveau: 3    Rolle: V
 Bekræft, at formelle metoder (f.eks. modelkontrol, teorembevis) eller egenskabsbaserede tests demonstrerer, at agentplaner opfylder alle erklærede begrænsninger.
 #9.9.5    Niveau: 3    Rolle: D
 Sørg for, at hændelser med intention-mismatch eller overtrædelse af begrænsninger bidrager til kontinuerlige forbedringscyklusser og deling af trusselsinformation.

---

### 9.10 Agentbegrænsningsstrategi Sikkerhed

Sikker udvælgelse og udførelse af forskellige ræsonneringsstrategier herunder ReAct, Chain-of-Thought og Tree-of-Thoughts tilgange.

 #9.10.1    Niveau: 1    Rolle: D/V
 Bekræft, at valg af ræsonneringsstrategi bruger deterministiske kriterier (inputkompleksitet, opgavetype, sikkerhedskontekst), og at identiske input producerer identiske strategivalg inden for samme sikkerhedskontekst.
 #9.10.2    Niveau: 1    Rolle: D/V
 Bekræft, at hver ræsonneringsstrategi (ReAct, Chain-of-Thought, Tree-of-Thoughts) har dedikeret inputvalidering, outputsanitering og eksekveringstidbegrænsninger, der er specifikke for dens kognitive tilgang.
 #9.10.3    Niveau: 2    Rolle: D/V
 Bekræft, at overgange i ræsonneringsstrategi logges med fuldstændig kontekst, herunder inputkarakteristika, værdier for udvælgelseskriterier og eksekveringsmetadata til rekonstruktion af revisionsspor.
 #9.10.4    Niveau: 2    Rolle: D/V
 Bekræft, at Tree-of-Thoughts-argumentation inkluderer grenbeskæringsmekanismer, der afslutter udforskning, når politikovertrædelser, ressourcebegrænsninger eller sikkerhedsgrænser opdages.
 #9.10.5    Niveau: 2    Rolle: D/V
 Bekræft, at ReAct (Reason-Act-Observe)-cyklusser inkluderer valideringskontrolpunkter i hver fase: verifikation af ræsonneringstrin, handlingstilladelse og observationrensning, før der fortsættes.
 #9.10.6    Niveau: 3    Rolle: D/V
 Bekræft, at præstationsmål for ræsonneringsstrategi (eksekveringstid, ressourceforbrug, outputkvalitet) overvåges med automatiserede advarsler, når målene afviger ud over konfigurerede grænseværdier.
 #9.10.7    Niveau: 3    Rolle: D/V
 Verificer, at hybride ræsonneringstilgange, der kombinerer flere strategier, opretholder inputvalidering og outputbegrænsninger for alle indgående strategier uden at omgå nogen sikkerhedskontroller.
 #9.10.8    Niveau: 3    Rolle: D/V
 Bekræft, at sikkerhedstest af ræsonneringsstrategi inkluderer fuzzing med fejlbehæftede input, fjendtlige prompts designet til at tvinge strategiændring samt test af grænsetilstande for hver kognitiv tilgang.

---

### 9.11 Agentens livscyklusstatusstyring og sikkerhed

Sikker agentinitialisering, tilstandsovergange og afslutning med kryptografiske revisionsspor og definerede genopretningsprocedurer.

 #9.11.1    Niveau: 1    Rolle: D/V
 Bekræft, at agentinitialisering inkluderer etablering af kryptografisk identitet med hardware-understøttede legitimationsoplysninger og uforanderlige opstartsrevisionslogfiler, der indeholder agent-ID, tidsstempel, konfigurationshash og initialiseringsparametre.
 #9.11.2    Niveau: 2    Rolle: D/V
 Bekræft, at agentens tilstandsændringer er kryptografisk underskrevet, tidsstemplet og logget med fuldstændig kontekst, herunder udløsende begivenheder, tidligere tilstandshash, ny tilstandshash og udførte sikkerhedsvalideringer.
 #9.11.3    Niveau: 2    Rolle: D/V
 Bekræft, at agentens nedlukningsprocedurer inkluderer sikker hukommelsesrensning ved hjælp af kryptografisk sletning eller multi-gennemskrivning, tilbagekaldelse af legitimationsoplysninger med underretning til certifikatmyndigheden, samt generering af manipulationssikre afslutningscertifikater.
 #9.11.4    Niveau: 3    Rolle: D/V
 Bekræft, at agentens genopretningsmekanismer validerer tilstandsintegritet ved hjælp af kryptografiske kontrolsummer (mindst SHA-256) og ruller tilbage til kendte gode tilstande, når korruption opdages, med automatiserede alarmer og krav om manuel godkendelse.
 #9.11.5    Niveau: 3    Rolle: D/V
 Bekræft, at agentens vedholdenhedsmekanismer krypterer følsomme tilstandsdata med per-agent AES-256-nøgler og implementerer sikker nøgleudskiftning efter konfigurerbare tidsplaner (maksimalt 90 dage) med nul nedetid ved implementering.

---

### 9.12 Værktøjsintegrationssikkerhedsramme

Sikkerhedskontroller for dynamisk værktøjsindlæsning, udførelse og resultatvalidering med definerede risikovurderings- og godkendelsesprocesser.

 #9.12.1    Niveau: 1    Rolle: D/V
 Bekræft, at værktøjsbeskrivelser indeholder sikkerhedsmetadata, der specificerer nødvendige privilegier (læs/skrive/udfør), risikoniveauer (lav/mellem/høj), ressourcebegrænsninger (CPU, hukommelse, netværk) og valideringskrav dokumenteret i værktøjsmanifest.
 #9.12.2    Niveau: 1    Rolle: D/V
 Bekræft, at værktøjets udførelsesresultater valideres i forhold til forventede skemaer (JSON Schema, XML Schema) og sikkerhedspolitikker (outputsanitering, dataklassificering) før integration med timeout-grænser og fejlbehandlingsprocedurer.
 #9.12.3    Niveau: 2    Rolle: D/V
 Bekræft, at værktøjsinteraktionslogfiler inkluderer detaljeret sikkerhedskontekst, herunder brug af privilegier, dataadgangsmønstre, eksekveringstid, ressourceforbrug og returkoder med struktureret logning til SIEM-integration.
 #9.12.4    Niveau: 2    Rolle: D/V
 Bekræft, at dynamiske værktøjsindlæsningsmekanismer validerer digitale signaturer ved hjælp af PKI-infrastruktur og implementerer sikre indlæsningsprotokoller med sandbox-isolation og tilladelsesverifikation før eksekvering.
 #9.12.5    Niveau: 3    Rolle: D/V
 Bekræft, at værktøjssikkerhedsvurderinger automatisk udløses for nye versioner med obligatoriske godkendelsesporte, herunder statisk analyse, dynamisk test og sikkerhedsteamets gennemgang med dokumenterede godkendelseskriterier og SLA-krav.

---

#### Referencer

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

## 10 Modstandsdygtighed over for angreb og privatlivsbeskyttelse

### Kontrolmål

Sørg for, at AI-modeller forbliver pålidelige, privatlivsbevarende og modstandsdygtige over for misbrug, når de udsættes for undvigelses-, inferens-, udtræknings- eller forgiftningsangreb.

---

### 10.1 Modeljustering og sikkerhed

Beskyt mod skadelige eller politikovertrædende output.

 #10.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at en testsuite for alignment (red-team prompts, jailbreak probes, forbudt indhold) er versionskontrolleret og køres ved hver modeludgivelse.
 #10.1.2    Niveau: 1    Rolle: D
 Bekræft, at afvisnings- og sikker-afslutnings-sikkerhedsforanstaltninger håndhæves.
 #10.1.3    Niveau: 2    Rolle: D/V
 Bekræft, at en automatiseret evaluator måler graden af skadeligt indhold og markerer regressionsændringer, der overstiger en fastsat tærskel.
 #10.1.4    Niveau: 2    Rolle: D
 Bekræft, at counter-jailbreak-træning er dokumenteret og reproducerbar.
 #10.1.5    Niveau: 3    Rolle: V
 Bekræft, at formelle beviser for overholdelse af politikker eller certificeret overvågning dækker kritiske domæner.

---

### 10.2 Modstandsdygtighed over for modstridende eksempler

Øg modstandsdygtigheden over for manipulerede input. Robust modstandertræning og benchmarkscoring er den nuværende bedste praksis.

 #10.2.1    Niveau: 1    Rolle: D
 Bekræft, at projektrepositories inkluderer adversarial-træningskonfigurationer med reproducerbare frø.
 #10.2.2    Niveau: 2    Rolle: D/V
 Bekræft, at detektionssystemet for fjendtlige eksempler udløser blokeringsadvarsler i produktionspipelines.
 #10.2.4    Niveau: 3    Rolle: V
 Bekræft, at certificerede robusthedsbeviser eller interval-grænsecertifikater dækker mindst de mest kritiske klasser.
 #10.2.5    Niveau: 3    Rolle: V
 Bekræft, at regressions tests bruger adaptive angreb for at bekræfte, at der ikke er noget målbar tab af robusthed.

---

### 10.3 Medlemskabsinferenceafværgelse

Begræns muligheden for at afgøre, om en post var i træningsdataene. Differential privacy og maskering af konfidensscore forbliver de mest effektive kendte forsvar.

 #10.3.1    Niveau: 1    Rolle: D
 Bekræft, at entropiregulering pr. forespørgsel eller temperaturskalering reducerer overmodige forudsigelser.
 #10.3.2    Niveau: 2    Rolle: D
 Bekræft, at træning anvender ε-begrænset differentialt privat optimering for følsomme datasæt.
 #10.3.3    Niveau: 2    Rolle: V
 Bekræft, at angrebssimuleringer (shadow-model eller black-box) viser angrebs AUC ≤ 0,60 på hold-out data.

---

### 10.4 Modstand mod modelinversion

Forhindre rekonstruktion af private attributter. Nylige undersøgelser understreger output-trunkering og DP-garantier som praktiske forsvar.

 #10.4.1    Niveau: 1    Rolle: D
 Bekræft, at følsomme attributter aldrig udskrives direkte; hvor det er nødvendigt, brug segmenter eller envejsomdannelser.
 #10.4.2    Niveau: 1    Rolle: D/V
 Bekræft, at forespørgselsrater begrænser gentagne adaptive forespørgsler fra samme principal.
 #10.4.3    Niveau: 2    Rolle: D
 Bekræft, at modellen er trænet med privatlivsbevarende støj.

---

### 10.5 Model-Uddragelsesforsvar

Opdag og forhindre uautoriseret kloning. Vandmærkning og analyse af forespørgselsmønstre anbefales.

 #10.5.1    Niveau: 1    Rolle: D
 Bekræft, at inferens-gateways håndhæver globale og per-API-nøgle ratebegrænsninger, som er tilpasset modellens memoriseringstærskel.
 #10.5.2    Niveau: 2    Rolle: D/V
 Bekræft, at statistikkerne for forespørgselsentropi og input-flertal fodrer en automatiseret ekstraktionsdetektor.
 #10.5.3    Niveau: 2    Rolle: V
 Bekræft, at skrøbelige eller probabilistiske vandmærker kan bevises med p < 0,01 i ≤ 1 000 forespørgsler mod en mistænkt klon.
 #10.5.4    Niveau: 3    Rolle: D
 Bekræft, at watermark-nøgler og trigger-sæt opbevares i en hardware-sikkerhedsmodul og roteres årligt.
 #10.5.5    Niveau: 3    Rolle: V
 Bekræft, at extraction-alert-hændelser inkluderer de problematiske forespørgsler og er integreret med incident-response playbooks.

---

### 10.6 Detektion af forgiftede data ved inferenstidspunktet

Identificer og neutraliser bagdørs- eller forgiftede input.

 #10.6.1    Niveau: 1    Rolle: D
 Bekræft, at inputs passerer gennem en anomali-detektor (f.eks. STRIP, konsistensscoring) før modelinference.
 #10.6.2    Niveau: 1    Rolle: V
 Bekræft, at detektortærskler er justeret på rene/forurenede valideringssæt for at opnå mindre end 5% falske positiver.
 #10.6.3    Niveau: 2    Rolle: D
 Bekræft, at input, der er markeret som forgiftede, udløser blød blokering og menneskelig gennemgangsarbejdsgange.
 #10.6.4    Niveau: 2    Rolle: V
 Bekræft, at detektorer er stress-testet med adaptive, triggerløse bagdørsangreb.
 #10.6.5    Niveau: 3    Rolle: D
 Bekræft, at målinger af detektions effektivitet logges og periodisk genvurderes med frisk trusselinformation.

---

### 10.7 Dynamisk tilpasning af sikkerhedspolitik

Opdateringer af sikkerhedspolitikker i realtid baseret på trusselsintelligens og adfærdsanalyse.

 #10.7.1    Niveau: 1    Rolle: D/V
 Bekræft, at sikkerhedspolitikker kan opdateres dynamisk uden genstart af agenten, samtidig med at politikversionens integritet opretholdes.
 #10.7.2    Niveau: 2    Rolle: D/V
 Bekræft, at politikopdateringer er kryptografisk underskrevet af autoriseret sikkerhedspersonale og valideret, før de anvendes.
 #10.7.3    Niveau: 2    Rolle: D/V
 Bekræft, at dynamiske politikændringer logges med fulde revisionsspor, inklusive begrundelse, godkendelseskæder og tilbageførselsprocedurer.
 #10.7.4    Niveau: 3    Rolle: D/V
 Bekræft, at adaptive sikkerhedsmekanismer justerer trusselsdetektionsfølsomheden baseret på risikokontekst og adfærdsmønstre.
 #10.7.5    Niveau: 3    Rolle: D/V
 Bekræft, at beslutninger om politiktilpasning er forklarlige og indeholder bevisspor til gennemgang af sikkerhedsteamet.

---

### 10.8 Reflektionsbaseret sikkerhedsanalyse

Sikkerhedsvalidering gennem agentens selvrefleksion og meta-kognitiv analyse.

 #10.8.1    Niveau: 1    Rolle: D/V
 Bekræft, at agentrefleksionsmekanismer inkluderer sikkerhedsorienteret selvevaluering af beslutninger og handlinger.
 #10.8.2    Niveau: 2    Rolle: D/V
 Sørg for, at refleksionsudgange bliver valideret for at forhindre manipulation af selvvurderingsmekanismer ved hjælp af modstridende input.
 #10.8.3    Niveau: 2    Rolle: D/V
 Bekræft, at meta-kognitiv sikkerhedsanalyse identificerer potentiel bias, manipulation eller kompromittering i agenters ræsonneringsprocesser.
 #10.8.4    Niveau: 3    Rolle: D/V
 Bekræft, at sikkerhedsadvarsler baseret på refleksion udløser forbedret overvågning og potentielle arbejdsgange for menneskelig indgriben.
 #10.8.5    Niveau: 3    Rolle: D/V
 Bekræft, at kontinuerlig læring fra sikkerhedsrefleksioner forbedrer trusselsdetektion uden at forringe legitim funktionalitet.

---

### 10.9 Evolution & Selvforbedringssikkerhed

Sikkerhedskontroller for agentsystemer med evne til selvmodifikation og udvikling.

 #10.9.1    Niveau: 1    Rolle: D/V
 Bekræft, at evnen til selvmodifikation er begrænset til udpegede sikre områder med formelle verifikationsgrænser.
 #10.9.2    Niveau: 2    Rolle: D/V
 Sørg for, at evolutionsforslag gennemgår en sikkerhedsvurdering, før de implementeres.
 #10.9.3    Niveau: 2    Rolle: D/V
 Bekræft, at selvforbedringsmekanismer inkluderer rollback-funktioner med integritetsverifikation.
 #10.9.4    Niveau: 3    Rolle: D/V
 Bekræft, at meta-læringssikkerhed forhindrer fjendtlig manipulation af forbedringsalgoritmer.
 #10.9.5    Niveau: 3    Rolle: D/V
 Verificer, at rekursiv selvforbedring er begrænset af formelle sikkerhedskriterier med matematiske beviser for konvergens.

---

#### Referencer

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

## 11 Beskyttelse af privatliv og håndtering af persondata

### Kontrolmål

Oprethold strenge privatlivsgarantier gennem hele AI-livscyklussen—indsamling, træning, inferens og hændelsesrespons—så persondata kun behandles med klart samtykke, minimalt nødvendigt omfang, beviselig sletning og formelle privatlivsgarantier.

---

### 11.1 Anonymisering og dataminimering

 #11.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at direkte og kvasi-identifikatorer er fjernet eller hash'et.
 #11.1.2    Niveau: 2    Rolle: D/V
 Bekræft, at automatiserede revisioner måler k-anonymitet/l-diversitet og alarmerer, når tærskler falder under politikken.
 #11.1.3    Niveau: 2    Rolle: V
 Bekræft, at model-attributevigtighedsrapporter beviser, at der ikke er nogen identificeringslækage ud over ε = 0.01 gensidig information.
 #11.1.4    Niveau: 3    Rolle: V
 Bekræft, at formelle beviser eller certificering baseret på syntetiske data viser, at risikoen for genidentifikation er ≤ 0,05 selv under koblingsangreb.

---

### 11.2 Ret-og-at-blive-glemt & Håndhævelse af sletning

 #11.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at sletningsanmodninger for dataemner forplanter sig til rå datasæt, checkpoints, embeddings, logs og backup inden for serviceaftaler på under 30 dage.
 #11.2.2    Niveau: 2    Rolle: D
 Bekræft, at "machine-unlearning" rutiner fysisk gentræner eller tilnærmer fjernelse ved hjælp af certificerede unlearning-algoritmer.
 #11.2.3    Niveau: 2    Rolle: V
 Bekræft, at evaluering af shadow-modellen beviser, at slettede poster påvirker mindre end 1% af outputtene efter unlearning.
 #11.2.4    Niveau: 3    Rolle: V
 Bekræft, at slettebegivenheder bliver uforanderligt logget og kan revideres for regulatorer.

---

### 11.3 Differential-Privacy-sikkerhedsforanstaltninger

 #11.3.1    Niveau: 2    Rolle: D/V
 Bekræft, at overvågningspaneler for privatlivs-tab-rapportering giver advarsel, når kumulativ ε overskrider policygrænser.
 #11.3.2    Niveau: 2    Rolle: V
 Bekræft, at black-box privatlivsaudits estimerer ε̂ inden for 10% af den erklærede værdi.
 #11.3.3    Niveau: 3    Rolle: V
 Bekræft, at formelle beviser dækker alle efter-trænings finjusteringer og indlejringer.

---

### 11.4 Formålsbegrænsning & Beskyttelse mod omfangsspredning

 #11.4.1    Niveau: 1    Rolle: D
 Bekræft, at hvert datasæt og model-checkpoint bærer et maskinlæsbart formåls-tag, der er i overensstemmelse med den oprindelige samtykke.
 #11.4.2    Niveau: 1    Rolle: D/V
 Bekræft, at runtime-overvågninger opdager forespørgsler, der er inkonsistente med det deklarerede formål, og udløser blød afvisning.
 #11.4.3    Niveau: 3    Rolle: D
 Bekræft, at policy-as-code-gates blokerer genudrulning af modeller til nye domæner uden DPIA-gennemgang.
 #11.4.4    Niveau: 3    Rolle: V
 Bekræft, at formelle sporbarhedsbeviser viser, at hele livscyklussen for personlige data forbliver inden for det givne samtykkeområde.

---

### 11.5 Samtykkestyring og juridisk grundlag for tracking

 #11.5.1    Niveau: 1    Rolle: D/V
 Bekræft, at en samtykkestyringsplatform (CMP) registrerer tilmeldingsstatus, formål og opbevaringsperiode pr. datasubjekt.
 #11.5.2    Niveau: 2    Rolle: D
 Bekræft, at API'er udsender samtykke-tokens; modeller skal validere token-omfanget før inferens.
 #11.5.3    Niveau: 2    Rolle: D/V
 Bekræft, at afvist eller tilbagetrukket samtykke stopper behandlingspipeline inden for 24 timer.

---

### 11.6 Fødereret læring med privatlivskontrol

 #11.6.1    Niveau: 1    Rolle: D
 Bekræft, at klientopdateringer anvender lokal differentialprivacy-støjtilføjelse før aggregering.
 #11.6.2    Niveau: 2    Rolle: D/V
 Bekræft, at træningsmålinger er differentielt private og aldrig afslører tab for en enkelt klient.
 #11.6.3    Niveau: 2    Rolle: V
 Bekræft, at forgiftningsresistent aggregering (f.eks. Krum/Trimmet-Middel) er aktiveret.
 #11.6.4    Niveau: 3    Rolle: V
 Bekræft, at formelle beviser viser et samlet ε-budget med mindre end 5 nyttetab.

---

#### Referencer

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

## C12 Overvågning, Logning og Anomalidetektion

### Kontrolmål

Denne sektion giver krav til levering af realtids- og retsmedicinsk synlighed i, hvad modellen og andre AI-komponenter ser, gør og returnerer, så trusler kan opdages, prioriteres og læres af.

### C12.1 Anmodning og svar logning

 #12.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle brugerforespørgsler og modelresponser bliver logget med passende metadata (f.eks. tidsstempel, bruger-ID, sessions-ID, modelversion).
 #12.1.2    Niveau: 1    Rolle: D/V
 Bekræft, at logs gemmes i sikre, adgangskontrollerede arkiver med passende opbevaringspolitikker og backupprocedurer.
 #12.1.3    Niveau: 1    Rolle: D/V
 Bekræft, at loglagringssystemer implementerer kryptering både ved lagring og under overførsel for at beskytte følsomme oplysninger indeholdt i logs.
 #12.1.4    Niveau: 1    Rolle: D/V
 Bekræft, at følsomme data i prompts og output automatisk bliver redigeret eller maskeret før logning, med konfigurerbare redigeringsregler for personligt identificerbare oplysninger (PII), legitimationsoplysninger og proprietære oplysninger.
 #12.1.5    Niveau: 2    Rolle: D/V
 Bekræft, at politiske beslutninger og sikkerhedsfiltreringshandlinger logges med tilstrækkelig detaljeringsgrad for at muliggøre revision og fejlfinding af indholdsmoderationssystemer.
 #12.1.6    Niveau: 2    Rolle: D/V
 Bekræft, at logintegriteten er beskyttet gennem f.eks. kryptografiske signaturer eller skrivebeskyttet lagring.

---

### C12.2 Misbrugsdetektion og alarmering

 #12.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at systemet registrerer og alarmerer om kendte jailbreak-mønstre, forsøg på promptinjektion og modstridende input ved hjælp af signaturbaseret detektion.
 #12.2.2    Niveau: 1    Rolle: D/V
 Bekræft, at systemet integreres med eksisterende Security Information and Event Management (SIEM)-platforme ved hjælp af standard logformater og -protokoller.
 #12.2.3    Niveau: 2    Rolle: D/V
 Bekræft, at berigede sikkerhedshændelser inkluderer AI-specifik kontekst såsom modelidentifikatorer, tillidsvurderinger og beslutninger fra sikkerhedsfiltre.
 #12.2.4    Niveau: 2    Rolle: D/V
 Bekræft, at opdagelse af adfærdsafvigelser identificerer usædvanlige samtalemønstre, overdrevne forsøg på genforsøg eller systematiske sonderingsadfærd.
 #12.2.5    Niveau: 2    Rolle: D/V
 Bekræft, at realtidsalarmeringsmekanismer underretter sikkerhedsteams, når potentielle politikovertrædelser eller angrebsforsøg opdages.
 #12.2.6    Niveau: 2    Rolle: D/V
 Bekræft, at brugerdefinerede regler er inkluderet for at opdage AI-specifikke trusselsmønstre, herunder koordinerede jailbreak-forsøg, promptinjektionskampagner og modeludtrækningsangreb.
 #12.2.7    Niveau: 3    Rolle: D/V
 Bekræft, at automatiserede hændelsesrespons-workflows kan isolere kompromitterede modeller, blokere ondsindede brugere og eskalere kritiske sikkerhedshændelser.

---

### C12.3 Model Drift Overvågning

 #12.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at systemet sporer grundlæggende ydelsesmetrikker såsom nøjagtighed, tillidsværdier, latenstid og fejlrater på tværs af modelversioner og tidsperioder.
 #12.3.2    Niveau: 2    Rolle: D/V
 Bekræft, at automatiseret alarmering udløses, når ydeevnemålinger overskrider foruddefinerede nedbrydningsterskler eller afviger markant fra baselineværdier.
 #12.3.3    Niveau: 2    Rolle: D/V
 Bekræft, at overvågningsværktøjer til hallucinationsdetektion identificerer og markerer tilfælde, hvor modeloutput indeholder faktuelt forkert, inkonsistent eller fabrikeret information.

---

### C12.4 Ydelse og Adfærd Telemetri

 #12.4.1    Niveau: 1    Rolle: D/V
 Bekræft, at operationelle metrics, herunder forespørgselsforsinkelse, tokenforbrug, hukommelsesforbrug og gennemløb, kontinuerligt indsamles og overvåges.
 #12.4.2    Niveau: 1    Rolle: D/V
 Bekræft, at succes- og fejlsatser spores med kategorisering af fejltyper og deres grundårsager.
 #12.4.3    Niveau: 2    Rolle: D/V
 Bekræft, at overvågning af ressourceudnyttelse inkluderer GPU/CPU-brug, hukommelsesforbrug og lagerkrav med alarmering ved overskridelse af tærskler.

---

### C12.5 AI hændelsesresponsplanlægning og -udførelse

 #12.5.1    Niveau: 1    Rolle: D/V
 Verificer, at beredskabsplaner for hændelser specifikt omhandler AI-relaterede sikkerhedshændelser, herunder modelkompromittering, datapoisning og adversariale angreb.
 #12.5.2    Niveau: 2    Rolle: D/V
 Sørg for, at incident response-hold har adgang til AI-specifikke retsmedicinske værktøjer og ekspertise til at undersøge modeladfærd og angrebsvinkler.
 #12.5.3    Niveau: 3    Rolle: D/V
 Bekræft, at efter-incident-analyse inkluderer overvejelser om modelgenindlæring, opdateringer af sikkerhedsfiltre og integration af erfaringer i sikkerhedskontroller.

---

### C12.5 AI-ydelsesforringelsesdetektion

Overvåg og påvis forringelse i AI-modelpræstation og kvalitet over tid.

 #12.5.1    Niveau: 1    Rolle: D/V
 Sørg for, at modelpræcision, nøjagtighed, tilbagekaldelse og F1-scores løbende overvåges og sammenlignes med baseline-grænseværdier.
 #12.5.2    Niveau: 1    Rolle: D/V
 Bekræft, at data drift-overvågning registrerer ændringer i inputfordelingen, der kan påvirke modellens ydeevne.
 #12.5.3    Niveau: 2    Rolle: D/V
 Bekræft, at konceptdrejningsdetektion identificerer ændringer i forholdet mellem input og forventede output.
 #12.5.4    Niveau: 2    Rolle: D/V
 Bekræft, at ydelsesforringelse udløser automatiserede alarmer og igangsætter arbejdsgange for omtræning eller udskiftning af modellen.
 #12.5.5    Niveau: 3    Rolle: V
 Bekræft, at årsagsanalysen for forringelse korrelerer ydelsesfald med datændringer, infrastrukturelle problemer eller eksterne faktorer.

---

### C12.6 DAG-visualisering og workflow-sikkerhed

Beskyt workflow-visualiseringssystemer mod informationslækage og manipulationsangreb.

 #12.6.1    Niveau: 1    Rolle: D/V
 Bekræft, at DAG-visualiseringsdata er renset for at fjerne følsomme oplysninger, inden de lagres eller overføres.
 #12.6.2    Niveau: 1    Rolle: D/V
 Bekræft, at adgangskontroller til workflow-visualisering sikrer, at kun autoriserede brugere kan se agentens beslutningsstier og ræsonnementsspor.
 #12.6.3    Niveau: 2    Rolle: D/V
 Bekræft, at DAG-dataintegriteten er beskyttet gennem kryptografiske signaturer og manipulation-synlige lagringsmekanismer.
 #12.6.4    Niveau: 2    Rolle: D/V
 Verificer, at workflow-visualiseringssystemer implementerer inputvalidering for at forhindre injektionsangreb gennem manipulerede node- eller kantdata.
 #12.6.5    Niveau: 3    Rolle: D/V
 Bekræft, at opdateringer af realtids-DAG'er er ratebegrænsede og validerede for at forhindre denial-of-service-angreb på visualiseringssystemer.

---

### C12.7 Proaktiv overvågning af sikkerhedsadfærd

Detektion og forebyggelse af sikkerhedstrusler gennem proaktiv agentadfærdsanalyse.

 #12.7.1    Niveau: 1    Rolle: D/V
 Verificer, at proaktive agentadfærd er sikkerhedsvaliderede før udførelse med integration af risikovurdering.
 #12.7.2    Niveau: 2    Rolle: D/V
 Bekræft, at autonome initiativudløsere inkluderer evaluering af sikkerhedskontekst og vurdering af trusselslandskabet.
 #12.7.3    Niveau: 2    Rolle: D/V
 Bekræft, at proaktive adfærdsmønstre analyseres for potentielle sikkerhedsmæssige konsekvenser og utilsigtede følgevirkninger.
 #12.7.4    Niveau: 3    Rolle: D/V
 Bekræft, at sikkerhedskritiske proaktive handlinger kræver eksplicitte godkendelseskæder med revisionsspor.
 #12.7.5    Niveau: 3    Rolle: D/V
 Bekræft, at adfærdsafvigelsesdetektion identificerer afvigelser i proaktive agentmønstre, der kan indikere kompromittering.

---

### Referencer

NIST AI Risk Management Framework 1.0 - Manage 4.1 and 4.3
ISO/IEC 42001:2023 — AI Management Systems Requirements - Annex B 6.2.6
EU AI Act — Article 12, 13, 16 and 19 on Logging and Record-keeping

## C13 Menneskelig Tilsyn, Ansvarlighed & Styring

### Kontrolmål

Dette kapitel indeholder krav til at opretholde menneskelig overvågning og klare ansvarskæder i AI-systemer, hvilket sikrer forklarlighed, gennemsigtighed og etisk forvaltning gennem hele AI-livscyklussen.

---

### C13.1 Kill-Switch & Override-mekanismer

Sørg for nedluknings- eller tilbagestillingsmuligheder, når usikker adfærd i AI-systemet observeres.

 #13.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at der findes en manuel driftsafbrydermekanisme til øjeblikkeligt at stoppe AI-modelinference og output.
 #13.1.2    Niveau: 1    Rolle: D
 Bekræft, at tilsidesættelseskontroller kun er tilgængelige for autoriseret personale.
 #13.1.3    Niveau: 3    Rolle: D/V
 Bekræft, at rollback-procedurer kan vende tilbage til tidligere modelversioner eller sikkerhedstilstandens operationer.
 #13.1.4    Niveau: 3    Rolle: V
 Sørg for, at overskrivningsmekanismer testes regelmæssigt.

---

### C13.2 Menneske-i-løkken beslutningskontrolpunkter

Krav menneskelig godkendelse, når indsatsen overskrider foruddefinerede risikogrænser.

 #13.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at højrisiko AI-beslutninger kræver eksplicit menneskelig godkendelse, før de udføres.
 #13.2.2    Niveau: 1    Rolle: D
 Sørg for, at risikogrænser er klart definerede og automatisk udløser menneskelig gennemgangsarbejdsgang.
 #13.2.3    Niveau: 2    Rolle: D
 Bekræft, at tidsfølsomme beslutninger har reservemetoder, når godkendelse fra mennesker ikke kan opnås inden for de krævede tidsrammer.
 #13.2.4    Niveau: 3    Rolle: D/V
 Bekræft, at eskaleringsprocedurer definerer klare myndighedsniveauer for forskellige beslutningstyper eller risikokategorier, hvis relevant.

---

### C13.3 Ansvarskæde og revisionsmulighed

Log operatørhandlinger og modelbeslutninger.

 #13.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at alle AI-systembeslutninger og menneskelige indgreb logges med tidsstempler, brugeridentiteter og beslutningsbegrundelser.
 #13.3.2    Niveau: 2    Rolle: D
 Bekræft, at revisionslogfiler ikke kan manipuleres, og inkluder mekanismer til integritetsverifikation.

---

### C13.4 Forklarlige AI-teknikker

Vigtighed af overfladefunktioner, kontra-faktiske eksempler og lokale forklaringer.

 #13.4.1    Niveau: 1    Rolle: D/V
 Sørg for, at AI-systemer giver grundlæggende forklaringer på deres beslutninger i et menneskeligt læsbart format.
 #13.4.2    Niveau: 2    Rolle: V
 Bekræft, at forklaringskvaliteten er valideret gennem menneskelige evalueringsstudier og målinger.
 #13.4.3    Niveau: 3    Rolle: D/V
 Bekræft, at feature importance-scores eller attribueringsmetoder (SHAP, LIME osv.) er tilgængelige for kritiske beslutninger.
 #13.4.4    Niveau: 3    Rolle: V
 Bekræft, at kontrafaktiske forklaringer viser, hvordan input kan ændres for at ændre resultater, hvis det er relevant for brugstilfældet og domænet.

---

### C13.5 Modelkort og brugsoplysninger

Vedligehold modelkort for tiltænkt anvendelse, præstationsmålinger og etiske overvejelser.

 #13.5.1    Niveau: 1    Rolle: D
 Bekræft, at modelkort dokumenterer tilsigtede anvendelsestilfælde, begrænsninger og kendte fejlsituationer.
 #13.5.2    Niveau: 1    Rolle: D/V
 Bekræft, at ydelsesmålinger på tværs af forskellige relevante anvendelsestilfælde er oplyst.
 #13.5.3    Niveau: 2    Rolle: D
 Bekræft, at etiske overvejelser, vurderinger af bias, evalueringer af retfærdighed, karakteristika ved træningsdata og kendte begrænsninger i træningsdata dokumenteres og opdateres regelmæssigt.
 #13.5.4    Niveau: 2    Rolle: D/V
 Bekræft, at modelkort er versionsstyrede og vedligeholdes gennem hele modellens livscyklus med ændringssporing.

---

### C13.6 Usikkerhedskvantificering

Propagér konfidensscores eller entropimål i svarene.

 #13.6.1    Niveau: 1    Rolle: D
 Bekræft, at AI-systemer leverer tillidsvurderinger eller usikkerhedsmål sammen med deres output.
 #13.6.2    Niveau: 2    Rolle: D/V
 Bekræft, at usikkerhedsterskler udløser yderligere menneskelig gennemgang eller alternative beslutningsveje.
 #13.6.3    Niveau: 2    Rolle: V
 Verificer, at metoder til usikkerhedskvantificering er kalibrerede og validerede mod grundlæggende sandhedsdata.
 #13.6.4    Niveau: 3    Rolle: D/V
 Bekræft, at usikkerhedspropagering opretholdes gennem flerstegs AI-arbejdsgange.

---

### C13.7 Brugervenlige gennemsigtighedsrapporter

Giv periodiske oplysninger om hændelser, drift og dataanvendelse.

 #13.7.1    Niveau: 1    Rolle: D/V
 Bekræft, at politikker for dataanvendelse og praksis for håndtering af brugeraccept klart kommunikeres til interessenter.
 #13.7.2    Niveau: 2    Rolle: D/V
 Bekræft, at AI-påvirkningsvurderinger udføres, og at resultaterne er inkluderet i rapporteringen.
 #13.7.3    Niveau: 2    Rolle: D/V
 Bekræft, at gennemsigtighedsrapporter, der offentliggøres regelmæssigt, afslører AI-hændelser og operationelle målinger i rimelig detalje.

#### Referencer

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

## Appendiks A: Ordliste

Denne omfattende ordliste giver definitioner på nøglebegreber inden for AI, ML og sikkerhed, som anvendes gennem hele AISVS for at sikre klarhed og fælles forståelse.

Adversarial eksempel: En input bevidst udformet til at få en AI-model til at begå en fejl, ofte ved at tilføje subtile forstyrrelser, som er umærkelige for mennesker.
​
Adversarial Robustness – Adversarial robusthed i AI henviser til en models evne til at opretholde sin ydeevne og modstå at blive narret eller manipuleret af bevidst konstruerede, skadelige input designet til at forårsage fejl.
​
Agent – AI-agenter er software-systemer, der bruger AI til at forfølge mål og udføre opgaver på vegne af brugerne. De udviser ræsonnering, planlægning og hukommelse og har et vist niveau af autonomi til at træffe beslutninger, lære og tilpasse sig.
​
Agentisk AI: AI-systemer, der kan operere med en vis grad af autonomi for at opnå mål, ofte ved at træffe beslutninger og udføre handlinger uden direkte menneskelig indgriben.
​
Attribueret adgangskontrol (ABAC): Et adgangskontrolparadigme, hvor autorisationsbeslutninger baseres på attributter for brugeren, ressourcen, handlingen og miljøet, vurderet på forespørgselstidspunktet.
​
Bagdørsangreb: En type dataforureningsangreb, hvor modellen trænes til at reagere på en bestemt måde på visse triggere, mens den ellers opfører sig normalt.
​
Bias: Systematiske fejl i AI-modeludgange, der kan føre til uretfærdige eller diskriminerende resultater for visse grupper eller i specifikke kontekster.
​
Biasudnyttelse: En angrebsteknik, der udnytter kendte bias i AI-modeller til at manipulere output eller resultater.
​
Cedar: Amazons politik-sprog og motor til detaljerede tilladelser, der bruges til implementering af ABAC for AI-systemer.
​
Chain of Thought: En teknik til at forbedre ræsonnement i sprogmodeller ved at generere mellemliggende ræsonnementstrin, før der produceres et endeligt svar.
​
Kredsløbsafbrydere: Mekanismer, der automatisk stopper AI-systemets drift, når specifikke risikogrænser overskrides.
​
Data Lækage: Utilsigtet eksponering af følsomme oplysninger gennem AI-models output eller adfærd.
​
Dataforgiftning: Den bevidste forvanskning af træningsdata for at kompromittere modellens integritet, ofte for at installere bagdøre eller forringe ydelsen.
​
Differential Privacy – Differential privacy er en matematisk stringent ramme for udgivelse af statistisk information om datasæt samtidig med beskyttelse af privatlivet for individuelle datasubjekter. Det gør det muligt for en dataholder at dele samlede mønstre for gruppen, samtidig med at information, der afsløres om specifikke individer, begrænses.
​
Embedninger: Tætte vektorrepræsentationer af data (tekst, billeder osv.), der fanger semantisk mening i et højdimensionelt rum.
​
Forklarbarhed – Forklarbarhed i AI er evnen hos et AI-system til at give menneskeligt forståelige grunde for dets beslutninger og forudsigelser, hvilket tilbyder indsigt i dets interne funktioner.
​
Forklarbar AI (XAI): AI-systemer designet til at give menneskeligt forståelige forklaringer på deres beslutninger og adfærd gennem forskellige teknikker og rammeværk.
​
Federeret læring: En maskinlæringsmetode, hvor modeller trænes på tværs af flere decentraliserede enheder, der indeholder lokale datasamples, uden at udveksle selve dataene.
​
Guardrails: Begrænsninger implementeret for at forhindre AI-systemer i at producere skadelige, forudindtagede eller på anden måde uønskede output.
​
Hallucination – En AI-hallucination refererer til et fænomen, hvor en AI-model genererer forkert eller vildledende information, som ikke er baseret på dens træningsdata eller faktuelle virkelighed.
​
Human-in-the-Loop (HITL): Systemer designet til at kræve menneskelig overvågning, verifikation eller indgriben ved afgørende beslutningspunkter.
​
Infrastructure as Code (IaC): Administration og levering af infrastruktur gennem kode i stedet for manuelle processer, hvilket muliggør sikkerhedsscanning og konsistente udrulninger.
​
Jailbreak: Teknikker brugt til at omgå sikkerhedsværn i AI-systemer, især i store sprogmodeller, for at producere forbudt indhold.
​
Mindste privilegium: Sikkerhedsprincippet om kun at give de nødvendige minimumsadgangsrettigheder til brugere og processer.
​
LIME (Local Interpretable Model-agnostic Explanations): En teknik til at forklare forudsigelser fra enhver maskinlæringsklassifikator ved at tilnærme den lokalt med en fortolkbar model.
​
Membership Inference Attack: Et angreb, der har til formål at afgøre, om et specifikt datapunkt blev brugt til at træne en maskinlæringsmodel.
​
MITRE ATLAS: Adversarial Threat Landscape for Artificial-Intelligence Systems; en vidensbase over modstanderes taktikker og teknikker mod AI-systemer.
​
Modelkort – Et modelkort er et dokument, der giver standardiseret information om en AI-modells ydeevne, begrænsninger, tilsigtede anvendelser og etiske overvejelser for at fremme gennemsigtighed og ansvarlig AI-udvikling.
​
Modeludtrækning: Et angreb, hvor en modstander gentagne gange forespørger en målmodel for at skabe en funktionelt lignende kopi uden autorisation.
​
Modelinversion: Et angreb, der forsøger at rekonstruere træningsdata ved at analysere modeludgange.
​
Model Lifecycle Management – AI Model Lifecycle Management er processen med at overvåge alle faser af en AI-models eksistens, inklusive dens design, udvikling, implementering, overvågning, vedligeholdelse og endelige udfasning, for at sikre, at den forbliver effektiv og i overensstemmelse med målsætningerne.
​
Modelforgiftning: Indførelse af sårbarheder eller bagdøre direkte i en model under træningsprocessen.
​
Modeltyveri/tyveri: Udtrækning af en kopi eller tilnærmelse af en proprietær model gennem gentagne forespørgsler.
​
Multi-agent System: Et system sammensat af flere interagerende AI-agenter, hver med potentielt forskellige kapabiliteter og mål.
​
OPA (Open Policy Agent): En open-source policy motor, der muliggør en ensartet håndhævelse af politikker på tværs af hele systemet.
​
Privatlivsbeskyttende Maskinlæring (PPML): Teknikker og metoder til at træne og implementere ML-modeller, samtidig med at træningsdataenes privatliv beskyttes.
​
Prompt Injection: Et angreb, hvor ondsindede instruktioner bliver indlejret i input for at tilsidesætte en models tilsigtede adfærd.
​
RAG (Retrieval-Augmented Generation): En teknik, der forbedrer store sprogmodeller ved at hente relevant information fra eksterne videnskilder, før der genereres et svar.
​
Red-Teaming: Praksis med aktivt at teste AI-systemer ved at simulere fjendtlige angreb for at identificere sårbarheder.
​
SBOM (Software Bill of Materials): En formel registrering, der indeholder detaljer og leverandørkædeforhold for forskellige komponenter, der anvendes til at bygge software eller AI-modeller.
​
SHAP (SHapley Additive exPlanations): En spilteoretisk tilgang til at forklare output fra enhver maskinlæringsmodel ved at beregne bidraget fra hver funktion til forudsigelsen.
​
Supply Chain Attack: Kompromittering af et system ved at målrette mindre sikre elementer i dets forsyningskæde, såsom tredjepartsbiblioteker, datasæt eller fortrænede modeller.
​
Transfer Learning: En teknik hvor en model udviklet til en opgave genbruges som udgangspunkt for en model til en anden opgave.
​
Vektordatabase: En specialiseret database designet til at gemme højdimensionelle vektorer (indlejringer) og udføre effektive søgninger efter lighed.
​
Sårbarhedsscanning: Automatiserede værktøjer, der identificerer kendte sikkerhedssårbarheder i softwarekomponenter, herunder AI-rammeværk og afhængigheder.
​
Vandmærkning: Teknikker til at indlejre uigenkendelige markører i AI-genereret indhold for at spore dets oprindelse eller opdage AI-generering.
​
Zero-Day-sårbarhed: En tidligere ukendt sårbarhed, som angribere kan udnytte, før udviklere skaber og implementerer en rettelse.

## Bilag B: Referencer

### TODO

## Appendiks C: AI-sikkerhedsstyring og dokumentation

### Mål

Dette appendiks giver grundlæggende krav til etablering af organisatoriske strukturer, politikker og processer til at styre AI-sikkerhed gennem hele systemets livscyklus.

---

### AC.1 Implementering af risikostyringsrammen for AI

Giv en formel ramme for at identificere, vurdere og afbøde AI-specifikke risici gennem hele systemets livscyklus.

 #AC.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at en AI-specifik risikovurderingsmetode er dokumenteret og implementeret.
 #AC.1.2    Niveau: 2    Rolle: D
 Bekræft, at risikovurderinger udføres på nøglepunkter i AI-livscyklussen og før væsentlige ændringer.
 #AC.1.3    Niveau: 3    Rolle: D/V
 Bekræft, at risikostyringsrammen er i overensstemmelse med etablerede standarder (f.eks. NIST AI RMF).

---

### AC.2 AI Sikkerhedspolitik & Procedurer

Definér og håndhæv organisatoriske standarder for sikker AI-udvikling, implementering og drift.

 #AC.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at dokumenterede AI-sikkerhedspolitikker findes.
 #AC.2.2    Niveau: 2    Rolle: D
 Sørg for, at politikker bliver gennemgået og opdateret mindst årligt og efter væsentlige ændringer i trusselslandskabet.
 #AC.2.3    Niveau: 3    Rolle: D/V
 Bekræft, at politikker dækker alle AISVS-kategorier og gældende lovgivningskrav.

---

### AC.3 Roller og ansvar for AI-sikkerhed

Etabler klar ansvarlighed for AI-sikkerhed på tværs af organisationen.

 #AC.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at AI-sikkerhedsroller og -ansvar er dokumenteret.
 #AC.3.2    Niveau: 2    Rolle: D
 Bekræft, at ansvarlige personer besidder passende sikkerhedsekspertise.
 #AC.3.3    Niveau: 3    Rolle: D/V
 Bekræft, at der er etableret et AI-etikudvalg eller en styringsgruppe for højrisiko AI-systemer.

---

### AC.4 Håndhævelse af etiske AI-retningslinjer

Sikre, at AI-systemer fungerer i overensstemmelse med etablerede etiske principper.

 #AC.4.1    Niveau: 1    Rolle: D/V
 Bekræft, at der findes etiske retningslinjer for udvikling og implementering af AI.
 #AC.4.2    Niveau: 2    Rolle: D
 Sørg for, at der er mekanismer på plads til at opdage og rapportere etiske overtrædelser.
 #AC.4.3    Niveau: 3    Rolle: D/V
 Bekræft, at regelmæssige etiske anmeldelser af implementerede AI-systemer bliver udført.

---

### AC.5 AI Overholdelse af Regulatorisk Overvågning

Oprethold bevidsthed om og overholdelse af de udviklende AI-regulativer.

 #AC.5.1    Niveau: 1    Rolle: D/V
 Bekræft, at der findes processer til at identificere gældende AI-reguleringer.
 #AC.5.2    Niveau: 2    Rolle: D
 Bekræft, at overholdelse af alle lovgivningsmæssige krav vurderes.
 #AC.5.3    Niveau: 3    Rolle: D/V
 Bekræft, at regulatoriske ændringer udløser rettidige gennemgange og opdateringer af AI-systemer.

### AC.6 Træningsdatastyring, dokumentation og proces

 #1.1.2    Niveau: 1    Rolle: D/V
 Sørg for, at kun datasæt, der er godkendt for kvalitet, repræsentativitet, etisk ophav og overholdelse af licens, tillades, hvilket reducerer risiciene for forurening, indlejret bias og krænkelse af intellektuelle rettigheder.
 #1.1.5    Niveau: 2    Rolle: D/V
 Sørg for, at kvaliteten af mærkning/annotering sikres via krydstjek af anmeldere eller konsensus.
 #1.1.6    Niveau: 2    Rolle: D/V
 Bekræft, at "datakort" eller "datasheets for datasæt" opretholdes for betydelige træningsdatasæt, og indeholder detaljer om karakteristika, motivationer, sammensætning, indsamling, forbehandling samt anbefalede/afrådede anvendelser.
 #1.3.2    Niveau: 2    Rolle: D/V
 Bekræft, at de identificerede skævheder afhjælpes via dokumenterede strategier såsom rebalancering, målrettet dataforøgelse, algoritmiske justeringer (f.eks. præ-processering, i-processering, post-processeringsteknikker) eller omvægtningsmetoder, og at virkningen af afhjælpning både på retfærdighed og på den samlede modelpræstation vurderes.
 #1.3.3    Niveau: 2    Rolle: D/V
 Bekræft, at fairness-metrikker efter træning bliver evalueret og dokumenteret.
 #1.3.4    Niveau: 3    Rolle: D/V
 Bekræft, at en politik for livscyklus bias-styring tildeler ejere og gennemgangsrytme.
 #1.4.1    Niveau: 2    Rolle: D/V
 Sørg for, at kvaliteten af mærkning/annotering sikres gennem klare retningslinjer, krydstjek af anmeldere, konsensusmekanismer (f.eks. overvågning af overensstemmelse mellem annotatorer) og definerede processer til løsning af uoverensstemmelser.
 #1.4.4    Niveau: 3    Rolle: D/V
 Bekræft, at etiketter, der er afgørende for sikkerhed, tryghed eller retfærdighed (f.eks. identificering af giftigt indhold, kritiske medicinske fund), gennemgår obligatorisk uafhængig dobbeltsyn eller tilsvarende robust verifikation.
 #1.4.6    Niveau: 2    Rolle: D/V
 Bekræft, at mærkningsvejledninger og instruktioner er omfattende, versionsstyrede og peer-reviewed.
 #1.4.6    Niveau: 2    Rolle: D/V
 Sørg for, at datastrukturer for etiketter er klart definerede og versionskontrollerede.
 #1.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at datasæt er profileret for repræsentationsmæssig ubalance og potentielle biaser på tværs af lovligt beskyttede attributter (f.eks. race, køn, alder) og andre etisk følsomme karakteristika, der er relevante for modellens anvendelsesområde (f.eks. socioøkonomisk status, placering).
 #1.5.3    Niveau: 2    Rolle: V
 Bekræft, at manuelle stikprøvekontroller udført af domæneeksperter dækker en statistisk signifikant prøve (f.eks. ≥1% eller 1.000 prøver, alt efter hvilket der er størst, eller som bestemt af risikovurdering) for at identificere subtile kvalitetsproblemer, som ikke fanges af automatisering.
 #1.8.4    Niveau: 2    Rolle: D/V
 Bekræft, at outsourcing eller crowdsourcing af mærkningsarbejdsgange inkluderer tekniske/procedurale sikkerhedsforanstaltninger for at sikre datakonfidentialitet, integritet, mærkningskvalitet og forhindre datalækage.
 #1.5.4    Niveau: 2    Rolle: D/V
 Bekræft, at udbedringsskridtene er tilføjet til oprindelsesregistre.
 #1.6.2    Niveau: 2    Rolle: D/V
 Bekræft, at markerede prøver udløser manuel gennemgang før træning.
 #1.6.3    Niveau: 2    Rolle: V
 Bekræft, at resultaterne føder modellens sikkerhedsdossier og informerer løbende trusselsintelligens.
 #1.6.4    Niveau: 3    Rolle: D/V
 Bekræft, at detektionslogikken opdateres med ny trusselsinformation.
 #1.6.5    Niveau: 3    Rolle: D/V
 Bekræft, at online-læringspipelines overvåger distributionsskift.
 #1.7.1    Niveau: 1    Rolle: D/V
 Bekræft, at arbejdsprocesser for sletning af træningsdata fjerner primære og afledte data og vurderer modellens indvirkning, samt at indvirkningen på berørte modeller vurderes og, hvis nødvendigt, håndteres (f.eks. gennem genoptræning eller recalibrering).
 #1.7.2    Niveau: 2    Rolle: D
 Bekræft, at der er mekanismer på plads til at spore og respektere omfanget og status for brugerens samtykke (og tilbagetrækninger) til data, der bruges i træning, og at samtykke valideres, før data indarbejdes i nye træningsprocesser eller betydelige modelopdateringer.
 #1.7.3    Niveau: 2    Rolle: V
 Bekræft, at workflows testes årligt og logges.
 #1.8.1    Niveau: 2    Rolle: D/V
 Sørg for, at tredjepartsdataudbydere, herunder leverandører af forudtrænede modeller og eksterne datasæt, gennemgår sikkerheds-, privatlivs-, etisk indkøb- og datakvalitetsdue diligence, før deres data eller modeller integreres.
 #1.8.2    Niveau: 1    Rolle: D
 Bekræft, at eksterne overførsler bruger TLS/autentificering og integritetskontrol.
 #1.8.3    Niveau: 2    Rolle: D/V
 Bekræft, at højriskokilder til data (f.eks. open source-datasæt med ukendt oprindelse, uverificerede leverandører) modtager øget kontrol, såsom sandkasseanalyser, omfattende kvalitets-/biaskontroller og målrettet forgiftningsdetektion, før de anvendes i følsomme applikationer.
 #1.8.4    Niveau: 3    Rolle: D/V
 Sørg for, at forudtrænede modeller, der er erhvervet fra tredjeparter, bliver evalueret for indlejrede skævheder, potentielle bagdøre, integriteten af deres arkitektur og proveniensen af deres oprindelige træningsdata, før de finjusteres eller implementeres.
 #1.5.3    Niveau: 2    Rolle: D/V
 Bekræft, at hvis adversarial træning anvendes, dokumenteres og kontrolleres generering, håndtering og versionering af adversariale datasæt.
 #1.5.3    Niveau: 3    Rolle: D/V
 Bekræft, at virkningen af træning i modstandsdygtighed over for angreb på modelpræstationer (både mod rene og mod angreb rettede input) samt retfærdighedsmetrikker bliver evalueret, dokumenteret og monitoreret.
 #1.5.4    Niveau: 3    Rolle: D/V
 Sørg for, at strategier for modstandsdygtighed og træning mod angreb regelmæssigt gennemgås og opdateres for at modvirke udviklende teknikker til modstanderangreb.
 #1.4.2    Niveau: 2    Rolle: D/V
 Bekræft, at fejlede datasæt er sat i karantæne med revisionsspor.
 #1.4.3    Niveau: 2    Rolle: D/V
 Bekræft, at kvalitetsporte blokerer undermålige datasæt, medmindre undtagelser er godkendt.
 #1.11.2    Niveau: 2    Rolle: D/V
 Bekræft, at genereringsprocessen, parametrene og den tilsigtede anvendelse af syntetiske data er dokumenteret.
 #1.11.3    Niveau: 2    Rolle: D/V
 Sørg for, at syntetiske data er risikovurderet for bias, privatlivsbrud og repræsentationsproblemer, før de bruges i træning.
 #1.12.3    Niveau: 2    Rolle: D/V
 Bekræft, at der genereres advarsler ved mistænkelige adgangsbegivenheder, og at de undersøges hurtigt.
 #1.13.1    Niveau: 1    Rolle: D/V
 Bekræft, at eksplicitte opbevaringsperioder er defineret for alle træningsdatasæt.
 #1.13.2    Niveau: 2    Rolle: D/V
 Bekræft, at datasæt automatisk udløber, slettes eller gennemgås til sletning ved slutningen af deres livscyklus.
 #1.13.3    Niveau: 2    Rolle: D/V
 Bekræft, at tilbageholdelses- og sletningshandlinger registreres og er reviderbare.
 #1.14.1    Niveau: 2    Rolle: D/V
 Bekræft, at krav til dataresidens og grænseoverskridende overførsler er identificeret og håndhævet for alle datasæt.
 #1.14.2    Niveau: 2    Rolle: D/V
 Bekræft, at sektorspecifikke regler (f.eks. sundhedspleje, finans) bliver identificeret og håndteret i datahåndteringen.
 #1.14.3    Niveau: 2    Rolle: D/V
 Verificer, at overholdelse af relevante privatlivslove (f.eks. GDPR, CCPA) er dokumenteret og gennemgås regelmæssigt.
 #1.16.1    Niveau: 2    Rolle: D/V
 Bekræft, at der findes mekanismer til at reagere på dataemners anmodninger om adgang, berigtigelse, begrænsning eller indsigelse.
 #1.16.2    Niveau: 2    Rolle: D/V
 Bekræft, at forespørgsler bliver logget, sporet og opfyldt inden for lovbestemte tidsrammer.
 #1.16.3    Niveau: 2    Rolle: D/V
 Bekræft, at processerne for registreredes rettigheder testes og gennemgås regelmæssigt for effektivitet.
 #1.17.1    Niveau: 2    Rolle: D/V
 Bekræft, at der udføres en konsekvensanalyse, før en datasætversion opdateres eller udskiftes, som omfatter modelpræstation, retfærdighed og overholdelse.
 #1.17.2    Niveau: 2    Rolle: D/V
 Bekræft, at resultaterne af konsekvensanalysen er dokumenteret og gennemgået af relevante interessenter.
 #1.17.3    Niveau: 2    Rolle: D/V
 Bekræft, at der findes rollback-planer i tilfælde af, at nye versioner introducerer uacceptable risici eller tilbageskridt.
 #1.18.1    Niveau: 2    Rolle: D/V
 Sørg for, at alt personale involveret i dataannotering er baggrundstjekket og trænet i datasikkerhed og privatliv.
 #1.18.2    Niveau: 2    Rolle: D/V
 Sørg for, at alt annoteringspersonale underskriver fortroligheds- og ikke-offentliggørelsesaftaler.
 #1.18.3    Niveau: 2    Rolle: D/V
 Bekræft, at annoteringsplatforme håndhæver adgangskontroller og overvåger for interne trusler.

#### Referencer

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
ISO/IEC 23894:2023 — Artificial Intelligence — Guidance on Risk Management
EU Artificial Intelligence Act — Regulation (EU) 2024/1689
ISO/IEC 24029‑2:2023 — Robustness of Neural Networks — Methodology for Formal Methods

## Appendiks D: AI-assisteret styring og verifikation af sikker kodning

### Mål

Dette kapitel definerer baseline organisatoriske kontroller for sikker og effektiv brug af AI-assisterede kodningsværktøjer under softwareudvikling og sikrer sikkerhed og sporbarhed gennem hele SDLC.

---

### AD.1 AI-assisteret sikker-kodings arbejdsgang

Integrer AI-værktøjer i organisationens sikre softwareudviklingslivscyklus (SSDLC) uden at svække de eksisterende sikkerhedsporter.

 #AD.1.1    Niveau: 1    Rolle: D/V
 Bekræft, at en dokumenteret arbejdsgang beskriver, hvornår og hvordan AI-værktøjer kan generere, omstrukturere eller gennemgå kode.
 #AD.1.2    Niveau: 2    Rolle: D
 Bekræft, at workflowet svarer til hver fase i SSDLC (design, implementering, kodegennemgang, test, implementering).
 #AD.1.3    Niveau: 3    Rolle: D/V
 Bekræft, at metrikker (f.eks. sårbarhedstæthed, gennemsnitlig tid til opdagelse) indsamles for AI-genereret kode og sammenlignes med kun menneskelige baselines.

---

### AD.2 AI-værktøjskvalificering og trusselsmodellering

Sørg for, at AI-kodeværktøjer vurderes for sikkerhedsfunktioner, risiko og forsyningskædepåvirkning inden implementering.

 #AD.2.1    Niveau: 1    Rolle: D/V
 Bekræft, at en trusselsmodel for hvert AI-værktøj identificerer misbrug, modelinversion, data lækage og afhængighedskæde-risici.
 #AD.2.2    Niveau: 2    Rolle: D
 Bekræft, at blivevurderinger af værktøjer inkluderer statisk/dynamisk analyse af eventuelle lokale komponenter samt vurdering af SaaS-endepunkter (TLS, autentificering/autorisation, logning).
 #AD.2.3    Niveau: 3    Rolle: D/V
 Verificer, at evalueringer følger en anerkendt ramme og udføres igen efter større versionsændringer.

---

### AD.3 Sikker Prompt- og Kontekststyring

Forebyg lækage af hemmeligheder, proprietær kode og persondata ved opbygning af prompts eller kontekster til AI-modeller.

 #AD.3.1    Niveau: 1    Rolle: D/V
 Bekræft, at skriftlige retningslinjer forbyder at sende hemmeligheder, legitimationsoplysninger eller klassificerede data i prompts.
 #AD.3.2    Niveau: 2    Rolle: D
 Bekræft, at tekniske kontroller (klient-side redigering, godkendte kontekstfiltre) automatisk fjerner følsomme elementer.
 #AD.3.3    Niveau: 3    Rolle: D/V
 Bekræft, at prompts og svar bliver tokeniseret, krypteret under overførsel og i hvile, og at opbevaringsperioderne overholder dataklassifikationspolitikken.

---

### AD.4 Validering af AI-genereret kode

Registrer og udbedr sårbarheder, som AI-output har introduceret, før koden flettes eller implementeres.

 #AD.4.1    Niveau: 1    Rolle: D/V
 Sørg for, at AI-genereret kode altid gennemgås af mennesker.
 #AD.4.2    Niveau: 2    Rolle: D
 Bekræft, at automatiserede scannere (SAST/IAST/DAST) kører på hver pull-anmodning, der indeholder AI-genereret kode, og blokerer sammenfletninger ved kritiske fund.
 #AD.4.3    Niveau: 3    Rolle: D/V
 Bekræft, at differential fuzz testing eller egenskabsbaserede tests beviser sikkerhedskritiske adfærd (f.eks. inputvalidering, autorisationslogik).

---

### AD.5 Forklarbarhed og Sporbarhed af Kodeforslag

Giv revisorer og udviklere indsigt i, hvorfor et forslag blev fremsat, og hvordan det udviklede sig.

 #AD.5.1    Niveau: 1    Rolle: D/V
 Bekræft, at prompt-/responspar logges med commit-ID'er.
 #AD.5.2    Niveau: 2    Rolle: D
 Sørg for, at udviklere kan fremvise modellens referencer (træningsudsnit, dokumentation), der understøtter et forslag.
 #AD.5.3    Niveau: 3    Rolle: D/V
 Bekræft, at forklaringsrapporter gemmes sammen med designartefakter og refereres til i sikkerhedsgennemgange, således at de opfylder ISO/IEC 42001 sporbarhedsprincipper.

---

### AD.6 Kontinuerlig feedback og modeljustering

Forbedr modelens sikkerhedsydelse over tid samtidig med at forhindre negativ drift.

 #AD.6.1    Niveau: 1    Rolle: D/V
 Bekræft, at udviklere kan markere usikre eller ikke-overholdende forslag, og at markeringerne bliver registreret.
 #AD.6.2    Niveau: 2    Rolle: D
 Bekræft, at samlet feedback informerer periodisk finjustering eller retrieval-augmenteret generering med gennemgåede sikre-kodingskorpora (f.eks. OWASP Cheat Sheets).
 #AD.6.3    Niveau: 3    Rolle: D/V
 Bekræft, at et lukket system evalueringsværktøj kører regressions tests efter hver finjustering; sikkerhedsmetrikker skal opfylde eller overstige tidligere baselines før implementering.

---

#### Referencer

NIST AI Risk Management Framework 1.0
ISO/IEC 42001:2023 — AI Management Systems Requirements
OWASP Secure Coding Practices — Quick Reference Guide

## Appendiks E: Eksempelværktøjer og -rammer

### Mål

Dette kapitel giver eksempler på værktøjer og frameworks, som kan understøtte implementeringen eller opfyldelsen af et givent AISVS-krav. Disse skal ikke betragtes som anbefalinger eller godkendelser fra AISVS-teamet eller OWASP GenAI Security Project.

---

### AE.1 Træningsdataforvaltning og biasstyring

Værktøjer brugt til dataanalyse, styring og biasstyring.

 #AE.1.1    Afsnit: 1.1
 Værktøjer til datalagerstyring: Værktøjer til styring af datalager som...
 #AE.1.2    Afsnit: 1.2
 Kryptering under overførsel Brug TLS til HTTPS-baserede applikationer, med værktøjer som openSSL og pythons`ssl`bibliotek.

---

### AE.2 Brugervalidering af input

Værktøjer til håndtering og validering af brugerinput.

 #AE.2.1    Afsnit: 2.1
 Prompt Injection Defense Tooling: Brug guardrail-værktøjer som NVIDIA's NeMo eller Guardrails AI.

---

