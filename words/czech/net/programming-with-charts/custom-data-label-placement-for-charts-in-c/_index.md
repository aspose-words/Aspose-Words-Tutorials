---
category: general
date: 2026-08-04
description: Vlastní umístění datových popisků pro grafy v C# vám umožňuje centrovat
  popisky na výsečích grafu. Postupujte podle tohoto krok‑za‑krokem průvodce s využitím
  API grafů Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: cs
lastmod: 2026-08-04
og_description: Vlastní umístění datových popisků pro grafy v C# vám ukazuje, jak
  vycentrovat všechny popisky dat na každém výseku grafu ve Wordu. Ovládněte umístění
  datových popisků v grafu s Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Vlastní umístění datových popisků v grafech v C# – krok za krokem průvodce
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Vlastní umístění datových popisků pro grafy v C#
url: /cs/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vlastní umístění datových popisků pro grafy v C#

**Custom Data‑Label Placement for Charts** vám umožní přesně řídit, kde se každý popisek zobrazí v grafu uvnitř dokumentu Word. V tomto tutoriálu se naučíte, jak vycentrovat všechny datové popisky na každém výseku pomocí C# a Aspose.Words chart API.

Získáte kompletní, spustitelný příklad, který načte soubor `.docx`, získá první tvar grafu, změní `Position` každého popisku na `Center` a uloží aktualizovaný dokument. Nejsou potřeba žádné externí odkazy – stačí knihovna Aspose.Words pro .NET a základní vývojové prostředí C#.

**Co se naučíte**

* Jak načíst dokument Word, který obsahuje graf.  
* Jak najít tvar grafu pomocí Aspose.Words chart API.  
* Jak použít **chart data label positioning** na každou sérii v grafu.  
* Jak uložit dokument, aby se vycentrované popisky zobrazily ve Wordu.  

**Požadavky**

* .NET 6.0 (nebo novější) nainstalováno.  
* Visual Studio 2022 (nebo jakékoli C# IDE).  
* Odkaz na NuGet balíček `Aspose.Words`.  
* Soubor Word (`Chart.docx`), který obsahuje alespoň jeden graf.

---

## Vlastní umístění datových popisků pro grafy – krok 1: načtení dokumentu

Prvním krokem je otevřít soubor Word, který obsahuje graf. `Document` je vstupní bod pro jakoukoli manipulaci s Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Proč je tento krok důležitý*: Bez načtení dokumentu nemůžete získat přístup k objektu grafu. Validace zajistí, že obdržíte jasnou chybu, pokud soubor neobsahuje graf, čímž se předejde pozdější chybě null‑reference.

## Použití Aspose.Words chart API pro přístup k tvarům grafu

Aspose.Words zachází s grafem jako s objektem `Chart` vloženým uvnitř `Shape`. Získáte jej přetypováním příslušného poduzlu.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Proč je tento krok důležitý*: Přímý přístup k `Chart` vám poskytuje plnou kontrolu nad sériemi, datovými body a vlastnostmi popisků. Pokud tvar není graf, kód se brzy ukončí s informativní zprávou.

## Nastavení umístění datových popisků grafu v C#

Nyní projděte každou sérii a každý datový popisek a nastavte `Position` na `Center`. Toto je jádro **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Tip**: Pokud potřebujete jiné umístění (např. `InsideEnd` pro sloupcový graf), změňte odpovídající hodnotu výčtu. Výčet `ChartDataLabelPosition` zahrnuje všechna standardní umístění podporovaná ve Wordu.

*Proč je tento krok důležitý*: Změna `label.Position` aktualizuje podkladovou reprezentaci OOXML, takže se popisek zobrazí vycentrovaně při otevření dokumentu v Microsoft Word.

## Uložení dokumentu Word s aktualizovanými popisky

Po úpravě grafu uložte změny zpět do souboru. Můžete přepsat originál nebo vytvořit novou kopii.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Proč je tento krok důležitý*: Uložení zapíše aktualizované OOXML na disk. Otevření `ChartLabelsCentered.docx` ve Wordu zobrazí každý popisek výseku vycentrovaný, což potvrzuje úspěšnost **Custom Data‑Label Placement for Charts**.

## Okrajové případy a varianty

| Situace | Jak řešit |
|-----------|---------------|
| **Více grafů** ve stejném dokumentu | Procházejte `doc.GetChildNodes(NodeType.Shape, true)` a pro každý tvar zkontrolujte `shape.HasChart`. |
| **Různé typy grafů** (pie, doughnut, bar) | Stejný `ChartDataLabelPosition.Center` funguje pro koláčové grafy. Pro sloupcové/tyčové grafy můžete upřednostnit `InsideEnd` nebo `OutsideEnd`. |
| **Text popisku vyžaduje formátování** | Přistupujte k `label.TextProperties` a nastavte velikost písma, barvu nebo tučnost. |
| **Běh na .NET Core** | Ujistěte se, že odkazujete na verzi Aspose.Words pro .NET Standard; API je identické. |

## Kompletní funkční příklad

Níže je celý program, který můžete zkopírovat a vložit do konzolové aplikace. Obsahuje všechny potřebné `using` direktivy a ošetření chyb.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Očekávaný výsledek**: Otevřete `ChartLabelsCentered.docx` v Microsoft Word. Každá výseka grafu nyní zobrazuje svůj datový popisek přímo ve středu výseky, což poskytuje čistší vizuální vzhled.

## Závěr

Nyní máte kompletní řešení **Custom Data‑Label Placement for Charts** v C#. Načtením dokumentu, přístupem k grafu přes Aspose.Words chart API, nastavením `ChartDataLabelPosition.Center` pro každý popisek a uložením souboru můžete automatizovat umístění popisků pro jakýkoli graf ve Wordu.

Dále prozkoumejte další možnosti **chart data label positioning**, jako jsou `InsideEnd` nebo `OutsideEnd`, nebo experimentujte s **C# chart manipulation**, abyste změnili barvy, přidali legendy nebo generovali grafy od nuly. Tyto rozšíření staví přímo na technikách zde popsaných a rozšiřují vaše dovednosti v automatizaci grafů v dokumentech Word. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}