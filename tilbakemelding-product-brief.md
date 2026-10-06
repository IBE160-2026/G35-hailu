# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G35 – G35-hailu |
| **Product brief** | `productbrief.md` (commit `9fccd3f`) |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

Vurdert fil: `productbrief.md` i repoets rot. `product-brief-template.md` er den uendrede malen og er ikke vurdert. Det finnes ennå ikke PRD, arkitektur eller epics.

## Samlet vurdering

- **Bør revideres før dere går videre.** Rett punktene markert «Endre» før dere lager PRD og arkitektur.

**Det som er bra:**

1. Kjerneberegningen er konkret og kontrollerbar. Eksempelet med 40 planlagte porsjoner der lageret dekker 25, og trinnene «beregn behov → trekk fra lager → rund opp til pakningsstørrelse», gir regler som kan regnes for hånd og testes.
2. Dere er bevisste på risiko: simulert leverandør i stedet for ekte kjøp, «agenten skal ikke finne på lagertall, priser eller leverandørbekreftelser», og beregninger med kontrollerbare regler i stedet for språkmodell. Det er gode valg.

**De viktigste endringene:**

1. Velg målgruppe og ett konkret kjøkken. Briefen sier selv at kjøkkentype, datakilder og arbeidsprosesser ikke er bekreftet, og listen med åpne spørsmål er lang. Bestem for eksempel «kjøkkenansvarlig i en liten kantine med fem faste retter», og lag dagscenarioet som neste steg i briefen nevner. Uten dette blir PRD-en bygget på antakelser.
2. Reduser omfanget av «agent»-delen i v1. MVP-en har ti punkter, og flere av dem er teknisk krevende: daglig planlagt kjøring, beskyttelse mot duplikatordre, statuskontroll etter tidsavbrudd og en ordrestatus med fem tilstander. Mot en simulert leverandør gir dette mye arbeid for lite synlig nytte. Start med manuell kjøring, behovsberegning, prep-liste og bestillingsforslag som brukeren godkjenner.
3. Avklar hva KI gjør i appen. Briefen kaller produktet en «autonom agent», men all beregning skal være regelbasert, og om en språkmodell skal brukes «er ikke besluttet». Bestem om appen skal ha en KI-funksjon (for eksempel å forklare planen eller tolke en meny i fritekst), eller om «agent» betyr automatisert regelmotor. Begge deler er greit, men det må være tydelig.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Middels**

**Sammenlignbart med:** En avgrenset del av 4) KI-støttet MRP II, nærmere bestemt 4.4) BOM og 4.5) MRP (vanskelig), med oppskrift som stykkliste på ett nivå og én leverandør. Fordi det er ett nivå, ett kjøkken og ingen prognoser, havner v1 på middels. Med daglig automatisk kjøring, idempotente ordre og håndtering av tidsavbrudd nærmer det seg vanskelig.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | Middels til høy | Behov fra oppskrift × porsjoner, lagerfradrag, leveranser som kommer i tide, buffere, pakningsstørrelser, bestillingsgrenser og enheter. Hver regel er enkel, men mange må stemme sammen. |
| Datamodell – antall entiteter og relasjoner mellom dem | Høy | Ingrediens, oppskrift, menyplan, lagerregistrering, leverandørvare, prep-oppgave, agentkjøring og ordre: åtte entiteter med mange relasjoner. |
| Brukere, roller og innlogging | Lav til middels | Kjøkkenansvarlig og medarbeider er nevnt. I v1 holder det med én bruker. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | Lav | Ikke besluttet. Slik briefen står, er det ingen KI-funksjon i selve appen. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | Lav | Leverandøren er simulert. Ekte bestilling og kassasystem er utelatt. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | Middels | Planlagt daglig kjøring, gjentatte kjøringer og tidsavbrudd krever bakgrunnsjobber og tilstandshåndtering. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | Lav | Ingen filhåndtering er beskrevet. |
| Sikkerhet og personvern | Lav | Ingen personopplysninger. Simulerte ordre må merkes tydelig, slik briefen sier. |

**Hva vanskelighetsgraden betyr for dere:**

- _Middels:_ Et godt balansert valg. Pass på at kjerneflyten blir ferdig og stabil før dere legger til mer. Her er kjerneflyten: legg inn meny og porsjoner, se beregnet behov og mangler, få en prep-liste og et bestillingsforslag med begrunnelse.

