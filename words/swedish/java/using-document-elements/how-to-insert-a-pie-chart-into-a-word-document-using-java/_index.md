---
category: general
date: 2026-09-27
description: Lär dig hur du infogar ett cirkeldiagram i ett Word‑dokument med Java,
  skapar ett cirkeldiagram i Word och visar procentsatser på cirkeldiagrammet för
  tydlig datainsikt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: sv
lastmod: 2026-09-27
og_description: Hur du infogar ett cirkeldiagram i ett Word‑dokument med Java. Den
  här guiden visar hur du skapar ett cirkeldiagram i Word, visar procentandelar på
  diagrammet och lägger till förklaringslinjer.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Hur man infogar ett cirkeldiagram i ett Word‑dokument med Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Hur man infogar ett cirkeldiagram i ett Word-dokument med Java
url: /sv/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så här infogar du ett pie chart i ett Word-dokument med Java

Om du behöver **how to insert pie chart** i en Word‑fil, guidar den här artikeln dig genom hela processen. Du får se hur du **create pie chart in Word**, visar procentandelar på varje segment och lägger till leader lines för ett polerat utseende.

Word‑automatisering känns ofta tung, men med Aspose.Words för Java kan du generera fullt formaterade dokument programatiskt. I slutet av den här tutorialen har du ett körbart Java‑snutt som producerar ett Word‑dokument som innehåller ett stylat pie chart.

## Förutsättningar

Innan du börjar, se till att du har:

- Java 17 eller senare installerat
- Maven eller Gradle för att hantera beroenden
- Aspose.Words för Java (version 23.11 eller nyare) tillagt i ditt projekt
- Grundläggande kunskap om Java‑syntax

Du behöver ingen tidigare erfarenhet av chart‑API:er; stegen nedan täcker allt från projektuppsättning till slutresultat.

## Steg 1: Lägg till Maven‑beroendet

Lägg till Aspose.Words‑biblioteket i din `pom.xml`. Detta enda beroende ger dig åtkomst till `Document`, `DocumentBuilder` och chart‑klasser.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Om du använder Gradle är motsvarigheten:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Pro tip:** Använd den senaste stabila versionen för att dra nytta av buggfixar och nya chart‑funktioner.

## Steg 2: Skapa ett nytt dokument och en builder

`Document`‑objektet representerar Word‑filen, medan `DocumentBuilder` låter dig infoga innehåll. Detta är grunden för **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Buildern är nu redo att placera objekt var som helst i dokumentet.

## Steg 3: Infoga ett pie chart

Aspose.Words stöder flera diagramtyper; vi väljer `ChartType.PIE`. Storleken anges i punkter (1 point = 1/72 tum).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

I detta skede innehåller diagrammet en standard‑dataserie med platshållarvärden. Du kan ersätta dessa värden senare om så behövs.

## Steg 4: Åtkomst till diagramserien

Ett pie chart har en enda serie som innehåller segmentvärdena. Hämta den för att applicera formatering.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Steg 5: Explodera det första segmentet

Att explodera ett segment drar uppmärksamhet till en specifik datapunkt. Detta är en vanlig visuell ledtråd när du vill framhäva en nyckelmetrik.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Steg 6: Visa procentandelar på varje segment

Att visa procentandelar direkt på diagrammet förbättrar datainsikten. Detta uppfyller kravet **show percentages on pie chart**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Steg 7: Lägg till leader lines för tydligare etiketter

Leader lines kopplar segmentetiketter till deras motsvarande delar och eliminerar tvetydighet. Detta uppfyller **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Steg 8: Spara dokumentet

Till sist skriver du dokumentet till disk. Du kan välja vilken mapp du har skrivbehörighet till.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

När programmet körs skapas `output/PieFormatted.docx`. Öppna filen i Microsoft Word så ser du ett pie chart där:

- Det första segmentet är exploderat.
- Varje segment visar sitt procentvärde.
- Leader lines pekar från procenttalen till motsvarande segment.

### Förväntat resultat

![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image alt="Formaterat pajdiagram infogat i ett Word-dokument"}

Skärmdumpen (alt‑texten använder huvudnyckelordet) illustrerar det slutgiltiga utseendet: ett rent, datadrivet pie chart redo för rapporter, förslag eller dashboards.

## Vanliga variationer och kantfall

### Ändra segmentvärden

Om du behöver anpassade data, ersätt standardseriens värden:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Flera serier (donut‑diagram)

Medan ett enkelt pie chart har en serie, stöder Aspose.Words även donut‑diagram med flera serier. Byt `ChartType.PIE` till `ChartType.DONUT` och upprepa stegen för serie‑konfiguration.

### Exportera till PDF

Om ditt efterföljande arbetsflöde kräver PDF, anropa `doc.save("output/PieFormatted.pdf");` efter att diagrammet byggts. Den visuella layouten förblir identisk.

## Fullständig källkod

Nedan är den kompletta, fristående Java‑filen som du kan kopiera‑klistra in i din IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Kompilera och kör programmet med `mvn compile exec:java -Dexec.mainClass=PieChartExample` (eller motsvarande Gradle‑kommando). Den genererade Word‑filen kommer att innehålla det fullt formaterade pie chart.

## Slutsats

Du vet nu **how to insert pie chart** i ett Word‑dokument med Java, hur du **create pie chart in Word**, hur du **show percentages on pie chart**, och hur du **add chart to word document** med leader lines. Det kompletta exemplet demonstrerar varje steg, förklarar varför koden är skriven på det sättet och ger tips för anpassning.

Nästa steg kan vara att utforska:

- Lägga till datalabels med anpassade typsnitt (**show percentages on pie chart**‑variationer)
- Kombinera flera diagram i ett enda dokument (**add chart to word document**‑användningsfall)
- Automatisera rapportgenerering med tabeller och diagram tillsammans

Känn dig fri att experimentera med färger, segmentordning eller export till PDF. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

De följande tutorialerna täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}