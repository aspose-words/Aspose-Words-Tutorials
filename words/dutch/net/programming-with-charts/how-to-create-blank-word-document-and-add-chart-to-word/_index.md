---
category: general
date: 2026-09-08
description: Maak een leeg Word‑document en voeg een grafiek toe aan Word met Aspose.Words.
  Leer hoe je een radardiagram invoegt, graduaties inschakelt en het bestand opslaat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: nl
lastmod: 2026-09-08
og_description: Maak een leeg Word‑document en voeg een grafiek toe aan Word met Aspose.Words.
  Deze tutorial laat zien hoe je een radardiagram invoegt, de assen configureert en
  het document opslaat.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Maak een leeg Word‑document en voeg een radardiagram toe – stapsgewijze
  handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Hoe maak je een leeg Word‑document en voeg je een grafiek toe aan Word
url: /nl/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een leeg Word‑document te maken en een diagram toe te voegen aan Word

Als je een **leeg Word‑document** moet maken voor een rapport, sjabloon of geautomatiseerde mail‑merge, leidt deze gids je door het volledige proces met C# en Aspose.Words. Je leert ook hoe je **een diagram aan Word toevoegt**, specifiek hoe je een **radardiagram invoegt**, graduaties inschakelt en het resultaat opslaat als een .docx‑bestand.

Deze tutorial behandelt alles, van projectconfiguratie tot de laatste verificatiestap. Aan het einde heb je een herbruikbare code‑snippet die je in elke .NET‑applicatie kunt gebruiken. Er is geen eerdere ervaring met Aspose.Words vereist, maar je moet wel basiskennis van C# hebben en een recente .NET‑SDK geïnstalleerd hebben.

## Vereisten

- .NET 6.0 SDK of later  
- Aspose.Words for .NET (NuGet‑pakket `Aspose.Words`)  
- Een IDE zoals Visual Studio 2022 of VS Code  
- Schrijfrechten voor de map waarin het document wordt opgeslagen  

Je kunt de bibliotheek installeren met het volgende commando:

```bash
dotnet add package Aspose.Words
```

## Stap 1: Een leeg Word‑document maken

De eerste stap is om een **leeg Word‑document** in het geheugen te **maken**. De `Document`‑klasse vertegenwoordigt het volledige bestand, terwijl `DocumentBuilder` een vloeiende API biedt voor het toevoegen van inhoud.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` begint leeg, zodat je een schoon canvas hebt om het diagram op te plaatsen. Het document in deze fase leeg houden maakt het eenvoudig om dezelfde code voor verschillende sjablonen te hergebruiken.

## Stap 2: Een diagram aan Word toevoegen

Vervolgens **voegen we een diagram toe aan Word** door `InsertChart` aan te roepen. De methode vereist het type diagram en de gewenste afmetingen in punten (1 punt = 1/72 inch).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` vertelt Aspose.Words om een radiaal diagram te genereren, wat ideaal is voor het weergeven van multivariate gegevens in een cirkelvormige lay-out. De afmetingen (400 × 300) werken goed voor de meeste staande pagina's, maar je kunt ze aanpassen aan jouw lay-out.

## Stap 3: Radardiagram invoegen en graduaties configureren

Nu **voegen we een radardiagram in** en schakelen we graduaties (streepjes) in op zowel de categorie‑as (X) als de waardenas (Y). Graduaties verbeteren de leesbaarheid door exacte posities voor elk datapunt weer te geven.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Door `HasGraduations` op `true` te zetten, worden streepjes op de assen getekend. De optionele `GraduationStep` bepaalt de afstand tussen de streepjes op de radiale as; een stap van 10 betekent een streepje elke 10 graden.

### Pro‑tip
Als je gegevenslabels wilt weergeven, roep dan `radarChart.Series[0].HasDataLabel = true;` aan. Dit voegt de numerieke waarde naast elk punt toe, wat handig is voor presentaties.

## Stap 4: Het diagram vullen met voorbeeldgegevens (optioneel)

Een radardiagram zonder gegevens is onzichtbaar. Hieronder staat een snelle manier om een reeks voorbeeldwaarden toe te voegen. Je kunt dit blok vervangen door je eigen gegevensbron.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Elke aanroep van `Add` voegt een punt toe aan de serie. De volgorde van de punten komt overeen met de hoekposities rond de cirkel.

## Stap 5: Het document met het diagram opslaan

Sla tenslotte het document op schijf op. De `Save`‑methode schrijft automatisch het .docx‑bestand weg, waarbij het diagram en alle opmaak behouden blijven.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Het uitvoeren van het programma maakt een **leeg Word‑document** dat nu een volledig functioneel radardiagram bevat. Open het bestand in Microsoft Word om het resultaat te zien.

![Radardiagram in Word‑document](radar_chart.png){alt="Radardiagram ingevoegd in een leeg Word‑document"}

## Veelvoorkomende variaties en randgevallen

| Situatie | Wat te wijzigen |
|-----------|----------------|
| **Andere diagramgrootte** | Pas de breedte/hoogte‑parameters van `InsertChart` aan. |
| **Andere diagramtypen** | Vervang `ChartType.Radar` door `ChartType.Column`, `ChartType.Pie`, enz., en behoud dezelfde graduatielogica. |
| **Opslaan naar een stream** | Gebruik `document.Save(Stream, SaveFormat.Docx)` |

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Area‑diagram invoegen in Word‑document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Word‑spreidingsdiagram maken met Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Kolomdiagram invoegen in Word met Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}