---
category: general
date: 2026-09-27
description: Erfahren Sie, wie Sie ein Kreisdiagramm mit Java in ein Word‑Dokument
  einfügen, ein Kreisdiagramm in Word erstellen und Prozentsätze im Kreisdiagramm
  anzeigen, um klare Dateneinblicke zu erhalten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: de
lastmod: 2026-09-27
og_description: Wie man ein Kreisdiagramm in ein Word-Dokument mit Java einfügt. Dieser
  Leitfaden zeigt Ihnen, wie Sie ein Kreisdiagramm in Word erstellen, Prozentsätze
  im Kreisdiagramm anzeigen und Führungslinien hinzufügen.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Wie man ein Kreisdiagramm in ein Word‑Dokument mit Java einfügt
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Wie man ein Kreisdiagramm in ein Word‑Dokument mit Java einfügt
url: /de/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Kreisdiagramm in ein Word‑Dokument mit Java einfügt

Wenn Sie **wie man ein Kreisdiagramm einfügt** in eine Word‑Datei, führt Sie diese Anleitung durch den gesamten Prozess. Sie sehen, wie Sie **ein Kreisdiagramm in Word erstellen**, Prozentsätze auf jedem Segment anzeigen und Führungslinien für ein professionelles Aussehen hinzufügen.

Die Word‑Automatisierung wirkt oft schwergewichtig, aber mit Aspose.Words für Java können Sie vollständig formatierte Dokumente programmgesteuert erzeugen. Am Ende dieses Tutorials haben Sie ein ausführbares Java‑Snippet, das ein Word‑Dokument mit einem formatierten Kreisdiagramm erzeugt.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie folgendes haben:

- Java 17 oder neuer installiert
- Maven oder Gradle zur Verwaltung der Abhängigkeiten
- Aspose.Words für Java (Version 23.11 oder neuer) zu Ihrem Projekt hinzugefügt
- Grundlegende Kenntnisse der Java‑Syntax

Sie benötigen keine Vorkenntnisse mit Diagramm‑APIs; die nachfolgenden Schritte decken alles von der Projekt‑Einrichtung bis zur finalen Ausgabe ab.

## Schritt 1: Maven‑Abhängigkeit einrichten

Fügen Sie die Aspose.Words‑Bibliothek zu Ihrer `pom.xml` hinzu. Diese einzelne Abhängigkeit gibt Ihnen Zugriff auf `Document`, `DocumentBuilder` und Diagramm‑Klassen.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Wenn Sie Gradle verwenden, lautet das Äquivalent:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro‑Tipp:** Verwenden Sie die neueste stabile Version, um von Fehlerbehebungen und neuen Diagramm‑Funktionen zu profitieren.

## Schritt 2: Ein neues Dokument und einen Builder erstellen

Das `Document`‑Objekt repräsentiert die Word‑Datei, während `DocumentBuilder` das Einfügen von Inhalten ermöglicht. Dies ist die Grundlage für **Diagramm zu Word‑Dokument hinzufügen**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Der Builder ist nun bereit, Objekte an beliebiger Stelle im Dokument zu platzieren.

## Schritt 3: Ein Kreisdiagramm einfügen

Aspose.Words unterstützt mehrere Diagrammtypen; wir wählen `ChartType.PIE`. Die Größe wird in Punkten angegeben (1 Punkt = 1/72 Zoll).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

In diesem Stadium enthält das Diagramm eine Standard‑Datenreihe mit Platzhalterwerten. Sie können diese Werte später bei Bedarf ersetzen.

## Schritt 4: Auf die Diagramm‑Reihe zugreifen

Ein Kreisdiagramm hat eine einzelne Reihe, die die Segmentwerte enthält. Rufen Sie sie ab, um Formatierungen anzuwenden.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Schritt 5: Das erste Segment „explodieren“

Ein Segment zu explodieren lenkt die Aufmerksamkeit auf einen bestimmten Datenpunkt. Dies ist ein gängiger visueller Hinweis, wenn Sie eine Schlüsselmetrik hervorheben möchten.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Schritt 6: Prozentsätze auf jedem Segment anzeigen

