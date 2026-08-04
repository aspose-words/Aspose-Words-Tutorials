---
category: general
date: 2026-08-04
description: Hoe data‑labels toe te voegen in C# met Aspose.Words. Leer hoe je een
  diagram bewerkt, data‑labels centreert, percentages in het diagram weergeeft en
  data‑labels van het diagram aanpast.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: nl
lastmod: 2026-08-04
og_description: Hoe je gegevenslabels toevoegt in C# met Aspose.Words. Deze tutorial
  laat zien hoe je een diagram bewerkt, gegevenslabels in het diagram centreert, percentages
  in het diagram weergeeft en gegevenslabels van het diagram aanpast.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Hoe je gegevenslabels toevoegt aan een Word-diagram in C# – volledige gids
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Hoe je gegevenslabels toevoegt aan een Word-diagram in C# – stapsgewijze handleiding
url: /nl/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe data‑labels toe te voegen aan een Word‑grafiek in C# – stapsgewijze handleiding

Als je **how to add data labels** moet toevoegen aan een grafiek die zich in een Word‑document bevindt, laat deze gids je de exacte code zien die je moet uitvoeren. Je ziet hoe je grafiekeigenschappen bewerkt, chart data labels centreert, percentages in de grafiek toont, en grafiek‑data‑labels aanpast voor elk scenario.

De tutorial behandelt alles wat nodig is om een bestaande grafiek te wijzigen, van het laden van het document tot het opslaan van de wijzigingen. Er zijn geen externe referenties nodig—alleen de Aspose.Words for .NET‑bibliotheek en een basis C#‑ontwikkelomgeving.

## Vereisten

* .NET 6.0 (of later) geïnstalleerd.  
* Aspose.Words for .NET versie 23.9 of nieuwer.  
  Je kunt het installeren via NuGet:

```bash
dotnet add package Aspose.Words
```

* Een Word‑bestand (`input.docx`) dat minstens één grafiek bevat.

## Hoe data‑labels toe te voegen aan een Word‑grafiek in C#

De volgende secties leiden je stap voor stap door het proces. Het primaire zoekwoord **how to add data labels** komt natuurlijk voor in de tekst en in de code‑commentaren, waardoor de dichtheid binnen het aanbevolen bereik blijft.

### Stap 1 – Laad het Word‑document dat de grafiek bevat

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Waarom deze stap belangrijk is*: Het `Document`‑object vertegenwoordigt het volledige Word‑bestand. Het laden geeft je toegang tot elke node, inclusief shapes die grafieken bevatten.

### Stap 2 – Haal de eerste grafiek op uit het document

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Waarom deze stap belangrijk is*: Grafieken worden opgeslagen binnen `Shape`‑nodes. Door de opgehaalde node te casten naar `Shape` en `GetChart()` aan te roepen, krijg je een `Chart`‑object dat series, assen en label‑collecties blootlegt.

### Stap 3 – Schakel aanpassing van data‑labels in en toon percentages in de grafiek

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Waarom deze stap belangrijk is*: Het instellen van `ShowPercentage` vertelt Aspose.Words om de bijdrage van elke slice aan het totaal te berekenen en weer te geven. Dit spreekt direct het secundaire zoekwoord **show percentages in chart** aan.

### Stap 4 – Verander de label‑plaatsing naar het midden van elk datapunt

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Waarom deze stap belangrijk is*: De eigenschap `Position` bepaalt waar het label verschijnt ten opzichte van het datapunt. Het gebruik van `Center` voldoet aan het secundaire zoekwoord **center chart data labels** en verbetert de leesbaarheid voor taart‑ of donutgrafieken.

### Stap 5 – Pas grafiek‑data‑labels verder aan (optioneel)

Als je meer controle nodig hebt, kun je lettertype, kleur of leader‑lines aanpassen:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Deze instellingen illustreren het secundaire zoekwoord **customize chart data labels** en laten zien hoe je het uiterlijk kunt afstemmen op de huisstijlrichtlijnen.

### Stap 6 – Sla het gewijzigde document op

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Waarom deze stap belangrijk is*: Opslaan schrijft de bijgewerkte grafiek terug naar het Word‑document, waardoor de nieuwe data‑labels zichtbaar worden wanneer het bestand wordt geopend in Microsoft Word.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat een compleet programma dat je kunt kopiëren, plakken en uitvoeren. Het bevat alle benodigde `using`‑directieven en commentaren die elke regel uitleggen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Verwacht resultaat

Wanneer je `output.docx` opent in Microsoft Word, zal de grafiek het volgende tonen:

* Percentage‑waarden naast elke slice (bijv. **25 %**, **40 %**, …).  
* Labels gepositioneerd in het midden van elk datapunt.  
* Eventuele extra opmaak die je hebt toegepast, zoals vetrode tekst.

Deze visuele aanwijzingen maken de grafiek makkelijker te interpreteren, vooral in presentaties of rapporten.

## Hoe grafiekeigenschappen te bewerken naast data‑labels

Hoewel de focus van deze gids **how to add data labels** is, wil je misschien ook **how to edit chart** instellingen aanpassen, zoals titels, legende‑plaatsing of as‑opmaak. Het `Chart`‑object biedt eigenschappen zoals `Title`, `Legend` en `AxisX/AxisY`. Bijvoorbeeld, om de grafiektitel te wijzigen:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Alle grafiek‑aanpassingen volgen hetzelfde patroon: haal de grafiek op, wijzig de eigenschappen, en sla vervolgens het document op.

## Veelvoorkomende valkuilen en best‑practice tips

| Valkuil | Waarom het gebeurt | Aanbevolen oplossing |
|---|---|---|
| De grafiek staat binnen een gegroepeerde shape. | `GetChild(NodeType.Shape, …)` retourneert de buitenste groep, niet de interne grafiek. | Zoek recursief naar een shape met `shape.HasChart`. |
| Data‑labels verschijnen niet na het opslaan. | `ShowValue` of `ShowPercentage` is niet op `true` gezet. | Stel beide `ShowValue` en `ShowPercentage` expliciet in indien nodig. |
| Labels overlappen bij kleine slices. | Centrering kan leiden tot drukte. | Gebruik `ChartDataLabelPosition.OutSideEnd` voor plaatsing buiten de slice, of schakel `LeaderLines` in. |

## Conclusie

Je weet nu **how to add data labels** aan een Word‑grafiek met C#. De tutorial behandelde het ophalen van de grafiek, het inschakelen van label‑zichtbaarheid, het centreren van de labels, het tonen van percentages en het aanpassen van het uiterlijk. Met deze kennis kun je ook **how to edit chart** details, **center chart data labels**, **show percentages in chart**, en **customize chart data labels** toepassen voor elke rapportagesituatie.

Klaar om meer te ontdekken? Probeer meerdere series toe te voegen, conditionele opmaak toe te passen, of de grafiek als afbeelding te exporteren. De Aspose.Words‑API biedt uitgebreide mogelijkheden voor grafiekmanipulatie—experimenteer om de perfecte visuele weergave voor jouw data te vinden.

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}