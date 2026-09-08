---
category: general
date: 2026-09-08
description: Získání oddělovače koncových poznámek a zobrazení oddělovače poznámek
  pod čarou při načítání dokumentu Word pomocí Aspose.Words pro .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve endnote separator
- load word document
- display footnote separator
- Aspose.Words C#
- footnote and endnote handling
language: cs
lastmod: 2026-09-08
og_description: Získat oddělovač koncových poznámek a zobrazit oddělovač poznámek
  pod čarou při načítání dokumentu Word pomocí Aspose.Words pro .NET.
og_image_alt: Console screenshot showing the footnote separator text printed by a
  C# program
og_title: Získat oddělovač koncových poznámek při načítání dokumentu Word v C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Retrieve endnote separator and display footnote separator when you
    load a Word document using Aspose.Words for .NET.
  headline: Retrieve endnote separator while loading a Word document in C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word processing
title: Získat oddělovač koncových poznámek při načítání dokumentu Word v C#
url: /cs/net/working-with-footnote-and-endnote/retrieve-endnote-separator-while-loading-a-word-document-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Získání oddělovače koncových poznámek při načítání dokumentu Word v C#

Pokud potřebujete **retrieve endnote separator** z Word souboru, tento průvodce vám přesně ukáže, jak na to. Také se naučíte, jak **load Word document** pomocí Aspose.Words a **display footnote separator** text v konzoli, vše v jednom spustitelném příkladu.

Práce s poznámkami pod čarou a koncovými poznámkami je běžnou požadavkem pro právní, akademické nebo vydavatelské aplikace. Tento tutoriál pokrývá vše, co potřebujete—od otevření souboru po zpracování případů, kdy chybí oddělovač—abyste mohli integrovat řešení do libovolného .NET projektu bez hádání.

## Co tento tutoriál pokrývá

* Jak **load Word document** pomocí Aspose.Words API.  
* Jak **retrieve endnote separator** a proč je oddělovač důležitý.  
* Jak **display footnote separator** v konzoli pro ladění nebo logování.  
* Zpracování okrajových případů, kdy dokument neobsahuje poznámky pod čarou ani koncové poznámky.  
* Kompletní, připravený k zkopírování ukázkový kód, který běží na .NET 6 nebo novějším.

### Požadavky

| Requirement | Reason |
|-------------|--------|
| .NET 6 SDK nebo novější | Poskytuje runtime pro C# příklad. |
| Aspose.Words pro .NET (NuGet balíček `Aspose.Words`) | Knihovna, která zpřístupňuje `Document.Footnotes` a `Document.Endnotes`. |
| Word soubor (`Footnotes.docx`), který obsahuje alespoň jednu poznámku pod čarou nebo koncovou poznámku | Ukazuje oddělovače. |
| Jakékoli IDE (Visual Studio, Rider, VS Code) | Pro kompilaci a spuštění programu. |

> **Tip:** Pokud nemáte dokument s poznámkami pod čarou, vytvořte rychle jeden v Microsoft Word: Insert → Footnote → napište nějaký text a uložte jako `Footnotes.docx`.

## Načtení Word dokumentu pomocí Aspose.Words

Prvním krokem je **load word document** do paměti. Aspose.Words načte formát souboru a vytvoří objektový model, který můžete dotazovat.

```csharp
using Aspose.Words;
using System;

class Program
{
    static void Main()
    {
        // Step 1: Load the document containing footnotes and endnotes
        // Adjust the path to point to your local file.
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");
```

*Proč je to důležité*: Načtení dokumentu je předpokladem pro jakoukoli další manipulaci. Pokud je cesta k souboru nesprávná, `Document` vyhodí `FileNotFoundException`, proto před spuštěním ověřte cestu.

## Získání odstavce oddělovače poznámky pod čarou

Oddělovač poznámky pod čarou je odstavec, který vizuálně odděluje hlavní text od seznamu poznámek pod čarou. Jeho získání vám umožní prohlédnout nebo upravit jeho formátování.

```csharp
        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.Footnotes.Separator;

        // The separator may be null if the document has no footnotes.
        if (footnoteSeparator != null)
        {
            // Step 3: **display footnote separator** text in the console
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }
```

*Proč je to důležité*: **Display footnote separator** vám pomůže ověřit, že je přistupováno ke správnému odstavci, zejména když potřebujete použít vlastní stylování (např. čáru nebo konkrétní font).

## Získání odstavce oddělovače koncové poznámky

Nyní **retrieve endnote separator**. Proces je obdobný jako u poznámek pod čarou, ale používá kolekci `Endnotes`.

