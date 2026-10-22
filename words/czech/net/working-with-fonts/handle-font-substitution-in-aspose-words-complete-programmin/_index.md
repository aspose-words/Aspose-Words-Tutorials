---
category: general
date: 2026-06-17
description: Řešte nahrazování písem v Aspose.Words a rychle odhalte chybějící písma
  pomocí tohoto krok‑za‑krokem tutoriálu pro vývojáře .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: cs
og_description: Zvládněte nahrazování písem v Aspose.Words a naučte se, jak v dokumentech
  detekovat chybějící písma pomocí přehledných ukázek kódu.
og_title: Řešení nahrazení fontů v Aspose.Words – Kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Zpracování náhrady písma v Aspose.Words – Kompletní programovací průvodce
url: /cs/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zpracování náhrady písma v Aspose.Words – Kompletní programovací průvodce

Už jste se někdy zamýšleli, jak **zpracovat náhradu písma**, když Word dokument odkazuje na písmo, které není nainstalováno na serveru? Nejste v tom sami. V mnoha reálných aplikacích – například generátorech faktur nebo automatizovaných službách pro tvorbu zpráv – chybějící písma způsobují tiché náhrady, které zničí rozvržení.  

Dobrou zprávou je, že Aspose.Words poskytuje vestavěný varovný systém, který vám umožní **detekovat chybějící písma** a reagovat tak, jak potřebujete. V tomto tutoriálu si projdeme registraci varovného handleru, načtení dokumentu a získání přesných událostí náhrady písma, o kterých potřebujete vědět. Na konci také uvidíte, jak odpovědět na klasickou otázku „**jak detekovat chybějící písma**?“ čistým, produkčně připraveným kódem.

## Co tento tutoriál pokrývá

* Nastavení Aspose.Words tak, aby generovalo varování pro každou náhradu písma.  
* Zachycení těchto varování v uživatelském handleru, abyste je mohli logovat, nahrazovat nebo přerušit.  
* Použití zachycených dat k **detekci chybějících písem** před uložením nebo vykreslením dokumentu.  
* Tipy pro řešení okrajových případů – například když je tichá náhrada písma vybrána automaticky.  
* Kompletní, spustitelný příklad, který můžete vložit do libovolné .NET konzolové aplikace.

> **Předpoklady** – Budete potřebovat aktuální .NET SDK (6.0+ funguje dobře), platnou licenci Aspose.Words pro .NET (nebo dočasný evaluační klíč) a ukázkový DOCX, který úmyslně odkazuje na písmo, které nemáte nainstalováno. Žádné další knihovny třetích stran nejsou vyžadovány.

---

## ## Zpracování náhrady písma pomocí vlastního varovného handleru

Aspose.Words vyvolá objekt `WarningInfo` pokaždé, když nenajde požadované písmo. Ve výchozím nastavení jsou tato varování ignorována, což je důvod, proč často nikdy nepoznáte, že došlo k náhradě. Pro **zpracování náhrady písma** nahradíte výchozí varovný handler tím, který skutečně něco udělá.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Proč to funguje

* `FontSettings.DefaultWarningHandler` je globální statická vlastnost – jakmile ji nastavíte, **každá** operace Aspose.Words v aktuálním AppDomain použije váš delegát.  
* `WarningInfoCollectionHandler` přijímá objekt `WarningInfo`, který obsahuje `WarningType` a čitelný `Description`. Filtrování na `WarningType.FontSubstitution` zajistí, že uvidíte jen události, které vás zajímají.  
* Volání `doc.Save` přinutí knihovnu vyřešit všechna písma, což je okamžik, kdy se varování spustí. Pokud potřebujete dokument jen prohlédnout bez ukládání, můžete místo toho zavolat `doc.UpdatePageLayout()`.

**Očekávaný výstup do konzole** (předpokládejme, že chybějící písmo je „Papyrus“):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Tento řádek je vaším důkazem, že knihovna **detekovala chybějící písma** a zvolila náhradní.

---

## ## Detekce chybějících písem před vykreslením

Někdy chcete proces úplně zastavit, pokud chybí požadované písmo – například protože firemní směrnice vyžadují přesnou typografii. Varovný handler lze rozšířit tak, aby sbíral všechny zprávy o chybějících písmenech do seznamu, a pak můžete učinit rozhodnutí.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Jak to odpovídá na otázku „jak detekovat chybějící písma“

