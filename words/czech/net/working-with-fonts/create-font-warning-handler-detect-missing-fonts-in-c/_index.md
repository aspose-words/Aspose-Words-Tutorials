---
category: general
date: 2026-02-12
description: Vytvořte obslužnou rutinu varování o písmu pro detekci chybějících fontů
  a sledování chybějících fontů v Aspose.Words. Naučte se efektivně zaznamenávat varování.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: cs
og_description: Vytvořte handler varování písma v C#, který detekuje chybějící písma,
  a naučte se, jak zaznamenávat varování, když Aspose.Words nahrazuje písma.
og_title: Vytvořit obslužný program varování o písmu – Detekovat chybějící písma
tags:
- Aspose.Words
- C#
- Document Processing
title: Vytvořit obslužný program varování o písmu – Detekovat chybějící písma v C#
url: /cs/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obslužného programu varování o písmu – Detekce chybějících písem v C#

Už jste někdy potřebovali **vytvořit obslužný program varování o písmu**, protože Word dokument tiše nahradil písmo, které jste nečekali? Nejste v tom sami. Když Aspose.Words načte DOCX, který odkazuje na písmo, jež na serveru chybí, tiše přejde na výchozí písmo – vaše rozložení tak zůstane mírně poškozené.  

V tomto tutoriálu vám ukážeme, jak **detekovat chybějící písma**, **sledovat chybějící písma** a **jak zaznamenávat varování**, abyste tyto náhrady odhalili dříve, než vám způsobí problémy. Na konci budete mít znovupoužitelný obslužný program varování, který vypíše každou událost náhrady písma do konzole (nebo do libovolného loggeru, který preferujete). Žádná hádanka, jen jasný, akční kód.

## Požadavky

- .NET 6.0 nebo novější (API je stejné pro .NET Framework 4.6+)
- Aspose.Words pro .NET nainstalovaný (`dotnet add package Aspose.Words`)
- Word soubor, který odkazuje na písmo, jež není nainstalováno na vašem počítači (např. `MissingFont.docx`)

Pokud už máte vše připravené, skvěle – přeskočíme na další krok.

## Krok 1: Nastavení LoadOptions s callbackem pro varování  

První věc, kterou uděláte, když chcete **vytvořit obslužný program varování o písmu**, je říct Aspose.Words, aby spustil callback, kdykoli narazí na problém. `LoadOptions` je kontejner pro tuto konfiguraci.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Proč je to důležité:**  
`LoadOptions` je jediným místem, kde můžete zapojit `IWarningCallback`. Bez něj Aspose.Words zaznamená varování interně, ale vy je nikdy neuvidíte. Přiřazením `FontWarningHandler` získáte plnou kontrolu nad tím, co se stane, když je chybějící písmo nahrazeno.

## Krok 2: Implementace třídy FontWarningHandler  

Nyní skutečně **vytvoříme kód obslužného programu varování o písmu**. Třída implementuje `IWarningCallback` a přijímá objekt `WarningInfo` pro každé varování, které Aspose.Words vygeneruje.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Vysvětlení:**  
- `info.Type` udává kategorii varování. Zajímá nás `WarningType.FontSubstitution`, protože právě to signalizuje chybějící písmo.  
- `info.Description` obsahuje lidsky čitelnou zprávu, např. *„Font 'Comic Sans MS' was not found. Substituted with 'Arial'.“*  
- Zapsáním do `Console.WriteLine` **okamžitě zaznamenáváme varování**. Ve skutečné aplikaci můžete místo toho použít `ILogger`, zapisovat do souboru nebo posílat data do telemetrické služby.

> **Tip:** Pokud potřebujete shromáždit všechna chybějící písma pro pozdější report, uložte `info.Description` do `List<string>` místo okamžitého výpisu.

## Krok 3: Načtení dokumentu s nakonfigurovanými LoadOptions  

S nastaveným callbackem se načtení dokumentu automaticky spustí náš obslužný program pokaždé, když chybí písmo.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Co uvidíte:**  
Spuštěním programu se vypíše něco podobného:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Tento řádek potvrzuje, že jste úspěšně **detekovali chybějící písma** a nyní **sledujete chybějící písma** v reálném čase.

## Krok 4: Ověření, že obslužný program funguje v různých scénářích  

Je snadné předpokládat, že obslužný program funguje jen pro soubory DOCX, ale Aspose.Words podporuje mnoho formátů. Zkuste načíst PDF, který odkazuje na vložené písmo, nebo starší soubor `.doc`. Stejný callback se spustí pro jakýkoli formát, který prochází pipeline pro řešení písem.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Pokud PDF odkazuje na písmo, které není nainstalováno, získáte stejný výstup do konzole. To dokazuje, že vaše řešení **vytvořit obslužný program varování o písmu** je nezávislé na formátu.

## Krok 5: Rozšíření obslužného programu – Zapisování do souboru  

Výstup do konzole je vhodný pro ukázky, ale v produkci se obvykle zapisuje do log souboru. Zde je rychlá úprava.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Nyní se při každé náhradě písma zpráva připojí do `font-warnings.log`. Tím splňujete část **jak zaznamenávat varování** a získáte trvalý auditní záznam.

## Krok 6: Kompletní ukázka – Plně spustitelný příklad  

Níže je kompletní program, který můžete zkopírovat do konzolové aplikace. Nechybí žádné části; jen nahraďte cestu k souboru vlastní cestou k dokumentu.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Očekávaný výsledek:**  

- Konzole vypíše každý řádek náhrady.  
- `font-warnings.log` nyní obsahuje časově označený záznam o každé události chybějícího písma.  
- Soubor `output.pdf` je vytvořen s náhradními písmy, což zajišťuje úspěšnou konverzi i když původní písma nejsou k dispozici.

## Často kladené otázky a okrajové případy  

| Otázka | Odpověď |
|----------|--------|
| *Co když chci ignorovat určitá písma?* | V metodě `Warning` zkontrolujte `info.Description` pro název písma a `return;` dříve, pokud je písmo pro vás přijatelné. |
| *Bude obslužný program fungovat pro vložená písma?* | Ne – vložená písma jsou vždy dostupná dokumentu, takže varování o náhradě se neobjeví. |
| *Mohu zachytit i jiné typy varování (např. problémy s rozlišením obrázků)?* | Rozhodně. Odstraňte podmínku `if (info.Type == WarningType.FontSubstitution)` nebo přidejte další `if` bloky pro `WarningType.ImageResolution`. |
| *Je obslužný program thread‑safe?* | Výchozí implementace zapisuje do souboru bez synchronizace. Pro vícevláknové scénáře obalte zápisy do souboru zamčením (`lock`) nebo použijte konkurenční logger. |

## Další kroky  

Nyní, když víte **jak zaznamenávat varování** pro chybějící písma, můžete:

- **Detekovat chybějící písma** během hromadného importu a generovat souhrnnou zprávu.  
- **Sledovat chybějící písma** napříč více dokumenty a posílat e‑mailové upozornění, když se konkrétní písmo objevuje často.  
- **Integrovat s monitorovacím systémem** (např. Azure Application Insights) a zobrazovat trendy náhrad písem v čase.  

Všechny tyto rozšíření staví na stejném základu `IWarningCallback`, který jsme vytvořili.

---

*Šťastné programování! Pokud narazíte na kuriozity – například vlastní složku s fonty nebo síťové úložiště – zanechte komentář níže. Komunita (a já) vám rádi pomohou doladit vaši strategii varování o písmu.* 

![vytvoření obslužného programu varování o písmu příklad](image-placeholder.png "vytvoření obslužného programu varování o písmu příklad")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}