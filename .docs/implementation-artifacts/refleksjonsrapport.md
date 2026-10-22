# Refleksjonsrapport - Programmering med KI

> **Arbeidsutkast – ikke innleveringsklart.** Rapporten følger den utdelte malen. Den beskriver dokumentert planleggingsarbeid fram til 22.10.2026. Implementering, applikasjonstester og brukerundersøkelser er ikke dokumentert i dette arbeidet. Drøftingene er skrevet med KI-støtte. Personlige avsnitt er bearbeidet fra Antenehs egne opplysninger om kjøkkenerfaring, arbeid med tall, nytte av KI og utfordringer med GitHub og KI-forslag. Resterende utfyllingsfelt gjelder opplysninger eller erfaringer som ennå ikke foreligger. Rapporten skal senere utvides med konkrete hendelser fra utviklingen, ikke med konstruerte resultater.

## 1. Gruppeinformasjon

**Gruppenavn:** G35 – Kitchen Prep

**Gruppemedlemmer:**
- Anteneh Hailu – **[Student-ID eller skole-e-post]**

**Dato:** 22.10.2026

---

## 2. Utviklingsprosessen

### 2.1 Oversikt over prosjektet

Jeg valgte Kitchen Prep fordi jeg har jobbet på kjøkken og kjenner arbeidsområdet fra praksis. Kjøkkenarbeid innebærer både praktiske oppgaver og mye arbeid med tall og planlegging. Derfor ønsket jeg å undersøke hvordan et digitalt verktøy kan støtte sammenhengen mellom porsjoner, råvarer og organisering av arbeidet.

Kitchen Prep er et planlagt verktøy for kjøkkenansvarlig i en liten kantine. Hovedmålet er å gjøre det enklere å lage en dagsplan ved å kombinere planlagte porsjoner, oppskrifter og registrert lager. Førsteversjonen er avgrenset til fem faste retter og én lokal bruker. Brukeren skal starte beregningen manuelt og få oversikt over ingrediensbehov, mangler, prep-oppgaver og bestillingsforslag. Godkjenning av et forslag er en simulering og skal ikke sende en faktisk bestilling.

Den opprinnelige produktbriefen beskrev en mer autonom agent med daglig automatisk kjøring og mer omfattende ordrehåndtering. Faglæreren vurderte dette som for stort for førsteversjonen og ba om en tydeligere målgruppe. Briefen ble derfor revidert. Det er den avgrensede løsningen som er grunnlaget for videre arbeid.

Et viktig skille er at KI brukes i utviklingsprosessen, mens selve appen i v1 skal bruke faste beregningsregler. En språkmodell trenger ikke beregne hvor mange pakker ris som mangler. Slike beregninger kan kontrolleres direkte med en håndregnet fasit.

### 2.2 Arbeidsmetodikk

Prosjektet har ett registrert medlem. Oppgavefordeling mellom flere studenter er derfor ikke relevant i det dokumenterte arbeidet. GitHub brukes til å lagre prosjektfiler og endringshistorikk. Dette gir mulighet til å sammenligne tidligere og nyere versjoner og vise hvordan tilbakemeldinger påvirker planen.

Jeg brukte ChatGPT/Codex til å gjennomgå sensorveiledningen og faglærerens tilbakemelding sammen med produktbriefen, README og prosjektreglene. Jeg fikk hjelp til å revidere produktbriefen og README på grunnlag av tilbakemeldingen. Endringene ble lagret på main, og den opprinnelige tilbakemeldingen ble beholdt.

Arbeidsformen viser både en mulighet og en begrensning. KI kan raskt sammenholde flere dokumenter og foreslå en helhetlig revisjon. Samtidig må jeg kontrollere forslagene og forstå valgene. Avgrensningen til en demokantine og fem retter kom fram med KI-støtte og er foreløpig et utgangspunkt for prototypen. Den er ikke testet mot en virkelig kunde.

BMAD finnes i prosjektoppsettet. Det er likevel ikke dokumentert her at hele BMAD-flyten er gjennomført. Neste planlagte steg er kravspesifikasjon, arkitektur og avgrensede utviklingsoppgaver.