Das direkte Anzeigen von Prozentsätzen im Diagramm verbessert die Datenverständlichkeit. Dies erfüllt die Anforderung **Prozentsätze auf Kreisdiagramm anzeigen**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Schritt 7: Führungslinien für klarere Beschriftungen hinzufügen

Führungslinien verbinden Segment‑Beschriftungen mit den jeweiligen Bereichen und beseitigen Mehrdeutigkeiten. Damit wird **wie man Führungslinien hinzufügt** umgesetzt.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Schritt 8: Das Dokument speichern

Schließlich schreiben Sie das Dokument auf die Festplatte. Sie können jeden Ordner wählen, in den Sie Schreibrechte haben.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Beim Ausführen des Programms wird `output/PieFormatted.docx` erstellt. Öffnen Sie die Datei in Microsoft Word, und Sie sehen ein Kreisdiagramm, bei dem:

- Das erste Segment explodiert ist.
- Jedes Segment seinen Prozentsatz anzeigt.
- Führungslinien von den Prozentsätzen zu den jeweiligen Segmenten zeigen.

### Erwartete Ausgabe

![Formatiertes Kreisdiagramm in Word](/images/pie-formatted.png){: .center-image alt="Formatiertes Kreisdiagramm in ein Word-Dokument eingefügt"}

Der Screenshot (Alt‑Text verwendet das Haupt‑Keyword) veranschaulicht das Endergebnis: ein sauberes, datengetriebenes Kreisdiagramm, bereit für Berichte, Angebote oder Dashboards.

## Häufige Variationen und Sonderfälle

### Segmentwerte ändern

Wenn Sie benutzerdefinierte Daten benötigen, ersetzen Sie die Standard‑Reihenwerte:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Mehrere Reihen (Donut‑Diagramm)

Während ein einfaches Kreisdiagramm nur eine Reihe hat, unterstützt Aspose.Words auch Donut‑Diagramme mit mehreren Reihen. Wechseln Sie `ChartType.PIE` zu `ChartType.DONUT` und wiederholen Sie die Schritte zur Reihen‑Konfiguration.

### Export nach PDF

Falls Ihr nachgelagerter Workflow PDF erfordert, rufen Sie `doc.save("output/PieFormatted.pdf");` nach dem Erstellen des Diagramms auf. Das visuelle Layout bleibt identisch.

## Vollständige Quellcode‑Auflistung

Nachfolgend finden Sie die komplette, eigenständige Java‑Datei, die Sie in Ihre IDE kopieren‑und‑einfügen können.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Kompilieren und führen Sie das Programm mit `mvn compile exec:java -Dexec.mainClass=PieChartExample` (oder dem entsprechenden Gradle‑Befehl) aus. Die erzeugte Word‑Datei enthält das vollständig formatierte Kreisdiagramm.

## Fazit

Sie wissen jetzt, **wie man ein Kreisdiagramm** in ein Word‑Dokument mit Java einfügt, **wie man ein Kreisdiagramm in Word erstellt**, **wie man Prozentsätze auf Kreisdiagramm anzeigt** und **wie man ein Diagramm zu Word‑Dokument hinzufügt** mit Führungslinien. Das vollständige Beispiel demonstriert jeden Schritt, erklärt, warum der Code so geschrieben ist, und gibt Tipps zur Anpassung.

Als Nächstes könnten Sie erkunden:

- Datenbeschriftungen mit benutzerdefinierten Schriftarten hinzufügen (**Prozentsätze auf Kreisdiagramm**‑Variationen)
- Mehrere Diagramme in einem einzigen Dokument kombinieren (**Diagramm zu Word‑Dokument**‑Anwendungsfall)
- Automatisierte Berichtserstellung mit Tabellen und Diagrammen zusammen

Experimentieren Sie gern mit Farben, Segmentreihenfolge oder dem Export nach PDF. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}