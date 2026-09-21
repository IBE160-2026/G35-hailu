# Produktbrief — Kitchen Prep

**Produktidé:** An autonomous daily kitchen prep and ordering agent.
**Gruppe:** G35
**Medlem:** Anteneh Hailu
**Status:** Første arbeidsutkast. Produktretningen er valgt; målgruppe, MVP og tekniske valg nedenfor er forslag.

## Sammendrag

Kitchen Prep er en autonom agent som hver dag planlegger kjøkkenforberedelser og varebestilling. Agenten skal bruke tilgjengelig lagerbeholdning, meny og forventet behov til å beregne hva kjøkkenet trenger, lage en prioritert prep-plan og håndtere manglende varer innenfor regler som kjøkkenet har satt.

Målet er at kjøkkenansvarlig starter dagen med en oppdatert plan: hva som må forberedes, i hvilke mengder, og hvilke varer som må bestilles. Den langsiktige løsningen kan sende rutinebestillinger automatisk innenfor godkjente rammer og be om avklaring ved avvik. Første prototype foreslås testet med eksempeldata og simulerte bestillinger.

## Beslutningsgrunnlag

Anteneh har valgt produktretningen «An autonomous daily kitchen prep and ordering agent». Et lite profesjonelt kjøkken foreslås som første målgruppe. Konkrete arbeidsprosesser, datakilder, leverandører og funksjonsgrenser er foreløpig ikke bekreftet. Ingen brukerintervjuer eller integrasjoner er gjennomført som del av dette dokumentet.

## Problemet

**Problemhypotese:** Kjøkkenansvarlige må daglig kombinere meny, forventet antall gjester, lagerstatus og leveringstid for å bestemme prep og innkjøp. Manuelle rutiner kan føre til dobbeltarbeid, manglende ingredienser, for mye prep og unødvendige bestillinger.

Eksempelscenario, ikke observert brukerdata: Kjøkkenet planlegger 40 porsjoner av en rett, men lageret dekker bare 25. Agenten beregner differansen fra oppskriften, foreslår prep for dagens behov og identifiserer varer som må bestilles. Hvis en levering kommer for sent, varsler den om at planen ikke kan gjennomføres som foreslått.

## Løsningen og den daglige arbeidsflyten

1. **Hent grunnlaget:** Dagens meny, forventet antall porsjoner, oppskrifter, brukbar lagerbeholdning, åpne bestillinger og leverandørdata.
2. **Kontroller data:** Identifiser manglende oppskrifter, utdaterte lagerdata, ukjente enheter og uavklarte priser. Vis hvilke deler av planen som blir berørt.
3. **Beregn behov:** Beregn ingrediensbehov, trekk fra brukbart lager og leveranser som ankommer i tide, og sammenlign med eventuelle definerte buffere.
4. **Lag prep-plan:** Foreslå oppgaver, mengder og rekkefølge ut fra rettene som skal produseres. Tidsestimater må komme fra oppgitte data eller merkes som anslag.
5. **Håndter bestillinger:** Beregn manglende varer, rund opp til tilgjengelige pakningsstørrelser og vurder leveringstid og bestillingsgrenser.
6. **Presenter og følg opp:** Vis dagsplan, datagrunnlag, bestillingsstatus og avvik. Registrer ferdigstilt prep og oppdatert lager når brukeren rapporterer det.

Agenten foreslås kjørt automatisk på et konfigurert tidspunkt hver dag. Manuell kjøring skal også være mulig. Tidssone og dagens bestillingsfrist må være eksplisitte.

## Autonomi og bestillingsregler

**Produktmål:** Rutinebestillinger kan sendes automatisk når kjøkkenansvarlig har aktivert dette og satt leverandører, vareutvalg og beløpsgrenser. Avvik som ukjent pris, for sen levering eller overskredet grense skal kreve avklaring.

**Første prototype:** Bruk en simulert leverandør. Agenten oppretter og sender simulerte ordre automatisk innenfor testreglene, uten ekte kjøp. Prototypen skal vise tydelig at ordrene er simulerte.

- Samme daglige kjøring skal ikke opprette samme ordre flere ganger. Hver plan og ordre får en stabil identifikator.
- Ved tidsavbrudd etter sending skal agenten kontrollere eksisterende ordrestatus før eventuell ny sending.
- Endringer i behov etter en sendt ordre skal behandles som en endring som må vurderes, ikke som en ny full bestilling.
- Ordrestatus skal skille mellom utkast, simulert sendt, bekreftet, avvist og ukjent status.
- Ved manglende eller foreldede grunnlagsdata skal berørte automatiske bestillinger stoppes og årsaken vises.
- Agenten skal ikke finne på lagertall, priser, leverandørbekreftelser eller erstatningsvarer.

