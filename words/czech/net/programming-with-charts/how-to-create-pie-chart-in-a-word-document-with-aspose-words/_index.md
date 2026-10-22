---
category: general
date: 2026-09-21
description: Naučte se, jak vytvořit koláčový graf a vložit jej do Wordu pomocí Aspose.Words,
  přidat datové popisky do koláčového grafu a zobrazit procenta v koláčovém grafu
  během několika kroků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: cs
lastmod: 2026-09-21
og_description: Vytvořte koláčový graf ve Wordu pomocí Aspose.Words, vložte graf do
  Wordu, přidejte datové popisky do koláčového grafu a zobrazte procenta v koláčovém
  grafu – vše s přehlednými ukázkami kódu.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Vytvořte koláčový graf ve Wordu s Aspose.Words – krok za krokem průvodce
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
title: Jak vytvořit koláčový graf v dokumentu Word pomocí Aspose.Words
url: /cs/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit koláčový graf v dokumentu Word pomocí Aspose.Words

Pokud potřebujete **vytvořit koláčový graf** programově, Aspose.Words to dělá jednoduchým způsobem. V tomto tutoriálu uvidíte, jak **vložit graf do Wordu**, nakonfigurovat řady, **přidat popisky dat do koláčového grafu** a nakonec **zobrazit procenta na koláčovém grafu**, aby vizualizace předávala přesné hodnoty. Na konci budete mít kompletní, spustitelný příklad, který můžete vložit do libovolného .NET projektu.

Tento průvodce pokrývá vše, co potřebujete vědět: požadované NuGet balíčky, celý C# zdrojový kód, vysvětlení, proč je každé volání API důležité, a tipy pro přizpůsobení grafu. Není potřeba žádná externí dokumentace – stačí zkopírovat, spustit a upravit.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 SDK nebo novější nainstalovaný.  
* Visual Studio 2022 (nebo jakékoli IDE podporující .NET).  
* Licenci Aspose.Words pro .NET (bezplatná zkušební verze funguje pro testování).  
* Základní znalosti C# a struktury dokumentu Word.

Pokud již vše máte, můžete přejít rovnou ke kódu.

## Krok 1: Nastavení projektu a import Aspose.Words

Vytvořte nový konzolový projekt a přidejte NuGet balíček Aspose.Words:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Balíček obsahuje jmenný prostor `Aspose.Words.Drawing.Charts`, který zahrnuje třídy `Chart` a `ChartSeries`, jež použijeme.

> **Tip:** Uložte soubor licence (`Aspose.Words.lic`) do kořenové složky projektu a načtěte jej při startu, abyste se vyhnuli vodoznakům z evaluační verze.

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

## Krok 2: Vytvoření prázdného dokumentu a DocumentBuilderu

`Document` představuje soubor Word, zatímco `DocumentBuilder` poskytuje plynulé API pro vkládání obsahu.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Proč je to důležité:** `DocumentBuilder` udržuje aktuální vkládací bod, což zajišťuje, že se graf objeví přesně tam, kde jej chcete v toku dokumentu.

## Krok 3: Vložení koláčového grafu do dokumentu Word

Nyní **vložíme graf do Wordu**. Metoda `InsertChart` přijímá typ grafu, šířku a výšku (v bodech).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

V tomto okamžiku graf obsahuje výchozí datovou řadu s placeholder hodnotami (25, 25, 25, 25). Později je můžete nahradit, pokud bude potřeba.

## Krok 4: Přístup k první řadě a přizpůsobení popisků dat

Koláčový graf obvykle má jedinou řadu. Pro **přidání popisků dat do koláčového grafu** ji získáme a povolíme zobrazení procent.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Proč nastavujeme `ShowPercentage`:** Tento příznak říká Aspose.Words, aby vypočítal podíl každého výseče a vykreslil jej jako procento. Vlastnost `Position` zajišťuje, že popisek nepřekrývá výseč, což zlepšuje čitelnost – zejména když jsou výseče malé.

## Krok 5: (Volitelné) Nahrazení placeholder dat

Pokud chcete konkrétní hodnoty, nahraďte výchozí body:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Zobrazená procenta se automaticky upraví tak, aby odrážela nové hodnoty.

## Krok 6: Uložení dokumentu

Nakonec zapíšeme dokument na disk. Přípona určuje formát; `.docx` vytvoří moderní soubor Word.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Spuštěním programu vznikne soubor **PieChart.docx** ve výstupní složce. Po otevření v Microsoft Wordu se zobrazí koláčový graf, kde je každá výseč označena svým procentem, umístěným mimo výseče.

### Očekávaný výstup

Po otevření vygenerovaného dokumentu byste měli vidět:

* Jeden koláčový graf o velikosti 400 × 300 pt.  
* Čtyři výseče (nebo tolik, kolik jste přidali bodů).  
* Popisky procent, např. „40 %“, „30 %“ atd., zobrazené mimo každou výseč.

Pokud se popisky objeví uvnitř výsečí, zkontrolujte, že `ChartDataLabelPosition.OutsideEnd` byl nastaven správně.

## Krok 7: Běžné varianty a okrajové případy

### Přidání názvu k grafu

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Změna barev výsečí

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Zpracování prázdné řady

Pokud může být váš zdroj dat prázdný, chraňte se před `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Export do PDF místo Wordu

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

Logika vykreslování grafu zůstává stejná; Aspose.Words automaticky převede rozvržení Wordu do PDF.

## Kompletní výpis zdrojového kódu

Níže je kompletní, připravený k spuštění program. Zkopírujte jej do `Program.cs` a spusťte `dotnet run`.

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

## Závěr

Nyní víte, jak **vytvořit koláčový graf** v souboru Word pomocí Aspose.Words, **vložit graf do Wordu**, **přidat popisky dat do koláčového grafu** a **zobrazit procenta na koláčovém grafu**. Příklad ukazuje celý workflow – od nastavení projektu až po finální dokument – takže jej můžete přizpůsobit pro dashboardy, reporty nebo automatické generování faktur.

Dále prozkoumejte související témata, jako je **zobrazení procent v legendě grafu**, přizpůsobení barev grafu nebo převod dokumentu Word do PDF pro distribuci. Experimentujte s různými typy grafů (Bar, Line) pomocí stejné metody `InsertChart` a rozšiřte své automatizační schopnosti.

Šťastné grafování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}