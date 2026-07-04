---
category: general
date: 2026-06-20
description: Povolte upozornění na nahrazování písem v C# pomocí Aspose.Words. Naučte
  se, jak nastavit LoadOptions, zachytit upozornění a efektivně řešit chybějící písma.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: cs
og_description: Povolte varování o nahrazení písma v C# pomocí Aspose.Words. Tento
  průvodce vám ukáže, jak nastavit LoadOptions, přečíst WarningInfo a zobrazit zprávy
  o chybějících písmech.
og_title: Povolit varování o nahrazování fontů v C# – Kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Povolit upozornění na náhradu písma v C# s Aspose.Words
url: /cs/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Povolení upozornění na nahrazení fontů v C# s Aspose.Words

Už jste se někdy zamýšleli, jak **povolit upozornění na nahrazení fontů**, když Word dokument odkazuje na font, který není nainstalován na serveru? Nejste v tom jediní. Chybějící fonty mohou tiše narušit rozvržení generovaných PDF nebo obrázků a jediný způsob, jak to včas zachytit, je poslouchat upozornění, která Aspose.Words vydává.

V tomto tutoriálu vás provedeme praktickým příkladem, který vám přesně ukáže, jak zapnout tato upozornění, vyjmout je ze sbírky `WarningInfo` a vytisknout smysluplné zprávy do konzole. Na konci budete vědět, jak nakonfigurovat **Aspose.Words LoadOptions**, zpracovávat **C# upozornění na nahrazení fontů** a udržet vaši pipeline pro zpracování dokumentů neporušenou.

Dotkneme se také několika okrajových případů – co se stane, když potlačíte upozornění, nebo pokud je potřebujete zaznamenat místo jejich výpisu – a poskytneme vám kompletní, připravený k zkopírování kód, který funguje s nejnovější verzí Aspose.Words pro .NET (od verze 24.10).

## Co budete potřebovat

- .NET 6.0 nebo novější (kód také funguje na .NET Framework 4.7+)
- Odkaz na NuGet balíček `Aspose.Words` (nainstalujte pomocí `dotnet add package Aspose.Words`)
- Word soubor, který odkazuje na font, který **nemáte** nainstalovaný (např. `DocumentWithMissingFont.docx`)
- Slušné IDE (Visual Studio, Rider nebo VS Code)

To je vše – žádné extra služby, žádné proprietární nástroje. Připravení? Ponořme se.

## Krok 1: Povolení upozornění na nahrazení fontů

První věc, kterou musíte udělat, je říct Aspose.Words, že chcete být upozorněni, když nahradí chybějící font. To se provádí pomocí vlastnosti `FontSettings` objektu `LoadOptions`. Ve výchozím nastavení jsou upozornění **zakázána**, aby API bylo tiché, takže musíme přepínač přepnout sami.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Why this works:** Když `FontSettings` není `null`, knihovna automaticky naplní `Document.WarningInfo` všemi položkami `WarningType.FontSubstitution`, na které narazí při načítání dokumentu. Považujte to za zapnutí „debug‑mode“ pro fonty.

## Krok 2: Načtení dokumentu s nakonfigurovanými možnostmi

Nyní, když je sbírka upozornění aktivní, načtěte svůj dokument pomocí `LoadOptions`, které jsme právě připravili. Pokud dokument obsahuje chybějící font, Aspose.Words nahradí náhradním a vloží upozornění do seznamu `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Pro tip:** Pokud zpracováváte mnoho souborů ve smyčce, znovu použijte stejnou instanci `LoadOptions` – vytvoření jednou ušetří několik milisekund na iteraci.

## Krok 3: Procházení WarningInfo a zobrazení zpráv o nahrazení fontů

Jakmile je dokument načten, sbírka `WarningInfo` obsahuje každé upozornění, ke kterému během načítání došlo. Zajímá nás jen `WarningType.FontSubstitution`, takže filtrujeme podle toho.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Spuštění výše uvedeného úryvku proti dokumentu, který odkazuje na chybějící font „Papyrus“, může vyprodukovat výstup jako:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

To jsou **zprávy o nahrazení fontů**, které jste hledali – jasné, akční a připravené k zaznamenání nebo odeslání do varovného systému.

## Kompletní funkční příklad

Níže je samostatný konzolový program, který spojuje vše dohromady. Zkopírujte jej do nového `.csproj` a spusťte **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Očekávaný výstup

Pokud dokument odkazuje na fonty, které nejsou nainstalovány, uvidíte něco podobného:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Pokud jsou všechny fonty na stroji přítomny, program jednoduše vytiskne:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Časté úskalí a tipy

| Problém | Proč k tomu dochází | Jak opravit / vyhnout se |
|-------|----------------|--------------------|
| **Upozornění zmizí** | Vymazali jste `FontSettings` nebo použili `LoadOptions` bez něj. | Vždy vytvořte instanci `FontSettings`, i když neměníte žádné vlastnosti. |
| **Příliš mnoho upozornění** | Dokument používá mnoho exotických fontů. | Zvažte přidání vlastní složky s fonty do `FontSettings` pomocí `SetFontsFolder`, abyste snížili náhrady. |
| **Výkonový dopad ve smyčce** | Znovu‑vytváření `LoadOptions` v každé iteraci přidává režii. | Znovu použijte jednu instanci `LoadOptions` pro všechny dokumenty. |
| **Chybějící výstup do konzole** | Spouštění uvnitř GUI aplikace, kde je `Console.WriteLine` ignorováno. | Přesměrujte upozornění do loggeru (`ILogger`) nebo je zapište do souboru. |

### Zpracování upozornění ve skutečné službě

Ve webovém API pravděpodobně nechcete zapisovat do konzole. Místo toho přesměrujte upozornění do strukturovaného logu:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Tím si zachováte **zpracování upozornění dokumentu**, zatímco vaše služba zůstane čistá.

## Rozšíření příkladu

- **Zachycení dalších typů upozornění** (např. `WarningType.UnknownFileFormat`) odstraněním `if` filtru.
- **Uložení zprávy** o všech upozorněních do JSON pro následnou analytiku.
- **Vynucení konkrétního náhradního fontu** nastavením `FontSettings.SubstitutionSettings.DefaultFontName`.

Všechny tyto jsou přirozenými rozšířeními, jakmile zvládnete **povolení upozornění na nahrazení fontů**.

## Závěr

Ukázali jsme vám, jak **povolit upozornění na nahrazení fontů** v C# pomocí Aspose.Words, od konfigurace `LoadOptions` po iteraci přes `WarningInfo` a výpis přátelských zpráv. Dodržením výše uvedených kroků můžete ochránit své pipeline pro zpracování dokumentů před tichými změnami rozvržení způsobenými chybějícími fonty.

Dále zkuste přidat vlastní složku s fonty, zaznamenávat upozornění do souboru nebo je dokonce odesílat na monitorovací dashboard. Stejný vzor funguje pro jakýkoli scénář **zpracování upozornění dokumentu**, ať už převádíte do PDF, renderujete obrázky nebo provádíte hromadnou korespondenci.

Máte otázky ohledně **C# upozornění na nahrazení fontů** nebo chcete sdílet chytrý workaround? Zanechte komentář níže – šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Povolení upozornění na nahrazení fontů v Aspose.Words – Kompletní průvodce](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Jak detekovat fonty v Aspose.Words – Zpracování upozornění a nastavení](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Zachycení upozornění na nahrazení fontů v Javě s Aspose.Words – Kompletní průvodce](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}