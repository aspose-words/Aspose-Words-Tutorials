---
category: general
date: 2026-11-15
description: Dowiedz się, jak stworzyć wykres kołowy w dokumencie Word i zapisać plik docx
  jako PDF przy użyciu Javy. Ten przewodnik obejmuje także konwersję Worda do PDF
  oraz sposób dodawania wykresu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: pl
lastmod: 2026-11-15
og_description: Utwórz wykres kołowy w pliku Word i zapisz docx jako PDF przy użyciu
  Javy. Postępuj zgodnie z tym krok po kroku poradnikiem, aby przekonwertować Word
  na PDF i dodać wykresy.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Tworzenie wykresu kołowego w Wordzie i zapisywanie pliku docx jako PDF –
  przewodnik Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Jak stworzyć wykres kołowy w Wordzie i zapisać plik docx jako PDF
url: /pl/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak utworzyć wykres kołowy w Wordzie i zapisać docx jako PDF

Jeśli potrzebujesz **utworzyć wykres kołowy** w dokumencie Word i następnie **zapisać docx jako PDF**, ten tutorial pokaże Ci dokładnie, jak to zrobić. Zobaczysz kompletny, działający przykład, który konwertuje plik .docx na PDF, jednocześnie osadzając wykres kołowy, dzięki czemu możesz odpowiedzieć na pytanie „jak dodać wykres” bez poszukiwania rozproszonych fragmentów kodu.

W tym przewodniku nauczysz się:

* Wczytać istniejący *.docx* (lub rozpocząć od zera)  
* Użyć Aspose.Words for Java do **utworzenia wykresu kołowego** i wypełnienia danymi  
* **Zapisz docx jako PDF** z prawidłowo renderowanym wykresem  
* Zrozumieć niuanse **konwersji Word do PDF** gdy w grę wchodzą wykresy  

Kroki działają z Aspose.Words 2024‑x.x i Java 17, ale koncepcje mają zastosowanie do każdej biblioteki obsługującej manipulację wykresami w Wordzie.

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz:

| Wymaganie | Dlaczego jest ważne |
|-----------|----------------------|
| Java 17 (lub nowsza) | Wymagane przez najnowszy JAR Aspose.Words |
| Narzędzie budowania Maven lub Gradle | Uproszcza zarządzanie zależnościami |
| Aspose.Words for Java (najnowsza wersja) | Dostarcza klasy `Document`, `Chart` i `ChartType` |
| Plik wejściowy **.docx** (lub pusty dokument) | Wykres zostanie wstawiony do tego pliku |

Dodaj zależność Aspose.Words do swojego `pom.xml` (Maven) lub `build.gradle` (Gradle). Przykład dla Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Krok 1: Wczytaj dokument Word (lub utwórz nowy)

Pierwszym działaniem jest uzyskanie instancji `Document`. Jeśli masz już szablon, podaj jego ścieżkę; w przeciwnym razie utwórz pusty dokument.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Dlaczego ten krok?* Obiekt `Document` jest kontenerem dla całej zawartości Word, w tym wykresów. Wczytanie istniejącego pliku pozwala zachować otaczający tekst i style, jednocześnie dodając nowy element wizualny.

## Krok 2: **Utworzyć wykres kołowy** – sedno „jak utworzyć wykres”

Teraz tworzymy obiekt `Chart` z `ChartType.PIE`. Automatycznie tworzy to miejsce na wykres kołowy, które później możesz wypełnić danymi.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Wyjaśnienie*: `ChartType.PIE` informuje Aspose.Words, aby użył szablonu wykresu kołowego. Wykres jest dodawany do ciała dokumentu, więc pojawia się w miejscu, w którym go potrzebujesz. Spełnia to wymóg „jak dodać wykres” w jednym wywołaniu.

## Krok 3: Wypełnij wykres – odpowiedź na „jak dodać wykres” danymi

Wykres kołowy jest bezwartościowy bez danych serii. Użyj kolekcji `Series`, aby dodać kategorie i wartości.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Dlaczego to ważne*: Każde wywołanie `add` tworzy kawałek wykresu kołowego. Pierwszy argument to etykieta, drugi to wartość liczbowa. Możesz je zastąpić dynamicznymi danymi z bazy danych lub pliku CSV.

