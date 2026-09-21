---
category: general
date: 2026-09-21
description: Hoe series opmaken in een lijndiagram in Word met C#. Leer hoe je een
  Word‑document maakt, een lijndiagram invoegt en een aangepast getalformaat toepast.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: nl
lastmod: 2026-09-21
og_description: Hoe je series in een lijndiagram in Word formatteert met C#. Deze
  tutorial laat zien hoe je een Word‑document maakt, een lijndiagram invoegt en een
  aangepast getalformaat toepast.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Hoe series opmaken in een Word‑lijndiagram met C# – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Hoe series opmaken in een Word‑lijndiagram met C#
url: /nl/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe series opmaken in een Word‑lijndiagram met C#

Als je **hoe series op te maken** in een Word‑lijndiagram nodig hebt, biedt deze gids een complete, kant‑klaar‑te‑run oplossing. Je ziet hoe je **een Word‑document maakt**, **een lijndiagram invoegt** en **een aangepast getalformaat toepast** op de Y‑waarden — alles met Aspose.Words voor .NET.

Word‑automatisering wordt eenvoudig zodra je het diagramobjectmodel begrijpt. Aan het einde van deze tutorial heb je een Word‑bestand dat een lijndiagram bevat waarvan de gegevensseries worden weergegeven als percentages met twee decimalen.

## Wat je zult bereiken

* Programma­matig een leeg `.docx`‑bestand genereren.  
* Een lijndiagram van 400 × 300 punten toevoegen.  
* De eerste gegevensserie van het diagram benaderen.  
* Het opmaak‑code `#,##0.00%` toepassen zodat de Y‑waarden als percentages verschijnen.  

Er zijn geen externe tools vereist, behalve het Aspose.Words NuGet‑pakket.

## Voorvereisten

* .NET 6.0 SDK of later.  
* Visual Studio 2022 (of een andere C#‑IDE).  
* Aspose.Words for .NET 23.10 of nieuwer — installeren via `dotnet add package Aspose.Words`.  

De code werkt op Windows, Linux en macOS omdat Aspose.Words platform‑onafhankelijk is.

## Een Word‑document maken met Aspose.Words

De eerste stap is het instantiëren van een `Document`‑object. Dit object vertegenwoordigt het volledige Word‑bestand in het geheugen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Waarom dit belangrijk is*: `Document` is het toegangspunt voor alle Word‑verwerkingsbewerkingen. Zonder dit kun je geen alinea’s, tabellen of diagrammen toevoegen.

## Een lijndiagram in het document invoegen

Een `DocumentBuilder` schrijft inhoud naar het `Document`. Het aanroepen van `InsertChart` maakt een diagramvorm op de huidige pagina.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Waarom dit belangrijk is*: `InsertChart` retourneert een `Chart`‑object dat je volledige controle geeft over series, assen en opmaak. De grootte‑parameters worden uitgedrukt in punten (1 punt = 1/72 inch).

## De eerste gegevensserie benaderen

Elk diagram bevat één of meer `ChartSeries`. De eerste serie heeft index 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Waarom dit belangrijk is*: Het `ChartSeries`‑object bevat de Y‑waarden, X‑waarden en opmaakopties voor één lijn in een lijndiagram. Het wijzigen van dit object verandert de visuele weergave van de gegevens.

## Een aangepast getalformaat op de serie toepassen

De eigenschap `FormatCode` bepaalt hoe numerieke waarden worden weergegeven. Door deze in te stellen op `#,##0.00%` vertel je Word de waarden als percentages met twee decimalen te behandelen.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Waarom dit belangrijk is*: Zonder een aangepast formaat toont Word ruwe decimale getallen (bijv. `0.15`). De opmaakcode zet ze om naar `15.00%`, wat vaak vereist is in zakelijke rapporten.

## Het document opslaan en het resultaat verifiëren

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wanneer je `FormattedSeriesLineChart.docx` opent in Microsoft Word, zie je een lijndiagram waarbij de Y‑as‑labels `15.00%`, `30.00%`, `45.00%` en `60.00%` lezen. De diagramgrootte komt overeen met de afmetingen die in `InsertChart` zijn opgegeven.

### Verwachte uitvoer‑screenshot

> *Afbeelding: Een Word‑documentpagina met een lijndiagram waarvan de Y‑as‑waarden als percentages zijn opgemaakt.*  
> *(Alt‑tekst: Screenshot van een Word‑document met een lijndiagram waarvan de Y‑as‑waarden als percentages zijn opgemaakt)*

## Veelvoorkomende variaties en randgevallen

| Situatie | Aanpassing |
|----------|------------|
| **Meerdere series** | Loop door `chart.Series` en stel `FormatCode` in voor elke serie. |
| **Ander diagramtype** | Vervang `ChartType.Line` door `ChartType.Column`, `ChartType.Pie`, enz. |
| **Locale‑specifieke scheidingstekens** | Gebruik `CultureInfo`‑bewuste opmaak‑strings, bv. `"# ##0,00 %"` voor Franse locales. |
| **Dynamische gegevensbron** | Vul `series.YValues` vanuit een database of CSV‑bestand voordat je het formaat toepast. |

**Pro tip:** Pas het formaat altijd **na** het toevoegen van de Y‑waarden toe. Het eerst toepassen van het formaat en daarna de waarden toevoegen werkt ook, maar later toepassen garandeert dat het formaat wordt toegepast op de uiteindelijke dataset.

## Samenvatting

Je weet nu **hoe series op te maken** in een Word‑lijndiagram met C#. De tutorial besloeg:

* Een Word‑document maken (`create word document`).  
* Een lijndiagram invoegen (`insert line chart`, `add chart to word`).  
* De eerste serie van het diagram benaderen.  
* Een aangepast getalformaat toepassen (`apply custom number format`) om percentages weer te geven.

## Volgende stappen

* Experimenteer met verschillende `ChartType`‑waarden om te zien hoe andere visualisaties zich gedragen.  
* Voeg titels, as‑labels en legenda’s toe met `chart.Title`, `chart.AxisX.Title` en `chart.AxisY.Title`.  
* Exporteer het diagram als afbeelding (`chart.Save` met `SaveFormat.Png`) voor gebruik in web‑rapporten.

Voel je vrij dit patroon aan te passen om dashboards, financiële rapporten of elk document dat programmatisch diagrammen vereist te genereren. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}