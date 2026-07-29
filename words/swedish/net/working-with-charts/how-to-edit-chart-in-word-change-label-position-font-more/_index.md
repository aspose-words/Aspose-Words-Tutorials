---
category: general
date: 2026-07-29
description: Hur du redigerar diagram i ett Word‑dokument – lär dig att ändra diagrammets
  etikettposition, justera stapeldiagrametiketter, modifiera diagrammets datamärkningar
  och ändra diagrammets teckensnitt för etiketter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: sv
lastmod: 2026-07-29
og_description: Hur man redigerar diagram i Word snabbt. Behärska att ändra diagrammets
  etikettposition, justera stapeldiagrametiketter, modifiera diagrammets datamärkningar
  och ändra diagrammets etikettteckensnitt.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Hur man redigerar diagram i Word – Ändra etiketter och teckensnitt
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Hur man redigerar diagram i Word: Ändra etikettposition, teckensnitt och mer'
url: /sv/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så redigerar du diagram i Word: Ändra etikettposition, teckensnitt och mer

Att redigera diagram i ett Word‑dokument är ett vanligt behov när du vill att dina rapporter ska se professionella ut. Har du någonsin haft problem med att **ändra diagrametikettens position** eller göra etiketterna läsbara utan att gräva igenom ändlösa menyer? Du är inte ensam – de flesta utvecklare stöter på detta när de automatiserar rapportgenerering. I den här guiden går vi igenom ett komplett, körbart exempel som visar exakt hur du **justerar stapeldiagrametiketter**, **modifierar diagramdatamärkningar** och **ändrar diagrametikettens teckensnitt** med C# och Aspose.Words‑biblioteket.

## Vad du kommer att lära dig

- Ladda en .docx‑fil som redan innehåller ett stapeldiagram.  
- Hämta den första diagramformen och komma åt dess datamärkningssamling.  
- **Ändra diagrametikettens position** för att få staplarna att se renare ut.  
- **Justera stapeldiagrametiketter** teckenstorlek för bättre läsbarhet.  
- Spara det modifierade dokumentet tillbaka till disk.  

Inga externa verktyg, inga manuella UI‑steg – bara ren kod som du kan släppa in i vilket .NET‑projekt som helst. När du är klar har du en självständig lösning som du kan återanvända i dussintals dokument.

> **Förutsättningar**  
> - .NET 6.0 eller senare (koden fungerar också på .NET Framework 4.7+).  
> - Aspose.Words för .NET (tillgängligt via NuGet).  
> - En Word‑fil (`BarChart.docx`) som redan innehåller ett stapeldiagram.  

Om du saknar någon av dessa, hämta det senaste Aspose.Words‑paketet nu:

```bash
dotnet add package Aspose.Words
```

---

## Så redigerar du diagram: Hämta diagrammet från Word‑dokumentet

Det första steget i **hur man redigerar diagram**‑objekt är att ladda dokumentet och lokalisera diagramformen. Aspose.Words behandlar diagram som `Shape`‑noder, så vi kan använda `GetChild` med `NodeType.Shape` för att hämta det första diagram vi stöter på.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Varför detta är viktigt:**  
> Genom att direkt komma åt `Chart`‑objektet undviker du kostnaden för att öppna filen i Word och manuellt justera varje etikett. Detta är hörnstenen i all **modifiera diagramdatamärkningar**‑automation.

## Justera stapeldiagrametiketter: Ändra diagrametikettens position

Nu när vi har `Chart`‑instansen, låt oss iterera över dess `DataLabelCollection`. Målet är att **ändra diagrametikettens position** så att varje etikett sitter snyggt inuti basen på sin stapel, istället för att sväva obekvämt ovanför den.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Proffstips:**  
> `InsideBase` fungerar bra för vertikala stapeldiagram. Om du arbetar med ett horisontellt stapeldiagram, prova `InsideEnd` istället. Att experimentera med positioner är billigt – kör bara om koden och öppna det sparade dokumentet.

