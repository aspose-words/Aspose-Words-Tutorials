---
category: general
date: 2026-09-14
description: Vložte radarový graf do Wordu pomocí C#. Naučte se nastavit název grafu,
  přidat více sérií a vytvořit graf programově během několika řádků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert radar chart
- set chart title
- create radar chart word
- multiple series radar chart
- create chart programmatically
language: cs
lastmod: 2026-09-14
og_description: Vložte radarový graf do Wordu pomocí C#. Tento tutoriál ukazuje, jak
  nastavit název grafu, přidat více sérií a vytvořit graf programově.
og_image_alt: Screenshot of a Word document displaying a radar chart with sales data
og_title: Vložení radarového grafu do Wordu pomocí C# – rychlý programovací návod
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Insert radar chart in Word with C#. Learn how to set chart title, add
    multiple series, and create the chart programmatically in just a few lines.
  headline: Insert radar chart in Word using C# – step‑by‑step guide
  type: TechArticle
tags:
- radar chart
- C#
- Aspose.Words
title: Vložení radarového grafu do Wordu pomocí C# – krok za krokem
url: /cs/net/programming-with-charts/insert-radar-chart-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení radarového grafu do Wordu pomocí C# – krok za krokem průvodce

Pokud potřebujete **vložit radarový graf** do dokumentu Word, tento návod vám ukáže, jak to provést programově v C#. Také se naučíte, jak **nastavit název grafu**, přidat **radarový graf s více sériemi** a uložit soubor, aniž byste opustili své IDE.

Návod pokrývá vše od nastavení projektu až po finální volání `doc.Save`, takže můžete celý příklad zkopírovat‑vložit a spustit ihned. Není potřeba hledat externí dokumentaci.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6 (nebo novější) nainstalovaný.
* Platnou licenci Aspose.Words pro .NET (nebo dočasný evaluační klíč).
* Visual Studio 2022 nebo jakékoli jiné C# IDE, které preferujete.

> **Tip:** Pokud používáte bezplatnou zkušební verzi, nezapomeňte nastavit licenci před první tvorbou `Document`, aby se zabránilo vodoznaku evaluace.

## Krok 1: Vložení radarového grafu do dokumentu Word

Prvním krokem je vytvořit nový `Document` a `DocumentBuilder`. Builder vám poskytuje přístup k obsahu dokumentu a umožňuje umístit **radarový graf** přesně tam, kde jej potřebujete.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank Word document.
Document doc = new Document();

// DocumentBuilder provides methods to insert content.
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a radar (radial) chart at the current cursor position.
Chart chart = builder.InsertChart(ChartType.Radar);
```

*Proč je tento krok důležitý:* `InsertChart` vytvoří objekt grafu, který můžete plně nakonfigurovat před uložením dokumentu. Použití `ChartType.Radar` říká Wordu, aby vykreslil radiální graf místo sloupcového nebo čárového.

## Krok 2: Nastavení názvu grafu a stupnice os

Graf bez názvu může být matoucí. Zde **nastavíme název grafu** na „Sales Radar“ a povolíme stupnici na obou osách (k dispozici od Aspose.Words 24.9 výše).

```csharp
// Give the chart a meaningful title.
chart.Title.Text = "Sales Radar";

// Enable graduations (grid lines) on both X and Y axes.
chart.AxisX.HasGraduations = true;
chart.AxisY.HasGraduations = true;
```

*Proč je tento krok důležitý:* Název poskytuje čtenářům kontext a stupnice zlepšují čitelnost tím, že ukazují, kde se jednotlivé datové body nacházejí na měřítku.

## Krok 3: Vytvoření více sérií pro radarový graf

**Radarový graf s více sériemi** vám umožní porovnat různé období vedle sebe. Níže přidáme dvě série — Q1 a Q2 — každou se třemi datovými body.

```csharp
// Series 1: Q1 data.
chart.Series.Add(
    "Q1",                                 // Series name
    new[] { "Jan", "Feb", "Mar" },        // Category labels
    new[] { 10, 20, 30 }                  // Values
);

