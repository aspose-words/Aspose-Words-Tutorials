---
title: Přizpůsobte mřížky osy X ve sloupcovém grafu pomocí Aspose.Words pro .NET
weight: 610
limit:
description: Naučte se přidávat a barevně přizpůsobovat hlavní mřížky osy X ve sloupcovém grafu Word pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se přidávat a barevně přizpůsobovat hlavní mřížky osy X ve sloupcovém
    grafu Word pomocí Aspose.Words pro .NET.
  headline: Přizpůsobte mřížky osy X ve sloupcovém grafu pomocí Aspose.Words pro .NET
  type: TechArticle
- description: Naučte se přidávat a barevně přizpůsobovat hlavní mřížky osy X ve sloupcovém
    grafu Word pomocí Aspose.Words pro .NET.
  name: Přizpůsobte mřížky osy X ve sloupcovém grafu pomocí Aspose.Words pro .NET
  steps:
  - name: Vytvořte nový dokument Word a DocumentBuilder pro jeho úpravu.
    text: Vytvořte nový dokument Word a DocumentBuilder pro jeho úpravu.
  - name: Vložte do dokumentu sloupcový graf o rozměrech 432×252 a získejte jeho objekt
      Chart.
    text: Vložte do dokumentu sloupcový graf o rozměrech 432×252 a získejte jeho objekt
      Chart.
  - name: Odeberte výchozí řadu a přidejte vlastní řadu se třemi skupinami a hodnotami.
    text: Odeberte výchozí řadu a přidejte vlastní řadu se třemi skupinami a hodnotami.
  - name: Získejte odkaz na primární vodorovnou (X) osu grafu.
    text: Získejte odkaz na primární vodorovnou (X) osu grafu.
  - name: Povolte zobrazení hlavních mřížek na primární ose X.
    text: Povolte zobrazení hlavních mřížek na primární ose X.
  - name: Nastavte barvu mřížek na modrou a jejich tloušťku na 2 body.
    text: Nastavte barvu mřížek na modrou a jejich tloušťku na 2 body.
  - name: Uložte dokument do souboru .docx.
    text: Uložte dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: 'Nastavte stejnou vlastnost osy na false: `horizontalAxis.HasMajorGridlines
      = false;` přepíná viditelnost hlavních mřížek osy X.'
    question: Jak mohu opět skrýt hlavní mřížky po jejich povolení?
  - answer: Ne, nastavení `Format.Stroke` se vztahuje pouze na osu, kterou upravujete;
      pro stylování mřížek osy Y musíte upravit `chart.AxisY.Format.Stroke` samostatně.
    question: Ovlivní změna `horizontalAxis.Format.Stroke.Color` také mřížky osy Y?
  - answer: Použijte `horizontalAxis.Format.Stroke.Weight` a přiřaďte hodnotu typu
      double (např. `0.5`), aby byly mřížky tenčí.
    question: Která vlastnost řídí tloušťku hlavních mřížek osy X?
  - answer: Ano, nastavte `horizontalAxis.Format.Stroke.DashStyle` na hodnotu výčtu
      `DashStyle`, například `DashStyle.Dash` nebo `DashStyle.Dot`.
    question: Mohu změnit vzor čáry hlavních mřížek osy X?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: Stylizujte mřížky osy X ve sloupcovém grafu Word.
og_description: Povolte a barevně přizpůsobte hlavní mřížky primární osy X grafu Word pomocí Aspose.Words pro .NET.
og_image_alt: Návod ukazující dokument Word se sloupcovým grafem, kde jsou hlavní mřížky primární osy X zvýrazněny vlastní barvou pomocí Aspose.Words pro .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přizpůsobte mřížky osy X ve sloupcovém grafu pomocí Aspose.Words pro .NET
Cílem tohoto tutoriálu je naučit se, jak vytvořit dokument Word, vložit sloupcový graf, nahradit jeho výchozí data a poté povolit hlavní mřížky na primární ose X. Také uvidíte, jak změnit barvu čáry mřížek tak, aby odpovídala vašemu designu. Postupujte podle krok‑za‑krokem kódu a získáte přesnou kontrolu nad viditelností a stylem mřížek osy X.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: Jak mohu opět skrýt hlavní mřížky po jejich povolení?**  
A: Nastavte stejnou vlastnost osy na false: `horizontalAxis.HasMajorGridlines = false;` přepíná viditelnost hlavních mřížek osy X.

**Q: Ovlivní změna `horizontalAxis.Format.Stroke.Color` také mřížky osy Y?**  
A: Ne, nastavení `Format.Stroke` se vztahuje pouze na osu, kterou upravujete; pro stylování mřížek osy Y musíte upravit `chart.AxisY.Format.Stroke` samostatně.

**Q: Která vlastnost řídí tloušťku hlavních mřížek osy X?**  
A: Použijte `horizontalAxis.Format.Stroke.Weight` a přiřaďte hodnotu typu double (např. `0.5`), aby byly mřížky tenčí.

**Q: Mohu změnit vzor čáry hlavních mřížek osy X?**  
A: Ano, nastavte `horizontalAxis.Format.Stroke.DashStyle` na hodnotu výčtu `DashStyle`, například `DashStyle.Dash` nebo `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}