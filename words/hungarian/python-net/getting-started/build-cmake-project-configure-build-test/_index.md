---
category: general
date: 2026-07-06
description: CMake projekt építése lépésről lépésre. Tanulja meg, hogyan konfigurálja
  a CMake-et, hogyan építi a CMake-et, és hogyan futtassa a CTest-et a megbízható
  teszteléshez.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: hu
og_description: Építs CMake projektet gyorsan, világos lépésekkel. Ez az útmutató
  bemutatja, hogyan konfiguráljuk a CMake-et, hogyan építsük a CMake-et, és hogyan
  futtassuk a CTest-et.
og_title: 'CMake projekt építése: Konfigurálás, építés és tesztelés útmutató'
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Build CMake project step‑by‑step. Learn how to configure CMake, how
    to build CMake, and how to run CTest for reliable testing.
  headline: 'Build CMake Project: Configure, Build & Test'
  type: TechArticle
tags:
- cmake
- ctest
- build-system
title: 'CMake projekt építése: konfigurálás, építés és tesztelés'
url: /hu/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# CMake projekt építése: konfigurálás, építés és tesztelés

Valaha is elgondolkodtál, hogyan **build CMake project** anélkül, hogy órákat töltenél a StackOverflow keresgélésével? Nem vagy egyedül. A legtöbb fejlesztő ugyanarra a problémára bukkan, amikor egy egyszerű `CMakeLists.txt`-ről egy reprodukálható építési csővezetékhez szeretne áttérni. 

Ebben az útmutatóban végigvezetünk a teljes folyamaton—*how to configure CMake*, *how to build CMake*, és *how to run CTest*—így egy tiszta, ismételhető építést kapsz, amelyet bármely gépen futtathatsz. A végére egy működő példát fogsz kapni, amelyet egyszerűen beilleszthetsz a saját tárolódba, extra szkriptek nélkül.

## Előfeltételek — Amire szükséged van a kezdés előtt

- Egy friss CMake verzió (3.20 vagy újabb) – a régebbi kiadások hiányoznak néhány általunk használt kapcsolót.
- A platformod által támogatott C++ fordító (gcc, clang, MSVC, stb.).
- Egy terminál vagy parancssor, amely hozzáfér a `cmake` és `ctest` parancsokhoz.
- (Opcionális) Git a példatároló klónozásához, ha pontosan követni szeretnéd a forrást.

Ha bármelyik hiányzik, szerezd be most; különben később „command not found” hibákkal fogsz szembesülni, és ez sosem szórakoztató.

## 1. lépés: A CMake projekt konfigurálása (Release konfiguráció)

Az első dolog, amit a *how to configure CMake* során teszel, hogy megmondod a CMake-nek, hol található a forrás, és hová szeretnéd, hogy az építési artefaktok menjenek. A `-S` kapcsoló a forráskönyvtárra mutat, a `-B` egy külön építési mappát hoz létre, és a `-D CMAKE_BUILD_TYPE=Release` egy optimalizált építést kényszerít.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**Miért fontos:** A forrás- és építési fájlok szétválasztása (`out‑of‑source` építések) megakadályozza a véletlen forrásmódosításokat, és később egyszerűvé teszi az építési könyvtár tisztítását. A `Release` kapcsoló azt is közli a fordítóval, hogy engedélyezze az optimalizációkat, ami általában a végleges binárisnál kívánatos.

> **Pro tipp:** Ha hibakereséshez Debug építésre van szükséged, egyszerűen cseréld le a `Release`-t `Debug`-re. Ugyanaz a parancs működik—CMake a többit kezeli.

## 2. lépés: A konfigurált projekt építése

Miután a konfigurációs lépés legenerálta az összes szükséges makefile-t vagy Visual Studio projektfájlt, már ténylegesen lefordíthatod a kódot. A `--build` opció elrejti a mögöttes építőeszközt (`make`, `ninja`, `MSBuild`, stb.), így ugyanaz a parancs működik Linuxon, macOS-en és Windows-on.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**Mi történik a háttérben?** A CMake beolvassa a korábbi lépésben létrehozott `CMakeCache.txt`-t, meghatározza a megfelelő építőeszközt, és a helyes kapcsolókkal meghívja azt. Ez a *how to build CMake* lényege—nem kell emlékezned, hogy `make`-et vagy `ninja`-t használsz; a CMake ezt megteszi helyetted.

Ha többmagos gépeken szeretnéd felgyorsítani a folyamatot, add hozzá a `-- -j$(nproc)` (Linux/macOS) vagy `-- /m` (Windows) kapcsolót a parancs után:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## 3. lépés: A példatesztek futtatása részletes kimenettel

A tesztelés az, ahol a gumi a útra kerül. A CMake a `ctest`-tel érkezik, egy tesztvezérlővel, amely felfedez és futtat minden tesztet, amelyet a `add_test()`-tel adtál hozzá a `CMakeLists.txt`-ben. A tesztek végrehajtásához és a részletes kimenet megtekintéséhez használd a `-E chdir` segédeszközt, hogy először a build könyvtárba lépj:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**Miért használjuk a `--verbose`-t?** Kiírja minden teszt parancssorát, kilépési kódját, és a teszt által generált kimenetet. Ez elengedhetetlen, amikor a *how to run CTest* megtanulásáról van szó, mivel pontosan megmutatja, mi történik a háttérben.

