---
category: general
date: 2026-08-04
description: Aangepaste plaatsing van gegevenslabels voor diagrammen in C# stelt je
  in staat om labels te centreren op diagramsegmenten. Volg deze stapsgewijze handleiding
  met behulp van de Aspose.Words diagram-API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: nl
lastmod: 2026-08-04
og_description: Aangepaste plaatsing van gegevenslabels voor grafieken in C# laat
  zien hoe je alle gegevenslabels centreert op elk segment van een Word‑grafiek. Beheers
  de positionering van grafiek‑gegevenslabels met Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Aangepaste plaatsing van datalabels voor grafieken in C# – stapsgewijze
  handleiding
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
title: Aangepaste plaatsing van gegevenslabels voor grafieken in C#
url: /nl/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aangepaste gegevens‑labelplaatsing voor diagrammen in C#

**Custom Data‑Label Placement for Charts** stelt je in staat om precies te bepalen waar elk label verschijnt op een diagram in een Word‑document. In deze tutorial leer je hoe je alle gegevenslabels op elke partitie centreert met C# en de Aspose.Words chart‑API.

Je krijgt een volledig, uitvoerbaar voorbeeld dat een `.docx`‑bestand laadt, de eerste diagramvorm opent, de `Position` van elk label wijzigt naar `Center`, en het bijgewerkte document opslaat. Er zijn geen externe referenties nodig—alleen de Aspose.Words for .NET‑bibliotheek en een basis C#‑ontwikkelomgeving.

**Wat je leert**

* Hoe je een Word‑document laadt dat een diagram bevat.  
* Hoe je de diagramvorm vindt met de Aspose.Words chart‑API.  
* Hoe je **chart data label positioning** toepast op elke serie in het diagram.  
* Hoe je het document opslaat zodat de gecentreerde labels in Word verschijnen.  

**Voorvereisten**

* .NET 6.0 (of later) geïnstalleerd.  
* Visual Studio 2022 (of een andere C#‑IDE).  
* Een referentie naar het `Aspose.Words` NuGet‑pakket.  
* Een Word‑bestand (`Chart.docx`) dat ten minste één diagram bevat.

---

## Aangepaste gegevens‑labelplaatsing voor diagrammen – stap 1: het document laden

De eerste stap is het openen van het Word‑bestand dat het diagram bevat. `Document` is het startpunt voor elke manipulatie met Aspose.Words.

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

*Waarom deze stap belangrijk is*: Zonder het document te laden kun je het diagramobject niet bereiken. De validatie zorgt ervoor dat je een duidelijke foutmelding krijgt als het bestand geen diagram bevat, waardoor een null‑reference later wordt voorkomen.

---

## De Aspose.Words chart‑API gebruiken om diagramvormen te benaderen

Aspose.Words beschouwt een diagram als een `Chart`‑object genest binnen een `Shape`. Je haalt het op door het juiste kindknooppunt te casten.

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

*Waarom deze stap belangrijk is*: Directe toegang tot `Chart` geeft je volledige controle over series, gegevenspunten en label‑eigenschappen. Als de vorm geen diagram is, stopt de code vroegtijdig met een informatieve melding.

---

## Instellen van diagramgegevens‑labelpositie in C#

Itereer nu door elke serie en elk gegevenslabel, en stel de `Position` in op `Center`. Dit is de kern van **Custom Data‑Label Placement for Charts**.

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

**Pro tip**: Als je een andere plaatsing nodig hebt (bijv. `InsideEnd` voor een kolomdiagram), wijzig dan de enum‑waarde dienovereenkomstig. De `ChartDataLabelPosition`‑enum bevat alle standaardposities die Word ondersteunt.

*Waarom deze stap belangrijk is*: Het wijzigen van `label.Position` werkt de onderliggende OOXML‑representatie bij, zodat het label gecentreerd verschijnt wanneer het document wordt geopend in Microsoft Word.

---

## Het Word‑document opslaan met bijgewerkte labels

Na het aanpassen van het diagram, sla je de wijzigingen op in een bestand. Je kunt het origineel overschrijven of een nieuwe kopie maken.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Waarom deze stap belangrijk is*: Opslaan schrijft de bijgewerkte OOXML naar schijf. Het openen van `ChartLabelsCentered.docx` in Word toont elk partitieslabel gecentreerd, wat bevestigt dat **Custom Data‑Label Placement for Charts** geslaagd is.

---

## Randgevallen en variaties

| Situatie | Hoe te handelen |
|-----------|-----------------|
| **Meerdere diagrammen** in hetzelfde document | Loop over `doc.GetChildNodes(NodeType.Shape, true)` en controleer `shape.HasChart` voor elke vorm. |
| **Verschillende diagramtypen** (taart, donut, staaf) | Dezelfde `ChartDataLabelPosition.Center` werkt voor taart‑type diagrammen. Voor staaf‑/kolomdiagrammen kun je `InsideEnd` of `OutsideEnd` verkiezen. |
| **Labeltekst moet worden opgemaakt** | Benader `label.TextProperties` om lettergrootte, kleur of vetgedrukt in te stellen. |
| **Uitvoeren op .NET Core** | Zorg ervoor dat je de .NET Standard‑versie van Aspose.Words referereert; de API is identiek. |

---

## Volledig werkend voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑en‑plakken in een console‑applicatie. Het bevat alle benodigde `using`‑directieven en foutafhandeling.

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

**Verwacht resultaat**: Open `ChartLabelsCentered.docx` in Microsoft Word. Elke partitie van het diagram toont nu zijn gegevenslabel direct in het midden van de partitie, wat een nettere weergave oplevert.

---

## Conclusie

Je hebt nu een volledige **Custom Data‑Label Placement for Charts**‑oplossing in C#. Door het document te laden, het diagram via de Aspose.Words chart‑API te benaderen, `ChartDataLabelPosition.Center` voor elk label in te stellen en het bestand op te slaan, kun je de label‑plaatsing automatiseren voor elk Word‑gebaseerd diagram.

Verken vervolgens andere **chart data label positioning**‑opties zoals `InsideEnd` of `OutsideEnd`, of experimenteer met **C# chart manipulation** om kleuren te wijzigen, legenda’s toe te voegen of diagrammen vanaf nul te genereren. Deze uitbreidingen bouwen direct voort op de hier behandelde technieken en breiden je vaardigheden in Word‑documentdiagram‑automatisering uit. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Grafiekgegevenslabel aanpassen](/words/english/net/programming-with-charts/chart-data-label/)
- [Aantal gegevenslabels in een diagram opmaken](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Diagramgegevenslabel](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}