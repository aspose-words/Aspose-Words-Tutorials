---
category: general
date: 2026-01-11
description: Povolte varování o nahrazování písma, abyste detekovali chybějící písma
  ve svých .NET dokumentech. Naučte se, jak získat název chybějícího písma a vypsat
  chybějící písma pomocí Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: cs
og_description: Povolte varování o náhradě písma v Aspose.Words, abyste detekovali
  chybějící písma, získali název chybějícího písma a vypsali chybějící písma ve svých
  dokumentech.
og_title: Povolit varování o nahrazení písma – krok za krokem C# tutoriál
tags:
- Aspose.Words
- C#
- Document Processing
title: Povolit varování o náhradě písma v Aspose.Words – kompletní průvodce
url: /cs/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Povolení varování o náhradě písem – Kompletní průvodce

Už jste se někdy divili, proč se Word dokument po nahrání na server mírně liší? Pravděpodobně autor použil písmo, které není na vašem počítači k dispozici, a Aspose.Words jej tiše nahradilo nejbližší alternativou. **Povolte varování o náhradě písem** a okamžitě zjistíte, která písma chybí, čím byla nahrazena a jak s těmito informacemi naložit.

V tomto tutoriálu si projdeme praktickým, end‑to‑end příkladem, který vám ukáže, jak **detekovat chybějící písma**, získat **get missing font name** a dokonce **list missing fonts** pro reportování. Žádné zbytečnosti, jen jasné řešení, které můžete dnes vložit do libovolného .NET projektu.

---

## Co se naučíte

- Jak nakonfigurovat `LoadOptions`, aby Aspose.Words vydával podrobná varování.
- Přesný kód potřebný k načtení dokumentu a výčtu varování souvisejících s písmy.
- Způsoby, jak extrahovat název chybějícího písma a jeho náhradu a poté vytvořit přehledný výstup.
- Tipy pro zpracování okrajových případů, jako jsou dokumenty s desítkami chybějících písem nebo vlastní složky s písmy.

### Předpoklady

- .NET 6+ (kód funguje také s .NET Framework 4.7+)
- Aspose.Words pro .NET 23.10 nebo novější (získáte jej z NuGet)
- Vzorek DOCX, který odkazuje na písmo, které nemáte nainstalované (nazveme jej `MissingFont.docx`)

Pokud máte tyto základy, pojďme na to.

---

## Krok 1: Nastavte LoadOptions pro povolení varování o náhradě písem  

První, co musíte udělat, je říct Aspose.Words, že vám na chybějících písmenech záleží. Ve výchozím nastavení knihovna varování pouze interně zaznamenává. Nastavením `SubstitutionWarningLevel` na `Typical` (nebo `All` pro nejpodrobnější výstup) přepnete přepínač.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Proč je to důležité:**  
Když je `SubstitutionWarningLevel` nastaven, pokaždé, když Aspose.Words nenajde odkazované písmo, přidá `FontSubstitutionWarning` do kolekce `Warnings` dokumentu. Tato kolekce je jediný spolehlivý způsob, jak **detekovat chybějící písma** bez ručního parsování dokumentu.

> **Pro tip:** Pokud zpracováváte dávku dokumentů a chcete mít naprostou jistotu, že zachytíte každou náhradu, použijte `FontSubstitutionWarningLevel.All`. Je to trochu hlučnější, ale zaručuje, že žádné varování neunikne.

---

## Krok 2: Načtěte dokument pomocí nakonfigurovaných možností  

Nyní, když je varovný systém připraven, načtěte svůj DOCX s `LoadOptions`, které jsme právě připravili. Cesta může být absolutní nebo relativní; jen se ujistěte, že soubor existuje.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Co se děje pod kapotou?**  
Aspose.Words parsuje XML dokumentu, řeší každý prvek `<w:font>` a kontroluje systémový katalog písem (plus jakékoli vlastní složky, které jste přidali do `FontSettings`). Když písmo nenajde, zaznamená varování – přesně to, co potřebujeme pro **list missing fonts** později.

---

## Krok 3: Projděte varování a extrahujte podrobnosti o chybějících písmenech  

S dokumentem v paměti kolekce `Warnings` obsahuje každé `FontSubstitutionWarning`. Projdeme ji, odfiltrujeme požadovaný typ a vytiskneme přátelský report.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Očekávaný výstup** (předpokládejme, že zdrojový dokument odkazuje na `MyCustomFont`, který není nainstalován):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Všimněte si, že každý záznam poskytuje jak **get missing font name** (`MyCustomFont`), tak náhradu (`Arial`). To je přesně ta informace, kterou potřebujete k rozhodnutí, zda vložit původní písmo, požádat autora o náhradu nebo prostě akceptovat substituci.

---

## Krok 4: Volitelné – shromážděte data do seznamu pro další zpracování  

Pokud potřebujete exportovat report do CSV, odeslat jej přes API nebo jen uchovat v paměti pro pozdější použití, můžete varování uložit do silně typovaného seznamu.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Nyní máte **list missing fonts** ve formátu, který může konzumovat jakýkoli downstream systém. Ať už napájíte dashboard nebo generujete auditní log, data jsou připravena.

---

## Krok 5: Zpracování okrajových případů a běžných úskalí  

### Více chybějících písem v jedné dávce  

Velké firemní šablony často odkazují na desítky vlastních písem. Kolekce varování může být rozsáhlá, ale vzor iterace uvedený výše škáluje lineárně, takže výkon není problém. Jen nezapomeňte udržet výstup čitelný – seskupení podle stránky nebo stylu může být užitečné, pokud potřebujete podrobnější analýzu.

### Vlastní složky s písmy  

Pokud ukládáte písma do nestandardního adresáře (např. sdílené síťové složky), řekněte Aspose.Words, kde má hledat:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Nastavení *před* načtením dokumentu dává knihovně šanci písma najít, což může některá varování zcela eliminovat.

### Potlačení konkrétních varování  

Někdy víte, že určitá substituce je přijatelna (např. dekorativní písmo, které vám nevadí nahradit). Můžete je po faktu odfiltrovat:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Kompatibilita verzí  

Enum `FontSubstitutionWarningLevel` je stabilní od Aspose.Words 20.12. Pokud používáte starší verzi, možná budete muset upgradovat, abyste získali funkci úrovně varování.

---

## Kompletní funkční příklad  

Níže je kompletní, připravený program, který zahrnuje všechny výše uvedené kroky. Vložte jej do nového konzolového projektu, přidejte NuGet balíček Aspose.Words a nastavte `docPath` na dokument, který odkazuje na chybějící písmo.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Spuštěním tohoto programu **povolíte varování o náhradě písem**, **detekujete chybějící písma**, **get missing font name** a **list missing fonts** jak v konzoli, tak v CSV souboru.

---

## Závěr  

Právě jsme probrali vše, co potřebujete k **povolení varování o náhradě písem** v Aspose.Words, od počáteční konfigurace až po získání čistého seznamu chybějících písem. Dodržením výše uvedených kroků budete schopni auditovat své dokumenty, zajistit vizuální věrnost a vyhnout se nepříjemným překvapením při renderování na serveru.

Dále můžete zkusit:

- **Vkládání chybějících písem** přímo do výstupního PDF nebo DOCX (použijte `FontSettings.EmbeddedFonts`).
- **Automatizaci instalace písem** na build agenty na základě vygenerovaného reportu.
- **Integraci s CI pipeline** pro selhání buildů, když chybí kritická písma.

Vyzkoušejte to a proměňte jednoduchý varovný systém v plnohodnotný workflow pro správu písem.

Šťastné programování a ať se vám všechna písma najdou!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}