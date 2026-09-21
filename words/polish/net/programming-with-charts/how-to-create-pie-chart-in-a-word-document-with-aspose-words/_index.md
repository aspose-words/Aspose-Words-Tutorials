---
category: general
date: 2026-09-21
description: Dowiedz się, jak stworzyć wykres kołowy i wstawić go do Worda przy użyciu
  Aspose.Words, dodać etykiety danych do wykresu kołowego oraz wyświetlić procenty
  na wykresie kołowym w kilku prostych krokach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: pl
lastmod: 2026-09-21
og_description: Utwórz wykres kołowy w Wordzie przy użyciu Aspose.Words, wstaw wykres
  do dokumentu, dodaj etykiety danych do wykresu kołowego i wyświetl procenty na wykresie
  — wszystko z przejrzystymi przykładami kodu.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Tworzenie wykresu kołowego w Wordzie z Aspose.Words – przewodnik krok po
  kroku
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Jak utworzyć wykres kołowy w dokumencie Word przy użyciu Aspose.Words
url: /pl/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć wykres kołowy w dokumencie Word przy użyciu Aspose.Words

Jeśli potrzebujesz **utworzyć wykres kołowy** programowo, Aspose.Words czyni to prostym. W tym samouczku zobaczysz, jak **wstawić wykres do Worda**, skonfigurować serie, **dodać etykiety danych do wykresu kołowego** oraz w końcu **wyświetlić procenty na wykresie kołowym**, aby wizualizacja przekazywała dokładne wartości. Po zakończeniu będziesz mieć kompletny, gotowy do uruchomienia przykład, który możesz wkleić do dowolnego projektu .NET.

Ten przewodnik obejmuje wszystko, co musisz wiedzieć: wymagane pakiety NuGet, pełny kod źródłowy C#, wyjaśnienia, dlaczego każde wywołanie API ma znaczenie, oraz wskazówki dotyczące dostosowywania wykresu. Nie potrzebujesz dodatkowej dokumentacji – po prostu skopiuj, uruchom i dostosuj.

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

* Zainstalowany .NET 6.0 SDK lub nowszy.  
* Visual Studio 2022 (lub dowolne IDE obsługujące .NET).  
* Licencję Aspose.Words for .NET (bezpłatna wersja próbna wystarczy do testów).  
* Podstawową znajomość C# oraz struktury dokumentów Word.

Jeśli już to wszystko masz, możesz przejść od razu do kodu.

## Krok 1: Utwórz projekt i zaimportuj Aspose.Words

Utwórz nowy projekt konsolowy i dodaj pakiet NuGet Aspose.Words:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Pakiet zawiera przestrzeń nazw `Aspose.Words.Drawing.Charts`, w której znajdują się klasy `Chart` i `ChartSeries`, z których będziemy korzystać.

> **Wskazówka:** Umieść plik licencyjny (`Aspose.Words.lic`) w katalogu głównym projektu i wczytaj go przy starcie, aby uniknąć znaków wodnych wersji ewaluacyjnej.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Krok 2: Utwórz pusty dokument i DocumentBuilder

`Document` reprezentuje plik Word, natomiast `DocumentBuilder` zapewnia płynne API do wstawiania treści.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Dlaczego to ważne:** `DocumentBuilder` utrzymuje bieżący punkt wstawiania, zapewniając, że wykres pojawi się dokładnie tam, gdzie chcesz w przepływie dokumentu.

## Krok 3: Wstaw wykres kołowy do dokumentu Word

Teraz **wstawiamy wykres do Worda**. Metoda `InsertChart` przyjmuje typ wykresu, szerokość i wysokość (w punktach).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Na tym etapie wykres zawiera domyślną serię danych z wartościami zastępczymi (25, 25, 25, 25). Możesz je później zamienić, jeśli zajdzie taka potrzeba.

## Krok 4: Uzyskaj dostęp do pierwszej serii i dostosuj etykiety danych

Wykres kołowy zazwyczaj ma jedną serię. Aby **dodać etykiety danych do wykresu kołowego**, pobieramy ją i włączamy wyświetlanie procentów.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Dlaczego ustawiamy `ShowPercentage`:** Ten znacznik mówi Aspose.Words, aby obliczył udział każdego wycinka i wyświetlił go jako procent. Właściwość `Position` zapewnia, że etykieta nie nachodzi na wycinek, co poprawia czytelność – szczególnie gdy wycinki są małe.

## Krok 5: (Opcjonalnie) Zamień dane zastępcze

Jeśli potrzebujesz konkretnych wartości, zamień domyślne punkty:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Wyświetlane procenty automatycznie dostosują się do nowych wartości.

## Krok 6: Zapisz dokument

Na koniec zapisz dokument na dysku. Rozszerzenie określa format; `.docx` tworzy nowoczesny plik Word.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Uruchomienie programu wygeneruje plik o nazwie **PieChart.docx** w folderze wyjściowym. Otwierając go w Microsoft Word zobaczysz wykres kołowy, w którym każdy wycinek jest oznaczony swoim procentem, umieszczonym na zewnątrz wycinków.

### Oczekiwany wynik

Po otwarciu wygenerowanego dokumentu powinieneś zobaczyć:

* Jeden wykres kołowy, o wymiarach 400 × 300 pt.  
* Cztery wycinki (lub tyle, ile dodałeś punktów).  
* Etykiety procentowe, takie jak „40 %”, „30 %” itp., wyświetlane poza każdym wycinkiem.

Jeśli etykiety pojawią się wewnątrz wycinków, sprawdź, czy poprawnie ustawiono `ChartDataLabelPosition.OutsideEnd`.

## Krok 7: Typowe warianty i przypadki brzegowe

### Dodanie tytułu do wykresu

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Zmiana kolorów wycinków

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Obsługa pustej serii

Jeśli źródło danych może być puste, zabezpiecz się przed `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Eksport do PDF zamiast Worda

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

Logika renderowania wykresu pozostaje taka sama; Aspose.Words automatycznie konwertuje układ Worda na PDF.

## Pełny listing źródłowy

Poniżej znajduje się kompletny, gotowy do uruchomienia program. Skopiuj go do `Program.cs` i wykonaj `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Podsumowanie

Teraz wiesz, jak **utworzyć wykres kołowy** w pliku Word przy użyciu Aspose.Words, **wstawić wykres do Worda**, **dodać etykiety danych do wykresu kołowego** oraz **wyświetlić procenty na wykresie kołowym**. Przykład demonstruje pełny przepływ – od konfiguracji projektu po finalny dokument – dzięki czemu możesz go dostosować do pulpitów nawigacyjnych, raportów czy automatycznego generowania faktur.

Następnie odkryj powiązane tematy, takie jak **wyświetlanie procentów w legendach wykresu**, dostosowywanie kolorów wykresu lub konwersja dokumentu Word do PDF w celu dystrybucji. Eksperymentuj z innymi typami wykresów (słupkowy, liniowy) używając tej samej metody `InsertChart`, aby poszerzyć możliwości automatyzacji.

Miłego wykreślania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}