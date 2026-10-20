---
category: general
date: 2026-06-30
description: Naučte se, jak načítat písma v .NET pomocí LoadOptions, nastavit nastavení
  písma, povolit vlastní písma a detekovat chybějící písma pomocí varovných callbacků.
draft: false
keywords:
- how to load fonts
- set font settings
- how to handle warnings
- enable custom fonts
- detect missing fonts
language: cs
og_description: Jak načíst písma v .NET? Tento průvodce ukazuje, jak nastavit nastavení
  písma, povolit vlastní písma a detekovat chybějící písma pomocí varovných zpětných
  volání.
og_title: Jak načíst fonty v .NET – Nastavit nastavení fontů a varování
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  headline: How to Load Fonts in .NET – Set Font Settings & Warnings
  type: TechArticle
- description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  name: How to Load Fonts in .NET – Set Font Settings & Warnings
  steps:
  - name: Creating `LoadOptions` and configuring **set font settings**.
    text: Creating `LoadOptions` and configuring **set font settings**.
  - name: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
    text: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
  - name: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
    text: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
  - name: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
    text: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
  - name: Saving the document, confirming that the fallback
    text: Saving the document, confirming that the fallback
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Jak načíst fonty v .NET – Nastavit nastavení fontů a varování
url: /cs/net/working-with-fonts/how-to-load-fonts-in-net-set-font-settings-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak načíst písma v .NET – Nastavení písma a varování

Už jste se někdy zamýšleli **jak načíst písma** v .NET dokumentu, aniž byste si trhali vlasy? Nejste v tom sami. Chybějící glyfy, tiché náhradní písma a kryptické varování mohou proměnit jednoduchý generátor reportů v noční můru.  

V tomto tutoriálu projdeme kompletním, připraveným příkladem, který ukazuje **jak načíst písma**, nakonfigurovat **nastavení písma**, **povolit vlastní písma** a **detekovat chybějící písma** pomocí zpracování varování. Na konci budete mít robustní vzor, který můžete vložit do libovolného projektu používajícího Aspose.Words nebo podobnou knihovnu.

> **Rychlý přehled:** vytvoříme objekt `LoadOptions`, připojíme callback pro varování a načteme DOCX, který úmyslně odkazuje na chybějící typ písma. Konzole vytiskne jasnou zprávu vždy, když engine nahradí písmo.

## Co budete potřebovat

- .NET 6.0 nebo novější (kód funguje také na .NET Framework 4.6+)  
- Aspose.Words pro .NET (balíček NuGet ve zkušební verzi stačí)  
- Soubor DOCX, který odkazuje na písmo, které *nemáte* nainstalované (např. `MissingFont.docx`)  

To je vše—žádné další služby, žádné nejasné konfigurační soubory. Pokud máte tyto tři položky, můžete pokračovat.

