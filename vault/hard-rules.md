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
- **Astro-sidor är statiska som standard.** Interaktiva delar är öar
  (`client:*`-direktiv) och laddas så sent som möjligt (`client:visible`,
  `client:idle`) så att effekterna inte sänker Lighthouse under ribban i
  `quality-targets.md`.
- **Effekter respekterar `prefers-reduced-motion`.** Varje animation har ett
  lugnt alternativ.
- **Externa länkar** som öppnas i ny flik har `rel="noopener noreferrer"`.
- **Hemligheter committas aldrig.** `.env*` är ignorerade; bara
  `.env.example` (utan värden) får finnas i repot.
