---
category: general
date: 2026-07-06
description: Bouw CMake‑project stap voor stap. Leer hoe je CMake configureert, hoe
  je CMake bouwt en hoe je CTest uitvoert voor betrouwbare tests.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: nl
og_description: Bouw CMake‑project snel met duidelijke stappen. Deze gids laat zien
  hoe je CMake configureert, hoe je CMake bouwt en hoe je CTest uitvoert.
og_title: 'CMake-project bouwen: Configuratie, bouw en testgids'
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
title: 'CMake‑project bouwen: configureren, bouwen & testen'
url: /nl/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bouw CMake-project: Configureren, Bouwen & Testen

Heb je je ooit afgevraagd hoe je **CMake-project kunt bouwen** zonder uren te verspillen aan zoeken op StackOverflow? Je bent niet de enige. De meeste ontwikkelaars lopen tegen hetzelfde probleem aan wanneer ze van een simpel `CMakeLists.txt` naar een reproduceerbare build‑pipeline willen overstappen. 

In deze tutorial lopen we het volledige proces door—*hoe je CMake configureert*, *hoe je CMake bouwt*, en *hoe je CTest uitvoert*—zodat je eindigt met een schone, herhaalbare build die je op elke machine kunt draaien. Aan het einde heb je een werkend voorbeeld dat je kunt kopiëren‑plakken in je eigen repository, zonder extra scripts.

## Vereisten — Wat je nodig hebt voordat je begint

Voordat we beginnen, zorg dat je het volgende hebt:

- Een recente CMake‑versie (3.20 of nieuwer) – oudere releases missen enkele van de vlaggen die we gaan gebruiken.
- Een C++‑compiler die door jouw platform wordt ondersteund (gcc, clang, MSVC, enz.).
- Een terminal of opdrachtprompt met toegang tot `cmake` en `ctest`.
- (Optioneel) Git om de voorbeeld‑repository te clonen als je de exacte bron wilt volgen.

Als een van deze ontbreekt, haal ze dan nu; anders krijg je later “command not found”-fouten, en dat is nooit leuk.

## Stap 1: Configureer het CMake-project (Release-configuratie)

Het eerste wat je doet wanneer je *hoe je CMake configureert* is CMake vertellen waar de broncode zich bevindt en waar je de build‑artefacten wilt plaatsen. De `-S`‑vlag wijst naar de bronmap, `-B` maakt een aparte build‑folder aan, en `-D CMAKE_BUILD_TYPE=Release` dwingt een geoptimaliseerde build af.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**Waarom dit belangrijk is:** Het gescheiden houden van bron‑ en build‑bestanden (`out‑of‑source` builds) voorkomt accidentele wijzigingen in de bron en maakt het later triviaal om de build‑directory op te schonen. De `Release`‑vlag vertelt de compiler ook om optimalisaties in te schakelen, wat je meestal wilt voor een definitief binary.

> **Pro tip:** Als je een Debug‑build nodig hebt voor probleemoplossing, verwissel dan simpelweg `Release` voor `Debug`. Hetzelfde commando werkt—CMake regelt de rest.

## Stap 2: Bouw het geconfigureerde project

Nu de configuratiestap alle benodigde makefiles of Visual‑Studio‑projectbestanden heeft gegenereerd, kun je de code daadwerkelijk compileren. De `--build`‑optie abstraheert het onderliggende build‑tool (`make`, `ninja`, `MSBuild`, enz.), zodat hetzelfde commando werkt op Linux, macOS en Windows.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**Wat er onder de motorkap gebeurt:** CMake leest de `CMakeCache.txt` die in de vorige stap is aangemaakt, bepaalt het juiste build‑tool en roept het aan met de correcte vlaggen. Dit is de kern van *hoe je CMake bouwt*—je hoeft niet te onthouden of je `make` of `ninja` gebruikt; CMake doet het voor je.

Als je de snelheid wilt verhogen op multi‑core machines, voeg `-- -j$(nproc)` (Linux/macOS) of `-- /m` (Windows) toe na het commando:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## Stap 3: Voer de voorbeeldtests uit met gedetailleerde output