// Series 2: Q2 data.
chart.Series.Add(
    "Q2",
    new[] { "Jan", "Feb", "Mar" },
    new[] { 15, 25, 35 }
);
```

*Proč je tento krok důležitý:* Přidání více sérií demonstruje, jak porovnávat datové sady na stejném radaru, což je častý požadavek pro prodeje, výkonnost nebo výsledky průzkumů.

## Krok 4: Programové uložení dokumentu Word

Nakonec **vytvoříte graf programově** a uložíte dokument na disk. Metoda `Save` zapíše soubor `.docx`, který lze otevřít v Microsoft Word.

```csharp
// Define the output path. Adjust the directory as needed.
string outputPath = Path.Combine(
    Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
    "RadialGraduations.docx"
);

// Save the document containing the radar chart.
doc.Save(outputPath);
```

Když otevřete `RadialGraduations.docx`, uvidíte radarový graf s názvem „Sales Radar“ a dvěma sériemi (Q1 a Q2) vykreslenými proti měsícům Jan‑Mar.

### Očekávaný výstup

![Radar chart in Word](https://example.com/radar-chart.png){: .align-center alt="Word dokument zobrazující radarový graf se dvěma datovými sériemi"}

Snímek obrazovky (nebo samotný soubor) potvrzuje, že graf byl vložen, pojmenován a správně naplněn.

## Kompletní, spustitelný příklad

Spojením všech částí získáte samostatný program, který můžete zkompilovat a spustit:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a radar chart.
        Chart chart = builder.InsertChart(ChartType.Radar);

        // 3. Set chart title and enable axis graduations.
        chart.Title.Text = "Sales Radar";
        chart.AxisX.HasGraduations = true;
        chart.AxisY.HasGraduations = true;

        // 4. Add two data series.
        chart.Series.Add("Q1", new[] { "Jan", "Feb", "Mar" }, new[] { 10, 20, 30 });
        chart.Series.Add("Q2", new[] { "Jan", "Feb", "Mar" }, new[] { 15, 25, 35 });

        // 5. Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialGraduations.docx"
        );
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Spusťte program, otevřete vygenerovaný soubor a ověřte, že operace **vložit radarový graf** proběhla úspěšně.

## Často kladené otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Mohu po vložení změnit typ grafu?** | Ano. Po `InsertChart` přiřaďte nový `ChartType` k `chart.Type`. Přesto je efektivnější vytvořit graf se správným typem hned od začátku. |
| **Co když potřebuji více než dvě série?** | Zavolejte `chart.Series.Add` pro každou další sérii. Graf automaticky upraví legendu a barvy. |
| **Jak přizpůsobit barvy nebo značky?** | Použijte `chart.Series[i].Format.Fill.ForeColor` pro barvy výplně a `chart.Series[i].Marker` pro styly značek. |
| **Je API kompatibilní s .NET Framework?** | Stejný kód funguje s .NET Framework 4.7+; stačí odkazovat na odpovídající Aspose.Words DLL. |
| **Co když používám starší verzi Aspose.Words?** | Stupnice (`HasGraduations`) byly zavedeny ve verzi 24.9. Ve starších verzích můžete ručně přidat mřížkové čáry pomocí `chart.AxisX.MajorGridLines` a `chart.AxisY.MajorGridLines`. |

## Závěr

Nyní víte, jak **vložit radarový graf** do dokumentu Word pomocí C#, **nastavit název grafu**, přidat **radarový graf s více sériemi** a **vytvořit graf programově**. Toto end‑to‑end řešení vám umožní automatizovat reporty, dashboardy nebo jakýkoli scénář, kde je vizuální porovnání kategorií vyžadováno.

Dále prozkoumejte související témata, jako je **přizpůsobení barev grafu**, **export grafů jako obrázků** nebo **vkládání grafů do PDF souborů**. Experimentujte s různými datovými sadami a sledujte, jak se radarová vizualizace přizpůsobuje.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vlastních projektech.

- [Vložit sloupcový graf do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Vložit bublinový graf do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-bubble-chart/)
- [Vložit plošný graf do dokumentu Word | Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}