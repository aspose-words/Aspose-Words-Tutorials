---
category: general
date: 2026-07-20
description: jak wstawić wykres kołowy w Wordzie przy użyciu Aspose.Words. Dowiedz
  się, jak dodać etykiety danych z procentami i wyświetlać procenty na wykresie w
  profesjonalnych dokumentach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: pl
lastmod: 2026-07-20
og_description: Jak wstawić wykres kołowy w Wordzie przy użyciu Aspose.Words. Ten
  przewodnik pokazuje, jak dodać etykiety danych z procentami i wyświetlić procenty
  na wykresie w kilku prostych linijkach.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: jak wstawić wykres kołowy w Wordzie – szybki przewodnik
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Jak wstawić wykres kołowy w Word – dodać etykietę danych z procentem
url: /pl/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak wstawić wykres kołowy w Word – dodać etykietę danych procentowych

Ever wondered **how to insert pie chart** into a Word document without wrestling with the UI? You’re not alone. In many reporting scenarios you need to *add pie chart to Word* and, more importantly, **show percent on pie chart** so readers instantly grasp the data distribution.

In this tutorial we’ll walk through the complete process using Aspose.Words for Java. By the end you’ll know exactly how to **add data label percent**, **display percentages on chart**, and get a polished pie chart that looks right the first time. No extra plugins, no manual tweaks—just clean code you can drop into any project.

---

## Wymagania wstępne

- Java 17 (lub nowsza) – aktualna wersja LTS wspierana przez Aspose.Words.
- Aspose.Words for Java 24.x (najnowsza w momencie pisania, lipiec 2026).
- Podstawowa konfiguracja Maven lub Gradle do pobrania biblioteki.
- Ulubione IDE (IntelliJ IDEA, Eclipse, VS Code… dowolne).

If you already have these, great—let’s dive in.

## Krok 1: Skonfiguruj projekt i zaimportuj bibliotekę

First, add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). This gives you access to the `Document`, `DocumentBuilder`, and chart classes.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Utrzymuj numer wersji aktualny; nowsze wydania często dodają poprawki związane z wykresami, które sprawiają, że **display percentages on chart** jest bardziej niezawodne.

## Krok 2: Utwórz nowy dokument Word i buildera

The builder is your Swiss‑army knife for inserting content. Here we create a fresh document and attach a `DocumentBuilder` to it.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Why do we need a builder? It abstracts the low‑level OpenXML structures, letting us focus on *what* we want—like **add pie chart to word**—instead of *how* the XML looks.

## Krok 3: Wstaw wykres kołowy

