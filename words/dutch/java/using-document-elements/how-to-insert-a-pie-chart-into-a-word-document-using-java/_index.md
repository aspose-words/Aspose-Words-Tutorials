---
category: general
date: 2026-09-27
description: Leer hoe je met Java een cirkeldiagram in een Word‑document kunt invoegen,
  een cirkeldiagram in Word maakt en percentages op het cirkeldiagram weergeeft voor
  duidelijk inzicht in de gegevens.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: nl
lastmod: 2026-09-27
og_description: Hoe een cirkeldiagram in een Word‑document in te voegen met Java.
  Deze gids laat zien hoe je een cirkeldiagram in Word maakt, percentages op het cirkeldiagram
  weergeeft en leidende lijnen toevoegt.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Hoe een cirkeldiagram in een Word‑document invoegen met Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Hoe een cirkeldiagram in een Word‑document invoegen met Java
url: /nl/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een pie chart in een Word‑document in te voegen met Java

Als je **how to insert pie chart** in een Word‑bestand nodig hebt, leidt deze gids je door het volledige proces. Je ziet hoe je **create pie chart in Word** maakt, percentages op elke partitie weergeeft en leader lines toevoegt voor een gepolijste uitstraling.

Word‑automatisering voelt vaak zwaar aan, maar met Aspose.Words for Java kun je volledig opgemaakte documenten programmatically genereren. Aan het einde van deze tutorial heb je een uitvoerbare Java‑snippet die een Word‑document produceert met een gestylede pie chart.

## Prerequisites

Voordat je begint, zorg dat je het volgende hebt:

- Java 17 of hoger geïnstalleerd
- Maven of Gradle om afhankelijkheden te beheren
- Aspose.Words for Java (versie 23.11 of nieuwer) toegevoegd aan je project
- Basiskennis van Java‑syntaxis

Je hebt geen eerdere ervaring met chart‑API’s nodig; de onderstaande stappen behandelen alles van projectsetup tot het uiteindelijke resultaat.

## Step 1: Set up the Maven dependency

Voeg de Aspose.Words‑bibliotheek toe aan je `pom.xml`. Deze enkele afhankelijkheid geeft je toegang tot `Document`, `DocumentBuilder` en chart‑klassen.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Als je Gradle gebruikt, is het equivalent:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** Gebruik de nieuwste stabiele versie om te profiteren van bug‑fixes en nieuwe chart‑functionaliteiten.

## Step 2: Create a new document and a builder

Het `Document`‑object vertegenwoordigt het Word‑bestand, terwijl `DocumentBuilder` je in staat stelt inhoud in te voegen. Dit vormt de basis voor **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

De builder is nu klaar om objecten overal in het document te plaatsen.

## Step 3: Insert a pie chart

Aspose.Words ondersteunt verschillende chart‑types; we kiezen `ChartType.PIE`. De grootte wordt uitgedrukt in points (1 point = 1/72 inch).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

Op dit moment bevat de chart een standaard dataserie met placeholder‑waarden. Je kunt die waarden later vervangen indien nodig.

## Step 4: Access the chart series

Een pie chart heeft één serie die de slice‑waarden bevat. Haal deze op om opmaak toe te passen.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Step 5: Explode the first slice

Het exploderen van een slice trekt de aandacht naar een specifiek datapunt. Dit is een veelgebruikte visuele aanwijzing wanneer je een belangrijke metric wilt benadrukken.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Step 6: Show percentages on each slice

Percentages direct op de chart weergeven verbetert het inzicht in de data. Dit voldoet aan de **show percentages on pie chart**‑vereiste.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Step 7: Add leader lines for clearer labels

Leader lines verbinden slice‑labels met hun overeenkomstige secties, waardoor onduidelijkheid wordt weggenomen. Dit vervult **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Step 8: Save the document

Schrijf tenslotte het document naar schijf. Je kunt elke map kiezen waar je schrijfrechten voor hebt.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Het uitvoeren van het programma maakt `output/PieFormatted.docx`. Open het bestand in Microsoft Word en je ziet een pie chart waarbij:

- De eerste slice is geëxplodeerd.
- Elke slice toont zijn percentage‑waarde.
- Leader lines wijzen van de percentages naar de bijbehorende slices.

### Expected output

![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image alt="Geformatteerde pie chart ingevoegd in een Word‑document"}

De screenshot (alt‑tekst gebruikt het primaire zoekwoord) illustreert het uiteindelijke uiterlijk: een nette, data‑gedreven pie chart klaar voor rapporten, voorstellen of dashboards.

## Common variations and edge cases

### Changing slice values

Als je aangepaste data nodig hebt, vervang dan de standaard series‑waarden:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Multiple series (donut chart)

Hoewel een eenvoudige pie chart één serie heeft, ondersteunt Aspose.Words ook donut charts met meerdere series. Vervang `ChartType.PIE` door `ChartType.DONUT` en herhaal de series‑configuratiestappen.

### Exporting to PDF

Als je downstream‑workflow PDF vereist, roep dan `doc.save("output/PieFormatted.pdf");` aan nadat de chart is opgebouwd. De visuele lay-out blijft identiek.

## Full source listing

Hieronder staat het volledige, zelfstandige Java‑bestand dat je kunt copy‑pasten in je IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Compileer en voer het programma uit met `mvn compile exec:java -Dexec.mainClass=PieChartExample` (of het equivalente Gradle‑commando). Het gegenereerde Word‑bestand zal de volledig opgemaakte pie chart bevatten.

## Conclusion

Je weet nu **how to insert pie chart** in een Word‑document met Java, hoe je **create pie chart in Word** maakt, hoe je **show percentages on pie chart** toont, en hoe je **add chart to word document** met leader lines toevoegt. Het volledige voorbeeld demonstreert elke stap, legt uit waarom de code op die manier is geschreven, en biedt tips voor aanpassing.

Vervolgens kun je verkennen:

- Data‑labels met aangepaste lettertypen toevoegen (**show percentages on pie chart**‑variaties)
- Meerdere charts combineren in één document (**add chart to word document**‑use case)
- Rapportgeneratie automatiseren met tabellen en charts samen

Voel je vrij om te experimenteren met kleuren, slice‑volgorde of exporteren naar PDF. Veel plezier met coderen!


## What Should You Learn Next?


De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}