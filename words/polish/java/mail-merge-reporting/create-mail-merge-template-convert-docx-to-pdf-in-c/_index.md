---
category: general
date: 2026-05-23
description: Utwórz szablon korespondencji seryjnej i konwertuj pliki DOCX na PDF
  przy użyciu LowCode w C#. Przewodnik krok po kroku obejmujący konwersję, korespondencję
  seryjną i przetwarzanie wsadowe.
draft: false
keywords:
- create mail merge template
- convert docx to pdf
- docx to pdf conversion
- convert word to pdf
- batch docx to pdf
language: pl
og_description: Utwórz szablon korespondencji seryjnej i konwertuj DOCX na PDF przy
  użyciu LowCode. Poznaj pełny przepływ pracy, od projektowania szablonu po generowanie
  PDF w partiach.
og_title: Utwórz szablon korespondencji seryjnej i konwertuj DOCX na PDF w C#
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Create mail merge template and convert DOCX to PDF using LowCode in
    C#. Step‑by‑step guide covering conversion, mail‑merge, and batch processing.
  headline: Create Mail Merge Template & Convert DOCX to PDF in C#
  type: TechArticle
- description: Create mail merge template and convert DOCX to PDF using LowCode in
    C#. Step‑by‑step guide covering conversion, mail‑merge, and batch processing.
  name: Create Mail Merge Template & Convert DOCX to PDF in C#
  steps:
  - name: Why this matters
    text: '- **Performance:** The library streams the file, so even large Word documents
      won’t blow up memory. - **Accuracy:** LowCode respects Word’s layout engine,
      preserving headers, footers, and complex tables—something many open‑source converters
      miss. - **Error handling:** If the source file is missing o'
  - name: CSV format expectations
    text: '| FirstName | LastName | ProductName | PurchaseDate | OrderNumber | |-----------|----------|------------|--------------|-------------|
      | Alice | Smith | Widget Pro | 2024‑03‑15 | 12345 | | Bob | Jones | Gadget X
      | 2024‑03‑16 | 12346 |'
  - name: Edge‑case handling
    text: '- **Large CSV files:** If your data source exceeds a few thousand rows,
      consider streaming the CSV instead of loading it all at once (LowCode supports
      `IEnumerable<string[]>`). - **File‑name collisions:** The batch script overwrites
      existing PDFs; add a timestamp or GUID if you need uniqueness. - **'
  type: HowTo
tags:
- C#
- LowCode
- DOCX
- PDF
- Mail Merge
title: Utwórz szablon korespondencji seryjnej i konwertuj DOCX na PDF w C#
url: /pl/java/mail-merge-reporting/create-mail-merge-template-convert-docx-to-pdf-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz szablon korespondencji seryjnej i konwertuj DOCX do PDF w C#

Zastanawiałeś się kiedyś, jak **create mail merge template** bez spędzania godzin na kombinowanie z makrami Worda? Nie jesteś sam. W tym samouczku przeprowadzimy Cię przez tworzenie wielokrotnego użytku szablonu korespondencji seryjnej, konwertowanie pliku DOCX do PDF oraz przetwarzanie całego folderu dokumentów w jednym kroku — wszystko przy użyciu biblioteki LowCode w C#.

Dodamy również kroki **convert docx to pdf**, które są potrzebne do płynnego **docx to pdf conversion** pipeline. Po zakończeniu będziesz mieć gotową do uruchomienia aplikację konsolową, która może pobrać źródło danych CSV, scalić je z szablonem Worda i wygenerować dopracowane pliki PDF. Bez tajemnic, tylko przejrzysty kod i uzasadnienie.

## Czego będziesz potrzebować

- .NET 6.0 SDK lub nowszy (kod kompiluje się również z .NET Core)  
- Odwołanie do pakietu NuGet **LowCode** (`LowCode.Converter` i `LowCode.MailMerger`)  
- Podstawowa znajomość aplikacji konsolowych C#  
- Dwa foldery: jeden dla plików źródłowych (`YOUR_DIRECTORY`) i drugi dla wyników  

