---
category: general
date: 2025-12-29
description: Možnosti načítání Aspose vám umožňují načíst soubory DOCX při přizpůsobení
  nastavení fontů a detekci chybějících fontů. Naučte se, jak načíst DOCX s plnou
  kontrolou.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: cs
og_description: Aspose Load Options vám umožňují načíst soubory DOCX a přitom přizpůsobit
  nastavení fontů a detekovat chybějící písma. Naučte se, jak načíst DOCX s plnou
  kontrolou.
og_title: Aspose možnosti načítání – Načíst DOCX s vlastními nastaveními písma
tags:
- Aspose.Words
- C#
- Document Processing
title: Možnosti načítání Aspose – Načíst DOCX s vlastními nastaveními písma
url: /cs/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – Načtení DOCX s vlastními nastaveními fontů

Už jste se někdy zamýšleli, jak načíst soubor DOCX v C# bez problémů s chybějícími fonty? Nejste sami. **Aspose Load Options** vám dávají možnost přesně řídit, jak se Word dokument otevře, a umožňují nastavit vlastní fonty a dokonce detekovat chybějící fonty ještě předtím, než se stanou problémem.

V tomto tutoriálu projdeme celý proces načtení DOCX pomocí Aspose.Words, konfiguraci **vlastních nastavení fontů** a nastavení varovného zpětného volání, které vám řekne, které fonty chybí. Na konci budete schopni **načíst Word dokument** s jistotou, bez ohledu na to, jaké fonty původní autor použil.

> **Předpoklad** – Potřebujete Aspose.Words pro .NET (nejnovější verze) přidaný do vašeho projektu a základní znalost C#. Žádné další knihovny nejsou vyžadovány.

## Co se naučíte

- Jak vytvořit objekt `LoadOptions` a připojit varovné zpětné volání.  
- Jak nastavit `FontSettings` pro **vlastní nastavení fontů**.  
- Jak skutečně **načíst docx** a ověřit, že chybějící fonty jsou hlášeny.  
- Tipy pro řešení okrajových případů, jako jsou vložené fonty nebo síťové složky s fonty.

## Krok 1: Instalace Aspose.Words a příprava projektu

Nejprve se ujistěte, že je Aspose.W nainstalován. Nejjednodušší cesta je přes NuGet:

```bash
dotnet add package Aspose.Words
```

Jakmile je balíček přidán, vytvořte nový C# konzolový projekt (nebo vložte kód do existující aplikace). Kód, který napíšeme, funguje s .NET 6+ a .NET Framework 4.7.2+, takže jste pokryti v obou případech.

> **Tip:** Pokud cílíte na .NET Core, přidejte na začátek souboru `using System;` – IDE jej obvykle vloží automaticky.

## Krok 2: Konfigurace Aspose Load Options s varovným zpětným voláním

Nyní přichází podstata – **aspose load options**. Třída `LoadOptions` vám umožní doladit, jak se dokument parsuje. Použijeme ji k:

1. Připojení zpětného volání, které se spustí, kdykoli načítač nenajde požadovaný font.  
2. Přiřazení instance `FontSettings`, kterou lze později upravit pro **vlastní nastavení fontů**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**Proč je to důležité:** Bez varovného zpětného volání Aspose tiše nahrazuje chybějící fonty, což může později vést k neočekávanému rozložení. Připojením zpětného volání **detekujete chybějící fonty** včas a můžete se rozhodnout, zda vložíte náhradní font nebo požádáte uživatele o instalaci chybějícího typu písma.

## Krok 3: Načtení DOCX pomocí nakonfigurovaných možností

S připraveným `LoadOptions` je načtení DOCX jedním řádkem. Konstruktor `Document` přijímá cestu k souboru a možnosti, které jsme právě vytvořili.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

Pokud zdrojový soubor odkazuje na font, který není v systému ani ve vlastní složce, uvidíte výstup jako:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

Tato okamžitá zpětná vazba je neocenitelná, když budujete dávkový proces, který musí garantovat vizuální věrnost.

## Krok 4: Ověření načteného dokumentu (volitelné, ale užitečné)

Po načtení můžete chtít potvrdit, že obsah dokumentu je přístupný. Pro rychlou kontrolu vypišme text prvního odstavce.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

Spuštěním programu nyní získáte:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## Krok 5: Okrajové případy a pokročilé tipy

### 5.1 Zpracování vložených fontů

Některé soubory DOCX mají požadované fonty vložené přímo v souboru. Aspose.Words je automaticky použije, takže pro ně nebudete vidět varování. Pokud však úmyslně **načítáte word document** soubory, které odstraňují vložené fonty (např. po konverzi), může být nutné dodat chybějící fonty pomocí `SetFontsFolder`, jak bylo ukázáno dříve.

### 5.2 Použití Memory Stream místo cesty k souboru

Pokud váš DOCX žije v databázi nebo přichází z HTTP požadavku, můžete jej načíst z `MemoryStream`:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

Stejné **aspose load options** se použijí a varovné zpětné volání i nadále funguje.

### 5.3 Globální přepsání substituce fontů

Pokud chcete nahradit chybějící fonty konkrétním náhradním (např. Arial), můžete přidat pravidlo substituce:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

Kombinujte to s varovným zpětným voláním, abyste zaznamenali událost substituce a udrželi výstup konzistentní.

## Krok 6: Kompletní funkční příklad

Níže je kompletní program připravený ke zkopírování, který zahrnuje všechny výše uvedené kroky. Uložte jej jako `Program.cs`, obnovte NuGet balíčky a spusťte.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Očekávaný výstup

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

Pokud žádné fonty nechybí, řádky s varováním se jednoduše neobjeví.

## Vizuální přehled

![aspose load options example](/images/aspose-load-options.png "Diagram showing Aspose Load Options workflow")

*Diagram ukazuje, jak **Aspose Load Options** leží mezi zdrojem souboru a objektem `Document`, řeší rozpoznávání fontů a detekci chybějících fontů.*

## Závěr

Prošli jsme kompletním řešením pro **aspose load options**, ukázali vám přesně **jak načíst docx** při aplikaci **vlastních nastavení fontů** a **detekci chybějících fontů**. Nastavením varovného zpětného volání a případným nasměrováním Aspose na vlastní složku s fonty získáte plnou kontrolu nad problémy s fonty ještě před tím, než ovlivní vykreslování.  

Od sem můžete zkoumat související témata, jako je **load word document** konverze do PDF, přidávání vodoznaků nebo dávkové zpracování desítek souborů ve složce. Stejný vzor – vytvořit `LoadOptions`, připojit zpětná volání a zavolat `new Document(...)` – funguje v celé Aspose.Words API.

Máte otázky ohledně konkrétního okrajového případu, například zpracování jazyků zprava doleva nebo šifrovaných DOCX souborů? Zanechte komentář nebo se podívejte do dokumentace Aspose.Words pro podrobnější informace. Šťastné programování a ať se vaše dokumenty vždy vykreslí přesně tak, jak mají!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}