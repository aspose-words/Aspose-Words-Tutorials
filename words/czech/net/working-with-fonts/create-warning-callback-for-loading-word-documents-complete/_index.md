---
category: general
date: 2026-03-25
description: Vytvořte varovný callback pro načtení dokumentu Word a detekci chybějících
  fontů. Naučte se, jak nastavit fonty v Aspose.Words pro .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: cs
og_description: Vytvořte výstražný callback pro načtení dokumentu Word při detekci
  chybějících fontů. Tento průvodce ukazuje, jak nastavit fonty v Aspose.Words.
og_title: Vytvořit varovný callback – Načíst Word dokument a detekovat chybějící fonty
tags:
- Aspose.Words
- C#
- Font handling
title: Vytvořte varovný callback pro načítání Word dokumentů – kompletní průvodce
url: /cs/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření varovného callbacku – Načtení Word dokumentu a detekce chybějících fontů

Už jste někdy potřebovali **vytvořit varovný callback** při načítání Word dokumentu a přemýšleli, proč některé fonty prostě zmizí? Nejste v tom sami. V mnoha podnikových aplikacích způsobují chybějící fonty katastrofy v rozvržení a bez správného callbacku si problém možná vůbec neuvědomíte.  

Dobrá zpráva? S Aspose.Words pro .NET můžete **načíst Word dokument**, **detekovat chybějící fonty** a **nastavit konfiguraci fontů** během několika úhledných řádků kódu. V tomto tutoriálu projdeme kompletním, spustitelným příkladem, vysvětlíme, proč je každá část důležitá, a ukážeme vám, jak ověřit, že varovný callback dělá svou práci.

> **Co si odnesete**  
> * Kompletní C# program, který načte DOCX, nahlásí jakékoli nahrazení fontů a umožní vám přizpůsobit cesty pro vyhledávání fontů.  
> * Porozumění třídám `FontSettings`, `LoadOptions` a `IWarningCallback`.  
> * Tipy pro řešení okrajových případů, jako jsou vložené fonty nebo systémové složky s fonty.

---

## Prerequisites

