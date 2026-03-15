---
category: general
date: 2026-03-14
description: Rychle řešte chybějící písma pomocí Aspose.Words. Naučte se zachytávat
  varování o náhradě písma, konfigurovat LoadOptions a vyhnout se problémům s vykreslováním.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: cs
og_description: Zpracujte chybějící písma v Aspose.Words pomocí sběrače varování.
  Tento tutoriál ukazuje krok za krokem, jak detekovat a zaznamenávat náhrady písem.
og_title: Řešení chybějících fontů v Aspose.Words – Kompletní průvodce C#
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Řešení chybějících fontů v Aspose.Words – Kompletní C# průvodce
url: /cs/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Řešení chybějících fontů v Aspose.Words – Kompletní průvodce v C#

Už jste někdy potřebovali **zpracovat chybějící fonty** při načítání Word dokumentu a přemýšleli, proč váš výstup PDF nebo obrázku vypadá špatně? Nejste v tom sami. Chybějící soubory fontů jsou tichým problémem, který může dokonalý návrh zprávy proměnit v nečitelný chaos.  

Dobrá zpráva? Aspose.Words vám poskytuje čistý způsob, jak zachytit události nahrazení fontů, zaznamenat je a dokonce vyměnit za náhradní font, pokud chcete. V tomto tutoriálu projdeme kompletním, připraveným příkladem, který přesně ukazuje, jak nastavit sběrač varování, připojit jej k `LoadOptions` a načíst dokument, který může obsahovat chybějící fonty.

Na konci tohoto průvodce budete schopni:

* Detekovat každou náhradu fontu, která nastane během načítání dokumentu.  
* Vypsat přátelskou zprávu do konzole (nebo ji směrovat do loggeru) pro každý chybějící font.  
* Rozšířit řešení tak, aby nahrazovalo fonty, pokud je to potřeba.  

**Předpoklady** – budete potřebovat:

* .NET 6.0 nebo novější (kód funguje i s .NET Core a .NET Framework).  
* NuGet balíček Aspose.Words for .NET (aktuální verze 23.11).  
* Word soubor, který úmyslně odkazuje na font, který nemáte nainstalovaný – nazveme ho `doc-with-missing-font.docx`.  

Pokud už ovládáte C# a máte projekt nastavený, můžete rovnou skočit na kód. Jinak čtěte dál; nejprve si projdeme drobné kroky nastavení.

---

## Proč je důležité řešit chybějící fonty

Když Aspose.Words načítá dokument, snaží se přiřadit každý glyf k fontu nainstalovanému v systému. Pokud přesně požadovaný font nenajde, tiše nahradí nejbližší shodou. Tato náhrada může změnit výšku řádků, kerning a dokonce způsobit, že některé znaky zmizí. Zachycením události `WarningType.FontSubstitution` získáte transparentní přehled o **tom, co** bylo nahrazeno a **proč**, což je nezbytné pro:

* Udržení konzistence značky (váš firemní font se musí zobrazovat přesně podle návrhu).  
* Ladění problémů s konverzí do PDF – často je viníkem chybějící font.  
* Budování automatizovaných pipeline pro dokumenty, kde potřebujete označit problematické soubory k ručnímu přezkoumání.

Nyní, když je „proč“ jasné, pojďme na **jak**.

---

## Krok 1 – Nastavení sběrače varování

První, co potřebujeme, je objekt, který dokáže poslouchat varování Aspose.Words. `DocumentWarnings` implementuje `IWarningCallback`, což nám umožňuje reagovat kdykoli knihovna vyvolá varování.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Co se děje?**  
* `DocumentWarnings` je tenký obal kolem rozhraní callbacku.  
* Lambda kontroluje `e.WarningType`, takže ignorujeme nesouvisející varování (např. zastaralé funkce).  
* `e.WarningInfo` obsahuje název chybějícího fontu, který vypisujeme do konzole.  

*Tip*: V produkci nahraďte `Console.WriteLine` strukturovaným loggerem (Serilog, NLog) – tak získáte automaticky časové razítko a úroveň logu.

---

## Krok 2 – Připojení sběrače k LoadOptions

