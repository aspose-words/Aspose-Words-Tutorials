---
category: general
date: 2026-09-21
description: Jak sformatować serię w wykresie liniowym w programie Word przy użyciu
  C#. Dowiedz się, jak utworzyć dokument Word, wstawić wykres liniowy i zastosować
  niestandardowy format liczbowy.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: pl
lastmod: 2026-09-21
og_description: Jak sformatować serie na wykresie liniowym w programie Word przy użyciu
  C#. Ten samouczek pokazuje, jak utworzyć dokument Word, wstawić wykres liniowy i
  zastosować własny format liczbowy.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Jak sformatować serie w wykresie liniowym Word przy użyciu C# – przewodnik
  krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Jak sformatować serie w wykresie liniowym w Wordzie przy użyciu C#
url: /pl/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak sformatować serie w wykresie liniowym Word przy użyciu C#

Jeśli potrzebujesz **jak sformatować serie** w wykresie liniowym Word, ten przewodnik dostarczy Ci kompletną, gotową do uruchomienia rozwiązanie. Zobaczysz, jak **utworzyć dokument Word**, **wstawić wykres liniowy** oraz **zastosować własny format liczbowy** do wartości Y — wszystko przy użyciu Aspose.Words for .NET.

Automatyzacja Worda staje się prosta, gdy zrozumiesz model obiektowy wykresu. Po zakończeniu tego samouczka będziesz mieć plik Word zawierający wykres liniowy, którego serie danych są wyświetlane jako procenty z dwoma miejscami po przecinku.

## Co osiągniesz

* Programowo wygenerujesz pusty plik `.docx`.  
* Dodasz wykres liniowy o rozmiarze 400 × 300 punktów.  
* Uzyskasz dostęp do pierwszej serii danych wykresu.  
* Zastosujesz kod formatu `#,##0.00%`, aby wartości Y wyświetlały się jako procenty.  

Nie są wymagane żadne zewnętrzne narzędzia poza pakietem NuGet Aspose.Words.

## Wymagania wstępne

* .NET 6.0 SDK lub nowszy.  
* Visual Studio 2022 (lub dowolne IDE C#).  
* Aspose.Words for .NET 23.10 lub nowszy – zainstaluj za pomocą `dotnet add package Aspose.Words`.  

Kod działa na Windows, Linux i macOS, ponieważ Aspose.Words jest niezależny od platformy.

## Utworzenie dokumentu Word przy użyciu Aspose.Words

Pierwszym krokiem jest utworzenie obiektu `Document`. Obiekt ten reprezentuje cały plik Word w pamięci.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Dlaczego to ważne*: `Document` jest punktem wejścia dla wszystkich operacji przetwarzania Worda. Bez niego nie możesz dodawać akapitów, tabel ani wykresów.

## Wstawienie wykresu liniowego do dokumentu

`DocumentBuilder` zapisuje zawartość do obiektu `Document`. Wywołanie `InsertChart` tworzy kształt wykresu na bieżącej stronie.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Dlaczego to ważne*: `InsertChart` zwraca obiekt `Chart`, który daje pełną kontrolę nad seriami, osiami i formatowaniem. Parametry rozmiaru wyrażone są w punktach (1 punkt = 1/72 cala).

## Uzyskanie dostępu do pierwszej serii danych

Każdy wykres zawiera jedną lub więcej `ChartSeries`. Pierwsza seria znajduje się pod indeksem 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Dlaczego to ważne*: Obiekt `ChartSeries` przechowuje wartości Y, wartości X oraz opcje formatowania dla jednej linii w wykresie liniowym. Modyfikacja tego obiektu zmienia wizualną reprezentację danych.

## Zastosowanie własnego formatu liczbowego do serii

Właściwość `FormatCode` kontroluje sposób wyświetlania wartości liczbowych. Ustawienie jej na `#,##0.00%` mówi Wordowi, aby traktował wartości jako procenty z dwoma miejscami po przecinku.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Dlaczego to ważne*: Bez własnego formatu Word pokazuje surowe liczby dziesiętne (np. `0.15`). Kod formatu zamienia je na `15.00%`, co jest częstym wymogiem raportów biznesowych.

## Zapisz dokument i zweryfikuj wynik

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Po otwarciu `FormattedSeriesLineChart.docx` w Microsoft Word zobaczysz wykres liniowy, w którym etykiety osi Y brzmią `15.00%`, `30.00%`, `45.00%` i `60.00%`. Rozmiar wykresu odpowiada wymiarom podanym w `InsertChart`.

### Oczekiwany zrzut ekranu

> *Obraz: Strona dokumentu Word pokazująca wykres liniowy z wartościami osi Y sformatowanymi jako procenty.*  
> *(Alt text: Zrzut ekranu dokumentu Word pokazujący wykres liniowy z wartościami osi Y sformatowanymi jako procenty)*

## Typowe warianty i przypadki brzegowe

| Sytuacja | Dostosowanie |
|-----------|------------|
| **Wiele serii** | Przejdź pętlą przez `chart.Series` i ustaw `FormatCode` dla każdej serii. |
| **Inny typ wykresu** | Zamień `ChartType.Line` na `ChartType.Column`, `ChartType.Pie` itp. |
| **Separatory specyficzne dla lokalizacji** | Użyj formatów uwzględniających `CultureInfo`, np. `"# ##0,00 %"` dla francuskich ustawień regionalnych. |
| **Dynamiczne źródło danych** | Wypełnij `series.YValues` danymi z bazy danych lub pliku CSV przed zastosowaniem formatu. |

**Wskazówka:** Zawsze stosuj format **po** dodaniu wartości Y. Zmiana formatu najpierw, a potem dodanie wartości również działa, ale zastosowanie go później gwarantuje, że format zostanie zastosowany do ostatecznego zestawu danych.

## Podsumowanie

Teraz wiesz **jak sformatować serie** w wykresie liniowym Word przy użyciu C#. W samouczku omówiono:

* Tworzenie dokumentu Word (`create word document`).  
* Wstawianie wykresu liniowego (`insert line chart`, `add chart to word`).  
* Dostęp do pierwszej serii wykresu.  
* Zastosowanie własnego formatu liczbowego (`apply custom number format`) w celu wyświetlenia procentów.

## Kolejne kroki

* Eksperymentuj z różnymi wartościami `ChartType`, aby zobaczyć, jak zachowują się inne wizualizacje.  
* Dodaj tytuły, etykiety osi i legendy używając `chart.Title`, `chart.AxisX.Title` oraz `chart.AxisY.Title`.  
* Eksportuj wykres jako obraz (`chart.Save` z `SaveFormat.Png`) do wykorzystania w raportach internetowych.

Śmiało dostosowuj ten wzorzec, aby generować pulpity nawigacyjne, raporty finansowe lub każdy dokument wymagający programowego tworzenia wykresów. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu oraz wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}