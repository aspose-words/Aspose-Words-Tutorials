---
category: general
date: 2026-04-05
description: Průvodce nahrazováním fontů Aspose pro detekci chybějících fontů při
  načítání dokumentu Word. Naučte se konfigurovat nastavení fontů a efektivně řešit
  chybějící fonty.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: cs
og_description: Průvodce nahrazováním fontů Aspose pro detekci chybějících fontů při
  načítání dokumentu Word. Naučte se konfigurovat nastavení fontů a efektivně řešit
  chybějící fonty.
og_title: Aspose Nahrazení fontů – Detekce chybějících fontů v dokumentech Word
tags:
- Aspose.Words
- C#
- Font Management
title: Aspose substituce fontů – Detekce chybějících fontů v dokumentech Word
url: /cs/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Detekce chybějících fontů v dokumentech Word

Už jste někdy narazili na soubor Word, který vypadá perfektně na jednom počítači, ale na jiném vykazuje podivné změny fontů? To je klasický problém **aspose font substitution**, který obvykle znamená, že na cílovém systému chybí některé fonty. V tomto tutoriálu vám krok za krokem ukážeme, jak **detekovat chybějící fonty** při **načítání dokumentu Word**, jak **nastavit font settings**, a co dělat, aby **chybějící fonty** byly zpracovány elegantně.

Projdeme kompletním, spustitelným příkladem v C#, vysvětlíme, proč je každý řádek důležitý, a dokonce vám ukážeme výstup v konzoli, který byste měli očekávat. Na konci budete schopni odhalit nahrazení fontů okamžitě po načtení dokumentu – žádné hádání.

## Co se naučíte

- Jak povolit diagnostický sběrač varování fontů v Aspose.Words.  
- Přesný kód potřebný k **načtení dokumentu Word** s vlastními **font settings**.  
- Jak iterovat přes objekty `WarningInfo` a vypsat každý nahrazený font.  
- Tipy, jak potlačit nechtěná varování nebo poskytnout náhradní fonty.  
- Připravený ukázkový kód, který můžete zkopírovat a vložit do Visual Studia.

### Požadavky

- .NET 6.0 nebo novější (API funguje stejně i na .NET Framework).  
- Aspose.Words pro .NET (NuGet balíček `Aspose.Words`).  
- Soubor Word, který odkazuje na font, který nemáte nainstalovaný (např. `MissingFont.docx`).  

Pokud máte vše připravené, pojďme na to.

## Krok 1 – Povolení diagnostického sběrače (Nastavení font settings)

Nejprve: Aspose.Words zaznamenává varování o nahrazení fontů jen tehdy, když mu to explicitně povolíte. Uděláte to vytvořením objektu `FontSettings` a přiřazením k instanci `LoadOptions`. Představte si to jako zapnutí „debug světel“ pro práci s fonty.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Proč?**  
Bez objektu `FontSettings` zůstane sběrač varování tichý a nikdy se nedozvíte, které fonty byly nahrazeny. Inicializací prázdného objektu umožníme Aspose použít výchozí systémové fonty *a* sledovat jakékoli náhrady.

> **Tip:** Pokud víte, že konkrétní složka obsahuje firemní fonty, nasměrujte `FontSettings` tam pomocí `SetFontsFolder("cesta")`. Tím můžete snížit počet varování o chybějících fontech.

## Krok 2 – Načtení dokumentu s nastavenými možnostmi (Load Word Document)

Jakmile je sběrač aktivní, načtěte svůj soubor `.docx` pomocí stejného `LoadOptions`. V tomto okamžiku Aspose prohledá dokument, najde všechny odkazy na fonty a rozhodne, zda je potřeba provést náhradu.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Proč je to důležité?**  
Kdybyste jen zavolali `new Document("MissingFont.docx")`, použily by se výchozí nastavení *a* seznam varování by zůstal prázdný. Předáním `loadOptions` zajistíte, že diagnostický sběrač je zapojen do načítacího pipeline.

