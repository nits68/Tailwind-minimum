# Keretek és Lekerekítések (Borders & Radius)

A Tailwindben a keretek (borders) kezelése nagyon logikusan épül fel: külön osztályok felelnek a vastagságért, a színért, a stílusért és a sarkok lekerekítéséért.

## 1. Keret vastagsága (Border Width) és Színe (Color)

Alapértelmezésben, ha csak a `border` osztályt használod, az egy 1px vastag, halványszürke keretet ad az elem minden oldalára. Ezt utána kedvedre módosíthatod.

- **Minden oldalra:** `border` (1px), `border-2` (2px), `border-4`, `border-8`.
- **Adott oldalra:** `border-t` (top), `border-b` (bottom), `border-l` (left), `border-r` (right). Hasonlóan működik a méretezés is: `border-b-2`.
- **Keret eltávolítása:** `border-0` (vagy pl. `border-b-0`, ha csak alulról akarod levenni).
- **Színek:** Ugyanaz a paletta, mint a szövegeknél vagy háttereknél: `border-{szín}-{árnyalat}` (pl. `border-red-500`).

**Példa (Figyelmeztető doboz piros bal oldali sávval):**
```html
<div class="border-l-4 border-red-500 bg-red-50 p-4">
  <p class="text-red-700">Figyelem: Fontos üzenet!</p>
</div>

```

## 2. Sarkok lekerekítése (Border Radius)

A `rounded` osztályokkal pillanatok alatt barátságosabbá teheted a felületeket.

* **Alapok:** `rounded-sm`, `rounded` (alap), `rounded-md`, `rounded-lg`, `rounded-xl`, `rounded-2xl`, `rounded-3xl`.
* **Teljes lekerekítés:** `rounded-full` (Tökéletes kör alakú profilképekhez vagy pirula alakú gombokhoz).
* **Adott sarkok:** `rounded-t-lg` (csak a felső két sarok), `rounded-r-md` (csak a jobb oldaliak), vagy akár egyetlen sarok: `rounded-tl-lg` (top-left).
* **Lekerekítés levétele:** `rounded-none`.

**Példa (Gomb és profilkép):**

```html
<button class="bg-blue-500 text-white px-4 py-2 rounded-lg">Gomb</button>
<img src="avatar.jpg" class="w-12 h-12 rounded-full border-2 border-gray-300" alt="Profil">

```

## 3. Keret stílusa (Border Style)

Az alapértelmezett stílus a folytonos vonal (`solid`), de van más is:

* `border-solid`: Folytonos (alapértelmezett).
* `border-dashed`: Szaggatott (pl. fájl feltöltő zónákhoz).
* `border-dotted`: Pontozott.
* `border-double`: Dupla vonal.

## 4. A titkos fegyver: `divide` (Osztóvonalak)

Ha van egy listád (vagy flex/grid elemeid egymás mellett/alatt), és vonalat akarsz tenni **közéjük** (de a legelső elé és a legutolsó után nem), a hagyományos CSS-sel ez elég macerás. A Tailwind `divide` osztálya egy pillanat alatt megoldja. Ezt mindig a **szülő** elemre kell tenni!

* **Függőleges listához:** `divide-y` (vízszintes vonalakat húz az elemek közé).
* **Vízszintes listához:** `divide-x` (függőleges vonalakat húz).
* **Szín megadása:** `divide-{szín}-{árnyalat}` (pl. `divide-gray-200`).

**Példa (Egy egyszerű, vonalakkal elválasztott lista):**

```html
<ul class="flex flex-col divide-y divide-gray-200 border border-gray-200 rounded-md">
  <li class="p-4">Első elem</li>
  <li class="p-4">Második elem</li>
  <li class="p-4">Harmadik elem</li>
</ul>

```

---

**💡 Tipp (Ring vs. Border):** A Tailwindben létezik egy `ring` nevű utility is (pl. `ring-2 ring-blue-500`). Ez vizuálisan nagyon hasonlít a borderre, de valójában `box-shadow`-t használ. A fő különbség: a `border` elfoglalja a helyet (megnöveli az elem fizikai méretét), míg a `ring` nem tolja el a többi elemet. Focus állapotoknál (pl. `focus:ring`) szinte mindig a `ring`-et érdemes használni `border` helyett, hogy ne "ugráljon" az elrendezés kattintáskor!