---
category: general
date: 2026-07-16
description: cmake build x64 tutorial visar hur man använder CMake för att generera
  en Visual Studio 2022‑lösning och bygga ett VS‑projekt på en 64‑bits värddator.
  Inkluderar steg för att ange källkatalog.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: sv
lastmod: 2026-07-16
og_description: 'cmake build x64 förklarat: lär dig hur du anger källkatalog, genererar
  en Visual Studio 2022‑lösning och kompilerar ett VS‑projekt på en 64‑bit‑värddator.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – Steg‑för‑steg guide för att generera och bygga VS 2022‑lösningar
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
title: cmake build x64 – Komplett guide till att generera och bygga VS 2022‑projekt
url: /sv/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Komplett guide för att generera och bygga VS 2022-projekt

Har du någonsin undrat **how to use CMake** för att skapa en 64‑bit Visual Studio-lösning utan att dra i håret? Du är inte ensam. I den här handledningen går vi igenom ett **cmake build x64**-arbetsflöde som sätter källkatalogen, kör generatorn för Visual Studio 2022 och slutligen bygger VS‑projektet—allt med några rena Bash‑kommandon.

I slutet av guiden har du ett reproducerbart skript som du kan släppa in i vilket repo som helst, samt en solid förståelse för de underliggande koncepten så att du kan anpassa det efter dina egna behov.

---

## Vad du kommer att lära dig

- **Set source directory** korrekt så att CMake vet var din `CMakeLists.txt` finns.  
- **cmake generate visual studio** – anropa Visual Studio 2022-generatorn med rätt host‑ och arkitekturflägor.  
- Utför en **cmake build x64** av den genererade lösningen, eventuellt med Release‑konfigurationen.  
- Förstå vanliga fallgropar när du försöker **build vs project** på en 64‑bit‑maskin.  

Ingen tidigare CMake‑trollkonst krävs; bara en terminal och en aktuell Visual Studio‑installation.

---

## Förutsättningar

| Requirement | Why it matters |
|-------------|----------------|
| CMake ≥ 3.20 | Stöder flaggorna `-Thost=` och `-Ax64` som används för 64‑bit‑byggen. |
| Visual Studio 2022 (Community, Professional, eller Enterprise) | Generatorn `Visual Studio 17 2022` pekar på denna version. |
| Ett Bash‑kompatibelt skal (Git Bash, WSL, PowerShell med `bash`‑alias) | Skriptet nedan använder Bash‑syntax för tydlighet. |
| Källträd som innehåller en giltig `CMakeLists.txt` | CMake kan inte generera en lösning utan den. |

Om någon av dessa saknas, installera dem först—CMake från <https://cmake.org/download/> och VS 2022 från Microsoft‑installationsprogrammet.

---

## Steg 1 – Sätt käll- och byggkataloger (`set source directory`)

Innan du anropar CMake måste du berätta för den **var** den ska leta efter projektfilerna. Att hårdkoda sökvägar gör skriptet skört, så vi använder miljövariabler som du kan justera per projekt.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Varför detta är viktigt:**  
> CMake behandlar *source directory* (`SRC_DIR`) som projektets rot. *Build directory* (`BUILD_DIR`) är där alla mellanfiler, cache‑filer och den slutgiltiga `.sln` finns. Att hålla dem separata förhindrar att ditt källträd blir förorenat och gör städning trivial (`rm -rf "$BUILD_DIR"`).

Du kan ersätta `YOUR_DIRECTORY` med vilken absolut eller relativ sökväg som helst; se bara till att mappen innehåller en `CMakeLists.txt`.

---

## Steg 2 – Generera en Visual Studio 2022‑lösning (`cmake generate visual studio`)

Nu ber vi CMake att spåna ut en VS 2022‑lösning som riktar sig mot **x64**. De viktigaste flaggorna är:

- `-G "Visual Studio 17 2022"` – väljer VS 2022‑generatorn.  
- `-Thost=x64` – talar om för CMake att *hosten* (IDE:n) kör som en 64‑bit‑process.  
- `-Ax64` – tvingar det genererade projektet att bygga för x64‑arkitekturen.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Vad händer under huven?**  
> CMake läser `CMakeLists.txt` från `$SRC_DIR`, löser alla `add_executable()`‑ och `add_library()`‑anrop, och skapar sedan en `.sln`‑fil och ett antal `.vcxproj`‑filer i `$BUILD_DIR`. Dessa projektfiler är nu redo att öppnas i Visual Studio eller byggas från kommandoraden.

