---
category: general
date: 2026-11-15
description: Erfahren Sie, wie Sie ein Kreisdiagramm zu einem Word‑Dokument mit Aspose.Words
  für Java hinzufügen. Enthält Donut‑Konvertierung, explodiertes Segment und vollständiges
  Codebeispiel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: de
lastmod: 2026-11-15
og_description: Fügen Sie einem Word-Dokument ein Kreisdiagramm mit Aspose.Words für
  Java hinzu. Dieses Tutorial zeigt, wie man ein Segment hervorhebt und das Diagramm
  in ein Donut‑Diagramm umwandelt.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Ein Kreisdiagramm zu einem Word‑Dokument mit Java hinzufügen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Wie man mit Java ein Kreisdiagramm in ein Word‑Dokument einfügt
url: /de/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ein Kreisdiagramm zu einem Word‑Dokument hinzufügen – vollständige Java‑Anleitung

Wenn Sie **programmgesteuert ein Kreisdiagramm zu einem Word‑Dokument hinzufügen** müssen, zeigt Ihnen dieses Tutorial genau, wie Sie das mit Aspose.Words für Java erledigen. Sie sehen den kompletten Ablauf: Laden einer DOCX, Erstellen eines Kreisdiagramms, Explodieren des ersten Segments und Umwandeln des Diagramms in ein Donut‑Diagramm, indem Sie eine Lochgröße festlegen.

Der Leitfaden behandelt außerdem gängige Varianten – z. B. das Hinzufügen mehrerer Serien, das Anpassen von Farben und den Umgang mit Dokumenten, die bereits Diagramme enthalten – sodass Sie den Code an reale Projekte wie automatisierte Berichte oder dynamische Präsentationen anpassen können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java 17 oder höher (der Code kompiliert auch mit JDK 11+)
* Maven 3.6+ oder Gradle für das Abhängigkeits‑Management
* Eine Aspose.Words‑für‑Java‑Lizenz (die kostenlose Testversion reicht für Tests)
* Grundlegende Kenntnisse der Java‑Syntax und der Maven‑Projektstruktur

## Schritt 1: Maven‑Projekt einrichten und Aspose.Words importieren

Erstellen Sie ein neues Maven‑Projekt (oder fügen Sie es einem bestehenden hinzu) und binden Sie die Aspose.Words‑Abhängigkeit ein:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Profi‑Tipp:** Wenn Sie Gradle verwenden, lautet der entsprechende Eintrag `implementation 'com.aspose:aspose-words:24.9'`.

Die Abhängigkeit bringt die Klassen `Document`, `Chart` und `ChartType` mit, die Sie zum Manipulieren von Diagrammen benötigen.

## Schritt 2: Ziel‑Dokument laden

Sie können von einer bestehenden `.docx`‑Datei starten oder ein neues leeres Dokument erzeugen. Das folgende Beispiel lädt eine Vorlage namens `input.docx`, die im Ordner `src/main/resources` liegt.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Existiert die Datei nicht, erstellt Aspose.Words automatisch ein leeres Dokument, wenn Sie `new Document()` ohne Dateinamen aufrufen.

## Schritt 3: Ein Kreisdiagramm erstellen und in das Dokument einfügen

Aspose.Words behandelt ein Diagramm als Form, die überall dort platziert werden kann, wo ein Absatz erscheinen darf. Der nachfolgende Code erzeugt ein **Kreisdiagramm**, fügt eine einzelne Datenserie hinzu und fügt das Diagramm nach dem ersten Absatz ein.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Warum dieser Schritt wichtig ist:**  
* `ChartType.PIE` weist Aspose.Words an, ein traditionelles Kreisdiagramm zu rendern.  
* Das Hinzufügen einer Serie mit sowohl Kategorienamen als auch numerischen Werten füllt die Segmente automatisch.  
* Das Einfügen des Diagramms als Kind eines `Paragraph` erhält den Dokumenten‑Fluss.

## Schritt 4: Das erste Segment explodieren, um es hervorzuheben

Ein *explodiertes Segment* lenkt die Aufmerksamkeit auf einen bestimmten Datenpunkt. Die API stellt `setExplode(boolean)` für ein `ChartSeries`‑Objekt bereit. Wird es bei der ersten Serie (Index 0) gesetzt, springt das erste Segment heraus.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Häufige Frage:** *Was, wenn ich mehrere Serien habe?*  
> Sie können eine bestimmte Serie über ihren Index ansprechen, z. B. `pieChart.getSeries().get(1).setExplode(true)` für die zweite Serie.

