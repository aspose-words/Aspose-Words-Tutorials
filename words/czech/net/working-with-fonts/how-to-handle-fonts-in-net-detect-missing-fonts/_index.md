---
category: general
date: 2026-06-02
description: jak pracovat s fonty v .NET – detekovat chybějící fonty a sledovat změny
  fontů pomocí LoadOptions a FontSettings. Naučte se kompletní, spustitelné řešení.
draft: false
keywords:
- how to handle fonts
- detect missing fonts
- track font changes
language: cs
og_description: Jak pracovat s fonty v .NET – detekovat chybějící fonty a sledovat
  změny fontů. Postupujte podle tohoto krok‑za‑krokem průvodce pro kompletní, připravené
  řešení.
og_title: Jak pracovat s fonty v .NET – detekovat chybějící fonty
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: how to handle fonts in .NET – detect missing fonts and track font changes
    using LoadOptions and FontSettings. Learn a complete, runnable solution.
  headline: how to handle fonts in .NET – detect missing fonts
  type: TechArticle
tags:
- .NET
- Aspose.Words
- FontSettings
title: Jak pracovat s fonty v .NET – detekovat chybějící fonty
url: /cs/net/working-with-fonts/how-to-handle-fonts-in-net-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak zacházet s fonty v .NET – detekce chybějících fontů

Už jste se někdy zamýšleli **jak zacházet s fonty**, když Word dokument odkazuje na typ písma, který není nainstalován v počítači? Nejste v tom sami. Chybějící fonty mohou proměnit upravenou zprávu v nečitelný chaos a bez řádných varování můžete nikdy nezjistit, co bylo nahrazeno.  

V tomto tutoriálu vám ukážeme přesně **jak zacházet s fonty** tím, že detekujeme chybějící fonty **a** sledujeme změny fontů za běhu. Na konci budete mít samostatnou konzolovou aplikaci, která zaznamená každou substituci, takže vás nikdy nepřekvapí tajemná Helvetica tam, kde by měla být Times New Roman.

> **Co získáte:** kompletní, připravený k kopírování a vložení ukázkový kód, vysvětlení každého řádku, tipy pro reálné projekty a rychlý pohled na okrajové případy, na které můžete narazit.

## Požadavky

- .NET 6.0 nebo novější (ukázka používá top‑level `Program.cs` pro stručnost)  
- Aspose.Words pro .NET 23.9 nebo novější – můžete jej stáhnout z NuGet pomocí `dotnet add package Aspose.Words`  
- Word dokument, který úmyslně odkazuje na font, který nemáte (např. `MissingFont.docx`)  

Žádné další knihovny nejsou potřeba.

![Diagram ukazující, jak LoadOptions proudí do FontSettings a události varování nahrazení – příklad jak zacházet s fonty v .NET](https://example.com/images/font‑handling‑flow.png "jak zacházet s fonty v .NET příklad")

## Krok 1: Nastavení LoadOptions s FontSettings  

Prvním, co potřebujeme, je objekt `LoadOptions`, který říká Aspose.Words, aby sledoval problémy s fonty.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

// Create LoadOptions and attach a fresh FontSettings instance.
var loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

**Proč je to důležité:** `LoadOptions` je bránou při čtení dokumentu z disku. Poskytnutím vlastního `FontSettings` získáme háček do interního enginu pro řešení fontů, což je jediný způsob, jak **detekovat chybějící fonty** před vykreslením dokumentu.

## Krok 2: Přihlášení k události SubstitutionWarning  

Aspose.Words vyvolá událost `SubstitutionWarning` pokaždé, když nenajde přesně ten font, který jste požadovali. Zaznamenáme podrobnosti, abyste viděli, které fonty byly požadovány a které byly skutečně použity.  

```csharp
// Hook into the warning event – this is where we “track font changes”.
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.RequestedFontName – the name the document asked for.
    // e.SubstitutedFontName – the name Aspose.Words fell back to.
    // e.WarningType – tells you why the substitution happened.
    Console.WriteLine(
        $"[Font Substitution] Requested: {e.RequestedFontName}, " +
        $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
};
```

**Proč posloucháme:** Bez tohoto posluchače byste nikdy nezjistili, že k substituci došlo. Událost vám poskytne kompletní auditní stopu, čímž splňuje požadavek „sledovat změny fontů“.

## Krok 3: Načtení dokumentu pomocí našich nastavených možností  

Nyní skutečně načteme soubor. Protože jsme předali `loadOptions`, Aspose.Words vyvolá událost varování pro každý chybějící font, na který narazí.  

```csharp
// Replace the path with the location of your test document.
string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

Document doc = new Document(docPath, loadOptions);
```

A to je vše – dokument je nyní načten a všechny problémy s fonty už byly vytištěny do konzole.

## Krok 4: (Volitelné) Ověření nahrazených fontů v dokumentu  

Pokud chcete dvojitě zkontrolovat, které fonty skončily ve finálním PDF nebo DOCX, můžete projít kolekci fontů dokumentu:  

```csharp
Console.WriteLine("\n--- Fonts actually used in the document ---");
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
}
```

Spuštění tohoto kódu po načtení vypíše každý font, který engine rozhodl vložit nebo na který odkazovat. Užitečné, když potřebujete vytvořit zprávu pro QA týmy.

## Kompletní funkční příklad  

Zkopírujte blok níže do nového konzolového projektu (`dotnet new console`) a spusťte jej. Program vypíše každou substituci a poté zobrazí fonty, které přežily načtení.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions with FontSettings.
        // -------------------------------------------------
        var loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Step 2: Hook the substitution warning event.
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"[Font Substitution] Requested: {e.RequestedFontName}, " +
                $"Used: {e.SubstitutedFontName}, Reason: {e.WarningType}");
        };

        // -------------------------------------------------
        // Step 3: Load the document (this triggers warnings).
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // Step 4 (optional): List fonts actually used.
        // -------------------------------------------------
        Console.WriteLine("\n--- Fonts actually used in the document ---");
        foreach (FontInfo fontInfo in doc.FontInfos)
        {
            Console.WriteLine($"{fontInfo.FontFamilyName} – {fontInfo.FontStyle}");
        }

        Console.WriteLine("\nDone. Press any key to exit.");
        Console.ReadKey();
    }
}
```

### Očekávaný výstup  

Pokud `MissingFont.docx` požaduje *„Comic Sans MS“* (který není nainstalován), uvidíte něco jako:  

```
[Font Substitution] Requested: Comic Sans MS, Used: Arial, Reason: FontNotFound
[Font Substitution] Requested: Times New Roman, Used: Times New Roman, Reason: None

