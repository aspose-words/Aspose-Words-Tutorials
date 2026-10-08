---
category: general
date: 2026-03-06
description: Zachyťte varování o písmu při načítání dokumentu Word v C#. Naučte se
  detekovat chybějící písma, kontrolovat písma v dokumentu a efektivně řešit chybějící
  písma.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: cs
og_description: Zachyťte varování o písmu při načítání dokumentu Word v C#. Tento
  tutoriál ukazuje, jak detekovat chybějící písma, zkontrolovat písma v dokumentu
  a řešit chybějící písma.
og_title: Zachycení varování o fontu v C# – Kompletní průvodce
tags:
- Aspose.Words
- C#
- Font Management
title: Zachycení varování o fontu v C# – kompletní průvodce
url: /cs/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zachycení varování o písmu v C# – Kompletní průvodce

Už jste někdy potřebovali **zachytit varování o písmu** při zpracování Word dokumentu? Zachycení varování o písmu je nezbytné pro **detekci chybějících písem** a zajištění, že konečný výstup vypadá přesně tak, jak jste zamýšleli.  

V tomto tutoriálu projdeme praktickým, end‑to‑end příkladem, který načte soubor `.docx`, monitoruje proces načítání a hlásí jakékoli nahrazení písem. Na konci budete vědět, jak **načíst Word dokument** bezpečně, **zkontrolovat písma v dokumentu** a **zpracovat chybějící písma** bez nečekaných runtime chyb.

## Co se naučíte

- Jak připojit sběrač varování k objektu Aspose.Words `Document`.
- Které typy varování indikují chybějící nebo nahrazené písmo.
- Způsoby, jak zaznamenat nebo reagovat na tato varování v aplikaci produkční úrovně.
- Tipy pro konfiguraci vlastních zdrojů písem, pokud potřebujete **zpracovat chybějící písma** elegantně.

> **Předpoklad:** Máte platnou licenci Aspose.Words pro .NET (nebo používáte bezplatnou zkušební verzi) a vývojové prostředí .NET (Visual Studio, Rider nebo VS Code). Žádné další knihovny nejsou vyžadovány.

---

## Zachycení varování o písmu – Krok za krokem

Níže je kompletní spustitelný kód. Každá část je oddělena do vlastního kroku, abyste ji mohli zkopírovat, experimentovat a rozšířit logiku.

![Zachycení varování o písmu diagram](image.png "Diagram zobrazující sběr varování"){: alt="zachycení varování o písmu diagram"}

### Krok 1: Načtení Word dokumentu

Nejprve potřebujeme **načíst Word dokument**, který může obsahovat písma neinstalovaná na aktuálním počítači. Konstruktor `Document` provádí těžkou práci, ale volání ponecháme izolované, abyste jej později mohli vyměnit za stream nebo pole bajtů, pokud bude potřeba.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Proč je to důležité:** Načtení dokumentu bez obsluhy varování znamená, že jakékoli nahrazení písma je tiše ignorováno. Nastavením `WarningCallback` *před* načtením garantujeme, že uvidíme každé varování `FontSubstitution`, které nastane.

### Krok 2: Připojení sběrače varování

Třída `WarningInfoCollector` je vestavěná implementace rozhraní `IWarningCallback`. Jednoduše ukládá každé varování do seznamu, který můžeme později prozkoumat.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Tip:** Pokud potřebujete **zpracovat chybějící písma** agresivněji (např. přerušit načítání nebo nahradit konkrétním záložním písmem), můžete nahradit `Console.WriteLine` vlastní logikou – vyhodit výjimku, zaznamenat do souboru nebo dokonce přidat vlastní zdroj písma.

### Krok 3: Ověření výstupu

Spusťte program z konzole. Pokud váš `input.docx` používá písmo, které není nainstalováno, uvidíte řádky jako:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Pokud se žádný výstup neobjeví, dokument buď použil pouze písma, která jsou již k dispozici **nebo** Aspose.Words našel odpovídající písmo ve své vestavěné kolekci záložních písem. V každém případě jste úspěšně **zkontrolovali písma v dokumentu**.

---

## Detekce chybějících písem bez licence (bezplatná zkušební verze)

I když používáte 30‑denní zkušební verzi, mechanismus varování funguje naprosto stejně. Jediný rozdíl je, že zkušební verze přidá vodoznak do generovaného výstupu, který **neovlivňuje** sběr varování. Takže můžete bezpečně **detekovat chybějící písma** před tím, než se rozhodnete zakoupit plnou licenci.

## Zpracování chybějících písem – Pokročilé možnosti

Někdy chcete poskytnout vlastní soubory písem (např. firemní značkové písma), aby k nahrazení nedošlo. Aspose.Words vám umožní zaregistrovat vlastní složky s písmy:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Umístěte výše uvedený kód **před** načtením dokumentu, pokud chcete, aby načítač zohlednil tato písma během počáteční fáze parsování. Toto je nejspolehlivější způsob, jak **zpracovat chybějící písma** bez spoléhání se na výchozí systémová písma.

## Časté úskalí a jak se jim vyhnout

| Problém | Proč k tomu dochází | Řešení |
|---------|----------------------|--------|
| **Warning collector attached after loading** | Dokument je již parsován, takže nejsou zaznamenána žádná varování. | Připojte `WarningCallback` **před** voláním `new Document(path)`. |
| **Only generic warnings appear** | Filtrovali jste špatný typ `WarningType`. | Použijte `WarningType.FontSubstitution` pro zaměření na problémy s písmy. |
| **No output despite missing fonts** | Aspose.Words našel vestavěnou náhradní možnost (např. Arial). | Vypněte vestavěné náhrady pomocí `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Performance hit when scanning large docs** | Sběr každého varování může být náročný. | Omezte sběr jen na `FontSubstitution`, nebo zpracovávejte varování po dávkách. |

## Kompletní funkční příklad (připravený ke kopírování)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Očekávaný výstup v konzoli** (při předpokladu dvou chybějících písem):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Pokud konzole zůstane tichá kromě zprávy “Document loaded successfully,” úspěšně jste **zkontrolovali písma v dokumentu** a nenašli žádná chybějící.

## Závěr

Ukázali jsme vám, jak **zachytit varování o písmu** v C# pomocí Aspose.Words, spolehlivý způsob, jak **detekovat chybějící písma**, **bezpečně načíst Word dokument**, **zkontrolovat písma v dokumentu** a **zpracovat chybějící písma** prostřednictvím vlastních zdrojů písem.  

S tímto vzorem můžete integrovat validaci písem do jakéhokoli automatizačního řetězce – ať už generujete PDF, převádíte do HTML nebo jen archivujete Word soubory.

### Co dál?

- Prozkoumejte API **FontSettings.SubstitutionSettings** pro definování vlastních pravidel náhrad.
- Spojte sběr varování s logovacím frameworkem (Serilog, NLog) pro monitorování v produkci.
- Použijte stejný přístup k zachycení dalších typů varování, jako je rozlišení obrázků nebo nepodporované funkce.

Máte další otázky ohledně zpracování písem nebo Aspose.Words obecně? Zanechte komentář nebo navštivte fóra komunity Aspose. Šťastné programování a ať se vaše dokumenty vždy vykreslují s očekávanými písmy!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}