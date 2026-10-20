---
category: general
date: 2026-10-20
description: Vytvořte koláčový graf v dokumentu Word pomocí Aspose.Words – krok za
  krokem průvodce, který ukazuje, jak nastavit barvu, oddělit výseč a uložit dokument
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: cs
lastmod: 2026-10-20
og_description: Vytvořte koláčový graf v dokumentu Word pomocí Aspose.Words. Naučte
  se nastavit barvu, oddělit výseč a uložit dokument Word v jednom spustitelném příkladu.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Vytvořte koláčový graf v dokumentu Word – kompletní průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Jak vytvořit koláčový graf ve Word dokumentu pomocí Aspose.Words
url: /cs/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit koláčový graf v dokumentu Word pomocí Aspose.Words

Pokud potřebujete **vytvořit koláčový graf** uvnitř souboru Word, tento průvodce vám přesně ukáže, jak na to. Uvidíte, jak nastavit vlastní barvu, „explodovat“ výsek pro zdůraznění a nakonec **uložit dokument Word** s vloženým grafem.

Generování grafů programově odstraňuje ruční kroky otevírání Wordu, vkládání grafu a úpravy jeho vzhledu. Na konci tohoto tutoriálu budete mít kompletní, spustitelnou C# konzolovou aplikaci, která vytvoří koláčový graf, přizpůsobí jej a zapíše výsledek na disk.

## Požadavky

* .NET 6.0 SDK nebo novější nainstalováno  
* Platná licence Aspose.Words pro .NET (nebo bezplatný evaluační klíč)  
* IDE, např. Visual Studio 2022 nebo VS Code  

Kromě `Aspose.Words` nejsou vyžadovány žádné další balíčky NuGet.

## Jak vytvořit koláčový graf v dokumentu Word

Prvním krokem je vytvořit instance `Document` a `DocumentBuilder`. Builder vám poskytuje přístup k vysoce‑úrovňovým funkcím Wordu, včetně vkládání grafů.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

V tomto okamžiku dokument již obsahuje základní koláčový graf. Následující sekce vysvětlují **jak explodovat výsek**, **jak nastavit barvu** a **jak uložit dokument Word**.

## Jak explodovat výsek pro zdůraznění

Explodování výseku jej oddělí od zbytku koláče, čímž přitáhne pozornost čtenáře. API Aspose.Words vám umožňuje zadat vzdálenost exploze v bodech.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Proč explodovat výsek? V reportech, které zdůrazňují konkrétní kategorii – například „Nejprodávanější produkt“ – vizuální oddělení okamžitě učiní datový bod rozpoznatelným.

## Jak nastavit barvu na výseku grafu

Vlastní barvy zlepšují konzistenci značky a čitelnost. Můžete přiřadit libovolnou `System.Drawing.Color` konkrétnímu datovému bodu.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Nejste omezeni na předdefinované barvy; můžete vytvořit hodnotu `Color.FromArgb` pro přesné odstíny.

## Jak uložit dokument Word s grafem

Jakmile graf vypadá tak, jak chcete, uložení souboru je jednoduché. Metoda `Document.Save` zapíše dokument ve formátu, který určíte – zde používáme výchozí `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Spuštěním programu se vytvoří `PieChart.docx`. Otevřením souboru v Microsoft Word se zobrazí koláčový graf, kde je první výsek explodován a vyplněn červeně, přesně podle toho, co určuje kód.

### Očekávaný výsledek

* Soubor Word pojmenovaný **PieChart.docx** v `C:\Temp`.  
* Dokument obsahuje jediný koláčový graf o velikosti 400 × 300 bodů.  
* Výsek 0 je posunut o 20 bodů a vyplněn červeně, zatímco ostatní výseky zachovávají výchozí barvu.  

Můžete ověřit explozi a barvu výběrem grafu ve Wordu a kontrolou vlastností výseku.

## Profesionální tipy a časté úskalí

* **Pro tip:** Pokud potřebujete změnit název grafu nebo legendu, použijte před uložením vlastnosti `pieChart.Title.Text` a `pieChart.Legend`.  
* **Dejte si pozor na:** Zapomenutí vymazat výchozí datové body může vést k nadbytečným, nechtěným výsekům. Vždy zavolejte `Series[0].DataPoints.Clear()` před přidáním vlastních dat.  
* **Tip pro výkon:** U velkých dokumentů znovu použijte jedinou instanci `DocumentBuilder` místo vytváření mnoha builderů; tím se sníží zatížení paměti.

## Jak vytvořit graf pomocí Aspose.Words (další kontext)

Metoda `InsertChart` podporuje mnoho typů grafů kromě koláčových, například sloupcové, čárové a plošné grafy. Pro přepnutí na jiný typ nahraďte `ChartType.Pie` požadovanou hodnotou výčtu, např. `ChartType.Column`. Zbývající kroky přizpůsobení (explodování výseků, nastavení barev) následují stejný vzor, i když ne všechny typy grafů mají vlastnost „explosion“.

## Jak explodovat výsek v jiných typech grafů

Pouze koláčové grafy mají metodu `SetExplosion`. Pokud ji zkusíte zavolat u sloupcového grafu, API vyhodí `ArgumentException`. V takových případech zvažte použití popisků dat nebo výkřiků (callouts) k zvýraznění konkrétního sloupce.

## Jak nastavit barvu na sérii místo jednotlivého výseku

Pokud chcete, aby každý výsek v sérii měl stejnou barvu, projděte smyčkou datové body:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Tento přístup je užitečný, když potřebujete jednotné barevné schéma napříč více grafy.

## Jak uložit dokument Word v jiných formátech

Aspose.Words může exportovat do PDF, HTML a mnoha dalších formátů. Změňte příponu souboru v `Save` a volitelně předávejte objekt `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Renderovací engine grafu automaticky převádí graf do cílového formátu, zachovává barvy a nastavení exploze.

## Závěr

Nyní víte, jak **vytvořit koláčový graf** v dokumentu Word, přizpůsobit jeho vzhled **explodováním výseku** a **nastavením barvy**, a nakonec **uložit dokument Word** s vloženým grafem. Tento kompletní příklad vám poskytuje pevný základ pro automatizaci generování reportů, dashboardů nebo jakéhokoli scénáře, kde je potřeba programově vložit vizuální data.

### Další kroky

* Prozkoumejte další typy grafů (`ChartType.Column`, `ChartType.Line`) a rozšiřte tak svou sadu nástrojů pro reportování.  
* Kombinujte více grafů v jednom dokumentu a vytvořte tak komplexní dashboardy.  
* Experimentujte s `ChartDataLabel` pro zobrazení procent nebo hodnot přímo na výsecích.  

Neváhejte přizpůsobit kód vlastním zdrojům dat – ať už čerpáte hodnoty z databáze, API nebo CSV souboru, stejný workflow Aspose.Words platí. Šťastné vytváření grafů!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Explodovat výsek koláčového grafu v C# s Aspose.Words – Kompletní průvodce](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Vložit vlastní sloupcový graf do dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Aktualizovat data řady grafu v dokumentu Word pomocí Aspose.Words pro .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}