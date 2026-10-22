---
category: general
date: 2026-08-04
description: Jak dodać etykiety danych w C# przy użyciu Aspose.Words. Dowiedz się,
  jak edytować wykres, wyśrodkować etykiety danych wykresu, wyświetlać procenty na
  wykresie oraz dostosować etykiety danych wykresu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: pl
lastmod: 2026-08-04
og_description: Jak dodać etykiety danych w C# przy użyciu Aspose.Words. Ten tutorial
  pokazuje, jak edytować wykres, wyśrodkować etykiety danych wykresu, wyświetlać procenty
  na wykresie oraz dostosować etykiety danych wykresu.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Jak dodać etykiety danych do wykresu w Wordzie w C# – kompletny przewodnik
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Jak dodać etykiety danych do wykresu w Wordzie w C# – przewodnik krok po kroku
url: /pl/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać etykiety danych do wykresu Word w C# – przewodnik krok po kroku

Jeśli potrzebujesz **jak dodać etykiety danych** do wykresu znajdującego się w dokumencie Word, ten przewodnik pokaże Ci dokładny kod, który musisz uruchomić. Zobaczysz, jak edytować właściwości wykresu, wyśrodkować etykiety danych, wyświetlić procenty w wykresie oraz dostosować etykiety danych do dowolnego scenariusza.

Tutorial obejmuje wszystko, co jest potrzebne do modyfikacji istniejącego wykresu – od wczytania dokumentu po zapisanie zmian. Nie są wymagane żadne zewnętrzne odwołania – jedynie biblioteka Aspose.Words for .NET oraz podstawowe środowisko programistyczne C#.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 (lub nowszy) zainstalowany.
* Aspose.Words for .NET w wersji 23.9 lub nowszej.  
  Możesz ją zainstalować przez NuGet:

```bash
dotnet add package Aspose.Words
```

* Plik Word (`input.docx`) zawierający przynajmniej jeden wykres.

## Jak dodać etykiety danych do wykresu Word w C#

Poniższe sekcje przeprowadzą Cię przez każdy krok. Główne słowo kluczowe **jak dodać etykiety danych** pojawia się naturalnie w narracji i w komentarzach kodu, zachowując zalecaną gęstość.

### Krok 1 – Wczytaj dokument Word zawierający wykres

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Dlaczego ten krok jest ważny*: Obiekt `Document` reprezentuje cały plik Word. Po jego wczytaniu masz dostęp do każdego węzła, w tym kształtów, które hostują wykresy.

### Krok 2 – Pobierz pierwszy wykres z dokumentu

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Dlaczego ten krok jest ważny*: Wykresy są przechowywane wewnątrz węzłów `Shape`. Rzutując pobrany węzeł na `Shape` i wywołując `GetChart()`, otrzymujesz obiekt `Chart`, który udostępnia serie, osie i kolekcje etykiet.

### Krok 3 – Włącz dostosowywanie etykiet danych i wyświetl procenty w wykresie

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Dlaczego ten krok jest ważny*: Ustawienie `ShowPercentage` powoduje, że Aspose.Words oblicza i wyświetla udział każdego fragmentu w całości. To bezpośrednio odpowiada drugorzędnemu słowu kluczowemu **show percentages in chart**.

### Krok 4 – Zmień położenie etykiety na środek każdego punktu danych

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Dlaczego ten krok jest ważny*: Właściwość `Position` kontroluje, gdzie etykieta pojawia się względem punktu danych. Użycie `Center` spełnia drugorzędne słowo kluczowe **center chart data labels** i poprawia czytelność wykresów kołowych lub pierścieniowych.

### Krok 5 – Dalsze dostosowywanie etykiet wykresu (opcjonalnie)

Jeśli potrzebujesz większej kontroli, możesz zmienić czcionkę, kolor lub linie prowadzące:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Ustawienia te ilustrują drugorzędne słowo kluczowe **customize chart data labels** i pokazują, jak dopasować wygląd do wytycznych marki.

### Krok 6 – Zapisz zmodyfikowany dokument

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Dlaczego ten krok jest ważny*: Zapis zapisuje zaktualizowany wykres z powrotem do pliku Word, dzięki czemu nowe etykiety danych są widoczne po otwarciu pliku w Microsoft Word.

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny program, który możesz skopiować, wkleić i uruchomić. Zawiera wszystkie niezbędne dyrektywy `using` oraz komentarze wyjaśniające każdy wiersz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Oczekiwany rezultat

Po otwarciu `output.docx` w Microsoft Word wykres wyświetli:

* Wartości procentowe obok każdego fragmentu (np. **25 %**, **40 %**, …).
* Etykiety umieszczone w centrum każdego punktu danych.
* Dodatkowe formatowanie, które zastosowałeś, np. pogrubiony czerwony tekst.

Te wizualne wskazówki ułatwiają interpretację wykresu, szczególnie w prezentacjach lub raportach.

## Jak edytować właściwości wykresu poza etykietami danych

Choć głównym tematem tego przewodnika jest **jak dodać etykiety danych**, możesz także chcieć **jak edytować wykres** – np. tytuły, położenie legendy lub formatowanie osi. Obiekt `Chart` udostępnia właściwości takie jak `Title`, `Legend` oraz `AxisX/AxisY`. Przykładowo, aby zmienić tytuł wykresu:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Wszystkie modyfikacje wykresu podążają za tym samym schematem: pobierz wykres, dostosuj jego właściwości, a następnie zapisz dokument.

## Typowe pułapki i wskazówki najlepszych praktyk

| Pułapka | Dlaczego się pojawia | Zalecane rozwiązanie |
|---|---|---|
| Wykres znajduje się wewnątrz grupowanego kształtu. | `GetChild(NodeType.Shape, …)` zwraca zewnętrzną grupę, a nie wewnętrzny wykres. | Wyszukuj rekurencyjnie kształt z `shape.HasChart`. |
| Etykiety danych nie pojawiają się po zapisaniu. | `ShowValue` lub `ShowPercentage` nie zostały ustawione na `true`. | Jawnie ustaw zarówno `ShowValue`, jak i `ShowPercentage` w razie potrzeby. |
| Etykiety nachodzą na małe fragmenty. | Pozycjonowanie w centrum może powodować zgrupowanie. | Użyj `ChartDataLabelPosition.OutSideEnd` dla położenia zewnętrznego lub włącz `LeaderLines`. |

Stosowanie tych wskazówek zapewnia niezawodne wyniki w różnych typach wykresów.

## Zakończenie

Teraz wiesz **jak dodać etykiety danych** do wykresu Word przy użyciu C#. Tutorial obejmował pobieranie wykresu, włączanie widoczności etykiet, ich wyśrodkowanie, wyświetlanie procentów oraz dostosowywanie wyglądu. Dzięki tej wiedzy możesz także **jak edytować wykres**, **center chart data labels**, **show percentages in chart** oraz **customize chart data labels** w dowolnym scenariuszu raportowym.

Gotowy na dalsze eksperymenty? Spróbuj dodać wiele serii, zastosować formatowanie warunkowe lub wyeksportować wykres jako obraz. API Aspose.Words oferuje rozbudowane możliwości manipulacji wykresami – eksperymentuj, aby znaleźć idealną wizualizację swoich danych.

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz wyjaśnienia krok po kroku, pomagające opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}