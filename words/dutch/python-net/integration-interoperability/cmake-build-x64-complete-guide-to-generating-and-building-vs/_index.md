---
category: general
date: 2026-07-16
description: cmake build x64 tutorial laat zien hoe je CMake gebruikt om een Visual
  Studio 2022‑oplossing te genereren en een VS‑project te bouwen op een 64‑bit host.
  Inclusief stappen voor het instellen van de bronmap.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: nl
lastmod: 2026-07-16
og_description: 'cmake build x64 uitgelegd: leer hoe je de bronmap instelt, een Visual
  Studio 2022‑oplossing genereert en een VS‑project compileert op een 64‑bit host.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – Stapsgewijze gids voor het genereren en bouwen van VS 2022‑oplossingen
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
title: cmake build x64 – Complete gids voor het genereren en bouwen van VS 2022‑projecten
url: /nl/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Complete gids voor het genereren en bouwen van VS 2022-projecten

Heb je je ooit afgevraagd **how to use CMake** om een 64‑bit Visual Studio‑oplossing te maken zonder je haar uit te trekken? Je bent niet de enige. In deze tutorial lopen we een **cmake build x64** workflow door die de bronmap instelt, de generator voor Visual Studio 2022 uitvoert, en uiteindelijk het VS‑project bouwt — allemaal met een paar nette Bash‑commando's.

Aan het einde van de gids heb je een reproduceerbaar script dat je in elke repository kunt plaatsen, plus een solide begrip van de onderliggende concepten zodat je het kunt aanpassen aan je eigen behoeften.

---

## Wat je zult leren

- **Set source directory** correct instellen zodat CMake weet waar je `CMakeLists.txt` zich bevindt.  
- **cmake generate visual studio** – roep de Visual Studio 2022 generator aan met de juiste host‑ en architectuur‑vlaggen.  
- Voer een **cmake build x64** uit van de gegenereerde oplossing, eventueel met de Release‑configuratie.  
- Begrijp veelvoorkomende valkuilen wanneer je probeert een **build vs project** op een 64‑bit machine uit te voeren.  

Geen voorafgaande CMake‑magie vereist; alleen een terminal en een recente Visual Studio‑installatie.

---

## Vereisten

| Vereiste | Waarom het belangrijk is |
|----------|--------------------------|
| CMake ≥ 3.20 | Ondersteunt de `-Thost=` en `-Ax64` vlaggen die worden gebruikt voor 64‑bit builds. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | De generator `Visual Studio 17 2022` wijst naar deze versie. |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | Het script hieronder gebruikt Bash‑syntaxis voor duidelijkheid. |
| Source tree containing a valid `CMakeLists.txt` | CMake kan geen oplossing genereren zonder. |

Als een van deze ontbreekt, installeer ze dan eerst — CMake van <https://cmake.org/download/> en VS 2022 via de Microsoft‑installer.

---

## Stap 1 – Stel de bron- en bouwmappen in (`set source directory`)

Voordat je CMake aanroept moet je aangeven **waar** het de projectbestanden moet zoeken. Paden hardcoderen maakt het script broos, dus we gebruiken omgevingsvariabelen die je per project kunt aanpassen.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Waarom dit belangrijk is:**  
> CMake beschouwt de *source directory* (`SRC_DIR`) als de root van het project. De *build directory* (`BUILD_DIR`) is waar alle tussenliggende bestanden, caches en de uiteindelijke `.sln` zich bevinden. Ze gescheiden houden voorkomt vervuiling van je bronboom en maakt opruimen triviaal (`rm -rf "$BUILD_DIR"`).

Je kunt `YOUR_DIRECTORY` vervangen door elk absoluut of relatief pad; zorg er alleen voor dat de map een `CMakeLists.txt` bevat.

---

## Stap 2 – Genereer een Visual Studio 2022‑oplossing (`cmake generate visual studio`)

Nu vragen we CMake om een VS 2022‑oplossing te genereren die **x64** target. De belangrijkste vlaggen zijn:

- `-G "Visual Studio 17 2022"` – selecteert de VS 2022 generator.  
- `-Thost=x64` – vertelt CMake dat de *host* (de IDE) draait als een 64‑bit proces.  
- `-Ax64` – dwingt het gegenereerde project om te bouwen voor de x64‑architectuur.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Wat gebeurt er onder de motorkap?**  
> CMake leest `CMakeLists.txt` vanuit `$SRC_DIR`, lost alle `add_executable()`‑ en `add_library()`‑aanroepen op, en maakt vervolgens een `.sln`‑bestand en een reeks `.vcxproj`‑bestanden aan in `$BUILD_DIR`. Deze projectbestanden zijn nu klaar om geopend te worden in Visual Studio of vanaf de commandoregel gebouwd te worden.

