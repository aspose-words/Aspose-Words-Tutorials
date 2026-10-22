---
category: general
date: 2026-10-13
description: Aspose.Words radiale grafiekvoorbeeld dat laat zien hoe graduaties op
  een radiale grafiek in te schakelen met C# en Aspose.Words 24.9+.
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
language: nl
lastmod: 2026-10-13
og_description: Aspose.Words radiale grafiekvoorbeeld dat laat zien hoe graduaties
  op een radiale grafiek in te schakelen met C# en de nieuwste 24.9+ bibliotheek.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words radiale grafiek voorbeeld – graduaties inschakelen in C#
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
title: 'Aspose.Words radiale grafiek voorbeeld: graduaties inschakelen in C#'
url: /nl/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words radiale grafiek voorbeeld: graduaties inschakelen in C#

Als je op zoek bent naar een **aspose.words radial chart example**, ben je op de juiste plek. Deze tutorial leidt je stap voor stap door het inschakelen van graduaties voor een radiale grafiek met behulp van de Aspose.Words for .NET API.

Radiale grafieken zijn handig voor het visualiseren van cyclische gegevens, zoals tijd‑van‑de‑dag‑metingen of seizoensgebonden trends. Standaard zijn de graduaties (de tick‑marks rond de cirkelvormige as) verborgen, waardoor de grafiek moeilijker leesbaar kan zijn. Ze inschakelen is een wijziging van één regel, maar je moet wel het juiste objectmodel en de versie kennen die deze functie ondersteunt.

In deze gids leer je hoe je:

* Laad een Word‑document dat al een radiale grafiek bevat.  
* Toegang tot de grafiekvorm via de Aspose.Words grafiek‑API.  
* Schakel **graduations visibility** in (beschikbaar vanaf **Aspose.Words versie 24.9**).  
* Sla het gewijzigde document op en controleer het resultaat.

De volledige, uitvoerbare code is inbegrepen, zodat je het kunt kopiëren‑plakken in een nieuw console‑project en het effect onmiddellijk kunt zien.

![Aspose.Words radiale grafiek voorbeeld met graduaties](https://example.com/images/radial-chart-graduations.png "Aspose.Words radiale grafiek voorbeeld dat graduaties ingeschakeld toont")

## Vereisten

| Requirement | Why it matters |
|-------------|----------------|
| .NET 6.0 of later | Aspose.Words for .NET 24.9+ richt zich op .NET Standard 2.0 en werkt op .NET 6+. |
| Aspose.Words for .NET **24.9** of nieuwer | De eigenschap `IsGraduationsVisible` werd geïntroduceerd in versie 24.9. Oudere releases zullen een `MissingMemberException` veroorzaken. |
| Een Word‑document (`RadialChart.docx`) dat een radiale grafiek bevat | Het voorbeeld wijzigt een bestaande grafiek; het maken van een nieuwe vanaf nul is een apart onderwerp. |
| Een C#‑IDE (Visual Studio, Rider, VS Code) | Elke IDE die .NET‑projecten kan compileren werkt. |
| NuGet‑pakket `Aspose.Words` | Installeer via `dotnet add package Aspose.Words --version 24.9.0` (of later). |

> **Pro tip:** Als je niet kunt upgraden naar 24.9, kun je nog steeds andere grafiekeigenschappen aanpassen, maar graduaties blijven verborgen omdat de API die vlag niet exposeerde.

## Aspose.Words radiale grafiek voorbeeld – stapsgewijze gids

De volgende secties splitsen het proces op in afzonderlijke, gemakkelijk te volgen stappen. Elke stap bevat de exacte code die je nodig hebt en een korte uitleg over *waarom* de stap bestaat.

### Stap 1: Laad het document dat een radiale grafiek bevat

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Waarom dit belangrijk is:**  
`Document` is het toegangspunt van de **Aspose.Words chart API**. Het laadt het DOCX‑bestand in het geheugen, waardoor je toegang krijgt tot elke node—paragrafen, tabellen en grafiekvormen. Als het bestand niet gevonden kan worden, gooit `Document` een `FileNotFoundException`, die je in productiecode moet afhandelen.

### Stap 2: Haal de eerste grafiekvorm op uit het document

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Waarom dit belangrijk is:**  
Grafieken worden opgeslagen als `Shape`‑nodes. De `GetChild`‑methode met `NodeType.Shape` doorloopt de DOM en retourneert de eerste overeenkomende vorm. Casten naar `Chart` geeft toegang tot grafiekspecifieke eigenschappen zoals `RadialChart`. De null‑check zorgt voor een duidelijke foutmelding als het document geen grafiek bevat, wat een veelvoorkomend randgeval is bij het hergebruiken van sjablonen.

### Stap 3: Schakel graduaties in op de radiale grafiek

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Waarom dit belangrijk is:**  
`IsGraduationsVisible` regelt de tick‑marks rond de cirkelvormige as. Wanneer ingesteld op `true`, rendert de grafiek graduaties, waardoor de leesbaarheid voor kijkers die waarden nauwkeurig moeten aflezen verbetert. De eigenschap bevindt zich onder `RadialChart`, een sub‑type van `Chart`. Als je dit probeert op een niet‑radiale grafiek (bijv. een staafgrafiek), zal de `RadialChart`‑eigenschap `null` zijn, dus controleer eerst het type grafiek in complexere scenario's.

#### Niet‑radiale grafieken afhandelen (optioneel)

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

Deze controle maakt de code robuust wanneer het bron‑document verschillende grafiektypen kan bevatten.

### Stap 4: Sla het gewijzigde document op

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Waarom dit belangrijk is:**  
Het aanroepen van `Save` schrijft de in‑memory DOM terug naar een .docx‑bestand, waardoor de wijziging aan de grafiek wordt opgeslagen. Het uitvoerbestand kan worden geopend in Microsoft Word, LibreOffice of elke viewer die DOCX ondersteunt. Je zult de radiale grafiek met zichtbare graduaties zien.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt plakken in `Program.cs` van een .NET console‑project.

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

### Verwachte output

Wanneer je `RadialChart_Graduations.docx` opent in Word, zal de radiale grafiek tick‑marks (graduaties) rond de cirkelvormige as weergeven, vergelijkbaar met de eerder getoonde screenshot. De rest van de grafiek (datereeks, legenda, titel) blijft ongewijzigd.

## Veelvoorkomende variaties en randgevallen

| Situatie | Oplossing |
|-----------|----------|
| **Oudere Aspose.Words versie (< 24.9)** | Upgrade naar het nieuwste NuGet‑pakket. De eigenschap `IsGraduationsVisible` bestaat niet in eerdere releases. |
| **Meerdere grafieken in hetzelfde document** | Gebruik `doc.GetChild(NodeType.Shape, index, true)` met de juiste `index` of iterate over `doc.GetChildNodes(NodeType.Shape, true)` en filter op `ChartType.Radial`. |
| **Grafiek programmatically aangemaakt** | Gebruik `DocumentBuilder` om een grafiek in te voegen, en stel vervolgens `RadialChart.IsGraduationsVisible` in op de |

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Grafiekreeksgegevens bijwerken in een Word‑document met Aspose.Words voor .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Een grafiekreeks verwijderen uit een Word‑document met Aspose.Words voor .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Plot‑gebiedrand verbergen in een kolomgrafiek met Aspose.Words voor .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}