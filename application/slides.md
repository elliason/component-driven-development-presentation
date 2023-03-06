---
# try also 'default' to start simple
#theme: default
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: true
# some information about the slides, markdown enabled
info: |
    ## CDD & MF
    Prezentace pro Media Factory team.

    Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
    persist: false
# use UnoCSS (experimental)
css: unocss
---

# Component Driven Development

<v-click>

## A Moderní přístup k vývoji **větších** webových aplikací

</v-click>

---

# Component Driven Development

<img src="/images/sgdd-flow.png" class="" />

---

# Úrovně Komponent

Na jakých úrovních můžeme uplatnit komponentární přístup ?

<v-click>

- Organizace kódu, balíčky
- UI komponenty
- <s>Služby (microservices)</s>
- <s>Mikrofrontendy</s>

</v-click>

<!-- notes: UI komponenty jsou součástí balíčků, které jsou součástí organizace kódu-->

---

<img src="/images/microservices-vs-modular.jpg" class="" />

---

# Proč Komponenty ?

<v-click>

- **Znovupoužívání kódu** - vývojáři mohou používat již existující komponenty. Komponenty mohou být sdíleny mezi různými aplikacemi.

</v-click>

<v-click>

- **Zjednodušení vývoje** - vývojáři se mohou soustředit na jednu část aplikace, lepší focus

</v-click>

<v-click>

- **Zrychlení vývoje** - vývojáři mohou pracovat paralelně

</v-click>

<v-click>

- **Snadnější testování** - vývojáři mohou testovat jednotlivé komponenty v izolaci.

</v-click>

<v-click>

- **Snadnější integrace** - vývojáři mohou vytvářet komponenty bez nutnosti znát celý systém

</v-click>

<v-click>

- **Snadnější udržování** - vývojáři mohou měnit a refaktorovat jednotlivé komponenty bez nutnosti znát celý systém

</v-click>

---
layout: image-left
image: /images/sitecore-monorepo.png
---

# Komponenty & Organizace kódu

<v-click>

- Modulární organizace kódu. Vytváření malých jednoúčelových balíčků.

</v-click>

<v-click>

- Monorepo - spojení balíčků do větších celků.

</v-click>

<!-- NA obrázku příklad monorepo organizace kódu -->

---

# Monorepo

- **Monorepo ≠ Monolithic repo**
- Kolokace menších balíčků uvnitř jednoho repozitáře.
- Balíčky můžou být vyvíjeny i distribuovány samostatně.
- Balíčky v monorepu mají jasně definované závislosti.
- Jasně definované task pipelines a orchestration (lint, test, dev, build, deploy, ...)

- viz: <https://monorepo.tools/>

---

<img src="/images/lib-deps.webp" class="" />

---

# Monorepo Tools pro Frontend

- <s>Lerna</s>
- Workspaces (Yarn, NPM, **PNPM**) - package management.
- Orchestrace tasků - **TurboRepo**, NX, Rush, ...
- Publikování - **Changesets**

---

# Jak nám pomůže PNPM ?

- <https://pnpm.io/>
- Pohodlný package management
- Řešení některých problémů s NPM/Yarn Classic (indirect (phantom) dependencies, npm doppelgangers - duplicitní balíčky)
- auto instalace peer dependencies
- rychlejší instalace oproti npm nebo Yarn Classic
- jednoduché nastavení v porovnání s Yarn Berry

---

# Nevýhoda PNPM

- špatně napsané balíčky mohou způsobit problémy (Storybook < 7, Strapi CMS < 4.7.2, ...)

---

# Jak nám pomůže TurboRepo ?

