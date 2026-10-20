---
category: general
date: 2026-07-16
description: Poradnik cmake build x64 pokazuje, jak używać CMake do generowania rozwiązania
  Visual Studio 2022 i budowania projektu VS na 64‑bitowym hoście. Zawiera kroki ustawiania
  katalogu źródłowego.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: pl
lastmod: 2026-07-16
og_description: 'CMake build x64 wyjaśnione: dowiedz się, jak ustawić katalog źródłowy,
  wygenerować rozwiązanie Visual Studio 2022 i skompilować projekt VS na 64‑bitowym
  hoście.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: Budowanie cmake x64 – Przewodnik krok po kroku generowania i budowania rozwiązań
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
title: cmake build x64 – Kompletny przewodnik po generowaniu i budowaniu projektów
  VS 2022
url: /pl/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Kompletny przewodnik po generowaniu i budowaniu projektów VS 2022

Zastanawiałeś się kiedyś **jak używać CMake**, aby wygenerować 64‑bitowe rozwiązanie Visual Studio bez wyrywania sobie włosów? Nie jesteś sam. W tym samouczku przeprowadzimy Cię przez **cmake build x64** workflow, które ustawia katalog źródłowy, uruchamia generator dla Visual Studio 2022 i w końcu buduje projekt VS — wszystko przy użyciu kilku czystych poleceń Bash.

Po zakończeniu przewodnika będziesz posiadał powtarzalny skrypt, który możesz wrzucić do dowolnego repozytorium, oraz solidne zrozumienie podstawowych koncepcji, dzięki czemu będziesz mógł dostosować go do własnych potrzeb.

---

## Czego się nauczysz

- **Set source directory** poprawnie, aby CMake wiedział, gdzie znajduje się Twój `CMakeLists.txt`.  
- **cmake generate visual studio** – wywołaj generator Visual Studio 2022 z odpowiednimi flagami hosta i architektury.  
- Wykonaj **cmake build x64** wygenerowanego rozwiązania, opcjonalnie wybierając konfigurację Release.  
- Zrozum typowe pułapki, które pojawiają się przy **build vs project** na maszynie 64‑bitowej.  

Nie wymagana jest wcześniejsza znajomość CMake; wystarczy terminal i aktualna instalacja Visual Studio.

## Wymagania wstępne

| Wymaganie | Dlaczego jest ważne |
|-------------|----------------|
| CMake ≥ 3.20 | Obsługuje flagi `-Thost=` i `-Ax64` używane do kompilacji 64‑bitowych. |
| Visual Studio 2022 (Community, Professional, or Enterprise) | Generator `Visual Studio 17 2022` odnosi się do tej wersji. |
| A Bash‑compatible shell (Git Bash, WSL, PowerShell with `bash` alias) | Poniższy skrypt używa składni Bash dla przejrzystości. |
| Source tree containing a valid `CMakeLists.txt` | CMake nie może wygenerować rozwiązania bez tego. |

Jeśli którekolwiek z nich brakuje, zainstaluj je najpierw — CMake ze <https://cmake.org/download/> oraz VS 2022 z instalatora Microsoft.

## Krok 1 – Ustaw katalogi źródłowy i budowania (`set source directory`)

Zanim wywołasz CMake, musisz powiedzieć mu **gdzie** szukać plików projektu. Sztywne kodowanie ścieżek czyni skrypt kruchym, więc użyjemy zmiennych środowiskowych, które możesz dostosować per‑projekt.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Dlaczego to ważne:**  
> CMake traktuje *katalog źródłowy* (`SRC_DIR`) jako korzeń projektu. *Katalog budowania* (`BUILD_DIR`) to miejsce, w którym znajdują się wszystkie pliki pośrednie, pamięci podręczne i ostateczny plik `.sln`. Trzymanie ich osobno zapobiega zanieczyszczeniu drzewa źródeł i ułatwia czyszczenie (`rm -rf "$BUILD_DIR"`).

Możesz zamienić `YOUR_DIRECTORY` na dowolną ścieżkę bezwzględną lub względną; po prostu upewnij się, że folder zawiera `CMakeLists.txt`.

## Krok 2 – Wygeneruj rozwiązanie Visual Studio 2022 (`cmake generate visual studio`)

Teraz prosimy CMake, aby wyprodukował rozwiązanie VS 2022 skierowane na **x64**. Kluczowe flagi to:

- `-G "Visual Studio 17 2022"` – wybiera generator VS 2022.  
- `-Thost=x64` – informuje CMake, że *host* (IDE) działa jako proces 64‑bitowy.  
- `-Ax64` – wymusza, aby wygenerowany projekt budował się dla architektury x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Co się dzieje pod maską?**  
> CMake odczytuje `CMakeLists.txt` z `$SRC_DIR`, rozwiązuje wszystkie wywołania `add_executable()` i `add_library()`, a następnie tworzy plik `.sln` oraz zestaw plików `.vcxproj` w `$BUILD_DIR`. Te pliki projektów są teraz gotowe do otwarcia w Visual Studio lub budowania z linii poleceń.

