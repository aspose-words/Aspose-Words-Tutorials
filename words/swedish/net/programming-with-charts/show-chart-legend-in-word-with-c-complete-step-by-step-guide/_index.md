---
category: general
date: 2026-06-02
description: Visa diagramförklaring i ett Word‑dokument med C#. Lär dig hur du lägger
  till förklaring, använder en förinställd diagramstil och anpassar Word‑diagrammets
  visuella utseende på några minuter.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: sv
og_description: Visa diagramförklaring i ett Word‑dokument omedelbart. Denna guide
  visar dig hur du lägger till en förklaring, tillämpar förinställd diagramstil och
  hanterar specialfall.
og_title: Visa diagramförklaring i Word – Fullständig C#‑handledning
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Visa diagramlegend i Word med C# – Komplett steg‑för‑steg‑guide
url: /sv/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Visa diagramförklaring i Word med C# – Komplett steg‑för‑steg‑guide

Har du någonsin undrat **hur man lägger till en förklaring** till ett diagram som finns i ett Word‑dokument? Du är inte ensam. I många rapporter gör en saknad förklaring data kryptisk, och att åtgärda det bör inte vara en huvudvärk.  

I den här handledningen kommer vi att **visa diagramförklaring** i en Word‑fil med Aspose.Words för .NET, tillämpa en förinställd diagramstil och se till att förklaringen visas exakt där du behöver den. I slutet har du ett färdigt exempel som du kan lägga in i vilket C#‑projekt som helst.

## Vad den här guiden täcker

Vi går igenom hela arbetsflödet:

1. Läs in ett befintligt *.docx* som redan innehåller ett diagram.  
2. Hämta det första diagrammet (eller vilket diagram du vill rikta in dig på).  
3. **Tillämpa förinställd diagramstil** för att ge visualiseringen ett professionellt utseende.  
4. **Visa diagramförklaring**, placera den till höger och hantera specialfall som Waterfall‑diagram.  
5. Spara det modifierade dokumentet.

Inga externa verktyg, ingen manuell trixning med UI‑tänget—bara ren kod. Det enda förutsättningen är en referens till Aspose.Words NuGet‑paketet (version 23.10 eller senare) och en grundläggande förståelse för C#.

## Förutsättningar

- .NET 6.0 eller senare (exemplet fungerar även med .NET Framework 4.7.2).  
- Aspose.Words för .NET‑biblioteket installerat (`Install-Package Aspose.Words`).  
- En Word‑fil (`input.docx`) som redan innehåller minst ett diagram.  
- Visual Studio, Rider eller någon annan IDE du föredrar.

## Steg 1: Ställ in projektet och läs in dokumentet

Först, skapa en konsolapp (eller integrera koden i ett befintligt projekt). Lägg till `using`‑direktiven och läs in `.docx`‑filen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Varför detta är viktigt:** Att läsa in dokumentet är grunden. Utan en `Document`‑instans kan du inte nå diagramobjekten som Aspose.Words exponerar.

## Steg 2: Hämta mål‑diagrammet

