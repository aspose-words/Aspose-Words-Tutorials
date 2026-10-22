---
category: general
date: 2026-08-10
description: Maak een Word‑document met een taartdiagram met Aspose.Words. Leer hoe
  je een diagram invoegt, de kleuren van het taartdiagram aanpast en de kleur van
  een taartpunt wijzigt in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: nl
lastmod: 2026-08-10
og_description: Maak een Word‑document met een cirkeldiagram met Aspose.Words. Deze
  gids legt uit hoe je een diagram invoegt, de kleuren van het cirkeldiagram aanpast
  en de kleur van een partitie van het cirkeldiagram wijzigt in een C#‑applicatie.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Maak een taartdiagram Word‑document – Aspose.Words‑gids
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Maak een taartdiagram Word-document met Aspose.Words
url: /nl/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak een taartdiagram Word-document met Aspose.Words

Als je programmatically een **pie chart Word document** moet **maken**, laat deze tutorial je precies zien hoe. We lopen door het invoegen van een diagram, **het aanpassen van taartdiagramkleuren**, en **het wijzigen van de kleur van een taartpunt** met Aspose.Words voor .NET.

Je ziet een volledig, uitvoerbaar voorbeeld dat je kunt kopiëren naar Visual Studio, uitvoeren, en direct het gegenereerde *.docx* kunt openen om het gestileerde taartdiagram te verifiëren. Geen externe documentatie is nodig—alles wat je nodig hebt staat in deze gids.

## Vereisten

* .NET 6.0 SDK of later geïnstalleerd  
* Een geldige Aspose.Words voor .NET‑licentie (of een tijdelijke evaluatiesleutel)  
* Visual Studio 2022 (of elke C#‑IDE)  

De code gebruikt alleen de `Aspose.Words` en `Aspose.Words.Drawing.Charts` namespaces, dus er zijn geen extra NuGet‑pakketten nodig naast de Aspose.Words‑bibliotheek.

## Maak een taartdiagram Word-document – volledig voorbeeld

Het volgende C#‑programma maakt een nieuw Word‑document, voegt een taartdiagram toe, stijlt de eerste twee segmenten, en slaat het bestand op. Elke stap wordt gedetailleerd uitgelegd.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Uitleg van elke stap

| Stap | Wat het doet | Waarom het belangrijk is |
|------|--------------|--------------------------|
| **1** | Maakt een nieuw `Document` en een `DocumentBuilder` aan. | De `DocumentBuilder` biedt vloeiende methoden voor het invoegen van inhoud, zoals diagrammen, in het Word‑bestand. |
| **2** | Roept `InsertChart` aan met `ChartType.Pie` en een vaste grootte. | `InsertChart` is de **how to insert chart** methode; het specificeren van breedte/hoogte zorgt ervoor dat het diagram netjes op de pagina past. |
| **3** | Voegt een gegevensreeks toe met drie categorieën en numerieke waarden. | Een taartdiagram zonder gegevens is onzichtbaar; het vullen ervan toont de stylingstappen. |
| **4** | Stelt `Explosion` in op het eerste punt. | Het exploderen van een segment trekt de aandacht naar een specifiek deel—handig om belangrijke gegevens te benadrukken. |
| **5** | Stelt `ForeColor` in voor de eerste twee punten. | Dit is de kern van **customize pie chart colors**; je kunt elke `System.Drawing.Color` gebruiken. |
| **6** | Toont hoe je **change pie slice color** kunt toepassen op extra segmenten. | Toont aan dat styling niet beperkt is tot de eerste twee segmenten; je kunt elk segment afzonderlijk kleuren. |
| **7** | Slaat het document op als `PieChartStyled.docx`. | De uiteindelijke output kan worden geopend in Microsoft Word, Google Docs, of elke compatibele viewer. |

#### Verwachte output

Opening `PieChartStyled.docx` toont een enkele pagina met een 400 × 300 pt taartdiagram:

* Segment 1 (oranje) is naar buiten geëxplodeerd.  
* Segment 2 (groen) verschijnt naast het geëxplodeerde segment.  
* Segment 3 (staal‑blauw) vult het resterende deel.

Het diagram weerspiegelt de gegevenswaarden (30, 45, 25) en de aangepaste kleuren die je hebt gedefinieerd.

## Hoe taart te stijlen – extra tips

* **Gebruik themakleuren** – in plaats van hard‑coderen van `Color.Orange`, kun je kleuren uit het documentthema halen:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Voeg gegevenslabels toe** – als je percentages op het diagram wilt weergeven:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Dynamisch aanpassen van grootte** – bereken de diagramgrootte op basis van paginamarges:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Deze variaties tonen de flexibiliteit van **how to style pie** voorbij het basisvoorbeeld.

## Veelgestelde vragen beantwoord

**V: Werkt dit met .NET Core?**  
A: Ja. Aspose.Words voor .NET is compatibel met .NET Core, .NET 5, .NET 6, en later. Verwijs gewoon naar hetzelfde NuGet‑pakket.

**V: Wat als ik een donut‑diagram in plaats van een taartdiagram nodig heb?**  
A: Vervang `ChartType.Pie` door `ChartType.Doughnut`. Dezelfde styling‑API’s (`Explosion`, `ForeColor`) zijn van toepassing.

**V: Kan ik het diagram in een bestaand document invoegen?**  
A: Open het bestaande bestand met `new Document("Existing.docx")`, maak een `DocumentBuilder` voor dat document, en roep `InsertChart` aan op de gewenste cursorpositie.

**V: Hoe ga ik om met grote datasets?**  
A: Taartdiagrammen zijn het beste voor een beperkt aantal categorieën (meestal < 10). Voor veel categorieën, overweeg een staaf‑ of kolomdiagram.

## Volledige broncode samenvatting

Hieronder staat het volledige programma in één blok voor eenvoudig kopiëren‑plakken:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Het uitvoeren van deze code produceert het gestileerde taartdiagram‑Word‑document dat eerder is beschreven.

## Conclusie

Je weet nu hoe je **pie chart Word** documenten kunt **maken** met Aspose.Words, **pie chart colors kunt aanpassen**, en **pie slice color kunt wijzigen** programmatically. De gids behandelde het invoegen van het diagram, het vullen van gegevens, het exploderen van een segment, het toepassen van aangepaste kleuren, en het opslaan van het resultaat.  

Vanaf hier kun je gerelateerde onderwerpen verkennen, zoals **how to insert chart** typen anders dan taart, het toevoegen van legenda’s, of het genereren van meer‑pagina‑rapporten met meerdere diagrammen. Experimenteer met verschillende kleurschema’s en datasets om aan je rapportagebehoeften te voldoen.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Kolomdiagram invoegen in Word met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Gebieddiagram invoegen in Word‑document | Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Word‑spreidingsdiagram maken met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}