Jeśli uruchomisz polecenie i zobaczysz długą listę komunikatów konfiguracyjnych kończących się `-- Configuring done` i `-- Generating done`, pomyślnie wykonałeś krok **cmake generate visual studio**.

## Krok 3 – Zbuduj wygenerowane rozwiązanie (`cmake build x64`)

Mając rozwiązanie, kolejnym logicznym krokiem jest jego kompilacja. CMake może sterować budowaniem, delegując do MSBuild w tle.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Dlaczego używać `--config Release`?**  
> Projekty Visual Studio obsługują wiele konfiguracji (Debug, Release, RelWithDebInfo, itp.). Określenie `Release` zapewnia, że binaria są zoptymalizowane pod produkcję i że wynikowy plik `.exe` lub `.dll` znajduje się w katalogu `Release/` w drzewie budowania.

Jeśli wolisz kompilację Debug, zamień `Release` na `Debug`. Polecenie działa tak samo, co dowodzi, że **how to use CMake** dla różnych konfiguracji to tylko kwestia zamiany tej flagi.

## Krok 4 – Zweryfikuj budowę (`build vs project` sanity check)

Udana kompilacja powinna zostawić Ci plik wykonywalny lub bibliotekę. Sprawdźmy, czy istnieje:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Typowe pułapki:**  
> - Zapomnienie o uruchomieniu kroku generatora po zmianie `CMakeLists.txt` spowoduje niepowodzenie tego sprawdzenia.  
> - Mieszanie łańcuchów narzędzi 32‑bitowych i 64‑bitowych może prowadzić do błędów linkera; zawsze utrzymuj spójność `-Ax64`.  
> - Jeśli widzisz błędy „MSB3073”, zazwyczaj oznacza to niepowodzenie kroku post‑build (np. kopiowanie zasobów) — przejrzyj wyjście w poszukiwaniu wskazówek.

## Krok 5 – Czyszczenie i ponowne uruchomienie (Iteracja na `cmake build x64`)

Podczas rozwoju często będziesz musiał przebudować od zera. Najczystszy sposób to usunięcie folderu budowania i rozpoczęcie od nowa:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Wskazówka:**  
> Dodanie `-DCMAKE_BUILD_TYPE=Release` do polecenia generatora jest opcjonalne dla generatorów wielokonfiguracyjnych, takich jak Visual Studio, ale może być przydatne, gdy przełączasz się na generator jednokonfiguracyjny, taki jak Ninja.

## Krok 6 – Rozszerzanie skryptu (Zaawansowane scenariusze `cmake generate visual studio`)

A co jeśli Twój projekt znajduje się w podkatalogu lub musisz przekazać własne definicje? CMake pozwala to zrobić przy pomocy argumentów `-D`:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Teraz wygenerowane rozwiązanie VS będzie miało zdefiniowane makro `MyFeature_ENABLED`, a cel instalacji umieści pliki pod `/opt/myapp`. To pokazuje elastyczność **how to use CMake** poza podstawowym trójstopniowym przepływem.

## Oczekiwany wynik

Gdy uruchomisz pełny skrypt od początku do końca, terminal powinien wyświetlić coś podobnego do:

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

Jeśli coś pójdzie nie tak, CMake wyświetli komunikaty o błędach wskazujące na problematyczną linię w `CMakeLists.txt` lub brakujące komponenty SDK — idealne do szybkiego debugowania.

## Zakończenie

Omówiliśmy wszystko, co potrzebne do wykonania **cmake build x64**: ustawienie katalogu źródłowego, wywołanie kroku **cmake generate visual studio**, kompilację wynikowego **build vs project** oraz weryfikację wyjścia. Skrypt jest zwięzły, przenośny i gotowy do integracji w pipeline'ach CI lub lokalnych procesach rozwoju.

Następnie możesz zbadać:

- Dodanie uruchamiania testów jednostkowych przy pomocy `ctest`.  
- Przejście na generator Ninja dla szybszych przyrostowych kompilacji (`-G Ninja`).  
- Użycie presetów CMake (`CMakePresets.json`) do przechowywania flag, które właśnie wpisaliśmy.

Śmiało eksperymentuj, psuj rzeczy, a potem przebudowuj — w końcu to najszybszy sposób, aby nauczyć się efektywnego używania CMake. Szczęśliwego budowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i zbadać alternatywne podejścia implementacyjne w własnych projektach.

- [Build Table](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Build Table With Style](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Build Table With Borders](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}