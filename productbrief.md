# Produktbrief — Kitchen Prep

**Gruppe:** G35 · **Medlem:** Anteneh Hailu  
**Revidert:** 22.10.2026 etter faglærers tilbakemelding 06.10.2026.  
**Status:** Avgrenset plan for v1; appen er ikke ferdig implementert eller brukervalidert.

## Sammendrag
Kitchen Prep er et regelbasert planleggingsverktøy for kjøkkenansvarlig i en liten kantine med fem faste retter. Brukeren registrerer dagens porsjoner og tilgjengelig lager, trykker «Beregn dagsplan» og får ingrediensbehov, mangler, prep-liste og et bestillingsforslag. Forslaget må godkjennes av brukeren og merkes «Simulert – ingen bestilling sendes».

## Beslutningsgrunnlag og målgruppe
Førsteversjonen avgrenses til ett fiktivt demonstrasjonskjøkken, «Demokantinen», med én bruker: kjøkkenansvarlig. Fem retter: kylling med ris, grønnsaksris, tomatpasta, linsesuppe og potetomelett. Dette er prosjektvalg for en håndterbar prototype, ikke opplysninger fra en faktisk kunde. Problem og nytte er hypoteser. Ingen brukerintervjuer, målinger eller godkjenning fra faglærer på denne revisjonen foreligger.

## Problemet
Kjøkkenansvarlig må kombinere porsjonsplan, oppskrifter og lager for å finne hva som kan tilberedes og hva som mangler. Manuell sammenstilling kan gi feil mengder og unødvendige innkjøp. Prototypen skal gjøre beregningen forståelig og kontrollerbar. Den skal ikke avgjøre mattrygghet eller allergener.

## Morgenflyt og brukeropplevelse
1. Åpne dagsplan og velg dato. Se at dataene er eksempeldata.
2. Velg retter og legg inn hele, ikke-negative porsjonstall.
3. Kontroller lagerbeholdningen og rett feil.
4. Trykk «Beregn dagsplan».
5. Se behov, tilgjengelig lager, mangel og pakker per ingrediens, samt prep-oppgaver per rett.
6. Ved mangel vises «Mangler råvarer – full plan kan ikke gjennomføres med dagens lager». Et bestillingsforslag betyr ikke at varene allerede finnes.
7. Godkjenn eller avvis det simulerte bestillingsforslaget. Godkjenning sender ingenting og øker ikke lageret.
8. Marker prep-oppgaver ferdige. Dette er oppgavestatus og trekker ikke automatisk råvarer fra lager i v1.

Dagsplanen skal ha stor lesbar tekst, tydelige knapper, skjemaetiketter, tastaturnavigasjon og feil som forklarer hva brukeren må rette. Visningen planlegges for nettbrett og PC, med enkel mobiltilpasning. Første skisse: øverst dato og porsjoner, deretter «Beregn dagsplan», så mangler, prep-liste og bestillingsforslag.

## Omfang for v1
- Ett kjøkken, én lokal bruker og fem faste oppskrifter.
- Manuell porsjons- og lagerregistrering med eksempeldata.
- Manuell beregning av samlet ingrediensbehov og lagerfradrag.
- Én simulert leverandør og faste pakningsstørrelser.
- Prep-liste med mengder og status «Ikke ferdig»/«Ferdig».
- Bestillingsforslag med «Utkast», «Godkjent simulering» eller «Avvist».
- Lokal lagring av dagsplan og oppgavestatus; gjenåpning skal bevare data.
- Ny beregning etter endret grunnlag erstatter utkastet og krever ny godkjenning.

### Utenfor v1
Automatisk daglig kjøring, bakgrunnsjobber, ordresending, leverandørbekreftelser, tidsavbrudd etter sending, full ordrestatus, innlogging og flere roller. Heller ikke betaling, kasseintegrasjon, prognoser, flere leverandører, automatisk lagerforbruk, svinnsystem, buffere, priser, beløpsgrenser eller leveringsberegning inngår. Varer i bestillingsforslag teller aldri som tilgjengelig lager.

## Hva betyr KI og agent?
V1 bruker en deterministisk regelmotor, uten språkmodell i appen. «Autonom agent» beholdes som langsiktig visjon, ikke som beskrivelse av v1. KI brukes som utviklingsstøtte til planlegging, kode og gjennomgang. Prompts, vurderinger og faktiske rettinger skal lagres med kobling til konkrete krav og endringer. En språkmodell som forklarer planen kan vurderes senere; den er ikke et krav til v1.

## Beregningsregler
For hver ingrediens summeres oppskriftsmengde per porsjon × porsjoner over alle valgte retter.
- Mangel = maks(0, samlet behov − registrert tilgjengelig lager).
- Antall pakker = rund opp(mangel / pakningsstørrelse).
- Foreslått bestillingsmengde = antall pakker × pakningsstørrelse.
- Vekt normaliseres til gram, volum til milliliter og antall til stykk. Ikke konverter mellom vekt, volum og stykk.
- Lager og oppskriftsmengder må være ikke-negative; pakningsstørrelse må være større enn null.
- Ukjent ingrediens, manglende oppskrift, ugyldig tall eller uforenlig enhet stopper berørt beregning med tydelig feil. Ikke vis et ufullstendig forslag som komplett.
- Alle mengder kommer fra registrerte data; systemet skal aldri finne på lagertall.

