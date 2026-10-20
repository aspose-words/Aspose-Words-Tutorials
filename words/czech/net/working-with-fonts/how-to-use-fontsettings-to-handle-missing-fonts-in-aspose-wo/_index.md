---
category: general
date: 2026-03-16
description: Naučte se, jak používat FontSettings v Aspose.Words k elegantnímu zpracování
  chybějících fontů – kompletní kód, zpracování událostí a tipy na osvědčené postupy.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: cs
og_description: Jak používat FontSettings v Aspose.Words k řešení chybějících fontů –
  krok za krokem průvodce s kompletním příkladem v C# a praktickými tipy.
og_title: Jak použít FontSettings k řešení chybějících písem v Aspose.Words
tags:
- Aspose.Words
- C#
- Font Management
title: Jak použít FontSettings k obsluze chybějících fontů v Aspose.Words
url: /cs/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak použít FontSettings k řešení chybějících fontů v Aspose.Words

Už jste se někdy zamýšleli **jak použít FontSettings**, když vaše Word dokumenty odkazují na fonty, které nejsou nainstalovány na serveru? Nejste v tom sami. Chybějící fonty mohou způsobit ošklivé náhradní fonty nebo dokonce vyvolat výjimky a většina vývojářů problém jednoduše ignoruje, dokud se neobjeví v produkci.  

V tomto tutoriálu vám přesně ukážeme **jak použít FontSettings** k **řešení chybějících fontů** v Aspose.Words, zachytit podrobná varování a zajistit předvídatelné vykreslování dokumentu. Na konci budete mít připravený ukázkový C# kód, pochopíte, proč je každý řádek důležitý, a budete vědět, jak přizpůsobit řešení pro větší projekty.

## Co tento průvodce pokrývá

- Nastavení **FontSettings** a přihlášení k události `SubstitutionWarning`.  
- Připojení nastavení k `LoadOptions`, aby byla respektována při načítání dokumentu.  
- Spuštění testovacího dokumentu, který úmyslně postrádá fonty, a čtení výstupu v konzoli.  
- Tipy pro logování, vypnutí automatické substituce a řešení okrajových případů, jako jsou více chybějících fontů.  

Externí dokumentace není potřeba — vše, co potřebujete, je zde.

## Předpoklady

- .NET 6+ (nebo .NET Framework 4.6.2+).  
- Aspose.Words pro .NET 23.9 nebo novější (API, které používáme, je stabilní napříč posledními verzemi).  
- Jednoduchý soubor `.docx`, který odkazuje na font, o kterém víte, že není nainstalován (např. *Comic Sans MS* v Linux kontejneru).  

To je vše — žádné další NuGet balíčky kromě Aspose.Words.

## Proč je důležité řešit chybějící fonty

Když dokument odkazuje na font, který runtime nemůže najít, Aspose.Words automaticky nahradí nejbližší shodou. Tato substituce je často přijatelna, ale někdy potřebujete **logovat**, které fonty chyběly (pro soulad) nebo **zabránit** substituci úplně (např. pro brand‑specifické PDF). Připojením se k `FontSettings.SubstitutionWarning` získáte plnou viditelnost a kontrolu.

## Krok 1: Vytvořte FontSettings a přihlaste se k události Substitution‑Warning

Prvním krokem je vytvořit instanci `FontSettings`. Tento objekt obsahuje veškerou konfiguraci související s fonty pro knihovnu. Klíčová část je napojení události `SubstitutionWarning`, která se spustí **každýkrát**, když Aspose.Words nedokáže najít požadovaný font.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**Proč je to důležité:**  
- **Viditelnost:** Okamžitě zjistíte, které fonty chybí.  
- **Auditovatelnost:** Konzole (nebo logger) může být přesměrována do souboru pro souladové zprávy.  
- **Kontrola:** Později můžete rozhodnout, zda nahradíte substituci vlastním fontem.

> **Pro tip:** Pokud dáváte přednost logovacímu frameworku (Serilog, NLog, atd.), nahraďte volání `Console.WriteLine` za `logger.Information(...)`.

## Krok 2: Připojte FontSettings k LoadOptions

`LoadOptions` je prostředek, který říká Aspose.Words, jak má soubor během načítání zpracovat. Přiřazením objektu `FontSettings` zajistíte, že handler varování bude aktivní *před* tím, než se začne parsovat obsah.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Proč je to důležité:**  
- Pokud načtete dokument bez předání `LoadOptions`, použije se výchozí zpracování fontů a varování vám unikne.  
- Tento přístup vám také umožní upravit další chování načítání (např. ochranu heslem) ve stejném objektu.

