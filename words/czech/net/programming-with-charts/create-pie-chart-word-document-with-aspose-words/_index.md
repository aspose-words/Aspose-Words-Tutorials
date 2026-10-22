---
category: general
date: 2026-08-10
description: Vytvořte dokument Word s koláčovým grafem pomocí Aspose.Words. Naučte
  se, jak vložit graf, přizpůsobit barvy koláčového grafu a změnit barvu výseče koláče
  v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: cs
lastmod: 2026-08-10
og_description: Vytvořte Word dokument s koláčovým grafem pomocí Aspose.Words. Tento
  průvodce vysvětluje, jak vložit graf, přizpůsobit barvy koláčového grafu a změnit
  barvu výseku koláče v aplikaci C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Vytvořte koláčový graf v dokumentu Word – průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Vytvořte Word dokument s koláčovým grafem pomocí Aspose.Words
url: /cs/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu s koláčovým grafem pomocí Aspose.Words

Pokud potřebujete **programově vytvořit Word dokument s koláčovým grafem**, tento tutoriál vám ukáže přesně jak na to. Provedeme vás vložením grafu, **přizpůsobením barev koláčového grafu** a **změnou barvy výseče koláče** pomocí Aspose.Words pro .NET.

Uvidíte kompletní, spustitelný příklad, který můžete zkopírovat do Visual Studia, spustit a okamžitě otevřít vygenerovaný *.docx* soubor a ověřit stylizovaný koláčový graf. Žádná externí dokumentace není potřeba — vše, co potřebujete, je v tomto průvodci.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 SDK nebo novější nainstalovaný  
* Platnou licenci Aspose.Words pro .NET (nebo dočasný evaluační klíč)  
* Visual Studio 2022 (nebo libovolné C# IDE)  

Kód používá pouze jmenné prostory `Aspose.Words` a `Aspose.Words.Drawing.Charts`, takže kromě knihovny Aspose.Words nejsou vyžadovány žádné další NuGet balíčky.

## Vytvoření Word dokumentu s koláčovým grafem — úplný příklad

Následující C# program vytvoří nový Word dokument, vloží koláčový graf, naformátuje první dvě výseče a soubor uloží. Každý krok je podrobně vysvětlen.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Vysvětlení jednotlivých kroků

| Krok | Co dělá | Proč je důležité |
|------|---------|------------------|
| **1** | Vytvoří nový `Document` a `DocumentBuilder`. | `DocumentBuilder` poskytuje řetězené metody pro vkládání obsahu, jako jsou grafy, do Word souboru. |
| **2** | Zavolá `InsertChart` s `ChartType.Pie` a pevnou velikostí. | `InsertChart` je **metoda pro vložení grafu**; určení šířky/výšky zajišťuje, že graf bude na stránce pěkně zapadat. |
| **3** | Přidá datovou sérii se třemi kategoriemi a číselnými hodnotami. | Koláčový graf bez dat je neviditelný; naplnění daty demonstruje kroky stylování. |
| **4** | Nastaví `Explosion` na první bod. | „Explodování“ výseče přitahuje pozornost k určitému segmentu — užitečné pro zvýraznění klíčových dat. |
| **5** | Nastaví `ForeColor` pro první dva body. | Toto je jádro **přizpůsobení barev koláčového grafu**; můžete použít libovolnou `System.Drawing.Color`. |
| **6** | Ukazuje, jak **změnit barvu výseče koláče** pro další výseče. | Demonstruje, že stylování není omezeno jen na první dvě výseče; každou výseč můžete obarvit individuálně. |
| **7** | Uloží dokument jako `PieChartStyled.docx`. | Výstup lze otevřít v Microsoft Word, Google Docs nebo jakémkoli kompatibilním prohlížeči. |

#### Očekávaný výstup

Otevření souboru `PieChartStyled.docx` zobrazí jedinou stránku s koláčovým grafem o rozměrech 400 × 300 pt:

* Výseč 1 (oranžová) je „explodována“ ven.  
* Výseč 2 (zelená) leží vedle explodované výseče.  
* Výseč 3 (ocelově‑modrá) vyplňuje zbývající segment.

Graf odráží datové hodnoty (30, 45, 25) a vámi definované vlastní barvy.

## Jak stylovat koláč — další tipy

* **Používejte barvy motivu** — místo pevného kódu `Color.Orange` můžete čerpat barvy z motivu dokumentu:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Přidejte popisky dat** — pokud chcete na grafu zobrazovat procenta:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Dynamicky měňte velikost** — vypočítejte velikost grafu na základě okrajů stránky:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Tyto varianty ukazují flexibilitu **stylování koláče** nad rámec základního příkladu.

## Často kladené otázky

**Q: Funguje to s .NET Core?**  
A: Ano. Aspose.Words pro .NET je kompatibilní s .NET Core, .NET 5, .NET 6 a novějšími verzemi. Stačí odkazovat na stejný NuGet balíček.

**Q: Co když potřebuji místo koláčového grafu donut graf?**  
A: Nahraďte `ChartType.Pie` za `ChartType.Doughnut`. Stejné API pro stylování (`Explosion`, `ForeColor`) platí.

**Q: Můžu graf vložit do existujícího dokumentu?**  
A: Otevřete existující soubor pomocí `new Document("Existing.docx")`, vytvořte `DocumentBuilder` pro tento dokument a zavolejte `InsertChart` na požadované pozici kurzoru.

**Q: Jak zacházet s velkými datovými sadami?**  
A: Koláčové grafy jsou vhodné pro omezený počet kategorií (typicky < 10). Pro mnoho kategorií zvažte sloupcový nebo pruhový graf.

## Kompletní zdrojový kód (rekapitulace)

Níže je celý program v jednom bloku pro snadné kopírování:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Spuštěním tohoto kódu získáte Word dokument s stylizovaným koláčovým grafem, jak bylo popsáno výše.

## Závěr

Nyní víte, jak **vytvořit Word dokument s koláčovým grafem** pomocí Aspose.Words, **přizpůsobit barvy koláčového grafu** a **změnit barvu výseče koláče** programově. Průvodce pokrýval vložení grafu, naplnění daty, explodování výseče, aplikaci vlastních barev a uložení výsledku.  

Od sem můžete zkoumat související témata, jako je **vkládání jiných typů grafů**, přidávání legend nebo generování vícestránkových reportů s více grafy. Experimentujte s různými barevnými schématy a datovými sadami, aby vyhovovaly vašim potřebám reportování.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}