--- Fonts actually used in the document ---
Arial – Regular
Times New Roman – Regular
```

První řádek dokazuje, že **detekujeme chybějící fonty** a **sledujeme změny fontů**. Druhý řádek ukazuje substituci, která nebyla nutná (žádné varování, protože font existoval).

## Časté úskalí a profesionální tipy  

| Problém | Co se stane | Jak opravit / vyhnout se |
|---------|--------------|--------------------------|
| **Nevyvolají se žádné varovné události** | Můžete si myslet, že API je rozbité. | Ujistěte se, že *přiřadíte* `FontSettings` k `LoadOptions` **před** načtením dokumentu. Háček události musí být připojen **před** voláním `new Document(...)`. |
| **Nahrazené fonty stále vypadají špatně** | Aspose.Words přejde na generický font, který neodpovídá stylu. | Poskytněte vlastní složku s fonty pomocí `fontSettings.SetFontsFolder(@"C:\MyFonts", true)`. To dává engine více možností, než aby použil generický font. |
| **Pokles výkonu u velkých dokumentů** | Prohledávání každého fontu může přidat několik milisekund. | Uložte objekt `FontSettings` do cache, pokud načítáte mnoho dokumentů po sobě. Opětovné použití stejné instance zabraňuje opakovanému čtení systémových tabulek fontů. |
| **Výstup do konzole se ztratí v GUI aplikacích** | Varování neuvidíte. | Přesměrujte událost do loggeru (např. `Serilog`) nebo zapisujte do souboru: `File.AppendAllText("font-warnings.log", …)`. |

## Rozšíření řešení  

- **Export do PDF s vloženými fonty** – po načtení zavolejte `doc.Save("output.pdf", SaveOptions.CreateSaveOptions(SaveFormat.Pdf));` a ujistěte se, že nastavíte `PdfSaveOptions.FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll;`.  
- **Dávkové zpracování** – obalte logiku načítání do `foreach` přes složku s DOCX soubory. Zaznamenávejte varování každého souboru do CSV pro auditní účely.  
- **Uživatelsky přívětivé UI** – vystavte stejnou logiku za tlačítkem ve WinForms/WPF aplikaci a zobrazte varování v `ListBox`.

## Závěr  

Prošli jsme **jak zacházet s fonty** v .NET nastavením `LoadOptions`, přihlášením k události `SubstitutionWarning` a nakonec načtením dokumentu. Příklad nejen **detekuje chybějící fonty**, ale také **sleduje změny fontů**, takže můžete auditovat každou substituci.  

Vyzkoušejte to s vlastními dokumenty, upravte cestu ke složce s fonty a už vás nikdy nepřekvapí neočekávaná výměna fontu. Pokud vám tento průvodce přišel užitečný, podívejte se i na související témata jako *„vložit vlastní fonty do PDF s Aspose.Words“* nebo *„vytvořit strategii fallback fontů pro cross‑platform .NET aplikace“*.  

Šťastné kódování a ať se vaše dokumenty vždy vykreslí přesně tak, jak jste zamýšleli!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Jak načíst DOCX a detekovat chybějící fonty – kompletní C# průvodce](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Jak detekovat fonty v Aspose.Words – zpracování varování a nastavení](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Jak používat LoadOptions v Aspose.Words – kompletní průvodce](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}