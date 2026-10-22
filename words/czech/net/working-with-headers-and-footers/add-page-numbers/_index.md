---
title: Přidejte čísla stránek do zápatí Word dokumentu pomocí Aspose.Words pro .NET
weight: 210
limit:
description: Přidejte automaticky aktualizující čísla stránek do primárního zápatí Word dokumentu pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Přidejte automaticky aktualizující čísla stránek do primárního zápatí
    Word dokumentu pomocí Aspose.Words pro .NET.
  headline: Přidejte čísla stránek do zápatí Word dokumentu pomocí Aspose.Words pro
    .NET
  type: TechArticle
- description: Přidejte automaticky aktualizující čísla stránek do primárního zápatí
    Word dokumentu pomocí Aspose.Words pro .NET.
  name: Přidejte čísla stránek do zápatí Word dokumentu pomocí Aspose.Words pro .NET
  steps:
  - name: Vytvořte nový objekt Document a DocumentBuilder k němu přiřazený.
    text: Vytvořte nový objekt Document a DocumentBuilder k němu přiřazený.
  - name: Přesuňte kurzor builderu do primárního zápatí první sekce.
    text: Přesuňte kurzor builderu do primárního zápatí první sekce.
  - name: Nastavte zarovnání odstavce na střed, aby byl text v zápatí vycentrován.
    text: Nastavte zarovnání odstavce na střed, aby byl text v zápatí vycentrován.
  - name: Napište popisek "Page " a vložte pole PAGE, které zobrazuje aktuální číslo
      stránky.
    text: Napište popisek "Page " a vložte pole PAGE, které zobrazuje aktuální číslo
      stránky.
  - name: Napište " of " a vložte pole NUMPAGES, které ukazuje celkový počet stránek.
    text: Napište " of " a vložte pole NUMPAGES, které ukazuje celkový počet stránek.
  - name: Uložte dokument do souboru .docx.
    text: Uložte dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: Ne. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` přesune builder
      pouze do primárního zápatí *první* sekce, takže pole jsou vložena jen tam.
    question: Pokud má dokument více než jednu sekci, přidá tento kód čísla stránek
      do zápatí každé sekce?
  - answer: Nastavte `builder.ParagraphFormat.Alignment` na jinou hodnotu `ParagraphAlignment`
      (např. `ParagraphAlignment.Right`) před zápisem polí.
    question: Jak mohu změnit zarovnání odstavce s číslem stránky v zápatí?
  - answer: '`InsertField` přijímá kód pole a volitelný výsledek pole; předání `null`
      říká Aspose.Words, aby nechalo Word vypočítat výsledek za běhu.'
    question: Co představuje argument `null` v `InsertField("PAGE", null)`?
  - answer: Ano — nahraďte `HeaderFooterType.FooterPrimary` za `HeaderFooterType.HeaderPrimary`
      (nebo jiný typ záhlaví) před vložením polí.
    question: Mohu umístit stejná pole "Page X of Y" do záhlaví místo zápatí?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Vložte automatická čísla stránek do zápatí Wordu
og_description: Krok za krokem kód pro přidání živých čísel stránek do zápatí Wordu s Aspose.Words pro .NET.
og_image_alt: Návod ukazující, jak přidat automatická čísla stránek do zápatí Word dokumentu pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidejte čísla stránek do zápatí Word dokumentu pomocí Aspose.Words pro .NET
Tento tutoriál ukazuje, jak použít Aspose.Words Document a DocumentBuilder k vložení automaticky aktualizujících čísel stránek do primárního zápatí Word dokumentu. Přidáním čísel stránek programově zajistíte konzistentní číslování po celém souboru bez ruční úpravy. Ukázkový kód je připraven ke spuštění v .NET prostředí.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Pokud má dokument více než jednu sekci, přidá tento kód čísla stránek do zápatí každé sekce?**  
A: Ne. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` přesune builder pouze do primárního zápatí *první* sekce, takže pole jsou vložena jen tam.

**Q: Jak mohu změnit zarovnání odstavce s číslem stránky v zápatí?**  
A: Nastavte `builder.ParagraphFormat.Alignment` na jinou hodnotu `ParagraphAlignment` (např. `ParagraphAlignment.Right`) před zápisem polí.

**Q: Co představuje argument `null` v `InsertField("PAGE", null)`?**  
A: `InsertField` přijímá kód pole a volitelný výsledek pole; předání `null` říká Aspose.Words, aby nechalo Word vypočítat výsledek za běhu.

**Q: Mohu umístit stejná pole "Page X of Y" do záhlaví místo zápatí?**  
A: Ano — nahraďte `HeaderFooterType.FooterPrimary` za `HeaderFooterType.HeaderPrimary` (nebo jiný typ záhlaví) před vložením polí.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}