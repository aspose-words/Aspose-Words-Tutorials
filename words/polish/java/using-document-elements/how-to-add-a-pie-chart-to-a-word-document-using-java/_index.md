---
category: general
date: 2026-11-15
description: Dowiedz się, jak dodać wykres kołowy do dokumentu Word przy użyciu Aspose.Words
  for Java. Zawiera konwersję na wykres pierścieniowy, wyodrębniony fragment oraz
  pełny przykład kodu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: pl
lastmod: 2026-11-15
og_description: Dodaj wykres kołowy do dokumentu Word przy użyciu Aspose.Words for
  Java. Ten samouczek pokazuje, jak wydzielić fragment wykresu i przekształcić go
  w wykres pierścieniowy.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Dodaj wykres kołowy do dokumentu Word przy użyciu Javy – przewodnik krok
  po kroku
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Jak dodać wykres kołowy do dokumentu Word przy użyciu Javy
url: /pl/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dodaj wykres kołowy do dokumentu Word – kompletny przewodnik Java

Jeśli potrzebujesz **dodać wykres kołowy do dokumentu Word** programowo, ten tutorial pokazuje dokładnie, jak to zrobić przy użyciu Aspose.Words for Java. Zobaczysz pełny przepływ pracy: wczytywanie pliku DOCX, tworzenie wykresu kołowego, „wybuchanie” pierwszego kawałka oraz konwersję wykresu w pierścień poprzez ustawienie rozmiaru otworu.

Poradnik obejmuje także typowe warianty — takie jak dodawanie wielu serii, dostosowywanie kolorów oraz obsługa dokumentów, które już zawierają wykresy — abyś mógł dostosować kod do rzeczywistych projektów, takich jak automatyczne raportowanie czy dynamiczne prezentacje.

## Wymagania wstępne

* Java 17 lub nowszy (kod kompiluje się również z JDK 11+)
* Maven 3.6+ lub Gradle do zarządzania zależnościami
* Licencja Aspose.Words for Java (bezpłatna wersja próbna działa do testów)
* Podstawowa znajomość składni Java i struktury projektu Maven

## Krok 1: Skonfiguruj projekt Maven i zaimportuj Aspose.Words

Utwórz nowy projekt Maven (lub dodaj do istniejącego) i uwzględnij zależność Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Wskazówka:** Jeśli używasz Gradle, równoważny wpis to `implementation 'com.aspose:aspose-words:24.9'`.

Zależność dostarcza klasy `Document`, `Chart` i `ChartType`, które będą potrzebne do manipulacji wykresami.

## Krok 2: Wczytaj docelowy dokument

Możesz rozpocząć od istniejącego pliku `.docx` lub utworzyć nowy pusty dokument. Poniższy przykład wczytuje szablon o nazwie `input.docx` znajdujący się w folderze `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Jeśli plik nie istnieje, Aspose.Words automatycznie utworzy nowy pusty dokument po wywołaniu `new Document()` bez podania nazwy pliku.

## Krok 3: Utwórz wykres kołowy i wstaw go do dokumentu

Aspose.Words traktuje wykres jako kształt, który może być umieszczony w dowolnym miejscu, gdzie może wystąpić akapit. Poniższy kod tworzy **wykres kołowy**, dodaje jedną serię danych i wstawia wykres po pierwszym akapicie.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Dlaczego ten krok jest ważny:**  
* `ChartType.PIE` instruuje Aspose.Words, aby renderował tradycyjny wykres kołowy.  
* Dodanie serii z etykietami kategorii i wartościami liczbowymi automatycznie wypełnia kawałki.  
* Wstawienie wykresu jako dziecka `Paragraph` zachowuje spójny przepływ dokumentu.

## Krok 4: „Wybuch” pierwszego kawałka, aby go wyróżnić

*Wybuchnięty kawałek* przyciąga uwagę do konkretnego punktu danych. API udostępnia metodę `setExplode(boolean)` w obiekcie `ChartSeries`. Ustawienie jej dla pierwszej serii (indeks 0) powoduje, że pierwszy kawałek wyłania się.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Częste pytanie:** *Co jeśli mam wiele serii?*  
> Możesz wybrać konkretną serię według jej indeksu, np. `pieChart.getSeries().get(1).setExplode(true)` dla drugiej serii.

## Krok 5: Przekształć wykres kołowy w pierścień, ustawiając rozmiar otworu

Wykres pierścieniowy to w zasadzie wykres kołowy z pustym środkiem. Aspose.Words pozwala określić rozmiar otworu jako procent promienia wykresu.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

Metoda `setHoleSize` przyjmuje wartości od **0** (zwykły wykres kołowy) do **100** (całkowicie pusty). Wartość w okolicach **30‑40** daje wizualnie zrównoważony pierścień.

## Krok 6: Zapisz i zweryfikuj wynik

Po wszystkich modyfikacjach zapisz dokument. Poniższa linia zapisuje plik do folderu `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Oczekiwany wynik

