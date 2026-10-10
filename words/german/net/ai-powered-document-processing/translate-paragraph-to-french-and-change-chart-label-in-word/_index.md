---
category: general
date: 2026-10-10
description: Übersetzen Sie den Absatz ins Französische und lernen Sie, wie Sie die
  Diagrammdatenbeschriftung ändern, die Diagrammdatenbeschriftung anpassen und die
  bearbeitete DOCX-Datei mit Aspose.Words AI speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: de
lastmod: 2026-10-10
og_description: Übersetzen Sie den Absatz ins Französische und lernen Sie, wie Sie
  Diagrammdatenbeschriftungen ändern, Diagrammdatenbeschriftungen anpassen und die
  bearbeitete DOCX-Datei mit Aspose.Words AI speichern.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Absatz ins Französische übersetzen und Diagrammbeschriftung in Word ändern
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
title: Absatz ins Französische übersetzen und Diagrammbeschriftung in Word ändern
url: /de/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Absatz ins Französische übersetzen und Diagrammbeschriftung in Word ändern

Wenn Sie einen **Absatz ins Französische übersetzen** müssen und gleichzeitig ein Diagramm im selben Word-Dokument aktualisieren wollen, zeigt Ihnen diese Anleitung genau, wie das geht. Mit Aspose.Words AI können Sie Text automatisch übersetzen, dann die Datenbeschriftung eines Diagramms ändern und schließlich die bearbeitete `.docx`‑Datei speichern – alles in wenigen einfachen Schritten.

Das Tutorial behandelt alles vom Laden der Quelldatei bis zum Speichern der Änderungen. Am Ende können Sie jeden Absatz übersetzen, die Datenbeschriftung eines Diagramms anpassen und eine neue Word‑Datei erstellen, die bereit für die Verteilung ist. Es werden keine externen Skripte benötigt; der gesamte Workflow befindet sich in einem einzigen C#‑Programm.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
- Eine Aspose.Words für .NET Lizenz (oder ein kostenloser Evaluierungsschlüssel)
- Internetzugang für den Google‑AI‑Übersetzer (die `Translator`‑Klasse nutzt die Google‑API im Hintergrund)
- Ein Word‑Dokument (`input.docx`), das mindestens einen Absatz und ein Diagramm enthält

## Schritt 1: Projekt einrichten und Namespaces importieren

Create a new console application and add the Aspose.Words NuGet package:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Now include the required namespaces at the top of `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

These imports give you access to document loading, AI translation, and chart editing functionality.

## Schritt 2: Quell‑Word‑Dokument laden

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Loading the file creates an in‑memory representation that you can query and modify without touching the original file on disk.

## Schritt 3: Ersten Absatz ins Französische übersetzen

The first paragraph is often a title or introductory sentence, making it a good candidate for translation. The `Translator` class abstracts the call to Google’s AI model.

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

**Why this works:**  
`paragraph.Runs.Clear()` removes all existing text runs, ensuring the new translation does not concatenate with the old content. `new Run(document, translatedText)` creates a fresh run that inherits the paragraph’s formatting.

**Warum das funktioniert:**  
`paragraph.Runs.Clear()` entfernt alle vorhandenen Text‑Runs, sodass die neue Übersetzung nicht an den alten Inhalt angehängt wird. `new Run(document, translatedText)` erzeugt einen neuen Run, der das Format des Absatzes übernimmt.

## Schritt 4: Erstes Diagramm finden und dessen Datenbeschriftung anpassen

Charts are stored as `Shape` nodes of type `NodeType.Shape`. The first chart can be fetched with `GetChild`.

Charts are stored as `Shape` nodes of type `NodeType.Shape`. The first chart can be fetched with `GetChild`.

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

**Explanation of the key steps:**

**Erklärung der wichtigsten Schritte:**

- `GetChild(NodeType.Shape, 0, true)` performs a depth‑first search and returns the first shape, which in our case is a chart.
- `ChartSeries` represents a collection of data points; the first series (`Series[0]`) typically corresponds to the primary data set.
- `ChartDataLabelPosition.OutsideEnd` moves the label outside the end of the bar, improving readability.
- Setting `dataLabel.Text` to a French string aligns the label with the translated paragraph.

- `GetChild(NodeType.Shape, 0, true)` führt eine Tiefensuche durch und gibt das erste Shape zurück, das in unserem Fall ein Diagramm ist.
- `ChartSeries` stellt eine Sammlung von Datenpunkten dar; die erste Serie (`Series[0]`) entspricht typischerweise dem primären Datensatz.
- `ChartDataLabelPosition.OutsideEnd` verschiebt die Beschriftung außerhalb des Endes des Balkens und verbessert die Lesbarkeit.
- Das Setzen von `dataLabel.Text` auf einen französischen String richtet die Beschriftung an dem übersetzten Absatz aus.

## Schritt 5: Dokument mit dem übersetzten Absatz speichern

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

At this point the document contains the French paragraph but still holds the original chart configuration.

## Schritt 6: Dokument mit dem aktualisierten Diagramm speichern

You can reuse the same `Document` instance—no need to reload it—because the chart modifications are already in memory.

Both files are now ready for distribution:

- **`translated.docx`** – contains the French paragraph.
- **`chart-updated.docx`** – contains the French paragraph *and* the customized chart label.

## Schritt 6: Dokument mit dem aktualisierten Diagramm speichern

You can reuse the same `Document` instance—no need to reload it—because the chart modifications are already in memory.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Both files are now ready for distribution:

- **`translated.docx`** – enthält den französischen Absatz.
- **`chart-updated.docx`** – enthält den französischen Absatz *und* die angepasste Diagrammbeschriftung.

## Vollständiges, ausführbares Beispiel

Below is the full program you can copy‑paste into `Program.cs`. It compiles and runs as‑is, assuming you have replaced `YOUR_DIRECTORY` with a real folder path.



## Was sollten Sie als Nächstes lernen?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}