# Skill: WordPress HTML Coding Standards

Denne skill definerer standarderne for skrivning af HTML i WordPress-kontekst (Templates, Block render-funktioner og Admin-sider). Målet er ren, semantisk og valid kode.

## 1. Generel Formatering
*   **Indrykning:** Brug altid **Tabs** (ligesom i PHP og JS). Indrykningen skal følge det logiske hierarki i DOM-strukturen.
*   **Tags:** Alle HTML-tags skal skrives med **små bogstaver**.
    *   *Korrekt:* `<div>`
    *   *Forkert:* `<DIV>`
*   **Selvlukkende elementer:** Alle selvlukkende tags skal have et mellemrum før skråstregen.
    *   *Korrekt:* `<br />`, `<img src="..." />`, `<input type="text" />`
    *   *Forkert:* `<br>`, `<img src="...">`

## 2. Attributter
*   **Anførselstegn:** Brug altid **dobbelt anførselstegn** (`"`) til attributværdier.
    *   *Korrekt:* `<div class="container">`
    *   *Forkert:* `<div class='container'>` eller `<div class=container>`
*   **Navngivning:** Attributter skal skrives med små bogstaver. Undgå camelCase.
*   **Boolean attributter:** Skriv dem fuldt ud (valgfrit i HTML5, men anbefalet i WP for klarhed).
    *   *Eksempel:* `<input type="checkbox" checked="checked" />`

## 3. PHP i HTML
Når PHP blandes med HTML, skal koden stadig være læselig:
*   **Indrykning af PHP-blokke:** PHP-tags skal følge HTML-indrykningen.
*   **Escaping:** Alle data, der indsættes i HTML-attributter (f.eks. `src`, `value`, `class`), skal escapes.
    *   *Korrekt:* `<input value="<?php echo esc_attr( $value ); ?>" />`
*   **Kortform:** Brug gerne `<?php echo` eller den korte echo-tag `<?=`, men vær konsistent (tjek projektets standard).

## 4. Semantik og Tilgængelighed (Accessibility)
*   **Alt-tekst:** Alle `<img>` tags skal have en `alt` attribut. Hvis billedet er dekorativt, lad den være tom (`alt=""`).
*   **Labels:** Alle form-elementer skal have et tilhørende `<label>` med en `for` attribut.
*   **ARIA:** Brug ARIA-attributter (`aria-expanded`, `aria-label` osv.) på interaktive elementer, der ikke er standard HTML-knapper eller links.

## 5. Scripts og Styles
*   **Inline styles:** Undgå inline styles (`style="..."`). Brug klasser i stedet.
*   **Type-attributter:** I HTML5 er `type="text/javascript"` og `type="text/css"` ikke længere nødvendige. Undlad dem for at holde koden ren.

## 6. Klasser og ID'er
*   **Navngivning:** Brug bindestreger (`-`) som separatorer (kebab-case).
*   **Prefixing:** I plugins og temaer bør du bruge et prefix for at undgå CSS-konflikter.
    *   *Korrekt:* `<div class="my-plugin-container">`

---

### Verificerings-tjekliste for HTML Code Review
1. [ ] Er der brugt tabs til indrykning?
2. [ ] Er alle tags og attributter i små bogstaver?
3. [ ] Har alle selvlukkende tags (`<img />`, `<input />`) et mellemrum før `/`?
4. [ ] Er alle attribut-værdier i dobbelte anførselstegn?
5. [ ] Er alle PHP-variable escaped korrekt (`esc_attr`, `esc_url`)?
6. [ ] Har alle billeder en `alt` attribut?
7. [ ] Er koden semantisk korrekt (f.eks. `<button>` til handlinger, `<a>` til links)?

---
