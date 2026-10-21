---
category: general
date: 2026-07-16
description: Utwórz wykres kołowy w Javie przy użyciu Aspose.Words. Dowiedz się, jak
  dodać linie prowadzące, wyświetlić legendę wykresu i oddzielić wycinek w jednym
  samouczku.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: pl
lastmod: 2026-07-16
og_description: Utwórz wykres kołowy w Javie przy użyciu Aspose.Words. Ten przewodnik
  pokazuje, jak dodać linie prowadzące, wyświetlić legendę wykresu oraz wydzielić
  fragment, zapewniając elegancki wygląd w kilka minut.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Tworzenie wykresu kołowego w Aspose.Words Java – Kompletny samouczek formatowania
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Tworzenie wykresu kołowego przy użyciu Aspose.Words Java – Pełny przewodnik
  krok po kroku
url: /pl/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tworzenie wykresu kołowego w Aspose.Words Java – Pełny przewodnik krok po kroku

Czy kiedykolwiek zastanawiałeś się, jak **utworzyć wykres kołowy** programowo w Javie, nie walcząc z niskopoziomowymi API rysowania? Nie jesteś jedyny. Wielu programistów potrzebuje szybkiej wizualizacji do raportów, pulpitów nawigacyjnych lub automatycznych dokumentów i sięga po Aspose.Words, ponieważ zajmuje się ciężką pracą.  

W tym samouczku przeprowadzimy Cię przez kompletny, gotowy do uruchomienia przykład, który nie tylko **tworzy wykres kołowy**, ale także pokazuje, jak **dodać linie prowadzące**, **wyświetlić legendę wykresu** i nawet **wybuchnąć fragment** w celu podkreślenia. Po zakończeniu będziesz mieć plik `.docx`, który wygląda na wystarczająco dopracowany, aby zaimponować klientowi.

> **Szybki sukces:** Poniższy fragment kodu działa od razu z Aspose.Words for Java 23.9 (lub nowszą wersją). Bez dodatkowych zależności, tylko plik JAR.

## Czego się nauczysz

- Utwórz pusty dokument Word przy użyciu `DocumentBuilder`.
- Wstaw **wykres kołowy** o niestandardowym rozmiarze.
- Skorzystaj z funkcji **wybuchnięcia fragmentu**, aby wyróżnić punkt danych.
- Włącz **linie prowadzące**, aby wybuchnięty fragment pozostał połączony z etykietą.
- Włącz **legendę wykresu**, aby czytelnicy mogli od razu zidentyfikować każdy fragment.
- Zapisz wynik do pliku `.docx`, który możesz otworzyć w Microsoft Word lub LibreOffice.

**Wymagania wstępne** – Będziesz potrzebować:

1. Zainstalowaną Javę 17 (lub nowszą).
2. JAR Aspose.Words for Java w classpath.
3. Podstawowe IDE lub edytor tekstu — IntelliJ IDEA, Eclipse, VS Code, cokolwiek wolisz.

Teraz zanurzmy się.

## Krok 1: Inicjalizacja dokumentu i buildera – Przygotowanie do **utworzenia wykresu kołowego**

Najpierw potrzebujemy czystego płótna dokumentu. `Document` reprezentuje cały plik Word, natomiast `DocumentBuilder` jest pomocnikiem, który pozwala nam dodawać zawartość.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Dlaczego to ważne:** Rozpoczęcie od nowego `Document` zapewnia brak ukrytych stylów lub pozostałych obiektów, które mogłyby zakłócić renderowanie wykresu.

## Krok 2: Wstawienie **wykresu kołowego** – Rozmiar ma znaczenie

Aspose.Words umożliwia wstawienie wykresu w jednej linii. Tutaj prosimy o wykres kołowy o wymiarach 400 × 300 punktów — w przybliżeniu 5,5 × 4,2 cala na typowym ekranie.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Wskazówka:** Jeśli potrzebujesz innego rozmiaru, po prostu zmień dwa argumenty liczbowe. API działa w punktach, gdzie 72 punkty = 1 cal.

## Krok 3: **Jak wybuchnąć fragment** – Podkreślenie kluczowego punktu danych

Wybuchnięcie fragmentu wyciąga go z reszty koła, przyciągając uwagę czytelnika. Metoda `setExplosion` przyjmuje liczbę całkowitą określającą odległość w punktach.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Co jeśli masz wiele serii?** Możesz wywołać `setExplosion` na dowolnym indeksie serii (`get(1)`, `get(2)`, …), aby wybuchnąć różne fragmenty.

## Krok 4: **Dodaj linie prowadzące** i **pokaż legendę wykresu** – Łączenie punktów

