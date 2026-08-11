---
category: general
date: 2026-08-10
description: Formátujte oddělovač poznámky pod čarou v C# pomocí Aspose.Words a přizpůsobte
  řádky poznámek pod čarou i koncových poznámek. Naučte se formátování poznámek pod
  čarou v C# během několika minut.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: cs
lastmod: 2026-08-10
og_description: Formátovat oddělovač poznámky pod čarou v C# pomocí Aspose.Words.
  Postupujte podle tohoto tutoriálu a rychle a spolehlivě stylizujte oddělovače poznámek
  pod čarou i koncových poznámek.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Formát oddělovače poznámky pod čarou v C# – kompletní průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Formátovat oddělovač poznámky pod čarou v C# pomocí Aspose.Words
url: /cs/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formátování oddělovače poznámky pod čarou v C# pomocí Aspose.Words

Pokud potřebujete **formátovat oddělovač poznámky pod čarou** ve Word dokumentu, tento průvodce vám ukáže, jak to provést pomocí Aspose.Words pro .NET. Uvidíte kompletní, spustitelný příklad, který mění zarovnání a barvu odstavce oddělovače, a naučíte se, jak použít stejnou techniku i na oddělovače koncových poznámek.

Tutoriál pokrývá každý krok — od načtení zdrojového souboru po uložení upraveného dokumentu — takže můžete kód zkopírovat a vložit do svého projektu bez dalšího výzkumu.

## Co budete potřebovat

* .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
* Platná licence Aspose.Words pro .NET (bezplatná zkušební verze funguje pro hodnocení)
* Soubor Word, který obsahuje alespoň jednu poznámku pod čarou nebo koncovou poznámku (např. `Footnotes.docx`)
* Visual Studio 2022 nebo jakékoli C# IDE, které preferujete

Mít tyto položky připravené vám umožní soustředit se na logiku **formátování poznámek pod čarou v C#** místo nastavení prostředí.

## Krok 1: Načtení dokumentu, který obsahuje poznámky pod čarou a koncové poznámky

Prvním krokem je vytvořit objekt `Document`, který ukazuje na váš zdrojový soubor. Aspose.Words načte celý balíček DOCX do paměti a poskytne vám plný přístup k uzlům poznámek pod čarou a koncových poznámek.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Proč je to důležité*: Načtení dokumentu je předpokladem pro jakoukoli manipulaci. Pokud je cesta k souboru špatná, Aspose.Words vyhodí `FileNotFoundException`, takže před pokračováním ověřte cestu.

## Krok 2: Získání uzlů oddělovače a pokračovacího‑oddělovače

Oddělovače poznámek pod čarou a koncových poznámek jsou uloženy jako speciální uzly uvnitř kolekcí `Footnotes` a `Endnotes`. Každá kolekce poskytuje vlastnosti `Separator` a `ContinuationSeparator`, které vrací referenci na `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Proč je to důležité*: Uzlu `Separator` představuje čáru, která vizuálně odděluje hlavní text od bloku poznámky pod čarou. Získáním reference můžete upravit formát odstavce, písmo nebo dokonce uzel úplně nahradit.

## Krok 3: Změna vizuálního stylu oddělovače poznámky pod čarou

Ve většině Word dokumentů je oddělovač jediný odstavec, který obsahuje pomlčku nebo hvězdičku. Níže uvedený kód kontroluje, zda je oddělovač typu `Paragraph`, a pokud ano, zarovná jej na střed a změní barvu textu na šedou.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Stylování pokračovacího oddělovače (volitelné)

Pokračovací oddělovač se objeví, když poznámka pod čarou přesahuje více stránek. Můžete jej stylovat podobně:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Proč je to důležité*: Zarovnání oddělovače zlepšuje čitelnost a změna barvy jej odlišuje od běžného textu odstavce. Můžete nahradit `ParagraphAlignment.Center` hodnotou `Left` nebo `Right`, aby odpovídalo designovým směrnicím vašeho dokumentu.

## Krok 4: Uložení upraveného dokumentu

Po aplikaci požadovaného stylu zapište dokument zpět na disk. Můžete přepsat původní soubor nebo vytvořit novou verzi.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Když otevřete `Footnotes_Styled.docx` v Microsoft Word, oddělovač poznámky pod čarou se zobrazí zarovnaný na střed a šedý, přesně tak, jak je uvedeno v kódu.

## Pokročilé varianty

### Formátování oddělovače koncové poznámky

Pokud váš dokument také používá koncové poznámky, můžete použít stejnou logiku na kolekci `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Použití vlastního řetězce pro oddělovač

Někdy chcete, aby oddělovač byl řada hvězdiček (`***`). Nahraďte existující běhy (runs) novým během:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Zpracování dokumentů bez uzlu oddělovače

Zřídka se může stát, že dokument neobsahuje uzel oddělovače (např. když jej autor smazal). V takovém případě `document.Footnotes.Separator` vrací `null`. Ošetřete to:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Časté úskalí a jak se jim vyhnout

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Oddělovač není `Paragraph`** | Některé šablony Word používají jako oddělovač `Table` nebo `Shape`. | Zkontrolujte typ uzlu pomocí `is Paragraph` před přetypováním. |
| **Kolekce `Runs` je prázdná** | Oddělovač může být prázdný odstavec. | Ověřte `Runs.Count > 0` před přístupem k `Runs[0]`. |
| **Licence není použita** | Bez licence Aspose.Words vloží vodoznak a může omezit používání API. | Zavolejte `License license = new License(); license.SetLicense("Aspose.Words.lic");` na začátku vašeho programu. |
| **Ukládání do složky jen pro čtení** | Metoda `Save` vyhodí `UnauthorizedAccessException`. | Ujistěte se, že cílový adresář má oprávnění k zápisu. |

Řešení těchto problémů včas zabraňuje výjimkám za běhu a zajišťuje plynulý zážitek při **úpravě oddělovače poznámky pod čarou**.

## Kompletní, spustitelný příklad

Níže je samostatná konzolová aplikace, která demonstruje každý krok zmíněný výše. Zkopírujte kód do nového .NET konzolového projektu, nahraďte cesty k souborům a spusťte jej.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Očekávaný výsledek**  

Když otevřete `Footnotes_Styled.docx`:

* Čára oddělovače poznámky pod čarou je zarovnaná na střed pod hlavním textem.
* Její barva je světle šedá, což ji vizuálně odlišuje.
* Pokud dokument obsahuje koncové poznámky, jejich oddělovače jsou také zarovnané na střed a zbarvené šedě (nebo slátově

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Zpracování textu s poznámkou pod čarou a koncovou poznámkou](/words/english/net/working-with-footnote-and-endnote/)
- [Nastavení pozice poznámky pod čarou a koncové poznámky](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Práce s poznámkou pod čarou a koncovou poznámkou](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}