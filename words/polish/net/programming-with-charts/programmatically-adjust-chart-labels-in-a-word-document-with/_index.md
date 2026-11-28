---
category: general
date: 2026-10-13
description: Dowiedz się, jak programowo dostosować etykiety wykresu w dokumencie
  Word przy użyciu C#. Ten przewodnik obejmuje manipulację wykresami w Aspose.Words
  oraz wyrównywanie etykiet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: pl
lastmod: 2026-10-13
og_description: Programowo dostosuj etykiety wykresu w dokumencie Word przy użyciu
  C#. Przejdź przez ten kompletny poradnik, aby zmienić położenie etykiet, ich wyrównanie
  i inne.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Programowo dostosuj etykiety wykresu w Word – przewodnik krok po kroku w
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Programowo dostosuj etykiety wykresu w dokumencie Word przy użyciu C#
url: /pl/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programowe dostosowanie etykiet wykresu w dokumencie Word przy użyciu C#

Jeśli potrzebujesz **programowo dostosować etykiety wykresu** w dokumencie Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić w C#. Niezależnie od tego, czy generujesz raporty, automatyzujesz pulpity nawigacyjne, czy dostosowujesz szablony, zobaczysz pełny, działający przykład, który zmienia położenie i wyrównanie etykiet wykresu w pliku .docx.

Dowiesz się także, jak używać technik **manipulacji wykresami Aspose.Words**, obsługiwać wiele serii i unikać typowych pułapek przy pracy z obiektami **C# chart data label**.

## Wymagania wstępne

* .NET 6.0 (lub nowszy) zainstalowany  
* Visual Studio 2022 (lub dowolne IDE C#)  
* Pakiet NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Dokument Word (`input.docx`) zawierający przynajmniej jeden wykres  

Te elementy są wymagane dla **przykładu wykresu w dokumencie Word**, który będziemy modyfikować.

## Krok 1: Konfiguracja projektu i import przestrzeni nazw

Utwórz nowy projekt konsolowy i dodaj niezbędne dyrektywy `using`. Przygotowuje to środowisko do **programowego dostosowania etykiet wykresu**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Dlaczego ten krok?*  
Załadowanie dokumentu daje dostęp do wewnętrznego drzewa **przykładu wykresu w dokumencie Word**, w którym wykresy są przechowywane jako węzły kształtów.

## Krok 2: Znalezienie pierwszego kształtu wykresu

Wykresy są przechowywane jako węzły `Shape`. Poniższy kod pobiera pierwszy wykres w dokumencie, który jest celem naszych modyfikacji etykiet.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Dlaczego ten krok?*  
Metoda `GetChild` przeszukuje rekurencyjnie (`true`) i zwraca pierwszy węzeł typu `Shape`. Rzutowanie na `Chart` umożliwia pracę z API specyficznym dla wykresu.

## Krok 3: Dostęp do etykiety danych, którą chcesz zmodyfikować

Każda seria w wykresie ma kolekcję etykiet danych. Dla prostego wykresu zazwyczaj wystarczy pierwsza etykieta. Poniższy kod pokazuje, jak do niej dotrzeć.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Dlaczego ten krok?*  
`ChartSeries` reprezentuje serię punktów. `DataLabelCollection` przechowuje etykiety dla tej serii, umożliwiając precyzyjną kontrolę nad położeniem i wyrównaniem.

## Krok 4: Zmiana położenia i wyrównania etykiet

Teraz **programowo dostosowujemy etykiety wykresu** ustawiając pozycję, wyrównanie poziome i pionowe. Właściwości te odpowiadają opcjom widocznym w interfejsie Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Dlaczego te ustawienia?*  

* `OutsideEnd` umieszcza etykietę tuż poza końcem każdego słupka lub kolumny, zwiększając czytelność.  
* `HorizontalAlignment.Center` utrzymuje tekst wyśrodkowany nad punktem, natomiast `VerticalAlignment.Top` wyrównuje górną krawędź etykiety z punktem danych, zapobiegając nakładaniu się na inne elementy.

### Porada
Jeśli wykres ma wiele serii, przeiteruj `chart.Series` i zastosuj te same ustawienia do każdej `DataLabelCollection`. Zapewni to spójny wygląd całego wykresu.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Krok 5: Zapisz zmodyfikowany dokument

Po dostosowaniu etykiet, zachowaj zmiany w nowym pliku. To kończy proces **modyfikacji pozycji etykiet wykresu**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Po otwarciu `output.docx` zobaczysz, że każda etykieta wykresu została przeniesiona na zewnętrzny koniec swojego punktu danych, wyśrodkowana poziomo i wyrównana do góry pionowo.

## Przypadki brzegowe i warianty

| Sytuacja | Na co zwrócić uwagę | Zalecane podejście |
|-----------|-------------------|----------------------|
| **Wiele wykresów** w tym samym dokumencie | `GetChild` zwraca tylko pierwszy wykres. | Użyj `doc.GetChildNodes(NodeType.Shape, true)`, aby iterować po wszystkich kształtach wykresów. |
| **Seria bez etykiet danych** | `DataLabelCollection` może być pusty. | Sprawdź `series.HasDataLabels` przed dostępem do kolekcji. |
| **Różne typy wykresów** (pie, line, scatter) | Nie wszystkie wartości `DataLabelPosition` są prawidłowe. | Użyj `DataLabelPosition.Auto` dla wykresów, które automatycznie decydują o najlepszym położeniu. |
| **Lokalizacja** | Stałe wyrównania są niezależne od języka, ale renderowany tekst może wymagać wsparcia od prawej do lewej. | Ustaw `dataLabel.TextDirection`, jeśli potrzebujesz języków RTL. |

## Pełny, działający przykład

Poniżej znajduje się pełny program, który możesz skopiować, wkleić i uruchomić. Zamień `YOUR_DIRECTORY` na rzeczywistą ścieżkę folderu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Oczekiwany wynik:** Po otwarciu `output.docx` każda etykieta wykresu będzie umieszczona poza punktem danych, wyśrodkowana poziomo i wyrównana do góry — dokładnie taki efekt **programowego dostosowania etykiet wykresu**, jaki zaprogramowałeś.

## Zakończenie

Teraz wiesz, jak **programowo dostosować etykiety wykresu** w dokumencie Word przy użyciu C#. Poradnik obejmował:

* Ładowanie dokumentu przy użyciu **manipulacji wykresami Aspose.Words**  
* Dostęp do **C# chart data label**  
* Zmianę **modify chart label position** i wyrównania  
* Zapisanie pliku i obsługę typowych przypadków brzegowych  

Od tego momentu możesz eksplorować bardziej zaawansowane scenariusze, takie jak dostosowywanie czcionek etykiet, dodawanie formatowania warunkowego lub aktualizowanie wielu wykresów w procesie wsadowym. Eksperymentuj z różnymi opcjami `DataLabelPosition`, aby znaleźć styl najlepiej pasujący do Twoich raportów.

---

*Gotowy, aby usprawnić swój zautomatyzowany proces raportowania? Spróbuj dodać własne formaty liczb do etykiet lub wyeksportować wykres jako obraz do użycia w PDF-ach.*

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Ustaw jednolite etykiety danych w wykresie kolumnowym przy użyciu Aspose.Words dla .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Ustaw domyślne opcje dla etykiet danych w wykresie](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Zaktualizuj dane serii wykresu w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}