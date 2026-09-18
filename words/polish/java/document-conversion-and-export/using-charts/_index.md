---
date: 2025-12-13
description: Dowiedz się, jak tworzyć wykres słupkowy i formatować etykiety danych
  wykresu przy użyciu Aspose.Words for Java. Poznaj dodawanie wielu serii, zmianę
  typu osi oraz ukrywanie osi wykresu.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Jak utworzyć wykres słupkowy przy użyciu Aspose.Words dla Javy
url: /pl/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak stworzyć wykres słupkowy przy użyciu Aspose.Words for Java

W tym samouczku **stworzysz wykres słupkowy** wizualizacje bezpośrednio w dokumentach Word przy użyciu Aspose.Words for Java. Przejdziemy przez tworzenie różnych typów wykresów, dodawanie wielu serii, formatowanie etykiet danych wykresu, zmianę typu osi oraz ukrywanie osi wykresu, gdy potrzebny jest czystszy wygląd. Po zakończeniu będziesz mieć solidne, gotowe do produkcji podejście do osadzania bogatych wykresów w swoich dokumentach.

## Szybkie odpowiedzi
- **Jaka jest podstawowa klasa do tworzenia wykresu?** `DocumentBuilder` z `insertChart`.
- **Która metoda dodaje nową serię?** `chart.getSeries().add(...)`.
- **Jak sformatować etykiety danych wykresu?** Użyj `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Czy mogę ukryć oś?** Tak, wywołaj `setHidden(true)` na obiekcie osi.
- **Czy potrzebna jest licencja na Aspose.Words?** Licencja jest wymagana do użytku produkcyjnego; dostępna jest darmowa wersja próbna.

## Czym jest wykres słupkowy i dlaczego go używać?

Wykres słupkowy wyświetla dane kategorialne jako pionowe słupki, co czyni go idealnym do porównywania wartości pomiędzy grupami (sprzedaż w regionie, miesięczne wydatki itp.). W aplikacjach Java generowanie wykresu słupkowego przy użyciu Aspose.Words pozwala osadzać te wizualizacje bezpośrednio w plikach Word / DOCX bez potrzeby korzystania z Excela lub zewnętrznych narzędzi.

## Jak stworzyć wykres słupkowy

Poniżej znajduje się prosty przykład, który tworzy prosty wykres słupkowy. Kod jest identyczny jak w oryginalnym fragmencie – dodaliśmy jedynie komentarze wyjaśniające, aby ułatwić zrozumienie.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Dodaj wiele serii

Możesz **dodać wiele serii** do wykresu słupkowego, wywołując wielokrotnie `chart.getSeries().add(...)`, jak pokazano powyżej. Każda seria może mieć własny zestaw kategorii i wartości, co pozwala porównywać kilka zestawów danych obok siebie.

## Jak stworzyć wykres liniowy z niestandardowymi etykietami danych

Jeśli potrzebujesz wykresu liniowego zamiast słupkowego, obowiązuje ten sam schemat. Ten przykład również pokazuje **formatowanie etykiet danych wykresu** przy użyciu różnych formatów liczbowych.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

### Dodaj etykiety danych

Wywołanie `series1.hasDataLabels(true)` **dodaje etykiety danych** do serii, natomiast `setShowValue(true)` sprawia, że rzeczywiste wartości są widoczne na wykresie.

## Jak zmienić typ osi i dostosować właściwości osi

Zmiana typu osi (np. z daty na kategorię) pozwala kontrolować sposób rysowania punktów danych. Ten fragment kodu również pokazuje, jak **ukryć oś wykresu**, jeśli preferujesz minimalistyczny projekt.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Zmień typ osi

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **zmienia typ osi** z oś opartej na dacie na oś kategorialną, dając pełną kontrolę nad rozmieszczeniem etykiet.

## Jak formatować etykiety danych wykresu (formaty liczbowe)

Możesz zastosować formatowanie liczb bezpośrednio do osi lub etykiet danych. Ten przykład formatuje liczby na osi Y przy użyciu separatora tysięcy.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Dodatkowe dostosowania wykresu

Poza podstawami możesz dostosować granice, ustawić jednostki interwału między etykietami, ukrywać konkretne osie i wiele więcej. Odwołaj się do dokumentacji API Aspose.Words for Java, aby uzyskać pełną listę właściwości.

## Najczęściej zadawane pytania

**Q: Jak mogę dodać wiele serii do wykresu?**  
A: Użyj `chart.getSeries().add()` dla każdej serii, którą chcesz wyświetlić. Każde wywołanie może dostarczyć unikalną nazwę, tablicę kategorii i tablicę wartości.

**Q: Jak sformatować etykiety danych wykresu przy użyciu niestandardowych formatów liczbowych?**  
A: Uzyskaj dostęp do obiektu `DataLabels` serii i wywołaj `getNumberFormat().setFormatCode("your format")`. Możesz także powiązać format z komórką źródłową przy użyciu `isLinkedToSource(true)`.

**Q: Jak mogę ukryć oś wykresu?**  
A: Wywołaj `setHidden(true)` na obiekcie `ChartAxis`, który chcesz ukryć (np. `chart.getAxisY().setHidden(true)`).

**Q: Jaki jest najlepszy sposób na zmianę typu osi?**  
A: Użyj `setCategoryType(AxisCategoryType.CATEGORY)` dla osi kategorialnych lub `AxisCategoryType.DATE` dla osi datowych.

**Q: Jak dodać etykiety danych do serii?**  
A: Włącz je za pomocą `series.hasDataLabels(true)`, a następnie skonfiguruj widoczność używając `series.getDataLabels().setShowValue(true)`.

## Podsumowanie

Omówiliśmy wszystko, co potrzebne, aby **stworzyć wykres słupkowy** wizualizacje przy użyciu Aspose.Words for Java — od wstawiania podstawowych wykresów i dodawania wielu serii, po formatowanie etykiet danych wykresu, zmianę typu osi oraz ukrywanie osi wykresu dla czystego wyglądu. Włącz te techniki do swoich procesów raportowania lub generowania dokumentów, aby dostarczać profesjonalne, oparte na danych dokumenty Word.

---

**Ostatnia aktualizacja:** 2025-12-13  
**Testowano z:** Aspose.Words for Java 24.12 (latest)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}