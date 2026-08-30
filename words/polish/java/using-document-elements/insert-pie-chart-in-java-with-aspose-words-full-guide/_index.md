---
category: general
date: 2026-07-29
description: Wstaw wykres kołowy przy użyciu Aspose.Words for Java i dowiedz się,
  jak generować wykres pierścieniowy, formatować wykres kołowy, formatować wykres
  w Wordzie oraz dostosować rozmiar wykresu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: pl
lastmod: 2026-07-29
og_description: Wstaw wykres kołowy przy użyciu Aspose.Words for Java i szybko naucz
  się tworzyć wykres pierścieniowy, formatować wykres kołowy, formatować wykres w
  Wordzie oraz dostosowywać rozmiar wykresu w profesjonalnych dokumentach.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Wstaw wykres kołowy w Javie – Kompletny samouczek Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Wstaw wykres kołowy w Javie z Aspose.Words – pełny przewodnik
url: /pl/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wstaw wykres kołowy w Javie z Aspose.Words – Kompletny przewodnik

Zastanawiałeś się kiedyś, jak **wstawić wykres kołowy** do dokumentu Worda z kodu Java? Nie jesteś jedyny – wielu programistów napotyka ten problem, gdy potrzebują szybkiego, programowego sposobu wizualizacji danych. Dobra wiadomość? Dzięki Aspose.Words for Java możesz to zrobić w zaledwie kilku linijkach, a przy okazji możesz także **generować wykres pierścieniowy**, **formatować wykres kołowy**, **formatować wykres w Wordzie** oraz **dostosować rozmiar wykresu** do swojej marki.

W tym tutorialu przejdziemy przez praktyczny przykład, który zaczyna się od utworzenia pustego dokumentu, wstawienia wykresu kołowego, drobnych modyfikacji wyglądu i w końcu zapisania pliku. Po zakończeniu będziesz mieć gotowy fragment kodu, który możesz wkleić do dowolnego projektu Java wymagającego automatyzacji wykresów. Bez dodatkowych bibliotek, bez ręcznego manipulowania interfejsem Office – po prostu czysta, skompilowana Java.

## Czego będziesz potrzebować

- **Java 17** (lub dowolny nowszy JDK; API jest kompatybilne wstecz)
- **Aspose.Words for Java** 22.12 lub nowszy – możesz pobrać artefakt Maven lub plik .jar ze strony Aspose.
- Skromne IDE (IntelliJ IDEA, Eclipse, VS Code…) – cokolwiek, co pozwala uruchomić metodę `main`.
- Opcjonalnie: plik licencji, jeśli nie chcesz wody znakowej wersji ewaluacyjnej.

Jeśli masz te elementy, możemy od razu przejść do kodu.

## Krok 1: Wstaw wykres kołowy z Aspose.Words

Pierwszą rzeczą, którą robimy, jest **wstawienie wykresu kołowego** do nowego dokumentu. Ten krok przygotowuje scenę dla wszystkiego, co nastąpi, ponieważ obiekt wykresu daje dostęp do serii, punktów danych i ustawień wizualnych.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Dlaczego to ważne:** `DocumentBuilder.insertChart` nie tylko tworzy wykres, ale także zwraca obiekt `Chart`, który możemy modyfikować. Argumenty szerokości i wysokości pozwalają **dostosować rozmiar wykresu** już w momencie tworzenia, więc nie musisz później zmieniać jego wymiarów.

## Krok 2: Generuj wykres pierścieniowy (opcjonalnie)

Jeśli Twój projekt wymaga otworu w środku – pomyśl o klasycznym wykresie pierścieniowym – Aspose robi to w jednej linii. Ten sam obiekt `Chart` można przełączyć z zwykłego koła na pierścień, zmieniając rozmiar otworu.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Wskazówka:** Rozmiar otworu działa tylko dla `ChartType.DONUT`. Jeśli pozostawisz typ jako `PIE`, wywołanie zostanie zignorowane, więc możesz swobodnie eksperymentować.

## Krok 3: Formatuj fragmenty wykresu kołowego

Dobry wykres często podkreśla konkretny fragment. Tutaj **formatujemy wykres kołowy**, „wybuchając” pierwszy kawałek o 20 punktów na zewnątrz. To przyciąga wzrok czytelnika do najważniejszego punktu danych.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Profesjonalna porada:** Możesz przeiterować `pieChart.getSeries()`, jeśli masz wiele serii, i ustawiać indywidualne kolory, obramowania lub etykiety danych. To sposób na **formatowanie wykresu w Wordzie** z bogatym stylem.

## Krok 4: Dodaj dane do wykresu

