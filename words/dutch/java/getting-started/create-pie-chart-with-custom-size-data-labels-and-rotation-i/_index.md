---
category: general
date: 2026-11-22
description: Maak een taartdiagram in Java en leer hoe je de grafiekgrootte instelt,
  gegevenslabels toevoegt, percentages weergeeft en de eerste sector roteert voor
  een duidelijk visueel effect.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: nl
lastmod: 2026-11-22
og_description: Maak een taartdiagram in Java, stel vervolgens de grootte van de grafiek
  in, toon percentages op de gegevenslabels en roteer het eerste segment—alles in
  één uitvoerbaar voorbeeld.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Maak een cirkeldiagram met aangepaste grootte, labels en rotatie in Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Maak een taartdiagram met aangepaste grootte, gegevenslabels en rotatie in
  Java
url: /nl/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een pie chart met aangepaste grootte, data‑labels en rotatie in Java

Als je een **pie chart** in Java moet **maken**, leidt deze gids je door het volledige proces. Je leert hoe je **chart size** instelt, **show percentages pie chart** inschakelt, **data labels pie chart** toevoegt, en **rotate pie chart slice** zodat de eerste slice begint onder een hoek van 45 graden.

Het voorbeeld maakt gebruik van **Aspose.Slides for Java**, een veelgebruikte bibliotheek voor het manipuleren van PowerPoint‑bestanden. Dezelfde concepten gelden voor andere chart‑bibliotheken; vervang gewoon de API‑aanroepen door de equivalenten in jouw toolkit.

## Vereisten

* Java 17 of later geïnstalleerd  
* Maven 3.8+ (of Gradle) voor afhankelijkheidsbeheer  
* Een basisbegrip van Java‑syntaxis  
* Toegang tot de Aspose.Slides for Java‑binary (je kunt een gratis proefversie verkrijgen op de officiële site)

Voeg de afhankelijkheid toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Maak een pie chart – volledig voorbeeld

Het volgende programma maakt een PowerPoint‑slide die een pie chart bevat met een aangepaste grootte, percentage‑gegevenslabels en een geroteerde eerste slice.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Waarom elke stap belangrijk is

| Stap | Doel | Hoe het zich verhoudt tot de trefwoorden |
|------|------|------------------------------------------|
| **Insert chart** | **Create pie chart** – het kernobject dat de visualisatie rendert. | Voldoet direct aan de *create pie chart* vereiste. |
| **Set dimensions** | De `addChart(..., 400, 300)`‑aanroep toont **set chart size**. | Regelt de breedte (400 px) en hoogte (300 px). |
| **Show percentages** | `setShowPercentage(true)` zorgt ervoor dat de chart **show percentages pie chart** op elke slice toont. | Gebruikers hebben vaak percentages nodig in plaats van ruwe waarden. |
| **Add data labels** | De `DataLabelFormat`‑configuratie voegt **data labels pie chart** toe met de gewenste zichtbaarheid. | Labels verbeteren de leesbaarheid en zijn aanpasbaar. |
| **Rotate slice** | `setFirstSliceAngle(45)` roteert de chart zodat de eerste slice begint onder een hoek van 45 graden, wat **rotate pie chart slice** vervult. | Verbetert de visuele nadruk voor een specifieke slice. |

## Stapsgewijze uiteenzetting

### 1. Voeg een pie chart toe en stel de chart size in

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*De `addChart`‑methode maakt de chart aan en stelt tegelijkertijd **set chart size** in op 400 × 300 punten.*  
Als je een andere grootte nodig hebt, pas dan de laatste twee argumenten aan.

### 2. Vul de chart met gegevens

De demo voegt drie categorieën en één serie toe. Vervang de hard‑gecodeerde getallen door gegevens uit een database, CSV‑bestand of gebruikersinvoer indien nodig.

### 3. Show percentages on each slice

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Het inschakelen van `setShowPercentage(true)` zorgt ervoor dat de chart **show percentages pie chart** automatisch het aandeel van elke slice van het totaal berekent.*

### 4. Add detailed data labels

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Je kunt andere labelopties (`setShowValue`, `setShowSeriesName`, etc.) in- of uitschakelen om de **add data labels pie chart** ervaring aan te passen.

### 5. Rotate the first slice

```java
chart.setFirstSliceAngle(45);
```

*Het aanroepen van `setFirstSliceAngle(45)` **rotate pie chart slice** zodat het eerste segment begint onder een hoek van 45 graden, waardoor het opvalt.*

### 6. Save and view the result

Het uitvoeren van het programma genereert `output/PieChartDemo.pptx`. Open dit in PowerPoint of een andere compatibele viewer om de uiteindelijke pie chart te zien:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Schermafbeelding van een gemaakte pie chart met aangepaste grootte, percentage‑labels en een geroteerde eerste slice"}

De afbeelding hierboven toont het resultaat van de **create pie chart**, wat bevestigt dat de grootte, labels, percentages en rotatie correct zijn toegepast.

## Veelvoorkomende variaties en randgevallen

| Situatie | Aanpassing |
|----------|------------|
| **Andere chart‑dimensies** | Wijzig de breedte/hoogte‑parameters in `addChart`. |
| **Meerdere series** | Voeg extra `IChartSeries`‑objecten toe; elke serie kan eigen labelinstellingen hebben. |
| **Aangepast labelformaat** | Gebruik `series.getDataLabelFormat().setNumberFormat("0.0%")` om het aantal decimalen te regelen. |
| **Roteren naar een andere hoek** | Geef een geheel getal (0‑360) door aan `setFirstSliceAngle`. |
| **Exporteren als afbeelding** | Na het opslaan, roep `chart.writeAsSvg(outPath)` of `chart.writeAsPng(outPath)` aan voor een rasterversie. |

> **Pro tip:** Als je van plan bent om veel charts in een lus te genereren, hergebruik dan hetzelfde `Presentation`‑object en vervang alleen de chart‑gegevens. Dit vermindert het geheugenverbruik en versnelt de verwerking.

## Conclusie

Je weet nu hoe je een **pie chart** in Java kunt **maken**, **chart size** kunt **instellen**, **show percentages pie chart** kunt inschakelen, **add data labels pie chart** kunt toevoegen, en **rotate pie chart slice** kunt uitvoeren voor een betere visuele nadruk. Het volledige, uitvoerbare voorbeeld laat elke stap zien, van initialisatie tot het opslaan van het uiteindelijke PowerPoint‑bestand.

### Wat is het volgende?

* Verken andere chart‑typen (Bar, Line, Area) met dezelfde `ChartType`‑enum.  
* Combineer meerdere charts op één slide voor dashboards.  
* Exporteer charts naar PNG of SVG voor gebruik in webapplicaties.  

Voel je vrij om te experimenteren met kleuren, legenda's en animatie‑effecten—je datavisualisaties worden alleen beperkt door je verbeelding. Veel plezier met charting!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [hoe een pie chart in Word in te voegen – add data label percent](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Hoe een pie slice te exploderen in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Pie Chart invoegen in Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}