---
category: general
date: 2026-07-20
description: Lägg till cirkeldiagrametiketter med Aspose.Words för .NET. Lär dig hur
  du ändrar cirkeldiagrametiketter, visar procentetiketter och snabbt uppdaterar diagramseriens
  etiketter.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: sv
lastmod: 2026-07-20
og_description: Lägg till pajdiagrametiketter i C# med Aspose.Words. Behärska ändring
  av pajdiagrametiketter, visa procentetiketter och uppdatera diagramseriens etiketter
  på bara några steg.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Lägg till etiketter för cirkeldiagram i C# – Aspose.Words fullständig handledning
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Lägg till cirkeldiagrametiketter i C# med Aspose.Words – Komplett guide
url: /sv/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lägg till pajdiagrametiketter i C# med Aspose.Words – Komplett guide

Behöver du **lägga till pajdiagrametiketter** i ett Word‑dokument med C#? Med Aspose.Words kan du enkelt **ändra pajdiagrametiketter** och **visa pajdiagramprocent** direkt i filen—ingen manuell justering i Word behövs.  

I den här handledningen går vi igenom de exakta stegen för att **visa procentetiketter**, flytta dem, och även **uppdatera diagramseriernas etiketter** för dynamiska data. I slutet har du ett återanvändbart kodsnutt som du kan lägga in i vilket .NET‑projekt som helst.

> **Snabb förhandsvisning:** Efter att ha följt guiden kommer öppning av den sparade `.docx` att visa ett pajdiagram där varje del är märkt med sin procent, placerad utanför delen för bästa läsbarhet.

---

## Vad du behöver

- **Aspose.Words for .NET** (den senaste versionen år 2026). Du kan hämta den från NuGet: `Install-Package Aspose.Words`.
- Ett **Word‑dokument** som redan innehåller ett paj‑ eller donut‑diagram (vi kallar det `Chart.docx`).
- Grundläggande kunskap om **C#** och Visual Studio (eller din föredragna IDE).

Det är allt—inga extra bibliotek, ingen COM‑interop, bara ren hanterad kod.

---

## Lägg till pajdiagrametiketter – Fullständig implementation

Nedan finns ett **komplett, körbart** C#‑konsolprogram som laddar ett dokument, ändrar det första pajdiagrammet och sparar resultatet. Varje rad är kommenterad så att du förstår **varför** vi gör vad vi gör, inte bara **vad**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Förväntat resultat

Öppna `ChartWithCustomLabels.docx` i Microsoft Word. Du bör se pajdiagrammet **med procentetiketter placerade utanför varje del**. Etiketterna ser ut ungefär som “35 %”, “20 %” osv., vilket gör diagrammet omedelbart förståeligt.

---

## Ändra pajdiagrametiketter: positionering och formatering

Om du bara behöver **ändra pajdiagrametiketter** utan att visa procent, kan du justera egenskapen `Position` till ett av följande:

| Position Enum | Visuell effekt |
|---------------|----------------|
| `InsideEnd`   | Etiketter sitter inne i delen, precis vid kanten. |
| `Center`      | Etiketter visas i mitten av delen (bra för små pajer). |
| `OutsideEnd`  | Etiketter är utanför delen, kopplade med en ledningslinje (vårt standardalternativ). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Proffstips:** `OutsideEnd` fungerar bäst när diagrammet har många delar; det förhindrar överlappande text.

---

## Visa procentetiketter på ett pajdiagram

Egenskapen `ShowPercentage` är en **boolean‑flagga**. Att sätta den till `true` instruerar Aspose.Words att beräkna varje parts bidrag baserat på den underliggande datakällan.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Du kan också kombinera den med `ShowValue` om du behöver både råa siffror **och** procent:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

När båda flaggorna är aktiverade ser etiketten ut som “45 % (120)”.

---

## Uppdatera diagramseriernas etiketter för dynamiska data

Ofta genererar du diagram i farten—tänk månatliga försäljningar eller enkätresultat. För att **uppdatera diagramseriernas etiketter** programatiskt, ändra `Series`‑samlingen innan du ändrar dataetiketterna:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Detta kodsnutt visar hur du **uppdaterar diagramseriernas etiketter** för vilken serie som helst, inte bara den första. Det är praktiskt när du bygger rapporter som kombinerar faktiska mot prognostiserade data.

---

## Särskilda fall & Vanliga fallgropar

| Situation | Vad att hålla utkik efter | Lösning |
|-----------|---------------------------|---------|
| **Chart isn’t a pie/doughnut** | `Position` may have no visual effect. | Verify `chart.Type` is `ChartType.Pie` or `ChartType.Doughnut`. |
| **No chart found** | `GetChild` returns `null`. | Add a guard clause (see code) and log a helpful message. |
| **Older Word version** | Some label features are ignored. | Save as `.docx` (the modern format) to guarantee full support. |
| **Large number of slices** | Labels can overlap even with `OutsideEnd`. | Consider reducing slice count or increasing chart size. |

---

## Fullt fungerande exempel (Kopiera‑klistra in)

Nedan är det **hela programmet** som du kan kopiera in i ett nytt konsolprojekt. Byt bara ut `YOUR_DIRECTORY` mot mappen som innehåller `Chart.docx`.



## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Ställ in standardalternativ för dataetiketter i ett diagram](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Anpassa enskild diagramserie i ett diagram](/words/english/net/programming-with-charts/single-chart-series/)
- [Infoga stapeldiagram i Word med Aspose.Words för .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}