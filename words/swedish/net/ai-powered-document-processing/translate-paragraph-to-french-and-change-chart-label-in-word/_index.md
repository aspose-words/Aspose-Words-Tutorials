---
category: general
date: 2026-10-10
description: Översätt stycket till franska och lär dig hur du ändrar diagrammets datamärkning,
  anpassar diagrammets datamärkning och sparar den redigerade docx-filen med Aspose.Words
  AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: sv
lastmod: 2026-10-10
og_description: Översätt stycket till franska och lär dig hur du ändrar diagrammets
  datamärkning, anpassar diagrammets datamärkning och sparar den redigerade docx-filen
  med Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Översätt stycke till franska och ändra diagrametikett i Word
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
title: Översätt stycke till franska och ändra diagrametikett i Word
url: /sv/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Översätt stycke till franska och ändra diagrametikett i Word

Om du behöver **translate paragraph to French** samtidigt som du uppdaterar ett diagram i samma Word‑dokument, visar den här guiden exakt hur du gör. Med Aspose.Words AI kan du automatiskt översätta text, sedan ändra ett diagrammets datamärkning och slutligen spara den redigerade `.docx`‑filen – allt i några enkla steg.

Handledningen täcker allt från att läsa in källfilen till att spara ändringarna. När du är klar kan du översätta vilket stycke som helst, anpassa en diagramdatamärkning och skapa en ny Word‑fil klar för distribution. Inga externa skript behövs; hela arbetsflödet finns i ett enda C#‑program.

## Förutsättningar

- .NET 6.0 eller senare (koden fungerar också med .NET Framework 4.7+)
- En Aspose.Words for .NET‑licens (eller en gratis utvärderingsnyckel)
- Internetåtkomst för Google AI‑översättaren (klassen `Translator` använder Googles API under huven)
- Ett Word‑dokument (`input.docx`) som innehåller minst ett stycke och ett diagram

## Steg 1: Skapa projektet och importera namnrymder

Skapa en ny konsolapplikation och lägg till Aspose.Words‑NuGet‑paketet:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Inkludera nu de nödvändiga namnrymderna högst upp i `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Dessa importeringar ger dig åtkomst till dokumentladdning, AI‑översättning och diagramredigeringsfunktionalitet.

## Steg 2: Läs in källdokumentet

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

När filen läses in skapas en minnesrepresentation som du kan fråga och modifiera utan att röra den ursprungliga filen på disken.

## Steg 3: Översätt det första stycket till franska

Det första stycket är ofta en rubrik eller inledande mening, vilket gör det till en bra kandidat för översättning. Klassen `Translator` abstraherar anropet till Googles AI‑modell.

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

**Varför detta fungerar:**  
`paragraph.Runs.Clear()` tar bort alla befintliga text‑runs, vilket säkerställer att den nya översättningen inte kedjas ihop med det gamla innehållet. `new Run(document, translatedText)` skapar en ny run som ärver styckets formatering.

## Steg 4: Hitta det första diagrammet och anpassa dess datamärkning

Diagram lagras som `Shape`‑noder av typen `NodeType.Shape`. Det första diagrammet kan hämtas med `GetChild`.

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

**Förklaring av de viktigaste stegen:**

- `GetChild(NodeType.Shape, 0, true)` utför en djup‑först‑sökning och returnerar den första formen, vilket i vårt fall är ett diagram.
- `ChartSeries` representerar en samling datapunkter; den första serien (`Series[0]`) motsvarar vanligtvis huvuddatamängden.
- `ChartDataLabelPosition.OutsideEnd` flyttar etiketten utanför stapelns slut, vilket förbättrar läsbarheten.
- Att sätta `dataLabel.Text` till en fransk sträng anpassar etiketten till det översatta stycket.

## Steg 5: Spara dokumentet med det översatta stycket

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

På den här punkten innehåller dokumentet det franska stycket men behåller fortfarande den ursprungliga diagramkonfigurationen.

## Steg 6: Spara dokumentet med det uppdaterade diagrammet

Du kan återanvända samma `Document`‑instans – ingen behov av att läsa in den igen – eftersom diagramändringarna redan finns i minnet.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Båda filerna är nu klara för distribution:

- **`translated.docx`** – innehåller det franska stycket.
- **`chart-updated.docx`** – innehåller det franska stycket *och* den anpassade diagrametiketten.

## Komplett, körbart exempel

Nedan är hela programmet som du kan kopiera‑klistra in i `Program.cs`. Det kompileras och körs som det är, förutsatt att du har ersatt `YOUR_DIRECTORY` med en riktig sökväg.



## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstreras i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationssätt i dina egna projekt.

- [Anpassa diagrammets datamärkning](/words/english/net/programming-with-charts/chart-data-label/)
- [Formatera antal datamärkningar i ett diagram](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Diagramdatamärkning](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}