Diagram lagras som noder i dokumentträdet. Metoden `GetChild` utför en djup sökning, vilket låter oss hämta det första diagrammet oavsett var det finns (sidhuvud, brödtext, sidfot osv.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Tips:** Om du har flera diagram, ändra indexet `0` till `1`, `2`, … eller iterera genom `doc.GetChildNodes(NodeType.Chart, true)`.

## Steg 3: Tillämpa en förinställd visuell stil

Ett snyggt diagram börjar ofta med en stil. Aspose.Words levereras med dussintals inbyggda stilar; `ChartStyle.Style12` är ett rent, modernt alternativ.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Hur det fungerar:** `Style`‑egenskapen motsvarar de inbyggda Word‑diagramstilarna du ser i UI. Att välja en förinställning sparar dig från att manuellt ställa in färger, typsnitt och markörer.

## Steg 4: Aktivera förklaringen och placera den

Nu till stjärnan i showen—**visa diagramförklaring**. Vi slår på förklaringen och dockar den till diagrammets högra sida.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Varför höger?** Att placera förklaringen till höger behåller dataområdet brett, vilket är särskilt hjälpsamt för stapel‑ eller kolumndiagram.

## Steg 5: Hantera Waterfall‑diagram (specialfall)

Waterfall‑diagram beter sig lite annorlunda; förklaringen kan vara dold som standard. Följande skyddsklausul säkerställer att förklaringen är synlig när diagramtypen är Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Obs om kantfall:** Vissa äldre Word‑versioner ignorerar `HasLegend` för Waterfall‑diagram, så att explicit sätta `Legend.Show` garanterar synlighet.

## Steg 6: Spara det modifierade dokumentet

Till sist, skriv tillbaka ändringarna till disk. Du kan skriva över originalfilen eller skapa en ny.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

När programmet körs kommer det att producera `output.docx` med en synlig förklaring till höger, stylad med `Style12`. Öppna filen i Word för att verifiera resultatet.

## Fullt fungerande exempel (alla steg kombinerade)

Nedan är den kompletta, färdiga koden. Kopiera‑och‑klistra in den i `Program.cs` (eller någon C#‑fil) och justera filsökvägarna.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Förväntat resultat:** När du öppnar `output.docx` visas det ursprungliga diagrammet med en högerriktad förklaring, stylad med den moderna `Style12`. Alla dataserier är tydligt märkta, vilket gör diagrammet omedelbart begripliga.

## Vanliga frågor (FAQ)

### Hur lägger man till förklaring till ett specifikt diagram (inte det första?)

Byt ut indexet `0` i `GetChild(NodeType.Chart, 0, true)` mot den nollbaserade positionen för ditt mål‑diagram, eller loopa igenom alla diagramnoder:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Kan jag placera förklaringen längst ner istället för till höger?

Absolut. Ändra bara `LegendPosition`‑enumet:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Vad händer om diagrammet redan har en förklaring men jag vill dölja den?

Sätt `HasLegend` till `false`:

```csharp
chart.HasLegend = false;
```

### Fungerar detta med Word 2010, 2016 och senare?

Ja. Aspose.Words abstraherar den underliggande Word‑versionen, så samma kod fungerar i alla moderna .docx‑filer.

## Pro‑tips & vanliga fallgropar

- **Pro‑tips:** Efter att ha tillämpat en stil kan du fortfarande justera enskilda element (färger, datalabels) via `Chart.Series`‑samlingen. Stilen ger dig en solid grund.
- **Se upp för:** Om diagrammet är i en tabellcell kan förklaringen bli trång. Överväg att öka diagrammets storlek (`chart.Width`, `chart.Height`) innan du placerar förklaringen.
- **Prestanda‑notering:** Att läsa in stora dokument (hundratals MB) kan vara minneskrävande. Använd `LoadOptions` med `LoadFormat.Docx` för att minska overhead om du bara behöver manipulera diagram.

## Nästa steg

Nu när du vet **hur man lägger till förklaring** och **tillämpa förinställd diagramstil** i Word, kan du utforska:

- **Anpassade diagramfärger** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Formatering av datalabels** (`chart.Series[i].HasDataLabel = true`).  
- **Exportera diagrammet som bild** (`chart.ToImage()`), användbart för inbäddning någon annanstans.  

Var och en av dessa ämnen bygger på samma objektmodell, så du kommer att finna inlärningskurvan mild.

## Slutsats

Vi har just demonstrerat en ren, helhetslösning för **visa diagramförklaring** i ett Word‑dokument med C#. Genom att läsa in dokumentet, hämta diagrammet, tillämpa en förinställd stil, aktivera förklaringen och hantera Waterfall‑särdrag får du ett polerat diagram redo för vilken affärsrapport som helst.  

Känn dig fri att experimentera med andra `ChartStyle`‑värden eller förklaringspositioner—dina datavisualiseringar förtjänar den bästa presentationen. Om du stöter på problem, lämna en kommentar nedan; glad kodning!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Infoga stapeldiagram i ett Word‑dokument](/words/english/net/programming-with-charts/insert-column-chart/)
- [Dölj diagramaxel i ett Word‑dokument](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Använda Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}