## Konkret dagscenario med håndregnet fasit
Dette er syntetiske testdata, ikke observerte kundedata. Dagen har 40 porsjoner kylling med ris og 20 porsjoner grønnsaksris; de andre tre rettene har 0 porsjoner.

| Rett | Ingredienser per porsjon |
|---|---|
| Kylling med ris | 150 g kylling, 75 g tørr ris, 100 g grønnsaker |
| Grønnsaksris | 75 g tørr ris, 200 g grønnsaker |

| Ingrediens | Behov | Lager | Mangel | Pakningsstørrelse | Pakker | Forslag |
|---|---:|---:|---:|---:|---:|---:|
| Kylling | 6 000 g | 3 750 g | 2 250 g | 1 000 g | 3 | 3 000 g |
| Ris | 4 500 g | 2 000 g | 2 500 g | 2 000 g | 2 | 4 000 g |
| Grønnsaker | 8 000 g | 5 000 g | 3 000 g | 2 500 g | 2 | 5 000 g |

Kontroll: kylling = 40 × 150 = 6 000 g; lageret dekker 25 porsjoner. Ris = (40 + 20) × 75 = 4 500 g. Grønnsaker = 40 × 100 + 20 × 200 = 8 000 g.
Prep-listen viser planlagt produksjon av de to rettene med disse råvaremengdene og et synlig mangelvarsel. Full produksjon krever at manglene faktisk dekkes; simulert godkjenning endrer ikke dette.

## Testbare suksesskriterier
K1: Dagscenarioet gir nøyaktig tallene over, inkludert summering av felles ingredienser.
K2: Lager lik eller større enn behov gir null mangel og null pakker.
K3: Eksakt én pakke i mangel gir én pakke; mangel litt over gir to.
K4: Negative verdier, desimale porsjoner, ugyldige tall, null pakningsstørrelse og uforenlige enheter avvises.
K5: Gjentatt beregning med samme grunnlag gir samme resultat og sender ingen ordre.
K6: Endret grunnlag krever ny beregning og godkjenning; godkjenning endrer ikke lageret.
K7: Dagsplan og prep-status bevares når appen lukkes og åpnes igjen.
K8: Sensor kan starte og teste lokalt etter README uten nøkler eller betalte kontoer.
K9: Manuell sjekk dokumenterer tastaturbruk, nettbrettvisning, tom plan og forståelige feilmeldinger.

Kriteriene er krav til kommende implementering, ikke beståtte tester. Tilbakemelding fra brukere ønskes senere og dokumenteres bare dersom testing faktisk gjennomføres.

## Teknisk retning og dokumentstruktur
Foreslått stakk til PRD/arkitektur: Python, Streamlit, SQLite og pytest. Dette er et forslag, ikke en allerede implementert løsning. Lokal kjøring og én bruker begrenser oppsettet; ingen køer eller bakgrunnstjenester trengs. Beregningslogikk skilles fra grensesnitt og lagring.

Denne rotfilen beholdes som produktbrief fordi AGENTS.md peker hit. Øvrige planleggingsdokumenter samles i `.docs/planning-artifacts/`; implementering, testplaner og faktiske testresultater i `.docs/implementation-artifacts/`; syntetiske eksempeldata i `data/examples/`; varig oppstartsveiledning i `docs/`. Mappene beskriver planlagt struktur, ikke ferdig innhold. Hemmeligheter og lokale databaser skal holdes utenfor Git.

## Hva skiller løsningen fra alternativer?
Den samler beregning, prep-liste og forklaring av bestillingsmengder i én enkel dagsflyt. Det hevdes ikke at funksjonene er unike. Konkurrentanalyse og måling av tidsbesparelse er ikke gjennomført.

## Videre visjon
Etter stabil og testet v1 kan faktisk brukerbehov avgjøre om KI-forklaring, lagerbevegelser, prognoser og ekte leverandørintegrasjon skal prioriteres. Automatisk bestilling krever en egen senere avgrensning.

## Neste steg og prosess
1. Gå gjennom de dokumenterte avgrensningene og foreslått teknologistakk.
2. Lag PRD med krav-ID-er K1–K9, deretter arkitektur og små stories.
3. Implementer og test beregningene mot håndregnet fasit før resten av flyten.
4. Oppdater README med faktisk installasjon, versjoner, oppstart og testkommandoer når appen finnes.
5. Dokumenter reelle prompts, feil, avviste KI-forslag og verifikasjon fortløpende. Ingen historikk eller tidligere resultater skal rekonstrueres som om de allerede forelå.

## Revisjon etter tilbakemelding
- Målgruppe: valgt én liten demokantine og én kjøkkenansvarlig.
- Omfang: redusert til manuell kjerneflyt; agent- og ordresendingskrav flyttet ut.
- KI: eksplisitt regelmotor i v1; KI som utviklingsstøtte.
- Datagrunnlag: lagt inn dagscenario med felles ingredienser og håndregnet fasit.
- UX, testkrav og dokumentplassering: konkretisert.
Revisjonen er utarbeidet med ChatGPT/Codex som KI-støtte på brukerens oppdrag. Faglærers opprinnelige tilbakemelding beholdes uendret i `tilbakemelding-product-brief.md`.
