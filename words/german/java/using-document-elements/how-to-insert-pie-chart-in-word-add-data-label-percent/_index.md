---
category: general
date: 2026-07-20
description: Wie man ein Kreisdiagramm in Word mit Aspose.Words einfügt. Lernen Sie,
  Datenbeschriftungsprozente hinzuzufügen und Prozentsätze im Diagramm für professionelle
  Dokumente anzuzeigen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: de
lastmod: 2026-07-20
og_description: Wie man ein Kreisdiagramm in Word mit Aspose.Words einfügt. Diese
  Anleitung zeigt, wie man Prozentwerte für Datenbeschriftungen hinzufügt und Prozentsätze
  im Diagramm mit nur wenigen Zeilen anzeigt.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: Wie man ein Kreisdiagramm in Word einfügt – Kurzleitfaden
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Wie man ein Kreisdiagramm in Word einfügt – Prozentwert als Datenbeschriftung
  hinzufügen
url: /de/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# how to insert pie chart in Word – add data label percent

Haben Sie sich jemals gefragt, **wie man ein Kreisdiagramm** in ein Word‑Dokument einfügt, ohne sich mit der Benutzeroberfläche herumzuschlagen? Sie sind nicht allein. In vielen Reporting‑Szenarien muss man *ein Kreisdiagramm zu Word hinzufügen* und, noch wichtiger, **Prozentwerte im Kreisdiagramm anzeigen**, damit die Leser die Datenverteilung sofort erfassen.

In diesem Tutorial gehen wir den gesamten Prozess mit Aspose.Words für Java durch. Am Ende wissen Sie genau, wie Sie **Datenbeschriftungs‑Prozentwerte hinzufügen**, **Prozentsätze im Diagramm anzeigen** und ein professionelles Kreisdiagramm erhalten, das beim ersten Mal richtig aussieht. Keine zusätzlichen Plugins, keine manuellen Nachbearbeitungen – nur sauberer Code, den Sie in jedes Projekt einbinden können.

---

## Prerequisites

- Java 17 (oder höher) – die aktuelle LTS‑Version, die Aspose.Words unterstützt.
- Aspose.Words für Java 24.x (die neueste zum Zeitpunkt des Schreibens, Juli 2026).
- Eine grundlegende Maven‑ oder Gradle‑Einrichtung, um die Bibliothek zu beziehen.
- Eine IDE Ihrer Wahl (IntelliJ IDEA, Eclipse, VS Code … jede ist geeignet).

Wenn Sie das bereits haben, großartig – lassen Sie uns loslegen.

---

## Step 1: Set up the project and import the library

Fügen Sie zuerst die Aspose.Words‑Abhängigkeit zu Ihrer `pom.xml` (Maven) oder `build.gradle` (Gradle) hinzu. Damit erhalten Sie Zugriff auf die Klassen `Document`, `DocumentBuilder` und die Diagramm‑Klassen.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro‑Tipp:** Halten Sie die Versionsnummer aktuell; neuere Releases enthalten oft Diagramm‑Fixes, die das **display percentages on chart** zuverlässiger machen.

---

## Step 2: Create a new Word document and a builder

Der Builder ist Ihr Schweizer Taschenmesser zum Einfügen von Inhalten. Hier erstellen wir ein frisches Dokument und binden einen `DocumentBuilder` daran.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Warum benötigen wir einen Builder? Er abstrahiert die Low‑Level‑OpenXML‑Strukturen, sodass wir uns auf das *Was* konzentrieren können – wie **add pie chart to word** – statt auf das *Wie* des XML.

---

## Step 3: Insert the pie chart

