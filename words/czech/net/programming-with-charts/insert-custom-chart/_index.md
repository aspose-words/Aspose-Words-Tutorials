---
title: Vložení vlastního sloupcového grafu do dokumentu Word pomocí Aspose.Words for .NET
weight: 310
limit:
description: Vytvořte soubor Word, vložte sloupcový graf, nahraďte jeho data vlastním polem, přidejte název a uložte — vše pomocí Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Vytvořte soubor Word, vložte sloupcový graf, nahraďte jeho data vlastním
    polem, přidejte název a uložte — vše pomocí Aspose.Words for .NET.
  headline: Vložení vlastního sloupcového grafu do dokumentu Word pomocí Aspose.Words
    for .NET
  type: TechArticle
- description: Vytvořte soubor Word, vložte sloupcový graf, nahraďte jeho data vlastním
    polem, přidejte název a uložte — vše pomocí Aspose.Words for .NET.
  name: Vložení vlastního sloupcového grafu do dokumentu Word pomocí Aspose.Words
    for .NET
  steps:
  - name: Vytvořte nový Document a DocumentBuilder k němu připojený.
    text: Vytvořte nový Document a DocumentBuilder k němu připojený.
  - name: Vložte sloupcový graf o velikosti 432 × 252 bodů do dokumentu a získejte
      jeho objekt Chart.
    text: Vložte sloupcový graf o velikosti 432 × 252 bodů do dokumentu a získejte
      jeho objekt Chart.
  - name: Odstraňte automaticky vygenerovanou ukázkovou sérii z grafu.
    text: Odstraňte automaticky vygenerovanou ukázkovou sérii z grafu.
  - name: Definujte popisky kategorií na ose X a položky legendy pro každou sérii.
    text: Definujte popisky kategorií na ose X a položky legendy pro každou sérii.
  - name: Vytvořte dvourozměrné pole, kde každý řádek obsahuje hodnoty pro jednu sérii.
    text: Vytvořte dvourozměrné pole, kde každý řádek obsahuje hodnoty pro jednu sérii.
  - name: Procházejte každou sérii, vyjměte její řádkové hodnoty z matice a přidejte
      sérii do grafu s odpovídající položkou legendy a popisky osy X.
    text: Procházejte každou sérii, vyjměte její řádkové hodnoty z matice a přidejte
      sérii do grafu s odpovídající položkou legendy a popisky osy X.
  - name: Nastavte text názvu grafu na 'Half‑Yearly Revenue' a zobrazte jej.
    text: Nastavte text názvu grafu na 'Half‑Yearly Revenue' a zobrazte jej.
  - name: Uložte dokument obsahující vlastní graf do souboru .docx.
    text: Uložte dokument obsahující vlastní graf do souboru .docx.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` očekává, že délka pole hodnot bude rovna počtu popisků
      osy X, a musíte přidat přesně jednu sérii na každou položku legendy; nesoulad
      vyvolá během běhu `ArgumentException`.'
    question: Co když řádky nebo sloupce v `dataMatrix` neodpovídají délkám `legendEntries`
      nebo `xLabels`?
  - answer: Ano — nahraďte `ChartType.Column` v `docBuilder.InsertChart` libovolným
      jiným `ChartType` (např. `ChartType.Line`) a následná volání `Series.Add` naplní
      nový graf stejným způsobem.
    question: Mohu použít jiný typ grafu, například čárový graf, se stejnou logikou
      naplňování dat?
  - answer: Upravte vlastnosti `Width` a `Height` objektu `Shape`, který vrací `InsertChart`
      (např. `chartContainer.Width = 500; chartContainer.Height = 300;`).
    question: Jak změním velikost grafu po jeho vložení?
  - answer: Nastavte `chartObj.Series[i].HasDataLabel = true;` pro každou sérii po
      jejím přidání, nebo projděte `chartObj.Series` a povolte `HasDataLabel`, aby
      se hodnoty v grafu zobrazily.
    question: Existuje rychlý způsob, jak zobrazit datové popisky u každého sloupce
      grafu?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Přidání vlastního sloupcového grafu do dokumentu Word
og_description: Vyměňte výchozí data grafu za vlastní pole a během okamžiku nastavte název.
og_image_alt: Snímek obrazovky ukazující dokument Word s vlastním sloupcovým grafem vytvořeným pomocí Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení vlastního sloupcového grafu do dokumentu Word pomocí Aspose.Words
Tento tutoriál vás provede vytvořením dokumentu Word, vložením sloupcového grafu, vymazáním jeho výchozích dat a naplněním grafu vlastními hodnotami ze dvourozměrného pole — přiřazením každého řádku k sérii a každého sloupce ke kategorii. Také uvidíte, jak před uložením souboru přidat název grafu. Postupujte podle kroků a vytvořte plně přizpůsobený graf přímo ve vašem souboru Word.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Co když řádky nebo sloupce v `dataMatrix` neodpovídají délkám `legendEntries` nebo `xLabels`?**  
A: `Chart.Series.Add` očekává, že délka pole hodnot bude rovna počtu popisků osy X, a musíte přidat přesně jednu sérii na každou položku legendy; nesoulad vyvolá během běhu `ArgumentException`.

**Q: Mohu použít jiný typ grafu, například čárový graf, se stejnou logikou naplňování dat?**  
A: Ano — nahraďte `ChartType.Column` v `docBuilder.InsertChart` libovolným jiným `ChartType` (např. `ChartType.Line`) a následná volání `Series.Add` naplní nový graf stejným způsobem.

**Q: Jak změním velikost grafu po jeho vložení?**  
A: Upravte vlastnosti `Width` a `Height` objektu `Shape`, který vrací `InsertChart` (např. `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Existuje rychlý způsob, jak zobrazit datové popisky u každého sloupce grafu?**  
A: Nastavte `chartObj.Series[i].HasDataLabel = true;` pro každou sérii po jejím přidání, nebo projděte `chartObj.Series` a povolte `HasDataLabel`, aby se hodnoty v grafu zobrazily.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}