## Målgruppe

**Foreslått primærbruker:** Kjøkkenansvarlig i en liten restaurant eller kantine som planlegger prep og innkjøp hver dag.

**Foreslått sekundærbruker:** Kjøkkenmedarbeidere som følger prep-planen og registrerer utført arbeid.

Restaurant, kantine eller et annet kjøkkenmiljø må velges sammen med Anteneh før detaljert utforming.

## Hva skiller løsningen fra alternativer?

Forslaget samler behovsberegning, daglig prep og bestillingsoppfølging i én automatisk arbeidsflyt. En vanlig sjekkliste viser oppgaver, mens dette produktet også skal kunne utlede oppgaver og varebehov fra grunnlagsdata. Eksisterende lager- og innkjøpssystemer må undersøkes før det hevdes at løsningen har unike funksjoner.

## Suksesskriterier for prototypen

- Et definert testscenario gir korrekt ingrediensbehov, lagerfradrag og antall bestillingspakker.
- Daglig kjøring produserer én sporbar prep-plan og eventuelle simulerte ordre.
- Gjentatt kjøring med samme grunnlag sender ikke duplikatordre.
- Ukjent lagerstatus, pris eller leveringsdato vises som avvik og hindrer berørte automatiske ordre.
- Et simulert tidsavbrudd etter sending fører til statuskontroll og ikke blind ny bestilling.
- Brukeren kan se hvorfor en vare bestilles, mengden som trengs og hvilken regel som tillot eller stoppet sending.
- Minst to personer i valgt målgruppe prøver prototypen. Opplevd nytte og konkrete problemer dokumenteres.

Dette er foreslåtte akseptansekriterier, ikke oppnådde resultater.

## Omfang for første versjon (MVP)

### Foreslått innhold

- Ett kjøkken og én simulert leverandør.
- Et lite sett med menyretter, oppskrifter og ingredienser.
- Manuell registrering av forventede porsjoner og lagerstatus.
- Definerte enheter, pakningsstørrelser, eksempelpriser og leveringstider.
- Beregning av ingrediensbehov, mangler og bestillingsmengder.
- Daglig planlagt kjøring og manuell kjøring.
- Prep-liste med mengder og status.
- Automatisk simulert bestilling innenfor konfigurerte grenser.
- Oversikt over ordre, avvik og beslutningsgrunnlag.
- Vedvarende lagring av planer, kjøringer og ordreidentifikatorer.

### Utenfor første prototype

- Ekte leverandørbestillinger og betalinger.
- Integrasjon med kassasystem, sensorer eller flere leverandører.
- Automatisk etterspørselsprognose fra historiske salgstall.
- Automatisk valg av erstatningsingredienser.
- Avansert turnus- eller bemanningsplanlegging.
- Dokumentasjon av mattrygghet og allergener eller godkjenning av matens brukbarhet.

## Data og teknisk retning

Foreslåtte datatyper er ingrediens, oppskrift, menyplan, lagerregistrering, leverandørvare, prep-oppgave, agentkjøring og ordre. Alle beregninger må bruke kompatible enheter. Første prototype bør unngå omregning mellom vekt og volum uten eksplisitt omregningsgrunnlag.

Mengde- og kostnadsberegninger bør gjøres med kontrollerbare regler. En språkmodell kan eventuelt brukes til å tolke fritekst og forklare planen, men behovet for en slik modell er ikke besluttet. Teknologistakk, kjøreplattform, lagring og eventuell modellleverandør er fortsatt åpne valg.

## Videre visjon

Etter validering kan agenten kobles til en reell leverandør, få salgstall og forbedre behovsanslag. Automatisk bestilling kan utvides gradvis innenfor uttrykkelig satte grenser. Mål som redusert matsvinn og spart planleggingstid må måles mot en dokumentert utgangssituasjon.

## Åpne spørsmål

- Hvilken type kjøkken skal bruke agenten først?
- Hvilke meny-, oppskrifts- og lagerdata finnes i dag, og hvem oppdaterer dem?
- Når på dagen skal agenten kjøre, i hvilken tidssone og før hvilken bestillingsfrist?
- Hvilke beslutninger skal alltid vurderes av kjøkkenansvarlig?
- Hvilke beløpsgrenser, buffere og leverandørregler er relevante?
- Hvordan skal lageret oppdateres etter prep, levering og registrert svinn?

## Neste steg

Avklar kjøkkentype og lag ett konkret dagscenario med oppskrifter, beholdning, forventede porsjoner og leverandørpakninger. Bruk dette til å validere beregningene og lage en liten ende-til-ende-prototype med simulert bestilling.
