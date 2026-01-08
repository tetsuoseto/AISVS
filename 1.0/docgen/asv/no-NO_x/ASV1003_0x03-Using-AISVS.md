# Ved bruk av AISVS

Standard for sikkerhetsverifisering av kunstig intelligens (AISVS) definerer sikkerhetskrav for moderne AI-applikasjoner og -tjenester, med fokus på aspekter som er innenfor kontrollen til applikasjonsutviklere.

AISVS er ment for alle som utvikler eller vurderer sikkerheten til AI-applikasjoner, inkludert utviklere, arkitekter, sikkerhetsingeniører og revisorer. Dette kapitlet introduserer strukturen og bruken av AISVS, inkludert dets verifiseringsnivåer og tiltenkte brukstilfeller.

## Sikkerhetsverifiseringsnivåer for kunstig intelligens

AISVS definerer tre stigende nivåer av sikkerhetsverifisering. Hvert nivå tilfører dybde og kompleksitet, noe som gjør det mulig for organisasjoner å tilpasse sin sikkerhetsstilling til risikonivået for sine AI-systemer.

Organisasjoner kan begynne på nivå 1 og gradvis ta i bruk høyere nivåer etter hvert som sikkerhetsmodenhet og trusseleksponering øker.

### Definisjon av nivåene

Hvert krav i AISVS v1.0 er tildelt ett av følgende nivåer:

#### Krav for nivå 1

Nivå 1 inkluderer de mest kritiske og grunnleggende sikkerhetskravene. Disse fokuserer på å forhindre vanlige angrep som ikke er avhengig av andre forutsetninger eller sårbarheter. De fleste kontroller på Nivå 1 er enten enkle å implementere eller viktige nok til å rettferdiggjøre innsatsen.

#### Nivå 2 krav

Nivå 2 håndterer mer avanserte eller mindre vanlige angrep, samt lagdelte forsvar mot utbredte trusler. Disse kravene kan innebære mer kompleks logikk eller målrette spesifikke angrepsforutsetninger.

#### Krav for nivå 3

Nivå 3 inkluderer kontroller som vanligvis er vanskeligere å implementere eller situasjonsavhengige i anvendelse. Disse representerer ofte forsvar-i-dybden-mekanismer eller tiltak mot nisje-, målrettede eller høyt komplekse angrep.

### Rolle (D/V)

Hvert AISVS-krav er merket i henhold til hovedmålgruppen:

* D – Utviklerfokuserte krav
* V – Krav fokusert på verifiserer/revisor
* D/V – Relevant for både utviklere og verifikatorer