Als je het commando uitvoert en een lange lijst met configuratie‑berichten ziet eindigend met `-- Configuring done` en `-- Generating done`, dan heb je met succes een **cmake generate visual studio** stap uitgevoerd.

---

## Stap 3 – Bouw de gegenereerde oplossing (`cmake build x64`)

Met de oplossing aanwezig, is de volgende logische stap om deze te compileren. CMake kan de build voor je aansturen, waarbij het op de achtergrond MSBuild gebruikt.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Waarom `--config Release` gebruiken?**  
> Visual Studio‑projecten ondersteunen meerdere configuraties (Debug, Release, RelWithDebInfo, enz.). Het specificeren van `Release` zorgt ervoor dat de binaries geoptimaliseerd zijn voor productie en dat de resulterende `.exe` of `.dll` onder `Release/` in de build‑boom staat.

Als je een Debug‑build verkiest, vervang dan `Release` door `Debug`. Het commando werkt op dezelfde manier, wat bewijst dat **how to use CMake** voor verschillende configuraties slechts een kwestie is van het verwisselen van deze vlag.

---

## Stap 4 – Verifieer de build (`build vs project` sanity check)

Een succesvolle compilatie moet je een uitvoerbaar bestand of bibliotheek opleveren. Laten we bevestigen dat het bestaat:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Veelvoorkomende valkuilen:**  
> - Vergeten de generatorstap uit te voeren na het wijzigen van `CMakeLists.txt` zal deze controle laten falen.  
> - Het mengen van 32‑bit en 64‑bit toolchains kan leiden tot linker‑fouten; houd `-Ax64` altijd consistent.  
> - Als je “MSB3073”‑fouten ziet, betekent dit meestal dat een post‑build stap (zoals het kopiëren van resources) is mislukt — inspecteer de output voor aanwijzingen.

---

## Stap 5 – Opruimen en opnieuw uitvoeren (Itereren op een `cmake build x64`)

Tijdens de ontwikkeling moet je vaak vanaf nul opnieuw bouwen. De schoonste manier is om de build‑map te verwijderen en opnieuw te beginnen:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Tip:**  
> Het toevoegen van `-DCMAKE_BUILD_TYPE=Release` aan het generator‑commando is optioneel voor multi‑config generators zoals Visual Studio, maar kan handig zijn wanneer je overschakelt naar een single‑config generator zoals Ninja.

---

## Stap 6 – Het script uitbreiden (Geavanceerde `cmake generate visual studio` scenario's)

Wat als je project zich in een sub‑directory bevindt, of je moet aangepaste definities doorgeven? CMake laat je dat doen met `-D` argumenten:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Nu zal de gegenereerde VS‑oplossing de macro `MyFeature_ENABLED` gedefinieerd hebben, en het install‑target zal bestanden plaatsen onder `/opt/myapp`. Dit toont de flexibiliteit van **how to use CMake** voorbij de basis drie‑stappen flow.

---

## Verwachte output

Wanneer je het volledige script van begin tot eind uitvoert, zou de terminal iets dergelijks moeten weergeven:

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

Als er iets misgaat, zal CMake foutmeldingen geven die wijzen naar de problematische regel in `CMakeLists.txt` of naar ontbrekende SDK‑componenten — perfect voor snelle debugging.

---

## Conclusie

We hebben alles behandeld wat je nodig hebt om een **cmake build x64** uit te voeren: het instellen van de source directory, het aanroepen van de **cmake generate visual studio** stap, het compileren van het resulterende **build vs project**, en het verifiëren van de output. Het script is compact, draagbaar, en klaar voor integratie in CI‑pipelines of lokale ontwikkel‑workflows.

Vervolgens kun je verkennen:

- Het toevoegen van unit‑test uitvoering met `ctest`.  
- Overschakelen naar de Ninja‑generator voor snellere incrementele builds (`-G Ninja`).  
- Het gebruiken van CMake‑presets (`CMakePresets.json`) om de vlaggen die we net hebben getypt op te slaan.

Voel je vrij om te experimenteren, dingen te breken, en vervolgens opnieuw te bouwen — uiteindelijk is dat de snelste manier om te leren **how to use CMake** effectief. Veel bouwplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Tabel bouwen](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Tabel bouwen met stijl](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Tabel bouwen met randen](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}