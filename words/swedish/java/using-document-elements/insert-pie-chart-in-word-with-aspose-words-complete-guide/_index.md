---
category: general
date: 2026-07-26
description: Infoga ett cirkeldiagram i ett Word‑dokument med Aspose.Words. Lär dig
  hur du lägger till diagram, exploderar en del och visar procentsatser på bara några
  steg.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: sv
lastmod: 2026-07-26
og_description: Infoga ett cirkeldiagram i en Word‑fil med Aspose.Words. Följ den
  här guiden för att lära dig hur du lägger till diagram, exploderar en del och visar
  procentsatser snabbt.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Infoga cirkeldiagram i Word – Steg‑för‑steg Aspose.Words‑handledning
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Infoga cirkeldiagram i Word med Aspose.Words – Komplett guide
url: /sv/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga cirkeldiagram i Word med Aspose.Words – Komplett guide

Har du någonsin behövt **infoga cirkeldiagram** i en Word‑rapport men varit osäker på var du ska börja? Du är inte ensam. I många affärsapplikationer ger den visuella effekten av ett cirkeldiagram data som omedelbart blir lättförståelig, och Aspose.Words gör det möjligt med bara några rader kod.

I den här handledningen går vi igenom de exakta stegen för att **lägga till diagram i Word**, "explodera" en del för att framhäva den, och visa procenttal på datamärkningarna. I slutet har du ett färdigt exempel som du kan klistra in i vilket .NET‑projekt som helst.

---

## Förutsättningar

Innan vi dyker ner, se till att du har:

- .NET 6.0 eller senare (koden fungerar både med .NET Core och .NET Framework)
- Aspose.Words for .NET NuGet‑paketet installerat  
  ```bash
  dotnet add package Aspose.Words
  ```
- Grundläggande förståelse för C#‑syntax – inget avancerat krävs
- En IDE du föredrar (Visual Studio, Rider eller VS Code)

Det är allt. Låt oss sätta igång.

---

## Infoga cirkeldiagram i ett Word‑dokument

Det första vi behöver är ett nytt `Document`‑objekt och en `DocumentBuilder`. Tänk på buildern som en penna som skriver direkt på Word‑ytan.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Varför detta är viktigt:** `Document` representerar hela .docx‑filen, medan `DocumentBuilder` ger oss ett bekvämt API för att infoga element som diagram, tabeller och text. Detta är grunden för varje **hur man lägger till diagram**‑operation.

---

## Hur man lägger till diagram i Word

Nu när vi har en builder kan vi faktiskt **infoga cirkeldiagram**. Metoden `insertChart` tar diagramtypen och de önskade dimensionerna i punkter (1 punkt = 1/72 tum).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Tips:** Om du behöver en annan storlek, justera bara värdena för bredd och höjd. Diagrammet skalas automatiskt för att passa sidmarginalerna.

---

## Hur man exploderar en del för att framhäva den

En vanlig visuell justering är att “explodera” en del så att den sticker ut ur cirkeln. Detta drar läsarens blick till det viktigaste segmentet.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Varför explodera en del?** När du vill markera en viss kategori – till exempel “Q1‑intäkter” i en finansiell rapport – gör en exploderad del den omedelbart märkbar utan extra text.

---

## Hur man visar procenttal på datamärkningarna

De flesta cirkeldiagram ser bättre ut när varje del visar sin procentandel. Aspose.Words låter oss aktivera detta med en enda egenskap.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Snabb notering:** Flaggan `ShowPercentage` gäller för alla punkter i serien, så du behöver inte sätta den för varje del.

---

## Spara dokumentet som innehåller diagrammet

Till sist skriver vi dokumentet till disk. Välj vilken mapp du vill; se bara till att sökvägen finns.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

När du öppnar `PieChart.docx` i Microsoft Word kommer du att se ett perfekt renderat cirkeldiagram med den första delen exploderad och procenttal visade – exakt vad du förväntar dig av en välpolerad affärsrapport.

---

## Fullständigt fungerande exempel

Nedan är det kompletta, kopiera‑och‑klistra‑klara programmet. Kör det som en konsolapp och verifiera utdatafilen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Förväntat resultat:** Öppna den genererade `PieChart.docx`. Du kommer att se ett tre‑delat cirkeldiagram med titeln “Sales Q1”, där den första delen är utdragen och varje del är märkt med “30 %”, “45 %” och “25 %”. Visualiseringen matchar de data vi matade in.

---

## Vanliga frågor & specialfall

- **Vad händer om jag behöver mer än en serie?**  
  Lägg bara till ytterligare `ChartSeries`‑objekt till `chart.Series`. Varje serie kan ha sin egen dataset, färger och explode‑inställningar.

- **Kan jag ändra diagrammets färger?**  
  Ja. Varje `ChartPoint` har en egenskap `Format.Fill.ForeColor` som du kan sätta till vilken `System.Drawing.Color` som helst.

- **Vad sägs om olika diagramtyper?**  
  `ChartType`‑enumet innehåller stapel, linje, donut och många fler. Byt `ChartType.Pie` mot den visualisering du behöver.

- **Är diagrammet redigerbart i Word efter infogning?**  
  Absolut. Word behandlar diagrammet som ett inbyggt Office‑diagram, så användare kan dubbelklicka på det för att öppna den inbyggda diagramredigeraren.

---

## Slutsats

Du vet nu exakt hur du **infogar cirkeldiagram** i ett Word‑dokument med Aspose.Words, **hur du lägger till diagram i Word**, **hur du exploderar en del**, och **hur du visar procenttal** på datamärkningarna. Det fullständiga exemplet ovan är redo att köras, och du kan utöka det med egna data, styling eller ytterligare serier.

Redo för nästa steg? Prova att byta ut cirkeln mot ett donut‑diagram, eller generera en batch av rapporter med olika dataset automatiskt. Om du är nyfiken på andra visualiseringar, kolla in våra guider om **hur man lägger till diagram** för stapel‑ och linjediagram, eller utforska **add chart to word**‑API‑referensen för djupare anpassningar.

Lycka till med kodandet, och må dina dokument alltid vara lika tydliga som en perfekt skivad paj!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga kolumndiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Infoga areadiagram i Word‑dokument \| Aspose.Words för .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Skapa spridningsdiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}