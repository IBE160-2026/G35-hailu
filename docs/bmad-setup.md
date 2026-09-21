# BMAD – oppsett og oppstart for G35

Repoet inneholder BMAD 6.12.0 med BMM og Creative Intelligence Suite. Ferdighetsfilene finnes for både Claude Code og Codex. Konfigurasjonen bruker norsk og prosjektnavnet Kitchen Prep.

## Oppstart

1. Klon repoet og åpne prosjektmappen i verktøyet ditt.
2. Kontroller at Python og `uv` er tilgjengelig dersom en BMAD-arbeidsflyt trenger støtteskriptene.
3. Start en ny samtale fra repoets rot og be om: «Bruk bmad-help. Les productbrief.md og hjelp meg med neste steg.»
4. Bruk `bmad-product-brief` for å videreutvikle Kitchen Prep som autonom daglig prep- og bestillingsagent og avklare målgruppe og MVP.

Ferdighetene er lagt inn i repoet; at verktøyet oppdager dem må kontrolleres i den lokale økten. Start økten på nytt dersom ferdighetene ikke vises.

## Mapper og dokumenter

- `.agents/skills/`: BMAD-ferdigheter for Codex.
- `.claude/skills/`: tilsvarende ferdigheter for Claude Code.
- `_bmad/`: felles konfigurasjon og støtteskript.
- `.docs/planning-artifacts/`: prosjektplanlegging og produktgrunnlag.
- `.docs/implementation-artifacts/`: implementering og testing.
- `productbrief.md`: prosjektets gjeldende arbeidsutkast.
- `product-brief-template.md`: mal for en produktbrief.
- `AGENTS.md` og `CLAUDE.md`: prosjektregler for KI-verktøyene.

Bruk de konfigurerte `.docs/`-mappene til BMAD-output.

## Konfigurasjon

Felles tilpasninger legges i `_bmad/custom/config.toml`. Personlige innstillinger kan legges i `_bmad/custom/config.user.toml`, som er ignorert av Git.

Konfigurasjonen kan kontrolleres fra repoets rot med:

```sh
uv run _bmad/scripts/resolve_config.py --project-root .
```

Ved oppdatering av BMAD bør begge ferdighetsmappene oppdateres sammen. Unngå å blande ulike versjoner.
