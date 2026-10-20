---
category: general
date: 2026-07-29
description: Jak edytować wykres w dokumencie Word — dowiedz się, jak zmienić położenie
  etykiet wykresu, dostosować etykiety wykresu słupkowego, modyfikować etykiety danych
  wykresu oraz zmienić czcionkę etykiet wykresu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: pl
lastmod: 2026-07-29
og_description: Jak szybko edytować wykres w Wordzie. Opanuj zmianę położenia etykiet
  wykresu, dostosowywanie etykiet wykresu słupkowego, modyfikowanie etykiet danych
  wykresu oraz zmianę czcionki etykiet wykresu.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Jak edytować wykres w Wordzie – zmień etykiety i czcionkę
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Jak edytować wykres w Wordzie: zmień położenie etykiet, czcionkę i więcej'
url: /pl/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak edytować wykres w Wordzie: zmień pozycję etykiety, czcionkę i więcej

Edycja wykresu w dokumencie Word jest powszechną potrzebą, gdy chcesz, aby Twoje raporty wyglądały profesjonalnie. Czy kiedykolwiek miałeś problem z **change chart label position** lub z czytelnością etykiet, nie przeszukując nieskończonych menu? Nie jesteś sam — większość programistów napotyka ten problem przy automatyzacji generowania raportów. W tym przewodniku przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który dokładnie pokazuje, jak **adjust bar chart labels**, **modify chart data labels** i **change chart label font** przy użyciu C# i biblioteki Aspose.Words.

## Czego się nauczysz

- Załaduj plik .docx, który już zawiera wykres słupkowy.  
- Pobierz pierwszy kształt wykresu i uzyskaj dostęp do jego kolekcji etykiet danych.  
- **Change chart label position**, aby słupki wyglądały schludniej.  
- **Adjust bar chart labels** rozmiar czcionki dla lepszej czytelności.  
- Zapisz zmodyfikowany dokument z powrotem na dysk.  

Bez zewnętrznych narzędzi, bez ręcznych kroków w interfejsie — tylko czysty kod, który możesz wkleić do dowolnego projektu .NET. Po zakończeniu będziesz mieć samodzielne rozwiązanie, które możesz ponownie wykorzystać w dziesiątkach dokumentów.

> **Wymagania wstępne**  
> - .NET 6.0 lub nowszy (kod działa również na .NET Framework 4.7+).  
> - Aspose.Words for .NET (dostępny przez NuGet).  
> - Plik Word (`BarChart.docx`) zawierający już wykres słupkowy.  

Jeśli brakuje Ci któregoś z nich, pobierz najnowszy pakiet Aspose.Words już teraz:

```bash
dotnet add package Aspose.Words
```

## Jak edytować wykres: pobranie wykresu z dokumentu Word

Pierwszym krokiem w **how to edit chart** jest załadowanie dokumentu i zlokalizowanie kształtu wykresu. Aspose.Words traktuje wykresy jako węzły `Shape`, więc możemy użyć `GetChild` z `NodeType.Shape`, aby pobrać pierwszy napotkany wykres.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Dlaczego to ważne:**  
> Bezpośredni dostęp do obiektu `Chart` pozwala uniknąć kosztów otwierania pliku w Wordzie i ręcznego dostosowywania każdej etykiety. To podstawa każdej automatyzacji **modify chart data labels**.

## Dostosowanie etykiet wykresu słupkowego: zmiana pozycji etykiety wykresu

Teraz, gdy mamy instancję `Chart`, przeiterujmy jej `DataLabelCollection`. Celem jest **change chart label position**, aby każda etykieta znajdowała się ładnie wewnątrz podstawy swojego słupka, zamiast nieporadnie unosić się nad nim.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Wskazówka:**  
> `InsideBase` dobrze działa dla pionowych wykresów słupkowych. Jeśli masz do czynienia z poziomym wykresem słupkowym, wypróbuj `InsideEnd`. Eksperymentowanie z pozycjami jest tanie — po prostu uruchom kod ponownie i otwórz zapisany dokument.

