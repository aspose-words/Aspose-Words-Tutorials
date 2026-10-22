---
category: general
date: 2026-07-26
description: Voeg een cirkeldiagram in een Word‑document in met Aspose.Words. Leer
  hoe je een diagram toevoegt, een segment uitwaaieren en percentages weergeeft in
  slechts een paar stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: nl
lastmod: 2026-07-26
og_description: Voeg een cirkeldiagram toe aan een Word‑bestand met Aspose.Words.
  Volg deze gids om te leren hoe je een diagram toevoegt, een segment uit elkaar trekt
  en snel percentages weergeeft.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Cirkeldiagram invoegen in Word – Stapsgewijze Aspose.Words‑tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Cirkeldiagram invoegen in Word met Aspose.Words – Complete gids
url: /nl/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Voeg een taartdiagram in Word toe met Aspose.Words – Complete gids

Heb je ooit een **pie chart invoegen** moeten doen in een Word‑rapport, maar wist je niet waar te beginnen? Je bent niet de enige. In veel zakelijke apps geeft een taartdiagram een visuele impact waardoor gegevens direct begrijpelijk worden, en Aspose.Words maakt dat mogelijk met slechts een paar regels code.

In deze tutorial lopen we de exacte stappen door om **add chart to Word** toe te voegen, een partitie te laten exploderen voor nadruk, en percentages weer te geven op de gegevenslabels. Aan het einde heb je een kant‑klaar voorbeeld dat je in elk .NET‑project kunt gebruiken.

Dat is alles. Laten we de handen uit de mouwen steken.

---

## Vereisten

- .NET 6.0 of later (de code werkt zowel met .NET Core als .NET Framework)
- Het Aspose.Words for .NET NuGet‑pakket geïnstalleerd  
  ```bash
  dotnet add package Aspose.Words
  ```
- Een basisbegrip van C#‑syntaxis—geen geavanceerde kennis vereist
- Een IDE naar keuze (Visual Studio, Rider of VS Code)

Dat is alles. Laten we de handen uit de mouwen steken.

---

## Voeg een taartdiagram in een Word‑document in

Het eerste wat we nodig hebben is een nieuw `Document`‑object en een `DocumentBuilder`. Beschouw de builder als een pen die direct op het Word‑canvas schrijft.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Waarom dit belangrijk is:** Het `Document` vertegenwoordigt het volledige .docx‑bestand, terwijl de `DocumentBuilder` ons een handige API biedt om elementen zoals diagrammen, tabellen en tekst in te voegen. Dit is de basis voor elke **how to add chart**‑operatie.

---

## Hoe een diagram toe te voegen aan Word

Nu we een builder hebben, kunnen we daadwerkelijk **pie chart invoegen**. De `insertChart`‑methode neemt het diagramtype en de gewenste afmetingen in points (1 point = 1/72 inch).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Tip:** Als je een andere grootte nodig hebt, pas dan simpelweg de breedte‑ en hoogte‑waarden aan. Het diagram schaalt automatisch om binnen de paginamarges te passen.

---

## Hoe een partitie te exploderen voor nadruk

Een veelvoorkomende visuele aanpassing is om een partitie te “exploderen” zodat deze uit de cirkel springt. Dit trekt de aandacht van de lezer naar het belangrijkste segment.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Waarom een partitie exploderen?** Wanneer je een specifieke categorie wilt benadrukken—bijvoorbeeld “Q1‑omzet” in een financieel rapport—maakt het exploderen van de partitie deze onmiddellijk opvallend zonder extra tekst.

---

## Hoe percentages weer te geven op gegevenslabels

De meeste taartdiagrammen zien er beter uit wanneer elke partitie zijn percentage weergeeft. Aspose.Words stelt ons in staat dit met één eigenschap in te schakelen.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Korte opmerking:** De `ShowPercentage`‑vlag werkt voor alle punten in de serie, dus je hoeft deze niet per partitie in te stellen.

---

## Sla het document met het diagram op

Tot slot schrijven we het document naar schijf. Kies een map naar keuze; zorg er alleen voor dat het pad bestaat.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Wanneer je `PieChart.docx` opent in Microsoft Word zie je een perfect gerenderd taartdiagram met de eerste partitie geëxplodeerd en percentages weergegeven—precies wat je zou verwachten van een professioneel bedrijfsrapport.

---

## Volledig werkend voorbeeld

Hieronder staat het volledige, kant‑klaar te kopiëren programma. Voer het uit als console‑applicatie en controleer het output‑bestand.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Verwacht resultaat:** Open het gegenereerde `PieChart.docx`. Je ziet een drie‑partitie taartdiagram met de titel “Sales Q1”, waarbij de eerste partitie eruit wordt getrokken en elke partitie gelabeld is met “30 %”, “45 %” en “25 %”. De visualisatie komt overeen met de ingevoerde gegevens.

---

## Veelgestelde vragen & randgevallen

- **Wat als ik meer dan één serie nodig heb?**  
  Voeg gewoon extra `ChartSeries`‑objecten toe aan `chart.Series`. Elke serie kan zijn eigen dataset, kleuren en explode‑instellingen hebben.

- **Kan ik de kleuren van het diagram wijzigen?**  
  Ja. Elke `ChartPoint` heeft een `Format.Fill.ForeColor`‑eigenschap die je kunt instellen op elke `System.Drawing.Color`.

- **Wat betreft verschillende diagramtypen?**  
  De `ChartType`‑enum bevat bar, line, doughnut en nog veel meer. Vervang `ChartType.Pie` door het diagramtype dat je nodig hebt.

- **Is het diagram bewerkbaar in Word na invoegen?**  
  Absoluut. Word behandelt het diagram als een native Office‑diagram, zodat gebruikers er dubbel op kunnen klikken om de ingebouwde diagrameditor te openen.

---

## Conclusie

Je weet nu precies hoe je **pie chart invoegt** in een Word‑document met Aspose.Words, **hoe je chart to word toevoegt**, **hoe je een partitie explodeert**, en **hoe je percentages weergeeft** op de gegevenslabels. Het volledige voorbeeld hierboven is klaar om uit te voeren, en je kunt het uitbreiden met aangepaste gegevens, styling of extra series.

Klaar voor de volgende stap? Probeer de taart te vervangen door een doughnut‑diagram, of genereer automatisch een batch rapporten met verschillende datasets. Als je nieuwsgierig bent naar andere visualisaties, bekijk dan onze handleidingen over **how to add chart** voor staaf‑ en lijndiagrammen, of verken de **add chart to word**‑API‑referentie voor diepere aanpassingen.

Veel plezier met coderen, en moge je documenten altijd zo duidelijk zijn als een perfect gesneden taart!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}