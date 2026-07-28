---
category: general
date: 2026-01-10
description: Naučte se, jak používat LoadOptions k řešení chybějících fontů v Aspose.Words.
  Krok za krokem kód, tipy a osvědčené postupy pro spolehlivé načítání dokumentů.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: cs
og_description: Jak použít LoadOptions k řešení chybějících fontů v Aspose.Words.
  Získejte kompletní, spustitelný příklad s vysvětleními a praktickými tipy.
og_title: Jak používat LoadOptions v Aspose.Words – kompletní průvodce
tags:
- Aspose.Words
- C#
- .NET
title: Jak používat LoadOptions v Aspose.Words – Kompletní průvodce
url: /cs/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak používat LoadOptions v Aspose.Words – Kompletní průvodce

Už jste se někdy zamysleli **jak používat LoadOptions** při načítání dokumentu Word, který může postrádat některá písma? Nejste jediní, kdo se nad tím trápí. V mnoha reálných projektech dokumenty putují mezi počítači a cílový systém často nemá přesně ty typy písma, které autor použil. Výsledek? Neočekávané náhrady písem, které mohou narušit rozvržení, skrýt důležité znaky nebo prostě vypadat nesprávně.  

Naštěstí Aspose.Words poskytuje čistý způsob, jak *zpracovat chybějící písma*, tím, že vystavuje objekt `LoadOptions` s výstražným zpětným voláním. V tomto tutoriálu se přesně naučíte **jak používat LoadOptions** k zachycení varování o náhradě písem, jejich zaznamenání a udržení robustnosti vašeho zpracovatelského řetězce.

Probereme:

* Nastavení třídy výstražného zpětného volání  
* Konfiguraci `LoadOptions` s tímto zpětným voláním  
* Načtení dokumentu při sledování chybějících písem  
* Tipy pro odstraňování problémů a rozšíření řešení  

Není potřeba žádná externí dokumentace – vše, co potřebujete, je zde.

---

## Co budete potřebovat

Než se pustíme dál, ujistěte se, že máte:

* **Aspose.Words pro .NET** (nejnovější verze k roku 2026) nainstalovaná přes NuGet  
* Vývojové prostředí .NET (Visual Studio, Rider nebo VS Code)  
* Ukázkový soubor DOCX, který odkazuje na písmo, které nemáte nainstalované (nazveme jej `input.docx`)  

To je vše – žádné další knihovny nejsou potřeba.

---

## Krok 1 – Definujte výstražný zpětný volání pro zachycení náhrady písma

Prvním dílkem skládačky je třída, která implementuje `IWarningCallback`. Aspose.Words zavolá její metodu `Warning`, kdykoli narazí na něco pozoruhodného – například chybějící písmo.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Proč je to důležité:**  
Filtrováním na `WarningType.FontSubstitution` se vyhneme nepořádku od nesouvisejících varování (např. zastaralých funkcí). Zpětné volání vám dává plnou kontrolu – můžete zaznamenávat do souboru, vyvolat výjimku nebo dokonce programově vložit náhradní písmo.

---

## Krok 2 – Nakonfigurujte LoadOptions se zpětným voláním

Nyní, když máme obslužnou rutinu, musíme Aspose.Words říct, aby ji použil. Zde se prakticky ukazuje **jak používat LoadOptions**.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Tip:** `LoadOptions` nabízí mnoho dalších přepínačů (např. `Password`, `LoadFormat`, `Encoding`). Můžete je řetězit, ale pro zpracování chybějících písem je `WarningCallback` hlavní hvězdou.

---

## Krok 3 – Načtěte dokument pomocí nakonfigurovaných možností

S připraveným `LoadOptions` je načtení dokumentu jednoduché. Aspose.Words automaticky zavolá zpětné volání pro každé písmo, které nenajde.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Očekávaný výstup:**  

Pokud `input.docx` používá písmo nazvané *“GothicBold”*, které není nainstalováno, uvidíte něco jako:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

Varovná řádka se objeví **přesně v okamžiku, kdy je chybějící písmo nalezeno**, a poskytne vám okamžitou zpětnou vazbu.

---

## Krok 4 – (Volitelné) Pokračujte ve zpracování dokumentu

Obvykle budete chtít udělat více než jen načíst soubor. Níže jsou uvedeny některé běžné akce po načtení, které fungují hladce s naším varovným nastavením.

### 4.1 Uložte dokument jako PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Nahraďte chybějící písma známou náhradou

