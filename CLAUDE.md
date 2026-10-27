# CLAUDE.md

## Projekt
Interaktivní webová aplikace pro učení angličtiny pro české uživatele. Uživatel zadá svou úroveň (A1–C2) a aplikace podle ní nabídne slovíčka, kvíz a doplňování vět. Hostuje se na GitHub Pages.

## Struktura
- `index.html` – celá aplikace (HTML + CSS + JS v jednom souboru; název vyžaduje GitHub Pages). Bez build kroku a bez externích závislostí.
  - `<style>` – vzhled, světlý/tmavý režim přes CSS proměnné.
  - `LEVELS` – data (slovíčka a věty) oddělená od logiky.
  - Stav a `localStorage` – klíče `level` a `stats`.
  - Pohledy: `viewLevel`, `viewCards`, `viewQuiz`, `viewFill`, `viewStats`; přepíná je `show(view)`.
- `README.md` – popis pro uživatele.

## Konvence
- Uživatelské rozhraní je česky, obsah cvičení anglicky.
- Kód: názvy proměnných a funkcí anglicky, `camelCase`; komentáře krátké.
- Text z dat vždy vkládat do HTML přes `esc()`.
- Přístupnost: ovladatelné klávesnicí, viditelný focus, `aria-live` pro zpětnou vazbu.
- Responzivní layout (mobil i desktop); žádné externí knihovny ani CDN.
- Zápis do `localStorage` vždy přes objekt `store` (ošetřuje chyby).

## Přidání obsahu
V objektu `LEVELS` u dané úrovně:
- slovíčko: přidat do `words` trojici `["anglicky", "česky", "Krátká anglická věta se slovem."]` (věta se zobrazí pod kartičkou);
- čtení nahlas zajišťuje funkce `speak()` (Web Speech API, `en-GB`);
- věta: přidat do `sentences` trojici `["Věta s ___.", "správná odpověď", "český překlad"]`.
Pro kvíz je potřeba alespoň 4 slovíčka na úroveň.

## Spuštění a test
Otevřít `index.html` v prohlížeči (nebo `python -m http.server` a http://localhost:8000). Ručně ověřit: výběr úrovně a její zapamatování po obnovení, otáčení kartiček, kvíz (klávesy 1–4), doplňování, statistiky, mobilní šířku.

## Git
Větev `main`, vzdálený repozitář `origin`. Po každé ucelené změně commit s popisnou zprávou a push.

## Plánovaná rozšíření
- Více slovíček a vět na úroveň (cíl 50+).
- Výslovnost přes Web Speech API.
- Opakování chybných odpovědí (spaced repetition).
- Další typy cvičení (poslech, řazení slov ve větě).
- Přepínač světlého/tmavého režimu a export/import pokroku.
