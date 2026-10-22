---
title: Vytvořte tabulku s otočeným textem v dokumentu Word pomocí Aspose.Words pro .NET
weight: 110
limit:
description: Naučte se vytvořit tabulku Word s pevnými šířkami sloupců, otočeným textem, přesnými výškami řádků a naplněnými buňkami pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Naučte se vytvořit tabulku Word s pevnými šířkami sloupců, otočeným
    textem, přesnými výškami řádků a naplněnými buňkami pomocí Aspose.Words pro .NET.
  headline: Vytvořte tabulku s otočeným textem v dokumentu Word pomocí Aspose.Words
    pro .NET
  type: TechArticle
- description: Naučte se vytvořit tabulku Word s pevnými šířkami sloupců, otočeným
    textem, přesnými výškami řádků a naplněnými buňkami pomocí Aspose.Words pro .NET.
  name: Vytvořte tabulku s otočeným textem v dokumentu Word pomocí Aspose.Words pro
    .NET
  steps:
  - name: Vytvořte novou instanci třídy Document a DocumentBuilder, které budou použity
      k vytvoření tabulky.
    text: Vytvořte novou instanci třídy Document a DocumentBuilder, které budou použity
      k vytvoření tabulky.
  - name: Začněte novou tabulku, vložte první buňku a nastavte pevné šířky sloupců,
      aby se automaticky nepřizpůsobovaly.
    text: Začněte novou tabulku, vložte první buňku a nastavte pevné šířky sloupců,
      aby se automaticky nepřizpůsobovaly.
  - name: Vertikálně vycentrujte obsah v aktuální buňce a zapište text první buňky
      prvního řádku.
    text: Vertikálně vycentrujte obsah v aktuální buňce a zapište text první buňky
      prvního řádku.
  - name: Vložte druhou buňku prvního řádku a zapište její text.
    text: Vložte druhou buňku prvního řádku a zapište její text.
  - name: Uzavřete první řádek, čímž dokončíte jeho rozvržení.
    text: Uzavřete první řádek, čímž dokončíte jeho rozvržení.
  - name: Začněte první buňku druhého řádku, nastavte výšku řádku přesně na 100 bodů,
      otočte text nahoru a zapište text buňky.
    text: Začněte první buňku druhého řádku, nastavte výšku řádku přesně na 100 bodů,
      otočte text nahoru a zapište text buňky.
  - name: Vložte druhou buňku druhého řádku, otočte její text dolů a zapište text
      buňky.
    text: Vložte druhou buňku druhého řádku, otočte její text dolů a zapište text
      buňky.
  - name: Uzavřete druhý řádek, čímž dokončíte druhou řádku tabulky.
    text: Uzavřete druhý řádek, čímž dokončíte druhou řádku tabulky.
  - name: Ukončete tvorbu tabulky, čímž uzavřete strukturu tabulky.
    text: Ukončete tvorbu tabulky, čímž uzavřete strukturu tabulky.
  - name: Uložte dokončený dokument do souboru .docx.
    text: Uložte dokončený dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: Po nastavení pevných šířek sloupců přiřaďte každé buňce šířku pomocí `builder.CellFormat.Width
      = <valueInPoints>;` před vložením další buňky; tabulka si tyto přesné šířky
      zachová.
    question: Jak mohu nastavit konkrétní šířky sloupců po volání `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` je nastavení na úrovni buňky,
      takže jej musíte nastavit znovu pro buňky ve druhém řádku (např. `builder.CellFormat.VerticalAlignment
      = CellVerticalAlignment.Center;`) před zápisem jejich obsahu.'
    question: Proč svislé zarovnání ovlivňuje jen první řádek a ne druhý řádek?
  - answer: Ano — nastavte `builder.RowFormat.Height` a `builder.RowFormat.HeightRule
      = HeightRule.Exactly` před každým voláním `builder.EndRow();`; následující řádek
      může mít jinou hodnotu výšky.
    question: Mohu každému řádku přiřadit jinou přesnou výšku, a pokud ano, jak?
  - answer: Resetujte orientaci přiřazením `builder.CellFormat.Orientation = TextOrientation.Horizontal;`
      před zápisem do další buňky.
    question: Jak mohu po použití `TextOrientation.Upward` nebo `Downward` vrátit
      orientaci textu zpět na výchozí hodnotu?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Vytvořte tabulku s otočeným textem v aplikaci Word pomocí Aspose.Words
og_description: Krok‑za‑krokem kód pro vytvoření tabulky s pevnou šířkou, vertikálně otočeným textem a přesnými výškami řádků.
og_image_alt: Snímek obrazovky zobrazující dokument Word s tabulkou, která má pevné šířky sloupců, otočený text v buňkách a definované výšky řádků, vytvořenou pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte tabulku s otočeným textem v dokumentu Word pomocí Aspose.Words pro .NET
Tento tutoriál ukazuje, jak vygenerovat dokument Word a přidat tabulku, jejíž sloupce mají pevné šířky, řádky přesné výšky a text v buňkách je otočen vertikálně. Naučíte se nastavit svislé zarovnání, použít orientaci textu, naplnit každou buňku obsahem a nakonec dokument uložit – vše pomocí Aspose.Words pro .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Jak mohu nastavit konkrétní šířky sloupců po volání `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: Po nastavení pevných šířek sloupců přiřaďte každé buňce šířku pomocí `builder.CellFormat.Width = <valueInPoints>;` před vložením další buňky; tabulka si tyto přesné šířky zachová.

**Q: Proč svislé zarovnání ovlivňuje jen první řádek a ne druhý řádek?**  
A: `builder.CellFormat.VerticalAlignment` je nastavení na úrovni buňky, takže jej musíte nastavit znovu pro buňky ve druhém řádku (např. `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) před zápisem jejich obsahu.

**Q: Mohu každému řádku přiřadit jinou přesnou výšku, a pokud ano, jak?**  
A: Ano — nastavte `builder.RowFormat.Height` a `builder.RowFormat.HeightRule = HeightRule.Exactly` před každým voláním `builder.EndRow();`; následující řádek může mít jinou hodnotu výšky.

**Q: Jak mohu po použití `TextOrientation.Upward` nebo `Downward` vrátit orientaci textu zpět na výchozí hodnotu?**  
A: Resetujte orientaci přiřazením `builder.CellFormat.Orientation = TextOrientation.Horizontal;` před zápisem do další buňky.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}