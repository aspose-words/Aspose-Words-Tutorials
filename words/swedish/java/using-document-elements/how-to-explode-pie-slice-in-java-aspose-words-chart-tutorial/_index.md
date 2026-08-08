---
category: general
date: 2026-08-07
description: Hur man exploderar ett pajsegment i Java med Aspose.Words. Lär dig att
  lägga till ledlinjer till pajen, skapa ett Word‑diagram och anpassa pajdiagrammets
  segment.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: sv
lastmod: 2026-08-07
og_description: Hur du exploderar ett pajsegment i Java med Aspose.Words. Den här
  guiden visar hur du lägger till ledlinjer till pajen, skapar Word-diagram och anpassar
  segment i pajdiagram för tydlig visuell effekt.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Hur man spränger en tårtbit i Java – Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Hur man exploderar ett pajsegment i Java – Aspose.Words-diagramhandledning
url: /sv/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man exploderar en pajskiva i Java – Aspose.Words-diagramhandledning

Om du behöver veta **hur man exploderar en pajskiva** i ett Word‑dokument med Java, så har den här handledningen dig täckt. Vi visar också **hur man lägger till ledarlinjer till paj**‑diagram, **java create word chart**‑objekt, och **anpassar pajdiagram‑skivor** för ett polerat resultat. I slutet av guiden har du ett komplett, körbart exempel som du kan lägga in i vilket Java‑projekt som helst.

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## Förutsättningar

Innan du börjar, se till att du har:

* Java Development Kit (JDK) 8 eller högre.
* Maven eller Gradle för beroendehantering.
* En Aspose.Words för Java-licens (den kostnadsfria utvärderingen fungerar för lärande).
* Grundläggande kunskap om Java‑syntax och objekt‑orienterade koncept.

> **Pro tip:** Även om Aspose.Words erbjuder en gratis provperiod, tar ett licensköp bort utvärderingsvattenstämpeln från genererade dokument.

## Vad den här handledningen täcker

* Skapa ett nytt Word‑dokument från grunden.  
* Infoga ett **pie chart** med hjälp av `DocumentBuilder`.  
* **Exploding a pie slice** för att markera en datapunkt.  
* **Adding leader lines to pie** för tydligare etikettering.  
* Anpassa skivornas utseende, såsom färger och kanter.  
* Spara dokumentet till disk och verifiera resultatet.

---

## Så exploderar du en pajskiva med Aspose.Words i Java

Det första steget är att konfigurera diagramobjektet och explodera den önskade skivan. Aspose.Words exponerar diagrammet via `Shape`‑klassen, och varje skiva är en `ChartPoint`. Genom att sätta egenskapen `Explosion` styr du hur långt skivan flyttas utåt.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Varför det fungerar:**  
`setExplosion(20)` talar om för diagrammotorn att förskjuta skivan med 20 punkter från diagrammets centrum. Värdet är relativt; större tal skapar en mer dramatisk effekt. Du kan explodera vilken skiva som helst genom att ändra indexet (`get(1)`, `get(2)`, …).

## Lägg till ledarlinjer till paj för tydligare etiketter

Ledarlinjer kopplar en skivas etikett till dess kant, vilket är särskilt användbart när skivor är exploderade eller när diagrammet innehåller många små sektioner. Anropet `setLeaderLines(true)` aktiverar denna funktion för hela serien.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Varför du behöver ledarlinjer:**  
När en skiva är exploderad kan standardetiketten överlappa med andra element. Ledarlinjer håller etiketten läsbar genom att rita en kort linje från skivan till textrutan.

## Java create Word chart – infoga dataserier

Ett diagram utan data är inte särskilt användbart. Du måste fylla serierna med kategorier och värden. Nedan lägger vi till tre kategorier som representerar marknadsandelar.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Förklaring:**  
`ChartSeries` innehåller både kategorierna (skivnamnen) och de numeriska värdena. Att aktivera `ShowCategoryName` och `ShowPercentage` gör diagrammet självförklarande, vilket passar bra ihop med de ledarlinjer vi lade till tidigare.

## Anpassa pajdiagram‑skivor bortom explosion

Förutom att explodera en skiva vill du ofta justera färger, kanter eller till och med dölja en skiva helt. Följande kodsnutt demonstrerar tre vanliga anpassningar:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Varför anpassa skivor:**  
Anpassade färger får diagrammet att stämma överens med företagets varumärke, medan kanter förbättrar läsbarheten på utskrivna sidor. Att dölja en skiva är användbart när du vill behålla datamodellen intakt men tillfälligt utesluta en kategori från den visuella utskriften.

## Spara dokumentet och verifiera resultatet

Slutligen skriver du dokumentet till disk. Du kan öppna den genererade `.docx`‑filen i Microsoft Word, LibreOffice eller någon annan visare som stödjer formatet.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Förväntat resultat:**  
När du öppnar `PieChartDemo.docx` kommer du att se ett pajdiagram där den första skivan (Product A) är exploderad utåt, ledarlinjer pekar från varje skiva till dess etikett, och skivorna visas i de anpassade färgerna grön, blå och orange. Den dolda skivan (Product C) kommer inte att vara synlig, men procentsatserna kommer fortfarande att summera till 100 % eftersom data kvarstår i diagrammets serier.

---

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan kopiera, klistra in och köra efter att ha lagt till Aspose.Words‑beroendet i ditt projekt.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Beroende (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hur man laddar Word‑dokument med Aspose.Words Java: Omfattande guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Hur man skapar formulärfält och lägger till innehåll med DocumentBuilder i Aspose.Words för Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}