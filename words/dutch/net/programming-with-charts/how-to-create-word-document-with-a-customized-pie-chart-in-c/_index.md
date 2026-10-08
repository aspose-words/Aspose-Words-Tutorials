---
category: general
date: 2026-10-07
description: Leer hoe je een Word‑document maakt en een cirkeldiagram invoegt met
  Aspose.Words in C#. De gids laat ook zien hoe je een Word‑bestand genereert met
  aangepaste diagramlabels.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: nl
lastmod: 2026-10-07
og_description: Maak een Word‑document en voeg een cirkeldiagram in C# in. Volg deze
  stap‑voor‑stap handleiding om een Word‑bestand te genereren met volledig aangepaste
  diagramlabels.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Maak een Word‑document met een aangepast cirkeldiagram in C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Hoe maak je een Word‑document met een aangepast taartdiagram in C#
url: /nl/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Word‑document te maken met een aangepast taartdiagram in C#

Als je **een Word‑document** programmatisch moet **maken**, laat deze tutorial je zien hoe je een **taartdiagram** kunt **invoegen** en de gegevenslabels kunt aanpassen met Aspose.Words for .NET. Je leert ook hoe je een **Word‑bestand** kunt **genereren** dat een volledig gestileerd diagram bevat, van projectopzet tot het opslaan van het uiteindelijke document.

De gids doorloopt elke stap die nodig is om een diagram toe te voegen, labelposities aan te passen, hulplijnen in te schakelen en uiteindelijk het resultaat op te slaan als een `.docx`‑bestand. Er zijn geen externe tools nodig buiten de Aspose.Words‑bibliotheek, en de volledige broncode wordt geleverd zodat je deze direct kunt kopiëren, plakken en uitvoeren.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 SDK of later geïnstalleerd  
* Een geldige Aspose.Words for .NET‑licentie (of een gratis evaluatiesleutel)  
* Een IDE zoals Visual Studio 2022 of Visual Studio Code  

Je moet ook de volgende NuGet‑pakketten aan je project toevoegen:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Deze pakketten stellen de `Document`, `DocumentBuilder` en diagram‑gerelateerde klassen beschikbaar die in de voorbeelden hieronder worden gebruikt.

## Word‑document maken en een diagram toevoegen

De eerste stap is om **een Word‑document** te **maken** en een `DocumentBuilder` te verkrijgen die je in staat stelt inhoud in te voegen. De builder werkt als een cursor die zich binnen het document bevindt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Het `Document`‑object vertegenwoordigt het volledige Word‑bestand, terwijl de `DocumentBuilder` methoden biedt zoals `InsertChart` die objecten direct in de documentstroom plaatsen.

## Taartdiagram in het document invoegen

Nu de builder klaar is, kun je een **taartdiagram** met een specifieke grootte **invoegen**. Het diagram wordt toegevoegd op de huidige positie van de builder.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` retourneert een `Chart`‑object dat je verder kunt manipuleren. De voorbeeldgegevens creëren vier segmenten die de kwartaalomzet weergeven.

## Taartdiagram‑gegevenslabels aanpassen

Om het diagram beter leesbaar te maken, moet je vaak de **taartdiagram**‑labels **aanpassen** — ze buiten de segmenten plaatsen en hulplijnen tonen. Hier komt de `ChartDataLabelCollection` van pas.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Door `Position` op `OutsideEnd` te zetten, wordt elk label buiten de rand van het segment geplaatst, terwijl `ShowLeaderLines` een lijn tekent die het label met het segment verbindt. De optionele vlaggen `ShowValue` en `ShowPercentage` geven de lezer zowel ruwe cijfers als relatieve percentages.

**Pro‑tip:** Als je het lettertype van het label wilt opmaken, gebruik dan `dataLabels.Font` om grootte, kleur en stijl in te stellen. Zo zorgt je ervoor dat het diagram overeenkomt met de huisstijl van je organisatie.

## Word‑bestand opslaan en genereren

Nadat het diagram volledig is geconfigureerd, kun je een **Word‑bestand** **genereren** door de `Document`‑instantie naar schijf op te slaan. Kies het `.docx`‑formaat voor maximale compatibiliteit met moderne versies van Word.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wanneer je `CustomPieChart.docx` opent, zie je een taartdiagram met vier segmenten, elk gelabeld buiten het segment, verbonden door hulplijnen, en zowel waarde als percentage weergevend.

![Schermafbeelding van een Word‑document dat een aangepast taartdiagram bevat gemaakt met C#](image-placeholder.png)

*De afbeelding toont het eindresultaat van de **maak Word‑document**‑tutorial.*

## Veelvoorkomende variaties en randgevallen

| Scenario | Hoe de code aan te passen |
|----------|---------------------------|
| **Meerdere series** | Voeg extra `ChartSeries`‑objecten toe aan `pieChart.Series`. Elke serie kan zijn eigen `DataLabels`‑collectie hebben voor onafhankelijke opmaak. |
| **Andere diagramgrootte** | Wijzig de breedte‑ en hoogte‑parameters in `InsertChart(width, height)`. Waarden staan in punten (1 pt ≈ 1/72 in). |
| **Diagramtitel** | Gebruik `pieChart.Title.Text = "Quarterly Sales"` om een beschrijvende titel toe te voegen. |
| **Exporteren naar PDF** | Roep `document.Save("Report.pdf", SaveFormat.Pdf);` aan nadat het diagram is opgebouwd. |
| **Licentie‑afhandeling** | Plaats je licentiebestand (`Aspose.Words.lic`) in de toepassingsmap en laad het met `new License().SetLicense("Aspose.Words.lic");` voordat je het document maakt. |

Deze variaties laten je de vraag **hoe een taartdiagram toe te voegen** beantwoorden in veel real‑world scenario’s, van eenvoudige rapporten tot complexe dashboards.

## Conclusie

Je weet nu hoe je **een Word‑document** kunt **maken**, een **taartdiagram** kunt **invoegen** en de **taartdiagram**‑labels kunt **aanpassen** met Aspose.Words for .NET. Het volledige voorbeeld toont een duidelijke workflow: initialiseert het document, voegt een diagram toe, past de positie van gegevenslabels aan, schakelt hulplijnen in en genereert tenslotte een **Word‑bestand** dat met iedereen gedeeld kan worden.

Probeer deze tutorial uit te breiden door te experimenteren met verschillende diagramtypen (`ChartType.Column`, `ChartType.Line`) of door aangepaste kleurenpaletten toe te passen die bij je merk passen. Als je tegen problemen aanloopt, raadpleeg dan de Aspose.Words‑documentatie of verken gerelateerde onderwerpen zoals “hoe een taartdiagram toe te voegen” met meerdere series en dynamische gegevensbronnen.

Veel programmeerplezier, en deel gerust je resultaten of stel vervolgvragen in de reacties!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}