---
category: general
date: 2026-07-29
description: Fügen Sie ein Kreisdiagramm mit Aspose.Words für Java ein und lernen
  Sie, wie man ein Ringdiagramm erstellt, ein Kreisdiagramm formatiert, Diagramme
  in Word formatiert und die Diagrammgröße anpasst.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: de
lastmod: 2026-07-29
og_description: Fügen Sie ein Kreisdiagramm mit Aspose.Words für Java ein und lernen
  Sie schnell, ein Donut‑Diagramm zu erstellen, Kreisdiagramme zu formatieren, Diagramme
  in Word zu formatieren und die Diagrammgröße für professionelle Dokumente anzupassen.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Kreisdiagramm in Java einfügen – Vollständiges Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Einfügen eines Kreisdiagramms in Java mit Aspose.Words – Vollständiger Leitfaden
url: /de/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kreisdiagramm in Java mit Aspose.Words einfügen – Vollständige Anleitung

Haben Sie sich jemals gefragt, wie man **insert pie chart** in ein Word‑Dokument aus Java‑Code einfügt? Sie sind nicht der Einzige – viele Entwickler stoßen auf dieses Problem, wenn sie schnell und programmgesteuert Daten visualisieren müssen. Die gute Nachricht? Mit Aspose.Words für Java können Sie das in nur wenigen Zeilen erledigen, und dabei können Sie auch **generate doughnut chart**, **format pie chart**, **format chart Word** und **customize chart size** an Ihre Marken‑identität anpassen.

In diesem Tutorial führen wir Sie durch ein praxisnahes Beispiel, das mit dem Erstellen eines leeren Dokuments beginnt, ein Kreisdiagramm einfügt, einige visuelle Eigenschaften anpasst und schließlich die Datei speichert. Am Ende haben Sie ein wiederverwendbares Snippet, das Sie in jedes Java‑Projekt einfügen können, das Diagramm‑Automatisierung benötigt. Keine zusätzlichen Bibliotheken, kein manuelles Herumhantieren mit Office‑Interop – nur sauberer, kompilierten Java‑Code.

## Was Sie benötigen

- **Java 17** (oder ein aktuelles JDK; die API ist abwärtskompatibel)
- **Aspose.Words for Java** 22.12 oder neuer – Sie können das Maven‑Artifact oder die .jar von der Aspose‑Website holen.
- Eine einfache IDE (IntelliJ IDEA, Eclipse, VS Code…) – alles, was Ihnen erlaubt, eine `main`‑Methode auszuführen.
- Optional: eine Lizenzdatei, wenn Sie das Evaluations‑Wasserzeichen nicht möchten.

Wenn Sie das haben, können wir direkt zum Code springen.

## Schritt 1: Kreisdiagramm mit Aspose.Words einfügen

Das Erste, was wir tun, ist **insert pie chart** in ein neues Dokument einzufügen. Dieser Schritt legt die Grundlage für alles Weitere, da das Diagramm‑Objekt uns Zugriff auf Serien, Datenpunkte und visuelle Anpassungen gibt.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Warum das wichtig ist:** `DocumentBuilder.insertChart` erstellt nicht nur das Diagramm, sondern gibt auch ein `Chart`‑Objekt zurück, das wir manipulieren können. Die Breiten‑ und Höhen‑Parameter ermöglichen es Ihnen, die **customize chart size** bereits beim Erstellen festzulegen, sodass Sie später nicht nachgrößen müssen.

## Schritt 2: Donut‑Diagramm erzeugen (optional)

Wenn Ihr Design ein Loch in der Mitte erfordert – denken Sie an ein klassisches Donut‑Diagramm – macht Aspose das mit einer einzigen Zeile möglich. Die gleiche `Chart`‑Instanz kann von einem normalen Kreisdiagramm zu einem Donut umgeschaltet werden, indem die Lochgröße angepasst wird.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Tipp:** Die Lochgröße wirkt nur bei `ChartType.DONUT`. Wenn Sie den Typ als `PIE` beibehalten, wird der Aufruf ignoriert, also können Sie gern experimentieren.

## Schritt 3: Kreisdiagramm‑Segmente formatieren

Eine gute Visualisierung hebt häufig ein bestimmtes Segment hervor. Hier **format pie chart** wir, indem wir das erste Segment um 20 Punkte nach außen „explodieren“. Das lenkt den Blick des Lesers auf den wichtigsten Datenpunkt.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro‑Tipp:** Sie können über `pieChart.getSeries()` iterieren, wenn Sie mehrere Serien haben, und einzelne Farben, Rahmen oder Datenbeschriftungen festlegen. So **format chart Word** Dokumente mit umfangreichem Styling.

## Schritt 4: Daten zum Diagramm hinzufügen

