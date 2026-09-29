# Product Brief – FreightLens AI

## 1. Produktoversikt

**FreightLens AI** er en applikasjon for analyse og kvalitetssikring av fraktdata. Løsningen skal hjelpe brukere som arbeider med logistikk, transport, innkjøp eller økonomi med å importere fraktfiler, standardisere data fra ulike transportører og få en rask oversikt over kostnader, datakvalitet og mulige avvik.

Bakgrunnen for prosjektet er at fraktdata ofte kommer fra forskjellige transportører og systemer, med ulike kolonnenavn, filstrukturer og formater. Dette gjør manuell kontroll og sammenligning tidkrevende. En transportør kan for eksempel bruke kolonnenavnet `AWB`, mens en annen bruker `Shipment ID` for samme type informasjon. Tilsvarende kan vekt, fraktkostnad, land og dato være navngitt forskjellig.

FreightLens AI skal redusere dette problemet ved å kombinere tradisjonell programmering og databehandling med kunstig intelligens. Programmet skal ikke erstatte faglig vurdering, men fungere som et støtteverktøy som gjør det enklere å finne feil, avvik og interessante mønstre i dataene.

---

## 2. Problemstilling

Hvordan kan kunstig intelligens og programmering brukes til å gjøre import, standardisering og analyse av fraktdata enklere og mer effektivt?

I mange virksomheter må fraktdata behandles manuelt før de kan analyseres. Dersom filene kommer fra flere transportører, kan brukeren måtte:

- identifisere hvilke kolonner som tilsvarer hverandre
- rydde opp i manglende eller feil formaterte verdier
- beregne nøkkeltall manuelt
- lete etter uvanlig høye kostnader eller andre avvik
- lage en egen oppsummering av resultatene

FreightLens AI skal samle disse stegene i én applikasjon.

---

## 3. Målgruppe

Primær målgruppe er personer som arbeider med:

- logistikk og transport
- eksport og import
- innkjøp
- fraktkostnader
- økonomi og controlling

I prosjektet utvikles løsningen som en prototype, og målgruppen brukes først og fremst for å definere realistiske brukerbehov og arbeidsflyt.

---

## 4. Mål for produktet

Målet med FreightLens AI er å utvikle en fungerende applikasjon hvor brukeren kan laste opp fraktdata og få en standardisert og forståelig analyse uten å måtte behandle hele datasettet manuelt.

Første versjon skal kunne:

1. lese inn en CSV- eller Excel-fil
2. identifisere relevante kolonner
3. foreslå mapping mellom ukjente kolonnenavn og et standardisert datasett
4. validere og rydde data
5. beregne relevante nøkkeltall
6. identifisere mulige kostnads- eller datakvalitetsavvik
7. presentere resultatene i et enkelt dashboard
8. lage en kort AI-generert oppsummering av analysen

---

## 5. Kjernefunksjoner

### 5.1 Filopplasting

Brukeren skal kunne laste opp en fraktfil i CSV- eller Excel-format. Systemet leser filen og viser en forhåndsvisning av dataene.

Eksempler på data som kan finnes i filen:

- sending-/AWB-nummer
- transportør
- destinasjonsland
- vekt
- fraktkostnad
- forsendelsesdato

Applikasjonen skal kontrollere at filen kan leses og gi en forståelig feilmelding dersom formatet ikke støttes.

### 5.2 AI-basert kolonnemapping

En sentral KI-funksjon i prosjektet er automatisk forslag til mapping av kolonner.

Eksempel:

| Opplastet kolonne | Standardisert felt |
| --- | --- |
| AWB | Shipment ID |
| Country | Destination |
| KG | Weight |
| Net Charge | Freight Cost |
| Supplier | Carrier |
| Pickup | Shipment Date |

KI skal foreslå hvordan ukjente kolonner bør tolkes. Brukeren skal kunne kontrollere og eventuelt endre forslaget før dataene behandles videre.

Dette gjør systemet mer fleksibelt enn en løsning som kun fungerer dersom alle filer har identiske kolonnenavn.

### 5.3 Datavalidering

Etter at kolonnene er standardisert skal programmet kontrollere datakvaliteten.

Eksempler på kontroller:

- manglende verdier
- negative eller ugyldige kostnader
- ugyldige datoer
- manglende vekt
- duplikate sendinger
- ukjente eller manglende land

Feil og mangler skal vises i en egen oversikt slik at brukeren kan se hvilke rader som bør undersøkes.

### 5.4 Analyse og nøkkeltall

Programmet skal beregne enkle nøkkeltall som gjør datasettet lettere å forstå.

Aktuelle nøkkeltall er:

- totalt antall sendinger
- samlet fraktkostnad
- gjennomsnittlig fraktkostnad
- samlet vekt
- gjennomsnittlig kostnad per kg
- kostnad fordelt på transportør
- kostnad fordelt på destinasjonsland

Resultatene skal presenteres i et oversiktlig dashboard med tabeller og enkle grafer.

### 5.5 Avviksanalyse

FreightLens AI skal forsøke å identifisere sendinger som skiller seg tydelig fra resten av datasettet.

Et eksempel kan være en sending som har vesentlig høyere kostnad per kg enn andre sendinger til samme land.

I første versjon kan avviksanalysen baseres på enkle statistiske regler og terskelverdier. KI kan deretter brukes til å forklare resultatet på et mer forståelig språk.

Et eksempel på output kan være:

