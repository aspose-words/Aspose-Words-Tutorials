---
category: general
date: 2026-07-19
description: Explode taartdiagramsegment met Aspose.Words voor C#. Leer hoe je een
  taartpunt kunt exploderen, de grootte van het donutgat kunt aanpassen en snel de
  gegevenspunten van de grafiek kunt wijzigen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: nl
lastmod: 2026-07-19
og_description: Explode taartdiagramsegment met Aspose.Words voor C#. Deze gids laat
  zien hoe je een taartsegment kunt exploderen, de grootte van het donutgat kunt aanpassen
  en efficiënt diagramgegevenspunten kunt wijzigen.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Taartdiagramsegment laten exploderen in C# – Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Taartdiagramsegment laten exploderen in C# met Aspose.Words – Volledige gids
url: /nl/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Explode-piechartsegment in C# met Aspose.Words – Volledige gids

Heb je je ooit afgevraagd hoe je **een piechartsegment kunt exploderen** in een Word‑document met C#? Je bent niet de enige. Of je nu een sales‑presentatie voorbereidt of enquête‑resultaten visualiseert, een geëxplodeerd segment trekt de aandacht precies daar waar je wilt. In deze tutorial lopen we het volledige proces door – een document laden, de grafiek ophalen, het eerste segment exploderen, een donut‑gat aanpassen en zelfs de gegevenspunten van de grafiek wijzigen.

We behandelen ook de secundaire concepten waar je misschien naar op zoek bent: **hoe je een pie‑segment explodeert**, **de grootte van het donut‑gat aanpassen**, en **grafiek‑gegevenspunten wijzigen**. Geen poespas, alleen een complete, copy‑paste‑klare oplossing.

---

## Wat je nodig hebt

Voordat we beginnen, zorg dat je het volgende hebt:

- **Aspose.Words for .NET** (de nieuwste versie op 2026‑07‑19). Je kunt het via NuGet installeren met `Install-Package Aspose.Words`.
- Een **.NET 6+**‑project (of .NET Framework 4.7.2+ als je nog legacy gebruikt).
- Een Word‑bestand (`Chart.docx`) dat al een taart‑ of donut‑grafiek bevat. Als je er geen hebt, maak dan snel een grafiek in Word en sla die op.

Dat is alles – geen extra libraries, geen COM‑interop, alleen pure managed code.

---

## Explode-piechartsegment – Stapsgewijze implementatie

Hieronder splitsen we de taak op in hapklare stappen. Elke sectie heeft een duidelijke kop, een code‑fragment en een korte uitleg *waarom* we doen wat we doen.

### Stap 1: Installeer en referentieer Aspose.Words

Allereerst voeg je het Aspose.Words‑pakket toe aan je project. In de Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Pro tip:** Als je de ingebouwde NuGet‑UI van Visual Studio gebruikt, zoek dan naar “Aspose.Words” en klik op Install. Zo krijg je de laatste bug‑fixes en kun je meteen met grafieken werken.

### Stap 2: Laad het Word‑document dat de grafiek bevat

We hebben een `Document`‑object nodig dat wijst naar de `.docx` met de grafiek die je wilt aanpassen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Waarom dit belangrijk is:** `Document` is het startpunt voor elke bewerking in Aspose.Words. Door vroegtijdig op grafieken te controleren, voorkom je een null‑referentie later wanneer je een segment wilt exploderen.

### Stap 3: Haal de eerste grafiek‑node op

De meeste voorbeelden gaan uit van één grafiek, dus pakken we de eerste. Als je meerdere grafieken hebt, pas dan de index aan.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Opmerking:** De cast naar `Chart` is veilig nadat we hebben bevestigd dat er een grafiek bestaat. Dit object geeft ons toegang tot series, gegevenspunten en grafiek‑type‑specifieke instellingen.

### Stap 4: Explode het eerste segment van een taartgrafiek

Nu het hoogtepunt – **hoe je een pie‑segment explodeert**. We stellen de `Exploded`‑eigenschap van het eerste gegevenspunt in.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Waarom dit werkt:** `Exploded` vertelt Word dat dat segment van het midden moet worden getrokken, waardoor het klassieke “exploded pie”‑effect ontstaat. De eigenschap is een boolean, dus `true` zet het effect aan.

### Stap 5: Pas de grootte van het donut‑gat aan (indien een donut‑grafiek)

