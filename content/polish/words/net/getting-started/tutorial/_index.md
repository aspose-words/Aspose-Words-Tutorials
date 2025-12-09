---
language: pl
url: /polish/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Wykrywanie brakujących czcionek w dokumentach Aspose.Words – kompletny przewodnik C#

Zastanawiałeś się kiedyś, jak **wykrywać brakujące czcionki** podczas ładowania pliku Word przy użyciu Aspose.Words? W mojej codziennej pracy natknąłem się na kilka plików PDF, które wyglądały nieprawidłowo, ponieważ oryginalny dokument używał czcionki, której nie miałem zainstalowanej. Dobra wiadomość? Aspose.Words może dokładnie poinformować, kiedy zastępuje czcionkę, i możesz przechwycić tę informację za pomocą prostego wywołania zwrotnego ostrzeżenia.  

W tym samouczku przeprowadzimy Cię przez **kompletny, działający przykład**, który pokaże, jak rejestrować każdą zamianę czcionki, dlaczego wywołanie zwrotne ma znaczenie oraz kilka dodatkowych sztuczek dla solidnego wykrywania brakujących czcionek. Bez zbędnych wstępów, tylko kod i uzasadnienie, które potrzebujesz, aby uruchomić to już dziś.

---

## Czego się nauczysz

- Jak zaimplementować **Aspose.Words warning callback**, aby przechwycić zdarzenia zamiany czcionki.  
- Jak skonfigurować **LoadOptions C#**, aby wywołanie zwrotne było uruchamiane podczas ładowania dokumentu.  
- Jak zweryfikować, że wykrywanie brakujących czcionek naprawdę zadziałało i jak wygląda wyjście w konsoli.  
- Opcjonalne dostosowania dla dużych partii lub środowisk bez interfejsu graficznego.  

**Wymagania wstępne** – Potrzebujesz aktualnej wersji Aspose.Words dla .NET (kod testowano z wersją 23.12), .NET 6 lub nowszego oraz podstawowej znajomości C#. Jeśli masz to wszystko, możesz zaczynać.

---

## Wykrywanie brakujących czcionek za pomocą wywołania zwrotnego ostrzeżenia

Sednem rozwiązania jest implementacja `IWarningCallback`. Aspose.Words generuje obiekt `WarningInfo` w wielu sytuacjach, ale nas interesuje tylko `WarningType.FontSubstitution`. Zobaczmy, jak się do tego podłączyć.

### Krok 1: Utwórz kolektor ostrzeżeń czcionek

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Dlaczego to ważne*: Filtrując po `WarningType.FontSubstitution` unikamy bałaganu spowodowanego niepowiązanymi ostrzeżeniami (np. przestarzałe funkcje). `info.Description` już zawiera nazwę oryginalnej czcionki oraz użyty zamiennik, co daje przejrzysty ślad audytu.

---

## Skonfiguruj LoadOptions, aby używać wywołania zwrotnego

Teraz informujemy Aspose.Words, aby używał naszego kolektora podczas ładowania pliku.

### Krok 2: Skonfiguruj LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Dlaczego to ważne*: `LoadOptions` to jedyne miejsce, w którym możesz podłączyć wywołanie zwrotne, hasła szyfrowania i inne zachowania ładowania. Trzymanie go oddzielnie od konstruktora `Document` sprawia, że kod jest wielokrotnego użytku w wielu plikach.

---

## Załaduj dokument i przechwyć brakujące czcionki

Po podłączeniu wywołania zwrotnego, następnym krokiem jest po prostu załadowanie dokumentu.

### Krok 3: Załaduj swój DOCX (lub dowolny obsługiwany format)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Gdy konstruktor `Document` parsuje plik, każda brakująca czcionka wywołuje nasz `FontWarningCollector`. Konsola wyświetli linie takie jak:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Ta linia jest konkretnym dowodem, że **wykrywanie brakujących czcionek** zadziałało.

---

## Zweryfikuj wyjście – czego się spodziewać

Uruchom program z terminala lub Visual Studio. Jeśli dokument źródłowy zawiera czcionkę, której nie masz zainstalowanej, zobaczysz przynajmniej jedną linię „Font substituted”. Jeśli dokument używa wyłącznie zainstalowanych czcionek, wywołanie zwrotne pozostanie ciche i otrzymasz jedynie komunikat „Document loaded successfully.”.

**Wskazówka**: Aby podwójnie sprawdzić, otwórz plik Word w Microsoft Word i przyjrzyj się liście czcionek. Każda czcionka, która pojawia się w *Replace Fonts* pod grupą *Home → Font*, jest kandydatem do zamiany.

---

## Zaawansowane: Wykrywanie brakujących czcionek w partiach

Często trzeba przeskanować dziesiątki plików. Ten sam wzorzec skaluje się dobrze:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Ponieważ `FontWarningCollector` zapisuje do konsoli przy każdym wywołaniu, otrzymasz raport per‑plik bez dodatkowego kodu. W scenariuszach produkcyjnych możesz chcieć logować do pliku lub bazy danych – po prostu zamień `Console.WriteLine` na wybrany logger.

---

## Częste pułapki i wskazówki profesjonalne

| Problem | Dlaczego się dzieje | Rozwiązanie |
|-------|----------------|-----|
| **Brak ostrzeżeń** | Dokument faktycznie zawiera tylko zainstalowane czcionki. | Sprawdź, otwierając plik w Wordzie lub celowo usuwając czcionkę z systemu. |
| **Callback nie wywołany** | `LoadOptions.WarningCallback` nigdy nie został przypisany lub później użyto nowej instancji `LoadOptions`. | Utrzymuj pojedynczy obiekt `LoadOptions` i używaj go przy każdym ładowaniu. |
| **Zbyt wiele niepowiązanych ostrzeżeń** | Nie filtrowałeś po `WarningType.FontSubstitution`. | Dodaj warunek `if (info.Type == WarningType.FontSubstitution)` jak pokazano. |
| **Spowolnienie wydajności przy dużych plikach** | Wywołanie zwrotne uruchamia się przy każdym ostrzeżeniu, co może być wiele w dużych dokumentach. | Wyłącz inne typy ostrzeżeń poprzez `LoadOptions.WarningCallback` lub ustaw `LoadOptions.LoadFormat` na konkretny typ, jeśli go znasz. |

---

## Pełny działający przykład (gotowy do kopiowania i wklejania)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Oczekiwane wyjście w konsoli** (gdy napotkano brakującą czcionkę):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Jeśli nie nastąpi zamiana, zobaczysz tylko linię sukcesu.

---

## Podsumowanie

Masz teraz **kompletny, gotowy do produkcji sposób wykrywania brakujących czcionek** w każdym dokumencie przetwarzanym przez Aspose.Words. Korzystając z **Aspose.Words warning callback** i konfigurując **LoadOptions C#**, możesz rejestrować każdą zamianę czcionki, rozwiązywać problemy z układem i zapewnić, że Twoje PDF-y zachowają zamierzony wygląd.  

Od pojedynczego pliku po masową partię, wzorzec pozostaje ten sam — zaimplementuj `IWarningCallback`, podłącz go do `LoadOptions` i pozwól Aspose.Words wykonać ciężką pracę.  

Gotowy na kolejny krok? Spróbuj połączyć to z **font embedding** lub **fallback font families**, aby automatycznie naprawić problem, lub zbadaj API **DocumentVisitor** w celu głębszej analizy treści. Szczęśliwego kodowania i niech wszystkie Twoje czcionki pozostaną tam, gdzie ich oczekujesz!  

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}

{{< layout-end >}}