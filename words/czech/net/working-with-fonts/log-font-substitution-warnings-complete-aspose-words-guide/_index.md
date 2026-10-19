---
category: general
date: 2026-01-14
description: Zaznamenávejte varování o nahrazení písem při načítání dokumentů Word
  pomocí Aspose.Words. Naučte se detekovat chybějící písma a jak zachytit chybějící
  písma v C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: cs
og_description: Zaznamenávejte varování o nahrazení písma při načítání dokumentů Word
  pomocí Aspose.Words. Objevte, jak detekovat chybějící písma a zachytit chybějící
  písma v C#.
og_title: Zaznamenávejte varování o substituci fontů – Kompletní průvodce Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Zaznamenávání varování o nahrazení písma – Kompletní průvodce Aspose.Words
url: /cs/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Log Font Substitution Warnings – Complete Aspose.Words Guide

Logování varování o náhradě fontů je nezbytné, když potřebujete zajistit, aby se Word dokument po načtení Aspose.Words zobrazoval naprosto stejně. Pokud jste se někdy ptali, **jak zjistit chybějící fonty**, nebo chcete vědět, **jak zachytit chybějící fonty**, jste na správném místě.  

V tomto tutoriálu projdeme reálný scénář, ukážeme kompletní C# kód a vysvětlíme, proč je každý řádek důležitý. Na konci budete schopni zaznamenat každou událost náhrady fontu a reagovat na ni – žádná tajemná varování už nebudou.

![Log font substitution warnings example](/images/font-warnings.png "Screenshot showing console output of log font substitution warnings")

## Co se naučíte

- Jak nakonfigurovat `LoadOptions`, aby Aspose.Words vyvolával typová varování pro náhradu fontů.  
- Přesné kroky k **detekci chybějících fontů** během načítání dokumentu.  
- Čistý způsob, jak **zachytit chybějící fonty** a zapsat je do vlastního logu nebo monitorovacího systému.  
- Řešení okrajových případů (např. když dokument obsahuje font, který není nainstalován na serveru).  

### Požadavky

- .NET 6.0 nebo novější (kód funguje také s .NET Framework 4.6+).  
- Platná licence Aspose.Words pro .NET (nebo bezplatná zkušební verze).  
- Základní znalost C# a konzolových aplikací.  

Pokud už máte vše připravené, pojďme na to.

## Krok 1 – Nastavení LoadOptions pro vyvolání typových varování

Jádrem řešení je `LoadOptions.FontSubstitutionWarning`. Přepnutím na `RaiseTypedWarnings` řeknete Aspose.Words, aby vyvolalo událost **každý**krát, když nenajde přesně požadovaný font.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Proč je to důležité:**  
> Výchozí chování tiše nahrazuje chybějící font nejbližší shodou, což může vést k rozvrhovým chybám, které si ani nevšimnete. Vyvolání typových varování vám poskytne plnou přehlednost.

## Krok 2 – Přihlášení k události varování

Nyní se připojíme k `loadOptions.FontSubstitutionWarning`. Lambda přijímá objekt `e`, který přesně říká, který font chyběl a který byl použit místo něj.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Tip:** Pokud spouštíte tento kód na webovém serveru, nahraďte `Console.WriteLine` strukturovaným loggerem (Serilog, NLog, atd.), abyste mohli data později dotazovat.

## Krok 3 – Načtení dokumentu s nakonfigurovanými možnostmi

S nastaveným mechanismem varování stačí načíst dokument jako obvykle. Událost se spustí automaticky pro každý chybějící font.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Očekávaný výstup v konzoli

Pokud `input.docx` odkazuje na font nazvaný *MyFancyFont*, který není nainstalován, uvidíte:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Každý řádek odpovídá události **detekce chybějících fontů**, čímž získáte kompletní auditní stopu.

## Krok 4 – Řešení okrajových případů a pokročilých scénářů

### 4.1 Když nedojde k žádné náhradě

Někdy dokument používá jen systémové fonty, které jsou již nainstalovány. V takovém případě se událost varování nikdy nevyvolá a konzole zůstane prázdná. To je dobré znamení – vaše prostředí již obsahuje všechny potřebné fonty.

### 4.2 Zachycení varování pro pozdější analýzu

Pokud potřebujete varování uložit pro noční report, shromažďujte je do seznamu:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Po načtení můžete `missingFonts` serializovat do JSON, zapsat do databáze nebo poslat e‑mailem souhrn.

### 4.3 Práce s PDF nebo jinými formáty

Stejný přístup s `LoadOptions` funguje i pro volání `Load` na PDF, RTF a dokonce HTML souborech. Stačí předat stejnou instanci možností a Aspose.Words vyvolá varování pro jakýkoli font, který nelze spárovat.

## Krok 5 – Ověření výsledku programově

Pokud dáváte přednost automatickému testu místo ručního sledování konzole, ověřte, že seznam obsahuje očekávané položky:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Tento úryvek ukazuje, **jak zachytit chybějící fonty** v kódu, nejen v logu.

## Časté chyby a jak se jim vyhnout

| Problém | Proč k tomu dochází | Řešení |
|---------|----------------------|--------|
| Zapomenutí nastavit `RaiseTypedWarnings` | Výchozí hodnota je `DoNotRaise`, takže se žádné události nevyvolají. | Explicitně nastavte `FontSubstitutionWarning` podle kroku 1. |
| Použití `Console.WriteLine` ve webové aplikaci | Výstup do konzole zmizí v IIS/ASP.NET Core. | Přepněte na trvalý logger (např. Serilog). |
| Načítání dokumentu s relativní cestou | Pracovní adresář se může během běhu lišit. | Používejte absolutní cesty nebo `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignorování `SubstitutedFontName` | Přicházíte o informace, který náhradní font byl zvolen. | Vždy logujte jak `FontName`, tak `SubstitutedFontName`. |

## Bonus: Automatizace instalace fontů

Pokud řídíte nasazovací prostředí, můžete chybějící fonty předinstalovat pomocí PowerShell skriptu:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Spuštěním tohoto skriptu před startem aplikace eliminujete většinu varování **detekce chybějících fontů**.

## Závěr

Probrali jsme vše, co potřebujete k **logování varování o náhradě fontů** při načítání Word dokumentů pomocí Aspose.Words. Nastavením `LoadOptions`, přihlášením k události varování a případným uložením výsledků můžete spolehlivě **detekovat chybějící fonty** a pochopit **jak zachytit chybějící fonty** v jakémkoli .NET projektu.

Vezměte kód, upravte logger podle svého stacku a už vás nikdy nepřekvapí tichá výměna fontu. Další kroky mohou zahrnovat:

- Integraci seznamu varování do CI/CD pipeline, aby se buildy zastavily, když chybí kritické fonty.  
- Rozšíření přístupu pro monitorování používání fontů napříč celou flotilou dokumentů.  
- Prozkoumání Aspose.Words `FontSettings` API pro poskytování vlastních náhradních fontů.

Máte otázky nebo složitý scénář? Zanechte komentář a pojďme to společně vyřešit. Šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}