- <https://turbo.build/>
- Orchestrace tasků
- Jednoduché nastavení
- Cache pro rychlejší buildy (lokální by default)
- Remote cache (Vercel placené řešení nebo vlastní implementace viz. <https://github.com/ducktors/turborepo-remote-cache>)

---

<img src="/images/turbo-0.webp" class="" />

---

<img src="/images/turbo-1.webp" class="" />

---

<img src="/images/turbo-2.webp" class="" />

---

<img src="/images/my-graph.png" class="" />

---

# Modulární kód = Udržovatelný kód

---

```json
{
  "devDependencies": {
      "@media-factory-cz/browserslist-config": "^0",
      "@media-factory-cz/eslint-config": "^1",
      "@media-factory-cz/eslint-config-react": "^1",
      "@media-factory-cz/prettier-config": "^1",
      "@media-factory-cz/stylelint-config": "^1",
      "@media-factory-cz/typescript-config": "^1",
      "@types/node": "^18",
      "@typescript-eslint/eslint-plugin": "^5",
      "@typescript-eslint/parser": "^5",
      "eslint": "^8",
      "eslint-config-prettier": "^8",
      "eslint-import-resolver-typescript": "^3.5.3",
      "eslint-plugin-import": "^2",
      "eslint-plugin-jest": "^27.2.1",
      "eslint-plugin-jsx-a11y": "^6",
      "eslint-plugin-react": "^7",
      "eslint-plugin-react-hooks": "^4",
      "eslint-plugin-testing-library": "^5",
      "postcss": "^8.4.18",
      "prettier": "^2",
      "stylelint": "^14",
      "stylelint-config-prettier": "^9",
      "stylelint-config-standard-scss": "^5",
      "typescript": "^4"
  },
}
```

---

```json
  "devDependencies": {
    "@media-factory-cz/prettier-config": "^1.0.3",
    "@types/node": "^18.14.0",
    "prettier": "^2.8.4"
  },
  "dependencies": {
    "turbo": "^1.8.2"
  }
```

---

# Komponenty v UI vývoji a designu

<v-click>

### Proč je 2023 skvělý rok pro CDD ?

</v-click>
<v-click>

- Vyspělý tooling ( Figma, Storybook, Bit ... ) - https://www.componentdriven.org/#tools
- Komponentové Frameworky ( React, Vue, Svelte, Solid, Qwik )
- Container Queries ( podpora v major browsers )
- Web Components ( Custom Elements, Shadow DOM, HTML Templates )

</v-click>

---

# Component Driven Development Proces

<v-click>

<img src="/images/sgdd-flow.png" class="" />

</v-click>

---

# Component Driven Development Proces


<v-click>

### 1) Vytváříme atomické komponenty v **izolovaném** prostředí. 

Storybook (nebo equivalent) je ideální nástroj pro tuto úlohu. Ve Stories definujeme možné stavy komponenty a její vlastnosti. Výsledný Storybook je také dokumentací komponenty.
Komponentu rovnou vytváříme s testy:
1) Snapshot testy (Jest nebo Storyshots pro Storybook)
2) Unit testy (Jest / Vitest + React Testing Library ...)

**Story = BDD vizuální test.**

</v-click>
<v-click>

### 2) Kombinujeme komponenty a sestavujeme složitější celky. 

Postupně zvyšujeme komplexitu komponenty a jejích vlastností kompozicí jednodušších celků.
Ze složených komponent stavíme "pages" a plníme je mock daty. 
Simulujeme chování komponent v krajních stavech.

Pokud je třeba přidáváme integrační testy (Jest / Vitest + React Testing Library ...).

</v-click>

---

# Component Driven Development Proces

<v-click>

### 3) Integrujeme pages do aplikace.

Napojujeme komponenty na data z backend API´s a přidáváme business logiku.
e2e testování (Cypress / Playwright)

</v-click>

---

# Výhody

- paralelní vývoj, FE nemusí čekat na BE a naopak
- Single Responsibility Principle, malé API je snažší na naučení a udržování
- DRY, kód se používá vícekrát
- Testovatelnost
- Udržitelnost, modulární kód bude jednoduší refaktorovat
- Debugovatelnost, mělo by být snažší identifikovat problém
- Feedback netechnických členů týmu pomocí Storybooku

## Automatizace!

- Vytváření malých izolovaných komponent se bude v budoucnu lépe automatizovat pomocí generativních AI nástrojů
- https://www.animaapp.com/ - Automatizace (auto dokumentace ve Storybooku, automatizace testů)

---

# F.I.R.S.T. principy

Keep it (**F**)ocused.

Keep it (**I**)ndependent.

Keep it (**R**)eusable.

Keep it (**S**)mall.

Keep it (**T**)estable.

or in short, FIRST.

~ Addy Osmani

https://addyosmani.com/first/

---

# Zajímavé nástroje

- https://storybook.js.org/
- https://www.animaapp.com/
- https://bit.dev/
- https://www.componentdriven.org/#tools
