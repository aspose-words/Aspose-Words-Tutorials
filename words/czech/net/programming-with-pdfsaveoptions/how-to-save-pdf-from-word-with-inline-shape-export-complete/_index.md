---
category: general
date: 2026-06-02
description: Jak uložit PDF z DOCX pomocí Aspose.Words, exportovat tvary jako inline
  span značky a převést Word do PDF během několika kroků.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: cs
og_description: Jak uložit PDF z dokumentu Word pomocí Aspose.Words, exportovat plovoucí
  tvary jako inline značky span pro čistý výsledek převodu Word do PDF.
og_title: Jak uložit PDF z Wordu – Návod na export vložených tvarů
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Jak uložit PDF z Wordu s exportem vložených tvarů – kompletní průvodce
url: /cs/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak uložit PDF z Wordu s exportem vložených tvarů – Kompletní průvodce

Už jste se někdy zamýšleli **jak uložit PDF** ze souboru Word a přitom zachovat každý plovoucí tvar úhledně vložený do toku? Nejste v tom sami. V mnoha podnikových aplikacích potřebujeme *převést Word do PDF* bez toho, aby se objevily špatně umístěné obrázky nebo roztroušené kresby. Dobrá zpráva? Aspose.Words to usnadňuje a můžete knihovně dokonce říct, aby **exportovala tvary jako inline `<span>` tagy**, takže PDF vypadá přesně jako původní DOCX.

V tomto tutoriálu projdeme celý proces – načtení DOCX, úpravu `PdfSaveOptions` a nakonec uložení čistého PDF. Na konci budete vědět **jak uložit PDF**, **uložit docx jako pdf** a dokonce **jak exportovat tvary** pomocí *inline span tagů*.

## Co budete potřebovat

- **Aspose.Words for .NET** (nejnovější verze, 24.x v době psaní).  
- **.NET 6.0** nebo novější – kód funguje také na .NET Framework 4.7.2, ale .NET 6 je ideální.  
- Jednoduchý Word dokument, který obsahuje alespoň jeden plovoucí tvar (obrázek, textové pole nebo kresba).  
- Jakékoliv IDE, které preferujete (Visual Studio, Rider, VS Code + C# rozšíření).  

To je vše – žádné extra NuGet balíčky, žádné komplikované COM interop. Připravení? Ponořme se.

## Krok 1: Nastavte projekt a přidejte Aspose.Words

Nejprve vytvořte konzolovou aplikaci (nebo integrujte kód do existující služby).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Tip:** Pokud používáte Visual Studio, můžete balíček přidat přes UI NuGet Package Manager – stačí vyhledat *Aspose.Words*.

## Krok 2: Načtěte zdrojový dokument

Jakmile je knihovna referencována, můžeme načíst DOCX. Toto je první konkrétní krok **jak uložit pdf** – načtení zdroje do paměti.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Proč je to důležité:** Načtení souboru ověří, že cesta je správná a že Aspose dokáže parsovat strukturu Wordu. Pokud soubor obsahuje plovoucí tvary, budou součástí stromu uzlů objektu `Document`.

## Krok 3: Nakonfigurujte PDF Save Options – Export tvarů jako inline tagy

Zde je jádro **jak exportovat tvary**. Ve výchozím nastavení Aspose.Words vykresluje plovoucí tvary jako samostatné objekty v PDF, což může posunout rozvržení. Nastavením `ExportFloatingShapesAsInlineTag` na `true` řeknete enginu, aby obalil každý tvar inline `<span>` elementem, čímž zachová tok.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**Proč povolit tento příznak?** Představte si smlouvu s podpisovým polem, které plave nad textem. Když ji převedete do PDF bez tohoto nastavení, pole se může objevit na jiné stránce. Inline `<span>` tagy udrží tvar ukotvený k okolnímu odstavci, čímž vytvoří věrnou vizuální repliku.

## Krok 4: Uložte dokument jako PDF

Nakonec zavoláme `doc.Save` s možnostmi, které jsme právě vytvořili. Toto je okamžik, kdy skutečně **uložíte docx jako pdf**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Spusťte program (`dotnet run`) a zkontrolujte `output.pdf`. Měli byste vidět své plovoucí tvary vykreslené inline, přesně tak, jak se objevily ve Wordu.

## Krok 5: Ověřte výsledek – Rychlý kontrolní seznam

1. **Veškerý text je přítomen** – žádné chybějící odstavce.  
2. **Plovoucí tvary se zobrazují tam, kde mají** – nyní jsou součástí toku textu.  
3. **Velikost PDF je rozumná** – export jako inline tagy obvykle snižuje velikost souboru oproti samostatným obrazovým tokům.  

Pokud něco vypadá špatně, dvakrát zkontrolujte, že zdrojový DOCX skutečně používá *plovoucí* tvary (klik pravým → Rozložení → „V řadě s textem“ vs „Čtverec/Za textem“). Přepnutí tvaru na „V řadě“ před konverzí také funguje, ale možnost inline‑tag vám dává kontrolu bez úpravy původního souboru.

## Okrajové případy a časté otázky

### Co když můj dokument obsahuje **SmartArt** nebo **Grafy**?

SmartArt a grafy jsou považovány za kreslicí objekty. Příznak `ExportFloatingShapesAsInlineTag` je i tak obalí do `<span>` tagů, ale složitá grafika může ztratit část věrnosti. V takových případech zvažte nejprve exportovat graf jako obrázek (`Chart.ToImage()`) a poté jej vložit inline.

### Mohu **zachovat hypertextové odkazy** a **záložky**?

Rozhodně. Tyto prvky nejsou ovlivněny nastavením `ExportFloatingShapesAsInlineTag`. Aspose.Words automaticky zachovává všechny informace o hypertextových odkazech a záložkách.

### Jak mohu **změnit kompresi PDF** nebo **vložit fonty**?

`PdfSaveOptions` nabízí mnoho dalších vlastností:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

## Kompletní funkční příklad (připravený ke zkopírování)

Níže je kompletní program, který můžete zkopírovat do `Program.cs`. Nahraďte `YOUR_DIRECTORY` skutečnou cestou ke složce.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Očekávaný výstup v konzoli:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Otevřete `output.pdf` – uvidíte původní rozvržení, se všemi plovoucími tvary úhledně umístěnými uvnitř textového toku.

## Závěr

Probrali jsme **jak uložit PDF** z Word dokumentu a zajistili, že plovoucí tvary se stanou inline `<span>` tagy. Načtením DOCX, nastavením `PdfSaveOptions` a voláním `doc.Save` můžete spolehlivě **uložit docx jako pdf** a **převést word do pdf** bez překvapení v rozvržení.  

Další kroky? Zkuste kombinovat tento přístup s **PDF/A** kompatibilitou pro archivaci, nebo hromadně zpracovat složku DOCX souborů pomocí jednoduché smyčky `foreach`. Můžete také prozkoumat **vlastní renderování** (např. přidání vodoznaku) využitím API `DocumentVisitor` v Aspose.Words.

Máte další otázky ohledně manipulace s tvary, vkládání fontů nebo ladění výkonu? Zanechte komentář níže a šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak uložit dokument jako pdf s Aspose.Words pro Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Převést Word do PDF s Aspose.Words pro Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Převést DOCX do PDF v Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}