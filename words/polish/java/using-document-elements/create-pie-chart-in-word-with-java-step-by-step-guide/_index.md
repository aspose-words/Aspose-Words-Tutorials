---
category: general
date: 2026-08-14
description: Utwórz wykres kołowy w Wordzie przy użyciu Javy i Aspose.Words. Dowiedz
  się, jak dodać dane serii do wykresu i obrócić fragment wykresu kołowego w kilku
  linijkach.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: pl
lastmod: 2026-08-14
og_description: Utwórz wykres kołowy w programie Word przy użyciu języka Java i biblioteki
  Aspose.Words. Ten samouczek pokazuje, jak dodać dane serii do wykresu oraz szybko
  obrócić fragment wykresu kołowego.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Tworzenie wykresu kołowego w Wordzie przy użyciu Javy – kompletny przewodnik
  kodowania
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Tworzenie wykresu kołowego w Wordzie przy użyciu Javy – przewodnik krok po
  kroku
url: /pl/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utwórz wykres kołowy w Wordzie przy użyciu Java – przewodnik krok po kroku

Jeśli potrzebujesz **utworzyć wykres kołowy w Wordzie** programowo, ten przewodnik pokaże Ci dokładnie, jak to zrobić w Javie i Aspose.Words. Poznasz kompletny przepływ pracy, od wstawiania wykresu po dodawanie punktów danych i obracanie pierwszego segmentu.

Generowanie wykresu bezpośrednio w pliku `.docx` eliminuje ręczny krok kopiuj‑wklej i pozwala automatyzować raporty, faktury lub pulpity. Po drodze omówimy także **jak dodać dane serii do wykresu** oraz **jak obrócić segment wykresu kołowego** dla lepszego podkreślenia wizualnego.

## Tworzenie wykresu kołowego w Wordzie – przegląd

Aspose.Words for Java udostępnia płynne API `DocumentBuilder`, które może wstawić obiekt wykresu do dokumentu Word. Wybrany typ wykresu określa domyślny układ, a Ty możesz dostosować serie, kolory, kąty i nawet przełączyć się na kształt pierścienia (doughnut) jednym wywołaniem metody.

### Dlaczego warto używać Aspose.Words?

* **No Microsoft Office required** – biblioteka działa na dowolnym serwerze lub w środowisku CI.  
* **Full .docx fidelity** – wygenerowany wykres wygląda identycznie jak ten utworzony ręcznie w Wordzie.  
* **Single‑file dependency** – wystarczy dodać plik JAR i jesteś gotowy do pracy.

## Jak dodać dane serii do wykresu

Wykres bez danych to tylko placeholder. Obiekt `Chart` udostępnia kolekcję `Series`; każda seria zawiera listę wartości liczbowych, które mapują się na segmenty (dla wykresu kołowego) lub punkty (dla wykresu liniowego). Dodawanie danych jest proste:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Co robi kod:**  
* `chart.getSeries()` zwraca `List<ChartSeries>`.  
* `get(0)` wybiera pierwszą serię, ponieważ wykres kołowy definiuje się jako posiadający tylko jedną serię.  
* `add(double)` dodaje punkt danych. Wartości są automatycznie konwertowane na procenty, które sumują się do 100 % przy renderowaniu wykresu.

> **Pro tip:** Jeśli Twoje źródło danych zawiera więcej niż trzy kategorie, kontynuuj dodawanie wartości w ten sam sposób. Aspose.Words automatycznie utworzy dodatkowe segmenty.

## Obróć segment wykresu kołowego

Czasami chcesz, aby konkretny segment zaczynał się pod określonym kątem, tak aby najważniejszy segment był skierowany w stronę widza. Metoda `setFirstSliceAngle(double)` obraca cały wykres, efektywnie przesuwając początek pierwszego segmentu:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

Kąt jest mierzony w stopniach zgodnie z ruchem wskazówek zegara od osi pionowej. Ustawienie go na `0` (wartość domyślna) umieszcza pierwszy segment na górze. Dostosuj wartość, aby podkreślić segment lub dopasować się do wytycznych projektowych.

