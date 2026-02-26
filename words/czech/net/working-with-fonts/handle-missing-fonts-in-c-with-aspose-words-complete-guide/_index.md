---
category: general
date: 2026-02-26
description: Zpracujte chybějící písma v C# pomocí Aspose.Words. Naučte se zachytávat
  varování o nahrazení písma, implementovat IWarningCallback a zajistit, aby vaše
  dokumenty vypadaly správně.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: cs
og_description: Rychle řešte chybějící písma v C#. Tento průvodce ukazuje, jak zachytit
  varování o substituci písma pomocí Aspose.Words, implementovat IWarningCallback
  a ověřit výsledky.
og_title: Řešení chybějících fontů v C# – krok po kroku tutoriál Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Řešení chybějících fontů v C# s Aspose.Words – Kompletní průvodce
url: /cs/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

to keep markdown formatting.

Let's produce the translated content.

We'll keep shortcodes exactly as they are.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Řešení chybějících fontů v C# s Aspose.Words – Kompletní průvodce

Už jste někdy potřebovali **zachytit chybějící fonty** při načítání Word dokumentu v C# a divili se, proč výstup vypadá podivně? Nejste v tom sami. Když zdrojový soubor odkazuje na font, který není nainstalován na počítači, Aspose.Words tiše nahradí jiný, což může narušit rozvržení nebo značku.

Dobrá zpráva? Pomocí **callbacku pro varování** můžete zachytit každou událost nahrazení fontu, zaznamenat ji a rozhodnout, zda poskytnete náhradu. V tomto tutoriálu projdeme celý proces – od nastavení projektu až po ověření výstupu v konzoli – takže už vás nikdy nepřekvapí neviditelný font.

> **Co získáte**: Připravenou C# konzolovou aplikaci, která hlásí každý chybějící font, vysvětluje, proč varování nastalo, a ukazuje, jak rozšířit handler o vlastní logiku.

---

## Předpoklady

- .NET 6.0 nebo novější (kód funguje jak na .NET Core, tak na .NET Framework)
- Visual Studio 2022 (nebo jakékoli C# IDE dle vašeho výběru)
- **Licence** pro Aspose.Words for .NET (zkušební verze stačí pro testování)
- Word dokument, který odkazuje na font, který nemáte nainstalovaný (např. *Comic Sans MS* na Linuxu)

Pokud máte vše připravené, pojďme na to.

---

## Krok 1: Vytvořte nový konzolový projekt a přidejte Aspose.Words

Pro přehlednost začněte s čistým konzolovým projektem.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Pro tip**: Použijte přepínač `--framework net6.0`, pokud chcete cílit na konkrétní runtime.

Tím se stáhne nejnovější NuGet balíček Aspose.Words, který obsahuje typy `LoadOptions` a `IWarningCallback`, jež budeme potřebovat.

---

## Krok 2: Implementujte handler pro varování (IWarningCallback)

Aspose.Words vyvolá objekt `WarningInfo` pro každou nekritickou záležitost, na kterou narazí při načítání dokumentu. Implementací `IWarningCallback` určíte, co s těmito varováními uděláte.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Proč je to důležité**: Bez handleru jsou varování o nahrazení fontu tiše ignorována. Vypsáním do konzole získáte okamžitý přehled, které fonty chybí a jaký font Aspose.Words použil místo nich.

---

## Krok 3: Nakonfigurujte LoadOptions s callbackem pro varování

Nyní propojujeme handler s procesem načítání dokumentu. `LoadOptions` vám umožní připojit callback ještě před tím, než je soubor parsován.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Poznámka**: Nahraďte `YOUR_DIRECTORY` skutečnou složkou, kde máte testovací `.docx`. Instance `LoadOptions` musí být předána konstruktoru `Document`; jinak se použije výchozí tichý režim.

---

## Krok 4: Spusťte aplikaci a ověřte výstup

Zkompilujte a spusťte:

```bash
dotnet run
```

Pokud dokument odkazuje na font, který ve vašem systému není (např. *Papyrus*), uvidíte něco jako:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Tento jediný řádek vám přesně řekne, který font chybí a jaký náhradní font Aspose.Words zvolil. Nyní můžete vložit chybějící font, změnit zdrojový dokument nebo akceptovat náhradu.

---

## Krok 5: Pokročilé – Shromažďování varování pro pozdější použití

Někdy chcete varování uložit místo okamžitého výpisu. Níže je rychlá úprava handleru, která agreguje zprávy do seznamu.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

A aktualizujte `Main` následovně:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Nyní máte znovupoužitelný seznam, který můžete zapsat do log souboru, poslat do monitorovací služby nebo zobrazit v UI.

---

## Krok 6: Časté problémy a jak se jim vyhnout

| Problém | Proč k tomu dochází | Řešení |
|---------|----------------------|--------|
| **Neobjevují se žádná varování** | Callback nebyl připojen, nebo byl dokument načten bez `LoadOptions`. | Ujistěte se, že `LoadOptions.WarningCallback` je nastaven **před** voláním konstruktoru `Document`. |
| **Špatný název fontu ve zprávě** | Některé fonty jsou v dokumentu vloženy; Aspose.Words hlásí *původní* název, ne vložený. | Zkontrolujte odkazy na fonty ve zdrojovém souboru; vložení fontů varování eliminuje. |
| **Dopad na výkon** | Shromažďování varování u tisíců dokumentů může přidat režii. | Pro rychlé ladění použijte jednoduchý `Console.WriteLine`; sběrač aktivujte jen tehdy, když data skutečně potřebujete. |

---

## Vizuální shrnutí

![Ilustrace řešení chybějících fontů zobrazující tok varování callbacku](/images/handle-missing-fonts.png "Diagram zachytávání chybějících fontů s Aspose.Words")

*Diagram (alternativní text zahrnuje hlavní klíčové slovo) vizualizuje, jak callback pro varování zachytává události nahrazení fontu během načítání dokumentu.*

---

## Závěr

Nyní víte, **jak řešit chybějící fonty** v C# pomocí Aspose.Words. Připojením `IWarningCallback` k `LoadOptions` získáte úplnou přehlednost o každém nahrazení fontu, můžete jej zaznamenat nebo na něj reagovat a zajistit, že vaše generované dokumenty zachovají zamýšlený vzhled.

> **Rychlé shrnutí**:  
> 1. Přidejte Aspose.Words do konzolové aplikace.  
> 2. Implementujte `FontWarningHandler` (nebo sběrač).  
> 3. Předávejte jej přes `LoadOptions` při načítání dokumentu.  
> 4. Ověřte výstup v konzoli nebo uložená varování.  

Odtud můžete zkoumat **vkládání chybějících fontů** (`FontSettings.SubstitutionSettings`) nebo **automatické stahování z firemního font serveru** – oba jsou přirozeným rozšířením vzoru, který jsme právě vytvořili.

Máte další otázky ohledně **varování fontů v Aspose.Words**, **C# LoadOptions** nebo **načítání dokumentu s chybějícími fonty**? Zanechte komentář a šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}