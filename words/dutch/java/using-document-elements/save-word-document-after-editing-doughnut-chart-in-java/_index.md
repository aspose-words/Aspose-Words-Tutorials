---
category: general
date: 2026-09-11
description: Sla het Word‑document op na het bewerken van een donutgrafiek met Aspose.Words
  voor Java. Leer hoe je de grootte van het donutgat kunt aanpassen, de donutgrafiek
  kunt roteren en de eigenschappen van de donutgrafiek kunt bewerken.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: nl
lastmod: 2026-09-11
og_description: Sla Word-document op na het bewerken van een donutgrafiek met Aspose.Words
  voor Java. Deze tutorial laat zien hoe je de grootte van het donutgat kunt aanpassen,
  de donutgrafiek kunt roteren en het uiterlijk van de grafiek kunt aanpassen.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Word-document opslaan na het bewerken van een donutgrafiek – Java-gids
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Word-document opslaan na het bewerken van een donutgrafiek in Java
url: /nl/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Opslaan Word-document na bewerken van donutgrafiek in Java

Als je een **Word-document** moet opslaan dat een aangepaste donutgrafiek bevat, laat deze gids je precies zien hoe. Met slechts een paar regels Java kun je het donutgat aanpassen, de donutgrafiek roteren en vervolgens het resultaat terug naar schijf schrijven.

Je ziet een volledig, uitvoerbaar voorbeeld dat Aspose.Words for Java gebruikt, plus tips voor het omgaan met meerdere grafieken, het verifiëren van knooppunttypes en het vermijden van veelvoorkomende valkuilen. Er zijn geen externe referenties nodig—alles wat je nodig hebt is inbegrepen.

## Vereisten

- Java 17 of nieuwer geïnstalleerd
- Maven of Gradle om afhankelijkheden te beheren
- Aspose.Words for Java (versie 23.9 of later) toegevoegd aan je project  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Een Word‑bestand (`input.docx`) dat een enkele donutgrafiek bevat

## Stap 1: Laad het Word-document

De eerste stap is het openen van het bronbestand. Deze stap is essentieel omdat elke volgende bewerking werkt op het in‑memory `Document`‑object.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Waarom?** Het laden van het document creëert een DOM‑representatie waarmee je vormen, tabellen en grafieken kunt doorlopen. Als het bestand niet kan worden geopend, gooit Aspose.Words een uitzondering, zodat je meteen weet dat het pad onjuist is.

## Stap 2: Zoek de donutgrafiek‑vorm

Een grafiek wordt opgeslagen binnen een `Shape`‑knooppunt. We halen de eerste vorm op die een grafiek bevat en casten de renderer naar `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Waarom?** Het controleren van `isChart()` voorkomt een `ClassCastException` wanneer het document afbeeldingen of andere vormen vóór de grafiek bevat. Dit maakt de code robuust voor documenten met gemengde inhoud.

## Stap 3: Verander de grootte van het donutgat  

Nu bewerken we het donutgat. De `setHoleSize`‑methode verwacht een percentage van de grafiekradius (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Waarom?** Het wijzigen van het donutgat (`change doughnut hole` / `change chart hole size`) stelt je in staat het centrale gebied te benadrukken of te dempen. Waarden buiten 10‑90 % worden door de API genegeerd.

## Stap 4: Roteer de donutgrafiek  

Om te bepalen waar de eerste partitie start, stel je de hoek van de eerste partitie in. Dit roteert effectief de **donutgrafiek**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Waarom?** Het roteren van de grafiek is nuttig wanneer je wilt dat een bepaalde partitie bovenaan verschijnt of om te voldoen aan een ontwerpspecificatie.

## Stap 5: Sla het bijgewerkte document op  

Tot slot schrijf je de wijzigingen terug naar een nieuw bestand. Dit is het moment waarop je het **Word-document** met de bewerkte grafiek opslaat.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Verwacht resultaat:** `output.docx` bevat de oorspronkelijke inhoud, maar de donutgrafiek heeft nu een gat van 30 % en de eerste partitie begint bij 45 °. Het openen van het bestand in Microsoft Word toont de getransformeerde grafiek.

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in je IDE. Het bevat alle imports en foutafhandeling die nodig zijn om veilig **donutgrafiek te bewerken** en **Word-document op te slaan**.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Verwachte uitvoer

Wanneer je `output.docx` opent:

- Het centrale gat van de donutgrafiek beslaat ongeveer een derde van de grafiekradius.  
- De eerste partitie begint op de 45‑graden positie, waardoor de hele grafiek met de klok mee verschuift.  

Beide visuele wijzigingen worden direct in Word weergegeven.

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe te handelen |
|-----------|----------------|
| **Meerdere grafieken** | Iterate through `doc.getChildNodes(NodeType.SHAPE, true)` and filter `shape.isChart()`; apply `setHoleSize` / `setFirstSliceAngle` to each `Chart`. |
| **Grafiek is geen donut** | Check `chart.getType()`; only call `setHoleSize` when `chart.getType() == ChartType.DOUGHNUT`. |
| **Hole size dynamisch aanpassen nodig** | Compute the desired percentage based on data values, then call `setHoleSize(computedValue)`. |
| **Opslaan naar een stream** | Use

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe maak je een kolomgrafiek met Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hoe sla je een document op als pdf met Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Word opslaan met wachtwoord met Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}