---
title: Vložení čárového kódu DataMatrix do dokumentu Word pomocí Aspose.Words pro .NET
weight: 210
limit:
description: Přidejte čárový kód DataMatrix do dokumentu Word programově pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Přidejte čárový kód DataMatrix do dokumentu Word programově pomocí
    Aspose.Words pro .NET.
  headline: Vložení čárového kódu DataMatrix do dokumentu Word pomocí Aspose.Words
    pro .NET
  type: TechArticle
- description: Přidejte čárový kód DataMatrix do dokumentu Word programově pomocí
    Aspose.Words pro .NET.
  name: Vložení čárového kódu DataMatrix do dokumentu Word pomocí Aspose.Words pro
    .NET
  steps:
  - name: Vytvořte nový prázdný dokument Word a DocumentBuilder pro jeho úpravu.
    text: Vytvořte nový prázdný dokument Word a DocumentBuilder pro jeho úpravu.
  - name: Vložte pole DISPLAYBARCODE na aktuální pozici kurzoru, čímž se do dokumentu
      přidá zástupce pole.
    text: Vložte pole DISPLAYBARCODE na aktuální pozici kurzoru, čímž se do dokumentu
      přidá zástupce pole.
  - name: Nastavte vlastnost BarcodeType pole na DataMatrix a zadejte řetězec dat
      k zakódování.
    text: Nastavte vlastnost BarcodeType pole na DataMatrix a zadejte řetězec dat
      k zakódování.
  - name: Volitelně definujte barvy pozadí a popředí čárového kódu.
    text: Volitelně definujte barvy pozadí a popředí čárového kódu.
  - name: Zavolejte na dokumentu metodu UpdateFields, aby se v poli vykreslil obrázek
      čárového kódu.
    text: Zavolejte na dokumentu metodu UpdateFields, aby se v poli vykreslil obrázek
      čárového kódu.
  - name: Uložte dokument do souboru .docx.
    text: Uložte dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: Pole bude vloženo, ale `document.UpdateFields()` nechá čárový kód prázdný
      a Aspose.Words vyhodí `FieldException`, která naznačuje neplatný typ čárového
      kódu.
    question: Co se stane, když přiřadím nepodporovanou hodnotu k `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` vykresluje obrázky čárových kódů, takže můžete vložit
      více objektů `FieldDisplayBarcode` a na konci zavolat `document.UpdateFields()`
      jednou, aby se všechny vykreslily.'
    question: Musím volat `document.UpdateFields()` po každém vložení čárového kódu,
      nebo mohu aktualizovat jednou po přidání všech polí?
  - answer: Obě vlastnosti očekávají hexadecimální řetězec RGB s předponou `0x` (např.
      "0xFF0000" pro červenou); jakýkoli jiný formát bude ignorován a použijí se výchozí
      barvy.
    question: V jakém formátu mají být řetězce barev pro `BackgroundColor` a `ForegroundColor`?
  - answer: Ano – stačí nastavit `displayBarcodeField.BarcodeValue` na nový řetězec
      a znovu zavolat `document.UpdateFields()`, aby se obrázek aktualizoval.
    question: Mohu změnit obsah čárového kódu po vložení pole?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Vložte čárový kód DataMatrix pomocí Aspose.Words
og_description: Naučte se, jak přidat čárový kód DataMatrix do souboru Word během několika řádků kódu .NET.
og_image_alt: Průvodce ukazující, jak vložit a vykreslit čárový kód DataMatrix v dokumentu Word pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení čárového kódu DataMatrix do dokumentu Word pomocí Aspose.Words pro .NET
S Aspose.Words pro .NET můžete programově přidat čárový kód DataMatrix do dokumentu Word. Tento tutoriál ukazuje, jak vytvořit nový dokument, vložit pole DISPLAYBARCODE, nastavit jeho typ na DataMatrix a vykreslit obrázek čárového kódu pomocí tříd Document a DocumentBuilder. Postupujte podle kroků a vytvořte tisknutelný čárový kód přímo ve vašem souboru .docx.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: Co se stane, když přiřadím nepodporovanou hodnotu k `displayBarcodeField.BarcodeType`?**  
A: Pole bude vloženo, ale `document.UpdateFields()` nechá čárový kód prázdný a Aspose.Words vyhodí `FieldException`, která naznačuje neplatný typ čárového kódu.

**Q: Musím volat `document.UpdateFields()` po každém vložení čárového kódu, nebo mohu aktualizovat jednou po přidání všech polí?**  
A: `UpdateFields()` vykresluje obrázky čárových kódů, takže můžete vložit více objektů `FieldDisplayBarcode` a na konci zavolat `document.UpdateFields()` jednou, aby se všechny vykreslily.

**Q: V jakém formátu mají být řetězce barev pro `BackgroundColor` a `ForegroundColor`?**  
A: Obě vlastnosti očekávají hexadecimální řetězec RGB s předponou `0x` (např. "0xFF0000" pro červenou); jakýkoli jiný formát bude ignorován a použijí se výchozí barvy.

**Q: Mohu změnit obsah čárového kódu po vložení pole?**  
A: Ano – stačí nastavit `displayBarcodeField.BarcodeValue` na nový řetězec a znovu zavolat `document.UpdateFields()`, aby se obrázek aktualizoval.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}