---
category: general
date: 2026-09-08
description: Utwórz pusty dokument Word i dodaj wykres do Worda przy użyciu Aspose.Words.
  Dowiedz się, jak wstawić wykres radarowy, włączyć podziały i zapisać plik.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: pl
lastmod: 2026-09-08
og_description: Utwórz pusty dokument Word i dodaj wykres do Worda przy użyciu Aspose.Words.
  Ten samouczek pokazuje, jak wstawić wykres radarowy, skonfigurować osie i zapisać
  dokument.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Utwórz pusty dokument Word i dodaj wykres radarowy – przewodnik krok po
  kroku
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Jak utworzyć pusty dokument Word i dodać wykres do Worda
url: /pl/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć pusty dokument Word i dodać wykres do Word

Jeśli potrzebujesz **utworzyć pusty dokument Word** do raportu, szablonu lub automatycznej korespondencji seryjnej, ten przewodnik przeprowadzi Cię przez cały proces przy użyciu C# i Aspose.Words. Dowiesz się także, jak **dodać wykres do Word**, konkretnie **wstawić wykres radarowy**, włączyć podziały i zapisać wynik jako plik .docx.

Ten tutorial obejmuje wszystko, od konfiguracji projektu po końcowy krok weryfikacji. Po jego zakończeniu będziesz mieć wielokrotnie używany fragment kodu, który można wstawić do dowolnej aplikacji .NET. Nie wymagana jest wcześniejsza znajomość Aspose.Words, ale powinieneś mieć podstawową wiedzę o C# oraz zainstalowany aktualny .NET SDK.

## Wymagania wstępne

- .NET 6.0 SDK lub nowszy  
- Aspose.Words for .NET (pakiet NuGet `Aspose.Words`)  
- IDE, np. Visual Studio 2022 lub VS Code  
- Uprawnienia do zapisu w folderze, w którym dokument zostanie zapisany  

Możesz zainstalować bibliotekę przy użyciu następującego polecenia:

```bash
dotnet add package Aspose.Words
```

## Krok 1: Utwórz pusty dokument Word

Pierwszym krokiem jest **utworzenie pustego dokumentu Word** w pamięci. Klasa `Document` reprezentuje cały plik, natomiast `DocumentBuilder` udostępnia płynne API do dodawania zawartości.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` rozpoczyna się pusty, więc masz czyste płótno, na którym możesz umieścić wykres. Utrzymanie dokumentu w stanie pustym na tym etapie ułatwia ponowne użycie tego samego kodu dla różnych szablonów.

## Krok 2: Dodaj wykres do Word

Następnie **dodajemy wykres do Word** wywołując `InsertChart`. Metoda wymaga określenia typu wykresu oraz żądanych wymiarów w punktach (1 punkt = 1/72 cala).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` instruuje Aspose.Words, aby wygenerował wykres radialny, co jest idealne do prezentacji danych wielowymiarowych w układzie kołowym. Wartości rozmiaru (400 × 300) dobrze sprawdzają się w większości stron w orientacji pionowej, ale możesz je dostosować do własnego układu.

## Krok 3: Wstaw wykres radarowy i skonfiguruj podziały

Teraz **wstawiamy wykres radarowy** i włączamy podziały (znaczniki) na obu osiach: kategorii (X) i wartości (Y). Podziały zwiększają czytelność, pokazując dokładne pozycje każdego punktu danych.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Ustawienie `HasGraduations` na `true` rysuje znaczniki na osiach. Opcjonalny parametr `GraduationStep` kontroluje odstęp między znacznikami na osi radialnej; krok 10 oznacza znacznik co 10 stopni.

### Wskazówka
Jeśli potrzebujesz wyświetlić etykiety danych, wywołaj `radarChart.Series[0].HasDataLabel = true;`. Dodaje to wartość liczbową obok każdego punktu, co jest przydatne w prezentacjach.

## Krok 4: Wypełnij wykres przykładowymi danymi (opcjonalnie)

Wykres radarowy bez danych jest niewidoczny. Poniżej znajduje się szybki sposób na dodanie serii przykładowych wartości. Możesz zamienić ten blok na własne źródło danych.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Każde wywołanie `Add` wstawia punkt do serii. Kolejność punktów odpowiada pozycjom kątowym wokół koła.

## Krok 5: Zapisz dokument zawierający wykres

Na koniec zapisz dokument na dysku. Metoda `Save` automatycznie zapisuje plik .docx, zachowując wykres i całe formatowanie.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Uruchomienie programu tworzy **pusty dokument Word**, który teraz zawiera w pełni funkcjonalny wykres radarowy. Otwórz plik w Microsoft Word, aby zobaczyć rezultat.

![Wykres radarowy w dokumencie Word](radar_chart.png){alt="Wykres radarowy wstawiony do pustego dokumentu Word"}

## Typowe warianty i przypadki brzegowe

| Sytuacja | Co zmienić |
|-----------|----------------|
| **Inny rozmiar wykresu** | Dostosuj parametry szerokości/wysokości w `InsertChart`. |
| **Inne typy wykresów** | Zastąp `ChartType.Radar` przez `ChartType.Column`, `ChartType.Pie` itp., zachowując tę samą logikę podziałów. |
| **Zapisywanie do strumienia** | Użyj `document.Save(Stream, SaveFormat.Docx)` |

## Co powinieneś się nauczyć dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Wstaw wykres obszarowy w dokumencie Word | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Utwórz wykres punktowy Word przy użyciu Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Wstaw wykres kolumnowy w Word przy użyciu Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}