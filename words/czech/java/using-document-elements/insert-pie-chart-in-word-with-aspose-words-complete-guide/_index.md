---
category: general
date: 2026-07-26
description: Vložte koláčový graf do dokumentu Word pomocí Aspose.Words. Naučte se,
  jak přidat graf, rozdělit výseč a zobrazit procenta během několika kroků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: cs
lastmod: 2026-07-26
og_description: Vložte koláčový graf do souboru Word pomocí Aspose.Words. Postupujte
  podle tohoto návodu a rychle se naučte, jak přidat graf, oddělit výsek a zobrazit
  procenta.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Vložení koláčového grafu do Wordu – krok za krokem tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Vložení koláčového grafu do Wordu s Aspose.Words – kompletní průvodce
url: /cs/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení koláčového grafu do Wordu pomocí Aspose.Words – Kompletní průvodce

Už jste někdy potřebovali **vložit koláčový graf** do Wordového reportu, ale nebyli jste si jisti, kde začít? Nejste v tom sami. V mnoha obchodních aplikacích vizuální úder koláčového grafu učiní data okamžitě stravitelnými a Aspose.Words to umožňuje pomocí jen několika řádků kódu.

V tomto tutoriálu projdeme přesně kroky, jak **přidat graf do Wordu**, „explodovat“ výsek pro zdůraznění a zobrazit procenta na popiscích dat. Na konci budete mít připravený příklad, který můžete vložit do libovolného .NET projektu.

---

## Požadavky

- .NET 6.0 nebo novější (kód funguje jak s .NET Core, tak s .NET Framework)
- NuGet balíček Aspose.Words pro .NET nainstalován  
  ```bash
  dotnet add package Aspose.Words
  ```
- Základní znalost syntaxe C# — nic složitého není potřeba
- IDE podle vašeho výběru (Visual Studio, Rider nebo VS Code)

To je vše. Pojďme se do toho pustit.

---

## Vložení koláčového grafu do Word dokumentu

Prvním, co potřebujeme, je čerstvý objekt `Document` a `DocumentBuilder`. Builder si představte jako pero, které píše přímo na plátno Wordu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Proč je to důležité:** `Document` představuje celý soubor .docx, zatímco `DocumentBuilder` nám poskytuje pohodlné API pro vkládání prvků, jako jsou grafy, tabulky a text. To je základ pro každou operaci **jak přidat graf**.

---

## Jak přidat graf do Wordu

Nyní, když máme builder, můžeme skutečně **vložit koláčový graf**. Metoda `insertChart` přijímá typ grafu a požadované rozměry v bodech (1 bod = 1/72 palce).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Tip:** Pokud potřebujete jinou velikost, stačí upravit hodnoty šířky a výšky. Graf se automaticky přizpůsobí okrajům stránky.

---

## Jak „explodovat“ výsek pro zdůraznění

Běžná vizuální úprava je „explodovat“ výsek, aby vyčníval z kruhu. To přitahuje pozornost čtenáře k nejdůležitějšímu segmentu.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Proč explodovat výsek?** Když chcete zvýraznit konkrétní kategorii — například „tržby Q1“ ve finančním reportu — explodování výseku jej okamžitě učiní viditelným bez dalšího textu.

---

## Jak zobrazit procenta na popiscích dat

Většina koláčových grafů vypadá lépe, když každý výsek zobrazuje své procento. Aspose.Words to umožňuje zapnout jednou vlastností.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Rychlá poznámka:** Příznak `ShowPercentage` funguje pro všechny body v sérii, takže jej nemusíte nastavovat pro každý výsek zvlášť.

---

## Uložení dokumentu obsahujícího graf

Nakonec zapíšeme dokument na disk. Vyberte libovolnou složku; jen se ujistěte, že cesta existuje.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Když otevřete `PieChart.docx` v Microsoft Word, uvidíte dokonale vykreslený koláčový graf s první výsečkou explodovanou a procenty zobrazenými — přesně to, co očekáváte od vylepšeného obchodního reportu.

---

## Kompletní funkční příklad

Níže je kompletní program připravený ke zkopírování a vložení. Spusťte jej jako konzolovou aplikaci a ověřte výstupní soubor.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Očekávaný výsledek:** Otevřete vygenerovaný `PieChart.docx`. Uvidíte třívýsečný koláčový graf s názvem „Sales Q1“, kde je první výsek vytažený a každý výsek označený „30 %“, „45 %“ a „25 %“. Vizualizace odpovídá vloženým datům.

---

## Časté otázky a okrajové případy

- **Co když potřebuji více než jednu sérii?**  
  Stačí přidat další objekty `ChartSeries` do `chart.Series`. Každá série může mít vlastní datovou sadu, barvy a nastavení explodování.

- **Mohu změnit barvy grafu?**  
  Ano. Každý `ChartPoint` má vlastnost `Format.Fill.ForeColor`, kterou můžete nastavit na libovolnou `System.Drawing.Color`.

- **Co s různými typy grafů?**  
  Enum `ChartType` zahrnuje sloupcové, čárové, prstencové a mnoho dalších. Vyměňte `ChartType.Pie` za typ, který potřebujete.

- **Je graf po vložení v Wordu editovatelný?**  
  Rozhodně. Word považuje graf za nativní Office graf, takže uživatelé mohou dvojklikem otevřít vestavěný editor grafu.

---

## Závěr

Nyní přesně víte, jak **vložit koláčový graf** do Word dokumentu pomocí Aspose.Words, **jak přidat graf do Wordu**, **jak explodovat výsek** a **jak zobrazit procenta** na popiscích dat. Výše uvedený kompletní příklad je připraven k spuštění a můžete jej rozšířit o vlastní data, stylování nebo další série.

Jste připraveni na další krok? Zkuste nahradit koláč prstencovým grafem nebo automaticky vygenerovat dávku reportů s různými datovými sadami. Pokud vás zajímají další vizualizace, podívejte se na naše návody o **jak přidat graf** pro sloupcové a čárové grafy, nebo prozkoumejte referenci API **add chart to word** pro podrobnější úpravy.

Šťastné programování a ať jsou vaše dokumenty vždy tak přehledné jako dokonale nakrájený koláč!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vložení sloupcového grafu do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Vložení plošného grafu do Word dokumentu | Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Vytvoření rozptylového grafu ve Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}