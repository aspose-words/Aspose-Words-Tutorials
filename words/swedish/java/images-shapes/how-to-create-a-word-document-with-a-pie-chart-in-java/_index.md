---
category: general
date: 2026-09-18
description: Lär dig att skapa ett Word‑dokument och infoga ett cirkeldiagram med
  Aspose.Words för Java. Inkluderar steg för att rotera cirkeldiagrammet och generera
  Word‑filen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: sv
lastmod: 2026-09-18
og_description: Skapa ett Word‑dokument och infoga ett cirkeldiagram med Java. Följ
  den här guiden för att rotera cirkeldiagrammet, spränga ut segmenten och generera
  en Word‑fil.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Skapa ett Word-dokument med ett cirkeldiagram – steg‑för‑steg Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Hur man skapar ett Word‑dokument med ett cirkeldiagram i Java
url: /sv/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur du skapar ett Word-dokument med ett cirkeldiagram i Java

Om du behöver **skapa ett Word-dokument** som visualiserar data, visar den här guiden hur du gör det med Aspose.Words for Java. Du kommer att lära dig att infoga ett cirkeldiagram, explodera en del, rotera diagrammet och slutligen **generera en Word-fil** som du kan öppna i Microsoft Word.

Att bygga rapporter som kombinerar text och diagram kräver inte ett separat grafikverktyg. I slutet av den här handledningen har du ett komplett, körbart program som skapar en .docx-fil som innehåller ett fullt konfigurerat cirkeldiagram.

## Förutsättningar

- Java 17 eller senare (koden kompileras även med Java 8+)
- Maven eller Gradle för beroendehantering
- Aspose.Words for Java-licens (gratis provversion fungerar för detta exempel)
- Grundläggande kunskap om Java-syntax

## Steg 1: Ställ in Maven-projektet

Skapa ett nytt Maven-projekt och lägg till Aspose.Words‑beroendet i `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Proffstips:** Håll versionsnumret uppdaterat; nyare releaser innehåller förbättringar av diagramtyper och buggfixar.

## Steg 2: Skapa ett nytt Word-dokument

Den första operationen när du **skapar ett Word-dokument** programmässigt är att instansiera ett `Document`‑objekt. Detta objekt representerar hela .docx‑filen i minnet.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

`Document`‑klassen är ingångspunkten för alla Word‑bearbetningsfunktioner. Ingen fil skrivs till disk i detta skede; allt sker i RAM tills du anropar `save`.

## Steg 3: Hur du infogar ett cirkeldiagram

En `DocumentBuilder` låter dig lägga till innehåll i dokumentet. Med `insertChart` kan du **infoga cirkeldiagram**‑objekt direkt.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` instruerar Aspose.Words att skapa ett cirkeldiagram. Dimensionerna anges i punkter (1 pt ≈ 1/72 in). Efter detta anrop visas diagrammet i ett nytt stycke.

## Steg 4: Fyll diagrammet med data

Ett cirkeldiagram behöver en serie värden. Här lägger vi till tre kategorier: “Apples”, “Bananas” och “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

`add`‑metoden bygger serien och skapar automatiskt legendposter. Du kan återanvända detta mönster för vilken numerisk datamängd som helst.

## Steg 5: Markera den första delen

Att explodera en del drar uppmärksamhet till ett specifikt värde. Den första delen (index 0) exploderas med 20 punkter.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Att sätta `explode` på serien påverkar hela diagrammet, så endast den första datapunkten förskjuts.

## Steg 6: Hur du roterar ett cirkeldiagram

Att rotera diagrammet förbättrar den visuella balansen, särskilt när den största delen inte är högst upp. Metoden `setRotationAngle` förväntar sig grader.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

En rotation på 45° flyttar startvinkeln medurs, vilket gör diagrammet lättare att läsa i många layouter.

## Steg 7: Spara dokumentet och generera en Word-fil

Slutligen skriver du dokumentet till disk. Detta steg **genererar en Word-fil** som kan öppnas med Microsoft Word, LibreOffice eller någon kompatibel visare.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

`save`‑metoden upptäcker automatiskt .docx‑filändelsen och skriver ett Word‑kompatibelt paket. Mappen `output` måste finnas eller så kan du skapa den programmässigt.

### Förväntat resultat

Efter att ha kört programmet, öppna `output/PieChart.docx`. Du bör se:

- En enda sida som innehåller ett 400 × 300 pt cirkeldiagram.
- “Apples”-delen exploderad utåt med 20 pt.
- Hela diagrammet roterat 45° medurs.
- En legend som matchar de tre fruktkategorierna.

## Vanliga variationer och kantfall

### Infoga flera diagram

Om du behöver mer än ett diagram, anropa `builder.insertChart` igen efter att ha flyttat markören:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Ändra diagramfärger

Du kan anpassa delarnas färger via seriens `getPoints()`‑samling:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Hantera stora datamängder

För datamängder med mer än 10 delar, överväg att använda ett doughnut‑diagram (`ChartType.DOUGHNUT`) för att hålla visualiseringen tydlig.

## Slutsats

Du vet nu hur du **skapar ett Word-dokument**, **infogar ett cirkeldiagram**, **roterar ett cirkeldiagram** och **genererar en Word-fil** med Aspose.Words for Java. Den kompletta lösningen demonstrerar hela arbetsflödet från dokumentinitiering till slutlig filutmatning, och täcker både “hur” och “varför” bakom varje steg.

Nästa, utforska relaterade ämnen såsom **hur du skapar cirkeldiagram**‑data från en databas, lägger till datalabels, eller exporterar diagrammet som en bild. Experimentera med olika diagramtyper (stapel, linje, doughnut) för att bredda ditt Word‑automatiseringsverktyg.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}