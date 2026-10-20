---
title: Vložení dynamického data do záhlaví v dokumentu Word pomocí Aspose.Words pro .NET
weight: 110
limit:
description: Naučte se, jak přidat dynamické pole DATE do primárního záhlaví dokumentu Word pomocí Aspose.Words pro .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Naučte se, jak přidat dynamické pole DATE do primárního záhlaví dokumentu
    Word pomocí Aspose.Words pro .NET.
  headline: Vložení dynamického data do záhlaví v dokumentu Word pomocí Aspose.Words
    pro .NET
  type: TechArticle
- description: Naučte se, jak přidat dynamické pole DATE do primárního záhlaví dokumentu
    Word pomocí Aspose.Words pro .NET.
  name: Vložení dynamického data do záhlaví v dokumentu Word pomocí Aspose.Words pro
    .NET
  steps:
  - name: Vytvořte nový Document a DocumentBuilder pro jeho úpravu.
    text: Vytvořte nový Document a DocumentBuilder pro jeho úpravu.
  - name: Přesuňte kurzor builderu do primárního záhlaví, aby následné vložení ovlivnilo
      záhlaví.
    text: Přesuňte kurzor builderu do primárního záhlaví, aby následné vložení ovlivnilo
      záhlaví.
  - name: Napište statický popisek a vložte pole DATE formátované jako „MMMM d, yyyy“
      do záhlaví, čímž vytvoříte dynamické datum.
    text: Napište statický popisek a vložte pole DATE formátované jako „MMMM d, yyyy“
      do záhlaví, čímž vytvoříte dynamické datum.
  - name: Vraťte se do hlavního těla dokumentu a přidejte ukázkový odstavec, který
      demonstruje běžný obsah dokumentu vedle záhlaví.
    text: Vraťte se do hlavního těla dokumentu a přidejte ukázkový odstavec, který
      demonstruje běžný obsah dokumentu vedle záhlaví.
  - name: Uložte dokument do souboru .docx.
    text: Uložte dokument do souboru .docx.
  type: HowTo
- questions:
  - answer: Volání `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` umístí builder
      na existující primární záhlaví a `Write`/`InsertField` jen přidají text k tomu,
      co už je; neodstraňují existující obsah.
    question: Co se stane, pokud dokument již má primární záhlaví – přepíše můj kód
      toto záhlaví?
  - answer: Ano – upravte formát přepínače ve kódu pole předaném do `InsertField`,
      např. `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\"")` vytvoří datum jako
      2026-09-22.
    question: Mohu změnit formát data používaný polem DATE a jak?
  - answer: Nahraďte `HeaderFooterType.HeaderPrimary` za `HeaderFooterType.HeaderFirst`
      při volání `MoveToHeaderFooter`; zbytek kódu funguje stejně.
    question: Pokud potřebuji pole datum v záhlaví první stránky místo primárního
      záhlaví, co mám udělat?
  - answer: Pole je vloženo pouze s přepínačem `\\@`, který říká Wordu, aby při každém
      obnovení pole (např. při otevření souboru nebo po stisknutí Ctrl+Alt+F9) zobrazil
      aktuální datum.
    question: Automaticky se pole DATE aktualizuje, když je dokument později otevřen?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Přidejte dynamické datum do záhlaví Wordu
og_description: Průvodce krok za krokem, jak vložit živé datumové pole do záhlaví Wordu pomocí Aspose.Words.
og_image_alt: Snímek obrazovky ukazující, jak vložit dynamické pole DATE do záhlaví dokumentu Word pomocí Aspose.Words pro .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení dynamického data do záhlaví v dokumentu Word pomocí Aspose.Words pro .NET
Cílem tohoto tutoriálu je ukázat, jak použít třídy Document a DocumentBuilder v Aspose.Words pro .NET k vložení dynamického pole DATE do primárního záhlaví dokumentu Word. Přidané pole se automaticky aktualizuje na aktuální datum při každém otevření dokumentu, což zajišťuje, že záhlaví vždy zobrazuje nejnovější datum. Postupujte podle krok‑za‑krokem kódu a přidejte pole a uložte aktualizovaný soubor.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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

**Q: Co se stane, pokud dokument již má primární záhlaví – přepíše můj kód toto záhlaví?**  
A: Volání `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` umístí builder na existující primární záhlaví a `Write`/`InsertField` jen přidají text k tomu, co už je; neodstraňují existující obsah.

**Q: Mohu změnit formát data používaný polem DATE a jak?**  
A: Ano – upravte formát přepínače ve kódu pole předaném do `InsertField`, např. `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\"")` vytvoří datum jako 2026-09-22.

**Q: Pokud potřebuji pole datum v záhlaví první stránky místo primárního záhlaví, co mám udělat?**  
A: Nahraďte `HeaderFooterType.HeaderPrimary` za `HeaderFooterType.HeaderFirst` při volání `MoveToHeaderFooter`; zbytek kódu funguje stejně.

**Q: Automaticky se pole DATE aktualizuje, když je dokument později otevřen?**  
A: Pole je vloženo pouze s přepínačem `\\@`, který říká Wordu, aby při každém obnovení pole (např. při otevření souboru nebo po stisknutí Ctrl+Alt+F9) zobrazil aktuální datum.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}