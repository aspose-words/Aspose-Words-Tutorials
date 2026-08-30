---
category: general
date: 2026-08-20
description: Szybko dodaj linie prowadzące do wykresu kołowego w Javie. Dowiedz się,
  jak wstawiać, rozdzielać, zmieniać kolory i oznaczać kawałki przy użyciu API wykresów.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: pl
lastmod: 2026-08-20
og_description: Dodaj linie prowadzące do wykresu kołowego w Javie w krótkim przykładzie.
  Postępuj zgodnie z tym przewodnikiem, aby wstawiać, rozdzielać, zmieniać kolory
  i etykietować kawałki przy użyciu API wykresów.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Dodaj linie prowadzące do wykresu kołowego w Javie – przewodnik krok po
  kroku po Chart API
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Jak dodać linie prowadzące do wykresu kołowego w Javie przy użyciu API wykresów
url: /pl/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak dodać linie prowadzące do wykresu kołowego w Javie przy użyciu Chart API

Jeśli potrzebujesz **dodać linie prowadzące do wykresu kołowego** w Javie, ten przewodnik przeprowadzi Cię przez cały proces. Zobaczysz, jak wstawić wykres kołowy, „wybuchnąć” (explode) wycinek dla podkreślenia, zmienić jego kolor oraz w końcu włączyć linie prowadzące, które opisują wycinek.

Przykład wykorzystuje standardowy Chart API dostępny w wielu bibliotekach raportujących dla Javy. Nie są wymagane żadne zewnętrzne narzędzia, a kod działa w każdym środowisku JDK 8+.

## Co osiągniesz

Pod koniec tego samouczka będziesz potrafił:

* Utworzyć `Chart` typu `ChartType.PIE` o niestandardowym rozmiarze.  
* „Wybuchnąć” pierwszy wycinek, aby przyciągnąć uwagę.  
* Ustawić kolor sektora wybuchniętego wycinka na niebieski.  
* **Dodać linie prowadzące do wykresu kołowego**, aby etykieta wycinka była wyraźnie połączona.

Powinieneś już mieć projekt Javy z biblioteką Chart na classpath. Jeśli używasz Maven, dodaj zależność podaną w sekcji wymagań wstępnych.

## Wymagania wstępne

* Zainstalowany JDK 8 lub nowszy.  
* Biblioteka Chart (np. `com.example.chart:chart-api:2.5.0`).  
* Podstawowa znajomość klas Javy i wywołań metod.

---

## Jak dodać linie prowadzące do wykresu kołowego

Poniżej znajduje się pełny, gotowy do uruchomienia program, który demonstruje każdy krok. Kod jest celowo samodzielny, więc możesz go skopiować, wkleić i uruchomić bez modyfikacji.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Wyjaśnienie poszczególnych kroków

| Krok | Co robi kod | Dlaczego to ważne |
|------|-------------|-------------------|
| **1️⃣ Wstaw wykres kołowy** | `builder.insertChart(ChartType.PIE, 400, 300)` tworzy wykres kołowy o wymiarach 400 × 300 pikseli. | Tworzy kontener wykresu i definiuje jego wymiary, co wpływa na rozmieszczenie etykiet i długość linii prowadzących. |
| **2️⃣ Wybuchnij pierwszy wycinek** | `setExplosion(20)` odsuwa wycinek o 20 % promienia. | Wybuchnięty wycinek przyciąga wzrok i sprawia, że linia prowadząca jest widoczna. |
| **3️⃣ Ustaw kolor sektora** | `setSectorColor(Color.BLUE)` zmienia wypełnienie wycinka na niebieskie. | Kontrast kolorów poprawia czytelność, szczególnie gdy wycinek jest podświetlony. |
| **4️⃣ Włącz linie prowadzące** | `setLeaderLines(true)` włącza linie łączące wycinek z jego etykietą. | Linie prowadzące zapewniają czytelność etykiety nawet po odsunięciu wycinka na zewnątrz. |

