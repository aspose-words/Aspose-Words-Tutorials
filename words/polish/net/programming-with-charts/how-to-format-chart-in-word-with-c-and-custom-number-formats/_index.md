---
category: general
date: 2026-10-13
description: Jak sformatować wykres w Wordzie przy użyciu C#, stosując własny format
  liczbowy, np. walutowy, do osi wykresu. Zawiera krok po kroku przykład kodu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: pl
lastmod: 2026-10-13
og_description: Jak sformatować wykres w programie Word przy użyciu C# pozwala zastosować
  własny format liczbowy do osi wykresu, zapewniając, że wartości będą wyświetlane
  jako waluta, procenty lub dowolny inny wzór, którego potrzebujesz. Postępuj zgodnie
  z przewodnikiem krok po kroku.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Jak sformatować wykres w Wordzie przy użyciu C# – niestandardowe formaty
  liczb
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Jak sformatować wykres w Wordzie przy użyciu C# i niestandardowych formatów
  liczb
url: /pl/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak sformatować wykres w Wordzie przy użyciu C# i własnych formatów liczb

Formatowanie wykresu w Wordzie przy użyciu C# jest częstym wymaganiem, gdy trzeba profesjonalnie przedstawić dane. Ten przewodnik pokazuje, jak zastosować własny format liczbowy do osi wykresu przy użyciu **Aspose.Words for .NET**, aby wartości wyświetlały się dokładnie tak, jak oczekujesz.

Nauczysz się, jak wczytać plik DOCX, znaleźć pierwszy wykres, odczytać bieżący format, a następnie ustawić nowy wzorzec, np. walutowy z dwoma miejscami po przecinku. Samouczek obejmuje także zmianę formatu osi wykresu dla dodatkowych serii oraz resetowanie formatu w razie potrzeby.

## Wymagania wstępne

* .NET 6.0 lub nowszy zainstalowany  
* Projekt w Visual Studio 2022 (lub dowolnym IDE obsługującym .NET)  
* Pakiet NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* Dokument Word (`input.docx`) zawierający przynajmniej jeden wykres

Możesz dodać pakiet przy użyciu następującego polecenia:

```bash
dotnet add package Aspose.Words
```

## Jak sformatować wykres w Wordzie przy użyciu Aspose.Words

Poniższy kompletny program demonstruje każdy krok niezbędny do **formatowania wykresu** wartości osi. Zapisz plik jako `Program.cs` i uruchom go z wiersza poleceń lub w swoim IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Wyjaśnienie każdego kroku

| Krok | Dlaczego ma znaczenie | Kluczowy kod |
|------|-----------------------|--------------|
| **Wczytaj dokument** | Potrzebujesz obiektu `Document`, aby pracować z plikiem Word. | `new Document("input.docx")` |
| **Pobierz wykres** | Obiekty `Chart` są przechowywane jako węzły `Shape`; rzutowanie pozwala używać API specyficznych dla wykresów. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Uzyskaj dostęp do wartości X** | Formatowanie osi jest stosowane do kolekcji wartości serii danych. | `chart.ChartData.Series[0].XValues` |
| **Odczytaj bieżący format** | Znajomość istniejącego `FormatCode` pomaga zdecydować, czy go zastąpić, czy rozszerzyć. | `xValues.FormatCode` |
| **Ustaw własny format** | Właściwość `FormatCode` akceptuje dowolny wzorzec zgodny z Excelem, umożliwiając waluty, procenty, daty itp. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Zapisz dokument** | Zachowanie zmian zapisuje nowy format osi z powrotem do pliku DOCX. | `doc.Save("output_formatted.docx")` |

Uruchomienie programu generuje `output_formatted.docx`. Otwórz go w Wordzie, a zobaczysz wartości osi X wykresu wyświetlane jako **$1,234.00**, **$2,345.00**, … zamiast zwykłych liczb.

## Zastosuj własny format liczbowy do osi wykresu