### Opcjonalnie: Dostosuj wygląd (nie wymagane, ale przydatne)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Te poprawki ilustrują, jak możesz **utworzyć wykres** z profesjonalnym wyglądem, nie opuszczając kodu Java.

## Krok 4: **Zapisz docx jako PDF** – ostatnia część „konwersji Word do PDF”

Po osadzeniu wykresu wyeksportuj dokument do PDF. Aspose.Words renderuje wykres jako grafikę wektorową, zachowując jakość.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Kluczowy punkt*: Metoda `save` automatycznie konwertuje plik Word na PDF, obsługując rasteryzację wykresu, osadzanie czcionek i układ stron. Spełnia to cel **zapisania docx jako pdf** i demonstruje niezawodny sposób **konwersji Word do PDF**, gdy w dokumencie znajdują się wykresy.

### Oczekiwany wynik

Uruchomienie programu generuje `output.pdf`, który zawiera:

* Oryginalną zawartość `input.docx` (jeśli istnieje)  
* W pełni renderowany wykres kołowy zatytułowany *Sales Distribution Q1*  
* Dokładne procenty kawałków odpowiadające danym (40 %, 30 %, 30 %)

Otwórz PDF w dowolnym przeglądarce i powinieneś zobaczyć wyraźny wykres kołowy, identyczny z tym, który widzisz w pliku Word.

## Częste pułapki i jak ich uniknąć

| Problem | Przyczyna | Rozwiązanie |
|---------|-----------|-------------|
| Wykres pojawia się pusty w PDF | Brak ustawień czcionki lub renderowania wykresu | Upewnij się, że używasz najnowszej wersji Aspose.Words; zawiera ona wymagane biblioteki renderujące. |
| Wartości danych są niepoprawnie zaokrąglane | Używanie wartości całkowitych przy dużych liczbach | Podaj wartości `double` lub przeskaluj liczby przed dodaniem ich do serii. |
| Plik PDF jest ogromny | Obrazy osadzone w wysokim DPI | Ustaw `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)`, jeśli również osadzasz obrazy. |
| „convert word to pdf” rzuca `UnsupportedOperationException` | Używanie starszej wersji Java (< 11) | Uaktualnij do Java 17 lub nowszej, której wymaga Aspose.Words 24.x. |

## Porada: Ponowne użycie logiki tworzenia wykresu

Jeśli potrzebujesz dodać wiele wykresów do tego samego dokumentu, wyodrębnij kod budujący wykres do metody pomocniczej:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Teraz możesz wywołać `doc.getFirstSection().getBody().appendChild(createPieChart(...));` dla każdego zestawu danych, utrzymując kod w zasadzie DRY (Nie Powtarzaj Siebie).

## Zakończenie

Teraz wiesz, jak **utworzyć wykres kołowy** w dokumencie Word, wypełnić go danymi i **zapisać docx jako PDF** przy użyciu Javy. Ten kompleksowy przykład obejmuje cały przepływ **konwersji Word do PDF**, odpowiada na pytanie **jak dodać wykres**, i demonstruje **jak utworzyć wykres** programowo.  

Od tego miejsca możesz zbadać:

* Dodawanie wykresów słupkowych lub liniowych (`ChartType.BAR`, `ChartType.LINE`) – kolejny scenariusz **jak utworzyć wykres**.  
* Eksport do innych formatów, takich jak PNG lub HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Dynamiczne generowanie dokumentu wejściowego z tabelami lub znacznikami przed wstawieniem wykresów.

Śmiało eksperymentuj z różnymi zestawami danych, opcjami stylizacji lub nawet osadzaniem wielu wykresów na jednej stronie. Szczęśliwego kodowania!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i zbadać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak wstawić wykres kołowy do dokumentu Word przy użyciu Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Jak zapisać Word jako PDF i utworzyć dostępny PDF w Javie](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Jak utworzyć wykres w Wordzie przy użyciu Java i Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}