A tipikus kimenet így néz ki:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

Ha egy teszt hibát jelez, a részletes napló tartalmazni fogja a hibás parancsot és a hibaüzeneteket, ami sokkal gyorsabb hibakeresést tesz lehetővé.

## 4. lépés: Az egész munkafolyamat automatizálása (Opcionális)

Sok projekt esetén egy egyetlen soros megoldást szeretnél, amely egy lépésben konfigurál, épít és tesztel. Ezt elérheted egy egyszerű Bash (vagy PowerShell) szkripttel:

```bash
#!/usr/bin/env bash
SRC=YOUR_DIRECTORY/Examples/DocsExamples
BUILD=$SRC/build

# 1️⃣ Configure
cmake -S "$SRC" -B "$BUILD" -D CMAKE_BUILD_TYPE=Release

# 2️⃣ Build
cmake --build "$BUILD" -- -j$(nproc)

# 3️⃣ Test
cmake -E chdir "$BUILD" ctest --verbose
```

Mentsd el `run_all.sh` néven, tedd futtathatóvá (`chmod +x run_all.sh`), és már van egy reprodukálható **cmake build and test** csővezetéked, amelyet bármely CI rendszerbe beilleszthetsz (GitHub Actions, GitLab CI, Azure Pipelines, bármi).

## Szélsőséges esetek és gyakori buktatók

| Helyzet | Mire figyelj | Javítás |
|-----------|-------------------|-----|
| **Hiányzó fordító** | A CMake leáll a „No CMAKE_CXX_COMPILER could be found.” hibával. | Telepíts egy fordítót (`sudo apt install build-essential` Ubuntu-n, `xcode-select --install` macOS-en). |
| **Az out‑of‑source mappa már létezik** | A CMake megtagadhatja a újrakonfigurálást, ha a mappa elavult fájlokat tartalmaz. | Töröld a `build` könyvtárat (`rm -rf build`) vagy futtasd a `cmake --fresh`-et (CMake 3.24+). |
| **A CTest nem talál teszteket** | `add_test()` sosem lett meghívva vagy a teszt végrehajtható fájl nem fordult le. | Ellenőrizd, hogy a `add_test(NAME MyTest COMMAND MyTestExe)` szerepel-e a `CMakeLists.txt`-ben, és hogy a cél épül. |
| **Párhuzamos építések versenyhelyzetbe kerülnek egyéni parancsoknál** | Néhány egyéni parancs nincs `DEPENDS`-ként jelölve, ami nem determinisztikus hibákhoz vezet. | Adj hozzá megfelelő `add_custom_command(... DEPENDS ...)` bejegyzéseket. |

Ezeknek a finomságoknak a megértése a különbséget jelenti egy ingatag építés és egy szilárd CI csővezeték között.

## Vizuális áttekintés (Az alt szöveg tartalmazza az elsődleges kulcsszót)

![Diagram, amely a CMake projekt konfigurálásának, építésének és tesztelésének folyamatát mutatja](/images/cmake-workflow.png "CMake projekt építési munkafolyamat diagram")

## Összefoglalás – Amit megtanultál

Az alap kérdéssel indultunk: *how to build CMake project* a nulláról. A végére már tudod, hogyan **configure CMake** egy tiszta out‑of‑source építéssel, hogyan **build CMake** az univerzális `--build` kapcsolóval, és hogyan **run CTest** részletes kimenettel, hogy ellenőrizd, minden működik. Emellett van egy használatra kész szkripted, amely összekapcsolja a három lépést, így egy teljes **cmake build and test** munkafolyamatot kapsz.

## Mi a következő?

- **Tesztlefedettség jelentés hozzáadása** – integráld a `gcov` vagy `llvm-cov` eszközt, és hagyd, hogy a CTest közzétegye az eredményeket.
- **Cross‑compilation** – vizsgáld meg a `-DCMAKE_TOOLCHAIN_FILE` használatát beágyazott eszközökön való építéshez.
- **Csomagkészítés** – használd a `cpack`-et a binárisok csomagolásához terjesztéshez.
- **CI integráció** – másold a szkriptet egy GitHub Actions munkafolyamatba, és figyeld, ahogy az automatizálás minden pull requestnél lefut.

Nyugodtan kísérletezz különböző építési típusokkal, adj hozzá több tesztet, vagy cseréld le a példaforrást a saját projektedre. A ma bemutatott minták bármely CMake‑alapú kódbázisra alkalmazhatók, legyen az egy apró segédprogram vagy egy hatalmas többmodulos rendszer.

Boldog építést, és legyenek a CMake építéseid mindig reprodukálhatóak!

## Mit érdemes legközelebb megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Hogyan exportáljunk LaTeX-et Word‑ből – Lépésről‑lépésre útmutató](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [Hogyan mentsünk Markdown‑t DOCX‑ből – Lépésről‑lépésre útmutató](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Hogyan jelenítsük meg az Aspose.Words verziót Pythonban és .NET‑ben&#58; Lépésről‑lépésre útmutató](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}