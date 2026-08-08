---
category: general
date: 2026-08-07
description: Rychle vytvořte koláčový graf ve Wordu pomocí C#. Naučte se, jak vložit
  koláčový graf, přidat datové popisky, zobrazit procenta a přizpůsobit popisky grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: cs
lastmod: 2026-08-07
og_description: Vytvořte koláčový graf ve Wordu v C# pomocí Aspose.Words. Tento tutoriál
  ukazuje, jak vložit koláčový graf, přidat datové popisky k výsečím a zobrazit procentuální
  hodnoty grafu při úpravě datových popisků grafu.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Vytvořte koláčový graf v C# – kompletní tutoriál
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Vytvořte koláčový graf ve Wordu v C# – krok za krokem
url: /cs/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření koláčového grafu ve Wordu v C# – krok za krokem

Pokud potřebujete **create pie chart word** dokumenty v C#, tento průvodce poskytuje kompletní, připravené řešení. Uvidíte, jak **insert pie chart**, **add data labels pie** a **show percentage chart**, zatímco **customize chart data labels** pro profesionální vzhled.

Generování grafů programově vás ušetří ruční úpravy, zejména když je třeba automaticky vytvářet zprávy nebo dashboardy. V následujících sekcích se naučíte vše potřebné k vložení plně označeného koláčového grafu do souboru Word pomocí Aspose.Words pro .NET.

## Požadavky a nastavení

* .NET 6.0 SDK nebo novější nainstalováno.  
* Platná licence Aspose.Words pro .NET (nebo dočasný evaluační klíč).  
* Visual Studio 2022 (nebo jakékoli IDE podporující C#).  

Přidejte balíček Aspose.Words NuGet do svého projektu:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Pokud plánujete generovat mnoho grafů, povolte režim **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) pro lepší výkon.

## Vytvoření koláčového grafu ve Wordu pomocí Aspose.Words

Prvním hlavním krokem je vytvořit prázdný dokument Word a `DocumentBuilder`. Tento objekt řídí všechny následné vkládání.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité*: `Document` představuje celý soubor `.docx`, zatímco `DocumentBuilder` poskytuje plynulé API pro přidávání odstavců, tabulek a grafů. Začátek s čistým dokumentem zajišťuje, že žádné skryté formátování neovlivní rozložení grafu.

## Vložení koláčového grafu do dokumentu

Nyní umístíme koláčový graf požadované velikosti. Metoda `InsertChart` vrací objekt `Chart`, který můžeme dále konfigurovat.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Proč je to důležité*: Příznak `ChartType.Pie` říká Aspose.Words, aby vygeneroval kruhový graf. Šířka (`400`) a výška (`300`) jsou vyjádřeny v bodech, což vám dává přesnou kontrolu nad vizuální stopou.

## Naplnění grafu daty

Koláčový graf potřebuje alespoň jednu sérii číselných hodnot. Zde přidáváme tři kategorie: „Apples“, „Bananas“ a „Cherries“.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Proč je to důležité*: Každé volání `AddCategory` vytvoří výseč. Číselná hodnota určuje velikost výseče, zatímco popisek se stane názvem kategorie zobrazeným, když jsou zapnuté popisky dat.

## Přidání popisků dat do koláče a zobrazení procentuálního grafu

Aby byl graf informativní, povolíme popisky dat, umístíme je mimo výseče a požádáme Aspose.Words, aby zobrazoval jak název kategorie, tak procento.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Proč je to důležité*: Nastavení `Position` na `OutsideEnd` zlepšuje čitelnost, zejména když jsou výseče malé. Povolení `ShowCategoryName` a `ShowPercentage` splňuje požadavek **show percentage chart** a naplňuje cíl **add data labels pie**.

## Další úpravy popisků grafu (volitelné)

Možná budete chtít změnit písmo, přidat vodící čáru nebo skrýt legendu. Následující úryvek ukazuje běžné úpravy:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Proč je to důležité*: Úprava vzhledu popisků zajišťuje, že graf odpovídá stylovému průvodci vašeho dokumentu. Odebrání legendy snižuje vizuální nepořádek, když popisky dat již předávají stejné informace.

