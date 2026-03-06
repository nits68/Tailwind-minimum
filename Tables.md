# Táblázatok (Tables)

A táblázatok formázása Tailwindben nagyrészt a cellák térközeinek (padding), a szegélyeknek (border) és a sorok háttérszínének beállításából áll.

## 1. Táblázat elrendezés (Table Layout)

A `<table class="...">` elemen két alapvető osztályt érdemes ismerni a szélesség kezelésére:

- `table-auto`: Az oszlopok szélessége a bennük lévő tartalomhoz igazodik (ez a leggyakoribb).
- `table-fixed`: Az oszlopok egyenlő szélességűek lesznek (hacsak nem adsz meg fix szélességet a `<th>` vagy `<td>` elemeken). Szuper hasznos, ha nem akarod, hogy egy hosszú szöveg "szétnyomja" a táblázatot.
- `w-full`: Szinte mindig érdemes rátenni, hogy a táblázat kitöltse a rendelkezésre álló helyet.

## 2. A fejléc (thead) és a cellák (th, td)

A fejlécet általában elkülönítjük egy finom háttérszínnel, más betűszínnel vagy vastagsággal. A celláknál a `p-*` (vagy `px-*`, `py-*`) osztályokkal adunk levegőt az adatoknak.

```html
<thead class="bg-gray-50 border-b border-gray-200">
  <tr>
    <th class="px-6 py-3 text-left text-sm font-semibold text-gray-900">Név</th>
    <th class="px-6 py-3 text-left text-sm font-semibold text-gray-900">Email</th>
  </tr>
</thead>

```

## 3. Zebra csíkozás és Hover effektek

A sorok (`<tr>`) formázására az állapot-prefixek (`even:`, `odd:`, `hover:`) a legjobb barátaid.

* `even:bg-gray-50`: Minden páros sor kap egy halvány szürke hátteret (zebra hatás).
* `hover:bg-gray-100`: Ha az egeret a sor fölé húzzák, kiemeli azt.

## 4. Elválasztó vonalak (divide)

Ahelyett, hogy minden egyes cellára vagy sorra egyenként tennél alsó keretet (`border-b`), használd a korábban tanult `divide-y` osztályt a táblázat törzsén (`<tbody>`)!

```html
<tbody class="divide-y divide-gray-200">
  <tr>...</tr>
  <tr>...</tr>
</tbody>

```

## 5. Reszponzív Táblázatok (A legfontosabb trükk!)

A táblázatok legnagyobb ellensége a mobil kijelző: a sok oszlop egyszerűen nem fér ki, és szétnyomja az oldal elrendezését.
**A megoldás:** Csomagold a teljes `<table ...>` elemet egy `<div>`-be, ami megkapja az **`overflow-x-auto`** osztályt. Így a táblázat mobilon vízszintesen görgethető lesz, de az oldal többi része nem törik szét.

---

## 🎯 Komplett, profi táblázat példa:

Ezt a kódot egy az egyben átmásolhatod, egy modern, letisztult (kicsit "Tailwind UI" stílusú) táblázatot kapsz eredményül:

```html
<div class="overflow-x-auto bg-white shadow-sm border border-gray-200 rounded-lg">
  <table class="w-full table-auto text-left">
    
    <thead class="bg-gray-50 border-b border-gray-200 text-sm text-gray-600">
      <tr>
        <th class="px-4 py-3 font-semibold">Név</th>
        <th class="px-4 py-3 font-semibold">Státusz</th>
        <th class="px-4 py-3 font-semibold">Szerepkör</th>
      </tr>
    </thead>
    
    <tbody class="divide-y divide-gray-200 text-sm text-gray-800">
      <tr class="hover:bg-gray-50 transition-colors">
        <td class="px-4 py-3 font-medium">Kovács János</td>
        <td class="px-4 py-3"><span class="bg-green-100 text-green-700 px-2 py-1 rounded-full text-xs">Aktív</span></td>
        <td class="px-4 py-3 text-gray-500">Admin</td>
      </tr>
      <tr class="hover:bg-gray-50 transition-colors">
        <td class="px-4 py-3 font-medium">Nagy Anna</td>
        <td class="px-4 py-3"><span class="bg-red-100 text-red-700 px-2 py-1 rounded-full text-xs">Inaktív</span></td>
        <td class="px-4 py-3 text-gray-500">Felhasználó</td>
      </tr>
    </tbody>
    
  </table>
</div>

```

---

**💡 Tipp:** Vedd észre a státusz oszlopban lévő trükköt! A "Badges" (jelvények) vagy címkék (mint az "Aktív") készítéséhez tökéletes kombó a kis padding, a kerekítés és egy háttérszín a megfelelő szövegszínnel (pl. `bg-green-100 text-green-700 px-2 py-1 rounded-full text-xs`). Ezt táblázatokon kívül is rengetegszer fogod használni!
