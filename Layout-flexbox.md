# Layout: Flexbox

A Flexbox (Rugalmas Dobozmodell) egydimenziós elrendezésekhez készült. Tökéletes navigációs sávokhoz, gombok egymás mellé/alá rendezéséhez, vagy elemek igazításához.

## Alapok és Irányok

A szülő elemen a `flex` osztály bekapcsolja a Flexboxot. Alapértelmezésben az elemek balról jobbra, egy **sorban** fognak elhelyezkedni.

- `flex`: Bekapcsolja a flexbox elrendezést.
- `flex-col`: Egymás alá (oszlopba) rendezi az elemeket.
- `flex-row`: Egymás mellé (sorba) rendezi az elemeket (ez az alapértelmezett).
- `gap-{n}`: Távolság az elemek között (ugyanúgy, mint a Gridnél).

**Példa (Oszlop elrendezés mobilon, sor asztali gépen):**
```html
<div class="flex flex-col md:flex-row gap-4">
  <div class="bg-blue-200 p-4">Első</div>
  <div class="bg-blue-300 p-4">Második</div>
  <div class="bg-blue-400 p-4">Harmadik</div>
</div>

```

## Igazítás a Főtengelyen (justify-*)

Ha sorba rendezted az elemeket (vízszintesen), a `justify-*` osztályokkal határozhatod meg, hogyan ossza el a maradék helyet az X tengelyen (oszlop elrendezés esetén az Y tengelyen).

* `justify-start`: Balra igazít (alapértelmezett).
* `justify-center`: Középre igazít.
* `justify-end`: Jobbra igazít.
* `justify-between`: A két szélső elem a szélekre tapad, a többi egyenletesen elosztva középen.
* `justify-around`: Egyenlő távolságot hagy az elemek körül (így a konténer két szélén is marad egy kis üres hely)

**Példa (Navigációs sáv logóval balra, menüvel jobbra):**

```html
<div class="flex justify-between p-4 bg-gray-100">
  <div>Logó</div>
  <div class="flex gap-4">
    <a href="#">Rólunk</a>
    <a href="#">Kapcsolat</a>
  </div>
</div>

```

## Igazítás a Kereszttengelyen (Items)

A kereszttengely a főtengelyre merőleges (sor esetén a függőleges (Y) tengely). Az `items-*` osztályok felelnek érte.

* `items-start`: Felülre igazít.
* `items-center`: Függőlegesen középre igazít (nagyon gyakori!).
* `items-end`: Alulra igazít.
* `items-stretch`: Kinyújtja az elemeket, hogy kitöltsék a rendelkezésre álló magasságot (alapértelmezett).

**Példa (Tökéletesen középre igazított tartalom X és Y tengelyen is):**

```html
<div class="flex justify-center items-center h-64 bg-gray-200">
  <div class="p-6 bg-white rounded shadow">Pontosan középen vagyok!</div>
</div>

```

## Méretezés és Sortörés

* `flex-1`: Az elem kitölti a rendelkezésre álló maradék helyet. Ha több elem is `flex-1`, akkor egyenlően osztoznak.
* `flex-wrap`: Ha az elemek nem férnek ki egy sorba, a `flex-wrap` engedi őket a következő sorba törni (alapértelmezésben a flexbox megpróbál mindent egy sorba zsúfolni).
* `flex-none`: Az elem pontosan akkora marad, amekkora a tartalma (vagy a megadott width/height). Nem fog megnőni a maradék helyre, és nem is megy össze, ha szűkös a hely.
* `flex-initial`: Alapértelezés. Az elem nem nő meg, hogy kitöltse a maradék helyet, de össze tud zsugorodni, ha nincs elég hely a képernyőn.
* ``flex-auto`: Figyelembe veszi az elem eredeti méretét, de utána szabadon megnőhet vagy összezsugorodhat a maradék hely függvényében.

**Példa (Input mező és gomb, ahol az input kitölti a maradék helyet):**

```html
<div class="flex gap-2">
  <input type="text" class="flex-1 border p-2" placeholder="Keresés...">
  <button class="bg-blue-500 text-white p-2">Gomb</button>
</div>

```

---

**💡 Tipp:** A leggyakoribb varázsige, amit Tailwindben használni fogsz, a `flex items-center gap-2` (vagy más gap érték). Ez tökéletes ikonok és szövegek, vagy gombok egymás mellé igazítására, hogy függőlegesen ne csússzanak el egymáshoz képest.
