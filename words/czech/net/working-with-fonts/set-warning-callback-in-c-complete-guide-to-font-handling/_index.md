---
category: general
date: 2026-02-10
description: Nastavte callback pro varování, aby sledoval změny písma při konfiguraci
  výchozího písma a nastavení výchozího importovaného písma v Aspose.Words. Seznamte
  se s kompletním řešením krok za krokem.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: cs
og_description: Nastavte callback pro varování, aby sledoval změny písma při konfiguraci
  výchozího písma a nastavení výchozího importovaného písma. Postupujte podle úplného
  tutoriálu pro Aspose.Words.
og_title: Nastavení varovného zpětného volání v C# – Kompletní průvodce
tags:
- Aspose.Words
- C#
- Document Import
title: Nastavte výstražný callback v C# – Kompletní průvodce správou fontů
url: /cs/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení varovného zpětného volání v C# – Kompletní průvodce manipulací s fonty

Už jste někdy potřebovali **set warning callback** při načítání dokumentu Word a přemýšleli, jak zároveň *configure default font*? Nejste v tom sami. V mnoha reálných projektech—jako jsou automatizované generátory reportů nebo pipeline pro konverzi dokumentů—chybějící fonty mohou tiše narušit rozvržení a jediný způsob, jak tyto problémy zachytit, je **monitor font changes** pomocí varovného zpětného volání.

V tomto tutoriálu projdeme praktickým příkladem, který vám ukáže, jak **set warning callback**, **configure default font** a dokonce **set default import font** pomocí Aspose.Words pro .NET. Na konci budete mít připravený úryvek k okamžitému spuštění, pochopíte, proč je každá část důležitá, a budete vědět, jak ji přizpůsobit pro okrajové případy, jako jsou vlastní složky s fonty nebo tiché substituce.

---

## Požadavky

- .NET 6.0 nebo novější (kód funguje také na .NET Framework 4.6+)  
- Aspose.Words pro .NET NuGet balíček (`Install-Package Aspose.Words`)  
- Složka, která obsahuje záložní font, který chcete použít (např. `fonts/Arial.ttf`)  
- Základní znalost C# konzolových aplikací  

Další knihovny nejsou vyžadovány.

---

## Krok 1: Vytvořte LoadOptions a **configure default font**

Prvním krokem, když chcete řídit manipulaci s fonty, je vytvořit instanci `LoadOptions`. Tento objekt říká Aspose.Words, jak má při importu zacházet s chybějícími fonty.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Proč je to důležité:**  
Pokud zdrojový dokument odkazuje na font, který není na serveru nainstalován, Aspose.Words se podívá do vámi zadané složky. To je jádro **set default import font**—explicitně říkáte knihovně, kde má najít náhradu, ještě před tím, než jsou vyvolána jakákoliv varování.

---

## Krok 2: **Set warning callback** pro **monitor font changes**

Aspose.Words vydává `WarningInfoCollection` vždy, když musí nahradit font, a také v dalších situacích. Připojením obslužné rutiny můžete zaznamenávat nebo reagovat na každou substituci.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Proč je to důležité:**  
Pouhé **configure default font** není dostatečné, pokud potřebujete auditovat, které fonty byly skutečně vyměněny. Zpětné volání vám poskytuje log v reálném čase, splňuje požadavek **monitor font changes** a pomáhá zachytit neočekávané náhrady již v rané fázi CI pipeline.

---

## Krok 3: Načtěte dokument s připravenými možnostmi

Jakmile jsou možnosti načítání plně připraveny, můžete bezpečně načíst libovolný soubor `.docx`. Zpětné volání se spustí automaticky, pokud dojde k substituci.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Co uvidíte:**  
Pokud zdroj používá font, který není k dispozici, konzole vytiskne něco jako:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Tento výstup potvrzuje, že jste úspěšně **set warning callback** a že **default import font** byl aplikován.

---

## Krok 4: (Volitelné) Jemně doladit chování substituce fontů

Někdy můžete chtít nahradit *všechny* chybějící fonty jednou rodinou, bez ohledu na původní požadavek. Aspose.Words vám umožňuje nastavit *fallback font* globálně.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Kdy použít:**  
Pokud generujete PDF pro značku, která povoluje jen omezenou sadu fontů, toto zajišťuje konzistenci napříč všemi dokumenty, i když zdroj zkouší použít něco exotického.

---

## Krok 5: Uložte nebo dále zpracujte dokument

Po načtení můžete pokračovat s jakýmkoli potřebným zpracováním—úpravou, konverzí do PDF, extrakcí textu atd. Zde je rychlý příklad uložení dokumentu jako PDF při zachování nahrazených fontů.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Výsledné PDF zobrazí fallback font všude, kde došlo k substituci, což vám poskytne vizuální potvrzení, že **set warning callback** fungovalo podle očekávání.

---

## Časté úskalí a tipy pro profesionály

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Callback never fires** | `LoadOptions.WarningCallback` nebyl přiřazen *před* načtením dokumentu. | Vždy připojte zpětné volání **před** voláním `new Document(...)`. |
| **Wrong font folder** | Chybná cesta nebo chybějící oprávnění ke čtení. | Ověřte, že složka existuje a aplikace má přístup `Read`. Používejte absolutní cesty pro spolehlivost. |
| **Multiple substitutions, noisy output** | Velké dokumenty s mnoha chybějícími fonty. | Filtrujte varování podle `WarningType.FontSubstitution` (jak je ukázáno) nebo je zapisujte do souboru logu místo konzole. |
| **Fallback font not applied** | Fallback font není nainstalován na stroji. | Umístěte soubor `.ttf`/`.otf` do složky, kterou jste předali metodě `SetFontsFolder`. Aspose.Words jej načte přímo, není potřeba instalace v OS. |

**Tip pro profesionály:** Když spouštíte toto v CI/CD pipeline, přesměrujte výstup konzole do artefaktu buildu. Tím získáte auditní stopu každé substituce fontu, která se během buildu stala.

---

## Kompletní funkční příklad (připravený ke zkopírování)

Níže je kompletní program, který můžete vložit do nového projektu Console App. Obsahuje všechny kroky, using direktivy a komentáře, které potřebujete.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Očekávaný výstup v konzoli** (předpokládáme, že `Times New Roman` chybí):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Spusťte program, otevřete `output.pdf` a uvidíte, že dokument je vykreslen s fallback fontem tam, kde je to potřeba.

---

## Závěr

Nyní máte solidní, připravený vzor pro produkci, jak **set warning callback** v C#, **configure default font**, **monitor font changes** a **set default import font** při práci s Aspose.Words. Připojením sběratele varování před načtením, nasměrováním `FontSettings` na spolehlivou složku s fonty a volitelným vynucením globálního fallbacku získáte úplnou přehlednost a kontrolu nad substitucí fontů—právě to, co potřebuje jakýkoli robustní pipeline pro zpracování dokumentů.

Jste připraveni na další úroveň? Zkuste kombinovat tento přístup s:

- **Dynamic font loading** z databáze (použijte `FontSettings.SetFontsFolder` za běhu).  
- **Custom warning handlers**, které zapisují do strukturovaného logu (JSON nebo CSV) pro analytiku.  
- **Parallel document processing**, kde každý vlákno získá vlastní `LoadOptions`, aby se předešlo vzájemnému rušení.

Neváhejte experimentovat, přizpůsobit kód své vlastní architektuře a sdílet jakékoli objevy v komentářích. Šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}