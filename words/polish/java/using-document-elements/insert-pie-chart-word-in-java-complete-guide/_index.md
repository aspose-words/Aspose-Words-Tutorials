---
category: general
date: 2026-09-24
description: Wstaw wykres kołowy do dokumentu DOCX przy użyciu Aspose.Words for Java.
  Dowiedz się, jak ustawić rozmiar otworu, wyodrębnić fragment koła, podświetlić wycinek
  wykresu kołowego oraz tworzyć wykresy w DOCX bez wysiłku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: pl
lastmod: 2026-09-24
og_description: Wstaw wykres kołowy do dokumentu DOCX przy użyciu Aspose.Words for
  Java. Opanuj ustawianie rozmiaru otworu, rozdzielanie kawałka wykresu, podświetlanie
  fragmentu wykresu kołowego i twórz wykres w formacie DOCX w kilka minut.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Wstaw wykres kołowy w Javie – samouczek krok po kroku
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Wstaw słowo wykres kołowy w Javie – kompletny przewodnik
url: /pl/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw wykres kołowy w Java – kompletny przewodnik

Jeśli potrzebujesz **wstawić wykres kołowy** w pliku DOCX, ten samouczek pokaże Ci dokładnie, jak to zrobić przy użyciu Aspose.Words for Java. Zobaczysz pełny przepływ pracy od tworzenia dokumentu po dostosowanie wykresu, tak aby wycinek został wybuchnięty, rozmiar otworu ustawiony na zero i wycinek podświetlony.

Praca z wykresami w dokumentach Word często wydaje się odrębną kwestią od zwykłego przetwarzania tekstu, ale Aspose.Words łączy oba. W poniższych krokach dowiesz się także, jak **tworzyć wykresy docx**, które są gotowe do otwarcia w Microsoft Word, Google Docs lub dowolnym innym przeglądarce kompatybilnej z DOCX.

## Co osiągniesz

* **Wstawić wykres kołowy** do pustego dokumentu  
* **Ustawić rozmiar otworu** aby przekształcić wykres w pełny kołowy (bez pączka)  
* **Wybuchnąć wycinek wykresu kołowego** aby przyciągnąć uwagę do konkretnego segmentu  
* **Podświetlić wycinek wykresu kołowego** przy użyciu własnego formatowania  
* **Utworzyć wykres docx**, który może być udostępniany lub dalej edytowany  

### Wymagania wstępne

* Java 17 lub nowszy (kod kompiluje się także z Java 8)  
* Biblioteka Aspose.Words for Java (wersja 23.9 lub nowsza)  
* IDE lub narzędzie budujące (Maven/Gradle), które może rozwiązać zależność Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Jak wstawić wykres kołowy w DOCX przy użyciu Aspose.Words

Pierwszym krokiem jest stworzenie nowego pustego dokumentu i uzyskanie `DocumentBuilder`. Builder daje bezpośredni dostęp do strumienia zawartości dokumentu, co sprawia, że **wstawienie wykresu kołowego** jest trywialne.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Dlaczego to ma znaczenie
`Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` jest wysokopoziomowym API, które pozwala wstawiać akapity, tabele i wykresy bez konieczności pracy z niskopoziomowym XML. Rozpoczęcie od czystego dokumentu zapewnia, że dodany wykres będzie jedyną zawartością, co jest idealne do nauki lub generowania raportów opartych na szablonach.

## Ustaw rozmiar otworu, aby stworzyć pełny kołowy

Domyślnie Aspose.Words tworzy wykres pierścieniowy (doughnut), gdy żądasz wykresu kołowego. Aby wykres był prawdziwym kołem, musisz **ustawić rozmiar otworu** na `0`. To usuwa wewnętrzny otwór i daje klasyczny wygląd wykresu kołowego.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Praktyczna wskazówka
Jeśli później zdecydujesz się przejść na wykres pierścieniowy, po prostu zmień wartość `holeSize` na procent (np. `30`). To samo API działa dla obu typów wykresów.

## Wybuchnij wycinek wykresu kołowego, aby podkreślić segment

