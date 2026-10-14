# 2026-10-15: Bootstrap

Projektets Claude-uppsättning skapades med `bakjob-surdeg:bootstrap` (v0.6.0)
efter en intervju. Svaren nedan är grunden för hur uppsättningen ser ut;
`feed` utgår från dem om något ska ändras.

| Område | Val |
|---|---|
| Namn | portfolio website |
| Pitch | En hemsida som fungerar som mitt portfolio, med länkar och coola saker överallt. Spel och andra hemsidor läggs in och länkas efter hand. |
| Mapp | `D:\PROG-PROJEKT\portfolio-website` |
| Typ | Webbplats (portfolio) |
| Team | Bara jag |
| Läge | Helt nytt |
| Ramverk | Astro |
| Pakethanterare | pnpm |
| Typning | Strikt TypeScript |
| Sidfamiljer | Ja (projektsidor) |
| Språk: kod | Engelska |
| Språk: docs | Svenska |
| Språk: UI | Engelska |
| Språk: commits | Engelska |
| Chattspråk | Svenska |
| Tankstreck | Regeln behålls |
| Kodstil | Mallens clean code-standard |
| Git-värd | GitHub, `Bakjob/portfolio-website` (publikt) |
| Brancher | Feature-branch + PR |
| Merge | Alltid jag |
| Autonomi | Claude committar, pushar och öppnar PR själv |
| Commit-stil | Fritt men tydligt |
| PR-titlar | Gitmoji + issue-ID |
| LFS | Nej |
| Testbranch | Nej (bara jag) |
| Tracker | GitHub Issues |
| Flöde | Enkelt: issue stängs vid merge (`Closes #N`) |
| Omfattning | Allt arbete |
| Checklista | I PR-beskrivningen |
| Tester | Bygg + lint + typecheck |
| Formatter-hook | Ja (Prettier) |
| CI | GitHub Actions på varje PR |
| Smoke test | Inte än |
| Vault | Full, `vault/` |
| Extramappar | `design/` |
| Obsidian | Nej |
| Säga emot | Flagga tydliga problem |
| Frågeformat | I terminalen |
| Behörigheter | Generöst |
| Deploy | Vercel, ingen egen domän än |
| Kvalitetsribba | Lighthouse 90+ och WCAG 2.2 AA |
| Plugins | `bakjob-core`, `bakjob-github`, `bakjob-web` |
| Install mode | Plugins (projekt-scope) |

## Gjort

- `CLAUDE.md`, vaulten, `hard-rules.md`, `running.md`, `quality-targets.md`,
  `design/page-families.md`.
- `.claude/settings.json`: plugins, marknadsplatsen `bakjob`, behörigheter,
  Prettier-hook.
- `.gitignore`, `.github/workflows/ci.yml`.
- Labels `in progress` och `in review` skapade på GitHub.
- `git init`, första commit, push till `main`.

## Medvetet utelämnat

- Ingen Astro-kod: skapas i första PR:en.
- Smoke test: läggs till när sajten finns (se `status/open-questions.md`).
- `bakjob-game` och `bakjob-linear`: spelen byggs i egna repon, och Linear
  används inte.
