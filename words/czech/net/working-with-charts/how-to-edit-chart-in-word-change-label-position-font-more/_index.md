---
category: general
date: 2026-07-29
description: Jak upravit graf v dokumentu Word – naučte se změnit umístění popisků
  grafu, upravit popisky sloupcového grafu, modifikovat datové popisky grafu a změnit
  písmo popisků grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: cs
lastmod: 2026-07-29
og_description: Jak rychle upravit graf ve Wordu. Zvládněte změnu umístění popisků
  grafu, úpravu popisků sloupcových grafů, úpravu datových popisků grafu a změnu písma
  popisků grafu.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Jak upravit graf ve Wordu – změnit popisky a písmo
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Jak upravit graf ve Wordu: změna pozice popisku, písma a další'
url: /cs/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak upravit graf ve Wordu: změna pozice popisku, písma a další

Úprava grafu ve Wordu je běžná potřeba, když chcete, aby vaše zprávy vypadaly profesionálně. Už jste někdy bojovali s **change chart label position** nebo s tím, aby byly popisky čitelné, aniž byste prohledávali nekonečné nabídky? Nejste v tom sami – většina vývojářů narazí na tento problém při automatizaci generování zpráv. V tomto průvodci projdeme kompletním, spustitelným příkladem, který vám přesně ukáže, jak **adjust bar chart labels**, **modify chart data labels** a **change chart label font** pomocí C# a knihovny Aspose.Words.

## Co se naučíte

- Načíst soubor .docx, který již obsahuje sloupcový graf.  
- Získat první tvar grafu a přistoupit k jeho kolekci popisků dat.  
- **Change chart label position** pro čistší vzhled sloupců.  
- **Adjust bar chart labels** velikost písma pro lepší čitelnost.  
- Uložit upravený dokument zpět na disk.  

Žádné externí nástroje, žádné ruční kroky v UI – jen čistý kód, který můžete vložit do libovolného .NET projektu. Na konci budete mít samostatné řešení, které můžete znovu použít v desítkách dokumentů.

> **Prerequisites**  
> - .NET 6.0 nebo novější (kód také funguje na .NET Framework 4.7+).  
> - Aspose.Words pro .NET (k dispozici přes NuGet).  
> - Word soubor (`BarChart.docx`), který již obsahuje sloupcový graf.  

Pokud vám něco chybí, stáhněte si nejnovější balíček Aspose.Words nyní:

```bash
dotnet add package Aspose.Words
```

---

## Jak upravit graf: načtení grafu z Word dokumentu

Prvním krokem v **how to edit chart** objektech je načíst dokument a najít tvar grafu. Aspose.Words zachází s grafy jako s uzly `Shape`, takže můžeme použít `GetChild` s `NodeType.Shape` k získání prvního grafu, na který narazíme.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> Přímým přístupem k objektu `Chart` se vyhnete zátěži spojené s otevíráním souboru ve Wordu a ruční úpravou každého popisku. To je základ každé automatizace **modify chart data labels**.

## Úprava popisků sloupcového grafu: změna pozice popisku grafu

Nyní, když máme instanci `Chart`, projděme její `DataLabelCollection`. Cílem je **change chart label position**, aby každý popisek byl pěkně umístěn uvnitř základny svého sloupce, místo aby visel nepohodlně nad ním.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Pro tip:**  
> `InsideBase` funguje dobře pro svislé sloupcové grafy. Pokud pracujete s vodorovným sloupcovým grafem, zkuste místo toho `InsideEnd`. Experimentování s pozicemi je levné – stačí znovu spustit kód a otevřít uložený dokument.

## Změna písma popisku grafu: úprava velikosti písma pro čitelnost

Malé písmo je tichým zabijákem srozumitelnosti zprávy. Pro **change chart label font** stačí nastavit vlastnost `Font.Size` u každého `ChartDataLabel`. Zvýšíme ji na 9 pt, což je ideální hodnota pro většinu tištěných zpráv.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Why we do this:**  
> Úprava velikosti písma je součástí nejlepších postupů **modify chart data labels**. Větší písmo zlepšuje přístupnost a snižuje potřebu ručního následného zpracování.

## Uložení aktualizovaného dokumentu

Po úpravě pozic a písem je posledním krokem v **how to edit chart** uložení změn. Aspose.Words to umožňuje jedním řádkem.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Otevřete `BarChartCustomLabels.docx` ve Wordu a uvidíte popisky těsně uvnitř sloupců, vykreslené jasným 9 pt písmem. Už nebudete mžít oči namáhat nad malými čísly.

---

## Kompletní funkční příklad (všechny kroky v jednom souboru)

Níže je kompletní, připravený ke spuštění konzolový program, který demonstruje celý proces – od načtení dokumentu po uložení aktualizované verze. Zkopírujte jej do nového .NET konzolového projektu a stiskněte **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Očekávaný výstup** při spuštění programu:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Otevřete výsledný soubor a uvidíte **adjust bar chart labels** umístěné uvnitř sloupců s pohodlnou velikostí písma.

---

## Časté otázky a okrajové případy

### Co když dokument obsahuje více grafů?

Kód výše získává *první* graf (`GetChild(NodeType.Shape, 0, true)`). Pro úpravu všech grafů nahraďte jednorázové získání smyčkou:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Jak **change chart label font** pouze pro konkrétní sérii?

Každý `ChartSeries` má svou vlastní `DataLabelCollection`. Cílovou sérii vyberte podle indexu:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Funguje to i s koláčovými nebo čárovými grafy?

Ano – `ChartDataLabelPosition` podporuje hodnoty jako `InsideEnd`, `OutsideEnd` a `BestFit`. Pro koláčový graf můžete upřednostnit `OutsideEnd`, aby byly popisky čitelné.

### Co lokalizace (např. různé desetinné oddělovače)?

Aspose.Words respektuje nastavení locale dokumentu. Pokud potřebujete vynutit konkrétní formát, upravte `label.NumberFormat` před uložením.

## Shrnutí a další kroky

Probrali jsme **how to edit chart** objekty v Word dokumentu od začátku do konce: načtení souboru, získání grafu, **changing chart label position**, **adjusting bar chart labels**, **modifying chart data labels** a nakonec **changing chart label font** před uložením. Kompletní příklad je připravený do produkce a lze jej vložit do jakéhokoli automatizačního pipeline.

Připraveni posunout se dál? Zvažte následující nápady:

- **Add data label colors** (`dataLabel.Font.Color = Color.Blue;`).  
- **Show values as percentages** (`dataLabel.NumberFormat = "0%";`).  
- **Create charts programmatically** místo načítání existujících.  

Všechny tyto nápady staví na stejném API, které jsme dnes použili, takže se budete cítit jako doma.

Pokud narazíte na nějaké potíže, zanechte komentář níže nebo si prohlédněte dokumentaci Aspose.Words pro podrobnější možnosti úpravy grafů. Šťastné programování a užívejte si ty krásně označené grafy!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Přizpůsobit popisek grafu](/words/english/net/programming-with-charts/chart-data-label/)
- [Formátovat číslo datového popisku v grafu](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Popisek dat v grafu](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}