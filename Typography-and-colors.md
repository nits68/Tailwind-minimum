# Tipográfia és Színek

A Tailwind egy rendkívül gazdag, előre definiált színpalettát és tipográfiai skálát ad a kezedbe, amivel percek alatt profi megjelenést érhetsz el.

## Színek (Colors)

A színek elnevezése következetes: a szín neve után jön az árnyalat sötétsége egy **50-től 950-ig terjedő skálán** (ahol az 50 a legvilágosabb, majdnem fehér, a 950 pedig a majdnem fekete). 

Ugyanezt a színskálát használhatod szövegre, háttérre és keretekre is:

- **Szöveg:** `text-{szín}-{árnyalat}` (pl. `text-blue-500`, `text-gray-900`)
- **Háttér:** `bg-{szín}-{árnyalat}` (pl. `bg-red-100`, `bg-green-700`)
- **Keret:** `border-{szín}-{árnyalat}` (pl. `border-gray-300`)
- **Fehér/Fekete:** `text-white`, `bg-black`, `text-transparent` (átlátszó).

**Opacitás (Átlátszóság) módosítása:**
Bármelyik szín végére tehetsz egy perjelet és egy százalékos értéket, hogy áttetszővé tedd:
`bg-black/50` (50%-ban átlátszó fekete háttér) vagy `text-blue-500/80`.

**Példa (Gomb stílus):**
```html
<button class="bg-blue-600 text-white border border-blue-700">Küldés</button>

```

## Tipográfia (Szövegformázás)

A Tailwind a betűméretek (`font-size`) beállításakor a sorközt (`line-height`) is automatikusan, arányosan állítja, így ezzel ritkán kell külön foglalkoznod.

### Betűméretek (Font Size)

* `text-xs`, `text-sm`: Kisebb, kiegészítő szövegek.
* `text-base`: Alapértelmezett méret (16px).
* `text-lg`, `text-xl`, `text-2xl` ... `text-9xl`: Címsorok és kiemelések.

### Betűvastagság (Font Weight)

* `font-light`: Vékony.
* `font-normal`: Normál (alapértelmezett).
* `font-medium`: Közepesen vastag.
* `font-semibold`: Félkövér (gyakran jobb gombokhoz, mint a sima bold).
* `font-bold`, `font-extrabold`: Vastag / Nagyon vastag.

### Betűtípusok (Font Family)

* `font-sans`: Sans-serif (talpatlan, ez az alapértelmezett).
* `font-serif`: Serif (talpas, elegánsabb, cikkekhez jó).
* `font-mono`: Monospace (egyenlő szélességű karakterek). **Kifejezetten hasznos kódblokkokhoz vagy adatok táblázatos megjelenítéséhez.**

### Igazítás (Text Alignment)

* `text-left`, `text-center`, `text-right`, `text-justify`.

## Szóközök és Sortörések (Whitespace)

Amikor dinamikus adatokat (pl. adatbázisból jövő szöveget vagy kód részleteket) jelenítesz meg, fontos lehet, hogyan kezeli a böngésző a szóközöket és entereket.

* **`whitespace-pre`**: Megtartja a szövegben lévő eredeti sortöréseket (entereket) és a többszörös szóközöket is. Pontosan úgy jeleníti meg, ahogy a forráskódban/változóban szerepel. (Gyakran használják a `font-mono`-val együtt `<pre>` tageken belül).
* **`whitespace-nowrap`**: Megakadályozza, hogy a szöveg a következő sorba törjön (akkor is, ha kifogyna a helyből). Hasznos gomboknál vagy egy soros kártya-címeknél, ahol inkább elrejtjük a végét (`truncate` osztállyal).

**Példa (Kódblokk megjelenítés):**

```html
<div class="bg-gray-900 text-gray-100 p-4 rounded">
  <pre class="font-mono whitespace-pre text-sm">
function hello() {
    console.log("Hello Világ!");
}
  </pre>
</div>

```

---

**💡 Tippek:**

* Ha a szöveg túl hosszú és ki akar lógni a dobozból, a **`truncate`** osztály egyetlen szóval megoldja: egy sorba kényszeríti a szöveget, és a végére "..."-ot tesz, ha nem fér ki.
* Színátmenetes szöveget is csinálhatsz! Így néz ki a kombó: `bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent`.
