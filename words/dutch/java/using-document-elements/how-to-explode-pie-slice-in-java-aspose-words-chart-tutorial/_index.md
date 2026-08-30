---
category: general
date: 2026-08-07
description: Hoe een taartsegment te laten exploderen in Java met Aspose.Words. Leer
  hoe je leiderslijnen aan de taart toevoegt, een Word-diagram maakt en taartsegmenten
  aanpast.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: nl
lastmod: 2026-08-07
og_description: Hoe een taartpunt te laten exploderen in Java met Aspose.Words. Deze
  gids laat zien hoe je leidende lijnen aan een taart toevoegt, Word-diagrammen maakt
  en taartdiagramsegmenten aanpast voor een duidelijke visuele impact.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Hoe een taartpunt te exploderen in Java – Aspose.Words-gids
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Hoe een taartpunt te exploderen in Java – Aspose.Words grafiektutorial
url: /nl/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een pie slice te exploderen in Java – Aspose.Words grafiektutorial

Als je wilt weten **how to explode pie slice** in een Word‑document met Java, dan dekt deze tutorial je behoeften. We laten je ook zien **how to add leader lines to pie** diagrammen, **java create word chart** objecten, en **customize pie chart slices** voor een gepolijst resultaat. Aan het einde van deze gids heb je een compleet, uitvoerbaar voorbeeld dat je in elk Java‑project kunt gebruiken.

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## Vereisten

* Java Development Kit (JDK) 8 of hoger.
* Maven of Gradle voor afhankelijkheidsbeheer.
* Een Aspose.Words for Java‑licentie (de gratis evaluatie werkt voor leerdoeleinden).
* Basiskennis van Java‑syntaxis en object‑georiënteerde concepten.

> **Pro tip:** Hoewel Aspose.Words een gratis proefversie aanbiedt, verwijdert het aanschaffen van een licentie het evaluatiewatermerk van gegenereerde documenten.

## Wat deze tutorial behandelt

* Een nieuw Word‑document vanaf nul maken.  
* Een **pie chart** invoegen met behulp van de `DocumentBuilder`.  
* **Exploding a pie slice** om een datapunten te benadrukken.  
* **Adding leader lines to pie** voor duidelijkere labeling.  
* Het uiterlijk van de taartpunten aanpassen, zoals kleuren en randen.  
* Het document opslaan op schijf en het resultaat verifiëren.

---

## Hoe een pie slice te exploderen met Aspose.Words in Java

De eerste stap is het instellen van het diagramobject en het exploderen van de gewenste slice. Aspose.Words maakt het diagram beschikbaar via de `Shape`‑klasse, en elke slice is een `ChartPoint`. Door de `Explosion`‑eigenschap in te stellen, bepaal je hoe ver de slice naar buiten wordt verplaatst.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Waarom het werkt:**  
`setExplosion(20)` vertelt de diagramengine om de slice 20 punten van het middelpunt van het diagram te verschuiven. De waarde is relatief; grotere getallen geven een dramatischer effect. Je kunt elke slice exploderen door de index te wijzigen (`get(1)`, `get(2)`, …).

## Leidende lijnen toevoegen aan pie voor duidelijkere labels

Leidende lijnen verbinden het label van een slice met de rand, wat vooral nuttig is wanneer slices zijn geëxplodeerd of wanneer het diagram veel kleine secties bevat. De aanroep `setLeaderLines(true)` schakelt deze functie in voor de hele serie.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Waarom je leidende lijnen nodig hebt:**  
Wanneer een slice is geëxplodeerd, kan het standaardlabel overlappen met andere elementen. Leidende lijnen houden het label leesbaar door een korte lijn van de slice naar het tekstvak te tekenen.

## Java create Word chart – gegevensreeks invoegen

Een diagram zonder gegevens is niet erg nuttig. Je moet de reeks vullen met categorieën en waarden. Hieronder voegen we drie categorieën toe die marktaandeel vertegenwoordigen.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Uitleg:**  
`ChartSeries` bevat zowel de categorieën (de slice‑namen) als de numerieke waarden. Het inschakelen van `ShowCategoryName` en `ShowPercentage` maakt het diagram zelfverklarend, wat goed samengaat met de eerder toegevoegde leidende lijnen.

## Pie chart slices aanpassen naast explosie

Naast het exploderen van een slice wil je vaak kleuren, randen aanpassen of zelfs een slice volledig verbergen. Het volgende fragment toont drie veelvoorkomende aanpassingen:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Waarom slices aanpassen:**  
Aangepaste kleuren laten het diagram aansluiten bij de huisstijl, terwijl randen de leesbaarheid op afgedrukte pagina's verbeteren. Een slice verbergen is handig wanneer je het datamodel intact wilt houden maar tijdelijk een categorie uit de visuele output wilt weglaten.

## Het document opslaan en het resultaat verifiëren

Tot slot schrijf je het document naar schijf. Je kunt de gegenereerde `.docx` openen in Microsoft Word, LibreOffice of een andere viewer die het formaat ondersteunt.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Verwachte output:**  
Wanneer je `PieChartDemo.docx` opent, zie je een pie chart waarbij de eerste slice (Product A) naar buiten is geëxplodeerd, leidende lijnen van elke slice naar het label wijzen, en de slices verschijnen in de aangepaste groene, blauwe en oranje kleuren. De verborgen slice (Product C) zal niet zichtbaar zijn, maar de percentages blijven optellen tot 100 % omdat de gegevens in de reeks van het diagram blijven.

---

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren, plakken en uitvoeren nadat je de Aspose.Words‑afhankelijkheid aan je project hebt toegevoegd.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Afhankelijkheid (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een kolomdiagram te maken met Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hoe Word‑documenten te laden met Aspose.Words Java: uitgebreide gids](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Hoe formulier‑velden te maken en inhoud toe te voegen met DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}