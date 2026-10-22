---
category: general
date: 2026-10-07
description: Naučte se, jak vytvořit dokument Word a vložit koláčový graf pomocí Aspose.Words
  v C#. Průvodce také ukazuje, jak vygenerovat soubor Word s vlastními popisky grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: cs
lastmod: 2026-10-07
og_description: Vytvořte dokument Word a vložte koláčový graf v C#. Postupujte podle
  tohoto krok‑za‑krokem průvodce a vytvořte soubor Word s plně přizpůsobenými popisky
  grafu.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Vytvořte dokument Word s přizpůsobeným koláčovým grafem v C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Jak vytvořit dokument Word s přizpůsobeným koláčovým grafem v C#
url: /cs/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit Word dokument s přizpůsobeným koláčovým grafem v C#

Pokud potřebujete **vytvořit Word dokument** programově, tento tutoriál vám ukáže, jak **vložit koláčový graf** a přizpůsobit jeho popisky dat pomocí Aspose.Words pro .NET. Také se naučíte, jak **vygenerovat Word soubor**, který obsahuje plně stylizovaný graf, a to od nastavení projektu až po uložení finálního dokumentu.

Průvodce vás provede každým krokem potřebným k přidání grafu, úpravě pozic popisků, povolení vodicích čar a nakonec uložení výsledku jako souboru `.docx`. Kromě knihovny Aspose.Words nejsou potřeba žádné externí nástroje a kompletní zdrojový kód je poskytován, abyste jej mohli okamžitě zkopírovat, vložit a spustit.

## Požadavky

* .NET 6.0 SDK nebo novější nainstalovaný  
* Platná licence Aspose.Words pro .NET (nebo bezplatný evaluační klíč)  
* IDE, například Visual Studio 2022 nebo Visual Studio Code  

Také budete muset do svého projektu přidat následující NuGet balíčky:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Tyto balíčky poskytují třídy `Document`, `DocumentBuilder` a související s grafy, které jsou použity v níže uvedených příkladech.

## Vytvoření Word dokumentu a přidání grafu

Prvním krokem je **vytvořit Word dokument** a získat `DocumentBuilder`, který vám umožní vkládat obsah. Builder funguje jako kurzor umístěný uvnitř dokumentu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` objekt představuje celý Word soubor, zatímco `DocumentBuilder` poskytuje metody jako `InsertChart`, které umisťují objekty přímo do toku dokumentu.

## Vložení koláčového grafu do dokumentu

Jakmile je builder připraven, můžete **vložit koláčový graf** s konkrétní velikostí. Graf je přidán na aktuální pozici builderu.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` vrací objekt `Chart`, který můžete dále upravovat. Ukázková data vytvářejí čtyři výseče představující čtvrtletní prodeje.

## Přizpůsobení popisků dat koláčového grafu

Aby byl graf čitelnější, často potřebujete **přizpůsobit koláčový graf** popisky – umístit je mimo výseče a zobrazit vodicí čáry. Zde přichází na řadu `ChartDataLabelCollection`.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Nastavení `Position` na `OutsideEnd` posune každou popisku za okraj výseče, zatímco `ShowLeaderLines` vykreslí čáru spojující popisku s její výsečí. Volitelné příznaky `ShowValue` a `ShowPercentage` poskytují čtenářům jak surová čísla, tak relativní procenta.

**Tip:** Pokud potřebujete formátovat písmo popisky, použijte `dataLabels.Font` k nastavení velikosti, barvy a stylu. To zajistí, že graf bude odpovídat vaší firemní identitě.

## Uložení a generování Word souboru

Po úplném nastavení grafu můžete **vygenerovat Word soubor** uložením instance `Document` na disk. Zvolte formát `.docx` pro maximální kompatibilitu s moderními verzemi Wordu.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Když otevřete `CustomPieChart.docx`, uvidíte koláčový graf se čtyřmi výsečemi, každou popsanou mimo výseč, propojenou vodicími čarami a zobrazující jak hodnotu, tak procento.

![Snímek obrazovky Word dokumentu, který obsahuje přizpůsobený koláčový graf vytvořený v C#](image-placeholder.png)

*Obrázek ukazuje konečný výsledek **vytvoření Word dokumentu** tutoriálu.*

## Běžné varianty a okrajové případy

| Scenario | How to adapt the code |
|----------|----------------------|
| **Multiple series** | Přidejte další objekty `ChartSeries` do `pieChart.Series`. Každá série může mít vlastní kolekci `DataLabels` pro nezávislé stylování. |
| **Different chart size** | Změňte parametry šířky a výšky v `InsertChart(width, height)`. Hodnoty jsou v bodech (1 pt ≈ 1/72 in). |
| **Chart title** | Použijte `pieChart.Title.Text = "Quarterly Sales"` pro přidání popisného názvu. |
| **Export to PDF** | Zavolejte `document.Save("Report.pdf", SaveFormat.Pdf);` po vytvoření grafu. |
| **License handling** | Umístěte soubor licence (`Aspose.Words.lic`) do složky aplikace a načtěte jej pomocí `new License().SetLicense("Aspose.Words.lic");` před vytvořením dokumentu. |

Tyto varianty vám umožní odpovědět na otázku **jak přidat koláčový graf** v mnoha reálných scénářích, od jednoduchých reportů po složité dashboardy.

## Závěr

Nyní víte, jak **vytvořit Word dokument**, **vložit koláčový graf** a **přizpůsobit popisky koláčového grafu** pomocí Aspose.Words pro .NET. Kompletní příklad ukazuje čistý pracovní postup: inicializovat dokument, přidat graf, upravit umístění popisků dat, povolit vodicí čáry a nakonec **vygenerovat Word soubor**, který můžete sdílet s kýmkoli.

Zkuste rozšířit tento tutoriál experimentováním s různými typy grafů (`ChartType.Column`, `ChartType.Line`) nebo použitím vlastních barevných palet, aby odpovídaly vaší značce. Pokud narazíte na problémy, konzultujte dokumentaci Aspose.Words nebo prozkoumejte související témata, jako je „jak přidat koláčový graf“ s více sériemi a dynamickými zdroji dat.

Šťastné programování a neváhejte sdílet své výsledky nebo klást doplňující otázky v komentářích!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vložit sloupcový graf do Word dokumentu](/words/english/net/programming-with-charts/insert-column-chart/)
- [Vložit plošný graf do Word dokumentu](/words/english/net/programming-with-charts/insert-area-chart/)
- [Vložit rozptylový graf do Word dokumentu](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}