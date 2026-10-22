---
category: general
date: 2026-10-13
description: Przykład wykresu radialnego w Aspose.Words, który pokazuje, jak włączyć
  podziały na wykresie radialnym przy użyciu C# i Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: pl
lastmod: 2026-10-13
og_description: Przykład wykresu radialnego Aspose.Words, który demonstruje włączanie
  podziałek na wykresie radialnym przy użyciu C# oraz najnowszej biblioteki 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Przykład wykresu radialnego Aspose.Words – włącz podziały w C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Przykład wykresu radialnego Aspose.Words: włącz podziały w C#'
url: /pl/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Przykład wykresu radialnego Aspose.Words: włączenie podziałek w C#

Jeśli szukasz **aspose.words radial chart example**, trafiłeś we właściwe miejsce. Ten tutorial prowadzi cię krok po kroku przez dokładne czynności włączenia podziałek dla wykresu radialnego przy użyciu API Aspose.Words dla .NET.

Wykresy radialne są przydatne do wizualizacji danych cyklicznych, takich jak metryki w ciągu dnia czy trendy sezonowe. Domyślnie podziałki (znaczniki na okrągłej osi) są ukryte, co może utrudniać odczyt wykresu. Włączenie ich wymaga jedynie jednej linii kodu, ale trzeba znać właściwy model obiektowy oraz wersję, która obsługuje tę funkcję.

W tym przewodniku dowiesz się, jak:

* Załadować dokument Word, który już zawiera wykres radialny.  
* Uzyskać dostęp do kształtu wykresu za pośrednictwem API wykresów Aspose.Words.  
* Włączyć **widoczność podziałek** (dostępne od **Aspose.Words version 24.9**).  
* Zapisz zmodyfikowany dokument i zweryfikuj wynik.

Pełny, uruchamialny kod jest dołączony, więc możesz go skopiować i wkleić do nowego projektu konsolowego i od razu zobaczyć efekt.

![Przykład wykresu radialnego Aspose.Words z podziałkami](https://example.com/images/radial-chart-graduations.png "Przykład wykresu radialnego Aspose.Words pokazujący włączone podziałki")

## Wymagania wstępne

Zanim rozpoczniesz, upewnij się, że masz:

| Wymaganie | Dlaczego jest ważne |
|-------------|----------------|
| .NET 6.0 lub nowszy | Aspose.Words for .NET 24.9+ celuje w .NET Standard 2.0 i działa na .NET 6+. |
| Aspose.Words for .NET **24.9** lub nowszy | Właściwość `IsGraduationsVisible` została wprowadzona w wersji 24.9. Starsze wydania spowodują `MissingMemberException`. |
| Dokument Word (`RadialChart.docx`) zawierający wykres radialny | Przykład modyfikuje istniejący wykres; tworzenie go od podstaw to osobny temat. |
| IDE C# (Visual Studio, Rider, VS Code) | Dowolne IDE, które potrafi kompilować projekty .NET, będzie działać. |
| Pakiet NuGet `Aspose.Words` | Zainstaluj za pomocą `dotnet add package Aspose.Words --version 24.9.0` (lub nowszej). |

> **Pro tip:** Jeśli nie możesz zaktualizować do wersji 24.9, nadal możesz modyfikować inne właściwości wykresu, ale podziałki pozostaną ukryte, ponieważ API nie udostępnia tego flagi.

## Przykład wykresu radialnego Aspose.Words – przewodnik krok po kroku

Poniższe sekcje dzielą proces na odrębne, łatwe do śledzenia kroki. Każdy krok zawiera dokładny kod, którego potrzebujesz, oraz krótkie wyjaśnienie, *dlaczego* dany krok istnieje.

### Krok 1: Załaduj dokument zawierający wykres radialny

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Dlaczego to ważne:**  
`Document` jest punktem wejścia **Aspose.Words chart API**. Ładuje plik DOCX do pamięci, dając dostęp do każdego węzła — akapitów, tabel i kształtów wykresów. Jeśli plik nie zostanie znaleziony, `Document` zgłosi `FileNotFoundException`, co powinno być obsłużone w kodzie produkcyjnym.

### Krok 2: Pobierz pierwszy kształt wykresu z dokumentu

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Dlaczego to ważne:**  
Wykresy są przechowywane jako węzły `Shape`. Metoda `GetChild` z parametrem `NodeType.Shape` przeszukuje DOM i zwraca pierwszy pasujący kształt. Rzutowanie na `Chart` daje dostęp do właściwości specyficznych dla wykresu, takich jak `RadialChart`. Sprawdzenie na `null` zapewnia czytelny błąd, jeśli dokument nie zawiera wykresu — częsty przypadek przy ponownym używaniu szablonów.

### Krok 3: Włącz podziałki na wykresie radialnym

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Dlaczego to ważne:**  
`IsGraduationsVisible` kontroluje znaczniki na okrągłej osi. Gdy ustawione na `true`, wykres renderuje podziałki, zwiększając czytelność dla odbiorców, którzy potrzebują precyzyjnie ocenić wartości. Właściwość znajduje się pod `RadialChart`, które jest podtypem `Chart`. Jeśli spróbujesz tego na wykresie nie‑radialnym (np. słupkowym), właściwość `RadialChart` będzie `null`, więc w bardziej złożonych scenariuszach należy najpierw zweryfikować typ wykresu.

#### Obsługa wykresów nie‑radialnych (opcjonalnie)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Ten warunek sprawia, że kod jest odporny, gdy źródłowy dokument może zawierać różne typy wykresów.

### Krok 4: Zapisz zmodyfikowany dokument

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Dlaczego to ważne:**  
Wywołanie `Save` zapisuje DOM w pamięci z powrotem do pliku .docx, utrwalając wprowadzone zmiany w wykresie. Plik wyjściowy można otworzyć w Microsoft Word, LibreOffice lub dowolnym przeglądarku obsługującym DOCX. Zobaczysz wykres radialny z widocznymi podziałkami.

## Pełny, uruchamialny przykład

Poniżej znajduje się kompletny program, który możesz wkleić do pliku `Program.cs` projektu konsolowego .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Oczekiwany wynik

Po otwarciu `RadialChart_Graduations.docx` w Wordzie, wykres radialny wyświetli znaczniki (podziałki) wokół okrągłej osi, podobnie jak na zrzucie ekranu pokazanym wcześniej. Reszta wykresu (serie danych, legenda, tytuł) pozostaje niezmieniona.

## Typowe wariacje i przypadki brzegowe

| Sytuacja | Rozwiązanie |
|-----------|----------|
| **Starsza wersja Aspose.Words (< 24.9)** | Zaktualizuj do najnowszego pakietu NuGet. Właściwość `IsGraduationsVisible` nie istnieje w wcześniejszych wydaniach. |
| **Wiele wykresów w tym samym dokumencie** | Użyj `doc.GetChild(NodeType.Shape, index, true)` z odpowiednim `index` lub iteruj po `doc.GetChildNodes(NodeType.Shape, true)` i filtruj po `ChartType.Radial`. |
| **Wykres tworzony programowo** | Użyj `DocumentBuilder` do wstawienia wykresu, a następnie ustaw `RadialChart.IsGraduationsVisible` na |

## Co powinieneś się nauczyć dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Aktualizuj dane serii wykresu w dokumencie Word przy użyciu Aspose.Words dla .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Usuń serię wykresu z dokumentu Word przy użyciu Aspose.Words dla .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Ukryj obramowanie obszaru wykresu w wykresie kolumnowym przy użyciu Aspose.Words dla .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}