Jetzt kommt der Kern von **how to insert pie chart**. Wir lassen den Builder ein Kreisdiagramm mit einer bestimmten Größe einfügen. Die Maße sind in Punkten (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

An diesem Punkt ist das Diagramm noch leer, aber der Platzhalter befindet sich bereits im Dokument. Sie haben gerade **add pie chart to word** programmgesteuert eingefügt.

---

## Step 4: Populate the chart with data

Ein Kreisdiagramm benötigt mindestens eine Datenreihe. Wir füttern es mit Beispieldaten, die den Marktanteil darstellen.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Falls Sie mehrere Reihen benötigen (gestapelte Kreisdiagramme, Donuts usw.), können Sie `pieChart.getSeries().add()` aufrufen und die Schritte wiederholen. Die gleiche Logik gilt, wenn Sie **display percentages on chart** für jeden Abschnitt anzeigen wollen.

---

## Step 5: **add data label percent** – show the percentages on the slices

Das ist der Teil, den die meisten Entwickler vergessen: die Datenbeschriftungen so konfigurieren, dass Prozentsätze angezeigt werden. Ohne diese Einstellung zeigt das Diagramm nur Rohzahlen, was mehrdeutig sein kann.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

Der Aufruf `setShowPercent(true)` weist Aspose.Words an, die Beschriftung als „30 %“, „45 %“ usw. zu rendern. Genau so zeigen Sie **show percent on pie chart** ohne zusätzlichen Formatierungsaufwand.

---

## Step 6: Save the document

Zum Schluss schreiben wir das Dokument auf die Festplatte. Sie können `.docx`, `.pdf` oder sogar `.html` wählen. Für diese Anleitung bleiben wir beim modernen `.docx`‑Format.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Führen Sie das Programm aus, öffnen Sie `PieChartDemo.docx` und Sie sehen ein sauber gerendertes Kreisdiagramm mit Prozent‑Beschriftungen auf jedem Abschnitt.

---

## Expected output

Unten sehen Sie einen Screenshot der erzeugten Word‑Datei. Beachten Sie, wie jeder Abschnitt seinen Anteil als Prozentsatz anzeigt – genau das, was wir wollten, als wir **add data label percent** gesetzt haben.

![Screenshot of a Word document containing a pie chart with percentage labels](/images/pie-chart-percent.png){.center width=600px alt="Screenshot, der zeigt, wie man ein Kreisdiagramm in Word mit Prozentbeschriftungen einfügt"}

*Der Alt‑Text enthält das Haupt‑Keyword und erfüllt sowohl SEO‑ als auch Barrierefreiheitsanforderungen.*

---

## Common questions & edge‑case handling

| Question | Answer |
|----------|--------|
| **Can I change the font of the percentage labels?** | Yes. After enabling `setShowPercent(true)`, retrieve the `DataLabel` object and adjust its `Font` property (`dataLabel.getFont().setSize(10);`). |
| **What if I need a doughnut chart instead of a pie?** | Replace `ChartType.PIE` with `ChartType.DOUGHNUT` in the `insertChart` call. The same **add data label percent** logic works. |
| **Do older Word versions (2007‑2010) display the percentages correctly?** | Aspose.Words writes the underlying XML in a version‑agnostic way, so the percentages appear in any Word that supports charts (2007+). |
| **How to add a title to the chart?** | Use `pieChart.getTitle().setText("Market Share");` before saving. |
| **Can I insert the chart into a specific paragraph or table cell?** | Absolutely. Move the `DocumentBuilder` to the desired location (`builder.moveToParagraph(index, true);` or `builder.moveToCell(table, row, column, true);`) before calling `insertChart`. |

---

## Tips and tricks from the field

- **Pro tip:** Wenn Sie viele Diagramme in einer Schleife erzeugen, verwenden Sie eine einzige `DocumentBuilder`‑Instanz; das reduziert den Speicherverbrauch.
- **Watch out for:** Sehr kleine Abschnitte (< 2 %). Aspose.Words kann die Beschriftung weglassen, um Unübersichtlichkeit zu vermeiden; Sie können sie mit `dataLabel.setShowLabel(true);` erzwingen.
- **Performance note:** Das Rendern von Diagrammen ist CPU‑intensiv. Für die massenhafte Berichtserstellung sollten Sie Multithreading in Betracht ziehen, jedoch sicherstellen, dass jeder Thread mit seiner eigenen `Document`‑Instanz arbeitet.
- **Version check:** Die Methode `setShowPercent` wurde in Aspose.Words 22.8 eingeführt. Wenn Sie eine ältere Version nutzen, aktualisieren Sie oder berechnen Sie die Prozentsätze manuell und setzen Sie sie als benutzerdefinierte Beschriftungen.

---

## Recap

Wir haben behandelt, **how to insert pie chart** in ein Word‑Dokument mit Aspose.Words, Ihnen gezeigt, wie Sie **add data label percent** setzen, und die einfachste Methode demonstriert, **display percentages on chart** zu erreichen. Mit nur wenigen Zeilen Java können Sie **add pie chart to word** und **show percent on pie chart** realisieren und rohe Zahlen in sofort lesbare Visualisierungen verwandeln.

---

## What’s next?

- Experimentieren Sie mit anderen Diagrammtypen (`BAR`, `LINE`, `AREA`) und sehen Sie, wie dieselbe **add data label percent**‑Logik angewendet wird.
- Kombinieren Sie Diagramme mit Tabellen für umfangreichere Berichte – Aspose.Words macht es trivial, ein Diagramm neben einer Datentabelle zu platzieren.
- Erkunden Sie den Export desselben Dokuments nach PDF oder HTML, um zu sehen, wie die Prozentsätze in verschiedenen Formaten gerendert werden.

Passen Sie die Abmessungen, Farben oder die Datenquelle (z. B. eine Datenbankabfrage) an und lassen Sie Ihre Word‑Berichte lebendig werden. Wenn Sie auf ein Problem stoßen, hinterlassen Sie einen Kommentar unten – happy charting!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}