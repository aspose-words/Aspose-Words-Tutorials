---
category: general
date: 2026-05-04
description: Naučte se, jak použít nahrazování fontů Aspose k detekci chybějících
  fontů při načítání dokumentu Word a získání podrobností o chybějících fontech –
  krok za krokem průvodce.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: cs
og_description: Ovládněte nahrazování písem v Aspose k detekci chybějících písem při
  načítání dokumentu Word a získání informací o chybějících písmenech pomocí kompletního
  C# kódu.
og_title: Aspose Náhrada písma – Detekce chybějících písem v dokumentech Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Aspose náhrada písma: Detekce chybějících písem v dokumentech Word'
url: /cs/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose náhrada fontů – Detekce chybějících fontů v dokumentech Word

Už jste se někdy zamysleli, proč dokument Word vypadá špatně na jiném počítači? Často je viníkem chybějící font a **Aspose font substitution** je nástroj, který vám umožní tyto mezery odhalit dříve, než se stanou vizuální katastrofou. V tomto tutoriálu si projdeme, jak **detekovat chybějící fonty** v okamžiku, kdy **načtete dokument Word**, a poté **získat podrobnosti o chybějících fontech**, abyste je mohli opravit nebo nahradit.

Probereme vše od nastavení výstražného callbacku až po získání čistého seznamu chybějících fontů. Na konci budete mít připravený spustitelný úryvek C#, který vám přesně řekne, které fonty nebyly nalezeny, a pochopíte, proč je to důležité pro věrnost dokumentu.

---

## Požadavky – Co potřebujete před zahájením

- **Aspose.Words for .NET** (doporučeno v verzi v23.12 nebo novější).  
- Vývojové prostředí .NET (Visual Studio, Rider nebo `dotnet` CLI).  
- Ukázkový DOCX, který úmyslně používá font, který nemáte nainstalovaný – nazvěte jej `DocumentWithMissingFont.docx`.  
- Základní znalost C# – nic složitého, jen schopnost spustit konzolovou aplikaci.

Pokud vám některá z těchto položek není známá, pozastavte se a nainstalujte NuGet balíček:

```bash
dotnet add package Aspose.Words
```

To je vše. Žádné extra fonty, žádné externí služby.

---

## Krok 1: Načtení dokumentu Word (a spuštění kontroly fontů)

První, co uděláte, je **načíst dokument Word**. Aspose.Words soubor parsuje a pokud nenajde odkazovaný font, zařadí varování *FontSubstitution*. Zde je kód, který načítání provádí:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Proč je to důležité:** Načtení dokumentu hned na začátku dává Aspose šanci prozkoumat každý úsek textu, styl i vložený objekt. Pokud font není nalezen v systému ani ve vlastní složce s fonty, dostanete později varování.

---

## Krok 2: Připojení výstražného callbacku pro zachycení událostí náhrady

Aspose.Words používá mechanismus callbacku, aby vás informoval o problémech, jako jsou chybějící fonty. Přiřazením implementace `IWarningCallback` k `doc.WarningCallback` můžete zachytit každé varování v reálném čase.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Tip:** Můžete připojit více callbacků (např. logování, aktualizace UI) jejich zabalením do kompozitního vzoru, ale pro tento tutoriál jeden callback stačí a udržuje věci přehledné.

---

## Krok 3: Implementace callbacku pro varování o náhradě fontu

Nyní definujeme třídu, která skutečně provádí práci. Callback přijímá objekt `WarningInfo`; filtrujeme `WarningType.FontSubstitution` a ukládáme popis pro pozdější použití.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Co se děje:** Když Aspose narazí na chybějící font, vytvoří varování typu „Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.“ Náš callback tuto řádku vytiskne a uloží.

---

## Krok 4: Zpracování dokumentu (volitelné) a sběr chybějících fontů

