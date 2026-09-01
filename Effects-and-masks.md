# Effektek és Maszkok

A Tailwind egyszerű utility osztályokat biztosít a leggyakoribb CSS vizuális effektekhez (árnyékok, átlátszóság), valamint a haladóbb képhatású keverési módokhoz (blend modes) és maszkoláshoz.

## 1. Árnyékok (Box Shadow)

Az árnyékok mélységet adnak a dizájnnak, "kiemelik" az elemeket a síkból. A skála a `sm`-től a `2xl`-ig terjed, plusz a belső árnyék.

- **Alapok:** `shadow-sm`, `shadow`, `shadow-md` (leggyakoribb), `shadow-lg`, `shadow-xl`, `shadow-2xl`.
- **Belső árnyék:** `shadow-inner` (belesüllyeszti az elemet a háttérbe).
- **Árnyék eltávolítása:** `shadow-none`.
- **Árnyék színe (v3+):** `shadow-{szín}-{árnyalat}` (pl. `shadow-blue-500/50` - kék árnyék 50% átlátszósággal).

**Példa (Interaktív kártya kiemelése hoverre):**
```html
<div class="p-6 bg-white rounded-lg shadow-md transition-shadow duration-300 hover:shadow-xl">
  Húzd fölém az egeret!
</div>

```

## 2. Átlátszóság (Opacity)

Az egész elem átlátszóságát szabályozza, beleértve a tartalmát (szöveget, képeket) is.

* **Skála:** `opacity-0` (teljesen átlátszó, de ott van), `opacity-25`, `opacity-50`, `opacity-75`, `opacity-100` (teljesen látszik).

**Példa (Halványuló gomb disabled állapotban):**

```html
<button class="bg-blue-500 text-white px-4 py-2 rounded disabled:opacity-50" disabled>
  Nem kattinthatsz rá
</button>

```

## 3. Keverési módok (Blend Modes)

Meghatározza, hogyan keveredjen egy elem tartalma az alatta lévő háttérrel (mint a Photoshop rétegei). Két fő típusa van:

* **Background Blend Mode:** Az elem saját háttérképe keveredik az elem saját háttérszínével.
* `bg-blend-multiply` (szorzat), `bg-blend-screen` (képernyő), `bg-blend-overlay` (átfedés) stb.


* **Mix Blend Mode:** Az elem teljes tartalma keveredik a *szülője* hátterével.
* `mix-blend-multiply`, `mix-blend-screen`, `mix-blend-difference` (különbség - pl. fekete-fehér invertáláshoz).



**Példa (Sötétített háttérkép `multiply`-jal):**

```html
<div class="w-full h-64 bg-blue-900 bg-[url('kep.jpg')] bg-cover bg-blend-multiply">
  <h1 class="text-white p-10">Cím a képen</h1>
</div>

```

## 4. Szűrők (Filters)

A `blur-*`-hoz hasonló szűrők közvetlenül az elemre (és a tartalmára) hatnak, nem csak a mögötte lévő háttérre (azzal ellentétben, amit a `backdrop-*` osztályoknál láttunk a Hátterek fejezetben).

* `blur-sm`, `blur`, `blur-md`, `blur-lg`, `blur-xl`: Elmosja az elemet. Gyakori pl. betöltés alatt lévő képeknél (placeholder), vagy háttérbe helyezett díszítőelemeknél.
* `grayscale`: Fekete-fehérré alakítja a képet (pl. hover előtt színes, hover után fekete-fehér termékkép esetén fordítva is használható: `grayscale hover:grayscale-0`).
* `brightness-{érték}`: Fényerő állítása (pl. `brightness-50` sötétebb, `brightness-125` világosabb).
* `contrast-{érték}`: Kontraszt állítása.
* `saturate-{érték}`: Szín telítettségének állítása (pl. `saturate-0` ugyanaz, mint a `grayscale`).

**Példa (Fekete-fehér termékkép, ami hoverre kiszínesedik):**
```html
<img src="termek.jpg" alt="Termék" class="grayscale hover:grayscale-0 transition duration-300">

```

## 5. Maszkok (Masks) - Gradiens átmenettel

Bár a teljes CSS maszkolás bonyolult, Tailwindben a legegyszerűbb maszkolást (egy elem széleinek elhalványítását) egy "menekülőutas" technikával, szögletes zárójelekkel (arbitrary values) érhetjük el legkönnyebben.

**Példa (Egy kép aljának elhalványítása átlátszóba):**

```html
<img src="kep.jpg" alt="Maszkolt kép" 
     class="w-full h-64 object-cover [mask-image:linear-gradient(to_bottom,black_60%,transparent_100%)]">

```

*(Magyarázat: Ahol a gradiens 'black', ott látszik a kép, ahol 'transparent', ott eltűnik).*

---

**💡 Tippek:**

* Az árnyékokat (`shadow-*`) és az átlátszóságot (`opacity-*`) szinte mindig érdemes `transition` osztályokkal kombinálni, hogy az állapotváltozások (pl. hover) lágyak legyenek.
* A keverési módok (`bg-blend-*`) nagyszerűek arra, hogy egységes tónust adj a különböző színű háttérképeknek anélkül, hogy előre szerkesztenéd őket.
* Ne keverd össze az `opacity-{n}`-t (egész elem) és a szín átlátszóságot (pl. `bg-blue-500/50` - csak a háttér)!
