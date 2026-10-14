# Running

Kommandona gäller när Astro-projektet är skapat (första PR:en). Tills dess
finns ingen `package.json`.

## Setup

```sh
corepack enable pnpm   # en gång per dator; pnpm följer med Node via corepack
pnpm install
```

Kräver Node 22 eller senare (utvecklas på Node 24).

Skapa projektet (bara första gången):

```sh
pnpm create astro@latest . --template minimal --install --no-git
```

Kontrollera sedan att `tsconfig.json` ärver `astro/tsconfigs/strict` (eller
`strictest`), och lås pnpm-versionen så att CI (`pnpm/action-setup`) hittar
den:

```sh
corepack use pnpm@latest   # skriver "packageManager" i package.json
```

## Dev

```sh
pnpm dev
```

Dev-servern körs på <http://localhost:4321>.

## Build

```sh
pnpm build     # astro build, output i dist/
pnpm preview   # serverar dist/ lokalt för en sista koll
```

## Test

Inga enhets- eller E2E-tester. Kontrollerna är bygge, typecheck och lint:

```sh
pnpm check   # astro check: typfel i .astro- och .ts-filer (@astrojs/check)
pnpm lint    # ESLint med eslint-plugin-astro
pnpm build
```

Samma tre körs i CI (`.github/workflows/ci.yml`) på varje PR.

## Lint and format

```sh
pnpm lint           # eslint .
pnpm format         # prettier --write . (med prettier-plugin-astro)
pnpm format:check   # prettier --check .
```

Prettier körs också automatiskt på varje fil Claude ändrar (hook i
`.claude/settings.json`).

## Smoke test

Inget smoke test än. Se `status/open-questions.md`.

## Deploy

- **Plattform:** Vercel, kopplat till GitHub-repot `Bakjob/portfolio-website`.
  Statisk output, ingen adapter behövs.
- **Projektnamn på Vercel:** inte kopplat än (förslag: `portfolio-website`).
- **Produktionsdomän:** ingen egen domän än; Vercels `*.vercel.app`-adress.
- **Produktionsbranch:** `main`. Varje push till `main` deployas
  automatiskt, och varje PR får en preview-URL.
- **Miljövariabler:** inga än. Nya läggs in i Vercels projektinställningar
  och med namn (aldrig värden) i `.env.example`.
- **Rollback:** i Vercels dashboard, välj en tidigare deployment och
  "Promote to Production" (eller `vercel rollback`).
- **Efter lansering:** lägg in sajten i Google Search Console och skicka in
  sitemapen (`@astrojs/sitemap`, `/sitemap-index.xml`).