> Sending 10482 har betydelig høyere kostnad per kg enn gjennomsnittet for tilsvarende sendinger til Tyskland. Sendingen bør undersøkes nærmere.

Dette er et forslag til videre kontroll, ikke en automatisk konklusjon om at sendingen er feil.

### 5.6 AI-oppsummering

Når analysen er fullført skal brukeren kunne generere en kort oppsummering.

Oppsummeringen kan for eksempel beskrive:

- hvor mange sendinger som er analysert
- totale kostnader
- viktigste transportører eller destinasjoner
- antall datakvalitetsproblemer
- hvilke avvik som bør undersøkes

Målet er at en bruker raskt skal kunne forstå hovedfunnene uten å lese hele datasettet.

---

## 6. Brukerflyt

En typisk brukerflyt i FreightLens AI vil være:

1. Brukeren åpner applikasjonen.
2. Brukeren laster opp en CSV- eller Excel-fil.
3. Programmet leser filen og viser en forhåndsvisning.
4. KI foreslår mapping av kolonnene.
5. Brukeren godkjenner eller endrer mappingen.
6. Programmet standardiserer og validerer dataene.
7. Dashboardet viser nøkkeltall, datakvalitet og mulige avvik.
8. Brukeren kan generere en AI-oppsummering.
9. Resultatene kan eventuelt eksporteres som en rapport eller ny datafil.

---

## 7. Teknisk plan

Applikasjonen planlegges utviklet i Python.

Aktuelle teknologier og biblioteker:

- **Python** – hovedspråk
- **pandas** – behandling og analyse av data
- **Streamlit** – brukergrensesnitt
- **openpyxl** – lesing og skriving av Excel-filer
- **matplotlib eller Plotly** – visualisering
- **LLM/API** – KI-funksjoner for kolonnemapping og tekstlig oppsummering

Programmet bør bygges modulært slik at filbehandling, datavalidering, analyse og KI-funksjoner er separert i egne funksjoner eller moduler.

Dette gjør programmet lettere å teste og videreutvikle.

---

## 8. Avgrensning – MVP

Prosjektet skal utvikles som en **Minimum Viable Product (MVP)**. Målet er å få en stabil og demonstrerbar løsning fremfor å implementere alle mulige funksjoner.

Første versjon skal derfor begrenses til:

- CSV- og Excel-filer
- et definert sett med standardfelt
- grunnleggende datavalidering
- enkle nøkkeltall
- enkel avviksanalyse
- AI-basert kolonnemapping
- AI-generert oppsummering
- lokalt eller enkelt webbasert brukergrensesnitt

Følgende funksjoner er utenfor første versjon:

- direkte integrasjon mot DHL, Bring, DSV eller andre transportører
- automatisk fakturakontroll mot transportøravtaler
- tollberegning
- juridisk vurdering av eksportregler
- automatiske HS-kodebeslutninger
- full brukeradministrasjon
- avansert maskinlæring
- ERP-integrasjoner
- sanntidsdata fra transportører

Disse funksjonene kan vurderes ved eventuell videreutvikling.

---

## 9. Bruk av kunstig intelligens

KI skal være en integrert del av produktet, men brukes der teknologien gir en tydelig fordel.

Tradisjonell programmering brukes til oppgaver hvor resultatet skal være forutsigbart og kontrollerbart, for eksempel:

- filinnlesing
- beregninger
- datavalidering
- statistikk
- filtrering
- visualisering

KI brukes til oppgaver som krever tolkning av tekst eller kontekst, for eksempel:

- forstå ukjente kolonnenavn
- foreslå kolonnemapping
- forklare mulige avvik
- lage en menneskelig lesbar oppsummering

Denne kombinasjonen gjør det mulig å vise forskjellen mellom deterministisk programmering og KI-baserte funksjoner.

---

## 10. Risiko og utfordringer

En utfordring er at fraktfiler kan ha svært forskjellig struktur. Det er derfor viktig at første versjon ikke forsøker å støtte alle mulige formater.

En annen utfordring er at KI kan gi feil forslag. Derfor skal brukeren kunne kontrollere forslag til kolonnemapping før de brukes.

Andre mulige utfordringer er:

- manglende data
- feil datatyper
- store variasjoner mellom datasett
- API-kostnader eller begrensninger
- håndtering av sensitive eller konfidensielle data

Prosjektet skal derfor bruke testdata eller anonymiserte data under utvikling og demonstrasjon.

---

## 11. Suksesskriterier

Prosjektet regnes som vellykket dersom vi har en fungerende prototype hvor en bruker kan:

- laste opp et realistisk fraktdatasett
- få kolonnene tolket og standardisert
- se datakvalitetsproblemer
- se relevante nøkkeltall
- identifisere minst én type avvik
- få en forståelig AI-generert oppsummering

I tillegg skal løsningen ha et ryddig brukergrensesnitt og være enkel å demonstrere.

---

## 12. Mulig videreutvikling

Dersom prosjektet videreutvikles etter første versjon kan FreightLens AI blant annet utvides med:

- støtte for flere transportørformater
- automatisk analyse av fraktfakturaer
- sammenligning av transportører
- kostnadsprognoser
- historisk utvikling
- transportørspesifikke regler
- automatisk rapportgenerering
- integrasjon mot ERP- eller TMS-systemer
- brukerinnlogging og lagrede analyser
- mer avansert avviksdeteksjon

På lengre sikt kan løsningen utvikles fra en skoleprototype til et mer komplett analyseverktøy for frakt og logistikk.
