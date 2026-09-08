---
category: general
date: 2026-09-08
description: Skapa ett tomt Word‑dokument och lägg till ett diagram i Word med Aspose.Words.
  Lär dig hur du infogar ett radardiagram, aktiverar graderingar och sparar filen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: sv
lastmod: 2026-09-08
og_description: Skapa ett tomt Word‑dokument och lägg till ett diagram i Word med
  Aspose.Words. Denna handledning visar hur man infogar ett radardiagram, konfigurerar
  axlarna och sparar dokumentet.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Skapa ett tomt Word‑dokument och lägg till ett radardiagram – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Hur man skapar ett tomt Word‑dokument och lägger till ett diagram i Word
url: /sv/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett tomt Word-dokument och lägger till diagram i Word

Om du behöver **create blank Word document** för en rapport, mall eller automatiserad kopplad utskrift, guidar den här guiden dig genom hela processen med C# och Aspose.Words. Du kommer också att lära dig hur du **add chart to Word**, specifikt hur du **insert radar chart**, aktiverar graduations och sparar resultatet som en .docx-fil.

Denna handledning täcker allt från projektuppsättning till det sista verifieringssteget. I slutet kommer du att ha ett återanvändbart kodexempel som kan läggas in i vilken .NET-applikation som helst. Ingen tidigare erfarenhet av Aspose.Words krävs, men du bör ha grundläggande kunskaper i C# och ett aktuellt .NET SDK installerat.

## Förutsättningar

- .NET 6.0 SDK eller senare  
- Aspose.Words for .NET (NuGet‑paketet `Aspose.Words`)  
- En IDE såsom Visual Studio 2022 eller VS Code  
- Skrivbehörighet till den mapp där dokumentet ska sparas  

Du kan installera biblioteket med följande kommando:

```bash
dotnet add package Aspose.Words
```

## Steg 1: Skapa ett tomt Word-dokument

Det första steget är att **create blank Word document** i minnet. Klassen `Document` representerar hela filen, medan `DocumentBuilder` erbjuder ett flytande API för att lägga till innehåll.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` startar tom, så du har en ren canvas att placera diagrammet på. Att hålla dokumentet tomt i detta skede gör det enkelt att återanvända samma kod för olika mallar.

## Steg 2: Lägg till diagram i Word

Därefter **add chart to Word** genom att anropa `InsertChart`. Metoden kräver diagramtypen och de önskade dimensionerna i punkter (1 point = 1/72 tum).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` instruerar Aspose.Words att generera ett radiellt diagram, vilket är idealiskt för att visa multivariata data i en cirkulär layout. Storleksvärdena (400 × 300) fungerar bra för de flesta stående sidor, men du kan justera dem för att passa din layout.

## Steg 3: Infoga radiellt diagram och konfigurera graduations

Nu **insert radar chart** och aktiverar graduations (staplar) på både kategori‑ (X) och värde‑ (Y)‑axlarna. Graduations förbättrar läsbarheten genom att visa exakta positioner för varje datapunkt.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Att sätta `HasGraduations` till `true` ritar staplar på axlarna. Den valfria `GraduationStep` styr avståndet mellan staplar på den radiella axeln; ett steg på 10 betyder en stapel var 10:e grad.

### Proffstips
Om du behöver visa datalabels, anropa `radarChart.Series[0].HasDataLabel = true;`. Detta lägger till det numeriska värdet bredvid varje punkt, vilket är användbart för presentationer.

## Steg 4: Fyll diagrammet med exempeldata (valfritt)

Ett radiellt diagram utan data är osynligt. Nedan är ett snabbt sätt att lägga till en serie exempelvärden. Du kan ersätta detta block med din egen datakälla.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Varje anrop till `Add` infogar en punkt i serien. Punktordningen motsvarar de vinkelfördelade positionerna runt cirkeln.

## Steg 5: Spara dokumentet som innehåller diagrammet

Till sist lagras dokumentet på disk. Metoden `Save` skriver automatiskt .docx-filen och bevarar diagrammet samt all formatering.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

När programmet körs skapas ett **blank Word document** som nu innehåller ett fullt fungerande radiellt diagram. Öppna filen i Microsoft Word för att se resultatet.

![Radar chart in Word document](radar_chart.png){alt="Radar diagram infogat i ett tomt Word-dokument"}

## Vanliga variationer och kantfall

| Situation | Vad som ska ändras |
|-----------|--------------------|
| **Olika diagramstorlek** | Justera bredd-/höjdparametrarna för `InsertChart`. |
| **Andra diagramtyper** | Byt ut `ChartType.Radar` mot `ChartType.Column`, `ChartType.Pie` osv., och behåll samma graduation‑logik. |
| **Spara till en ström** | Använd `document.Save(Stream, SaveFormat.Docx)` |

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}