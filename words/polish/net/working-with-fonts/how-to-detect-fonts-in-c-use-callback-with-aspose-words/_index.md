---
category: general
date: 2026-03-17
description: Jak wykrywać czcionki w C# przy użyciu Aspose.Words i wywołania zwrotnego
  ostrzeżeń. Dowiedz się, jak używać wywołania zwrotnego do przechwytywania zastąpień
  brakujących czcionek podczas ładowania dokumentów.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: pl
og_description: Jak wykrywać czcionki w C# przy użyciu Aspose.Words. Ten przewodnik
  pokazuje, jak używać wywołania zwrotnego do przechwytywania ostrzeżeń o brakujących
  czcionkach podczas ładowania dokumentu.
og_title: Jak wykrywać czcionki w C# – użyj wywołania zwrotnego z Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak wykrywać czcionki w C# – użyj wywołania zwrotnego z Aspose.Words
url: /pl/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

unchanged.

Then heading "# How to Detect Fonts in C# – Use Callback with Aspose.Words" translate: "Jak wykrywać czcionki w C# – użycie callbacka z Aspose.Words". Keep #.

Proceed paragraph.

Translate accordingly.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wykrywać czcionki w C# – użycie callbacka z Aspose.Words

Kiedykolwiek potrzebowałeś **jak wykrywać czcionki** w dokumencie Word programowo i zastanawiałeś się, dlaczego niektóre znaki wyglądają dziwnie po konwersji? Nie jesteś sam. W wielu rzeczywistych projektach — generatorach faktur, eksporterach raportów czy potokach przetwarzania wsadowego — brakujące czcionki powodują ciche błędy układu, które trudno zdebugować.  

Dobra wiadomość? Aspose.Words oferuje prosty sposób na ujawnienie tych problemów za pomocą callbacka ostrzeżeń. W tym samouczku zobaczysz **jak używać callbacka**, aby przechwycić każde podstawienie czcionki, które Aspose wykonuje podczas ładowania dokumentu, i otrzymasz gotowy przykład, który wypisuje czytelny raport brakujących czcionek.

Omówimy:

* Minimalne wymagania (projekt .NET i pakiet NuGet Aspose.Words).  
* Jak zaimplementować `IWarningCallback`, aby nasłuchiwać `WarningType.FontSubstitution`.  
* Jak podłączyć callback do `LoadOptions` i załadować dokument.  
* Jak wygląda wyjściowy raport oraz kilka praktycznych wskazówek dla kodu produkcyjnego.

Po zakończeniu będziesz mógł automatycznie **wykrywać czcionki** w każdym pliku DOCX, DOC lub RTF i reagować na informacje o brakujących czcionkach — czy to logując, alarmując użytkownika, czy podstawiając czcionkę zapasową.

---