Wywołanie `saveAsPng` jest opcjonalne, ale przydatne do weryfikacji wyniku wizualnego. Po uruchomieniu programu powinieneś zobaczyć obraz podobny do tego poniżej.

![Add leader lines to pie chart](https://example.com/assets/pie-leader-lines.png "Add leader lines to pie chart – exploded slice with blue color and leader lines")

*Rysunek: Wykres kołowy, w którym pierwszy wycinek jest wybuchnięty, niebieski i połączony z etykietą linią prowadzącą.*

## Dostosowywanie linii prowadzących (zaawansowane)

Podstawowe wywołanie `setLeaderLines(true)` używa domyślnego stylu biblioteki. Możesz dodatkowo kontrolować wygląd:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Opcje te są przydatne, gdy musisz dopasować wykres do identyfikacji wizualnej firmy lub poprawić dostępność.

### Obsługa wielu serii

Jeśli Twój wykres kołowy zawiera więcej niż jedną serię, możesz chcieć linie prowadzące tylko dla konkretnego wycinka. Użyj indeksu serii, aby trafić w odpowiedni element:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Gdy wycinek nie jest wybuchnięty, linia prowadząca jest zazwyczaj automatycznie ukryta, ale możesz wymusić jej wyświetlenie za pomocą `setLeaderLineEnabled(true)`.

## Typowe pułapki i jak ich unikać

| Pułapka | Objaw | Rozwiązanie |
|--------|-------|--------------|
| **Linie prowadzące niewidoczne** | Wykres renderuje się bez łączników. | Upewnij się, że wycinek jest wybuchnięty (`setExplosion` > 0) lub wyraźnie włącz linie prowadzące na wycinku. |
| **Nakładanie się etykiet** | Etykiety kolidują ze sobą. | Zwiększ rozmiar wykresu lub ustaw `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Kolor nie zastosowany** | Wycinek pozostaje w domyślnym kolorze. | Sprawdź, czy odwołujesz się do właściwego indeksu serii (`getSeries().get(0)`). |
| **Obraz nie zapisuje się** | `saveAsPng` zgłasza wyjątek. | Sprawdź uprawnienia zapisu w katalogu wyjściowym oraz czy biblioteka obsługuje eksport do PNG. |

Rozwiązanie tych problemów na wczesnym etapie zapobiega niespodziewanym błędom w czasie działania i daje dopracowany wykres.

## Pełny listing źródłowy

Dla wygody, oto ponownie kompletny plik źródłowy, łącznie z importami i komentarzami:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Uruchomienie tego programu generuje plik `pie-with-leader-lines.png`, który przedstawia wykres kołowy z wybuchniętym niebieskim wycinkiem i wyraźnymi liniami prowadzącymi wskazującymi etykietę wycinka.

## Podsumowanie

Teraz wiesz, jak **dodać linie prowadzące do wykresu kołowego** w Javie przy użyciu Chart API. Proces polega na wstawieniu `ChartType.PIE`, wybuchnięciu wybranego wycinka, dostosowaniu jego koloru oraz włączeniu linii prowadzących. Dzięki opcjonalnym ustawieniom stylu możesz precyzyjnie dostroić kolor linii, grubość i położenie etykiet, aby spełnić dowolne wymagania wizualne.

Następnie rozważ zgłębienie tematów takich jak **pie chart explosion Java**, **set sector color Chart API** oraz **builder.insertChart usage**, aby tworzyć bardziej zaawansowane wizualizacje, np. wykresy pierścieniowe, warstwowe koła lub interaktywne pulpity nawigacyjne.

Śmiało eksperymentuj z różnymi indeksami wycinków, kolorami i stylami linii prowadzących — Twoje wykresy będą coraz bardziej informacyjne i atrakcyjne wizualnie. Powodzenia w kodowaniu!

## Co powinieneś nauczyć się dalej?

Poniższe samouczki obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz wyjaśnienia krok po kroku, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia implementacyjne w własnych projektach.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Add Date Time Values To Axis Of A Chart](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}