Pokud potřebujete jen **detekovat chybějící fonty**, stačí krok načtení – varování se spustí automaticky. Mnoho vývojářů však potřebuje **získat informace o chybějících fontech** po provedení dalších operací (např. uložení, konverze). Níže vynutíme malou operaci – uložení do PDF – aby se všechna varování vyprodukovala, a pak vyzvedneme nasbírané zprávy.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Očekávaný výstup v konzoli** (příklad):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Všimněte si, že každá řádka jasně uvádí původní font a náhradní font, který Aspose zvolil. To je podstata **aspose font substitution** reportování.

---

## Krok 5: Pokročilé – Použití vlastních zdrojů fontů ke snížení náhrad

Někdy *má* chybějící fonty, jen nejsou ve výchozí systémové složce. Aspose.Words vám umožní nasměrovat vlastní adresář pomocí `FontSettings`. Přidání tohoto kroku může dramaticky snížit počet varování o náhradě.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Proč to přidat?** Pokud distribuujete dokumenty mezi různými počítači, zabalení potřebných fontů do známé složky zajišťuje stejný vizuální vzhled všude. Také to činí vaši **detekci chybějících fontů** přesnější, protože Aspose nejprve zkontroluje tuto složku, než použije náhradní font.

---

## Kompletní funkční příklad

Sestavíme vše dohromady v jednom připraveném programu pro konzoli. Uložte jej jako `Program.cs` a spusťte pomocí `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Co byste měli vidět:** Pokud zdrojový DOCX odkazuje na fonty, které nemáte, konzole vypíše každou řádku náhrady následovanou stručným souhrnem. Pokud jsou všechny fonty přítomny, zobrazí se zpráva „No missing fonts were detected.“.

---

## Časté problémy a jak se jim vyhnout

| Problém | Proč k němu dochází | Řešení |
|-------|----------------|-----|
| **Neobjeví se žádná varování** | Dokument používá jen systémové fonty, nebo jste již přidali vlastní složku obsahující chybějící fonty. | Ověřte, že DOCX skutečně odkazuje na nedostupný font. V Wordu můžete změnit odstavec na raritní font (např. „Papyrus“). |
| **Duplicitní zprávy** | Ten samý font je použit ve více úsecích, což způsobí více varování. | Odstraňte duplicity pomocí `Distinct()`, pokud potřebujete jen jedinečnou sadu. |
| **Pokles výkonu u velkých dokumentů** | Každé varování se zpracovává na UI vlákně. | Načítání spusťte v background úkolu nebo použijte `Parallel.ForEach` pro následné zpracování. |
| **Špatný náhradní font** | Výchozí náhrada Aspose nemusí odpovídat vaší značce. | Nastavte `FontSettings.SubstitutionSettings.DefaultFontName` na preferovaný náhradní font (např. „Calibri“). |

---

## Rozšíření řešení – Export chybějících fontů do JSON

Pokud budujete webovou službu, která musí klientovi vracet informace o chybějících fontech, serializace seznamu je triviální:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Nyní může vaše API vrátit čistý JSON payload, který může spotřebovat jiný systém.

---

## Závěr

V tomto průvodci jsme ukázali **Aspose font substitution** od začátku až do konce: načtení dokumentu Word, připojení výstražného callbacku, zachycení každé události *detekce chybějících fontů* a nakonec **získání informací o chybějících fontech** pro reportování nebo nápravu. Přidáním volitelných vlastních složek s fonty můžete snížit počet náhrad a několika řádky kódu můžete dokonce exportovat výsledky jako JSON.

Pamatujte, že vizuální integrita vašich dokumentů závisí na použitém fontu. S technikou popsanou zde už vás nikdy nepřekvapí neočekávaná náhrada.  

Jste připraveni na další krok? Zkuste integrovat tuto logiku do většího pipeline pro zpracování dokumentů, nebo prozkoumejte další funkce Aspose.Words, jako je vkládání fontů (`doc.FontSettings.EmbeddedFonts`). Možnosti jsou neomezené a vaši uživatelé vám poděkují za dokonalý výstup.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}