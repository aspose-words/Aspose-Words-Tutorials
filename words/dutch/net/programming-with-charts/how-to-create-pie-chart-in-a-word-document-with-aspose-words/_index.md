---
category: general
date: 2026-09-21
description: Leer hoe je een cirkeldiagram maakt en een diagram in Word invoegt met
  Aspose.Words, gegevenslabels toevoegt aan het cirkeldiagram en percentages weergeeft
  op het cirkeldiagram in slechts een paar stappen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: nl
lastmod: 2026-09-21
og_description: Maak een taartdiagram in Word met Aspose.Words, voeg het diagram in
  Word in, voeg gegevenslabels toe aan het taartdiagram en toon percentages op het
  taartdiagram – allemaal met duidelijke codevoorbeelden.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Maak een cirkeldiagram in Word met Aspose.Words – stapsgewijze handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Hoe maak je een cirkeldiagram in een Word‑document met Aspose.Words
url: /nl/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe maak je een taartdiagram in een Word‑document met Aspose.Words

Als je programmatically **pie chart maken** wilt, maakt Aspose.Words het eenvoudig. In deze tutorial zie je hoe je **chart in Word invoegen** kunt, de series configureert, **data labels aan pie chart toevoegen**, en uiteindelijk **percentages op pie chart weergeven** zodat de visualisatie exacte waarden toont. Aan het einde heb je een compleet, uitvoerbaar voorbeeld dat je in elk .NET‑project kunt plaatsen.

Deze gids behandelt alles wat je moet weten: vereiste NuGet‑pakketten, de volledige C#‑broncode, uitleg waarom elke API‑aanroep belangrijk is, en tips voor het aanpassen van het diagram. Er is geen externe documentatie nodig—kopieer, voer uit en pas aan.

## Vereisten

* .NET 6.0 SDK of later geïnstalleerd.  
* Visual Studio 2022 (of een IDE die .NET ondersteunt).  
* Een Aspose.Words for .NET‑licentie (de gratis proefversie werkt voor testen).  
* Basiskennis van C# en Word‑documentstructuren.

Als je deze al hebt, kun je direct naar de code gaan.

## Stap 1: Het project opzetten en Aspose.Words importeren

Maak een nieuw console‑project aan en voeg het Aspose.Words‑NuGet‑pakket toe:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Het pakket bevat de `Aspose.Words.Drawing.Charts`‑namespace, die de `Chart`‑ en `ChartSeries`‑klassen bevat die we gaan gebruiken.

> **Pro tip:** Bewaar je licentiebestand (`Aspose.Words.lic`) in de project‑root en laad het bij opstarten om evaluatiewatermerken te vermijden.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Stap 2: Een leeg document en een DocumentBuilder maken

Een `Document` vertegenwoordigt het Word‑bestand, terwijl `DocumentBuilder` een vloeiende API biedt voor het invoegen van inhoud.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Waarom dit belangrijk is:** De `DocumentBuilder` behoudt het huidige invoegpunt, waardoor het diagram precies op de gewenste plaats in de documentstroom verschijnt.

## Stap 3: Een taartdiagram in het Word‑document invoegen

Nu **chart in Word invoegen**. De `InsertChart`‑methode neemt het diagramtype, de breedte en de hoogte (in punten) als parameters.

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

Op dit moment bevat het diagram een standaard gegevensreeks met tijdelijke waarden (25, 25, 25, 25). Je kunt ze later vervangen indien nodig.

## Stap 4: De eerste reeks benaderen en data‑labels aanpassen

Een taartdiagram heeft doorgaans één reeks. Om **data labels aan pie chart toevoegen**, halen we deze op en schakelen we de weergave van percentages in.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Waarom we `ShowPercentage` instellen:** Deze vlag vertelt Aspose.Words om de bijdrage van elke part te berekenen en als percentage weer te geven. De `Position`‑eigenschap zorgt ervoor dat het label niet overlapt met de part, wat de leesbaarheid verbetert—vooral wanneer de delen klein zijn.

## Stap 5: (Optioneel) Vervang de tijdelijke gegevens

Als je specifieke waarden wilt, vervang dan de standaardpunten:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

De weergegeven percentages passen zich automatisch aan om de nieuwe waarden weer te geven.

## Stap 6: Het document opslaan

Schrijf tenslotte het document naar schijf. De extensie bepaalt het formaat; `.docx` maakt een modern Word‑bestand.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Het uitvoeren van het programma genereert een bestand met de naam **PieChart.docx** in de uitvoermap. Het openen in Microsoft Word toont een taartdiagram waarbij elke part gelabeld is met zijn percentage, geplaatst buiten de delen.

### Verwachte output

Wanneer je het gegenereerde document opent, zou je moeten zien:

* Een enkel taartdiagram, 400 × 300 pt groot.  
* Vier delen (of zoveel punten als je hebt toegevoegd).  
* Percentage‑labels zoals “40 %”, “30 %”, enz., weergegeven buiten elke part.

Als de labels binnen de delen verschijnen, controleer dan of `ChartDataLabelPosition.OutsideEnd` correct is ingesteld.

## Stap 7: Veelvoorkomende variaties en randgevallen

### Een titel aan het diagram toevoegen

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Kleuren van de delen wijzigen

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Een lege reeks verwerken

Als je gegevensbron leeg kan zijn, bescherm dan tegen `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Exporteren naar PDF in plaats van Word

Dezelfde diagram‑renderlogica is van toepassing; Aspose.Words converteert de Word‑indeling automatisch naar PDF.

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

## Volledige broncode

Hieronder staat het volledige, kant‑klaar programma. Kopieer het naar `Program.cs` en voer `dotnet run` uit.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Conclusie

Je weet nu hoe je **pie chart maken** in een Word‑bestand met Aspose.Words, **chart in Word invoegen**, **data labels aan pie chart toevoegen**, en **percentages op pie chart weergeven**. Het voorbeeld toont de volledige workflow—van projectopzet tot het einddocument—zodat je het kunt aanpassen voor dashboards, rapporten of geautomatiseerde factuurgeneratie.  

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **hoe percentages in diagram‑legenda's weer te geven**, het aanpassen van diagramkleuren, of het converteren van het Word‑document naar PDF voor distributie. Experimenteer met verschillende diagramtypen (Bar, Line) met dezelfde `InsertChart`‑methode om je automatiseringsmogelijkheden uit te breiden.

Veel plezier met diagrammen!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Kolomdiagram in Word invoegen met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Word Scatter‑diagram maken met Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Area‑diagram in Word‑document invoegen | Aspose.Words voor .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}