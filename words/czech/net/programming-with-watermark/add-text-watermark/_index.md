---
title: Přidejte červený diagonální textový vodoznak do dokumentů Word pomocí Aspose.Words pro .NET
weight: 110
limit:
description: Automaticky aplikujte červený diagonální textový vodoznak na každý soubor Word generovaný v hromadném procesu pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Automaticky aplikujte červený diagonální textový vodoznak na každý
    soubor Word generovaný v hromadném procesu pomocí Aspose.Words pro .NET.
  headline: Přidejte červený diagonální textový vodoznak do dokumentů Word pomocí
    Aspose.Words pro .NET
  type: TechArticle
- description: Automaticky aplikujte červený diagonální textový vodoznak na každý
    soubor Word generovaný v hromadném procesu pomocí Aspose.Words pro .NET.
  name: Přidejte červený diagonální textový vodoznak do dokumentů Word pomocí Aspose.Words
    pro .NET
  steps:
  - name: Vytvořte složku "GeneratedReports", kam budou uloženy výstupní soubory.
    text: Vytvořte složku "GeneratedReports", kam budou uloženy výstupní soubory.
  - name: Spusťte smyčku, která vygeneruje tři samostatné dokumenty.
    text: Spusťte smyčku, která vygeneruje tři samostatné dokumenty.
  - name: Vytvořte nový prázdný objekt Word dokumentu.
    text: Vytvořte nový prázdný objekt Word dokumentu.
  - name: Použijte DocumentBuilder k zápisu titulní řádky a popisu do dokumentu.
    text: Použijte DocumentBuilder k zápisu titulní řádky a popisu do dokumentu.
  - name: Definujte vzhled vodoznaku, včetně písma, velikosti, barvy a diagonálního
      rozložení.
    text: Definujte vzhled vodoznaku, včetně písma, velikosti, barvy a diagonálního
      rozložení.
  - name: Aplikujte nakonfigurovaný červený diagonální vodoznak s textem "PROTECTED"
      do dokumentu.
    text: Aplikujte nakonfigurovaný červený diagonální vodoznak s textem "PROTECTED"
      do dokumentu.
  - name: Uložte dokument s vodoznakem do složky "GeneratedReports" s unikátním názvem
      souboru.
    text: Uložte dokument s vodoznakem do složky "GeneratedReports" s unikátním názvem
      souboru.
  - name: Uzavřete smyčku po zpracování aktuálního dokumentu.
    text: Uzavřete smyčku po zpracování aktuálního dokumentu.
  type: HowTo
- questions:
  - answer: IsSemitrasparent určuje, zda je vodoznak vykreslen s částečnou neprůhledností;
      nastavení na **true** způsobí, že text bude semi‑průhledný, takže podkladový
      obsah zůstane čitelnější.
    question: Co řídí možnost **IsSemitrasparent** a jaký má nastavení na **true**
      efekt?
  - answer: Ano — nastavte vlastnost **Layout** na **WatermarkLayout.Horizontal**
      v **TextWatermarkOptions** před voláním **document.Watermark.SetText**.
    question: Mohu změnit orientaci vodoznaku na horizontální místo diagonální?
  - answer: Ukázka vytvoří novou instanci **Document**, ale můžete otevřít libovolný
      existující soubor (např. `new Document("Existing.docx")`) a poté zavolat **document.Watermark.SetText**,
      abyste aplikovali stejný vodoznak.
    question: Přidá tento kód vodoznak do existujícího souboru Word, nebo jen do nově
      vytvořených dokumentů?
  - answer: Přiřaďte vlastní barvu pomocí **Color.FromArgb(red, green, blue)** k vlastnosti
      **Color** v **TextWatermarkOptions**, např. `Color = Color.FromArgb(128, 0,
      128)` pro fialovou.
    question: Jak mohu použít vlastní RGB barvu pro vodoznak místo předdefinované
      **Color.Red**?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Přidejte červený diagonální textový vodoznak do dokumentů Word
og_description: Podívejte se, jak automaticky aplikovat červený diagonální vodoznak na každý dokument Word v hromadném procesu s Aspose.Words.
og_image_alt: Průvodce ukazující, jak přidat červený diagonální textový vodoznak do dokumentů Word pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidejte červený diagonální textový vodoznak do dokumentů Word pomocí Aspose.Words pro .NET
Tento tutoriál ukazuje, jak automaticky vložit červený diagonální textový vodoznak do každého dokumentu Word vytvořeného během hromadného generování reportů. Pomocí tříd Document a DocumentBuilder z Aspose.Words pro .NET se vodoznak aplikuje programově při vytváření souborů, což zajišťuje, že každý dokument nese stejné značení nebo upozornění na důvěrnost bez ručního zásahu.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Co řídí možnost **IsSemitrasparent** a jaký má nastavení na **true** efekt?**  
A: IsSemitrasparent určuje, zda je vodoznak vykreslen s částečnou neprůhledností; nastavení na **true** způsobí, že text bude semi‑průhledný, takže podkladový obsah zůstane čitelnější.

**Q: Mohu změnit orientaci vodoznaku na horizontální místo diagonální?**  
A: Ano — nastavte vlastnost **Layout** na **WatermarkLayout.Horizontal** v **TextWatermarkOptions** před voláním **document.Watermark.SetText**.

**Q: Přidá tento kód vodoznak do existujícího souboru Word, nebo jen do nově vytvořených dokumentů?**  
A: Ukázka vytvoří novou instanci **Document**, ale můžete otevřít libovolný existující soubor (např. `new Document("Existing.docx")`) a poté zavolat **document.Watermark.SetText**, abyste aplikovali stejný vodoznak.

**Q: Jak mohu použít vlastní RGB barvu pro vodoznak místo předdefinované **Color.Red**?**  
A: Přiřaďte vlastní barvu pomocí **Color.FromArgb(red, green, blue)** k vlastnosti **Color** v **TextWatermarkOptions**, např. `Color = Color.FromArgb(128, 0, 128)` pro fialovou.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}