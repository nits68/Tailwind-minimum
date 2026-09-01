# Box Alignment

A Tailwind CSS segítségével a Flexbox és a Grid elrendezések igazítása hihetetlenül egyszerű. Nem kell többé bonyolult CSS szabályokkal bajlódnod, pár osztállyal tökéletesen pozicionálhatod az elemeidet mind vízszintesen, mind függőlegesen.

## Igazítás a Főtengelyen (Justify Content)

A `justify-*` osztályokkal szabályozhatod, hogyan helyezkedjenek el az elemek a főtengely mentén. Flexbox esetében ez alapértelmezés szerint a vízszintes tengelyt jelenti (de `flex-col` esetén a függőlegeset).

* **`justify-start`**: Elemek a tartály elejére igazítva (alapértelmezett).
* **`justify-center`**: Elemek pontosan középre igazítása.
* **`justify-end`**: Elemek a tartály végére (jobb szélére) tolva.
* **`justify-between`**: Egyenletes eloszlás: az első elem a kezdőponton, az utolsó a végponton tapad, a többi között egyenlő a hely.
* **`justify-around` / `justify-evenly**`: Egyenletes térközök az elemek körül (a széleken is marad hely).

## Igazítás a Kereszttengelyen (Align Items)

Az `items-*` osztályok a kereszttengely mentén (soroknál ez a függőleges tengely) igazítják a flex vagy grid elemeket.

* **`items-start`**: Elemek a tartály tetejére (kereszttengely elejére) igazítva.
* **`items-center`**: Elemek függőlegesen középre igazítva.
* **`items-end`**: Elemek a tartály aljára igazítva.
* **`items-stretch`**: Az elemek kitöltik a rendelkezésre álló magasságot (alapértelmezett, ha nincs megadva fix magasság).
* **`items-baseline`**: Az elemek a bennük lévő szöveg alapvonalához igazodnak.

**Példa (Flexbox igazítás):**

```html
<div class="flex justify-between items-center bg-gray-100 p-4 h-24">
  <div class="bg-blue-600 text-white p-2">Balra</div>
  <div class="bg-blue-600 text-white p-2">Középen és függőlegesen is!</div>
  <div class="bg-blue-600 text-white p-2">Jobbra</div>
</div>

```

## Gyermek elemek egyedi igazítása (Align Self)

Ha csak egyetlen elemet szeretnél máshogy igazítani, mint a konténer többi elemét (felülbírálva a szülő `items-*` beállítását), a `self-*` osztályokat használd közvetlenül a gyermek elemen.

* **`self-auto`**: Követi a szülő beállítását.
* **`self-start`, `self-center`, `self-end`, `self-stretch**`: Ugyanúgy működnek, mint az `items-*`, de csak a kiválasztott gyermek elemre hatnak.

**Példa (Egyedi igazítás a sorban):**
Ebben a példában a szülő konténer alapból a tetejére (`items-start`) igazítja az elemeket, de a második elem középre, a harmadik pedig az aljára kényszeríti magát.

```html
<div class="flex items-start bg-gray-100 p-4 h-32 gap-4">
  <div class="bg-blue-400 text-white p-2">Alap (Fent)</div>
  <div class="bg-red-500 text-white p-2 self-center">Középre kényszerítve</div>
  <div class="bg-green-500 text-white p-2 self-end">Alulra kényszerítve</div>
</div>
```

## Többsoros Tartalom (Align Content)

Ha az elemeid több sorba törnek (például a `flex-wrap` használata miatt), a `content-*` osztályokkal maguknak a *soroknak* az eloszlását és távolságát szabályozhatod.

* **`content-start`**: Minden sor a tartály tetejére gyűlik.
* **`content-center`**: A sorok egy tömbben, középen helyezkednek el.
* **`content-between`, `content-around`, `content-evenly**`: A sorok egyenletesen eloszlanak a rendelkezésre álló függőleges térben.

**Példa (Sorok elosztása egy magas dobozban):**
Itt a doboz direkt magasabb (`h-48`, azaz 192px), az elemek pedig több sorba törnek (`flex-wrap`). A `content-between` gondoskodik róla, hogy az első sor a doboz tetejére, az alsó pedig az aljára tapadjon.

```html
<div class="flex flex-wrap content-between bg-gray-100 p-4 h-48">
  <div class="w-5/12 bg-purple-500 text-white p-2 m-1">1. Elem (Felső sor)</div>
  <div class="w-5/12 bg-purple-500 text-white p-2 m-1">2. Elem (Felső sor)</div>
  <div class="w-5/12 bg-purple-600 text-white p-2 m-1">3. Elem (Alsó sor)</div>
  <div class="w-5/12 bg-purple-600 text-white p-2 m-1">4. Elem (Alsó sor)</div>
</div>
```
---

**💡 Tippek:**

* Ha egy elemet tökéletesen a képernyő (vagy egy doboz) közepére szeretnél igazítani vízszintesen és függőlegesen is, a klasszikus "varázsige": `class="flex items-center justify-center min-h-screen"`.
* Ne feledkezz meg a **`gap-{méret}`** (pl. `gap-4`) osztályról! Ez a legtisztább és legmodernebb módja annak, hogy egyenletes távolságot tarts az elemek között anélkül, hogy marginokkal (margókkal) kellene trükköznöd az egyes elemeken.

