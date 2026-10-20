---
category: general
date: 2026-03-17
description: Jak detekovat písma v C# pomocí Aspose.Words a varovného callbacku. Naučte
  se, jak použít callback k zachycení substitucí chybějících písem při načítání dokumentů.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: cs
og_description: Jak detekovat písma v C# pomocí Aspose.Words. Tento průvodce ukazuje,
  jak použít zpětné volání k zachycení varování o chybějících písmech při načítání
  dokumentu.
og_title: Jak detekovat písma v C# – Použijte zpětné volání s Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak detekovat fonty v C# – Použijte zpětné volání s Aspose.Words
url: /cs/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak detekovat písma v C# – Použití callbacku s Aspose.Words

Už jste někdy potřebovali **jak detekovat písma** v dokumentu Word programově a přemýšleli, proč některé znaky po konverzi vypadají divně? Nejste v tom sami. V mnoha reálných projektech—generátorech faktur, exportérech reportů nebo dávkových zpracovacích pipelinech—chybějící písma způsobují tiché problémy s rozvržením, které je těžké ladit.  

Dobrá zpráva? Aspose.Words vám poskytuje čistý způsob, jak tyto problémy odhalit pomocí warning callbacku. V tomto tutoriálu uvidíte **jak použít callback** k zachycení každé náhrady písma, kterou Aspose provádí při načítání dokumentu, a získáte připravený příklad, který vytiskne přehled chybějících písem.

Budeme pokrývat:

* Minimální předpoklady (projekt .NET a NuGet balíček Aspose.Words).  
* Jak implementovat `IWarningCallback` pro naslouchání `WarningType.FontSubstitution`.  
* Jak zapojit callback do `LoadOptions` a načíst dokument.  
* Jak vypadá výstup, plus několik praktických tipů pro produkční kód.

Na konci budete schopni automaticky **detekovat písma** v libovolném souboru DOCX, DOC nebo RTF a reagovat na informace o chybějících písmenech—ať už to znamená logování, upozornění uživatele nebo nahrazení náhradním písmem.

---

![Jak detekovat písma v dokumentu Word pomocí warning callbacku Aspose.Words](https://example.com/images/detect-fonts.png "jak detekovat písma v dokumentu Word")

## Co budete potřebovat

* **.NET 6.0** nebo novější (příklad se také kompiluje s .NET Framework 4.6+).  
* **Aspose.Words for .NET** – nainstalujte přes NuGet: `Install-Package Aspose.Words`.  
* Ukázkový soubor Word, který úmyslně odkazuje na písmo, které nemáte nainstalované (např. `MissingFont.docx`).  

Žádné další knihovny nejsou potřeba; vše žije v rámci jmenného prostoru Aspose.

---

## Jak detekovat písma pomocí warning callbacku

### Krok 1: Vytvořte třídu warning‑callbacku

Callback implementuje `IWarningCallback`. Když Aspose.Words narazí na písmo, které nemůže najít, vyvolá `WarningInfo` s `WarningType.FontSubstitution`. Naše třída jednoduše zapíše přátelský řádek do konzole.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Proč je to důležité:** Filtrováním na `WarningType.FontSubstitution` se vyhneme hlučným varováním (např. zastaralé funkce) a udržujeme log zaměřený na konkrétní problém, který se snažíte vyřešit—**detekci písem**, která nejsou na stroji přítomna.

### Krok 2: Připojte callback do `LoadOptions`

`LoadOptions` vám umožňuje přizpůsobit, jak se dokument parsuje. Přiřazením našeho `FontWarningCollector` k vlastnosti `WarningCallback` řeknete Aspose, aby jej volal vždy, když narazí na chybějící písmo.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Tip:** Můžete zde také nastavit `LoadOptions.FontSettings`, pokud chcete programově poskytnout náhradní písmo. To je pokročilý scénář, který zmíníme později.

### Krok 3: Načtěte dokument a sledujte výstup

Nyní skutečně načteme soubor. Jakmile Aspose parsuje dokument, každé písmo, které nemůže najít, spustí náš callback.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Očekávaný výstup v konzoli** (předpokládáme, že dokument odkazuje na *Comic Sans MS*, které není nainstalováno):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Pokud dokument obsahuje více chybějících písem, uvidíte jeden řádek pro každé písmo—přesně informace **jak detekovat písma**, které potřebujete.

## Jak použít callback pro složitější scénáře

### Logování do souboru místo konzole

V produkci pravděpodobně chcete trvalý log. Vyměňte `Console.WriteLine` za `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Shromažďování varování pro pozdější analýzu

Někdy potřebujete seznam chybějících písem po načtení dokumentu, třeba pro zobrazení UI dialogu. Uložte varování do `List<string>` a zpřístupněte je:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Poskytnutí náhradního písma programově

Pokud máte firemní písmo, které chcete vynutit, můžete jej přidat do `FontSettings` před načtením:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Nyní Aspose nahradí chybějící písma *Arial Unicode MS*, přičemž stále hlásí náhradu přes callback. To je šikovný způsob, jak **použít callback** jak pro detekci, tak pro automatické řešení.

## Časté úskalí a profesionální tipy

| Úskalí | Proč se to stane | Jak se vyhnout |
|--------|------------------|----------------|
| **Zapomenutí referencovat `Aspose.Words.Warnings`** | Rozhraní `IWarningCallback` se nachází tam. | Přidejte `using Aspose.Words.Warnings;` na začátek. |
| **Načtení dokumentu bez `LoadOptions`** | Výchozí načítač tiše nahrazuje písma bez upozornění. | Vždy vytvořte instanci `LoadOptions` a přiřaďte svůj callback. |
| **Spuštění na serveru s omezenými oprávněními** | Zápis do souboru logu může vyvolat `UnauthorizedAccessException`. | Použijte zapisovatelnou složku (např. datový adresář aplikace) nebo se držte kolekcí v paměti. |
| **Více vláken sdílejících stejný collector** | `FontWarningCollector` není ve výchozím nastavení thread‑safe. | Vytvořte samostatný collector pro každé vlákno nebo chráněte seznam zámkem. |
| **Předpokládání, že callback se spustí pro vložená písma** | Vložená písma jsou již v dokumentu přítomna; žádné varování není vyvoláno. | Pokud potřebujete ověřit integritu vložených písem, prozkoumejte `FontInfo` přes `FontSettings`. |

## Kompletní funkční příklad (připravený ke zkopírování)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Co byste měli vidět** (předpokládáme, že soubor odkazuje na dvě chybějící písma):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Pokud soubor používá jen nainstalovaná písma, konzole jednoduše vypíše:

```
Document loaded successfully.

No missing fonts detected.
```

## Závěr

Prošli jsme **jak detekovat písma** v dokumentu Word pomocí připojení vlastního warning callbacku do Aspose.Words. Přístup je nenáročný, vyžaduje

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}