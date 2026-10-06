---
category: general
date: 2026-03-13
description: Jak zachytit varování při načítání dokumentů pomocí Aspose.Words, plus
  tipy, jak řešit chybějící písma a nastavit vlastní nastavení písma. Naučte se kompletní
  řešení v C#.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: cs
og_description: Jak zachytit varování při načítání souborů Word pomocí Aspose.Words,
  a praktické způsoby, jak řešit chybějící písma a nastavit vlastní nastavení fontů.
og_title: Jak zachytit varování v Aspose.Words – kompletní průvodce
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak zachytit varování v Aspose.Words – kompletní průvodce
url: /cs/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak zachytit varování v Aspose.Words – Kompletní průvodce

Už jste se někdy zamýšleli **jak zachytit varování**, která se objeví při načítání dokumentu v Aspose.Words? V mnoha reálných projektech uvidíte upozornění na nahrazení fontu, poznámky o zastaralých funkcích nebo dokonce zprávy související se zabezpečením. Ignorovat je jako jezdit s rozbitým čelním sklem – možná dorazíte do cíle, ale nikdy nebudete vědět, kdy se něco rozbije.

Dobrou zprávou je, že Aspose.Words vám poskytuje čistý, založený na zpětných voláních způsob, jak tato zpráva zachytit. V tomto tutoriálu projdeme **kompletní příklad v C#**, který nejen zachytí varování, ale také vám ukáže, jak **zpracovat chybějící fonty** a **nastavit vlastní nastavení fontů**, aby se vaše dokumenty vykreslovaly přesně tak, jak očekáváte.

---

## Co se naučíte

- Nastavit `LoadOptions` tak, aby použily vlastní objekt `FontSettings`.  
- Zaregistrovat zpětné volání varování, které filtruje události `FontSubstitution`.  
- Vypisovat podrobnosti varování do konzole (nebo do libovolného loggeru, který preferujete).  
- Rozšířit řešení tak, aby elegantně zvládalo chybějící fonty na různých platformách.  

Na konci tohoto průvodce budete mít připravený úryvek kódu, který můžete vložit do libovolného .NET projektu, a také několik praktických tipů, jak se vyhnout běžným úskalím.

---

## Požadavky

| Requirement | Why It Matters |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 nebo novější) | API, které používáme (`LoadOptions`, `IWarningCallback`), se nachází zde. |
| **.NET 6+** (or .NET Framework 4.7.2+) | Moderní jazykové funkce činí kód přehlednějším. |
| **A sample DOCX** (named `input.docx`) placed in a known folder | Potřebujeme něco, co načíst a vyvolat varování. |
| **A console or logging framework** (optional) | Pro zobrazení zachycených varování v praxi. |

Kromě samotného Aspose.Words nejsou vyžadovány žádné další balíčky NuGet.

---

## Krok 1: Nastavení vlastních fontů  

Před načtením dokumentu můžete Aspose.Words říci, kde má hledat fonty. Toto je část hádanky **nastavit vlastní nastavení fontů**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Proč je to důležité:**  
Pokud DOCX odkazuje na font, který není nainstalován v systému, Aspose.Words tiše nahradí náhradním fontem *pokud* jste nenastavili složku s požadovanými fonty. Nastavením vlastní složky snížíte pravděpodobnost varování o „nahrazení fontu“ již na začátku.

> **Tip:** Na Linuxu možná budete muset přidat balíček `fonts-dejavu-core` nebo jakoukoli kolekci TrueType, na které vaše dokumenty spoléhají.

---

## Krok 2: Zaregistrovat zpětné volání varování  

Aspose.Words implementuje `IWarningCallback`. Vytvoříme malý handler, který vypisuje jen varování, na která nám záleží: chybějící nebo nahrazené fonty.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Proč je to důležité:**  
Scénář **zpracování chybějících fontů** je nyní viditelný. Místo hádání, který font byl vyměněn, získáte jasný popis jako „Font 'Calibri' byl nahrazen fontem 'Arial'“. To je neocenitelné při ladění problémů s rozvržením v generovaných PDF nebo tištěných zprávách.

---

## Krok 3: Načtení dokumentu s nakonfigurovanými možnostmi  

Nyní konečně načteme dokument do paměti pomocí `LoadOptions`, které jsme právě připravili.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Pokud zdrojový soubor používá font, který není přítomen v `C:\MyFonts`, uvidíte výstup podobný:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Tento řádek je výsledek **zachycení varování**, který jste hledali.

---

## Krok 4: Kompletní funkční příklad (připravený ke kopírování)

Níže je celý program, připravený ke kompilaci. Vložte jej do nového konzolového projektu a spusťte – jen se ujistěte, že cesty ukazují na skutečná umístění ve vašem počítači.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Očekávaný výstup:**  

- Pokud jsou všechny fonty k dispozici:  
  `Document processed. Check console for any warning messages.`  

- Pokud chybí font:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Krok 5: Běžné varianty a okrajové případy  

| Situation | What to Adjust |
|-----------|----------------|
| **Více složek s fonty** | Zavolejte `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` pro každé další umístění. |
| **Potlačit všechna varování** | Implementujte `Warn`, ale nechte tělo prázdné, nebo nastavte `loadOptions.WarningCallback = null;`. |
| **Zachytit jiné typy varování** | Zkontrolujte `info.WarningType` proti `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent` atd. |
| **Běh na Linuxu/macOS** | Ujistěte se, že složka s fonty obsahuje soubory `.ttf`/`.otf` kompatibilní s Linuxem; možná budete muset nainstalovat `libfontconfig`. |
| **Velké dokumenty** | Zvažte streamování dokumentu (`LoadOptions.LoadFormat = LoadFormat.Docx;`) pro snížení zatížení paměti. |

Předvídáním těchto scénářů se vyhnete překvapením při přechodu z vývojového počítače do CI pipeline nebo cloudové VM.

---

## Krok 6: Vizuální potvrzení (volitelné)

Pokud dáváte přednost rychlému vizuálnímu náznaku, můžete zachycená varování vypsat do malého HTML reportu. Zde je malý úryvek, který zapisuje zprávy do `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Po načtení dokumentu zavolejte `handler.WriteReport(@"C:\Docs\warnings.html");` a otevřete jej v prohlížeči. Obrázek níže ukazuje, jak by report mohl vypadat:

![How to capture warnings screenshot](/images/capture-warnings.png)

*Alt text:* **jak zachytit varování** – snímek obrazovky výstupu v konzoli a HTML reportu.

---

## Závěr  

Probrali jsme **jak zachytit varování** v Aspose.Words, ukázali spolehlivý způsob **zpracování chybějících fontů** a ukázali, jak **nastavit vlastní nastavení fontů** pro deterministické vykreslování. Kompletní příklad je připravený k vložení do libovolného .NET řešení a modulární `FontWarningHandler` lze rozšířit tak, aby vyhovoval vaší strategii logování nebo telemetrie.

Další kroky? Zkuste nahradit volání `Console.WriteLine` strukturovaným loggerem jako Serilog, nebo poslat varování do Application Insights pro monitorování v reálném čase. Můžete také prozkoumat vzor `DocumentVisitor`, pokud potřebujete po načtení prozkoumat obsah dokumentu.

Máte otázky ohledně jiných typů varování nebo strategií vkládání fontů? Zanechte komentář níže – šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}