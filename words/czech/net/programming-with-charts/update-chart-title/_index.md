---
title: Aktualizujte název grafu a přepněte viditelnost legendy ve Wordu pomocí Aspose.Words pro .NET
weight: 810
limit:
description: Naučte se měnit název grafu a řídit viditelnost legendy v dokumentu Word pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se měnit název grafu a řídit viditelnost legendy v dokumentu
    Word pomocí Aspose.Words pro .NET.
  headline: Aktualizujte název grafu a přepněte viditelnost legendy ve Wordu pomocí
    Aspose.Words pro .NET
  type: TechArticle
- description: Naučte se měnit název grafu a řídit viditelnost legendy v dokumentu
    Word pomocí Aspose.Words pro .NET.
  name: Aktualizujte název grafu a přepněte viditelnost legendy ve Wordu pomocí Aspose.Words
    pro .NET
  steps:
  - name: Definujte uživatelem dodaný název grafu a zda má být legenda zobrazena.
    text: Definujte uživatelem dodaný název grafu a zda má být legenda zobrazena.
  - name: Vytvořte nový dokument Word a DocumentBuilder pro přidání obsahu.
    text: Vytvořte nový dokument Word a DocumentBuilder pro přidání obsahu.
  - name: Vložte do dokumentu sloupcový graf o rozměrech 432 × 252 pt a ověřte, že
      tvar skutečně obsahuje graf.
    text: Vložte do dokumentu sloupcový graf o rozměrech 432 × 252 pt a ověřte, že
      tvar skutečně obsahuje graf.
  - name: Získejte objekt grafu, nastavte jeho text názvu na hodnotu od uživatele
      a zajistěte, aby byl název zobrazen.
    text: Získejte objekt grafu, nastavte jeho text názvu na hodnotu od uživatele
      a zajistěte, aby byl název zobrazen.
  - name: 'Nastavte legendu: pokud je požadována, zobrazte ji vpravo, jinak ji skryjte,
      a povolte překrytí oblasti grafu.'
    text: 'Nastavte legendu: pokud je požadována, zobrazte ji vpravo, jinak ji skryjte,
      a povolte překrytí oblasti grafu.'
  - name: Uložte upravený dokument na disk jako CustomChart.docx.
    text: Uložte upravený dokument na disk jako CustomChart.docx.
  type: HowTo
- questions:
  - answer: Když je `displayLegend` nastaveno na `true`, kód nastaví `chartLegend.Position`
      na `LegendPosition.Right`, čímž se legenda zobrazí na pravé straně oblasti grafu;
      vlastnost `Overlay` zůstává `true`, takže legenda může překrývat graf a šetřit
      místo.
    question: Co změní nastavení `displayLegend` na `true` v generovaném grafu?
  - answer: Nastavte `chartTitle.Show = false` (nebo jednoduše nevyplňujte `Show`
      na `true`) po přiřazení `chartTitle.Text`; název se v dokumentu Word nevykreslí.
    question: Jak mohu skrýt název grafu, pokud jej uživatel neposkytne?
  - answer: Ano — `InsertChart` vrací `Shape`, který by měl obsahovat graf, ale ověření
      `HasChart` zajišťuje, že tvar skutečně obsahuje objekt `Chart`; jinak kód vyhodí
      `InvalidOperationException`.
    question: Je nutné po volání `InsertChart` zkontrolovat `chartContainer.HasChart`?
  - answer: Rozhodně; přiřaďte libovolnou hodnotu z výčtu `LegendPosition` (např.
      `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) do `chartLegend.Position`,
      abyste legendu podle potřeby přemístili.
    question: Mohu legendu umístit jinam než na pravou stranu?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Změna názvu grafu a legendy ve Wordu
og_description: Naučte se nastavit vlastní název grafu a řídit zobrazení legendy v dokumentu Word pomocí Aspose.Words pro .NET.
og_image_alt: Průvodce ukazující kód, který aktualizuje název grafu a přepíná legendu v dokumentu Word pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aktualizujte název grafu a přepněte viditelnost legendy ve Wordu pomocí Aspose.Words pro .NET
Tento tutoriál ukazuje, jak programově upravit graf v dokumentu Word pomocí Aspose.Words pro .NET. Naučíte se vložit sloupcový graf, nahradit jeho název textem poskytnutým uživatelem a řídit viditelnost a překrytí legendy podle uživatelských preferencí. Tyto kroky vám umožní dynamicky přizpůsobit prezentaci grafu bez ruční úpravy.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Co změní nastavení `displayLegend` na `true` v generovaném grafu?**  
A: Když je `displayLegend` nastaveno na `true`, kód nastaví `chartLegend.Position` na `LegendPosition.Right`, čímž se legenda zobrazí na pravé straně oblasti grafu; vlastnost `Overlay` zůstává `true`, takže legenda může překrývat graf a šetřit místo.

**Q: Jak mohu skrýt název grafu, pokud jej uživatel neposkytne?**  
A: Nastavte `chartTitle.Show = false` (nebo jednoduše nevyplňujte `Show` na `true`) po přiřazení `chartTitle.Text`; název se v dokumentu Word nevykreslí.

**Q: Je nutné po volání `InsertChart` zkontrolovat `chartContainer.HasChart`?**  
A: Ano — `InsertChart` vrací `Shape`, který by měl obsahovat graf, ale ověření `HasChart` zajišťuje, že tvar skutečně obsahuje objekt `Chart`; jinak kód vyhodí `InvalidOperationException`.

**Q: Mohu legendu umístit jinam než na pravou stranu?**  
A: Rozhodně; přiřaďte libovolnou hodnotu z výčtu `LegendPosition` (např. `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) do `chartLegend.Position`, abyste legendu podle potřeby přemístili.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}