---
category: general
date: 2026-10-04
description: Poznaj, jak wydzielić fragment wykresu w Wordzie, wydzielić kawałek wykresu
  kołowego i zmienić rozmiar wykresu pierścieniowego, korzystając z przykładu w Javie
  krok po kroku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: pl
lastmod: 2026-10-04
og_description: Jak wyodrębnić fragment wykresu w Wordzie i dostosować wykresy kołowe
  lub pierścieniowe w Javie. Skorzystaj z pełnego przykładu, aby zmodyfikować wykres
  w Wordzie.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Jak rozdzielić wycinek w wykresie Word – pełny przewodnik Java
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Jak wyodrębnić fragment wykresu w Wordzie i dostosować jego wygląd
url: /pl/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wystrzelić fragment w wykresie Word i dostosować jego wygląd

If you need to **how to explode slice** in a Word chart, this guide shows you exactly how. Whether you’re preparing a sales presentation or a financial report, exploding a pie‑chart slice or adjusting a doughnut hole can make the most important data stand out. In the following sections you’ll also learn how to **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, and **customize pie chart word** documents using Aspose.Words for Java.

Jeśli potrzebujesz **how to explode slice** w wykresie Word, ten przewodnik pokaże Ci dokładnie, jak to zrobić. Niezależnie od tego, czy przygotowujesz prezentację sprzedażową, czy raport finansowy, wystrzelenie fragmentu wykresu kołowego lub dostosowanie otworu w wykresie pierścieniowym może sprawić, że najważniejsze dane będą się wyróżniać. W kolejnych sekcjach dowiesz się także, jak **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size** oraz **customize pie chart word** dokumenty przy użyciu Aspose.Words for Java.

You’ll finish this tutorial with a complete, ready‑to‑run Java program that loads a `.docx` file, explodes the first slice of a pie chart, changes the doughnut hole size, and saves the result. No external scripts or manual editing are required.

Zakończysz ten samouczek pełnym, gotowym do uruchomienia programem Java, który wczytuje plik `.docx`, wystrzeliwuje pierwszy fragment wykresu kołowego, zmienia rozmiar otworu w wykresie pierścieniowym i zapisuje wynik. Nie są wymagane żadne zewnętrzne skrypty ani ręczna edycja.

## Wymagania wstępne

- Java 17 lub nowszy zainstalowany na Twojej maszynie deweloperskiej.  
- Maven 3.6+ (lub Gradle) do zarządzania zależnościami.  
- Biblioteka Aspose.Words for Java (bezpłatna wersja próbna działa w środowisku deweloperskim).  
- Dokument Word (`input.docx`) zawierający przynajmniej jeden wykres (kołowy lub pierścieniowy).

## Krok 1: Dodaj Aspose.Words do swojego projektu

If you use Maven, add the following dependency to your `pom.xml`:

Jeśli używasz Maven, dodaj następującą zależność do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

For Gradle, place this in `build.gradle`:

