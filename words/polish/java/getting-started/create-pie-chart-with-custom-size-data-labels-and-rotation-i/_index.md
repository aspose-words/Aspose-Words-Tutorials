---
category: general
date: 2026-11-22
description: Utwórz wykres kołowy w Javie i dowiedz się, jak ustawić rozmiar wykresu,
  dodać etykiety danych, wyświetlić procenty oraz obrócić pierwszy segment, aby uzyskać
  wyraźny efekt wizualny.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: pl
lastmod: 2026-11-22
og_description: Utwórz wykres kołowy w Javie, następnie ustaw rozmiar wykresu, pokaż
  procenty na etykietach danych i obróć pierwszy segment — wszystko w jednym, gotowym
  do uruchomienia przykładzie.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Utwórz wykres kołowy o niestandardowym rozmiarze, etykietach i obrocie w
  Javie
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Utwórz wykres kołowy o niestandardowym rozmiarze, etykietach danych i obrocie
  w Javie
url: /pl/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz wykres kołowy o niestandardowym rozmiarze, etykietach danych i obrocie w Javie

Jeśli potrzebujesz **create pie chart** w Javie, ten przewodnik przeprowadzi Cię przez cały proces. Dowiesz się, jak **set chart size**, włączyć **show percentages pie chart**, dodać **data labels pie chart** oraz **rotate pie chart slice**, tak aby pierwszy segment zaczynał się pod kątem 45 stopni.

Przykład wykorzystuje **Aspose.Slides for Java**, szeroko używaną bibliotekę do manipulacji plikami PowerPoint. Te same koncepcje mają zastosowanie do innych bibliotek wykresów; wystarczy zamienić wywołania API na ich odpowiedniki w używanym zestawie narzędzi.

## Wymagania wstępne

* Java 17 lub nowszy zainstalowany  
* Maven 3.8+ (lub Gradle) do zarządzania zależnościami  
* Podstawowa znajomość składni Java  
* Dostęp do pliku binarnego Aspose.Slides for Java (można uzyskać darmową wersję próbną na oficjalnej stronie)

Dodaj zależność do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Utwórz wykres kołowy – pełny przykład

Poniższy program tworzy slajd PowerPoint, który zawiera wykres kołowy o niestandardowym rozmiarze, etykietach danych w procentach oraz obróconym pierwszym segmentem.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Dlaczego każdy krok ma znaczenie

| Krok | Cel | Jak odnosi się do słów kluczowych |
|------|-----|-----------------------------------|
| **Insert chart** | **Create pie chart** – podstawowy obiekt, który renderuje wizualizację. | Bezpośrednio spełnia wymaganie *create pie chart*. |
| **Set dimensions** | Wywołanie `addChart(..., 400, 300)` demonstruje **set chart size**. | Kontroluje szerokość (400 px) i wysokość (300 px). |
| **Show percentages** | `setShowPercentage(true)` sprawia, że wykres **show percentages pie chart** na każdym segmencie. | Użytkownicy często potrzebują procentów zamiast surowych wartości. |
| **Add data labels** | Konfiguracja `DataLabelFormat` dodaje **data labels pie chart** z żądaną widocznością. | Etykiety poprawiają czytelność i są konfigurowalne. |
| **Rotate slice** | `setFirstSliceAngle(45)` obraca wykres tak, aby pierwszy segment zaczynał się pod kątem 45 stopni, spełniając **rotate pie chart slice**. | Poprawia wizualne podkreślenie konkretnego segmentu. |

## Szczegółowy podział krok po kroku

### 1. Wstaw wykres kołowy i ustaw rozmiar wykresu

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*Metoda `addChart` tworzy wykres i jednocześnie **set chart size** na 400 × 300 punktów.*  
Jeśli potrzebujesz innego rozmiaru, zmodyfikuj ostatnie dwa argumenty.

### 2. Wypełnij wykres danymi

Demo dodaje trzy kategorie i jedną serię. Zastąp sztywno zakodowane liczby danymi z bazy danych, pliku CSV lub wejścia użytkownika w razie potrzeby.

### 3. Pokaż procenty na każdym segmencie

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Włączenie `setShowPercentage(true)` zapewnia, że wykres **show percentages pie chart** automatycznie oblicza udział każdego segmentu w całości.*

### 4. Dodaj szczegółowe etykiety danych

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Możesz przełączać inne opcje etykiet (`setShowValue`, `setShowSeriesName` itp.), aby dostosować doświadczenie **add data labels pie chart**.

### 5. Obróć pierwszy segment

```java
chart.setFirstSliceAngle(45);
```

*Wywołanie `setFirstSliceAngle(45)` **rotate pie chart slice**, dzięki czemu pierwszy segment zaczyna się pod kątem 45 stopni, wyróżniając go.*

### 6. Zapisz i zobacz wynik

Uruchomienie programu generuje `output/PieChartDemo.pptx`. Otwórz go w PowerPoint lub dowolnym kompatybilnym przeglądarce, aby zobaczyć końcowy wykres kołowy:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Zrzut ekranu utworzonego wykresu kołowego o niestandardowym rozmiarze, etykietach procentowych i obróconym pierwszym segmencie"}

Powyższy obrazek demonstruje rezultat **create pie chart**, potwierdzając, że rozmiar, etykiety, procenty i obrót zostały zastosowane prawidłowo.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Dostosowanie |
|----------|--------------|
| **Different chart dimensions** | Zmień parametry szerokości/wysokości w `addChart`. |
| **Multiple series** | Dodaj dodatkowe obiekty `IChartSeries`; każda seria może mieć własne ustawienia etykiet. |
| **Custom label format** | Użyj `series.getDataLabelFormat().setNumberFormat("0.0%")`, aby kontrolować liczbę miejsc po przecinku. |
| **Rotating to another angle** | Podaj dowolną liczbę całkowitą (0‑360) do `setFirstSliceAngle`. |
| **Export as image** | Po zapisaniu wywołaj `chart.writeAsSvg(outPath)` lub `chart.writeAsPng(outPath)`, aby uzyskać wersję rastrową. |

> **Pro tip:** Jeśli planujesz generować wiele wykresów w pętli, ponownie użyj tego samego obiektu `Presentation` i zamieniaj tylko dane wykresu. Redukuje to zużycie pamięci i przyspiesza przetwarzanie.

## Podsumowanie

Teraz wiesz, jak **create pie chart** w Javie, **set chart size**, włączyć **show percentages pie chart**, **add data labels pie chart** oraz **rotate pie chart slice** dla lepszego podkreślenia wizualnego. Pełny, działający przykład demonstruje każdy krok od inicjalizacji po zapisanie ostatecznego pliku PowerPoint.

### Co dalej?

* Zbadaj inne typy wykresów (Bar, Line, Area) używając tego samego wyliczenia `ChartType`.  
* Połącz wiele wykresów na jednym slajdzie, tworząc pulpity nawigacyjne.  
* Eksportuj wykresy do PNG lub SVG do użycia w aplikacjach internetowych.  

Śmiało eksperymentuj z kolorami, legendami i efektami animacji — Twoje wizualizacje danych są ograniczone jedynie wyobraźnią. Szczęśliwego tworzenia wykresów!

## Co powinieneś się nauczyć dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [jak wstawić wykres kołowy w Word – dodać etykietę procentową](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Jak rozdzielić segment wykresu kołowego w Javie – samouczek wykresu Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Wstaw wykres kołowy w Javie – rozdziel, obróć i podświetl segmenty](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}