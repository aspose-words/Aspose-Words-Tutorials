---
category: general
date: 2026-09-11
description: Návod na úpravu popisků grafu ukazující, jak změnit umístění popisku
  grafu, přizpůsobit datový popisek grafu, skrýt název kategorie grafu a zobrazit
  hodnotu popisku grafu pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: cs
lastmod: 2026-09-11
og_description: Návod na úpravu popisků grafu vás provede změnou pozice popisku grafu,
  přizpůsobením datového popisku grafu, skrytím názvu kategorie grafu a zobrazením
  hodnoty popisku grafu pomocí Aspose.Words pro .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Návod na úpravu popisku grafu – přizpůsobení popisků grafu ve Wordu v C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Návod na úpravu popisků grafu – upravte popisky grafu ve Wordu v C#
url: /cs/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Návod na úpravu popisků grafu – úprava popisků grafu ve Wordu v C#

Pokud potřebujete **edit chart label tutorial** pro dokument Word, tento průvodce vám přesně ukáže, jak změnit umístění popisku grafu, přizpůsobit datový popisek grafu, skrýt název kategorie grafu a zobrazit hodnotu popisku grafu pomocí Aspose.Words pro .NET. Uvidíte kompletní, spustitelný příklad, který můžete vložit do libovolného projektu C#.

Práce s popisky grafu je běžná požadavek při programovém generování zpráv, faktur nebo řídicích panelů. Tento tutoriál pokrývá každý krok – od načtení dokumentu až po uložení změn – takže můžete vytvářet vylepšené grafy bez ruční úpravy.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 nebo novější nainstalovaný  
* Platnou licenci Aspose.Words pro .NET (nebo dočasný evaluační klíč)  
* Visual Studio 2022 nebo jakékoli IDE kompatibilní s C#  
* Soubor Word (`Chart.docx`), který obsahuje alespoň jeden graf  

Žádné další NuGet balíčky nejsou potřeba nad rámec `Aspose.Words`.

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte novou konzolovou aplikaci a přidejte NuGet balíček Aspose.Words:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Otevřete `Program.cs` a importujte požadované jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Tyto jmenné prostory vám poskytují přístup ke třídě `Document` pro práci se soubory Word a třídám `Chart` pro manipulaci s prvky grafu.

## Krok 2: Načtení dokumentu Word, který obsahuje graf

První akční řádek načte zdrojový dokument. Nahraďte `YOUR_DIRECTORY` skutečnou cestou, kde se nachází `Chart.docx`.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Načtení dokumentu vytvoří v‑paměťovou reprezentaci, kterou můžete procházet a měnit.

## Krok 3: Získání prvního grafu v dokumentu

Grafy jsou uloženy jako podřízené uzly typu `NodeType.Chart`. Metoda `GetChild` prohledá strom dokumentu a vrátí graf, který chcete upravit.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Pokud dokument obsahuje více grafů, můžete změnit index a cílit na jiný.

## Krok 4: Přístup a úprava datového popisku první řady

Každá řada grafu má objekt `DataLabel`, který řídí, jak se popisek zobrazuje. Níže uvedený kód demonstruje čtyři klíčové úpravy požadované v sekundárních klíčových slovech tutoriálu.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Proč jsou tato nastavení důležitá**

* `DataLabelPosition.Center` přesune popisek z výchozího umístění mimo bod do středu datového bodu, což usnadňuje čtení grafu, když jsou body těsně u sebe.  
* Nastavení vlastního `Separator` vám umožní řídit, jak jsou spojeny název řady, hodnota a další části.  
* Skrytí názvu kategorie (`ShowCategoryName = false`) snižuje vizuální nepořádek, pokud je kategorie již patrná z osy.  
* Povolení `ShowValue` zajistí, že je viditelná skutečná datová hodnota, což je často vyžadováno ve finančních nebo statistických zprávách.

## Krok 5: Uložení upraveného dokumentu

Po úpravě vlastností popisku uložte změny do nového souboru:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Nový soubor (`CustomLabelChart.docx`) obsahuje stejný rozvrh grafu, ale s popiskem, který jste definovali.

## Kompletní zdrojový kód

Níže je kompletní, připravený ke spuštění program. Zkopírujte jej do `Program.cs`, upravte cesty k souborům a spusťte projekt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Očekávaný výsledek

Otevřete `CustomLabelChart.docx` v Microsoft Word. Měli byste vidět, že popisek první řady je vycentrován na každém datovém bodu, zobrazuje pouze číselnou hodnotu a používá “; ” jako oddělovač. Názvy kategorií se již vedle hodnot neobjeví.

## Často kladené otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Co když dokument neobsahuje žádný graf?** | Příklad kontroluje, zda je graf `null`, a v takovém případě ukončí běh s informativní zprávou v konzoli. |
| **Mohu upravovat popisky pro více řad?** | Ano. Projděte `chart.Series` a aplikujte stejná nastavení `DataLabel` na každou `Series[i].DataLabel`. |
| **Jak změním styl písma popisku?** | Použijte `label.Font` (např. `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **Je `DataLabelPosition.Center` podporováno pro všechny typy grafů?** | Většina 2‑D typů grafů jej podporuje. U 3‑D grafů mohou být některá umístění Wordem ignorována. |
| **Potřebuji licenci pro Aspose.Words?** | Evaluační režim funguje, ale přidává vodoznak. Licence vodoznak odstraní a odemkne plnou funkčnost. |

## Profesionální tipy

* **Dávkové zpracování:** Zabalte logiku načítání a ukládání do metody, která přijímá vstupní a výstupní cesty. To usnadní zpracování desítek dokumentů ve smyčce.  
* **Výkon:** Znovu použijte jedinou instanci `Document`, pokud upravujete více grafů ve stejném souboru, abyste se vyhnuli opakovanému I/O.  
* **Testování:** Ověřte změny popisků automatizací vizuálního rozdílu (např. pomocí headless Word viewer), pokud potřebujete výstup potvrdit v CI pipelinech.

## Další kroky

Nyní, když ovládáte základy **edit chart label tutorial**, můžete zkusit:

* **Změnit umístění popisku grafu** pro jiné řady nebo jiné typy grafů  
* **Přizpůsobit formátování datového popisku grafu** jako číselné formáty, barvy písma nebo výplně pozadí  
* **Skrýt název kategorie grafu** a přitom zobrazit název řady u více‑řadových grafů  
* **Zobrazit hodnotu popisku grafu** společně s procentuálními hodnotami u koláčových grafů  

Tyto témata prohloubí vaši kontrolu nad estetikou grafů ve Wordu a připraví vás na pokročilé scénáře reportingu.

---

*Šťastné programování! Pokud se vám tento tutoriál líbil, sdílejte ho s kolegy nebo přispějte vylepšení na GitHubu.*

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným krok‑za‑krokem vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}