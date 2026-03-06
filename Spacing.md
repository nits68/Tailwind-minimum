# Spacing és Méretezés

A Tailwind egy arányos méretskálát használ. Alapszabály: **1 egység = 0.25rem (4px)**.
Tehát a leggyakrabban használt `4`-es érték pontosan `1rem` vagyis `16px`. (pl. `p-4`, `m-4`, `w-4`, `h-4`).

## Padding (Belső margó/térköz-"bélés") és Margin (Külső margó/térköz)

A szintaxis nagyon logikus: `{tulajdonság}{irány}-{méret}`.

**Tulajdonságok:**
- `p`: Padding (a tartalom és a keret közötti távolság)
- `m`: Margin (az elem és a többi elem közötti távolság)

**Irányok:**
- *Nincs irány (pl. `p-4`)*: Minden oldalra (Top, Right, Bottom, Left).
- `x`: Vízszintes (bal és jobb, pl. `px-4`).
- `y`: Függőleges (alsó és felső, pl. `my-8`).
- `t`: Top (fent) | `b`: Bottom (lent) | `l`: Left (bal) | `r`: Right (jobb).

**Példa:**
```html
<div class="py-4 px-8 mb-6 bg-white shadow">
  Tartalom
</div>

```

**Negatív Margin:**
Ha egy elemet rá akarsz húzni egy másikra, használj mínusz jelet a prefix előtt: `-mt-4` (margin-top: -1rem).

## Width (Szélesség) és Height (Magasság)

Az alap skálán (`w-4`, `h-8` stb.) felül vannak speciális, százalékos és képernyőhöz igazodó értékek is.

* `w-full` / `h-full`: 100% (kitölti a szülő elem méretét).
* `w-screen` / `h-screen`: 100vw / 100vh (kitölti a teljes képernyőt).
* Törtek: `w-1/2` (50%), `w-1/3` (33.3%), `w-2/3` (66.6%) stb.
* `min-h-screen`: Legalább a képernyő magassága (nagyon hasznos a fő konténernél, hogy a footer mindig alul maradjon).

**Példa:**

```html
<div class="w-1/2 h-16 bg-blue-500">...</div>

```

## "Menekülőút": Egyedi értékek (Arbitrary Values)

Ha a dizájn megkíván egy olyan méretet, ami nincs benne a Tailwind skálájában (pl. pontosan 117px kell), használd a szögletes zárójeleket. Ez az esetek 20%-ában fog kelleni, de olyankor életmentő.

```html
<div class="w-[117px] mt-[13px] p-[5%]">...</div>

```

---

**💡 Tippek a mindennapokra:**

* `mx-auto`: Ez a leggyorsabb módja egy fix szélességű blokk középre igazításának (pl. `w-full max-w-7xl mx-auto`).
* Ha elemek közötti távolságot akarsz megadni, Flexbox vagy Grid esetén **mindig a `gap-*` osztályt használd** a szülőn, ahelyett, hogy a gyerekekre egyenként margókat (`m-*`) tennél! Ez sokkal tisztább kódot eredményez.