Jeg har brukt kjøkkenerfaringen min som utgangspunkt for ideen. KI har hjulpet meg med å tenke utenfor det jeg allerede kjenner, og gjort arbeidet med å utvikle ideen lettere. Samtidig har både GitHub og forståelsen av enkelte KI-forslag vært utfordrende. Jeg trenger derfor en arbeidsmåte der endringer forklares konkret og kan knyttes til en oppgave fra kjøkkenet. Jeg vil også dokumentere verktøybruken videre i prosjektet.

### 2.3 Teknologi og verktøy

| Område | Dokumentert bruk eller status |
|---|---|
| Frontend | Streamlit er foreslått; implementering er ikke dokumentert her. |
| Backend/beregningslogikk | Python er foreslått; beregningsmodul er ikke dokumentert her. |
| Database | SQLite er foreslått for lokal lagring. |
| Testing | pytest er foreslått; ingen applikasjonstester er kjørt i denne revisjonen. |
| KI-verktøy | Jeg brukte ChatGPT/Codex til dokumentgjennomgang, revisjon og språklig bearbeiding av rapporten. Tidligere KI-bruk må beskrives mer konkret før innlevering. |
| Andre verktøy | GitHub til dokumenter og versjonshistorikk; BMAD er konfigurert i repoet. |

Teknologiforslagene er valgt med tanke på en liten lokal prototype uten betalte tjenester. De må vurderes i arkitekturarbeidet. Tabellen skiller mellom det som faktisk er brukt i denne økten og det som bare er planlagt.

### 2.4 Utviklingsfaser

**Fase 1: Planlegging**

Det forelå en produktbrief med ideen om en autonom kjøkkenagent. Faglærerens tilbakemelding fra 06.10.2026 fremhevet konkrete og kontrollerbare beregninger som en styrke. Den pekte samtidig på uavklart målgruppe, for stort MVP-omfang og uklart formål med KI i appen.

Den dokumenterte revisjonen 22.10.2026 besto av disse stegene:

1. Jeg delte sensorveiledningen for del 1 og ba om hjelp til å bruke den sammen med faglærerens tilbakemelding.
2. Jeg brukte ChatGPT/Codex til å sammenholde veiledningen og tilbakemeldingen med prosjektet.
3. Gjennomgangen tok utgangspunkt i produktbriefen, README og prosjektreglene.
4. Jeg fikk forslag til en mer avgrenset og konkret prosjektbeskrivelse.
5. Målgruppen ble avgrenset til kjøkkenansvarlig i én liten demokantine.
6. Automatisk kjøring og avansert ordrehåndtering ble flyttet ut av v1.
7. Det ble presisert at beregninger skal være regelbaserte.
8. Et syntetisk dagscenario med håndregnet fasit ble lagt inn.
9. Testbare kriterier K1–K9 ble formulert.
10. Produktbriefen ble lagret i commit bd2030bf597b4cd6fdd53dddd3abfe4278a3a6b2.
11. README ble oppdatert i commit edc42aadd48146067b46299d33942996fb58a4f5.
12. Produktbriefen ble hentet på nytt for å kontrollere at den lagrede teksten var oppdatert.

Dette er stegene som kan dokumenteres fra den aktuelle økten. Listen er ikke en påstand om å dekke alle tidligere aktiviteter i prosjektet.

**Fase 2: Utvikling**

Implementeringen av den avgrensede v1 er ikke dokumentert i denne rapportversjonen. Det er derfor ikke grunnlag for å beskrive en ferdig app, feilsøking av programkode eller beståtte tester. Neste fase skal bygge beregningslogikk før brukergrensesnitt og lagring kobles sammen.

Hver gjennomført utviklingsoppgave bør senere dokumenteres med krav, faktisk prompt eller et merket sammendrag, endret kode, kontroll og resultat. Dersom KI gir et feil forslag, bør både feilen og rettingen forklares. Jeg vil forklare hvordan jeg brukte KI og kontrollerte forslagene, framfor bare å skrive at KI hjalp med kode.

**Gjenstår etter utviklingen:** konkrete oppgaver, kodeendringer, commit-lenker, testkommandoer, faktiske feil og mine vurderinger.

---

## 3. Utfordringer og løsninger

### 3.1 Tekniske utfordringer

De følgende utfordringene gjelder foreløpig krav og løsningsdesign, ikke observerte feil i en kjørende app.

**Utfordring 1: For stort omfang**

