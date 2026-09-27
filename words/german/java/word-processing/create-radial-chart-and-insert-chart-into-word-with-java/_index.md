---
category: general
date: 2026-09-27
description: Erstelle ein Radialdiagramm in Java und füge das Diagramm in Word ein.
  Erfahre, wie du die Diagrammgröße festlegst, Datenreihen hinzufügst und ein leeres
  Word‑Dokument erzeugst.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: de
lastmod: 2026-09-27
og_description: Erstellen Sie ein Radialdiagramm in Java und fügen Sie das Diagramm
  in Word ein. Diese Anleitung zeigt, wie Sie die Diagrammgröße festlegen, Datenreihen
  hinzufügen und ein leeres Word‑Dokument erstellen.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Radialdiagramm erstellen und Diagramm mit Java in Word einfügen
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Radialdiagramm erstellen und Diagramm mit Java in Word einfügen
url: /de/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie ein radial chart und fügen Sie das chart in Word mit Java ein

Wenn Sie ein **radial chart** in einer Word‑Datei mit Java erstellen müssen, zeigt Ihnen dieses Tutorial genau, wie es geht. Sie sehen, wie Sie **chart in Word einfügen**, die Abmessungen des charts festlegen und ein **blank Word document** von Grund auf erstellen.

Wir gehen jeden erforderlichen Schritt durch, vom Initialisieren des Dokuments über das Hinzufügen einer Datenreihe bis zum Speichern der finalen `.docx`. Am Ende haben Sie eine voll funktionsfähige Word‑Datei, die ein radial chart enthält, und Sie verstehen **how to set chart size** und **add data series chart** für zukünftige Anpassungen.

## Voraussetzungen

* Java 17 oder höher (der Code kompiliert mit jedem modernen JDK)
* Aspose.Words for Java 24.9 oder neuer – die Methode `setShowGraduations` ist erst ab dieser Version verfügbar
* Eine IDE oder ein Build‑Tool (Maven/Gradle), das das Aspose.Words‑JAR einbinden kann
* Grundlegende Kenntnisse der Java‑Syntax und der Maven/Gradle‑Abhängigkeitsverwaltung

> **Profi‑Tipp:** Wenn Sie Maven verwenden, fügen Sie Folgendes zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Schritt 1: Erstellen Sie ein leeres Word‑Dokument

Ein leeres Dokument ist die Leinwand, auf der das Diagramm platziert wird. Die Klasse `Document` repräsentiert die gesamte `.docx`‑Datei.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Das Erstellen eines leeren Dokuments stellt sicher, dass kein bereits vorhandener Inhalt das Diagrammlayout beeinträchtigt.

## Schritt 2: Initialisieren Sie einen DocumentBuilder

`DocumentBuilder` bietet praktische Methoden zum Einfügen von Objekten, Text und anderen Elementen in das Dokument.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Der Builder wird später verwendet, um **chart in Word einzufügen**.

## Schritt 3: Erstellen Sie das radial chart

Aspose.Words unterstützt viele Diagrammtypen; `ChartType.RADIAL` erzeugt ein radial (polar) chart.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Zu diesem Zeitpunkt existiert das chart, hat jedoch keine Daten, Größe oder visuellen Optionen.

## Schritt 4: Fügen Sie dem chart eine Datenreihe hinzu

Ein chart ohne Datenreihe ist leer. Die Methode `add` nimmt einen Seriennamen und ein Array von Werten.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Sie können mehrere Serien hinzufügen, indem Sie `add` wiederholt aufrufen. Dies erfüllt die Anforderung **add data series chart**.

## Schritt 5: Graduierungen aktivieren (optional)

Graduierungen sind die radialen Gitternetzlinien, die die Lesbarkeit verbessern. Sie sind erst ab Version 24.9 verfügbar.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Wenn Sie eine ältere Aspose.Words‑Version verwenden, wird diese Zeile eine Ausnahme auslösen – prüfen Sie also zuerst Ihre Bibliotheksversion.

