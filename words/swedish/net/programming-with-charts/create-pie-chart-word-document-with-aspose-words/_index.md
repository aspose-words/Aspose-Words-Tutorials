---
category: general
date: 2026-08-10
description: Skapa ett Word‑dokument med ett cirkeldiagram med Aspose.Words. Lär dig
  hur du infogar diagram, anpassar färgerna i cirkeldiagrammet och ändrar färgen på
  en diagramdel i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: sv
lastmod: 2026-08-10
og_description: Skapa ett Word-dokument med ett cirkeldiagram med Aspose.Words. Denna
  guide förklarar hur du infogar diagram, anpassar färgerna på cirkeldiagrammet och
  ändrar färgen på en diagramdel i en C#‑applikation.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Skapa cirkeldiagram i Word-dokument – Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Skapa ett Word‑dokument med ett cirkeldiagram med Aspose.Words
url: /sv/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa pajdiagram Word-dokument med Aspose.Words

Om du behöver **skapa pajdiagram Word-dokument** programatiskt, visar den här handledningen exakt hur. Vi går igenom hur du infogar ett diagram, **anpassar färger på pajdiagram**, och **ändrar färg på pajskiva** med Aspose.Words för .NET.

Du kommer att se ett komplett, körbart exempel som du kan kopiera till Visual Studio, köra och omedelbart öppna den genererade *.docx* för att verifiera det stylade pajdiagrammet. Ingen extern dokumentation krävs—allt du behöver finns i den här guiden.

## Förutsättningar

* .NET 6.0 SDK eller senare installerat  
* En giltig Aspose.Words för .NET-licens (eller en tillfällig utvärderingsnyckel)  
* Visual Studio 2022 (eller någon C#-IDE)  

Koden använder endast namnutrymmena `Aspose.Words` och `Aspose.Words.Drawing.Charts`, så inga ytterligare NuGet‑paket krävs utöver Aspose.Words‑biblioteket.

## Skapa pajdiagram Word-dokument – fullständigt exempel

Följande C#‑program skapar ett nytt Word‑dokument, infogar ett pajdiagram, formaterar de två första skivorna och sparar filen. Varje steg förklaras i detalj.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Förklaring av varje steg

| Steg | Vad det gör | Varför det är viktigt |
|------|--------------|----------------|
| **1** | Skapar ett nytt `Document` och en `DocumentBuilder`. | `DocumentBuilder` tillhandahåller flytande metoder för att infoga innehåll, såsom diagram, i Word‑filen. |
| **2** | Anropar `InsertChart` med `ChartType.Pie` och en fast storlek. | `InsertChart` är metoden för **hur man infogar diagram**; att specificera bredd/höjd säkerställer att diagrammet passar bra på sidan. |
| **3** | Lägger till en dataserie med tre kategorier och numeriska värden. | Ett pajdiagram utan data är osynligt; att fylla i det visar stilstegen. |
| **4** | Ställer in `Explosion` på den första punkten. | Att explodera en skiva drar uppmärksamhet till ett specifikt segment—användbart för att framhäva viktig data. |
| **5** | Ställer in `ForeColor` för de två första punkterna. | Detta är kärnan i **anpassa färger på pajdiagram**; du kan använda vilken `System.Drawing.Color` som helst. |
| **6** | Visar hur man **ändrar färg på pajskiva** för ytterligare skivor. | Visar att formatering inte är begränsad till de två första skivorna; du kan färga varje skiva individuellt. |
| **7** | Sparar dokumentet som `PieChartStyled.docx`. | Det slutgiltiga resultatet kan öppnas i Microsoft Word, Google Docs eller någon kompatibel visare. |

#### Förväntat resultat

När du öppnar `PieChartStyled.docx` visas en enda sida med ett 400 × 300 pt pajdiagram:

* Skiva 1 (orange) är exploderad utåt.  
* Skiva 2 (grön) visas intill den exploderade skivan.  
* Skiva 3 (stål‑blå) fyller det återstående segmentet.

Diagrammet återspeglar datavärdena (30, 45, 25) och de anpassade färgerna du definierade.

## Hur man formaterar paj – ytterligare tips

* **Använd temafärger** – istället för att hårdkoda `Color.Orange` kan du hämta färger från dokumenttemat:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Lägg till datamärkningar** – om du vill ha procenttal visade på diagrammet:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Ändra storlek dynamiskt** – beräkna diagrammets storlek baserat på sidmarginaler:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Dessa variationer visar flexibiliteten i **hur man formaterar paj** utöver grundexemplet.

## Vanliga frågor besvarade

**Q: Fungerar detta med .NET Core?**  
**A: Ja. Aspose.Words för .NET är kompatibel med .NET Core, .NET 5, .NET 6 och senare. Referera bara samma NuGet‑paket.**

**Q: Vad händer om jag behöver ett donut‑diagram istället för en paj?**  
**A: Ersätt `ChartType.Pie` med `ChartType.Doughnut`. Samma stil‑API:er (`Explosion`, `ForeColor`) gäller.**

**Q: Kan jag infoga diagrammet i ett befintligt dokument?**  
**A: Öppna den befintliga filen med `new Document("Existing.docx")`, skapa en `DocumentBuilder` för det dokumentet och anropa `InsertChart` på önskad markörposition.**

**Q: Hur hanterar jag stora datamängder?**  
**A: Pajdiagram är bäst för ett begränsat antal kategorier (vanligtvis < 10). För många kategorier, överväg ett stapel‑ eller kolumndiagram istället.**

## Fullständig källkodssammanfattning

Nedan är hela programmet i ett block för enkel kopiering‑och‑klistring:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Att köra denna kod producerar det stylade pajdiagram‑Word‑dokumentet som beskrevs tidigare.

## Slutsats

Du vet nu hur du **skapar pajdiagram Word**‑dokument med Aspose.Words, **anpassar färger på pajdiagram** och **ändrar färg på pajskiva** programatiskt. Guiden täckte infogning av diagrammet, fyllning av data, exploderande av en skiva, applicering av anpassade färger och sparande av resultatet.  

Härifrån kan du utforska relaterade ämnen som **hur man infogar diagram** av andra typer än paj, lägga till förklaringar eller generera flersidiga rapporter med flera diagram. Experimentera med olika färgscheman och datamängder för att passa dina rapporteringsbehov.

Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Infoga stapeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Infoga områdesdiagram i Word-dokument | Aspose.Words för .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Skapa spridningsdiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}