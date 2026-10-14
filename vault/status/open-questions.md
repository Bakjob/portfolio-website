# Open questions

Saker om portfolio website som inte är bestämda än. Flytta en post till
`decisions/` när den är avgjord, eller ta bort den när den inte längre spelar
roll.

- **Smoke test:** lägg till kommando och kontroller under `## Smoke test` i
  `running.md` när sajten finns. Förslag: bygg + kontroll av trasiga interna
  och externa länkar (sajten är full av länkar).
- **Lint-kommando:** bekräfta `pnpm lint` (ESLint med Astro-plugin) i
  `running.md` när Astro-projektet är skapat; uppdatera CI om skriptnamnen
  blir andra.
- **Vercel-projekt:** skriv in projektnamnet på Vercel och den faktiska
  produktions-URL:en (`*.vercel.app`) i `running.md` under `## Deploy` när
  projektet är kopplat.
- **Egen domän:** ingen än. Lägg in den under `## Deploy` och i
  `quality-targets.md` (kanonisk URL) när den finns.
- **Hur spel bäddas in:** iframe från itch.io, egen statisk build i `public/`,
  eller bara länk? Avgör när första spelet läggs in, och skriv ett beslut.
- **Projektsidornas mall:** vilka sektioner en projektsida har (se
  `design/page-families.md`). Fylls i när första projektsidan byggs.
- **Visuell stil och varumärke:** färger, typsnitt och vilka "coola saker"
  (animationer, effekter) som är signaturen. Hamnar i `design/`.
