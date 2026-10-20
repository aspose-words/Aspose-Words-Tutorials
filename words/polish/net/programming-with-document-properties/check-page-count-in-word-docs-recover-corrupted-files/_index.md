---
category: general
date: 2026-03-30
description: Sprawdź liczbę stron w dokumentach Word, jednocześnie ucząc się odzyskiwać
  uszkodzony plik Word i wykrywać uszkodzony plik Word przy użyciu Aspose.Words.
draft: false
keywords:
- check page count
- recover corrupted word file
- detect corrupted word file
- Aspose.Words
- C# document loading
language: pl
og_description: Sprawdź liczbę stron w dokumentach Word i dowiedz się, jak odzyskać
  uszkodzony plik Word przy użyciu Aspose.Words. Samouczek krok po kroku w C#.
og_title: Sprawdź liczbę stron w dokumentach Word – Kompletny przewodnik
tags:
- Aspose.Words
- C#
- document processing
title: Sprawdź liczbę stron w dokumentach Word – odzyskaj uszkodzone pliki
url: /pl/net/programming-with-document-properties/check-page-count-in-word-docs-recover-corrupted-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sprawdź liczbę stron w dokumentach Word – odzyskaj uszkodzone pliki

Czy kiedykolwiek potrzebowałeś **sprawdzić liczbę stron** w dokumencie Word, ale nie byłeś pewien, czy plik jest nadal zdrowy? Nie jesteś sam. W wielu pipeline'ach automatyzacji pierwszą rzeczą, którą robimy, jest weryfikacja długości dokumentu, a jednocześnie często musimy **wykrywać problemy z uszkodzonym plikiem Word**, zanim cały proces się zawiesi.  

W tym samouczku przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład w C#, który pokazuje, jak **sprawdzić liczbę stron**, a jednocześnie demonstruje najlepszy sposób **odzyskiwania uszkodzonego pliku Word** przy użyciu Aspose.Words LoadOptions. Po zakończeniu dokładnie zrozumiesz, dlaczego każde ustawienie ma znaczenie, jak obsługiwać przypadki brzegowe i na co zwracać uwagę, gdy plik odmawia otwarcia.

---

## Czego się nauczysz

- Jak skonfigurować `LoadOptions`, aby **wykrywać problemy z uszkodzonym plikiem Word**.
- Różnicę między `RecoveryMode.Strict` a `RecoveryMode.Auto`.
- Niezawodny wzorzec ładowania dokumentu i bezpiecznego **sprawdzania liczby stron**.
- Typowe pułapki (brak pliku, błędy uprawnień, nieoczekiwany format) i jak ich unikać.
- Pełny, gotowy do skopiowania i wklejenia kod, który możesz uruchomić już dziś.

