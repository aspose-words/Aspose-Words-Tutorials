---
category: general
date: 2026-09-21
description: Utwórz pusty dokument Word i dowiedz się, jak wstawić wykres radarowy
  w pliku Word przy użyciu DocumentBuilder – przewodnik krok po kroku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: pl
lastmod: 2026-09-21
og_description: Utwórz pusty dokument Word i wstaw wykres radarowy w pliku Word przy
  użyciu Aspose.Words. Skorzystaj z tego samouczka, aby szybko wygenerować wykres
  w dokumencie Word.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Utwórz pusty dokument Word i dodaj wykres radarowy – kompletny przewodnik
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Jak utworzyć pusty dokument Word i dodać wykres radarowy w C#
url: /pl/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć pusty dokument Word i dodać wykres radarowy w C#

Jeśli potrzebujesz **utworzyć pusty dokument Word** i osadzić wykres radarowy (radialny), ten tutorial dostarcza gotowe rozwiązanie do uruchomienia. Zobaczysz, jak używać Aspose.Words .NET do generowania pliku, wstawiania wykresu i zapisywania wyniku — w kilku zwięzłych krokach.

Pusty dokument zapewnia czyste płótno dla każdego scenariusza automatycznego raportowania, a dodanie wykresu radarowego pozwala wizualizować dane wielowymiarowe bezpośrednio w Wordzie. Po zakończeniu tego przewodnika będziesz w stanie wygenerować wykres w dokumencie Word bez ręcznej edycji.

## Czego się nauczysz

* Jak **utworzyć pusty dokument Word** programowo w C#.
* Dokładny kod, **jak wstawić wykres radarowy** przy użyciu `DocumentBuilder`.
* Sposoby **wstawienia wykresu do pliku Word** i dostosowania jego rozmiaru.
* Jak **generować wykres w dokumencie Word** i zweryfikować wynik.
* Wskazówki dotyczące **dodawania wykresu radialnego do plików Word**, w tym typowe pułapki.

### Wymagania wstępne

* .NET 6.0 lub nowszy (kod działa również z .NET Framework 4.6+).
* Aspose.Words for .NET (pakiet NuGet `Aspose.Words` w wersji 23.9 lub nowszej).
* Podstawowa znajomość C# oraz Visual Studio lub wybranego IDE.

## Utwórz pusty dokument Word w C#

Pierwszym krokiem jest utworzenie pustego obiektu `Document`. Obiekt ten reprezentuje całkowicie pusty plik `.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` tworzy strukturę pliku, ale nie zawiera jeszcze żadnych sekcji ani stron. Aspose.Words automatycznie dodaje domyślną sekcję, gdy zaczynasz dodawać zawartość, dlatego kolejny krok działa bez dodatkowej konfiguracji.

## Jak wstawić wykres radarowy do pliku Word

Wykres radarowy (zwany także wykresem radialnym) wizualizuje punkty danych na osiach promieniujących z centralnego punktu. Aspose.Words udostępnia metodę `DocumentBuilder.insertChart` w tym celu.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` zwraca obiekt `Chart`, który możesz dalej konfigurować. Wykres pojawia się na pierwszej stronie pustego dokumentu, ponieważ builder domyślnie jest ustawiony na początek dokumentu.

## Wstaw wykres do pliku Word — dodawanie serii danych

Wykres bez danych jest niewidoczny. Wypełnij wykres radarowy jedną lub wieloma seriami, aby miał sens.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Możesz dodać dowolną liczbę serii. Każda seria może mieć odrębną nazwę, która pojawia się w legendzie wykresu. Punkty danych odpowiadają osiom radialnym; kolejność ich dodawania definiuje pozycję wokół koła.

## Generowanie wykresu w dokumencie Word — zapisywanie pliku

Po skonstruowaniu wykresu zapisz dokument na dysku. Wybierz lokalizację, do której masz prawo zapisu.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Kiedy otworzysz wygenerowany plik `.docx` w Microsoft Word, zobaczysz pustą stronę z wykresem radarowym o wymiarach 400 × 300 punktów, wypełnionym przykładowymi danymi.

### Oczekiwany wynik

* Plik `RadialChartExample.docx` na pulpicie.
* Pierwsza strona zawiera wykres radarowy z pięcioma punktami danych oznaczonymi „Series 1”.
* Nie pojawia się dodatkowy tekst, ponieważ dokument rozpoczął się jako pusty.

## Dodawanie wykresu radialnego do Word — obsługa typowych przypadków brzegowych

### 1. Zmiana rozmiaru wykresu po wstawieniu

Jeśli początkowe wymiary nie pasują do Twojego układu, zmień rozmiar wykresu w następujący sposób:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Wstawianie wykresu w określone miejsce

Możesz przenieść kursor buildera do zakładki, komórki tabeli lub akapitu przed wywołaniem `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Dostosowywanie wyglądu wykresu

Aspose.Words udostępnia pełny model obiektowy wykresu, pozwalając ustawić tytuły, etykiety osi i kolory.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Radzenie sobie z brakującymi czcionkami

Jeśli środowisko docelowe nie posiada czcionki użytej w wykresie, Aspose.Words zastępuje ją domyślną czcionką. Aby zapewnić spójność, osadź wymagane czcionki:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Eksport do innych formatów

Ten sam dokument może być zapisany jako PDF, HTML lub PNG bez dodatkowych zmian w kodzie:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Pełny, gotowy do uruchomienia przykład

Połączenie wszystkich elementów daje pojedynczy program, który możesz skopiować, wkleić i uruchomić.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Uruchom ten program, otwórz wygenerowany plik i zobaczysz profesjonalny wykres radarowy gotowy do dystrybucji.

## Podsumowanie

Teraz wiesz, jak **utworzyć pusty dokument Word**, **jak wstawić wykres radarowy** oraz **generować wykres w dokumencie Word** przy użyciu Aspose.Words. Postępując zgodnie z powyższymi krokami, możesz także **dodawać wykresy radialne do plików Word** w dowolnym zautomatyzowanym procesie raportowania, dostosowywać rozmiar, styl i eksportować do dodatkowych formatów.

**Kolejne kroki**

* Poznaj inne typy wykresów (`ChartType.Column`, `ChartType.Pie`), aby poszerzyć zestaw narzędzi raportowych.
* Łącz wiele wykresów na jednej stronie, wywołując `InsertChart` wielokrotnie.
* Integruj dane z bazy danych lub pliku CSV, aby dynamicznie wypełniać serie.
* Przejrzyj dokumentację Aspose.Words pod kątem zaawansowanych opcji formatowania, takich jak warunkowe etykiety danych i szablony wykresów.

Śmiało eksperymentuj z kodem, zmieniaj wymiary lub zamień przykładowe dane na rzeczywiste wskaźniki biznesowe. Szczęśliwego kodowania!

## Co powinieneś się nauczyć dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Wstaw wykres kolumnowy w Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Utwórz wykres punktowy w Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Wstaw wykres bąbelkowy w Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}