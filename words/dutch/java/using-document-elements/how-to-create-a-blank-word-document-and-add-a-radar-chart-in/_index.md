---
category: general
date: 2026-09-21
description: Maak een leeg Word‑document en leer hoe je een radardiagram in een Word‑bestand
  kunt invoegen met DocumentBuilder – stapsgewijze handleiding.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: nl
lastmod: 2026-09-21
og_description: Maak een leeg Word‑document en voeg een radardiagram in een Word‑bestand
  toe met Aspose.Words. Volg deze tutorial om snel een diagram in een Word‑document
  te genereren.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Maak een leeg Word‑document en voeg een radardiagram toe – volledige C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Hoe maak je een leeg Word‑document en voeg je een radardiagram toe in C#
url: /nl/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een leeg Word‑document te maken en een radardiagram toe te voegen in C#

Als je een **leeg Word‑document** moet **maken** en een radar‑ (radiaal) diagram wilt insluiten, biedt deze tutorial een kant‑klaar werkende oplossing. Je ziet hoe je Aspose.Words .NET gebruikt om het bestand te genereren, het diagram in te voegen en het resultaat op te slaan — alles in een paar beknopte stappen.

Een leeg document biedt een schoon canvas voor elke geautomatiseerde rapportagesituatie, en het toevoegen van een radardiagram stelt je in staat multidimensionale gegevens direct in Word te visualiseren. Aan het einde van deze gids kun je een Word‑document met diagram genereren zonder handmatige bewerking.

## Wat je zult leren

* Hoe je **een leeg Word‑document** programmatically maakt met C#.
* De exacte code om **een radardiagram in te voegen** met `DocumentBuilder`.
* Manieren om **een diagram in een Word‑bestand in te voegen** en de grootte aan te passen.
* Hoe je **een Word‑document met diagram genereert** en de output verifieert.
* Tips voor **radiale diagrammen toe te voegen aan Word‑bestanden**, inclusief veelvoorkomende valkuilen.

### Vereisten

* .NET 6.0 of later (de code werkt ook met .NET Framework 4.6+).
* Aspose.Words for .NET (NuGet‑pakket `Aspose.Words` versie 23.9 of nieuwer).
* Basiskennis van C# en Visual Studio of je favoriete IDE.

## Een leeg Word‑document maken met C#

De eerste stap is het instantieren van een lege `Document`‑object. Dit object vertegenwoordigt een volledig leeg `.docx`‑bestand.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` maakt de bestandsstructuur aan, maar bevat nog geen secties of pagina's. Aspose.Words voegt automatisch een standaardsectie toe zodra je begint met inhoud toe te voegen, waardoor de volgende stap zonder extra configuratie werkt.

## Hoe een radardiagram in het Word‑bestand in te voegen

Een radardiagram (ook wel radiaal diagram genoemd) visualiseert gegevenspunten op assen die vanuit een centraal punt uitstralen. Aspose.Words biedt `DocumentBuilder.insertChart` voor dit doel.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` retourneert een `Chart`‑object dat je verder kunt configureren. Het diagram verschijnt op de eerste pagina van het lege document omdat de builder standaard aan het begin van het document staat.

## Diagram in een Word‑bestand invoegen – gegevensreeksen toevoegen

Een diagram zonder gegevens is onzichtbaar. Vul het radardiagram met één of meer reeksen om het betekenisvol te maken.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Je kunt zoveel reeksen toevoegen als nodig. Elke reeks kan een eigen naam hebben, die in de legenda van het diagram wordt weergegeven. De gegevenspunten corresponderen met de radiale assen; de volgorde waarin je ze toevoegt bepaalt hun positie rond de cirkel.

## Een Word‑document met diagram genereren – het bestand opslaan

Nadat je het diagram hebt opgebouwd, sla je het document op schijf op. Kies een locatie waar je schrijfrechten voor hebt.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Wanneer je het resulterende `.docx`‑bestand opent in Microsoft Word, zie je een lege pagina met een radardiagram van 400 × 300 punten, gevuld met de voorbeeldgegevens.

### Verwachte output

* Een `RadialChartExample.docx`‑bestand op je bureaublad.
* De eerste pagina bevat een radardiagram met vijf gegevenspunten gelabeld “Series 1”.
* Er verschijnt geen extra tekst omdat het document leeg is begonnen.

## Radiaal diagram toevoegen aan Word – omgaan met veelvoorkomende randgevallen

### 1. Diagramgrootte wijzigen na invoegen

Als de initiële afmetingen niet in je lay‑out passen, wijzig je de grootte als volgt:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Het diagram op een specifieke locatie invoegen

Je kunt de cursor van de builder verplaatsen naar een bladwijzer, tabelcel of alinea voordat je `InsertChart` aanroept.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Het uiterlijk van het diagram aanpassen

Aspose.Words biedt toegang tot het volledige diagram‑objectmodel, zodat je titels, as‑labels en kleuren kunt instellen.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Omgaan met ontbrekende lettertypen

Als de doelomgeving een lettertype dat in het diagram wordt gebruikt niet heeft, vervangt Aspose.Words dit door een standaardlettertype. Om consistentie te garanderen, embed je de benodigde lettertypen:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Exporteren naar andere formaten

Hetzelfde document kan worden opgeslagen als PDF, HTML of PNG zonder extra code‑aanpassingen:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Volledig, uitvoerbaar voorbeeld

Alle onderdelen samenvoegen levert een enkel programma op dat je kunt kopiëren, plakken en uitvoeren.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Voer dit programma uit, open het gegenereerde bestand, en je ziet een professioneel radardiagram klaar voor distributie.

## Conclusie

Je weet nu hoe je **een leeg Word‑document maakt**, **een radardiagram invoegt**, en **een Word‑document met diagram genereert** met Aspose.Words. Door de bovenstaande stappen te volgen kun je ook **radiale diagrammen toevoegen aan Word‑bestanden** in elke geautomatiseerde rapportage‑pipeline, de grootte en stijl aanpassen en exporteren naar extra formaten.

**Volgende stappen**

* Verken andere diagramtypen (`ChartType.Column`, `ChartType.Pie`) om je rapportagetoolkit uit te breiden.
* Combineer meerdere diagrammen op één pagina door `InsertChart` herhaaldelijk aan te roepen.
* Integreer gegevens uit een database of CSV‑bestand om reeksen dynamisch te vullen.
* Raadpleeg de Aspose.Words‑documentatie voor geavanceerde opmaakopties zoals voorwaardelijke gegevenslabels en diagram‑sjablonen.

Voel je vrij om met de code te experimenteren, afmetingen aan te passen of de voorbeeldgegevens te vervangen door echte bedrijfs‑metriek. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}