Wykres bez danych to tylko ozdobny kształt. Dodajmy prosty zestaw – na przykład kwartalne wyniki sprzedaży.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Dlaczego to robimy:** Dodając explicite obiekty `ChartPoint`, zapewniamy, że wykres odzwierciedla naszą logikę biznesową. Wywołania `setShowCategoryName` i `setShowValue` są częścią **formatowania wykresu kołowego**, aby pokazać zarówno etykiety, jak i liczby.

## Krok 5: Dopracuj wygląd (dostosuj rozmiar i styl wykresu)

Poza początkowymi wymiarami, możesz chcieć dostosować legendę, tytuł czy nawet czcionkę używaną w etykietach danych. Wszystko to wchodzi w zakres **dostosowywania rozmiaru wykresu** i ogólnego formatowania.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Przypadek brzegowy:** Jeśli później zdecydujesz się wyeksportować dokument do PDF, wektorowe dane wykresu pozostaną ostre, ponieważ rozmiar jest określony w punktach, a nie w pikselach. To korzyść dla **formatowania wykresu w Wordzie** i formatów downstream.

## Krok 6: Zapisz i otwórz dokument

Ostatni krok jest tak prosty, jak wywołanie `doc.save`. To zapisuje plik `.docx`, który możesz otworzyć w Microsoft Word, LibreOffice lub dowolnym podglądzie obsługującym format OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Rezultat:** Otwórz `PieChart.docx` i zobaczysz ładnie wymiarowany wykres kołowy (lub pierścieniowy) z „wybuchniętym” fragmentem, tytułem i legendą – wszystko wygenerowane bez ręcznej interwencji w UI.

### Oczekiwany wynik

| Element | Co zobaczysz |
|---------|---------------|
| Typ wykresu | Wykres kołowy (lub pierścieniowy, jeśli `holeSize` > 0) |
| Wybuch fragmentu | Pierwszy fragment odsunięty o 20 pt |
| Legenda | Umieszczona po prawej stronie |
| Tytuł | „Quarterly Sales Distribution” pogrubiony, 14 pt |
| Etykiety danych | Nazwa kategorii i wartość wyświetlane na każdym fragmencie |
| Dokument | Standardowy plik Word `.docx` gotowy do udostępnienia |

## Częste pytania i pułapki

- **Czy potrzebna jest licencja?**  
  Wersja ewaluacyjna działa w porządku do testów, ale dodaje znak wodny. Umieść plik `aspose.words.lic` w classpath, aby uzyskać czysty wynik.

- **Czy mogę używać tego z Mavenem?**  
  Oczywiście. Dodaj następującą zależność do swojego `pom.xml`:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Co jeśli mam więcej niż jedną serię?**  
  Przejdź po `pieChart.getSeries()` i zastosuj `setExplosion`, `setFillColor` lub inne formatowanie dla każdej serii. To sposób na **formatowanie wykresu kołowego** dla danych wielowymiarowych.

- **Czy wykres jest edytowalny w Wordzie po wygenerowaniu?**  
  Tak – po zapisaniu możesz otworzyć dokument i ręcznie zmienić kolory, czcionki lub nawet przekształcić wykres kołowy w słupkowy, jeśli zajdzie taka potrzeba.

## Podsumowanie

Właśnie **wstawiliśmy wykres kołowy** do dokumentu Word przy użyciu Aspose.Words for Java, pokazaliśmy, jak **generować wykres pierścieniowy**, zademonstrowaliśmy różne sposoby **formatowania wykresu kołowego**, omówiliśmy najlepsze praktyki **formatowania wykresu w Wordzie** oraz nauczyliśmy się **dostosowywać rozmiar wykresu** dla profesjonalnego wyglądu. Pełny, gotowy do uruchomienia przykład powyżej można wkleić do dowolnego projektu Java, dając natychmiastową automatyzację wykresów bez konieczności używania COM interop czy instalacji Office.

Co dalej? Spróbuj podmienić źródło danych na żywą bazę, dodać warunkowe kolory w zależności od progów lub wyeksportować ten sam dokument do PDF jako gotowy do druku raport. Każdy z tych kroków opiera się na fundamentach, które właśnie zbudowaliśmy, więc przejście będzie płynne.

Jeśli napotkasz problemy lub masz pomysły na dalsze ulepszenia – może wykres słupkowy skumulowany lub liniowy – zostaw komentarz poniżej. Powodzenia w tworzeniu wykresów!

## Co powinieneś nauczyć się dalej?

Poniższe tutoriale obejmują tematy ściśle powiązane, które rozwijają techniki przedstawione w tym przewodniku. Każdy zasób zawiera kompletne, działające przykłady kodu oraz szczegółowe wyjaśnienia, aby pomóc Ci opanować dodatkowe funkcje API i odkrywać alternatywne podejścia w własnych projektach.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}