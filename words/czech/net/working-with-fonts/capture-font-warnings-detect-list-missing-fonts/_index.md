---
category: general
date: 2025-12-31
description: Zachyťte varování o fontu v Aspose.Words, abyste zjistili chybějící fonty
  a vypsali je ve vaší .NET aplikaci. Naučte se krok za krokem řešení v C#.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: cs
og_description: Zachyťte varování o písmu v Aspose.Words, abyste zjistili chybějící
  písma a vypsali je. Kompletní průvodce C# s kódem a tipy.
og_title: Zachytit varování o písmu – detekovat a vypsat chybějící písma
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Zachytit varování o písmu – Detekovat a vypsat chybějící písma
url: /cs/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zachycení varování o písmu – Detekce a výpis chybějících písem

Už jste někdy potřebovali **zachytit varování o písmu** při načítání Word dokumentu, ale nevedeli ste, jak zobrazit podrobnosti o chybějících písmenech? Nejste v tom sami. V mnoha reálných projektech způsobují chybějící písma vizuální problémy a bez odpovídajících varování se honíte za „fantomovými“ chybami.  

V tomto tutoriálu vám ukážeme, jak **detekovat chybějící písma** a **vypsat chybějící písma** pomocí Aspose.Words pro .NET. Na konci budete mít připravený úryvek C#, který vytiskne každé varování o substituci, takže jej můžete logovat, upozorňovat nebo dokonce automaticky nahrazovat písma.

---

## Proč je zachycení varování o písmu důležité

Když Aspose.Words otevře DOCX, který odkazuje na písmo, jež není nainstalováno na serveru, tiše použije náhradní písmo. Dokument vypadá v pořádku, ale vizuální věrnost je narušena – představte si firemní logo vykreslené nesprávným typem písma.  

Zachycení těchto varování vám umožní:

* **Udržet konzistenci značky** – přesně víte, která písma chybí.
* **Automatizovat nápravu** – programově nahradit chybějící písma.
* **Auditovat shodu** – generovat zprávy pro právní nebo designové revize.

Stručně řečeno, **zachycení varování o písmu** je první obrannou linií proti tichému nahrazování písem.

---

## Nastavení LoadOptions pro detekci chybějících písem

Klíčem k zobrazení varování je vlastnost `LoadOptions.FontSubstitutionWarning`. Ve výchozím nastavení je nastavena na `None`, což znamená, že Aspose.Words zprávy pohlcuje. Přepnutím na `All` řeknete knihovně, aby zaznamenala každou událost substituce.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Tip:** Pokud již máte vlastní složku s písmy, přiřaďte ji pomocí `FontSettings.SetFontsFolder("path")` před načtením dokumentu. Tím můžete **detekovat chybějící písma**, která nejsou v systémovém adresáři.

---

## Načtení dokumentu a výpis chybějících písem

Jakmile jsou `LoadOptions` připravené, dalším krokem je načíst Word soubor. Konstruktor přijímá objekt s možnostmi a jakákoli substituce bude zaznamenána v `WarningInfoCollection` dokumentu.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Pokud soubor odkazuje na písma, která nejsou k dispozici, každé chybějící písmo vytvoří položku `WarningInfo`. **Výpis chybějících písem** získáte iterací přes tuto kolekci.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Typický výstup vypadá takto:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Každý řádek vám přesně řekne, které písmo chybělo, čímž splňuje požadavek **výpisu chybějících písem**.

---

## Čtení a interpretace WarningInfoCollection

`WarningInfoCollection` může obsahovat různé typy varování (např. `DocumentStructure`, `ImageLoading`). Pro zaměření se výhradně na problémy s písmy filtrujte podle `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Proč filtrovat? Protože velký dokument může také generovat varování o poškozených obrázcích nebo nepodporovaných funkcích. Zúžením kolekce odstraníte šum a udržíte výstup **zachycení varování o písmu** přehledný.

---

## Kompletní funkční příklad – Zachycení varování o písmu v praxi

Níže je kompletní, samostatný program, který můžete vložit do libovolného .NET konzolového projektu. Ukazuje každý krok od konfigurace `LoadOptions` po vytištění přehledného seznamu chybějících písem.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Očekávaný výstup v konzoli**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Pokud dokument neobsahuje žádná chybějící písma, uvidíte:

```
All referenced fonts are available – no warnings captured.
```

---

## Časté okrajové případy a jak je řešit

| Situace | Proč k tomu dochází | Doporučené řešení |
|-----------|----------------|-----------------|
| **Dokument používá vložené OpenType písmo** | Aspose.Words dokáže číst vložená písma, ale pouze pokud soubor není poškozen. | Ověřte DOCX ve Wordu; případně písmo znovu vložte. |
| **Velké množství varování** (např. 200+ chybějících písem) | Hromadné importy ze starých systémů často odkazují na širokou paletu písem. | Zpracovávejte varování dávkově: uložte je do databáze a poté spusťte skript pro instalaci písem. |
| **WarningInfoCollection je prázdná** | Buď má dokument všechna písma, nebo `FontSubstitutionWarning` zůstalo nastaveno na `None`. | Zkontrolujte konfiguraci `LoadOptions` a ujistěte se, že načítáte správnou cestu k souboru. |
| **Vlastní písma umístěná na síťovém disku** | Síťová latence může způsobit časové limity při vyhledávání písem. | Přednačtěte písma do `FontSettings` pomocí `SetFontsFolder` a nastavte `CacheFontData = true`. |

Tyto tipy vám pomohou **detekovat chybějící písma** spolehlivě i v složitých prostředích.

---

## Ilustrace

![capture font warnings example](https://example.com/images/capture-font-warnings.png "capture font warnings example")

*Na snímku je vidět běh konzole, kde jsou nahlášena dvě chybějící písma.*

---

## Další kroky – Za hranice jednoduchého reportování

Nyní, když můžete **zachytit varování o písmu**, zvažte automatizaci nápravy:

1. **Automatická substituce písem** – Nahraďte chybějící písma firemně schváleným náhradním písmem úpravou `FontSettings.SubstitutionSettings`.
2. **Logování do monitorovacího systému** – Přesměrujte varování do Serilog, ELK nebo Azure Application Insights.
3. **Reporty pro uživatele** – Vygenerujte souhrn v HTML nebo PDF, aby designéři mohli zkontrolovat, která písma je třeba nainstalovat.

Všechny tyto rozšíření staví na stejném základu, který jsme probrali: konfigurace `LoadOptions`, načtení dokumentu a čtení `WarningInfoCollection`.

---

## Závěr

Právě jste se naučili, jak **zachytit varování o písmu** v Aspose.Words, **detekovat chybějící písma** a **vypsat chybějící písma** s čistým výstupem vhodným pro konzoli. Přístup je přímočarý, vyžaduje jen několik řádků C# a funguje s libovolnou verzí .NET, která podporuje Aspose.Words 23.x nebo novější.  

Vyzkoušejte to na ukázkovém DOCX, který odkazuje na písmo, jež úmyslně odinstalujete – varování se objeví okamžitě. Pak můžete rozhodnout, zda písmo nainstalujete, nahradíte ho programově, nebo jen zaznamenáte problém pro pozdější revizi.

Šťastné programování a ať se vaše dokumenty vždy vykreslují s těmi správnými písmy!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}