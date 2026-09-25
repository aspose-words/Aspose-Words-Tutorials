---
category: general
date: 2026-02-28
description: Dowiedz się, jak obsługiwać ostrzeżenia dotyczące czcionek i wykrywać
  brakujące czcionki w Aspose.Words przy użyciu C#. Kompletny przewodnik krok po kroku
  z pełnym kodem.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: pl
og_description: Obsłuż ostrzeżenia dotyczące czcionek w Aspose.Words i wykryj brakujące
  czcionki za pomocą gotowego przykładu w C#. Postępuj zgodnie z instrukcjami i zobacz
  wynik.
og_title: Obsługa ostrzeżeń czcionek w Aspose.Words – Kompletny przewodnik
tags:
- Aspose.Words
- C#
- Document Loading
title: Obsługa ostrzeżeń o czcionkach w Aspose.Words – wykrywanie brakujących czcionek
url: /pl/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obsługa ostrzeżeń czcionek w Aspose.Words – Wykrywanie brakujących czcionek

Czy kiedykolwiek musiałeś **obsługiwać ostrzeżenia czcionek** podczas ładowania dokumentu Word i zastanawiałeś się, dlaczego niektóry tekst wygląda dziwnie? Nie jesteś sam. Brakujące czcionki wywołują ostrzeżenia o podstawieniu, które mogą po cichu zepsuć układ wizualny, a jeśli nie **wykryjesz brakujących czcionek**, nigdy nie dowiesz się, co poszło nie tak.

W tym samouczku pokażemy praktyczny sposób **obsługi ostrzeżeń czcionek** przy użyciu `IWarningCallback` z Aspose.Words. Po zakończeniu przewodnika będziesz w stanie wykrywać każde zdarzenie podstawienia czcionki, rejestrować je i nawet zdecydować, czy przerwać ładowanie. Bez zewnętrznych dokumentów, tylko jeden gotowy do skopiowania przykład.

## Czego się nauczysz

- Skonfiguruj własny obsługiwacz ostrzeżeń, który reaguje tylko na alerty o podstawieniu czcionki.  
- Dołącz obsługiwacz do `LoadOptions`, aby każde ładowanie dokumentu przechodziło przez niego.  
- Sprawdź wyjście w konsoli i zrozum, co oznacza każde ostrzeżenie.  

**Wymagania wstępne**

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+).  
- Aspose.Words for .NET zainstalowany przez NuGet (`Install-Package Aspose.Words`).  
- Plik Word, który odwołuje się do czcionki niezainstalowanej na twoim komputerze (np. własna czcionka firmowa).  

Jeśli czegoś brakuje, zdobądź to teraz — w przeciwnym razie, przejdźmy dalej.

## Jak obsługiwać ostrzeżenia czcionek w Aspose.Words

Poniżej znajduje się pełny, gotowy do uruchomienia program. Zawiera wszystko od dyrektyw `using` po metodę `Main`, więc możesz go wkleić do aplikacji konsolowej i nacisnąć **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Oczekiwany output w konsoli** (zakładając, że dokument używa czcionki, której nie masz zainstalowanej):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Jeśli dokument nie zawiera **brakujących czcionek**, linia ostrzeżenia nigdy się nie pojawia — więc skutecznie **wykryłeś brakujące czcionki** tylko wtedy, gdy było to potrzebne.

### Dlaczego to działa

Aspose.Words generuje `WarningInfo` dla każdego niekrytycznego problemu, na który natrafi podczas parsowania pliku. Implementując `IWarningCallback` uzyskujesz punkt zaczepienia w tym procesie. Flaga `WarningType.FontSubstitution` informuje dokładnie, kiedy biblioteka musiała zastąpić żądaną czcionkę alternatywną. To najpewniejszy sposób **obsługi ostrzeżeń czcionek**, ponieważ działa *podczas* ładowania, zanim jeszcze dotkniesz modelu obiektowego dokumentu.

## Wykrywanie brakujących czcionek bez przerywania działania aplikacji

Czasami możesz chcieć traktować brakującą czcionkę jako błąd krytyczny — być może wytyczne Twojej marki zakazują jakiejkolwiek zamiany. Możesz zmodyfikować obsługiwacz, aby rzucał wyjątek zamiast jedynie logować:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Teraz blok `try…catch` wokół `new Document(...)` przechwyci problem, pozwalając Ci zdecydować, czy przerwać, użyć awaryjnego rozwiązania, czy poprosić użytkownika.

## Bonus: Wizualizacja ostrzeżeń w aplikacji UI

Jeśli tworzysz aplikację WinForms lub WPF, zamień `Console.WriteLine` na wywołanie przyjazne UI:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

W ten sposób użytkownicy końcowi zobaczą ostrzeżenie od razu, a Ty nadal **obsługujesz ostrzeżenia czcionek** konsekwentnie na wszystkich platformach.

## Częste pułapki i wskazówki profesjonalistów

- **Pułapka:** Zapomnienie o ustawieniu `WarningCallback`. Domyślne zachowanie to ignorowanie ostrzeżeń czcionek, więc nigdy ich nie zobaczysz.  
  **Wskazówka:** Zawsze twórz instancję `LoadOptions`, nawet jeśli potrzebujesz tylko obsługiwacza ostrzeżeń. To tanie i wyraźne.  

- **Pułapka:** Używanie niewłaściwego separatora ścieżek na systemach nie‑Windows.  
  **Wskazówka:** Używaj `Path.Combine` lub surowego literału ciągu (`@"C:\Docs\MissingFont.docx"` działa na Windows; na Linux użyj `"/home/user/docs/MissingFont.docx"`).  

- **Pułapka:** Zakładanie, że ostrzeżenie zostanie wywołane dla czcionek osadzonych.  
  **Wskazówka:** Osadzone czcionki są uznawane za dostępne, więc nie pojawia się ostrzeżenie o podstawieniu. Testuj z naprawdę *brakującymi* czcionkami, aby zobaczyć działanie obsługiwacza.  

- **Pułapka:** Nadmierne logowanie każdego typu ostrzeżenia.  
  **Wskazówka:** Filtruj po `WarningType.FontSubstitution`, jak pokazano — to utrzymuje konsolę w czystości i skupia się na scenariuszu **wykrywania brakujących czcionek**.  

## Pełny działający przykład – podsumowanie

Oto cały program ponownie, tym razem bez komentarzy dla tych, którzy wolą czysty widok:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Skopiuj, wklej, uruchom — twoja konsola teraz **obsłuży ostrzeżenia czcionek** i automatycznie **wykryje brakujące czcionki**.

## Kolejne kroki

- **Logowanie do pliku:** Zamień `Console.WriteLine` na logger (np. NLog) dla śledzenia na poziomie produkcyjnym.  
- **Przetwarzanie wsadowe:** Przejdź przez folder dokumentów, zbierając wszystkie zdarzenia podstawienia czcionek w raporcie CSV.  
- **Automatyczna instalacja czcionek:** Podłącz się do obsługiwacza ostrzeżeń, aby pobrać brakujące czcionki z repozytorium firmowego przed kontynuacją ładowania.  

Każde z tych rozszerzeń opiera się na podstawowej idei **obsługi ostrzeżeń czcionek** w czysty, wielokrotnego użytku sposób.

---

*Szczęśliwego kodowania! Jeśli napotkasz jakiekolwiek problemy podczas próby **wykrywania brakujących czcionek**, zostaw komentarz poniżej. Chętnie pomogę rozwiązać problem.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}