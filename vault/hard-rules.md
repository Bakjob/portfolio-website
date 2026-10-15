# Hard rules

Korta och tvingande. Krockar något här med `CLAUDE.md` vinner den här filen.

## Språk och text

- Kod, identifierare och kommentarer på **engelska**.
- Docs och vault på **svenska**.
- All text på sajten på **engelska**.
- Commit-meddelanden, issues och PR:er på **engelska**.
- **Aldrig tankstreck (em dash)**, varken i kod, docs eller på sajten. Använd
  kolon, komma, parentes eller punkt.

## Git

- **Committa aldrig direkt till `main`.** Allt utom en trivial enradsfix går
  via en feature-branch och en PR. Bara jag mergar.
- **Aldrig force push.**
- Commit-meddelanden nämner issuet (`#N`) när commiten jobbar mot ett.
- PR-titel: gitmoji + issue-ID (`✨ #12 Add project grid`). PR-beskrivningen
  har `Closes #N` och den manuella testchecklistan.

## Stack

- **Strikt TypeScript.** Ingen `any` utan en kommentar som förklarar varför,
  inga `@ts-ignore` som täcker över riktiga fel.
- **pnpm är enda pakethanteraren.** Inga `package-lock.json` eller
  `yarn.lock`; `pnpm-lock.yaml` committas.
- **Innehållssidor förrenderas.** Sidor utan inloggning eller
  per-besökar-data har `export const prerender = true`.
- **Serverkod hålls på servern.** Databas, inloggning och hemligheter bara i
  `src/lib/server/`, `+page.server.ts`, `+layout.server.ts` och `+server.ts`.
  Hemligheter läses bara via `$env/static/private` eller
  `$env/dynamic/private`, aldrig med `PUBLIC_`-prefix.
- **Tunga effekter och inbäddade spel laddas sent** (dynamisk import när de
  syns, eller bakom en klick-för-att-spela), så att de inte sänker
  Lighthouse under ribban i `quality-targets.md`.
- **Effekter respekterar `prefers-reduced-motion`.** Varje animation har ett
  lugnt alternativ.
- **Externa länkar** som öppnas i ny flik har `rel="noopener noreferrer"`.
- **Config file:** `src/lib/config.ts`. Varje justerbart värde ligger där:
  tider och hastigheter för animationer, tröskelvärden, storlekar, gränser
  (t.ex. sessionslängd, antal projekt per sida).
- **Hemligheter committas aldrig.** `.env*` är ignorerade; bara
  `.env.example` (utan värden) får finnas i repot.
