---
category: general
date: 2026-09-21
description: Vytvořte prázdný dokument Word a naučte se, jak vložit radarový graf
  do souboru Word pomocí DocumentBuilder – krok za krokem průvodce.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: cs
lastmod: 2026-09-21
og_description: Vytvořte prázdný dokument Word a vložte radarový graf do souboru Word
  pomocí Aspose.Words. Postupujte podle tohoto tutoriálu a rychle vygenerujte graf
  v dokumentu Word.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Vytvořte prázdný dokument Word a přidejte radarový graf – kompletní průvodce
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Jak vytvořit prázdný dokument Word a přidat radarový graf v C#
url: /cs/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument Word a přidat radarový graf v C#

Pokud potřebujete **vytvořit prázdný dokument Word** a vložit radarový (radiální) graf, tento tutoriál poskytuje připravené řešení připravené k spuštění. Uvidíte, jak použít Aspose.Words .NET k vygenerování souboru, vložení grafu a uložení výsledku — během několika stručných kroků.

Prázdný dokument poskytuje čisté plátno pro jakýkoli scénář automatizovaného reportování a přidání radarového grafu vám umožní vizualizovat vícerozměrná data přímo ve Wordu. Na konci tohoto průvodce budete schopni vygenerovat graf v dokumentu Word bez ruční úpravy.

## Co se naučíte

* Jak **vytvořit prázdný dokument Word** programově v C#.
* Přesný kód, jak **vložit radarový graf** pomocí `DocumentBuilder`.
* Způsoby, jak **vložit graf do souboru Word** a přizpůsobit jeho velikost.
* Jak **vygenerovat graf v dokumentu Word** a ověřit výstup.
* Tipy pro **přidání radiálního grafu do Wordu** souborů, včetně běžných úskalí.

### Požadavky

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+).
* Aspose.Words pro .NET (NuGet balíček `Aspose.Words` verze 23.9 nebo novější).
* Základní znalost C# a Visual Studio nebo vašeho preferovaného IDE.

## Vytvoření prázdného dokumentu Word pomocí C#

Prvním krokem je vytvořit instanci prázdného objektu `Document`. Tento objekt představuje zcela prázdný soubor `.docx`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` vytvoří strukturu souboru, ale zatím neobsahuje žádné sekce ani stránky. Aspose.Words automaticky přidá výchozí sekci, když začnete přidávat obsah, což je důvod, proč další krok funguje bez další konfigurace.

## Jak vložit radarový graf do souboru Word

Radarový graf (také nazývaný radiální graf) vizualizuje datové body na osách, které vycházejí z centrálního bodu. Aspose.Words poskytuje `DocumentBuilder.insertChart` pro tento účel.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` vrací objekt `Chart`, který můžete dále konfigurovat. Graf se zobrazí na první stránce prázdného dokumentu, protože builder je ve výchozím nastavení umístěn na začátek dokumentu.

## Vložení grafu do souboru Word – přidání datových sérií

Graf bez dat je neviditelný. Naplňte radarový graf jednou nebo více sériemi, aby byl smysluplný.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Můžete přidat libovolný počet sérií. Každá série může mít odlišný název, který se zobrazí v legendě grafu. Datové body odpovídají radiálním osám; pořadí, ve kterém je přidáte, určuje jejich umístění kolem kruhu.

## Vygenerování grafu v dokumentu Word – uložení souboru

Po vytvoření grafu uložte dokument na disk. Vyberte umístění, ke kterému máte právo zápisu.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Když otevřete výsledný soubor `.docx` v Microsoft Word, uvidíte prázdnou stránku s radarovým grafem o velikosti 400 × 300 bodů, naplněným ukázkovými daty.

### Očekávaný výstup

* Soubor `RadialChartExample.docx` na ploše.
* První stránka obsahuje radarový graf s pěti datovými body označenými „Series 1“.
* Žádný další text se neobjeví, protože dokument byl zahájen prázdný.

## Přidání radiálního grafu do Wordu – řešení běžných okrajových případů

### 1. Změna velikosti grafu po vložení

Pokud počáteční rozměry nevyhovují vašemu rozvržení, změňte velikost grafu takto:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Vložení grafu na konkrétní místo

Můžete přesunout kurzor builderu na záložku, buňku tabulky nebo odstavec před voláním `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Přizpůsobení vzhledu grafu

Aspose.Words zpřístupňuje celý model objektu grafu, což vám umožní nastavit tituly, popisky os a barvy.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Řešení chybějících fontů

Pokud cílové prostředí postrádá font použitý v grafu, Aspose.Words nahradí výchozím fontem. Pro zajištění konzistence vložte požadované fonty:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Export do jiných formátů

Stejný dokument lze uložit jako PDF, HTML nebo PNG bez dalších změn kódu:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Kompletní, spustitelný příklad

Sestavením všech částí dohromady získáte jeden program, který můžete zkopírovat, vložit a spustit.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Spusťte tento program, otevřete vygenerovaný soubor a uvidíte profesionální radarový graf připravený k distribuci.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **vložit radarový graf** a **vygenerovat graf v dokumentu Word** pomocí Aspose.Words. Dodržením výše uvedených kroků můžete také **přidat radiální graf do Wordu** do jakéhokoli automatizovaného reportovacího kanálu, přizpůsobit velikost, styl a exportovat do dalších formátů.

**Další kroky**

* Prozkoumejte další typy grafů (`ChartType.Column`, `ChartType.Pie`) a rozšiřte svůj nástrojový set pro reportování.
* Kombinujte více grafů na jedné stránce opakovaným voláním `InsertChart`.
* Integrujte data z databáze nebo CSV souboru pro dynamické naplnění sérií.
* Projděte dokumentaci Aspose.Words pro pokročilé možnosti formátování, jako jsou podmíněné popisky dat a šablony grafů.

Neváhejte experimentovat s kódem, upravit rozměry nebo nahradit ukázková data skutečnými obchodními metrikami. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vložení sloupcového grafu do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Vytvoření rozptylového grafu ve Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Vložení bublinového grafu do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}