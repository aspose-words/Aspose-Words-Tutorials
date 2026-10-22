---
category: general
date: 2026-10-13
description: 'Spara det modifierade dokumentet efter att ha anpassat ett cirkeldiagram:
  spränga ut segment, ändra första segmentets vinkel och visa procentetiketter i C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: sv
lastmod: 2026-10-13
og_description: Spara det modifierade dokumentet efter att ha anpassat ett pajdiagram
  i C#. Lär dig hur du exploderar sektorer i pajdiagrammet, ändrar vinkeln för den
  första sektorn och visar procentetiketter.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Spara modifierat dokument med utspridda sektorer i cirkeldiagram – C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Spara modifierat dokument med utbrytna pajdiagramdelar i C#
url: /sv/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara modifierat dokument med utspridda pajdiagramdelar i C#

Om du behöver **save modified document** efter att ha justerat ett Word-pajdiagram, visar den här guiden exakt hur du gör. Du kommer att lära dig att spränga pajdiagramdelar, ändra den första delens vinkel och visa procentetiketter — allt med några rader C#-kod.

Att anpassa diagram är ett vanligt krav när man genererar rapporter, fakturor eller instrumentpaneler programatiskt. I slutet av den här handledningen kommer du att kunna läsa in en DOCX-fil, ändra diagrammets utseende och **save modified document** klar för distribution.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 eller nyare (gratis provversion eller licensierad kopia)
- En Word‑fil (`input.docx`) som innehåller ett enda pajdiagram
- Visual Studio 2022 eller någon C#‑IDE

> **Tips:** Aspose.Words NuGet‑paketet läggs till med `dotnet add package Aspose.Words`.

## Steg 1: Läs in Word-dokumentet som innehåller diagrammet

Det första steget är att öppna källdokumentet DOCX. Klassen `Document` representerar hela Word-filen i minnet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

När du läser in dokumentet får du full åtkomst till varje nod, inklusive former som innehåller diagram.

## Steg 2: Hämta den första diagramformen från dokumentet

Diagram lagras i `Shape`‑noder. Du kan hitta det första diagrammet med `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Om dokumentet innehåller flera diagram, justera indexet (`0`) eller iterera genom samlingen. Den här raden säkerställer att du har en referens till `Chart`‑objektet som du ska modifiera.

## Steg 3: Spränga pajdiagramdelar

Att spränga en del separerar den från resten av pajen, vilket gör diagrammet lättare att läsa. `Explode`‑egenskapen fungerar för hela serien.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Genom att sätta `Explode` till `true` **explodes pie chart slices** för hela serien, vilket är användbart när du vill att varje del ska sticka ut.

## Steg 4: Ändra den första delens vinkel

Ibland behöver du att den första delen börjar vid en anpassad vinkel, till exempel för att följa en designriktlinje.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

`FirstSliceAngle`‑egenskapen **changes first slice** orientering, roterar hela pajen så att den första delen börjar vid 30 grader.

## Steg 5: Visa procentetiketter på pajdelarna

Att visa den numeriska andelen för varje del krävs ofta i rapporter. Flaggan `DataLabel.ShowPercentage` aktiverar procentvärden.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Detta steg **show percentage labels** direkt på diagrammet, vilket också uppfyller kravet **display percentages pie**.

## Steg 6: Spara det modifierade dokumentet

När alla anpassningar har tillämpats, spara förändringarna till en ny fil. Metoden `Save` skriver den uppdaterade DOCX-filen till disk.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Nu har du ett **save modified document** som innehåller ett sprängt pajdiagram, en roterad första del och synliga procentetiketter.

![Spara modifierat dokument som visar utspridda pajdiagramdelar](/images/pie-chart-exploded.png "Spara modifierat dokument med utspridda pajdiagramdelar och procentetiketter")

*Skärmdumpen illustrerar slutresultatet efter att dokumentet har sparats.*

## Fullt, körbart exempel

När du sätter ihop delarna, här är det kompletta programmet som du kan kopiera‑och‑klistra in i ett konsolprojekt:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Förväntat resultat

När du öppnar `output.docx` visas ett pajdiagram där:

- Varje del är något separerad (**exploded pie chart slices**)
- Den första delen börjar med ett 30‑graders offset (**change first slice**)
- Varje del visar sitt bidrag som en procentandel (**show percentage labels**, **display percentages pie**)
- Filen har blivit **save modified document** utan att ändra originalet.

## Vanliga frågor och edge‑cases

| Fråga | Svar |
|----------|--------|
| **Vad händer om dokumentet saknar diagram?** | Koden kontrollerar `null` efter `GetChild`. Om inget diagram finns kan du antingen lägga till ett programatiskt eller avbryta med ett tydligt meddelande. |
| **Kan jag spränga bara en enskild del?** | Ja. Använd `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` där `i` är delens index. |
| **Hur ändrar jag etikettformatet (t.ex. visa värde + %)?** | Sätt `chart.PieChart.DataLabel.ShowValue = true;` och eventuellt `chart.PieChart.DataLabel.ShowPercentage = true;` för att kombinera båda. |
| **Behålls diagramstilen efter sparning?** | Aspose.Words behåller all styling, inklusive färger och typsnitt, när du **save modified document**. |
| **Kan jag bearbeta flera diagram i samma fil?** | Loopa igenom alla `Shape`‑noder med `NodeType.Shape` och filtrera på `shape.HasChart`. Applicera samma steg på varje diagram. |

## Slutsats

Du vet nu hur du **save modified document** efter att programatiskt ha anpassat ett pajdiagram i Word. Guiden täckte att spränga pajdiagramdelar, ändra den första delens vinkel och visa procentetiketter — vilket uppfyller kraven **show percentage labels**, **explode pie chart slices**, **display percentages pie** och **change first slice**.

Nästa, överväg att utforska:

- Lägga till dataserier dynamiskt (`chart.Series.Add(...)`)  
- Anpassa legendplacering och diagramrubriker  
- Konvertera DOCX till PDF samtidigt som diagramstilen bevaras  

Känn dig fri att experimentera med olika vinklar, spränginställningar eller etikettformat för att matcha dina rapporteringsbehov. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

De följande handledningarna täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Hur man sparar redigerat dokument i C# med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Uppdatera diagramseriedata i ett Word-dokument med Aspose.Words för .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Infoga stapeldiagram i ett Word-dokument](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}