Jeśli potrzebujesz **zastosować własny format liczbowy** do osi Y lub do dodatkowych serii, proces jest identyczny — wystarczy skierować się do innej kolekcji:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Wskazówka:** Używaj podwójnych cudzysłowów wewnątrz łańcucha formatu, aby wstawić znaki dosłowne (np. `"$"` dla waluty). Ucieknij cudzysłowy tak, jak pokazano powyżej.

## Własny format liczbowy w Wordzie – obsługa lokalizacji Worda

Word respektuje lokalizację dokumentu przy interpretacji formatów liczbowych. Jeśli dokument używa innej niż amerykańska lokalizacji, może być konieczne dostosowanie łańcucha formatu:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Testowanie formatu w dokumencie z ustawieniami języka niemieckiego potwierdza, że wartości pojawiają się jako **€ 1.234,00**.

## Jak ustawiać właściwości wykresu programowo

Poza formatowaniem osi, często chcesz **ustawić wykres** tytuły, legendy lub etykiety danych. Oto szybki fragment kodu, który demonstruje ustawianie tytułu wykresu po sformatowaniu osi:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Połączenie tego z własnym formatem liczbowym daje w pełni dopracowany wykres gotowy do raportowania.

## Zmieniaj format osi wykresu dynamicznie w zależności od danych wejściowych użytkownika

W rzeczywistych aplikacjach możesz pozwolić użytkownikom wybrać format w czasie działania. Poniższa metoda enkapsuluje logikę formatowania:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Możesz wywołać `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` dla waluty lub `SetAxisFormat(chart, 0, "0%")` dla procentów. Takie podejście utrzymuje główny kod w czystości i wspiera przyszłe rozszerzenia.

## Przypadki brzegowe i typowe pułapki

| Sytuacja | Na co zwrócić uwagę | Sugerowane rozwiązanie |
|----------|---------------------|------------------------|
| Dokument nie zawiera **żadnego wykresu** | `GetChild` zwraca `null`, co powoduje wyjątek rzutowania. | Sprawdź `null` przed rzutowaniem (zobacz przykład). |
| Wiele wykresów w tym samym dokumencie | Kod zawsze pobiera pierwszy wykres (`indeks 0`). | Iteruj przez `doc.GetChildNodes(NodeType.Shape, true)` i filtruj po `ShapeType.Chart`. |
| Seria **bez wartości X** (np. wykresy kołowe) | Dostęp do `XValues` może rzucić `ArgumentOutOfRangeException`. | Sprawdź, czy `Series[i].XValues` nie jest puste przed formatowaniem. |
| Niezgodność lokalizacji | Symbol waluty może wyświetlać się niepoprawnie. | Jawnie ustaw `xValues.FormatCode` z odpowiednimi symbolami lokalizacji. |

## Oczekiwany wynik

Po uruchomieniu przykładowego programu, otwórz **output_formatted.docx**. Oś X wykresu powinna wyświetlać liczby w wybranym własnym formacie. Dla przykładu walutowego etykiety osi wyglądają tak:

```
$1,000.00
$2,000.00
$3,000.00
```

Jeśli zastosowałeś format procentowy do wartości Y, etykiety osi Y pojawiają się jako:

```
10%
20%
30%
```

## Podsumowanie

Ten samouczek pokazał, **jak sformatować wykres** w Wordzie przy użyciu C# poprzez **zastosowanie własnego formatu liczbowego** do wartości osi. Masz teraz wzorzec wielokrotnego użytku do ustawiania waluty, procentów lub dowolnego innego wzoru liczbowego, a także wskazówki dotyczące obsługi lokalizacji, wielu serii i dynamicznych danych wejściowych od użytkownika.

Następnie możesz zbadać **jak ustawiać tytuły wykresu**, etykiety danych lub nawet eksportować wykres jako obraz przy użyciu `ChartRenderer`. Te tematy rozwijają bezpośrednio koncepcje omówione tutaj i pomogą Ci stworzyć w pełni zautomatyzowane rozwiązania raportowe.

---

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i zbadać alternatywne podejścia implementacyjne w własnych projektach.

- [Format liczb dla osi w wykresie](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Formatuj liczbę etykiety danych w wykresie](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Formatuj drugą oś X i ustaw jednostki wyświetlania na tysiące w wykresach liniowych Worda przy użyciu Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}