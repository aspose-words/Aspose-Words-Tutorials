---
category: general
date: 2026-07-16
description: Tutorial „cmake build x64“ ukazuje, jak použít CMake k vygenerování řešení
  Visual Studio 2022 a sestavení projektu VS na 64‑bitovém hostiteli. Obsahuje kroky
  pro nastavení zdrojového adresáře.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: cs
lastmod: 2026-07-16
og_description: 'cmake build x64 vysvětleno: naučte se nastavit zdrojový adresář,
  vygenerovat řešení Visual Studio 2022 a zkompilovat projekt VS na 64‑bitovém hostiteli.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – Krok za krokem průvodce generováním a sestavením řešení
  VS 2022
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
title: cmake build x64 – Kompletní průvodce generováním a sestavováním projektů VS 2022
url: /cs/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Kompletní průvodce generováním a sestavováním projektů VS 2022

Už jste se někdy zamysleli **jak používat CMake**, abyste vytvořili 64‑bitové řešení Visual Studio, aniž byste si trhali vlasy? Nejste sami. V tomto tutoriálu projdeme workflow **cmake build x64**, které nastaví adresář se zdrojovým kódem, spustí generátor pro Visual Studio 2022 a nakonec sestaví projekt VS — vše pomocí několika čistých Bash příkazů.

Na konci tohoto průvodce budete mít reprodukovatelný skript, který můžete vložit do libovolného repozitáře, a také pevné pochopení základních konceptů, abyste jej mohli přizpůsobit svým potřebám.

---

## Co se naučíte

- **Set source directory** správně, aby CMake vědělo, kde se nachází váš `CMakeLists.txt`.  
- **cmake generate visual studio** – vyvolá generátor Visual Studio 2022 se správnými příznaky pro hostitele a architekturu.  
- Proveďte **cmake build x64** vygenerovaného řešení, volitelně s výběrem konfigurace Release.  
- Pochopte běžné úskalí, když se snažíte **build vs project** na 64‑bitovém stroji.  

Není vyžadována žádná předchozí magická znalost CMake; stačí terminál a aktuální instalace Visual Studio.

## Požadavky

| Requirement | Proč je to důležité |
|-------------|---------------------|
| CMake ≥ 3.20 | Podporuje příznaky `-Thost=` a `-Ax64` používané pro 64‑bitové sestavení. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | Generátor `Visual Studio 17 2022` odkazuje na tuto verzi. |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | Níže uvedený skript používá Bash syntaxi pro přehlednost. |
| Source tree containing a valid `CMakeLists.txt` | CMake nemůže vygenerovat řešení bez něj. |

Pokud některý z nich chybí, nejprve jej nainstalujte — CMake ze <https://cmake.org/download/> a VS 2022 z instalátoru Microsoftu.

## Krok 1 – Nastavte adresáře zdrojů a sestavení (`set source directory`)

Než zavoláte CMake, musíte mu říct **kde** hledat soubory projektu. Pevně zakódované cesty činí skript křehkým, proto použijeme proměnné prostředí, které můžete upravit pro každý projekt.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Proč je to důležité:**  
> CMake považuje *adresář zdrojů* (`SRC_DIR`) za kořen projektu. *Adresář sestavení* (`BUILD_DIR`) je místo, kde jsou uloženy všechny mezilehlé soubory, cache a finální `.sln`. Udržování je oddělených zabraňuje znečištění stromu zdrojů a usnadňuje úklid (`rm -rf "$BUILD_DIR"`).

Můžete nahradit `YOUR_DIRECTORY` libovolnou absolutní nebo relativní cestou; jen se ujistěte, že složka obsahuje `CMakeLists.txt`.

## Krok 2 – Vygenerujte řešení Visual Studio 2022 (`cmake generate visual studio`)

Nyní požádáme CMake, aby vytvořil řešení VS 2022 zaměřené na **x64**. Klíčové příznaky jsou:

- `-G "Visual Studio 17 2022"` – vybere generátor VS 2022.  
- `-Thost=x64` – říká CMake, že *hostitel* (IDE) běží jako 64‑bitový proces.  
- `-Ax64` – vynutí, aby vygenerovaný projekt byl sestaven pro architekturu x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Co se děje pod kapotou?**  
> CMake načte `CMakeLists.txt` z `$SRC_DIR`, vyřeší všechny volání `add_executable()` a `add_library()`, poté vytvoří soubor `.sln` a sadu souborů `.vcxproj` uvnitř `$BUILD_DIR`. Tyto projektové soubory jsou nyní připraveny k otevření ve Visual Studio nebo ke sestavení z příkazové řádky.

