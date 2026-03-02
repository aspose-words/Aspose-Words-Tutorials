---
category: general
date: 2026-03-01
description: Vytvořte FontSettings v C# pro detekci chybějících písem, zachycení zpráv
  o písmu a zpracování chybějících písem pomocí Aspose.Words. Průvodce krok za krokem
  pro vývojáře.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: cs
og_description: Vytvořte FontSettings v C# pro detekci chybějících fontů, zachycení
  zpráv o fontech a zpracování chybějících fontů pomocí Aspose.Words. Kompletní tutoriál
  s kódem.
og_title: Vytvořte FontSettings v C# – Detekujte chybějící písma a zachyťte zprávy
  o písmu
tags:
- Aspose.Words
- C#
- Font Management
title: Vytvořte FontSettings v C# – Detekujte chybějící písma a zachyťte zprávy o
  písmu
url: /cs/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření FontSettings v C# – Detekce chybějících fontů a zachycení zpráv o fontech

Už jste někdy potřebovali **create FontSettings** v .NET projektu, ale nebyli jste si jisti, jak odhalit fonty, které nejsou nainstalovány na cílovém počítači? Nejste v tom sami. V mnoha reálných aplikacích – například automatizovaných generátorech reportů nebo konvertorech dokumentů – chybějící fonty mohou tiše narušit rozvržení a neuvědomíte si to, dokud PDF nevypadá podivně.  

Co kdybyste mohli **detect missing fonts**, **capture font messages** a **handle missing fonts** ještě předtím, než zničí váš výstup? Dobrou zprávou je, že Aspose.Words to dělá hračkou. V tomto tutoriálu projdeme celý proces, od nastavení objektu `FontSettings` až po připojení callbacku pro varování, který vám řekne přesně, které glyfy byly nahrazeny.

> **TL;DR:** Na konci budete mít připravenou C# konzolovou aplikaci, která zaznamená každou substituci fontu, a umožní vám rozhodnout, zda vložit náhradní font nebo upozornit uživatele.

---

## Požadavky

- .NET 6 SDK (nebo jakákoli recentní verze .NET)  
- Visual Studio 2022 nebo VS Code s rozšířeními C#  
- Licence Aspose.Words pro .NET (pro tuto ukázku funguje i bezplatná zkušební verze)  
- Ukázkový DOCX, který odkazuje na font, který nemáte nainstalovaný (např. *Comic Sans MS* na Linuxu)  

Kromě `Aspose.Words` nejsou vyžadovány žádné speciální NuGet balíčky.

## Krok 1 – Instalace Aspose.Words a nastavení projektu

Nejprve vytvořte nový konzolový projekt a přidejte knihovnu Aspose.Words.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Tip:** Pokud již máte řešení, stačí přidat balíček přes UI NuGet Package Manager – usnadní to sledování verzí.

## Krok 2 – Vytvoření FontSettings (Zde se objeví primární klíčové slovo)

Krok **create FontSettings** je základem každého workflow souvisejícího s fonty. `FontSettings` říká Aspose.Words, kde hledat fonty, zda použít systémové složky a jak postupovat, když něco chybí.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Proč je to důležité? Bez správně nakonfigurovaného `FontSettings` engine tiše nahrazuje chybějící glyfy výchozím systémovým fontem a vy nikdy neobdržíte varování.

## Krok 3 – Propojení LoadOptions s FontSettings

