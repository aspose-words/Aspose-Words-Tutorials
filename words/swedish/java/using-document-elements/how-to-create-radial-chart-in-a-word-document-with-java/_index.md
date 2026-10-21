---
category: general
date: 2026-09-18
description: Lär dig hur du skapar ett radialdiagram i ett Word‑dokument med Java,
  lägger till diagrammets datamärkningar och infogar seriedata med ett komplett kodexempel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: sv
lastmod: 2026-09-18
og_description: Skapa ett radialdiagram i ett Word‑dokument med Java, lägg till diagrammets
  datamärkningar och infoga seriedata i en enda handledning.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Skapa radialdiagram i Word med Java – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Hur man skapar ett radialdiagram i ett Word‑dokument med Java
url: /sv/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du ett radialdiagram i ett Word‑dokument med Java

Om du behöver skapa ett radialdiagram i ett Word‑dokument visar den här guiden dig de exakta stegen. Du kommer också att lära dig hur du lägger till diagrammets datamärkningar och infogar seriedata så att diagrammet är redo för presentation.

Att generera ett diagram programatiskt tar bort manuellt formateringsarbete och garanterar konsekvens över rapporter. Handledningen förutsätter att du har grundläggande kunskaper i Java och en aktuell version av Aspose.Words for Java‑biblioteket installerat.

## Vad du behöver

* Java 17 eller nyare  
* Aspose.Words for Java (version 23.12 eller senare)  
* En IDE eller ett byggverktyg som kan lösa Maven/Gradle‑beroenden  

Att ha dessa förutsättningar installerade låter dig köra exemplet utan ytterligare konfiguration.

## Så skapar du ett radialdiagram i ett Word‑dokument

Det första steget är att skapa en tom Word‑fil som ska innehålla diagrammet. Ett tomt dokument ger en ren canvas och undviker oönskade stilar.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` representerar hela .docx‑filen, medan `DocumentBuilder` tillhandahåller metoder för att infoga element såsom stycken, tabeller och diagram.

## Så infogar du diagrammet

Nästa steg är att infoga själva diagrammet. Metoden `insertChart` skapar ett diagramobjekt och placerar det på builderns aktuella markörposition.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Ett polärt diagram renderar datapunkter runt en central axel, vilket är idealiskt för att visa cyklisk information. Dimensionerna uttrycks i punkter (1 pt ≈ 1/72 tum).

## Lägg till seriedata i diagrammet

Ett diagram utan seriedata är tomt. Du kan lägga till en serie manuellt eller binda den till en datakälla. Exemplet nedan lägger till en enda serie med tre datapunkter.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` tar emot ett serienamn, en lista med kategorimärkningar och en lista med motsvarande numeriska värden. Du kan upprepa detta block för att lägga till ytterligare serier (`addSeriesData`).

## Lägg till diagrammets datamärkningar för den första serien

Datamärkningar gör diagrammet läsbart utan att behöva hovra över punkterna. Följande rad slår på värdemärkningar för den första serien.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Genom att sätta `showValue` till `true` visas varje punkts värde direkt på diagrammet. Du kan också aktivera kategorinamn, procenttal eller ledarlinjer via samma `DataLabelFormat`‑objekt.

## Spara Word‑filen

När diagrammet är konfigurerat, skriv dokumentet till disk. Välj en plats som din applikation kan komma åt.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Filen `RadialChart.docx` innehåller nu ett fullt fungerande radialdiagram med datamärkningar.

## Fullt fungerande exempel

Nedan finns ett självständigt program som du kan kopiera, kompilera och köra. Det demonstrerar hela arbetsflödet från att skapa ett tomt Word‑dokument till att spara ett radialdiagram med datamärkningar.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Förväntat resultat**

När du öppnar `output/RadialChart.docx` i Microsoft Word kommer du att se ett radialdiagram med rubriken *Quarterly Sales*. Varje punkt visar sitt numeriska värde (t.ex. “15000”) bredvid markören.

## Vanliga variationer och kantfall

| Situation | Rekommenderad ändring |
|-----------|-----------------------|
| Du behöver en annan diagramtyp | Byt ut `ChartType.POLAR` mot någon annan `ChartType`‑enum‑värde (t.ex. `ChartType.COLUMN`). |
| Diagrammet måste använda ett externt Excel‑område | Använd `chart.setDataRange("Sheet1!A1:B5")` efter att diagrammet har skapats och arbetsboken har laddats. |
| Du vill dölja förklaringen | `chart.getLegend().setVisible(false);` |
| Dokumentet måste sparas som PDF | Anropa `doc.save("RadialChart.pdf");` – Aspose.Words konverterar automatiskt diagrammet. |

Dessa justeringar behåller kärnlogiken intakt samtidigt som de anpassar resultatet till specifika krav.

## Proffstips

* **Återanvänd buildern** – Du kan infoga flera diagram i samma dokument genom att anropa `builder.insertChart` upprepade gånger.  
* **Prestanda** – När du genererar många diagram, skapa en enda `DocumentBuilder`‑instans och återanvänd den för att minska minnesallokeringen.  
* **Styling** – Diagrammets utseende (färger, linjetjocklek) styrs via `Chart`‑objektets `getSeries().get(i).getFormat()`‑metoder. Experimentera med dessa inställningar för att matcha företagets varumärke.

## Slutsats

Du vet nu hur du skapar ett radialdiagram i ett Word‑dokument med Java, lägger till seriedata och diagrammets datamärkningar innan du sparar filen. Det kompletta exemplet kan utökas för att hantera ytterligare serier, anpassade stilar eller alternativa utdataformat.

Utforska relaterade ämnen såsom **how to insert chart** från externa datakällor, **create blank word**‑dokument med fördefinierade mallar och **add series data** dynamiskt från databaser. Experimentera med olika diagramtyper för att upptäcka vilken visualisering som bäst kommunicerar dina data.

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}