---
category: general
date: 2026-09-18
description: Leer hoe je een Word‑document maakt en een cirkeldiagram invoegt met
  Aspose.Words voor Java. Inclusief het roteren van het cirkeldiagram en de stappen
  om een Word‑bestand te genereren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: nl
lastmod: 2026-09-18
og_description: Maak een Word‑document en voeg een cirkeldiagram in met Java. Volg
  deze gids om het cirkeldiagram te draaien, segmenten te laten exploderen en een
  Word‑bestand te genereren.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Maak een Word‑document met een cirkeldiagram – stap‑voor‑stap Java‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Hoe maak je een Word‑document met een cirkeldiagram in Java
url: /nl/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Word‑document met een cirkeldiagram maken in Java

Als je een **Word‑document** wilt **maken** dat gegevens visualiseert, laat deze gids je zien hoe je dat doet met Aspose.Words for Java. Je leert een cirkeldiagram in te voegen, een segment te laten explodéren, het diagram te roteren en uiteindelijk een **Word‑bestand** te **genereren** dat je kunt openen in Microsoft Word.

Rapporten maken die tekst en diagrammen combineren, vereist geen apart grafisch hulpmiddel. Aan het einde van deze tutorial heb je een compleet, uitvoerbaar programma dat een .docx‑bestand maakt met een volledig geconfigureerd cirkeldiagram.

## Vereisten

- Java 17 of hoger (de code compileert ook met Java 8+)
- Maven of Gradle voor afhankelijkheidsbeheer
- Aspose.Words for Java‑licentie (de gratis proefversie werkt voor dit voorbeeld)
- Basiskennis van Java‑syntaxis

## Stap 1: Het Maven‑project opzetten

Maak een nieuw Maven‑project aan en voeg de Aspose.Words‑dependency toe aan `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Houd het versienummer up‑to‑date; nieuwere releases bevatten verbeteringen en bugfixes voor diagramtypen.

## Stap 2: Een nieuw Word‑document maken

De eerste handeling bij het **programmeren van een Word‑document** is het instantiëren van een `Document`‑object. Dit object vertegenwoordigt het volledige .docx‑bestand in het geheugen.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

De `Document`‑klasse is het startpunt voor alle Word‑verwerkingsfuncties. Er wordt op dit moment nog niets naar schijf geschreven; alles gebeurt in RAM totdat je `save` aanroept.

## Stap 3: Een cirkeldiagram invoegen

Een `DocumentBuilder` laat je inhoud aan het document toevoegen. Met `insertChart` kun je **cirkeldiagrammen** direct invoegen.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` vertelt Aspose.Words een cirkeldiagram te maken. De afmetingen worden opgegeven in points (1 pt ≈ 1/72 in). Na deze aanroep verschijnt het diagram in een nieuwe alinea.

## Stap 4: Het diagram vullen met gegevens

Een cirkeldiagram heeft een reeks waarden nodig. Hier voegen we drie categorieën toe: “Apples”, “Bananas” en “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

De `add`‑methode bouwt de serie op en maakt automatisch legenda‑items aan. Je kunt dit patroon hergebruiken voor elke numerieke dataset.

## Stap 5: Het eerste segment benadrukken

Een segment laten explodéren trekt de aandacht naar een specifieke waarde. Het eerste segment (index 0) explodeert met 20 points.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Door `explode` op de serie in te stellen, wordt alleen het eerste datapunt verschoven; de rest van het diagram blijft ongewijzigd.

## Stap 6: Een cirkeldiagram roteren

Het roteren van het diagram verbetert de visuele balans, vooral wanneer het grootste segment niet bovenaan staat. De methode `setRotationAngle` verwacht een hoek in graden.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Een rotatie van 45° verplaatst de starthoek met de klok mee, waardoor het diagram in veel lay‑outs beter leesbaar wordt.

## Stap 7: Het document opslaan en een Word‑bestand genereren

Schrijf tenslotte het document naar schijf. Deze stap **genereert een Word‑bestand** dat geopend kan worden met Microsoft Word, LibreOffice of een andere compatibele viewer.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

De `save`‑methode detecteert automatisch de .docx‑extensie en schrijft een Word‑compatibel pakket. De map `output` moet bestaan, of je kunt deze programmatisch aanmaken.

### Verwachte output

Na het uitvoeren van het programma, open `output/PieChart.docx`. Je zou moeten zien:

- Eén pagina met een cirkeldiagram van 400 × 300 pt.
- Het “Apples”‑segment explodeert 20 pt naar buiten.
- Het volledige diagram is 45° met de klok mee geroteerd.
- Een legenda die overeenkomt met de drie fruitcategorieën.

## Veelvoorkomende variaties en randgevallen

### Meerdere diagrammen invoegen

Als je meer dan één diagram nodig hebt, roep je `builder.insertChart` opnieuw aan nadat je de cursor hebt verplaatst:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Diagramkleuren wijzigen

Je kunt de kleuren van de segmenten aanpassen via de `getPoints()`‑collectie van de serie:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Grote datasets verwerken

Voor datasets met meer dan 10 segmenten kun je overwegen een donut‑diagram (`ChartType.DOUGHNUT`) te gebruiken om de visualisatie overzichtelijk te houden.

## Conclusie

Je weet nu hoe je **een Word‑document maakt**, **een cirkeldiagram invoegt**, **een cirkeldiagram roteert** en **een Word‑bestand genereert** met Aspose.Words for Java. De volledige oplossing toont de volledige workflow van documentinitialisatie tot het uiteindelijke bestand, en behandelt zowel het *hoe* als het *waarom* van elke stap.

Ga vervolgens verder met gerelateerde onderwerpen zoals **hoe je cirkeldiagramgegevens uit een database haalt**, het toevoegen van gegevenslabels, of het exporteren van het diagram als afbeelding. Experimenteer met verschillende diagramtypen (balk, lijn, donut) om je Word‑automatiseringstoolkit uit te breiden.


## Wat moet je hierna leren?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}