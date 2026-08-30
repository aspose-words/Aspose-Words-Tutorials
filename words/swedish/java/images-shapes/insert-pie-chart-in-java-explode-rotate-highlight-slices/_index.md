---
category: general
date: 2026-07-20
description: Infoga ett cirkeldiagram i Java med en steg‑för‑steg‑guide. Lär dig hur
  du exploderar en sektor, roterar cirkeldiagrammet, markerar en sektor i cirkeldiagrammet
  och anpassar en sektor i cirkeldiagrammet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: sv
lastmod: 2026-07-20
og_description: Infoga ett cirkeldiagram i Java och lär dig hur du exploderar en skiva,
  roterar cirkeldiagrammet, markerar en skiva och anpassar en skiva för polerade visuella
  rapporter.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Infoga cirkeldiagram i Java – Explodera, rotera och markera
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
title: Infoga cirkeldiagram i Java – explodera, rotera & markera segment
url: /sv/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga pajdiagram i Java – Explodera, rotera & markera segment

Har du någonsin behövt **insert pie chart** i en Java-rapport men varit osäker på hur du får ett enskilt segment att poppa ut? Du är inte ensam. Oavsett om du bygger en instrumentpanel, genererar en faktura eller bara visualiserar enkätresultat, kan ett välstylat pajdiagram förvandla råa siffror till omedelbart begripliga insikter.

I den här handledningen kommer du att se ett komplett, färdigt‑att‑köra exempel som visar hur du **insert pie chart**, **how to explode slice**, **how to rotate pie chart**, och till och med **highlight pie chart slice** med anpassade färger. I slutet har du ett återanvändbart kodsnutt som du kan lägga in i vilket Java‑projekt som helst som använder det populära *JFreeChart*-biblioteket (eller någon liknande API).

## Förutsättningar

- Java 17 eller senare (koden kompileras med äldre versioner, men vi använder den moderna `var`‑syntaxen för korthet).  
- Maven eller Gradle för att hämta `org.jfree:jfreechart`‑beroendet.  
- En grundläggande förståelse för Java‑klasser och konceptet med en diagram‑byggare.  

Om du aldrig har lagt till ett bibliotek i ett Maven‑projekt, klistra bara in detta i din `pom.xml`:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Klart—ingen extra konfiguration krävs.

## Steg 1: Infoga pajdiagram – Skapa byggaren och diagramobjektet

Först och främst: vi behöver en *builder* (tänk på den som en fabrik) som vet hur man skapar diagram. I JFreeChart gör `ChartFactory` det tunga lyftet.

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

Varför börjar vi med datasetet? För diagrammet i sig är bara ett visuellt omslag runt siffrorna. Genom att **insert pie chart** här har vi redan en 400 × 300‑canvas (storleken kommer att appliceras senare när vi renderar den till en bild).

## Steg 2: How to Explode Slice – Markera det första segmentet

Nu när diagrammet finns, låt oss få det första segmentet att sticka ut. Att explodera ett segment drar det lite bort från cirkeln, vilket fångar läsarens uppmärksamhet.

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

Observera att vi använder frasen **how to explode slice** i metodnamnet; det gör avsikten kristallklar. Metoden `setExplodePercent` tar en nyckel (segmentets etikett) och en procentsats, så du kan justera “pop‑out”-avståndet efter behov.

## Steg 3: How to Rotate Pie Chart – Ändra startvinkeln

Ett standardpajdiagram startar vid 12‑timmarspositionen. Ibland vill du att det första segmentet ska börja någon annanstans—kanske för att matcha en design‑mockup eller för att passa ett annat diagram.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Genom att anropa `rotateChart(chart, 45)` roteras hela pajen så att “Apples”-segmentet börjar vid en 45‑gradig vinkel, exakt vad **how to rotate pie chart**‑kravet efterfrågar.

## Steg 4: Highlight Pie Chart Slice – Anpassade färger och etiketter

Förutom att explodera kan du vilja ge ett segment en unik färg eller en fet etikett för att verkligen **highlight pie chart slice**.

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

Här har vi **customize pie chart slice** genom att ändra dess färg och etikettstil. Känn dig fri att byta färg eller teckensnitt för att matcha ditt varumärkespalett.

## Steg 5: Rendera diagrammet till en bild (valfritt men praktiskt)

De flesta verkliga applikationer behöver diagrammet som PNG, JPEG eller till och med en PDF. Nedan är ett snabbt sätt att skriva diagrammet till en fil.

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

Att köra hela flödet kommer att producera en 400 × 300 PNG som ser ut ungefär så här:

![Insert pie chart example](image.png){: alt="Insert pie chart example showing an exploded and rotated slice"}

## Fullständigt fungerande exempel

Sätter vi ihop allt, här är en `main`‑metod som du kan kopiera‑klistra in i en ny Java‑klass och köra:

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

### Förväntat resultat

När programmet körs skapas en fil som heter **fruit-pie.png**. Öppna den så ser du:

- Ett 400 × 300 pajdiagram med titeln “Fruit Distribution”.  
- “Apples”-segmentet exploderat utåt med 15 %.  
- Hela diagrammet roterat så att “Apples” startar vid 45‑graderspositionen.  
- The exploded

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Infoga spridningsdiagram](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Infoga ytdiagram](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}