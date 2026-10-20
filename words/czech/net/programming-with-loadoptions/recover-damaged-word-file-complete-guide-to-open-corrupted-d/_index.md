---
category: general
date: 2026-01-03
description: Rychle obnovte poškozený soubor Word pomocí Aspose.Words LoadOptions.
  Naučte se, jak otevřít poškozený DOCX a jak získat počet stránek v C#.
draft: false
keywords:
- recover damaged word file
- how to get page count
- open corrupted docx
- aspose words load options
language: cs
og_description: Obnovte poškozený soubor Word pomocí Aspose.Words LoadOptions. Tento
  průvodce ukazuje, jak otevřít poškozený DOCX a jak získat počet stránek v C#.
og_title: Obnovit poškozený soubor Word – Otevřít poškozený DOCX a zjistit počet stránek
tags:
- Aspose.Words
- C#
- Document Recovery
title: Obnova poškozeného souboru Word – Kompletní průvodce otevřením poškozeného
  DOCX a získáním počtu stránek
url: /cs/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obnova poškozeného souboru Word – Kompletní průvodce

Už jste se někdy pokusili **obnovit poškozený soubor Word** a narazili na překážku, protože se dokument odmítá otevřít? Je to frustrující okamžik, zejména když soubor obsahuje kritický obsah. V tomto tutoriálu vám přesně ukážeme, jak **otevřít poškozený DOCX** pomocí Aspose.Words LoadOptions, a poté demonstrujeme **jak získat počet stránek** po načtení souboru. Už žádné hádání nebo nekonečné pokusy‑a‑chyby—jen jasné, spustitelné řešení.

Probereme vše od nastavení knihovny Aspose.Words, konfigurace správných možností načítání, zpracování okrajových případů a nakonec extrakce počtu stránek. Na konci budete mít solidní, připravený k nasazení úryvek kódu, který můžete vložit do jakéhokoli .NET projektu.

## Požadavky

- .NET 6.0 nebo novější (kód funguje také s .NET Core)
- Platná licence Aspose.Words pro .NET (nebo můžete začít s bezplatnou zkušební verzí)
- Visual Studio 2022 nebo jakékoli C#‑kompatibilní IDE
- Poškozený `Corrupted.docx` soubor, který chcete zachránit

Pokud je máte, skvělé—pustíme se do toho.

## Krok 1: Nainstalujte Aspose.Words a přidejte using direktivy

Nejprve potřebujete NuGet balíček. Otevřete terminál ve složce projektu a spusťte:

```bash
dotnet add package Aspose.Words
```

Po instalaci přidejte potřebné jmenné prostory na začátek vašeho C# souboru:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **Pro tip:** Pokud používáte zkušební licenci, zavolejte `License license = new License(); license.SetLicense("Aspose.Total.lic");` brzy v metodě `Main`, abyste se vyhnuli vodoznakům.

## Krok 2: Nakonfigurujte LoadOptions pro obnovu poškozeného souboru Word

Jádrem **obnovy poškozeného souboru Word** je objekt `LoadOptions`. Nastavením `RecoveryMode` na `Lenient` se Aspose.Words pokusí načíst vše, co může, a přeskočí nečitelné části místo vyhození výjimky.

```csharp
// Step 2: Prepare load options for lenient recovery
LoadOptions loadOptions = new LoadOptions
{
    // Lenient mode tells Aspose to salvage what it can.
    RecoveryMode = RecoveryMode.Lenient
};
```

Proč `Lenient`? V režimu *strict* knihovna přeruší při prvním náznaku poškození, což znamená, že ztratíte vše. `Lenient` je bezpečnostní síť, která často vrátí většinu textu, tabulek a dokonce i obrázků.

## Krok 3: Otevřete poškozený DOCX pomocí nakonfigurovaných možností

Nyní skutečně načteme soubor. Nahraďte `YOUR_DIRECTORY` cestou, kde se nachází váš poškozený dokument.

```csharp
// Step 3: Load the corrupted document with our recovery settings
string filePath = @"YOUR_DIRECTORY\Corrupted.docx";

Document document;
try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    return;
}
```

Pokud je soubor silně poškozen, stále získáte objekt `Document`, ale některé sekce mohou chybět. Proto načítání obalujeme do `try/catch`—aby aplikace nezhavárla a můžete zaznamenat přesný problém.

## Krok 4: Jak získat počet stránek z obnoveného dokumentu

Jakmile je dokument v paměti, získání počtu stránek je hračka. Aspose.Words vypočítává stránkování na požádání, takže volání je levné.

```csharp
// Step 4: Retrieve the page count
int pageCount = document.PageCount;
Console.WriteLine($"Recovered document contains {pageCount} page(s).");
```

Tento jediný řádek odpovídá na otázku **jak získat počet stránek**, i pro dříve poškozený soubor. Vlastnost `PageCount` odráží rozvržení po tom, co knihovna zpracovala veškerý dostupný obsah.

## Krok 5: Uložení opraveného dokumentu (volitelné)

Pokud chcete zachovat zachráněnou verzi, jednoduše ji uložte na nové místo. Aspose.Words podporuje mnoho formátů, ale zůstaneme u DOCX pro známé prostředí.

```csharp
// Step 5: Save the cleaned-up document
string outputPath = @"YOUR_DIRECTORY\Recovered.docx";
document.Save(outputPath);
Console.WriteLine($"Recovered document saved to {outputPath}");
```

