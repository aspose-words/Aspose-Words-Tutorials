---
category: general
date: 2026-11-25
description: Erfahren Sie, wie Sie in Java ein Kreisdiagramm erstellen, das Kreisdiagramm
  in ein Word‑Dokument einfügen, ein Kuchenscheiben‑Segment hervorheben und die Diagrammausrichtung
  ändern – mit klaren Codebeispielen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: de
lastmod: 2026-11-25
og_description: Erstelle ein Kreisdiagramm in Java, füge das Kreisdiagramm in ein
  Dokument ein, explodiere ein Segment und ändere die Diagrammausrichtung mit Schritt‑für‑Schritt‑Code.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Erstelle ein Kreisdiagramm in Java – einfügen, Stück herauslösen und drehen
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Wie man ein Kreisdiagramm erstellt, einfügt und die Ausrichtung in Java anpasst
url: /de/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Kreisdiagramm erstellt, einfügt und die Orientierung in Java anpasst

Wenn Sie ein **create a pie chart** in ein Word‑Dokument einfügen müssen, zeigt Ihnen diese Anleitung genau, wie Sie das tun. Sie sehen, wie man **insert pie chart**, ein Segment zur Hervorhebung explodiert und **change chart orientation** mit einer einfachen Drehung.

Das Tutorial deckt alles ab, was Sie benötigen – von der Einrichtung der Aspose.Words for Java‑Bibliothek bis zur Erstellung einer finalen `.docx`‑Datei, die ein rotiertes, explodiertes Kreisdiagramm anzeigt. Keine externe Dokumentation ist nötig; folgen Sie einfach den Schritten und führen Sie den Code aus.

## Voraussetzungen

* Java 17 oder neuer installiert.
* Maven oder Gradle zur Verwaltung von Abhängigkeiten.
* Eine gültige Aspose.Words for Java‑Lizenz (oder verwenden Sie den kostenlosen Evaluierungsmodus).

Fügen Sie die Aspose.Words‑Abhängigkeit zu Ihrer `pom.xml` (Maven) oder `build.gradle` (Gradle) hinzu. Beispiel für Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Profi‑Tip:** Halten Sie die Bibliotheksversion aktuell; die neueste Version (24.10 zum Zeitpunkt dieses Schreibens) enthält Fehlerbehebungen für die Diagrammdarstellung.

## Schritt 1: Kreisdiagramm erstellen und in das Dokument einfügen

Der erste Schritt besteht darin, **create pie chart**‑Objekte zu erstellen und in einer Word‑Datei einzubetten. Der untenstehende Code erzeugt ein einfaches Dokument, fügt einen Diagramm‑Platzhalter hinzu und fügt ein Kreisdiagramm mit der Größe 400 × 300 Pixel ein.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Warum das wichtig ist:** `builder.insertChart` erstellt einen Diagramm‑Platzhalter, den Aspose.Words beim Speichern des Dokuments automatisch in ein OOXML‑Diagramm umwandelt. Das Argument `ChartType.PIE` weist die Bibliothek an, ein Kreisdiagramm zu rendern, wodurch die Anforderung **insert pie chart** erfüllt wird.

## Schritt 2: Kreisdiagramm‑Segment explodieren, um ein Segment hervorzuheben

Das Explodieren eines Segments lenkt die Aufmerksamkeit auf einen bestimmten Datenpunkt. Die folgende Zeile explodiert das erste Segment (Index 0) um 10 Punkte:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Sie können den Index ändern, um ein anderes Segment zu treffen, oder den Explosionsabstand für einen dezenteren Effekt anpassen. Das Explodieren eines Segments ist die Standardmethode, um **explode pie slice** in Aspose.Words zu erreichen.

## Schritt 3: Diagramm‑Orientierung durch Drehen ändern

Das Drehen des Diagramms bietet eine neue visuelle Perspektive. Verwenden Sie `setRotationAngle`, um das gesamte Diagramm im Uhrzeigersinn zu drehen (der Winkel wird in Grad gemessen).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

Der obige Aufruf erfüllt die Anforderungen **rotate pie chart** und **change chart orientation**. Jeder Winkel zwischen 0 und 360 Grad wird akzeptiert.

## Vollständiges ausführbares Beispiel

Wenn man alles zusammenfügt, hier ein vollständiges, eigenständiges Programm, das ein Kreisdiagramm erstellt, ein Segment explodiert und das Diagramm dreht. Führen Sie es aus Ihrer IDE oder über die Befehlszeile mit `java -cp <classpath> PieChartDemo` aus.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Erwartete Ausgabe

* Eine Datei namens **CreatePieChartDemo.docx** erscheint im Arbeitsverzeichnis.
* Öffnet man die Datei in Microsoft Word, wird ein 400 × 300 Pixel‑Kreisdiagramm angezeigt.
* Das erste Segment (Q1) wird um 10 Punkte nach außen verschoben und erzeugt einen **explode pie slice**‑Effekt.
* Das gesamte Diagramm ist um 45 Grad geneigt, was **change chart orientation** und **rotate pie chart** demonstriert.

## Häufige Variationen und Sonderfälle

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Andere Diagrammgröße** | Change the `400, 300` arguments in `insertChart`. |
| **Mehrere Serien** | Add more `ChartSeries` objects to `chart.getSeries()`. |
| **Ein anderes Segment explodieren** | Use `setExplode(sliceIndex, distance)` with the desired `sliceIndex`. |
| **Keine Rotation erforderlich** | Omit the `setRotationAngle` call or set the angle to `0`. |
| **Export nach PDF statt DOCX** | After building the document, call `doc.save("output.pdf")` with the PDF format. |

> **Achten Sie darauf:** Die Verwendung eines negativen Explosionsabstands löst `IllegalArgumentException` aus. Geben Sie immer einen nicht‑negativen Wert an.

## Leistungstipp

Wenn Sie viele Diagramme in einer Schleife erzeugen, verwenden Sie einen einzigen `DocumentBuilder` und rufen Sie `insertChart` nur für jede Iteration auf. Das reduziert den Speicherverbrauch und beschleunigt die Verarbeitung.

## Fazit

Sie wissen jetzt, wie Sie **create pie chart**, **insert pie chart**, **explode pie slice** und **rotate pie chart** mit Aspose.Words for Java verwenden. Das vollständige Beispiel demonstriert den gesamten Workflow – vom Initialisieren des Dokuments bis zum Speichern einer Datei, die ein rotiertes, explodiertes Kreisdiagramm visualisiert.

Als Nächstes können Sie **change chart orientation** weiter erforschen, indem Sie 3‑D‑Effekte anwenden, oder mit anderen Diagrammtypen wie **Bar** oder **Line** experimentieren. Die gleichen API‑Muster gelten, sodass die Erweiterung dieses Tutorials unkompliziert ist.

Passen Sie die Daten, den Segment‑Index oder den Rotationswinkel an Ihre eigenen Reporting‑Bedürfnisse an und teilen Sie Ihre Ergebnisse mit der Community!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Kreisdiagramm in ein Word‑Dokument mit Java einfügt](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Wie man ein Kreisdiagramm‑Segment in Java explodiert – Aspose.Words Diagramm‑Tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}