### Gjennomførbarhet med BMAD og Claude Code

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | Stor risiko | Ti MVP-punkter og åtte entiteter er mye for én person i ett semester. Med reduserte agent-krav er det realistisk. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | Risiko | Arbeidsflyten er godt beskrevet, men målgruppen og datagrunnlaget er uavklart. Det gir mange stories og fare for at KI fyller hullene. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | Risiko | CRUD og beregninger er godt egnet. Planlagte bakgrunnsjobber og idempotens er vanskeligere og krever mer oppsett. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | OK | Beregningene er aritmetikk som kan sjekkes for hånd, særlig når dagscenarioet er laget. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | OK | Suksesskriteriene (korrekt behov, lagerfradrag, antall pakker, ingen duplikatordre) egner seg godt som tester. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | OK | Simulert leverandør og eksempeldata gjør dette enkelt. Planlagt kjøring må kunne utløses manuelt for sensor. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | OK | Ingen betalte tjenester er nødvendige. Hvis dere legger til en språkmodell, trenger dere en plan for nøkkel og testmodus. |

**Konklusjon om gjennomførbarhet:**

- **Gjennomførbart med justert omfang.** Se forslagene under.

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. V1: ett kjøkken, 3–5 retter, manuell kjøring, behovsberegning med pakningsstørrelser, prep-liste og bestillingsforslag som brukeren godkjenner. Flytt automatisk daglig kjøring, håndtering av tidsavbrudd og full ordrestatus til et senere trinn.
2. Hvis dere vil ha en tydelig KI-funksjon, legg til én avgrenset funksjon, for eksempel at en språkmodell forklarer dagens plan med enkle ord, eller tolker en meny skrevet i fritekst til retter og porsjoner som brukeren bekrefter. Beregningene skal fortsatt være regelbaserte.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | OK | Sammendraget forklarer tydelig hva appen gjør: dagsplan for prep og bestilling ut fra meny, lager og behov. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | Juster | Problemet er en hypotese uten observerte brukere, slik dere selv skriver. Snakk gjerne med en kjøkkenansvarlig, eller lag et realistisk scenario fra et kjøkken dere kjenner. |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | Juster | Seks trinn beskriver arbeidsflyten godt, men mye handler om datakontroll og ordrehåndtering. Beskriv også hva kjøkkenansvarlig ser og gjør om morgenen. |
| What Makes This Different – er vurderingen ærlig og realistisk? | OK | Ærlig: eksisterende systemer må undersøkes før dere hevder noe unikt. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | Endre | Primærbrukeren er bare «foreslått», og kjøkkentype skal velges senere. Bestem dette nå. |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | OK | Konkrete og testbare kriterier, særlig korrekt behov og antall pakker i et definert testscenario. |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | Endre | Tydelig inn/ut-liste, men innholdet i v1 er for stort. Reduser som foreslått over. |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | OK | Ekte leverandør, salgstall og bedre anslag er tydelig lagt etter v1. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | Juster | Arbeidsflyten og kriteriene gir godt grunnlag, men målgruppe og dagscenario må på plass før PRD. Lagre promptene fra arbeidet videre. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | Endre | For stort for v1. En kjerneflyt med beregning, prep-liste og bestillingsforslag gir nok funksjonalitet. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | OK | Beregningsreglene egner seg svært godt for tester med håndregnet fasit. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | Juster | Dagsplan og bestillingsoversikt er lette å se for seg, men tenk på bruk i et travelt kjøkken (stor skrift, nettbrett?). Skisser dagsplanen. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | Juster | Teknologi er ikke valgt ennå. Unngå bakgrunnstjenester og køer i v1 hvis manuell kjøring holder. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | OK | Simulert leverandør og eksempeldata gjør appen kjørbar for sensor. Legg med eksempeldataene i repoet. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Juster | Repoet har allerede `.docs/planning-artifacts`, men briefen ligger i roten. Bestem én plass for planleggingsdokumentene og en egen mappe for eksempeldata. |

## 3. Neste steg for gruppen

1. Bestem kjøkkentype og primærbruker, og lag ett konkret dagscenario med retter, oppskrifter, lager, porsjoner og pakningsstørrelser, med håndregnet fasit.
2. Reduser v1 til manuell kjøring, behovsberegning, prep-liste og godkjente bestillingsforslag. Flytt resten av agent-funksjonene til et senere trinn.
3. Bestem om og hvordan KI skal brukes i appen, og oppdater briefen før dere lager PRD.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
