---
category: general
date: 2026-05-29
description: Naučte se, jak nastavit FontSettings v Aspose.Words a elegantně řešit
  chybějící písma. Krok za krokem průvodce s kompletním kódem a osvědčenými postupy.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: cs
og_description: Jak nastavit FontSettings v Aspose.Words a rychle řešit chybějící
  písma. Postupujte podle tohoto návodu pro kompletní, spustitelné řešení.
og_title: Jak nastavit FontSettings – řešit chybějící písma
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Jak nastavit FontSettings – řešení chybějících fontů
url: /cs/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nastavit FontSettings – Řešení chybějících fontů

Už jste se někdy zamysleli **jak nastavit FontSettings**, když pracujete s Aspose.Words a najednou narazíte na dokument, který odkazuje na font, který nemáte nainstalovaný? Je to častý problém, zejména při zpracování souborů dodaných klientem na serveru, který má jen minimální sadu fontů. Dobrá zpráva? Můžete tyto mezery zachytit a **zpracovat chybějící fonty** bez toho, aby se vaše aplikace zhroutila nebo vytvářela ošklivé PDF.

V tomto tutoriálu si projdeme reálný scénář: načtení DOCX, který požaduje „Calibri“, zatímco váš Linux kontejner má jen „DejaVu Sans“. Uvidíte přesně, jak nakonfigurovat FontSettings, přihlásit se k upozorněním na substituci a dodat náhradní fonty, aby se dokument vykreslil tak, jak autor zamýšlel. Žádné zbytečnosti – jen kód, který můžete dnes vložit do svého projektu.

## Požadavky

- .NET 6.0 nebo novější (API funguje stejně na .NET Framework 4.7+)
- Aspose.Words pro .NET 23.10 nebo novější (název NuGet balíčku je `Aspose.Words`)
- Základní vývojové prostředí C# (Visual Studio, Rider nebo VS Code)

Pokud máte vše připravené, pojďme na to.

## Krok 1: Vytvořte FontSettings a naslouchejte událostem substituce

Srdcem řešení je objekt `FontSettings`. Připojením obslužné rutiny k jeho události `FontSubstitutionWarning` získáte živé hlášení pokaždé, když Aspose.Words musí nahradit chybějící typ písma.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Proč je to důležité:**  
Když engine nenajde *Calibri*, může tiše přejít na *Arial*. Posloucháním varování si udržujete transparentní auditní stopu – ideální pro ladění nebo reportování souladu.

> **Tip:** Pokud spouštíte tento kód na CI serveru, přesměrujte výstup do logovacího souboru, abyste po dávkovém běhu mohli zkontrolovat, které fonty chyběly.

## Krok 2: Připojte FontSettings k LoadOptions

`LoadOptions` je vstupní brána pro řízení toho, jak se dokument parsuje. Přiřazením právě nakonfigurovaných `FontSettings` zajistíte, že každé následné načtení `Document` bude respektovat naši logiku substituce.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Co se děje pod kapotou?**  
Během konstruktoru `Document` Aspose.Words načte XML DOCX, vyřeší odkazy na fonty a – pokud font nenajde – spustí varování, které jsme nastavili dříve. Bez tohoto háčku byste o provedené substituci nikdy neveděli.

## Krok 3: Načtěte dokument a (volitelně) definujte náhradní fonty

Nyní konečně načteme soubor do paměti. Pokud už máte složku s náhradními fonty (např. adresář OpenType fontů dodávaných s aplikací), řekněte `FontSettings`, kde má hledat. Tento krok je volitelný, ale často nejčistší způsob, jak *zpracovat chybějící fonty*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Upozornění na okrajové případy:**  
Pokud dokument obsahuje vlastní font vložený jako binární stream, Aspose.Words jej použije automaticky – není potřeba substituce. Varování se spustí jen pro *chybějící* systémové fonty.

### Ověření výsledku

Po načtení můžete dokument uložit do PDF nebo Word, abyste se ujistili, že vše vypadá správně.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

Když spustíte program, konzole vypíše řádky jako:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Pokud vidíte tyto zprávy, úspěšně jste **zpracovali chybějící fonty** a přesně víte, které substituce proběhly.

## Krok 4: Pokročilé – Vlastní pravidla substituce fontů (volitelné)

Někdy potřebujete deterministické mapování, např. vždy nahradit *Times New Roman* fontem *Liberation Serif*. To můžete dosáhnout pomocí `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Proč to dělat?**  
Explicitní pravidla vám dávají kontrolu nad typografií, zajišťují konzistenci značky napříč generovanými PDF, zejména když vytváříte marketingové materiály.

## Časté úskalí a jak se jim vyhnout

| Problém | Příznak | Řešení |
|---------|---------|-----|
| **Žádný výstup varování** | Myslíte si, že jsou fonty v pořádku, ale dokument vypadá špatně. | Ujistěte se, že `FontSubstitutionWarning` je připojen **před** načtením dokumentu. |
| **Složka s náhradními fonty není prohledána** | Substituce stále přechází na systémové výchozí fonty. | Zavolejte `SetFontsFolder(path, true)` s druhým argumentem `true`, aby se prohledávaly podadresáře. |
| **Pokles výkonu při velkých dávkách** | Načítání 10 000 dokumentů je pomalé. | Cacheujte jedinou instanci `FontSettings` a znovu ji používejte při načítání; neprovádějte její vytvoření pokaždé. |
| **Ignorované vložené fonty** | Očekávali jste, že se použije vlastní vložený font, ale dochází k substituci. | Ověřte, že zdrojový DOCX skutečně vložený font obsahuje (zkontrolujte ve Word → Soubor → Informace → Fonty). |

## Kompletní funkční příklad

Níže je kompletní program připravený ke zkopírování. Ukazuje vše od obsluhy událostí až po uložení finálního PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Očekávaný výstup v konzoli** (příklad):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Spusťte program, otevřete `Output.pdf` a uvidíte text vykreslený s náhradními fonty – žádné chybějící znaky, žádné pády.

## Závěr

Nyní máte solidní, produkčně připravený vzor pro **nastavení FontSettings** v Aspose.Words a **elegantní zpracování chybějících fontů**. Připojením události `FontSubstitutionWarning`, nasměrováním na složku s náhradními fonty a (v případě potřeby) definováním explicitních pravidel substituce získáte úplnou přehlednost a kontrolu nad typografií v automatizovaných dokumentových pipelinech.

Co dál? Zkuste přidat vlastní kolekci fontů pro značkové typy, nebo prozkoumejte API `FontSourceBase` pro načítání fontů z databáze či cloudového úložiště. Stejné principy platí – stačí připojit jiný zdroj do `FontSettings`.

Máte otázky ohledně okrajových případů, jako je zpracování skriptů zprava doleva nebo emoji fontů? Zanechte komentář níže a šťastné kódování!

## Co byste se měli naučit dál?

- [Jak zachytit fonty v Aspose.Words – Kompletní průvodce](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Jak detekovat fonty v Aspose.Words – Zpracování varování a nastavení](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Jak načíst DOCX a detekovat chybějící fonty – Kompletní C# průvodce](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}