- .NET 6+ (nebo .NET Framework 4.7.2+) s C# kompilátorem.  
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`).  
- Ukázkový Word soubor (`input.docx`), který používá alespoň jeden font, který není nainstalován na stroji (např. *Calibri Light* v minimálním Windows kontejneru).  
- Základní znalost C# konzolových aplikací.

Žádné další knihovny nejsou potřeba; vše je součástí Aspose.Words.

---

## Step 1: Create warning callback to detect missing fonts

**Primární** část tohoto puzzle je třída, která implementuje `IWarningCallback`. Aspose.Words zavolá tento callback vždy, když narazí na situaci, která vyžaduje varování – nejčastěji jde o nahrazení fontu.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Proč je to důležité** – Bez callbacku byste museli po faktu procházet logy. Zpracováním varování v reálném čase můžete rozhodnout, zda načítání přerušit, nahradit chybějící font náhradním, nebo jen zaznamenat problém pro pozdější revizi.

---

## Step 2: Configure FontSettings for custom font handling

Než skutečně načteme dokument, můžeme Aspose.Words říct, kde má hledat fonty, které nejsou nainstalovány v systému. K tomu slouží `FontSettings`.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Proč je to důležité** – Ukazováním Aspose.Words na složku, která obsahuje chybějící fonty, často zabráníte úplnému nahrazení. Když to není možné, rozumná výchozí volba (např. *Arial*) udrží dokument čitelný.

---

## Step 3: Load Word document with the configured warning callback

Nyní vše spojíme: vytvoříme `LoadOptions`, připojíme naše `FontSettings` a `FontWarningHandler` a nakonec načteme dokument.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Proč je to důležité** – `LoadOptions` je jediné místo, kde nastavujete *jak* se dokument čte. Poskytnutím jak konfigurace fontů, tak varovného callbacku zajistíme, že jakýkoli chybějící font bude hledán na správných místech **a** okamžitě nahlášen.

---

## Step 4: Verify the output – what should you see?

Spusťte program z konzole. Pokud `input.docx` používá font, který není nainstalován a také není v `C:\SharedFonts`, uvidíte něco jako:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Pokud jsou všechny fonty dostupné, řádek s varováním se jednoduše neobjeví. Tento okamžitý zpětný kanál je neocenitelný během automatizovaných pipeline pro zpracování dokumentů, kde by tiché nahrazení fontů mohlo porušit brandové směrnice.

---

## Step 5: Common pitfalls and best‑practice tips

| Pitfall | How to avoid it |
|---------|-----------------|
| **Zapomněli jste odkazovat na `Aspose.Words.Fonts`** | Ujistěte se, že na začátku máte `using Aspose.Words.Fonts;`; jinak kompilátor bude stěžovat na chybějící typy. |
| **Cesta ke složce s fonty je špatná** | Dvakrát zkontrolujte cestu a nastavte `recursive: true`, pokud máte podsložky. Pro ladění použijte `Path.GetFullPath`. |
| **Více varovných callbacků** | Aspose.Words respektuje jen poslední přiřazený `WarningCallback`. Používejte jediný handler, který deleguje, pokud potřebujete složitější logiku. |
| **Běh na serveru bez UI** | Výpisy do konzole jsou v pořádku, ale pro webové aplikace můžete raději logovat do souboru nebo monitorovacího systému místo `Console.WriteLine`. |
| **Velké dokumenty způsobují pokles výkonu** | Znovu použijte jedinou instanci `FontSettings` napříč více načteními; opakované vytváření může být nákladné. |

**Pro tip:** Pokud potřebujete *shromažďovat* varování pro pozdější analýzu, uložte je do `List<string>` uvnitř handleru místo přímého výpisu.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Pak můžete po načtení dokumentu prozkoumat `handler.Messages`.

---

## Step 6: Extending the solution – what if I need to embed a fallback font?

Někdy chcete, aby chybějící font byl *vložen* do výstupního PDF, aby downstream prohlížeče viděly přesně stejný vzhled. Po načtení dokumentu můžete vynutit vložení:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Tento úryvek ukazuje, jak lze stejný **configure font settings** přístup rozšířit i mimo samotné načítání.

---

## Full runnable example

Níže je kompletní program, který můžete zkopírovat a vložit do nového projektu Console App. Obsahuje všechny výše diskutované části.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Očekávaný výstup** (když je přítomen chybějící font):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Pokud nedojde k žádnému nahrazení, zobrazí se jen úspěšné zprávy.

---

## Conclusion

Právě jsme **vytvořili varovný callback**, který spolehlivě **detekuje chybějící fonty** při **načítání Word dokumentu** s Aspose.Words, a ukázali jsme, jak **nastavit konfiguraci fontů**, aby knihovna věděla, kde hledat fonty a jaký fallback použít. Propojením `FontSettings` a `LoadOptions` získáte plnou přehlednost o problémech s fonty — žádné tiché chyby v rozvržení.

Další kroky? Zkuste vyměnit `FontWarningHandler` za logger zapisující do databáze, nebo experimentujte s **pravidly nahrazování fontů**, abyste mapovali konkrétní chybějící fonty na schválené alternativy značky. Můžete také prozkoumat **dynamické načítání fontů** z cloudového úložiště, pokud vaše aplikace běží v kontejnerizovaném prostředí.

Máte otázky k určitému okrajovému případu — například jak zacházet s OpenType funkcemi nebo jak pracovat s šifrovanými DOCX soubory? Zanechte komentář níže a šťastné programování!  

---

![Diagram vytvoření varovného callbacku](https://example.com/images/create-warning-callback.png "Diagram vytvoření varovného callbacku")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}