- **Problem:** Første brief kombinerte behovsberegning med automatisk kjøring, beskyttelse mot duplikatordre og håndtering av tidsavbrudd. Det økte antallet tilstander og feil som måtte håndteres.
- **Løsning:** V1 ble redusert til manuell kjøring og simulerte bestillingsforslag med brukergodkjenning.
- **KI sin rolle:** Jeg fikk KI-hjelp til å omskrive briefen etter lærerens anbefaling. Omfangsreduksjonen bygger på tilbakemeldingen og er ikke et selvstendig funn fra KI.

Avgrensningen gjør det mulig å prioritere en sammenhengende kjerneflyt. Den fjerner også behovet for å undersøke om en ordre allerede har kommet fram etter et nettverksbrudd. Dette er fortsatt relevant for en framtidig løsning, men trenger ikke løses i den første prototypen.

**Utfordring 2: Beregninger som kan kontrolleres**

- **Problem:** Flere retter kan bruke samme ingrediens, og pakningsstørrelser gjør at bestillingsmengden blir større enn mangelen.
- **Løsning:** Briefen beskriver summering per ingrediens, lagerfradrag og avrunding opp til hele pakker.
- **KI sin rolle:** Jeg fikk KI-hjelp til å formulere regler og et scenario med håndregnet fasit. Dette er testgrunnlag, ikke en gjennomført programvaretest.

For eksempel gir 40 porsjoner kyllingrett og 20 porsjoner grønnsaksris et samlet risbehov på 4500 gram. Med 2000 gram på lager mangler 2500 gram. Pakker på 2000 gram gir et forslag på to pakker. Eksempelet viser hvorfor behov, mangel og bestillingsmengde må presenteres som ulike størrelser.

**Utfordring 3: Forslag må ikke forveksles med lager**

- **Problem:** En godkjent simulering kan misforstås som om varene er levert.
- **Løsning:** Briefen krever at godkjenning ikke øker lageret, og at mangler fortsatt vises.
- **KI sin rolle:** Jeg fikk KI-hjelp til å tydeliggjøre skillet i regler og brukerflyt.

**Gjenstår:** minst to konkrete tekniske hendelser fra implementeringen, med feilårsak, løsning og kontroll av resultatet.

### 3.2 Samarbeidsutfordringer

Jeg arbeider alene i prosjektet og har derfor ikke arbeidsfordeling eller gruppemøter å beskrive. En relevant utfordring i et soloprosjekt er at den samme personen både spesifiserer og kontrollerer løsningen.

Faglærerens tilbakemelding gir et eksternt perspektiv på omfang og gjennomførbarhet. KI kan også foreslå alternative løsninger, men er ikke en uavhengig bekreftelse på at et forslag er riktig. Jeg trenger egne kontroller og etter hvert faktiske brukerobservasjoner.

For meg har utfordringene særlig handlet om de digitale verktøyene og om å forstå forslagene fra KI. Jeg kjenner kjøkkenarbeidet, men det er ikke alltid enkelt å oversette behovene til en teknisk beskrivelse. Faglærerens skriftlige tilbakemelding og KI-assistansen har vært støtte i det dokumenterte planleggingsarbeidet. Det er ikke beskrevet ytterligere samarbeid eller tilbakemeldinger fra andre personer her.

### 3.3 KI-spesifikke utfordringer

Jeg har opplevd at enkelte forslag fra KI er vanskelige å forstå. Når et forslag inneholder flere tekniske begreper eller funksjoner samtidig, blir det krevende å vurdere hvordan det passer til ideen min. Derfor er det viktig for mitt videre arbeid at forslag forklares med enkle ord og konkrete eksempler. Jeg må kunne se hvilken oppgave på kjøkkenet forslaget skal løse.

En sentral risiko er at KI fyller inn uavklarte deler med plausible detaljer. I dette prosjektet gjelder det blant annet kjøkkentype, meny, teknologistakk og antatt nytte. Revidert brief markerer derfor demodata som syntetiske og teknologistakken som foreslått.

En annen risiko er at velformulert dokumentasjon gir inntrykk av større framdrift enn det finnes bevis for. Testkriterier er ikke testresultater, og en gjennomarbeidet plan er ikke en kjørbar applikasjon. Rapporten må opprettholde dette skillet også når teksten skrives med KI.

---

## 4. Kritisk vurdering av KI sin påvirkning

