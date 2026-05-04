# Skill: WordPress CSS Coding Standards

Denne skill definerer reglerne for CSS-udvikling i WordPress. Formålet er at sikre en ensartet struktur, der er let at scanne visuelt og minimere konflikter i det globale CSS-namespace.

## 1. Generel Formatering
*   **Indrykning:** Brug altid **Tabs** (ikke spaces).
*   **Selectors:** Hver selector skal stå på sin egen linje.
*   **Braces (Krølleparenteser):**
    *   Den åbnende parentes `{` skal stå på samme linje som den sidste selector.
    *   Den lukkende parentes `}` skal stå på sin egen linje i samme indrykningsniveau som selectoren.
*   **Egenskaber (Properties):**
    *   Hver egenskab skal stå på sin egen linje med én indrykning (tab).
    *   Brug et mellemrum efter kolonet (`:`), men ikke før.
    *   Afslut altid med et semikolon (`;`).
    ```css
    .my-plugin-container {
        display: block;
        margin: 0 auto;
    }
    ```

## 2. Navngivning (Selectors)
*   **Lowercase:** Brug kun små bogstaver.
*   **Separation:** Brug bindestreger (`-`) til at adskille ord (kebab-case). Undgå `_` (underscores) og camelCase.
*   **Undgå ID'er:** Brug aldrig ID'er (`#header`) til styling. Brug altid klasser.
*   **Prefixing:** Giv altid dine klasser et unikt prefix for at undgå konflikter med andre plugins/temaer.
    *   *Korrekt:* `.my-plugin-button { ... }`

## 3. Egenskabs-rækkefølge (Property Ordering)
WordPress foreskriver en logisk rækkefølge af egenskaber for at gøre koden lettere at læse:
1.  **Display & Positioning** (`display`, `position`, `float`, `z-index`)
2.  **Box Model** (`width`, `height`, `margin`, `padding`, `border`)
3.  **Typography** (`font`, `line-height`, `text-align`)
4.  **Visuals** (`background`, `color`, `opacity`)
5.  **Misc** (`cursor`, `transition`)

## 4. Værdier (Values)
*   **Nul-enheder:** Brug aldrig enheder ved `0` (f.eks. brug `0`, ikke `0px`).
*   **Farver:**
    *   Brug små bogstaver til hex-koder (f.eks. `#ffffff`).
    *   Brug shorthand hex hvis muligt (f.eks. `#fff` i stedet for `#ffffff`).
*   **Anførselstegn:** Brug dobbelte anførselstegn (`"`) i attribut-selectors eller font-navne.
*   **Media Queries:** Placer media queries direkte efter den relevante CSS-regel eller samlet i bunden. Indryk indholdet i media query'en med en tab.

## 5. Kommentarer
Brug sektions-kommentarer til at opdele dit stylesheet:
```css
/**
 * # Section Name
 * -------------------------------------------------------------------------
 */

.my-plugin-element {
    /* Individuel kommentar */
    color: #333;
}
```

## 6. Best Practices
*   **Ingen !important:** Undgå `!important` medmindre det er absolut nødvendigt (f.eks. for at overskrive inline-styles fra 3.-parts biblioteker).
*   **Shorthand:** Brug shorthand egenskaber (`margin: 10px 0;`) frem for individuelle (`margin-top: 10px; margin-bottom: 10px;`) hvor det giver mening for læsbarhed.

---

### Verificerings-tjekliste for CSS Code Review
1. [ ] Er der brugt tabs til indrykning?
2. [ ] Er alle selectors i små bogstaver med bindestreger?
3. [ ] Er der mellemrum efter kolonet i egenskaber?
4. [ ] Er der undgået enheder ved 0-værdier (f.eks. bare `0`)?
5. [ ] Er alle hex-farvekoder i små bogstaver?
6. [ ] Er rækkefølgen af egenskaber logisk (Position -> Box Model -> Typos -> Visuals)?
7. [ ] Er der brugt prefix på alle klassenavne?

---