Pokud preferujete konkrétní náhradu (např. *“Calibri”*), můžete před uložením upravit `FontSettings`:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Zaznamenejte všechna varování do souboru

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Tyto úryvky ilustrují **jak používat LoadOptions** nad rámec základního případu a poskytují vám flexibilitu pro řešení úrovně produkce.

---

## Časté úskalí a jak **zpracovat chybějící písma** elegantně

| Úskalí | Proč se to stane | Jak opravit / zmírnit |
|--------|------------------|-----------------------|
| **Žádné zpětné volání nepřipojeno** | Zapomněli jste nastavit `WarningCallback`. | Vždy vytvořte instanci `LoadOptions` a přiřaďte svůj obslužný kód před načtením. |
| **Zpětné volání pouze tiskne, nikdy neukládá** | Ve webové službě se výstup na konzoli ztrácí. | Nahraďte `Console.WriteLine` loggerem (Serilog, NLog) nebo zapisujte do trvalého úložiště. |
| **Více chybějících písem, hlásí se jen první** | Vaše zpětné volání vyhodí výjimku při prvním varování. | Udržujte zpětné volání lehké; vyhýbejte se vyhazování výjimek, pokud opravdu nechcete ukončit. |
| **Náhradní písmo vypadá špatně** | Výchozí náhrada může zvolit vizuálně odlišné písmo. | Použijte `FontSettings.SubstitutionSettings.FontSubstitutionRules` k upřednostnění požadované náhrady. |
| **Výkonnostní dopad u obrovských dokumentů** | Zpětné volání varování je vyvoláno tisíckrát. | Shromažďujte varování do seznamu a zpracujte je po načtení, nebo filtrujte jen unikátní názvy písem. |

---

## Kompletní funkční příklad – všechny části dohromady

Níže je kompletní, připravený program, který demonstruje celý tok. Zkopírujte a vložte do konzolového projektu, přidejte NuGet balíček Aspose.Words a bude fungovat ihned.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Spuštěním tohoto programu**:

1. Vytiskne všechna varování o náhradě písem do konzole.  
2. Uloží původní rozvržení jako `output.pdf`.  
3. Uloží druhý PDF (`output-with-fallback.pdf`), který vynutí náhradu na *Calibri* nebo *Arial*.

---

## Často kladené otázky (FAQ)

**Q: Funguje to i pro soubory DOC, RTF nebo HTML?**  
A: Ano. `LoadOptions` je nezávislý na formátu; pokud předáte správnou cestu k souboru, výstražné zpětné volání se spustí pro chybějící písma ve všech podporovaných formátech.

**Q: Mohu varování úplně potlačit?**  
A: Můžete přiřadit nečinné zpětné volání (`new IWarningCallback { Warning = _ => {} }`) nebo nastavit `LoadOptions.WarningCallback = null`. Avšak ztráta viditelnosti může znamenat, že vám uniknou kritické problémy s písmy.

**Q: Co když potřebuji nahradit chybějící písma vloženými?**  
A: Použijte `FontSettings` k vložení souboru náhradního písma (`AddFontSource`). Kombinujte to s pravidly náhrady pro plynulý zážitek.

**Q: Je zpětné volání thread‑safe?**  
A: Zpětné volání může být vyvoláno z více vláken při paralelním načítání velkých dokumentů. Zajistěte, aby sdílené prostředky (např. soubory logů) byly synchronizovány.

---

## Závěr

Prošli jsme **jak používat LoadOptions** v Aspose.Words k **elegantnímu zpracování chybějících písem**. Definováním vlastního `IWarningCallback`, jeho připojením k instanci `LoadOptions` a načtením dokumentu s touto konfigurací získáte okamžitý přehled o všech událostech náhrady písem. Odtud můžete logovat, nahrazovat nebo vkládat náhradní písma, aby výstup vypadal přesně tak, jak má.

Pamatujte, klíčové kroky jsou:

1. Implementujte výstražné zpětné volání, které se zaměřuje na `WarningType.FontSubstitution`.  
2. Propojte zpětné volání s objektem `LoadOptions`.  
3. Načtěte svůj dokument s těmito možnostmi.  
4. (Volitelné) Aplikujte další pravidla náhrady písem nebo logování podle potřeby.

Klidně experimentujte – vyměňte konzolový logger za strukturovaný logger, přidejte e‑mailová upozornění pro kritická chybějící písma nebo integrujte tento vzor do většího pipeline pro zpracování dokumentů. Přístup se dobře škáluje, ať už zpracováváte jeden soubor nebo tisíce v dávkovém úkolu.

Šťastné kódování a ať se vaše dokumenty vždy vykreslují s těmi správnými typy písma!  

---

![how to use loadoptions example]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}