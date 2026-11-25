---
category: general
date: 2026-11-25
description: Leer hoe je een taartdiagram in Java maakt, een taartdiagram in een Word‑document
  invoegt, een taartpunt explodeert en de oriëntatie van het diagram wijzigt, met
  duidelijke codevoorbeelden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: nl
lastmod: 2026-11-25
og_description: Maak een taartdiagram in Java, voeg het taartdiagram in een document
  in, explodeer een taartpunt en wijzig de oriëntatie van het diagram met stapsgewijze
  code.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Maak een taartdiagram in Java – voeg een segment toe, explodeer het en roteer
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Hoe maak je een cirkeldiagram, voeg je het in en pas je de oriëntatie aan in
  Java
url: /nl/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een cirkeldiagram, voeg je het in, en pas je de oriëntatie aan in Java

Als je een **cirkeldiagram** in een Word‑document moet maken, laat deze gids je precies zien hoe je dat doet. Je ziet hoe je een **cirkeldiagram invoegt**, een partitie explodeert voor nadruk, en **de diagramoriëntatie wijzigt** met een eenvoudige rotatie.

De tutorial behandelt alles wat je nodig hebt — van het opzetten van de Aspose.Words for Java‑bibliotheek tot het produceren van een definitief `.docx`‑bestand dat een geroteerd, geëxplodeerd cirkeldiagram toont. Er is geen externe documentatie nodig; volg gewoon de stappen en voer de code uit.

## Vereisten

* Java 17 of nieuwer geïnstalleerd.
* Maven of Gradle om afhankelijkheden te beheren.
* Een geldige Aspose.Words for Java‑licentie (of gebruik de gratis evaluatiemodus).

Voeg de Aspose.Words‑afhankelijkheid toe aan je `pom.xml` (Maven) of `build.gradle` (Gradle). Voorbeeld voor Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Pro tip:** Houd de bibliotheekversie up‑to‑date; de nieuwste release (24.10 op het moment van schrijven) bevat bugfixes voor diagramweergave.

## Stap 1: Maak een cirkeldiagram en voeg het in het document in

De eerste stap is om **cirkeldiagram**‑objecten te **maken** en ze in een Word‑bestand in te sluiten. De onderstaande code maakt een eenvoudig document, voegt een diagram‑placeholder toe, en voegt een cirkeldiagram van grootte 400 × 300 pixels in.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Waarom dit belangrijk is:** `builder.insertChart` maakt een diagram‑placeholder die Aspose.Words automatisch converteert naar een OOXML‑diagram wanneer het document wordt opgeslagen. Het argument `ChartType.PIE` vertelt de bibliotheek om een cirkeldiagram weer te geven, waardoor aan de **insert pie chart**‑vereiste wordt voldaan.

## Stap 2: Explodeer een cirkelpartitie om een segment te benadrukken

Een partitie explodeeren vestigt de aandacht op een specifiek gegevenspunt. De volgende regel explodeert de eerste partitie (index 0) met 10 punten:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Je kunt de index wijzigen om een andere partitie te targeten, of de explode‑afstand aanpassen voor een subtieler effect. Een partitie explodeeren is de standaard manier om een **explode pie slice** in Aspose.Words uit te voeren.

## Stap 3: Verander de diagramoriëntatie door te roteren

Het roteren van het diagram geeft een nieuw visueel perspectief. Gebruik `setRotationAngle` om het hele diagram met de klok mee te roteren (de hoek wordt gemeten in graden).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

De bovenstaande aanroep voldoet aan de **rotate pie chart**‑ en **change chart orientation**‑vereisten. Elke hoek tussen 0 en 360 graden wordt geaccepteerd.

## Volledig uitvoerbaar voorbeeld

Alles samenvoegend, hier is een compleet, zelfstandig programma dat een cirkeldiagram maakt, een partitie explodeert en het diagram roteert. Voer het uit vanuit je IDE of vanaf de opdrachtregel met `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Verwachte output

* Een bestand met de naam **CreatePieChartDemo.docx** verschijnt in de werkmap.
* Het openen van het bestand in Microsoft Word toont een 400 × 300 pixel cirkeldiagram.
* De eerste partitie (Q1) wordt 10 punten naar buiten verplaatst, waardoor een **explode pie slice**‑effect ontstaat.
* Het hele diagram is 45 graden gekanteld, wat **change chart orientation** en **rotate pie chart** demonstreert.

## Veelvoorkomende variaties en randgevallen

| Situatie | Hoe de code aan te passen |
|-----------|-----------------------|
| **Andere diagramgrootte** | Wijzig de `400, 300` argumenten in `insertChart`. |
| **Meerdere series** | Voeg meer `ChartSeries`‑objecten toe aan `chart.getSeries()`. |
| **Explodeer een andere partitie** | Gebruik `setExplode(sliceIndex, distance)` met de gewenste `sliceIndex`. |
| **Geen rotatie nodig** | Sla de `setRotationAngle`‑aanroep over of stel de hoek in op `0`. |
| **Exporteren naar PDF in plaats van DOCX** | Na het bouwen van het document, roep `doc.save("output.pdf")` aan met het PDF‑formaat. |

> **Let op:** Het gebruiken van een negatieve explode‑afstand veroorzaakt een `IllegalArgumentException`. Geef altijd een niet‑negatieve waarde op.

## Prestatie‑tip

Als je veel diagrammen in een lus genereert, hergebruik dan één `DocumentBuilder` en roep alleen `insertChart` aan voor elke iteratie. Dit vermindert het geheugenverbruik en versnelt de verwerking.

## Conclusie

Je weet nu hoe je **cirkeldiagram kunt maken**, **cirkeldiagram kunt invoegen**, **cirkeldiagram‑partitie kunt explodeeren**, en **cirkeldiagram kunt roteren** met Aspose.Words for Java. Het volledige voorbeeld toont de volledige workflow — van het initialiseren van het document tot het opslaan van een bestand dat een geroteerd, geëxplodeerd cirkeldiagram visualiseert.

Vervolgens kun je **de diagramoriëntatie** verder verkennen door 3‑D‑effecten toe te passen, of experimenteren met andere diagramtypen zoals **Bar** of **Line**. Dezelfde API‑patronen gelden, dus het uitbreiden van deze tutorial is eenvoudig.

Voel je vrij om de gegevens, partitie‑index of rotatiehoek aan te passen aan je eigen rapportagebehoeften, en deel je resultaten met de community!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een cirkeldiagram in een Word‑document in te voegen met Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Hoe een cirkeldiagram‑partitie te explodeeren in Java – Aspose.Words diagram‑tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}