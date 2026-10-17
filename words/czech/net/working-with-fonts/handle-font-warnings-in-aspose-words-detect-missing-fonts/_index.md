---
category: general
date: 2026-02-28
description: Naučte se, jak zpracovávat varování o písmu a detekovat chybějící písma
  v Aspose.Words pomocí C#. Kompletní krok‑za‑krokem průvodce s úplným kódem.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: cs
og_description: Zpracujte varování o písmu v Aspose.Words a detekujte chybějící písma
  pomocí připraveného C# příkladu. Postupujte podle kroků a podívejte se na výstup.
og_title: Zpracování upozornění na písma v Aspose.Words – Kompletní průvodce
tags:
- Aspose.Words
- C#
- Document Loading
title: Zpracování varování o písmu v Aspose.Words – Detekce chybějících písem
url: /cs/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zpracování varování o písmu v Aspose.Words – Detekce chybějících písem

Už jste někdy potřebovali **zpracovat varování o písmu** při načítání dokumentu Word a přemýšleli, proč některý text vypadá podivně? Nejste v tom sami. Chybějící písma spouštějí varování o substituci, která mohou tiše narušit vizuální rozvržení, a pokud **nedetekujete chybějící písma**, nikdy se nedozvíte, co se pokazilo.

V tomto tutoriálu vám ukážeme praktický způsob, jak **zpracovat varování o písmu** pomocí `IWarningCallback` z Aspose.Words. Na konci průvodce budete schopni zachytit každou událost substituce písma, zaznamenat ji a dokonce se rozhodnout, zda načítání přerušit. Žádná externí dokumentace, jen jeden připravený příklad ke zkopírování.

## Co se naučíte

- Nastavte vlastní obslužnou rutinu varování, která reaguje pouze na upozornění o substituci písma.  
- Připojte tuto rutinu k `LoadOptions`, aby každé načtení dokumentu procházelo skrz ni.  
- Ověřte výstup v konzoli a pochopte, co každé varování znamená.  

**Požadavky**

- .NET 6.0 nebo novější (kód funguje také s .NET Framework 4.6+).  
- Aspose.Words pro .NET nainstalovaný přes NuGet (`Install-Package Aspose.Words`).  
- Soubor Word, který odkazuje na písmo, které není nainstalováno na vašem počítači (např. vlastní firemní písmo).  

Pokud vám něco chybí, pořiďte si to hned—jinak pojďme na to.

## Jak zpracovat varování o písmu v Aspose.Words

Níže je kompletní spustitelný program. Obsahuje vše od `using` direktiv po metodu `Main`, takže jej můžete vložit do konzolové aplikace a stisknout **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Očekávaný výstup v konzoli** (předpokládáme, že dokument používá písmo, které nemáte nainstalováno):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Pokud dokument neobsahuje **žádná chybějící písma**, řádek s varováním se nikdy neobjeví—takže jste efektivně **detekovali chybějící písma** jen když to bylo potřeba.

### Proč to funguje

Aspose.Words vyhodí `WarningInfo` pro každý nekritický problém, na který narazí při parsování souboru. Implementací `IWarningCallback` získáte háček do tohoto zpracování. Příznak `WarningType.FontSubstitution` vám přesně říká, kdy knihovna musela nahradit požadované písmo náhradním. Toto je nejspolehlivější způsob, jak **zpracovat varování o písmu**, protože běží *během* načítání, ještě předtím, než se dotknete objektového modelu dokumentu.

## Detekce chybějících písem bez narušení aplikace

Někdy můžete chtít považovat chybějící písmo za fatální chybu—možná vaše brandingové směrnice zakazují jakoukoli substituci. Můžete upravit obslužnou rutinu tak, aby místo pouhého logování vyhodila výjimku:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Nyní blok `try…catch` kolem `new Document(...)` zachytí problém, což vám umožní rozhodnout, zda načítání přerušit, použít náhradní řešení nebo vyzvat uživatele.

## Bonus: Vizualizace varování v UI aplikaci

Pokud vytváříte aplikaci WinForms nebo WPF, nahraďte `Console.WriteLine` voláním vhodným pro UI:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

Tímto způsobem uživatelé okamžitě uvidí varování a vy stále **zpracováváte varování o písmu** konzistentně napříč všemi platformami.

## Časté úskalí a tipy

- **Pitfall:** Zapomenutí nastavit `WarningCallback`. Výchozí chování je ignorovat varování o písmu, takže je nikdy neuvidíte.  
  **Pro tip:** Vždy vytvořte instanci `LoadOptions`, i když potřebujete jen obslužnou rutinu varování. Je to levné a explicitní.  

- **Pitfall:** Použití nesprávného oddělovače cesty na ne‑Windows OS.  
  **Pro tip:** Používejte `Path.Combine` nebo surový řetězec (`@"C:\Docs\MissingFont.docx"` funguje na Windows; na Linuxu použijte `"/home/user/docs/MissingFont.docx"`).  

- **Pitfall:** Předpoklad, že varování se spustí i pro vložená písma.  
  **Pro tip:** Vložená písma jsou považována za přítomná, takže se neobjeví varování o substituci. Testujte s opravdu *chybějícími* písmy, abyste viděli obslužnou rutinu v akci.  

- **Pitfall:** Přehnané logování všech typů varování.  
  **Pro tip:** Filtrujte podle `WarningType.FontSubstitution`, jak je ukázáno—tím udržíte konzoli čistou a zaměříte se na scénář **detekce chybějících písem**.  

## Shrnutí kompletního funkčního příkladu

Zde je celý program znovu, tentokrát bez komentářů pro ty, kteří preferují čistý pohled:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Zkopírujte, vložte, spusťte—vaše konzole nyní automaticky **zpracuje varování o písmu** a **detekuje chybějící písma**.

## Další kroky

- **Log to a file:** Nahraďte `Console.WriteLine` loggerem (např. NLog) pro produkční sledování.  
- **Batch processing:** Projděte složku s dokumenty a sbírejte všechny události substituce písma do CSV zprávy.  
- **Automatic font installation:** Připojte se k obslužné rutině varování, aby stáhla chybějící písma z firemního repozitáře před pokračováním načítání.  

Každé z těchto rozšíření staví na základní myšlence **zpracování varování o písmu** čistým a znovupoužitelným způsobem.

---

*Šťastné kódování! Pokud narazíte na nějaké podivnosti při pokusu **detekovat chybějící písma**, zanechte komentář níže. Rád vám pomohu s řešením.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}