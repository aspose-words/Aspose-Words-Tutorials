---
category: general
date: 2026-02-18
description: Naučte se zachytávat varování o písmu a detekovat chybějící písma v C#
  pomocí Aspose.Words. Postupujte podle tohoto krok‑za‑krokem průvodce a efektivně
  řešte chybějící písma.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: cs
og_description: Zachyťte varování o fontu v C# a naučte se detekovat chybějící fonty,
  zpracovávat chybějící fonty a vypisovat chybějící fonty s kompletním příkladem kódu.
og_title: Zachycení varování o fontu v C# – Kompletní průvodce
tags:
- Aspose.Words
- C#
- Font Management
title: Zachycení varování o fontu v C# – Kompletní programovací průvodce
url: /cs/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

– ať už"

Then close shortcodes as given.

Now ensure we keep all shortcodes at bottom unchanged.

Let's assemble final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zachycení varování o písmu v C# – Kompletní programovací průvodce

Už jste se někdy zamýšleli, jak **zachytit varování o písmu**, když dokument odkazuje na font, který není nainstalován na serveru? Nejste v tom sami. V mnoha podnikových aplikacích chybějící fonty způsobují problémy s rozvržením a jediný spolehlivý způsob, jak je odhalit, je poslouchat varování, která knihovna vyhazuje.  

V tomto tutoriálu vám ukážeme připravené řešení, které nejen **zachytí varování o písmu**, ale také **detekuje chybějící fonty**, **zpracuje chybějící fonty** a dokonce **vypíše chybějící fonty**, takže si můžete rozhodnout, zda je nahradit, vložit nebo upozornit uživatele. Nepotřebujete žádnou externí dokumentaci – stačí zkopírovat, vložit a spustit.

## Co se naučíte

- Jak nakonfigurovat `LoadOptions` pro zapnutí varování o substituci fontů.  
- Přesný kód, který potřebujete k načtení DOCX a získání všech varování.  
- Proč je každý krok důležitý, včetně úvah o výkonu.  
- Zvládání okrajových případů, jako jsou dokumenty s fonty pro smíšené skripty nebo vlastní složky s fonty.  

**Požadavky**: .NET 6+ (nebo .NET Framework 4.6+), odkaz na NuGet balíček **Aspose.Words** a základní znalost C#. Pokud jste s Aspose.Words nikdy nepracovali, nebojte se – tento průvodce vás provede každým detailem.

![Diagram showing capture font warnings flow](image.png){alt="capture font warnings diagram"}

## Zachycení varování o písmu – Proč je to důležité

Když Aspose.Words načte dokument, tiše nahradí jakýkoli nedostupný font náhradním. Tato náhrada udrží načítání funkční, ale vizuální výsledek může být zcela posunutý. Zapnutím příznaku **SubstitutionWarningLevel.All** knihovna přidá záznam `WarningInfo` pro každý chybějící font, což vám umožní **detekovat chybějící fonty** ještě před tím, než je dokument vykreslen nebo uložen.

> **Tip:** Pokud zpracováváte stovky souborů v dávkovém úkolu, zaznamenávání těchto varování do centrálního úložiště vám může později ušetřit hodiny ruční kontroly kvality.

## Krok 1: Nastavte svůj projekt

1. Otevřete své oblíbené IDE (Visual Studio, Rider, VS Code).  
2. Vytvořte nový konzolový projekt:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Přidejte balíček Aspose.Words:

```bash
dotnet add package Aspose.Words
```

A to je vše – žádné extra DLL, žádné COM interop. Knihovna obsahuje vše, co potřebujete k **zpracování chybějících fontů**.

## Krok 2: Připravte Load Options pro zachycení všech varování o substituci fontů

Aby engine **zachytil varování o písmu**, musíte mu říct, aby zaznamenával každou substituci. Následující úryvek vytvoří instanci `LoadOptions`, povolí úroveň varování a (volitelně) nasměruje engine do složky, která obsahuje vlastní fonty, jež můžete chtít použít.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Proč je to důležité:**  
- `SubstitutionWarningLevel.All` zajišťuje, že **každá** událost chybějícího fontu je zaznamenána, ne jen první.  
- Bez tohoto příznaku Aspose.Words tiše nahrazuje font a nikdy se nedozvíte, že problém existuje.

## Krok 3: Načtěte dokument pomocí nakonfigurovaných možností

Nyní skutečně otevřeme soubor. Nahraďte `DocumentWithMissingFonts.docx` cestou k vašemu testovacímu dokumentu.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Pokud soubor obsahuje odkazy na fonty, které nejsou na stroji (nebo v volitelně přidané složce), bude `document.WarningInfoCollection` naplněna.

## Krok 4: Najděte a zobrazte všechna varování o substituci fontů

Zde je jádro tutoriálu: iterace přes `WarningInfoCollection` za účelem **vypsání chybějících fontů**. Budeme filtrovat podle `WarningType.FontSubstitution` a vytiskneme přátelskou zprávu.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Očekávaný výstup

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Pokud dokument používá pouze nainstalované fonty, uvidíte řádek “✅ No missing fonts detected”.

## Krok 5: Pokročilé – Jak **zpracovat chybějící fonty** programově

Pouhé vytištění seznamu může stačit pro diagnostický nástroj, ale mnoho produkčních systémů potřebuje **automaticky zpracovat chybějící fonty**. Níže jsou dvě běžné strategie:

### 5.1 Nahradit známým fallbackem

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Vložit vlastní font za běhu

Pokud máte firemní soubor fontu (`MyBrand.ttf`), můžete jej vložit, když je detekován chybějící font:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Poznámka:** Vkládání fontů může zvýšit velikost výstupního souboru, takže zvažte kompromis mezi věrností a šířkou pásma.

## Časté úskalí a jak se jim vyhnout

| Příznak | Pravděpodobná příčina | Řešení |
|---------|-----------------------|--------|
| Neobjevují se žádná varování, i když dokument vypadá špatně | `SubstitutionWarningLevel` není nastaven na `All` | Ujistěte se, že krok 2 nastavuje příznak přesně tak, jak je uvedeno |
| Varování uvádějí stejný font vícekrát | Dokument obsahuje font v několika stylech | Odstraňte duplicity, pokud potřebujete jen jedinečný seznam: `fontWarnings.Select(w => w.Description).Distinct()` |
| Aplikace spadne při velkých souborech DOCX | Načítání s výchozími nastaveními paměti | Použijte `LoadOptions.LoadFormat` nebo streamujte soubor, aby se snížil tlak na paměť |

## Kompletní funkční příklad (připravený ke kopírování a vložení)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Spusťte program pomocí `dotnet run`. Měli byste vidět seznam chybějících fontů vytištěný do konzole, což potvrzuje, že jste úspěšně **zachytili varování o písmu**.

## Závěr

Nyní máte kompletní, připravený vzor pro **zachycení varování o písmu**, **detekci chybějících fontů**, **zpracování chybějících fontů** a **výpis chybějících fontů** pomocí Aspose.Words v C#. Přístup je nenáročný, vyžaduje jen několik řádků kódu a lze jej vložit do jakéhokoli existujícího pipeline – ať už

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}