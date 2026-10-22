---
category: general
date: 2026-10-13
description: Ställ in antalet histogramklasser i ett Word‑diagram med C# och lägg
  till datamärkningar för att förbättra läsbarheten. Lär dig hur du laddar ett Word‑dokument
  med C# och uppdaterar diagrammet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set histogram bin count
- add data labels histogram
- how to update word chart
- enable chart data labels
- load word document c#
language: sv
lastmod: 2026-10-13
og_description: Ställ in antalet staplar i ett histogram i ett Word‑diagram med C#
  och aktivera datamärkningar för tydligare visuell data. Följ den här kompletta handledningen
  för att ladda ett Word‑dokument med C# och uppdatera diagrammet.
og_image_alt: Screenshot of a Word histogram chart after setting bin count and enabling
  data labels
og_title: Ställ in antalet histogramintervall i Word-diagram med C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Set histogram bin count in a Word chart with C# and add data labels
    to improve readability. Learn how to load a Word document C# and update the chart.
  headline: How to set histogram bin count and add data labels in a Word chart using
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart manipulation
title: Hur man ställer in antalet bin i ett histogram och lägger till datamärkningar
  i ett Word-diagram med C#
url: /sv/net/programming-with-charts/how-to-set-histogram-bin-count-and-add-data-labels-in-a-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man ställer in histogrammets bin-antal och lägger till datamärkningar i ett Word-diagram med C#

Om du behöver **ställa in histogrammets bin-antal** i ett Word-diagram visar den här guiden hur du gör det med C#. Du kommer också att lära dig hur du **lägger till datamärkningar i histogrammet** så att varje bin visar sitt värde, vilket gör diagrammet lättare att läsa. Lösningen fungerar med alla `.docx`‑filer som innehåller ett histogramdiagram och använder Aspose.Words för .NET‑biblioteket.

Att uppdatera ett diagram är en vanlig uppgift när du genererar rapporter automatiskt. I slutet av den här handledningen kommer du att kunna **ladda Word-dokument C#**, ändra histogrammets bin-antal, slå på datamärkningar och spara resultatet utan manuell redigering.

## Vad du kommer att lära dig

* Hur man laddar ett Word-dokument i C# (`load word document c#`).
* Hur man hittar det första histogramdiagrammet i dokumentet (`how to update word chart`).
* De exakta stegen för att **ställa in histogrammets bin-antal** och **aktivera diagrammets datamärkningar**.
* Tips för att hantera flera diagram, olika diagramtyper och vanliga fallgropar.

## Förutsättningar