`LoadOptions` vám umožňuje předat `FontSettings` do načítače dokumentu. Toto je most, který umožňuje engine **detect missing fonts** během fáze konstrukce `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Nyní pokaždé, když načtete DOCX s `loadOptions`, Aspose.Words použije `FontSettings`, které jsme nastavili dříve.

## Krok 4 – Připojení callbacku pro varování k **Capture Font Messages**

Aspose.Words vydává varování pro různé podmínky – substituce fontu je jednou z běžných. Poskytnutím implementace `IWarningCallback` můžete **capture font messages** v reálném čase.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Třída pro zpracování varování

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Pole `info.Description` obsahuje lidsky čitelnou zprávu, například *„Font 'Comic Sans MS' nebyl nalezen. Nahrazen fontem 'Arial'.“* To je přesně ten typ výstupu, který potřebujete k **handle missing fonts** elegantně.

## Krok 5 – Načtení dokumentu a nechte callback vykonat svou práci

Po propojení všeho je načtení dokumentu jednoduché. Pokud zdrojový soubor odkazuje na font, který v systému chybí, náš handler varování se spustí.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Když spustíte program, uvidíte výstup v konzoli podobný:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Tento výstup je část **capture font messages** našeho workflow. Můžete rozšířit handler tak, aby zapisoval do souboru, posílal telemetrii nebo dokonce přerušil konverzi, pokud chybí kritické fonty.

## Krok 6 – Kompletní funkční příklad (Vše dohromady)

Níže je kompletní program připravený ke zkopírování. Vložte jej do `Program.cs`, upravte cesty k souborům a spusťte `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Očekávaný výstup

Spuštění programu na stroji, který nemá *Comic Sans MS*, vytiskne něco jako:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Také získáte `Result.pdf`, který používá nahrazené fonty, což zajišťuje, že konverze nikdy nezhavaruje.

## Často kladené otázky a okrajové případy

| Question | Answer |
|----------|--------|
| **Co když chci, aby konverze selhala místo substituce?** | V `FontSubstitutionWarningHandler` vyhoďte výjimku, když `info.Description` obsahuje název kritického fontu. |
| **Mohu automaticky vložit náhradní font?** | Ano. Po detekci chybějícího fontu můžete načíst náhradní `FontInfo` ze známé cesty a přidat jej do `fontSettings` pomocí `fontSettings.SetFontsFolder`. |
| **Funguje to na Linuxu/macOS?** | Rozhodně. `FontSettings` funguje napříč platformami; ujistěte se jen, že složka s náhradními fonty obsahuje příslušné soubory `.ttf` nebo `.otf`. |
| **Je callback pro varování thread‑safe?** | Callback běží ve stejném vlákně, které načítá dokument, takže pro zápis do konzole nepotřebujete další synchronizaci. V multithreadových scénářích chraňte sdílené zdroje. |
| **Jak mohu varování logovat do souboru?** | Nahraďte `Console.WriteLine` za `File.AppendAllText("font_warnings.log", ...)` nebo použijte libovolný logging framework (Serilog, NLog). |

## Pro tipy pro produkčně připravené zpracování fontů

1. **Cache Font Lookups** – Opětovné použití stejné instance `FontSettings` napříč více načteními dokumentů zabraňuje opakovanému skenování souborového systému.  
2. **Whitelist Critical Fonts** – Pokud vaše značka vyžaduje konkrétní font, ověřte jeho přítomnost včas a při jeho chybě ukončete s jasnou chybovou zprávou.  
3. **Use `SetFontFolder` Recursively** – Nastavení `recursive: true` zajistí skenování podadresářů, což je užitečné, když distribuujete celou kolekci fontů.  
4. **Combine with `FontSubstitutionSettings`** – Můžete jemně doladit pravidla substituce (např. upřednostnit fonty se stejným názvem rodiny).  

## Závěr

Právě jsme **created FontSettings**, nakonfigurovali `LoadOptions` k **detect missing fonts**, připojili callback, který **captures font messages**, a ukázali, jak **handle missing fonts** čistým, produkčně připraveným způsobem. Celý tok se vejde do několika desítek řádků C#, přičemž vám poskytuje úplný přehled o fontovém prostředí libovolného DOCX, který zpracováváte.

Další kroky, které můžete prozkoumat:

- **Embedding fallback fonts** přímo do výstupního PDF (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programmatically substituting fonts** na základě firemních pravidel značky.  
- **Integrating with a CI pipeline** pro automatické označování dokumentů, které používají neautorizované fonty.

Vyzkoušejte to, upravte handler varování podle svých potřeb a nechte své dokumentové pipeline běžet s jistotou – žádné další záhadné problémy s rozvržením způsobené neviditelnými výměnami fontů.

Šťastné programování! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}