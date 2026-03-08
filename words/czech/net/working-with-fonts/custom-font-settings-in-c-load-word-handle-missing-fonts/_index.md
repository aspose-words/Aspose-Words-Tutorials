---
category: general
date: 2026-03-08
description: Vlastní nastavení písma vám umožňuje nastavit parametry písma, bezpečně
  načíst dokument Word a zpracovat chybějící písma pomocí Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: cs
og_description: Vlastní nastavení písma vám umožňuje nastavit nastavení písma, bezpečně
  načíst dokument Word a zpracovat chybějící písma pomocí Aspose.Words.
og_title: Vlastní nastavení fontů v C# – Načítání Wordu a řešení chybějících fontů
tags:
- Aspose.Words
- C#
- Font Management
title: Vlastní nastavení písma v C# – načíst Word a zpracovat chybějící písma
url: /cs/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

Translate bullet points.

Then "## Conclusion" etc.

Translate final paragraph.

Make sure to keep placeholders.

Also keep any code block placeholders unchanged.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vlastní nastavení fontů v C# – Načtení Wordu a zpracování chybějících fontů

Už jste se někdy zamýšleli, jak **vlastní nastavení fontů** funguje, když Word soubor odkazuje na fonty, které nemáte nainstalované? Je to častý problém – dokument vypadá dobře na jednom počítači, a najednou se na jiném každý odstavec přepne na náhradní font.

Dobrá zpráva? S Aspose.Words můžete **nastavit fonty**, **načíst obsah Word dokumentu** a **zpracovat chybějící fonty** v jednom přehledném postupu. Níže najdete kompletní, připravený příklad, který přesně ukazuje, jak na to, a také „proč“ za každým krokem.

## Co se naučíte

V tomto průvodci se podíváme na:

* Vytvoření objektu `LoadOptions` a připojení instance `FontSettings`.  
* Registraci callbacku pro varování, abyste viděli, které fonty jsou nahrazeny.  
* Načtení souboru DOCX, který může postrádat fonty, a výpis detailů o substitucích do konzole.  

Na konci budete schopni nasadit svou C# aplikaci s jistotou, že každý scénář s chybějícím fontem je zaznamenán a může být později řešen.

> **Předpoklad:** Aspose.Words pro .NET (v23.12 nebo novější) nainstalovaný přes NuGet a základní znalost C# konzolových aplikací.

---

## Vlastní nastavení fontů – Konfigurace LoadOptions

Prvním, co potřebujete, je objekt `LoadOptions`. Ten říká Aspose.Words, jak má zacházet s načítaným souborem. Přidáním čerstvé instance `FontSettings` poskytujete knihovně místo, kde má hledat vlastní fonty.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Proč je to důležité:**  
Pokud vynecháte `FontSettings`, Aspose.Words použije výchozí kolekci systémových fontů. To znamená, že jakýkoli chybějící font bude tiše nahrazen a nebudete vědět, které byly vyměněny. Vytvořením explicitního kontejneru `FontSettings` získáte plnou kontrolu nad procesem vyhledávání.

---

## Nastavení fontů na LoadOptions

Nyní, když máme objekt `FontSettings`, možná se ptáte, kam ho nasměrovat. Obvykle přidáte složku, která obsahuje fonty, jež distribuujete se svou aplikací:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Pokud nemáte soukromou složku, můžete tento blok vynechat – Aspose.Words i tak bude hlásit chybějící fonty pomocí callbacku pro varování.*

**Tip:** Použijte příznak `recursive: true`, pokud jsou vaše fonty rozptýlené v podadresářích. Ušetříte si ruční přidávání každé cesty.

---

## Načtení Word dokumentu s vlastním nastavením fontů

S připravenými možnostmi je načtení dokumentu hračka. Konstruktor `Document` přijímá cestu k souboru a `LoadOptions`, které jsme právě vytvořili.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Co se děje pod kapotou?**  
Aspose.Words parsuje DOCX, kontroluje každou referenci `<w:font>` a konzultuje poskytnuté `FontSettings`. Pokud font není nalezen, spustí varování typu `FontSubstitution`. Náš vlastní handler (zobrazený níže) tato varování zachytí.

---

## Zpracování chybějících fontů pomocí callbacku pro varování

Rozhraní `IWarningCallback` vám umožní reagovat na jakékoli problémy, které nastanou během načítání. Implementace je přímočará:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Když je dokument načten, každý chybějící font způsobí řádek jako:

```
Font substituted: Arial -> Liberation Sans
```

**Proč to logovat:**  
V produkci můžete tyto zprávy přesměrovat do souboru nebo telemetrického systému, což usnadní identifikaci fontů, které je potřeba zabalení nebo licencovat.

---

## Kompletní funkční příklad

Níže je samostatný konzolový program, který spojuje všechny části dohromady. Zkopírujte jej do nového .NET Core konzolového projektu a spusťte **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Očekávaný výstup** (předpokládáme, že `input.docx` používá font, který nemáte):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Pokud jsou všechny fonty přítomny, uvidíte jen poslední potvrzovací řádek.

---

## Často kladené otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Co když potřebuji vložit chybějící fonty do PDF?** | Po načtení zavolejte `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` a poté povolte vkládání pomocí `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Mohu varování potlačit místo jejich logování?** | Ano – nastavte `loadOptions.WarningCallback = null;` nebo implementujte callback tak, aby ignoroval ne‑fontová varování. |
| **Funguje to i s `.doc` a `.rtf` soubory?** | Rozhodně. Stejný objekt `LoadOptions` platí pro jakýkoli formát podporovaný Aspose.Words. |
| **Je callback thread‑safe?** | Callback běží ve stejném vlákně, které načítá dokument, takže můžete bezpečně zapisovat do konzole. Pro vícevláknové scénáře použijte souběžnou kolekci nebo logovací framework. |

---

## Tipy a úskalí

* **Tip:** Pokud distribuujete font, který není nainstalován na cílovém počítači, přidejte jej do složky, kterou předáte `SetFontsFolder`. Tím zajistíte deterministické vykreslení.
* **Dávejte pozor na licencování:** Některé fonty vyžadují komerční licence pro vkládání. Vždy si před zabalením ověřte EULA fontu.
* **Poznámka o výkonu:** Načítání velkých knihoven fontů může zpomalit parsování dokumentu. Udržujte složku úspornou – zahrňte jen fonty, které skutečně potřebujete.
* **Okrajový případ:** Když dokument odkazuje na font podle jeho *PostScript názvu* místo názvu rodiny, Aspose.Words jej stále rozpozná, pokud je soubor fontu přítomen ve vyhledávací cestě.

---

## Závěr

Nyní máte kompletní, produkčně připravený vzor pro použití **vlastního nastavení fontů** v C#. Konfigurací `LoadOptions`, registrací callbacku pro varování a volitelným nasměrováním na soukromou složku s fonty můžete **nastavit font settings**, **načíst Word dokument** spolehlivě.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}