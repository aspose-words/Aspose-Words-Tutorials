---
category: general
date: 2026-07-20
description: Voeg taartdiagramlabels toe met Aspose.Words voor .NET. Leer hoe je taartdiagramlabels
  kunt wijzigen, percentage‑labels kunt weergeven en diagramreekslabels snel kunt
  bijwerken.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: nl
lastmod: 2026-07-20
og_description: Voeg taartdiagramlabels toe in C# met Aspose.Words. Beheers het wijzigen
  van taartdiagramlabels, het weergeven van percentage‑labels en het bijwerken van
  diagramreekslabels in slechts een paar stappen.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Voeg taartdiagramlabels toe in C# – Aspose.Words volledige tutorial
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
title: Voeg taartdiagramlabels toe in C# met Aspose.Words – Complete gids
url: /nl/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Voeg taartdiagramlabels toe in C# met Aspose.Words – Complete Gids

Moet je **taartdiagramlabels** toevoegen aan een Word‑document met C#? Met Aspose.Words kun je moeiteloos **taartdiagramlabels wijzigen** en **taartdiagrampercentages weergeven** direct in het bestand—zonder handmatig in Word te knoeien.  

In deze tutorial lopen we stap voor stap door hoe je **percentage‑labels weergeeft**, ze verplaatst, en zelfs **diagramreeks‑labels bijwerkt** voor dynamische data. Aan het einde heb je een herbruikbare code‑snippet die je in elk .NET‑project kunt gebruiken.

> **Snelle preview:** Na het volgen van de gids zie je bij het openen van het opgeslagen `.docx`‑bestand een taartdiagram waarbij elke partitie gelabeld is met zijn percentage, buiten de partitie geplaatst voor maximale leesbaarheid.

---

## Wat je nodig hebt

- **Aspose.Words for .NET** (de nieuwste versie van 2026). Haal het op via NuGet: `Install-Package Aspose.Words`.
- Een **Word‑document** dat al een taart‑ of donut‑diagram bevat (we noemen het `Chart.docx`).
- Basiskennis van **C#** en Visual Studio (of je favoriete IDE).

Dat is alles—geen extra libraries, geen COM‑interop, alleen pure managed code.

---

## Voeg taartdiagramlabels toe – Volledige implementatie

Hieronder staat een **volledig, uitvoerbaar** C#‑console‑programma dat een document laadt, het eerste taartdiagram wijzigt en het resultaat opslaat. Elke regel is becommentarieerd zodat je begrijpt **waarom** we iets doen, niet alleen **wat** we doen.

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

### Verwacht resultaat

Open `ChartWithCustomLabels.docx` in Microsoft Word. Je zou het taartdiagram **met percentage‑labels buiten elke partitie** moeten zien. De labels zien er ongeveer zo uit: “35 %”, “20 %”, enz., waardoor het diagram direct begrijpelijk is.

---

## Wijzig taartdiagramlabels: positionering en opmaak

Als je alleen **taartdiagramlabels wilt wijzigen** zonder percentages te tonen, kun je de eigenschap `Position` aanpassen naar een van de volgende waarden:

| Position‑Enum | Visueel effect |
|---------------|----------------|
| `InsideEnd`   | Labels staan binnen de partitie, precies aan de rand. |
| `Center`      | Labels verschijnen in het midden van de partitie (handig voor kleine taarten). |
| `OutsideEnd`  | Labels staan buiten de partitie, verbonden met een lijn (onze standaard). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Pro‑tip:** `OutsideEnd` werkt het beste wanneer het diagram veel partities heeft; het voorkomt overlappende tekst.

---

## Toon percentage‑labels op een taartdiagram

De eigenschap `ShowPercentage` is een **boolean‑vlag**. Deze op `true` zetten vertelt Aspose.Words om de bijdrage van elke partitie te berekenen op basis van de onderliggende gegevensbron.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Je kunt het ook combineren met `ShowValue` als je zowel ruwe getallen **als** percentages nodig hebt:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Wanneer beide vlaggen zijn ingeschakeld, ziet het label er zo uit: “45 % (120)”.

---

## Werk diagramreeks‑labels bij voor dynamische data

Vaak genereer je diagrammen on‑the‑fly—bijvoorbeeld maandelijkse verkoopcijfers of enquête‑resultaten. Om **diagramreeks‑labels** programmatisch bij te werken, wijzig je de `Series`‑collectie voordat je de gegevenslabels aanpast:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Deze snippet laat zien hoe je **diagramreeks‑labels** bijwerkt voor elke reeks, niet alleen de eerste. Handig wanneer je rapporten bouwt die feitelijke versus prognose‑data combineren.

---

## Randgevallen & Veelvoorkomende valkuilen

| Situatie | Waar je op moet letten | Oplossing |
|----------|------------------------|-----------|
| **Diagram is geen taart/donut** | `Position` heeft mogelijk geen visueel effect. | Controleer of `chart.Type` `ChartType.Pie` of `ChartType.Doughnut` is. |
| **Geen diagram gevonden** | `GetChild` retourneert `null`. | Voeg een guard‑clausule toe (zie code) en log een nuttig bericht. |
| **Oudere Word‑versie** | Sommige label‑functies worden genegeerd. | Sla op als `.docx` (het moderne formaat) om volledige ondersteuning te garanderen. |
| **Groot aantal partities** | Labels kunnen overlappen zelfs met `OutsideEnd`. | Overweeg het aantal partities te verminderen of de diagramgrootte te vergroten. |

---

## Volledig werkend voorbeeld (Kopie‑en‑Plak)

Hieronder staat het **volledige programma** dat je kunt kopiëren naar een nieuw console‑project. Vervang `YOUR_DIRECTORY` door de map die `Chart.docx` bevat.



## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Standaardopties voor gegevenslabels in een diagram instellen](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Enkele diagramreeks aanpassen in een diagram](/words/english/net/programming-with-charts/single-chart-series/)
- [Kolomdiagram invoegen in Word met Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}