> **Wymagania wstępne**: .NET 6+ (lub .NET Framework 4.7+), Visual Studio 2022 (lub dowolne IDE C#) oraz licencja Aspose.Words dla .NET (bezpłatna wersja próbna działa w tej demonstracji).

---

## Krok 1 – Zainstaluj Aspose.Words

Na początek potrzebujesz pakietu NuGet Aspose.Words. Otwórz terminal w folderze projektu i uruchom:

```bash
dotnet add package Aspose.Words
```

To pojedyncze polecenie pobiera wszystko, czego potrzebujesz — nie musisz szukać dodatkowych plików DLL. Jeśli używasz Visual Studio, możesz również zainstalować go poprzez interfejs NuGet Package Manager UI.

---

## Krok 2 – Skonfiguruj LoadOptions, aby **wykrywać uszkodzony plik Word**

Sercem rozwiązania jest klasa `LoadOptions`. Pozwala ona określić Aspose.Words, jak rygorystycznie ma podchodzić do napotkania problematycznego pliku.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Choose a recovery strategy.
// Strict → throws an exception the moment corruption is spotted.
// Auto   → tries to salvage what it can and keeps loading.
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Strict   // <‑‑ change to Auto if you prefer auto‑recovery
};
```

**Dlaczego to ważne**: Jeśli pozwolisz bibliotece cicho zgadywać, możesz skończyć z dokumentem, któremu brakuje stron — co czyni późniejsze operacje **sprawdzania liczby stron** niewiarygodnymi. Użycie `Strict` zmusza do obsłużenia problemu od razu, co jest bezpieczniejszym wyborem w pipeline'ach produkcyjnych.

---

## Krok 3 – Załaduj dokument i **sprawdź liczbę stron**

Teraz faktycznie otwieramy plik. Konstruktor `Document` przyjmuje ścieżkę oraz `LoadOptions`, które właśnie skonfigurowaliśmy.

```csharp
try
{
    // Replace the placeholder with the real path to your .docx file.
    const string filePath = @"C:\Docs\maybeCorrupt.docx";

    // Load the document using the strict recovery mode we set above.
    Document doc = new Document(filePath, loadOptions);

    // If we reach this line, the file is considered healthy enough.
    Console.WriteLine($"✅ Document loaded successfully. Page count: {doc.PageCount}");

    // You can now safely use the page count for any downstream logic.
    // Example: abort processing if the document is unexpectedly short.
    if (doc.PageCount < 2)
    {
        Console.WriteLine("⚠️ Document seems too short – double‑check the source.");
    }
}
catch (Exception ex) when (ex is FileCorruptedException || ex is LoadOptionsException)
{
    // This block runs only when Strict mode catches corruption.
    Console.WriteLine($"❌ Failed to load document: {ex.Message}");
    // Optional: switch to Auto mode on the fly, then retry.
    loadOptions.RecoveryMode = RecoveryMode.Auto;
    Console.WriteLine("🔄 Retrying with Auto recovery mode…");
    // Recursive retry is omitted for brevity—see Step 5 for a reusable method.
}
```

**Co widzisz**:

- Wzorzec `try/catch` zapewnia czysty sposób **wykrywania uszkodzonego pliku Word**.
- `doc.PageCount` to właściwość, która faktycznie **sprawdza liczbę stron**.
- Warunek po `Console.WriteLine` pokazuje realistyczny scenariusz, w którym możesz przerwać działanie, jeśli dokument jest nieoczekiwanie krótki.

---

## Krok 4 – Obsługuj przypadki brzegowe w sposób elegancki

Kod w rzeczywistym świecie rzadko działa w próżni. Poniżej trzy typowe scenariusze „co‑jeśli” i sposoby ich obsługi.

### 4.1 Plik nie znaleziony

```csharp
if (!File.Exists(filePath))
{
    Console.WriteLine($"❗ File not found: {filePath}");
    return; // Bail out early – nothing to load.
}
```

### 4.2 Brak wystarczających uprawnień

```csharp
try
{
    // Attempt to open with read‑only sharing.
    using var stream = new FileStream(filePath, FileMode.Open, FileAccess.Read, FileShare.Read);
    Document doc = new Document(stream, loadOptions);
    Console.WriteLine($"📄 Page count: {doc.PageCount}");
}
catch (UnauthorizedAccessException)
{
    Console.WriteLine("🔐 You don’t have permission to read this file.");
}
```

### 4.3 Automatyczne odzyskiwanie – awaryjny fallback

Jeśli uznasz, że ciche przywrócenie pliku jest dopuszczalne, opakuj automatyczne odzyskiwanie w metodę pomocniczą:

```csharp
static Document LoadWithFallback(string path)
{
    var options = new LoadOptions { RecoveryMode = RecoveryMode.Strict };
    try
    {
        return new Document(path, options);
    }
    catch
    {
        // Switch to Auto and try again.
        options.RecoveryMode = RecoveryMode.Auto;
        return new Document(path, options);
    }
}
```

Teraz masz jedną linię `Document doc = LoadWithFallback(filePath);`, która zawsze zwraca instancję `Document` — albo nienaruszoną, albo odzyskaną w miarę możliwości.

---

## Krok 5 – Pełny działający przykład (gotowy do kopiowania i wklejania)

Poniżej znajduje się cały program, gotowy do wstawienia w projekt aplikacji konsolowej. Zawiera wszystkie wskazówki z poprzednich kroków.

```csharp
// ------------------------------------------------------------
// Check Page Count in Word Docs – Recover Corrupted Files
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        const string filePath = @"C:\Docs\maybeCorrupt.docx";

        // 1️⃣ Verify the file exists.
        if (!File.Exists(filePath))
        {
            Console.WriteLine($"❗ File not found: {filePath}");
            return;
        }

        // 2️⃣ Try loading with strict recovery mode.
        Document doc = LoadDocument(filePath, RecoveryMode.Strict);

        // 3️⃣ If we have a document, we can safely check page count.
        Console.WriteLine($"✅ Document loaded. Page count: {doc.PageCount}");

        // 4️⃣ Example business rule – abort if too few pages.
        if (doc.PageCount < 2)
        {
            Console.WriteLine("⚠️ Document seems too short – investigate the source file.");
        }
    }

    /// <summary>
    /// Loads a Word document using the specified recovery mode.
    /// Falls back to Auto mode if Strict fails.
    /// </summary>
    static Document LoadDocument(string path, RecoveryMode mode)
    {
        var options = new LoadOptions { RecoveryMode = mode };

        try
        {
            return new Document(path, options);
        }
        catch (Exception ex) when (ex is FileCorruptedException || ex is LoadOptionsException)
        {
            Console.WriteLine($"❌ Strict mode failed: {ex.Message}");
            Console.WriteLine("🔄 Switching to Auto recovery mode…");
            options.RecoveryMode = RecoveryMode.Auto;
            return new Document(path, options); // Auto will attempt to salvage.
        }
    }
}
```

**Oczekiwany wynik (zdrowy plik)**:

```
✅ Document loaded. Page count: 12
```

**Oczekiwany wynik (uszkodzony plik, tryb strict)**:

```
❌ Strict mode failed: The file is corrupted and cannot be opened.
🔄 Switching to Auto recovery mode…
✅ Document loaded. Page count: 8   // Might be less than original.
```

---

## Krok 6 – Porady profesjonalne i typowe pułapki

- **Porada:** Zawsze loguj użyty `RecoveryMode`. Kiedy później audytujesz uruchomienie wsadu, będziesz wiedział, które pliki zostały automatycznie odzyskane.
- **Uwaga:** Dokumenty zawierające osadzone obiekty (wykresy, SmartArt). Tryb Auto może je pominąć, co może wpłynąć na układ stron i tym samym na wynik **sprawdzania liczby stron**.
- **Uwaga dotycząca wydajności:** `RecoveryMode.Auto` jest nieco wolniejszy, ponieważ Aspose.Words wykonuje dodatkowe przebiegi walidacji. Jeśli przetwarzasz tysiące plików, trzymaj się `Strict` i używaj fallbacku tylko w razie potrzeby dla konkretnego pliku.
- **Sprawdzenie wersji:** Powyższy kod działa z Aspose.Words 22.12 i nowszymi. Wcześniejsze wersje miały inną nazwę enum (`LoadOptions.RecoveryMode` wprowadzono w 20.10).

---

## Zakończenie

Masz teraz solidny, gotowy do produkcji wzorzec do **sprawdzania liczby stron** w dokumentach Word, a także wiesz, jak **odzyskać uszkodzony plik Word** i **wykrywać uszkodzone pliki Word** przy użyciu Aspose.Words. Najważniejsze wnioski to:

1. Skonfiguruj `LoadOptions` z odpowiednim `RecoveryMode`.
2. Opakuj ładowanie w `try/catch`, aby wcześnie wykrywać uszkodzenia.
3. Użyj właściwości `PageCount` jako ostatecznego źródła liczby stron.
4. Wdroż eleganckie fallbacki (automatyczne odzyskiwanie, obsługa uprawnień, sprawdzanie istnienia pliku).

Od tego momentu możesz rozważyć:

- Wyodrębnianie tekstu z każdej strony (`doc.GetText()` z zakresem stron).
- Konwersję dokumentu do PDF po potwierdzeniu liczby stron.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}