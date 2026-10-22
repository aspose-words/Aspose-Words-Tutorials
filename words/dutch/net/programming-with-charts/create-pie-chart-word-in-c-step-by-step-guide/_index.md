---
category: general
date: 2026-08-07
description: Maak snel een taartdiagram in C#. Leer hoe je een taartdiagram invoegt,
  gegevenslabels toevoegt, percentages weergeeft en diagramgegevenslabels aanpast.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: nl
lastmod: 2026-08-07
og_description: Maak een taartdiagram in Word met C# en Aspose.Words. Deze tutorial
  laat zien hoe je een taartdiagram invoegt, gegevenslabels toevoegt en een taartdiagram
  met percentages weergeeft, terwijl je de diagramgegevenslabels aanpast.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Maak een taartdiagram in C# – volledige tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Maak een taartdiagram‑woord in C# – stapsgewijze handleiding
url: /nl/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een taartdiagram in Word met C# – stapsgewijze handleiding

Als je **taartdiagrammen in Word** wilt **maken** met C#, biedt deze gids een complete, kant‑klaar werkende oplossing. Je ziet hoe je **een taartdiagram invoegt**, **gegevenslabels voor taart toevoegt**, en **een procentueel diagram weergeeft**, terwijl je **grafiek‑gegevenslabels aanpast** voor een gepolijste uitstraling.

Grafieken programmatisch genereren bespaart je handmatig bewerken, vooral wanneer rapporten of dashboards automatisch moeten worden geproduceerd. In de onderstaande secties leer je alles wat nodig is om een volledig gelabelde taartgrafiek in een Word‑bestand te embedden met Aspose.Words voor .NET.

