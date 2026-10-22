---
category: general
date: 2026-10-07
description: Leer hoe je een cirkeldiagram maakt in Word, gegevensreeksen toevoegt
  en de grafiek opslaat als PNG met Java. Volg de stapsgewijze handleiding voor snelle
  resultaten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: nl
lastmod: 2026-10-07
og_description: 'Maak snel een cirkeldiagram in Word: deze tutorial laat zien hoe
  je een gegevensreeks toevoegt, het diagram genereert en het Word-diagram opslaat
  als afbeelding (PNG). Volg het volledige codevoorbeeld.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Maak een cirkeldiagram in Word en exporteer als PNG – gids
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
title: Hoe maak je een cirkeldiagram in Word en sla je het op als PNG
url: /nl/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een pie chart in Word en sla je het op als PNG

Als je **create pie chart** objecten moet maken binnen een Microsoft Word‑bestand, laat deze gids je precies zien hoe je dat doet met Java. Je leert ook hoe je **add data series** aan het diagram kunt toevoegen en **save chart as PNG** zodat de visual buiten Word opnieuw kan worden gebruikt.

Een diagram direct in een document genereren bespaart je het exporteren van gegevens naar een afzonderlijk grafisch hulpmiddel. Aan het einde van deze tutorial heb je een volledig functioneel Word‑bestand dat een pie chart bevat en een bijbehorende PNG‑afbeelding op schijf.

## Vereisten

* Java 17 of later geïnstalleerd.
* De **GroupDocs.Viewer for Java** (of een compatibele bibliotheek die de klassen `Document`, `Chart`, `ChartType` en `ImageSaveOptions` levert).
* Een Maven- of Gradle‑project waarin je de bibliotheek‑dependency kunt toevoegen.
* Een invoer‑Word‑document (`input.docx`) dat zich bevindt in een map die je vanuit code kunt refereren.

Als je Maven gebruikt, voeg dan de dependency toe (vervang `VERSION` door de nieuwste release):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Hoe maak je een pie chart in Word

De kern van de oplossing draait om drie acties:

1. Laad het bron‑`.docx`‑bestand.
2. **Add data series** aan een nieuw `Chart`‑object van het type `PIE`.
3. **Save chart as PNG** zodat je een afbeeldingsbestand naast het Word‑document krijgt.

Hieronder wordt elke stap in detail uitgelegd, gevolgd door de exacte Java‑code die je nodig hebt.

### Stap 1: Laad het bron‑document

Je moet het Word‑bestand openen dat het diagram zal bevatten. De `Document`‑klasse leest de `.docx`‑inhoud in het geheugen.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Waarom dit belangrijk is*: Het laden van het document creëert een mutabel model. Alle daaropvolgende diagram‑bewerkingen wijzigen deze in‑memory‑representatie, die je later weer naar schijf schrijft.

### Stap 2: Voeg data series toe aan het diagram

Het maken van een **pie chart** begint met een `Chart`‑instantie. De constructor ontvangt het bovenliggende `Document` en het diagramtype (`ChartType.PIE`). Nadat het diagramobject bestaat, vul je het met numerieke waarden en optionele labels.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Waarom dit belangrijk is*: De `add`‑methode **adds data series** aan het diagram. Elke invoer in `values` wordt een segment van de taart, terwijl `categories` de legende‑labels leveren. Je kunt een willekeurig aantal punten opgeven; de bibliotheek berekent automatisch de segmenthoeken.

### Stap 3: Sla diagram op als PNG

Zodra het diagram deel uitmaakt van het document, kun je de visuele weergave exporteren. De `save`‑methode op het onderliggende diagramobject schrijft een PNG‑bestand naar het bestandssysteem.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Waarom dit belangrijk is*: Het opslaan van het diagram als PNG levert een rasterafbeelding op die kan worden ingebed in webpagina's, e‑mails of rapporten zonder dat het originele Word‑bestand nodig is. Het `ImageSaveOptions`‑object stelt je in staat het formaat, de resolutie en andere exportinstellingen te regelen.

## Pie chart genereren in Word – het uiterlijk aanpassen

Naast de basisstappen wil je misschien kleuren, titels of data‑labels aanpassen. De meeste bibliotheken bieden een `ChartOptions`‑ of soortgelijk object. Hier is een snel voorbeeld dat een titel toevoegt en de segmentkleuren wijzigt:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Deze aanpassingen zijn optioneel, maar laten zien hoe je een **generate pie chart in Word** kunt maken die bij je huisstijl past.

## Word‑diagram opslaan als afbeelding – alternatieve benaderingen

Als je alleen de afbeelding nodig hebt en niet het diagram in het document, kun je het invoegen van de diagramvorm in het Word‑bestand overslaan en direct de `save`‑methode aanroepen na het maken van het diagram. De code blijft hetzelfde; je laat simpelweg de stappen weg die het diagram aan de body van het document toevoegen.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Deze techniek is handig wanneer je veel diagrammen in een batch‑proces genereert en alleen de PNG‑output nodig hebt.

## Volledig uitvoerbaar voorbeeld

Kopieer de volgende klasse naar je project, pas de bestands‑paden aan en voer het uit. Het programma zal:

1. Laad `input.docx`.
2. **Create a pie chart**, **add data series**, en embed het in het document.
3. **Save the chart as PNG** (`radial.png`).
4. Sla het gewijzigde Word‑bestand op als `output.docx`.



## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe maak je een kolomdiagram met Aspose.Words voor Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Maak een Word Scatter Chart met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Voeg een kolomdiagram in Word in met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}