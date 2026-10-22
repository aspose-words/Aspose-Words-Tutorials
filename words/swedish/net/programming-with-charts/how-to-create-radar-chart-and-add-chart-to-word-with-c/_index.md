---
category: general
date: 2026-09-05
description: Skapa ett radardiagram i Word med C#. Lär dig att generera ett tomt Word‑dokument,
  lägga till ett radardiagram, ställa in diagrammets storlek och snabbt aktivera markeringar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: sv
lastmod: 2026-09-05
og_description: Skapa radardiagram i Word med C#. Den här guiden visar hur du genererar
  ett tomt Word‑dokument, lägger till ett radardiagram, ställer in diagrammets storlek
  och aktiverar markeringar – allt på några minuter.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Skapa radardiagram i Word – steg‑för‑steg C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Hur man skapar ett radardiagram och lägger till diagram i Word med C#
url: /sv/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så skapar du ett radardiagram och lägger till diagram i Word med C#

Om du behöver **skapa radardiagram** i en Word‑fil, guidar den här handledningen dig genom hela processen. Du lär dig hur du **genererar ett tomt Word‑dokument**, infogar ett radardiagram, **ställer in diagramstorlek i Word**, och aktiverar axelgradueringar – allt med några få rader C#‑kod.

Att lägga till visuella data i rapporter är ett vanligt krav, och med Aspose.Words blir det enkelt. I stegen nedan täcker vi också hur du **lägger till diagram i Word**‑dokument programatiskt, så att du kan automatisera instrumentpaneler, finansiella sammanfattningar eller annat datadrivet innehåll.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 eller senare installerat  
* En Aspose.Words for .NET‑licens (eller en gratis provversion) – biblioteket tillhandahåller `Document`, `DocumentBuilder` och diagram‑API:erna som används i den här handledningen  
* Visual Studio 2022 (eller någon annan C#‑IDE)  

> **Proffstips:** Om du testar, placera Aspose.Words‑DLL‑filen i ditt projekts `bin`‑mapp och referera den via NuGet (`Install-Package Aspose.Words`).

## Så skapar du radardiagram i ett Word‑dokument

Det första steget är att **generera ett tomt Word‑dokument** som ska innehålla diagrammet. Detta ger dig en ren canvas och låter dig kontrollera dokumentets metadata innan något innehåll läggs till.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Varför detta är viktigt:* Ett tomt `Document`‑objekt säkerställer att inga dolda stilar eller sektioner stör diagrammets layout. Det låter dig också senare sätta dokumentegenskaper (författare, titel) om så behövs.

## Så lägger du till diagram i Word med Aspose.Words

Nästa steg är att skapa en `DocumentBuilder`. Buildern är arbetshästen som låter dig infoga text, bilder och diagram i dokumentet.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Nu kan du **lägga till radardiagram** exakt där markören är placerad. Metoden `InsertChart` accepterar en `ChartType`‑enum, bredd och höjd i punkter.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Varför 400 × 300?* Dessa dimensioner ger ett tydligt, läsbart diagram på en standard‑A4‑sida. Du kan justera storleken senare med steget **ställ in diagramstorlek i Word** om ditt layoutbehov kräver ett annat bildförhållande.

## Ställa in diagramstorlek i Word

Om du behöver finjustera storleken efter infogandet kan du ändra diagrammets `Width`‑ och `Height`‑egenskaper. Detta är användbart när omgivande text eller sidmarginaler kräver en annan visuell balans.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Obs:** Överlagringen av `InsertChart` sätter redan storleken, så koden ovan är valfri och visas för fullständighetens skull.

## Aktivera streck på den radiella axeln

Ett radardiagram är mest användbart när den radiella axeln visar tydliga gradueringar. Följande inställningar slår på streck och sätter intervallet till 30 grader, vilket stämmer med vanliga kompass‑liknande radardiagram.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Varför detta är viktigt:* Gradueringar hjälper läsaren att uppskatta värden vid varje vinkel, vilket förbättrar läsbarheten för intressenter som inte är bekanta med datan.

## Spara dokumentet som innehåller diagrammet

Till sist skriver du dokumentet till disk. Du kan välja vilken mapp du vill; se bara till att sökvägen finns.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

När du öppnar `RadialChart.docx` i Microsoft Word kommer du att se ett fullt renderat radardiagram centrerat på sidan, med den angivna storleken och streck var 30:e grad.

### Förväntat resultat

* En `.docx`‑fil med namnet **RadialChart.docx**  
* Första sidan innehåller ett radardiagram på 400 × 300 punkter  
* X‑axeln (radiell axel) visar streck vid 0°, 30°, 60°, …, 330°  

Du kan nu ersätta platshållardataserien med dina egna värden genom att komma åt `radarChart.Series` – men det ligger utanför ramen för denna grundläggande **lägg till radardiagram**‑handledning.

## Vanliga variationer och kantfall

| Scenario | Justering |
|----------|-----------|
| **Olika diagramtyp** | Ersätt `ChartType.Radar` med `ChartType.Column`, `ChartType.Pie` osv. |
| **Flera diagram** | Anropa `InsertChart` upprepade gånger; varje anrop placerar det nya diagrammet efter det föregående. |
| **Stora datamängder** | Använd `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` för att fylla många punkter. |
| **Spara som PDF** | Anropa `document.Save("RadialChart.pdf", SaveFormat.Pdf);` efter att diagrammet har lagts till. |
| **Kör på .NET Core** | Säkerställ att du refererar paketet `Aspose.Words.NETCore`; API‑användningen är identisk. |

## Fullt, körbart exempel

Nedan finns det kompletta programmet som du kan kopiera‑och‑klistra in i en konsolapplikation. Det innehåller alla steg, valfria storleksjusteringar och kommentarer för tydlighet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Kör programmet, öppna den resulterande filen, och du kommer att se radardiagrammet exakt som beskrivet.

## Slutsats

Du vet nu hur du **skapar radardiagram** och **lägger till diagram i Word**‑dokument med C#. Handledningen täckte att generera ett **tomt Word‑dokument**, infoga ett radardiagram, **ställa in diagramstorlek i Word**, och aktivera axelgradueringar. Med denna grund kan du utöka lösningen till flera diagram, anpassade dataserier eller export till PDF.

### Nästa steg

* Utforska andra diagramtyper med `ChartType` (t.ex. `Bar`, `Line`) – se nyckelordet **add radar chart** för relaterade exempel.

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna i den här guiden. Varje resurs innehåller kompletta kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringssätt i dina egna projekt.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}