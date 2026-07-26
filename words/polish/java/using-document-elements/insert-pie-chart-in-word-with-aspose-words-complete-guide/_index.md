---
category: general
date: 2026-07-26
description: Wstaw wykres kołowy do dokumentu Word przy użyciu Aspose.Words. Dowiedz
  się, jak dodać wykres, oddzielić fragment i wyświetlić procenty w kilku prostych
  krokach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: pl
lastmod: 2026-07-26
og_description: Wstaw wykres kołowy do pliku Word przy użyciu Aspose.Words. Skorzystaj
  z tego przewodnika, aby szybko dowiedzieć się, jak dodać wykres, rozdzielić kawałki
  i wyświetlić procenty.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: 'Wstaw wykres kołowy w Word – krok po kroku: samouczek Aspose.Words'
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Wstaw wykres kołowy w Wordzie za pomocą Aspose.Words – Kompletny przewodnik
url: /pl/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw wykres kołowy w Wordzie przy użyciu Aspose.Words – Kompletny przewodnik

Kiedykolwiek potrzebowałeś **wstawić wykres kołowy** do raportu w Wordzie, ale nie wiedziałeś od czego zacząć? Nie jesteś sam. W wielu aplikacjach biznesowych wizualny efekt wykresu kołowego sprawia, że dane są od razu przyswajalne, a Aspose.Words umożliwia to przy użyciu zaledwie kilku linii kodu.

W tym samouczku przeprowadzimy Cię krok po kroku przez **dodawanie wykresu do Worda**, „wybuchnięcie” fragmentu dla podkreślenia oraz wyświetlenie procentów na etykietach danych. Po zakończeniu będziesz mieć gotowy przykład, który możesz wkleić do dowolnego projektu .NET.

---

## Prerequisites

Zanim zaczniemy, upewnij się, że masz:

- .NET 6.0 lub nowszy (kod działa zarówno z .NET Core, jak i .NET Framework)
- Zainstalowany pakiet NuGet Aspose.Words for .NET  
  ```bash
  dotnet add package Aspose.Words
  ```
- Podstawową znajomość składni C# — nic skomplikowanego nie jest wymagane
- Wybrane IDE (Visual Studio, Rider lub VS Code)

To wszystko. Zaczynamy.

---

## Insert Pie Chart into a Word Document

Pierwszą rzeczą, której potrzebujemy, jest nowy obiekt `Document` oraz `DocumentBuilder`. Traktuj builder jak pióro, które pisze bezpośrednio na płótnie Worda.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Dlaczego to ważne:** `Document` reprezentuje cały plik .docx, natomiast `DocumentBuilder` zapewnia wygodne API do wstawiania elementów takich jak wykresy, tabele i tekst. To podstawa każdej operacji **how to add chart**.

---

## How to Add Chart to Word

Teraz, gdy mamy builder, możemy naprawdę **wstawić wykres kołowy**. Metoda `insertChart` przyjmuje typ wykresu oraz żądane wymiary w punktach (1 punkt = 1/72 cala).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Wskazówka:** Jeśli potrzebujesz innego rozmiaru, po prostu zmień wartości szerokości i wysokości. Wykres automatycznie dopasuje się do marginesów strony.

---

## How to Explode Slice for Emphasis

Częstym zabiegiem wizualnym jest „wybuchnięcie” fragmentu, aby wystawał poza koło. To przyciąga wzrok czytelnika do najważniejszego segmentu.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Dlaczego wybuchać fragment?** Kiedy chcesz wyróżnić konkretną kategorię — np. „przychody Q1” w raporcie finansowym — wybuchnięcie fragmentu sprawia, że od razu przyciąga uwagę bez dodatkowego tekstu.

---

## How to Show Percentages on Data Labels

Większość wykresów kołowych wygląda lepiej, gdy każdy fragment wyświetla swój procent. Aspose.Words pozwala włączyć to jednym właściwością.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Szybka uwaga:** Flaga `ShowPercentage` działa dla wszystkich punktów w serii, więc nie musisz ustawiać jej osobno dla każdego fragmentu.

---

## Save the Document Containing the Chart

Na koniec zapisujemy dokument na dysku. Wybierz dowolny folder; upewnij się jedynie, że ścieżka istnieje.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Gdy otworzysz `PieChart.docx` w Microsoft Word, zobaczysz perfekcyjnie wyrenderowany wykres kołowy z pierwszym fragmentem wybuchniętym i wyświetlonymi procentami — dokładnie to, czego oczekujesz od dopracowanego raportu biznesowego.

---

## Full Working Example

Poniżej znajduje się kompletny, gotowy do skopiowania program. Uruchom go jako aplikację konsolową i sprawdź wygenerowany plik.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Oczekiwany rezultat:** Otwórz wygenerowany `PieChart.docx`. Zobaczysz wykres kołowy z trzema fragmentami zatytułowany „Sales Q1”, przy czym pierwszy fragment jest wyciągnięty, a każdy fragment oznaczony jest kolejno „30 %”, „45 %” i „25 %”. Wizualizacja odpowiada wprowadzonym danym.

---

## Common Questions & Edge Cases

- **Co jeśli potrzebuję więcej niż jednej serii?**  
  Po prostu dodaj dodatkowe obiekty `ChartSeries` do `chart.Series`. Każda seria może mieć własny zestaw danych, kolory i ustawienia wybuchnięcia.

- **Czy mogę zmienić kolory wykresu?**  
  Tak. Każdy `ChartPoint` posiada właściwość `Format.Fill.ForeColor`, którą możesz ustawić na dowolny `System.Drawing.Color`.

- **A co z innymi typami wykresów?**  
  Enum `ChartType` zawiera wykresy słupkowe, liniowe, pierścieniowe i wiele innych. Zamień `ChartType.Pie` na dowolny typ, którego potrzebujesz.

- **Czy wykres można edytować w Wordzie po wstawieniu?**  
  Absolutnie. Word traktuje wykres jako natywny wykres Office, więc użytkownicy mogą dwukrotnie kliknąć go, aby otworzyć wbudowany edytor wykresów.

---

## Conclusion

Teraz wiesz dokładnie, jak **wstawić wykres kołowy** do dokumentu Word przy użyciu Aspose.Words, **jak dodać wykres do Worda**, **jak wybuchnąć fragment** oraz **jak wyświetlić procenty** na etykietach danych. Pełny przykład powyżej jest gotowy do uruchomienia, a Ty możesz go rozbudować o własne dane, stylizacje lub dodatkowe serie.

Gotowy na kolejny krok? Spróbuj zamienić wykres kołowy na pierścieniowy lub wygeneruj partię raportów z różnymi zestawami danych automatycznie. Jeśli interesują Cię inne wizualizacje, sprawdź nasze przewodniki o **how to add chart** dla wykresów słupkowych i liniowych lub zagłęb się w referencję API **add chart to word** po więcej zaawansowanych dostosowań.

Miłego kodowania i niech Twoje dokumenty będą zawsze tak klarowne jak idealnie pokrojona tarta!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}