---
category: general
date: 2026-10-07
description: Dowiedz się, jak utworzyć dokument Word i wstawić wykres kołowy przy
  użyciu Aspose.Words w C#. Poradnik pokazuje również, jak wygenerować plik Word z
  niestandardowymi etykietami wykresu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: pl
lastmod: 2026-10-07
og_description: Utwórz dokument Word i wstaw wykres kołowy w C#. Skorzystaj z tego
  przewodnika krok po kroku, aby wygenerować plik Word z w pełni dostosowanymi etykietami
  wykresu.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Utwórz dokument Word z niestandardowym wykresem kołowym w C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Jak utworzyć dokument Word z dostosowanym wykresem kołowym w C#
url: /pl/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć dokument Word z dostosowanym wykresem kołowym w C#

Jeśli potrzebujesz **utworzyć dokument Word** programowo, ten samouczek pokaże Ci, jak **wstawić wykres kołowy** i dostosować jego etykiety danych przy użyciu Aspose.Words for .NET. Dowiesz się również, jak **generować plik Word**, który zawiera w pełni stylizowany wykres, obejmując wszystko od konfiguracji projektu po zapisanie końcowego dokumentu.

Poradnik przechodzi przez każdy krok potrzebny do dodania wykresu, regulacji pozycji etykiet, włączenia linii prowadzących oraz ostatecznego zapisania wyniku jako pliku `.docx`. Nie są wymagane żadne zewnętrzne narzędzia poza biblioteką Aspose.Words, a pełny kod źródłowy jest udostępniony, abyś mógł go skopiować, wkleić i uruchomić od razu.

## Prerequisites

Zanim rozpoczniesz, upewnij się, że masz:

* .NET 6.0 SDK lub nowszy zainstalowany  
* Ważną licencję Aspose.Words for .NET (lub darmowy klucz ewaluacyjny)  
* IDE, takie jak Visual Studio 2022 lub Visual Studio Code  

Będziesz także musiał dodać następujące pakiety NuGet do swojego projektu:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Te pakiety udostępniają klasy `Document`, `DocumentBuilder` oraz klasy związane z wykresami używane w poniższych przykładach.

## Create word document and add a chart

Pierwszym krokiem jest **utworzyć dokument Word** i uzyskać `DocumentBuilder`, który pozwala wstawiać treść. Builder działa jak kursor umieszczony wewnątrz dokumentu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Obiekt `Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` zapewnia metody takie jak `InsertChart`, które umieszczają obiekty bezpośrednio w przepływie dokumentu.

## Insert pie chart into the document

Teraz, gdy builder jest gotowy, możesz **wstawić wykres kołowy** o określonym rozmiarze. Wykres jest dodawany w bieżącej pozycji buildera.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` zwraca obiekt `Chart`, który możesz dalej modyfikować. Przykładowe dane tworzą cztery segmenty reprezentujące kwartalne przychody.

## Customize pie chart data labels

Aby wykres był bardziej czytelny, często trzeba **dostosować etykiety wykresu kołowego** — umieścić je poza segmentami i pokazać linie prowadzące. W tym miejscu przydaje się `ChartDataLabelCollection`.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Ustawienie `Position` na `OutsideEnd` przesuwa każdą etykietę poza krawędź segmentu, a `ShowLeaderLines` rysuje linię łączącą etykietę z jej segmentem. Opcjonalne flagi `ShowValue` i `ShowPercentage` dostarczają czytelnikom zarówno surowe liczby, jak i względne procenty.

**Pro tip:** Jeśli potrzebujesz sformatować czcionkę etykiety, użyj `dataLabels.Font`, aby ustawić rozmiar, kolor i styl. Dzięki temu wykres będzie zgodny z identyfikacją wizualną Twojej firmy.

## Save and generate word file

Po pełnym skonfigurowaniu wykresu możesz **generować plik Word**, zapisując instancję `Document` na dysku. Wybierz format `.docx` dla maksymalnej kompatybilności z nowoczesnymi wersjami Worda.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kiedy otworzysz `CustomPieChart.docx`, zobaczysz wykres kołowy z czterema segmentami, każdy oznaczony etykietą poza segmentem, połączoną linią prowadzącą i wyświetlającą zarówno wartość, jak i procent.

![Zrzut ekranu dokumentu Word zawierającego dostosowany wykres kołowy utworzony w C#](image-placeholder.png)

*Obraz przedstawia ostateczny wynik tutorialu **create word document**.*

## Common variations and edge cases

| Scenario | How to adapt the code |
|----------|----------------------|
| **Multiple series** | Dodaj dodatkowe obiekty `ChartSeries` do `pieChart.Series`. Każda seria może mieć własną kolekcję `DataLabels` dla niezależnego stylu. |
| **Different chart size** | Zmień parametry szerokości i wysokości w `InsertChart(width, height)`. Wartości podawane są w punktach (1 pt ≈ 1/72 in). |
| **Chart title** | Użyj `pieChart.Title.Text = "Quarterly Sales"` aby dodać opisowy tytuł. |
| **Export to PDF** | Wywołaj `document.Save("Report.pdf", SaveFormat.Pdf);` po zbudowaniu wykresu. |
| **License handling** | Umieść plik licencji (`Aspose.Words.lic`) w folderze aplikacji i załaduj go przy pomocy `new License().SetLicense("Aspose.Words.lic");` przed utworzeniem dokumentu. |

Te warianty pozwalają odpowiedzieć na pytanie **how to add pie chart** w wielu rzeczywistych scenariuszach, od prostych raportów po złożone pulpity nawigacyjne.

## Conclusion

Teraz wiesz, jak **utworzyć dokument Word**, **wstawić wykres kołowy** i **dostosować etykiety wykresu kołowego** przy użyciu Aspose.Words for .NET. Pełny przykład demonstruje czysty przepływ pracy: inicjalizacja dokumentu, dodanie wykresu, regulacja położenia etykiet danych, włączenie linii prowadzących oraz ostateczne **generowanie pliku Word**, który można udostępnić każdemu.

Spróbuj rozszerzyć ten samouczek, eksperymentując z innymi typami wykresów (`ChartType.Column`, `ChartType.Line`) lub stosując własne palety kolorów, aby dopasować je do marki. Jeśli napotkasz problemy, zajrzyj do dokumentacji Aspose.Words lub zbadaj powiązane tematy, takie jak „how to add pie chart” z wieloma seriami i dynamicznymi źródłami danych.

Miłego kodowania i zachęcamy do dzielenia się wynikami lub zadawania pytań w komentarzach!

## What Should You Learn Next?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}