# Skill: WordPress PHP Coding Standards (WPCS)

Denne skill definerer de strikse krav til PHP-udvikling i WordPress-økosystemet (Plugins og Themes) baseret på de officielle [WordPress Coding Standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/php/).

## 1. Syntax & Formatering
*   **Indrykning:** Brug altid **Tabs** (ikke spaces).
*   **Yoda Conditions:** Logiske sammenligninger skal have konstanten/værdien til venstre.
    *   *Korrekt:* `if ( true === $variable )`
    *   *Forkert:* `if ( $variable === true )`
*   **PHP Tags:** Brug aldrig short tags (`<?`). Brug altid `<?php`. Undlad den afsluttende `?>` i rene PHP-filer.
*   **Braces (Krølleparenteser):** Skal altid bruges, selv ved simple statements.
    ```php
    if ( $condition ) {
        do_something();
    }
    ```
*   **Mellemrum (Whitespace):** Indsæt mellemrum inde i parenteser og efter kommaer.
    *   *Korrekt:* `my_function( $param1, $param2 );`
    *   *Forkert:* `my_function($param1,$param2);`

## 2. Navngivning (Naming Conventions)
*   **Funktioner & Variabler:** Brug `snake_case` (små bogstaver og underscores).
*   **Klasser:** Brug `Pascal_Case` med underscores som separator.
    *   Eksempel: `class My_Plugin_Admin_UI {}`
*   **Filer:** Filnavne skal være i små bogstaver, og underscores erstattes med bindestreger.
    *   Klasser skal ligge i filer præfikset med `class-`.
    *   Eksempel: `class-my-plugin-admin-ui.php`
*   **Prefixing:** Alle globale funktioner, klasser og variabler SKAL have et unikt prefix for at undgå navnesammenstød (collisons).
    *   Eksempel: `function myproject_save_data()`

## 3. Sikkerhed (Data Validation & Sanitization)
Dette er det vigtigste punkt for WordPress-standarder.
*   **Input (Sanitization):** Rens alle data fra brugeren eller databasen før brug.
    *   `sanitize_text_field()`, `absint()`, `sanitize_email()`, etc.
*   **Output (Escaping):** Alt data der printes til skærmen SKAL escapes så tæt på output som muligt ("Late Escaping").
    *   `esc_html()`, `esc_attr()`, `esc_url()`, `wp_kses_post()`.
*   **Database:** Brug altid `$wpdb->prepare()` for at forhindre SQL-injection.
*   **Nonces:** Brug altid Nonces til at verificere intention ved handlinger (f.eks. i forms eller AJAX).
    *   `wp_create_nonce()`, `check_admin_referer()`.

## 4. Dokumentation (Inline Docs)
Følg PHPDoc-standarden for alle elementer:
*   **Filer:** Skal have en file header.
*   **Funktioner:** Skal have en beskrivelse, `@param` (med type) og `@return` (med type).
*   **Hooks:** Brug `/** This filter is documented in... */` hvis et filter genbruges.

```php
/**
 * Beregner summen af to tal.
 *
 * @since 1.0.0
 *
 * @param int $a Første tal.
 * @param int $b Andet tal.
 * @return int Summen.
 */
function my_prefix_add_numbers( $a, $b ) {
    return (int) $a + (int) $b;
}
```

## 5. Best Practices
*   **Ingen "Magic Numbers":** Brug konstanter i stedet for rå tal i koden.
*   **Loose Coupling:** Undgå direkte afhængigheder; brug hooks (`add_action`, `add_filter`) til at interagere med andre dele af systemet.
*   **Error Handling:** Undgå at undertrykke fejl med `@`. Brug WordPress' fejlhåndtering eller standard PHP exceptions.

---

### Verificerings-tjekliste (Code Review)
1. [ ] Er der brugt tabs i stedet for spaces?
2. [ ] Er alle variable og output escaped (`esc_html` osv.)?
3. [ ] Er alle sammenligninger skrevet som Yoda Conditions?
4. [ ] Er der prefix på alle globale funktioner?
5. [ ] Findes der PHPDoc til alle funktioner?
6. [ ] Er filnavnet korrekt i forhold til klassenavnet?

---
