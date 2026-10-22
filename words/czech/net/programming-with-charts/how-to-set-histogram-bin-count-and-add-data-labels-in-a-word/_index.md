---
category: general
date: 2026-10-13
description: Nastavte počet košů histogramu v grafu Wordu pomocí C# a přidejte popisky
  dat pro zlepšení čitelnosti. Naučte se, jak načíst dokument Word v C# a aktualizovat
  graf.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set histogram bin count
- add data labels histogram
- how to update word chart
- enable chart data labels
- load word document c#
language: cs
lastmod: 2026-10-13
og_description: Nastavte počet košů histogramu v grafu Wordu pomocí C# a povolte popisky
  dat pro přehlednější vizuální údaje. Postupujte podle tohoto kompletního tutoriálu,
  jak načíst dokument Word v C# a aktualizovat graf.
og_image_alt: Screenshot of a Word histogram chart after setting bin count and enabling
  data labels
og_title: Nastavte počet intervalů histogramu v grafu Wordu pomocí C# – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Set histogram bin count in a Word chart with C# and add data labels
    to improve readability. Learn how to load a Word document C# and update the chart.
  headline: How to set histogram bin count and add data labels in a Word chart using
    C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart manipulation
title: Jak nastavit počet košů histogramu a přidat popisky dat v grafu Wordu pomocí
  C#
url: /cs/net/programming-with-charts/how-to-set-histogram-bin-count-and-add-data-labels-in-a-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit počet binů histogramu a přidat popisky dat v grafu Word pomocí C#

Pokud potřebujete **nastavit počet binů histogramu** v grafu Word, tento průvodce vám ukáže, jak to provést pomocí C#. Také se naučíte, jak **přidat popisky dat do histogramu**, aby každý bin zobrazoval svou hodnotu, což usnadní čtení grafu. Řešení funguje s libovolným souborem `.docx`, který obsahuje histogramový graf, a používá knihovnu Aspose.Words pro .NET.

Aktualizace grafu je běžný úkol při automatickém generování zpráv. Na konci tohoto tutoriálu budete schopni **načíst Word dokument C#**, upravit počet binů histogramu, zapnout popisky dat a výsledek uložit bez ruční úpravy.

## Co se naučíte

* Jak načíst Word dokument v C# (`load word document c#`).
* Jak najít první histogramový graf v dokumentu (`how to update word chart`).
* Přesné kroky k **nastavení počtu binů histogramu** a **povolení popisků dat v grafu**.
* Tipy pro práci s více grafy, různými typy grafů a běžnými úskalími.

## Požadavky

