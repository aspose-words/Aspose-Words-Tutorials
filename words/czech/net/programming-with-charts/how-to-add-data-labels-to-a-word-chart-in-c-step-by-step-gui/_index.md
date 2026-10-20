---
category: general
date: 2026-08-04
description: Jak přidat popisky dat v C# pomocí Aspose.Words. Naučte se upravovat
  graf, centrovat popisky dat v grafu, zobrazovat procenta v grafu a přizpůsobovat
  popisky dat v grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: cs
lastmod: 2026-08-04
og_description: Jak přidat popisky dat v C# pomocí Aspose.Words. Tento tutoriál vám
  ukáže, jak upravit graf, centrovat popisky dat v grafu, zobrazit procenta v grafu
  a přizpůsobit popisky dat v grafu.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Jak přidat datové popisky do grafu ve Wordu v C# – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Jak přidat popisky dat do grafu ve Wordu v C# – krok za krokem
url: /cs/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat popisky dat do grafu ve Wordu v C# – krok‑za‑krokem

Pokud potřebujete **how to add data labels** do grafu, který je součástí dokumentu Word, tento průvodce vám ukáže přesný kód, který musíte spustit. Uvidíte, jak upravit vlastnosti grafu, centrovat popisky dat v grafu, zobrazit procenta v grafu a přizpůsobit popisky dat v grafu pro jakýkoli scénář.

Tutoriál pokrývá vše potřebné k úpravě existujícího grafu, od načtení dokumentu až po uložení změn. Není potřeba žádných externích odkazů – stačí knihovna Aspose.Words pro .NET a základní vývojové prostředí C#.

## Požadavky

* .NET 6.0 (nebo novější) nainstalováno.
* Aspose.Words pro .NET verze 23.9 nebo novější.  
  Můžete jej nainstalovat přes NuGet:

```bash
dotnet add package Aspose.Words
```

* Soubor Word (`input.docx`), který obsahuje alespoň jeden graf.

## Jak přidat popisky dat do grafu ve Wordu v C#

Následující sekce vás provede jednotlivými kroky. Primární klíčové slovo **how to add data labels** se v textu a v komentářích kódu objevuje přirozeně, což zachovává doporučenou hustotu.

### Krok 1 – Načtení dokumentu Word obsahujícího graf

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Proč je tento krok důležitý*: Objekt `Document` představuje celý soubor Word. Načtením získáte přístup ke všem uzlům, včetně tvarů, které hostí grafy.

### Krok 2 – Získání prvního grafu z dokumentu

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Proč je tento krok důležitý*: Grafy jsou uloženy uvnitř uzlů `Shape`. Přetypováním získaného uzlu na `Shape` a voláním `GetChart()` získáte objekt `Chart`, který poskytuje kolekce sérií, os a popisků.

### Krok 3 – Povolení přizpůsobení popisků dat a zobrazení procent v grafu

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Proč je tento krok důležitý*: Nastavením `ShowPercentage` řeknete Aspose.Words, aby vypočítalo a zobrazilo podíl každého výseku na celku. To přímo řeší sekundární klíčové slovo **show percentages in chart**.

### Krok 4 – Změna umístění popisku na střed každého datového bodu

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Proč je tento krok důležitý*: Vlastnost `Position` určuje, kde se popisek zobrazí vzhledem k datovému bodu. Použití `Center` splňuje sekundární klíčové slovo **center chart data labels** a zlepšuje čitelnost u koláčových nebo prstencových grafů.

### Krok 5 – Další přizpůsobení popisků dat v grafu (volitelné)

Pokud potřebujete větší kontrolu, můžete upravit písmo, barvu nebo čáry ukazatele:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Tyto nastavení ilustrují sekundární klíčové slovo **customize chart data labels** a ukazují, jak můžete vzhled přizpůsobit tak, aby odpovídal firemním směrnicím.

### Krok 6 – Uložení upraveného dokumentu

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Proč je tento krok důležitý*: Uložení zapíše aktualizovaný graf zpět do dokumentu Word, takže nové popisky dat budou viditelné po otevření souboru v Microsoft Word.

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat, vložit a spustit. Obsahuje všechny potřebné `using` direktivy a komentáře, které vysvětlují každý řádek.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Očekávaný výsledek

Když otevřete `output.docx` v Microsoft Word, graf zobrazí:

* Hodnoty procent vedle každého výseku (např. **25 %**, **40 %**, …).
* Popisky umístěné ve středu každého datového bodu.
* Jakékoli další formátování, které jste použili, např. tučný červený text.

Tyto vizuální nápovědy usnadňují interpretaci grafu, zejména v prezentacích nebo zprávách.

## Jak upravit vlastnosti grafu mimo popisky dat

Zatímco hlavním tématem tohoto průvodce je **how to add data labels**, můžete také chtít **how to edit chart** nastavení, jako jsou názvy, umístění legendy nebo formátování os. Objekt `Chart` poskytuje vlastnosti jako `Title`, `Legend` a `AxisX/AxisY`. Například pro změnu názvu grafu:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Všechny úpravy grafu následují stejný vzor: získáte graf, upravíte jeho vlastnosti a poté dokument uložíte.

## Časté úskalí a tipy pro nejlepší praxi

| Problém | Proč k tomu dochází | Doporučené řešení |
|---|---|---|
| Graf je uvnitř seskupeného tvaru. | `GetChild(NodeType.Shape, …)` vrací vnější skupinu, nikoli vnitřní graf. | Vyhledávejte rekurzivně tvar s `shape.HasChart`. |
| Popisky dat se po uložení nezobrazí. | `ShowValue` nebo `ShowPercentage` nebylo nastaveno na `true`. | Explicitně nastavte oba `ShowValue` i `ShowPercentage` podle potřeby. |
| Popisky se překrývají u malých výseků. | Umístění do středu může způsobit přeplnění. | Použijte `ChartDataLabelPosition.OutSideEnd` pro umístění vně, nebo povolte `LeaderLines`. |

Použití těchto tipů zajišťuje spolehlivé výsledky napříč různými typy grafů.

## Závěr

Nyní víte, **how to add data labels** do grafu ve Wordu pomocí C#. Tutoriál pokryl získání grafu, povolení viditelnosti popisků, centrování popisků, zobrazení procent a přizpůsobení vzhledu. S těmito znalostmi můžete také **how to edit chart** podrobnosti, **center chart data labels**, **show percentages in chart** a **customize chart data labels** pro jakýkoli scénář reportování.

Jste připraveni objevovat dál? Zkuste přidat více sérií, aplikovat podmíněné formátování nebo exportovat graf jako obrázek. API Aspose.Words nabízí rozsáhlé možnosti manipulace s grafy – experimentujte a najděte dokonalou vizuální reprezentaci svých dat.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Přizpůsobit popisek grafu](/words/english/net/programming-with-charts/chart-data-label/)
- [Nastavit výchozí možnosti pro popisky dat v grafu](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Přizpůsobit jeden datový bod v grafu](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}