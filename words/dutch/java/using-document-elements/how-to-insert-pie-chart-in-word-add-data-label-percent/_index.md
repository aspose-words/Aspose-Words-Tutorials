---
category: general
date: 2026-07-20
description: Hoe een cirkeldiagram in Word in te voegen met Aspose.Words. Leer hoe
  je een gegevenslabelpercentage kunt toevoegen en percentages op het diagram kunt
  weergeven voor professionele documenten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: nl
lastmod: 2026-07-20
og_description: hoe je een cirkeldiagram in Word invoegt met Aspose.Words. Deze gids
  laat zien hoe je het percentage van gegevenslabels toevoegt en percentages op het
  diagram weergeeft in slechts een paar regels.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: hoe een cirkeldiagram in Word in te voegen – snelle gids
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
title: hoe een taartdiagram in Word invoegen – gegevenslabel procent toevoegen
url: /nl/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hoe een cirkeldiagram in Word in te voegen – data label procent toevoegen

Ever wondered **how to insert pie chart** into a Word document without wrestling with the UI? You’re not alone. In many reporting scenarios you need to *add pie chart to Word* and, more importantly, **show percent on pie chart** so readers instantly grasp the data distribution.

In this tutorial we’ll walk through the complete process using Aspose.Words for Java. By the end you’ll know exactly how to **add data label percent**, **display percentages on chart**, and get a polished pie chart that looks right the first time. No extra plugins, no manual tweaks—just clean code you can drop into any project.

---

## Vereisten

- Java 17 (of later) – de huidige LTS‑versie die Aspose.Words ondersteunt.
- Aspose.Words for Java 24.x (de nieuwste op het moment van schrijven, juli 2026).
- Een basis Maven‑ of Gradle‑setup om de bibliotheek te halen.
- Een IDE naar keuze (IntelliJ IDEA, Eclipse, VS Code… alles is geschikt).

Als je deze al hebt, prima—laten we beginnen.

---

## Stap 1: Het project opzetten en de bibliotheek importeren

First, add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). This gives you access to the `Document`, `DocumentBuilder`, and chart classes.

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

> **Pro tip:** Houd het versienummer up‑to‑date; nieuwere releases voegen vaak chart‑gerelateerde fixes toe die **display percentages on chart** betrouwbaarder maken.

---

## Stap 2: Maak een nieuw Word‑document en een builder

The builder is your Swiss‑army knife for inserting content. Here we create a fresh document and attach a `DocumentBuilder` to it.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Why do we need a builder? It abstracts the low‑level OpenXML structures, letting us focus on *what* we want—like **add pie chart to word**—instead of *how* the XML looks.

---

## Stap 3: Voeg het cirkeldiagram in