## Ändra diagrametikettens teckensnitt: Justera teckenstorlek för läsbarhet

Ett litet teckensnitt är den tysta mördaren av rapportklarhet. För att **ändra diagrametikettens teckensnitt**, sätt helt enkelt `Font.Size`‑egenskapen på varje `ChartDataLabel`. Vi höjer den till 9 pt, vilket är en bra kompromiss för de flesta utskrivna rapporter.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Varför vi gör detta:**  
> Att justera teckenstorleken är en del av **modifiera diagramdatamärkningar**‑bästa praxis. Större teckensnitt förbättrar tillgängligheten och minskar behovet av manuell efterbehandling.

## Spara det uppdaterade dokumentet

Efter att ha justerat positioner och teckensnitt är det sista steget i **hur man redigerar diagram** att persistera förändringarna. Aspose.Words gör detta med en enda rad kod.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Öppna `BarChartCustomLabels.docx` i Word så ser du att etiketterna sitter tätt inuti staplarna, renderade med ett tydligt 9 pt‑teckensnitt. Inga fler ansträngda blickar på små siffror.

---

## Fullt fungerande exempel (Alla steg i en fil)

Nedan hittar du ett komplett, körbart konsolprogram som demonstrerar hela flödet – från att ladda dokumentet till att spara den uppdaterade versionen. Kopiera och klistra in det i ett nytt .NET‑konsolprojekt och tryck **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Förväntad utskrift** när du kör programmet:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Öppna den resulterande filen så ser du **justera stapeldiagrametiketter** placerade inuti staplarna med en bekväm teckenstorlek.

---

## Vanliga frågor & kantfall

### Vad händer om dokumentet innehåller flera diagram?

Koden ovan hämtar det *första* diagrammet (`GetChild(NodeType.Shape, 0, true)`). För att redigera alla diagram, ersätt den enkla hämtningen med en loop:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Hur ändrar man **diagrametikettens teckensnitt** för en specifik serie endast?

Varje `ChartSeries` har sin egen `DataLabelCollection`. Rikta in dig på en serie via index:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Fungerar detta med paj‑ eller linjediagram?

Ja – `ChartDataLabelPosition` stödjer värden som `InsideEnd`, `OutsideEnd` och `BestFit`. För ett pajdiagram kan du föredra `OutsideEnd` för att hålla etiketterna läsbara.

### Vad gäller lokalisering (t.ex. olika decimalavgränsare)?

Aspose.Words respekterar dokumentets språkinställningar. Om du behöver påtvinga ett specifikt format, justera `label.NumberFormat` innan du sparar.

---

## Sammanfattning & nästa steg

Vi har gått igenom **hur man redigerar diagram**‑objekt i ett Word‑dokument från början till slut: ladda filen, hämta diagrammet, **ändra diagrametikettens position**, **justera stapeldiagrametiketter**, **modifiera diagramdatamärkningar** och slutligen **ändra diagrametikettens teckensnitt** innan vi sparar. Det kompletta exemplet är produktionsklart och kan släppas in i vilken automatiseringspipeline som helst.

Redo att ta nästa steg? Överväg dessa uppföljningsidéer:

- **Lägg till färg på datamärkningar** (`dataLabel.Font.Color = Color.Blue;`).  
- **Visa värden som procent** (`dataLabel.NumberFormat = "0%";`).  
- **Skapa diagram programatiskt** istället för att ladda befintliga.  

Alla dessa bygger på samma API‑ytor som vi använde idag, så du kommer känna dig hemma.

Om du stöter på problem, lämna en kommentar nedan eller kolla in Aspose.Words‑dokumentationen för djupare diagram‑anpassningsalternativ. Lycka till med kodningen, och njut av vackert märkta diagram!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närliggande ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Anpassa diagramdatamärkning](/words/english/net/programming-with-charts/chart-data-label/)
- [Formatera antal i diagramdatamärkning](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Diagramdatamärkning](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}