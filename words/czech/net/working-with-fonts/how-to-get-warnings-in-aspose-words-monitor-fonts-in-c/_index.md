---
category: general
date: 2026-01-06
description: Naučte se, jak získávat varování při načítání dokumentů a jak sledovat
  písma pomocí Aspose.Words. Tento průvodce pokrývá zpětná volání varování a sledování
  náhrady písem.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: cs
og_description: Jak získat varování v Aspose.Words? Postupujte podle tohoto krok‑za‑krokem
  tutoriálu, abyste sledovali písma a zachytili zprávy o substituci při načítání dokumentů.
og_title: Jak získat varování v Aspose.Words – sledovat písma
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Jak získat varování v Aspose.Words – sledovat písma v C#
url: /cs/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak získat varování v Aspose.Words – Monitorování fontů v C#

Už jste se někdy zamysleli **jak získat varování**, když Word dokument obsahuje fonty, které nemáte nainstalované? Je to častý problém – vaše aplikace tiše nahrazuje chybějící fonty a nikdy nevíte, co se změnilo. Dobrou zprávou je, že se můžete napojit na varovný systém Aspose.Words a **monitorovat fonty** v reálném čase.

> **Tip:** Pokud budujete pipeline pro konverzi dokumentů, zaznamenání chybějících fontů včas vás ochrání před nepříjemnými překvapeními v rozložení později.

---

## Co budete potřebovat

- **Aspose.Words for .NET** (nejnovější verze; API se nezměnilo od v23.10)
- Vývojové prostředí .NET (Visual Studio, Rider nebo VS Code s rozšířením C#)
- Ukázkový `.docx`, který odkazuje na font, který nemáte nainstalovaný (např. **„NonExistentFont“**)

To je vše – žádné další NuGet balíčky kromě Aspose.Words.

---

## Krok 1 – Nastavte sběrač varování (Primární klíčové slovo v nadpisu)

První, co potřebujete, je místo, kde budete ukládat varování v okamžiku, kdy nastanou. Aspose.Words poskytuje vlastnost `WarningCallback` na `LoadOptions` právě pro tento účel.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Proč je to důležité:**  
Když knihovna narazí na chybějící font, nevyhodí výjimku; místo toho vytvoří objekt `WarningInfo`. Připojením sběrače získáte úplnou přehlednost o každé události substituce, což vám umožní **monitorovat fonty** bez zaplňování konzole nesouvisejícími zprávami.

---

## Krok 2 – Načtěte dokument s možnostmi povolenými pro varování

Nyní skutečně načteme soubor. `LoadOptions`, které jsme připravili v předchozím kroku, zajistí, že všechna varování související s fonty budou zachycena.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Co se děje pod kapotou?**  
Aspose.Words parsuje Word soubor, řeší fonty a kdykoli nenajde požadovaný font, přepne na náhradní (obvykle Arial). Tento přechod vyvolá varování `WarningType.FontSubstitution`, které skončí v `warningCollector`.

---

## Krok 3 – Prohlédněte si shromážděná varování (Primární klíčové slovo se objevuje znovu)

Po načtení dokumentu jednoduše projdeme `warningCollector` a vypíšeme všechny zprávy o substituci fontů.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Očekávaný výstup** (při předpokladu, že chybějící font je *„FancyScript“*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Pokud dokument obsahuje více neznámých fontů, uvidíte jeden řádek na každou substituci – ideální pro logování nebo upozorňování.

---

## Krok 4 – Volitelné: Zaznamenejte nebo uložte informace o varováních

Ve výrobě pravděpodobně chcete něco víc než `Console.WriteLine`. Zde je rychlý příklad, který zapisuje varování do JSON souboru pro pozdější analýzu.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Nyní máte trvalý záznam, který můžete nasadit do monitorovacího dashboardu, nebo dokonce spustit automatický požadavek na chybějící soubory fontů.

---

## Krok 5 – Ověřte výsledek a vyčistěte prostředí

Spusťte program. Pokud uvidíte zprávy o substituci, úspěšně **získáte varování** a nyní **monitorujete fonty**. Pokud se nic neobjeví, zkontrolujte, že testovací dokument skutečně odkazuje na font, který není nainstalován na stroji.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Počet nula obvykle znamená buď:

1. Všechny fonty byly vyřešeny (možná je font *nainstalován* lokálně), nebo
2. Dokument neobsahoval žádné odkazy na fonty, které by vyžadovaly substituci.

---

## Časté problémy & Jak se jim vyhnout

| Problém | Proč k tomu dochází | Řešení |
|---------|---------------------|--------|
| **Neobjeví se žádná varování** | Font ve skutečnosti existuje v systému, nebo dokument používá jen vestavěné fonty. | Přejmenujte font ve zdrojovém souboru na něco nemožného (např. `XYZ123`) a zkuste to znovu. |
| **Příliš mnoho varování (šum)** | Načítáte mnoho dokumentů ve smyčce, aniž byste vyčistili sběrač. | Znovu vytvořte `WarningInfoCollection` pro každý dokument, nebo po zpracování zavolejte `warningCollector.Clear()`. |
| **Dopad na výkon** | Nadměrné zapisování do disku může zpomalit dávkové zpracování. | Ukládejte varování v paměti a zapisujte je hromadně, nebo použijte asynchronní I/O. |
| **Chybějící `using Aspose.Words.Loading;`** | Třída `LoadOptions` se nachází v tomto jmenném prostoru. | Přidejte chybějící `using` direktivu, jak je ukázáno v kroku 1. |

---

## Rozšíření řešení – Monitorování dalších typů varování

Zatímco substituce fontů je nejviditelnější, Aspose.Words může vydávat varování pro:

- **Zastaralé funkce** (`WarningType.Deprecated`),
- **Potenciální ztrátu dat** (`WarningType.DataLoss`),
- **Ne podporované formáty souborů** (`WarningType.UnsupportedFileFormat`).

Můžete rozšířit filtr v kroku 3 tak, aby zachycoval i tato varování:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Tímto způsobem nejde jen **jak monitorovat fonty**, ale také **jak získat varování** pro jakýkoli scénář, se kterým se vaše aplikace může setkat.

---

## Kompletní funkční příklad (připravený ke zkopírování)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Spusťte to:** Sestavte projekt, spusťte a uvidíte varování vytištěná i uložena. To je kompletní odpověď na **jak získat varování** a **jak monitorovat fonty** s Aspose.Words.

---

## Závěr

Nyní víte **jak získat varování** z Aspose.Words, konkrétně pro scénáře substituce fontů, a naučili jste se **jak monitorovat fonty** během procesu načítání dokumentu. Připojením `WarningCallback`, iterací shromážděných objektů `WarningInfo` a volitelným ukládáním dat získáte úplnou transparentnost nad událostmi chybějících fontů – klíčová schopnost pro jakýkoli pipeline zpracování dokumentů.

Další kroky? Zkuste rozšířit filtr varování tak, aby zahrnoval ztrátu dat nebo varování o zastaralých funkcích, nebo integrujte JSON log do monitorovacího dashboardu jako Grafana. Stejný vzor funguje pro všechny typy varování, takže budete dobře připraveni sledovat jakýkoli problém, který vám Aspose.Words hodí do cesty.

Šťastné programování a ať se vaše dokumenty vždy vykreslí přesně tak, jak očekáváte! 

---

<img src="font-warnings.png" alt="how to get warnings in Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}