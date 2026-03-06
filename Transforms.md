
# Transzformációk (Transforms)

A Tailwind transzformációs osztályaival anélkül méretezhetsz, forgathatsz, tolhatsz el vagy dönthetsz meg elemeket, hogy a dokumentum normál folyását (tehát a többi elem elhelyezkedését) megzavarnád.

## Méretezés (Scale)

A `scale-*` osztályokkal az elemeket az eredeti méretük százalékában tudod nagyítani vagy kicsinyíteni. A `scale-100` az eredeti (100%-os) méret.

* **`scale-50`, `scale-75`, `scale-90`, `scale-95**`: Kicsinyítés (pl. 50%, 75%).
* **`scale-105`, `scale-110`, `scale-125`, `scale-150**`: Nagyítás.
* **Tengelyenkénti méretezés**: Ha csak széltében vagy hosszában nyújtanál valamit, használd a `scale-x-*` (vízszintes) vagy `scale-y-*` (függőleges) osztályokat.

## Forgatás (Rotate)

A `rotate-*` osztályok fokban (degree) forgatják el az elemet.

* **`rotate-45`, `rotate-90`, `rotate-180**`: Az óramutató járásával megegyező forgatás (pl. 45 fok).
* **`-rotate-45`, `-rotate-90**`: Az óramutató járásával ellentétes (negatív) forgatás. *(Tipp: a mínusz jelet egyszerűen az osztály elé kell tenni!)*

**Példa (Lenyíló menü nyíl animációja):**
Gyakori trükk, hogy egy gomb melletti kis nyíl lefelé néz, de ha a menü aktív (vagy a gomb fölé viszed az egeret), felfelé fordul.

```html
<button class="flex items-center gap-2 group p-2 bg-gray-100 rounded">
  Menü lenyitása
  <svg class="w-4 h-4 transition-transform duration-300 group-hover:rotate-180" viewBox="0 0 24 24">
    </svg>
</button>

```

## Eltolás (Translate)

A `translate-*` osztályokkal az elemet a saját pozíciójához képest mozgathatod el vízszintes (X) vagy függőleges (Y) irányban. Az értékek megegyeznek a Tailwind térköz (spacing) skálájával, de használhatsz tört részeket (százalékokat) is.

* **`translate-x-4`**: Jobbra tolja az elemet (kb. 16px).
* **`-translate-y-2`**: Felfelé tolja az elemet (negatív érték).
* **`translate-x-1/2` vagy `translate-x-full**`: Az elem a *saját szélességének* felével (50%), vagy a teljes szélességével (100%) tolódik el. Ez hihetetlenül hasznos középre igazításnál vagy képernyőről kicsúszó paneleknél!

## Döntés (Skew)

A `skew-*` osztályokkal paralelogrammává torzíthatod (döntheted) az elemeket. Gyakran használják modern, ferde hátterű szekciók létrehozására.

* **`skew-x-12`**: Vízszintes tengely mentén dönti meg az elemet 12 fokkal.
* **`-skew-y-6`**: Függőleges tengely mentén dönti meg ellenkező irányba.

## Transzformáció Középpontja (Transform Origin)

Alapértelmezés szerint minden transzformáció (forgatás, nagyítás) az elem *kellős közepéből* (`origin-center`) indul ki. Az `origin-*` osztályokkal ezt a kiindulási pontot áthelyezheted a sarkokba vagy a szélekre.

* **`origin-top`**: Az elem tetejéhez rögzíti a pontot (pl. egy lefelé nyíló kártya vagy redőny effektushoz).
* **`origin-bottom-left`**: A bal alsó sarokból indul a forgatás vagy nagyítás.
* **`origin-right`**: A jobb oldalhoz van "szögelve".

**Példa (Kreatív kombináció):**
Egy kis értesítő kártya, ami a jobb felső sarkához van rögzítve, és amikor megjelenik, onnan "nyílik le" egy picit megdőlve, majd a helyére ugrik.

```html
<div class="bg-indigo-600 text-white p-4 rounded-lg shadow-lg
            origin-top-right transform scale-95 -rotate-3 hover:scale-100 hover:rotate-0 transition-all duration-300">
  <p class="font-bold">Új üzeneted érkezett!</p>
</div>

```

---

**💡 Tippek:**

* A **`translate-x-[-50%] translate-y-[-50%]`** (azaz `-translate-x-1/2 -translate-y-1/2`) osztályok a `position: absolute; top: 50%; left: 50%;` osztályokkal együtt adják a CSS történetének legbiztosabb és legpontosabb "tökéletesen középre igazító" módszerét, ha egy lebegő elemet (pl. modális ablakot) akarsz a képernyő közepére tenni.
* Ha sok animációt (főleg mozgást és nagyítást) használsz, érdemes odaírni a **`transform-gpu`** osztályt is. Ez rákényszeríti a böngészőt, hogy a videókártyát (GPU) használja a számításokhoz, így sokkal simább, 60fps sebességű lesz az animációd, és nem fog "szaggatni" mobilon sem.
