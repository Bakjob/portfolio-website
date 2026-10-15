# 0001: SvelteKit i stället för Astro

**Status:** Gällande

**Beslut:** Sajten byggs med SvelteKit (pnpm, strikt TypeScript,
`@sveltejs/adapter-vercel`), inte Astro. Projektet räknas som en webbapp.

**Varför:** Portfolion ska få inloggning och en backend senare. Astro är
byggt för innehållssajter och klarar serverlogik men inte som sin styrka;
SvelteKit har load-funktioner, form actions och server-routes från början.
Svelte är dessutom redan bekant, Astro hade varit ett nytt lager att lära.
Bytet gjordes innan någon kod fanns, så det kostade inget.

**Utesluter:** Astro och dess content collections och öar. Innehållssidor
(projektsidorna) får i stället förrenderas i SvelteKit, t.ex. med mdsvex
eller markdown-filer som läses i en `load`-funktion.

**Se även:** `../status/open-questions.md` (databas och inloggning),
`../hard-rules.md` (SvelteKit-reglerna).
