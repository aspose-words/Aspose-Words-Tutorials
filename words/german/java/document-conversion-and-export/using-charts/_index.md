---
date: 2026-02-16
description: Erfahren Sie, wie Sie in Aspose.Words für Java mehrere Serien zu Diagrammen
  hinzufügen, Achsenunterteilungen ändern, ein benutzerdefiniertes Zahlenformat anwenden
  und Word‑Dokumente mit Linien‑ und Säulendiagrammen erzeugen.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Mehrere Serien zu Diagrammen in Aspose.Words für Java hinzufügen
url: /de/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mehrere Serien zu Diagrammen in Aspose.Words für Java hinzufügen

## Einführung in die Verwendung von Diagrammen in Aspose.Words für Java

## Schnelle Antworten
- **Wie füge ich mehrere Serien hinzu?** Verwenden Sie `chart.getSeries().add(...)` für jede Serie, die Sie anzeigen möchten.  
- **Kann ich Achsen‑Tick‑Marks ändern?** Ja – verwenden Sie `setMajorTickMark()` und `setMinorTickMark()` an den Achsenobjekten.  
- **Welches Format kann ich auf Datenbeschriftungen anwenden?** Jedes Excel‑kompatible Zahlenformat, z. B. `"$"#,##0.00` oder `0.00%`.  
- **Welche Diagrammtypen werden unterstützt?** Linie, Säule, Fläche, Blase, Streuung und viele weitere über `ChartType`.  
- **Ist für die Produktion eine Lizenz erforderlich?** Eine gültige Aspose.Words für Java‑Lizenz ist für die volle Funktionalität erforderlich.

## Was bedeutet „mehrere Serien hinzufügen“ in einem Diagramm?
Das Hinzufügen mehrerer Serien bedeutet, mehr als einen Datensatz in denselben Diagrammbereich einzufügen, sodass Sie verschiedene Kategorien oder Zeiträume nebeneinander vergleichen können. Jede Serie erscheint als eigene Linie, Säule oder Markierung, was den Lesern eine reichhaltigere visuelle Darstellung bietet.

## Warum Aspose.Words für Java verwenden, um Word‑Dokumente mit Diagrammen zu erstellen?
- **Vollständige Kontrolle** über Diagrammtyp, Layout und Stil, ohne Word manuell zu öffnen.  
- **Programmgesteuerte Erstellung** passt in automatisierte Reporting‑Pipelines.  
- **Plattformübergreifend** – funktioniert in jeder Java‑kompatiblen Umgebung.  
- **Umfangreiche API** zum Anpassen von Achsen, Datenbeschriftungen und Zahlenformaten.

## Voraussetzungen
- Java Development Kit (JDK) 8 oder höher.  
- Aspose.Words for Java‑Bibliothek zu Ihrem Projekt hinzugefügt (Maven/Gradle oder JAR).  
- Eine gültige Aspose‑Lizenz für die Produktion (optional für Evaluation).

## Schritt‑für‑Schritt‑Anleitung

### Schritt 1: Erstellen Sie ein Liniendiagramm und **fügen mehrere Serien hinzu**
Unten finden Sie den Kerncode, der ein Liniendiagramm erstellt, die Standardserie löscht und dann drei unterschiedliche Serien mit benutzerdefinierten Datenbeschriftungen hinzufügt.

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

> **Profi‑Tipp:** Rufen Sie `chart.getSeries().add(...)` so oft auf, wie nötig, um **mehrere Serien hinzuzufügen** – jeder Aufruf erstellt eine neue Linie (oder Säule usw.) im selben Diagramm.

### Schritt 2: **Erstellen Sie ein Säulendiagramm** (create column chart java)
Der nächste Ausschnitt zeigt, wie man ein einfaches Säulendiagramm einfügt, das nützlich ist, um Kategorien nebeneinander zu vergleichen.

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

