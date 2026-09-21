# G35 — Kitchen Prep

Gruppeprosjekt i **IBE160 Programmering med KI** ved Høgskolen i Molde, høsten 2026 (15 studiepoeng).

Repoet inneholder gruppens applikasjon og dokumentasjon av utvikling, testing og kvalitetssikring med KI.

## Medlemmer

- anteneh hailu

## Prosjektoppsett

- `_bmad/`: BMAD-rammeverk for planlegging, utvikling og kvalitetssikring.
- `.agents/skills/`: BMAD-ferdigheter for Codex.
- `AGENTS.md`: prosjektregler for Codex og andre KI-verktøy.
- `.claude/skills/`: BMAD-ferdigheter for Claude Code.
- `.docs/planning-artifacts/`: produktbeskrivelse og prosjektplanlegging.
- `.docs/implementation-artifacts/`: dokumentasjon av implementering og testing.

BMAD er konfigurert for Anteneh og prosjektet **Kitchen Prep**, med norsk som arbeids- og dokumentspråk. **Kitchen Prep er en autonom agent for daglig kjøkkenprep og varebestilling.** Agenten skal bruke meny, forventet behov og lagerstatus til å lage prep-planer og håndtere varebehov. Produktbriefen foreslår en første prototype med simulerte bestillinger.


## Produktbrief og oppstart

- [Produktbrief](productbrief.md): arbeidsutkast for Kitchen Prep; målgruppe og MVP er forslag.
- [Produktbrief-mal](product-brief-template.md).
- [BMAD – oppsett og oppstart](docs/bmad-setup.md).
- [Prosjektregler](AGENTS.md).

BMAD-ferdighetene finnes for både Codex (`.agents/skills/`) og Claude Code (`.claude/skills/`).

## Kom i gang med Codex

Åpne dette repoet som prosjekt i Codex. BMAD-ferdighetene ligger i `.agents/skills/`. Start med:

```text
Bruk bmad-help. Les productbrief.md og hjelp meg med neste steg for Kitchen Prep.
```

Se [oppstartsveiledningen](docs/bmad-setup.md) og [OpenAIs dokumentasjon om ferdigheter](https://developers.openai.com/codex/skills).
