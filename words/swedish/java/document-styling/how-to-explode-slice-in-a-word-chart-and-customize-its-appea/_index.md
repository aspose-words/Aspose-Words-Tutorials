---
category: general
date: 2026-10-04
description: Lär dig hur du exploderar ett segment i ett Word‑diagram, exploderar
  ett pajdiagramsegment och ändrar storleken på ett donutdiagram med ett steg‑för‑steg
  Java‑exempel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: sv
lastmod: 2026-10-04
og_description: Hur man spränger ut en del i ett Word-diagram och anpassar cirkel-
  eller donutdiagram med Java. Följ det kompletta exemplet för att modifiera diagram
  i Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Hur man spränger ut en del i ett Word-diagram – fullständig Java-guide
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
title: Hur du drar ut en del i ett Word-diagram och anpassar dess utseende
url: /sv/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man exploderar en del i ett Word‑diagram och anpassar dess utseende

Om du behöver **how to explode slice** i ett Word‑diagram, visar den här guiden exakt hur. Oavsett om du förbereder en försäljningspresentation eller en finansiell rapport, kan det att explodera en paj‑diagramdel eller justera ett doughnut‑hål få den viktigaste datan att sticka ut. I följande avsnitt kommer du också att lära dig hur du **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, och **customize pie chart word** dokument med Aspose.Words for Java.

Du avslutar den här handledningen med ett komplett, färdigt‑att‑köra Java‑program som laddar en `.docx`‑fil, exploderar den första delen av ett paj‑diagram, ändrar storleken på doughnut‑hålet och sparar resultatet. Inga externa skript eller manuell redigering krävs.

## Förutsättningar

- Java 17 eller senare installerat på din utvecklingsmaskin.  
- Maven 3.6+ (eller Gradle) för att hantera beroenden.  
- Aspose.Words for Java‑biblioteket (gratis provversion fungerar för utveckling).  
- Ett Word‑dokument (`input.docx`) som innehåller minst ett diagram (pie eller doughnut).

## Steg 1: Lägg till Aspose.Words i ditt projekt

Om du använder Maven, lägg till följande beroende i din `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

För Gradle, placera detta i `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Håll ditt biblioteks version uppdaterad; nyare releaser lägger till stöd för ytterligare diagramtyper och förbättrar prestanda.

## Steg 2: Ladda Word‑dokumentet som innehåller ett diagram

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Varför detta är viktigt:** Att ladda dokumentet skapar en in‑memory‑representation som Aspose.Words kan traversera. Utan detta objekt kan du inte komma åt diagram‑noderna.

## Steg 3: Hämta det första diagrammet i dokumentet

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Förklaring:** `NodeType.SHAPE` täcker alla ritobjekt, inklusive diagram. Argumentet `true` talar om för Aspose att söka rekursivt, vilket säkerställer att det första diagrammet hittas även om det är inbäddat i en tabell.

## Steg 4: Explodera den första delen av ett paj‑diagram

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Hur det fungerar:** Metoden `setExplosion` tar ett numeriskt värde som bestämmer hur långt delen flyttas bort från centrum. Ett värde på `20` är visuellt märkbart utan att bryta diagrammets layout.

## Steg 5: Justera storleken på doughnut‑hålet för ett doughnut‑diagram

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Varför detta hjälper:** Ett större doughnut‑hål kan förbättra läsbarheten när du har många datapunkter. Metoden `setDoughnutHoleSize` förväntar sig en procentandel (0‑100).

## Steg 6: Spara det modifierade dokumentet

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Förväntat resultat

- Den första delen av det första paj‑diagrammet förskjuts utåt, vilket får den att sticka ut.
- Om diagrammet är ett doughnut, expanderar det centrala hålet till 40 % av diagrammets radie.
- Den resulterande filen `PieChart.docx` kan öppnas i Microsoft Word, LibreOffice eller någon kompatibel visare, och visar de visuella förändringarna du applicerat programatiskt.

## Fullt, körbart exempel

Nedan är hela programmet i ett block. Kopiera det till `ChartExploder.java`, justera filsökvägarna och kör det med `mvn compile exec:java` (eller din IDE:s körkonfiguration).

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

Att köra den här koden kommer automatiskt att **modify chart in Word**, **explode pie chart slice**, och **change doughnut chart size**.

## Vanliga frågor och specialfall

| Question | Answer |
|----------|--------|
| *Vad händer om dokumentet innehåller flera diagram?* | Exemplet riktar sig mot det **första** diagrammet (`NodeType.SHAPE, 0`). För att arbeta med andra diagram, ändra indexet eller iterera genom `doc.getChildNodes(NodeType.SHAPE, true)` och filtrera på `shape.getChart() != null`. |
| *Kan jag explodera en annan del än den första?* | Ja. Åtkomst till önskad serie via `chart.getSeries().get(seriesIndex)` och anropa `setExplosion(value)`. Index är noll‑baserade. |
| *Fungerar detta med Word 2007‑2021‑filer?* | Aspose.Words stöder `.doc`, `.docx`, `.dot` och `.dotx`. Samma kod fungerar över versioner eftersom biblioteket abstraherar filformatet. |
| *Vad händer om diagrammet är ett stapel‑ eller linjediagram?* | `setExplosion` och `setDoughnutHoleSize` är endast tillämpliga på paj‑typ diagram. Koden hoppar säkert över dessa operationer när diagramtypen är annorlunda. |
| *Behöver jag en licens för Aspose.Words?* | En gratis utvärderingslicens tar bort 30‑dagarsgränsen men lägger till ett vattenmärke. För produktion, köp en licens för att ta bort vattenmärket och låsa upp full funktionalitet. |

## Slutsats

Du vet nu **how to explode slice** i ett Word‑diagram, hur du **modify chart in Word**, och hur du **change doughnut chart size** med Aspose.Words for Java. Det kompletta exemplet demonstrerar hela arbetsflödet — från att ladda ett dokument, lokalisera diagrammet, applicera visuella justeringar, till att spara resultatet — så att du kan integrera dessa steg i vilken rapport‑ eller dokumentgenereringspipeline som helst.

**Nästa steg**

- Utforska andra diagramanpassningar såsom att ändra färger, lägga till datalabels eller byta diagramtyp (`chart.setChartType(ChartType.BAR_CLUSTERED)`).
- Kombinera denna logik med Aspose.PDF för att generera en PDF‑version av samma rapport.
- Automatisera processen för en mängd dokument genom att loopa över filer i en katalog.

Känn dig fri att experimentera med olika explosion‑värden eller doughnut‑hålsprocent för att matcha dina designriktlinjer. Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man skapar stapeldiagram med Aspose.Words för Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Dölj diagramaxel i ett Word‑dokument](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Infoga bubbeldiagram i Word‑dokument](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}