Jeśli używasz Gradle, umieść to w `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Utrzymuj wersję biblioteki aktualną; nowsze wydania dodają wsparcie dla dodatkowych typów wykresów i poprawiają wydajność.

## Krok 2: Wczytaj dokument Word zawierający wykres

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Why this matters:** Ładowanie dokumentu tworzy reprezentację w pamięci, którą Aspose.Words może przeglądać. Bez tego obiektu nie możesz uzyskać dostępu do węzłów wykresu.

## Krok 3: Pobierz pierwszy wykres w dokumencie

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** `NodeType.SHAPE` obejmuje wszystkie obiekty rysunkowe, w tym wykresy. Argument `true` instruuje Aspose, aby przeszukiwał rekurencyjnie, zapewniając znalezienie pierwszego wykresu, nawet jeśli jest zagnieżdżony w tabeli.

## Krok 4: Wystrzel pierwszy fragment wykresu kołowego

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**How it works:** Metoda `setExplosion` przyjmuje wartość liczbową określającą, jak daleko fragment przemieszcza się od środka. Wartość `20` jest widocznie zauważalna, nie naruszając układu wykresu.

## Krok 5: Dostosuj rozmiar otworu w wykresie pierścieniowym

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Why this helps:** Większy otwór w wykresie pierścieniowym może poprawić czytelność przy wielu punktach danych. Metoda `setDoughnutHoleSize` oczekuje wartości procentowej (0‑100).

## Krok 6: Zapisz zmodyfikowany dokument

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Oczekiwany wynik

- Pierwszy fragment pierwszego wykresu kołowego jest przesunięty na zewnątrz, co powoduje jego wyróżnienie.
- Jeśli wykres jest pierścieniowy, centralny otwór rozszerza się do 40 % promienia wykresu.
- Powstały plik `PieChart.docx` można otworzyć w Microsoft Word, LibreOffice lub dowolnym kompatybilnym przeglądarce, wyświetlając wprowadzone programowo zmiany wizualne.

## Pełny, uruchamialny przykład

Below is the entire program in one block. Copy it into `ChartExploder.java`, adjust the file paths, and run it with `mvn compile exec:java` (or your IDE’s run configuration).

Poniżej znajduje się cały program w jednym bloku. Skopiuj go do `ChartExploder.java`, dostosuj ścieżki plików i uruchom przy pomocy `mvn compile exec:java` (lub konfiguracji uruchamiania w IDE).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Running this code will **modify chart in Word**, **explode pie chart slice**, and **change doughnut chart size** automatically.

Uruchomienie tego kodu **modify chart in Word**, **explode pie chart slice** oraz **change doughnut chart size** automatycznie.

## Częste pytania i przypadki brzegowe

| Question | Answer |
|----------|--------|
| *Co jeśli dokument zawiera wiele wykresów?* | Przykład celuje w **pierwszy** wykres (`NodeType.SHAPE, 0`). Aby pracować z innymi wykresami, zmień indeks lub iteruj przez `doc.getChildNodes(NodeType.SHAPE, true)` i filtruj po `shape.getChart() != null`. |
| *Czy mogę wystrzelić fragment inny niż pierwszy?* | Tak. Uzyskaj dostęp do żądanej serii poprzez `chart.getSeries().get(seriesIndex)` i wywołaj `setExplosion(value)`. Indeksy są zerowe. |
| *Czy to działa z plikami Word 2007‑2021?* | Aspose.Words obsługuje `.doc`, `.docx`, `.dot` i `.dotx`. Ten sam kod działa we wszystkich wersjach, ponieważ biblioteka abstrahuje format pliku. |
| *Co jeśli wykres jest słupkowy lub liniowy?* | `setExplosion` i `setDoughnutHoleSize` mają zastosowanie tylko do wykresów kołowych. Kod pomija te operacje, gdy typ wykresu jest inny. |
| *Czy potrzebuję licencji na Aspose.Words?* | Darmowa licencja ewaluacyjna usuwa limit 30‑dni, ale dodaje znak wodny. W środowisku produkcyjnym zakup licencji usuwa znak wodny i odblokowuje pełną funkcjonalność. |

## Podsumowanie

Teraz wiesz, **how to explode slice** w wykresie Word, jak **modify chart in Word**, oraz jak **change doughnut chart size** przy użyciu Aspose.Words for Java. Pełny przykład demonstruje cały przepływ pracy — od wczytania dokumentu, przez zlokalizowanie wykresu, zastosowanie poprawek wizualnych, po zapisanie wyniku — dzięki czemu możesz zintegrować te kroki w dowolnym procesie raportowania lub generowania dokumentów.

**Kolejne kroki**

- Zbadaj inne dostosowania wykresów, takie jak zmiana kolorów, dodawanie etykiet danych lub zmiana typu wykresu (`chart.setChartType(ChartType.BAR_CLUSTERED)`).
- Połącz tę logikę z Aspose.PDF, aby wygenerować wersję PDF tego samego raportu.
- Zautomatyzuj proces dla serii dokumentów, iterując po plikach w katalogu.

Śmiało eksperymentuj z różnymi wartościami wystrzelenia lub procentami otworu w wykresie pierścieniowym, aby dopasować je do wytycznych projektowych. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak stworzyć wykres słupkowy przy użyciu Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ukryj oś wykresu w dokumencie Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Wstaw wykres bąbelkowy w dokumencie Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}