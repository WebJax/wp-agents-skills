# Skill: WordPress Accessibility (a11y) Coding Standards

Denne skill sikrer, at alt hvad der bygges i WordPress, kan bruges af alle, uanset handicap eller brug af hjælpemidler som skærmlæsere, tastatur-navigation eller skærmforstørrere.

## 1. Tastatur-navigation (Keyboard Interaction)
*   **Focus States:** Fjern aldrig focus-outlines (`outline: none`) uden at erstatte dem med en tydelig, kontrastfuld visuel stil.
*   **Interaktive elementer:** Brug rigtige HTML-elementer til interaktion.
    *   Brug `<button>` til handlinger på siden (f.eks. åbne en menu, slette noget).
    *   Brug `<a>` til navigation (skifte side eller hoppe til et anker).
*   **Tab-rækkefølge:** Sørg for at den logiske rækkefølge i koden matcher den visuelle rækkefølge på skærmen.

## 2. Semantisk HTML & Struktur
*   **Overskrifts-hierarki:** Spring aldrig over overskriftsniveauer. En `<h3>` skal altid efterfølge en `<h2>`. Brug aldrig overskrifter kun for deres visuelle størrelse.
*   **Landmarks:** Brug HTML5 elementer som `<header>`, `<nav>`, `<main>`, `<footer>` og `<aside>` korrekt for at hjælpe skærmlæsere med at navigere.
*   **Lister:** Brug `<ul>` eller `<ol>` til grupperet indhold. Skærmlæsere fortæller brugeren, hvor mange punkter der er i en liste.

## 3. Tekstalternativer & Billeder
*   **Alt-attributter:** Alle billeder SKAL have en `alt` attribut.
    *   *Beskrivende:* Hvis billedet giver information (f.eks. en graf).
    *   *Tom (`alt=""`):* Hvis billedet kun er dekorativt (f.eks. et baggrundsmønster).
*   **Link-tekst:** Undgå intetsigende links som "Læs mere" eller "Klik her". Link-teksten skal give mening uden for kontekst (f.eks. "Læs mere om vores ydelser").

## 4. Skærmlæser-tekst (.screen-reader-text)
WordPress har en standard CSS-klasse til tekst, der kun skal læses højt af skærmlæsere, men ikke vises visuelt.
*   **Brug:** Brug den til at give ekstra kontekst til knapper eller links, der kun bruger ikoner.
    ```html
    <button>
        <span class="dashicons dashicons-trash"></span>
        <span class="screen-reader-text">Slet indlæg</span>
    </button>
    ```

## 5. Formularer & Labels
*   **Explicit Labels:** Alle form-elementer skal have et tilhørende `<label>` med en `for` attribut, der matcher inputtets `id`.
    *   *Forkert:* Brug af `placeholder` som den eneste label.
*   **Fejlmeddelelser:** Skal være tydelige og linket til inputfeltet via `aria-describedby`.

## 6. Farver & Kontrast
*   **Kontrastforhold:** Tekst skal have et kontrastforhold på mindst **4.5:1** mod baggrunden (WCAG AA).
*   **Farve som eneste indikator:** Brug aldrig kun farve til at formidle information (f.eks. "Klik på den grønne knap for at starte"). Brug tekst eller ikoner som supplement.

## 7. ARIA (Accessible Rich Internet Applications)
*   **Brug ARIA med måde:** Den første regel om ARIA er: "Brug ikke ARIA, hvis du kan bruge et standard HTML-element".
*   **Vigtige attributter:**
    *   `aria-expanded="true/false"` til dropdown-menuer eller accordions.
    *   `aria-hidden="true"` på dekorative ikoner så skærmlæsere ignorerer dem.
    *   `aria-live="polite"` til dynamisk indhold, der opdateres uden side-reload (f.eks. søgeresultater).

---

### Verificerings-tjekliste for Accessibility Review
1. [ ] Kan jeg navigere gennem hele interfacet kun ved brug af tastaturet (Tab)?
2. [ ] Er der en tydelig ramme (focus-ring) om det element, jeg har valgt med tastaturet?
3. [ ] Har alle billeder en `alt` attribut (selv hvis den er tom)?
4. [ ] Er overskrifterne i korrekt rækkefølge (H1 -> H2 -> H3)?
5. [ ] Har alle knapper med ikoner en `.screen-reader-text` forklaring?
6. [ ] Er kontrasten på teksten høj nok til at blive læst nemt?
7. [ ] Har alle input-felter en tilhørende `<label>`?

---
