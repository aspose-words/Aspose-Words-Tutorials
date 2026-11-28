---
category: general
date: 2026-03-30
description: Zkontrolujte počet stránek ve Wordových dokumentech, zatímco se učíte
  obnovovat poškozený soubor Word a detekovat poškozený soubor Word pomocí Aspose.Words.
draft: false
keywords:
- check page count
- recover corrupted word file
- detect corrupted word file
- Aspose.Words
- C# document loading
language: cs
og_description: Zkontrolujte počet stránek v dokumentech Word a zjistěte, jak obnovit
  poškozený soubor Word pomocí Aspose.Words. Krok za krokem tutoriál v C#.
og_title: Zkontrolujte počet stránek v dokumentech Word – kompletní průvodce
tags:
- Aspose.Words
- C#
- document processing
title: Zkontrolujte počet stránek ve Word dokumentech – Obnovte poškozené soubory
url: /cs/net/programming-with-document-properties/check-page-count-in-word-docs-recover-corrupted-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zkontrolujte počet stránek v dokumentech Word – Obnovte poškozené soubory

Už jste někdy potřebovali **zkontrolovat počet stránek** v dokumentu Word, ale nebyli jste si jisti, zda je soubor stále v pořádku? Nejste v tom sami. V mnoha automatizačních pipelinech je první věc, kterou děláme, ověření délky dokumentu, a zároveň často musíme **detekovat poškozený soubor Word** před tím, než celý proces spadne.  

V tomto tutoriálu projdeme kompletním, spustitelným příkladem v C#, který vám ukáže, jak **zkontrolovat počet stránek**, a zároveň demonstruje nejlepší způsob, jak **obnovit poškozený soubor Word** pomocí Aspose.Words LoadOptions. Na konci přesně pochopíte, proč má každé nastavení význam, jak zacházet s okrajovými případy a na co se zaměřit, když se soubor odmítá otevřít.

---

## Co se naučíte

- Jak nakonfigurovat `LoadOptions` pro **detekci poškozeného souboru Word** problémů.
- Rozdíl mezi `RecoveryMode.Strict` a `RecoveryMode.Auto`.
- Spolehlivý vzor pro načtení dokumentu a bezpečnou **kontrolu počtu stránek**.
- Běžné úskalí (chybějící soubor, chyby oprávnění, neočekávaný formát) a jak se jim vyhnout.
- Úplný, připravený k zkopírování a vložení kódový příklad, který můžete spustit ještě dnes.