## Schritt 6: Setzen Sie die Abmessungen des charts

Die Kontrolle der Diagrammgröße ermöglicht es Ihnen, es gut innerhalb der Seitenränder zu platzieren. Dies behandelt **how to set chart size**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Sie können die Breiten‑ und Höhenwerte an Ihre Layout‑Bedürfnisse anpassen. Denken Sie daran, dass 1 Punkt ≈ 1/72 Zoll entspricht.

## Schritt 7: Fügen Sie das chart in das Word‑Dokument ein

Jetzt ist das chart bereit zum Einfügen. Die Methode `insertChart` von `DocumentBuilder` übernimmt das Einfügen.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Dies ist der Kern der **insert chart into word**‑Operation.

## Schritt 8: Speichern Sie das Dokument

Schließlich schreiben Sie das Dokument auf die Festplatte. Die Datei enthält das radial chart, das Sie gerade erstellt haben.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Das Ausführen des Programms erzeugt `RadialChart.docx` im Arbeitsverzeichnis des Projekts. Das Öffnen der Datei in Microsoft Word zeigt ein radial chart mit drei Datenpunkten und sichtbaren Graduierungen.

### Erwartete Ausgabe

* Eine Word‑Datei mit dem Namen `RadialChart.docx`
* In der Datei eine einzelne Seite, die ein radial chart mit der Größe 400 × 300 Punkten enthält
* Das chart zeigt eine Serie mit dem Titel **Series 1** und den Werten **10, 20, 30**
* Graduierungen (radiale Gitternetzlinien) sind um das chart herum sichtbar

## Häufige Variationen und Sonderfälle

| Situation | Was zu ändern | Grund |
|-----------|----------------|--------|
| **Multiple series** | Rufen Sie `chart.getSeries().add(...)` für jede Serie auf | Ermöglicht vergleichende Datenvisualisierung |
| **Different chart type** | Ersetzen Sie `ChartType.RADIAL` durch `ChartType.COLUMN` (oder einen anderen) | Verwenden Sie den Diagrammtyp, der Ihre Daten am besten darstellt |
| **Custom colors** | Greifen Sie auf `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` zu | Verbessert das visuelle Branding |
| **Older Aspose.Words version** | Lassen Sie die Zeile `setShowGraduations` weg oder aktualisieren Sie die Bibliothek | Verhindert `NoSuchMethodError` |
| **Saving to a different format** | Use `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Erzeugt ein PDF anstelle eines DOCX |

## Vollständiges ausführbares Beispiel

Unten finden Sie das vollständige, eigenständige Java‑Programm. Kopieren Sie es in eine Datei namens `RadialChartExample.java`, fügen Sie die Aspose.Words‑Abhängigkeit hinzu und führen Sie es aus.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Fazit

Sie wissen jetzt, wie man programmgesteuert **create radial chart** durchführt, **add data series chart**, **how to set chart size** steuert und **insert chart into Word** einfügt, während man von einem **blank Word document** ausgeht. Das Beispiel verwendet Aspose.Words for Java 24.9, aber dieselben Konzepte gelten für andere Diagrammbibliotheken, die eine ähnliche API bereitstellen.

### Nächste Schritte

* Erkunden Sie weitere Diagrammtypen (`ChartType.PIE`, `ChartType.LINE` usw.) – dies knüpft an das sekundäre Stichwort **insert chart into word** an.
* Passen Sie Achsenbeschriftungen, Legenden und Farben an Ihre Markenrichtlinien an.
* Generieren Sie Diagramme dynamisch aus Datenbankabfragen oder CSV‑Dateien.
* Konvertieren Sie das resultierende `.docx` für die Verteilung in PDF (`doc.save("output.pdf", SaveFormat.PDF)`).

Fühlen Sie sich frei, mit den Abmessungen, Serien‑Daten und Stiloptionen zu experimentieren, um die gewünschte Visualisierung zu erstellen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words for Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Word‑Dokument mit Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Flächendiagramm in ein Word‑Dokument einfügen](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}