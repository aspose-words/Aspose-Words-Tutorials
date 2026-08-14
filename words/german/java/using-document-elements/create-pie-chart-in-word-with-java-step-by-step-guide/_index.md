---
category: general
date: 2026-08-14
description: Erstellen Sie ein Kreisdiagramm in Word mit Java unter Verwendung von
  Aspose.Words. Erfahren Sie, wie Sie Diagrammdaten hinzufügen und ein Kreisdiagrammsegment
  mit nur wenigen Zeilen drehen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: de
lastmod: 2026-08-14
og_description: Erstellen Sie ein Kreisdiagramm in Word mit Java unter Verwendung
  von Aspose.Words. Dieses Tutorial zeigt, wie man Datenreihen zum Diagramm hinzufügt
  und ein Kreisdiagrammsegment schnell dreht.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Kreisdiagramm in Word mit Java erstellen – vollständiger Programmierleitfaden
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Kreisdiagramm in Word mit Java erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines Kreisdiagramms in Word mit Java – Schritt‑für‑Schritt‑Anleitung

Wenn Sie **ein Kreisdiagramm in Word** programmgesteuert erstellen müssen, zeigt Ihnen dieser Leitfaden genau, wie Sie dies mit Java und Aspose.Words tun. Sie lernen den kompletten Workflow, vom Einfügen des Diagramms über das Hinzufügen von Datenpunkten bis zum Drehen des ersten Segments.

Das direkte Erzeugen eines Diagramms in einer `.docx`‑Datei eliminiert den manuellen Kopier‑Einfügen‑Schritt und ermöglicht die Automatisierung von Berichten, Rechnungen oder Dashboards. Dabei behandeln wir auch **wie man Serien‑Daten zu einem Diagramm hinzufügt** und wie man **ein Kreisdiagramm‑Segment dreht** für eine bessere visuelle Betonung.

## Kreisdiagramm in Word erstellen – Übersicht

Aspose.Words for Java bietet eine fluente `DocumentBuilder`‑API, mit der ein Diagramm‑Objekt in ein Word‑Dokument eingefügt werden kann. Der von Ihnen gewählte Diagrammtyp bestimmt das Standard‑Layout, und Sie können die Serien, Farben, Winkel und sogar zu einer Donut‑Form wechseln – alles mit einem einzigen Methodenaufruf.

### Warum Aspose.Words verwenden?

* **Kein Microsoft Office erforderlich** – die Bibliothek funktioniert auf jedem Server oder CI‑Umgebung.  
* **Vollständige .docx‑Treue** – das erzeugte Diagramm sieht identisch aus wie ein manuell in Word erstelltes.  
* **Einzeldatei‑Abhängigkeit** – einfach das JAR hinzufügen und Sie können loslegen.

## Wie man Serien‑Daten zu einem Diagramm hinzufügt

Ein Diagramm ohne Daten ist nur ein Platzhalter. Das `Chart`‑Objekt stellt eine `Series`‑Sammlung bereit; jede Serie enthält eine Liste numerischer Werte, die den Segmenten (bei einem Kreisdiagramm) bzw. Punkten (bei einer Linie) zugeordnet werden. Daten hinzuzufügen ist einfach:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Was der Code macht:**  
* `chart.getSeries()` gibt eine `List<ChartSeries>` zurück.  
* `get(0)` wählt die erste Serie aus, weil ein Kreisdiagramm definitionsgemäß nur eine Serie enthält.  
* `add(double)` fügt einen Datenpunkt hinzu. Die Werte werden automatisch in Prozentsätze umgewandelt, die bei der Darstellung des Diagramms 100 % ergeben.

> **Profi‑Tipp:** Wenn Ihre Datenquelle mehr als drei Kategorien enthält, fügen Sie weiterhin Werte auf dieselbe Weise hinzu. Aspose.Words erstellt automatisch zusätzliche Segmente.

## Kreisdiagramm‑Segment drehen

Manchmal möchten Sie, dass ein bestimmtes Segment bei einem bestimmten Winkel beginnt, sodass das wichtigste Segment dem Betrachter zugewandt ist. Die Methode `setFirstSliceAngle(double)` dreht das gesamte Diagramm und verschiebt damit den Start des ersten Segments:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

Der Winkel wird in Grad im Uhrzeigersinn von der Vertikalachse aus gemessen. Wird er auf `0` (Standard) gesetzt, befindet sich das erste Segment oben. Passen Sie den Wert an, um ein Segment hervorzuheben oder einer Designrichtlinie zu entsprechen.

