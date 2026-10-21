---
category: general
date: 2026-09-27
description: Dowiedz się, jak wstawić wykres kołowy do dokumentu Word przy użyciu
  Javy, stworzyć wykres kołowy w Wordzie oraz wyświetlić procenty na wykresie kołowym,
  aby uzyskać przejrzyste informacje o danych.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: pl
lastmod: 2026-09-27
og_description: Jak wstawić wykres kołowy do dokumentu Word przy użyciu Javy. Ten
  przewodnik pokazuje, jak stworzyć wykres kołowy w Wordzie, wyświetlić procenty na
  wykresie kołowym oraz dodać linie prowadzące.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Jak wstawić wykres kołowy do dokumentu Word przy użyciu Javy
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Jak wstawić wykres kołowy do dokumentu Word przy użyciu Javy
url: /pl/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak wstawić wykres kołowy do dokumentu Word przy użyciu Javy

Jeśli potrzebujesz **how to insert pie chart** do pliku Word, ten przewodnik przeprowadzi Cię przez cały proces. Zobaczysz, jak **create pie chart in Word**, wyświetlić procenty na każdym kawałku i dodać linie prowadzące dla eleganckiego wyglądu.

Automatyzacja Worda często wydaje się ciężka, ale dzięki Aspose.Words for Java możesz programowo generować w pełni sformatowane dokumenty. Po zakończeniu tego samouczka będziesz mieć działający fragment kodu Java, który tworzy dokument Word zawierający stylizowany wykres kołowy.

## Wymagania wstępne

- Zainstalowany Java 17 lub nowszy
- Maven lub Gradle do zarządzania zależnościami
- Aspose.Words for Java (wersja 23.11 lub nowsza) dodany do projektu
- Podstawowa znajomość składni Java

Nie potrzebujesz żadnego wcześniejszego doświadczenia z API wykresów; poniższe kroki obejmują wszystko od konfiguracji projektu po ostateczny wynik.

## Krok 1: Skonfiguruj zależność Maven

Dodaj bibliotekę Aspose.Words do swojego `pom.xml`. Ta pojedyncza zależność zapewnia dostęp do `Document`, `DocumentBuilder` oraz klas wykresów.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Jeśli używasz Gradle, odpowiednik wygląda następująco:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** Używaj najnowszej stabilnej wersji, aby korzystać z poprawek błędów i nowych funkcji wykresów.

## Krok 2: Utwórz nowy dokument i builder

`Document` reprezentuje plik Word, natomiast `DocumentBuilder` pozwala wstawiać treść. To podstawa dla **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder jest teraz gotowy do umieszczania obiektów w dowolnym miejscu dokumentu.

## Krok 3: Wstaw wykres kołowy

Aspose.Words obsługuje kilka typów wykresów; wybieramy `ChartType.PIE`. Rozmiar wyrażany jest w punktach (1 punkt = 1/72 cala).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

Na tym etapie wykres zawiera domyślną serię danych z wartościami zastępczymi. W razie potrzeby możesz później zamienić te wartości.

## Krok 4: Uzyskaj dostęp do serii wykresu

Wykres kołowy ma jedną serię, która przechowuje wartości kawałków. Pobierz ją, aby zastosować formatowanie.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Krok 5: Rozdziel pierwszy kawałek

Rozdzielenie kawałka przyciąga uwagę do konkretnego punktu danych. To powszechny element wizualny, gdy chcesz wyróżnić kluczowy wskaźnik.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Krok 6: Pokaż procenty na każdym kawałku

Wyświetlanie procentów bezpośrednio na wykresie poprawia wgląd w dane. Spełnia to wymóg **show percentages on pie chart**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Krok 7: Dodaj linie prowadzące dla czytelniejszych etykiet

Linie prowadzące łączą etykiety kawałków z ich odpowiednimi sekcjami, eliminując niejasności. To spełnia **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Krok 8: Zapisz dokument

Na koniec zapisz dokument na dysku. Możesz wybrać dowolny folder, do którego masz prawo zapisu.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Uruchomienie programu tworzy `output/PieFormatted.docx`. Otwórz plik w Microsoft Word i zobaczysz wykres kołowy, w którym:

- Pierwszy kawałek jest rozdzielony.
- Każdy kawałek pokazuje swoją wartość procentową.
- Linie prowadzące wskazują z procentów na odpowiednie kawałki.

### Oczekiwany wynik

![Sformatowany wykres kołowy w Word](/images/pie-formatted.png){: .center-image alt="Sformatowany wykres kołowy wstawiony do dokumentu Word"}

Zrzut ekranu (tekst alternatywny używa głównego słowa kluczowego) ilustruje ostateczny wygląd: czysty, oparty na danych wykres kołowy gotowy do raportów, propozycji lub pulpitów nawigacyjnych.

## Typowe warianty i przypadki brzegowe

### Zmiana wartości kawałków

Jeśli potrzebujesz własnych danych, zamień domyślne wartości serii:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Wiele serii (wykres pierścieniowy)

Podczas gdy prosty wykres kołowy ma jedną serię, Aspose.Words obsługuje także wykresy pierścieniowe z wieloma seriami. Zmień `ChartType.PIE` na `ChartType.DONUT` i powtórz kroki konfiguracji serii.

### Eksport do PDF

Jeśli Twój dalszy przepływ pracy wymaga PDF, wywołaj `doc.save("output/PieFormatted.pdf");` po zbudowaniu wykresu. Układ wizualny pozostaje identyczny.

## Pełny listing źródła

Poniżej znajduje się kompletny, samodzielny plik Java, który możesz skopiować i wkleić do swojego IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Skompiluj i uruchom program przy użyciu `mvn compile exec:java -Dexec.mainClass=PieChartExample` (lub równoważnego polecenia Gradle). Wygenerowany plik Word będzie zawierał w pełni sformatowany wykres kołowy.

## Zakończenie

Teraz wiesz, **how to insert pie chart** do dokumentu Word przy użyciu Javy, jak **create pie chart in Word**, jak **show percentages on pie chart**, oraz jak **add chart to word document** z liniami prowadzącymi. Pełny przykład demonstruje każdy krok, wyjaśnia dlaczego kod jest napisany w ten sposób i daje wskazówki dotyczące dostosowywania.

Następnie możesz zbadać:

- Dodawanie etykiet danych z własnymi czcionkami (warianty **show percentages on pie chart**)
- Łączenie wielu wykresów w jednym dokumencie (przypadek użycia **add chart to word document**)
- Automatyzacja generowania raportów z tabelami i wykresami razem

Śmiało eksperymentuj z kolorami, kolejnością kawałków lub eksportem do PDF. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć wykres słupkowy przy użyciu Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ukryj oś wykresu w dokumencie Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Utwórz wykres liniowy w Word przy użyciu Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}