## Krok 3: Načtěte dokument s nakonfigurovanými možnostmi

Nyní konečně načteme Word soubor. Cesta může být absolutní nebo relativní; Aspose.Words respektuje `LoadOptions`, které jsme právě připravili.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

Pokud dokument obsahuje font, který není nainstalován, událost `SubstitutionWarning` se spustí a uvidíte výstup podobný příkladu níže.

### Očekávaný výstup v konzoli

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

Přesná náhrada se může lišit podle řetězce náhradních fontů operačního systému, ale **název chybějícího fontu** bude vždy uveden.

## Krok 4: Ověřte výsledek (volitelné vykreslení)

Často chcete mít jistotu, že dokument po substituci stále vypadá v pořádku. Rychlý způsob je uložit jej jako PDF a otevřít výsledek.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

Pokud potřebujete **zabránit** substituci úplně, nastavte `FontSettings.SubstitutionSettings.TableSubstitution = false` před načtením. Pak Aspose.Words vyhodí výjimku pro chybějící fonty, kterou můžete zachytit a ošetřit.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## Kompletní funkční příklad

Níže je kompletní, připravený k spuštění program. Vložte jej do konzolové aplikace, upravte cestu k souboru a stiskněte **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### Co očekávat

- Konzole vypíše každý chybějící font spolu s vybranou náhradou.  
- Výsledné PDF (pokud jste ponechali volitelné uložení) zobrazí dokument pomocí náhradního fontu, čímž zajistí integritu rozvržení.

## Často kladené otázky a okrajové případy

| Otázka | Odpověď |
|----------|--------|
| **Co když chybí více fontů?** | Událost se spustí jednou pro každý chybějící font, takže získáte samostatný řádek logu pro každý. |
| **Mohu nahradit náhradu vlastním fontem?** | Ano. V obsluze události můžete zavolat `e.SubstitutedFont = new FontInfo("MyCustomFont")`. |
| **Je varování vyvoláno i pro vložené fonty, které se nepodaří načíst?** | Rozhodně — ať už je font externí nebo vložený, varování se projeví stejným způsobem. |
| **Musím uvolnit `Document`?** | `Document` implementuje `IDisposable`. Zabalte jeho použití do bloku `using`, pokud načítáte mnoho souborů ve smyčce. |
| **Bude to fungovat v Linux kontejnerech?** | Pokud Aspose.Words dokáže najít systémové fonty (např. přes `fontconfig`), funguje stejný mechanismus událostí. |

## Nejlepší postupy a profesionální tipy

- **Centralizujte logování:** Vytvořte pomocnou metodu, která zapisuje jak do konzole, tak do trvalého log souboru.  
- **Dávkové zpracování:** Při konverzi desítek dokumentů znovu použijte jedinou instanci `FontSettings`, abyste se vyhnuli opakovaným přihlášením k událostem.  
- **Výkon:** Varování o substituci přidává zanedbatelný overhead, ale pokud zpracováváte tisíce souborů, zvažte jejich vypnutí po ověření sady fontů.  
- **Bezpečnost verzí:** API `SubstitutionWarning` je stabilní od Aspose.Words 16.0, takže se na něj můžete spolehnout při budoucích aktualizacích.

## Závěr

Prošli jsme **jak použít FontSettings** v Aspose.Words k **elegantnímu řešení chybějících fontů**. Vytvořením objektu `FontSettings`, přihlášením k `SubstitutionWarning` a načítáním dokumentů přes `LoadOptions` získáte plnou viditelnost problémů s fonty a můžete se rozhodnout, zda je logovat, nahradit nebo ukončit zpracování.  

Od jednoduchého výstupu v konzoli po vlastní logiku substituce, tento vzor škáluje na velké dávky dokumentů, což zajišťuje konzistentní a auditovatelný výstup.

**Další kroky:**  

- Prozkoumejte **vlastní substituci fontů** přiřazením `e.SubstitutedFont` uvnitř události.  
- Kombinujte tento přístup s **vykreslováním dokumentu do obrázků** pro generování náhledů.  
- Podívejte se na **Aspose.PDF**, pokud potřebujete vložit substituované fonty přímo do finálního PDF pro úplnou přenositelnost.

Šťastné programování a ať vaše dokumenty už nikdy netrpí zlobivým chybějícím fontem!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}