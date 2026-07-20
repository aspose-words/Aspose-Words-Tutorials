---
category: general
date: 2026-07-20
description: Přidejte popisky koláčových grafů pomocí Aspose.Words pro .NET. Naučte
  se, jak změnit popisky koláčových grafů, zobrazit procentuální popisky a rychle
  aktualizovat popisky řad grafu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: cs
lastmod: 2026-07-20
og_description: Přidejte popisky koláčových grafů v C# pomocí Aspose.Words. Ovládněte
  úpravu popisků koláčových grafů, zobrazování procentuálních popisků a aktualizaci
  popisků řad grafu během několika kroků.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Přidání popisků koláčových grafů v C# – Kompletní tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Přidání popisků koláčových grafů v C# pomocí Aspose.Words – Kompletní průvodce
url: /cs/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidání popisků koláčových grafů v C# pomocí Aspose.Words – Kompletní průvodce

Potřebujete **přidat popisky koláčových grafů** do dokumentu Word pomocí C#? S Aspose.Words můžete snadno **měnit popisky koláčových grafů** a **zobrazovat procenta koláčových grafů** přímo v souboru—žádná ruční úprava ve Wordu není potřeba.  

V tomto tutoriálu vás provedeme přesnými kroky k **zobrazení procentních popisků**, jejich přemístění a dokonce **aktualizaci popisků řad grafu** pro dynamická data. Na konci budete mít znovupoužitelný úryvek, který můžete vložit do libovolného .NET projektu.

> **Rychlý náhled:** Po absolvování průvodce a otevření uloženého souboru `.docx` se zobrazí koláčový graf, kde je každá část označena svým procentem, umístěným mimo část pro maximální čitelnost.

---

## Co budete potřebovat

- **Aspose.Words for .NET** (nejnovější verze k roku 2026). Můžete ji získat z NuGet: `Install-Package Aspose.Words`.
- **Word dokument**, který již obsahuje koláčový nebo prstencový graf (nazveme jej `Chart.docx`).
- Základní znalost **C#** a Visual Studio (nebo vašeho oblíbeného IDE).

To je vše—žádné další knihovny, žádný COM interop, jen čistý spravovaný kód.

---

## Přidání popisků koláčového grafu – Kompletní implementace

Níže je **kompletní, spustitelný** C# konzolový program, který načte dokument, upraví první koláčový graf a uloží výsledek. Každý řádek je okomentován, abyste pochopili **proč** děláme to, co děláme, a ne jen **co**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Očekávaný výsledek

Otevřete `ChartWithCustomLabels.docx` v Microsoft Word. Měli byste vidět koláčový graf **s procentními popisky umístěnými mimo každou část**. Popisky vypadají například jako „35 %“, „20 %“ atd., což činí graf okamžitě srozumitelným.

---

## Změna popisků koláčového grafu: umístění a formátování

Pokud potřebujete pouze **změnit popisky koláčového grafu** bez zobrazování procent, můžete upravit vlastnost `Position` na jednu z následujících:

| Enum pozice   | Vizuální efekt |
|---------------|----------------|
| `InsideEnd`   | Popisky jsou uvnitř části, těsně na okraji. |
| `Center`      | Popisky se zobrazují uprostřed části (vhodné pro malé koláče). |
| `OutsideEnd`  | Popisky jsou mimo část, spojené s čarou (náš výchozí). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Tip:** `OutsideEnd` funguje nejlépe, když má graf mnoho částí; zabraňuje překrývání textu.

---

## Zobrazení procentních popisků na koláčovém grafu

Vlastnost `ShowPercentage` je **boolean příznak**. Nastavením na `true` řeknete Aspose.Words, aby vypočítala podíl každé části na základě podkladových dat.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Můžete ji také kombinovat s `ShowValue`, pokud potřebujete jak surová čísla, **tak** i procenta:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Když jsou oba příznaky povoleny, popisek vypadá jako „45 % (120)“.

---

## Aktualizace popisků řad grafu pro dynamická data

Často budete generovat grafy za běhu—například měsíční prodeje nebo výsledky průzkumu. Pro **programatickou aktualizaci popisků řad grafu** upravte kolekci `Series` před úpravou popisků dat:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Tento úryvek ukazuje, jak **aktualizovat popisky řad grafu** pro libovolnou řadu, ne jen pro první. Je užitečný při tvorbě reportů, které kombinují skutečná a prognózovaná data.

---

## Okrajové případy a časté úskalí

| Situace | Na co si dát pozor | Řešení |
|---------|--------------------|--------|
| **Graf není koláčový/prstencový** | `Position` nemusí mít žádný vizuální efekt. | Ověřte, že `chart.Type` je `ChartType.Pie` nebo `ChartType.Doughnut`. |
| **Graf nebyl nalezen** | `GetChild` vrací `null`. | Přidejte ochrannou podmínku (viz kód) a zaznamenejte užitečnou zprávu. |
| **Starší verze Wordu** | Některé funkce popisků jsou ignorovány. | Uložte jako `.docx` (moderní formát) pro zajištění plné podpory. |
| **Velký počet částí** | Popisky se mohou překrývat i při `OutsideEnd`. | Zvažte snížení počtu částí nebo zvětšení velikosti grafu. |

---

## Kompletní funkční příklad (Kopíruj‑Vlož)

Níže je **celý program**, který můžete zkopírovat do nového konzolového projektu. Stačí nahradit `YOUR_DIRECTORY` složkou, která obsahuje `Chart.docx`.



## Co byste se měli naučit dál?

Následující tutoriály se zabývají úzce souvisejícími tématy, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Nastavení výchozích možností pro popisky dat v grafu](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Přizpůsobení jedné řady grafu v grafu](/words/english/net/programming-with-charts/single-chart-series/)
- [Vložení sloupcového grafu do Wordu pomocí Aspose.Words pro .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}