`LoadOptions` je strážcem pro každý dokument, který otevřete pomocí Aspose.Words. Přiřazením instance `fontWarnings` k jeho vlastnosti `WarningCallback` zajistíme, že sběrač bude aktivní během načítání.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Proč používat LoadOptions?**  
Kromě varování vám `LoadOptions` umožňuje řídit zpracování hesel, kódování a dokonce vlastní načítání zdrojů. Zde se soustředíme na část s varováními, ale stejný vzor funguje i pro jiné callbacky.

---

## Krok 3 – Načtení dokumentu s nakonfigurovanými možnostmi

Nyní konečně načteme dokument do paměti. Pokud bude některý font chybět, náš sběrač spustí událost a uvidíte řádek v konzoli pro každou náhradu.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Pokud spustíte tento úryvek s dokumentem, který odkazuje např. na *Calibri Light*, zatímco testovací stroj má jen *Calibri*, získáte výstup podobný tomuto:

```
Font 'Calibri Light' was substituted.
```

To je celý detekční smyčka – jednoduchá, ale výkonná.

---

## Krok 4 – (Volitelné) Nahrazení chybějících fontů známým náhradním fontem

Někdy nechcete jen logovat problém; chcete vynutit náhradní font, aby výstup vypadal konzistentně. Aspose.Words vám umožňuje poskytnout vlastní objekt `FontSettings`, který mapuje chybějící fonty na náhradu.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Vysvětlení**  
* Zástupný znak `"*"` říká Aspose.Words, aby s jakýmkoli chybějícím fontem zacházel stejným způsobem.  
* Můžete také mapovat konkrétní fonty jednotlivě, pokud potřebujete jemnější kontrolu.  
* Po nastavení `document.FontSettings` bude jakékoli následné renderování (PDF, obrázek, HTML) respektovat tuto náhradu.

---

## Kompletní funkční příklad

Níže je celý program, který můžete zkopírovat a vložit do konzolové aplikace. Obsahuje všechny potřebné `using` direktivy, ošetření chyb a komentáře pro přehlednost.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Očekávaný výstup** (když je detekován chybějící font):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Pokud zdrojový dokument již obsahuje všechny požadované fonty, řádek s varováním se jednoduše neobjeví – není co řešit.

---

## Často kladené otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Co když chci jen logovat, ne nahrazovat fonty?** | Vynechte celý blok `FontSettings`; samotný sběrač varování stačí. |
| **Mohu varování přesměrovat do souboru?** | Ano – nahraďte `Console.WriteLine` například `File.AppendAllText("font-warnings.log", …)`. |
| **Funguje to pro DOC, DOCX i ODT?** | Rozhodně. `LoadOptions` se vztahuje na všechny formáty podporované Aspose.Words. |
| **Co s vlastním fontem vloženým v dokumentu?** | Vložené fonty obcházejí mechanismus náhrady; používají se tak, jak jsou. |
| **Je tu nějaký dopad na výkon?** | Překrytí je minimální – jen jeden callback na chybějící font. U velkých dávek zvažte agregaci varování místo zápisu po každé události. |

---

## Závěr

Ukázali jsme **jak řešit chybějící fonty** v Aspose.Words tím, že jsme připojili sběrač `DocumentWarnings` k `LoadOptions`, případně přidali náhradní font a uložili výsledek. Tento vzor vám poskytuje úplnou viditelnost událostí náhrady fontů, což pomáhá udržet vizuální věrnost při konverzi do PDF, obrázku nebo HTML.

Další kroky, které můžete prozkoumat:

* Integrace sběrače varování s centralizovaným logging frameworkem.  
* Vytvoření UI dashboardu, který vypisuje dokumenty s chybějícími fonty pro dávkové zpracování.  
* Kombinace tohoto přístupu s Aspose.PDF k ověření, že generované PDF skutečně používají náhradní font.  

Nebojte se experimentovat – zaměňte `"Arial"` za `"Tahoma"` nebo načtěte jinou sadu dokumentů. Hlavní myšlenka zůstává stejná: zachytit varování, reagovat na něj a zajistit, aby vaše dokumenty vypadaly přesně tak, jak mají.

Šťastné programování! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}