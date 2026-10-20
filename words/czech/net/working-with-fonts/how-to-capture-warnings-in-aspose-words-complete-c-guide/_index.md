---
category: general
date: 2026-03-28
description: Jak zachytit varování při načítání souboru DOCX pomocí Aspose.Words a
  získat varovné zprávy o chybějících písmenech. Naučte se efektivně řešit chybějící
  písma.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: cs
og_description: Jak zachytit varování při načítání DOCX pomocí Aspose.Words, získat
  varovné zprávy a řešit chybějící písma s praktickými ukázkami kódu.
og_title: Jak zachytit varování v Aspose.Words – Kompletní průvodce C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak zachytit varování v Aspose.Words – kompletní průvodce C#
url: /cs/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak zachytit varování v Aspose.Words – Kompletní průvodce pro C#

Už jste se někdy zamýšleli **jak zachytit varování**, která se objeví při načítání Word dokumentu pomocí Aspose.Words? Možná vidíte podivné změny fontů a potřebujete přesně vědět proč. Zkrátka můžete napojit se na varovný systém knihovny, **získat varovné zprávy** a dokonce **zpracovat chybějící fonty**, než zničí vaše rozložení.  

V tomto tutoriálu projdeme reálný scénář: načtení DOCX, sběr všech varování, která engine vyprodukuje, a výpis detailů o jakékoli substituci fontu, která nastane. Na konci budete mít připravený kód, pochopíte „proč“ každého kroku a budete vědět, jak přístup rozšířit pro své projekty.

## Co se naučíte

- Jak nakonfigurovat `LoadOptions`, aby se varování zachytávala automaticky.  
- Přesný způsob, jak **získat varovné zprávy** z `WarningInfoCollection`.  
- Jak identifikovat a reagovat na **chybějící fonty** pomocí příznaku `WarningType.FontSubstitution`.  
- Tipy pro řešení okrajových případů, jako jsou dokumenty s vloženými fonty nebo vlastní složky s fonty.  

Žádné externí odkazy nejsou potřeba – vše, co potřebujete, je zde.

---

## Požadavky

