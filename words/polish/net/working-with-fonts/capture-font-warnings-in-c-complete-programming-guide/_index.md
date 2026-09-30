---
category: general
date: 2026-02-18
description: Dowiedz się, jak przechwytywać ostrzeżenia dotyczące czcionek i wykrywać
  brakujące czcionki w C# przy użyciu Aspose.Words. Skorzystaj z tego przewodnika
  krok po kroku, aby skutecznie radzić sobie z brakującymi czcionkami.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: pl
og_description: Przechwytuj ostrzeżenia o czcionkach w C# i dowiedz się, jak wykrywać
  brakujące czcionki, obsługiwać je oraz wyświetlać ich listę w pełnym przykładzie
  kodu.
og_title: Przechwytywanie ostrzeżeń czcionek w C# – Kompletny przewodnik
tags:
- Aspose.Words
- C#
- Font Management
title: Przechwytywanie ostrzeżeń czcionek w C# – Kompletny przewodnik programistyczny
url: /pl/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

. There are none besides image.png which we kept same.

Now produce final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Przechwytywanie ostrzeżeń dotyczących czcionek w C# – Kompletny przewodnik programistyczny

Zastanawiałeś się kiedyś, jak **przechwycić ostrzeżenia dotyczące czcionek**, gdy dokument odwołuje się do czcionki, która nie jest zainstalowana na serwerze? Nie jesteś jedyny. W wielu aplikacjach korporacyjnych brakujące czcionki powodują problemy z układem, a jedynym niezawodnym sposobem ich wykrycia jest nasłuchiwanie ostrzeżeń generowanych przez bibliotekę.  

W tym samouczku pokażemy Ci gotowe do uruchomienia rozwiązanie, które nie tylko **przechwytuje ostrzeżenia dotyczące czcionek**, ale także **wykrywa brakujące czcionki**, **obsługuje brakujące czcionki**, a nawet **wyświetla listę brakujących czcionek**, dzięki czemu możesz zdecydować, czy podmienić, osadzić je, czy powiadomić użytkownika. Nie potrzebujesz dodatkowej dokumentacji — wystarczy skopiować, wkleić i uruchomić.

## Czego się nauczysz

- Jak skonfigurować `LoadOptions`, aby włączyć ostrzeżenia o podstawianiu czcionek.  
- Dokładny kod potrzebny do załadowania pliku DOCX i wyciągnięcia każdego ostrzeżenia.  
- Dlaczego każdy krok ma znaczenie, w tym względy wydajności.  
- Obsługa przypadków brzegowych, takich jak dokumenty z czcionkami mieszanych skryptów lub własne foldery czcionek.  

**Wymagania wstępne**: .NET 6+ (lub .NET Framework 4.6+), odwołanie do pakietu NuGet **Aspose.Words** oraz podstawowa znajomość C#. Jeśli nigdy nie używałeś Aspose.Words, nie martw się — ten przewodnik przeprowadzi Cię przez wszystkie niuanse.

![Diagram showing capture font warnings flow](image.png){alt="diagram przechwytywania ostrzeżeń czcionek"}

## Przechwytywanie ostrzeżeń czcionek – dlaczego ma to znaczenie

Gdy Aspose.Words ładuje dokument, cicho zamienia każdą niedostępną czcionkę na zapasową. Ta zapasowa czcionka utrzymuje operację ładowania, ale wynik wizualny może być całkowicie nieprawidłowy. Włączając flagę **SubstitutionWarningLevel.All**, biblioteka dodaje wpis `WarningInfo` dla każdej brakującej czcionki, co pozwala **wykrywać brakujące czcionki** przed renderowaniem lub zapisem dokumentu.

> **Pro tip:** Jeśli przetwarzasz setki plików w zadaniu wsadowym, logowanie tych ostrzeżeń w centralnym repozytorium może zaoszczędzić Ci godziny ręcznej kontroli jakości później.

## Krok 1: Przygotuj projekt

1. Otwórz swoje ulubione IDE (Visual Studio, Rider, VS Code).  
2. Utwórz nowy projekt konsolowy:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Dodaj pakiet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

To wszystko — bez dodatkowych plików DLL, bez interfejsu COM. Biblioteka dostarcza wszystko, co potrzebne do **obsługi brakujących czcionek**.

