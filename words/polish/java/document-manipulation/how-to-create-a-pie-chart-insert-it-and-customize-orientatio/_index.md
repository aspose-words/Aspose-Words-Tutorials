---
category: general
date: 2026-11-25
description: Dowiedz się, jak stworzyć wykres kołowy w Javie, wstawić go do dokumentu
  Word, rozdzielić fragment wykresu i zmienić orientację wykresu, korzystając z przejrzystych
  przykładów kodu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: pl
lastmod: 2026-11-25
og_description: Utwórz wykres kołowy w Javie, wstaw go do dokumentu, wyodrębnij kawałek
  koła i zmień orientację wykresu, podając kod krok po kroku.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Tworzenie wykresu kołowego w Javie – wstawianie, wyodrębnianie wycinka i
  obracanie
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Jak stworzyć wykres kołowy, wstawić go i dostosować orientację w Javie
url: /pl/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć wykres kołowy, wstawić go i dostosować orientację w Javie

Jeśli potrzebujesz **utworzyć wykres kołowy** w dokumencie Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Zobaczysz, jak **wstawić wykres kołowy**, wyeksplodować wycinek dla podkreślenia oraz **zmienić orientację wykresu** przy użyciu prostej rotacji.

Tutorial obejmuje wszystko, czego potrzebujesz — od skonfigurowania biblioteki Aspose.Words for Java po wygenerowanie końcowego pliku `.docx`, który wyświetla obrócony, wyeksplodowany wykres kołowy. Nie wymagana jest żadna zewnętrzna dokumentacja; po prostu postępuj zgodnie z krokami i uruchom kod.

## Prerequisites

Before you start, make sure you have:

* Zainstalowany Java 17 lub nowsza.
* Maven lub Gradle do zarządzania zależnościami.
* Ważna licencja Aspose.Words for Java (lub użyj trybu darmowej oceny).

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Example for Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Porada:** Utrzymuj wersję biblioteki aktualną; najnowsze wydanie (24.10 w momencie pisania) zawiera poprawki błędów związane z renderowaniem wykresów.

## Krok 1: Utwórz wykres kołowy i wstaw go do dokumentu

Pierwszym krokiem jest **utworzenie wykresu kołowego** i osadzenie go w pliku Word. Poniższy kod tworzy prosty dokument, dodaje miejsce na wykres i wstawia wykres kołowy o rozmiarze 400 × 300 pikseli.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Dlaczego to ważne:** `builder.insertChart` tworzy miejsce na wykres, które Aspose.Words automatycznie konwertuje na wykres OOXML podczas zapisywania dokumentu. Argument `ChartType.PIE` informuje bibliotekę, aby renderowała wykres kołowy, spełniając wymóg **wstawienia wykresu kołowego**.

## Krok 2: Wyeksploduj wycinek wykresu kołowego, aby wyróżnić segment

Wyeksplodowanie wycinka przyciąga uwagę do konkretnego punktu danych. Poniższa linia wyeksplodowuje pierwszy wycinek (indeks 0) o 10 punktów:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Możesz zmienić indeks, aby wybrać inny wycinek, lub dostosować odległość wyeksplodowania dla subtelniejszego efektu. Wyeksplodowanie wycinka jest standardowym sposobem **wyeksplodowania wycinka wykresu kołowego** w Aspose.Words.

## Krok 3: Zmień orientację wykresu poprzez jego obrót

Obrócenie wykresu daje nową perspektywę wizualną. Użyj `setRotationAngle`, aby obrócić cały wykres zgodnie z ruchem wskazówek zegara (kąt podawany jest w stopniach).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

Powyższe wywołanie spełnia wymagania **obrócenia wykresu kołowego** oraz **zmiany orientacji wykresu**. Akceptowany jest dowolny kąt między 0 a 360 stopni.

## Pełny, uruchamialny przykład

Łącząc wszystko razem, oto kompletny, samodzielny program, który tworzy wykres kołowy, wyeksplodowuje wycinek i obraca wykres. Uruchom go ze swojego IDE lub z wiersza poleceń przy użyciu `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Oczekiwany wynik

* Plik o nazwie **CreatePieChartDemo.docx** pojawia się w katalogu roboczym.
* Otwarcie pliku w Microsoft Word wyświetla wykres kołowy o rozmiarze 400 × 300 pikseli.
* Pierwszy wycinek (Q1) jest odsunięty na zewnątrz o 10 punktów, tworząc efekt **wyeksplodowanego wycinka wykresu kołowego**.
* Cały wykres jest przechylony o 45 stopni, demonstrując **zmianę orientacji wykresu** oraz **obrócenie wykresu kołowego**.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Jak dostosować kod |
|-----------|-----------------------|
| **Inny rozmiar wykresu** | Zmień argumenty `400, 300` w `insertChart`. |
| **Wiele serii** | Dodaj więcej obiektów `ChartSeries` do `chart.getSeries()`. |
| **Wyeksploduj inny wycinek** | Użyj `setExplode(sliceIndex, distance)` z żądanym `sliceIndex`. |
| **Brak potrzeby rotacji** | Pomiń wywołanie `setRotationAngle` lub ustaw kąt na `0`. |
| **Eksportuj do PDF zamiast DOCX** | Po zbudowaniu dokumentu wywołaj `doc.save("output.pdf")` z formatem PDF. |

> **Uwaga:** Użycie ujemnej odległości wyeksplodowania powoduje wyrzucenie `IllegalArgumentException`. Zawsze podawaj wartość nieujemną.

## Wskazówka dotycząca wydajności

Jeśli generujesz wiele wykresów w pętli, używaj jednego `DocumentBuilder` i wywołuj `insertChart` tylko w każdej iteracji. To zmniejsza zużycie pamięci i przyspiesza przetwarzanie.

## Podsumowanie

Teraz wiesz, jak **utworzyć wykres kołowy**, **wstawić wykres kołowy**, **wyeksplodować wycinek wykresu kołowego** oraz **obrócić wykres kołowy** przy użyciu Aspose.Words for Java. Pełny przykład demonstruje cały przepływ pracy — od inicjalizacji dokumentu po zapisanie pliku, który wizualizuje obrócony, wyeksplodowany wykres kołowy.

Następnie możesz dalej badać **zmianę orientacji wykresu**, stosując efekty 3‑D, lub eksperymentować z innymi typami wykresów, takimi jak **Bar** czy **Line**. Te same wzorce API mają zastosowanie, więc rozszerzenie tego tutorialu jest proste.

Śmiało modyfikuj dane, indeks wycinka lub kąt obrotu, aby dopasować je do własnych potrzeb raportowych i podziel się wynikami ze społecznością!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak wstawić wykres kołowy do dokumentu Word przy użyciu Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Jak wyeksplodować wycinek wykresu kołowego w Javie – tutorial wykresów Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}