- .NET 6.0 nebo novější (kód také funguje na .NET Framework 4.7+).  
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`).  
- Ukázkový DOCX (`input.docx`), který buď postrádá některé fonty, nebo používá fonty, které nejsou nainstalovány na vašem počítači.  

To je vše. Pokud už jste zvyklí na C# a Visual Studio, můžete kód zkopírovat a spustit okamžitě.

---

## Krok 1: Připravte Load Options a Callback pro varování

První věc, kterou Aspose.Words udělá, když zavoláte `new Document(path, loadOptions)`, je parsování souboru. Během parsování může narazit na chybějící fonty, nepodporované funkce nebo zastaralý markup. Abyste tyto události zachytili, potřebujete objekt **warning callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Proč je to důležité:** Bez callbacku Aspose.Words tiše zapisuje varování do konzole (nebo je zahazuje), takže zůstáváte v temnotě ohledně substitucí fontů, které mohou ovlivnit rozložení. Poskytnutím dedikované `WarningInfoCollection` získáte plnou viditelnost.

> **Tip:** Pokud vás zajímají jen varování související s fonty, můžete je později filtrovat – ale sběr *všech* varování vám poskytne bezpečnostní síť pro budoucí problémy.

---

## Krok 2: Načtěte dokument s nakonfigurovanými možnostmi

Nyní, když je callback připraven, načtěte soubor. Konstruktor `Document` automaticky vyvolá callback pro jakýkoli problém, který najde.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Co se děje pod kapotou?** Aspose.Words parsuje Open XML, řeší styly a snaží se přiřadit každou referenci na font k systémově nainstalovanému fontu. Pokud shoda není nalezena, vytvoří položku `WarningInfo` typu `FontSubstitution`.

---

## Krok 3: Získejte a prozkoumejte shromážděná varování

Po dokončení načítání váš `warningCollector` nyní obsahuje každé varování, které nastalo. Vyjmeme je a zaměříme se na zprávy o substituci fontů.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Ukázkový výstup** (vaše konzole může zobrazit něco podobného):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Pokud chcete *všechna* varování, jednoduše odstraňte podmínku `if` nebo logujte `warning.Type` pro každou položku.

---

## Krok 4: Zpracování chybějících fontů – víc než jen logování

Zachytávání varování je užitečné, ale často potřebujete **zpracovat chybějící fonty** programově. Zde jsou dvě běžné strategie:

### 4.1 Nahraďte chybějící fonty konkrétním náhradním fontem

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Nyní bude jakýkoli chybějící font nahrazen *Calibri* místo výchozí náhrady knihovny.

### 4.2 Dynamicky vložte náhradní font

Pokud máte vlastní soubor s fontem (např. `MyFallback.ttf`), můžete jej zaregistrovat za běhu:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Tento přístup je užitečný, když distribuujete konkrétní firemní font spolu s aplikací.

> **Okrajový případ:** Dokumenty, které již embedují požadovaný font, budou ignorovat systémová pravidla substituce. V takovém scénáři bude kolekce varování pro tento font prázdná, což je přesně to, co chcete.

---

## Krok 5: Kompletní funkční příklad (připravený ke kopírování)

Níže je samostatný program, který demonstruje vše od začátku do konce. Stačí nahradit `YOUR_DIRECTORY/input.docx` cestou k vašemu testovacímu souboru.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Co očekávat**

- Konzole vypíše každé varování o substituci fontu, předponované emoji varování pro lepší viditelnost.  
- Výstupní DOCX (`output.docx`) použije *Calibri* všude, kde byl detekován chybějící font.  
- Žádné neodchycené výjimky – systém varování elegantně zpracuje jakýkoli neznámý font.

---

## Často kladené otázky a odpovědi

**Q: Bude to fungovat i s PDF generovanými z Wordu?**  
A: Ano. Aspose.Words zachází s PDF jako s dalším výstupním formátem. Zachycení varování probíhá během fáze *load*, takže je nezávislé na konečném exportu.

**Q: Co když potřebuji zachytit varování pro **všechny** operace s dokumentem (uložení, konverze, atd.)?**  
A: Stejnou `WarningInfoCollection` můžete znovu použít přiřazením k `Document.WarningCallback` po vytvoření dokumentu. Každá následná operace přidá nové položky do stejné kolekce.

**Q: Ovlivňuje warning callback výkon?**  
A: Nezaznamenatelně. Kolekce jen ukládá objekty; pokud nepracujete s tisíci varováními v těsném smyčce, zpomalení si nevšimnete.

**Q: Jak mohu potlačit varování, která mě nezajímají?**  
A: Implementujte vlastní třídu, která dědí z `IWarningCallback`, a filtrujte uvnitř metody `Warning`. Vestavěná `WarningInfoCollection` pouze ukládá, nefiltruje.

---

## Tipy a úskalí

- **Tip:** Vždy kontrolujte `Warning.Description` – obsahuje přesný název chybějícího fontu. To vám může pomoci rozhodnout, zda font zahrnout do aplikace.  
- **Pozor na vložené fonty:** Pokud zdrojový DOCX již obsahuje potřebný font, Aspose.Words nevygeneruje varování o substituci, i když font není lokálně nainstalován.  
- **Bezpečnost vláken:** `WarningInfoCollection` není thread‑safe. Pokud načítáte více dokumentů současně, dejte každému vláknu vlastní kolekci.  
- **Kontrola verze:** API varování je stabilní od Aspose.Words 20.8. Ujistěte se, že používáte aktuální verzi, aby nedošlo k opomenutí nových typů varování.

---

## Závěr

Probrali jsme **jak zachytit varování** z Aspose.Words, ukázali jsme, jak **získat varovné zprávy**, a představili praktické způsoby **zpracování chybějících fontů** pomocí náhradních fontů nebo vlastních složek s fonty. Kompletní příklad je připravený k vložení do libovolného .NET projektu a koncepty se dají rozšířit na větší automatizační pipeline.

Dále můžete zkoumat:

- Použití `Document.WarningCallback` k zachycení varování během operací **uložení**.  
- Logování varování do souboru nebo telemetrického systému pro monitorování v produkci.  
- Rozšíření callbacku pro automatické nahrazení chybějících fontů typografiemi specifickými pro značku.

Klidně experimentujte – vyměňte náhradní font, přidejte více dokumentů do dávky nebo integrujte sběrač varování do CI pipeline, která označí regresi související s fonty. Šťastné programování a ať se vaše dokumenty vždy vykreslí přesně tak, jak očekáváte!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}