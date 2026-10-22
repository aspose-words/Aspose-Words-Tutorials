---
category: general
date: 2026-04-24
description: Jak detekovat nahrazení chybějících fontů v Aspose.Words pomocí C#. Tento
  průvodce ukazuje, jak spolehlivě řešit chybějící fonty pomocí varování FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: cs
og_description: Jak detekovat nahrazení chybějících fontů v Aspose.Words v C#. Naučte
  se, jak řešit chybějící fonty pomocí varování FontSettings.
og_title: Jak detekovat substituci v Aspose.Words – Kompletní průvodce
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Jak detekovat substituci v Aspose.Words – řešení chybějících fontů
url: /cs/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak detekovat substituci v Aspose.Words – Řešení chybějících fontů

Už jste se někdy ptali, **jak detekovat substituci**, když se dokument pokouší použít font, který není nainstalován na vašem serveru? Je to častý problém, zejména při generování PDF nebo Word souborů v automatizovaném pipeline. Dobrou zprávou je, že Aspose.Words poskytuje vestavěný hák, který vám umožní tuto situaci zachytit, a také můžete **zvládat chybějící fonty** elegantně.

V tomto tutoriálu projdeme reálný příklad, který ukazuje **jak detekovat substituci** pomocí události `FontSettings.Warning`, a vysvětlíme, jak **zvládat chybějící fonty** bez narušení vašeho zpracovatelského toku. Na konci budete mít připravený úryvek k okamžitému spuštění, jasné pochopení, proč je každý řádek důležitý, a několik tipů, jak se vyhnout typickým úskalím.

## Požadavky

- .NET 6.0 nebo novější (kód funguje také na .NET Framework)
- Aspose.Words pro .NET (NuGet balíček `Aspose.Words`) – verze 23.11 nebo novější
- Ukázkový dokument, který odkazuje na font, který nemáte nainstalovaný (např. `MissingFont.docx`)
- Visual Studio, VS Code nebo jakékoli C# IDE, které preferujete  

Žádná další konfigurace není potřeba kromě přidání NuGet balíčku.

## Jak detekovat substituci pomocí FontSettings

Jádrem **jak detekovat substituci** je událost `FontSettings.Warning`. Když Aspose.Words nemůže najít požadovaný font, vyvolá varování `WarningType.FontSubstitution`. Přihlášením k této události získáte notifikaci v reálném čase, včetně původního názvu fontu a fontu, který byl použit jako náhradní.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Proč to funguje:**  
- `LoadOptions.FontSettings` říká Aspose.Words, aby použil objekt `FontSettings`, který jste právě vytvořili.  
- Přihlášení k `Warning` vám poskytuje jedno místo pro sledování *všech* problémů souvisejících s fonty, nejen chybějících fontů.  
- Filtr `WarningType.FontSubstitution` zajišťuje, že reagujete pouze na konkrétní scénář, který vás zajímá – podstata **jak detekovat substituci**.

### Očekávaný výstup

Spuštěním výše uvedeného kódu s dokumentem, který odkazuje na neexistující font, se vytiskne něco jako:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Pokud dokument používá pouze nainstalované fonty, konzole zůstane tichá – jasný signál, že **jak detekovat substituci** uspělo bez falešných poplachů.

## Elegantní řešení chybějících fontů

Detekce substituce je jen polovina boje; potřebujete také strategii, jak **zvládat chybějící fonty**, aby finální výstup vypadal podle očekávání. Níže jsou tři praktické přístupy, které můžete kombinovat.

### 1. Poskytněte složku s náhradními fonty

Aspose.Words může prohledávat další adresáře pro fonty. Ukázáním na složku, která obsahuje nejčastější fonty, které očekáváte, snížíte pravděpodobnost substituce.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Proč:** Když původní font chybí, Aspose.Words má nyní známou sadu alternativ, což často vede k předvídatelnějšímu vizuálnímu výsledku.

### 2. Nahraďte chybějící fonty programově

Pokud chcete plnou kontrolu, můžete po detekci nahradit chybějící font konkrétním.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Proč:** Toto říká enginu přesně, které fonty má zkusit, což vám umožní vynutit firemní branding nebo standardy přístupnosti.

