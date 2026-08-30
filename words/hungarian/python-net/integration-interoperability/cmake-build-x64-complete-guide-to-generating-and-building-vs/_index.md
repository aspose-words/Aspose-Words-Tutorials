---
category: general
date: 2026-07-16
description: A cmake build x64 tutorial bemutatja, hogyan használjuk a CMake-et Visual
  Studio 2022 megoldás generálásához és egy VS projekt felépítéséhez 64‑bit gépen.
  Tartalmazza a forráskönyvtár beállításának lépéseit.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: hu
lastmod: 2026-07-16
og_description: 'cmake build x64 magyarázata: megtanulhatod, hogyan állítsd be a forráskönyvtárat,
  generálj Visual Studio 2022 megoldást, és fordíts egy VS projektet 64‑bit gépen.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – Lépésről lépésre útmutató a VS 2022 megoldások generálásához
  és felépítéséhez
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: cmake build x64 – Teljes útmutató a VS 2022 projektek generálásához és építéséhez
url: /hu/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Teljes útmutató a VS 2022 projektek generálásához és felépítéséhez

Kíváncsi voltál már **hogyan használjuk a CMake‑et** egy 64‑bit Visual Studio megoldás előállításához anélkül, hogy a hajadba nyúlnál? Nem vagy egyedül. Ebben az útmutatóban végigvezetünk egy **cmake build x64** munkafolyamaton, amely beállítja a forráskönyvtárat, elindítja a Visual Studio 2022 generátort, és végül felépíti a VS projektet – mindezt néhány egyszerű Bash parancs segítségével.

A útmutató végére egy újrahasználható szkriptet kapsz, amelyet bármely tárolóba beilleszthetsz, valamint alapos megértést a mögöttes koncepciókról, hogy saját igényeid szerint módosíthasd.

---

## Mit fogsz megtanulni

- **A forráskönyvtár** helyes beállítása, hogy a CMake tudja, hol található a `CMakeLists.txt`.  
- **cmake generate visual studio** – a Visual Studio 2022 generátor meghívása a megfelelő host és architektúra kapcsolókkal.  
- **cmake build x64** végrehajtása a generált megoldáson, opcionálisan a Release konfiguráció kiválasztásával.  
- A gyakori hibák megértése, amikor **build vs project**‑et próbálsz 64‑bit gépen futtatni.  

Előzetes CMake tudás nem szükséges; csak egy terminál és egy friss Visual Studio telepítés.

---

## Előfeltételek

| Követelmény | Miért fontos |
|-------------|--------------|
| CMake ≥ 3.20 | Támogatja a `-Thost=` és `-Ax64` kapcsolókat, amelyeket 64‑bit buildhez használunk. |
| Visual Studio 2022 (Community, Professional vagy Enterprise) | A `Visual Studio 17 2022` generátor erre a verzióra mutat. |
| Bash‑kompatibilis shell (Git Bash, WSL, PowerShell `bash` alias‑szal) | A lentebb látható szkript Bash szintaxist használ a tisztaság kedvéért. |
| Érvényes `CMakeLists.txt`‑et tartalmazó forrásfa | CMake nem tud megoldást generálni nélküle. |

Ha valamelyik hiányzik, telepítsd előbb – a CMake letölthető innen: <https://cmake.org/download/> és a VS 2022 a Microsoft telepítőjéből.

---

## 1. Lépés – Állítsd be a forrás- és buildkönyvtárakat (`set source directory`)

Mielőtt meghívnád a CMake‑et, meg kell mondanod **hol** keresse a projektfájlokat. A keménykódolt útvonalak törékennyé teszik a szkriptet, ezért környezeti változókat használunk, amelyeket projektenként módosíthatsz.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Miért fontos:**  
> A CMake a *forráskönyvtár* (`SRC_DIR`) értékét a projekt gyökereként kezeli. A *buildkönyvtár* (`BUILD_DIR`) tartalmazza az összes köztes fájlt, gyorsítót és a végső `.sln`‑t. Ezek szétválasztása megakadályozza a forrásfa szennyeződését, és a tisztítás egyszerű (`rm -rf "$BUILD_DIR"`).

A `YOUR_DIRECTORY`‑t bármilyen abszolút vagy relatív úttal helyettesítheted; csak győződj meg róla, hogy a mappában megtalálható egy `CMakeLists.txt`.

---

## 2. Lépés – Visual Studio 2022 megoldás generálása (`cmake generate visual studio`)

Most megkérjük a CMake‑et, hogy készítsen egy VS 2022 megoldást, amely **x64** célra épül. A kulcsfontosságú kapcsolók:

