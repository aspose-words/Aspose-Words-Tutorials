---
category: general
date: 2026-10-13
description: Naučte se programově upravovat popisky grafů v dokumentu Word pomocí
  C#. Tento průvodce pokrývá manipulaci s grafy v Aspose.Words a zarovnání popisků.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: cs
lastmod: 2026-10-13
og_description: Programově upravte popisky grafu ve Word dokumentu pomocí C#. Postupujte
  podle tohoto kompletního tutoriálu a změňte umístění popisků, zarovnání a další.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Programově upravte popisky grafu ve Wordu – krok‑za‑krokem průvodce v C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Programově upravit popisky grafu v dokumentu Word pomocí C#
url: /cs/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programatické úpravy popisků grafu ve Word dokumentu pomocí C#

Pokud potřebujete **programaticky upravit popisky grafu** ve Word dokumentu, tento návod vám přesně ukáže, jak to provést pomocí C#. Ať už generujete zprávy, automatizujete dashboardy nebo přizpůsobujete šablony, uvidíte kompletní, spustitelný příklad, který mění umístění a zarovnání popisků grafu uvnitř souboru .docx.

Také se naučíte, jak používat techniky **Aspose.Words chart manipulation**, pracovat s více sériemi a vyhnout se běžným úskalím při práci s objekty **C# chart data label**.

## Požadavky

* .NET 6.0 (nebo novější) nainstalováno  
* Visual Studio 2022 (nebo jakékoli C# IDE)  
* NuGet balíček **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Word dokument (`input.docx`), který obsahuje alespoň jeden graf  

Tyto položky jsou vyžadovány pro **Word document chart example**, který budeme upravovat.

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte nový konzolový projekt a přidejte potřebné `using` direktivy. Tím připravíte prostředí pro **programatické úpravy popisků grafu**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Proč tento krok?*  
Načtení dokumentu vám poskytuje přístup k internímu stromu **Word document chart example**, kde jsou grafy uloženy jako uzly tvaru.

## Krok 2: Najděte první tvar grafu

Grafy jsou uloženy jako uzly `Shape`. Následující kód získá první graf v dokumentu, který je cílem našich úprav popisků.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Proč tento krok?*  
Metoda `GetChild` vyhledává rekurzivně (`true`) a vrací první uzel typu `Shape`. Přetypování na `Chart` nám umožňuje pracovat s API specifickým pro grafy.

## Krok 3: Přístup k datovému popisku, který chcete upravit

Každá série v grafu má kolekci datových popisků. Pro jednoduchý graf stačí často první popisek. Níže uvedený kód ukazuje, jak k němu přistoupit.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Proč tento krok?*  
`ChartSeries` představuje sérii bodů. `DataLabelCollection` obsahuje popisky pro tuto sérii, což umožňuje přesné řízení umístění a zarovnání.

## Krok 4: Změna umístění a zarovnání popisků

Nyní **programaticky upravujeme popisky grafu** nastavením pozice, vodorovného a svislého zarovnání. Tyto vlastnosti odpovídají možnostem, které vidíte v uživatelském rozhraní Wordu.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Proč tato nastavení?*  

* `OutsideEnd` umístí popisek těsně za konec každého sloupce nebo pruhu, což zlepšuje čitelnost.  
* `HorizontalAlignment.Center` udržuje text vycentrovaný nad bodem, zatímco `VerticalAlignment.Top` zarovnává horní okraj popisku s datovým bodem, čímž zabraňuje překrytí s ostatními prvky.

### Tip
Pokud má graf více sérií, projděte `chart.Series` a aplikujte stejná nastavení na každou `DataLabelCollection`. Tím zajistíte jednotný vzhled po celém grafu.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Krok 5: Uložení upraveného dokumentu

Po úpravě popisků uložte změny do nového souboru. Tím se dokončí proces **modify chart label position**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Když otevřete `output.docx`, uvidíte, že každý popisek grafu byl přesunut na vnější konec svého datového bodu, vodorovně vycentrován a svisle zarovnán nahoru.

## Okrajové případy a varianty

| Situace | Na co si dát pozor | Doporučený postup |
|-----------|-------------------|----------------------|
| **Více grafů** ve stejném dokumentu | `GetChild` vrací pouze první graf. | Použijte `doc.GetChildNodes(NodeType.Shape, true)`, abyste prošli všechny tvary grafů. |
| **Série bez datových popisků** | `DataLabelCollection` může být prázdná. | Zkontrolujte `series.HasDataLabels` před přístupem ke kolekci. |
| **Různé typy grafů** (koláčový, čárový, rozptylový) | Ne všechny hodnoty `DataLabelPosition` jsou platné. | Použijte `DataLabelPosition.Auto` pro grafy, které automaticky rozhodnou o nejlepším umístění. |
| **Lokalizace** | Konstanty zarovnání jsou jazykově nezávislé, ale vykreslený text může vyžadovat podporu zprava doleva. | Nastavte `dataLabel.TextDirection`, pokud potřebujete jazyky RTL. |

## Kompletní, spustitelný příklad

Níže je celý program, který můžete zkopírovat, vložit a spustit. Nahraďte `YOUR_DIRECTORY` skutečnou cestou ke složce.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Očekávaný výsledek:** Otevřením `output.docx` uvidíte, že každý popisek grafu je umístěn mimo datový bod, vodorovně vycentrován a svisle zarovnán nahoru – přesně takový efekt **programatických úprav popisků grafu**, který jste naprogramovali.

## Závěr

Nyní víte, jak **programaticky upravit popisky grafu** ve Word dokumentu pomocí C#. Tutoriál pokryl:

* Načtení dokumentu s **Aspose.Words chart manipulation**  
* Přístup k **C# chart data label**  
* Změnu **modify chart label position** a zarovnání  
* Uložení souboru a řešení běžných okrajových případů  

Odtud můžete zkoumat pokročilejší scénáře, jako je přizpůsobení fontů popisků, přidání podmíněného formátování nebo aktualizace více grafů v dávkovém procesu. Experimentujte s různými možnostmi `DataLabelPosition`, abyste našli styl, který nejlépe vyhovuje vašim zprávám.

---

*Připraveni vylepšit svůj automatizovaný reportingový proces? Zkuste přidat vlastní číselné formáty k popiskům nebo exportovat graf jako obrázek pro použití v PDF.*

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Nastavit jednotné datové popisky ve sloupcovém grafu pomocí Aspose.Words pro .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Nastavit výchozí možnosti pro datové popisky v grafu](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Aktualizovat data sérií grafu ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}