![Jak wykrywać czcionki w dokumencie Word przy użyciu callbacka ostrzeżeń Aspose.Words](https://example.com/images/detect-fonts.png "jak wykrywać czcionki w dokumencie Word")

## Co będzie potrzebne

* **.NET 6.0** lub nowszy (przykład kompiluje się także z .NET Framework 4.6+).  
* **Aspose.Words for .NET** – zainstaluj przez NuGet: `Install-Package Aspose.Words`.  
* Przykładowy plik Word, który celowo odwołuje się do czcionki, której nie masz zainstalowanej (np. `MissingFont.docx`).  

Nie są wymagane dodatkowe biblioteki; wszystko znajduje się w przestrzeni nazw Aspose.

---

## Jak wykrywać czcionki za pomocą callbacka ostrzeżeń

### Krok 1: Utwórz klasę callbacka ostrzeżeń

Callback implementuje `IWarningCallback`. Gdy Aspose.Words napotka czcionkę, której nie może znaleźć, podnosi `WarningInfo` z `WarningType.FontSubstitution`. Nasza klasa po prostu wypisuje przyjazną linię na konsolę.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Dlaczego to ważne:** Filtrując po `WarningType.FontSubstitution` unikamy hałaśliwych ostrzeżeń (np. o przestarzałych funkcjach) i utrzymujemy log skupiony na dokładnym problemie, który chcesz rozwiązać — **wykrywaniu czcionek**, które nie są obecne na maszynie.

---

### Krok 2: Podłącz callback do `LoadOptions`

`LoadOptions` pozwala dostosować sposób parsowania dokumentu. Przypisanie naszego `FontWarningCollector` do właściwości `WarningCallback` mówi Aspose, aby wywoływał go przy każdym brakującym fontcie.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Wskazówka:** Możesz także ustawić tutaj `LoadOptions.FontSettings`, jeśli chcesz programowo dostarczyć czcionkę zapasową. To zaawansowany scenariusz, o którym wspomnimy później.

---

### Krok 3: Załaduj dokument i obserwuj wynik

Teraz faktycznie ładujemy plik. Gdy tylko Aspose przetworzy dokument, każde nieodnalezione font wywoła nasz callback.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Oczekiwany wynik w konsoli** (zakładając, że dokument odwołuje się do *Comic Sans MS*, której nie ma zainstalowanej):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Jeśli dokument zawiera wiele brakujących czcionek, zobaczysz jedną linię na czcionkę — dokładnie informacje **jak wykrywać czcionki**, których potrzebujesz.

---

## Jak używać callbacka w bardziej złożonych scenariuszach

### Logowanie do pliku zamiast konsoli

W produkcji prawdopodobnie chcesz mieć trwały log. Zamień `Console.WriteLine` na `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Zbieranie ostrzeżeń do późniejszej analizy

Czasami potrzebna jest lista brakujących czcionek po załadowaniu dokumentu, np. aby wyświetlić dialog UI. Przechowaj ostrzeżenia w `List<string>` i udostępnij je:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Programowe dostarczanie czcionki zapasowej

Jeśli masz firmową czcionkę, którą chcesz wymusić, możesz dodać ją do `FontSettings` przed ładowaniem:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Teraz Aspose podstawia brakujące czcionki *Arial Unicode MS*, jednocześnie raportując podstawienie przez callback. To sprytny sposób na **jak używać callbacka** zarówno do wykrywania, jak i automatycznej naprawy.

---

## Typowe pułapki i wskazówki dla zaawansowanych

| Pułapka | Dlaczego się pojawia | Jak uniknąć |
|--------|----------------------|-------------|
| **Zapomnienie o odwołaniu do `Aspose.Words.Warnings`** | Interfejs `IWarningCallback` znajduje się w tej przestrzeni nazw. | Dodaj `using Aspose.Words.Warnings;` na początku pliku. |
| **Ładowanie dokumentu bez `LoadOptions`** | Domyślny loader cicho podstawia czcionki bez powiadomienia. | Zawsze twórz instancję `LoadOptions` i przypisuj swój callback. |
| **Uruchamianie na serwerze z ograniczonymi uprawnieniami** | Zapisywanie do pliku logu może wywołać `UnauthorizedAccessException`. | Użyj folderu zapisywalnego (np. katalog danych aplikacji) lub trzymaj się kolekcji w pamięci. |
| **Wiele wątków współdzielących ten sam collector** | `FontWarningCollector` nie jest domyślnie wątkowo‑bezpieczny. | Utwórz oddzielny collector dla każdego wątku lub zabezpiecz listę przy pomocy blokady. |
| **Zakładanie, że callback uruchamia się dla czcionek osadzonych** | Czcionki osadzone są już w dokumencie; nie generują ostrzeżenia. | Jeśli musisz zweryfikować integralność czcionek osadzonych, sprawdź `FontInfo` przez `FontSettings`. |

---

## Pełny działający przykład (gotowy do skopiowania)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Co powinno się pojawić** (zakładając, że plik odwołuje się do dwóch nieobecnych czcionek):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Jeśli plik używa wyłącznie zainstalowanych czcionek, konsola po prostu wypisze:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Podsumowanie

Przeszliśmy przez **jak wykrywać czcionki** w dokumencie Word, podłączając własny callback ostrzeżeń do Aspose.Words. Podejście jest lekkie, wymaga

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}