- `-G "Visual Studio 17 2022"` – a VS 2022 generátort választja.  
- `-Thost=x64` – azt mondja a CMake‑nek, hogy a *host* (az IDE) 64‑bit folyamatként fut.  
- `-Ax64` – kényszeríti a generált projektet, hogy az x64 architektúrára épüljön.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Mi történik a háttérben?**  
> A CMake beolvassa a `$SRC_DIR`‑ben lévő `CMakeLists.txt`‑t, feloldja az összes `add_executable()` és `add_library()` hívást, majd létrehozza a `.sln` fájlt és egy sor `.vcxproj` fájlt a `$BUILD_DIR`‑ben. Ezek a projektfájlok már készen állnak a Visual Studio‑ban való megnyitásra vagy a parancssori buildre.

Ha a parancs futtatása után egy hosszú konfigurációs üzenetsorozatot látsz, amely `-- Configuring done`‑ra és `-- Generating done`‑ra végződik, akkor sikeresen végrehajtottad a **cmake generate visual studio** lépést.

---

## 3. Lépés – A generált megoldás felépítése (`cmake build x64`)

Miután a megoldás elkészült, a következő logikus lépés a fordítás. A CMake képes a buildet vezérelni, a háttérben az MSBuild‑et használva.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Miért használjuk a `--config Release`‑t?**  
> A Visual Studio projektek több konfigurációt támogatnak (Debug, Release, RelWithDebInfo stb.). A `Release` megadása biztosítja, hogy a binárisok a termelésre optimalizálva legyenek, és a keletkező `.exe` vagy `.dll` a `Release/` könyvtárba kerüljön a buildfában.

Ha Debug buildet szeretnél, cseréld a `Release`‑t `Debug`‑ra. A parancs ugyanúgy működik, bizonyítva, hogy a **how to use CMake** különböző konfigurációkhoz csupán a flag cseréjével változtatható.

---

## 4. Lépés – A build ellenőrzése (`build vs project` sanity check)

Egy sikeres fordítás után egy futtatható vagy könyvtár fájl áll rendelkezésre. Ellenőrizzük, hogy létezik-e:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Gyakori buktatók:**  
> - Ha a `CMakeLists.txt` módosítása után nem futtatod újra a generátor lépést, ez az ellenőrzés hibát fog jelezni.  
> - 32‑bit és 64‑bit eszközkészletek keverése linker hibákhoz vezethet; mindig tartsd konzisztensen a `-Ax64` kapcsolót.  
> - A “MSB3073” hibák általában egy post‑build lépés (például erőforrások másolása) kudarcát jelzik – nézd meg a kimenetet a részletekért.

---

## 5. Lépés – Tisztítás és újrafuttatás (`cmake build x64` újraindítása)

Fejlesztés közben gyakran szükség van a teljes újrafordításra. A legegyszerűbb módja a build mappa törlése és az elejétől való kezdés:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Tipp:**  
> A `-DCMAKE_BUILD_TYPE=Release` hozzáadása a generátor parancshoz opcionális a többkonfigurációs generátoroknál, mint a Visual Studio, de hasznos lehet, ha egy egykonfigurációs generátorra, például a Ninja‑ra váltasz.

---

## 6. Lépés – A szkript kibővítése (haladó `cmake generate visual studio` szcenáriók)

Mi van, ha a projekt egy alkönyvtárban található, vagy egyedi definíciókat kell átadni? A CMake ezt `-D` argumentumokkal teszi lehetővé:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Most a generált VS megoldásban a `MyFeature_ENABLED` makró definiálva lesz, és az install cél a fájlokat a `/opt/myapp` könyvtárba helyezi. Ez bemutatja a **how to use CMake** rugalmasságát az alap háromlépéses folyamaton túl.

---

## Várt kimenet

Ha a teljes szkriptet elejétől végéig lefuttatod, a terminál valami ilyesmit kell, hogy mutasson:

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

Ha valami rosszul sül el, a CMake hibajelzéseket ad, amelyek a `CMakeLists.txt`‑ben lévő hibás sorra vagy hiányzó SDK komponensekre mutatnak – tökéletes a gyors hibakereséshez.

---

## Összegzés

Mindent lefedtünk, ami a **cmake build x64** elvégzéséhez szükséges: a forráskönyvtár beállítása, a **cmake generate visual studio** lépés meghívása, a **build vs project** lefordítása, és a kimenet ellenőrzése. A szkript kompakt, hordozható, és készen áll a CI pipeline‑okba vagy helyi fejlesztési munkafolyamatokba való integrálásra.

A következő lépések lehetnek:

- Egységtesztek futtatása `ctest`‑tel.  
- Átváltás a Ninja generátorra a gyorsabb inkrementális buildhez (`-G Ninja`).  
- CMake presetek használata (`CMakePresets.json`) a most beírt flag‑ek tárolásához.

Nyugodtan kísérletezz, törj el dolgokat, majd építs újra – hiszen ez a leggyorsabb módja annak, hogy hatékonyan megtanuld, **how to use CMake**. Boldog építést!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás komplett, működő kódrészleteket és lépésről‑lépésre magyarázatot tartalmaz, hogy további API‑funkciókat saját projektjeidben is felfedezhess.

- [Táblázat építése](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Stílussal ellátott táblázat építése](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Szegélyekkel ellátott táblázat építése](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}