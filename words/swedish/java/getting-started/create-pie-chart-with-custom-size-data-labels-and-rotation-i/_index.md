---
category: general
date: 2026-11-22
description: Skapa ett cirkeldiagram i Java och lär dig hur du ställer in diagrammets
  storlek, lägger till datamärkningar, visar procentsatser och roterar den första
  sektorn för tydlig visuell effekt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: sv
lastmod: 2026-11-22
og_description: Skapa ett cirkeldiagram i Java, ställ sedan in diagrammets storlek,
  visa procent på datamärkningarna och rotera den första sektorn – allt i ett enda
  körbart exempel.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Skapa cirkeldiagram med anpassad storlek, etiketter och rotation i Java
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
title: Skapa cirkeldiagram med anpassad storlek, datamärkning och rotation i Java
url: /sv/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa pie chart med anpassad storlek, dataetiketter och rotation i Java

Om du behöver **create pie chart** i Java, guidar den här guiden dig genom hela processen. Du kommer att lära dig hur du **set chart size**, aktiverar **show percentages pie chart**, lägger till **data labels pie chart**, och **rotate pie chart slice** så att den första delen startar vid en 45‑gradig vinkel.

Exemplet använder **Aspose.Slides for Java**, ett allmänt använt bibliotek för att manipulera PowerPoint‑filer. Samma koncept gäller för andra diagrambibliotek; byt bara ut API‑anropen mot motsvarande i ditt verktyg.

## Förutsättningar

* Java 17 eller senare installerat  
* Maven 3.8+ (eller Gradle) för beroendehantering  
* Grundläggande förståelse för Java‑syntax  
* Tillgång till Aspose.Slides for Java‑binären (du kan få en gratis provversion från den officiella webbplatsen)

Add the dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Skapa pie chart – fullständigt exempel

Följande program skapar en PowerPoint‑bild som innehåller ett pie chart med anpassad storlek, procentuella datalabels och en roterad första del.

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

### Varför varje steg är viktigt

| Steg | Syfte | Hur det relaterar till nyckelorden |
|------|-------|------------------------------------|
| **Insert chart** | **Create pie chart** – kärnobjektet som renderar visualiseringen. | Uppfyller direkt *create pie chart*-kravet. |
| **Set dimensions** | `addChart(..., 400, 300)`‑anropet demonstrerar **set chart size**. | Styr bredden (400 px) och höjden (300 px). |
| **Show percentages** | `setShowPercentage(true)` får diagrammet att **show percentages pie chart** på varje del. | Användare behöver ofta procent istället för råa värden. |
| **Add data labels** | `DataLabelFormat`‑konfigurationen lägger till **data labels pie chart** med önskad synlighet. | Etiketter förbättrar läsbarheten och kan anpassas. |
| **Rotate slice** | `setFirstSliceAngle(45)` roterar diagrammet så att den första delen startar vid en 45‑gradig vinkel, vilket uppfyller **rotate pie chart slice**. | Förbättrar visuell betoning för en specifik del. |

## Steg‑för‑steg genomgång

### 1. Infoga ett pie chart och **set chart size**

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*`addChart`‑metoden skapar diagrammet och samtidigt **set chart size** till 400 × 300 punkter.*  
Om du behöver en annan storlek, justera de två sista argumenten.

### 2. Fyll diagrammet med data

Demo‑exemplet lägger till tre kategorier och en enda serie. Ersätt de hårdkodade siffrorna med data från en databas, CSV‑fil eller användarinmatning efter behov.

### 3. Show percentages on each slice

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Att aktivera `setShowPercentage(true)` säkerställer att diagrammet **show percentages pie chart** automatiskt beräknar varje delens andel av totalen.*

### 4. Add detailed data labels

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Du kan växla andra etikettalternativ (`setShowValue`, `setShowSeriesName`, etc.) för att anpassa **add data labels pie chart**‑upplevelsen.

### 5. Rotate the first slice

```java
chart.setFirstSliceAngle(45);
```

*Att anropa `setFirstSliceAngle(45)` **rotate pie chart slice** så att den första segmentet börjar vid en 45‑gradig vinkel, vilket får den att sticka ut.*

### 6. Spara och visa resultatet

När programmet körs skapas `output/PieChartDemo.pptx`. Öppna den i PowerPoint eller någon kompatibel visare för att se det färdiga pie chart:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Skärmdump av ett skapat pie chart med anpassad storlek, procentuella etiketter och en roterad första del"}

Bilden ovan visar resultatet av **create pie chart**, vilket bekräftar att storlek, etiketter, procent och rotation har tillämpats korrekt.

## Vanliga variationer och kantfall

| Situation | Justering |
|-----------|-----------|
| **Different chart dimensions** | Ändra bredd-/höjd‑parametrarna i `addChart`. |
| **Multiple series** | Lägg till ytterligare `IChartSeries`‑objekt; varje serie kan ha egna etikettinställningar. |
| **Custom label format** | Använd `series.getDataLabelFormat().setNumberFormat("0.0%")` för att styra decimaler. |
| **Rotating to another angle** | Skicka vilket heltal som helst (0‑360) till `setFirstSliceAngle`. |
| **Export as image** | Efter sparning, anropa `chart.writeAsSvg(outPath)` eller `chart.writeAsPng(outPath)` för en rasterversion. |

> **Pro tip:** Om du planerar att generera många diagram i en loop, återanvänd samma `Presentation`‑objekt och ersätt bara diagramdata. Detta minskar minnesanvändning och snabbar upp bearbetningen.

## Slutsats

Du vet nu hur du **create pie chart** i Java, **set chart size**, aktiverar **show percentages pie chart**, **add data labels pie chart**, och **rotate pie chart slice** för bättre visuell betoning. Det kompletta, körbara exemplet visar varje steg från initiering till sparande av den slutgiltiga PowerPoint‑filen.

### Vad blir nästa?

* Utforska andra diagramtyper (Bar, Line, Area) med samma `ChartType`‑enum.  
* Kombinera flera diagram på en enda bild för instrumentpaneler.  
* Exportera diagram till PNG eller SVG för användning i webbapplikationer.  

Känn dig fri att experimentera med färger, legender och animationseffekter—dina datavisualiseringar är bara begränsade av fantasin. Lycka till med diagrammen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [hur man infogar pie chart i Word – lägg till dataetikett procent](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Hur man exploderar pie slice i Java – Aspose.Words diagramhandledning](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Infoga Pie Chart i Java – Explodera, Rotera & Markera Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}