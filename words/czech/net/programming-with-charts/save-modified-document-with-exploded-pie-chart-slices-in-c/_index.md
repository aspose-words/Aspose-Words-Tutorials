---
category: general
date: 2026-10-13
description: 'Uložit upravený dokument po úpravě koláčového grafu: rozdělit výseče,
  změnit úhel první výseče a zobrazit procentuální popisky v C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: cs
lastmod: 2026-10-13
og_description: Uložte upravený dokument po přizpůsobení koláčového grafu v C#. Naučte
  se, jak rozdělit výseky koláčového grafu, změnit úhel první výseky a zobrazit procentuální
  popisky.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Uložte upravený dokument s roztroušenými výsečemi koláčového grafu – průvodce
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Uložit upravený dokument s oddělenými výsečemi koláčového grafu v C#
url: /cs/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uložte upravený dokument s roztrženými výsečemi koláčového grafu v C#

Pokud potřebujete **uložit upravený dokument** po úpravě koláčového grafu ve Wordu, tento návod vám přesně ukáže, jak na to. Naučíte se roztrhnout výseče koláčového grafu, změnit úhel první výseče a zobrazit štítky s procenty – vše pomocí několika řádků kódu v C#.

Přizpůsobení grafů je častým požadavkem při programovém generování reportů, faktur nebo dashboardů. Na konci tohoto tutoriálu budete schopni načíst soubor DOCX, upravit vzhled grafu a **uložit upravený dokument** připravený k distribuci.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
- Aspose.Words pro .NET 23.10 nebo novější (zkušební verze nebo licencovaná kopie)
- Word soubor (`input.docx`) obsahující jediný koláčový graf
- Visual Studio 2022 nebo jakékoli C# IDE

> **Tip:** Balíček Aspose.Words NuGet se přidá pomocí `dotnet add package Aspose.Words`.

## Krok 1: Načtěte Word dokument, který obsahuje graf

Prvním krokem je otevřít zdrojový soubor DOCX. Třída `Document` představuje celý Word soubor v paměti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Načtením dokumentu získáte plný přístup ke všem uzlům, včetně tvarů, které hostí grafy.

## Krok 2: Získejte první tvar grafu z dokumentu

Grafy jsou uloženy uvnitř uzlů `Shape`. První graf můžete najít pomocí `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Pokud dokument obsahuje více grafů, upravte index (`0`) nebo iterujte přes kolekci. Tento řádek zajistí, že máte referenci na objekt `Chart`, který budete upravovat.

## Krok 3: Roztrhněte výseče koláčového grafu

Roztržení výseče ji oddělí od zbytku koláče, což usnadní čtení grafu. Vlastnost `Explode` funguje pro celou sérii.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Nastavením `Explode` na `true` **roztrhnete výseče koláčového grafu** pro celou sérii, což je užitečné, když chcete, aby každá výseč vynikla.

## Krok 4: Změňte úhel první výseče

Někdy potřebujete, aby první výseč začínala pod vlastním úhlem, například aby odpovídala designovému směrnici.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

Vlastnost `FirstSliceAngle` **mění orientaci první výseče**, otáčením celého koláče tak, aby první výseč začínala při 30 stupních.

## Krok 5: Zobrazte procentuální štítky na výsečích koláče

Zobrazení číselného podílu každé výseče je často vyžadováno v reportech. Příznak `DataLabel.ShowPercentage` zapíná zobrazení procentuálních hodnot.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Tento krok **zobrazuje procentuální štítky** přímo na grafu, což také splňuje požadavek **zobrazit procenta v koláči**.

## Krok 6: Uložte upravený dokument

Po aplikaci všech úprav uložte změny do nového souboru. Metoda `Save` zapíše aktualizovaný DOCX na disk.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Nyní máte **uložený upravený dokument**, který obsahuje roztržený koláčový graf, otočenou první výseč a viditelné procentuální štítky.

![Uložený upravený dokument zobrazující roztržené výseče koláčového grafu](/images/pie-chart-exploded.png "Uložený upravený dokument s roztrženými výsečemi koláčového grafu a procentuálními štítky")

*Snímek obrazovky ilustruje finální výstup po uložení dokumentu.*

## Kompletní, spustitelný příklad

Spojením všech částí získáte kompletní program, který můžete zkopírovat a vložit do konzolového projektu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Očekávaný výsledek

Otevřením `output.docx` se zobrazí koláčový graf, kde:

- Každá výseč je mírně oddělena (**exploded pie chart slices**)
- První výseč začíná s posunem 30 stupňů (**change first slice**)
- Každá výseč zobrazuje svůj podíl v procentech (**show percentage labels**, **display percentages pie**)
- Soubor byl **save modified document** bez změny originálu.

## Časté otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Co když dokument neobsahuje žádný graf?** | Kód kontroluje `null` po `GetChild`. Pokud graf neexistuje, můžete jej buď přidat programově, nebo ukončit s jasnou zprávou. |
| **Mohu roztrhnout jen jednu výseč?** | Ano. Použijte `chart.PieChart.Series[0].DataPoints[i].Explosion = true;`, kde `i` je index výseče. |
| **Jak změním formát štítku (např. zobrazit hodnotu + %)?** | Nastavte `chart.PieChart.DataLabel.ShowValue = true;` a volitelně `chart.PieChart.DataLabel.ShowPercentage = true;` pro kombinaci obojího. |
| **Zůstane styl grafu po uložení zachován?** | Aspose.Words zachovává veškeré styly, včetně barev a fontů, když **save modified document**. |
| **Mohu zpracovat více grafů v jednom souboru?** | Procházejte všechny uzly `Shape` s `NodeType.Shape` a filtrujte podle `shape.HasChart`. Na každý graf aplikujte stejné kroky. |

## Závěr

Nyní víte, jak **uložit upravený dokument** po programové úpravě koláčového grafu ve Wordu. Průvodce pokryl roztržení výsečí koláčového grafu, změnu úhlu první výseče a zobrazení procentuálních štítků – splňující požadavky **show percentage labels**, **explode pie chart slices**, **display percentages pie** a **change first slice**.

Další kroky, které můžete prozkoumat:

- Dynamické přidávání datových sérií (`chart.Series.Add(...)`)  
- Přizpůsobení umístění legendy a názvů grafů  
- Převod DOCX do PDF při zachování stylu grafu  

Neváhejte experimentovat s různými úhly, nastavením roztržení nebo formáty štítků, aby vyhovovaly vašim potřebám reportování. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak uložit upravený dokument v C# s Aspose.Words – krok za krokem průvodce](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Aktualizace datové série grafu ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Vložení sloupcového grafu do Word dokumentu](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}