Ein Diagramm ohne Daten ist nur eine dekorative Form. Lassen Sie uns ein einfaches Datenset zuführen – zum Beispiel Quartalsumsatzzahlen.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Warum wir das tun:** Durch das explizite Hinzufügen von `ChartPoint`‑Objekten stellen wir sicher, dass das Diagramm unsere Geschäftslogik widerspiegelt. Die Aufrufe `setShowCategoryName` und `setShowValue` sind Teil des **formatting the pie chart**, um sowohl Beschriftungen als auch Zahlen anzuzeigen.

## Schritt 5: Aussehen feinjustieren (customize chart size & style)

Über die anfänglichen Abmessungen hinaus möchten Sie vielleicht die Legende, den Titel oder sogar die für Datenbeschriftungen verwendete Schriftart anpassen. All das fällt unter **customize chart size** und die allgemeine Formatierung.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Randfall:** Wenn Sie später entscheiden, das Dokument als PDF zu exportieren, bleibt die Vektordaten des Diagramms scharf, weil die Größe in Punkten und nicht in Pixeln definiert ist. Das ist ein Gewinn für **format chart Word** und nachgelagerte Formate.

## Schritt 6: Dokument speichern und anzeigen

Der letzte Schritt ist so einfach wie ein Aufruf von `doc.save`. Damit wird eine `.docx`‑Datei geschrieben, die Sie in Microsoft Word, LibreOffice oder jedem Viewer öffnen können, der das OpenXML‑Format unterstützt.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Ergebnis:** Öffnen Sie `PieChart.docx` und Sie sehen ein ordentlich dimensioniertes Kreis‑ (oder Donut‑)Diagramm mit einem explodierten Segment, einem Titel und einer Legende – alles erzeugt, ohne die Benutzeroberfläche zu berühren.

### Erwartete Ausgabe

| Element | Was Sie sehen werden |
|---------|----------------------|
| Diagrammtyp | Pie chart (oder Donut, wenn `holeSize` > 0) |
| Segment‑Explosion | Erstes Segment um 20 pts verschoben |
| Legende | Rechts positioniert |
| Titel | „Quarterly Sales Distribution“ in fett 14 pt |
| Datenbeschriftungen | Kategoriename und Wert auf jedem Segment angezeigt |
| Dokument | Eine standardmäßige Word `.docx`‑Datei, bereit zum Teilen |

## Häufige Fragen & Stolperfallen

- **Brauche ich eine Lizenz?**  
  Die Evaluierungs‑Version funktioniert für Tests, fügt jedoch ein Wasserzeichen hinzu. Legen Sie Ihre `aspose.words.lic`‑Datei in den Klassenpfad, um eine saubere Ausgabe zu erhalten.

- **Kann ich das mit Maven verwenden?**  
  Absolut. Fügen Sie die folgende Abhängigkeit zu Ihrer `pom.xml` hinzu:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Was, wenn ich mehr als eine Serie habe?**  
  Durchlaufen Sie `pieChart.getSeries()` und wenden Sie `setExplosion`, `setFillColor` oder andere Formatierungen pro Serie an. So **format pie chart** für mehrdimensionale Daten.

- **Ist das Diagramm nach der Erzeugung in Word editierbar?**  
  Ja – nach dem Speichern können Sie das Dokument öffnen und Farben, Schriften manuell anpassen oder das Kreisdiagramm sogar in ein Balkendiagramm umwandeln, falls nötig.

## Fazit

Wir haben soeben **inserted pie chart** in ein Word‑Dokument mit Aspose.Words für Java eingefügt, gezeigt, wie man **generate doughnut chart** erstellt, mehrere Methoden zum **format pie chart** demonstriert, **format chart Word** Best Practices behandelt und gelernt, wie man **customize chart size** für ein professionelles Aussehen anpasst. Das komplette, ausführbare Beispiel oben kann in jedes Java‑Projekt eingefügt werden und liefert sofortige Diagramm‑Automatisierung ohne den Aufwand von COM‑Interop oder Office‑Installationen.

Was kommt als Nächstes? Versuchen Sie, die Datenquelle gegen eine Live‑Datenbank auszutauschen, bedingte Farben basierend auf Schwellenwerten hinzuzufügen oder dasselbe Dokument als PDF für einen druckfertigen Bericht zu exportieren. Jeder dieser Schritte baut auf dem von uns geschaffenen Fundament auf, sodass der Übergang reibungslos verläuft.

Wenn Sie auf Probleme stoßen oder Ideen für weitere Verbesserungen haben – vielleicht ein gestapeltes Balkendiagramm oder ein Liniendiagramm – hinterlassen Sie unten einen Kommentar. Viel Spaß beim Diagramm‑Erstellen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, die Ihnen helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein Säulendiagramm mit Aspose.Words für Java erstellt](/words/english/java/document-conversion-and-export/using-charts/)
- [Nummerformatierung von Datenbeschriftungen in einem Diagramm](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Zahlenformat für Achsen in einem Diagramm](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}