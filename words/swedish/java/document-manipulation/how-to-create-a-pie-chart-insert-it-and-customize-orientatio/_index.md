---
category: general
date: 2026-11-25
description: Lär dig hur du skapar ett cirkeldiagram i Java, infogar cirkeldiagrammet
  i ett Word‑dokument, exploderar en diagramdel och ändrar diagramorienteringen med
  tydliga kodexempel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: sv
lastmod: 2026-11-25
og_description: Skapa ett cirkeldiagram i Java, infoga cirkeldiagrammet i ett dokument,
  spränga ut en diagramdel och ändra diagramorienteringen med steg‑för‑steg‑kod.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Skapa ett cirkeldiagram i Java – infoga, explodera en sektor och rotera
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
title: Hur man skapar ett cirkeldiagram, infogar det och anpassar orienteringen i
  Java
url: /sv/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett pajdiagram, infogar det och anpassar orienteringen i Java

Om du behöver **create a pie chart** i ett Word‑dokument, visar den här guiden exakt hur du gör. Du kommer att se hur du **insert pie chart**, exploderar en skiva för att framhäva den, och **change chart orientation** med en enkel rotation.

Handledningen täcker allt du behöver—från att sätta upp Aspose.Words for Java‑biblioteket till att producera en slutlig `.docx`‑fil som visar ett roterat, exploderat pajdiagram. Ingen extern dokumentation krävs; följ bara stegen och kör koden.

## Förutsättningar

* Java 17 eller nyare installerat.
* Maven eller Gradle för att hantera beroenden.
* En giltig Aspose.Words for Java‑licens (eller använd gratis utvärderingsläge).

Lägg till Aspose.Words‑beroendet i din `pom.xml` (Maven) eller `build.gradle` (Gradle). Exempel för Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Pro tip:** Håll biblioteksversionen uppdaterad; den senaste releasen (24.10 vid skrivande) innehåller buggfixar för diagramrendering.

## Steg 1: Skapa pajdiagram och infoga det i dokumentet

Det första steget är att **create pie chart**‑objekt och bädda in dem i en Word‑fil. Koden nedan bygger ett enkelt dokument, lägger till en diagram‑platshållare och infogar ett pajdiagram med storleken 400 × 300 pixlar.

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

**Varför detta är viktigt:** `builder.insertChart` skapar en diagram‑platshållare som Aspose.Words automatiskt konverterar till ett OOXML‑diagram när dokumentet sparas. Argumentet `ChartType.PIE` talar om för biblioteket att rendera ett pajdiagram, vilket uppfyller kravet **insert pie chart**.

## Steg 2: Explodera pajskiva för att markera ett segment

Att explodera en skiva drar uppmärksamhet till en specifik datapunkt. Följande rad exploderar den första skivan (index 0) med 10 punkter:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Du kan ändra indexet för att rikta in dig på en annan skiva, eller justera exploderingsavståndet för en mer subtil effekt. Att explodera en skiva är det standardmässiga sättet att **explode pie slice** i Aspose.Words.

## Steg 3: Ändra diagramorientering genom att rotera det

Att rotera diagrammet ger ett nytt visuellt perspektiv. Använd `setRotationAngle` för att rotera hela diagrammet medurs (vinkeln mäts i grader).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

Anropet ovan uppfyller kraven **rotate pie chart** och **change chart orientation**. Alla vinklar mellan 0 och 360 grader accepteras.

## Fullt körbart exempel

När allt sätts ihop, här är ett komplett, fristående program som skapar ett pajdiagram, exploderar en skiva och roterar diagrammet. Kör det från din IDE eller från kommandoraden med `java -cp <classpath> PieChartDemo`.

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

### Förväntat resultat

* En fil med namnet **CreatePieChartDemo.docx** visas i arbetskatalogen.
* När filen öppnas i Microsoft Word visas ett 400 × 300 pixlar stort pajdiagram.
* Den första skivan (Q1) är förskjuten utåt med 10 punkter, vilket skapar en **explode pie slice**‑effekt.
* Hela diagrammet är lutat 45 grader, vilket demonstrerar **change chart orientation** och **rotate pie chart**.

## Vanliga variationer och kantfall

| Situation | Hur man anpassar koden |
|-----------|------------------------|
| **Olika diagramstorlek** | Ändra argumenten `400, 300` i `insertChart`. |
| **Flera serier** | Lägg till fler `ChartSeries`‑objekt till `chart.getSeries()`. |
| **Explodera en annan skiva** | Använd `setExplode(sliceIndex, distance)` med önskat `sliceIndex`. |
| **Ingen rotation behövs** | Utelämna anropet `setRotationAngle` eller sätt vinkeln till `0`. |
| **Exportera till PDF istället för DOCX** | Efter att dokumentet byggts, anropa `doc.save("output.pdf")` med PDF‑formatet. |

> **Watch out for:** Att använda ett negativt exploderingsavstånd kastar `IllegalArgumentException`. Ange alltid ett icke‑negativt värde.

## Prestandatips

Om du genererar många diagram i en loop, återanvänd en enda `DocumentBuilder` och anropa bara `insertChart` för varje iteration. Detta minskar minnesåtgången och snabbar upp bearbetningen.

## Slutsats

Du vet nu hur du **create pie chart**, **insert pie chart**, **explode pie slice** och **rotate pie chart** med Aspose.Words for Java. Det kompletta exemplet demonstrerar hela arbetsflödet—från att initiera dokumentet till att spara en fil som visualiserar ett roterat, exploderat pajdiagram.

Nästa steg kan vara att utforska **changing chart orientation** ytterligare genom att applicera 3‑D‑effekter, eller experimentera med andra diagramtyper såsom **Bar** eller **Line**. Samma API‑mönster gäller, så det är enkelt att utöka den här handledningen.

Känn dig fri att ändra data, skiva‑index eller rotationsvinkel för att passa dina egna rapporteringsbehov, och dela dina resultat med communityn!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}