Now comes the core of **how to insert pie chart**. We ask the builder to place a pie chart of a specific size. The dimensions are in points (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

At this point the chart is empty, but the placeholder is already in the document. You’ve just **add pie chart to word** programmatically.

## Krok 4: Wypełnij wykres danymi

A pie chart needs at least one series of values. Let’s feed it some sample data that represents market share.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

If you ever need multiple series (stacked pies, doughnuts, etc.) you can call `pieChart.getSeries().add()` and repeat the steps. The same logic applies when you want to **display percentages on chart** for each slice.

## Krok 5: **add data label percent** – pokaż procenty na kawałkach

This is the part most developers forget: configuring the data labels to show percentages. Without it, the chart only shows raw numbers, which can be ambiguous.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

The `setShowPercent(true)` call tells Aspose.Words to render the label as “30 %”, “45 %”, etc. That’s exactly how you **show percent on pie chart** without any extra formatting work.

## Krok 6: Zapisz dokument

Finally, write the document to disk. You can choose `.docx`, `.pdf`, or even `.html`. For this guide we’ll stick with the modern `.docx` format.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Run the program, open `PieChartDemo.docx`, and you’ll see a neatly rendered pie chart with percentage labels on each slice.

## Oczekiwany wynik

Below is a screenshot of the generated Word file. Notice how each slice displays its share as a percentage—exactly what we wanted when we set **add data label percent**.

![Zrzut ekranu dokumentu Word zawierającego wykres kołowy z etykietami procentowymi](/images/pie-chart-percent.png){.center width=600px alt="Zrzut ekranu pokazujący, jak wstawić wykres kołowy w Word z etykietami procentowymi"}

*Tekst alternatywny zawiera główne słowo kluczowe, spełniając zarówno wymagania SEO, jak i dostępności.*

## Częste pytania i obsługa przypadków brzegowych

| Question | Answer |
|----------|--------|
| **Czy mogę zmienić czcionkę etykiet procentowych?** | Tak. Po włączeniu `setShowPercent(true)`, pobierz obiekt `DataLabel` i dostosuj jego właściwość `Font` (`dataLabel.getFont().setSize(10);`). |
| **Co zrobić, jeśli potrzebuję wykresu pierścieniowego zamiast kołowego?** | Zastąp `ChartType.PIE` przez `ChartType.DOUGHNUT` w wywołaniu `insertChart`. Ta sama logika **add data label percent** działa. |
| **Czy starsze wersje Worda (2007‑2010) wyświetlają procenty poprawnie?** | Aspose.Words zapisuje podstawowy XML w sposób niezależny od wersji, więc procenty pojawiają się w każdym Wordzie obsługującym wykresy (2007+). |
| **Jak dodać tytuł do wykresu?** | Użyj `pieChart.getTitle().setText("Market Share");` przed zapisem. |
| **Czy mogę wstawić wykres do konkretnego akapitu lub komórki tabeli?** | Oczywiście. Przenieś `DocumentBuilder` do żądanej lokalizacji (`builder.moveToParagraph(index, true);` lub `builder.moveToCell(table, row, column, true);`) przed wywołaniem `insertChart`. |

## Porady i triki z praktyki

- **Pro tip:** Jeśli planujesz generować wiele wykresów w pętli, ponownie używaj jednej instancji `DocumentBuilder`; zmniejsza to zużycie pamięci.
- **Watch out for:** Bardzo małe kawałki (< 2 %). Aspose.Words może pominąć etykietę, aby uniknąć bałaganu; możesz wymusić jej wyświetlenie za pomocą `dataLabel.setShowLabel(true);`.
- **Performance note:** Renderowanie wykresów jest intensywne pod względem CPU. Przy masowej generacji raportów rozważ wielowątkowość, ale upewnij się, że każdy wątek pracuje na własnej instancji `Document`.
- **Version check:** Metoda `setShowPercent` została wprowadzona w Aspose.Words 22.8. Jeśli używasz starszej wersji, zaktualizuj ją lub ręcznie oblicz procenty i ustaw je jako niestandardowe etykiety.

## Podsumowanie

Omówiliśmy **how to insert pie chart** w dokumencie Word przy użyciu Aspose.Words, pokazaliśmy, jak **add data label percent**, i zaprezentowaliśmy najprostszy sposób na **display percentages on chart**. Dzięki kilku linijkom Java możesz **add pie chart to word** i **show percent on pie chart**, przekształcając surowe liczby w od razu czytelne wizualizacje.

## Co dalej?

- Eksperymentuj z innymi typami wykresów (`BAR`, `LINE`, `AREA`) i zobacz, jak ta sama logika **add data label percent** ma zastosowanie.
- Połącz wykresy z tabelami, aby uzyskać bardziej bogate raporty — Aspose.Words umożliwia łatwe umieszczenie wykresu obok tabeli danych.
- Zbadaj eksport tego samego dokumentu do PDF lub HTML, aby zobaczyć, jak procenty renderują się w różnych formatach.

Śmiało modyfikuj wymiary, kolory lub źródło danych (np. zapytanie do bazy), a Twoje raporty Word ożyją. Jeśli napotkasz problem, zostaw komentarz poniżej — miłego wykreślania!

## Co powinieneś nauczyć się dalej?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Wstaw wykres kolumnowy w Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Wstaw wykres powierzchniowy w dokumencie Word | Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Wstaw wykres bąbelkowy w Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}