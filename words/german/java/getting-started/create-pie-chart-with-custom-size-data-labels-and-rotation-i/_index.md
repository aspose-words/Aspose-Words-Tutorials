---
category: general
date: 2026-11-22
description: Erstelle ein Kreisdiagramm in Java und lerne, wie man die Diagrammgröße
  festlegt, Datenbeschriftungen hinzufügt, Prozentsätze anzeigt und das erste Segment
  für klare visuelle Wirkung dreht.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: de
lastmod: 2026-11-22
og_description: Erstelle ein Kreisdiagramm in Java, setze anschließend die Diagrammgröße,
  zeige Prozentsätze in den Datenbeschriftungen an und rotiere das erste Segment –
  alles in einem einzigen, ausführbaren Beispiel.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Erstelle ein Kreisdiagramm mit benutzerdefinierter Größe, Beschriftungen
  und Rotation in Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Kreisdiagramm mit benutzerdefinierter Größe, Datenbeschriftungen und Drehung
  in Java erstellen
url: /de/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kreisdiagramm mit benutzerdefinierter Größe, Datenbeschriftungen und Drehung in Java

Wenn Sie in Java **create pie chart** benötigen, führt Sie diese Anleitung durch den gesamten Prozess. Sie lernen, wie Sie **set chart size** festlegen, **show percentages pie chart** aktivieren, **data labels pie chart** hinzufügen und **rotate pie chart slice**, sodass das erste Segment bei einem Winkel von 45 Grad beginnt.

Das Beispiel verwendet **Aspose.Slides for Java**, eine weit verbreitete Bibliothek zur Manipulation von PowerPoint-Dateien. Die gleichen Konzepte gelten für andere Diagrammbibliotheken; ersetzen Sie einfach die API‑Aufrufe durch die entsprechenden in Ihrem Toolkit.

## Voraussetzungen

* Java 17 oder neuer installiert  
* Maven 3.8+ (oder Gradle) für die Abhängigkeitsverwaltung  
* Grundlegendes Verständnis der Java‑Syntax  
* Zugriff auf die Aspose.Slides for Java‑Binärdatei (Sie können eine kostenlose Testversion von der offiziellen Website erhalten)

Fügen Sie die Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Kreisdiagramm erstellen – vollständiges Beispiel

Das folgende Programm erstellt eine PowerPoint‑Folien, die ein pie chart mit benutzerdefinierter Größe, prozentualen Datenbeschriftungen und einem gedrehten ersten Segment enthält.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Warum jeder Schritt wichtig ist

| Step | Purpose | How it relates to the keywords |
|------|---------|--------------------------------|
| **Insert chart** | **Create pie chart** – das Kernobjekt, das die Visualisierung rendert. | Erfüllt direkt die *create pie chart* Anforderung. |
| **Set dimensions** | Der Aufruf `addChart(..., 400, 300)` demonstriert **set chart size**. | Steuert die Breite (400 px) und Höhe (300 px). |
| **Show percentages** | `setShowPercentage(true)` lässt das Diagramm **show percentages pie chart** auf jedem Segment anzeigen. | Benutzer benötigen häufig Prozentsätze anstelle von Rohwerten. |
| **Add data labels** | Die `DataLabelFormat`‑Konfiguration fügt **data labels pie chart** mit der gewünschten Sichtbarkeit hinzu. | Beschriftungen verbessern die Lesbarkeit und sind anpassbar. |
| **Rotate slice** | `setFirstSliceAngle(45)` dreht das Diagramm, sodass das erste Segment bei einem Winkel von 45 Grad beginnt, und erfüllt **rotate pie chart slice**. | Verbessert die visuelle Hervorhebung eines bestimmten Segments. |

## Schritt‑für‑Schritt‑Aufschlüsselung

### 1. Ein pie chart einfügen und **set chart size** festlegen

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*Die Methode `addChart` erstellt das Diagramm und legt gleichzeitig **set chart size** auf 400 × 300 Punkte fest.*  
Wenn Sie eine andere Größe benötigen, passen Sie die letzten beiden Argumente an.

### 2. Das Diagramm mit Daten füllen