## Vereisten en installatie

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 SDK of later geïnstalleerd.  
* Een geldige Aspose.Words voor .NET‑licentie (of een tijdelijke evaluatiesleutel).  
* Visual Studio 2022 (of een andere IDE die C# ondersteunt).  

Voeg het Aspose.Words NuGet‑pakket toe aan je project:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Als je veel diagrammen gaat genereren, schakel dan de **Free‑Form Drawing**‑modus (`DocumentBuilder.UseFreeFormDrawing = true`) in voor betere prestaties.

## Maak een taartdiagram in Word met Aspose.Words

De eerste grote stap is het aanmaken van een leeg Word‑document en een `DocumentBuilder`. Dit object regelt alle volgende invoegacties.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is*: `Document` vertegenwoordigt het volledige `.docx`‑bestand, terwijl `DocumentBuilder` een vloeiende API biedt om alinea’s, tabellen en diagrammen toe te voegen. Beginnen met een schoon document zorgt ervoor dat er geen verborgen opmaak de diagramlay-out beïnvloedt.

## Voeg een taartdiagram toe aan het document

Nu plaatsen we een taartdiagram van de gewenste grootte. De methode `InsertChart` retourneert een `Chart`‑object dat we verder kunnen configureren.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Waarom dit belangrijk is*: De vlag `ChartType.Pie` vertelt Aspose.Words een cirkelvormig diagram te genereren. De breedte (`400`) en hoogte (`300`) worden uitgedrukt in punten, waardoor je precieze controle hebt over de visuele footprint.

## Vul het diagram met gegevens

Een taartdiagram heeft minimaal één reeks numerieke waarden nodig. Hier voegen we drie categorieën toe: “Apples”, “Bananas” en “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Waarom dit belangrijk is*: Elke `AddCategory`‑aanroep creëert een segment. De numerieke waarde bepaalt de grootte van het segment, terwijl het label de categorienaam wordt die wordt weergegeven wanneer gegevenslabels zijn ingeschakeld.

## Voeg gegevenslabels toe aan de taart en toon procenten

Om het diagram informatief te maken, schakelen we gegevenslabels in, positioneren ze buiten de segmenten, en laten we Aspose.Words zowel de categorienaam als het percentage weergeven.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Waarom dit belangrijk is*: Het instellen van `Position` op `OutsideEnd` verbetert de leesbaarheid, vooral wanneer segmenten klein zijn. Het inschakelen van `ShowCategoryName` en `ShowPercentage` vervult de **show percentage chart**‑vereiste en voldoet aan het **add data labels pie**‑doel.

## Pas diagram‑gegevenslabels verder aan (optioneel)

Je wilt misschien het lettertype wijzigen, een verbindingslijn toevoegen, of de legenda verbergen. Het volgende fragment toont veelvoorkomende aanpassingen:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Waarom dit belangrijk is*: Het aanpassen van de label‑uiterlijk zorgt ervoor dat het diagram overeenkomt met de stijlgids van je document. Het verwijderen van de legenda vermindert visuele rommel wanneer gegevenslabels dezelfde informatie al overbrengen.

## Sla het document op met het aangepaste diagram

Tot slot schrijf je het document naar schijf. Kies een pad waar je schrijfrechten voor hebt.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Wanneer je `ChartWithCustomLabels.docx` opent in Microsoft Word, zie je een taartdiagram waarbij elk segment is gelabeld met de categorienaam en het percentage, buiten het segment gepositioneerd, en gestyled met de aangepaste lettertype‑instellingen.

### Verwachte output

| Segment | Waarde | Percentage | Label weergegeven in Word |
|---------|--------|------------|----------------------------|
| Apples  | 40     | 40 %       | Apples – 40 %              |
| Bananas | 35     | 35 %       | Bananas – 35 %             |
| Cherries| 25     | 25 %       | Cherries – 25 %            |

Het diagram zou er ongeveer zo uit moeten zien:

![Word document displaying a pie chart with percentage labels outside each slice](pie-chart-word.png "Create pie chart word example")

*Afbeeldings‑alt‑tekst bevat het primaire zoekwoord voor SEO.*

## Meerdere reeksen en randgevallen behandelen

Het basisvoorbeeld gebruikt één reeks, wat typisch is voor een taartdiagram. Als je meerdere reeksen wilt weergeven (bijv. twee jaren vergelijken), moet je:

1. `chart.Series.Add()` aanroepen voor elke extra reeks.  
2. Zorgen dat elke reeks dezelfde categorieën gebruikt; anders gooit Aspose.Words een `ArgumentException`.  
3. Optioneel `labels.ShowSeriesName = true` instellen om reeksen te onderscheiden.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Wanneer er meerdere reeksen bestaan, rendert het diagram automatisch als een **clustered pie** (ook wel “pie of pies” genoemd). Controleer de output om te verifiëren dat de labels leesbaar blijven.

## Veelvoorkomende valkuilen en hoe ze te vermijden

| Probleem | Oorzaak | Oplossing |
|----------|---------|-----------|
| Labels overlappen segmenten | Klein diagramgebied of veel categorieën | Vergroot de diagramafmetingen (`InsertChart(width, height)`) of schakel `Position` over naar `InsideEnd`. |
| Percentages tellen niet op tot 100 % | Afrondingsfouten in de data | Gebruik `labels.ShowPercentage = true` (Aspose.Words normaliseert automatisch). |
| Diagram verschijnt leeg in Word | Ontbrekende licentie of verlopen evaluatie | Zorg dat een geldige Aspose.Words‑licentie is geladen vóór het aanmaken van het document. |
| Letterkleur verschilt van Word‑thema | Aangepast lettertype ingesteld in code | Verwijder aangepaste lettertype‑instellingen of stem af op de themakleuren van Word (`System.Drawing.Color.Black`). |

## Volledige broncode (uitvoerbaar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Het uitvoeren van het programma produceert `ChartWithCustomLabels.docx`, dat een **create pie chart word**‑voorbeeld bevat dat aan alle in de tutorial genoemde eisen voldoet.

## Conclusie

Je weet nu hoe je **taartdiagrammen in Word** kunt **maken** met C# en Aspose.Words. De gids behandelde het invoegen van een taartdiagram, **add data labels pie**, **show percentage chart**, en **customize chart data labels** om een professioneel, data‑gedreven Word‑bestand te realiseren.  

Vanaf hier kun je gerelateerde onderwerpen verkennen, zoals **insert pie chart** in bestaande alinea’s, het genereren van **bar**‑ of **line**‑diagrammen, of het automatiseren van batch‑creatie van rapporten met wisselende datasets. Experimenteer met verschillende labelposities, lettertype‑stijlen en multi‑reeks‑configuraties om de output af te stemmen op jouw specifieke rapportagebehoeften.

Veel succes met diagrammen maken!


## Wat kun je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}