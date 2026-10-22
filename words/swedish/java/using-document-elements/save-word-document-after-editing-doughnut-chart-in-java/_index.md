---
category: general
date: 2026-09-11
description: Spara Word-dokument efter att ha redigerat ett donutdiagram med Aspose.Words
  för Java. Lär dig hur du ändrar storleken på donutens hål, roterar donutdiagrammet
  och redigerar donutdiagrammets egenskaper.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: sv
lastmod: 2026-09-11
og_description: Spara Word-dokument efter att ha redigerat ett munkdiagram med Aspose.Words
  för Java. Denna handledning visar hur du ändrar storleken på munkens hål, roterar
  munkdiagrammet och anpassar diagrammets utseende.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Spara Word-dokument efter att ha redigerat donutdiagram – Java‑guide
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
title: Spara Word-dokument efter att ha redigerat donutdiagram i Java
url: /sv/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara Word-dokument efter redigering av doughnut-diagram i Java

Om du behöver **spara Word-dokument** som innehåller ett anpassat doughnut-diagram, visar den här guiden exakt hur du gör. På bara några rader Java kan du ändra doughnut‑hålet, rotera doughnut‑diagrammet och sedan skriva resultatet tillbaka till disk.

Du får se ett komplett, körbart exempel som använder Aspose.Words for Java, samt tips för att hantera flera diagram, verifiera nodtyper och undvika vanliga fallgropar. Inga externa referenser krävs – allt du behöver är med.

## Förutsättningar

- Java 17 eller nyare installerat
- Maven eller Gradle för att hantera beroenden
- Aspose.Words for Java (version 23.9 eller senare) tillagt i ditt projekt  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- En Word‑fil (`input.docx`) som innehåller ett enda doughnut-diagram

## Steg 1: Läs in Word-dokumentet

Det första steget är att öppna källfilen. Detta steg är avgörande eftersom varje efterföljande operation arbetar på `Document`‑objektet i minnet.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Varför?** Att läsa in dokumentet skapar en DOM‑representation som låter dig gå igenom former, tabeller och diagram. Om filen inte kan öppnas kastar Aspose.Words ett undantag, så du omedelbart vet att sökvägen är fel.

## Steg 2: Hitta doughnut-diagrammets form

Ett diagram lagras i en `Shape`‑nod. Vi hämtar den första formen som innehåller ett diagram och kastar dess renderare till `Chart`.

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

> **Varför?** Att kontrollera `isChart()` förhindrar ett `ClassCastException` när dokumentet innehåller bilder eller andra former före diagrammet. Detta gör koden robust för dokument med blandat innehåll.

## Steg 3: Ändra storlek på doughnut‑hålet  

Nu redigerar vi doughnut‑hålet. Metoden `setHoleSize` förväntar sig en procentsats av diagrammets radie (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Varför?** Att ändra doughnut‑hålet (`change doughnut hole` / `change chart hole size`) låter dig framhäva eller tona ner det centrala området. Värden utanför 10‑90 % ignoreras av API‑et.

## Steg 4: Rotera doughnut‑diagrammet  

För att kontrollera var den första sektorn börjar, ange vinkeln för första sektorn. Detta roterar i praktiken **doughnut‑diagrammet**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Varför?** Att rotera diagrammet är användbart när du vill att en viss sektor ska visas högst upp eller för att matcha en designspecifikation.

## Steg 5: Spara det uppdaterade dokumentet  

Till sist skriver du tillbaka ändringarna till en ny fil. Detta är ögonblicket då du **sparar Word-dokument** med det redigerade diagrammet.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Förväntat resultat:** `output.docx` innehåller originalinnehållet, men doughnut‑diagrammet har nu ett 30 % hål och dess första sektor börjar vid 45 °. När du öppnar filen i Microsoft Word visas det omvandlade diagrammet.

## Fullt fungerande exempel

Nedan är det kompletta programmet som du kan kopiera‑klistra in i din IDE. Det innehåller alla import‑ och felhanteringsrutiner som behövs för att **redigera doughnut‑diagram** och **spara Word-dokument** på ett säkert sätt.

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

### Förväntat resultat

När du öppnar `output.docx`:

- Doughnut‑diagrammets centrala hål upptar ungefär en tredjedel av diagrammets radie.  
- Den första sektorn börjar vid 45‑graderspositionen, vilket förflyttar hela diagrammet medurs.  

## Vanliga variationer och kantfall

| Situation | Så hanterar du |
|-----------|----------------|
| **Flera diagram** | Iterera genom `doc.getChildNodes(NodeType.SHAPE, true)` och filtrera `shape.isChart()`; tillämpa `setHoleSize` / `setFirstSliceAngle` på varje `Chart`. |
| **Diagrammet är inte ett doughnut** | Kontrollera `chart.getType()`; anropa endast `setHoleSize` när `chart.getType() == ChartType.DOUGHNUT`. |
| **Behöver ändra hålstorlek dynamiskt** | Beräkna önskad procentsats baserat på datavärden och anropa sedan `setHoleSize(computedValue)`. |
| **Spara till en ström** | Använd |

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hur man sparar dokument som PDF med Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Spara Word med lösenord med Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}