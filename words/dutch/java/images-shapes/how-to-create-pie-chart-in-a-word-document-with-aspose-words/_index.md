---
category: general
date: 2026-10-20
description: Maak een cirkeldiagram in een Word‑document met Aspose.Words – een stapsgewijze
  handleiding die laat zien hoe je de kleur instelt, een segment laat exploderen en
  het Word‑document opslaat.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: nl
lastmod: 2026-10-20
og_description: Maak een taartdiagram in een Word‑document met Aspose.Words. Leer
  hoe je de kleur instelt, een part uitwaaieren en het Word‑document opslaan in één
  uitvoerbaar voorbeeld.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Maak een cirkeldiagram in een Word‑document – volledige C#‑gids
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Hoe maak je een taartdiagram in een Word‑document met Aspose.Words
url: /nl/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een taartdiagram te maken in een Word‑document met Aspose.Words

Als je een **taartdiagram** in een Word‑bestand moet **maken**, laat deze gids je precies zien hoe. Je ziet hoe je een aangepaste kleur instelt, een partje explodeert voor nadruk, en uiteindelijk het **Word‑document** opslaat met het diagram erin ingebed.

Het programmatisch genereren van diagrammen verwijdert de handmatige stappen van het openen van Word, het invoegen van een diagram en het aanpassen van de weergave. Aan het einde van deze tutorial heb je een volledige, uitvoerbare C#‑console‑applicatie die een taartdiagram maakt, het aanpast en het resultaat naar schijf schrijft.

## Vereisten

Voordat je begint, zorg dat je het volgende hebt:

* .NET 6.0 SDK of later geïnstalleerd  
* Een geldige Aspose.Words for .NET‑licentie (of een gratis evaluatiesleutel)  
* Een IDE zoals Visual Studio 2022 of VS Code  

Er zijn geen extra NuGet‑pakketten nodig naast `Aspose.Words`.

## Hoe een taartdiagram te maken in een Word‑document

De eerste stap is het instantieren van een `Document` en een `DocumentBuilder`. De builder geeft je toegang tot high‑level Word‑functionaliteit, inclusief het invoegen van diagrammen.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

Op dit moment bevat het document al een basis‑taartdiagram. De volgende secties leggen uit **hoe je een partje explodeert**, **hoe je een kleur instelt**, en **hoe je het Word‑document opslaat**.

## Hoe een partje te explodeeren voor nadruk

Een partje exploderen scheidt het van de rest van de taart, waardoor de lezer ernaar kijkt. De Aspose.Words‑API laat je een explosie‑afstand in punten opgeven.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Waarom een partje exploderen? In rapporten die een specifieke categorie benadrukken — bijvoorbeeld “Best‑verkochte product” — maakt de visuele scheiding het datapunt direct herkenbaar.

## Hoe een kleur in te stellen op een diagram‑partje

Aangepaste kleuren verbeteren merkconsistentie en leesbaarheid. Je kunt elke `System.Drawing.Color` toewijzen aan een specifiek datapunt.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Je bent niet beperkt tot vooraf gedefinieerde kleuren; je kunt een `Color.FromArgb`‑waarde maken voor precieze tinten.

## Hoe het Word‑document met het diagram op te slaan

Zodra het diagram er uitziet zoals je wilt, is het opslaan van het bestand eenvoudig. De `Document.Save`‑methode schrijft het document in het formaat dat je opgeeft — hier gebruiken we de standaard `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Het uitvoeren van het programma maakt `PieChart.docx`. Het openen van het bestand in Microsoft Word toont een taartdiagram waarbij het eerste partje is geëxplodeerd en rood is gekleurd, precies zoals de code aangeeft.

### Verwacht resultaat

* Een Word‑bestand met de naam **PieChart.docx** in `C:\Temp`.  
* Het document bevat één taartdiagram, 400 × 300 punten groot.  
* Partje 0 is verschoven met 20 punten en gevuld met rood, terwijl de andere partjes de standaardkleur behouden.  

Je kunt de explosie en kleur verifiëren door het diagram in Word te selecteren en de partje‑eigenschappen te inspecteren.

## Pro‑tips en veelvoorkomende valkuilen

* **Pro‑tip:** Als je de diagramtitel of legenda wilt wijzigen, gebruik dan `pieChart.Title.Text` en `pieChart.Legend`‑eigenschappen vóór het opslaan.  
* **Let op:** Het vergeten om de standaarddatapunten te wissen kan leiden tot extra, ongewenste partjes. Roep altijd `Series[0].DataPoints.Clear()` aan voordat je je eigen data toevoegt.  
* **Prestatie‑tip:** Voor grote documenten, hergebruik één `DocumentBuilder`‑instantie in plaats van vele builders; dit vermindert het geheugen‑overhead.

## Hoe een diagram te maken met Aspose.Words (extra context)

De `InsertChart`‑methode ondersteunt veel diagramtypen naast taartdiagrammen, zoals kolom‑, lijn‑ en gebiedsdiagrammen. Om over te schakelen naar een ander type, vervang je `ChartType.Pie` door de gewenste enum‑waarde, bijvoorbeeld `ChartType.Column`. De overige aanpassingsstappen (exploderen van partjes, kleuren instellen) volgen hetzelfde patroon, hoewel niet alle diagramtypen een “explosie”‑eigenschap blootleggen.

## Hoe een partje te exploderen in andere diagramtypen

Alleen taart‑type diagrammen bieden de `SetExplosion`‑methode. Als je deze oproept op een staafdiagram, gooit de API een `ArgumentException`. In die gevallen kun je overwegen om gegevenslabels of call‑outs te gebruiken om een specifieke staaf te benadrukken.

## Hoe een kleur in te stellen op een serie in plaats van één partje

Wil je dat elk partje in een serie dezelfde kleur heeft, loop dan over de datapunten:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Deze aanpak is handig wanneer je een uniform kleurenpalet over meerdere diagrammen nodig hebt.

## Hoe een Word‑document in andere formaten op te slaan

Aspose.Words kan exporteren naar PDF, HTML en vele andere formaten. Verander de bestandsextensie in `Save` en geef eventueel een `SaveOptions`‑object door:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

De diagram‑renderengine converteert het diagram automatisch naar het doelformaat, waarbij kleuren en explosie‑instellingen behouden blijven.

## Conclusie

Je weet nu hoe je een **taartdiagram** in een Word‑document kunt **maken**, de weergave kunt aanpassen door een **partje te exploderen** en **een kleur in te stellen**, en uiteindelijk het **Word‑document** kunt **opslaan** met het diagram erin ingebed. Dit end‑to‑end‑voorbeeld biedt een solide basis voor het automatiseren van rapportgeneratie, dashboards of elke situatie waarin visuele data programmatisch moet worden ingevoegd.

### Volgende stappen

* Verken andere diagramtypen (`ChartType.Column`, `ChartType.Line`) om je rapportagetoolkit uit te breiden.  
* Combineer meerdere diagrammen in één document om uitgebreide dashboards te bouwen.  
* Experimenteer met `ChartDataLabel` om percentages of waarden direct op de partjes weer te geven.  

Voel je vrij om de code aan te passen aan je eigen gegevensbronnen — of je nu waarden uit een database, een API of een CSV‑bestand haalt, dezelfde Aspose.Words‑workflow is van toepassing. Veel plezier met diagrammen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}