## Krok 3 – Získání a zobrazení varování o nahrazení fontů (Detect Missing Fonts)

Po načtení dokumentu do paměti Aspose uloží všechna varování do `document.WarningCallback.Warnings`. Projděte tuto kolekci, filtrujte podle `WarningType.FontSubstitution` a vytiskněte popis. Každý popis vám řekne, který font chyběl a který byl místo něj použit.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Očekávaný výstup v konzoli**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Tento výstup přesně ukazuje, které fonty chybí na počítači, na kterém kód běží. Nyní můžete rozhodnout, zda chybějící fonty nainstalujete, vložíte do dokumentu, nebo ponecháte náhradu.

![aspose font substitution – výstup konzole zobrazující varování o nahrazení fontů](/images/aspose-font-substitution-console.png)

*Text alt:* aspose font substitution – výstup konzole zobrazující varování o nahrazení fontů

## Krok 4 – Volitelné: Přizpůsobení chování náhrady (Handle Missing Fonts)

Někdy nechcete jen vědět, *že* k náhradě došlo – chcete také řídit, *jak* se to provede. Aspose.Words vám umožní zaregistrovat vlastní `IFontSubstitutionRule`. Níže je rychlý příklad, který vynutí, aby jakýkoli chybějící font byl nahrazen `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Kdy byste to použili?**  
Pokud generujete PDF pro webovou službu a víte, že každý klient dokáže vykreslit `Tahoma`, vynucení této náhrady zaručí vizuální konzistenci bez nutnosti distribuovat desítky souborů s fonty.

## Kompletní funkční příklad (Všechny kroky dohromady)

Zde je celý program, který můžete vložit do nového konzolového projektu. Překompiluje se tak, jak je, pokud máte nainstalovaný NuGet balíček Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Spusťte program, sledujte konzoli a uvidíte každý událost chybějícího fontu vytištěnou. Na základě toho můžete rozhodnout, zda fonty nainstalujete, vložíte, nebo ponecháte náhradu.

## Často kladené otázky

**Q: Funguje to i při konverzi do PDF?**  
Ano. Když později zavoláte `doc.Save("output.pdf")`, všechny fonty, které byly nahrazeny během načítání, budou ty, které se vloží do PDF. Zachycení varování včas vám pomůže vyhnout se neočekávaným změnám fontů ve finálním PDF.

**Q: Co když mám zpracovávat mnoho dokumentů?**  
Zabalte načítací logiku do `try‑catch` bloku a znovu použijte jedinou instanci `FontSettings` napříč dokumenty. Tím snížíte režii a udržíte sběrač varování aktivní pro každý soubor.

**Q: Můžu varování úplně potlačit?**  
Můžete nastavit `loadOptions.WarningCallback = null;` před načtením, ale přijdete o možnost **detekovat chybějící fonty** – což obvykle není žádoucí.

## Závěr

Probrali jsme vše, co potřebujete k ovládnutí **aspose font substitution**: povolení diagnostického sběrače, načtení souboru Word s vlastními **font settings**, extrakci seznamu chybějících fontů a dokonce přepsání výchozího pravidla náhrady, abyste **zvládli chybějící fonty** po svém. Pouhých několik řádků C# vám poskytne úplnou přehlednost o problémech s fonty, které by jinak zůstaly skryté za jemnými změnami rozložení.

Další kroky? Zkuste vložit původní fonty do dokumentu pomocí `FontSettings.SetFontsFolder` nebo prozkoumejte `FontSourceBase` pro načítání fontů z databáze. Můžete také experimentovat se sbírkou `Document.BuiltInStyle`, abyste viděli, jak se změny fontů na úrovni stylu šíří.

Máte další otázky ohledně Aspose.Words nebo správy fontů? Zanechte komentář, prozkoumejte oficiální dokumentaci Aspose, nebo si založte nový projekt a pohrávejte si s výše uvedeným kódem. Šťastné programování a ať se vaše dokumenty vždy vykreslí přesně tak, jak mají!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}