## Zmiana czcionki etykiety wykresu: dostosowanie rozmiaru czcionki dla czytelności

Mała czcionka to cichy zabójca przejrzystości raportu. Aby **change chart label font**, po prostu ustaw właściwość `Font.Size` dla każdej `ChartDataLabel`. Podniesiemy ją do 9 pt, co jest optymalnym rozmiarem dla większości drukowanych raportów.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Dlaczego to robimy:**  
> Dostosowanie rozmiaru czcionki jest częścią najlepszych praktyk **modify chart data labels**. Większe czcionki poprawiają dostępność i zmniejszają potrzebę ręcznego przetwarzania po zakończeniu.

## Zapisz zaktualizowany dokument

Po dostosowaniu pozycji i czcionek, ostatnim krokiem w **how to edit chart** jest zachowanie zmian. Aspose.Words umożliwia to w jednej linii kodu.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Otwórz `BarChartCustomLabels.docx` w Wordzie i zobaczysz etykiety ściśle wewnątrz słupków, wyświetlane czcionką 9 pt. Koniec z mrużeniem oczu na małe liczby.

## Pełny działający przykład (wszystkie kroki w jednym pliku)

Poniżej znajduje się kompletny, gotowy do uruchomienia program konsolowy, który demonstruje cały przepływ — od załadowania dokumentu po zapisanie zaktualizowanej wersji. Skopiuj i wklej go do nowego projektu konsolowego .NET i naciśnij **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Oczekiwany wynik** po uruchomieniu programu:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Otwórz wygenerowany plik i zobaczysz **adjust bar chart labels** umieszczone wewnątrz słupków z wygodnym rozmiarem czcionki.

## Częste pytania i przypadki brzegowe

### Co zrobić, jeśli dokument zawiera wiele wykresów?

Powyższy kod pobiera *pierwszy* wykres (`GetChild(NodeType.Shape, 0, true)`). Aby edytować wszystkie wykresy, zamień pojedyncze pobranie na pętlę:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Jak **change chart label font** tylko dla konkretnej serii?

Każdy `ChartSeries` ma własną `DataLabelCollection`. Wskaż serię za pomocą indeksu:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Czy to działa z wykresami kołowymi lub liniowymi?

Tak — `ChartDataLabelPosition` obsługuje wartości takie jak `InsideEnd`, `OutsideEnd` i `BestFit`. Dla wykresu kołowego możesz preferować `OutsideEnd`, aby etykiety były czytelne.

### Co z lokalizacją (np. różne separatory dziesiętne)?

Aspose.Words respektuje ustawienia regionalne dokumentu. Jeśli musisz wymusić konkretny format, dostosuj `label.NumberFormat` przed zapisem.

## Podsumowanie i kolejne kroki

Omówiliśmy **how to edit chart** w dokumencie Word od początku do końca: ładowanie pliku, pobieranie wykresu, **changing chart label position**, **adjusting bar chart labels**, **modifying chart data labels** oraz w końcu **changing chart label font** przed zapisem. Pełny przykład jest gotowy do produkcji i może być wstawiony do dowolnego potoku automatyzacji.

Gotowy, aby podnieść poziom? Rozważ następujące pomysły:

- **Dodaj kolory etykiet danych** (`dataLabel.Font.Color = Color.Blue;`).  
- **Wyświetlaj wartości jako procenty** (`dataLabel.NumberFormat = "0%";`).  
- **Twórz wykresy programowo** zamiast ładować istniejące.

Wszystko to opiera się na tym samym interfejsie API, którego używaliśmy dzisiaj, więc poczujesz się jak w domu.

Jeśli napotkasz jakiekolwiek problemy, zostaw komentarz poniżej lub sprawdź dokumentację Aspose.Words w celu głębszych opcji dostosowywania wykresów. Szczęśliwego kodowania i ciesz się pięknie oznaczonymi wykresami!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Dostosuj etykietę danych wykresu](/words/english/net/programming-with-charts/chart-data-label/)
- [Formatuj liczbę etykiet danych w wykresie](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Etykieta danych wykresu](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}