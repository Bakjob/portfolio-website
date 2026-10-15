# portfolio website

En hemsida som fungerar som mitt portfolio, med länkar och coola saker
överallt. Spel och andra hemsidor läggs in och länkas härifrån efter hand.
Byggd med SvelteKit, strikt TypeScript och pnpm, hostad på Vercel.
Inloggning och backend kommer senare.

Den här filen handlar om process och samarbete: hur man jobbar i repot, inte
vad projektet gör. Allt om själva projektet (hårda regler, hur det körs,
fattade beslut, nuläget) ligger i `vault/` (se nedan). Buggar och att-göra
ligger i GitHub Issues. Om du ska skriva kod och inte har läst
`vault/hard-rules.md` i den här sessionen, läs den först: den är kort, och
varje regel i den finns för att det redan kostat ett varv att bryta den.

**Den här filen hålls kort, med flit.** Om den växer förbi några hundra rader
(designbeslut, statusuppdateringar, buggar, en hel historik påklistrad över
tid), bryt ut historiken till en daterad fil och lämna en pekare. Ska du lägga
till ett designbeslut, en statusuppdatering, en bugg eller mer än en rad om
"hur projektet funkar" här, hör det nästan säkert hemma i `vault/` i stället,
med högst en pekare kvar här.

---

## Språkregel

- **Kod, identifierare och kommentarer:** engelska.
- **Dokumentation och vault:** svenska.
- **Text på sajten (allt besökaren ser):** engelska.
- **Commit-meddelanden, issues och PR:er:** engelska.
- **Chatt med Claude:** svenska.

**Använd aldrig tankstreck (em dash).** Använd kolon, komma, parentes eller
punkt i stället. Det gäller kodkommentarer, docs och text på sajten.

---

## Project docs: läs detta före allt designrelaterat

`vault/` är projektets minne: hårda regler, hur det körs, fattade beslut,
nuläget och en daterad framstegslogg. Börja med `vault/README.md` för
upplägget. Viktigaste ingångarna:

- `vault/hard-rules.md`: de regler som gäller. Läs innan du rör kod.
- `vault/running.md`: hur projektet installeras, körs, byggs, kontrolleras
  och deployas.
- `vault/quality-targets.md`: kvalitetsribban (Lighthouse, WCAG, SEO).
- `vault/design/`: stil, varumärke och mallarna för projektsidorna
  (`page-families.md`).
- `vault/status/current-status.md` och `.../open-questions.md`: läs innan
  riktigt arbete börjar; de beskriver idag.
- `vault/decisions/`: numrerade beslut (ADR) för allt som är avgjort, så
  att ingen öppnar en utkämpad fråga av misstag.
- Buggar och att-göra: i GitHub Issues, inte i vaulten.

**Håll den aktuell.** Efter en riktig arbetsinsats (ett varv, en buggfix värd
att minnas, ett beslut), uppdatera vaulten: en daterad post i `progress/`, en
ny numrerad beslutsfil om något faktiskt avgjordes, en ändring på plats i
`current-status.md` om det som är sant om projektet ändrats. Använd
`vault-update`, `new-decision` eller agenten `vault-scribe` för det, i stället
för att låta uppdateringarna glida.

### Om en begäran går emot något i beslutsloggen

Gå inte tyst med på det och vägra inte tyst. Säg rakt ut vad beslutet säger
och att begäran går emot det, och fråga sedan: **"Är du säker?"** Det är inte
friktion för sakens skull: beslutsloggen finns just för att ingen, människa
eller Claude, ska öppna en avgjord fråga i smyg, och att fråga en gång,
uttryckligen, är det som gör att en kursändring är en kursändring och inte
en glidning.

---

## Issue tracker

**Allt nytt arbete, buggar och förbättringar går genom GitHub Issues** i repot
`Bakjob/portfolio-website`, inte bara buggar, inte i docs, inte i en fil i
repot. Labels skiljer på typ av arbete (`bug`, `enhancement`,
`documentation`); flödet nedan är detsamma för alla. Den dagliga mekaniken
(exakta kommandon) finns i skillen `github-issues-workflow`.

Projektet använder det **enkla flödet**: ett issue stängs när dess PR mergas.
Labeln `in progress` används medan arbetet pågår; `in review`-loopen används
inte.

- **När en riktig arbetsinsats börjar skapas issuet**, om det inte redan
  finns, i samma stund arbetet börjar, inte efteråt.
- **Sätt `in progress` OCH assignee i samma steg, före första ändringen**,
  inte i samband med commit eller PR.
- **Om en commit fixar eller jobbar mot ett issue, nämn det i meddelandet**
  (t.ex. `#30: fix broken project link`), så att git log ensam visar vilka
  commits som försöker fixa vad.
- **PR-titeln börjar med en gitmoji som matchar typen och issue-numret**,
  t.ex. `✨ #12 Add project grid` (🐛 bugg, ✨ funktion, ♻️ förbättring,
  📝 docs). Upprepa gitmojin bredvid "Ready to merge" i slutet av beskrivningen
  när PR:en faktiskt är klar.
