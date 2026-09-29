---
title: Vytvořte diagonální textový vodoznak s vlastním písmem v dokumentu Word pomocí Aspose.Words pro .NET
weight: 210
limit:
description: Kód krok za krokem pro přidání diagonálního textového vodoznaku s vlastním písmem do souboru Word .docx pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Kód krok za krokem pro přidání diagonálního textového vodoznaku s vlastním
    písmem do souboru Word .docx pomocí Aspose.Words pro .NET.
  headline: Vytvořte diagonální textový vodoznak s vlastním písmem v dokumentu Word
    pomocí Aspose.Words pro .NET
  type: TechArticle
- description: Kód krok za krokem pro přidání diagonálního textového vodoznaku s vlastním
    písmem do souboru Word .docx pomocí Aspose.Words pro .NET.
  name: Vytvořte diagonální textový vodoznak s vlastním písmem v dokumentu Word pomocí
    Aspose.Words pro .NET
  steps:
  - name: Vytvořte novou prázdnou instanci dokumentu Word pojmenovanou `document`.
    text: Vytvořte novou prázdnou instanci dokumentu Word pojmenovanou `document`.
  - name: Nakonfigurujte `watermarkSettings` s písmem Arial 48 pt šedé barvy, diagonálním
      rozložením a neprůhledným vykreslením.
    text: Nakonfigurujte `watermarkSettings` s písmem Arial 48 pt šedé barvy, diagonálním
      rozložením a neprůhledným vykreslením.
  - name: Aplikujte textový vodoznak „Private“ na `document` pomocí dříve definovaných
      nastavení.
    text: Aplikujte textový vodoznak „Private“ na `document` pomocí dříve definovaných
      nastavení.
  - name: Definujte cestu k souboru, kam bude vodoznakovaný dokument uložen.
    text: Definujte cestu k souboru, kam bude vodoznakovaný dokument uložen.
  - name: Uložte upravený `document` na zadanou cestu jako soubor .docx.
    text: Uložte upravený `document` na zadanou cestu jako soubor .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` určuje, zda je vodoznak vykreslen s částečnou průhledností;
      nastavení na `false` způsobí, že je vodoznak zcela neprůhledný, zatímco `true`
      použije výchozí poloprůhledný efekt.'
    question: Co řídí příznak **IsSemitrasparent** v `TextWatermarkOptions`?
  - answer: Ano — nastavte vlastnost `Layout` na `WatermarkLayout.Horizontal` (nebo
      jinou hodnotu výčtu) před voláním `document.Watermark.SetText`.
    question: Mohu změnit orientaci vodoznaku na horizontální místo diagonální?
  - answer: Word použije jako náhradní výchozí písmo pro vodoznak, takže text se stále
      zobrazí, ale může vypadat jinak než zamýšlený styl.
    question: Co se stane, pokud není na cílovém počítači nainstalována zadaná `FontFamily`
      (např. "Arial")?
  - answer: Načtěte existující soubor pomocí `Document document = new Document(\"Existing.docx\");`,
      poté nakonfigurujte `TextWatermarkOptions` a zavolejte `document.Watermark.SetText`
      podle ukázky.
    question: Je možné přidat vodoznak do existujícího souboru `.docx` místo vytvoření
      nového?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Přidejte diagonální textový vodoznak s vlastním písmem
og_description: Naučte se během několika minut vložit šikmý textový vodoznak s vlastním písmem do souboru Word.
og_image_alt: Průvodce ukazující, jak přidat diagonální textový vodoznak s vlastním písmem do dokumentu Word pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte diagonální textový vodoznak s vlastním písmem v dokumentu Word pomocí Aspose.Words pro .NET
Tento tutoriál vás provede vytvořením nového dokumentu Word, nastavením diagonálního textového vodoznaku s vámi zvolenými nastaveními písma, jeho aplikací pomocí API Document.Watermark.SetText a uložením výsledku jako soubor .docx. Na konci budete mít profesionálně vodoznakovaný dokument, který prezentuje vaši značku nebo vlastnictví. Krok‑za‑krokem připravený kód je připraven ke zkopírování do libovolného projektu .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: Co řídí příznak **IsSemitrasparent** v `TextWatermarkOptions`?**  
A: `IsSemitrasparent` určuje, zda je vodoznak vykreslen s částečnou průhledností; nastavení na `false` způsobí, že je vodoznak zcela neprůhledný, zatímco `true` použije výchozí poloprůhledný efekt.

**Q: Mohu změnit orientaci vodoznaku na horizontální místo diagonální?**  
A: Ano — nastavte vlastnost `Layout` na `WatermarkLayout.Horizontal` (nebo jinou hodnotu výčtu) před voláním `document.Watermark.SetText`.

**Q: Co se stane, pokud není na cílovém počítači nainstalována zadaná `FontFamily` (např. "Arial")?**  
A: Word použije jako náhradní výchozí písmo pro vodoznak, takže text se stále zobrazí, ale může vypadat jinak než zamýšlený styl.

**Q: Je možné přidat vodoznak do existujícího souboru `.docx` místo vytvoření nového?**  
A: Načtěte existující soubor pomocí `Document document = new Document(\"Existing.docx\");`, poté nakonfigurujte `TextWatermarkOptions` a zavolejte `document.Watermark.SetText` podle ukázky.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}