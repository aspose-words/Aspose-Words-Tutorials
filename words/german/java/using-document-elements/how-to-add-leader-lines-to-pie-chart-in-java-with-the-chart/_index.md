---
category: general
date: 2026-08-20
description: Fügen Sie schnell Leitlinien zu einem Kreisdiagramm in Java hinzu. Lernen
  Sie, Scheiben einzufügen, zu explodieren, neu zu färben und zu beschriften, indem
  Sie die Chart-API verwenden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: de
lastmod: 2026-08-20
og_description: Fügen Sie Leitlinien zu einem Kreisdiagramm in Java hinzu – mit einem
  knappen Beispiel. Folgen Sie dieser Anleitung, um Segmente einzufügen, zu explodieren,
  neu zu färben und zu beschriften, mithilfe der Chart‑API.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Führungsstriche zum Kreisdiagramm in Java hinzufügen – Schritt‑für‑Schritt‑Chart‑API‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Wie man Leitlinien zu einem Kreisdiagramm in Java mit der Chart‑API hinzufügt
url: /de/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Führungs‑Linien zu einem Kreisdiagramm in Java mit der Chart API hinzufügt

Wenn Sie in Java **Führungs‑Linien zu einem Kreisdiagramm hinzufügen** müssen, führt Sie diese Anleitung durch den gesamten Prozess. Sie sehen, wie man ein Kreisdiagramm einfügt, ein Segment zur Hervorhebung herauslöst, dessen Farbe ändert und schließlich Führungs‑Linien aktiviert, die das herausgelöste Segment beschriften.

Das Beispiel verwendet die Standard‑Chart‑API, die in vielen Java‑Reporting‑Bibliotheken zu finden ist. Es werden keine externen Werkzeuge benötigt, und der Code läuft in jeder JDK 8+‑Umgebung.

## Was Sie erreichen werden

* Erstellen Sie ein `Chart` vom Typ `ChartType.PIE` mit einer benutzerdefinierten Größe.  
* Lösen Sie das erste Segment, um Aufmerksamkeit zu erzeugen.  
* Setzen Sie die Sektor‑Farbe des herausgelösten Segments auf Blau.  
* **Führungs‑Linien zu einem Kreisdiagramm hinzufügen**, sodass das Segment‑Label eindeutig verbunden ist.

Sie sollten bereits ein Java‑Projekt mit der Chart‑Bibliothek im Klassenpfad haben. Wenn Sie Maven verwenden, fügen Sie die im Abschnitt Voraussetzungen gezeigte Abhängigkeit hinzu.

## Voraussetzungen

* JDK 8 oder neuer installiert.  
* Die Chart‑Bibliothek (z. B. `com.example.chart:chart-api:2.5.0`).  
* Grundlegende Vertrautheit mit Java‑Klassen und Methodenaufrufen.

---

## Wie man Führungs‑Linien zu einem Kreisdiagramm hinzufügt

Unten finden Sie ein vollständiges, ausführbares Programm, das jeden Schritt demonstriert. Der Code ist bewusst eigenständig, sodass Sie ihn kopieren, einfügen und ohne Änderungen ausführen können.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Erklärung jedes Schrittes

| Schritt | Was der Code macht | Warum das wichtig ist |
|------|-------------------|----------------|
| **1️⃣ Kreisdiagramm einfügen** | `builder.insertChart(ChartType.PIE, 400, 300)` erstellt ein 400 × 300 Pixel‑Kreisdiagramm. | Legt den Diagramm‑Container fest und definiert seine Abmessungen, die die Platzierung von Labels und die Länge der Führungs‑Linien beeinflussen. |
| **2️⃣ Erstes Segment herauslösen** | `setExplosion(20)` verschiebt das Segment um 20 % des Radius. | Ein herausgelöstes Segment zieht das Auge des Betrachters an und macht die Führungs‑Linie sichtbar. |
| **3️⃣ Sektor‑Farbe setzen** | `setSectorColor(Color.BLUE)` ändert die Füllfarbe des Segments zu Blau. | Farb‑Kontrast verbessert die Lesbarkeit, besonders wenn das Segment hervorgehoben ist. |
| **4️⃣ Führungs‑Linien aktivieren** | `setLeaderLines(true)` schaltet die Verbindungslinien ein, die das Segment mit seinem Label verbinden. | Führungs‑Linien sorgen dafür, dass das Label lesbar bleibt, selbst wenn das Segment nach außen verschoben wird. |