Testen is waar de rubber de weg ontmoet. CMake wordt geleverd met `ctest`, een test‑driver die elke test kan ontdekken en uitvoeren die via `add_test()` in je `CMakeLists.txt` is toegevoegd. Om de tests uit te voeren en gedetailleerde output te zien, gebruik je de `-E chdir`‑helper om eerst naar de build‑directory te gaan:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**Waarom `--verbose` gebruiken?** Het print de commandoregel, exit‑code en eventuele output van elke test. Dit is essentieel wanneer je *hoe je CTest uitvoert* leert, omdat het precies laat zien wat er achter de schermen gebeurt.

Typische output ziet er als volgt uit:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

Als een test faalt, bevat het gedetailleerde log de mislukte commandoregel en eventuele foutmeldingen, waardoor debuggen veel sneller gaat.

## Stap 4: Automatiseer de volledige workflow (Optioneel)

Voor veel projecten wil je een één‑regel‑script dat configureert, bouwt en test in één keer. Dat kun je bereiken met een simpel Bash‑ (of PowerShell‑)script:

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

Sla het op als `run_all.sh`, maak het uitvoerbaar (`chmod +x run_all.sh`), en je hebt een reproduceerbare **cmake build and test**‑pipeline die je in elk CI‑systeem kunt droppen (GitHub Actions, GitLab CI, Azure Pipelines, noem maar op).

## Randgevallen & Veelvoorkomende valkuilen

| Situatie | Waar je op moet letten | Oplossing |
|-----------|------------------------|-----------|
| **Ontbrekende compiler** | CMake stopt met “No CMAKE_CXX_COMPILER could be found.” | Installeer een compiler (`sudo apt install build-essential` op Ubuntu, `xcode-select --install` op macOS). |
| **Out‑of‑source map bestaat al** | CMake weigert mogelijk te herconfigureren als de map verouderde bestanden bevat. | Verwijder de `build`‑directory (`rm -rf build`) of voer `cmake --fresh` uit (CMake 3.24+). |
| **CTest kan tests niet vinden** | `add_test()` is nooit aangeroepen of de test‑executable kon niet worden gecompileerd. | Controleer dat `add_test(NAME MyTest COMMAND MyTestExe)` in `CMakeLists.txt` staat en dat de target wordt gebouwd. |
| **Parallelle builds race op custom commands** | Sommige custom commands zijn niet gemarkeerd als `DEPENDS`, wat leidt tot niet‑deterministische fouten. | Voeg juiste `add_custom_command(... DEPENDS ...)`‑vermeldingen toe. |

Het begrijpen van deze nuances maakt het verschil tussen een wankele build en een rotsvaste CI‑pipeline.

## Visueel overzicht (Alt‑tekst bevat hoofdzoekwoord)

![Diagram dat de stroom van configureren, bouwen en testen van een CMake‑project toont](/images/cmake-workflow.png "Diagram van de workflow van het bouwen van een CMake‑project")

## Samenvatting – Wat je hebt geleerd

We begonnen met de kernvraag: *hoe je een CMake‑project vanaf nul bouwt*. Tegen het einde weet je nu hoe je **CMake configureert** met een schone out‑of‑source build, **CMake bouwt** met de universele `--build`‑vlag, en **CTest uitvoert** met verbose output om te verifiëren dat alles werkt. Je hebt ook een kant‑klaar script dat de drie stappen samenvoegt, waardoor je een volledige **cmake build and test**‑workflow hebt.

## Wat is het vervolg?

- **Coverage‑rapportage toevoegen** – integreer `gcov` of `llvm-cov` en laat CTest de resultaten publiceren.
- **Cross‑compilatie** – verken `-DCMAKE_TOOLCHAIN_FILE` voor bouwen op embedded apparaten.
- **Pakketcreatie** – gebruik `cpack` om je binaries te bundelen voor distributie.
- **CI‑integratie** – kopieer het script naar een GitHub Actions‑workflow en zie de automatisering draaien bij elke pull‑request.

Voel je vrij om te experimenteren met verschillende build‑types, meer tests toe te voegen, of de voorbeeldbron te vervangen door je eigen project. De patronen die we vandaag hebben behandeld gelden voor elke CMake‑gebaseerde codebase, of het nu een klein hulpprogramma of een enorm multi‑module systeem is.

Happy building, and may your CMake builds always be reproducible!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe LaTeX te exporteren vanuit Word – Stapsgewijze handleiding](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [Hoe Markdown op te slaan vanuit DOCX – Stapsgewijze handleiding](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Hoe de Aspose.Words‑versie weer te geven in Python en .NET: Een stapsgewijze handleiding](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}