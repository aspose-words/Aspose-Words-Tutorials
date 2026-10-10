---
category: general
date: 2026-10-10
description: Lär dig hur du roterar diagram i en Word‑fil och modifierar diagram i
  Word för att ändra storleken på ett donutdiagram med ett komplett Java‑exempel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: sv
lastmod: 2026-10-10
og_description: Hur man roterar diagram i en Word‑fil och modifierar diagram i Word
  för att ändra storleken på ett donutdiagram med Aspose.Words för Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Hur man roterar diagram i ett Word‑dokument – steg‑för‑steg Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Hur man roterar diagram i ett Word‑dokument med Aspose.Words
url: /sv/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man roterar diagram i ett Word-dokument med Aspose.Words

Om du behöver **how to rotate chart** i en Microsoft Word‑fil, visar den här guiden de exakta stegen. Du kommer också att lära dig hur du **modify chart in Word** för att **change doughnut chart size** utan att lämna din Java‑kod.

Word‑automatisering känns ofta som en serie av separata API‑anrop, men med Aspose.Words kan du behandla ett diagram som vilken annan dokumentnod som helst. I slutet av den här handledningen har du ett körbart program som laddar en befintlig `.docx`, roterar ett doughnut‑diagram med 45°, minskar hålet till 50 % av radien och sparar resultatet som en ny fil.

## Förutsättningar

* Java 17 eller nyare installerat.
* Maven (eller Gradle) för att hantera beroenden.
* Ett inmatnings‑Word‑dokument (`input.docx`) som redan innehåller ett doughnut‑diagram.
* En giltig Aspose.Words för Java‑licens (eller använd utvärderingsläget).

## Steg 1: Ställ in Maven‑projektet

Skapa ett nytt Maven‑projekt eller lägg till följande beroende i din befintliga `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Att köra `mvn clean install` laddar ner biblioteket och gör klasserna tillgängliga på din classpath.

## Steg 2: Ladda Word‑dokumentet som innehåller ett diagram

Den första operationen är att öppna det befintliga dokumentet. Klassen `Document` representerar hela filen.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Att ladda filen **modifierar inte** den; den skapar helt enkelt en in‑memory‑representation som du kan fråga och redigera.

## Steg 3: Skapa en DocumentBuilder för navigering

`DocumentBuilder` ger dig ett markör‑likt API för att gå igenom dokumentträdet. Vi kommer att använda den för att hitta den första diagramformen.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Buildern startar i början av dokumentet, men du kan flytta den till vilken nod som helst senare om så behövs.

## Steg 4: Hämta den första diagramformen

Diagram lagras som `Shape`‑noder. Genom att filtrera barnnoder av typen `NodeType.SHAPE` kan vi extrahera diagramobjektet.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Om dokumentet innehåller flera diagram kan du iterera över `getChildNodes` och kontrollera varje `Shape` för `hasChart()` innan du castar.

## Steg 5: Rotera diagrammet (how to rotate chart)

Ett doughnut‑diagram är i princip ett pajdiagram med ett hål. Att rotera det ändrar startvinkeln för den första sektorn.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

`setStartAngle`‑metoden förväntar sig en double som representerar grader. Positiva värden roterar medurs, medan negativa värden roterar moturs.

## Steg 6: Ändra storleken på doughnut‑hålet (change doughnut chart size)

Hålets storlek uttrycks som en bråkdel av diagramradien. Ett värde på `0.5` betyder att hålet upptar 50 % av den totala radien.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Tips:** Det giltiga intervallet är `0.0` (inget hål, dvs. en vanlig paj) till `0.9` (mycket tunn ring). Värden utanför detta intervall kommer att kasta ett `IllegalArgumentException`.

## Steg 7: Spara det modifierade dokumentet

Slutligen, skriv tillbaka ändringarna till disk.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

När du öppnar `DoughnutFormatted.docx` i Microsoft Word kommer du att se doughnut‑diagrammet roterat 45° och hålet minskat till hälften av sin ursprungliga storlek.

## Fullt, körbart exempel

När alla bitar sätts ihop, här är det kompletta programmet som du kan kopiera‑och‑klistra in i din IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Förväntat resultat

Att köra programmet skriver ut:

```
Chart rotated and doughnut size changed successfully.
```

Att öppna `DoughnutFormatted.docx` visar ett doughnut‑diagram där den första sektorn startar vid 45°‑positionen och den inre radien upptar hälften av den yttre radien.

## Vanliga varianter och edge cases

| Situation | Vad som ska justeras | Varför det är viktigt |
|-----------|----------------------|-----------------------|
| **Flera diagram** | Loopa igenom `getChildNodes(NodeType.SHAPE, true)` och kontrollera `shape.hasChart()` för varje | Säkerställer att du modifierar det avsedda diagrammet snarare än det första |
| **Stapeldiagram eller linjediagram** | `setStartAngle` gäller inte; använd `chart.getSeries().get(0).setFillFormat(...)` för andra visuella justeringar | Inte alla diagramtyper stödjer rotation; doughnut‑/paj‑diagram är de enda med en startvinkel |
| **Diagram utan doughnut‑hål** | Hoppa över `setDoughnutHoleSize` eller konvertera först diagramtypen till doughnut via `chart.setChartType(ChartType.DONUT)` | Att ändra hålstorlek på ett icke‑doughnut‑diagram kastar ett undantag |
| **Stora dokument** | Använd `DocumentBuilder.moveToDocumentStart()` och `builder.moveToNode(chartShape)` för riktad navigering | Förbättrar prestanda genom att undvika full traversering av orelaterade noder |

## Pro‑tips för pålitlig diagrammanipulation

* **Cache the chart reference** – Om du planerar att modifiera flera egenskaper, behåll en lokal `Chart`‑variabel istället för att upprepade gånger anropa `chartShape.getChart()`.
* **Validate input values** – Innan du anropar `setStartAngle` eller `setDoughnutHoleSize`, verifiera intervallet för att undvika körfel.
* **Use a license** – Utvärderingsläget sätter in ett vattenstämpel på första sidan. Att tillämpa en licens (`License license = new License(); license.setLicense("Aspose.Words.lic");`) tar bort den.

## Nästa steg

Nu när du vet **how to rotate chart** och **change doughnut chart size**, kan du utforska andra **modify chart in Word**‑scenarier:

* Ändra sektorns färger med `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Lägg till datamärkningar genom att anropa `chart.getSeries().get(0).setHasDataLabel(true)`.
* Exportera diagrammet som en bild med `chart.toImage(300, 300, ImageType.PNG)`.

Var och en av dessa tillägg följer samma mönster: hämta `Chart`‑objektet, anropa den lämpliga settern och spara dokumentet.

**Du har just bemästrat att rotera och ändra storlek på doughnut‑diagram i Word med Java.** Känn dig fri att anpassa koden för andra diagramtyper, integrera den i en större dokument‑genereringspipeline, eller kombinera den med Aspose.Slides för PowerPoint‑automatisering. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Dölj diagramaxel i ett Word‑dokument](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Infoga bubbeldiagram i Word‑dokument](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}