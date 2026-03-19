---
category: general
date: 2026-03-19
description: Naučte se, jak zachytit varování v Aspose.Words, nastavit výchozí nastavení
  písma a detekovat chybějící písma při načítání dokumentu Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: cs
og_description: Jak zachytit varování v Aspose.Words, nastavit výchozí nastavení písma
  a detekovat chybějící písma při načítání dokumentu Word.
og_title: Jak zachytit varování – Nastavit výchozí nastavení písma
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak zachytit varování – nastavit výchozí nastavení písma
url: /cs/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak zachytit varování – nastavit výchozí nastavení písma

**Jak zachytit varování** je běžná potřeba při práci s Aspose.Words, zejména pokud vaše dokumenty závisí na konkrétních písmech, která nemusí být na cílovém počítači k dispozici. Už jste někdy otevřeli DOCX a přemýšleli, proč vypadá rozvržení špatně? Odpověď je často skryta ve varování o chybějícím písmu.  

V tomto průvodci si projdeme **jak zachytit varování** při **načítání Word dokumentu**, nakonfigurujeme **nastavení výchozího písma**, a nakonec **detekujeme chybějící písma**, abyste mohli reagovat programově. Žádné zbytečnosti – jen kompletní, spustitelný příklad a vysvětlení každého řádku.

> *Tip:* Zachycení varování včas vám ušetří ladění tajemných problémů s rozvržením později.

---

## Co budete potřebovat

- **Aspose.Words for .NET** (nejnovější verze k roku 2026).  
- Vývojové prostředí .NET (Visual Studio, Rider nebo VS Code).  
- Vzorek DOCX, který odkazuje na písmo, které *nemáte* nainstalované (např. *Comic Sans MS* na Linuxu).  

To je vše. Kromě Aspose.Words nejsou vyžadovány žádné další balíčky NuGet.

---

## Krok 1 – Pochopte, proč potřebujete zachytit varování

Když Aspose.Words parsuje dokument, může narazit na písma, která nejsou na hostiteli k dispozici. Ve výchozím nastavení knihovna tiše nahrazuje písmo náhradním, což může změnit zalomení řádků, mezery a dokonce způsobit, že text zmizí.  

Použití **WarningCallback** spolu s objektem **FontSettings** vám poskytne dvě věci:

1. **Viditelnost** – získáte položku `WarningInfo` pro každou substituci.  
2. **Kontrola** – můžete předem nakonfigurovat výchozí písmo, aby se minimalizovaly vizuální překvapení.

Představte si to jako instalaci „hlídacího psa“, který křičí pokaždé, když motor vymění část pod kapotou.

---

## Krok 2 – Nastavte výchozí nastavení písma

První sekundární klíčové slovo, **set default font settings**, se objevuje právě zde. Vytvoříte instanci `FontSettings` a volitelně ji nasměrujete na složku, která obsahuje vaše náhradní písma.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Proč?**  
> Pokud nespecifikujete náhradu, Aspose.Words vybere první systémové písmo, které odpovídá stylu, což může být výrazně odlišné. Nastavením známého výchozího písma zajistíte konzistentní vykreslování napříč počítači.

---

## Krok 3 – Připravte Warning Callback pro zachycení varování

Nyní si ukážeme **jak zachytit varování** připojením `WarningInfoCollection` k možnostem načítání. Tato kolekce bude ukládat každé varování vyvolané během procesu načítání.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` implementuje `IWarningCallback`, takže Aspose.Words automaticky vloží každé varování do `warningInfos`. Není potřeba žádné dotazování.

---

## Krok 4 – Načtěte Word dokument s nakonfigurovanými možnostmi

Zde se uplatní druhé sekundární klíčové slovo, **load word document**. Předáme jak `FontSettings`, tak `WarningCallback` prostřednictvím instance `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Pokud dokument odkazuje na písmo, které není nainstalováno, callback varování zachytí položku `WarningType.FontSubstitution`.

---

## Krok 5 – Detekujte chybějící písma ze shromážděných varování

Nakonec odpovíme na třetí sekundární klíčové slovo, **detect missing fonts**, iterací přes shromážděná varování.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Typický výstup vypadá takto:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Tento řádek vám přesně říká, které písmo chybí a jaká náhrada byla použita – informace, které můžete zaznamenat, zobrazit uživateli nebo dokonce spustit vlastní rutinu instalace písma.

---

## Kompletní spustitelný příklad

Níže je celý program, který můžete zkopírovat a vložit do konzolové aplikace. Ukazuje **jak zachytit varování**, **nastavit výchozí nastavení písma**, **načíst Word dokument** a **detekovat chybějící písma** v jednom toku.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Očekávaný výsledek:** Když specifikovaný DOCX odkazuje na písmo, které není nainstalováno, konzole vypíše varování pro každou substituci. Pokud jsou všechna písma přítomna, smyčka nevytiskne žádný výstup.

---

## Časté úskalí a okrajové případy

| Situation | Why it Happens | How to Handle It |
|-----------|----------------|------------------|
| **Neobjeví se žádná varování**, i když vypadá rozvržení špatně | Dokument může používat *vložená* písma, která Aspose.Words vykresluje bez substituce. | Zkontrolujte `Document.HasEmbeddedFonts` a zvažte extrakci vložených písem, pokud je potřebujete na jiném počítači. |
| **Více varování pro |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}