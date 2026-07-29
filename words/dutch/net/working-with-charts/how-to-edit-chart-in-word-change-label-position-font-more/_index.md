---
category: general
date: 2026-07-29
description: Hoe een grafiek in een Word‑document te bewerken – leer de positie van
  grafieklabels te wijzigen, balkgrafieklabels aan te passen, gegevenslabels van de
  grafiek te wijzigen en het lettertype van grafieklabels te veranderen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: nl
lastmod: 2026-07-29
og_description: Hoe je snel een grafiek in Word bewerkt. Beheers het wijzigen van
  de positie van grafieklabels, het aanpassen van staafgrafieklabels, het wijzigen
  van gegevenslabels en het veranderen van het lettertype van grafieklabels.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Hoe een grafiek in Word bewerken – Labels en lettertype wijzigen
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Hoe een grafiek in Word te bewerken: labelpositie, lettertype en meer wijzigen'
url: /nl/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een diagram in Word bewerken: labelpositie, lettertype & meer

Het bewerken van een diagram in een Word‑document is een veelvoorkomende behoefte wanneer je wilt dat je rapporten er professioneel uitzien. Heb je ooit moeite gehad om **change chart label position** te wijzigen of de labels leesbaar te maken zonder eindeloze menu's door te zoeken? Je bent niet alleen—de meeste ontwikkelaars lopen tegen deze muur aan bij het automatiseren van rapportgeneratie. In deze gids lopen we een volledig, uitvoerbaar voorbeeld door dat precies laat zien hoe je **adjust bar chart labels**, **modify chart data labels**, en **change chart label font** kunt gebruiken met C# en de Aspose.Words‑bibliotheek.

## Wat je zult leren

- Laad een .docx‑bestand dat al een staafdiagram bevat.  
- Haal de eerste diagramvorm op en krijg toegang tot de data‑labelcollectie.  
- **Change chart label position** om de balken er netter uit te laten zien.  
- **Adjust bar chart labels** lettergrootte aanpassen voor betere leesbaarheid.  
- Sla het gewijzigde document op naar schijf.  

> **Prerequisites**  
> - .NET 6.0 of later (de code werkt ook op .NET Framework 4.7+).  
> - Aspose.Words for .NET (beschikbaar via NuGet).  
> - Een Word‑bestand (`BarChart.docx`) dat al een staafdiagram bevat.  

Als je een van deze mist, download dan nu het nieuwste Aspose.Words‑pakket:

```bash
dotnet add package Aspose.Words
```

---

## Hoe een diagram bewerken: het diagram uit het Word‑document ophalen

De eerste stap in **how to edit chart**‑objecten is het laden van het document en het vinden van de diagramvorm. Aspose.Words behandelt diagrammen als `Shape`‑nodes, dus we kunnen `GetChild` met `NodeType.Shape` gebruiken om het eerste diagram dat we tegenkomen op te halen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> Door direct toegang te krijgen tot het `Chart`‑object, vermijd je de overhead van het openen van het bestand in Word en het handmatig aanpassen van elk label. Dit is de hoeksteen van elke **modify chart data labels**‑automatisering.

## Staafdiagramlabels aanpassen: diagramlabelpositie wijzigen

Nu we de `Chart`‑instantie hebben, laten we itereren over de `DataLabelCollection`. Het doel is om **change chart label position** te wijzigen zodat elk label netjes binnen de basis van zijn balk zit, in plaats van ongemakkelijk erboven te zweven.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> `InsideBase` werkt goed voor verticale staafdiagrammen. Als je een horizontaal staafdiagram hebt, probeer dan `InsideEnd`. Experimenteren met posities is goedkoop—voer de code gewoon opnieuw uit en open het opgeslagen document.

## Diagramlabellettertype wijzigen: lettergrootte aanpassen voor leesbaarheid

Een klein lettertype is de stille moordenaar van rapportduidelijkheid. Om **change chart label font** te wijzigen, stel je simpelweg de eigenschap `Font.Size` in op elk `ChartDataLabel`. We verhogen het naar 9 pt, wat een goede balans is voor de meeste afgedrukte rapporten.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Why we do this:**  
> Het aanpassen van de lettergrootte maakt deel uit van **modify chart data labels**‑best practices. Grotere letters verbeteren de toegankelijkheid en verminderen de noodzaak voor handmatige post‑processing.

## Het bijgewerkte document opslaan

Na het aanpassen van posities en lettertypen is de laatste stap in **how to edit chart** het opslaan van de wijzigingen. Aspose.Words maakt dit met één regel code.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Open `BarChartCustomLabels.docx` in Word en je ziet de labels netjes binnen de balken, weergegeven met een duidelijk 9 pt lettertype. Geen gekreuk meer over kleine cijfers.

---

## Volledig werkend voorbeeld (alle stappen in één bestand)

Hieronder staat een compleet, kant‑klaar console‑programma dat de volledige workflow demonstreert—van het laden van het document tot het opslaan van de bijgewerkte versie. Kopieer‑en‑plak het in een nieuw .NET console‑project en druk op **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Expected output** wanneer je het programma uitvoert:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Open het resulterende bestand en je ziet de **adjust bar chart labels** gepositioneerd binnen de balken met een comfortabel lettertype.

---

## Veelgestelde vragen & randgevallen

### Wat als het document meerdere diagrammen bevat?

De bovenstaande code haalt het *eerste* diagram op (`GetChild(NodeType.Shape, 0, true)`). Om alle diagrammen te bewerken, vervang je de enkele ophalen door een lus:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Hoe **change chart label font** voor slechts één specifieke serie?

Elke `ChartSeries` heeft zijn eigen `DataLabelCollection`. Richt je op een serie via de index:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Werkt dit met taart‑ of lijndiagrammen?

Ja—`ChartDataLabelPosition` ondersteunt waarden zoals `InsideEnd`, `OutsideEnd` en `BestFit`. Voor een taartdiagram kun je `OutsideEnd` verkiezen om de labels leesbaar te houden.

### Hoe zit het met lokalisatie (bijv. verschillende decimale scheidingstekens)?

Aspose.Words respecteert de locale‑instellingen van het document. Als je een specifiek formaat moet afdwingen, pas dan `label.NumberFormat` aan vóór het opslaan.

---

## Samenvatting & vervolgstappen

We hebben **how to edit chart**‑objecten in een Word‑document van begin tot eind behandeld: het laden van het bestand, het ophalen van het diagram, **changing chart label position**, **adjusting bar chart labels**, **modifying chart data labels**, en uiteindelijk **changing chart label font** vóór het opslaan. Het volledige voorbeeld is productie‑klaar en kan in elke automatiseringspipeline worden geïntegreerd.

Klaar om een stap hoger te gaan? Overweeg deze vervolgidées:

- **Add data label colors** (`dataLabel.Font.Color = Color.Blue;`).  
- **Show values as percentages** (`dataLabel.NumberFormat = "0%";`).  
- **Create charts programmatically** in plaats van bestaande te laden.  

Al deze opties bouwen voort op dezelfde API‑surface die we vandaag hebben gebruikt, dus je voelt je meteen thuis.

Als je tegen problemen aanloopt, laat dan een reactie achter of raadpleeg de Aspose.Words‑documentatie voor diepere diagram‑aanpassingsopties. Veel programmeerplezier, en geniet van die prachtig gelabelde diagrammen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Grafiekgegevenslabel aanpassen](/words/english/net/programming-with-charts/chart-data-label/)
- [Aantal gegevenslabels in een grafiek opmaken](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Grafiekgegevenslabel](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}