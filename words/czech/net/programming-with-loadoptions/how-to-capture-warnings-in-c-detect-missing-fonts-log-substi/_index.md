---
category: general
date: 2026-04-04
description: Naučte se, jak zachytit varování, detekovat chybějící písma a jak zaznamenávat
  události nahrazení pomocí Aspose.Words LoadOptions v C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: cs
og_description: Jak zachytit varování, detekovat chybějící písma a zaznamenávat události
  nahrazení pomocí Aspose.Words LoadOptions v C#.
og_title: Jak zachytit varování v C# – detekovat chybějící fonty a zaznamenávat substituce
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Jak zachytit varování v C# – detekovat chybějící písma a zaznamenat substituci
url: /cs/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak zachytit varování v C# – Detekce chybějících fontů a logování náhrad

Už jste se někdy zamýšleli **jak zachytit varování**, která se objeví při načítání Word dokumentu s chybějícími fonty? Nejste v tom sami. V mnoha reálných projektech se fonty během migrace ztratí a tichá náhrada může rozbít rozvržení. Dobrá zpráva? Aspose.Words vám poskytuje čistý způsob, jak naslouchat těmto varováním, detekovat chybějící fonty a dokonce zaznamenat každou náhradu, abyste mohli zdroj později opravit.

V tomto tutoriálu projdeme kompletní, připravené řešení, které ukazuje **jak zachytit varování**, demonstruje **detekci chybějících fontů** a vysvětluje **jak logovat události náhrady**. Na konci budete mít znovupoužitelný handler varování, plně nakonfigurovaný objekt `LoadOptions` a ukázkový výstup v konzoli, který můžete ověřit.

> **Předpoklad:** Potřebujete Aspose.Words pro .NET (v24.x nebo novější) nainstalovaný přes NuGet a základní vývojové prostředí C# (Visual Studio 2022 nebo VS Code jsou v pořádku).

---

## Jak zachytit varování při načítání dokumentů

Jádrem řešení je třída, která implementuje `IWarningCallback`. Aspose.Words volá tento callback automaticky pro každé varování generované během načítání dokumentu, včetně varování o náhradě fontů.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Proč tento krok?**  
> Filtrací na `WarningType.FontSubstitution` se vyhneme nepořádku od nesouvisejících varování (např. zastaralých funkcí). To zaměří log na přesný problém, který vás zajímá — chybějící fonty.

---

## Detekce chybějících fontů s Aspose.Words

Když dokument odkazuje na font, který není nainstalován na počítači, Aspose.Words nahradí nejbližší shodou a vyvolá varování. Náš výše uvedený handler zachytí každou takovou událost a efektivně **detekuje chybějící fonty**.

Abychom to viděli v akci, musíme nakonfigurovat `LoadOptions` a připojit handler:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tip:** Pokud raději sbíráte varování pro pozdější zpracování (např. zápis do souboru), nahraďte `Console.WriteLine` kódem, který přidá zprávu do `List<string>`.

---

## Jak logovat události náhrady

Logování je tak jednoduché, jako nasměrovat výstup varování do trvalého úložiště. Níže je rychlý příklad, který zapisuje každé varování o náhradě do textového souboru `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Proč logovat do souboru?**  
> Trvalé logy vám umožní auditovat problémy s fonty napříč více spuštěními, automatizovat upozornění nebo předat data do kontroly v build‑pipeline.

---

## Kompletní funkční příklad

Spojením všech částí získáte samostatnou konzolovou aplikaci, kterou můžete zkopírovat, vložit a spustit. Demonstruje **jak zachytit varování**, **detekovat chybějící fonty** a **jak logovat náhrady** najednou.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Očekávaný výstup v konzoli

Pokud `input.docx` odkazuje na font, který není nainstalován, uvidíte něco jako:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Pokud přepnete na `FileLoggingWarningHandler`, stejné řádky se objeví v souboru `font-warnings.log` s časovými razítky.

![ukázka výstupu zachycení varování v konzoli](image-placeholder.png)

---

## Časté otázky a okrajové případy

### Co když potřebuji zachytit *všechna* varování, nejen náhrady fontů?

Jednoduše odstraňte podmínku `if (info.Type == WarningType.FontSubstitution)`. Callback obdrží každý typ varování (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent` atd.). Pak můžete podle `info.Type` rozvětvit zpracování jednotlivých případů.

### Funguje to s PDF nebo jen s Word dokumenty?

`LoadOptions` a `IWarningCallback` jsou součástí Aspose.Words, takže se vztahují na formáty kompatibilní s Wordem (`.docx`, `.doc`, `.rtf`, `.html`). Pro PDF byste použili varovné mechanismy Aspose.PDF.

### Jak mohu varování potlačit místo jejich logování?

Nastavte `LoadOptions.WarningCallback = null` nebo implementujte callback, ale nechte tělo metody prázdné. Knihovna i nadále provede náhradu tiše.

### Co s bezpečností vláken?

Instance callbacku je volána ve stejném vlákně, které načítá dokument, takže není potřeba další synchronizace, pokud handler nesdílíte mezi paralelními načítáními. V takovém případě chraňte sdílené zdroje (např. soubor logu) pomocí zámku nebo použijte souběžné kolekce.

---

## Závěr

Probrali jsme **jak zachytit varování** z Aspose.Words, ukázali vám **jak detekovat chybějící fonty** a vysvětlili **jak logovat události náhrady** pro pozdější analýzu. Připojením jednoduché implementace `IWarningCallback` do `LoadOptions` získáte plnou přehlednost o problémech souvisejících s fonty, aniž byste zaplňovali kód zbytečným šumem.

Další kroky? Zkuste rozšířit logger tak, aby posílal e‑maily, integroval se s Azure Monitor nebo automaticky instaloval chybějící fonty na build serveru. Můžete také prozkoumat další typy varování — `WarningType.DegradedDocument` vás může upozornit na funkce, které nepřežily konverzi.

Máte další otázky ohledně správy fontů nebo Aspose.Words obecně? Zanechte komentář nebo otevřete nové téma na fóru Aspose. Šťastné programování a ať se vaše dokumenty vždy vykreslují s správným typem písma!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}