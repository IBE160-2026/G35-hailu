# G35 — Kitchen Prep

Gruppeprosjekt i **IBE160 Programmering med KI**, Høgskolen i Molde, høsten 2026 (15 studiepoeng).
**Medlem:** Anteneh Hailu.

## Formål og status
Kitchen Prep planlegges som et regelbasert verktøy for kjøkkenansvarlig i en liten kantine med fem faste retter. Førsteversjonen skal ha manuell behovsberegning, prep-liste og bestillingsforslag som brukeren godkjenner som simulering. Ingen ordre sendes.

**Planleggingsfase:** Produktbriefen er revidert 22.10.2026 etter faglærers tilbakemelding. Denne revisjonen leverer dokumentasjon, ikke en kjørbar applikasjon. Installasjons-, oppstarts- og testkommandoer for appen foreligger derfor ikke ennå. Teknologistakken er foreslått, ikke ferdig implementert.

## Dokumentasjon
- [Produktbrief med avgrensning, dagscenario og krav K1–K9](productbrief.md).
- [Faglærers opprinnelige tilbakemelding](tilbakemelding-product-brief.md).
- [BMAD – oppsett og oppstart](docs/bmad-setup.md).
- [Prosjektregler](AGENTS.md).
- [Produktbrief-mal](product-brief-template.md) – referansemal, ikke prosjektets gjeldende brief.

Produktbriefen beholdes i roten slik AGENTS.md angir. Øvrig planlegging legges i `.docs/planning-artifacts/`, implementeringsdokumentasjon og testresultater i `.docs/implementation-artifacts/`, syntetiske eksempeldata i `data/examples/` og varig prosjektveiledning i `docs/`. Dette er også planlagt plassering for innhold som ennå ikke finnes.

## KI og prosess
V1 planlegges uten språkmodell i appen. KI brukes til utviklingsstøtte. Beregninger skal følge kontrollerbare regler. Revisjonen av brief og README er gjort med ChatGPT/Codex på brukerens oppdrag. Brukerintervjuer, implementering og beståtte applikasjonstester er ikke gjennomført som del av denne revisjonen.

## Neste steg
Lag PRD fra briefen, avklar foreslått teknologistakk, og lag arkitektur og små stories. Implementer beregningene først og test mot dagscenarioet. Dokumenter faktiske prompts, beslutninger og kontroller fortløpende. Legg inn presise kommandoer for installasjon, oppstart og testing når appen er implementert.

BMAD er konfigurert i `_bmad/`, med ferdigheter i `.agents/skills/` og `.claude/skills/`. Forslag til neste oppgave:

```text
Bruk bmad-help. Les AGENTS.md, productbrief.md og tilbakemelding-product-brief.md.
Lag neste planleggingssteg fra den reviderte briefen. Behold v1-avgrensningen,
skill forslag fra beslutninger og ikke påstå at tester eller brukerintervjuer er gjennomført.
```
