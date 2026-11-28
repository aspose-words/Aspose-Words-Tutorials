---
category: general
date: 2026-10-10
description: Przetłumacz akapit na francuski i dowiedz się, jak zmienić etykietę danych
  wykresu, dostosować etykietę danych wykresu oraz zapisać edytowany plik docx przy
  użyciu Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: pl
lastmod: 2026-10-10
og_description: Przetłumacz akapit na francuski i dowiedz się, jak zmienić etykietę
  danych wykresu, dostosować etykietę danych wykresu oraz zapisać edytowany plik docx
  przy użyciu Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Przetłumacz akapit na francuski i zmień etykietę wykresu w Wordzie
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Przetłumacz akapit na francuski i zmień etykietę wykresu w Wordzie
url: /pl/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Przetłumacz akapit na francuski i zmień etykietę wykresu w Word

Jeśli potrzebujesz **przetłumaczyć akapit na francuski** i jednocześnie zaktualizować wykres w tym samym dokumencie Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Korzystając z Aspose.Words AI możesz automatycznie tłumaczyć tekst, następnie zmodyfikować etykietę danych wykresu i w końcu zapisać edytowany plik `.docx` — wszystko w kilku prostych krokach.

Poradnik obejmuje wszystko, od wczytania pliku źródłowego po zapisanie wprowadzonych zmian. Po jego zakończeniu będziesz w stanie przetłumaczyć dowolny akapit, dostosować etykietę danych wykresu i wyprodukować nowy plik Word gotowy do dystrybucji. Nie są wymagane żadne zewnętrzne skrypty; cały przepływ pracy mieści się w jednym programie C#.

## Wymagania wstępne

- .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.7+)
- Licencja Aspose.Words for .NET (lub darmowy klucz ewaluacyjny)
- Dostęp do Internetu dla tłumacza Google AI (klasa `Translator` korzysta z API Google)
- Dokument Word (`input.docx`) zawierający przynajmniej jeden akapit i jeden wykres

## Krok 1: Utwórz projekt i zaimportuj przestrzenie nazw

Utwórz nową aplikację konsolową i dodaj pakiet NuGet Aspose.Words:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Teraz dołącz wymagane przestrzenie nazw na początku pliku `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Te importy dają dostęp do ładowania dokumentu, tłumaczenia AI oraz funkcji edycji wykresów.

## Krok 2: Wczytaj źródłowy dokument Word

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Wczytanie pliku tworzy reprezentację w pamięci, którą możesz przeszukiwać i modyfikować bez ingerencji w oryginalny plik na dysku.

## Krok 3: Przetłumacz pierwszy akapit na francuski

Pierwszy akapit jest często tytułem lub zdaniem wprowadzającym, więc jest dobrym kandydatem do tłumaczenia. Klasa `Translator` abstrahuje wywołanie modelu AI Google.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Dlaczego to działa:**  
`paragraph.Runs.Clear()` usuwa wszystkie istniejące fragmenty tekstu, zapewniając, że nowe tłumaczenie nie zostanie połączone ze starym tekstem. `new Run(document, translatedText)` tworzy nowy fragment, który dziedziczy formatowanie akapitu.

## Krok 4: Znajdź pierwszy wykres i dostosuj jego etykietę danych

Wykresy są przechowywane jako węzły `Shape` typu `NodeType.Shape`. Pierwszy wykres można pobrać przy pomocy `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Wyjaśnienie kluczowych kroków:**

- `GetChild(NodeType.Shape, 0, true)` wykonuje przeszukiwanie w głąb i zwraca pierwszy kształt, którym w naszym przypadku jest wykres.
- `ChartSeries` reprezentuje kolekcję punktów danych; pierwsza seria (`Series[0]`) zazwyczaj odpowiada głównemu zestawowi danych.
- `ChartDataLabelPosition.OutsideEnd` przenosi etykietę poza koniec słupka, poprawiając czytelność.
- Ustawienie `dataLabel.Text` na francuski ciąg znaków synchronizuje etykietę z przetłumaczonym akapitem.

## Krok 5: Zapisz dokument z przetłumaczonym akapitem

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

W tym momencie dokument zawiera francuski akapit, ale wciąż posiada oryginalną konfigurację wykresu.

## Krok 6: Zapisz dokument z zaktualizowanym wykresem

Możesz ponownie użyć tej samej instancji `Document` — nie ma potrzeby ponownego wczytywania, ponieważ modyfikacje wykresu już znajdują się w pamięci.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Oba pliki są teraz gotowe do dystrybucji:

- **`translated.docx`** – zawiera francuski akapit.
- **`chart-updated.docx`** – zawiera francuski akapit *oraz* dostosowaną etykietę wykresu.

## Kompletny, gotowy do uruchomienia przykład

Poniżej znajduje się pełny program, który możesz skopiować i wkleić do `Program.cs`. Kompiluje się i działa od razu, pod warunkiem że zamienisz `YOUR_DIRECTORY` na rzeczywistą ścieżkę folderu.



## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Dostosuj etykietę danych wykresu](/words/english/net/programming-with-charts/chart-data-label/)
- [Formatuj liczbę etykiet danych na wykresie](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Etykieta danych wykresu](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}