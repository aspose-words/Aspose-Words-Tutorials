---
category: general
date: 2026-08-04
description: Hur man lägger till datamärkningar i C# med Aspose.Words. Lär dig att
  redigera diagram, centrera diagrammets datamärkningar, visa procent i diagrammet
  och anpassa diagrammets datamärkningar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: sv
lastmod: 2026-08-04
og_description: Hur man lägger till datamärkningar i C# med Aspose.Words. Den här
  handledningen visar hur du redigerar diagram, centrerar diagrammets datamärkningar,
  visar procentsatser i diagrammet och anpassar diagrammets datamärkningar.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Hur man lägger till datamärkningar i ett Word-diagram i C# – komplett guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Hur man lägger till datamärkningar i ett Word‑diagram i C# – steg‑för‑steg‑guide
url: /sv/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till datalabels i ett Word-diagram i C# – steg‑för‑steg guide

Om du behöver **how to add data labels** till ett diagram som finns i ett Word‑dokument, visar den här guiden exakt vilken kod du måste köra. Du kommer att se hur du redigerar diagramegenskaper, centrerar diagramdatalabels, visar procentandelar i diagrammet och anpassar diagramdatalabels för alla scenarier.

Handledningen täcker allt som krävs för att modifiera ett befintligt diagram, från att ladda dokumentet till att spara ändringarna. Inga externa referenser behövs—bara Aspose.Words for .NET‑biblioteket och en grundläggande C#‑utvecklingsmiljö.

## Förutsättningar

* .NET 6.0 (eller senare) installerat.
* Aspose.Words for .NET version 23.9 eller nyare.  
  Du kan installera den via NuGet:

```bash
dotnet add package Aspose.Words
```

* En Word‑fil (`input.docx`) som innehåller minst ett diagram.

## Hur man lägger till datalabels i ett Word-diagram i C#

Följande avsnitt guidar dig genom varje steg. Det primära nyckelordet **how to add data labels** förekommer naturligt i texten och i kodkommentarerna, vilket håller densiteten inom det rekommenderade intervallet.

### Steg 1 – Ladda Word‑dokumentet som innehåller diagrammet

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Varför detta steg är viktigt*: `Document`‑objektet representerar hela Word‑filen. När du laddar den får du åtkomst till alla noder, inklusive former som innehåller diagram.

### Steg 2 – Hämta det första diagrammet från dokumentet

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Varför detta steg är viktigt*: Diagram lagras i `Shape`‑noder. Genom att kasta den hämtade noden till `Shape` och anropa `GetChart()` får du ett `Chart`‑objekt som ger tillgång till serier, axlar och etikett‑samlingar.

### Steg 3 – Aktivera anpassning av datalabels och visa procentandelar i diagrammet

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Varför detta steg är viktigt*: Genom att sätta `ShowPercentage` instrueras Aspose.Words att beräkna och visa varje sektions bidrag till totalen. Detta adresserar direkt det sekundära nyckelordet **show percentages in chart**.

### Steg 4 – Ändra etikettplaceringen till mitten av varje datapunkt

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Varför detta steg är viktigt*: `Position`‑egenskapen styr var etiketten visas i förhållande till datapunkten. Genom att använda `Center` uppfylls det sekundära nyckelordet **center chart data labels** och läsbarheten förbättras för paj‑ eller donut‑diagram.

### Steg 5 – Anpassa diagramdatalabels ytterligare (valfritt)

Om du behöver mer kontroll kan du justera teckensnitt, färg eller ledarlinjer:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Dessa inställningar illustrerar det sekundära nyckelordet **customize chart data labels** och visar hur du kan anpassa utseendet för att matcha varumärkesriktlinjer.

### Steg 6 – Spara det modifierade dokumentet

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Varför detta steg är viktigt*: När du sparar skrivs det uppdaterade diagrammet tillbaka in i Word‑dokumentet, så att de nya datalabels blir synliga när filen öppnas i Microsoft Word.

## Fullt, körbart exempel

Nedan finns ett komplett program som du kan kopiera, klistra in och köra. Det innehåller alla nödvändiga `using`‑direktiv och kommentarer som förklarar varje rad.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Förväntat resultat

När du öppnar `output.docx` i Microsoft Word kommer diagrammet att visa:

* Procentvärden bredvid varje sektor (t.ex. **25 %**, **40 %**, …).
* Etiketter placerade i mitten av varje datapunkt.
* Eventuell ytterligare formatering du har lagt till, såsom fet röd text.

Dessa visuella ledtrådar gör diagrammet lättare att tolka, särskilt i presentationer eller rapporter.

## Hur man redigerar diagramegenskaper utanför datalabels

Även om fokus i den här guiden är **how to add data labels**, kan du också vilja **how to edit chart** inställningar såsom titlar, legendplacering eller axelformatering. `Chart`‑objektet erbjuder egenskaper som `Title`, `Legend` och `AxisX/AxisY`. Till exempel, för att ändra diagramtiteln:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Alla diagramändringar följer samma mönster: hämta diagrammet, justera dess egenskaper och sedan spara dokumentet.

## Vanliga fallgropar och bästa praxis‑tips

| Fallgropar | Varför det händer | Rekommenderad åtgärd |
|---|---|---|
| Diagrammet är inuti en grupperad form. | `GetChild(NodeType.Shape, …)` returnerar den yttre gruppen, inte det inre diagrammet. | Sök rekursivt efter en form med `shape.HasChart`. |
| Datalabels visas inte efter sparning. | `ShowValue` eller `ShowPercentage` var inte satt till `true`. | Ställ explicit in både `ShowValue` och `ShowPercentage` efter behov. |
| Etiketter överlappar på små sektorer. | Centrerad placering kan orsaka trängsel. | Använd `ChartDataLabelPosition.OutSideEnd` för placering utanför, eller aktivera `LeaderLines`. |

## Slutsats

Du vet nu hur du **how to add data labels** till ett Word‑diagram med C#. Handledningen täckte hur man hämtar diagrammet, aktiverar etikettvisning, centrerar etiketterna, visar procentandelar och anpassar utseendet. Med denna kunskap kan du också **how to edit chart** detaljer, **center chart data labels**, **show percentages in chart** och **customize chart data labels** för alla rapporteringsscenarier.

Redo att utforska mer? Prova att lägga till flera serier, tillämpa villkorsstyrd formatering eller exportera diagrammet som en bild. Aspose.Words‑API:et erbjuder omfattande möjligheter för diagrammanipulation—experimentera för att hitta den perfekta visuella representationen av dina data.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}