![diagram příkladu načítání písem](https://example.com/how-to-load-fonts-diagram.png)

*Text obrázku: diagram příkladu načítání písem*

## Krok 1: Vytvořit Load Options a povolit vlastní nastavení písma  

Prvním krokem, když chcete **nastavit nastavení písma**, je vytvořit objekt `LoadOptions`. Do něj vložíte instanci `FontSettings`, která ukazuje na složku obsahující libovolné vlastní soubory .ttf nebo .otf, které můžete potřebovat.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Step 1: Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // Point to a folder that holds extra fonts (optional but useful)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

**Proč je to důležité:** Ve výchozím nastavení Aspose.Words hledá pouze systémově nainstalovaná písma. Pokud váš dokument používá firemní značkové písmo, které je uloženo na síťovém disku, musíte knihovně říct, kde jej najít. To je podstata **povolení vlastních písem**.

## Krok 2: Připojit handler varování pro detekci chybějících písem  

Pokud vynecháte zpracování varování, chybějící glyfy jsou tiše nahrazeny náhradním písmem—často Times New Roman. To může narušit značku nebo dokonce způsobit posuny rozložení. Pro **jak zpracovávat varování**, připojte callback, který kontroluje `WarningType.FontSubstitution`.

```csharp
        // Step 2: Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution detected: {args.Description}");
        };
```

**Tip:** `WarningCallback` se spustí pro *každé* varování, nejen pro chybějící písma. Filtrování podle `WarningType.FontSubstitution` udržuje výstup čistý a přímo odpovídá na otázku **detekovat chybějící písma**.

## Krok 3: Načíst dokument pomocí nakonfigurovaných možností  

Nyní, když jsme připravili možnosti, můžeme konečně **načíst písma** do dokumentu. Konstruktor `Document` přijímá cestu k souboru a `LoadOptions`, které jsme právě vytvořili.

```csharp
        // Step 3: Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);
```

Pokud zdrojový soubor odkazuje na písmo, které není v systémové složce *nebo* ve vlastní složce, kterou jsme nastavili dříve, callback varování ze Krok 2 vytiskne užitečnou zprávu do konzole.

## Krok 4: Ověřit načtenou sadu písem (volitelné, ale poučné)  

Někdy chcete dvakrát zkontrolovat, která písma byla skutečně vyřešena. Aspose.Words poskytuje `FontSettings`, které jste předali, takže můžete vyjmenovat vyřešené zdroje písem.

```csharp
        // Step 4: (Optional) List all font sources that were used
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");
```

Spuštění tohoto úryvku po načtení vytiskne něco jako:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was substituted with 'Arial'.
Loaded font sources:
- FolderFontSource
- SystemFontSource
```

Řádek s varováním potvrzuje, že jsme úspěšně **detekovali chybějící písma**, zatímco seznam ukazuje, že byly prohledány jak systémové, tak vlastní složky.

## Krok 5: Uložit nebo vykreslit dokument  

Jakmile je dokument načten a písma ověřena, můžete pokračovat s jakýmkoli zpracováním—uložit jako PDF, vykreslit do obrázků nebo manipulovat s DOM. Pro úplnost zde je jednorázový řádek, který uloží výsledek jako PDF:

```csharp
        // Step 5: Save the document as PDF (fonts now embedded where possible)
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ Document saved as PDF.");
    }
}
```

Když otevřete PDF, všechny chybějící glyfy budou nahrazeny náhradou, kterou jste viděli ve výstupu konzole. Pokud jste přidali chybějící písmo do `C:\MyCustomFonts`, spusťte program znovu a varování zmizí—důkaz, že **povolení vlastních písem** skutečně funguje.

---

## Kompletní funkční příklad

Zkopírujte celý blok níže do nového konzolového projektu, přidejte balíček Aspose.Words NuGet a stiskněte **Run**. Přizpůsobte cesty k souborům tak, aby odpovídaly vašemu prostředí.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };
        // Point to a folder with extra fonts (if you have any)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);

        // 2️⃣ Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        };

        // 3️⃣ Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);

        // 4️⃣ (Optional) List loaded font sources for debugging
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");

        // 5️⃣ Save as PDF – you’ll see the same warnings if fonts were missing
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ PDF saved successfully.");
    }
}
```

### Očekávaný výstup

```
⚠️ Font substitution: Font 'Papyrus' was substituted with 'Arial'.

Loaded font sources:
- FolderFontSource
- SystemFontSource

✅ PDF saved successfully.
```

Pokud umístíte chybějící soubor `Papyrus.ttf` do `C:\MyCustomFonts` a spustíte program znovu, řádek s varováním zmizí, což potvrzuje, že vlastní složka byla správně použita.

---

## Časté otázky a úskalí

| Question | Answer |
|----------|--------|
| **Co když nemám callback pro varování?** | Dokument se stále načte, ale nebudete vědět, kdy došlo k náhradě. Přidání callbacku je nejjednodušší způsob, jak **zpracovávat varování**. |
| **Mohu načíst písma ze zip souboru?** | Ano—použijte `new FolderFontSource(zipPath, true)` nebo implementujte vlastní `IFontSource`. To stále spadá pod **povolení vlastních písem**. |
| **Potřebuji vkládat písma do PDF?** | Nastavte `doc.SaveOptions.PdfSaveOptions.EmbedFullFonts = true;` před uložením. Vkládání zaručuje, že PDF vypadá stejně na jakémkoli počítači. |
| **Co když dokument používá písmo, které je licencované a nesmí být distribuováno?** | Stále můžete *detekovat* chybějící písmo pomocí varování, ale neměli byste jej vkládat, pokud nemáte práva. Zvažte náhradu podobným open‑source písmem. |

---

## Shrnutí

Probrali jsme **jak načíst písma** v .NET tím, že:

1. Vytvořením `LoadOptions` a nakonfigurováním **nastavení písma**.  
2. **Povolením vlastních písem** ukázáním na složku s extra typy písem.  
3. **Jak zpracovávat varování** pomocí `WarningCallback`, který vypisuje zprávy o náhradě písma.  
4. **Detekovat chybějící písma** filtrováním `WarningType.FontSubstitution`.  
5. Uložením dokumentu, potvrzujíc, že náhrada

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Nastavit složky písem – systémová a vlastní](/words/english/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/)
- [Jak detekovat písma v Aspose.Words – zpracovat varování a nastavení](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Jak zachytit písma v Aspose.Words – kompletní průvodce](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}