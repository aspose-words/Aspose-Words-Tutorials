---
category: general
date: 2026-03-01
description: Utwórz FontSettings w C#, aby wykrywać brakujące czcionki, przechwytywać
  komunikaty o czcionkach i obsługiwać brakujące czcionki przy użyciu Aspose.Words.
  Przewodnik krok po kroku dla programistów.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: pl
og_description: Utwórz FontSettings w C#, aby wykrywać brakujące czcionki, przechwytywać
  komunikaty o czcionkach i obsługiwać brakujące czcionki przy użyciu Aspose.Words.
  Pełny samouczek z kodem.
og_title: Utwórz FontSettings w C# – Wykryj brakujące czcionki i przechwyć komunikaty
  czcionek
tags:
- Aspose.Words
- C#
- Font Management
title: Utwórz FontSettings w C# – wykryj brakujące czcionki i przechwyć komunikaty
  o czcionkach
url: /pl/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz FontSettings w C# – Wykryj brakujące czcionki i przechwyć komunikaty o czcionkach

Czy kiedykolwiek potrzebowałeś **create FontSettings** w projekcie .NET, ale nie byłeś pewien, jak wykryć czcionki, które nie są zainstalowane na docelowej maszynie? Nie jesteś sam. W wielu rzeczywistych aplikacjach — pomyśl o generatorach raportów automatycznych lub konwerterach dokumentów — brakujące czcionki mogą cicho zepsuć układ i nie dowiesz się o tym, dopóki PDF nie będzie wyglądał nieprawidłowo.  

Co gdybyś mógł **detect missing fonts**, **capture font messages** i **handle missing fonts** zanim zepsują Twój wynik? Dobra wiadomość jest taka, że Aspose.Words sprawia, że to dziecinnie proste. W tym samouczku przeprowadzimy Cię przez cały proces, od skonfigurowania obiektu `FontSettings` po podłączenie callbacku ostrzeżeń, który dokładnie powie, które glify zostały podstawione.

> **TL;DR:** Po zakończeniu będziesz mieć gotową do uruchomienia aplikację konsolową C#, która loguje każdą podstawę czcionki, pozwalając Ci zdecydować, czy wbudować zamiennik, czy powiadomić użytkownika.

---

## Wymagania wstępne

- .NET 6 SDK (lub dowolna nowsza wersja .NET)  
- Visual Studio 2022 lub VS Code z rozszerzeniami C#  
- Licencja Aspose.Words for .NET (bezpłatna wersja próbna wystarczy do tego demo)  
- Przykładowy plik DOCX, który odwołuje się do czcionki, której nie masz zainstalowanej (np. *Comic Sans MS* na Linuxie)  

Nie są wymagane żadne specjalne pakiety NuGet poza `Aspose.Words`.

---

## Krok 1 – Zainstaluj Aspose.Words i skonfiguruj projekt

Na początek, utwórz nowy projekt konsolowy i dodaj bibliotekę Aspose.Words do projektu.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Jeśli już masz rozwiązanie, po prostu dodaj pakiet przez interfejs NuGet Package Manager — ułatwia to śledzenie wersji.

---

## Krok 2 – Utwórz FontSettings (Primary Keyword Appears Here)

Krok **create FontSettings** jest kamieniem węgielnym każdego przepływu pracy związanego z czcionkami. `FontSettings` informuje Aspose.Words, gdzie szukać czcionek, czy używać folderów systemowych oraz jak postępować, gdy coś brakuje.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Dlaczego to ważne? Bez prawidłowo skonfigurowanego `FontSettings` silnik cicho podstawia brakujące glify domyślną czcionką systemową i nigdy nie zobaczysz ostrzeżenia.

---

## Krok 3 – Połącz LoadOptions z FontSettings

