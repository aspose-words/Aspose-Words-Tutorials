---
category: general
date: 2026-09-18
description: Lernen Sie, ein Word-Dokument zu erstellen und ein Kreisdiagramm mit
  Aspose.Words für Java einzufügen. Enthält das Drehen des Kreisdiagramms und die
  Schritte zum Generieren einer Word-Datei.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: de
lastmod: 2026-09-18
og_description: Erstellen Sie ein Word‑Dokument und fügen Sie ein Kreisdiagramm mit
  Java ein. Folgen Sie dieser Anleitung, um das Kreisdiagramm zu drehen, Segmente
  zu explodieren und eine Word‑Datei zu erzeugen.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Erstellen Sie ein Word‑Dokument mit einem Kreisdiagramm – Schritt‑für‑Schritt
  Java‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Wie man ein Word‑Dokument mit einem Kreisdiagramm in Java erstellt
url: /de/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Word-Dokument mit einem Kreisdiagramm in Java erstellt

Wenn Sie ein **Word-Dokument** erstellen müssen, das Daten visualisiert, zeigt Ihnen diese Anleitung, wie Sie dies mit Aspose.Words für Java erledigen. Sie lernen, ein Kreisdiagramm einzufügen, ein Segment zu „explodieren“, das Diagramm zu drehen und schließlich **eine Word‑Datei zu erzeugen**, die Sie in Microsoft Word öffnen können.

Berichte zu erstellen, die Text und Diagramme kombinieren, erfordert kein separates Grafik‑Tool. Am Ende dieses Tutorials verfügen Sie über ein vollständiges, ausführbares Programm, das eine .docx‑Datei mit einem vollständig konfigurierten Kreisdiagramm erzeugt.

## Voraussetzungen

- Java 17 oder neuer (der Code kompiliert auch mit Java 8+)
- Maven oder Gradle für die Abhängigkeitsverwaltung
- Aspose.Words für Java Lizenz (die kostenlose Testversion funktioniert für dieses Beispiel)
- Grundlegende Kenntnisse der Java‑Syntax

## Schritt 1: Maven‑Projekt einrichten

Erstellen Sie ein neues Maven‑Projekt und fügen Sie die Aspose.Words‑Abhängigkeit zu `pom.xml` hinzu:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

**Pro‑Tipp:** Halten Sie die Versionsnummer aktuell; neuere Releases bringen Verbesserungen bei Diagrammtypen und Fehlerbehebungen.

## Schritt 2: Ein neues Word‑Dokument erstellen

Der erste Vorgang, wenn Sie programmgesteuert ein **Word‑Dokument** **erstellen**, besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert die gesamte .docx‑Datei im Speicher.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

Die Klasse `Document` ist der Einstiegspunkt für alle Word‑Verarbeitungs‑Funktionen. Zu diesem Zeitpunkt wird noch keine Datei auf die Festplatte geschrieben; alles geschieht im RAM, bis Sie `save` aufrufen.

## Schritt 3: Ein Kreisdiagramm einfügen

Ein `DocumentBuilder` ermöglicht das Hinzufügen von Inhalten zum Dokument. Mit `insertChart` können Sie **Kreisdiagramm**‑Objekte direkt **einfügen**.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` weist Aspose.Words an, ein Kreisdiagramm zu erstellen. Die Abmessungen werden in Punkten angegeben (1 pt ≈ 1/72 in). Nach diesem Aufruf erscheint das Diagramm in einem neuen Absatz.

## Schritt 4: Das Diagramm mit Daten füllen

Ein Kreisdiagramm benötigt eine Reihe von Werten. Hier fügen wir drei Kategorien hinzu: „Apples“, „Bananas“ und „Cherries“.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

Die Methode `add` erstellt die Serie und erzeugt automatisch Legenden‑Einträge. Sie können dieses Muster für jeden numerischen Datensatz wiederverwenden.

## Schritt 5: Das erste Segment hervorheben

Das Explodieren eines Segments lenkt die Aufmerksamkeit auf einen bestimmten Wert. Das erste Segment (Index 0) wird um 20 Punkte explodiert.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Das Setzen von `explode` auf die Serie wirkt sich auf das gesamte Diagramm aus, sodass nur der erste Datenpunkt versetzt wird.

## Schritt 6: Ein Kreisdiagramm drehen

Das Drehen des Diagramms verbessert das visuelle Gleichgewicht, insbesondere wenn das größte Segment nicht oben liegt. Die Methode `setRotationAngle` erwartet Grad.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Eine Drehung um 45° verschiebt den Startwinkel im Uhrzeigersinn und macht das Diagramm in vielen Layouts leichter lesbar.

## Schritt 7: Das Dokument speichern und eine Word‑Datei erzeugen

Schließlich schreiben Sie das Dokument auf die Festplatte. Dieser Schritt **erzeugt eine Word‑Datei**, die mit Microsoft Word, LibreOffice oder jedem kompatiblen Viewer geöffnet werden kann.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Die Methode `save` erkennt automatisch die .docx‑Erweiterung und schreibt ein Word‑kompatibles Paket. Der Ordner `output` muss existieren oder Sie können ihn programmgesteuert erstellen.

### Erwartete Ausgabe

Nach dem Ausführen des Programms öffnen Sie `output/PieChart.docx`. Sie sollten sehen:

- Eine einzelne Seite mit einem 400 × 300 pt Kreisdiagramm.
- Das „Apples“-Segment ist um 20 pt nach außen explodiert.
- Das gesamte Diagramm ist um 45° im Uhrzeigersinn gedreht.
- Eine Legende, die den drei Fruchtkategorien entspricht.

## Häufige Variationen und Sonderfälle

### Mehrere Diagramme einfügen

Wenn Sie mehr als ein Diagramm benötigen, rufen Sie `builder.insertChart` erneut auf, nachdem Sie den Cursor verschoben haben:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Diagrammfarben ändern

Sie können die Farben der Segmente über die `getPoints()`‑Sammlung der Serie anpassen:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Umgang mit großen Datensätzen

Für Datensätze mit mehr als 10 Segmenten sollten Sie ein Donut‑Diagramm (`ChartType.DOUGHNUT`) in Betracht ziehen, um die Visualisierung klar zu halten.

## Fazit

Sie wissen jetzt, wie man mit Aspose.Words für Java **ein Word‑Dokument erstellt**, **ein Kreisdiagramm einfügt**, **ein Kreisdiagramm dreht** und **eine Word‑Datei erzeugt**. Die vollständige Lösung demonstriert den gesamten Arbeitsablauf von der Dokumentinitialisierung bis zur finalen Dateiausgabe und behandelt sowohl das „Wie“ als auch das „Warum“ jedes Schrittes.

Als Nächstes erkunden Sie verwandte Themen wie **wie man Kreisdiagrammdaten** aus einer Datenbank erstellt, Datenbeschriftungen hinzufügt oder das Diagramm als Bild exportiert. Experimentieren Sie mit verschiedenen Diagrammtypen (Balken, Linie, Donut), um Ihr Word‑Automatisierungs‑Toolkit zu erweitern.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}