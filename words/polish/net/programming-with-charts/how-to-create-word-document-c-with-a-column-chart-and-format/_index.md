---
category: general
date: 2026-09-21
description: Dowiedz się, jak w C# utworzyć dokument Word i wstawić wykres słupkowy,
  ustawić pozycję etykiet oraz wyświetlić wartości przy użyciu Aspose.Words w przewodniku
  krok po kroku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: pl
lastmod: 2026-09-21
og_description: Utwórz dokument Word w C# przy użyciu Aspose.Words. Ten samouczek
  pokazuje, jak wstawić wykres kolumnowy, ustawić pozycję etykiet i wyświetlić wartości.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Utwórz dokument Word w C# – wstaw wykres kolumnowy, ustaw etykietę, wyświetl
  wartości
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Jak utworzyć dokument Word w C# z wykresem słupkowym i sformatowanymi etykietami
url: /pl/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć dokument Word w C# z wykresem słupkowym i sformatowanymi etykietami

Jeśli potrzebujesz **create Word document C#**, który zawiera wykres, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Nauczysz się, jak wstawić wykres słupkowy, ustawić jego etykietę danych oraz wyświetlić wartości etykiety — wszystko przy użyciu Aspose.Words for .NET.

Tworzenie pliku Word z wykresem wymagało wcześniej ręcznej pracy w Microsoft Word. Dzięki opisanym tutaj krokom **how to insert chart** możesz zautomatyzować cały proces w kodzie, co sprawia, że generowanie raportów jest szybkie i powtarzalne. Poradnik obejmuje także **how to set label** oraz **how to display values**, dzięki czemu wykres jest gotowy dla użytkowników końcowych.

Po przeczytaniu tego artykułu będziesz mieć kompletny, działający program w C#, który tworzy plik `.docx` zawierający wykres słupkowy, którego etykiety danych znajdują się wewnątrz każdego słupka i wyświetlają ich wartości liczbowe.

## Wymagania wstępne

* .NET 6.0 SDK lub nowszy zainstalowany  
* Licencjonowana kopia **Aspose.Words for .NET** (bezpłatna wersja próbna działa do testów)  
* IDE, np. Visual Studio 2022 lub Visual Studio Code  

Nie są wymagane dodatkowe pakiety NuGet poza `Aspose.Words`.

## Krok 1: Skonfiguruj projekt i dodaj Aspose.Words

Utwórz nowy projekt konsolowy i dodaj pakiet Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

Polecenie `dotnet add package` pobiera najnowszą stabilną wersję **Aspose.Words**, która zawiera API wykresów używane w przykładzie **insert column chart word**.

## Krok 2: Utwórz nowy pusty dokument Word

Pierwszy fragment kodu tworzy pusty dokument oraz `DocumentBuilder`, który umożliwia wstawianie treści. To podstawa dla **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` reprezentuje cały plik `.docx`, natomiast `DocumentBuilder` udostępnia metody takie jak `InsertParagraph`, `InsertImage` oraz, co kluczowe w tym poradniku, `InsertChart`.

## Krok 3: Wstaw wykres słupkowy (how to insert chart)

Teraz wstawiamy **column chart**. Metoda `InsertChart` przyjmuje typ wykresu, szerokość i wysokość w punktach.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

W tym momencie wykres zawiera domyślną serię danych z wartościami zastępczymi. Możesz zamienić dane serii, jeśli potrzebujesz własnych liczb, ale do demonstracji **how to set label** i **how to display values** domyślne dane są wystarczające.

## Krok 4: Ustaw etykietę danych wewnątrz każdego słupka (how to set label)

Etykiety danych to tekst wyświetlany na każdym słupku. Aby wykres był łatwiejszy do odczytania, przenosimy etykietę do wnętrza słupka i włączamy jej wartość liczbową.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` umieszcza etykietę na szczycie słupka, ale nadal wewnątrz jego kształtu, co jest typowym stylem wizualnym w raportach. Ustawienie `ShowValue` na `true` spełnia wymaganie **how to display values**.

## Krok 5: Zapisz dokument

Na koniec zapisujemy dokument na dysku. Plik można otworzyć w Microsoft Word, LibreOffice lub dowolnym przeglądarce obsługującej format Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Uruchomienie programu generuje `output.docx`, który zawiera wykres słupkowy z etykietami danych umieszczonymi wewnątrz każdego słupka i wyświetlającymi ich wartości.

### Oczekiwany rezultat

Po otwarciu `output.docx` powinieneś zobaczyć pojedynczy wykres słupkowy podobny do poniższego obrazu. Każdy słupek ma etykietę liczbową na szczycie, wewnątrz słupka, wyświetlającą wartość serii.

![Chart in a Word document created with C#](/images/word-chart-example.png "Chart in a Word document created with C# – create word document C#")

*Alt text:* *Wykres w dokumencie Word utworzonym w C#, który demonstruje, jak wstawić column chart word i wyświetlić wartości.*

## Typowe warianty i przypadki brzegowe

### Dodawanie własnych danych do wykresu

Jeśli musisz zamienić dane zastępcze, możesz zmodyfikować kolekcję `Series` wykresu:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Zmiana czcionki i koloru etykiety

Możesz dodatkowo dostosować wygląd etykiety:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Wstawianie wielu wykresów

`DocumentBuilder` może wstawiać dowolną liczbę wykresów. Wystarczy ponownie wywołać `InsertChart` po przesunięciu kursora przy użyciu `builder.Writeln()` lub `builder.InsertParagraph()`.

## Porady profesjonalne

* **Pro tip:** Ustaw `chart.HasTitle = true` i przypisz `chart.Title.Text`, aby nadać wykresowi opisowy tytuł. Poprawia to dostępność dla czytników ekranu.  
* **Watch out for:** Przy zapisywaniu na udział sieciowy upewnij się, że aplikacja ma uprawnienia do zapisu; w przeciwnym razie `doc.Save` zgłosi `UnauthorizedAccessException`.  
* **Performance tip:** Ponownie używaj jednej instancji `DocumentBuilder` dla wielu wstawek; tworzenie nowego buildera dla każdej operacji generuje niepotrzebny narzut.

## Zakończenie

Teraz wiesz, jak **create Word document C#**, który zawiera wykres słupkowy, jak **insert chart** elementy, **set label** pozycje oraz **display values** wewnątrz każdego słupka. Pełny przykład kodu powyżej jest gotowy do uruchomienia i możesz go rozszerzyć o własne dane, stylizację lub dodatkowe wykresy.

Następnie odkryj powiązane tematy, takie jak **how to insert picture**, **how to generate tables** lub **how to apply document themes**, aby Twoje automatyczne raporty były jeszcze bogatsze. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i poznać alternatywne podejścia implementacyjne w własnych projektach.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}