To wszystko. Jeśli masz to wszystko, możemy od razu przejść do sedna rozwiązania.

![Create mail merge template workflow diagram](image-placeholder.png){alt="Diagram przepływu tworzenia szablonu korespondencji seryjnej"}

## Krok 1: Skonfiguruj projekt i zainstaluj LowCode

Najpierw utwórz nowy projekt konsolowy:

```bash
dotnet new console -n MailMergeDemo
cd MailMergeDemo
dotnet add package LowCode.Converter
dotnet add package LowCode.MailMerger
```

Dlaczego instalować oba pakiety? `LowCode.Converter` obsługuje operację **convert word to pdf**, natomiast `LowCode.MailMerger` zarządza logiką scalania. Trzymanie ich osobno pozwala ponownie używać konwertera w innych częściach aplikacji, bez wciągania niepotrzebnego kodu mail‑merge.

> **Wskazówka:** Jeśli celujesz w .NET Framework zamiast .NET Core, po prostu zmień polecenia `dotnet` na odpowiednie wywołania `nuget`.

## Krok 2: Konwertuj DOCX do PDF – Podstawowy element konwersji docx do pdf

Zanim pomyślimy o scalaniu danych, upewnijmy się, że możemy **convert docx to pdf** niezawodnie. API LowCode to jednowierszowy kod:

```csharp
using LowCode.Converter;

// Paths – adjust to your environment
string sourceDoc = @"YOUR_DIRECTORY\input.docx";
string pdfResult = @"YOUR_DIRECTORY\output.pdf";

// Perform the conversion
Converter.convert(sourceDoc, pdfResult);
Console.WriteLine($"✅ PDF created at {pdfResult}");
```

### Dlaczego to ma znaczenie

- **Performance:** Biblioteka strumieniuje plik, więc nawet duże dokumenty Word nie wyczerpią pamięci.  
- **Accuracy:** LowCode respektuje silnik układu Worda, zachowując nagłówki, stopki i złożone tabele — coś, czego brakuje wielu konwerterom open‑source.  
- **Error handling:** Jeśli plik źródłowy jest brakujący lub uszkodzony, `convert` rzuca opisowy `ConversionException`. Możesz go przechwycić, aby zalogować lub ponowić próbę.

```csharp
try
{
    Converter.convert(sourceDoc, pdfResult);
}
catch (ConversionException ex)
{
    Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
}
```

## Krok 3: Utwórz szablon korespondencji seryjnej (krok „create mail merge template”)

Szablon mail‑merge to po prostu zwykły plik `.docx` z polami zastępczymi, które LowCode podmieni. Otwórz Word i wstaw **Content Controls** (lub proste pola scalania takie jak `{{FirstName}}`). Zapisz plik jako `Template.docx`.

Oto mały przykład tego, co może zawierać szablon:

```
Dear {{FirstName}} {{LastName}},

Thank you for purchasing {{ProductName}} on {{PurchaseDate}}.
Your order number is {{OrderNumber}}.

Best regards,
Acme Corp.
```

Dlaczego używać podwójnych nawiasów klamrowych? `MailMerger` LowCode domyślnie szuka tego wzorca, co sprawia, że szablon jest niezależny od języka. Można również użyć wbudowanej składni Worda «MERGEFIELD», ale nawiasy utrzymują porządek i unikają specyficznych dla Worda problemów.

## Krok 4: Wykonaj scalanie korespondencji seryjnej

Teraz łączymy źródło danych (plik CSV) z szablonem i generujemy scalony `.docx`. API LowCode ponownie umożliwia to jednym wywołaniem:

```csharp
using LowCode.MailMerger;

// Define file locations
string templateFile = @"YOUR_DIRECTORY\Template.docx";
string dataFile = @"YOUR_DIRECTORY\Data.csv";          // Must have a header row matching placeholders
string mergedResult = @"YOUR_DIRECTORY\MergedResult.docx";

// Execute the merge
MailMerger.merge(templateFile, dataFile, mergedResult);
Console.WriteLine($"✅ Merged document created at {mergedResult}");
```