* Seznam `missingFonts` funguje jako evidence každé události náhrady.  
* Po volání `UpdatePageLayout` můžete seznam prozkoumat a rozhodnout, zda pokračovat, logovat nebo vyhodit výjimku.  
* Tento vzor funguje pro jakýkoli výstupní formát (PDF, HTML, obrázky), protože varovný systém je nezávislý na formátu.

---

## ## Pokročilý tip: Nahrazení chybějících písem konkrétní náhradou

Pokud máte firemní písmo, které musí být použito, můžete Aspose.Words říct, aby automaticky nahradil jakékoli chybějící písmo vaším náhradním písmem. To je užitečné, když chcete, aby dokument *stále* vypadal přijatelně bez ručního post‑processingu.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Umístěte výše uvedený úryvek **před** načtením dokumentu. Nyní bude jakékoli chybějící písmo – bez ohledu na jeho původní název – vyměněno za „Calibri“ (nebo „Arial“, pokud Calibri není k dispozici). Varování stále obdržíte, ale dokument se vykreslí s písmem, které kontrolujete.

---

## ## Časté úskalí a jak se jim vyhnout

| Úskalí | Proč se to děje | Řešení |
|---------|----------------|-----|
| **Varování zmizí po prvním volání** | Statický `DefaultWarningHandler` je později v aplikaci přepsán. | Nastavte handler **jednou** při startu aplikace, nebo si uchovejte referenci a při změně ji znovu přiřaďte. |
| **Je hlášeno jen první chybějící písmo** | Některé API dávkují varování; musíte zavolat `UpdatePageLayout` nebo `Save`, aby se fronta vyprázdnila. | Vynutíte aktualizaci rozvržení nebo uložení ve formátu, který chcete generovat. |
| **Náhrada se stále provádí i po přerušení** | Varovný handler běží *po* tom, co již k náhradě došlo. | Použijte handler k **logování** a poté vyhoďte výjimku, aby se další zpracování zastavilo. |
| **Chybějící písma v Linuxových kontejnerech** | Linux často postrádá katalog písem Windows, což vede k mnoha náhradám. | Připojte požadovaná písma do kontejneru nebo použijte `FontSettings.SetFontsFolder` k nasměrování na vlastní adresář s písmy. |

---

## ## Detekce náhrady písma ve scénáři Web API

Pokud služby dokumentů poskytujete přes ASP.NET Core, pravděpodobně nechcete zapisovat do konzole. Místo toho sbírejte varování a vraťte je jako součást HTTP odpovědi.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Nyní API **detekuje chybějící písma** a vrací jasný JSON payload před tím, než je vygenerován jakýkoli PDF. Jedná se o praktickou ukázku „jak detekovat chybějící písma“ v produkčním servisu.

---

## ## Testování vaší implementace

1. **Vytvořte testovací DOCX**, který odkazuje na písmo, o kterém víte, že není na stroji (např. „Comic Sans MS“ na minimalistickém Docker image).  
2. Spusťte konzolovou aplikaci nebo API endpoint.  
3. Ověřte, že konzole (nebo HTTP odpověď) vypisuje varování o náhradě.  
4. Volitelně otevřete vzniklý PDF a zkontrolujte vlastnosti písma – Aspose.Words by měl ukazovat náhradní písmo, které jste nastavili.

Pokud vidíte varování, ale PDF stále používá neočekávané písmo, zkontrolujte pořadí v `SubstitutionSettings`; první shoda vyhrává.

---

## ## Závěr

Probrali jsme vše, co potřebujete k **zpracování náhrady písma** v Aspose.Words, od registrace varovného handleru po programatickou **detekci chybějících písem** a jejich nahrazení firemním typem písma. Využitím vestavěného varovného systému získáte plnou přehlednost o každé události „písmo nenalezeno“, což přímo odpovídá na otázku „**jak detekovat chybějící písma**?“ každého vývojáře, který automatizuje tvorbu dokumentů.

Co dál? Zkuste kombinovat tuto logiku s **dynamickým načítáním písem** (`FontSettings.SetFontsFolder`) pro podporu uživatelských fontů nahrávaných za běhu, nebo rozšiřte varovný handler tak, aby záznamy zapisoval do centrálního logovacího systému jako je Serilog. Čím více instrumentujete práci s písmy, tím spolehlivější bude vaše dokumentová pipeline.

Máte složitý scénář náhrady písma, se kterým bojujete? Zanechte komentář níže a pojďme to společně vyřešit. Šťastné kódování!


## Co byste se měli naučit dál?


Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}