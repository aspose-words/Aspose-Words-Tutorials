---
category: general
date: 2026-10-04
description: Leer hoe je een segment in een Word‑diagram kunt laten exploderen, een
  taartdiagramsegment kunt laten exploderen en de grootte van een donutdiagram kunt
  aanpassen met een stapsgewijs Java‑voorbeeld.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: nl
lastmod: 2026-10-04
og_description: Hoe een segment in een Word‑grafiek kunt laten exploderen en taart‑
  of donutgrafieken kunt aanpassen met Java. Volg het volledige voorbeeld om een grafiek
  in Word te wijzigen.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Hoe een segment in een Word-diagram te exploderen – volledige Java-gids
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Hoe een segment in een Word‑grafiek explodeert en het uiterlijk aanpast
url: /nl/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een slice te exploderen in een Word‑diagram en het uiterlijk aan te passen

Als je **how to explode slice** in een Word‑diagram moet doen, laat deze gids je precies zien hoe. Of je nu een verkooppresentatie of een financieel rapport voorbereidt, het exploderen van een slice van een taart‑chart of het aanpassen van een donut‑hole kan de belangrijkste gegevens laten opvallen. In de volgende secties leer je ook hoe je **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, en **customize pie chart word** documenten kunt gebruiken met Aspose.Words for Java.

Je rondt deze tutorial af met een compleet, kant‑en‑klaar Java‑programma dat een `.docx`‑bestand laadt, de eerste slice van een taart‑chart explodeert, de grootte van het donut‑hole wijzigt en het resultaat opslaat. Er zijn geen externe scripts of handmatige bewerkingen nodig.

## Vereisten

- Java 17 of later geïnstalleerd op je ontwikkelmachine.  
- Maven 3.6+ (of Gradle) om afhankelijkheden te beheren.  
- Aspose.Words for Java‑bibliotheek (de gratis proefversie werkt voor ontwikkeling).  
- Een Word‑document (`input.docx`) dat minstens één diagram bevat (taart of donut).

## Stap 1: Voeg Aspose.Words toe aan je project

Als je Maven gebruikt, voeg dan de volgende afhankelijkheid toe aan je `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Voor Gradle, plaats dit in `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Houd je bibliotheekversie up‑to‑date; nieuwere releases voegen ondersteuning toe voor extra diagramtypen en verbeteren de prestaties.

## Stap 2: Laad het Word‑document dat een diagram bevat

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Waarom dit belangrijk is:** Het laden van het document creëert een in‑memory representatie die Aspose.Words kan doorlopen. Zonder dit object kun je de diagram‑knooppunten niet benaderen.

## Stap 3: Haal het eerste diagram op in het document

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Uitleg:** `NodeType.SHAPE` omvat alle tekenobjecten, inclusief diagrammen. Het argument `true` vertelt Aspose om recursief te zoeken, zodat het eerste diagram wordt gevonden, zelfs als het genest is in een tabel.

## Stap 4: Explode de eerste slice van een taart‑chart

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Hoe het werkt:** De `setExplosion`‑methode neemt een numerieke waarde die bepaalt hoe ver de slice van het midden af beweegt. Een waarde van `20` is visueel merkbaar zonder de diagramlay-out te breken.

## Stap 5: Pas de grootte van het donut‑hole aan voor een donut‑chart

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Waarom dit helpt:** Een groter donut‑hole kan de leesbaarheid verbeteren wanneer je veel gegevenspunten hebt. De `setDoughnutHoleSize`‑methode verwacht een percentage (0‑100).

## Stap 6: Sla het gewijzigde document op

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Verwachte output

- De eerste slice van het eerste taart‑diagram wordt naar buiten verplaatst, waardoor deze opvalt.
- Als het diagram een donut is, wordt het centrale gat uitgebreid tot 40 % van de diagramradius.
- Het resulterende bestand `PieChart.docx` kan worden geopend in Microsoft Word, LibreOffice, of elke compatibele viewer, waarbij de visuele wijzigingen die je programmatically hebt toegepast worden getoond.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma in één blok. Kopieer het naar `ChartExploder.java`, pas de bestands‑paden aan, en voer het uit met `mvn compile exec:java` (of de run‑configuratie van je IDE).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Het uitvoeren van deze code zal **modify chart in Word**, **explode pie chart slice**, en **change doughnut chart size** automatisch.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| *Wat als het document meerdere diagrammen bevat?* | Het voorbeeld richt zich op het **eerste** diagram (`NodeType.SHAPE, 0`). Om met andere diagrammen te werken, wijzig je de index of iterate je door `doc.getChildNodes(NodeType.SHAPE, true)` en filter je op `shape.getChart() != null`. |
| *Kan ik een slice exploderen die niet de eerste is?* | Ja. Toegang tot de gewenste serie via `chart.getSeries().get(seriesIndex)` en roep `setExplosion(value)` aan. Indexen zijn nul‑gebaseerd. |
| *Werkt dit met Word‑bestanden van 2007‑2021?* | Aspose.Words ondersteunt `.doc`, `.docx`, `.dot` en `.dotx`. dezelfde code werkt in alle versies omdat de bibliotheek het bestandsformaat abstracteert. |
| *Wat als het diagram een staaf‑ of lijndiagram is?* | `setExplosion` en `setDoughnutHoleSize` zijn alleen van toepassing op taart‑type diagrammen. De code slaat die bewerkingen veilig over wanneer het diagramtype anders is. |
| *Heb ik een licentie nodig voor Aspose.Words?* | Een gratis evaluatielicentie verwijdert de 30‑daagse limiet maar voegt een watermerk toe. Voor productie, koop een licentie om het watermerk te verwijderen en volledige functionaliteit te ontgrendelen. |

## Conclusie

Je weet nu **how to explode slice** in een Word‑diagram, hoe je **modify chart in Word** en hoe je **change doughnut chart size** kunt uitvoeren met Aspose.Words for Java. Het volledige voorbeeld toont de volledige workflow — van het laden van een document, het vinden van het diagram, het toepassen van visuele aanpassingen, tot het opslaan van het resultaat — zodat je deze stappen kunt integreren in elke rapportage‑ of document‑generatie‑pipeline.

**Volgende stappen**

- Verken andere diagram‑aanpassingen zoals het wijzigen van kleuren, het toevoegen van gegevenslabels, of het wisselen van diagramtypen (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Combineer deze logica met Aspose.PDF om een PDF‑versie van hetzelfde rapport te genereren.  
- Automatiseer het proces voor een batch documenten door over bestanden in een map te itereren.

Voel je vrij om te experimenteren met verschillende explosiewaarden of donut‑hole‑percentages om aan je ontwerprichtlijnen te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een kolomdiagram te maken met Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Diagramas as verbergen in een Word‑document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Bubbeldiagram invoegen in Word‑document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}