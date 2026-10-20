---
category: general
date: 2026-10-20
description: Utwórz wykres kołowy w dokumencie Word przy użyciu Aspose.Words – przewodnik
  krok po kroku, który pokazuje, jak ustawić kolor, oddzielić wycinek i zapisać dokument
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: pl
lastmod: 2026-10-20
og_description: Utwórz wykres kołowy w dokumencie Word przy użyciu Aspose.Words. Dowiedz
  się, jak ustawić kolor, wydzielić fragment i zapisać dokument Word w jednym, gotowym
  do uruchomienia przykładzie.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Tworzenie wykresu kołowego w dokumencie Word – pełny przewodnik C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Jak utworzyć wykres kołowy w dokumencie Word przy użyciu Aspose.Words
url: /pl/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć wykres kołowy w dokumencie Word przy użyciu Aspose.Words

Jeśli potrzebujesz **utworzyć wykres kołowy** w pliku Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz, jak ustawić niestandardowy kolor, wyodrębnić fragment wykresu dla podkreślenia oraz w końcu **zapisać dokument Word** z osadzonym wykresem.

Generowanie wykresów programowo eliminuje ręczne kroki otwierania Worda, wstawiania wykresu i dostosowywania jego wyglądu. Po zakończeniu tego samouczka będziesz mieć kompletną, działającą aplikację konsolową C#, która tworzy wykres kołowy, dostosowuje go i zapisuje wynik na dysku.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz:

* .NET 6.0 SDK lub nowszy zainstalowany  
* Ważną licencję Aspose.Words for .NET (lub darmowy klucz ewaluacyjny)  
* IDE, takie jak Visual Studio 2022 lub VS Code  

Nie są wymagane dodatkowe pakiety NuGet poza `Aspose.Words`.

## Jak utworzyć wykres kołowy w dokumencie Word

Pierwszym krokiem jest utworzenie obiektu `Document` oraz `DocumentBuilder`. Builder zapewnia dostęp do wysokopoziomowych funkcji Worda, w tym wstawiania wykresów.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

W tym momencie dokument już zawiera podstawowy wykres kołowy. Następne sekcje wyjaśniają **jak wyodrębnić fragment**, **jak ustawić kolor** oraz **jak zapisać dokument Word**.

## Jak wyodrębnić fragment wykresu dla podkreślenia

Wyodrębnienie fragmentu oddziela go od reszty koła, przyciągając wzrok czytelnika. API Aspose.Words pozwala określić odległość wyodrębnienia w punktach.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Dlaczego wyodrębnia się fragment? W raportach podkreślających określoną kategorię — np. „Najlepiej sprzedający się produkt” — wizualne oddzielenie sprawia, że punkt danych jest od razu rozpoznawalny.

## Jak ustawić kolor fragmentu wykresu

Niestandardowe kolory poprawiają spójność marki i czytelność. Możesz przypisać dowolny `System.Drawing.Color` do konkretnego punktu danych.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Nie jesteś ograniczony do predefiniowanych kolorów; możesz utworzyć wartość `Color.FromArgb` dla precyzyjnych odcieni.

## Jak zapisać dokument Word z wykresem

Gdy wykres wygląda tak, jak chcesz, zapisanie pliku jest proste. Metoda `Document.Save` zapisuje dokument w wybranym formacie — tutaj używamy domyślnego `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Uruchomienie programu tworzy plik `PieChart.docx`. Otworzenie go w Microsoft Word pokazuje wykres kołowy, w którym pierwszy fragment jest wyodrębniony i pokolorowany na czerwono, dokładnie tak jak określono w kodzie.

### Oczekiwany rezultat

* Plik Word o nazwie **PieChart.docx** w `C:\Temp`.  
* Dokument zawiera pojedynczy wykres kołowy, o wymiarach 400 × 300 punktów.  
* Fragment 0 jest przesunięty o 20 punktów i wypełniony na czerwono, podczas gdy pozostałe fragmenty zachowują domyślny kolor.  

Możesz zweryfikować wyodrębnienie i kolor, zaznaczając wykres w Wordzie i sprawdzając właściwości fragmentu.

## Porady i typowe pułapki

* **Porada:** Jeśli musisz zmienić tytuł wykresu lub legendę, użyj właściwości `pieChart.Title.Text` oraz `pieChart.Legend` przed zapisem.  
* **Uwaga:** Zapomnienie o wyczyszczeniu domyślnych punktów danych może prowadzić do dodatkowych, niechcianych fragmentów. Zawsze wywołuj `Series[0].DataPoints.Clear()` przed dodaniem własnych danych.  
* **Wskazówka dotycząca wydajności:** Dla dużych dokumentów, używaj jednego egzemplarza `DocumentBuilder` zamiast tworzyć wiele builderów; zmniejsza to zużycie pamięci.

## Jak utworzyć wykres przy użyciu Aspose.Words (dodatkowy kontekst)

Metoda `InsertChart` obsługuje wiele typów wykresów oprócz wykresów kołowych, takich jak kolumnowe, liniowe i obszarowe. Aby przełączyć się na inny typ, zamień `ChartType.Pie` na żądaną wartość wyliczeniową, np. `ChartType.Column`. Reszta kroków dostosowywania (wyodrębnianie fragmentów, ustawianie kolorów) przebiega tak samo, choć nie wszystkie typy wykresów udostępniają właściwość „explosion”.

## Jak wyodrębnić fragment w innych typach wykresów

Tylko wykresy typu kołowego udostępniają metodę `SetExplosion`. Jeśli spróbujesz wywołać ją na wykresie słupkowym, API zgłosi `ArgumentException`. W takich przypadkach rozważ użycie etykiet danych lub dymków, aby podkreślić konkretny słupek.

## Jak ustawić kolor serii zamiast pojedynczego fragmentu

Jeśli chcesz, aby wszystkie fragmenty w serii miały ten sam kolor, przeiteruj po punktach danych:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

To podejście jest przydatne, gdy potrzebujesz jednolitej palety kolorów w wielu wykresach.

## Jak zapisać dokument Word w innych formatach

Aspose.Words może eksportować do PDF, HTML i wielu innych formatów. Zmień rozszerzenie pliku w metodzie `Save` i opcjonalnie przekaż obiekt `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Silnik renderujący wykres automatycznie konwertuje wykres do docelowego formatu, zachowując kolory i ustawienia wyodrębnienia.

## Zakończenie

Teraz wiesz, jak **utworzyć wykres kołowy** w dokumencie Word, dostosować jego wygląd przez **wyodrębnienie fragmentu** i **ustawienie koloru**, a na końcu **zapisać dokument Word** z osadzonym wykresem. Ten kompleksowy przykład daje solidne podstawy do automatyzacji generowania raportów, pulpitów nawigacyjnych lub dowolnych scenariuszy, w których dane wizualne muszą być wstawiane programowo.

### Kolejne kroki

* Poznaj inne typy wykresów (`ChartType.Column`, `ChartType.Line`), aby poszerzyć swoje możliwości raportowania.  
* Połącz wiele wykresów w jednym dokumencie, aby zbudować kompleksowe pulpity nawigacyjne.  
* Eksperymentuj z `ChartDataLabel`, aby wyświetlać procenty lub wartości bezpośrednio na fragmentach.  

Śmiało dostosuj kod do własnych źródeł danych — niezależnie od tego, czy pobierasz wartości z bazy danych, API, czy pliku CSV, ten sam przepływ pracy Aspose.Words ma zastosowanie. Szczęśliwego wykreślania!


## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, pomagając Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}