### 4.1 Fordeler med KI-assistanse

**Effektivitet og produktivitet:**

Jeg opplever at KI har gjort arbeidet lettere og hjulpet meg med å tenke utenfor mine egne første ideer. Det har vært nyttig å kunne ta utgangspunkt i et område jeg kjenner, kjøkkenarbeid, og få hjelp til å strukturere en mulig digital løsning. Dette er min opplevelse av støtten, ikke en målt tidsbesparelse.

Med hjelp fra KI fikk jeg sammenholdt lærerens kommentarer med produktbriefen og revidert flere deler av dokumentasjonen i samme arbeidsøkt. Den konkrete nytten var en mer samlet revisjon: målgruppe, omfang, beregningsregler og README ble tilpasset samme retning.

Tidsbruk er ikke målt. Det er derfor ikke grunnlag for å oppgi en prosentvis effektivitetsgevinst. Rask produksjon av tekst må dessuten vurderes sammen med tiden jeg trenger for å forstå og kontrollere innholdet.

**Læring og forståelse:**

Dagscenarioet gir et konkret grunnlag for å diskutere forskjellen mellom behov og innkjøp. Kravene til enheter viser også at programmet må forstå hva tall representerer. To tall kan ikke summeres bare fordi begge er numeriske.

For meg gjør koblingen til kjøkkenarbeid tallene relevante. Et konkret eksempel er at 40 porsjoner med 150 gram kylling krever 6000 gram. Hvis lageret inneholder 3750 gram, mangler 2250 gram. Jeg kan bruke dette eksempelet fra produktbriefen til å kontrollere beregningene når modulen er laget. Foreløpig er det et planlagt kontrollgrunnlag.

**Kvalitet på koden:**

Kodekvalitet kan ennå ikke vurderes ut fra denne revisjonen. KI har foreløpig bidratt til et tydeligere grunnlag for kommende kode: mindre omfang, eksplisitte regler og testbare krav. Om det gir bedre kode, må vurderes etter implementering og kontroll.

### 4.2 Begrensninger og ulemper

**Kvalitet og pålitelighet:**

Den opprinnelige planen var mer omfattende enn det faglæreren anbefalte. Dette viser at en detaljert plan kan være lite realistisk. Dokumentasjonen alene viser imidlertid ikke hvem som foreslo hver tidligere funksjon, så ansvaret for det opprinnelige omfanget kan ikke tilskrives KI uten mer informasjon.

Jeg må også gjennomgå valgene i den reviderte planen. Fem retter er valgt, men det detaljerte dagscenarioet dekker bare to. Det er et godt beregningseksempel, men ikke et komplett datasett for hele appen. Oppskriftene for resten må spesifiseres før implementeringen kan regnes som fullstendig.

**Avhengighet og forståelse:**

Når KI både foreslår og lagrer endringer, kan jeg bli for passiv i arbeidet. Risikoen reduseres ved å forklare sentrale regler selv og sammenligne forslag med konkrete krav. Jeg bør for eksempel kunne forklare hvorfor en godkjenning ikke betyr at lageret øker.

Mitt utgangspunkt er erfaring med kjøkkenarbeid, tall og hvordan arbeidet organiseres. Både GitHub og noen av KI-forslagene har vært vanskelige. Det betyr at jeg ikke kan vurdere alle tekniske forslag bare fordi de virker godt forklart i teksten. Jeg trenger å knytte dem til konkrete eksempler og få forklart hva de innebærer. Jeg har foreløpig ikke dokumentert et konkret KI-forslag som jeg avviste. Dette vil jeg følge opp i det videre arbeidet.

**Kreativitet og problemløsning:**

KI har hjulpet meg med å tenke utenfor de første ideene mine. Dette har gjort det lettere å se muligheter for hvordan kjøkkenerfaring kan brukes i et digitalt prosjekt. Samtidig må nye muligheter vurderes mot hva jeg kan forstå, kontrollere og gjennomføre i oppgaven.

Avgrensningen kan oppleves som mindre spennende enn en autonom agent. Samtidig kan en liten løsning gjøre det lettere å undersøke brukerbehov før nye funksjoner legges til. KI bør brukes til å utforske alternativer, mens valget begrunnes ut fra oppgaven og tilgjengelig tid.

### 4.3 Sammenligning: Med og uten KI