### Schritt 3: **Achsen‑Tick‑Marks ändern** (change axis tick marks)
Das Anpassen der X‑ und Y‑Achse verbessert die Lesbarkeit. Der folgende Code zeigt, wie man Tick‑Marks ändert, die Reihenfolge umkehrt und benutzerdefinierte Schnittpunkte festlegt.

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

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Schritt 4: **Ein benutzerdefiniertes Zahlenformat anwenden** (apply custom number format)
Sie können Achsenzahlen oder Datenbeschriftungen mit jedem von Excel unterstützten Muster formatieren. Unten ist ein kurzes Beispiel, das die Y‑Achse mit einem Tausendertrennzeichen‑Muster formatiert.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Schritt 5: Das endgültige Word‑Dokument erzeugen (generate chart word document)
Nachdem Sie Serien, Achsen und Beschriftungen konfiguriert haben, rufen Sie einfach `doc.save(...)` wie in den obigen Ausschnitten gezeigt auf. Die resultierende `.docx`‑Datei enthält voll funktionsfähige Diagramme, die in Microsoft Word geöffnet und bearbeitet werden können.

## Häufige Anwendungsfälle
- **Finanz‑Dashboards** – Liniendiagramme mit mehreren Serien für Umsatz, Ausgaben und Gewinn.  
- **Verkaufsberichte** – Säulendiagramme zum Vergleich des Quartalsumsatzes nach Regionen.  
- **Projektverfolgung** – Flächen‑ oder Streudiagramme, die den Fortschritt über die Zeit visualisieren.

## Zusätzliche Diagrammanpassungen
Über die Grundlagen hinaus können Sie Grenzen anpassen, Achsen ausblenden (`axis.setHidden(true)`), Farben ändern, Legenden hinzufügen und mehr. Weitere Optionen finden Sie in der Aspose.Words für Java API‑Referenz.

## Fazit
In diesem Leitfaden haben wir behandelt, wie man **mehrere Serien** zu Diagrammen **hinzufügt**, sowohl Linien‑ als auch Säulendiagramme erstellt, **Achsen‑Tick‑Marks ändert**, **benutzerdefinierte Zahlenformate anwendet** und schließlich ein **Diagramm‑reiches Word‑Dokument erzeugt**. Mit Aspose.Words für Java haben Sie eine leistungsstarke, code‑first‑Methode, um professionelle Datenvisualisierungen direkt in Ihre Dokumente einzubetten.

## Häufig gestellte Fragen

**F: Wie kann ich mehrere Serien zu einem Diagramm hinzufügen?**  
A: Rufen Sie `chart.getSeries().add()` für jede Serie auf, die Sie anzeigen möchten. Jeder Aufruf erstellt einen neuen Datensatz, der als eigene Linie, Säule oder Markierungsgruppe erscheint.

**F: Wie formatiere ich Datenbeschriftungen mit einem benutzerdefinierten Zahlenformat?**  
A: Greifen Sie auf das `DataLabels`‑Objekt der Serie zu und verwenden Sie `getNumberFormat().setFormatCode("your pattern")`. Sie können das Format auch mit einer Quellzelle verknüpfen mittels `isLinkedToSource(true)`.

**F: Wie kann ich Achsen‑Tick‑Marks ändern?**  
A: Verwenden Sie `setMajorTickMark()` und `setMinorTickMark()` auf `ChartAxis`. Optionen umfassen `CROSS`, `INSIDE`, `OUTSIDE` und `NONE`.

**F: Kann ich andere Diagrammtypen wie Streu‑ oder Flächendiagramme erstellen?**  
A: Ja – geben Sie den gewünschten `ChartType` (z. B. `ChartType.SCATTER`, `ChartType.AREA`) beim Aufruf von `builder.insertChart(...)` an.

**F: Wie blende ich eine Achse aus, die ich nicht benötige?**  
A: Rufen Sie `axis.setHidden(true)` auf der `ChartAxis` auf, die Sie ausblenden möchten.

---

**Zuletzt aktualisiert:** 2026-02-16  
**Getestet mit:** Aspose.Words for Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}