### 3. Logujte a přerušte (když je substituce nepřijatelná)

Někdy chybějící font znamená, že dokument je pro váš případ použití neplatný (např. právní formuláře). V takovém scénáři můžete vyhodit výjimku hned, jakmile dojde k substituci.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Proč:** Okamžité selhání zabraňuje následným chybám, jako jsou špatně zarovnané tabulky nebo poškozené podpisy.

## Kompletní funkční příklad – všechny kroky dohromady

Níže je jeden program připravený ke zkopírování, který demonstruje **jak detekovat substituci** *a* několik způsobů, jak **zvládat chybějící fonty**. Klidně zakomentujte části, které nepotřebujete.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Co očekávat:**  
- Pokud `MissingFont.docx` odkazuje na font, který není na stroji, konzole vytiskne varování o substituci.  
- Uložený `Processed.docx` používá náhradní font, který jste nakonfigurovali (nebo výchozí font knihovny).  
- Nevyskytují se neošetřené výjimky, pokud úmyslně nepřerušíte při substituci.

## Časté otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| *Co když dokument obsahuje mnoho chybějících fontů?* | Událost varování se spustí pro **každou** substituci, takže uvidíte více řádků. Můžete je agregovat do seznamu pro souhrnnou zprávu. |
| *Funguje to i při konverzi do PDF?* | Ano. Stejné `FontSettings` jsou respektovány při volání `doc.Save("out.pdf")`. Varování o substituci se stále spustí, což vám umožní ověřit vizuální věrnost PDF. |
| *Mohu detekovat substituci po načtení dokumentu?* | Ne přímo. Varování se vyvolá **během** načítání nebo ukládání. Pokud potřebujete analýzu po načtení, zachyťte varování do kolekce během fáze načítání. |
| *Co s vlastními fonty vloženými v DOCX?* | Vložené fonty jsou považovány za přítomné, takže nedochází k substituci. Pokud je vložený font poškozen, Aspose.Words stále vyvolá varování, které můžete zachytit stejným způsobem. |
| *Má to dopad na výkon?* | Minimální. Kontrola varování je nenáročná; skutečná cena je načítání samotného dokumentu. Přidání složky s fonty může mírně prodloužit čas hledání, ale jen při prvním načtení. |

## Profesionální tipy a úskalí, kterým se vyhnout

- **Pro tip:** Vždy nastavte `recursive: true`, když ukazujete na složku s mnoha fonty; jinak jsou podsložky ignorovány.  
- **Dejte si pozor na:** citlivost na velikost písmen na Linuxu. Názvy fontů jsou na Windows necitlivé na velikost, ale na Linuxu ne, takže použijte přesný název nebo přidejte obě varianty.  
- **Pamatujte:** Pokud běžíte v kontejnerizovaném prostředí, ujistěte se, že složka s fonty je součástí obrazu nebo je připojena během běhu.  
- **Tip:** Ukládejte varování do `List<string>`, pokud potřebujete prezentovat souhrn koncovým uživatelům nebo je zaznamenat do monitorovacího systému.  

## Závěr

Probrali jsme **jak detekovat substituci** chybějících fontů v Aspose.Words, ukázali vám několik způsobů, jak **zvládat chybějící fonty**, a poskytli kompletní, spustitelný příklad, který můžete vložit do libovolného .NET projektu. Připojením k události `FontSettings.Warning` získáte viditelnost problémů s fonty v reálném čase a pomocí složek s náhradními fonty nebo explicitních pravidel substituce zajistíte, že výstup bude vypadat přesně tak, jak očekáváte.

Připraveni na další krok? Zkuste rozšířit řešení tak, aby automaticky vložilo náhradní font do generovaného PDF, nebo připojte handler varování k centralizované logovací službě pro rozsáhlé dokumentové pipeline. Vzory, které jsme dnes probírali – detekce řízená událostmi, elegantní náhrada a explicitní zpracování chyb – se vztahují na mnoho dalších Aspose API, takže jste nyní připraveni řešit výzvy související s fonty napříč celým ekosystémem.

Máte další otázky ohledně práce s fonty, konverze PDF nebo triků v Aspose.Words? Zanechte komentář níže a šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}