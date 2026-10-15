# Running

Kommandona gäller när SvelteKit-projektet är skapat (första PR:en efter
setup). Tills dess finns ingen `package.json`.

## Setup

```sh
corepack enable pnpm   # en gång per dator; pnpm följer med Node via corepack
pnpm install
```

Kräver Node 22 eller senare (utvecklas på Node 24).

Skapa projektet (bara första gången):

```sh
pnpm dlx sv create . --template minimal --types ts --no-add-ons --install pnpm
pnpm dlx sv add prettier eslint
pnpm add -D @sveltejs/adapter-vercel   # och byt adapter i svelte.config.js
corepack use pnpm@latest               # skriver "packageManager" i package.json, behövs av CI
```

Kontrollera sedan att `tsconfig.json` har `"strict": true`.

## Dev

```sh
pnpm dev
```

Dev-servern körs på <http://localhost:5173>.

## Build

```sh
pnpm build     # vite build med adapter-vercel
pnpm preview   # kör bygget lokalt på http://localhost:4173
```

## Test

Inga enhets- eller E2E-tester. Kontrollerna är bygge, typecheck och lint:

```sh
pnpm check   # svelte-kit sync + svelte-check: typfel i .svelte- och .ts-filer
pnpm lint    # prettier --check . && eslint .
pnpm build
```

Samma tre körs i CI (`.github/workflows/ci.yml`) på varje PR.

## Lint and format

```sh
pnpm lint     # prettier --check . && eslint .
pnpm format   # prettier --write . (med prettier-plugin-svelte)
```

Prettier körs också automatiskt på varje fil Claude ändrar (hook i
`.claude/settings.json`).

## Smoke test

Inget smoke test än. Se `status/open-questions.md`.

## Deploy

- **Plattform:** Vercel, kopplat till GitHub-repot `Bakjob/portfolio-website`,
  med `@sveltejs/adapter-vercel`. Förrenderade sidor serveras statiskt;
  serverkod (`+page.server.ts`, `+server.ts`) körs som Vercel Functions.
- **Projektnamn på Vercel:** inte kopplat än (förslag: `portfolio-website`).
- **Produktionsdomän:** ingen egen domän än; Vercels `*.vercel.app`-adress.
- **Produktionsbranch:** `main`. Varje push till `main` deployas
  automatiskt, och varje PR får en preview-URL.
- **Miljövariabler:** inga än. Nya läggs in i Vercels projektinställningar
  (Production och Preview separat) och med namn (aldrig värden) i
  `.env.example`. Lokalt i `.env`, som är git-ignorerad.
- **Rollback:** i Vercels dashboard, välj en tidigare deployment och
  "Promote to Production" (eller `vercel rollback`).
- **Efter lansering:** lägg in sajten i Google Search Console och skicka in
  en sitemap (en `src/routes/sitemap.xml/+server.ts`, förrenderad).