- **PR-beskrivningen har `Closes #N`**, så att issuet stängs vid merge.
- **Den manuella testchecklistan ligger i PR-beskrivningen**, som riktiga
  markdown-checkboxar, inte prosa. Det här går före skillens standard (som
  lägger checklistan på issuet). Lägg bara upp det som verkligen behöver
  ögon och händer (hur en effekt känns, visuella glitchar, ett inbäddat spel
  på mobil). Allt som bygge, lint och typecheck kan bevisa kör Claude själv
  innan PR:en öppnas.
- **Synka issues direkt när något mergats.** När `git pull` eller
  `gh pr list --state merged` visar en mergad PR, kolla att issuet stängts.

---

## Säg emot, var ingen ja-sägare

Om en designändring ser ut att kräva att fungerande delar rivs upp för en liten
vinst, eller krockar med de hårda reglerna eller resonemanget i
beslutsloggen, **säg det innan du bygger.** Förklara konkret vad det kostar:
vilka delar som måste göras om, vilken regel eller vilket beslut det krockar
med, och varför avvägningen ser dålig ut. Be sedan om en uttrycklig
bekräftelse innan du kör.

---

## Clean code-standard

- **Namn säger vad saken är.** Ett variabel-, funktions- eller klassnamn ska
  göra en kommentar onödig. Behövs en kommentar för att förklara vad koden gör
  snarare än varför, byt namn i stället.
- **Små funktioner, ett ansvar.** En funktion gör en sak. Behöver
  beskrivningen ett "och" är det troligen två funktioner.
- **Ingen död kod.** Ta bort oanvända funktioner, bortkommenterade block och
  oanvända variabler i stället för att spara dem "för säkerhets skull". Git
  är säkerhetsnätet.
- **DRY, men inte till priset av fel abstraktion.** Tre likadana rader på tre
  ställen behöver inte automatiskt en gemensam hjälpare. Bryt ut när ett
  TREDJE riktigt användningsfall dyker upp, inte innan.
- **Kommentarer förklarar VARFÖR, aldrig VAD.**
- **Konsekvent formatering**, enligt det filen redan gör (Prettier sköter det).
- **Inga halvfärdiga implementationer.** En funktion fungerar hela vägen
  eller committas inte. Inga feature flags, inga tysta fallbacks för fall som
  inte kan hända, ingen TODO i stället för logik som borde finnas.
- Krockar detta med `vault/hard-rules.md` vinner hard-rules.

---

## Git workflow

Bara jag (plus Claude) jobbar i repot. Reglerna:

- **Committa ofta, vid rimliga punkter.** En commit är en sammanhängande,
  fungerande ändring. Kan du inte beskriva den i en mening är den troligen
  mer än en commit.
- **Arbete sker på en branch, inte på `main`.** Brancha från `main` för allt
  utom en trivial enradsfix. Namnge efter vad branchen gör:
  `feature/<slug>`, `fix/<slug>`, `chore/<slug>`.
- **Merge till `main` sker via pull request.** Små, täta PR:er slår en
  jättestor.
- **Committa, brancha, pusha och öppna PR:en själv, utan att fråga, när en
  ändring är verifierad** (bygge, lint och typecheck går igenom, eller
  granskningsnivå för en ren docs-ändring).
- **Merge är det enda steget detta INTE täcker.** Öppna PR:en, kör den
  verifiering som finns, säg rakt ut att den är klar; själva mergen gör jag,
  varje gång, utan undantag.
- **Commit-meddelanden:** fritt men tydligt, på engelska. Vad som ändrats
  och ofta varför, inget fyllnadsprat, inga tankstreck.
- Force push är blockerat i `.claude/settings.json`.

---

## Skills och agenter i projektet

Installerade som plugins från marknadsplatsen `bakjob` (se
`.claude/settings.json`). De ligger i `~/.claude/plugins`, utanför projektet.
De läser projektets värden från den här filen och från `vault/hard-rules.md`,
`vault/running.md`, `vault/quality-targets.md` och vaulten, så håll dem
aktuella. Anropa dem direkt i stället för att återskapa deras logik.

- **`bakjob-core`:** `git-checkpoint` (commit vid rätt punkt), `vault-update`
  och `new-decision` (håller vaulten aktuell), `smoke-test`; agenterna
  `architect` (planerar större ändringar), `test-runner` (kör och läser
  kontrollerna), `vault-scribe` och `config-value-auditor` (letar efter
  hårdkodade värden som hör hemma i `src/lib/config.ts`).
- **`bakjob-github`:** `github-issues-workflow` (skapa, ta och stänga issues
  med `gh`).
- **`bakjob-web`:** `design-taste-frontend` och `redesign-skill` (visuell
  kvalitet), `content-page-family` (projektsidorna enligt samma mall),
  `web-deploy` och `static-site-deploy` (Vercel), `visual-check`
  (skärmdumpar mot dev-servern); agenten `seo-a11y-auditor` (kollar mot
  `quality-targets.md`).
- **`bakjob-surdeg`:** `feed` ändrar en del av uppsättningen senare, `doctor`
  kontrollerar att allt hänger ihop.