Uten KI måtte dokumentgjennomgangen og omskrivingen vært gjort manuelt. Da måtte jeg ha arbeidet mer direkte med hver formulering. Med KI ble en samlet revidert versjon produsert raskt, men behovet for faglig kontroll forsvant ikke.

Beregningene kan utføres uten KI. Det kan derfor være nyttig å løse scenarioet manuelt før koden vurderes. Den manuelle fasiten blir et kontrollgrunnlag som ikke avhenger av at samme KI vurderer sitt eget forslag.

Dette er en begrunnet sammenligning, ikke et eksperiment. Det er ikke gjennomført to parallelle prosjekter med og uten KI. Rapporten kan derfor ikke slå fast at sluttresultatet ville vært bedre eller dårligere uten assistanse.

### 4.4 Samlet vurdering

På dette stadiet har KI bidratt til mer konkret planlegging og tydeligere dokumentasjon av endringer. Den samlede påvirkningen på appens funksjonalitet og kodekvalitet er foreløpig uavklart.

En foreløpig lærdom er at verdien av KI avhenger av tydelige rammer og etterprøvbare kontroller. Faglærerens tilbakemelding ga retning, mens scenarioet gir et kontrollgrunnlag for videre utvikling. Min foreløpige vurdering er at KI har vært nyttig fordi det har gjort arbeidet lettere og gitt meg flere perspektiver. Samtidig viser utfordringene med GitHub og KI-forslag at jeg fortsatt trenger å utvikle den tekniske forståelsen min. Vurderingen gjelder planleggingsarbeidet så langt.

---

## 5. Etiske implikasjoner

### 5.1 Ansvar og eierskap

Jeg har ansvar for det jeg leverer, også når jeg har fått KI-hjelp med dokumentasjon eller kode. Ansvar innebærer å kunne forklare sentrale valg og å opplyse om begrensninger. En formulering som «KI sa at det var riktig» er ikke tilstrekkelig kvalitetssikring.

For Kitchen Prep betyr dette blant annet at mengder må kontrolleres, at simulering merkes tydelig, og at appen ikke framstilles som et system for mattrygghet. Dersom feil beregninger senere påvirker innkjøp, kan det gi praktiske og økonomiske konsekvenser.

Opphavsrett og eierskap må også tas på alvor. KI-generert innhold bør ikke automatisk behandles som kontrollert og fritt for tredjepartsrettigheter. Ved bruk av biblioteker, maler og gjenbrukt kode må relevante vilkår undersøkes og kreditering beholdes. Denne rapporten gir ikke en juridisk avklaring av eierskap.

### 5.2 Transparens

Jeg har brukt ChatGPT/Codex til å gjennomgå dokumenter, foreslå avgrensninger og bearbeide tekst. Det gjelder også denne rapporten. Mine erfaringer med kjøkkenarbeid, tall, GitHub og KI er utgangspunktet for de personlige avsnittene. Jeg må selv lese gjennom teksten og stå inne for vurderingene før innlevering.

Transparens handler ikke bare om å navngi et verktøy. Det bør framgå hva verktøyet gjorde, hvilke forslag som ble vurdert og hvordan resultatet ble kontrollert. Dokumentasjon av en konkret omfangsreduksjon er mer informativt enn en generell erklæring om KI-bruk.

Manglende åpenhet kan gjøre det vanskelig å skille mine vurderinger fra generert tekst. Det kan også svekke troverdigheten dersom rapporten hevder aktiviteter som ikke kan finnes i historikken. Derfor skal manglende erfaringer markeres og senere fylles inn.

### 5.3 Påvirkning på læring og kompetanse

KI kan gi forklaringer og eksempler som støtter læring. Samtidig kan jeg gå glipp av øvelse i å bryte ned problemer dersom verktøyet alltid lager planen først. Det gjelder også feilsøking og forståelse av sammenhengen mellom datamodell og brukergrensesnitt.

En praktisk balanse er å formulere forventet resultat før KI får implementere. Jeg kan for eksempel beregne risbehovet selv, skrive ned forventningen og deretter undersøke om programmet gir samme svar. Da blir KI et hjelpemiddel i arbeidet, mens kontrollen forblir faglig forankret.

