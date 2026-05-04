# Skill: WordPress JavaScript Coding Standards (WPJCS)

Denne skill definerer standarderne for JavaScript-udvikling i WordPress. Den dækker alt fra simple scripts i temaer til avanceret Block-udvikling med React/JSX.

## 1. Syntax & Formatering
*   **Indrykning:** Brug altid **Tabs** (ligesom i PHP).
*   **Semikoloner:** Skal altid bruges. Undlad aldrig semikoloner ved afslutning af statements.
*   **Anførselstegn:** Brug **enkelte anførselstegn** (`'`) til strenge, medmindre strengen indeholder et enkelt anførselstegn.
    *   *Korrekt:* `const text = 'Her er en tekst';`
*   **Mellemrum (Whitespace):**
    *   Mellemrum efter kommaer og omkring operatorer (`=`, `+`, `===`).
    *   Mellemrum inde i parenteser og krølleparenteser.
    *   *Korrekt:* `myFunction( arg1, arg2 );` eller `const { data } = settings;`
*   **Lighed:** Brug altid striks sammenligning (`===` og `!==`) i stedet for løs sammenligning (`==`).

## 2. Navngivning (Naming Conventions)
*   **Variabler & Funktioner:** Brug `camelCase`.
    *   *Korrekt:* `const myVariable = 10;`
*   **Klasser:** Brug `PascalCase`.
*   **Konstanter:** Brug `SCREAMING_SNAKE_CASE` (kun store bogstaver og underscores).
*   **Filer:** Brug bindestreger til at adskille ord i filnavne.
    *   *Korrekt:* `my-block-script.js`

## 3. Blok-udvikling & React (Gutenberg)
Ved udvikling af blocks skal du følge moderne ESNext-standarder via `@wordpress/scripts`:
*   **Destructuring:** Brug destructuring til props og WordPress-pakker.
    *   *Korrekt:* `const { registerBlockType } = wp.blocks;`
*   **Dependencies:** Brug aldrig globale variabler direkte hvis muligt; træk dem fra `wp`-objektet (f.eks. `wp.element`, `wp.components`, `wp.i18n`).
*   **JSX:** Følg React-best-practices. Husk altid `key` i loops og brug `Fragment` (`<></>`) for at undgå unødvendige DOM-noder.
*   **block.json:** Brug altid `block.json` (Metadata Version 3) til registrering af blocks.

## 4. Internationalisering (i18n)
Hardkod aldrig tekststrenge. Brug `wp.i18n` pakken:
*   Brug `__()` til almindelige strenge.
*   Brug `_x()` hvis der er brug for kontekst.
*   Husk altid at inkludere dit "text-domain".
    *   *Eksempel:* `__( 'Save Settings', 'my-plugin-slug' )`

## 5. Dokumentation (JSDoc)
Alle funktioner skal dokumenteres med JSDoc:
```javascript
/**
 * Kontrollerer om en værdi er gyldig.
 *
 * @param {string} value - Værdien der skal tjekkes.
 * @param {Object} settings - Indstillinger for validering.
 * @return {boolean} True hvis værdien er gyldig.
 */
function isValid( value, settings ) {
    // Kode her...
}
```

## 6. Best Practices
*   **Event Listeners:** Ryd altid op efter event listeners, hvis de tilføjes i React (f.eks. i `useEffect`).
*   **Optional Chaining:** Brug `?.` for at undgå fejl ved dybe objekt-strukturer.
*   **Ingen Console.log i produktion:** Fjern alle logs eller brug en wrapper før koden pushes.

---

### Verificerings-tjekliste for JS Code Review
1. [ ] Er der brugt tabs (ikke spaces)?
2. [ ] Er der semikolon efter alle statements?
3. [ ] Er variabler navngivet med `camelCase`?
4. [ ] Er alle tekststrenge wrappet i `__()` eller lignende i18n-funktioner?
5. [ ] Er der mellemrum inde i parenteser? (f.eks. `if ( condition )`)
6. [ ] Bruges `wp`-globalerne korrekt (f.eks. `wp.element.createElement`)?

---
