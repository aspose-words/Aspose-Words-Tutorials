---
category: general
date: 2026-10-20
description: Skapa ett cirkeldiagram i ett Word‑dokument med Aspose.Words – steg‑för‑steg‑guide
  som visar hur man ställer in färg, exploderar en skiva och sparar Word‑dokumentet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: sv
lastmod: 2026-10-20
og_description: Skapa ett cirkeldiagram i ett Word‑dokument med Aspose.Words. Lär
  dig hur du anger färg, exploderar en del och sparar Word‑dokumentet i ett enda körbart
  exempel.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Skapa ett cirkeldiagram i ett Word-dokument – komplett C#-guide
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Hur man skapar ett cirkeldiagram i ett Word-dokument med Aspose.Words
url: /sv/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett cirkeldiagram i ett Word-dokument med Aspose.Words

Om du behöver **skapa ett cirkeldiagram** i en Word-fil, visar den här guiden exakt hur du gör det. Du kommer att se hur du ställer in en anpassad färg, exploderar en del för att framhäva den, och slutligen **spara Word-dokument** med diagrammet inbäddat.

Att generera diagram programatiskt tar bort de manuella stegen att öppna Word, infoga ett diagram och justera dess utseende. I slutet av den här handledningen har du ett komplett, körbart C#-konsolprogram som skapar ett cirkeldiagram, anpassar det och skriver resultatet till disk.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare installerat  
* En giltig Aspose.Words for .NET-licens (eller en gratis utvärderingsnyckel)  
* En IDE såsom Visual Studio 2022 eller VS Code  

Inga ytterligare NuGet‑paket krävs utöver `Aspose.Words`.

## Så skapar du ett cirkeldiagram i ett Word-dokument

Det första steget är att instansiera ett `Document` och en `DocumentBuilder`. Buildern ger dig åtkomst till hög‑nivå Word‑funktioner, inklusive diagraminfogning.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

Vid detta tillfälle innehåller dokumentet redan ett grundläggande cirkeldiagram. De följande avsnitten förklarar **hur man exploderar en del**, **hur man ställer in färg**, och **hur man sparar Word-dokument**.

## Hur man exploderar en del för att framhäva den

Att explodera en del separerar den från resten av cirkeln och drar läsarens uppmärksamhet. Aspose.Words API låter dig ange ett explosionsavstånd i points.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Varför explodera delen? I rapporter som framhäver en specifik kategori—t.ex. “Top‑selling product”—gör den visuella separationen datapunkten omedelbart igenkännbar.

## Hur man ställer in färg på en diagramdel

Anpassade färger förbättrar varumärkeskonsekvens och läsbarhet. Du kan tilldela vilken `System.Drawing.Color` som helst till en specifik datapunkt.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Du är inte begränsad till fördefinierade färger; du kan skapa ett `Color.FromArgb`‑värde för exakta nyanser.

## Hur man sparar Word-dokument med diagrammet

När diagrammet ser ut som du vill är det enkelt att spara filen. Metoden `Document.Save` skriver dokumentet i det format du anger—här använder vi standard‑`.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

När programmet körs skapas `PieChart.docx`. Att öppna filen i Microsoft Word visar ett cirkeldiagram där den första delen är exploderad och färgad röd, exakt som koden specificerar.

### Förväntat resultat

* En Word‑fil med namnet **PieChart.docx** i `C:\Temp`.  
* Dokumentet innehåller ett enda cirkeldiagram, 400 × 300 points i storlek.  
* Del 0 är förskjuten med 20 points och fylld med röd, medan de andra delarna behåller standardfärgen.  

Du kan verifiera explosionen och färgen genom att markera diagrammet i Word och inspektera delens egenskaper.

## Pro‑tips och vanliga fallgropar

* **Pro tip:** Om du behöver ändra diagrammets titel eller legend, använd `pieChart.Title.Text` och `pieChart.Legend`‑egenskaperna innan du sparar.  
* **Watch out for:** Att glömma att rensa standarddatapunkterna kan leda till extra, oönskade delar. Anropa alltid `Series[0].DataPoints.Clear()` innan du lägger till dina egna data.  
* **Performance tip:** För stora dokument, återanvänd en enda `DocumentBuilder`‑instans istället för att skapa många byggare; detta minskar minnesanvändningen.

## Så skapar du diagram med Aspose.Words (ytterligare kontext)

Metoden `InsertChart` stöder många diagramtyper förutom cirkeldiagram, såsom stapel-, linje‑ och områdesdiagram. För att byta till en annan typ, ersätt `ChartType.Pie` med önskat enum‑värde, t.ex. `ChartType.Column`. Resten av anpassningsstegen (explodera delar, ställa in färger) följer samma mönster, även om inte alla diagramtyper exponerar en “explosion”-egenskap.

## Hur man exploderar en del i andra diagramtyper

Endast cirkeldiagramtyper exponerar metoden `SetExplosion`. Om du försöker anropa den på ett stapeldiagram kastar API:t ett `ArgumentException`. I sådana fall kan du överväga att använda datalabels eller anmärkningar för att framhäva en specifik stapel.

## Hur man ställer in färg på en serie istället för en enskild del

Om du vill att varje del i en serie ska ha samma färg, loopa över datapunkterna:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Denna metod är praktisk när du behöver ett enhetligt färgschema över flera diagram.

## Hur man sparar Word-dokument i andra format

Aspose.Words kan exportera till PDF, HTML och många andra format. Ändra filändelsen i `Save` och skicka eventuellt ett `SaveOptions`‑objekt:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Diagramrenderingsmotorn konverterar automatiskt diagrammet till målformatet och bevarar färger och explosionsinställningar.

## Slutsats

Du vet nu hur du **skapar ett cirkeldiagram** i ett Word-dokument, anpassar dess utseende genom att **explodera en del** och **ställa in färg**, och slutligen **spara Word-dokument** med diagrammet inbäddat. Detta end‑to‑end‑exempel ger dig en solid grund för att automatisera rapportgenerering, instrumentpaneler eller någon situation där visuella data måste infogas programatiskt.

### Nästa steg

* Utforska andra diagramtyper (`ChartType.Column`, `ChartType.Line`) för att bredda ditt rapporteringsverktyg.  
* Kombinera flera diagram i ett enda dokument för att bygga omfattande instrumentpaneler.  
* Experimentera med `ChartDataLabel` för att visa procenttal eller värden direkt på delarna.  

Känn dig fri att anpassa koden till dina egna datakällor—oavsett om du hämtar värden från en databas, ett API eller en CSV‑fil, gäller samma Aspose.Words‑arbetsflöde. Lycka till med diagrammen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Explodera cirkeldiagramdel i C# med Aspose.Words – Fullständig guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Infoga anpassat stapeldiagram i Word-dokument med Aspose.Words för .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Uppdatera diagramseriedata i ett Word-dokument med Aspose.Words för .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}