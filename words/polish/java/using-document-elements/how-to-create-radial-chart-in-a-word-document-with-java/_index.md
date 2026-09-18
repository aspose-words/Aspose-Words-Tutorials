---
category: general
date: 2026-09-18
description: Dowiedz się, jak stworzyć wykres radialny w dokumencie Word przy użyciu
  Javy, dodać etykiety danych wykresu oraz wstawić dane serii, wraz z kompletnym przykładem
  kodu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: pl
lastmod: 2026-09-18
og_description: Utwórz wykres radialny w dokumencie Word przy użyciu Javy, dodaj etykiety
  danych wykresu i wstaw dane serii w jednym poradniku.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Tworzenie wykresu radialnego w Wordzie przy użyciu Javy – przewodnik krok
  po kroku
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Jak stworzyć wykres radialny w dokumencie Word przy użyciu Javy
url: /pl/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć wykres radialny w dokumencie Word przy użyciu Javy

Jeśli potrzebujesz utworzyć wykres radialny w dokumencie Word, ten przewodnik pokaże Ci dokładne kroki. Dowiesz się także, jak dodać etykiety danych wykresu i wstawić dane serii, aby wykres był gotowy do prezentacji.

Generowanie wykresu programowo usuwa ręczną pracę formatowania i zapewnia spójność raportów. Samouczek zakłada, że masz podstawową wiedzę z Javy oraz zainstalowaną najnowszą wersję biblioteki Aspose.Words for Java.

## Czego będziesz potrzebować

* Java 17 lub nowszy  
* Aspose.Words for Java (wersja 23.12 lub nowsza)  
* IDE lub narzędzie budujące, które potrafi rozwiązać zależności Maven/Gradle  

Posiadanie tych wymagań zainstalowanych pozwala uruchomić przykład bez dodatkowej konfiguracji.

## Jak utworzyć wykres radialny w dokumencie Word

Pierwszym krokiem jest utworzenie pustego pliku Word, który będzie zawierał wykres. Pusty dokument zapewnia czyste płótno i unika niezamierzonych stylów.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` reprezentuje cały plik .docx, natomiast `DocumentBuilder` udostępnia metody do wstawiania elementów, takich jak akapity, tabele i wykresy.

## Jak wstawić wykres

Następnie wstawiasz sam wykres. Metoda `insertChart` tworzy obiekt wykresu i umieszcza go w bieżącej pozycji kursora buildera.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Wykres polarny renderuje punkty danych wokół centralnej osi, co jest idealne do prezentacji informacji cyklicznych. Wymiary wyrażane są w punktach (1 pt ≈ 1/72 cala).

## Dodaj dane serii do wykresu

Wykres bez danych serii jest pusty. Możesz dodać serię ręcznie lub powiązać ją ze źródłem danych. Poniższy przykład dodaje jedną serię z trzema punktami danych.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` przyjmuje nazwę serii, listę etykiet kategorii oraz listę odpowiadających wartości liczbowych. Możesz powtórzyć ten blok, aby dodać dodatkowe serie (`addSeriesData`).

## Dodaj etykiety danych wykresu do pierwszej serii

Etykiety danych sprawiają, że wykres jest czytelny bez najeżdżania na punkty. Poniższa linia włącza etykiety wartości dla pierwszej serii.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Ustawienie `showValue` na `true` wyświetla wartość każdego punktu bezpośrednio na wykresie. Możesz także włączyć nazwy kategorii, procenty lub linie prowadzące przy użyciu tego samego obiektu `DataLabelFormat`.

## Zapisz plik Word

Po skonfigurowaniu wykresu zapisz dokument na dysku. Wybierz lokalizację, do której Twoja aplikacja ma dostęp.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Plik `RadialChart.docx` zawiera teraz w pełni funkcjonalny wykres radialny z etykietami danych.

## Pełny działający przykład

Poniżej znajduje się samodzielny program, który możesz skopiować, skompilować i uruchomić. Demonstruje on kompletny przepływ pracy od utworzenia pustego dokumentu Word po zapisanie wykresu radialnego z etykietami danych.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Oczekiwany wynik**

Gdy otworzysz `output/RadialChart.docx` w programie Microsoft Word, zobaczysz wykres radialny zatytułowany *Quarterly Sales*. Każdy punkt wyświetla swoją wartość liczbową (np. „15000”) obok znacznika.

## Typowe warianty i przypadki brzegowe

| Sytuacja | Zalecana zmiana |
|-----------|--------------------|
| Potrzebujesz innego typu wykresu | Zastąp `ChartType.POLAR` dowolną inną wartością enum `ChartType` (np. `ChartType.COLUMN`). |
| Wykres musi używać zewnętrznego zakresu Excel | Użyj `chart.setDataRange("Sheet1!A1:B5")` po utworzeniu wykresu i załadowaniu skoroszytu. |
| Chcesz ukryć legendę | `chart.getLegend().setVisible(false);` |
| Dokument musi być zapisany jako PDF | Wywołaj `doc.save("RadialChart.pdf");` – Aspose.Words automatycznie konwertuje wykres. |

Te zmiany zachowują podstawową logikę, jednocześnie dostosowując wynik do konkretnych wymagań.

## Porady profesjonalne

* **Reuse the builder** – Możesz wstawiać wiele wykresów w tym samym dokumencie, wywołując `builder.insertChart` wielokrotnie.  
* **Performance** – Generując wiele wykresów, utwórz jedną instancję `DocumentBuilder` i używaj jej ponownie, aby zmniejszyć narzut alokacji obiektów.  
* **Styling** – Wygląd wykresu (kolory, grubość linii) kontrolowany jest metodami obiektu `Chart` poprzez `getSeries().get(i).getFormat()`. Eksperymentuj z tymi ustawieniami, aby dopasować je do identyfikacji wizualnej firmy.

## Zakończenie

Teraz wiesz, jak utworzyć wykres radialny w dokumencie Word przy użyciu Javy, dodać dane serii oraz etykiety danych wykresu przed zapisaniem pliku. Pełny przykład można rozszerzyć o obsługę dodatkowych serii, niestandardowych stylów lub alternatywnych formatów wyjściowych.

Zbadaj powiązane tematy, takie jak **how to insert chart** z zewnętrznych źródeł danych, **create blank word** dokumenty z predefiniowanymi szablonami oraz **add series data** dynamicznie z baz danych. Eksperymentuj z różnymi typami wykresów, aby odkryć, który wizual najlepiej przekazuje Twoje dane.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}