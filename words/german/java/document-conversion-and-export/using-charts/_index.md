---
date: 2025-12-13
description: Erfahren Sie, wie Sie ein Säulendiagramm erstellen und Diagrammdatenbeschriftungen
  mit Aspose.Words für Java formatieren. Erkunden Sie das Hinzufügen mehrerer Serien,
  das Ändern des Achsentyps und das Ausblenden der Diagrammachse.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt
url: /de/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt

In diesem Tutorial erstellen Sie **Säulendiagramm**‑Visualisierungen direkt in Word‑Dokumenten mithilfe von Aspose.Words für Java. Wir führen Sie durch das Erstellen verschiedener Diagrammtypen, das Hinzufügen mehrerer Serien, das Formatieren von Diagrammdatenbeschriftungen, das Ändern des Achsentypus und sogar das Ausblenden einer Diagrammachse, wenn Sie ein saubereres Aussehen benötigen. Am Ende haben Sie einen soliden, produktions‑bereiten Ansatz, um reichhaltige Diagramme in Ihre Dokumente einzubetten.

## Schnelle Antworten
- **Welche Hauptklasse wird zum Erstellen eines Diagramms verwendet?** `DocumentBuilder` mit `insertChart`.
- **Welche Methode fügt eine neue Serie hinzu?** `chart.getSeries().add(...)`.
- **Wie formatiere ich Diagrammdatenbeschriftungen?** Verwenden Sie `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Kann ich eine Achse ausblenden?** Ja, rufen Sie `setHidden(true)` am Achsenobjekt auf.
- **Benötige ich eine Lizenz für Aspose.Words?** Eine Lizenz ist für den Produktionseinsatz erforderlich; eine kostenlose Testversion ist verfügbar.

## Was ist ein Säulendiagramm und warum verwenden?

Ein Säulendiagramm stellt kategoriale Daten als vertikale Balken dar und eignet sich ideal zum Vergleich von Werten über Gruppen hinweg (Umsatz pro Region, monatliche Ausgaben usw.). In Java‑Anwendungen ermöglicht das Erzeugen eines Säulendiagramms mit Aspose.Words das direkte Einbetten dieser Visualisierungen in Word / DOCX‑Dateien, ohne Excel oder externe Werkzeuge zu benötigen.

## Wie man ein Säulendiagramm erstellt

Unten finden Sie ein einfaches Beispiel, das ein schlichtes Säulendiagramm erzeugt. Der Code ist identisch mit dem Original‑Snippet – wir haben nur erläuternde Kommentare hinzugefügt, um das Verständnis zu erleichtern.

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

### Mehrere Serien hinzufügen

Sie können **mehrere Serien** zu einem Säulendiagramm hinzufügen, indem Sie `chart.getSeries().add(...)` wiederholt aufrufen, wie oben gezeigt. Jede Serie kann ihr eigenes Satz von Kategorien und Werten besitzen, sodass Sie mehrere Datensätze nebeneinander vergleichen können.

## Wie man ein Liniendiagramm mit benutzerdefinierten Datenbeschriftungen erstellt

Falls Sie ein Liniendiagramm statt eines Säulendiagramms benötigen, gilt das gleiche Muster. Dieses Beispiel demonstriert zudem das **Formatieren von Diagrammdatenbeschriftungen** mit unterschiedlichen Zahlenformaten.

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

### Datenbeschriftungen hinzufügen

Der Aufruf `series1.hasDataLabels(true)` **fügt Datenbeschriftungen** zur Serie hinzu, während `setShowValue(true)` die tatsächlichen Werte im Diagramm sichtbar macht.

## Wie man den Achsentyp ändert und Achseneigenschaften anpasst

Das Ändern des Achsentypus (z. B. von Datum zu Kategorie) ermöglicht die Kontrolle darüber, wie Datenpunkte dargestellt werden. Dieses Snippet zeigt außerdem, wie man **Diagrammachse ausblendet**, wenn ein minimalistisches Design bevorzugt wird.

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

### Achsentyp ändern

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **ändert den Achsentyp** von einer datumsbasierten Achse zu einer kategorialen, wodurch Sie die Platzierung der Beschriftungen vollständig steuern können.

## Wie man Diagrammdatenbeschriftungen formatiert (Zahlenformate)

Sie können Zahlenformatierungen direkt auf die Achse oder Datenbeschriftungen anwenden. Dieses Beispiel formatiert die Y‑Achsen‑Zahlen mit einem Tausendertrennzeichen.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Weitere Diagrammanpassungen

Über die Grundlagen hinaus können Sie Grenzen anpassen, Intervall‑Einheiten zwischen Beschriftungen festlegen, bestimmte Achsen ausblenden und mehr. Konsultieren Sie die Aspose.Words für Java API‑Dokumentation für eine vollständige Liste der Eigenschaften.

## Häufig gestellte Fragen

**F: Wie kann ich mehrere Serien zu einem Diagramm hinzufügen?**  
A: Verwenden Sie `chart.getSeries().add()` für jede Serie, die Sie anzeigen möchten. Jeder Aufruf kann einen eindeutigen Namen, ein Kategorien‑Array und ein Werte‑Array bereitstellen.

**F: Wie formatiere ich Diagrammdatenbeschriftungen mit benutzerdefinierten Zahlenformaten?**  
A: Greifen Sie auf das `DataLabels`‑Objekt einer Serie zu und rufen Sie `getNumberFormat().setFormatCode("Ihr Format")` auf. Sie können das Format auch mit `isLinkedToSource(true)` an eine Quellzelle binden.

**F: Wie kann ich eine Diagrammachse ausblenden?**  
A: Rufen Sie `setHidden(true)` auf der `ChartAxis` auf, die Sie ausblenden möchten (z. B. `chart.getAxisY().setHidden(true)`).

**F: Was ist der beste Weg, den Achsentyp zu ändern?**  
A: Verwenden Sie `setCategoryType(AxisCategoryType.CATEGORY)` für kategoriale Achsen oder `AxisCategoryType.DATE` für Datums‑Achsen.

**F: Wie füge ich einer Serie Datenbeschriftungen hinzu?**  
A: Aktivieren Sie sie mit `series.hasDataLabels(true)` und konfigurieren Sie die Sichtbarkeit über `series.getDataLabels().setShowValue(true)`.

## Fazit

Wir haben alles behandelt, was Sie benötigen, um **Säulendiagramm**‑Visualisierungen mit Aspose.Words für Java zu **erstellen** – vom Einfügen einfacher Diagramme und Hinzufügen mehrerer Serien über das Formatieren von Diagrammdatenbeschriftungen bis hin zum Ändern des Achsentypus und dem Ausblenden von Diagrammachsen für ein sauberes Erscheinungsbild. Integrieren Sie diese Techniken in Ihre Reporting‑ oder Dokumentengenerierungs‑Pipelines, um professionelle, datengetriebene Word‑Dokumente zu liefern.

---

**Zuletzt aktualisiert:** 2025-12-13  
**Getestet mit:** Aspose.Words für Java 24.12 (neueste)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}