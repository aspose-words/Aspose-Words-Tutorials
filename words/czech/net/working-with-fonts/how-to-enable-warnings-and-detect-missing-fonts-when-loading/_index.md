---
category: general
date: 2026-02-21
description: Naučte se, jak povolit varování, detekovat chybějící písma a jak bezpečně
  načíst soubor docx pomocí Aspose.Words v C#. Postupujte podle krok‑za‑krokem průvodce.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: cs
og_description: Jak povolit varování, detekovat chybějící písma a správně načíst soubory
  DOCX pomocí Aspose.Words. Kompletní ukázkový kód je zahrnut.
og_title: Jak povolit varování a detekovat chybějící písma při načítání DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Jak povolit varování a detekovat chybějící písma při načítání souborů DOCX
url: /cs/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak povolit varování a detekovat chybějící písma při načítání souborů DOCX

Už jste se někdy zamýšleli **jak povolit varování** pro chybějící písma, než tiše naruší vykreslování vašeho dokumentu? Nejste sami – většina vývojářů předpokládá, že knihovna prostě „udělá to správně“, až později zjistí, že písmo bylo vyměněno bez jakéhokoli náznaku.  

V tomto tutoriálu vám ukážeme přesně **jak povolit varování**, jak **detekovat chybějící písma** a správný způsob **jak načíst docx** pomocí Aspose.Words pro .NET. Na konci budete mít připravený ukázkový program, který vypíše každé varování o náhradě písma do konzole, takže už nebudete hádat, co se v souboru stalo.

## Požadavky

- .NET 6.0 nebo novější (kód funguje také na .NET Framework 4.7+)  
- Visual Studio 2022 nebo jakékoli C# IDE, které preferujete  
- NuGet balíček **Aspose.Words** (`Install-Package Aspose.Words`)  
- Soubor DOCX, který může obsahovat písma neinstalovaná na vašem počítači (budeme ho nazývat `input.docx`)

> **Pro tip:** Pokud nemáte testovací soubor, stačí otevřít Word dokument, který používá vlastní firemní písmo, a uložit jej jako `input.docx`. To spustí varování, které chceme zachytit.

## Přehled řešení

1. **Vytvořit** objekt `LoadOptions` s povoleným `FontSubstitutionWarnings`.  
2. **Načíst** soubor DOCX pomocí těchto možností.  
3. **Prozkoumat** kolekci `WarningCallback` na případné položky `FontSubstitution`.  
4. **Reagovat** – můžete zaznamenávat, zobrazovat nebo dokonce programově nahradit chybějící písmo.

Níže rozebíráme každý krok, vysvětlujeme *proč* je důležitý, a poskytujeme kompletní spustitelný úryvek kódu.

---

## Krok 1: Nainstalujte Aspose.Words a nastavte projekt

Než budeme moci **jak povolit varování**, potřebujeme knihovnu, která je skutečně podporuje.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Or, in the Visual Studio Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Proč tento krok?**  
> Bez balíčku neexistují třídy `LoadOptions`, `Document` ani infrastruktura varování. Přidání odkazu na NuGet zajišťuje, že získáte nejnovější stabilní verzi (k datu psaní 24.5).

---

## Krok 2: Vytvořte možnosti načtení, které povolují varování o náhradě písma

Jádro **jak povolit varování** se nachází ve třídě `LoadOptions`. Nastavením `FontSubstitutionWarnings` na `true` řeknete enginu, aby zaznamenával každou výměnu chybějícího písma.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Proč povolit tento příznak?**  
> Ve výchozím nastavení Aspose.Words tiše nahrazuje chybějící písma náhradním (obvykle Arial). To může vést k posunům rozvržení, neviditelným znakům nebo porušení značky. Zapnutím příznaku získáte úplnou přehlednost.

---

## Krok 3: Načtěte soubor DOCX pomocí nakonfigurovaných možností

Nyní, když víme **jak načíst docx** s povolenými varováními, skutečně provedeme načtení.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Co se děje pod kapotou?**  
> Při parsování DOCX Aspose.Words kontroluje každý prvek `<w:rFonts>`. Pokud není uvedené písmo nainstalováno, zaznamená varování `FontSubstitution` a použije výchozí písmo. Protože jsme povolili varování, tyto položky skončí v `document.WarningCallback.Warnings`.

---

## Krok 4: Získejte a zobrazte varování o náhradě písma

Vlastnost `WarningCallback` obsahuje `WarningInfoCollection`. Projděte ji v cyklu, filtrujte podle `WarningType.FontSubstitution` a vypište zprávy.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Expected output** (example):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Co dělat s těmito zprávami?**  
> Můžete je zaznamenat do souboru, zobrazit v uživatelském rozhraní nebo dokonce spustit vlastní rutinu náhrady písma. Klíčové je, že nyní *detekujete chybějící písma* místo hádání později.

---

## Krok 5: (Volitelné) Nahradit chybějící písma konkrétní náhradou

Pokud máte firemní písmo, které chcete vynutit, můžete varování zpracovat a nahradit je za běhu.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Proč to zvažovat?**  
> Zajišťuje vizuální konzistenci ve všech generovaných dokumentech, což je klíčové pro dodržování značky.

---

## Kompletní, spustitelný příklad

Níže je jeden soubor C#, který můžete zkopírovat a vložit do konzolové aplikace. Pokrývá vše – od instalace balíčku po tisk varování.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Spusťte**: `dotnet run` z kořenové složky projektu. Pokud chybí nějaká písma, uvidíte vytištěná varování a volitelná náhrada bude aplikována před uložením souboru.

---

## Často kladené otázky

### Funguje to také při konverzi do PDF?

Ano. Po zpracování varování můžete zavolat `doc.Save("output.pdf")` a nahrazená písma se objeví v PDF stejně jako v DOCX.

### Co když potřebuji potlačit varování pro konkrétní písmo?

Můžete je ve smyčce odfiltrovat – prostě přeskočte `WarningInfo`, jehož `Message` obsahuje název písma, které chcete ignorovat.

### Je `FontSubstitutionWarnings` dostupné ve starších verzích Aspose.Words?

Byl zaveden ve verzi 20.5. Pokud jste uvízli na starší verzi, aktualizujte přes NuGet; změna API je zpětně kompatibilní.

---

## Závěr

Prošli jsme **jak povolit varování**, ukázali vám **detekovat chybějící písma** a demonstrovali správný způsob **jak načíst docx** s Aspose.Words při zachování úplné přehlednosti o náhradách písma. Prohlížením `document.WarningCallback.Warnings` získáte spolehlivý auditní záznam – žádné tiché náhrady.

Další kroky? Zkuste propojit logiku varování s logovacím frameworkem jako Serilog, nebo vytvořit UI, které zvýrazní chybějící písma před odesláním dokumentu uživatelům. Můžete také prozkoumat třídu `FontSettings` pro podrobnější kontrolu nad politikou náhrady písma.

Šťastné programování a ať se vaše dokumenty vždy vykreslují přesně tak, jak jste zamýšleli! 

![Diagram illustrating the flow from loading a DOCX file to capturing font substitution warnings – how to enable warnings in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}