---
category: general
date: 2026-10-10
description: Fordítsa le a bekezdést franciára, és tanulja meg, hogyan módosíthatja
  a diagram adatcímkéjét, testre szabhatja azt, valamint hogyan mentheti el a szerkesztett
  docx fájlt az Aspose.Words AI segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: hu
lastmod: 2026-10-10
og_description: Fordítsa le a bekezdést franciára, és tanulja meg, hogyan változtathatja
  meg a diagram adatcímkéjét, testre szabhatja azt, valamint hogyan mentheti el a
  szerkesztett docx fájlt az Aspose.Words AI segítségével.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Bekezdés franciára fordítása és diagramcímke módosítása Wordben
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
title: Bekezdés lefordítása franciára és diagramcímke módosítása Wordben
url: /hu/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bekezdés francia nyelvre fordítása és diagramcímke módosítása Wordben

Ha **bekezdés francia nyelvre fordítása** mellett egy diagram adatcímkéjét is módosítani szeretné ugyanabban a Word‑dokumentumban, ez az útmutató pontosan megmutatja, hogyan teheti meg. Az Aspose.Words AI segítségével automatikusan lefordíthatja a szöveget, majd módosíthatja a diagram adatcímkéjét, és végül elmentheti a szerkesztett `.docx` fájlt – mindezt néhány egyszerű lépésben.

A tutorial mindent lefed a forrásfájl betöltésétől a változtatások mentéséig. A végére képes lesz bármely bekezdést lefordítani, egy diagram adatcímkét testreszabni, és egy új Word‑fájlt előállítani, amely készen áll a terjesztésre. Külső szkriptekre nincs szükség; a teljes munkafolyamat egyetlen C# programban valósul meg.

## Előfeltételek

- .NET 6.0 vagy újabb (a kód .NET Framework 4.7+‑vel is működik)
- Aspose.Words for .NET licenc (vagy egy ingyenes értékelő kulcs)
- Internetkapcsolat a Google AI fordítóhoz (a `Translator` osztály a Google API‑t használja a háttérben)
- Egy Word‑dokumentum (`input.docx`), amely legalább egy bekezdést és egy diagramot tartalmaz

## 1. lépés: A projekt beállítása és a névtér importálása

Hozzon létre egy új konzolalkalmazást, és adja hozzá az Aspose.Words NuGet csomagot:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Most vegye fel a szükséges névtereket a `Program.cs` tetején:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Ezek az importok hozzáférést biztosítanak a dokumentum betöltéséhez, az AI fordításhoz és a diagram szerkesztéséhez.

## 2. lépés: A forrás Word‑dokumentum betöltése

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

A fájl betöltése egy memóriában létező reprezentációt hoz létre, amelyet lekérdezhet és módosíthat anélkül, hogy az eredeti fájlt a lemezen érintené.

## 3. lépés: Az első bekezdés francia nyelvre fordítása

Az első bekezdés gyakran cím vagy bevezető mondat, így jó jelölt a fordításhoz. A `Translator` osztály elrejti a Google AI modell hívását.

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

**Miért működik ez:**  
`paragraph.Runs.Clear()` eltávolítja az összes meglévő szövegrészt, biztosítva, hogy az új fordítás ne fűződjön össze a régi tartalommal. `new Run(document, translatedText)` egy friss részt hoz létre, amely örökli a bekezdés formázását.

## 4. lépés: Az első diagram megtalálása és adatcímkéjének testreszabása

A diagramok `Shape` típusú `NodeType.Shape` csomópontként tárolódnak. Az első diagram a `GetChild` metódussal kérhető le.

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

**A kulcsfontosságú lépések magyarázata:**

- `GetChild(NodeType.Shape, 0, true)` mélységi keresést végez, és visszaadja az első alakzatot, amely jelen esetben egy diagram.
- A `ChartSeries` adatpontok gyűjteményét képviseli; az első sorozat (`Series[0]`) általában az elsődleges adatkészletnek felel meg.
- A `ChartDataLabelPosition.OutsideEnd` a címkét a sáv végén kívülre helyezi, javítva az olvashatóságot.
- A `dataLabel.Text` francia nyelvű szövegre állítása összhangba hozza a címkét a lefordított bekezdéssel.

## 5. lépés: A dokumentum mentése a lefordított bekezdéssel

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

Ezen a ponton a dokumentum már tartalmazza a francia bekezdést, de még mindig a régi diagramkonfigurációt őrzi.

## 6. lépés: A dokumentum mentése a frissített diagrammal

Ugyanazt a `Document` példányt újra felhasználhatja – nincs szükség újratöltésre –, mivel a diagram módosításai már a memóriában vannak.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Mindkét fájl most már készen áll a terjesztésre:

- **`translated.docx`** – a francia bekezdést tartalmazza.
- **`chart-updated.docx`** – a francia bekezdést *és* a testreszabott diagramcímkét tartalmazza.

## Teljes, futtatható példa

Az alábbi teljes programot másolja be a `Program.cs`‑be. Fordítható és futtatható úgy, ahogy van, feltéve, hogy a `YOUR_DIRECTORY`‑t egy valós mappára cserélte.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

namespace WordAiDemo
{
    class Program
    {
        static void Main()
        {
            // ---------- Load the source document ----------
            string inputPath = @"YOUR_DIRECTORY/input.docx";
            Document document = new Document(inputPath);
            Console.WriteLine("Document loaded.");

            // ---------- Translate the first paragraph ----------
            Paragraph paragraph = document.FirstSection.Body.FirstParagraph;
            string original = paragraph.GetText();
            string translated = Translator.Translate(original, Language.French);
            Console.WriteLine


## Mit érdemes legközelebb megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy segítsen elsajátítani további API‑funkciókat és alternatív megvalósítási módokat saját projektjeiben.

- [Diagramadatcímke testreszabása](/words/english/net/programming-with-charts/chart-data-label/)
- [Adatcímke számformázása diagramon](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Diagram adatcímke](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}