# Quality targets

Ribban som `seo-a11y-auditor` kollar mot. Kommer från bootstrap-intervjun
2026-10-15.

## Prestanda och SEO (Lighthouse)

- **Performance, Accessibility, Best Practices, SEO: 90+** i alla fyra.
- **Mäts på:** startsidan, projektlistan och minst en projektsida, på mobil
  (Lighthouse standard-throttling).
- Tunga effekter och inbäddade spel får inte dra ner en sida under 90:
  ladda dem sent (`client:visible`) eller bakom en klick-för-att-spela.

## Tillgänglighet

- **WCAG 2.2, nivå AA.**
- Allt nås med tangentbord, med synligt fokus.
- `prefers-reduced-motion` respekteras.
- Kontrast minst 4.5:1 för text, 3:1 för stor text och UI-komponenter.
- Inbäddade spel har en titel (`title` på iframen) och en länk till spelet
  i egen flik.

## Meta

- **Titelkonvention:** `<Sidans namn> | <Ditt namn>`; startsidan bara
  `<Ditt namn>: Portfolio`. Namnet bestäms när sajten byggs.
- Varje sida har en unik `description` (max cirka 155 tecken) och Open
  Graph-bild.
- Kanonisk URL: produktionsdomänen när den finns (se `running.md`).

## JSON-LD per sidtyp

| Sidtyp | Schema |
|---|---|
| Startsida | `Person` + `WebSite` |
| Projektsida (spel) | `VideoGame` |
| Projektsida (hemsida/app) | `CreativeWork` (eller `WebApplication`) |
| Projektlista | `CollectionPage` med `ItemList` |