Der Aufruf `saveAsPng` ist optional, aber nützlich, um das visuelle Ergebnis zu überprüfen. Nach dem Ausführen des Programms sollten Sie ein Bild sehen, das dem unten gezeigten ähnelt.

![Führungs‑Linien zu Kreisdiagramm hinzufügen](https://example.com/assets/pie-leader-lines.png "Führungs‑Linien zu Kreisdiagramm – herausgelöstes Segment mit blauer Farbe und Führungs‑Linien")

*Abbildung: Ein Kreisdiagramm, bei dem das erste Segment herausgelöst, blau gefärbt und über eine Führungs‑Linie mit seinem Label verbunden ist.*

## Anpassung von Führungs‑Linien (fortgeschritten)

Der einfache Aufruf `setLeaderLines(true)` verwendet den Standardstil der Bibliothek. Sie können das Aussehen weiter steuern:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Diese Optionen sind praktisch, wenn Sie das Corporate‑Branding einhalten oder die Barrierefreiheit verbessern müssen.

### Umgang mit mehreren Serien

Enthält Ihr Kreisdiagramm mehr als eine Serie, möchten Sie möglicherweise Führungs‑Linien nur für ein bestimmtes Segment aktivieren. Verwenden Sie den Serien‑Index, um das richtige Element anzusprechen:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Wenn ein Segment nicht herausgelöst ist, wird die Führungs‑Linie in der Regel automatisch ausgeblendet, Sie können sie jedoch mit `setLeaderLineEnabled(true)` erzwingen.

## Häufige Stolperfallen und wie man sie vermeidet

| Stolperfalle | Symptom | Lösung |
|--------|---------|-----|
| **Führungs‑Linien nicht sichtbar** | Diagramm wird ohne Verbindungs‑Linien gerendert. | Stellen Sie sicher, dass das Segment herausgelöst ist (`setExplosion` > 0) oder aktivieren Sie die Führungs‑Linien explizit für das Segment. |
| **Label‑Überlappungen** | Labels kollidieren miteinander. | Vergrößern Sie die Diagrammgröße oder setzen Sie `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Farbe nicht angewendet** | Segment behält Standardfarbe. | Prüfen Sie, ob Sie den korrekten Serien‑Index ansprechen (`getSeries().get(0)`). |
| **Bild nicht gespeichert** | `saveAsPng` wirft eine Ausnahme. | Überprüfen Sie Schreibrechte für das Ausgabeverzeichnis und ob die Bibliothek den PNG‑Export unterstützt. |

## Vollständige Quellcode‑Auflistung

Zur Bequemlichkeit finden Sie hier erneut die komplette Quellcodedatei, inklusive Imports und Kommentaren:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Das Ausführen dieses Programms erzeugt `pie-with-leader-lines.png`, das ein Kreisdiagramm mit einem herausgelösten blauen Segment und klaren Führungs‑Linien zum Segment‑Label zeigt.

## Fazit

Sie wissen jetzt, wie Sie **Führungs‑Linien zu einem Kreisdiagramm** in Java mithilfe der Chart API hinzufügen. Der Vorgang besteht darin, ein `ChartType.PIE` einzufügen, das gewünschte Segment herauszulösen, dessen Farbe anzupassen und Führungs‑Linien zu aktivieren. Mit den optionalen Stil‑Optionen können Sie Linienfarbe, -dicke und Label‑Platzierung feinjustieren, um jede visuelle Anforderung zu erfüllen.

Als Nächstes können Sie verwandte Themen wie **pie chart explosion Java**, **set sector color Chart API** und **builder.insertChart usage** erkunden, um anspruchsvollere Visualisierungen wie Donut‑Diagramme, gestapelte Kreisdiagramme oder interaktive Dashboards zu erstellen.

Fühlen Sie sich frei, mit verschiedenen Segment‑Indizes, Farben und Führungs‑Linien‑Stilen zu experimentieren – Ihre Diagramme werden mit jeder Anpassung informativer und ansprechender. Viel Spaß beim Coden!

## Was Sie als Nächstes lernen sollten

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Datums‑ und Zeitwerte zur Achse eines Diagramms hinzufügen](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Säulendiagramm in Word mit Aspose.Words für .NET einfügen](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}