| Krav | Varför det är viktigt |
|------|-----------------------|
| .NET 6.0 eller senare | Tillhandahåller runtime för Aspose.Words. |
| Aspose.Words for .NET (v23.9 eller nyare) | Erbjuder `Chart`‑API:t som används för att modifiera Word‑diagram. |
| En Word‑fil (`input.docx`) som innehåller ett histogramdiagram | Koden fungerar på ett befintligt histogram; du kan skapa ett manuellt i Word för testning. |
| Visual Studio 2022 (eller någon C#‑IDE) | Gör det enkelt att kompilera och köra exemplet. |

Installera NuGet‑paketet med följande kommando:

```bash
dotnet add package Aspose.Words
```

> **Proffstips:** Om du planerar att bearbeta många dokument, aktivera Aspose.Words‑licensen för att ta bort utvärderingsvattenmärken.

## Steg 1: Ladda Word-dokumentet (load word document c#)

Den första operationen är att öppna `.docx`‑filen som innehåller histogrammet. Genom att använda `Document.Load` säkerställs att alla dokumentdelar, inklusive diagram, är tillgängliga i minnet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Path to the source document
string inputPath = @"C:\Docs\input.docx";

// Load the Word document
Document doc = new Document(inputPath);
```

> **Varför detta steg är viktigt:** Att ladda dokumentet är grunden för alla modifieringar. Om filen inte kan öppnas kommer efterföljande steg att misslyckas med ett `FileNotFoundException`.

## Steg 2: Hitta histogramdiagrammet (how to update word chart)

Word lagrar diagram som `Shape`‑noder. Vi måste hitta den första formen och kasta den till `Chart`. Om ditt dokument innehåller flera diagram kan du iterera över alla former och inspektera `chart.ChartType`.

```csharp
// Retrieve the first shape in the document (depth‑first search)
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Ensure the shape really is a chart
if (shape?.Chart == null)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Cast the shape to a Chart object
Chart histogramChart = shape.Chart;
```

> **Edge case:** Om dokumentet inte innehåller ett diagram returnerar `GetChild` `null`. Kontrolleringen ovan förhindrar ett `NullReferenceException`.

## Steg 3: Ställ in histogrammets bin-antal (set histogram bin count)

Ett histograms visuella granularitet styrs av egenskapen `BinCount`. Att sätta den till ett högre värde skapar fler staplar, vilket kan avslöja en finare datadistribution.

```csharp
// Verify that the chart is a histogram
if (histogramChart.ChartType != ChartType.Histogram)
{
    throw new InvalidOperationException("The selected chart is not a histogram.");
}

// Set the desired number of bins (e.g., 15)
histogramChart.HistogramChart.BinCount = 15;
```

> **Varför du behöver detta:** Att justera bin‑antalet låter dig anpassa diagrammet för målgruppen. Ett litet bin‑antal förenklar vyn, medan ett större antal ger mer detaljer.

## Steg 4: Aktivera diagrammets datamärkningar (add data labels histogram / enable chart data labels)

Datamärkningar gör varje bins värde synligt direkt på diagrammet. Detta är särskilt användbart när histogrammet skrivs ut eller exporteras till PDF.

```csharp
// Turn on data labels for each bin
histogramChart.HistogramChart.ShowLabels = true;

// Optional: customize label format (e.g., show percentage)
histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";
```

> **Praktiskt tips:** Om du föredrar procent istället för råa räknare, sätt `NumberFormat = "0%"` och justera `ShowPercentage = true`.

## Steg 5: Spara det modifierade dokumentet

Efter ändringarna skrivs dokumentet tillbaka till disk. Du kan skriva över originalfilen eller skapa en ny.

```csharp
// Path to the output document
string outputPath = @"C:\Docs\output.docx";

// Save the updated document
doc.Save(outputPath);
```

När du öppnar `output.docx` i Microsoft Word visas nu ett histogram med 15 bin och synliga datamärkningar.

## Steg 6: Verifiera resultatet (förväntad output)

För att säkerställa att operationen lyckades utan visuell inspektion kan du programatiskt läsa tillbaka egenskaperna:

```csharp
// Reload the saved file for verification
Document verifyDoc = new Document(outputPath);
Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
```

Konsolen bör visa:

```
BinCount: 15
ShowLabels: True
```

Om värdena matchar har histogrammet uppdaterats korrekt.

## Fullt körbart exempel

När allt sätts ihop är här ett fristående program som du kan kopiera, klistra in och köra:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // ---------- Step 2: Locate the histogram chart ----------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape?.Chart == null)
            throw new InvalidOperationException("No chart found in the document.");

        Chart histogramChart = shape.Chart;

        // ---------- Step 3: Set histogram bin count ----------
        if (histogramChart.ChartType != ChartType.Histogram)
            throw new InvalidOperationException("The chart is not a histogram.");

        histogramChart.HistogramChart.BinCount = 15;

        // ---------- Step 4: Enable chart data labels ----------
        histogramChart.HistogramChart.ShowLabels = true;
        histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";

        // ---------- Step 5: Save the modified document ----------
        string outputPath = @"C:\Docs\output.docx";
        doc.Save(outputPath);

        // ---------- Step 6: Verify the changes ----------
        Document verifyDoc = new Document(outputPath);
        Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

        Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
        Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
    }
}
```

Kör programmet och öppna sedan `output.docx` för att se det uppdaterade histogrammet.

## Vanliga frågor och edge cases

| Fråga | Svar |
|-------|------|
| **Vad händer om dokumentet innehåller mer än ett diagram?** | Använd `doc.GetChildNodes(NodeType.Shape, true)` för att hämta en samling, iterera sedan och kontrollera varje `Chart.ChartType`. |
| **Kan jag ändra bin‑bredden istället för antalet?** | Ja. Använd `histogramChart.HistogramChart.BinWidth` för att ange en fast bredd; inställning av `BinCount` kommer att ignoreras. |
| **Är API:et kompatibelt med .NET Core?** | Aspose.Words for .NET stödjer .NET Core, .NET 5+ och .NET Framework. Samma kod fungerar på alla stödda runtime‑miljöer. |
| **Hur döljer jag legenden efter att ha lagt till märken?** | Sätt `histogramChart.Legend.Visible = false;`. Detta håller diagrammet rent när märkena redan förmedlar datan. |

## Slutsats

Du vet nu hur du **ställer in histogrammets bin-antal** och **lägger till datamärkningar** i ett Word-diagram med C#. Genom att ladda dokumentet, hitta histogrammet, justera `BinCount`, aktivera `ShowLabels` och spara filen kan du automatisera diagramuppdateringar i vilken rapporteringspipeline som helst.  

Härifrån kan du utforska:

* **how to update word chart** färger och stilar,
* **enable chart data labels** för andra diagramtyper (cirkeldiagram, stapeldiagram, linjediagram),
* Generera diagram från rådata med Aspose.Words eller Aspose.Cells,
* Bädda in det uppdaterade dokumentet i en PDF med Aspose.PDF.

Experimentera med olika bin‑antal och märkningsformat för att hitta den visuella balansen som bäst tjänar din publik. Lycka till med kodandet!  

![Word-histogram efter

## Vad du bör lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Uppdatera diagramseriedata i ett Word-dokument med Aspose.Words för .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Ställ in enhetliga datamärkningar i ett stapeldiagram med Aspose.Words för .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Ställ in standardalternativ för datamärkningar i ett diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}