---
category: general
date: 2026-10-13
description: Aspose.Words-exempel på radialdiagram som visar hur man aktiverar graderingar
  på ett radialdiagram med C# och Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: sv
lastmod: 2026-10-13
og_description: Aspose.Words-exempel på radialdiagram som demonstrerar hur man aktiverar
  graderingar på ett radialdiagram med C# och det senaste 24.9+‑biblioteket.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words-exempel på radialdiagram – aktivera graderingar i C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Aspose.Words‑exempel på radialdiagram: aktivera graderingar i C#'
url: /sv/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words radialdiagram-exempel: aktivera graderingar i C#

Om du letar efter ett **aspose.words radial chart example**, har du hamnat på rätt plats. Denna handledning guidar dig genom de exakta stegen för att slå på graderingar för ett radialdiagram med hjälp av Aspose.Words for .NET API.

Radialdiagram är användbara för att visualisera cyklisk data såsom tid‑på‑dagen-mått eller säsongstrender. Som standard är graderingar (de små markeringarna runt den cirkulära axeln) dolda, vilket kan göra diagrammet svårare att läsa. Att aktivera dem är en ändring på en rad, men du måste känna till rätt objektmodell och den version som stödjer funktionen.

I den här guiden kommer du att lära dig hur du:

* Ladda ett Word-dokument som redan innehåller ett radialdiagram.  
* Åtkomst till diagramformen via Aspose.Words diagram-API.  
* Aktivera **graduations visibility** (tillgängligt från **Aspose.Words version 24.9**).  
* Spara det modifierade dokumentet och verifiera resultatet.

Den kompletta, körbara koden är inkluderad, så du kan kopiera‑klistra in den i ett nytt konsolprojekt och se effekten omedelbart.

![Aspose.Words radialdiagram-exempel med graderingar](https://example.com/images/radial-chart-graduations.png "Aspose.Words radialdiagram-exempel som visar graderingar aktiverade")

## Förutsättningar

Innan du börjar, se till att du har:

| Krav | Varför det är viktigt |
|------|------------------------|
| .NET 6.0 or later | Aspose.Words for .NET 24.9+ riktar sig mot .NET Standard 2.0 och fungerar på .NET 6+. |
| Aspose.Words for .NET **24.9** or newer | `IsGraduationsVisible`-egenskapen introducerades i version 24.9. Äldre versioner kommer att kasta ett `MissingMemberException`. |
| A Word document (`RadialChart.docx`) that contains a radial chart | Ett Word-dokument (`RadialChart.docx`) som innehåller ett radialdiagram. Exemplet manipulerar ett befintligt diagram; att skapa ett från början är ett separat ämne. |
| En C#-IDE (Visual Studio, Rider, VS Code) | Alla IDE:er som kan kompilera .NET-projekt fungerar. |
| NuGet package `Aspose.Words` | Installera via `dotnet add package Aspose.Words --version 24.9.0` (eller senare). |

> **Pro tip:** Om du inte kan uppgradera till 24.9, kan du fortfarande ändra andra diagramegenskaper, men graderingar kommer att förbli dolda eftersom API:et inte exponerade den flaggan.

## Aspose.Words radialdiagram-exempel – steg‑för‑steg‑guide

Följande avsnitt delar upp processen i diskreta, lätt‑följda steg. Varje steg innehåller den exakta koden du behöver och en kort förklaring till *varför* steget finns.

### Steg 1: Ladda dokumentet som innehåller ett radialdiagram

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Varför detta är viktigt:**  
`Document` är startpunkten för **Aspose.Words chart API**. Den laddar DOCX-filen i minnet och ger dig åtkomst till varje nod—paragrafer, tabeller och diagramformer. Om filen inte kan hittas, kastar `Document` ett `FileNotFoundException`, vilket du bör hantera i produktionskod.

### Steg 2: Hämta den första diagramformen från dokumentet

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Varför detta är viktigt:**  
Diagram lagras som `Shape`-noder. Metoden `GetChild` med `NodeType.Shape` går igenom DOM och returnerar den första matchande formen. Att kasta till `Chart` ger dig åtkomst till diagram‑specifika egenskaper som `RadialChart`. Null‑kontrollen säkerställer att du får ett tydligt fel om dokumentet inte innehåller ett diagram, vilket är ett vanligt kantfall när mallar återanvänds.

### Steg 3: Aktivera graderingar på radialdiagrammet

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Varför detta är viktigt:**  
`IsGraduationsVisible` styr de små markeringarna runt den cirkulära axeln. När den sätts till `true` renderas diagrammet med graderingar, vilket förbättrar läsbarheten för tittare som behöver avläsa värden exakt. Egenskapen finns under `RadialChart`, som är en sub‑typ av `Chart`. Om du försöker detta på ett icke‑radialdiagram (t.ex. ett stapeldiagram) kommer `RadialChart`‑egenskapen att vara `null`, så du bör verifiera diagramtypen först i mer komplexa scenarier.

#### Hantering av icke‑radialdiagram (valfritt)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Detta skydd gör koden robust när källdokumentet kan innehålla olika diagramtyper.

### Steg 4: Spara det modifierade dokumentet

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Varför detta är viktigt:**  
Att anropa `Save` skriver tillbaka DOM‑minnet till en .docx‑fil och persisterar förändringen du gjort i diagrammet. Utdatafilen kan öppnas i Microsoft Word, LibreOffice eller någon annan visare som stödjer DOCX. Du kommer att se radialdiagrammet med synliga graderingar.

## Fullt, körbart exempel

Nedan är det kompletta programmet som du kan klistra in i `Program.cs` i ett .NET-konsolprojekt.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Förväntat resultat

När du öppnar `RadialChart_Graduations.docx` i Word kommer radialdiagrammet att visa markeringar (graderingar) runt den cirkulära axeln, liknande skärmbilden som visades tidigare. Resten av diagrammet (dataserier, legend, titel) förblir oförändrat.

## Vanliga variationer och kantfall

| Situation | Lösning |
|-----------|----------|
| **Äldre Aspose.Words-version (< 24.9)** | Uppgradera till det senaste NuGet-paketet. `IsGraduationsVisible`-egenskapen finns inte i tidigare versioner. |
| **Flera diagram i samma dokument** | Använd `doc.GetChild(NodeType.Shape, index, true)` med lämpligt `index` eller iterera över `doc.GetChildNodes(NodeType.Shape, true)` och filtrera på `ChartType.Radial`. |
| **Diagram skapat programatiskt** | Använd `DocumentBuilder` för att infoga ett diagram, sätt sedan `RadialChart.IsGraduationsVisible` på |

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Uppdatera diagramseriedata i ett Word-dokument med Aspose.Words för .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Ta bort en diagramserie från ett Word-dokument med Aspose.Words för .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Dölj plotområde‑kant i ett stapeldiagram med Aspose.Words för .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}