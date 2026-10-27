---
category: general
date: 2026-10-26
description: Skapa doughnut‑diagram och infoga cirkeldiagram i Java med steg‑för‑steg‑kod.
  Lär dig hela arbetsflödet för flexibla diagramvisualiseringar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: sv
lastmod: 2026-10-26
og_description: Skapa donutdiagram i Java med den här guiden som också visar hur du
  infogar ett pajdiagram för flexibla visualiseringar.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Skapa donutdiagram och infoga cirkeldiagram – Java‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Hur man skapar ett donutdiagram och infogar ett cirkeldiagram
url: /sv/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du ett doughnut-diagram och infogar ett pie-diagram

Om du behöver **create doughnut chart** i Java, guidar den här handledningen dig genom de exakta stegen. Vi visar också hur du **insert pie chart** med samma builder‑API, så att du enkelt kan växla mellan visuella stilar. I slutet av guiden har du ett komplett, körbart program som producerar båda diagramtyperna och demonstrerar vanliga anpassningar.

Handledningen täcker:

* Initiera chart builder som tillhandahålls av det valda biblioteket.  
* Skapa ett doughnut-diagram och konfigurera hålstorleken.  
* Infoga ett pie-diagram och explodera en skiva för att framhäva den.  
* Tips för att hantera edge cases såsom saknade serier eller ej stödjade diagramtyper.

Du behöver bara en aktuell JDK (8 eller senare) och chart‑bibliotekets JAR på din classpath. Inga externa tjänster krävs.

---

## Förutsättningar

| Objekt | Orsak |
|------|--------|
| Java Development Kit (JDK) 8+ | Krävs för att kompilera och köra exemplet. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | Tillhandahåller `ChartBuilder`, `ChartType` och metoder för serie‑manipulation som används i koden. |
| An IDE or a text editor | För att skriva och köra Java‑källfilen. |

Se till att bibliotekets JAR läggs till i ditt projekts build‑path. Om du använder Maven, lägg till rätt dependency; annars placera JAR‑filen i `libs`‑mappen och referera till den vid kompilering.

## Steg 1: Ställ in chart builder

Det första steget är att skapa en `ChartBuilder`‑instans (eller motsvarande) som kommer att generera diagramobjekten. Detta objekt fungerar som en fabrik och innehåller arbetsbladet eller canvas där diagrammet kommer att placeras.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Varför detta är viktigt:**  
Buildern kopplar diagrammet till ett specifikt arbetsblad, vilket säkerställer att alla efterföljande diagramobjekt delar samma ritningsyta. Att hoppa över detta steg skulle lämna dig utan en målplats för de visuella elementen.

## Steg 2: **Create doughnut chart**

Nu genererar vi ett doughnut-diagram med en definierad storlek. Hålstorleken bestämmer hur mycket av diagrammets centrum som är tomt, vilket förvandlar en vanlig pie till ett doughnut.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Förklaring:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` skapar diagramobjektet och reserverar utrymme på arbetsbladet.  
* `setHoleSize(30)` omvandlar pie‑diagrammet till ett doughnut med 30 % tomt centrum.  
* `add("{10, 20, 30, 40}", true)` tillhandahåller fyra datapunkter; flaggan `true` talar om för biblioteket att behandla värdena som en enda serie.

**Edge case:** Om den valda diagramtypen inte stödjer ett hål (t.ex. ett stapeldiagram) kastar ett anrop till `getDoughnutChart()` ett undantag. Verifiera alltid diagramtypen innan du justerar hålstorleken.

## Steg 3: **Insert pie chart**

När doughnut‑diagrammet är klart demonstrerar vi hur man **insert pie chart** med samma builder. Detta steg belyser likheten mellan de två diagramtyperna och visar hur man framhäver en skiva.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Förklaring:**  

* `ChartType.PIE` instruerar buildern att skapa ett klassiskt pie‑diagram.  
* `setExplode(10)` förskjuter den första skivan med 10 % av radien, en vanlig teknik för att framhäva en viktig datapunkt.  

**Tips:** `setExplode`‑metoden fungerar endast på den första serien i ett pie‑diagram. Om du har flera serier måste du rikta in dig på rätt index.

## Steg 4: Spara arbetsboken

Slutligen skriver du arbetsboken till en fil så att du kan visa diagrammen i Excel eller någon kompatibel visare.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Varför spara nu:** Att spara arbetsboken persisterar alla ritningsoperationer. Att försöka visa filen innan den sparas resulterar i ett tomt eller ofullständigt dokument.

**Resultat:** När du öppnar *DoughnutAndPieChart.xlsx* visas ett doughnut‑diagram med 30 % hål till vänster och ett pie‑diagram med en exploderad första skiva till höger.

## Steg 5: Vanliga variationer och felsökning

| Situation | Justering |
|-----------|------------|
| **Different chart dimensions** | Ändra bredd‑ och höjduppgifterna i `insertChart`. |
| **Multiple data series** | Anropa `add` flera gånger eller skicka en 2‑D‑array‑sträng. |
| **Dynamic hole size** | Beräkna hålstorleken baserat på dataintervall och anropa sedan `setHoleSize`. |
| **Explode multiple slices** | Loopa genom `chart.getSeries().get(i).setExplode(percent)` för varje skiva du vill förskjuta. |
| **Library not supporting doughnut** | Använd ett pie‑diagram och rita manuellt ett vitt cirkel‑overlay, även om detta är mindre exakt. |

**Pro tip:** Anropa alltid `builder.flush()` (om tillgängligt) efter att ha infogat diagram när du arbetar med stora arbetsböcker. Detta frigör interna buffertar och förhindrar minnesläckor.

![Java‑kod som skapar ett doughnut‑diagram och infogar ett pie‑diagram](https://example.com/images/doughnut-pie-java.png "exempel på att skapa doughnut‑diagram i Java")

*Bilden illustrerar den slutgiltiga arbetsbokslayouten med båda diagrammen sida vid sida.*

## Slutsats

Du vet nu hur du **create doughnut chart** och **insert pie chart** i Java med ett flytande builder‑API. Det fullständiga exemplet täcker initiering, storlekskonfiguration, hålstorlek, skivexplosion och filutmatning. Härifrån kan du utforska ytterligare anpassningar såsom färger, legender och datalabels för att matcha dina rapporteringsbehov.

**Nästa steg**

* Experimentera med **chart customization Java**‑funktioner som gradientfyllningar och datalabels.  
* Integrera diagramgenereringen i en webbtjänst som returnerar arbetsboken på begäran.  
* Jämför builder‑metoden med andra bibliotek (t.ex. JFreeChart) för att välja den bästa lösningen för ditt projekt.

Lycka till med diagrammen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man skapar doughnut‑diagram i ett Word‑dokument med Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Spara Word‑dokument efter redigering av doughnut‑diagram i Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Infoga pie‑diagram i Java – Explodera, rotera och markera skivor](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}