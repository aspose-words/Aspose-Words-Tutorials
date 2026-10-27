---
category: general
date: 2026-10-07
description: Dowiedz się, jak stworzyć wykres kołowy w programie Word, dodać serię
  danych i zapisać wykres jako PNG przy użyciu Javy. Postępuj zgodnie z przewodnikiem
  krok po kroku, aby uzyskać szybkie rezultaty.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: pl
lastmod: 2026-10-07
og_description: 'Szybko utwórz wykres kołowy w Wordzie: ten samouczek pokazuje, jak
  dodać serię danych, wygenerować wykres i zapisać wykres Worda jako obraz (PNG).
  Skorzystaj z pełnego przykładu kodu.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Utwórz wykres kołowy w Wordzie i wyeksportuj jako PNG – przewodnik
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Jak stworzyć wykres kołowy w Wordzie i zapisać go jako PNG
url: /pl/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć wykres kołowy w Wordzie i zapisać go jako PNG

Jeśli potrzebujesz **utworzyć wykres kołowy** w pliku Microsoft Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić w Javie. Dowiesz się również, jak **dodać serie danych** do wykresu oraz **zapisać wykres jako PNG**, aby wizualizacja mogła być używana poza Wordem.

Generowanie wykresu bezpośrednio w dokumencie pozwala uniknąć eksportowania danych do osobnego narzędzia graficznego. Po zakończeniu tego samouczka będziesz mieć w pełni funkcjonalny plik Word, który zawiera wykres kołowy oraz odpowiadający mu obraz PNG na dysku.

## Prerequisites

Before you start, make sure you have:

* Java 17 lub nowszy zainstalowany.
* **GroupDocs.Viewer for Java** (lub kompatybilna biblioteka, która udostępnia klasy `Document`, `Chart`, `ChartType` i `ImageSaveOptions`).
* Projekt Maven lub Gradle, w którym możesz dodać zależność biblioteki.
* Dokument Word jako wejście (`input.docx`) znajdujący się w folderze, do którego możesz odwołać się w kodzie.

If you’re using Maven, add the dependency (replace `VERSION` with the latest release):

Jeśli używasz Maven, dodaj zależność (zastąp `VERSION` najnowszą wersją):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Jak utworzyć wykres kołowy w Wordzie

The core of the solution revolves around three actions:

Rdzeń rozwiązania opiera się na trzech działaniach:

1. Załaduj źródłowy plik `.docx`.
2. **Dodaj serie danych** do nowego obiektu `Chart` typu `PIE`.
3. **Zapisz wykres jako PNG**, aby uzyskać plik obrazu obok dokumentu Word.

Below each step is explained in detail, followed by the exact Java code you need.

Poniżej każdy krok jest wyjaśniony szczegółowo, wraz z dokładnym kodem Java, którego potrzebujesz.

### Krok 1: Załaduj dokument źródłowy

You must open the Word file that will host the chart. The `Document` class reads the `.docx` content into memory.

Musisz otworzyć plik Word, w którym zostanie umieszczony wykres. Klasa `Document` odczytuje zawartość `.docx` do pamięci.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Dlaczego to ważne*: Załadowanie dokumentu tworzy mutowalny model. Wszystkie późniejsze operacje na wykresie modyfikują tę reprezentację w pamięci, którą później zapisujesz z powrotem na dysk.

### Krok 2: Dodaj serie danych do wykresu

Creating a **pie chart** starts with a `Chart` instance. The constructor receives the parent `Document` and the chart type (`ChartType.PIE`). After the chart object exists, you populate it with numeric values and optional labels.

Tworzenie **wykresu kołowego** zaczyna się od instancji `Chart`. Konstruktor przyjmuje nadrzędny `Document` oraz typ wykresu (`ChartType.PIE`). Po utworzeniu obiektu wykresu, wypełniasz go wartościami liczbowymi i opcjonalnymi etykietami.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Dlaczego to ważne*: Metoda `add` **dodaje serie danych** do wykresu. Każdy element w `values` staje się kawałkiem koła, natomiast `categories` dostarczają etykiety legendy. Możesz podać dowolną liczbę punktów; biblioteka automatycznie obliczy kąty kawałków.

### Krok 3: Zapisz wykres jako PNG

Once the chart is part of the document, you can export the visual representation. The `save` method on the underlying chart object writes a PNG file to the file system.

Po umieszczeniu wykresu w dokumencie możesz wyeksportować jego wizualną reprezentację. Metoda `save` na obiekcie wykresu zapisuje plik PNG w systemie plików.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Dlaczego to ważne*: Zapisanie wykresu jako PNG daje Ci obraz rastrowy, który może być osadzony w stronach internetowych, e‑mailach lub raportach bez potrzeby posiadania oryginalnego pliku Word. Obiekt `ImageSaveOptions` pozwala kontrolować format, rozdzielczość i inne ustawienia eksportu.

## Generowanie wykresu kołowego w Wordzie – dostosowywanie wyglądu

Beyond the basic steps, you might want to customize colors, titles, or data labels. Most libraries expose a `ChartOptions` or similar object. Here’s a quick example that adds a title and changes the slice colors:

Poza podstawowymi krokami, możesz chcieć dostosować kolory, tytuły lub etykiety danych. Większość bibliotek udostępnia obiekt `ChartOptions` lub podobny. Oto szybki przykład, który dodaje tytuł i zmienia kolory kawałków:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

These customizations are optional but illustrate how you can **generate pie chart in Word** that matches your branding.

Te dostosowania są opcjonalne, ale ilustrują, jak możesz **generować wykres kołowy w Wordzie**, który pasuje do Twojej marki.

## Zapisz wykres Word jako obraz – alternatywne podejścia

If you only need the image and not the chart inside the document, you can skip inserting the chart shape into the Word file and directly call the `save` method after creating the chart. The code remains the same; you simply omit any steps that add the chart to the document’s body.

Jeśli potrzebujesz tylko obrazu, a nie wykresu w dokumencie, możesz pominąć wstawianie kształtu wykresu do pliku Word i bezpośrednio wywołać metodę `save` po utworzeniu wykresu. Kod pozostaje taki sam; po prostu pomijasz kroki, które dodają wykres do treści dokumentu.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

This technique is useful when you generate many charts in a batch process and only care about the PNG output.

Ta technika jest przydatna, gdy generujesz wiele wykresów w procesie wsadowym i zależy Ci jedynie na wyjściu PNG.

## Pełny, działający przykład

Copy the following class into your project, adjust the file paths, and run it. The program will:

Skopiuj poniższą klasę do swojego projektu, dostosuj ścieżki plików i uruchom ją. Program wykona:

1. Załaduje `input.docx`.
2. **Utworzy wykres kołowy**, **doda serie danych** i osadzi go w dokumencie.
3. **Zapisze wykres jako PNG** (`radial.png`).
4. Zapisze zmodyfikowany plik Word jako `output.docx`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Chart;
import com.groupdocs.viewer.ChartType;
import com.groupdocs.viewer.options.ImageSaveOptions;
import com.groupdocs.viewer.options.SaveFormat;

public class PieChartGenerator {

    public static void main(String[] args) {
        // Adjust these paths for your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";


## Co warto nauczyć się dalej?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć wykres słupkowy przy użyciu Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Utwórz wykres punktowy w Wordzie przy użyciu Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Wstaw wykres słupkowy w Wordzie przy użyciu Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}