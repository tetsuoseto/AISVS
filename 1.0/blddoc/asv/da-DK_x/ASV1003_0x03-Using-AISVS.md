# Brug af AISVS

Den kunstige intelligens sikkerhedsverifikationsstandard (AISVS) definerer sikkerhedskrav for moderne AI-applikationer og -tjenester med fokus på aspekter, der ligger inden for applikationsudvikleres kontrol.

AISVS er beregnet til alle, der udvikler eller vurderer sikkerheden af AI-applikationer, herunder udviklere, arkitekter, sikkerhedsingeniører og revisorer. Dette kapitel introducerer strukturen og brugen af AISVS, herunder dets verifikationsniveauer og tilsigtede anvendelsestilfælde.

## Sikkerhedsgodkendelsesniveauer for kunstig intelligens

AISVS definerer tre stigende niveauer af sikkerhedsverifikation. Hvert niveau tilføjer dybde og kompleksitet, hvilket giver organisationer mulighed for at tilpasse deres sikkerhedsposition til risikoniveauet for deres AI-systemer.

Organisationer kan starte på Niveau 1 og gradvist adoptere højere niveauer, efterhånden som sikkerhedsmodenhed og trusselsniveau stiger.

### Definition af niveauerne

Hvert krav i AISVS v1.0 tildeles et af følgende niveauer:

#### Niveau 1 krav

Niveau 1 omfatter de mest kritiske og grundlæggende sikkerhedskrav. Disse fokuserer på at forhindre almindelige angreb, som ikke er afhængige af andre forudsætninger eller sårbarheder. De fleste kontrolforanstaltninger på Niveau 1 er enten enkle at implementere eller så væsentlige, at de retfærdiggør indsatsen.

#### Krav på niveau 2

Niveau 2 omhandler mere avancerede eller mindre almindelige angreb samt lagdelte forsvar mod udbredte trusler. Disse krav kan involvere mere kompleks logik eller målrette specifikke forudsætninger for angreb.

#### Krav for niveau 3

Niveau 3 inkluderer kontroller, der typisk er sværere at implementere eller anvendelige i særlige situationer. Disse repræsenterer ofte forsvar-i-dybden mekanismer eller afbødning mod nicheprægede, målrettede eller høj-kompleksitetsangreb.

### Rolle (D/V)

Hvert AISVS-krav er markeret i henhold til den primære målgruppe:

* D – Udviklerfokuserede krav
* V – Krav med fokus på verificer/auditor
* D/V – Relevant for både udviklere og verificatorer

