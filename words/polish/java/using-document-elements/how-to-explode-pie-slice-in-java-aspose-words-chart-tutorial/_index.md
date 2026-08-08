---
category: general
date: 2026-08-07
description: Jak rozdzielić fragment wykresu kołowego w Javie przy użyciu Aspose.Words.
  Dowiedz się, jak dodać linie prowadzące do koła, utworzyć wykres w Wordzie i dostosować
  fragmenty wykresu kołowego.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: pl
lastmod: 2026-08-07
og_description: Jak rozdzielić kawałek wykresu kołowego w Javie przy użyciu Aspose.Words.
  Ten przewodnik pokazuje, jak dodać linie prowadzące do wykresu kołowego, tworzyć
  wykresy w Wordzie oraz dostosować kawałki wykresu kołowego dla wyraźnego efektu
  wizualnego.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Jak rozdzielić wycinek kołowego wykresu w Javie – przewodnik Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Jak odłączyć fragment wykresu kołowego w Javie – samouczek wykresów Aspose.Words
url: /pl/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wyodrębnić kawałek wykresu kołowego w Javie – samouczek wykresów Aspose.Words

Jeśli potrzebujesz wiedzieć **how to explode pie slice** w dokumencie Word przy użyciu Javy, ten samouczek Cię poprowadzi. Pokażemy również **how to add leader lines to pie** charts, **java create word chart** objects oraz **customize pie chart slices** dla uzyskania dopracowanego rezultatu. Po zakończeniu tego przewodnika będziesz mieć kompletny, uruchamialny przykład, który możesz wstawić do dowolnego projektu Java.

![Jak wyodrębnić kawałek wykresu kołowego w Javie – wykres Aspose.Words](/images/pie-chart-exploded.png)

## Wymagania wstępne

* Java Development Kit (JDK) 8 lub nowszy.  
* Maven lub Gradle do zarządzania zależnościami.  
* Licencja Aspose.Words for Java (bezpłatna wersja ewaluacyjna działa w celach edukacyjnych).  
* Podstawowa znajomość składni Javy i koncepcji programowania obiektowego.

> **Pro tip:** Mimo że Aspose.Words oferuje darmową wersję próbną, zakup licencji usuwa znak wodny oceny z wygenerowanych dokumentów.

## Co obejmuje ten samouczek

* Tworzenie nowego dokumentu Word od podstaw.  
* Wstawianie **pie chart** przy użyciu `DocumentBuilder`.  
* **Exploding a pie slice** w celu podkreślenia punktu danych.  
* **Adding leader lines to pie** dla lepszej etykietowania.  
* Dostosowywanie wyglądu kawałków, takich jak kolory i obramowania.  
* Zapisywanie dokumentu na dysku i weryfikacja wyniku.

---

## Jak wyodrębnić kawałek wykresu kołowego przy użyciu Aspose.Words w Javie

Pierwszym krokiem jest skonfigurowanie obiektu wykresu i wyodrębnienie wybranego kawałka. Aspose.Words udostępnia wykres poprzez klasę `Shape`, a każdy kawałek jest `ChartPoint`. Ustawiając właściwość `Explosion`, kontrolujesz, jak daleko kawałek przemieszcza się na zewnątrz.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Dlaczego to działa:**  
`setExplosion(20)` informuje silnik wykresu, aby przesunął kawałek o 20 punktów od środka wykresu. Wartość jest względna; większe liczby tworzą bardziej dramatyczny efekt. Możesz wyodrębnić dowolny kawałek, zmieniając indeks (`get(1)`, `get(2)`, …).

## Dodaj linie prowadzące do wykresu kołowego dla czytelniejszych etykiet

Linie prowadzące łączą etykietę kawałka z jego krawędzią, co jest szczególnie przydatne, gdy kawałki są wyodrębnione lub gdy wykres zawiera wiele małych sekcji. Wywołanie `setLeaderLines(true)` włącza tę funkcję dla całej serii.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Dlaczego potrzebujesz linii prowadzących:**  
Gdy kawałek jest wyodrębniony, domyślna etykieta może nachodzić na inne elementy. Linie prowadzące utrzymują czytelność etykiety, rysując krótką linię od kawałka do pola tekstowego.

## Java create Word chart – wstawianie serii danych

Wykres bez danych nie jest zbyt przydatny. Musisz wypełnić serię kategoriami i wartościami. Poniżej dodajemy trzy kategorie reprezentujące udział w rynku.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Wyjaśnienie:**  
`ChartSeries` przechowuje zarówno kategorie (nazwy kawałków), jak i wartości liczbowe. Włączenie `ShowCategoryName` i `ShowPercentage` sprawia, że wykres jest samowyjaśniający, co dobrze współgra z wcześniej dodanymi liniami prowadzącymi.

## Dostosuj kawałki wykresu kołowego poza wyodrębnianiem

Poza wyodrębnianiem kawałka, często chcesz dostosować kolory, obramowania lub nawet całkowicie ukryć kawałek. Poniższy fragment kodu demonstruje trzy typowe dostosowania:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Dlaczego dostosowywać kawałki:**  
Niestandardowe kolory sprawiają, że wykres pasuje do identyfikacji wizualnej firmy, a obramowania poprawiają czytelność na wydrukowanych stronach. Ukrycie kawałka jest przydatne, gdy chcesz zachować integralność modelu danych, ale tymczasowo pominąć kategorię w wizualnym wyjściu.

## Zapisz dokument i zweryfikuj wynik

Na koniec zapisz dokument na dysku. Możesz otworzyć wygenerowany plik `.docx` w Microsoft Word, LibreOffice lub dowolnym przeglądarce obsługującej ten format.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Oczekiwany wynik:**  
Gdy otworzysz `PieChartDemo.docx`, zobaczysz wykres kołowy, w którym pierwszy kawałek (Product A) jest wyodrębniony na zewnątrz, linie prowadzące wskazują z każdego kawałka na jego etykietę, a kawałki mają niestandardowe kolory zielony, niebieski i pomarańczowy. Ukryty kawałek (Product C) nie będzie widoczny, ale procenty nadal będą sumować się do 100 %, ponieważ dane pozostają w serii wykresu.

---

## Pełny, uruchamialny przykład

Poniżej znajduje się kompletny program, który możesz skopiować, wkleić i uruchomić po dodaniu zależności Aspose.Words do swojego projektu.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Zależność (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć wykres kolumnowy przy użyciu Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Jak załadować dokumenty Word przy użyciu Aspose.Words Java: Kompletny przewodnik](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Jak utworzyć pola formularza i dodać treść przy użyciu DocumentBuilder w Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}