Pokud spustíte příkaz a uvidíte dlouhý seznam konfiguračních zpráv končících `-- Configuring done` a `-- Generating done`, úspěšně jste provedli krok **cmake generate visual studio**.

## Krok 3 – Sestavte vygenerované řešení (`cmake build x64`)

S řešením na místě je dalším logickým krokem jeho kompilace. CMake může řídit sestavení za vás, delegujíc na MSBuild v pozadí.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Proč použít `--config Release`?**  
> Projekty Visual Studio podporují více konfigurací (Debug, Release, RelWithDebInfo, atd.). Zadání `Release` zajišťuje, že binárky jsou optimalizovány pro produkci a že výsledný `.exe` nebo `.dll` se nachází ve složce `Release/` uvnitř stromu sestavení.

Pokud dáváte přednost Debug sestavení, nahraďte `Release` za `Debug`. Příkaz funguje stejným způsobem, což dokazuje, že **how to use CMake** pro různé konfigurace je jen otázka výměny tohoto příznaku.

## Krok 4 – Ověřte sestavení (`build vs project` kontrola)

Úspěšná kompilace by vám měla zanechat spustitelný soubor nebo knihovnu. Ověřme, že existuje:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Běžné úskalí:**  
> - Zapomenutí spustit krok generátoru po změně `CMakeLists.txt` způsobí selhání tohoto ověření.  
> - Míchání 32‑bitových a 64‑bitových toolchainů může vést k chybám linkeru; vždy udržujte `-Ax64` konzistentní.  
> - Pokud vidíte chyby “MSB3073”, obvykle to znamená, že selhal post‑build krok (např. kopírování zdrojů) — prozkoumejte výstup pro nápovědu.

## Krok 5 – Vyčistěte a spusťte znovu (Iterace na `cmake build x64`)

Během vývoje často potřebujete přestavět od začátku. Nejčistší způsob je smazat složku sestavení a začít znovu:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Tip:**  
> Přidání `-DCMAKE_BUILD_TYPE=Release` do příkazu generátoru je volitelné pro multi‑config generátory jako Visual Studio, ale může být užitečné, když přepnete na single‑config generátor jako Ninja.

## Krok 6 – Rozšíření skriptu (Pokročilé scénáře `cmake generate visual studio`)

Co když váš projekt žije v podadresáři, nebo potřebujete předat vlastní definice? CMake vám to umožní pomocí argumentů `-D`:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Nyní bude vygenerované řešení VS mít definované makro `MyFeature_ENABLED` a cíl instalace umístí soubory pod `/opt/myapp`. To ukazuje flexibilitu **how to use CMake** mimo základní tříkrokový tok.

## Očekávaný výstup

Když spustíte celý skript od začátku do konce, terminál by měl zobrazit něco jako:

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

Pokud se něco pokazí, CMake vypíše chybové zprávy, které ukazují na problematický řádek v `CMakeLists.txt` nebo na chybějící komponenty SDK — ideální pro rychlé ladění.

## Závěr

Probrali jsme vše, co potřebujete k provedení **cmake build x64**: nastavení adresáře zdrojů, vyvolání kroku **cmake generate visual studio**, kompilaci výsledného **build vs project** a ověření výstupu. Skript je kompaktní, přenosný a připravený k integraci do CI pipeline nebo lokálních vývojových workflow.

Dále můžete zkoumat:
- Přidání spouštění unit‑testů pomocí `ctest`.  
- Přepnutí na generátor Ninja pro rychlejší inkrementální sestavení (`-G Ninja`).  
- Použití CMake presetů (`CMakePresets.json`) k uložení právě zadaných příznaků.

Neváhejte experimentovat, rozbíjet věci a pak znovu sestavit — v konečném důsledku je to nejrychlejší způsob, jak se efektivně naučit používat CMake. Šťastné sestavování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit tabulku](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Vytvořit tabulku se stylem](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Vytvořit tabulku s okraji](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}