> **Požadavky**: .NET 6+ (nebo .NET Framework 4.7+), Visual Studio 2022 (nebo jakékoli C# IDE) a licence Aspose.Words pro .NET (bezplatná zkušební verze funguje pro tuto ukázku).

---

## Krok 1 – Instalace Aspose.Words

Nejprve potřebujete balíček Aspose.Words NuGet. Otevřete terminál ve složce projektu a spusťte:

```bash
dotnet add package Aspose.Words
```

Tento jediný příkaz stáhne vše, co potřebujete — žádné další hledání DLL souborů není nutné. Pokud používáte Visual Studio, můžete také instalovat přes UI Správce balíčků NuGet.

---

## Krok 2 – Nastavení LoadOptions pro **detekci poškozeného souboru Word**

Jádrem řešení je třída `LoadOptions`. Umožňuje vám říci Aspose.Words, jak přísná má být, když narazí na problematický soubor.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Choose a recovery strategy.
// Strict → throws an exception the moment corruption is spotted.
// Auto   → tries to salvage what it can and keeps loading.
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Strict   // <‑‑ change to Auto if you prefer auto‑recovery
};
```

**Proč je to důležité**: Pokud necháte knihovnu tiše hádat, můžete skončit s dokumentem, který postrádá stránky — což činí jakoukoli následnou operaci **kontroly počtu stránek** nespolehlivou. Použití `Strict` vás nutí problém řešit hned na začátku, což je bezpečnější volba pro produkční pipeline.

---

## Krok 3 – Načtení dokumentu a **kontrola počtu stránek**

Nyní skutečně otevřeme soubor. Konstruktor `Document` přijímá cestu a `LoadOptions`, které jsme právě nakonfigurovali.

```csharp
try
{
    // Replace the placeholder with the real path to your .docx file.
    const string filePath = @"C:\Docs\maybeCorrupt.docx";

    // Load the document using the strict recovery mode we set above.
    Document doc = new Document(filePath, loadOptions);

    // If we reach this line, the file is considered healthy enough.
    Console.WriteLine($"✅ Document loaded successfully. Page count: {doc.PageCount}");

    // You can now safely use the page count for any downstream logic.
    // Example: abort processing if the document is unexpectedly short.
    if (doc.PageCount < 2)
    {
        Console.WriteLine("⚠️ Document seems too short – double‑check the source.");
    }
}
catch (Exception ex) when (ex is FileCorruptedException || ex is LoadOptionsException)
{
    // This block runs only when Strict mode catches corruption.
    Console.WriteLine($"❌ Failed to load document: {ex.Message}");
    // Optional: switch to Auto mode on the fly, then retry.
    loadOptions.RecoveryMode = RecoveryMode.Auto;
    Console.WriteLine("🔄 Retrying with Auto recovery mode…");
    // Recursive retry is omitted for brevity—see Step 5 for a reusable method.
}
```

**Co vidíte**:

- Vzor `try/catch` vám poskytuje čistý způsob, jak **detekovat poškozený soubor Word** situace.
- `doc.PageCount` je vlastnost, která skutečně **kontroluje počet stránek**.
- Podmínka po `Console.WriteLine` ukazuje realistický scénář, kdy můžete ukončit, pokud je dokument nečekaně krátký.

---

## Krok 4 – Elegantní zpracování okrajových případů

Kód v reálném světě se zřídka spouští ve vakuu. Níže jsou tři běžné scénáře „co‑když“ a jak je řešit.

### 4.1 Soubor nenalezen

```csharp
if (!File.Exists(filePath))
{
    Console.WriteLine($"❗ File not found: {filePath}");
    return; // Bail out early – nothing to load.
}
```

### 4.2 Nedostatečná oprávnění

```csharp
try
{
    // Attempt to open with read‑only sharing.
    using var stream = new FileStream(filePath, FileMode.Open, FileAccess.Read, FileShare.Read);
    Document doc = new Document(stream, loadOptions);
    Console.WriteLine($"📄 Page count: {doc.PageCount}");
}
catch (UnauthorizedAccessException)
{
    Console.WriteLine("🔐 You don’t have permission to read this file.");
}
```

### 4.3 Záložní automatické obnovení

Pokud se rozhodnete, že tiché zachránění souboru je přijatelné, zabalte automatické obnovení do pomocné metody:

```csharp
static Document LoadWithFallback(string path)
{
    var options = new LoadOptions { RecoveryMode = RecoveryMode.Strict };
    try
    {
        return new Document(path, options);
    }
    catch
    {
        // Switch to Auto and try again.
        options.RecoveryMode = RecoveryMode.Auto;
        return new Document(path, options);
    }
}
```

Nyní máte jediný řádek `Document doc = LoadWithFallback(filePath);`, který vždy vrátí instanci `Document` — buď čistou, nebo co nejlépe obnovenou.

---

## Krok 5 – Kompletní funkční příklad (připravený ke kopírování a vložení)

Níže je celý program, připravený vložit do projektu konzolové aplikace. Obsahuje všechny tipy z předchozích kroků.

```csharp
// ------------------------------------------------------------
// Check Page Count in Word Docs – Recover Corrupted Files
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        const string filePath = @"C:\Docs\maybeCorrupt.docx";

        // 1️⃣ Verify the file exists.
        if (!File.Exists(filePath))
        {
            Console.WriteLine($"❗ File not found: {filePath}");
            return;
        }

        // 2️⃣ Try loading with strict recovery mode.
        Document doc = LoadDocument(filePath, RecoveryMode.Strict);

        // 3️⃣ If we have a document, we can safely check page count.
        Console.WriteLine($"✅ Document loaded. Page count: {doc.PageCount}");

        // 4️⃣ Example business rule – abort if too few pages.
        if (doc.PageCount < 2)
        {
            Console.WriteLine("⚠️ Document seems too short – investigate the source file.");
        }
    }

    /// <summary>
    /// Loads a Word document using the specified recovery mode.
    /// Falls back to Auto mode if Strict fails.
    /// </summary>
    static Document LoadDocument(string path, RecoveryMode mode)
    {
        var options = new LoadOptions { RecoveryMode = mode };

        try
        {
            return new Document(path, options);
        }
        catch (Exception ex) when (ex is FileCorruptedException || ex is LoadOptionsException)
        {
            Console.WriteLine($"❌ Strict mode failed: {ex.Message}");
            Console.WriteLine("🔄 Switching to Auto recovery mode…");
            options.RecoveryMode = RecoveryMode.Auto;
            return new Document(path, options); // Auto will attempt to salvage.
        }
    }
}
```

**Očekávaný výstup (zdravý soubor)**:

```
✅ Document loaded. Page count: 12
```

**Očekávaný výstup (poškozený soubor, přísný režim)**:

```
❌ Strict mode failed: The file is corrupted and cannot be opened.
🔄 Switching to Auto recovery mode…
✅ Document loaded. Page count: 8   // Might be less than original.
```

---

## Krok 6 – Profesionální tipy a běžné úskalí

- **Pro tip:** Vždy zaznamenejte použité `RecoveryMode`. Když později auditujete dávkové spuštění, budete vědět, které soubory byly automaticky obnoveny.
- **Dejte pozor na:** Dokumenty, které obsahují vložené objekty (grafy, SmartArt). Automatický režim je může odstranit, což může ovlivnit rozvržení stránky a tím i výsledek **kontroly počtu stránek**.
- **Poznámka k výkonu:** `RecoveryMode.Auto` je o něco pomalejší, protože Aspose.Words provádí další validační průchody. Pokud zpracováváte tisíce souborů, držte se `Strict` a přecházejte na automatické obnovení jen na úrovni jednotlivých souborů.
- **Kontrola verze:** Výše uvedený kód funguje s Aspose.Words 22.12 a novějšími. Starší verze měly jiný název výčtu (`LoadOptions.RecoveryMode` byl zaveden v 20.10).

---

## Závěr

Nyní máte solidní, připravený pro produkci vzor pro **kontrolu počtu stránek** v dokumentech Word a zároveň jste se naučili, jak **obnovit poškozený soubor Word** a **detekovat poškozený soubor Word** pomocí Aspose.Words. Hlavní body jsou:

1. Nakonfigurujte `LoadOptions` s odpovídajícím `RecoveryMode`.
2. Zabalte načítání do `try/catch`, aby se poškození odhalilo brzy.
3. Použijte vlastnost `PageCount` jako definitivní zdroj počtu stránek.
4. Implementujte elegantní záložní řešení (automatické obnovení, handling oprávnění, kontrola existence souboru).

Odtud můžete dále zkoumat:

- Extrakci textu z každé stránky (`doc.GetText()` s rozsahem stránek).
- Převod dokumentu do PDF po potvrzení počtu stránek.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}