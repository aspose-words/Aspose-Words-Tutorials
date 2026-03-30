---
category: general
date: 2026-03-30
description: jak zachytit varování při načítání souboru DOCX – naučte se detekovat
  chybějící písma, konfigurovat nastavení fontů a nastavit možnosti načítání v C#
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: cs
og_description: Jak zachytit varování při načítání souboru DOCX – průvodce krok za
  krokem pro detekci chybějících fontů a nastavení fontů v C#.
og_title: jak zachytit varování – nastavit možnosti načítání pro chybějící fonty
tags:
- Aspose.Words
- C#
- Font management
title: Jak zachytit varování – nakonfigurujte možnosti načítání pro chybějící písma
url: /cs/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# jak zachytit varování – nakonfigurujte možnosti načítání pro chybějící fonty

Už jste se někdy zamysleli **jak zachytit varování**, která se objeví, když se dokument pokusí použít font, který nemáte nainstalovaný? Jedná se o situaci, která mnohé vývojáře pracující s knihovnami pro zpracování textu zaskočí, zejména když potřebujete **detekovat chybějící fonty**, než naruší váš PDF exportní řetězec.

V tomto tutoriálu vám ukážeme praktické, připravené řešení, které **konfiguruje nastavení fontů**, **nastavuje možnosti načítání** a vypisuje každé varování o substituci do konzole. Na konci budete přesně vědět, jak **zacházet s chybějícími fonty** způsobem, který udrží vaši aplikaci robustní a uživatele spokojené.

## Co se naučíte

- Jak **nastavit možnosti načítání**, aby knihovna hlásila problémy s fonty místo tichého nahrazování.
- Přesné kroky k **konfiguraci nastavení fontů** pro zachycení varování.
- Způsoby, jak **programově detekovat chybějící fonty** a reagovat na ně.
- Kompletní příklad v C#, který lze zkopírovat a funguje s nejnovější verzí Aspose.Words pro .NET (v24.10 v době psaní).
- Tipy, jak rozšířit řešení o logování varování, přepnutí na vlastní fonty nebo přerušení zpracování, když chybí kritické fonty.

> **Předpoklad:** Musíte mít nainstalovaný NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`). Žádné další externí závislosti nejsou potřeba.

---

## Krok 1: Importujte jmenné prostory a připravte projekt

Nejprve přidejte nezbytné `using` direktivy. Nejedná se jen o boilerplate; říkáte tak kompilátoru, kde se nachází `LoadOptions`, `FontSettings` a `Document`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Tip:** Pokud používáte .NET 6+, můžete povolit *global using* pro vyhnutí se opakování těchto řádků v každém souboru.

---

## Krok 2: Nastavte možnosti načítání a povolte varování o substituci fontů

Jádrem **jak zachytit varování** je objekt `LoadOptions`. Vytvořením nového instance `FontSettings` a připojením obslužné rutiny k události `SubstitutionWarning` řeknete knihovně, aby upozornila pokaždé, když nenajde požadovaný font.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Proč je to důležité:** Bez přihlášení k události Aspose.Words tiše přepne na výchozí font a nikdy se nedozvíte, které glyfy byly nahrazeny. Poslechnutím `SubstitutionWarning` získáte kompletní auditní stopu – klíčové pro prostředí s vysokými požadavky na shodu.

---

## Krok 3: Načtěte dokument pomocí nakonfigurovaných možností

Jakmile jsou varování nastavená, načtěte svůj DOCX (nebo jakýkoli podporovaný formát) s `loadOptions`, které jste právě připravili. Konstruktor `Document` okamžitě spustí logiku kontroly fontů.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Pokud soubor odkazuje například na *„Comic Sans MS“* na stroji, který má jen *„Arial“*, uvidíte něco jako:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Tento řádek je vytištěn přímo do konzole díky obslužné rutině, kterou jsme připojili dříve.

---

## Krok 4: Ověřte a reagujte na zachycená varování

Zachycení varování je jen polovina boje; často musíte rozhodnout, co dál. Níže je rychlý vzor, který ukládá varování do seznamu pro pozdější analýzu – ideální, pokud je chcete zaznamenat do souboru nebo přerušit import, když chybí kritický font.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Zvládání okrajových případů:**  
- **Více chybějících fontů:** Seznam bude obsahovat jeden záznam na každou substituci, takže můžete iterovat a vytvořit podrobnou zprávu.  
- **Vlastní náhradní fonty:** Pokud máte vlastní soubory fontů, přidejte je do `FontSettings` před načtením: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Varování pak ukáží vlastní náhradu místo systémové výchozí.

---

## Krok 5: Kompletní funkční příklad (připravený ke zkopírování)

Sestavením všeho dohromady získáte samostatnou konzolovou aplikaci, kterou můžete nyní zkompilovat a spustit.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Očekávaný výstup do konzole** (když DOCX odkazuje na chybějící font):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Pokud chybí *kritický* font, například „Times New Roman“, uvidíte místo toho zprávu o přerušení.

---

## Často kladené otázky a úskalí

| Otázka | Odpověď |
|----------|--------|
| **Musím volat `SetFontsFolder` pro zachycení varování?** | Ne. Událost varování funguje s výchozími systémovými fonty. `SetFontsFolder` použijte jen tehdy, když chcete dodat další náhradní fonty. |
| **Bude to fungovat na .NET Core / .NET 5+?** | Ano. Aspose.Words 24.10 podporuje všechny moderní .NET runtime. Jen se ujistěte, že NuGet balíček odpovídá vašemu cílovému frameworku. |
| **Co když chci varování zapisovat do souboru místo do konzole?** | Nahraďte `Console.WriteLine(msg);` voláním libovolného logovacího frameworku, např. `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Mohu potlačit varování pro konkrétní fonty?** | Ano. V obslužné rutině můžete filtrovat: `if (e.FontName == "SomeFont") return;`. To poskytuje jemnozrnné řízení. |
| **Existuje způsob, jak považovat chybějící fonty za chyby?** | Vraťte výjimku ručně uvnitř obslužné rutiny, když je splněna podmínka, nebo nastavte příznak a přerušte po konstrukci `Document`, jak ukazuje příklad. |

---

## Závěr

Nyní máte solidní, produkčně připravený vzor pro **jak zachytit varování**, která se objeví při načítání dokumentů s chybějícími fonty. **Detekcí chybějících fontů**, **konfigurací nastavení fontů** a **nastavením možností načítání** získáte úplnou přehlednost o událostech substituce fontů a můžete rozhodnout, zda je zaznamenáte, použijete náhradu nebo proces přerušíte.

Dalším krokem může být integrace této logiky do vašeho PDF konverzního řetězce, přidání vlastních náhradních fontů nebo předání seznamu varování do monitorovacího systému. Přístup škáluje od malých utilit až po enterprise‑grade služby pro zpracování dokumentů.

---

### Další čtení a další kroky

- **Prozkoumejte další funkce FontSettings** – vkládání vlastních fontů, řízení pořadí náhrad a licenční otázky.  
- **Kombinujte s PDF konverzí** – po zachycení varování zavolejte `doc.Save("output.pdf");` a ověřte, že PDF používá očekávané fonty.  
- **Automatizujte testování** – napište unit testy, které načtou dokumenty s vědomě chybějícími fonty a ověří, že seznam varování obsahuje očekávané zprávy.  

Pokud narazíte na problémy nebo máte nápady na vylepšení, neváhejte zanechat komentář. Šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}