Wybuchnięcie wycinka sprawia, że wyróżnia się wizualnie. Operacja **wybuchnięcia wycinka wykresu kołowego** przesuwa wybrany wycinek na zewnątrz o procent promienia wykresu.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Dlaczego wybuchnąć?
Wybuchnięty wycinek przyciąga wzrok czytelnika do najważniejszego punktu danych — idealny do pulpitów nawigacyjnych lub podsumowań zarządczych. Wartość `20` oznacza 20 % promienia; możesz ją dostosować w zakresie od `0` (brak wybuchu) do `100` (całkowicie odłączony).

## Podświetl wycinek wykresu kołowego przy użyciu własnego formatowania

Poza wybuchaniem, możesz chcieć **podświetlić wycinek wykresu kołowego** zmieniając jego kolor wypełnienia lub obramowanie. Chociaż kod demonstracyjny skupia się na wybuchu, możesz go rozbudować w następujący sposób:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Notatka eksperta
Zmiana koloru wypełnienia konkretnego wycinka wymaga dostępu do obiektu `DataPoint`. Jeśli masz wiele serii, iteruj przez `series.getDataPoints()` i stosuj style warunkowo.

## Zapisz i zweryfikuj utworzony wykres docx

Na koniec **tworzysz wykres docx**, zapisując `Document`. Powstały plik można otworzyć w Microsoft Word, aby zobaczyć sformatowany wykres kołowy.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Oczekiwany wynik
Otwieranie `PieChartFormatted.docx` pokazuje pojedynczy wykres kołowy:

* Wykres zajmuje obszar 400 × 300 pt.  
* Rozmiar otworu to `0`, więc wykres jest pełnym kołem.  
* Pierwszy wycinek jest wybuchnięty o 20 % i pomalowany na czerwono (jeśli dodałeś opcjonalne formatowanie).  

Masz teraz **utworzony wykres docx**, który może być rozpowszechniany, osadzany w e‑mailach lub dalej edytowany programowo.

---

## Typowe warianty i przypadki brzegowe

| Scenariusz | Jak dostosować kod |
|------------|--------------------|
| **Wiele serii** | Iteruj po `pieChart.getChart().getSeries()` i ustaw `Explosion` lub `FillColor` dla każdej serii. |
| **Dynamiczne dane** | Wypełnij serie wartościami z bazy danych lub pliku CSV przed wywołaniem `setExplosion`. |
| **Inny rozmiar wykresu** | Zmień argumenty szerokości/wysokości w `insertChart(ChartType.PIE, width, height)`. |
| **Eksport do PDF** | Po zapisaniu DOCX, wywołaj `doc.save("output.pdf")`, aby wygenerować wersję PDF tego samego wykresu. |
| **Lokalizacja** | Użyj `DocumentBuilder.insertChart` z formatem liczb specyficznym dla lokalizacji przy etykietach. |

### Pro tip
Zawsze wywołuj `setHoleSize(0)` **po** `insertChart`. Jeśli ustawisz to przed wstawieniem, Aspose.Words przywróci domyślny rozmiar pierścienia po utworzeniu wykresu.

---

## Podsumowanie

Teraz wiesz, jak **wstawić wykres kołowy** do dokumentu Word przy użyciu Java, jak **ustawić rozmiar otworu** dla wyglądu pełnego koła, jak **wybuchnąć wycinek wykresu kołowego**, aby przyciągnąć uwagę, oraz jak **podświetlić wycinek wykresu kołowego** własnymi kolorami. Pełny przykład pokazuje również, jak **utworzyć wykres docx**, który jest gotowy do dystrybucji.

---

## Kolejne kroki

* Poznaj inne typy wykresów (`BAR`, `LINE`, `SCATTER`) przy użyciu `ChartType`.  
* Połącz generowanie wykresów z scalaniem korespondencji (mail merge), aby tworzyć spersonalizowane raporty.  
* Zintegruj wygenerowany DOCX z usługą sieciową, która zwraca plik na żądanie.  

Jeśli napotkasz problemy, pamiętaj, aby sprawdzić, czy używasz kompatybilnej wersji Aspose.Words oraz czy katalog wyjściowy istnieje i jest zapisywalny.

Miłego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z instrukcjami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak stworzyć wykres słupkowy przy użyciu Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Korzystanie z Word Chart API](/words/english/net/programming-with-charts/)
- [Wstaw wykres bąbelkowy w Word przy użyciu Aspose.Words dla .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}