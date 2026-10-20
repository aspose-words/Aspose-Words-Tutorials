---
category: general
date: 2026-04-21
description: Naučte se, jak detekovat písma, zachytávat varování, nastavit callback
  a vyjmenovávat varování pomocí Aspose.Words v C#. Krok za krokem průvodce spolehlivou
  správou písem.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: cs
og_description: Jak detekovat fonty v Aspose.Words? Tento tutoriál vám ukáže, jak
  zachytit varování, nastavit zpětné volání a vypsat varování v C#.
og_title: Jak detekovat písma v Aspose.Words – kompletní průvodce
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak detekovat písma v Aspose.Words – kompletní průvodce
url: /cs/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak detekovat písma v Aspose.Words – Kompletní průvodce

Už jste se někdy zamysleli, **jak detekovat písma**, která chybí při načítání Word dokumentu? Jedná se o situaci, která se objevuje častěji, než byste si přáli, zejména při práci se staršími soubory nebo při nasazení napříč platformami. V tomto tutoriálu projdeme kompletním, spustitelným příkladem, který **zachytává varování**, **konfiguruje callback** a **vypisuje varování**, takže vždy budete vědět, která písma byla nahrazena.

Budeme používat Aspose.Words pro .NET (v24.9 v době psaní) a čistý C#. Žádné externí služby, žádná magie — pouze API a pár řádků kódu. Na konci budete schopni odhalit každou substituci písma, zaznamenat ji a dokonce se rozhodnout, zda načítání přerušit, pokud chybí kritické písmo.

### Co budete potřebovat
- **Aspose.Words pro .NET** (instalace přes NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 nebo novější (kód funguje i na .NET Framework)
- Ukázkový DOCX, který odkazuje na písmo, jež není nainstalováno na počítači (např. „MyCustomFont.ttf“)
- Visual Studio, Rider nebo jakýkoli C# editor, který preferujete

> **Tip:** Pokud nemáte dokument s chybějícími písmy, jednoduše přejmenujte soubor písma ve vašem systému nebo upravte XML v DOCX tak, aby odkazovalo na neexistující rodinu písma.

---

## Jak detekovat písma pomocí Aspose.Words

Základní myšlenkou je napojit se na systém varování Aspose.Words. Když knihovna nenajde požadované písmo, vygeneruje varování typu `WarningType.FontSubstitution`. Poskytnutím vlastní implementace `IWarningCallback` můžete **detekovat písma**, která byla během načítání vyměněna.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Proč to funguje:** Aspose.Words volá metodu `Warning` pro každou nekritickou událost. Ukládáním objektů `WarningInfo` získáte plný přístup k typu, zprávě i kontextu, což je přesně to, co potřebujete k **detekci písma**, které bylo substituováno.

---

## Jak zachytit varování při načítání dokumentu

Nyní, když máme sběrač, musíme `LoadOptions` nastavit tak, aby jej používal. Toto je část, kde **zachytáváme varování**.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Hraniční případ:** Pokud načítáte dokument ze streamu (`new Document(stream, loadOptions)`), stejný callback funguje — stačí předat stream místo cesty k souboru.

V tomto okamžiku je dokument plně načten, ale všechna varování o substituci písma jsou bezpečně uložena v `warningCollector.Warnings`.

---

## Jak procházet varování a reportovat substituce písma

Nakonec projdeme shromážděná varování a **projdeme varování**, která se konkrétně týkají substituce písma. Tento krok převádí surová data na čitelnou zprávu.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Očekávaný výstup** (příklad):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Pokud dokument neobsahuje žádná chybějící písma, smyčka jednoduše nevytiskne žádný výstup — není co řešit.

---

## Kompletní funkční příklad (všechny kroky v jednom souboru)

Níže je kompletní program, který můžete zkopírovat a vložit do konzolového projektu. Spojuje **detekci písem**, **zachycení varování**, **konfiguraci callbacku** a **procházení varování** v jedné koherentní sekvenci.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Spuštěním tohoto programu** vytisknete každé písmo, které Aspose.Words muselo nahradit. Výstup můžete přesměrovat do souboru s logem, vyvolat upozornění nebo dokonce přerušit načítání, pokud chybí kritické písmo.

---

## Často kladené otázky a úskalí

### Co když potřebuji zastavit načítání, když chybí požadované písmo?
Můžete v callbacku prozkoumat objekty `WarningInfo` a vyhodit výjimku, když se objeví konkrétní název písma. Výjimka přeruší načítání a získáte tak plnou kontrolu.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Funguje to i s PDF nebo jinými formáty?
Ano. Aspose.Words používá stejnou infrastrukturu varování pro PDF, RTF i HTML. Stačí změnit příponu souboru a zbytek kódu zůstane stejný.

### Jak mohu varování logovat do souboru místo na konzoli?
Nahraďte `Console.WriteLine` libovolným logovacím frameworkem, který preferujete (`Serilog`, `NLog` atd.). Třída `WarningInfo` poskytuje `Message`, `Source` a `Exception` pro podrobné logy.

### Ovlivní to výkon?
Zátěž je zanedbatelná — Aspose.Words už interně generuje varování. Přidání callbacku jen ukládá varování do seznamu, což je O(n) vzhledem k počtu varování. Pro typické dokumenty je dopad výrazně pod 1 % celkové doby načítání.

---

## Vizualizace

![Jak detekovat písma v Aspose.Words – diagram toku varování](https://example.com/images/font-detection-diagram.png "jak detekovat písma")

*Alt text:* **jak detekovat písma** – diagram zobrazující kroky callbacku varování, sběru a procházení.

---

## Závěr

Probrali jsme **jak detekovat písma** v Aspose.Words pomocí **zachycení varování**, **konfigurace callbacku** a **procházení varování**. Kompletní ukázkový kód představuje produkčně připravený vzor, který můžete vložit do libovolné .NET aplikace.  

Dále můžete zkusit:

- **Zachytit varování** pro jiné problémy (např. problémy s konverzí obrázků)
- **Konfigurovat callback** pro vlastní logovací frameworky
- **Procházet varování** napříč více dokumenty v dávkovém zpracování
- Použít **Aspose.Words.Fonts.FontSettings** k nastavení složek s náhradními písmy, což může snížit počet substitucí již na začátku.

Vyzkoušejte to, upravte sběrač podle svého stylu logování a už vás nikdy nepřekvapí nečekaná výměna písma. Pokud narazíte na nějaké problémy, zanechte komentář níže — šťastné kódování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}