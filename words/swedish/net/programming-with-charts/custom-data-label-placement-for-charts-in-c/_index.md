---
category: general
date: 2026-08-04
description: Anpassad placering av datamärken för diagram i C# låter dig centrera
  etiketter på diagramdelar. Följ den här steg‑för‑steg‑guiden med Aspose.Words diagram‑API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: sv
lastmod: 2026-08-04
og_description: Anpassad placering av datamärkning för diagram i C# visar hur du centrerar
  alla datamärken på varje del av ett Word‑diagram. Mästra placeringen av diagrammets
  datamärken med Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Anpassad placering av dataetiketter för diagram i C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Anpassad placering av dataetiketter för diagram i C#
url: /sv/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Anpassad placering av dataetiketter för diagram i C#

**Anpassad placering av dataetiketter för diagram** låter dig styra exakt var varje etikett visas i ett diagram i ett Word‑dokument. I den här handledningen lär du dig hur du centrerar alla dataetiketter på varje segment med C# och Aspose.Words diagram‑API.

Du får ett komplett, körbart exempel som laddar en `.docx`‑fil, hämtar den första diagramformen, ändrar varje etikett`s Position` till `Center` och sparar det uppdaterade dokumentet. Inga externa referenser behövs – bara Aspose.Words för .NET‑biblioteket och en grundläggande C#‑utvecklingsmiljö.

**Vad du kommer att lära dig**

* Hur du laddar ett Word‑dokument som innehåller ett diagram.  
* Hur du hittar diagramformen med Aspose.Words diagram‑API.  
* Hur du tillämpar **diagram‑dataetikett‑positionering** på varje serie i diagrammet.  
* Hur du sparar dokumentet så att de centrerade etiketterna visas i Word.  

**Förutsättningar**

* .NET 6.0 (eller senare) installerat.  
* Visual Studio 2022 (eller någon C#‑IDE).  
* En referens till `Aspose.Words`‑NuGet‑paketet.  
* En Word‑fil (`Chart.docx`) som innehåller minst ett diagram.

---

## Anpassad placering av dataetiketter för diagram – steg 1: ladda dokumentet

Den första åtgärden är att öppna Word‑filen som innehåller diagrammet. `Document` är startpunkten för all manipulation med Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Varför detta steg är viktigt*: Utan att ladda dokumentet kan du inte nå diagramobjektet. Valideringen säkerställer att du får ett tydligt felmeddelande om filen saknar ett diagram, vilket förhindrar en null‑referens senare.

---

## Använda Aspose.Words diagram‑API för att komma åt diagramformer

Aspose.Words behandlar ett diagram som ett `Chart`‑objekt som är inbäddat i en `Shape`. Du hämtar det genom att kasta den lämpliga barnnoden.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Varför detta steg är viktigt*: Genom att direkt komma åt `Chart` får du full kontroll över serier, datapunkter och etikett‑egenskaper. Om formen inte är ett diagram avbryts koden tidigt med ett informativt meddelande.

---

## Ställa in diagram‑dataetikett‑positionering i C#

Iterera nu genom varje serie och varje dataetikett och sätt `Position` till `Center`. Detta är kärnan i **Anpassad placering av dataetiketter för diagram**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Proffstips**: Om du behöver en annan placering (t.ex. `InsideEnd` för ett stapeldiagram), ändra enum‑värdet därefter. `ChartDataLabelPosition`‑enumet täcker alla standardpositioner som stöds av Word.

*Varför detta steg är viktigt*: Att ändra `label.Position` uppdaterar den underliggande OOXML‑representationen, så etiketten visas centrerad när dokumentet öppnas i Microsoft Word.

---

## Spara Word‑dokumentet med uppdaterade etiketter

Efter att ha modifierat diagrammet, skriv tillbaka ändringarna till en fil. Du kan skriva över originalet eller skapa en ny kopia.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Varför detta steg är viktigt*: Sparandet skriver den uppdaterade OOXML‑filen till disk. När du öppnar `ChartLabelsCentered.docx` i Word visas varje sektionsetikett centrerad, vilket bekräftar att **Anpassad placering av dataetiketter för diagram** lyckades.

---

## Kantfall och variationer

| Situation | Hur du hanterar det |
|-----------|---------------------|
| **Flera diagram** i samma dokument | Loopa över `doc.GetChildNodes(NodeType.Shape, true)` och kontrollera `shape.HasChart` för varje form. |
| **Olika diagramtyper** (pie, doughnut, bar) | Samma `ChartDataLabelPosition.Center` fungerar för paj‑typ diagram. För stapel‑/kolumndiagram kan du föredra `InsideEnd` eller `OutsideEnd`. |
| **Etiketttexten behöver formatering** | Hämta `label.TextProperties` för att sätta teckenstorlek, färg eller fetstil. |
| **Körning på .NET Core** | Se till att du refererar .NET Standard‑versionen av Aspose.Words; API‑et är identiskt. |

---

## Komplett fungerande exempel

Nedan är hela programmet som du kan kopiera och klistra in i en konsolapplikation. Det innehåller alla nödvändiga `using`‑direktiv och felhantering.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Förväntat resultat**: Öppna `ChartLabelsCentered.docx` i Microsoft Word. Varje sektionsetikett i diagrammet visas nu direkt i mitten av sektorn, vilket ger ett renare visuellt intryck.

---

## Slutsats

Du har nu en komplett **Anpassad placering av dataetiketter för diagram**‑lösning i C#. Genom att ladda dokumentet, komma åt diagrammet via Aspose.Words diagram‑API, sätta `ChartDataLabelPosition.Center` för varje etikett och spara filen, kan du automatisera etikettplacering för alla Word‑baserade diagram.

Utforska nästa steg, som andra **diagram‑dataetikett‑positionerings**‑alternativ såsom `InsideEnd` eller `OutsideEnd`, eller experimentera med **C#‑diagrammanipulation** för att ändra färger, lägga till förklaringar eller generera diagram från grunden. Dessa utökningar bygger direkt på teknikerna i den här guiden och breddar dina färdigheter i automatisering av Word‑dokumentdiagram. Lycka till med kodandet!


## Vad bör du lära dig härnäst?


De följande handledningarna täcker nära besläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}