`LoadOptions` pozwala przekazać `FontSettings` do ładowarki dokumentu. To most, który umożliwia silnikowi **detect missing fonts** podczas fazy konstrukcji `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Teraz za każdym razem, gdy załadujesz DOCX przy użyciu `loadOptions`, Aspose.Words skonsultuje się z wcześniej skonfigurowanym `FontSettings`.

---

## Krok 4 – Dołącz callback ostrzeżeń do **Capture Font Messages**

Aspose.Words generuje ostrzeżenia dla różnych warunków — podstawienie czcionki jest jednym z najczęstszych. Dostarczając implementację `IWarningCallback`, możesz **capture font messages** w czasie rzeczywistym.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Klasa obsługi ostrzeżeń

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Pole `info.Description` zawiera czytelną dla człowieka wiadomość, taką jak *„Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* To dokładnie taki rodzaj wyjścia, którego potrzebujesz, aby **handle missing fonts** w sposób elegancki.

---

## Krok 5 – Załaduj dokument i pozwól callbackowi wykonać swoją pracę

Po podłączeniu wszystkiego, ładowanie dokumentu jest proste. Jeśli plik źródłowy odwołuje się do czcionki nieobecnej w systemie, nasz handler ostrzeżeń zostanie wywołany.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Po uruchomieniu programu zobaczysz w konsoli wyjście podobne do:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

To wyjście jest częścią **capture font messages** naszego przepływu pracy. Możesz rozbudować handler, aby logował do pliku, wysyłał telemetry, lub nawet przerywał konwersję, jeśli brak krytycznych czcionek.

---

## Krok 6 – Pełny działający przykład (wszystkie elementy razem)

Poniżej znajduje się kompletny, gotowy do skopiowania program. Wklej go do `Program.cs`, dostosuj ścieżki plików i uruchom `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Oczekiwane wyjście

Uruchomienie programu na maszynie, która nie ma *Comic Sans MS*, wydrukuje coś w stylu:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Otrzymasz także `Result.pdf`, który używa podstawionych czcionek, zapewniając, że konwersja nigdy nie zawiedzie.

---

## Często zadawane pytania i przypadki brzegowe

| Question | Answer |
|----------|--------|
| **Co zrobić, jeśli chcę, aby konwersja zakończyła się błędem zamiast podstawienia?** | Wewnątrz `FontSubstitutionWarningHandler` rzuć wyjątek, gdy `info.Description` zawiera nazwę krytycznej czcionki. |
| **Czy mogę automatycznie osadzić zamienną czcionkę?** | Tak. Po wykryciu brakującej czcionki możesz załadować zastępczy `FontInfo` z znanej ścieżki i dodać go do `fontSettings` za pomocą `fontSettings.SetFontsFolder`. |
| **Czy to działa na Linux/macOS?** | Absolutnie. `FontSettings` działa wieloplatformowo; upewnij się tylko, że folder zastępczy zawiera odpowiednie pliki `.ttf` lub `.otf`. |
| **Czy callback ostrzeżeń jest bezpieczny wątkowo?** | Callback działa w tym samym wątku, który ładuje dokument, więc nie potrzebujesz dodatkowej synchronizacji dla logowania w konsoli. W scenariuszach wielowątkowych zabezpiecz współdzielone zasoby. |
| **Jak logować ostrzeżenia do pliku?** | Zastąp `Console.WriteLine` wywołaniem `File.AppendAllText("font_warnings.log", ...)` lub użyj dowolnego frameworka logowania (Serilog, NLog). |

## Pro tipy dla produkcyjnego zarządzania czcionkami

1. **Cache Font Lookups** – Ponowne użycie tej samej instancji `FontSettings` przy wielu ładowaniach dokumentów eliminuje powtarzające się skanowanie systemu plików.  
2. **Whitelist Critical Fonts** – Jeśli Twoja marka wymaga konkretnej czcionki, sprawdź jej obecność na wczesnym etapie i przerwij z czytelnym komunikatem o błędzie.  
3. **Use `SetFontFolder` Recursively** – Ustawienie `recursive: true` zapewnia skanowanie podfolderów, co jest przydatne, gdy dystrybuujesz całą kolekcję czcionek.  
4. **Combine with `FontSubstitutionSettings`** – Możesz precyzyjnie dostosować reguły podstawiania (np. preferować czcionki o tej samej nazwie rodziny).  

## Zakończenie

Właśnie **created FontSettings**, skonfigurowaliśmy `LoadOptions`, aby **detect missing fonts**, podłączyliśmy callback, który **captures font messages**, i pokazaliśmy, jak **handle missing fonts** w czysty, gotowy do produkcji sposób. Cały przepływ mieści się w kilkudziesięciu linijkach C#, a jednocześnie daje pełną widoczność krajobrazu czcionek w każdym przetwarzanym DOCX.

Następnie możesz zbadać:

- **Embedding fallback fonts** bezpośrednio do wyjściowego PDF (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programmatically substituting fonts** w oparciu o zasady brandingowe firmy.  
- **Integrating with a CI pipeline** aby automatycznie oznaczać dokumenty używające nieautoryzowanych czcionek.

Wypróbuj to, dostosuj handler ostrzeżeń do swoich potrzeb i pozwól swoim potokom dokumentów działać pewnie — koniec z tajemniczymi problemami układu spowodowanymi niewidzialnymi zamianami czcionek.

Szczęśliwego kodowania! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}