## Uložení dokumentu s upraveným grafem

Nakonec zapíšete dokument na disk. Vyberte cestu, ke které máte právo zápisu.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Když otevřete `ChartWithCustomLabels.docx` v Microsoft Word, uvidíte koláčový graf, kde je každá výseč označena názvem kategorie a procentem, umístěna mimo výseč a stylizována pomocí vlastních nastavení písma.

### Očekávaný výstup

| Výseč   | Hodnota | Procento | Popisek ve Wordu |
|---------|---------|----------|------------------|
| Apples  | 40      | 40 %     | Apples – 40 %    |
| Bananas | 35      | 35 %     | Bananas – 35 %  |
| Cherries| 25      | 25 %     | Cherries – 25 % |

Graf by měl vypadat podobně jako ilustrace níže:

![Word dokument zobrazující koláčový graf s procentními popisky mimo každou výseč](pie-chart-word.png "Příklad vytvoření koláčového grafu ve Wordu")

*Alt text obrázku obsahuje primární klíčové slovo pro SEO.*

## Zpracování více sérií a okrajových případů

Základní příklad používá jednu sérii, což je typické pro koláčový graf. Pokud potřebujete zobrazit více sérií (např. porovnání dvou let), musíte:

1. Volat `chart.Series.Add()` pro každou další sérii.  
2. Zajistit, aby každá série používala stejné kategorie; jinak Aspose.Words vyhodí `ArgumentException`.  
3. Volitelně nastavit `labels.ShowSeriesName = true` pro rozlišení výsečí.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Když existuje více sérií, graf se automaticky vykreslí jako **clustered pie** (také nazývaný „pie of pies“). Zkontrolujte výstup, aby popisky zůstaly čitelné.

## Časté úskalí a jak se jim vyhnout

| Problém | Příčina | Řešení |
|---------|---------|--------|
| Popisky překrývají výseče | Malá oblast grafu nebo mnoho kategorií | Zvětšit rozměry grafu (`InsertChart(width, height)`) nebo změnit `Position` na `InsideEnd`. |
| Procenta nesčítají na 100 % | Zaokrouhlovací chyby v datech | Použít `labels.ShowPercentage = true` (Aspose.Words automaticky normalizuje). |
| Graf se v Wordu zobrazuje prázdný | Chybějící licence nebo vypršení evaluačního období | Zajistit, aby byla načtena platná licence Aspose.Words před vytvořením dokumentu. |
| Barvy písma se liší od motivu Wordu | V kódu nastavené vlastní písmo | Odstranit vlastní nastavení písma nebo použít barvy motivu Wordu (`System.Drawing.Color.Black`). |

## Kompletní zdrojový kód (spustitelný)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Spuštěním programu se vytvoří `ChartWithCustomLabels.docx`, který obsahuje příklad **create pie chart word**, který splňuje všechny požadavky uvedené v tutoriálu.

## Závěr

Nyní víte, jak **create pie chart word** dokumenty v C# pomocí Aspose.Words. Průvodce pokryl vkládání koláčového grafu, **add data labels pie**, **show percentage chart** a **customize chart data labels**, abyste dosáhli profesionálního, datově řízeného souboru Word.  

Odtud můžete prozkoumat související témata, jako je **insert pie chart** do existujících odstavců, generování **bar** nebo **line** grafů, nebo automatizovat hromadné vytváření zpráv s různými datovými sadami. Experimentujte s různými pozicemi popisků, styly písma a konfiguracemi více sérií, abyste výstup přizpůsobili svým specifickým potřebám reportování.

Šťastné vytváření grafů!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok za krokem vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Přizpůsobení popisku grafu](/words/english/net/programming-with-charts/chart-data-label/)
- [Nastavení výchozích možností pro popisky dat v grafu](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Vložení sloupcového grafu do dokumentu Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}