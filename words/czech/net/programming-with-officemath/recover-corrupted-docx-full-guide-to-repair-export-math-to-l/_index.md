---
category: general
date: 2025-12-23
description: Naučte se, jak obnovit poškozené soubory docx, použít režim obnovy, exportovat
  rovnice do LaTeXu a generovat unikátní názvy obrázků v C#. Krok za krokem kód s vysvětleními.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: cs
og_description: Obnovte poškozené soubory docx, použijte režim obnovy, exportujte
  rovnice do LaTeXu a generujte jedinečné názvy obrázků pomocí Aspose.Words v C#.
og_title: Obnovit poškozený docx – Kompletní C# tutoriál
tags:
- Aspose.Words
- C#
- Document Recovery
title: obnovit poškozený docx – Kompletní průvodce opravou, exportem matematiky do
  LaTeXu a generováním unikátních názvů obrázků
url: /cs/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# obnovit poškozený docx – Kompletní průvodce opravou, exportem rovnic do LaTeX a generováním jedinečných názvů obrázků

Už jste někdy otevřeli **.docx**, který se odmítá načíst, protože je poškozený? Nejste v tom sami. V mnoha reálných projektech může poškozený soubor Word zastavit celý pracovní postup, ale dobrá zpráva je, že můžete **recover corrupted docx** soubory programově.  

V tomto tutoriálu projdeme přesně kroky k **recover corrupted docx**, ukážeme **how to use recovery mode**, demonstrujeme **export equations to LaTeX** a nakonec **generate unique image names** při ukládání do Markdownu. Na konci budete mít jeden spustitelný C# program, který zvládne všechny tyto úkoly bez problémů.

## Požadavky

- .NET 6 nebo novější (kód také funguje s .NET Framework 4.6+).  
- Aspose.Words pro .NET (bezplatná zkušební verze nebo licencovaná verze). Instalujte přes NuGet:

```bash
dotnet add package Aspose.Words
```

- Základní znalost C# a práce se soubory (I/O).  
- Poškozený soubor `corrupt.docx` pro testování (můžete simulovat poškození zkrácením platného souboru).

> **Tip:** Uchovejte si zálohu původního souboru před zahájením — obnova je destruktivní pouze pokud přepíšete zdroj.

## Krok 1 – Obnovit poškozený DOCX pomocí Recovery Mode

Prvním krokem je říct Aspose.Words, aby považoval přicházející soubor za potenciálně poškozený. Zde vstupuje do hry **how to use recovery mode**.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**Proč je to důležité:**  
Když je povoleno `RecoveryMode.Recover`, Aspose.Words se pokusí obnovit interní strom dokumentu, přeskočit nečitelné části a zachovat co nejvíce obsahu. Bez toho by konstruktor `Document` vyhodil výjimku a ztratili byste jakoukoli šanci soubor zachránit.

> **Co když je soubor neopravitelný?**  
> Knihovna i tak vrátí objekt `Document`, ale některé uzly mohou chybět. Můžete zkontrolovat `doc.GetChildNodes(NodeType.Any, true).Count`, abyste zjistili, kolik prvků přežilo.

## Krok 2 – Export Office Math equations do LaTeX při ukládání jako Markdown

Mnoho technických dokumentů obsahuje rovnice napsané pomocí Office Math. Pokud potřebujete tyto rovnice v LaTeXu — například pro publikaci na vědeckém blogu — můžete požádat Aspose.Words, aby provedl konverzi za vás.

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**Jak to funguje:**  
`OfficeMathExportMode.LaTeX` říká ukladači, aby nahradil každý uzel `OfficeMath` jeho LaTeXovou reprezentací zabalenou do `$…$` (inline) nebo `$$…$$` (display). Výsledný soubor Markdown může být předán přímo generátorům statických stránek jako Hugo nebo Jekyll.

