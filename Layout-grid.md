# Layout: Grid

A CSS Grid tökéletes eszköz a kétdimenziós (sorokat és oszlopokat is tartalmazó) elrendezések létrehozására. A Tailwind rendkívül egyszerűvé teszi a használatát a `grid` utility osztállyal.

## Alapok

Ahhoz, hogy a Grid bekapcsoljon, a szülő elemen használd a `grid` osztályt. Ezután meg kell adnod, hány oszlopot szeretnél.

- `grid`: Bekapcsolja a grid elrendezést.
- `grid-cols-{n}`: Meghatározza az oszlopok számát (pl. `grid-cols-3` = 3 egyenlő oszlop).
- `gap-{n}`: Beállítja a távolságot az elemek között (sorok és oszlopok között is).

**Példa (3 oszlopos elrendezés):**
```html
<div class="grid grid-cols-3 gap-4">
  <div class="bg-blue-200 p-4">1. Elem</div>
  <div class="bg-blue-300 p-4">2. Elem</div>
  <div class="bg-blue-400 p-4">3. Elem</div>
</div>
```


## Cellák összevonása (Spanning)

Gyakran előfordul, hogy egy elemnek szélesebbnek kell lennie a többinél. Erre valók a `col-span-*` osztályok.

* `col-span-{n}`: Az elem `n` oszlopnyi helyet foglal el.
* `col-span-full`: Az elem a teljes elérhető szélességet (minden oszlopot) kitölti.

**Példa:**

```html
<div class="grid grid-cols-3 gap-4">
  <div class="col-span-2 bg-green-200">Két oszlopot foglal el</div>
  <div class="bg-green-300">Egy oszlopot foglal el</div>
  <div class="col-span-full bg-green-400">Teljes szélességű (3 oszlop)</div>
</div>

```

## Reszponzív Grid (A Tailwind szuperereje)

A Tailwind "Mobile-First" (mobilra tervezett) megközelítést alkalmaz. Alapértelmezésben érdemes 1 oszloppal kezdeni, és csak nagyobb képernyőkön növelni az oszlopok számát a breakpoint prefixek (`sm:`, `md:`, `lg:`, `xl:`) segítségével.

**Példa (1 oszlop mobilon, 2 tableten, 4 asztali gépen):**

```html
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
  <div class="bg-red-200">Kártya 1</div>
  <div class="bg-red-200">Kártya 2</div>
  <div class="bg-red-200">Kártya 3</div>
  <div class="bg-red-200">Kártya 4</div>
</div>

```

## Sorok kezelése (Opcionális)

Legtöbbször a sorok magasságát a tartalom határozza meg, de ha explicit módon kell sorokat definiálni:

* `grid-rows-{n}`: Sorok számának megadása.
* `row-span-{n}`: Több soron átívelő elem.

```html
<div class="grid grid-rows-3 grid-flow-col gap-4">
  <div class="row-span-3">Bal oldali, magas elem</div>
  <div class="col-span-2">Jobb felső</div>
  <div class="col-span-2 row-span-2">Jobb alsó, nagyobb elem</div>
</div>

```

---

**💡 Tipp:** Ha az esetek 80%-át akarod lefedni, csak tanuld meg a `grid`, `grid-cols-*`, `gap-*` és a `col-span-*` használatát. Ezekkel szinte bármilyen modern layout felépíthető!