Gdy fragment jest wybuchnięty, etykieta może się oddalić. Linie prowadzące utrzymują etykietę przyczepioną, zachowując czytelność. Jednocześnie legenda zapewnia szybki klucz do wszystkich fragmentów.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Dlaczego włączyć linie prowadzące?** Bez nich etykieta może wydawać się unosząca, wprowadzając użytkowników w błąd co do tego, do którego fragmentu należy.  
> **Potrzebujesz niestandardowej pozycji legendy?** Użyj `chart.getLegend().setPosition(LegendPosition.TOP)` lub dowolnej innej wartości wyliczeniowej.

## Krok 5: Zapisz dokument – Ostatni krok **tworzenia wykresu kołowego**

Na koniec zapisujemy dokument na dysku. Dostosuj ścieżkę do folderu, do którego masz prawo zapisu.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Uruchom program, otwórz wygenerowany plik `PieChartDemo.docx`, a zobaczysz ładnie sformatowany wykres kołowy z wybuchniętym pierwszym fragmentem, liniami prowadzącymi i widoczną legendą.

![Przykład wykresu kołowego pokazujący wybuchnięty fragment i legendę](pie-chart-example.png){: .center-image alt="Utwórz przykład wykresu kołowego z wybuchniętym fragmentem, liniami prowadzącymi i legendą"}

### Oczekiwany wynik

Gdy otworzysz plik Word, wykres wygląda mniej więcej tak:

- Wykres kołowy 400 × 300 pt.
- Pierwszy fragment jest odsunięty o 10 pt.
- Cienka linia prowadząca łączy wybuchnięty fragment z jego etykietą.
- Legenda pod wykresem wymienia nazwę każdej serii.

Jeśli nie widzisz linii prowadzącej, sprawdź dwukrotnie, czy `setLeaderLines(true)` jest wywoływane *po* ustawieniu wybuchnięcia — kolejność ma znaczenie.

## Częste pułapki i jak ich uniknąć

| Problem | Dlaczego się dzieje | Rozwiązanie |
|-------|----------------|-----|
| **No legend appears** | `setShowLegend(true)` was omitted or called on the wrong chart object. | Ensure you call `chart.setShowLegend(true)` **after** retrieving the `Chart` from the shape. |
| **Leader line missing** | The slice wasn’t exploded, or the chart type doesn’t support leader lines. | Only `ChartType.PIE` (or `PIE_3D`) supports leader lines. Call `setExplosion` first, then `setLeaderLines(true)`. |
| **Slice doesn’t move** | Explosion value too low (0‑2 pt). | Increase the integer, e.g., `setExplosion(10)` or higher for a more dramatic effect. |
| **Chart looks distorted** | Using a non‑square size (width ≠ height) can squash the pie. | Keep width and height equal or close; 400 × 300 works but 400 × 400 gives a perfect circle. |

## Zaawansowane dopasowania (opcjonalnie)

Jeśli chcesz wyjść poza podstawy, rozważ:

- **Niestandardowe kolory**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Etykiety danych**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **Efekt 3‑D**: Zamień `ChartType.PIE` na `ChartType.PIE_3D`.

Te opcje pozwalają precyzyjnie dostroić wygląd, aby pasował do wytycznych marki korporacyjnej.

## Podsumowanie – Co osiągnęliśmy

Zaczęliśmy od pustego dokumentu Word, **utworzyliśmy wykres kołowy**, **wybuchnęliśmy pierwszy fragment**, **dodaliśmy linie prowadzące** i **wyświetliliśmy legendę wykresu**. Cały przepływ mieści się w zwięzłej metodzie `main`, co ułatwia wstawienie go do większych potoków raportowania.

## Kolejne kroki

- **Dodaj więcej serii**: Wypełnij wykres rzeczywistymi danymi z bazy danych lub pliku CSV.
- **Eksportuj do PDF**: Użyj `doc.save("output.pdf", SaveFormat.PDF);`, aby wygenerować wersję PDF.
- **Połącz z innymi kształtami**: Wstaw tabele, obrazy lub dodatkowe wykresy, aby uzyskać pełny raport.

Jeśli jesteś ciekawy innych typów wykresów — kolumnowy, słupkowy, liniowy — po prostu zamień `ChartType.PIE` na odpowiedni enum i postępuj zgodnie z tymi samymi krokami formatowania.

*Szczęśliwego wykreślania!* Śmiało zostaw komentarz, jeśli coś nie działało zgodnie z oczekiwaniami, lub podziel się, jak dostosowałeś pozycję legendy. Twoja opinia pomaga nam wszystkim tworzyć lepsze automatyczne dokumenty.

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują ściśle powiązane tematy, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}