Om du kör kommandot och ser en lång lista med konfigurationsmeddelanden som avslutas med `-- Configuring done` och `-- Generating done`, har du framgångsrikt genomfört ett **cmake generate visual studio**‑steg.

---

## Steg 3 – Bygg den genererade lösningen (`cmake build x64`)

Med lösningen på plats är nästa logiska steg att kompilera den. CMake kan driva bygget åt dig, och delegera till MSBuild bakom kulisserna.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Varför använda `--config Release`?**  
> Visual Studio‑projekt stödjer flera konfigurationer (Debug, Release, RelWithDebInfo, etc.). Att ange `Release` säkerställer att binärerna är optimerade för produktion och att den resulterande `.exe`‑ eller `.dll`‑filen ligger under `Release/` i byggträdet.

Om du föredrar en Debug‑byggnad, ersätt `Release` med `Debug`. Kommandot fungerar på samma sätt, vilket visar att **how to use CMake** för olika konfigurationer bara är en fråga om att byta den flaggan.

---

## Steg 4 – Verifiera bygget (`build vs project` sanity check)

En lyckad kompilering bör lämna dig med en körbar fil eller ett bibliotek. Låt oss bekräfta att den finns:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Vanliga fallgropar:**  
> - Att glömma att köra generatorsteget efter att ha ändrat `CMakeLists.txt` får denna kontroll att misslyckas.  
> - Att blanda 32‑bit‑ och 64‑bit‑verktygskedjor kan leda till länkfel; håll alltid `-Ax64` konsekvent.  
> - Om du ser “MSB3073”-fel betyder det vanligtvis att ett efter‑byggsteg (som att kopiera resurser) misslyckades—inspektera utdata för ledtrådar.

---

## Steg 5 – Rensa upp och kör igen (Iterera på ett `cmake build x64`)

Under utveckling kommer du ofta behöva bygga om från början. Det renaste sättet är att radera byggmappen och börja om:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Tips:**  
> Att lägga till `-DCMAKE_BUILD_TYPE=Release` till generatorkommandot är valfritt för multi‑config‑generatorer som Visual Studio, men det kan vara praktiskt när du byter till en single‑config‑generator som Ninja.

---

## Steg 6 – Utöka skriptet (Avancerade `cmake generate visual studio`‑scenarier)

Vad händer om ditt projekt ligger i en underkatalog, eller du behöver skicka anpassade definitioner? CMake låter dig göra det med `-D`‑argument.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Nu kommer den genererade VS‑lösningen att ha makrot `MyFeature_ENABLED` definierat, och installationsmålet kommer att placera filer under `/opt/myapp`. Detta demonstrerar flexibiliteten i **how to use CMake** bortom det grundläggande tre‑stegsflödet.

---

## Förväntad output

När du kör hela skriptet från början till slut bör terminalen visa något liknande:

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

Om något går fel kommer CMake att ge felmeddelanden som pekar på den felande raden i `CMakeLists.txt` eller på saknade SDK‑komponenter—perfekt för snabb felsökning.

---

## Slutsats

Vi har gått igenom allt du behöver för att utföra ett **cmake build x64**: sätta källkatalogen, anropa **cmake generate visual studio**‑steget, kompilera det resulterande **build vs project**, och verifiera resultatet. Skriptet är kompakt, portabelt och redo för integration i CI‑pipelines eller lokala utvecklingsarbetsflöden.

Nästa steg kan du utforska:

- Lägga till körning av enhetstester med `ctest`.  
- Byta till Ninja‑generatorn för snabbare inkrementella byggen (`-G Ninja`).  
- Använda CMake‑presets (`CMakePresets.json`) för att lagra flaggorna vi just skrev.

Känn dig fri att experimentera, bryta saker och sedan bygga om—det är ändå det snabbaste sättet att lära sig **how to use CMake** effektivt. Lycka till med bygget!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Build Table](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Build Table With Style](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Build Table With Borders](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}