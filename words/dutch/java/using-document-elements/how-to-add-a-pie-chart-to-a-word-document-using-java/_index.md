---
category: general
date: 2026-11-15
description: Leer hoe je een taartdiagram toevoegt aan een Word‑document met Aspose.Words
  for Java. Inclusief omzetting naar een donutdiagram, een uitgeklapte segment en
  een volledig codevoorbeeld.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: nl
lastmod: 2026-11-15
og_description: Voeg een cirkeldiagram toe aan een Word‑document met Aspose.Words
  for Java. Deze tutorial laat zien hoe je een segment kunt laten uitwaaieren en het
  diagram kunt omzetten in een donut.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Voeg een cirkeldiagram toe aan een Word‑document met Java – stapsgewijze
  handleiding
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Hoe voeg je een cirkeldiagram toe aan een Word‑document met Java
url: /nl/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Een taartdiagram toevoegen aan een Word‑document – volledige Java‑gids

Als je **een taartdiagram aan een Word‑document** wilt toevoegen via code, laat deze tutorial je precies zien hoe je dat doet met Aspose.Words for Java. Je ziet de volledige workflow: een DOCX laden, een taartdiagram maken, de eerste partitie laten exploderen en het diagram omzetten naar een donut door een gatgrootte in te stellen.

De gids behandelt ook veelvoorkomende variaties—zoals het toevoegen van meerdere series, het aanpassen van kleuren en het verwerken van documenten die al diagrammen bevatten—zodat je de code kunt aanpassen aan real‑world projecten zoals geautomatiseerde rapportage of dynamische presentaties.

## Vereisten

* Java 17 of later (de code compileert ook met JDK 11+)
* Maven 3.6+ of Gradle voor afhankelijkheidsbeheer
* Een Aspose.Words for Java‑licentie (de gratis proefversie werkt voor testen)
* Een basisbegrip van Java‑syntaxis en Maven‑projectstructuur

## Stap 1: Het Maven‑project opzetten en Aspose.Words importeren

Maak een nieuw Maven‑project (of voeg toe aan een bestaand project) en voeg de Aspose.Words‑dependency toe:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Als je Gradle gebruikt, is de equivalente vermelding `implementation 'com.aspose:aspose-words:24.9'`.

De dependency brengt de `Document`-, `Chart`- en `ChartType`‑klassen mee die je nodig hebt om diagrammen te manipuleren.

## Stap 2: Het doel‑document laden

Je kunt beginnen met een bestaand `.docx`‑bestand of een nieuw leeg document maken. Het voorbeeld hieronder laadt een sjabloon genaamd `input.docx` dat zich bevindt in de map `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Als het bestand niet bestaat, maakt Aspose.Words automatisch een nieuw leeg document aan wanneer je `new Document()` zonder bestandsnaam aanroept.

## Stap 3: Een taartdiagram maken en in het document invoegen

Aspose.Words beschouwt een diagram als een vorm die overal kan worden geplaatst waar een alinea kan staan. De volgende code maakt een **taartdiagram**, voegt een enkele gegevensreeks toe en plaatst het diagram na de eerste alinea.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Why this step matters:**  
* `ChartType.PIE` vertelt Aspose.Words om een traditioneel taartdiagram weer te geven.  
* Het toevoegen van een reeks met zowel categorielabels als numerieke waarden vult de partities automatisch.  
* Het invoegen van het diagram als kind van een `Paragraph` behoudt de stroom van het document.

## Stap 4: De eerste partitie laten exploderen om deze te benadrukken

Een *exploded slice* trekt de aandacht naar een specifiek datapunt. De API biedt `setExplode(boolean)` op een `ChartSeries`‑object. Door dit in te stellen op de eerste reeks (index 0) wordt de eerste partitie eruit gepopt.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Veelgestelde vraag:** *Wat als ik meerdere series heb?*  
> Je kunt een specifieke serie targeten op basis van de index, bijv. `pieChart.getSeries().get(1).setExplode(true)` voor de tweede serie.

## Stap 5: Het taartdiagram omzetten naar een donut door een gatgrootte in te stellen

Een donut‑diagram is in wezen een taartdiagram met een holle kern. Aspose.Words laat je de gatgrootte definiëren als een percentage van de straal van het diagram.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

De `setHoleSize`‑methode accepteert waarden van **0** (normale taart) tot **100** (volledig leeg). Een waarde rond **30‑40** levert een visueel gebalanceerde donut op.

## Stap 6: Het resultaat opslaan en verifiëren

Na alle aanpassingen, sla het document op. De volgende regel schrijft het bestand naar de map `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Verwachte output

Open `final-pie-doughnut.docx` in Microsoft Word:

* Er verschijnt een donut‑diagram waar de eerste alinea stond.
* De “Apples”‑partitie is geëxplodeerd (licht gescheiden van de rest).
* Het diagram toont vier partities gelabeld *Apples*, *Bananas*, *Cherries*, *Dates* met de percentages die je hebt opgegeven.

Als je liever PDF‑output wilt, wijzig dan `SaveFormat` naar `SaveFormat.PDF`.

## Afhandelen van randgevallen en variaties

### Meerdere series toevoegen

Als je meerdere series nodig hebt (bijv. gestapelde donut), voeg ze dan opeenvolgend toe:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Aangepaste kleuren

Je kunt elke partitie een kleur toewijzen via `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Werken met een bestaand diagram

Als het document al een diagram bevat en je wilt alleen dit aanpassen, zoek dan de diagramvorm op:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Licentie‑afhandeling

Aspose.Words vereist een licentie voor productiegebruik. Plaats je `Aspose.Words.lic`‑bestand in het classpath en laad het bij het starten van de applicatie:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Als je geen licentie instelt, wordt er een watermerk aan het gegenereerde document toegevoegd.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat de volledige Java‑klasse die elke besproken stap bevat. Kopieer deze naar `src/main/java/com/example/AddPieChart.java` en voer `mvn compile exec:java` uit.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Het uitvoeren van het programma genereert de eerder beschreven donut‑diagram. Pas `categories`, `values` of `holeSize` aan op jouw gegevens.

## Conclusie

Je weet nu hoe je **een taartdiagram aan een Word‑document** kunt toevoegen met Java en Aspose.Words. De tutorial behandelde het laden van een document, het maken van een taartdiagram, het laten exploderen van een partitie, het omzetten van het diagram naar een donut, en het afhandelen van veelvoorkomende variaties zoals meerdere series, aangepaste kleuren en bestaande diagrammen. Met deze basis kun je geautomatiseerde rapportagetools bouwen, dynamische presentaties genereren of rijke visualisaties direct in Word‑bestanden insluiten.

### Wat je hierna kunt verkennen

* **balkdiagram toevoegen aan Word‑document** – vergelijkbare stappen maar gebruik `ChartType.BAR`.
* **legenda's en titels van diagrammen aanpassen** – gebruik `pieChart.getTitle().setText("...")` en `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.
* **het Word‑document exporteren als PDF** – wijzig `SaveFormat` naar `PDF` voor distributieklaar bestanden.
* **diagramgegevens uit een database vullen** – vervang de statische arrays door JDBC‑queryresultaten.

Voel je vrij om te experimenteren met verschillende diagramtypen, gegevensbronnen en opmaakopties. Veel plezier met coderen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een taartpartitie te exploderen in Java – Aspose.Words diagram tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Taartdiagram maken met Aspose.Words Java – volledige stap‑voor‑stap gids](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}