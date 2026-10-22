---
category: general
date: 2026-09-21
description: Hur man formaterar serier i ett Word-linjediagram med C#. Lär dig att
  skapa ett Word-dokument, infoga ett linjediagram och tillämpa ett anpassat talformat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: sv
lastmod: 2026-09-21
og_description: Hur man formaterar serier i ett Word‑linjediagram med C#. Denna handledning
  visar hur du skapar ett Word‑dokument, infogar ett linjediagram och tillämpar ett
  anpassat talformat.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Hur man formaterar serier i ett Word‑linjediagram med C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Hur man formaterar serier i ett Word‑linjediagram med C#
url: /sv/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man formaterar serier i ett Word‑linjediagram med C#

Om du behöver **formatera serier** i ett Word‑linjediagram, ger den här guiden en komplett, färdig‑körbar lösning. Du kommer att se hur du **skapar ett Word‑dokument**, **infogar linjediagram**, och **tillämpa anpassat talformat** på Y‑värdena — allt med Aspose.Words för .NET.

Word‑automation blir enkel när du förstår diagrammets objektmodell. I slutet av den här handledningen har du en Word‑fil som innehåller ett linjediagram vars dataserier visas som procent med två decimaler.

## Vad du kommer att uppnå

* Generera en tom `.docx`‑fil programatiskt.  
* Lägg till ett linjediagram med storleken 400 × 300 punkter.  
* Åtkomst till diagrammets första dataserie.  
* Tillämpa formatkoden `#,##0.00%` så att Y‑värdena visas som procent.  

Inga externa verktyg krävs utöver Aspose.Words NuGet‑paketet.

## Förutsättningar

* .NET 6.0 SDK eller senare.  
* Visual Studio 2022 (eller någon C#‑IDE).  
* Aspose.Words för .NET 23.10 eller nyare – installera via `dotnet add package Aspose.Words`.  

Koden fungerar på Windows, Linux och macOS eftersom Aspose.Words är plattforms‑agnostisk.

## Skapa ett Word‑dokument med Aspose.Words

Det första steget är att instansiera ett `Document`‑objekt. Detta objekt representerar hela Word‑filen i minnet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Why this matters*: `Document` är ingångspunkten för alla Word‑behandlingsoperationer. Utan den kan du inte lägga till stycken, tabeller eller diagram.

## Infoga linjediagram i dokumentet

En `DocumentBuilder` skriver innehåll i `Document`. Anropet `InsertChart` skapar en diagramform på den aktuella sidan.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Why this matters*: `InsertChart` returnerar ett `Chart`‑objekt som ger dig full kontroll över serier, axlar och formatering. Storleksparametrarna uttrycks i punkter (1 punkt = 1/72 tum).

## Åtkomst till den första dataserien

Varje diagram innehåller en eller flera `ChartSeries`. Den första serien har index 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Why this matters*: `ChartSeries`‑objektet innehåller Y‑värden, X‑värden och formateringsalternativ för en enskild linje i ett linjediagram. Att modifiera detta objekt ändrar den visuella representationen av data.

## Tillämpa ett anpassat talformat på serien

`FormatCode`‑egenskapen styr hur numeriska värden visas. Att sätta den till `#,##0.00%` talar om för Word att behandla värdena som procent med två decimaler.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Why this matters*: Utan ett anpassat format visar Word råa decimaltal (t.ex. `0.15`). Formatkoden konverterar dem till `15.00%`, vilket ofta krävs i affärsrapporter.

## Spara dokumentet och verifiera resultatet

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

När du öppnar `FormattedSeriesLineChart.docx` i Microsoft Word kommer du att se ett linjediagram där Y‑axelns etiketter visar `15.00%`, `30.00%`, `45.00%` och `60.00%`. Diagrammets storlek matchar de dimensioner som angavs i `InsertChart`.

### Förväntad skärmbild

> *Image: En Word‑dokument sida som visar ett linjediagram med procent‑formaterade Y‑axelvärden.*  
> *(Alt text: Skärmbild av ett Word‑dokument som visar ett linjediagram med procent‑formaterade Y‑axelvärden)*

## Vanliga variationer och kantfall

| Situation | Justering |
|-----------|------------|
| **Flera serier** | Loopa igenom `chart.Series` och sätt `FormatCode` för varje serie. |
| **Olika diagramtyp** | Ersätt `ChartType.Line` med `ChartType.Column`, `ChartType.Pie` osv. |
| **Locale‑specifika avgränsare** | Använd `CultureInfo`‑medvetna formatsträngar, t.ex. `"# ##0,00 %"` för franska locale. |
| **Dynamisk datakälla** | Fyll `series.YValues` från en databas eller CSV‑fil innan du tillämpar formatet. |

**Pro tip:** Applicera alltid formatet **efter** att du har lagt till Y‑värdena. Att ändra formatet först och sedan lägga till värden fungerar också, men att göra det senare garanterar att formatet tillämpas på den slutgiltiga datamängden.

## Sammanfattning

Du vet nu **hur man formaterar serier** i ett Word‑linjediagram med C#. Handledningen täckte:

* Skapa ett Word‑dokument (`create word document`).  
* Infoga ett linjediagram (`insert line chart`, `add chart to word`).  
* Åtkomst till diagrammets första serie.  
* Tillämpa ett anpassat talformat (`apply custom number format`) för att visa procent.

## Nästa steg

* Experimentera med olika `ChartType`‑värden för att se hur andra visualiseringar beter sig.  
* Lägg till titlar, axelrubriker och förklaringar med `chart.Title`, `chart.AxisX.Title` och `chart.AxisY.Title`.  
* Exportera diagrammet som en bild (`chart.Save` med `SaveFormat.Png`) för användning i webb‑rapporter.

Känn dig fri att anpassa detta mönster för att generera instrumentpaneler, finansiella rapporter eller vilket dokument som helst som behöver programmatisk diagramgenerering. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}