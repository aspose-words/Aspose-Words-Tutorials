---
category: general
date: 2026-09-21
description: Jak formátovat řadu v čárovém grafu ve Wordu pomocí C#. Naučte se vytvořit
  dokument ve Wordu, vložit čárový graf a použít vlastní číselný formát.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: cs
lastmod: 2026-09-21
og_description: Jak formátovat řadu v čárovém grafu ve Wordu pomocí C#. Tento tutoriál
  vám ukáže, jak vytvořit dokument Word, vložit čárový graf a použít vlastní číselný
  formát.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Jak formátovat řady v čárovém grafu ve Wordu pomocí C# – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Jak formátovat řady v čárovém grafu ve Wordu pomocí C#
url: /cs/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak formátovat řady v čárovém grafu Wordu pomocí C#

Pokud potřebujete **formátovat řady** v čárovém grafu Wordu, tento návod vám poskytne kompletní, připravené řešení. Uvidíte, jak **vytvořit dokument Word**, **vložit čárový graf** a **použít vlastní číselný formát** na hodnoty osy Y – vše pomocí Aspose.Words pro .NET.

Automatizace Wordu se stane jednoduchou, jakmile pochopíte model objektů grafu. Na konci tohoto tutoriálu budete mít soubor Word, který obsahuje čárový graf, jehož datové řady jsou zobrazeny jako procenta se dvěma desetinnými místy.

## Co dosáhnete

* Programově vygenerujete prázdný soubor `.docx`.  
* Přidáte čárový graf o rozměrech 400 × 300 bodů.  
* Získáte první datovou řadu grafu.  
* Použijete formátovací kód `#,##0.00%`, aby se hodnoty osy Y zobrazovaly jako procenta.  

K žádným externím nástrojům nepotřebujete nic kromě balíčku Aspose.Words NuGet.

## Předpoklady

* .NET 6.0 SDK nebo novější.  
* Visual Studio 2022 (nebo jakékoli C# IDE).  
* Aspose.Words pro .NET 23.10 nebo novější – instalujte pomocí `dotnet add package Aspose.Words`.  

Kód funguje na Windows, Linuxu i macOS, protože Aspose.Words je platformně nezávislý.

## Vytvoření dokumentu Word s Aspose.Words

Prvním krokem je vytvořit objekt `Document`. Tento objekt představuje celý soubor Word v paměti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Proč je to důležité*: `Document` je vstupní bod pro všechny operace zpracování Wordu. Bez něj nemůžete přidávat odstavce, tabulky ani grafy.

## Vložení čárového grafu do dokumentu

`DocumentBuilder` zapisuje obsah do objektu `Document`. Volání `InsertChart` vytvoří tvar grafu na aktuální stránce.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Proč je to důležité*: `InsertChart` vrací objekt `Chart`, který vám dává plnou kontrolu nad řadami, osami a formátováním. Parametry velikosti jsou vyjádřeny v bodech (1 bod = 1/72 palce).

## Přístup k první datové řadě

Každý graf obsahuje jednu nebo více `ChartSeries`. První řada má index 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Proč je to důležité*: Objekt `ChartSeries` obsahuje hodnoty Y, hodnoty X a možnosti formátování pro jedinou čáru v čárovém grafu. Úprava tohoto objektu mění vizuální reprezentaci dat.

## Použití vlastního číselného formátu na řadu

Vlastnost `FormatCode` určuje, jak se číselné hodnoty zobrazují. Nastavením na `#,##0.00%` řeknete Wordu, aby hodnoty zobrazoval jako procenta se dvěma desetinnými místy.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Proč je to důležité*: Bez vlastního formátu Word zobrazuje surová desetinná čísla (např. `0.15`). Formátovací kód je převede na `15.00%`, což je často požadováno v obchodních zprávách.

## Uložení dokumentu a ověření výsledku

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Když otevřete `FormattedSeriesLineChart.docx` v Microsoft Word, uvidíte čárový graf, kde popisky osy Y jsou `15.00%`, `30.00%`, `45.00%` a `60.00%`. Velikost grafu odpovídá rozměrům zadaným v `InsertChart`.

### Očekávaný výstup – snímek obrazovky

> *Obrázek: Stránka dokumentu Word zobrazující čárový graf s hodnotami osy Y formátovanými jako procenta.*  
> *(Alt text: Snímek obrazovky dokumentu Word zobrazující čárový graf s hodnotami osy Y formátovanými jako procenta)*

## Běžné varianty a okrajové případy

| Situace | Úprava |
|-----------|------------|
| **Více řad** | Procházejte `chart.Series` a nastavte `FormatCode` pro každou řadu. |
| **Jiný typ grafu** | Nahraďte `ChartType.Line` za `ChartType.Column`, `ChartType.Pie` atd. |
| **Regionálně specifické oddělovače** | Použijte formátovací řetězce citlivé na `CultureInfo`, např. `"# ##0,00 %"` pro francouzské lokály. |
| **Dynamický zdroj dat** | Naplňte `series.YValues` z databáze nebo CSV souboru před aplikací formátu. |

**Tip:** Vždy aplikujte formát **po** přidání hodnot Y. Změna formátu před přidáním hodnot také funguje, ale aplikace formátu později zaručuje, že bude použit na finální datovou sadu.

## Shrnutí

Nyní víte, **jak formátovat řady** v čárovém grafu Wordu pomocí C#. V tutoriálu jsme pokryli:

* Vytvoření dokumentu Word (`create word document`).  
* Vložení čárového grafu (`insert line chart`, `add chart to word`).  
* Přístup k první řadě grafu.  
* Použití vlastního číselného formátu (`apply custom number format`) pro zobrazení procent.

## Další kroky

* Experimentujte s různými hodnotami `ChartType` a zjistěte, jak se chovají jiné vizualizace.  
* Přidejte názvy, popisky os a legendy pomocí `chart.Title`, `chart.AxisX.Title` a `chart.AxisY.Title`.  
* Exportujte graf jako obrázek (`chart.Save` s `SaveFormat.Png`) pro použití ve webových zprávách.

Neváhejte tento vzor přizpůsobit pro generování dashboardů, finančních zpráv nebo jakéhokoli dokumentu, který vyžaduje programové vytváření grafů. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}