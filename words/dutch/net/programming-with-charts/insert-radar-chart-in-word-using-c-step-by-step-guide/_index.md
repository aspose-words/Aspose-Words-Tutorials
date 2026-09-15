---
category: general
date: 2026-09-14
description: Radar-diagram invoegen in Word met C#. Leer hoe je de diagramtitel instelt,
  meerdere series toevoegt en het diagram programmeert in slechts een paar regels.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: nl
lastmod: 2026-09-14
og_description: Radar-diagram invoegen in Word met C#. Deze tutorial laat zien hoe
  je de diagramtitel instelt, meerdere series toevoegt en het diagram programmatisch
  maakt.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: Radar-diagram invoegen in Word met C# – snelle programmeergids
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: Radar‑diagram invoegen in Word met C# – stap‑voor‑stap handleiding
url: /nl/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Radar-diagram invoegen in Word met C# – stapsgewijze handleiding

Als je een **radar-diagram** in een Word‑document moet invoegen, laat deze handleiding je zien hoe je dit programmatically met C# kunt doen. Je leert ook hoe je **de diagramtitel instelt**, een **radar-diagram met meerdere series** toevoegt, en het bestand opslaat zonder je IDE te verlaten.

De tutorial behandelt alles van projectconfiguratie tot de uiteindelijke `doc.Save`‑aanroep, zodat je het volledige voorbeeld kunt kopiëren‑plakken en direct kunt uitvoeren. Het is niet nodig om externe documentatie te raadplegen.

## Vereisten

* .NET 6 (of later) geïnstalleerd.
* Een geldige Aspose.Words for .NET‑licentie (of een tijdelijke evaluatiesleutel).
* Visual Studio 2022 of een andere C#‑IDE naar keuze.

> **Pro tip:** Als je de gratis proefversie gebruikt, vergeet dan niet de licentie in te stellen vóór de eerste `Document`‑creatie om het evaluatiewatermerk te vermijden.

## Stap 1: Radar-diagram invoegen in een Word‑document

De eerste handeling is het aanmaken van een nieuw `Document` en een `DocumentBuilder`. De builder geeft je toegang tot de inhoud van het document en stelt je in staat een **radar-diagram** precies op de gewenste plaats te plaatsen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Waarom deze stap belangrijk is:* `InsertChart` maakt een diagramobject aan dat je volledig kunt configureren voordat het document wordt opgeslagen. Het gebruik van `ChartType.Radar` vertelt Word om een radiaal diagram weer te geven in plaats van een kolom‑ of lijndiagram.

## Stap 2: Diagramtitel en asgraduaties instellen

Een diagram zonder titel kan verwarrend zijn. Hier **stellen we de diagramtitel** in op “Sales Radar” en schakelen we graduaties in op beide assen (beschikbaar vanaf Aspose.Words 24.9).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Waarom deze stap belangrijk is:* De titel biedt context voor de lezer, en graduaties verbeteren de leesbaarheid door te laten zien waar elk datapunt op de schaal valt.

## Stap 3: Meerdere series maken voor radar-diagram

Een **radar-diagram met meerdere series** stelt je in staat verschillende perioden naast elkaar te vergelijken. Hieronder voegen we twee series toe — Q1 en Q2 — elk met drie datapunten.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Waarom deze stap belangrijk is:* Het toevoegen van meerdere series toont hoe je datasets op dezelfde radar kunt vergelijken, een veelvoorkomende eis voor verkoop, prestaties of enquête‑resultaten.

## Stap 4: Het Word‑document programmatically opslaan

Tot slot **maak je het diagram programmatically** en sla je het document op schijf op. De `Save`‑methode schrijft een `.docx`‑bestand dat geopend kan worden in Microsoft Word.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

Wanneer je `RadialGraduations.docx` opent, zie je een radar-diagram met de titel “Sales Radar” en twee series (Q1 en Q2) uitgezet tegen de maanden Jan‑Mar.

### Verwachte output

![Radar-diagram in Word](https://example.com/radar-chart.png){: .align-center alt="Word-document dat een radar-diagram toont met twee dataseries"}

De screenshot (of het daadwerkelijke bestand) bevestigt dat het diagram correct is ingevoegd, getiteld en gevuld.

## Volledig, uitvoerbaar voorbeeld

Alles samenvoegend, hier is een zelfstandige programma dat je kunt compileren en uitvoeren:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Voer het programma uit, open het gegenereerde bestand, en controleer dat de **insert radar chart**‑operatie geslaagd is.

## Veelgestelde vragen & randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Kan ik het diagramtype na invoegen wijzigen?** | Ja. Na `InsertChart` ken je een nieuw `ChartType` toe aan `chart.Type`. Het is echter efficiënter om het diagram vanaf het begin met het juiste type te maken. |
| **Wat als ik meer dan twee series nodig heb?** | Roep `chart.Series.Add` aan voor elke extra serie. Het diagram past de legenda en kleuren automatisch aan. |
| **Hoe pas ik kleuren of markers aan?** | Gebruik `chart.Series[i].Format.Fill.ForeColor` voor vulkleuren en `chart.Series[i].Marker` voor marker‑stijlen. |
| **Is de API compatibel met .NET Framework?** | Dezelfde code werkt met .NET Framework 4.7+; verwijs gewoon naar de juiste Aspose.Words‑DLL. |
| **Wat als ik een oudere Aspose.Words‑versie gebruik?** | Graduaties (`HasGraduations`) werden geïntroduceerd in 24.9. Voor oudere versies kun je handmatig rasterlijnen toevoegen met `chart.AxisX.MajorGridLines` en `chart.AxisY.MajorGridLines`. |

## Conclusie

Je weet nu hoe je een **radar-diagram** in een Word‑document kunt **invoegen** met C#, **de diagramtitel kunt instellen**, een **radar-diagram met meerdere series** kunt toevoegen, en **het diagram programmatically kunt maken**. Deze end‑to‑end‑oplossing stelt je in staat rapportages, dashboards of elke situatie waarin visuele vergelijking van categorieën vereist is, te automatiseren.

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **het aanpassen van diagramkleuren**, **diagrammen exporteren als afbeeldingen**, of **diagrammen insluiten in PDF‑bestanden**. Experimenteer met verschillende datasets om te zien hoe de radarvisualisatie zich aanpast.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Kolomdiagram invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Bubbeldiagram invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Vlakdiagram invoegen in Word‑document | Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}