I den dokumenterte økten ba jeg KI bruke lærerens tilbakemelding til å rette produktbriefen. Resultatet var en tydeligere beskrivelse av én målgruppe og et mindre omfang. Dette er et konkret eksempel på hvordan KI hjalp meg med å bearbeide prosjektideen. Jeg har særlig strevd med GitHub og med å forstå enkelte KI-forslag. Konkrete erfaringer fra feilsøking vil jeg legge til når implementeringen er i gang.

### 5.4 Arbeidsmarkedet

KI kan endre hvilke oppgaver utviklere bruker tid på. Dersom utkast til kode og dokumentasjon blir enklere å produsere, kan forståelse av krav, testing og vedlikehold få større betydning. Dette er en refleksjon om mulige endringer, ikke en dokumentert prognose.

Kitchen Prep illustrerer betydningen av domeneforståelse. Det er nødvendig å skille mellom planlagt forbruk, faktisk lager og foreslått bestilling. En teknisk løsning kan være ryddig skrevet og likevel støtte en dårlig arbeidsprosess.

Kitchen Prep gir meg mulighet til å knytte kjøkkenerfaringen min til det jeg arbeider med i IT-studiet. Jeg er opptatt av tall og hvordan arbeidet kan organiseres. Prosjektet er derfor en anledning til å undersøke hvordan teknologi kan støtte praktiske arbeidsoppgaver. Det er foreløpig ikke grunnlag for å beskrive dette som en ferdig forretningsidé eller en bestemt karrierebeslutning.

### 5.5 Datasikkerhet og personvern

I denne arbeidsøkten ble sensorveiledningen og relevante prosjektfiler brukt som grunnlag for KI-assistanse. Dagscenarioet i revisjonen er syntetisk. Det er ikke grunnlag for å beskrive all tidligere datadeling i prosjektet uten at jeg først går gjennom hva jeg har delt.

Ved senere bruk av reelle kjøkkendata må behovet for deling vurderes. Oppskrifter, priser, leverandøravtaler og driftsopplysninger kan være sensitive selv uten personopplysninger. Navn på ansatte og kundedata bør ikke følge med bare fordi de finnes i en eksport.

API-nøkler og passord skal ikke legges i repoet eller i prompts. Før materiale deles, bør jeg undersøke hva det inneholder og dele minst mulig. Offentlig prosessdokumentasjon bør bruke relevante utdrag, ikke komplette private samtaler.

---

## 6. Teknologiske implikasjoner

### 6.1 Kodekvalitet og vedlikehold

Langsiktig vedlikehold krever at programmet er forståelig for andre enn den som genererte det. KI kan produsere mye kode raskt, men mengde er ikke et kvalitetsmål. En liten modul med tydelige innganger og resultater kan være enklere å kontrollere enn en stor sammenhengende fil.

For Kitchen Prep er det planlagt å skille beregning fra brukergrensesnitt og lagring. Da kan beregningsreglene testes uten å åpne appen. En endring i presentasjonen trenger heller ikke endre hvordan mangel beregnes.

Ved feilsøking bør jeg følge dataene gjennom systemet. Hvis antall pakker er feil, må det undersøkes om feilen kommer fra oppskrift, enhet, lager eller avrunding. Å be KI «fikse alt» kan gi en endring som skjuler symptomet uten å forklare årsaken.

### 6.2 Standarder og beste praksis

Det er ikke dokumentert konkrete utdaterte kodeforslag i denne revisjonen. Rapporten skal derfor ikke konstruere et eksempel bare fordi malen spør etter det. Etter implementering bør faktiske forslag vurderes opp mot prosjektets krav og valgt teknologi.

De viktigste planlagte kontrollene er validering av tall og enheter, tester av sentral logikk og en README som stemmer med en ren lokal oppstart. Kvalitetssikringen bør også omfatte hva brukeren ser ved feil. En korrekt beregning hjelper lite dersom mangler skjules eller godkjenning framstår som ekte levering.

Et annet relevant prinsipp er sporbarhet. Krav K1–K9 bør kunne kobles til kode og tester. Koblingen gjør det lettere å oppdage krav som bare finnes i dokumentasjonen. Den gir også et bedre grunnlag for å vurdere når en oppgave faktisk er ferdig.

### 6.3 Fremtidig utvikling

KI kan bli en vanlig del av utviklingsarbeidet, men behovet for vurdering og kontroll består. Utviklere må kunne formulere presise oppgaver, vurdere alternativer og undersøke om resultatet passer den faktiske brukssituasjonen.

