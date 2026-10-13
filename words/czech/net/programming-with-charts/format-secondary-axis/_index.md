---
title: Formátujte sekundární osu Y jako měnu v grafu Word pomocí Aspose.Words pro .NET
weight: 710
limit:
description: Naučte se přidat a naformátovat sekundární osu Y jako měnu v čárovém grafu Word pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se přidat a naformátovat sekundární osu Y jako měnu v čárovém
    grafu Word pomocí Aspose.Words pro .NET.
  headline: Formátujte sekundární osu Y jako měnu v grafu Word pomocí Aspose.Words
    pro .NET
  type: TechArticle
- description: Naučte se přidat a naformátovat sekundární osu Y jako měnu v čárovém
    grafu Word pomocí Aspose.Words pro .NET.
  name: Formátujte sekundární osu Y jako měnu v grafu Word pomocí Aspose.Words pro
    .NET
  steps:
  - name: Vytvořte nový prázdný dokument Word a DocumentBuilder pro jeho úpravu.
    text: Vytvořte nový prázdný dokument Word a DocumentBuilder pro jeho úpravu.
  - name: Vložte čárový graf o rozměrech 450×250 bodů do dokumentu a získejte jeho
      objekt Chart.
    text: Vložte čárový graf o rozměrech 450×250 bodů do dokumentu a získejte jeho
      objekt Chart.
  - name: Odeberte výchozí zástupnou sérii, kterou Aspose přidává do nového grafu.
    text: Odeberte výchozí zástupnou sérii, kterou Aspose přidává do nového grafu.
  - name: Definujte štítky čtvrtletí a přidejte primární datovou sérii s ukázkovými
      hodnotami do grafu.
    text: Definujte štítky čtvrtletí a přidejte primární datovou sérii s ukázkovými
      hodnotami do grafu.
  - name: Vytvořte sekundární skupinu sérií typu Line a přiřaďte ji ke skupině sekundární
      osy.
    text: Vytvořte sekundární skupinu sérií typu Line a přiřaďte ji ke skupině sekundární
      osy.
  - name: Skryjte sekundární osu X, aby byla viditelná pouze sekundární osa Y.
    text: Skryjte sekundární osu X, aby byla viditelná pouze sekundární osa Y.
  - name: Zobrazte název sekundární osy Y a nastavte jeho text na "Sales (USD)".
    text: Zobrazte název sekundární osy Y a nastavte jeho text na "Sales (USD)".
  - name: Nastavte číselný formát sekundární osy Y na měnový vzor se dvěma desetinnými
      místy a odpojte jej od formátování zdroje.
    text: Nastavte číselný formát sekundární osy Y na měnový vzor se dvěma desetinnými
      místy a odpojte jej od formátování zdroje.
  - name: Přidejte pomocnou sérii do sekundární skupiny, která poskytne data vykreslená
      proti sekundární ose Y.
    text: Přidejte pomocnou sérii do sekundární skupiny, která poskytne data vykreslená
      proti sekundární ose Y.
  - name: Uložte dokončený dokument do souboru s názvem ProfitChart.docx v aktuálním
      adresáři.
    text: Uložte dokončený dokument do souboru s názvem ProfitChart.docx v aktuálním
      adresáři.
  type: HowTo
- questions:
  - answer: Graf si ponechá výchozí zástupnou sérii, kterou Aspose.Words vloží, takže
      vaše vlastní „Main Series“ se objeví vedle nechtěných datových bodů.
    question: Co se stane, pokud vynechám volání `lineChart.Series.Clear()`?
  - answer: Nastavte `secondarySeriesGroup.AxisX.Hidden = false;` (nebo jednoduše
      vynechejte řádek, který ji nastavuje na `true`).
    question: Jak mohu zobrazit sekundární osu X místo jejího skrytí?
  - answer: Ano – změňte řetězec formátu, např. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = "\"€\"#,##0.00";` pro eura nebo upravte vzor podle vašeho locale.
    question: Mohu pro sekundární osu Y použít jiný měnový symbol nebo formát?
  - answer: Když je `IsLinkedToSource` nastaven na true, osa zdědí číselný formát
      z podkladového zdroje dat, čímž přepíše jakýkoli vlastní `FormatCode`; nastavení
      na false vynutí, aby graf použil formát, který určíte.
    question: Proč potřebuji nastavit `IsLinkedToSource = false` při aplikaci vlastního
      číselného formátu?
  - answer: Ano, přiřaďte `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (nebo `Right` pro výchozí) k určení, na které straně bude osa vykreslena.
    question: Je možné přesunout sekundární osu Y na levou stranu grafu?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formátujte sekundární osu grafu jako měnu
og_description: Naučte se přidat sekundární osu Y do čárového grafu Word a stylizovat ji jako měnu se dvěma desetinnými místy.
og_image_alt: Snímek obrazovky zobrazující čárový graf Word se sekundární osou Y formátovanou jako měna pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formátujte sekundární osu Y jako měnu v grafu Word pomocí Aspose.Words pro .NET
Cílem tohoto tutoriálu je ukázat, jak vytvořit dokument Word, vložit čárový graf, přidat sekundární osu Y, naformátovat tuto osu jako měnu se dvěma desetinnými místy a svázat s ní sekundární datovou sérii pomocí Aspose.Words pro .NET. Formátování sekundární osy jako měny vám umožní jasně prezentovat finanční data vedle primární série. Postupujte podle krok‑za‑krokem kódu a uvidíte graf vykreslený přímo v generovaném dokumentu.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: Co se stane, pokud vynechám volání `lineChart.Series.Clear()`?**  
A: Graf si ponechá výchozí zástupnou sérii, kterou Aspose.Words vloží, takže vaše vlastní „Main Series“ se objeví vedle nechtěných datových bodů.

**Q: Jak mohu zobrazit sekundární osu X místo jejího skrytí?**  
A: Nastavte `secondarySeriesGroup.AxisX.Hidden = false;` (nebo jednoduše vynechejte řádek, který ji nastavuje na `true`).

**Q: Mohu pro sekundární osu Y použít jiný měnový symbol nebo formát?**  
A: Ano – změňte řetězec formátu, např. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = "\"€\"#,##0.00";` pro eura nebo upravte vzor podle vašeho locale.

**Q: Proč potřebuji nastavit `IsLinkedToSource = false` při aplikaci vlastního číselného formátu?**  
A: Když je `IsLinkedToSource` nastaven na true, osa zdědí číselný formát z podkladového zdroje dat, čímž přepíše jakýkoli vlastní `FormatCode`; nastavení na false vynutí, aby graf použil formát, který určíte.

**Q: Je možné přesunout sekundární osu Y na levou stranu grafu?**  
A: Ano, přiřaďte `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (nebo `Right` pro výchozí) k určení, na které straně bude osa vykreslena.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}