---
category: general
date: 2026-06-24
description: Jak použít IWarningCallback k detekci chybějících fontů v dokumentech
  Aspose.Words. Naučte se kompletní spustitelný příklad a osvědčené postupy.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: cs
og_description: Jak použít IWarningCallback k detekci chybějících fontů v Aspose.Words.
  Postupujte podle podrobného návodu krok za krokem pro kompletní, produkčně připravené
  řešení.
og_title: Jak používat IWarningCallback – Detekce chybějících fontů
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak používat IWarningCallback – Detekce chybějících fontů v Aspose.Words
url: /cs/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak používat IWarningCallback – Detekce chybějících fontů v Aspose.Words

Použití **IWarningCallback** je nezbytné, když pracujete s Aspose.Words a potřebujete **detekovat chybějící fonty** v souboru DOCX. V tomto průvodci vás provedeme kompletním příkladem, který můžete zkopírovat a vložit, a ukážeme vám přesně, jak použít IWarningCallback k zachycení varování o substituci fontů, proč je to důležité a co s nimi udělat, až je získáte.

Pokud jste někdy otevřeli dokument a viděli nesmyslný text, protože nebyl nainstalován vlastní font, znáte tu frustraci. Na konci tohoto tutoriálu budete mít spolehlivý způsob, jak tyto problémy programově odhalit, zaznamenat je nebo dokonce automaticky použít náhradní font.

## Co se naučíte

- Účel **IWarningCallback** a kdy jej použít.  
- Jak implementovat vlastní sběrač varování, který izoluje události **detect missing fonts**.  
- Připojení sběrače k **LoadOptions**, aby byl každý načtený dokument monitorován.  
- Ověření výstupu a zpracování okrajových případů (více chybějících fontů, tichá varování atd.).  

### Požadavky

- .NET 6.0 nebo novější (kód funguje také na .NET Framework 4.6+).  
- Aspose.Words pro .NET nainstalovaný přes NuGet (`Install-Package Aspose.Words`).  
- Soubor DOCX, který odkazuje na font, který není na počítači přítomen (např. `DocumentWithMissingFont.docx`).  

Žádné další knihovny nejsou potřeba – vše je součástí Aspose.Words.

---

## Jak použít IWarningCallback k detekci chybějících fontů v Aspose.Words

Níže je **úplný, spustitelný program**. Zkopírujte jej do nového konzolového projektu, upravte cestu k souboru a spusťte. V konzoli uvidíte výstup pro každé varování o chybějícím fontu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Očekávaný výstup

Pokud `DocumentWithMissingFont.docx` odkazuje na font nazvaný *„MyFancyFont“*, který není nainstalován, uvidíte něco jako:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Každý řádek začínající **[Missing Font]** je generován naší implementací **IWarningCallback**, což dokazuje, že jsme úspěšně **detect missing fonts**.

---

## Krok 1: Implementace rozhraní IWarningCallback

Proč potřebujeme vlastní třídu? Aspose.Words generuje **varování** z různých důvodů – problémy s formátem souboru, zastaralé funkce a, co je pro nás nejdůležitější, substituci fontů. Implementací `IWarningCallback` získáme háček, který přijímá každé varování v okamžiku, kdy nastane. Filtrování na `WarningType.FontSubstitution` izoluje konkrétní scénář, kdy font chybí.

**Tip:** Pokud potřebujete zachytit *všechna* varování pro diagnostiku, jednoduše odstraňte podmínku `if` a logujte každý `info.Type`.

---

## Krok 2: Připojení callbacku k LoadOptions

`LoadOptions` je brána, která říká Aspose.Words, jak má zacházet s načítaným dokumentem. Nastavením `WarningCallback` na instanci našeho sběrače zajistíme, že callback bude aktivní po celou dobu načítání. Stejný objekt `LoadOptions` můžete znovu použít pro více dokumentů, což je užitečné v dávkových zpracovacích pipelinech.

**Často kladená otázka:** *Co když načtu dokument bez specifikace LoadOptions?*  
Odpověď: Aspose.Words i nadále generuje varování interně, ale bez callbacku jsou tiše zahozena a přijdete o možnost **detect missing fonts**.

---

## Krok 3: Načtení dokumentu a zachycení varování o chybějících fontech

Konstruktor `Document`, který přijímá cestu k souboru a `LoadOptions`, provádí těžkou práci. Jakmile je soubor parsován, jakýkoli chybějící font spustí naši metodu `FontWarningCollector.Warning`. Výstup v konzoli dokazuje, že mechanismus funguje.

**Okrajový případ:** Jeden dokument může odkazovat na několik chybějících fontů. Callback se spustí jednou pro každý chybějící font, takže uvidíte více řádků – ideální pro vytvoření komplexní zprávy.

---

## Proč použít IWarningCallback místo manuálního kontrolování fontů?

Můžete ručně procházet vlastnosti `Run.Font` po načtení dokumentu, ale to vyžaduje, aby se dokument načetl úspěšně – což selže, pokud je font zcela nedostupný. Systém varování funguje **před** jakoukoliv substitucí, takže získáte pravdivý obrázek o tom, co chybí.

Navíc callback běží **jako součást načítacího pipeline**, což vám umožní včas přerušit proces, nahradit fonty za běhu nebo zaznamenat podrobné diagnostické informace bez dalších průchodů stromem dokumentu.

---

## Elegantní zpracování více chybějících fontů

Pokud očekáváte mnoho chybějících fontů, zvažte jejich shromažďování do kolekce:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Po načtení můžete iterovat přes `MissingFonts` a například je zapsat do CSV souboru pro designový tým.

---

## Bonus: Logování varování do souboru

Výstup do konzole stačí pro ukázky, ale produkční kód obvykle loguje do perzistentního úložiště. Nahraďte volání `Console.WriteLine` například tímto:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Nyní máte auditní stopu, kterou lze později přezkoumat, což splňuje požadavky na shodu.

---

## Závěr

Probrali jsme **jak používat IWarningCallback** k **detect missing fonts** v Aspose.Words, od implementace callbacku přes jeho připojení k `LoadOptions` až po zpracování vzniklých varování. Tento přístup vám poskytuje okamžitý přehled o problémech s fonty, umožňuje logovat, nahrazovat nebo upozorňovat uživatele ještě před vykreslením dokumentu.

Další kroky, které můžete prozkoumat:

- **Náhradní fonty:** programově přiřadit výchozí font, když dojde k substituci.  
- **Dávkové zpracování:** projít složku dokumentů a znovu použít stejný `AggregatingFontCollector`.  
- **Uživatelská zpětná vazba:** zobrazit varování o chybějících fontech v UI místo v konzoli.

Vyzkoušejte to ve svém projektu – už žádný tajemný rozmazaný text, jen jasná a akční diagnostika. Šťastné kódování!

## Co se naučíte dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}