Otwórz `final-pie-doughnut.docx` w programie Microsoft Word:

* W miejscu pierwszego akapitu pojawia się wykres pierścieniowy.
* Kawałek „Apples” jest wybuchnięty (nieco oddzielony od pozostałych).
* Wykres pokazuje cztery kawałki oznaczone *Apples*, *Bananas*, *Cherries*, *Dates* wraz z podanymi procentami.

Jeśli wolisz wyjście w formacie PDF, zmień `SaveFormat` na `SaveFormat.PDF`.

## Obsługa przypadków brzegowych i wariantów

### Dodawanie wielu serii

Jeśli potrzebujesz kilku serii (np. pierścień warstwowy), dodaj je kolejno:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Niestandardowe kolory

Możesz przypisać kolor do każdego kawałka za pomocą `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Praca z istniejącym wykresem

Jeśli dokument już zawiera wykres i chcesz go jedynie zmodyfikować, znajdź kształt wykresu:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Obsługa licencji

Aspose.Words wymaga licencji do użytku produkcyjnego. Umieść plik `Aspose.Words.lic` w classpath i załaduj go przy starcie aplikacji:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Brak ustawionej licencji spowoduje dodanie znaku wodnego do wygenerowanego dokumentu.

## Pełny, uruchamialny przykład

Poniżej znajduje się pełna klasa Java, która zawiera wszystkie omówione kroki. Skopiuj ją do `src/main/java/com/example/AddPieChart.java` i uruchom `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Uruchomienie programu generuje wykres pierścieniowy opisany wcześniej. Dostosuj `categories`, `values` lub `holeSize` do swoich danych.

## Podsumowanie

Teraz wiesz, jak **dodać wykres kołowy do dokumentu Word** przy użyciu Javy i Aspose.Words. Poradnik obejmował wczytywanie dokumentu, tworzenie wykresu kołowego, wybuchanie kawałka, przekształcanie wykresu w pierścień oraz obsługę typowych wariantów, takich jak wiele serii, niestandardowe kolory i istniejące wykresy. Dzięki tej bazie możesz budować narzędzia do automatycznego raportowania, generować dynamiczne prezentacje lub osadzać bogate wizualizacje bezpośrednio w plikach Word.

### Co warto zbadać dalej

* **add bar chart to Word document** – podobne kroki, ale użyj `ChartType.BAR`.
* **customize chart legends and titles** – użyj `pieChart.getTitle().setText("...")` i `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.
* **export the Word document as PDF** – zmień `SaveFormat` na `PDF` dla plików gotowych do dystrybucji.
* **populate chart data from a database** – zamień statyczne tablice na wyniki zapytań JDBC.

Śmiało eksperymentuj z różnymi typami wykresów, źródłami danych i opcjami stylizacji. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak wybuchnąć kawałek kołowy w Javie – tutorial wykresów Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Utwórz wykres kołowy z Aspose.Words Java – pełny przewodnik krok po kroku](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}