Als je grafiek een donut is, wil je misschien **de grootte van het donut‑gat aanpassen**. De gatgrootte is een percentage van de straal van de grafiek.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Wat het getal betekent:** Een waarde van `30` betekent dat de binnenste cirkel 30 % van de totale straal inneemt, waardoor de buitenste ring dikker wordt.

### Stap 6: Wijzig grafiek‑gegevenspunten (optioneel)

Soms moet je **grafiek‑gegevenspunten wijzigen** – misschien heb je de onderliggende cijfers bijgewerkt en wil je dat de visualisatie dat weerspiegelt.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Waarom je dit zou doen:** Het wijzigen van de waarde van een gegevenspunt rekent automatisch de percentages van de segmenten opnieuw uit, waardoor de grafiek accuraat blijft zonder handmatige bewerking in Word.

### Stap 7: Sla het gewijzigde document op

Tot slot schrijf je de wijzigingen terug naar schijf. Je kunt het origineel overschrijven of een nieuw bestand maken – hoe jij wilt.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Tip:** Gebruik `SaveFormat.Docx` als je expliciet wilt zijn, maar `Save(string)` detecteert automatisch het formaat aan de hand van de bestandsextensie.

---

## Verwacht resultaat

Wanneer je `FormattedChart.docx` opent in Microsoft Word, zie je:

- Het eerste segment van een taartgrafiek **geëxplodeerd** naar buiten.
- Als de grafiek een donut is, neemt het centrale gat nu **30 %** van de straal in.
- Eventueel gewijzigde gegevenspunten tonen de nieuwe waarden die je hebt ingesteld.

Hieronder een mock‑up van hoe het geëxplodeerde segment eruitziet (alleen ter illustratie).

![Exploded pie chart slice created with Aspose.Words in C#](exploded-pie-slice.png)

*Alt‑tekst:* **exploded pie chart slice** die een weggesleept segment toont in een Word‑document.

---

## Veelgestelde vragen & randgevallen

**Wat als de grafiek geen taart‑ of donut‑grafiek is?**  
De code controleert `ChartType` voordat `Exploded` of `HoleSize` wordt toegepast. Voor staaf‑, lijn‑ of gebiedsgrafieken bestaan die eigenschappen simpelweg niet, dus slaat de logica ze veilig over.

**Kan ik meerdere segmenten exploderen?**  
Zeker. Loop door `chart.PieChartData.Series[0].DataPoints` en zet `Exploded = true` op elke gewenste index.

**Moet ik me zorgen maken over cultuurspecifieke getalnotaties?**  
Aspose.Words slaat numerieke waarden op als doubles, onafhankelijk van locale, dus je bent veilig met komma‑ versus punt‑problemen.

**Hoe zit het met grafieken die in kop‑ of voetteksten zijn ingebed?**  
Gebruik `doc.GetChildNodes(NodeType.Chart, true)` om alle grafieken op te halen, inspecteer vervolgens `ParentNode` van elke node om te zien waar deze zich bevindt. Dezelfde explode‑logica is van toepassing.

---

## Conclusie

Je beschikt nu over een solide, copy‑paste‑klare oplossing voor **het exploderen van een pie‑segment** met Aspose.Words in C#. We hebben de volledige workflow behandeld – van het laden van het document, ophalen van de grafiek, exploderen van het segment, **de grootte van het donut‑gat aanpassen**, **grafiek‑gegevenspunten wijzigen** en uiteindelijk het bestand opslaan.

Voel je vrij om te experimenteren: probeer een ander segment te exploderen, pas de gatgrootte aan naar 45 %, of werk meerdere gegevenspunten tegelijk bij. De Aspose.Words‑API maakt deze aanpassingen moeiteloos, en de wijzigingen zijn direct zichtbaar wanneer je het Word‑bestand opent.

---

### Wat is de volgende stap?

- **Stijl het geëxplodeerde segment** (verander vulkleur, rand, of voeg een gegevenslabel toe). Zoek op “Aspose.Words chart formatting”.
- **Automatiseer batchverwerking** van meerdere documenten – loop door een map, explodeer segmenten en sla nieuwe versies op.
- **Combineer met Aspose.Slides** als je dezelfde grafiek in een PowerPoint‑presentatie nodig hebt.

Heb je meer vragen over grafiekmanipulatie, of wil je dieper ingaan op andere grafiektype­n? Laat een reactie achter hieronder, en happy coding!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementaties in je eigen projecten te verkennen.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}