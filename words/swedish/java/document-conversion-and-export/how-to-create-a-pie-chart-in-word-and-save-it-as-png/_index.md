---
category: general
date: 2026-10-07
description: Lär dig hur du skapar ett cirkeldiagram i Word, lägger till dataserier
  och sparar diagrammet som PNG med Java. Följ den steg‑för‑steg‑guiden för snabba
  resultat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: sv
lastmod: 2026-10-07
og_description: 'Skapa ett cirkeldiagram i Word snabbt: den här handledningen visar
  hur du lägger till dataserier, genererar diagrammet och sparar Word‑diagrammet som
  en bild (PNG). Följ det kompletta kodexemplet.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Skapa ett cirkeldiagram i Word och exportera som PNG – guide
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Hur man skapar ett cirkeldiagram i Word och sparar det som PNG
url: /sv/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create a pie chart in Word and save it as PNG

Om du behöver **create pie chart** objekt i en Microsoft Word‑fil, visar den här guiden exakt hur du gör det med Java. Du kommer också att lära dig hur du **add data series** till diagrammet och **save chart as PNG** så att visualiseringen kan återanvändas utanför Word.

Att generera ett diagram direkt i ett dokument sparar dig från att exportera data till ett separat grafikverktyg. I slutet av den här handledningen kommer du att ha en fullt funktionell Word‑fil som innehåller ett cirkeldiagram och en matchande PNG‑bild på disken.

## Prerequisites

Innan du börjar, se till att du har:

* Java 17 eller senare installerat.
* The **GroupDocs.Viewer for Java** (eller ett kompatibelt bibliotek som tillhandahåller klasserna `Document`, `Chart`, `ChartType` och `ImageSaveOptions`).
* Ett Maven‑ eller Gradle‑projekt där du kan lägga till bibliotekets beroende.
* Ett inmatnings‑Word‑dokument (`input.docx`) som ligger i en mapp du kan referera till från koden.

Om du använder Maven, lägg till beroendet (ersätt `VERSION` med den senaste releasen):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## How to create pie chart in Word

Kärnan i lösningen kretsar kring tre åtgärder:

1. Läs in källfilen `.docx`.
2. **Add data series** till ett nytt `Chart`‑objekt av typen `PIE`.
3. **Save chart as PNG** så att du får en bildfil bredvid Word‑dokumentet.

Nedan förklaras varje steg i detalj, följt av den exakta Java‑koden du behöver.

### Step 1: Load the source document

Du måste öppna Word‑filen som ska innehålla diagrammet. Klassen `Document` läser `.docx`‑innehållet till minnet.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this matters*: Att läsa in dokumentet skapar en muterbar modell. Alla efterföljande diagramoperationer modifierar denna representation i minnet, som du senare sparar tillbaka till disk.

### Step 2: Add data series to the chart

Att skapa ett **pie chart** börjar med en `Chart`‑instans. Konstruktorn tar emot det överordnade `Document` och diagramtypen (`ChartType.PIE`). När diagramobjektet finns, fyller du det med numeriska värden och valfria etiketter.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Why this matters*: Metoden `add` **adds data series** till diagrammet. Varje post i `values` blir en del av cirkeln, medan `categories` ger legendetiketterna. Du kan ange ett godtyckligt antal punkter; biblioteket beräknar automatiskt delarnas vinklar.

### Step 3: Save chart as PNG

När diagrammet är en del av dokumentet kan du exportera den visuella representationen. Metoden `save` på det underliggande diagramobjektet skriver en PNG‑fil till filsystemet.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Why this matters*: Att spara diagrammet som PNG ger dig en rasterbild som kan bäddas in i webbsidor, e‑post eller rapporter utan att kräva den ursprungliga Word‑filen. Objektet `ImageSaveOptions` låter dig styra format, upplösning och andra exportinställningar.

## Generate pie chart in Word – customizing the look

Utöver de grundläggande stegen kan du vilja anpassa färger, titlar eller datalabels. De flesta bibliotek exponerar ett `ChartOptions`‑objekt eller liknande. Här är ett snabbt exempel som lägger till en titel och ändrar delarnas färger:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Dessa anpassningar är valfria men visar hur du kan **generate pie chart in Word** som matchar ditt varumärke.

## Save Word chart as image – alternative approaches

Om du bara behöver bilden och inte diagrammet i dokumentet, kan du hoppa över att infoga diagramformen i Word‑filen och direkt anropa `save`‑metoden efter att ha skapat diagrammet. Koden förblir densamma; du utelämnar helt enkelt de steg som lägger till diagrammet i dokumentets kropp.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Denna teknik är användbar när du genererar många diagram i ett batch‑process och bara bryr dig om PNG‑utdata.

## Full runnable example

Kopiera följande klass till ditt projekt, justera filsökvägarna och kör den. Programmet kommer:

1. Läsa in `input.docx`.
2. **Create a pie chart**, **add data series**, och bädda in det i dokumentet.
3. **Save the chart as PNG** (`radial.png`).
4. Spara den modifierade Word‑filen som `output.docx`.



## What Should You Learn Next?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Skapa Word spridningsdiagram med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Infoga stapeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}