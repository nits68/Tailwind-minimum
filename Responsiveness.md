# Reszponzivitás (Mobil-első megközelítés)

A Tailwind CSS **"Mobile-First"** elvet követi. Ez azt jelenti, hogy a prefix (előtag) nélküli osztályok (pl. `text-center` vagy `w-full`) minden képernyőméreten érvényesek, a legkisebb mobiltól kezdve. A prefixekkel (`sm:`, `md:`, `lg:` stb.) pedig felülírhatod ezeket a viselkedéseket a *nagyobb* képernyőkön.



## A beépített töréspontok (Breakpoints)

A Tailwind öt alapértelmezett töréspontot biztosít, amik lefedik a modern eszközöket:

- `sm:` (640px-től felfelé): Nagyobb mobilok fektetve, kis tabletek.
- `md:` (768px-től felfelé): Tabletek (Portré).
- `lg:` (1024px-től felfelé): Laptopok, asztali monitorok.
- `xl:` (1280px-től felfelé): Nagy asztali monitorok.
- `2xl:` (1536px-től felfelé): Extra nagy monitorok és TV-k.

## Hogyan gondolkodj Tailwindben?

1. Először dizájnd meg a mobil nézetet (prefix nélküli osztályokkal).
2. Utána növeld a böngészőablak méretét, és ahol "szétesik" vagy már túl üres a dizájn, ott avatkozz be a megfelelő prefixszel (pl. `md:`).

**❌ Rossz megközelítés (Asztali-első):**
`<div class="lg:w-1/2 w-full">` -> Bár működhet, nehezebb olvasni és nem ez a Tailwind útja.

**✅ Jó megközelítés (Mobil-első):**
`<div class="w-full lg:w-1/2">` -> Mobilon alapból 100%, és *csak* laptop mérettől lesz 50%.

## Gyakori reszponzív minták

### 1. Elrendezés megváltoztatása (Egymás alól egymás mellé)
A legtipikusabb eset: mobilon oszlopba rendezzük a tartalmat, nagyobb képernyőn sorba.

```html
<div class="flex flex-col md:flex-row gap-4">
  <div class="bg-red-200 p-4">Felső mobilon / Bal oldali gépen</div>
  <div class="bg-blue-200 p-4">Alsó mobilon / Jobb oldali gépen</div>
</div>

```

### 2. Elemek elrejtése és megjelenítése (Hamburger menü logika)

Sokszor van olyan elem, ami mobilon nem fér ki (pl. egy hosszú navigációs menü), ezért elrejtjük, de asztali gépen megmutatjuk.

* `hidden`: Elrejti az elemet (`display: none`).
* `block` / `flex` / `grid`: Újra megjeleníti (felülírja a hidden-t).

```html
<nav class="flex justify-between p-4 bg-gray-100">
  <div class="font-bold">Logó</div>
  
  <ul class="hidden md:flex gap-4">
    <li>Kezdőlap</li>
    <li>Rólunk</li>
  </ul>
  
  <button class="md:hidden p-2 bg-gray-200 rounded">☰ Menü</button>
</nav>

```

### 3. Rács (Grid) sűrítése

Képgalériáknál vagy termékkártyáknál klasszikus eset: mobilon 1 oszlop, tableten 2, asztali gépen 3 vagy 4.

```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
  <div class="bg-green-100 p-6">Kártya 1</div>
  <div class="bg-green-100 p-6">Kártya 2</div>
  <div class="bg-green-100 p-6">Kártya 3</div>
  <div class="bg-green-100 p-6">Kártya 4</div>
</div>

```

---

**💡 Tipp:** Nem kell minden egyes töréspontot használnod! Az esetek 80%-ában bőven elég a prefix nélküli (mobil) alap, és egy `md:` vagy `lg:` prefix a nagyobb nézetekhez. Ne bonyolítsd túl a kódot felesleges `sm:` és `xl:` lépcsőkkel, ha nem muszáj!
