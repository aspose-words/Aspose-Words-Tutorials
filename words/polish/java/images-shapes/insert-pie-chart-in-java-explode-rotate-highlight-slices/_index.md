---
category: general
date: 2026-07-20
description: Wstaw wykres kołowy w Javie z przewodnikiem krok po kroku. Dowiedz się,
  jak wyodrębnić wycinek, jak obrócić wykres kołowy, podświetlić wycinek wykresu kołowego
  i dostosować wycinek wykresu kołowego.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: pl
lastmod: 2026-07-20
og_description: Wstaw wykres kołowy w Javie i opanuj, jak wyodrębnić kawałek, jak
  obrócić wykres kołowy, podświetlić kawałek wykresu kołowego oraz dostosować kawałek
  wykresu kołowego, aby uzyskać dopracowane raporty wizualne.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Wstaw wykres kołowy w Javie – rozdziel, obróć i podświetl
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Wstaw wykres kołowy w Javie – rozdziel, obróć i podświetl kawałki
url: /pl/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw wykres kołowy w Javie – Rozdziel, Obróć i Podświetl fragmenty

Czy kiedykolwiek potrzebowałeś **wstawić wykres kołowy** w raporcie Java, ale nie byłeś pewien, jak sprawić, by pojedynczy fragment wystawał? Nie jesteś jedyny. Niezależnie od tego, czy tworzysz pulpit nawigacyjny, generujesz fakturę, czy po prostu wizualizujesz wyniki ankiety, dobrze sformatowany wykres kołowy może przekształcić surowe liczby w od razu zrozumiałe wnioski.

W tym samouczku zobaczysz kompletny, gotowy do uruchomienia przykład, który pokazuje, jak wstawić wykres kołowy, **jak rozdzielić fragment**, **jak obrócić wykres kołowy**, a nawet **jak podświetlić fragment wykresu kołowego** przy użyciu własnych kolorów. Po zakończeniu będziesz mieć wielokrotnego użytku fragment kodu, który możesz wkleić do dowolnego projektu Java korzystającego z popularnej biblioteki *JFreeChart* (lub dowolnego podobnego API).

## Wymagania wstępne

- Java 17 lub nowszy (kod kompiluje się również ze starszymi wersjami, ale użyjemy nowoczesnej składni `var` dla zwięzłości).  
- Maven lub Gradle do pobrania zależności `org.jfree:jfreechart`.  
- Podstawowa znajomość klas Java oraz koncepcji budowniczego wykresów.  

Jeśli nigdy nie dodawałeś biblioteki do projektu Maven, po prostu wstaw to do swojego `pom.xml`:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

To wszystko — nie wymaga dodatkowej konfiguracji.

## Krok 1: Wstaw wykres kołowy – Utwórz builder i obiekt wykresu

Na początek potrzebujemy *buildera* (pomyśl o nim jak o fabryce), który potrafi tworzyć wykresy. W JFreeChart za ciężką pracę odpowiada `ChartFactory`.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Dlaczego zaczynamy od zestawu danych? Ponieważ sam wykres jest jedynie wizualną nakładką na liczby. **Wstawiając wykres kołowy** tutaj, mamy już płótno 400 × 300 (rozmiar zostanie zastosowany później, gdy wyrenderujemy go do obrazu).

## Krok 2: Jak rozdzielić fragment – Podkreśl pierwszy segment

Teraz, gdy wykres istnieje, sprawmy, by pierwszy fragment się wyróżniał. Rozdzielenie fragmentu odsuwa go nieco od koła, przyciągając wzrok czytelnika.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Zauważ, że w nazwie metody używamy frazy **jak rozdzielić fragment**; dzięki temu intencja jest całkowicie jasna. Metoda `setExplodePercent` przyjmuje klucz (etykietę fragmentu) oraz procent, więc możesz dostosować odległość „wysunięcia” w razie potrzeby.

## Krok 3: Jak obrócić wykres kołowy – Zmień kąt początkowy

Domyślny wykres kołowy zaczyna się od pozycji 12 godziny. Czasami chcesz, aby pierwszy fragment zaczynał się w innym miejscu — być może aby dopasować się do projektu graficznego lub do innego wykresu.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Wywołanie `rotateChart(chart, 45)` obraca cały wykres kołowy tak, że fragment „Apples” zaczyna się pod kątem 45 stopni, dokładnie spełniając wymaganie **jak obrócić wykres kołowy**.

## Krok 4: Podświetl fragment wykresu kołowego – Niestandardowe kolory i etykiety

Poza rozdzielaniem, możesz chcieć nadać fragmentowi unikalny kolor lub wyraźną etykietę, aby naprawdę **podświetlić fragment wykresu kołowego**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Tutaj **dostosowujemy fragment wykresu kołowego** zmieniając jego farbę i styl etykiety. Śmiało zamień kolor lub czcionkę, aby dopasować je do palety Twojej marki.

## Krok 5: Renderuj wykres do obrazu (Opcjonalnie, ale przydatne)

Większość rzeczywistych aplikacji potrzebuje wykresu w formacie PNG, JPEG lub nawet PDF. Poniżej znajduje się szybki sposób na zapisanie wykresu do pliku.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Uruchomienie pełnego przepływu wygeneruje PNG 400 × 300, które wygląda mniej więcej tak:

![Insert pie chart example](image.png){: alt="Przykład wstawienia wykresu kołowego pokazujący rozdzielony i obrócony fragment"}

## Pełny działający przykład

Łącząc wszystko razem, oto metoda `main`, którą możesz skopiować i wkleić do nowej klasy Java i uruchomić:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Oczekiwany wynik

Uruchomienie programu tworzy plik o nazwie **fruit-pie.png**. Otwórz go, a zobaczysz:

- Wykres kołowy 400 × 300 o tytule „Fruit Distribution”.  
- Fragment „Apples” rozdzielony na zewnątrz o 15 %.  
- Cały wykres obrócony, tak że „Apples” zaczyna się pod kątem 45 stopni.  
- Rozdzielony

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak stworzyć wykres słupkowy przy użyciu Aspose.Words dla Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Wstaw wykres punktowy](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Wstaw wykres powierzchniowy](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}