```csharp
        // Step 4: Retrieve the endnote separator paragraph
        Paragraph endnoteSeparator = doc.Endnotes.Separator;

        // The separator can also be null if there are no endnotes.
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

*Proč je to důležité*: Krok **retrieve endnote separator** je nezbytný, když potřebujete upravit vizuální oddělení mezi hlavním obsahem a seznamem koncových poznámek—běžné v akademickém vydavatelství, kde se koncové poznámky objevují na konci kapitoly.

### Zpracování chybějících oddělovačů

Oba `Footnotes.Separator` i `Endnotes.Separator` vrací `null`, pokud dokument nedefinuje oddělovač. Vždy zkontrolujte `null` před voláním `GetText()`, abyste se vyhnuli `NullReferenceException`. Pokud potřebujete výchozí oddělovač, můžete jej vytvořit:

```csharp
if (endnoteSeparator == null)
{
    endnoteSeparator = new Paragraph(doc);
    endnoteSeparator.AppendChild(new Run(doc, "—")); // Simple dash as a separator
    doc.Endnotes.InsertSeparator(endnoteSeparator);
}
```

Tento kód vloží minimální oddělovač, aby se pozdější zpracování mohlo spolehnout na jeho existenci.

## Očekávaný výstup v konzoli

Když se ukázka spustí proti dokumentu, který obsahuje jednu poznámku pod čarou a jednu koncovou poznámku, měli byste vidět něco podobného:

```
Document loaded successfully.
Footnote separator text: — 
Endnote separator text: — 
```

Pokud dokument postrádá poznámky pod čarou nebo koncové poznámky, program vytiskne odpovídající zprávy „not found“, což demonstruje elegantní zpracování chyb.

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat do nového C# konzolového projektu. Není potřeba žádný další kód.

```csharp
using Aspose.Words;
using System;

class RetrieveSeparatorsDemo
{
    static void Main()
    {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/Footnotes.docx");
        Console.WriteLine("Document loaded successfully.");

        // Retrieve and display the footnote separator
        Paragraph footnoteSeparator = doc.Footnotes.Separator;
        if (footnoteSeparator != null)
        {
            Console.WriteLine("Footnote separator text: " + footnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No footnote separator found – the document may not contain footnotes.");
        }

        // Retrieve and display the endnote separator
        Paragraph endnoteSeparator = doc.Endnotes.Separator;
        if (endnoteSeparator != null)
        {
            Console.WriteLine("Endnote separator text: " + endnoteSeparator.GetText().Trim());
        }
        else
        {
            Console.WriteLine("No endnote separator found – the document may not contain endnotes.");
        }
    }
}
```

Uložte soubor jako `Program.cs`, přidejte NuGet balíček Aspose.Words (`dotnet add package Aspose.Words`) a spusťte `dotnet run`. Program vytiskne texty oddělovačů nebo vás informuje, pokud chybí.

## Běžné varianty a co‑když scénáře

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Více vlastních oddělovačů** | Použijte `doc.Footnotes.Separator` k nahrazení výchozího, poté přidejte další odstavce oddělovačů ručně pomocí `doc.Footnotes.Add(separatorParagraph)`. |
| **Změna stylu oddělovače** | Po získání oddělovače upravte jeho `ParagraphFormat` (např. `footnoteSeparator.ParagraphFormat.Alignment = ParagraphAlignment.Center;`). |
| **Práce s .doc soubory** | Stejná API funguje; stačí zajistit, aby cesta k souboru končila na `.doc`. |
| **Zpracování mnoha dokumentů** | Zabalte načítání a získání oddělovačů do `foreach` smyčky; použijte jedinou instanci `Document` pouze pokud ji resetujete pomocí `doc = new Document(path)`. |

## Seznam osvědčených postupů

- ✅ **Vždy zkontrolujte `null`** před přístupem k textu oddělovače.  
- ✅ **Ořízněte** výsledek `GetText()` pro odstranění skrytých znaků konce řádku.  
- ✅ **Uvolněte** velké objekty `Document`, pokud zpracováváte mnoho souborů najednou (použijte `using` nebo zavolejte `doc.Dispose()`).  
- ✅ **Logujte** text oddělovače pouze během vývoje; vyhněte se jeho zveřejňování v produkčních logách, pokud to není vyžadováno.  

## Závěr

Nyní víte, jak **retrieve endnote separator** při **load Word document** a **display footnote separator** v .NET konzolové aplikaci. Kompletní příklad ukazuje načítání, dotazování a bezpečné zpracování chybějících oddělovačů, což vám poskytuje pevný základ pro jakýkoli úkol manipulace s poznámkami pod čarou nebo koncovými poznámkami.

Další kroky, které můžete prozkoumat:

* **Přizpůsobení formátování poznámek pod čarou/koncových poznámek** – upravte písma, okraje nebo číslovací styly.  
* **Extrahování obsahu poznámek pod čarou/koncových poznámek** – iterujte kolekce `doc.Footnotes` nebo `doc.Endnotes`.  
* **Uložení upraveného dokumentu** – použijte `doc.Save("output.docx")` pro zachování změn.

Neváhejte experimentovat s různými Word soubory, styly oddělovačů a funkcemi Aspose.Words. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak načíst Word dokumenty pomocí Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)
- [Získání oddělovače stylu odstavce ve Word dokumentu](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Vytvoření a stylování Word dokumentu v Aspose.Words pro .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}