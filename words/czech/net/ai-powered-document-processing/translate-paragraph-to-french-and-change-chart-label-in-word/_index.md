---
category: general
date: 2026-10-10
description: Přeložte odstavec do francouzštiny a naučte se, jak změnit popisek dat
  v grafu, přizpůsobit popisek dat v grafu a uložit upravený soubor docx pomocí Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: cs
lastmod: 2026-10-10
og_description: Přeložte odstavec do francouzštiny a naučte se, jak změnit popisek
  dat v grafu, přizpůsobit popisek dat v grafu a uložit upravený soubor docx pomocí
  Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Přeložit odstavec do francouzštiny a změnit popisek grafu ve Wordu
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
title: Přeložit odstavec do francouzštiny a změnit popisek grafu ve Wordu
url: /cs/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přeložit odstavec do francouzštiny a změnit popisek grafu ve Wordu

Pokud potřebujete **přeložit odstavec do francouzštiny** a zároveň aktualizovat graf ve stejném dokumentu Word, tento návod vám přesně ukáže, jak na to. Pomocí Aspose.Words AI můžete automaticky přeložit text, poté upravit popisek dat v grafu a nakonec uložit upravený soubor `.docx` – vše během několika jednoduchých kroků.

Tutoriál pokrývá vše od načtení zdrojového souboru až po uložení změn. Na konci budete schopni přeložit libovolný odstavec, přizpůsobit popisek dat v grafu a vytvořit nový soubor Word připravený k distribuci. Žádné externí skripty nejsou potřeba; celý pracovní postup běží v jediném C# programu.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7+)
- Licence Aspose.Words pro .NET (nebo bezplatný evaluační klíč)
- Přístup k internetu pro překladač Google AI (třída `Translator` používá pod kapotou API Google)
- Dokument Word (`input.docx`), který obsahuje alespoň jeden odstavec a jeden graf

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte novou konzolovou aplikaci a přidejte balíček Aspose.Words NuGet:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Nyní zahrňte požadované jmenné prostory na začátek souboru `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Tyto importy vám poskytují přístup k načítání dokumentu, AI překladu a funkci úpravy grafu.

## Krok 2: Načtení zdrojového dokumentu Word

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Načtení souboru vytvoří v‑paměti reprezentaci, kterou můžete dotazovat a upravovat, aniž byste se dotkli původního souboru na disku.

## Krok 3: Překlad prvního odstavce do francouzštiny

První odstavec je často titulek nebo úvodní věta, což z něj dělá dobrý kandidát na překlad. Třída `Translator` abstrahuje volání na AI model Google.

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

**Proč to funguje:**  
`paragraph.Runs.Clear()` odstraní všechny existující textové běhy, čímž zajistí, že nový překlad se nespojí se starým obsahem. `new Run(document, translatedText)` vytvoří nový běh, který dědí formátování odstavce.

## Krok 4: Vyhledání prvního grafu a přizpůsobení jeho popisku dat

Grafy jsou uloženy jako uzly `Shape` typu `NodeType.Shape`. První graf lze získat pomocí `GetChild`.

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

**Vysvětlení klíčových kroků:**

- `GetChild(NodeType.Shape, 0, true)` provádí prohledávání do hloubky a vrací první tvar, který je v našem případě graf.
- `ChartSeries` představuje kolekci datových bodů; první série (`Series[0]`) obvykle odpovídá hlavnímu datovému souboru.
- `ChartDataLabelPosition.OutsideEnd` přesune popisek mimo konec sloupce, čímž zlepšuje čitelnost.
- Nastavení `dataLabel.Text` na francouzský řetězec zarovná popisek s přeloženým odstavcem.

## Krok 5: Uložení dokumentu s přeloženým odstavcem

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

V tomto okamžiku dokument obsahuje francouzský odstavec, ale stále zachovává původní konfiguraci grafu.

## Krok 6: Uložení dokumentu s aktualizovaným grafem

Můžete znovu použít stejnou instanci `Document` – není potřeba ji znovu načítat – protože úpravy grafu jsou již v paměti.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Oba soubory jsou nyní připraveny k distribuci:

- **`translated.docx`** – obsahuje francouzský odstavec.
- **`chart-updated.docx`** – obsahuje francouzský odstavec *a* přizpůsobený popisek grafu.

## Kompletní, spustitelný příklad

Níže je celý program, který můžete zkopírovat a vložit do `Program.cs`. Kompiluje a spouští se tak, jak je, pokud jste nahradili `YOUR_DIRECTORY` skutečnou cestou ke složce.

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


## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Přizpůsobit popisek dat v grafu](/words/english/net/programming-with-charts/chart-data-label/)
- [Formátovat počet popisků dat v grafu](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Popisek dat v grafu](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}