### Oczekiwania co do formatu CSV

| FirstName | LastName | ProductName | PurchaseDate | OrderNumber |
|-----------|----------|------------|--------------|-------------|
| Alice     | Smith    | Widget Pro | 2024‑03‑15   | 12345       |
| Bob       | Jones    | Gadget X   | 2024‑03‑16   | 12346       |

- **Header row** musi dokładnie odpowiadać nazwom pól (bez rozróżniania wielkości liter).  
- **UTF‑8** jest przyjmowane jako kodowanie; jeśli potrzebujesz innej strony kodowej, przekaż obiekt `CsvOptions` (nie pokazano tutaj dla zwięzłości).

## Krok 5: Konwertuj scalony DOCX do PDF

Gdy masz `MergedResult.docx`, prawdopodobnie będziesz chciał PDF do wysłania klientom. Ponownie użyj konwertera z Kroku 2:

```csharp
string mergedPdf = @"YOUR_DIRECTORY\MergedResult.pdf";
try
{
    Converter.convert(mergedResult, mergedPdf);
    Console.WriteLine($"✅ Final PDF ready at {mergedPdf}");
}
catch (ConversionException ex)
{
    Console.Error.WriteLine($"❌ PDF conversion failed: {ex.Message}");
}
```

To pełny cykl **convert docx to pdf**: szablon → scalanie → PDF.

## Krok 6: Batch DOCX to PDF (opcjonalnie, ale przydatne)

Jeśli masz dziesiątki lub setki scalonych dokumentów, ręczne iterowanie po nich jest uciążliwe. Oto szybki pomocnik **batch docx to pdf**, który pobiera każdy `.docx` w folderze i tworzy odpowiadający `.pdf`:

```csharp
using System.IO;

// Folder containing merged DOCX files
string mergedFolder = @"YOUR_DIRECTORY\Merged";
string pdfFolder = @"YOUR_DIRECTORY\PDFs";

Directory.CreateDirectory(pdfFolder);

foreach (var docxPath in Directory.GetFiles(mergedFolder, "*.docx"))
{
    string fileName = Path.GetFileNameWithoutExtension(docxPath);
    string pdfPath = Path.Combine(pdfFolder, $"{fileName}.pdf");

    try
    {
        Converter.convert(docxPath, pdfPath);
        Console.WriteLine($"✅ {fileName}.pdf created");
    }
    catch (ConversionException ex)
    {
        Console.Error.WriteLine($"❌ Failed on {fileName}: {ex.Message}");
    }
}
```

### Obsługa przypadków brzegowych

- **Large CSV files:** Jeśli źródło danych przekracza kilka tysięcy wierszy, rozważ strumieniowanie CSV zamiast ładowania wszystkiego naraz (LowCode obsługuje `IEnumerable<string[]>`).  
- **File‑name collisions:** Skrypt batch nadpisuje istniejące pliki PDF; dodaj znacznik czasu lub GUID, jeśli potrzebna jest unikalność.  
- **Permissions:** Upewnij się, że proces ma uprawnienia do zapisu w folderze wyjściowym, szczególnie przy uruchamianiu pod IIS lub jako usługa Windows.

## Pełny działający przykład

Łącząc wszystko razem, oto minimalny `Program.cs`, który demonstruje cały przepływ od tworzenia szablonu po generowanie PDF w trybie wsadowym:



## Powiązane samouczki

- [Utwórz dostępny PDF z Worda w C# – Przewodnik krok po kroku](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-with-c-step-by-step-guide/)
- [convert word to pdf w C# przy użyciu Aspose.Words – Poradnik](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)
- [Utwórz dostępny PDF – Przewodnik krok po kroku dla zgodności PDF/UA](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-step-by-step-guide-for-pdf-ua-complian/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}