| Požadavek | Proč je to důležité |
|-------------|----------------|
| .NET 6.0 or later | Poskytuje runtime pro Aspose.Words. |
| Aspose.Words for .NET (v23.9 or newer) | Nabízí API `Chart`, které se používá k úpravě grafů ve Wordu. |
| A Word file (`input.docx`) that contains a histogram chart | Soubor Word (`input.docx`), který obsahuje histogramový graf. Kód funguje na existujícím histogramu; můžete si jej ručně vytvořit ve Wordu pro testování. |
| Visual Studio 2022 (or any C# IDE) | Umožňuje snadno zkompilovat a spustit ukázku. |

Nainstalujte NuGet balíček pomocí následujícího příkazu:

```bash
dotnet add package Aspose.Words
```

> **Tip:** Pokud plánujete zpracovávat mnoho dokumentů, aktivujte licenci Aspose.Words, abyste odstranili evaluační vodoznaky.

## Krok 1: Načtení Word dokumentu (load word document c#)

Prvním krokem je otevřít soubor `.docx`, který obsahuje histogram. Použití `Document.Load` zajistí, že všechny části dokumentu, včetně grafů, jsou dostupné v paměti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Path to the source document
string inputPath = @"C:\Docs\input.docx";

// Load the Word document
Document doc = new Document(inputPath);
```

> **Proč je tento krok důležitý:** Načtení dokumentu je základem pro jakoukoli úpravu. Pokud soubor nelze otevřít, následující kroky selžou s výjimkou `FileNotFoundException`.

## Krok 2: Vyhledání histogramového grafu (how to update word chart)

Word ukládá grafy jako uzly `Shape`. Musíme najít první tvar a přetypovat jej na `Chart`. Pokud váš dokument obsahuje více grafů, můžete iterovat přes všechny tvary a zkontrolovat `chart.ChartType`.

```csharp
// Retrieve the first shape in the document (depth‑first search)
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Ensure the shape really is a chart
if (shape?.Chart == null)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Cast the shape to a Chart object
Chart histogramChart = shape.Chart;
```

> **Hraniční případ:** Pokud dokument neobsahuje žádný graf, `GetChild` vrátí `null`. Výše uvedená kontrola zabraňuje `NullReferenceException`.

## Krok 3: Nastavení počtu binů histogramu (set histogram bin count)

Vizuální granularita histogramu je řízena vlastností `BinCount`. Nastavením vyšší hodnoty vytvoříte více sloupců, což může odhalit jemnější rozdělení dat.

```csharp
// Verify that the chart is a histogram
if (histogramChart.ChartType != ChartType.Histogram)
{
    throw new InvalidOperationException("The selected chart is not a histogram.");
}

// Set the desired number of bins (e.g., 15)
histogramChart.HistogramChart.BinCount = 15;
```

> **Proč to potřebujete:** Úprava počtu binů vám umožní přizpůsobit graf publiku. Malý počet binů zjednodušuje zobrazení, zatímco větší počet poskytuje více detailů.

## Krok 4: Povolení popisků dat v grafu (add data labels histogram / enable chart data labels)

Popisky dat zobrazují hodnotu každého binu přímo v grafu. To je zvláště užitečné, když je histogram tištěn nebo exportován do PDF.

```csharp
// Turn on data labels for each bin
histogramChart.HistogramChart.ShowLabels = true;

// Optional: customize label format (e.g., show percentage)
histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";
```

> **Praktický tip:** Pokud dáváte přednost procentům místo surových počtů, nastavte `NumberFormat = "0%"` a upravte `ShowPercentage = true`.

## Krok 5: Uložení upraveného dokumentu

Po provedení změn zapište dokument zpět na disk. Můžete přepsat původní soubor nebo vytvořit nový.

```csharp
// Path to the output document
string outputPath = @"C:\Docs\output.docx";

// Save the updated document
doc.Save(outputPath);
```

Otevření `output.docx` v Microsoft Word nyní zobrazí histogram s 15 biny a viditelnými popisky dat.

## Krok 6: Ověření výsledku (očekávaný výstup)

Aby bylo zajištěno, že operace proběhla úspěšně bez vizuální kontroly, můžete programově načíst zpět vlastnosti:

```csharp
// Reload the saved file for verification
Document verifyDoc = new Document(outputPath);
Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
```

Konzole by měla zobrazit:

```
BinCount: 15
ShowLabels: True
```

Pokud se hodnoty shodují, histogram byl správně aktualizován.

## Kompletní spustitelný příklad

Spojením všeho dohromady zde máte samostatný program, který můžete zkopírovat, vložit a spustit:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // ---------- Step 2: Locate the histogram chart ----------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape?.Chart == null)
            throw new InvalidOperationException("No chart found in the document.");

        Chart histogramChart = shape.Chart;

        // ---------- Step 3: Set histogram bin count ----------
        if (histogramChart.ChartType != ChartType.Histogram)
            throw new InvalidOperationException("The chart is not a histogram.");

        histogramChart.HistogramChart.BinCount = 15;

        // ---------- Step 4: Enable chart data labels ----------
        histogramChart.HistogramChart.ShowLabels = true;
        histogramChart.HistogramChart.Labels.NumberFormat = "#,##0";

        // ---------- Step 5: Save the modified document ----------
        string outputPath = @"C:\Docs\output.docx";
        doc.Save(outputPath);

        // ---------- Step 6: Verify the changes ----------
        Document verifyDoc = new Document(outputPath);
        Chart verifyChart = ((Shape)verifyDoc.GetChild(NodeType.Shape, 0, true)).Chart;

        Console.WriteLine($"BinCount: {verifyChart.HistogramChart.BinCount}");
        Console.WriteLine($"ShowLabels: {verifyChart.HistogramChart.ShowLabels}");
    }
}
```

Spusťte program, poté otevřete `output.docx` a uvidíte aktualizovaný histogram.

## Časté otázky a hraniční případy

| Otázka | Odpověď |
|----------|--------|
| **Co když dokument obsahuje více než jeden graf?** | Použijte `doc.GetChildNodes(NodeType.Shape, true)` k získání kolekce, poté iterujte a zkontrolujte každý `Chart.ChartType`. |
| **Mohu změnit šířku binu místo počtu?** | Ano. Použijte `histogramChart.HistogramChart.BinWidth` k určení pevné šířky; nastavení `BinCount` bude ignorováno. |
| **Je API kompatibilní s .NET Core?** | Aspose.Words pro .NET podporuje .NET Core, .NET 5+ a .NET Framework. Stejný kód funguje na všech podporovaných runtimech. |
| **Jak skrýt legendu po přidání popisků?** | Nastavte `histogramChart.Legend.Visible = false;`. To udrží graf čistý, když popisky již předávají data. |

## Závěr

Nyní víte, jak **nastavit počet binů histogramu** a **přidat popisky dat** do grafu Word pomocí C#. Načtením dokumentu, vyhledáním histogramu, úpravou `BinCount`, povolením `ShowLabels` a uložením souboru můžete automatizovat aktualizace grafů v jakémkoli reportovacím procesu.  

Odtud můžete dále zkoumat:

* **jak aktualizovat graf Word** barvy a styly,
* **povolit popisky dat v grafu** pro jiné typy grafů (koláčový, sloupcový, čárový),
* Generování grafů ze surových dat pomocí Aspose.Words nebo Aspose.Cells,
* Vložení aktualizovaného dokumentu do PDF pomocí Aspose.PDF.

Experimentujte s různými počty binů a formáty popisků, abyste našli vizuální rovnováhu, která nejlépe vyhovuje vašemu publiku. Šťastné programování!  

![Word histogram after

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Aktualizace dat řady grafu v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Nastavení jednotných popisků dat ve sloupcovém grafu pomocí Aspose.Words pro .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Nastavení výchozích možností pro popisky dat v grafu](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}