Now comes the core of **how to insert pie chart**. We ask the builder to place a pie chart of a specific size. The dimensions are in points (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

At this point the chart is empty, but the placeholder is already in the document. You’ve just **add pie chart to word** programmatically.

---

## Stap 4: Vul het diagram met gegevens

A pie chart needs at least one series of values. Let’s feed it some sample data that represents market share.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

If you ever need multiple series (stacked pies, doughnuts, etc.) you can call `pieChart.getSeries().add()` and repeat the steps. The same logic applies when you want to **display percentages on chart** for each slice.

---

## Stap 5: **add data label percent** – toon de percentages op de segmenten

This is the part most developers forget: configuring the data labels to show percentages. Without it, the chart only shows raw numbers, which can be ambiguous.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

The `setShowPercent(true)` call tells Aspose.Words to render the label as “30 %”, “45 %”, etc. That’s exactly how you **show percent on pie chart** without any extra formatting work.

---

## Stap 6: Sla het document op

Finally, write the document to disk. You can choose `.docx`, `.pdf`, or even `.html`. For this guide we’ll stick with the modern `.docx` format.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Run the program, open `PieChartDemo.docx`, and you’ll see a neatly rendered pie chart with percentage labels on each slice.

---

## Verwachte output

Below is a screenshot of the generated Word file. Notice how each slice displays its share as a percentage—exactly what we wanted when we set **add data label percent**.

![Screenshot van een Word‑document met een cirkeldiagram met percentage‑labels](/images/pie-chart-percent.png){.center width=600px alt="Screenshot die laat zien hoe je een cirkeldiagram in Word invoegt met percentage‑labels"}

*De alt‑tekst bevat het primaire zoekwoord, wat zowel SEO als toegankelijkheid bevredigt.*

---

## Veelgestelde vragen & edge‑case handling

| Question | Answer |
|----------|--------|
| **Kan ik het lettertype van de percentage‑labels wijzigen?** | Ja. Na het inschakelen van `setShowPercent(true)`, haal je het `DataLabel`‑object op en pas je de `Font`‑eigenschap aan (`dataLabel.getFont().setSize(10);`). |
| **Wat als ik een doughnut‑diagram in plaats van een cirkel nodig heb?** | Vervang `ChartType.PIE` door `ChartType.DOUGHNUT` in de `insertChart`‑aanroep. Dezelfde **add data label percent**‑logica werkt. |
| **Geven oudere Word‑versies (2007‑2010) de percentages correct weer?** | Aspose.Words schrijft de onderliggende XML op een versie‑agnostische manier, zodat de percentages in elke Word‑versie die diagrammen ondersteunt (2007+) verschijnen. |
| **Hoe voeg ik een titel toe aan het diagram?** | Gebruik `pieChart.getTitle().setText("Market Share");` vóór het opslaan. |
| **Kan ik het diagram invoegen in een specifieke alinea of tabelcel?** | Absoluut. Verplaats de `DocumentBuilder` naar de gewenste locatie (`builder.moveToParagraph(index, true);` of `builder.moveToCell(table, row, column, true);`) vóór het aanroepen van `insertChart`. |

---

## Tips en trucs uit de praktijk

- **Pro tip:** Als je van plan bent om veel diagrammen in een lus te genereren, hergebruik dan één `DocumentBuilder`‑instance; dit vermindert geheugen‑churn.
- **Let op:** Zeer kleine segmenten (< 2 %). Aspose.Words kan het label weglaten om rommel te voorkomen; je kunt het forceren met `dataLabel.setShowLabel(true);`.
- **Prestatienota:** Het renderen van diagrammen is CPU‑intensief. Voor bulk‑rapportgeneratie, overweeg multi‑threading maar zorg ervoor dat elke thread op zijn eigen `Document`‑instance werkt.
- **Versie‑check:** De methode `setShowPercent` werd geïntroduceerd in Aspose.Words 22.8. Als je een oudere versie gebruikt, upgrade dan of bereken handmatig de percentages en stel ze in als aangepaste labels.

---

## Samenvatting

We hebben **how to insert pie chart** in een Word‑document behandeld met Aspose.Words, laten zien hoe je **add data label percent** kunt doen, en de eenvoudigste manier gedemonstreerd om **display percentages on chart** te laten zien. Met slechts een paar regels Java kun je **add pie chart to word** en **show percent on pie chart** uitvoeren, waardoor ruwe getallen omgezet worden in direct leesbare visuals.

---

## Wat is het volgende?

- Experimenteer met andere diagramtypen (`BAR`, `LINE`, `AREA`) en zie hoe dezelfde **add data label percent**‑logica van toepassing is.
- Combineer diagrammen met tabellen voor rijkere rapporten—Aspose.Words maakt het eenvoudig om een diagram naast een datatabel te plaatsen.
- Verken het exporteren van hetzelfde document naar PDF of HTML om te zien hoe de percentages in verschillende formaten worden weergegeven.

Feel free to tweak the dimensions, colors, or data source (e.g., a database query) and watch your Word reports come alive. If you hit a snag, drop a comment below—happy charting!

## Wat moet je hierna leren?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Kolomdiagram invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Vlakdiagram invoegen in Word‑document | Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Bubbeldiagram invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}