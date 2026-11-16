---
category: general
date: 2026-11-15
description: Lär dig hur du skapar ett cirkeldiagram i ett Word‑dokument och sparar
  docx som PDF med Java. Denna guide täcker också hur man konverterar Word till PDF
  och hur man lägger till diagram.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: sv
lastmod: 2026-11-15
og_description: Skapa ett cirkeldiagram i en Word‑fil och spara docx som PDF med Java.
  Följ den här steg‑för‑steg‑handledningen för att konvertera Word till PDF och lägga
  till diagram.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Skapa ett cirkeldiagram i Word och spara docx som PDF – Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Hur man skapar ett cirkeldiagram i Word och sparar docx som PDF
url: /sv/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett cirkeldiagram i Word och sparar docx som PDF

Om du behöver **skapa ett cirkeldiagram** i ett Word‑dokument och sedan **spara docx som PDF**, visar den här handledningen exakt hur du gör. Du får se ett komplett, körbart exempel som konverterar en .docx‑fil till en PDF samtidigt som ett cirkeldiagram bäddas in, så att du kan svara på “hur man lägger till diagram” utan att leta efter spridda kodsnuttar.

I den här guiden lär du dig att:

* Ladda ett befintligt *.docx* (eller börja från början)  
* Använda Aspose.Words för Java för att **skapa ett cirkeldiagram** och fylla i data  
* **Spara docx som PDF** med diagrammet korrekt renderat  
* Förstå nyanserna i **convert word to pdf** när diagram är inblandade  

Stegen fungerar med Aspose.Words 2024‑x.x och Java 17, men koncepten gäller för alla bibliotek som stödjer Word‑diagrammanipulation.

## Förutsättningar

Innan du börjar, se till att du har:

| Krav | Varför det är viktigt |
|------|------------------------|
| Java 17 (eller senare) | Krävs av den senaste Aspose.Words JAR |
| Maven eller Gradle byggverktyg | Förenklar hantering av beroenden |
| Aspose.Words for Java (senaste version) | Tillhandahåller `Document`, `Chart` och `ChartType`‑klasser |
| En inmatnings‑**.docx**‑fil (eller ett tomt dokument) | Diagrammet kommer att infogas i den här filen |

Lägg till Aspose.Words‑beroendet i din `pom.xml` (Maven) eller `build.gradle` (Gradle). Exempel för Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Steg 1: Ladda Word-dokumentet (eller skapa ett nytt)

Den första åtgärden är att skapa en `Document`‑instans. Om du redan har en mall, ange dess sökväg; annars skapa ett tomt dokument.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Varför detta steg?* `Document`‑objektet är behållaren för allt Word‑innehåll, inklusive diagram. Att ladda en befintlig fil låter dig bevara omgivande text och format medan du lägger till ett nytt visuellt element.

## Steg 2: **Skapa cirkeldiagram** – kärnan i “how to create chart”

Nu instansierar vi ett `Chart`‑objekt med `ChartType.PIE`. Detta skapar automatiskt en platshållare för ett cirkeldiagram som du senare kan fylla med data.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Förklaring*: `ChartType.PIE` talar om för Aspose.Words att använda en cirkeldiagram‑mall. Diagrammet läggs till i dokumentets kropp, så det visas där du behöver det. Detta uppfyller kravet “how to add chart” i ett enda anrop.

## Steg 3: Fyll diagrammet – svarar på “how to add chart” med data

Ett cirkeldiagram är meningslöst utan seriedata. Använd `Series`‑samlingen för att lägga till kategorier och värden.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Varför detta är viktigt*: Varje anrop till `add` skapar en skiva i cirkeln. Det första argumentet är etiketten, det andra är det numeriska värdet. Du kan ersätta dessa med dynamisk data från en databas eller CSV‑fil.

### Valfritt: Anpassa utseende (inte obligatoriskt men användbart)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Dessa justeringar visar hur du kan **how to create chart** med ett professionellt utseende, utan att lämna Java‑koden.

## Steg 4: **Spara docx som PDF** – den sista delen av “convert word to pdf”

När diagrammet är infogat, exportera dokumentet till PDF. Aspose.Words renderar diagrammet som en vektorgrafik och bevarar kvaliteten.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Viktigt*: `save`‑metoden konverterar automatiskt Word‑filen till PDF, hanterar diagram‑rasterisering, teckensnittsinbäddning och sidlayout. Detta uppfyller målet **save docx as pdf** och demonstrerar ett pålitligt sätt att **convert word to pdf** när diagram finns med.

### Förväntat resultat

När programmet körs får du `output.pdf` som innehåller:

* Det ursprungliga innehållet i `input.docx` (om något)  
* Ett fullt renderat cirkeldiagram med rubriken *Sales Distribution Q1*  
* Exakta skivprocent som matchar data (40 %, 30 %, 30 %)

Öppna PDF‑filen i någon visare så bör du se ett skarpt cirkeldiagram, identiskt med vad du ser i Word‑filen.

## Vanliga fallgropar och hur man undviker dem

| Problem | Orsak | Lösning |
|---------|-------|---------|
| Diagrammet visas tomt i PDF | Teckensnitt eller diagramrenderingsinställningar saknas | Säkerställ att du använder den senaste Aspose.Words‑versionen; den innehåller nödvändiga renderingsbibliotek. |
| Datavärden avrundas felaktigt | Använder heltalsvärden med stora tal | Ange `double`‑värden eller skala siffrorna innan du lägger till dem i serien. |
| Utgående PDF är stor | Bilder inbäddade med hög DPI | Använd `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` om du också bäddar in bilder. |
| “convert word to pdf” kastar `UnsupportedOperationException` | Äldre Java‑version (< 11) | Uppgradera till Java 17 eller senare, vilket Aspose.Words 24.x kräver. |

## Proffstips: Återanvänd diagramskapande‑logiken

Om du behöver lägga till flera diagram i samma dokument, extrahera diagram‑byggkoden till en hjälpfunktion:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Nu kan du anropa `doc.getFirstSection().getBody().appendChild(createPieChart(...));` för varje dataset och hålla koden DRY (Don’t Repeat Yourself).

## Slutsats

Du vet nu hur du **skapar ett cirkeldiagram** i ett Word‑dokument, fyller det med data, och **sparar docx som PDF** med Java. Detta end‑to‑end‑exempel täcker hela **convert word to pdf**‑arbetsflödet, svarar på **how to add chart**, och demonstrerar **how to create chart** programatiskt.  

Härifrån kan du utforska:

* Att lägga till stapel‑ eller linjediagram (`ChartType.BAR`, `ChartType.LINE`) – ett annat **how to create chart**‑scenario.  
* Export till andra format som PNG eller HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Dynamisk generering av inmatningsdokumentet med tabeller eller platshållare innan du infogar diagram.

Känn dig fri att experimentera med olika dataset, stilalternativ eller till och med bädda in flera diagram per sida. Lycka till med kodningen!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närliggande ämnen som bygger på teknikerna i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man infogar ett cirkeldiagram i ett Word-dokument med Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Hur man sparar word som pdf och skapar en tillgänglig PDF i Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [Hur man skapar diagram i Word med Java och Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}