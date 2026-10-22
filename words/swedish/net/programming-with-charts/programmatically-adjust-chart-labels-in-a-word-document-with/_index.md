---
category: general
date: 2026-10-13
description: Lär dig hur du programatiskt justerar diagrametiketter i ett Word‑dokument
  med C#. Denna guide täcker Aspose.Words diagrammanipulation och etikettjustering.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: sv
lastmod: 2026-10-13
og_description: Programmera justering av diagrametiketter i ett Word‑dokument med
  C#. Följ den här kompletta handledningen för att ändra etikettplacering, justering
  och mer.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Programmera justering av diagrametiketter i Word – steg‑för‑steg guide i
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Justera diagrametiketter i ett Word-dokument programmässigt med C#
url: /sv/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programmera justering av diagrametiketter i ett Word‑dokument med C#

Om du behöver **programmera justering av diagrametiketter** i ett Word‑dokument, visar den här guiden exakt hur du gör det med C#. Oavsett om du genererar rapporter, automatiserar instrumentpaneler eller anpassar mallar, får du se ett komplett, körbart exempel som ändrar etikettplacering och -justering för ett diagram i en .docx‑fil.

Du får också lära dig hur du använder **Aspose.Words diagrammanipulation**‑tekniker, hanterar flera serier och undviker vanliga fallgropar när du arbetar med **C# diagramdatatetikett**‑objekt.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 (eller senare) installerat  
* Visual Studio 2022 (eller någon C#‑IDE)  
* **Aspose.Words for .NET**‑paketet från NuGet (`Install-Package Aspose.Words`)  
* Ett Word‑dokument (`input.docx`) som innehåller minst ett diagram  

Dessa komponenter krävs för **Word‑dokumentdiagramexemplet** som vi kommer att modifiera.

## Steg 1: Skapa projektet och importera namnrymder

Skapa ett nytt konsolprojekt och lägg till de nödvändiga `using`‑direktiven. Detta förbereder miljön för **programmera justering av diagrametiketter**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Varför detta steg?*  
Att ladda dokumentet ger dig åtkomst till den interna **Word‑dokumentdiagramexempel**‑trädet, där diagram lagras som form‑noder.

## Steg 2: Hitta den första diagramformen

Diagram lagras som `Shape`‑noder. Följande kod hämtar det första diagrammet i dokumentet, vilket är målet för våra etikettjusteringar.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Varför detta steg?*  
`GetChild`‑metoden söker rekursivt (`true`) och returnerar den första noden av typen `Shape`. En cast till `Chart` låter oss arbeta med diagram‑specifika API‑metoder.

## Steg 3: Åtkomst till den datatetikett du vill ändra

Varje serie i ett diagram har en samling datatetiketter. För ett enkelt diagram räcker ofta den första etiketten. Koden nedan visar hur du når den.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Varför detta steg?*  
`ChartSeries` representerar en serie av punkter. `DataLabelCollection` innehåller etiketterna för den serien, vilket möjliggör exakt kontroll över placering och justering.

## Steg 4: Ändra etikettplacering och -justering

Nu **programmerar vi justering av diagrametiketter** genom att ange position, horisontell justering och vertikal justering. Dessa egenskaper motsvarar de alternativ du ser i Word‑gränssnittet.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Varför dessa inställningar?*  

* `OutsideEnd` placerar etiketten precis utanför slutet på varje stapel eller kolumn, vilket förbättrar läsbarheten.  
* `HorizontalAlignment.Center` håller texten centrerad över punkten, medan `VerticalAlignment.Top` justerar etikettens övre kant med datapunkten, vilket förhindrar överlappning med andra element.

### Proffstips
Om ett diagram har flera serier, loopa igenom `chart.Series` och tillämpa samma inställningar på varje `DataLabelCollection`. Detta säkerställer ett enhetligt utseende i hela diagrammet.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Steg 5: Spara det modifierade dokumentet

Efter att ha justerat etiketterna, skriv ändringarna till en ny fil. Detta slutför processen för **ändra diagrametikettens position**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

När du öppnar `output.docx` kommer du att se att varje diagrametikett har flyttats till den yttre slutet av sin datapunkt, centrerad horisontellt och justerad till toppen vertikalt.

## Kantfall och variationer

| Situation | Vad du bör hålla utkik efter | Rekommenderad metod |
|-----------|------------------------------|---------------------|
| **Flera diagram** i samma dokument | `GetChild` returnerar bara det första diagrammet. | Använd `doc.GetChildNodes(NodeType.Shape, true)` för att iterera över alla diagramformer. |
| **Serier utan datatetiketter** | `DataLabelCollection` kan vara tom. | Kontrollera `series.HasDataLabels` innan du åtkommer samlingen. |
| **Olika diagramtyper** (cirkeldiagram, linjediagram, spridningsdiagram) | Inte alla `DataLabelPosition`‑värden är giltiga. | Använd `DataLabelPosition.Auto` för diagram som automatiskt bestämmer bästa placering. |
| **Lokalisering** | Justeringskonstanter är språkoberoende, men den renderade texten kan behöva stöd för höger‑till‑vänster. | Ange `dataLabel.TextDirection` om du behöver RTL‑språk. |

## Komplett, körbart exempel

Nedan är hela programmet som du kan kopiera, klistra in och köra. Ersätt `YOUR_DIRECTORY` med en faktisk mappväg.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Förväntat resultat:** När du öppnar `output.docx` visas varje diagrametikett placerad utanför datapunkten, centrerad horisontellt och justerad till toppen – exakt den effekt du scripted med **programmera justering av diagrametiketter**.

## Slutsats

Du vet nu hur du **programmerar justering av diagrametiketter** i ett Word‑dokument med C#. Handledningen täckte:

* Laddning av ett dokument med **Aspose.Words diagrammanipulation**  
* Åtkomst till en **C# diagramdatatetikett**  
* Ändring av **ändra diagrametikettens position** och justering  
* Spara filen och hantera vanliga kantfall  

Härifrån kan du utforska mer avancerade scenarier, såsom att anpassa etikettfonter, lägga till villkorlig formatering eller uppdatera flera diagram i en batch‑process. Experimentera med de olika `DataLabelPosition`‑alternativen för att hitta den stil som bäst passar dina rapporter.

---

*Redo att förbättra din automatiserade rapporteringspipeline? Prova att lägga till anpassade talformat till etiketterna eller exportera diagrammet som en bild för användning i PDF‑filer.*

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Ställ in enhetliga datatetiketter i ett stapeldiagram med Aspose.Words för .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Ställ in standardalternativ för datatetiketter i ett diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Uppdatera diagramseriedata i ett Word‑dokument med Aspose.Words för .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}