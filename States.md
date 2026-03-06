# Állapotok (Hover, Focus és társai)

A Tailwindben a CSS pseudo-osztályok (mint a `:hover` vagy `:focus`) használatához csak a megfelelő prefixet és egy kettőspontot kell tenned az osztály neve elé (pl. `hover:bg-blue-600`). Ezt *bármelyik* osztállyal megteheted, nem csak színekkel!

## A leggyakoribb állapotok

- `hover:`: Amikor az egeret az elem fölé húzzák.
- `focus:`: Amikor az elem (pl. egy input mező vagy gomb) aktív fókuszt kap (kattintással vagy Tab billentyűvel).
- `active:`: A kattintás (vagy lenyomás) pontos pillanata.
- `disabled:`: Amikor az elem (pl. gomb vagy input) `disabled` attribútummal rendelkezik. Ilyenkor érdemes halványabb színt és más kurzort beállítani.

**Példa (Egy gomb teljes életciklusa):**
```html
<button class="bg-blue-500 text-white py-2 px-4 rounded 
               hover:bg-blue-600 
               active:bg-blue-700 
               focus:outline-none focus:ring-2 focus:ring-blue-400 
               disabled:bg-gray-400 disabled:cursor-not-allowed">
  Kattints rám!
</button>

```

## A titkos fegyver: `group-hover`

Gyakori probléma, hogy van egy kártyád (szülő elem), és ha az egeret a *kártya* fölé húzzák, a benne lévő *gyerek* elem (pl. egy ikon vagy szöveg) színét akarod megváltoztatni. Erre való a `group`.

1. Tedd a `group` osztályt a **szülő** elemre.
2. Használd a `group-hover:` prefixet a **gyerek** elemen.

**Példa (Kártya hover hatás):**

```html
<div class="group border p-6 hover:bg-blue-50">
  <h3 class="text-gray-900 group-hover:text-blue-600">Kártya címe</h3>
  <p class="text-gray-500">Ez a szöveg marad szürke, de a cím kék lesz, ha a kártyára viszed az egeret.</p>
</div>

```

## További hasznos állapotok

* `focus-within:`: A szülő elemen használatos. Akkor aktiválódik, ha *bármelyik* gyerekeleme (pl. egy input a formban) fókuszt kap. Kiváló egyedi keresőmezők építéséhez.
* `first:`, `last:`, `odd:`, `even:`: Listaelemek (pl. `<li>` vagy táblázat sorok `<tr>`) célzására. Szuper hasznos "zebra" csíkozású táblázatokhoz (`even:bg-gray-100`).

## Átmenetek (Transitions) - Hogy ne legyen darabos

Az állapotváltozások (pl. színváltás hoverre) alapértelmezésben azonnaliak. Ha profi, lágy hatást szeretnél, add hozzá az elemhez a `transition` osztályokat is!

* `transition` vagy `transition-colors`: Bekapcsolja a lágy átmenetet.
* `duration-{ms}`: Az átmenet hossza milliszekundumban (pl. `duration-200` vagy `duration-300`).

**Példa:**

```html
<a href="#" class="text-gray-500 hover:text-blue-500 transition-colors duration-300">
  Lágyan váltok színt
</a>

```

---

**💡 Tipp:** Az állapotokat kombinálhatod is más prefixekkel, például reszponzív nézetekkel. Így leírhatod, hogy egy gomb *csak nagy képernyőn, hover esetén* legyen piros: `md:hover:bg-red-500`.