> **Häufige Frage:** *Beeinflusst das Drehen die Datenreihenfolge?*  
> Nein. Die Datenreihenfolge bleibt unverändert; nur die visuelle Startposition ändert sich.

## Vollständiges Java‑Beispiel

Unten finden Sie ein vollständiges, sofort ausführbares Programm, das ein Word‑Dokument mit einem Kreisdiagramm erstellt, Serien‑Daten hinzufügt, das Segment dreht und die Datei speichert. Alle erforderlichen Importe sind aufgelistet, sodass Sie den Code in jede IDE kopieren können.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Erwartete Ausgabe

* Eine Datei namens **PieChart.docx** erscheint im Ordner `output`.  
* Öffnet man die Datei in Microsoft Word, wird ein farbenfrohes Kreisdiagramm mit drei Segmenten (40 %, 30 %, 30 %) angezeigt.  
* Das Diagramm ist um 45° im Uhrzeigersinn gedreht, sodass das erste Segment leicht rechts von der Vertikalachse beginnt.

## Häufige Fallstricke und bewährte Vorgehensweisen

| Problem | Warum es passiert | Lösung |
|-------|----------------|-----|
| **Diagramm erscheint leer** | Das Dokument wurde gespeichert, bevor das Diagramm vollständig gerendert war. | Rufen Sie `doc.save()` **nach** allen Diagramm‑Modifikationen auf. |
| **Segmentwerte summieren sich nicht zu 100 %** | Das Hinzufügen von Rohzahlen, die keine Prozentsätze darstellen, kann zu unerwarteter Skalierung führen. | Geben Sie Werte an, die logisch Teile eines Ganzen repräsentieren, oder lassen Sie Aspose.Words die Prozentsätze automatisch berechnen. |
| **Drehung hat keine Wirkung** | Die Verwendung von `ChartType.DOUGHNUT` ohne Festlegung von `holeSize` kann den Drehungseffekt verbergen. | Behalten Sie das Diagramm als `PIE` oder passen Sie `holeSize` nach dem Setzen des Winkels an. |
| **Dateipfad‑Fehler** | Relative Pfade können sich unter Windows und Linux unterschiedlich auflösen. | Verwenden Sie `Paths.get("output", "PieChart.docx").toString()` oder einen absoluten Pfad für Produktionscode. |

### Tipps für den Produktionseinsatz

* **Den `DocumentBuilder` wiederverwenden** – Sie können mehrere Diagramme im selben Dokument einfügen, indem Sie `insertChart` wiederholt aufrufen.  
* **Styling** – verwenden Sie `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`, um Prozentsätze direkt im Diagramm anzuzeigen.  
* **Performance** – erzeugen Sie das Diagramm einmal und klonen Sie es (`chart.deepClone()`), wenn Sie identische Diagramme an mehreren Stellen benötigen.

## Kreisdiagramm‑Segment drehen – erweiterte Szenarien

* **Dynamischer Winkel** – berechnen Sie den Winkel basierend auf den Daten (z. B. das größte Segment oben beginnen lassen).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Mehrere Serien** – obwohl ein Kreisdiagramm normalerweise eine Serie hat, ermöglicht Aspose.Words das Hinzufügen weiterer für gestapelte Kreisdiagramme. Die Drehung gilt weiterhin nur für die erste Serie.

## Fazit

Sie wissen jetzt, wie Sie mit Java **ein Kreisdiagramm in Word erstellen**, **Serien‑Daten zu einem Diagramm hinzufügen** und **ein Kreisdiagramm‑Segment für visuelle Betonung drehen**. Das vollständige Beispiel demonstriert den gesamten Workflow – von der Dokumentinitialisierung bis zum Speichern der finalen `.docx`‑Datei – sodass Sie die Diagrammerstellung in jede automatisierte Berichtspipeline integrieren können.

### Was kommt als Nächstes?

* Erkunden Sie weitere Diagrammtypen (`ChartType.BAR`, `ChartType.LINE`), um Ihr Automatisierungs‑Toolkit zu erweitern.  
* Kombinieren Sie die Diagrammerstellung mit **Serienbrief** (mail merge), um personalisierte Berichte für jeden Empfänger zu erzeugen.  
* Tauchen Sie in die **Styling‑API** (`ChartFormat`, `DataLabel`, `ChartTitle`) ein, um Ihr Corporate Branding anzupassen.

Fühlen Sie sich frei, mit verschiedenen Datensätzen, Winkeln und Diagramm‑Stilen zu experimentieren. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Wie man Word mit Aspose.Words für Java in PDF konvertiert](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}