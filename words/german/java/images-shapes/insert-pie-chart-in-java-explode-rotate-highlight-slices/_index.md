---
category: general
date: 2026-07-20
description: Kreisdiagramm in Java einfügen mit einer Schritt‑für‑Schritt‑Anleitung.
  Erfahren Sie, wie Sie ein Segment explodieren, das Kreisdiagramm drehen, ein Segment
  hervorheben und ein Segment anpassen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: de
lastmod: 2026-07-20
og_description: Kreisdiagramm in Java einfügen und lernen, wie man ein Segment explodiert,
  das Diagramm dreht, ein Segment hervorhebt und ein Segment anpasst, um professionelle
  visuelle Berichte zu erstellen.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Kuchendiagramm in Java einfügen – Explodieren, Drehen & Hervorheben
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Kuchendiagramm in Java einfügen – Segmente explodieren, drehen und hervorheben
url: /de/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kreisdiagramm in Java einfügen – Slice explodieren, drehen & Slice hervorheben

Haben Sie jemals **Kreisdiagramm einfügen** müssen in einem Java‑Bericht, waren sich aber nicht sicher, wie man ein einzelnes Segment hervorheben kann? Sie sind nicht allein. Egal, ob Sie ein Dashboard erstellen, eine Rechnung generieren oder einfach Umfrageergebnisse visualisieren, ein gut gestaltetes Kreisdiagramm kann Rohdaten in sofort verständliche Erkenntnisse verwandeln.

In diesem Tutorial sehen Sie ein komplettes, sofort ausführbares Beispiel, das zeigt, wie man ein Kreisdiagramm einfügt, **wie man ein Segment explodiert**, **wie man ein Kreisdiagramm dreht** und sogar **ein Kreisdiagramm‑Segment hervorhebt** mit benutzerdefinierten Farben. Am Ende haben Sie ein wiederverwendbares Snippet, das Sie in jedes Java‑Projekt einbinden können, das die beliebte *JFreeChart*‑Bibliothek (oder eine ähnliche API) verwendet.

## Voraussetzungen

- Java 17 oder höher (der Code kompiliert auch mit älteren Versionen, aber wir verwenden die moderne `var`‑Syntax zur Kürze).  
- Maven oder Gradle, um die `org.jfree:jfreechart`‑Abhängigkeit zu holen.  
- Grundlegendes Verständnis von Java‑Klassen und dem Konzept eines Chart‑Builders.  

Falls Sie noch nie eine Bibliothek zu einem Maven‑Projekt hinzugefügt haben, fügen Sie einfach Folgendes in Ihre `pom.xml` ein:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Das war’s – keine weitere Einrichtung erforderlich.

## Schritt 1: Kreisdiagramm einfügen – Builder und Chart‑Objekt erstellen

Zuerst benötigen wir einen *Builder* (denken Sie an eine Fabrik), der weiß, wie man Diagramme erzeugt. In JFreeChart übernimmt die `ChartFactory` die schwere Arbeit.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Warum beginnen wir mit dem Datensatz? Weil das Diagramm selbst nur ein visueller Wrapper um die Zahlen ist. Durch das **Einfügen eines Kreisdiagramms** hier haben wir bereits eine 400 × 300‑Leinwand (die Größe wird später beim Rendern in ein Bild angewendet).

## Schritt 2: Slice explodieren – Erstes Segment betonen

Jetzt, wo das Diagramm existiert, lassen Sie uns das erste Segment hervorheben. Das Explodieren eines Segments zieht es leicht vom Kreis weg und lenkt das Auge des Betrachters.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Beachten Sie, dass wir die Phrase **how to explode slice** im Methodennamen verwenden; das macht die Absicht kristallklar. Die Methode `setExplodePercent` nimmt einen Schlüssel (die Segment‑Bezeichnung) und einen Prozentsatz, sodass Sie den „Aus‑pop‑Abstand“ nach Bedarf anpassen können.

## Schritt 3: Kreisdiagramm drehen – Startwinkel ändern

Ein Standard‑Kreisdiagramm beginnt bei der 12‑Uhr‑Position. Manchmal soll das erste Segment an einer anderen Stelle beginnen – vielleicht um sich an einem Design‑Mock‑up auszurichten oder ein anderes Diagramm zu ergänzen.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Der Aufruf `rotateChart(chart, 45)` dreht das gesamte Kreisdiagramm, sodass das Segment „Apples“ bei einem Winkel von 45 Grad beginnt, genau das, was die Anforderung **how to rotate pie chart** verlangt.

## Schritt 4: Kreisdiagramm‑Segment hervorheben – Benutzerdefinierte Farben und Beschriftungen

Neben dem Explodieren möchten Sie einem Segment vielleicht eine einzigartige Farbe oder eine fette Beschriftung geben, um das **Kreisdiagramm‑Segment wirklich hervorzuheben**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Hier haben wir das **customize pie chart slice** durch Ändern seiner Farbe und Beschriftungsstil angepasst. Sie können die Farbe oder Schriftart gerne austauschen, um sie an Ihre Markenpalette anzupassen.

## Schritt 5: Diagramm als Bild rendern (optional aber praktisch)

Die meisten realen Anwendungen benötigen das Diagramm als PNG, JPEG oder sogar als PDF. Unten finden Sie eine schnelle Methode, das Diagramm in eine Datei zu schreiben.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Das Ausführen des kompletten Ablaufs erzeugt ein 400 × 300 PNG, das etwa so aussieht:

![Kreisdiagramm‑Beispiel](image.png){: alt="Kreisdiagramm‑Beispiel mit explodiertem und gedrehten Segment"}

## Voll funktionsfähiges Beispiel

Wenn wir alles zusammenführen, hier ist eine `main`‑Methode, die Sie in eine neue Java‑Klasse kopieren und ausführen können:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Erwartete Ausgabe

Das Ausführen des Programms erstellt eine Datei namens **fruit-pie.png**. Öffnen Sie sie und Sie sehen:

- Ein 400 × 300‑Kreisdiagramm mit dem Titel „Fruit Distribution“.  
- Das „Apples“-Segment ist um 15 % nach außen explodiert.  
- Das gesamte Diagramm ist gedreht, sodass „Apples“ bei 45 Grad beginnt.  
- The exploded

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Scatter‑Diagramm einfügen](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Flächendiagramm einfügen](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}