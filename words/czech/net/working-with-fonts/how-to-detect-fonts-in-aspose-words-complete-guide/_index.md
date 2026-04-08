---
category: general
date: 2026-04-07
description: Naučte se, jak detekovat písma a jak zachytit varování při zpracování
  chybějících písem v C# pomocí Aspose.Words. Kód krok za krokem je zahrnut.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: cs
og_description: Jak detekovat písma v Aspose.Words? Postupujte podle tohoto tutoriálu,
  abyste zachytili varování a snadno řešili chybějící písma.
og_title: Jak detekovat písma v Aspose.Words – kompletní průvodce
tags:
- Aspose.Words
- C#
- Font handling
title: Jak detekovat písma v Aspose.Words – kompletní průvodce
url: /cs/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak detekovat písma v Aspose.Words – Kompletní průvodce

Už jste se někdy zamýšleli **jak detekovat písma**, která ve Word dokumentu chybí, ještě před tím, než jej nasadíte do produkce? Nejste v tom sami. V mnoha podnikových scénářích může chybějící písmo rozbít pipeline pro konverzi do PDF nebo způsobit rozložení, které vypadá neprofesionálně. Dobrou zprávou je, že Aspose.Words poskytuje vestavěný způsob, jak odhalit tyto chybějící typy písma a zobrazit jasná varování.

V tomto tutoriálu si projdeme **jak detekovat písma**, **jak zachytit varování** a nejlepší postupy **jak zacházet s chybějícími písmy**, aby vaše aplikace zůstala robustní. Žádné externí nástroje, žádné hádání — pouze čistý C# kód, který můžete hned vložit do svého projektu.

> **Rychlý náhled:** Na konci budete mít znovupoužitelný `FontSubstitutionWarningCollector`, který sbírá každou zprávu o substituci písma během načítání dokumentu, a budete vědět, jak reagovat, když písmo nelze najít.

---

## Co se naučíte

- Jak nakonfigurovat `LoadOptions`, aby naslouchala varováním o substituci písma.  
- Jak zachytit tato varování v vlastní třídě sběrače.  
- Jak zpracovat nasbíraná varování a rozhodnout, zda ukončit, zalogovat nebo nahradit písma.  
- Jak řešit okrajové případy u dokumentů, které odkazují na vzdálená nebo vložená písma.  

**Požadavky:** .NET 6+ (nebo .NET Framework 4.6+), Aspose.Words pro .NET (nejnovější verze) a základní znalost C#. Pokud jste s Aspose.Words nikdy nepracovali, nebojte se — tento průvodce předpokládá jen pár minut nastavení.

---

## Jak detekovat písma pomocí Aspose.Words LoadOptions

Prvním krokem k detekci chybějících písem je říci Aspose.Words, aby je hlásila. To se provádí pomocí vlastnosti `LoadOptions.WarningCallback`, která přijímá libovolnou třídu implementující `IWarningCallback`. Níže vytvoříme malý sběrač, který ukládá každé varování pro pozdější kontrolu.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Proč je to důležité:** Bez callbacku pro varování Aspose.Words tiše nahrazuje chybějící písma výchozím, a nikdy se nedozvíte, že problém existuje. Zachycením `WarningType.FontSubstitution` získáte úplnou přehlednost — právě data, která potřebujete k **detekci písem**, která nejsou na hostitelském stroji dostupná.

Nyní připojíme sběrač k `LoadOptions` a načteme dokument:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Tip:** Pokud pracujete s mnoha dokumenty najednou, znovu použijte stejnou instanci `FontSubstitutionWarningCollector`, ale nezapomeňte mezi načteními zavolat `Clear()`, aby nedošlo ke smíchání varování z různých souborů.

---

## Zachycení varování během načítání dokumentu

Po načtení dokumentu už sběrač obsahuje všechna varování související s písmy. Další logická otázka je: *Jak zachytit varování* tak, aby se dala snadno zalogovat nebo zobrazit?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Typický výstup vypadá takto:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Co vám to říká:** Každý řádek odhaluje původní název písma a náhradní, které Aspose.Words zvolilo. S těmito informacemi můžete rozhodnout, zda je náhrada přijatelna, nebo zda musíte chybějící písmo vložit ručně.

---

## Elegantní zacházení s chybějícími písmy

Detekce a zachycení varování je jen polovina boje. Skutečná hodnota přichází, když **zacházíte s chybějícími písmy** připraveným způsobem pro produkci. Níže jsou tři běžné strategie:

1. **Logovat a pokračovat** – Vhodné pro dávkové zpracování, kde stačí auditní stopa.  
2. **Ukončit při kritických písmenech** – Vyhodit výjimku, pokud chybí konkrétní písmo (např. firemní typ písma).  
3. **Vložit písmo za běhu** – Načíst chybějící písmo ze známé složky a zaregistrovat jej v Aspose.Words před opětovným načtením dokumentu.

### Příklad: Ukončit při kritickém písmu

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Příklad: Automaticky vložit chybějící písma

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Proč tyto vzory pomáhají:** Tím, že explicitně rozhodnete, co dělat, když písmo chybí, eliminujete tiché náhrady, které by mohly ohrozit značku nebo čitelnost. To je podstata **zacházení s chybějícími písmy** kontrolovaným způsobem.

---

## Kompletní funkční příklad

Spojením všeho dohromady získáte jeden připravený program, který demonstruje **jak detekovat písma**, **jak zachytit varování** a jednoduchou politiku **zacházení s chybějícími písmy** prostřednictvím jejich logování.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Očekávaný výsledek:** Když spustíte program proti dokumentu, který odkazuje na písmo, jež na stroji není, konzole vypíše každé varování o substituci. Pokud některé varování zahrnuje písmo ze sady `critical`, program se předčasně ukončí, čímž zabrání vytvoření poškozeného PDF.

---

## Často kladené otázky (FAQ)

| Otázka | Odpověď |
|----------|--------|
| *Potřebuji licenci pro Aspose.Words, abych mohl použít tento kód?* | Ano, platná licence Aspose.Words odstraní evaluační vodoznaky a odemkne plnou funkcionalitu. |
| *Dokáže tento přístup detekovat vložená písma?* | Vložená písma jsou již součástí souboru, takže Aspose.Words nevyvolá varování o substituci. Pro výčet vložených písem můžete použít `Document.FontInfos`. |
| *Co když chybějící písmo existuje jako systémové na Windows, ale ne na Linuxu?* | Na Linuxu se spustí stejné varování, protože písmo není nainstalováno. Použijte strategii „zacházení s chybějícími písmy“ a přiložte potřebné soubory `.ttf` k aplikaci. |
| *Je sběrač varování thread...* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}