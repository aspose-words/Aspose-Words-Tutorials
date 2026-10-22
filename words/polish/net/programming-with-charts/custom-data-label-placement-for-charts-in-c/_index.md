---
category: general
date: 2026-08-04
description: Niestandardowe rozmieszczanie etykiet danych w wykresach w C# umożliwia
  wyśrodkowanie etykiet na segmentach wykresu. Postępuj zgodnie z tym przewodnikiem
  krok po kroku, korzystając z API wykresów Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: pl
lastmod: 2026-08-04
og_description: Niestandardowe rozmieszczenie etykiet danych dla wykresów w C# pokazuje,
  jak wyśrodkować wszystkie etykiety danych na każdym segmencie wykresu w programie
  Word. Opanuj pozycjonowanie etykiet danych wykresu z Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Niestandardowe rozmieszczanie etykiet danych w wykresach w C# – przewodnik
  krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Niestandardowe rozmieszczenie etykiet danych w wykresach w C#
url: /pl/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Niestandardowe rozmieszczenie etykiet danych w wykresach w C#

**Custom Data‑Label Placement for Charts** pozwala dokładnie kontrolować, gdzie pojawia się każda etykieta na wykresie w dokumencie Word. W tym samouczku nauczysz się, jak wyśrodkować wszystkie etykiety danych na każdym kawałku przy użyciu C# i API wykresów Aspose.Words.

Otrzymasz kompletny, gotowy do uruchomienia przykład, który ładuje plik `.docx`, uzyskuje dostęp do pierwszego kształtu wykresu, zmienia `Position` każdej etykiety na `Center` i zapisuje zaktualizowany dokument. Nie są wymagane zewnętrzne odwołania — wystarczy biblioteka Aspose.Words for .NET oraz podstawowe środowisko programistyczne C#.

**Co się nauczysz**

* Jak załadować dokument Word zawierający wykres.  
* Jak zlokalizować kształt wykresu przy użyciu API wykresów Aspose.Words.  
* Jak zastosować **pozycjonowanie etykiet danych wykresu** do każdej serii w wykresie.  
* Jak zapisać dokument, aby wyśrodkowane etykiety pojawiały się w Wordzie.  

**Wymagania wstępne**

* .NET 6.0 (lub nowszy) zainstalowany.  
* Visual Studio 2022 (lub dowolne IDE C#).  
* Odwołanie do pakietu NuGet `Aspose.Words`.  
* Plik Word (`Chart.docx`) zawierający przynajmniej jeden wykres.

---

## Niestandardowe rozmieszczenie etykiet danych w wykresach – krok 1: załaduj dokument

Pierwszym działaniem jest otwarcie pliku Word, który zawiera wykres. `Document` jest punktem wejścia do wszelkich manipulacji przy użyciu Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Dlaczego ten krok ma znaczenie*: Bez załadowania dokumentu nie możesz uzyskać dostępu do obiektu wykresu. Walidacja zapewnia wyświetlenie czytelnego błędu, jeśli plik nie zawiera wykresu, zapobiegając późniejszemu odwołaniu do null.

---

## Korzystanie z API wykresów Aspose.Words do uzyskania dostępu do kształtów wykresów

Aspose.Words traktuje wykres jako obiekt `Chart` zagnieżdżony wewnątrz `Shape`. Pobierasz go, rzutując odpowiedni węzeł potomny.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Dlaczego ten krok ma znaczenie*: Bezpośredni dostęp do `Chart` daje pełną kontrolę nad seriami, punktami danych i właściwościami etykiet. Jeśli kształt nie jest wykresem, kod przerywa działanie wcześnie, wyświetlając informacyjną wiadomość.

---

## Ustawianie pozycjonowania etykiet danych wykresu w C#

Teraz przeiteruj przez każdą serię i każdą etykietę danych, ustawiając `Position` na `Center`. To jest sedno **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Wskazówka**: Jeśli potrzebujesz innego rozmieszczenia (np. `InsideEnd` dla wykresu kolumnowego), zmień odpowiednio wartość wyliczenia. Wyliczenie `ChartDataLabelPosition` obejmuje wszystkie standardowe pozycje obsługiwane przez Word.

*Dlaczego ten krok ma znaczenie*: Zmiana `label.Position` aktualizuje podstawową reprezentację OOXML, dzięki czemu etykieta pojawia się wyśrodkowana po otwarciu dokumentu w Microsoft Word.

---

## Zapisywanie dokumentu Word z zaktualizowanymi etykietami

Po modyfikacji wykresu zapisz zmiany z powrotem do pliku. Możesz nadpisać oryginał lub utworzyć nową kopię.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Dlaczego ten krok ma znaczenie*: Zapis zapisuje zaktualizowany OOXML na dysku. Otwarcie `ChartLabelsCentered.docx` w Wordzie pokaże każdą etykietę wyśrodkowaną, potwierdzając, że **Custom Data‑Label Placement for Charts** zakończyło się sukcesem.

---

## Przypadki brzegowe i warianty

| Sytuacja | Jak postąpić |
|-----------|---------------|
| **Wiele wykresów** w tym samym dokumencie | Iteruj po `doc.GetChildNodes(NodeType.Shape, true)` i sprawdzaj `shape.HasChart` dla każdego kształtu. |
| **Różne typy wykresów** (pie, doughnut, bar) | To samo `ChartDataLabelPosition.Center` działa dla wykresów kołowych. Dla wykresów słupkowych/kolumnowych możesz preferować `InsideEnd` lub `OutsideEnd`. |
| **Tekst etykiety wymaga formatowania** | Uzyskaj dostęp do `label.TextProperties`, aby ustawić rozmiar czcionki, kolor lub pogrubienie. |
| **Uruchamianie na .NET Core** | Upewnij się, że odwołujesz się do wersji .NET Standard biblioteki Aspose.Words; API jest identyczne. |

---

## Pełny działający przykład

Poniżej znajduje się pełny program, który możesz skopiować i wkleić do aplikacji konsolowej. Zawiera wszystkie niezbędne dyrektywy `using` oraz obsługę błędów.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Oczekiwany rezultat**: Otwórz `ChartLabelsCentered.docx` w Microsoft Word. Każdy kawałek wykresu wyświetla teraz swoją etykietę danych bezpośrednio w centrum kawałka, zapewniając czystszy wygląd wizualny.

---

## Zakończenie

Masz teraz kompletną **Custom Data‑Label Placement for Charts** rozwiązanie w C#. Ładując dokument, uzyskując dostęp do wykresu za pomocą API wykresów Aspose.Words, ustawiając `ChartDataLabelPosition.Center` dla każdej etykiety i zapisując plik, możesz automatyzować pozycjonowanie etykiet dla dowolnego wykresu w Wordzie.

Następnie, poznaj inne opcje **pozycjonowania etykiet danych wykresu**, takie jak `InsideEnd` lub `OutsideEnd`, lub eksperymentuj z **manipulacją wykresów w C#**, aby zmieniać kolory, dodawać legendy lub generować wykresy od podstaw. Te rozszerzenia opierają się bezpośrednio na technikach omówionych tutaj i poszerzają Twoje umiejętności automatyzacji wykresów w dokumentach Word. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Dostosuj etykietę danych wykresu](/words/english/net/programming-with-charts/chart-data-label/)
- [Formatuj liczbę etykiet danych w wykresie](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Etykieta danych wykresu](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}