Uložení také vynutí poslední průchod rozvržením, což může někdy odhalit další problémy, které nebyly patrné během inspekce v paměti.

## Kompletní funkční příklad

Níže je kompletní program, který spojuje všechny kroky. Zkopírujte‑vložit tento kód do nové konzolové aplikace a spusťte jej.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose license here
        // var license = new License();
        // license.SetLicense("Aspose.Total.lic");

        // 1️⃣ Set up load options for lenient recovery
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Lenient
        };

        // 2️⃣ Path to the corrupted DOCX
        string inputPath = @"YOUR_DIRECTORY\Corrupted.docx";

        // 3️⃣ Attempt to load the document
        Document doc;
        try
        {
            doc = new Document(inputPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to open file: {ex.Message}");
            return;
        }

        // 4️⃣ Get the page count (how to get page count)
        int pages = doc.PageCount;
        Console.WriteLine($"✅ Recovered document has {pages} page(s).");

        // 5️⃣ Save the repaired version (optional)
        string outputPath = @"YOUR_DIRECTORY\Recovered.docx";
        doc.Save(outputPath);
        Console.WriteLine($"💾 Recovered file saved at {outputPath}");
    }
}
```

**Očekávaný výstup** (předpokládáme, že soubor měl obsah):

```
✅ Recovered document has 12 page(s).
💾 Recovered file saved at C:\Docs\Recovered.docx
```

Pokud byl soubor zcela nečitelný, uvidíte místo toho chybovou zprávu z bloku catch.

## Běžné okrajové případy a jak je řešit

| Situace | Proč k tomu dochází | Doporučené řešení |
|-----------|----------------|-----------------|
| **Soubor vyhodí `BadImageFormatException`** | Soubor není ve skutečnosti DOCX (možná starý `.doc` nebo přejmenovaný zip). | Ověřte příponu souboru, nebo použijte `LoadOptions.LoadFormat = LoadFormat.Doc` pro starší Word soubory. |
| **Načte se jen část dokumentu** | Některé sekce jsou neodstranitelně poškozené (např. poškozené XML části). | Po načtení zkontrolujte `doc.GetChildNodes(NodeType.Any, true).Count`, abyste viděli, které uzly přežily. Můžete také rychle získat text pomocí `doc.GetText()`. |
| **Počet stránek je nula** | Dokument byl načten, ale neobsahuje žádné informace o rozvržení (např. jen surový text). | Vynutíte rozvržení voláním `doc.UpdatePageLayout();` před čtením `PageCount`. |
| **Problémy s výkonem u velkých souborů** | Lenient režim může být náročný na CPU u velkých dokumentů. | Zvažte načítání jen potřebných sekcí pomocí `LoadOptions.LoadFormat` a `LoadOptions.Password`, pokud je to relevantní. |

## Tipy pro práci s Aspose.Words LoadOptions

- **RecoveryMode.Lenient** je vaše první volba pro poškozené soubory; **RecoveryMode.Strict** je užitečný, když potřebujete vynutit integritu souboru.
- Můžete kombinovat `LoadOptions` s **Password**, pokud je poškozený soubor také chráněn heslem.
- Použijte `Document.UpdatePageLayout()`, když po načtení manipulujete s dokumentem (např. přidáváte/odstraňujete uzly), před opětovným kontrolováním počtu stránek.

## Často kladené otázky

**Q: Funguje to i se soubory .doc (binárními)?**  
A: Ano, ale musíte nastavit `LoadOptions.LoadFormat = LoadFormat.Doc` před voláním konstruktoru.

**Q: Můžu obnovit obrázky vložené v poškozeném souboru?**  
A: Ve většině případů režim Lenient zachová obrázky. Po načtení můžete iterovat `doc.GetChildNodes(NodeType.Shape, true)`, abyste je extrahovali.

**Q: Existuje způsob, jak zaznamenat, které části byly přeskočeny?**  
A: Aspose.Words vyvolá `DocumentLoadingException` s podrobnostmi. Můžete se přihlásit k událostem `Document.Loading`, abyste zachytili tyto zprávy.

## Závěr

Prošli jsme praktickým, kompletním řešením, jak **obnovit poškozený soubor Word**, **otevřít poškozený DOCX** a **získat počet stránek** pomocí Aspose.Words LoadOptions v C#. Nastavením `RecoveryMode.Lenient` necháte knihovnu udělat těžkou práci, zatímco okolní kód vám poskytuje kontrolu, zpracování chyb a volitelné ukládání.

Neváhejte experimentovat: zkuste otevřít starší soubory `.doc`, upravte režim obnovy nebo automatizujte hromadné zpracování mnoha poškozených dokumentů. Koncepty, které jste se zde naučili—načítání s možnostmi, zpracování výjimek, extrakce stránkování—jsou použitelné v široké škále úloh zpracování dokumentů.

Máte další otázky ohledně Aspose.Words, obnovy dokumentů nebo extrakce počtu stránek? Zanechte komentář níže nebo se podívejte na oficiální dokumentaci Aspose pro podrobnější informace. Šťastné programování a ať vaše soubory zůstávají neporušené!

---

![Snímek obrazovky obnoveného dokumentu Word zobrazujícího čísla stránek – příklad obnovy poškozeného souboru Word](https://example.com/images/recover-damaged-word-file.png "obnova poškozeného souboru Word")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}