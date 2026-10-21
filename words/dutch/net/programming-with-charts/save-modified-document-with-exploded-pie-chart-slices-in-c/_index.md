---
category: general
date: 2026-10-13
description: 'Sla het gewijzigde document op na het aanpassen van een taartdiagram:
  explodeer segmenten, wijzig de hoek van het eerste segment en toon percentage‑labels
  in C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: nl
lastmod: 2026-10-13
og_description: Sla het gewijzigde document op na het aanpassen van een taartdiagram
  in C#. Leer hoe je taartdiagramsegmenten kunt laten exploderen, de hoek van het
  eerste segment kunt wijzigen en procentuele labels kunt weergeven.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Opslaan van aangepast document met uitgepofte taartdiagramsegmenten – C#‑gids
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
title: Aangepast document opslaan met uitgepofte taartdiagramsegmenten in C#
url: /nl/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Document opslaan met uitgepofte taartdiagramsegmenten in C#

Als je **save modified document** moet opslaan na het aanpassen van een Word-taartdiagram, laat deze gids je precies zien hoe. Je leert taartdiagramsegmenten uitpuffen, de hoek van het eerste segment wijzigen en percentage‑labels weergeven — allemaal met een paar regels C#‑code.

Grafieken aanpassen is een veelvoorkomende eis bij het programmatisch genereren van rapporten, facturen of dashboards. Aan het einde van deze tutorial kun je een DOCX‑bestand laden, het uiterlijk van de grafiek wijzigen en **save modified document** klaar voor distributie.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+)
- Aspose.Words for .NET 23.10 of nieuwer (free trial of licensed copy)
- Een Word‑bestand (`input.docx`) dat een enkel taartdiagram bevat
- Visual Studio 2022 of een andere C#‑IDE

> **Tip:** Het Aspose.Words NuGet‑pakket wordt toegevoegd met `dotnet add package Aspose.Words`.

## Stap 1: Laad het Word‑document dat de grafiek bevat

De eerste stap is het openen van het bron‑DOCX‑bestand. De `Document`‑klasse vertegenwoordigt het volledige Word‑bestand in het geheugen.

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

Het laden van het document geeft je volledige toegang tot elke node, inclusief vormen die grafieken bevatten.

## Stap 2: Haal de eerste grafiekvorm uit het document

Grafieken worden opgeslagen in `Shape`‑nodes. Je kunt de eerste grafiek vinden met `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Als het document meerdere grafieken bevat, pas dan de index (`0`) aan of doorloop de collectie. Deze regel zorgt ervoor dat je een referentie hebt naar het `Chart`‑object dat je gaat wijzigen.

## Stap 3: Uitpuffen van taartdiagramsegmenten

Een segment uitpuffen scheidt het van de rest van de taart, waardoor de grafiek makkelijker leesbaar wordt. De `Explode`‑eigenschap werkt voor de hele serie.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Het instellen van `Explode` op `true` **explodes pie chart slices** voor de volledige serie, wat handig is wanneer je elk segment wilt laten opvallen.

## Stap 4: Verander de hoek van het eerste segment

Soms moet het eerste segment beginnen met een aangepaste hoek, bijvoorbeeld om te voldoen aan een ontwerprichtlijn.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

De `FirstSliceAngle`‑eigenschap **changes first slice** oriëntatie, waardoor de hele taart wordt geroteerd zodat het eerste segment begint bij 30 graden.

## Stap 5: Toon percentage‑labels op de taartsegmenten

Het weergeven van de numerieke bijdrage van elk segment is vaak vereist in rapporten. De `DataLabel.ShowPercentage`‑vlag zet de percentage‑waarden aan.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Deze stap **show percentage labels** direct op de grafiek, wat ook voldoet aan de **display percentages pie**‑eis.

## Stap 6: Sla het gewijzigde document op

Nadat alle aanpassingen zijn toegepast, sla je de wijzigingen op in een nieuw bestand. De `Save`‑methode schrijft de bijgewerkte DOCX naar de schijf.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Nu heb je een **save modified document** dat een uitgepofte taartgrafiek, een geroteerd eerste segment en zichtbare percentage‑labels bevat.

![Opslaan gewijzigd document met uitgepofte taartdiagram](/images/pie-chart-exploded.png "Opslaan gewijzigd document met uitgepofte taartdiagramsegmenten en percentage‑labels")

*De screenshot illustreert de uiteindelijke output nadat het document is opgeslagen.*

## Volledig, uitvoerbaar voorbeeld

Door de onderdelen samen te voegen, hier is het volledige programma dat je kunt copy‑paste in een console‑project:

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

### Verwacht resultaat

Het openen van `output.docx` toont een taartgrafiek waar:

- Elk segment is licht gescheiden (**exploded pie chart slices**)
- Het eerste segment begint met een offset van 30 graden (**change first slice**)
- Elk segment toont zijn bijdrage als percentage (**show percentage labels**, **display percentages pie**)
- Het bestand is **save modified document** zonder het origineel te wijzigen.

## Veelgestelde vragen en randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Wat als het document geen grafiek heeft?** | De code controleert op `null` na `GetChild`. Als er geen grafiek bestaat, kun je er één programmatisch toevoegen of afbreken met een duidelijke melding. |
| **Kan ik alleen één segment uitpuffen?** | Ja. Gebruik `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` waarbij `i` de index van het segment is. |
| **Hoe wijzig ik het label‑formaat (bijv. waarde + % weergeven)?** | Stel `chart.PieChart.DataLabel.ShowValue = true;` in en optioneel `chart.PieChart.DataLabel.ShowPercentage = true;` om beide te combineren. |
| **Wordt de grafiekstijl behouden na het opslaan?** | Aspose.Words behoudt alle styling, inclusief kleuren en lettertypen, wanneer je **save modified document**. |
| **Kan ik meerdere grafieken in hetzelfde bestand verwerken?** | Loop door alle `Shape`‑nodes met `NodeType.Shape` en filter op `shape.HasChart`. Pas dezelfde stappen toe op elke grafiek. |

## Conclusie

Je weet nu hoe je **save modified document** kunt uitvoeren na het programmatisch aanpassen van een taartgrafiek in Word. De gids behandelde het uitpuffen van taartdiagramsegmenten, het wijzigen van de hoek van het eerste segment en het tonen van percentage‑labels — waarmee wordt voldaan aan de eisen **show percentage labels**, **explode pie chart slices**, **display percentages pie**, en **change first slice**.

Vervolgens kun je overwegen om te verkennen:

- Dynamisch gegevensreeksen toevoegen (`chart.Series.Add(...)`)
- Aanpassen van de plaatsing van de legenda en grafiektitels
- Het DOCX naar PDF converteren terwijl de grafiekstijl behouden blijft

Voel je vrij om te experimenteren met verschillende hoeken, explosie‑instellingen of label‑formaten om aan je rapportagebehoeften te voldoen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Hoe een bewerkt document opslaan in C# met Aspose.Words – Stapsgewijze gids](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Grafiekreeksgegevens bijwerken in een Word‑document met Aspose.Words voor .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Kolomgrafiek invoegen in een Word‑document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}