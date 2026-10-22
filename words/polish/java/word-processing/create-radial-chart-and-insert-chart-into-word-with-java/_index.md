---
category: general
date: 2026-09-27
description: Utwórz wykres radialny w Javie i wstaw go do dokumentu Word. Dowiedz
  się, jak ustawić rozmiar wykresu, dodać serię danych oraz wygenerować pusty dokument
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: pl
lastmod: 2026-09-27
og_description: Utwórz wykres radialny w Javie, a następnie wstaw go do Worda. Ten
  przewodnik pokazuje, jak ustawić rozmiar wykresu, dodać serię danych i utworzyć
  pusty dokument Word.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Utwórz wykres radialny i wstaw go do Worda przy użyciu Javy
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Utwórz wykres radialny i wstaw go do Worda przy użyciu Javy
url: /pl/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz wykres radialny i wstaw wykres do Worda przy użyciu Javy

Jeśli potrzebujesz **create radial chart** w pliku Word przy użyciu Javy, ten tutorial pokaże Ci dokładnie, jak to zrobić. Zobaczysz, jak **insert chart into Word**, ustawić wymiary wykresu i stworzyć **blank Word document** od podstaw.

Przejdziemy przez każdy wymagany krok, od inicjalizacji dokumentu po dodanie serii danych i zapisanie finalnego `.docx`. Po zakończeniu będziesz mieć w pełni funkcjonalny plik Word zawierający wykres radialny oraz zrozumiesz **how to set chart size** i **add data series chart** dla przyszłych modyfikacji.

## Prerequisites

* Java 17 lub nowszy (kod kompiluje się na dowolnym nowoczesnym JDK)
* Aspose.Words for Java 24.9 lub nowszy – metoda `setShowGraduations` jest dostępna dopiero od tej wersji
* IDE lub narzędzie budujące (Maven/Gradle), które może dołączyć JAR Aspose.Words
* Podstawowa znajomość składni Javy oraz zarządzania zależnościami w Maven/Gradle

> **Pro tip:** Jeśli używasz Maven, dodaj poniższy fragment do swojego `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Krok 1: Utwórz pusty dokument Word

Pusty dokument jest płótnem, na którym zostanie umieszczony wykres. Klasa `Document` reprezentuje cały plik `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Utworzenie pustego dokumentu zapewnia, że żadne istniejące wcześniej treści nie będą kolidować z układem wykresu.

## Krok 2: Zainicjalizuj DocumentBuilder

`DocumentBuilder` udostępnia wygodne metody wstawiania obiektów, tekstu i innych elementów do dokumentu.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder będzie później użyty do **insert chart into Word**.

## Krok 3: Zbuduj wykres radialny

Aspose.Words obsługuje wiele typów wykresów; `ChartType.RADIAL` tworzy wykres radialny (polarny).

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Na tym etapie wykres istnieje, ale nie ma danych, rozmiaru ani opcji wizualnych.

## Krok 4: Dodaj serię danych do wykresu

Wykres bez serii danych jest pusty. Metoda `add` przyjmuje nazwę serii oraz tablicę wartości.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Możesz dodać wiele serii, wywołując `add` wielokrotnie. Spełnia to wymóg **add data series chart**.

## Krok 5: Włącz graduacje (opcjonalnie)

Graduacje to radialne linie siatki, które poprawiają czytelność. Są dostępne dopiero od wersji 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Jeśli używasz starszej wersji Aspose.Words, ta linia spowoduje wyrzucenie wyjątku — dlatego najpierw sprawdź wersję biblioteki.

## Krok 6: Ustaw wymiary wykresu

Kontrolowanie rozmiaru wykresu pozwala dopasować go ładnie do marginesów strony. To odpowiada na pytanie **how to set chart size**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Możesz dostosować wartości szerokości i wysokości do potrzeb układu. Pamiętaj, że 1 punkt ≈ 1/72 cala.

## Krok 7: Wstaw wykres do dokumentu Word

Teraz wykres jest gotowy do umieszczenia. Metoda `insertChart` klasy `DocumentBuilder` obsługuje wstawianie.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

To jest sedno operacji **insert chart into word**.

## Krok 8: Zapisz dokument

Na koniec zapisz dokument na dysku. Plik będzie zawierał wykres radialny, który właśnie utworzyłeś.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Uruchomienie programu generuje `RadialChart.docx` w katalogu roboczym projektu. Otwarcie pliku w Microsoft Word pokazuje wykres radialny z trzema punktami danych i widocznymi graduacjami.

### Oczekiwany wynik

* Plik Word o nazwie `RadialChart.docx`
* Wewnątrz pliku, pojedyncza strona zawierająca wykres radialny o rozmiarze 400 × 300 punktów
* Wykres wyświetla jedną serię zatytułowaną **Series 1** z wartościami **10, 20, 30**
* Graduacje (radialne linie siatki) są widoczne wokół wykresu

## Typowe warianty i przypadki brzegowe

| Sytuacja | Co zmienić | Powód |
|-----------|----------------|--------|
| **Wiele serii** | Wywołaj `chart.getSeries().add(...)` dla każdej serii | Umożliwia porównawczą wizualizację danych |
| **Inny typ wykresu** | Zastąp `ChartType.RADIAL` przez `ChartType.COLUMN` (lub inny) | Użyj typu wykresu, który najlepiej reprezentuje Twoje dane |
| **Niestandardowe kolory** | Uzyskaj dostęp do `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Poprawia identyfikację wizualną |
| **Starsza wersja Aspose.Words** | Pomiń linię `setShowGraduations` lub zaktualizuj bibliotekę | Zapobiega `NoSuchMethodError` |
| **Zapisywanie w innym formacie** | Użyj `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Generuje PDF zamiast DOCX |

## Pełny, gotowy do uruchomienia przykład

Poniżej znajduje się kompletny, samodzielny program w Javie. Skopiuj go do pliku o nazwie `RadialChartExample.java`, dodaj zależność Aspose.Words i uruchom.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Zakończenie

Teraz wiesz, jak programowo **create radial chart**, **add data series chart**, kontrolować **how to set chart size** oraz **insert chart into Word**, zaczynając od **blank Word document**. Przykład używa Aspose.Words for Java 24.9, ale te same koncepcje mają zastosowanie do innych bibliotek wykresów, które udostępniają podobne API.

### Kolejne kroki

* Zbadaj inne typy wykresów (`ChartType.PIE`, `ChartType.LINE` itd.) – to nawiązuje do drugiego słowa kluczowego **insert chart into word**.
* Dostosuj etykiety osi, legendy i kolory, aby pasowały do wytycznych Twojej marki.
* Generuj wykresy dynamicznie z zapytań bazodanowych lub plików CSV.
* Konwertuj wynikowy `.docx` do PDF w celu dystrybucji (`doc.save("output.pdf", SaveFormat.PDF)`).

Śmiało eksperymentuj z wymiarami, danymi serii i opcjami stylizacji, aby stworzyć dokładnie taki wizual, jaki potrzebujesz. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z krok po kroku wyjaśnieniami, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak stworzyć wykres kolumnowy przy użyciu Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Utwórz dokument Word w Javie – Dodaj prostokątny kształt z efektem cienia](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Wstaw wykres obszarowy do dokumentu Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}