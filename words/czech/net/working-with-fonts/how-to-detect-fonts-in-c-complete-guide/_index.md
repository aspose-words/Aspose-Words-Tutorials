---
category: general
date: 2026-04-02
description: Jak detekovat písma v dokumentech C# pomocí Aspose.Words. Naučte se konfigurovat
  nastavení písem a efektivně řešit chybějící písma.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: cs
og_description: Jak detekovat písma v dokumentech C# pomocí Aspose.Words. Tento průvodce
  ukazuje, jak nastavit nastavení písma a jak řešit chybějící písma.
og_title: Jak detekovat písma v C# – kompletní průvodce
tags:
- C#
- Aspose.Words
- Document Processing
title: Jak detekovat písma v C# – kompletní průvodce
url: /cs/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak detekovat písma v C# – Kompletní průvodce

Už jste se někdy zamýšleli **jak detekovat písma**, která chybí nebo jsou nahrazena při načítání Word dokumentu v .NET? Nejste v tom sami — vývojáři často narazí na problém, když dokument odkazuje na písmo, které není nainstalováno na serveru. Dobrou zprávou je, že Aspose.Words vám poskytuje čistý programový způsob, jak tyto mezery odhalit.

V tomto tutoriálu projdeme praktickým příkladem, který nejen ukazuje **jak detekovat písma**, ale také demonstruje, jak **konfigurovat nastavení písma** a **zpracovat chybějící písma** elegantně. Na konci budete mít připravený útržek kódu, který vytiskne každé varování o substituci písma, takže jej můžete zaznamenat, upozornit nebo nahradit písma podle potřeby.

---

## Co budete potřebovat

- **Aspose.Words for .NET** (nejnovější verze funguje nejlépe; kód níže cílí na .NET 6+)
- Vývojové prostředí .NET (Visual Studio, Rider nebo VS Code)
- Ukázkový `.docx`, který odkazuje na písmo, které nemáte nainstalováno (skvělé pro testování)

Žádné další NuGet balíčky kromě Aspose.Words nejsou vyžadovány a řešení funguje na Windows, Linuxu i macOS.

---

## Krok 1: Instalace a reference Aspose.Words

Nejprve přidejte knihovnu do svého projektu. NuGet příkaz je jednoduchý:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Pokud pracujete na CI serveru, připněte verzi balíčku, abyste se vyhnuli neočekávaným breaking changes.

---

## Krok 2: Konfigurace nastavení písma (a příprava Load Options)

Než otevřete dokument, můžete Aspose.Words říct, kde má hledat náhradní písma. Toto je část **konfigurovat nastavení písma**, která zabraňuje motoru tiše zaměňovat písma, která možná nechcete.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Proč to dělat? Pokud dokument odkazuje na *Comic Sans*, ale váš server má jen *Calibri*, Aspose.Words nahradí *Calibri* a vyvolá varování. Konfigurací vyhledávací cesty snížíte nechtěná překvapení.

---

## Krok 3: Načtení dokumentu s připravenými možnostmi

Nyní skutečně otevřeme soubor. `LoadOptions`, které jsme vytvořili v předchozím kroku, předáme přímo konstruktoru `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Pokud soubor nelze najít nebo je poškozený, vyvolá se výjimka — v produkčním kódu ji možná budete chtít zachytit pomocí try/catch.

---

## Krok 4: Prohledání varování dokumentu pro substituce písma

Aspose.Words sbírá seznam varování během parsování. Mezi nimi `FontSubstitutionWarning` vám přesně řekne, které písmo bylo zaměněno.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

Kolekce `Warnings` může obsahovat i jiné položky (např. `DocumentStructureWarning`). Filtrování na `FontSubstitutionWarning` zajišťuje, že hlásíme jen **zpracování chybějících písem**, o které nám jde.

---

## Krok 5: Sestavení všeho dohromady — kompletní spustitelný příklad

Níže je celý program. Zkopírujte jej do nové konzolové aplikace a spusťte; uvidíte každé chybějící písmo vytištěné do konzole.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Očekávaný výstup** (příklad):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Pokud dokument používá jen písma, která jsou na stroji dostupná, uvidíte místo toho řádek „No font substitutions detected“.

---

## Okrajové případy a časté otázky

### Co když dokument neobsahuje **žádná varování** vůbec?

To jednoduše znamená, že každé odkazované písmo bylo nalezeno ve složkách, které jste nakonfigurovali. Příznak `anySubstitutions` v příkladu pokrývá tento případ.

### Mohu **logovat** varování do souboru místo konzole?

Určitě. Nahraďte volání `Console.WriteLine` loggerem dle vašeho výběru (Serilog, NLog, atd.). Objekt `WarningInfo` také poskytuje `WarningType` a `WarningMessage`, pokud potřebujete podrobnější informace.

### Jak mohu **ignorovat** určitá písma, například firemní značkové písmo, které by nikdy nemělo být nahrazeno?

Můžete přidat vlastní pravidlo substituce:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Nyní Aspose.Words nahradí *MyBrandFont* jen uvedenými alternativami a stále obdržíte varování, na které můžete reagovat.

### Funguje to v **Linux** kontejnerech?

Ano — stačí zajistit, aby byl připojený adresář s potřebnými soubory `.ttf`/`.otf` a nasměrovat `SetFontsFolder` na něj. Aspose.Words se nespoléhá na písma nainstalovaná v OS.

---

## Vizualizace

![schéma jak detekovat písma](detect-fonts.png "Diagram ukazující kroky pro detekci písem v dokumentu")

*Image alt text:* **jak detekovat písma** schéma ilustrující konfiguraci, načítání a kontrolu varování.

---

## Shrnutí — Co jsme se naučili

- **Jak detekovat písma**, která chybí nebo jsou nahrazena pomocí varování Aspose.Words.  
- Jak **konfigurovat nastavení písma** tak, aby ukazovalo na vlastní složky s písmy a nastavit výchozí náhradní písmo.  
- Strategie pro **zpracování chybějících písem**, od logování po vlastní pravidla substituce.

Vše toto zapadá do kompaktní, samostatné konzolové aplikace, kterou můžete vložit do libovolného .NET řešení.

---

## Další kroky a související témata

- **Vkládání písem** přímo do výstupního dokumentu, aby se předešlo budoucím substitucím (`SaveOptions` s `EmbedFullFonts`).  
- **Programová výměna písem** — nahradit chybějící písma konkrétní alternativou před uložením.  
- **Ladění výkonu** — kešovat `FontSettings` při zpracování mnoha dokumentů najednou.  

Pokud vás tato témata zajímají, vyhledejte *configure font settings* a *handle missing fonts* — nasměrují vás k podrobnějším informacím o správě písem s Aspose.Words.

---

Happy coding! Máte podivný okrajový případ s písmy? Zanechte komentář a společně to vyřešíme.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}