## Krok 2: Przygotuj opcje ładowania, aby przechwycić wszystkie ostrzeżenia o podstawianiu czcionek

Aby silnik **przechwytywał ostrzeżenia czcionek**, musisz go poinstruować, aby rejestrował każde podstawienie. Poniższy fragment kodu tworzy instancję `LoadOptions`, włącza poziom ostrzeżeń i (opcjonalnie) wskazuje silnikowi folder zawierający własne czcionki, które możesz chcieć używać.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Dlaczego to ważne:**  
- `SubstitutionWarningLevel.All` zapewnia, że **każde** zdarzenie brakującej czcionki jest rejestrowane, a nie tylko pierwsze.  
- Bez tej flagi Aspose.Words cicho podmienia czcionkę i nigdy nie dowiesz się, że istnieje problem.

## Krok 3: Załaduj dokument przy użyciu skonfigurowanych opcji

Teraz faktycznie otwieramy plik. Zastąp `DocumentWithMissingFonts.docx` ścieżką do swojego dokumentu testowego.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Jeśli plik zawiera odwołania do czcionek, które nie znajdują się na maszynie (lub w opcjonalnym folderze, który dodałeś), `document.WarningInfoCollection` zostanie wypełniona.

## Krok 4: Znajdź i wyświetl wszystkie ostrzeżenia o podstawianiu czcionek

Oto sedno samouczka: iterowanie po `WarningInfoCollection`, aby **wyświetlić brakujące czcionki**. Przefiltrujemy według `WarningType.FontSubstitution` i wydrukujemy przyjazny komunikat.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Oczekiwany wynik

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Jeśli dokument używa tylko zainstalowanych czcionek, zobaczysz linię „✅ No missing fonts detected”.

## Krok 5: Zaawansowane – Jak programowo **obsługiwać brakujące czcionki**

Proste wypisanie listy może wystarczyć dla narzędzia diagnostycznego, ale wiele systemów produkcyjnych wymaga automatycznej **obsługi brakujących czcionek**. Poniżej dwie popularne strategie:

### 5.1 Podstawienie znanym zamiennikiem

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Osadzenie własnej czcionki w locie

Jeśli masz plik czcionki firmowej (`MyBrand.ttf`), możesz go osadzić, gdy zostanie wykryta brakująca czcionka:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Uwaga:** Osadzanie czcionek może zwiększyć rozmiar pliku wyjściowego, więc rozważ kompromis między wiernością a przepustowością.

## Typowe pułapki i jak ich uniknąć

| Objaw | Prawdopodobna przyczyna | Rozwiązanie |
|-------|--------------------------|-------------|
| Brak ostrzeżeń, mimo że dokument wygląda niepoprawnie | `SubstitutionWarningLevel` nie ustawiony na `All` | Upewnij się, że krok 2 ustawia flagę dokładnie tak, jak pokazano |
| Ostrzeżenia wymieniają tę samą czcionkę wielokrotnie | Dokument zawiera czcionkę w kilku stylach | Usuń duplikaty, jeśli potrzebna jest tylko unikalna lista: `fontWarnings.Select(w => w.Description).Distinct()` |
| Aplikacja się zawiesza przy dużych plikach DOCX | Ładowanie z domyślnymi ustawieniami pamięci | Użyj `LoadOptions.LoadFormat` lub strumieniuj plik, aby zmniejszyć obciążenie pamięci |

## Pełny działający przykład (gotowy do kopiowania i wklejania)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Uruchom program poleceniem `dotnet run`. Powinieneś zobaczyć listę brakujących czcionek wypisaną w konsoli, co potwierdza, że pomyślnie **przechwyciłeś ostrzeżenia czcionek**.

## Podsumowanie

Masz teraz kompletny, gotowy do produkcji wzorzec do **przechwytywania ostrzeżeń czcionek**, **wykrywania brakujących czcionek**, **obsługi brakujących czcionek** oraz **wyświetlania listy brakujących czcionek** przy użyciu Aspose.Words w C#. Podejście jest lekkie, wymaga tylko kilku linii kodu i może być wstawione do dowolnego istniejącego potoku — niezależnie od tego, czy...

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}