# Hátterek (Backgrounds)

A szimpla háttérszíneket (`bg-blue-500`) már érintettük, de a Tailwind rengeteg eszközt ad a háttérképek, színátmenetek és rétegek (overlay) kezelésére is. Ezekkel pillanatok alatt feldobhatsz egy unalmas szekciót.

## Háttérképek és viselkedésük

Ha beállítasz egy háttérképet (akár a konfigurációban, akár "menet közben" szögletes zárójelekkel: `bg-[url('...')]`), három dolgot szinte biztosan meg kell adnod: a méretet, a pozíciót és az ismétlődést.

- **Méret (Size):**
  - `bg-cover`: A kép kitölti a teljes rendelkezésre álló helyet (előfordulhat, hogy a szélei le lesznek vágva, de sosem lesz üres sáv a konténerben). **Ez kell az esetek 90%-ában!**
  - `bg-contain`: A kép teljes egészében látszódni fog, anélkül, hogy torzulna vagy levágódna (de lehetnek mellette üres sávok).
  - `bg-auto`: A kép az eredeti, natív méretében jelenik meg.

- **Pozíció (Position):**
  - `bg-center`, `bg-top`, `bg-bottom`, `bg-left`, `bg-right`.
  - Ezzel szabályzod, hogy ha a kép egy része levágódik (pl. a `bg-cover` miatt), melyik része maradjon biztosan fókuszban.

- **Ismétlődés (Repeat):**
  - `bg-no-repeat`: Ne ismétlődjön a kép (alapvető fontosságú háttérképeknél).
  - `bg-repeat`, `bg-repeat-x`, `bg-repeat-y`: Ha mintázatot (pattern) használsz.

**Példa (Egy klasszikus "Hero" szekció háttere, ami kitölti a képernyőt):**
```html
<div class="h-screen bg-[url('/img/hero.jpg')] bg-cover bg-center bg-no-repeat">
  <h1 class="text-white">Üdv az oldalon!</h1>
</div>

```

## Színátmenetek (Gradients)

A Tailwind beépített színátmenet-kezelője fantasztikus. Csak meg kell adnod az irányt és a színeket.

1. **Irány:** `bg-gradient-to-t` (fel), `bg-gradient-to-r` (jobbra), `bg-gradient-to-b` (le), `bg-gradient-to-l` (balra), vagy az átlók (pl. `bg-gradient-to-br` - jobb le).
2. **Színek:** `from-{szín}`, `via-{szín}` (opcionális, középső szín), `to-{szín}`.

**Példa (Elegáns, kékből lilába átmenő gomb):**

```html
<button class="bg-gradient-to-r from-blue-500 to-purple-600 text-white px-6 py-2 rounded shadow-lg">
  Kattints rám
</button>

```

## Háttér elhomályosítása (Glassmorphism / Üveg hatás)

Gyakori dizájn trend, amikor egy elem áttetsző, és a mögötte lévő háttér elmosódik. Ezt a `backdrop-blur` osztályokkal érheted el. Fontos, hogy magának a háttérszínnek is áttetszőnek kell lennie (pl. `bg-white/30`).

**Példa (Üveg hatású kártya egy színes háttéren):**

```html
<div class="bg-[url('hatter.jpg')] bg-cover bg-center p-10">
  <div class="bg-white/30 backdrop-blur-md p-6 rounded-lg border border-white/20">
    <h2 class="text-black font-bold">Jól olvasható szöveg az üvegen</h2>
  </div>
</div>

```

---

**💡 Tipp (Sötétítő réteg / Overlay):** Ha a háttérképed túl világos, és nem olvasható rajta a fehér szöveg, a leggyorsabb trükk, ha egy sötétből átlátszóba menő színátmenetet húzol rá. Ha a Tailwind konfiguráció nélkül akarod megoldani, használj egy belső div-et, ami ráborul a képre:
`<div class="absolute inset-0 bg-black/50"></div>`. Így tökéletes kontrasztot kapsz a szövegednek!
