---
title: Přidejte Hyperlink Comment a exportujte jako PDF anotaci pomocí Aspose.Words pro .NET
weight: 110
limit:
description: Naučte se přidat hypertextový odkaz do komentáře v souboru Word a exportovat jej jako PDF anotaci pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Naučte se přidat hypertextový odkaz do komentáře v souboru Word a exportovat
    jej jako PDF anotaci pomocí Aspose.Words pro .NET.
  headline: Přidejte Hyperlink Comment a exportujte jako PDF anotaci pomocí Aspose.Words
    pro .NET
  type: TechArticle
- description: Naučte se přidat hypertextový odkaz do komentáře v souboru Word a exportovat
    jej jako PDF anotaci pomocí Aspose.Words pro .NET.
  name: Přidejte Hyperlink Comment a exportujte jako PDF anotaci pomocí Aspose.Words
    pro .NET
  steps:
  - name: Vytvořte nový prázdný objekt Document a DocumentBuilder, se kterým budete
      pracovat.
    text: Vytvořte nový prázdný objekt Document a DocumentBuilder, se kterým budete
      pracovat.
  - name: Napište řádek viditelného textu, který bude hostit nadcházející komentář.
    text: Napište řádek viditelného textu, který bude hostit nadcházející komentář.
  - name: Vytvořte Comment od autora Jane Doe a připojte jej k prvnímu odstavci dokumentu.
    text: Vytvořte Comment od autora Jane Doe a připojte jej k prvnímu odstavci dokumentu.
  - name: Uvnitř komentáře přidejte odstavec a vložte modrý podtržený hypertextový
      odkaz na web Aspose.Words Library.
    text: Uvnitř komentáře přidejte odstavec a vložte modrý podtržený hypertextový
      odkaz na web Aspose.Words Library.
  - name: Nastavte dokument tak, aby vykresloval komentáře jako anotace PDF, a obnovte
      rozvržení.
    text: Nastavte dokument tak, aby vykresloval komentáře jako anotace PDF, a obnovte
      rozvržení.
  - name: Vytvořte složku "Output" v aktuálním adresáři pro uložení vygenerovaného
      PDF.
    text: Vytvořte složku "Output" v aktuálním adresáři pro uložení vygenerovaného
      PDF.
  - name: Uložte připravený dokument jako PDF soubor pomocí PdfSaveOptions.
    text: Uložte připravený dokument jako PDF soubor pomocí PdfSaveOptions.
  - name: Zkontrolujte, že PDF soubor existuje a obsahuje data, a poté výsledek vypište
      do konzole.
    text: Zkontrolujte, že PDF soubor existuje a obsahuje data, a poté výsledek vypište
      do konzole.
  type: HowTo
- questions:
  - answer: Třetí parametr metody `InsertHyperlink` určuje, zda má být odkaz považován
      za pole; nastavením na `false` vloží prostý hypertextový odkaz, který funguje
      v PDF anotaci bez potřeby kódu pole.
    question: Co řídí třetí argument (`false`) v metodě `InsertHyperlink`?
  - answer: Nastavte `myDocument.LayoutOptions.CommentDisplayMode` na `CommentDisplayMode.ShowInBalloons`
      před voláním `Save`; PDF pak bude obsahovat komentář jako běžný Word komentář
      místo anotace.
    question: Jak mohu zobrazit komentář jako bublinu v dokumentu Word místo PDF anotace?
  - answer: Ano — každý `Comment`, který přidáte k odstavci, může obsahovat vlastní
      volání `InsertHyperlink`, a všechny hypertextové odkazy budou při uložení dokumentu
      zachovány jako samostatné PDF anotace.
    question: Pokud přidám více než jeden komentář, bude každý hypertextový odkaz
      fungovat v exportovaném PDF?
  - answer: Otevřete vygenerované PDF, najděte anotaci komentáře (obvykle zobrazenou
      jako ikona poznámky), klikněte na ni pro zobrazení textu komentáře a poté klikněte
      na modrý podtržený odkaz; měl by otevřít cílovou URL v webovém prohlížeči.
    question: Jak ověřím, že hypertextový odkaz uvnitř komentáře skutečně funguje
      po vygenerování PDF?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Vložit Hyperlink Comment a exportovat do PDF
og_description: Naučte se vložit klikací odkaz do komentáře ve Wordu a převést jej na PDF anotaci.
og_image_alt: Průvodce ukazující, jak přidat komentář s klikacím hypertextovým odkazem do dokumentu Word a exportovat jej jako PDF anotaci pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidejte Hyperlink Comment a exportujte jako PDF anotaci pomocí Aspose.Words pro .NET
V tomto tutoriálu uvidíte, jak vytvořit dokument Word, vložit komentář obsahující klikací hypertextový odkaz na externí webovou stránku, nastavit, aby se tento komentář zobrazoval jako anotace PDF, exportovat dokument do PDF a ověřit výsledný PDF soubor. Krok‑za‑krokem kód vám umožní přidat bohaté, na odkazy připravené komentáře a zachovat je při převodu do PDF, což usnadňuje sdílení interaktivních poznámek s čtenáři.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: Co řídí třetí argument (`false`) v metodě `InsertHyperlink`?**  
A: Třetí parametr metody `InsertHyperlink` určuje, zda má být odkaz považován za pole; nastavením na `false` vloží prostý hypertextový odkaz, který funguje v PDF anotaci bez potřeby kódu pole.

**Q: Jak mohu zobrazit komentář jako bublinu v dokumentu Word místo PDF anotace?**  
A: Nastavte `myDocument.LayoutOptions.CommentDisplayMode` na `CommentDisplayMode.ShowInBalloons` před voláním `Save`; PDF pak bude obsahovat komentář jako běžný Word komentář místo anotace.

**Q: Pokud přidám více než jeden komentář, bude každý hypertextový odkaz fungovat v exportovaném PDF?**  
A: Ano — každý `Comment`, který přidáte k odstavci, může obsahovat vlastní volání `InsertHyperlink`, a všechny hypertextové odkazy budou při uložení dokumentu zachovány jako samostatné PDF anotace.

**Q: Jak ověřím, že hypertextový odkaz uvnitř komentáře skutečně funguje po vygenerování PDF?**  
A: Otevřete vygenerované PDF, najděte anotaci komentáře (obvykle zobrazenou jako ikona poznámky), klikněte na ni pro zobrazení textu komentáře a poté klikněte na modrý podtržený odkaz; měl by otevřít cílovou URL v webovém prohlížeči.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}