---
category: general
date: 2026-11-15
description: Lär dig hur du lägger till ett cirkeldiagram i ett Word‑dokument med
  Aspose.Words för Java. Inkluderar konvertering till donut‑diagram, utspritt segment
  och komplett kodexempel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: sv
lastmod: 2026-11-15
og_description: Lägg till ett cirkeldiagram i ett Word‑dokument med Aspose.Words för
  Java. Den här handledningen visar hur du exploderar ett segment och omvandlar diagrammet
  till ett donutdiagram.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Lägg till ett cirkeldiagram i ett Word‑dokument med Java – steg‑för‑steg‑guide
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
title: Hur man lägger till ett cirkeldiagram i ett Word‑dokument med Java
url: /sv/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till ett cirkeldiagram i ett Word-dokument – komplett Java-guide

Om du behöver **lägga till ett cirkeldiagram i ett Word-dokument** programatiskt, visar den här handledningen exakt hur du gör det med Aspose.Words för Java. Du får se hela arbetsflödet: läsa in en DOCX, skapa ett cirkeldiagram, explodera den första delen och omvandla diagrammet till en donut genom att ange en hålstorlek.

Handledningen täcker också vanliga variationer—såsom att lägga till flera serier, anpassa färger och hantera dokument som redan innehåller diagram—så att du kan anpassa koden till verkliga projekt som automatiserad rapportering eller dynamiska presentationer.

## Förutsättningar

* Java 17 eller senare (koden kompileras även med JDK 11+)
* Maven 3.6+ eller Gradle för beroendehantering
* En Aspose.Words för Java-licens (gratis provversion fungerar för testning)
* Grundläggande förståelse för Java-syntax och Maven-projektstruktur

## Steg 1: Ställ in Maven-projektet och importera Aspose.Words

Skapa ett nytt Maven-projekt (eller lägg till i ett befintligt) och inkludera Aspose.Words‑beroendet:

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

> **Proffstips:** Om du använder Gradle är motsvarande post `implementation 'com.aspose:aspose-words:24.9'`.

Beroendet hämtar klasserna `Document`, `Chart` och `ChartType` som du behöver för att manipulera diagram.

## Steg 2: Ladda mål‑dokumentet

Du kan börja från en befintlig `.docx`‑fil eller skapa ett nytt tomt dokument. Exemplet nedan laddar en mall som heter `input.docx` i mappen `src/main/resources`.

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

Om filen inte finns skapar Aspose.Words automatiskt ett nytt tomt dokument när du anropar `new Document()` utan ett filnamn.

## Steg 3: Skapa ett cirkeldiagram och infoga det i dokumentet

Aspose.Words behandlar ett diagram som en form som kan placeras var som helst ett stycke kan visas. Följande kod skapar ett **cirkeldiagram**, lägger till en enda dataserie och infogar diagrammet efter det första stycket.

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

**Varför detta steg är viktigt:**  
* `ChartType.PIE` talar om för Aspose.Words att rendera ett traditionellt cirkeldiagram.  
* Att lägga till en serie med både kategorietiketter och numeriska värden fyller automatiskt i delarna.  
* Att infoga diagrammet som ett barn till ett `Paragraph` behåller dokumentets flöde intakt.

## Steg 4: Explodera den första delen för att markera den

En *exploderad del* drar uppmärksamhet till en specifik datapunkt. API‑et exponerar `setExplode(boolean)` på ett `ChartSeries`‑objekt. Att sätta den på den första serien (index 0) får den första delen att poppa ut.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Vanlig fråga:** *Vad händer om jag har flera serier?*  
> Du kan rikta in dig på en specifik serie genom dess index, t.ex. `pieChart.getSeries().get(1).setExplode(true)` för den andra serien.

## Steg 5: Omvandla cirkeldiagrammet till en donut genom att ange hålstorlek

Ett donut‑diagram är i princip ett cirkeldiagram med ett ihåligt centrum. Aspose.Words låter dig definiera hålstorleken som en procentandel av diagrammets radie.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

`setHoleSize`‑metoden accepterar värden från **0** (vanligt cirkeldiagram) till **100** (helt tomt). Ett värde runt **30‑40** ger en visuellt balanserad donut.

## Steg 6: Spara och verifiera resultatet

Efter alla ändringar, spara dokumentet. Följande rad skriver filen till mappen `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Förväntat resultat

Öppna `final-pie-doughnut.docx` i Microsoft Word:

* Ett donut‑diagram visas där det första stycket var.
* “Apples”-delen är exploderad (lite separerad från resten).
* Diagrammet visar fyra delar märkta *Apples*, *Bananas*, *Cherries*, *Dates* med de procentsatser du angav.

Om du föredrar PDF‑utdata, ändra `SaveFormat` till `SaveFormat.PDF`.

## Hantera kantfall och variationer

### Lägga till flera serier

Om du behöver flera serier (t.ex. staplad donut), lägg till dem sekventiellt:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Anpassade färger

Du kan tilldela en färg till varje del via `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Arbeta med ett befintligt diagram

Om dokumentet redan innehåller ett diagram och du bara vill ändra det, lokalisera diagramformen:

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

### Licenshantering

Aspose.Words kräver en licens för produktionsanvändning. Placera din `Aspose.Words.lic`‑fil i classpath och ladda den vid applikationens start:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Om du misslyckas med att ange en licens kommer ett vattenstämpel att läggas till i det genererade dokumentet.

## Fullt, körbart exempel

Nedan är den kompletta Java‑klassen som innehåller alla steg som diskuterats. Kopiera den till `src/main/java/com/example/AddPieChart.java` och kör `mvn compile exec:java`.

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

När programmet körs produceras donut‑diagrammet som beskrivits tidigare. Justera `categories`, `values` eller `holeSize` för att passa dina data.

## Slutsats

Du vet nu hur du **lägger till ett cirkeldiagram i ett Word-dokument** med Java och Aspose.Words. Handledningen täckte att ladda ett dokument, skapa ett cirkeldiagram, explodera en del, omvandla diagrammet till en donut samt hantera vanliga variationer såsom flera serier, anpassade färger och befintliga diagram. Med detta fundament kan du bygga automatiserade rapporteringsverktyg, generera dynamiska presentationer eller bädda in rika visualiseringar direkt i Word‑filer.

### Vad du kan utforska härnäst

* **add bar chart to Word document** – liknande steg men använd `ChartType.BAR`.
* **customize chart legends and titles** – använd `pieChart.getTitle().setText("...")` och `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.
* **export the Word document as PDF** – ändra `SaveFormat` till `PDF` för distributionsklara filer.
* **populate chart data from a database** – ersätt de statiska arrayerna med JDBC‑frågeresultat.

Var gärna experimentera med olika diagramtyper, datakällor och stilalternativ. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man exploderar en pajskiva i Java – Aspose.Words diagramhandledning](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Skapa cirkeldiagram med Aspose.Words Java – Full steg‑för‑steg‑guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}