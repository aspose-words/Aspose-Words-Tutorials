---
title: Nahraďte data čárového kódu v dokumentech Word pomocí Aspose.Words pro .NET
weight: 110
limit:
description: Naučte se, jak vložit pole DISPLAYBARCODE a nahradit jeho datový řetězec pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, barcode field, replace barcode data, Document.Range.Replace, DISPLAYBARCODE, Word barcode update]
url: /net/working-with-fields/replace-barcode-data/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Naučte se, jak vložit pole DISPLAYBARCODE a nahradit jeho datový řetězec
    pomocí Aspose.Words pro .NET.
  headline: Nahraďte data čárového kódu v dokumentech Word pomocí Aspose.Words pro
    .NET
  type: TechArticle
- description: Naučte se, jak vložit pole DISPLAYBARCODE a nahradit jeho datový řetězec
    pomocí Aspose.Words pro .NET.
  name: Nahraďte data čárového kódu v dokumentech Word pomocí Aspose.Words pro .NET
  steps:
  - name: Vytvořte nový objekt Document a DocumentBuilder pro vytvoření jeho obsahu.
    text: Vytvořte nový objekt Document a DocumentBuilder pro vytvoření jeho obsahu.
  - name: Vložte pole DISPLAYBARCODE a nastavte jeho typ, počáteční hodnotu a start/stop
      znaky, poté přidejte zalomení řádku.
    text: Vložte pole DISPLAYBARCODE a nastavte jeho typ, počáteční hodnotu a start/stop
      znaky, poté přidejte zalomení řádku.
  - name: Zavolejte UpdateFields pro vykreslení nově vloženého pole čárového kódu.
    text: Zavolejte UpdateFields pro vykreslení nově vloženého pole čárového kódu.
  - name: Použijte engine Find/Replace k změně datového řetězce čárového kódu z INIT123
      na NEWVAL.
    text: Použijte engine Find/Replace k změně datového řetězce čárového kódu z INIT123
      na NEWVAL.
  - name: Znovu aktualizujte pole, aby DISPLAYBARCODE odráželo nový datový řetězec.
    text: Znovu aktualizujte pole, aby DISPLAYBARCODE odráželo nový datový řetězec.
  - name: Uložte dokument do souboru .docx.
    text: Uložte dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: '`Range.Replace` mění pouze podkladový text; vizuální výsledek pole DISPLAYBARCODE
      se znovu vygeneruje až po zavolání `UpdateFields()`, takže nový čárový kód se
      objeví v uloženém dokumentu.'
    question: Proč potřebuji po provedení `Range.Replace` zavolat `myDocument.UpdateFields()`?
  - answer: Ano, `Document.Range.Replace` pracuje na celém rozsahu dokumentu, takže
      veškerý odpovídající text jinde bude nahrazen, pokud neomezíte hledání pomocí
      `FindReplaceOptions` (např. nastavením konkrétního `Range` nebo použitím `.MatchWholeWord`).
    question: Ovlivní volání `Replace(\"INIT123\", \"NEWVAL\", ...)` i jiné výskyty
      \"INIT123\" mimo pole čárového kódu?
  - answer: Můžete kdykoli přiřadit novou hodnotu do `displayBarcode.BarcodeType`,
      ale poté musíte zavolat `myDocument.UpdateFields()`, aby se změna projevila
      v vykresleném čárovém kódu.
    question: Mohu po vložení pole změnit typ čárového kódu (např. z CODE39 na QR)?
  - answer: Když je `AddStartStopChar` nastaven na true, Aspose.Words automaticky
      přidá požadované start/stop znaky (`*`) kolem hodnoty čárového kódu, což CODE39
      vyžaduje; nastavte jej na false, pokud vaše symbologie tyto znaky nepotřebuje.
    question: Co dělá vlastnost `AddStartStopChar = true` u čárových kódů CODE39?
  - answer: Pro jednoduchou přesnou shodu nejsou vyžadována žádná speciální nastavení,
      ale můžete v `FindReplaceOptions` povolit `.MatchCase` nebo `.MatchWholeWord`,
      abyste předešli neúmyslným částečným náhradám.
    question: Musím v `FindReplaceOptions` nastavit nějaké speciální možnosti pro
      bezpečnou náhradu hodnoty čárového kódu?
  type: FAQPage
images:
- /net/working-with-fields/replace-barcode-data/og-image.png
og_title: Aktualizujte pole čárového kódu ve Wordu pomocí Aspose.Words
og_description: Vyměňte datový řetězec čárového kódu a okamžitě jej obnovte v souboru Word.
og_image_alt: Snímek obrazovky zobrazující dokument Word s polem DISPLAYBARCODE před a po nahrazení dat pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nahraďte data čárového kódu v dokumentech Word pomocí Aspose.Words pro .NET
Tento tutoriál demonstruje, jak vložit pole DISPLAYBARCODE do dokumentu Word a poté použít metodu Document.Range.Replace k změně datového řetězce čárového kódu. Po nahrazení je pole obnoveno, aby se aktualizovaný čárový kód objevil v uloženém souboru. Postupujte podle kroků a uvidíte okamžitou aktualizaci čárového kódu, aniž byste pole znovu vytvářeli.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/replace-barcode-data" >}}


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

**Q: Proč potřebuji po provedení `Range.Replace` zavolat `myDocument.UpdateFields()`?**  
A: `Range.Replace` mění pouze podkladový text; vizuální výsledek pole DISPLAYBARCODE se znovu vygeneruje až po zavolání `UpdateFields()`, takže nový čárový kód se objeví v uloženém dokumentu.

**Q: Ovlivní volání `Replace(\"INIT123\", \"NEWVAL\", ...)` i jiné výskyty \"INIT123\" mimo pole čárového kódu?**  
A: Ano, `Document.Range.Replace` pracuje na celém rozsahu dokumentu, takže veškerý odpovídající text jinde bude nahrazen, pokud neomezíte hledání pomocí `FindReplaceOptions` (např. nastavením konkrétního `Range` nebo použitím `.MatchWholeWord`).

**Q: Mohu po vložení pole změnit typ čárového kódu (např. z CODE39 na QR)?**  
A: Můžete kdykoli přiřadit novou hodnotu do `displayBarcode.BarcodeType`, ale poté musíte zavolat `myDocument.UpdateFields()`, aby se změna projevila v vykresleném čárovém kódu.

**Q: Co dělá vlastnost `AddStartStopChar = true` u čárových kódů CODE39?**  
A: Když je `AddStartStopChar` nastaven na true, Aspose.Words automaticky přidá požadované start/stop znaky (`*`) kolem hodnoty čárového kódu, což CODE39 vyžaduje; nastavte jej na false, pokud vaše symbologie tyto znaky nepotřebuje.

**Q: Musím v `FindReplaceOptions` nastavit nějaké speciální možnosti pro bezpečnou náhradu hodnoty čárového kódu?**  
A: Pro jednoduchou přesnou shodu nejsou vyžadována žádná speciální nastavení, ale můžete v `FindReplaceOptions` povolit `.MatchCase` nebo `.MatchWholeWord`, abyste předešli neúmyslným částečným náhradám.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}