---
category: general
date: 2026-09-18
description: Naucz się tworzyć dokument Word i wstawiać wykres kołowy przy użyciu
  Aspose.Words for Java. Zawiera kroki obracania wykresu kołowego oraz generowania
  pliku Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: pl
lastmod: 2026-09-18
og_description: Utwórz dokument Word i wstaw wykres kołowy przy użyciu Javy. Skorzystaj
  z tego przewodnika, aby obrócić wykres kołowy, rozdzielić kawałki i wygenerować
  plik Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Utwórz dokument Word z wykresem kołowym – przewodnik Java krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Jak utworzyć dokument Word z wykresem kołowym w Javie
url: /pl/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć dokument Word z wykresem kołowym w Javie

Jeśli potrzebujesz **utworzyć dokument Word**, który wizualizuje dane, ten przewodnik pokaże Ci, jak zrobić to za pomocą Aspose.Words for Java. Nauczysz się wstawiać wykres kołowy, wyodrębniać fragment, obracać wykres i ostatecznie **wygenerować plik Word**, który możesz otworzyć w Microsoft Word.

Tworzenie raportów łączących tekst i wykresy nie wymaga osobnego narzędzia graficznego. Po zakończeniu tego samouczka będziesz mieć kompletny, działający program, który tworzy plik .docx zawierający w pełni skonfigurowany wykres kołowy.

## Wymagania wstępne

- Java 17 lub nowszy (kod kompiluje się również z Java 8+)
- Maven lub Gradle do zarządzania zależnościami
- Licencja Aspose.Words for Java (bezpłatna wersja próbna działa w tym przykładzie)
- Podstawowa znajomość składni Java

## Krok 1: Konfiguracja projektu Maven

Utwórz nowy projekt Maven i dodaj zależność Aspose.Words do pliku `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Wskazówka:** Utrzymuj numer wersji aktualny; nowsze wydania wprowadzają ulepszenia typów wykresów i poprawki błędów.

## Krok 2: Utworzenie nowego dokumentu Word

Pierwszą operacją przy **tworzeniu dokumentu Word** programowo jest utworzenie obiektu `Document`. Obiekt ten reprezentuje cały plik .docx w pamięci.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

Klasa `Document` jest punktem wejścia dla wszystkich funkcji przetwarzania Word. W tym momencie żaden plik nie jest zapisywany na dysk; wszystko odbywa się w pamięci RAM, aż wywołasz `save`.

## Krok 3: Jak wstawić wykres kołowy

`DocumentBuilder` pozwala dodawać treść do dokumentu. Za pomocą `insertChart` możesz **wstawiać wykresy kołowe** bezpośrednio.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` instruuje Aspose.Words, aby utworzyć wykres kołowy. Wymiary podawane są w punktach (1 pt ≈ 1/72 cala). Po tym wywołaniu wykres pojawia się w nowym akapicie.

## Krok 4: Wypełnienie wykresu danymi

Wykres kołowy potrzebuje serii wartości. Tutaj dodajemy trzy kategorie: „Apples”, „Bananas” i „Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

Metoda `add` buduje serię i automatycznie tworzy pozycje legendy. Możesz ponownie użyć tego wzorca dla dowolnego zestawu danych liczbowych.

## Krok 5: Podkreślenie pierwszego fragmentu

Wyodrębnienie fragmentu przyciąga uwagę do konkretnej wartości. Pierwszy fragment (indeks 0) jest wyodrębniony o 20 punktów.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Ustawienie `explode` na serii wpływa na cały wykres, więc tylko pierwszy punkt danych jest przesunięty.

## Krok 6: Jak obrócić wykres kołowy

Obracanie wykresu poprawia równowagę wizualną, szczególnie gdy największy fragment nie znajduje się na górze. Metoda `setRotationAngle` przyjmuje stopnie.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Obrót o 45° przesuwa kąt początkowy zgodnie z ruchem wskazówek zegara, co ułatwia odczyt wykresu w wielu układach.

## Krok 7: Zapisz dokument i wygeneruj plik Word

Na koniec zapisz dokument na dysku. Ten krok **generuje plik Word**, który może być otwarty w Microsoft Word, LibreOffice lub dowolnym kompatybilnym przeglądarce.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Metoda `save` automatycznie wykrywa rozszerzenie .docx i zapisuje pakiet kompatybilny z Word. Folder `output` musi istnieć lub możesz go utworzyć programowo.

### Oczekiwany wynik

Po uruchomieniu programu otwórz `output/PieChart.docx`. Powinieneś zobaczyć:

- Jedną stronę zawierającą wykres kołowy o wymiarach 400 × 300 pt.
- Fragment „Apples” wyodrębniony na zewnątrz o 20 pt.
- Cały wykres obrócony o 45° zgodnie z ruchem wskazówek zegara.
- Legendę odpowiadającą trzem kategoriom owoców.

## Typowe warianty i przypadki brzegowe

### Wstawianie wielu wykresów

Jeśli potrzebujesz więcej niż jednego wykresu, wywołaj ponownie `builder.insertChart` po przesunięciu kursora:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Zmiana kolorów wykresu

Możesz dostosować kolory fragmentów za pomocą kolekcji `getPoints()` serii:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Obsługa dużych zestawów danych

Dla zestawów danych z więcej niż 10 fragmentami rozważ użycie wykresu pierścieniowego (`ChartType.DOUGHNUT`), aby zachować przejrzystość wizualną.

## Zakończenie

Teraz wiesz, jak **utworzyć dokument Word**, **wstawić wykres kołowy**, **obrócić wykres kołowy** i **wygenerować plik Word** przy użyciu Aspose.Words for Java. Pełne rozwiązanie demonstruje cały przepływ pracy od inicjalizacji dokumentu po ostateczne zapisanie pliku, obejmując zarówno „jak”, jak i „dlaczego” każdego kroku.

Następnie, zapoznaj się z powiązanymi tematami, takimi jak **tworzenie danych wykresu kołowego** z bazy danych, dodawanie etykiet danych lub eksportowanie wykresu jako obrazu. Eksperymentuj z różnymi typami wykresów (słupkowy, liniowy, pierścieniowy), aby poszerzyć swoje narzędzia automatyzacji Word.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć wykres słupkowy przy użyciu Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Utwórz dokument Word w Javie – Dodaj kształt prostokąta z efektem cienia](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Śledzenie zmian w dokumentach Word przy użyciu Aspose.Words Java: Kompletny przewodnik po wersjach dokumentu](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}