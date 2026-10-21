---
category: general
date: 2026-09-21
description: Lär dig hur du skapar ett cirkeldiagram och infogar diagram i Word med
  Aspose.Words, lägger till datamärkningar i cirkeldiagrammet och visar procentandelar
  i cirkeldiagrammet på bara några steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: sv
lastmod: 2026-09-21
og_description: Skapa ett cirkeldiagram i Word med Aspose.Words, infoga diagrammet
  i Word, lägg till datamärkningar i cirkeldiagrammet och visa procentandelar i cirkeldiagrammet
  – allt med tydliga kodexempel.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Skapa ett cirkeldiagram i Word med Aspose.Words – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Hur man skapar ett cirkeldiagram i ett Word‑dokument med Aspose.Words
url: /sv/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett cirkeldiagram i ett Word-dokument med Aspose.Words

Om du behöver **create pie chart** programatiskt, gör Aspose.Words det enkelt. I den här handledningen kommer du att se hur du **insert chart into Word**, konfigurerar serierna, **add data labels to pie chart**, och slutligen **show percentages on pie chart** så att visualiseringen förmedlar exakta värden. I slutet har du ett komplett, körbart exempel som du kan lägga in i vilket .NET‑projekt som helst.

Den här guiden täcker allt du behöver veta: nödvändiga NuGet‑paket, den fullständiga C#‑källkoden, förklaringar till varför varje API‑anrop är viktigt, och tips för att anpassa diagrammet. Ingen extern dokumentation krävs—kopiera bara, kör och anpassa.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare installerat.  
* Visual Studio 2022 (eller någon IDE som stödjer .NET).  
* En Aspose.Words för .NET‑licens (gratis provversion fungerar för testning).  
* Grundläggande kunskap om C# och Word‑dokumentstrukturer.

Om du redan har dessa kan du gå direkt till koden.

## Steg 1: Ställ in projektet och importera Aspose.Words

Skapa ett nytt konsolprojekt och lägg till Aspose.Words‑NuGet‑paketet:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Paketet innehåller namnutrymmet `Aspose.Words.Drawing.Charts`, som innehåller klasserna `Chart` och `ChartSeries` som vi kommer att använda.

> **Pro tip:** Behåll din licensfil (`Aspose.Words.lic`) i projektets rot och läs in den vid start för att undvika utvärderingsvattenstämplar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Steg 2: Skapa ett tomt dokument och en DocumentBuilder

Ett `Document` representerar Word‑filen, medan `DocumentBuilder` erbjuder ett flytande API för att infoga innehåll.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Varför detta är viktigt:** `DocumentBuilder` behåller den aktuella infogningspunkten, vilket säkerställer att diagrammet visas exakt där du vill ha det i dokumentflödet.

## Steg 3: Infoga ett cirkeldiagram i Word‑dokumentet

Nu **insert chart into Word**. Metoden `InsertChart` tar diagramtypen, bredden och höjden (i punkter).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Vid detta tillfälle innehåller diagrammet en standarddataserie med platshållarvärden (25, 25, 25, 25). Du kan ersätta dem senare om så behövs.

## Steg 4: Åtkomst till den första serien och anpassa datalabels

Ett cirkeldiagram har vanligtvis en enda serie. För att **add data labels to pie chart** hämtar vi den och aktiverar procentvisning.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Varför vi sätter `ShowPercentage`:** Denna flagga talar om för Aspose.Words att beräkna varje sektions bidrag och rendera det som en procentandel. `Position`‑egenskapen säkerställer att etiketten inte överlappar sektorn, vilket förbättrar läsbarheten—särskilt när sektorerna är små.

## Steg 5: (Valfritt) Ersätt platshållardatan

Om du vill ha specifika värden, ersätt standardpunkterna:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

De visade procentandelarna kommer automatiskt att justeras för att återspegla de nya värdena.

## Steg 6: Spara dokumentet

Slutligen skriv dokumentet till disk. Filändelsen bestämmer formatet; `.docx` skapar en modern Word‑fil.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

När programmet körs skapas en fil med namnet **PieChart.docx** i utdata‑mappen. När du öppnar den i Microsoft Word visas ett cirkeldiagram där varje sektor är märkt med sin procentandel, placerad utanför sektorerna.

### Förväntad output

När du öppnar det genererade dokumentet bör du se:

* Ett enda cirkeldiagram, 400 × 300 pt i storlek.  
* Fyra sektorer (eller hur många punkter du har lagt till).  
* Procentetiketter såsom “40 %”, “30 %”, osv., visas utanför varje sektor.

Om etiketterna visas inuti sektorerna, dubbelkolla att `ChartDataLabelPosition.OutsideEnd` har ställts in korrekt.

## Steg 7: Vanliga variationer och kantfall

### Lägg till en titel på diagrammet

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Ändra sektorfärger

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Hantera en tom serie

Om din datakälla kan vara tom, skydda mot `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Exportera till PDF istället för Word

Samma diagramrenderingslogik gäller; Aspose.Words konverterar automatiskt Word‑layouten till PDF.

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

## Fullständig källkod

Nedan är det kompletta, färdiga att köra programmet. Kopiera det till `Program.cs` och kör `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Slutsats

Du vet nu hur man **create pie chart** i en Word‑fil med Aspose.Words, **insert chart into Word**, **add data labels to pie chart**, och **show percentages on pie chart**. Exemplet visar hela arbetsflödet—från projektuppsättning till slutdokument—så att du kan anpassa det för instrumentpaneler, rapporter eller automatiserad fakturagenerering.

Nästa steg är att utforska relaterade ämnen som **how to display percentages in chart**‑legender, anpassning av diagramfärger, eller konvertering av Word‑dokumentet till PDF för distribution. Experimentera med olika diagramtyper (Bar, Line) med samma `InsertChart`‑metod för att bredda dina automatiseringsmöjligheter.

Lycka till med diagrammen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker nära besläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}