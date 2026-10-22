---
category: general
date: 2026-07-20
description: Voeg een cirkeldiagram toe in Java met een stapsgewijze handleiding.
  Leer hoe je een segment explodeert, hoe je een cirkeldiagram draait, een segment
  van het cirkeldiagram markeert en een segment van het cirkeldiagram aanpast.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: nl
lastmod: 2026-07-20
og_description: Voeg een taartdiagram toe in Java en leer hoe je een segment kunt
  laten uitwaaieren, hoe je een taartdiagram kunt roteren, een segment kunt markeren
  en een segment kunt aanpassen voor gepolijste visuele rapporten.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Voeg taartdiagram in Java in – Exploderen, roteren en markeren
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Taartdiagram invoegen in Java – Exploderen, roteren & segmenten markeren
url: /nl/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Pie chart invoegen in Java – Exploderen, roteren & segmenten markeren

Heb je ooit een **pie chart invoegen** nodig gehad in een Java‑rapport maar wist je niet hoe je een enkel segment kunt laten uitsteken? Je bent niet de enige. Of je nu een dashboard bouwt, een factuur genereert, of gewoon enquête‑resultaten visualiseert, een goed gestyled pie chart kan ruwe cijfers omzetten in direct begrijpelijke inzichten.

In deze tutorial zie je een compleet, kant‑klaar voorbeeld dat laat zien hoe je een pie chart invoegt, **hoe een slice te exploderen**, **hoe een pie chart te roteren**, en zelfs **een pie chart slice te markeren** met aangepaste kleuren. Aan het einde heb je een herbruikbare code‑fragment die je in elk Java‑project kunt plaatsen dat de populaire *JFreeChart*‑bibliotheek gebruikt (of een vergelijkbare API).

## Vereisten

- Java 17 of hoger (de code compileert ook met oudere versies, maar we gebruiken de moderne `var`‑syntaxis voor beknoptheid).  
- Maven of Gradle om de `org.jfree:jfreechart`‑dependency binnen te halen.  
- Een basisbegrip van Java‑klassen en het concept van een chart‑builder.  

Als je nog nooit een bibliotheek aan een Maven‑project hebt toegevoegd, plak dan gewoon dit in je `pom.xml`:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Dat is alles—geen extra configuratie nodig.

## Stap 1: Pie chart invoegen – Maak de Builder en Chart‑object

Allereerst hebben we een *builder* (denk aan een fabriek) die weet hoe grafieken te produceren. In JFreeChart doet de `ChartFactory` het zware werk.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Waarom beginnen we met de dataset? Omdat de grafiek zelf slechts een visuele omhulling van de cijfers is. Door hier een **pie chart invoegen** hebben we al een canvas van 400 × 300 (de grootte wordt later toegepast wanneer we deze naar een afbeelding renderen).

## Stap 2: Hoe een slice te exploderen – Benadruk het eerste segment

Nu de grafiek bestaat, laten we de eerste slice laten opvallen. Een slice exploderen trekt het iets weg van de cirkel, waardoor de lezer’s aandacht wordt getrokken.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Let op dat we de **how to explode slice**‑phrase in de methodenaam gebruiken; dat maakt de intentie glashelder. De `setExplodePercent`‑methode neemt een sleutel (het slice‑label) en een percentage, zodat je de “pop‑out”‑afstand naar wens kunt aanpassen.

## Stap 3: Hoe een pie chart te roteren – Verander de starthoek

Een standaard pie chart start op de 12‑uur‑positie. Soms wil je dat de eerste slice ergens anders begint—misschien om uit te lijnen met een design‑mock‑up of om overeen te komen met een andere grafiek.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Het aanroepen van `rotateChart(chart, 45)` roteert de hele pie zodat de “Apples”‑slice begint op een hoek van 45 graden, precies wat de **how to rotate pie chart**‑eis vereist.

## Stap 4: Pie chart slice markeren – Aangepaste kleuren en labels

Naast het exploderen wil je misschien een slice een unieke kleur of een vet label geven om echt **pie chart slice te markeren**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Hier hebben we **customize pie chart slice** door de verf en label‑stijl aan te passen. Voel je vrij om de kleur of het lettertype te wijzigen zodat het bij je merkpalet past.

## Stap 5: Render de grafiek naar een afbeelding (optioneel maar handig)

De meeste real‑world apps hebben de grafiek nodig als PNG, JPEG of zelfs een PDF. Hieronder een snelle manier om de grafiek naar een bestand te schrijven.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Het uitvoeren van de volledige flow produceert een 400 × 300 PNG die er ongeveer zo uitziet:

![Voorbeeld van ingevoegde pie chart](image.png){: alt="Voorbeeld van ingevoegde pie chart die een geëxplodeerde en geroteerde slice toont"}

## Volledig werkend voorbeeld

Alles samenvoegend, hier is een `main`‑methode die je kunt kopiëren‑plakken in een nieuwe Java‑klasse en uitvoeren:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Verwachte output

Het uitvoeren van het programma maakt een bestand genaamd **fruit-pie.png**. Open het en je ziet:

- Een 400 × 300 pie chart met de titel “Fruit Distribution”.  
- De “Apples”‑slice geëxplodeerd naar buiten met 15 %.  
- De volledige grafiek geroteerd zodat “Apples” begint op de 45‑graden‑positie.  
- De geëxplodeerde

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een kolomgrafiek te maken met Aspose.Words voor Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Scatter‑grafiek invoegen](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Area‑grafiek invoegen](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}