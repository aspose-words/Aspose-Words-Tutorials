---
category: general
date: 2026-08-10
description: Utwórz dokument Word z wykresem kołowym przy użyciu Aspose.Words. Dowiedz
  się, jak wstawić wykres, dostosować kolory wykresu kołowego oraz zmienić kolor kawałka
  koła w C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: pl
lastmod: 2026-08-10
og_description: Utwórz dokument Word z wykresem kołowym przy użyciu Aspose.Words.
  Ten przewodnik wyjaśnia, jak wstawić wykres, dostosować kolory wykresu kołowego
  oraz zmienić kolor kawałka koła w aplikacji C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Tworzenie wykresu kołowego w dokumencie Word – przewodnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Utwórz dokument Word z wykresem kołowym przy użyciu Aspose.Words
url: /pl/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz dokument Word z wykresem kołowym przy użyciu Aspose.Words

Jeśli potrzebujesz **utworzyć dokument Word z wykresem kołowym** programowo, ten samouczek pokaże Ci dokładnie, jak to zrobić. Przejdziemy przez wstawianie wykresu, **dostosowywanie kolorów wykresu kołowego**, oraz **zmianę koloru fragmentu koła** przy użyciu Aspose.Words dla .NET.

Zobaczysz kompletny, gotowy do uruchomienia przykład, który możesz skopiować do Visual Studio, uruchomić i od razu otworzyć wygenerowany *.docx*, aby zweryfikować stylizowany wykres kołowy. Nie jest wymagana żadna zewnętrzna dokumentacja — wszystko, czego potrzebujesz, znajduje się w tym przewodniku.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz:

* .NET 6.0 SDK lub nowszy zainstalowany  
* Ważną licencję Aspose.Words dla .NET (lub tymczasowy klucz ewaluacyjny)  
* Visual Studio 2022 (lub dowolne IDE C#)  

Kod używa wyłącznie przestrzeni nazw `Aspose.Words` i `Aspose.Words.Drawing.Charts`, więc nie są potrzebne dodatkowe pakiety NuGet poza biblioteką Aspose.Words.

## Utwórz dokument Word z wykresem kołowym – pełny przykład

Poniższy program w C# tworzy nowy dokument Word, wstawia wykres kołowy, stylizuje pierwsze dwa fragmenty i zapisuje plik. Każdy krok jest szczegółowo wyjaśniony.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Wyjaśnienie każdego kroku

| Krok | Co robi | Dlaczego ma znaczenie |
|------|---------|-----------------------|
| **1** | Tworzy nowy `Document` i `DocumentBuilder`. | `DocumentBuilder` zapewnia płynne metody wstawiania treści, takich jak wykresy, do pliku Word. |
| **2** | Wywołuje `InsertChart` z `ChartType.Pie` i stałym rozmiarem. | `InsertChart` jest **metodą wstawiania wykresu**; określenie szerokości/wysokości zapewnia, że wykres ładnie mieści się na stronie. |
| **3** | Dodaje serię danych z trzema kategoriami i wartościami liczbowymi. | Wykres kołowy bez danych jest niewidoczny; jego wypełnienie demonstruje kroki stylizacji. |
| **4** | Ustawia `Explosion` na pierwszym punkcie. | „Wybuch” fragmentu przyciąga uwagę do konkretnego segmentu — przydatne przy podkreślaniu kluczowych danych. |
| **5** | Ustawia `ForeColor` dla pierwszych dwóch punktów. | To jest sedno **dostosowywania kolorów wykresu kołowego**; możesz użyć dowolnego `System.Drawing.Color`. |
| **6** | Pokazuje, jak **zmienić kolor fragmentu koła** dla dodatkowych fragmentów. | Demonstracja, że stylizacja nie ogranicza się do pierwszych dwóch fragmentów; możesz pokolorować każdy fragment indywidualnie. |
| **7** | Zapisuje dokument jako `PieChartStyled.docx`. | Końcowy wynik może być otwarty w Microsoft Word, Google Docs lub dowolnym kompatybilnym podglądzie. |

#### Oczekiwany wynik

Otwarcie `PieChartStyled.docx` wyświetla jedną stronę z wykresem kołowym o wymiarach 400 × 300 pt:

* Fragment 1 (pomarańczowy) jest wybuchnięty na zewnątrz.  
* Fragment 2 (zielony) znajduje się obok wybuchniętego fragmentu.  
* Fragment 3 (stalowo‑niebieski) wypełnia pozostały segment.

Wykres odzwierciedla wartości danych (30, 45, 25) oraz niestandardowe kolory, które zdefiniowałeś.

## Jak stylizować koło – dodatkowe wskazówki

* **Użyj kolorów motywu** – zamiast twardo kodować `Color.Orange`, możesz pobrać kolory z motywu dokumentu:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Dodaj etykiety danych** – jeśli chcesz, aby na wykresie wyświetlane były procenty:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Dynamicznie zmieniaj rozmiar** – oblicz rozmiar wykresu na podstawie marginesów strony:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Te warianty pokazują elastyczność **stylizacji koła** poza podstawowym przykładem.

## Najczęściej zadawane pytania

**P: Czy to działa z .NET Core?**  
O: Tak. Aspose.Words dla .NET jest kompatybilny z .NET Core, .NET 5, .NET 6 i nowszymi. Wystarczy odwołać się do tego samego pakietu NuGet.

**P: Co zrobić, jeśli potrzebuję wykresu pierścieniowego zamiast kołowego?**  
O: Zamień `ChartType.Pie` na `ChartType.Doughnut`. Te same API stylizacji (`Explosion`, `ForeColor`) mają zastosowanie.

**P: Czy mogę wstawić wykres do istniejącego dokumentu?**  
O: Otwórz istniejący plik za pomocą `new Document("Existing.docx")`, utwórz `DocumentBuilder` dla tego dokumentu i wywołaj `InsertChart` w żądanej pozycji kursora.

**P: Jak radzić sobie z dużymi zestawami danych?**  
O: Wykresy kołowe najlepiej sprawdzają się przy ograniczonej liczbie kategorii (zwykle < 10). Przy wielu kategoriach rozważ wykres słupkowy lub kolumnowy.

## Pełny kod źródłowy – podsumowanie

Poniżej znajduje się kompletny program w jednym bloku, gotowy do skopiowania i wklejenia:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Uruchomienie tego kodu generuje opisany wcześniej stylizowany wykres kołowy w dokumencie Word.

## Zakończenie

Teraz wiesz, jak **utworzyć dokument Word z wykresem kołowym** przy użyciu Aspose.Words, **dostosować kolory wykresu kołowego** oraz **zmienić kolor fragmentu koła** programowo. Przewodnik obejmował wstawianie wykresu, wypełnianie danymi, „wybuch” fragmentu, stosowanie niestandardowych kolorów i zapisywanie wyniku.  

Od tego momentu możesz zgłębiać tematy pokrewne, takie jak **wstawianie innych typów wykresów**, dodawanie legend lub generowanie raportów wielostronicowych z wieloma wykresami. Eksperymentuj z różnymi schematami kolorów i zestawami danych, aby dopasować je do swoich potrzeb raportowych.

Miłego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz szczegółowe wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Wstaw wykres kolumnowy w Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Wstaw wykres obszarowy w dokumencie Word \| Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Utwórz wykres punktowy w Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}