Die Demo fügt drei Kategorien und eine einzelne Serie hinzu. Ersetzen Sie die fest codierten Zahlen bei Bedarf durch Daten aus einer Datenbank, CSV-Datei oder Benutzereingabe.

### 3. **show percentages pie chart** auf jedem Segment anzeigen

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Durch Aktivieren von `setShowPercentage(true)` wird sichergestellt, dass das Diagramm **show percentages pie chart** automatisch den Anteil jedes Segments am Gesamtwert berechnet.*

### 4. Detaillierte **data labels pie chart** hinzufügen

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Sie können weitere Beschriftungsoptionen (`setShowValue`, `setShowSeriesName` usw.) umschalten, um das **add data labels pie chart** Erlebnis anzupassen.

### 5. **rotate pie chart slice** – erste Scheibe drehen

```java
chart.setFirstSliceAngle(45);
```

*Durch Aufrufen von `setFirstSliceAngle(45)` wird **rotate pie chart slice** ausgeführt, sodass das erste Segment bei einem Winkel von 45 Grad beginnt und hervorgehoben wird.*

### 6. Ergebnis speichern und anzeigen

Das Ausführen des Programms erzeugt `output/PieChartDemo.pptx`. Öffnen Sie die Datei in PowerPoint oder einem kompatiblen Viewer, um das endgültige pie chart zu sehen:

![Beispiel für erstelltes pie chart](images/pie_chart_example.png){.align-center alt="Screenshot eines erstellten pie chart mit benutzerdefinierter Größe, Prozent‑Beschriftungen und einer gedrehten ersten Scheibe"}

Das obige Bild zeigt das Ergebnis des **create pie chart**, was bestätigt, dass Größe, Beschriftungen, Prozentsätze und Drehung korrekt angewendet wurden.

## Häufige Variationen und Sonderfälle

| Situation | Adjustment |
|-----------|------------|
| **Different chart dimensions** | Ändern Sie die Breiten‑/Höhen‑Parameter in `addChart`. |
| **Multiple series** | Fügen Sie zusätzliche `IChartSeries`‑Objekte hinzu; jede Serie kann eigene Beschriftungseinstellungen haben. |
| **Custom label format** | Verwenden Sie `series.getDataLabelFormat().setNumberFormat("0.0%")`, um die Dezimalstellen zu steuern. |
| **Rotating to another angle** | Geben Sie eine beliebige ganze Zahl (0‑360) an `setFirstSliceAngle` weiter. |
| **Export as image** | Nach dem Speichern rufen Sie `chart.writeAsSvg(outPath)` oder `chart.writeAsPng(outPath)` für eine Rasterversion auf. |

> **Pro Tipp:** Wenn Sie planen, viele Diagramme in einer Schleife zu erzeugen, verwenden Sie dasselbe `Presentation`‑Objekt erneut und ersetzen nur die Diagrammdaten. Dies reduziert den Speicherverbrauch und beschleunigt die Verarbeitung.

## Fazit

Sie wissen jetzt, wie man in Java **create pie chart**, **set chart size**, **show percentages pie chart** aktiviert, **add data labels pie chart** hinzufügt und **rotate pie chart slice** für eine bessere visuelle Betonung durchführt. Das vollständige, ausführbare Beispiel demonstriert jeden Schritt von der Initialisierung bis zum Speichern der finalen PowerPoint‑Datei.

### Was kommt als Nächstes?

* Untersuchen Sie weitere Diagrammtypen (Bar, Line, Area) mit demselben `ChartType`‑Enum.  
* Kombinieren Sie mehrere Diagramme auf einer Folie für Dashboards.  
* Exportieren Sie Diagramme nach PNG oder SVG für die Verwendung in Webanwendungen.  

Fühlen Sie sich frei, mit Farben, Legenden und Animationseffekten zu experimentieren – Ihre Datenvisualisierungen sind nur durch die Vorstellungskraft begrenzt. Viel Spaß beim Diagrammerstellen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein pie chart in Word einfügt – Datenbeschriftungsprozentsatz hinzufügen](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Wie man ein pie chart Segment in Java explodiert – Aspose.Words Diagramm‑Tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Pie Chart in Java einfügen – Explodieren, Drehen & Hervorheben von Segmenten](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}