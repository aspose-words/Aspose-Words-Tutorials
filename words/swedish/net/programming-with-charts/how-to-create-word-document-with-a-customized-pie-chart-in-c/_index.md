---
category: general
date: 2026-10-07
description: Lär dig hur du skapar ett Word‑dokument och infogar ett cirkeldiagram
  med Aspose.Words i C#. Guiden visar också hur du genererar en Word‑fil med anpassade
  diagrametiketter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: sv
lastmod: 2026-10-07
og_description: Skapa ett Word‑dokument och infoga ett cirkeldiagram i C#. Följ den
  här steg‑för‑steg‑guiden för att generera en Word‑fil med helt anpassade diagrametiketter.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Skapa ett Word‑dokument med ett anpassat cirkeldiagram i C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Hur man skapar ett Word‑dokument med ett anpassat cirkeldiagram i C#
url: /sv/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar Word-dokument med ett anpassat cirkeldiagram i C#

Om du behöver **skapa Word-dokument** programatiskt, visar den här handledningen hur du **infogar ett cirkeldiagram** och anpassar dess datalabels med hjälp av Aspose.Words för .NET. Du kommer också att lära dig hur du **genererar Word-fil** som innehåller ett fullt stylat diagram, och täcker allt från projektuppsättning till att spara det slutliga dokumentet.

Guiden går igenom varje steg som krävs för att lägga till ett diagram, justera labelpositioner, aktivera ledarlinjer och slutligen spara resultatet som en `.docx`-fil. Inga externa verktyg behövs utöver Aspose.Words-biblioteket, och den kompletta källkoden tillhandahålls så att du kan kopiera, klistra in och köra den omedelbart.

## Förutsättningar

* .NET 6.0 SDK eller senare installerat  
* En giltig Aspose.Words för .NET-licens (eller en gratis utvärderingsnyckel)  
* En IDE såsom Visual Studio 2022 eller Visual Studio Code  

Du måste också lägga till följande NuGet-paket i ditt projekt:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Dessa paket exponerar klasserna `Document`, `DocumentBuilder` och diagramrelaterade klasser som används i exemplen nedan.

## Skapa Word-dokument och lägg till ett diagram

Det första steget är att **skapa Word-dokument** och få en `DocumentBuilder` som låter dig infoga innehåll. Buildern fungerar som en markör placerad i dokumentet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document`-objektet representerar hela Word-filen, medan `DocumentBuilder` tillhandahåller metoder som `InsertChart` som placerar objekt direkt i dokumentflödet.

## Infoga cirkeldiagram i dokumentet

Nu när buildern är redo kan du **infoga ett cirkeldiagram** med en specifik storlek. Diagrammet läggs till på builderns aktuella position.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` returnerar ett `Chart`-objekt som du kan manipulera vidare. Exempeldatan skapar fyra segment som representerar kvartalsförsäljning.

## Anpassa datalabels för cirkeldiagram

För att göra diagrammet mer läsbart behöver du ofta **anpassa cirkeldiagrammets** etiketter—placera dem utanför segmenten och visa ledarlinjer. Det är här `ChartDataLabelCollection` kommer in i bilden.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Att sätta `Position` till `OutsideEnd` flyttar varje etikett bortom segmentets kant, medan `ShowLeaderLines` ritar en linje som kopplar etiketten till dess segment. De valfria flaggorna `ShowValue` och `ShowPercentage` ger läsarna både råa siffror och relativa procentsatser.

**Proffstips:** Om du behöver formatera etikettens teckensnitt, använd `dataLabels.Font` för att ange storlek, färg och stil. Detta säkerställer att diagrammet matchar ditt företags varumärke.

## Spara och generera Word-fil

När diagrammet är helt konfigurerat kan du **generera Word-fil** genom att spara `Document`-instansen till disk. Välj `.docx`-formatet för maximal kompatibilitet med moderna Word-versioner.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

När du öppnar `CustomPieChart.docx` kommer du att se ett cirkeldiagram med fyra segment, var och en etiketterad utanför segmentet, kopplad med ledarlinjer och som visar både värde och procentandel.

![Skärmdump av ett Word-dokument som innehåller ett anpassat cirkeldiagram skapat med C#](image-placeholder.png)

*Bilden visar det slutgiltiga resultatet av **skapa Word-dokument**-handledningen.*

## Vanliga variationer och kantfall

| Scenario | Hur man anpassar koden |
|----------|------------------------|
| **Multiple series** | Lägg till ytterligare `ChartSeries`-objekt till `pieChart.Series`. Varje serie kan ha sin egen `DataLabels`-samling för oberoende styling. |
| **Different chart size** | Ändra bredd- och höjdpunkterna i `InsertChart(width, height)`. Värdena är i punkter (1 pt ≈ 1/72 tum). |
| **Chart title** | Använd `pieChart.Title.Text = "Quarterly Sales"` för att lägga till en beskrivande titel. |
| **Export to PDF** | Anropa `document.Save("Report.pdf", SaveFormat.Pdf);` efter att diagrammet har byggts. |
| **License handling** | Placera din licensfil (`Aspose.Words.lic`) i applikationsmappen och ladda den med `new License().SetLicense("Aspose.Words.lic");` innan du skapar dokumentet. |

Dessa variationer låter dig svara på frågan **hur man lägger till cirkeldiagram** i många verkliga scenarier, från enkla rapporter till komplexa instrumentpaneler.

## Slutsats

Du vet nu hur man **skapar Word-dokument**, **infogar cirkeldiagram** och **anpassar cirkeldiagrammets** etiketter med Aspose.Words för .NET. Det kompletta exemplet visar ett rent arbetsflöde: initiera dokumentet, lägg till ett diagram, justera datalabelpositionering, aktivera ledarlinjer och slutligen **generera Word-fil** som kan delas med vem som helst.

Försök utöka den här handledningen genom att experimentera med olika diagramtyper (`ChartType.Column`, `ChartType.Line`) eller genom att tillämpa anpassade färgpaletter för att matcha ditt varumärke. Om du stöter på problem, konsultera Aspose.Words-dokumentationen eller utforska relaterade ämnen såsom “hur man lägger till cirkeldiagram” med flera serier och dynamiska datakällor.

Lycka till med kodandet, och dela gärna dina resultat eller ställ följdfrågor i kommentarerna!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga kolumndiagram i ett Word-dokument](/words/english/net/programming-with-charts/insert-column-chart/)
- [Infoga områdesdiagram i ett Word-dokument](/words/english/net/programming-with-charts/insert-area-chart/)
- [Infoga spridningsdiagram i Word-dokument](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}