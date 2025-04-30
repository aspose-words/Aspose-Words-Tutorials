---
"description": "Dowiedz się, jak tworzyć i dostosowywać wykresy w Aspose.Words for Java. Poznaj typy wykresów, formatowanie i właściwości osi do wizualizacji danych."
"linktitle": "Korzystanie z wykresów"
"second_title": "Aspose.Words API przetwarzania dokumentów Java"
"title": "Korzystanie z wykresów w Aspose.Words dla Java"
"url": "/pl/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Korzystanie z wykresów w Aspose.Words dla Java


## Wprowadzenie do korzystania z wykresów w Aspose.Words dla Java

W tym samouczku pokażemy, jak pracować z wykresami przy użyciu Aspose.Words for Java. Dowiesz się, jak tworzyć różne typy wykresów, dostosowywać właściwości osi, formatować etykiety danych i nie tylko. Zanurzmy się!

## Tworzenie wykresu liniowego

Aby utworzyć wykres liniowy, użyj następującego kodu:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Usuń domyślnie wygenerowaną serię.
chart.getSeries().clear();

// Dodawanie serii z danymi i etykietami danych.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Lub połącz kod formatu z komórką źródłową.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Tworzenie innych typów wykresów

Możesz tworzyć różne typy wykresów, takie jak kolumnowy, obszarowy, bąbelkowy, punktowy i inne, używając podobnych technik. Oto przykład wstawiania prostego wykresu kolumnowego:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Usuń domyślnie wygenerowaną serię.
chart.getSeries().clear();

// Tworzenie kategorii i dodawanie danych.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Dostosowywanie właściwości osi

Możesz dostosować właściwości osi, takie jak zmiana typu osi, ustawienie znaczników, formatowanie etykiet i wiele więcej. Oto przykład definiowania właściwości osi XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Wyczyść domyślne serie i dodaj swoje dane.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Zmień oś X tak, aby przedstawiała kategorię zamiast daty.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Mierzone w jednostkach wyświetlanych na osi Y (setkach).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Formatowanie etykiet danych

Możesz formatować etykiety danych za pomocą różnych formatów liczb. Oto przykład:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Wyczyść domyślne serie i dodaj swoje dane.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Dodatkowe dostosowania wykresu

Możesz dalej dostosowywać swoje wykresy, dostosowując granice, jednostki interwału między etykietami, ukrywając osie wykresu i nie tylko. Przeglądaj dostarczone fragmenty kodu, aby dowiedzieć się więcej o tych opcjach.

## Wniosek

tym samouczku przyjrzeliśmy się, jak pracować z wykresami przy użyciu Aspose.Words for Java. Nauczyłeś się, jak tworzyć różne typy wykresów, dostosowywać właściwości osi, formatować etykiety danych i nie tylko. Aspose.Words for Java udostępnia potężne narzędzia do dodawania wizualnych reprezentacji danych do dokumentów, ulepszając sposób prezentacji informacji.

## Najczęściej zadawane pytania

### Jak mogę dodać wiele serii do wykresu?

Do wykresu można dodać wiele serii za pomocą `chart.getSeries().add()` metoda. Upewnij się, że określiłeś nazwę serii, kategorie i wartości danych.

### Jak mogę sformatować etykiety danych, używając niestandardowych formatów liczb?

Możesz sformatować etykiety danych, uzyskując dostęp do `DataLabels` właściwości serii i ustawienie żądanego kodu formatu za pomocą `getNumberFormat().setFormatCode()`.

### Jak dostosować właściwości osi na wykresie?

Możesz dostosować właściwości osi, takie jak typ, znaczniki, etykiety i inne, uzyskując dostęp do `ChartAxis` właściwości takie jak `setCategoryType()`, `setCrosses()`, I `setMajorTickMark()`.

### Jak mogę tworzyć inne rodzaje wykresów, np. wykresy punktowe lub wykresy powierzchniowe?

Możesz tworzyć różne typy wykresów, określając odpowiednie `ChartType` podczas wstawiania wykresu za pomocą `builder.insertChart(ChartType.TYPE, width, height)`.

### Jak mogę ukryć oś wykresu?

Możesz ukryć oś wykresu, ustawiając `setHidden(true)` Własność osi.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}