For dette prosjektet bør videre arbeid skje i små trinn. Først kommer beregningene med håndregnet fasit. Deretter kan brukerflyt og lagring legges til. En eventuell KI-forklaring av planen bør vurderes etter at kjernen er stabil, og forklaringen må bygge på beregnede data.

En framtidig autonom bestillingsfunksjon vil kreve en ny vurdering av ansvar, bekreftelser og feiltilstander. At slike funksjoner er utsatt, betyr ikke at de er uviktige. Det betyr at førsteversjonen må gi et troverdig grunnlag før mer ansvar overlates til systemet.

---

## 7. Konklusjon og læring

### 7.1 Viktigste lærdommer

Ut fra planleggingsarbeidet så langt ser jeg disse foreløpige lærdommene:

1. En tydelig målgruppe gjør det enklere å avgjøre hvilke funksjoner førsteversjonen trenger.
2. Redusert omfang kan gi bedre mulighet til å ferdigstille en sammenhengende kjerneflyt.
3. KI i utviklingen trenger ikke bety at appen skal inneholde en språkmodell.
4. Håndregnede eksempler gir et konkret kontrollgrunnlag for KI-generert kode.
5. Sporbare endringer og ærlig status er viktigere enn å framstille planen som ferdig arbeid.

### 7.2 Hva ville dere gjort annerledes?

Et mulig forbedringspunkt er å avgrense kjøkkentype og dagscenario tidligere. Da kunne omfanget vært vurdert før avansert agent- og ordrehåndtering ble skrevet inn. Det ville også gjort kravene mer konkrete fra starten.

Teknologivalg bør begrunnes etter at kjerneflyten er avklart. Det er foreløpig ikke dokumentert en sammenligning som viser at den foreslåtte stakken er best. En slik beslutning bør ta hensyn til læringsbehov, lokal kjøring og hvor lett løsningen er å teste.

Jeg vil dele opp KI-arbeidet slik at jeg kan vurdere ett hovedvalg om gangen. Det bør være tydelig hvilke forslag som ble godtatt og hvorfor. Dette er en arbeidsmåte jeg ønsker å følge videre.

Med utgangspunkt i utfordringene jeg har beskrevet, vil jeg i videre arbeid be om enklere forklaringer og mindre oppgaver om gangen. For GitHub vil jeg prioritere å forstå hva som er endret og hvor endringen er lagret. For KI-forslag vil jeg prioritere å forstå hva forslaget skal løse før jeg går videre. Dette er planlagte forbedringer i arbeidsmåten min.

### 7.3 Anbefalinger

Start med et problem som kan beskrives gjennom en konkret arbeidsdag. Lag et lite eksempel med forventet resultat før du ber KI skrive kode. Be deretter om avgrensede endringer og kontroller at løsningen faktisk følger reglene.

Lagre relevante prompts og vurderinger underveis. Ikke vent til slutten med å rekonstruere prosessen. Skill mellom det du planlegger, det du har implementert og det du har kontrollert. Dette gjør både egen læring og senere vurdering mer etterprøvbar.

Bruk tilbakemeldinger til å endre planen, og dokumenter endringen. Unngå å legge til funksjoner bare fordi KI enkelt kan beskrive dem. En funksjon gir også arbeid med data, feiltilstander, tester og forklaring til brukeren.

### 7.4 Personlig refleksjon (individuelt)

**Anteneh Hailu:**

Jeg valgte Kitchen Prep fordi jeg har jobbet på kjøkken og kjenner dette arbeidsområdet. Jeg ønsket å bruke erfaringen min til et prosjekt med en praktisk hensikt. Kjøkkenarbeid handler også om tall: hvor mange porsjoner som skal lages, hvor mye råvarer som trengs, og hvordan oppgavene skal organiseres. Dette gjorde temaet relevant for meg.

KI har hjulpet meg med å tenke utenfor mine egne første ideer. Det har gjort det lettere å utvikle ideen videre og få en mer strukturert beskrivelse av hva løsningen kan gjøre. Jeg opplever at KI gjør det enklere å komme videre når jeg har en praktisk idé, men trenger hjelp til å beskrive den som et digitalt prosjekt.