## Schritt 5: Das Kreisdiagramm in ein Donut‑Diagramm umwandeln, indem Sie die Lochgröße festlegen

Ein Donut‑Diagramm ist im Grunde ein Kreisdiagramm mit einem hohlen Zentrum. Aspose.Words ermöglicht es, die Lochgröße als Prozentsatz des Diagrammradius zu definieren.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

Die Methode `setHoleSize` akzeptiert Werte von **0** (normales Kreisdiagramm) bis **100** (vollständig leer). Ein Wert zwischen **30‑40** ergibt ein optisch ausgewogenes Donut‑Diagramm.

## Schritt 6: Dokument speichern und Ergebnis prüfen

Nach allen Änderungen speichern Sie das Dokument. Die folgende Zeile schreibt die Datei in den Ordner `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Erwartetes Ergebnis

Öffnen Sie `final-pie-doughnut.docx` in Microsoft Word:

* An der Stelle des ersten Absatzes erscheint ein Donut‑Diagramm.  
* Das Segment „Apples“ ist explodiert (leicht vom Rest getrennt).  
* Das Diagramm zeigt vier Segmente mit den Bezeichnungen *Apples*, *Bananas*, *Cherries*, *Dates* und den von Ihnen angegebenen Prozentsätzen.

Wenn Sie lieber PDF ausgeben möchten, ändern Sie das `SaveFormat` zu `SaveFormat.PDF`.

## Umgang mit Sonderfällen und Varianten

### Mehrere Serien hinzufügen

Falls Sie mehrere Serien benötigen (z. B. gestapeltes Donut), fügen Sie sie nacheinander hinzu:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Benutzerdefinierte Farben

Sie können jedem Segment eine Farbe zuweisen über `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Arbeiten mit einem bestehenden Diagramm

Enthält das Dokument bereits ein Diagramm und Sie möchten nur dieses ändern, lokalisieren Sie die Diagramm‑Form:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Lizenzverwaltung

Aspose.Words benötigt für den Produktionseinsatz eine Lizenz. Platzieren Sie Ihre Datei `Aspose.Words.lic` im Klassenpfad und laden Sie sie beim Anwendungsstart:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Fehlt die Lizenz, wird dem erzeugten Dokument ein Wasserzeichen hinzugefügt.

## Vollständiges, ausführbares Beispiel

Unten finden Sie die komplette Java‑Klasse, die jeden besprochenen Schritt integriert. Kopieren Sie sie nach `src/main/java/com/example/AddPieChart.java` und führen Sie `mvn compile exec:java` aus.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Das Ausführen des Programms erzeugt das zuvor beschriebene Donut‑Diagramm. Passen Sie `categories`, `values` oder `holeSize` an Ihre Daten an.

## Fazit

Sie wissen jetzt, wie Sie **ein Kreisdiagramm zu einem Word‑Dokument hinzufügen** können – mit Java und Aspose.Words. Das Tutorial behandelte das Laden eines Dokuments, das Erstellen eines Kreisdiagramms, das Explodieren eines Segments, das Umwandeln in ein Donut‑Diagramm sowie gängige Varianten wie mehrere Serien, benutzerdefinierte Farben und bereits vorhandene Diagramme. Mit diesem Fundament können Sie automatisierte Reporting‑Tools bauen, dynamische Präsentationen generieren oder reichhaltige Visualisierungen direkt in Word‑Dateien einbetten.

### Was Sie als Nächstes erkunden können

* **add bar chart to Word document** – ähnliche Schritte, jedoch `ChartType.BAR` verwenden.  
* **customize chart legends and titles** – `pieChart.getTitle().setText("...")` und `pieChart.getLegend().setPosition(LegendPosition.RIGHT)` nutzen.  
* **export the Word document as PDF** – `SaveFormat` zu `PDF` ändern für vertriebsfertige Dateien.  
* **populate chart data from a database** – die statischen Arrays durch JDBC‑Abfrageergebnisse ersetzen.

Probieren Sie gern verschiedene Diagrammtypen, Datenquellen und Stiloptionen aus. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren eigenen Projekten erkunden können.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}