> **Hraniční případ:** Pokud originální dokument obsahuje složité objekty rovnic (např. matice), konverze do LaTeXu může generovat víceřádkový výstup. Zkontrolujte vygenerovaný `.md`, aby odpovídal vašim očekáváním formátování.

## Krok 3 – Uložit dokument jako PDF při řízení značek plovoucích tvarů

Někdy potřebujete PDF verzi stejného dokumentu, ale také vám záleží na tom, jak jsou plovoucí tvary (obrázky, textová pole) označeny pro přístupnost. Příznak `ExportFloatingShapesAsInlineTag` vám dává tuto kontrolu.

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**Proč přepínat tento příznak?**  
- `true` → Plovoucí tvary se stanou značkám `<Figure>`, které mnoho čteček obrazovky považuje za samostatné obrázky s popisky.  
- `false` → Tvary jsou zabaleny do obecných značek `<Div>`, které mohou být asistivními technologiemi ignorovány. Vyberte podle vašich požadavků na přístupnost.

## Krok 4 – Export do Markdown s vlastním zpracováním obrázků (generate unique image names)

Když uložíte Word dokument do Markdownu, všechny vložené obrázky jsou zapsány na disk. Ve výchozím nastavení dostanou původní název souboru, což může způsobit kolize, pokud zpracováváte mnoho dokumentů ve stejné složce. Připojíme se k procesu ukládání a **generate unique image names** automaticky.

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**Co se děje pod kapotou?**  
`ResourceSavingCallback` je volán pro každý externí zdroj (obrázky, SVG atd.) během operace ukládání. Vrácením úplné cesty určujete, kam se soubor uloží a jak se bude jmenovat. GUID zajišťuje **generate unique image names** bez jakéhokoli ručního vedení záznamů.

> **Tip:** Pokud potřebujete deterministické pojmenování (např. založené na alt textu obrázku), nahraďte `Guid.NewGuid()` hašem `resourceInfo.Name`.

## Kompletní funkční příklad

Spojením všech částí zde máte kompletní program, který můžete zkopírovat a vložit do konzolové aplikace:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### Očekávaný výstup

Spuštěním programu by se měly zobrazit zprávy v konzoli podobné těmto:

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

Najdete tři soubory:

| Soubor | Účel |
|------|---------|
| `out.md` | Markdown, kde se každá rovnice Office Math zobrazuje jako LaTeX (`$…$` nebo `$$…$$`). |
| `out.pdf` | PDF verze s plovoucími tvary označenými jako `<Figure>` pro lepší přístupnost. |
| `out2.md` + `md_images\*` | Markdown plus složka s jedinečně pojmenovanými soubory obrázků (na základě GUID). |

## Často kladené otázky a hraniční případy

| Otázka | Odpověď |
|----------|--------|
| **Co když poškozený soubor nemá žádný obnovitelný obsah?** | Aspose.Words i tak vrátí objekt `Document`, ale může být prázdný. Před pokračováním zkontrolujte `doc.GetChildNodes(NodeType.Paragraph, true).Count`. |
| **Mohu změnit LaTeX oddělovač?** | Ano — nastavte `markdownMathOptions.MathDelimiter = "$$"` pro vynucení oddělovačů ve stylu display. |
| **Musím uvolnit objekt `Document`?** | Třída `Document` implementuje `IDisposable`. Zabalte ji do bloku `using`, pokud zpracováváte mnoho souborů, aby se rychle uvolnily nativní zdroje. |
| **Jak zachovat původní názvy souborů obrázků?** | V callbacku vraťte `Path.Combine(imageFolder, resourceInfo.Name)`. Jen pamatujte na riziko kolizí názvů. |
| **Je přístup pomocí GUID bezpečný pro repozitáře pod verzovacím systémem?** | GUID jsou stabilní mezi běhy, ale nejsou čitelné pro člověka. Pokud potřebujete reprodukovatelné názvy, hašujte původní název plus projektový sůl. |

## Závěr

Ukázali jsme vám, jak **recover corrupted docx** soubory, demonstrovali **how to use

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}