Samtidig har både GitHub og enkelte forslag fra KI vært utfordrende. Jeg kjenner kjøkkenarbeidet bedre enn de tekniske verktøyene. Derfor er det ikke nok for meg å få et ferdig forslag; jeg trenger også å forstå hvordan det henger sammen med det jeg ønsker å lage. En god forklaring bør bruke konkrete eksempler fra kjøkkenet og vise hva en endring betyr.

Dagscenarioet i produktbriefen er et slikt eksempel. Det knytter porsjoner til mengder, lager og bestillingspakker. Denne typen eksempler er relevant for meg fordi den gjør sammenhengen mellom tall og praktisk arbeid synlig. Framover vil jeg bruke slike eksempler til å kontrollere om løsningen følger de reglene vi har beskrevet.

Jeg ønsker å bli tryggere på å bruke GitHub og på å vurdere KI-forslag. Målet mitt er å forstå mer av arbeidet, slik at jeg kan ta bedre valg underveis. KI har vært en nyttig støtte så langt, men jeg må fortsatt utvikle min egen tekniske forståelse. Denne refleksjonen gjelder planleggingsfasen. Erfaringer med kode, feilretting og tester må legges til når det arbeidet faktisk er gjennomført.

---

## 8. Vedlegg (valgfritt)

### Prosjekt og dokumenterte endringer

- [GitHub-repo](https://github.com/IBE160-2026/G35-hailu)
- [Gjeldende produktbrief](../../productbrief.md)
- [Faglærers tilbakemelding](../../tilbakemelding-product-brief.md)
- [Revisjon av produktbrief](https://github.com/IBE160-2026/G35-hailu/commit/bd2030bf597b4cd6fdd53dddd3abfe4278a3a6b2)
- [Oppdatering av README](https://github.com/IBE160-2026/G35-hailu/commit/edc42aadd48146067b46299d33942996fb58a4f5)

### Prompts fra den synlige arbeidsøkten

Her er noen av beskjedene jeg ga til ChatGPT/Codex:
- «les den tilbake melding og rett opp i forhold til og de tilbake melding han har gitt meg»
- «har vi tatt med tilbakemeldingen også»
- «har du oppdartert»
- «la oss gjøre del 2 og følge den malen»

Dette er et utvalg av beskjedene mine, ikke en komplett KI-logg. De viser hva jeg ba om hjelp til, og hvordan jeg fulgte opp arbeidet.

### Grunnlag for refleksjonen

Refleksjonen bygger på kjøkkenerfaringen min, arbeidet med tall og planlegging, og utfordringene mine med GitHub og enkelte KI-forslag. Jeg har fått KI-hjelp til å strukturere og formulere teksten. Beregningseksemplene kommer fra produktbriefens syntetiske scenario og er foreløpig grunnlag for planlagte tester.

### Kilder og avgrensninger

Strukturen følger den utdelte reflection-report-template.md. Sensorveiledning IBE160 – Del 1 applikasjon og prosess, høst 2026, er brukt som bakgrunn for koblingen mellom prosess, testing og dokumentasjon. Detaljerte vurderingskriterier for del 2 er ikke levert her; del 1-veiledningen erstatter ikke disse.

Ingen skjermbilder av en ferdig app eller rapporter om gjennomførte applikasjonstester inngår i dette utkastet. Det finnes heller ikke dokumenterte intervjuer eller målinger av tidsbesparelse i grunnlaget som er brukt.

### Før innlevering

- Fyll inn student-ID eller skole-e-post, og les gjennom vurderingene og den personlige refleksjonen.
- Utvid utviklingsfasen med det som faktisk gjennomføres.
- Legg til reelle tekniske utfordringer og dokumenterte kontroller.
- Gjennomgå KI-formuleringene og sørg for at refleksjonen uttrykker egne vurderinger.
- Kontroller eventuelle særkrav til del 2, lengde og kildebruk.
- Oppdater dato og ordantall, og fjern arbeidsutkastmarkeringen først når innholdet er ferdig.

---

**Ordantall:** Omtrent 4327 ord i arbeidsutkastet, inkludert tabeller og vedlegg.

**Forventet lengde i malen:** 3000–5000 ord, avhengig av gruppestørrelse og prosjektets kompleksitet. Endelig ordantall må kontrolleres etter at egne erfaringer og faktiske utviklingsresultater er innarbeidet.