> **Common question:** *Czy obracanie wpływa na kolejność danych?*  
> Nie. Kolejność danych pozostaje taka sama; zmienia się tylko wizualna pozycja początkowa.

## Pełny przykład w Javie

Poniżej znajduje się kompletny, gotowy do uruchomienia program, który tworzy dokument Word z wykresem kołowym, dodaje dane serii, obraca segment i zapisuje plik. Wszystkie wymagane importy są wymienione, więc możesz skopiować kod do dowolnego IDE.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Oczekiwany wynik

* Plik o nazwie **PieChart.docx** pojawia się w folderze `output`.  
* Otwierając plik w Microsoft Word, widzisz kolorowy wykres kołowy z trzema segmentami (40 %, 30 %, 30 %).  
* Wykres jest obrócony o 45° zgodnie z ruchem wskazówek zegara, więc pierwszy segment zaczyna się nieco w prawo od osi pionowej.

## Typowe pułapki i najlepsze praktyki

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| **Wykres jest pusty** | Dokument został zapisany przed pełnym wyrenderowaniem wykresu. | Wywołaj `doc.save()` **po** wszystkich modyfikacjach wykresu. |
| **Wartości segmentów nie sumują się do 100 %** | Dodawanie surowych liczb, które nie reprezentują procentów, może prowadzić do nieoczekiwanego skalowania. | Podaj wartości, które logicznie reprezentują części całości, lub pozwól Aspose.Words automatycznie obliczyć procenty. |
| **Obrót nie ma efektu** | Użycie `ChartType.DOUGHNUT` bez ustawienia `holeSize` może ukryć efekt obrotu. | Utrzymaj wykres jako `PIE` lub dostosuj `holeSize` po ustawieniu kąta. |
| **Błędy ścieżki pliku** | Ścieżki względne mogą być rozwiązywane inaczej w systemie Windows niż Linux. | Użyj `Paths.get("output", "PieChart.docx").toString()` lub ścieżki bezwzględnej w kodzie produkcyjnym. |

### Wskazówki do użytku produkcyjnego

* **Reuse the `DocumentBuilder`** – możesz wstawiać wiele wykresów w tym samym dokumencie, wywołując `insertChart` wielokrotnie.  
* **Styling** – użyj `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`, aby wyświetlić procenty bezpośrednio na wykresie.  
* **Performance** – wygeneruj wykres raz i sklonuj go (`chart.deepClone()`), jeśli potrzebujesz identycznych wykresów w wielu miejscach.

## Obrócenie segmentu wykresu kołowego – zaawansowane scenariusze

* **Dynamic angle** – oblicz kąt na podstawie danych (np. aby największy segment zaczynał się na górze).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Multiple series** – choć wykres kołowy zazwyczaj ma jedną serię, Aspose.Words pozwala dodać więcej dla wykresów warstwowych. Obrót nadal dotyczy tylko pierwszej serii.

## Podsumowanie

Teraz wiesz, jak **utworzyć wykres kołowy w Wordzie** przy użyciu Java, jak **dodać dane serii do wykresu**, oraz jak **obrócić segment wykresu kołowego** dla podkreślenia wizualnego. Pełny przykład demonstruje cały przepływ pracy — od inicjalizacji dokumentu po zapisanie końcowego pliku `.docx` — dzięki czemu możesz zintegrować generowanie wykresów z dowolnym zautomatyzowanym pipeline'em raportowania.

### Co dalej?

* Zbadaj inne typy wykresów (`ChartType.BAR`, `ChartType.LINE`), aby poszerzyć swój zestaw narzędzi automatyzacji.  
* Połącz generowanie wykresów z **mail merge**, aby tworzyć spersonalizowane raporty dla każdego odbiorcy.  
* Zanurz się w **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`), aby dopasować wykresy do identyfikacji wizualnej Twojej firmy.

Śmiało eksperymentuj z różnymi zestawami danych, kątami i stylami wykresów. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każde źródło zawiera kompletne działające przykłady kodu z wyjaśnieniami krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [Jak utworzyć wykres słupkowy przy użyciu Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Jak utworzyć pola formularza i dodać zawartość przy użyciu DocumentBuilder w Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak konwertować Word do PDF przy użyciu Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}