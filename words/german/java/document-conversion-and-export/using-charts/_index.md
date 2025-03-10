---
title: Verwenden von Diagrammen in Aspose.Words für Java
linktitle: Verwenden von Diagrammen
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie in Aspose.Words für Java Diagramme erstellen und anpassen. Erkunden Sie Diagrammtypen, Formatierungen und Achseneigenschaften zur Datenvisualisierung.
weight: 12
url: /de/java/document-conversion-and-export/using-charts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Diagrammen in Aspose.Words für Java


## Einführung in die Verwendung von Diagrammen in Aspose.Words für Java

In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für Java mit Diagrammen arbeiten. Sie erfahren, wie Sie verschiedene Diagrammtypen erstellen, Achseneigenschaften anpassen, Datenbeschriftungen formatieren und vieles mehr. Lassen Sie uns eintauchen!

## Erstellen eines Liniendiagramms

Um ein Liniendiagramm zu erstellen, verwenden Sie den folgenden Code:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Standardmäßig generierte Serien löschen.
chart.getSeries().clear();

// Hinzufügen einer Reihe mit Daten und Datenbeschriftungen.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Oder verknüpfen Sie Formatcode mit einer Quellzelle.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Erstellen anderer Diagrammtypen

Sie können mit ähnlichen Techniken verschiedene Diagrammtypen wie Säulen-, Flächen-, Blasen-, Streudiagramme und mehr erstellen. Hier ist ein Beispiel für das Einfügen eines einfachen Säulendiagramms:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Standardmäßig generierte Serien löschen.
chart.getSeries().clear();

// Kategorien erstellen und Daten hinzufügen.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Anpassen der Achseneigenschaften

Sie können Achseneigenschaften anpassen, z. B. den Achsentyp ändern, Teilstriche setzen, Beschriftungen formatieren und vieles mehr. Hier ist ein Beispiel für die Definition von XY-Achseneigenschaften:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Löschen Sie die Standardreihe und fügen Sie Ihre Daten hinzu.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Ändern Sie die X-Achse so, dass sie eine Kategorie statt einem Datum anzeigt.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); //Gemessen in Anzeigeeinheiten der Y-Achse (Hunderter).
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

## Formatieren von Datenbeschriftungen

Sie können Datenbeschriftungen mit unterschiedlichen Zahlenformaten formatieren. Hier ist ein Beispiel:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Löschen Sie die Standardreihe und fügen Sie Ihre Daten hinzu.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Zusätzliche Diagrammanpassungen

Sie können Ihre Diagramme weiter anpassen, indem Sie Grenzen, Intervalleinheiten zwischen Beschriftungen, das Ausblenden von Diagrammachsen und mehr anpassen. Sehen Sie sich die bereitgestellten Codeausschnitte an, um mehr über diese Optionen zu erfahren.

## Abschluss

In diesem Tutorial haben wir untersucht, wie Sie mit Diagrammen unter Verwendung von Aspose.Words für Java arbeiten. Sie haben gelernt, wie Sie verschiedene Diagrammtypen erstellen, Achseneigenschaften anpassen, Datenbeschriftungen formatieren und vieles mehr. Aspose.Words für Java bietet leistungsstarke Tools zum Hinzufügen visueller Darstellungen von Daten zu Ihren Dokumenten und verbessert so die Art und Weise, wie Sie Informationen präsentieren.

## Häufig gestellte Fragen

### Wie kann ich einem Diagramm mehrere Reihen hinzufügen?

 Sie können einem Diagramm mehrere Reihen hinzufügen, indem Sie das`chart.getSeries().add()` Methode. Stellen Sie sicher, dass Sie den Seriennamen, die Kategorien und die Datenwerte angeben.

### Wie kann ich Datenbeschriftungen mit benutzerdefinierten Zahlenformaten formatieren?

Sie können Datenbeschriftungen formatieren, indem Sie auf das`DataLabels` Eigenschaften einer Serie und Festlegen des gewünschten Formatcodes mit`getNumberFormat().setFormatCode()`.

### Wie passe ich Achseneigenschaften in einem Diagramm an?

 Sie können Achseneigenschaften wie Typ, Teilstriche, Beschriftungen und mehr anpassen, indem Sie auf das`ChartAxis` Eigenschaften wie`setCategoryType()`, `setCrosses()` , Und`setMajorTickMark()`.

### Wie kann ich andere Diagrammtypen wie Streu- oder Flächendiagramme erstellen?

 Sie können verschiedene Diagrammtypen erstellen, indem Sie die entsprechenden`ChartType` beim Einfügen des Diagramms mit`builder.insertChart(ChartType.TYPE, width, height)`.

### Wie kann ich eine Diagrammachse ausblenden?

 Sie können eine Diagrammachse ausblenden, indem Sie das`setHidden(true)` Eigenschaft der Achse.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
