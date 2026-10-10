---
category: general
date: 2026-10-10
description: Vertaal de alinea naar het Frans en leer hoe je het gegevenslabel van
  een grafiek wijzigt, het gegevenslabel van een grafiek aanpast en een bewerkt docx‑bestand
  opslaat met Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: nl
lastmod: 2026-10-10
og_description: Vertaal alinea naar het Frans en leer hoe je het gegevenslabel van
  een grafiek wijzigt, het gegevenslabel van een grafiek aanpast, en een bewerkte
  docx‑bestand opslaat met Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Vertaal alinea naar het Frans en wijzig de grafiektitel in Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Vertaal alinea naar het Frans en wijzig grafieklabel in Word
url: /nl/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Paragraaf naar het Frans vertalen en grafieklabel wijzigen in Word

Als je een **paragraaf naar het Frans wilt vertalen** en tegelijkertijd een grafiek in hetzelfde Word‑document wilt bijwerken, laat deze gids je precies zien hoe. Met Aspose.Words AI kun je tekst automatisch vertalen, vervolgens een grafiek‑databelabel aanpassen en tenslotte het bewerkte `.docx`‑bestand opslaan — alles in een paar eenvoudige stappen.

De tutorial behandelt alles, van het laden van het bronbestand tot het opslaan van de wijzigingen. Aan het einde kun je elke paragraaf vertalen, een grafiek‑databelabel aanpassen en een nieuw Word‑bestand maken dat klaar is voor distributie. Er zijn geen externe scripts nodig; de volledige workflow bevindt zich in één enkel C#‑programma.

## Vereisten

- .NET 6.0 of later (de code werkt ook met .NET Framework 4.7+)
- Een Aspose.Words for .NET‑licentie (of een gratis evaluatiesleutel)
- Internettoegang voor de Google AI‑vertaler (de `Translator`‑klasse maakt gebruik van de Google‑API onder de motorkap)
- Een Word‑document (`input.docx`) dat minstens één paragraaf en één grafiek bevat

## Stap 1: Het project opzetten en namespaces importeren

Maak een nieuwe console‑applicatie aan en voeg het Aspose.Words‑NuGet‑pakket toe:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Voeg nu de vereiste namespaces toe aan de bovenkant van `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Deze imports geven je toegang tot document‑laden, AI‑vertaling en grafiek‑bewerkingsfunctionaliteit.

## Stap 2: Het bron‑Word‑document laden

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Het laden van het bestand maakt een in‑memory‑representatie aan die je kunt opvragen en aanpassen zonder het oorspronkelijke bestand op schijf aan te raken.

## Stap 3: De eerste paragraaf naar het Frans vertalen

De eerste paragraaf is vaak een titel of inleidende zin, waardoor deze een goede kandidaat is voor vertaling. De `Translator`‑klasse abstraheert de oproep naar het AI‑model van Google.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Waarom dit werkt:**  
`paragraph.Runs.Clear()` verwijdert alle bestaande tekst‑runs, zodat de nieuwe vertaling niet wordt samengevoegd met de oude inhoud. `new Run(document, translatedText)` maakt een nieuwe run aan die de opmaak van de paragraaf erft.

## Stap 4: De eerste grafiek vinden en het databelabel aanpassen

Grafieken worden opgeslagen als `Shape`‑nodes van het type `NodeType.Shape`. De eerste grafiek kan worden opgehaald met `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Uitleg van de belangrijkste stappen:**

- `GetChild(NodeType.Shape, 0, true)` voert een diepte‑eerste zoekopdracht uit en retourneert de eerste shape, die in ons geval een grafiek is.
- `ChartSeries` vertegenwoordigt een verzameling datapunten; de eerste serie (`Series[0]`) komt doorgaans overeen met de primaire dataset.
- `ChartDataLabelPosition.OutsideEnd` verplaatst het label naar buiten het einde van de balk, waardoor de leesbaarheid verbetert.
- Het instellen van `dataLabel.Text` op een Franse tekenreeks zorgt ervoor dat het label overeenkomt met de vertaalde paragraaf.

## Stap 5: Het document opslaan met de vertaalde paragraaf

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

Op dit moment bevat het document de Franse paragraaf, maar behoudt nog steeds de oorspronkelijke grafiekconfiguratie.

## Stap 6: Het document opslaan met de bijgewerkte grafiek

Je kunt dezelfde `Document`‑instantie hergebruiken — geen herladen nodig — omdat de grafiekaanpassingen al in het geheugen staan.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Beide bestanden zijn nu klaar voor distributie:

- **`translated.docx`** – bevat de Franse paragraaf.
- **`chart-updated.docx`** – bevat de Franse paragraaf *en* het aangepaste grafieklabel.

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑en‑plakken in `Program.cs`. Het compileert en draait direct, ervan uitgaande dat je `YOUR_DIRECTORY` hebt vervangen door een echt mappad.



## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Grafiekdatabelabel aanpassen](/words/english/net/programming-with-charts/chart-data-label/)
- [Aantal datalabels in een grafiek opmaken](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Grafiekdatabelabel](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}