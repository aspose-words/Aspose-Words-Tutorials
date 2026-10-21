---
category: general
date: 2026-08-07
description: Získejte oddělovač poznámky pod čarou pomocí Aspose.Words pro .NET. Naučte
  se, jak extrahovat oddělovače poznámek pod čarou a koncových poznámek, kontrolovat
  typy uzlů a upravovat je v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: cs
lastmod: 2026-08-07
og_description: Získat oddělovač poznámky pod čarou pomocí Aspose.Words pro .NET.
  Tento průvodce ukazuje, jak extrahovat oddělovače poznámek pod čarou a koncových
  poznámek, zkontrolovat jejich typy uzlů a uložit změny.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: Získat oddělovač poznámky pod čarou v C# – krok za krokem tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: Získání oddělovače poznámky pod čarou v C# – kompletní průvodce Aspose.Words
url: /cs/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Získání oddělovače poznámky pod čarou v C# – kompletní průvodce Aspose.Words

Pokud potřebujete **retrieve footnote separator** z dokumentu Word, tento tutoriál vám přesně ukáže, jak to provést pomocí Aspose.Words pro .NET. Ať už vytváříte službu pro zpracování dokumentů nebo čistíte formátování poznámek pod čarou, uvidíte kompletní, spustitelný příklad, který extrahuje jak oddělovače poznámek pod čarou, tak koncových poznámek.

V tomto průvodci se naučíte, jak načíst soubor `.docx`, zavolat vlastnosti `FootnoteSeparator` a `EndnoteSeparator`, prozkoumat vrácené objekty `Node` a případně nahradit čáru oddělovače. Není potřeba žádná externí dokumentace – vše, co potřebujete, je uvedeno níže.

## Požadavky

* .NET 6.0 nebo novější (kód také funguje na .NET Framework 4.7.2)
* NuGet balíček Aspose.Words pro .NET (verze 24.9 nebo novější)
* Dokument Word, který obsahuje poznámky pod čarou a/nebo koncové poznámky (např. `Footnotes.docx`)

Balíček Aspose.Words můžete přidat pomocí následujícího příkazu CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte nový konzolový projekt nebo přidejte kód do existujícího. Požadované `using` direktivy jsou uvedeny níže.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Tyto jmenné prostory vám poskytují přístup ke třídě `Document`, hierarchii `Node` a výčtu `NodeType`, které jsou potřebné pro operace **retrieve footnote separator**.

## Krok 2: Načtení dokumentu, který obsahuje poznámky pod čarou a koncové poznámky

První operací v jakémkoli workflow Aspose.Words je načtení zdrojového souboru. Nahraďte zástupnou cestu skutečnou polohou vašeho souboru `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Načtení souboru připraví interní strom uzlů, což je nezbytné pro **retrieve footnote separator**, protože uzly oddělovače jsou součástí tohoto stromu.

## Krok 3: Získání uzlu oddělovače poznámky pod čarou

Nyní můžete **retrieve footnote separator** získat přístupem k vlastnosti `FootnoteSeparator` objektu `Document`. Tento uzel představuje čáru, která odděluje poznámky pod čarou od hlavního textu.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

`NodeType` bude `Paragraph` pro standardní čáru oddělovače. Znalost typu uzlu vám pomůže rozhodnout, zda potřebujete oddělovač upravit nebo jej zcela nahradit.

## Krok 4: Získání uzlu oddělovače koncové poznámky

Podobně můžete **retrieve endnote separator** pomocí vlastnosti `EndnoteSeparator`. Tento uzel odděluje koncové poznámky od hlavního obsahu.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Oba uzly oddělovačů sdílejí ve většině dokumentů stejný `NodeType` (`Paragraph`), ale mohou být přizpůsobeny nezávisle.

## Krok 5: Prozkoumání nebo úprava obsahu oddělovače (volitelné)

Pokud potřebujete změnit vizuální vzhled oddělovače – například nahradit řadu pomlček tenkou čarou – můžete přímo upravit uzel `Paragraph`. Níže je příklad, který nahrazuje výchozí text oddělovače vlastním řetězcem.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Po úpravě uzlů můžete dokument uložit a vidět změny v aplikaci Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Očekávaný výstup v konzoli

Když spustíte program s původním souborem `Footnotes.docx`, měli byste vidět něco podobného:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Pokud otevřete `Footnotes_Updated.docx` v Microsoft Word, oddělovače poznámek pod čarou a koncových poznámek zobrazí vlastní text, který jste vložili.

## Časté otázky a okrajové případy

**Co když dokument neobsahuje žádné poznámky pod čarou?**  
Vlastnost `FootnoteSeparator` stále vrací uzel `Paragraph`, protože Word vždy zahrnuje zástupný oddělovač. Uzel bude prázdný, takže můžete bezpečně přidat obsah nebo jej nechat tak, jak je.

**Mohu získat oddělovač pro konkrétní sekci?**  
Oddělovače poznámek pod čarou a koncových poznámek jsou platné pro celý dokument, nikoli pro konkrétní sekci. Pokud potřebujete řízení na úrovni sekce, musíte pracovat s `Section.FootnoteOptions` a `Section.EndnoteOptions` místo globálních uzlů oddělovačů.

**Funguje to s .NET Core?**  
Ano. Aspose.Words pro .NET je multiplatformní a stejný kód běží na Windows, Linuxu i macOS s .NET 6+.

**Jaký typ uzlu mám očekávat?**  
Jak `FootnoteSeparator`, tak `EndnoteSeparator` vrací uzel `Paragraph` (`NodeType.Paragraph`). Pokud narazíte na jiný typ, dokument může být poškozený a měli byste jej znovu načíst nebo ověřit zdrojový soubor.

## Kompletní zdrojový kód pro rychlé zkopírování

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Zkopírujte kód do souboru `Program.cs`, upravte cesty k souborům a spusťte `dotnet run`. Program demonstruje kompletní workflow **retrieve footnote separator**, od načtení dokumentu až po uložení změn.

## Závěr

Nyní víte, jak **retrieve footnote separator** a **endnote separator retrieval** pomocí Aspose.Words pro .NET, prozkoumat jejich `document node type` a případně nahradit jejich obsah. Tato technika vám umožní automatizovat formátování poznámek pod čarou, generovat vlastní čáry oddělovačů nebo ověřovat strukturu dokumentu v jakékoli aplikaci C#.

Dále můžete prozkoumat související témata, jako je **C# footnote extraction** pro jednotlivé texty poznámek pod čarou, nebo se naučit **modify footnote reference marks** pomocí `FootnoteOptions`. Obě koncepty staví přímo na základech stromu uzlů, které jsou zde popsány.

Šťastné programování a nebojte se experimentovat s různými styly oddělovačů, aby odpovídaly brandingu vašeho projektu!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Zpracování textu s poznámkami pod čarou a koncovými poznámkami](/words/english/net/working-with-footnote-and-endnote/)
- [Přidání obsahu pomocí Document Builder v Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/)
- [Práce s poznámkami pod čarou a koncovými poznámkami](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}